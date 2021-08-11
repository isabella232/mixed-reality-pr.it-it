---
title: Rendering dei volumi
description: Informazioni su come eseguire in modo efficiente il rendering di immagini volumetriche con opacità e colore Windows Mixed Reality.
author: kevinkennedy
ms.author: kkennedy
ms.date: 03/21/2018
ms.topic: article
keywords: immagine volumetrica, rendering del volume, prestazioni, realtà mista
ms.openlocfilehash: 3843f0f4e49a0564b41d834231630d281aa9e874df8d35c4feaa4fe5bba0ed68
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115220930"
---
# <a name="volume-rendering"></a>Rendering dei volumi

Per la MRI medicale o i volumi di progettazione, vedere [Rendering dei volumi in Wikipedia.](https://en.wikipedia.org/wiki/Volume_rendering) Queste "immagini volumetriche" contengono informazioni dettagliate con opacità e colore in tutto il volume che non possono essere facilmente espresse come superfici come [mesh poligonali.](https://en.wikipedia.org/wiki/Polygon_mesh)

Soluzioni chiave per migliorare le prestazioni
1. BAD: Approccio ingenuo: Mostra volume intero, in genere viene eseguito troppo lentamente
2. GOOD: Piano di taglio: mostra solo una singola sezione del volume
3. GOOD: Cutting Sub-Volume :Mostra solo alcuni livelli del volume
4. GOOD: ridurre la risoluzione del rendering del volume (vedere 'Mixed Resolution Scene Rendering')

Esiste solo una determinata quantità di informazioni che possono essere trasferite dall'applicazione allo schermo in un frame specifico, ovvero la larghezza di banda totale della memoria. Inoltre, qualsiasi elaborazione (o "ombreggiatura") necessaria per trasformare i dati per la presentazione richiede tempo. Le considerazioni principali quando si esegue il rendering del volume sono le seguenti:
* Screen-Width * Screen-Height * Screen-Count * Volume-Layers-On-That-Pixel = Total-Volume-Samples-Per-Frame
* 1028 * 720 * 2 * 256 = 378961920 (100%) (volume res completo: troppi esempi)
* 1028 * 720 * 2 * 1 = 1480320 (0,3% del totale) (sezione sottile: 1 campione per pixel, viene eseguito senza problemi)
* 1028 * 720 * 2 * 10 = 14803200 (3,9% del totale) (sezione sottovolume: 10 campioni per pixel, viene eseguita in modo abbastanza uniforme, sembra 3d)
* 200 * 200 * 2 * 256 = 204800000 (5% del volume completo) (volume res inferiore: meno pixel, volume completo, appare 3d ma un po' sfocato)

## <a name="representing-3d-textures"></a>Rappresentazione di trame 3D

Nella CPU:

```
public struct Int3 { public int X, Y, Z; /* ... */ }
 public class VolumeHeader  {
   public readonly Int3 Size;
   public VolumeHeader(Int3 size) { this.Size = size;  }
   public int CubicToLinearIndex(Int3 index) {
     return index.X + (index.Y * (Size.X)) + (index.Z * (Size.X * Size.Y));
   }
   public Int3 LinearToCubicIndex(int linearIndex)
   {
     return new Int3((linearIndex / 1) % Size.X,
       (linearIndex / Size.X) % Size.Y,
       (linearIndex / (Size.X * Size.Y)) % Size.Z);
   }
   /* ... */
 }
 public class VolumeBuffer<T> {
   public readonly VolumeHeader Header;
   public readonly T[] DataArray;
   public T GetVoxel(Int3 pos)        {
     return this.DataArray[this.Header.CubicToLinearIndex(pos)];
   }
   public void SetVoxel(Int3 pos, T val)        {
     this.DataArray[this.Header.CubicToLinearIndex(pos)] = val;
   }
   public T this[Int3 pos] {
     get { return this.GetVoxel(pos); }
     set { this.SetVoxel(pos, value); }
   }
   /* ... */
 }
```

Nella GPU:

```
float3 _VolBufferSize;
 int3 UnitVolumeToIntVolume(float3 coord) {
   return (int3)( coord * _VolBufferSize.xyz );
 }
 int IntVolumeToLinearIndex(int3 coord, int3 size) {
   return coord.x + ( coord.y * size.x ) + ( coord.z * ( size.x * size.y ) );
 }
 uniform StructuredBuffer<float> _VolBuffer;
 float SampleVol(float3 coord3 ) {
   int3 intIndex3 = UnitVolumeToIntVolume( coord3 );
   int index1D = IntVolumeToLinearIndex( intIndex3, _VolBufferSize.xyz);
   return __VolBuffer[index1D];
 }
```

## <a name="shading-and-gradients"></a>Ombreggiatura e sfumature

Come ombreggiatura di un volume, ad esempio la MRI, per una visualizzazione utile. Il metodo principale è avere una "finestra di intensità" (min e max) all'interno della quale si vogliono visualizzare le intensità e scalare semplicemente in tale spazio per visualizzare l'intensità bianco e nero. Una "rampa di colori" può quindi essere applicata ai valori all'interno di tale intervallo e archiviata come trama, in modo che diverse parti dello spettro di intensità possano essere ombreggiate con colori diversi:

```
float4 ShadeVol( float intensity ) {
   float unitIntensity = saturate( intensity - IntensityMin / ( IntensityMax - IntensityMin ) );
   // Simple two point black and white intensity:
   color.rgba = unitIntensity;
   // Color ramp method:
   color.rgba = tex2d( ColorRampTexture, float2( unitIntensity, 0 ) );
```

In molte delle applicazioni vengono archiviati nel volume sia un valore di intensità non elaborato che un "indice di segmentazione" (per segmentare parti diverse come l'aspetto e l'osso; questi segmenti vengono creati da esperti in strumenti dedicati). Questo approccio può essere combinato con l'approccio precedente per inserire un colore diverso o anche una scala di colori diversa per ogni indice di segmento:

```
// Change color to match segment index (fade each segment towards black):
 color.rgb = SegmentColors[ segment_index ] * color.a; // brighter alpha gives brighter color
```

## <a name="volume-slicing-in-a-shader"></a>Sezione del volume in uno shader

Un ottimo primo passaggio consiste nel creare un "piano di sezione" che possa spostarsi nel volume, "secernerlo" e come i valori di analisi in ogni punto. Si presuppone che sia presente un cubo 'VolumeSpace', che rappresenta la posizione del volume nello spazio mondiale, che può essere usato come riferimento per posizionare i punti:

```
// In the vertex shader:
 float4 worldPos = mul(_Object2World, float4(input.vertex.xyz, 1));
 float4 volSpace = mul(_WorldToVolume, float4(worldPos, 1));
```

```
// In the pixel shader:
 float4 color = ShadeVol( SampleVol( volSpace ) );
```

## <a name="volume-tracing-in-shaders"></a>Traccia del volume negli shader

Come usare la GPU per eseguire la traccia dei subvolume (si possono eseguire alcuni voxel in profondità e quindi i livelli sui dati da dietro a davanti):

```
float4 AlphaBlend(float4 dst, float4 src) {
   float4 res = (src * src.a) + (dst - dst * src.a);
   res.a = src.a + (dst.a - dst.a*src.a);
   return res;
 }
 float4 volTraceSubVolume(float3 objPosStart, float3 cameraPosVolSpace) {
   float maxDepth = 0.15; // depth in volume space, customize!!!
   float numLoops = 10; // can be 400 on nice PC
   float4 curColor = float4(0, 0, 0, 0);
   // Figure out front and back volume coords to walk through:
   float3 frontCoord = objPosStart;
   float3 backCoord = frontPos + (normalize(cameraPosVolSpace - objPosStart) * maxDepth);
   float3 stepCoord = (frontCoord - backCoord) / numLoops;
   float3 curCoord = backCoord;
   // Add per-pixel random offset, avoids layer aliasing:
   curCoord += stepCoord * RandomFromPositionFast(objPosStart);
   // Walk from back to front (to make front appear in-front of back):
   for (float i = 0; i < numLoops; i++) {
     float intensity = SampleVol(curCoord);
     float4 shaded = ShadeVol(intensity);
     curColor = AlphaBlend(curColor, shaded);
     curCoord += stepCoord;
   }
   return curColor;
 }
```

```
// In the vertex shader:
 float4 worldPos = mul(_Object2World, float4(input.vertex.xyz, 1));
 float4 volSpace = mul(_WorldToVolume, float4(worldPos.xyz, 1));
 float4 cameraInVolSpace = mul(_WorldToVolume, float4(_WorldSpaceCameraPos.xyz, 1));
```

```
// In the pixel shader:
 float4 color = volTraceSubVolume( volSpace, cameraInVolSpace );
```

## <a name="whole-volume-rendering"></a>Rendering dell'intero volume

Modificando il codice subvolume precedente, si ottiene:

```
float4 volTraceSubVolume(float3 objPosStart, float3 cameraPosVolSpace) {
   float maxDepth = 1.73; // sqrt(3), max distance from point on cube to any other point on cube
   int maxSamples = 400; // just in case, keep this value within bounds
   // not shown: trim front and back positions to both be within the cube
   int distanceInVoxels = length(UnitVolumeToIntVolume(frontPos - backPos)); // measure distance in voxels
   int numLoops = min( distanceInVoxels, maxSamples ); // put a min on the voxels to sample
```

## <a name="mixed-resolution-scene-rendering"></a>Rendering della scena a risoluzione mista

Come eseguire il rendering di una parte della scena con una bassa risoluzione e rilasperla:
1. Configurare due fotocamere fuori schermo, una per seguire ogni occhio che aggiorna ogni fotogramma
2. Configurare due destinazioni di rendering a bassa risoluzione ,ovvero 200x200 ciascuna, in cui le fotocamere eseguono il rendering
3. Configurare un quad che si sposta davanti all'utente

Ogni frame:
1. Disegnare le destinazioni di rendering per ogni occhio a bassa risoluzione (dati di volume, shader costosi e così via)
2. Disegnare la scena normalmente come risoluzione completa (mesh, interfaccia utente e così via)
3. Disegnare un quad davanti all'utente, sulla scena, e proiettare il rendering a bassa res su tale
4. Risultato: combinazione visiva di elementi a risoluzione completa con dati di volume a bassa risoluzione ma ad alta densità

---
title: Case study - Ridimensionamento di Datascape tra dispositivi con prestazioni diverse
description: Questo case study informazioni dettagliate su come gli sviluppatori Microsoft hanno ottimizzato l'app Datascape per offrire un'esperienza accattivante tra i dispositivi con una gamma di funzionalità per le prestazioni.
author: danandersson
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: visore VR immersive, ottimizzazione delle prestazioni, REALTÀ VIRTUALE, case study
ms.openlocfilehash: d1c54f5fbe6843f9bf61af20b611c6aeb22b0704c209bfdb555fe57b95805cf9
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115195760"
---
# <a name="case-study---scaling-datascape-across-devices-with-different-performance"></a>Case study - Ridimensionamento di Datascape tra dispositivi con prestazioni diverse

Datascape è un'Windows Mixed Reality sviluppata internamente in Microsoft, in cui ci si è concentrati sulla visualizzazione dei dati meteo sui dati del terreno. L'applicazione esplora le informazioni dettagliate univoche che gli utenti ottengono dall'individuazione dei dati nella realtà mista circondando l'utente con la visualizzazione dei dati olografici.

Per Datascape si è voluto scegliere come destinazione un'ampia gamma di piattaforme con diverse funzionalità hardware, da Microsoft HoloLens Windows Mixed Reality visori VR immersive e da PC con tecnologia più bassa ai PC più recenti con GPU di fascia alta. La sfida principale consisteva nel rendere la scena visivamente accattivante nei dispositivi con funzionalità grafiche molto diverse durante l'esecuzione a una frequenza dei fotogrammi elevata.

Questo case study il processo e le tecniche usati per creare alcuni dei sistemi più a elevato utilizzo di GPU, descrivendo i problemi riscontrati e il modo in cui sono stati superati.

## <a name="transparency-and-overdraw"></a>Trasparenza e sovrapposizione

Il rendering principale ha problemi di trasparenza, perché la trasparenza può essere costosa in una GPU.

È possibile eseguire il rendering di una geometria a tinta unita front-to-back durante la scrittura nel buffer di profondità, bloccando l'eliminazione di tutti i pixel futuri che si trovano dietro tale pixel. Ciò impedisce ai pixel nascosti di eseguire il pixel shader, velocizzando in modo significativo il processo. Se la geometria è ordinata in modo ottimale, ogni pixel sullo schermo verrà disegnato una sola volta.

La geometria trasparente deve essere ordinata in primo piano e si basa sulla fusione dell'output del pixel shader al pixel corrente sullo schermo. Ciò può comportare che ogni pixel sullo schermo venga disegnato più volte per fotogramma, definito sovrapposizione.

Per HoloLens e i PC Mainstream, lo schermo può essere riempito solo alcune volte, rendendo problematico il rendering trasparente.

## <a name="introduction-to-datascape-scene-components"></a>Introduzione ai componenti della scena Datascape

Nella scena erano disponibili tre componenti principali: **l'interfaccia utente, la mappa** e **il meteo**. Si era a sapere fin dalle prime ore che gli effetti meteorologici richiederebbero tutto il tempo possibile per la GPU, quindi abbiamo progettato appositamente l'interfaccia utente e il terreno in modo da ridurre qualsiasi sovrapposizione.

L'interfaccia utente è stata rielaborata più volte per ridurre al minimo la quantità di sovrapposizione che produrrebbe. Abbiamo erroneo sul lato di una geometria più complessa invece di sovrapporre l'immagine trasparente l'una sull'altra per componenti come pulsanti incandescenti e panoramiche della mappa.

Per la mappa, è stato usato uno shader personalizzato che rimuove le funzionalità standard di Unity, ad esempio ombreggiature e illuminazione complessa, sostituendole con un semplice modello di illuminazione a singolo sole e un calcolo personalizzato del sole. Ciò ha prodotto una semplice pixel shader e liberare cicli GPU.

È stato possibile ottenere sia l'interfaccia utente che la mappa per il rendering in base al budget in cui non sono state necessarie modifiche a seconda dell'hardware. Tuttavia, la visualizzazione meteo, in particolare il rendering cloud, ha dimostrato di essere più difficile.

## <a name="background-on-cloud-data"></a>Informazioni di base sui dati cloud

I dati cloud sono stati scaricati dai server NOAA ( e sono stati disponibili in tre livelli 2D distinti, ognuno con l'altezza superiore e inferiore del cloud, nonché la densità del cloud per ogni cella della https://nomads.ncep.noaa.gov/) griglia. I dati sono stati elaborati in una trama di informazioni cloud in cui ogni componente è stato archiviato nel componente rosso, verde e blu della trama per un facile accesso alla GPU.

## <a name="geometry-clouds"></a>Cloud geometrici

Per assicurarsi che le macchine a potenza inferiore siano in grado di eseguire il rendering dei cloud, si è deciso di iniziare con un approccio che usasse una geometria solida per ridurre al minimo la sovrapposizione.

Per la prima volta si è provato a produrre le cloud generando una mesh di mappa ad altezza continua per ogni livello usando il raggio della trama di informazioni sulla nuvola per vertice per generare la forma. È stato usato uno shader geometrico per produrre i vertici sia nella parte superiore che nella parte inferiore del cloud generando forme di cloud solide. È stato usato il valore di densità della trama per colorare la nuvola con colori più scuri per le nubi più densi.

**Shader per la creazione dei vertici:**

```
v2g vert (appdata v)
{
    v2g o;
    o.height = tex2Dlod(_MainTex, float4(v.uv, 0, 0)).x;
    o.vertex = v.vertex;
    return o;
}
 
g2f GetOutput(v2g input, float heightDirection)
{
    g2f ret;
    float4 newBaseVert = input.vertex;
    newBaseVert.y += input.height * heightDirection * _HeigthScale;
    ret.vertex = UnityObjectToClipPos(newBaseVert);
    ret.height = input.height;
    return ret;
}
 
[maxvertexcount(6)]
void geo(triangle v2g p[3], inout TriangleStream<g2f> triStream)
{
    float heightTotal = p[0].height + p[1].height + p[2].height;
    if (heightTotal > 0)
    {
        triStream.Append(GetOutput(p[0], 1));
        triStream.Append(GetOutput(p[1], 1));
        triStream.Append(GetOutput(p[2], 1));
 
        triStream.RestartStrip();
 
        triStream.Append(GetOutput(p[2], -1));
        triStream.Append(GetOutput(p[1], -1));
        triStream.Append(GetOutput(p[0], -1));
    }
}
fixed4 frag (g2f i) : SV_Target
{
    clip(i.height - 0.1f);
 
    float3 finalColor = lerp(_LowColor, _HighColor, i.height);
    return float4(finalColor, 1);
}
```

È stato introdotto un modello di disturbo ridotto per ottenere maggiori dettagli sui dati reali. Per produrre bordi arrotondati della nuvola, abbiamo ritagliato i pixel nel pixel shader quando il valore del raggio interpolato ha raggiunto una soglia per eliminare i valori prossimi allo zero.

![Cloud geometrici](images/datascape-geometry-clouds-700px.jpg)

Poiché le cloud sono geometrie solide, è possibile eseguire il rendering prima del terreno per nascondere i dispendiosi pixel della mappa sottostanti per migliorare ulteriormente la frequenza dei fotogrammi. Questa soluzione è stata eseguita in modo ottimale in tutte le schede grafiche, dalle specifiche min alle schede grafiche di fascia alta, nonché in HoloLens, a causa dell'approccio di rendering di geometria continua.

## <a name="solid-particle-clouds"></a>Nubi di particelle solide

Ora abbiamo una soluzione di backup che produceva una rappresentazione discreta dei dati cloud, ma era un po' poco disponibile nel fattore "wow" e non trasmetteva l'aspetto volumetrico desiderato per i computer di fascia alta.

Il passaggio successivo consisteva nel creare le cloud rappresentandole con circa 100.000 particelle per produrre un aspetto più organico e volumetrico.

Se le particelle rimangono solide e si ordinano front-to-back, è comunque possibile trarre vantaggio dall'culling del buffer di profondità dei pixel dietro le particelle di cui è stato eseguito il rendering in precedenza, riducendo la sovrapposizione. Inoltre, con una soluzione basata su particelle, è possibile modificare la quantità di particelle usate per l'hardware diverso. Tuttavia, tutti i pixel devono comunque essere testati in profondità, con un sovraccarico aggiuntivo.

In primo luogo, sono state create posizioni di particelle intorno al punto centrale dell'esperienza all'avvio. Le particelle sono distribuite in modo più denso intorno al centro e meno in distanza. Tutte le particelle sono già ordinate dal centro alla parte posteriore, in modo che il rendering delle particelle più vicine sia stato eseguito per primo.

Un compute shader campionare la trama delle informazioni cloud per posizionare ogni particella all'altezza corretta e colorarla in base alla densità.

È stato *usato DrawProcedural per eseguire* il rendering di un quad per particella consentendo ai dati delle particelle di rimanere sempre nella GPU.

Ogni particella contiene sia un'altezza che un raggio. L'altezza era basata sui dati del cloud campionati dalla trama delle informazioni cloud e il raggio era basato sulla distribuzione iniziale in cui verrebbe calcolato per archiviare la distanza orizzontale dal vicino più vicino. I quad userebbero questi dati per orientarsi in modo angolato in base all'altezza, in modo che quando gli utenti li guardano orizzontalmente, l'altezza verrebbe visualizzata e, quando gli utenti li guardavano dall'alto verso il basso, l'area tra i suoi vicini verrebbe coperta.

![Forma particella](images/particle-shape-700px.png)

**Codice shader che mostra la distribuzione:**

```
ComputeBuffer cloudPointBuffer = new ComputeBuffer(6, quadPointsStride);
cloudPointBuffer.SetData(new[]
{
    new Vector2(-.5f, .5f),
    new Vector2(.5f, .5f),
    new Vector2(.5f, -.5f),
    new Vector2(.5f, -.5f),
    new Vector2(-.5f, -.5f),
    new Vector2(-.5f, .5f)
});
 
StructuredBuffer<float2> quadPoints;
StructuredBuffer<float3> particlePositions;
v2f vert(uint id : SV_VertexID, uint inst : SV_InstanceID)
{
    // Find the center of the quad, from local to world space
    float4 centerPoint = mul(unity_ObjectToWorld, float4(particlePositions[inst], 1));
 
    // Calculate y offset for each quad point
    float3 cameraForward = normalize(centerPoint - _WorldSpaceCameraPos);
    float y = dot(quadPoints[id].xy, cameraForward.xz);
 
    // Read out the particle data
    float radius = ...;
    float height = ...;
 
    // Set the position of the vert
    float4 finalPos = centerPoint + float4(quadPoints[id].x, y * height, quadPoints[id].y, 0) * radius;
    o.pos = mul(UNITY_MATRIX_VP, float4(finalPos.xyz, 1));
    o.uv = quadPoints[id].xy + 0.5;
 
    return o;
}
```

Poiché le particelle vengono ordinate front-to-back ed è stato ancora usato uno shader in stile tinta unita per ritagliare (non unire) pixel trasparenti, questa tecnica gestisce una quantità sorprendente di particelle, evitando costose e sovra disegnate anche nelle macchine a potenza inferiore.

## <a name="transparent-particle-clouds"></a>Cloud di particelle trasparenti

Le particelle solide hanno fornito un buon aspetto organico alla forma delle nubi, ma hanno comunque bisogno di qualcosa per vendere la fluffiness delle nubi. Si è deciso di provare una soluzione personalizzata per le schede grafiche di fascia alta in cui è possibile introdurre trasparenza.

A tale scopo, è stato semplicemente cambiato l'ordinamento iniziale delle particelle e lo shader è stato modificato in modo da usare le trame alfa.

![Cloud fluffy](images/fluffy-clouds-700px.jpg)

Ha avuto un aspetto eccezionale, ma ha dimostrato di essere troppo pesante anche per i computer più difficili perché avrebbe comportato il rendering di ogni pixel sullo schermo centinaia di volte.

## <a name="render-off-screen-with-lower-resolution"></a>Rendering fuori schermo con risoluzione inferiore

Per ridurre il numero di pixel sottoposti a rendering dalle cloud, è stato avviato il rendering in un buffer di risoluzione trimestrale (rispetto allo schermo) e l'estensione del risultato finale sullo schermo dopo che tutte le particelle sono state disegnate. Ciò ha dato un'approssimazione di circa 4 volte, ma ha fornito un paio di avvertenze.

**Codice per il rendering fuori schermo:**

```
cloudBlendingCommand = new CommandBuffer();
Camera.main.AddCommandBuffer(whenToComposite, cloudBlendingCommand);
 
cloudCamera.CopyFrom(Camera.main);
cloudCamera.rect = new Rect(0, 0, 1, 1);    //Adaptive rendering can set the main camera to a smaller rect
cloudCamera.clearFlags = CameraClearFlags.Color;
cloudCamera.backgroundColor = new Color(0, 0, 0, 1);
 
currentCloudTexture = RenderTexture.GetTemporary(Camera.main.pixelWidth / 2, Camera.main.pixelHeight / 2, 0);
cloudCamera.targetTexture = currentCloudTexture;
 
// Render clouds to the offscreen buffer
cloudCamera.Render();
cloudCamera.targetTexture = null;
 
// Blend low-res clouds to the main target
cloudBlendingCommand.Blit(currentCloudTexture, new RenderTargetIdentifier(BuiltinRenderTextureType.CurrentActive), blitMaterial);
```

In primo luogo, quando si esegue il rendering in un buffer fuori schermo, si perdono tutte le informazioni di profondità dalla scena principale, causando il rendering delle particelle dietro le particelle sulla cima della cima.

In secondo luogo, l'estensione del buffer ha introdotto anche artefatti sui bordi delle cloud in cui la modifica della risoluzione è stata evidente. Le due sezioni successive descrivono come sono stati risolti questi problemi.

## <a name="particle-depth-buffer"></a>Buffer di profondità particella

Per far coesistere le particelle con la geometria del mondo in cui una cima o un oggetto potrebbe coprire particelle dietro di essa, il buffer fuori schermo è stato popolato con un buffer di profondità contenente la geometria della scena principale. Per produrre un buffer di profondità di questo tipo, è stata creata una seconda fotocamera, che esegue il rendering solo della geometria continua e della profondità della scena.

È stata quindi usata la nuova trama nel pixel shader delle nubi per occludere i pixel. È stata usata la stessa trama per calcolare la distanza dalla geometria dietro un pixel della nuvola. Usando tale distanza e applicandola al valore alfa del pixel, ora abbiamo avuto l'effetto che le nubi si dissolvevano quando si avvicinano al terreno, rimuovendo eventuali riduzioni rigide in cui si incontrano particelle e terreno.

![Cloud misti nel terreno](images/clouds-blended-to-terrain-700px.jpg)

## <a name="sharpening-the-edges"></a>Affilatura dei bordi

Le nubi allungate erano quasi identiche a cloud di dimensioni normali al centro delle particelle o dove si sovrapponevano, ma mostravano alcuni artefatti ai bordi della nuvola. In caso contrario, i bordi appuntiti appaiono sfocati e sono stati introdotti effetti alias quando la fotocamera è stata spostata.

Questo problema è stato risolto eseguendo un semplice shader nel buffer fuori schermo per determinare dove si sono verificate modifiche di contrasto di grandi dimensioni (1). I pixel con modifiche di grandi dimensioni vengono inseriti in un nuovo buffer degli stencil (2). È stato quindi usato il buffer degli stencil per mascherare queste aree a contrasto elevato quando si applica di nuovo il buffer fuori schermo allo schermo, causando buchi all'interno e intorno alle cloud (3).

È stato quindi eseguito di nuovo il rendering di tutte le particelle in modalità schermo intero, ma questa volta è stato usato il buffer degli stencil per mascherare tutti gli elementi, a parte i bordi, determinando un set minimo di pixel toccati (4). Poiché il buffer dei comandi è già stato creato per le particelle, è stato sufficiente eseguirne il rendering nella nuova fotocamera.

![Avanzamento del rendering dei bordi cloud](images/cloud-steps-1-4-700px.jpg)

Il risultato finale era un bordo acuto con sezioni al centro poco costose delle cloud.

Anche se questa operazione era molto più veloce del rendering di tutte le particelle a schermo intero, il test di un pixel sul buffer degli stencil ha comunque un costo, quindi una grande quantità di sovrapposizione ha comunque un costo.

## <a name="culling-particles"></a>Culling delle particelle

Per l'effetto vento, abbiamo generato lunghe strisce di triangoli in un compute shader, creando molte frammenti di vento nel mondo. Anche se l'effetto del vento non era elevato sul fill rate a causa delle strisce sfasato generate, ha prodotto molte centinaia di migliaia di vertici, con conseguente carico elevato per il vertex shader.

Sono stati introdotti buffer di accodamento nel compute shader per alimentare un subset delle strisce eoliche da disegnare. Con una semplice logica di culling del frustum di visualizzazione nel compute shader, è possibile determinare se una striscia si trova all'esterno della visualizzazione della fotocamera e impedirne l'aggiunta al buffer di push. In questo modo la quantità di striping è stata ridotta in modo significativo, liberando alcuni cicli necessari nella GPU.

**Codice che illustra un buffer di accodamento:**

*Compute shader:*

```
AppendStructuredBuffer<int> culledParticleIdx;
 
if (show)
    culledParticleIdx.Append(id.x);
```

*Codice C#:*

```
protected void Awake() 
{
    // Create an append buffer, setting the maximum size and the contents stride length
    culledParticlesIdxBuffer = new ComputeBuffer(ParticleCount, sizeof(int), ComputeBufferType.Append);
 
    // Set up Args Buffer for Draw Procedural Indirect
    argsBuffer = new ComputeBuffer(4, sizeof(int), ComputeBufferType.IndirectArguments);
    argsBuffer.SetData(new int[] { DataVertCount, 0, 0, 0 });
}
 
protected void Update()
{
    // Reset the append buffer, and dispatch the compute shader normally
    culledParticlesIdxBuffer.SetCounterValue(0);
 
    computer.Dispatch(...)
 
    // Copy the append buffer count into the args buffer used by the Draw Procedural Indirect call
    ComputeBuffer.CopyCount(culledParticlesIdxBuffer, argsBuffer, dstOffset: 1);
    ribbonRenderCommand.DrawProceduralIndirect(Matrix4x4.identity, renderMaterial, 0, MeshTopology.Triangles, dataBuffer);
}
```

È stata tentata l'uso della stessa tecnica sulle particelle cloud, in cui le si ullava sul compute shader e si esegue il push solo delle particelle visibili per il rendering. Questa tecnica in realtà non ha risparmiato molto sulla GPU perché il collo di bottiglia principale era la quantità di pixel di cui è stato eseguito il rendering sullo schermo e non il costo del calcolo dei vertici.

L'altro problema di questa tecnica è che il buffer di accodamento viene popolato in ordine casuale a causa della natura parallelizzata del calcolo delle particelle, causando l'annullamento dell'ordinamento delle particelle ordinate, con conseguente sfarfallio delle particelle cloud.

Esistono tecniche per ordinare il buffer di push, ma la quantità limitata di miglioramento delle prestazioni ottenuto da particelle di culling probabilmente sarebbe stata compensata con un ordinamento aggiuntivo, quindi si è deciso di non eseguire questa ottimizzazione.

## <a name="adaptive-rendering"></a>Rendering adattivo

Per garantire una frequenza dei fotogrammi stabile in un'app con condizioni di rendering variabili, ad esempio una visualizzazione cloud rispetto a una visualizzazione chiara, è stato introdotto il rendering adattivo per l'app.

Il primo passaggio del rendering adattivo consiste nel misurare la GPU. A tale scopo, è stato inserito codice personalizzato nel buffer dei comandi DELLA GPU all'inizio e alla fine di un frame di cui è stato eseguito il rendering, acquisendo sia l'ora dello schermo dell'occhio sinistro che quello destro.

Misurando il tempo impiegato per il rendering e confrontandolo con la frequenza di aggiornamento desiderata, si è ottenuto un'idea di quanto sia stato possibile eliminare i fotogrammi.

Quando si avvicina il rilascio dei fotogrammi, il rendering viene adattato per renderlo più veloce. Un modo semplice per adattarsi è modificare le dimensioni del viewport dello schermo, richiedendo meno pixel per il rendering.

Usando *UnityEngine.XR.XRSettings.renderViewportScale,* il sistema compatta il viewport di destinazione e adatta automaticamente il risultato in base alla schermata. Una piccola modifica della scala è evidente nella geometria globale e un fattore di scala di 0,7 richiede la metà della quantità di pixel di cui eseguire il rendering.

![Scala del 70%, metà dei pixel](images/datascape-scaling-700px.jpg)

Quando si rileva che si stanno per eliminare i fotogrammi, si riduce la scala di un numero fisso e la si aumenta di nuovo quando si esegue di nuovo la velocità.

Anche se è stata deciso quale tecnica cloud usare in base alle funzionalità grafiche dell'hardware all'avvio, è possibile basarla sui dati provenienti dalla misurazione GPU per impedire al sistema di rimanere a bassa risoluzione per un lungo periodo di tempo, ma questo non ha avuto tempo per esplorarlo in Datascape.

## <a name="final-thoughts"></a>Considerazioni finali

Scegliere come destinazione un'ampia gamma di hardware è difficile e richiede una pianificazione.

È consigliabile iniziare a usare computer con potenza inferiore per acquisire familiarità con lo spazio problematico e sviluppare una soluzione di backup che verrà eseguita in tutti i computer. Progettare la soluzione fill rate, poiché i pixel saranno la risorsa più importante. Fare riferimento alla geometria a tinta unita sulla trasparenza.

Con una soluzione di backup, è quindi possibile iniziare a creare livelli più complessi per i computer di fascia alta o forse semplicemente migliorare la risoluzione della soluzione di backup.

Progettare per gli scenari peggiori e prendere in considerazione l'uso del rendering adattivo in situazioni complesse.

## <a name="about-the-authors"></a>Informazioni sugli autori

<table style="border:0">
<tr>
<td style="border:0" width="60px"><img alt="Picture of Robert Ferrese" width="60" height="60" src="images/robert-ferrese-60px.jpg"></td>
<td style="border:0"><b>Robert Robese</b><br>Software engineer @Microsoft</td>
</tr>
<tr>
<td style="border:0" width="60px"><img alt="Picture of Dan Andersson" width="60" height="60" src="images/dan-andersson-60px.jpg"></td>
<td style="border:0"><b>Dan Andersson</b><br>Software engineer @Microsoft</td>
</tr>
</table>


## <a name="see-also"></a>Vedi anche
* [Informazioni sulle prestazioni per la realtà mista](../develop/platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md)
* [Prestazioni Consigli per Unity](../develop/unity/performance-recommendations-for-unity.md)

 

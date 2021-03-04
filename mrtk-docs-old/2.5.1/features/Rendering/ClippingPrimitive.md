---
title: ClippingPrimitive
description: Documentazione sulle primitive di ritaglio con esempi in MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, primitiva di ritaglio,
ms.openlocfilehash: 4d82cc7e3d43e2ecd554e5815e36753a41ec9ba6
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/03/2021
ms.locfileid: "101782503"
---
# <a name="clipping-primitive"></a>Primitiva di ritaglio

I [`ClippingPrimitive`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) comportamenti consentono il [`plane`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPlane) [`sphere`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingSphere) ritaglio delle forme, e [`box`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingBox) con la possibilità di specificare il lato della primitiva a cui ritagliare (all'interno o all'esterno) se usato con MRTK shader.

![Gizmos di ritaglio primitivi](../images/mrtk-standard-shader/MRTK_PrimitiveClippingGizmos.gif)

> [!NOTE]
> [`ClippingPrimitives`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) usare le istruzioni di ritaglio [/eliminazione](https://developer.download.nvidia.com/cg/clip.html) negli shader e disabilitare la capacità di Unity di eseguire il batch dei renderer ritagliati. Tenere presenti queste implicazioni sulle prestazioni quando si utilizzano le primitive di ritaglio.

[`ClippingPlane.cs`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPlane), [`ClippingSphere.cs`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingSphere) e [`ClippingBox.cs`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingBox) possono essere usati per controllare facilmente le proprietà primitive di ritaglio. Usare questi componenti con gli shader seguenti per sfruttare gli scenari di ritaglio.

- *Toolkit di realtà mista/standard*
- *Toolkit di realtà mista/TextMeshPro*
- *Toolkit di realtà mista/Text3DShader*

## <a name="examples"></a>Esempio

Le scene **ClippingExamples** e **MaterialGallery** illustrano l'utilizzo dei [`ClippingPrimitive`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) comportamenti ed è possibile trovare in: MRTK/examples/Demos/StandardShader/scenes/

## <a name="advanced-usage"></a>Utilizzo avanzato

Per impostazione predefinita, solo uno [`ClippingPrimitive`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) può ritagliare un [renderer](https://docs.unity3d.com/ScriptReference/Renderer.html) alla volta. Se il progetto richiede più di uno [`ClippingPrimitive`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) per influenzare un [renderer](https://docs.unity3d.com/ScriptReference/Renderer.html)  , il codice di esempio seguente illustra come ottenere questo risultato.

> [!NOTE]
> Se [`ClippingPrimitives`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) si dispone di più clip, un [renderer](https://docs.unity3d.com/ScriptReference/Renderer.html) aumenterà pixel shader istruzioni e influirà sulle prestazioni. Per profilare queste modifiche all'interno del progetto.

*Modalità di visualizzazione di due diverse [`ClippingPrimitives`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) clip di un rendering. Ad esempio a [`ClippingSphere`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingSphere) e [`ClippingBox`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingBox) allo stesso tempo:*

```C#
// Within MRTK/Core/StandardAssets/Shaders/MixedRealityStandard.shader (or another MRTK shader) change:

#pragma multi_compile _ _CLIPPING_PLANE _CLIPPING_SPHERE _CLIPPING_BOX

// to:

#pragma multi_compile _ _CLIPPING_PLANE
#pragma multi_compile _ _CLIPPING_SPHERE
#pragma multi_compile _ _CLIPPING_BOX
```

> [!NOTE]
> La modifica precedente comporterà un ulteriore tempo di compilazione dello shader.

*Modalità di rendering di due della stessa [`ClippingPrimitives`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) clip. Ad esempio due [`ClippingBoxes`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingBox) allo stesso tempo:*

```C#
// 1) Add the below MonoBehaviour to your project:

[ExecuteInEditMode]
public class SecondClippingBox : ClippingBox
{
    /// <inheritdoc />
    protected override string Keyword
    {
        get { return "_CLIPPING_BOX2"; }
    }

    /// <inheritdoc />
    protected override string ClippingSideProperty
    {
        get { return "_ClipBoxSide2"; }
    }

    /// <inheritdoc />
    protected override void Initialize()
    {
        base.Initialize();

        clipBoxSizeID = Shader.PropertyToID("_ClipBoxSize2");
        clipBoxInverseTransformID = Shader.PropertyToID("_ClipBoxInverseTransform2");
    }
}

// 2) Within MRTK/Core/StandardAssets/Shaders/MixedRealityStandard.shader (or another MRTK shader) add the following multi_compile pragma:

#pragma multi_compile _ _CLIPPING_BOX2

// 3) In the same shader change:

#if defined(_CLIPPING_PLANE) || defined(_CLIPPING_SPHERE) || defined(_CLIPPING_BOX)

// to:

#if defined(_CLIPPING_PLANE) || defined(_CLIPPING_SPHERE) || defined(_CLIPPING_BOX) || defined(_CLIPPING_BOX2)

// 4) In the same shader add the following shader variables:

#if defined(_CLIPPING_BOX2)
    fixed _ClipBoxSide2;
    float4 _ClipBoxSize2;
    float4x4 _ClipBoxInverseTransform2;
#endif

// 5) In the same shader change:

#if defined(_CLIPPING_BOX)
    primitiveDistance = min(primitiveDistance, PointVsBox(i.worldPosition.xyz, _ClipBoxSize.xyz, _ClipBoxInverseTransform) * _ClipBoxSide);
#endif

// to:

#if defined(_CLIPPING_BOX)
    primitiveDistance = min(primitiveDistance, PointVsBox(i.worldPosition.xyz, _ClipBoxSize.xyz, _ClipBoxInverseTransform) * _ClipBoxSide);
#endif
#if defined(_CLIPPING_BOX2)
    primitiveDistance = min(primitiveDistance, PointVsBox(i.worldPosition.xyz, _ClipBoxSize2.xyz, _ClipBoxInverseTransform2) * _ClipBoxSide2);
#endif
```

Aggiungere infine un [`ClippingBox`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingBox) componente e SecondClippingBox alla scena e specificare lo stesso renderer per entrambe le caselle. Il renderer dovrebbe ora essere ritagliato da entrambe le caselle simultaneamente.

## <a name="see-also"></a>Vedi anche

- [Shader standard MRTK](MRTKStandardShader.md)

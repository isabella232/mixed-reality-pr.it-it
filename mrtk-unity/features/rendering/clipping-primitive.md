---
title: Primitiva di ritaglio
description: Documentazione sulle primitive di ritaglio con esempi in MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realtà mista, sviluppo, MRTK, primitiva di ritaglio,
ms.openlocfilehash: 35b7166045986df34eaf2c23161efc6379160ead
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/19/2021
ms.locfileid: "110145199"
---
# <a name="clipping-primitive"></a>Primitiva di ritaglio

I comportamenti consentono il ritaglio delle forme performanti , e con la possibilità di specificare il lato della primitiva su cui ritagliare (all'interno o all'esterno) quando viene usato con [`ClippingPrimitive`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) [`plane`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPlane) shader [`sphere`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingSphere) [`box`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingBox) MRTK.

![gizmo di ritaglio primitivo](../images/mrtk-standard-shader/MRTK_PrimitiveClippingGizmos.gif)

> [!NOTE]
> [`ClippingPrimitives`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) usare le [istruzioni clip/discard](https://developer.download.nvidia.com/cg/clip.html) all'interno degli shader e disabilitare la possibilità di Unity di troncato in batch. Tenere presenti queste implicazioni in termini di prestazioni quando si utilizzano primitive di ritaglio.

[`ClippingPlane.cs`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPlane), [`ClippingSphere.cs`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingSphere) e possono essere usati per controllare facilmente le proprietà [`ClippingBox.cs`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingBox) primitive di ritaglio. Usare questi componenti con gli shader seguenti per sfruttare gli scenari di ritaglio.

- *Mixed Reality Toolkit/Standard*
- *Mixed Reality Toolkit/TextMeshPro*
- *Mixed Reality Toolkit/Text3DShader*

## <a name="examples"></a>Esempio

Le **scene ClippingExamples** e **MaterialGallery** illustrano l'uso dei comportamenti e sono disponibili [`ClippingPrimitive`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) in: MRTK/Examples/Demos/StandardShader/Scenes/

## <a name="advanced-usage"></a>Utilizzo avanzato

Per impostazione predefinita, solo [`ClippingPrimitive`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) uno può ritagliare [un renderer](https://docs.unity3d.com/ScriptReference/Renderer.html) alla volta. Se il progetto richiede più di uno [`ClippingPrimitive`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) per influire su un [renderer,](https://docs.unity3d.com/ScriptReference/Renderer.html)  il codice di esempio seguente illustra come ottenere questo risultato.

> [!NOTE]
> La presenza [`ClippingPrimitives`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) di più clip di un [renderer](https://docs.unity3d.com/ScriptReference/Renderer.html) aumenta pixel shader istruzioni e influisce sulle prestazioni. Profilare queste modifiche all'interno del progetto.

*Come fare in modo che due [`ClippingPrimitives`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) clip diversi eseere un rendering. Ad esempio, [`ClippingSphere`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingSphere) e [`ClippingBox`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingBox) contemporaneamente:*

```C#
// Within MRTK/Core/StandardAssets/Shaders/MixedRealityStandard.shader (or another MRTK shader) change:

#pragma multi_compile _ _CLIPPING_PLANE _CLIPPING_SPHERE _CLIPPING_BOX

// to:

#pragma multi_compile _ _CLIPPING_PLANE
#pragma multi_compile _ _CLIPPING_SPHERE
#pragma multi_compile _ _CLIPPING_BOX
```

> [!NOTE]
> La modifica precedente comporta un tempo di compilazione dello shader aggiuntivo.

*Come fare in modo che due dello stesso [`ClippingPrimitives`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) clip esere un rendering. Ad esempio due [`ClippingBoxes`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingBox) contemporaneamente:*

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

Infine, aggiungere un [`ClippingBox`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingBox) componente e SecondClippingBox alla scena e specificare lo stesso renderer per entrambe le caselle. Il renderer dovrebbe ora essere ritagliato da entrambe le caselle contemporaneamente.

## <a name="see-also"></a>Vedi anche

- [MRTK Standard Shader](mrtk-standard-shader.md)

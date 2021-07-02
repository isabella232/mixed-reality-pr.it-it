---
title: Primitiva di ritaglio
description: Documentazione sulle primitive di ritaglio con esempi in MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, primitiva di ritaglio,
ms.openlocfilehash: c3331084f87ccc57208426910d84ed7bef457bc1
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176746"
---
# <a name="clipping-primitive"></a><span data-ttu-id="e12fe-104">Primitiva di ritaglio</span><span class="sxs-lookup"><span data-stu-id="e12fe-104">Clipping primitive</span></span>

<span data-ttu-id="e12fe-105">I comportamenti consentono il ritaglio delle forme performanti , e con la possibilità di specificare il lato della primitiva su cui ritagliare (all'interno o all'esterno) quando viene usato con [`ClippingPrimitive`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) [`plane`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPlane) shader [`sphere`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingSphere) [`box`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingBox) MRTK.</span><span class="sxs-lookup"><span data-stu-id="e12fe-105">The [`ClippingPrimitive`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) behaviors allow for performant [`plane`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPlane), [`sphere`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingSphere), and [`box`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingBox) shape clipping with the ability to specify which side of the primitive to clip against (inside or outside) when used with MRTK shaders.</span></span>

![gizmo di ritaglio primitivo](../images/mrtk-standard-shader/MRTK_PrimitiveClippingGizmos.gif)

> [!NOTE]
> <span data-ttu-id="e12fe-107">[`ClippingPrimitives`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) usare le [istruzioni clip/discard](https://developer.download.nvidia.com/cg/clip.html) all'interno degli shader e disabilitare la possibilità di Unity di troncato in batch.</span><span class="sxs-lookup"><span data-stu-id="e12fe-107">[`ClippingPrimitives`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) utilize [clip/discard](https://developer.download.nvidia.com/cg/clip.html) instructions within shaders and disable Unity's ability to batch clipped renderers.</span></span> <span data-ttu-id="e12fe-108">Tenere presenti queste implicazioni in termini di prestazioni quando si utilizzano primitive di ritaglio.</span><span class="sxs-lookup"><span data-stu-id="e12fe-108">Take these performance implications in mind when utilizing clipping primitives.</span></span>

<span data-ttu-id="e12fe-109">[`ClippingPlane.cs`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPlane), [`ClippingSphere.cs`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingSphere) e possono essere usati per controllare facilmente le proprietà [`ClippingBox.cs`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingBox) primitive di ritaglio.</span><span class="sxs-lookup"><span data-stu-id="e12fe-109">[`ClippingPlane.cs`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPlane), [`ClippingSphere.cs`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingSphere), and [`ClippingBox.cs`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingBox) can be used to easily control clipping primitive properties.</span></span> <span data-ttu-id="e12fe-110">Usare questi componenti con gli shader seguenti per sfruttare gli scenari di ritaglio.</span><span class="sxs-lookup"><span data-stu-id="e12fe-110">Use these components with the following shaders to leverage clipping scenarios.</span></span>

- <span data-ttu-id="e12fe-111">*Realtà mista Toolkit/Standard*</span><span class="sxs-lookup"><span data-stu-id="e12fe-111">*Mixed Reality Toolkit/Standard*</span></span>
- <span data-ttu-id="e12fe-112">*Realtà mista Toolkit/TextMeshPro*</span><span class="sxs-lookup"><span data-stu-id="e12fe-112">*Mixed Reality Toolkit/TextMeshPro*</span></span>
- <span data-ttu-id="e12fe-113">*Realtà mista Toolkit/Text3DShader*</span><span class="sxs-lookup"><span data-stu-id="e12fe-113">*Mixed Reality Toolkit/Text3DShader*</span></span>

## <a name="examples"></a><span data-ttu-id="e12fe-114">Esempio</span><span class="sxs-lookup"><span data-stu-id="e12fe-114">Examples</span></span>

<span data-ttu-id="e12fe-115">Le **scene ClippingExamples** e **MaterialGallery** illustrano l'uso dei comportamenti e sono disponibili [`ClippingPrimitive`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) in: MRTK/Examples/Demos/StandardShader/Scenes/</span><span class="sxs-lookup"><span data-stu-id="e12fe-115">The **ClippingExamples** and **MaterialGallery** scenes demonstrate usage of the [`ClippingPrimitive`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) behaviors, and can be found at: MRTK/Examples/Demos/StandardShader/Scenes/</span></span>

## <a name="advanced-usage"></a><span data-ttu-id="e12fe-116">Utilizzo avanzato</span><span class="sxs-lookup"><span data-stu-id="e12fe-116">Advanced Usage</span></span>

<span data-ttu-id="e12fe-117">Per impostazione predefinita, [`ClippingPrimitive`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) solo uno può ritagliare un [renderer](https://docs.unity3d.com/ScriptReference/Renderer.html) alla volta.</span><span class="sxs-lookup"><span data-stu-id="e12fe-117">By default only one [`ClippingPrimitive`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) can clip a [renderer](https://docs.unity3d.com/ScriptReference/Renderer.html) at a time.</span></span> <span data-ttu-id="e12fe-118">Se il progetto richiede più di uno [`ClippingPrimitive`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) per influire su un [renderer,](https://docs.unity3d.com/ScriptReference/Renderer.html)  il codice di esempio seguente illustra come ottenere questo risultato.</span><span class="sxs-lookup"><span data-stu-id="e12fe-118">If your project requires more than one [`ClippingPrimitive`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) to influence a [renderer](https://docs.unity3d.com/ScriptReference/Renderer.html)  the sample code below demonstrates how to achieve this.</span></span>

> [!NOTE]
> <span data-ttu-id="e12fe-119">La presenza [`ClippingPrimitives`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) di più clip di un [renderer](https://docs.unity3d.com/ScriptReference/Renderer.html) aumenta pixel shader istruzioni e influisce sulle prestazioni.</span><span class="sxs-lookup"><span data-stu-id="e12fe-119">Having multiple [`ClippingPrimitives`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) clip a [renderer](https://docs.unity3d.com/ScriptReference/Renderer.html) will increase pixel shader instructions and will impact performance.</span></span> <span data-ttu-id="e12fe-120">Profilare queste modifiche all'interno del progetto.</span><span class="sxs-lookup"><span data-stu-id="e12fe-120">Please profile these changes within your project.</span></span>

<span data-ttu-id="e12fe-121">*Come eseguire il rendering di [`ClippingPrimitives`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) due clip diverse. Ad esempio, [`ClippingSphere`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingSphere) e [`ClippingBox`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingBox) contemporaneamente:*</span><span class="sxs-lookup"><span data-stu-id="e12fe-121">*How to have two different [`ClippingPrimitives`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) clip a render. For example a [`ClippingSphere`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingSphere) and [`ClippingBox`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingBox) at the same time:*</span></span>

```C#
// Within MRTK/Core/StandardAssets/Shaders/MixedRealityStandard.shader (or another MRTK shader) change:

#pragma multi_compile _ _CLIPPING_PLANE _CLIPPING_SPHERE _CLIPPING_BOX

// to:

#pragma multi_compile _ _CLIPPING_PLANE
#pragma multi_compile _ _CLIPPING_SPHERE
#pragma multi_compile _ _CLIPPING_BOX
```

> [!NOTE]
> <span data-ttu-id="e12fe-122">La modifica precedente comporta un tempo di compilazione dello shader aggiuntivo.</span><span class="sxs-lookup"><span data-stu-id="e12fe-122">The above change will incur additional shader compilation time.</span></span>

<span data-ttu-id="e12fe-123">*Come fare in modo che due dello stesso [`ClippingPrimitives`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) clip esere un rendering. Ad esempio due [`ClippingBoxes`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingBox) contemporaneamente:*</span><span class="sxs-lookup"><span data-stu-id="e12fe-123">*How to have two of the same [`ClippingPrimitives`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingPrimitive) clip a render. For example two [`ClippingBoxes`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingBox) at the same time:*</span></span>

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

<span data-ttu-id="e12fe-124">Infine, aggiungere un [`ClippingBox`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingBox) componente e SecondClippingBox alla scena e specificare lo stesso renderer per entrambe le caselle.</span><span class="sxs-lookup"><span data-stu-id="e12fe-124">Finally, add a [`ClippingBox`](xref:Microsoft.MixedReality.Toolkit.Utilities.ClippingBox) and SecondClippingBox component to your scene and specify the same renderer for both boxes.</span></span> <span data-ttu-id="e12fe-125">Il renderer dovrebbe ora essere ritagliato da entrambe le caselle contemporaneamente.</span><span class="sxs-lookup"><span data-stu-id="e12fe-125">The renderer should now be clipped by both boxes simultaneously.</span></span>

## <a name="see-also"></a><span data-ttu-id="e12fe-126">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="e12fe-126">See also</span></span>

- [<span data-ttu-id="e12fe-127">MRTK Standard Shader</span><span class="sxs-lookup"><span data-stu-id="e12fe-127">MRTK Standard Shader</span></span>](mrtk-standard-shader.md)

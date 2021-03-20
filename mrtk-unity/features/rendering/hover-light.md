---
title: HoverLight
description: Documentazione su HoverLight con esempi in MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, hover Light,
ms.openlocfilehash: 60662245111abe39285b3b8ac2cfb9d71e1300ed
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2021
ms.locfileid: "104702287"
---
# <a name="hover-light"></a><span data-ttu-id="614b1-104">Luce al passaggio del mouse</span><span class="sxs-lookup"><span data-stu-id="614b1-104">Hover Light</span></span>

<span data-ttu-id="614b1-105">Un [`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) è un paradigma del [sistema di progettazione Fluent](https://www.microsoft.com/design/fluent/) che simula una [luce puntiforme](https://docs.unity3d.com/Manual/Lighting.html) posizionata vicino alla superficie di un oggetto.</span><span class="sxs-lookup"><span data-stu-id="614b1-105">A [`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) is a [Fluent Design System](https://www.microsoft.com/design/fluent/) paradigm that mimics a [point light](https://docs.unity3d.com/Manual/Lighting.html) hovering near the surface of an object.</span></span> <span data-ttu-id="614b1-106">Spesso usato per le interazioni lontane, l'applicazione può controllare le proprietà di una luce del passaggio del mouse tramite il [`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) componente.</span><span class="sxs-lookup"><span data-stu-id="614b1-106">Often used for far away interactions, the application can control the properties of a Hover Light via the [`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) component.</span></span>

<span data-ttu-id="614b1-107">Affinché un materiale venga influenzato da un [`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) Toolkit di *realtà mista o* da un shader standard, è necessario che sia abilitata la proprietà del *passaggio del mouse* .</span><span class="sxs-lookup"><span data-stu-id="614b1-107">For a material to be influenced by a [`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) the *Mixed Reality Toolkit/Standard* shader must be used and the *Hover Light* property must be enabled.</span></span>

> [!Note]
> <span data-ttu-id="614b1-108">Lo shader MRTK/standard supporta fino a due per [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) impostazione predefinita, ma viene scalato in modo da supportare quattro e poi dieci con l'aggiunta di più luci alla scena.</span><span class="sxs-lookup"><span data-stu-id="614b1-108">The MRTK/Standard shader supports up to two [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) by default, but will scale to support four and then ten as more lights are added to the scene.</span></span>

## <a name="examples"></a><span data-ttu-id="614b1-109">Esempio</span><span class="sxs-lookup"><span data-stu-id="614b1-109">Examples</span></span>

<span data-ttu-id="614b1-110">La maggior parte delle scene all'interno della MRTK utilizza un [`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) .</span><span class="sxs-lookup"><span data-stu-id="614b1-110">Most scenes within the MRTK utilize a [`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight).</span></span> <span data-ttu-id="614b1-111">Il caso d'uso più comune è reperibile in MRTK/SDK/features/UX/prefabrics/Cursors/DefaultCursor. prefabrical</span><span class="sxs-lookup"><span data-stu-id="614b1-111">The most common use case can be found on the MRTK/SDK/Features/UX/Prefabs/Cursors/DefaultCursor.prefab</span></span>

<span data-ttu-id="614b1-112">La scena **HoverLightExamples** illustra anche l'uso dei [`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) comportamenti ed è disponibile all'indirizzo: MRTK/examples/Demos/StandardShader/scenes/</span><span class="sxs-lookup"><span data-stu-id="614b1-112">The **HoverLightExamples** scene also demonstrates usage of [`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) behaviors, and can be found at: MRTK/Examples/Demos/StandardShader/Scenes/</span></span>

## <a name="advanced-usage"></a><span data-ttu-id="614b1-113">Utilizzo avanzato</span><span class="sxs-lookup"><span data-stu-id="614b1-113">Advanced Usage</span></span>

<span data-ttu-id="614b1-114">Solo dieci [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) può illuminare un [materiale](https://docs.unity3d.com/ScriptReference/Material.html) alla volta.</span><span class="sxs-lookup"><span data-stu-id="614b1-114">Only ten [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) can illuminate a [material](https://docs.unity3d.com/ScriptReference/Material.html) at a time.</span></span> <span data-ttu-id="614b1-115">Se il progetto richiede più di dieci [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) per influenzare un [materiale](https://docs.unity3d.com/ScriptReference/Material.html) , nel codice di esempio riportato di seguito viene illustrato come ottenere questo risultato.</span><span class="sxs-lookup"><span data-stu-id="614b1-115">If your project requires more than ten [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) to influence a [material](https://docs.unity3d.com/ScriptReference/Material.html) the sample code below demonstrates how to achieve this.</span></span>

> [!Note]
> <span data-ttu-id="614b1-116">La presenza [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) di molti [materiali](https://docs.unity3d.com/ScriptReference/Material.html) illuminati aumenterà pixel shader istruzioni e influirà sulle prestazioni.</span><span class="sxs-lookup"><span data-stu-id="614b1-116">Having many [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) illuminate a [material](https://docs.unity3d.com/ScriptReference/Material.html) will increase pixel shader instructions and will impact performance.</span></span> <span data-ttu-id="614b1-117">**Per profilare queste modifiche all'interno del progetto.**</span><span class="sxs-lookup"><span data-stu-id="614b1-117">**Please profile these changes within your project.**</span></span>

<span data-ttu-id="614b1-118">*Come aumentare il numero di disponibili [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) da dieci a dodici.*</span><span class="sxs-lookup"><span data-stu-id="614b1-118">*How to increase the number of available [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) from ten to twelve.*</span></span>

```C#
// 1) Within MRTK/Core/StandardAssets/Shaders/MixedRealityStandard.shader change:

#if defined(_HOVER_LIGHT_HIGH)
#define HOVER_LIGHT_COUNT 10

// to:

#if defined(_HOVER_LIGHT_HIGH)
#define HOVER_LIGHT_COUNT 12

// 2) Within MRTK/Core/Utilities/StandardShader/HoverLight.cs change:

private const int hoverLightCountHigh = 10;

// to:

private const int hoverLightCountHigh = 12;
```

> [!NOTE]
> <span data-ttu-id="614b1-119">Se Unity registra un avviso simile a quello riportato di seguito, è necessario riavviare Unity prima che le modifiche siano effettive.</span><span class="sxs-lookup"><span data-stu-id="614b1-119">If Unity logs a warning similar to below then you must restart Unity before your changes will take effect.</span></span>
>
> `Property (_HoverLightData) exceeds previous array size (24 vs 20). Cap to previous >size.`

## <a name="see-also"></a><span data-ttu-id="614b1-120">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="614b1-120">See also</span></span>

* [<span data-ttu-id="614b1-121">Shader standard MRTK</span><span class="sxs-lookup"><span data-stu-id="614b1-121">MRTK Standard Shader</span></span>](mrtk-standard-shader.md)

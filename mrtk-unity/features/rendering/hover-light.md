---
title: Luce del passaggio del mouse
description: Documentazione su HoverLight con esempi in MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realtà mista, sviluppo, MRTK, Hover Light,
ms.openlocfilehash: b98dff0dd3ff0312f6ce607a5fb8a26f94959ff2
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/19/2021
ms.locfileid: "110145172"
---
# <a name="hover-light"></a><span data-ttu-id="0be50-104">Luce del passaggio del mouse</span><span class="sxs-lookup"><span data-stu-id="0be50-104">Hover Light</span></span>

<span data-ttu-id="0be50-105">Un [`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) è un [paradigma Fluent Design System](https://www.microsoft.com/design/fluent/) che [](https://docs.unity3d.com/Manual/Lighting.html) simula una luce del punto che si sposta vicino alla superficie di un oggetto.</span><span class="sxs-lookup"><span data-stu-id="0be50-105">A [`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) is a [Fluent Design System](https://www.microsoft.com/design/fluent/) paradigm that mimics a [point light](https://docs.unity3d.com/Manual/Lighting.html) hovering near the surface of an object.</span></span> <span data-ttu-id="0be50-106">Spesso usata per interazioni di distanza, l'applicazione può controllare le proprietà di una luce al passaggio del mouse tramite il [`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) componente .</span><span class="sxs-lookup"><span data-stu-id="0be50-106">Often used for far away interactions, the application can control the properties of a Hover Light via the [`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) component.</span></span>

<span data-ttu-id="0be50-107">Perché un materiale sia influenzato da uno [`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) shader *Mixed Reality Toolkit/Standard,* è necessario che sia abilitata la proprietà *Hover Light.*</span><span class="sxs-lookup"><span data-stu-id="0be50-107">For a material to be influenced by a [`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) the *Mixed Reality Toolkit/Standard* shader must be used and the *Hover Light* property must be enabled.</span></span>

> [!Note]
> <span data-ttu-id="0be50-108">Lo shader MRTK/Standard supporta fino a due per impostazione predefinita, ma verrà ridimensionato in modo da supportare quattro e quindi dieci quando vengono aggiunte altre luci [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) alla scena.</span><span class="sxs-lookup"><span data-stu-id="0be50-108">The MRTK/Standard shader supports up to two [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) by default, but will scale to support four and then ten as more lights are added to the scene.</span></span>

## <a name="examples"></a><span data-ttu-id="0be50-109">Esempio</span><span class="sxs-lookup"><span data-stu-id="0be50-109">Examples</span></span>

<span data-ttu-id="0be50-110">La maggior parte delle scene all'interno di MRTK usa un [`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) oggetto .</span><span class="sxs-lookup"><span data-stu-id="0be50-110">Most scenes within the MRTK utilize a [`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight).</span></span> <span data-ttu-id="0be50-111">Il caso d'uso più comune è disponibile in MRTK/SDK/Features/UX/Prefabs/Cursors/DefaultCursor.prefab</span><span class="sxs-lookup"><span data-stu-id="0be50-111">The most common use case can be found on the MRTK/SDK/Features/UX/Prefabs/Cursors/DefaultCursor.prefab</span></span>

<span data-ttu-id="0be50-112">La **scena HoverLightExamples** illustra anche l'uso dei comportamenti ed è disponibile [`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) in: MRTK/Examples/Demos/StandardShader/Scenes/</span><span class="sxs-lookup"><span data-stu-id="0be50-112">The **HoverLightExamples** scene also demonstrates usage of [`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) behaviors, and can be found at: MRTK/Examples/Demos/StandardShader/Scenes/</span></span>

## <a name="advanced-usage"></a><span data-ttu-id="0be50-113">Utilizzo avanzato</span><span class="sxs-lookup"><span data-stu-id="0be50-113">Advanced Usage</span></span>

<span data-ttu-id="0be50-114">Solo dieci [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) possono illuminare [un materiale](https://docs.unity3d.com/ScriptReference/Material.html) alla volta.</span><span class="sxs-lookup"><span data-stu-id="0be50-114">Only ten [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) can illuminate a [material](https://docs.unity3d.com/ScriptReference/Material.html) at a time.</span></span> <span data-ttu-id="0be50-115">Se il progetto richiede più di dieci elementi per influenzare un materiale, il codice di esempio seguente [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) illustra come ottenere questo risultato. [](https://docs.unity3d.com/ScriptReference/Material.html)</span><span class="sxs-lookup"><span data-stu-id="0be50-115">If your project requires more than ten [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) to influence a [material](https://docs.unity3d.com/ScriptReference/Material.html) the sample code below demonstrates how to achieve this.</span></span>

> [!Note]
> <span data-ttu-id="0be50-116">La presenza [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) di molti elementi che [illuminano un](https://docs.unity3d.com/ScriptReference/Material.html) materiale aumenta pixel shader istruzioni e influisce sulle prestazioni.</span><span class="sxs-lookup"><span data-stu-id="0be50-116">Having many [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) illuminate a [material](https://docs.unity3d.com/ScriptReference/Material.html) will increase pixel shader instructions and will impact performance.</span></span> <span data-ttu-id="0be50-117">**Profilare queste modifiche all'interno del progetto.**</span><span class="sxs-lookup"><span data-stu-id="0be50-117">**Please profile these changes within your project.**</span></span>

<span data-ttu-id="0be50-118">*Come aumentare il numero di disponibili [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) da dieci a dodici.*</span><span class="sxs-lookup"><span data-stu-id="0be50-118">*How to increase the number of available [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) from ten to twelve.*</span></span>

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
> <span data-ttu-id="0be50-119">Se Unity registra un avviso simile al seguente, è necessario riavviare Unity prima che le modifiche avranno effetto.</span><span class="sxs-lookup"><span data-stu-id="0be50-119">If Unity logs a warning similar to below then you must restart Unity before your changes will take effect.</span></span>
>
> `Property (_HoverLightData) exceeds previous array size (24 vs 20). Cap to previous >size.`

## <a name="see-also"></a><span data-ttu-id="0be50-120">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="0be50-120">See also</span></span>

* [<span data-ttu-id="0be50-121">MRTK Standard Shader</span><span class="sxs-lookup"><span data-stu-id="0be50-121">MRTK Standard Shader</span></span>](mrtk-standard-shader.md)

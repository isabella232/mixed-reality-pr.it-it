---
title: HoverLight
description: Documentazione su HoverLight con esempi in MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, hover Light,
ms.openlocfilehash: 129ba1fc0614e414d3f3a67a0e633e87279b7f6c
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/03/2021
ms.locfileid: "101782953"
---
# <a name="hover-light"></a><span data-ttu-id="31872-104">Luce al passaggio del mouse</span><span class="sxs-lookup"><span data-stu-id="31872-104">Hover Light</span></span>

<span data-ttu-id="31872-105">Un [`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) è un paradigma del [sistema di progettazione Fluent](https://www.microsoft.com/design/fluent/) che simula una [luce puntiforme](https://docs.unity3d.com/Manual/Lighting.html) posizionata vicino alla superficie di un oggetto.</span><span class="sxs-lookup"><span data-stu-id="31872-105">A [`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) is a [Fluent Design System](https://www.microsoft.com/design/fluent/) paradigm that mimics a [point light](https://docs.unity3d.com/Manual/Lighting.html) hovering near the surface of an object.</span></span> <span data-ttu-id="31872-106">Spesso usato per le interazioni lontane, l'applicazione può controllare le proprietà di una luce del passaggio del mouse tramite il [`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) componente.</span><span class="sxs-lookup"><span data-stu-id="31872-106">Often used for far away interactions, the application can control the properties of a Hover Light via the [`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) component.</span></span>

<span data-ttu-id="31872-107">Affinché un materiale venga influenzato da un [`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) Toolkit di *realtà mista o* da un shader standard, è necessario che sia abilitata la proprietà del *passaggio del mouse* .</span><span class="sxs-lookup"><span data-stu-id="31872-107">For a material to be influenced by a [`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) the *Mixed Reality Toolkit/Standard* shader must be used and the *Hover Light* property must be enabled.</span></span>

> [!Note]
> <span data-ttu-id="31872-108">Per [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) impostazione predefinita, sono supportati fino a due.</span><span class="sxs-lookup"><span data-stu-id="31872-108">Up to two [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) are supported by default.</span></span>

## <a name="examples"></a><span data-ttu-id="31872-109">Esempio</span><span class="sxs-lookup"><span data-stu-id="31872-109">Examples</span></span>

<span data-ttu-id="31872-110">La maggior parte delle scene all'interno della MRTK utilizza un [`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) .</span><span class="sxs-lookup"><span data-stu-id="31872-110">Most scenes within the MRTK utilize a [`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight).</span></span> <span data-ttu-id="31872-111">Il caso d'uso più comune è reperibile in MRTK/SDK/features/UX/prefabrics/Cursors/DefaultCursor. prefabrical</span><span class="sxs-lookup"><span data-stu-id="31872-111">The most common use case can be found on the MRTK/SDK/Features/UX/Prefabs/Cursors/DefaultCursor.prefab</span></span>

## <a name="advanced-usage"></a><span data-ttu-id="31872-112">Utilizzo avanzato</span><span class="sxs-lookup"><span data-stu-id="31872-112">Advanced Usage</span></span>

<span data-ttu-id="31872-113">Per impostazione predefinita, solo due [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) possono illuminare un [materiale](https://docs.unity3d.com/ScriptReference/Material.html) alla volta.</span><span class="sxs-lookup"><span data-stu-id="31872-113">By default only two [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) can illuminate a [material](https://docs.unity3d.com/ScriptReference/Material.html) at a time.</span></span> <span data-ttu-id="31872-114">Se il progetto richiede più di due [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) per influenzare un [materiale](https://docs.unity3d.com/ScriptReference/Material.html) , nel codice di esempio riportato di seguito viene illustrato come ottenere questo risultato.</span><span class="sxs-lookup"><span data-stu-id="31872-114">If your project requires more than two [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) to influence a [material](https://docs.unity3d.com/ScriptReference/Material.html) the sample code below demonstrates how to achieve this.</span></span>

> [!Note]
> <span data-ttu-id="31872-115">La presenza [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) di molti [materiali](https://docs.unity3d.com/ScriptReference/Material.html) illuminati aumenterà pixel shader istruzioni e influirà sulle prestazioni.</span><span class="sxs-lookup"><span data-stu-id="31872-115">Having many [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) illuminate a [material](https://docs.unity3d.com/ScriptReference/Material.html) will increase pixel shader instructions and will impact performance.</span></span> <span data-ttu-id="31872-116">Per profilare queste modifiche all'interno del progetto.</span><span class="sxs-lookup"><span data-stu-id="31872-116">Please profile these changes within your project.</span></span>

<span data-ttu-id="31872-117">*Come aumentare il numero di disponibili [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) da due a quattro.*</span><span class="sxs-lookup"><span data-stu-id="31872-117">*How to increase the number of available [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) from two to four.*</span></span>

```C#
// 1) Within MRTK/Core/StandardAssets/Shaders/MixedRealityStandard.shader change:

#define HOVER_LIGHT_COUNT 2

// to:

#define HOVER_LIGHT_COUNT 4

// 2) Within MRTK/Core/Utilities/StandardShader/HoverLight.cs change:

private const int hoverLightCount = 2;

// to:

private const int hoverLightCount = 4;
```

> [!NOTE]
> <span data-ttu-id="31872-118">Se Unity registra un avviso simile a quello riportato di seguito, è necessario riavviare Unity prima che le modifiche siano effettive.</span><span class="sxs-lookup"><span data-stu-id="31872-118">If Unity logs a warning similar to below then you must restart Unity before your changes will take effect.</span></span>
>
> `Property (_HoverLightData) exceeds previous array size (8 vs 4). Cap to previous >size.`

## <a name="see-also"></a><span data-ttu-id="31872-119">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="31872-119">See also</span></span>

* [<span data-ttu-id="31872-120">Shader standard MRTK</span><span class="sxs-lookup"><span data-stu-id="31872-120">MRTK Standard Shader</span></span>](../README_MRTKStandardShader.md)

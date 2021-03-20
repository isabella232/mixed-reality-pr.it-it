---
title: ProximityLight
description: Documentazione su prossimità Light con esempi in MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: 7f6d37592ea1ac200651030fb4d4dbafc0d1f4d8
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2021
ms.locfileid: "104689911"
---
# <a name="proximity-light"></a><span data-ttu-id="0dbde-104">Luce vicina</span><span class="sxs-lookup"><span data-stu-id="0dbde-104">Proximity Light</span></span>

<span data-ttu-id="0dbde-105">Un [`ProximityLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) è un paradigma del [sistema di progettazione Fluent](https://www.microsoft.com/design/fluent/) che simula una "sfumatura del punto inverso della sfumatura" accanto alla superficie di un oggetto.</span><span class="sxs-lookup"><span data-stu-id="0dbde-105">A [`ProximityLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) is a [Fluent Design System](https://www.microsoft.com/design/fluent/) paradigm that mimics a "gradient inverse point light" hovering near the surface of an object.</span></span> <span data-ttu-id="0dbde-106">Spesso usato per le interazioni near, l'applicazione può controllare le proprietà di una luce di prossimità tramite il [`ProximityLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) componente.</span><span class="sxs-lookup"><span data-stu-id="0dbde-106">Often used for near interactions, the application can control the properties of a Proximity Light via the [`ProximityLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) component.</span></span>

<span data-ttu-id="0dbde-107">Affinché un materiale venga influenzato da un [`ProximityLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) Toolkit di *realtà mista o* da un shader standard, è necessario che sia abilitata la proprietà *prossimità luce* .</span><span class="sxs-lookup"><span data-stu-id="0dbde-107">For a material to be influenced by a [`ProximityLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) the *Mixed Reality Toolkit/Standard* shader must be used and the *Proximity Light* property must be enabled.</span></span>

> [!NOTE]
> <span data-ttu-id="0dbde-108">Per [`ProximityLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) impostazione predefinita, sono supportati fino a due.</span><span class="sxs-lookup"><span data-stu-id="0dbde-108">Up to two [`ProximityLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) are supported by default.</span></span>

## <a name="examples"></a><span data-ttu-id="0dbde-109">Esempio</span><span class="sxs-lookup"><span data-stu-id="0dbde-109">Examples</span></span>

<span data-ttu-id="0dbde-110">La maggior parte delle scene all'interno della MRTK utilizza un [`ProximityLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) .</span><span class="sxs-lookup"><span data-stu-id="0dbde-110">Most scenes within the MRTK utilize a [`ProximityLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight).</span></span> <span data-ttu-id="0dbde-111">Il caso d'uso più comune è reperibile in MRTK/SDK/features/UX/prefabrics/Cursors/FingerCursor. prefabrical</span><span class="sxs-lookup"><span data-stu-id="0dbde-111">The most common use case can be found on the MRTK/SDK/Features/UX/Prefabs/Cursors/FingerCursor.prefab</span></span>

## <a name="advanced-usage"></a><span data-ttu-id="0dbde-112">Utilizzo avanzato</span><span class="sxs-lookup"><span data-stu-id="0dbde-112">Advanced Usage</span></span>

<span data-ttu-id="0dbde-113">Per impostazione predefinita, solo due [`ProximityLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) possono illuminare un [materiale](https://docs.unity3d.com/ScriptReference/Material.html) alla volta.</span><span class="sxs-lookup"><span data-stu-id="0dbde-113">By default only two [`ProximityLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) can illuminate a [material](https://docs.unity3d.com/ScriptReference/Material.html) at a time.</span></span> <span data-ttu-id="0dbde-114">Se il progetto richiede più di due [`ProximityLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) per influenzare un [materiale](https://docs.unity3d.com/ScriptReference/Material.html) , nel codice di esempio riportato di seguito viene illustrato come ottenere questo risultato.</span><span class="sxs-lookup"><span data-stu-id="0dbde-114">If your project requires more than two [`ProximityLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) to influence a [material](https://docs.unity3d.com/ScriptReference/Material.html) the sample code below demonstrates how to achieve this.</span></span>

> [!NOTE]
> <span data-ttu-id="0dbde-115">La presenza [`ProximityLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) di molti [materiali](https://docs.unity3d.com/ScriptReference/Material.html) illuminati aumenterà pixel shader istruzioni e influirà sulle prestazioni.</span><span class="sxs-lookup"><span data-stu-id="0dbde-115">Having many [`ProximityLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) illuminate a [material](https://docs.unity3d.com/ScriptReference/Material.html) will increase pixel shader instructions and will impact performance.</span></span> <span data-ttu-id="0dbde-116">Per profilare queste modifiche all'interno del progetto.</span><span class="sxs-lookup"><span data-stu-id="0dbde-116">Please profile these changes within your project.</span></span>

<span data-ttu-id="0dbde-117">*Come aumentare il numero di disponibili [`ProximityLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) da due a quattro.*</span><span class="sxs-lookup"><span data-stu-id="0dbde-117">*How to increase the number of available [`ProximityLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) from two to four.*</span></span>

```C#
// 1) Within MRTK/Core/StandardAssets/Shaders/MixedRealityStandard.shader change:

#define PROXIMITY_LIGHT_COUNT 2

// to:

#define PROXIMITY_LIGHT_COUNT 4

// 2) Within MRTK/Core/Utilities/StandardShader/ProximityLight.cs change:

private const int proximityLightCount = 2;

// to:

private const int proximityLightCount = 4;
```

> [!NOTE]
> <span data-ttu-id="0dbde-118">Se Unity registra un avviso simile a quello riportato di seguito, è necessario riavviare Unity prima che le modifiche siano effettive.</span><span class="sxs-lookup"><span data-stu-id="0dbde-118">If Unity logs a warning similar to below then you must restart Unity before your changes will take effect.</span></span>
>
>`Property (_ProximityLightData) exceeds previous array size (24 vs 12). Cap to previous size.`

## <a name="see-also"></a><span data-ttu-id="0dbde-119">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="0dbde-119">See also</span></span>

* [<span data-ttu-id="0dbde-120">Shader standard MRTK</span><span class="sxs-lookup"><span data-stu-id="0dbde-120">MRTK Standard Shader</span></span>](../README_MRTKStandardShader.md)

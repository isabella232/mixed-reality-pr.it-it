---
title: Luce di prossimità
description: Documentazione sulla luce di prossimità con esempi in MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: 6e57a76d54d0f3f63ce8dcb80582e178effa39d9
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176386"
---
# <a name="proximity-light"></a><span data-ttu-id="2a30a-104">Luce di prossimità</span><span class="sxs-lookup"><span data-stu-id="2a30a-104">Proximity light</span></span>

<span data-ttu-id="2a30a-105">Un è un paradigma Fluent Design System che simula una "luce del punto inverso sfumatura" che si posiziona accanto [`ProximityLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) alla superficie di un oggetto. [](https://www.microsoft.com/design/fluent/)</span><span class="sxs-lookup"><span data-stu-id="2a30a-105">A [`ProximityLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) is a [Fluent Design System](https://www.microsoft.com/design/fluent/) paradigm that mimics a "gradient inverse point light" hovering near the surface of an object.</span></span> <span data-ttu-id="2a30a-106">Spesso usata per le interazioni da vicino, l'applicazione può controllare le proprietà di una luce di prossimità tramite il [`ProximityLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) componente .</span><span class="sxs-lookup"><span data-stu-id="2a30a-106">Often used for near interactions, the application can control the properties of a Proximity Light via the [`ProximityLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) component.</span></span>

<span data-ttu-id="2a30a-107">Perché un materiale sia influenzato da uno shader Toolkit/Standard di realtà mista, è necessario usare e la proprietà Luce di prossimità [`ProximityLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) deve essere  abilitata. </span><span class="sxs-lookup"><span data-stu-id="2a30a-107">For a material to be influenced by a [`ProximityLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) the *Mixed Reality Toolkit/Standard* shader must be used and the *Proximity Light* property must be enabled.</span></span>

> [!NOTE]
> <span data-ttu-id="2a30a-108">Per impostazione [`ProximityLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) predefinita, sono supportate fino a due.</span><span class="sxs-lookup"><span data-stu-id="2a30a-108">Up to two [`ProximityLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) are supported by default.</span></span>

## <a name="examples"></a><span data-ttu-id="2a30a-109">Esempio</span><span class="sxs-lookup"><span data-stu-id="2a30a-109">Examples</span></span>

<span data-ttu-id="2a30a-110">La maggior parte delle scene all'interno di MRTK usa un [`ProximityLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) oggetto .</span><span class="sxs-lookup"><span data-stu-id="2a30a-110">Most scenes within the MRTK utilize a [`ProximityLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight).</span></span> <span data-ttu-id="2a30a-111">Il caso d'uso più comune è disponibile in MRTK/SDK/Features/UX/Prefabs/Cursors/FingerCursor.prefab</span><span class="sxs-lookup"><span data-stu-id="2a30a-111">The most common use case can be found on the MRTK/SDK/Features/UX/Prefabs/Cursors/FingerCursor.prefab</span></span>

## <a name="advanced-usage"></a><span data-ttu-id="2a30a-112">Utilizzo avanzato</span><span class="sxs-lookup"><span data-stu-id="2a30a-112">Advanced Usage</span></span>

<span data-ttu-id="2a30a-113">Per impostazione predefinita, [`ProximityLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) solo due possono illuminare [un](https://docs.unity3d.com/ScriptReference/Material.html) materiale alla volta.</span><span class="sxs-lookup"><span data-stu-id="2a30a-113">By default only two [`ProximityLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) can illuminate a [material](https://docs.unity3d.com/ScriptReference/Material.html) at a time.</span></span> <span data-ttu-id="2a30a-114">Se il progetto richiede più di due elementi [`ProximityLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) per influenzare un [materiale,](https://docs.unity3d.com/ScriptReference/Material.html) il codice di esempio seguente illustra come ottenere questo risultato.</span><span class="sxs-lookup"><span data-stu-id="2a30a-114">If your project requires more than two [`ProximityLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) to influence a [material](https://docs.unity3d.com/ScriptReference/Material.html) the sample code below demonstrates how to achieve this.</span></span>

> [!NOTE]
> <span data-ttu-id="2a30a-115">La presenza [`ProximityLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) di molti elementi che [illuminano un](https://docs.unity3d.com/ScriptReference/Material.html) materiale aumenterà pixel shader istruzioni e inciderà sulle prestazioni.</span><span class="sxs-lookup"><span data-stu-id="2a30a-115">Having many [`ProximityLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) illuminate a [material](https://docs.unity3d.com/ScriptReference/Material.html) will increase pixel shader instructions and will impact performance.</span></span> <span data-ttu-id="2a30a-116">Profilare queste modifiche all'interno del progetto.</span><span class="sxs-lookup"><span data-stu-id="2a30a-116">Please profile these changes within your project.</span></span>

<span data-ttu-id="2a30a-117">*Come aumentare il numero di disponibili [`ProximityLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) da due a quattro.*</span><span class="sxs-lookup"><span data-stu-id="2a30a-117">*How to increase the number of available [`ProximityLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) from two to four.*</span></span>

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
> <span data-ttu-id="2a30a-118">Se Unity registra un avviso simile al seguente, è necessario riavviare Unity prima che le modifiche avranno effetto.</span><span class="sxs-lookup"><span data-stu-id="2a30a-118">If Unity logs a warning similar to below then you must restart Unity before your changes will take effect.</span></span>
>
>`Property (_ProximityLightData) exceeds previous array size (24 vs 12). Cap to previous size.`

## <a name="see-also"></a><span data-ttu-id="2a30a-119">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="2a30a-119">See also</span></span>

* [<span data-ttu-id="2a30a-120">MRTK Standard Shader</span><span class="sxs-lookup"><span data-stu-id="2a30a-120">MRTK Standard Shader</span></span>](mrtk-standard-shader.md)

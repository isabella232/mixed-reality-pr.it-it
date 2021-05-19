---
title: Luce di prossimità
description: Documentazione sulla luce di prossimità con esempi in MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realtà mista, sviluppo, MRTK,
ms.openlocfilehash: 1adf4d1d70313c917d63224b91a14d995d1888c1
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/19/2021
ms.locfileid: "110145006"
---
# <a name="proximity-light"></a><span data-ttu-id="d01b7-104">Luce di prossimità</span><span class="sxs-lookup"><span data-stu-id="d01b7-104">Proximity Light</span></span>

<span data-ttu-id="d01b7-105">Un [`ProximityLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) è un [paradigma Fluent Design System](https://www.microsoft.com/design/fluent/) che simula una "luce del punto inverso della sfumatura" che si sposta vicino alla superficie di un oggetto.</span><span class="sxs-lookup"><span data-stu-id="d01b7-105">A [`ProximityLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) is a [Fluent Design System](https://www.microsoft.com/design/fluent/) paradigm that mimics a "gradient inverse point light" hovering near the surface of an object.</span></span> <span data-ttu-id="d01b7-106">Spesso usata per le interazioni near, l'applicazione può controllare le proprietà di una luce di prossimità tramite il [`ProximityLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) componente .</span><span class="sxs-lookup"><span data-stu-id="d01b7-106">Often used for near interactions, the application can control the properties of a Proximity Light via the [`ProximityLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) component.</span></span>

<span data-ttu-id="d01b7-107">Perché un materiale sia influenzato da uno [`ProximityLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) shader *Mixed Reality Toolkit/Standard,* è necessario che sia abilitata la proprietà *Proximity Light.*</span><span class="sxs-lookup"><span data-stu-id="d01b7-107">For a material to be influenced by a [`ProximityLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) the *Mixed Reality Toolkit/Standard* shader must be used and the *Proximity Light* property must be enabled.</span></span>

> [!NOTE]
> <span data-ttu-id="d01b7-108">Per impostazione [`ProximityLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) predefinita, sono supportate fino a due.</span><span class="sxs-lookup"><span data-stu-id="d01b7-108">Up to two [`ProximityLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) are supported by default.</span></span>

## <a name="examples"></a><span data-ttu-id="d01b7-109">Esempio</span><span class="sxs-lookup"><span data-stu-id="d01b7-109">Examples</span></span>

<span data-ttu-id="d01b7-110">La maggior parte delle scene all'interno di MRTK usa un [`ProximityLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) oggetto .</span><span class="sxs-lookup"><span data-stu-id="d01b7-110">Most scenes within the MRTK utilize a [`ProximityLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight).</span></span> <span data-ttu-id="d01b7-111">Il caso d'uso più comune è disponibile in MRTK/SDK/Features/UX/Prefabs/Cursors/FingerCursor.prefab</span><span class="sxs-lookup"><span data-stu-id="d01b7-111">The most common use case can be found on the MRTK/SDK/Features/UX/Prefabs/Cursors/FingerCursor.prefab</span></span>

## <a name="advanced-usage"></a><span data-ttu-id="d01b7-112">Utilizzo avanzato</span><span class="sxs-lookup"><span data-stu-id="d01b7-112">Advanced Usage</span></span>

<span data-ttu-id="d01b7-113">Per impostazione predefinita, [`ProximityLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) solo due possono [illuminare un materiale](https://docs.unity3d.com/ScriptReference/Material.html) alla volta.</span><span class="sxs-lookup"><span data-stu-id="d01b7-113">By default only two [`ProximityLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) can illuminate a [material](https://docs.unity3d.com/ScriptReference/Material.html) at a time.</span></span> <span data-ttu-id="d01b7-114">Se il progetto richiede più di due elementi per influenzare un materiale, il codice di esempio seguente [`ProximityLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) illustra come ottenere questo risultato. [](https://docs.unity3d.com/ScriptReference/Material.html)</span><span class="sxs-lookup"><span data-stu-id="d01b7-114">If your project requires more than two [`ProximityLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) to influence a [material](https://docs.unity3d.com/ScriptReference/Material.html) the sample code below demonstrates how to achieve this.</span></span>

> [!NOTE]
> <span data-ttu-id="d01b7-115">La presenza [`ProximityLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) di molti elementi che [illuminano un](https://docs.unity3d.com/ScriptReference/Material.html) materiale aumenta pixel shader istruzioni e influisce sulle prestazioni.</span><span class="sxs-lookup"><span data-stu-id="d01b7-115">Having many [`ProximityLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) illuminate a [material](https://docs.unity3d.com/ScriptReference/Material.html) will increase pixel shader instructions and will impact performance.</span></span> <span data-ttu-id="d01b7-116">Profilare queste modifiche all'interno del progetto.</span><span class="sxs-lookup"><span data-stu-id="d01b7-116">Please profile these changes within your project.</span></span>

<span data-ttu-id="d01b7-117">*Come aumentare il numero di disponibili [`ProximityLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) da due a quattro.*</span><span class="sxs-lookup"><span data-stu-id="d01b7-117">*How to increase the number of available [`ProximityLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) from two to four.*</span></span>

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
> <span data-ttu-id="d01b7-118">Se Unity registra un avviso simile al seguente, è necessario riavviare Unity prima che le modifiche avranno effetto.</span><span class="sxs-lookup"><span data-stu-id="d01b7-118">If Unity logs a warning similar to below then you must restart Unity before your changes will take effect.</span></span>
>
>`Property (_ProximityLightData) exceeds previous array size (24 vs 12). Cap to previous size.`

## <a name="see-also"></a><span data-ttu-id="d01b7-119">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="d01b7-119">See also</span></span>

* [<span data-ttu-id="d01b7-120">MRTK Standard Shader</span><span class="sxs-lookup"><span data-stu-id="d01b7-120">MRTK Standard Shader</span></span>](mrtk-standard-shader.md)

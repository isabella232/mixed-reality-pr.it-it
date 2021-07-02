---
title: Rilevamento delle funzionalità della piattaforma
description: Dettagli delle diverse funzionalità supportate da MRTK
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, funzionalità,
ms.openlocfilehash: 70d320e178f4635d74b5be6a1874eb4254801719
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2021
ms.locfileid: "113175526"
---
# <a name="detecting-platform-capabilities"></a><span data-ttu-id="d17cb-104">Rilevamento delle funzionalità della piattaforma</span><span class="sxs-lookup"><span data-stu-id="d17cb-104">Detecting platform capabilities</span></span>

<span data-ttu-id="d17cb-105">Una domanda comune su MRTK consiste nel sapere quale dispositivo specifico (ad esempio, Microsoft HoloLens 2) viene usato per eseguire un'applicazione.</span><span class="sxs-lookup"><span data-stu-id="d17cb-105">A common question asked of the MRTK involves knowing which specific device (ex: Microsoft HoloLens 2) is being used to run an application.</span></span> <span data-ttu-id="d17cb-106">L'identificazione dell'hardware esatto può risultare complessa in piattaforme diverse.</span><span class="sxs-lookup"><span data-stu-id="d17cb-106">Identifying the exact hardware can be challenging on different platforms.</span></span> <span data-ttu-id="d17cb-107">MrTK consente invece di identificare funzionalità specifiche in fase di esecuzione, ad esempio se l'endpoint del dispositivo corrente supporta mani articolate.</span><span class="sxs-lookup"><span data-stu-id="d17cb-107">Instead, the MRTK provides a way to identify specific capabilities at runtime, (e.g. if the current device endpoint supports articulated hands).</span></span>

## <a name="capabilities"></a><span data-ttu-id="d17cb-108">Funzionalità</span><span class="sxs-lookup"><span data-stu-id="d17cb-108">Capabilities</span></span>

<span data-ttu-id="d17cb-109">L'Toolkit di realtà mista fornisce l'enumerazione , che definisce un set di funzionalità per cui un'applicazione [`MixedRealityCapability`](xref:Microsoft.MixedReality.Toolkit.MixedRealityCapability) può eseguire query in fase di esecuzione.</span><span class="sxs-lookup"><span data-stu-id="d17cb-109">The Mixed Reality Toolkit provides the [`MixedRealityCapability`](xref:Microsoft.MixedReality.Toolkit.MixedRealityCapability) enumeration, which defines a set of capabilities for which an application can query at runtime.</span></span>

### <a name="input-system-capabilities"></a><span data-ttu-id="d17cb-110">Funzionalità del sistema di input</span><span class="sxs-lookup"><span data-stu-id="d17cb-110">Input system capabilities</span></span>

<span data-ttu-id="d17cb-111">Il sistema di input MRTK predefinito supporta l'esecuzione di query sulle funzionalità seguenti:</span><span class="sxs-lookup"><span data-stu-id="d17cb-111">The default MRTK Input System supports querying the following capabilities:</span></span>

| <span data-ttu-id="d17cb-112">Funzionalità</span><span class="sxs-lookup"><span data-stu-id="d17cb-112">Capability</span></span> | <span data-ttu-id="d17cb-113">Descrizione</span><span class="sxs-lookup"><span data-stu-id="d17cb-113">Description</span></span> |
|---|---|
| <span data-ttu-id="d17cb-114">ArticulatedHand</span><span class="sxs-lookup"><span data-stu-id="d17cb-114">ArticulatedHand</span></span> | <span data-ttu-id="d17cb-115">Input manuale articolato</span><span class="sxs-lookup"><span data-stu-id="d17cb-115">Articulated hand input</span></span> |
| <span data-ttu-id="d17cb-116">EyeTracking</span><span class="sxs-lookup"><span data-stu-id="d17cb-116">EyeTracking</span></span> | <span data-ttu-id="d17cb-117">Targeting dello sguardo fisso</span><span class="sxs-lookup"><span data-stu-id="d17cb-117">Eye gaze targeting</span></span> |
| <span data-ttu-id="d17cb-118">GGVHand</span><span class="sxs-lookup"><span data-stu-id="d17cb-118">GGVHand</span></span> | <span data-ttu-id="d17cb-119">Input della mano Gaze-Gesture-Voice</span><span class="sxs-lookup"><span data-stu-id="d17cb-119">Gaze-Gesture-Voice hand input</span></span> |
| <span data-ttu-id="d17cb-120">MotionController</span><span class="sxs-lookup"><span data-stu-id="d17cb-120">MotionController</span></span> | <span data-ttu-id="d17cb-121">Input del controller di movimento</span><span class="sxs-lookup"><span data-stu-id="d17cb-121">Motion controller input</span></span> |
| <span data-ttu-id="d17cb-122">VoiceCommand</span><span class="sxs-lookup"><span data-stu-id="d17cb-122">VoiceCommand</span></span> | <span data-ttu-id="d17cb-123">Comandi vocali con parole chiave definite dall'app</span><span class="sxs-lookup"><span data-stu-id="d17cb-123">Voice commands using app defined keywords</span></span> |
| <span data-ttu-id="d17cb-124">VoiceDictation</span><span class="sxs-lookup"><span data-stu-id="d17cb-124">VoiceDictation</span></span> | <span data-ttu-id="d17cb-125">Dettatura da voce a testo</span><span class="sxs-lookup"><span data-stu-id="d17cb-125">Voice to text dictation</span></span> |

<span data-ttu-id="d17cb-126">Il codice di esempio seguente verifica se il sistema di input ha caricato un provider di dati con supporto per mani articolate.</span><span class="sxs-lookup"><span data-stu-id="d17cb-126">The example code below checks to see if the input system has loaded a data provider with support for articulated hands.</span></span>

```c#
bool supportsArticulatedHands = false;

IMixedRealityCapabilityCheck capabilityCheck = CoreServices.InputSystem as IMixedRealityCapabilityCheck;
if (capabilityCheck != null)
{
    supportsArticulatedHands = capabilityCheck.CheckCapability(MixedRealityCapability.ArticulatedHand);
}
```

### <a name="spatial-awareness-capabilities"></a><span data-ttu-id="d17cb-127">Funzionalità di consapevolezza spaziale</span><span class="sxs-lookup"><span data-stu-id="d17cb-127">Spatial awareness capabilities</span></span>

<span data-ttu-id="d17cb-128">Il sistema di riconoscimento spaziale MRTK predefinito supporta l'esecuzione di query sulle funzionalità seguenti:</span><span class="sxs-lookup"><span data-stu-id="d17cb-128">The default MRTK Spatial Awareness system supports querying the following capabilities:</span></span>

| <span data-ttu-id="d17cb-129">Funzionalità</span><span class="sxs-lookup"><span data-stu-id="d17cb-129">Capability</span></span> | <span data-ttu-id="d17cb-130">Descrizione</span><span class="sxs-lookup"><span data-stu-id="d17cb-130">Description</span></span> |
|---|---|
| <span data-ttu-id="d17cb-131">SpatialAwarenessMesh</span><span class="sxs-lookup"><span data-stu-id="d17cb-131">SpatialAwarenessMesh</span></span> | <span data-ttu-id="d17cb-132">Mesh spaziali</span><span class="sxs-lookup"><span data-stu-id="d17cb-132">Spatial meshes</span></span> |
| <span data-ttu-id="d17cb-133">SpatialAwarenessPlane</span><span class="sxs-lookup"><span data-stu-id="d17cb-133">SpatialAwarenessPlane</span></span> | <span data-ttu-id="d17cb-134">Piani spaziali</span><span class="sxs-lookup"><span data-stu-id="d17cb-134">Spatial planes</span></span> |
| <span data-ttu-id="d17cb-135">SpatialAwarenessPoint</span><span class="sxs-lookup"><span data-stu-id="d17cb-135">SpatialAwarenessPoint</span></span> | <span data-ttu-id="d17cb-136">Punti spaziali</span><span class="sxs-lookup"><span data-stu-id="d17cb-136">Spatial points</span></span> |

<span data-ttu-id="d17cb-137">Questo esempio verifica se il sistema di riconoscimento spaziale ha caricato un provider di dati con supporto per le mesh spaziali.</span><span class="sxs-lookup"><span data-stu-id="d17cb-137">This example checks to see if the spatial awareness system has loaded a data provider with support for spatial meshes.</span></span>

```c#
bool supportsSpatialMesh = false;

IMixedRealityCapabilityCheck capabilityCheck = CoreServices.SpatialAwarenessSystem as IMixedRealityCapabilityCheck;
if (capabilityCheck != null)
{
    supportsSpatialMesh = capabilityCheck.CheckCapability(MixedRealityCapability.SpatialAwarenessMesh);
}
```

## <a name="see-also"></a><span data-ttu-id="d17cb-138">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="d17cb-138">See also</span></span>

- [<span data-ttu-id="d17cb-139">Documentazione dell'API IMixedRealityCapabilityCheck</span><span class="sxs-lookup"><span data-stu-id="d17cb-139">IMixedRealityCapabilityCheck API documentation</span></span>](xref:Microsoft.MixedReality.Toolkit.IMixedRealityCapabilityCheck)
- [<span data-ttu-id="d17cb-140">Documentazione dell'enumerazione MixedRealityCapability</span><span class="sxs-lookup"><span data-stu-id="d17cb-140">MixedRealityCapability enum documentation</span></span>](xref:Microsoft.MixedReality.Toolkit.MixedRealityCapability)

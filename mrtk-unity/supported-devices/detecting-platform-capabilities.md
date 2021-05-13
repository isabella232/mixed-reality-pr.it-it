---
title: DetectingPlatformCapabilities
description: Dettagli delle diverse funzionalità supportate da MRTK
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, funzionalità,
ms.openlocfilehash: 62e03c6d47deb079d3460759b5c694dd258a7767
ms.sourcegitcommit: 8e1a1d48d9c7cd94dab4ce6246aa2c0f49ff5308
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/13/2021
ms.locfileid: "109852437"
---
# <a name="detecting-platform-capabilities"></a><span data-ttu-id="c2be5-104">Rilevamento delle funzionalità della piattaforma</span><span class="sxs-lookup"><span data-stu-id="c2be5-104">Detecting platform capabilities</span></span>

<span data-ttu-id="c2be5-105">Una domanda comune posta su MRTK implica la conoscenza del dispositivo specifico (ad esempio, Microsoft HoloLens 2) usato per eseguire un'applicazione.</span><span class="sxs-lookup"><span data-stu-id="c2be5-105">A common question asked of the MRTK involves knowing which specific device (ex: Microsoft HoloLens 2) is being used to run an application.</span></span> <span data-ttu-id="c2be5-106">L'identificazione dell'hardware esatto può risultare complessa in piattaforme diverse.</span><span class="sxs-lookup"><span data-stu-id="c2be5-106">Identifying the exact hardware can be challenging on different platforms.</span></span> <span data-ttu-id="c2be5-107">MrTK consente invece di identificare funzionalità specifiche in fase di esecuzione, ad esempio se l'endpoint del dispositivo corrente supporta mani articolate.</span><span class="sxs-lookup"><span data-stu-id="c2be5-107">Instead, the MRTK provides a way to identify specific capabilities at runtime, (e.g. if the current device endpoint supports articulated hands).</span></span>

## <a name="capabilities"></a><span data-ttu-id="c2be5-108">Funzionalità</span><span class="sxs-lookup"><span data-stu-id="c2be5-108">Capabilities</span></span>

<span data-ttu-id="c2be5-109">Mixed Reality Toolkit fornisce l'enumerazione , che definisce un set di funzionalità per cui un'applicazione può eseguire query in [`MixedRealityCapability`](xref:Microsoft.MixedReality.Toolkit.MixedRealityCapability) fase di esecuzione.</span><span class="sxs-lookup"><span data-stu-id="c2be5-109">The Mixed Reality Toolkit provides the [`MixedRealityCapability`](xref:Microsoft.MixedReality.Toolkit.MixedRealityCapability) enumeration, which defines a set of capabilities for which an application can query at runtime.</span></span>

### <a name="input-system-capabilities"></a><span data-ttu-id="c2be5-110">Funzionalità del sistema di input</span><span class="sxs-lookup"><span data-stu-id="c2be5-110">Input system capabilities</span></span>

<span data-ttu-id="c2be5-111">Il sistema di input MRTK predefinito supporta l'esecuzione di query sulle funzionalità seguenti:</span><span class="sxs-lookup"><span data-stu-id="c2be5-111">The default MRTK Input System supports querying the following capabilities:</span></span>

| <span data-ttu-id="c2be5-112">Funzionalità</span><span class="sxs-lookup"><span data-stu-id="c2be5-112">Capability</span></span> | <span data-ttu-id="c2be5-113">Descrizione</span><span class="sxs-lookup"><span data-stu-id="c2be5-113">Description</span></span> |
|---|---|
| <span data-ttu-id="c2be5-114">ArticulatedHand</span><span class="sxs-lookup"><span data-stu-id="c2be5-114">ArticulatedHand</span></span> | <span data-ttu-id="c2be5-115">Input della mano articolato</span><span class="sxs-lookup"><span data-stu-id="c2be5-115">Articulated hand input</span></span> |
| <span data-ttu-id="c2be5-116">Tracciamento oculare</span><span class="sxs-lookup"><span data-stu-id="c2be5-116">EyeTracking</span></span> | <span data-ttu-id="c2be5-117">Targeting dello sguardo fisso</span><span class="sxs-lookup"><span data-stu-id="c2be5-117">Eye gaze targeting</span></span> |
| <span data-ttu-id="c2be5-118">GGVHand</span><span class="sxs-lookup"><span data-stu-id="c2be5-118">GGVHand</span></span> | <span data-ttu-id="c2be5-119">Input mano sguardo fisso-movimento-voce</span><span class="sxs-lookup"><span data-stu-id="c2be5-119">Gaze-Gesture-Voice hand input</span></span> |
| <span data-ttu-id="c2be5-120">MotionController</span><span class="sxs-lookup"><span data-stu-id="c2be5-120">MotionController</span></span> | <span data-ttu-id="c2be5-121">Input del controller del movimento</span><span class="sxs-lookup"><span data-stu-id="c2be5-121">Motion controller input</span></span> |
| <span data-ttu-id="c2be5-122">VoiceCommand</span><span class="sxs-lookup"><span data-stu-id="c2be5-122">VoiceCommand</span></span> | <span data-ttu-id="c2be5-123">Comandi vocali con parole chiave definite dall'app</span><span class="sxs-lookup"><span data-stu-id="c2be5-123">Voice commands using app defined keywords</span></span> |
| <span data-ttu-id="c2be5-124">VoiceDictation</span><span class="sxs-lookup"><span data-stu-id="c2be5-124">VoiceDictation</span></span> | <span data-ttu-id="c2be5-125">Dettatura da voce a testo</span><span class="sxs-lookup"><span data-stu-id="c2be5-125">Voice to text dictation</span></span> |

<span data-ttu-id="c2be5-126">Il codice di esempio seguente verifica se il sistema di input ha caricato un provider di dati con supporto per mani articolate.</span><span class="sxs-lookup"><span data-stu-id="c2be5-126">The example code below checks to see if the input system has loaded a data provider with support for articulated hands.</span></span>

```c#
bool supportsArticulatedHands = false;

IMixedRealityCapabilityCheck capabilityCheck = CoreServices.InputSystem as IMixedRealityCapabilityCheck;
if (capabilityCheck != null)
{
    supportsArticulatedHands = capabilityCheck.CheckCapability(MixedRealityCapability.ArticulatedHand);
}
```

### <a name="spatial-awareness-capabilities"></a><span data-ttu-id="c2be5-127">Funzionalità di consapevolezza spaziale</span><span class="sxs-lookup"><span data-stu-id="c2be5-127">Spatial awareness capabilities</span></span>

<span data-ttu-id="c2be5-128">Il sistema di riconoscimento spaziale MRTK predefinito supporta l'esecuzione di query sulle funzionalità seguenti:</span><span class="sxs-lookup"><span data-stu-id="c2be5-128">The default MRTK Spatial Awareness system supports querying the following capabilities:</span></span>

| <span data-ttu-id="c2be5-129">Funzionalità</span><span class="sxs-lookup"><span data-stu-id="c2be5-129">Capability</span></span> | <span data-ttu-id="c2be5-130">Descrizione</span><span class="sxs-lookup"><span data-stu-id="c2be5-130">Description</span></span> |
|---|---|
| <span data-ttu-id="c2be5-131">SpatialAwarenessMesh</span><span class="sxs-lookup"><span data-stu-id="c2be5-131">SpatialAwarenessMesh</span></span> | <span data-ttu-id="c2be5-132">Mesh spaziali</span><span class="sxs-lookup"><span data-stu-id="c2be5-132">Spatial meshes</span></span> |
| <span data-ttu-id="c2be5-133">SpatialAwarenessPlane</span><span class="sxs-lookup"><span data-stu-id="c2be5-133">SpatialAwarenessPlane</span></span> | <span data-ttu-id="c2be5-134">Piani spaziali</span><span class="sxs-lookup"><span data-stu-id="c2be5-134">Spatial planes</span></span> |
| <span data-ttu-id="c2be5-135">SpatialAwarenessPoint</span><span class="sxs-lookup"><span data-stu-id="c2be5-135">SpatialAwarenessPoint</span></span> | <span data-ttu-id="c2be5-136">Punti spaziali</span><span class="sxs-lookup"><span data-stu-id="c2be5-136">Spatial points</span></span> |

<span data-ttu-id="c2be5-137">Questo esempio verifica se il sistema di riconoscimento spaziale ha caricato un provider di dati con supporto per le mesh spaziali.</span><span class="sxs-lookup"><span data-stu-id="c2be5-137">This example checks to see if the spatial awareness system has loaded a data provider with support for spatial meshes.</span></span>

```c#
bool supportsSpatialMesh = false;

IMixedRealityCapabilityCheck capabilityCheck = CoreServices.SpatialAwarenessSystem as IMixedRealityCapabilityCheck;
if (capabilityCheck != null)
{
    supportsSpatialMesh = capabilityCheck.CheckCapability(MixedRealityCapability.SpatialAwarenessMesh);
}
```

## <a name="see-also"></a><span data-ttu-id="c2be5-138">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="c2be5-138">See also</span></span>

- [<span data-ttu-id="c2be5-139">Documentazione dell'API IMixedRealityCapabilityCheck</span><span class="sxs-lookup"><span data-stu-id="c2be5-139">IMixedRealityCapabilityCheck API documentation</span></span>](xref:Microsoft.MixedReality.Toolkit.IMixedRealityCapabilityCheck)
- [<span data-ttu-id="c2be5-140">Documentazione dell'enumerazione MixedRealityCapability</span><span class="sxs-lookup"><span data-stu-id="c2be5-140">MixedRealityCapability enum documentation</span></span>](xref:Microsoft.MixedReality.Toolkit.MixedRealityCapability)

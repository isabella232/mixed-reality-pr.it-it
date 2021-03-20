---
title: DetectingPlatformCapabilities
description: Informazioni dettagliate sulle diverse funzionalità supportate da MRTK
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, funzionalità,
ms.openlocfilehash: 62e03c6d47deb079d3460759b5c694dd258a7767
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2021
ms.locfileid: "104681834"
---
# <a name="detecting-platform-capabilities"></a><span data-ttu-id="c2ca0-104">Rilevamento delle funzionalità della piattaforma</span><span class="sxs-lookup"><span data-stu-id="c2ca0-104">Detecting platform capabilities</span></span>

<span data-ttu-id="c2ca0-105">Una domanda comune di MRTK prevede la conoscenza del dispositivo specifico (ad esempio, Microsoft HoloLens 2) usato per eseguire un'applicazione.</span><span class="sxs-lookup"><span data-stu-id="c2ca0-105">A common question asked of the MRTK involves knowing which specific device (ex: Microsoft HoloLens 2) is being used to run an application.</span></span> <span data-ttu-id="c2ca0-106">Identificare l'hardware esatto può risultare complesso su piattaforme diverse.</span><span class="sxs-lookup"><span data-stu-id="c2ca0-106">Identifying the exact hardware can be challenging on different platforms.</span></span> <span data-ttu-id="c2ca0-107">Al contrario, MRTK fornisce un modo per identificare funzionalità specifiche in fase di esecuzione, ad esempio se l'endpoint del dispositivo corrente supporta le mani articolate.</span><span class="sxs-lookup"><span data-stu-id="c2ca0-107">Instead, the MRTK provides a way to identify specific capabilities at runtime, (e.g. if the current device endpoint supports articulated hands).</span></span>

## <a name="capabilities"></a><span data-ttu-id="c2ca0-108">Funzionalità</span><span class="sxs-lookup"><span data-stu-id="c2ca0-108">Capabilities</span></span>

<span data-ttu-id="c2ca0-109">Il Toolkit di realtà mista fornisce l' [`MixedRealityCapability`](xref:Microsoft.MixedReality.Toolkit.MixedRealityCapability) enumerazione, che definisce un set di funzionalità per le quali un'applicazione può eseguire query in fase di esecuzione.</span><span class="sxs-lookup"><span data-stu-id="c2ca0-109">The Mixed Reality Toolkit provides the [`MixedRealityCapability`](xref:Microsoft.MixedReality.Toolkit.MixedRealityCapability) enumeration, which defines a set of capabilities for which an application can query at runtime.</span></span>

### <a name="input-system-capabilities"></a><span data-ttu-id="c2ca0-110">Funzionalità del sistema di input</span><span class="sxs-lookup"><span data-stu-id="c2ca0-110">Input system capabilities</span></span>

<span data-ttu-id="c2ca0-111">Il sistema di input MRTK predefinito supporta l'esecuzione di query sulle funzionalità seguenti:</span><span class="sxs-lookup"><span data-stu-id="c2ca0-111">The default MRTK Input System supports querying the following capabilities:</span></span>

| <span data-ttu-id="c2ca0-112">Funzionalità</span><span class="sxs-lookup"><span data-stu-id="c2ca0-112">Capability</span></span> | <span data-ttu-id="c2ca0-113">Descrizione</span><span class="sxs-lookup"><span data-stu-id="c2ca0-113">Description</span></span> |
|---|---|
| <span data-ttu-id="c2ca0-114">ArticulatedHand</span><span class="sxs-lookup"><span data-stu-id="c2ca0-114">ArticulatedHand</span></span> | <span data-ttu-id="c2ca0-115">Input della mano articolata</span><span class="sxs-lookup"><span data-stu-id="c2ca0-115">Articulated hand input</span></span> |
| <span data-ttu-id="c2ca0-116">EyeTracking</span><span class="sxs-lookup"><span data-stu-id="c2ca0-116">EyeTracking</span></span> | <span data-ttu-id="c2ca0-117">Targeting degli occhi</span><span class="sxs-lookup"><span data-stu-id="c2ca0-117">Eye gaze targeting</span></span> |
| <span data-ttu-id="c2ca0-118">GGVHand</span><span class="sxs-lookup"><span data-stu-id="c2ca0-118">GGVHand</span></span> | <span data-ttu-id="c2ca0-119">Sguardo-movimento-input della mano vocale</span><span class="sxs-lookup"><span data-stu-id="c2ca0-119">Gaze-Gesture-Voice hand input</span></span> |
| <span data-ttu-id="c2ca0-120">MotionController</span><span class="sxs-lookup"><span data-stu-id="c2ca0-120">MotionController</span></span> | <span data-ttu-id="c2ca0-121">Input del controller di movimento</span><span class="sxs-lookup"><span data-stu-id="c2ca0-121">Motion controller input</span></span> |
| <span data-ttu-id="c2ca0-122">VoiceCommand</span><span class="sxs-lookup"><span data-stu-id="c2ca0-122">VoiceCommand</span></span> | <span data-ttu-id="c2ca0-123">Comandi vocali che usano parole chiave definite dall'app</span><span class="sxs-lookup"><span data-stu-id="c2ca0-123">Voice commands using app defined keywords</span></span> |
| <span data-ttu-id="c2ca0-124">VoiceDictation</span><span class="sxs-lookup"><span data-stu-id="c2ca0-124">VoiceDictation</span></span> | <span data-ttu-id="c2ca0-125">Dettatura da voce a testo</span><span class="sxs-lookup"><span data-stu-id="c2ca0-125">Voice to text dictation</span></span> |

<span data-ttu-id="c2ca0-126">Il codice di esempio seguente controlla se il sistema di input ha caricato un provider di dati con supporto per le mani articolate.</span><span class="sxs-lookup"><span data-stu-id="c2ca0-126">The example code below checks to see if the input system has loaded a data provider with support for articulated hands.</span></span>

```c#
bool supportsArticulatedHands = false;

IMixedRealityCapabilityCheck capabilityCheck = CoreServices.InputSystem as IMixedRealityCapabilityCheck;
if (capabilityCheck != null)
{
    supportsArticulatedHands = capabilityCheck.CheckCapability(MixedRealityCapability.ArticulatedHand);
}
```

### <a name="spatial-awareness-capabilities"></a><span data-ttu-id="c2ca0-127">Funzionalità di riconoscimento spaziale</span><span class="sxs-lookup"><span data-stu-id="c2ca0-127">Spatial awareness capabilities</span></span>

<span data-ttu-id="c2ca0-128">Il sistema di riconoscimento spaziale MRTK predefinito supporta l'esecuzione di query sulle funzionalità seguenti:</span><span class="sxs-lookup"><span data-stu-id="c2ca0-128">The default MRTK Spatial Awareness system supports querying the following capabilities:</span></span>

| <span data-ttu-id="c2ca0-129">Funzionalità</span><span class="sxs-lookup"><span data-stu-id="c2ca0-129">Capability</span></span> | <span data-ttu-id="c2ca0-130">Descrizione</span><span class="sxs-lookup"><span data-stu-id="c2ca0-130">Description</span></span> |
|---|---|
| <span data-ttu-id="c2ca0-131">SpatialAwarenessMesh</span><span class="sxs-lookup"><span data-stu-id="c2ca0-131">SpatialAwarenessMesh</span></span> | <span data-ttu-id="c2ca0-132">Mesh spaziali</span><span class="sxs-lookup"><span data-stu-id="c2ca0-132">Spatial meshes</span></span> |
| <span data-ttu-id="c2ca0-133">SpatialAwarenessPlane</span><span class="sxs-lookup"><span data-stu-id="c2ca0-133">SpatialAwarenessPlane</span></span> | <span data-ttu-id="c2ca0-134">Piani spaziali</span><span class="sxs-lookup"><span data-stu-id="c2ca0-134">Spatial planes</span></span> |
| <span data-ttu-id="c2ca0-135">SpatialAwarenessPoint</span><span class="sxs-lookup"><span data-stu-id="c2ca0-135">SpatialAwarenessPoint</span></span> | <span data-ttu-id="c2ca0-136">Punti spaziali</span><span class="sxs-lookup"><span data-stu-id="c2ca0-136">Spatial points</span></span> |

<span data-ttu-id="c2ca0-137">Questo esempio verifica se il sistema di riconoscimento spaziale ha caricato un provider di dati con supporto per le mesh spaziali.</span><span class="sxs-lookup"><span data-stu-id="c2ca0-137">This example checks to see if the spatial awareness system has loaded a data provider with support for spatial meshes.</span></span>

```c#
bool supportsSpatialMesh = false;

IMixedRealityCapabilityCheck capabilityCheck = CoreServices.SpatialAwarenessSystem as IMixedRealityCapabilityCheck;
if (capabilityCheck != null)
{
    supportsSpatialMesh = capabilityCheck.CheckCapability(MixedRealityCapability.SpatialAwarenessMesh);
}
```

## <a name="see-also"></a><span data-ttu-id="c2ca0-138">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="c2ca0-138">See also</span></span>

- [<span data-ttu-id="c2ca0-139">Documentazione dell'API IMixedRealityCapabilityCheck</span><span class="sxs-lookup"><span data-stu-id="c2ca0-139">IMixedRealityCapabilityCheck API documentation</span></span>](xref:Microsoft.MixedReality.Toolkit.IMixedRealityCapabilityCheck)
- [<span data-ttu-id="c2ca0-140">Documentazione di enumerazione MixedRealityCapability</span><span class="sxs-lookup"><span data-stu-id="c2ca0-140">MixedRealityCapability enum documentation</span></span>](xref:Microsoft.MixedReality.Toolkit.MixedRealityCapability)

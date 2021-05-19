---
title: Eye Tracking Eye Gaze Provider
description: Documentazione per il provider Eye Gaze in MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realtà mista, sviluppo, MRTK, EyeTracking, EyeGaze,
ms.openlocfilehash: ef50a55d52a5dad9f424c8af8139565e02542b6c
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144021"
---
# <a name="accessing-eye-tracking-data-in-your-unity-script"></a><span data-ttu-id="f2c9d-104">Accesso ai dati di tracciamento oculare nello script unity</span><span class="sxs-lookup"><span data-stu-id="f2c9d-104">Accessing eye tracking data in your Unity script</span></span>

<span data-ttu-id="f2c9d-105">Questo articolo presuppone che si abbia una conoscenza per la configurazione del tracciamento oculare in una scena MRTK (vedere Configurazione MRTK di base per [l'uso del tracciamento oculare](eye-tracking-basic-setup.md)).</span><span class="sxs-lookup"><span data-stu-id="f2c9d-105">This article assumes one has understanding for setting up eye tracking in an MRTK scene (see [Basic MRTK setup to use eye tracking](eye-tracking-basic-setup.md)).</span></span>
<span data-ttu-id="f2c9d-106">L'accesso ai dati di tracciamento oculare in uno script MonoBehaviour è semplice.</span><span class="sxs-lookup"><span data-stu-id="f2c9d-106">Accessing eye tracking data in a MonoBehaviour script is easy!</span></span> <span data-ttu-id="f2c9d-107">È sufficiente *usare CoreServices.InputSystem.EyeGazeProvider*.</span><span class="sxs-lookup"><span data-stu-id="f2c9d-107">Simply use *CoreServices.InputSystem.EyeGazeProvider*.</span></span>

## <a name="imixedrealityeyegazeprovider"></a><span data-ttu-id="f2c9d-108">IMixedRealityEyeGazeProvider</span><span class="sxs-lookup"><span data-stu-id="f2c9d-108">IMixedRealityEyeGazeProvider</span></span>

<span data-ttu-id="f2c9d-109">La configurazione del tracciamento oculare in MRTK viene configurata tramite [`IMixedRealityEyeGazeProvider`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityEyeGazeProvider) l'interfaccia .</span><span class="sxs-lookup"><span data-stu-id="f2c9d-109">Eye tracking configuration in MRTK is configured via the [`IMixedRealityEyeGazeProvider`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityEyeGazeProvider) interface.</span></span> <span data-ttu-id="f2c9d-110">[L'uso di CoreServices.InputSystem.EyeGazeProvider fornisce](eye-tracking-eye-gaze-provider.md) l'implementazione predefinita del provider gaze registrato nel toolkit in fase di esecuzione.</span><span class="sxs-lookup"><span data-stu-id="f2c9d-110">Using [CoreServices.InputSystem.EyeGazeProvider](eye-tracking-eye-gaze-provider.md) provides the default gaze provider implementation registered in the toolkit at runtime.</span></span>
<span data-ttu-id="f2c9d-111">Le proprietà utili `EyeGazeProvider` dell'oggetto sono descritte di seguito.</span><span class="sxs-lookup"><span data-stu-id="f2c9d-111">Useful properties of the `EyeGazeProvider` is outlined below.</span></span>

- <span data-ttu-id="f2c9d-112">**IsEyeTrackingEnabled:** True se l'utente ha selezionato di usare il tracciamento oculare per lo sguardo.</span><span class="sxs-lookup"><span data-stu-id="f2c9d-112">**IsEyeTrackingEnabled**: True if user has selected to use eye tracking for gaze.</span></span>

- <span data-ttu-id="f2c9d-113">**IsEyeCalibrationValid:** indica se la calibrazione del tracciamento oculare dell'utente è valida o meno.</span><span class="sxs-lookup"><span data-stu-id="f2c9d-113">**IsEyeCalibrationValid**: Indicates whether the user's eye tracking calibration is valid or not.</span></span>
<span data-ttu-id="f2c9d-114">Restituisce "null", se il valore non ha ancora ricevuto dati dal sistema di tracciamento oculare.</span><span class="sxs-lookup"><span data-stu-id="f2c9d-114">It returns 'null', if the value has not yet received data from the eye tracking system.</span></span>
<span data-ttu-id="f2c9d-115">Potrebbe non essere valido perché l'utente ha ignorato la calibrazione del tracciamento oculare.</span><span class="sxs-lookup"><span data-stu-id="f2c9d-115">It may be invalid, because the user skipped the eye tracking calibration.</span></span>

- <span data-ttu-id="f2c9d-116">**IsEyeTrackingEnabledAndValid:** indica se i dati di tracciamento oculare corrente sono attualmente usati per lo sguardo fisso.</span><span class="sxs-lookup"><span data-stu-id="f2c9d-116">**IsEyeTrackingEnabledAndValid**: Indicates whether the current eye tracking data is currently been used for gaze.</span></span>

- <span data-ttu-id="f2c9d-117">**IsEyeTrackingDataValid:** True se sono disponibili dati di tracciamento oculare.</span><span class="sxs-lookup"><span data-stu-id="f2c9d-117">**IsEyeTrackingDataValid**: True if eye tracking data is available.</span></span>
<span data-ttu-id="f2c9d-118">Potrebbe non essere disponibile a causa del timeout superato (dovrebbe essere affidabile per l'utente che lampeggia) o della mancanza di hardware o autorizzazioni di rilevamento.</span><span class="sxs-lookup"><span data-stu-id="f2c9d-118">It may be unavailable due to exceeded timeout (should be robust to the user blinking though) or lack of tracking hardware or permissions.</span></span>
<span data-ttu-id="f2c9d-119">Vedere [l'esempio di notifica di calibrazione](eye-tracking-is-user-calibrated.md) oculare mancante che spiega come rilevare se un utente è calibrato dagli occhi e visualizzare una notifica appropriata.</span><span class="sxs-lookup"><span data-stu-id="f2c9d-119">Check out our [Missing eye calibration notification sample](eye-tracking-is-user-calibrated.md) that explains how to detect whether a user is eye calibrated and to show an appropriate notification.</span></span>

- <span data-ttu-id="f2c9d-120">**GazeOrigin:** origine del raggio dello sguardo.</span><span class="sxs-lookup"><span data-stu-id="f2c9d-120">**GazeOrigin**: Origin of the gaze ray.</span></span>
<span data-ttu-id="f2c9d-121">Si noti che restituirà l'origine *dello sguardo* fisso con la testa se 'IsEyeGazeValid' è false.</span><span class="sxs-lookup"><span data-stu-id="f2c9d-121">Please note that this will return the *head* gaze origin if 'IsEyeGazeValid' is false.</span></span>

- <span data-ttu-id="f2c9d-122">**GazeDirection:** direzione del raggio dello sguardo fisso.</span><span class="sxs-lookup"><span data-stu-id="f2c9d-122">**GazeDirection**: Direction of the gaze ray.</span></span>
<span data-ttu-id="f2c9d-123">Verrà restituita la *direzione dello sguardo* con la testa se 'IsEyeGazeValid' è false.</span><span class="sxs-lookup"><span data-stu-id="f2c9d-123">This will return the *head* gaze direction if 'IsEyeGazeValid' is false.</span></span>

- <span data-ttu-id="f2c9d-124">**HitInfo,** **HitPosition,** **HitNormal** e così via: informazioni sull'oggetto attualmente rivolto verso la destinazione.</span><span class="sxs-lookup"><span data-stu-id="f2c9d-124">**HitInfo**, **HitPosition**, **HitNormal**, etc.: Information about the currently gazed at target.</span></span>
<span data-ttu-id="f2c9d-125">Anche in questo `IsEyeGazeValid` caso, se è false, si baserà sullo sguardo con la testa *dell'utente.*</span><span class="sxs-lookup"><span data-stu-id="f2c9d-125">Again, if `IsEyeGazeValid` is false, this will be based on the user's *head* gaze.</span></span>

## <a name="examples-for-using-coreservicesinputsystemeyegazeprovider"></a><span data-ttu-id="f2c9d-126">Esempi per l'uso di CoreServices.InputSystem.EyeGazeProvider</span><span class="sxs-lookup"><span data-stu-id="f2c9d-126">Examples for using CoreServices.InputSystem.EyeGazeProvider</span></span>

<span data-ttu-id="f2c9d-127">Di seguito è riportato un esempio [del file FollowEyeGaze.cs:](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.FollowEyeGaze)</span><span class="sxs-lookup"><span data-stu-id="f2c9d-127">Here is an example from the [FollowEyeGaze.cs](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.FollowEyeGaze):</span></span>

- <span data-ttu-id="f2c9d-128">Ottenere il punto di un ologramma che l'utente sta guardando:</span><span class="sxs-lookup"><span data-stu-id="f2c9d-128">Get the point of a hologram that the user is looking at:</span></span>

```c#
// Show the object at the hit position of the user's eye gaze ray with the target.
gameObject.transform.position = CoreServices.InputSystem.EyeGazeProvider.HitPosition;
```

- <span data-ttu-id="f2c9d-129">Visualizzazione di un asset visivo a una distanza fissa dalla posizione in cui l'utente sta attualmente cercando:</span><span class="sxs-lookup"><span data-stu-id="f2c9d-129">Showing a visual asset at a fixed distance from where the user is currently looking:</span></span>

```c#
// If no target is hit, show the object at a default distance along the gaze ray.
gameObject.transform.position =
CoreServices.InputSystem.EyeGazeProvider.GazeOrigin +
CoreServices.InputSystem.EyeGazeProvider.GazeDirection.normalized * defaultDistanceInMeters;
```

## <a name="see-also"></a><span data-ttu-id="f2c9d-130">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="f2c9d-130">See also</span></span>

- [<span data-ttu-id="f2c9d-131">Panoramica del tracciamento oculare di MRTK</span><span class="sxs-lookup"><span data-stu-id="f2c9d-131">MRTK Eye Tracking Overview</span></span>](eye-tracking-main.md)
- [<span data-ttu-id="f2c9d-132">Configurazione del tracciamento oculare di MRTK</span><span class="sxs-lookup"><span data-stu-id="f2c9d-132">MRTK Eye Tracking setup</span></span>](eye-tracking-basic-setup.md)
- [<span data-ttu-id="f2c9d-133">Calibrazione del tracciamento oculare MRTK</span><span class="sxs-lookup"><span data-stu-id="f2c9d-133">MRTK Eye Tracking Calibration</span></span>](eye-tracking-is-user-calibrated.md)
- [<span data-ttu-id="f2c9d-134">HoloLens 2 di tracciamento oculare</span><span class="sxs-lookup"><span data-stu-id="f2c9d-134">HoloLens 2 Eye Tracking Documentation</span></span>](/windows/mixed-reality/eye-tracking)
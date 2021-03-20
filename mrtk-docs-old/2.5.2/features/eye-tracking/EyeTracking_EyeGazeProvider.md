---
title: EyeTracking_EyeGazeProvider
description: Documentazione per il provider di sguardi con occhio in MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, EyeTracking, EyeGaze,
ms.openlocfilehash: 27b888ddcb9f6897da78b22e3d9fd486951366d0
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2021
ms.locfileid: "104683304"
---
# <a name="accessing-eye-tracking-data-in-your-unity-script"></a><span data-ttu-id="7234c-104">Accesso ai dati di rilevamento degli occhi nello script Unity</span><span class="sxs-lookup"><span data-stu-id="7234c-104">Accessing eye tracking data in your Unity script</span></span>

<span data-ttu-id="7234c-105">Questo articolo presuppone che si abbia la consapevolezza di configurare la registrazione degli occhi in una scena MRTK. vedere la pagina relativa [all'installazione di base di MRTK per l'uso di Eye Tracking](EyeTracking_BasicSetup.md).</span><span class="sxs-lookup"><span data-stu-id="7234c-105">This article assumes one has understanding for setting up eye tracking in an MRTK scene (see [Basic MRTK setup to use eye tracking](EyeTracking_BasicSetup.md)).</span></span>
<span data-ttu-id="7234c-106">L'accesso ai dati di rilevamento degli occhi in uno script monobehavior è facile.</span><span class="sxs-lookup"><span data-stu-id="7234c-106">Accessing eye tracking data in a MonoBehaviour script is easy!</span></span> <span data-ttu-id="7234c-107">Usare semplicemente *CoreServices. InputSystem. EyeGazeProvider*.</span><span class="sxs-lookup"><span data-stu-id="7234c-107">Simply use *CoreServices.InputSystem.EyeGazeProvider*.</span></span>

## <a name="imixedrealityeyegazeprovider"></a><span data-ttu-id="7234c-108">IMixedRealityEyeGazeProvider</span><span class="sxs-lookup"><span data-stu-id="7234c-108">IMixedRealityEyeGazeProvider</span></span>

<span data-ttu-id="7234c-109">La configurazione di rilevamento degli occhi in MRTK viene configurata tramite l' [`IMixedRealityEyeGazeProvider`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityEyeGazeProvider) interfaccia.</span><span class="sxs-lookup"><span data-stu-id="7234c-109">Eye tracking configuration in MRTK is configured via the [`IMixedRealityEyeGazeProvider`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityEyeGazeProvider) interface.</span></span> <span data-ttu-id="7234c-110">L'uso di [CoreServices. InputSystem. EyeGazeProvider](EyeTracking_EyeGazeProvider.md) fornisce l'implementazione predefinita del provider di sguardi registrata nel Toolkit in fase di esecuzione.</span><span class="sxs-lookup"><span data-stu-id="7234c-110">Using [CoreServices.InputSystem.EyeGazeProvider](EyeTracking_EyeGazeProvider.md) provides the default gaze provider implementation registered in the toolkit at runtime.</span></span>
<span data-ttu-id="7234c-111">Le proprietà utili di `EyeGazeProvider` sono descritte di seguito.</span><span class="sxs-lookup"><span data-stu-id="7234c-111">Useful properties of the `EyeGazeProvider` is outlined below.</span></span>

- <span data-ttu-id="7234c-112">**IsEyeTrackingEnabled**: true se l'utente ha scelto di usare la verifica degli sguardi.</span><span class="sxs-lookup"><span data-stu-id="7234c-112">**IsEyeTrackingEnabled**: True if user has selected to use eye tracking for gaze.</span></span>

- <span data-ttu-id="7234c-113">**IsEyeCalibrationValid**: indica se la calibrazione del rilevamento occhi dell'utente è valida o meno.</span><span class="sxs-lookup"><span data-stu-id="7234c-113">**IsEyeCalibrationValid**: Indicates whether the user's eye tracking calibration is valid or not.</span></span>
<span data-ttu-id="7234c-114">Restituisce ' null ', se il valore non ha ancora ricevuto dati dal sistema di rilevamento degli occhi.</span><span class="sxs-lookup"><span data-stu-id="7234c-114">It returns 'null', if the value has not yet received data from the eye tracking system.</span></span>
<span data-ttu-id="7234c-115">Potrebbe non essere valido perché l'utente ha ignorato la calibrazione del rilevamento degli occhi.</span><span class="sxs-lookup"><span data-stu-id="7234c-115">It may be invalid, because the user skipped the eye tracking calibration.</span></span>

- <span data-ttu-id="7234c-116">**IsEyeTrackingEnabledAndValid**: indica se i dati di rilevamento degli occhi correnti sono attualmente utilizzati per lo sguardo.</span><span class="sxs-lookup"><span data-stu-id="7234c-116">**IsEyeTrackingEnabledAndValid**: Indicates whether the current eye tracking data is currently been used for gaze.</span></span>

- <span data-ttu-id="7234c-117">**IsEyeTrackingDataValid**: true se i dati di rilevamento degli occhi sono disponibili.</span><span class="sxs-lookup"><span data-stu-id="7234c-117">**IsEyeTrackingDataValid**: True if eye tracking data is available.</span></span>
<span data-ttu-id="7234c-118">Potrebbe non essere disponibile a causa di un timeout superato (dovrebbe essere affidabile per l'utente lampeggiante) o se l'hardware o le autorizzazioni di rilevamento non sono sufficienti.</span><span class="sxs-lookup"><span data-stu-id="7234c-118">It may be unavailable due to exceeded timeout (should be robust to the user blinking though) or lack of tracking hardware or permissions.</span></span>
<span data-ttu-id="7234c-119">Vedere l'esempio di notifica per la [taratura degli occhi mancanti](EyeTracking_IsUserCalibrated.md) che spiega come rilevare se un utente è calibrato e visualizzare una notifica appropriata.</span><span class="sxs-lookup"><span data-stu-id="7234c-119">Check out our [Missing eye calibration notification sample](EyeTracking_IsUserCalibrated.md) that explains how to detect whether a user is eye calibrated and to show an appropriate notification.</span></span>

- <span data-ttu-id="7234c-120">**GazeOrigin**: origine del raggio di sguardi.</span><span class="sxs-lookup"><span data-stu-id="7234c-120">**GazeOrigin**: Origin of the gaze ray.</span></span>
<span data-ttu-id="7234c-121">Si noti che questa operazione restituirà l'origine dello sguardo a *capo* se ' IsEyeGazeValid ' è false.</span><span class="sxs-lookup"><span data-stu-id="7234c-121">Please note that this will return the *head* gaze origin if 'IsEyeGazeValid' is false.</span></span>

- <span data-ttu-id="7234c-122">**GazeDirection**: direzione del raggio di sguardi.</span><span class="sxs-lookup"><span data-stu-id="7234c-122">**GazeDirection**: Direction of the gaze ray.</span></span>
<span data-ttu-id="7234c-123">Se ' IsEyeGazeValid ' è false, verrà restituita la direzione dello sguardo *Head* .</span><span class="sxs-lookup"><span data-stu-id="7234c-123">This will return the *head* gaze direction if 'IsEyeGazeValid' is false.</span></span>

- <span data-ttu-id="7234c-124">**HitInfo**, **HitPosition**, **HitNormal** e così via: informazioni sull'oggetto attualmente guardato.</span><span class="sxs-lookup"><span data-stu-id="7234c-124">**HitInfo**, **HitPosition**, **HitNormal**, etc.: Information about the currently gazed at target.</span></span>
<span data-ttu-id="7234c-125">Anche in questo caso, se `IsEyeGazeValid` è false, questo sarà basato sullo sguardo a *capo* dell'utente.</span><span class="sxs-lookup"><span data-stu-id="7234c-125">Again, if `IsEyeGazeValid` is false, this will be based on the user's *head* gaze.</span></span>

## <a name="examples-for-using-coreservicesinputsystemeyegazeprovider"></a><span data-ttu-id="7234c-126">Esempi per l'uso di CoreServices. InputSystem. EyeGazeProvider</span><span class="sxs-lookup"><span data-stu-id="7234c-126">Examples for using CoreServices.InputSystem.EyeGazeProvider</span></span>

<span data-ttu-id="7234c-127">Di seguito è riportato un esempio di [FollowEyeGaze. cs](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.FollowEyeGaze):</span><span class="sxs-lookup"><span data-stu-id="7234c-127">Here is an example from the [FollowEyeGaze.cs](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.FollowEyeGaze):</span></span>

- <span data-ttu-id="7234c-128">Ottenere il punto di un ologramma esaminato dall'utente:</span><span class="sxs-lookup"><span data-stu-id="7234c-128">Get the point of a hologram that the user is looking at:</span></span>

```c#
// Show the object at the hit position of the user's eye gaze ray with the target.
gameObject.transform.position = CoreServices.InputSystem.EyeGazeProvider.HitPosition;
```

- <span data-ttu-id="7234c-129">Visualizzazione di un asset visivo a una distanza fissa dal punto in cui l'utente sta cercando:</span><span class="sxs-lookup"><span data-stu-id="7234c-129">Showing a visual asset at a fixed distance from where the user is currently looking:</span></span>

```c#
// If no target is hit, show the object at a default distance along the gaze ray.
gameObject.transform.position =
CoreServices.InputSystem.EyeGazeProvider.GazeOrigin +
CoreServices.InputSystem.EyeGazeProvider.GazeDirection.normalized * defaultDistanceInMeters;
```

## <a name="see-also"></a><span data-ttu-id="7234c-130">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="7234c-130">See also</span></span>

- [<span data-ttu-id="7234c-131">Panoramica di MRTK Eye Tracking</span><span class="sxs-lookup"><span data-stu-id="7234c-131">MRTK Eye Tracking Overview</span></span>](EyeTracking_Main.md)
- [<span data-ttu-id="7234c-132">Configurazione di MRTK Eye Tracking</span><span class="sxs-lookup"><span data-stu-id="7234c-132">MRTK Eye Tracking setup</span></span>](EyeTracking_BasicSetup.md)
- [<span data-ttu-id="7234c-133">Calibrazione di MRTK Eye Tracking</span><span class="sxs-lookup"><span data-stu-id="7234c-133">MRTK Eye Tracking Calibration</span></span>](EyeTracking_IsUserCalibrated.md)
- [<span data-ttu-id="7234c-134">Documentazione di HoloLens 2 Eye Tracking</span><span class="sxs-lookup"><span data-stu-id="7234c-134">HoloLens 2 Eye Tracking Documentation</span></span>](https://docs.microsoft.com/windows/mixed-reality/eye-tracking)

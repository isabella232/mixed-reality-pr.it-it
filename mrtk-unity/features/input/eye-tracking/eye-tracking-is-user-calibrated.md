---
title: Calibrazione oculare
description: Come configurare la calibrazione dell'occhio utente in MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realtà mista, sviluppo, MRTK, EyeTracking, Calibrazione,
ms.openlocfilehash: d7ae9885b77798b44b3d63bb7f92283658e05411
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144005"
---
# <a name="eye-calibration"></a><span data-ttu-id="e33c3-104">Calibrazione oculare</span><span class="sxs-lookup"><span data-stu-id="e33c3-104">Eye calibration</span></span>

![Screenshot della notifica di calibrazione oculare](../../images/eye-tracking/mrtk_et_calibration_notification_example.jpg)

## <a name="overview"></a><span data-ttu-id="e33c3-106">Panoramica</span><span class="sxs-lookup"><span data-stu-id="e33c3-106">Overview</span></span>

<span data-ttu-id="e33c3-107">Se il tracciamento oculare è una parte fondamentale dell'esperienza dell'app, è possibile assicurarsi che la calibrazione oculare dell'utente sia valida.</span><span class="sxs-lookup"><span data-stu-id="e33c3-107">If eye tracking is a fundamental part of your app experience, one may wish to ensure that the user's eye calibration is valid.</span></span>
<span data-ttu-id="e33c3-108">Il motivo principale per cui non è valido è che l'utente ha scelto di ignorare la calibrazione del tracciamento oculare durante l'inserimento del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="e33c3-108">The main reason for it to be invalid is that the user has chosen to skip the eye tracking calibration when putting on the device.</span></span>

<span data-ttu-id="e33c3-109">Questa pagina illustra quanto segue:</span><span class="sxs-lookup"><span data-stu-id="e33c3-109">This page covers the following:</span></span>

- <span data-ttu-id="e33c3-110">Descrive come rilevare che un utente è calibrato dagli occhi</span><span class="sxs-lookup"><span data-stu-id="e33c3-110">Describes how to detect that a user is eye calibrated</span></span>
- <span data-ttu-id="e33c3-111">Fornisce un esempio di come attivare una notifica utente per indicare all'utente di eseguire la calibrazione oculare</span><span class="sxs-lookup"><span data-stu-id="e33c3-111">Provides a sample for how to trigger a user notification to instruct the user to go through the eye calibration</span></span>
  - <span data-ttu-id="e33c3-112">Ignora automaticamente la notifica se la calibrazione oculare diventa valida</span><span class="sxs-lookup"><span data-stu-id="e33c3-112">Automatically dismiss notification if eye calibration becomes valid</span></span>
  - <span data-ttu-id="e33c3-113">Ignorare manualmente la notifica se l'utente sceglie di continuare senza calibrazione</span><span class="sxs-lookup"><span data-stu-id="e33c3-113">Manually dismiss notification if user chooses to continue without calibration</span></span>

### <a name="how-to-detect-the-eye-calibration-state"></a><span data-ttu-id="e33c3-114">Come rilevare lo stato di calibrazione oculare</span><span class="sxs-lookup"><span data-stu-id="e33c3-114">How to detect the eye calibration state</span></span>

<span data-ttu-id="e33c3-115">La configurazione del tracciamento oculare in MRTK viene configurata tramite [`IMixedRealityEyeGazeProvider`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityEyeGazeProvider) l'interfaccia .</span><span class="sxs-lookup"><span data-stu-id="e33c3-115">Eye tracking configuration in MRTK is configured via the [`IMixedRealityEyeGazeProvider`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityEyeGazeProvider) interface.</span></span>

<span data-ttu-id="e33c3-116">[L'uso di CoreServices.InputSystem.EyeGazeProvider fornisce](eye-tracking-eye-gaze-provider.md) l'implementazione predefinita del provider gaze registrato nel toolkit in fase di esecuzione.</span><span class="sxs-lookup"><span data-stu-id="e33c3-116">Using [CoreServices.InputSystem.EyeGazeProvider](eye-tracking-eye-gaze-provider.md) provides the default gaze provider implementation registered in the toolkit at runtime.</span></span> <span data-ttu-id="e33c3-117">`IMixedRealityEyeGazeProvider.IsEyeGazeValid` restituisce un valore null se non sono ancora disponibili informazioni dal `bool?` tracciamento oculare.</span><span class="sxs-lookup"><span data-stu-id="e33c3-117">`IMixedRealityEyeGazeProvider.IsEyeGazeValid` returns a `bool?` which is null if no information from the eye tracker is available yet.</span></span>
<span data-ttu-id="e33c3-118">Dopo la ricezione, i dati restituiranno true o false per indicare che la calibrazione del tracciamento oculare dell'utente è valida o non valida.</span><span class="sxs-lookup"><span data-stu-id="e33c3-118">Once data has been received, it will either return true or false to indicate that the user's eye tracking calibration is valid or invalid.</span></span>

### <a name="sample-eye-calibration-notification---step-by-step"></a><span data-ttu-id="e33c3-119">Notifica di calibrazione oculare di esempio - procedura dettagliata</span><span class="sxs-lookup"><span data-stu-id="e33c3-119">Sample eye calibration notification - step-by-step</span></span>

1. <span data-ttu-id="e33c3-120">Aprire il pacchetto di esempio di tracciamento oculare MRTK (Assets/MRTK/Examples/Demos/EyeTracking)</span><span class="sxs-lookup"><span data-stu-id="e33c3-120">Open the MRTK eye tracking example package (Assets/MRTK/Examples/Demos/EyeTracking)</span></span>

2. <span data-ttu-id="e33c3-121">Caricare _la scena EyeTrackingDemo-00-RootScene.unity_</span><span class="sxs-lookup"><span data-stu-id="e33c3-121">Load _EyeTrackingDemo-00-RootScene.unity_ scene</span></span>

3. <span data-ttu-id="e33c3-122">Vedere _EyeCalibrationChecker:_</span><span class="sxs-lookup"><span data-stu-id="e33c3-122">Check out _EyeCalibrationChecker_:</span></span>
   - <span data-ttu-id="e33c3-123">In questa scena è già disponibile un esempio per rilevare se l'utente corrente è calibrato nell'oggetto gioco *_EyeCalibrationChecker_*.</span><span class="sxs-lookup"><span data-stu-id="e33c3-123">In this scene, we have already a sample for detecting whether the current user is calibrated under the *_EyeCalibrationChecker_ game object*.</span></span>
<span data-ttu-id="e33c3-124">Contiene semplicemente alcune mesh di testo e include alcuni trigger aggiuntivi per la fusione della notifica in e in uscita. Ciò include l'aumento lento delle dimensioni e dell'opacità all'attivazione.</span><span class="sxs-lookup"><span data-stu-id="e33c3-124">It simply parents a few text meshes and has some additional triggers for blending the notification in and out. This includes slowly increasing its size and opacity on activation.</span></span>
<span data-ttu-id="e33c3-125">Una volta chiusa, la notifica diminuisce lentamente le dimensioni e si dissolve in uscita.</span><span class="sxs-lookup"><span data-stu-id="e33c3-125">Once the notification is dismissed, it will slowly decrease its size and fade out.</span></span>

   - <span data-ttu-id="e33c3-126">Associato *_all'oggetto gioco EyeCalibrationChecker_* è lo script [EyeCalibrationChecker](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.EyeCalibrationChecker) che espone due eventi unity:</span><span class="sxs-lookup"><span data-stu-id="e33c3-126">Attached to the *_EyeCalibrationChecker_ game object* is the [EyeCalibrationChecker](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.EyeCalibrationChecker) script which exposes two Unity Events:</span></span>
      - `OnEyeCalibrationDetected()`
      - `OnNoEyeCalibrationDetected()`

   - <span data-ttu-id="e33c3-127">Questi eventi verranno attivati solo se lo stato di calibrazione cambia.</span><span class="sxs-lookup"><span data-stu-id="e33c3-127">These events will only trigger if the calibration status changes.</span></span> <span data-ttu-id="e33c3-128">Di conseguenza, se un utente sceglie di ignorare la notifica, la notifica non verrà visualizzata di nuovo fino a quando</span><span class="sxs-lookup"><span data-stu-id="e33c3-128">Hence, if a user chooses to dismiss the notification, the notification will not show up again until</span></span>
      - <span data-ttu-id="e33c3-129">L'app viene riavviata</span><span class="sxs-lookup"><span data-stu-id="e33c3-129">The app gets restarted</span></span>
      - <span data-ttu-id="e33c3-130">È stato rilevato un utente valido e quindi un nuovo utente non certificato ha inserito il dispositivo</span><span class="sxs-lookup"><span data-stu-id="e33c3-130">A valid user has been detected and then a new uncalibrated user has put the device on</span></span>

   - <span data-ttu-id="e33c3-131">Per verificare se le animazioni e gli eventi vengono attivati correttamente, lo script EyeCalibrationChecker possiede un `bool editorTestUserIsCalibrated` flag.</span><span class="sxs-lookup"><span data-stu-id="e33c3-131">For testing whether the animations and events are triggered correctly, the EyeCalibrationChecker script possesses a `bool editorTestUserIsCalibrated` flag.</span></span> <span data-ttu-id="e33c3-132">Ad esempio, quando si esegue nell'editor di Unity, è possibile testare:</span><span class="sxs-lookup"><span data-stu-id="e33c3-132">For example, when running in the Unity Editor, one can test:</span></span>
      1. <span data-ttu-id="e33c3-133">Indica se la notifica viene visualizzata automaticamente quando lo stato di calibrazione cambia da true a false</span><span class="sxs-lookup"><span data-stu-id="e33c3-133">Whether the notification automatically pops up once the calibration status changes from true to false</span></span>
      1. <span data-ttu-id="e33c3-134">Indica se la notifica viene chiusa automaticamente quando lo stato cambia da false a true.</span><span class="sxs-lookup"><span data-stu-id="e33c3-134">Whether it automatically dismisses the notification again once the status changes from false to true.</span></span>

```c#
    private bool? prevCalibrationStatus = null;
    ...

   void Update()
   {
      // Get the latest calibration state from the EyeGazeProvider
      bool? calibrationStatus = CoreServices.InputSystem?.EyeGazeProvider?.IsEyeCalibrationValid;

      ...

      if (calibrationStatus != null)
      {
         if (prevCalibrationStatus != calibrationStatus)
         {
            if (calibrationStatus == false)
            {
               OnNoEyeCalibrationDetected.Invoke();
            }
         else
         {
            OnEyeCalibrationDetected.Invoke();
         }

         prevCalibrationStatus = calibrationStatus;
      }
   }
```

## <a name="see-also"></a><span data-ttu-id="e33c3-135">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="e33c3-135">See also</span></span>

- [<span data-ttu-id="e33c3-136">Panoramica del tracciamento oculare di MRTK</span><span class="sxs-lookup"><span data-stu-id="e33c3-136">MRTK Eye Tracking Overview</span></span>](eye-tracking-main.md)
- [<span data-ttu-id="e33c3-137">Configurazione del tracciamento oculare di MRTK</span><span class="sxs-lookup"><span data-stu-id="e33c3-137">MRTK Eye Tracking setup</span></span>](eye-tracking-basic-setup.md)
- [<span data-ttu-id="e33c3-138">Tracciamento oculare MRTK tramite codice</span><span class="sxs-lookup"><span data-stu-id="e33c3-138">MRTK Eye Tracking via Code</span></span>](eye-tracking-eye-gaze-provider.md)
- [<span data-ttu-id="e33c3-139">HoloLens 2 di tracciamento oculare</span><span class="sxs-lookup"><span data-stu-id="e33c3-139">HoloLens 2 Eye Tracking Documentation</span></span>](/windows/mixed-reality/eye-tracking)
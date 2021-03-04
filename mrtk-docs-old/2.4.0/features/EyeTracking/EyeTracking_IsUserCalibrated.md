---
title: EyeTracking_IsUserCalibrated
description: Come configurare la calibrazione degli occhi degli utenti in MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, EyeTracking, calibrazione,
ms.openlocfilehash: ea7b0a30426ecc92f7f571b0346d78c656ec7ee8
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/03/2021
ms.locfileid: "101781916"
---
# <a name="eye-calibration"></a><span data-ttu-id="77e46-104">Calibrazione degli occhi</span><span class="sxs-lookup"><span data-stu-id="77e46-104">Eye calibration</span></span>

![Screenshot della notifica di calibrazione degli occhi](../Images/EyeTracking/mrtk_et_calibration_notification_example.jpg)

## <a name="overview"></a><span data-ttu-id="77e46-106">Panoramica</span><span class="sxs-lookup"><span data-stu-id="77e46-106">Overview</span></span>

<span data-ttu-id="77e46-107">Se il rilevamento degli occhi è una parte fondamentale dell'esperienza dell'app, è possibile che si voglia assicurarsi che la calibrazione degli occhi dell'utente sia valida.</span><span class="sxs-lookup"><span data-stu-id="77e46-107">If eye tracking is a fundamental part of your app experience, one may wish to ensure that the user's eye calibration is valid.</span></span>
<span data-ttu-id="77e46-108">Il motivo principale per cui non è valido è che l'utente ha scelto di ignorare la calibrazione del rilevamento degli occhi quando si inserisce il dispositivo.</span><span class="sxs-lookup"><span data-stu-id="77e46-108">The main reason for it to be invalid is that the user has chosen to skip the eye tracking calibration when putting on the device.</span></span>

<span data-ttu-id="77e46-109">In questa pagina vengono illustrati gli elementi seguenti:</span><span class="sxs-lookup"><span data-stu-id="77e46-109">This page covers the following:</span></span>

- <span data-ttu-id="77e46-110">Viene descritto come rilevare che un utente è a occhio calibrato</span><span class="sxs-lookup"><span data-stu-id="77e46-110">Describes how to detect that a user is eye calibrated</span></span>
- <span data-ttu-id="77e46-111">Fornisce un esempio su come attivare una notifica utente per indicare all'utente di esaminare la calibrazione degli occhi</span><span class="sxs-lookup"><span data-stu-id="77e46-111">Provides a sample for how to trigger a user notification to instruct the user to go through the eye calibration</span></span>
  - <span data-ttu-id="77e46-112">Ignora automaticamente la notifica se la calibrazione dell'occhio diventa valida</span><span class="sxs-lookup"><span data-stu-id="77e46-112">Automatically dismiss notification if eye calibration becomes valid</span></span>
  - <span data-ttu-id="77e46-113">Ignora manualmente la notifica se l'utente sceglie di continuare senza calibrazione</span><span class="sxs-lookup"><span data-stu-id="77e46-113">Manually dismiss notification if user chooses to continue without calibration</span></span>

### <a name="how-to-detect-the-eye-calibration-state"></a><span data-ttu-id="77e46-114">Come rilevare lo stato della taratura degli occhi</span><span class="sxs-lookup"><span data-stu-id="77e46-114">How to detect the eye calibration state</span></span>

<span data-ttu-id="77e46-115">La configurazione di rilevamento degli occhi in MRTK viene configurata tramite l' [`IMixedRealityEyeGazeProvider`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityEyeGazeProvider) interfaccia.</span><span class="sxs-lookup"><span data-stu-id="77e46-115">Eye tracking configuration in MRTK is configured via the [`IMixedRealityEyeGazeProvider`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityEyeGazeProvider) interface.</span></span>

<span data-ttu-id="77e46-116">L'uso di [CoreServices. InputSystem. EyeGazeProvider](EyeTracking_EyeGazeProvider.md) fornisce l'implementazione predefinita del provider di sguardi registrata nel Toolkit in fase di esecuzione.</span><span class="sxs-lookup"><span data-stu-id="77e46-116">Using [CoreServices.InputSystem.EyeGazeProvider](EyeTracking_EyeGazeProvider.md) provides the default gaze provider implementation registered in the toolkit at runtime.</span></span> <span data-ttu-id="77e46-117">`IMixedRealityEyeGazeProvider.IsEyeGazeValid` Restituisce un `bool?` valore che è null se non sono ancora disponibili informazioni dallo strumento di analisi degli occhi.</span><span class="sxs-lookup"><span data-stu-id="77e46-117">`IMixedRealityEyeGazeProvider.IsEyeGazeValid` returns a `bool?` which is null if no information from the eye tracker is available yet.</span></span>
<span data-ttu-id="77e46-118">Una volta ricevuti i dati, verrà restituito true o false per indicare che la calibrazione del rilevamento occhi dell'utente è valida o non valida.</span><span class="sxs-lookup"><span data-stu-id="77e46-118">Once data has been received, it will either return true or false to indicate that the user's eye tracking calibration is valid or invalid.</span></span>

### <a name="sample-eye-calibration-notification---step-by-step"></a><span data-ttu-id="77e46-119">Esempio di notifica di calibrazione degli occhi-procedura dettagliata</span><span class="sxs-lookup"><span data-stu-id="77e46-119">Sample eye calibration notification - step-by-step</span></span>

1. <span data-ttu-id="77e46-120">Aprire il pacchetto di esempio di rilevamento degli occhi di MRTK (assets/MRTK/examples/Demos/EyeTracking)</span><span class="sxs-lookup"><span data-stu-id="77e46-120">Open the MRTK eye tracking example package (Assets/MRTK/Examples/Demos/EyeTracking)</span></span>

2. <span data-ttu-id="77e46-121">Caricare la scena _EyeTrackingDemo-00-RootScene. Unity_</span><span class="sxs-lookup"><span data-stu-id="77e46-121">Load _EyeTrackingDemo-00-RootScene.unity_ scene</span></span>

3. <span data-ttu-id="77e46-122">Vedere _EyeCalibrationChecker_:</span><span class="sxs-lookup"><span data-stu-id="77e46-122">Check out _EyeCalibrationChecker_:</span></span>
   - <span data-ttu-id="77e46-123">In questa scena è già presente un esempio per rilevare se l'utente corrente è calibrato nell' *oggetto del gioco _EyeCalibrationChecker_*.</span><span class="sxs-lookup"><span data-stu-id="77e46-123">In this scene, we have already a sample for detecting whether the current user is calibrated under the *_EyeCalibrationChecker_ game object*.</span></span>
<span data-ttu-id="77e46-124">Si tratta semplicemente di un numero ridotto di mesh di testo che include alcuni trigger aggiuntivi per la fusione della notifica. Sono incluse le dimensioni e l'opacità che aumentano all'attivazione.</span><span class="sxs-lookup"><span data-stu-id="77e46-124">It simply parents a few text meshes and has some additional triggers for blending the notification in and out. This includes slowly increasing its size and opacity on activation.</span></span>
<span data-ttu-id="77e46-125">Quando la notifica viene rilasciata, diminuisce lentamente le sue dimensioni e si dissolve in uscita.</span><span class="sxs-lookup"><span data-stu-id="77e46-125">Once the notification is dismissed, it will slowly decrease its size and fade out.</span></span>

   - <span data-ttu-id="77e46-126">Collegato all' *oggetto gioco _EyeCalibrationChecker_* è lo script [EyeCalibrationChecker](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.EyeCalibrationChecker) che espone due eventi Unity:</span><span class="sxs-lookup"><span data-stu-id="77e46-126">Attached to the *_EyeCalibrationChecker_ game object* is the [EyeCalibrationChecker](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.EyeCalibrationChecker) script which exposes two Unity Events:</span></span>
      - `OnEyeCalibrationDetected()`
      - `OnNoEyeCalibrationDetected()`

   - <span data-ttu-id="77e46-127">Questi eventi vengono attivati solo se lo stato della calibrazione viene modificato.</span><span class="sxs-lookup"><span data-stu-id="77e46-127">These events will only trigger if the calibration status changes.</span></span> <span data-ttu-id="77e46-128">Di conseguenza, se un utente sceglie di ignorare la notifica, la notifica non verrà più visualizzata fino a quando non</span><span class="sxs-lookup"><span data-stu-id="77e46-128">Hence, if a user chooses to dismiss the notification, the notification will not show up again until</span></span>
      - <span data-ttu-id="77e46-129">L'app viene riavviata</span><span class="sxs-lookup"><span data-stu-id="77e46-129">The app gets restarted</span></span>
      - <span data-ttu-id="77e46-130">È stato rilevato un utente valido e quindi un nuovo utente non calibrato ha inserito il dispositivo</span><span class="sxs-lookup"><span data-stu-id="77e46-130">A valid user has been detected and then a new uncalibrated user has put the device on</span></span>

   - <span data-ttu-id="77e46-131">Per verificare se le animazioni e gli eventi vengono attivati correttamente, lo script EyeCalibrationChecker possiede un `bool editorTestUserIsCalibrated` flag.</span><span class="sxs-lookup"><span data-stu-id="77e46-131">For testing whether the animations and events are triggered correctly, the EyeCalibrationChecker script possesses a `bool editorTestUserIsCalibrated` flag.</span></span> <span data-ttu-id="77e46-132">Ad esempio, in caso di esecuzione nell'editor di Unity, è possibile eseguire un test:</span><span class="sxs-lookup"><span data-stu-id="77e46-132">For example, when running in the Unity Editor, one can test:</span></span>
      1. <span data-ttu-id="77e46-133">Indica se la notifica viene visualizzata automaticamente quando lo stato della calibrazione passa da true a false</span><span class="sxs-lookup"><span data-stu-id="77e46-133">Whether the notification automatically pops up once the calibration status changes from true to false</span></span>
      1. <span data-ttu-id="77e46-134">Indica se la notifica viene rilasciata automaticamente quando lo stato viene modificato da false a true.</span><span class="sxs-lookup"><span data-stu-id="77e46-134">Whether it automatically dismisses the notification again once the status changes from false to true.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="77e46-135">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="77e46-135">See also</span></span>

- [<span data-ttu-id="77e46-136">Panoramica di MRTK Eye Tracking</span><span class="sxs-lookup"><span data-stu-id="77e46-136">MRTK Eye Tracking Overview</span></span>](EyeTracking_Main.md)
- [<span data-ttu-id="77e46-137">Configurazione di MRTK Eye Tracking</span><span class="sxs-lookup"><span data-stu-id="77e46-137">MRTK Eye Tracking setup</span></span>](EyeTracking_BasicSetup.md)
- [<span data-ttu-id="77e46-138">MRTK la verifica degli occhi tramite codice</span><span class="sxs-lookup"><span data-stu-id="77e46-138">MRTK Eye Tracking via Code</span></span>](EyeTracking_EyeGazeProvider.md)
- [<span data-ttu-id="77e46-139">Documentazione di HoloLens 2 Eye Tracking</span><span class="sxs-lookup"><span data-stu-id="77e46-139">HoloLens 2 Eye Tracking Documentation</span></span>](https://docs.microsoft.com/windows/mixed-reality/eye-tracking)

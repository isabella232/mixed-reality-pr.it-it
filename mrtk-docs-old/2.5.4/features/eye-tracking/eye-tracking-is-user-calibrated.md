---
title: EyeTracking_IsUserCalibrated
description: Come configurare la calibrazione degli occhi degli utenti in MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, EyeTracking, calibrazione,
ms.openlocfilehash: c3a21ec35f245972401193257d67902b381b3b30
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/03/2021
ms.locfileid: "101783774"
---
# <a name="eye-calibration"></a>Calibrazione degli occhi

![Screenshot della notifica di calibrazione degli occhi](../images/eye-tracking/mrtk_et_calibration_notification_example.jpg)

## <a name="overview"></a>Panoramica

Se il rilevamento degli occhi è una parte fondamentale dell'esperienza dell'app, è possibile che si voglia assicurarsi che la calibrazione degli occhi dell'utente sia valida.
Il motivo principale per cui non è valido è che l'utente ha scelto di ignorare la calibrazione del rilevamento degli occhi quando si inserisce il dispositivo.

In questa pagina vengono illustrati gli elementi seguenti:

- Viene descritto come rilevare che un utente è a occhio calibrato
- Fornisce un esempio su come attivare una notifica utente per indicare all'utente di esaminare la calibrazione degli occhi
  - Ignora automaticamente la notifica se la calibrazione dell'occhio diventa valida
  - Ignora manualmente la notifica se l'utente sceglie di continuare senza calibrazione

### <a name="how-to-detect-the-eye-calibration-state"></a>Come rilevare lo stato della taratura degli occhi

La configurazione di rilevamento degli occhi in MRTK viene configurata tramite l' [`IMixedRealityEyeGazeProvider`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityEyeGazeProvider) interfaccia.

L'uso di [CoreServices. InputSystem. EyeGazeProvider](eye-tracking-eye-gaze-provider.md) fornisce l'implementazione predefinita del provider di sguardi registrata nel Toolkit in fase di esecuzione. `IMixedRealityEyeGazeProvider.IsEyeGazeValid` Restituisce un `bool?` valore che è null se non sono ancora disponibili informazioni dallo strumento di analisi degli occhi.
Una volta ricevuti i dati, verrà restituito true o false per indicare che la calibrazione del rilevamento occhi dell'utente è valida o non valida.

### <a name="sample-eye-calibration-notification---step-by-step"></a>Esempio di notifica di calibrazione degli occhi-procedura dettagliata

1. Aprire il pacchetto di esempio di rilevamento degli occhi di MRTK (assets/MRTK/examples/Demos/EyeTracking)

2. Caricare la scena _EyeTrackingDemo-00-RootScene. Unity_

3. Vedere _EyeCalibrationChecker_:
   - In questa scena è già presente un esempio per rilevare se l'utente corrente è calibrato nell' *oggetto del gioco _EyeCalibrationChecker_*.
Si tratta semplicemente di un numero ridotto di mesh di testo che include alcuni trigger aggiuntivi per la fusione della notifica. Sono incluse le dimensioni e l'opacità che aumentano all'attivazione.
Quando la notifica viene rilasciata, diminuisce lentamente le sue dimensioni e si dissolve in uscita.

   - Collegato all' *oggetto gioco _EyeCalibrationChecker_* è lo script [EyeCalibrationChecker](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.EyeCalibrationChecker) che espone due eventi Unity:
      - `OnEyeCalibrationDetected()`
      - `OnNoEyeCalibrationDetected()`

   - Questi eventi vengono attivati solo se lo stato della calibrazione viene modificato. Di conseguenza, se un utente sceglie di ignorare la notifica, la notifica non verrà più visualizzata fino a quando non
      - L'app viene riavviata
      - È stato rilevato un utente valido e quindi un nuovo utente non calibrato ha inserito il dispositivo

   - Per verificare se le animazioni e gli eventi vengono attivati correttamente, lo script EyeCalibrationChecker possiede un `bool editorTestUserIsCalibrated` flag. Ad esempio, in caso di esecuzione nell'editor di Unity, è possibile eseguire un test:
      1. Indica se la notifica viene visualizzata automaticamente quando lo stato della calibrazione passa da true a false
      1. Indica se la notifica viene rilasciata automaticamente quando lo stato viene modificato da false a true.

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

## <a name="see-also"></a>Vedi anche

- [Panoramica di MRTK Eye Tracking](eye-tracking-main.md)
- [Configurazione di MRTK Eye Tracking](eye-tracking-basic-setup.md)
- [MRTK la verifica degli occhi tramite codice](eye-tracking-eye-gaze-provider.md)
- [Documentazione di HoloLens 2 Eye Tracking](https://docs.microsoft.com/windows/mixed-reality/eye-tracking)

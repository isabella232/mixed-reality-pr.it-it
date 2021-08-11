---
title: Calibrazione oculare
description: Come configurare la calibrazione dell'occhio dell'utente in MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, tracciamento oculare, calibrazione,
ms.openlocfilehash: 02b173bbc7a6bf410d3521b37660f292b8e3340de6b1a98007fdbc200f26bc49
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115199770"
---
# <a name="eye-calibration"></a>Calibrazione oculare

![Screenshot della notifica di calibrazione oculare](../../images/eye-tracking/mrtk_et_calibration_notification_example.jpg)

## <a name="overview"></a>Panoramica

Se il tracciamento oculare è una parte fondamentale dell'esperienza dell'app, è possibile assicurarsi che la calibrazione oculare dell'utente sia valida.
Il motivo principale per cui non è valido è che l'utente ha scelto di ignorare la calibrazione del tracciamento oculare quando si mette sul dispositivo.

Questa pagina illustra quanto segue:

- Descrive come rilevare che un utente è calibrato con gli occhi
- Fornisce un esempio di come attivare una notifica utente per indicare all'utente di eseguire la calibrazione oculare
  - Ignora automaticamente la notifica se la calibrazione oculare diventa valida
  - Ignorare manualmente la notifica se l'utente sceglie di continuare senza calibrazione

### <a name="how-to-detect-the-eye-calibration-state"></a>Come rilevare lo stato di calibrazione oculare

La configurazione del tracciamento oculare in MRTK viene configurata tramite [`IMixedRealityEyeGazeProvider`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityEyeGazeProvider) l'interfaccia .

[L'uso di CoreServices.InputSystem.EyeGazeProvider fornisce](eye-tracking-eye-gaze-provider.md) l'implementazione predefinita del provider di sguardo fisso registrata nel toolkit in fase di esecuzione. `IMixedRealityEyeGazeProvider.IsEyeGazeValid` restituisce un valore null se non sono ancora disponibili informazioni `bool?` dallo strumento di tracciamento oculare.
Dopo la ricezione dei dati, restituirà true o false per indicare che la calibrazione del tracciamento oculare dell'utente è valida o non valida.

### <a name="sample-eye-calibration-notification---step-by-step"></a>Notifica di calibrazione oculare di esempio - procedura dettagliata

1. Aprire il pacchetto di esempio di tracciamento oculare MRTK (Assets/MRTK/Examples/Demos/EyeTracking)

2. Scena _Load EyeTrackingDemo-00-RootScene.unity_

3. Vedere _EyeCalibrationChecker:_
   - In questa scena è già disponibile un esempio per rilevare se l'utente corrente è calibrato nell'oggetto gioco *_EyeCalibrationChecker_*.
Contiene semplicemente alcune mesh di testo e include alcuni trigger aggiuntivi per la fusione della notifica in e in uscita. Ciò include l'aumento lento delle dimensioni e dell'opacità all'attivazione.
Una volta chiusa, la notifica diminuisce lentamente le dimensioni e si dissolve in uscita.

   - Associato *_all'oggetto gioco EyeCalibrationChecker_* è lo script [EyeCalibrationChecker](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.EyeCalibrationChecker) che espone due eventi unity:
      - `OnEyeCalibrationDetected()`
      - `OnNoEyeCalibrationDetected()`

   - Questi eventi verranno attivati solo se lo stato di calibrazione cambia. Di conseguenza, se un utente sceglie di ignorare la notifica, la notifica non verrà visualizzata di nuovo fino a quando
      - L'app viene riavviata
      - È stato rilevato un utente valido e quindi un nuovo utente non certificato ha inserito il dispositivo

   - Per verificare se le animazioni e gli eventi vengono attivati correttamente, lo script EyeCalibrationChecker possiede un `bool editorTestUserIsCalibrated` flag . Ad esempio, quando si esegue nell'editor di Unity, è possibile testare:
      1. Indica se la notifica viene visualizzata automaticamente quando lo stato di calibrazione cambia da true a false
      1. Indica se la notifica viene chiusa automaticamente quando lo stato cambia da false a true.

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

- [Panoramica del tracciamento oculare di MRTK](eye-tracking-main.md)
- [Configurazione del tracciamento oculare di MRTK](eye-tracking-basic-setup.md)
- [Tracciamento oculare MRTK tramite codice](eye-tracking-eye-gaze-provider.md)
- [HoloLens 2 Documentazione sul tracciamento oculare](/windows/mixed-reality/eye-tracking)

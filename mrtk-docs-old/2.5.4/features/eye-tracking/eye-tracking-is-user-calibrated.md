---
title: EyeTracking_IsUserCalibrated
description: Come configurare la calibrazione dell'occhio utente in MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, EyeTracking, Calibrazione,
ms.openlocfilehash: 69a8882b6b90af6610b6d7a4d77cc016730e0f18df161c1ffb28f908b986ca5f
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115211637"
---
# <a name="eye-calibration"></a>Calibrazione oculare

![Screenshot della notifica di calibrazione oculare](../images/eye-tracking/mrtk_et_calibration_notification_example.jpg)

## <a name="overview"></a>Panoramica

Se il tracciamento oculare è una parte fondamentale dell'esperienza dell'app, è possibile assicurarsi che la calibrazione oculare dell'utente sia valida.
Il motivo principale per cui non è valido è che l'utente ha scelto di ignorare la calibrazione del tracciamento oculare durante l'inserimento del dispositivo.

Questa pagina illustra quanto segue:

- Descrive come rilevare la calibrazione oculare di un utente
- Fornisce un esempio di come attivare una notifica utente per indicare all'utente di eseguire la calibrazione oculare
  - Ignora automaticamente la notifica se la calibrazione oculare diventa valida
  - Ignorare manualmente la notifica se l'utente sceglie di continuare senza calibrazione

### <a name="how-to-detect-the-eye-calibration-state"></a>Come rilevare lo stato di calibrazione oculare

La configurazione del tracciamento oculare in MRTK viene configurata tramite [`IMixedRealityEyeGazeProvider`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityEyeGazeProvider) l'interfaccia .

[L'uso di CoreServices.InputSystem.EyeGazeProvider fornisce](eye-tracking-eye-gaze-provider.md) l'implementazione predefinita del provider gaze registrato nel toolkit in fase di esecuzione. `IMixedRealityEyeGazeProvider.IsEyeGazeValid` restituisce un valore null se non sono ancora disponibili informazioni dal `bool?` tracciamento oculare.
Dopo la ricezione, i dati restituiranno true o false per indicare che la calibrazione del tracciamento oculare dell'utente è valida o non valida.

### <a name="sample-eye-calibration-notification---step-by-step"></a>Notifica di calibrazione oculare di esempio - procedura dettagliata

1. Aprire il pacchetto di esempio di tracciamento oculare MRTK (Assets/MRTK/Examples/Demos/EyeTracking)

2. Caricare _la scena EyeTrackingDemo-00-RootScene.unity_

3. Vedere _EyeCalibrationChecker:_
   - In questa scena è già disponibile un esempio per rilevare se l'utente corrente è calibrato nell'oggetto di gioco *_EyeCalibrationChecker_*.
Contiene semplicemente alcune mesh di testo e include alcuni trigger aggiuntivi per la fusione della notifica in e out. Ciò include l'aumento lento delle dimensioni e dell'opacità all'attivazione.
Una volta chiusa, la notifica ridurrà lentamente le dimensioni e si dissolverà.

   - Associato *_all'oggetto gioco EyeCalibrationChecker_* è lo script [EyeCalibrationChecker](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.EyeCalibrationChecker) che espone due eventi Unity:
      - `OnEyeCalibrationDetected()`
      - `OnNoEyeCalibrationDetected()`

   - Questi eventi verranno attivati solo se lo stato di calibrazione cambia. Di conseguenza, se un utente sceglie di ignorare la notifica, la notifica non verrà visualizzata di nuovo fino a quando
      - L'app viene riavviata
      - È stato rilevato un utente valido e quindi un nuovo utente non bilanciato ha inserito il dispositivo

   - Per verificare se le animazioni e gli eventi vengono attivati correttamente, lo script EyeCalibrationChecker dispone di un `bool editorTestUserIsCalibrated` flag. Ad esempio, quando si esegue nell'editor di Unity, è possibile testare:
      1. Indica se la notifica viene visualizzata automaticamente quando lo stato della calibrazione cambia da true a false
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

- [Panoramica del tracciamento oculare MRTK](eye-tracking-main.md)
- [Configurazione di MrTK Eye Tracking](eye-tracking-basic-setup.md)
- [Tracciamento oculare MRTK tramite codice](eye-tracking-eye-gaze-provider.md)
- [HoloLens 2 Documentazione sul tracciamento oculare](https://docs.microsoft.com/windows/mixed-reality/eye-tracking)

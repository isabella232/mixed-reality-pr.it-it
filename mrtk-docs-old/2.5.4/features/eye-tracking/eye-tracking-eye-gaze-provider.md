---
title: EyeTracking_EyeGazeProvider
description: Documentazione per il provider Eye Gaze in MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realtà mista, sviluppo, MRTK, EyeTracking, EyeGaze,
ms.openlocfilehash: 943ac8d4bdd7943e337d832aeef7239a254c3e1f3086620d561de1daa7a23080
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115197689"
---
# <a name="accessing-eye-tracking-data-in-your-unity-script"></a>Accesso ai dati di tracciamento oculare nello script unity

Questo articolo presuppone che si abbia una conoscenza per la configurazione del tracciamento oculare in una scena MRTK (vedere Configurazione MRTK di base per [l'uso del tracciamento oculare](eye-tracking-basic-setup.md)).
L'accesso ai dati di tracciamento oculare in uno script MonoBehaviour è semplice. È sufficiente *usare CoreServices.InputSystem.EyeGazeProvider*.

## <a name="imixedrealityeyegazeprovider"></a>IMixedRealityEyeGazeProvider

La configurazione del tracciamento oculare in MRTK viene configurata tramite [`IMixedRealityEyeGazeProvider`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityEyeGazeProvider) l'interfaccia . [L'uso di CoreServices.InputSystem.EyeGazeProvider fornisce](eye-tracking-eye-gaze-provider.md) l'implementazione predefinita del provider gaze registrato nel toolkit in fase di esecuzione.
Le proprietà utili `EyeGazeProvider` dell'oggetto sono descritte di seguito.

- **IsEyeTrackingEnabled:** True se l'utente ha scelto di usare il tracciamento oculare per lo sguardo.

- **IsEyeCalibrationValid:** indica se la calibrazione del tracciamento oculare dell'utente è valida o meno.
Restituisce "null", se il valore non ha ancora ricevuto dati dal sistema di tracciamento oculare.
Potrebbe non essere valido perché l'utente ha ignorato la calibrazione del tracciamento oculare.

- **IsEyeTrackingEnabledAndValid:** indica se i dati di tracciamento oculare corrente sono attualmente usati per lo sguardo fisso.

- **IsEyeTrackingDataValid:** True se sono disponibili dati di tracciamento oculare.
Potrebbe non essere disponibile a causa del timeout superato (dovrebbe essere affidabile per l'utente che lampeggia) o della mancanza di hardware o autorizzazioni di rilevamento.
Vedere [l'esempio di notifica di calibrazione](eye-tracking-is-user-calibrated.md) oculare mancante che spiega come rilevare se un utente è calibrato dagli occhi e visualizzare una notifica appropriata.

- **GazeOrigin:** origine del raggio dello sguardo.
Si noti che verrà restituita l'origine *dello* sguardo head se 'IsEyeGazeValid' è false.

- **GazeDirection:** direzione del raggio dello sguardo.
Verrà restituita la *direzione dello* sguardo head se 'IsEyeGazeValid' è false.

- **HitInfo,** **HitPosition,** **HitNormal** e così via: informazioni sull'oggetto attualmente a guardare la destinazione.
Anche in questo caso, se è false, si baserà sullo sguardo della `IsEyeGazeValid` *testa dell'utente.*

## <a name="examples-for-using-coreservicesinputsystemeyegazeprovider"></a>Esempi per l'uso di CoreServices.InputSystem.EyeGazeProvider

Di seguito è riportato un esempio [di FollowEyeGaze.cs:](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.FollowEyeGaze)

- Ottenere il punto di un ologramma che l'utente sta osservando:

```c#
// Show the object at the hit position of the user's eye gaze ray with the target.
gameObject.transform.position = CoreServices.InputSystem.EyeGazeProvider.HitPosition;
```

- Visualizzazione di un asset visivo a una distanza fissa da dove l'utente sta attualmente cercando:

```c#
// If no target is hit, show the object at a default distance along the gaze ray.
gameObject.transform.position =
CoreServices.InputSystem.EyeGazeProvider.GazeOrigin +
CoreServices.InputSystem.EyeGazeProvider.GazeDirection.normalized * defaultDistanceInMeters;
```

## <a name="see-also"></a>Vedi anche

- [Panoramica del tracciamento oculare MRTK](eye-tracking-main.md)
- [Configurazione di MrTK Eye Tracking](eye-tracking-basic-setup.md)
- [Calibrazione del tracciamento oculare MRTK](eye-tracking-is-user-calibrated.md)
- [HoloLens 2 Documentazione sul tracciamento oculare](https://docs.microsoft.com/windows/mixed-reality/eye-tracking)

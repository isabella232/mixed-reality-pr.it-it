---
title: EyeTracking_EyeGazeProvider
description: Documentazione per il provider di sguardi con occhio in MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, EyeTracking, EyeGaze,
ms.openlocfilehash: c696bb6ad6b7ecd0239ca5c50c27c44735ee685d
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2021
ms.locfileid: "104688471"
---
# <a name="accessing-eye-tracking-data-in-your-unity-script"></a>Accesso ai dati di rilevamento degli occhi nello script Unity

Questo articolo presuppone che si abbia la consapevolezza di configurare la registrazione degli occhi in una scena MRTK. vedere la pagina relativa [all'installazione di base di MRTK per l'uso di Eye Tracking](eye-tracking-basic-setup.md).
L'accesso ai dati di rilevamento degli occhi in uno script monobehavior è facile. Usare semplicemente *CoreServices. InputSystem. EyeGazeProvider*.

## <a name="imixedrealityeyegazeprovider"></a>IMixedRealityEyeGazeProvider

La configurazione di rilevamento degli occhi in MRTK viene configurata tramite l' [`IMixedRealityEyeGazeProvider`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityEyeGazeProvider) interfaccia. L'uso di [CoreServices. InputSystem. EyeGazeProvider](eye-tracking-eye-gaze-provider.md) fornisce l'implementazione predefinita del provider di sguardi registrata nel Toolkit in fase di esecuzione.
Le proprietà utili di `EyeGazeProvider` sono descritte di seguito.

- **IsEyeTrackingEnabled**: true se l'utente ha scelto di usare la verifica degli sguardi.

- **IsEyeCalibrationValid**: indica se la calibrazione del rilevamento occhi dell'utente è valida o meno.
Restituisce ' null ', se il valore non ha ancora ricevuto dati dal sistema di rilevamento degli occhi.
Potrebbe non essere valido perché l'utente ha ignorato la calibrazione del rilevamento degli occhi.

- **IsEyeTrackingEnabledAndValid**: indica se i dati di rilevamento degli occhi correnti sono attualmente utilizzati per lo sguardo.

- **IsEyeTrackingDataValid**: true se i dati di rilevamento degli occhi sono disponibili.
Potrebbe non essere disponibile a causa di un timeout superato (dovrebbe essere affidabile per l'utente lampeggiante) o se l'hardware o le autorizzazioni di rilevamento non sono sufficienti.
Vedere l'esempio di notifica per la [taratura degli occhi mancanti](eye-tracking-is-user-calibrated.md) che spiega come rilevare se un utente è calibrato e visualizzare una notifica appropriata.

- **GazeOrigin**: origine del raggio di sguardi.
Si noti che questa operazione restituirà l'origine dello sguardo a *capo* se ' IsEyeGazeValid ' è false.

- **GazeDirection**: direzione del raggio di sguardi.
Se ' IsEyeGazeValid ' è false, verrà restituita la direzione dello sguardo *Head* .

- **HitInfo**, **HitPosition**, **HitNormal** e così via: informazioni sull'oggetto attualmente guardato.
Anche in questo caso, se `IsEyeGazeValid` è false, questo sarà basato sullo sguardo a *capo* dell'utente.

## <a name="examples-for-using-coreservicesinputsystemeyegazeprovider"></a>Esempi per l'uso di CoreServices. InputSystem. EyeGazeProvider

Di seguito è riportato un esempio di [FollowEyeGaze. cs](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.FollowEyeGaze):

- Ottenere il punto di un ologramma esaminato dall'utente:

```c#
// Show the object at the hit position of the user's eye gaze ray with the target.
gameObject.transform.position = CoreServices.InputSystem.EyeGazeProvider.HitPosition;
```

- Visualizzazione di un asset visivo a una distanza fissa dal punto in cui l'utente sta cercando:

```c#
// If no target is hit, show the object at a default distance along the gaze ray.
gameObject.transform.position =
CoreServices.InputSystem.EyeGazeProvider.GazeOrigin +
CoreServices.InputSystem.EyeGazeProvider.GazeDirection.normalized * defaultDistanceInMeters;
```

## <a name="see-also"></a>Vedi anche

- [Panoramica di MRTK Eye Tracking](eye-tracking-main.md)
- [Configurazione di MRTK Eye Tracking](eye-tracking-basic-setup.md)
- [Calibrazione di MRTK Eye Tracking](eye-tracking-is-user-calibrated.md)
- [Documentazione di HoloLens 2 Eye Tracking](https://docs.microsoft.com/windows/mixed-reality/eye-tracking)

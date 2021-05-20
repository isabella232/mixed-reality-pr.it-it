---
title: Provider di input
description: Documentazione sui diversi tipi di provider di input in MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: ad4a643d0fb46cdb15cee3c37edaffb4f51ed44b
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/19/2021
ms.locfileid: "110145266"
---
# <a name="input-providers"></a>Provider di input

I provider di input vengono registrati nel profilo dei provider di servizi **registrati,** disponibile nel componente Mixed Reality Toolkit:

<img src="../images/input/RegisteredServiceProviders.PNG" width="650px" style="display:block;" alt="Service providers">

Di seguito sono disponibili i provider di input predefiniti, insieme ai controller corrispondenti:

| Input Provider | Controllers |
| --- | --- |
| [`Input Simulation Service`](xref:Microsoft.MixedReality.Toolkit.Input.InputSimulationService) | Mano simulata |
| [`Mouse Device Manager`](xref:Microsoft.MixedReality.Toolkit.Input.UnityInput.MouseDeviceManager) | Mouse  |
| [`OpenVR Device Manager`](xref:Microsoft.MixedReality.Toolkit.OpenVR.Input.OpenVRDeviceManager) | Generic OpenVR, Vive Wand, ViveUckles, Oculus Touch, Oculus Remote, Windows Mixed Reality OpenVR  |
| [`Unity Joystick Manager`](xref:Microsoft.MixedReality.Toolkit.Input.UnityInput.UnityJoystickManager) | Azzarre generico  |
| [`Unity Touch Device Manager`](xref:Microsoft.MixedReality.Toolkit.Input.UnityInput.UnityTouchDeviceManager) | Unity Touch Controller  |
| [`Windows Dictation Input Provider`](xref:Microsoft.MixedReality.Toolkit.Windows.Input.WindowsDictationInputProvider) | *Nessuna*  |
| [`Windows Mixed Reality Device Manager`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityDeviceManager) | Mano articolata WMR, controller WMR, GGV WMR (sguardo fisso, movimento e voce) mano |
| [`Windows Speech Input Provider`](xref:Microsoft.MixedReality.Toolkit.Windows.Input.WindowsSpeechInputProvider) | *Nessuna* |

I provider di dettatura e riconoscimento vocale non creano controller, ma generano direttamente i propri eventi di input specializzati.

È possibile creare provider di input personalizzati implementando [`IMixedRealityInputDeviceManager`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputDeviceManager) l'interfaccia .

Per altre informazioni, vedere Creazione [di un provider di dati di sistema di input.](create-data-provider.md)

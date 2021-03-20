---
title: InputProviders
description: Documentazione su diversi tipi di provider di input in MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
ms.localizationpriority: medium
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: e84c6c4f73110f4827a36c48bb098c44fb20092c
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2021
ms.locfileid: "104682754"
---
# <a name="input-providers"></a>Provider di input

I provider di input sono registrati nel **profilo dei provider di servizi registrati**, disponibile nel componente del Toolkit di realtà mista:

<img src="../Images/Input/RegisteredServiceProviders.PNG" width="650px" style="display:block;" alt="Registerd Service providers">

Questi sono i provider di input disponibili, insieme ai controller corrispondenti:

| Provider di input | Controllers |
| --- | --- |
| [`Input Simulation Service`](xref:Microsoft.MixedReality.Toolkit.Input.InputSimulationService) | Mano simulata |
| [`Mouse Device Manager`](xref:Microsoft.MixedReality.Toolkit.Input.UnityInput.MouseDeviceManager) | Mouse  |
| [`OpenVR Device Manager`](xref:Microsoft.MixedReality.Toolkit.OpenVR.Input.OpenVRDeviceManager) | Generic OpenVR, vive Wand, vive Knuckles, Oculus touch, Oculus remote, Windows Mixed Reality OpenVR  |
| [`Unity Joystick Manager`](xref:Microsoft.MixedReality.Toolkit.Input.UnityInput.UnityJoystickManager) | Joystick generico  |
| [`Unity Touch Device Manager`](xref:Microsoft.MixedReality.Toolkit.Input.UnityInput.UnityTouchDeviceManager) | Controller tocco Unity  |
| [`Windows Dictation Input Provider`](xref:Microsoft.MixedReality.Toolkit.Windows.Input.WindowsDictationInputProvider) | *Nessuno*  |
| [`Windows Mixed Reality Device Manager`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityDeviceManager) | Mano articolata WMR, controller WMR, WMR GGV (sguardi, movimenti e voce) |
| [`Windows Speech Input Provider`](xref:Microsoft.MixedReality.Toolkit.Windows.Input.WindowsSpeechInputProvider) | *Nessuno* |

I provider di dettatura e sintesi vocale non creano controller, generano direttamente eventi di input specifici.

I provider di input personalizzati possono essere creati implementando l' [`IMixedRealityInputDeviceManager`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputDeviceManager) interfaccia.

Per ulteriori informazioni, vedere [creazione di un provider di dati di sistema di input](CreateDataProvider.md).

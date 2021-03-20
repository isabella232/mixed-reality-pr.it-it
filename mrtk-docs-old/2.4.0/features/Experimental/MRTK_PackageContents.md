---
title: MRTK_PakageContents
description: Pakages correlati a MRTK e a XR SDK.
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
ms.localizationpriority: medium
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: 1236618db6b9447677c41bca26cf2c5577d8ace3
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2021
ms.locfileid: "104690928"
---
# <a name="mixed-reality-toolkit-packages"></a>Pacchetti Toolkit per realtà mista

Microsoft Mixed Reality Toolkit viene fornito come raccolta di pacchetti. Il contenuto di questi pacchetti è descritto nelle sezioni seguenti.

- [Foundation](#foundation)
- [Estensioni](#extensions)
- [Strumenti](#tools)
- [esempi](#examples)

## <a name="foundation"></a>Foundation

Il pacchetto Microsoft. MixedRealityToolkit. Unity. Foundation include i componenti di base necessari per creare un'applicazione di realtà mista.

| Cartella | Componente | Descrizione |
| --- | --- | --- |
| MRTK/Core | | Interfacce e definizioni di tipi, classi base e shader standard. |
| MRTK/provider | | |
| | [ObjectMeshObserver](../features/SpatialAwareness/SpatialObjectMeshObserver.md) | Osservatore di consapevolezza spaziale che usa un modello 3D come dati. |
| | OpenVR | Supporto per i dispositivi OpenVR. |
| | [Unity](../features/CameraSystem/UnityArCameraSettings.md) | Sperimentale Provider di impostazioni della fotocamera che consente l'uso di MRTK con i dispositivi mobili AR. |
| | WindowsMixedReality | Supporto per i dispositivi di realtà mista di Windows, tra cui Microsoft HoloLens e gli auricolari immersivi. |
| | WindowsVoiceInput | Supporto per la voce e la dettatura sulle piattaforme Microsoft Windows. |
| | XRSDK | Sperimentale Supporto per [il nuovo Framework XR di Unity](https://blogs.unity3d.com/2020/01/24/unity-xr-platform-updates/) in unity 2019,3. |
| MRTK/SDK | | |
| | Sperimentale | Funzionalità sperimentali, tra cui shader, controlli dell'interfaccia utente e singoli gestori di sistema. |
| | Funzionalità | Funzionalità basata sul pacchetto di base. |
| | Profiles | Profili predefiniti per i sistemi e i servizi Microsoft Mixed Reality Toolkit. |
| | StandardAssets | Asset comuni; modelli, trame, materiali e così via |
| MRTK/servizi | | |
| | [BoundarySystem](../features/Boundary/BoundarySystemGettingStarted.md) | Sistema che implementa il supporto per i confini VR. |
| | [CameraSystem](../features/CameraSystem/CameraSystemOverview.md) | Sistema che implementa la configurazione della fotocamera e la gestione. |
| | [DiagnosticsSystem](../features/Diagnostics/DiagnosticsSystemGettingStarted.md) | Implementazione del sistema in Application Diagnostics, ad esempio un Profiler Visual. |
| | [InputAnimation](../features/InputSimulation/InputAnimationRecording.md) | Supporto per la registrazione dei dati di rilevamento della mano e del movimento Head. |
| | [InputSimulation](../features/InputSimulation/InputSimulationService.md) | Supporto per la simulazione in-editor di input mano e occhio. |
| | [InputSystem](../features/Input/Overview.md) | Sistema che fornisce supporto per l'accesso e la gestione dell'input dell'utente. |
| | [SceneSystem](../features/SceneSystem/SceneSystemGettingStarted.md) | Sistema che fornisce supporto per le applicazioni multiscena. |
| | [SpatialAwarenessSystem](../features/SpatialAwareness/SpatialAwarenessGettingStarted.md) | Sistema che fornisce supporto per la consapevolezza dell'ambiente dell'utente. |
| | [TeleportSystem](../features/TeleportSystem/Overview.md) | Sistema che fornisce il supporto per il Teleporting (spostandosi sull'esperienza nei salti). |

## <a name="extensions"></a>Estensioni

Il pacchetto facoltativo Microsoft. MixedRealityToolkit. Unity. Extensions include servizi aggiuntivi che estendono le funzionalità di Microsoft Mixed Reality Toolkit.

> [!NOTE]
> Il pacchetto Extensions richiede Microsoft. MixedRealityToolkit. Unity. Foundation.

| Cartella | Componente | Descrizione |
| --- | --- | --- |
| MRTK/estensioni | |
| | HandPhysicsService | Servizio che aggiunge il supporto per la fisica a mani articolate. |
| | LostTrackingService | Servizio che semplifica la gestione delle perdite di rilevamento nei dispositivi Microsoft HoloLens. |
| | [SceneTransitionService](../features/Extensions/SceneTransitionService/SceneTransitionServiceOverview.md) | Servizio che semplifica l'aggiunta di transizioni di scene uniformi. |

## <a name="tools"></a>Strumenti

Il pacchetto facoltativo Microsoft. MixedRealityToolkit. Unity. Tools include strumenti utili che migliorano l'esperienza di sviluppo di realtà mista usando Microsoft Mixed Reality Toolkit.
Questi strumenti si trovano nel menu **utilità di reality Toolkit > Utilities** nell'editor di Unity.

> [!NOTE]
> Il pacchetto di strumenti richiede Microsoft. MixedRealityToolkit. Unity. Foundation.

| Cartella | Componente | Descrizione |
| --- | --- | --- |
| MRTK/strumenti | |
| | [DependencyWindow](../features/Tools/DependencyWindow.md) | Strumento che consente di creare un grafico delle dipendenze di asset in un progetto. |
| | [ExtensionServiceCreator](../features/Tools/ExtensionServiceCreationWizard.md) | Procedura guidata per semplificare la creazione di servizi di estensione. |
| | [OptimizeWindow](../features/Tools/OptimizeWindow.md) | Utilità che consente di automatizzare la configurazione di un progetto di realtà mista per ottenere prestazioni ottimali in Unity. |
| | ReserializeAssetsUtility | Fornisce supporto per la riserializzazione di file Unity specifici. |
| | [RuntimeTools/strumenti/ControllerMappingTool](../features/Tools/ControllerMappingTool.md) | Utilità che consente agli sviluppatori di determinare rapidamente i mapping di Unity per i controller hardware. |
| | ScreenshotUtility | Abilita l'acquisizione delle immagini dell'applicazione nell'editor di Unity. |
| | TextureCombinerWindow | Utilità per combinare trame grafiche. |

## <a name="examples"></a>Esempio

Il pacchetto facoltativo Microsoft. MixedRealityToolkit. Unity. Examples include progetti dimostrativi che illustrano le funzionalità di Microsoft Mixed Reality Toolkit.

> [!NOTE]
> Il pacchetto degli esempi richiede Microsoft. MixedRealityToolkit. Unity. Foundation.

| Cartella | Componente | Descrizione |
| --- | --- | --- |
| MRTK/esempi | | |
| | Demo | Scene semplici che illustrano una o due funzionalità correlate. |
| | Sperimentale | Scene demo che illustrano le funzionalità sperimentali. |
| | Controlli | Controlli dell'editor Unity usati dalle scene demo. |
| | StandardAssets | Risorse comuni condivise da più scene demo. |

## <a name="see-also"></a>Vedi anche

- [Benvenuti in MRTK](../WelcomeToMRTK.md)
- [Creazione di pacchetti NuGet](MRTKNuGetPackage.md)

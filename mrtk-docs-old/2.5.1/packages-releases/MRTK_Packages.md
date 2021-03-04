---
title: MRTK_Pakages
description: Pakages in MRTK che supportano l'hardware e le piattaforme a realtà mista.
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, Unity pakage Manager,
ms.openlocfilehash: 98a37610187e1e352696f92a80400dd516c474f8
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/03/2021
ms.locfileid: "101783301"
---
# <a name="mixed-reality-toolkit-packages"></a>Pacchetti Toolkit per realtà mista

Il Toolkit di realtà mista (MRTK) è una raccolta di pacchetti che consentono lo sviluppo di applicazioni di realtà mista multipiattaforma offrendo supporto per l'hardware e le piattaforme di realtà mista.

MRTK è disponibile come pacchetti [Asset](#asset-packages) (. file unitypackage Tools) e tramite [Gestione pacchetti Unity](#unity-package-manager).

## <a name="asset-packages"></a>Pacchetti di asset

È possibile scaricare l'asset MRTK (con estensione file unitypackage Tools) da [GitHub](https://github.com/microsoft/MixedRealityToolkit-Unity/releases).

Di seguito sono riportati alcuni dei vantaggi derivanti dall'utilizzo dei pacchetti di asset:

- Disponibile per Unity 2018,4 e versioni successive
- Modifiche facili da apportare a MRTK
  - MRTK si trova nella cartella assets

Alcuni di questi problemi sono:

- MRTK fa parte della cartella assets del progetto, che conduce a
  - Progetti di dimensioni maggiori
  - Tempi di compilazione più lenti
- Nessuna gestione delle dipendenze
  - I clienti devono risolvere manualmente le dipendenze dei pacchetti
- Processo di aggiornamento manuale
  - Più passaggi
  - Aggiornamenti del controllo del codice sorgente (3000 + file) di grandi dimensioni
  - Rischio di perdere le modifiche apportate a MRTK
- Importazione del pacchetto di esempi in genere significa includere tutti gli esempi

I pacchetti disponibili sono:

- [Foundation](#foundation-package)
- [Estensioni](#extensions-package)
- [Strumenti](#tools-package)
- [Utilità di test](#test-utilities-package)
- [esempi](#examples-package)

Questi pacchetti vengono rilasciati e supportati da Microsoft dal codice sorgente nel ramo [mrtk_release](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/mrtk_release) su GitHub.

### <a name="foundation-package"></a>Pacchetto di base

Mixed Reality Toolkit Foundation è il set di codice che consente all'applicazione di sfruttare le funzionalità comuni nelle piattaforme di realtà mista.

<img src="../features/images/input/MRTK_Package_Foundation.png" width="350px" alt="Foundation Pakages" style="display:block;">  
<sup>Pacchetto di MRTK Foundation</sup>

Il pacchetto MRTK Foundation contiene quanto segue.

| Cartella | Componente | Descrizione |
| --- | --- | --- |
| MRTK/Core | | Interfacce e definizioni di tipi, classi base e shader standard. |
| MRTK/Core/provider | | Provider di dati indipendenti dalla piattaforma |
| | Mani | Supporto della classe di base e servizi per il rilevamento manuale. |
| | [InputAnimation](../features/input-simulation/InputAnimationRecording.md) | Supporto per la registrazione dei dati di rilevamento della mano e del movimento Head. |
| | [InputSimulation](../features/input-simulation/InputSimulationService.md) | Supporto per la simulazione in-editor di input mano e occhio. |
| | [ObjectMeshObserver](../features/spatial-awareness/SpatialObjectMeshObserver.md) | Osservatore di consapevolezza spaziale che usa un modello 3D come dati. |
| | UnityInput | Dispositivi di input comuni (joystick, mouse e così via) implementati tramite l'API di input di Unity. |
| MRTK/provider | | Provider di dati specifici della piattaforma |
| | LeapMotion | Supporto per UltraLeap Leap Motion controller. |
| | OpenVR | Supporto per i dispositivi OpenVR. |
| | Oculus | Supporto per dispositivi Oculus, ad esempio la ricerca. |
| | [Unity](../features/camera-system/UnityArCameraSettings.md) | Sperimentale Provider di impostazioni della fotocamera che consente l'uso di MRTK con i dispositivi mobili AR. |
| | WindowsMixedReality | Supporto per i dispositivi di realtà mista di Windows, tra cui Microsoft HoloLens e gli auricolari immersivi. |
| | Windows | Supporto per le API specifiche di Microsoft Windows, ad esempio la voce e la dettatura. |
| | SDK XR | Sperimentale Supporto per [il nuovo Framework XR di Unity](https://blogs.unity3d.com/2020/01/24/unity-xr-platform-updates/) in unity 2019,3 e versioni successive. |
| MRTK/SDK | | |
| | Sperimentale | Funzionalità sperimentali, tra cui shader, controlli dell'interfaccia utente e singoli gestori di sistema. |
| | Funzionalità | Funzionalità basata sul pacchetto di base. |
| | Profiles | Profili predefiniti per i sistemi e i servizi Microsoft Mixed Reality Toolkit. |
| | StandardAssets | Asset comuni; modelli, trame, materiali e così via |
| MRTK/SceneSystemResources | | Asset e risorse usati dal sistema di scena |
| MRTK/servizi | | |
| | [BoundarySystem](../features/boundary/BoundarySystemGettingStarted.md) | Sistema che implementa il supporto per i confini VR. |
| | [CameraSystem](../features/camera-system/CameraSystemOverview.md) | Sistema che implementa la configurazione della fotocamera e la gestione. |
| | [DiagnosticsSystem](../features/diagnostics/DiagnosticsSystemGettingStarted.md) | Implementazione del sistema in Application Diagnostics, ad esempio un Profiler Visual. |
| | [InputSystem](../features/input/Overview.md) | Sistema che fornisce supporto per l'accesso e la gestione dell'input dell'utente. |
| | [SceneSystem](../features/scene-system/SceneSystemGettingStarted.md) | Sistema che fornisce supporto per le applicazioni multiscena. |
| | [SpatialAwarenessSystem](../features/spatial-awareness/SpatialAwarenessGettingStarted.md) | Sistema che fornisce supporto per la consapevolezza dell'ambiente dell'utente. |
| | [TeleportSystem](../features/teleport-system/Overview.md) | Sistema che fornisce il supporto per il Teleporting (spostandosi sull'esperienza nei salti). |
| MRTK/StandardAssets | | Shader standard MRTK, materiali di base e altre risorse standard per esperienze di realtà miste |

### <a name="extensions-package"></a>Pacchetto di estensioni

Il pacchetto facoltativo Microsoft. MixedRealityToolkit. Unity. Extensions include servizi aggiuntivi che estendono le funzionalità di Microsoft Mixed Reality Toolkit.

> [!NOTE]
> Il pacchetto Extensions richiede Microsoft. MixedRealityToolkit. Unity. Foundation.

| Cartella | Componente | Descrizione |
| --- | --- | --- |
| MRTK/estensioni | |
| | [HandPhysicsService](../features/extensions/hand-physics-service/HandPhysicsServiceOverview.md) | Servizio che aggiunge il supporto per la fisica a mani articolate. |
| | LostTrackingService | Servizio che semplifica la gestione delle perdite di rilevamento nei dispositivi Microsoft HoloLens. |
| | [SceneTransitionService](../features/extensions/scene-transition-service/SceneTransitionServiceOverview.md) | Servizio che semplifica l'aggiunta di transizioni di scene uniformi. |

### <a name="tools-package"></a>Pacchetto strumenti

Il pacchetto facoltativo Microsoft. MixedRealityToolkit. Unity. Tools include strumenti utili che migliorano l'esperienza di sviluppo di realtà mista usando Microsoft Mixed Reality Toolkit.
Questi strumenti si trovano nel menu **utilità di reality Toolkit > Utilities** nell'editor di Unity.

> [!NOTE]
> Il pacchetto di strumenti richiede Microsoft. MixedRealityToolkit. Unity. Foundation.

| Cartella | Componente | Descrizione |
| --- | --- | --- |
| MRTK/strumenti | |
| | BuildWindow | Strumento che consente di semplificare il processo di compilazione e distribuzione di applicazioni UWP. |
| | [DependencyWindow](../features/tools/DependencyWindow.md) | Strumento che consente di creare un grafico delle dipendenze di asset in un progetto. |
| | [ExtensionServiceCreator](../features/tools/ExtensionServiceCreationWizard.md) | Procedura guidata per semplificare la creazione di servizi di estensione. |
| | [MigrationWindow](../features/tools/MigrationWindow.md) | Strumento che facilita l'aggiornamento del codice che usa componenti MRTK deprecati.  |
| | [OptimizeWindow](../features/tools/OptimizeWindow.md) | Utilità che consente di automatizzare la configurazione di un progetto di realtà mista per ottenere prestazioni ottimali in Unity. |
| | ReserializeAssetsUtility | Fornisce supporto per la riserializzazione di file Unity specifici. |
| | [RuntimeTools/strumenti/ControllerMappingTool](../features/tools/ControllerMappingTool.md) | Utilità che consente agli sviluppatori di determinare rapidamente i mapping di Unity per i controller hardware. |
| | ScreenshotUtility | Abilita l'acquisizione delle immagini dell'applicazione nell'editor di Unity. |
| | TextureCombinerWindow | Utilità per combinare trame grafiche. |
| | [Casella degli strumenti](../features/ux-building-blocks/Toolbox.md) | Interfaccia utente che semplifica l'individuazione e l'utilizzo dei componenti UX MRTK. |

### <a name="test-utilities-package"></a>Pacchetto di utilità di test

Il pacchetto Microsoft. MixedRealityToolkit. TestUtilities facoltativo è una raccolta di script helper che consentono agli sviluppatori di [creare facilmente test in modalità di riproduzione](../contributing/UnitTests.md#play-mode-tests). Queste utilità sono particolarmente utili per gli sviluppatori che creano componenti MRTK.

| Cartella | Componente | Descrizione |
| --- | --- | --- |
| MRTK/test | |
| | TestUtilities | Metodi per semplificare la creazione di test in modalità di riproduzione, incluse le utilità di simulazione manuale. |

### <a name="examples-package"></a>Pacchetto di esempi

Il pacchetto degli esempi contiene demo, script di esempio e scene di esempio che esercitano le funzionalità del pacchetto di base. Questo pacchetto contiene la [scena HandInteractionExample](../features/example-scenes/HandInteractionExamples.md) (illustrata di seguito) che contiene oggetti di esempio che rispondono a diversi tipi di input della mano (articolati e non articolati).

![Scena HandInteractionExample](../features/images/MRTK_Examples.png)

Questo pacchetto contiene anche le demo di rilevamento degli occhi, [documentate qui](../features/eye-tracking/EyeTracking_ExamplesOverview.md)

Più in generale, tutte le nuove funzionalità di MRTK devono contenere un esempio corrispondente nel pacchetto degli esempi, approssimativamente seguendo la stessa struttura di cartelle e la stessa posizione.

> [!NOTE]
> Il pacchetto degli esempi richiede Microsoft. MixedRealityToolkit. Unity. Foundation.

| Cartella | Componente | Descrizione |
| --- | --- | --- |
| MRTK/esempi | | |
| | Demo | Scene semplici che illustrano una o due funzionalità correlate. |
| | Sperimentale | Scene demo che illustrano le funzionalità sperimentali. |
| | StandardAssets | Risorse comuni condivise da più scene demo. |

## <a name="unity-package-manager"></a>Gestione pacchetti Unity

Per le esperienze create usando Unity 2019,4 e versioni successive, MRTK è disponibile tramite [Gestione pacchetti Unity](https://docs.unity3d.com/Manual/Packages.html).

Di seguito sono riportati alcuni dei vantaggi derivanti dall'utilizzo dei pacchetti di asset:

- Progetti più piccoli
  - Soluzioni di Visual Studio più pulite
  - Un numero inferiore di file da archiviare (MRTK è un riferimento semplice nel `Packages/manifest.json` file)
- Compilazione più veloce
  - Unity non è necessario ricompilare MRTK durante la compilazione
- Risoluzione delle dipendenze
  - I pacchetti MRTK richiesti vengono installati automaticamente quando si specificano i pacchetti con dipendenze
- Facile aggiornamento alle nuove versioni di MRTK
  - Modificare la versione nel `Packages/manifest.json` file

Alcuni di questi problemi sono:

- MRTK non è modificabile
  - Non è possibile apportare modifiche senza che vengano rimosse durante la risoluzione del pacchetto
- MRTK non supporta i pacchetti UPM con Unity 2018,4

### <a name="foundation-package"></a>Pacchetto di base

Il pacchetto di base ( `com.microsoft.mixedreality.toolkit.foundation` ) costituisce la base del Toolkit di realtà mista.

| Cartella | Componente | Descrizione |
| --- | --- | --- |
| MRTK/Core | | Interfacce e definizioni di tipi, classi base e shader standard. |
| MRTK/Core/provider | | Provider di dati indipendenti dalla piattaforma |
| | Mani | Supporto della classe di base e servizi per il rilevamento manuale. |
| | [InputAnimation](../features/input-simulation/InputAnimationRecording.md) | Supporto per la registrazione dei dati di rilevamento della mano e del movimento Head. |
| | [InputSimulation](../features/input-simulation/InputSimulationService.md) | Supporto per la simulazione in-editor di input mano e occhio. |
| | [ObjectMeshObserver](../features/spatial-awareness/SpatialObjectMeshObserver.md) | Osservatore di consapevolezza spaziale che usa un modello 3D come dati. |
| | UnityInput | Dispositivi di input comuni (joystick, mouse e così via) implementati tramite l'API di input di Unity. |
| MRTK/provider | | Provider di dati specifici della piattaforma |
| | LeapMotion | Supporto per UltraLeap Leap Motion controller. |
| | OpenVR | Supporto per i dispositivi OpenVR. |
| | Oculus | Supporto per dispositivi Oculus, ad esempio la ricerca. |
| | [Unity](../features/camera-system/UnityArCameraSettings.md) | Sperimentale Provider di impostazioni della fotocamera che consente l'uso di MRTK con i dispositivi mobili AR. |
| | WindowsMixedReality | Supporto per i dispositivi di realtà mista di Windows, tra cui Microsoft HoloLens e gli auricolari immersivi. |
| | Windows | Supporto per le API specifiche di Microsoft Windows, ad esempio la voce e la dettatura. |
| | SDK XR | Sperimentale Supporto per [il nuovo Framework XR di Unity](https://blogs.unity3d.com/2020/01/24/unity-xr-platform-updates/) in unity 2019,3 e versioni successive. |
| MRTK/SDK | | |
| | Sperimentale | Funzionalità sperimentali, tra cui shader, controlli dell'interfaccia utente e singoli gestori di sistema. |
| | Funzionalità | Funzionalità basata sul pacchetto di base. |
| | Profiles | Profili predefiniti per i sistemi e i servizi Microsoft Mixed Reality Toolkit. |
| | StandardAssets | Asset comuni; modelli, trame, materiali e così via |
| MRTK/servizi | | |
| | [BoundarySystem](../features/boundary/BoundarySystemGettingStarted.md) | Sistema che implementa il supporto per i confini VR. |
| | [CameraSystem](../features/camera-system/CameraSystemOverview.md) | Sistema che implementa la configurazione della fotocamera e la gestione. |
| | [DiagnosticsSystem](../features/diagnostics/DiagnosticsSystemGettingStarted.md) | Implementazione del sistema in Application Diagnostics, ad esempio un Profiler Visual. |
| | [InputSystem](../features/input/Overview.md) | Sistema che fornisce supporto per l'accesso e la gestione dell'input dell'utente. |
| | [SceneSystem](../features/scene-system/SceneSystemGettingStarted.md) | Sistema che fornisce supporto per le applicazioni multiscena. |
| | [SpatialAwarenessSystem](../features/spatial-awareness/SpatialAwarenessGettingStarted.md) | Sistema che fornisce supporto per la consapevolezza dell'ambiente dell'utente. |
| | [TeleportSystem](../features/teleport-system/Overview.md) | Sistema che fornisce il supporto per il Teleporting (spostandosi sull'esperienza nei salti). |

Dipendenze:

- Asset standard ( `com.microsoft.mixedreality.toolkit.standardassets` )

### <a name="standard-assets"></a>Asset standard

Il pacchetto di asset standard ( `com.microsoft.mixedreality.toolkit.standardassets)` è una raccolta di componenti consigliati per tutte le esperienze di realtà miste, tra cui:

- Shader standard MRTK
- Materiali di base con lo shader standard MRTK
- File audio
- Tipi di carattere
- Trame
- Icone

> [!Note]
> Per evitare modifiche di rilievo basate sulle definizioni degli assembly, gli script usati per controllare alcune funzionalità dello shader standard MRTK non sono inclusi nel pacchetto di asset standard. Questi script sono disponibili nel pacchetto di base nella `MRTK/Core/Utilities/StandardShader` cartella.

Dipendenze: nessuna

### <a name="extension-packages"></a>Pacchetti di estensione

Il pacchetto facoltativo Extensions ( `com.microsoft.mixedreality.toolkit.extensions)` contiene componenti aggiuntivi che espandono la funzionalità del MRTK di.

| Cartella | Componente | Descrizione |
| --- | --- | --- |
| MRTK/estensioni | |
| | [HandPhysicsService](../features/extensions/hand-physics-service/HandPhysicsServiceOverview.md) | Servizio che aggiunge il supporto per la fisica a mani articolate. |
| | LostTrackingService | Servizio che semplifica la gestione delle perdite di rilevamento nei dispositivi Microsoft HoloLens. |
| | [SceneTransitionService](../features/extensions/scene-transition-service/SceneTransitionServiceOverview.md) | Servizio che semplifica l'aggiunta di transizioni di scene uniformi. |
| | Esempi ~ | Una cartella nascosta (nell'editor di Unity) che contiene le scene di esempio e gli asset. |

Per altri dettagli sul processo di uso dei pacchetti che contengono progetti di esempio, vedere l'articolo relativo al [Toolkit di realtà mista e a gestione pacchetti Unity](../configuration/usingupm.md#using-mixed-reality-toolkit-examples) .

Dipendenze:

- Fondamenta ( `com.microsoft.mixedreality.toolkit.foundation` )

### <a name="tools-package"></a>Pacchetto strumenti

Il pacchetto di strumenti facoltativo ( `com.microsoft.mixedreality.toolkit.tools)` contiene strumenti utili per la creazione di esperienze di realtà miste. In generale, questi strumenti sono componenti dell'editor e il codice non viene fornito come parte di un'applicazione.

| Cartella | Componente | Descrizione |
| --- | --- | --- |
| MRTK/strumenti | |
| | BuildWindow | Strumento che consente di semplificare il processo di compilazione e distribuzione di applicazioni UWP. |
| | [DependencyWindow](../features/tools/DependencyWindow.md) | Strumento che consente di creare un grafico delle dipendenze di asset in un progetto. |
| | [ExtensionServiceCreator](../features/tools/ExtensionServiceCreationWizard.md) | Procedura guidata per semplificare la creazione di servizi di estensione. |
| | [MigrationWindow](../features/tools/MigrationWindow.md) | Strumento che facilita l'aggiornamento del codice che usa componenti MRTK deprecati.  |
| | [OptimizeWindow](../features/tools/OptimizeWindow.md) | Utilità che consente di automatizzare la configurazione di un progetto di realtà mista per ottenere prestazioni ottimali in Unity. |
| | ReserializeAssetsUtility | Fornisce supporto per la riserializzazione di file Unity specifici. |
| | [RuntimeTools/strumenti/ControllerMappingTool](../features/tools/ControllerMappingTool.md) | Utilità che consente agli sviluppatori di determinare rapidamente i mapping di Unity per i controller hardware. |
| | ScreenshotUtility | Abilita l'acquisizione delle immagini dell'applicazione nell'editor di Unity. |
| | TextureCombinerWindow | Utilità per combinare trame grafiche. |
| | [Casella degli strumenti](../features/ux-building-blocks/Toolbox.md) | Interfaccia utente che semplifica l'individuazione e l'utilizzo dei componenti UX MRTK. |

Dipendenze:

- Fondamenta ( `com.microsoft.mixedreality.toolkit.foundation` )

### <a name="test-utilities-package"></a>Pacchetto di utilità di test

Il pacchetto di utilità di test facoltativo ( `com.microsoft.mixedreality.toolkit.testutilities` ) contiene una raccolta di script helper che consentono agli sviluppatori di creare facilmente test in modalità di riproduzione. Queste utilità sono particolarmente utili per gli sviluppatori che creano componenti MRTK.

| Cartella | Componente | Descrizione |
| --- | --- | --- |
| MRTK/test | |
| | TestUtilities | Metodi per semplificare la creazione di test in modalità di riproduzione, incluse le utilità di simulazione manuale. |

Dipendenze:

- Fondamenta ( `com.microsoft.mixedreality.toolkit.foundation` )

### <a name="examples-package"></a>Pacchetto di esempi

Il pacchetto degli esempi ( `com.microsoft.mixedreality.toolkit.examples` ) è strutturato per consentire agli sviluppatori di importare solo gli esempi di interesse.

Per altri dettagli sul processo di uso dei pacchetti che contengono progetti di esempio, vedere l'articolo relativo al [Toolkit di realtà mista e a gestione pacchetti Unity](../configuration/usingupm.md#using-mixed-reality-toolkit-examples) .

| Cartella | Componente | Descrizione |
| --- | --- | --- |
| MRTK/esempi | | |
| | Esempi ~ | Una cartella nascosta (nell'editor di Unity) che contiene le scene di esempio e gli asset. |
| | StandardAssets | Risorse comuni condivise da più scene demo. |

Dipendenze:

- Fondamenta ( `com.microsoft.mixedreality.toolkit.foundation` )
- Estensioni (`com.microsoft.mixedreality.toolkit.extensions`)

## <a name="see-also"></a>Vedi anche

- [Panoramica dell'architettura](../architecture/Overview.md)
- [Sistemi, servizi di estensione e provider di dati](../architecture/SystemsExtensionsProviders.md)
- [Toolkit per realtà mista e gestione pacchetti Unity](../configuration/usingupm.md)

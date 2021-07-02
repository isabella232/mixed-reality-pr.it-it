---
title: Pacchetti MRTK
description: Pacchetti in MRTK che supportano l'hardware e le piattaforme di realtà mista.
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realtà mista, sviluppo, MRTK, Unity Gestione pacchetti,
ms.openlocfilehash: 3c2a11dd4036a78ccb96aa2c640ef8324181c1e0
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176504"
---
# <a name="mrtk-packages"></a>Pacchetti MRTK

Mixed Reality Toolkit (MRTK) è una raccolta di pacchetti che consentono lo sviluppo di applicazioni di realtà mista multipiattaforma fornendo il supporto per l'hardware e le piattaforme di realtà mista.

MRTK è disponibile come [pacchetti asset](#asset-packages) (.unitypackage) e tramite [unity Gestione pacchetti](#unity-package-manager).

## <a name="asset-packages"></a>Pacchetti di asset

L'asset MRTK (.unitypackage) può essere scaricato da [GitHub](https://github.com/microsoft/MixedRealityToolkit-Unity/releases).

Alcuni dei vantaggi dell'uso dei pacchetti di asset includono:

- Disponibile per Unity 2018.4 e versione più recente
- Facilità di apportare modifiche a MRTK
  - MRTK si trova nella cartella Assets

Alcuni di questi problemi sono:

- MRTK fa parte della cartella Assets del progetto,
  - Progetti più grandi
  - Tempi di compilazione più lenti
- Nessuna gestione delle dipendenze
  - I clienti devono risolvere manualmente le dipendenze dei pacchetti
- Processo di aggiornamento manuale
  - Più passaggi
  - Aggiornamenti del controllo del codice sorgente di grandi dimensioni (oltre 3000 file)
  - Rischio di perdita delle modifiche apportate a MRTK
- L'importazione del pacchetto examples in genere significa includere tutti gli esempi

I pacchetti disponibili sono:

- [fondazione](#foundation-package)
- [Estensioni](#extensions-package)
- [Strumenti](#tools-package)
- [Utilità di test](#test-utilities-package)
- [esempi](#examples-package)

Questi pacchetti vengono rilasciati e supportati da Microsoft dal codice sorgente nel ramo [mrtk_release](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/mrtk_release) in GitHub.

### <a name="foundation-package"></a>Pacchetto Di base

Mixed Reality Toolkit Foundation è il set di codice che consente all'applicazione di sfruttare le funzionalità comuni tra piattaforme di realtà mista.

<img src="../features/images/input/MRTK_Package_Foundation.png" width="350px" alt="Pakage foundation" style="display:block;">  
<sup>Pacchetto DI BASE MRTK</sup>

Il pacchetto MRTK Foundation contiene quanto segue.

| Cartella | Componente | Descrizione |
| --- | --- | --- |
| MRTK/Core | | Definizioni di interfacce e tipi, classi di base, shader standard. |
| MRTK/Core/Providers | | Provider di dati indipendenti dalla piattaforma |
| | Mani | Supporto e servizi della classe base per il rilevamento manuale. |
| | [InputAnimation](../features/input-simulation/input-animation-recording.md) | Supporto per la registrazione dei dati di spostamento della testa e rilevamento della mano. |
| | [InputSimulation](../features/input-simulation/input-simulation-service.md) | Supporto per la simulazione nell'editor dell'input di mani e occhi. |
| | [ObjectMeshObserver](../features/spatial-awareness/spatial-object-mesh-observer.md) | Osservatore di consapevolezza spaziale che usa un modello 3D come dati. |
| | UnityInput | Dispositivi di input comuni (joystick, mouse e così via) implementati tramite l'API di input di Unity. |
| MRTK/Providers | | Provider di dati specifici della piattaforma |
| | LeapMotion | Supporto per il controller Leap Motion UltraLeap. |
| | OpenVR | Supporto per i dispositivi OpenVR. |
| | Oculus | Supporto per i dispositivi Oculus, ad esempio quest. |
| | [UnityAR](../features/camera-system/unity-ar-camera-settings.md) | (Sperimentale) Provider di impostazioni della fotocamera che abilita l'uso di MRTK con dispositivi AR per dispositivi mobili. |
| | WindowsMixedReality | Supporto per Windows Mixed Reality dispositivi, tra cui Microsoft HoloLens visori immersivi. |
| | Windows | Supporto per Microsoft Windows API specifiche, ad esempio voce e dettatura. |
| | XR SDK | (Sperimentale) Supporto per [il nuovo framework XR](https://blogs.unity3d.com/2020/01/24/unity-xr-platform-updates/) di Unity in Unity 2019.3 e versioni più nuove. |
| MRTK/SDK | | |
| | Sperimentale | Funzionalità sperimentali, tra cui shader, controlli dell'interfaccia utente e singoli responsabili di sistema. |
| | Funzionalità | Funzionalità che si basa sul pacchetto Foundation. |
| | Profiles | Profili predefiniti per microsoft Mixed Reality Toolkit sistemi e servizi. |
| | StandardAssets | Asset comuni; modelli, trame, materiali e così via. |
| MRTK/SceneSystemResources | | Asset e risorse usati dal sistema di scena |
| MRTK/Services | | |
| | [BoundarySystem](../features/boundary/boundary-system-getting-started.md) | Sistema che implementa il supporto dei limiti VR. |
| | [CameraSystem](../features/camera-system/camera-system-overview.md) | Sistema che implementa la configurazione e la gestione della fotocamera. |
| | [DiagnosticsSystem](../features/diagnostics/diagnostics-system-getting-started.md) | Implementazione del sistema nella diagnostica delle applicazioni, ad esempio un profiler visivo. |
| | [InputSystem](../features/input/overview.md) | Sistema che fornisce supporto per l'accesso e la gestione dell'input dell'utente. |
| | [SceneSystem](../features/scene-system/scene-system-getting-started.md) | Sistema che fornisce supporto per applicazioni multi-scena. |
| | [SpatialAwarenessSystem](../features/spatial-awareness/spatial-awareness-getting-started.md) | Sistema che fornisce supporto per la consapevolezza dell'ambiente dell'utente. |
| | [TeleportSystem](../features/teleport-system/teleport-system.md) | Sistema che fornisce supporto per il teletrasporto (spostamento dell'esperienza in salti). |
| MRTK/StandardAssets | | Shader MRTK Standard, materiali di base e altri asset standard per esperienze di realtà mista |

### <a name="extensions-package"></a>Pacchetto di estensioni

Il pacchetto facoltativo Microsoft.MixedRealityToolkit.Unity.Extensions include servizi aggiuntivi che estendono le funzionalità di Microsoft Mixed Reality Toolkit.

> [!NOTE]
> Il pacchetto di estensioni richiede Microsoft.MixedRealityToolkit.Unity.Foundation.

| Cartella | Componente | Descrizione |
| --- | --- | --- |
| MRTK/Extensions | |
| | [HandPhysicsService](../features/extensions/hand-physics-service.md) | Servizio che aggiunge il supporto fisico alle mani articolate. |
| | LostTrackingService | Servizio che semplifica la gestione della perdita di rilevamento Microsoft HoloLens dispositivi. |
| | [SceneTransitionService](../features/extensions/scene-transition-service.md) | Servizio che semplifica l'aggiunta di transizioni di scena uniformi. |

### <a name="tools-package"></a>Pacchetto tools

Il pacchetto facoltativo Microsoft.MixedRealityToolkit.Unity.Tools include strumenti utili che migliorano l'esperienza di sviluppo di realtà mista usando Microsoft Mixed Reality Toolkit.
Questi strumenti si trovano nel menu **Utilità Toolkit > realtà mista** nell'editor di Unity.

> [!NOTE]
> Il pacchetto di strumenti richiede Microsoft.MixedRealityToolkit.Unity.Foundation.

| Cartella | Componente | Descrizione |
| --- | --- | --- |
| MRTK/Tools | |
| | BuildWindow | Strumento che consente di semplificare il processo di compilazione e distribuzione di applicazioni UWP. |
| | [DependencyWindow](../features/tools/dependency-window.md) | Strumento che crea un grafo delle dipendenze di asset in un progetto. |
| | [ExtensionServiceCreator](../features/tools/extension-service-creation-wizard.md) | Procedura guidata per facilitare la creazione di servizi di estensione. |
| | [MigrationWindow](../features/tools/migration-window.md) | Strumento che consente di aggiornare il codice che usa componenti MRTK deprecati.  |
| | [OptimizeWindow](../features/tools/optimize-window.md) | Utilità che consente di automatizzare la configurazione di un progetto di realtà mista per ottenere prestazioni ottimali in Unity. |
| | ReserializeAssetsUtility | Fornisce il supporto per la deserializzazione di file Unity specifici. |
| | [RuntimeTools/Tools/ControllerMappingTool](../features/tools/controller-mapping-tool.md) | Utilità che consente agli sviluppatori di determinare rapidamente i mapping di Unity per i controller hardware. |
| | ScreenshotUtility | Abilita l'acquisizione di immagini dell'applicazione nell'editor di Unity. |
| | TextureCombinerWindow | Utilità per combinare trame grafiche. |
| | [Casella degli strumenti](../features/ux-building-blocks/toolbox.md) | Interfaccia utente che semplifica l'individuazione e l'uso dei componenti dell'esperienza utente MRTK. |

### <a name="test-utilities-package"></a>Pacchetto di utilità di test

Il pacchetto facoltativo Microsoft.MixedRealityToolkit.TestUtilities è una raccolta di script helper che consentono agli sviluppatori di creare facilmente [test in modalità di riproduzione.](../contributing/unit-tests.md#play-mode-tests) Queste utilità sono particolarmente utili per gli sviluppatori che creano componenti MRTK.

| Cartella | Componente | Descrizione |
| --- | --- | --- |
| MRTK/Tests | |
| | TestUtilities | Metodi per semplificare la creazione di test in modalità di riproduzione, incluse le utilità di simulazione manuale. |

### <a name="examples-package"></a>Pacchetto di esempi

Il pacchetto degli esempi contiene demo, script di esempio e scene di esempio che esercitino la funzionalità nel pacchetto di base. Questo pacchetto contiene la scena [HandInteractionExample](../features/example-scenes/hand-interaction-examples.md) (nella figura seguente) che contiene oggetti di esempio che rispondono a vari tipi di input manuale (articolati e non articolati).

![Scena HandInteractionExample](../features/images/MRTK_Examples.png)

Questo pacchetto contiene anche demo di tracciamento oculare, [documentate qui](../features/example-scenes/eye-tracking-examples-overview.md)

Più in generale, qualsiasi nuova funzionalità in MRTK deve contenere un esempio corrispondente nel pacchetto degli esempi, seguendo approssimativamente la stessa struttura di cartelle e la stessa posizione.

> [!NOTE]
> Il pacchetto di esempi richiede Microsoft.MixedRealityToolkit.Unity.Foundation.

| Cartella | Componente | Descrizione |
| --- | --- | --- |
| MRTK/Esempi | | |
| | Demo | Scene semplici che illustrano una o due funzionalità correlate. |
| | Sperimentale | Scene demo che illustrano le funzionalità sperimentali. |
| | StandardAssets | Asset comuni condivisi da più scene demo. |

## <a name="unity-package-manager"></a>Unity Gestione pacchetti

Per le esperienze create con Unity 2019.4 e versione più recente, il codice MRTK è disponibile tramite [unity Gestione pacchetti](https://docs.unity3d.com/Manual/Packages.html).

Alcuni dei vantaggi dell'uso dei pacchetti di asset includono:

- Progetti più piccoli
  - Soluzioni Visual Studio più pulite
  - Meno file da archiviare (MRTK è un riferimento semplice nel `Packages/manifest.json` file)
- Compilazione più veloce
  - Unity non deve ricompilare MRTK durante la compilazione
- Risoluzione delle dipendenze
  - I pacchetti MRTK necessari vengono installati automaticamente quando si specificano pacchetti con dipendenze
- Aggiornamento semplice alle nuove versioni di MRTK
  - Modificare la versione nel `Packages/manifest.json` file

Alcuni di questi problemi sono:

- MRTK non è modificabile
  - Non è possibile apportare modifiche senza che vengano rimosse durante la risoluzione del pacchetto
- MRTK non supporta i pacchetti UPM con Unity 2018.4

### <a name="foundation-package"></a>Pacchetto Di base

Il pacchetto di base ( `com.microsoft.mixedreality.toolkit.foundation` ) costituisce la base dell'Toolkit.

| Cartella | Componente | Descrizione |
| --- | --- | --- |
| MRTK/Core | | Definizioni di interfacce e tipi, classi di base, shader standard. |
| MRTK/Core/Providers | | Provider di dati indipendenti dalla piattaforma |
| | Mani | Supporto e servizi della classe base per il rilevamento manuale. |
| | [InputAnimation](../features/input-simulation/input-animation-recording.md) | Supporto per la registrazione dei dati di spostamento della testa e rilevamento della mano. |
| | [InputSimulation](../features/input-simulation/input-simulation-service.md) | Supporto per la simulazione nell'editor dell'input di mani e occhi. |
| | [ObjectMeshObserver](../features/spatial-awareness/spatial-object-mesh-observer.md) | Osservatore di consapevolezza spaziale che usa un modello 3D come dati. |
| | UnityInput | Dispositivi di input comuni (joystick, mouse e così via) implementati tramite l'API di input di Unity. |
| MRTK/Providers | | Provider di dati specifici della piattaforma |
| | LeapMotion | Supporto per il controller UltraLeap Leap Motion. |
| | OpenVR | Supporto per dispositivi OpenVR. |
| | Oculus | Supporto per i dispositivi Oculus, ad esempio quest. |
| | [UnityAR](../features/camera-system/unity-ar-camera-settings.md) | (Sperimentale) Provider di impostazioni della fotocamera che abilita l'uso di MRTK con dispositivi AR mobili. |
| | WindowsMixedReality | Supporto per dispositivi Windows Mixed Reality, inclusi visori VR Microsoft HoloLens immersive. |
| | Windows | Supporto per Microsoft Windows API specifiche, ad esempio voce e dettatura. |
| | XR SDK | (Sperimentale) Supporto per [il nuovo framework XR](https://blogs.unity3d.com/2020/01/24/unity-xr-platform-updates/) di Unity in Unity 2019.3 e versioni più nuove. |
| MRTK/SDK | | |
| | Sperimentale | Funzionalità sperimentali, inclusi shader, controlli dell'interfaccia utente e singoli gestori di sistema. |
| | Funzionalità | Funzionalità che si basa sul pacchetto Foundation. |
| | Profiles | Profili predefiniti per microsoft mixed reality Toolkit sistemi e servizi. |
| | StandardAssets | Asset comuni; modelli, trame, materiali e così via. |
| MRTK/Services | | |
| | [BoundarySystem](../features/boundary/boundary-system-getting-started.md) | Sistema che implementa il supporto dei limiti di realtà virtuale. |
| | [CameraSystem](../features/camera-system/camera-system-overview.md) | Sistema che implementa la configurazione e la gestione della fotocamera. |
| | [DiagnosticsSystem](../features/diagnostics/diagnostics-system-getting-started.md) | Implementazione del sistema nella diagnostica delle applicazioni, ad esempio un profiler visivo. |
| | [InputSystem](../features/input/overview.md) | Sistema che fornisce supporto per l'accesso e la gestione dell'input dell'utente. |
| | [SceneSystem](../features/scene-system/scene-system-getting-started.md) | Sistema che fornisce supporto per applicazioni multi-scena. |
| | [SpatialAwarenessSystem](../features/spatial-awareness/spatial-awareness-getting-started.md) | Sistema che fornisce supporto per la consapevolezza dell'ambiente dell'utente. |
| | [TeleportSystem](../features/teleport-system/teleport-system.md) | Sistema che fornisce supporto per il teletrasporto (spostamento dell'esperienza in salti). |

Dipendenze:

- Asset standard ( `com.microsoft.mixedreality.toolkit.standardassets` )

### <a name="standard-assets"></a>Asset standard

Il pacchetto di asset standard ( è una raccolta di componenti consigliati per tutte le `com.microsoft.mixedreality.toolkit.standardassets)` esperienze di realtà mista, tra cui:

- Shader MRTK Standard
- Materiali di base che usano lo shader MRTK Standard
- File audio
- Tipi di carattere
- Trame
- Icone

> [!Note]
> Per evitare modifiche di rilievo basate sulle definizioni di assembly, gli script usati per controllare alcune funzionalità dello shader MRTK Standard non sono inclusi nel pacchetto di asset standard. Questi script sono disponibili nel pacchetto di base nella `MRTK/Core/Utilities/StandardShader` cartella .

Dipendenze: nessuna

### <a name="extension-packages"></a>Pacchetti di estensione

Il pacchetto di estensioni facoltativo ( `com.microsoft.mixedreality.toolkit.extensions)` contiene componenti aggiuntivi che espandono le funzionalità di MRTK.

| Cartella | Componente | Descrizione |
| --- | --- | --- |
| MRTK/Estensioni | |
| | [HandPhysicsService](../features/extensions/hand-physics-service.md) | Servizio che aggiunge il supporto fisico alle mani articolate. |
| | LostTrackingService | Servizio che semplifica la gestione della perdita di tracciabilità Microsoft HoloLens dispositivi. |
| | [SceneTransitionService](../features/extensions/scene-transition-service.md) | Servizio che semplifica l'aggiunta di transizioni di scena uniformi. |
| | Esempi~ | Una cartella nascosta (nell'editor di Unity) che contiene le scene e gli asset di esempio. |

Altre informazioni sul processo di uso dei pacchetti contenenti progetti di esempio sono disponibili nell'articolo Mixed Reality Toolkit and Unity Gestione pacchetti (Realtà mista e [unity Gestione pacchetti).](../configuration/usingupm.md#using-mixed-reality-toolkit-examples)

Dipendenze:

- Foundation ( `com.microsoft.mixedreality.toolkit.foundation` )

### <a name="tools-package"></a>Pacchetto tools

Il pacchetto di strumenti facoltativo ( `com.microsoft.mixedreality.toolkit.tools)` contiene strumenti utili per la creazione di esperienze di realtà mista. In generale, questi strumenti sono componenti dell'editor e il relativo codice non viene specificato come parte di un'applicazione.

| Cartella | Componente | Descrizione |
| --- | --- | --- |
| MRTK/Strumenti | |
| | Finestra di compilazione | Strumento che semplifica il processo di compilazione e distribuzione di applicazioni UWP. |
| | [Finestra di dipendenza](../features/tools/dependency-window.md) | Strumento che crea un grafico delle dipendenze degli asset in un progetto. |
| | [ExtensionServiceCreator](../features/tools/extension-service-creation-wizard.md) | Procedura guidata per facilitare la creazione di servizi di estensione. |
| | [Finestra di migrazione](../features/tools/migration-window.md) | Strumento che consente di aggiornare il codice che usa componenti MRTK deprecati.  |
| | [OptimizeWindow](../features/tools/optimize-window.md) | Utilità che consente di automatizzare la configurazione di un progetto di realtà mista per ottenere prestazioni ottimali in Unity. |
| | ReserializeAssetsUtility | Fornisce supporto per la deserializzazione di file Unity specifici. |
| | [RuntimeTools/Tools/ControllerMappingTool](../features/tools/controller-mapping-tool.md) | Utilità che consente agli sviluppatori di determinare rapidamente i mapping di Unity per i controller hardware. |
| | ScreenshotUtilità | Abilita l'acquisizione di immagini dell'applicazione nell'editor di Unity. |
| | TextureCombinerWindow | Utilità per combinare trame grafiche. |
| | [Casella degli strumenti](../features/ux-building-blocks/toolbox.md) | Interfaccia utente che semplifica l'individuazione e l'uso dei componenti UX di MRTK. |

Dipendenze:

- Foundation ( `com.microsoft.mixedreality.toolkit.foundation` )

### <a name="test-utilities-package"></a>Pacchetto di utilità di test

Il pacchetto di utilità di test facoltativo ( ) contiene una raccolta di script helper che consentono agli `com.microsoft.mixedreality.toolkit.testutilities` sviluppatori di creare facilmente test in modalità di riproduzione. Queste utilità sono particolarmente utili per gli sviluppatori che creano componenti MRTK.

| Cartella | Componente | Descrizione |
| --- | --- | --- |
| MRTK/Tests | |
| | TestUtilities | Metodi per semplificare la creazione di test in modalità di riproduzione, incluse le utilità di simulazione manuale. |

Dipendenze:

- Base ( `com.microsoft.mixedreality.toolkit.foundation` )

### <a name="examples-package"></a>Pacchetto di esempi

Il pacchetto degli esempi ( `com.microsoft.mixedreality.toolkit.examples` ), è strutturato per consentire agli sviluppatori di importare solo gli esempi di interesse.

Per altre informazioni sul processo di utilizzo dei pacchetti contenenti progetti di esempio, vedere l'articolo [Toolkit e Unity Gestione pacchetti.](../configuration/usingupm.md#using-mixed-reality-toolkit-examples)

| Cartella | Componente | Descrizione |
| --- | --- | --- |
| MRTK/Esempi | | |
| | Esempi~ | Cartella nascosta (nell'editor unity) che contiene le scene e gli asset di esempio. |
| | StandardAssets | Asset comuni condivisi da più scene demo. |

Dipendenze:

- Base ( `com.microsoft.mixedreality.toolkit.foundation` )
- Estensioni (`com.microsoft.mixedreality.toolkit.extensions`)

## <a name="see-also"></a>Vedere anche

- [Panoramica dell'architettura](../architecture/overview.md)
- [Sistemi, servizi di estensione e provider di dati](../architecture/systems-extensions-providers.md)
- [Realtà mista Toolkit e Unity Gestione pacchetti](../configuration/usingupm.md)

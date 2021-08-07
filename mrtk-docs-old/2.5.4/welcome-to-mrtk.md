---
title: MRTK_Documentation
description: Pagina della documentazione introduttiva di MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: b555401c6e3f410b5b90f3fa9956ee3408aaad3a56796e3afb0bebd6c4e25474
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115188211"
---
# <a name="what-is-the-mixed-reality-toolkit"></a>Informazioni su Mixed Reality Toolkit

![Mixed Reality Toolkit](features/images/Logo_MRTK_Unity_Banner.png)

MRTK-Unity è un progetto gestito da Microsoft che fornisce un set di componenti e funzionalità che consentono di accelerare lo sviluppo di app di realtà mista multipiattaforma in Unity. Ecco alcune delle sue funzioni:

* Fornisce il **sistema di input multipiattaforma e i blocchi predefiniti per le interazioni spaziali e l'interfaccia utente.**
* Abilita **la creazione rapida di prototipi** tramite simulazione nell'editor che consente di visualizzare immediatamente le modifiche.
* Funziona come un **framework estendibile che** offre agli sviluppatori la possibilità di sostituire i componenti di base.
* **Supporta un'ampia gamma di piattaforme,** tra cui
  * OpenXR (Unity 2020.2 o versione più recente)
    * Microsoft HoloLens 2
    * Visori VR di Windows Mixed Reality
  * Windows Mixed Reality
    * Microsoft HoloLens
    * Microsoft HoloLens 2
    * Visori VR di Windows Mixed Reality
  * Oculus (Unity 2019.3 o versione più recente)
    * Oculus Quest
  * OpenVR
    * Visori VR di Windows Mixed Reality
    * PIÙ VIVE Vive
    * Oculus Rift
  * Tracciamento della mano Ultraleap
  * Dispositivi mobili come iOS e Android

## <a name="getting-started-with-mrtk"></a>Introduzione a MRTK

Se non hai ancora iniziato a usare lo sviluppo di MRTK o realtà mista in **Unity,** ti consigliamo di iniziare dall'inizio del percorso di sviluppo di [Unity](https://docs.microsoft.com/windows/mixed-reality/unity-development-overview?tabs=mrtk%2Chl2) nel Microsoft Docs. Il percorso di sviluppo di Unity è specifico per illustrare ai nuovi sviluppatori l'installazione, i concetti di base e l'uso di MRTK.

| IMPORTANTE: il percorso di sviluppo di Unity attualmente usa **MRTK versione 2.4.0** e **Unity 2019.4.** |
| --- |

Gli sviluppatori esperti di realtà mista o MRTK possono consultare i collegamenti nella sezione successiva per i pacchetti e le note sulla versione più recenti.

## <a name="documentation"></a>Documentazione

| [![Note sulla versione](features/images/MRTK_Icon_ReleaseNotes.png)](/windows/mixed-reality/mrtk-unity/release-notes/mrtk-27-release-notes)<br/>[Note sulla versione](/windows/mixed-reality/mrtk-unity/release-notes/mrtk-27-release-notes)| [![Panoramica di MRTK](features/images/MRTK_Icon_ArchitectureOverview.png)](/windows/mixed-reality/mrtk-unity/architecture/overview)<br/>[Panoramica di MRTK](/windows/mixed-reality/mrtk-unity/architecture/overview)| [![Guide alle funzionalità](features/images/MRTK_Icon_FeatureGuides.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/features/ux-building-blocks/Button.html)<br/>[Guide alle funzionalità](https://microsoft.github.io/MixedRealityToolkit-Unity/features/ux-building-blocks/Button.html)| [![Informazioni di riferimento sulle API](features/images/MRTK_Icon_APIReference.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/api/Microsoft.MixedReality.Toolkit.html)<br/>[Riferimento API](https://microsoft.github.io/MixedRealityToolkit-Unity/api/Microsoft.MixedReality.Toolkit.html)|
|:---|:---|:---|:---|

## <a name="build-status"></a>Stato della compilazione

| Ramo | Stato ci | Stato della documentazione |
|---|---|---|
| `mrtk_development` |[![Stato ci](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_apis/build/status/public/mrtk_CI?branchName=mrtk_development)](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_build/latest?definitionId=15)|[![Stato della documentazione](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_apis/build/status/public/mrtk_docs?branchName=mrtk_development)](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_build/latest?definitionId=7)

## <a name="required-software"></a>Requisiti software

 | [ ![ Windows SDK 18362+](features/images/MRTK170802_Short_17.png)](https://developer.microsoft.com/windows/downloads/windows-10-sdk) [Windows SDK 18362+](https://developer.microsoft.com/windows/downloads/windows-10-sdk)| [ ![ Unity](features/images/MRTK170802_Short_18.png)](https://unity3d.com/get-unity/download/archive) [Unity 2018.4.x](https://unity3d.com/get-unity/download/archive)| [ ![ Visual Studio 2019](features/images/MRTK170802_Short_19.png)](http://dev.windows.com/downloads) [Visual Studio 2019](http://dev.windows.com/downloads)| [ ![ Emulatori (facoltativo)](features/images/MRTK170802_Short_20.png)](https://docs.microsoft.com/windows/mixed-reality/using-the-hololens-emulator) [Emulatori (facoltativo)](https://docs.microsoft.com/windows/mixed-reality/using-the-hololens-emulator)|
| :--- | :--- | :--- | :--- |
| Per creare app con MRTK v2, è necessario Aggiornamento di Windows 10 (maggio 2019) SDK. <br> Per eseguire app per visori VR immersive, è necessario il Windows 10 Fall Creators Update. | Il motore 3D di Unity offre il supporto per la compilazione di progetti di realtà mista in Windows 10 | Visual Studio viene usato per la modifica del codice, la distribuzione e la compilazione di pacchetti di app UWP | Gli emulatori consentono di testare l'app senza il dispositivo in un ambiente simulato |

## <a name="feature-areas"></a>Aree di funzionalità

| ![Input System ](features/images/MRTK_Icon_InputSystem.png) [Input System](features/input/overview.md)<br/>&nbsp;  | ![Tracciamento mano<br/> (HoloLens 2) ](features/images/MRTK_Icon_HandTracking.png) [Hand Tracking <br/> (HoloLens 2)](features/input/hand-tracking.md) | ![Tracciamento oculare<br/> (HoloLens 2) ](features/images/MRTK_Icon_EyeTracking.png) [Tracciamento <br/> oculare (HoloLens 2)](features/eye-tracking/eye-tracking-Main.md) | ![Profili ](features/images/MRTK_Icon_Profiles.png) [profili](configuration/mixed-reality-configuration-guide.md)<br/>&nbsp; | ![Tracciamento<br/> (Ultraleap) ](features/images/MRTK_Icon_HandTracking.png) [Hand Tracking (Ultraleap)](features/cross-platform/leap-motion-mrtk.md)|
| :--- | :--- | :--- | :--- | :--- |
| ![Controlli dell'interfaccia utente 1 ](features/images/MRTK_Icon_UIControls.png) [Controlli dell'interfaccia utente 2](welcome-to-mrtk.md#ux-building-blocks)<br/>&nbsp; | ![Risolutori ](features/images/MRTK_Icon_Solver.png) [1](features/ux-building-blocks/solvers/solver.md)<br/>&nbsp; | ![Multi-Scene<br/> Manager ](features/images/MRTK_Icon_SceneSystem.png) [Multi-Scene <br/> Manager](features/scene-system/scene-system-getting-started.md) | ![Spatial<br/> Awareness ](features/images/MRTK_Icon_SpatialUnderstanding.png) [Spatial <br/> Awareness](features/spatial-awareness/spatial-awareness-getting-started.md) | ![Strumento<diagnostica br/> ](features/images/MRTK_Icon_Diagnostics.png) [ <br/> ](features/diagnostics/diagnostics-system-getting-started.md) |
| ![Visualizzazione shader standard MRTK Visualizzazione di esempio dello ](features/images/MRTK_Icon_StandardShader.png) [shader standard MRTK](features/rendering/mrtk-standard-shader.md?q=shader) | ![Riconoscimento vocale & ](features/images/MRTK_Icon_VoiceCommand.png) [](features/input/speech.md) voce<br/> & [Dettatura](features/input/dictation.md) | ![Limite<br/>system boundary ](features/images/MRTK_Icon_Boundary.png) [ <br/> system](features/boundary/boundary-system-getting-started.md)| ![Simulazione nell'editor<br/>](features/images/MRTK_Icon_InputSystem.png) [simulazione <br/> nell'editor](features/input-simulation/input-simulation-service.md) | ![Funzionalità sperimentali<br/>funzionalità ](features/images/MRTK_Icon_Experimental.png) [ <br/> sperimentali](contributing/experimental-features.md)|

## <a name="ux-building-blocks"></a>Blocchi predefiniti dell'esperienza utente

|  [ ![ Pulsante](features/images/Button/MRTK_Button_Main.png)](features/ux-building-blocks/button.md) [Pulsante](features/ux-building-blocks/button.md) | [ ![ Controllo Limiti del](features/images/bounds-control/MRTK_BoundsControl_Main.png)](features/ux-building-blocks/bounds-control.md) controllo [Bounds](features/ux-building-blocks/bounds-control.md) | [ ![ Manipolatore di oggetti](features/images/manipulation-handler/MRTK_Manipulation_Main.png)](features/ux-building-blocks/object-manipulator.md) [Manipolatore di oggetti](features/ux-building-blocks/object-manipulator.md) |
|:--- | :--- | :--- |
| Controllo pulsante che supporta vari metodi di input, tra cui HoloLens 2 mano articolata del controllo | Interfaccia utente standard per la modifica di oggetti nello spazio 3D | Script per la manipolazione di oggetti con una o due mani |
|  [ ![ Slate](features/images/slate/MRTK_Slate_Main.png)](features/ux-building-blocks/slate.md) [Slate](features/ux-building-blocks/slate.md) | [ ![ Tastiera di sistema tastiera](features/images/system-keyboard/MRTK_SystemKeyboard_Main.png)](features/ux-building-blocks/system-keyboard.md) di [sistema](features/ux-building-blocks/system-keyboard.md) | [ ![ Interactable](features/images/interactable/InteractableExamples.png)](features/ux-building-blocks/interactable.md) [Interactable](features/ux-building-blocks/interactable.md) |
| Piano di stile 2D che supporta lo scorrimento con input della mano articolato | Script di esempio dell'uso della tastiera di sistema in Unity  | Uno script per rendere gli oggetti intervienibili con gli stati di visualizzazione e il supporto del tema |
|  [ ![ Risolutore](features/images/solver/MRTK_Solver_Main.png)](features/ux-building-blocks/solvers/solver.md) [](features/ux-building-blocks/solvers/solver.md) | [ ![ Raccolta di oggetti Raccolta](features/images/object-collection/MRTK_ObjectCollection_Main.jpg)](features/ux-building-blocks/object-collection.md) [oggetti](features/ux-building-blocks/object-collection.md) | [ ![ Descrizione comando](features/images/tooltip/MRTK_Tooltip_Main.png)](features/ux-building-blocks/tooltip.md) [](features/ux-building-blocks/tooltip.md) |
| Vari comportamenti di posizionamento degli oggetti, ad esempio tag lungo, blocco del corpo, dimensioni della visualizzazione costanti e magnetismo della superficie | Script per il layout di una matrice di oggetti in una forma tridimensionale | Interfaccia utente di annotazione con un sistema di ancoraggio/pivot flessibile, che può essere usato per l'etichettatura di controller del movimento e oggetti |
|  [ ![ Dispositivo di scorrimento](features/images/slider/MRTK_UX_Slider_Main.jpg)](features/ux-building-blocks/sliders.md) [](features/ux-building-blocks/sliders.md) | [ ![ MrTK Standard Shader View 2](features/images/mrtk-standard-shader/MRTK_StandardShader.jpg)](features/rendering/mrtk-standard-shader.md) [MRTK Standard Shader 2](features/rendering/mrtk-standard-shader.md) | [ ![ Hand Menu 1](features/images/solver/MRTK_UX_HandMenu.png)](features/ux-building-blocks/hand-menu.md) [Hand Menu 2](features/ux-building-blocks/hand-menu.md) |
| Interfaccia utente del dispositivo di scorrimento per la modifica dei valori che supportano l'interazione con il tracciamento diretto della mano | Lo shader Standard di MRTK supporta vari Fluent di progettazione con prestazioni | Interfaccia utente bloccata a mano per l'accesso rapido con il risolutore di vincoli di mano |
|  [ ![ Barra dell'app barra](features/images/app-bar/MRTK_AppBar_Main.png)](features/ux-building-blocks/app-bar.md) [dell'app](features/ux-building-blocks/app-bar.md) | [ ![ Puntatori](features/images/Pointers/MRTK_Pointer_Main.png)](features/input/pointers.md) [](features/input/Pointers.md) | [ ![ Visualizzazione punta del dito](features/images/fingertip/MRTK_FingertipVisualization_Main.png)](features/ux-building-blocks/fingertip-visualization.md) [Visualizzazione punta del dito](features/ux-building-blocks/fingertip-visualization.md) |
| Interfaccia utente per l'attivazione manuale del controllo Bounds | Informazioni sui vari tipi di puntatori | L'affordance visivo sulla punta del dito che migliora la confidenza per l'interazione diretta |
|  Near Menu Near Menu [ ![ (Menu](features/images/near-menu/MRTK_UX_NearMenu.png)](features/ux-building-blocks/near-menu.md) [vicino al menu vicino)](features/ux-building-blocks/near-menu.md) | [ ![ Consapevolezza spaziale 1](features/images/spatial-awareness/MRTK_SpatialAwareness_Main.png)](features/spatial-awareness/spatial-awareness-getting-started.md) [Consapevolezza spaziale](features/spatial-awareness/spatial-awareness-getting-started.md) | [ ![ Dettatura comando](features/images/input/MRTK_Input_Speech.png)](features/input/speech.md) vocale [](features/input/speech.md)  /  [](features/input/dictation.md) |
| Interfaccia utente a menu mobile per le interazioni da vicino | Fare in modo che gli oggetti olografici interagiscano con gli ambienti fisici | Script ed esempi per l'integrazione dell'input vocale |
|  [ ![ Indicatore di stato Indicatore](features/images/progress-indicator/MRTK_ProgressIndicator_Main.png)](features/ux-building-blocks/progress-indicator.md) di [stato](features/ux-building-blocks/progress-indicator.md) | [ ![ Finestra di](features/images/Dialog/MRTK_UX_Dialog_Main.png)](features/experimental/dialog.md) [dialogo [Sperimentale]](features/experimental/dialog.md) | [ ![ Hand Hand](features/images/hand-coach/MRTK_UX_HandCoach_Main.jpg)](features/experimental/hand-coach.md) [Hand Hand](features/experimental/hand-coach.md) |
| Indicatore visivo per la comunicazione del processo o dell'operazione dei dati | Interfaccia utente per chiedere conferma o acknowledgement dell'utente  | Componente che consente di guidare l'utente quando il movimento non è stato insegnato |
|  [ ![ Hand Physics Service](features/images/hand-physics/MRTK_UX_HandPhysics_Main.jpg)](features/experimental/hand-physics-service.md) Hand Physics Service [[Experimental]](features/experimental/hand-physics-service.md) | [ ![ Raccolta Scrolling Collection](features/images/scrolling-collection/ScrollingCollection_Main.jpg)](features/ux-building-blocks/scrolling-object-collection.md) [Scrolling](features/ux-building-blocks/scrolling-object-collection.md) | [ ![ Dock](features/images/Dock/MRTK_UX_Dock_Main.png)](features/experimental/dock.md) [[Sperimentale]](features/experimental/dock.md) |
| Il servizio di fisica della mano consente eventi rigidi di collisione del corpo e interazioni con le mani articolate | Raccolta di oggetti che scorre in modo nativo gli oggetti 3D | Dock consente di spostare gli oggetti da e verso posizioni predeterminate |
|  [ ![ Tracciamento oculare: Selezione della destinazione](features/images/eye-tracking/mrtk_et_targetselect.png)](features/eye-tracking/eye-tracking-target-selection.md) [Tracciamento oculare: selezione della destinazione](features/eye-tracking/eye-tracking-target-selection.md) | [ ![ Tracciamento oculare: navigazione](features/images/eye-tracking/mrtk_et_navigation.png)](features/eye-tracking/eye-tracking-navigation.md) [tracciamento oculare: navigazione](features/eye-tracking/eye-tracking-navigation.md) | [ ![ Tracciamento oculare: Tracciamento](features/images/eye-tracking/mrtk_et_heatmaps.png)](features/eye-tracking/eye-tracking-examples-overview.md#visualization-of-visual-attention) [oculare mappa termica: mappa termica](features/eye-tracking/eye-tracking-examples-overview.md#visualization-of-visual-attention) |
| Combina gli occhi, la voce e l'input delle mani per selezionare in modo semplice e rapido gli ologrammi nella scena | Informazioni su come scorrere automaticamente il testo o ingrandire fluently il contenuto con stato attivo in base a ciò che si sta esaminando | Esempi per la registrazione, il caricamento e la visualizzazione di ciò che gli utenti hanno visto nell'app |

## <a name="tools"></a>Strumenti

|  [ ![ Ottimizza finestra Ottimizza](features/images/MRTK_Icon_OptimizeWindow.png)](features/tools/optimize-window.md) [finestra](features/tools/optimize-window.md) | [ ![ Finestra dipendenze finestra](features/images/MRTK_Icon_DependencyWindow.png)](features/tools/dependency-window.md) [dipendenze](features/tools/dependency-window.md) | ![Finestra Di compilazione](features/images/MRTK_Icon_BuildWindow.png) Finestra Di compilazione | [ ![ Registrazione di input](features/images/MRTK_Icon_InputRecording.png)](features/input-simulation/input-animation-recording.md) Registrazione di [input](features/input-simulation/input-animation-recording.md) |
|:--- | :--- | :--- | :--- |
| Automatizzare la configurazione dei progetti di realtà mista per ottimizzare le prestazioni | Analizzare le dipendenze tra asset e identificare gli asset inutilizzati |  Configurare ed eseguire un processo di compilazione end-to-end per le applicazioni di realtà mista | Registrare e riprodurre i dati relativi al movimento della testa e al tracciamento della mano nell'editor |

## <a name="example-scenes"></a>Scene di esempio

Esplora i vari tipi di interazioni e controlli dell'interfaccia utente di MRTK in [questa scena di esempio.](features/example-scenes/hand-interaction-examples.md)

Altre scene di esempio sono disponibili [**nella cartella Assets/MixedRealityToolkit.Examples/Demos.**](/Assets/MixedRealityToolkit.Examples/Demos)

[![Scena di esempio 2](features/images/MRTK_Examples.png)](features/example-scenes/hand-interaction-examples.md)

## <a name="mrtk-examples-hub"></a>Hub degli esempi di MRTK

Con l'hub degli esempi di MRTK è possibile provare varie scene di esempio in MRTK.
I pacchetti di app predefiniti per HoloLens(x86), HoloLens 2 (ARM) e Windows Mixed Reality visori VR immersive (x64) sono disponibili nella cartella [**Release Assets (Rilascia**](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/tag/v2.4.0) asset). [Usare il Windows Portale di dispositivi per installare le app in HoloLens](https://docs.microsoft.com/hololens/hololens-install-apps#use-the-windows-device-portal-to-install-apps-on-hololens). In HoloLens 2 possibile scaricare e installare [l'hub di esempi MRTK tramite l'app Microsoft Store](https://www.microsoft.com/p/mrtk-examples-hub/9mv8c39l2sj4).

Per informazioni dettagliate sulla creazione di un hub a più scene con il sistema di scena e il servizio di transizione della scena di MRTK, vedere la pagina [Examples Hub README](features/example-scenes/example-hub.md) (File LEGGIMI dell'hub di esempi).

[![Hub scena di esempio](features/images/MRTK_ExamplesHub.png)](features/example-scenes/hand-interaction-examples.md)

## <a name="sample-apps-made-with-mrtk"></a>App di esempio effettuate con MRTK

| [![Tavola periodica degli elementi](features/images/MRDL_PeriodicTable.jpg)](https://docs.microsoft.com/windows/mixed-reality/periodic-table-of-the-elements-2.md)| [![Galaxy Explorer 1](features/images/MRTK_GalaxyExplorer.jpg)](https://docs.microsoft.com/windows/mixed-reality/galaxy-explorer-update)| [![Galaxy Explorer 2](features/images/MRDL_Surfaces.jpg)](https://docs.microsoft.com/windows/mixed-reality/galaxy-explorer-update)|
|:--- | :--- | :--- |
| [La tabella](https://github.com/Microsoft/MRDL_Unity_PeriodicTable) periodica degli elementi è un'app di esempio open source che illustra come usare il sistema di input e i blocchi predefiniti di MRTK per creare un'esperienza app per visori VR HoloLens e immersive. Leggere la storia della portabilità: Portare la tabella [periodica dell'app Elements HoloLens 2 con MRTK v2](https://medium.com/@dongyoonpark/bringing-the-periodic-table-of-the-elements-app-to-hololens-2-with-mrtk-v2-a6e3d8362158) |[Galaxy Explorer](https://github.com/Microsoft/GalaxyExplorer) è un'app di esempio open source sviluppata originariamente nel mese di marzo 2016 nell'ambito della HoloLens 'Share Your Idea'. Galaxy Explorer è stato aggiornato con nuove funzionalità per HoloLens 2, usando MRTK v2. Leggere la storia: [The Making of Galaxy Explorer for HoloLens 2](https://docs.microsoft.com/windows/mixed-reality/galaxy-explorer-update) |[Surfaces](https://github.com/Microsoft/GalaxyExplorer) è un'app di esempio open source per HoloLens 2 che esplora come è possibile creare una tattilità con elementi visivi, audio e tracciamento delle mani completamente articolati. Per informazioni dettagliate sulla progettazione e lo sviluppo, vedere la sessione Microsoft MR Dev Days [Learnings from the Surfaces app](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Learnings-from-the-MR-Surfaces-App) (Apprendimento della sessione di Microsoft MR Dev Days dall'app Surfaces). |

## <a name="session-videos-from-mixed-reality-dev-days-2020"></a>Video di sessione di Mixed Reality Dev Days 2020

| [![MRDevDays 1](features/images/MRDevDays_Session1.png)](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Intro-to-MRTK-Unity)| [![MRDevDays 3](features/images/MRDevDays_Session2.png)](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/MRTKs-UX-Building-Blocks)| [![MRDevDays 2](features/images/MRDevDays_Session3.png)](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/MRTK-Performance-and-Shaders)|
|:--- | :--- | :--- |
| Esercitazione su come creare una semplice app MRTK dall'inizio alla fine. Informazioni sui concetti di interazione e sulle funzionalità multipiattaforma di MRTK. | Approfondimento sui blocchi predefiniti dell'esperienza utente di MRTK che consentono di creare esperienze di realtà mista di qualità. | Introduzione agli strumenti per le prestazioni, sia in MRTK che esterni, nonché una panoramica dello shader standard MRTK. |

Vedi [Mixed Reality Dev Days per](https://docs.microsoft.com/windows/mixed-reality/mr-dev-days-sessions) esplorare altri video di sessione.

## <a name="engage-with-the-community"></a>Interagire con la community

* Partecipare alla conversazione su MRTK in [Slack.](https://holodevelopers.slack.com/) È possibile partecipare alla community di Slack tramite il [mittente dell'invito automatico](https://holodevelopersslack.azurewebsites.net/).

* Porre domande sull'uso di MRTK [Stack Overflow](https://stackoverflow.com/questions/tagged/mrtk) usando il tag **MRTK.**

* Cercare i [problemi noti o](https://github.com/Microsoft/MixedRealityToolkit-Unity/issues) creare un nuovo problema [se](https://github.com/Microsoft/MixedRealityToolkit-Unity/issues) si verificano problemi nel codice MRTK.

* Per domande sui contributi a MRTK, visitare il canale [mixed-reality-toolkit](https://holodevelopers.slack.com/messages/C2H4HT858) su Slack.

Questo progetto ha adottato il [Codice di comportamento di Microsoft per l'open source](https://opensource.microsoft.com/codeofconduct/).
Per altre informazioni, vedere le [Domande frequenti sul codice di comportamento](https://opensource.microsoft.com/codeofconduct/faq/) o scrivere a [opencode@microsoft.com](mailto:opencode@microsoft.com) per domande aggiuntive o commenti.

## <a name="useful-resources-on-the-mixed-reality-dev-center"></a>Risorse utili sul modello di realtà mista Dev Center

| ![Individuazione ](features/images/mrdevcenter/icon-discover.png) [individuazione](https://docs.microsoft.com/windows/mixed-reality/)| ![Progettazione ](features/images/mrdevcenter/icon-design.png) [](https://docs.microsoft.com/windows/mixed-reality/design)| ![Sviluppare ](features/images/mrdevcenter/icon-develop.png) [lo sviluppo](https://docs.microsoft.com/windows/mixed-reality/development)| ![Distribuisci) ](features/images/mrdevcenter/icon-distribute.png) [Distribuisci](https://docs.microsoft.com/windows/mixed-reality/implementing-3d-app-launchers)|
| :--------------------- | :----------------- | :------------------ | :------------------------ |
| Informazioni su come creare esperienze di realtà mista per HoloLens visori VR immersive.          | Ottenere le guide di progettazione. Compilare l'interfaccia utente. Informazioni sulle interazioni e sull'input.     | Ottenere le guide di sviluppo. Informazioni sulla tecnologia. Comprendere la scienza.       | Preparare l'app per gli utenti e valutare la possibilità di creare un'utilità di avvio 3D. |

## <a name="useful-resources-on-azure"></a>Risorse utili in Azure

| ![Ancoraggi nello spazio](features/images/mrdevcenter/icon-azurespatialanchors.png)<br> [Ancoraggi nello spazio](https://docs.microsoft.com/azure/spatial-anchors/)| ![Servizi Voce di ](features/images/mrdevcenter/icon-azurespeechservices.png) [Servizi di riconoscimento vocale](https://docs.microsoft.com/azure/cognitive-services/speech-service/)| ![Servizi visione ](features/images/mrdevcenter/icon-azurevisionservices.png) [visione](https://docs.microsoft.com/azure/cognitive-services/computer-vision/)|
| :------------------------| :--------------------- | :---------------------- |
| Ancoraggi nello stato spaziale è un servizio multipiattaforma che consente di creare esperienze di realtà mista usando oggetti che mantendono la posizione tra i dispositivi nel corso del tempo.| Individuare e integrare nell'applicazione le funzionalità vocali di Azure, come il riconoscimento vocale, il riconoscimento del parlante o la traduzione vocale.| Identificare e analizzare il contenuto di immagini o video con i servizi di visione artificiale come il rilevamento dei volti, il riconoscimento delle emozioni o Video Indexer. |

## <a name="learn-more-about-the-mrtk-project"></a>Altre informazioni sul progetto MRTK

È possibile trovare il materiale di pianificazione [nel wiki](https://github.com/Microsoft/MixedRealityToolkit-Unity/wiki) nella sezione Project management. È sempre possibile visualizzare gli elementi su cui il team sta lavorando attivamente nel problema relativo al piano di iterazione.

## <a name="how-to-contribute"></a>Come contribuire

Per informazioni su come contribuire a MRTK, vedere [Contribuire a](contributing/contributing.md).

**Per informazioni dettagliate sui diversi rami usati nei repository di Toolkit realtà mista, vedere questa [Guida ai rami qui.](https://github.com/Microsoft/MixedRealityToolkit-Unity/wiki/Branch-Guide)**

## <a name="getting-help"></a>Guida

Se si verificano problemi causati da MRTK o in caso di domande su come eseguire un'operazione, sono disponibili alcune risorse utili:

* Per i report sui bug, [segnala un](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/new/choose) problema nel GitHub del bug.
* Per domande, contattare [StackOverflow](https://stackoverflow.com/questions/tagged/mrtk) o il canale [mixed-reality-toolkit](https://holodevelopers.slack.com/messages/C2H4HT858) su Slack. È possibile partecipare alla community di Slack tramite il [mittente dell'invito automatico](https://holodevelopersslack.azurewebsites.net/).

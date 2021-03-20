---
title: MRTK_Documentation
description: Pagina della documentazione introduttiva di MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: d7f6f7516b838b2b1a538c668917929f7696a2f2
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2021
ms.locfileid: "104702017"
---
# <a name="what-is-the-mixed-reality-toolkit"></a>Che cos'è il Toolkit di realtà mista

![Mixed Reality Toolkit](features/images/Logo_MRTK_Unity_Banner.png)

MRTK-Unity è un progetto gestito da Microsoft che fornisce un set di componenti e funzionalità che consentono di accelerare lo sviluppo di app di realtà mista multipiattaforma in Unity. Ecco alcune delle sue funzioni:

* Fornisce il **sistema di input multipiattaforma e i blocchi predefiniti per le interazioni spaziali e l'interfaccia utente**.
* Consente la **prototipazione rapida** tramite la simulazione in-editor che consente di visualizzare immediatamente le modifiche.
* Opera come **framework estendibile** che offre agli sviluppatori la possibilità di scambiare componenti di base.
* **Supporta un'ampia gamma di piattaforme**, tra cui
  * OpenXR (Unity 2020,2 o versione successiva)
    * Microsoft HoloLens 2
    * Visori VR di Windows Mixed Reality
  * Windows Mixed Reality
    * Microsoft HoloLens
    * Microsoft HoloLens 2
    * Visori VR di Windows Mixed Reality
  * Oculus (Unity 2019,3 o versione successiva)
    * Oculus-ricerca
  * OpenVR
    * Visori VR di Windows Mixed Reality
    * HTC vive
    * Oculus Rift
  * Tracciamento della mano Ultraleap
  * Dispositivi mobili come iOS e Android

## <a name="getting-started-with-mrtk"></a>Introduzione a MRTK

Se non si ha familiarità con MRTK o lo sviluppo di realtà mista in Unity, **è consigliabile iniziare dall'inizio del percorso di** [sviluppo unity](https://docs.microsoft.com/windows/mixed-reality/unity-development-overview?tabs=mrtk%2Chl2) nel Microsoft docs. Il percorso di sviluppo Unity è appositamente progettato per esplorare nuovi sviluppatori tramite l'installazione, i concetti di base e l'uso di MRTK.

| IMPORTANTE: il percorso di sviluppo di Unity usa attualmente **MRTK versione 2.4.0** e **Unity 2019,4**. |
| --- |

Se si è uno sviluppatore MRTK o di realtà mista, controllare i collegamenti nella sezione successiva per i pacchetti più recenti e le note sulla versione.

## <a name="documentation"></a>Documentazione

| [![Note sulla versione](features/images/MRTK_Icon_ReleaseNotes.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/ReleaseNotes.html)<br/>[Note sulla versione](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/ReleaseNotes.html)| [![Panoramica di MRTK](features/images/MRTK_Icon_ArchitectureOverview.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Architecture/Overview.html)<br/>[Panoramica di MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Architecture/Overview.html)| [![Guide alle funzionalità](features/images/MRTK_Icon_FeatureGuides.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/features/ux-building-blocks/Button.html)<br/>[Guide alle funzionalità](https://microsoft.github.io/MixedRealityToolkit-Unity/features/ux-building-blocks/Button.html)| [![Riferimento API](features/images/MRTK_Icon_APIReference.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/api/Microsoft.MixedReality.Toolkit.html)<br/>[Riferimento API](https://microsoft.github.io/MixedRealityToolkit-Unity/api/Microsoft.MixedReality.Toolkit.html)|
|:---|:---|:---|:---|

## <a name="build-status"></a>Stato della compilazione

| Ramo | Stato CI | Stato docs |
|---|---|---|
| `mrtk_development` |[![Stato CI](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_apis/build/status/public/mrtk_CI?branchName=mrtk_development)](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_build/latest?definitionId=15)|[![Stato docs](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_apis/build/status/public/mrtk_docs?branchName=mrtk_development)](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_build/latest?definitionId=7)

## <a name="required-software"></a>Requisiti software

 | [ ![ Windows SDK 18362 +](features/images/MRTK170802_Short_17.png)](https://developer.microsoft.com/windows/downloads/windows-10-sdk) [Windows SDK 18362 +](https://developer.microsoft.com/windows/downloads/windows-10-sdk)| [ ![ Unity Unity](features/images/MRTK170802_Short_18.png)](https://unity3d.com/get-unity/download/archive) [2018.4. x](https://unity3d.com/get-unity/download/archive)| Visual [ ![ Studio 2019](features/images/MRTK170802_Short_19.png)](http://dev.windows.com/downloads) [Visual Studio 2019](http://dev.windows.com/downloads)| Emulatori [ ![ (facoltativo)](features/images/MRTK170802_Short_20.png)](https://docs.microsoft.com/windows/mixed-reality/using-the-hololens-emulator) [emulatori (facoltativo)](https://docs.microsoft.com/windows/mixed-reality/using-the-hololens-emulator)|
| :--- | :--- | :--- | :--- |
| Per compilare app con MRTK V2, è necessario Windows 10 May 2019 Update SDK. <br> Per eseguire app per auricolari immersivi, è necessario Windows 10 Fall Creators Update. | Il motore di Unity 3D fornisce supporto per la compilazione di progetti di realtà mista in Windows 10 | Visual Studio viene usato per la modifica del codice, la distribuzione e la creazione di pacchetti di app UWP | Gli emulatori consentono di testare l'app senza il dispositivo in un ambiente simulato |

## <a name="feature-areas"></a>Aree di funzionalità

| ![Sistema di ](features/images/MRTK_Icon_InputSystem.png) [input](features/input/overview.md) del sistema di input<br/>&nbsp;  | ![Rilevamento manuale<BR/> (HoloLens 2) ](features/images/MRTK_Icon_HandTracking.png) [rilevamento della mano <br/> (HoloLens 2)](features/input/hand-tracking.md) | ![Eye Tracking<BR/> (HoloLens 2) ](features/images/MRTK_Icon_EyeTracking.png) [Eye Tracking <br/> (HoloLens 2)](features/eye-tracking/eye-tracking-Main.md) | ![Profili ](features/images/MRTK_Icon_Profiles.png) [](configuration/mixed-reality-configuration-guide.md) profili<br/>&nbsp; | ![Rilevamento manuale<BR/> (Ultraleap) ](features/images/MRTK_Icon_HandTracking.png) [(Ultraleap)](features/cross-platform/leap-motion-mrtk.md)|
| :--- | :--- | :--- | :--- | :--- |
| ![Controlli dell'interfaccia utente 1 ](features/images/MRTK_Icon_UIControls.png) [controlli dell'interfaccia utente 2](welcome-to-mrtk.md#ux-building-blocks)<br/>&nbsp; | ![Risolutori dei risolutori ](features/images/MRTK_Icon_Solver.png) [1](features/ux-building-blocks/solvers/solver.md)<br/>&nbsp; | ![Multiscena<BR/> Manager per ](features/images/MRTK_Icon_SceneSystem.png) [ <br/> più scene](features/scene-system/scene-system-getting-started.md) | ![](features/images/MRTK_Icon_SpatialUnderstanding.png) [ <br/> Conoscenza spaziale](features/spatial-awareness/spatial-awareness-getting-started.md) del<spaziale BR/> | ![](features/images/MRTK_Icon_Diagnostics.png) [ <br/> Strumento di diagnostica](features/diagnostics/diagnostics-system-getting-started.md)<di diagnostica BR/> |
| ![Visualizzazione di esempio dello shader standard MRTK per visualizzazione shader standard ](features/images/MRTK_Icon_StandardShader.png) [MRTK](features/rendering/mrtk-standard-shader.md?q=shader) | ![Sintesi vocale & dettatura ](features/images/MRTK_Icon_VoiceCommand.png) [](features/input/speech.md)<br/> & [Dettatura](features/input/dictation.md) | ![Limite<](features/images/MRTK_Icon_Boundary.png) [ <br/> sistema di limiti](features/boundary/boundary-system-getting-started.md) di sistema br/>| ![Simulazione nell'editor<BR/>simulazione ](features/images/MRTK_Icon_InputSystem.png) [ <br/> ](features/input-simulation/input-simulation-service.md) | ![Funzionalità sperimentali di<BR/>](features/images/MRTK_Icon_Experimental.png) [ <br/> ](contributing/experimental-features.md)|

## <a name="ux-building-blocks"></a>Blocchi predefiniti di UX

|  [Pulsante](features/ux-building-blocks/button.md) [ ![ pulsante](features/images/Button/MRTK_Button_Main.png)](features/ux-building-blocks/button.md) | [Controllo](features/ux-building-blocks/bounds-control.md) dei limiti del [ ![ controllo dei limiti](features/images/bounds-control/MRTK_BoundsControl_Main.png)](features/ux-building-blocks/bounds-control.md) | [Manipolatore oggetto](features/ux-building-blocks/object-manipulator.md) [ ![ manipolatore oggetti](features/images/manipulation-handler/MRTK_Manipulation_Main.png)](features/ux-building-blocks/object-manipulator.md) |
|:--- | :--- | :--- |
| Controllo Button che supporta vari metodi di input, tra cui la mano articolata di HoloLens 2 | Interfaccia utente standard per la modifica di oggetti nello spazio 3D | Script per la modifica di oggetti con una o due mani |
|  [ ![ Ardesia ardesia](features/images/slate/MRTK_Slate_Main.png)](features/ux-building-blocks/slate.md) [](features/ux-building-blocks/slate.md) | [Tastiera sistema](features/ux-building-blocks/system-keyboard.md) [ ![ tastiera](features/images/system-keyboard/MRTK_SystemKeyboard_Main.png)](features/ux-building-blocks/system-keyboard.md) sistema | [ ![ Interazione](features/images/interactable/InteractableExamples.png)](features/ux-building-blocks/interactable.md) interactabile [](features/ux-building-blocks/interactable.md) |
| piano di stile 2D che supporta lo scorrimento con l'input della mano articolata | Script di esempio di uso della tastiera di sistema in Unity  | Uno script per rendere gli oggetti interagiscono con gli stati visivi e il supporto dei temi |
|  [Risolutore](features/ux-building-blocks/solvers/solver.md) [ ![ Risolutore](features/images/solver/MRTK_Solver_Main.png)](features/ux-building-blocks/solvers/solver.md) | [Raccolta oggetti](features/ux-building-blocks/object-collection.md) [ ![ raccolta oggetti](features/images/object-collection/MRTK_ObjectCollection_Main.jpg)](features/ux-building-blocks/object-collection.md) | [Descrizione comando](features/ux-building-blocks/tooltip.md) [ ![ Descrizione comando](features/images/tooltip/MRTK_Tooltip_Main.png)](features/ux-building-blocks/tooltip.md) |
| Vari comportamenti di posizionamento degli oggetti, ad esempio tag-along, blocco del corpo, dimensioni della visualizzazione costante e magnetismo della superficie | Script per il layout di una matrice di oggetti in una forma tridimensionale | Interfaccia utente dell'annotazione con un sistema di ancoraggio/pivot flessibile, che può essere usato per etichettare i controller e gli oggetti di movimento |
|  [ ![ Dispositivo di](features/images/slider/MRTK_UX_Slider_Main.jpg)](features/ux-building-blocks/sliders.md) [scorrimento](features/ux-building-blocks/sliders.md) | [ ![ MRTK standard shader View 2](features/images/mrtk-standard-shader/MRTK_StandardShader.jpg)](features/rendering/mrtk-standard-shader.md) [MRTK standard shader 2](features/rendering/mrtk-standard-shader.md) | Menu a mano [ ![ 1](features/images/solver/MRTK_UX_HandMenu.png)](features/ux-building-blocks/hand-menu.md) menu a [mano 2](features/ux-building-blocks/hand-menu.md) |
| Interfaccia utente Slider per la regolazione dei valori che supportano l'interazione diretta di rilevamento | Lo shader standard di MRTK supporta vari elementi di progettazione fluenti con prestazioni | Interfaccia utente bloccata a mano per accedere rapidamente, usando il Risolutore di vincoli Hand |
|  [Barra dell'app](features/ux-building-blocks/app-bar.md) [ ![ barra dell'app](features/images/app-bar/MRTK_AppBar_Main.png)](features/ux-building-blocks/app-bar.md) | [ ![ Puntatori puntatori](features/images/Pointers/MRTK_Pointer_Main.png)](features/input/pointers.md) [](features/input/Pointers.md) | [Visualizzazione a portata](features/ux-building-blocks/fingertip-visualization.md) di mano [ ![ visualizzazione a mano](features/images/fingertip/MRTK_FingertipVisualization_Main.png)](features/ux-building-blocks/fingertip-visualization.md) |
| Interfaccia utente per l'attivazione manuale del controllo dei limiti | Informazioni sui diversi tipi di puntatori | Offerta visiva a portata di mano che migliora la confidenza per l'interazione diretta |
|  [Menu](features/ux-building-blocks/near-menu.md) vicino a [ ![ menu vicino](features/images/near-menu/MRTK_UX_NearMenu.png)](features/ux-building-blocks/near-menu.md) | Consapevolezza [spaziale](features/spatial-awareness/spatial-awareness-getting-started.md) [ ![ 1](features/images/spatial-awareness/MRTK_SpatialAwareness_Main.png)](features/spatial-awareness/spatial-awareness-getting-started.md) | Dettatura del [comando](features/input/speech.md)Voice del [ ![ comando](features/images/input/MRTK_Input_Speech.png)](features/input/speech.md) Voice  /  [](features/input/dictation.md) |
| Interfaccia utente dei menu a virgola mobile per le interazioni near | Fare in modo che gli oggetti olografici interagiscano con gli ambienti fisici | Script ed esempi per l'integrazione dell'input vocale |
|  [Indicatore di stato](features/ux-building-blocks/progress-indicator.md) [ ![ indicatore di stato](features/images/progress-indicator/MRTK_ProgressIndicator_Main.png)](features/ux-building-blocks/progress-indicator.md) | Finestra di [ ![ dialogo](features/images/Dialog/MRTK_UX_Dialog_Main.png)](features/experimental/dialog.md) [[sperimentale]](features/experimental/dialog.md) | [ ![ Coach Hand Coach](features/images/hand-coach/MRTK_UX_HandCoach_Main.jpg)](features/experimental/hand-coach.md) [[sperimentale]](features/experimental/hand-coach.md) |
| Indicatore visivo per la comunicazione del processo o dell'operazione dati | INTERFACCIA utente per la richiesta di conferma o riconoscimento da un utente  | Componente che consente di guidare l'utente quando il movimento non è stato insegnato |
|  Servizio fisica della mano del [ ![ servizio](features/images/hand-physics/MRTK_UX_HandPhysics_Main.jpg)](features/experimental/hand-physics-service.md) fisica della mano [[sperimentale]](features/experimental/hand-physics-service.md) | [ ![ Scorrimento](features/images/scrolling-collection/ScrollingCollection_Main.jpg)](features/ux-building-blocks/scrolling-object-collection.md) raccolta [scorrevole](features/ux-building-blocks/scrolling-object-collection.md) raccolta | [ ![ Dock Dock](features/images/Dock/MRTK_UX_Dock_Main.png)](features/experimental/dock.md) [[sperimentale]](features/experimental/dock.md) |
| Il servizio di fisica della mano Abilita eventi di collisione del corpo rigidi e interazioni con le mani articolate | Raccolta di oggetti che scorre in modo nativo gli oggetti 3D | Il Dock consente lo spostamento di oggetti all'interno e all'esterno di posizioni predeterminate |
|  [ ![ Rilevamento degli occhi: rilevamento occhi selezione destinazione](features/images/eye-tracking/mrtk_et_targetselect.png)](features/eye-tracking/eye-tracking-target-selection.md) [: selezione destinazione](features/eye-tracking/eye-tracking-target-selection.md) | [ ![ Rilevamento degli occhi:](features/images/eye-tracking/mrtk_et_navigation.png)](features/eye-tracking/eye-tracking-navigation.md) esplorazione [degli occhi: navigazione](features/eye-tracking/eye-tracking-navigation.md) | [ ![ Verifica degli occhi:](features/images/eye-tracking/mrtk_et_heatmaps.png)](features/eye-tracking/eye-tracking-examples-overview.md#visualization-of-visual-attention) [monitoraggio degli occhi della mappa termica: mappa termica](features/eye-tracking/eye-tracking-examples-overview.md#visualization-of-visual-attention) |
| Combina gli occhi, l'input voce e la mano per selezionare gli ologrammi in modo rapido e semplice nella tua scena | Informazioni su come scorrere automaticamente il testo o ingrandire in modo scorrevole il contenuto con lo stato attivo in base a ciò che si sta esaminando | Esempi per la registrazione, il caricamento e la visualizzazione delle informazioni visualizzate dall'utente nell'app |

## <a name="tools"></a>Strumenti

|  [ ![ Ottimizza](features/images/MRTK_Icon_OptimizeWindow.png)](features/tools/optimize-window.md) [finestra ottimizza](features/tools/optimize-window.md) finestra | [Finestra dipendenza](features/tools/dependency-window.md) [ ![ finestra](features/images/MRTK_Icon_DependencyWindow.png)](features/tools/dependency-window.md) dipendenze | ![Finestra di compilazione](features/images/MRTK_Icon_BuildWindow.png) Finestra di compilazione | [Registrazione](features/input-simulation/input-animation-recording.md) input [ ![ registrazione](features/images/MRTK_Icon_InputRecording.png)](features/input-simulation/input-animation-recording.md) input |
|:--- | :--- | :--- | :--- |
| Automatizzare la configurazione dei progetti di realtà mista per le ottimizzazioni delle prestazioni | Analizzare le dipendenze tra le risorse e identificare le risorse inutilizzate |  Configurare ed eseguire un processo di compilazione end-to-end per applicazioni di realtà miste | Registrare e riprodurre i dati del movimento Head e del rilevamento della mano nell'editor |

## <a name="example-scenes"></a>Scene di esempio

Esplorare i diversi tipi di interazioni e i controlli dell'interfaccia utente di MRTK in [questa scena di esempio](features/example-scenes/hand-interaction-examples.md).

È possibile trovare altre scene di esempio nella cartella [**assets/MixedRealityToolkit. examples/Demos**](/Assets/MixedRealityToolkit.Examples/Demos) .

[![Scena di esempio 2](features/images/MRTK_Examples.png)](features/example-scenes/hand-interaction-examples.md)

## <a name="mrtk-examples-hub"></a>Hub esempi MRTK

Con l'hub esempi di MRTK è possibile provare diverse scene di esempio in MRTK.
È possibile trovare i pacchetti dell'app predefiniti per HoloLens (x86), HoloLens 2 (ARM) e gli auricolari immersivi a realtà mista di Windows (x64) nella cartella [**asset di versione**](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/tag/v2.4.0) . [Usare il portale per dispositivi Windows per installare le app in HoloLens](https://docs.microsoft.com/hololens/hololens-install-apps#use-the-windows-device-portal-to-install-apps-on-hololens). In HoloLens 2 è possibile scaricare e installare [l'hub esempi di MRTK tramite l'app Microsoft Store](https://www.microsoft.com/p/mrtk-examples-hub/9mv8c39l2sj4).

Vedere la [pagina del file Leggimi dell'hub esempi](features/example-scenes/example-hub.md) per informazioni dettagliate sulla creazione di un hub a più scene con il sistema di scena di MRTK e il servizio di transizione della scena.

[![Hub scene di esempio](features/images/MRTK_ExamplesHub.png)](features/example-scenes/hand-interaction-examples.md)

## <a name="sample-apps-made-with-mrtk"></a>App di esempio create con MRTK

| [![Tavola periodica degli elementi](features/images/MRDL_PeriodicTable.jpg)](https://medium.com/@dongyoonpark/bringing-the-periodic-table-of-the-elements-app-to-hololens-2-with-mrtk-v2-a6e3d8362158)| [![Galaxy Explorer 1](features/images/MRTK_GalaxyExplorer.jpg)](https://docs.microsoft.com/windows/mixed-reality/galaxy-explorer-update)| [![Galaxy Explorer 2](features/images/MRDL_Surfaces.jpg)](https://docs.microsoft.com/windows/mixed-reality/galaxy-explorer-update)|
|:--- | :--- | :--- |
| [La tabella periodica degli elementi](https://github.com/Microsoft/MRDL_Unity_PeriodicTable) è un'app di esempio Open source che illustra come usare il sistema di input e i blocchi predefiniti di MRTK per creare un'esperienza di app per HoloLens e auricolari immersivi. Leggere la storia di porting: [portare la tabella periodica dell'app elementi a HoloLens 2 con MRTK V2](https://medium.com/@dongyoonpark/bringing-the-periodic-table-of-the-elements-app-to-hololens-2-with-mrtk-v2-a6e3d8362158) |[Galaxy Explorer](https://github.com/Microsoft/GalaxyExplorer) è un'app di esempio Open source che è stata sviluppata in origine nel 2016 marzo come parte della campagna HoloLens ' Condividi la tua idea '. Galaxy Explorer è stato aggiornato con nuove funzionalità per HoloLens 2, usando MRTK V2. Leggi la storia: [creazione di Galaxy Explorer per HoloLens 2](https://docs.microsoft.com/windows/mixed-reality/galaxy-explorer-update) |[Surfaces](https://github.com/Microsoft/GalaxyExplorer) è un'app di esempio Open Source per HoloLens 2, che Esplora come creare una sensazione tattile con l'oggetto visivo, l'audio e il rilevamento manuale completamente articolato. Per informazioni dettagliate sulla progettazione e sullo sviluppo, vedere l'articolo relativo alle informazioni sulla sessione di Microsoft MR dev Days [dall'app Surfaces](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Learnings-from-the-MR-Surfaces-App) . |

## <a name="session-videos-from-mixed-reality-dev-days-2020"></a>Video di sessione da giorni di sviluppo di realtà mista 2020

| [![MRDevDays 1](features/images/MRDevDays_Session1.png)](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Intro-to-MRTK-Unity)| [![MRDevDays 3](features/images/MRDevDays_Session2.png)](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/MRTKs-UX-Building-Blocks)| [![MRDevDays 2](features/images/MRDevDays_Session3.png)](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/MRTK-Performance-and-Shaders)|
|:--- | :--- | :--- |
| Esercitazione su come creare un'app MRTK semplice dall'inizio alla fine. Informazioni sui concetti di interazione e sulle funzionalità multipiattaforma di MRTK. | Approfondimenti sui blocchi predefiniti di MRTK che consentono di creare esperienze di realtà miste. | Introduzione agli strumenti per le prestazioni, sia in MRTK che in esterno, nonché una panoramica dello shader standard MRTK. |

Vedere [giorni di sviluppo di realtà mista](https://docs.microsoft.com/windows/mixed-reality/mr-dev-days-sessions) per esplorare più video di sessione.

## <a name="engage-with-the-community"></a>Interagisci con la community

* Unisciti alla conversazione intorno a MRTK in [Slack](https://holodevelopers.slack.com/). È possibile partecipare alla community di Slack tramite il [mittente dell'invito automatico](https://holodevelopersslack.azurewebsites.net/).

* Porre domande sull'uso di MRTK in [stack overflow](https://stackoverflow.com/questions/tagged/mrtk) usando il tag **MRTK** .

* È possibile cercare [problemi noti](https://github.com/Microsoft/MixedRealityToolkit-Unity/issues) o archiviare un [nuovo problema](https://github.com/Microsoft/MixedRealityToolkit-Unity/issues) se si riscontra un problema nel codice MRTK.

* Per domande su come contribuire a MRTK, vedere il canale [mixed-reality-Toolkit](https://holodevelopers.slack.com/messages/C2H4HT858) in slack.

Questo progetto ha adottato il [Codice di comportamento di Microsoft per l'open source](https://opensource.microsoft.com/codeofconduct/).
Per altre informazioni, vedere le [Domande frequenti sul codice di comportamento](https://opensource.microsoft.com/codeofconduct/faq/) o scrivere a [opencode@microsoft.com](mailto:opencode@microsoft.com) per domande aggiuntive o commenti.

## <a name="useful-resources-on-the-mixed-reality-dev-center"></a>Risorse utili per la realtà mista Dev Center

| ![Individua ](features/images/mrdevcenter/icon-discover.png) [individua](https://docs.microsoft.com/windows/mixed-reality/)| ![Progettazione ](features/images/mrdevcenter/icon-design.png) [](https://docs.microsoft.com/windows/mixed-reality/design) progettazione| ![Sviluppare ](features/images/mrdevcenter/icon-develop.png) [](https://docs.microsoft.com/windows/mixed-reality/development) lo sviluppo| ![Distribuisci) ](features/images/mrdevcenter/icon-distribute.png) [Distribuisci](https://docs.microsoft.com/windows/mixed-reality/implementing-3d-app-launchers)|
| :--------------------- | :----------------- | :------------------ | :------------------------ |
| Scopri come creare esperienze di realtà miste per HoloLens e auricolari immersivi (VR).          | Ottenere le guide di progettazione. Interfaccia utente di compilazione. Informazioni sulle interazioni e sull'input.     | Ottenere le guide di sviluppo. Scopri la tecnologia. Comprendere la scienza.       | Preparare l'app per gli utenti e valutare la possibilità di creare un'utilità di avvio 3D. |

## <a name="useful-resources-on-azure"></a>Risorse utili in Azure

| ![Ancoraggi nello spazio](features/images/mrdevcenter/icon-azurespatialanchors.png)<br> [Ancoraggi nello spazio](https://docs.microsoft.com/azure/spatial-anchors/)| ![Servizi di riconoscimento vocale](features/images/mrdevcenter/icon-azurespeechservices.png) [Servizi di riconoscimento vocale](https://docs.microsoft.com/azure/cognitive-services/speech-service/)| ![Servizi visioni Vision Services ](features/images/mrdevcenter/icon-azurevisionservices.png) [](https://docs.microsoft.com/azure/cognitive-services/computer-vision/)|
| :------------------------| :--------------------- | :---------------------- |
| Gli ancoraggi spaziali sono un servizio multipiattaforma che consente di creare esperienze di realtà miste usando oggetti che rendono permanente la loro posizione tra i dispositivi nel tempo.| Individuare e integrare nell'applicazione le funzionalità vocali di Azure, come il riconoscimento vocale, il riconoscimento del parlante o la traduzione vocale.| Identificare e analizzare il contenuto di immagini o video con i servizi di visione artificiale come il rilevamento dei volti, il riconoscimento delle emozioni o Video Indexer. |

## <a name="learn-more-about-the-mrtk-project"></a>Altre informazioni sul progetto MRTK

Il materiale di pianificazione è reperibile nel [wiki](https://github.com/Microsoft/MixedRealityToolkit-Unity/wiki) nella sezione relativa alla gestione del progetto. È sempre possibile visualizzare gli elementi su cui il team sta lavorando attivamente nel problema relativo al piano di iterazione.

## <a name="how-to-contribute"></a>Come contribuire

Scopri come [contribuire a MRTK per contribuire.](contributing/contributing.md)

**Per informazioni dettagliate sui diversi rami usati nei repository del Toolkit di realtà mista, vedere questa [Guida di Branch](https://github.com/Microsoft/MixedRealityToolkit-Unity/wiki/Branch-Guide).**

## <a name="getting-help"></a>Risorse della Guida

Se si verificano problemi causati da MRTK o in caso di domande su come eseguire un'operazione, sono disponibili alcune risorse che consentono di:

* Per le segnalazioni di bug, inviare [un problema](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/new/choose) nel repository GitHub.
* Per domande, rivolgersi a [StackOverflow](https://stackoverflow.com/questions/tagged/mrtk) o al canale di [reality-Toolkit](https://holodevelopers.slack.com/messages/C2H4HT858) in slack. È possibile partecipare alla community di Slack tramite il [mittente dell'invito automatico](https://holodevelopersslack.azurewebsites.net/).

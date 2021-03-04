---
title: README_MRTK_Documentation
description: Pagina della documentazione introduttiva di MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: e7e17bce16a96c6cb6a9c71224ae57ae64f4030f
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/03/2021
ms.locfileid: "101782677"
---
# <a name="what-is-the-mixed-reality-toolkit"></a>Che cos'è il Toolkit di realtà mista

![Mixed Reality Toolkit](../Images/Logo_MRTK_Unity_Banner.png)

MRTK-Unity è un progetto gestito da Microsoft che fornisce un set di componenti e funzionalità che consentono di accelerare lo sviluppo di app di realtà mista multipiattaforma in Unity. Ecco alcune delle sue funzioni:

* Fornisce il **sistema di input multipiattaforma e i blocchi predefiniti per le interazioni spaziali e l'interfaccia utente**.
* Consente la **prototipazione rapida** tramite la simulazione in-editor che consente di visualizzare immediatamente le modifiche.
* Opera come **framework estendibile** che offre agli sviluppatori la possibilità di scambiare componenti di base.
* **Supporta un'ampia gamma di piattaforme**, tra cui
  * Microsoft HoloLens
  * Microsoft HoloLens 2
  * Visori VR di Windows Mixed Reality
  * Visori VR di OpenVR (HTC Vive/Oculus Rift)
  * Tracciamento della mano Ultraleap
  * Dispositivi mobili come iOS e Android

# <a name="getting-started-with-mrtk"></a>Introduzione a MRTK

Se non si ha familiarità con MRTK o lo sviluppo di realtà mista in Unity, **è consigliabile iniziare dall'inizio del percorso di** [sviluppo unity](https://docs.microsoft.com/windows/mixed-reality/unity-development-overview?tabs=mrtk%2Chl2) nel Microsoft docs. Il percorso di sviluppo Unity è appositamente progettato per esplorare nuovi sviluppatori tramite l'installazione, i concetti di base e l'uso di MRTK.

| IMPORTANTE: il percorso di sviluppo di Unity usa attualmente **MRTK versione 2.4.0** e **Unity 2019,4**. |
| --- |

Se si è uno sviluppatore MRTK o di realtà mista, controllare i collegamenti nella sezione successiva per i pacchetti più recenti e le note sulla versione.

# <a name="documentation"></a>Documentazione

| [![Note sulla versione](../Images/MRTK_Icon_ReleaseNotes.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/../ReleaseNotes.html)<br/>[Note sulla versione](https://microsoft.github.io/MixedRealityToolkit-Unity/../ReleaseNotes.html)| [![Panoramica di MRTK](../Images/MRTK_Icon_ArchitectureOverview.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/../Architecture/Overview.html)<br/>[Panoramica di MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/../Architecture/Overview.html)| [![Guide alle funzionalità](../Images/MRTK_Icon_FeatureGuides.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/../README_Button.html)<br/>[Guide alle funzionalità](https://microsoft.github.io/MixedRealityToolkit-Unity/../README_Button.html)| [![Riferimento API](../Images/MRTK_Icon_APIReference.png)](https://microsoft.github.io/MixedRealityToolkit-Unity/api/Microsoft.MixedReality.Toolkit.html)<br/>[Riferimento API](https://microsoft.github.io/MixedRealityToolkit-Unity/api/Microsoft.MixedReality.Toolkit.html)|
|:---|:---|:---|:---|

# <a name="build-status"></a>Stato della compilazione

| Ramo | Stato CI | Stato docs |
|---|---|---|
| `mrtk_development` |[![Stato CI](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_apis/build/status/public/mrtk_CI?branchName=mrtk_development)](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_build/latest?definitionId=15)|[![Stato docs](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_apis/build/status/public/mrtk_docs?branchName=mrtk_development)](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_build/latest?definitionId=7)

# <a name="required-software"></a>Requisiti software

 | [ ![ Windows SDK 18362 +](../Images/MRTK170802_Short_17.png)](https://developer.microsoft.com/windows/downloads/windows-10-sdk) [Windows SDK 18362 +](https://developer.microsoft.com/windows/downloads/windows-10-sdk)| [ ![ Unity Unity](../Images/MRTK170802_Short_18.png)](https://unity3d.com/get-unity/download/archive) [2018.4. x](https://unity3d.com/get-unity/download/archive)| Visual [ ![ Studio 2019](../Images/MRTK170802_Short_19.png)](http://dev.windows.com/downloads) [Visual Studio 2019](http://dev.windows.com/downloads)| Emulatori [ ![ (facoltativo)](../Images/MRTK170802_Short_20.png)](https://docs.microsoft.com/windows/mixed-reality/using-the-hololens-emulator) [emulatori (facoltativo)](https://docs.microsoft.com/windows/mixed-reality/using-the-hololens-emulator)|
| :--- | :--- | :--- | :--- |
| Per compilare app con MRTK V2, è necessario Windows 10 May 2019 Update SDK. <br> Per eseguire app per auricolari immersivi, è necessario Windows 10 Fall Creators Update. | Il motore di Unity 3D fornisce supporto per la compilazione di progetti di realtà mista in Windows 10 | Visual Studio viene usato per la modifica del codice, la distribuzione e la creazione di pacchetti di app UWP | Gli emulatori consentono di testare l'app senza il dispositivo in un ambiente simulato |

# <a name="feature-areas"></a>Aree di funzionalità

| ![Sistema di ](../Images/MRTK_Icon_InputSystem.png) [input](../Input/Overview.md) del sistema di input<br/>&nbsp;  | ![Rilevamento manuale<BR/> (HoloLens 2) ](../Images/MRTK_Icon_HandTracking.png) [rilevamento della mano <br/> (HoloLens 2)](../Input/HandTracking.md) | ![Eye Tracking<BR/> (HoloLens 2) ](../Images/MRTK_Icon_EyeTracking.png) [Eye Tracking <br/> (HoloLens 2)](../EyeTracking/EyeTracking_Main.md) | ![Profili ](../Images/MRTK_Icon_Profiles.png) [](../out-of-scope/MixedRealityConfigurationGuide.md) profili<br/>&nbsp; | ![Rilevamento manuale<BR/> (Ultraleap) ](../Images/MRTK_Icon_HandTracking.png) [(Ultraleap)](../CrossPlatform/LeapMotionMRTK.md)|
| :--- | :--- | :--- | :--- | :--- |
| ![Controlli dell' ](../Images/MRTK_Icon_UIControls.png) [interfaccia](README.md#ux-building-blocks) utente controlli dell'interfaccia utente<br/>&nbsp; | ![Risolutori dei risolutori ](../Images/MRTK_Icon_Solver.png) [](../README_Solver.md)<br/>&nbsp; | ![Multiscena<BR/> Manager per ](../Images/MRTK_Icon_SceneSystem.png) [ <br/> più scene](../SceneSystem/SceneSystemGettingStarted.md) | ![](../Images/MRTK_Icon_SpatialUnderstanding.png) [ <br/> Conoscenza spaziale](../SpatialAwareness/SpatialAwarenessGettingStarted.md) del<spaziale BR/> | ![](../Images/MRTK_Icon_Diagnostics.png) [ <br/> Strumento di diagnostica](../Diagnostics/DiagnosticsSystemGettingStarted.md)<di diagnostica BR/> |
| ![Shader standard MRTK standard ](../Images/MRTK_Icon_StandardShader.png) [MRTK](../README_MRTKStandardShader.md?q=shader) shader | ![Sintesi vocale & dettatura ](../Images/MRTK_Icon_VoiceCommand.png) [](../Input/Speech.md)<br/> & [Dettatura](../Input/Dictation.md) | ![Limite<](../Images/MRTK_Icon_Boundary.png) [ <br/> sistema di limiti](../Boundary/BoundarySystemGettingStarted.md) di sistema br/>| ![Simulazione nell'editor<BR/>simulazione ](../Images/MRTK_Icon_InputSystem.png) [ <br/> ](../InputSimulation/InputSimulationService.md) | ![Funzionalità sperimentali di<BR/>](../Images/MRTK_Icon_Experimental.png) [ <br/> ](../../Contributing/ExperimentalFeatures.md)|

# <a name="ux-building-blocks"></a>Blocchi predefiniti di UX

|  [Pulsante](../README_Button.md) [ ![ pulsante](../Images/Button/MRTK_Button_Main.png)](../README_Button.md) | [Controllo](../README_BoundsControl.md) dei limiti del [ ![ controllo dei limiti](../Images/BoundsControl/MRTK_BoundsControl_Main.png)](../README_BoundsControl.md) | [Manipolatore oggetto](../README_ObjectManipulator.md) [ ![ manipolatore oggetti](../Images/ManipulationHandler/MRTK_Manipulation_Main.png)](../README_ObjectManipulator.md) |
|:--- | :--- | :--- |
| Controllo Button che supporta vari metodi di input, tra cui la mano articolata di HoloLens 2 | Interfaccia utente standard per la modifica di oggetti nello spazio 3D | Script per la modifica di oggetti con una o due mani |
|  [ ![ Ardesia ardesia](../Images/Slate/MRTK_Slate_Main.png)](../README_Slate.md) [](../README_Slate.md) | [Tastiera sistema](../README_SystemKeyboard.md) [ ![ tastiera](../Images/SystemKeyboard/MRTK_SystemKeyboard_Main.png)](../README_SystemKeyboard.md) sistema | [ ![ Interazione](../Images/Interactable/InteractableExamples.png)](../README_Interactable.md) interactabile [](../README_Interactable.md) |
| piano di stile 2D che supporta lo scorrimento con l'input della mano articolata | Script di esempio di uso della tastiera di sistema in Unity  | Uno script per rendere gli oggetti interagiscono con gli stati visivi e il supporto dei temi |
|  [Risolutore](../README_Solver.md) [ ![ Risolutore](../Images/Solver/MRTK_Solver_Main.png)](../README_Solver.md) | [Raccolta oggetti](../README_ObjectCollection.md) [ ![ raccolta oggetti](../Images/ObjectCollection/MRTK_ObjectCollection_Main.jpg)](../README_ObjectCollection.md) | [Descrizione comando](../README_Tooltip.md) [ ![ Descrizione comando](../Images/Tooltip/MRTK_Tooltip_Main.png)](../README_Tooltip.md) |
| Vari comportamenti di posizionamento degli oggetti, ad esempio tag-along, blocco del corpo, dimensioni della visualizzazione costante e magnetismo della superficie | Script per il layout di una matrice di oggetti in una forma tridimensionale | Interfaccia utente dell'annotazione con un sistema di ancoraggio/pivot flessibile, che può essere usato per etichettare i controller e gli oggetti di movimento |
|  [ ![ Dispositivo di](../Images/Slider/MRTK_UX_Slider_Main.jpg)](../README_Sliders.md) [scorrimento](../README_Sliders.md) | Shader standard [ ![ MRTK standard](../Images/MRTKStandardShader/MRTK_StandardShader.jpg)](../README_MRTKStandardShader.md) [MRTK](../README_MRTKStandardShader.md) shader | [Menu](../README_HandMenu.md) a mano [ ![ menu](../Images/Solver/MRTK_UX_HandMenu.png)](../README_HandMenu.md) a mano |
| Interfaccia utente Slider per la regolazione dei valori che supportano l'interazione diretta di rilevamento | Lo shader standard di MRTK supporta vari elementi di progettazione fluenti con prestazioni | Interfaccia utente bloccata a mano per accedere rapidamente, usando il Risolutore di vincoli Hand |
|  [Barra dell'app](../README_AppBar.md) [ ![ barra dell'app](../Images/AppBar/MRTK_AppBar_Main.png)](../README_AppBar.md) | [ ![ Puntatori puntatori](../Images/Pointers/MRTK_Pointer_Main.png)](../Input/Pointers.md) [](../Input/Pointers.md) | [Visualizzazione a portata](../README_FingertipVisualization.md) di mano [ ![ visualizzazione a mano](../Images/Fingertip/MRTK_FingertipVisualization_Main.png)](../README_FingertipVisualization.md) |
| Interfaccia utente per l'attivazione manuale del controllo dei limiti | Informazioni sui diversi tipi di puntatori | Offerta visiva a portata di mano che migliora la confidenza per l'interazione diretta |
|  [Menu](../README_NearMenu.md) vicino a [ ![ menu vicino](../Images/NearMenu/MRTK_UX_NearMenu.png)](../README_NearMenu.md) | [ ![ ](../Images/SpatialAwareness/MRTK_SpatialAwareness_Main.png)](../SpatialAwareness/SpatialAwarenessGettingStarted.md) [Consapevolezza](../SpatialAwareness/SpatialAwarenessGettingStarted.md) spaziale | Dettatura del [comando](../Input/Speech.md)Voice del [ ![ comando](../Images/Input/MRTK_Input_Speech.png)](../Input/Speech.md) Voice  /  [](../Input/Dictation.md) |
| Interfaccia utente dei menu a virgola mobile per le interazioni near | Fare in modo che gli oggetti olografici interagiscano con gli ambienti fisici | Script ed esempi per l'integrazione dell'input vocale |
|  [Indicatore di stato](../README_ProgressIndicator.md) [ ![ indicatore di stato](../Images/ProgressIndicator/MRTK_ProgressIndicator_Main.png)](../README_ProgressIndicator.md) | Finestra di [ ![ dialogo](../Images/Dialog/MRTK_UX_Dialog_Main.png)](Dialog/README_Dialog.md) [[sperimentale]](Dialog/README_Dialog.md) | [ ![ Coach Hand Coach](../Images/HandCoach/MRTK_UX_HandCoach_Main.jpg)](HandCoach/README_HandCoach.md) [[sperimentale]](HandCoach/README_HandCoach.md) |
| Indicatore visivo per la comunicazione del processo o dell'operazione dati | INTERFACCIA utente per la richiesta di conferma o riconoscimento da un utente  | Componente che consente di guidare l'utente quando il movimento non è stato insegnato |
|  Servizio fisica della mano del [ ![ servizio](../Images/HandPhysics/MRTK_UX_HandPhysics_Main.jpg)](HandPhysicsService/README.md) fisica della mano [[sperimentale]](HandPhysicsService/README.md) | [ ![ Scorrimento](../Images/ScrollingCollection/ScrollingCollection_Main.jpg)](../README_ScrollingObjectCollection.md) raccolta [scorrevole](../README_ScrollingObjectCollection.md) raccolta | [ ![ Dock Dock](../Images/Dock/MRTK_UX_Dock_Main.png)](Dock/README_Dock.md) [[sperimentale]](Dock/README_Dock.md) |
| Il servizio di fisica della mano Abilita eventi di collisione del corpo rigidi e interazioni con le mani articolate | Raccolta di oggetti che scorre in modo nativo gli oggetti 3D | Il Dock consente lo spostamento di oggetti all'interno e all'esterno di posizioni predeterminate |
|  [ ![ Rilevamento degli occhi: rilevamento occhi selezione destinazione](../Images/EyeTracking/mrtk_et_targetselect.png)](../EyeTracking/EyeTracking_TargetSelection.md) [: selezione destinazione](../EyeTracking/EyeTracking_TargetSelection.md) | [ ![ Rilevamento degli occhi:](../Images/EyeTracking/mrtk_et_navigation.png)](../EyeTracking/EyeTracking_Navigation.md) esplorazione [degli occhi: navigazione](../EyeTracking/EyeTracking_Navigation.md) | [ ![ Verifica degli occhi:](../Images/EyeTracking/mrtk_et_heatmaps.png)](../EyeTracking/EyeTracking_ExamplesOverview.md#visualization-of-visual-attention) [monitoraggio degli occhi della mappa termica: mappa termica](../EyeTracking/EyeTracking_ExamplesOverview.md#visualization-of-visual-attention) |
| Combina gli occhi, l'input voce e la mano per selezionare gli ologrammi in modo rapido e semplice nella tua scena | Informazioni su come scorrere automaticamente il testo o ingrandire in modo scorrevole il contenuto con lo stato attivo in base a ciò che si sta esaminando | Esempi per la registrazione, il caricamento e la visualizzazione delle informazioni visualizzate dall'utente nell'app |

# <a name="tools"></a>Strumenti

|  [ ![ Ottimizza](../Images/MRTK_Icon_OptimizeWindow.png)](../Tools/OptimizeWindow.md) [finestra ottimizza](../Tools/OptimizeWindow.md) finestra | [Finestra dipendenza](../Tools/DependencyWindow.md) [ ![ finestra](../Images/MRTK_Icon_DependencyWindow.png)](../Tools/DependencyWindow.md) dipendenze | ![Finestra di compilazione](../Images/MRTK_Icon_BuildWindow.png) Finestra di compilazione | [Registrazione](../InputSimulation/InputAnimationRecording.md) input [ ![ registrazione](../Images/MRTK_Icon_InputRecording.png)](../InputSimulation/InputAnimationRecording.md) input |
|:--- | :--- | :--- | :--- |
| Automatizzare la configurazione dei progetti di realtà mista per le ottimizzazioni delle prestazioni | Analizzare le dipendenze tra le risorse e identificare le risorse inutilizzate |  Configurare ed eseguire un processo di compilazione end-to-end per applicazioni di realtà miste | Registrare e riprodurre i dati del movimento Head e del rilevamento della mano nell'editor |

# <a name="example-scenes"></a>Scene di esempio

Esplorare i diversi tipi di interazioni e i controlli dell'interfaccia utente di MRTK in [questa scena di esempio](../README_HandInteractionExamples.md).

È possibile trovare altre scene di esempio nella cartella [**assets/MixedRealityToolkit. examples/Demos**](/Assets/MixedRealityToolkit.Examples/Demos) .

[![Scena di esempio](../Images/MRTK_Examples.png)](../README_HandInteractionExamples.md)

# <a name="mrtk-examples-hub"></a>Hub esempi MRTK

Con l'hub esempi di MRTK è possibile provare diverse scene di esempio in MRTK.
È possibile trovare i pacchetti dell'app predefiniti per HoloLens (x86), HoloLens 2 (ARM) e gli auricolari immersivi a realtà mista di Windows (x64) nella cartella [**asset di versione**](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/tag/v2.4.0) . [Usare il portale per dispositivi Windows per installare le app in HoloLens](https://docs.microsoft.com/hololens/hololens-install-apps#use-the-windows-device-portal-to-install-apps-on-hololens). In HoloLens 2 è possibile scaricare e installare [l'hub esempi di MRTK tramite l'app Microsoft Store](https://www.microsoft.com/p/mrtk-examples-hub/9mv8c39l2sj4).

Vedere la [pagina del file Leggimi dell'hub esempi](../README_ExampleHub.md) per informazioni dettagliate sulla creazione di un hub a più scene con il sistema di scena di MRTK e il servizio di transizione della scena.

[![Scena di esempio](../Images/MRTK_ExamplesHub.png)](../README_HandInteractionExamples.md)

# <a name="sample-apps-made-with-mrtk"></a>App di esempio create con MRTK

| [![Tavola periodica degli elementi](../Images/MRDL_PeriodicTable.jpg)](https://medium.com/@dongyoonpark/bringing-the-periodic-table-of-the-elements-app-to-hololens-2-with-mrtk-v2-a6e3d8362158)| [![Galaxy Explorer](../Images/MRTK_GalaxyExplorer.jpg)](https://docs.microsoft.com/windows/mixed-reality/galaxy-explorer-update)| [![Galaxy Explorer](../Images/MRDL_Surfaces.jpg)](https://docs.microsoft.com/windows/mixed-reality/galaxy-explorer-update)|
|:--- | :--- | :--- |
| [La tabella periodica degli elementi](https://github.com/Microsoft/MRDL_Unity_PeriodicTable) è un'app di esempio Open source che illustra come usare il sistema di input e i blocchi predefiniti di MRTK per creare un'esperienza di app per HoloLens e auricolari immersivi. Leggere la storia di porting: [portare la tabella periodica dell'app elementi a HoloLens 2 con MRTK V2](https://medium.com/@dongyoonpark/bringing-the-periodic-table-of-the-elements-app-to-hololens-2-with-mrtk-v2-a6e3d8362158) |[Galaxy Explorer](https://github.com/Microsoft/GalaxyExplorer) è un'app di esempio Open source che è stata sviluppata in origine nel 2016 marzo come parte della campagna HoloLens ' Condividi la tua idea '. Galaxy Explorer è stato aggiornato con nuove funzionalità per HoloLens 2, usando MRTK V2. Leggi la storia: [creazione di Galaxy Explorer per HoloLens 2](https://docs.microsoft.com/windows/mixed-reality/galaxy-explorer-update) |[Surfaces](https://github.com/Microsoft/GalaxyExplorer) è un'app di esempio Open Source per HoloLens 2, che Esplora come creare una sensazione tattile con l'oggetto visivo, l'audio e il rilevamento manuale completamente articolato. Per informazioni dettagliate sulla progettazione e sullo sviluppo, vedere l'articolo relativo alle informazioni sulla sessione di Microsoft MR dev Days [dall'app Surfaces](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Learnings-from-the-MR-Surfaces-App) . |

# <a name="session-videos-from-mixed-reality-dev-days-2020"></a>Video di sessione da giorni di sviluppo di realtà mista 2020

| [![MRDevDays](../Images/MRDevDays_Session1.png)](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Intro-to-MRTK-Unity)| [![MRDevDays](../Images/MRDevDays_Session2.png)](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/MRTKs-UX-Building-Blocks)| [![MRDevDays](../Images/MRDevDays_Session3.png)](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/MRTK-Performance-and-Shaders)|
|:--- | :--- | :--- |
| Esercitazione su come creare un'app MRTK semplice dall'inizio alla fine. Informazioni sui concetti di interazione e sulle funzionalità multipiattaforma di MRTK. | Approfondimenti sui blocchi predefiniti di MRTK che consentono di creare esperienze di realtà miste. | Introduzione agli strumenti per le prestazioni, sia in MRTK che in esterno, nonché una panoramica dello shader standard MRTK. |

Vedere [giorni di sviluppo di realtà mista](https://docs.microsoft.com/windows/mixed-reality/mr-dev-days-sessions) per esplorare più video di sessione.

# <a name="engage-with-the-community"></a>Interagisci con la community

* Unisciti alla conversazione intorno a MRTK in [Slack](https://holodevelopers.slack.com/). È possibile partecipare alla community di Slack tramite il [mittente dell'invito automatico](https://holodevelopersslack.azurewebsites.net/).

* Porre domande sull'uso di MRTK in [stack overflow](https://stackoverflow.com/questions/tagged/mrtk) usando il tag **MRTK** .

* È possibile cercare [problemi noti](https://github.com/Microsoft/MixedRealityToolkit-Unity/issues) o archiviare un [nuovo problema](https://github.com/Microsoft/MixedRealityToolkit-Unity/issues) se si riscontra un problema nel codice MRTK.

* Per domande su come contribuire a MRTK, vedere il canale [mixed-reality-Toolkit](https://holodevelopers.slack.com/messages/C2H4HT858) in slack.

Questo progetto ha adottato il [Codice di comportamento di Microsoft per l'open source](https://opensource.microsoft.com/codeofconduct/).
Per altre informazioni, vedere le [Domande frequenti sul codice di comportamento](https://opensource.microsoft.com/codeofconduct/faq/) o scrivere a [opencode@microsoft.com](mailto:opencode@microsoft.com) per domande aggiuntive o commenti.

# <a name="useful-resources-on-the-mixed-reality-dev-center"></a>Risorse utili per la realtà mista Dev Center

| ![Individua ](../Images/mrdevcenter/icon-discover.png) [individua](https://docs.microsoft.com/windows/mixed-reality/)| ![Progettazione ](../Images/mrdevcenter/icon-design.png) [](https://docs.microsoft.com/windows/mixed-reality/design) progettazione| ![Sviluppare ](../Images/mrdevcenter/icon-develop.png) [](https://docs.microsoft.com/windows/mixed-reality/development) lo sviluppo| ![Distribuisci) ](../Images/mrdevcenter/icon-distribute.png) [Distribuisci](https://docs.microsoft.com/windows/mixed-reality/implementing-3d-app-launchers)|
| :--------------------- | :----------------- | :------------------ | :------------------------ |
| Scopri come creare esperienze di realtà miste per HoloLens e auricolari immersivi (VR).          | Ottenere le guide di progettazione. Interfaccia utente di compilazione. Informazioni sulle interazioni e sull'input.     | Ottenere le guide di sviluppo. Scopri la tecnologia. Comprendere la scienza.       | Preparare l'app per gli utenti e valutare la possibilità di creare un'utilità di avvio 3D. |

# <a name="useful-resources-on-azure"></a>Risorse utili in Azure

| ![Ancoraggi nello spazio](../Images/mrdevcenter/icon-azurespatialanchors.png)<br> [Ancoraggi nello spazio](https://docs.microsoft.com/azure/spatial-anchors/)| ![Servizi di riconoscimento vocale](../Images/mrdevcenter/icon-azurespeechservices.png) [Servizi di riconoscimento vocale](https://docs.microsoft.com/azure/cognitive-services/speech-service/)| ![Servizi visioni Vision Services ](../Images/mrdevcenter/icon-azurevisionservices.png) [](https://docs.microsoft.com/azure/cognitive-services/computer-vision/)|
| :------------------------| :--------------------- | :---------------------- |
| Gli ancoraggi spaziali sono un servizio multipiattaforma che consente di creare esperienze di realtà miste usando oggetti che rendono permanente la loro posizione tra i dispositivi nel tempo.| Individuare e integrare nell'applicazione le funzionalità vocali di Azure, come il riconoscimento vocale, il riconoscimento del parlante o la traduzione vocale.| Identificare e analizzare il contenuto di immagini o video con i servizi di visione artificiale come il rilevamento dei volti, il riconoscimento delle emozioni o Video Indexer. |

# <a name="learn-more-about-the-mrtk-project"></a>Altre informazioni sul progetto MRTK

Il materiale di pianificazione è reperibile nel [wiki](https://github.com/Microsoft/MixedRealityToolkit-Unity/wiki) nella sezione relativa alla gestione del progetto. È sempre possibile visualizzare gli elementi su cui il team sta lavorando attivamente nel problema relativo al piano di iterazione.

# <a name="how-to-contribute"></a>Come contribuire

Scopri come [contribuire a MRTK per contribuire.](../../Contributing/CONTRIBUTING.md)

**Per informazioni dettagliate sui diversi rami usati nei repository del Toolkit di realtà mista, vedere questa [Guida di Branch](https://github.com/Microsoft/MixedRealityToolkit-Unity/wiki/Branch-Guide).**

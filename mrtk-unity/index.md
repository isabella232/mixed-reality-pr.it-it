---
title: MRTK-Unity per sviluppatori
description: Informazioni sul modello di realtà mista Toolkit per Unity.
author: polar-kev
ms.author: kesemple
ms.date: 03/03/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK
ms.openlocfilehash: ecd12cb6fbed305f1a2532f0b55a6d0441df43fa537c63d9919ae9bc91a675c0
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115204658"
---
# <a name="what-is-the-mixed-reality-toolkit"></a>Che cos'è l'Toolkit

![Mixed Reality Toolkit](features/images/Logo_MRTK_Unity_Banner.png)

<br>

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RWyXHW]

MRTK-Unity è un progetto gestito da Microsoft che fornisce un set di componenti e funzionalità che consentono di accelerare lo sviluppo di app di realtà mista multipiattaforma in Unity. Ecco alcune delle sue funzioni:

* Fornisce il **sistema di input multipiattaforma e i blocchi predefiniti per le interazioni spaziali e l'interfaccia utente.**
* Abilita **la creazione rapida di prototipi** tramite simulazione nell'editor che consente di visualizzare immediatamente le modifiche.
* Opera come un **framework estendibile che** offre agli sviluppatori la possibilità di scambiare i componenti principali.
* **Supporta un'ampia gamma di piattaforme:**

::: moniker range=">= mrtkunity-2021-05"
| Piattaforma | Dispositivi supportati |
|---|---|
| OpenXR (Unity 2020.3.8+) | Microsoft HoloLens 2 <br> Visori VR di Windows Mixed Reality |
| Windows Mixed Reality | Microsoft HoloLens <br> Microsoft HoloLens 2 <br> Visori VR di Windows Mixed Reality  |
| Oculus (Unity 2019.3 o versione più recente) | Oculus Quest |
| OpenVR |  Visori VR di Windows Mixed Reality <br> HTC Vive <br> Oculus Rift |
| Tracciamento della mano Ultraleap | Controller Ultraleap Leap Motion |
| Dispositivi mobili | iOS e Android |
::: moniker-end
::: moniker range="< mrtkunity-2021-05"
| Piattaforma | Dispositivi supportati |
|---|---|
| OpenXR (anteprima in MRTK 2.6, Unity 2020.3.8+) | Microsoft HoloLens 2 <br> Visori VR di Windows Mixed Reality |
| Windows Mixed Reality | Microsoft HoloLens <br> Microsoft HoloLens 2 <br> Visori VR di Windows Mixed Reality  |
| Oculus (Unity 2019.3 o versione più recente) | Oculus Quest |
| OpenVR |  Visori VR di Windows Mixed Reality <br> HTC Vive <br> Oculus Rift |
| Tracciamento della mano Ultraleap | Controller Ultraleap Leap Motion |
| Dispositivi mobili | iOS e Android |
::: moniker-end

## <a name="getting-started-with-mrtk"></a>Introduzione a MRTK

Se non si ha una nuova attività di sviluppo MRTK o realtà mista in Unity, è consigliabile installare ed esplorare l'applicazione di esempio MRTK Examples Hub nel dispositivo o [nell'emulatore.](/windows/mixed-reality/develop/platform-capabilities-and-apis/using-the-hololens-emulator) 

> [!div class="nextstepaction"]
> [Scaricare l'app hub esempi MRTK](running-examples-hub.md)

Dopo aver ottenuto il blocco di ciò che realtà mista e MRTK ha da offrire, installare gli strumenti necessari e seguire la serie di esercitazioni HoloLens 2 principianti.

> [!div class="nextstepaction"]
> [Installare gli strumenti](/windows/mixed-reality/develop/install-the-tools?tabs=unity)

> [!div class="nextstepaction"]
> [HoloLens 2 Serie di esercitazioni](/windows/mixed-reality/develop/unity/tutorials/mr-learning-base-02)

Vuoi vedere cosa succede sotto il cofano?
> [!div class="nextstepaction"]
> [Esplorare MRTK in GitHub](https://github.com/Microsoft/MixedRealityToolkit-Unity)

## <a name="documentation"></a>Documentazione

| [![Note sulla versione](features/images/MRTK_Icon_ReleaseNotes.png)](release-notes/mrtk-27-release-notes.md)<br/>[Note sulla versione](release-notes/mrtk-26-release-notes.md)| [![Panoramica di MRTK](features/images/MRTK_Icon_ArchitectureOverview.png)](architecture/overview.md)<br/>[Panoramica di MRTK](architecture/overview.md)|[![Informazioni di riferimento sulle API](features/images/MRTK_Icon_APIReference.png)](/dotnet/api/Microsoft.MixedReality.Toolkit)<br/>[Riferimento API](/dotnet/api/Microsoft.MixedReality.Toolkit)|
|:---|:---|:---|

## <a name="build-status"></a>Stato della compilazione

| Ramo | Stato ci | Stato della documentazione |
|---|---|---|
| `main` |[![Stato ci](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_apis/build/status/public/mrtk_CI?branchName=main)](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_build/latest?definitionId=15)|[![Stato della documentazione](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_apis/build/status/public/mrtk_docs?branchName=main)](https://dev.azure.com/aipmr/MixedRealityToolkit-Unity-CI/_build/latest?definitionId=7)

## <a name="feature-areas"></a>Aree di funzionalità

:::row:::
    :::column:::
       [![Sistema di input](features/images/MRTK_Icon_InputSystem.png)](features/input/overview.md)<br>
        **[Sistema di input](features/input/overview.md)**<br>
    :::column-end:::
    :::column:::
        [![Tracciamento manuale (HoloLens 2)](features/images/MRTK_Icon_HandTracking.png)](features/input/overview.md)<br>
        **[Tracciamento <br> manuale (HoloLens 2)](features/input/hand-tracking.md)**<br>
    :::column-end:::
    :::column:::
        [![Tracciamento oculare (HoloLens 2)](features/images/MRTK_Icon_EyeTracking.png)](features/input/eye-tracking/eye-tracking-Main.md)<br>
        **[Tracciamento <br/> oculare (HoloLens 2)](features/input/eye-tracking/eye-tracking-Main.md)**<br>
    :::column-end:::
    :::column:::
        [![Profiles](features/images/MRTK_Icon_Profiles.png)](configuration/mixed-reality-configuration-guide.md)<br>
        **[Profiles](configuration/mixed-reality-configuration-guide.md)**<br>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       [![Tracciamento manuale (Ultraleap)](features/images/MRTK_Icon_HandTracking.png)](supported-devices/leap-motion-mrtk.md)<br>
        **[Tracciamento <br/> manuale (Ultraleap)](supported-devices/leap-motion-mrtk.md)**<br>
    :::column-end:::
    :::column:::
        [![Controlli dell'interfaccia utente](features/images/MRTK_Icon_UIControls.png)](#ux-building-blocks)<br>
        **[Controlli dell'interfaccia utente](#ux-building-blocks)**<br>
    :::column-end:::
    :::column:::
        [![Risolutori](features/images/MRTK_Icon_Solver.png)](features/ux-building-blocks/solvers/solver.md)<br>
        **[Risolutori](features/ux-building-blocks/solvers/solver.md)**<br>
    :::column-end:::
    :::column:::
        [![Gestione più scene](features/images/MRTK_Icon_SceneSystem.png)](features/scene-system/scene-system-getting-started.md)<br>
        **[Gestione più <br/> scene](features/scene-system/scene-system-getting-started.md)**<br>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       [![Consapevolezza spaziale](features/images/MRTK_Icon_SpatialUnderstanding.png)](features/spatial-awareness/spatial-awareness-getting-started.md)<br>
        **[Consapevolezza <br/> spaziale](features/spatial-awareness/spatial-awareness-getting-started.md)**<br>
    :::column-end:::
    :::column:::
        [![Strumento di diagnostica](features/images/MRTK_Icon_Diagnostics.png)](features/diagnostics/diagnostics-system-getting-started.md)<br>
        **[Strumento di <br/> diagnostica](features/diagnostics/diagnostics-system-getting-started.md)**<br>
    :::column-end:::
    :::column:::
        [![Visualizzazione shader standard MRTK](features/images/MRTK_Icon_StandardShader.png)](features/rendering/mrtk-standard-shader.md?q=shader)<br>
        **[Visualizzazione di esempio dello shader standard MRTK](features/rendering/mrtk-standard-shader.md?q=shader)**<br>
    :::column-end:::
    :::column:::
        [![Dettatura & voce](features/images/MRTK_Icon_VoiceCommand.png)](features/scene-system/scene-system-getting-started.md)<br>
        **[Riconoscimento vocale](features/input/speech.md) <br/>  &  [Dettatura](features/input/dictation.md)**<br>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       [![Sistema di limiti](features/images/MRTK_Icon_Boundary.png)](features/boundary/boundary-system-getting-started.md)<br>
        **[Sistema di <br/> limiti](features/boundary/boundary-system-getting-started.md)**<br>
    :::column-end:::
    :::column:::
        [![Simulazione nell'editor](features/images/MRTK_Icon_InputSystem.png)](features/diagnostics/diagnostics-system-getting-started.md)<br>
        **[Simulazione <br/> nell'editor](features/diagnostics/diagnostics-system-getting-started.md)**<br>
    :::column-end:::
    :::column:::
        [![Funzionalità sperimentali](features/images/MRTK_Icon_Experimental.png)](contributing/experimental-features.md)<br>
        **[Funzionalità <br/> sperimentali](contributing/experimental-features.md)**<br>
    :::column-end:::
    :::column:::
    :::column-end:::
:::row-end:::

## <a name="ux-building-blocks"></a>Blocchi predefiniti dell'esperienza utente

:::row:::
    :::column:::
       [ ![ Pulsante](features/images/Button/MRTK_Button_Main.png)](features/ux-building-blocks/button.md) **[](features/ux-building-blocks/button.md)**<br>
        Controllo pulsante che supporta vari metodi di input, HoloLens 2 la mano articolata di un pulsante
    :::column-end:::
    :::column:::
        [ ![ Controllo Bounds Control](features/images/bounds-control/MRTK_BoundsControl_Main.png)](features/ux-building-blocks/bounds-control.md) **[Bounds](features/ux-building-blocks/bounds-control.md)**<br>
        Interfaccia utente standard per la modifica di oggetti nello spazio 3D
    :::column-end:::
    :::column:::
        [ ![ Manipolatore di oggetti](features/images/manipulation-handler/MRTK_Manipulation_Main.png)](features/ux-building-blocks/object-manipulator.md) **[manipolatore di oggetti](features/ux-building-blocks/object-manipulator.md)**<br>
        Script per la modifica di oggetti con una o due mani
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       [ ![ Slate](features/images/slate/MRTK_Slate_Main.png)](features/ux-building-blocks/slate.md) **[Slate](features/ux-building-blocks/slate.md)**<br>
        Piano di stile 2D che supporta lo scorrimento con input manuale articolato
    :::column-end:::
    :::column:::
        [ ![ Tastiera di sistema tastiera](features/images/system-keyboard/MRTK_SystemKeyboard_Main.png)](features/ux-building-blocks/system-keyboard.md) di **[sistema](features/ux-building-blocks/system-keyboard.md)**<br>
        Script di esempio dell'uso della tastiera di sistema in Unity
    :::column-end:::
    :::column:::
        [ ![ Interactable](features/images/interactable/InteractableExamples.png)](features/ux-building-blocks/interactable.md) **[Interactable](features/ux-building-blocks/interactable.md)**<br>
        Uno script per rendere gli oggetti intervienibili con gli stati di visualizzazione e il supporto del tema
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       [ ![ Risolutore](features/images/solver/MRTK_Solver_Main.png)](features/ux-building-blocks/solvers/solver.md) **[di risolutore](features/ux-building-blocks/solvers/solver.md)**<br>
        Vari comportamenti di posizionamento degli oggetti, ad esempio tag-along, body-lock, constant view size e surface magnetism
    :::column-end:::
    :::column:::
        [ ![ Raccolta di oggetti della](features/images/object-collection/MRTK_ObjectCollection_Main.jpg)](features/ux-building-blocks/object-collection.md) raccolta di **[oggetti](features/ux-building-blocks/object-collection.md)**<br>
        Script per il layout di una matrice di oggetti in una forma tridimensionale
    :::column-end:::
    :::column:::
        [ ![ Descrizione](features/images/tooltip/MRTK_Tooltip_Main.png)](features/ux-building-blocks/tooltip.md) **[comando](features/ux-building-blocks/tooltip.md)**<br>
        Interfaccia utente delle annotazioni con un sistema di ancoraggio/pivot flessibile, che può essere usato per l'etichettatura di controller di movimento e oggetti
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       [ ![ Dispositivo di](features/images/slider/MRTK_UX_Slider_Main.jpg)](features/ux-building-blocks/sliders.md) **[scorrimento](features/ux-building-blocks/sliders.md)**<br>
        Interfaccia utente del dispositivo di scorrimento per la regolazione dei valori che supportano l'interazione di rilevamento diretto della mano
    :::column-end:::
    :::column:::
        [ ![ MrTK Standard Shader](features/images/mrtk-standard-shader/MRTK_StandardShader.jpg)](features/rendering/mrtk-standard-shader.md) **[MRTK Standard Shader](features/rendering/mrtk-standard-shader.md)**<br>
        Lo shader Standard di MRTK supporta vari elementi Fluent di progettazione con prestazioni elevate
    :::column-end:::
    :::column:::
        [ ![ Menu a mano](features/images/solver/MRTK_UX_HandMenu.png)](features/ux-building-blocks/hand-menu.md) a **[mano](features/ux-building-blocks/hand-menu.md)**<br>
        Interfaccia utente bloccata a mano per l'accesso rapido con il risolutore di vincoli della mano
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       [ ![ Barra dell'app Barra](features/images/app-bar/MRTK_AppBar_Main.png)](features/ux-building-blocks/app-bar.md) **[delle app](features/ux-building-blocks/app-bar.md)**<br>
        Interfaccia utente per l'attivazione manuale del controllo Bounds
    :::column-end:::
    :::column:::
        [ ![ Puntatori](features/images/Pointers/MRTK_Pointer_Main.png)](features/input/pointers.md) **[puntatori](features/input/pointers.md)**<br>
        Informazioni sui vari tipi di puntatori
    :::column-end:::
    :::column:::
        [ ![ Visualizzazione della punta delle dita](features/images/fingertip/MRTK_FingertipVisualization_Main.png)](features/ux-building-blocks/fingertip-visualization.md) **[Visualizzazione punta del dito](features/ux-building-blocks/fingertip-visualization.md)**<br>
        Convenienza visiva sulla punta delle dita che migliora la confidenza per l'interazione diretta
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       Near Menu Near Menu Near Menu [ ![ (Vicino al](features/images/near-menu/MRTK_UX_NearMenu.png)](features/ux-building-blocks/near-menu.md) **[menu vicino)](features/ux-building-blocks/near-menu.md)**<br>
        Interfaccia utente del menu mobile per le interazioni vicine
    :::column-end:::
    :::column:::
        [ ![ Visualizzazione di consapevolezza spaziale Introduzione](features/images/spatial-awareness/MRTK_SpatialAwareness_Main.png)](features/spatial-awareness/spatial-awareness-getting-started.md) alla **[consapevolezza spaziale](features/spatial-awareness/spatial-awareness-getting-started.md)**<br>
        Fare in modo che gli oggetti olografici interagiscano con gli ambienti fisici
    :::column-end:::
    :::column:::
        [ ![ Comando vocale Comando](features/images/input/MRTK_Input_Speech.png)](features/input/speech.md) **[vocale](features/input/speech.md)**<br>
        Script ed esempi per l'integrazione dell'input vocale
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       [ ![ Indicatore di stato indicatore](features/images/progress-indicator/MRTK_ProgressIndicator_Main.png)](features/ux-building-blocks/progress-indicator.md) di **[stato](features/ux-building-blocks/progress-indicator.md)**<br>
        Indicatore visivo per la comunicazione del processo o dell'operazione dei dati
    :::column-end:::
    :::column:::
        [ ![ Finestra di](features/images/Dialog/MRTK_UX_Dialog_Main.png)](features/ux-building-blocks/dialog.md) **[dialogo](features/ux-building-blocks/dialog.md)**<br>
        Interfaccia utente per la richiesta di conferma o conferma dell'utente
    :::column-end:::
    :::column:::
        [ ![ Hand Coach](features/images/hand-coach/MRTK_UX_HandCoach_Main.jpg)](features/ux-building-blocks/hand-coach.md) **[Hand Coach](features/ux-building-blocks/hand-coach.md)**<br>
        Componente che consente di guidare l'utente quando il movimento non è stato insegnato
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       [ ![ Hand Physics Service](features/images/hand-physics/MRTK_UX_HandPhysics_Main.jpg)](features/extensions/hand-physics-service.md) Hand Physics Service **[[Sperimentale]](features/extensions/hand-physics-service.md)**<br>
        Il servizio di fisica della mano consente eventi rigidi di collisione del corpo e interazioni con mani articolate
    :::column-end:::
    :::column:::
        [ ![ Raccolta scrolling collection](features/images/scrolling-collection/ScrollingCollection_Main.jpg)](features/ux-building-blocks/scrolling-object-collection.md) **[scrolling](features/ux-building-blocks/scrolling-object-collection.md)**<br>
        Raccolta di oggetti che scorre in modo nativo gli oggetti 3D
    :::column-end:::
    :::column:::
        [ ![ Dock](features/images/Dock/MRTK_UX_Dock_Main.png)](features/experimental/dock.md) **[Dock [Sperimentale]](features/experimental/dock.md)**<br>
        Dock consente agli oggetti di essere spostati in e fuori da posizioni predeterminate
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       [ ![ Tracciamento oculare: Tracciamento oculare](features/images/eye-tracking/mrtk_et_targetselect.png)](features/input/eye-tracking/eye-tracking-target-selection.md) **[selezione destinazione: Selezione destinazione](features/input/eye-tracking/eye-tracking-target-selection.md)**<br>
        Combinare gli occhi, la voce e l'input delle mani per selezionare rapidamente e senza sforzo gli ologrammi nella scena
    :::column-end:::
    :::column:::
        [ ![ Tracciamento oculare: Tracciamento](features/images/eye-tracking/mrtk_et_navigation.png)](features/input/eye-tracking/eye-tracking-navigation.md) **[oculare di navigazione: Navigazione](features/input/eye-tracking/eye-tracking-navigation.md)**<br>
        Informazioni su come scorrere automaticamente il testo o ingrandire fluentemente il contenuto con stato attivo in base a ciò che si sta esaminando
    :::column-end:::
    :::column:::
        [ ![ Tracciamento oculare: Tracciamento oculare](features/images/eye-tracking/mrtk_et_heatmaps.png)](features/example-scenes/eye-tracking-examples-overview.md#visualization-of-visual-attention) **[mappa termica: Mappa termica](features/example-scenes/eye-tracking-examples-overview.md#visualization-of-visual-attention)**<br>
        Esempi per la registrazione, il caricamento e la visualizzazione di ciò che gli utenti hanno visto nell'app
    :::column-end:::
:::row-end:::

## <a name="tools"></a>Strumenti

|  [ ![ Ottimizzare la finestra](features/images/MRTK_Icon_OptimizeWindow.png)](features/tools/optimize-window.md) di [Ottimizzazione finestra](features/tools/optimize-window.md) | [ ![ Finestra Dipendenze finestra](features/images/MRTK_Icon_DependencyWindow.png)](features/tools/dependency-window.md) [dipendenze](features/tools/dependency-window.md) | [ ![ Finestra di compilazione della](features/images/MRTK_Icon_BuildWindow.png)](features/tools/build-window.md) finestra di [compilazione](features/tools/build-window.md) | [ ![ Registrazione di input](features/images/MRTK_Icon_InputRecording.png)](features/input-simulation/input-animation-recording.md) Registrazione [input](features/input-simulation/input-animation-recording.md) |
|:--- | :--- | :--- | :--- |
| Automatizzare la configurazione dei progetti di realtà mista per le ottimizzazioni delle prestazioni | Analizzare le dipendenze tra asset e identificare gli asset inutilizzati |  Configurare ed eseguire un processo di compilazione end-to-end per applicazioni di realtà mista | Registrare e riprodurre i dati di spostamento della testa e rilevamento della mano nell'editor |

## <a name="example-scenes"></a>Scene di esempio

MRTK fornisce scene di esempio che illustrano come usare le funzionalità di MRTK. Le scene di esempio sono disponibili nella cartella Assets/MRTK/Examples/Demos. Leggere la [pagina Scene di esempio](running-example-scenes.md) per informazioni su come acquisire ed eseguire scene di esempio. [La scena Esempi di interazione manuale](features/example-scenes/hand-interaction-examples.md) è un ottimo punto per iniziare a sperimentare i blocchi predefiniti di MRTK per le interazioni e l'interfaccia utente.

[![Scena di esempio 2](features/images/MRTK_Examples.png)](features/example-scenes/hand-interaction-examples.md)

## <a name="mrtk-examples-hub"></a>Hub degli esempi MRTK

Con l'hub esempi MRTK è possibile provare varie scene di esempio in MRTK senza compilare e distribuire ogni scena.
È possibile scaricare pacchetti di app predefiniti per HoloLens(x86), HoloLens 2(ARM) e visori immersivi Windows Mixed Reality (x64) selezionando il pacchetto "Esempi di realtà mista Toolkit" nello strumento di funzionalità [MR.](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool) Assicurarsi di usare il Windows Portale di dispositivi per installare le app in HoloLens [(prima generazione).](/hololens/hololens-install-apps#use-the-windows-device-portal-to-install-apps-on-hololens) In HoloLens 2 è possibile scaricare e installare [l'hub esempi MRTK tramite l'app Microsoft Store .](https://www.microsoft.com/p/mrtk-examples-hub/9mv8c39l2sj4)

Per [informazioni dettagliate sulla](features/example-scenes/example-hub.md) creazione di un hub a più scene con il sistema di scena e il servizio di transizione della scena di MRTK, vedere la pagina README dell'hub degli esempi.

[![Hub scena di esempio](features/images/MRTK_ExamplesHub.png)](features/example-scenes/hand-interaction-examples.md)

## <a name="sample-apps-made-with-mrtk"></a>App di esempio effettuate con MRTK

| [![Tavola periodica degli elementi](features/images/MRDL_PeriodicTable.jpg)](https://medium.com/@dongyoonpark/bringing-the-periodic-table-of-the-elements-app-to-hololens-2-with-mrtk-v2-a6e3d8362158)| [![Galaxy Explorer](features/images/MRTK_GalaxyExplorer.jpg)](/windows/mixed-reality/galaxy-explorer-update)| [![App di esempio Surfaces](features/images/MRDL_Surfaces.jpg)](/windows/mixed-reality/sampleapp-surfaces)|
|:--- | :--- | :--- |
| [La tabella periodica degli](https://github.com/Microsoft/MRDL_Unity_PeriodicTable) elementi è un'app di esempio open source che illustra come usare il sistema di input e i blocchi predefiniti di MRTK per creare un'esperienza di app per visori HoloLens e immersive. Leggere la storia di porting: Portare la tabella [periodica dell'app Elements HoloLens 2 con MRTK v2](https://medium.com/@dongyoonpark/bringing-the-periodic-table-of-the-elements-app-to-hololens-2-with-mrtk-v2-a6e3d8362158) |[Galaxy Explorer](https://github.com/Microsoft/GalaxyExplorer) è un'app di esempio open source originariamente sviluppata nel marzo 2016 come parte della campagna HoloLens 'Condividi la tua idea'. Galaxy Explorer è stato aggiornato con nuove funzionalità per HoloLens 2, usando MRTK v2. Leggere la storia: [The Making of Galaxy Explorer for HoloLens 2](/windows/mixed-reality/galaxy-explorer-update) |[Surfaces](https://github.com/microsoft/MRDL_Unity_Surfaces) è un'app di esempio open source per HoloLens 2 che esplora come creare una emozione tattile con visual, audio e tracciamento manuale completamente articolato. Per informazioni dettagliate sulla progettazione e sullo sviluppo, vedere la sessione Microsoft MR Dev Days [Learnings dell'app Surfaces.](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Learnings-from-the-MR-Surfaces-App) |

## <a name="session-videos-from-mixed-reality-dev-days-2020"></a>Video di sessione di Mixed Reality Dev Days 2020

| [![MRDevDays 1](features/images/MRDevDays_Session1.png)](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Intro-to-MRTK-Unity)| [![MRDevDays 3](features/images/MRDevDays_Session2.png)](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/MRTKs-UX-Building-Blocks)| [![MRDevDays 2](features/images/MRDevDays_Session3.png)](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/MRTK-Performance-and-Shaders)|
|:--- | :--- | :--- |
| Esercitazione su come creare una semplice app MRTK dall'inizio alla fine. Informazioni sui concetti di interazione e sulle funzionalità multipiattaforma di MRTK. | Approfondimenti sui blocchi predefiniti dell'esperienza utente di MRTK che consentono di creare esperienze di realtà mista eccezionali. | Introduzione agli strumenti per le prestazioni, sia in MRTK che esterna, nonché una panoramica dello shader STANDARD MRTK. |

Vedere [Mixed Reality Dev Days](/windows/mixed-reality/mr-dev-days-sessions) per esplorare altri video di sessione.

## <a name="engage-with-the-community"></a>Interagire con la community

* Partecipare alla conversazione su MRTK in [Slack.](https://holodevelopers.slack.com/) È possibile partecipare alla community di Slack tramite il [mittente dell'invito automatico](https://holodevelopersslack.azurewebsites.net/).

* Porre domande sull'uso di MRTK [Stack Overflow](https://stackoverflow.com/questions/tagged/mrtk) usando il tag **MRTK.**

* Cercare i [problemi noti o](https://github.com/Microsoft/MixedRealityToolkit-Unity/issues) creare un nuovo problema [se](https://github.com/Microsoft/MixedRealityToolkit-Unity/issues) si verificano problemi nel codice MRTK.

* Per domande sui contributi a MRTK, visitare il canale [mixed-reality-toolkit](https://holodevelopers.slack.com/messages/C2H4HT858) su Slack.

Questo progetto ha adottato il [Codice di comportamento di Microsoft per l'open source](https://opensource.microsoft.com/codeofconduct/).
Per altre informazioni, vedere le [Domande frequenti sul codice di comportamento](https://opensource.microsoft.com/codeofconduct/faq/) o scrivere a [opencode@microsoft.com](mailto:opencode@microsoft.com) per domande aggiuntive o commenti.

## <a name="useful-resources-on-the-mixed-reality-dev-center"></a>Risorse utili sul modello di realtà mista Dev Center

| ![Individuazione ](features/images/mrdevcenter/icon-discover.png) [individuazione](/windows/mixed-reality/)| ![Progettazione ](features/images/mrdevcenter/icon-design.png) [](/windows/mixed-reality/design)| ![Sviluppare ](features/images/mrdevcenter/icon-develop.png) [lo sviluppo](/windows/mixed-reality/development)| ![Distribuisci) ](features/images/mrdevcenter/icon-distribute.png) [Distribuisci](/windows/mixed-reality/implementing-3d-app-launchers)|
| :--------------------- | :----------------- | :------------------ | :------------------------ |
| Informazioni su come creare esperienze di realtà mista per HoloLens visori VR immersive.          | Ottenere le guide di progettazione. Compilare l'interfaccia utente. Informazioni sulle interazioni e sull'input.     | Ottenere le guide di sviluppo. Informazioni sulla tecnologia. Comprendere la scienza.       | Preparare l'app per gli utenti e valutare la possibilità di creare un'utilità di avvio 3D. |

## <a name="useful-resources-on-azure"></a>Risorse utili in Azure

| ![Ancoraggi nello spazio](features/images/mrdevcenter/icon-azurespatialanchors.png)<br> [Ancoraggi nello spazio](/azure/spatial-anchors/)| ![Servizi Voce di ](features/images/mrdevcenter/icon-azurespeechservices.png) [Servizi di riconoscimento vocale](/azure/cognitive-services/speech-service/)| ![Servizi visione ](features/images/mrdevcenter/icon-azurevisionservices.png) [visione](/azure/cognitive-services/computer-vision/)|
| :------------------------| :--------------------- | :---------------------- |
| Ancoraggi nello spaziale è un servizio multipiattaforma che consente di creare esperienze di realtà mista usando oggetti che mantendono la posizione tra i dispositivi nel corso del tempo.| Individuare e integrare nell'applicazione le funzionalità vocali di Azure, come il riconoscimento vocale, il riconoscimento del parlante o la traduzione vocale.| Identificare e analizzare il contenuto di immagini o video con i servizi di visione artificiale come il rilevamento dei volti, il riconoscimento delle emozioni o Video Indexer. |

## <a name="how-to-contribute"></a>Come contribuire

Per informazioni su come contribuire a MRTK, vedere [Contribuire a](contributing/contributing.md).

## <a name="getting-help"></a>Guida

Se si verificano problemi causati da MRTK o in caso di domande su come eseguire un'operazione, sono disponibili alcune risorse utili:

* Per i report sui bug, [segnala un](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/new/choose) problema nel GitHub del bug.
* Per domande, contattare [StackOverflow](https://stackoverflow.com/questions/tagged/mrtk) o il canale [mixed-reality-toolkit](https://holodevelopers.slack.com/messages/C2H4HT858) su Slack. È possibile partecipare alla community di Slack tramite il [mittente dell'invito automatico](https://holodevelopersslack.azurewebsites.net/).
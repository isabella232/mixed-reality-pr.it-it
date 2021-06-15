---
title: MRTK-Unity developer
description: Informazioni su Mixed Reality Toolkit per Unity.
author: polar-kev
ms.author: kesemple
ms.date: 03/03/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK
ms.openlocfilehash: bf0a97547aa482e5c206916faea2b2de41d28a7b
ms.sourcegitcommit: 65f58055c831d58a3d38fb333f09b323ee2ac9b7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/14/2021
ms.locfileid: "112064146"
---
# <a name="what-is-the-mixed-reality-toolkit"></a>Informazioni su Mixed Reality Toolkit

![Mixed Reality Toolkit](features/images/Logo_MRTK_Unity_Banner.png)

<br>

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RWyXHW]

MRTK-Unity è un progetto gestito da Microsoft che fornisce un set di componenti e funzionalità che consentono di accelerare lo sviluppo di app di realtà mista multipiattaforma in Unity. Ecco alcune delle sue funzioni:

* Fornisce il **sistema di input multipiattaforma e i blocchi predefiniti per le interazioni spaziali e l'interfaccia utente.**
* Abilita **la creazione rapida di prototipi** tramite simulazione nell'editor che consente di visualizzare immediatamente le modifiche.
* Opera come un **framework estendibile che** offre agli sviluppatori la possibilità di sostituire i componenti di base.
* **Supporta un'ampia gamma di piattaforme:**

::: moniker range=">= mrtkunity-2021-05"
| Piattaforma | Dispositivi supportati |
|---|---|
| OpenXR (Unity 2020.3.8+) | Microsoft HoloLens 2 <br> Visori VR di Windows Mixed Reality |
| Windows Mixed Reality | Microsoft HoloLens <br> Microsoft HoloLens 2 <br> Visori VR di Windows Mixed Reality  |
| Oculus (Unity 2019.3 o versione più recente) | Oculus Quest |
| OpenVR |  Visori VR di Windows Mixed Reality <br> PIÙ VIVE Vive <br> Oculus Rift |
| Tracciamento della mano Ultraleap | Controller Ultraleap Leap Motion |
| Dispositivi mobili | iOS e Android |
::: moniker-end
::: moniker range="< mrtkunity-2021-05"
| Piattaforma | Dispositivi supportati |
|---|---|
| OpenXR (anteprima in MRTK 2.6, Unity 2020.3.8+) | Microsoft HoloLens 2 <br> Visori VR di Windows Mixed Reality |
| Windows Mixed Reality | Microsoft HoloLens <br> Microsoft HoloLens 2 <br> Visori VR di Windows Mixed Reality  |
| Oculus (Unity 2019.3 o versione più recente) | Oculus Quest |
| OpenVR |  Visori VR di Windows Mixed Reality <br> PIÙ VIVE Vive <br> Oculus Rift |
| Tracciamento della mano Ultraleap | Controller Ultraleap Leap Motion |
| Dispositivi mobili | iOS e Android |
::: moniker-end

## <a name="getting-started-with-mrtk"></a>Introduzione a MRTK

Se non si ha disatteso lo sviluppo di MRTK o realtà mista in Unity, è consigliabile installare ed esplorare l'applicazione di esempio MRTK Examples Hub nel dispositivo o [nell'emulatore.](https://docs.microsoft.com/windows/mixed-reality/develop/platform-capabilities-and-apis/using-the-hololens-emulator) 

> [!div class="nextstepaction"]
> [Scaricare l'app hub degli esempi di MRTK](running-examples-hub.md)

Dopo aver ottenuto il blocco delle offerte offerte da Realtà mista e MRTK, installare gli strumenti necessari e seguire la serie di esercitazioni HoloLens 2 per principianti.

> [!div class="nextstepaction"]
> [Installare gli strumenti](/windows/mixed-reality/develop/install-the-tools?tabs=unity)

> [!div class="nextstepaction"]
> [HoloLens 2 serie di esercitazioni](/windows/mixed-reality/develop/unity/tutorials/mr-learning-base-02)

Si vuole vedere cosa succede in un secondo tempo?
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
        [![Tracciamento delle mani (HoloLens 2)](features/images/MRTK_Icon_HandTracking.png)](features/input/overview.md)<br>
        **[Tracciamento <br> delle mani (HoloLens 2)](features/input/hand-tracking.md)**<br>
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
       [![Tracciamento delle mani (Ultraleap)](features/images/MRTK_Icon_HandTracking.png)](supported-devices/leap-motion-mrtk.md)<br>
        **[Tracciamento <br/> delle mani (Ultraleap)](supported-devices/leap-motion-mrtk.md)**<br>
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
       [ ![ Pulsante](features/images/Button/MRTK_Button_Main.png)](features/ux-building-blocks/button.md) **[Pulsante](features/ux-building-blocks/button.md)**<br>
        Controllo pulsante che supporta vari metodi di input, inclusa HoloLens 2 mano articolata del controllo
    :::column-end:::
    :::column:::
        [ ![ Controllo Limiti del](features/images/bounds-control/MRTK_BoundsControl_Main.png)](features/ux-building-blocks/bounds-control.md) controllo **[Bounds](features/ux-building-blocks/bounds-control.md)**<br>
        Interfaccia utente standard per la modifica di oggetti nello spazio 3D
    :::column-end:::
    :::column:::
        [ ![ Manipolatore di oggetti](features/images/manipulation-handler/MRTK_Manipulation_Main.png)](features/ux-building-blocks/object-manipulator.md) **[Manipolatore di oggetti](features/ux-building-blocks/object-manipulator.md)**<br>
        Script per la manipolazione di oggetti con una o due mani
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       [ ![ Slate](features/images/slate/MRTK_Slate_Main.png)](features/ux-building-blocks/slate.md) **[Slate](features/ux-building-blocks/slate.md)**<br>
        Piano di stile 2D che supporta lo scorrimento con input con mano articolata
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
       [ ![ Risolutore](features/images/solver/MRTK_Solver_Main.png)](features/ux-building-blocks/solvers/solver.md) **[](features/ux-building-blocks/solvers/solver.md)**<br>
        Vari comportamenti di posizionamento degli oggetti, ad esempio tag lungo, blocco del corpo, dimensioni della visualizzazione costanti e magnetismo della superficie
    :::column-end:::
    :::column:::
        [ ![ Raccolta di oggetti Raccolta](features/images/object-collection/MRTK_ObjectCollection_Main.jpg)](features/ux-building-blocks/object-collection.md) **[oggetti](features/ux-building-blocks/object-collection.md)**<br>
        Script per il layout di una matrice di oggetti in una forma tridimensionale
    :::column-end:::
    :::column:::
        [ ![ Descrizione comando](features/images/tooltip/MRTK_Tooltip_Main.png)](features/ux-building-blocks/tooltip.md) **[](features/ux-building-blocks/tooltip.md)**<br>
        Interfaccia utente di annotazione con un sistema di ancoraggio/pivot flessibile, che può essere usato per l'etichettatura di controller del movimento e oggetti
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       [ ![ Dispositivo di](features/images/slider/MRTK_UX_Slider_Main.jpg)](features/ux-building-blocks/sliders.md) **[scorrimento](features/ux-building-blocks/sliders.md)**<br>
        Interfaccia utente del dispositivo di scorrimento per la modifica dei valori che supportano l'interazione con il tracciamento diretto della mano
    :::column-end:::
    :::column:::
        Shader [ ![ MRTK Standard](features/images/mrtk-standard-shader/MRTK_StandardShader.jpg)](features/rendering/mrtk-standard-shader.md) **[MRTK Standard Shader](features/rendering/mrtk-standard-shader.md)**<br>
        Lo shader Standard di MRTK supporta vari elementi di progettazione Fluent con prestazioni
    :::column-end:::
    :::column:::
        [ ![ Menu a mano](features/images/solver/MRTK_UX_HandMenu.png)](features/ux-building-blocks/hand-menu.md) Menu **[mano](features/ux-building-blocks/hand-menu.md)**<br>
        Interfaccia utente bloccata a mano per l'accesso rapido con il risolutore di vincoli di mano
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       [ ![ Barra dell'app barra](features/images/app-bar/MRTK_AppBar_Main.png)](features/ux-building-blocks/app-bar.md) **[dell'app](features/ux-building-blocks/app-bar.md)**<br>
        Interfaccia utente per l'attivazione manuale del controllo Bounds
    :::column-end:::
    :::column:::
        [ ![ Puntatori](features/images/Pointers/MRTK_Pointer_Main.png)](features/input/pointers.md) **[](features/input/pointers.md)**<br>
        Informazioni sui vari tipi di puntatori
    :::column-end:::
    :::column:::
        [ ![ Visualizzazione punta del dito](features/images/fingertip/MRTK_FingertipVisualization_Main.png)](features/ux-building-blocks/fingertip-visualization.md) **[Visualizzazione punta del dito](features/ux-building-blocks/fingertip-visualization.md)**<br>
        L'affordance visivo sulla punta del dito che migliora la confidenza per l'interazione diretta
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       [ ![ Near Menu](features/images/near-menu/MRTK_UX_NearMenu.png)](features/ux-building-blocks/near-menu.md) Near **[Menu (Menu vicino al menu vicino)](features/ux-building-blocks/near-menu.md)**<br>
        Interfaccia utente a menu mobile per le interazioni da vicino
    :::column-end:::
    :::column:::
        [ ![ Spatial Awareness Getting Started](features/images/spatial-awareness/MRTK_SpatialAwareness_Main.png)](features/spatial-awareness/spatial-awareness-getting-started.md) Spatial Awareness View **[(Introduzione alla consapevolezza spaziale)](features/spatial-awareness/spatial-awareness-getting-started.md)**<br>
        Fare in modo che gli oggetti olografici interagiscano con gli ambienti fisici
    :::column-end:::
    :::column:::
        [ ![ Comando vocale](features/images/input/MRTK_Input_Speech.png)](features/input/speech.md) **[Comando vocale](features/input/speech.md)**<br>
        Script ed esempi per l'integrazione dell'input vocale
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       [ ![ Indicatore di stato Indicatore](features/images/progress-indicator/MRTK_ProgressIndicator_Main.png)](features/ux-building-blocks/progress-indicator.md) di **[stato](features/ux-building-blocks/progress-indicator.md)**<br>
        Indicatore visivo per la comunicazione del processo o dell'operazione dei dati
    :::column-end:::
    :::column:::
        [ ![ Finestra di](features/images/Dialog/MRTK_UX_Dialog_Main.png)](features/ux-building-blocks/dialog.md) **[dialogo](features/ux-building-blocks/dialog.md)**<br>
        Interfaccia utente per chiedere conferma o acknowledgement dell'utente
    :::column-end:::
    :::column:::
        [ ![ Hand Hand Hand](features/images/hand-coach/MRTK_UX_HandCoach_Main.jpg)](features/ux-building-blocks/hand-coach.md) **[Hand](features/ux-building-blocks/hand-coach.md)**<br>
        Componente che consente di guidare l'utente quando il movimento non è stato insegnato
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       [ ![ Hand Physics Service](features/images/hand-physics/MRTK_UX_HandPhysics_Main.jpg)](features/experimental/hand-physics-service.md) Hand Physics Service **[[Experimental]](features/experimental/hand-physics-service.md)**<br>
        Il servizio di fisica della mano consente eventi rigidi di collisione del corpo e interazioni con le mani articolate
    :::column-end:::
    :::column:::
        [ ![ Raccolta Scrolling Collection](features/images/scrolling-collection/ScrollingCollection_Main.jpg)](features/ux-building-blocks/scrolling-object-collection.md) **[Scrolling](features/ux-building-blocks/scrolling-object-collection.md)**<br>
        Raccolta di oggetti che scorre in modo nativo gli oggetti 3D
    :::column-end:::
    :::column:::
        [ ![ Dock](features/images/Dock/MRTK_UX_Dock_Main.png)](features/experimental/dock.md) **[[Sperimentale]](features/experimental/dock.md)**<br>
        Dock consente di spostare gli oggetti da e verso posizioni predeterminate
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       [ ![ Tracciamento oculare: Tracciamento](features/images/eye-tracking/mrtk_et_targetselect.png)](features/input/eye-tracking/eye-tracking-target-selection.md) **[oculare della selezione della destinazione: selezione della destinazione](features/input/eye-tracking/eye-tracking-target-selection.md)**<br>
        Combina gli occhi, la voce e l'input delle mani per selezionare in modo semplice e rapido gli ologrammi nella scena
    :::column-end:::
    :::column:::
        [ ![ Tracciamento oculare: navigazione](features/images/eye-tracking/mrtk_et_navigation.png)](features/input/eye-tracking/eye-tracking-navigation.md) **[tracciamento oculare: navigazione](features/input/eye-tracking/eye-tracking-navigation.md)**<br>
        Informazioni su come scorrere automaticamente il testo o ingrandire fluently il contenuto con stato attivo in base a ciò che si sta esaminando
    :::column-end:::
    :::column:::
        [ ![ Tracciamento oculare: Tracciamento](features/images/eye-tracking/mrtk_et_heatmaps.png)](features/example-scenes/eye-tracking-examples-overview.md#visualization-of-visual-attention) **[oculare mappa termica: mappa termica](features/example-scenes/eye-tracking-examples-overview.md#visualization-of-visual-attention)**<br>
        Esempi per la registrazione, il caricamento e la visualizzazione di ciò che gli utenti hanno cercato nell'app
    :::column-end:::
:::row-end:::

## <a name="tools"></a>Strumenti

|  [ ![ Ottimizza finestra Ottimizza](features/images/MRTK_Icon_OptimizeWindow.png)](features/tools/optimize-window.md) [finestra](features/tools/optimize-window.md) | [ ![ Finestra Dipendenze finestra](features/images/MRTK_Icon_DependencyWindow.png)](features/tools/dependency-window.md) [dipendenze](features/tools/dependency-window.md) | [ ![ Finestra di compilazione della](features/images/MRTK_Icon_BuildWindow.png)](features/tools/build-window.md) finestra di [compilazione](features/tools/build-window.md) | [ ![ Registrazione di input](features/images/MRTK_Icon_InputRecording.png)](features/input-simulation/input-animation-recording.md) Registrazione di [input](features/input-simulation/input-animation-recording.md) |
|:--- | :--- | :--- | :--- |
| Automatizzare la configurazione dei progetti di realtà mista per ottimizzare le prestazioni | Analizzare le dipendenze tra asset e identificare gli asset inutilizzati |  Configurare ed eseguire un processo di compilazione end-to-end per le applicazioni di realtà mista | Registrare e riprodurre i dati relativi al movimento della testa e al tracciamento della mano nell'editor |

## <a name="example-scenes"></a>Scene di esempio

MRTK fornisce scene di esempio che illustrano come usare le funzionalità di MRTK. È possibile trovare le scene di esempio nella cartella Assets/MRTK/Examples/Demos. Leggere la [pagina Scene di](running-example-scenes.md) esempio per informazioni su come acquisire ed eseguire scene di esempio. [La scena Hand Interaction Examples (Esempi](features/example-scenes/hand-interaction-examples.md) di interazione manuale) è un ottimo punto di partenza per iniziare a sperimentare i blocchi predefiniti di MRTK per le interazioni e l'interfaccia utente.

[![Scena di esempio 2](features/images/MRTK_Examples.png)](features/example-scenes/hand-interaction-examples.md)

## <a name="mrtk-examples-hub"></a>Hub degli esempi di MRTK

Con l'hub degli esempi di MRTK è possibile provare varie scene di esempio in MRTK senza compilare e distribuire ogni scena.
Puoi scaricare pacchetti di app predefiniti per HoloLens(x86), HoloLens 2 (ARM) e visori VR immersive (x64) di Windows Mixed Reality selezionando il pacchetto "Mixed Reality Toolkit Examples" (Esempi di Mixed Reality Toolkit) nello strumento per le funzionalità [MR.](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool) Assicurarsi di usare [il Portale di dispositivi di Windows per installare le app in HoloLens (prima generazione).](/hololens/hololens-install-apps#use-the-windows-device-portal-to-install-apps-on-hololens) In HoloLens 2 possibile scaricare e installare [l'hub di esempi mrtk tramite l'app Microsoft Store](https://www.microsoft.com/p/mrtk-examples-hub/9mv8c39l2sj4).

Per informazioni dettagliate sulla creazione di un hub a più scene con il sistema di scena e il servizio di transizione della scena di MRTK, vedere la pagina [Examples Hub README](features/example-scenes/example-hub.md) (File LEGGIMI dell'hub di esempi).

[![Hub scena di esempio](features/images/MRTK_ExamplesHub.png)](features/example-scenes/hand-interaction-examples.md)

## <a name="sample-apps-made-with-mrtk"></a>App di esempio effettuate con MRTK

| [![Tavola periodica degli elementi](features/images/MRDL_PeriodicTable.jpg)](https://medium.com/@dongyoonpark/bringing-the-periodic-table-of-the-elements-app-to-hololens-2-with-mrtk-v2-a6e3d8362158)| [![Galaxy Explorer](features/images/MRTK_GalaxyExplorer.jpg)](/windows/mixed-reality/galaxy-explorer-update)| [![App di esempio Surfaces](features/images/MRDL_Surfaces.jpg)](/windows/mixed-reality/sampleapp-surfaces)|
|:--- | :--- | :--- |
| [La tabella](https://github.com/Microsoft/MRDL_Unity_PeriodicTable) periodica degli elementi è un'app di esempio open source che illustra come usare il sistema di input e i blocchi predefiniti di MRTK per creare un'esperienza app per HoloLens e visori VR immersive. Leggere la storia della portabilità: Portare la tabella [periodica dell'app Elements HoloLens 2 con MRTK v2](https://medium.com/@dongyoonpark/bringing-the-periodic-table-of-the-elements-app-to-hololens-2-with-mrtk-v2-a6e3d8362158) |[Galaxy Explorer](https://github.com/Microsoft/GalaxyExplorer) è un'app di esempio open source sviluppata originariamente nel mese di marzo 2016 come parte della campagna "Condividi la tua idea" di HoloLens. Galaxy Explorer è stato aggiornato con nuove funzionalità per HoloLens 2, usando MRTK v2. Leggere la storia: [The Making of Galaxy Explorer for HoloLens 2](/windows/mixed-reality/galaxy-explorer-update) |[Surfaces](https://github.com/microsoft/MRDL_Unity_Surfaces) è un'app di esempio open source per HoloLens 2 che illustra come è possibile creare un tattile con elementi visivi, audio e tracciamento delle mani completamente articolati. Per informazioni dettagliate sulla progettazione e lo sviluppo, vedere la sessione Microsoft MR Dev Days [Learnings from the Surfaces app](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Learnings-from-the-MR-Surfaces-App) (Apprendimento della sessione di Microsoft MR Dev Days dall'app Surfaces). |

## <a name="session-videos-from-mixed-reality-dev-days-2020"></a>Video di sessione di Mixed Reality Dev Days 2020

| [![MRDevDays 1](features/images/MRDevDays_Session1.png)](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Intro-to-MRTK-Unity)| [![MRDevDays 3](features/images/MRDevDays_Session2.png)](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/MRTKs-UX-Building-Blocks)| [![MRDevDays 2](features/images/MRDevDays_Session3.png)](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/MRTK-Performance-and-Shaders)|
|:--- | :--- | :--- |
| Esercitazione su come creare una semplice app MRTK dall'inizio alla fine. Informazioni sui concetti di interazione e sulle funzionalità multipiattaforma di MRTK. | Approfondimento sui blocchi predefiniti dell'esperienza utente di MRTK che consentono di creare esperienze di realtà mista di qualità. | Introduzione agli strumenti per le prestazioni, sia in MRTK che esterni, nonché una panoramica dello shader standard MRTK. |

Vedi [Mixed Reality Dev Days per](/windows/mixed-reality/mr-dev-days-sessions) esplorare altri video di sessione.

## <a name="engage-with-the-community"></a>Interagire con la community

* Partecipare alla conversazione su MRTK in [Slack.](https://holodevelopers.slack.com/) È possibile partecipare alla community di Slack tramite il [mittente dell'invito automatico.](https://holodevelopersslack.azurewebsites.net/)

* Porre domande sull'uso di MRTK [Stack Overflow](https://stackoverflow.com/questions/tagged/mrtk) il tag **MRTK.**

* Cercare i [problemi noti o](https://github.com/Microsoft/MixedRealityToolkit-Unity/issues) determinare un nuovo [problema](https://github.com/Microsoft/MixedRealityToolkit-Unity/issues) se si verificano problemi nel codice MRTK.

* Per domande sul contributo a MRTK, passare al canale [mixed-reality-toolkit](https://holodevelopers.slack.com/messages/C2H4HT858) su Slack.

Questo progetto ha adottato il [Codice di comportamento di Microsoft per l'open source](https://opensource.microsoft.com/codeofconduct/).
Per altre informazioni, vedere le [Domande frequenti sul codice di comportamento](https://opensource.microsoft.com/codeofconduct/faq/) o scrivere a [opencode@microsoft.com](mailto:opencode@microsoft.com) per domande aggiuntive o commenti.

## <a name="useful-resources-on-the-mixed-reality-dev-center"></a>Risorse utili per l'ambiente di Dev Center

| ![Individuazione ](features/images/mrdevcenter/icon-discover.png) [individuazione](/windows/mixed-reality/)| ![Progettazione ](features/images/mrdevcenter/icon-design.png) [](/windows/mixed-reality/design)| ![Sviluppare ](features/images/mrdevcenter/icon-develop.png) [lo sviluppo](/windows/mixed-reality/development)| ![Distribuisci) ](features/images/mrdevcenter/icon-distribute.png) [Distribuisci](/windows/mixed-reality/implementing-3d-app-launchers)|
| :--------------------- | :----------------- | :------------------ | :------------------------ |
| Informazioni su come creare esperienze di realtà mista per HoloLens e visori vr immersive.          | Ottenere guide di progettazione. Compilare l'interfaccia utente. Informazioni sulle interazioni e sull'input.     | Ottenere guide di sviluppo. Apprendere la tecnologia. Comprendere la scienza.       | Preparare l'app per gli utenti e valutare la possibilità di creare un'utilità di avvio 3D. |

## <a name="useful-resources-on-azure"></a>Risorse utili in Azure

| ![Ancoraggi nello spazio](features/images/mrdevcenter/icon-azurespatialanchors.png)<br> [Ancoraggi nello spazio](/azure/spatial-anchors/)| ![Servizi voce ](features/images/mrdevcenter/icon-azurespeechservices.png) [di Servizi di riconoscimento vocale](/azure/cognitive-services/speech-service/)| ![Servizi di ](features/images/mrdevcenter/icon-azurevisionservices.png) [visione vision](/azure/cognitive-services/computer-vision/)|
| :------------------------| :--------------------- | :---------------------- |
| Ancoraggi nello spaziali è un servizio multipiattaforma che consente di creare esperienze di realtà mista usando oggetti che persistono la loro posizione tra dispositivi nel tempo.| Individuare e integrare nell'applicazione le funzionalità vocali di Azure, come il riconoscimento vocale, il riconoscimento del parlante o la traduzione vocale.| Identificare e analizzare il contenuto di immagini o video con i servizi di visione artificiale come il rilevamento dei volti, il riconoscimento delle emozioni o Video Indexer. |

## <a name="how-to-contribute"></a>Come contribuire

Per informazioni su come contribuire a MRTK, vedere [Contribuire a](contributing/contributing.md).

## <a name="getting-help"></a>Guida

Se si verificano problemi causati da MRTK o si hanno domande su come eseguire un'operazione, sono disponibili alcune risorse che possono essere utili:

* Per i report sui bug, [mettere un problema](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/new/choose) nel repository GitHub.
* Per domande, contattare [StackOverflow](https://stackoverflow.com/questions/tagged/mrtk) o il canale [mixed-reality-toolkit](https://holodevelopers.slack.com/messages/C2H4HT858) in Slack. È possibile partecipare alla community di Slack tramite il [mittente dell'invito automatico.](https://holodevelopersslack.azurewebsites.net/)

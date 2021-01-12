---
title: Creazione di contenuto dinamico tramite risolutori
description: In questo corso viene illustrato come usare i risolutori di Mixed Reality Toolkit (MRTK) per creare contenuto dinamico.
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens, MRTK, mixed reality toolkit, UWP, risolutori
ms.localizationpriority: high
ms.openlocfilehash: 959ed164e566f5bee3db203437145fa08ce168d8
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2021
ms.locfileid: "98008021"
---
# <a name="5-creating-dynamic-content-using-solvers"></a><span data-ttu-id="bcab6-104">5. Creazione di contenuto dinamico tramite risolutori</span><span class="sxs-lookup"><span data-stu-id="bcab6-104">5. Creating dynamic content using Solvers</span></span>

<span data-ttu-id="bcab6-105">In questa esercitazione verrà analizzato come posizionare in modo dinamico gli ologrammi usando gli strumenti di posizionamento disponibili in MRTK, noti come risolutori, per risolvere scenari complessi di posizionamento nello spazio.</span><span class="sxs-lookup"><span data-stu-id="bcab6-105">In this tutorial, you will explore ways to dynamically place holograms using the MRTK's available placement tools, known as Solvers, to solve complex spatial placement scenarios.</span></span> <span data-ttu-id="bcab6-106">In MRTK i risolutori sono un sistema di script e comportamenti usati per consentire agli oggetti di seguire te, l'utente o altri oggetti gioco nella scena.</span><span class="sxs-lookup"><span data-stu-id="bcab6-106">In the MRTK, Solvers are a system of scripts and behaviors used to allow objects to follow you, the user, or other game objects in the scene.</span></span> <span data-ttu-id="bcab6-107">Possono anche essere usati per l'ancoraggio a determinate posizioni, rendendo così più intuitiva l'app.</span><span class="sxs-lookup"><span data-stu-id="bcab6-107">They can also be used to snap to certain positions, making your app more intuitive.</span></span>

## <a name="objectives"></a><span data-ttu-id="bcab6-108">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="bcab6-108">Objectives</span></span>

* <span data-ttu-id="bcab6-109">Illustrare i risolutori di MRTK</span><span class="sxs-lookup"><span data-stu-id="bcab6-109">Introduce the MRTK's Solvers</span></span>
* <span data-ttu-id="bcab6-110">Apprendere l'uso dei risolutori per indirizzare l'utente verso gli oggetti</span><span class="sxs-lookup"><span data-stu-id="bcab6-110">Learn how to use Solvers to direct the user to objects</span></span>
* <span data-ttu-id="bcab6-111">Apprendere l'uso dei risolutori per riposizionare gli oggetti</span><span class="sxs-lookup"><span data-stu-id="bcab6-111">Learn how to use Solvers to reposition objects</span></span>

## <a name="location-of-solvers-in-the-mrtk"></a><span data-ttu-id="bcab6-112">Posizione dei risolutori in MRTK</span><span class="sxs-lookup"><span data-stu-id="bcab6-112">Location of Solvers in the MRTK</span></span>

 <span data-ttu-id="bcab6-113">I risolutori di MRTK si trovano nella cartella MRTK SDK.</span><span class="sxs-lookup"><span data-stu-id="bcab6-113">The MRTK's Solvers are located in the MRTK SDK folder.</span></span> <span data-ttu-id="bcab6-114">Per visualizzare i risolutori disponibili in un progetto, nella finestra Project (Progetto) passa ad **Assets (Asset)**  > **MRTK** > **SDK** > **Features (Funzionalità)**  > **Utilities (Utilità)**  > **Solvers** (Risolutori):</span><span class="sxs-lookup"><span data-stu-id="bcab6-114">To see the available Solvers in your project, in the Project window, navigate to **Assets** > **MRTK** > **SDK** > **Features** > **Utilities** > **Solvers**:</span></span>

![Finestra Project di Unity con la cartella Solvers selezionata](images/mr-learning-base/base-05-section1-step1-1.png)

<span data-ttu-id="bcab6-116">In questa esercitazione verrà esaminata l'implementazione dei risolutori Directional Indicator (Indicatore direzionale) e Tap To Place (Tocco per posizionamento).</span><span class="sxs-lookup"><span data-stu-id="bcab6-116">In this tutorial, we will review the implementation of the Directional Indicator Solver and the Tap To Place Solver.</span></span> <span data-ttu-id="bcab6-117">Per altre informazioni sull'intera gamma di risolutori disponibili in MRTK, puoi fare riferimento alla guida [Risolutori](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html) nel [portale della documentazione di MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span><span class="sxs-lookup"><span data-stu-id="bcab6-117">To learn more about the full range of Solvers available in the MRTK, you can refer to the [Solvers](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html) guide in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

> [!NOTE]
> <span data-ttu-id="bcab6-118">Il risolutore Directional Indicator (Indicatore direzionale) non è contenuto nelle cartelle dei risolutori indicate precedentemente, ma è contenuto nelle cartelle Assets (Asset) > MRTK > SDK > Experimental (Sperimentali) > Features (Funzionalità) > Utilities (Utilità) perché si tratta di una funzionalità sperimentale.</span><span class="sxs-lookup"><span data-stu-id="bcab6-118">The Directional Indicator Solver is not located in the Solvers folders referenced above, but in the Assets > MRTK > SDK > Experimental > Features > Utilities folders, because it is an experimental feature.</span></span>

## <a name="using-the-directional-indicator-solver-to-direct-the-user-to-objects"></a><span data-ttu-id="bcab6-119">Uso del risolutore Directional Indicator (Indicatore direzionale) per indirizzare l'utente verso gli oggetti</span><span class="sxs-lookup"><span data-stu-id="bcab6-119">Using the Directional Indicator Solver to direct the user to objects</span></span>

<span data-ttu-id="bcab6-120">Nella finestra Project (Progetto) passa alla cartella **Assets (Asset)**  > **MRTK.Tutorials.GettingStarted** > **Prefabs** (Prefab), fai clic sul prefab **Chevron** e trascinalo sulla finestra Hierarchy (Gerarchia), quindi nella sezione Transform (Trasformazione) imposta **Position** (Posizione) su X = 0, Y = 0, Z = 2 per posizionarlo accanto all'oggetto RoverExplorer:</span><span class="sxs-lookup"><span data-stu-id="bcab6-120">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** folder, click-and-drag the **Chevron** prefab into the Hierarchy window, and set it's Transform **Position** to X = 0, Y = 0, Z = 2 to position it near the RoverExplorer object:</span></span>

![Unity con il prefab Chevron appena aggiunto selezionato](images/mr-learning-base/base-05-section2-step1-1.png)

> [!TIP]
> <span data-ttu-id="bcab6-122">Se ritieni che la fotocamera o altre icone nella scena nascondano gli oggetti o siano elementi di distrazione, puoi nasconderli <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">disattivando il menu Gizmos</a> come illustrato nell'immagine precedente.</span><span class="sxs-lookup"><span data-stu-id="bcab6-122">If you find that the camera or any other icons in your scene are hiding the objects or are distracting, you can hide these by <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">toggling the Gizmos</a> to the off position, as shown in the image above.</span></span> <span data-ttu-id="bcab6-123">Per altre informazioni sul menu Gizmos e su come è possibile usarlo per ottimizzare la vista della scena, puoi fare riferimento alla documentazione relativa al <a href="https://docs.unity3d.com/Manual/GizmosMenu.html" target="_blank">menu Gizmos</a> di Unity.</span><span class="sxs-lookup"><span data-stu-id="bcab6-123">To learn more about the Gizmos menu and how you can use it to optimize your scene view, you can refer to Unity's <a href="https://docs.unity3d.com/Manual/GizmosMenu.html" target="_blank">Gizmos menu</a> documentation.</span></span>

<span data-ttu-id="bcab6-124">Rinominare l'oggetto Chevron **Indicator** (Indicatore) appena aggiunto, quindi nella finestra Inspector (Controllo) usare il pulsante **Add Component** (Aggiungi componente) per aggiungere **DirectionalIndicator**:</span><span class="sxs-lookup"><span data-stu-id="bcab6-124">Rename the newly added Chevron object **Indicator**, then in the Inspector window, use the **Add Component** button to add the **DirectionalIndicator**:</span></span>

![Unity con il componente risolutore DirectionalIndicator aggiunto](images/mr-learning-base/base-05-section2-step1-2.png)

> [!NOTE]
> <span data-ttu-id="bcab6-126">Quando aggiungi un risolutore, in questo caso il componente DirectionalIndicator, viene aggiunto automaticamente il componente SolverHandler perché è richiesto dai risolutori.</span><span class="sxs-lookup"><span data-stu-id="bcab6-126">When you add a Solver, in this case, the DirectionalIndicator component, the SolverHandler component is automatically added because Solvers require it.</span></span>

> [!NOTE]
> <span data-ttu-id="bcab6-127">Directional Indicator Controller (Script) (Controllo indicatore direzionale - script) non fa parte di MRTK, ma è stato incluso negli asset dell'esercitazione.</span><span class="sxs-lookup"><span data-stu-id="bcab6-127">The Directional Indicator Controller (Script) is not part of the MRTK but was included with the tutorial assets.</span></span>

<span data-ttu-id="bcab6-128">Configura i componenti DirectionalIndicator e SolverHandler nel modo seguente:</span><span class="sxs-lookup"><span data-stu-id="bcab6-128">Configure the DirectionalIndicator and SolverHandler components as follows:</span></span>

* <span data-ttu-id="bcab6-129">Verifica che per **Tracked Target Type** (Tipo destinazione tracciata) del componente **SolverHandler** sia impostato il valore **Head** (Testa)</span><span class="sxs-lookup"><span data-stu-id="bcab6-129">Verify that the **SolverHandler** component's **Tracked Target Type** is set to **Head**</span></span>
* <span data-ttu-id="bcab6-130">Assegna **RoverExplorer** a **Directional Target** (Destinazione direzionale) del componente **DirectionalIndicator** trascinandolo dalla finestra Hierarchy (Gerarchia) sul campo **None (Transform)** (Nessuna - Trasformazione)</span><span class="sxs-lookup"><span data-stu-id="bcab6-130">Assign the **RoverExplorer** to the **DirectionalIndicator** component's **Directional Target** by dragging it from the Hierarchy window into the **None (Transform)** field</span></span>
* <span data-ttu-id="bcab6-131">Modifica il valore di **View Offset** (Offset visualizzazione) impostandolo su 0,2</span><span class="sxs-lookup"><span data-stu-id="bcab6-131">Change the **View Offset** to 0.2</span></span>

![Unity con il componente risolutore DirectionalIndicator configurato](images/mr-learning-base/base-05-section2-step1-3.png)

<span data-ttu-id="bcab6-133">Seleziona il pulsante Play (Riproduci) per attivare la modalità di gioco e tieni premuto il pulsante destro del mouse mentre muovi il mouse verso sinistra o verso destra per ruotare la direzione dello sguardo. Potrai osservare quanto segue:</span><span class="sxs-lookup"><span data-stu-id="bcab6-133">Press the Play button to enter Game mode, press-and-hold the right mouse button while moving your mouse to the left or right to rotate your gaze direction, and notice the following:</span></span>

* <span data-ttu-id="bcab6-134">Quando allontani lo sguardo dall'oggetto RoverExplorer, viene visualizzato l'oggetto Indicator (Indicatore) che punta verso l'oggetto RoverExplorer</span><span class="sxs-lookup"><span data-stu-id="bcab6-134">When you look away from the RoverExplorer object, the Indicator object will appear and point towards the RoverExplorer object</span></span>

![Visualizzazione suddivisa della modalità di riproduzione in Unity con il risolutore DirectionalIndicator in uso](images/mr-learning-base/base-05-section2-step1-4.png)

> [!NOTE]
> <span data-ttu-id="bcab6-136">Se il raggio della fotocamera non è visibile nella finestra della scena, verifica che sia attivato il menu Gizmos, come mostrato nell'immagine precedente.</span><span class="sxs-lookup"><span data-stu-id="bcab6-136">If you don't see the camera ray in your Scene window, make sure your Gizmos menu is enabled, as shown in the image above.</span></span>

> [!TIP]
> <span data-ttu-id="bcab6-137">Per informazioni sulla procedura di simulazione di input nell'editor, puoi fare riferimento alla guida [Uso della simulazione di input manuale nell'editor per testare una scena](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html#using-the-in-editor-hand-input-simulation-to-test-a-scene) nel [portale della documentazione di MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span><span class="sxs-lookup"><span data-stu-id="bcab6-137">To learn how to use the in-editor input simulation, you can refer to the [Using the In-Editor Hand Input Simulation to test a scene](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html#using-the-in-editor-hand-input-simulation-to-test-a-scene) guide in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

> [!TIP]
> <span data-ttu-id="bcab6-138">Se il computer è dotato di un microfono, puoi impostare facilmente lo stato attivo del pannello di diagnostica visualizzato nella finestra di gioco usando il comando di riconoscimento vocale "toggle diagnostics" (Attiva/disattiva diagnostica).</span><span class="sxs-lookup"><span data-stu-id="bcab6-138">If your computer has a microphone, you can easily toggle the active state of the Diagnostics panel that appears in the Game window by using the speech command "toggle diagnostics."</span></span> <span data-ttu-id="bcab6-139">In alternativa, puoi disabilitarlo in MRTK Configuration Profile (Profilo di configurazione di MRTK) > Diagnostics (Diagnostica) > Enable Diagnostics System (Abilita sistema di diagnostica).</span><span class="sxs-lookup"><span data-stu-id="bcab6-139">Alternatively, you can disable it in the MRTK Configuration Profile > Diagnostics > Enable Diagnostics System.</span></span> <span data-ttu-id="bcab6-140">Tuttavia, è consigliabile in genere lasciare il sistema di diagnostica attivo durante lo sviluppo.</span><span class="sxs-lookup"><span data-stu-id="bcab6-140">However, it is generally recommended to keep the Diagnostics System active during development.</span></span>

## <a name="using-the-tap-to-place-solver-to-reposition-objects"></a><span data-ttu-id="bcab6-141">Uso del risolutore Tap to Place (Tocco per posizionamento) per riposizionare gli oggetti</span><span class="sxs-lookup"><span data-stu-id="bcab6-141">Using the Tap to Place Solver to reposition objects</span></span>

<span data-ttu-id="bcab6-142">Nella finestra Hierarchy (Gerarchia) seleziona l'oggetto RoverExplorer > **RoverAssembly** e quindi nella finestra Inspector (Controllo) usa il pulsante **Add Component** (Aggiungi componente) per aggiungere il componente **Tap To Place (Script)** (Tocco per posizionamento - Script) e configuralo come indicato di seguito:</span><span class="sxs-lookup"><span data-stu-id="bcab6-142">In the Hierarchy window, select the RoverExplorer > **RoverAssembly** object, then in the Inspector window, use the **Add Component** button to add the **Tap To Place (Script)** component, and configure it as follows:</span></span>

* <span data-ttu-id="bcab6-143">Verifica che per **Tracked Target Type** (Tipo destinazione tracciata) del componente **SolverHandler** sia impostato il valore **Head** (Testa)</span><span class="sxs-lookup"><span data-stu-id="bcab6-143">Verify that the **SolverHandler** component's **Tracked Target Type** is set to **Head**</span></span>
* <span data-ttu-id="bcab6-144">Seleziona la casella di controllo **Keep Orientation Vertical** (Mantieni orientamento verticale)</span><span class="sxs-lookup"><span data-stu-id="bcab6-144">Check the **Keep Orientation Vertical** checkbox</span></span>
* <span data-ttu-id="bcab6-145">Dall'elenco a discesa **Magnetic Surfaces (Superfici magnetiche)**  > **Element 0 (Elemento 0)** deseleziona tutte le opzioni tranne **Spatial Awareness** (Consapevolezza spaziale)</span><span class="sxs-lookup"><span data-stu-id="bcab6-145">From the **Magnetic Surfaces** > **Element 0** dropdown, uncheck all options expect **Spatial Awareness**</span></span>

![Unity con il componente risolutore TapToPlace aggiunto e configurato](images/mr-learning-base/base-05-section3-step1-1.png)

> [!NOTE]
> <span data-ttu-id="bcab6-147">L'impostazione Magnetic Surfaces (Superfici magnetiche) determina quali oggetti possono essere rilevati dal componente Tap To Place (Script) (Tocco per posizionamento - script) quando viene posizionato un oggetto.</span><span class="sxs-lookup"><span data-stu-id="bcab6-147">The Magnetic Surfaces setting determines which objects the Tap To Place (Script) component can detect when placing an object.</span></span> <span data-ttu-id="bcab6-148">Modificando l'impostazione in modo da definire solo Spatial Awareness (Consapevolezza spaziale), il componente Tap To Place (Script) (Tocco per posizionamento - script) potrà posizionare Rover solo su oggetti del livello di Unity denominato Spatial Awareness (Consapevolezza spaziale), che per impostazione predefinita è la mesh di consapevolezza spaziale generata da HoloLens.</span><span class="sxs-lookup"><span data-stu-id="bcab6-148">By changing the setting to only Spatial Awareness, the Tap To Place (Script) component will only be able to place the Rover on objects on the Unity Layer named Spatial Awareness, which by default is the Spatial Awareness Mesh generated by the HoloLens.</span></span>
>
><span data-ttu-id="bcab6-149">Per altre informazioni sui livelli, puoi fare riferimento alla documentazione di Unity relativa ai <a href="https://docs.unity3d.com/Manual/Layers.html" target="_blank">livelli</a>.</span><span class="sxs-lookup"><span data-stu-id="bcab6-149">To learn more about Layers, you can refer to Unity's <a href="https://docs.unity3d.com/Manual/Layers.html" target="_blank">Layers</a> documentation.</span></span>

> [!TIP]
> <span data-ttu-id="bcab6-150">Se vuoi visualizzare la mesh di consapevolezza spaziale quando testi la funzionalità Tap To Place (Tocco per posizionamento) in HoloLens, puoi impostare temporaneamente l'opzione di visualizzazione dell'osservatore della mesh spaziale come visibile.</span><span class="sxs-lookup"><span data-stu-id="bcab6-150">If you want to see the Spatial Awareness Mesh when testing the Tap To Place functionality on your HoloLens, you can temporarily set the Spatial Mesh Observer's Display Option to Visible.</span></span> <span data-ttu-id="bcab6-151">Per un promemoria su come modificare l'opzione di visualizzazione, puoi fare riferimento alle istruzioni [Modifica dell'opzione di visualizzazione di consapevolezza spaziale](mr-learning-base-03.md#changing-the-spatial-awareness-display-option).</span><span class="sxs-lookup"><span data-stu-id="bcab6-151">For a reminder on how to change the Display Option, you can refer to the [Changing the Spatial Awareness Display Option](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) instructions.</span></span>

<span data-ttu-id="bcab6-152">Con l'oggetto RoverAssembly ancora selezionato nella finestra Hierarchy (Gerarchia), nella finestra Inspector (Controllo) individua l'evento **On Placing Started ()** (All'avvio del posizionamento) e fai clic sull'icona **+** per aggiungere un nuovo evento:</span><span class="sxs-lookup"><span data-stu-id="bcab6-152">With the RoverAssembly object still selected in the Hierarchy window, in the Inspector window, locate the **On Placing Started ()** event and click the **+** icon to add a new event:</span></span>

![Unity con l'evento OnPlacingStarted di TapToPlace aggiunto](images/mr-learning-base/base-05-section3-step1-2.png)

<span data-ttu-id="bcab6-154">Configura l'evento come indicato di seguito:</span><span class="sxs-lookup"><span data-stu-id="bcab6-154">Configure the event as follows:</span></span>

* <span data-ttu-id="bcab6-155">Assegna l'oggetto **RoverAssembly** come listener per l'evento On Placing Started () (All'avvio del posizionamento) trascinandolo dalla finestra Hierarchy (Gerarchia) sul campo **None (Object)** (Nessuno - oggetto)</span><span class="sxs-lookup"><span data-stu-id="bcab6-155">Assign the **RoverAssembly** object as a listener for the On Placing Started () event by dragging it from the Hierarchy window into the **None (Object)** field</span></span>
* <span data-ttu-id="bcab6-156">Dall'elenco a discesa **No Function** (Nessuna funzione) seleziona **TapToPlace** > **float SurfaceNormalOffset** per aggiornare il valore della proprietà SurfaceNormalOffset quando viene attivato l'evento</span><span class="sxs-lookup"><span data-stu-id="bcab6-156">From the **No Function** dropdown, select **TapToPlace** > **float SurfaceNormalOffset** to update the SurfaceNormalOffset property value when the event is triggered</span></span>
* <span data-ttu-id="bcab6-157">Verifica che l'argomento sia impostato su **0**</span><span class="sxs-lookup"><span data-stu-id="bcab6-157">Verify that the argument is set to **0**</span></span>

![Unity con l'evento OnPlacingStarted di TapToPlace configurato](images/mr-learning-base/base-05-section3-step1-3.png)

<span data-ttu-id="bcab6-159">Nella finestra Hierarchy (Gerarchia) fai clic con il pulsante destro del mouse in un punto vuoto e scegli **3D Object (Oggetto 3D)**  > **Cube (Cubo)** per creare un oggetto temporaneo che rappresenta il terreno e configura il componente **Transform** (Trasformazione) come segue:</span><span class="sxs-lookup"><span data-stu-id="bcab6-159">In the Hierarchy window, right-click on an empty spot and select **3D Object** > **Cube**, to create a temporary object representing the ground, and configure the **Transform** component as follows:</span></span>

* <span data-ttu-id="bcab6-160">**Position** (Posizione): X = 0, Y = -1,65, Z = 6</span><span class="sxs-lookup"><span data-stu-id="bcab6-160">**Position**: X = 0, Y = -1.65, Z = 6</span></span>
* <span data-ttu-id="bcab6-161">**Rotation** (Rotazione): X = 0, Y = 0, Z = 0</span><span class="sxs-lookup"><span data-stu-id="bcab6-161">**Rotation**: X = 0, Y = 0, Z = 0</span></span>
* <span data-ttu-id="bcab6-162">**Scale** (Scala): X = 10, Y = 0,2, Z = 10</span><span class="sxs-lookup"><span data-stu-id="bcab6-162">**Scale**: X = 10, Y = 0.2, Z = 10</span></span>

![Unity con oggetto cubo temporaneo del terreno aggiunto e posizionato](images/mr-learning-base/base-05-section3-step1-4.png)

<span data-ttu-id="bcab6-164">Con il cubo temporaneo ancora selezionato nella finestra Hierarchy (Gerarchia), nella finestra Inspector (Controllo) usa l'elenco a discesa **Layers** (Livelli) per modificare l'impostazione del livello del cubo in modo da includere solo il livello **Spatial Awareness** (Consapevolezza spaziale):</span><span class="sxs-lookup"><span data-stu-id="bcab6-164">With the temporary Cube still selected in the Hierarchy window, in the Inspector window, use the **Layers** dropdown to change the Cube's Layer setting only to include the **Spatial Awareness** layer:</span></span>

![Unity con il livello dell'oggetto cubo temporaneo del terreno impostato su Spatial Awareness](images/mr-learning-base/base-05-section3-step1-5.png)

<span data-ttu-id="bcab6-166">Seleziona il pulsante Play (Riproduci) per attivare la modalità di gioco, quindi tieni premuto il pulsante destro del mouse mentre muovi il mouse verso il basso finché lo sguardo non incontra l'oggetto RoverAssembly:</span><span class="sxs-lookup"><span data-stu-id="bcab6-166">Press the Play button to enter Game mode, then press-and-hold the right mouse button while moving your mouse down until the gaze hit's the RoverAssembly object:</span></span>

![Visualizzazione suddivisa della modalità di riproduzione in Unity con lo sguardo fisso che incontra l'oggetto RoverAssembly](images/mr-learning-base/base-05-section3-step1-6.png)

<span data-ttu-id="bcab6-168">Fai clic con il pulsante sinistro del mouse per avviare il processo di tocco e posizionamento:</span><span class="sxs-lookup"><span data-stu-id="bcab6-168">Click the left mouse button to start the tap-to-place process:</span></span>

![Visualizzazione suddivisa della modalità di riproduzione in Unity con il posizionamento TapToPlace avviato](images/mr-learning-base/base-05-section3-step1-7.png)

<span data-ttu-id="bcab6-170">Tieni premuto il pulsante destro del mouse mentre muovi il mouse verso sinistra o verso destra per ruotare la direzione dello sguardo. Quando sei soddisfatto del posizionamento, fai clic con il pulsante sinistro del mouse:</span><span class="sxs-lookup"><span data-stu-id="bcab6-170">Press-and-hold the right mouse button while moving your mouse to the left or right to rotate your gaze direction, when you are happy with the placement, click the left mouse button:</span></span>

![Visualizzazione suddivisa della modalità di riproduzione in Unity con il posizionamento TapToPlace terminato](images/mr-learning-base/base-05-section3-step1-8.png)

<span data-ttu-id="bcab6-172">Dopo aver testato la funzionalità in modalità di gioco, fai clic con il pulsante destro del mouse sull'oggetto Cube (Cubo) e scegli **Delete** (Elimina) per rimuoverlo dalla scena:</span><span class="sxs-lookup"><span data-stu-id="bcab6-172">Once you are done testing the feature in the Game mode, right-click on the Cube object and select **Delete** to remove it from the scene:</span></span>

![Unity con cubo temporaneo del terreno selezionato e il menu popup contestuale Delete](images/mr-learning-base/base-05-section3-step1-9.png)

## <a name="congratulations"></a><span data-ttu-id="bcab6-174">Lezione completata</span><span class="sxs-lookup"><span data-stu-id="bcab6-174">Congratulations</span></span>

<span data-ttu-id="bcab6-175">In questa esercitazione hai appreso come usare il risolutore Directional Indicator (Indicatore direzionale) di MRTK per fare in modo che un elemento dell'interfaccia utente indirizzi intuitivamente l'utente verso gli oggetti.</span><span class="sxs-lookup"><span data-stu-id="bcab6-175">In this tutorial, you learned how to use the MRTK's Directional Indicator Solver to have a UI element intuitively direct the user to objects.</span></span> <span data-ttu-id="bcab6-176">Hai appreso inoltre come usare il risolutore Tap To Place (Tocco per posizionamento) per riposizionare facilmente gli oggetti.</span><span class="sxs-lookup"><span data-stu-id="bcab6-176">You also learned how to use the Tap To Place Solver to reposition objects easily.</span></span>

<span data-ttu-id="bcab6-177">Per altre informazioni su questi e altri risolutori inclusi in MRTK, puoi fare riferimento alla guida [Risolutori](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html) nel [portale della documentazione di MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span><span class="sxs-lookup"><span data-stu-id="bcab6-177">To learn more about these and other solvers included with the MRTK,  you can refer to the [Solvers](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html) guide in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

[<span data-ttu-id="bcab6-178">Esercitazione successiva: 6. Creazione delle interfacce utente</span><span class="sxs-lookup"><span data-stu-id="bcab6-178">Next Tutorial: 6. Creating user interfaces</span></span>](mr-learning-base-06.md)
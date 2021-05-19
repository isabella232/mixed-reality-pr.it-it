---
title: Panoramica dell'esempio di tracciamento oculare
description: Esempio di creazione di tracciamento oculare in MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realtà mista, sviluppo, MRTK, EyeTracking,
ms.openlocfilehash: b5fd3ee35e54c54f2f6b21dc1ce53625c68f65b4
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144688"
---
# <a name="eye-tracking-examples"></a><span data-ttu-id="1039b-104">Esempi di tracciamento oculare</span><span class="sxs-lookup"><span data-stu-id="1039b-104">Eye tracking examples</span></span>

<span data-ttu-id="1039b-105">Questo argomento descrive come iniziare rapidamente a usare il tracciamento oculare in MRTK compilando esempi di tracciamento oculare MRTK (Assets/MRTK/Examples/Demos/EyeTracking).</span><span class="sxs-lookup"><span data-stu-id="1039b-105">This topic describes how to quickly get started with eye tracking in MRTK by building on MRTK eye tracking examples (Assets/MRTK/Examples/Demos/EyeTracking).</span></span>
<span data-ttu-id="1039b-106">Questi esempi consentono di sperimentare una delle nuove funzionalità di input magiche: **Tracciamento oculare**!</span><span class="sxs-lookup"><span data-stu-id="1039b-106">These samples let you experience one of our new magical input capabilities: **Eye tracking**!</span></span>
<span data-ttu-id="1039b-107">La demo include diversi casi d'uso, dalle attivazioni implicite basate sugli occhi  a come combinare facilmente le informazioni su ciò che si sta esaminando con l'input vocale **e** manuale.</span><span class="sxs-lookup"><span data-stu-id="1039b-107">The demo includes various use cases, ranging from implicit eye-based activations to how to seamlessly combine information about what you are looking at with **voice** and **hand** input.</span></span>
<span data-ttu-id="1039b-108">In questo modo gli utenti possono selezionare e spostare in modo semplice e rapido il contenuto olografico nella visualizzazione semplicemente osservando una destinazione e pronunciando _"Seleziona"_ o eseguendo un movimento della mano.</span><span class="sxs-lookup"><span data-stu-id="1039b-108">This enables users to quickly and effortlessly select and move holographic content across their view simply by looking at a target and saying _'Select'_ or performing a hand gesture.</span></span>
<span data-ttu-id="1039b-109">Le demo includono anche un esempio di scorrimento con sguardo rivolto verso gli occhi, panoramica e zoom di testo e immagini su uno slate.</span><span class="sxs-lookup"><span data-stu-id="1039b-109">The demos also include an example for eye-gaze-directed scroll, pan and zoom of text and images on a slate.</span></span>
<span data-ttu-id="1039b-110">Infine, viene fornito un esempio per la registrazione e la visualizzazione dell'attenzione visiva dell'utente su uno slate 2D.</span><span class="sxs-lookup"><span data-stu-id="1039b-110">Finally, an example is provided for recording and visualizing the user's visual attention on a 2D slate.</span></span>
<span data-ttu-id="1039b-111">Nella sezione seguente sono disponibili altri dettagli sui diversi esempi inclusi nel pacchetto di esempio di tracciamento oculare MRTK (Assets/MRTK/Examples/Demos/EyeTracking):</span><span class="sxs-lookup"><span data-stu-id="1039b-111">In the following section, you will find more details on what each of the different samples in the MRTK eye tracking example package (Assets/MRTK/Examples/Demos/EyeTracking) includes:</span></span>

![Elenco di scene di tracciamento oculare](../images/eye-tracking/mrtk_et_list_et_scenes.jpg)

<span data-ttu-id="1039b-113">La sezione seguente è una rapida panoramica delle singole scene della demo di tracciamento oculare.</span><span class="sxs-lookup"><span data-stu-id="1039b-113">The following section is a quick overview of what the individual eye tracking demo scenes are about.</span></span>
<span data-ttu-id="1039b-114">Le scene demo di tracciamento oculare MRTK vengono caricate in modo [aggiuntivo,](https://docs.unity3d.com/ScriptReference/SceneManagement.LoadSceneMode.Additive.html)che verranno illustrate di seguito come configurare.</span><span class="sxs-lookup"><span data-stu-id="1039b-114">The MRTK eye tracking demo scenes are [loaded additively](https://docs.unity3d.com/ScriptReference/SceneManagement.LoadSceneMode.Additive.html), which we will explain below how to set up.</span></span>

## <a name="overview-of-the-eye-tracking-demo-samples"></a><span data-ttu-id="1039b-115">Panoramica degli esempi di demo di tracciamento oculare</span><span class="sxs-lookup"><span data-stu-id="1039b-115">Overview of the eye tracking demo samples</span></span>

### <a name="eye-supported-target-selection"></a>[<span data-ttu-id="1039b-116">**Selezione della destinazione supportata dagli occhi**</span><span class="sxs-lookup"><span data-stu-id="1039b-116">**Eye-Supported Target Selection**</span></span>](../input/eye-tracking/eye-tracking-target-selection.md)

<span data-ttu-id="1039b-117">Questa esercitazione illustra la facilità di accesso ai dati dello sguardo fisso per selezionare le destinazioni.</span><span class="sxs-lookup"><span data-stu-id="1039b-117">This tutorial showcases the ease of accessing eye gaze data to select targets.</span></span>
<span data-ttu-id="1039b-118">Include un esempio di feedback sottile ma potente per fornire all'utente la certezza che un obiettivo è incentrato senza essere eccessivo.</span><span class="sxs-lookup"><span data-stu-id="1039b-118">It includes an example for subtle yet powerful feedback to provide the user with the confidence that a target is focused without being overwhelming.</span></span>
<span data-ttu-id="1039b-119">Esiste anche un semplice esempio di notifiche intelligenti che scompaiono automaticamente dopo la lettura.</span><span class="sxs-lookup"><span data-stu-id="1039b-119">In addition, there is a simple example of smart notifications that automatically disappear after being read.</span></span>

<span data-ttu-id="1039b-120">**Riepilogo:** selezioni di destinazione veloci e senza sforzo usando una combinazione di occhi, voce e input manuale.</span><span class="sxs-lookup"><span data-stu-id="1039b-120">**Summary**: Fast and effortless target selections using a combination of eyes, voice and hand input.</span></span>

### <a name="eye-supported-navigation"></a>[<span data-ttu-id="1039b-121">**Navigazione supportata dagli occhi**</span><span class="sxs-lookup"><span data-stu-id="1039b-121">**Eye-Supported Navigation**</span></span>](../input/eye-tracking/eye-tracking-navigation.md)

<span data-ttu-id="1039b-122">Si supponga di leggere alcune informazioni su uno schermo distante o sull'e-reader e, quando si raggiunge la fine del testo visualizzato, il testo scorre automaticamente verso l'alto per visualizzare più contenuto.</span><span class="sxs-lookup"><span data-stu-id="1039b-122">Imagine that you are reading some information on a distant display or your e-reader and when you reach the end of the displayed text, the text automatically scrolls up to reveal more content.</span></span>
<span data-ttu-id="1039b-123">O che ne dite di eseguire uno zoom diretto verso la posizione in cui si stava guardando?</span><span class="sxs-lookup"><span data-stu-id="1039b-123">Or how about magically zooming directly toward where you were looking at?</span></span>
<span data-ttu-id="1039b-124">Di seguito sono riportati alcuni esempi presentati in questa esercitazione relativi alla navigazione con supporto oculare.</span><span class="sxs-lookup"><span data-stu-id="1039b-124">These are some of the examples showcased in this tutorial regarding eye-supported navigation.</span></span>
<span data-ttu-id="1039b-125">Esiste anche un esempio di rotazione a mani libere degli ologrammi 3D facendo in modo che ruotino automaticamente in base allo stato attivo corrente.</span><span class="sxs-lookup"><span data-stu-id="1039b-125">In addition, there is an example for hands-free rotation of 3D holograms by making them automatically rotate based on your current focus.</span></span>

<span data-ttu-id="1039b-126">**Riepilogo:** scorrimento, panoramica, zoom, rotazione 3D con una combinazione di occhi, voce e input della mano.</span><span class="sxs-lookup"><span data-stu-id="1039b-126">**Summary**: Scroll, pan, zoom, 3D rotation using a combination of eyes, voice and hand input.</span></span>

### <a name="eye-supported-positioning"></a>[<span data-ttu-id="1039b-127">**Posizionamento supportato dagli occhi**</span><span class="sxs-lookup"><span data-stu-id="1039b-127">**Eye-Supported Positioning**</span></span>](../input/eye-tracking/eye-tracking-eyes-and-hands.md)

<span data-ttu-id="1039b-128">Questa esercitazione illustra uno scenario di input denominato [Put-That-There](https://youtu.be/CbIn8p4_4CQ) che torna alla ricerca del MIT Media Lab all'inizio degli anni '80 con input oculare, mano e voce.</span><span class="sxs-lookup"><span data-stu-id="1039b-128">This tutorial shows an input scenario called [Put-That-There](https://youtu.be/CbIn8p4_4CQ) dating back to research from the MIT Media Lab in the early 1980's with eye, hand and voice input.</span></span>
<span data-ttu-id="1039b-129">L'idea è semplice: trarre vantaggio dagli occhi per la selezione e il posizionamento rapidi della destinazione.</span><span class="sxs-lookup"><span data-stu-id="1039b-129">The idea is simple: Benefit from your eyes for fast target selection and positioning.</span></span>
<span data-ttu-id="1039b-130">È sufficiente esaminare un ologramma e pronunciare _"put this",_ osservare dove si vuole posizionarlo e pronunciare _"there!"._</span><span class="sxs-lookup"><span data-stu-id="1039b-130">Simply look at a hologram and say _'put this'_, look over where you want to place it and say _'there!'_.</span></span>
<span data-ttu-id="1039b-131">Per un posizionamento più preciso dell'ologramma, è possibile usare un input aggiuntivo dalle mani, dalla voce o dai controller.</span><span class="sxs-lookup"><span data-stu-id="1039b-131">For more precisely positioning your hologram, you can use additional input from your hands, voice or controllers.</span></span>

<span data-ttu-id="1039b-132">**Riepilogo:** posizionamento degli ologrammi con occhi, voce e input della mano *(trascinamento della selezione).*</span><span class="sxs-lookup"><span data-stu-id="1039b-132">**Summary**: Positioning holograms using eyes, voice and hand input (*drag-and-drop*).</span></span> <span data-ttu-id="1039b-133">Dispositivi di scorrimento supportati dagli occhi con occhi e mani.</span><span class="sxs-lookup"><span data-stu-id="1039b-133">Eye-supported sliders using eyes + hands.</span></span>

### <a name="visualization-of-visual-attention"></a><span data-ttu-id="1039b-134">**Visualizzazione dell'attenzione visiva**</span><span class="sxs-lookup"><span data-stu-id="1039b-134">**Visualization of visual attention**</span></span>

<span data-ttu-id="1039b-135">I dati basati sul punto di vista degli utenti sono uno strumento estremamente potente per valutare l'usabilità di una progettazione e identificare i problemi in flussi di lavoro efficienti.</span><span class="sxs-lookup"><span data-stu-id="1039b-135">Data based on where users look makes an immensely powerful tool to assess usability of a design and to identify problems in efficient work streams.</span></span>
<span data-ttu-id="1039b-136">Questa esercitazione illustra diverse visualizzazioni del tracciamento oculare e il modo in cui si adattano alle diverse esigenze.</span><span class="sxs-lookup"><span data-stu-id="1039b-136">This tutorial discusses different eye tracking visualizations and how they fit different needs.</span></span>
<span data-ttu-id="1039b-137">Vengono forniti esempi di base per la registrazione e il caricamento di dati di tracciamento oculare ed esempi su come visualizzarli.</span><span class="sxs-lookup"><span data-stu-id="1039b-137">We provide basic examples for logging and loading eye tracking data and examples for how to visualize them.</span></span>

<span data-ttu-id="1039b-138">**Riepilogo:** mappa di attenzione bidimensionale (mappe termica) sugli slate.</span><span class="sxs-lookup"><span data-stu-id="1039b-138">**Summary**: Two-dimensional attention map (heatmaps) on slates.</span></span> <span data-ttu-id="1039b-139">Registrazione & riproduzione dei dati di tracciamento oculare.</span><span class="sxs-lookup"><span data-stu-id="1039b-139">Recording & replaying eye tracking data.</span></span>

## <a name="setting-up-the-mrtk-eye-tracking-samples"></a><span data-ttu-id="1039b-140">Configurazione dei campioni di tracciamento oculare di MRTK</span><span class="sxs-lookup"><span data-stu-id="1039b-140">Setting up the MRTK eye tracking samples</span></span>

### <a name="prerequisites"></a><span data-ttu-id="1039b-141">Prerequisiti</span><span class="sxs-lookup"><span data-stu-id="1039b-141">Prerequisites</span></span>

<span data-ttu-id="1039b-142">Si noti che l'uso degli esempi di tracciamento oculare nel dispositivo richiede un HoloLens 2 e un pacchetto di app di esempio compilato con la funzionalità "Input sguardo fisso" nell'app AppXManifest del pacchetto.</span><span class="sxs-lookup"><span data-stu-id="1039b-142">Note that using the eye tracking samples on device requires a HoloLens 2 and a sample app package that is built with the "Gaze Input" capability on the package's AppXManifest.</span></span>

<span data-ttu-id="1039b-143">Per usare questi esempi di tracciamento oculare [](../input/eye-tracking/eye-tracking-basic-setup.md#testing-your-unity-app-on-a-hololens-2) nel dispositivo, assicurarsi di seguire questa procedura prima di compilare l'app in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="1039b-143">In order to use these eye tracking samples on device, make sure to follow [these steps](../input/eye-tracking/eye-tracking-basic-setup.md#testing-your-unity-app-on-a-hololens-2) prior to building the app in Visual Studio.</span></span>

### <a name="1-load-eyetrackingdemo-00-rootsceneunity"></a><span data-ttu-id="1039b-144">1. Load EyeTrackingDemo-00-RootScene.unity</span><span class="sxs-lookup"><span data-stu-id="1039b-144">1. Load EyeTrackingDemo-00-RootScene.unity</span></span>

<span data-ttu-id="1039b-145">*EyeTrackingDemo-00-RootScene* è lascena di base (radice) che include tutti i componenti principali di MRTK.</span><span class="sxs-lookup"><span data-stu-id="1039b-145">The *EyeTrackingDemo-00-RootScene* is the base (_root_) scene that has all the core MRTK components included.</span></span>
<span data-ttu-id="1039b-146">Questa è la scena che è necessario caricare per prima e da cui si eseguiranno le demo di tracciamento oculare.</span><span class="sxs-lookup"><span data-stu-id="1039b-146">This is the scene that you need to load first and from which you will run the eye tracking demos.</span></span>
<span data-ttu-id="1039b-147">È dotato di un menu della scena grafica che consente di passare facilmente tra i diversi campioni di tracciamento oculare che verranno caricati [in modo aggiuntivo.](https://docs.unity3d.com/ScriptReference/SceneManagement.LoadSceneMode.Additive.html)</span><span class="sxs-lookup"><span data-stu-id="1039b-147">It features a graphical scene menu that allows you to easily switch between the different eye tracking samples which will be [loaded additively](https://docs.unity3d.com/ScriptReference/SceneManagement.LoadSceneMode.Additive.html).</span></span>

![Menu della scena nell'esempio di tracciamento oculare](../images/eye-tracking/mrtk_et_scenemenu.jpg)

<span data-ttu-id="1039b-149">La scena radice include alcuni componenti principali che verranno mantenuti nelle scene caricate in modo aggiuntivo, ad esempio i profili configurati per MRTK e la fotocamera della scena.</span><span class="sxs-lookup"><span data-stu-id="1039b-149">The root scene includes a few core components that will persist across the additively loaded scenes, such as the MRTK configured profiles and scene camera.</span></span>
<span data-ttu-id="1039b-150">_MixedRealityBasicSceneSetup_ (vedere lo screenshot seguente) include uno script che carica automaticamente la scena di riferimento all'avvio.</span><span class="sxs-lookup"><span data-stu-id="1039b-150">The _MixedRealityBasicSceneSetup_ (see screenshot below) includes a script that will automatically load the referenced scene on startup.</span></span>
<span data-ttu-id="1039b-151">Per impostazione predefinita, si _tratta di EyeTrackingDemo-02-TargetSelection._</span><span class="sxs-lookup"><span data-stu-id="1039b-151">By default, this is _EyeTrackingDemo-02-TargetSelection_.</span></span>  

![Esempio per lo script OnLoadStartScene](../images/eye-tracking/mrtk_et_onloadstartscene.jpg)

### <a name="2-adding-scenes-to-the-build-menu"></a><span data-ttu-id="1039b-153">2. Aggiunta di scene al menu di compilazione</span><span class="sxs-lookup"><span data-stu-id="1039b-153">2. Adding scenes to the build menu</span></span>

<span data-ttu-id="1039b-154">Per caricare scene additive durante il runtime, è necessario aggiungere prima queste scene alle impostazioni di compilazione _-> scene_ nel menu Compila.</span><span class="sxs-lookup"><span data-stu-id="1039b-154">To load additive scenes during runtime, you must add these scenes to your _Build Settings -> Scenes in Build_ menu first.</span></span>
<span data-ttu-id="1039b-155">È importante che la scena radice sia visualizzata come prima scena nell'elenco:</span><span class="sxs-lookup"><span data-stu-id="1039b-155">It is important that the root scene is shown as the first scene in the list:</span></span>

![Menu della scena Build Settings (Impostazioni di compilazione) per gli esempi di tracciamento oculare](../images/eye-tracking/mrtk_et_build_settings.jpg)

### <a name="3-play-the-eye-tracking-samples-in-the-unity-editor"></a><span data-ttu-id="1039b-157">3. Riprodurre gli esempi di tracciamento oculare nell'editor di Unity</span><span class="sxs-lookup"><span data-stu-id="1039b-157">3. Play the eye tracking samples in the Unity editor</span></span>

<span data-ttu-id="1039b-158">Dopo aver aggiunto le scene di tracciamento oculare alle impostazioni di compilazione e aver caricato _EyeTrackingDemo-00-RootScene,_ è possibile verificare che sia abilitato lo script _'OnLoadStartScene'_ collegato a _MixedRealityBasicSceneSetup_ GameObject?</span><span class="sxs-lookup"><span data-stu-id="1039b-158">After adding the eye tracking scenes to the Build Settings and loading the _EyeTrackingDemo-00-RootScene_, there is one last thing you may want to check: Is the _'OnLoadStartScene'_ script that is attached to the _MixedRealityBasicSceneSetup_ GameObject enabled?</span></span> <span data-ttu-id="1039b-159">Questo consente alla scena radice di sapere quale scena demo caricare per prima.</span><span class="sxs-lookup"><span data-stu-id="1039b-159">This is to let the root scene know which demo scene to load first.</span></span>

![Esempio per lo script OnLoad_StartScene](../images/eye-tracking/mrtk_et_onloadstartscene.jpg)

<span data-ttu-id="1039b-161">È possibile eseguire il roll-to-roll.</span><span class="sxs-lookup"><span data-stu-id="1039b-161">Let's roll!</span></span> <span data-ttu-id="1039b-162">Premere _"Play"_!</span><span class="sxs-lookup"><span data-stu-id="1039b-162">Hit _"Play"_!</span></span>
<span data-ttu-id="1039b-163">Verranno visualizzate diverse gemme e il menu della scena nella parte superiore.</span><span class="sxs-lookup"><span data-stu-id="1039b-163">You should see several gems appear and the scene menu at the top.</span></span>

![Screenshot di esempio dalla scena di selezione della destinazione ET](../images/eye-tracking/mrtk_et_targetselect.png)

<span data-ttu-id="1039b-165">Si noterà anche un piccolo cerchio semitrasparente al centro della visualizzazione del gioco.</span><span class="sxs-lookup"><span data-stu-id="1039b-165">You should also notice a small semitransparent circle at the center of your game view.</span></span>
<span data-ttu-id="1039b-166">Funge da indicatore (cursore) dello sguardo _fisso simulato:_ è sufficiente premere il pulsante destro del _mouse_ e spostare il mouse per modificarne la posizione.</span><span class="sxs-lookup"><span data-stu-id="1039b-166">This acts as an indicator (cursor) of your _simulated eye gaze_: Simply press down the _right mouse button_ and move the mouse to change its position.</span></span>
<span data-ttu-id="1039b-167">Quando il cursore si posiziona sulle gemme, si noterà che verrà allineato al centro della gemma attualmente visualizzata.</span><span class="sxs-lookup"><span data-stu-id="1039b-167">When the cursor is hovering over the gems, you will notice that it will snap to the center of the currently viewed gem.</span></span>
<span data-ttu-id="1039b-168">Questo è un ottimo modo per verificare se gli eventi vengono attivati come previsto quando _si "esamina"_ una destinazione.</span><span class="sxs-lookup"><span data-stu-id="1039b-168">This is a great way to test if events are triggered as expected when _"looking"_ at a target.</span></span>
<span data-ttu-id="1039b-169">Tenere presente che lo _sguardo fisso simulato_ tramite il controllo del mouse è un integratore piuttosto scarso dei movimenti oculari rapidi e non intenzionali.</span><span class="sxs-lookup"><span data-stu-id="1039b-169">Be aware that the _simulated eye gaze_ via mouse control is a rather poor supplement to our rapid and unintentional eye movements.</span></span>
<span data-ttu-id="1039b-170">Tuttavia, è ideale per testare le funzionalità di base prima di eseguire l'iterazione della progettazione distribuerla nel HoloLens 2 dispositivo.</span><span class="sxs-lookup"><span data-stu-id="1039b-170">However, it is great for testing the basic functionality before iterating on the design by deploying it to the HoloLens 2 device.</span></span>
<span data-ttu-id="1039b-171">Tornare alla scena di esempio del tracciamento oculare: la gemma ruota fino a quando viene guardata e può essere distrutta "guardando" e ...</span><span class="sxs-lookup"><span data-stu-id="1039b-171">Returning to our eye tracking sample scene: The gem rotates as long as being looked at and can be destroyed by "looking" at it and ...</span></span>

- <span data-ttu-id="1039b-172">Premere _INVIO_ (che simula il pronunciare "select")</span><span class="sxs-lookup"><span data-stu-id="1039b-172">Pressing _Enter_ (which simulates saying "select")</span></span>
- <span data-ttu-id="1039b-173">Pronunciare _"select"_ nel microfono</span><span class="sxs-lookup"><span data-stu-id="1039b-173">Saying _"select"_ into your microphone</span></span>
- <span data-ttu-id="1039b-174">Mentre si preme _BARRA SPAZIATRICE_ per visualizzare l'input della mano simulato, fare clic sul pulsante sinistro del mouse per eseguire un avvicinamento delle dita simulato</span><span class="sxs-lookup"><span data-stu-id="1039b-174">While pressing _Space_ to show the simulated hand input, click the left mouse button to perform a simulated pinch</span></span>

<span data-ttu-id="1039b-175">Nell'esercitazione Selezione destinazione supportata dagli occhi viene descritto in modo più dettagliato come ottenere [**queste**](../input/eye-tracking/eye-tracking-target-selection.md) interazioni.</span><span class="sxs-lookup"><span data-stu-id="1039b-175">We describe in more detail how you can achieve these interactions in our [**Eye-Supported Target Selection**](../input/eye-tracking/eye-tracking-target-selection.md) tutorial.</span></span>

<span data-ttu-id="1039b-176">Quando si sposta il cursore verso l'alto fino alla barra dei menu superiore nella scena, si noterà che l'elemento attualmente al passaggio del mouse verrà evidenziato in modo secondario.</span><span class="sxs-lookup"><span data-stu-id="1039b-176">When moving the cursor up to the top menu bar in the scene, you will notice that the currently hovered item will highlight subtly.</span></span>
<span data-ttu-id="1039b-177">È possibile selezionare l'elemento attualmente evidenziato usando uno dei metodi di commit descritti in precedenza, ad esempio premendo _INVIO._</span><span class="sxs-lookup"><span data-stu-id="1039b-177">You can select the currently highlighted item by using one of the above described commit methods (e.g., pressing _Enter_).</span></span>
<span data-ttu-id="1039b-178">In questo modo è possibile passare da una scena di esempio di tracciamento oculare all'altra.</span><span class="sxs-lookup"><span data-stu-id="1039b-178">This way you can switch between the different eye tracking sample scenes.</span></span>

### <a name="4-how-to-test-specific-sub-scenes"></a><span data-ttu-id="1039b-179">4. Come testare sotto-scene specifiche</span><span class="sxs-lookup"><span data-stu-id="1039b-179">4. How to test specific sub scenes</span></span>

<span data-ttu-id="1039b-180">Quando si lavora a uno scenario specifico, è possibile che non si voglia scorrere ogni volta il menu della scena.</span><span class="sxs-lookup"><span data-stu-id="1039b-180">When working on a specific scenario, you may not want to go through the scene menu every time.</span></span>
<span data-ttu-id="1039b-181">Al contrario, è possibile iniziare direttamente dalla scena su cui si sta lavorando quando si preme il _pulsante_ Riproduci.</span><span class="sxs-lookup"><span data-stu-id="1039b-181">Instead, you may want to start directly from the scene that you are currently working on when pressing the _Play_ button.</span></span>
<span data-ttu-id="1039b-182">non è un problema.</span><span class="sxs-lookup"><span data-stu-id="1039b-182">No problem!</span></span> <span data-ttu-id="1039b-183">Ecco cosa è possibile fare:</span><span class="sxs-lookup"><span data-stu-id="1039b-183">Here is what you can do:</span></span>

1. <span data-ttu-id="1039b-184">Caricare la _scena_ radice</span><span class="sxs-lookup"><span data-stu-id="1039b-184">Load the _root_ scene</span></span>
2. <span data-ttu-id="1039b-185">Nella _scena radice_ disabilitare lo script _'OnLoadStartScene'_</span><span class="sxs-lookup"><span data-stu-id="1039b-185">In the _root_ scene, disable the _'OnLoadStartScene'_ script</span></span>
3. <span data-ttu-id="1039b-186">_Trascinare e rilasciare_ una delle scene di test di tracciamento oculare descritte di seguito (o qualsiasi altra scena) nella visualizzazione _Gerarchia,_ come illustrato nello screenshot seguente.</span><span class="sxs-lookup"><span data-stu-id="1039b-186">_Drag and drop_ one of the eye tracking test scenes that are described below (or any other scene) into your _Hierarchy_ view as shown in the screenshot below.</span></span>

    ![Esempio di scena additiva](../images/eye-tracking/mrtk_et_additivescene.jpg)

4. <span data-ttu-id="1039b-188">Premere _Riproduci_</span><span class="sxs-lookup"><span data-stu-id="1039b-188">Press _Play_</span></span>

<span data-ttu-id="1039b-189">Si noti che il caricamento della scena secondaria come questo non è persistente: ciò significa che se si distribuisce l'app nel dispositivo HoloLens 2, verrà caricata solo la scena radice (presupponendo che venga visualizzata nella parte superiore delle impostazioni di compilazione).</span><span class="sxs-lookup"><span data-stu-id="1039b-189">Please note that loading the sub scene like this is not persistent: This means that if you deploy your app to the HoloLens 2 device, it will only load the root scene (assuming it appears at the top of your Build Settings).</span></span>
<span data-ttu-id="1039b-190">Inoltre, quando si condivide il progetto con altri utenti, le scene secondarie non vengono caricate automaticamente.</span><span class="sxs-lookup"><span data-stu-id="1039b-190">Also, when you share your project with others, the sub scenes are not automatically loaded.</span></span>

---

<span data-ttu-id="1039b-191">Ora che si è in grado di usare le scene di esempio di tracciamento oculare di MRTK, è possibile continuare con un approfondimento su come selezionare gli ologrammi con gli occhi: selezione della destinazione supportata dagli [occhi.](../input/eye-tracking/eye-tracking-target-selection.md)</span><span class="sxs-lookup"><span data-stu-id="1039b-191">Now that you know how to get the MRTK eye tracking example scenes to work, let's continue with diving deeper into how to select holograms with your eyes: [Eye-supported target selection](../input/eye-tracking/eye-tracking-target-selection.md).</span></span>

---
[<span data-ttu-id="1039b-192">Torna a "Tracciamento oculare in MixedRealityToolkit"</span><span class="sxs-lookup"><span data-stu-id="1039b-192">Back to "Eye tracking in the MixedRealityToolkit"</span></span>](../input/eye-tracking/eye-tracking-Main.md)

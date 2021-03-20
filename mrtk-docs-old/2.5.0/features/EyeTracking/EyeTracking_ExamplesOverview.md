---
title: EyeTracking_ExampleOverview
description: Esempio per compilare eyetracking in MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, EyeTracking,
ms.openlocfilehash: d92daf5bc423fb6c6b528b31a5908e8d9232271f
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2021
ms.locfileid: "104690051"
---
# <a name="eye-tracking-examples"></a><span data-ttu-id="0e1e5-104">Esempi di rilevamento degli occhi</span><span class="sxs-lookup"><span data-stu-id="0e1e5-104">Eye tracking examples</span></span>

<span data-ttu-id="0e1e5-105">Questo argomento descrive come iniziare rapidamente a usare la gestione degli occhi in MRTK tramite la compilazione degli esempi di rilevamento degli occhi di MRTK (assets/MRTK/examples/Demos/EyeTracking).</span><span class="sxs-lookup"><span data-stu-id="0e1e5-105">This topic describes how to quickly get started with eye tracking in MRTK by building on MRTK eye tracking examples (Assets/MRTK/Examples/Demos/EyeTracking).</span></span>
<span data-ttu-id="0e1e5-106">Questi esempi consentono di sperimentare una delle nuove funzionalità di input magiche: **rilevamento degli occhi**</span><span class="sxs-lookup"><span data-stu-id="0e1e5-106">These samples let you experience one of our new magical input capabilities: **Eye tracking**!</span></span>
<span data-ttu-id="0e1e5-107">La demo include diversi casi d'uso, che vanno da attivazioni basate sugli sguardi implicite a come combinare facilmente le informazioni relative a ciò che si sta osservando con l'input **vocale** e **manuale** .</span><span class="sxs-lookup"><span data-stu-id="0e1e5-107">The demo includes various use cases, ranging from implicit eye-based activations to how to seamlessly combine information about what you are looking at with **voice** and **hand** input.</span></span>
<span data-ttu-id="0e1e5-108">Ciò consente agli utenti di selezionare e spostare in modo rapido e semplice il contenuto olografico attraverso la visualizzazione semplicemente esaminando una destinazione e pronunciando _' Select '_ o eseguendo un gesto manuale.</span><span class="sxs-lookup"><span data-stu-id="0e1e5-108">This enables users to quickly and effortlessly select and move holographic content across their view simply by looking at a target and saying _'Select'_ or performing a hand gesture.</span></span>
<span data-ttu-id="0e1e5-109">Le demo includono anche un esempio di scorrimento con sguardo diretto, panning e zoom del testo e delle immagini in uno Slate.</span><span class="sxs-lookup"><span data-stu-id="0e1e5-109">The demos also include an example for eye-gaze-directed scroll, pan and zoom of text and images on a slate.</span></span>
<span data-ttu-id="0e1e5-110">Infine, viene fornito un esempio per la registrazione e la visualizzazione dell'attenzione visiva dell'utente su uno Slate 2D.</span><span class="sxs-lookup"><span data-stu-id="0e1e5-110">Finally, an example is provided for recording and visualizing the user's visual attention on a 2D slate.</span></span>
<span data-ttu-id="0e1e5-111">Nella sezione seguente sono disponibili ulteriori informazioni su tutti i diversi esempi nel pacchetto di esempio MRTK Eye Tracking (assets/MRTK/examples/Demos/EyeTracking):</span><span class="sxs-lookup"><span data-stu-id="0e1e5-111">In the following section, you will find more details on what each of the different samples in the MRTK eye tracking example package (Assets/MRTK/Examples/Demos/EyeTracking) includes:</span></span>

![Elenco di scene di rilevamento degli occhi](../Images/EyeTracking/mrtk_et_list_et_scenes.jpg)

<span data-ttu-id="0e1e5-113">La sezione seguente è una rapida panoramica delle informazioni sulle singole scene demo di rilevamento degli occhi.</span><span class="sxs-lookup"><span data-stu-id="0e1e5-113">The following section is a quick overview of what the individual eye tracking demo scenes are about.</span></span>
<span data-ttu-id="0e1e5-114">Le scene demo di MRTK Eye Tracking vengono [caricate in modo additivo](https://docs.unity3d.com/ScriptReference/SceneManagement.LoadSceneMode.Additive.html), che verrà illustrato di seguito come configurare.</span><span class="sxs-lookup"><span data-stu-id="0e1e5-114">The MRTK eye tracking demo scenes are [loaded additively](https://docs.unity3d.com/ScriptReference/SceneManagement.LoadSceneMode.Additive.html), which we will explain below how to set up.</span></span>

## <a name="overview-of-the-eye-tracking-demo-samples"></a><span data-ttu-id="0e1e5-115">Panoramica degli esempi di demo per la verifica degli occhi</span><span class="sxs-lookup"><span data-stu-id="0e1e5-115">Overview of the eye tracking demo samples</span></span>

### <a name="eye-supported-target-selection"></a>[<span data-ttu-id="0e1e5-116">**Selezione della destinazione supportata dagli occhi**</span><span class="sxs-lookup"><span data-stu-id="0e1e5-116">**Eye-Supported Target Selection**</span></span>](EyeTracking_TargetSelection.md)

<span data-ttu-id="0e1e5-117">In questa esercitazione viene illustrata la facilità di accesso ai dati degli occhi per selezionare le destinazioni.</span><span class="sxs-lookup"><span data-stu-id="0e1e5-117">This tutorial showcases the ease of accessing eye gaze data to select targets.</span></span>
<span data-ttu-id="0e1e5-118">Include un esempio di commenti impercettibili ma potenti per fornire all'utente la certezza che una destinazione sia concentrata senza sopraffare.</span><span class="sxs-lookup"><span data-stu-id="0e1e5-118">It includes an example for subtle yet powerful feedback to provide the user with the confidence that a target is focused without being overwhelming.</span></span>
<span data-ttu-id="0e1e5-119">Inoltre, è disponibile un semplice esempio di notifiche intelligenti che scompaiono automaticamente dopo la lettura.</span><span class="sxs-lookup"><span data-stu-id="0e1e5-119">In addition, there is a simple example of smart notifications that automatically disappear after being read.</span></span>

<span data-ttu-id="0e1e5-120">**Riepilogo**: selezioni di destinazione rapide e veloci con una combinazione di occhi, input vocale e manuale.</span><span class="sxs-lookup"><span data-stu-id="0e1e5-120">**Summary**: Fast and effortless target selections using a combination of eyes, voice and hand input.</span></span>

### <a name="eye-supported-navigation"></a>[<span data-ttu-id="0e1e5-121">**Navigazione con supporto oculistico**</span><span class="sxs-lookup"><span data-stu-id="0e1e5-121">**Eye-Supported Navigation**</span></span>](EyeTracking_Navigation.md)

<span data-ttu-id="0e1e5-122">Si supponga di leggere alcune informazioni su una visualizzazione distante o sull'e-Reader e quando si raggiunge la fine del testo visualizzato, il testo scorre automaticamente verso l'alto per rivelare altro contenuto.</span><span class="sxs-lookup"><span data-stu-id="0e1e5-122">Imagine that you are reading some information on a distant display or your e-reader and when you reach the end of the displayed text, the text automatically scrolls up to reveal more content.</span></span>
<span data-ttu-id="0e1e5-123">O come ingrandire lo zoom direttamente verso la posizione in cui si è cercato?</span><span class="sxs-lookup"><span data-stu-id="0e1e5-123">Or how about magically zooming directly toward where you were looking at?</span></span>
<span data-ttu-id="0e1e5-124">Di seguito sono riportati alcuni esempi illustrati in questa esercitazione sulla navigazione con supporto oculistico.</span><span class="sxs-lookup"><span data-stu-id="0e1e5-124">These are some of the examples showcased in this tutorial regarding eye-supported navigation.</span></span>
<span data-ttu-id="0e1e5-125">Inoltre, è disponibile un esempio per la rotazione senza mani di ologrammi 3D, facendo in modo che ruotino automaticamente in base allo stato attivo corrente.</span><span class="sxs-lookup"><span data-stu-id="0e1e5-125">In addition, there is an example for hands-free rotation of 3D holograms by making them automatically rotate based on your current focus.</span></span>

<span data-ttu-id="0e1e5-126">**Riepilogo**: scorrimento, panoramica, zoom, rotazione 3D con una combinazione di occhi, input vocale e manuale.</span><span class="sxs-lookup"><span data-stu-id="0e1e5-126">**Summary**: Scroll, pan, zoom, 3D rotation using a combination of eyes, voice and hand input.</span></span>

### <a name="eye-supported-positioning"></a>[<span data-ttu-id="0e1e5-127">**Posizionamento con supporto per gli occhi**</span><span class="sxs-lookup"><span data-stu-id="0e1e5-127">**Eye-Supported Positioning**</span></span>](EyeTracking_Positioning.md)

<span data-ttu-id="0e1e5-128">Questa esercitazione illustra uno scenario di input denominato [put-that-](https://youtu.be/CbIn8p4_4CQ) here risalendo alla ricerca dal MIT Media Lab nel primo 1980 con input Eye, hand e Voice.</span><span class="sxs-lookup"><span data-stu-id="0e1e5-128">This tutorial shows an input scenario called [Put-That-There](https://youtu.be/CbIn8p4_4CQ) dating back to research from the MIT Media Lab in the early 1980's with eye, hand and voice input.</span></span>
<span data-ttu-id="0e1e5-129">L'idea è semplice: trarre vantaggio dagli occhi per la selezione e il posizionamento rapidi delle destinazioni.</span><span class="sxs-lookup"><span data-stu-id="0e1e5-129">The idea is simple: Benefit from your eyes for fast target selection and positioning.</span></span>
<span data-ttu-id="0e1e5-130">Basta osservare un ologramma e pronunciare _"put this"_, esaminare il punto in cui si vuole posizionarlo e pronunciare _"There!"_.</span><span class="sxs-lookup"><span data-stu-id="0e1e5-130">Simply look at a hologram and say _'put this'_, look over where you want to place it and say _'there!'_.</span></span>
<span data-ttu-id="0e1e5-131">Per posizionare con maggiore precisione l'ologramma, è possibile usare input aggiuntivi da Hands, Voice o Controllers.</span><span class="sxs-lookup"><span data-stu-id="0e1e5-131">For more precisely positioning your hologram, you can use additional input from your hands, voice or controllers.</span></span>

<span data-ttu-id="0e1e5-132">**Riepilogo**: posizionamento degli ologrammi con gli occhi, input vocale e mano (*trascinamento della selezione*).</span><span class="sxs-lookup"><span data-stu-id="0e1e5-132">**Summary**: Positioning holograms using eyes, voice and hand input (*drag-and-drop*).</span></span> <span data-ttu-id="0e1e5-133">Dispositivi di scorrimento supportati dagli occhi con occhi e mani.</span><span class="sxs-lookup"><span data-stu-id="0e1e5-133">Eye-supported sliders using eyes + hands.</span></span>

### <a name="visualization-of-visual-attention"></a><span data-ttu-id="0e1e5-134">**Visualizzazione dell'attenzione visiva**</span><span class="sxs-lookup"><span data-stu-id="0e1e5-134">**Visualization of visual attention**</span></span>

<span data-ttu-id="0e1e5-135">I dati basati sul punto in cui gli utenti appaiono rendono uno strumento estremamente potente per valutare l'usabilità di una progettazione e identificare i problemi nei flussi di lavoro efficienti.</span><span class="sxs-lookup"><span data-stu-id="0e1e5-135">Data based on where users look makes an immensely powerful tool to assess usability of a design and to identify problems in efficient work streams.</span></span>
<span data-ttu-id="0e1e5-136">Questa esercitazione illustra diverse visualizzazioni di rilevamento degli occhi e il modo in cui si adattano a esigenze diverse.</span><span class="sxs-lookup"><span data-stu-id="0e1e5-136">This tutorial discusses different eye tracking visualizations and how they fit different needs.</span></span>
<span data-ttu-id="0e1e5-137">Sono disponibili esempi di base per la registrazione e il caricamento di dati di rilevamento degli occhi ed esempi su come visualizzarli.</span><span class="sxs-lookup"><span data-stu-id="0e1e5-137">We provide basic examples for logging and loading eye tracking data and examples for how to visualize them.</span></span>

<span data-ttu-id="0e1e5-138">**Riepilogo**: mappa di attenzione bidimensionale (heatmaps) in slate.</span><span class="sxs-lookup"><span data-stu-id="0e1e5-138">**Summary**: Two-dimensional attention map (heatmaps) on slates.</span></span> <span data-ttu-id="0e1e5-139">Registrazione & la riproduzione dei dati di rilevamento degli occhi.</span><span class="sxs-lookup"><span data-stu-id="0e1e5-139">Recording & replaying eye tracking data.</span></span>

## <a name="setting-up-the-mrtk-eye-tracking-samples"></a><span data-ttu-id="0e1e5-140">Configurazione degli esempi di rilevamento degli occhi di MRTK</span><span class="sxs-lookup"><span data-stu-id="0e1e5-140">Setting up the MRTK eye tracking samples</span></span>

### <a name="prerequisites"></a><span data-ttu-id="0e1e5-141">Prerequisiti</span><span class="sxs-lookup"><span data-stu-id="0e1e5-141">Prerequisites</span></span>

<span data-ttu-id="0e1e5-142">Si noti che l'uso degli esempi di rilevamento degli occhi sul dispositivo richiede un HoloLens 2 e un pacchetto dell'app di esempio compilato con la funzionalità di "input dello sguardo" nel AppXManifest del pacchetto.</span><span class="sxs-lookup"><span data-stu-id="0e1e5-142">Note that using the eye tracking samples on device requires a HoloLens 2 and a sample app package that is built with the "Gaze Input" capability on the package's AppXManifest.</span></span>

<span data-ttu-id="0e1e5-143">Per usare questi esempi di monitoraggio degli occhi nel dispositivo, assicurarsi di seguire [questi passaggi](EyeTracking_BasicSetup.md#testing-your-unity-app-on-a-hololens-2) prima di compilare l'app in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="0e1e5-143">In order to use these eye tracking samples on device, make sure to follow [these steps](EyeTracking_BasicSetup.md#testing-your-unity-app-on-a-hololens-2) prior to building the app in Visual Studio.</span></span>

### <a name="1-load-eyetrackingdemo-00-rootsceneunity"></a><span data-ttu-id="0e1e5-144">1. caricare EyeTrackingDemo-00-RootScene. Unity</span><span class="sxs-lookup"><span data-stu-id="0e1e5-144">1. Load EyeTrackingDemo-00-RootScene.unity</span></span>

<span data-ttu-id="0e1e5-145">*EyeTrackingDemo-00-RootScene* è la scena di base (_radice_) con tutti i componenti di MRTK principali inclusi.</span><span class="sxs-lookup"><span data-stu-id="0e1e5-145">The *EyeTrackingDemo-00-RootScene* is the base (_root_) scene that has all the core MRTK components included.</span></span>
<span data-ttu-id="0e1e5-146">Questa è la scena che è necessario caricare per prima e da cui verrà eseguita la demo di rilevamento degli occhi.</span><span class="sxs-lookup"><span data-stu-id="0e1e5-146">This is the scene that you need to load first and from which you will run the eye tracking demos.</span></span>
<span data-ttu-id="0e1e5-147">È disponibile un menu di scena grafica che consente di passare facilmente tra i diversi esempi di rilevamento degli occhi, che verranno caricati in modo [additivo](https://docs.unity3d.com/ScriptReference/SceneManagement.LoadSceneMode.Additive.html).</span><span class="sxs-lookup"><span data-stu-id="0e1e5-147">It features a graphical scene menu that allows you to easily switch between the different eye tracking samples which will be [loaded additively](https://docs.unity3d.com/ScriptReference/SceneManagement.LoadSceneMode.Additive.html).</span></span>

![Menu scene nell'esempio di monitoraggio degli occhi](../Images/EyeTracking/mrtk_et_scenemenu.jpg)

<span data-ttu-id="0e1e5-149">La scena radice include alcuni componenti di base che vengono mantenuti tra le scene caricate in modo additivo, ad esempio i profili configurati per MRTK e la fotocamera della scena.</span><span class="sxs-lookup"><span data-stu-id="0e1e5-149">The root scene includes a few core components that will persist across the additively loaded scenes, such as the MRTK configured profiles and scene camera.</span></span>
<span data-ttu-id="0e1e5-150">Il _MixedRealityBasicSceneSetup_ (vedere la schermata riportata di seguito) include uno script che caricherà automaticamente la scena a cui si fa riferimento all'avvio.</span><span class="sxs-lookup"><span data-stu-id="0e1e5-150">The _MixedRealityBasicSceneSetup_ (see screenshot below) includes a script that will automatically load the referenced scene on startup.</span></span>
<span data-ttu-id="0e1e5-151">Per impostazione predefinita, il valore è _EyeTrackingDemo-02-TargetSelection_.</span><span class="sxs-lookup"><span data-stu-id="0e1e5-151">By default, this is _EyeTrackingDemo-02-TargetSelection_.</span></span>  

![Esempio per lo script OnLoadStartScene](../Images/EyeTracking/mrtk_et_onloadstartscene.jpg)

### <a name="2-adding-scenes-to-the-build-menu"></a><span data-ttu-id="0e1e5-153">2. aggiunta di scene al menu Compila</span><span class="sxs-lookup"><span data-stu-id="0e1e5-153">2. Adding scenes to the build menu</span></span>

<span data-ttu-id="0e1e5-154">Per caricare le scene additive durante la fase di esecuzione, è necessario aggiungere prima di tutto le scene _nelle impostazioni di compilazione, > nel menu Compila_ .</span><span class="sxs-lookup"><span data-stu-id="0e1e5-154">To load additive scenes during runtime, you must add these scenes to your _Build Settings -> Scenes in Build_ menu first.</span></span>
<span data-ttu-id="0e1e5-155">È importante che la scena radice venga visualizzata come prima scena nell'elenco:</span><span class="sxs-lookup"><span data-stu-id="0e1e5-155">It is important that the root scene is shown as the first scene in the list:</span></span>

![Menu della scena delle impostazioni di compilazione per gli esempi di rilevamento degli occhi](../Images/EyeTracking/mrtk_et_build_settings.jpg)

### <a name="3-play-the-eye-tracking-samples-in-the-unity-editor"></a><span data-ttu-id="0e1e5-157">3. riprodurre gli esempi di rilevamento degli occhi nell'editor di Unity</span><span class="sxs-lookup"><span data-stu-id="0e1e5-157">3. Play the eye tracking samples in the Unity editor</span></span>

<span data-ttu-id="0e1e5-158">Dopo aver aggiunto le scene di rilevamento degli occhi alle impostazioni di compilazione e aver caricato _EyeTrackingDemo-00-RootScene_, è possibile verificare che sia lo script _' OnLoadStartScene '_ collegato al _MixedRealityBasicSceneSetup_ GameObject abilitato?</span><span class="sxs-lookup"><span data-stu-id="0e1e5-158">After adding the eye tracking scenes to the Build Settings and loading the _EyeTrackingDemo-00-RootScene_, there is one last thing you may want to check: Is the _'OnLoadStartScene'_ script that is attached to the _MixedRealityBasicSceneSetup_ GameObject enabled?</span></span> <span data-ttu-id="0e1e5-159">In questo modo, la scena radice sa quale scena demo caricare per prima.</span><span class="sxs-lookup"><span data-stu-id="0e1e5-159">This is to let the root scene know which demo scene to load first.</span></span>

![Esempio per lo script OnLoad_StartScene](../Images/EyeTracking/mrtk_et_onloadstartscene.jpg)

<span data-ttu-id="0e1e5-161">Eseguiamo il roll</span><span class="sxs-lookup"><span data-stu-id="0e1e5-161">Let's roll!</span></span> <span data-ttu-id="0e1e5-162">Premere _"Play"_.</span><span class="sxs-lookup"><span data-stu-id="0e1e5-162">Hit _"Play"_!</span></span>
<span data-ttu-id="0e1e5-163">Verranno visualizzate diverse gemme e il menu della scena nella parte superiore.</span><span class="sxs-lookup"><span data-stu-id="0e1e5-163">You should see several gems appear and the scene menu at the top.</span></span>

![Schermata di esempio dalla scena Select di ET target](../Images/EyeTracking/mrtk_et_targetselect.png)

<span data-ttu-id="0e1e5-165">Si noti anche un piccolo cerchio semitrasparente al centro della visualizzazione del gioco.</span><span class="sxs-lookup"><span data-stu-id="0e1e5-165">You should also notice a small semitransparent circle at the center of your game view.</span></span>
<span data-ttu-id="0e1e5-166">Questo funge da indicatore (cursore) dello _sguardo simulato_: è sufficiente premere il _pulsante destro del mouse_ e spostare il mouse per modificarne la posizione.</span><span class="sxs-lookup"><span data-stu-id="0e1e5-166">This acts as an indicator (cursor) of your _simulated eye gaze_: Simply press down the _right mouse button_ and move the mouse to change its position.</span></span>
<span data-ttu-id="0e1e5-167">Quando si passa il cursore sulle gemme, si noterà che il cursore si blocca al centro della gemma attualmente visualizzata.</span><span class="sxs-lookup"><span data-stu-id="0e1e5-167">When the cursor is hovering over the gems, you will notice that it will snap to the center of the currently viewed gem.</span></span>
<span data-ttu-id="0e1e5-168">Questo è un ottimo modo per verificare se gli eventi vengono attivati come previsto quando si esegue la _ricerca_ in una destinazione.</span><span class="sxs-lookup"><span data-stu-id="0e1e5-168">This is a great way to test if events are triggered as expected when _"looking"_ at a target.</span></span>
<span data-ttu-id="0e1e5-169">Tenere presente che l' _occhio simulato_ tramite il controllo del mouse è un supplemento piuttosto scarso ai nostri movimenti oculari rapidi e non intenzionali.</span><span class="sxs-lookup"><span data-stu-id="0e1e5-169">Be aware that the _simulated eye gaze_ via mouse control is a rather poor supplement to our rapid and unintentional eye movements.</span></span>
<span data-ttu-id="0e1e5-170">Tuttavia, è ideale per testare la funzionalità di base prima di eseguire l'iterazione sulla progettazione distribuendo il dispositivo nel dispositivo HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="0e1e5-170">However, it is great for testing the basic functionality before iterating on the design by deploying it to the HoloLens 2 device.</span></span>
<span data-ttu-id="0e1e5-171">Tornando alla scena di esempio di analisi degli occhi: la gemma ruota fino a quando non viene analizzata e può essere distrutta "cercando" e...</span><span class="sxs-lookup"><span data-stu-id="0e1e5-171">Returning to our eye tracking sample scene: The gem rotates as long as being looked at and can be destroyed by "looking" at it and ...</span></span>

- <span data-ttu-id="0e1e5-172">Premere _invio_ (che simula la dicitura "Select")</span><span class="sxs-lookup"><span data-stu-id="0e1e5-172">Pressing _Enter_ (which simulates saying "select")</span></span>
- <span data-ttu-id="0e1e5-173">Dicitura _"Seleziona"_ nel microfono</span><span class="sxs-lookup"><span data-stu-id="0e1e5-173">Saying _"select"_ into your microphone</span></span>
- <span data-ttu-id="0e1e5-174">Quando si preme _spazio_ per visualizzare l'input della mano simulata, fare clic con il pulsante sinistro del mouse per eseguire un pizzico simulato</span><span class="sxs-lookup"><span data-stu-id="0e1e5-174">While pressing _Space_ to show the simulated hand input, click the left mouse button to perform a simulated pinch</span></span>

<span data-ttu-id="0e1e5-175">Viene descritto in dettaglio come è possibile ottenere queste interazioni nell'esercitazione sulla [**selezione di destinazioni supportata dagli occhi**](EyeTracking_TargetSelection.md) .</span><span class="sxs-lookup"><span data-stu-id="0e1e5-175">We describe in more detail how you can achieve these interactions in our [**Eye-Supported Target Selection**](EyeTracking_TargetSelection.md) tutorial.</span></span>

<span data-ttu-id="0e1e5-176">Quando si sposta il cursore verso l'alto sulla barra dei menu superiore della scena, si noterà che l'elemento attualmente spostato viene evidenziato in modo impercettibile.</span><span class="sxs-lookup"><span data-stu-id="0e1e5-176">When moving the cursor up to the top menu bar in the scene, you will notice that the currently hovered item will highlight subtly.</span></span>
<span data-ttu-id="0e1e5-177">È possibile selezionare l'elemento attualmente evidenziato usando uno dei metodi di commit descritti sopra (ad esempio, premendo _invio_).</span><span class="sxs-lookup"><span data-stu-id="0e1e5-177">You can select the currently highlighted item by using one of the above described commit methods (e.g., pressing _Enter_).</span></span>
<span data-ttu-id="0e1e5-178">In questo modo è possibile passare tra le diverse scene di esempio di tracking degli occhi.</span><span class="sxs-lookup"><span data-stu-id="0e1e5-178">This way you can switch between the different eye tracking sample scenes.</span></span>

### <a name="4-how-to-test-specific-sub-scenes"></a><span data-ttu-id="0e1e5-179">4. come testare le sottoscene specifiche</span><span class="sxs-lookup"><span data-stu-id="0e1e5-179">4. How to test specific sub scenes</span></span>

<span data-ttu-id="0e1e5-180">Quando si lavora in uno scenario specifico, è possibile che non si desideri eseguire ogni volta il menu della scena.</span><span class="sxs-lookup"><span data-stu-id="0e1e5-180">When working on a specific scenario, you may not want to go through the scene menu every time.</span></span>
<span data-ttu-id="0e1e5-181">In alternativa, è possibile iniziare direttamente dalla scena in cui si sta lavorando quando si preme il pulsante _Riproduci_ .</span><span class="sxs-lookup"><span data-stu-id="0e1e5-181">Instead, you may want to start directly from the scene that you are currently working on when pressing the _Play_ button.</span></span>
<span data-ttu-id="0e1e5-182">non è un problema.</span><span class="sxs-lookup"><span data-stu-id="0e1e5-182">No problem!</span></span> <span data-ttu-id="0e1e5-183">Ecco cosa è possibile fare:</span><span class="sxs-lookup"><span data-stu-id="0e1e5-183">Here is what you can do:</span></span>

1. <span data-ttu-id="0e1e5-184">Caricare la scena _radice_</span><span class="sxs-lookup"><span data-stu-id="0e1e5-184">Load the _root_ scene</span></span>
2. <span data-ttu-id="0e1e5-185">Nella scena _radice_ disabilitare lo script _' OnLoadStartScene '_</span><span class="sxs-lookup"><span data-stu-id="0e1e5-185">In the _root_ scene, disable the _'OnLoadStartScene'_ script</span></span>
3. <span data-ttu-id="0e1e5-186">_Trascinare e rilasciare_ una delle scene di test di rilevamento degli occhi descritte di seguito (o qualsiasi altra scena) nella visualizzazione _gerarchia_ , come illustrato nella schermata seguente.</span><span class="sxs-lookup"><span data-stu-id="0e1e5-186">_Drag and drop_ one of the eye tracking test scenes that are described below (or any other scene) into your _Hierarchy_ view as shown in the screenshot below.</span></span>

    ![Esempio di scena additiva](../Images/EyeTracking/mrtk_et_additivescene.jpg)

4. <span data-ttu-id="0e1e5-188">Premere _Play_</span><span class="sxs-lookup"><span data-stu-id="0e1e5-188">Press _Play_</span></span>

<span data-ttu-id="0e1e5-189">Si noti che il caricamento della scena secondaria come questa non è persistente: ciò significa che se si distribuisce l'app nel dispositivo HoloLens 2, viene caricata solo la scena radice (presupponendo che venga visualizzata nella parte superiore delle impostazioni di compilazione).</span><span class="sxs-lookup"><span data-stu-id="0e1e5-189">Please note that loading the sub scene like this is not persistent: This means that if you deploy your app to the HoloLens 2 device, it will only load the root scene (assuming it appears at the top of your Build Settings).</span></span>
<span data-ttu-id="0e1e5-190">Inoltre, quando si condivide il progetto con altri utenti, le scene secondarie non vengono caricate automaticamente.</span><span class="sxs-lookup"><span data-stu-id="0e1e5-190">Also, when you share your project with others, the sub scenes are not automatically loaded.</span></span>

---

<span data-ttu-id="0e1e5-191">Ora che si è appreso come usare le scene di esempio di MRTK Eye Tracking, procedere con l'approfondimento su come selezionare gli ologrammi con gli occhi: [selezione della destinazione supportata dagli occhi](EyeTracking_TargetSelection.md).</span><span class="sxs-lookup"><span data-stu-id="0e1e5-191">Now that you know how to get the MRTK eye tracking example scenes to work, let's continue with diving deeper into how to select holograms with your eyes: [Eye-supported target selection](EyeTracking_TargetSelection.md).</span></span>

---
[<span data-ttu-id="0e1e5-192">Torna a "Eye Tracking in the MixedRealityToolkit"</span><span class="sxs-lookup"><span data-stu-id="0e1e5-192">Back to "Eye tracking in the MixedRealityToolkit"</span></span>](EyeTracking_Main.md)

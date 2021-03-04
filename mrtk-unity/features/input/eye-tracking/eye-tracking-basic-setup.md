---
title: EyeTracking_BasicSetup
description: Come configurare la gestione degli occhi in MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, monitoraggio degli occhi,
ms.openlocfilehash: daa15ee6966c9e26be45a3918ee585dc42b00610
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/03/2021
ms.locfileid: "101782614"
---
# <a name="getting-started-with-eye-tracking-in-mrtk"></a><span data-ttu-id="af388-104">Introduzione a Eye Tracking in MRTK</span><span class="sxs-lookup"><span data-stu-id="af388-104">Getting started with eye tracking in MRTK</span></span>

<span data-ttu-id="af388-105">Questa pagina illustra come configurare la scena MRTK Unity per l'uso della traccia degli occhi nell'app.</span><span class="sxs-lookup"><span data-stu-id="af388-105">This page covers how to set up your Unity MRTK scene to use eye tracking in your app.</span></span>
<span data-ttu-id="af388-106">Di seguito si presuppone che si inizi con una nuova scena.</span><span class="sxs-lookup"><span data-stu-id="af388-106">The following assumes you are starting out with a fresh new scene.</span></span>
<span data-ttu-id="af388-107">In alternativa, è possibile consultare gli [esempi di MRTK Eye Tracking](../../example-scenes/eye-tracking-examples-overview.md) già configurati con numerosi esempi eccezionali che è possibile compilare direttamente in.</span><span class="sxs-lookup"><span data-stu-id="af388-107">Alternatively, you can check out our already configured [MRTK eye tracking examples](../../example-scenes/eye-tracking-examples-overview.md) with tons of great examples that you can directly build on.</span></span>

## <a name="eye-tracking-requirements-checklist"></a><span data-ttu-id="af388-108">Elenco di controllo dei requisiti di rilevamento degli occhi</span><span class="sxs-lookup"><span data-stu-id="af388-108">Eye tracking requirements checklist</span></span>

<span data-ttu-id="af388-109">Per il corretto funzionamento del rilevamento degli occhi, è necessario soddisfare i requisiti seguenti.</span><span class="sxs-lookup"><span data-stu-id="af388-109">For eye tracking to work correctly, the following requirements must be met.</span></span>
<span data-ttu-id="af388-110">Se non si ha familiarità con la registrazione degli occhi su HoloLens 2 e il modo in cui la verifica degli occhi è configurata in MRTK, non è un problema.</span><span class="sxs-lookup"><span data-stu-id="af388-110">If you are new to eye tracking on HoloLens 2 and to how eye tracking is set up in MRTK, don't worry!</span></span>
<span data-ttu-id="af388-111">Verranno illustrati in dettaglio come indirizzarli a ognuno di essi.</span><span class="sxs-lookup"><span data-stu-id="af388-111">We will go into detail on how to address each of them further below.</span></span>

1. <span data-ttu-id="af388-112">È necessario aggiungere al sistema di input un _"provider di dati occhio a occhio"_ .</span><span class="sxs-lookup"><span data-stu-id="af388-112">An _'Eye Gaze Data Provider'_ must be added to the input system.</span></span> <span data-ttu-id="af388-113">Che fornisce i dati di rilevamento degli occhi dalla piattaforma.</span><span class="sxs-lookup"><span data-stu-id="af388-113">This provides eye tracking data from the platform.</span></span>
2. <span data-ttu-id="af388-114">La funzionalità _' GazeInput '_ deve essere abilitata nel manifesto dell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="af388-114">The _'GazeInput'_ capability must be enabled in the application manifest.</span></span>
   <span data-ttu-id="af388-115">**Questa funzionalità può essere impostata in Unity 2019, ma in Unity 2018 e versioni precedenti questa funzionalità è disponibile solo in Visual Studio e tramite lo strumento di compilazione MRTK**</span><span class="sxs-lookup"><span data-stu-id="af388-115">**This capability can be set in Unity 2019, but in Unity 2018 and earlier this capability is only available in Visual Studio and through the MRTK build tool**</span></span>
3. <span data-ttu-id="af388-116">Il HoloLens **deve** essere a occhio calibrato per l'utente corrente.</span><span class="sxs-lookup"><span data-stu-id="af388-116">The HoloLens **must** be eye calibrated for the current user.</span></span> <span data-ttu-id="af388-117">Vedere l' [esempio per rilevare se un utente è calibrato o meno a occhio](eye-tracking-is-user-calibrated.md).</span><span class="sxs-lookup"><span data-stu-id="af388-117">Check out our [sample for detecting whether a user is eye calibrated or not](eye-tracking-is-user-calibrated.md).</span></span>

### <a name="a-note-on-the-gazeinput-capability"></a><span data-ttu-id="af388-118">Una nota sulla funzionalità GazeInput</span><span class="sxs-lookup"><span data-stu-id="af388-118">A note on the GazeInput capability</span></span>

<span data-ttu-id="af388-119">Gli strumenti di compilazione forniti da MRTK, ad esempio il Toolkit di realtà mista-> Utilities-> finestra di compilazione, possono abilitare automaticamente la funzionalità GazeInput.</span><span class="sxs-lookup"><span data-stu-id="af388-119">The MRTK-provided build tooling (i.e. Mixed Reality Toolkit -> Utilities -> Build Window) can automatically enable the GazeInput capability for you.</span></span> <span data-ttu-id="af388-120">Per eseguire questa operazione, è necessario assicurarsi che la funzionalità di input di sguardi sia selezionata nella scheda ' appx Build Options ' (opzioni di compilazione):</span><span class="sxs-lookup"><span data-stu-id="af388-120">In order to do this, you need to make sure that the 'Gaze Input Capability' is checked on the 'Appx Build Options' tab:</span></span>

![Strumenti di compilazione MRTK](../../images/eye-tracking/mrtk_et_buildsetup.png)

<span data-ttu-id="af388-122">Questo strumento consente di trovare il manifesto di AppX dopo il completamento della compilazione Unity e di aggiungere manualmente la funzionalità GazeInput.</span><span class="sxs-lookup"><span data-stu-id="af388-122">This tooling will find the AppX manifest after the Unity build is completed and manually add the GazeInput capability.</span></span>
<span data-ttu-id="af388-123">**Prima di unity 2019, questi strumenti non sono attivi quando si usa la finestra di compilazione incorporata di Unity** (ad esempio, le impostazioni di compilazione di file >).</span><span class="sxs-lookup"><span data-stu-id="af388-123">**Prior to Unity 2019, this tooling is NOT active when using Unity's built-in Build Window** (i.e. File -> Build Settings).</span></span>

<span data-ttu-id="af388-124">Prima di Unity 2019, quando si usa la finestra di compilazione di Unity, è necessario aggiungere manualmente la funzionalità dopo la compilazione Unity, come indicato di seguito:</span><span class="sxs-lookup"><span data-stu-id="af388-124">Prior to Unity 2019, when using Unity's build window, the capability will need to be manually added after the Unity build, as follows:</span></span>

1. <span data-ttu-id="af388-125">Aprire il progetto di Visual Studio compilato e quindi aprire il _pacchetto "Package. appxmanifest"_ nella soluzione.</span><span class="sxs-lookup"><span data-stu-id="af388-125">Open your compiled Visual Studio project and then open the _'Package.appxmanifest'_ in your solution.</span></span>
2. <span data-ttu-id="af388-126">Assicurarsi di selezionare la casella di controllo _' GazeInput '_ in _funzionalità_.</span><span class="sxs-lookup"><span data-stu-id="af388-126">Make sure to tick the _'GazeInput'_ checkbox under _Capabilities_.</span></span> <span data-ttu-id="af388-127">Se non viene visualizzata la funzionalità _' GazeInput '_ , verificare che il sistema soddisfi i [prerequisiti per l'uso di MRTK](https://docs.microsoft.com/windows/mixed-reality/develop/install-the-tools) (in particolare la versione Windows SDK).</span><span class="sxs-lookup"><span data-stu-id="af388-127">If you don't see a _'GazeInput'_ capability, check that your system meets the [prerequisites for using MRTK](https://docs.microsoft.com/windows/mixed-reality/develop/install-the-tools) (in particular the Windows SDK version).</span></span>

<span data-ttu-id="af388-128">_Nota:_ È necessario eseguire questa operazione solo se si compila in una nuova cartella di compilazione.</span><span class="sxs-lookup"><span data-stu-id="af388-128">_Please note:_ You only have to do this if you build into a new build folder.</span></span>
<span data-ttu-id="af388-129">Ciò significa che se è già stato compilato il progetto Unity e si configura il appxmanifest prima e ora la destinazione della stessa cartella, non sarà necessario riapplicare le modifiche.</span><span class="sxs-lookup"><span data-stu-id="af388-129">This means that if you had already built your Unity project and set up the appxmanifest before and now target the same folder again, you will not need to reapply your changes.</span></span>

## <a name="setting-up-eye-tracking-step-by-step"></a><span data-ttu-id="af388-130">Procedura dettagliata per la configurazione del monitoraggio degli occhi</span><span class="sxs-lookup"><span data-stu-id="af388-130">Setting up eye tracking step-by-step</span></span>

### <a name="setting-up-the-scene"></a><span data-ttu-id="af388-131">Impostazione della scena</span><span class="sxs-lookup"><span data-stu-id="af388-131">Setting up the scene</span></span>

<span data-ttu-id="af388-132">Per configurare il _MixedRealityToolkit_ , è sufficiente fare clic su _' mixed reality Toolkit-> configure.. .'_</span><span class="sxs-lookup"><span data-stu-id="af388-132">Set up the _MixedRealityToolkit_ by simply clicking _'Mixed Reality Toolkit -> Configure…'_</span></span> <span data-ttu-id="af388-133">nella barra dei menu.</span><span class="sxs-lookup"><span data-stu-id="af388-133">in the menu bar.</span></span>

![Configurazione di MRTK](../../images/eye-tracking/mrtk_setup_configure.jpg)

### <a name="setting-up-the-mrtk-profiles-required-for-eye-tracking"></a><span data-ttu-id="af388-135">Configurazione dei profili MRTK necessari per la verifica degli occhi</span><span class="sxs-lookup"><span data-stu-id="af388-135">Setting up the MRTK profiles required for eye tracking</span></span>

<span data-ttu-id="af388-136">Dopo aver configurato la scena MRTK, verrà richiesto di scegliere un profilo per MRTK.</span><span class="sxs-lookup"><span data-stu-id="af388-136">After setting up your MRTK scene, you will be asked to choose a profile for MRTK.</span></span>
<span data-ttu-id="af388-137">È sufficiente selezionare _DefaultMixedRealityToolkitConfigurationProfile_ e quindi selezionare l'opzione _"copia & Personalizza"_ .</span><span class="sxs-lookup"><span data-stu-id="af388-137">You can simply select _DefaultMixedRealityToolkitConfigurationProfile_ and then select the _'Copy & Customize'_ option.</span></span>

![Profilo MRTK](../../images/eye-tracking/mrtk_setup_configprofile.jpg)

### <a name="create-an-eye-gaze-data-provider"></a><span data-ttu-id="af388-139">Creare un "provider di dati con occhio sguardo"</span><span class="sxs-lookup"><span data-stu-id="af388-139">Create an "eye gaze data provider"</span></span>

- <span data-ttu-id="af388-140">Fare clic sulla scheda _"input"_ nel profilo MRTK.</span><span class="sxs-lookup"><span data-stu-id="af388-140">Click on the _'Input'_ tab in your MRTK profile.</span></span>
- <span data-ttu-id="af388-141">Per modificare quello predefinito ( _"DefaultMixedRealityInputSystemProfile"_ ), fare clic sul pulsante _"Clona"_ accanto.</span><span class="sxs-lookup"><span data-stu-id="af388-141">To edit the default one ( _'DefaultMixedRealityInputSystemProfile'_ ), click the _'Clone'_ button next to it.</span></span> <span data-ttu-id="af388-142">Verrà visualizzato il menu _' clona profilo '_ .</span><span class="sxs-lookup"><span data-stu-id="af388-142">A _'Clone Profile'_ menu appears.</span></span> <span data-ttu-id="af388-143">È sufficiente fare clic su _' clone '_ nella parte inferiore del menu.</span><span class="sxs-lookup"><span data-stu-id="af388-143">Simply click on _'Clone'_ at the bottom of that menu.</span></span>
- <span data-ttu-id="af388-144">Fare doppio clic sul nuovo profilo di input, espandere _"provider di dati di input"_ e selezionare _"+ Aggiungi provider di dati"_.</span><span class="sxs-lookup"><span data-stu-id="af388-144">Double click on your new input profile, expand _'Input Data Providers'_, and select _'+ Add Data Provider'_.</span></span>
- <span data-ttu-id="af388-145">Creare un nuovo provider di dati:</span><span class="sxs-lookup"><span data-stu-id="af388-145">Create a new data provider:</span></span>
  - <span data-ttu-id="af388-146">In **tipo** selezionare _' Microsoft. MixedReality. Toolkit. WindowsMixedReality. input '_  ->  _' WindowsMixedRealityEyeGazeDataProvider '_</span><span class="sxs-lookup"><span data-stu-id="af388-146">Under **Type** select _'Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input'_ -> _'WindowsMixedRealityEyeGazeDataProvider'_</span></span>
  - <span data-ttu-id="af388-147">Per le **piattaforme** selezionare _"universale di Windows"_.</span><span class="sxs-lookup"><span data-stu-id="af388-147">For **Platform(s)** select _'Windows Universal'_.</span></span>

![Provider di dati MRTK](../../images/eye-tracking/mrtk_setup_eyes_dataprovider.jpg)

### <a name="simulating-eye-tracking-in-the-unity-editor"></a><span data-ttu-id="af388-149">Simulazione del rilevamento degli occhi nell'editor di Unity</span><span class="sxs-lookup"><span data-stu-id="af388-149">Simulating eye tracking in the Unity Editor</span></span>

<span data-ttu-id="af388-150">È possibile simulare l'input di rilevamento degli occhi nell'editor di Unity per assicurarsi che gli eventi vengano attivati correttamente prima di distribuire l'app in HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="af388-150">You can simulate eye tracking input in the Unity Editor to ensure that events are correctly triggered before deploying the app to your HoloLens 2.</span></span>
<span data-ttu-id="af388-151">Il segnale di sguardi occhi viene simulato semplicemente usando la posizione della fotocamera come origine dello sguardo oculare e il vettore di avanzamento della fotocamera come direzione degli sguardi oculari.</span><span class="sxs-lookup"><span data-stu-id="af388-151">The eye gaze signal is simulated by simply using the camera's location as eye gaze origin and the camera's forward vector as eye gaze direction.</span></span>
<span data-ttu-id="af388-152">Sebbene questo sia ideale per i test iniziali, tenere presente che non si tratta di un'imitazione efficace per i movimenti rapidi degli occhi.</span><span class="sxs-lookup"><span data-stu-id="af388-152">While this is great for initial testing, please note that it is not a good imitation for rapid eye movements.</span></span>
<span data-ttu-id="af388-153">A tale fine, è preferibile garantire i test frequenti delle interazioni basate sugli occhi in HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="af388-153">For this, it is better to ensure frequent tests of your eye-based interactions on the HoloLens 2.</span></span>

1. <span data-ttu-id="af388-154">**Abilita rilevamento occhi simulato**:</span><span class="sxs-lookup"><span data-stu-id="af388-154">**Enable simulated eye tracking**:</span></span>
    - <span data-ttu-id="af388-155">Fare clic sulla scheda _"input"_ nel profilo di configurazione di MRTK.</span><span class="sxs-lookup"><span data-stu-id="af388-155">Click on the _'Input'_ tab in your MRTK configuration profile.</span></span>
    - <span data-ttu-id="af388-156">Passare a _"provider di dati di input"_  ->  _"servizio di simulazione input_".</span><span class="sxs-lookup"><span data-stu-id="af388-156">From there, navigate to _'Input Data Providers'_ -> _'Input Simulation Service'_.</span></span>
    - <span data-ttu-id="af388-157">Clonare l'oggetto _' DefaultMixedRealityInputSimpulationProfile '_ per apportare modifiche.</span><span class="sxs-lookup"><span data-stu-id="af388-157">Clone the _'DefaultMixedRealityInputSimpulationProfile'_ to make changes to it.</span></span>
    - <span data-ttu-id="af388-158">Selezionare la casella di controllo _"simula posizione occhio"_ .</span><span class="sxs-lookup"><span data-stu-id="af388-158">Check the _'Simulate Eye Position'_ checkbox.</span></span>

    ![MRTK Eyes simulate](../../images/eye-tracking/mrtk_setup_eyes_simulate.jpg)

2. <span data-ttu-id="af388-160">**Disabilitare il cursore per lo sguardo a capo predefinito**: in generale, è consigliabile evitare di visualizzare un cursore con lo sguardo d'occhio o, se necessario, per renderlo _estremamente_ sottile.</span><span class="sxs-lookup"><span data-stu-id="af388-160">**Disable default head gaze cursor**: In general, it is recommended to avoid showing an eye gaze cursor or if absolutely required to make it _very_ subtle.</span></span>
<span data-ttu-id="af388-161">Per impostazione predefinita, è consigliabile nascondere il cursore predefinito per lo sguardo a capo associato al profilo del puntatore MRTK per impostazione predefinita.</span><span class="sxs-lookup"><span data-stu-id="af388-161">We do recommend to hide the default head gaze cursor that is attached to the MRTK gaze pointer profile by default.</span></span>
    - <span data-ttu-id="af388-162">Passare al profilo di configurazione di MRTK-> _' input '_  ->  _' puntatori '_</span><span class="sxs-lookup"><span data-stu-id="af388-162">Navigate to your MRTK configuration profile -> _'Input'_ -> _'Pointers'_</span></span>
    - <span data-ttu-id="af388-163">Clonare l'oggetto _' DefaultMixedRealityInputPointerProfile '_ per apportare modifiche.</span><span class="sxs-lookup"><span data-stu-id="af388-163">Clone the _'DefaultMixedRealityInputPointerProfile'_ to make changes to it.</span></span>
    - <span data-ttu-id="af388-164">Nella parte superiore di _' Pointer Settings '_ è necessario assegnare un cursore invisibile prefabbricato a _' GazeCursor '_.</span><span class="sxs-lookup"><span data-stu-id="af388-164">At the top of the _'Pointer Settings'_, you should assign an invisible cursor prefab to the _'GazeCursor'_.</span></span> <span data-ttu-id="af388-165">Questa operazione può essere eseguita selezionando la prefabbricata _' EyeGazeCursor '_ di MRTK Foundation.</span><span class="sxs-lookup"><span data-stu-id="af388-165">You can do this by selecting the _'EyeGazeCursor'_ prefab from the MRTK Foundation.</span></span>

### <a name="enabling-eye-based-gaze-in-the-gaze-provider"></a><span data-ttu-id="af388-166">Abilitazione dello sguardo basato sull'occhio nel provider di sguardi</span><span class="sxs-lookup"><span data-stu-id="af388-166">Enabling eye-based gaze in the gaze provider</span></span>

<span data-ttu-id="af388-167">In HoloLens V1, il primo sguardo è stato usato come tecnica di puntamento principale.</span><span class="sxs-lookup"><span data-stu-id="af388-167">In HoloLens v1, head gaze was used as primary pointing technique.</span></span>
<span data-ttu-id="af388-168">Mentre lo sguardo a capo è ancora disponibile tramite _GazeProvider_ in MRTK, che è collegato alla [fotocamera](https://docs.unity3d.com/ScriptReference/Camera.html), è possibile selezionare l'opzione per l'uso degli occhi, selezionando la casella di controllo _' IsEyeTrackingEnabled '_ nelle impostazioni dello sguardo del profilo del puntatore di input.</span><span class="sxs-lookup"><span data-stu-id="af388-168">While head gaze is still available via the _GazeProvider_ in MRTK which is attached to your [Camera](https://docs.unity3d.com/ScriptReference/Camera.html), you can check to use eye gaze instead by ticking the _'IsEyeTrackingEnabled'_ checkbox in the gaze settings of the input pointer profile.</span></span>

>[!NOTE]
><span data-ttu-id="af388-169">Gli sviluppatori possono passare da un sguardo a un occhio basato sull'occhio a quello basato su Head nel codice modificando la proprietà _' IsEyeTrackingEnabled '_ di _' GazeProvider '_.</span><span class="sxs-lookup"><span data-stu-id="af388-169">Developers can toggle between eye-based gaze and head-based gaze in code by changing the _'IsEyeTrackingEnabled'_ property of _'GazeProvider'_.</span></span>  

>[!IMPORTANT]
><span data-ttu-id="af388-170">Se non vengono soddisfatti i requisiti di rilevamento degli occhi, l'applicazione eseguirà automaticamente il fallback allo sguardo basato su Head.</span><span class="sxs-lookup"><span data-stu-id="af388-170">If any of the eye tracking requirements are not met, the application will automatically fall back to head-based gaze.</span></span>

### <a name="accessing-eye-gaze-data"></a><span data-ttu-id="af388-171">Accesso ai dati di Eye sguardi</span><span class="sxs-lookup"><span data-stu-id="af388-171">Accessing eye gaze data</span></span>

<span data-ttu-id="af388-172">Ora che la scena è configurata in modo da usare la verifica degli occhi, esaminiamo come accedervi negli script: [accesso ai dati di rilevamento degli occhi tramite EyeGazeProvider](eye-tracking-eye-gaze-provider.md) e [selezioni di destinazione supportate dagli occhi](eye-tracking-target-selection.md).</span><span class="sxs-lookup"><span data-stu-id="af388-172">Now that your scene is set up to use eye tracking, let's take a look at how to access it in your scripts: [Accessing eye tracking data via EyeGazeProvider](eye-tracking-eye-gaze-provider.md) and [eye-supported target selections](eye-tracking-target-selection.md).</span></span>

### <a name="testing-your-unity-app-on-a-hololens-2"></a><span data-ttu-id="af388-173">Test dell'app Unity in un HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="af388-173">Testing your Unity app on a HoloLens 2</span></span>

<span data-ttu-id="af388-174">La compilazione dell'app con la verifica degli occhi dovrebbe essere simile a quella di altre app MRTK HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="af388-174">Building your app with eye tracking should be similar to how you would compile other HoloLens 2 MRTK apps.</span></span> <span data-ttu-id="af388-175">Assicurarsi di aver abilitato la funzionalità di *"input dello sguardo"* , come descritto in precedenza nella sezione [*una nota sulla funzionalità GazeInput*](#a-note-on-the-gazeinput-capability).</span><span class="sxs-lookup"><span data-stu-id="af388-175">Be sure that you have enabled the *'Gaze Input'* capability as described above in the section [*A note on the GazeInput capability*](#a-note-on-the-gazeinput-capability).</span></span>

#### <a name="eye-calibration"></a><span data-ttu-id="af388-176">Calibrazione degli occhi</span><span class="sxs-lookup"><span data-stu-id="af388-176">Eye calibration</span></span>

<span data-ttu-id="af388-177">Infine, non dimenticare di eseguire la taratura degli occhi sulla HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="af388-177">Finally, please don't forget to run through the eye calibration on your HoloLens 2.</span></span>
<span data-ttu-id="af388-178">Il sistema di rilevamento degli occhi non restituirà alcun input se l'utente non è calibrato.</span><span class="sxs-lookup"><span data-stu-id="af388-178">The eye tracking system will not return any input if the user is not calibrated.</span></span>
<span data-ttu-id="af388-179">Il modo più semplice per ottenere la calibrazione consiste nell'instradare la visiera e viceversa.</span><span class="sxs-lookup"><span data-stu-id="af388-179">Easiest way to get to the calibration is by flipping up the visor and back down.</span></span>
<span data-ttu-id="af388-180">Una notifica di sistema dovrebbe essere visualizzata come un nuovo utente e chiedere di esaminare la calibrazione degli occhi.</span><span class="sxs-lookup"><span data-stu-id="af388-180">A system notification should appear welcoming you as a new user and asking you to go through the eye calibration.</span></span>
<span data-ttu-id="af388-181">In alternativa, è possibile trovare la calibrazione degli occhi nelle impostazioni di sistema: impostazioni > sistema > la calibrazione > eseguire la calibrazione degli occhi.</span><span class="sxs-lookup"><span data-stu-id="af388-181">Alternatively you can find the eye calibration in the system settings: Settings > System > Calibration > Run eye calibration.</span></span>

#### <a name="eye-tracking-permission"></a><span data-ttu-id="af388-182">Autorizzazione per la verifica degli occhi</span><span class="sxs-lookup"><span data-stu-id="af388-182">Eye tracking permission</span></span>

<span data-ttu-id="af388-183">Quando si avvia l'app in HoloLens 2 per la prima volta, viene visualizzato un messaggio che richiede all'utente l'autorizzazione per l'uso di Eye Tracking.</span><span class="sxs-lookup"><span data-stu-id="af388-183">When starting the app on your HoloLens 2 for the first time, a prompt should pop up asking the user for permission to use eye tracking.</span></span>
<span data-ttu-id="af388-184">Se non viene visualizzato, indica in genere che non è stata impostata la funzionalità _' GazeInput '_ .</span><span class="sxs-lookup"><span data-stu-id="af388-184">If it is not showing up, then that is usually an indication that the _'GazeInput'_ capability was not set.</span></span>

<span data-ttu-id="af388-185">Una volta visualizzata la richiesta di autorizzazione, questa non verrà visualizzata di nuovo automaticamente.</span><span class="sxs-lookup"><span data-stu-id="af388-185">After the permission prompt showed up once, it will not show up automatically again.</span></span>
<span data-ttu-id="af388-186">Se è stata _negata l'autorizzazione per la verifica degli occhi_, è possibile reimpostarla in impostazioni-> Privacy-> app.</span><span class="sxs-lookup"><span data-stu-id="af388-186">If you _"denied eye tracking permission"_, you can reset this in Settings -> Privacy -> Apps.</span></span>

---

<span data-ttu-id="af388-187">Questa operazione dovrebbe iniziare a usare la verifica degli occhi nell'app MRTK Unity.</span><span class="sxs-lookup"><span data-stu-id="af388-187">This should get you started with using eye tracking in your MRTK Unity app.</span></span>
<span data-ttu-id="af388-188">Non dimenticare di consultare [le esercitazioni e gli esempi di MRTK Eye Tracking](../../example-scenes/eye-tracking-examples-overview.md) che illustrano come usare l'input di rilevamento degli occhi e fornire facilmente gli script che è possibile riutilizzare nei progetti.</span><span class="sxs-lookup"><span data-stu-id="af388-188">Don't forget to check out [our MRTK eye tracking tutorials and samples](../../example-scenes/eye-tracking-examples-overview.md) demonstrating how to use eye tracking input and conveniently providing scripts that you can reuse in your projects.</span></span>

---
[<span data-ttu-id="af388-189">Torna a "Eye Tracking in the MixedRealityToolkit"</span><span class="sxs-lookup"><span data-stu-id="af388-189">Back to "Eye tracking in the MixedRealityToolkit"</span></span>](eye-tracking-main.md)

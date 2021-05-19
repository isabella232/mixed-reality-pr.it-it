---
title: Configurazione di base del tracciamento oculare
description: Come configurare Eye Tracking in MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realtà mista, sviluppo, MRTK, Eye Tracking,
ms.openlocfilehash: 0513161bf8151069296c39612cbcacd15cc5c6c1
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144095"
---
# <a name="getting-started-with-eye-tracking-in-mrtk"></a><span data-ttu-id="369ed-104">Introduzione al tracciamento oculare in MRTK</span><span class="sxs-lookup"><span data-stu-id="369ed-104">Getting started with eye tracking in MRTK</span></span>

<span data-ttu-id="369ed-105">Questa pagina illustra come configurare la scena di Unity MRTK per usare il tracciamento oculare nell'app.</span><span class="sxs-lookup"><span data-stu-id="369ed-105">This page covers how to set up your Unity MRTK scene to use eye tracking in your app.</span></span>
<span data-ttu-id="369ed-106">Di seguito si presuppone che si inizi con una nuova scena.</span><span class="sxs-lookup"><span data-stu-id="369ed-106">The following assumes you are starting out with a fresh new scene.</span></span>
<span data-ttu-id="369ed-107">In alternativa, è possibile consultare gli esempi di tracciamento oculare [MRTK](../../example-scenes/eye-tracking-examples-overview.md) già configurati con moltissimi esempi di cui è possibile basarsi direttamente.</span><span class="sxs-lookup"><span data-stu-id="369ed-107">Alternatively, you can check out our already configured [MRTK eye tracking examples](../../example-scenes/eye-tracking-examples-overview.md) with tons of great examples that you can directly build on.</span></span>

## <a name="eye-tracking-requirements-checklist"></a><span data-ttu-id="369ed-108">Elenco di controllo dei requisiti di tracciamento oculare</span><span class="sxs-lookup"><span data-stu-id="369ed-108">Eye tracking requirements checklist</span></span>

<span data-ttu-id="369ed-109">Per il corretto funzionamento del tracciamento oculare, è necessario soddisfare i requisiti seguenti.</span><span class="sxs-lookup"><span data-stu-id="369ed-109">For eye tracking to work correctly, the following requirements must be met.</span></span>
<span data-ttu-id="369ed-110">Se non si ha di che HoloLens 2 e come è configurato il tracciamento oculare in MRTK, non preoccuparsi.</span><span class="sxs-lookup"><span data-stu-id="369ed-110">If you are new to eye tracking on HoloLens 2 and to how eye tracking is set up in MRTK, don't worry!</span></span>
<span data-ttu-id="369ed-111">Verranno fornite informazioni dettagliate su come risolvere ognuno di essi più avanti.</span><span class="sxs-lookup"><span data-stu-id="369ed-111">We will go into detail on how to address each of them further below.</span></span>

1. <span data-ttu-id="369ed-112">È _necessario aggiungere un provider di dati 'Eye Gaze'_ al sistema di input.</span><span class="sxs-lookup"><span data-stu-id="369ed-112">An _'Eye Gaze Data Provider'_ must be added to the input system.</span></span> <span data-ttu-id="369ed-113">In questo modo vengono forniti i dati di tracciamento oculare dalla piattaforma.</span><span class="sxs-lookup"><span data-stu-id="369ed-113">This provides eye tracking data from the platform.</span></span>
2. <span data-ttu-id="369ed-114">La _funzionalità 'GazeInput'_ deve essere abilitata nel manifesto dell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="369ed-114">The _'GazeInput'_ capability must be enabled in the application manifest.</span></span>
   <span data-ttu-id="369ed-115">**Questa funzionalità può essere impostata in Unity 2019, ma in Unity 2018 e versioni precedenti questa funzionalità è disponibile solo in Visual Studio e tramite lo strumento di compilazione MRTK**</span><span class="sxs-lookup"><span data-stu-id="369ed-115">**This capability can be set in Unity 2019, but in Unity 2018 and earlier this capability is only available in Visual Studio and through the MRTK build tool**</span></span>
3. <span data-ttu-id="369ed-116">HoloLens deve **essere calibrato** con gli occhi per l'utente corrente.</span><span class="sxs-lookup"><span data-stu-id="369ed-116">The HoloLens **must** be eye calibrated for the current user.</span></span> <span data-ttu-id="369ed-117">Vedere [l'esempio per rilevare se un utente è calibrato dagli occhi o meno.](eye-tracking-is-user-calibrated.md)</span><span class="sxs-lookup"><span data-stu-id="369ed-117">Check out our [sample for detecting whether a user is eye calibrated or not](eye-tracking-is-user-calibrated.md).</span></span>

### <a name="a-note-on-the-gazeinput-capability"></a><span data-ttu-id="369ed-118">Nota sulla funzionalità GazeInput</span><span class="sxs-lookup"><span data-stu-id="369ed-118">A note on the GazeInput capability</span></span>

<span data-ttu-id="369ed-119">Gli strumenti di compilazione forniti da MRTK (ad esempio Mixed Reality Toolkit -> Utilities -> Build Window) possono abilitare automaticamente la funzionalità GazeInput.</span><span class="sxs-lookup"><span data-stu-id="369ed-119">The MRTK-provided build tooling (i.e. Mixed Reality Toolkit -> Utilities -> Build Window) can automatically enable the GazeInput capability for you.</span></span> <span data-ttu-id="369ed-120">A tale scopo, è necessario assicurarsi che la "Funzionalità di input sguardo fisso" sia selezionata nella scheda "Opzioni di compilazione Appx":</span><span class="sxs-lookup"><span data-stu-id="369ed-120">In order to do this, you need to make sure that the 'Gaze Input Capability' is checked on the 'Appx Build Options' tab:</span></span>

![Strumenti di compilazione MRTK](../../images/eye-tracking/mrtk_et_buildsetup.png)

<span data-ttu-id="369ed-122">Questi strumenti troveranno il manifesto AppX dopo il completamento della compilazione di Unity e aggiungeranno manualmente la funzionalità GazeInput.</span><span class="sxs-lookup"><span data-stu-id="369ed-122">This tooling will find the AppX manifest after the Unity build is completed and manually add the GazeInput capability.</span></span>
<span data-ttu-id="369ed-123">**Prima di Unity 2019,** questo strumento NON è attivo quando si usa la finestra di compilazione predefinita di Unity, ad esempio File -> Build Settings (Impostazioni di compilazione file-> compilazione).</span><span class="sxs-lookup"><span data-stu-id="369ed-123">**Prior to Unity 2019, this tooling is NOT active when using Unity's built-in Build Window** (i.e. File -> Build Settings).</span></span>

<span data-ttu-id="369ed-124">Prima di Unity 2019, quando si usa la finestra di compilazione di Unity, la funzionalità dovrà essere aggiunta manualmente dopo la compilazione di Unity, come indicato di seguito:</span><span class="sxs-lookup"><span data-stu-id="369ed-124">Prior to Unity 2019, when using Unity's build window, the capability will need to be manually added after the Unity build, as follows:</span></span>

1. <span data-ttu-id="369ed-125">Aprire il progetto Visual Studio e quindi aprire _'Package.appxmanifest'_ nella soluzione.</span><span class="sxs-lookup"><span data-stu-id="369ed-125">Open your compiled Visual Studio project and then open the _'Package.appxmanifest'_ in your solution.</span></span>
2. <span data-ttu-id="369ed-126">Assicurarsi di selezionare la casella _di controllo "GazeInput"_ in _Capabilities (Funzionalità)._</span><span class="sxs-lookup"><span data-stu-id="369ed-126">Make sure to tick the _'GazeInput'_ checkbox under _Capabilities_.</span></span> <span data-ttu-id="369ed-127">Se non viene visualizzata una funzionalità _"GazeInput",_ verificare che il sistema soddisfi i prerequisiti per l'uso di [MRTK](/windows/mixed-reality/develop/install-the-tools) (in particolare la Windows SDK precedente.</span><span class="sxs-lookup"><span data-stu-id="369ed-127">If you don't see a _'GazeInput'_ capability, check that your system meets the [prerequisites for using MRTK](/windows/mixed-reality/develop/install-the-tools) (in particular the Windows SDK version).</span></span>

<span data-ttu-id="369ed-128">_Si noti che:_ È necessario eseguire questa operazione solo se si compila in una nuova cartella di compilazione.</span><span class="sxs-lookup"><span data-stu-id="369ed-128">_Please note:_ You only have to do this if you build into a new build folder.</span></span>
<span data-ttu-id="369ed-129">Ciò significa che se il progetto Unity è già stato compilato e si è configurato appxmanifest in precedenza e ora è stata impostata di nuovo come destinazione la stessa cartella, non sarà necessario riapplicare le modifiche.</span><span class="sxs-lookup"><span data-stu-id="369ed-129">This means that if you had already built your Unity project and set up the appxmanifest before and now target the same folder again, you will not need to reapply your changes.</span></span>

## <a name="setting-up-eye-tracking-step-by-step"></a><span data-ttu-id="369ed-130">Configurazione dettagliata del tracciamento oculare</span><span class="sxs-lookup"><span data-stu-id="369ed-130">Setting up eye tracking step-by-step</span></span>

### <a name="setting-up-the-scene"></a><span data-ttu-id="369ed-131">Configurazione della scena</span><span class="sxs-lookup"><span data-stu-id="369ed-131">Setting up the scene</span></span>

<span data-ttu-id="369ed-132">Configurare _MixedRealityToolkit_ semplicemente facendo clic su _"Mixed Reality Toolkit -> Configura"._</span><span class="sxs-lookup"><span data-stu-id="369ed-132">Set up the _MixedRealityToolkit_ by simply clicking _'Mixed Reality Toolkit -> Configure…'_</span></span> <span data-ttu-id="369ed-133">nella barra dei menu.</span><span class="sxs-lookup"><span data-stu-id="369ed-133">in the menu bar.</span></span>

![Configurazione di MRTK](../../images/eye-tracking/mrtk_setup_configure.jpg)

### <a name="setting-up-the-mrtk-profiles-required-for-eye-tracking"></a><span data-ttu-id="369ed-135">Configurazione dei profili MRTK necessari per il tracciamento oculare</span><span class="sxs-lookup"><span data-stu-id="369ed-135">Setting up the MRTK profiles required for eye tracking</span></span>

<span data-ttu-id="369ed-136">Dopo aver impostato la scena MRTK, ti verrà chiesto di scegliere un profilo per MRTK.</span><span class="sxs-lookup"><span data-stu-id="369ed-136">After setting up your MRTK scene, you will be asked to choose a profile for MRTK.</span></span>
<span data-ttu-id="369ed-137">È sufficiente selezionare _DefaultMixedRealityToolkitConfigurationProfile_ e quindi selezionare l'opzione _"Copia_ & Personalizza".</span><span class="sxs-lookup"><span data-stu-id="369ed-137">You can simply select _DefaultMixedRealityToolkitConfigurationProfile_ and then select the _'Copy & Customize'_ option.</span></span>

![Profilo MRTK](../../images/eye-tracking/mrtk_setup_configprofile.jpg)

### <a name="create-an-eye-gaze-data-provider"></a><span data-ttu-id="369ed-139">Creare un "provider di dati di sguardo fisso"</span><span class="sxs-lookup"><span data-stu-id="369ed-139">Create an "eye gaze data provider"</span></span>

- <span data-ttu-id="369ed-140">Fare clic sulla _scheda "Input"_ nel profilo MRTK.</span><span class="sxs-lookup"><span data-stu-id="369ed-140">Click on the _'Input'_ tab in your MRTK profile.</span></span>
- <span data-ttu-id="369ed-141">Per modificare quello predefinito ( _'DefaultMixedRealityInputSystemProfile'),_ fare clic sul _pulsante "Clona"_ accanto.</span><span class="sxs-lookup"><span data-stu-id="369ed-141">To edit the default one ( _'DefaultMixedRealityInputSystemProfile'_ ), click the _'Clone'_ button next to it.</span></span> <span data-ttu-id="369ed-142">Viene visualizzato il menu _"Clone Profile" (Clona_ profilo).</span><span class="sxs-lookup"><span data-stu-id="369ed-142">A _'Clone Profile'_ menu appears.</span></span> <span data-ttu-id="369ed-143">È sufficiente fare _clic su "Clone" (Clona)_ nella parte inferiore del menu.</span><span class="sxs-lookup"><span data-stu-id="369ed-143">Simply click on _'Clone'_ at the bottom of that menu.</span></span>
- <span data-ttu-id="369ed-144">Fare doppio clic sul nuovo profilo di input, espandere _"Provider di dati di input"_ e selezionare _"+ Aggiungi provider di dati"._</span><span class="sxs-lookup"><span data-stu-id="369ed-144">Double click on your new input profile, expand _'Input Data Providers'_, and select _'+ Add Data Provider'_.</span></span>
- <span data-ttu-id="369ed-145">Creare un nuovo provider di dati:</span><span class="sxs-lookup"><span data-stu-id="369ed-145">Create a new data provider:</span></span>
  - <span data-ttu-id="369ed-146">In **Tipo** selezionare _'Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input'_  ->  _'WindowsMixedRealityEyeGazeDataProvider'_</span><span class="sxs-lookup"><span data-stu-id="369ed-146">Under **Type** select _'Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input'_ -> _'WindowsMixedRealityEyeGazeDataProvider'_</span></span>
  - <span data-ttu-id="369ed-147">Per **Piattaforme selezionare** _"Universale di Windows"._</span><span class="sxs-lookup"><span data-stu-id="369ed-147">For **Platform(s)** select _'Windows Universal'_.</span></span>

![Provider di dati MRTK](../../images/eye-tracking/mrtk_setup_eyes_dataprovider.jpg)

### <a name="simulating-eye-tracking-in-the-unity-editor"></a><span data-ttu-id="369ed-149">Simulazione del tracciamento oculare nell'editor di Unity</span><span class="sxs-lookup"><span data-stu-id="369ed-149">Simulating eye tracking in the Unity Editor</span></span>

<span data-ttu-id="369ed-150">È possibile simulare l'input del tracciamento oculare nell'editor di Unity per assicurarsi che gli eventi vengano attivati correttamente prima di distribuire l'app nel HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="369ed-150">You can simulate eye tracking input in the Unity Editor to ensure that events are correctly triggered before deploying the app to your HoloLens 2.</span></span>
<span data-ttu-id="369ed-151">Il segnale dello sguardo fisso viene simulato semplicemente usando la posizione della fotocamera come origine dello sguardo e il vettore in avanti della fotocamera come direzione dello sguardo fisso.</span><span class="sxs-lookup"><span data-stu-id="369ed-151">The eye gaze signal is simulated by simply using the camera's location as eye gaze origin and the camera's forward vector as eye gaze direction.</span></span>
<span data-ttu-id="369ed-152">Anche se è ideale per i test iniziali, si noti che non è una buona idea per i movimenti oculari rapidi.</span><span class="sxs-lookup"><span data-stu-id="369ed-152">While this is great for initial testing, please note that it is not a good imitation for rapid eye movements.</span></span>
<span data-ttu-id="369ed-153">A questo scopo, è meglio garantire test frequenti delle interazioni basate sugli occhi sul HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="369ed-153">For this, it is better to ensure frequent tests of your eye-based interactions on the HoloLens 2.</span></span>

1. <span data-ttu-id="369ed-154">**Abilitare il tracciamento oculare simulato:**</span><span class="sxs-lookup"><span data-stu-id="369ed-154">**Enable simulated eye tracking**:</span></span>
    - <span data-ttu-id="369ed-155">Fare clic sulla _scheda "Input"_ nel profilo di configurazione di MRTK.</span><span class="sxs-lookup"><span data-stu-id="369ed-155">Click on the _'Input'_ tab in your MRTK configuration profile.</span></span>
    - <span data-ttu-id="369ed-156">Da qui passare a _"Input Data Providers" (Provider di dati di_  ->  _input) "Input Simulation Service" (Servizio simulazione input)._</span><span class="sxs-lookup"><span data-stu-id="369ed-156">From there, navigate to _'Input Data Providers'_ -> _'Input Simulation Service'_.</span></span>
    - <span data-ttu-id="369ed-157">Clonare _'DefaultMixedRealityInputSimpulationProfile'_ per apportare modifiche.</span><span class="sxs-lookup"><span data-stu-id="369ed-157">Clone the _'DefaultMixedRealityInputSimpulationProfile'_ to make changes to it.</span></span>
    - <span data-ttu-id="369ed-158">Selezionare la _casella di controllo "Simulate Eye Position" (Simula posizione_ oculare).</span><span class="sxs-lookup"><span data-stu-id="369ed-158">Check the _'Simulate Eye Position'_ checkbox.</span></span>

    ![MrTK eyes simulate (Simulazione occhi MRTK)](../../images/eye-tracking/mrtk_setup_eyes_simulate.jpg)

2. <span data-ttu-id="369ed-160">**Disabilitare il cursore predefinito** per lo sguardo fisso con la testa: in generale, è consigliabile evitare di visualizzare un cursore con sguardo fisso o se assolutamente necessario per renderlo _molto_ sottile.</span><span class="sxs-lookup"><span data-stu-id="369ed-160">**Disable default head gaze cursor**: In general, it is recommended to avoid showing an eye gaze cursor or if absolutely required to make it _very_ subtle.</span></span>
<span data-ttu-id="369ed-161">È consigliabile nascondere il cursore dello sguardo fisso predefinito associato al profilo del puntatore dello sguardo fisso MRTK per impostazione predefinita.</span><span class="sxs-lookup"><span data-stu-id="369ed-161">We do recommend to hide the default head gaze cursor that is attached to the MRTK gaze pointer profile by default.</span></span>
    - <span data-ttu-id="369ed-162">Passare al profilo di configurazione MRTK -> _'Input'_  ->  _'Pointers'_</span><span class="sxs-lookup"><span data-stu-id="369ed-162">Navigate to your MRTK configuration profile -> _'Input'_ -> _'Pointers'_</span></span>
    - <span data-ttu-id="369ed-163">Clonare _'DefaultMixedRealityInputPointerProfile'_ per apportare modifiche.</span><span class="sxs-lookup"><span data-stu-id="369ed-163">Clone the _'DefaultMixedRealityInputPointerProfile'_ to make changes to it.</span></span>
    - <span data-ttu-id="369ed-164">Nella parte superiore di _"Impostazioni puntatore"_ è necessario assegnare un prefab del cursore invisibile a _'GazeCursor'._</span><span class="sxs-lookup"><span data-stu-id="369ed-164">At the top of the _'Pointer Settings'_, you should assign an invisible cursor prefab to the _'GazeCursor'_.</span></span> <span data-ttu-id="369ed-165">A tale scopo, selezionare il prefab _"EyeGazeCursor"_ da MRTK Foundation.</span><span class="sxs-lookup"><span data-stu-id="369ed-165">You can do this by selecting the _'EyeGazeCursor'_ prefab from the MRTK Foundation.</span></span>

### <a name="enabling-eye-based-gaze-in-the-gaze-provider"></a><span data-ttu-id="369ed-166">Abilitazione dello sguardo oculare nel provider di sguardo</span><span class="sxs-lookup"><span data-stu-id="369ed-166">Enabling eye-based gaze in the gaze provider</span></span>

<span data-ttu-id="369ed-167">In HoloLens v1, lo sguardo rivolto verso la testa è stato usato come tecnica di puntamento principale.</span><span class="sxs-lookup"><span data-stu-id="369ed-167">In HoloLens v1, head gaze was used as primary pointing technique.</span></span>
<span data-ttu-id="369ed-168">Mentre lo sguardo della testa è ancora disponibile tramite _GazeProvider_ in MRTK collegato alla [fotocamera,](https://docs.unity3d.com/ScriptReference/Camera.html)è possibile controllare di usare lo sguardo fisso selezionando invece la casella di controllo _"IsEyeTrackingEnabled"_ nelle impostazioni dello sguardo fisso del profilo del puntatore di input.</span><span class="sxs-lookup"><span data-stu-id="369ed-168">While head gaze is still available via the _GazeProvider_ in MRTK which is attached to your [Camera](https://docs.unity3d.com/ScriptReference/Camera.html), you can check to use eye gaze instead by ticking the _'IsEyeTrackingEnabled'_ checkbox in the gaze settings of the input pointer profile.</span></span>

>[!NOTE]
><span data-ttu-id="369ed-169">Gli sviluppatori possono alternare lo sguardo visivo e lo sguardo con la testa nel codice modificando la proprietà _'IsEyeTrackingEnabled'_ di _'GazeProvider'._</span><span class="sxs-lookup"><span data-stu-id="369ed-169">Developers can toggle between eye-based gaze and head-based gaze in code by changing the _'IsEyeTrackingEnabled'_ property of _'GazeProvider'_.</span></span>  

>[!IMPORTANT]
><span data-ttu-id="369ed-170">Se uno dei requisiti di tracciamento oculare non viene soddisfatto, l'applicazione torna automaticamente alla vista basata sulla testa.</span><span class="sxs-lookup"><span data-stu-id="369ed-170">If any of the eye tracking requirements are not met, the application will automatically fall back to head-based gaze.</span></span>

### <a name="accessing-eye-gaze-data"></a><span data-ttu-id="369ed-171">Accesso ai dati dello sguardo fisso</span><span class="sxs-lookup"><span data-stu-id="369ed-171">Accessing eye gaze data</span></span>

<span data-ttu-id="369ed-172">Ora che la scena è stata impostata per l'uso del tracciamento oculare, è possibile esaminare come accedervi negli script: Accesso ai dati di tracciamento oculare tramite [EyeGazeProvider](eye-tracking-eye-gaze-provider.md) e selezioni di destinazione supportate dagli [occhi.](eye-tracking-target-selection.md)</span><span class="sxs-lookup"><span data-stu-id="369ed-172">Now that your scene is set up to use eye tracking, let's take a look at how to access it in your scripts: [Accessing eye tracking data via EyeGazeProvider](eye-tracking-eye-gaze-provider.md) and [eye-supported target selections](eye-tracking-target-selection.md).</span></span>

### <a name="testing-your-unity-app-on-a-hololens-2"></a><span data-ttu-id="369ed-173">Test dell'app Unity in un HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="369ed-173">Testing your Unity app on a HoloLens 2</span></span>

<span data-ttu-id="369ed-174">La compilazione dell'app con il tracciamento oculare dovrebbe essere simile alla compilazione di altre app HoloLens 2 MRTK.</span><span class="sxs-lookup"><span data-stu-id="369ed-174">Building your app with eye tracking should be similar to how you would compile other HoloLens 2 MRTK apps.</span></span> <span data-ttu-id="369ed-175">Assicurarsi di aver abilitato la funzionalità *"Gaze Input"* come descritto in precedenza nella sezione Nota sulla [*funzionalità GazeInput*](#a-note-on-the-gazeinput-capability).</span><span class="sxs-lookup"><span data-stu-id="369ed-175">Be sure that you have enabled the *'Gaze Input'* capability as described above in the section [*A note on the GazeInput capability*](#a-note-on-the-gazeinput-capability).</span></span>

#### <a name="eye-calibration"></a><span data-ttu-id="369ed-176">Calibrazione oculare</span><span class="sxs-lookup"><span data-stu-id="369ed-176">Eye calibration</span></span>

<span data-ttu-id="369ed-177">Infine, non dimenticare di eseguire la calibrazione dell'occhio sul HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="369ed-177">Finally, please don't forget to run through the eye calibration on your HoloLens 2.</span></span>
<span data-ttu-id="369ed-178">Il sistema di tracciamento oculare non restituirà alcun input se l'utente non è calibrato.</span><span class="sxs-lookup"><span data-stu-id="369ed-178">The eye tracking system will not return any input if the user is not calibrated.</span></span>
<span data-ttu-id="369ed-179">Il modo più semplice per ottenere la calibrazione è capovolgere la visiera e tornare indietro.</span><span class="sxs-lookup"><span data-stu-id="369ed-179">Easiest way to get to the calibration is by flipping up the visor and back down.</span></span>
<span data-ttu-id="369ed-180">Verrà visualizzata una notifica di sistema che indica l'utente come nuovo utente e chiede di eseguire la calibrazione oculare.</span><span class="sxs-lookup"><span data-stu-id="369ed-180">A system notification should appear welcoming you as a new user and asking you to go through the eye calibration.</span></span>
<span data-ttu-id="369ed-181">In alternativa, è possibile trovare la calibrazione oculare nelle impostazioni di sistema: Impostazioni > sistema > calibrazione > Calibrazione oculare.</span><span class="sxs-lookup"><span data-stu-id="369ed-181">Alternatively you can find the eye calibration in the system settings: Settings > System > Calibration > Run eye calibration.</span></span>

#### <a name="eye-tracking-permission"></a><span data-ttu-id="369ed-182">Autorizzazione di tracciamento oculare</span><span class="sxs-lookup"><span data-stu-id="369ed-182">Eye tracking permission</span></span>

<span data-ttu-id="369ed-183">Quando si avvia l'app nel HoloLens 2 per la prima volta, viene visualizzata una richiesta che richiede all'utente l'autorizzazione per usare il tracciamento oculare.</span><span class="sxs-lookup"><span data-stu-id="369ed-183">When starting the app on your HoloLens 2 for the first time, a prompt should pop up asking the user for permission to use eye tracking.</span></span>
<span data-ttu-id="369ed-184">Se non viene visualizzato, in genere si tratta di un'indicazione che la funzionalità _'GazeInput'_ non è stata impostata.</span><span class="sxs-lookup"><span data-stu-id="369ed-184">If it is not showing up, then that is usually an indication that the _'GazeInput'_ capability was not set.</span></span>

<span data-ttu-id="369ed-185">Dopo che la richiesta di autorizzazione è stata visualizzata una sola volta, non verrà visualizzata di nuovo automaticamente.</span><span class="sxs-lookup"><span data-stu-id="369ed-185">After the permission prompt showed up once, it will not show up automatically again.</span></span>
<span data-ttu-id="369ed-186">Se si _"nega l'autorizzazione di_ tracciamento oculare", è possibile reimpostarla in Impostazioni -> Privacy -> App.</span><span class="sxs-lookup"><span data-stu-id="369ed-186">If you _"denied eye tracking permission"_, you can reset this in Settings -> Privacy -> Apps.</span></span>

---

<span data-ttu-id="369ed-187">Questo dovrebbe iniziare a usare il tracciamento oculare nell'app MRTK Unity.</span><span class="sxs-lookup"><span data-stu-id="369ed-187">This should get you started with using eye tracking in your MRTK Unity app.</span></span>
<span data-ttu-id="369ed-188">Non dimenticare di consultare le esercitazioni e gli esempi sul tracciamento oculare [di MRTK](../../example-scenes/eye-tracking-examples-overview.md) che illustrano come usare l'input di tracciamento oculare e forniscono in modo pratico script che è possibile riutilizzare nei progetti.</span><span class="sxs-lookup"><span data-stu-id="369ed-188">Don't forget to check out [our MRTK eye tracking tutorials and samples](../../example-scenes/eye-tracking-examples-overview.md) demonstrating how to use eye tracking input and conveniently providing scripts that you can reuse in your projects.</span></span>

---
[<span data-ttu-id="369ed-189">Tornare a "Tracciamento oculare in MixedRealityToolkit"</span><span class="sxs-lookup"><span data-stu-id="369ed-189">Back to "Eye tracking in the MixedRealityToolkit"</span></span>](eye-tracking-main.md)
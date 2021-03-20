---
title: MixedRealityConfigurationGuide
description: Documentazione per la configurazione di MRTK in Unity.
author: RogPodge
ms.author: roliu
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: 21ff15b4a87f3631077c59c01d3afcd9dff386c5
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2021
ms.locfileid: "104694548"
---
# <a name="mixed-reality-toolkit-profile-configuration-guide"></a><span data-ttu-id="b5547-104">Guida alla configurazione del profilo del Toolkit di realtà mista</span><span class="sxs-lookup"><span data-stu-id="b5547-104">Mixed Reality Toolkit profile configuration guide</span></span>

![Logo di MRTK](../features//Images/MRTK_Logo_Rev.png)

<span data-ttu-id="b5547-106">Il Toolkit di realtà mista centralizza la maggior parte della configurazione necessaria per gestire il Toolkit come possibile (ad eccezione di true Runtime "Things").</span><span class="sxs-lookup"><span data-stu-id="b5547-106">The Mixed Reality Toolkit centralizes as much of the configuration required to manage the toolkit as possible (except for true runtime "things").</span></span>

<span data-ttu-id="b5547-107">Questa guida è una semplice procedura dettagliata per ogni schermata del profilo di configurazione attualmente disponibile per il Toolkit.</span><span class="sxs-lookup"><span data-stu-id="b5547-107">This guide is a simple walkthrough for each of the configuration profile screens currently available for the toolkit.</span></span>

## <a name="the-main-mixed-reality-toolkit-configuration-profile"></a><span data-ttu-id="b5547-108">Il profilo di configurazione principale di Mixed Reality Toolkit</span><span class="sxs-lookup"><span data-stu-id="b5547-108">The main Mixed Reality Toolkit configuration profile</span></span>

<span data-ttu-id="b5547-109">Il profilo di configurazione principale, associato al GameObject *MixedRealityToolkit* nella scena, fornisce il punto di ingresso principale per il Toolkit nel progetto.</span><span class="sxs-lookup"><span data-stu-id="b5547-109">The main configuration profile, which is attached to the *MixedRealityToolkit* GameObject in your Scene, provides the main entry point for the Toolkit in your project.</span></span>

> [!NOTE]
> <span data-ttu-id="b5547-110">Il Toolkit di realtà mista "blocca" le schermate di configurazione predefinite per assicurarsi di avere sempre un punto iniziale comune per il progetto ed è consigliabile iniziare a definire le proprie impostazioni durante l'evoluzione del progetto.</span><span class="sxs-lookup"><span data-stu-id="b5547-110">The Mixed Reality Toolkit "locks" the default configuration screens to ensure you always have a common start point for your project and it is encouraged to start defining your own settings as your project evolves.</span></span> <span data-ttu-id="b5547-111">La configurazione di MRTK non è modificabile durante la modalità di riproduzione.</span><span class="sxs-lookup"><span data-stu-id="b5547-111">The MRTK configuration is not editable during play-mode.</span></span>

![Profilo di configurazione di MRTK](../features/Images/MixedRealityToolkitConfigurationProfileScreens/MRTK_ActiveConfiguration.png)

<span data-ttu-id="b5547-113">Tutti i profili "predefiniti" per il Toolkit di realtà mista sono disponibili nel progetto SDK nella cartella assets/MRTK/SDK/Profiles.</span><span class="sxs-lookup"><span data-stu-id="b5547-113">All the "default" profiles for the Mixed Reality Toolkit can be found in the SDK project in the folder Assets/MRTK/SDK/Profiles.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b5547-114">DefaultHoloLens2ConfigurationProfile è ottimizzato per HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="b5547-114">DefaultHoloLens2ConfigurationProfile is optimized for HoloLens 2.</span></span> <span data-ttu-id="b5547-115">Per informazioni dettagliate, vedere [profili](Profiles/Profiles.md) .</span><span class="sxs-lookup"><span data-stu-id="b5547-115">See [Profiles](Profiles/Profiles.md) for the details.</span></span>

<span data-ttu-id="b5547-116">Quando si apre il profilo di configurazione principale del Toolkit di realtà mista, viene visualizzata la schermata seguente nel controllo:</span><span class="sxs-lookup"><span data-stu-id="b5547-116">When you open the main Mixed Reality Toolkit Configuration Profile, you will see the following screen in the inspector:</span></span>

<img src="../features/Images/MixedRealityToolkitConfigurationProfileScreens/MRTK_MixedRealityToolkitConfigurationScreen.png" width="650px" alt="Configuration screen" style="display:block;">

<span data-ttu-id="b5547-117">Se si seleziona un asset MixedRealityToolkitConfigurationProfile senza MixedRealityToolkit nella scena, verrà chiesto se si desidera che il MRTK Configure automaticamente la scena.</span><span class="sxs-lookup"><span data-stu-id="b5547-117">If you select a MixedRealityToolkitConfigurationProfile asset without the MixedRealityToolkit in the scene, it will ask you if you want the MRTK to automatically setup the scene for you.</span></span> <span data-ttu-id="b5547-118">Questa operazione è facoltativa, tuttavia, per accedere a tutte le schermate di configurazione deve essere presente un oggetto MixedRealityToolkit attivo nella scena.</span><span class="sxs-lookup"><span data-stu-id="b5547-118">This is optional, however, there must be an active MixedRealityToolkit object in the scene to access all the configuration screens.</span></span>

<span data-ttu-id="b5547-119">In questo modo viene ospitata la configurazione di runtime attiva corrente per il progetto.</span><span class="sxs-lookup"><span data-stu-id="b5547-119">This houses the current active runtime configuration for the project.</span></span>

<span data-ttu-id="b5547-120">Da qui è possibile passare a tutti i profili di configurazione per MRTK, tra cui:</span><span class="sxs-lookup"><span data-stu-id="b5547-120">From here you can navigate to all the configuration profiles for the MRTK, including:</span></span>

- [<span data-ttu-id="b5547-121">Guida alla configurazione del profilo del Toolkit di realtà mista</span><span class="sxs-lookup"><span data-stu-id="b5547-121">Mixed Reality Toolkit profile configuration guide</span></span>](#mixed-reality-toolkit-profile-configuration-guide)
  - [<span data-ttu-id="b5547-122">Il profilo di configurazione principale di Mixed Reality Toolkit</span><span class="sxs-lookup"><span data-stu-id="b5547-122">The main Mixed Reality Toolkit configuration profile</span></span>](#the-main-mixed-reality-toolkit-configuration-profile)
  - [<span data-ttu-id="b5547-123">Impostazioni esperienza</span><span class="sxs-lookup"><span data-stu-id="b5547-123">Experience settings</span></span>](#experience-settings)
  - [<span data-ttu-id="b5547-124">Impostazioni della fotocamera</span><span class="sxs-lookup"><span data-stu-id="b5547-124">Camera settings</span></span>](#camera-settings)
  - [<span data-ttu-id="b5547-125">Impostazioni del sistema di input</span><span class="sxs-lookup"><span data-stu-id="b5547-125">Input system settings</span></span>](#input-system-settings)
  - [<span data-ttu-id="b5547-126">Impostazioni visualizzazione limite</span><span class="sxs-lookup"><span data-stu-id="b5547-126">Boundary visualization settings</span></span>](#boundary-visualization-settings)
  - [<span data-ttu-id="b5547-127">Selezione del sistema di Teleportation</span><span class="sxs-lookup"><span data-stu-id="b5547-127">Teleportation system selection</span></span>](#teleportation-system-selection)
  - [<span data-ttu-id="b5547-128">Impostazioni di consapevolezza spaziale</span><span class="sxs-lookup"><span data-stu-id="b5547-128">Spatial awareness settings</span></span>](#spatial-awareness-settings)
  - [<span data-ttu-id="b5547-129">Impostazioni di diagnostica</span><span class="sxs-lookup"><span data-stu-id="b5547-129">Diagnostics settings</span></span>](#diagnostics-settings)
  - [<span data-ttu-id="b5547-130">Impostazioni del sistema di scena</span><span class="sxs-lookup"><span data-stu-id="b5547-130">Scene system settings</span></span>](#scene-system-settings)
  - [<span data-ttu-id="b5547-131">Impostazioni servizi aggiuntivi</span><span class="sxs-lookup"><span data-stu-id="b5547-131">Additional services settings</span></span>](#additional-services-settings)
  - [<span data-ttu-id="b5547-132">Impostazioni azioni di input</span><span class="sxs-lookup"><span data-stu-id="b5547-132">Input actions settings</span></span>](#input-actions-settings)
  - [<span data-ttu-id="b5547-133">Regole azioni di input</span><span class="sxs-lookup"><span data-stu-id="b5547-133">Input actions rules</span></span>](#input-actions-rules)
  - [<span data-ttu-id="b5547-134">Configurazione puntatore</span><span class="sxs-lookup"><span data-stu-id="b5547-134">Pointer configuration</span></span>](#pointer-configuration)
  - [<span data-ttu-id="b5547-135">Configurazione di movimenti</span><span class="sxs-lookup"><span data-stu-id="b5547-135">Gestures configuration</span></span>](#gestures-configuration)
  - [<span data-ttu-id="b5547-136">Comandi vocali</span><span class="sxs-lookup"><span data-stu-id="b5547-136">Speech commands</span></span>](#speech-commands)
  - [<span data-ttu-id="b5547-137">Configurazione mapping controller</span><span class="sxs-lookup"><span data-stu-id="b5547-137">Controller mapping configuration</span></span>](#controller-mapping-configuration)
  - [<span data-ttu-id="b5547-138">Impostazioni di visualizzazione del controller</span><span class="sxs-lookup"><span data-stu-id="b5547-138">Controller visualization settings</span></span>](#controller-visualization-settings)
  - [<span data-ttu-id="b5547-139">Utilità Editor</span><span class="sxs-lookup"><span data-stu-id="b5547-139">Editor utilities</span></span>](#editor-utilities)
    - [<span data-ttu-id="b5547-140">Controlli servizio</span><span class="sxs-lookup"><span data-stu-id="b5547-140">Service inspectors</span></span>](#service-inspectors)
    - [<span data-ttu-id="b5547-141">Renderer buffer profondità</span><span class="sxs-lookup"><span data-stu-id="b5547-141">Depth buffer renderer</span></span>](#depth-buffer-renderer)
  - [<span data-ttu-id="b5547-142">Modifica dei profili in fase di esecuzione</span><span class="sxs-lookup"><span data-stu-id="b5547-142">Changing profiles at runtime</span></span>](#changing-profiles-at-runtime)
  - [<span data-ttu-id="b5547-143">Scambio di profili prima dell'inizializzazione di MRTK</span><span class="sxs-lookup"><span data-stu-id="b5547-143">Swapping profiles prior to MRTK initialization</span></span>](#swapping-profiles-prior-to-mrtk-initialization)
  - [<span data-ttu-id="b5547-144">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="b5547-144">See also</span></span>](#see-also)

<span data-ttu-id="b5547-145">Questi profili di configurazione sono descritti in dettaglio nelle sezioni pertinenti:</span><span class="sxs-lookup"><span data-stu-id="b5547-145">These configuration profiles are detailed below in their relevant sections:</span></span>

---
<a name="experience"></a>

## <a name="experience-settings"></a><span data-ttu-id="b5547-146">Impostazioni esperienza</span><span class="sxs-lookup"><span data-stu-id="b5547-146">Experience settings</span></span>

<span data-ttu-id="b5547-147">Situato nella pagina di configurazione principale del Toolkit di realtà mista, questa impostazione definisce l'operazione predefinita della [scala dell'ambiente di realtà mista](https://docs.microsoft.com/en-us/windows/mixed-reality/coordinate-systems-in-unity) per il progetto.</span><span class="sxs-lookup"><span data-stu-id="b5547-147">Located on the main Mixed Reality Toolkit configuration page, this setting defines the default operation of the [Mixed Reality environment scale](https://docs.microsoft.com/en-us/windows/mixed-reality/coordinate-systems-in-unity) for your project.</span></span>

<img src="../features/Images/MixedRealityToolkitConfigurationProfileScreens/MRTK_ExperienceSettings.png" width="650px" alt="Configuration profile scene" style="display:block;">

---
<a name="camera"></a>

## <a name="camera-settings"></a><span data-ttu-id="b5547-148">Impostazioni della fotocamera</span><span class="sxs-lookup"><span data-stu-id="b5547-148">Camera settings</span></span>

<span data-ttu-id="b5547-149">Le impostazioni della fotocamera definiscono come verrà configurata la fotocamera per il progetto di realtà mista, definendo le impostazioni generiche di ritaglio, qualità e trasparenza.</span><span class="sxs-lookup"><span data-stu-id="b5547-149">The camera settings define how the camera will be setup for your Mixed Reality project, defining the generic clipping, quality and transparency settings.</span></span>

<img src="../features/Images/MixedRealityToolkitConfigurationProfileScreens/MRTK_CameraProfile.png" width="650px" alt="Camera setting" style="display:block;">

---
<a name="inputsystem"></a>

## <a name="input-system-settings"></a><span data-ttu-id="b5547-150">Impostazioni del sistema di input</span><span class="sxs-lookup"><span data-stu-id="b5547-150">Input system settings</span></span>

<span data-ttu-id="b5547-151">Il progetto di realtà mista fornisce un sistema di input solido e ben preparato per il routing di tutti gli eventi di input intorno al progetto selezionato per impostazione predefinita.</span><span class="sxs-lookup"><span data-stu-id="b5547-151">The Mixed Reality Project provides a robust and well-trained input system for routing all the input events around the project which is selected by default.</span></span>

<img src="../features/Images/MixedRealityToolkitConfigurationProfileScreens/MRTK_InputSystemSelection.png" width="650px" style="display:block;" alt="Input system setting 1">

<span data-ttu-id="b5547-152">Dietro il sistema di input fornito da MRTK sono disponibili diversi altri sistemi, che consentono di gestire e gestire le complesse interoperabilità necessarie per astrarre le complessità di un Framework multipiattaforma/realtà mista.</span><span class="sxs-lookup"><span data-stu-id="b5547-152">Behind the Input System provided by the MRTK are several other systems, these help to drive and manage the complex inter-weavings required to abstract out the complexities of a multi-platform / mixed reality framework.</span></span>

<img src="../features/Images/MixedRealityToolkitConfigurationProfileScreens/MRTK_InputSystemProfile.png" width="650px" alt="Input system setting 2" style="display:block;">

<span data-ttu-id="b5547-153">Di seguito sono elencati i singoli profili:</span><span class="sxs-lookup"><span data-stu-id="b5547-153">Each of the individual profiles are detailed below:</span></span>

- <span data-ttu-id="b5547-154">Impostazioni stato attivo</span><span class="sxs-lookup"><span data-stu-id="b5547-154">Focus Settings</span></span>
- [<span data-ttu-id="b5547-155">Impostazioni azioni di input</span><span class="sxs-lookup"><span data-stu-id="b5547-155">Input actions settings</span></span>](#input-actions-settings)
- [<span data-ttu-id="b5547-156">Regole azioni di input</span><span class="sxs-lookup"><span data-stu-id="b5547-156">Input actions rules</span></span>](#input-actions-rules)
- [<span data-ttu-id="b5547-157">Configurazione puntatore</span><span class="sxs-lookup"><span data-stu-id="b5547-157">Pointer configuration</span></span>](#pointer-configuration)
- [<span data-ttu-id="b5547-158">Configurazione di movimenti</span><span class="sxs-lookup"><span data-stu-id="b5547-158">Gestures configuration</span></span>](#gestures-configuration)
- [<span data-ttu-id="b5547-159">Comandi vocali</span><span class="sxs-lookup"><span data-stu-id="b5547-159">Speech commands</span></span>](#speech-commands)
- [<span data-ttu-id="b5547-160">Configurazione mapping controller</span><span class="sxs-lookup"><span data-stu-id="b5547-160">Controller mapping configuration</span></span>](#Controller-mapping-configuration)
- [<span data-ttu-id="b5547-161">Impostazioni di visualizzazione del controller</span><span class="sxs-lookup"><span data-stu-id="b5547-161">Controller visualization settings</span></span>](#Controller-visualization-settings)

---
<a name="boundary"></a>

## <a name="boundary-visualization-settings"></a><span data-ttu-id="b5547-162">Impostazioni visualizzazione limite</span><span class="sxs-lookup"><span data-stu-id="b5547-162">Boundary visualization settings</span></span>

<span data-ttu-id="b5547-163">Il sistema di limiti converte il limite percepito segnalato dal sistema di confine/sorveglianza delle piattaforme sottostanti.</span><span class="sxs-lookup"><span data-stu-id="b5547-163">The boundary system translates the perceived boundary reported by the underlying platforms boundary / guardian system.</span></span> <span data-ttu-id="b5547-164">La configurazione del Visualizzatore di limiti consente di visualizzare automaticamente il limite registrato nella scena rispetto alla posizione dell'utente. Il limite viene anche reattivo/aggiornato in base alla posizione in cui l'utente si trasferisce nella scena.</span><span class="sxs-lookup"><span data-stu-id="b5547-164">The Boundary visualizer configuration gives you the ability to automatically show the recorded boundary within your scene relative to the user's position.The boundary will also react / update based on where the user teleports within the scene.</span></span>

<img src="../features/Images/MixedRealityToolkitConfigurationProfileScreens/MRTK_BoundaryVisualizationProfile.png" width="650px" alt="Boundary visualization settings" style="display:block;">

---
<a name="teleportation"></a>

## <a name="teleportation-system-selection"></a><span data-ttu-id="b5547-165">Selezione del sistema di Teleportation</span><span class="sxs-lookup"><span data-stu-id="b5547-165">Teleportation system selection</span></span>

<span data-ttu-id="b5547-166">Il progetto di realtà mista fornisce un sistema di teleporte completo per la gestione di eventi di teleportazione nel progetto selezionato per impostazione predefinita.</span><span class="sxs-lookup"><span data-stu-id="b5547-166">The Mixed Reality Project provides a full featured Teleportation system for managing teleportation events in the project which is selected by default.</span></span>

<img src="../features/Images/MixedRealityToolkitConfigurationProfileScreens/MRTK_TeleportationSystemSelection.png" width="650px" alt="Teleportation system" style="display:block;">

---
<a name="spatialawareness"></a>

## <a name="spatial-awareness-settings"></a><span data-ttu-id="b5547-167">Impostazioni di consapevolezza spaziale</span><span class="sxs-lookup"><span data-stu-id="b5547-167">Spatial awareness settings</span></span>

<span data-ttu-id="b5547-168">Il progetto di realtà mista fornisce un sistema di riconoscimento spaziale ricompilato per l'utilizzo di sistemi di analisi spaziale nel progetto selezionato per impostazione predefinita.</span><span class="sxs-lookup"><span data-stu-id="b5547-168">The Mixed Reality Project provides a rebuilt spatial awareness system for working with spatial scanning systems in the project which is selected by default.</span></span>
<span data-ttu-id="b5547-169">Qui è possibile visualizzare l'architettura dietro il [sistema di riconoscimento spaziale MRTK](../Architecture/SpatialAwareness.md).</span><span class="sxs-lookup"><span data-stu-id="b5547-169">You can view the architecture behind the [MRTK Spatial awareness system here](../Architecture/SpatialAwareness.md).</span></span>

<img src="../features/Images/MixedRealityToolkitConfigurationProfileScreens/MRTK_SpatialAwarenessSystemSelection.png" width="650px" alt="Spatial awareness settings 1" style="display:block;">

<span data-ttu-id="b5547-170">La configurazione della consapevolezza spaziale del Toolkit di realtà mista consente di personalizzare la modalità di avvio del sistema, se è automaticamente quando l'applicazione viene avviata o successivamente a livello di codice, nonché come impostare gli extent per il campo di visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="b5547-170">The Mixed Reality Toolkit spatial awareness configuration lets you tailor how the system starts, whether it is automatically when the application starts or later programmatically as well as setting the extents for the field of view.</span></span>

<span data-ttu-id="b5547-171">Consente inoltre di configurare le impostazioni della rete e della superficie, personalizzando ulteriormente il modo in cui il progetto riconosce l'ambiente.</span><span class="sxs-lookup"><span data-stu-id="b5547-171">It also lets you configure the mesh and surface settings, further customizing how your project understands the environment around you.</span></span>

<span data-ttu-id="b5547-172">Questa operazione è applicabile solo ai dispositivi che possono fornire un ambiente analizzato.</span><span class="sxs-lookup"><span data-stu-id="b5547-172">This is only applicable for devices that can provide a scanned environment.</span></span>

<img src="../features/Images/MixedRealityToolkitConfigurationProfileScreens/MRTK_SpatialAwarenessProfile.png" width="650px" alt="Spatial awarensess setting 1" style="display:block;">

---
<a name="diagnostic"></a>

## <a name="diagnostics-settings"></a><span data-ttu-id="b5547-173">Impostazioni di diagnostica</span><span class="sxs-lookup"><span data-stu-id="b5547-173">Diagnostics settings</span></span>

<span data-ttu-id="b5547-174">Una funzionalità facoltativa ma estremamente utile di MRTK è la funzionalità di diagnostica del plug-in.</span><span class="sxs-lookup"><span data-stu-id="b5547-174">An optional but highly useful feature of the MRTK is the plugin diagnostics functionality.</span></span>

<img src="../features/Images/MixedRealityToolkitConfigurationProfileScreens/MRTK_DiagnosticsSystemSelection.png" width="650px" alt="Diagnostics system selection" style="display:block;">

<span data-ttu-id="b5547-175">Il profilo di diagnostica fornisce diversi sistemi semplici da monitorare durante l'esecuzione del progetto, inclusa un'opzione di attivazione/disattivazione utile per abilitare o disabilitare il pannello di visualizzazione nella scena.</span><span class="sxs-lookup"><span data-stu-id="b5547-175">The diagnostics profile provides several simple systems to monitor whilst the project is running, including a handy On/Off switch to enable / disable the display panel in the scene.</span></span>

<img src="../features/Images/MixedRealityToolkitConfigurationProfileScreens/MRTK_DiagnosticsProfile.png" width="650px" alt="Diagnostics profile screen" style="display:block;">

---
<a name="scenesystem"></a>

## <a name="scene-system-settings"></a><span data-ttu-id="b5547-176">Impostazioni del sistema di scena</span><span class="sxs-lookup"><span data-stu-id="b5547-176">Scene system settings</span></span>

<span data-ttu-id="b5547-177">MRTK fornisce questo servizio facoltativo che consente di gestire il caricamento e lo scaricamento di scene additive complesse.</span><span class="sxs-lookup"><span data-stu-id="b5547-177">The MRTK provides this optional service to help you manage complex additive scene loading / unloading.</span></span> <span data-ttu-id="b5547-178">Per decidere se il sistema di scena costituisce una scelta ottimale per il progetto, vedere la pagina relativa al [sistema della scena Introduzione Guida.](../features/SceneSystem/SceneSystemGettingStarted.md)</span><span class="sxs-lookup"><span data-stu-id="b5547-178">To decide if the Scene System would be a good fit for your project, read the [Scene System Getting Started Guide.](../features/SceneSystem/SceneSystemGettingStarted.md)</span></span>

<img src="../features/Images/MixedRealityToolkitConfigurationProfileScreens/MRTK_SceneSystemProfile.png" width="650px" alt="Scene system settings" style="display:block;">

---
<a name="services"></a>

## <a name="additional-services-settings"></a><span data-ttu-id="b5547-179">Impostazioni servizi aggiuntivi</span><span class="sxs-lookup"><span data-stu-id="b5547-179">Additional services settings</span></span>

<span data-ttu-id="b5547-180">Una delle aree più avanzate del Toolkit di realtà mista è l'implementazione del [modello del localizzatore di servizi](https://en.wikipedia.org/wiki/Service_locator_pattern) che consente la registrazione di qualsiasi "servizio" con il Framework.</span><span class="sxs-lookup"><span data-stu-id="b5547-180">One of the more advanced areas of the Mixed Reality Toolkit is its [service locator pattern](https://en.wikipedia.org/wiki/Service_locator_pattern) implementation which allows the registering of any "Service" with the framework.</span></span> <span data-ttu-id="b5547-181">In questo modo è possibile estendere il Framework con nuove funzionalità o sistemi, ma anche consentire ai progetti di sfruttare queste funzionalità per registrare i propri componenti Runtime.</span><span class="sxs-lookup"><span data-stu-id="b5547-181">This allows the framework to be both extended with new features / systems easily but also allows for projects to take advantage of these capabilities to register their own runtime components.</span></span>

<span data-ttu-id="b5547-182">Qualsiasi servizio registrato ottiene comunque il vantaggio completo di tutti gli eventi di Unity, senza l'overhead e i costi di implementazione di un monocomportamento o di modelli singleton goffi.</span><span class="sxs-lookup"><span data-stu-id="b5547-182">Any registered service still gets the full advantage of all of the Unity events, without the overhead and cost of implementing a MonoBehaviour or clunky singleton patterns.</span></span> <span data-ttu-id="b5547-183">Questo consente i componenti C# puri senza overhead di scena per l'esecuzione di processi in primo piano e in background, ad esempio i sistemi di generazione, la logica del gioco di runtime o praticamente qualsiasi altra cosa.</span><span class="sxs-lookup"><span data-stu-id="b5547-183">This allows for pure C# components with no scene overhead for running both foreground and background processes, e.g. spawning systems, runtime game logic, or practically anything else.</span></span>

<img src="../features/Images/MixedRealityToolkitConfigurationProfileScreens/MRTK_RegisteredServiceProvidersProfile.png" alt="Additional services settings" width="650px" style="display:block;">

---
<a name="inputactions"></a>

## <a name="input-actions-settings"></a><span data-ttu-id="b5547-184">Impostazioni azioni di input</span><span class="sxs-lookup"><span data-stu-id="b5547-184">Input actions settings</span></span>

<span data-ttu-id="b5547-185">Le azioni di input consentono di astrarre eventuali interazioni fisiche e input da un progetto di Runtime.</span><span class="sxs-lookup"><span data-stu-id="b5547-185">Input actions provide a way to abstract any physical interactions and input from a runtime project.</span></span> <span data-ttu-id="b5547-186">Tutto l'input fisico (da controller/mano/mouse/ecc) viene convertito in un'azione di input logica da usare nel progetto di Runtime.</span><span class="sxs-lookup"><span data-stu-id="b5547-186">All physical input (from controllers / hands / mouse / etc) is translated in to a logical input action for use in your runtime project.</span></span> <span data-ttu-id="b5547-187">In questo modo, indipendentemente dalla provenienza dell'input, il progetto implementa semplicemente queste azioni come "operazioni da eseguire" o "interagire con" nelle scene.</span><span class="sxs-lookup"><span data-stu-id="b5547-187">This ensures no matter where the input comes from, your project simply implements these actions as "Things to do" or "Interact with" in your scenes.</span></span>

<span data-ttu-id="b5547-188">Per creare una nuova azione di input, è sufficiente fare clic sul pulsante "Aggiungi una nuova azione" e immettere un nome descrittivo per il valore che rappresenta.</span><span class="sxs-lookup"><span data-stu-id="b5547-188">To create a new input action, simply click the "Add a new Action" button and enter a friendly text name for what it represents.</span></span> <span data-ttu-id="b5547-189">È quindi necessario solo selezionare un asse (il tipo di dati) che l'azione deve fornire o, nel caso di controller fisici, il tipo di input fisico a cui è possibile collegarsi, ad esempio:</span><span class="sxs-lookup"><span data-stu-id="b5547-189">You then only need select an axis (the type of data) the action is meant to convey, or in the case of physical controllers, the physical input type it can be attached to, for example:</span></span>

| <span data-ttu-id="b5547-190">Vincolo asse</span><span class="sxs-lookup"><span data-stu-id="b5547-190">Axis Constraint</span></span> | <span data-ttu-id="b5547-191">Tipo di dati</span><span class="sxs-lookup"><span data-stu-id="b5547-191">Data Type</span></span> | <span data-ttu-id="b5547-192">Descrizione</span><span class="sxs-lookup"><span data-stu-id="b5547-192">Description</span></span> | <span data-ttu-id="b5547-193">Esempio di utilizzo</span><span class="sxs-lookup"><span data-stu-id="b5547-193">Example use</span></span> |
| :--- | :--- | :--- | :--- |
| <span data-ttu-id="b5547-194">nessuno</span><span class="sxs-lookup"><span data-stu-id="b5547-194">None</span></span> | <span data-ttu-id="b5547-195">Nessun dato</span><span class="sxs-lookup"><span data-stu-id="b5547-195">No data</span></span> | <span data-ttu-id="b5547-196">Usato per un'azione o un evento vuoto</span><span class="sxs-lookup"><span data-stu-id="b5547-196">Used for an empty action or event</span></span> | <span data-ttu-id="b5547-197">Trigger evento</span><span class="sxs-lookup"><span data-stu-id="b5547-197">Event Trigger</span></span> |
| <span data-ttu-id="b5547-198">RAW (riservato)</span><span class="sxs-lookup"><span data-stu-id="b5547-198">Raw (reserved)</span></span> | <span data-ttu-id="b5547-199">object</span><span class="sxs-lookup"><span data-stu-id="b5547-199">object</span></span> | <span data-ttu-id="b5547-200">Riservate per utilizzo futuro</span><span class="sxs-lookup"><span data-stu-id="b5547-200">Reserved for future use</span></span> | <span data-ttu-id="b5547-201">N/D</span><span class="sxs-lookup"><span data-stu-id="b5547-201">N/A</span></span> |
| <span data-ttu-id="b5547-202">Digitale</span><span class="sxs-lookup"><span data-stu-id="b5547-202">Digital</span></span> | <span data-ttu-id="b5547-203">bool</span><span class="sxs-lookup"><span data-stu-id="b5547-203">bool</span></span> | <span data-ttu-id="b5547-204">Un valore booleano per i dati di tipo</span><span class="sxs-lookup"><span data-stu-id="b5547-204">A boolean on or off type data</span></span> | <span data-ttu-id="b5547-205">Pulsante controller</span><span class="sxs-lookup"><span data-stu-id="b5547-205">A controller button</span></span> |
| <span data-ttu-id="b5547-206">Asse singolo</span><span class="sxs-lookup"><span data-stu-id="b5547-206">Single Axis</span></span> | <span data-ttu-id="b5547-207">float</span><span class="sxs-lookup"><span data-stu-id="b5547-207">float</span></span> | <span data-ttu-id="b5547-208">Un singolo valore di dati di precisione</span><span class="sxs-lookup"><span data-stu-id="b5547-208">A single precision data value</span></span> | <span data-ttu-id="b5547-209">Un input con intervallo, ad esempio un trigger</span><span class="sxs-lookup"><span data-stu-id="b5547-209">A ranged input, e.g. a trigger</span></span> |
| <span data-ttu-id="b5547-210">Asse doppio</span><span class="sxs-lookup"><span data-stu-id="b5547-210">Dual Axis</span></span> | <span data-ttu-id="b5547-211">Vector2</span><span class="sxs-lookup"><span data-stu-id="b5547-211">Vector2</span></span> | <span data-ttu-id="b5547-212">Data di tipo float doppio per più assi</span><span class="sxs-lookup"><span data-stu-id="b5547-212">A dual float type date for multiple axis</span></span> | <span data-ttu-id="b5547-213">DPad o levetta</span><span class="sxs-lookup"><span data-stu-id="b5547-213">A Dpad or Thumbstick</span></span> |
| <span data-ttu-id="b5547-214">Tre posizioni DOF</span><span class="sxs-lookup"><span data-stu-id="b5547-214">Three Dof Position</span></span> | <span data-ttu-id="b5547-215">Vector3</span><span class="sxs-lookup"><span data-stu-id="b5547-215">Vector3</span></span> | <span data-ttu-id="b5547-216">Dati di tipo posizionale da con 3 assi a virgola mobile</span><span class="sxs-lookup"><span data-stu-id="b5547-216">Positional type data from with 3 float axis</span></span> | <span data-ttu-id="b5547-217">controller solo stile posizione 3D</span><span class="sxs-lookup"><span data-stu-id="b5547-217">3D position style only controller</span></span> |
| <span data-ttu-id="b5547-218">Rotazione di tre DOF</span><span class="sxs-lookup"><span data-stu-id="b5547-218">Three Dof Rotation</span></span> | <span data-ttu-id="b5547-219">Quaternion</span><span class="sxs-lookup"><span data-stu-id="b5547-219">Quaternion</span></span> | <span data-ttu-id="b5547-220">Input solo rotazionale con 4 assi a virgola mobile</span><span class="sxs-lookup"><span data-stu-id="b5547-220">Rotational only input with 4 float axis</span></span> | <span data-ttu-id="b5547-221">Un controller di stile A tre gradi, ad esempio un controller Oculus go</span><span class="sxs-lookup"><span data-stu-id="b5547-221">A Three degrees style controller, e.g. Oculus Go controller</span></span> |
| <span data-ttu-id="b5547-222">Sei DOF</span><span class="sxs-lookup"><span data-stu-id="b5547-222">Six Dof</span></span> | <span data-ttu-id="b5547-223">Pose di realtà mista (Vector3, Quaternion)</span><span class="sxs-lookup"><span data-stu-id="b5547-223">Mixed Reality Pose (Vector3, Quaternion)</span></span> | <span data-ttu-id="b5547-224">Input di tipo posizione e rotazione con i componenti Vector3 e Quaternion</span><span class="sxs-lookup"><span data-stu-id="b5547-224">A position and rotation style input with both Vector3 and Quaternion components</span></span> | <span data-ttu-id="b5547-225">Un controller di movimento o un puntatore</span><span class="sxs-lookup"><span data-stu-id="b5547-225">A motion controller or Pointer</span></span> |

<span data-ttu-id="b5547-226">Gli eventi che utilizzano azioni di input non sono limitati ai controller fisici e possono comunque essere utilizzati all'interno del progetto affinché gli effetti di runtime generino nuove azioni.</span><span class="sxs-lookup"><span data-stu-id="b5547-226">Events utilizing input actions are not limited to physical controllers and can still be utilized within the project to have runtime effects generate new actions.</span></span>

> [!NOTE]
> <span data-ttu-id="b5547-227">Le azioni di input sono uno dei pochi componenti che non sono modificabili in fase di esecuzione, bensì una configurazione in fase di progettazione.</span><span class="sxs-lookup"><span data-stu-id="b5547-227">Input actions are one of the few components which is not editable at runtime, they are a design time configuration only.</span></span> <span data-ttu-id="b5547-228">Questo profilo non deve essere scambiato mentre il progetto è in esecuzione a causa della dipendenza del Framework (e dei progetti) nell'ID generato per ogni azione.</span><span class="sxs-lookup"><span data-stu-id="b5547-228">This profile should not be swapped out whilst the project is running due to the framework (and your projects) dependency on the ID's generated for each action.</span></span>

<img src="../features/Images/MixedRealityToolkitConfigurationProfileScreens/MRTK_InputActionsProfile.png" width="650px" alt="Configuration profile" style="display:block;">

---
<a name="inputactionrules"></a>

## <a name="input-actions-rules"></a><span data-ttu-id="b5547-229">Regole azioni di input</span><span class="sxs-lookup"><span data-stu-id="b5547-229">Input actions rules</span></span>

<span data-ttu-id="b5547-230">Le regole di azione di input consentono di convertire automaticamente un evento generato per un'azione di input in in azioni diverse in base al relativo valore di dati.</span><span class="sxs-lookup"><span data-stu-id="b5547-230">Input action rules provide a way to automatically translate an event raised for one input action in to different actions based on its data value.</span></span> <span data-ttu-id="b5547-231">Questi vengono gestiti senza problemi all'interno del Framework e non comportano costi di prestazioni.</span><span class="sxs-lookup"><span data-stu-id="b5547-231">These are managed seamlessly within the framework and do not incur any performance costs.</span></span>

<span data-ttu-id="b5547-232">Ad esempio, la conversione del singolo evento di input a doppio asse da un DPad in alle 4 azioni corrispondenti "DPad UP"/"DPad Down"/"DPad left"/"DPad Right", come illustrato nell'immagine seguente.</span><span class="sxs-lookup"><span data-stu-id="b5547-232">For example, converting the single dual axis input event from a DPad in to the 4 corresponding "Dpad Up" / "DPad Down" / "Dpad Left" / "Dpad Right" actions (as shown in the image below).</span></span>

<span data-ttu-id="b5547-233">Questa operazione può essere eseguita anche nel codice personalizzato.</span><span class="sxs-lookup"><span data-stu-id="b5547-233">This could also be done in your own code.</span></span> <span data-ttu-id="b5547-234">Tuttavia, visto che si tratta di un modello molto comune, il Framework fornisce un meccanismo per eseguire questa operazione "predefinita".</span><span class="sxs-lookup"><span data-stu-id="b5547-234">However, seeing as this was a very common pattern, the framework provides a mechanism to do this "out of the box"</span></span>

<span data-ttu-id="b5547-235">Le regole di azione di input possono essere configurate per uno qualsiasi degli assi di input disponibili.</span><span class="sxs-lookup"><span data-stu-id="b5547-235">Input action Rules can be configured for any of the available input axis.</span></span> <span data-ttu-id="b5547-236">Tuttavia, le azioni di input da un tipo di asse possono essere convertite in un'altra azione di input dello stesso tipo di asse.</span><span class="sxs-lookup"><span data-stu-id="b5547-236">However, input actions from one axis type can be translated to another input action of the same axis type.</span></span> <span data-ttu-id="b5547-237">È possibile eseguire il mapping di un'azione a doppio asse a un'altra azione a due assi, ma non a un'azione digitale o nessuna.</span><span class="sxs-lookup"><span data-stu-id="b5547-237">You can map a dual axis action to another dual axis action, but not to a digital or none action.</span></span>

![Profilo delle regole di azione di input](../features/Images/MixedRealityToolkitConfigurationProfileScreens/MRTK_InputActionRulesProfile.png)

---
<a name="pointer"></a>

## <a name="pointer-configuration"></a><span data-ttu-id="b5547-239">Configurazione puntatore</span><span class="sxs-lookup"><span data-stu-id="b5547-239">Pointer configuration</span></span>

<span data-ttu-id="b5547-240">I puntatori vengono usati per guidare l'interattività nella scena da qualsiasi dispositivo di input, assegnando una direzione e un hit test a qualsiasi oggetto in una scena (con un Collider collegato o è un componente dell'interfaccia utente).</span><span class="sxs-lookup"><span data-stu-id="b5547-240">Pointers are used to drive interactivity in the scene from any input device, giving both a direction and hit test with any object in a scene (that has a collider attached, or is a UI component).</span></span> <span data-ttu-id="b5547-241">Per impostazione predefinita, i puntatori sono configurati automaticamente per i controller, le cuffie (sguardo/stato attivo) e l'input del mouse/tocco.</span><span class="sxs-lookup"><span data-stu-id="b5547-241">Pointers are by default automatically configured for controllers, headsets (gaze / focus) and mouse / touch input.</span></span>

<span data-ttu-id="b5547-242">I puntatori possono anche essere visualizzati all'interno della scena attiva usando uno dei molti componenti linea forniti dal Toolkit di realtà mista o uno dei propri se implementano l'interfaccia IMixedRealityPointer di MRTK.</span><span class="sxs-lookup"><span data-stu-id="b5547-242">Pointers can also be visualized within the active scene using one of the many line components provided by the Mixed Reality Toolkit, or any of your own if they implement the MRTK IMixedRealityPointer interface.</span></span>

<img src="../features/Images/MixedRealityToolkitConfigurationProfileScreens/MRTK_InputPointerProfile.png" width="650px" alt="Pointer configuratoion" style="display:block;">

- <span data-ttu-id="b5547-243">Extent di puntamento: determina l'extent di puntamento globale per tutti i puntatori, incluso lo sguardo.</span><span class="sxs-lookup"><span data-stu-id="b5547-243">Pointing Extent: Determines the global pointing extent for all pointers, including gaze.</span></span>
- <span data-ttu-id="b5547-244">Pointing Raycast layer masks: determina a quali puntatori si raycast.</span><span class="sxs-lookup"><span data-stu-id="b5547-244">Pointing Raycast Layer Masks: Determines which layers pointers will raycast against.</span></span>
- <span data-ttu-id="b5547-245">Debug di disegni che puntano raggi: un helper di debug per la visualizzazione dei raggi usati per Raycasting.</span><span class="sxs-lookup"><span data-stu-id="b5547-245">Debug Draw Pointing Rays: A debug helper for visualizing the rays used for raycasting.</span></span>
- <span data-ttu-id="b5547-246">Disegni di debug che puntano i colori: un set di colori da usare per la visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="b5547-246">Debug Draw Pointing Rays Colors: A set of colors to use for visualizing.</span></span>
- <span data-ttu-id="b5547-247">Precostruzione del cursore di sguardi: consente di specificare facilmente un cursore globale di sguardi per qualsiasi scena.</span><span class="sxs-lookup"><span data-stu-id="b5547-247">Gaze cursor prefab: Makes it easy to specify a global gaze cursor for any scene.</span></span>

<span data-ttu-id="b5547-248">È disponibile un pulsante Helper aggiuntivo che consente di passare rapidamente al provider di sguardi per eseguire l'override di alcuni valori specifici per lo sguardo, se necessario.</span><span class="sxs-lookup"><span data-stu-id="b5547-248">There's an additional helper button to quickly jump to the Gaze Provider to override some specific values for Gaze if needed.</span></span>

---
<a name="gestures"></a>

## <a name="gestures-configuration"></a><span data-ttu-id="b5547-249">Configurazione di movimenti</span><span class="sxs-lookup"><span data-stu-id="b5547-249">Gestures configuration</span></span>

<span data-ttu-id="b5547-250">I movimenti sono un'implementazione specifica del sistema che consente di assegnare azioni di input ai vari metodi di input "movimento" forniti da vari SDK (ad esempio HoloLens).</span><span class="sxs-lookup"><span data-stu-id="b5547-250">Gestures are a system specific implementation allowing you to assign input actions to the various "Gesture" input methods provided by various SDKs (e.g. HoloLens).</span></span>

> [!NOTE]
> <span data-ttu-id="b5547-251">L'implementazione dei movimenti correnti è solo per il HoloLens e verrà migliorata per gli altri sistemi Man mano che vengono aggiunti al Toolkit in futuro (nessuna data ancora).</span><span class="sxs-lookup"><span data-stu-id="b5547-251">The current Gestures implementation is for the HoloLens only and will be enhanced for other systems as they are added to the Toolkit in the future (no dates yet).</span></span>

<img src="../features/Images/MixedRealityToolkitConfigurationProfileScreens/MRTK_GesturesProfile.png" width="650px" alt="Gesture configuration" style="display:block;">

---
<a name="speech"></a>

## <a name="speech-commands"></a><span data-ttu-id="b5547-252">Comandi vocali</span><span class="sxs-lookup"><span data-stu-id="b5547-252">Speech commands</span></span>

<span data-ttu-id="b5547-253">Analogamente ai movimenti, alcune piattaforme di runtime forniscono anche una funzionalità intelligente di riconoscimento vocale con la possibilità di generare comandi che possono essere ricevuti da un progetto Unity.</span><span class="sxs-lookup"><span data-stu-id="b5547-253">Like gestures, some runtime platforms also provide intelligent "Speech to Text" functionality with the ability to generate commands that can be received by a Unity project.</span></span> <span data-ttu-id="b5547-254">Questo profilo di configurazione consente di configurare quanto segue:</span><span class="sxs-lookup"><span data-stu-id="b5547-254">This configuration profile allows you to configure the following:</span></span>

1. <span data-ttu-id="b5547-255">Impostazioni generali: "avvia comportamento" impostato su avvio automatico o avvio manuale determina se inizializzare KeywordRecognizer all'avvio del sistema di input o lasciare che il progetto decida quando inizializzare il KeywordRecognizer.</span><span class="sxs-lookup"><span data-stu-id="b5547-255">General Settings - "Start Behavior" set to Auto Start or Manual Start determines whether to initialize KeywordRecognizer at input system startup or let the project decide when to initialize the KeywordRecognizer.</span></span> <span data-ttu-id="b5547-256">"Livello di confidenza del riconoscimento" viene usato per inizializzare l' [API KeywordRecognizer](https://docs.unity3d.com/ScriptReference/Windows.Speech.KeywordRecognizer-ctor.html) di Unity</span><span class="sxs-lookup"><span data-stu-id="b5547-256">"Recognition Confidence Level" is used to initialize Unity's [KeywordRecognizer API](https://docs.unity3d.com/ScriptReference/Windows.Speech.KeywordRecognizer-ctor.html)</span></span>
2. <span data-ttu-id="b5547-257">Comandi vocali: registra "Words" e li converte in azioni di input che possono essere ricevute dal progetto.</span><span class="sxs-lookup"><span data-stu-id="b5547-257">Speech Commands - Registers "words" and translates them in to input actions that can be received by your project.</span></span> <span data-ttu-id="b5547-258">Possono anche essere collegati alle azioni della tastiera, se necessario.</span><span class="sxs-lookup"><span data-stu-id="b5547-258">They can also be attached to keyboard actions if required.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b5547-259">Il sistema supporta attualmente solo il riconoscimento vocale quando viene eseguito su piattaforme Windows 10, ad esempio HoloLens e Windows 10 desktop e sarà migliorato per altri sistemi Man mano che vengono aggiunti a MRTK in futuro (nessuna data).</span><span class="sxs-lookup"><span data-stu-id="b5547-259">The system currently only supports speech when running on Windows 10 platforms, e.g. HoloLens and Windows 10 desktop and will be enhanced for other systems as they are added to MRTK in the future (no dates yet).</span></span>

<img src="../features/Images/MixedRealityToolkitConfigurationProfileScreens/MRTK_SpeechCommandsProfile.png" width="650px" alt="Speech command profile" style="display:block;">

---
<a name="mapping"></a>

## <a name="controller-mapping-configuration"></a><span data-ttu-id="b5547-260">Configurazione mapping controller</span><span class="sxs-lookup"><span data-stu-id="b5547-260">Controller mapping configuration</span></span>

<span data-ttu-id="b5547-261">Una delle schermate di configurazione principali per il Toolkit di realtà mista è la possibilità di configurare ed eseguire il mapping dei vari tipi di controller che possono essere utilizzati dal progetto.</span><span class="sxs-lookup"><span data-stu-id="b5547-261">One of the core configuration screens for the Mixed Reality Toolkit is the ability to configure and map the various types of controllers that can be utilized by your project.</span></span>

<span data-ttu-id="b5547-262">La schermata di configurazione seguente consente di configurare i controller attualmente riconosciuti dal Toolkit.</span><span class="sxs-lookup"><span data-stu-id="b5547-262">The configuration screen below allows you to configure any of the controllers currently recognized by the toolkit.</span></span>

<img src="../features/Images/MixedRealityToolkitConfigurationProfileScreens/MRTK_ControllerMappingProfile.png" width="650px" alt="Controller maping profile" style="display:block;">

<span data-ttu-id="b5547-263">MRTK fornisce una configurazione predefinita per i controller/sistemi seguenti:</span><span class="sxs-lookup"><span data-stu-id="b5547-263">The MRTK provides a default configuration for the following controllers / systems:</span></span>

- <span data-ttu-id="b5547-264">Mouse (incluso il supporto del mouse spaziale 3D)</span><span class="sxs-lookup"><span data-stu-id="b5547-264">Mouse (including 3D spatial mouse support)</span></span>
- <span data-ttu-id="b5547-265">Touch screen</span><span class="sxs-lookup"><span data-stu-id="b5547-265">Touch Screen</span></span>
- <span data-ttu-id="b5547-266">Controller Xbox</span><span class="sxs-lookup"><span data-stu-id="b5547-266">Xbox controllers</span></span>
- <span data-ttu-id="b5547-267">Controller della realtà mista di Windows</span><span class="sxs-lookup"><span data-stu-id="b5547-267">Windows Mixed Reality controllers</span></span>
- <span data-ttu-id="b5547-268">Movimenti HoloLens</span><span class="sxs-lookup"><span data-stu-id="b5547-268">HoloLens Gestures</span></span>
- <span data-ttu-id="b5547-269">Controller della bacchetta HTC vive</span><span class="sxs-lookup"><span data-stu-id="b5547-269">HTC Vive wand controllers</span></span>
- <span data-ttu-id="b5547-270">Controller Oculus touch</span><span class="sxs-lookup"><span data-stu-id="b5547-270">Oculus Touch controllers</span></span>
- <span data-ttu-id="b5547-271">Controller remoto Oculus</span><span class="sxs-lookup"><span data-stu-id="b5547-271">Oculus Remote controller</span></span>
- <span data-ttu-id="b5547-272">Dispositivi OpenVR generici (solo utenti avanzati)</span><span class="sxs-lookup"><span data-stu-id="b5547-272">Generic OpenVR devices (advanced users only)</span></span>

<span data-ttu-id="b5547-273">Facendo clic sull'immagine per uno dei sistemi controller predefiniti è possibile configurare una singola azione di input per tutti gli input corrispondenti. ad esempio, vedere la schermata di configurazione di Oculus touch controller riportata di seguito:</span><span class="sxs-lookup"><span data-stu-id="b5547-273">Clicking on the Image for any of the pre-built controller systems allows you to configure a single input action for all its corresponding inputs, for example, see the Oculus Touch controller configuration screen below:</span></span>

<img src="../features/Images/MixedRealityToolkitConfigurationProfileScreens/MRTK_WindowsMixedRealityControllerConfigScreen.png" width="650px" alt="Configuration profile screen" style="display:block;">

<span data-ttu-id="b5547-274">È disponibile anche una schermata avanzata per la configurazione di altri controller di input OpenVR o Unity che non sono stati identificati in precedenza.</span><span class="sxs-lookup"><span data-stu-id="b5547-274">There is also an advanced screen for configuring other OpenVR or Unity input controllers that are not identified above.</span></span>

---
<a name="visualization"></a>

## <a name="controller-visualization-settings"></a><span data-ttu-id="b5547-275">Impostazioni di visualizzazione del controller</span><span class="sxs-lookup"><span data-stu-id="b5547-275">Controller visualization settings</span></span>

<span data-ttu-id="b5547-276">Oltre al mapping del controller, viene fornito un profilo di configurazione separato per personalizzare il modo in cui vengono presentati i controller all'interno delle scene.</span><span class="sxs-lookup"><span data-stu-id="b5547-276">In addition to the controller mapping, a separate configuration profile is provided to customize how your controllers are presented within your scenes.</span></span>

<span data-ttu-id="b5547-277">Questa operazione può essere configurata in un "globale" (tutte le istanze di un controller per una specifica mano) o specifica per un singolo tipo di controller/mano.</span><span class="sxs-lookup"><span data-stu-id="b5547-277">This can be configured at a "Global" (all instances of a controller for a specific hand) or specific to an individual controller type / hand.</span></span>

<span data-ttu-id="b5547-278">MRTK supporta anche modelli di controller SDK nativi per la realtà mista di Windows e OpenVR.</span><span class="sxs-lookup"><span data-stu-id="b5547-278">The MRTK also supports native SDK controller models for Windows Mixed Reality and OpenVR.</span></span> <span data-ttu-id="b5547-279">Questi vengono caricati come GameObject nella scena e posizionati usando il rilevamento del controller della piattaforma.</span><span class="sxs-lookup"><span data-stu-id="b5547-279">These are loaded as GameObjects in your scene and positioned using the platform's controller tracking.</span></span>

<span data-ttu-id="b5547-280">Se la rappresentazione del controller nella scena deve essere sottoposta a offset dalla posizione del controller fisico, è sufficiente impostare tale offset rispetto al prefabbricato del modello del controller (ad esempio, impostando la posizione di trasformazione del prefabbricato del controller con una posizione di offset).</span><span class="sxs-lookup"><span data-stu-id="b5547-280">If your controller representation in the scene needs to be offset from the physical controller position, then simply set that offset against the controller model's prefab (e.g. setting the transform position of the controller prefab with an offset position).</span></span>

<img src="../features/Images/MixedRealityToolkitConfigurationProfileScreens/MRTK_ControllerVisualizationProfile.png" width="650px" alt="Visualization  setting" style="display:block;">

<a name="editor-utilities"></a>

## <a name="editor-utilities"></a><span data-ttu-id="b5547-281">Utilità Editor</span><span class="sxs-lookup"><span data-stu-id="b5547-281">Editor utilities</span></span>

<span data-ttu-id="b5547-282">Le utilità seguenti funzionano solo nell'editor e sono utili per migliorare la produttività dello sviluppo.</span><span class="sxs-lookup"><span data-stu-id="b5547-282">The following utilities work only in the editor and are useful to improve development productivity.</span></span>

![Utilità di configurazione dell'editor MRTK](../features/Images/MixedRealityToolkitConfigurationProfileScreens/MRTK_EditorConfiguration.png)

### <a name="service-inspectors"></a><span data-ttu-id="b5547-284">Controlli servizio</span><span class="sxs-lookup"><span data-stu-id="b5547-284">Service inspectors</span></span>

<span data-ttu-id="b5547-285">I controlli servizio sono una funzionalità di solo editor che genera oggetti in scena che rappresentano servizi attivi.</span><span class="sxs-lookup"><span data-stu-id="b5547-285">Service Inspectors are an editor-only feature that generates in-scene objects representing active services.</span></span> <span data-ttu-id="b5547-286">Selezionando questi oggetti vengono visualizzati i controlli che offrono collegamenti alla documentazione, il controllo sulle visualizzazioni dell'editor e informazioni dettagliate sullo stato del servizio.</span><span class="sxs-lookup"><span data-stu-id="b5547-286">Selecting these objects displays inspectors which offer documentation links, control over editor visualizations and insight into the state of the service.</span></span>

<img src="../features/Images/MixedRealityToolkitConfigurationProfileScreens/MRTK_ServiceInspectors.PNG" width="350px" alt="Service inspector" style="display:block;">

<span data-ttu-id="b5547-287">È possibile abilitare gli ispettori dei servizi controllando *Usa controlli servizio* in *Impostazioni editor* nel profilo di configurazione.</span><span class="sxs-lookup"><span data-stu-id="b5547-287">You can enable service inspectors by checking *Use Service Inspectors* under *Editor Settings* in the Configuration Profile.</span></span>

### <a name="depth-buffer-renderer"></a><span data-ttu-id="b5547-288">Renderer buffer profondità</span><span class="sxs-lookup"><span data-stu-id="b5547-288">Depth buffer renderer</span></span>

<span data-ttu-id="b5547-289">La condivisione del buffer di profondità con alcune piattaforme di realtà miste può migliorare la [stabilizzazione di ologrammi](../Performance/hologram-stabilization.md).</span><span class="sxs-lookup"><span data-stu-id="b5547-289">Sharing the depth buffer with some mixed reality platforms can improve [hologram stabilization](../Performance/hologram-stabilization.md).</span></span> <span data-ttu-id="b5547-290">La piattaforma per la realtà mista di Windows, ad esempio, può modificare la scena di cui è stato eseguito il rendering per ogni pixel per tenere conto dei movimenti di intestazioni sottili durante il tempo impiegato per il rendering del frame.</span><span class="sxs-lookup"><span data-stu-id="b5547-290">For example, the Windows Mixed Reality platform can modify the rendered scene per-pixel to account for subtle head movements during the time it took to render a frame.</span></span> <span data-ttu-id="b5547-291">Tuttavia, queste tecniche richiedono buffer di profondità con dati accurati per individuare la posizione e la distanza di geometria dall'utente.</span><span class="sxs-lookup"><span data-stu-id="b5547-291">However, these techniques require depth buffers with accurate data to know where and how far geometry is from the user.</span></span>

<span data-ttu-id="b5547-292">Per assicurarsi che una scena esegua il rendering di tutti i dati necessari nel buffer di profondità, gli sviluppatori possono abilitare o disabilitare la funzionalità di *buffer di profondità di rendering* in *Impostazioni editor* nel profilo di configurazione.</span><span class="sxs-lookup"><span data-stu-id="b5547-292">To ensure a scene renders all necessary data to the depth buffer, developers can toggle the *Render Depth Buffer* feature under *Editor Settings* in the Configuration Profile.</span></span> <span data-ttu-id="b5547-293">Questa operazione condurrà il buffer di profondità corrente e ne eseguirà il rendering come colore nella visualizzazione della scena applicando un effetto di post-elaborazione, [`DepthBufferRenderer`](xref:Microsoft.MixedReality.Toolkit.Rendering.DepthBufferRenderer) , alla fotocamera principale.</span><span class="sxs-lookup"><span data-stu-id="b5547-293">This will take the current depth buffer and render it as color to the scene view by applying a post-processing effect, [`DepthBufferRenderer`](xref:Microsoft.MixedReality.Toolkit.Rendering.DepthBufferRenderer), to the main camera.</span></span>

<span data-ttu-id="b5547-294">![Utilità del buffer di profondità ](../features/Images/MixedRealityToolkitConfigurationProfileScreens/MRTK_DepthBufferExample.gif)
 <sup>di rendering il cilindro blu nella scena ha un materiale con ZWrite off, quindi non viene scritto alcun dato di profondità</sup></span><span class="sxs-lookup"><span data-stu-id="b5547-294">![Render Depth Buffer Utility](../features/Images/MixedRealityToolkitConfigurationProfileScreens/MRTK_DepthBufferExample.gif)
<sup>The blue cylinder in the scene has a material with ZWrite off so no depth data is written</sup></span></span>

## <a name="changing-profiles-at-runtime"></a><span data-ttu-id="b5547-295">Modifica dei profili in fase di esecuzione</span><span class="sxs-lookup"><span data-stu-id="b5547-295">Changing profiles at runtime</span></span>

<span data-ttu-id="b5547-296">È possibile aggiornare i profili in fase di esecuzione e in genere esistono due diversi scenari e tempi in cui questo è utile:</span><span class="sxs-lookup"><span data-stu-id="b5547-296">It is possible to update profiles at runtime, and there are generally two different scenarios and times in which in this is helpful:</span></span>

1. <span data-ttu-id="b5547-297">All'avvio, prima dell'inizializzazione di MRTK, lo scambio del profilo per abilitare o disabilitare funzionalità diverse in base alle funzionalità del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="b5547-297">At startup, before the MRTK is initialized, swapping the profile to enable/disable different features based on the device capabilities.</span></span> <span data-ttu-id="b5547-298">Se, ad esempio, l'esperienza viene eseguita in VR senza hardware per il mapping spaziale, probabilmente non ha senso avere un componente di mapping spaziale abilitato.</span><span class="sxs-lookup"><span data-stu-id="b5547-298">For example, if the experience is running in VR that doesn't have spatial mapping hardware it probably doesn't make sense to have spatial mapping component enabled.</span></span>
1. <span data-ttu-id="b5547-299">Dopo l'avvio, dopo l'inizializzazione di MRTK, lo scambio del profilo per modificare la modalità di funzionamento di determinate funzionalità.</span><span class="sxs-lookup"><span data-stu-id="b5547-299">After startup, after the MRTK is initialized, swapping the profile to change the way certain features behave.</span></span> <span data-ttu-id="b5547-300">È ad esempio possibile che nell'applicazione sia presente un'esperienza secondaria specifica che desidera che i puntatori a distanza siano completamente rimossi.</span><span class="sxs-lookup"><span data-stu-id="b5547-300">For example, there may be a specific sub-experience in the application that wants far hand pointers completely removed.</span></span> <span data-ttu-id="b5547-301">**Si noti** che questo tipo di scambio attualmente non funziona a causa di questo problema: [https://github.com/microsoft/MixedRealityToolkit-Unity/issues/4289](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/4289) .</span><span class="sxs-lookup"><span data-stu-id="b5547-301">**Note** that this type of swapping currently doesn't work due to this issue: [https://github.com/microsoft/MixedRealityToolkit-Unity/issues/4289](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/4289).</span></span>

## <a name="swapping-profiles-prior-to-mrtk-initialization"></a><span data-ttu-id="b5547-302">Scambio di profili prima dell'inizializzazione di MRTK</span><span class="sxs-lookup"><span data-stu-id="b5547-302">Swapping profiles prior to MRTK initialization</span></span>

<span data-ttu-id="b5547-303">Questa operazione può essere eseguita connettendo un monocomportamento (esempio riportato di seguito) che viene eseguito prima dell'inizializzazione di MRTK:</span><span class="sxs-lookup"><span data-stu-id="b5547-303">This can be accomplished by attaching a MonoBehaviour (example below) which runs before MRTK initialization:</span></span>

```csharp
using Microsoft.MixedReality.Toolkit;
using UnityEditor;
using UnityEngine;

/// <summary>
/// Sample MonoBehaviour that will run before the MixedRealityToolkit object, and change
/// the profile, so that when the MRTK initializes it uses the profile specified below
/// rather than the one that is saved in its scene.
/// </summary>
/// <remarks>
/// Note that this script must have a higher priority in the script execution order compared
/// to that of MixedRealityToolkit.cs. See https://docs.unity3d.com/Manual/class-MonoManager.html
/// for more information on script execution order.
/// </remarks>
public class ProfileSwapper : MonoBehaviour
{
    void Start()
    {
        // Here you could choose any arbitrary MixedRealityToolkitConfigurationProfile (for example, you could
        // add some platform checking code here to determine which profile to load).
        var profile = AssetDatabase.LoadAssetAtPath<MixedRealityToolkitConfigurationProfile>("Assets/MixedRealityToolkit.Generated/CustomProfiles/RuntimeSwapparoo.asset");
        MixedRealityToolkit.Instance.ActiveProfile = profile;
    }
}
```

<span data-ttu-id="b5547-304">Anziché "RuntimeSwapparoo. asset", è possibile avere un set arbitrario di profili che si applicano a piattaforme specifiche, ad esempio una per HoloLens 1, una per VR, una per HoloLens 2 e così via.</span><span class="sxs-lookup"><span data-stu-id="b5547-304">Instead of "RuntimeSwapparoo.asset", it's possible to have some arbitrary set of profiles which apply to specific platforms (for example, one for HoloLens 1, one for VR, one for HoloLens 2, etc).</span></span> <span data-ttu-id="b5547-305">È possibile usare diversi altri indicatori, ad esempio [https://docs.unity3d.com/ScriptReference/SystemInfo.html](https://docs.unity3d.com/ScriptReference/SystemInfo.html) o se la fotocamera è opaca o trasparente, per individuare il profilo da caricare.</span><span class="sxs-lookup"><span data-stu-id="b5547-305">It's possible to use various other indicators (i.e. [https://docs.unity3d.com/ScriptReference/SystemInfo.html](https://docs.unity3d.com/ScriptReference/SystemInfo.html), or whether or not the camera is opaque/transparent), to figure out which profile to load.</span></span>

## <a name="see-also"></a><span data-ttu-id="b5547-306">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="b5547-306">See also</span></span>

- [<span data-ttu-id="b5547-307">Stabilizzazione ologramma</span><span class="sxs-lookup"><span data-stu-id="b5547-307">Hologram Stabilization</span></span>](../Performance/hologram-stabilization.md)

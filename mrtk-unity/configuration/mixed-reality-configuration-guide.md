---
title: Guida alla configurazione della realtà mista
description: Documentazione per configurare MRTK in Unity.
author: RogPodge
ms.author: roliu
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: a8aca05b4a4bc154061d6f7594e5128ab91d5f0e
ms.sourcegitcommit: c08997a75acfe4ac1d044c0fb9112e6817eb3d45
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/24/2021
ms.locfileid: "112588858"
---
# <a name="mixed-reality-toolkit-profile-configuration-guide"></a><span data-ttu-id="461ba-104">Guida alla configurazione del profilo di Mixed Reality Toolkit</span><span class="sxs-lookup"><span data-stu-id="461ba-104">Mixed Reality Toolkit profile configuration guide</span></span>

<span data-ttu-id="461ba-105">Mixed Reality Toolkit centralizza la maggior parte della configurazione necessaria per gestire il toolkit il più possibile (ad eccezione dei veri "cose" di runtime).</span><span class="sxs-lookup"><span data-stu-id="461ba-105">The Mixed Reality Toolkit centralizes as much of the configuration required to manage the toolkit as possible (except for true runtime "things").</span></span>

<span data-ttu-id="461ba-106">Questa guida è una procedura dettagliata semplice per ognuna delle schermate del profilo di configurazione attualmente disponibili per il toolkit.</span><span class="sxs-lookup"><span data-stu-id="461ba-106">This guide is a simple walkthrough for each of the configuration profile screens currently available for the toolkit.</span></span>

## <a name="the-main-mixed-reality-toolkit-configuration-profile"></a><span data-ttu-id="461ba-107">Profilo di configurazione principale di Mixed Reality Toolkit</span><span class="sxs-lookup"><span data-stu-id="461ba-107">The main Mixed Reality Toolkit configuration profile</span></span>

<span data-ttu-id="461ba-108">Il profilo di configurazione principale, collegato al GameObject *MixedRealityToolkit* nella scena, fornisce il punto di ingresso principale per il Toolkit nel progetto.</span><span class="sxs-lookup"><span data-stu-id="461ba-108">The main configuration profile, which is attached to the *MixedRealityToolkit* GameObject in your Scene, provides the main entry point for the Toolkit in your project.</span></span>

> [!NOTE]
> <span data-ttu-id="461ba-109">Mixed Reality Toolkit "blocca" le schermate di configurazione predefinite per assicurarsi di avere sempre un punto di partenza comune per il progetto ed è consigliato iniziare a definire impostazioni personalizzate con l'evolversi del progetto.</span><span class="sxs-lookup"><span data-stu-id="461ba-109">The Mixed Reality Toolkit "locks" the default configuration screens to ensure you always have a common start point for your project and it is encouraged to start defining your own settings as your project evolves.</span></span> <span data-ttu-id="461ba-110">La configurazione di MRTK non è modificabile durante la modalità di riproduzione.</span><span class="sxs-lookup"><span data-stu-id="461ba-110">The MRTK configuration is not editable during play-mode.</span></span>

![Profilo di configurazione di MRTK](../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_ActiveConfiguration.png)

<span data-ttu-id="461ba-112">Tutti i profili "predefiniti" per Mixed Reality Toolkit sono disponibili nel progetto SDK nella cartella Assets/MRTK/SDK/Profiles.</span><span class="sxs-lookup"><span data-stu-id="461ba-112">All the "default" profiles for the Mixed Reality Toolkit can be found in the SDK project in the folder Assets/MRTK/SDK/Profiles.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="461ba-113">DefaultHoloLens2ConfigurationProfile è ottimizzato per HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="461ba-113">DefaultHoloLens2ConfigurationProfile is optimized for HoloLens 2.</span></span> <span data-ttu-id="461ba-114">Per [informazioni dettagliate,](../features/profiles/profiles.md) vedere Profili.</span><span class="sxs-lookup"><span data-stu-id="461ba-114">See [Profiles](../features/profiles/profiles.md) for the details.</span></span>

<span data-ttu-id="461ba-115">Quando apri il profilo di configurazione principale di Mixed Reality Toolkit, nella finestra di controllo verrà visualizzata la schermata seguente:</span><span class="sxs-lookup"><span data-stu-id="461ba-115">When you open the main Mixed Reality Toolkit Configuration Profile, you will see the following screen in the inspector:</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_MixedRealityToolkitConfigurationScreen.png" width="650px" alt="MRTK configuration scene" style="display:block;">

<span data-ttu-id="461ba-116">Se si seleziona un asset MixedRealityToolkitConfigurationProfile senza MixedRealityToolkit nella scena, verrà chiesto se si vuole che MRTK configura automaticamente la scena.</span><span class="sxs-lookup"><span data-stu-id="461ba-116">If you select a MixedRealityToolkitConfigurationProfile asset without the MixedRealityToolkit in the scene, it will ask you if you want the MRTK to automatically setup the scene for you.</span></span> <span data-ttu-id="461ba-117">Questo è facoltativo, tuttavia, deve essere presente un oggetto MixedRealityToolkit attivo nella scena per accedere a tutte le schermate di configurazione.</span><span class="sxs-lookup"><span data-stu-id="461ba-117">This is optional, however, there must be an active MixedRealityToolkit object in the scene to access all the configuration screens.</span></span>

<span data-ttu-id="461ba-118">In questo modo viene ospitata la configurazione di runtime attiva corrente per il progetto.</span><span class="sxs-lookup"><span data-stu-id="461ba-118">This houses the current active runtime configuration for the project.</span></span>

<span data-ttu-id="461ba-119">Da qui è possibile passare a tutti i profili di configurazione per MRTK, tra cui:</span><span class="sxs-lookup"><span data-stu-id="461ba-119">From here you can navigate to all the configuration profiles for the MRTK, including:</span></span>

- [<span data-ttu-id="461ba-120">Guida alla configurazione del profilo di Mixed Reality Toolkit</span><span class="sxs-lookup"><span data-stu-id="461ba-120">Mixed Reality Toolkit profile configuration guide</span></span>](#mixed-reality-toolkit-profile-configuration-guide)
  - [<span data-ttu-id="461ba-121">Profilo di configurazione principale di Mixed Reality Toolkit</span><span class="sxs-lookup"><span data-stu-id="461ba-121">The main Mixed Reality Toolkit configuration profile</span></span>](#the-main-mixed-reality-toolkit-configuration-profile)
  - [<span data-ttu-id="461ba-122">Impostazioni dell'esperienza</span><span class="sxs-lookup"><span data-stu-id="461ba-122">Experience settings</span></span>](#experience-settings)
  - [<span data-ttu-id="461ba-123">Impostazioni della fotocamera</span><span class="sxs-lookup"><span data-stu-id="461ba-123">Camera settings</span></span>](#camera-settings)
  - [<span data-ttu-id="461ba-124">Impostazioni di sistema di input</span><span class="sxs-lookup"><span data-stu-id="461ba-124">Input system settings</span></span>](#input-system-settings)
  - [<span data-ttu-id="461ba-125">Impostazioni di visualizzazione dei limiti</span><span class="sxs-lookup"><span data-stu-id="461ba-125">Boundary visualization settings</span></span>](#boundary-visualization-settings)
  - [<span data-ttu-id="461ba-126">Selezione del sistema di teletrasporto</span><span class="sxs-lookup"><span data-stu-id="461ba-126">Teleportation system selection</span></span>](#teleportation-system-selection)
  - [<span data-ttu-id="461ba-127">Impostazioni di consapevolezza spaziale</span><span class="sxs-lookup"><span data-stu-id="461ba-127">Spatial awareness settings</span></span>](#spatial-awareness-settings)
  - [<span data-ttu-id="461ba-128">Impostazioni di diagnostica</span><span class="sxs-lookup"><span data-stu-id="461ba-128">Diagnostics settings</span></span>](#diagnostics-settings)
  - [<span data-ttu-id="461ba-129">Impostazioni di sistema della scena</span><span class="sxs-lookup"><span data-stu-id="461ba-129">Scene system settings</span></span>](#scene-system-settings)
  - [<span data-ttu-id="461ba-130">Impostazioni dei servizi aggiuntivi</span><span class="sxs-lookup"><span data-stu-id="461ba-130">Additional services settings</span></span>](#additional-services-settings)
  - [<span data-ttu-id="461ba-131">Impostazioni delle azioni di input</span><span class="sxs-lookup"><span data-stu-id="461ba-131">Input actions settings</span></span>](#input-actions-settings)
  - [<span data-ttu-id="461ba-132">Regole delle azioni di input</span><span class="sxs-lookup"><span data-stu-id="461ba-132">Input actions rules</span></span>](#input-actions-rules)
  - [<span data-ttu-id="461ba-133">Configurazione del puntatore</span><span class="sxs-lookup"><span data-stu-id="461ba-133">Pointer configuration</span></span>](#pointer-configuration)
  - [<span data-ttu-id="461ba-134">Configurazione dei movimenti</span><span class="sxs-lookup"><span data-stu-id="461ba-134">Gestures configuration</span></span>](#gestures-configuration)
  - [<span data-ttu-id="461ba-135">Comandi vocali</span><span class="sxs-lookup"><span data-stu-id="461ba-135">Speech commands</span></span>](#speech-commands)
  - [<span data-ttu-id="461ba-136">Configurazione del mapping del controller</span><span class="sxs-lookup"><span data-stu-id="461ba-136">Controller mapping configuration</span></span>](#controller-mapping-configuration)
  - [<span data-ttu-id="461ba-137">Impostazioni di visualizzazione del controller</span><span class="sxs-lookup"><span data-stu-id="461ba-137">Controller visualization settings</span></span>](#controller-visualization-settings)
  - [<span data-ttu-id="461ba-138">Utilità dell'editor</span><span class="sxs-lookup"><span data-stu-id="461ba-138">Editor utilities</span></span>](#editor-utilities)
    - [<span data-ttu-id="461ba-139">Controlli dei servizi</span><span class="sxs-lookup"><span data-stu-id="461ba-139">Service inspectors</span></span>](#service-inspectors)
    - [<span data-ttu-id="461ba-140">Renderer del buffer di profondità</span><span class="sxs-lookup"><span data-stu-id="461ba-140">Depth buffer renderer</span></span>](#depth-buffer-renderer)
  - [<span data-ttu-id="461ba-141">Modifica dei profili in fase di esecuzione</span><span class="sxs-lookup"><span data-stu-id="461ba-141">Changing profiles at runtime</span></span>](#changing-profiles-at-runtime)
    - [<span data-ttu-id="461ba-142">Opzione del profilo di inizializzazione di MRTK precedente</span><span class="sxs-lookup"><span data-stu-id="461ba-142">Pre MRTK initialization profile switch</span></span>](#pre-mrtk-initialization-profile-switch)
    - [<span data-ttu-id="461ba-143">Opzione del profilo attivo</span><span class="sxs-lookup"><span data-stu-id="461ba-143">Active profile switch</span></span>](#active-profile-switch)
  - [<span data-ttu-id="461ba-144">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="461ba-144">See also</span></span>](#see-also)

<span data-ttu-id="461ba-145">Questi profili di configurazione sono riportati di seguito nelle sezioni pertinenti:</span><span class="sxs-lookup"><span data-stu-id="461ba-145">These configuration profiles are detailed below in their relevant sections:</span></span>

---
<a name="experience"></a>

## <a name="experience-settings"></a><span data-ttu-id="461ba-146">Impostazioni dell'esperienza</span><span class="sxs-lookup"><span data-stu-id="461ba-146">Experience settings</span></span>

<span data-ttu-id="461ba-147">Disponibile nella pagina principale di configurazione di Mixed Reality Toolkit, questa impostazione definisce il funzionamento predefinito della scalabilità dell'ambiente di [realtà mista](/windows/mixed-reality/coordinate-systems-in-unity) per il progetto.</span><span class="sxs-lookup"><span data-stu-id="461ba-147">Located on the main Mixed Reality Toolkit configuration page, this setting defines the default operation of the [Mixed Reality environment scale](/windows/mixed-reality/coordinate-systems-in-unity) for your project.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_ExperienceSettings.png" width="650px" alt="Experiance settings" style="display:block;">

---
<a name="camera"></a>

## <a name="camera-settings"></a><span data-ttu-id="461ba-148">Impostazioni della fotocamera</span><span class="sxs-lookup"><span data-stu-id="461ba-148">Camera settings</span></span>

<span data-ttu-id="461ba-149">Le impostazioni della fotocamera definiscono come verrà impostata la fotocamera per il progetto di realtà mista, definendo le impostazioni generiche di ritaglio, qualità e trasparenza.</span><span class="sxs-lookup"><span data-stu-id="461ba-149">The camera settings define how the camera will be setup for your Mixed Reality project, defining the generic clipping, quality and transparency settings.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_CameraProfile.png" width="650px" alt="Camera Profile" style="display:block;">

---
<a name="inputsystem"></a>

## <a name="input-system-settings"></a><span data-ttu-id="461ba-150">Impostazioni di sistema di input</span><span class="sxs-lookup"><span data-stu-id="461ba-150">Input system settings</span></span>

<span data-ttu-id="461ba-151">Il progetto di realtà mista offre un sistema di input affidabile e ben formato per il routing di tutti gli eventi di input intorno al progetto selezionato per impostazione predefinita.</span><span class="sxs-lookup"><span data-stu-id="461ba-151">The Mixed Reality Project provides a robust and well-trained input system for routing all the input events around the project which is selected by default.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_InputSystemSelection.png" width="650px" alt="Input System settings 1" style="display:block;">

<span data-ttu-id="461ba-152">Dietro il sistema di input fornito da MRTK ci sono diversi altri sistemi, che consentono di gestire le complesse inter-tessere necessarie per astrarre le complessità di un framework multipiattaforma/realtà mista.</span><span class="sxs-lookup"><span data-stu-id="461ba-152">Behind the Input System provided by the MRTK are several other systems, these help to drive and manage the complex inter-weavings required to abstract out the complexities of a multi-platform / mixed reality framework.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_InputSystemProfile.png" width="650px" alt="Input System settings 2" style="display:block;">

<span data-ttu-id="461ba-153">Ognuno dei singoli profili è descritto in dettaglio di seguito:</span><span class="sxs-lookup"><span data-stu-id="461ba-153">Each of the individual profiles are detailed below:</span></span>

- <span data-ttu-id="461ba-154">Impostazioni dello stato attivo</span><span class="sxs-lookup"><span data-stu-id="461ba-154">Focus Settings</span></span>
- [<span data-ttu-id="461ba-155">Impostazioni delle azioni di input</span><span class="sxs-lookup"><span data-stu-id="461ba-155">Input actions settings</span></span>](#input-actions-settings)
- [<span data-ttu-id="461ba-156">Regole delle azioni di input</span><span class="sxs-lookup"><span data-stu-id="461ba-156">Input actions rules</span></span>](#input-actions-rules)
- [<span data-ttu-id="461ba-157">Configurazione del puntatore</span><span class="sxs-lookup"><span data-stu-id="461ba-157">Pointer configuration</span></span>](#pointer-configuration)
- [<span data-ttu-id="461ba-158">Configurazione dei movimenti</span><span class="sxs-lookup"><span data-stu-id="461ba-158">Gestures configuration</span></span>](#gestures-configuration)
- [<span data-ttu-id="461ba-159">Comandi vocali</span><span class="sxs-lookup"><span data-stu-id="461ba-159">Speech commands</span></span>](#speech-commands)
- [<span data-ttu-id="461ba-160">Configurazione del mapping del controller</span><span class="sxs-lookup"><span data-stu-id="461ba-160">Controller mapping configuration</span></span>](#controller-mapping-configuration)
- [<span data-ttu-id="461ba-161">Impostazioni di visualizzazione del controller</span><span class="sxs-lookup"><span data-stu-id="461ba-161">Controller visualization settings</span></span>](#controller-visualization-settings)

---
<a name="boundary"></a>

## <a name="boundary-visualization-settings"></a><span data-ttu-id="461ba-162">Impostazioni di visualizzazione dei limiti</span><span class="sxs-lookup"><span data-stu-id="461ba-162">Boundary visualization settings</span></span>

<span data-ttu-id="461ba-163">Il sistema di limiti trasla il limite percepito segnalato dal sistema limite/guardiano delle piattaforme sottostanti.</span><span class="sxs-lookup"><span data-stu-id="461ba-163">The boundary system translates the perceived boundary reported by the underlying platforms boundary / guardian system.</span></span> <span data-ttu-id="461ba-164">La configurazione del visualizzatore di limiti consente di visualizzare automaticamente il limite registrato all'interno della scena rispetto alla posizione dell'utente. Il limite reagirà o si aggiornerà anche in base al punto in cui l'utente si teletrasporta all'interno della scena.</span><span class="sxs-lookup"><span data-stu-id="461ba-164">The Boundary visualizer configuration gives you the ability to automatically show the recorded boundary within your scene relative to the user's position.The boundary will also react / update based on where the user teleports within the scene.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_BoundaryVisualizationProfile.png" width="650px" alt="Boundry Visualization Settings" style="display:block;">

---
<a name="teleportation"></a>

## <a name="teleportation-system-selection"></a><span data-ttu-id="461ba-165">Selezione del sistema di teletrasporto</span><span class="sxs-lookup"><span data-stu-id="461ba-165">Teleportation system selection</span></span>

<span data-ttu-id="461ba-166">Il progetto di realtà mista offre un sistema di teletrasporto completo per la gestione degli eventi di teletrasporto nel progetto, selezionato per impostazione predefinita.</span><span class="sxs-lookup"><span data-stu-id="461ba-166">The Mixed Reality Project provides a full featured Teleportation system for managing teleportation events in the project which is selected by default.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_TeleportationSystemSelection.png" width="650px" alt="Teleport System settings" style="display:block;">

---
<a name="spatialawareness"></a>

## <a name="spatial-awareness-settings"></a><span data-ttu-id="461ba-167">Impostazioni di consapevolezza spaziale</span><span class="sxs-lookup"><span data-stu-id="461ba-167">Spatial awareness settings</span></span>

<span data-ttu-id="461ba-168">Il progetto di realtà mista fornisce un sistema di consapevolezza spaziale ricompilato per l'uso di sistemi di analisi spaziale nel progetto, che è selezionato per impostazione predefinita.</span><span class="sxs-lookup"><span data-stu-id="461ba-168">The Mixed Reality Project provides a rebuilt spatial awareness system for working with spatial scanning systems in the project which is selected by default.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_SpatialAwarenessSystemSelection.png" width="650px" alt="Spatial Awareness settings 1" style="display:block;">

<span data-ttu-id="461ba-169">La configurazione della consapevolezza spaziale di Mixed Reality Toolkit consente di personalizzare la modalità di avvio del sistema, indipendentemente dal fatto che sia automaticamente all'avvio dell'applicazione o in un secondo momento a livello di codice, nonché di impostare gli extent per il campo di visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="461ba-169">The Mixed Reality Toolkit spatial awareness configuration lets you tailor how the system starts, whether it is automatically when the application starts or later programmatically as well as setting the extents for the field of view.</span></span>

<span data-ttu-id="461ba-170">Consente anche di configurare le impostazioni della mesh e della superficie, personalizzando ulteriormente il modo in cui il progetto comprende l'ambiente intorno all'utente.</span><span class="sxs-lookup"><span data-stu-id="461ba-170">It also lets you configure the mesh and surface settings, further customizing how your project understands the environment around you.</span></span>

<span data-ttu-id="461ba-171">Questo è applicabile solo per i dispositivi che possono fornire un ambiente analizzato.</span><span class="sxs-lookup"><span data-stu-id="461ba-171">This is only applicable for devices that can provide a scanned environment.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_SpatialAwarenessProfile.png" width="650px" alt="Spatial Awareness settings 2" style="display:block;">

---
<a name="diagnostic"></a>

## <a name="diagnostics-settings"></a><span data-ttu-id="461ba-172">Impostazioni di diagnostica</span><span class="sxs-lookup"><span data-stu-id="461ba-172">Diagnostics settings</span></span>

<span data-ttu-id="461ba-173">Una funzionalità facoltativa ma estremamente utile di MRTK è la funzionalità di diagnostica del plug-in.</span><span class="sxs-lookup"><span data-stu-id="461ba-173">An optional but highly useful feature of the MRTK is the plugin diagnostics functionality.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_DiagnosticsSystemSelection.png" width="650px" alt="Diagnostics settings" style="display:block;">

<span data-ttu-id="461ba-174">Il profilo di diagnostica offre diversi sistemi semplici da monitorare durante l'esecuzione del progetto, tra cui un pratico interruttore On/Off per abilitare/disabilitare il pannello di visualizzazione nella scena.</span><span class="sxs-lookup"><span data-stu-id="461ba-174">The diagnostics profile provides several simple systems to monitor whilst the project is running, including a handy On/Off switch to enable / disable the display panel in the scene.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_DiagnosticsProfile.png" width="650px" alt="Diagnostics settings System settings 2" style="display:block;">

---
<a name="scenesystem"></a>

## <a name="scene-system-settings"></a><span data-ttu-id="461ba-175">Impostazioni di sistema della scena</span><span class="sxs-lookup"><span data-stu-id="461ba-175">Scene system settings</span></span>

<span data-ttu-id="461ba-176">MRTK fornisce questo servizio facoltativo che consente di gestire il caricamento/scaricamento di scene additive complesse.</span><span class="sxs-lookup"><span data-stu-id="461ba-176">The MRTK provides this optional service to help you manage complex additive scene loading / unloading.</span></span> <span data-ttu-id="461ba-177">Per decidere se il sistema della scena è una scelta adatta al progetto, leggi la Guida al sistema [Attività iniziali scena.](../features/scene-system/scene-system-getting-started.md)</span><span class="sxs-lookup"><span data-stu-id="461ba-177">To decide if the Scene System would be a good fit for your project, read the [Scene System Getting Started Guide.](../features/scene-system/scene-system-getting-started.md)</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_SceneSystemProfile.png" width="650px" alt="Scene System settings 1" style="display:block;">

---
<a name="services"></a>

## <a name="additional-services-settings"></a><span data-ttu-id="461ba-178">Impostazioni dei servizi aggiuntivi</span><span class="sxs-lookup"><span data-stu-id="461ba-178">Additional services settings</span></span>

<span data-ttu-id="461ba-179">Una delle aree più avanzate di Mixed [](https://en.wikipedia.org/wiki/Service_locator_pattern) Reality Toolkit è l'implementazione del modello di localizzatore di servizi che consente la registrazione di qualsiasi "servizio" con il framework.</span><span class="sxs-lookup"><span data-stu-id="461ba-179">One of the more advanced areas of the Mixed Reality Toolkit is its [service locator pattern](https://en.wikipedia.org/wiki/Service_locator_pattern) implementation which allows the registering of any "Service" with the framework.</span></span> <span data-ttu-id="461ba-180">In questo modo il framework può essere esteso con facilità con nuove funzionalità/sistemi, ma consente anche ai progetti di sfruttare queste funzionalità per registrare i propri componenti di runtime.</span><span class="sxs-lookup"><span data-stu-id="461ba-180">This allows the framework to be both extended with new features / systems easily but also allows for projects to take advantage of these capabilities to register their own runtime components.</span></span>

<span data-ttu-id="461ba-181">Qualsiasi servizio registrato ottiene comunque il vantaggio completo di tutti gli eventi unity, senza il sovraccarico e il costo dell'implementazione di modelli singleton MonoBehaviour o clunky.</span><span class="sxs-lookup"><span data-stu-id="461ba-181">Any registered service still gets the full advantage of all of the Unity events, without the overhead and cost of implementing a MonoBehaviour or clunky singleton patterns.</span></span> <span data-ttu-id="461ba-182">Ciò consente componenti C# puri senza overhead della scena per l'esecuzione di processi in primo piano e in background, ad esempio sistemi di generazione, logica di gioco di runtime o praticamente qualsiasi altro elemento.</span><span class="sxs-lookup"><span data-stu-id="461ba-182">This allows for pure C# components with no scene overhead for running both foreground and background processes, e.g. spawning systems, runtime game logic, or practically anything else.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_RegisteredServiceProvidersProfile.png" width="650px" alt="additional System settings" style="display:block;">

---
<a name="inputactions"></a>

## <a name="input-actions-settings"></a><span data-ttu-id="461ba-183">Impostazioni delle azioni di input</span><span class="sxs-lookup"><span data-stu-id="461ba-183">Input actions settings</span></span>

<span data-ttu-id="461ba-184">Le azioni di input consentono di astrarre eventuali interazioni fisiche e input da un progetto di runtime.</span><span class="sxs-lookup"><span data-stu-id="461ba-184">Input actions provide a way to abstract any physical interactions and input from a runtime project.</span></span> <span data-ttu-id="461ba-185">Tutto l'input fisico (da controller/mani/mouse/e così via) viene convertito in un'azione di input logica da usare nel progetto di runtime.</span><span class="sxs-lookup"><span data-stu-id="461ba-185">All physical input (from controllers / hands / mouse / etc) is translated in to a logical input action for use in your runtime project.</span></span> <span data-ttu-id="461ba-186">In questo modo, indipendentemente dall'origine dell'input, il progetto implementa semplicemente queste azioni come "Cose da fare" o "Interagisci" nelle scene.</span><span class="sxs-lookup"><span data-stu-id="461ba-186">This ensures no matter where the input comes from, your project simply implements these actions as "Things to do" or "Interact with" in your scenes.</span></span>

<span data-ttu-id="461ba-187">Per creare una nuova azione di input, è sufficiente fare clic sul pulsante "Aggiungi una nuova azione" e immettere un nome di testo descrittivo per ciò che rappresenta.</span><span class="sxs-lookup"><span data-stu-id="461ba-187">To create a new input action, simply click the "Add a new Action" button and enter a friendly text name for what it represents.</span></span> <span data-ttu-id="461ba-188">È quindi necessario selezionare solo un asse (il tipo di dati) a cui l'azione deve comunicare o, nel caso dei controller fisici, il tipo di input fisico a cui può essere collegata, ad esempio:</span><span class="sxs-lookup"><span data-stu-id="461ba-188">You then only need select an axis (the type of data) the action is meant to convey, or in the case of physical controllers, the physical input type it can be attached to, for example:</span></span>

| <span data-ttu-id="461ba-189">Vincolo dell'asse</span><span class="sxs-lookup"><span data-stu-id="461ba-189">Axis Constraint</span></span> | <span data-ttu-id="461ba-190">Tipo di dati</span><span class="sxs-lookup"><span data-stu-id="461ba-190">Data Type</span></span> | <span data-ttu-id="461ba-191">Descrizione</span><span class="sxs-lookup"><span data-stu-id="461ba-191">Description</span></span> | <span data-ttu-id="461ba-192">Esempio d'uso</span><span class="sxs-lookup"><span data-stu-id="461ba-192">Example use</span></span> |
| :--- | :--- | :--- | :--- |
| <span data-ttu-id="461ba-193">Nessuno</span><span class="sxs-lookup"><span data-stu-id="461ba-193">None</span></span> | <span data-ttu-id="461ba-194">Nessun dato</span><span class="sxs-lookup"><span data-stu-id="461ba-194">No data</span></span> | <span data-ttu-id="461ba-195">Usato per un'azione o un evento vuoto</span><span class="sxs-lookup"><span data-stu-id="461ba-195">Used for an empty action or event</span></span> | <span data-ttu-id="461ba-196">Trigger di evento</span><span class="sxs-lookup"><span data-stu-id="461ba-196">Event Trigger</span></span> |
| <span data-ttu-id="461ba-197">Non elaborato (riservato)</span><span class="sxs-lookup"><span data-stu-id="461ba-197">Raw (reserved)</span></span> | <span data-ttu-id="461ba-198">object</span><span class="sxs-lookup"><span data-stu-id="461ba-198">object</span></span> | <span data-ttu-id="461ba-199">Riservate per utilizzo futuro</span><span class="sxs-lookup"><span data-stu-id="461ba-199">Reserved for future use</span></span> | <span data-ttu-id="461ba-200">N/D</span><span class="sxs-lookup"><span data-stu-id="461ba-200">N/A</span></span> |
| <span data-ttu-id="461ba-201">Digitale</span><span class="sxs-lookup"><span data-stu-id="461ba-201">Digital</span></span> | <span data-ttu-id="461ba-202">bool</span><span class="sxs-lookup"><span data-stu-id="461ba-202">bool</span></span> | <span data-ttu-id="461ba-203">Dati booleani di tipo on o off</span><span class="sxs-lookup"><span data-stu-id="461ba-203">A boolean on or off type data</span></span> | <span data-ttu-id="461ba-204">Pulsante controller</span><span class="sxs-lookup"><span data-stu-id="461ba-204">A controller button</span></span> |
| <span data-ttu-id="461ba-205">Asse singolo</span><span class="sxs-lookup"><span data-stu-id="461ba-205">Single Axis</span></span> | <span data-ttu-id="461ba-206">float</span><span class="sxs-lookup"><span data-stu-id="461ba-206">float</span></span> | <span data-ttu-id="461ba-207">Un singolo valore di dati di precisione</span><span class="sxs-lookup"><span data-stu-id="461ba-207">A single precision data value</span></span> | <span data-ttu-id="461ba-208">Input con intervallo, ad esempio un trigger</span><span class="sxs-lookup"><span data-stu-id="461ba-208">A ranged input, e.g. a trigger</span></span> |
| <span data-ttu-id="461ba-209">Doppio asse</span><span class="sxs-lookup"><span data-stu-id="461ba-209">Dual Axis</span></span> | <span data-ttu-id="461ba-210">Vector2</span><span class="sxs-lookup"><span data-stu-id="461ba-210">Vector2</span></span> | <span data-ttu-id="461ba-211">Data di tipo float doppio per più assi</span><span class="sxs-lookup"><span data-stu-id="461ba-211">A dual float type date for multiple axis</span></span> | <span data-ttu-id="461ba-212">Un Dpad o una levetta</span><span class="sxs-lookup"><span data-stu-id="461ba-212">A Dpad or Thumbstick</span></span> |
| <span data-ttu-id="461ba-213">Posizione di tre dof</span><span class="sxs-lookup"><span data-stu-id="461ba-213">Three Dof Position</span></span> | <span data-ttu-id="461ba-214">Vector3</span><span class="sxs-lookup"><span data-stu-id="461ba-214">Vector3</span></span> | <span data-ttu-id="461ba-215">Dati di tipo posizionale da con 3 assi float</span><span class="sxs-lookup"><span data-stu-id="461ba-215">Positional type data from with 3 float axis</span></span> | <span data-ttu-id="461ba-216">Controller solo stile di posizione 3D</span><span class="sxs-lookup"><span data-stu-id="461ba-216">3D position style only controller</span></span> |
| <span data-ttu-id="461ba-217">Rotazione di tre dof</span><span class="sxs-lookup"><span data-stu-id="461ba-217">Three Dof Rotation</span></span> | <span data-ttu-id="461ba-218">Quaternion</span><span class="sxs-lookup"><span data-stu-id="461ba-218">Quaternion</span></span> | <span data-ttu-id="461ba-219">Input solo rotazionale con 4 assi float</span><span class="sxs-lookup"><span data-stu-id="461ba-219">Rotational only input with 4 float axis</span></span> | <span data-ttu-id="461ba-220">Un controller di stile a tre gradi, ad esempio un controller Oculus Go</span><span class="sxs-lookup"><span data-stu-id="461ba-220">A Three degrees style controller, e.g. Oculus Go controller</span></span> |
| <span data-ttu-id="461ba-221">Sei Dof</span><span class="sxs-lookup"><span data-stu-id="461ba-221">Six Dof</span></span> | <span data-ttu-id="461ba-222">Pose di realtà mista (Vector3, Quaternion)</span><span class="sxs-lookup"><span data-stu-id="461ba-222">Mixed Reality Pose (Vector3, Quaternion)</span></span> | <span data-ttu-id="461ba-223">Input di posizione e stile di rotazione con componenti Vector3 e Quaternion</span><span class="sxs-lookup"><span data-stu-id="461ba-223">A position and rotation style input with both Vector3 and Quaternion components</span></span> | <span data-ttu-id="461ba-224">Un controller di movimento o un puntatore</span><span class="sxs-lookup"><span data-stu-id="461ba-224">A motion controller or Pointer</span></span> |

<span data-ttu-id="461ba-225">Gli eventi che utilizzano azioni di input non sono limitati ai controller fisici e possono comunque essere utilizzati all'interno del progetto per fare in modo che gli effetti di runtime generino nuove azioni.</span><span class="sxs-lookup"><span data-stu-id="461ba-225">Events utilizing input actions are not limited to physical controllers and can still be utilized within the project to have runtime effects generate new actions.</span></span>

> [!NOTE]
> <span data-ttu-id="461ba-226">Le azioni di input sono uno dei pochi componenti non modificabili in fase di esecuzione, ma sono solo una configurazione in fase di progettazione.</span><span class="sxs-lookup"><span data-stu-id="461ba-226">Input actions are one of the few components which is not editable at runtime, they are a design time configuration only.</span></span> <span data-ttu-id="461ba-227">Questo profilo non deve essere scambiato mentre il progetto è in esecuzione a causa della dipendenza del framework (e dei progetti) dall'ID generato per ogni azione.</span><span class="sxs-lookup"><span data-stu-id="461ba-227">This profile should not be swapped out whilst the project is running due to the framework (and your projects) dependency on the ID's generated for each action.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_InputActionsProfile.png" width="650px" alt="Configuration Profile" style="display:block;">

---
<a name="inputactionrules"></a>

## <a name="input-actions-rules"></a><span data-ttu-id="461ba-228">Regole delle azioni di input</span><span class="sxs-lookup"><span data-stu-id="461ba-228">Input actions rules</span></span>

<span data-ttu-id="461ba-229">Le regole di azione di input consentono di convertire automaticamente un evento generato per un'azione di input in azioni diverse in base al valore dei dati.</span><span class="sxs-lookup"><span data-stu-id="461ba-229">Input action rules provide a way to automatically translate an event raised for one input action in to different actions based on its data value.</span></span> <span data-ttu-id="461ba-230">Questi vengono gestiti senza problemi all'interno del framework e non comportano costi per le prestazioni.</span><span class="sxs-lookup"><span data-stu-id="461ba-230">These are managed seamlessly within the framework and do not incur any performance costs.</span></span>

<span data-ttu-id="461ba-231">Ad esempio, convertendo il singolo evento di input del doppio asse da un DPad in alle 4 azioni "Dpad Up" /"DPad Down" /"Dpad Left" /"Dpad Right" corrispondenti (come illustrato nell'immagine seguente).</span><span class="sxs-lookup"><span data-stu-id="461ba-231">For example, converting the single dual axis input event from a DPad in to the 4 corresponding "Dpad Up" / "DPad Down" / "Dpad Left" / "Dpad Right" actions (as shown in the image below).</span></span>

<span data-ttu-id="461ba-232">Questa operazione può essere eseguita anche nel codice.</span><span class="sxs-lookup"><span data-stu-id="461ba-232">This could also be done in your own code.</span></span> <span data-ttu-id="461ba-233">Tuttavia, poiché si tratta di un modello molto comune, il framework fornisce un meccanismo per eseguire questa operazione "predefinita"</span><span class="sxs-lookup"><span data-stu-id="461ba-233">However, seeing as this was a very common pattern, the framework provides a mechanism to do this "out of the box"</span></span>

<span data-ttu-id="461ba-234">Le regole dell'azione di input possono essere configurate per qualsiasi asse di input disponibile.</span><span class="sxs-lookup"><span data-stu-id="461ba-234">Input action Rules can be configured for any of the available input axis.</span></span> <span data-ttu-id="461ba-235">Tuttavia, le azioni di input da un tipo di asse possono essere convertite in un'altra azione di input dello stesso tipo di asse.</span><span class="sxs-lookup"><span data-stu-id="461ba-235">However, input actions from one axis type can be translated to another input action of the same axis type.</span></span> <span data-ttu-id="461ba-236">È possibile eseguire il mapping di un'azione del doppio asse a un'altra azione del doppio asse, ma non a un'azione digitale o nessuna.</span><span class="sxs-lookup"><span data-stu-id="461ba-236">You can map a dual axis action to another dual axis action, but not to a digital or none action.</span></span>

![Profilo delle regole di azione di input](../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_InputActionRulesProfile.png)

---
<a name="pointer"></a>

## <a name="pointer-configuration"></a><span data-ttu-id="461ba-238">Configurazione del puntatore</span><span class="sxs-lookup"><span data-stu-id="461ba-238">Pointer configuration</span></span>

<span data-ttu-id="461ba-239">I puntatori vengono usati per guidare l'interattività nella scena da qualsiasi dispositivo di input, fornendo sia una direzione che un hit test con qualsiasi oggetto in una scena (che ha un collisore collegato o è un componente dell'interfaccia utente).</span><span class="sxs-lookup"><span data-stu-id="461ba-239">Pointers are used to drive interactivity in the scene from any input device, giving both a direction and hit test with any object in a scene (that has a collider attached, or is a UI component).</span></span> <span data-ttu-id="461ba-240">Per impostazione predefinita, i puntatori vengono configurati automaticamente per controller, visori (sguardo fisso/messa a fuoco) e input tramite mouse/tocco.</span><span class="sxs-lookup"><span data-stu-id="461ba-240">Pointers are by default automatically configured for controllers, headsets (gaze / focus) and mouse / touch input.</span></span>

<span data-ttu-id="461ba-241">I puntatori possono anche essere visualizzati all'interno della scena attiva usando uno dei numerosi componenti di linea forniti da Mixed Reality Toolkit o uno dei propri se implementano l'interfaccia MRTK IMixedRealityPointer.</span><span class="sxs-lookup"><span data-stu-id="461ba-241">Pointers can also be visualized within the active scene using one of the many line components provided by the Mixed Reality Toolkit, or any of your own if they implement the MRTK IMixedRealityPointer interface.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_InputPointerProfile.png" width="650px" alt="Input Pointer Profile" style="display:block;">

- <span data-ttu-id="461ba-242">Extent di puntamento: determina l'extent di puntamento globale per tutti i puntatori, incluso lo sguardo fisso.</span><span class="sxs-lookup"><span data-stu-id="461ba-242">Pointing Extent: Determines the global pointing extent for all pointers, including gaze.</span></span>
- <span data-ttu-id="461ba-243">Maschere di livello Raycast di puntamento: determina i puntatori ai livelli su cui verranno raggiati.</span><span class="sxs-lookup"><span data-stu-id="461ba-243">Pointing Raycast Layer Masks: Determines which layers pointers will raycast against.</span></span>
- <span data-ttu-id="461ba-244">Debug dei raggi di puntamento di disegno: un helper di debug per la visualizzazione dei raggi usati per il raycasting.</span><span class="sxs-lookup"><span data-stu-id="461ba-244">Debug Draw Pointing Rays: A debug helper for visualizing the rays used for raycasting.</span></span>
- <span data-ttu-id="461ba-245">Debug dei colori dei raggi di disegno: set di colori da usare per la visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="461ba-245">Debug Draw Pointing Rays Colors: A set of colors to use for visualizing.</span></span>
- <span data-ttu-id="461ba-246">Prefab cursore sguardo fisso: consente di specificare facilmente un cursore di sguardo globale per qualsiasi scena.</span><span class="sxs-lookup"><span data-stu-id="461ba-246">Gaze cursor prefab: Makes it easy to specify a global gaze cursor for any scene.</span></span>

<span data-ttu-id="461ba-247">È presente un pulsante helper aggiuntivo per passare rapidamente al provider gaze per eseguire l'override di alcuni valori specifici per Gaze, se necessario.</span><span class="sxs-lookup"><span data-stu-id="461ba-247">There's an additional helper button to quickly jump to the Gaze Provider to override some specific values for Gaze if needed.</span></span>

---
<a name="gestures"></a>

## <a name="gestures-configuration"></a><span data-ttu-id="461ba-248">Configurazione dei movimenti</span><span class="sxs-lookup"><span data-stu-id="461ba-248">Gestures configuration</span></span>

<span data-ttu-id="461ba-249">I movimenti sono un'implementazione specifica del sistema che consente di assegnare azioni di input ai vari metodi di input "Gesture" forniti da vari SDK ,ad esempio HoloLens.</span><span class="sxs-lookup"><span data-stu-id="461ba-249">Gestures are a system specific implementation allowing you to assign input actions to the various "Gesture" input methods provided by various SDKs (e.g. HoloLens).</span></span>

> [!NOTE]
> <span data-ttu-id="461ba-250">L'implementazione corrente di Gestures è solo per HoloLens e verrà migliorata per altri sistemi in quanto verranno aggiunti al Toolkit in futuro (nessuna data).</span><span class="sxs-lookup"><span data-stu-id="461ba-250">The current Gestures implementation is for the HoloLens only and will be enhanced for other systems as they are added to the Toolkit in the future (no dates yet).</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_GesturesProfile.png" width="650px" alt="Gesture configuration" style="display:block;">

---
<a name="speech"></a>

## <a name="speech-commands"></a><span data-ttu-id="461ba-251">Comandi vocali</span><span class="sxs-lookup"><span data-stu-id="461ba-251">Speech commands</span></span>

<span data-ttu-id="461ba-252">Analogamente ai movimenti, alcune piattaforme di runtime offrono anche funzionalità intelligenti di Riconoscimento vocale con la possibilità di generare comandi che possono essere ricevuti da un progetto Unity.</span><span class="sxs-lookup"><span data-stu-id="461ba-252">Like gestures, some runtime platforms also provide intelligent "Speech to Text" functionality with the ability to generate commands that can be received by a Unity project.</span></span> <span data-ttu-id="461ba-253">Questo profilo di configurazione consente di configurare quanto segue:</span><span class="sxs-lookup"><span data-stu-id="461ba-253">This configuration profile allows you to configure the following:</span></span>

1. <span data-ttu-id="461ba-254">Impostazioni generali: "Comportamento di avvio" impostato su Avvio automatico o Avvio manuale determina se inizializzare KeywordRecognizer all'avvio del sistema di input o lasciare che il progetto decida quando inizializzare KeywordRecognizer.</span><span class="sxs-lookup"><span data-stu-id="461ba-254">General Settings - "Start Behavior" set to Auto Start or Manual Start determines whether to initialize KeywordRecognizer at input system startup or let the project decide when to initialize the KeywordRecognizer.</span></span> <span data-ttu-id="461ba-255">Il "livello di attendibilità del riconoscimento" viene usato per inizializzare [l'API KeywordRecognizer di](https://docs.unity3d.com/ScriptReference/Windows.Speech.KeywordRecognizer-ctor.html) Unity</span><span class="sxs-lookup"><span data-stu-id="461ba-255">"Recognition Confidence Level" is used to initialize Unity's [KeywordRecognizer API](https://docs.unity3d.com/ScriptReference/Windows.Speech.KeywordRecognizer-ctor.html)</span></span>
2. <span data-ttu-id="461ba-256">Comandi vocali: registra le "parole" e le converte in azioni di input che possono essere ricevute dal progetto.</span><span class="sxs-lookup"><span data-stu-id="461ba-256">Speech Commands - Registers "words" and translates them in to input actions that can be received by your project.</span></span> <span data-ttu-id="461ba-257">Possono anche essere collegati alle azioni della tastiera, se necessario.</span><span class="sxs-lookup"><span data-stu-id="461ba-257">They can also be attached to keyboard actions if required.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="461ba-258">Il sistema attualmente supporta il riconoscimento vocale solo quando viene eseguito su piattaforme Windows 10, ad esempio HoloLens e Windows 10 desktop e verrà migliorato per altri sistemi in quanto verranno aggiunti a MRTK in futuro (nessuna data).</span><span class="sxs-lookup"><span data-stu-id="461ba-258">The system currently only supports speech when running on Windows 10 platforms, e.g. HoloLens and Windows 10 desktop and will be enhanced for other systems as they are added to MRTK in the future (no dates yet).</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_SpeechCommandsProfile.png" width="650px" alt="Configuration Profile screens" style="display:block;">

---
<a name="mapping"></a>

## <a name="controller-mapping-configuration"></a><span data-ttu-id="461ba-259">Configurazione del mapping del controller</span><span class="sxs-lookup"><span data-stu-id="461ba-259">Controller mapping configuration</span></span>

<span data-ttu-id="461ba-260">Una delle schermate di configurazione principali per Mixed Reality Toolkit è la possibilità di configurare ed eseguire il mapping dei vari tipi di controller che possono essere utilizzati dal progetto.</span><span class="sxs-lookup"><span data-stu-id="461ba-260">One of the core configuration screens for the Mixed Reality Toolkit is the ability to configure and map the various types of controllers that can be utilized by your project.</span></span>

<span data-ttu-id="461ba-261">La schermata di configurazione seguente consente di configurare uno dei controller attualmente riconosciuti dal toolkit.</span><span class="sxs-lookup"><span data-stu-id="461ba-261">The configuration screen below allows you to configure any of the controllers currently recognized by the toolkit.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_ControllerMappingProfile.png" width="650px" alt="Controller Mapping" style="display:block;">

<span data-ttu-id="461ba-262">MrTK fornisce una configurazione predefinita per i controller/sistemi seguenti:</span><span class="sxs-lookup"><span data-stu-id="461ba-262">The MRTK provides a default configuration for the following controllers / systems:</span></span>

- <span data-ttu-id="461ba-263">Mouse (incluso il supporto del mouse spaziale 3D)</span><span class="sxs-lookup"><span data-stu-id="461ba-263">Mouse (including 3D spatial mouse support)</span></span>
- <span data-ttu-id="461ba-264">Touch screen</span><span class="sxs-lookup"><span data-stu-id="461ba-264">Touch Screen</span></span>
- <span data-ttu-id="461ba-265">Controller Xbox</span><span class="sxs-lookup"><span data-stu-id="461ba-265">Xbox controllers</span></span>
- <span data-ttu-id="461ba-266">Windows Mixed Reality controller</span><span class="sxs-lookup"><span data-stu-id="461ba-266">Windows Mixed Reality controllers</span></span>
- <span data-ttu-id="461ba-267">Movimenti di HoloLens</span><span class="sxs-lookup"><span data-stu-id="461ba-267">HoloLens Gestures</span></span>
- <span data-ttu-id="461ba-268">CONTROLLER WAND DI VIVE IN STATO DI INSODATI</span><span class="sxs-lookup"><span data-stu-id="461ba-268">HTC Vive wand controllers</span></span>
- <span data-ttu-id="461ba-269">Controller Oculus Touch</span><span class="sxs-lookup"><span data-stu-id="461ba-269">Oculus Touch controllers</span></span>
- <span data-ttu-id="461ba-270">Controller remoto Oculus</span><span class="sxs-lookup"><span data-stu-id="461ba-270">Oculus Remote controller</span></span>
- <span data-ttu-id="461ba-271">Dispositivi OpenVR generici (solo utenti esperti)</span><span class="sxs-lookup"><span data-stu-id="461ba-271">Generic OpenVR devices (advanced users only)</span></span>

<span data-ttu-id="461ba-272">Facendo clic sull'immagine per uno dei sistemi controller predefiniti è possibile configurare una singola azione di input per tutti gli input corrispondenti, ad esempio, vedere la schermata di configurazione del controller Oculus Touch riportata di seguito:</span><span class="sxs-lookup"><span data-stu-id="461ba-272">Clicking on the Image for any of the pre-built controller systems allows you to configure a single input action for all its corresponding inputs, for example, see the Oculus Touch controller configuration screen below:</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_WindowsMixedRealityControllerConfigScreen.png" width="650px" alt="Controller config screen" style="display:block;">

<span data-ttu-id="461ba-273">È disponibile anche una schermata avanzata per la configurazione di altri controller di input OpenVR o Unity non identificati in precedenza.</span><span class="sxs-lookup"><span data-stu-id="461ba-273">There is also an advanced screen for configuring other OpenVR or Unity input controllers that are not identified above.</span></span>

---
<a name="visualization"></a>

## <a name="controller-visualization-settings"></a><span data-ttu-id="461ba-274">Impostazioni di visualizzazione del controller</span><span class="sxs-lookup"><span data-stu-id="461ba-274">Controller visualization settings</span></span>

<span data-ttu-id="461ba-275">Oltre al mapping del controller, viene fornito un profilo di configurazione separato per personalizzare il modo in cui i controller vengono presentati all'interno delle scene.</span><span class="sxs-lookup"><span data-stu-id="461ba-275">In addition to the controller mapping, a separate configuration profile is provided to customize how your controllers are presented within your scenes.</span></span>

<span data-ttu-id="461ba-276">Questo può essere configurato in un "Globale" (tutte le istanze di un controller per una mano specifica) o specifico per un singolo tipo di controller/ mano.</span><span class="sxs-lookup"><span data-stu-id="461ba-276">This can be configured at a "Global" (all instances of a controller for a specific hand) or specific to an individual controller type / hand.</span></span>

<span data-ttu-id="461ba-277">MrTK supporta anche modelli di controller SDK nativi per Windows Mixed Reality e OpenVR.</span><span class="sxs-lookup"><span data-stu-id="461ba-277">The MRTK also supports native SDK controller models for Windows Mixed Reality and OpenVR.</span></span> <span data-ttu-id="461ba-278">Vengono caricati come GameObject nella scena e posizionati usando il monitoraggio del controller della piattaforma.</span><span class="sxs-lookup"><span data-stu-id="461ba-278">These are loaded as GameObjects in your scene and positioned using the platform's controller tracking.</span></span>

<span data-ttu-id="461ba-279">Se la rappresentazione del controller nella scena deve essere compensata dalla posizione del controller fisico, è sufficiente impostare tale offset rispetto al prefab del modello controller (ad esempio, impostando la posizione di trasformazione del prefab controller con una posizione di offset).</span><span class="sxs-lookup"><span data-stu-id="461ba-279">If your controller representation in the scene needs to be offset from the physical controller position, then simply set that offset against the controller model's prefab (e.g. setting the transform position of the controller prefab with an offset position).</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_ControllerVisualizationProfile.png" width="650px" alt="Visualization profile" style="display:block;">

<a name="editor-utilities"></a>

## <a name="editor-utilities"></a><span data-ttu-id="461ba-280">Utilità dell'editor</span><span class="sxs-lookup"><span data-stu-id="461ba-280">Editor utilities</span></span>

<span data-ttu-id="461ba-281">Le utilità seguenti funzionano solo nell'editor e sono utili per migliorare la produttività dello sviluppo.</span><span class="sxs-lookup"><span data-stu-id="461ba-281">The following utilities work only in the editor and are useful to improve development productivity.</span></span>

![Utilità di configurazione dell'editor MRTK](../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_EditorConfiguration.png)

### <a name="service-inspectors"></a><span data-ttu-id="461ba-283">Controlli dei servizi</span><span class="sxs-lookup"><span data-stu-id="461ba-283">Service inspectors</span></span>

<span data-ttu-id="461ba-284">I controlli dei servizi sono una funzionalità solo editor che genera oggetti nella scena che rappresentano i servizi attivi.</span><span class="sxs-lookup"><span data-stu-id="461ba-284">Service Inspectors are an editor-only feature that generates in-scene objects representing active services.</span></span> <span data-ttu-id="461ba-285">Selezionando questi oggetti vengono visualizzati i controlli che offrono collegamenti alla documentazione, controllano le visualizzazioni dell'editor e informazioni dettagliate sullo stato del servizio.</span><span class="sxs-lookup"><span data-stu-id="461ba-285">Selecting these objects displays inspectors which offer documentation links, control over editor visualizations and insight into the state of the service.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_ServiceInspectors.PNG" width="350px" alt="Service Inspectors" style="display:block;">

<span data-ttu-id="461ba-286">È possibile abilitare i controlli dei servizi selezionando *Usa controlli servizio* in Impostazioni *editor* nel profilo di configurazione.</span><span class="sxs-lookup"><span data-stu-id="461ba-286">You can enable service inspectors by checking *Use Service Inspectors* under *Editor Settings* in the Configuration Profile.</span></span>

### <a name="depth-buffer-renderer"></a><span data-ttu-id="461ba-287">Renderer del buffer di profondità</span><span class="sxs-lookup"><span data-stu-id="461ba-287">Depth buffer renderer</span></span>

<span data-ttu-id="461ba-288">La condivisione del buffer di profondità con alcune piattaforme di realtà mista può migliorare [la stabilizzazione dell'ologramma.](../performance/hologram-stabilization.md)</span><span class="sxs-lookup"><span data-stu-id="461ba-288">Sharing the depth buffer with some mixed reality platforms can improve [hologram stabilization](../performance/hologram-stabilization.md).</span></span> <span data-ttu-id="461ba-289">Ad esempio, la piattaforma Windows Mixed Reality può modificare la scena sottoposta a rendering per pixel in modo da rendere conto dei piccoli movimenti della testa durante il tempo necessario per il rendering di un frame.</span><span class="sxs-lookup"><span data-stu-id="461ba-289">For example, the Windows Mixed Reality platform can modify the rendered scene per-pixel to account for subtle head movements during the time it took to render a frame.</span></span> <span data-ttu-id="461ba-290">Tuttavia, queste tecniche richiedono buffer di profondità con dati accurati per sapere dove e quanto è distante la geometria dall'utente.</span><span class="sxs-lookup"><span data-stu-id="461ba-290">However, these techniques require depth buffers with accurate data to know where and how far geometry is from the user.</span></span>

<span data-ttu-id="461ba-291">Per assicurarsi che una scena eserciti il rendering di tutti i dati necessari nel buffer di profondità, gli sviluppatori possono attivare o disattivare la funzionalità *Buffer* di profondità di rendering in *Impostazioni editor* nel profilo di configurazione.</span><span class="sxs-lookup"><span data-stu-id="461ba-291">To ensure a scene renders all necessary data to the depth buffer, developers can toggle the *Render Depth Buffer* feature under *Editor Settings* in the Configuration Profile.</span></span> <span data-ttu-id="461ba-292">In questo modo il buffer di profondità corrente verrà visualizzato come colore per la visualizzazione della scena applicando un effetto di post-elaborazione, [`DepthBufferRenderer`](xref:Microsoft.MixedReality.Toolkit.Rendering.DepthBufferRenderer) , alla fotocamera principale.</span><span class="sxs-lookup"><span data-stu-id="461ba-292">This will take the current depth buffer and render it as color to the scene view by applying a post-processing effect, [`DepthBufferRenderer`](xref:Microsoft.MixedReality.Toolkit.Rendering.DepthBufferRenderer), to the main camera.</span></span>

<span data-ttu-id="461ba-293">![Utilità buffer di profondità di rendering Il cilindro blu nella scena ha un materiale con ](../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_DepthBufferExample.gif)
 <sup>ZWrite disattivato in modo</sup> che non siano scritti dati di profondità</span><span class="sxs-lookup"><span data-stu-id="461ba-293">![Render Depth Buffer Utility](../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_DepthBufferExample.gif)
<sup>The blue cylinder in the scene has a material with ZWrite off so no depth data is written</sup></span></span>

## <a name="changing-profiles-at-runtime"></a><span data-ttu-id="461ba-294">Modifica dei profili in fase di esecuzione</span><span class="sxs-lookup"><span data-stu-id="461ba-294">Changing profiles at runtime</span></span>

<span data-ttu-id="461ba-295">È possibile aggiornare i profili in fase di esecuzione e in genere esistono due scenari e orari diversi in cui è utile:</span><span class="sxs-lookup"><span data-stu-id="461ba-295">It is possible to update profiles at runtime, and there are generally two different scenarios and times in which in this is helpful:</span></span>

1. <span data-ttu-id="461ba-296">Pre-opzione del profilo di inizializzazione **MRTK:** all'avvio, prima dell'inizializzazione di MRTK e del profilo diventa attivo, sostituendo il profilo non ancora in uso per abilitare o disabilitare funzionalità diverse in base alle funzionalità del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="461ba-296">**Pre MRTK initialization profile switch**: At startup, before the MRTK is initialized and profile becomes active, replacing the not-yet-in-use profile to enable/disable different features based on the device capabilities.</span></span> <span data-ttu-id="461ba-297">Ad esempio, se l'esperienza è in esecuzione nella realtà virtuale che non ha hardware di mapping spaziale, probabilmente non ha senso che il componente di mapping spaziale sia abilitato.</span><span class="sxs-lookup"><span data-stu-id="461ba-297">For example, if the experience is running in VR that doesn't have spatial mapping hardware it probably doesn't make sense to have spatial mapping component enabled.</span></span>
1. <span data-ttu-id="461ba-298">**Opzione profilo attivo:** dopo l'avvio, dopo l'inizializzazione di MRTK e l'attivazione di un profilo, lo scambio del profilo attualmente in uso per modificare il comportamento di determinate funzionalità.</span><span class="sxs-lookup"><span data-stu-id="461ba-298">**Active profile switch**: After startup, after the MRTK is initialized and a profile has become active, swapping the profile currently in use to change the way certain features behave.</span></span> <span data-ttu-id="461ba-299">Ad esempio, potrebbe essere presente un'esperienza secondaria specifica nell'applicazione che vuole rimuovere completamente i puntatori a mano.</span><span class="sxs-lookup"><span data-stu-id="461ba-299">For example, there may be a specific sub-experience in the application that wants far hand pointers completely removed.</span></span>

### <a name="pre-mrtk-initialization-profile-switch"></a><span data-ttu-id="461ba-300">Opzione del profilo di inizializzazione MRTK precedente</span><span class="sxs-lookup"><span data-stu-id="461ba-300">Pre MRTK initialization profile switch</span></span>

<span data-ttu-id="461ba-301">Questa operazione può essere eseguita collegando un oggetto MonoBehaviour (esempio seguente) che viene eseguito prima dell'inizializzazione di MRTK (ad esempio, Awake()).</span><span class="sxs-lookup"><span data-stu-id="461ba-301">This can be accomplished by attaching a MonoBehaviour (example below) which runs before MRTK initialization (i.e. Awake()).</span></span> <span data-ttu-id="461ba-302">Si noti che lo script , ad esempio la chiamata a , deve essere eseguito prima dello script, che può essere ottenuto impostando le impostazioni dell'ordine di esecuzione `SetProfileBeforeInitialization` `MixedRealityToolkit` dello [script.](https://docs.unity3d.com/Manual/class-MonoManager.html)</span><span class="sxs-lookup"><span data-stu-id="461ba-302">Note the script (i.e. call to `SetProfileBeforeInitialization`) have to be executed earlier than the `MixedRealityToolkit` script, which can be achieved by setting [Script Execution Order settings](https://docs.unity3d.com/Manual/class-MonoManager.html).</span></span>

```csharp
using Microsoft.MixedReality.Toolkit;
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
public class PreInitProfileSwapper : MonoBehaviour
{

    [SerializeField]
    private MixedRealityToolkitConfigurationProfile profileToUse = null;

    private void Awake()
    {
        // Here you could choose any arbitrary MixedRealityToolkitConfigurationProfile (for example, you could
        // add some platform checking code here to determine which profile to load).
        MixedRealityToolkit.SetProfileBeforeInitialization(profileToUse);
    }
}
```

<span data-ttu-id="461ba-303">Invece di "profileToUse", è possibile avere un set arbitrario di profili che si applicano a piattaforme specifiche (ad esempio, uno per HoloLens 1, uno per la realtà virtuale, uno per HoloLens 2 e così via).</span><span class="sxs-lookup"><span data-stu-id="461ba-303">Instead of "profileToUse", it's possible to have some arbitrary set of profiles which apply to specific platforms (for example, one for HoloLens 1, one for VR, one for HoloLens 2, etc).</span></span> <span data-ttu-id="461ba-304">È possibile usare vari altri indicatori (ad esempio , o se la fotocamera è opaca/trasparente) per determinare il profilo https://docs.unity3d.com/ScriptReference/SystemInfo.html da caricare.</span><span class="sxs-lookup"><span data-stu-id="461ba-304">It's possible to use various other indicators (e.g. https://docs.unity3d.com/ScriptReference/SystemInfo.html, or whether or not the camera is opaque/transparent), to figure out which profile to load.</span></span>

### <a name="active-profile-switch"></a><span data-ttu-id="461ba-305">Opzione del profilo attivo</span><span class="sxs-lookup"><span data-stu-id="461ba-305">Active profile switch</span></span>

<span data-ttu-id="461ba-306">A tale scopo, impostare la `MixedRealityToolkit.Instance.ActiveProfile` proprietà su un nuovo profilo sostituendo il profilo attivo.</span><span class="sxs-lookup"><span data-stu-id="461ba-306">This can be accomplished by setting the `MixedRealityToolkit.Instance.ActiveProfile` property to a new profile replacing the active profile.</span></span>

```csharp
MixedRealityToolkit.Instance.ActiveProfile = profileToUse;
```

<span data-ttu-id="461ba-307">Si noti che quando si imposta durante il runtime, l'eliminazione dei servizi attualmente in esecuzione verrà eseguita dopo l'ultimo LateUpdate() di tutti i servizi e la creazione e l'inizializzazione dei servizi associati al nuovo profilo verranno eseguite prima del primo Update() di tutti i `ActiveProfile` servizi.</span><span class="sxs-lookup"><span data-stu-id="461ba-307">Note when setting `ActiveProfile` during runtime, the destroy of the currently running services will happen after the last LateUpdate() of all services, and the instantiation and initialization of the services associated with the new profile will happen before the first Update() of all services.</span></span>

<span data-ttu-id="461ba-308">Durante questo processo può verificarsi un'esitazione evidente dell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="461ba-308">A noticeable application hesitation may occur during this process.</span></span> <span data-ttu-id="461ba-309">Anche qualsiasi script con priorità più alta rispetto allo `MixedRealityToolkit` script può immettere il relativo aggiornamento prima che il nuovo profilo sia configurato correttamente.</span><span class="sxs-lookup"><span data-stu-id="461ba-309">Also any script with higher priority than the `MixedRealityToolkit` script can enter its Update before the new profile is properly setup.</span></span> <span data-ttu-id="461ba-310">Per [altre informazioni sulla priorità dello script,](https://docs.unity3d.com/Manual/class-MonoManager.html) vedere Impostazioni dell'ordine di esecuzione degli script.</span><span class="sxs-lookup"><span data-stu-id="461ba-310">See [Script Execution Order settings](https://docs.unity3d.com/Manual/class-MonoManager.html) for more information on script priority.</span></span>

<span data-ttu-id="461ba-311">Nel processo di cambio profilo la fotocamera dell'interfaccia utente esistente rimarrà invariata, assicurando che i componenti dell'interfaccia utente di Unity che richiedono canvas funzionino ancora dopo il passaggio.</span><span class="sxs-lookup"><span data-stu-id="461ba-311">In the profile switching process the existing UI camera will remain unchanged, ensuring Unity UI components that require canvas still work after the switch.</span></span>

## <a name="see-also"></a><span data-ttu-id="461ba-312">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="461ba-312">See also</span></span>

- [<span data-ttu-id="461ba-313">Stabilizzazione dell'ologramma</span><span class="sxs-lookup"><span data-stu-id="461ba-313">Hologram Stabilization</span></span>](../performance/hologram-stabilization.md)
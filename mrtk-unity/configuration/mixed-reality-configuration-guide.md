---
title: Guida alla configurazione della realtà mista
description: Documentazione per configurare MRTK in Unity.
author: RogPodge
ms.author: roliu
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: b714e01a0969b88a4ca7a3a5047bc5d61516e3f3
ms.sourcegitcommit: bb9f54f3e872a5464a5d9ba88b7ab5b8896efd82
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/25/2021
ms.locfileid: "110345144"
---
# <a name="mixed-reality-toolkit-profile-configuration-guide"></a><span data-ttu-id="063a0-104">Guida alla configurazione del profilo di Mixed Reality Toolkit</span><span class="sxs-lookup"><span data-stu-id="063a0-104">Mixed Reality Toolkit profile configuration guide</span></span>

![Logo di MRTK](../features/images/MRTK_Logo_Rev.png)

<span data-ttu-id="063a0-106">Mixed Reality Toolkit centralizza la maggior parte della configurazione necessaria per gestire il toolkit il più possibile (ad eccezione dei veri "cose" di runtime).</span><span class="sxs-lookup"><span data-stu-id="063a0-106">The Mixed Reality Toolkit centralizes as much of the configuration required to manage the toolkit as possible (except for true runtime "things").</span></span>

<span data-ttu-id="063a0-107">Questa guida è una procedura dettagliata semplice per ognuna delle schermate del profilo di configurazione attualmente disponibili per il toolkit.</span><span class="sxs-lookup"><span data-stu-id="063a0-107">This guide is a simple walkthrough for each of the configuration profile screens currently available for the toolkit.</span></span>

## <a name="the-main-mixed-reality-toolkit-configuration-profile"></a><span data-ttu-id="063a0-108">Profilo di configurazione principale di Mixed Reality Toolkit</span><span class="sxs-lookup"><span data-stu-id="063a0-108">The main Mixed Reality Toolkit configuration profile</span></span>

<span data-ttu-id="063a0-109">Il profilo di configurazione principale, collegato al GameObject *MixedRealityToolkit* nella scena, fornisce il punto di ingresso principale per il Toolkit nel progetto.</span><span class="sxs-lookup"><span data-stu-id="063a0-109">The main configuration profile, which is attached to the *MixedRealityToolkit* GameObject in your Scene, provides the main entry point for the Toolkit in your project.</span></span>

> [!NOTE]
> <span data-ttu-id="063a0-110">Mixed Reality Toolkit "blocca" le schermate di configurazione predefinite per assicurarsi di avere sempre un punto di partenza comune per il progetto ed è consigliato iniziare a definire impostazioni personalizzate con l'evolversi del progetto.</span><span class="sxs-lookup"><span data-stu-id="063a0-110">The Mixed Reality Toolkit "locks" the default configuration screens to ensure you always have a common start point for your project and it is encouraged to start defining your own settings as your project evolves.</span></span> <span data-ttu-id="063a0-111">La configurazione di MRTK non è modificabile durante la modalità di riproduzione.</span><span class="sxs-lookup"><span data-stu-id="063a0-111">The MRTK configuration is not editable during play-mode.</span></span>

![Profilo di configurazione di MRTK](../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_ActiveConfiguration.png)

<span data-ttu-id="063a0-113">Tutti i profili "predefiniti" per Mixed Reality Toolkit sono disponibili nel progetto SDK nella cartella Assets/MRTK/SDK/Profiles.</span><span class="sxs-lookup"><span data-stu-id="063a0-113">All the "default" profiles for the Mixed Reality Toolkit can be found in the SDK project in the folder Assets/MRTK/SDK/Profiles.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="063a0-114">DefaultHoloLens2ConfigurationProfile è ottimizzato per HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="063a0-114">DefaultHoloLens2ConfigurationProfile is optimized for HoloLens 2.</span></span> <span data-ttu-id="063a0-115">Per [informazioni dettagliate,](../features/profiles/profiles.md) vedere Profili.</span><span class="sxs-lookup"><span data-stu-id="063a0-115">See [Profiles](../features/profiles/profiles.md) for the details.</span></span>

<span data-ttu-id="063a0-116">Quando apri il profilo di configurazione principale di Mixed Reality Toolkit, nella finestra di controllo verrà visualizzata la schermata seguente:</span><span class="sxs-lookup"><span data-stu-id="063a0-116">When you open the main Mixed Reality Toolkit Configuration Profile, you will see the following screen in the inspector:</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_MixedRealityToolkitConfigurationScreen.png" width="650px" alt="MRTK configuration scene" style="display:block;">

<span data-ttu-id="063a0-117">Se si seleziona un asset MixedRealityToolkitConfigurationProfile senza MixedRealityToolkit nella scena, verrà chiesto se si vuole che MRTK configura automaticamente la scena.</span><span class="sxs-lookup"><span data-stu-id="063a0-117">If you select a MixedRealityToolkitConfigurationProfile asset without the MixedRealityToolkit in the scene, it will ask you if you want the MRTK to automatically setup the scene for you.</span></span> <span data-ttu-id="063a0-118">Questo è facoltativo, tuttavia, deve essere presente un oggetto MixedRealityToolkit attivo nella scena per accedere a tutte le schermate di configurazione.</span><span class="sxs-lookup"><span data-stu-id="063a0-118">This is optional, however, there must be an active MixedRealityToolkit object in the scene to access all the configuration screens.</span></span>

<span data-ttu-id="063a0-119">In questo modo viene ospitata la configurazione di runtime attiva corrente per il progetto.</span><span class="sxs-lookup"><span data-stu-id="063a0-119">This houses the current active runtime configuration for the project.</span></span>

<span data-ttu-id="063a0-120">Da qui è possibile passare a tutti i profili di configurazione per MRTK, tra cui:</span><span class="sxs-lookup"><span data-stu-id="063a0-120">From here you can navigate to all the configuration profiles for the MRTK, including:</span></span>

- [<span data-ttu-id="063a0-121">Guida alla configurazione del profilo di Mixed Reality Toolkit</span><span class="sxs-lookup"><span data-stu-id="063a0-121">Mixed Reality Toolkit profile configuration guide</span></span>](#mixed-reality-toolkit-profile-configuration-guide)
  - [<span data-ttu-id="063a0-122">Profilo di configurazione principale di Mixed Reality Toolkit</span><span class="sxs-lookup"><span data-stu-id="063a0-122">The main Mixed Reality Toolkit configuration profile</span></span>](#the-main-mixed-reality-toolkit-configuration-profile)
  - [<span data-ttu-id="063a0-123">Impostazioni dell'esperienza</span><span class="sxs-lookup"><span data-stu-id="063a0-123">Experience settings</span></span>](#experience-settings)
  - [<span data-ttu-id="063a0-124">Impostazioni della fotocamera</span><span class="sxs-lookup"><span data-stu-id="063a0-124">Camera settings</span></span>](#camera-settings)
  - [<span data-ttu-id="063a0-125">Impostazioni del sistema di input</span><span class="sxs-lookup"><span data-stu-id="063a0-125">Input system settings</span></span>](#input-system-settings)
  - [<span data-ttu-id="063a0-126">Impostazioni di visualizzazione dei limiti</span><span class="sxs-lookup"><span data-stu-id="063a0-126">Boundary visualization settings</span></span>](#boundary-visualization-settings)
  - [<span data-ttu-id="063a0-127">Selezione del sistema di teletrasporto</span><span class="sxs-lookup"><span data-stu-id="063a0-127">Teleportation system selection</span></span>](#teleportation-system-selection)
  - [<span data-ttu-id="063a0-128">Impostazioni di consapevolezza spaziale</span><span class="sxs-lookup"><span data-stu-id="063a0-128">Spatial awareness settings</span></span>](#spatial-awareness-settings)
  - [<span data-ttu-id="063a0-129">Impostazioni di diagnostica</span><span class="sxs-lookup"><span data-stu-id="063a0-129">Diagnostics settings</span></span>](#diagnostics-settings)
  - [<span data-ttu-id="063a0-130">Impostazioni di sistema della scena</span><span class="sxs-lookup"><span data-stu-id="063a0-130">Scene system settings</span></span>](#scene-system-settings)
  - [<span data-ttu-id="063a0-131">Impostazioni dei servizi aggiuntivi</span><span class="sxs-lookup"><span data-stu-id="063a0-131">Additional services settings</span></span>](#additional-services-settings)
  - [<span data-ttu-id="063a0-132">Impostazioni delle azioni di input</span><span class="sxs-lookup"><span data-stu-id="063a0-132">Input actions settings</span></span>](#input-actions-settings)
  - [<span data-ttu-id="063a0-133">Regole delle azioni di input</span><span class="sxs-lookup"><span data-stu-id="063a0-133">Input actions rules</span></span>](#input-actions-rules)
  - [<span data-ttu-id="063a0-134">Configurazione del puntatore</span><span class="sxs-lookup"><span data-stu-id="063a0-134">Pointer configuration</span></span>](#pointer-configuration)
  - [<span data-ttu-id="063a0-135">Configurazione dei movimenti</span><span class="sxs-lookup"><span data-stu-id="063a0-135">Gestures configuration</span></span>](#gestures-configuration)
  - [<span data-ttu-id="063a0-136">Comandi vocali</span><span class="sxs-lookup"><span data-stu-id="063a0-136">Speech commands</span></span>](#speech-commands)
  - [<span data-ttu-id="063a0-137">Configurazione del mapping del controller</span><span class="sxs-lookup"><span data-stu-id="063a0-137">Controller mapping configuration</span></span>](#controller-mapping-configuration)
  - [<span data-ttu-id="063a0-138">Impostazioni di visualizzazione del controller</span><span class="sxs-lookup"><span data-stu-id="063a0-138">Controller visualization settings</span></span>](#controller-visualization-settings)
  - [<span data-ttu-id="063a0-139">Utilità dell'editor</span><span class="sxs-lookup"><span data-stu-id="063a0-139">Editor utilities</span></span>](#editor-utilities)
    - [<span data-ttu-id="063a0-140">Controlli dei servizi</span><span class="sxs-lookup"><span data-stu-id="063a0-140">Service inspectors</span></span>](#service-inspectors)
    - [<span data-ttu-id="063a0-141">Renderer del buffer di profondità</span><span class="sxs-lookup"><span data-stu-id="063a0-141">Depth buffer renderer</span></span>](#depth-buffer-renderer)
  - [<span data-ttu-id="063a0-142">Modifica dei profili in fase di esecuzione</span><span class="sxs-lookup"><span data-stu-id="063a0-142">Changing profiles at runtime</span></span>](#changing-profiles-at-runtime)
    - [<span data-ttu-id="063a0-143">Opzione del profilo di inizializzazione di MRTK precedente</span><span class="sxs-lookup"><span data-stu-id="063a0-143">Pre MRTK initialization profile switch</span></span>](#pre-mrtk-initialization-profile-switch)
    - [<span data-ttu-id="063a0-144">Opzione del profilo attivo</span><span class="sxs-lookup"><span data-stu-id="063a0-144">Active profile switch</span></span>](#active-profile-switch)
  - [<span data-ttu-id="063a0-145">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="063a0-145">See also</span></span>](#see-also)

<span data-ttu-id="063a0-146">Questi profili di configurazione sono riportati di seguito nelle sezioni pertinenti:</span><span class="sxs-lookup"><span data-stu-id="063a0-146">These configuration profiles are detailed below in their relevant sections:</span></span>

---
<a name="experience"></a>

## <a name="experience-settings"></a><span data-ttu-id="063a0-147">Impostazioni dell'esperienza</span><span class="sxs-lookup"><span data-stu-id="063a0-147">Experience settings</span></span>

<span data-ttu-id="063a0-148">Disponibile nella pagina principale di configurazione di Mixed Reality Toolkit, questa impostazione definisce il funzionamento predefinito della scalabilità dell'ambiente di [realtà mista](/windows/mixed-reality/coordinate-systems-in-unity) per il progetto.</span><span class="sxs-lookup"><span data-stu-id="063a0-148">Located on the main Mixed Reality Toolkit configuration page, this setting defines the default operation of the [Mixed Reality environment scale](/windows/mixed-reality/coordinate-systems-in-unity) for your project.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_ExperienceSettings.png" width="650px" alt="Experiance settings" style="display:block;">

---
<a name="camera"></a>

## <a name="camera-settings"></a><span data-ttu-id="063a0-149">Impostazioni della fotocamera</span><span class="sxs-lookup"><span data-stu-id="063a0-149">Camera settings</span></span>

<span data-ttu-id="063a0-150">Le impostazioni della fotocamera definiscono come verrà impostata la fotocamera per il progetto di realtà mista, definendo le impostazioni generiche di ritaglio, qualità e trasparenza.</span><span class="sxs-lookup"><span data-stu-id="063a0-150">The camera settings define how the camera will be setup for your Mixed Reality project, defining the generic clipping, quality and transparency settings.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_CameraProfile.png" width="650px" alt="Camera Profile" style="display:block;">

---
<a name="inputsystem"></a>

## <a name="input-system-settings"></a><span data-ttu-id="063a0-151">Impostazioni di sistema di input</span><span class="sxs-lookup"><span data-stu-id="063a0-151">Input system settings</span></span>

<span data-ttu-id="063a0-152">Il progetto di realtà mista offre un sistema di input affidabile e ben formato per il routing di tutti gli eventi di input intorno al progetto selezionato per impostazione predefinita.</span><span class="sxs-lookup"><span data-stu-id="063a0-152">The Mixed Reality Project provides a robust and well-trained input system for routing all the input events around the project which is selected by default.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_InputSystemSelection.png" width="650px" alt="Input System settings 1" style="display:block;">

<span data-ttu-id="063a0-153">Dietro il sistema di input fornito da MRTK ci sono diversi altri sistemi, che consentono di gestire le complesse inter-tessere necessarie per astrarre le complessità di un framework multipiattaforma/realtà mista.</span><span class="sxs-lookup"><span data-stu-id="063a0-153">Behind the Input System provided by the MRTK are several other systems, these help to drive and manage the complex inter-weavings required to abstract out the complexities of a multi-platform / mixed reality framework.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_InputSystemProfile.png" width="650px" alt="Input System settings 2" style="display:block;">

<span data-ttu-id="063a0-154">Ognuno dei singoli profili è descritto in dettaglio di seguito:</span><span class="sxs-lookup"><span data-stu-id="063a0-154">Each of the individual profiles are detailed below:</span></span>

- <span data-ttu-id="063a0-155">Impostazioni dello stato attivo</span><span class="sxs-lookup"><span data-stu-id="063a0-155">Focus Settings</span></span>
- [<span data-ttu-id="063a0-156">Impostazioni delle azioni di input</span><span class="sxs-lookup"><span data-stu-id="063a0-156">Input actions settings</span></span>](#input-actions-settings)
- [<span data-ttu-id="063a0-157">Regole delle azioni di input</span><span class="sxs-lookup"><span data-stu-id="063a0-157">Input actions rules</span></span>](#input-actions-rules)
- [<span data-ttu-id="063a0-158">Configurazione del puntatore</span><span class="sxs-lookup"><span data-stu-id="063a0-158">Pointer configuration</span></span>](#pointer-configuration)
- [<span data-ttu-id="063a0-159">Configurazione dei movimenti</span><span class="sxs-lookup"><span data-stu-id="063a0-159">Gestures configuration</span></span>](#gestures-configuration)
- [<span data-ttu-id="063a0-160">Comandi vocali</span><span class="sxs-lookup"><span data-stu-id="063a0-160">Speech commands</span></span>](#speech-commands)
- [<span data-ttu-id="063a0-161">Configurazione del mapping del controller</span><span class="sxs-lookup"><span data-stu-id="063a0-161">Controller mapping configuration</span></span>](#controller-mapping-configuration)
- [<span data-ttu-id="063a0-162">Impostazioni di visualizzazione del controller</span><span class="sxs-lookup"><span data-stu-id="063a0-162">Controller visualization settings</span></span>](#controller-visualization-settings)

---
<a name="boundary"></a>

## <a name="boundary-visualization-settings"></a><span data-ttu-id="063a0-163">Impostazioni di visualizzazione dei limiti</span><span class="sxs-lookup"><span data-stu-id="063a0-163">Boundary visualization settings</span></span>

<span data-ttu-id="063a0-164">Il sistema di limiti trasla il limite percepito segnalato dal sistema di limiti/guardiani delle piattaforme sottostanti.</span><span class="sxs-lookup"><span data-stu-id="063a0-164">The boundary system translates the perceived boundary reported by the underlying platforms boundary / guardian system.</span></span> <span data-ttu-id="063a0-165">La configurazione del visualizzatore di limiti consente di visualizzare automaticamente il limite registrato all'interno della scena rispetto alla posizione dell'utente. Il limite reagirà o si aggiornerà anche in base al punto in cui l'utente si teletrasporta all'interno della scena.</span><span class="sxs-lookup"><span data-stu-id="063a0-165">The Boundary visualizer configuration gives you the ability to automatically show the recorded boundary within your scene relative to the user's position.The boundary will also react / update based on where the user teleports within the scene.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_BoundaryVisualizationProfile.png" width="650px" alt="Boundry Visualization Settings" style="display:block;">

---
<a name="teleportation"></a>

## <a name="teleportation-system-selection"></a><span data-ttu-id="063a0-166">Selezione del sistema di teletrasporto</span><span class="sxs-lookup"><span data-stu-id="063a0-166">Teleportation system selection</span></span>

<span data-ttu-id="063a0-167">Il progetto di realtà mista offre un sistema di teletrasporto completo per la gestione degli eventi di teletrasporto nel progetto, selezionato per impostazione predefinita.</span><span class="sxs-lookup"><span data-stu-id="063a0-167">The Mixed Reality Project provides a full featured Teleportation system for managing teleportation events in the project which is selected by default.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_TeleportationSystemSelection.png" width="650px" alt="Teleport System settings" style="display:block;">

---
<a name="spatialawareness"></a>

## <a name="spatial-awareness-settings"></a><span data-ttu-id="063a0-168">Impostazioni di consapevolezza spaziale</span><span class="sxs-lookup"><span data-stu-id="063a0-168">Spatial awareness settings</span></span>

<span data-ttu-id="063a0-169">Il progetto di realtà mista fornisce un sistema di consapevolezza spaziale ricompilato per l'uso di sistemi di analisi spaziale nel progetto, che è selezionato per impostazione predefinita.</span><span class="sxs-lookup"><span data-stu-id="063a0-169">The Mixed Reality Project provides a rebuilt spatial awareness system for working with spatial scanning systems in the project which is selected by default.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_SpatialAwarenessSystemSelection.png" width="650px" alt="Spatial Awareness settings 1" style="display:block;">

<span data-ttu-id="063a0-170">La configurazione della consapevolezza spaziale di Mixed Reality Toolkit consente di personalizzare la modalità di avvio del sistema, indipendentemente dal fatto che sia automaticamente all'avvio dell'applicazione o in un secondo momento a livello di codice, nonché di impostare gli extent per il campo di visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="063a0-170">The Mixed Reality Toolkit spatial awareness configuration lets you tailor how the system starts, whether it is automatically when the application starts or later programmatically as well as setting the extents for the field of view.</span></span>

<span data-ttu-id="063a0-171">Consente anche di configurare le impostazioni della mesh e della superficie, personalizzando ulteriormente il modo in cui il progetto comprende l'ambiente intorno all'utente.</span><span class="sxs-lookup"><span data-stu-id="063a0-171">It also lets you configure the mesh and surface settings, further customizing how your project understands the environment around you.</span></span>

<span data-ttu-id="063a0-172">Questo è applicabile solo per i dispositivi che possono fornire un ambiente analizzato.</span><span class="sxs-lookup"><span data-stu-id="063a0-172">This is only applicable for devices that can provide a scanned environment.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_SpatialAwarenessProfile.png" width="650px" alt="Spatial Awareness settings 2" style="display:block;">

---
<a name="diagnostic"></a>

## <a name="diagnostics-settings"></a><span data-ttu-id="063a0-173">Impostazioni di diagnostica</span><span class="sxs-lookup"><span data-stu-id="063a0-173">Diagnostics settings</span></span>

<span data-ttu-id="063a0-174">Una funzionalità facoltativa ma estremamente utile di MRTK è la funzionalità di diagnostica del plug-in.</span><span class="sxs-lookup"><span data-stu-id="063a0-174">An optional but highly useful feature of the MRTK is the plugin diagnostics functionality.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_DiagnosticsSystemSelection.png" width="650px" alt="Diagnostics settings" style="display:block;">

<span data-ttu-id="063a0-175">Il profilo di diagnostica fornisce diversi sistemi semplici da monitorare durante l'esecuzione del progetto, tra cui un pratico interruttore On/Off per abilitare/disabilitare il pannello di visualizzazione nella scena.</span><span class="sxs-lookup"><span data-stu-id="063a0-175">The diagnostics profile provides several simple systems to monitor whilst the project is running, including a handy On/Off switch to enable / disable the display panel in the scene.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_DiagnosticsProfile.png" width="650px" alt="Diagnostics settings System settings 2" style="display:block;">

---
<a name="scenesystem"></a>

## <a name="scene-system-settings"></a><span data-ttu-id="063a0-176">Impostazioni di sistema della scena</span><span class="sxs-lookup"><span data-stu-id="063a0-176">Scene system settings</span></span>

<span data-ttu-id="063a0-177">MRTK fornisce questo servizio facoltativo che consente di gestire il caricamento/scaricamento di scene additive complesse.</span><span class="sxs-lookup"><span data-stu-id="063a0-177">The MRTK provides this optional service to help you manage complex additive scene loading / unloading.</span></span> <span data-ttu-id="063a0-178">Per decidere se il sistema della scena è una scelta adatta al progetto, leggi la Guida al sistema [Attività iniziali scena.](../features/scene-system/scene-system-getting-started.md)</span><span class="sxs-lookup"><span data-stu-id="063a0-178">To decide if the Scene System would be a good fit for your project, read the [Scene System Getting Started Guide.](../features/scene-system/scene-system-getting-started.md)</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_SceneSystemProfile.png" width="650px" alt="Scene System settings 1" style="display:block;">

---
<a name="services"></a>

## <a name="additional-services-settings"></a><span data-ttu-id="063a0-179">Impostazioni dei servizi aggiuntivi</span><span class="sxs-lookup"><span data-stu-id="063a0-179">Additional services settings</span></span>

<span data-ttu-id="063a0-180">Una delle aree più avanzate di Mixed [](https://en.wikipedia.org/wiki/Service_locator_pattern) Reality Toolkit è l'implementazione del modello di localizzatore di servizi che consente la registrazione di qualsiasi "servizio" con il framework.</span><span class="sxs-lookup"><span data-stu-id="063a0-180">One of the more advanced areas of the Mixed Reality Toolkit is its [service locator pattern](https://en.wikipedia.org/wiki/Service_locator_pattern) implementation which allows the registering of any "Service" with the framework.</span></span> <span data-ttu-id="063a0-181">In questo modo il framework può essere esteso con facilità con nuove funzionalità/sistemi, ma consente anche ai progetti di sfruttare queste funzionalità per registrare i propri componenti di runtime.</span><span class="sxs-lookup"><span data-stu-id="063a0-181">This allows the framework to be both extended with new features / systems easily but also allows for projects to take advantage of these capabilities to register their own runtime components.</span></span>

<span data-ttu-id="063a0-182">Qualsiasi servizio registrato ottiene comunque il vantaggio completo di tutti gli eventi unity, senza il sovraccarico e il costo dell'implementazione di modelli singleton MonoBehaviour o clunky.</span><span class="sxs-lookup"><span data-stu-id="063a0-182">Any registered service still gets the full advantage of all of the Unity events, without the overhead and cost of implementing a MonoBehaviour or clunky singleton patterns.</span></span> <span data-ttu-id="063a0-183">Ciò consente componenti C# puri senza overhead della scena per l'esecuzione di processi in primo piano e in background, ad esempio sistemi di generazione, logica di gioco di runtime o praticamente qualsiasi altro elemento.</span><span class="sxs-lookup"><span data-stu-id="063a0-183">This allows for pure C# components with no scene overhead for running both foreground and background processes, e.g. spawning systems, runtime game logic, or practically anything else.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_RegisteredServiceProvidersProfile.png" width="650px" alt="additional System settings" style="display:block;">

---
<a name="inputactions"></a>

## <a name="input-actions-settings"></a><span data-ttu-id="063a0-184">Impostazioni delle azioni di input</span><span class="sxs-lookup"><span data-stu-id="063a0-184">Input actions settings</span></span>

<span data-ttu-id="063a0-185">Le azioni di input consentono di astrarre eventuali interazioni fisiche e input da un progetto di runtime.</span><span class="sxs-lookup"><span data-stu-id="063a0-185">Input actions provide a way to abstract any physical interactions and input from a runtime project.</span></span> <span data-ttu-id="063a0-186">Tutto l'input fisico (da controller/mani/mouse/e così via) viene convertito in un'azione di input logica da usare nel progetto di runtime.</span><span class="sxs-lookup"><span data-stu-id="063a0-186">All physical input (from controllers / hands / mouse / etc) is translated in to a logical input action for use in your runtime project.</span></span> <span data-ttu-id="063a0-187">In questo modo, indipendentemente dall'origine dell'input, il progetto implementa semplicemente queste azioni come "Cose da fare" o "Interagisci" nelle scene.</span><span class="sxs-lookup"><span data-stu-id="063a0-187">This ensures no matter where the input comes from, your project simply implements these actions as "Things to do" or "Interact with" in your scenes.</span></span>

<span data-ttu-id="063a0-188">Per creare una nuova azione di input, è sufficiente fare clic sul pulsante "Aggiungi una nuova azione" e immettere un nome di testo descrittivo per ciò che rappresenta.</span><span class="sxs-lookup"><span data-stu-id="063a0-188">To create a new input action, simply click the "Add a new Action" button and enter a friendly text name for what it represents.</span></span> <span data-ttu-id="063a0-189">È quindi necessario selezionare solo un asse (il tipo di dati) a cui l'azione deve comunicare o, nel caso dei controller fisici, il tipo di input fisico a cui può essere collegata, ad esempio:</span><span class="sxs-lookup"><span data-stu-id="063a0-189">You then only need select an axis (the type of data) the action is meant to convey, or in the case of physical controllers, the physical input type it can be attached to, for example:</span></span>

| <span data-ttu-id="063a0-190">Vincolo dell'asse</span><span class="sxs-lookup"><span data-stu-id="063a0-190">Axis Constraint</span></span> | <span data-ttu-id="063a0-191">Tipo di dati</span><span class="sxs-lookup"><span data-stu-id="063a0-191">Data Type</span></span> | <span data-ttu-id="063a0-192">Descrizione</span><span class="sxs-lookup"><span data-stu-id="063a0-192">Description</span></span> | <span data-ttu-id="063a0-193">Esempio d'uso</span><span class="sxs-lookup"><span data-stu-id="063a0-193">Example use</span></span> |
| :--- | :--- | :--- | :--- |
| <span data-ttu-id="063a0-194">Nessuno</span><span class="sxs-lookup"><span data-stu-id="063a0-194">None</span></span> | <span data-ttu-id="063a0-195">Nessun dato</span><span class="sxs-lookup"><span data-stu-id="063a0-195">No data</span></span> | <span data-ttu-id="063a0-196">Usato per un'azione o un evento vuoto</span><span class="sxs-lookup"><span data-stu-id="063a0-196">Used for an empty action or event</span></span> | <span data-ttu-id="063a0-197">Trigger di evento</span><span class="sxs-lookup"><span data-stu-id="063a0-197">Event Trigger</span></span> |
| <span data-ttu-id="063a0-198">Non elaborato (riservato)</span><span class="sxs-lookup"><span data-stu-id="063a0-198">Raw (reserved)</span></span> | <span data-ttu-id="063a0-199">object</span><span class="sxs-lookup"><span data-stu-id="063a0-199">object</span></span> | <span data-ttu-id="063a0-200">Riservate per utilizzo futuro</span><span class="sxs-lookup"><span data-stu-id="063a0-200">Reserved for future use</span></span> | <span data-ttu-id="063a0-201">N/D</span><span class="sxs-lookup"><span data-stu-id="063a0-201">N/A</span></span> |
| <span data-ttu-id="063a0-202">Digitale</span><span class="sxs-lookup"><span data-stu-id="063a0-202">Digital</span></span> | <span data-ttu-id="063a0-203">bool</span><span class="sxs-lookup"><span data-stu-id="063a0-203">bool</span></span> | <span data-ttu-id="063a0-204">Dati di tipo booleano on o off</span><span class="sxs-lookup"><span data-stu-id="063a0-204">A boolean on or off type data</span></span> | <span data-ttu-id="063a0-205">Un pulsante del controller</span><span class="sxs-lookup"><span data-stu-id="063a0-205">A controller button</span></span> |
| <span data-ttu-id="063a0-206">Asse singolo</span><span class="sxs-lookup"><span data-stu-id="063a0-206">Single Axis</span></span> | <span data-ttu-id="063a0-207">float</span><span class="sxs-lookup"><span data-stu-id="063a0-207">float</span></span> | <span data-ttu-id="063a0-208">Un singolo valore di dati di precisione</span><span class="sxs-lookup"><span data-stu-id="063a0-208">A single precision data value</span></span> | <span data-ttu-id="063a0-209">Un input con intervallo, ad esempio un trigger</span><span class="sxs-lookup"><span data-stu-id="063a0-209">A ranged input, e.g. a trigger</span></span> |
| <span data-ttu-id="063a0-210">Asse doppio</span><span class="sxs-lookup"><span data-stu-id="063a0-210">Dual Axis</span></span> | <span data-ttu-id="063a0-211">Vector2</span><span class="sxs-lookup"><span data-stu-id="063a0-211">Vector2</span></span> | <span data-ttu-id="063a0-212">Data di tipo float doppia per più assi</span><span class="sxs-lookup"><span data-stu-id="063a0-212">A dual float type date for multiple axis</span></span> | <span data-ttu-id="063a0-213">Un Dpad o una levetta</span><span class="sxs-lookup"><span data-stu-id="063a0-213">A Dpad or Thumbstick</span></span> |
| <span data-ttu-id="063a0-214">Posizione tre Dof</span><span class="sxs-lookup"><span data-stu-id="063a0-214">Three Dof Position</span></span> | <span data-ttu-id="063a0-215">Vector3</span><span class="sxs-lookup"><span data-stu-id="063a0-215">Vector3</span></span> | <span data-ttu-id="063a0-216">Dati di tipo posizionale da con 3 assi float</span><span class="sxs-lookup"><span data-stu-id="063a0-216">Positional type data from with 3 float axis</span></span> | <span data-ttu-id="063a0-217">Controller solo stile di posizione 3D</span><span class="sxs-lookup"><span data-stu-id="063a0-217">3D position style only controller</span></span> |
| <span data-ttu-id="063a0-218">Rotazione di tre Dof</span><span class="sxs-lookup"><span data-stu-id="063a0-218">Three Dof Rotation</span></span> | <span data-ttu-id="063a0-219">Quaternion</span><span class="sxs-lookup"><span data-stu-id="063a0-219">Quaternion</span></span> | <span data-ttu-id="063a0-220">Input solo rotazionale con 4 assi float</span><span class="sxs-lookup"><span data-stu-id="063a0-220">Rotational only input with 4 float axis</span></span> | <span data-ttu-id="063a0-221">Un controller di tipo Tre gradi, ad esempio controller Oculus Go</span><span class="sxs-lookup"><span data-stu-id="063a0-221">A Three degrees style controller, e.g. Oculus Go controller</span></span> |
| <span data-ttu-id="063a0-222">Sei Dof</span><span class="sxs-lookup"><span data-stu-id="063a0-222">Six Dof</span></span> | <span data-ttu-id="063a0-223">Posizione in realtà mista (Vector3, Quaternion)</span><span class="sxs-lookup"><span data-stu-id="063a0-223">Mixed Reality Pose (Vector3, Quaternion)</span></span> | <span data-ttu-id="063a0-224">Input dello stile di posizione e rotazione con componenti Vector3 e Quaternion</span><span class="sxs-lookup"><span data-stu-id="063a0-224">A position and rotation style input with both Vector3 and Quaternion components</span></span> | <span data-ttu-id="063a0-225">Un controller del movimento o un puntatore</span><span class="sxs-lookup"><span data-stu-id="063a0-225">A motion controller or Pointer</span></span> |

<span data-ttu-id="063a0-226">Gli eventi che utilizzano azioni di input non sono limitati ai controller fisici e possono comunque essere utilizzati all'interno del progetto per fare in modo che gli effetti di runtime generino nuove azioni.</span><span class="sxs-lookup"><span data-stu-id="063a0-226">Events utilizing input actions are not limited to physical controllers and can still be utilized within the project to have runtime effects generate new actions.</span></span>

> [!NOTE]
> <span data-ttu-id="063a0-227">Le azioni di input sono uno dei pochi componenti non modificabili in fase di esecuzione, ma solo una configurazione in fase di progettazione.</span><span class="sxs-lookup"><span data-stu-id="063a0-227">Input actions are one of the few components which is not editable at runtime, they are a design time configuration only.</span></span> <span data-ttu-id="063a0-228">Questo profilo non deve essere scambiato mentre il progetto è in esecuzione a causa della dipendenza del framework (e dei progetti) dall'ID generato per ogni azione.</span><span class="sxs-lookup"><span data-stu-id="063a0-228">This profile should not be swapped out whilst the project is running due to the framework (and your projects) dependency on the ID's generated for each action.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_InputActionsProfile.png" width="650px" alt="Configuration Profile" style="display:block;">

---
<a name="inputactionrules"></a>

## <a name="input-actions-rules"></a><span data-ttu-id="063a0-229">Regole delle azioni di input</span><span class="sxs-lookup"><span data-stu-id="063a0-229">Input actions rules</span></span>

<span data-ttu-id="063a0-230">Le regole di azione di input consentono di convertire automaticamente un evento generato per un'azione di input in azioni diverse in base al valore dei dati.</span><span class="sxs-lookup"><span data-stu-id="063a0-230">Input action rules provide a way to automatically translate an event raised for one input action in to different actions based on its data value.</span></span> <span data-ttu-id="063a0-231">Questi vengono gestiti senza problemi all'interno del framework e non comportano costi per le prestazioni.</span><span class="sxs-lookup"><span data-stu-id="063a0-231">These are managed seamlessly within the framework and do not incur any performance costs.</span></span>

<span data-ttu-id="063a0-232">Ad esempio, la conversione del singolo evento di input doppio asse da un DPad in alle 4 azioni corrispondenti "Dpad Up" / "DPad Down" / "Dpad Left" / "Dpad Right" (come illustrato nell'immagine seguente).</span><span class="sxs-lookup"><span data-stu-id="063a0-232">For example, converting the single dual axis input event from a DPad in to the 4 corresponding "Dpad Up" / "DPad Down" / "Dpad Left" / "Dpad Right" actions (as shown in the image below).</span></span>

<span data-ttu-id="063a0-233">Questa operazione può essere eseguita anche nel codice.</span><span class="sxs-lookup"><span data-stu-id="063a0-233">This could also be done in your own code.</span></span> <span data-ttu-id="063a0-234">Tuttavia, poiché si tratta di un modello molto comune, il framework fornisce un meccanismo per eseguire questa operazione "predefinita"</span><span class="sxs-lookup"><span data-stu-id="063a0-234">However, seeing as this was a very common pattern, the framework provides a mechanism to do this "out of the box"</span></span>

<span data-ttu-id="063a0-235">Le regole dell'azione di input possono essere configurate per qualsiasi asse di input disponibile.</span><span class="sxs-lookup"><span data-stu-id="063a0-235">Input action Rules can be configured for any of the available input axis.</span></span> <span data-ttu-id="063a0-236">Tuttavia, le azioni di input da un tipo di asse possono essere convertite in un'altra azione di input dello stesso tipo di asse.</span><span class="sxs-lookup"><span data-stu-id="063a0-236">However, input actions from one axis type can be translated to another input action of the same axis type.</span></span> <span data-ttu-id="063a0-237">È possibile eseguire il mapping di un'azione asse doppio a un'altra azione asse doppio, ma non a un'azione digitale o nessuna azione.</span><span class="sxs-lookup"><span data-stu-id="063a0-237">You can map a dual axis action to another dual axis action, but not to a digital or none action.</span></span>

![Profilo delle regole di azione di input](../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_InputActionRulesProfile.png)

---
<a name="pointer"></a>

## <a name="pointer-configuration"></a><span data-ttu-id="063a0-239">Configurazione del puntatore</span><span class="sxs-lookup"><span data-stu-id="063a0-239">Pointer configuration</span></span>

<span data-ttu-id="063a0-240">I puntatori vengono usati per guidare l'interattività nella scena da qualsiasi dispositivo di input, fornendo sia una direzione che un hit test con qualsiasi oggetto in una scena (che ha un collisore collegato o è un componente dell'interfaccia utente).</span><span class="sxs-lookup"><span data-stu-id="063a0-240">Pointers are used to drive interactivity in the scene from any input device, giving both a direction and hit test with any object in a scene (that has a collider attached, or is a UI component).</span></span> <span data-ttu-id="063a0-241">Per impostazione predefinita, i puntatori vengono configurati automaticamente per controller, visori VR (sguardo fisso/messa a fuoco) e input tramite mouse/tocco.</span><span class="sxs-lookup"><span data-stu-id="063a0-241">Pointers are by default automatically configured for controllers, headsets (gaze / focus) and mouse / touch input.</span></span>

<span data-ttu-id="063a0-242">I puntatori possono anche essere visualizzati all'interno della scena attiva usando uno dei numerosi componenti line forniti da Mixed Reality Toolkit o uno dei propri se implementano l'interfaccia IMixedRealityPointer di MRTK.</span><span class="sxs-lookup"><span data-stu-id="063a0-242">Pointers can also be visualized within the active scene using one of the many line components provided by the Mixed Reality Toolkit, or any of your own if they implement the MRTK IMixedRealityPointer interface.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_InputPointerProfile.png" width="650px" alt="Input Pointer Profile" style="display:block;">

- <span data-ttu-id="063a0-243">Extent di puntamento: determina l'extent di puntamento globale per tutti i puntatori, incluso lo sguardo fisso.</span><span class="sxs-lookup"><span data-stu-id="063a0-243">Pointing Extent: Determines the global pointing extent for all pointers, including gaze.</span></span>
- <span data-ttu-id="063a0-244">Raycast Layer Masks (Maschera livello raycast di puntamento): determina su quali puntatori di livelli verrà esere il raycast.</span><span class="sxs-lookup"><span data-stu-id="063a0-244">Pointing Raycast Layer Masks: Determines which layers pointers will raycast against.</span></span>
- <span data-ttu-id="063a0-245">Debug dei raggi di puntamento di disegno: un helper di debug per la visualizzazione dei raggi usati per il raycasting.</span><span class="sxs-lookup"><span data-stu-id="063a0-245">Debug Draw Pointing Rays: A debug helper for visualizing the rays used for raycasting.</span></span>
- <span data-ttu-id="063a0-246">Eseguire il debug dei colori dei raggi di disegno: set di colori da usare per la visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="063a0-246">Debug Draw Pointing Rays Colors: A set of colors to use for visualizing.</span></span>
- <span data-ttu-id="063a0-247">Prefab cursore sguardo fisso: consente di specificare facilmente un cursore di sguardo fisso globale per qualsiasi scena.</span><span class="sxs-lookup"><span data-stu-id="063a0-247">Gaze cursor prefab: Makes it easy to specify a global gaze cursor for any scene.</span></span>

<span data-ttu-id="063a0-248">È presente un pulsante helper aggiuntivo per passare rapidamente al provider di sguardo fisso per eseguire l'override di alcuni valori specifici per Sguardo fisso, se necessario.</span><span class="sxs-lookup"><span data-stu-id="063a0-248">There's an additional helper button to quickly jump to the Gaze Provider to override some specific values for Gaze if needed.</span></span>

---
<a name="gestures"></a>

## <a name="gestures-configuration"></a><span data-ttu-id="063a0-249">Configurazione dei movimenti</span><span class="sxs-lookup"><span data-stu-id="063a0-249">Gestures configuration</span></span>

<span data-ttu-id="063a0-250">I movimenti sono un'implementazione specifica del sistema che consente di assegnare azioni di input ai vari metodi di input "Movimento" forniti da vari SDK (ad esempio HoloLens).</span><span class="sxs-lookup"><span data-stu-id="063a0-250">Gestures are a system specific implementation allowing you to assign input actions to the various "Gesture" input methods provided by various SDKs (e.g. HoloLens).</span></span>

> [!NOTE]
> <span data-ttu-id="063a0-251">L'implementazione corrente di Gestures è solo per HoloLens e verrà migliorata per altri sistemi, perché verranno aggiunti al Toolkit in futuro (nessuna data ancora).</span><span class="sxs-lookup"><span data-stu-id="063a0-251">The current Gestures implementation is for the HoloLens only and will be enhanced for other systems as they are added to the Toolkit in the future (no dates yet).</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_GesturesProfile.png" width="650px" alt="Gesture configuration" style="display:block;">

---
<a name="speech"></a>

## <a name="speech-commands"></a><span data-ttu-id="063a0-252">Comandi vocali</span><span class="sxs-lookup"><span data-stu-id="063a0-252">Speech commands</span></span>

<span data-ttu-id="063a0-253">Analogamente ai movimenti, alcune piattaforme di runtime forniscono anche funzionalità intelligenti di Riconoscimento vocale con la possibilità di generare comandi che possono essere ricevuti da un progetto Unity.</span><span class="sxs-lookup"><span data-stu-id="063a0-253">Like gestures, some runtime platforms also provide intelligent "Speech to Text" functionality with the ability to generate commands that can be received by a Unity project.</span></span> <span data-ttu-id="063a0-254">Questo profilo di configurazione consente di configurare quanto segue:</span><span class="sxs-lookup"><span data-stu-id="063a0-254">This configuration profile allows you to configure the following:</span></span>

1. <span data-ttu-id="063a0-255">Impostazioni generali: "Comportamento di avvio" impostato su Avvio automatico o Avvio manuale determina se inizializzare KeywordRecognizer all'avvio del sistema di input o consentire al progetto di decidere quando inizializzare KeywordRecognizer.</span><span class="sxs-lookup"><span data-stu-id="063a0-255">General Settings - "Start Behavior" set to Auto Start or Manual Start determines whether to initialize KeywordRecognizer at input system startup or let the project decide when to initialize the KeywordRecognizer.</span></span> <span data-ttu-id="063a0-256">Il "livello di attendibilità del riconoscimento" viene usato per inizializzare [l'API KeywordRecognizer di Unity](https://docs.unity3d.com/ScriptReference/Windows.Speech.KeywordRecognizer-ctor.html)</span><span class="sxs-lookup"><span data-stu-id="063a0-256">"Recognition Confidence Level" is used to initialize Unity's [KeywordRecognizer API](https://docs.unity3d.com/ScriptReference/Windows.Speech.KeywordRecognizer-ctor.html)</span></span>
2. <span data-ttu-id="063a0-257">Comandi vocali: registra le "parole" e le converte in azioni di input che possono essere ricevute dal progetto.</span><span class="sxs-lookup"><span data-stu-id="063a0-257">Speech Commands - Registers "words" and translates them in to input actions that can be received by your project.</span></span> <span data-ttu-id="063a0-258">Possono anche essere collegati alle azioni della tastiera, se necessario.</span><span class="sxs-lookup"><span data-stu-id="063a0-258">They can also be attached to keyboard actions if required.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="063a0-259">Il sistema attualmente supporta il riconoscimento vocale solo in caso di esecuzione su piattaforme Windows 10, ad esempio HoloLens e Windows 10 Desktop, e verrà migliorato per altri sistemi, perché verranno aggiunti a MRTK in futuro (nessuna data ancora).</span><span class="sxs-lookup"><span data-stu-id="063a0-259">The system currently only supports speech when running on Windows 10 platforms, e.g. HoloLens and Windows 10 desktop and will be enhanced for other systems as they are added to MRTK in the future (no dates yet).</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_SpeechCommandsProfile.png" width="650px" alt="Configuration Profile screens" style="display:block;">

---
<a name="mapping"></a>

## <a name="controller-mapping-configuration"></a><span data-ttu-id="063a0-260">Configurazione del mapping del controller</span><span class="sxs-lookup"><span data-stu-id="063a0-260">Controller mapping configuration</span></span>

<span data-ttu-id="063a0-261">Una delle schermate di configurazione principali per Mixed Reality Toolkit è la possibilità di configurare ed eseguire il mapping dei vari tipi di controller che possono essere utilizzati dal progetto.</span><span class="sxs-lookup"><span data-stu-id="063a0-261">One of the core configuration screens for the Mixed Reality Toolkit is the ability to configure and map the various types of controllers that can be utilized by your project.</span></span>

<span data-ttu-id="063a0-262">La schermata di configurazione seguente consente di configurare uno dei controller attualmente riconosciuti dal toolkit.</span><span class="sxs-lookup"><span data-stu-id="063a0-262">The configuration screen below allows you to configure any of the controllers currently recognized by the toolkit.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_ControllerMappingProfile.png" width="650px" alt="Controller Mapping" style="display:block;">

<span data-ttu-id="063a0-263">MRTK fornisce una configurazione predefinita per i controller/sistemi seguenti:</span><span class="sxs-lookup"><span data-stu-id="063a0-263">The MRTK provides a default configuration for the following controllers / systems:</span></span>

- <span data-ttu-id="063a0-264">Mouse (incluso il supporto del mouse spaziale 3D)</span><span class="sxs-lookup"><span data-stu-id="063a0-264">Mouse (including 3D spatial mouse support)</span></span>
- <span data-ttu-id="063a0-265">Touch screen</span><span class="sxs-lookup"><span data-stu-id="063a0-265">Touch Screen</span></span>
- <span data-ttu-id="063a0-266">Controller Xbox</span><span class="sxs-lookup"><span data-stu-id="063a0-266">Xbox controllers</span></span>
- <span data-ttu-id="063a0-267">controller Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="063a0-267">Windows Mixed Reality controllers</span></span>
- <span data-ttu-id="063a0-268">Movimenti di HoloLens</span><span class="sxs-lookup"><span data-stu-id="063a0-268">HoloLens Gestures</span></span>
- <span data-ttu-id="063a0-269">CONTROLLER DELLA RETE WAND DI VIVE</span><span class="sxs-lookup"><span data-stu-id="063a0-269">HTC Vive wand controllers</span></span>
- <span data-ttu-id="063a0-270">Controller Oculus Touch</span><span class="sxs-lookup"><span data-stu-id="063a0-270">Oculus Touch controllers</span></span>
- <span data-ttu-id="063a0-271">Controller remoto Oculus</span><span class="sxs-lookup"><span data-stu-id="063a0-271">Oculus Remote controller</span></span>
- <span data-ttu-id="063a0-272">Dispositivi OpenVR generici (solo utenti avanzati)</span><span class="sxs-lookup"><span data-stu-id="063a0-272">Generic OpenVR devices (advanced users only)</span></span>

<span data-ttu-id="063a0-273">Facendo clic sull'immagine per uno dei sistemi controller predefiniti è possibile configurare una singola azione di input per tutti gli input corrispondenti, ad esempio, vedere la schermata di configurazione del controller Oculus Touch riportata di seguito:</span><span class="sxs-lookup"><span data-stu-id="063a0-273">Clicking on the Image for any of the pre-built controller systems allows you to configure a single input action for all its corresponding inputs, for example, see the Oculus Touch controller configuration screen below:</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_WindowsMixedRealityControllerConfigScreen.png" width="650px" alt="Controller config screen" style="display:block;">

<span data-ttu-id="063a0-274">È disponibile anche una schermata avanzata per la configurazione di altri controller di input OpenVR o Unity non identificati in precedenza.</span><span class="sxs-lookup"><span data-stu-id="063a0-274">There is also an advanced screen for configuring other OpenVR or Unity input controllers that are not identified above.</span></span>

---
<a name="visualization"></a>

## <a name="controller-visualization-settings"></a><span data-ttu-id="063a0-275">Impostazioni di visualizzazione del controller</span><span class="sxs-lookup"><span data-stu-id="063a0-275">Controller visualization settings</span></span>

<span data-ttu-id="063a0-276">Oltre al mapping del controller, viene fornito un profilo di configurazione separato per personalizzare il modo in cui i controller vengono presentati all'interno delle scene.</span><span class="sxs-lookup"><span data-stu-id="063a0-276">In addition to the controller mapping, a separate configuration profile is provided to customize how your controllers are presented within your scenes.</span></span>

<span data-ttu-id="063a0-277">Può essere configurata a livello "globale" (tutte le istanze di un controller per una mano specifica) o specifica per un singolo tipo di controller/mano.</span><span class="sxs-lookup"><span data-stu-id="063a0-277">This can be configured at a "Global" (all instances of a controller for a specific hand) or specific to an individual controller type / hand.</span></span>

<span data-ttu-id="063a0-278">MRTK supporta anche modelli di controller SDK nativi per Windows Mixed Reality e OpenVR.</span><span class="sxs-lookup"><span data-stu-id="063a0-278">The MRTK also supports native SDK controller models for Windows Mixed Reality and OpenVR.</span></span> <span data-ttu-id="063a0-279">Questi vengono caricati come GameObject nella scena e posizionati usando il monitoraggio del controller della piattaforma.</span><span class="sxs-lookup"><span data-stu-id="063a0-279">These are loaded as GameObjects in your scene and positioned using the platform's controller tracking.</span></span>

<span data-ttu-id="063a0-280">Se la rappresentazione del controller nella scena deve essere offset dalla posizione fisica del controller, è sufficiente impostare tale offset rispetto al prefab del modello controller (ad esempio, impostando la posizione di trasformazione del prefab controller con una posizione di offset).</span><span class="sxs-lookup"><span data-stu-id="063a0-280">If your controller representation in the scene needs to be offset from the physical controller position, then simply set that offset against the controller model's prefab (e.g. setting the transform position of the controller prefab with an offset position).</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_ControllerVisualizationProfile.png" width="650px" alt="Visualization profile" style="display:block;">

<a name="editor-utilities"></a>

## <a name="editor-utilities"></a><span data-ttu-id="063a0-281">Utilità dell'editor</span><span class="sxs-lookup"><span data-stu-id="063a0-281">Editor utilities</span></span>

<span data-ttu-id="063a0-282">Le utilità seguenti funzionano solo nell'editor e sono utili per migliorare la produttività di sviluppo.</span><span class="sxs-lookup"><span data-stu-id="063a0-282">The following utilities work only in the editor and are useful to improve development productivity.</span></span>

![Utilità di configurazione dell'editor MRTK](../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_EditorConfiguration.png)

### <a name="service-inspectors"></a><span data-ttu-id="063a0-284">Controlli dei servizi</span><span class="sxs-lookup"><span data-stu-id="063a0-284">Service inspectors</span></span>

<span data-ttu-id="063a0-285">I controlli dei servizi sono una funzionalità solo editor che genera oggetti nella scena che rappresentano i servizi attivi.</span><span class="sxs-lookup"><span data-stu-id="063a0-285">Service Inspectors are an editor-only feature that generates in-scene objects representing active services.</span></span> <span data-ttu-id="063a0-286">Selezionando questi oggetti vengono visualizzati controlli che offrono collegamenti alla documentazione, controllo sulle visualizzazioni dell'editor e informazioni dettagliate sullo stato del servizio.</span><span class="sxs-lookup"><span data-stu-id="063a0-286">Selecting these objects displays inspectors which offer documentation links, control over editor visualizations and insight into the state of the service.</span></span>

<img src="../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_ServiceInspectors.PNG" width="350px" alt="Service Inspectors" style="display:block;">

<span data-ttu-id="063a0-287">È possibile abilitare i controlli dei servizi selezionando *Use Service Inspectors* (Usa controlli servizio) in Editor Settings *(Impostazioni editor)* nel profilo di configurazione.</span><span class="sxs-lookup"><span data-stu-id="063a0-287">You can enable service inspectors by checking *Use Service Inspectors* under *Editor Settings* in the Configuration Profile.</span></span>

### <a name="depth-buffer-renderer"></a><span data-ttu-id="063a0-288">Renderer del buffer di profondità</span><span class="sxs-lookup"><span data-stu-id="063a0-288">Depth buffer renderer</span></span>

<span data-ttu-id="063a0-289">La condivisione del buffer di profondità con alcune piattaforme di realtà mista può migliorare [la stabilizzazione dell'ologramma.](../performance/hologram-stabilization.md)</span><span class="sxs-lookup"><span data-stu-id="063a0-289">Sharing the depth buffer with some mixed reality platforms can improve [hologram stabilization](../performance/hologram-stabilization.md).</span></span> <span data-ttu-id="063a0-290">Ad esempio, la piattaforma Windows Mixed Reality può modificare la scena di cui è stato eseguito il rendering per pixel per rendere conto dei movimenti della testa durante il tempo necessario per il rendering di un fotogramma.</span><span class="sxs-lookup"><span data-stu-id="063a0-290">For example, the Windows Mixed Reality platform can modify the rendered scene per-pixel to account for subtle head movements during the time it took to render a frame.</span></span> <span data-ttu-id="063a0-291">Tuttavia, queste tecniche richiedono buffer di profondità con dati accurati per sapere dove e quanto è distante la geometria dall'utente.</span><span class="sxs-lookup"><span data-stu-id="063a0-291">However, these techniques require depth buffers with accurate data to know where and how far geometry is from the user.</span></span>

<span data-ttu-id="063a0-292">Per assicurarsi che una scena eserciti il rendering di tutti i dati necessari nel buffer di profondità, gli sviluppatori possono attivare o disattivare la funzionalità *Buffer* profondità di rendering in *Impostazioni editor* nel profilo di configurazione.</span><span class="sxs-lookup"><span data-stu-id="063a0-292">To ensure a scene renders all necessary data to the depth buffer, developers can toggle the *Render Depth Buffer* feature under *Editor Settings* in the Configuration Profile.</span></span> <span data-ttu-id="063a0-293">In questo modo il buffer di profondità corrente verrà visualizzato come colore per la visualizzazione della scena applicando un effetto di post-elaborazione, [`DepthBufferRenderer`](xref:Microsoft.MixedReality.Toolkit.Rendering.DepthBufferRenderer) , alla fotocamera principale.</span><span class="sxs-lookup"><span data-stu-id="063a0-293">This will take the current depth buffer and render it as color to the scene view by applying a post-processing effect, [`DepthBufferRenderer`](xref:Microsoft.MixedReality.Toolkit.Rendering.DepthBufferRenderer), to the main camera.</span></span>

<span data-ttu-id="063a0-294">![Utilità buffer di profondità di rendering Il cilindro blu nella scena ha un materiale con ](../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_DepthBufferExample.gif)
 <sup>ZWrite disattivato,</sup> quindi non vengono scritti dati di profondità</span><span class="sxs-lookup"><span data-stu-id="063a0-294">![Render Depth Buffer Utility](../features/images/mixed-reality-toolkit-configuration-profile-screens/MRTK_DepthBufferExample.gif)
<sup>The blue cylinder in the scene has a material with ZWrite off so no depth data is written</sup></span></span>

## <a name="changing-profiles-at-runtime"></a><span data-ttu-id="063a0-295">Modifica dei profili in fase di esecuzione</span><span class="sxs-lookup"><span data-stu-id="063a0-295">Changing profiles at runtime</span></span>

<span data-ttu-id="063a0-296">È possibile aggiornare i profili in fase di esecuzione e in genere esistono due scenari e momenti diversi in cui ciò risulta utile:</span><span class="sxs-lookup"><span data-stu-id="063a0-296">It is possible to update profiles at runtime, and there are generally two different scenarios and times in which in this is helpful:</span></span>

1. <span data-ttu-id="063a0-297">Pre-opzione del profilo di inizializzazione **MRTK:** all'avvio, prima che MRTK venga inizializzato e il profilo diventi attivo, sostituendo il profilo non ancora in uso per abilitare o disabilitare funzionalità diverse in base alle funzionalità del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="063a0-297">**Pre MRTK initialization profile switch**: At startup, before the MRTK is initialized and profile becomes active, replacing the not-yet-in-use profile to enable/disable different features based on the device capabilities.</span></span> <span data-ttu-id="063a0-298">Ad esempio, se l'esperienza è in esecuzione nella realtà virtuale che non dispone di hardware di mapping spaziale, probabilmente non ha senso avere un componente di mapping spaziale abilitato.</span><span class="sxs-lookup"><span data-stu-id="063a0-298">For example, if the experience is running in VR that doesn't have spatial mapping hardware it probably doesn't make sense to have spatial mapping component enabled.</span></span>
1. <span data-ttu-id="063a0-299">**Cambio di profilo** attivo: dopo l'avvio, dopo l'inizializzazione di MRTK e l'attivazione di un profilo, lo scambio del profilo attualmente in uso per modificare il comportamento di determinate funzionalità.</span><span class="sxs-lookup"><span data-stu-id="063a0-299">**Active profile switch**: After startup, after the MRTK is initialized and a profile has become active, swapping the profile currently in use to change the way certain features behave.</span></span> <span data-ttu-id="063a0-300">Ad esempio, potrebbe esserci un'esperienza secondaria specifica nell'applicazione che vuole rimuovere completamente i puntatori a mano da lontano.</span><span class="sxs-lookup"><span data-stu-id="063a0-300">For example, there may be a specific sub-experience in the application that wants far hand pointers completely removed.</span></span>

### <a name="pre-mrtk-initialization-profile-switch"></a><span data-ttu-id="063a0-301">Opzione del profilo di inizializzazione di MRTK precedente</span><span class="sxs-lookup"><span data-stu-id="063a0-301">Pre MRTK initialization profile switch</span></span>

<span data-ttu-id="063a0-302">Questa operazione può essere eseguita collegando un MonoBehaviour (esempio seguente) che viene eseguito prima dell'inizializzazione di MRTK (ad esempio, Awake()).</span><span class="sxs-lookup"><span data-stu-id="063a0-302">This can be accomplished by attaching a MonoBehaviour (example below) which runs before MRTK initialization (i.e. Awake()).</span></span> <span data-ttu-id="063a0-303">Si noti che lo script (ad esempio, la chiamata a ) deve essere eseguito prima dello script, operazione che può essere ottenuta impostando le `SetProfileBeforeInitialization` `MixedRealityToolkit` impostazioni [dell'ordine di esecuzione dello script](https://docs.unity3d.com/Manual/class-MonoManager.html).</span><span class="sxs-lookup"><span data-stu-id="063a0-303">Note the script (i.e. call to `SetProfileBeforeInitialization`) have to be executed earlier than the `MixedRealityToolkit` script, which can be achieved by setting [Script Execution Order settings](https://docs.unity3d.com/Manual/class-MonoManager.html).</span></span>

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

<span data-ttu-id="063a0-304">Invece di "profileToUse", è possibile avere un set arbitrario di profili che si applicano a piattaforme specifiche (ad esempio, uno per HoloLens 1, uno per la realtà virtuale, uno per HoloLens 2 e così via).</span><span class="sxs-lookup"><span data-stu-id="063a0-304">Instead of "profileToUse", it's possible to have some arbitrary set of profiles which apply to specific platforms (for example, one for HoloLens 1, one for VR, one for HoloLens 2, etc).</span></span> <span data-ttu-id="063a0-305">È possibile usare vari altri indicatori (ad esempio , o se la fotocamera è opaca/trasparente) per determinare il profilo https://docs.unity3d.com/ScriptReference/SystemInfo.html da caricare.</span><span class="sxs-lookup"><span data-stu-id="063a0-305">It's possible to use various other indicators (e.g. https://docs.unity3d.com/ScriptReference/SystemInfo.html, or whether or not the camera is opaque/transparent), to figure out which profile to load.</span></span>

### <a name="active-profile-switch"></a><span data-ttu-id="063a0-306">Opzione del profilo attivo</span><span class="sxs-lookup"><span data-stu-id="063a0-306">Active profile switch</span></span>

<span data-ttu-id="063a0-307">A tale scopo, impostare la `MixedRealityToolkit.Instance.ActiveProfile` proprietà su un nuovo profilo sostituendo il profilo attivo.</span><span class="sxs-lookup"><span data-stu-id="063a0-307">This can be accomplished by setting the `MixedRealityToolkit.Instance.ActiveProfile` property to a new profile replacing the active profile.</span></span>

```csharp
MixedRealityToolkit.Instance.ActiveProfile = profileToUse;
```

<span data-ttu-id="063a0-308">Si noti che quando si imposta durante il runtime, l'eliminazione dei servizi attualmente in esecuzione verrà eseguita dopo l'ultimo LateUpdate() di tutti i servizi e la creazione di istanze e l'inizializzazione dei servizi associati al nuovo profilo verranno eseguite prima del primo Update() di tutti i `ActiveProfile` servizi.</span><span class="sxs-lookup"><span data-stu-id="063a0-308">Note when setting `ActiveProfile` during runtime, the destroy of the currently running services will happen after the last LateUpdate() of all services, and the instantiation and initialization of the services associated with the new profile will happen before the first Update() of all services.</span></span>

<span data-ttu-id="063a0-309">Durante questo processo può verificarsi un'esitazione notevole dell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="063a0-309">A noticeable application hesitation may occur during this process.</span></span> <span data-ttu-id="063a0-310">Inoltre, qualsiasi script con priorità più alta rispetto allo `MixedRealityToolkit` script può immettere il relativo aggiornamento prima che il nuovo profilo sia configurato correttamente.</span><span class="sxs-lookup"><span data-stu-id="063a0-310">Also any script with higher priority than the `MixedRealityToolkit` script can enter its Update before the new profile is properly setup.</span></span> <span data-ttu-id="063a0-311">Per [altre informazioni sulla priorità degli script,](https://docs.unity3d.com/Manual/class-MonoManager.html) vedere Impostazioni dell'ordine di esecuzione degli script.</span><span class="sxs-lookup"><span data-stu-id="063a0-311">See [Script Execution Order settings](https://docs.unity3d.com/Manual/class-MonoManager.html) for more information on script priority.</span></span>

<span data-ttu-id="063a0-312">Nel processo di cambio profilo la fotocamera dell'interfaccia utente esistente rimarrà invariata, assicurando che i componenti dell'interfaccia utente di Unity che richiedono canvas funzionino ancora dopo il passaggio.</span><span class="sxs-lookup"><span data-stu-id="063a0-312">In the profile switching process the existing UI camera will remain unchanged, ensuring Unity UI components that require canvas still work after the switch.</span></span>

## <a name="see-also"></a><span data-ttu-id="063a0-313">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="063a0-313">See also</span></span>

- [<span data-ttu-id="063a0-314">Stabilizzazione dell'ologramma</span><span class="sxs-lookup"><span data-stu-id="063a0-314">Hologram Stabilization</span></span>](../performance/hologram-stabilization.md)
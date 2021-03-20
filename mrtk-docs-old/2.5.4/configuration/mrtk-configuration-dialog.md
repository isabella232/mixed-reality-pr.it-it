---
title: MRTK_Configuration_Dialog
description: Configurare MRTK nel progetto Unity
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, Unity
ms.openlocfilehash: 74c7f411f0be5ac4ecc2d70767335fb3a20ce8f4
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2021
ms.locfileid: "104682184"
---
# <a name="mrtk-project-configuration-dialog"></a><span data-ttu-id="8f7a9-104">Finestra di dialogo di configurazione del progetto MRTK</span><span class="sxs-lookup"><span data-stu-id="8f7a9-104">MRTK project configuration dialog</span></span>

<span data-ttu-id="8f7a9-105">La finestra di dialogo di configurazione MRTK viene visualizzata quando Unity carica un progetto ed è determinato che una o più opzioni di configurazione richiedono l'attenzione dello sviluppatore.</span><span class="sxs-lookup"><span data-stu-id="8f7a9-105">The MRTK configuration dialog is displayed when Unity loads a project and it is determined that one or more configuration options needs the attention of the developer.</span></span>

![Applica in seguito Ignora](../features/images/configuration-dialog/ConfigurationDialogHeader.png)

<span data-ttu-id="8f7a9-107">Per applicare le modifiche, fare clic sul pulsante **applica** .</span><span class="sxs-lookup"><span data-stu-id="8f7a9-107">To apply the changes, click the **Apply** button.</span></span> <span data-ttu-id="8f7a9-108">Il pulsante **più avanti** rinvia le modifiche finché il progetto non viene ricaricato in un momento successivo.</span><span class="sxs-lookup"><span data-stu-id="8f7a9-108">The **Later** button will defer the changes until the project is reloaded at a future time.</span></span>

> [!NOTE]
> <span data-ttu-id="8f7a9-109">Se una o più delle impostazioni consigliate non sono state controllate, verrà visualizzata nuovamente la finestra di dialogo di configurazione.</span><span class="sxs-lookup"><span data-stu-id="8f7a9-109">The configuration dialog will reappear if one or more of the recommended settings is left unchecked.</span></span> <span data-ttu-id="8f7a9-110">Per evitare che ciò accada, applicare le opzioni desiderate, quindi riavviare la finestra di dialogo tramite le utilità del **Toolkit di realtà mista**  >    >  **configurare il progetto Unity** e fare clic su **Ignora**.</span><span class="sxs-lookup"><span data-stu-id="8f7a9-110">To prevent this from occurring, apply the desired options, then relaunch the dialog via  **Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project** and click **Ignore**.</span></span> <span data-ttu-id="8f7a9-111">In questo modo si impedisce la visualizzazione automatica della finestra di dialogo di configurazione.</span><span class="sxs-lookup"><span data-stu-id="8f7a9-111">This will prevent the configuration dialog from reappearing automatically.</span></span>

## <a name="common-settings"></a><span data-ttu-id="8f7a9-112">Impostazioni comuni</span><span class="sxs-lookup"><span data-stu-id="8f7a9-112">Common settings</span></span>

<span data-ttu-id="8f7a9-113">Tutte le destinazioni di compilazione condividono una raccolta di opzioni comuni.</span><span class="sxs-lookup"><span data-stu-id="8f7a9-113">All build targets share a collection of common options.</span></span>

![Impostazioni comuni](../features/images/configuration-dialog/ConfigurationDialogCommonSettings.png)

### <a name="force-text-asset-serialization-and-enable-visible-meta-files"></a><span data-ttu-id="8f7a9-115">Forza la serializzazione degli asset di testo e Abilita i metadati visibili</span><span class="sxs-lookup"><span data-stu-id="8f7a9-115">Force text asset serialization and Enable visible meta files</span></span>

<span data-ttu-id="8f7a9-116">Queste impostazioni consentono di semplificare l'uso dei progetti Unity e dei sistemi di controllo del codice sorgente (ad esempio, git).</span><span class="sxs-lookup"><span data-stu-id="8f7a9-116">These settings help simplify working with Unity projects and source control systems (ex: Git).</span></span>

### <a name="enable-vr-supported"></a><span data-ttu-id="8f7a9-117">Abilitazione di VR supportata</span><span class="sxs-lookup"><span data-stu-id="8f7a9-117">Enable VR supported</span></span>

<span data-ttu-id="8f7a9-118">**Unity 2018**</span><span class="sxs-lookup"><span data-stu-id="8f7a9-118">**Unity 2018**</span></span>

<span data-ttu-id="8f7a9-119">Configura le opzioni Virtual Reality supported e Virtual Reality SDK in **Impostazioni lettore**  >  **XR impostazioni**.</span><span class="sxs-lookup"><span data-stu-id="8f7a9-119">Configures the Virtual Reality Supported and Virtual Reality SDK options in **Player Settings** > **XR Settings**.</span></span>

### <a name="set-single-pass-instanced-rendering-path"></a><span data-ttu-id="8f7a9-120">Imposta il percorso di rendering con istanza Single Pass</span><span class="sxs-lookup"><span data-stu-id="8f7a9-120">Set Single Pass Instanced rendering path</span></span>

<span data-ttu-id="8f7a9-121">Configura le impostazioni del **lettore impostazioni**  >  **XR**  >  **modalità di rendering stereo** per **singolo passaggio istanza**.</span><span class="sxs-lookup"><span data-stu-id="8f7a9-121">Configures the **Player Settings** > **XR Settings** > **Stereo Rendering Mode** to **Single Pass Instanced**.</span></span>

### <a name="set-default-spatial-awareness-layer"></a><span data-ttu-id="8f7a9-122">Imposta livello di riconoscimento spaziale predefinito</span><span class="sxs-lookup"><span data-stu-id="8f7a9-122">Set default Spatial Awareness layer</span></span>

<span data-ttu-id="8f7a9-123">Registra la consapevolezza spaziale come livello 31 per consentire una configurazione semplice e coerente delle opzioni di Raycast e fisica.</span><span class="sxs-lookup"><span data-stu-id="8f7a9-123">Registers Spatial Awareness as layer 31 to enable easy and consistent configuration of raycast and physics options.</span></span>

### <a name="audio-spatializer"></a><span data-ttu-id="8f7a9-124">Spatializer audio</span><span class="sxs-lookup"><span data-stu-id="8f7a9-124">Audio spatializer</span></span>

<span data-ttu-id="8f7a9-125">Spatializers audio sono i componenti che sbloccano la potenza del suono spaziale e dell'audio posizionale per rendere realmente immersive le esperienze di realtà miste.</span><span class="sxs-lookup"><span data-stu-id="8f7a9-125">Audio spatializers are the components that unlock the power of Spatial Sound and positional audio to make mixed reality experiences truly immersive.</span></span>

> [!NOTE]
> <span data-ttu-id="8f7a9-126">Se si imposta Spatializer audio su None, le funzionalità audio posizionali non vengono disabilitate.</span><span class="sxs-lookup"><span data-stu-id="8f7a9-126">Setting the audio spatializer to None will disable positional audio features.</span></span>

#### <a name="common-spatializers"></a><span data-ttu-id="8f7a9-127">Spatializers comuni</span><span class="sxs-lookup"><span data-stu-id="8f7a9-127">Common spatializers</span></span>

- <span data-ttu-id="8f7a9-128">Microsoft Spatializer</span><span class="sxs-lookup"><span data-stu-id="8f7a9-128">Microsoft Spatializer</span></span>

<span data-ttu-id="8f7a9-129">Microsoft ha fornito Spatializer che supporta l'utilizzo dell'accelerazione hardware in HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="8f7a9-129">Microsoft provided spatializer that supports utilization of hardware acceleration on HoloLens 2.</span></span>

<span data-ttu-id="8f7a9-130">Questo Spatializer è disponibile tramite [NuGet](https://www.nuget.org/packages/Microsoft.SpatialAudio.Spatializer.Unity/) e [GitHub](https://github.com/microsoft/spatialaudio-unity).</span><span class="sxs-lookup"><span data-stu-id="8f7a9-130">This spatializer is available via [NuGet](https://www.nuget.org/packages/Microsoft.SpatialAudio.Spatializer.Unity/) and [GitHub](https://github.com/microsoft/spatialaudio-unity).</span></span>

<span data-ttu-id="8f7a9-131">Per ulteriori informazioni su Microsoft Spatializer, vedere la [documentazione relativa al suono spaziale](https://docs.microsoft.com/windows/mixed-reality/spatial-sound-in-unity).</span><span class="sxs-lookup"><span data-stu-id="8f7a9-131">More details on Microsoft Spatializer can be found in the [Spatial Sound documentation](https://docs.microsoft.com/windows/mixed-reality/spatial-sound-in-unity).</span></span>

- <span data-ttu-id="8f7a9-132">MS HRTF Spatializer</span><span class="sxs-lookup"><span data-stu-id="8f7a9-132">MS HRTF Spatializer</span></span>

<span data-ttu-id="8f7a9-133">Microsoft Windows Spatializer fornito da Unity come parte della realtà mista di Windows e dei pacchetti della piattaforma Windows XR.</span><span class="sxs-lookup"><span data-stu-id="8f7a9-133">Microsoft Windows spatializer that is provided by Unity as part of the Windows Mixed Reality and Windows XR Platform packages.</span></span>

- <span data-ttu-id="8f7a9-134">Audio risonanza</span><span class="sxs-lookup"><span data-stu-id="8f7a9-134">Resonance Audio</span></span>

<span data-ttu-id="8f7a9-135">Spatializer multipiattaforma di Google fornito da Unity.</span><span class="sxs-lookup"><span data-stu-id="8f7a9-135">A cross platform spatializer from Google that is provided by Unity.</span></span>

<span data-ttu-id="8f7a9-136">Altre informazioni sono reperibili nel sito di [documentazione audio risonanza](https://resonance-audio.github.io/resonance-audio/develop/unity/getting-started) .</span><span class="sxs-lookup"><span data-stu-id="8f7a9-136">More information can be found on the [Resonance Audio documentation](https://resonance-audio.github.io/resonance-audio/develop/unity/getting-started) site.</span></span>

## <a name="universal-windows-platform-settings"></a><span data-ttu-id="8f7a9-137">Impostazioni piattaforma UWP (Universal Windows Platform)</span><span class="sxs-lookup"><span data-stu-id="8f7a9-137">Universal Windows Platform settings</span></span>

![Impostazioni UWP](../features/images/configuration-dialog/ConfigurationDialogUWPSettings.png)

### <a name="uwp-capabilities"></a><span data-ttu-id="8f7a9-139">Funzionalità UWP</span><span class="sxs-lookup"><span data-stu-id="8f7a9-139">UWP Capabilities</span></span>

<span data-ttu-id="8f7a9-140">Abilita funzionalità specifiche dell'applicazione per piattaforma UWP (Universal Windows Platform) applicazione.</span><span class="sxs-lookup"><span data-stu-id="8f7a9-140">Enables specific application capabilities for Universal Windows Platform application.</span></span> <span data-ttu-id="8f7a9-141">Queste funzionalità consentono alla piattaforma di informare e richiedere l'autorizzazione per abilitare funzionalità specifiche.</span><span class="sxs-lookup"><span data-stu-id="8f7a9-141">These capabilities enable the platform to inform and request permission to enable specific functionality.</span></span>

- <span data-ttu-id="8f7a9-142">Microfono</span><span class="sxs-lookup"><span data-stu-id="8f7a9-142">Microphone</span></span>

  <span data-ttu-id="8f7a9-143">Abilita l'acquisizione di suoni tramite il microfono.</span><span class="sxs-lookup"><span data-stu-id="8f7a9-143">Enables capturing sound via the microphone.</span></span>

- <span data-ttu-id="8f7a9-144">Client Internet</span><span class="sxs-lookup"><span data-stu-id="8f7a9-144">Internet Client</span></span>

  <span data-ttu-id="8f7a9-145">Abilita il supporto per l'accesso alle risorse su Internet.</span><span class="sxs-lookup"><span data-stu-id="8f7a9-145">Enables support for accessing resources on the internet.</span></span>

- <span data-ttu-id="8f7a9-146">Percezione spaziale</span><span class="sxs-lookup"><span data-stu-id="8f7a9-146">Spatial Perception</span></span>

  <span data-ttu-id="8f7a9-147">Abilita il supporto per l'uso dell'ambiente reale.</span><span class="sxs-lookup"><span data-stu-id="8f7a9-147">Enables support for using the real-world environment.</span></span>

- <span data-ttu-id="8f7a9-148">Occhio</span><span class="sxs-lookup"><span data-stu-id="8f7a9-148">Eye Gaze</span></span>

  <span data-ttu-id="8f7a9-149">**Unity 2019,3 e versioni successive**</span><span class="sxs-lookup"><span data-stu-id="8f7a9-149">**Unity 2019.3 and newer**</span></span>

  <span data-ttu-id="8f7a9-150">Abilita il supporto per tenere traccia degli sguardi dell'utente.</span><span class="sxs-lookup"><span data-stu-id="8f7a9-150">Enables support for tracking the user's eye gaze.</span></span>

### <a name="avoid-unity-playersettingsgraphicsjob-crash"></a><span data-ttu-id="8f7a9-151">Evitare l'arresto anomalo di Unity ' PlayerSettings. graphicsJob '</span><span class="sxs-lookup"><span data-stu-id="8f7a9-151">Avoid Unity 'PlayerSettings.graphicsJob' crash</span></span>

<span data-ttu-id="8f7a9-152">**Unity 2019,3 e versioni successive**</span><span class="sxs-lookup"><span data-stu-id="8f7a9-152">**Unity 2019.3 and newer**</span></span>

<span data-ttu-id="8f7a9-153">Nella versione più recente di Unity 2019, quando è abilitato "processi grafici", l'app si arresterà in modo anomalo quando viene distribuita in un HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="8f7a9-153">In the latest version of Unity 2019, when "Graphics Jobs" is enabled, the app will crash when deployed to a HoloLens 2.</span></span>
<span data-ttu-id="8f7a9-154">Questa impostazione è abilitata per impostazione predefinita in Unity. questo bug è disponibile (vedere il [bug Unity](https://issuetracker.unity3d.com/issues/enabling-graphics-jobs-in-2019-dot-3-x-results-in-a-crash-or-nothing-rendering-on-hololens-2)). per impostazione predefinita, lo strumento di configurazione imposta i processi grafici su' false ', consentendo così alle app distribuite in HoloLens 2 di non arrestarsi in modo anomalo.</span><span class="sxs-lookup"><span data-stu-id="8f7a9-154">This setting is enabled by default in Unity - while this bug exists (see [Unity bug](https://issuetracker.unity3d.com/issues/enabling-graphics-jobs-in-2019-dot-3-x-results-in-a-crash-or-nothing-rendering-on-hololens-2)), the configurator will default to setting Graphics Jobs to 'false' (thus allowing apps deployed to HoloLens 2 not to crash).</span></span>

## <a name="android-settings"></a><span data-ttu-id="8f7a9-155">Impostazioni Android</span><span class="sxs-lookup"><span data-stu-id="8f7a9-155">Android settings</span></span>

<span data-ttu-id="8f7a9-156">Impostazioni di configurazione per supportare le applicazioni AR nei dispositivi Android.</span><span class="sxs-lookup"><span data-stu-id="8f7a9-156">Configuration settings to support AR applications on Android powered devices.</span></span>

![Impostazioni Android](../features/images/configuration-dialog/ConfigurationDialogAndroidSettings.png)

### <a name="disable-multi-threaded-rendering"></a><span data-ttu-id="8f7a9-158">Disabilitare il rendering multithread</span><span class="sxs-lookup"><span data-stu-id="8f7a9-158">Disable Multi-Threaded Rendering</span></span>

<span data-ttu-id="8f7a9-159">Disabilita **le impostazioni del lettore**  >  **altre impostazioni**  >  di **rendering multithreading** come richiesto dal supporto AR di Android.</span><span class="sxs-lookup"><span data-stu-id="8f7a9-159">Disables **Player Settings** > **Other Settings** > **Multithreaded Rendering** as required by Android's AR support.</span></span>

### <a name="set-minimum-api-level"></a><span data-ttu-id="8f7a9-160">Imposta il livello API minimo</span><span class="sxs-lookup"><span data-stu-id="8f7a9-160">Set Minimum API Level</span></span>

<span data-ttu-id="8f7a9-161">Imposta il valore delle **impostazioni del lettore**  >  **altre impostazioni**  >  **livello API minimo** per applicare i requisiti del sistema operativo per le applicazioni AR.</span><span class="sxs-lookup"><span data-stu-id="8f7a9-161">Sets the value of **Player Settings** > **Other Settings** > **Minimum API Level** to enforce operating system requirements for AR applications.</span></span>

## <a name="ios-settings"></a><span data-ttu-id="8f7a9-162">Impostazioni iOS</span><span class="sxs-lookup"><span data-stu-id="8f7a9-162">iOS settings</span></span>

<span data-ttu-id="8f7a9-163">Impostazioni di configurazione per supportare le applicazioni AR nei dispositivi con tecnologia iOS.</span><span class="sxs-lookup"><span data-stu-id="8f7a9-163">Configuration settings to support AR applications on iOS powered devices.</span></span>

![Impostazioni iOS](../features/images/configuration-dialog/ConfigurationDialogiOSSettings.png)

### <a name="set-required-os-version"></a><span data-ttu-id="8f7a9-165">Imposta la versione richiesta del sistema operativo</span><span class="sxs-lookup"><span data-stu-id="8f7a9-165">Set Required OS Version</span></span>

<span data-ttu-id="8f7a9-166">Imposta il valore delle **impostazioni del lettore**  >  **altre impostazioni** di  >  **destinazione della versione minima di iOS** per applicare i requisiti del sistema operativo per le applicazioni AR.</span><span class="sxs-lookup"><span data-stu-id="8f7a9-166">Sets the value of **Player Settings** > **Other Settings** > **Target minimum iOS Version** to enforce operating system requirements for AR applications.</span></span>

### <a name="set-required-architecture"></a><span data-ttu-id="8f7a9-167">Imposta architettura necessaria</span><span class="sxs-lookup"><span data-stu-id="8f7a9-167">Set Required Architecture</span></span>

<span data-ttu-id="8f7a9-168">Imposta il valore dell'   >  architettura di **altre impostazioni** del lettore  >   per applicare i requisiti di piattaforma per le applicazioni AR.</span><span class="sxs-lookup"><span data-stu-id="8f7a9-168">Sets the value of **Player Settings** > **Other Settings** > **Architecture** to enforce platform requirements for AR applications.</span></span>

### <a name="set-camera-usage-descriptions"></a><span data-ttu-id="8f7a9-169">Imposta descrizioni utilizzo della fotocamera</span><span class="sxs-lookup"><span data-stu-id="8f7a9-169">Set Camera Usage Descriptions</span></span>

<span data-ttu-id="8f7a9-170">Imposta il valore di **Impostazioni lettore**  >  **altre impostazioni**  >  **Descrizione utilizzo fotocamera** usato per richiedere l'autorizzazione per l'uso della fotocamera del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="8f7a9-170">Sets the value of **Player Settings** > **Other Settings** > **Camera Usage Description** used to request permission to use the device's camera.</span></span>

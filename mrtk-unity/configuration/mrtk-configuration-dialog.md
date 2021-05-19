---
title: Finestra di dialogo di configurazione MRTK
description: Configurare MRTK nel progetto Unity
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realtà mista, sviluppo, MRTK, Unity
ms.openlocfilehash: ef326a4e4c9e34479cebacf3f3f575cd902ff24e
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144838"
---
# <a name="mrtk-project-configuration-dialog"></a><span data-ttu-id="b81a4-104">Finestra di dialogo di configurazione del progetto MRTK</span><span class="sxs-lookup"><span data-stu-id="b81a4-104">MRTK project configuration dialog</span></span>

<span data-ttu-id="b81a4-105">La finestra di dialogo di configurazione MRTK viene visualizzata quando Unity carica un progetto ed è determinato che una o più opzioni di configurazione devono essere attenzioni dello sviluppatore.</span><span class="sxs-lookup"><span data-stu-id="b81a4-105">The MRTK configuration dialog is displayed when Unity loads a project and it is determined that one or more configuration options needs the attention of the developer.</span></span>

![Applica in seguito Ignora](../features/images/configuration-dialog/ConfigurationDialogHeader.png)

<span data-ttu-id="b81a4-107">Per applicare le modifiche, fare clic **sul pulsante** Applica.</span><span class="sxs-lookup"><span data-stu-id="b81a4-107">To apply the changes, click the **Apply** button.</span></span> <span data-ttu-id="b81a4-108">Il **pulsante** In seguito posticiperà le modifiche fino a quando il progetto non verrà ricaricato in un momento futuro.</span><span class="sxs-lookup"><span data-stu-id="b81a4-108">The **Later** button will defer the changes until the project is reloaded at a future time.</span></span>

> [!NOTE]
> <span data-ttu-id="b81a4-109">La finestra di dialogo di configurazione verrà visualizzata di nuovo se una o più impostazioni consigliate non vengono deselezionate.</span><span class="sxs-lookup"><span data-stu-id="b81a4-109">The configuration dialog will reappear if one or more of the recommended settings is left unchecked.</span></span> <span data-ttu-id="b81a4-110">Per evitare questo problema, applicare le opzioni desiderate, quindi riavviare la finestra di dialogo tramite **Mixed Reality Toolkit** Utilities Configure Unity Project e  >    >   fare clic su **Ignora**.</span><span class="sxs-lookup"><span data-stu-id="b81a4-110">To prevent this from occurring, apply the desired options, then relaunch the dialog via  **Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project** and click **Ignore**.</span></span> <span data-ttu-id="b81a4-111">In questo modo la finestra di dialogo di configurazione non verrà visualizzata automaticamente.</span><span class="sxs-lookup"><span data-stu-id="b81a4-111">This will prevent the configuration dialog from reappearing automatically.</span></span>

## <a name="common-settings"></a><span data-ttu-id="b81a4-112">Impostazioni comuni</span><span class="sxs-lookup"><span data-stu-id="b81a4-112">Common settings</span></span>

<span data-ttu-id="b81a4-113">Tutte le destinazioni di compilazione condividono una raccolta di opzioni comuni.</span><span class="sxs-lookup"><span data-stu-id="b81a4-113">All build targets share a collection of common options.</span></span>

![Impostazioni comuni](../features/images/configuration-dialog/ConfigurationDialogCommonSettings.png)

### <a name="force-text-asset-serialization-and-enable-visible-meta-files"></a><span data-ttu-id="b81a4-115">Forzare la serializzazione degli asset di testo e abilitare i metafile visibili</span><span class="sxs-lookup"><span data-stu-id="b81a4-115">Force text asset serialization and Enable visible meta files</span></span>

<span data-ttu-id="b81a4-116">Queste impostazioni consentono di semplificare l'uso dei progetti Unity e dei sistemi di controllo del codice sorgente (ad esempio Git).</span><span class="sxs-lookup"><span data-stu-id="b81a4-116">These settings help simplify working with Unity projects and source control systems (ex: Git).</span></span>

### <a name="enable-vr-supported"></a><span data-ttu-id="b81a4-117">Abilitare la realtà virtuale supportata</span><span class="sxs-lookup"><span data-stu-id="b81a4-117">Enable VR supported</span></span>

<span data-ttu-id="b81a4-118">**Unity 2018**</span><span class="sxs-lookup"><span data-stu-id="b81a4-118">**Unity 2018**</span></span>

<span data-ttu-id="b81a4-119">Configura le opzioni Virtual Reality Supported e Virtual Reality SDK in **Player Settings**  >  XR Settings (Impostazioni **lettore XR Settings XR).**</span><span class="sxs-lookup"><span data-stu-id="b81a4-119">Configures the Virtual Reality Supported and Virtual Reality SDK options in **Player Settings** > **XR Settings**.</span></span>

### <a name="set-single-pass-instanced-rendering-path"></a><span data-ttu-id="b81a4-120">Impostare il percorso di rendering con istanza a passaggio singolo</span><span class="sxs-lookup"><span data-stu-id="b81a4-120">Set Single Pass Instanced rendering path</span></span>

<span data-ttu-id="b81a4-121">Configura le impostazioni **del lettore**  >  **XR Settings** Stereo Rendering  >  **Mode** su Single Pass **Instanced**.</span><span class="sxs-lookup"><span data-stu-id="b81a4-121">Configures the **Player Settings** > **XR Settings** > **Stereo Rendering Mode** to **Single Pass Instanced**.</span></span>

### <a name="set-default-spatial-awareness-layer"></a><span data-ttu-id="b81a4-122">Impostare il livello di consapevolezza spaziale predefinito</span><span class="sxs-lookup"><span data-stu-id="b81a4-122">Set default Spatial Awareness layer</span></span>

<span data-ttu-id="b81a4-123">Registra la consapevolezza spaziale come livello 31 per consentire la configurazione semplice e coerente delle opzioni di raycast e fisica.</span><span class="sxs-lookup"><span data-stu-id="b81a4-123">Registers Spatial Awareness as layer 31 to enable easy and consistent configuration of raycast and physics options.</span></span>

### <a name="audio-spatializer"></a><span data-ttu-id="b81a4-124">Spazializzatore audio</span><span class="sxs-lookup"><span data-stu-id="b81a4-124">Audio spatializer</span></span>

<span data-ttu-id="b81a4-125">Gli spazializzatori audio sono i componenti che sbloccano la potenza del suono spaziale e dell'audio posizionale per rendere realmente immersive le esperienze di realtà mista.</span><span class="sxs-lookup"><span data-stu-id="b81a4-125">Audio spatializers are the components that unlock the power of Spatial Sound and positional audio to make mixed reality experiences truly immersive.</span></span>

> [!NOTE]
> <span data-ttu-id="b81a4-126">L'impostazione dello spazializzatore audio su Nessuno disabilita le funzionalità audio posizionali.</span><span class="sxs-lookup"><span data-stu-id="b81a4-126">Setting the audio spatializer to None will disable positional audio features.</span></span>

#### <a name="common-spatializers"></a><span data-ttu-id="b81a4-127">Spazializzatori comuni</span><span class="sxs-lookup"><span data-stu-id="b81a4-127">Common spatializers</span></span>

- <span data-ttu-id="b81a4-128">Spazializzatore Microsoft</span><span class="sxs-lookup"><span data-stu-id="b81a4-128">Microsoft Spatializer</span></span>

<span data-ttu-id="b81a4-129">Microsoft ha fornito un spazializzatore che supporta l'utilizzo dell'accelerazione hardware HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="b81a4-129">Microsoft provided spatializer that supports utilization of hardware acceleration on HoloLens 2.</span></span>

<span data-ttu-id="b81a4-130">Questo spazializzatore è disponibile tramite [NuGet](https://www.nuget.org/packages/Microsoft.SpatialAudio.Spatializer.Unity/) e [GitHub.](https://github.com/microsoft/spatialaudio-unity)</span><span class="sxs-lookup"><span data-stu-id="b81a4-130">This spatializer is available via [NuGet](https://www.nuget.org/packages/Microsoft.SpatialAudio.Spatializer.Unity/) and [GitHub](https://github.com/microsoft/spatialaudio-unity).</span></span>

<span data-ttu-id="b81a4-131">Per altre informazioni su Microsoft Spatializer, vedere la documentazione [relativa al suono spaziale](/windows/mixed-reality/spatial-sound-in-unity).</span><span class="sxs-lookup"><span data-stu-id="b81a4-131">More details on Microsoft Spatializer can be found in the [Spatial Sound documentation](/windows/mixed-reality/spatial-sound-in-unity).</span></span>

- <span data-ttu-id="b81a4-132">Spazializzatore MS HRTF</span><span class="sxs-lookup"><span data-stu-id="b81a4-132">MS HRTF Spatializer</span></span>

<span data-ttu-id="b81a4-133">Spazializzatore di Microsoft Windows fornito da Unity come parte dei pacchetti Windows Mixed Reality e della piattaforma Windows XR.</span><span class="sxs-lookup"><span data-stu-id="b81a4-133">Microsoft Windows spatializer that is provided by Unity as part of the Windows Mixed Reality and Windows XR Platform packages.</span></span>

- <span data-ttu-id="b81a4-134">Audio di risonazione</span><span class="sxs-lookup"><span data-stu-id="b81a4-134">Resonance Audio</span></span>

<span data-ttu-id="b81a4-135">Spazializzatore multipiattaforma di Google fornito da Unity.</span><span class="sxs-lookup"><span data-stu-id="b81a4-135">A cross platform spatializer from Google that is provided by Unity.</span></span>

<span data-ttu-id="b81a4-136">Altre informazioni sono disponibili nel sito [della documentazione di Resonance Audio.](https://resonance-audio.github.io/resonance-audio/develop/unity/getting-started)</span><span class="sxs-lookup"><span data-stu-id="b81a4-136">More information can be found on the [Resonance Audio documentation](https://resonance-audio.github.io/resonance-audio/develop/unity/getting-started) site.</span></span>

## <a name="universal-windows-platform-settings"></a><span data-ttu-id="b81a4-137">piattaforma UWP (Universal Windows Platform) impostazioni</span><span class="sxs-lookup"><span data-stu-id="b81a4-137">Universal Windows Platform settings</span></span>

![Impostazioni UWP](../features/images/configuration-dialog/ConfigurationDialogUWPSettings.png)

### <a name="uwp-capabilities"></a><span data-ttu-id="b81a4-139">Funzionalità UWP</span><span class="sxs-lookup"><span data-stu-id="b81a4-139">UWP Capabilities</span></span>

<span data-ttu-id="b81a4-140">Abilita funzionalità specifiche dell'applicazione per piattaforma UWP (Universal Windows Platform)appalta.</span><span class="sxs-lookup"><span data-stu-id="b81a4-140">Enables specific application capabilities for Universal Windows Platform application.</span></span> <span data-ttu-id="b81a4-141">Queste funzionalità consentono alla piattaforma di informare e richiedere l'autorizzazione per abilitare funzionalità specifiche.</span><span class="sxs-lookup"><span data-stu-id="b81a4-141">These capabilities enable the platform to inform and request permission to enable specific functionality.</span></span>

- <span data-ttu-id="b81a4-142">Microfono</span><span class="sxs-lookup"><span data-stu-id="b81a4-142">Microphone</span></span>

  <span data-ttu-id="b81a4-143">Abilita l'acquisizione dell'audio tramite il microfono.</span><span class="sxs-lookup"><span data-stu-id="b81a4-143">Enables capturing sound via the microphone.</span></span>

- <span data-ttu-id="b81a4-144">Internet Client</span><span class="sxs-lookup"><span data-stu-id="b81a4-144">Internet Client</span></span>

  <span data-ttu-id="b81a4-145">Abilita il supporto per l'accesso alle risorse su Internet.</span><span class="sxs-lookup"><span data-stu-id="b81a4-145">Enables support for accessing resources on the internet.</span></span>

- <span data-ttu-id="b81a4-146">Percezione spaziale</span><span class="sxs-lookup"><span data-stu-id="b81a4-146">Spatial Perception</span></span>

  <span data-ttu-id="b81a4-147">Abilita il supporto per l'uso dell'ambiente reale.</span><span class="sxs-lookup"><span data-stu-id="b81a4-147">Enables support for using the real-world environment.</span></span>

- <span data-ttu-id="b81a4-148">Sguardo fisso</span><span class="sxs-lookup"><span data-stu-id="b81a4-148">Eye Gaze</span></span>

  <span data-ttu-id="b81a4-149">**Unity 2019.3 e versione più recente**</span><span class="sxs-lookup"><span data-stu-id="b81a4-149">**Unity 2019.3 and newer**</span></span>

  <span data-ttu-id="b81a4-150">Abilita il supporto per tenere traccia dello sguardo fisso dell'utente.</span><span class="sxs-lookup"><span data-stu-id="b81a4-150">Enables support for tracking the user's eye gaze.</span></span>

### <a name="avoid-unity-playersettingsgraphicsjob-crash"></a><span data-ttu-id="b81a4-151">Evitare l'arresto anomalo di 'PlayerSettings.graphicsJob' di Unity</span><span class="sxs-lookup"><span data-stu-id="b81a4-151">Avoid Unity 'PlayerSettings.graphicsJob' crash</span></span>

<span data-ttu-id="b81a4-152">**Unity 2019.3 e versione più recente**</span><span class="sxs-lookup"><span data-stu-id="b81a4-152">**Unity 2019.3 and newer**</span></span>

<span data-ttu-id="b81a4-153">Nella versione più recente di Unity 2019, quando è abilitato "Processi di grafica", l'app si arresta in modo anomalo quando viene distribuita in un HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="b81a4-153">In the latest version of Unity 2019, when "Graphics Jobs" is enabled, the app will crash when deployed to a HoloLens 2.</span></span>
<span data-ttu-id="b81a4-154">Questa impostazione è abilitata per impostazione predefinita in Unity. Anche se questo bug esiste (vedere il bug di [Unity),](https://issuetracker.unity3d.com/issues/enabling-graphics-jobs-in-2019-dot-3-x-results-in-a-crash-or-nothing-rendering-on-hololens-2)lo configuratore imposta per impostazione predefinita Processi grafici su "false", consentendo così alle app distribuite di HoloLens 2 di non bloccarsi.</span><span class="sxs-lookup"><span data-stu-id="b81a4-154">This setting is enabled by default in Unity - while this bug exists (see [Unity bug](https://issuetracker.unity3d.com/issues/enabling-graphics-jobs-in-2019-dot-3-x-results-in-a-crash-or-nothing-rendering-on-hololens-2)), the configurator will default to setting Graphics Jobs to 'false' (thus allowing apps deployed to HoloLens 2 not to crash).</span></span>

## <a name="android-settings"></a><span data-ttu-id="b81a4-155">Impostazioni Android</span><span class="sxs-lookup"><span data-stu-id="b81a4-155">Android settings</span></span>

<span data-ttu-id="b81a4-156">Impostazioni di configurazione per supportare le applicazioni AR nei dispositivi Android.</span><span class="sxs-lookup"><span data-stu-id="b81a4-156">Configuration settings to support AR applications on Android powered devices.</span></span>

![Impostazioni Android](../features/images/configuration-dialog/ConfigurationDialogAndroidSettings.png)

### <a name="disable-multi-threaded-rendering"></a><span data-ttu-id="b81a4-158">Disabilitare il rendering multi-thread</span><span class="sxs-lookup"><span data-stu-id="b81a4-158">Disable Multi-Threaded Rendering</span></span>

<span data-ttu-id="b81a4-159">Disabilita le impostazioni **del**  >  **lettore Altre impostazioni** Rendering  >  **multithreading** come richiesto dal supporto AR di Android.</span><span class="sxs-lookup"><span data-stu-id="b81a4-159">Disables **Player Settings** > **Other Settings** > **Multithreaded Rendering** as required by Android's AR support.</span></span>

### <a name="set-minimum-api-level"></a><span data-ttu-id="b81a4-160">Impostare il livello API minimo</span><span class="sxs-lookup"><span data-stu-id="b81a4-160">Set Minimum API Level</span></span>

<span data-ttu-id="b81a4-161">Imposta il valore di **Player Settings Other Settings** Minimum API Level per applicare i requisiti del sistema operativo per le applicazioni  >    >   AR.</span><span class="sxs-lookup"><span data-stu-id="b81a4-161">Sets the value of **Player Settings** > **Other Settings** > **Minimum API Level** to enforce operating system requirements for AR applications.</span></span>

## <a name="ios-settings"></a><span data-ttu-id="b81a4-162">Impostazioni iOS</span><span class="sxs-lookup"><span data-stu-id="b81a4-162">iOS settings</span></span>

<span data-ttu-id="b81a4-163">Impostazioni di configurazione per supportare le applicazioni AR nei dispositivi iOS.</span><span class="sxs-lookup"><span data-stu-id="b81a4-163">Configuration settings to support AR applications on iOS powered devices.</span></span>

![Impostazioni iOS](../features/images/configuration-dialog/ConfigurationDialogiOSSettings.png)

### <a name="set-required-os-version"></a><span data-ttu-id="b81a4-165">Impostare la versione del sistema operativo richiesta</span><span class="sxs-lookup"><span data-stu-id="b81a4-165">Set Required OS Version</span></span>

<span data-ttu-id="b81a4-166">Imposta il valore di **Player Settings Other Settings** Target minimum iOS Version per applicare i requisiti del sistema operativo per le applicazioni  >    >   AR.</span><span class="sxs-lookup"><span data-stu-id="b81a4-166">Sets the value of **Player Settings** > **Other Settings** > **Target minimum iOS Version** to enforce operating system requirements for AR applications.</span></span>

### <a name="set-required-architecture"></a><span data-ttu-id="b81a4-167">Impostare l'architettura richiesta</span><span class="sxs-lookup"><span data-stu-id="b81a4-167">Set Required Architecture</span></span>

<span data-ttu-id="b81a4-168">Imposta il valore di **Impostazioni lettore Altre**  >  **impostazioni**  >  **Architettura per** applicare i requisiti della piattaforma per le applicazioni ar.</span><span class="sxs-lookup"><span data-stu-id="b81a4-168">Sets the value of **Player Settings** > **Other Settings** > **Architecture** to enforce platform requirements for AR applications.</span></span>

### <a name="set-camera-usage-descriptions"></a><span data-ttu-id="b81a4-169">Impostare le descrizioni di utilizzo della fotocamera</span><span class="sxs-lookup"><span data-stu-id="b81a4-169">Set Camera Usage Descriptions</span></span>

<span data-ttu-id="b81a4-170">Imposta il valore di **Impostazioni lettore Altre impostazioni** Descrizione utilizzo fotocamera usata per richiedere  >    >   l'autorizzazione per l'uso della fotocamera del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="b81a4-170">Sets the value of **Player Settings** > **Other Settings** > **Camera Usage Description** used to request permission to use the device's camera.</span></span>
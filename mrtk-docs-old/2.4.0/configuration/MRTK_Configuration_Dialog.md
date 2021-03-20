---
title: MRTK_Configuration_Dialog
description: Configurare MRTK nel progetto Unity
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
ms.localizationpriority: medium
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, Unity
ms.openlocfilehash: 7acb19d26ee8c3d0379f0ada4eb1374a0d3fd7cd
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2021
ms.locfileid: "104681244"
---
# <a name="mrtk-project-configuration-dialog"></a><span data-ttu-id="38977-104">Finestra di dialogo di configurazione del progetto MRTK</span><span class="sxs-lookup"><span data-stu-id="38977-104">MRTK project configuration dialog</span></span>

<span data-ttu-id="38977-105">La finestra di dialogo di configurazione MRTK viene visualizzata quando Unity carica un progetto ed è determinato che una o più opzioni di configurazione richiedono l'attenzione dello sviluppatore.</span><span class="sxs-lookup"><span data-stu-id="38977-105">The MRTK configuration dialog is displayed when Unity loads a project and it is determined that one or more configuration options needs the attention of the developer.</span></span>

![Applica in seguito Ignora](../features/Images/ConfigurationDialog/ConfigurationDialogHeader.png)

<span data-ttu-id="38977-107">Per applicare le modifiche, fare clic sul pulsante **applica** .</span><span class="sxs-lookup"><span data-stu-id="38977-107">To apply the changes, click the **Apply** button.</span></span> <span data-ttu-id="38977-108">Il pulsante **più avanti** rinvia le modifiche finché il progetto non viene ricaricato in un momento successivo.</span><span class="sxs-lookup"><span data-stu-id="38977-108">The **Later** button will defer the changes until the project is reloaded at a future time.</span></span>

> [!NOTE]
> <span data-ttu-id="38977-109">Se una o più delle impostazioni consigliate non sono state controllate, verrà visualizzata nuovamente la finestra di dialogo di configurazione.</span><span class="sxs-lookup"><span data-stu-id="38977-109">The configuration dialog will reappear if one or more of the recommended settings is left unchecked.</span></span> <span data-ttu-id="38977-110">Per evitare che ciò accada, applicare le opzioni desiderate, quindi riavviare la finestra di dialogo tramite le utilità del **Toolkit di realtà mista**  >    >  **configurare il progetto Unity** e fare clic su **Ignora**.</span><span class="sxs-lookup"><span data-stu-id="38977-110">To prevent this from occurring, apply the desired options, then relaunch the dialog via  **Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project** and click **Ignore**.</span></span> <span data-ttu-id="38977-111">In questo modo si impedisce la visualizzazione automatica della finestra di dialogo di configurazione.</span><span class="sxs-lookup"><span data-stu-id="38977-111">This will prevent the configuration dialog from reappearing automatically.</span></span>

## <a name="common-settings"></a><span data-ttu-id="38977-112">Impostazioni comuni</span><span class="sxs-lookup"><span data-stu-id="38977-112">Common settings</span></span>

<span data-ttu-id="38977-113">Tutte le destinazioni di compilazione condividono una raccolta di opzioni comuni.</span><span class="sxs-lookup"><span data-stu-id="38977-113">All build targets share a collection of common options.</span></span>

![Impostazioni comuni](../features/Images/ConfigurationDialog/ConfigurationDialogCommonSettings.png)

### <a name="force-text-asset-serialization-and-enable-visible-meta-files"></a><span data-ttu-id="38977-115">Forza la serializzazione degli asset di testo e Abilita i metadati visibili</span><span class="sxs-lookup"><span data-stu-id="38977-115">Force text asset serialization and Enable visible meta files</span></span>

<span data-ttu-id="38977-116">Queste impostazioni consentono di semplificare l'uso dei progetti Unity e dei sistemi di controllo del codice sorgente (ad esempio, git).</span><span class="sxs-lookup"><span data-stu-id="38977-116">These settings help simplify working with Unity projects and source control systems (ex: Git).</span></span>

### <a name="enable-vr-supported"></a><span data-ttu-id="38977-117">Abilitazione di VR supportata</span><span class="sxs-lookup"><span data-stu-id="38977-117">Enable VR supported</span></span>

<span data-ttu-id="38977-118">**Unity 2018**</span><span class="sxs-lookup"><span data-stu-id="38977-118">**Unity 2018**</span></span>

<span data-ttu-id="38977-119">Configura le opzioni Virtual Reality supported e Virtual Reality SDK in **Impostazioni lettore**  >  **XR impostazioni**.</span><span class="sxs-lookup"><span data-stu-id="38977-119">Configures the Virtual Reality Supported and Virtual Reality SDK options in **Player Settings** > **XR Settings**.</span></span>

### <a name="set-single-pass-instanced-rendering-path"></a><span data-ttu-id="38977-120">Imposta il percorso di rendering con istanza Single Pass</span><span class="sxs-lookup"><span data-stu-id="38977-120">Set Single Pass Instanced rendering path</span></span>

<span data-ttu-id="38977-121">Configura le impostazioni del **lettore impostazioni**  >  **XR**  >  **modalità di rendering stereo** per **singolo passaggio istanza**.</span><span class="sxs-lookup"><span data-stu-id="38977-121">Configures the **Player Settings** > **XR Settings** > **Stereo Rendering Mode** to **Single Pass Instanced**.</span></span>

### <a name="set-default-spatial-awareness-layer"></a><span data-ttu-id="38977-122">Imposta livello di riconoscimento spaziale predefinito</span><span class="sxs-lookup"><span data-stu-id="38977-122">Set default Spatial Awareness layer</span></span>

<span data-ttu-id="38977-123">Registra la consapevolezza spaziale come livello 31 per consentire una configurazione semplice e coerente delle opzioni di Raycast e fisica.</span><span class="sxs-lookup"><span data-stu-id="38977-123">Registers Spatial Awareness as layer 31 to enable easy and consistent configuration of raycast and physics options.</span></span>

### <a name="audio-spatializer"></a><span data-ttu-id="38977-124">Spatializer audio</span><span class="sxs-lookup"><span data-stu-id="38977-124">Audio spatializer</span></span>

<span data-ttu-id="38977-125">Spatializers audio sono i componenti che sbloccano la potenza del suono spaziale e dell'audio posizionale per rendere realmente immersive le esperienze di realtà miste.</span><span class="sxs-lookup"><span data-stu-id="38977-125">Audio spatializers are the components that unlock the power of Spatial Sound and positional audio to make mixed reality experiences truly immersive.</span></span>

> [!NOTE]
> <span data-ttu-id="38977-126">Se si imposta Spatializer audio su None, le funzionalità audio posizionali non vengono disabilitate.</span><span class="sxs-lookup"><span data-stu-id="38977-126">Setting the audio spatializer to None will disable positional audio features.</span></span>

#### <a name="common-spatializers"></a><span data-ttu-id="38977-127">Spatializers comuni</span><span class="sxs-lookup"><span data-stu-id="38977-127">Common spatializers</span></span>

- <span data-ttu-id="38977-128">Microsoft Spatializer</span><span class="sxs-lookup"><span data-stu-id="38977-128">Microsoft Spatializer</span></span>

<span data-ttu-id="38977-129">Microsoft ha fornito Spatializer che supporta l'utilizzo dell'accelerazione hardware in HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="38977-129">Microsoft provided spatializer that supports utilization of hardware acceleration on HoloLens 2.</span></span>

<span data-ttu-id="38977-130">Questo Spatializer è disponibile tramite [NuGet](https://www.nuget.org/packages/Microsoft.SpatialAudio.Spatializer.Unity/) e [GitHub](https://github.com/microsoft/spatialaudio-unity).</span><span class="sxs-lookup"><span data-stu-id="38977-130">This spatializer is available via [NuGet](https://www.nuget.org/packages/Microsoft.SpatialAudio.Spatializer.Unity/) and [GitHub](https://github.com/microsoft/spatialaudio-unity).</span></span>

<span data-ttu-id="38977-131">Per ulteriori informazioni su Microsoft Spatializer, vedere la [documentazione relativa al suono spaziale](https://docs.microsoft.com/windows/mixed-reality/spatial-sound-in-unity).</span><span class="sxs-lookup"><span data-stu-id="38977-131">More details on Microsoft Spatializer can be found in the [Spatial Sound documentation](https://docs.microsoft.com/windows/mixed-reality/spatial-sound-in-unity).</span></span>

- <span data-ttu-id="38977-132">MS HRTF Spatializer</span><span class="sxs-lookup"><span data-stu-id="38977-132">MS HRTF Spatializer</span></span>

<span data-ttu-id="38977-133">Microsoft Windows Spatializer fornito da Unity come parte della realtà mista di Windows e dei pacchetti della piattaforma Windows XR.</span><span class="sxs-lookup"><span data-stu-id="38977-133">Microsoft Windows spatializer that is provided by Unity as part of the Windows Mixed Reality and Windows XR Platform packages.</span></span>

- <span data-ttu-id="38977-134">Audio risonanza</span><span class="sxs-lookup"><span data-stu-id="38977-134">Resonance Audio</span></span>

<span data-ttu-id="38977-135">Spatializer multipiattaforma di Google fornito da Unity.</span><span class="sxs-lookup"><span data-stu-id="38977-135">A cross platform spatializer from Google that is provided by Unity.</span></span>

<span data-ttu-id="38977-136">Altre informazioni sono reperibili nel sito di [documentazione audio risonanza](https://resonance-audio.github.io/resonance-audio/develop/unity/getting-started) .</span><span class="sxs-lookup"><span data-stu-id="38977-136">More information can be found on the [Resonance Audio documentation](https://resonance-audio.github.io/resonance-audio/develop/unity/getting-started) site.</span></span>

## <a name="universal-windows-platform-settings"></a><span data-ttu-id="38977-137">Impostazioni piattaforma UWP (Universal Windows Platform)</span><span class="sxs-lookup"><span data-stu-id="38977-137">Universal Windows Platform settings</span></span>

![Impostazioni UWP](../features/Images/ConfigurationDialog/ConfigurationDialogUWPSettings.png)

### <a name="enable-msbuild-for-unity"></a><span data-ttu-id="38977-139">Abilita MSBuild per Unity</span><span class="sxs-lookup"><span data-stu-id="38977-139">Enable MSBuild for Unity</span></span>

<span data-ttu-id="38977-140">**Unity 2019,2 e versioni precedenti**</span><span class="sxs-lookup"><span data-stu-id="38977-140">**Unity 2019.2 and earlier**</span></span>

<span data-ttu-id="38977-141">MSBuild per Unity è un componente che consente il ripristino automatico di pacchetti NuGet specifici.</span><span class="sxs-lookup"><span data-stu-id="38977-141">MSBuild for Unity is a component that enables automatic restoring of specific NuGet packages.</span></span> <span data-ttu-id="38977-142">In questa versione, il pacchetto **Microsoft. Windows. MixedReality. DotNetWinRT** verrà installato dopo l'abilitazione di MSBuild per Unity.</span><span class="sxs-lookup"><span data-stu-id="38977-142">In this version, the **Microsoft.Windows.MixedReality.DotNetWinRT** package will be installed after enabling MSBuild for Unity.</span></span>

### <a name="uwp-capabilities"></a><span data-ttu-id="38977-143">Funzionalità UWP</span><span class="sxs-lookup"><span data-stu-id="38977-143">UWP Capabilities</span></span>

<span data-ttu-id="38977-144">Abilita funzionalità specifiche dell'applicazione per piattaforma UWP (Universal Windows Platform) applicazione.</span><span class="sxs-lookup"><span data-stu-id="38977-144">Enables specific application capabilities for Universal Windows Platform application.</span></span> <span data-ttu-id="38977-145">Queste funzionalità consentono alla piattaforma di informare e richiedere l'autorizzazione per abilitare funzionalità specifiche.</span><span class="sxs-lookup"><span data-stu-id="38977-145">These capabilities enable the platform to inform and request permission to enable specific functionality.</span></span>

- <span data-ttu-id="38977-146">Microfono</span><span class="sxs-lookup"><span data-stu-id="38977-146">Microphone</span></span>

  <span data-ttu-id="38977-147">Abilita l'acquisizione di suoni tramite il microfono.</span><span class="sxs-lookup"><span data-stu-id="38977-147">Enables capturing sound via the microphone.</span></span>

- <span data-ttu-id="38977-148">Client Internet</span><span class="sxs-lookup"><span data-stu-id="38977-148">Internet Client</span></span>

  <span data-ttu-id="38977-149">Abilita il supporto per l'accesso alle risorse su Internet.</span><span class="sxs-lookup"><span data-stu-id="38977-149">Enables support for accessing resources on the internet.</span></span>

- <span data-ttu-id="38977-150">Percezione spaziale</span><span class="sxs-lookup"><span data-stu-id="38977-150">Spatial Perception</span></span>

  <span data-ttu-id="38977-151">Abilita il supporto per l'uso dell'ambiente reale.</span><span class="sxs-lookup"><span data-stu-id="38977-151">Enables support for using the real-world environment.</span></span>

- <span data-ttu-id="38977-152">Occhio</span><span class="sxs-lookup"><span data-stu-id="38977-152">Eye Gaze</span></span>

  <span data-ttu-id="38977-153">**Unity 2019,3 e versioni successive**</span><span class="sxs-lookup"><span data-stu-id="38977-153">**Unity 2019.3 and newer**</span></span>

  <span data-ttu-id="38977-154">Abilita il supporto per tenere traccia degli sguardi dell'utente.</span><span class="sxs-lookup"><span data-stu-id="38977-154">Enables support for tracking the user's eye gaze.</span></span>

## <a name="android-settings"></a><span data-ttu-id="38977-155">Impostazioni Android</span><span class="sxs-lookup"><span data-stu-id="38977-155">Android settings</span></span>

<span data-ttu-id="38977-156">Impostazioni di configurazione per supportare le applicazioni AR nei dispositivi Android.</span><span class="sxs-lookup"><span data-stu-id="38977-156">Configuration settings to support AR applications on Android powered devices.</span></span>

![Impostazioni Android](../features/Images/ConfigurationDialog/ConfigurationDialogAndroidSettings.png)

### <a name="disable-multi-threaded-rendering"></a><span data-ttu-id="38977-158">Disabilitare il rendering multithread</span><span class="sxs-lookup"><span data-stu-id="38977-158">Disable Multi-Threaded Rendering</span></span>

<span data-ttu-id="38977-159">Disabilita **le impostazioni del lettore**  >  **altre impostazioni**  >  di **rendering multithreading** come richiesto dal supporto AR di Android.</span><span class="sxs-lookup"><span data-stu-id="38977-159">Disables **Player Settings** > **Other Settings** > **Multithreaded Rendering** as required by Android's AR support.</span></span>

### <a name="set-minimum-api-level"></a><span data-ttu-id="38977-160">Imposta il livello API minimo</span><span class="sxs-lookup"><span data-stu-id="38977-160">Set Minimum API Level</span></span>

<span data-ttu-id="38977-161">Imposta il valore delle **impostazioni del lettore**  >  **altre impostazioni**  >  **livello API minimo** per applicare i requisiti del sistema operativo per le applicazioni AR.</span><span class="sxs-lookup"><span data-stu-id="38977-161">Sets the value of **Player Settings** > **Other Settings** > **Minimum API Level** to enforce operating system requirements for AR applications.</span></span>

## <a name="ios-settings"></a><span data-ttu-id="38977-162">Impostazioni iOS</span><span class="sxs-lookup"><span data-stu-id="38977-162">iOS settings</span></span>

<span data-ttu-id="38977-163">Impostazioni di configurazione per supportare le applicazioni AR nei dispositivi con tecnologia iOS.</span><span class="sxs-lookup"><span data-stu-id="38977-163">Configuration settings to support AR applications on iOS powered devices.</span></span>

![Impostazioni iOS](../features/Images/ConfigurationDialog/ConfigurationDialogiOSSettings.png)

### <a name="set-required-os-version"></a><span data-ttu-id="38977-165">Imposta la versione richiesta del sistema operativo</span><span class="sxs-lookup"><span data-stu-id="38977-165">Set Required OS Version</span></span>

<span data-ttu-id="38977-166">Imposta il valore delle **impostazioni del lettore**  >  **altre impostazioni** di  >  **destinazione della versione minima di iOS** per applicare i requisiti del sistema operativo per le applicazioni AR.</span><span class="sxs-lookup"><span data-stu-id="38977-166">Sets the value of **Player Settings** > **Other Settings** > **Target minimum iOS Version** to enforce operating system requirements for AR applications.</span></span>

### <a name="set-required-architecture"></a><span data-ttu-id="38977-167">Imposta architettura necessaria</span><span class="sxs-lookup"><span data-stu-id="38977-167">Set Required Architecture</span></span>

<span data-ttu-id="38977-168">Imposta il valore dell'   >  architettura di **altre impostazioni** del lettore  >   per applicare i requisiti di piattaforma per le applicazioni AR.</span><span class="sxs-lookup"><span data-stu-id="38977-168">Sets the value of **Player Settings** > **Other Settings** > **Architecture** to enforce platform requirements for AR applications.</span></span>

### <a name="set-camera-usage-descriptions"></a><span data-ttu-id="38977-169">Imposta descrizioni utilizzo della fotocamera</span><span class="sxs-lookup"><span data-stu-id="38977-169">Set Camera Usage Descriptions</span></span>

<span data-ttu-id="38977-170">Imposta il valore di **Impostazioni lettore**  >  **altre impostazioni**  >  **Descrizione utilizzo fotocamera** usato per richiedere l'autorizzazione per l'uso della fotocamera del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="38977-170">Sets the value of **Player Settings** > **Other Settings** > **Camera Usage Description** used to request permission to use the device's camera.</span></span>

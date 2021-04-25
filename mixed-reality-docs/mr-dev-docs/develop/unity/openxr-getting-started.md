---
title: Uso del plug-in OpenXR di realtà mista per Unity
description: Informazioni su come abilitare il plug-in OpenXR di Realtà mista per i progetti Unity.
author: hferrone
ms.author: alexturn
ms.date: 01/11/2021
ms.topic: article
keywords: openxr, unity, hololens, hololens 2, realtà mista, MRTK, Mixed Reality Toolkit, realtà aumentata, realtà virtuale, visori VR di realtà mista, apprendimento, esercitazione, introduzione
ms.openlocfilehash: 4c220deeca13c6807857375b71640207823b94ed
ms.sourcegitcommit: 95fbb851336b6c5977a2ce4d4ac10f0eeb0df31f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/24/2021
ms.locfileid: "107944662"
---
# <a name="using-the-mixed-reality-openxr-plugin-for-unity"></a><span data-ttu-id="9679a-104">Uso del plug-in OpenXR di realtà mista per Unity</span><span class="sxs-lookup"><span data-stu-id="9679a-104">Using the Mixed Reality OpenXR Plugin for Unity</span></span>

<span data-ttu-id="9679a-105">A partire da Unity versione 2020.2, il pacchetto di plug-in OpenXR di Realtà mista di Microsoft è disponibile tramite mixed [reality feature tool.](welcome-to-mr-feature-tool.md)</span><span class="sxs-lookup"><span data-stu-id="9679a-105">Starting with Unity version 2020.2, Microsoft’s Mixed Reality OpenXR Plugin package is available using the [Mixed Reality Feature Tool](welcome-to-mr-feature-tool.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="9679a-106">Prerequisiti</span><span class="sxs-lookup"><span data-stu-id="9679a-106">Prerequisites</span></span>

* <span data-ttu-id="9679a-107">Unity 2020.3 LTS o versione successiva</span><span class="sxs-lookup"><span data-stu-id="9679a-107">Unity 2020.3 LTS or later</span></span>
* <span data-ttu-id="9679a-108">Plug-in Unity OpenXR 1.1.1 o versione successiva</span><span class="sxs-lookup"><span data-stu-id="9679a-108">Unity OpenXR plugin 1.1.1 or later</span></span>
* <span data-ttu-id="9679a-109">Visual Studio 2019 o versione successiva</span><span class="sxs-lookup"><span data-stu-id="9679a-109">Visual Studio 2019 or later</span></span>
* <span data-ttu-id="9679a-110">Installare il supporto della piattaforma **UWP** in Unity per HoloLens 2 app</span><span class="sxs-lookup"><span data-stu-id="9679a-110">Install **UWP** platform support in Unity for HoloLens 2 apps</span></span>

> [!NOTE]
> <span data-ttu-id="9679a-111">Se si compilano applicazioni di realtà virtuale in PC Windows, il plug-in OpenXR di Realtà mista non è necessariamente necessario.</span><span class="sxs-lookup"><span data-stu-id="9679a-111">If you're building VR applications on Windows PC, the Mixed Reality OpenXR plugin is not necessarily required.</span></span> <span data-ttu-id="9679a-112">Tuttavia, è necessario installare il plug-in se si personalizza il mapping del controller per i controller HP Reverb G2 o si compilano app che funzionano sia su visori VR HoloLens 2 che su visori VR.</span><span class="sxs-lookup"><span data-stu-id="9679a-112">However, you'll want to install the plugin if you're customizing controller mapping for HP Reverb G2 controllers or building apps that work on both HoloLens 2 and VR headsets.</span></span>

## <a name="setting-up-your-project-with-mrtk"></a><span data-ttu-id="9679a-113">Configurazione del progetto con MRTK</span><span class="sxs-lookup"><span data-stu-id="9679a-113">Setting up your project with MRTK</span></span>

<span data-ttu-id="9679a-114">MRTK per Unity offre un sistema di input multipiattaforma, componenti fondamentali e blocchi predefiniti comuni per le interazioni spaziali.</span><span class="sxs-lookup"><span data-stu-id="9679a-114">MRTK for Unity provides a cross-platform input system, foundational components, and common building blocks for spatial interactions.</span></span> <span data-ttu-id="9679a-115">MRTK versione 2 intende accelerare lo sviluppo di applicazioni per Microsoft HoloLens, i visori VR immersive di Windows Mixed Reality e la piattaforma OpenVR.</span><span class="sxs-lookup"><span data-stu-id="9679a-115">MRTK version 2 intends to speed up application development for Microsoft HoloLens, Windows Mixed Reality immersive (VR) headsets, and OpenVR platform.</span></span> <span data-ttu-id="9679a-116">Il progetto mira a ridurre le barriere di accesso, creare applicazioni di realtà mista e restituire contributi alla community per continuare a crescere insieme.</span><span class="sxs-lookup"><span data-stu-id="9679a-116">The project is aimed at reducing barriers to entry, creating mixed reality applications, and contributing back to the community as we all grow.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="9679a-117">Configurare il progetto con MRTK</span><span class="sxs-lookup"><span data-stu-id="9679a-117">Set up your project using MRTK</span></span>](https://docs.microsoft.com/windows/mixed-reality/develop/unity/tutorials/mr-learning-base-02?tabs=openxr)

<span data-ttu-id="9679a-118">Per altri dettagli sulle funzionalità, vedere la documentazione di [MRTK.](/windows/mixed-reality/mrtk-unity)</span><span class="sxs-lookup"><span data-stu-id="9679a-118">Take a look at [MRTK's documentation](/windows/mixed-reality/mrtk-unity) for more feature details.</span></span>

## <a name="manual-setup-without-mrtk"></a><span data-ttu-id="9679a-119">Configurazione manuale senza MRTK</span><span class="sxs-lookup"><span data-stu-id="9679a-119">Manual setup without MRTK</span></span>

<span data-ttu-id="9679a-120">Installare il plug-in OpenXR con la nuova applicazione Mixed Reality Feature Tool.</span><span class="sxs-lookup"><span data-stu-id="9679a-120">Install the OpenXR plugin with the new Mixed Reality Feature Tool application.</span></span> <span data-ttu-id="9679a-121">Seguire le [istruzioni di installazione e utilizzo](welcome-to-mr-feature-tool.md) e selezionare il pacchetto Mixed Reality **OpenXR Plugin** nella categoria Mixed Reality Toolkit:</span><span class="sxs-lookup"><span data-stu-id="9679a-121">Follow the [installation and usage instructions](welcome-to-mr-feature-tool.md) and select the **Mixed Reality OpenXR Plugin** package in the Mixed Reality Toolkit category:</span></span>

![Finestra dei pacchetti dello strumento di funzionalità di realtà mista con il plug-in xr aperto evidenziato](images/feature-tool-openxr.png)

## <a name="setting-your-build-target"></a><span data-ttu-id="9679a-123">Impostazione della destinazione di compilazione</span><span class="sxs-lookup"><span data-stu-id="9679a-123">Setting your build target</span></span>

<span data-ttu-id="9679a-124">Se si usa la realtà virtuale desktop come destinazione, è consigliabile usare la piattaforma pc autonoma selezionata per impostazione predefinita in un nuovo progetto Unity:</span><span class="sxs-lookup"><span data-stu-id="9679a-124">If you're targeting Desktop VR, we suggest using the PC Standalone Platform selected by default on a new Unity project:</span></span>

![Screenshot della finestra Build Settings (Impostazioni di compilazione) aperta nell'editor di Unity con PC, Mac & piattaforma autonoma evidenziata](images/wmr-config-img-3.png)

<span data-ttu-id="9679a-126">Se la destinazione è HoloLens 2, è necessario passare al piattaforma UWP (Universal Windows Platform):</span><span class="sxs-lookup"><span data-stu-id="9679a-126">If you're targeting HoloLens 2, you need to switch to the Universal Windows Platform:</span></span>

1.  <span data-ttu-id="9679a-127">Selezionare **Impostazioni > file...**</span><span class="sxs-lookup"><span data-stu-id="9679a-127">Select **File > Build Settings...**</span></span>
2.  <span data-ttu-id="9679a-128">Selezionare **piattaforma UWP (Universal Windows Platform)** nell'elenco Piattaforma e selezionare **Cambia piattaforma**</span><span class="sxs-lookup"><span data-stu-id="9679a-128">Select **Universal Windows Platform** in the Platform list and select **Switch Platform**</span></span>
3.  <span data-ttu-id="9679a-129">Impostare **Architecture (Architettura)** **su ARM 64**</span><span class="sxs-lookup"><span data-stu-id="9679a-129">Set **Architecture** to **ARM 64**</span></span>
4.  <span data-ttu-id="9679a-130">Impostare **Dispositivo di destinazione** su **HoloLens**</span><span class="sxs-lookup"><span data-stu-id="9679a-130">Set **Target device** to **HoloLens**</span></span>
5.  <span data-ttu-id="9679a-131">Impostare **Tipo di compilazione** su **D3D**</span><span class="sxs-lookup"><span data-stu-id="9679a-131">Set **Build Type** to **D3D**</span></span>
6.  <span data-ttu-id="9679a-132">Impostare **UWP SDK su** Latest installed **(Versione più recente installata)**</span><span class="sxs-lookup"><span data-stu-id="9679a-132">Set **UWP SDK** to **Latest installed**</span></span>
7.  <span data-ttu-id="9679a-133">Impostare **Build configuration (Configurazione build)** **su Release (Versione)** perché sono presenti problemi di prestazioni noti con Debug</span><span class="sxs-lookup"><span data-stu-id="9679a-133">Set **Build configuration** to **Release** because there are known performance issues with Debug</span></span>

![Screenshot della finestra Build Settings (Impostazioni di compilazione) aperta nell'editor di Unity con piattaforma UWP (Universal Windows Platform) evidenziato](images/wmr-config-img-4.png)

<span data-ttu-id="9679a-135">Dopo aver impostato la piattaforma, è necessario invii a Unity una visualizzazione [immersiva](../../design/app-views.md) anziché una visualizzazione 2D quando viene esportata.</span><span class="sxs-lookup"><span data-stu-id="9679a-135">After setting your platform, you need to let Unity know to create an [immersive view](../../design/app-views.md) instead of a 2D view when exported.</span></span>

## <a name="configuring-xr-plugin-management-for-openxr"></a><span data-ttu-id="9679a-136">Configurazione della gestione dei plug-in XR per OpenXR</span><span class="sxs-lookup"><span data-stu-id="9679a-136">Configuring XR Plugin Management for OpenXR</span></span>

<span data-ttu-id="9679a-137">Per impostare OpenXR come runtime in Unity:</span><span class="sxs-lookup"><span data-stu-id="9679a-137">To set OpenXR as the the runtime in Unity:</span></span>

1. <span data-ttu-id="9679a-138">Nell'editor di Unity passare a **Edit > Project Settings (Modifica impostazioni progetto)**</span><span class="sxs-lookup"><span data-stu-id="9679a-138">In the Unity Editor, navigate to **Edit > Project Settings**</span></span>
2. <span data-ttu-id="9679a-139">Nell'elenco delle impostazioni selezionare **XR Plugin Management (Gestione plug-in XR)**</span><span class="sxs-lookup"><span data-stu-id="9679a-139">In the list of Settings, select **XR Plugin Management**</span></span>
3. <span data-ttu-id="9679a-140">Selezionare le **caselle Inizializza XR all'avvio** **e OpenXR**</span><span class="sxs-lookup"><span data-stu-id="9679a-140">Check the **Initialize XR on Startup** and **OpenXR** boxes</span></span>
4. <span data-ttu-id="9679a-141">Se la destinazione HoloLens 2, assicurarsi di essere nella piattaforma UWP e selezionare Microsoft HoloLens **set di funzionalità**</span><span class="sxs-lookup"><span data-stu-id="9679a-141">If targeting HoloLens 2, make sure you're on the UWP platform and select **Microsoft HoloLens Feature Set**</span></span>

![Screenshot del pannello delle impostazioni del progetto aperto nell'editor di Unity con gestione plug-in XR evidenziata](images/openxr-img-05.png)

## <a name="optimization"></a><span data-ttu-id="9679a-143">Optimization</span><span class="sxs-lookup"><span data-stu-id="9679a-143">Optimization</span></span>

<span data-ttu-id="9679a-144">Se stai sviluppando per HoloLens 2, passa a **Mixed Reality> OpenXR > Apply recommended project settings for HoloLens 2** (Applica le impostazioni di progetto consigliate per HoloLens 2 per ottenere prestazioni migliori per le app).</span><span class="sxs-lookup"><span data-stu-id="9679a-144">If you're developing for HoloLens 2, navigate to **Mixed Reality> OpenXR > Apply recommended project settings for HoloLens 2** to get better app performance.</span></span>

![Screenshot della voce di menu di realtà mista aperta con OpenXR selezionato](images/openxr-img-08.png)

> [!IMPORTANT]
> <span data-ttu-id="9679a-146">Se viene visualizzata un'icona di avviso rossa accanto al **plug-in OpenXR,** fare clic sull'icona e selezionare **Correggi tutto** prima di continuare.</span><span class="sxs-lookup"><span data-stu-id="9679a-146">If you see a red warning icon next to **OpenXR Plugin**, click the icon and select **Fix all** before continuing.</span></span> <span data-ttu-id="9679a-147">Per l'applicazione delle modifiche potrebbe essere necessario riavviare l'editor di Unity.</span><span class="sxs-lookup"><span data-stu-id="9679a-147">The Unity Editor may need to restart itself for the changes to take effect.</span></span>

![Screenshot della finestra di convalida del progetto OpenXR](images/openxr-img-06.png)

<span data-ttu-id="9679a-149">A questo punto è possibile iniziare a sviluppare con OpenXR in Unity.</span><span class="sxs-lookup"><span data-stu-id="9679a-149">You're now ready to begin developing with OpenXR in Unity!</span></span>  <span data-ttu-id="9679a-150">Passare alla sezione successiva per informazioni su come usare gli esempi OpenXR.</span><span class="sxs-lookup"><span data-stu-id="9679a-150">Continue on to the next section to learn how to use the OpenXR samples.</span></span>

## <a name="try-out-the-unity-sample-scenes"></a><span data-ttu-id="9679a-151">Provare le scene di esempio di Unity</span><span class="sxs-lookup"><span data-stu-id="9679a-151">Try out the Unity sample scenes</span></span>

### <a name="hololens-2-samples"></a><span data-ttu-id="9679a-152">HoloLens 2 esempi</span><span class="sxs-lookup"><span data-stu-id="9679a-152">HoloLens 2 samples</span></span>

1. <span data-ttu-id="9679a-153">Nell'editor di Unity passare a **Finestra > Gestione pacchetti**</span><span class="sxs-lookup"><span data-stu-id="9679a-153">In the Unity Editor, navigate to **Window > Package Manager**</span></span>
2. <span data-ttu-id="9679a-154">Nell'elenco dei pacchetti selezionare **Mixed Reality OpenXR Plugin**</span><span class="sxs-lookup"><span data-stu-id="9679a-154">In the list of packages, select **Mixed Reality OpenXR Plugin**</span></span>
3. <span data-ttu-id="9679a-155">Individuare l'esempio **nell'elenco Esempi** e selezionare **Importa**</span><span class="sxs-lookup"><span data-stu-id="9679a-155">Locate the sample in the **Samples** list and select **Import**</span></span>

![Screenshot di Unity Gestione pacchetti aperto nell'editor unity con il plug-in OpenXR di realtà mista selezionato e il pulsante di importazione degli esempi evidenziato](images/openxr-img-03.png)

<!-- ### For all other OpenXR samples

1. In the Unity Editor, navigate to **Window > Package Manager**
2. In the list of packages, select **OpenXR Plugin**
3. Locate the sample in the **Samples** list and select **Import**

![Screenshot of Unity Package Manager open in Unity editor with OpenXR Plugin selected and samples import button highlighted](images/openxr-img-10.png) -->

> [!NOTE]
> <span data-ttu-id="9679a-157">Quando un pacchetto viene aggiornato, Unity offre la possibilità di aggiornare gli esempi importati.</span><span class="sxs-lookup"><span data-stu-id="9679a-157">When a package is updated, Unity provides the option to update imported samples.</span></span>  <span data-ttu-id="9679a-158">L'aggiornamento di un esempio importato sovrascriverà tutte le modifiche apportate all'esempio e agli asset associati.</span><span class="sxs-lookup"><span data-stu-id="9679a-158">Updating an imported sample will overwrite any changes that have been made to the sample and associated assets.</span></span>

## <a name="using-mrtk-with-openxr-support"></a><span data-ttu-id="9679a-159">Uso di MRTK con il supporto OpenXR</span><span class="sxs-lookup"><span data-stu-id="9679a-159">Using MRTK with OpenXR support</span></span>

<span data-ttu-id="9679a-160">MRTK-Unity supporta il plug-in OpenXR di realtà mista a partire dalla versione 2.5.3.</span><span class="sxs-lookup"><span data-stu-id="9679a-160">MRTK-Unity supports the Mixed Reality OpenXR plugin starting with the 2.5.3 release.</span></span>

1. <span data-ttu-id="9679a-161">Aprire di [nuovo Mixed Reality Feature Tool](welcome-to-mr-feature-tool.md) per installare Mixed Reality Toolkit, se non è già stato fatto.</span><span class="sxs-lookup"><span data-stu-id="9679a-161">Open the [Mixed Reality Feature Tool](welcome-to-mr-feature-tool.md) again to install the Mixed Reality Toolkit, if you haven't already.</span></span> <span data-ttu-id="9679a-162">Il supporto openXR è nel **pacchetto Foundation.**</span><span class="sxs-lookup"><span data-stu-id="9679a-162">OpenXR support is in the **Foundation** package.</span></span>
2. <span data-ttu-id="9679a-163">Passare allo script del componente MixedReality Toolkit in Inspector e passare al **profilo DefaultOpenXRConfigurationProfile:**</span><span class="sxs-lookup"><span data-stu-id="9679a-163">Go to the MixedReality Toolkit component script in the Inspector and switch to the **DefaultOpenXRConfigurationProfile** profile:</span></span>

    ![Screenshot del cambio della configurazione MRTK nel componente Mixed Reality Toolkit nel controllo](images/openxr-img-11.png)

    1. <span data-ttu-id="9679a-165">Per informazioni più dettagliate sulla [migrazione a OpenXR,](/windows/mixed-reality/mrtk-unity/configuration/getting-started-with-mrtk-and-xrsdk#configuring-mrtk-for-the-xr-sdk-pipeline)vedere la documentazione di MRTK.</span><span class="sxs-lookup"><span data-stu-id="9679a-165">See the MRTK documentation for [more in-depth information on migrating to OpenXR](/windows/mixed-reality/mrtk-unity/configuration/getting-started-with-mrtk-and-xrsdk#configuring-mrtk-for-the-xr-sdk-pipeline).</span></span>

> [!NOTE]
> <span data-ttu-id="9679a-166">Quando si esegue l'aggiornamento da una versione precedente di MRTK, assicurarsi che la riga seguente si trova nel file **Assets/MixedRealityToolkit.Generated/link.xml:**</span><span class="sxs-lookup"><span data-stu-id="9679a-166">When upgrading from a previous version of MRTK, ensure the following line is in the **Assets/MixedRealityToolkit.Generated/link.xml** file:</span></span>
>
> ```xml
> <assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.OpenXR" preserve="all"/>
> ```
>
> <span data-ttu-id="9679a-167">Questa riga verrà aggiunta per impostazione predefinita se si è iniziato con MRTK 2.5.4 o versione successiva.</span><span class="sxs-lookup"><span data-stu-id="9679a-167">This line will be added by default if you started with MRTK 2.5.4 or newer.</span></span>

## <a name="next-steps"></a><span data-ttu-id="9679a-168">Passaggi successivi</span><span class="sxs-lookup"><span data-stu-id="9679a-168">Next steps</span></span>

<span data-ttu-id="9679a-169">Ora che il progetto è configurato per OpenXR e [](openxr-supported-features.md) si ha accesso agli esempi, vedere quali funzionalità sono attualmente supportate nel plug-in OpenXR.</span><span class="sxs-lookup"><span data-stu-id="9679a-169">Now that you have your project configured for OpenXR and have access to samples, check out what [features](openxr-supported-features.md) are currently supported in our OpenXR plugin.</span></span>

## <a name="have-feedback"></a><span data-ttu-id="9679a-170">Commenti e suggerimenti?</span><span class="sxs-lookup"><span data-stu-id="9679a-170">Have Feedback?</span></span>

<span data-ttu-id="9679a-171">OpenXR è ancora sperimentale, quindi i commenti e i suggerimenti che è possibile inviare sono utili per migliorarlo.</span><span class="sxs-lookup"><span data-stu-id="9679a-171">OpenXR is still experimental, so we’d appreciate any feedback you can give us to help make it better.</span></span> <span data-ttu-id="9679a-172">È possibile trovare microsoft nei [forum unity](https://aka.ms/unityforums) contrassegnando il post del forum con **Microsoft**  +  **OpenXR** e HoloLens 2 o **Windows Mixed Reality**. </span><span class="sxs-lookup"><span data-stu-id="9679a-172">You'll find us on the [Unity Forums](https://aka.ms/unityforums) by tagging your forum post with **Microsoft** + **OpenXR** and either **HoloLens 2** or **Windows Mixed Reality**.</span></span>

## <a name="see-also"></a><span data-ttu-id="9679a-173">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="9679a-173">See also</span></span>

* [<span data-ttu-id="9679a-174">Configurazione del progetto senza MRTK</span><span class="sxs-lookup"><span data-stu-id="9679a-174">Configuring your project without MRTK</span></span>](configure-unity-project.md)
* [<span data-ttu-id="9679a-175">Impostazioni consigliate per Unity</span><span class="sxs-lookup"><span data-stu-id="9679a-175">Recommended settings for Unity</span></span>](recommended-settings-for-unity.md)
* [<span data-ttu-id="9679a-176">Consigli sulle prestazioni per Unity</span><span class="sxs-lookup"><span data-stu-id="9679a-176">Performance recommendations for Unity</span></span>](performance-recommendations-for-unity.md#how-to-profile-with-unity)

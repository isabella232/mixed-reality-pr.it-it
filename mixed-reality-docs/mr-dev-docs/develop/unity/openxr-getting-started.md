---
title: Uso del plug-in OpenXR per la realtà mista per Unity
description: Informazioni su come abilitare il plug-in OpenXR per la realtà mista per i progetti Unity.
author: hferrone
ms.author: alexturn
ms.date: 01/11/2021
ms.topic: article
keywords: openxr, Unity, hololens, hololens 2, realtà mista, MRTK, Toolkit per realtà mista, realtà aumentata, realtà virtuale, cuffie con realtà mista, informazioni, esercitazione, introduzione
ms.openlocfilehash: ebe7d32b236e28259b2ed9a7915bd337f84f8762
ms.sourcegitcommit: 8d386bf6c82ec9860815e873e1f2870ea410f40f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/31/2021
ms.locfileid: "106088510"
---
# <a name="using-the-mixed-reality-openxr-plugin-for-unity"></a><span data-ttu-id="a49b0-104">Uso del plug-in OpenXR per la realtà mista per Unity</span><span class="sxs-lookup"><span data-stu-id="a49b0-104">Using the Mixed Reality OpenXR Plugin for Unity</span></span>

<span data-ttu-id="a49b0-105">A partire da Unity versione 2020,2, il pacchetto di plug-in per la realtà mista di Microsoft OpenXR è disponibile tramite Gestione pacchetti Unity (UPM).</span><span class="sxs-lookup"><span data-stu-id="a49b0-105">Starting with Unity version 2020.2, Microsoft’s Mixed Reality OpenXR Plugin package is available using the Unity Package Manager (UPM).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="a49b0-106">Prerequisiti</span><span class="sxs-lookup"><span data-stu-id="a49b0-106">Prerequisites</span></span>

* <span data-ttu-id="a49b0-107">Unity 2020,3 LTS o versione successiva</span><span class="sxs-lookup"><span data-stu-id="a49b0-107">Unity 2020.3 LTS or later</span></span>
* <span data-ttu-id="a49b0-108">Plug-in OpenXR Unity 1.0.3 o versione successiva</span><span class="sxs-lookup"><span data-stu-id="a49b0-108">Unity OpenXR plugin 1.0.3 or later</span></span>
* <span data-ttu-id="a49b0-109">Visual Studio 2019 o versione successiva</span><span class="sxs-lookup"><span data-stu-id="a49b0-109">Visual Studio 2019 or later</span></span>
* <span data-ttu-id="a49b0-110">Installare il supporto della piattaforma **UWP** in Unity per le app HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="a49b0-110">Install **UWP** platform support in Unity for HoloLens 2 apps</span></span>

> [!NOTE]
> <span data-ttu-id="a49b0-111">Se si stanno compilando applicazioni VR in PC Windows, il plug-in OpenXR per realtà mista non è necessariamente obbligatorio.</span><span class="sxs-lookup"><span data-stu-id="a49b0-111">If you're building VR applications on Windows PC, the Mixed Reality OpenXR plugin is not necessarily required.</span></span> <span data-ttu-id="a49b0-112">Tuttavia, è necessario installare il plug-in se si sta personalizzando il mapping del controller per i controller HP Reverb G2 o la creazione di app che funzionano sia con le cuffie HoloLens 2 sia con le cuffie VR.</span><span class="sxs-lookup"><span data-stu-id="a49b0-112">However, you'll want to install the plugin if you're customizing controller mapping for HP Reverb G2 controllers or building apps that work on both HoloLens 2 and VR headsets.</span></span>

## <a name="setting-up-your-project-with-mrtk"></a><span data-ttu-id="a49b0-113">Impostazione del progetto con MRTK</span><span class="sxs-lookup"><span data-stu-id="a49b0-113">Setting up your project with MRTK</span></span>

<span data-ttu-id="a49b0-114">MRTK per Unity offre un sistema di input multipiattaforma, componenti fondamentali e blocchi predefiniti comuni per le interazioni spaziali.</span><span class="sxs-lookup"><span data-stu-id="a49b0-114">MRTK for Unity provides a cross-platform input system, foundational components, and common building blocks for spatial interactions.</span></span> <span data-ttu-id="a49b0-115">MRTK versione 2 intende accelerare lo sviluppo di applicazioni per Microsoft HoloLens, i visori VR immersive di Windows Mixed Reality e la piattaforma OpenVR.</span><span class="sxs-lookup"><span data-stu-id="a49b0-115">MRTK version 2 intends to speed up application development for Microsoft HoloLens, Windows Mixed Reality immersive (VR) headsets, and OpenVR platform.</span></span> <span data-ttu-id="a49b0-116">Il progetto mira a ridurre le barriere di accesso, creare applicazioni di realtà mista e restituire contributi alla community per continuare a crescere insieme.</span><span class="sxs-lookup"><span data-stu-id="a49b0-116">The project is aimed at reducing barriers to entry, creating mixed reality applications, and contributing back to the community as we all grow.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="a49b0-117">Configurare il progetto con MRTK</span><span class="sxs-lookup"><span data-stu-id="a49b0-117">Set up your project using MRTK</span></span>](https://docs.microsoft.com/windows/mixed-reality/develop/unity/tutorials/mr-learning-base-02?tabs=openxr)

<span data-ttu-id="a49b0-118">Per altri dettagli sulle funzionalità, vedere la [documentazione di MRTK](/windows/mixed-reality/mrtk-unity) .</span><span class="sxs-lookup"><span data-stu-id="a49b0-118">Take a look at [MRTK's documentation](/windows/mixed-reality/mrtk-unity) for more feature details.</span></span>

## <a name="manual-setup-without-mrtk"></a><span data-ttu-id="a49b0-119">Installazione manuale senza MRTK</span><span class="sxs-lookup"><span data-stu-id="a49b0-119">Manual setup without MRTK</span></span>

<span data-ttu-id="a49b0-120">Installare il plug-in OpenXR con la nuova applicazione dello strumento per la funzionalità di realtà mista.</span><span class="sxs-lookup"><span data-stu-id="a49b0-120">Install the OpenXR plugin with the new Mixed Reality Feature Tool application.</span></span> <span data-ttu-id="a49b0-121">Seguire le [istruzioni per l'installazione e l'utilizzo](welcome-to-mr-feature-tool.md) e selezionare il pacchetto di plug-in **realtà mista OpenXR** nella categoria del Toolkit di realtà mista:</span><span class="sxs-lookup"><span data-stu-id="a49b0-121">Follow the [installation and usage instructions](welcome-to-mr-feature-tool.md) and select the **Mixed Reality OpenXR Plugin** package in the Mixed Reality Toolkit category:</span></span>

![Finestra pacchetti degli strumenti della funzionalità di realtà mista con plug-in Open XR evidenziato](images/feature-tool-openxr.png)

## <a name="setting-your-build-target"></a><span data-ttu-id="a49b0-123">Impostazione della destinazione di compilazione</span><span class="sxs-lookup"><span data-stu-id="a49b0-123">Setting your build target</span></span>

<span data-ttu-id="a49b0-124">Se la destinazione è Desktop VR, è consigliabile usare la piattaforma autonoma per PC selezionata per impostazione predefinita in un nuovo progetto Unity:</span><span class="sxs-lookup"><span data-stu-id="a49b0-124">If you're targeting Desktop VR, we suggest using the PC Standalone Platform selected by default on a new Unity project:</span></span>

![Screenshot della finestra impostazioni di compilazione aperta nell'editor di Unity con PC, Mac & piattaforma autonoma evidenziata](images/wmr-config-img-3.png)

<span data-ttu-id="a49b0-126">Se la destinazione è HoloLens 2, è necessario passare al piattaforma UWP (Universal Windows Platform):</span><span class="sxs-lookup"><span data-stu-id="a49b0-126">If you're targeting HoloLens 2, you need to switch to the Universal Windows Platform:</span></span>

1.  <span data-ttu-id="a49b0-127">Seleziona **File > impostazioni di compilazione...**</span><span class="sxs-lookup"><span data-stu-id="a49b0-127">Select **File > Build Settings...**</span></span>
2.  <span data-ttu-id="a49b0-128">Selezionare **piattaforma UWP (Universal Windows Platform)** nell'elenco piattaforma e selezionare **Switch Platform (Cambia piattaforma** )</span><span class="sxs-lookup"><span data-stu-id="a49b0-128">Select **Universal Windows Platform** in the Platform list and select **Switch Platform**</span></span>
3.  <span data-ttu-id="a49b0-129">Impostare l' **architettura** su **ARM 64**</span><span class="sxs-lookup"><span data-stu-id="a49b0-129">Set **Architecture** to **ARM 64**</span></span>
4.  <span data-ttu-id="a49b0-130">Impostare il **dispositivo di destinazione** su **HoloLens**</span><span class="sxs-lookup"><span data-stu-id="a49b0-130">Set **Target device** to **HoloLens**</span></span>
5.  <span data-ttu-id="a49b0-131">Imposta **tipo di compilazione** su **D3D**</span><span class="sxs-lookup"><span data-stu-id="a49b0-131">Set **Build Type** to **D3D**</span></span>
6.  <span data-ttu-id="a49b0-132">Impostare **UWP SDK** sull' **ultima versione installata**</span><span class="sxs-lookup"><span data-stu-id="a49b0-132">Set **UWP SDK** to **Latest installed**</span></span>
7.  <span data-ttu-id="a49b0-133">Impostare la **configurazione della compilazione** su **Release** a causa di problemi noti relativi alle prestazioni con debug</span><span class="sxs-lookup"><span data-stu-id="a49b0-133">Set **Build configuration** to **Release** because there are known performance issues with Debug</span></span>

![Screenshot della finestra impostazioni di compilazione aperta nell'editor di Unity con piattaforma UWP (Universal Windows Platform) evidenziato](images/wmr-config-img-4.png)

<span data-ttu-id="a49b0-135">Dopo aver impostato la piattaforma, è necessario consentire a Unity di creare una [visualizzazione immersiva](../../design/app-views.md) anziché una visualizzazione 2D quando viene esportata.</span><span class="sxs-lookup"><span data-stu-id="a49b0-135">After setting your platform, you need to let Unity know to create an [immersive view](../../design/app-views.md) instead of a 2D view when exported.</span></span>

## <a name="configuring-xr-plugin-management-for-openxr"></a><span data-ttu-id="a49b0-136">Configurazione della gestione dei plug-in XR per OpenXR</span><span class="sxs-lookup"><span data-stu-id="a49b0-136">Configuring XR Plugin Management for OpenXR</span></span>

<span data-ttu-id="a49b0-137">Per impostare OpenXR come runtime in Unity:</span><span class="sxs-lookup"><span data-stu-id="a49b0-137">To set OpenXR as the the runtime in Unity:</span></span>

1. <span data-ttu-id="a49b0-138">Nell'editor di Unity passare a **modifica > impostazioni progetto**</span><span class="sxs-lookup"><span data-stu-id="a49b0-138">In the Unity Editor, navigate to **Edit > Project Settings**</span></span>
2. <span data-ttu-id="a49b0-139">Nell'elenco delle impostazioni selezionare **Gestione plug** -in XR</span><span class="sxs-lookup"><span data-stu-id="a49b0-139">In the list of Settings, select **XR Plugin Management**</span></span>
3. <span data-ttu-id="a49b0-140">Selezionare le caselle **Inizializza XR all'avvio** e **OpenXR**</span><span class="sxs-lookup"><span data-stu-id="a49b0-140">Check the **Initialize XR on Startup** and **OpenXR** boxes</span></span>
4. <span data-ttu-id="a49b0-141">Se la destinazione è HoloLens 2, assicurarsi di trovarsi nella piattaforma UWP e selezionare il **set di funzionalità di Microsoft HoloLens**</span><span class="sxs-lookup"><span data-stu-id="a49b0-141">If targeting HoloLens 2, make sure you're on the UWP platform and select **Microsoft HoloLens Feature Set**</span></span>

![Screenshot del pannello Impostazioni progetto aperto nell'editor di Unity con la gestione dei plug-in di XR evidenziata](images/openxr-img-05.png)

## <a name="optimization"></a><span data-ttu-id="a49b0-143">Optimization</span><span class="sxs-lookup"><span data-stu-id="a49b0-143">Optimization</span></span>

<span data-ttu-id="a49b0-144">Se si sta sviluppando per HoloLens 2, passare a **realtà mista> OpenXR > applicare le impostazioni di progetto consigliate per HoloLens 2** per ottenere prestazioni migliori per le app.</span><span class="sxs-lookup"><span data-stu-id="a49b0-144">If you're developing for HoloLens 2, navigate to **Mixed Reality> OpenXR > Apply recommended project settings for HoloLens 2** to get better app performance.</span></span>

![Screenshot della voce di menu della realtà mista aperta con OpenXR selezionato](images/openxr-img-08.png)

> [!IMPORTANT]
> <span data-ttu-id="a49b0-146">Se viene visualizzata un'icona di avviso rossa accanto a plug-in **OpenXR**, fare clic sull'icona e selezionare **Correggi tutto** prima di continuare.</span><span class="sxs-lookup"><span data-stu-id="a49b0-146">If you see a red warning icon next to **OpenXR Plugin**, click the icon and select **Fix all** before continuing.</span></span> <span data-ttu-id="a49b0-147">Per rendere effettive le modifiche, potrebbe essere necessario riavviare l'editor di Unity.</span><span class="sxs-lookup"><span data-stu-id="a49b0-147">The Unity Editor may need to restart itself for the changes to take effect.</span></span>

![Screenshot della finestra di convalida del progetto OpenXR](images/openxr-img-06.png)

<span data-ttu-id="a49b0-149">A questo punto si è pronti per iniziare a sviluppare con OpenXR in Unity.</span><span class="sxs-lookup"><span data-stu-id="a49b0-149">You're now ready to begin developing with OpenXR in Unity!</span></span>  <span data-ttu-id="a49b0-150">Continuare con la sezione successiva per informazioni su come usare gli esempi di OpenXR.</span><span class="sxs-lookup"><span data-stu-id="a49b0-150">Continue on to the next section to learn how to use the OpenXR samples.</span></span>

## <a name="try-out-the-unity-sample-scenes"></a><span data-ttu-id="a49b0-151">Provare le scene di esempio di Unity</span><span class="sxs-lookup"><span data-stu-id="a49b0-151">Try out the Unity sample scenes</span></span>

### <a name="hololens-2-samples"></a><span data-ttu-id="a49b0-152">Esempi di HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="a49b0-152">HoloLens 2 samples</span></span>

1. <span data-ttu-id="a49b0-153">Nell'editor di Unity passare a **finestra > gestione pacchetti**</span><span class="sxs-lookup"><span data-stu-id="a49b0-153">In the Unity Editor, navigate to **Window > Package Manager**</span></span>
2. <span data-ttu-id="a49b0-154">Nell'elenco dei pacchetti selezionare il plug-in **OpenXR realtà mista**</span><span class="sxs-lookup"><span data-stu-id="a49b0-154">In the list of packages, select **Mixed Reality OpenXR Plugin**</span></span>
3. <span data-ttu-id="a49b0-155">Individuare l'esempio nell'elenco degli **esempi** e selezionare **Importa** .</span><span class="sxs-lookup"><span data-stu-id="a49b0-155">Locate the sample in the **Samples** list and select **Import**</span></span>

![Screenshot di gestione pacchetti Unity aperto nell'editor di Unity con la realtà mista OpenXR plug-in selezionato ed esempi pulsante di importazione evidenziato](images/openxr-img-03.png)

<!-- ### For all other OpenXR samples

1. In the Unity Editor, navigate to **Window > Package Manager**
2. In the list of packages, select **OpenXR Plugin**
3. Locate the sample in the **Samples** list and select **Import**

![Screenshot of Unity Package Manager open in Unity editor with OpenXR Plugin selected and samples import button highlighted](images/openxr-img-10.png) -->

> [!NOTE]
> <span data-ttu-id="a49b0-157">Quando viene aggiornato un pacchetto, Unity offre la possibilità di aggiornare gli esempi importati.</span><span class="sxs-lookup"><span data-stu-id="a49b0-157">When a package is updated, Unity provides the option to update imported samples.</span></span>  <span data-ttu-id="a49b0-158">L'aggiornamento di un esempio importato sovrascriverà tutte le modifiche apportate all'esempio e alle risorse associate.</span><span class="sxs-lookup"><span data-stu-id="a49b0-158">Updating an imported sample will overwrite any changes that have been made to the sample and associated assets.</span></span>

## <a name="using-mrtk-with-openxr-support"></a><span data-ttu-id="a49b0-159">Uso di MRTK con il supporto OpenXR</span><span class="sxs-lookup"><span data-stu-id="a49b0-159">Using MRTK with OpenXR support</span></span>

<span data-ttu-id="a49b0-160">MRTK-Unity supporta il plug-in OpenXR realtà mista a partire dalla versione 2.5.3.</span><span class="sxs-lookup"><span data-stu-id="a49b0-160">MRTK-Unity supports the Mixed Reality OpenXR plugin starting with the 2.5.3 release.</span></span>

1. <span data-ttu-id="a49b0-161">Aprire di nuovo lo [strumento della funzionalità di realtà mista](welcome-to-mr-feature-tool.md) per installare il Toolkit di realtà mista, se non è già stato fatto.</span><span class="sxs-lookup"><span data-stu-id="a49b0-161">Open the [Mixed Reality Feature Tool](welcome-to-mr-feature-tool.md) again to install the Mixed Reality Toolkit, if you haven't already.</span></span> <span data-ttu-id="a49b0-162">Il supporto di OpenXR è incluso nel pacchetto di **base** .</span><span class="sxs-lookup"><span data-stu-id="a49b0-162">OpenXR support is in the **Foundation** package.</span></span>
2. <span data-ttu-id="a49b0-163">Passare allo script del componente MixedReality Toolkit nel controllo e passare al profilo **DefaultOpenXRConfigurationProfile** :</span><span class="sxs-lookup"><span data-stu-id="a49b0-163">Go to the MixedReality Toolkit component script in the Inspector and switch to the **DefaultOpenXRConfigurationProfile** profile:</span></span>

    ![Screenshot del cambio della configurazione di MRTK nel componente del Toolkit per realtà mista del controllo](images/openxr-img-11.png)

    1. <span data-ttu-id="a49b0-165">Vedere la documentazione di MRTK per [informazioni più dettagliate sulla migrazione a OpenXR](/windows/mixed-reality/mrtk-unity/configuration/getting-started-with-mrtk-and-xrsdk#configuring-mrtk-for-the-xr-sdk-pipeline).</span><span class="sxs-lookup"><span data-stu-id="a49b0-165">See the MRTK documentation for [more in-depth information on migrating to OpenXR](/windows/mixed-reality/mrtk-unity/configuration/getting-started-with-mrtk-and-xrsdk#configuring-mrtk-for-the-xr-sdk-pipeline).</span></span>

> [!NOTE]
> <span data-ttu-id="a49b0-166">Quando si esegue l'aggiornamento da una versione precedente di MRTK, verificare che la riga seguente si trovi nel file **assets/MixedRealityToolkit. generated/link.xml** :</span><span class="sxs-lookup"><span data-stu-id="a49b0-166">When upgrading from a previous version of MRTK, ensure the following line is in the **Assets/MixedRealityToolkit.Generated/link.xml** file:</span></span>
>
> ```xml
> <assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.OpenXR" preserve="all"/>
> ```
>
> <span data-ttu-id="a49b0-167">Questa riga verrà aggiunta per impostazione predefinita se è stata avviata con MRTK 2.5.4 o versione successiva.</span><span class="sxs-lookup"><span data-stu-id="a49b0-167">This line will be added by default if you started with MRTK 2.5.4 or newer.</span></span>

## <a name="next-steps"></a><span data-ttu-id="a49b0-168">Passaggi successivi</span><span class="sxs-lookup"><span data-stu-id="a49b0-168">Next steps</span></span>

<span data-ttu-id="a49b0-169">Ora che il progetto è stato configurato per OpenXR ed è possibile accedere agli esempi, vedere quali [funzionalità](openxr-supported-features.md) sono attualmente supportate nel plug-in OpenXR.</span><span class="sxs-lookup"><span data-stu-id="a49b0-169">Now that you have your project configured for OpenXR and have access to samples, check out what [features](openxr-supported-features.md) are currently supported in our OpenXR plugin.</span></span>

## <a name="have-feedback"></a><span data-ttu-id="a49b0-170">Inviare commenti e suggerimenti?</span><span class="sxs-lookup"><span data-stu-id="a49b0-170">Have Feedback?</span></span>

<span data-ttu-id="a49b0-171">OpenXR è ancora in fase di sperimentazione, quindi saremmo lieti di ricevere commenti e suggerimenti per aiutarti a migliorarlo.</span><span class="sxs-lookup"><span data-stu-id="a49b0-171">OpenXR is still experimental, so we’d appreciate any feedback you can give us to help make it better.</span></span> <span data-ttu-id="a49b0-172">Ci troviamo nei [Forum di Unity](https://aka.ms/unityforums) contrassegnando il post del forum con **Microsoft**  +  **OpenXR** e **HoloLens 2** o la **realtà mista di Windows**.</span><span class="sxs-lookup"><span data-stu-id="a49b0-172">You'll find us on the [Unity Forums](https://aka.ms/unityforums) by tagging your forum post with **Microsoft** + **OpenXR** and either **HoloLens 2** or **Windows Mixed Reality**.</span></span>

## <a name="see-also"></a><span data-ttu-id="a49b0-173">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="a49b0-173">See also</span></span>

* [<span data-ttu-id="a49b0-174">Configurazione del progetto senza MRTK</span><span class="sxs-lookup"><span data-stu-id="a49b0-174">Configuring your project without MRTK</span></span>](configure-unity-project.md)
* [<span data-ttu-id="a49b0-175">Impostazioni consigliate per Unity</span><span class="sxs-lookup"><span data-stu-id="a49b0-175">Recommended settings for Unity</span></span>](recommended-settings-for-unity.md)
* [<span data-ttu-id="a49b0-176">Consigli sulle prestazioni per Unity</span><span class="sxs-lookup"><span data-stu-id="a49b0-176">Performance recommendations for Unity</span></span>](performance-recommendations-for-unity.md#how-to-profile-with-unity)

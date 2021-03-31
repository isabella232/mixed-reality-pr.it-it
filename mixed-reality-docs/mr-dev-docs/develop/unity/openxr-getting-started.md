---
title: Uso del plug-in OpenXR per la realtà mista per Unity
description: Informazioni su come abilitare il plug-in OpenXR per la realtà mista per i progetti Unity.
author: hferrone
ms.author: alexturn
ms.date: 01/11/2021
ms.topic: article
keywords: openxr, Unity, hololens, hololens 2, realtà mista, MRTK, Toolkit per realtà mista, realtà aumentata, realtà virtuale, cuffie con realtà mista, informazioni, esercitazione, introduzione
ms.openlocfilehash: 6e300c6117e04e2a49b060bcd7a6d268204f14da
ms.sourcegitcommit: 6272d086a2856e8b514a719e1f9e3b78554be5be
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/30/2021
ms.locfileid: "105937476"
---
# <a name="using-the-mixed-reality-openxr-plugin-for-unity"></a><span data-ttu-id="76717-104">Uso del plug-in OpenXR per la realtà mista per Unity</span><span class="sxs-lookup"><span data-stu-id="76717-104">Using the Mixed Reality OpenXR Plugin for Unity</span></span>

<span data-ttu-id="76717-105">A partire da Unity versione 2020,2, il pacchetto di plug-in per la realtà mista di Microsoft OpenXR è disponibile tramite Gestione pacchetti Unity (UPM).</span><span class="sxs-lookup"><span data-stu-id="76717-105">Starting with Unity version 2020.2, Microsoft’s Mixed Reality OpenXR Plugin package is available using the Unity Package Manager (UPM).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="76717-106">Prerequisiti</span><span class="sxs-lookup"><span data-stu-id="76717-106">Prerequisites</span></span>

* <span data-ttu-id="76717-107">Unity 2020,3 LTS o versione successiva</span><span class="sxs-lookup"><span data-stu-id="76717-107">Unity 2020.3 LTS or later</span></span>
* <span data-ttu-id="76717-108">Plug-in OpenXR Unity 1.0.3 o versione successiva</span><span class="sxs-lookup"><span data-stu-id="76717-108">Unity OpenXR plugin 1.0.3 or later</span></span>
* <span data-ttu-id="76717-109">Visual Studio 2019 o versione successiva</span><span class="sxs-lookup"><span data-stu-id="76717-109">Visual Studio 2019 or later</span></span>
* <span data-ttu-id="76717-110">Installare il supporto della piattaforma **UWP** in Unity per le app HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="76717-110">Install **UWP** platform support in Unity for HoloLens 2 apps</span></span>

> [!NOTE]
> <span data-ttu-id="76717-111">Se si stanno compilando applicazioni VR in PC Windows, il plug-in OpenXR per realtà mista non è necessariamente obbligatorio.</span><span class="sxs-lookup"><span data-stu-id="76717-111">If you're building VR applications on Windows PC, the Mixed Reality OpenXR plugin is not necessarily required.</span></span> <span data-ttu-id="76717-112">Tuttavia, è necessario installare il plug-in se si sta personalizzando il mapping del controller per i controller HP Reverb G2 o la creazione di app che funzionano sia con le cuffie HoloLens 2 sia con le cuffie VR.</span><span class="sxs-lookup"><span data-stu-id="76717-112">However, you'll want to install the plugin if you're customizing controller mapping for HP Reverb G2 controllers or building apps that work on both HoloLens 2 and VR headsets.</span></span>

<!-- ## Setting up your project with MRTK

MRTK for Unity provides a cross-platform input system, foundational components, and common building blocks for spatial interactions. MRTK version 2 intends to speed up application development for Microsoft HoloLens, Windows Mixed Reality immersive (VR) headsets, and OpenVR platform. The project is aimed at reducing barriers to entry, creating mixed reality applications, and contributing back to the community as we all grow.

> [!div class="nextstepaction"]
> [Set up your project using MRTK](tutorials/mr-learning-base-01.md)

Take a look at [MRTK's documentation](/windows/mixed-reality/mrtk-unity) for more feature details. -->

## <a name="manual-setup-without-mrtk"></a><span data-ttu-id="76717-113">Installazione manuale senza MRTK</span><span class="sxs-lookup"><span data-stu-id="76717-113">Manual setup without MRTK</span></span>

<span data-ttu-id="76717-114">Installare il plug-in OpenXR con la nuova applicazione dello strumento per la funzionalità di realtà mista.</span><span class="sxs-lookup"><span data-stu-id="76717-114">Install the OpenXR plugin with the new Mixed Reality Feature Tool application.</span></span> <span data-ttu-id="76717-115">Seguire le [istruzioni per l'installazione e l'utilizzo](welcome-to-mr-feature-tool.md) e selezionare il pacchetto di plug-in **realtà mista OpenXR** nella categoria del Toolkit di realtà mista:</span><span class="sxs-lookup"><span data-stu-id="76717-115">Follow the [installation and usage instructions](welcome-to-mr-feature-tool.md) and select the **Mixed Reality OpenXR Plugin** package in the Mixed Reality Toolkit category:</span></span>

![Finestra pacchetti degli strumenti della funzionalità di realtà mista con plug-in Open XR evidenziato](images/feature-tool-openxr.png)

## <a name="setting-your-build-target"></a><span data-ttu-id="76717-117">Impostazione della destinazione di compilazione</span><span class="sxs-lookup"><span data-stu-id="76717-117">Setting your build target</span></span>

<span data-ttu-id="76717-118">Se la destinazione è Desktop VR, è consigliabile usare la piattaforma autonoma per PC selezionata per impostazione predefinita in un nuovo progetto Unity:</span><span class="sxs-lookup"><span data-stu-id="76717-118">If you're targeting Desktop VR, we suggest using the PC Standalone Platform selected by default on a new Unity project:</span></span>

![Screenshot della finestra impostazioni di compilazione aperta nell'editor di Unity con PC, Mac & piattaforma autonoma evidenziata](images/wmr-config-img-3.png)

<span data-ttu-id="76717-120">Se la destinazione è HoloLens 2, è necessario passare al piattaforma UWP (Universal Windows Platform):</span><span class="sxs-lookup"><span data-stu-id="76717-120">If you're targeting HoloLens 2, you need to switch to the Universal Windows Platform:</span></span>

1.  <span data-ttu-id="76717-121">Seleziona **File > impostazioni di compilazione...**</span><span class="sxs-lookup"><span data-stu-id="76717-121">Select **File > Build Settings...**</span></span>
2.  <span data-ttu-id="76717-122">Selezionare **piattaforma UWP (Universal Windows Platform)** nell'elenco piattaforma e selezionare **Switch Platform (Cambia piattaforma** )</span><span class="sxs-lookup"><span data-stu-id="76717-122">Select **Universal Windows Platform** in the Platform list and select **Switch Platform**</span></span>
3.  <span data-ttu-id="76717-123">Impostare l' **architettura** su **ARM 64**</span><span class="sxs-lookup"><span data-stu-id="76717-123">Set **Architecture** to **ARM 64**</span></span>
4.  <span data-ttu-id="76717-124">Impostare il **dispositivo di destinazione** su **HoloLens**</span><span class="sxs-lookup"><span data-stu-id="76717-124">Set **Target device** to **HoloLens**</span></span>
5.  <span data-ttu-id="76717-125">Imposta **tipo di compilazione** su **D3D**</span><span class="sxs-lookup"><span data-stu-id="76717-125">Set **Build Type** to **D3D**</span></span>
6.  <span data-ttu-id="76717-126">Impostare **UWP SDK** sull' **ultima versione installata**</span><span class="sxs-lookup"><span data-stu-id="76717-126">Set **UWP SDK** to **Latest installed**</span></span>
7.  <span data-ttu-id="76717-127">Impostare la **configurazione della compilazione** su **Release** a causa di problemi noti relativi alle prestazioni con debug</span><span class="sxs-lookup"><span data-stu-id="76717-127">Set **Build configuration** to **Release** because there are known performance issues with Debug</span></span>

![Screenshot della finestra impostazioni di compilazione aperta nell'editor di Unity con piattaforma UWP (Universal Windows Platform) evidenziato](images/wmr-config-img-4.png)

<span data-ttu-id="76717-129">Dopo aver impostato la piattaforma, è necessario consentire a Unity di creare una [visualizzazione immersiva](../../design/app-views.md) anziché una visualizzazione 2D quando viene esportata.</span><span class="sxs-lookup"><span data-stu-id="76717-129">After setting your platform, you need to let Unity know to create an [immersive view](../../design/app-views.md) instead of a 2D view when exported.</span></span>

## <a name="configuring-xr-plugin-management-for-openxr"></a><span data-ttu-id="76717-130">Configurazione della gestione dei plug-in XR per OpenXR</span><span class="sxs-lookup"><span data-stu-id="76717-130">Configuring XR Plugin Management for OpenXR</span></span>

<span data-ttu-id="76717-131">Per impostare OpenXR come runtime in Unity:</span><span class="sxs-lookup"><span data-stu-id="76717-131">To set OpenXR as the the runtime in Unity:</span></span>

1. <span data-ttu-id="76717-132">Nell'editor di Unity passare a **modifica > impostazioni progetto**</span><span class="sxs-lookup"><span data-stu-id="76717-132">In the Unity Editor, navigate to **Edit > Project Settings**</span></span>
2. <span data-ttu-id="76717-133">Nell'elenco delle impostazioni selezionare **Gestione plug** -in XR</span><span class="sxs-lookup"><span data-stu-id="76717-133">In the list of Settings, select **XR Plugin Management**</span></span>
3. <span data-ttu-id="76717-134">Selezionare le caselle **Inizializza XR all'avvio** e **OpenXR**</span><span class="sxs-lookup"><span data-stu-id="76717-134">Check the **Initialize XR on Startup** and **OpenXR** boxes</span></span>
4. <span data-ttu-id="76717-135">Se la destinazione è HoloLens 2, assicurarsi di trovarsi nella piattaforma UWP e selezionare il **set di funzionalità di Microsoft HoloLens**</span><span class="sxs-lookup"><span data-stu-id="76717-135">If targeting HoloLens 2, make sure you're on the UWP platform and select **Microsoft HoloLens Feature Set**</span></span>

![Screenshot del pannello Impostazioni progetto aperto nell'editor di Unity con la gestione dei plug-in di XR evidenziata](images/openxr-img-05.png)

## <a name="optimization"></a><span data-ttu-id="76717-137">Optimization</span><span class="sxs-lookup"><span data-stu-id="76717-137">Optimization</span></span>

<span data-ttu-id="76717-138">Se si sta sviluppando per HoloLens 2, passare a **realtà mista> OpenXR > applicare le impostazioni di progetto consigliate per HoloLens 2** per ottenere prestazioni migliori per le app.</span><span class="sxs-lookup"><span data-stu-id="76717-138">If you're developing for HoloLens 2, navigate to **Mixed Reality> OpenXR > Apply recommended project settings for HoloLens 2** to get better app performance.</span></span>

![Screenshot della voce di menu della realtà mista aperta con OpenXR selezionato](images/openxr-img-08.png)

> [!IMPORTANT]
> <span data-ttu-id="76717-140">Se viene visualizzata un'icona di avviso rossa accanto a plug-in **OpenXR (anteprima)**, fare clic sull'icona e selezionare **Correggi tutto** prima di continuare.</span><span class="sxs-lookup"><span data-stu-id="76717-140">If you see a red warning icon next to **OpenXR Plugin (Preview)**, click the icon and select **Fix all** before continuing.</span></span> <span data-ttu-id="76717-141">Per rendere effettive le modifiche, potrebbe essere necessario riavviare l'editor di Unity.</span><span class="sxs-lookup"><span data-stu-id="76717-141">The Unity Editor may need to restart itself for the changes to take effect.</span></span>

![Screenshot della finestra di convalida del progetto OpenXR](images/openxr-img-06.png)

<span data-ttu-id="76717-143">A questo punto si è pronti per iniziare a sviluppare con OpenXR in Unity.</span><span class="sxs-lookup"><span data-stu-id="76717-143">You're now ready to begin developing with OpenXR in Unity!</span></span>  <span data-ttu-id="76717-144">Continuare con la sezione successiva per informazioni su come usare gli esempi di OpenXR.</span><span class="sxs-lookup"><span data-stu-id="76717-144">Continue on to the next section to learn how to use the OpenXR samples.</span></span>

## <a name="try-out-the-unity-sample-scenes"></a><span data-ttu-id="76717-145">Provare le scene di esempio di Unity</span><span class="sxs-lookup"><span data-stu-id="76717-145">Try out the Unity sample scenes</span></span>

### <a name="hololens-2-samples"></a><span data-ttu-id="76717-146">Esempi di HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="76717-146">HoloLens 2 samples</span></span>

1. <span data-ttu-id="76717-147">Nell'editor di Unity passare a **finestra > gestione pacchetti**</span><span class="sxs-lookup"><span data-stu-id="76717-147">In the Unity Editor, navigate to **Window > Package Manager**</span></span>
2. <span data-ttu-id="76717-148">Nell'elenco dei pacchetti selezionare il plug-in **OpenXR realtà mista**</span><span class="sxs-lookup"><span data-stu-id="76717-148">In the list of packages, select **Mixed Reality OpenXR Plugin**</span></span>
3. <span data-ttu-id="76717-149">Individuare l'esempio nell'elenco degli **esempi** e selezionare **Importa** .</span><span class="sxs-lookup"><span data-stu-id="76717-149">Locate the sample in the **Samples** list and select **Import**</span></span>

![Screenshot di gestione pacchetti Unity aperto nell'editor di Unity con la realtà mista OpenXR plug-in selezionato ed esempi pulsante di importazione evidenziato](images/openxr-img-03.png)

<!-- ### For all other OpenXR samples

1. In the Unity Editor, navigate to **Window > Package Manager**
2. In the list of packages, select **OpenXR Plugin**
3. Locate the sample in the **Samples** list and select **Import**

![Screenshot of Unity Package Manager open in Unity editor with OpenXR Plugin selected and samples import button highlighted](images/openxr-img-10.png) -->

> [!NOTE]
> <span data-ttu-id="76717-151">Quando viene aggiornato un pacchetto, Unity offre la possibilità di aggiornare gli esempi importati.</span><span class="sxs-lookup"><span data-stu-id="76717-151">When a package is updated, Unity provides the option to update imported samples.</span></span>  <span data-ttu-id="76717-152">L'aggiornamento di un esempio importato sovrascriverà tutte le modifiche apportate all'esempio e alle risorse associate.</span><span class="sxs-lookup"><span data-stu-id="76717-152">Updating an imported sample will overwrite any changes that have been made to the sample and associated assets.</span></span>

## <a name="using-mrtk-with-openxr-support"></a><span data-ttu-id="76717-153">Uso di MRTK con il supporto OpenXR</span><span class="sxs-lookup"><span data-stu-id="76717-153">Using MRTK with OpenXR support</span></span>

<span data-ttu-id="76717-154">MRTK-Unity supporta il plug-in OpenXR realtà mista a partire dalla versione 2.5.3.</span><span class="sxs-lookup"><span data-stu-id="76717-154">MRTK-Unity supports the Mixed Reality OpenXR plugin starting with the 2.5.3 release.</span></span>

1. <span data-ttu-id="76717-155">Aprire di nuovo lo [strumento della funzionalità di realtà mista](welcome-to-mr-feature-tool.md) per installare il Toolkit di realtà mista, se non è già stato fatto.</span><span class="sxs-lookup"><span data-stu-id="76717-155">Open the [Mixed Reality Feature Tool](welcome-to-mr-feature-tool.md) again to install the Mixed Reality Toolkit, if you haven't already.</span></span> <span data-ttu-id="76717-156">Il supporto di OpenXR è incluso nel pacchetto di **base** .</span><span class="sxs-lookup"><span data-stu-id="76717-156">OpenXR support is in the **Foundation** package.</span></span>
2. <span data-ttu-id="76717-157">Passare allo script del componente MixedReality Toolkit nel controllo e passare al profilo **DefaultOpenXRConfigurationProfile** :</span><span class="sxs-lookup"><span data-stu-id="76717-157">Go to the MixedReality Toolkit component script in the Inspector and switch to the **DefaultOpenXRConfigurationProfile** profile:</span></span>

    ![Screenshot del cambio della configurazione di MRTK nel componente del Toolkit per realtà mista del controllo](images/openxr-img-11.png)

    1. <span data-ttu-id="76717-159">Vedere la documentazione di MRTK per [informazioni più dettagliate sulla migrazione a OpenXR](/windows/mixed-reality/mrtk-unity/configuration/getting-started-with-mrtk-and-xrsdk#configuring-mrtk-for-the-xr-sdk-pipeline).</span><span class="sxs-lookup"><span data-stu-id="76717-159">See the MRTK documentation for [more in-depth information on migrating to OpenXR](/windows/mixed-reality/mrtk-unity/configuration/getting-started-with-mrtk-and-xrsdk#configuring-mrtk-for-the-xr-sdk-pipeline).</span></span>

> [!NOTE]
> <span data-ttu-id="76717-160">Quando si esegue l'aggiornamento da una versione precedente di MRTK, verificare che la riga seguente si trovi nel file **assets/MixedRealityToolkit. generated/link.xml** :</span><span class="sxs-lookup"><span data-stu-id="76717-160">When upgrading from a previous version of MRTK, ensure the following line is in the **Assets/MixedRealityToolkit.Generated/link.xml** file:</span></span>
>
> ```xml
> <assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.OpenXR" preserve="all"/>
> ```
>
> <span data-ttu-id="76717-161">Questa riga verrà aggiunta per impostazione predefinita se è stata avviata con MRTK 2.5.4 o versione successiva.</span><span class="sxs-lookup"><span data-stu-id="76717-161">This line will be added by default if you started with MRTK 2.5.4 or newer.</span></span>

## <a name="next-steps"></a><span data-ttu-id="76717-162">Passaggi successivi</span><span class="sxs-lookup"><span data-stu-id="76717-162">Next steps</span></span>

<span data-ttu-id="76717-163">Ora che il progetto è stato configurato per OpenXR ed è possibile accedere agli esempi, vedere quali [funzionalità](openxr-supported-features.md) sono attualmente supportate nel plug-in OpenXR.</span><span class="sxs-lookup"><span data-stu-id="76717-163">Now that you have your project configured for OpenXR and have access to samples, check out what [features](openxr-supported-features.md) are currently supported in our OpenXR plugin.</span></span>

## <a name="have-feedback"></a><span data-ttu-id="76717-164">Inviare commenti e suggerimenti?</span><span class="sxs-lookup"><span data-stu-id="76717-164">Have Feedback?</span></span>

<span data-ttu-id="76717-165">OpenXR è ancora in fase di sperimentazione, quindi saremmo lieti di ricevere commenti e suggerimenti per aiutarti a migliorarlo.</span><span class="sxs-lookup"><span data-stu-id="76717-165">OpenXR is still experimental, so we’d appreciate any feedback you can give us to help make it better.</span></span> <span data-ttu-id="76717-166">Ci troviamo nei [Forum di Unity](https://aka.ms/unityforums) contrassegnando il post del forum con **Microsoft**  +  **OpenXR** e **HoloLens 2** o la **realtà mista di Windows**.</span><span class="sxs-lookup"><span data-stu-id="76717-166">You'll find us on the [Unity Forums](https://aka.ms/unityforums) by tagging your forum post with **Microsoft** + **OpenXR** and either **HoloLens 2** or **Windows Mixed Reality**.</span></span>

## <a name="see-also"></a><span data-ttu-id="76717-167">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="76717-167">See also</span></span>

* [<span data-ttu-id="76717-168">Configurazione del progetto senza MRTK</span><span class="sxs-lookup"><span data-stu-id="76717-168">Configuring your project without MRTK</span></span>](configure-unity-project.md)
* [<span data-ttu-id="76717-169">Impostazioni consigliate per Unity</span><span class="sxs-lookup"><span data-stu-id="76717-169">Recommended settings for Unity</span></span>](recommended-settings-for-unity.md)
* [<span data-ttu-id="76717-170">Consigli sulle prestazioni per Unity</span><span class="sxs-lookup"><span data-stu-id="76717-170">Performance recommendations for Unity</span></span>](performance-recommendations-for-unity.md#how-to-profile-with-unity)

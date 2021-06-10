---
title: Uso del plug-in Mixed Reality OpenXR
description: Informazioni su come abilitare il plug-in OpenXR di Realtà mista per i progetti Unity.
author: hferrone
ms.author: alexturn
ms.date: 01/11/2021
ms.topic: article
keywords: openxr, unity, hololens, hololens 2, realtà mista, MRTK, Mixed Reality Toolkit, realtà aumentata, realtà virtuale, visori VR di realtà mista, apprendimento, esercitazione, introduzione
ms.openlocfilehash: 65b79aadeb52db6be61edcc90a5d4a44c12384a1
ms.sourcegitcommit: 5617575cf550dd03fba0bfd5263e97972dcc646b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/06/2021
ms.locfileid: "111547039"
---
# <a name="using-the-mixed-reality-openxr-plugin"></a><span data-ttu-id="ec99c-104">Uso del plug-in Mixed Reality OpenXR</span><span class="sxs-lookup"><span data-stu-id="ec99c-104">Using the Mixed Reality OpenXR Plugin</span></span>

<span data-ttu-id="ec99c-105">Per gli sviluppatori che hanno come destinazione Unity 2020 la creazione di applicazioni HoloLens 2 o realtà mista, è possibile usare il plug-in OpenXR invece del plug-in WindowsXR per una migliore compatibilità multipiattaforma.</span><span class="sxs-lookup"><span data-stu-id="ec99c-105">For developers targeting Unity 2020 to build HoloLens 2 or Mixed Reality applications, OpenXR plugin can be used instead of WindowsXR plugin for better cross platform compatibilities.</span></span>  <span data-ttu-id="ec99c-106">Il plug-in OpenXR di Realtà mista funziona bene anche con la versione più recente di [Mixed Reality Toolkit 2.7.](/windows/mixed-reality/mrtk-unity)</span><span class="sxs-lookup"><span data-stu-id="ec99c-106">The Mixed Reality OpenXR Plugin also works well with latest [Mixed Reality Toolkit 2.7](/windows/mixed-reality/mrtk-unity).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="ec99c-107">Prerequisiti</span><span class="sxs-lookup"><span data-stu-id="ec99c-107">Prerequisites</span></span>

* <span data-ttu-id="ec99c-108">Versione più recente di Unity 2020.3 LTS (è consigliabile usare 2020.3.8f1 o versione superiore)</span><span class="sxs-lookup"><span data-stu-id="ec99c-108">Latest Unity 2020.3 LTS, (we recommend 2020.3.8f1 or above)</span></span>
* <span data-ttu-id="ec99c-109">Plug-in Unity OpenXR più recente (è consigliabile usare la versione 1.2 o successiva)</span><span class="sxs-lookup"><span data-stu-id="ec99c-109">Latest Unity OpenXR plugin, (we recommend 1.2 or later)</span></span>
* <span data-ttu-id="ec99c-110">Strumenti [più recenti per HoloLens 2 sviluppo](/windows/mixed-reality/develop/install-the-tools?tabs=unity#installation-checklist)</span><span class="sxs-lookup"><span data-stu-id="ec99c-110">Latest [tools for HoloLens 2 development](/windows/mixed-reality/develop/install-the-tools?tabs=unity#installation-checklist)</span></span>
* <span data-ttu-id="ec99c-111">MrTK più recente (facoltativo), (è consigliabile la versione 2.7 o successiva)</span><span class="sxs-lookup"><span data-stu-id="ec99c-111">Latest MRTK (optional), (we recommend version 2.7 or later)</span></span>
* <span data-ttu-id="ec99c-112">Plug-in OpenXR di realtà mista più recente (è consigliabile usare la versione 1.0.0-preview.1 o successiva)</span><span class="sxs-lookup"><span data-stu-id="ec99c-112">Latest Mixed Reality OpenXR Plugin, (we recommend version 1.0.0-preview.1 or later)</span></span>

![Screenshot dell'esempio di base xr unity aperto in esecuzione in holoLens](images/openxr-example.png)

> [!NOTE]
> <span data-ttu-id="ec99c-114">Se si compilano applicazioni di realtà virtuale in PC Windows, il plug-in OpenXR di Realtà mista non è necessariamente necessario.</span><span class="sxs-lookup"><span data-stu-id="ec99c-114">If you're building VR applications on Windows PC, the Mixed Reality OpenXR plugin is not necessarily required.</span></span> <span data-ttu-id="ec99c-115">Tuttavia, è necessario installare il plug-in se si personalizza il mapping del controller per i controller HP Reverb G2 o si compilano app che funzionano sia su visori VR HoloLens 2 che su visori VR.</span><span class="sxs-lookup"><span data-stu-id="ec99c-115">However, you'll want to install the plugin if you're customizing controller mapping for HP Reverb G2 controllers or building apps that work on both HoloLens 2 and VR headsets.</span></span>

## <a name="setting-up-your-project-with-mrtk"></a><span data-ttu-id="ec99c-116">Configurazione del progetto con MRTK</span><span class="sxs-lookup"><span data-stu-id="ec99c-116">Setting up your project with MRTK</span></span>

<span data-ttu-id="ec99c-117">MRTK per Unity offre un sistema di input multipiattaforma, componenti fondamentali e blocchi predefiniti comuni per le interazioni spaziali.</span><span class="sxs-lookup"><span data-stu-id="ec99c-117">MRTK for Unity provides a cross-platform input system, foundational components, and common building blocks for spatial interactions.</span></span> <span data-ttu-id="ec99c-118">MRTK versione 2 intende accelerare lo sviluppo di applicazioni per Microsoft HoloLens, i visori VR immersive di Windows Mixed Reality e la piattaforma OpenVR.</span><span class="sxs-lookup"><span data-stu-id="ec99c-118">MRTK version 2 intends to speed up application development for Microsoft HoloLens, Windows Mixed Reality immersive (VR) headsets, and OpenVR platform.</span></span> <span data-ttu-id="ec99c-119">Il progetto mira a ridurre le barriere di accesso, creare applicazioni di realtà mista e restituire contributi alla community per continuare a crescere insieme.</span><span class="sxs-lookup"><span data-stu-id="ec99c-119">The project is aimed at reducing barriers to entry, creating mixed reality applications, and contributing back to the community as we all grow.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="ec99c-120">Configurare il progetto con MRTK</span><span class="sxs-lookup"><span data-stu-id="ec99c-120">Set up your project using MRTK</span></span>](./tutorials/mr-learning-base-02.md?tabs=openxr)

<span data-ttu-id="ec99c-121">Per altri dettagli sulle funzionalità, vedere la documentazione di [MRTK.](/windows/mixed-reality/mrtk-unity)</span><span class="sxs-lookup"><span data-stu-id="ec99c-121">Take a look at [MRTK's documentation](/windows/mixed-reality/mrtk-unity) for more feature details.</span></span>

## <a name="manual-setup-without-mrtk"></a><span data-ttu-id="ec99c-122">Configurazione manuale senza MRTK</span><span class="sxs-lookup"><span data-stu-id="ec99c-122">Manual setup without MRTK</span></span>

<span data-ttu-id="ec99c-123">Installare il plug-in OpenXR con la nuova applicazione Mixed Reality Feature Tool.</span><span class="sxs-lookup"><span data-stu-id="ec99c-123">Install the OpenXR plugin with the new Mixed Reality Feature Tool application.</span></span> <span data-ttu-id="ec99c-124">Seguire le [istruzioni di installazione e utilizzo](welcome-to-mr-feature-tool.md) e selezionare il pacchetto Mixed Reality **OpenXR Plugin** nella categoria Mixed Reality Toolkit:</span><span class="sxs-lookup"><span data-stu-id="ec99c-124">Follow the [installation and usage instructions](welcome-to-mr-feature-tool.md) and select the **Mixed Reality OpenXR Plugin** package in the Mixed Reality Toolkit category:</span></span>

![Finestra dei pacchetti degli strumenti di funzionalità di realtà mista con il plug-in xr aperto evidenziato](images/feature-tool-openxr.png)

## <a name="setting-your-build-target"></a><span data-ttu-id="ec99c-126">Impostazione della destinazione di compilazione</span><span class="sxs-lookup"><span data-stu-id="ec99c-126">Setting your build target</span></span>

<span data-ttu-id="ec99c-127">Se si usa la realtà virtuale desktop come destinazione, è consigliabile usare la piattaforma pc autonoma selezionata per impostazione predefinita in un nuovo progetto Unity:</span><span class="sxs-lookup"><span data-stu-id="ec99c-127">If you're targeting Desktop VR, we suggest using the PC Standalone Platform selected by default on a new Unity project:</span></span>

![Screenshot della finestra Build Settings (Impostazioni di compilazione) aperta nell'editor di Unity con PC, Mac & piattaforma autonoma evidenziata](images/wmr-config-img-3.png)

<span data-ttu-id="ec99c-129">Se la destinazione è HoloLens 2, è necessario passare al piattaforma UWP (Universal Windows Platform):</span><span class="sxs-lookup"><span data-stu-id="ec99c-129">If you're targeting HoloLens 2, you need to switch to the Universal Windows Platform:</span></span>

1. <span data-ttu-id="ec99c-130">Selezionare **Impostazioni > file...**</span><span class="sxs-lookup"><span data-stu-id="ec99c-130">Select **File > Build Settings...**</span></span>
2. <span data-ttu-id="ec99c-131">Selezionare **piattaforma UWP (Universal Windows Platform)** nell'elenco Piattaforma e selezionare **Cambia piattaforma**</span><span class="sxs-lookup"><span data-stu-id="ec99c-131">Select **Universal Windows Platform** in the Platform list and select **Switch Platform**</span></span>
3. <span data-ttu-id="ec99c-132">Impostare **Architecture (Architettura)** **su ARM 64**</span><span class="sxs-lookup"><span data-stu-id="ec99c-132">Set **Architecture** to **ARM 64**</span></span>
4. <span data-ttu-id="ec99c-133">Impostare **Dispositivo di destinazione** su **HoloLens**</span><span class="sxs-lookup"><span data-stu-id="ec99c-133">Set **Target device** to **HoloLens**</span></span>
5. <span data-ttu-id="ec99c-134">Impostare **Tipo di compilazione** su **D3D**</span><span class="sxs-lookup"><span data-stu-id="ec99c-134">Set **Build Type** to **D3D**</span></span>
6. <span data-ttu-id="ec99c-135">Impostare **UWP SDK su** Latest installed **(Versione più recente installata)**</span><span class="sxs-lookup"><span data-stu-id="ec99c-135">Set **UWP SDK** to **Latest installed**</span></span>

![Screenshot della finestra Build Settings (Impostazioni di compilazione) aperta nell'editor di Unity con piattaforma UWP (Universal Windows Platform) evidenziato](images/wmr-config-img-4.png)

## <a name="configuring-xr-plugin-management-for-openxr"></a><span data-ttu-id="ec99c-137">Configurazione della gestione dei plug-in XR per OpenXR</span><span class="sxs-lookup"><span data-stu-id="ec99c-137">Configuring XR Plugin Management for OpenXR</span></span>

<span data-ttu-id="ec99c-138">Per impostare OpenXR come runtime in Unity:</span><span class="sxs-lookup"><span data-stu-id="ec99c-138">To set OpenXR as the the runtime in Unity:</span></span>

1. <span data-ttu-id="ec99c-139">Nell'editor di Unity passare a **Edit > Project Settings (Modifica impostazioni progetto)**</span><span class="sxs-lookup"><span data-stu-id="ec99c-139">In the Unity Editor, navigate to **Edit > Project Settings**</span></span>
2. <span data-ttu-id="ec99c-140">Nell'elenco delle impostazioni selezionare **XR Plugin Management (Gestione plug-in XR)**</span><span class="sxs-lookup"><span data-stu-id="ec99c-140">In the list of Settings, select **XR Plugin Management**</span></span>
3. <span data-ttu-id="ec99c-141">Selezionare le **caselle Inizializza XR all'avvio** **e OpenXR**</span><span class="sxs-lookup"><span data-stu-id="ec99c-141">Check the **Initialize XR on Startup** and **OpenXR** boxes</span></span>
4. <span data-ttu-id="ec99c-142">Se la destinazione HoloLens 2, assicurarsi di essere nella piattaforma UWP e selezionare Microsoft HoloLens **set di funzionalità**</span><span class="sxs-lookup"><span data-stu-id="ec99c-142">If targeting HoloLens 2, make sure you're on the UWP platform and select **Microsoft HoloLens Feature Set**</span></span>

![Screenshot del pannello delle impostazioni del progetto aperto nell'editor di Unity con gestione plug-in XR evidenziata](images/openxr-img-05.png)

## <a name="optimization"></a><span data-ttu-id="ec99c-144">Optimization</span><span class="sxs-lookup"><span data-stu-id="ec99c-144">Optimization</span></span>

<span data-ttu-id="ec99c-145">Se stai sviluppando per HoloLens 2, passa a **Mixed Reality> OpenXR > Apply recommended project settings for HoloLens 2** (Applica le impostazioni di progetto consigliate per HoloLens 2 per ottenere prestazioni migliori per le app).</span><span class="sxs-lookup"><span data-stu-id="ec99c-145">If you're developing for HoloLens 2, navigate to **Mixed Reality> OpenXR > Apply recommended project settings for HoloLens 2** to get better app performance.</span></span>

![Screenshot della voce di menu di realtà mista aperta con OpenXR selezionato](images/openxr-img-08.png)

> [!IMPORTANT]
> <span data-ttu-id="ec99c-147">Se viene visualizzata un'icona di avviso rossa accanto a **Plug-in OpenXR,** fare clic sull'icona e **selezionare Correggi tutto** prima di continuare.</span><span class="sxs-lookup"><span data-stu-id="ec99c-147">If you see a red warning icon next to **OpenXR Plugin**, click the icon and select **Fix all** before continuing.</span></span> <span data-ttu-id="ec99c-148">Per l'applicazione delle modifiche, potrebbe essere necessario riavviare l'editor di Unity.</span><span class="sxs-lookup"><span data-stu-id="ec99c-148">The Unity Editor may need to restart itself for the changes to take effect.</span></span>

![Screenshot della finestra di convalida del progetto OpenXR](images/openxr-img-06.png)

<span data-ttu-id="ec99c-150">A questo punto è possibile iniziare a sviluppare con OpenXR in Unity.</span><span class="sxs-lookup"><span data-stu-id="ec99c-150">You're now ready to begin developing with OpenXR in Unity!</span></span>  <span data-ttu-id="ec99c-151">Continuare con la sezione successiva per informazioni su come usare gli esempi di OpenXR.</span><span class="sxs-lookup"><span data-stu-id="ec99c-151">Continue on to the next section to learn how to use the OpenXR samples.</span></span>

## <a name="unity-sample-projects-for-openxr-and-hololens-2"></a><span data-ttu-id="ec99c-152">Progetti di esempio Unity per OpenXR e HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="ec99c-152">Unity sample projects for OpenXR and HoloLens 2</span></span>

<span data-ttu-id="ec99c-153">Consulta il repo di esempi di [OpenXR Mixed Reality](https://github.com/microsoft/OpenXR-Unity-MixedReality-Samples) per progetti Unity di esempio che illustrano come compilare applicazioni Unity per HoloLens 2 o visori VR di realtà mista usando il plug-in OpenXR di Realtà mista.</span><span class="sxs-lookup"><span data-stu-id="ec99c-153">Check out the [OpenXR Mixed Reality samples repo](https://github.com/microsoft/OpenXR-Unity-MixedReality-Samples) for sample unity projects showcasing how to build Unity applications for HoloLens 2 or Mixed Reality headsets using the Mixed Reality OpenXR plugin.</span></span>

## <a name="using-mrtk-with-openxr-support"></a><span data-ttu-id="ec99c-154">Uso di MRTK con il supporto di OpenXR</span><span class="sxs-lookup"><span data-stu-id="ec99c-154">Using MRTK with OpenXR support</span></span>

<span data-ttu-id="ec99c-155">MRTK per Unity versione 2.7 ora supporta ufficialmente il plug-in OpenXR di Realtà mista.</span><span class="sxs-lookup"><span data-stu-id="ec99c-155">MRTK for Unity version 2.7 now officially supports the Mixed Reality OpenXR plugin.</span></span>

<span data-ttu-id="ec99c-156">Aprire di [nuovo Mixed Reality Feature Tool](welcome-to-mr-feature-tool.md) per installare Mixed Reality Toolkit, se non è già stato fatto.</span><span class="sxs-lookup"><span data-stu-id="ec99c-156">Open the [Mixed Reality Feature Tool](welcome-to-mr-feature-tool.md) again to install the Mixed Reality Toolkit, if you haven't already.</span></span> <span data-ttu-id="ec99c-157">Il supporto di OpenXR è in pacchetto **Foundation.**</span><span class="sxs-lookup"><span data-stu-id="ec99c-157">OpenXR support is in the **Foundation** package.</span></span>

![Finestra delle funzionalità di individuazione delle funzionalità di realtà mista con gli asset standard evidenziati](images/mrft-install-openxr.png)

> [!NOTE]
> <span data-ttu-id="ec99c-159">Quando si esegue l'aggiornamento da una versione precedente di MRTK, assicurarsi che la riga seguente si trova nel file **Assets/MixedRealityToolkit.Generated/link.xml:**</span><span class="sxs-lookup"><span data-stu-id="ec99c-159">When upgrading from a previous version of MRTK, ensure the following line is in the **Assets/MixedRealityToolkit.Generated/link.xml** file:</span></span>
>
> ```xml
> <assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.OpenXR" preserve="all"/>
> ```
>
> <span data-ttu-id="ec99c-160">Questa riga verrà aggiunta per impostazione predefinita se si è iniziato con MRTK 2.5.4 o versione successiva.</span><span class="sxs-lookup"><span data-stu-id="ec99c-160">This line will be added by default if you started with MRTK 2.5.4 or newer.</span></span>

## <a name="next-steps"></a><span data-ttu-id="ec99c-161">Passaggi successivi</span><span class="sxs-lookup"><span data-stu-id="ec99c-161">Next steps</span></span>

<span data-ttu-id="ec99c-162">Ora che il progetto è configurato per OpenXR e [](openxr-supported-features.md) si ha accesso agli esempi, vedere quali funzionalità sono attualmente supportate nel plug-in OpenXR.</span><span class="sxs-lookup"><span data-stu-id="ec99c-162">Now that you have your project configured for OpenXR and have access to samples, check out what [features](openxr-supported-features.md) are currently supported in our OpenXR plugin.</span></span>

## <a name="have-feedback"></a><span data-ttu-id="ec99c-163">Commenti e suggerimenti?</span><span class="sxs-lookup"><span data-stu-id="ec99c-163">Have Feedback?</span></span>

<span data-ttu-id="ec99c-164">OpenXR è ancora sperimentale, quindi i commenti e i suggerimenti che è possibile inviare sono utili per migliorarlo.</span><span class="sxs-lookup"><span data-stu-id="ec99c-164">OpenXR is still experimental, so we’d appreciate any feedback you can give us to help make it better.</span></span> <span data-ttu-id="ec99c-165">È possibile trovare microsoft nei [forum unity](https://aka.ms/unityforums) contrassegnando il post del forum con **Microsoft**  +  **OpenXR** e HoloLens 2 o **Windows Mixed Reality**. </span><span class="sxs-lookup"><span data-stu-id="ec99c-165">You'll find us on the [Unity Forums](https://aka.ms/unityforums) by tagging your forum post with **Microsoft** + **OpenXR** and either **HoloLens 2** or **Windows Mixed Reality**.</span></span>

## <a name="see-also"></a><span data-ttu-id="ec99c-166">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="ec99c-166">See also</span></span>

* [<span data-ttu-id="ec99c-167">Configurazione del progetto senza MRTK</span><span class="sxs-lookup"><span data-stu-id="ec99c-167">Configuring your project without MRTK</span></span>](configure-unity-project.md)
* [<span data-ttu-id="ec99c-168">Impostazioni consigliate per Unity</span><span class="sxs-lookup"><span data-stu-id="ec99c-168">Recommended settings for Unity</span></span>](recommended-settings-for-unity.md)
* [<span data-ttu-id="ec99c-169">Consigli sulle prestazioni per Unity</span><span class="sxs-lookup"><span data-stu-id="ec99c-169">Performance recommendations for Unity</span></span>](performance-recommendations-for-unity.md#how-to-profile-with-unity)

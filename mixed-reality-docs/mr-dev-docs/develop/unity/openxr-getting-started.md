---
title: Uso del plug-in OpenXR per la realtà mista per Unity
description: Informazioni su come abilitare il plug-in OpenXR per la realtà mista per i progetti Unity.
author: hferrone
ms.author: alexturn
ms.date: 01/11/2021
ms.topic: article
keywords: openxr, Unity, hololens, hololens 2, realtà mista, MRTK, Toolkit per realtà mista, realtà aumentata, realtà virtuale, cuffie con realtà mista, informazioni, esercitazione, introduzione
ms.openlocfilehash: cae588acbcddeefae45a555f335f1c74389f1824
ms.sourcegitcommit: 029f247a6c33068360d3a06f2a473a12586017e1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/14/2021
ms.locfileid: "100496169"
---
# <a name="using-the-mixed-reality-openxr-plugin-for-unity"></a><span data-ttu-id="57992-104">Uso del plug-in OpenXR per la realtà mista per Unity</span><span class="sxs-lookup"><span data-stu-id="57992-104">Using the Mixed Reality OpenXR Plugin for Unity</span></span>

<span data-ttu-id="57992-105">A partire da Unity versione 2020,2, il pacchetto di plug-in per la realtà mista di Microsoft OpenXR è disponibile tramite Gestione pacchetti Unity (UPM).</span><span class="sxs-lookup"><span data-stu-id="57992-105">Starting with Unity version 2020.2, Microsoft’s Mixed Reality OpenXR Plugin package is available using the Unity Package Manager (UPM).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="57992-106">Prerequisiti</span><span class="sxs-lookup"><span data-stu-id="57992-106">Prerequisites</span></span>

* <span data-ttu-id="57992-107">Unity 2020,2 o versione successiva</span><span class="sxs-lookup"><span data-stu-id="57992-107">Unity 2020.2 or later</span></span>
* <span data-ttu-id="57992-108">Plug-in OpenXR Unity 0.1.3 o versione successiva</span><span class="sxs-lookup"><span data-stu-id="57992-108">Unity OpenXR plugin 0.1.3 or later</span></span>
* <span data-ttu-id="57992-109">Visual Studio 2019 o versione successiva</span><span class="sxs-lookup"><span data-stu-id="57992-109">Visual Studio 2019 or later</span></span>
* <span data-ttu-id="57992-110">Installare il supporto della piattaforma **UWP** in Unity per le app HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="57992-110">Install **UWP** platform support in Unity for HoloLens 2 apps</span></span>

> [!NOTE]
> <span data-ttu-id="57992-111">Se si stanno compilando applicazioni VR in PC Windows, il plug-in OpenXR per realtà mista non è necessariamente obbligatorio.</span><span class="sxs-lookup"><span data-stu-id="57992-111">If you're building VR applications on Windows PC, the Mixed Reality OpenXR plugin is not necessarily required.</span></span> <span data-ttu-id="57992-112">Tuttavia, è necessario installare il plug-in se si sta personalizzando il mapping del controller per i controller HP Reverb G2 o la creazione di app che funzionano sia con le cuffie HoloLens 2 sia con le cuffie VR.</span><span class="sxs-lookup"><span data-stu-id="57992-112">However, you'll want to install the plugin if you're customizing controller mapping for HP Reverb G2 controllers or building apps that work on both HoloLens 2 and VR headsets.</span></span>

## <a name="installing-openxr-with-the-mixed-reality-feature-tool"></a><span data-ttu-id="57992-113">Installazione di OpenXR con lo strumento di funzionalità della realtà mista</span><span class="sxs-lookup"><span data-stu-id="57992-113">Installing OpenXR with the Mixed Reality Feature Tool</span></span>

<span data-ttu-id="57992-114">Installare il plug-in OpenXR con la nuova applicazione dello strumento per la funzionalità di realtà mista.</span><span class="sxs-lookup"><span data-stu-id="57992-114">Install the OpenXR plugin with the new Mixed Reality Feature Tool application.</span></span> <span data-ttu-id="57992-115">Seguire le [istruzioni per l'installazione e l'utilizzo](welcome-to-mr-feature-tool.md) e selezionare il pacchetto di plug-in **realtà mista OpenXR** nella categoria del Toolkit di realtà mista:</span><span class="sxs-lookup"><span data-stu-id="57992-115">Follow the [installation and usage instructions](welcome-to-mr-feature-tool.md) and select the **Mixed Reality OpenXR Plugin** package in the Mixed Reality Toolkit category:</span></span>

![Finestra pacchetti degli strumenti della funzionalità di realtà mista con plug-in Open XR evidenziato](images/feature-tool-openxr.png)

## <a name="configuring-xr-plugin-management-for-openxr"></a><span data-ttu-id="57992-117">Configurazione della gestione dei plug-in XR per OpenXR</span><span class="sxs-lookup"><span data-stu-id="57992-117">Configuring XR Plugin Management for OpenXR</span></span>

<span data-ttu-id="57992-118">Per impostare OpenXR come runtime in Unity:</span><span class="sxs-lookup"><span data-stu-id="57992-118">To set OpenXR as the the runtime in Unity:</span></span>

1. <span data-ttu-id="57992-119">Nell'editor di Unity passare a **modifica > impostazioni progetto**</span><span class="sxs-lookup"><span data-stu-id="57992-119">In the Unity Editor, navigate to **Edit > Project Settings**</span></span>
2. <span data-ttu-id="57992-120">Nell'elenco delle impostazioni selezionare **Gestione plug** -in XR</span><span class="sxs-lookup"><span data-stu-id="57992-120">In the list of Settings, select **XR Plugin Management**</span></span>
3. <span data-ttu-id="57992-121">Selezionare le caselle **Inizializza XR all'avvio** e **OpenXR (anteprima)**</span><span class="sxs-lookup"><span data-stu-id="57992-121">Check the **Initialize XR on Startup** and **OpenXR (Preview)** boxes</span></span>
4. <span data-ttu-id="57992-122">Se la destinazione è HoloLens 2, assicurarsi di trovarsi nella piattaforma UWP e selezionare il **set di funzionalità di Microsoft HoloLens**</span><span class="sxs-lookup"><span data-stu-id="57992-122">If targeting HoloLens 2, make sure you're on the UWP platform and select **Microsoft HoloLens Feature Set**</span></span>

![Screenshot del pannello Impostazioni progetto aperto nell'editor di Unity con la gestione dei plug-in di XR evidenziata](images/openxr-img-05.png)

> [!IMPORTANT]
> <span data-ttu-id="57992-124">Se viene visualizzata un'icona di avviso rossa accanto a plug-in **OpenXR (anteprima)**, fare clic sull'icona e selezionare **Correggi tutto** prima di continuare.</span><span class="sxs-lookup"><span data-stu-id="57992-124">If you see a red warning icon next to **OpenXR Plugin (Preview)**, click the icon and select **Fix all** before continuing.</span></span> <span data-ttu-id="57992-125">Per rendere effettive le modifiche, potrebbe essere necessario riavviare l'editor di Unity.</span><span class="sxs-lookup"><span data-stu-id="57992-125">The Unity Editor may need to restart itself for the changes to take effect.</span></span>

![Screenshot della finestra di convalida del progetto OpenXR](images/openxr-img-06.png)

<span data-ttu-id="57992-127">A questo punto si è pronti per iniziare a sviluppare con OpenXR in Unity.</span><span class="sxs-lookup"><span data-stu-id="57992-127">You're now ready to begin developing with OpenXR in Unity!</span></span>  <span data-ttu-id="57992-128">Continuare con la sezione successiva per informazioni su come usare gli esempi di OpenXR.</span><span class="sxs-lookup"><span data-stu-id="57992-128">Continue on to the next section to learn how to use the OpenXR samples.</span></span>

## <a name="optimization"></a><span data-ttu-id="57992-129">Optimization</span><span class="sxs-lookup"><span data-stu-id="57992-129">Optimization</span></span>

<span data-ttu-id="57992-130">Se si sta sviluppando per HoloLens 2, passare a **realtà mista> OpenXR > applicare le impostazioni di progetto consigliate per HoloLens 2** per ottenere prestazioni migliori per le app.</span><span class="sxs-lookup"><span data-stu-id="57992-130">If you're developing for HoloLens 2, navigate to **Mixed Reality> OpenXR > Apply recommended project settings for HoloLens 2** to get better app performance.</span></span>

![Screenshot della voce di menu della realtà mista aperta con OpenXR selezionato](images/openxr-img-08.png)

## <a name="try-out-the-unity-sample-scenes"></a><span data-ttu-id="57992-132">Provare le scene di esempio di Unity</span><span class="sxs-lookup"><span data-stu-id="57992-132">Try out the Unity sample scenes</span></span>

<span data-ttu-id="57992-133">Per usare uno o più degli esempi, installare [ARFoundation 4.0 +](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/index.html#installing-ar-foundation) da **Gestione pacchetti**:</span><span class="sxs-lookup"><span data-stu-id="57992-133">To utilize one or more of the examples, install [ARFoundation 4.0+](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/index.html#installing-ar-foundation) from the **Package Manager**:</span></span>

![Screenshot di gestione pacchetti Unity aperto nell'editor di Unity con AR Foundation evidenziato](images/openxr-img-09.png)

### <a name="hololens-2-samples"></a><span data-ttu-id="57992-135">Esempi di HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="57992-135">HoloLens 2 samples</span></span>

1. <span data-ttu-id="57992-136">Nell'editor di Unity passare a **finestra > gestione pacchetti**</span><span class="sxs-lookup"><span data-stu-id="57992-136">In the Unity Editor, navigate to **Window > Package Manager**</span></span>
2. <span data-ttu-id="57992-137">Nell'elenco dei pacchetti selezionare il plug-in **OpenXR realtà mista**</span><span class="sxs-lookup"><span data-stu-id="57992-137">In the list of packages, select **Mixed Reality OpenXR Plugin**</span></span>
3. <span data-ttu-id="57992-138">Individuare l'esempio nell'elenco degli **esempi** e selezionare **Importa** .</span><span class="sxs-lookup"><span data-stu-id="57992-138">Locate the sample in the **Samples** list and select **Import**</span></span>

![Screenshot di gestione pacchetti Unity aperto nell'editor di Unity con la realtà mista OpenXR plug-in selezionato ed esempi pulsante di importazione evidenziato](images/openxr-img-03.png)

<!-- ### For all other OpenXR samples

1. In the Unity Editor, navigate to **Window > Package Manager**
2. In the list of packages, select **OpenXR Plugin**
3. Locate the sample in the **Samples** list and select **Import**

![Screenshot of Unity Package Manager open in Unity editor with OpenXR Plugin selected and samples import button highlighted](images/openxr-img-10.png) -->

> [!NOTE]
> <span data-ttu-id="57992-140">Quando viene aggiornato un pacchetto, Unity offre la possibilità di aggiornare gli esempi importati.</span><span class="sxs-lookup"><span data-stu-id="57992-140">When a package is updated, Unity provides the option to update imported samples.</span></span>  <span data-ttu-id="57992-141">L'aggiornamento di un esempio importato sovrascriverà tutte le modifiche apportate all'esempio e alle risorse associate.</span><span class="sxs-lookup"><span data-stu-id="57992-141">Updating an imported sample will overwrite any changes that have been made to the sample and associated assets.</span></span>

## <a name="using-mrtk-with-openxr-support"></a><span data-ttu-id="57992-142">Uso di MRTK con il supporto OpenXR</span><span class="sxs-lookup"><span data-stu-id="57992-142">Using MRTK with OpenXR support</span></span>

<span data-ttu-id="57992-143">MRTK Unity supporta il plug-in OpenXR realtà mista a partire dalla versione 2.5.3.</span><span class="sxs-lookup"><span data-stu-id="57992-143">MRTK Unity supports the Mixed Reality OpenXR plugin starting with the 2.5.3 release.</span></span>  

1. <span data-ttu-id="57992-144">Aprire di nuovo lo strumento per la [funzionalità di realtà mista](welcome-to-mr-feature-tool.md) e selezionare il pacchetto di plug-in OpenXR per la **realtà mista** nella categoria supporto piattaforma</span><span class="sxs-lookup"><span data-stu-id="57992-144">Open the [Mixed Reality Feature Tool](welcome-to-mr-feature-tool.md) again and select the **Mixed Reality OpenXR Plugin** package in the Platform Support category</span></span>
2. <span data-ttu-id="57992-145">Passare allo script del componente MixedReality Toolkit nel controllo e passare al profilo **DefaultOpenXRConfigurationProfile** :</span><span class="sxs-lookup"><span data-stu-id="57992-145">Go to the MixedReality Toolkit component script in the Inspector and switch to the **DefaultOpenXRConfigurationProfile** profile:</span></span>

![Screenshot del cambio della configurazione di MRTK nel componente del Toolkit per realtà mista del controllo](images/openxr-img-11.png)

### <a name="known-issues"></a><span data-ttu-id="57992-147">Problemi noti</span><span class="sxs-lookup"><span data-stu-id="57992-147">Known issues</span></span> 

<span data-ttu-id="57992-148">Quando si usa la funzionalità di rilevamento della mano, aggiungere la riga seguente nel file **assets/MixedRealityToolkit. generated/link.xml** :</span><span class="sxs-lookup"><span data-stu-id="57992-148">When using the Hand Tracking feature, add following line in the **Assets/MixedRealityToolkit.Generated/link.xml** file:</span></span>

```
<assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.OpenXR" preserve="all"/>
```

## <a name="next-steps"></a><span data-ttu-id="57992-149">Passaggi successivi</span><span class="sxs-lookup"><span data-stu-id="57992-149">Next steps</span></span>

<span data-ttu-id="57992-150">Ora che il progetto è stato configurato per OpenXR ed è possibile accedere agli esempi, vedere quali [funzionalità](openxr-supported-features.md) sono attualmente supportate nel plug-in OpenXR.</span><span class="sxs-lookup"><span data-stu-id="57992-150">Now that you have your project configured for OpenXR and have access to samples, check out what [features](openxr-supported-features.md) are currently supported in our OpenXR plugin.</span></span>

## <a name="have-feedback"></a><span data-ttu-id="57992-151">Inviare commenti e suggerimenti?</span><span class="sxs-lookup"><span data-stu-id="57992-151">Have Feedback?</span></span>

<span data-ttu-id="57992-152">OpenXR è ancora in fase di sperimentazione, quindi saremmo lieti di ricevere commenti e suggerimenti per aiutarti a migliorarlo.</span><span class="sxs-lookup"><span data-stu-id="57992-152">OpenXR is still experimental, so we’d appreciate any feedback you can give us to help make it better.</span></span> <span data-ttu-id="57992-153">Ci troviamo nei [Forum di Unity](https://aka.ms/unityforums) contrassegnando il post del forum con **Microsoft**  +  **OpenXR** e **HoloLens 2** o la **realtà mista di Windows**.</span><span class="sxs-lookup"><span data-stu-id="57992-153">You'll find us on the [Unity Forums](https://aka.ms/unityforums) by tagging your forum post with **Microsoft** + **OpenXR** and either **HoloLens 2** or **Windows Mixed Reality**.</span></span>

## <a name="see-also"></a><span data-ttu-id="57992-154">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="57992-154">See also</span></span>

* [<span data-ttu-id="57992-155">Configurazione del progetto senza MRTK</span><span class="sxs-lookup"><span data-stu-id="57992-155">Configuring your project without MRTK</span></span>](configure-unity-project.md)
* [<span data-ttu-id="57992-156">Impostazioni consigliate per Unity</span><span class="sxs-lookup"><span data-stu-id="57992-156">Recommended settings for Unity</span></span>](recommended-settings-for-unity.md)
* [<span data-ttu-id="57992-157">Consigli sulle prestazioni per Unity</span><span class="sxs-lookup"><span data-stu-id="57992-157">Performance recommendations for Unity</span></span>](performance-recommendations-for-unity.md#how-to-profile-with-unity)

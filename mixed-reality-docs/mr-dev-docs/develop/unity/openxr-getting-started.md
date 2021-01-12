---
title: Uso del plug-in OpenXR per la realtà mista per Unity
description: Informazioni su come abilitare il plug-in OpenXR per la realtà mista per i progetti Unity.
author: hferrone
ms.author: alexturn
ms.date: 01/11/2021
ms.topic: article
keywords: openxr, Unity, hololens, hololens 2, realtà mista, MRTK, Toolkit per realtà mista, realtà aumentata, realtà virtuale, cuffie con realtà mista, informazioni, esercitazione, introduzione
ms.openlocfilehash: c5d312161b7d0f4f832e8d09dbacf5af700ffd8d
ms.sourcegitcommit: aa29b68603721e909f08f352feed24c65d2e505e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/12/2021
ms.locfileid: "98108884"
---
# <a name="using-the-mixed-reality-openxr-plugin-for-unity"></a><span data-ttu-id="ea1d9-104">Uso del plug-in OpenXR per la realtà mista per Unity</span><span class="sxs-lookup"><span data-stu-id="ea1d9-104">Using the Mixed Reality OpenXR Plugin for Unity</span></span>

<span data-ttu-id="ea1d9-105">A partire da Unity versione 2020,2, il pacchetto di plug-in per la realtà mista di Microsoft OpenXR è disponibile tramite Gestione pacchetti Unity (UPM).</span><span class="sxs-lookup"><span data-stu-id="ea1d9-105">Starting with Unity version 2020.2, Microsoft’s Mixed Reality OpenXR Plugin package is available using the Unity Package Manager (UPM).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="ea1d9-106">Prerequisiti</span><span class="sxs-lookup"><span data-stu-id="ea1d9-106">Prerequisites</span></span>

* <span data-ttu-id="ea1d9-107">Unity 2020,2 o versione successiva</span><span class="sxs-lookup"><span data-stu-id="ea1d9-107">Unity 2020.2 or later</span></span>
* <span data-ttu-id="ea1d9-108">Plug-in OpenXR Unity 0.1.2 o versione successiva</span><span class="sxs-lookup"><span data-stu-id="ea1d9-108">Unity OpenXR plugin 0.1.2 or later</span></span>
* <span data-ttu-id="ea1d9-109">Visual Studio 2019 o versione successiva</span><span class="sxs-lookup"><span data-stu-id="ea1d9-109">Visual Studio 2019 or later</span></span>
* <span data-ttu-id="ea1d9-110">Installare il supporto della piattaforma **UWP** in Unity per le app HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="ea1d9-110">Install **UWP** platform support in Unity for HoloLens 2 apps</span></span>

> [!NOTE]
> <span data-ttu-id="ea1d9-111">Se si stanno compilando applicazioni VR in PC Windows, il plug-in OpenXR per realtà mista non è necessariamente obbligatorio.</span><span class="sxs-lookup"><span data-stu-id="ea1d9-111">If you're building VR applications on Windows PC, the Mixed Reality OpenXR plugin is not necessarily required.</span></span> <span data-ttu-id="ea1d9-112">Tuttavia, è necessario installare il plug-in se si sta personalizzando il mapping del controller per i controller HP Reverb G2 o la creazione di app che funzionano sia con le cuffie HoloLens 2 sia con le cuffie VR.</span><span class="sxs-lookup"><span data-stu-id="ea1d9-112">However, you'll want to install the plugin if you're customizing controller mapping for HP Reverb G2 controllers or building apps that work on both HoloLens 2 and VR headsets.</span></span>

## <a name="installing-the-mixed-reality-openxr-plugin"></a><span data-ttu-id="ea1d9-113">Installare il plug-in OpenXR per la realtà mista</span><span class="sxs-lookup"><span data-stu-id="ea1d9-113">Installing the Mixed Reality OpenXR plugin</span></span>

<span data-ttu-id="ea1d9-114">Il progetto deve installare il plug-in **OpenXR** e i pacchetti di **gestione dei plug** -in XR prima di usare il plug-in OpenXR realtà mista.</span><span class="sxs-lookup"><span data-stu-id="ea1d9-114">Your project needs to install the **OpenXR Plugin** and **XR Plugin Management** packages before using the Mixed Reality OpenXR Plugin.</span></span> <span data-ttu-id="ea1d9-115">Se sono già stati installati,</span><span class="sxs-lookup"><span data-stu-id="ea1d9-115">If you've already installed them, great!</span></span> <span data-ttu-id="ea1d9-116">In caso contrario, l'installazione del plug-in OpenXR per la realtà mista li installerà automaticamente come dipendenze:</span><span class="sxs-lookup"><span data-stu-id="ea1d9-116">If not, installing the Mixed Reality OpenXR plugin will automatically install them as dependencies:</span></span>

1. <span data-ttu-id="ea1d9-117">Nell'editor di Unity passare a **modifica > impostazioni progetto > gestione pacchetti**</span><span class="sxs-lookup"><span data-stu-id="ea1d9-117">In the Unity Editor, navigate to **Edit > Project Settings > Package Manager**</span></span>
2. <span data-ttu-id="ea1d9-118">Espandere la sezione **registri con ambito** , immettere le informazioni seguenti e selezionare **Salva**:</span><span class="sxs-lookup"><span data-stu-id="ea1d9-118">Expand the **Scoped Registries** section, enter the following information, and select **Save**:</span></span>
    * <span data-ttu-id="ea1d9-119">Imposta il **nome** su **Microsoft Mixed Reality**</span><span class="sxs-lookup"><span data-stu-id="ea1d9-119">Set **Name** to **Microsoft Mixed Reality**</span></span>
    * <span data-ttu-id="ea1d9-120">Imposta **URL** su **https://pkgs.dev.azure.com/aipmr/MixedReality-Unity-Packages/_packaging/Unity-packages/npm/registry/**</span><span class="sxs-lookup"><span data-stu-id="ea1d9-120">Set **URL** to **https://pkgs.dev.azure.com/aipmr/MixedReality-Unity-Packages/_packaging/Unity-packages/npm/registry/**</span></span>
    * <span data-ttu-id="ea1d9-121">Imposta **ambito/i** su **com. Microsoft. mixedreality**</span><span class="sxs-lookup"><span data-stu-id="ea1d9-121">Set **Scope(s)** to **com.microsoft.mixedreality**</span></span>

3. <span data-ttu-id="ea1d9-122">In **Impostazioni avanzate** selezionare **Abilita pacchetti di anteprima**</span><span class="sxs-lookup"><span data-stu-id="ea1d9-122">Under **Advanced Settings**, select **Enable Preview Packages**</span></span>

![Screenshot della finestra di gestione pacchetti Unity aperta in Impostazioni progetto](images/openxr-img-01.png)

<span data-ttu-id="ea1d9-124">Gestione pacchetti Unity usa un file manifesto denominato *manifest.json* per determinare i pacchetti da installare e i registri da cui possono essere installati.</span><span class="sxs-lookup"><span data-stu-id="ea1d9-124">The Unity Package Manager uses a manifest file named *manifest.json* to determine which packages to install and the registries they can be installed from.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ea1d9-125">OpenXR è ancora sperimentale in Unity e questo processo può variare nel tempo mentre si lavora per ottimizzare l'esperienza degli sviluppatori.</span><span class="sxs-lookup"><span data-stu-id="ea1d9-125">OpenXR is still experimental in Unity and this process may change over time as we work to optimize the developer experience.</span></span>

### <a name="registering-the-mixed-reality-dependency"></a><span data-ttu-id="ea1d9-126">Registrazione della dipendenza della realtà mista</span><span class="sxs-lookup"><span data-stu-id="ea1d9-126">Registering the Mixed Reality dependency</span></span>

<span data-ttu-id="ea1d9-127">Quando il registro con ambito Microsoft Mixed Reality è stato aggiunto al manifesto, è possibile specificare il pacchetto OpenXR.</span><span class="sxs-lookup"><span data-stu-id="ea1d9-127">Once the Microsoft Mixed Reality scoped registry has been added to the manifest, the OpenXR package can be specified.</span></span>

<span data-ttu-id="ea1d9-128">Per aggiungere il pacchetto OpenXR:</span><span class="sxs-lookup"><span data-stu-id="ea1d9-128">To add the OpenXR package:</span></span>

1. <span data-ttu-id="ea1d9-129">Aprire **[projectRoot]/Packages/manifest.js** in un editor di testo, ad esempio Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="ea1d9-129">Open **[projectRoot]/Packages/manifest.json** in a text editor like Visual Studio Code</span></span>
    1. <span data-ttu-id="ea1d9-130">Per ottenerlo, fare clic con il pulsante destro del mouse su **pacchetti** nel riquadro sinistro della finestra del progetto.</span><span class="sxs-lookup"><span data-stu-id="ea1d9-130">To get here, right click on **Packages** in the left panel of the Project window.</span></span> <span data-ttu-id="ea1d9-131">Quindi, fare clic su **Mostra in Esplora**.</span><span class="sxs-lookup"><span data-stu-id="ea1d9-131">Then, click **Show in Explorer**.</span></span>
    <span data-ttu-id="ea1d9-132">![Screenshot dell'elenco di pacchetti nella finestra del progetto](images/packages.png)</span><span class="sxs-lookup"><span data-stu-id="ea1d9-132">![Screenshot of the packages listing in the Project window](images/packages.png)</span></span>
1. <span data-ttu-id="ea1d9-133">Modificare la sezione relativa alle dipendenze dei *pacchetti/manifest.jsnel* file come indicato di seguito:</span><span class="sxs-lookup"><span data-stu-id="ea1d9-133">Modify the dependencies section of the *Packages/manifest.json* file as follows:</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="ea1d9-134">Nel file manifesto potrebbero essere presenti più dipendenze di quelle illustrate qui.</span><span class="sxs-lookup"><span data-stu-id="ea1d9-134">There may be more dependencies in your manifest file than shown here.</span></span> <span data-ttu-id="ea1d9-135">Non eliminare alcun oggetto, ma è sufficiente aggiungere la dipendenza OpenXR all'elenco.</span><span class="sxs-lookup"><span data-stu-id="ea1d9-135">Don't delete any of them, just add the OpenXR dependency to the list.</span></span>

    ``` json
      "dependencies": {
        "com.microsoft.mixedreality.openxr": "0.1.2",
      }
    ```

1. <span data-ttu-id="ea1d9-136">Salvare il file, tornare all'editor di Unity e aprire **Gestione pacchetti** per verificare che il plug-in sia installato:</span><span class="sxs-lookup"><span data-stu-id="ea1d9-136">Save the file, switch back to the Unity Editor, and open the **Package Manager** to confirm the plugin is installed:</span></span>

    ![Screenshot di gestione pacchetti Unity aperto nell'editor di Unity con il plug-in di OpenXR realtà mista evidenziato](images/openxr-img-03.png)

    > [!Note]
    > <span data-ttu-id="ea1d9-138">Se il pacchetto OpenXR viene rimosso usando Gestione pacchetti Unity, sarà necessario aggiungerlo di nuovo usando i passaggi descritti in precedenza.</span><span class="sxs-lookup"><span data-stu-id="ea1d9-138">If the OpenXR package is removed using the Unity Package Manager, you'll have to re-add it using the previously described steps.</span></span>

## <a name="configuring-xr-plugin-management-for-openxr"></a><span data-ttu-id="ea1d9-139">Configurazione della gestione dei plug-in XR per OpenXR</span><span class="sxs-lookup"><span data-stu-id="ea1d9-139">Configuring XR Plugin Management for OpenXR</span></span>

<span data-ttu-id="ea1d9-140">Per impostare OpenXR come runtime in Unity:</span><span class="sxs-lookup"><span data-stu-id="ea1d9-140">To set OpenXR as the the runtime in Unity:</span></span>

1. <span data-ttu-id="ea1d9-141">Nell'editor di Unity passare a **modifica > impostazioni progetto**</span><span class="sxs-lookup"><span data-stu-id="ea1d9-141">In the Unity Editor, navigate to **Edit > Project Settings**</span></span>
2. <span data-ttu-id="ea1d9-142">Nell'elenco delle impostazioni selezionare **Gestione plug** -in XR</span><span class="sxs-lookup"><span data-stu-id="ea1d9-142">In the list of Settings, select **XR Plugin Management**</span></span>
3. <span data-ttu-id="ea1d9-143">Selezionare le caselle **Inizializza XR all'avvio** e **OpenXR (anteprima)**</span><span class="sxs-lookup"><span data-stu-id="ea1d9-143">Check the **Initialize XR on Startup** and **OpenXR (Preview)** boxes</span></span>
4. <span data-ttu-id="ea1d9-144">Se la destinazione è HoloLens 2, assicurarsi di trovarsi nella piattaforma UWP e selezionare il **set di funzionalità di Microsoft HoloLens**</span><span class="sxs-lookup"><span data-stu-id="ea1d9-144">If targeting HoloLens 2, make sure you're on the UWP platform and select **Microsoft HoloLens Feature Set**</span></span>

![Screenshot del pannello Impostazioni progetto aperto nell'editor di Unity con la gestione dei plug-in di XR evidenziata](images/openxr-img-05.png)

> [!IMPORTANT]
> <span data-ttu-id="ea1d9-146">Se viene visualizzata un'icona di avviso rossa accanto a plug-in **OpenXR (anteprima)**, fare clic sull'icona e selezionare **Correggi tutto** prima di continuare.</span><span class="sxs-lookup"><span data-stu-id="ea1d9-146">If you see a red warning icon next to **OpenXR Plugin (Preview)**, click the icon and select **Fix all** before continuing.</span></span> <span data-ttu-id="ea1d9-147">Per rendere effettive le modifiche, potrebbe essere necessario riavviare l'editor di Unity.</span><span class="sxs-lookup"><span data-stu-id="ea1d9-147">The Unity Editor may need to restart itself for the changes to take effect.</span></span>

![Screenshot della finestra di convalida del progetto OpenXR](images/openxr-img-06.png)

<span data-ttu-id="ea1d9-149">A questo punto si è pronti per iniziare a sviluppare con OpenXR in Unity.</span><span class="sxs-lookup"><span data-stu-id="ea1d9-149">You're now ready to begin developing with OpenXR in Unity!</span></span>  <span data-ttu-id="ea1d9-150">Continuare con la sezione successiva per informazioni su come usare gli esempi di OpenXR.</span><span class="sxs-lookup"><span data-stu-id="ea1d9-150">Continue on to the next section to learn how to use the OpenXR samples.</span></span>

## <a name="optimization"></a><span data-ttu-id="ea1d9-151">Optimization</span><span class="sxs-lookup"><span data-stu-id="ea1d9-151">Optimization</span></span>

<span data-ttu-id="ea1d9-152">Se si sta sviluppando per HoloLens 2, passare a **realtà mista> OpenXR > applicare le impostazioni di progetto consigliate per HoloLens 2** per ottenere prestazioni migliori per le app.</span><span class="sxs-lookup"><span data-stu-id="ea1d9-152">If you're developing for HoloLens 2, navigate to **Mixed Reality> OpenXR > Apply recommended project settings for HoloLens 2** to get better app performance.</span></span>

![Screenshot della voce di menu della realtà mista aperta con OpenXR selezionato](images/openxr-img-08.png)

## <a name="try-out-the-unity-sample-scenes"></a><span data-ttu-id="ea1d9-154">Provare le scene di esempio di Unity</span><span class="sxs-lookup"><span data-stu-id="ea1d9-154">Try out the Unity sample scenes</span></span>

<span data-ttu-id="ea1d9-155">Per usare uno o più degli esempi, installare [ARFoundation 4.0 +](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/index.html#installing-ar-foundation) da **Gestione pacchetti**:</span><span class="sxs-lookup"><span data-stu-id="ea1d9-155">To utilize one or more of the examples, install [ARFoundation 4.0+](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/index.html#installing-ar-foundation) from the **Package Manager**:</span></span>

![Screenshot di gestione pacchetti Unity aperto nell'editor di Unity con AR Foundation evidenziato](images/openxr-img-09.png)

### <a name="hololens-2-samples"></a><span data-ttu-id="ea1d9-157">Esempi di HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="ea1d9-157">HoloLens 2 samples</span></span>

1. <span data-ttu-id="ea1d9-158">Nell'editor di Unity passare a **finestra > gestione pacchetti**</span><span class="sxs-lookup"><span data-stu-id="ea1d9-158">In the Unity Editor, navigate to **Window > Package Manager**</span></span>
2. <span data-ttu-id="ea1d9-159">Nell'elenco dei pacchetti selezionare il plug-in **OpenXR realtà mista**</span><span class="sxs-lookup"><span data-stu-id="ea1d9-159">In the list of packages, select **Mixed Reality OpenXR Plugin**</span></span>
3. <span data-ttu-id="ea1d9-160">Individuare l'esempio nell'elenco degli **esempi** e selezionare **Importa** .</span><span class="sxs-lookup"><span data-stu-id="ea1d9-160">Locate the sample in the **Samples** list and select **Import**</span></span>

![Screenshot di gestione pacchetti Unity aperto nell'editor di Unity con la realtà mista OpenXR plug-in selezionato ed esempi pulsante di importazione evidenziato](images/openxr-img-03.png)

<!-- ### For all other OpenXR samples

1. In the Unity Editor, navigate to **Window > Package Manager**
2. In the list of packages, select **OpenXR Plugin**
3. Locate the sample in the **Samples** list and select **Import**

![Screenshot of Unity Package Manager open in Unity editor with OpenXR Plugin selected and samples import button highlighted](images/openxr-img-10.png) -->

> [!NOTE]
> <span data-ttu-id="ea1d9-162">Quando viene aggiornato un pacchetto, Unity offre la possibilità di aggiornare gli esempi importati.</span><span class="sxs-lookup"><span data-stu-id="ea1d9-162">When a package is updated, Unity provides the option to update imported samples.</span></span>  <span data-ttu-id="ea1d9-163">L'aggiornamento di un esempio importato sovrascriverà tutte le modifiche apportate all'esempio e alle risorse associate.</span><span class="sxs-lookup"><span data-stu-id="ea1d9-163">Updating an imported sample will overwrite any changes that have been made to the sample and associated assets.</span></span>

## <a name="using-mrtk-with-openxr-support"></a><span data-ttu-id="ea1d9-164">Uso di MRTK con il supporto OpenXR</span><span class="sxs-lookup"><span data-stu-id="ea1d9-164">Using MRTK with OpenXR support</span></span>

<span data-ttu-id="ea1d9-165">MRTK Unity supporta il plug-in OpenXR realtà mista a partire dalla versione 2.5.3.</span><span class="sxs-lookup"><span data-stu-id="ea1d9-165">MRTK Unity supports the Mixed Reality OpenXR plugin starting with the 2.5.3 release.</span></span>  <span data-ttu-id="ea1d9-166">I plug-in MRTK possono essere installati dagli stessi registri con ambito impostati quando si [installa il plug-in OpenXR realtà mista](#installing-the-mixed-reality-openxr-plugin).</span><span class="sxs-lookup"><span data-stu-id="ea1d9-166">MRTK plugins can be installed from the same scoped registries as you set up when [installing the Mixed Reality OpenXR plugin](#installing-the-mixed-reality-openxr-plugin).</span></span> <span data-ttu-id="ea1d9-167">Per informazioni più dettagliate, vedere la [documentazione di MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/usingupm.html#registering-the-mixed-reality-component-server).</span><span class="sxs-lookup"><span data-stu-id="ea1d9-167">You can find more detailed information in the [MRTK documentation](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/usingupm.html#registering-the-mixed-reality-component-server).</span></span>

1. <span data-ttu-id="ea1d9-168">Aggiungere i pacchetti seguenti in **[projectRoot]/Packages/manifest.js** nel file:</span><span class="sxs-lookup"><span data-stu-id="ea1d9-168">Add following packages in your **[projectRoot]/Packages/manifest.json** file:</span></span>

```json
"dependencies": {
    "com.microsoft.mixedreality.toolkit.foundation": "2.5.3",
    "com.microsoft.mixedreality.toolkit.tools": "2.5.3",
    "com.microsoft.mixedreality.toolkit.examples": "2.5.3",
    …
}
```

2. <span data-ttu-id="ea1d9-169">Passare allo script del componente MixedReality Toolkit nel controllo e passare al profilo **DefaultOpenXRConfigurationProfile** :</span><span class="sxs-lookup"><span data-stu-id="ea1d9-169">Go to the MixedReality Toolkit component script in the Inspector and switch to the **DefaultOpenXRConfigurationProfile** profile:</span></span>

![Screenshot del cambio della configurazione di MRTK nel componente del Toolkit per realtà mista del controllo](images/openxr-img-11.png)

### <a name="known-issues"></a><span data-ttu-id="ea1d9-171">Problemi noti</span><span class="sxs-lookup"><span data-stu-id="ea1d9-171">Known issues</span></span> 

<span data-ttu-id="ea1d9-172">Quando si usa la funzionalità di rilevamento della mano, aggiungere la riga seguente nel file **assets/MixedRealityToolkit. generated/link.xml** :</span><span class="sxs-lookup"><span data-stu-id="ea1d9-172">When using the Hand Tracking feature, add following line in the **Assets/MixedRealityToolkit.Generated/link.xml** file:</span></span>

```
<assembly fullname = "Microsoft.MixedReality.Toolkit.Providers.OpenXR" preserve="all"/>
```

## <a name="next-steps"></a><span data-ttu-id="ea1d9-173">Passaggi successivi</span><span class="sxs-lookup"><span data-stu-id="ea1d9-173">Next steps</span></span>

<span data-ttu-id="ea1d9-174">Ora che il progetto è stato configurato per OpenXR ed è possibile accedere agli esempi, vedere quali [funzionalità](openxr-supported-features.md) sono attualmente supportate nel plug-in OpenXR.</span><span class="sxs-lookup"><span data-stu-id="ea1d9-174">Now that you have your project configured for OpenXR and have access to samples, check out what [features](openxr-supported-features.md) are currently supported in our OpenXR plugin.</span></span>

## <a name="have-feedback"></a><span data-ttu-id="ea1d9-175">Inviare commenti e suggerimenti?</span><span class="sxs-lookup"><span data-stu-id="ea1d9-175">Have Feedback?</span></span>

<span data-ttu-id="ea1d9-176">OpenXR è ancora in fase di sperimentazione, quindi saremmo lieti di ricevere commenti e suggerimenti per aiutarti a migliorarlo.</span><span class="sxs-lookup"><span data-stu-id="ea1d9-176">OpenXR is still experimental, so we’d appreciate any feedback you can give us to help make it better.</span></span> <span data-ttu-id="ea1d9-177">Ci troviamo nei [Forum di Unity](https://aka.ms/unityforums) contrassegnando il post del forum con **Microsoft**  +  **OpenXR** e **HoloLens 2** o la **realtà mista di Windows**.</span><span class="sxs-lookup"><span data-stu-id="ea1d9-177">You'll find us on the [Unity Forums](https://aka.ms/unityforums) by tagging your forum post with **Microsoft** + **OpenXR** and either **HoloLens 2** or **Windows Mixed Reality**.</span></span>

## <a name="see-also"></a><span data-ttu-id="ea1d9-178">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="ea1d9-178">See also</span></span>

* [<span data-ttu-id="ea1d9-179">Configurazione del progetto senza MRTK</span><span class="sxs-lookup"><span data-stu-id="ea1d9-179">Configuring your project without MRTK</span></span>](configure-unity-project.md)
* [<span data-ttu-id="ea1d9-180">Impostazioni consigliate per Unity</span><span class="sxs-lookup"><span data-stu-id="ea1d9-180">Recommended settings for Unity</span></span>](recommended-settings-for-unity.md)
* [<span data-ttu-id="ea1d9-181">Consigli sulle prestazioni per Unity</span><span class="sxs-lookup"><span data-stu-id="ea1d9-181">Performance recommendations for Unity</span></span>](performance-recommendations-for-unity.md#how-to-profile-with-unity)

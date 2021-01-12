---
title: Inizializzazione del progetto e distribuzione della prima applicazione
description: In questo corso viene illustrato come configurare il progetto Unity per Mixed Reality Toolkit (MRTK) e come distribuirlo in HoloLens 2.
author: jessemcculloch
ms.author: v-vtieto
ms.date: 12/30/2020
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens, MRTK, mixed reality toolkit, UWP, TextMeshPro,
ms.localizationpriority: high
ms.openlocfilehash: 2ce119e1dd18eacf02088d00e99fb70d06bf956e
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2021
ms.locfileid: "98008221"
---
# <a name="2-initializing-your-project-and-deploying-your-first-application"></a><span data-ttu-id="c3b95-104">2. Inizializzazione del progetto e distribuzione della prima applicazione</span><span class="sxs-lookup"><span data-stu-id="c3b95-104">2. Initializing your project and deploying your first application</span></span>

<span data-ttu-id="c3b95-105">In questa esercitazione apprenderai come creare un nuovo progetto Unity, come configurarlo per lo sviluppo <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank">Mixed Reality Toolkit (MRTK)</a> e come importare MRTK.</span><span class="sxs-lookup"><span data-stu-id="c3b95-105">In this tutorial, you'll learn how to create a new Unity project, configure it for <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank">Mixed Reality Toolkit (MRTK)</a> development, and import MRTK.</span></span> <span data-ttu-id="c3b95-106">Verranno inoltre esaminati i processi di configurazione, compilazione e distribuzione di una scena Unity di base da Visual Studio a HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="c3b95-106">You'll also walk through configuring, building, and deploying a basic Unity scene from Visual Studio to your HoloLens 2.</span></span> <span data-ttu-id="c3b95-107">Dopo la distribuzione in HoloLens 2, dovrebbe essere visualizzata una mesh di mapping spaziale che copre le superfici percepite da HoloLens.</span><span class="sxs-lookup"><span data-stu-id="c3b95-107">Once you have deployed it to your HoloLens 2, you should see a spatial mapping mesh covering the surfaces that are perceived by the HoloLens.</span></span> <span data-ttu-id="c3b95-108">Dovresti anche vedere indicatori sulle mani e sulle dita per il tracciamento delle mani e un contatore della frequenza dei fotogrammi per tenere sotto controllo le prestazioni dell'app.</span><span class="sxs-lookup"><span data-stu-id="c3b95-108">Additionally, you should see indicators on your hands and fingers for hand tracking and a frame rate counter for keeping an eye on app performance.</span></span>

## <a name="objectives"></a><span data-ttu-id="c3b95-109">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="c3b95-109">Objectives</span></span>

* <span data-ttu-id="c3b95-110">Apprendere come configurare Unity per lo sviluppo per HoloLens.</span><span class="sxs-lookup"><span data-stu-id="c3b95-110">Learn how to configure Unity for HoloLens development.</span></span>
* <span data-ttu-id="c3b95-111">Apprendere come compilare e distribuire l'app in HoloLens.</span><span class="sxs-lookup"><span data-stu-id="c3b95-111">Learn how to build and deploy your app to HoloLens.</span></span>
* <span data-ttu-id="c3b95-112">Sperimentare la mesh di mapping spaziale, le mesh mano il contatore della frequenza dei fotogrammi sul dispositivo HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="c3b95-112">Experience the spatial mapping mesh, hand meshes, and  framerate counter on your HoloLens 2 device.</span></span>

## <a name="creating-the-unity-project"></a><span data-ttu-id="c3b95-113">Creazione del progetto Unity</span><span class="sxs-lookup"><span data-stu-id="c3b95-113">Creating the Unity project</span></span>

1. <span data-ttu-id="c3b95-114">Avviare **Unity Hub**, selezionare la scheda **Projects** (Progetti) e quindi fare clic sulla **freccia giù** accanto al pulsante **New** (Nuovo):</span><span class="sxs-lookup"><span data-stu-id="c3b95-114">Launch **Unity Hub**, select the **Projects** tab, and then click the **down arrow** next to the **New** button:</span></span>

![Unity Hub in cui è evidenziata la freccia giù del pulsante "New" (Nuovo)](images/mr-learning-base/base-02-section1-step1-1.png)

2. <span data-ttu-id="c3b95-116">Dal menu a discesa scegliere la versione di Unity specificata nella sezione [Prerequisiti](mr-learning-base-01.md#prerequisites):</span><span class="sxs-lookup"><span data-stu-id="c3b95-116">In the dropdown menu, select the Unity version specified in the [Prerequisites](mr-learning-base-01.md#prerequisites):</span></span>

![Selezionare la versione di Unity](images/mr-learning-base/base-02-section1-step1-2.png)

> [!TIP]
> <span data-ttu-id="c3b95-118">Se la versione specifica di Unity non è disponibile in Unity Hub, puoi avviare l'installazione da <a href="https://unity3d.com/get-unity/download/archive" target="_blank">Download Archive</a> (Archivio download) di Unity.</span><span class="sxs-lookup"><span data-stu-id="c3b95-118">If the particular Unity version is not available in Unity Hub, you can initiate the installation from Unity's <a href="https://unity3d.com/get-unity/download/archive" target="_blank">Download Archive</a>.</span></span>

3. <span data-ttu-id="c3b95-119">Nella finestra **Create a new project** (Crea un nuovo progetto) eseguire queste operazioni:</span><span class="sxs-lookup"><span data-stu-id="c3b95-119">In the **Create a new project** window, do the following:</span></span>

    * <span data-ttu-id="c3b95-120">Assicurarsi che in **Templates** (Modelli) sia impostata l'opzione **3D**.</span><span class="sxs-lookup"><span data-stu-id="c3b95-120">Ensure **Templates** is set to **3D**.</span></span>
    * <span data-ttu-id="c3b95-121">Nella casella **Project Name** (Nome progetto) immettere un nome appropriato per il progetto, ad esempio "Esercitazioni di MRTK".</span><span class="sxs-lookup"><span data-stu-id="c3b95-121">In the **Project Name** box, enter a suitable name for your project (for example, "MRTK Tutorials").</span></span>
    * <span data-ttu-id="c3b95-122">Fare clic sul pulsante con tre punti accanto a **Location** (Percorso) e quindi passare alla cartella in cui si intende salvare il progetto.</span><span class="sxs-lookup"><span data-stu-id="c3b95-122">Click the three-dot button next to **Location**, and then navigate to the folder where you want to save your project.</span></span>

> [!CAUTION]
> <span data-ttu-id="c3b95-123">Se lavori in Windows, tieni presente che è previsto un limite (MAX_PATH) di 255 caratteri per il percorso.</span><span class="sxs-lookup"><span data-stu-id="c3b95-123">When working on Windows, there is a MAX_PATH limit of 255 characters.</span></span> <span data-ttu-id="c3b95-124">È pertanto consigliabile salvare il progetto Unity in prossimità della radice dell'unità.</span><span class="sxs-lookup"><span data-stu-id="c3b95-124">Because of this, you should save the Unity project close to the root of the drive.</span></span>

    * <span data-ttu-id="c3b95-125">Fare clic sul pulsante **Create** (Crea).</span><span class="sxs-lookup"><span data-stu-id="c3b95-125">Click the **Create** button.</span></span> <span data-ttu-id="c3b95-126">Il nuovo progetto Unity viene creato e avviato.</span><span class="sxs-lookup"><span data-stu-id="c3b95-126">This creates and launches your new Unity project.</span></span>

![Unity Hub con la finestra "Create a new project" (Crea un nuovo progetto) completata](images/mr-learning-base/base-02-section1-step1-3.png)

<span data-ttu-id="c3b95-128">La barra di stato consente di restare aggiornati sullo stato di avanzamento.</span><span class="sxs-lookup"><span data-stu-id="c3b95-128">The status bar keeps you updated on your progress.</span></span>

![L'indicatore di stato di Unity consente di restare aggiornati sullo stato di "creazione del progetto"](images/mr-learning-base/base-02-section1-step1-4.png)

## <a name="switching-the-build-platform"></a><span data-ttu-id="c3b95-130">Passaggio a un'altra piattaforma di compilazione</span><span class="sxs-lookup"><span data-stu-id="c3b95-130">Switching the build platform</span></span>

1. <span data-ttu-id="c3b95-131">Sulla barra dei menu scegliere **File** > **Build Settings** (Impostazioni di compilazione).</span><span class="sxs-lookup"><span data-stu-id="c3b95-131">On the menu bar, select **File** > **Build Settings...**</span></span>

![Percorso del menu Build Settings... di Unity](images/mr-learning-base/base-02-section2-step1-1.png)

2. <span data-ttu-id="c3b95-133">Nella finestra **Build Settings** (Impostazioni di compilazione) selezionare **Universal Windows Platform** (Piattaforma UWP) e quindi fare clic sul pulsante **Switch Platform** (Cambia piattaforma):</span><span class="sxs-lookup"><span data-stu-id="c3b95-133">In the **Build Settings** window, select **Universal Windows Platform** and then click the **Switch Platform** button:</span></span>

![Finestra Build Settings di Unity con la piattaforma UWP selezionata in sostituzione della piattaforma Standalone](images/mr-learning-base/base-02-section2-step1-2.png)

3. <span data-ttu-id="c3b95-135">Attendere che venga completato il cambiamento di piattaforma e quindi chiudere la finestra **Build Settings** (Impostazioni di compilazione).</span><span class="sxs-lookup"><span data-stu-id="c3b95-135">Wait for Unity to finish switching the platform, and then close the **Build Settings** window.</span></span>

## <a name="importing-the-textmeshpro-essential-resources"></a><span data-ttu-id="c3b95-136">Importazione delle risorse essenziali TextMeshPro</span><span class="sxs-lookup"><span data-stu-id="c3b95-136">Importing the TextMeshPro Essential Resources</span></span>

<span data-ttu-id="c3b95-137">Le risorse essenziali TextMeshPro sono richieste dagli elementi dell'interfaccia utente di MRTK.</span><span class="sxs-lookup"><span data-stu-id="c3b95-137">The TextMeshPro Essential Resources are required by MRTK's UI elements.</span></span> <span data-ttu-id="c3b95-138">Se non si prevede di usare gli elementi dell'interfaccia utente di MRTK nel progetto, è possibile ignorare questo passaggio.</span><span class="sxs-lookup"><span data-stu-id="c3b95-138">If you are not planning to use MRTK's UI elements in your project, you can skip this step.</span></span>

1. <span data-ttu-id="c3b95-139">Sulla barra dei menu scegliere **Window** (Finestra) > **TextMeshPro** > **Import TMP Essential Resources** (Importa le risorse essenziali TMP).</span><span class="sxs-lookup"><span data-stu-id="c3b95-139">On the menu bar, select **Window** > **TextMeshPro** > **Import TMP Essential Resources**.</span></span>

![Percorso del menu Import TMP Essential Resources di Unity](images/mr-learning-base/base-02-section3-step1-1.png)

2. <span data-ttu-id="c3b95-141">Nella finestra **Import Unity Package** (Importa il pacchetto Unity) fare clic sul pulsante **All** (Tutti) per assicurarsi che vengano selezionati tutti gli asset e quindi fare clic sul pulsante **Import** (Importa) per importare gli asset:</span><span class="sxs-lookup"><span data-stu-id="c3b95-141">In the **Import Unity Package** window, click the **All** button to ensure that all the assets are selected, and then click the **Import** button to import the assets:</span></span>

![Finestra di importazione TMP Essential Resources di Unity](images/mr-learning-base/base-02-section3-step1-2.png)

## <a name="importing-the-mixed-reality-toolkit"></a><span data-ttu-id="c3b95-143">Importazione di Mixed Reality Toolkit</span><span class="sxs-lookup"><span data-stu-id="c3b95-143">Importing the Mixed Reality Toolkit</span></span>

1. <span data-ttu-id="c3b95-144">Scarica il pacchetto personalizzato di Unity:</span><span class="sxs-lookup"><span data-stu-id="c3b95-144">Download the Unity custom package:</span></span>

    [<span data-ttu-id="c3b95-145">Microsoft.MixedReality.Toolkit.Unity.Foundation.2.4.0.unitypackage</span><span class="sxs-lookup"><span data-stu-id="c3b95-145">Microsoft.MixedReality.Toolkit.Unity.Foundation.2.4.0.unitypackage</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.4.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.4.0.unitypackage)

2. <span data-ttu-id="c3b95-146">Sulla barra dei menu scegliere **Assets** (Asset) > **Import Package (Importa pacchetto)**  > **Custom Package** (Pacchetto personalizzato).</span><span class="sxs-lookup"><span data-stu-id="c3b95-146">On the menu bar, select **Assets** > **Import Package** > **Custom Package...**.</span></span>
3. <span data-ttu-id="c3b95-147">Nella finestra di dialogo **Import package** (Importa pacchetto) passare al percorso del pacchetto appena scaricato, selezionare il pacchetto e quindi fare clic sul pulsante **Open** (Apri).</span><span class="sxs-lookup"><span data-stu-id="c3b95-147">In the **Import package...** dialog, navigate to the location of the package you just downloaded, then select it, and then click the **Open** button.</span></span>
4. <span data-ttu-id="c3b95-148">Nella finestra **Import Unity Package** (Importa il pacchetto Unity) fare clic sul pulsante **All** (Tutti) per assicurarsi che vengano selezionati tutti gli asset e quindi fare clic sul pulsante **Import** (Importa) per importare gli asset.</span><span class="sxs-lookup"><span data-stu-id="c3b95-148">In the **Import Unity Package** window, click the **All** button to ensure that all the assets are selected, and then click the **Import** button to import the assets.</span></span>

## <a name="selecting-mrtk-and-project-settings"></a><span data-ttu-id="c3b95-149">Selezione delle impostazioni di MRTK e del progetto</span><span class="sxs-lookup"><span data-stu-id="c3b95-149">Selecting MRTK and project settings</span></span>

<span data-ttu-id="c3b95-150">Al termine dell'importazione del pacchetto dalla sezione precedente, viene visualizzata la finestra **MRTK Project Configurator** (Configuratore del progetto MRTK).</span><span class="sxs-lookup"><span data-stu-id="c3b95-150">After Unity has finished importing the package from the previous section, the **MRTK Project Configurator** window should appear.</span></span> <span data-ttu-id="c3b95-151">In caso contrario, è possibile aprirlo manualmente passando a **Mixed Reality Toolkit** > **Utilities** (Utilità) > **Configure Unity Project** (Configura il progetto Unity):</span><span class="sxs-lookup"><span data-stu-id="c3b95-151">If it doesn't, you can manually open it by going to **Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project**:</span></span>

![Percorso del menu Configure Unity Project di Unity](images/mr-learning-base/base-02-section5-step1-1.png)

1. <span data-ttu-id="c3b95-153">Nella finestra **MRTK Project Configurator** (Configuratore del progetto MRTK) espandere la sezione **Modify Configurations** (Modifica configurazioni), se necessario, e quindi verificare che tutte le opzioni siano selezionate.</span><span class="sxs-lookup"><span data-stu-id="c3b95-153">In the **MRTK Project Configurator** window, expand the **Modify Configurations** section, if necessary, and then ensure that all options are selected.</span></span>

![Finestra MRTK Project Configurator (Configuratore del progetto MRTK) di Unity in cui è visualizzata la sezione Modify Configurations (Modifica configurazioni)](images/mr-learning-base/base-02-section5-step1-2.png)

2. <span data-ttu-id="c3b95-155">Per applicare le impostazioni, fare clic sul pulsante **Apply** (Applica).</span><span class="sxs-lookup"><span data-stu-id="c3b95-155">To apply the settings, click the **Apply** button.</span></span>

![Pulsante Apply (Applica) in MRTK](images/mr-learning-base/apply.png)

> [!NOTE]
> <span data-ttu-id="c3b95-157">Viene usata la versione legacy di XR incorporata in Unity, invece del nuovo sistema di plug-in XR, perché il nuovo sistema non è completamente compatibile con le [versioni consigliate di Unity e MRTK](mr-learning-base-01.md#prerequisites) per questa serie di esercitazioni.</span><span class="sxs-lookup"><span data-stu-id="c3b95-157">You are using Unity's built-in legacy XR instead of the new XR Plugin System because the new system is not fully compatible with the [recommended Unity and MRTK versions](mr-learning-base-01.md#prerequisites) for this tutorial series.</span></span> <span data-ttu-id="c3b95-158">Se vengono visualizzati avvisi relativi alla deprecazione di XR incorporata, è possibile ignorarli.</span><span class="sxs-lookup"><span data-stu-id="c3b95-158">If you see any warnings about built-in XR being deprecated, you can ignore them.</span></span>

> [!TIP]
> <span data-ttu-id="c3b95-159">L'applicazione delle impostazioni predefinite di MRTK è facoltativa ma fortemente consigliata, poiché consente di configurare alcune impostazioni consigliate di Unity:</span><span class="sxs-lookup"><span data-stu-id="c3b95-159">Applying the MRTK Default Settings is optional but strongly recommended as it will help configure some recommended Unity settings:</span></span>
>
> * <span data-ttu-id="c3b95-160">Enable legacy XR (Abilita XR legacy): abilita VR per il progetto.</span><span class="sxs-lookup"><span data-stu-id="c3b95-160">Enable legacy XR: Enables VR for the project.</span></span>
> * <span data-ttu-id="c3b95-161">Set Single Pass Instanced rendering path (Imposta il percorso di rendering con istanze a singolo passaggio): migliora le prestazioni grafiche eseguendo la pipeline di rendering per entrambi gli occhi nella stessa chiamata di disegno.</span><span class="sxs-lookup"><span data-stu-id="c3b95-161">Set Single Pass Instanced rendering path: Improves graphics performance by executing the render pipeline for both eyes in the same draw call.</span></span> <span data-ttu-id="c3b95-162">Per altre informazioni su questo argomento, è possibile fare riferimento alla sezione sul [rendering con istanze a singolo passaggio](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html#single-pass-instanced-rendering) della documentazione di MRTK relativa alle [prestazioni](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html).</span><span class="sxs-lookup"><span data-stu-id="c3b95-162">To learn more about this topic, you can refer to the [Single-Pass Instanced rendering](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html#single-pass-instanced-rendering) section of MRTK's [Performance](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html) documentation.</span></span>
> * <span data-ttu-id="c3b95-163">Set default Spatial Awareness layer (Imposta livello di consapevolezza spaziale predefinito): crea un livello di Unity denominato Spatial Awareness e configura MRTK per l'uso di questo livello per la mesh di consapevolezza spaziale.</span><span class="sxs-lookup"><span data-stu-id="c3b95-163">Set default Spatial Awareness layer: Creates a Unity Layer named Spatial Awareness and configures MRTK to use this layer for the spatial awareness mesh.</span></span> <span data-ttu-id="c3b95-164">Per altre informazioni sui livelli di Unity, vedere la documentazione relativa alla <a href="https://docs.unity3d.com/Manual/Layers.html" target="_blank">personalizzazione dell'area di lavoro</a> di Unity.</span><span class="sxs-lookup"><span data-stu-id="c3b95-164">To learn more about Unity Layers, you can refer to Unity's <a href="https://docs.unity3d.com/Manual/Layers.html" target="_blank">Customizing Your Workspace</a> documentation.</span></span>

3. <span data-ttu-id="c3b95-165">Sulla barra dei menu scegliere **Edit** (Modifica) > **Project Settings** (Impostazioni progetto).</span><span class="sxs-lookup"><span data-stu-id="c3b95-165">On the menu bar, select **Edit** > **Project Settings...** .</span></span>

4. <span data-ttu-id="c3b95-166">Nella finestra **Project Settings** (Impostazioni progetto) selezionare **Player** (Lettore), fare clic sull'elenco a discesa **XR Settings** (Impostazioni XR) e quindi selezionare la casella accanto a **Virtual Reality Supported** (Realtà virtuale supportata):</span><span class="sxs-lookup"><span data-stu-id="c3b95-166">In the **Project Settings** window, select **Player**, then click the **XR Settings** dropdown, and then select the box next to **Virtual Reality Supported**:</span></span>

![Finestra XR Settings(Impostazioni XR) di Unity in cui è visualizzata la casella Virtual Reality Supported (Realtà virtuale supportata)](images/mr-learning-base/base-02-section5-step2-2.png)

<span data-ttu-id="c3b95-168">Viene importato Windows Mixed Reality SDK:</span><span class="sxs-lookup"><span data-stu-id="c3b95-168">This imports the Windows Mixed Reality SDK:</span></span>

![Finestra XR Settings(Impostazioni XR) di Unity in cui è visualizzata la sezione Virtual Reality SDKs (Virtual Reality SDK)](images/mr-learning-base/mixed-reality-sdk.png)

<span data-ttu-id="c3b95-170">Al termine dell'importazione di Windows Mixed Reality SDK, viene visualizzata di nuovo la finestra **MRTK Project Configurator** (Configuratore del progetto MRTK).</span><span class="sxs-lookup"><span data-stu-id="c3b95-170">After Unity has finished importing the Windows Mixed Reality SDK, the **MRTK Project Configurator** window should appear again.</span></span> <span data-ttu-id="c3b95-171">In caso contrario, selezionare **Mixed Reality Toolkit** > **Utilities** (Utilità) > **Configure Unity Project** (Configura il progetto Unity) per aprirla.</span><span class="sxs-lookup"><span data-stu-id="c3b95-171">If it doesn't, select **Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project** to open it.</span></span>

5. <span data-ttu-id="c3b95-172">Nella finestra **MRTK Project Configurator** (Configuratore del progetto MRTK) fare clic sull'elenco a discesa **Audio spatializer** (Spazializzatore audio) e quindi selezionare **MS HRTF Spatializer** (Spazializzatore MS HRTF).</span><span class="sxs-lookup"><span data-stu-id="c3b95-172">In the **MRTK Project Configurator** window, click the **Audio spatializer** dropdown, and then select **MS HRTF Spatializer**.</span></span>

![Finestra Project Settings (Impostazioni progetto) in cui sono visualizzate le opzioni Audio spatializer (Spazializzatore audio)](images/mr-learning-base/base-02-section5-step2-3.png)

6. <span data-ttu-id="c3b95-174">Fare clic sul pulsante **Applica**.</span><span class="sxs-lookup"><span data-stu-id="c3b95-174">Click the **Apply** button.</span></span> <span data-ttu-id="c3b95-175">La finestra **MRTK Project Configurator** (Configuratore del progetto MRTK) viene chiusa.</span><span class="sxs-lookup"><span data-stu-id="c3b95-175">This closes the **MRTK Project Configurator** window.</span></span>

    > [!TIP]
    > <span data-ttu-id="c3b95-176">L'impostazione della proprietà Audio spatializer (Spazializzatore audio) è facoltativa, ma può migliorare l'esperienza audio nel progetto.</span><span class="sxs-lookup"><span data-stu-id="c3b95-176">Setting the Audio spatializer property is optional but may improve the audio experience in your project.</span></span> <span data-ttu-id="c3b95-177">Se si imposta questa proprietà su MS HRTF Spatializer, questo plug-in di spazializzatore verrà usato quando la proprietà AudioSource.spatialize di Unity è abilitata.</span><span class="sxs-lookup"><span data-stu-id="c3b95-177">If you set it to MS HRTF Spatializer, this spatializer plugin will be used when Unity's AudioSource.spatialize property is enabled.</span></span> <span data-ttu-id="c3b95-178">Per altre informazioni su questo argomento, è possibile fare riferimento alle esercitazioni sull'audio spaziale.</span><span class="sxs-lookup"><span data-stu-id="c3b95-178">To learn more about this topic, you can refer to the Spatial audio tutorials.</span></span>

7. <span data-ttu-id="c3b95-179">Nella finestra **Project Settings** (Impostazioni progetto) fare clic sull'elenco a discesa **Depth Format** (Formato profondità) e quindi selezionare **16-bit depth** (Profondità a 16 bit):</span><span class="sxs-lookup"><span data-stu-id="c3b95-179">In the **Project Settings** window, click the **Depth Format** dropdown, and then select **16-bit depth**:</span></span>

    :::image type="content" source="images/mr-learning-base/base-02-section5-step2-4.png" alt-text="Area XR Settings (Impostazioni XR) di Unity in cui è selezionata l'opzione 16-bit depth (Profondità a 16 bit).":::

    > [!TIP]
    > <span data-ttu-id="c3b95-181">La riduzione del formato profondità a 16 bit è facoltativa, ma consente di migliorare le prestazioni grafiche nel progetto.</span><span class="sxs-lookup"><span data-stu-id="c3b95-181">Reducing the Depth Format to 16-bit is optional but may help improve graphics performance in your project.</span></span> <span data-ttu-id="c3b95-182">Per altre informazioni su questo argomento, è possibile fare riferimento alla sezione sulla [condivisione del buffer di intensità (HoloLens)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html#depth-buffer-sharing-hololens) della documentazione di MRTK relativa alle [prestazioni](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html).</span><span class="sxs-lookup"><span data-stu-id="c3b95-182">To learn more about this topic, you can refer to the [Depth buffer sharing (HoloLens)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html#depth-buffer-sharing-hololens) section of MRTK's [Performance](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html) documentation.</span></span>

8. <span data-ttu-id="c3b95-183">Fare clic sull'elenco a discesa **Publishing Settings** (Impostazioni di pubblicazione) e quindi nella casella **Package name** (Nome pacchetto) immettere un nome appropriato, ad esempio "MRTK-Tutorials-Getting-Started".</span><span class="sxs-lookup"><span data-stu-id="c3b95-183">Click the **Publishing Settings** drop-down, and then in the **Package name** box, enter a suitable name (for example, "MRTK-Tutorials-Getting-Started").</span></span>

    :::image type="content" source="images/mr-learning-base/base-02-section5-step2-5.png" alt-text="Finestra Publishing Settings (Impostazioni di pubblicazione) di Unity con il nome pacchetto configurato.":::

    <span data-ttu-id="c3b95-185">**Nome pacchetto e nome prodotto**</span><span class="sxs-lookup"><span data-stu-id="c3b95-185">**Package Name and Product Name**</span></span>

    - <span data-ttu-id="c3b95-186">Il valore di 'Package name' (Nome del pacchetto) è l'identificatore univoco dell'app.</span><span class="sxs-lookup"><span data-stu-id="c3b95-186">The 'Package name' is the unique identifier for the app.</span></span> <span data-ttu-id="c3b95-187">Creare questo identificatore prima di distribuire l'app per evitare di sovrascrivere app installate in precedenza.</span><span class="sxs-lookup"><span data-stu-id="c3b95-187">You should create this identifier before deploying the app to avoid overwriting previously installed apps.</span></span>
    - <span data-ttu-id="c3b95-188">Il valore di 'Product Name' (Nome del prodotto) è il nome visualizzato nel menu di avvio di HoloLens.</span><span class="sxs-lookup"><span data-stu-id="c3b95-188">The 'Product Name' is the name displayed in the HoloLens Start menu.</span></span> <span data-ttu-id="c3b95-189">Per semplificare l'individuazione dell'app durante lo sviluppo, è possibile anteporre un carattere di sottolineatura al nome in modo che compaia all'inizio dell'elenco.</span><span class="sxs-lookup"><span data-stu-id="c3b95-189">To make the app easier to locate during development, you can add an underscore in front of the name to sort it to the top.</span></span>

    :::image type="content" source="images/mr-learning-base/product-name.png" alt-text="Finestra Project Settings (Impostazioni progetto) di Unity con il nome prodotto configurato.":::

9. <span data-ttu-id="c3b95-191">Chiudere la finestra **Project Settings** (Impostazioni progetto).</span><span class="sxs-lookup"><span data-stu-id="c3b95-191">Close the **Project Settings** window.</span></span>

## <a name="creating-and-configuring-the-scene"></a><span data-ttu-id="c3b95-192">Creazione e configurazione della scena</span><span class="sxs-lookup"><span data-stu-id="c3b95-192">Creating and configuring the scene</span></span>

1. <span data-ttu-id="c3b95-193">Sulla barra dei menu scegliere **File** > **New Scene** (Nuova scena).</span><span class="sxs-lookup"><span data-stu-id="c3b95-193">On the menu bar, select **File** > **New Scene**.</span></span>
2. <span data-ttu-id="c3b95-194">Per aggiungere MRTK alla scena, sulla barra dei menu scegliere **Mixed Reality Toolkit** > **Add to Scene and Configure** (Aggiungi alla scena e configura).</span><span class="sxs-lookup"><span data-stu-id="c3b95-194">To add the MRTK to the scene, on the menu bar, select **Mixed Reality Toolkit** > **Add to Scene and Configure...**.</span></span>

    :::image type="content" source="images/mr-learning-base/base-02-section6-step1-2.png" alt-text="Percorso del menu Add to Scene and Configure (Aggiungi alla scena e configura) di Unity.":::

3. <span data-ttu-id="c3b95-196">Nella finestra **Hierarchy** (Gerarchia) assicurarsi che sia selezionato l'oggetto **MixedRealityToolkit**.</span><span class="sxs-lookup"><span data-stu-id="c3b95-196">In the **Hierarchy** window, ensure that **MixedRealityToolkit** is selected.</span></span>

    :::image type="content" source="images/mr-learning-base/select-mixed-reality-toolkit.png" alt-text="Assicurarsi che l'oggetto MixedRealityTookit sia selezionato.":::

4. <span data-ttu-id="c3b95-198">Nella sezione **MixedRealityToolkit** della finestra **Inspector** (Controllo) verificare che il profilo di configurazione sia impostato su **DefaultMixedRealityToolkitConfigurationProfile**:</span><span class="sxs-lookup"><span data-stu-id="c3b95-198">In the **Inspector** window's **MixedRealityToolkit** section, verify that the configuration profile is set to **DefaultMixedRealityToolkitConfigurationProfile**:</span></span>

    :::image type="content" source="images/mr-learning-base/base-02-section6-step1-3.png" alt-text="Componente MixedRealityToolkit di Unity con DefaultMixedRealityTookitConfigurationProfile selezionato.":::

    > [!IMPORTANT]
    > <span data-ttu-id="c3b95-200">Durante le attività di sviluppo per HoloLens viene usato in genere DefaultHoloLens2ConfigurationProfile.</span><span class="sxs-lookup"><span data-stu-id="c3b95-200">Typically, you will use the DefaultHoloLens2ConfigurationProfile when developing for HoloLens.</span></span> <span data-ttu-id="c3b95-201">Tuttavia, per questa esercitazione si userà DefaultMixedRealityToolkitConfigurationProfile.</span><span class="sxs-lookup"><span data-stu-id="c3b95-201">However, for this tutorial, you will use the DefaultMixedRealityToolkitConfigurationProfile.</span></span> <span data-ttu-id="c3b95-202">Nell'esercitazione successiva, riguardante la [configurazione dei profili MRTK](mr-learning-base-03.md), si passerà a DefaultHoloLens2ConfigurationProfile.</span><span class="sxs-lookup"><span data-stu-id="c3b95-202">In the next tutorial, [Configuring the MRTK profiles](mr-learning-base-03.md), you will change to the DefaultHoloLens2ConfigurationProfile.</span></span>

5. <span data-ttu-id="c3b95-203">Sulla barra dei menu scegliere **File** > **Save As** (Salva con nome).</span><span class="sxs-lookup"><span data-stu-id="c3b95-203">On the menu bar, select **File** > **Save As...**</span></span>
6. <span data-ttu-id="c3b95-204">Nella finestra di dialogo **Save scene** (Salva scena) passare alla cartella **Scenes** (Scene) del progetto.</span><span class="sxs-lookup"><span data-stu-id="c3b95-204">In the **Save Scene** dialog, navigate to your project's **Scenes** folder.</span></span> <span data-ttu-id="c3b95-205">Nella casella **File name** (Nome file) assegnare alla scena un nome appropriato, ad esempio "\_GettingStarted\_", e quindi fare clic sul pulsante **Save** (Salva).</span><span class="sxs-lookup"><span data-stu-id="c3b95-205">In the **File name** box, give your scene a suitable name (for example, "\_GettingStarted\_"), and then click the **Save** button.</span></span>

    :::image type="content" source="images/mr-learning-base/base-02-section6-step1-5.png" alt-text="Finestra del prompt di salvataggio della scena di Unity.":::

## <a name="building-and-deploying-to-your-hololens-2"></a><span data-ttu-id="c3b95-207">Compilazione e distribuzione in HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="c3b95-207">Building and deploying to your HoloLens 2</span></span>

> <span data-ttu-id="c3b95-208">Prima di compilare sul dispositivo, verificare quanto segue:</span><span class="sxs-lookup"><span data-stu-id="c3b95-208">Before building to your device, confirm the following:</span></span>
- <span data-ttu-id="c3b95-209">Il dispositivo è in modalità sviluppatore.</span><span class="sxs-lookup"><span data-stu-id="c3b95-209">Your device is in Developer Mode.</span></span>
- <span data-ttu-id="c3b95-210">Il dispositivo è associato al computer di sviluppo.</span><span class="sxs-lookup"><span data-stu-id="c3b95-210">Your device is paired with your development computer.</span></span> <span data-ttu-id="c3b95-211">In caso contrario, verrà visualizzata la finestra di dialogo seguente in Visual Studio durante il processo di compilazione:</span><span class="sxs-lookup"><span data-stu-id="c3b95-211">If it's not, you will see the following dialog box in Visual Studio during the build process:</span></span>

![Immissione del PIN per l'associazione dei dispositivi](images/mr-learning-base/pin-request.png)

 <span data-ttu-id="c3b95-213">Per altre informazioni su entrambi questi passaggi, vedere [Uso di Visual Studio per la distribuzione e il debug](../../platform-capabilities-and-apis/using-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="c3b95-213">To learn more about both of these steps, see [Using Visual Studio to deploy and debug](../../platform-capabilities-and-apis/using-visual-studio.md).</span></span>

1. <span data-ttu-id="c3b95-214">Sulla barra dei menu scegliere **File** > **Build Settings** (Impostazioni di compilazione).</span><span class="sxs-lookup"><span data-stu-id="c3b95-214">On the menu bar, select **File** > **Build Settings...**.</span></span>
2. <span data-ttu-id="c3b95-215">Nella finestra **Build Settings** (Impostazioni di compilazione) fare clic sul pulsante **Add Open Scenes** (Aggiungi scene aperte) per aggiungere la scena corrente all'elenco **Scenes In Build** (Scene in compilazione).</span><span class="sxs-lookup"><span data-stu-id="c3b95-215">In the **Build Settings** window, click the **Add Open Scenes** button to add your current scene to the **Scenes In Build** list.</span></span>

![Aggiungere la scena corrente all'elenco "Scenes in Build" (Scene in compilazione)](images/mr-learning-base/base-02-section7-step1-1.png)

3. <span data-ttu-id="c3b95-217">Fare clic sul pulsante **Build**.</span><span class="sxs-lookup"><span data-stu-id="c3b95-217">Click the **Build** button.</span></span>

    :::image type="content" source="images/mr-learning-base/build-button.png" alt-text="Fare clic sul pulsante Build.":::

4. <span data-ttu-id="c3b95-219">Nella finestra di dialogo **Build Universal Windows Platform** (Compila piattaforma UWP) scegliere un percorso appropriato per memorizzare la build, ad esempio è possibile creare una cartella "Build" nella cartella "Esercitazioni di MRTK".</span><span class="sxs-lookup"><span data-stu-id="c3b95-219">In the **Build Universal Windows Platform** dialog, choose a suitable location to store your build (for example, you may want to create a "Builds" folder in your "MRTK Tutorials" folder).</span></span> <span data-ttu-id="c3b95-220">Creare una nuova cartella e assegnarle un nome appropriato, ad esempio "GettingStarted", selezionare la cartella e quindi fare clic sul pulsante **Select Folder** (Seleziona cartella) per avviare il processo di compilazione.</span><span class="sxs-lookup"><span data-stu-id="c3b95-220">Create a new folder and give it a suitable name (for example, "GettingStarted"), then select the folder, and then click the **Select Folder** button to start the build process.</span></span>

    :::image type="content" source="images/mr-learning-base/base-02-section7-step1-2.png" alt-text="Finestra di compilazione di Unity in cui è visualizzata la cartella della build.":::

    <span data-ttu-id="c3b95-222">Viene visualizzata una barra di stato che consente di restare aggiornati sullo stato di avanzamento della compilazione.</span><span class="sxs-lookup"><span data-stu-id="c3b95-222">A status bar appears and keeps you updated on your build progress.</span></span>

    :::image type="content" source="images/mr-learning-base/base-02-section7-step1-3.png" alt-text="Processo di compilazione di Unity in corso.":::

    > [!TIP]
    > <span data-ttu-id="c3b95-224">Puoi anche eseguire la distribuzione nell'[emulatore HoloLens](../../platform-capabilities-and-apis/using-the-hololens-emulator.md) o creare un [Pacchetto applicazione](https://docs.microsoft.com/windows/uwp/packaging/packaging-uwp-apps) per il sideload.</span><span class="sxs-lookup"><span data-stu-id="c3b95-224">You can also deploy to the [HoloLens Emulator](../../platform-capabilities-and-apis/using-the-hololens-emulator.md) or create an [App Package](https://docs.microsoft.com/windows/uwp/packaging/packaging-uwp-apps) for sideloading.</span></span>

5. <span data-ttu-id="c3b95-225">Al termine del processo di compilazione, in Esplora file passare al percorso in cui è stata memorizzata la build e quindi fare doppio clic sul file della soluzione per aprirlo in Visual Studio:</span><span class="sxs-lookup"><span data-stu-id="c3b95-225">When the build process has completed, in File Explorer, navigate to the location where you stored the build, and then double-click the solution file to open it in Visual Studio:</span></span>

    :::image type="content" source="images/mr-learning-base/base-02-section8-step1-1.png" alt-text="Esplora risorse in cui è selezionato il file appena creato per la soluzione di Visual Studio.":::

    > [!NOTE]
    > <span data-ttu-id="c3b95-227">Se Visual Studio chiede di installare nuovi componenti, dedica qualche minuto a verificare di disporre di tutti i componenti indispensabili come specificato nella documentazione **[Installare gli strumenti](../../install-the-tools.md)** .</span><span class="sxs-lookup"><span data-stu-id="c3b95-227">If Visual Studio asks you to install new components, take a moment to check that you have all the prerequisite components in the **[Install the Tools](../../install-the-tools.md)** documentation.</span></span>

6. <span data-ttu-id="c3b95-228">Configurare Visual Studio per HoloLens selezionando la configurazione **Master** o **Release**, l'architettura **ARM64** e **Dispositivo** come destinazione.</span><span class="sxs-lookup"><span data-stu-id="c3b95-228">Configure Visual Studio for HoloLens by selecting the **Master** or **Release** configuration, the **ARM64** architecture, and **Device** as the target.</span></span>

    > [!TIP]
    > <span data-ttu-id="c3b95-229">Se esegui la distribuzione in HoloLens (1a generazione), seleziona l'architettura **x86**.</span><span class="sxs-lookup"><span data-stu-id="c3b95-229">If you're deploying to HoloLens (1st generation), select the **x86** architecture.</span></span>

    :::image type="content" source="images/mr-learning-base/base-02-section8-step1-2.png" alt-text="Visual Studio configurato per la distribuzione in HoloLens 2.":::

    > [!NOTE]
    > <span data-ttu-id="c3b95-231">Per HoloLens, in genere la compilazione viene eseguita per l'architettura ARM.</span><span class="sxs-lookup"><span data-stu-id="c3b95-231">For HoloLens, you will typically build for the ARM architecture.</span></span> <span data-ttu-id="c3b95-232">Esiste tuttavia un <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank"><strong>problema noto</strong></a> in Unity 2019.3 che causa errori quando viene selezionata l'architettura di compilazione ARM in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c3b95-232">However, there is a  <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank"><strong>known issue</strong></a> in Unity 2019.3 that causes errors when selecting ARM as the build architecture in Visual Studio.</span></span> <span data-ttu-id="c3b95-233">La soluzione consigliata consiste nel compilare per ARM64.</span><span class="sxs-lookup"><span data-stu-id="c3b95-233">The recommended workaround is to build for ARM64.</span></span> <span data-ttu-id="c3b95-234">Se questa opzione non è applicabile, passa a **Modifica > Impostazioni progetto > Player (Lettore) > Altre impostazioni** e disabilita **Graphics Jobs** (Processi grafici).</span><span class="sxs-lookup"><span data-stu-id="c3b95-234">If that is not an option, go to **Edit > Project Settings > Player > Other Settings** and disable **Graphics Jobs**.</span></span>

    > [!NOTE]
    > <span data-ttu-id="c3b95-235">Se non viene visualizzata l'opzione Dispositivo come destinazione, potresti dover modificare il progetto di avvio per la soluzione di Visual Studio passando dal progetto IL2CPP al progetto UWP.</span><span class="sxs-lookup"><span data-stu-id="c3b95-235">If you don't see Device as a target option, you may need to change the startup project for the Visual Studio solution from the IL2CPP project to the UWP project.</span></span> <span data-ttu-id="c3b95-236">A tale scopo, in Esplora soluzioni fare clic con il pulsante destro del mouse su NomeProgetto (Windows universale) e quindi scegliere **Imposta come progetto di avvio**.</span><span class="sxs-lookup"><span data-stu-id="c3b95-236">To do this, in the Solution Explorer, right-click on YourProjectName (Universal Windows), and then select **Set as StartUp Project**.</span></span>

7. <span data-ttu-id="c3b95-237">Connettere HoloLens al computer e quindi eseguire una di queste operazioni:</span><span class="sxs-lookup"><span data-stu-id="c3b95-237">Connect your HoloLens to your computer, and then do one of the following:</span></span>
- <span data-ttu-id="c3b95-238">Per compilare l'app, distribuirla in HoloLens e avviarla automaticamente senza il debugger di Visual Studio associato, pertanto sulla barra dei menu scegliere **Debug** > **Avvia senza eseguire il debug**.</span><span class="sxs-lookup"><span data-stu-id="c3b95-238">To build the app, deploy it to your HoloLens, and start it automatically without the Visual Studio debugger attached, on the menu bar, select **Debug** > **Start Without Debugging**.</span></span>

    :::image type="content" source="images/mr-learning-base/base-02-section8-step1-3.png" alt-text="Percorso del menu di Visual Studio per l'avvio senza il debug.":::

- <span data-ttu-id="c3b95-240">Per compilare e distribuire l'app in HoloLens senza però avviarla automaticamente, sulla barra dei menu scegliere **Compila > Distribuisci soluzione**.</span><span class="sxs-lookup"><span data-stu-id="c3b95-240">To build and deploy the app to your HoloLens but not have it start automatically, on the menu bar, select **Build > Deploy Solution**.</span></span>

    > [!NOTE]
    ><span data-ttu-id="c3b95-241">Potrebbe essere visibile nell'app il profiler di diagnostica, che può essere attivato o disattivato tramite il comando vocale **Toggle Diagnostics** (Attiva/Disattiva diagnostica).</span><span class="sxs-lookup"><span data-stu-id="c3b95-241">You may notice the Diagnostics profiler in the app, which you can toggle on or off by using the speech command **Toggle Diagnostics**.</span></span> <span data-ttu-id="c3b95-242">È consigliabile mantenere visibile il profiler la maggior parte del tempo durante lo sviluppo per verificare quando le modifiche apportate all'app possono produrre effetti negativi sulle prestazioni.</span><span class="sxs-lookup"><span data-stu-id="c3b95-242">It's recommended that you keep the profiler visible most of the time during development to understand when changes to the app may impact performance.</span></span> <span data-ttu-id="c3b95-243">Le app HoloLens ad esempio devono [essere eseguite costantemente a 60 FPS](../../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md).</span><span class="sxs-lookup"><span data-stu-id="c3b95-243">For example, HoloLens apps should [continuously run at 60 FPS](../../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md).</span></span>

## <a name="congratulations"></a><span data-ttu-id="c3b95-244">Lezione completata</span><span class="sxs-lookup"><span data-stu-id="c3b95-244">Congratulations</span></span>

<span data-ttu-id="c3b95-245">A questo punto hai distribuito la tua prima app per HoloLens.</span><span class="sxs-lookup"><span data-stu-id="c3b95-245">You've now deployed your first HoloLens app.</span></span> <span data-ttu-id="c3b95-246">Esplorando, noterai una mesh di mapping spaziale che copre le superfici percepite da HoloLens.</span><span class="sxs-lookup"><span data-stu-id="c3b95-246">As you walk around, you should see a spatial mapping mesh covering the surfaces that are perceived by the HoloLens.</span></span> <span data-ttu-id="c3b95-247">Dovresti anche vedere indicatori sulle mani e sulle dita per il tracciamento delle mani e un contatore della frequenza dei fotogrammi per tenere sotto controllo le prestazioni dell'app.</span><span class="sxs-lookup"><span data-stu-id="c3b95-247">Additionally, you should see indicators on your hands and fingers for hand tracking and a frame rate counter for keeping an eye on app performance.</span></span> <span data-ttu-id="c3b95-248">Queste funzionalità sono solo alcune delle parti fondamentali incluse in MRTK.</span><span class="sxs-lookup"><span data-stu-id="c3b95-248">These features are just a few foundational pieces included with MRTK.</span></span> <span data-ttu-id="c3b95-249">Nelle esercitazioni successive aggiungerai contenuto alla scena per esplorare le funzionalità di HoloLens e MRTK.</span><span class="sxs-lookup"><span data-stu-id="c3b95-249">In the upcoming tutorials, you'll add content to your scene to explore the capabilities of HoloLens and the MRTK.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="c3b95-250">Esercitazione successiva: 3. Configurazione dei profili di MRTK</span><span class="sxs-lookup"><span data-stu-id="c3b95-250">Next Tutorial: 3. Configuring the MRTK profiles</span></span>](mr-learning-base-03.md)

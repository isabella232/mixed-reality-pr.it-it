---
title: Inizializzazione del progetto e distribuzione della prima applicazione
description: In questo corso viene illustrato come configurare il progetto Unity per Mixed Reality Toolkit (MRTK) e come distribuirlo in HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens, MRTK, mixed reality toolkit, UWP, TextMeshPro,
ms.localizationpriority: high
ms.openlocfilehash: c9cf580b1123002e9e8cdfd5c3914c3aa39e2825
ms.sourcegitcommit: 848b4b7bb8514c2e088a3a55512b1a8075d29093
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/07/2021
ms.locfileid: "107003130"
---
# <a name="2-initializing-your-project-and-deploying-your-first-application"></a><span data-ttu-id="afe8f-104">2. Inizializzazione del progetto e distribuzione della prima applicazione</span><span class="sxs-lookup"><span data-stu-id="afe8f-104">2. Initializing your project and deploying your first application</span></span>

<span data-ttu-id="afe8f-105">In questa esercitazione apprenderai come creare un nuovo progetto Unity, come configurarlo per lo sviluppo <a href="https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/" target="_blank">Mixed Reality Toolkit (MRTK)</a> e come importare MRTK.</span><span class="sxs-lookup"><span data-stu-id="afe8f-105">In this tutorial, you'll learn how to create a new Unity project, configure it for <a href="https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/" target="_blank">Mixed Reality Toolkit (MRTK)</a> development, and import MRTK.</span></span> <span data-ttu-id="afe8f-106">Verranno inoltre esaminati i processi di configurazione, compilazione e distribuzione di una scena Unity di base da Visual Studio a HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="afe8f-106">You'll also walk through configuring, building, and deploying a basic Unity scene from Visual Studio to your HoloLens 2.</span></span> <span data-ttu-id="afe8f-107">Dopo la distribuzione in HoloLens 2, dovrebbe essere visualizzata una mesh di mapping spaziale che copre le superfici percepite da HoloLens.</span><span class="sxs-lookup"><span data-stu-id="afe8f-107">Once you have deployed it to your HoloLens 2, you should see a spatial mapping mesh covering the surfaces that are perceived by the HoloLens.</span></span> <span data-ttu-id="afe8f-108">Dovresti anche vedere indicatori sulle mani e sulle dita per il tracciamento delle mani e un contatore della frequenza dei fotogrammi per tenere sotto controllo le prestazioni dell'app.</span><span class="sxs-lookup"><span data-stu-id="afe8f-108">Additionally, you should see indicators on your hands and fingers for hand tracking and a frame rate counter for keeping an eye on app performance.</span></span>

![MRTK](../../../develop/images/Unity_MRTK_MRFT_Flow.png)

## <a name="objectives"></a><span data-ttu-id="afe8f-110">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="afe8f-110">Objectives</span></span>

* <span data-ttu-id="afe8f-111">Apprendere come configurare Unity per lo sviluppo per HoloLens</span><span class="sxs-lookup"><span data-stu-id="afe8f-111">Learn how to configure Unity for HoloLens development</span></span>
* <span data-ttu-id="afe8f-112">Apprendere come compilare e distribuire l'app in HoloLens</span><span class="sxs-lookup"><span data-stu-id="afe8f-112">Learn how to build and deploy your app to HoloLens</span></span>
* <span data-ttu-id="afe8f-113">Sperimentare la mesh di mapping spaziale, le mesh manuali e il contatore della frequenza dei fotogrammi sul dispositivo HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="afe8f-113">Experience the spatial mapping mesh, hand meshes, and the framerate counter on HoloLens 2 device</span></span>

## <a name="creating-the-unity-project"></a><span data-ttu-id="afe8f-114">Creazione del progetto Unity</span><span class="sxs-lookup"><span data-stu-id="afe8f-114">Creating the Unity project</span></span>

<span data-ttu-id="afe8f-115">Avvia **Unity Hub**, seleziona la scheda **Projects** (Progetti) e fai clic sulla **freccia giù** accanto al pulsante **New** (Nuovo):</span><span class="sxs-lookup"><span data-stu-id="afe8f-115">Launch **Unity Hub**, select the **Projects** tab, and click the **down arrow** next to the **New** button:</span></span>

![Unity Hub con il pulsante New evidenziato](images/mr-learning-base/base-02-section1-step1-1.png)

<span data-ttu-id="afe8f-117">Nell'elenco a discesa seleziona la **versione** di Unity specificata nella sezione [Prerequisiti](mr-learning-base-01.md#prerequisites):</span><span class="sxs-lookup"><span data-stu-id="afe8f-117">In the dropdown, select the Unity **version** specified in the [Prerequisites](mr-learning-base-01.md#prerequisites):</span></span>

![Unity Hub con l'elenco a discesa per la seleziona della versione NEW](images/mr-learning-base/base-02-section1-step1-2.png)

> [!TIP]
> <span data-ttu-id="afe8f-119">Se la versione specifica di Unity non è disponibile in Unity Hub, puoi avviare l'installazione da <a href="https://unity3d.com/get-unity/download/archive" target="_blank">Download Archive</a> (Archivio download) di Unity.</span><span class="sxs-lookup"><span data-stu-id="afe8f-119">If the particular Unity version is not available in Unity Hub, you can initiate the installation from Unity's <a href="https://unity3d.com/get-unity/download/archive" target="_blank">Download Archive</a>.</span></span>

<span data-ttu-id="afe8f-120">Nella finestra Create a new project (Crea un nuovo progetto):</span><span class="sxs-lookup"><span data-stu-id="afe8f-120">In the Create a new project window:</span></span>

* <span data-ttu-id="afe8f-121">Assicurati che in **Templates** (Modelli) sia impostata l'opzione **3D**</span><span class="sxs-lookup"><span data-stu-id="afe8f-121">Ensure **Templates** is set to **3D**</span></span>
* <span data-ttu-id="afe8f-122">Immetti un nome appropriato nel campo **Project Name** (Nome progetto), ad esempio _MRTK Tutorials_</span><span class="sxs-lookup"><span data-stu-id="afe8f-122">Enter a suitable **Project Name**, for example, _MRTK Tutorials_</span></span>
* <span data-ttu-id="afe8f-123">Nel campo **Location** (Percorso) scegli un percorso appropriato in cui archiviare il progetto, ad esempio _D:\MixedRealityLearning_</span><span class="sxs-lookup"><span data-stu-id="afe8f-123">Choose a suitable **Location** to store your project, for example, _D:\MixedRealityLearning_</span></span>
* <span data-ttu-id="afe8f-124">Fai clic sul pulsante **Create** (Crea) per creare e avviare il nuovo progetto Unity</span><span class="sxs-lookup"><span data-stu-id="afe8f-124">Click the **Create** button to create and launch your new Unity project</span></span>

![Unity Hub con la finestra Create a new project compilata](images/mr-learning-base/base-02-section1-step1-3.png)

> [!CAUTION]
> <span data-ttu-id="afe8f-126">Se lavori in Windows, tieni presente che è previsto un limite (MAX_PATH) di 255 caratteri per il percorso.</span><span class="sxs-lookup"><span data-stu-id="afe8f-126">When working on Windows, there is a MAX_PATH limit of 255 characters.</span></span> <span data-ttu-id="afe8f-127">Dovresti pertanto salvare il progetto Unity in prossimità della radice dell'unità.</span><span class="sxs-lookup"><span data-stu-id="afe8f-127">Consequently, you should save the Unity project close to the root of the drive.</span></span>

<span data-ttu-id="afe8f-128">Attendi che Unity crei il progetto:</span><span class="sxs-lookup"><span data-stu-id="afe8f-128">Wait for Unity to create the project:</span></span>

![Creazione di un nuovo progetto Unity in corso](images/mr-learning-base/base-02-section1-step1-4.png)

## <a name="switching-the-build-platform"></a><span data-ttu-id="afe8f-130">Passaggio a un'altra piattaforma di compilazione</span><span class="sxs-lookup"><span data-stu-id="afe8f-130">Switching the build platform</span></span>

[!INCLUDE[](includes/switching-build-platform.md)]

## <a name="importing-the-textmeshpro-essential-resources"></a><span data-ttu-id="afe8f-131">Importazione delle risorse essenziali TextMeshPro</span><span class="sxs-lookup"><span data-stu-id="afe8f-131">Importing the TextMeshPro Essential Resources</span></span>

<span data-ttu-id="afe8f-132">Scegli **Window (Finestra)**  > **TextMeshPro** > **Import TMP Essential Resources** (Importa le risorse essenziali TMP) dal menu di Unity per aprire la finestra Import Unity Package (Importa pacchetto Unity):</span><span class="sxs-lookup"><span data-stu-id="afe8f-132">In the Unity menu, select **Window** > **TextMeshPro** > **Import TMP Essential Resources** to open the Import Unity Package window:</span></span>

![Percorso del menu Import TMP Essential Resources di Unity](images/mr-learning-base/base-02-section3-step1-1.png)

<span data-ttu-id="afe8f-134">Nella finestra Import Unity Package (Importa il pacchetto Unity), fai clic sul pulsante **All** (Tutti) per assicurarti che vengano selezionati tutti gli asset e quindi fai clic sul pulsante **Import** (Importa) per importare gli asset:</span><span class="sxs-lookup"><span data-stu-id="afe8f-134">In the Import Unity Package window, click the **All** button to ensure all the assets are selected, then click the **Import** button to import the assets:</span></span>

![Finestra di importazione TMP Essential Resources di Unity](images/mr-learning-base/base-02-section3-step1-2.png)

> [!TIP]
> <span data-ttu-id="afe8f-136">Le risorse essenziali TextMeshPro sono richieste dagli elementi dell'interfaccia utente di MRTK.</span><span class="sxs-lookup"><span data-stu-id="afe8f-136">The TextMeshPro Essential Resources are required by MRTK's UI elements.</span></span> <span data-ttu-id="afe8f-137">Puoi ignorare questo passaggio se non prevedi di usare gli elementi dell'interfaccia utente di MRTK nel progetto.</span><span class="sxs-lookup"><span data-stu-id="afe8f-137">You can skip this step if you are not planning to use MRTK's UI elements in your project.</span></span>

## <a name="importing-the-mixed-reality-toolkit"></a><span data-ttu-id="afe8f-138">Importazione di Mixed Reality Toolkit</span><span class="sxs-lookup"><span data-stu-id="afe8f-138">Importing the Mixed Reality Toolkit</span></span>

<span data-ttu-id="afe8f-139">Per importare il Toolkit di realtà mista nel progetto Unity, è necessario usare [lo strumento per la funzionalità di realtà mista](../welcome-to-mr-feature-tool.md) che consente agli sviluppatori di individuare, aggiornare e aggiungere pacchetti di funzionalità di realtà mista in progetti Unity.</span><span class="sxs-lookup"><span data-stu-id="afe8f-139">To Import Mixed Reality Toolkit into the Unity Project you will have to use [Mixed Reality Feature Tool](../welcome-to-mr-feature-tool.md) which allows  developers to discover, update, and add Mixed Reality feature packages into Unity projects.</span></span> <span data-ttu-id="afe8f-140">È possibile cercare i pacchetti in base al nome o alla categoria, visualizzarne le dipendenze e persino visualizzare le modifiche proposte al file manifesto del progetto prima dell'importazione.</span><span class="sxs-lookup"><span data-stu-id="afe8f-140">You can search packages by name or category, see their dependencies, and even view proposed changes to your projects manifest file before importing.</span></span>

<span data-ttu-id="afe8f-141">Scaricare la versione più recente dello strumento per le funzionalità di realtà mista dall' [area download Microsoft](https://aka.ms/MRFeatureTool), al termine del download, decomprimere il file e salvarlo sul desktop.</span><span class="sxs-lookup"><span data-stu-id="afe8f-141">Download the latest version of the Mixed Reality Feature Tool from the [Microsoft Download Center](https://aka.ms/MRFeatureTool), When the download is complete, unzip the file and save it to your desktop.</span></span>

> [!NOTE]
> <span data-ttu-id="afe8f-142">Prima di poter eseguire lo strumento per la funzionalità di realtà mista, installare il [runtime di .net 5,0](https://dotnet.microsoft.com/download/dotnet/5.0)</span><span class="sxs-lookup"><span data-stu-id="afe8f-142">Before you can run the Mixed Reality Feature Tool please install [.NET 5.0 runtime](https://dotnet.microsoft.com/download/dotnet/5.0)</span></span>

> [!NOTE]
> <span data-ttu-id="afe8f-143">Lo strumento per la funzionalità di realtà mista attualmente viene eseguito solo in Windows. per MacOS, seguire questa [procedura](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html#1-get-the-latest-mrtk-unity-packages) per scaricare e importare il Toolkit di realtà mista nel progetto Unity.</span><span class="sxs-lookup"><span data-stu-id="afe8f-143">The Mixed Reality Feature Tool currently only runs on Windows, For MacOS please follow this [procedure](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html#1-get-the-latest-mrtk-unity-packages) to download and import the Mixed Reality Toolkit into the unity project.</span></span>

<span data-ttu-id="afe8f-144">Aprire il file eseguibile **MixedRealityFeatureTool** dalla cartella scaricata per avviare lo strumento della funzionalità di realtà mista.</span><span class="sxs-lookup"><span data-stu-id="afe8f-144">Open the executable file **MixedRealityFeatureTool** from the downloaded folder to launch the Mixed Reality Feature Tool.</span></span>  

![Apertura di MixedRealityFeatureTool](images/mr-learning-base/base-02-section4-step1-1.png)


[!INCLUDE[](includes/importing-mrtk.md)]

## <a name="configuring-the-unity-project"></a><span data-ttu-id="afe8f-146">Configurazione del progetto Unity</span><span class="sxs-lookup"><span data-stu-id="afe8f-146">Configuring the Unity project</span></span>

### <a name="1-apply-the-mrtk-project-configurator-settings"></a><span data-ttu-id="afe8f-147">1. Applicare le impostazioni di MRTK Project Configurator (Configuratore del progetto MRTK)</span><span class="sxs-lookup"><span data-stu-id="afe8f-147">1. Apply the MRTK Project Configurator settings</span></span>

<span data-ttu-id="afe8f-148">Al termine dell'importazione del pacchetto dalla sezione precedente, viene visualizzata la finestra MRTK Project Configurator (Configuratore del progetto MRTK).</span><span class="sxs-lookup"><span data-stu-id="afe8f-148">After Unity has finished importing the package from the previous section, the MRTK Project Configurator window should appear.</span></span> <span data-ttu-id="afe8f-149">In caso contrario, è possibile aprirlo manualmente passando a **Mixed Reality Toolkit** > **Utilities** (Utilità) > **Configure Unity Project** (Configura il progetto Unity):</span><span class="sxs-lookup"><span data-stu-id="afe8f-149">If it doesn't, you can manually open it by going to **Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project**:</span></span>

![Percorso del menu Configure Unity Project di Unity](images/mr-learning-base/base-02-section5-step1-1.png)

<span data-ttu-id="afe8f-151">Nella finestra MRTK Project Configurator (Configuratore del progetto MRTK) espandi la sezione **Modify Configurations** (Modifica configurazioni), verifica che tutte le opzioni siano selezionate e fai clic sul pulsante **Apply** (Applica) per applicare le impostazioni:</span><span class="sxs-lookup"><span data-stu-id="afe8f-151">In the MRTK Project Configurator window, expand the **Modify Configurations** section, ensure all options are checked, and click the **Apply** button to apply the settings:</span></span>

![Finestra MRTK Project Configurator di Unity](images/mr-learning-base/base-02-section5-step1-2.png)

> [!TIP]
> <span data-ttu-id="afe8f-153">L'applicazione delle impostazioni predefinite di MRTK è facoltativa ma fortemente consigliata, poiché consente di configurare alcune impostazioni consigliate di Unity:</span><span class="sxs-lookup"><span data-stu-id="afe8f-153">Applying the MRTK Default Settings is optional but strongly recommended as it will help configure some recommended Unity settings:</span></span>

> * <span data-ttu-id="afe8f-154">Set Single Pass Instanced rendering path (Imposta il percorso di rendering con istanze a singolo passaggio): migliora le prestazioni grafiche eseguendo la pipeline di rendering per entrambi gli occhi nella stessa chiamata di disegno.</span><span class="sxs-lookup"><span data-stu-id="afe8f-154">Set Single Pass Instanced rendering path: Improves graphics performance by executing the render pipeline for both eyes in the same draw call.</span></span> <span data-ttu-id="afe8f-155">Per altre informazioni su questo argomento, è possibile fare riferimento alla sezione sul [rendering con istanze a singolo passaggio](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering) della documentazione di MRTK relativa alle [prestazioni](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering).</span><span class="sxs-lookup"><span data-stu-id="afe8f-155">To learn more about this topic, you can refer to the [Single-Pass Instanced rendering](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering) section of MRTK's [Performance](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering) documentation.</span></span>
> * <span data-ttu-id="afe8f-156">Set default Spatial Awareness layer (Imposta livello di consapevolezza spaziale predefinito): crea un livello di Unity denominato Spatial Awareness e configura MRTK per l'uso di questo livello per la mesh di consapevolezza spaziale.</span><span class="sxs-lookup"><span data-stu-id="afe8f-156">Set default Spatial Awareness layer: Creates a Unity Layer named Spatial Awareness and configures MRTK to use this layer for the spatial awareness mesh.</span></span> <span data-ttu-id="afe8f-157">Per altre informazioni sui livelli di Unity, vedere la documentazione relativa alla <a href="https://docs.unity3d.com/Manual/Layers.html" target="_blank">personalizzazione dell'area di lavoro</a> di Unity.</span><span class="sxs-lookup"><span data-stu-id="afe8f-157">To learn more about Unity Layers, you can refer to Unity's <a href="https://docs.unity3d.com/Manual/Layers.html" target="_blank">Customizing Your Workspace</a> documentation.</span></span>

### <a name="2-configure-additional-project-settings"></a><span data-ttu-id="afe8f-158">2. Configurare impostazioni di progetto aggiuntive</span><span class="sxs-lookup"><span data-stu-id="afe8f-158">2. Configure additional project settings</span></span>

[!INCLUDE[](includes/configuring-additional-project-settings.md)]

## <a name="creating-the-scene-and-configuring-mrtk"></a><span data-ttu-id="afe8f-159">Creazione della scena e configurazione di MRTK</span><span class="sxs-lookup"><span data-stu-id="afe8f-159">Creating the scene and configuring MRTK</span></span>

<span data-ttu-id="afe8f-160">Scegli **File** > **New Scene** (Nuova scena) dal menu di Unity per creare una nuova scena:</span><span class="sxs-lookup"><span data-stu-id="afe8f-160">In the Unity menu, select **File** > **New Scene** to create a new scene:</span></span>

![Percorso del menu New Scene di Unity](images/mr-learning-base/base-02-section6-step1-1.png)

<span data-ttu-id="afe8f-162">Scegli **Mixed Reality Toolkit** > **Add to Scene and Configure...** (Aggiungi alla scena e configura) dal menu di Unity per aggiungere MRTK alla scena corrente:</span><span class="sxs-lookup"><span data-stu-id="afe8f-162">In the Unity menu, select **Mixed Reality Toolkit** > **Add to Scene and Configure...** to add the MRTK to your current scene:</span></span>

![Percorso del menu Add to Scene and Configure... di Unity](images/mr-learning-base/base-02-section6-step1-2.png)

[!INCLUDE[](includes/changing-profile.md)]

<span data-ttu-id="afe8f-164">Dal menu di Unity scegli **File** > **Save As** (Salva con nome) per visualizzare la finestra Save Scene (Salva la scena):</span><span class="sxs-lookup"><span data-stu-id="afe8f-164">In the Unity menu, select **File** > **Save As...** to open the Save Scene window:</span></span>

![Percorso del menu Save As... di Unity](images/mr-learning-base/base-02-section6-step1-4.png)

> [!TIP]
> <span data-ttu-id="afe8f-166">La riduzione del formato profondità a 16 bit è facoltativa, ma consente di migliorare le prestazioni grafiche nel progetto.</span><span class="sxs-lookup"><span data-stu-id="afe8f-166">Reducing the Depth Format to 16-bit is optional but may help improve graphics performance in your project.</span></span> <span data-ttu-id="afe8f-167">Per ulteriori informazioni su questo argomento, è possibile fare riferimento alla sezione   <a href="/windows/mixed-reality/mrtk-unity/performance/perf-getting-started.md#single-pass-instanced-rendering" target="_blank">  HoloLens (depth buffer sharing) </a> della documentazione  <a href="/windows/mixed-reality/mrtk-unity/performance/perf-getting-started.md#single-pass-instanced-rendering" target="_blank"> sulle prestazioni </a> di MRTK.</span><span class="sxs-lookup"><span data-stu-id="afe8f-167">To learn more about this topic, you can refer to the   <a href="/windows/mixed-reality/mrtk-unity/performance/perf-getting-started.md#single-pass-instanced-rendering" target="_blank">  Depth buffer sharing (HoloLens) </a> section of MRTK's  <a href="/windows/mixed-reality/mrtk-unity/performance/perf-getting-started.md#single-pass-instanced-rendering" target="_blank"> Performance </a> documentation.</span></span>

![Finestra Save Scene di Unity con il prompt di salvataggio](images/mr-learning-base/base-02-section6-step1-5.png)

## <a name="importing-the-tutorial-assets"></a><span data-ttu-id="afe8f-169">Importazione degli asset dell'esercitazione</span><span class="sxs-lookup"><span data-stu-id="afe8f-169">Importing the tutorial assets</span></span>

<span data-ttu-id="afe8f-170">Scaricare il pacchetto personalizzato Unity seguente:</span><span class="sxs-lookup"><span data-stu-id="afe8f-170">Download the following Unity custom package:</span></span>

* [<span data-ttu-id="afe8f-171">MRTK. HoloLens2. Unity. Esercitations. assets. GettingStarted. 2.5.0.1. file unitypackage Tools</span><span class="sxs-lookup"><span data-stu-id="afe8f-171">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.5.0.1.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.5.0/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.5.0.1.unitypackage)

<span data-ttu-id="afe8f-172">Per importare un pacchetto personalizzato Unity, nel menu Unity selezionare **Asset**  >  **Import Package**  >  **Custom Package..** . per aprire il pacchetto di importazione... finestra</span><span class="sxs-lookup"><span data-stu-id="afe8f-172">To Import a Unity custom package, In the Unity menu, select **Assets** > **Import Package** > **Custom Package...** to open the Import package... window:</span></span>

![Importazione di un pacchetto personalizzato](images/mr-learning-base/base-02-section7-step1-1.png)

<span data-ttu-id="afe8f-174">Nel pacchetto di importazione... Selezionare il **MRTK. HoloLens2. Unity. Tutorials. assets. GettingStarted. 2.5.0.1. file unitypackage Tools** è stato scaricato e si fa clic sul pulsante Apri:</span><span class="sxs-lookup"><span data-stu-id="afe8f-174">In the Import package... window, select the **MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.5.0.1.unitypackage** you downloaded and click the Open button:</span></span>

![Selezione di un pacchetto di asset](images/mr-learning-base/base-02-section7-step1-2.png)

<span data-ttu-id="afe8f-176">Nella finestra Import Unity Package (Importa il pacchetto Unity), fai clic sul pulsante All (Tutti) per assicurarti che vengano selezionati tutti gli asset e quindi fai clic sul pulsante Import (Importa) per importare gli asset:</span><span class="sxs-lookup"><span data-stu-id="afe8f-176">In the Import Unity Package window, click the All button to ensure all the assets are selected, then click the Import button to import the assets:</span></span>

![Selezione di tutti gli asset da importare](images/mr-learning-base/base-02-section7-step1-3.png)

<span data-ttu-id="afe8f-178">Dopo l'importazione degli asset dell'esercitazione, la finestra Project (Progetto) avrà un aspetto simile al seguente:</span><span class="sxs-lookup"><span data-stu-id="afe8f-178">After you have imported the tutorial assets your Project window should look similar to this:</span></span>

![Finestra del progetto Unity dopo l'importazione di asset](images/mr-learning-base/base-02-section7-step1-4.png)

## <a name="configuring-the-scene"></a><span data-ttu-id="afe8f-180">Configurazione della scena</span><span class="sxs-lookup"><span data-stu-id="afe8f-180">Configuring the Scene</span></span>

<span data-ttu-id="afe8f-181">Nella finestra del progetto passare al Asset > MRTK. Tutorials. GettingStarted > cartella prefabbricates:</span><span class="sxs-lookup"><span data-stu-id="afe8f-181">In the Project window, navigate to the Assets > MRTK.Tutorials.GettingStarted > Prefabs folder:</span></span>

<span data-ttu-id="afe8f-182">Dalla finestra del progetto, fare clic e trascinare il prefabbricato **Cube** nella finestra gerarchia, quindi nella finestra di controllo configurare il componente **Transform** come indicato di seguito.</span><span class="sxs-lookup"><span data-stu-id="afe8f-182">From the Project window, click-and-drag the **Cube** prefab on to the Hierarchy window, then in the Inspector window configure its **Transform** component as follows</span></span>

* <span data-ttu-id="afe8f-183">**Posizione**: X = 0, Y = 0, Z = 0,5</span><span class="sxs-lookup"><span data-stu-id="afe8f-183">**Position**: X = 0, Y = 0, Z = 0.5</span></span>
* <span data-ttu-id="afe8f-184">**Rotation** (Rotazione): X = 0, Y = 0, Z = 0</span><span class="sxs-lookup"><span data-stu-id="afe8f-184">**Rotation**: X = 0, Y = 0, Z = 0</span></span>
* <span data-ttu-id="afe8f-185">**Scale** (Scala): X = 1, Y = 1, Z = 1</span><span class="sxs-lookup"><span data-stu-id="afe8f-185">**Scale**: X = 1, Y = 1, Z = 1</span></span>

![Aggiunta del cubo alla scena](images/mr-learning-base/base-02-section8-step1-1.png)

<span data-ttu-id="afe8f-187">Per concentrare l'attenzione sugli oggetti nella scena, è possibile fare doppio clic sull'oggetto **cubo** , quindi eseguire nuovamente lo zoom indietro:</span><span class="sxs-lookup"><span data-stu-id="afe8f-187">To focus in on the objects in the scene, you can double-click on the **Cube** object, and then zoom slightly in again:</span></span>

<span data-ttu-id="afe8f-188">Per interagire e acquisire un oggetto con le lancette rilevate, l'oggetto deve avere un componente Collider, ad esempio un componente di **Box Collider**, un componente di  **manipolazione degli oggetti (script)** e un componente **NearInteractionGrabbable (script)** .</span><span class="sxs-lookup"><span data-stu-id="afe8f-188">To interact and grab an object with tracked hands, the object must have Collider component for example a **Box Collider**,  **Object Manipulator (Script)** component and **NearInteractionGrabbable(Script)** component.</span></span>

<span data-ttu-id="afe8f-189">Con il **cubo** ancora selezionato nella finestra gerarchia, nella finestra di controllo fare clic sul pulsante **Aggiungi componente** , quindi cercare e selezionare script **manipolatore oggetto** per aggiungere lo script del manipolatore di oggetti all'oggetto cubo.</span><span class="sxs-lookup"><span data-stu-id="afe8f-189">With the **Cube** still selected in the Hierarchy window, in the Inspector window ,click on **Add Component** button, then search and select **Object Manipulator** script to add the Object Manipulator script to the cube object.</span></span>

![Aggiunta dell'oggetto manupulator al cubo](images/mr-learning-base/base-02-section8-step1-2.png)

<span data-ttu-id="afe8f-191">Ripetere lo stesso per aggiungere lo **script near Interactionable di interazione** al cubo</span><span class="sxs-lookup"><span data-stu-id="afe8f-191">Repeat the same to add **Near Interaction Grabbable script** to the cube</span></span>

![Aggiunta di near interactionable al cubo](images/mr-learning-base/base-02-section8-step1-3.png)

> [!NOTE]
> <span data-ttu-id="afe8f-193">Quando si aggiunge un manipolatore di oggetti (script), in questo caso, il gestore di vincoli (script) viene aggiunto automaticamente perché il manipolatore di oggetti (script) dipende da esso.</span><span class="sxs-lookup"><span data-stu-id="afe8f-193">When you add a Object Manipulator (Script), in this case, the Constraint Manager (Script) is automatically added because Object Manipulator (Script) depends on it.</span></span>

> [!NOTE]
> <span data-ttu-id="afe8f-194">Ai fini di questa esercitazione, i Collider sono già stati aggiunti all'oggetto Cube.</span><span class="sxs-lookup"><span data-stu-id="afe8f-194">For the purpose of this tutorial, colliders have already been added to the Cube Object.</span></span> <span data-ttu-id="afe8f-195">Per altre informazioni sui collisori, puoi visitare la documentazione <a href="https://docs.unity3d.com/Manual/CollidersOverview.html" target="_blank">corrispondente</a> di Unity.</span><span class="sxs-lookup"><span data-stu-id="afe8f-195">To learn more about colliders, you can visit Unity's <a href="https://docs.unity3d.com/Manual/CollidersOverview.html" target="_blank">Collider</a> documentation.</span></span>

<span data-ttu-id="afe8f-196">Per eseguire il test nell'editor di Unity, è possibile attivare la modalità di riproduzione e tenere premuto il **LeftShift** o **lo spazio** per abilitare il controller, il movimento del mouse sposterà il controller e anche può essere spostato più o più vicino alla fotocamera usando la rotellina del mouse.</span><span class="sxs-lookup"><span data-stu-id="afe8f-196">To test this in the Unity editor, you can enter the play mode and hold the **LeftShift** or **Space** key to enable the controller, Mouse movement will move the controller and also it can be moved further or closer to the camera using the mouse wheel.</span></span> <span data-ttu-id="afe8f-197">Quando il puntatore si trova sul cubo, premere e tenere premuto il **pulsante destro del mouse** per spostare l'oggetto cubo.</span><span class="sxs-lookup"><span data-stu-id="afe8f-197">Once the pointer is on the Cube  press and hold **Right Mouse Button** to move the the Cube object.</span></span>

![Modalità di gioco](images/mr-learning-base/base-02-section8-step1-4.png)

## <a name="building-your-application-to-your-hololens-2"></a><span data-ttu-id="afe8f-199">Compilazione dell'applicazione nel dispositivo HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="afe8f-199">Building your application to your HoloLens 2</span></span>

### <a name="1-build-the-unity-project"></a><span data-ttu-id="afe8f-200">1. Compilare il progetto Unity</span><span class="sxs-lookup"><span data-stu-id="afe8f-200">1. Build the Unity project</span></span>

<span data-ttu-id="afe8f-201">Dal menu di Unity scegli **File** > **Build Settings** (Impostazioni di compilazione) per visualizzare la finestra corrispondente.</span><span class="sxs-lookup"><span data-stu-id="afe8f-201">In the Unity menu, select **File** > **Build Settings...** to open the Build Settings window.</span></span>

<span data-ttu-id="afe8f-202">Nella finestra Build Settings (Impostazioni di compilazione), fai clic sul pulsante **Add Open Scenes** (Aggiungi scene aperte) per aggiungere la scena corrente all'elenco **Scenes In Build** (Scene in compilazione) e quindi fai clic sul pulsante **Build** (Compila) per visualizzare la finestra Build Universal Windows Platform (Compilazione UWP):</span><span class="sxs-lookup"><span data-stu-id="afe8f-202">In the Build Settings window, click the **Add Open Scenes** button to add your current scene to the **Scenes In Build** list, then click the **Build** button to open the Build Universal Windows Platform window:</span></span>

![Finestra Build Settings di Unity con la piattaforma UWP selezionata](images/mr-learning-base/base-02-section9-step1-1.png)

<span data-ttu-id="afe8f-204">Nella finestra Build Universal Windows Platform (Compilazione UWP), scegli un percorso appropriato in cui archiviare la compilazione, ad esempio _D:\MixedRealityLearning\Builds_, crea una nuova cartella e assegnale un nome adatto (ad esempio, _GettingStarted_) e quindi fai clic sul pulsante **Select Folder** (Seleziona cartella) per avviare il processo di compilazione:</span><span class="sxs-lookup"><span data-stu-id="afe8f-204">In the Build Universal Windows Platform window, choose a suitable location to store your build, for example, _D:\MixedRealityLearning\Builds_, create a new folder and give it a suitable name, for example, _GettingStarted_, and then click the **Select Folder** button to start the build process:</span></span>

![Finestra Build Settings di Unity con la finestra del prompt di selezione della cartella](images/mr-learning-base/base-02-section9-step1-2.png)

<span data-ttu-id="afe8f-206">Attendi che Unity completi il processo di compilazione:</span><span class="sxs-lookup"><span data-stu-id="afe8f-206">Wait for Unity to finish the build process:</span></span>

![Processo di compilazione di Unity in corso](images/mr-learning-base/base-02-section9-step1-3.png)

### <a name="2-build-and-deploy-the-application"></a><span data-ttu-id="afe8f-208">2. Compilare e distribuire l'applicazione</span><span class="sxs-lookup"><span data-stu-id="afe8f-208">2. Build and deploy the application</span></span>

<span data-ttu-id="afe8f-209">Al termine del processo di compilazione, Unity richiederà a Esplora file di Windows di aprire il percorso in cui è stata archiviata la compilazione.</span><span class="sxs-lookup"><span data-stu-id="afe8f-209">When the build process has completed, Unity will prompt Windows File Explorer to open the location you stored the build.</span></span> <span data-ttu-id="afe8f-210">Spostati all'interno della cartella e fai doppio clic sul file della soluzione per aprirlo in Visual Studio:</span><span class="sxs-lookup"><span data-stu-id="afe8f-210">Navigate inside the folder, and double-click the solution file to open it in Visual Studio:</span></span>

![Esplora risorse con la soluzione di Visual Studio appena creata selezionata](images/mr-learning-base/base-02-section10-step1-1.png)

> [!NOTE]
> <span data-ttu-id="afe8f-212">Se Visual Studio chiede di installare nuovi componenti, dedica qualche minuto a verificare di disporre di tutti i componenti indispensabili come specificato nella documentazione **[Installare gli strumenti](../../install-the-tools.md)** .</span><span class="sxs-lookup"><span data-stu-id="afe8f-212">If Visual Studio asks you to install new components, take a moment to check that you have all the prerequisite components in the **[Install the Tools](../../install-the-tools.md)** documentation.</span></span>

<span data-ttu-id="afe8f-213">Configura Visual Studio per HoloLens selezionando la configurazione **Master** o **Release**, l'architettura **ARM64** e **Dispositivo** come destinazione:</span><span class="sxs-lookup"><span data-stu-id="afe8f-213">Configure Visual Studio for HoloLens by selecting the **Master** or **Release** configuration, the **ARM64** architecture, and **Device** as target:</span></span>

![Visual Studio configurato per la distribuzione in HoloLens 2](images/mr-learning-base/base-02-section10-step1-2.png)

> [!TIP]
> <span data-ttu-id="afe8f-215">Se esegui la distribuzione in HoloLens (1a generazione), seleziona l'architettura **x86**.</span><span class="sxs-lookup"><span data-stu-id="afe8f-215">If you're deploying to HoloLens (1st generation), select the **x86** architecture.</span></span>

> [!NOTE]
> <span data-ttu-id="afe8f-216">Per HoloLens, in genere la compilazione viene eseguita per l'architettura ARM.</span><span class="sxs-lookup"><span data-stu-id="afe8f-216">For HoloLens, you will typically build for the ARM architecture.</span></span> <span data-ttu-id="afe8f-217">Esiste tuttavia un <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank"><strong>problema noto</strong></a> in Unity 2019.3 che causa errori quando viene selezionata l'architettura di compilazione ARM in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="afe8f-217">However, there is a  <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank"><strong>known issue</strong></a> in Unity 2019.3 that causes errors when selecting ARM as the build architecture in Visual Studio.</span></span> <span data-ttu-id="afe8f-218">La soluzione consigliata consiste nel compilare per ARM64.</span><span class="sxs-lookup"><span data-stu-id="afe8f-218">The recommended workaround is to build for ARM64.</span></span> <span data-ttu-id="afe8f-219">Se questa opzione non è applicabile, passa a **Modifica > Impostazioni progetto > Player (Lettore) > Altre impostazioni** e disabilita **Graphics Jobs** (Processi grafici).</span><span class="sxs-lookup"><span data-stu-id="afe8f-219">If that is not an option, go to **Edit > Project Settings > Player > Other Settings** and disable **Graphics Jobs**.</span></span>

> [!NOTE]
> <span data-ttu-id="afe8f-220">Se non viene visualizzata l'opzione Dispositivo come destinazione, potresti dover modificare il progetto di avvio per la soluzione di Visual Studio passando dal progetto IL2CPP al progetto UWP.</span><span class="sxs-lookup"><span data-stu-id="afe8f-220">If you don't see Device as a target option, you may need to change the startup project for the Visual Studio solution from the IL2CPP project to the UWP project.</span></span> <span data-ttu-id="afe8f-221">A tale scopo, in Esplora soluzioni fai clic con il pulsante destro del mouse su NomeProgetto (Windows universale) e scegli **Imposta come progetto di avvio**.</span><span class="sxs-lookup"><span data-stu-id="afe8f-221">To do this, in the Solution Explorer, right-click on YourProjectName (Universal Windows) and select **Set as StartUp Project**.</span></span>

<span data-ttu-id="afe8f-222">Connetti HoloLens al computer e quindi seleziona **Debug** > **Avvia senza eseguire il debug** per eseguire la compilazione e la distribuzione nel dispositivo:</span><span class="sxs-lookup"><span data-stu-id="afe8f-222">Connect your HoloLens to your computer, then select **Debug** > **Start Without Debugging** to build and deploy to your device:</span></span>

![Percorso del menu di avvio di Visual Studio senza debug](images/mr-learning-base/base-02-section10-step1-3.png)

> [!IMPORTANT]
> <span data-ttu-id="afe8f-224">Prima della compilazione nel dispositivo, quest'ultimo deve essere in modalità sviluppatore e associato al computer di sviluppo.</span><span class="sxs-lookup"><span data-stu-id="afe8f-224">Before building to your device, the device must be in Developer Mode and paired with your development computer.</span></span> <span data-ttu-id="afe8f-225">Per completare i due passaggi segui [queste istruzioni](../../platform-capabilities-and-apis/using-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="afe8f-225">Both of these steps can be completed by following [these instructions](../../platform-capabilities-and-apis/using-visual-studio.md).</span></span>

> [!TIP]
> <span data-ttu-id="afe8f-226">Puoi anche eseguire la distribuzione nell'[emulatore HoloLens](../../platform-capabilities-and-apis/using-the-hololens-emulator.md) o creare un [Pacchetto applicazione](/windows/uwp/packaging/packaging-uwp-apps) per il sideload.</span><span class="sxs-lookup"><span data-stu-id="afe8f-226">You can also deploy to the [HoloLens Emulator](../../platform-capabilities-and-apis/using-the-hololens-emulator.md) or create an [App Package](/windows/uwp/packaging/packaging-uwp-apps) for sideloading.</span></span>

<span data-ttu-id="afe8f-227">Usando Avvia senza eseguire il debug, l'app viene avviata nel dispositivo senza collegare il debugger di Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="afe8f-227">Using Start Without Debugging automatically starts the app on your device without the Visual Studio debugger attached.</span></span>

<span data-ttu-id="afe8f-228">Seleziona **Compila > Distribuisci soluzione** per eseguire la distribuzione nel dispositivo senza che l'app venga avviata automaticamente.</span><span class="sxs-lookup"><span data-stu-id="afe8f-228">Select **Build > Deploy Solution** to deploy to your device without having the app start automatically.</span></span>

> [!NOTE]
><span data-ttu-id="afe8f-229">Potrebbe essere visibile nell'app il profiler di diagnostica, che può essere attivato o disattivato tramite il comando vocale **Toggle Diagnostics** (Attiva/Disattiva diagnostica).</span><span class="sxs-lookup"><span data-stu-id="afe8f-229">You may notice the Diagnostics profiler in the app, which you can toggle on or off by using the speech command **Toggle Diagnostics**.</span></span> <span data-ttu-id="afe8f-230">È consigliabile mantenere visibile il profiler la maggior parte del tempo durante lo sviluppo per verificare quando le modifiche apportate all'app possono produrre effetti negativi sulle prestazioni.</span><span class="sxs-lookup"><span data-stu-id="afe8f-230">It's recommended that you keep the profiler visible most of the time during development to understand when changes to the app may impact performance.</span></span> <span data-ttu-id="afe8f-231">Le app HoloLens ad esempio devono [essere eseguite costantemente a 60 FPS](../../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md).</span><span class="sxs-lookup"><span data-stu-id="afe8f-231">For example, HoloLens apps should [continuously run at 60 FPS](../../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md).</span></span>

## <a name="congratulations"></a><span data-ttu-id="afe8f-232">Lezione completata</span><span class="sxs-lookup"><span data-stu-id="afe8f-232">Congratulations</span></span>

<span data-ttu-id="afe8f-233">A questo punto hai distribuito la tua prima app per HoloLens.</span><span class="sxs-lookup"><span data-stu-id="afe8f-233">You've now deployed your first HoloLens app.</span></span> <span data-ttu-id="afe8f-234">Dopo che l'app è stata aperta, dovrebbe essere visualizzato un oggetto cubo davanti all'utente e dovrebbe essere in grado di interagire con il cubo spostando l'app e anche quando si procede in questo modo, verrà visualizzata una mesh di mapping spaziale che copre le superfici percepite dal HoloLens.</span><span class="sxs-lookup"><span data-stu-id="afe8f-234">Once the app is opened you should see a Cube object in front of you and should be able to interact with the cube by moving it and also as you walk around, you should see a spatial mapping mesh covering the surfaces that are perceived by the HoloLens.</span></span> <span data-ttu-id="afe8f-235">Dovresti anche vedere indicatori sulle mani e sulle dita per il tracciamento delle mani e un contatore della frequenza dei fotogrammi per tenere sotto controllo le prestazioni dell'app.</span><span class="sxs-lookup"><span data-stu-id="afe8f-235">Additionally, you should see indicators on your hands and fingers for hand tracking and a frame rate counter for keeping an eye on app performance.</span></span> <span data-ttu-id="afe8f-236">Queste funzionalità sono solo alcune delle parti fondamentali incluse in MRTK.</span><span class="sxs-lookup"><span data-stu-id="afe8f-236">These features are just a few foundational pieces included with MRTK.</span></span> <span data-ttu-id="afe8f-237">Nelle esercitazioni successive aggiungerai contenuto alla scena per esplorare le funzionalità di HoloLens e MRTK.</span><span class="sxs-lookup"><span data-stu-id="afe8f-237">In the upcoming tutorials, you'll add content to your scene to explore the capabilities of HoloLens and the MRTK.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="afe8f-238">Esercitazione successiva: 3. Configurazione dei profili di MRTK</span><span class="sxs-lookup"><span data-stu-id="afe8f-238">Next Tutorial: 3. Configuring the MRTK profiles</span></span>](mr-learning-base-03.md)

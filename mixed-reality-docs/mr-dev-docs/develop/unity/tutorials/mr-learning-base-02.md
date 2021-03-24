---
title: Inizializzazione del progetto e distribuzione della prima applicazione
description: In questo corso viene illustrato come configurare il progetto Unity per Mixed Reality Toolkit (MRTK) e come distribuirlo in HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens, MRTK, mixed reality toolkit, UWP, TextMeshPro,
ms.localizationpriority: high
ms.openlocfilehash: da1c61abab70ae30ba187c6ee255923a552f3562
ms.sourcegitcommit: b01be2046d1e6728259568cb3e4ac7c677407b4b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/23/2021
ms.locfileid: "104890813"
---
# <a name="2-initializing-your-project-and-deploying-your-first-application"></a><span data-ttu-id="13287-104">2. Inizializzazione del progetto e distribuzione della prima applicazione</span><span class="sxs-lookup"><span data-stu-id="13287-104">2. Initializing your project and deploying your first application</span></span>

<span data-ttu-id="13287-105">In questa esercitazione apprenderai come creare un nuovo progetto Unity, come configurarlo per lo sviluppo <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank">Mixed Reality Toolkit (MRTK)</a> e come importare MRTK.</span><span class="sxs-lookup"><span data-stu-id="13287-105">In this tutorial, you'll learn how to create a new Unity project, configure it for <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank">Mixed Reality Toolkit (MRTK)</a> development, and import MRTK.</span></span> <span data-ttu-id="13287-106">Verranno inoltre esaminati i processi di configurazione, compilazione e distribuzione di una scena Unity di base da Visual Studio a HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="13287-106">You'll also walk through configuring, building, and deploying a basic Unity scene from Visual Studio to your HoloLens 2.</span></span> <span data-ttu-id="13287-107">Dopo la distribuzione in HoloLens 2, dovrebbe essere visualizzata una mesh di mapping spaziale che copre le superfici percepite da HoloLens.</span><span class="sxs-lookup"><span data-stu-id="13287-107">Once you have deployed it to your HoloLens 2, you should see a spatial mapping mesh covering the surfaces that are perceived by the HoloLens.</span></span> <span data-ttu-id="13287-108">Dovresti anche vedere indicatori sulle mani e sulle dita per il tracciamento delle mani e un contatore della frequenza dei fotogrammi per tenere sotto controllo le prestazioni dell'app.</span><span class="sxs-lookup"><span data-stu-id="13287-108">Additionally, you should see indicators on your hands and fingers for hand tracking and a frame rate counter for keeping an eye on app performance.</span></span>

![MRTK](../../../develop/images/Unity_MRTK_MRFT_Flow.png)


## <a name="objectives"></a><span data-ttu-id="13287-110">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="13287-110">Objectives</span></span>

* <span data-ttu-id="13287-111">Apprendere come configurare Unity per lo sviluppo per HoloLens</span><span class="sxs-lookup"><span data-stu-id="13287-111">Learn how to configure Unity for HoloLens development</span></span>
* <span data-ttu-id="13287-112">Apprendere come compilare e distribuire l'app in HoloLens</span><span class="sxs-lookup"><span data-stu-id="13287-112">Learn how to build and deploy your app to HoloLens</span></span>
* <span data-ttu-id="13287-113">Sperimentare la mesh di mapping spaziale, le mesh manuali e il contatore della frequenza dei fotogrammi sul dispositivo HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="13287-113">Experience the spatial mapping mesh, hand meshes, and the framerate counter on HoloLens 2 device</span></span>

## <a name="creating-the-unity-project"></a><span data-ttu-id="13287-114">Creazione del progetto Unity</span><span class="sxs-lookup"><span data-stu-id="13287-114">Creating the Unity project</span></span>

<span data-ttu-id="13287-115">Avvia **Unity Hub**, seleziona la scheda **Projects** (Progetti) e fai clic sulla **freccia giù** accanto al pulsante **New** (Nuovo):</span><span class="sxs-lookup"><span data-stu-id="13287-115">Launch **Unity Hub**, select the **Projects** tab, and click the **down arrow** next to the **New** button:</span></span>

![Unity Hub con il pulsante New evidenziato](images/mr-learning-base/base-02-section1-step1-1.png)

<span data-ttu-id="13287-117">Nell'elenco a discesa seleziona la **versione** di Unity specificata nella sezione [Prerequisiti](mr-learning-base-01.md#prerequisites):</span><span class="sxs-lookup"><span data-stu-id="13287-117">In the dropdown, select the Unity **version** specified in the [Prerequisites](mr-learning-base-01.md#prerequisites):</span></span>

![Unity Hub con l'elenco a discesa per la seleziona della versione NEW](images/mr-learning-base/base-02-section1-step1-2.png)

> [!TIP]
> <span data-ttu-id="13287-119">Se la versione specifica di Unity non è disponibile in Unity Hub, puoi avviare l'installazione da <a href="https://unity3d.com/get-unity/download/archive" target="_blank">Download Archive</a> (Archivio download) di Unity.</span><span class="sxs-lookup"><span data-stu-id="13287-119">If the particular Unity version is not available in Unity Hub, you can initiate the installation from Unity's <a href="https://unity3d.com/get-unity/download/archive" target="_blank">Download Archive</a>.</span></span>

<span data-ttu-id="13287-120">Nella finestra Create a new project (Crea un nuovo progetto):</span><span class="sxs-lookup"><span data-stu-id="13287-120">In the Create a new project window:</span></span>

* <span data-ttu-id="13287-121">Assicurati che in **Templates** (Modelli) sia impostata l'opzione **3D**</span><span class="sxs-lookup"><span data-stu-id="13287-121">Ensure **Templates** is set to **3D**</span></span>
* <span data-ttu-id="13287-122">Immetti un nome appropriato nel campo **Project Name** (Nome progetto), ad esempio _MRTK Tutorials_</span><span class="sxs-lookup"><span data-stu-id="13287-122">Enter a suitable **Project Name**, for example, _MRTK Tutorials_</span></span>
* <span data-ttu-id="13287-123">Nel campo **Location** (Percorso) scegli un percorso appropriato in cui archiviare il progetto, ad esempio _D:\MixedRealityLearning_</span><span class="sxs-lookup"><span data-stu-id="13287-123">Choose a suitable **Location** to store your project, for example, _D:\MixedRealityLearning_</span></span>
* <span data-ttu-id="13287-124">Fai clic sul pulsante **Create** (Crea) per creare e avviare il nuovo progetto Unity</span><span class="sxs-lookup"><span data-stu-id="13287-124">Click the **Create** button to create and launch your new Unity project</span></span>

![Unity Hub con la finestra Create a new project compilata](images/mr-learning-base/base-02-section1-step1-3.png)

> [!CAUTION]
> <span data-ttu-id="13287-126">Se lavori in Windows, tieni presente che è previsto un limite (MAX_PATH) di 255 caratteri per il percorso.</span><span class="sxs-lookup"><span data-stu-id="13287-126">When working on Windows, there is a MAX_PATH limit of 255 characters.</span></span> <span data-ttu-id="13287-127">Dovresti pertanto salvare il progetto Unity in prossimità della radice dell'unità.</span><span class="sxs-lookup"><span data-stu-id="13287-127">Consequently, you should save the Unity project close to the root of the drive.</span></span>

<span data-ttu-id="13287-128">Attendi che Unity crei il progetto:</span><span class="sxs-lookup"><span data-stu-id="13287-128">Wait for Unity to create the project:</span></span>

![Creazione di un nuovo progetto Unity in corso](images/mr-learning-base/base-02-section1-step1-4.png)

## <a name="switching-the-build-platform"></a><span data-ttu-id="13287-130">Passaggio a un'altra piattaforma di compilazione</span><span class="sxs-lookup"><span data-stu-id="13287-130">Switching the build platform</span></span>

<span data-ttu-id="13287-131">Dal menu di Unity scegli **File** > **Build Settings** (Impostazioni di compilazione) per visualizzare la finestra corrispondente:</span><span class="sxs-lookup"><span data-stu-id="13287-131">In the Unity menu, select **File** > **Build Settings...** to open the Build Settings window:</span></span>

![Percorso del menu Build Settings... di Unity](images/mr-learning-base/base-02-section2-step1-1.png)

<span data-ttu-id="13287-133">Nella finestra Build Settings (Impostazioni di compilazione), seleziona **Universal Windows Platform** e fai clic sul pulsante **Switch Platform** (Cambia piattaforma):</span><span class="sxs-lookup"><span data-stu-id="13287-133">In the Build Settings window, select **Universal Windows Platform** and click the **Switch Platform** button:</span></span>

![Finestra Build Settings di Unity con la piattaforma UWP selezionata in sostituzione della piattaforma Standalone](images/mr-learning-base/base-02-section2-step1-2.png)

<span data-ttu-id="13287-135">Attendi che Unity completi il passaggio all'altra piattaforma:</span><span class="sxs-lookup"><span data-stu-id="13287-135">Wait for Unity to finish switching the platform:</span></span>

![Passaggio di Unity all'altra piattaforma in corso](images/mr-learning-base/base-02-section2-step1-3.png)

<span data-ttu-id="13287-137">Una volta completato il passaggio all'altra piattaforma, fai clic sull'icona **x** di colore rosso per chiudere la finestra Build Settings (Impostazioni di compilazione):</span><span class="sxs-lookup"><span data-stu-id="13287-137">When Unity has finished switching the platform, click the red **x** icon to close the Build Settings window:</span></span>

![Finestra Build Settings di Unity con l'icona di chiusura evidenziata](images/mr-learning-base/base-02-section2-step1-4.png)

## <a name="importing-the-textmeshpro-essential-resources"></a><span data-ttu-id="13287-139">Importazione delle risorse essenziali TextMeshPro</span><span class="sxs-lookup"><span data-stu-id="13287-139">Importing the TextMeshPro Essential Resources</span></span>

<span data-ttu-id="13287-140">Scegli **Window (Finestra)**  > **TextMeshPro** > **Import TMP Essential Resources** (Importa le risorse essenziali TMP) dal menu di Unity per aprire la finestra Import Unity Package (Importa pacchetto Unity):</span><span class="sxs-lookup"><span data-stu-id="13287-140">In the Unity menu, select **Window** > **TextMeshPro** > **Import TMP Essential Resources** to open the Import Unity Package window:</span></span>

![Percorso del menu Import TMP Essential Resources di Unity](images/mr-learning-base/base-02-section3-step1-1.png)

<span data-ttu-id="13287-142">Nella finestra Import Unity Package (Importa il pacchetto Unity), fai clic sul pulsante **All** (Tutti) per assicurarti che vengano selezionati tutti gli asset e quindi fai clic sul pulsante **Import** (Importa) per importare gli asset:</span><span class="sxs-lookup"><span data-stu-id="13287-142">In the Import Unity Package window, click the **All** button to ensure all the assets are selected, then click the **Import** button to import the assets:</span></span>

![Finestra di importazione TMP Essential Resources di Unity](images/mr-learning-base/base-02-section3-step1-2.png)

> [!TIP]
> <span data-ttu-id="13287-144">Le risorse essenziali TextMeshPro sono richieste dagli elementi dell'interfaccia utente di MRTK.</span><span class="sxs-lookup"><span data-stu-id="13287-144">The TextMeshPro Essential Resources are required by MRTK's UI elements.</span></span> <span data-ttu-id="13287-145">Puoi ignorare questo passaggio se non prevedi di usare gli elementi dell'interfaccia utente di MRTK nel progetto.</span><span class="sxs-lookup"><span data-stu-id="13287-145">You can skip this step if you are not planning to use MRTK's UI elements in your project.</span></span>

## <a name="importing-the-mixed-reality-toolkit"></a><span data-ttu-id="13287-146">Importazione di Mixed Reality Toolkit</span><span class="sxs-lookup"><span data-stu-id="13287-146">Importing the Mixed Reality Toolkit</span></span>

<span data-ttu-id="13287-147">Per importare il Toolkit di realtà mista nel progetto Unity, è necessario usare [lo strumento per la funzionalità di realtà mista](https://docs.microsoft.com//windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool) che consente agli sviluppatori di individuare, aggiornare e aggiungere pacchetti di funzionalità di realtà mista in progetti Unity.</span><span class="sxs-lookup"><span data-stu-id="13287-147">To Import Mixed Reality Toolkit into the Unity Project you will have to use [Mixed Reality Feature Tool](https://docs.microsoft.com//windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool) which allows  developers to discover, update, and add Mixed Reality feature packages into Unity projects.</span></span> <span data-ttu-id="13287-148">È possibile cercare i pacchetti in base al nome o alla categoria, visualizzarne le dipendenze e persino visualizzare le modifiche proposte al file manifesto del progetto prima dell'importazione.</span><span class="sxs-lookup"><span data-stu-id="13287-148">You can search packages by name or category, see their dependencies, and even view proposed changes to your projects manifest file before importing.</span></span>

<span data-ttu-id="13287-149">Scaricare la versione più recente dello strumento per le funzionalità di realtà mista dall' [area download Microsoft](https://aka.ms/MRFeatureTool), al termine del download, decomprimere il file e salvarlo sul desktop.</span><span class="sxs-lookup"><span data-stu-id="13287-149">Download the latest version of the Mixed Reality Feature Tool from the [Microsoft Download Center](https://aka.ms/MRFeatureTool), When the download is complete, unzip the file and save it to your desktop.</span></span>

> [!NOTE]
> <span data-ttu-id="13287-150">Prima di poter eseguire lo strumento per la funzionalità di realtà mista, installare il [runtime di .net 5,0](https://dotnet.microsoft.com/download/dotnet/5.0)</span><span class="sxs-lookup"><span data-stu-id="13287-150">Before you can run the Mixed Reality Feature Tool please install [.NET 5.0 runtime](https://dotnet.microsoft.com/download/dotnet/5.0)</span></span>

> [!NOTE]
> <span data-ttu-id="13287-151">Lo strumento per la funzionalità di realtà mista attualmente viene eseguito solo in Windows. per MacOS, seguire questa [procedura](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html#1-get-the-latest-mrtk-unity-packages) per scaricare e importare il Toolkit di realtà mista nel progetto Unity.</span><span class="sxs-lookup"><span data-stu-id="13287-151">The Mixed Reality Feature Tool currently only runs on Windows, For MacOS please follow this [procedure](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html#1-get-the-latest-mrtk-unity-packages) to download and import the Mixed Reality Toolkit into the unity project.</span></span>

> [!NOTE]
> <span data-ttu-id="13287-152">È anche possibile scaricare manualmente i pacchetti MRTK dalla [pagina della versione di GitHub di MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases).</span><span class="sxs-lookup"><span data-stu-id="13287-152">You can also manually download MRTK packages from [MRTK Github's release page](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases).</span></span> <span data-ttu-id="13287-153">Importare i pacchetti MRTK usando il pacchetto di importazione asset-> di Unity-> pacchetto personalizzato.</span><span class="sxs-lookup"><span data-stu-id="13287-153">Import MRTK packages using Unity's Asset -> Import Package -> Custom Package menu.</span></span> 


<span data-ttu-id="13287-154">Aprire il file eseguibile **MixedRealityFeatureTool** dalla cartella scaricata per avviare lo strumento della funzionalità di realtà mista.</span><span class="sxs-lookup"><span data-stu-id="13287-154">Open the executable file **MixedRealityFeatureTool** from the downloaded folder to launch the Mixed Reality Feature Tool.</span></span>  

![Apertura di MixedRealityFeatureTool](images/mr-learning-base/base-02-section4-step1-1.png)

<span data-ttu-id="13287-156">Dopo aver aperto **MixedRealityFeatureTool** , fare clic su Start per iniziare a usare lo strumento per le funzionalità di realtà mista.</span><span class="sxs-lookup"><span data-stu-id="13287-156">Once **MixedRealityFeatureTool** is opened click on start to get started with Mixed Reality Feature Tool.</span></span>

![MixedRealityFeatureTool](images/mr-learning-base/base-02-section4-step1-2.png)

<span data-ttu-id="13287-158">È necessario impostare il percorso del progetto Unity di destinazione in modo da fornire il **percorso del progetto**, fare clic sui **tre puntini** di sospensione accanto al percorso del progetto e passare alla cartella del progetto nella finestra di esplorazione, ad esempio le _esercitazioni di D:\MixedRealityLearning\MRTK_.</span><span class="sxs-lookup"><span data-stu-id="13287-158">You need to set the location of the target unity project to provide the **Project path**, click on the **Three dots** next to the Project path and browse to your project folder in the explorer for example _D:\MixedRealityLearning\MRTK Tutorials_.</span></span> <span data-ttu-id="13287-159">Fare clic su' individua funzionalità' per il passaggio successivo.</span><span class="sxs-lookup"><span data-stu-id="13287-159">Click 'Discover Features' for the next step.</span></span>

![Percorso del progetto MixedRealityFeatureTool](images/mr-learning-base/base-02-section4-step1-2b.png)

<span data-ttu-id="13287-161">Le funzionalità sono raggruppate per categoria per semplificare la ricerca, fare clic sull'elenco a discesa del **Toolkit per realtà mista** per trovare i pacchetti relativi al Toolkit di realtà mista.</span><span class="sxs-lookup"><span data-stu-id="13287-161">Features are grouped by category to make things easier to find, click on **Mixed Reality Toolkit** dropdown to find packages relating to the Mixed Reality Toolkit.</span></span>

![Finestra MixedRealityFeatureTool](images/mr-learning-base/base-02-section4-step1-3.png)

<span data-ttu-id="13287-163">Controllare **mixed reality Toolkit Foundation**, quindi fare clic sull'elenco a discesa accanto per selezionare la versione richiesta di MRTK. per questa serie di esercitazioni selezionare **2.5.3**.</span><span class="sxs-lookup"><span data-stu-id="13287-163">Check the **Mixed Reality Toolkit Foundation**, and click on the dropdown next to it to select the required MRTK version, for this tutorial series please select **2.5.3**.</span></span> <span data-ttu-id="13287-164">Fare quindi clic sul pulsante **Ottieni funzionalità** per scaricare i pacchetti selezionati.</span><span class="sxs-lookup"><span data-stu-id="13287-164">then click on **Get features** button to download the selected packages.</span></span>

![Selezione della realtà mista](images/mr-learning-base/base-02-section4-step1-4.png)

<span data-ttu-id="13287-166">Viene presentato il pacchetto selezionato **mixed reality Toolkit Foundation 2.5.3** , insieme al relativo pacchetto di dipendenza **mixed reality Toolkit standard 2.5.3** nella finestra di **importazione delle funzionalità** .</span><span class="sxs-lookup"><span data-stu-id="13287-166">Selected package **Mixed Reality Toolkit Foundation 2.5.3** is presented, along with its dependence package **Mixed Reality Toolkit Standard Assets 2.5.3** in the **Import Features** window.</span></span>

> [!NOTE]
> <span data-ttu-id="13287-167">La finestra di dialogo visualizzata quando si Esplora la cartella del progetto Unity contiene ' _' come nome file.</span><span class="sxs-lookup"><span data-stu-id="13287-167">The dialog that's displayed when browsing for the Unity project folder contains '_' as the file name.</span></span> <span data-ttu-id="13287-168">Per abilitare la selezione della cartella, è necessario specificare un valore per il nome del file.</span><span class="sxs-lookup"><span data-stu-id="13287-168">There must be a value for the file name to enable the folder to be selected.</span></span>

<span data-ttu-id="13287-169">Fare quindi clic sul pulsante **convalida** per convalidare il pacchetto selezionato. verrà visualizzata una finestra popup con un messaggio in cui **non sono stati rilevati problemi di convalida** fare clic su **OK** per chiudere la finestra popup e fare clic sul pulsante **Importa** .</span><span class="sxs-lookup"><span data-stu-id="13287-169">Next click on the **Validate** button to validate the selected package, you will get a popup with message **No validation issues were detected** click on **OK** to close the popup and click on **Import** button.</span></span>

![Convalida della realtà mista](images/mr-learning-base/base-02-section4-step1-5.png)

<span data-ttu-id="13287-171">Fare clic sul pulsante **approva** per aggiungere il **Toolkit di realtà misto** al progetto.</span><span class="sxs-lookup"><span data-stu-id="13287-171">Click on **Approve** Button to add the **Mixed Reality Toolkit** into the project.</span></span>

![Approva la realtà mista](images/mr-learning-base/base-02-section4-step1-6.png)

<span data-ttu-id="13287-173">Quando si chiude lo strumento funzionalità di realtà mista e si torna a Unity, verranno caricati nuovi pacchetti.</span><span class="sxs-lookup"><span data-stu-id="13287-173">When you close Mixed Reality Feature Tool and return to Unity, new packages will be loaded.</span></span>

## <a name="configuring-the-unity-project"></a><span data-ttu-id="13287-174">Configurazione del progetto Unity</span><span class="sxs-lookup"><span data-stu-id="13287-174">Configuring the Unity project</span></span>

### <a name="1-apply-the-mrtk-project-configurator-settings"></a><span data-ttu-id="13287-175">1. Applicare le impostazioni di MRTK Project Configurator (Configuratore del progetto MRTK)</span><span class="sxs-lookup"><span data-stu-id="13287-175">1. Apply the MRTK Project Configurator settings</span></span>

<span data-ttu-id="13287-176">Al termine dell'importazione del pacchetto dalla sezione precedente, viene visualizzata la finestra MRTK Project Configurator (Configuratore del progetto MRTK).</span><span class="sxs-lookup"><span data-stu-id="13287-176">After Unity has finished importing the package from the previous section, the MRTK Project Configurator window should appear.</span></span> <span data-ttu-id="13287-177">In caso contrario, è possibile aprirlo manualmente passando a **Mixed Reality Toolkit** > **Utilities** (Utilità) > **Configure Unity Project** (Configura il progetto Unity):</span><span class="sxs-lookup"><span data-stu-id="13287-177">If it doesn't, you can manually open it by going to **Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project**:</span></span>

![Percorso del menu Configure Unity Project di Unity](images/mr-learning-base/base-02-section5-step1-1.png)

<span data-ttu-id="13287-179">Nella finestra MRTK Project Configurator (Configuratore del progetto MRTK) espandi la sezione **Modify Configurations** (Modifica configurazioni), verifica che tutte le opzioni siano selezionate e fai clic sul pulsante **Apply** (Applica) per applicare le impostazioni:</span><span class="sxs-lookup"><span data-stu-id="13287-179">In the MRTK Project Configurator window, expand the **Modify Configurations** section, ensure all options are checked, and click the **Apply** button to apply the settings:</span></span>

![Finestra MRTK Project Configurator di Unity](images/mr-learning-base/base-02-section5-step1-2.png)

> [!TIP]
> <span data-ttu-id="13287-181">L'applicazione delle impostazioni predefinite di MRTK è facoltativa ma fortemente consigliata, poiché consente di configurare alcune impostazioni consigliate di Unity:</span><span class="sxs-lookup"><span data-stu-id="13287-181">Applying the MRTK Default Settings is optional but strongly recommended as it will help configure some recommended Unity settings:</span></span>

> * <span data-ttu-id="13287-182">Set Single Pass Instanced rendering path (Imposta il percorso di rendering con istanze a singolo passaggio): migliora le prestazioni grafiche eseguendo la pipeline di rendering per entrambi gli occhi nella stessa chiamata di disegno.</span><span class="sxs-lookup"><span data-stu-id="13287-182">Set Single Pass Instanced rendering path: Improves graphics performance by executing the render pipeline for both eyes in the same draw call.</span></span> <span data-ttu-id="13287-183">Per altre informazioni su questo argomento, è possibile fare riferimento alla sezione sul [rendering con istanze a singolo passaggio](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/performance/perf-getting-started.md#single-pass-instanced-rendering) della documentazione di MRTK relativa alle [prestazioni](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/performance/perf-getting-started.md#single-pass-instanced-rendering).</span><span class="sxs-lookup"><span data-stu-id="13287-183">To learn more about this topic, you can refer to the [Single-Pass Instanced rendering](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/performance/perf-getting-started.md#single-pass-instanced-rendering) section of MRTK's [Performance](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/performance/perf-getting-started.md#single-pass-instanced-rendering) documentation.</span></span>
> * <span data-ttu-id="13287-184">Set default Spatial Awareness layer (Imposta livello di consapevolezza spaziale predefinito): crea un livello di Unity denominato Spatial Awareness e configura MRTK per l'uso di questo livello per la mesh di consapevolezza spaziale.</span><span class="sxs-lookup"><span data-stu-id="13287-184">Set default Spatial Awareness layer: Creates a Unity Layer named Spatial Awareness and configures MRTK to use this layer for the spatial awareness mesh.</span></span> <span data-ttu-id="13287-185">Per altre informazioni sui livelli di Unity, vedere la documentazione relativa alla <a href="https://docs.unity3d.com/Manual/Layers.html" target="_blank">personalizzazione dell'area di lavoro</a> di Unity.</span><span class="sxs-lookup"><span data-stu-id="13287-185">To learn more about Unity Layers, you can refer to Unity's <a href="https://docs.unity3d.com/Manual/Layers.html" target="_blank">Customizing Your Workspace</a> documentation.</span></span>

### <a name="2-configure-additional-project-settings"></a><span data-ttu-id="13287-186">2. Configurare impostazioni di progetto aggiuntive</span><span class="sxs-lookup"><span data-stu-id="13287-186">2. Configure additional project settings</span></span>

<span data-ttu-id="13287-187">Dal menu di Unity scegli **Edit** (Modifica) > **Project Settings** (Impostazioni del progetto) per visualizzare la finestra corrispondente:</span><span class="sxs-lookup"><span data-stu-id="13287-187">In the Unity menu, select **Edit** > **Project Settings...** to open the Project Settings window:</span></span>

<span data-ttu-id="13287-188">Nella finestra Impostazioni progetto selezionare **Player**  >  **XR Settings** e selezionare la casella di controllo **Virtual Reality supported** .</span><span class="sxs-lookup"><span data-stu-id="13287-188">In the Project Settings window, select **Player** > **XR Settings** and check the **Virtual Reality Supported** checkbox.</span></span> <span data-ttu-id="13287-189">L'esecuzione di questo processo richiede tempo.</span><span class="sxs-lookup"><span data-stu-id="13287-189">This process takes some time.</span></span> <span data-ttu-id="13287-190">Dopo aver selezionato la **realtà virtuale supportata** , fare clic sull' **+** icona e selezionare **realtà mista di Windows** per aggiungere l'SDK di realtà mista di Windows:</span><span class="sxs-lookup"><span data-stu-id="13287-190">Once **Virtual Reality Supported** is checked, click the **+** icon, and select **Windows Mixed Reality** to add the Windows Mixed Reality SDK:</span></span>

![Area XR Settings di Unity con Windows Mixed Reality SDK selezionato](images/mr-learning-base/base-02-section5-step2-4.png)

<span data-ttu-id="13287-192">Al termine dell'importazione di Windows Mixed Reality SDK, dovrebbe visualizzarsi di nuovo la finestra MRTK Project Configurator (Configuratore del progetto MRTK).</span><span class="sxs-lookup"><span data-stu-id="13287-192">After Unity has finished importing the Windows Mixed Reality SDK, the MRTK Project Configurator window should appear again.</span></span> <span data-ttu-id="13287-193">In caso contrario, è possibile aprirlo manualmente dal menu di Unity passando a Utility del **Toolkit di realtà mista**  >    >  **configurare il progetto Unity**</span><span class="sxs-lookup"><span data-stu-id="13287-193">If it doesn't, you can manually open it from the Unity menu by going to **Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project**</span></span>

<span data-ttu-id="13287-194">Nella finestra MRTK Project Configurator (Configuratore del progetto MRTK) usa l'elenco a discesa **Audio spatializer** (Spazializzatore audio) per selezionare **MS HRTF Spatializer** e quindi fai clic sul pulsante **Apply** (Applica) per applicare l'impostazione:</span><span class="sxs-lookup"><span data-stu-id="13287-194">In the MRTK Project Configurator window, use the **Audio spatializer** dropdown to select the **MS HRTF Spatializer**, then click the **Apply** button to apply the setting:</span></span>

![Impostazioni di Unity XR con l'opzione Aggiungi Windows Mixed Reality SDK selezionata](images/mr-learning-base/base-02-section5-step2-5.png)

> [!TIP]
><span data-ttu-id="13287-196">L'impostazione della proprietà Audio spatializer (Spazializzatore audio) è facoltativa, ma può migliorare l'esperienza audio nel progetto.</span><span class="sxs-lookup"><span data-stu-id="13287-196">Setting the Audio spatializer property is optional but may improve the audio experience in your project.</span></span> <span data-ttu-id="13287-197">Se si imposta questa proprietà su MS HRTF Spatializer, questo plug-in di spazializzatore verrà usato quando la proprietà AudioSource.spatialize di Unity è abilitata.</span><span class="sxs-lookup"><span data-stu-id="13287-197">If you set it to MS HRTF Spatializer, this spatializer plugin will be used when Unity's AudioSource.spatialize property is enabled.</span></span> <span data-ttu-id="13287-198">Per ulteriori informazioni su questo argomento, è possibile fare riferimento alle  <a href="https://docs.microsoft.com//windows/mixed-reality/develop/unity/tutorials/unity-spatial-audio-ch1" target="_blank"> esercitazioni audio spaziali</a>.</span><span class="sxs-lookup"><span data-stu-id="13287-198">To learn more about this topic, you can refer to the  <a href="https://docs.microsoft.com//windows/mixed-reality/develop/unity/tutorials/unity-spatial-audio-ch1" target="_blank"> Spatial audio tutorials</a>.</span></span>

<span data-ttu-id="13287-199">Nella finestra Project Settings (Impostazioni progetto) seleziona **Player (Lettore)**  > **XR Settings** (Impostazioni XR) e quindi usa l'elenco a discesa **Depth Format** (Formato profondità) per selezionare **16-bit depth** (Profondità a 16 bit):</span><span class="sxs-lookup"><span data-stu-id="13287-199">In the Project Settings window, select **Player** > **XR Settings**, then use the **Depth Format** dropdown to select **16-bit depth**:</span></span>

![Unity Abilita 16 profondità](images/mr-learning-base/base-02-section5-step2-6.png)

> [!TIP]
> <span data-ttu-id="13287-201">La riduzione del formato di profondità a 16 bit è facoltativa, ma consente di migliorare le prestazioni grafiche nel progetto.</span><span class="sxs-lookup"><span data-stu-id="13287-201">Reducing the Depth Format to 16-bit is optional but my help improve graphics performance in your project.</span></span> <span data-ttu-id="13287-202">Per ulteriori informazioni su questo argomento, è possibile fare riferimento alla sezione   <a href="https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/performance/perf-getting-started.md#single-pass-instanced-rendering#depth-buffer-sharing-hololens" target="_blank">  HoloLens (depth buffer sharing) </a> della documentazione  <a href="https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/performance/perf-getting-started.md#single-pass-instanced-rendering" target="_blank"> sulle prestazioni </a> di MRTK.</span><span class="sxs-lookup"><span data-stu-id="13287-202">To learn more about this topic, you can refer to the   <a href="https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/performance/perf-getting-started.md#single-pass-instanced-rendering#depth-buffer-sharing-hololens" target="_blank">  Depth buffer sharing (HoloLens) </a> section of MRTK's  <a href="https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/performance/perf-getting-started.md#single-pass-instanced-rendering" target="_blank"> Performance </a> documentation.</span></span>

<span data-ttu-id="13287-203">Nella finestra Project Settings (Impostazioni progetto) seleziona **Player (Lettore)**  > **Publishing Settings** (Impostazioni di pubblicazione) e quindi nel campo **Package name** (Nome del pacchetto) immetti un nome appropriato, ad esempio _MRTKTutorials-GettingStarted_:</span><span class="sxs-lookup"><span data-stu-id="13287-203">In the Project Settings window, select **Player** > **Publishing Settings**, then in the **Package name** field, enter a suitable name, for example, _MRTKTutorials-GettingStarted_:</span></span>

![Finestra Project Settings di Unity con il nome del pacchetto configurato](images/mr-learning-base/base-02-section5-step2-7.png)

> [!NOTE]
> <span data-ttu-id="13287-205">Il valore di 'Package name' (Nome del pacchetto) è l'identificatore univoco dell'app.</span><span class="sxs-lookup"><span data-stu-id="13287-205">The 'Package name' is the unique identifier for the app.</span></span> <span data-ttu-id="13287-206">Modifica questo identificatore prima di distribuire l'app per evitare di sovrascrivere app installate in precedenza.</span><span class="sxs-lookup"><span data-stu-id="13287-206">You should change this identifier before deploying the app to avoid overwriting previously installed apps.</span></span>

> [!TIP]
> <span data-ttu-id="13287-207">Il valore di 'Product Name' (Nome del prodotto) è il nome visualizzato nel menu di avvio di HoloLens.</span><span class="sxs-lookup"><span data-stu-id="13287-207">The 'Product Name' is the name displayed in the HoloLens Start menu.</span></span> <span data-ttu-id="13287-208">Per semplificare l'individuazione dell'app durante lo sviluppo, anteponi un carattere di sottolineatura al nome in modo che compaia all'inizio dell'elenco.</span><span class="sxs-lookup"><span data-stu-id="13287-208">To make the app easier to locate during development, add an underscore in front of the name to sort it to the top.</span></span>

## <a name="creating-and-configuring-the-scene"></a><span data-ttu-id="13287-209">Creazione e configurazione della scena</span><span class="sxs-lookup"><span data-stu-id="13287-209">Creating and configuring the scene</span></span>

<span data-ttu-id="13287-210">Scegli **File** > **New Scene** (Nuova scena) dal menu di Unity per creare una nuova scena:</span><span class="sxs-lookup"><span data-stu-id="13287-210">In the Unity menu, select **File** > **New Scene** to create a new scene:</span></span>

![Percorso del menu New Scene di Unity](images/mr-learning-base/base-02-section6-step1-1.png)

<span data-ttu-id="13287-212">Scegli **Mixed Reality Toolkit** > **Add to Scene and Configure...** (Aggiungi alla scena e configura) dal menu di Unity per aggiungere MRTK alla scena corrente:</span><span class="sxs-lookup"><span data-stu-id="13287-212">In the Unity menu, select **Mixed Reality Toolkit** > **Add to Scene and Configure...** to add the MRTK to your current scene:</span></span>

![Percorso del menu Add to Scene and Configure... di Unity](images/mr-learning-base/base-02-section6-step1-2.png)

<span data-ttu-id="13287-214">Con l'oggetto **MixedRealityToolkit** selezionato nella finestra Hierarchy (Gerarchia), nella finestra Inspector (Controllo) verifica che il profilo di configurazione di **Mixed Reality Toolkit** sia impostato su **DefaultMixedRealityToolkitConfigurationProfile**:</span><span class="sxs-lookup"><span data-stu-id="13287-214">With the **MixedRealityToolkit** object still selected in the Hierarchy window, in the Inspector window, verify that the **MixedRealityToolkit** configuration profile is set to **DefaultMixedRealityToolkitConfigurationProfile**:</span></span>

![Componente MixedRealityToolkit di Unity con DefaultMixedRealityTookitConfigurationProfile selezionato](images/mr-learning-base/base-02-section6-step1-3.png)

<span data-ttu-id="13287-216">Dal menu di Unity scegli **File** > **Save As** (Salva con nome) per visualizzare la finestra Save Scene (Salva la scena):</span><span class="sxs-lookup"><span data-stu-id="13287-216">In the Unity menu, select **File** > **Save As...** to open the Save Scene window:</span></span>

![Percorso del menu Save As... di Unity](images/mr-learning-base/base-02-section6-step1-4.png)

<span data-ttu-id="13287-218">Nella finestra Save Scene (Salva la scena) passa alla cartella **Scenes** (Scene) del progetto, assegna alla scena un nome appropriato, ad esempio _GettingStarted_, e fai clic sul pulsante **Save** (Salva) per salvare la scena:</span><span class="sxs-lookup"><span data-stu-id="13287-218">In the Save Scene window, navigate to your project's **Scenes** folder, give your scene a suitable name, for example, _GettingStarted_, and click the **Save** button to save the scene:</span></span>

![Finestra Save Scene di Unity con il prompt di salvataggio](images/mr-learning-base/base-02-section6-step1-5.png)

## <a name="building-your-application-to-your-hololens-2"></a><span data-ttu-id="13287-220">Compilazione dell'applicazione nel dispositivo HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="13287-220">Building your application to your HoloLens 2</span></span>

### <a name="1-build-the-unity-project"></a><span data-ttu-id="13287-221">1. Compilare il progetto Unity</span><span class="sxs-lookup"><span data-stu-id="13287-221">1. Build the Unity project</span></span>

<span data-ttu-id="13287-222">Dal menu di Unity scegli **File** > **Build Settings** (Impostazioni di compilazione) per visualizzare la finestra corrispondente.</span><span class="sxs-lookup"><span data-stu-id="13287-222">In the Unity menu, select **File** > **Build Settings...** to open the Build Settings window.</span></span>

<span data-ttu-id="13287-223">Nella finestra Build Settings (Impostazioni di compilazione), fai clic sul pulsante **Add Open Scenes** (Aggiungi scene aperte) per aggiungere la scena corrente all'elenco **Scenes In Build** (Scene in compilazione) e quindi fai clic sul pulsante **Build** (Compila) per visualizzare la finestra Build Universal Windows Platform (Compilazione UWP):</span><span class="sxs-lookup"><span data-stu-id="13287-223">In the Build Settings window, click the **Add Open Scenes** button to add your current scene to the **Scenes In Build** list, then click the **Build** button to open the Build Universal Windows Platform window:</span></span>

![Finestra Build Settings di Unity con la piattaforma UWP selezionata](images/mr-learning-base/base-02-section7-step1-1.png)

<span data-ttu-id="13287-225">Nella finestra Build Universal Windows Platform (Compilazione UWP), scegli un percorso appropriato in cui archiviare la compilazione, ad esempio _D:\MixedRealityLearning\Builds_, crea una nuova cartella e assegnale un nome adatto (ad esempio, _GettingStarted_) e quindi fai clic sul pulsante **Select Folder** (Seleziona cartella) per avviare il processo di compilazione:</span><span class="sxs-lookup"><span data-stu-id="13287-225">In the Build Universal Windows Platform window, choose a suitable location to store your build, for example, _D:\MixedRealityLearning\Builds_, create a new folder and give it a suitable name, for example, _GettingStarted_, and then click the **Select Folder** button to start the build process:</span></span>

![Finestra Build Settings di Unity con la finestra del prompt di selezione della cartella](images/mr-learning-base/base-02-section7-step1-2.png)

<span data-ttu-id="13287-227">Attendi che Unity completi il processo di compilazione:</span><span class="sxs-lookup"><span data-stu-id="13287-227">Wait for Unity to finish the build process:</span></span>

![Processo di compilazione di Unity in corso](images/mr-learning-base/base-02-section7-step1-3.png)

### <a name="2-build-and-deploy-the-application"></a><span data-ttu-id="13287-229">2. Compilare e distribuire l'applicazione</span><span class="sxs-lookup"><span data-stu-id="13287-229">2. Build and deploy the application</span></span>

<span data-ttu-id="13287-230">Al termine del processo di compilazione, Unity richiederà a Esplora file di Windows di aprire il percorso in cui è stata archiviata la compilazione.</span><span class="sxs-lookup"><span data-stu-id="13287-230">When the build process has completed, Unity will prompt Windows File Explorer to open the location you stored the build.</span></span> <span data-ttu-id="13287-231">Spostati all'interno della cartella e fai doppio clic sul file della soluzione per aprirlo in Visual Studio:</span><span class="sxs-lookup"><span data-stu-id="13287-231">Navigate inside the folder, and double-click the solution file to open it in Visual Studio:</span></span>

![Esplora risorse con la soluzione di Visual Studio appena creata selezionata](images/mr-learning-base/base-02-section8-step1-1.png)

> [!NOTE]
> <span data-ttu-id="13287-233">Se Visual Studio chiede di installare nuovi componenti, dedica qualche minuto a verificare di disporre di tutti i componenti indispensabili come specificato nella documentazione **[Installare gli strumenti](../../install-the-tools.md)** .</span><span class="sxs-lookup"><span data-stu-id="13287-233">If Visual Studio asks you to install new components, take a moment to check that you have all the prerequisite components in the **[Install the Tools](../../install-the-tools.md)** documentation.</span></span>

<span data-ttu-id="13287-234">Configura Visual Studio per HoloLens selezionando la configurazione **Master** o **Release**, l'architettura **ARM64** e **Dispositivo** come destinazione:</span><span class="sxs-lookup"><span data-stu-id="13287-234">Configure Visual Studio for HoloLens by selecting the **Master** or **Release** configuration, the **ARM64** architecture, and **Device** as target:</span></span>

> [!NOTE]
> <span data-ttu-id="13287-235">Scegliere la destinazione a seconda del metodo di distribuzione.</span><span class="sxs-lookup"><span data-stu-id="13287-235">Choose your target depending on your deployment method.</span></span>

![Visual Studio configurato per la distribuzione in HoloLens 2](images/mr-learning-base/base-02-section8-step1-2.png)

> [!TIP]
> <span data-ttu-id="13287-237">Se esegui la distribuzione in HoloLens (1a generazione), seleziona l'architettura **x86**.</span><span class="sxs-lookup"><span data-stu-id="13287-237">If you're deploying to HoloLens (1st generation), select the **x86** architecture.</span></span>

> [!NOTE]
> <span data-ttu-id="13287-238">Per HoloLens, in genere la compilazione viene eseguita per l'architettura ARM.</span><span class="sxs-lookup"><span data-stu-id="13287-238">For HoloLens, you will typically build for the ARM architecture.</span></span> <span data-ttu-id="13287-239">Esiste tuttavia un <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank"><strong>problema noto</strong></a> in Unity 2019.3 che causa errori quando viene selezionata l'architettura di compilazione ARM in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="13287-239">However, there is a  <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank"><strong>known issue</strong></a> in Unity 2019.3 that causes errors when selecting ARM as the build architecture in Visual Studio.</span></span> <span data-ttu-id="13287-240">La soluzione consigliata consiste nel compilare per ARM64.</span><span class="sxs-lookup"><span data-stu-id="13287-240">The recommended workaround is to build for ARM64.</span></span> <span data-ttu-id="13287-241">Se questa opzione non è applicabile, passa a **Modifica > Impostazioni progetto > Player (Lettore) > Altre impostazioni** e disabilita **Graphics Jobs** (Processi grafici).</span><span class="sxs-lookup"><span data-stu-id="13287-241">If that is not an option, go to **Edit > Project Settings > Player > Other Settings** and disable **Graphics Jobs**.</span></span>

> [!NOTE]
> <span data-ttu-id="13287-242">Se non viene visualizzata l'opzione Dispositivo come destinazione, potresti dover modificare il progetto di avvio per la soluzione di Visual Studio passando dal progetto IL2CPP al progetto UWP.</span><span class="sxs-lookup"><span data-stu-id="13287-242">If you don't see Device as a target option, you may need to change the startup project for the Visual Studio solution from the IL2CPP project to the UWP project.</span></span> <span data-ttu-id="13287-243">A tale scopo, in Esplora soluzioni fai clic con il pulsante destro del mouse su NomeProgetto (Windows universale) e scegli **Imposta come progetto di avvio**.</span><span class="sxs-lookup"><span data-stu-id="13287-243">To do this, in the Solution Explorer, right-click on YourProjectName (Universal Windows) and select **Set as StartUp Project**.</span></span>

<span data-ttu-id="13287-244">Connettere il HoloLens al computer usando un cavo USB-C, quindi selezionare **debug**  >  **Avvia senza eseguire debug** per compilare e distribuire nel dispositivo:</span><span class="sxs-lookup"><span data-stu-id="13287-244">Connect your HoloLens to your computer using a USB-C cable, then select **Debug** > **Start Without Debugging** to build and deploy to your device:</span></span>

![Percorso del menu di avvio di Visual Studio senza debug](images/mr-learning-base/base-02-section8-step1-3.png)

> [!IMPORTANT]
> <span data-ttu-id="13287-246">Prima della compilazione nel dispositivo, quest'ultimo deve essere in modalità sviluppatore e associato al computer di sviluppo.</span><span class="sxs-lookup"><span data-stu-id="13287-246">Before building to your device, the device must be in Developer Mode and paired with your development computer.</span></span> <span data-ttu-id="13287-247">Per completare i due passaggi segui [queste istruzioni](../../platform-capabilities-and-apis/using-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="13287-247">Both of these steps can be completed by following [these instructions](../../platform-capabilities-and-apis/using-visual-studio.md).</span></span>

> [!TIP]
> <span data-ttu-id="13287-248">Puoi anche eseguire la distribuzione nell'[emulatore HoloLens](../../platform-capabilities-and-apis/using-the-hololens-emulator.md) o creare un [Pacchetto applicazione](https://docs.microsoft.com/windows/uwp/packaging/packaging-uwp-apps) per il sideload.</span><span class="sxs-lookup"><span data-stu-id="13287-248">You can also deploy to the [HoloLens Emulator](../../platform-capabilities-and-apis/using-the-hololens-emulator.md) or create an [App Package](https://docs.microsoft.com/windows/uwp/packaging/packaging-uwp-apps) for sideloading.</span></span>

<span data-ttu-id="13287-249">Usando Avvia senza eseguire il debug, l'app viene avviata nel dispositivo senza collegare il debugger di Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="13287-249">Using Start Without Debugging automatically starts the app on your device without the Visual Studio debugger attached.</span></span>

<span data-ttu-id="13287-250">Seleziona **Compila > Distribuisci soluzione** per eseguire la distribuzione nel dispositivo senza che l'app venga avviata automaticamente.</span><span class="sxs-lookup"><span data-stu-id="13287-250">Select **Build > Deploy Solution** to deploy to your device without having the app start automatically.</span></span>

> [!NOTE]
><span data-ttu-id="13287-251">Potrebbe essere visibile nell'app il profiler di diagnostica, che può essere attivato o disattivato tramite il comando vocale **Toggle Diagnostics** (Attiva/Disattiva diagnostica).</span><span class="sxs-lookup"><span data-stu-id="13287-251">You may notice the Diagnostics profiler in the app, which you can toggle on or off by using the speech command **Toggle Diagnostics**.</span></span> <span data-ttu-id="13287-252">È consigliabile mantenere visibile il profiler la maggior parte del tempo durante lo sviluppo per verificare quando le modifiche apportate all'app possono produrre effetti negativi sulle prestazioni.</span><span class="sxs-lookup"><span data-stu-id="13287-252">It's recommended that you keep the profiler visible most of the time during development to understand when changes to the app may impact performance.</span></span> <span data-ttu-id="13287-253">Le app HoloLens ad esempio devono [essere eseguite costantemente a 60 FPS](../../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md).</span><span class="sxs-lookup"><span data-stu-id="13287-253">For example, HoloLens apps should [continuously run at 60 FPS](../../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md).</span></span>

## <a name="congratulations"></a><span data-ttu-id="13287-254">Lezione completata</span><span class="sxs-lookup"><span data-stu-id="13287-254">Congratulations</span></span>

<span data-ttu-id="13287-255">A questo punto hai distribuito la tua prima app per HoloLens.</span><span class="sxs-lookup"><span data-stu-id="13287-255">You've now deployed your first HoloLens app.</span></span> <span data-ttu-id="13287-256">Esplorando, noterai una mesh di mapping spaziale che copre le superfici percepite da HoloLens.</span><span class="sxs-lookup"><span data-stu-id="13287-256">As you walk around, you should see a spatial mapping mesh covering the surfaces that are perceived by the HoloLens.</span></span> <span data-ttu-id="13287-257">Dovresti anche vedere indicatori sulle mani e sulle dita per il tracciamento delle mani e un contatore della frequenza dei fotogrammi per tenere sotto controllo le prestazioni dell'app.</span><span class="sxs-lookup"><span data-stu-id="13287-257">Additionally, you should see indicators on your hands and fingers for hand tracking and a frame rate counter for keeping an eye on app performance.</span></span> <span data-ttu-id="13287-258">Queste funzionalità sono solo alcune delle parti fondamentali incluse in MRTK.</span><span class="sxs-lookup"><span data-stu-id="13287-258">These features are just a few foundational pieces included with MRTK.</span></span> <span data-ttu-id="13287-259">Nelle esercitazioni successive aggiungerai contenuto alla scena per esplorare le funzionalità di HoloLens e MRTK.</span><span class="sxs-lookup"><span data-stu-id="13287-259">In the upcoming tutorials, you'll add content to your scene to explore the capabilities of HoloLens and the MRTK.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="13287-260">Esercitazione successiva: 3. Configurazione dei profili di MRTK</span><span class="sxs-lookup"><span data-stu-id="13287-260">Next Tutorial: 3. Configuring the MRTK profiles</span></span>](mr-learning-base-03.md)

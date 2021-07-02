---
title: Inizializzazione del progetto e distribuzione della prima applicazione
description: In questo corso viene illustrato come configurare il progetto Unity per Mixed Reality Toolkit (MRTK) e come distribuirlo in HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens, MRTK, mixed reality toolkit, UWP, TextMeshPro,
ms.localizationpriority: high
ms.openlocfilehash: 7124650a59271b48b763719063411765b5457768
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2021
ms.locfileid: "113175810"
---
# <a name="2-initializing-your-project-and-deploying-your-first-application"></a><span data-ttu-id="77adf-104">2. Inizializzazione del progetto e distribuzione della prima applicazione</span><span class="sxs-lookup"><span data-stu-id="77adf-104">2. Initializing your project and deploying your first application</span></span>

<span data-ttu-id="77adf-105">In questa esercitazione apprenderai come creare un nuovo progetto Unity, come configurarlo per lo sviluppo Mixed Reality Toolkit (MRTK) e come importare MRTK.</span><span class="sxs-lookup"><span data-stu-id="77adf-105">In this tutorial, you'll learn how to create a new Unity project, configure it for Mixed Reality Toolkit (MRTK) development, and import MRTK.</span></span> <span data-ttu-id="77adf-106">Verranno inoltre esaminati i processi di configurazione, compilazione e distribuzione di una scena Unity di base da Visual Studio a HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="77adf-106">You'll also walk through configuring, building, and deploying a basic Unity scene from Visual Studio to your HoloLens 2.</span></span> <span data-ttu-id="77adf-107">Dopo la distribuzione in HoloLens 2, dovrebbe essere visualizzata una mesh di mapping spaziale che copre le superfici percepite da HoloLens.</span><span class="sxs-lookup"><span data-stu-id="77adf-107">Once you have deployed it to your HoloLens 2, you should see a spatial mapping mesh covering the surfaces that are perceived by the HoloLens.</span></span> <span data-ttu-id="77adf-108">Dovresti anche vedere indicatori sulle mani e sulle dita per il tracciamento delle mani e un contatore della frequenza dei fotogrammi per tenere sotto controllo le prestazioni dell'app.</span><span class="sxs-lookup"><span data-stu-id="77adf-108">Additionally, you should see indicators on your hands and fingers for hand tracking and a frame rate counter for keeping an eye on app performance.</span></span>

## <a name="objectives"></a><span data-ttu-id="77adf-109">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="77adf-109">Objectives</span></span>

* <span data-ttu-id="77adf-110">Apprendere come configurare Unity per lo sviluppo per HoloLens</span><span class="sxs-lookup"><span data-stu-id="77adf-110">Learn how to configure Unity for HoloLens development</span></span>
* <span data-ttu-id="77adf-111">Apprendere come compilare e distribuire l'app in HoloLens</span><span class="sxs-lookup"><span data-stu-id="77adf-111">Learn how to build and deploy your app to HoloLens</span></span>
* <span data-ttu-id="77adf-112">Sperimentare la mesh di mapping spaziale, le mesh manuali e il contatore della frequenza dei fotogrammi sul dispositivo HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="77adf-112">Experience the spatial mapping mesh, hand meshes, and the framerate counter on HoloLens 2 device</span></span>

### <a name="steps-overview"></a><span data-ttu-id="77adf-113">Panoramica dei passaggi</span><span class="sxs-lookup"><span data-stu-id="77adf-113">Steps overview</span></span>
:::row:::
    :::column:::
       <span data-ttu-id="77adf-114">![Panoramica Passaggio 1 ](images/mr-learning-base/base-02-overview-step1.png) **1. Creare un nuovo progetto Unity**</span><span class="sxs-lookup"><span data-stu-id="77adf-114">![Overview Step 1](images/mr-learning-base/base-02-overview-step1.png) **1. Create a new Unity project**</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="77adf-115">![Panoramica Passaggio 2 ](images/mr-learning-base/base-02-overview-step2.png) **2. Importare MRTK nel progetto**</span><span class="sxs-lookup"><span data-stu-id="77adf-115">![Overview Step 2](images/mr-learning-base/base-02-overview-step2.png) **2. Import MRTK into the project**</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="77adf-116">![Panoramica Passaggio 3 ](images/mr-learning-base/base-02-overview-step3.png) **3. Configurare una nuova scena con MRTK**</span><span class="sxs-lookup"><span data-stu-id="77adf-116">![Overview Step 3](images/mr-learning-base/base-02-overview-step3.png) **3. Configure a new scene with MRTK**</span></span>
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::
       <span data-ttu-id="77adf-117">![Panoramica Passaggio 4 ](images/mr-learning-base/base-02-overview-step4.png) **4. Compilare Unity Project**</span><span class="sxs-lookup"><span data-stu-id="77adf-117">![Overview Step 4](images/mr-learning-base/base-02-overview-step4.png) **4. Build Unity Project**</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="77adf-118">![Panoramica Passaggio 5 ](images/mr-learning-base/base-02-overview-step5.png) **5. Compilare la Project UWP**</span><span class="sxs-lookup"><span data-stu-id="77adf-118">![Overview Step 5](images/mr-learning-base/base-02-overview-step5.png) **5. Build UWP Project**</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="77adf-119">![Panoramica Passaggio 6 ](images/mr-learning-base/base-02-overview-step6.png) **6. Eseguire Project nel dispositivo**</span><span class="sxs-lookup"><span data-stu-id="77adf-119">![Overview Step 6](images/mr-learning-base/base-02-overview-step6.png) **6. Run Project on the Device**</span></span>
    :::column-end:::
:::row-end:::

## <a name="creating-the-unity-project"></a><span data-ttu-id="77adf-120">Creazione del progetto Unity</span><span class="sxs-lookup"><span data-stu-id="77adf-120">Creating the Unity project</span></span>

<span data-ttu-id="77adf-121">Avvia **Unity Hub**, seleziona la scheda **Projects** (Progetti) e fai clic sulla **freccia giù** accanto al pulsante **New** (Nuovo):</span><span class="sxs-lookup"><span data-stu-id="77adf-121">Launch **Unity Hub**, select the **Projects** tab, and click the **down arrow** next to the **New** button:</span></span>

<img src="images/mr-learning-base/base-02-section1-step1-1.png" width="650px" alt="Unity Hub with New button highlighted">

<span data-ttu-id="77adf-122">Nell'elenco a discesa seleziona la **versione** di Unity specificata nella sezione [Prerequisiti](mr-learning-base-01.md#prerequisites):</span><span class="sxs-lookup"><span data-stu-id="77adf-122">In the dropdown, select the Unity **version** specified in the [Prerequisites](mr-learning-base-01.md#prerequisites):</span></span>

<img src="images/mr-learning-base/base-02-section1-step1-2.png" width="650px" alt="Unity Hub with NEW version selector dropdown">


> [!TIP]
> <span data-ttu-id="77adf-123">Se la versione specifica di Unity non è disponibile in Unity Hub, puoi avviare l'installazione da <a href="https://unity3d.com/get-unity/download/archive" target="_blank">Download Archive</a> (Archivio download) di Unity.</span><span class="sxs-lookup"><span data-stu-id="77adf-123">If the particular Unity version is not available in Unity Hub, you can initiate the installation from Unity's <a href="https://unity3d.com/get-unity/download/archive" target="_blank">Download Archive</a>.</span></span>

<span data-ttu-id="77adf-124">Nella finestra Create a new project (Crea un nuovo progetto):</span><span class="sxs-lookup"><span data-stu-id="77adf-124">In the Create a new project window:</span></span>

* <span data-ttu-id="77adf-125">Assicurati che in **Templates** (Modelli) sia impostata l'opzione **3D**</span><span class="sxs-lookup"><span data-stu-id="77adf-125">Ensure **Templates** is set to **3D**</span></span>
* <span data-ttu-id="77adf-126">Immetti un nome appropriato nel campo **Project Name** (Nome progetto), ad esempio _MRTK Tutorials_</span><span class="sxs-lookup"><span data-stu-id="77adf-126">Enter a suitable **Project Name**, for example, _MRTK Tutorials_</span></span>
* <span data-ttu-id="77adf-127">Nel campo **Location** (Percorso) scegli un percorso appropriato in cui archiviare il progetto, ad esempio _D:\MixedRealityLearning_</span><span class="sxs-lookup"><span data-stu-id="77adf-127">Choose a suitable **Location** to store your project, for example, _D:\MixedRealityLearning_</span></span>
* <span data-ttu-id="77adf-128">Fai clic sul pulsante **Create** (Crea) per creare e avviare il nuovo progetto Unity</span><span class="sxs-lookup"><span data-stu-id="77adf-128">Click the **Create** button to create and launch your new Unity project</span></span>

<img src="images/mr-learning-base/base-02-section1-step1-3.png" width="650px" alt="Unity Hub with Create a new project window filled out">

> [!CAUTION]
> <span data-ttu-id="77adf-129">Se lavori in Windows, tieni presente che è previsto un limite (MAX_PATH) di 255 caratteri per il percorso.</span><span class="sxs-lookup"><span data-stu-id="77adf-129">When working on Windows, there is a MAX_PATH limit of 255 characters.</span></span> <span data-ttu-id="77adf-130">Dovresti pertanto salvare il progetto Unity in prossimità della radice dell'unità.</span><span class="sxs-lookup"><span data-stu-id="77adf-130">Consequently, you should save the Unity project close to the root of the drive.</span></span>

<span data-ttu-id="77adf-131">Attendi che Unity crei il progetto:</span><span class="sxs-lookup"><span data-stu-id="77adf-131">Wait for Unity to create the project:</span></span>

<img src="images/mr-learning-base/base-02-section1-step1-4.png" width="650px" alt="Unity create new project in progress">

## <a name="switching-the-build-platform"></a><span data-ttu-id="77adf-132">Passaggio a un'altra piattaforma di compilazione</span><span class="sxs-lookup"><span data-stu-id="77adf-132">Switching the build platform</span></span>

<span data-ttu-id="77adf-133">Dal menu di Unity scegli **File** > **Build Settings** (Impostazioni di compilazione) per visualizzare la finestra corrispondente:</span><span class="sxs-lookup"><span data-stu-id="77adf-133">In the Unity menu, select **File** > **Build Settings...** to open the Build Settings window:</span></span>

![Percorso del menu Build Settings... di Unity](images/mr-learning-base/base-02-section2-step1-1.png)

<span data-ttu-id="77adf-135">Nella finestra Build Impostazioni selezionare **Universal Windows Platform** e:</span><span class="sxs-lookup"><span data-stu-id="77adf-135">In the Build Settings window, select **Universal Windows Platform** and:</span></span>

1. <span data-ttu-id="77adf-136">Impostare **Dispositivo di destinazione** su **HoloLens**</span><span class="sxs-lookup"><span data-stu-id="77adf-136">Set **Target device** to **HoloLens**</span></span>
2. <span data-ttu-id="77adf-137">Impostare **Architettura** su **ARM 64**</span><span class="sxs-lookup"><span data-stu-id="77adf-137">Set **Architecture** to **ARM 64**</span></span> 
3. <span data-ttu-id="77adf-138">Impostare **Build Type** (Tipo di compilazione) su **D3D Project**</span><span class="sxs-lookup"><span data-stu-id="77adf-138">Set **Build Type** to **D3D Project**</span></span>
4. <span data-ttu-id="77adf-139">Impostare **Versione SDK di destinazione** su Versione più recente **installata**</span><span class="sxs-lookup"><span data-stu-id="77adf-139">Set **Target SDK Version** to **Latest Installed**</span></span>
5. <span data-ttu-id="77adf-140">Impostare **Versione minima della piattaforma** su **10.0.1024.0**</span><span class="sxs-lookup"><span data-stu-id="77adf-140">Set **Minimum Platform Version** to **10.0.1024.0**</span></span>
6. <span data-ttu-id="77adf-141">Impostare **Visual Studio versione più recente** **installata**</span><span class="sxs-lookup"><span data-stu-id="77adf-141">Set **Visual Studio Version** to **Latest installed**</span></span>
7. <span data-ttu-id="77adf-142">Impostare **Compila ed Esegui su** dispositivo **USB**</span><span class="sxs-lookup"><span data-stu-id="77adf-142">Set **Build and Run on** to **USB Device**</span></span>
8. <span data-ttu-id="77adf-143">Impostare **Configurazione build** su **Versione** perché si sono noti problemi di prestazioni con debug</span><span class="sxs-lookup"><span data-stu-id="77adf-143">Set **Build configuration** to **Release** because there are known performance issues with Debug</span></span>
9. <span data-ttu-id="77adf-144">Fare clic sul pulsante Cambia piattaforma</span><span class="sxs-lookup"><span data-stu-id="77adf-144">Click the Switch Platform button</span></span>

![Unity Build Impostazioni con le impostazioni della piattaforma Windows universali impostate](images/mr-learning-base/base-02-section2-step1-2-openxr.png)

<span data-ttu-id="77adf-146">Attendi che Unity completi il passaggio all'altra piattaforma:</span><span class="sxs-lookup"><span data-stu-id="77adf-146">Wait for Unity to finish switching the platform:</span></span>

![Passaggio di Unity all'altra piattaforma in corso](images/mr-learning-base/base-02-section2-step1-3-openxr.png)

<span data-ttu-id="77adf-148">Al termine del passaggio della piattaforma da parte di Unity, fare clic sull'icona **x** per chiudere la Impostazioni compilazione.</span><span class="sxs-lookup"><span data-stu-id="77adf-148">When Unity has finished switching the platform, click the  **x** icon to close the Build Settings window.</span></span>

## <a name="importing-the-mixed-reality-toolkit-and-configuring-the-unity-project"></a><span data-ttu-id="77adf-149">Importazione del progetto Toolkit realtà mista e configurazione del progetto Unity</span><span class="sxs-lookup"><span data-stu-id="77adf-149">Importing the Mixed Reality Toolkit and Configuring the Unity project</span></span>

<span data-ttu-id="77adf-150">Per importare Toolkit realtà mista nel Project Unity Project è necessario usare lo strumento [funzionalità](../welcome-to-mr-feature-tool.md) realtà mista che consente agli sviluppatori di individuare, aggiornare e aggiungere pacchetti di funzionalità di realtà mista nei progetti Unity.</span><span class="sxs-lookup"><span data-stu-id="77adf-150">To Import Mixed Reality Toolkit into the Unity Project you will have to use [Mixed Reality Feature Tool](../welcome-to-mr-feature-tool.md) which allows  developers to discover, update, and add Mixed Reality feature packages into Unity projects.</span></span> <span data-ttu-id="77adf-151">È possibile cercare i pacchetti in base al nome o alla categoria, visualizzarne le dipendenze e persino visualizzare le modifiche proposte al file manifesto del progetto prima dell'importazione.</span><span class="sxs-lookup"><span data-stu-id="77adf-151">You can search packages by name or category, see their dependencies, and even view proposed changes to your projects manifest file before importing.</span></span>

<span data-ttu-id="77adf-152">Scaricare la versione più recente di Mixed Reality Feature Tool dall'Area download [Microsoft](https://aka.ms/MRFeatureTool). Al termine del download, decomprimere il file e salvarlo sul desktop.</span><span class="sxs-lookup"><span data-stu-id="77adf-152">Download the latest version of the Mixed Reality Feature Tool from the [Microsoft Download Center](https://aka.ms/MRFeatureTool), When the download is complete, unzip the file and save it to your desktop.</span></span>

> [!NOTE]
> <span data-ttu-id="77adf-153">Prima di poter eseguire lo strumento di funzionalità di realtà mista, installare [il runtime di .NET 5.0](https://dotnet.microsoft.com/download/dotnet/thank-you/runtime-desktop-5.0.7-windows-x64-installer)</span><span class="sxs-lookup"><span data-stu-id="77adf-153">Before you can run the Mixed Reality Feature Tool please install [.NET 5.0 runtime](https://dotnet.microsoft.com/download/dotnet/thank-you/runtime-desktop-5.0.7-windows-x64-installer)</span></span>

<span data-ttu-id="77adf-154">Aprire il file eseguibile **MixedRealityFeatureTool** dalla cartella scaricata per avviare Mixed Reality Feature Tool.</span><span class="sxs-lookup"><span data-stu-id="77adf-154">Open the executable file **MixedRealityFeatureTool** from the downloaded folder to launch the Mixed Reality Feature Tool.</span></span>  


<img src="images/mr-learning-base/base-02-section4-step1-1.png" width="750px" alt="Opening MixedRealityFeatureTool">

[!INCLUDE[](includes/importing-mrtk.md)]

## <a name="creating-the-scene-and-configuring-mrtk"></a><span data-ttu-id="77adf-155">Creazione della scena e configurazione di MRTK</span><span class="sxs-lookup"><span data-stu-id="77adf-155">Creating the scene and configuring MRTK</span></span>

<span data-ttu-id="77adf-156">Nel menu Unity selezionare **File**  >  **Nuova scena**:</span><span class="sxs-lookup"><span data-stu-id="77adf-156">In the Unity menu, select **File** > **New Scene**:</span></span>

![Percorso del menu New Scene di Unity](images/mr-learning-base/base-02-section6-step1-1.png)

<span data-ttu-id="77adf-158">Nella finestra **Nuova scena** selezionare **Basic (incorporato)** e fare clic su **Crea** per creare una nuova scena:</span><span class="sxs-lookup"><span data-stu-id="77adf-158">In the **New Scene** window select **Basic (Built-in)** and click on **create** to create a new scene:</span></span>

![Finestra Nuova scena di Unity](images/mr-learning-base/base-02-section6-step1-1-newscene.png)

> [!NOTE]
> <span data-ttu-id="77adf-160">Lo screenshot precedente è della versione 2020 di Unity, se si  usa Unity 2019 quando si fa clic su Crea una nuova scena vuota.</span><span class="sxs-lookup"><span data-stu-id="77adf-160">Above screenshot is from Unity Version 2020, if you are using Unity 2019 when you click on **create** a new empty scene will be created.</span></span>

<span data-ttu-id="77adf-161">Nel menu Unity selezionare **Realtà** mista Toolkit Aggiungi alla scena e  >    >  **Configura...** per aggiungere MRTK alla scena corrente:</span><span class="sxs-lookup"><span data-stu-id="77adf-161">In the Unity menu, select **Mixed Reality** > **Toolkit** > **Add to Scene and Configure...** to add the MRTK to your current scene:</span></span>

![Percorso del menu Add to Scene and Configure... di Unity](images/mr-learning-base/base-02-section6-step1-2.png)

<span data-ttu-id="77adf-163">Con l'oggetto **MixedRealityToolkit** selezionato nella finestra Hierarchy (Gerarchia), nella finestra Inspector (Controllo) verifica che il profilo di configurazione di **Mixed Reality Toolkit** sia impostato su **DefaultMixedRealityToolkitConfigurationProfile**:</span><span class="sxs-lookup"><span data-stu-id="77adf-163">With the **MixedRealityToolkit** object still selected in the Hierarchy window, in the Inspector window, verify that the **MixedRealityToolkit** configuration profile is set to **DefaultMixedRealityToolkitConfigurationProfile**:</span></span>

![Componente MixedRealityToolkit di Unity con DefaultMixedRealityTookitConfigurationProfile selezionato](images/mr-learning-base/base-02-section6-step1-3.png)

<span data-ttu-id="77adf-165">Dal menu di Unity scegli **File** > **Save As** (Salva con nome) per visualizzare la finestra Save Scene (Salva la scena):</span><span class="sxs-lookup"><span data-stu-id="77adf-165">In the Unity menu, select **File** > **Save As...** to open the Save Scene window:</span></span>

![Percorso del menu Save As... di Unity](images/mr-learning-base/base-02-section6-step1-4.png)

<span data-ttu-id="77adf-167">Salvare la scena nel progetto in **Asset**  >  **Scenes**.</span><span class="sxs-lookup"><span data-stu-id="77adf-167">Save the scene in you project under **Asset** > **Scenes**.</span></span>

![Finestra Save Scene di Unity con il prompt di salvataggio](images/mr-learning-base/base-02-section6-step1-5.png)

## <a name="adding-hand-interaction-to-an-object"></a><span data-ttu-id="77adf-169">Aggiunta dell'interazione manuale a un oggetto</span><span class="sxs-lookup"><span data-stu-id="77adf-169">Adding hand interaction to an object</span></span>

<span data-ttu-id="77adf-170">Nel menu Unity selezionare **GameObject**  >  **3D Object**  >  **Cube** per aggiungere un oggetto cubo alla scena.</span><span class="sxs-lookup"><span data-stu-id="77adf-170">In the Unity menu, select **GameObject** > **3D Object** > **Cube** to add a cube object to the scene.</span></span>

![Aggiunta di un cubo alla scena](images/mr-learning-base/base-02-section8-step1-1.png)

<span data-ttu-id="77adf-172">Fare clic **sull'oggetto** Cube nella finestra Hierarchy (Gerarchia), quindi nella finestra Inspector (Controllo) configurare **il componente Transform (Trasforma)** come indicato di seguito</span><span class="sxs-lookup"><span data-stu-id="77adf-172">Click the **Cube** object in the Hierarchy window, then in the Inspector window configure its **Transform** component as follows</span></span>

* <span data-ttu-id="77adf-173">**Posizione:** X = 0, Y = -0,1, Z = 0,5</span><span class="sxs-lookup"><span data-stu-id="77adf-173">**Position**: X = 0, Y = -0.1, Z = 0.5</span></span>
* <span data-ttu-id="77adf-174">**Rotation** (Rotazione): X = 0, Y = 0, Z = 0</span><span class="sxs-lookup"><span data-stu-id="77adf-174">**Rotation**: X = 0, Y = 0, Z = 0</span></span>
* <span data-ttu-id="77adf-175">**Scala:** X = 0,1, Y = 0,1, Z = 0,1</span><span class="sxs-lookup"><span data-stu-id="77adf-175">**Scale**: X = 0.1, Y = 0.1, Z = 0.1</span></span>

<span data-ttu-id="77adf-176">1 unità Unity è di 1 metro.</span><span class="sxs-lookup"><span data-stu-id="77adf-176">1 Unity unit is 1 meter.</span></span> <span data-ttu-id="77adf-177">Le dimensioni del cubo sono state aggiornate a 10x10x10 cm, posizionate a 50 cm dalla posizione del visore (0,0,0).</span><span class="sxs-lookup"><span data-stu-id="77adf-177">We have updated cube's size to 10x10x10 cm, placed at 50cm from the headset position (0,0,0).</span></span> <span data-ttu-id="77adf-178">10 cm sotto il livello dell'occhio per un'interazione comoda.</span><span class="sxs-lookup"><span data-stu-id="77adf-178">10cm below the eye level for comfortable interaction.</span></span> 

<span data-ttu-id="77adf-179">Se si usa la scala predefinita (1,1,1), il cubo sarà troppo grande.</span><span class="sxs-lookup"><span data-stu-id="77adf-179">If you use the default scale (1,1,1), the cube will be too big.</span></span> <span data-ttu-id="77adf-180">Se si usa la posizione predefinita (0,0,0), il cubo verrà posizionato nella stessa posizione del visore e non sarà possibile visualizzare il cubo fino a quando non si passa all'indietro.</span><span class="sxs-lookup"><span data-stu-id="77adf-180">If you use the default position (0,0,0), the cube will be placed at the same position as your headset and you won't be able to see it until you move backward.</span></span>

![Modifica delle informazioni di trasformazione](images/mr-learning-base/base-02-section8-step1-1b.png)

<span data-ttu-id="77adf-182">Per concentrarsi sugli oggetti nella scena, è possibile fare doppio clic **sull'oggetto Cubo** e quindi eseguire di nuovo lo zoom avanti leggermente.</span><span class="sxs-lookup"><span data-stu-id="77adf-182">To focus in on the objects in the scene, you can double-click on the **Cube** object, and then zoom slightly in again.</span></span> <span data-ttu-id="77adf-183">Oppure è possibile usare il tasto F per eseguire lo zoom e lo stato attivo sull'oggetto.</span><span class="sxs-lookup"><span data-stu-id="77adf-183">Or you can use F key to zoom and focus on the object.</span></span>

<span data-ttu-id="77adf-184">Per interagire e afferrare un oggetto con le mani tracciate, l'oggetto deve avere:</span><span class="sxs-lookup"><span data-stu-id="77adf-184">To interact and grab an object with tracked hands, the object must have:</span></span>
 * <span data-ttu-id="77adf-185">Componente collisore, ad **esempio Box Collider** (il cubo di Unity ha già un Collisore di box per impostazione predefinita)</span><span class="sxs-lookup"><span data-stu-id="77adf-185">Collider component such as **Box Collider** (Unity's cube already has a Box Collider by default)</span></span>
 * <span data-ttu-id="77adf-186">Componente **Object Manipulator (Script)** (Manipolatore oggetti - script)</span><span class="sxs-lookup"><span data-stu-id="77adf-186">**Object Manipulator (Script)** component</span></span>
 * <span data-ttu-id="77adf-187">**Componente NearInteractionGrabbable(Script)**</span><span class="sxs-lookup"><span data-stu-id="77adf-187">**NearInteractionGrabbable(Script)** component</span></span>

<span data-ttu-id="77adf-188">Lo script **ObjectManipulator** di MRTK rende un oggetto mobile, scalabile e rotabile usando una o due mani.</span><span class="sxs-lookup"><span data-stu-id="77adf-188">MRTK's **ObjectManipulator** script makes an object movable, scalable, and rotatable using one or two hands.</span></span> <span data-ttu-id="77adf-189">Questo script supporta il modello di input di manipolazione diretta in quanto consente all'utente di toccare gli ologrammi direttamente con le proprie mani.</span><span class="sxs-lookup"><span data-stu-id="77adf-189">This script supports the direct manipulation input model as the script enables the user to touch holograms directly with their hands.</span></span>

<span data-ttu-id="77adf-190">Con il **cubo** ancora selezionato nella finestra Hierarchy (Gerarchia), nella finestra Inspector (Controllo) fare clic sul pulsante **Add Component** (Aggiungi componente), quindi cercare e selezionare **Object Manipulator** script (Manipolatore di oggetti) per aggiungere lo script Object Manipulator all'oggetto cubo.</span><span class="sxs-lookup"><span data-stu-id="77adf-190">With the **Cube** still selected in the Hierarchy window, in the Inspector window ,click on **Add Component** button, then search and select **Object Manipulator** script to add the Object Manipulator script to the cube object.</span></span>

![aggiunta dell'oggetto manupulator al cubo](images/mr-learning-base/base-02-section8-step1-2.PNG)

<span data-ttu-id="77adf-192">Ripetere la stessa operazione per aggiungere **lo script Near Interaction Grabbable** al cubo</span><span class="sxs-lookup"><span data-stu-id="77adf-192">Repeat the same to add **Near Interaction Grabbable script** to the cube</span></span>

![aggiunta di Near Interaction Grabable al cubo](images/mr-learning-base/base-02-section8-step1-3.PNG)

> [!NOTE]
> <span data-ttu-id="77adf-194">Quando si aggiunge un manipolatore di oggetti (script), in questo caso, Gestione vincoli (script) viene aggiunto automaticamente perché il manipolatore di oggetti (script) dipende da esso.</span><span class="sxs-lookup"><span data-stu-id="77adf-194">When you add a Object Manipulator (Script), in this case, the Constraint Manager (Script) is automatically added because Object Manipulator (Script) depends on it.</span></span>

## <a name="testing-your-application-in-unity-editor-with-mrtk-input-simulation"></a><span data-ttu-id="77adf-195">Test dell'applicazione nell'editor unity con simulazione di input MRTK</span><span class="sxs-lookup"><span data-stu-id="77adf-195">Testing your application in Unity editor with MRTK input simulation</span></span>

<span data-ttu-id="77adf-196">Con la simulazione di input di MRTK è possibile testare vari tipi di interazioni nell'editor di Unity senza compilare e distribuire in un dispositivo.</span><span class="sxs-lookup"><span data-stu-id="77adf-196">With MRTK's input simulation, you can test various types of interactions in the Unity editor without building and deploying to a device.</span></span> <span data-ttu-id="77adf-197">In questo modo è possibile scorrere rapidamente le idee nel processo di progettazione e sviluppo.</span><span class="sxs-lookup"><span data-stu-id="77adf-197">This allows you quickly iterate your ideas in the design and development process.</span></span> <span data-ttu-id="77adf-198">Usare combinazioni di tastiera e mouse per controllare gli input simulati.</span><span class="sxs-lookup"><span data-stu-id="77adf-198">Use keyboard and mouse combinations to control simulated inputs.</span></span>

<span data-ttu-id="77adf-199">Fare clic sul pulsante play (Riproduci) e immettere la modalità di riproduzione.</span><span class="sxs-lookup"><span data-stu-id="77adf-199">Click the play button and enter the play mode.</span></span> <span data-ttu-id="77adf-200">Tenere premuto MAIUSC  **sinistro** o BARRA SPAZIATRICE per visualizzare il controller (mani simulate), lo spostamento del mouse sposterà il controller e potrà anche essere spostato più o più vicino alla fotocamera usando la rotellina del mouse.</span><span class="sxs-lookup"><span data-stu-id="77adf-200">Hold the **Left Shift** or **Space** key to bring up the controller (simulated hands), Mouse movement will move the controller and also it can be moved further or closer to the camera using the mouse wheel.</span></span> <span data-ttu-id="77adf-201">Quando il puntatore è posizionato sul cubo, tenere premuto **il pulsante sinistro del mouse** per afferrare l'oggetto Cube.</span><span class="sxs-lookup"><span data-stu-id="77adf-201">Once the pointer is on the Cube press and hold **Left Mouse Button** to grab the Cube object.</span></span>

* <span data-ttu-id="77adf-202">Premere **i tasti W, A, S, D, Q, E** per spostare la fotocamera.</span><span class="sxs-lookup"><span data-stu-id="77adf-202">Press **W, A, S, D, Q, E** keys to move the camera.</span></span>
* <span data-ttu-id="77adf-203">Tenere premuto **il pulsante destro del mouse** e spostare il mouse per guardarsi attorno.</span><span class="sxs-lookup"><span data-stu-id="77adf-203">Hold the **Right mouse button** and move the mouse to look around.</span></span>
* <span data-ttu-id="77adf-204">Per visualizzare le mani simulate, premere **BARRA SPAZIATRICE (mano destra)** o **MAIUSC sinistro (mano sinistra)**</span><span class="sxs-lookup"><span data-stu-id="77adf-204">To bring up the simulated hands, press **Space bar(Right hand)** or **Left Shift key(Left hand)**</span></span>
* <span data-ttu-id="77adf-205">Per mantenere le mani simulate nella visualizzazione, premere **il tasto T** o **Y**</span><span class="sxs-lookup"><span data-stu-id="77adf-205">To keep simulated hands in the view, press **T** or **Y** key</span></span>
* <span data-ttu-id="77adf-206">Per ruotare le mani simulate, tenere premuto **CTRL** e spostare il mouse</span><span class="sxs-lookup"><span data-stu-id="77adf-206">To rotate simulated hands, press and hold **Ctrl** key and move mouse</span></span>

![Modalità di gioco](images/mr-learning-base/base-02-section8-step1-4.gif)


## <a name="building-your-application-to-your-hololens-2"></a><span data-ttu-id="77adf-208">Compilazione dell'applicazione nel dispositivo HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="77adf-208">Building your application to your HoloLens 2</span></span>

### <a name="1-build-the-unity-project"></a><span data-ttu-id="77adf-209">1. Compilare il progetto Unity</span><span class="sxs-lookup"><span data-stu-id="77adf-209">1. Build the Unity project</span></span>

<span data-ttu-id="77adf-210">Dal menu di Unity scegli **File** > **Build Settings** (Impostazioni di compilazione) per visualizzare la finestra corrispondente.</span><span class="sxs-lookup"><span data-stu-id="77adf-210">In the Unity menu, select **File** > **Build Settings...** to open the Build Settings window.</span></span>

<span data-ttu-id="77adf-211">Nella finestra Build Settings (Impostazioni di compilazione), fai clic sul pulsante **Add Open Scenes** (Aggiungi scene aperte) per aggiungere la scena corrente all'elenco **Scenes In Build** (Scene in compilazione) e quindi fai clic sul pulsante **Build** (Compila) per visualizzare la finestra Build Universal Windows Platform (Compilazione UWP):</span><span class="sxs-lookup"><span data-stu-id="77adf-211">In the Build Settings window, click the **Add Open Scenes** button to add your current scene to the **Scenes In Build** list, then click the **Build** button to open the Build Universal Windows Platform window:</span></span>

![Finestra Build Settings di Unity con la piattaforma UWP selezionata](images/mr-learning-base/base-02-section9-step1-1.png)

<span data-ttu-id="77adf-213">Nella finestra Build Universal Windows Platform (Compilazione UWP), scegli un percorso appropriato in cui archiviare la compilazione, ad esempio _D:\MixedRealityLearning\Builds_, crea una nuova cartella e assegnale un nome adatto (ad esempio, _GettingStarted_) e quindi fai clic sul pulsante **Select Folder** (Seleziona cartella) per avviare il processo di compilazione:</span><span class="sxs-lookup"><span data-stu-id="77adf-213">In the Build Universal Windows Platform window, choose a suitable location to store your build, for example, _D:\MixedRealityLearning\Builds_, create a new folder and give it a suitable name, for example, _GettingStarted_, and then click the **Select Folder** button to start the build process:</span></span>

![Finestra Build Settings di Unity con la finestra del prompt di selezione della cartella](images/mr-learning-base/base-02-section9-step1-2.png)

<span data-ttu-id="77adf-215">Attendi che Unity completi il processo di compilazione:</span><span class="sxs-lookup"><span data-stu-id="77adf-215">Wait for Unity to finish the build process:</span></span>

![Processo di compilazione di Unity in corso](images/mr-learning-base/base-02-section9-step1-3.png)

### <a name="2-build-and-deploy-the-application"></a><span data-ttu-id="77adf-217">2. Compilare e distribuire l'applicazione</span><span class="sxs-lookup"><span data-stu-id="77adf-217">2. Build and deploy the application</span></span>

<span data-ttu-id="77adf-218">Al termine del processo di compilazione, Unity richiederà a Esplora file di Windows di aprire il percorso in cui è stata archiviata la compilazione.</span><span class="sxs-lookup"><span data-stu-id="77adf-218">When the build process has completed, Unity will prompt Windows File Explorer to open the location you stored the build.</span></span> <span data-ttu-id="77adf-219">Spostati all'interno della cartella e fai doppio clic sul file della soluzione per aprirlo in Visual Studio:</span><span class="sxs-lookup"><span data-stu-id="77adf-219">Navigate inside the folder, and double-click the solution file to open it in Visual Studio:</span></span>

![Esplora risorse con la soluzione di Visual Studio appena creata selezionata](images/mr-learning-base/base-02-section10-step1-1.png)

> [!NOTE]
> <span data-ttu-id="77adf-221">Se Visual Studio chiede di installare nuovi componenti, dedica qualche minuto a verificare di disporre di tutti i componenti indispensabili come specificato nella documentazione **[Installare gli strumenti](../../install-the-tools.md)** .</span><span class="sxs-lookup"><span data-stu-id="77adf-221">If Visual Studio asks you to install new components, take a moment to check that you have all the prerequisite components in the **[Install the Tools](../../install-the-tools.md)** documentation.</span></span>

<span data-ttu-id="77adf-222">Configura Visual Studio per HoloLens selezionando la configurazione **Master** o **Release**, l'architettura **ARM64** e **Dispositivo** come destinazione:</span><span class="sxs-lookup"><span data-stu-id="77adf-222">Configure Visual Studio for HoloLens by selecting the **Master** or **Release** configuration, the **ARM64** architecture, and **Device** as target:</span></span>

![Visual Studio configurato per la distribuzione in HoloLens 2](images/mr-learning-base/base-02-section10-step1-2.png)

> [!TIP]
> <span data-ttu-id="77adf-224">Se esegui la distribuzione in HoloLens (1a generazione), seleziona l'architettura **x86**.</span><span class="sxs-lookup"><span data-stu-id="77adf-224">If you're deploying to HoloLens (1st generation), select the **x86** architecture.</span></span>

> [!NOTE]
> <span data-ttu-id="77adf-225">Per HoloLens, in genere la compilazione viene eseguita per l'architettura ARM.</span><span class="sxs-lookup"><span data-stu-id="77adf-225">For HoloLens, you will typically build for the ARM architecture.</span></span> <span data-ttu-id="77adf-226">Esiste tuttavia un <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank"><strong>problema noto</strong></a> in Unity 2019.3 che causa errori quando viene selezionata l'architettura di compilazione ARM in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="77adf-226">However, there is a  <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank"><strong>known issue</strong></a> in Unity 2019.3 that causes errors when selecting ARM as the build architecture in Visual Studio.</span></span> <span data-ttu-id="77adf-227">La soluzione consigliata consiste nel compilare per ARM64.</span><span class="sxs-lookup"><span data-stu-id="77adf-227">The recommended workaround is to build for ARM64.</span></span> <span data-ttu-id="77adf-228">Se questa opzione non è applicabile, passa a **Modifica > Impostazioni progetto > Player (Lettore) > Altre impostazioni** e disabilita **Graphics Jobs** (Processi grafici).</span><span class="sxs-lookup"><span data-stu-id="77adf-228">If that is not an option, go to **Edit > Project Settings > Player > Other Settings** and disable **Graphics Jobs**.</span></span>

> [!NOTE]
> <span data-ttu-id="77adf-229">Se non viene visualizzata l'opzione Dispositivo come destinazione, potresti dover modificare il progetto di avvio per la soluzione di Visual Studio passando dal progetto IL2CPP al progetto UWP.</span><span class="sxs-lookup"><span data-stu-id="77adf-229">If you don't see Device as a target option, you may need to change the startup project for the Visual Studio solution from the IL2CPP project to the UWP project.</span></span> <span data-ttu-id="77adf-230">A tale scopo, in Esplora soluzioni fai clic con il pulsante destro del mouse su NomeProgetto (Windows universale) e scegli **Imposta come progetto di avvio**.</span><span class="sxs-lookup"><span data-stu-id="77adf-230">To do this, in the Solution Explorer, right-click on YourProjectName (Universal Windows) and select **Set as StartUp Project**.</span></span>

<span data-ttu-id="77adf-231">Connetti HoloLens al computer e quindi seleziona **Debug** > **Avvia senza eseguire il debug** per eseguire la compilazione e la distribuzione nel dispositivo:</span><span class="sxs-lookup"><span data-stu-id="77adf-231">Connect your HoloLens to your computer, then select **Debug** > **Start Without Debugging** to build and deploy to your device:</span></span>

![Percorso del menu di avvio di Visual Studio senza debug](images/mr-learning-base/base-02-section10-step1-3.png)

> [!IMPORTANT]
> <span data-ttu-id="77adf-233">Prima della compilazione nel dispositivo, quest'ultimo deve essere in modalità sviluppatore e associato al computer di sviluppo.</span><span class="sxs-lookup"><span data-stu-id="77adf-233">Before building to your device, the device must be in Developer Mode and paired with your development computer.</span></span> <span data-ttu-id="77adf-234">Per completare i due passaggi segui [queste istruzioni](../../platform-capabilities-and-apis/using-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="77adf-234">Both of these steps can be completed by following [these instructions](../../platform-capabilities-and-apis/using-visual-studio.md).</span></span>

> [!TIP]
> <span data-ttu-id="77adf-235">Puoi anche eseguire la distribuzione nell'[emulatore HoloLens](../../platform-capabilities-and-apis/using-the-hololens-emulator.md) o creare un [Pacchetto applicazione](/windows/uwp/packaging/packaging-uwp-apps) per il sideload.</span><span class="sxs-lookup"><span data-stu-id="77adf-235">You can also deploy to the [HoloLens Emulator](../../platform-capabilities-and-apis/using-the-hololens-emulator.md) or create an [App Package](/windows/uwp/packaging/packaging-uwp-apps) for sideloading.</span></span>

<span data-ttu-id="77adf-236">Usando Avvia senza eseguire il debug, l'app viene avviata nel dispositivo senza collegare il debugger di Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="77adf-236">Using Start Without Debugging automatically starts the app on your device without the Visual Studio debugger attached.</span></span>

<span data-ttu-id="77adf-237">Seleziona **Compila > Distribuisci soluzione** per eseguire la distribuzione nel dispositivo senza che l'app venga avviata automaticamente.</span><span class="sxs-lookup"><span data-stu-id="77adf-237">Select **Build > Deploy Solution** to deploy to your device without having the app start automatically.</span></span>

> [!NOTE]
><span data-ttu-id="77adf-238">È possibile notare il profiler di diagnostica nell'app, che è possibile attivare o disattivare usando il comando vocale **"Attiva/Disattiva diagnostica".**</span><span class="sxs-lookup"><span data-stu-id="77adf-238">You may notice the Diagnostics profiler in the app, which you can toggle on or off by using the speech command **"Toggle Diagnostics"**.</span></span> <span data-ttu-id="77adf-239">È consigliabile mantenere visibile il profiler la maggior parte del tempo durante lo sviluppo per verificare quando le modifiche apportate all'app possono produrre effetti negativi sulle prestazioni.</span><span class="sxs-lookup"><span data-stu-id="77adf-239">It's recommended that you keep the profiler visible most of the time during development to understand when changes to the app may impact performance.</span></span> <span data-ttu-id="77adf-240">Le app HoloLens ad esempio devono [essere eseguite costantemente a 60 FPS](../../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md).</span><span class="sxs-lookup"><span data-stu-id="77adf-240">For example, HoloLens apps should [continuously run at 60 FPS](../../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md).</span></span>

## <a name="congratulations"></a><span data-ttu-id="77adf-241">Lezione completata</span><span class="sxs-lookup"><span data-stu-id="77adf-241">Congratulations</span></span>

<span data-ttu-id="77adf-242">A questo punto hai distribuito la tua prima app per HoloLens.</span><span class="sxs-lookup"><span data-stu-id="77adf-242">You've now deployed your first HoloLens app.</span></span> <span data-ttu-id="77adf-243">Una volta aperta l'app, dovrebbe essere visualizzato un oggetto Cube e dovrebbe essere possibile interagire con il cubo spostando il cubo e, mentre ci si sposta, si dovrebbe vedere una mesh di mapping spaziale che copre le superfici percepite dal HoloLens.</span><span class="sxs-lookup"><span data-stu-id="77adf-243">Once the app is opened you should see a Cube object in front of you and should be able to interact with the cube by moving it and also as you walk around, you should see a spatial mapping mesh covering the surfaces that are perceived by the HoloLens.</span></span> <span data-ttu-id="77adf-244">Dovresti anche vedere indicatori sulle mani e sulle dita per il tracciamento delle mani e un contatore della frequenza dei fotogrammi per tenere sotto controllo le prestazioni dell'app.</span><span class="sxs-lookup"><span data-stu-id="77adf-244">Additionally, you should see indicators on your hands and fingers for hand tracking and a frame rate counter for keeping an eye on app performance.</span></span> <span data-ttu-id="77adf-245">Queste funzionalità sono solo alcune delle parti fondamentali incluse in MRTK.</span><span class="sxs-lookup"><span data-stu-id="77adf-245">These features are just a few foundational pieces included with MRTK.</span></span> <span data-ttu-id="77adf-246">Nelle esercitazioni successive aggiungerai contenuto alla scena per esplorare le funzionalità di HoloLens e MRTK.</span><span class="sxs-lookup"><span data-stu-id="77adf-246">In the upcoming tutorials, you'll add content to your scene to explore the capabilities of HoloLens and the MRTK.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="77adf-247">Esercitazione successiva: 3. Configurazione dei profili di MRTK</span><span class="sxs-lookup"><span data-stu-id="77adf-247">Next Tutorial: 3. Configuring the MRTK profiles</span></span>](mr-learning-base-03.md)

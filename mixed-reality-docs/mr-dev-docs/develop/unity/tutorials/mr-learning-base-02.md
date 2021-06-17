---
title: Inizializzazione del progetto e distribuzione della prima applicazione
description: In questo corso viene illustrato come configurare il progetto Unity per Mixed Reality Toolkit (MRTK) e come distribuirlo in HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens, MRTK, mixed reality toolkit, UWP, TextMeshPro,
ms.localizationpriority: high
ms.openlocfilehash: fad4b389dc1aef2085b212404c7e17dfcf017701
ms.sourcegitcommit: c65759b8d6465b6b13925cacab5af74443f7e6bd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/15/2021
ms.locfileid: "112110290"
---
# <a name="2-initializing-your-project-and-deploying-your-first-application"></a><span data-ttu-id="d24c3-104">2. Inizializzazione del progetto e distribuzione della prima applicazione</span><span class="sxs-lookup"><span data-stu-id="d24c3-104">2. Initializing your project and deploying your first application</span></span>

<span data-ttu-id="d24c3-105">In questa esercitazione apprenderai come creare un nuovo progetto Unity, come configurarlo per lo sviluppo Mixed Reality Toolkit (MRTK) e come importare MRTK.</span><span class="sxs-lookup"><span data-stu-id="d24c3-105">In this tutorial, you'll learn how to create a new Unity project, configure it for Mixed Reality Toolkit (MRTK) development, and import MRTK.</span></span> <span data-ttu-id="d24c3-106">Verranno inoltre esaminati i processi di configurazione, compilazione e distribuzione di una scena Unity di base da Visual Studio a HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="d24c3-106">You'll also walk through configuring, building, and deploying a basic Unity scene from Visual Studio to your HoloLens 2.</span></span> <span data-ttu-id="d24c3-107">Dopo la distribuzione in HoloLens 2, dovrebbe essere visualizzata una mesh di mapping spaziale che copre le superfici percepite da HoloLens.</span><span class="sxs-lookup"><span data-stu-id="d24c3-107">Once you have deployed it to your HoloLens 2, you should see a spatial mapping mesh covering the surfaces that are perceived by the HoloLens.</span></span> <span data-ttu-id="d24c3-108">Dovresti anche vedere indicatori sulle mani e sulle dita per il tracciamento delle mani e un contatore della frequenza dei fotogrammi per tenere sotto controllo le prestazioni dell'app.</span><span class="sxs-lookup"><span data-stu-id="d24c3-108">Additionally, you should see indicators on your hands and fingers for hand tracking and a frame rate counter for keeping an eye on app performance.</span></span>

![MRTK](../../../develop/images/Unity_MRTK_MRFT_Flow.png)

## <a name="objectives"></a><span data-ttu-id="d24c3-110">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="d24c3-110">Objectives</span></span>

* <span data-ttu-id="d24c3-111">Apprendere come configurare Unity per lo sviluppo per HoloLens</span><span class="sxs-lookup"><span data-stu-id="d24c3-111">Learn how to configure Unity for HoloLens development</span></span>
* <span data-ttu-id="d24c3-112">Apprendere come compilare e distribuire l'app in HoloLens</span><span class="sxs-lookup"><span data-stu-id="d24c3-112">Learn how to build and deploy your app to HoloLens</span></span>
* <span data-ttu-id="d24c3-113">Sperimentare la mesh di mapping spaziale, le mesh manuali e il contatore della frequenza dei fotogrammi sul dispositivo HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="d24c3-113">Experience the spatial mapping mesh, hand meshes, and the framerate counter on HoloLens 2 device</span></span>

## <a name="creating-the-unity-project"></a><span data-ttu-id="d24c3-114">Creazione del progetto Unity</span><span class="sxs-lookup"><span data-stu-id="d24c3-114">Creating the Unity project</span></span>

<span data-ttu-id="d24c3-115">Avvia **Unity Hub**, seleziona la scheda **Projects** (Progetti) e fai clic sulla **freccia giù** accanto al pulsante **New** (Nuovo):</span><span class="sxs-lookup"><span data-stu-id="d24c3-115">Launch **Unity Hub**, select the **Projects** tab, and click the **down arrow** next to the **New** button:</span></span>

![Unity Hub con il pulsante New evidenziato](images/mr-learning-base/base-02-section1-step1-1.png)

<span data-ttu-id="d24c3-117">Nell'elenco a discesa seleziona la **versione** di Unity specificata nella sezione [Prerequisiti](mr-learning-base-01.md#prerequisites):</span><span class="sxs-lookup"><span data-stu-id="d24c3-117">In the dropdown, select the Unity **version** specified in the [Prerequisites](mr-learning-base-01.md#prerequisites):</span></span>

![Unity Hub con l'elenco a discesa per la seleziona della versione NEW](images/mr-learning-base/base-02-section1-step1-2.png)

> [!TIP]
> <span data-ttu-id="d24c3-119">Se la versione specifica di Unity non è disponibile in Unity Hub, puoi avviare l'installazione da <a href="https://unity3d.com/get-unity/download/archive" target="_blank">Download Archive</a> (Archivio download) di Unity.</span><span class="sxs-lookup"><span data-stu-id="d24c3-119">If the particular Unity version is not available in Unity Hub, you can initiate the installation from Unity's <a href="https://unity3d.com/get-unity/download/archive" target="_blank">Download Archive</a>.</span></span>

<span data-ttu-id="d24c3-120">Nella finestra Create a new project (Crea un nuovo progetto):</span><span class="sxs-lookup"><span data-stu-id="d24c3-120">In the Create a new project window:</span></span>

* <span data-ttu-id="d24c3-121">Assicurati che in **Templates** (Modelli) sia impostata l'opzione **3D**</span><span class="sxs-lookup"><span data-stu-id="d24c3-121">Ensure **Templates** is set to **3D**</span></span>
* <span data-ttu-id="d24c3-122">Immetti un nome appropriato nel campo **Project Name** (Nome progetto), ad esempio _MRTK Tutorials_</span><span class="sxs-lookup"><span data-stu-id="d24c3-122">Enter a suitable **Project Name**, for example, _MRTK Tutorials_</span></span>
* <span data-ttu-id="d24c3-123">Nel campo **Location** (Percorso) scegli un percorso appropriato in cui archiviare il progetto, ad esempio _D:\MixedRealityLearning_</span><span class="sxs-lookup"><span data-stu-id="d24c3-123">Choose a suitable **Location** to store your project, for example, _D:\MixedRealityLearning_</span></span>
* <span data-ttu-id="d24c3-124">Fai clic sul pulsante **Create** (Crea) per creare e avviare il nuovo progetto Unity</span><span class="sxs-lookup"><span data-stu-id="d24c3-124">Click the **Create** button to create and launch your new Unity project</span></span>

![Unity Hub con la finestra Create a new project compilata](images/mr-learning-base/base-02-section1-step1-3.png)

> [!CAUTION]
> <span data-ttu-id="d24c3-126">Se lavori in Windows, tieni presente che è previsto un limite (MAX_PATH) di 255 caratteri per il percorso.</span><span class="sxs-lookup"><span data-stu-id="d24c3-126">When working on Windows, there is a MAX_PATH limit of 255 characters.</span></span> <span data-ttu-id="d24c3-127">Dovresti pertanto salvare il progetto Unity in prossimità della radice dell'unità.</span><span class="sxs-lookup"><span data-stu-id="d24c3-127">Consequently, you should save the Unity project close to the root of the drive.</span></span>

<span data-ttu-id="d24c3-128">Attendi che Unity crei il progetto:</span><span class="sxs-lookup"><span data-stu-id="d24c3-128">Wait for Unity to create the project:</span></span>

![Creazione di un nuovo progetto Unity in corso](images/mr-learning-base/base-02-section1-step1-4.png)

## <a name="switching-the-build-platform"></a><span data-ttu-id="d24c3-130">Passaggio a un'altra piattaforma di compilazione</span><span class="sxs-lookup"><span data-stu-id="d24c3-130">Switching the build platform</span></span>

[!INCLUDE[](includes/switching-build-platform.md)]

## <a name="importing-the-textmeshpro-essential-resources"></a><span data-ttu-id="d24c3-131">Importazione delle risorse essenziali TextMeshPro</span><span class="sxs-lookup"><span data-stu-id="d24c3-131">Importing the TextMeshPro Essential Resources</span></span>

<span data-ttu-id="d24c3-132">Scegli **Window (Finestra)**  > **TextMeshPro** > **Import TMP Essential Resources** (Importa le risorse essenziali TMP) dal menu di Unity per aprire la finestra Import Unity Package (Importa pacchetto Unity):</span><span class="sxs-lookup"><span data-stu-id="d24c3-132">In the Unity menu, select **Window** > **TextMeshPro** > **Import TMP Essential Resources** to open the Import Unity Package window:</span></span>

![Percorso del menu Import TMP Essential Resources di Unity](images/mr-learning-base/base-02-section3-step1-1.png)

<span data-ttu-id="d24c3-134">Nella finestra Import Unity Package (Importa il pacchetto Unity), fai clic sul pulsante **All** (Tutti) per assicurarti che vengano selezionati tutti gli asset e quindi fai clic sul pulsante **Import** (Importa) per importare gli asset:</span><span class="sxs-lookup"><span data-stu-id="d24c3-134">In the Import Unity Package window, click the **All** button to ensure all the assets are selected, then click the **Import** button to import the assets:</span></span>

![Finestra di importazione TMP Essential Resources di Unity](images/mr-learning-base/base-02-section3-step1-2.png)

> [!TIP]
> <span data-ttu-id="d24c3-136">Le risorse essenziali TextMeshPro sono richieste dagli elementi dell'interfaccia utente di MRTK.</span><span class="sxs-lookup"><span data-stu-id="d24c3-136">The TextMeshPro Essential Resources are required by MRTK's UI elements.</span></span> <span data-ttu-id="d24c3-137">Puoi ignorare questo passaggio se non prevedi di usare gli elementi dell'interfaccia utente di MRTK nel progetto.</span><span class="sxs-lookup"><span data-stu-id="d24c3-137">You can skip this step if you are not planning to use MRTK's UI elements in your project.</span></span>

## <a name="importing-the-mixed-reality-toolkit-and-configuring-the-unity-project"></a><span data-ttu-id="d24c3-138">Importazione di Mixed Reality Toolkit e configurazione del progetto Unity</span><span class="sxs-lookup"><span data-stu-id="d24c3-138">Importing the Mixed Reality Toolkit and Configuring the Unity project</span></span>

<span data-ttu-id="d24c3-139">Per importare Mixed Reality Toolkit nel progetto Unity, è necessario usare lo strumento [funzionalità](../welcome-to-mr-feature-tool.md) realtà mista che consente agli sviluppatori di individuare, aggiornare e aggiungere pacchetti di funzionalità di realtà mista nei progetti Unity.</span><span class="sxs-lookup"><span data-stu-id="d24c3-139">To Import Mixed Reality Toolkit into the Unity Project you will have to use [Mixed Reality Feature Tool](../welcome-to-mr-feature-tool.md) which allows  developers to discover, update, and add Mixed Reality feature packages into Unity projects.</span></span> <span data-ttu-id="d24c3-140">È possibile cercare i pacchetti in base al nome o alla categoria, visualizzarne le dipendenze e persino visualizzare le modifiche proposte al file manifesto del progetto prima dell'importazione.</span><span class="sxs-lookup"><span data-stu-id="d24c3-140">You can search packages by name or category, see their dependencies, and even view proposed changes to your projects manifest file before importing.</span></span>

<span data-ttu-id="d24c3-141">Scaricare la versione più recente di Mixed Reality Feature Tool dall'Area download [Microsoft](https://aka.ms/MRFeatureTool). Al termine del download, decomprimere il file e salvarlo sul desktop.</span><span class="sxs-lookup"><span data-stu-id="d24c3-141">Download the latest version of the Mixed Reality Feature Tool from the [Microsoft Download Center](https://aka.ms/MRFeatureTool), When the download is complete, unzip the file and save it to your desktop.</span></span>

> [!NOTE]
> <span data-ttu-id="d24c3-142">Prima di poter eseguire lo strumento di funzionalità di realtà mista, installare [il runtime di .NET 5.0](https://dotnet.microsoft.com/download/dotnet/5.0)</span><span class="sxs-lookup"><span data-stu-id="d24c3-142">Before you can run the Mixed Reality Feature Tool please install [.NET 5.0 runtime](https://dotnet.microsoft.com/download/dotnet/5.0)</span></span>

> [!NOTE]
> <span data-ttu-id="d24c3-143">Lo strumento di funzionalità realtà mista attualmente viene [](/windows/mixed-reality/mrtk-unity/configuration/usingupm) eseguito solo in Windows. Per MacOS seguire questa procedura per scaricare e importare Mixed Reality Toolkit nel progetto unity.</span><span class="sxs-lookup"><span data-stu-id="d24c3-143">The Mixed Reality Feature Tool currently only runs on Windows, For MacOS please follow this [procedure](/windows/mixed-reality/mrtk-unity/configuration/usingupm) to download and import the Mixed Reality Toolkit into the unity project.</span></span>

<span data-ttu-id="d24c3-144">Aprire il file eseguibile **MixedRealityFeatureTool** dalla cartella scaricata per avviare Mixed Reality Feature Tool.</span><span class="sxs-lookup"><span data-stu-id="d24c3-144">Open the executable file **MixedRealityFeatureTool** from the downloaded folder to launch the Mixed Reality Feature Tool.</span></span>  

![Apertura di MixedRealityFeatureTool](images/mr-learning-base/base-02-section4-step1-1.png)

[!INCLUDE[](includes/importing-mrtk.md)]

## <a name="creating-the-scene-and-configuring-mrtk"></a><span data-ttu-id="d24c3-146">Creazione della scena e configurazione di MRTK</span><span class="sxs-lookup"><span data-stu-id="d24c3-146">Creating the scene and configuring MRTK</span></span>

<span data-ttu-id="d24c3-147">Nel menu Unity selezionare **File**  >  **Nuova scena**:</span><span class="sxs-lookup"><span data-stu-id="d24c3-147">In the Unity menu, select **File** > **New Scene**:</span></span>

![Percorso del menu New Scene di Unity](images/mr-learning-base/base-02-section6-step1-1.png)

<span data-ttu-id="d24c3-149">Nella finestra **Nuova scena** selezionare **Basic (incorporato)** e fare clic su **Crea** per creare una nuova scena:</span><span class="sxs-lookup"><span data-stu-id="d24c3-149">In the **New Scene** window select **Basic (Built-in)** and click on **create** to create a new scene:</span></span>

![Finestra Nuova scena di Unity](images/mr-learning-base/base-02-section6-step1-1-newscene.png)

> [!NOTE]
> <span data-ttu-id="d24c3-151">Lo screenshot precedente è della versione 2020 di Unity, se si  usa Unity 2019 quando si fa clic su Crea una nuova scena vuota.</span><span class="sxs-lookup"><span data-stu-id="d24c3-151">Above screenshot is from Unity Version 2020, if you are using Unity 2019 when you click on **create** a new empty scene will be created.</span></span>

<span data-ttu-id="d24c3-152">Nel menu Unity selezionare **Mixed Reality** Toolkit Add to Scene (Aggiungi alla scena)  >    >  **e Configure (Configura)** per aggiungere MRTK alla scena corrente:</span><span class="sxs-lookup"><span data-stu-id="d24c3-152">In the Unity menu, select **Mixed Reality** > **Toolkit** > **Add to Scene and Configure...** to add the MRTK to your current scene:</span></span>

![Percorso del menu Add to Scene and Configure... di Unity](images/mr-learning-base/base-02-section6-step1-2.png)

<span data-ttu-id="d24c3-154">Con l'oggetto **MixedRealityToolkit** selezionato nella finestra Hierarchy (Gerarchia), nella finestra Inspector (Controllo) verifica che il profilo di configurazione di **Mixed Reality Toolkit** sia impostato su **DefaultMixedRealityToolkitConfigurationProfile**:</span><span class="sxs-lookup"><span data-stu-id="d24c3-154">With the **MixedRealityToolkit** object still selected in the Hierarchy window, in the Inspector window, verify that the **MixedRealityToolkit** configuration profile is set to **DefaultMixedRealityToolkitConfigurationProfile**:</span></span>

![Componente MixedRealityToolkit di Unity con DefaultMixedRealityTookitConfigurationProfile selezionato](images/mr-learning-base/base-02-section6-step1-3.png)

<span data-ttu-id="d24c3-156">Dal menu di Unity scegli **File** > **Save As** (Salva con nome) per visualizzare la finestra Save Scene (Salva la scena):</span><span class="sxs-lookup"><span data-stu-id="d24c3-156">In the Unity menu, select **File** > **Save As...** to open the Save Scene window:</span></span>

![Percorso del menu Save As... di Unity](images/mr-learning-base/base-02-section6-step1-4.png)

<span data-ttu-id="d24c3-158">Salvare la scena nel progetto in **Asset**  >  **Scenes**.</span><span class="sxs-lookup"><span data-stu-id="d24c3-158">Save the scene in you project under **Asset** > **Scenes**.</span></span>

![Finestra Save Scene di Unity con il prompt di salvataggio](images/mr-learning-base/base-02-section6-step1-5.png)

## <a name="importing-the-tutorial-assets"></a><span data-ttu-id="d24c3-160">Importazione degli asset dell'esercitazione</span><span class="sxs-lookup"><span data-stu-id="d24c3-160">Importing the tutorial assets</span></span>

<span data-ttu-id="d24c3-161">Scaricare il pacchetto personalizzato Unity seguente:</span><span class="sxs-lookup"><span data-stu-id="d24c3-161">Download the following Unity custom package:</span></span>

* [<span data-ttu-id="d24c3-162">MRTK. HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.5.0.1.unitypackage</span><span class="sxs-lookup"><span data-stu-id="d24c3-162">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.5.0.1.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.5.0/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.5.0.1.unitypackage)

<span data-ttu-id="d24c3-163">Per importare un pacchetto personalizzato unity, nel menu Unity selezionare **Asset Importa** pacchetto personalizzato  >    >  **pacchetto...** per aprire Importa pacchetto. Finestra:</span><span class="sxs-lookup"><span data-stu-id="d24c3-163">To Import a Unity custom package, In the Unity menu, select **Assets** > **Import Package** > **Custom Package...** to open the Import package... window:</span></span>

![Importazione di un pacchetto personalizzato](images/mr-learning-base/base-02-section7-step1-1.png)

<span data-ttu-id="d24c3-165">Nel pacchetto Di importazione... , selezionare **MRTK. HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.5.0.1.unitypackage** scaricato e fare clic sul pulsante Apri:</span><span class="sxs-lookup"><span data-stu-id="d24c3-165">In the Import package... window, select the **MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.5.0.1.unitypackage** you downloaded and click the Open button:</span></span>

![Selezione di un pacchetto di asset](images/mr-learning-base/base-02-section7-step1-2.png)

<span data-ttu-id="d24c3-167">Nella finestra Importa pacchetto Unity fare clic sul pulsante Tutti per assicurarsi che siano selezionati tutti gli asset, quindi fare clic sul pulsante Importa per importare gli asset:</span><span class="sxs-lookup"><span data-stu-id="d24c3-167">In the Import Unity Package window, click the All button to ensure all the assets are selected, then click the Import button to import the assets:</span></span>

![Selezione di tutti gli asset da importare](images/mr-learning-base/base-02-section7-step1-3.png)

<span data-ttu-id="d24c3-169">Dopo l'importazione degli asset dell'esercitazione, la finestra Project (Progetto) avrà un aspetto simile al seguente:</span><span class="sxs-lookup"><span data-stu-id="d24c3-169">After you have imported the tutorial assets your Project window should look similar to this:</span></span>

![Finestra del progetto Unity dopo l'importazione di asset](images/mr-learning-base/base-02-section7-step1-4.png)

## <a name="configuring-the-scene"></a><span data-ttu-id="d24c3-171">Configurazione della scena</span><span class="sxs-lookup"><span data-stu-id="d24c3-171">Configuring the Scene</span></span>

<span data-ttu-id="d24c3-172">Nella finestra Project (Progetto) passare alla cartella **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** (Prefab):</span><span class="sxs-lookup"><span data-stu-id="d24c3-172">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** folder:</span></span>

<span data-ttu-id="d24c3-173">Dalla finestra Progetto fare clic e trascinare il **prefab** Cubo nella finestra Gerarchia, quindi nella finestra Controllo configurare il componente Trasforma come indicato di seguito. </span><span class="sxs-lookup"><span data-stu-id="d24c3-173">From the Project window, click-and-drag the **Cube** prefab on to the Hierarchy window, then in the Inspector window configure its **Transform** component as follows</span></span>

* <span data-ttu-id="d24c3-174">**Posizione:** X = 0, Y = 0, Z = 0,5</span><span class="sxs-lookup"><span data-stu-id="d24c3-174">**Position**: X = 0, Y = 0, Z = 0.5</span></span>
* <span data-ttu-id="d24c3-175">**Rotation** (Rotazione): X = 0, Y = 0, Z = 0</span><span class="sxs-lookup"><span data-stu-id="d24c3-175">**Rotation**: X = 0, Y = 0, Z = 0</span></span>
* <span data-ttu-id="d24c3-176">**Scale** (Scala): X = 1, Y = 1, Z = 1</span><span class="sxs-lookup"><span data-stu-id="d24c3-176">**Scale**: X = 1, Y = 1, Z = 1</span></span>

![Aggiunta di un cubo alla scena](images/mr-learning-base/base-02-section8-step1-1.PNG)

<span data-ttu-id="d24c3-178">Per concentrarsi sugli oggetti nella scena, è possibile fare doppio clic **sull'oggetto Cubo** e quindi eseguire di nuovo lo zoom avanti leggermente:</span><span class="sxs-lookup"><span data-stu-id="d24c3-178">To focus in on the objects in the scene, you can double-click on the **Cube** object, and then zoom slightly in again:</span></span>

<span data-ttu-id="d24c3-179">Per interagire e afferrare un oggetto con le mani rilevate, l'oggetto deve avere un componente Collisore, ad esempio un componente **Box Collider**, **Object Manipulator (Script)** e **NearInteractionGrabbable(Script).**</span><span class="sxs-lookup"><span data-stu-id="d24c3-179">To interact and grab an object with tracked hands, the object must have Collider component for example a **Box Collider**,  **Object Manipulator (Script)** component and **NearInteractionGrabbable(Script)** component.</span></span>

<span data-ttu-id="d24c3-180">Con il **cubo** ancora selezionato nella finestra Hierarchy (Gerarchia), nella finestra Inspector (Controllo) fare clic sul pulsante **Add Component** (Aggiungi componente), quindi cercare e selezionare **Object Manipulator** script (Manipolatore di oggetti) per aggiungere lo script Object Manipulator all'oggetto cubo.</span><span class="sxs-lookup"><span data-stu-id="d24c3-180">With the **Cube** still selected in the Hierarchy window, in the Inspector window ,click on **Add Component** button, then search and select **Object Manipulator** script to add the Object Manipulator script to the cube object.</span></span>

![aggiunta dell'oggetto manupulator al cubo](images/mr-learning-base/base-02-section8-step1-2.PNG)

<span data-ttu-id="d24c3-182">Ripetere la stessa operazione per aggiungere **lo script Near Interaction Grabbable** al cubo</span><span class="sxs-lookup"><span data-stu-id="d24c3-182">Repeat the same to add **Near Interaction Grabbable script** to the cube</span></span>

![aggiunta di Near Interaction Grabable al cubo](images/mr-learning-base/base-02-section8-step1-3.PNG)

> [!NOTE]
> <span data-ttu-id="d24c3-184">Quando si aggiunge un manipolatore di oggetti (script), in questo caso, Gestione vincoli (script) viene aggiunto automaticamente perché il manipolatore di oggetti (script) dipende da esso.</span><span class="sxs-lookup"><span data-stu-id="d24c3-184">When you add a Object Manipulator (Script), in this case, the Constraint Manager (Script) is automatically added because Object Manipulator (Script) depends on it.</span></span>

> [!NOTE]
> <span data-ttu-id="d24c3-185">Ai fini di questa esercitazione, i collisori sono già stati aggiunti all'oggetto cubo.</span><span class="sxs-lookup"><span data-stu-id="d24c3-185">For the purpose of this tutorial, colliders have already been added to the Cube Object.</span></span> <span data-ttu-id="d24c3-186">Per altre informazioni sui collisori, puoi visitare la documentazione <a href="https://docs.unity3d.com/Manual/CollidersOverview.html" target="_blank">corrispondente</a> di Unity.</span><span class="sxs-lookup"><span data-stu-id="d24c3-186">To learn more about colliders, you can visit Unity's <a href="https://docs.unity3d.com/Manual/CollidersOverview.html" target="_blank">Collider</a> documentation.</span></span>

<span data-ttu-id="d24c3-187">Per testarlo nell'editor di Unity, è possibile attivare la modalità di riproduzione e tenere premuto il tasto **LeftShift** o **Space** per abilitare il controller, lo spostamento del mouse sposterà il controller e può anche essere spostato più o più vicino alla fotocamera usando la rotellina del mouse.</span><span class="sxs-lookup"><span data-stu-id="d24c3-187">To test this in the Unity editor, you can enter the play mode and hold the **LeftShift** or **Space** key to enable the controller, Mouse movement will move the controller and also it can be moved further or closer to the camera using the mouse wheel.</span></span> <span data-ttu-id="d24c3-188">Quando il puntatore si trova sul cubo, premere e tenere premuto **il pulsante sinistro del mouse** per spostare l'oggetto Cubo.</span><span class="sxs-lookup"><span data-stu-id="d24c3-188">Once the pointer is on the Cube  press and hold **Left Mouse Button** to move the the Cube object.</span></span>

![Modalità di gioco](images/mr-learning-base/base-02-section8-step1-4.PNG)

## <a name="building-your-application-to-your-hololens-2"></a><span data-ttu-id="d24c3-190">Compilazione dell'applicazione nel dispositivo HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="d24c3-190">Building your application to your HoloLens 2</span></span>

### <a name="1-build-the-unity-project"></a><span data-ttu-id="d24c3-191">1. Compilare il progetto Unity</span><span class="sxs-lookup"><span data-stu-id="d24c3-191">1. Build the Unity project</span></span>

<span data-ttu-id="d24c3-192">Dal menu di Unity scegli **File** > **Build Settings** (Impostazioni di compilazione) per visualizzare la finestra corrispondente.</span><span class="sxs-lookup"><span data-stu-id="d24c3-192">In the Unity menu, select **File** > **Build Settings...** to open the Build Settings window.</span></span>

<span data-ttu-id="d24c3-193">Nella finestra Build Settings (Impostazioni di compilazione), fai clic sul pulsante **Add Open Scenes** (Aggiungi scene aperte) per aggiungere la scena corrente all'elenco **Scenes In Build** (Scene in compilazione) e quindi fai clic sul pulsante **Build** (Compila) per visualizzare la finestra Build Universal Windows Platform (Compilazione UWP):</span><span class="sxs-lookup"><span data-stu-id="d24c3-193">In the Build Settings window, click the **Add Open Scenes** button to add your current scene to the **Scenes In Build** list, then click the **Build** button to open the Build Universal Windows Platform window:</span></span>

![Finestra Build Settings di Unity con la piattaforma UWP selezionata](images/mr-learning-base/base-02-section9-step1-1.png)

<span data-ttu-id="d24c3-195">Nella finestra Build Universal Windows Platform (Compilazione UWP), scegli un percorso appropriato in cui archiviare la compilazione, ad esempio _D:\MixedRealityLearning\Builds_, crea una nuova cartella e assegnale un nome adatto (ad esempio, _GettingStarted_) e quindi fai clic sul pulsante **Select Folder** (Seleziona cartella) per avviare il processo di compilazione:</span><span class="sxs-lookup"><span data-stu-id="d24c3-195">In the Build Universal Windows Platform window, choose a suitable location to store your build, for example, _D:\MixedRealityLearning\Builds_, create a new folder and give it a suitable name, for example, _GettingStarted_, and then click the **Select Folder** button to start the build process:</span></span>

![Finestra Build Settings di Unity con la finestra del prompt di selezione della cartella](images/mr-learning-base/base-02-section9-step1-2.png)

<span data-ttu-id="d24c3-197">Attendi che Unity completi il processo di compilazione:</span><span class="sxs-lookup"><span data-stu-id="d24c3-197">Wait for Unity to finish the build process:</span></span>

![Processo di compilazione di Unity in corso](images/mr-learning-base/base-02-section9-step1-3.png)

### <a name="2-build-and-deploy-the-application"></a><span data-ttu-id="d24c3-199">2. Compilare e distribuire l'applicazione</span><span class="sxs-lookup"><span data-stu-id="d24c3-199">2. Build and deploy the application</span></span>

<span data-ttu-id="d24c3-200">Al termine del processo di compilazione, Unity richiederà a Esplora file di Windows di aprire il percorso in cui è stata archiviata la compilazione.</span><span class="sxs-lookup"><span data-stu-id="d24c3-200">When the build process has completed, Unity will prompt Windows File Explorer to open the location you stored the build.</span></span> <span data-ttu-id="d24c3-201">Spostati all'interno della cartella e fai doppio clic sul file della soluzione per aprirlo in Visual Studio:</span><span class="sxs-lookup"><span data-stu-id="d24c3-201">Navigate inside the folder, and double-click the solution file to open it in Visual Studio:</span></span>

![Esplora risorse con la soluzione di Visual Studio appena creata selezionata](images/mr-learning-base/base-02-section10-step1-1.png)

> [!NOTE]
> <span data-ttu-id="d24c3-203">Se Visual Studio chiede di installare nuovi componenti, dedica qualche minuto a verificare di disporre di tutti i componenti indispensabili come specificato nella documentazione **[Installare gli strumenti](../../install-the-tools.md)** .</span><span class="sxs-lookup"><span data-stu-id="d24c3-203">If Visual Studio asks you to install new components, take a moment to check that you have all the prerequisite components in the **[Install the Tools](../../install-the-tools.md)** documentation.</span></span>

<span data-ttu-id="d24c3-204">Configura Visual Studio per HoloLens selezionando la configurazione **Master** o **Release**, l'architettura **ARM64** e **Dispositivo** come destinazione:</span><span class="sxs-lookup"><span data-stu-id="d24c3-204">Configure Visual Studio for HoloLens by selecting the **Master** or **Release** configuration, the **ARM64** architecture, and **Device** as target:</span></span>

![Visual Studio configurato per la distribuzione in HoloLens 2](images/mr-learning-base/base-02-section10-step1-2.png)

> [!TIP]
> <span data-ttu-id="d24c3-206">Se esegui la distribuzione in HoloLens (1a generazione), seleziona l'architettura **x86**.</span><span class="sxs-lookup"><span data-stu-id="d24c3-206">If you're deploying to HoloLens (1st generation), select the **x86** architecture.</span></span>

> [!NOTE]
> <span data-ttu-id="d24c3-207">Per HoloLens, in genere la compilazione viene eseguita per l'architettura ARM.</span><span class="sxs-lookup"><span data-stu-id="d24c3-207">For HoloLens, you will typically build for the ARM architecture.</span></span> <span data-ttu-id="d24c3-208">Esiste tuttavia un <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank"><strong>problema noto</strong></a> in Unity 2019.3 che causa errori quando viene selezionata l'architettura di compilazione ARM in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="d24c3-208">However, there is a  <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank"><strong>known issue</strong></a> in Unity 2019.3 that causes errors when selecting ARM as the build architecture in Visual Studio.</span></span> <span data-ttu-id="d24c3-209">La soluzione consigliata consiste nel compilare per ARM64.</span><span class="sxs-lookup"><span data-stu-id="d24c3-209">The recommended workaround is to build for ARM64.</span></span> <span data-ttu-id="d24c3-210">Se questa opzione non è applicabile, passa a **Modifica > Impostazioni progetto > Player (Lettore) > Altre impostazioni** e disabilita **Graphics Jobs** (Processi grafici).</span><span class="sxs-lookup"><span data-stu-id="d24c3-210">If that is not an option, go to **Edit > Project Settings > Player > Other Settings** and disable **Graphics Jobs**.</span></span>

> [!NOTE]
> <span data-ttu-id="d24c3-211">Se non viene visualizzata l'opzione Dispositivo come destinazione, potresti dover modificare il progetto di avvio per la soluzione di Visual Studio passando dal progetto IL2CPP al progetto UWP.</span><span class="sxs-lookup"><span data-stu-id="d24c3-211">If you don't see Device as a target option, you may need to change the startup project for the Visual Studio solution from the IL2CPP project to the UWP project.</span></span> <span data-ttu-id="d24c3-212">A tale scopo, in Esplora soluzioni fai clic con il pulsante destro del mouse su NomeProgetto (Windows universale) e scegli **Imposta come progetto di avvio**.</span><span class="sxs-lookup"><span data-stu-id="d24c3-212">To do this, in the Solution Explorer, right-click on YourProjectName (Universal Windows) and select **Set as StartUp Project**.</span></span>

<span data-ttu-id="d24c3-213">Connetti HoloLens al computer e quindi seleziona **Debug** > **Avvia senza eseguire il debug** per eseguire la compilazione e la distribuzione nel dispositivo:</span><span class="sxs-lookup"><span data-stu-id="d24c3-213">Connect your HoloLens to your computer, then select **Debug** > **Start Without Debugging** to build and deploy to your device:</span></span>

![Percorso del menu di avvio di Visual Studio senza debug](images/mr-learning-base/base-02-section10-step1-3.png)

> [!IMPORTANT]
> <span data-ttu-id="d24c3-215">Prima della compilazione nel dispositivo, quest'ultimo deve essere in modalità sviluppatore e associato al computer di sviluppo.</span><span class="sxs-lookup"><span data-stu-id="d24c3-215">Before building to your device, the device must be in Developer Mode and paired with your development computer.</span></span> <span data-ttu-id="d24c3-216">Per completare i due passaggi segui [queste istruzioni](../../platform-capabilities-and-apis/using-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="d24c3-216">Both of these steps can be completed by following [these instructions](../../platform-capabilities-and-apis/using-visual-studio.md).</span></span>

> [!TIP]
> <span data-ttu-id="d24c3-217">Puoi anche eseguire la distribuzione nell'[emulatore HoloLens](../../platform-capabilities-and-apis/using-the-hololens-emulator.md) o creare un [Pacchetto applicazione](/windows/uwp/packaging/packaging-uwp-apps) per il sideload.</span><span class="sxs-lookup"><span data-stu-id="d24c3-217">You can also deploy to the [HoloLens Emulator](../../platform-capabilities-and-apis/using-the-hololens-emulator.md) or create an [App Package](/windows/uwp/packaging/packaging-uwp-apps) for sideloading.</span></span>

<span data-ttu-id="d24c3-218">Usando Avvia senza eseguire il debug, l'app viene avviata nel dispositivo senza collegare il debugger di Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="d24c3-218">Using Start Without Debugging automatically starts the app on your device without the Visual Studio debugger attached.</span></span>

<span data-ttu-id="d24c3-219">Seleziona **Compila > Distribuisci soluzione** per eseguire la distribuzione nel dispositivo senza che l'app venga avviata automaticamente.</span><span class="sxs-lookup"><span data-stu-id="d24c3-219">Select **Build > Deploy Solution** to deploy to your device without having the app start automatically.</span></span>

> [!NOTE]
><span data-ttu-id="d24c3-220">Potrebbe essere visibile nell'app il profiler di diagnostica, che può essere attivato o disattivato tramite il comando vocale **Toggle Diagnostics** (Attiva/Disattiva diagnostica).</span><span class="sxs-lookup"><span data-stu-id="d24c3-220">You may notice the Diagnostics profiler in the app, which you can toggle on or off by using the speech command **Toggle Diagnostics**.</span></span> <span data-ttu-id="d24c3-221">È consigliabile mantenere visibile il profiler la maggior parte del tempo durante lo sviluppo per verificare quando le modifiche apportate all'app possono produrre effetti negativi sulle prestazioni.</span><span class="sxs-lookup"><span data-stu-id="d24c3-221">It's recommended that you keep the profiler visible most of the time during development to understand when changes to the app may impact performance.</span></span> <span data-ttu-id="d24c3-222">Le app HoloLens ad esempio devono [essere eseguite costantemente a 60 FPS](../../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md).</span><span class="sxs-lookup"><span data-stu-id="d24c3-222">For example, HoloLens apps should [continuously run at 60 FPS](../../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md).</span></span>

## <a name="congratulations"></a><span data-ttu-id="d24c3-223">Lezione completata</span><span class="sxs-lookup"><span data-stu-id="d24c3-223">Congratulations</span></span>

<span data-ttu-id="d24c3-224">A questo punto hai distribuito la tua prima app per HoloLens.</span><span class="sxs-lookup"><span data-stu-id="d24c3-224">You've now deployed your first HoloLens app.</span></span> <span data-ttu-id="d24c3-225">Una volta aperta l'app, dovrebbe essere visualizzato un oggetto Cube e dovrebbe essere possibile interagire con il cubo spostando il cubo e, mentre ci si sposta, si dovrebbe vedere una mesh di mapping spaziale che copre le superfici percepite da HoloLens.</span><span class="sxs-lookup"><span data-stu-id="d24c3-225">Once the app is opened you should see a Cube object in front of you and should be able to interact with the cube by moving it and also as you walk around, you should see a spatial mapping mesh covering the surfaces that are perceived by the HoloLens.</span></span> <span data-ttu-id="d24c3-226">Dovresti anche vedere indicatori sulle mani e sulle dita per il tracciamento delle mani e un contatore della frequenza dei fotogrammi per tenere sotto controllo le prestazioni dell'app.</span><span class="sxs-lookup"><span data-stu-id="d24c3-226">Additionally, you should see indicators on your hands and fingers for hand tracking and a frame rate counter for keeping an eye on app performance.</span></span> <span data-ttu-id="d24c3-227">Queste funzionalità sono solo alcune delle parti fondamentali incluse in MRTK.</span><span class="sxs-lookup"><span data-stu-id="d24c3-227">These features are just a few foundational pieces included with MRTK.</span></span> <span data-ttu-id="d24c3-228">Nelle esercitazioni successive aggiungerai contenuto alla scena per esplorare le funzionalità di HoloLens e MRTK.</span><span class="sxs-lookup"><span data-stu-id="d24c3-228">In the upcoming tutorials, you'll add content to your scene to explore the capabilities of HoloLens and the MRTK.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="d24c3-229">Esercitazione successiva: 3. Configurazione dei profili di MRTK</span><span class="sxs-lookup"><span data-stu-id="d24c3-229">Next Tutorial: 3. Configuring the MRTK profiles</span></span>](mr-learning-base-03.md)

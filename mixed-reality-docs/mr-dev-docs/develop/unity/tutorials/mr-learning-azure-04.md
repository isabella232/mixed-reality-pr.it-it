---
title: Integrazione di Ancoraggi nello spazio di Azure
description: In questo corso viene illustrato come implementare Ancoraggi nello spazio di Azure in un'applicazione HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens, hololens 2, ancoraggi nello spazio di Azure, servizi cloud di azure, visione personalizzata di azure, Windows 10
ms.localizationpriority: high
ms.openlocfilehash: ab5bcfe92e5de2149e844fc02164f5079e215142
ms.sourcegitcommit: 114c304a416bfe9d9b294c4adbb4c23cbe60ea4e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/15/2021
ms.locfileid: "114224284"
---
# <a name="4-integrating-azure-spatial-anchors"></a><span data-ttu-id="fd364-104">4. Integrazione di Ancoraggi nello spazio di Azure</span><span class="sxs-lookup"><span data-stu-id="fd364-104">4. Integrating Azure Spatial Anchors</span></span>

<span data-ttu-id="fd364-105">In questa esercitazione verrà spiegato come usare **Ancoraggi nello spazio di Azure**.</span><span class="sxs-lookup"><span data-stu-id="fd364-105">In this tutorial, you will learn how to use **Azure Spatial Anchors**.</span></span> <span data-ttu-id="fd364-106">Si archivierà la posizione di un **oggetto tracciato** come oggetto di Ancoraggi nello spazio di Azure.</span><span class="sxs-lookup"><span data-stu-id="fd364-106">You will store the location of a **Tracked Object** as an Azure Spatial Anchor.</span></span> <span data-ttu-id="fd364-107">Quando si esegue una query per l'ancoraggio, viene visualizzata una freccia che indica all'utente la posizione.</span><span class="sxs-lookup"><span data-stu-id="fd364-107">Once you query for the anchor, an arrow will appear to guide you toward the location.</span></span>

## <a name="objectives"></a><span data-ttu-id="fd364-108">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="fd364-108">Objectives</span></span>

* <span data-ttu-id="fd364-109">Acquisire le nozioni di base su Ancoraggi nello spazio di Azure.</span><span class="sxs-lookup"><span data-stu-id="fd364-109">Learn the basics of Azure Spatial Anchors.</span></span>
* <span data-ttu-id="fd364-110">Imparare a impostare la scena per l'uso di Ancoraggi nello spazio di Azure in questo progetto.</span><span class="sxs-lookup"><span data-stu-id="fd364-110">Learn how to set up the scene to use Azure Spatial Anchors in this project.</span></span>
* <span data-ttu-id="fd364-111">Scoprire come integrare le posizioni di archiviazione e query.</span><span class="sxs-lookup"><span data-stu-id="fd364-111">Learn how to integrate storing and querying locations.</span></span>

## <a name="understanding-azure-spatial-anchors"></a><span data-ttu-id="fd364-112">Informazioni su Ancoraggi nello spazio di Azure</span><span class="sxs-lookup"><span data-stu-id="fd364-112">Understanding Azure Spatial Anchors</span></span>

 <span data-ttu-id="fd364-113">**Ancoraggi nello spazio di Azure** fa parte della famiglia di Servizi cloud di Azure e viene utilizzato per salvare posizioni di ancoraggio.</span><span class="sxs-lookup"><span data-stu-id="fd364-113">**Azure Spatial Anchors** is part of the Azure Cloud Services family and is used to save anchor locations.</span></span> <span data-ttu-id="fd364-114">Le posizioni di ancoraggio salvate possono essere recuperate in base all'*ID di ancoraggio* dal cloud.</span><span class="sxs-lookup"><span data-stu-id="fd364-114">The saved anchor locations can be retrieved based on the *anchor ID* from the cloud.</span></span> <span data-ttu-id="fd364-115">Questa posizione di ancoraggio è condivisibile e accessibile da dispositivi multipiattaforma come i dispositivi HoloLens, iOS e Android.</span><span class="sxs-lookup"><span data-stu-id="fd364-115">This anchor location can be shared and accessed by multi-platform devices like HoloLens, iOS, and Android devices.</span></span>

<span data-ttu-id="fd364-116">Altre informazioni su [Ancoraggi nello spazio di Azure](/azure/spatial-anchors/overview).</span><span class="sxs-lookup"><span data-stu-id="fd364-116">Learn more about [Azure Spatial Anchors](/azure/spatial-anchors/overview).</span></span>

## <a name="preparing-azure-spatial-anchors"></a><span data-ttu-id="fd364-117">Preparazione di Ancoraggi nello spazio di Azure</span><span class="sxs-lookup"><span data-stu-id="fd364-117">Preparing Azure Spatial Anchors</span></span>

<span data-ttu-id="fd364-118">Prima di iniziare, è necessario creare una risorsa di ancoraggio nello spazio nel portale di Azure.</span><span class="sxs-lookup"><span data-stu-id="fd364-118">Before you can start, you have to create a spatial anchor resource in your Azure portal.</span></span>
<span data-ttu-id="fd364-119">Vedere come [creare una risorsa di Ancoraggi nello spazio](/azure/spatial-anchors/quickstarts/get-started-hololens#create-a-spatial-anchors-resource).</span><span class="sxs-lookup"><span data-stu-id="fd364-119">Learn how to make a [spatial anchor resource](/azure/spatial-anchors/quickstarts/get-started-hololens#create-a-spatial-anchors-resource).</span></span>

## <a name="preparing-the-scene"></a><span data-ttu-id="fd364-120">Preparazione della scena</span><span class="sxs-lookup"><span data-stu-id="fd364-120">Preparing the scene</span></span>

<span data-ttu-id="fd364-121">In questa sezione verrà illustrato come configurare la scena e apportare le modifiche necessarie.</span><span class="sxs-lookup"><span data-stu-id="fd364-121">In this section, you will learn how to configure the scene and make the necessary changes.</span></span>

<span data-ttu-id="fd364-122">Selezionare **l'oggetto MixedRealityToolkit** nella finestra Hierarchy **(Gerarchia)** e usare il pulsante Add **Component** (Aggiungi componente) nella finestra Inspector (Controllo) per aggiungere AR Anchor Manager (Script)</span><span class="sxs-lookup"><span data-stu-id="fd364-122">Select **MixedRealityToolkit** object in the Hierarchy window and use the **Add Component** button in the Inspector window to add the **AR Anchor Manager (Script)**</span></span>

![<span data-ttu-id="fd364-123">Oggetto Unity MixedRealityToolkit con componenti ar Anchor Manager aggiunti</span><span class="sxs-lookup"><span data-stu-id="fd364-123">Unity MixedRealityToolkit object with AR Anchor Manager components added</span></span> ](images/mr-learning-azure/tutorial4-section1-step1-1.png)

> [!NOTE]
> <span data-ttu-id="fd364-124">Quando si aggiunge il componente AR Anchor Manager (Script), il componente AR Session Origin (Script) viene aggiunto automaticamente perché è richiesto dal componente AR Anchor Manager (Script).</span><span class="sxs-lookup"><span data-stu-id="fd364-124">When you add the AR Anchor Manager (Script) component, the AR Session Origin (Script) component is automatically added because it is required by the AR Anchor Manager (Script) component.</span></span>

<span data-ttu-id="fd364-125">Nella finestra Project (Progetto) passa a **Assets > MRTK.Tutorials.AzureCloudServices > Prefabs > Manager**</span><span class="sxs-lookup"><span data-stu-id="fd364-125">In the Project window, navigate to the **Assets > MRTK.Tutorials.AzureCloudServices > Prefabs > Manager**</span></span>

![Unity con il prefab AnchorManager selezionato](images/mr-learning-azure/tutorial4-section1-step1-2.png)

<span data-ttu-id="fd364-127">Dalla cartella **Manager** trascinare e rilasciare il prefab **Anchor Manager** (Gestione ancoraggi) nella gerarchia della scena.</span><span class="sxs-lookup"><span data-stu-id="fd364-127">From the **Manager** folder, drag and drop the prefab **Anchor Manager** into the scene Hierarchy.</span></span>

<span data-ttu-id="fd364-128">Selezionare il GameObject **Anchor Manager** nella gerarchia e nella sezione Inspector (Controllo) si noterà **Spatial Anchor Manager** (Script).</span><span class="sxs-lookup"><span data-stu-id="fd364-128">Select **Anchor Manager** GameObject in the Hierarchy, and in the Inspector section, you will find **Spatial Anchor Manager** (Script).</span></span> <span data-ttu-id="fd364-129">Trovare il campo ID account chiave e aggiungere le credenziali che create nel prerequisito nella fase precedente.</span><span class="sxs-lookup"><span data-stu-id="fd364-129">Find account ID and key field and add the credentials which you had created in the prerequisite in the earlier stage.</span></span>

![Unity con il prefab AnchorManager appena aggiunto ancora selezionato](images/mr-learning-azure/tutorial4-section1-step2-1.png)

<span data-ttu-id="fd364-131">Ora trovare l'oggetto **Scene Controller** (Controllo scena) nella gerarchia della scena e selezionarlo.</span><span class="sxs-lookup"><span data-stu-id="fd364-131">Now find the **Scene Controller** object in your scene Hierarchy and select it.</span></span> <span data-ttu-id="fd364-132">Verrà visualizzata la finestra Inspector (Controllo) di **Scene Controller** (Controllo scena).</span><span class="sxs-lookup"><span data-stu-id="fd364-132">You will see the **Scene Controller** Inspector.</span></span>

![Unity con il componente script SceneController configurato](images/mr-learning-azure/tutorial4-section1-step3-1.png)

<span data-ttu-id="fd364-134">Si osserverà che il campo **Anchor Manager** (Gestione ancoraggi) nel componente **Scene Controller** (Controllo scena) è vuoto. Trascinare **Anchor Manager** (Gestione ancoraggi) da Hierarchy (Gerarchia) nella scena, rilasciarlo nel campo e salvare la scena.</span><span class="sxs-lookup"><span data-stu-id="fd364-134">You will observe that the **Anchor Manager** field in the **Scene Controller** component is empty, drag and drop the **Anchor Manager** from the Hierarchy in the scene into that field and save the scene.</span></span>

## <a name="build-and-deploy-the-app-to-your-hololens-2"></a><span data-ttu-id="fd364-135">Creare e distribuire l'app in un dispositivo HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="fd364-135">Build and Deploy the app to your HoloLens 2</span></span>

<span data-ttu-id="fd364-136">Non è possibile eseguire Ancoraggi nello spazio di Azure in Unity. Pertanto, per testare la funzionalità di questo servizio devi distribuire il progetto nel tuo dispositivo.</span><span class="sxs-lookup"><span data-stu-id="fd364-136">Azure Spatial Anchors can not run in Unity, so to test the Azure Spatial Anchors functionality, you need to deploy the project to your device.</span></span>

> [!TIP]
> <span data-ttu-id="fd364-137">Per rivedere la procedura di compilazione e distribuzione di un progetto Unity in HoloLens 2, fare riferimento alle istruzioni riportate in [Compilazione dell'applicazione nel dispositivo HoloLens 2]((mr-learning-base-02.md#building-and-deploying-to-your-hololens-2).</span><span class="sxs-lookup"><span data-stu-id="fd364-137">For a reminder on how to build and deploy your Unity project to HoloLens 2, you can refer to the [Building your application to your HoloLens 2]((mr-learning-base-02.md#building-and-deploying-to-your-hololens-2) instructions.</span></span>

## <a name="run-the-app-on-your-hololens-2-and-follow-the-in-app-instructions"></a><span data-ttu-id="fd364-138">Eseguire l'app in HoloLens 2 e seguire le istruzioni in-app</span><span class="sxs-lookup"><span data-stu-id="fd364-138">Run the app on your HoloLens 2 and follow the in-app instructions</span></span>

### <a name="create-an-anchor-to-store-a-location"></a><span data-ttu-id="fd364-139">Creare un ancoraggio per archiviare una posizione</span><span class="sxs-lookup"><span data-stu-id="fd364-139">Create an anchor to store a location</span></span>

<span data-ttu-id="fd364-140">In questa sezione verrà illustrato come salvare la posizione dell'oggetto.</span><span class="sxs-lookup"><span data-stu-id="fd364-140">In this section you will see how to save the object location.</span></span>

<span data-ttu-id="fd364-141">Eseguire l'applicazione e fare clic su **Set Object** (Imposta oggetto) nel menu principale dell'esperienza.</span><span class="sxs-lookup"><span data-stu-id="fd364-141">Run the application and click on **Set Object** in the main menu of the experience.</span></span>

<span data-ttu-id="fd364-142">Specificare il **nome** dell'oggetto da salvare e fare clic su **Set Object** (Imposta oggetto) per proseguire.</span><span class="sxs-lookup"><span data-stu-id="fd364-142">Give the **name** of the object you want to save and click on **Set Object** to continue.</span></span> <span data-ttu-id="fd364-143">Per aggiungere altre informazioni sull'oggetto, selezionare l'**immagine** e descrivere l'oggetto.</span><span class="sxs-lookup"><span data-stu-id="fd364-143">To add more information about the object, select the **image**, and describe the object.</span></span>

<span data-ttu-id="fd364-144">Per salvare la posizione, fare clic su **Save Location** (Salva posizione)</span><span class="sxs-lookup"><span data-stu-id="fd364-144">To save the location, click on **Save Location**</span></span>

<span data-ttu-id="fd364-145">Viene visualizzato un **puntatore di ancoraggio** che è possibile spostare e posizionare nella posizione da salvare.</span><span class="sxs-lookup"><span data-stu-id="fd364-145">You will see an **anchor pointer** that you can move and place on the location you want to save.</span></span> <span data-ttu-id="fd364-146">Successivamente, viene visualizzata una finestra popup di conferma.</span><span class="sxs-lookup"><span data-stu-id="fd364-146">After that, you will get a confirmation popup.</span></span> <span data-ttu-id="fd364-147">Se si vuole confermare e salvare la posizione, fare clic su **Yes** (Sì); in caso contrario, è possibile modificare la posizione facendo clic su **No** e selezionando nuovamente la posizione.</span><span class="sxs-lookup"><span data-stu-id="fd364-147">If you want to confirm and save the location, click on **Yes**; otherwise, you can change the location by clicking on **No** and selecting the location again.</span></span>

<span data-ttu-id="fd364-148">Dopo avere confermato la posizione facendo clic su **Yes** (Sì), la posizione e l'ID di ancoraggio verranno salvati nell'archiviazione cloud di Azure.</span><span class="sxs-lookup"><span data-stu-id="fd364-148">Once you confirm the location by clicking on **Yes**, the location and the Anchor ID will be saved in the Azure cloud storage.</span></span> <span data-ttu-id="fd364-149">Eseguito il salvataggio, verrà visualizzato il **tag dell'oggetto** nell'ancoraggio con il nome dell'oggetto.</span><span class="sxs-lookup"><span data-stu-id="fd364-149">Once it is saved, you will see the **Object tag**  in the anchor with the object's name.</span></span>

<span data-ttu-id="fd364-150">A questo punto, la posizione dell'oggetto è salvata correttamente.</span><span class="sxs-lookup"><span data-stu-id="fd364-150">Now the object location is saved successfully.</span></span>

### <a name="query-for-finding-an-anchor-location"></a><span data-ttu-id="fd364-151">Query per trovare una posizione di ancoraggio</span><span class="sxs-lookup"><span data-stu-id="fd364-151">Query for finding an anchor location</span></span>

<span data-ttu-id="fd364-152">Dopo avere salvato la posizione di ancoraggio, è possibile trovarla selezionando **Search Object** (Cerca oggetto) nel menu principale.</span><span class="sxs-lookup"><span data-stu-id="fd364-152">Once after you successfully saved the anchor location, now you can find the anchor location by selecting **Search Object** in the main menu.</span></span>

<span data-ttu-id="fd364-153">Facendo clic su **Search Object** (Cerca oggetto), viene visualizzata una nuova finestra in cui occorre specificare il nome dell'oggetto da cercare.</span><span class="sxs-lookup"><span data-stu-id="fd364-153">After clicking on **Search Object**, a new window will pop up in which you should give the name of the object you want to search.</span></span>

<span data-ttu-id="fd364-154">Immettere il nome dell'oggetto e fare clic su **Search Object** (Cerca oggetto).</span><span class="sxs-lookup"><span data-stu-id="fd364-154">Enter the name of the object and click on **Search Object**.</span></span> <span data-ttu-id="fd364-155">Se l'oggetto è stato salvato in precedenza ed è presente nel database, si otterrà la scheda dell'oggetto con tutti i dettagli che lo riguardano.</span><span class="sxs-lookup"><span data-stu-id="fd364-155">If the object is saved previously and is found in the database, you will get the object card with all the details of the object you would have saved earlier.</span></span>

<span data-ttu-id="fd364-156">A questo punto è possibile fare clic su **Show Location** (Mostra posizione) per trovare l'oggetto.</span><span class="sxs-lookup"><span data-stu-id="fd364-156">Now you can click on **Show Location** to find the object.</span></span> <span data-ttu-id="fd364-157">Dopo avere fatto clic su **Show Location** (Mostra percorso), il sistema eseguirà una query nella risorsa di archiviazione cloud alla ricerca dell'indirizzo dell'oggetto.</span><span class="sxs-lookup"><span data-stu-id="fd364-157">Once you click on **Show Location**, the system will query the object address from the cloud storage.</span></span>

<span data-ttu-id="fd364-158">Una volta recuperata a posizione, apparirà una **freccia** rivolta verso la posizione dell'oggetto.</span><span class="sxs-lookup"><span data-stu-id="fd364-158">After successfully retrieving the location, an **arrow** will direct you towards the location of the object.</span></span> <span data-ttu-id="fd364-159">Seguire il segno della freccia fino a trovare la posizione dell'oggetto.</span><span class="sxs-lookup"><span data-stu-id="fd364-159">Follow the arrow mark until you find the location of the object.</span></span>

<span data-ttu-id="fd364-160">Una volta trovato l'oggetto, nella parte superiore verrà visualizzato il nome dell'oggetto, il segno della freccia scomparirà e sarà possibile fare clic sul **tag dell'oggetto** per visualizzare i dettagli dell'oggetto.</span><span class="sxs-lookup"><span data-stu-id="fd364-160">Once you find the object, the object name will appear at the top, and the arrow mark will disappear, and now you can click on the **object tag** to see the details of the object.</span></span>

## <a name="congratulations"></a><span data-ttu-id="fd364-161">Lezione completata</span><span class="sxs-lookup"><span data-stu-id="fd364-161">Congratulations</span></span>

<span data-ttu-id="fd364-162">In questa esercitazione è stato illustrato come salvare e recuperare la posizione di un oggetto in HoloLens 2 con Ancoraggi nello spazio di Azure.</span><span class="sxs-lookup"><span data-stu-id="fd364-162">In this tutorial, you learned how Azure Spatial Anchors could save and retrieve the object location on Hololense 2.</span></span>

<span data-ttu-id="fd364-163">Nell'esercitazione finale si imparerà a usare il **Servizio Azure Bot** per aggiungere il linguaggio naturale come nuovo metodo di interazione per l'applicazione.</span><span class="sxs-lookup"><span data-stu-id="fd364-163">In the final tutorial, you will learn how to use the **Azure Bot Service** to add natural language as a new interaction method for our application.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="fd364-164">Esercitazione successiva: 5. Integrazione del servizio Azure Bot con LUIS</span><span class="sxs-lookup"><span data-stu-id="fd364-164">Next tutorial: 5. Integrating Azure Bot Service with LUIS</span></span>](mr-learning-azure-05.md)
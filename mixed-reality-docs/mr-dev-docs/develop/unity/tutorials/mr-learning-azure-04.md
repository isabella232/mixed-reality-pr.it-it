---
title: Integrazione di Ancoraggi nello spazio di Azure
description: In questo corso viene illustrato come implementare Ancoraggi nello spazio di Azure in un'applicazione HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens, hololens 2, ancoraggi nello spazio di Azure, servizi cloud di azure, visione personalizzata di azure, Windows 10
ms.localizationpriority: high
ms.openlocfilehash: 0837ebd9d34ba12d660098fc765824da3c561d07
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2021
ms.locfileid: "99590543"
---
# <a name="4-integrating-azure-spatial-anchors"></a><span data-ttu-id="2522f-104">4. Integrazione di Ancoraggi nello spazio di Azure</span><span class="sxs-lookup"><span data-stu-id="2522f-104">4. Integrating Azure Spatial Anchors</span></span>

<span data-ttu-id="2522f-105">In questa esercitazione verrà spiegato come usare **Ancoraggi nello spazio di Azure**.</span><span class="sxs-lookup"><span data-stu-id="2522f-105">In this tutorial, you will learn how to use **Azure Spatial Anchors**.</span></span> <span data-ttu-id="2522f-106">Si archivierà la posizione di un **oggetto tracciato** come oggetto di Ancoraggi nello spazio di Azure.</span><span class="sxs-lookup"><span data-stu-id="2522f-106">You will store the location of a **Tracked Object** as an Azure Spatial Anchor.</span></span> <span data-ttu-id="2522f-107">Quando si esegue una query per l'ancoraggio, viene visualizzata una freccia che indica all'utente la posizione.</span><span class="sxs-lookup"><span data-stu-id="2522f-107">Once you query for the anchor, an arrow will appear to guide you toward the location.</span></span>

## <a name="objectives"></a><span data-ttu-id="2522f-108">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="2522f-108">Objectives</span></span>

* <span data-ttu-id="2522f-109">Acquisire le nozioni di base su Ancoraggi nello spazio di Azure.</span><span class="sxs-lookup"><span data-stu-id="2522f-109">Learn the basics of Azure Spatial Anchors.</span></span>
* <span data-ttu-id="2522f-110">Imparare a impostare la scena per l'uso di Ancoraggi nello spazio di Azure in questo progetto.</span><span class="sxs-lookup"><span data-stu-id="2522f-110">Learn how to set up the scene to use Azure Spatial Anchors in this project.</span></span>
* <span data-ttu-id="2522f-111">Scoprire come integrare le posizioni di archiviazione e query.</span><span class="sxs-lookup"><span data-stu-id="2522f-111">Learn how to integrate storing and querying locations.</span></span>

## <a name="understanding-azure-spatial-anchors"></a><span data-ttu-id="2522f-112">Informazioni su Ancoraggi nello spazio di Azure</span><span class="sxs-lookup"><span data-stu-id="2522f-112">Understanding Azure Spatial Anchors</span></span>

 <span data-ttu-id="2522f-113">**Ancoraggi nello spazio di Azure** fa parte della famiglia di Servizi cloud di Azure e viene utilizzato per salvare posizioni di ancoraggio.</span><span class="sxs-lookup"><span data-stu-id="2522f-113">**Azure Spatial Anchors** is part of the Azure Cloud Services family and is used to save anchor locations.</span></span> <span data-ttu-id="2522f-114">Le posizioni di ancoraggio salvate possono essere recuperate in base all'*ID di ancoraggio* dal cloud.</span><span class="sxs-lookup"><span data-stu-id="2522f-114">The saved anchor locations can be retrieved based on the *anchor ID* from the cloud.</span></span> <span data-ttu-id="2522f-115">Questa posizione di ancoraggio è condivisibile e accessibile da dispositivi multipiattaforma come i dispositivi HoloLens, iOS e Android.</span><span class="sxs-lookup"><span data-stu-id="2522f-115">This anchor location can be shared and accessed by multi-platform devices like HoloLens, iOS, and Android devices.</span></span>

<span data-ttu-id="2522f-116">Altre informazioni su [Ancoraggi nello spazio di Azure](/azure/spatial-anchors/overview).</span><span class="sxs-lookup"><span data-stu-id="2522f-116">Learn more about [Azure Spatial Anchors](/azure/spatial-anchors/overview).</span></span>

## <a name="preparing-azure-spatial-anchors"></a><span data-ttu-id="2522f-117">Preparazione di Ancoraggi nello spazio di Azure</span><span class="sxs-lookup"><span data-stu-id="2522f-117">Preparing Azure Spatial Anchors</span></span>

<span data-ttu-id="2522f-118">Prima di iniziare, è necessario creare una risorsa di ancoraggio nello spazio nel portale di Azure.</span><span class="sxs-lookup"><span data-stu-id="2522f-118">Before you can start, you have to create a spatial anchor resource in your Azure portal.</span></span>
<span data-ttu-id="2522f-119">Vedere come [creare una risorsa di Ancoraggi nello spazio](/azure/spatial-anchors/quickstarts/get-started-hololens#create-a-spatial-anchors-resource).</span><span class="sxs-lookup"><span data-stu-id="2522f-119">Learn how to make a [spatial anchor resource](/azure/spatial-anchors/quickstarts/get-started-hololens#create-a-spatial-anchors-resource).</span></span>

## <a name="preparing-the-scene"></a><span data-ttu-id="2522f-120">Preparazione della scena</span><span class="sxs-lookup"><span data-stu-id="2522f-120">Preparing the scene</span></span>

<span data-ttu-id="2522f-121">In questa sezione verrà illustrato come configurare la scena e apportare le modifiche necessarie.</span><span class="sxs-lookup"><span data-stu-id="2522f-121">In this section, you will learn how to configure the scene and make the necessary changes.</span></span>

<span data-ttu-id="2522f-122">Nella finestra Project (Progetto) passa a **Assets > MRTK.Tutorials.AzureCloudServices > Prefabs > Manager**</span><span class="sxs-lookup"><span data-stu-id="2522f-122">In the Project window, navigate to the **Assets > MRTK.Tutorials.AzureCloudServices > Prefabs > Manager**</span></span>

![Unity con il prefab AnchorManager selezionato](images/mr-learning-azure/tutorial4-section1-step1-1.png)

<span data-ttu-id="2522f-124">Dalla cartella **Manager** trascinare e rilasciare il prefab **Anchor Manager** (Gestione ancoraggi) nella gerarchia della scena.</span><span class="sxs-lookup"><span data-stu-id="2522f-124">From the **Manager** folder, drag and drop the prefab **Anchor Manager** into the scene Hierarchy.</span></span>

<span data-ttu-id="2522f-125">Selezionare il GameObject **Anchor Manager** nella gerarchia e nella sezione Inspector (Controllo) si noterà **Spatial Anchor Manager** (Script).</span><span class="sxs-lookup"><span data-stu-id="2522f-125">Select **Anchor Manager** GameObject in the Hierarchy, and in the Inspector section, you will find **Spatial Anchor Manager** (Script).</span></span> <span data-ttu-id="2522f-126">Trovare il campo ID account chiave e aggiungere le credenziali che create nel prerequisito nella fase precedente.</span><span class="sxs-lookup"><span data-stu-id="2522f-126">Find account ID and key field and add the credentials which you had created in the prerequisite in the earlier stage.</span></span>

![Unity con il prefab AnchorManager appena aggiunto ancora selezionato](images/mr-learning-azure/tutorial4-section1-step2-1.png)

<span data-ttu-id="2522f-128">Ora trovare l'oggetto **Scene Controller** (Controllo scena) nella gerarchia della scena e selezionarlo.</span><span class="sxs-lookup"><span data-stu-id="2522f-128">Now find the **Scene Controller** object in your scene Hierarchy and select it.</span></span> <span data-ttu-id="2522f-129">Verrà visualizzata la finestra Inspector (Controllo) di **Scene Controller** (Controllo scena).</span><span class="sxs-lookup"><span data-stu-id="2522f-129">You will see the **Scene Controller** Inspector.</span></span>

![Unity con il componente script SceneController configurato](images/mr-learning-azure/tutorial4-section1-step3-1.png)

<span data-ttu-id="2522f-131">Si osserverà che il campo **Anchor Manager** (Gestione ancoraggi) nel componente **Scene Controller** (Controllo scena) è vuoto. Trascinare **Anchor Manager** (Gestione ancoraggi) da Hierarchy (Gerarchia) nella scena, rilasciarlo nel campo e salvare la scena.</span><span class="sxs-lookup"><span data-stu-id="2522f-131">You will observe that the **Anchor Manager** field in the **Scene Controller** component is empty, drag and drop the **Anchor Manager** from the Hierarchy in the scene into that field and save the scene.</span></span>

## <a name="build-and-deploy-the-app-to-your-hololens-2"></a><span data-ttu-id="2522f-132">Creare e distribuire l'app in un dispositivo HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="2522f-132">Build and Deploy the app to your HoloLens 2</span></span>

<span data-ttu-id="2522f-133">Non è possibile eseguire Ancoraggi nello spazio di Azure in Unity. Pertanto, per testare la funzionalità di questo servizio devi distribuire il progetto nel tuo dispositivo.</span><span class="sxs-lookup"><span data-stu-id="2522f-133">Azure Spatial Anchors can not run in Unity, so to test the Azure Spatial Anchors functionality, you need to deploy the project to your device.</span></span>

> [!TIP]
> <span data-ttu-id="2522f-134">Per rivedere la procedura di compilazione e distribuzione di un progetto Unity in HoloLens 2, fare riferimento alle istruzioni riportate in [Compilazione dell'applicazione nel dispositivo HoloLens 2]((mr-learning-base-02.md#building-and-deploying-to-your-hololens-2).</span><span class="sxs-lookup"><span data-stu-id="2522f-134">For a reminder on how to build and deploy your Unity project to HoloLens 2, you can refer to the [Building your application to your HoloLens 2]((mr-learning-base-02.md#building-and-deploying-to-your-hololens-2) instructions.</span></span>

## <a name="run-the-app-on-your-hololens-2-and-follow-the-in-app-instructions"></a><span data-ttu-id="2522f-135">Eseguire l'app in HoloLens 2 e seguire le istruzioni in-app</span><span class="sxs-lookup"><span data-stu-id="2522f-135">Run the app on your HoloLens 2 and follow the in-app instructions</span></span>

### <a name="create-an-anchor-to-store-a-location"></a><span data-ttu-id="2522f-136">Creare un ancoraggio per archiviare una posizione</span><span class="sxs-lookup"><span data-stu-id="2522f-136">Create an anchor to store a location</span></span>

<span data-ttu-id="2522f-137">In questa sezione verrà illustrato come salvare la posizione dell'oggetto.</span><span class="sxs-lookup"><span data-stu-id="2522f-137">In this section you will see how to save the object location.</span></span>

<span data-ttu-id="2522f-138">Eseguire l'applicazione e fare clic su **Set Object** (Imposta oggetto) nel menu principale dell'esperienza.</span><span class="sxs-lookup"><span data-stu-id="2522f-138">Run the application and click on **Set Object** in the main menu of the experience.</span></span>

<span data-ttu-id="2522f-139">Specificare il **nome** dell'oggetto da salvare e fare clic su **Set Object** (Imposta oggetto) per proseguire.</span><span class="sxs-lookup"><span data-stu-id="2522f-139">Give the **name** of the object you want to save and click on **Set Object** to continue.</span></span> <span data-ttu-id="2522f-140">Per aggiungere altre informazioni sull'oggetto, selezionare l'**immagine** e descrivere l'oggetto.</span><span class="sxs-lookup"><span data-stu-id="2522f-140">To add more information about the object, select the **image**, and describe the object.</span></span>

<span data-ttu-id="2522f-141">Per salvare la posizione, fare clic su **Save Location** (Salva posizione)</span><span class="sxs-lookup"><span data-stu-id="2522f-141">To save the location, click on **Save Location**</span></span>

<span data-ttu-id="2522f-142">Viene visualizzato un **puntatore di ancoraggio** che è possibile spostare e posizionare nella posizione da salvare.</span><span class="sxs-lookup"><span data-stu-id="2522f-142">You will see an **anchor pointer** that you can move and place on the location you want to save.</span></span> <span data-ttu-id="2522f-143">Successivamente, viene visualizzata una finestra popup di conferma.</span><span class="sxs-lookup"><span data-stu-id="2522f-143">After that, you will get a confirmation popup.</span></span> <span data-ttu-id="2522f-144">Se si vuole confermare e salvare la posizione, fare clic su **Yes** (Sì); in caso contrario, è possibile modificare la posizione facendo clic su **No** e selezionando nuovamente la posizione.</span><span class="sxs-lookup"><span data-stu-id="2522f-144">If you want to confirm and save the location, click on **Yes**; otherwise, you can change the location by clicking on **No** and selecting the location again.</span></span>

<span data-ttu-id="2522f-145">Dopo avere confermato la posizione facendo clic su **Yes** (Sì), la posizione e l'ID di ancoraggio verranno salvati nell'archiviazione cloud di Azure.</span><span class="sxs-lookup"><span data-stu-id="2522f-145">Once you confirm the location by clicking on **Yes**, the location and the Anchor ID will be saved in the Azure cloud storage.</span></span> <span data-ttu-id="2522f-146">Eseguito il salvataggio, verrà visualizzato il **tag dell'oggetto** nell'ancoraggio con il nome dell'oggetto.</span><span class="sxs-lookup"><span data-stu-id="2522f-146">Once it is saved, you will see the **Object tag**  in the anchor with the object's name.</span></span>

<span data-ttu-id="2522f-147">A questo punto, la posizione dell'oggetto è salvata correttamente.</span><span class="sxs-lookup"><span data-stu-id="2522f-147">Now the object location is saved successfully.</span></span>

### <a name="query-for-finding-an-anchor-location"></a><span data-ttu-id="2522f-148">Query per trovare una posizione di ancoraggio</span><span class="sxs-lookup"><span data-stu-id="2522f-148">Query for finding an anchor location</span></span>

<span data-ttu-id="2522f-149">Dopo avere salvato la posizione di ancoraggio, è possibile trovarla selezionando **Search Object** (Cerca oggetto) nel menu principale.</span><span class="sxs-lookup"><span data-stu-id="2522f-149">Once after you successfully saved the anchor location, now you can find the anchor location by selecting **Search Object** in the main menu.</span></span>

<span data-ttu-id="2522f-150">Facendo clic su **Search Object** (Cerca oggetto), viene visualizzata una nuova finestra in cui occorre specificare il nome dell'oggetto da cercare.</span><span class="sxs-lookup"><span data-stu-id="2522f-150">After clicking on **Search Object**, a new window will pop up in which you should give the name of the object you want to search.</span></span>

<span data-ttu-id="2522f-151">Immettere il nome dell'oggetto e fare clic su **Search Object** (Cerca oggetto).</span><span class="sxs-lookup"><span data-stu-id="2522f-151">Enter the name of the object and click on **Search Object**.</span></span> <span data-ttu-id="2522f-152">Se l'oggetto è stato salvato in precedenza ed è presente nel database, si otterrà la scheda dell'oggetto con tutti i dettagli che lo riguardano.</span><span class="sxs-lookup"><span data-stu-id="2522f-152">If the object is saved previously and is found in the database, you will get the object card with all the details of the object you would have saved earlier.</span></span>

<span data-ttu-id="2522f-153">A questo punto è possibile fare clic su **Show Location** (Mostra posizione) per trovare l'oggetto.</span><span class="sxs-lookup"><span data-stu-id="2522f-153">Now you can click on **Show Location** to find the object.</span></span> <span data-ttu-id="2522f-154">Dopo avere fatto clic su **Show Location** (Mostra percorso), il sistema eseguirà una query nella risorsa di archiviazione cloud alla ricerca dell'indirizzo dell'oggetto.</span><span class="sxs-lookup"><span data-stu-id="2522f-154">Once you click on **Show Location**, the system will query the object address from the cloud storage.</span></span>

<span data-ttu-id="2522f-155">Una volta recuperata a posizione, apparirà una **freccia** rivolta verso la posizione dell'oggetto.</span><span class="sxs-lookup"><span data-stu-id="2522f-155">After successfully retrieving the location, an **arrow** will direct you towards the location of the object.</span></span> <span data-ttu-id="2522f-156">Seguire il segno della freccia fino a trovare la posizione dell'oggetto.</span><span class="sxs-lookup"><span data-stu-id="2522f-156">Follow the arrow mark until you find the location of the object.</span></span>

<span data-ttu-id="2522f-157">Una volta trovato l'oggetto, nella parte superiore verrà visualizzato il nome dell'oggetto, il segno della freccia scomparirà e sarà possibile fare clic sul **tag dell'oggetto** per visualizzare i dettagli dell'oggetto.</span><span class="sxs-lookup"><span data-stu-id="2522f-157">Once you find the object, the object name will appear at the top, and the arrow mark will disappear, and now you can click on the **object tag** to see the details of the object.</span></span>

## <a name="congratulations"></a><span data-ttu-id="2522f-158">Lezione completata</span><span class="sxs-lookup"><span data-stu-id="2522f-158">Congratulations</span></span>

<span data-ttu-id="2522f-159">In questa esercitazione è stato illustrato come salvare e recuperare la posizione di un oggetto in HoloLens 2 con Ancoraggi nello spazio di Azure.</span><span class="sxs-lookup"><span data-stu-id="2522f-159">In this tutorial, you learned how Azure Spatial Anchors could save and retrieve the object location on Hololense 2.</span></span>

<span data-ttu-id="2522f-160">Nell'esercitazione finale si imparerà a usare il **Servizio Azure Bot** per aggiungere il linguaggio naturale come nuovo metodo di interazione per l'applicazione.</span><span class="sxs-lookup"><span data-stu-id="2522f-160">In the final tutorial, you will learn how to use the **Azure Bot Service** to add natural language as a new interaction method for our application.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="2522f-161">Esercitazione successiva: 5. Integrazione del servizio Azure Bot con LUIS</span><span class="sxs-lookup"><span data-stu-id="2522f-161">Next tutorial: 5. Integrating Azure Bot Service with LUIS</span></span>](mr-learning-azure-05.md)
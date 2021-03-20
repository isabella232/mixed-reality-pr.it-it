---
title: Integrazione di Visione personalizzata di Azure
description: In questo corso viene illustrato come implementare Visione personalizzata di Azure in un'applicazione di realtà mista per HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens, hololens 2, visione personalizzata di azure, servizi cognitivi di azure, servizi cloud di azure, Windows 10
ms.localizationpriority: high
ms.openlocfilehash: cb391aa2cdb7944234cdeede7dd05825c008d0d8
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2021
ms.locfileid: "99590573"
---
# <a name="3-integrating-azure-custom-vision"></a><span data-ttu-id="4cb09-104">3. Integrazione di Visione personalizzata di Azure</span><span class="sxs-lookup"><span data-stu-id="4cb09-104">3. Integrating Azure Custom Vision</span></span>

<span data-ttu-id="4cb09-105">In questa esercitazione si imparerà a usare **Visione personalizzata di Azure**. Si caricherà un set di foto per associarle a un *oggetto tracciato*, caricarle nel servizio **Visione personalizzata** e avviare il processo di training.</span><span class="sxs-lookup"><span data-stu-id="4cb09-105">In this tutorial, you will learn how to use **Azure Custom Vision**.You will upload a set of photos to associate it with a *Tracked Object*, upload them to the **Custom Vision** service and start the training process.</span></span> <span data-ttu-id="4cb09-106">Si userà quindi il servizio per rilevare l'*oggetto tracciato* acquisendo foto dal feed della webcam.</span><span class="sxs-lookup"><span data-stu-id="4cb09-106">Then you will use the service to detect the *Tracked Object* by capturing photos from the webcam feed.</span></span>

## <a name="objectives"></a><span data-ttu-id="4cb09-107">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="4cb09-107">Objectives</span></span>

* <span data-ttu-id="4cb09-108">Acquisire nozioni di base su Visione personalizzata di Azure</span><span class="sxs-lookup"><span data-stu-id="4cb09-108">Learn the basics about Azure Custom Vision</span></span>
* <span data-ttu-id="4cb09-109">Imparare a impostare la scena per usare il servizio Visione personalizzata di Azure nel progetto</span><span class="sxs-lookup"><span data-stu-id="4cb09-109">Learn how to setup the scene to use Custom Vision in this project</span></span>
* <span data-ttu-id="4cb09-110">Scoprire come caricare, eseguire il training e rilevare le immagini</span><span class="sxs-lookup"><span data-stu-id="4cb09-110">Learn how to integrate upload, train and detect images</span></span>

## <a name="understanding-azure-custom-vision"></a><span data-ttu-id="4cb09-111">Informazioni su Visione personalizzata di Azure</span><span class="sxs-lookup"><span data-stu-id="4cb09-111">Understanding Azure Custom Vision</span></span>

<span data-ttu-id="4cb09-112">**Visione personalizzata di Azure** fa parte della famiglia di **Servizi cognitivi** e viene usato per il training dei classificatori di immagini.</span><span class="sxs-lookup"><span data-stu-id="4cb09-112">**Azure Custom Vision** is part of the **Cognitive Services** family and is used to train image classifiers.</span></span> <span data-ttu-id="4cb09-113">Il classificatore di immagini è un servizio di intelligenza artificiale che usa il modello con training per applicare tag corrispondenti.</span><span class="sxs-lookup"><span data-stu-id="4cb09-113">The image classifier is an AI service that uses the trained model to apply matching tags.</span></span> <span data-ttu-id="4cb09-114">Questa funzionalità di classificazione verrà usata dall'applicazione per rilevare gli *oggetti tracciati*.</span><span class="sxs-lookup"><span data-stu-id="4cb09-114">This classification feature will be used by our application to detect *Tracked Objects*.</span></span>

<span data-ttu-id="4cb09-115">Altre informazioni su [Visione personalizzata di Azure](/azure/cognitive-services/custom-vision-service/home).</span><span class="sxs-lookup"><span data-stu-id="4cb09-115">Learn more about [Azure Custom Vision](/azure/cognitive-services/custom-vision-service/home).</span></span>

## <a name="preparing-azure-custom-vision"></a><span data-ttu-id="4cb09-116">Preparazione di Visione personalizzata di Azure</span><span class="sxs-lookup"><span data-stu-id="4cb09-116">Preparing Azure Custom Vision</span></span>

<span data-ttu-id="4cb09-117">Prima di iniziare, è necessario creare un progetto di visione personalizzata. Il modo più rapido consiste nell'usare il portale Web.</span><span class="sxs-lookup"><span data-stu-id="4cb09-117">Before you can start, you have to create a custom vision project, the fastest way is by using the web portal.</span></span>

<span data-ttu-id="4cb09-118">Seguire questa [esercitazione introduttiva](/azure/cognitive-services/custom-vision-service/getting-started-build-a-classifier#choose-training-images) per configurare l'account e il progetto fino alla sezione *Caricare e taggare le immagini*.</span><span class="sxs-lookup"><span data-stu-id="4cb09-118">Follow this [quickstart tutorial](/azure/cognitive-services/custom-vision-service/getting-started-build-a-classifier#choose-training-images) to setup your account and project until section *Upload and tag images*.</span></span>

> [!WARNING]
> <span data-ttu-id="4cb09-119">Per eseguire il training di un modello, è necessario disporre di almeno 2 tag e 5 immagini per ogni tag.</span><span class="sxs-lookup"><span data-stu-id="4cb09-119">To train a model you need to have at least 2 tags and 5 images per tag.</span></span> <span data-ttu-id="4cb09-120">Per usare questa applicazione, è necessario creare almeno un tag con 5 immagini, affinché il processo di training non abbia esito negativo in un secondo momento.</span><span class="sxs-lookup"><span data-stu-id="4cb09-120">To use this application you should at least create one tag with 5 images, so that the training process later won't fail.</span></span>

## <a name="preparing-the-scene"></a><span data-ttu-id="4cb09-121">Preparazione della scena</span><span class="sxs-lookup"><span data-stu-id="4cb09-121">Preparing the scene</span></span>

<span data-ttu-id="4cb09-122">Nella finestra Project (Progetto) passare alla cartella **Assets** (Asset)  > **MRTK.Tutorials.AzureCloudServices** > **Prefabs** (Prefab)  > **Manager**.</span><span class="sxs-lookup"><span data-stu-id="4cb09-122">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.AzureCloudServices** > **Prefabs** > **Manager** folder.</span></span>

![Unity con la finestra Project che mostra il percorso del prefab ObjectDetectionManager](images/mr-learning-azure/tutorial3-section4-step1-1.png)

<span data-ttu-id="4cb09-124">Da qui, trascinare il prefab **ObjectDetectionManager** nella gerarchia della scena.</span><span class="sxs-lookup"><span data-stu-id="4cb09-124">From there drag the prefab **ObjectDetectionManager** into the scene Hierarchy.</span></span>

![Unity con i campi di configurazione del componente script ObjectDetectionManager visualizzati in Inspector](images/mr-learning-azure/tutorial3-section4-step1-2.png)

<span data-ttu-id="4cb09-126">Nella finestra Hierarchy (Gerarchia) individuare l'oggetto **ObjectDetectionManager** e selezionarlo.</span><span class="sxs-lookup"><span data-stu-id="4cb09-126">In the Hierarchy window locate the **ObjectDetectionManager** object and select it.</span></span>
<span data-ttu-id="4cb09-127">La prefabbricazione **ObjectDetectionManager** contiene il componente **ObjectDetectionManager (script)** e, come si può notare dalla finestra di controllo, dipende dalle impostazioni di Azure e del progetto.</span><span class="sxs-lookup"><span data-stu-id="4cb09-127">The **ObjectDetectionManager** prefab contains the **ObjectDetectionManager (script)** component and as you can see from the Inspector window it depends on Azure settings and Project settings.</span></span>

## <a name="retrieving-azure-api-resource-credentials"></a><span data-ttu-id="4cb09-128">Recupero delle credenziali delle risorse API di Azure</span><span class="sxs-lookup"><span data-stu-id="4cb09-128">Retrieving Azure api resource credentials</span></span>

<span data-ttu-id="4cb09-129">Le credenziali necessarie per le impostazioni **ObjectDetectionManager (script)** possono essere recuperate dal portale di Azure e dal portale del servizio Visione personalizzata.</span><span class="sxs-lookup"><span data-stu-id="4cb09-129">The necessary credentials for the **ObjectDetectionManager (script)** settings can be retrieve from the Azure Portal and the custom vision portal.</span></span>

### <a name="retrieving-azure-settings-credentials"></a><span data-ttu-id="4cb09-130">Recupero delle credenziali delle impostazioni di Azure</span><span class="sxs-lookup"><span data-stu-id="4cb09-130">Retrieving Azure Settings credentials</span></span>

<span data-ttu-id="4cb09-131">Trovare e individuare la risorsa visione personalizzata di tipo **Servizi cognitivi** creati nella sezione *preparazione della scena* di questa esercitazione (selezionare il nome delle risorse della visione personalizzata seguito da *-stima* ).</span><span class="sxs-lookup"><span data-stu-id="4cb09-131">Find and locate the custom vision resource of type **Cognitive Services** you have created in the *Preparing the scene* section of this tutorial (select custom vision resources name followed by *-Prediction* ).</span></span> <span data-ttu-id="4cb09-132">Fare clic su *Panoramica* o *chiavi ed endpoint* per recuperare le credenziali necessarie.</span><span class="sxs-lookup"><span data-stu-id="4cb09-132">There click on *Overview* or *Keys and Endpoint* to retrieve the necessary credentials.</span></span>

### <a name="retrieving-project-settings-credentials"></a><span data-ttu-id="4cb09-133">Recupero delle credenziali delle impostazioni di progetto</span><span class="sxs-lookup"><span data-stu-id="4cb09-133">Retrieving Project Settings credentials</span></span>

<span data-ttu-id="4cb09-134">Nel dashboard [Visione personalizzata](https://www.customvision.ai/projects) aprire il progetto creato per questa esercitazione e fare clic sull'icona a forma di ingranaggio nell'angolo in alto a destra della pagina per aprire la pagina delle impostazioni.</span><span class="sxs-lookup"><span data-stu-id="4cb09-134">In the [custom vision](https://www.customvision.ai/projects) dashboard, open the project you have created for this tutorial and click on the top right corner of the page on the gear icon to open the settings page.</span></span> <span data-ttu-id="4cb09-135">Qui nella sezione *Resources* (Risorse) a destra sono riportate le credenziali necessarie.</span><span class="sxs-lookup"><span data-stu-id="4cb09-135">Here on the right hand *Resources* section you will find the necessary credentials.</span></span>

<span data-ttu-id="4cb09-136">Dopo avere configurato correttamente **ObjectDetectionManager (script)** , trovare l'oggetto **SceneController** nella gerarchia della scena e selezionarlo.</span><span class="sxs-lookup"><span data-stu-id="4cb09-136">Now with the **ObjectDetectionManager (script)** setup correctly, find the **SceneController** object in your scene Hierarchy and select it.</span></span>

![Unity con i campi di configurazione del componente script SceneController visualizzati in Inspector](images/mr-learning-azure/tutorial3-section4-step1-3.png)

<span data-ttu-id="4cb09-138">Si noterà che il campo *Object Detection Manager* (Gestione rilevamento oggetti) nel componente **SceneController** è vuoto; trascinare **ObjectDetectionManager** dalla gerarchia a quel campo e salvare la scena.</span><span class="sxs-lookup"><span data-stu-id="4cb09-138">You see *Object Detection Manager* field in the **SceneController** component is empty, drag the **ObjectDetectionManager** from the Hierarchy into that field and save the scene.</span></span>

![Unity con il componente script SceneController configurato](images/mr-learning-azure/tutorial3-section4-step1-4.png)

## <a name="take-and-upload-images"></a><span data-ttu-id="4cb09-140">Acquisire e caricare immagini</span><span class="sxs-lookup"><span data-stu-id="4cb09-140">Take and upload images</span></span>

<span data-ttu-id="4cb09-141">Eseguire la scena e fare clic su **Set Object** (Imposta oggetto), quindi digitare il nome di uno degli **oggetti tracciati** creati nella [lezione precedente](mr-learning-azure-02.md).</span><span class="sxs-lookup"><span data-stu-id="4cb09-141">Run the scene and click on **Set Object**, type in the name for one of the **Tracked Objects** you have created in the [previous lesson](mr-learning-azure-02.md).</span></span> <span data-ttu-id="4cb09-142">A questo punto, fare clic sul pulsante **Computer Vision** (Visione artificiale) nella parte inferiore della **Object Card** (Scheda oggetto).</span><span class="sxs-lookup"><span data-stu-id="4cb09-142">Now click on **Computer Vision** button you can find at the bottom of the **Object Card**.</span></span>

<span data-ttu-id="4cb09-143">Verrà aperta una nuova finestra in cui è necessario scattare sei foto per eseguire il training del modello per il riconoscimento delle immagini.</span><span class="sxs-lookup"><span data-stu-id="4cb09-143">A new window will open where you have to take six photos to train the model for image recognition.</span></span> <span data-ttu-id="4cb09-144">Fare clic sul pulsante **Camera** (Fotocamera) ed eseguire un AirTap quando si osserva l'oggetto da tracciare e ripetere sei volte.</span><span class="sxs-lookup"><span data-stu-id="4cb09-144">Click on the **Camera** button and perform an AirTap when you look on the object you like to track, do this six times.</span></span>

> [!TIP]
> <span data-ttu-id="4cb09-145">Per migliorare il training del modello, provare ad acquisire ogni immagine da diverse angolazioni e in condizioni di illuminazione.</span><span class="sxs-lookup"><span data-stu-id="4cb09-145">To improve the model training try to take each image from different angles and lighting conditions.</span></span>

<span data-ttu-id="4cb09-146">Quando le immagini sono sufficienti, fare clic sul pulsante **Train** (Esegui training) per avviare il processo di training del modello nel cloud.</span><span class="sxs-lookup"><span data-stu-id="4cb09-146">Once you have enough images click on the **Train** button to start the model training process in the cloud.</span></span> <span data-ttu-id="4cb09-147">L'attivazione del training caricherà tutte le immagini e quindi inizierà il training. Questa operazione può richiedere un minuto o più.</span><span class="sxs-lookup"><span data-stu-id="4cb09-147">Activating the training will upload all images and then start the training, this can take up to a minute or more.</span></span> <span data-ttu-id="4cb09-148">Un messaggio all'interno del menu indica lo stato di avanzamento e, quando risulta completato, è possibile arrestare l'applicazione</span><span class="sxs-lookup"><span data-stu-id="4cb09-148">A message inside the menu indicates the current progress and once it indicates the completion you can stop the application</span></span>

> [!TIP]
> <span data-ttu-id="4cb09-149">**ObjectDetectionManager (script)** carica direttamente le immagini acquisite nel servizio Visione personalizzata.</span><span class="sxs-lookup"><span data-stu-id="4cb09-149">The **ObjectDetectionManager (script)** directly uploads taken images into the Custom Vision service.</span></span> <span data-ttu-id="4cb09-150">In alternativa, l'API di visione personalizzata accetta gli URL delle immagini; come esercizio, è possibile modificare **ObjectDetectionManager (script)** per caricare le immagini in un archivio BLOB.</span><span class="sxs-lookup"><span data-stu-id="4cb09-150">As an alternative the custom vision API accepts URLs to the images, as an exercise you can modify the **ObjectDetectionManager (script)** to upload the images to a Blob storage instead.</span></span>

## <a name="detect-objects"></a><span data-ttu-id="4cb09-151">Rilevare oggetti</span><span class="sxs-lookup"><span data-stu-id="4cb09-151">Detect objects</span></span>

<span data-ttu-id="4cb09-152">Prima di rilevare gli oggetti, è necessario modificare la chiave API presente in  **ObjectDetectionManager (script)** in Impostazioni progetto già assegnate con la chiave visiva personalizzata.</span><span class="sxs-lookup"><span data-stu-id="4cb09-152">Before detecting the objects we have to change the Api key present in  **ObjectDetectionManager (script)** under project settings that already assign with custom vision key.</span></span>

<span data-ttu-id="4cb09-153">Trovare e individuare la risorsa visione personalizzata in portale di Azure. Fare clic su *chiavi ed endpoint* per recuperare la chiave API e sostituire con la chiave API precedente in Impostazioni progetto.</span><span class="sxs-lookup"><span data-stu-id="4cb09-153">Find and locate the custom vision resource in Azure portal.There click on *Keys and Endpoint* to retrieve the Api key and replace with old Api key under project settings.</span></span>

<span data-ttu-id="4cb09-154">A questo punto è possibile testare il modello con training, eseguire l'applicazione e dal *menu principale* fare clic su **Search Object** (Cerca oggetto) e digitare il nome dell'**oggetto tracciato** in questione.</span><span class="sxs-lookup"><span data-stu-id="4cb09-154">You can now put the trained model to the test, run the application and from the *main menu* click on **Search Object** and type the name of the **Tracked Object** in question.</span></span> <span data-ttu-id="4cb09-155">Quando viene visualizzata la **Object Card** (Scheda oggetto), fare clic sul pulsante **Custom Vision** (Visione personalizzata).</span><span class="sxs-lookup"><span data-stu-id="4cb09-155">The **Object Card** will appear and click on the **Custom Vision** button.</span></span> <span data-ttu-id="4cb09-156">Da qui, **ObjectDetectionManager** inizierà ad acquisire immagini in background dalla fotocamera e lo stato di avanzamento verrà indicato nel menu.</span><span class="sxs-lookup"><span data-stu-id="4cb09-156">From here the **ObjectDetectionManager** will start taking image captures in the background from the camera and the progress will be indicated on the menu.</span></span> <span data-ttu-id="4cb09-157">Puntare la fotocamera sull'oggetto usato per eseguire il training del modello. Si noterà che dopo un breve periodo di tempo rileverà l'oggetto.</span><span class="sxs-lookup"><span data-stu-id="4cb09-157">Point the camera to the object you used to train the model and you will see that after a short while it will detect the object.</span></span>

## <a name="congratulations"></a><span data-ttu-id="4cb09-158">Lezione completata</span><span class="sxs-lookup"><span data-stu-id="4cb09-158">Congratulations</span></span>

<span data-ttu-id="4cb09-159">In questa esercitazione si è appreso come usare Visione personalizzata di Azure per eseguire il training delle immagini e usare il servizio di classificazione per rilevare le immagini che corrispondono all'**oggetto tracciato** associato.</span><span class="sxs-lookup"><span data-stu-id="4cb09-159">In this tutorial you learned how Azure Custom Vision can be used to train images and use the classification service to detect images that match the associated **Tracked Object**.</span></span>

<span data-ttu-id="4cb09-160">Nell'esercitazione successiva verrà spiegato come usare Ancoraggi nello spazio di Azure per collegare un *oggetto tracciato* a una posizione nel mondo fisico e come visualizzare una freccia che guiderà l'utente per tornare alla posizione collegata dell'oggetto tracciato.</span><span class="sxs-lookup"><span data-stu-id="4cb09-160">In the next tutorial you will learn how to use Azure Spatial Anchors to link a *Tracked Object* with a location in the physical world and how to display an arrow that will guide the user back to the Tracked Object's linked location.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="4cb09-161">Esercitazione successiva: 4. Integrazione di Ancoraggi nello spazio di Azure</span><span class="sxs-lookup"><span data-stu-id="4cb09-161">Next tutorial: 4. Integrating Azure Spatial Anchors</span></span>](mr-learning-azure-04.md)
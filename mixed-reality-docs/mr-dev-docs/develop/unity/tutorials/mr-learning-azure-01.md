---
title: Servizi cloud di Azure per HoloLens 2
description: Completa questo corso per imparare a implementare vari servizi di Azure all'interno di un'applicazione HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: azure, realtà mista, unity, esercitazione, hololens, hololens 2, archiviazione blob di azure, archiviazione tabelle di azure, ancoraggi nello spazio di azure, azure bot framework, servizi cloud di azure, visione personalizzata di azure, Windows 10
ms.localizationpriority: high
ms.openlocfilehash: 3c52384b118a72b1c2f2dfaa2205e4f890e2e5a7
ms.sourcegitcommit: 114c304a416bfe9d9b294c4adbb4c23cbe60ea4e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/15/2021
ms.locfileid: "114224402"
---
# <a name="1-azure-cloud-services-for-hololens-2"></a><span data-ttu-id="3f381-104">1. Servizi cloud di Azure per HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="3f381-104">1. Azure Cloud Services for HoloLens 2</span></span>

<span data-ttu-id="3f381-105">Questa serie di esercitazioni è incentrata sull'inserimento di servizi **cloud di Azure** in un'applicazione **HoloLens 2**.</span><span class="sxs-lookup"><span data-stu-id="3f381-105">Welcome to this series of tutorials focused on bringing **Azure Cloud** services into a **HoloLens 2** application.</span></span> <span data-ttu-id="3f381-106">In questa serie di esercitazioni in cinque parti imparerai come integrare diversi servizi **cloud di Azure** in un progetto **Unity** per **HoloLens 2**.</span><span class="sxs-lookup"><span data-stu-id="3f381-106">In this five-part tutorial series, you will learn how to integrate several **Azure Cloud** services into a **Unity** project for **HoloLens 2**.</span></span> <span data-ttu-id="3f381-107">Un capitolo dopo l'altro, aggiungerai nuovi servizi **cloud di Azure** per espandere le funzionalità dell'applicazione e l'esperienza utente e allo stesso tempo apprenderai i concetti di base di ciascun servizio **cloud di Azure**.</span><span class="sxs-lookup"><span data-stu-id="3f381-107">With each consecutive chapter, you will add new **Azure Cloud** services to expand the application features and user experience, while teaching you the fundamentals of each **Azure Cloud** service.</span></span>

> [!NOTE]
> <span data-ttu-id="3f381-108">Questa serie di esercitazioni verterà soprattutto su **HoloLens 2** ma, data la natura multipiattaforma di Unity, la maggior parte delle nozioni apprese si applicherà anche alle applicazioni desktop e per smartphone.</span><span class="sxs-lookup"><span data-stu-id="3f381-108">This tutorial series will focus on the **HoloLens 2** but due the cross-platform nature of Unity, most of your learnings will also apply for Desktop and Smartphone applications.</span></span>

<span data-ttu-id="3f381-109">In questa prima esercitazione verranno presentati gli obiettivi della serie e i singoli servizi cloud di Azure che verranno usati e verrà configurato il progetto Unity iniziale.</span><span class="sxs-lookup"><span data-stu-id="3f381-109">In this first tutorial, you'll be introduced to the goals of the series and each Azure Cloud service you'll be using, as well as setting up the initial Unity project.</span></span>

<span data-ttu-id="3f381-110">Nella seconda esercitazione [Integrazione di Archiviazione di Azure](mr-learning-azure-02.md) si inizierà a integrare Archiviazione di Azure come soluzione di persistenza per l'applicazione demo.</span><span class="sxs-lookup"><span data-stu-id="3f381-110">In the second tutorial, [Integrating Azure Storage](mr-learning-azure-02.md), you'll start off by integrating Azure Storage as the persistence solution for the demo application.</span></span> <span data-ttu-id="3f381-111">Inoltre, verrà spiegato quali sono le differenze tra Archiviazione BLOB e Archiviazione tabelle e come preparare le risorse di progetto necessarie e configurare la scena.</span><span class="sxs-lookup"><span data-stu-id="3f381-111">You'll also learn the differences between Blob Storage and Table Storage, prepare the needed project resources, setup the scene.</span></span> <span data-ttu-id="3f381-112">Infine, si imparerà a verificare le operazioni di lettura, aggiornamento ed eliminazione dei dati.</span><span class="sxs-lookup"><span data-stu-id="3f381-112">Finally, you'll learn how to verify the read, update, and delete data operations.</span></span>

<span data-ttu-id="3f381-113">Continuando con la terza esercitazione, [Integrazione di Visione personalizzata di Azure](mr-learning-azure-03.md), userai questo servizio per eseguire il training e il rilevamento delle immagini nell'applicazione HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="3f381-113">Continuing with the third tutorial, [Integrating Azure Custom Vision](mr-learning-azure-03.md), you will use Azure Custom Vision to train and detect images in the HoloLens 2 application.</span></span> <span data-ttu-id="3f381-114">Il capitolo comincia con l'impostazione della risorsa Visione personalizzata di Azure e potrai preparare i componenti della scena e iniziare a lavorare eseguendo il training e rilevando le tue immagini dall'interno dell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="3f381-114">The chapter starts off with setting up your own Azure Custom Vision resource, preparing the scene components and getting into action by training and detecting your own images from inside the application.</span></span>

<span data-ttu-id="3f381-115">Potrai quindi passare alla quarta esercitazione, [Integrazione di ancoraggi nello spazio di Azure](mr-learning-azure-04.md), ed esplorare questo servizio per salvare e trovare le posizioni, apprendere i concetti principali, preparare le risorse necessarie, impostare la scena e iniziare a usare la nuova funzionalità nell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="3f381-115">Next you advance in the fourth tutorial, [Integrating Azure Spatial Anchors](mr-learning-azure-04.md), with exploring Azure Spatial Anchors service to save and find locations, learn the core concepts, prepare necessary resources, setup the scene and start using the new feature in the application.</span></span>

<span data-ttu-id="3f381-116">Con la quinta esercitazione, [Integrazione del servizio Azure Bot con LUIS](mr-learning-azure-05.md), potrai terminare la tua preparazione fornendo all'applicazione un nuovo metodo di interazione dell'utente: il linguaggio naturale.</span><span class="sxs-lookup"><span data-stu-id="3f381-116">With the fifth tutorial, [Integrating Azure Bot Service with LUIS](mr-learning-azure-05.md), you finalize by giving the application a new method of user interaction: natural language!</span></span> <span data-ttu-id="3f381-117">Questa funzionalità verrà realizzata usando Azure Bot Framework insieme a Language Understanding (LUIS).</span><span class="sxs-lookup"><span data-stu-id="3f381-117">This feature will be realized by using the Azure Bot Framework together with Language Understanding (LUIS).</span></span> <span data-ttu-id="3f381-118">Questo capitolo finale illustra le nozioni di base del servizio Azure Bot e, per velocizzare il processo, userai Bot Framework Composer come soluzione senza codice.</span><span class="sxs-lookup"><span data-stu-id="3f381-118">This final chapter teaches you the basics of Azure Bot Service and to speed up the process you will be using the Bot Framework Composer as a zero code solution.</span></span> <span data-ttu-id="3f381-119">Una volta creato il bot, lo integrerai nella scena e potrai eseguirlo con la fase finale dell'applicazione HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="3f381-119">Once the bot is created, you will integrate it into the scene and give it a run with the final stage of the HoloLens 2 application.</span></span>

## <a name="application-goals"></a><span data-ttu-id="3f381-120">Obiettivi dell'applicazione</span><span class="sxs-lookup"><span data-stu-id="3f381-120">Application goals</span></span>

<span data-ttu-id="3f381-121">In questa serie di esercitazioni verrà creata un'applicazione **HoloLens 2** in grado di rilevare oggetti dalle immagini e trovarne la posizione nello spazio.</span><span class="sxs-lookup"><span data-stu-id="3f381-121">In this tutorial series, you will build a **HoloLens 2** application that can detect objects from images and find its spatial location.</span></span> <span data-ttu-id="3f381-122">Per definire una terminologia specifica, da questo momento in poi tali entità vengono definite **oggetto tracciato**.</span><span class="sxs-lookup"><span data-stu-id="3f381-122">To set a domain language, you call such entities from now **Tracked Object**.</span></span>
<span data-ttu-id="3f381-123">L'utente può creare un **oggetto tracciato** per associare un set di immagini tramite visione artificiale e/o una posizione nello spazio.</span><span class="sxs-lookup"><span data-stu-id="3f381-123">The user can create a **Tracked Object** to either or both associate a set of images via computer vision and/or a spatial location.</span></span> <span data-ttu-id="3f381-124">Tutti i dati devono essere salvati nel cloud.</span><span class="sxs-lookup"><span data-stu-id="3f381-124">All data must be persisted into the cloud.</span></span> <span data-ttu-id="3f381-125">Inoltre, alcuni aspetti dell'applicazione saranno controllati facoltativamente dal linguaggio naturale assistito tramite un bot.</span><span class="sxs-lookup"><span data-stu-id="3f381-125">Furthermore some aspects of the application will be optionally controlled by natural language assisted through a bot.</span></span>

### <a name="features"></a><span data-ttu-id="3f381-126">Caratteristiche</span><span class="sxs-lookup"><span data-stu-id="3f381-126">Features</span></span>

* <span data-ttu-id="3f381-127">Gestione di base di dati e immagini</span><span class="sxs-lookup"><span data-stu-id="3f381-127">Basic managing of data and images</span></span>
* <span data-ttu-id="3f381-128">Training e rilevamento delle immagini</span><span class="sxs-lookup"><span data-stu-id="3f381-128">Image training and detection</span></span>
* <span data-ttu-id="3f381-129">Archiviazione di una posizione nello spazio e indicazioni per trovarla</span><span class="sxs-lookup"><span data-stu-id="3f381-129">Storing a spatial location and guidance to it</span></span>
* <span data-ttu-id="3f381-130">Assistente bot per usare alcune funzionalità tramite linguaggio naturale</span><span class="sxs-lookup"><span data-stu-id="3f381-130">Bot assistant to use some features via natural language</span></span>

## <a name="azure-cloud-services"></a><span data-ttu-id="3f381-131">Servizi cloud di Azure</span><span class="sxs-lookup"><span data-stu-id="3f381-131">Azure Cloud services</span></span>

<span data-ttu-id="3f381-132">Verranno usati i seguenti **Servizi cloud di Azure** per implementare le funzionalità indicate sopra:</span><span class="sxs-lookup"><span data-stu-id="3f381-132">You'll use the following **Azure Cloud** services to implement the above features:</span></span>

### <a name="azure-storage"></a><span data-ttu-id="3f381-133">Archiviazione di Azure</span><span class="sxs-lookup"><span data-stu-id="3f381-133">Azure Storage</span></span>

<span data-ttu-id="3f381-134">Userai [Archiviazione di Azure](https://azure.microsoft.com/services/storage/) per la soluzione di persistenza.</span><span class="sxs-lookup"><span data-stu-id="3f381-134">You will use [Azure Storage](https://azure.microsoft.com/services/storage/) for the persistence solution.</span></span> <span data-ttu-id="3f381-135">Consente di archiviare i dati in una tabella e caricare file binari di grandi dimensioni, ad esempio immagini.</span><span class="sxs-lookup"><span data-stu-id="3f381-135">It allows you to store data on a table and upload large binaries like images.</span></span>

### <a name="azure-custom-vision"></a><span data-ttu-id="3f381-136">Visione personalizzata di Azure</span><span class="sxs-lookup"><span data-stu-id="3f381-136">Azure Custom Vision</span></span>

<span data-ttu-id="3f381-137">Con [Visione personalizzata di Azure](https://azure.microsoft.com/services/cognitive-services/custom-vision-service/) (che fa parte di [Servizi cognitivi di Azure](https://azure.microsoft.com/services/cognitive-services/)) puoi associare agli *oggetti tracciati* un set di immagini, eseguire il training di un modello di Machine Learning per il set e rilevare l'*oggetto tracciato*.</span><span class="sxs-lookup"><span data-stu-id="3f381-137">With [Azure Custom Vision](https://azure.microsoft.com/services/cognitive-services/custom-vision-service/) (part of the [Azure Cognitive Services](https://azure.microsoft.com/services/cognitive-services/)) you can associate to *Tracked Objects* a set of images, train a machine learning model on the set and detect the *Tracked Object*.</span></span>

### <a name="azure-spatial-anchors"></a><span data-ttu-id="3f381-138">Ancoraggi nello spazio di Azure</span><span class="sxs-lookup"><span data-stu-id="3f381-138">Azure Spatial Anchors</span></span>

<span data-ttu-id="3f381-139">Per archiviare la posizione di un *oggetto tracciato* e fornire indicazioni guidate per trovarla, puoi usare [ancoraggi nello spazio di Azure](https://azure.microsoft.com/services/spatial-anchors/).</span><span class="sxs-lookup"><span data-stu-id="3f381-139">To store a *Tracked Object* location and give a guided directions to find it, you use [Azure Spatial Anchors](https://azure.microsoft.com/services/spatial-anchors/).</span></span>

### <a name="azure-bot-service"></a><span data-ttu-id="3f381-140">servizio Azure Bot</span><span class="sxs-lookup"><span data-stu-id="3f381-140">Azure Bot Service</span></span>

<span data-ttu-id="3f381-141">L'applicazione è basata principalmente sull'interfaccia utente tradizionale, quindi puoi usare il [servizio Azure Bot](https://azure.microsoft.com/services/bot-service/) per aggiungere personalità e operare con un nuovo metodo di interazione.</span><span class="sxs-lookup"><span data-stu-id="3f381-141">The application is mainly driven by traditional UI, so you use the [Azure Bot Service](https://azure.microsoft.com/services/bot-service/) to add some personality and act as a new interaction method.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="3f381-142">Prerequisiti</span><span class="sxs-lookup"><span data-stu-id="3f381-142">Prerequisites</span></span>

>[!TIP]
><span data-ttu-id="3f381-143">Se non hai ancora completato la serie di [Esercitazioni introduttive](mr-learning-base-01.md), è consigliabile completare prima queste esercitazioni.</span><span class="sxs-lookup"><span data-stu-id="3f381-143">If you have not completed the [Getting started tutorials](mr-learning-base-01.md) series yet, it's recommended that you complete those tutorials first.</span></span>

* <span data-ttu-id="3f381-144">Un PC Windows 10 configurato in cui siano [installati gli strumenti](../../install-the-tools.md) corretti</span><span class="sxs-lookup"><span data-stu-id="3f381-144">A Windows 10 PC configured with the correct [tools installed](../../install-the-tools.md)</span></span>
* <span data-ttu-id="3f381-145">Windows 10 SDK 10.0.18362.0 o versioni successive</span><span class="sxs-lookup"><span data-stu-id="3f381-145">Windows 10 SDK 10.0.18362.0 or later</span></span>
* <span data-ttu-id="3f381-146">Alcune funzionalità di programmazione C# di base</span><span class="sxs-lookup"><span data-stu-id="3f381-146">Some basic C# programming ability</span></span>
* <span data-ttu-id="3f381-147">Un dispositivo HoloLens 2 [configurato per lo sviluppo](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)</span><span class="sxs-lookup"><span data-stu-id="3f381-147">A HoloLens 2 device [configured for development](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)</span></span>
* <span data-ttu-id="3f381-148">Una webcam connessa se vuoi eseguire il test dall'editor di Unity</span><span class="sxs-lookup"><span data-stu-id="3f381-148">A connected webcam if you like to test from Unity editor</span></span>
* <span data-ttu-id="3f381-149"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> con Unity 2020/2019 LTS installato e il modulo Universal Windows Platform Build Support aggiunto</span><span class="sxs-lookup"><span data-stu-id="3f381-149"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2020/2019 LTS installed and the Universal Windows Platform Build Support module added</span></span>

> [!Important]
> <span data-ttu-id="3f381-150">Questa serie di esercitazioni supporta Unity 2020 LTS (attualmente 2020.3.x) se si usa Open XR o Windows XR Plugin e anche Unity 2019 LTS (attualmente 2019.4.x) se si usa WSA legacy.</span><span class="sxs-lookup"><span data-stu-id="3f381-150">This tutorial series supports Unity 2020 LTS(currently 2020.3.x) if you are using Open XR or Windows XR Plugin and also Unity 2019 LTS (currently 2019.4.x) if you are using Legacy WSA.</span></span> <span data-ttu-id="3f381-151">Questa istruzione sostituisce gli eventuali requisiti relativi alla versione di Unity indicati negli argomenti visualizzabili facendo clic sui collegamenti dei prerequisiti sopra riportati.</span><span class="sxs-lookup"><span data-stu-id="3f381-151">This supersedes any Unity version requirements stated in the prerequisites linked above.</span></span>

## <a name="creating-and-preparing-the-unity-project"></a><span data-ttu-id="3f381-152">Creazione e preparazione del progetto Unity</span><span class="sxs-lookup"><span data-stu-id="3f381-152">Creating and preparing the Unity project</span></span>

<span data-ttu-id="3f381-153">In questa sezione creerai un nuovo progetto Unity per prepararti allo sviluppo con MRTK.</span><span class="sxs-lookup"><span data-stu-id="3f381-153">In this section, you will create a new Unity project and get it ready for MRTK development.</span></span>

<span data-ttu-id="3f381-154">Seguire prima l'esercitazione [Inizializzazione del progetto e prima applicazione](mr-learning-base-02.md), escluse le istruzioni della sezione [Compilare l'applicazione nel dispositivo](mr-learning-base-02.md#building-your-application-to-your-hololens-2). L'esercitazione include i passaggi seguenti:</span><span class="sxs-lookup"><span data-stu-id="3f381-154">First, follow the [Initializing your project and first application](mr-learning-base-02.md), excluding the [Build your application to your device](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions, which includes the following steps:</span></span>

1. <span data-ttu-id="3f381-155">[Creazione del progetto Unity](mr-learning-base-02.md#creating-the-unity-project) e assegnazione di un nome appropriato, ad esempio *Azure Cloud Tutorials*</span><span class="sxs-lookup"><span data-stu-id="3f381-155">[Creating the Unity project](mr-learning-base-02.md#creating-the-unity-project) and give it a suitable name, for example, *Azure Cloud Tutorials*</span></span>
2. [<span data-ttu-id="3f381-156">Passaggio a un'altra piattaforma di compilazione</span><span class="sxs-lookup"><span data-stu-id="3f381-156">Switching the build platform</span></span>](mr-learning-base-02.md#switching-the-build-platform)
3. [<span data-ttu-id="3f381-157">Importazione delle risorse essenziali TextMeshPro</span><span class="sxs-lookup"><span data-stu-id="3f381-157">Importing the TextMeshPro Essential Resources</span></span>](mr-learning-base-04.md#importing-the-textmeshpro-essential-resources)
4. [<span data-ttu-id="3f381-158">Importazione del progetto Toolkit realtà mista e configurazione del progetto Unity</span><span class="sxs-lookup"><span data-stu-id="3f381-158">Importing the Mixed Reality Toolkit and Configuring the Unity project</span></span>](mr-learning-base-02.md#importing-the-mixed-reality-toolkit-and-configuring-the-unity-project)
5. <span data-ttu-id="3f381-159">[Creazione e configurazione della scena](mr-learning-base-02.md#creating-the-scene-and-configuring-mrtk) e assegnazione di un nome appropriato, ad esempio *AzureCloudServices*</span><span class="sxs-lookup"><span data-stu-id="3f381-159">[Creating and configuring the scene](mr-learning-base-02.md#creating-the-scene-and-configuring-mrtk) and give the scene a suitable name, for example, *AzureCloudServices*</span></span>

<span data-ttu-id="3f381-160">Seguire quindi [](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) le istruzioni relative alla modifica dell'opzione di visualizzazione della consapevolezza spaziale per assicurarsi che il profilo di configurazione MRTK per la scena sia **DefaultHololens2ConfigurationProfile** e modificare le opzioni di visualizzazione per la mesh di riconoscimento spaziale in **Occlusione.**</span><span class="sxs-lookup"><span data-stu-id="3f381-160">Then follow the [Changing the Spatial Awareness Display Option](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) instructions to ensure the MRTK configuration profile for your scene is **DefaultHololens2ConfigurationProfile** and change the display options for the spatial awareness mesh to **Occlusion**.</span></span>

## <a name="installing-inbuilt-unity-packages-and-importing-the-tutorial-assets"></a><span data-ttu-id="3f381-161">Installazione di pacchetti Unity predefiniti e importazione degli asset dell'esercitazione</span><span class="sxs-lookup"><span data-stu-id="3f381-161">Installing inbuilt Unity packages and Importing the tutorial assets</span></span>

[!INCLUDE[](includes/installing-packages-for-azure-cloud-services.md)]

## <a name="creating-and-preparing-the-scene"></a><span data-ttu-id="3f381-162">Creazione e preparazione della scena</span><span class="sxs-lookup"><span data-stu-id="3f381-162">Creating and preparing the scene</span></span>

<span data-ttu-id="3f381-163">In questa sezione preparerai la scena aggiungendo alcuni dei prefab dell'esercitazione.</span><span class="sxs-lookup"><span data-stu-id="3f381-163">In this section, you will prepare the scene by adding some of the tutorial prefabs.</span></span>

<span data-ttu-id="3f381-164">Nella finestra Project (Progetto) passa alla cartella **Assets** (Asset)  > **MRTK.Tutorials.AzureCloudServices** > **Prefabs** (Prefab)  > **Manager**.</span><span class="sxs-lookup"><span data-stu-id="3f381-164">In the Project window, navigate to **Assets** > **MRTK.Tutorials.AzureCloudServices** > **Prefabs** > **Manager** folder.</span></span> <span data-ttu-id="3f381-165">Tenendo premuto il tasto CTRL, fai clic su **SceneController**, **RootMenu** e **DataManager** per selezionare i tre prefab:</span><span class="sxs-lookup"><span data-stu-id="3f381-165">While holding down the CTRL button, click on **SceneController**, **RootMenu** and **DataManager** to select the three prefabs:</span></span>

![Unity con i prefab SceneController, RootMenu e DataManager selezionati](images/mr-learning-azure/tutorial1-section5-step1-1.png)

<span data-ttu-id="3f381-167">SceneController **(prefab)** contiene due script, **SceneController (script)** e **AppDispatcher (script).**</span><span class="sxs-lookup"><span data-stu-id="3f381-167">The **SceneController (prefab)** contains two scripts, **SceneController (script)** and **AppDispatcher (script)**.</span></span> <span data-ttu-id="3f381-168">Il componente script **SceneController** contiene diverse funzioni UX e facilita la funzionalità di acquisizione di foto, mentre **AppDispatcher** è una classe helper per consentire l'esecuzione di azioni nel thread principale di Unity.</span><span class="sxs-lookup"><span data-stu-id="3f381-168">The **SceneController** script component contains several UX functions and facilitates the photo capture functionality while **AppDispatcher** is a helper class to allow execute actions on the Unity main thread.</span></span>

<span data-ttu-id="3f381-169">**RootMenu (prefab)** è il principale prefab dell'interfaccia utente e include tutte le relative finestre, che sono connesse tra loro tramite vari piccoli componenti script e controllano il flusso UX generale dell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="3f381-169">The **RootMenu (prefab)** is the primary UI prefab that holds all UI windows that are connected to each other through various small script components and control the general UX flow of the application.</span></span>

<span data-ttu-id="3f381-170">**DataManager (prefab)** è responsabile della comunicazione con Archiviazione di Azure e verrà illustrato più in dettaglio nell'esercitazione successiva.</span><span class="sxs-lookup"><span data-stu-id="3f381-170">The **DataManager (prefab)** is responsible for talking to Azure storage and will be explained further in the next tutorial.</span></span>

<span data-ttu-id="3f381-171">Ora con i tre prefab ancora selezionati, trascinali nella finestra Hierarchy (Gerarchia) per aggiungerli alla scena:</span><span class="sxs-lookup"><span data-stu-id="3f381-171">Now with the three prefabs still selected, drag them into the Hierarchy window to add them to the scene:</span></span>

![Unity con i nuovi prefab SceneController, RootMenu e DataManager aggiunti ancora selezionati](images/mr-learning-azure/tutorial1-section5-step1-2.png)

<span data-ttu-id="3f381-173">Per concentrarti sugli oggetti nella scena, puoi fare doppio clic sull'oggetto **RootMenu** e quindi fare di nuovo leggermente zoom indietro:</span><span class="sxs-lookup"><span data-stu-id="3f381-173">To focus in on the objects in the scene, you can double-click on the **RootMenu** object, and then zoom slightly out again:</span></span>

![Unity con l'oggetto RootMenu selezionato](images/mr-learning-azure/tutorial1-section5-step1-3.png)

> [!TIP]
> <span data-ttu-id="3f381-175">Se trovi che le icone grandi nella scena, come quelle a forma di "T", siano motivo di distrazione, puoi nasconderle <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">disattivando i gizmo</a>.</span><span class="sxs-lookup"><span data-stu-id="3f381-175">If you find the large icons in your scene, for example, the large framed 'T' icons distracting, you can hide these by <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">toggling the Gizmos</a> to the off position.</span></span>

## <a name="configuring-the-scene"></a><span data-ttu-id="3f381-176">Configurazione della scena</span><span class="sxs-lookup"><span data-stu-id="3f381-176">Configuring the scene</span></span>

<span data-ttu-id="3f381-177">In questa sezione connetterai *SceneManager*, *DataManager* e *RootMenu* insieme in modo che una scena di lavoro sia pronta per l'esercitazione successiva, ovvero [Integrazione di Archiviazione di Azure](mr-learning-azure-01.md).</span><span class="sxs-lookup"><span data-stu-id="3f381-177">In this section, you will connect *SceneManager*, *DataManager* and *RootMenu* together to have a working scene to be ready for the following [Integrating Azure storage](mr-learning-azure-01.md) tutorial.</span></span>

### <a name="connect-the-objects"></a><span data-ttu-id="3f381-178">Connettere gli oggetti</span><span class="sxs-lookup"><span data-stu-id="3f381-178">Connect the objects</span></span>

<span data-ttu-id="3f381-179">Nella finestra Hierarchy (Gerarchia) seleziona l'oggetto **DataManager**:</span><span class="sxs-lookup"><span data-stu-id="3f381-179">In the Hierarchy window, select the **DataManager** object:</span></span>

![Unity con l'oggetto DataManager selezionato](images/mr-learning-azure/tutorial1-section6-step1-1.png)

<span data-ttu-id="3f381-181">Nella finestra Inspector (Controllo) individua il componente **DataManager (Script)** . Verrà visualizzato uno slot vuoto per l'evento **On Data Manager Ready ()** (Quando Data Manager è pronto).</span><span class="sxs-lookup"><span data-stu-id="3f381-181">In the Inspector window, locate the **DataManager (Script)** component and you will see an empty slot on the **On Data Manager Ready ()** event.</span></span> <span data-ttu-id="3f381-182">Ora dalla finestra Hierarchy (Gerarchia) trascina l'oggetto **SceneController** nell'evento **On Data Manager Ready ()** (Quando Data Manager è pronto).</span><span class="sxs-lookup"><span data-stu-id="3f381-182">Now from the Hierarchy window drag the **SceneController** object into the **On Data Manager Ready ()** event.</span></span>

![Unity con il listener di eventi DataManager aggiunto](images/mr-learning-azure/tutorial1-section6-step1-2.png)

<span data-ttu-id="3f381-184">Noterai che il menu a discesa dell'evento è diventato attivo. Fai clic su questo menu e passa a **SceneController**, quindi dal sottomenu scegli l'opzione **Init ()** :</span><span class="sxs-lookup"><span data-stu-id="3f381-184">You will notice that the dropdown menu of the event became active, click on the dropdown menu and navigate to **SceneController** and in the sub menu select the **Init ()** option:</span></span>

![Unity con l'azione evento DataManager aggiunto](images/mr-learning-azure/tutorial1-section6-step1-3.png)

<span data-ttu-id="3f381-186">Nella finestra Hierarchy (Gerarchia) seleziona l'oggetto **SceneController**. In Inspector (Controllo) sarà disponibile il componente **SceneController** (script).</span><span class="sxs-lookup"><span data-stu-id="3f381-186">From the Hierarchy window, select the **SceneController** object, there in the Inspector you will find the **SceneController** (script) component.</span></span>

![Unity con SceneController selezionato](images/mr-learning-azure/tutorial1-section6-step1-4.png)

<span data-ttu-id="3f381-188">Noterai che sono presenti diversi campi non popolati. Ora puoi modificarli.</span><span class="sxs-lookup"><span data-stu-id="3f381-188">You will see that there are several unpopulated fields, let's change that.</span></span> <span data-ttu-id="3f381-189">Sposta l'oggetto **DataManager** da Hierarchy (Gerarchia) nel campo *Data Manager*, quindi sposta GameObject di **RootMenu** da Hierarchy (Gerarchia) nel campo *Main Menu* (Menu principale).</span><span class="sxs-lookup"><span data-stu-id="3f381-189">Move the **DataManager** object from the Hierarchy into the *Data Manager* field and move the **RootMenu** GameObject from the Hierarchy into the *Main Menu* field.</span></span>

![Unity con SceneController configurato](images/mr-learning-azure/tutorial1-section6-step1-5.png)

<span data-ttu-id="3f381-191">Ora la scena è pronta per le prossime esercitazioni.</span><span class="sxs-lookup"><span data-stu-id="3f381-191">Now your scene is ready for the upcoming tutorials.</span></span> <span data-ttu-id="3f381-192">Non dimenticare di salvarla nel progetto.</span><span class="sxs-lookup"><span data-stu-id="3f381-192">Don't forget to save it into your project.</span></span>

## <a name="prepare-project-build-pipeline"></a><span data-ttu-id="3f381-193">Preparare la pipeline di compilazione del progetto</span><span class="sxs-lookup"><span data-stu-id="3f381-193">Prepare project build pipeline</span></span>

<span data-ttu-id="3f381-194">Anche se nel progetto deve essere ancora inserito il contenuto, devi eseguire alcune operazioni di preparazione, in modo che il progetto sia pronto per la compilazione per **HoloLens 2**.</span><span class="sxs-lookup"><span data-stu-id="3f381-194">While the project yet has to be filled with content, you have to perform some preparations, so the project is ready for building for **HoloLens 2**.</span></span>

### <a name="1-add-additional-required-capabilities"></a><span data-ttu-id="3f381-195">1. Aggiungere altre funzionalità necessarie</span><span class="sxs-lookup"><span data-stu-id="3f381-195">1. Add additional required capabilities</span></span>

<span data-ttu-id="3f381-196">Dal menu di Unity scegli **Edit** (Modifica) > **Project Settings** (Impostazioni del progetto) per visualizzare la finestra corrispondente:</span><span class="sxs-lookup"><span data-stu-id="3f381-196">In the Unity menu, select **Edit** > **Project Settings...** to open the Project Settings window:</span></span>

![Unity con impostazioni di progetto aperte](images/mr-learning-azure/tutorial1-section7-step1-1.png)

<span data-ttu-id="3f381-198">Nella finestra Project Settings (Impostazioni progetto) seleziona **Player** (Lettore) e quindi **Publishing Settings** (Impostazioni di pubblicazione):</span><span class="sxs-lookup"><span data-stu-id="3f381-198">In the Project Settings window, select **Player** and then **Publishing Settings**:</span></span>

![Impostazioni di pubblicazione di Unity](images/mr-learning-azure/tutorial1-section7-step1-2.png)

<span data-ttu-id="3f381-200">In **Publishing Settings** (Impostazioni di pubblicazione) scorri verso il basso fino alla sezione **Capabilities** (Funzionalità) e riverifica che siano abilitate le funzionalità **InternetClient**, **Microphone** e **SpatialPerception**, che hai abilitato al momento della creazione del progetto all'inizio dell'esercitazione.</span><span class="sxs-lookup"><span data-stu-id="3f381-200">In the  **Publishing Settings**, scroll down to the **Capabilities** section and double-check that the **InternetClient**, **Microphone** and **SpatialPerception** capabilities, which you enabled when you created the project at the beginning of the tutorial, are enabled.</span></span> <span data-ttu-id="3f381-201">Abilita quindi le funzionalità **InternetClientServer**, **PrivateNetworkClientServer** e **Webcam**:</span><span class="sxs-lookup"><span data-stu-id="3f381-201">Then, enable the **InternetClientServer**, **PrivateNetworkClientServer**, and **Webcam** capabilities:</span></span>

![Funzionalità di Unity](images/mr-learning-azure/tutorial1-section7-step1-3.png)

### <a name="2-deploy-the-app-to-your-hololens-2"></a><span data-ttu-id="3f381-203">2. Distribuire l'app nel dispositivo HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="3f381-203">2. Deploy the app to your HoloLens 2</span></span>

<span data-ttu-id="3f381-204">Non tutte le funzionalità che userai in questa serie di esercitazioni possono essere eseguite nell'editor di Unity. Ciò significa che è necessario avere familiarità con la distribuzione dell'applicazione nel dispositivo HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="3f381-204">Not all features that you will use in this tutorial series can run inside the Unity editor, this means that you need to be familiar with deploying the application to your HoloLens 2 device.</span></span>

> [!TIP]
> <span data-ttu-id="3f381-205">Per rileggere come creare e distribuire il progetto Unity in HoloLens 2, puoi fare riferimento alle istruzioni riportate in [Esercitazioni introduttive - Compilare l'applicazione nel dispositivo](mr-learning-base-02.md#building-your-application-to-your-hololens-2).</span><span class="sxs-lookup"><span data-stu-id="3f381-205">For a reminder on how to build and deploy your Unity project to HoloLens 2, you can refer to the [Getting started tutorials - Build your application to your device](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions.</span></span>

### <a name="3-run-the-app-on-your-hololens-2-and-follow-the-in-app-instructions"></a><span data-ttu-id="3f381-206">3. Eseguire l'app in HoloLens 2 e seguire le istruzioni in-app</span><span class="sxs-lookup"><span data-stu-id="3f381-206">3. Run the app on your HoloLens 2 and follow the in-app instructions</span></span>

> [!CAUTION]
> <span data-ttu-id="3f381-207">Tutti i servizi di Azure usano Internet, quindi assicurati che il dispositivo sia connesso a Internet.</span><span class="sxs-lookup"><span data-stu-id="3f381-207">All Azure Services uses the internet, so make sure your device is connected to the internet.</span></span>

<span data-ttu-id="3f381-208">Quando l'applicazione è in esecuzione nel dispositivo, accetta l'accesso alle seguenti funzionalità richieste:</span><span class="sxs-lookup"><span data-stu-id="3f381-208">When the application is running on your device, accept access to the following requested capabilities:</span></span>

* <span data-ttu-id="3f381-209">Microfono</span><span class="sxs-lookup"><span data-stu-id="3f381-209">Microphone</span></span>
* <span data-ttu-id="3f381-210">Fotocamera</span><span class="sxs-lookup"><span data-stu-id="3f381-210">Camera</span></span>

<span data-ttu-id="3f381-211">Queste funzionalità sono necessarie per il corretto funzionamento di servizi quali *Chat bot* e *Visione personalizzata*.</span><span class="sxs-lookup"><span data-stu-id="3f381-211">These capabilities are required for services like *Chat Bot* and *Custom Vision* to function properly.</span></span>

## <a name="congratulations"></a><span data-ttu-id="3f381-212">Lezione completata</span><span class="sxs-lookup"><span data-stu-id="3f381-212">Congratulations</span></span>

<span data-ttu-id="3f381-213">In questa esercitazione è stata presentata la serie di esercitazioni, sono state illustrate le funzionalità che implementerai ed è stato spiegato in che modo interagiscono i servizi **cloud di Azure** per far funzionare la tua applicazione *HoloLens 2*.</span><span class="sxs-lookup"><span data-stu-id="3f381-213">In this tutorial, you were introduced to the tutorial series, learned about the features you will implement and how **Azure Cloud** services tie in to making your *HoloLens 2* application happen.</span></span> <span data-ttu-id="3f381-214">Hai aggiunto i componenti necessari nel progetto e hai preparato la scena per questa serie di esercitazioni.</span><span class="sxs-lookup"><span data-stu-id="3f381-214">You added the required components into the project and prepared the scene for this tutorial series.</span></span>

<span data-ttu-id="3f381-215">Nella lezione successiva userai Archiviazione di Azure come soluzione di persistenza basata sul cloud per archiviare dati e immagini.</span><span class="sxs-lookup"><span data-stu-id="3f381-215">In the next lesson, you will use Azure storage as a cloud based persistence solution for storing data and images.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="3f381-216">Esercitazione successiva: 2. Integrazione di Archiviazione di Azure</span><span class="sxs-lookup"><span data-stu-id="3f381-216">Next tutorial: 2. Integrating Azure storage</span></span>](mr-learning-azure-02.md)
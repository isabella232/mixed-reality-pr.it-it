---
title: Integrazione del servizio Azure Bot con LUIS
description: Completa questo corso per apprendere come implementare il servizio Azure Bot e il riconoscimento del linguaggio naturale in un'applicazione HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens, hololens 2, servizio azure bot, luis, linguaggio naturale, bot conversazione, servizi cloud di azure, visione personalizzata di azure, Windows 10
ms.localizationpriority: high
ms.openlocfilehash: 7119dfd54c2b5384ff0e219a494ca8423fe4ebfc
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/20/2021
ms.locfileid: "98583386"
---
# <a name="5-integrating-azure-bot-service"></a><span data-ttu-id="9c662-104">5. Integrazione del servizio Azure Bot</span><span class="sxs-lookup"><span data-stu-id="9c662-104">5. Integrating Azure Bot Service</span></span>

<span data-ttu-id="9c662-105">In questa esercitazione apprenderai come usare il **servizio Azure Bot** nell'applicazione demo **HoloLens 2** per aggiungere Language Understanding (LUIS), consentendo al bot di assistere l'utente durante la ricerca di **oggetti tracciati**.</span><span class="sxs-lookup"><span data-stu-id="9c662-105">In this tutorial, you will learn how to use **Azure Bot Service** in the **HoloLens 2** demo application to add Language Understanding (LUIS) and letting the Bot assist the user when searching for **Tracked Objects**.</span></span> <span data-ttu-id="9c662-106">Si tratta di un'esercitazione in due parti, in cui nella prima parte creerai il bot tramite [Bot Composer](/composer/introduction) come soluzione senza codice e avrai una rapida descrizione della funzione di Azure che fornisce al bot i dati necessari.</span><span class="sxs-lookup"><span data-stu-id="9c662-106">This is a two part tutorial where in the first part you create the Bot with the [Bot Composer](/composer/introduction) as a code free solution and take a quick look in the Azure Function that feeds the Bot with the needed data.</span></span> <span data-ttu-id="9c662-107">Nella seconda parte userai **BotManager (script)** nel progetto Unity per utilizzare il servizio Bot ospitato.</span><span class="sxs-lookup"><span data-stu-id="9c662-107">In the second part you use the **BotManager (script)** in the Unity project to consume the hosted Bot Service.</span></span>

## <a name="objectives"></a><span data-ttu-id="9c662-108">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="9c662-108">Objectives</span></span>

## <a name="part-1"></a><span data-ttu-id="9c662-109">Parte 1</span><span class="sxs-lookup"><span data-stu-id="9c662-109">Part 1</span></span>

* <span data-ttu-id="9c662-110">Apprendere le nozioni di base relative al servizio Azure Bot</span><span class="sxs-lookup"><span data-stu-id="9c662-110">Learn the basics about Azure Bot Service</span></span>
* <span data-ttu-id="9c662-111">Apprendere come usare Bot Composer per creare un bot</span><span class="sxs-lookup"><span data-stu-id="9c662-111">Learn how to use the Bot Composer to create a Bot</span></span>
* <span data-ttu-id="9c662-112">Apprendere come usare una funzione di Azure per fornire dati dall'archivio di Azure</span><span class="sxs-lookup"><span data-stu-id="9c662-112">Learn how to use an Azure Function to provide data from the Azure Storage</span></span>

## <a name="part-2"></a><span data-ttu-id="9c662-113">Parte 2</span><span class="sxs-lookup"><span data-stu-id="9c662-113">Part 2</span></span>

* <span data-ttu-id="9c662-114">Apprendere come impostare la scena per l'uso del servizio Azure Bot in questo progetto</span><span class="sxs-lookup"><span data-stu-id="9c662-114">Learn how to setup the scene to use Azure Bot Service in this project</span></span>
* <span data-ttu-id="9c662-115">Apprendere come impostare e trovare oggetti tramite conversazione con il bot</span><span class="sxs-lookup"><span data-stu-id="9c662-115">Learn how to set and find objects via conversing with the Bot</span></span>

## <a name="understanding-azure-bot-service"></a><span data-ttu-id="9c662-116">Informazioni sul servizio Azure Bot</span><span class="sxs-lookup"><span data-stu-id="9c662-116">Understanding Azure Bot Service</span></span>

<span data-ttu-id="9c662-117">Il **servizio Azure Bot** consente agli sviluppatori di creare bot intelligenti in grado di avere una conversazione naturale con gli utenti grazie a **LUIS**.</span><span class="sxs-lookup"><span data-stu-id="9c662-117">The **Azure Bot Service** empowers developers to create intelligent bots that can maintain natural conversation with users thanks to **LUIS**.</span></span> <span data-ttu-id="9c662-118">Un bot conversazionale è un ottimo mezzo per espandere i modi in cui un utente può interagire con l'applicazione.</span><span class="sxs-lookup"><span data-stu-id="9c662-118">A conversational Bot is a great way to expand the ways a user can interact with your application.</span></span> <span data-ttu-id="9c662-119">Un bot può infatti fungere da knowledge base con [QnA Maker](/azure/bot-service/bot-builder-howto-qna?preserve-view=true&tabs=cs&view=azure-bot-service-4.0) per gestire una conversazione complessa con le potenzialità di [Language Understanding (LUIS)](/azure/bot-service/bot-builder-howto-v4-luis?preserve-view=true&tabs=csharp&view=azure-bot-service-4.0).</span><span class="sxs-lookup"><span data-stu-id="9c662-119">A Bot can act as a knowledge base with a [QnA Maker](/azure/bot-service/bot-builder-howto-qna?preserve-view=true&tabs=cs&view=azure-bot-service-4.0) to maintaining sophisticated conversation with the power of [Language Understanding (LUIS)](/azure/bot-service/bot-builder-howto-v4-luis?preserve-view=true&tabs=csharp&view=azure-bot-service-4.0).</span></span>

<span data-ttu-id="9c662-120">Scopri di più sul [servizio Azure Bot](/azure/bot-service/bot-service-overview-introduction?preserve-view=true&view=azure-bot-service-4.0).</span><span class="sxs-lookup"><span data-stu-id="9c662-120">Learn more about [Azure Bot Service](/azure/bot-service/bot-service-overview-introduction?preserve-view=true&view=azure-bot-service-4.0).</span></span>

## <a name="part-1---creating-the-bot"></a><span data-ttu-id="9c662-121">Parte 1 - Creazione del bot</span><span class="sxs-lookup"><span data-stu-id="9c662-121">Part 1 - Creating the Bot</span></span>

<span data-ttu-id="9c662-122">Prima di poter usare il bot nell'applicazione Unity, è necessario svilupparlo, fornirgli i dati e ospitarlo in **Azure**.</span><span class="sxs-lookup"><span data-stu-id="9c662-122">Before you can use the bot in the Unity application, you need to develope it, provide it with data and host it on **Azure**.</span></span>
<span data-ttu-id="9c662-123">L'obiettivo del bot è quello di poter indicare quanti *oggetti tracciati* sono archiviati nel database, trovare un *oggetto tracciato* in base al nome e fornire all'utente alcune informazioni di base relative a tale oggetto.</span><span class="sxs-lookup"><span data-stu-id="9c662-123">The goal of the bot is to have the abilities to tell how many *Tracked Objects* are stored in the database, find a *Tracked Object* by its name, and tell the user some basic information about it.</span></span>

### <a name="a-quick-look-into-tracked-objects-azure-function"></a><span data-ttu-id="9c662-124">Rapida descrizione della funzione di Azure relativa agli oggetti tracciati</span><span class="sxs-lookup"><span data-stu-id="9c662-124">A quick look into Tracked Objects Azure Function</span></span>

<span data-ttu-id="9c662-125">Stai per iniziare a creare il bot, ma per renderlo utile devi assegnargli una risorsa da cui possa eseguire il pull dei dati.</span><span class="sxs-lookup"><span data-stu-id="9c662-125">You are about to start creating the Bot, but to make it useful you need to give it a resource from which it can pull data.</span></span> <span data-ttu-id="9c662-126">Poiché il *bot* sarà in grado di contare il numero di **oggetti tracciati**, trovare oggetti specifici in base al nome e fornirne i dettagli, userai una semplice funzione di Azure che ha accesso all'**archivio tabelle di Azure**.</span><span class="sxs-lookup"><span data-stu-id="9c662-126">Since the *Bot* will be able to count the amount of **Tracked Objects**, find specific ones by name and tell details, you will use a simple Azure Function that has access to the **Azure Table storage**.</span></span>

<span data-ttu-id="9c662-127">Scaricare il progetto della funzione di Azure Tracked Objects: [AzureFunction_TrackedObjectsService.zip](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-cloud-services-v2.4.0/AzureFunction_TrackedObjectsService.zip) ed estrarlo nel disco rigido.</span><span class="sxs-lookup"><span data-stu-id="9c662-127">Download the Tracked Objects Azure Function project: [AzureFunction_TrackedObjectsService.zip](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-cloud-services-v2.4.0/AzureFunction_TrackedObjectsService.zip) and extract it to your hard drive.</span></span>

<span data-ttu-id="9c662-128">Questa funzione di Azure dispone di due azioni, **Count** e **Find**, che possono essere richiamate tramite chiamate *GET* *HTTP* di base.</span><span class="sxs-lookup"><span data-stu-id="9c662-128">This Azure Function has two actions, **Count** and **Find** which can be invoked via basic *HTTP* *GET* calls.</span></span> <span data-ttu-id="9c662-129">Puoi esaminare il codice in **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="9c662-129">You can inspect the code in **Visual Studio**.</span></span>

<span data-ttu-id="9c662-130">Scopri di più sulle [funzioni di Azure](/azure/azure-functions/functions-overview).</span><span class="sxs-lookup"><span data-stu-id="9c662-130">Learn more about [Azure Functions](/azure/azure-functions/functions-overview).</span></span>

<span data-ttu-id="9c662-131">La funzione **Count** esegue una query nell'**archivio tabelle** per recuperare tutti i **TrackedObject** dalla tabella: un concetto molto semplice.</span><span class="sxs-lookup"><span data-stu-id="9c662-131">The **Count** function queries from the **Table storage** all **TrackedObjects** from the table, very simple.</span></span> <span data-ttu-id="9c662-132">Dall'altra parte, la funzione **Find** accetta un parametro di query *name* dalla richiesta *GET*, esegue una query nell'**archivio tabelle** per trovare un **TrackedObject** corrispondente e restituisce un DTO come JSON.</span><span class="sxs-lookup"><span data-stu-id="9c662-132">On the other hand the **Find** function takes a *name* query parameter from the *GET* request and queries the **Table storage** for a matching **TrackedObject** and returns a DTO as JSON.</span></span>

<span data-ttu-id="9c662-133">Puoi distribuire questa **funzione di Azure** direttamente da **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="9c662-133">You can deploy this **Azure Function** directly from **Visual Studio**.</span></span>
<span data-ttu-id="9c662-134">Fai clic sul collegamento per accedere a tutte le informazioni relative alla [distribuzione di una funzione di Azure](/azure/devops/pipelines/targets/azure-functions?preserve-view=true&tabs=dotnet-core%2cyaml&view=azure-devops).</span><span class="sxs-lookup"><span data-stu-id="9c662-134">Find here all information regarding [Azure Function deployment](/azure/devops/pipelines/targets/azure-functions?preserve-view=true&tabs=dotnet-core%2cyaml&view=azure-devops).</span></span>

<span data-ttu-id="9c662-135">Una volta completata la distribuzione, nel **portale di Azure** apri la risorsa corrispondente e fai clic su **Configurazione** all'interno della sezione *Impostazioni*.</span><span class="sxs-lookup"><span data-stu-id="9c662-135">Once you have completed the deployment, in the **Azure Portal**, open the corresponding resource and click on **Configuration** which is under the *Settings* section.</span></span> <span data-ttu-id="9c662-136">In **Impostazioni applicazione** devi fornire la *stringa di connessione* all'**archivio di Azure** in cui si trovano gli **oggetti tracciati**.</span><span class="sxs-lookup"><span data-stu-id="9c662-136">There on **Application Settings** you need to provide the *Connection string* to the **Azure Storage** where the **Tracked Objects** are stored.</span></span> <span data-ttu-id="9c662-137">Fai clic su **Nuova impostazione applicazione**, quindi come nome usa **AzureStorageConnectionString** e come valore fornisci la *stringa di connessione* corretta.</span><span class="sxs-lookup"><span data-stu-id="9c662-137">Click on **New Application setting** and use for name: **AzureStorageConnectionString** and for value provide the correct *Connection string*.</span></span> <span data-ttu-id="9c662-138">Fai quindi clic su **Salva**. La **funzione di Azure** è ora pronta a servire il *bot* che creerai più avanti.</span><span class="sxs-lookup"><span data-stu-id="9c662-138">After that click on **Save** and the **Azure Function** is ready to server the *Bot* which you will create next.</span></span>

### <a name="creating-a-conversation-bot"></a><span data-ttu-id="9c662-139">Creazione di un bot conversazionale</span><span class="sxs-lookup"><span data-stu-id="9c662-139">Creating a conversation Bot</span></span>

<span data-ttu-id="9c662-140">Esistono diversi modi per sviluppare un bot conversazionale basato su Bot Framework.</span><span class="sxs-lookup"><span data-stu-id="9c662-140">There are several ways to develope a Bot Framework based conversational bot.</span></span> <span data-ttu-id="9c662-141">In questa lezione userai l'applicazione desktop [Bot Framework Composer](/composer/), ovvero una finestra di progettazione visiva ideale per lo sviluppo rapido.</span><span class="sxs-lookup"><span data-stu-id="9c662-141">In this lesson you will use the [Bot Framework Composer](/composer/) desktop application which is a visual designer that is perfect for rapid development.</span></span>

<span data-ttu-id="9c662-142">Puoi scaricare le versioni più recenti dal [repository di GitHub](https://github.com/microsoft/BotFramework-Composer/releases).</span><span class="sxs-lookup"><span data-stu-id="9c662-142">You can download the latest releases from the [Github repository](https://github.com/microsoft/BotFramework-Composer/releases).</span></span> <span data-ttu-id="9c662-143">È disponibile per Windows, Mac e Linux.</span><span class="sxs-lookup"><span data-stu-id="9c662-143">It is available for Windows, Mac, and Linux.</span></span>

<span data-ttu-id="9c662-144">Dopo aver installato **Bot Framework Composer**, avvia l'applicazione. Verrà visualizzata l'interfaccia seguente:</span><span class="sxs-lookup"><span data-stu-id="9c662-144">Once the **Bot Framework Composer** is installed, start the application and you should see this interface:</span></span>

![Home di Bot Framework Composer](images/mr-learning-azure/tutorial5-section4-step1-1.png)

<span data-ttu-id="9c662-146">È stato preparato un progetto per la creazione di bot che fornisce le finestre di dialogo e i trigger necessari per questa esercitazione.</span><span class="sxs-lookup"><span data-stu-id="9c662-146">We have prepared a bot composer project which provides the needed dialogues and triggers for this tutorial.</span></span> <span data-ttu-id="9c662-147">Scaricare il progetto di Bot Framework Composer: [BotComposerProject_TrackedObjectsBot.zip](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-cloud-services-v2.4.0/BotComposerProject_TrackedObjectsBot.zip) ed estrarlo nel disco rigido.</span><span class="sxs-lookup"><span data-stu-id="9c662-147">Download the Bot Framework Composer project: [BotComposerProject_TrackedObjectsBot.zip](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-cloud-services-v2.4.0/BotComposerProject_TrackedObjectsBot.zip) and extract it to your hard drive.</span></span>

<span data-ttu-id="9c662-148">Sulla barra superiore fai clic su **Open** (Apri) e seleziona il progetto Bot Framework scaricato, che è denominato **TrackedObjectsBot**.</span><span class="sxs-lookup"><span data-stu-id="9c662-148">On the top bar click on **Open** and select the Bot Framework project you have downloaded which is named **TrackedObjectsBot**.</span></span> <span data-ttu-id="9c662-149">Dopo che il progetto viene caricato completamente, dovresti vedere che è pronto.</span><span class="sxs-lookup"><span data-stu-id="9c662-149">After the project is fully loaded, you should see the project ready.</span></span>

![Bot Framework Composer con il progetto TrackedObjectsBot aperto](images/mr-learning-azure/tutorial5-section4-step1-2.png)

<span data-ttu-id="9c662-151">Guardando il lato sinistro, puoi vedere il **pannello delle finestre di dialogo**.</span><span class="sxs-lookup"><span data-stu-id="9c662-151">Let's focus on the left side where you can see the **Dialogs Panel**.</span></span> <span data-ttu-id="9c662-152">In tale area è presente una finestra di dialogo denominata **TrackedObjectsBot**, sotto il cui nome sono visibili diversi **trigger**.</span><span class="sxs-lookup"><span data-stu-id="9c662-152">There you have one dialog named **TrackedObjectsBot** under which you can see several **Triggers**.</span></span>

<span data-ttu-id="9c662-153">Scopri di più sui [concetti relativi a Bot Framework](/composer/concept-dialog).</span><span class="sxs-lookup"><span data-stu-id="9c662-153">Learn more about [Bot Framework concepts](/composer/concept-dialog).</span></span>

<span data-ttu-id="9c662-154">Questi trigger eseguono le operazioni descritte di seguito.</span><span class="sxs-lookup"><span data-stu-id="9c662-154">These triggers do the following:</span></span>

#### <a name="greeting"></a><span data-ttu-id="9c662-155">Greeting (Messaggio introduttivo)</span><span class="sxs-lookup"><span data-stu-id="9c662-155">Greeting</span></span>

<span data-ttu-id="9c662-156">Questo è il punto di ingresso del chat *bot* ogni volta che un *utente* avvia una conversazione.</span><span class="sxs-lookup"><span data-stu-id="9c662-156">This is the entry point of the chat *bot* when ever a *user* initiates a conversation.</span></span>

![Trigger di finestra di dialogo Greeting del progetto TrackedObjectsBot](images/mr-learning-azure/tutorial5-section4-step1-3.png)

#### <a name="askingforcount"></a><span data-ttu-id="9c662-158">AskingForCount</span><span class="sxs-lookup"><span data-stu-id="9c662-158">AskingForCount</span></span>

<span data-ttu-id="9c662-159">Questa finestra di dialogo viene attivata quando l'*utente* chiede di contare tutti gli **oggetti tracciati**.</span><span class="sxs-lookup"><span data-stu-id="9c662-159">This dialog is triggered when the *user* asks for counting all **Tracked Objects**.</span></span>
<span data-ttu-id="9c662-160">Le frasi trigger sono le seguenti:</span><span class="sxs-lookup"><span data-stu-id="9c662-160">These are the trigger phrases:</span></span>

>* <span data-ttu-id="9c662-161">count me all (conta tutto)</span><span class="sxs-lookup"><span data-stu-id="9c662-161">count me all</span></span>
>* <span data-ttu-id="9c662-162">how many are stored (quanti sono archiviati)</span><span class="sxs-lookup"><span data-stu-id="9c662-162">how many are stored</span></span>

![Trigger di finestra di dialogo AskForCount del progetto TrackedObjectsBot](images/mr-learning-azure/tutorial5-section4-step1-4.png)

<span data-ttu-id="9c662-164">Grazie a [LUIS](/composer/how-to-use-luis), non è necessario che l'*utente* esprima le frasi esattamente come farebbe in una conversazione naturale.</span><span class="sxs-lookup"><span data-stu-id="9c662-164">Thanks to [LUIS](/composer/how-to-use-luis) the *user* does not have to ask the phrases in that exact way which allows a natural conversation for the *user*.</span></span>

<span data-ttu-id="9c662-165">In questa finestra di dialogo il *bot* comunicherà anche con la funzione **Count** di Azure, per la quale più avanti sono disponibili altre informazioni.</span><span class="sxs-lookup"><span data-stu-id="9c662-165">In this dialog the *bot* will also talk to the **Count** Azure Function, more about that later.</span></span>

#### <a name="unknown-intent"></a><span data-ttu-id="9c662-166">Unknown Intent (Finalità sconosciuta)</span><span class="sxs-lookup"><span data-stu-id="9c662-166">Unknown Intent</span></span>

<span data-ttu-id="9c662-167">Questa finestra di dialogo viene attivata se l'input dell'*utente* non si adatta ad altre condizioni di trigger e risponde chiedendo all'utente di provare a riformulare la domanda.</span><span class="sxs-lookup"><span data-stu-id="9c662-167">This dialogue is triggered if the input from the *user* does not fit any other trigger condition and responses the user with trying his question again.</span></span>

![Trigger di finestra di dialogo Unknown Intent del progetto TrackedObjectsBot](images/mr-learning-azure/tutorial5-section4-step1-5.png)

#### <a name="findentity"></a><span data-ttu-id="9c662-169">FindEntity</span><span class="sxs-lookup"><span data-stu-id="9c662-169">FindEntity</span></span>

<span data-ttu-id="9c662-170">L'ultima finestra di dialogo è più complessa perché correlata alla creazione di rami e all'archiviazione dei dati nella memoria *bots*.</span><span class="sxs-lookup"><span data-stu-id="9c662-170">The last dialogue is more complex with branching and storing data in the *bots* memory.</span></span>
<span data-ttu-id="9c662-171">Chiede all'utente il *nome* dell'**oggetto tracciato** per cui vuole ottenere altre informazioni, esegue una query per la funzione **Find** di Azure e usa la risposta per procedere con la conversazione.</span><span class="sxs-lookup"><span data-stu-id="9c662-171">It asks the user for the *name* of the **Tracked Object** it want's to know more information about, performs a query to the **Find** Azure Function, and uses the response to proceed with the conversation.</span></span>

![Trigger di finestra di dialogo FindEntity del progetto TrackedObjectsBot](images/mr-learning-azure/tutorial5-section4-step1-6.png)

<span data-ttu-id="9c662-173">Se l'**oggetto tracciato** non viene trovato, l'utente viene informato e la conversazione termina.</span><span class="sxs-lookup"><span data-stu-id="9c662-173">If the **Tracked Object** is not found, the user is informed and the conversation ends.</span></span> <span data-ttu-id="9c662-174">Quando l'**oggetto tracciato** in questione viene trovato, vengono verificate e segnalate le proprietà disponibili.</span><span class="sxs-lookup"><span data-stu-id="9c662-174">When the **Tracked Object** in question is found, the boot will check what properties are available and report on them.</span></span>

### <a name="adapting-the-bot"></a><span data-ttu-id="9c662-175">Adattamento del bot</span><span class="sxs-lookup"><span data-stu-id="9c662-175">Adapting the Bot</span></span>

<span data-ttu-id="9c662-176">I trigger **AskingForCount** e **FindEntity** devono comunicare con il back-end, pertanto devi aggiungere l'URL corretto della **funzione di Azure** distribuita in precedenza.</span><span class="sxs-lookup"><span data-stu-id="9c662-176">The **AskingForCount** and **FindEntity** trigger need to talk to the backend, this means you have to add the correct URL of the **Azure Function** you deployed previously.</span></span>

<span data-ttu-id="9c662-177">Nel pannello delle finestre di dialogo fai clic su **AskingForCount** e individua l'azione *Send an HTTP request* (Invia una richiesta HTTP). Qui puoi vedere il campo **URL** in cui è necessario specificare l'URL corretto per l'endpoint della funzione **Count**.</span><span class="sxs-lookup"><span data-stu-id="9c662-177">On the dialog panel click on **AskingForCount** and locate the *Send an HTTP request* action, here you can see the field **URL** which you need to change the correct URL for the **Count** function endpoint.</span></span>

![Configurazione dell'endpoint del trigger di finestra di dialogo AskingForCount del progetto TrackedObjectsBot](images/mr-learning-azure/tutorial5-section5-step1-1.png)

<span data-ttu-id="9c662-179">Cerca infine il trigger **FindEntity** e individua l'azione *Send an HTTP request* (Invia una richiesta HTTP), quindi nel campo **URL** sostituisci l'URL corrente con l'endpoint della funzione **Find**.</span><span class="sxs-lookup"><span data-stu-id="9c662-179">Finally, look for the **FindEntity** trigger and locate the *Send an HTTP request* action, in the **URL** field change the URL to the **Find** function endpoint.</span></span>

![Configurazione dell'endpoint del trigger di finestra di dialogo FindEntity del progetto TrackedObjectsBot](images/mr-learning-azure/tutorial5-section5-step1-2.png)

<span data-ttu-id="9c662-181">Con tutti gli elementi impostati, ora sei pronto per distribuire il bot.</span><span class="sxs-lookup"><span data-stu-id="9c662-181">With everything set you are now ready to deploy the Bot.</span></span> <span data-ttu-id="9c662-182">Poiché Bot Framework Composer è installato, puoi pubblicare il bot direttamente da tale posizione.</span><span class="sxs-lookup"><span data-stu-id="9c662-182">Since you have Bot Framework composer installed, you can publish it directly from there.</span></span>

<span data-ttu-id="9c662-183">Scopri di più su come [pubblicare un bot da Bot Composer](/composer/how-to-publish-bot).</span><span class="sxs-lookup"><span data-stu-id="9c662-183">Learn more about [Publish a bot from Bot Composer](/composer/how-to-publish-bot).</span></span>

> [!TIP]
> <span data-ttu-id="9c662-184">Se vuoi, puoi provare a usare il bot aggiungendo frasi trigger diverse, nuove risposte o altri rami di conversazione.</span><span class="sxs-lookup"><span data-stu-id="9c662-184">Feel free playing around with Bot by adding more trigger phrases, new responses or conversation branching.</span></span>

## <a name="part-2---putting-everything-together-in-unity"></a><span data-ttu-id="9c662-185">Parte 2 - Integrazione di tutti gli elementi in Unity</span><span class="sxs-lookup"><span data-stu-id="9c662-185">Part 2 - Putting everything together in Unity</span></span>

### <a name="preparing-the-scene"></a><span data-ttu-id="9c662-186">Preparazione della scena</span><span class="sxs-lookup"><span data-stu-id="9c662-186">Preparing the scene</span></span>

<span data-ttu-id="9c662-187">Nella finestra Project (Progetto) passa alla cartella **Assets** (Asset)  > **MRTK.Tutorials.AzureCloudServices** > **Prefabs** (Prefab)  > **Manager**.</span><span class="sxs-lookup"><span data-stu-id="9c662-187">In the Project window, navigate to **Assets** > **MRTK.Tutorials.AzureCloudServices** > **Prefabs** > **Manager** folder.</span></span>

![Finestra Project di Unity con il prefab ChatBotManager selezionato](images/mr-learning-azure/tutorial5-section6-step1-1.png)

<span data-ttu-id="9c662-189">Da questa posizione, sposta il prefab **ChatBotManager** nella gerarchia della scena.</span><span class="sxs-lookup"><span data-stu-id="9c662-189">From there move the prefab **ChatBotManager** into the scene Hierarchy.</span></span>

<span data-ttu-id="9c662-190">Una volta aggiunto ChatBotManager alla scena, fai clic sul componente **Chat Bot Manager** (Manager chat bot).</span><span class="sxs-lookup"><span data-stu-id="9c662-190">Once you add the ChatBotManager to the scene, click on the **Chat Bot Manager** component.</span></span>
<span data-ttu-id="9c662-191">Nella finestra Inspector (Controllo) noterai che è presente un campo **Direct Line Secret Key** (Chiave privata Direct Line) vuoto da completare.</span><span class="sxs-lookup"><span data-stu-id="9c662-191">In the Inspector you will see that there is an empty **Direct Line Secret Key** field which you need to fill out.</span></span>

> [!TIP]
> <span data-ttu-id="9c662-192">Puoi recuperare la *chiave privata* dal portale di Azure cercando la risorsa di tipo **Registrazione canali bot** creata nella prima parte di questa esercitazione.</span><span class="sxs-lookup"><span data-stu-id="9c662-192">You can retrieve the *secret key* from the Azure portal by looking for the resource of type **Bot Channels Registration** you have created in the first part of this tutorial.</span></span>

![Unity con il nuovo prefab ChatBotManager aggiunto ancora selezionato](images/mr-learning-azure/tutorial5-section6-step1-2.png)

<span data-ttu-id="9c662-194">A questo punto connetterai l'oggetto **ChatBotManager** al componente **ChatBotController** collegato all'oggetto **ChatBotPanel**.</span><span class="sxs-lookup"><span data-stu-id="9c662-194">Now you will connect the **ChatBotManager** object with the **ChatBotController** component that is attached to the **ChatBotPanel** object.</span></span> <span data-ttu-id="9c662-195">In Hierarchy (Gerarchia) seleziona **ChatBotPanel** per visualizzare un campo **Chat Bot Manager** (Manager chat bot) vuoto. Dalla gerarchia trascina l'oggetto **ChatBotManager** nel campo **Chat Bot Manager** (Manager chat bot) vuoto.</span><span class="sxs-lookup"><span data-stu-id="9c662-195">In the Hierarchy select the **ChatBotPanel** and you will see an empty **Chat Bot Manager** field, drag from the Hierarchy the **ChatBotManager** object into the empty **Chat Bot Manager** field.</span></span>

![Unity con ChatBotPanel configurato](images/mr-learning-azure/tutorial5-section6-step1-3.png)

<span data-ttu-id="9c662-197">A questo punto, è necessario un modo per aprire **ChatBotPanel** affinché l'utente possa interagire con esso.</span><span class="sxs-lookup"><span data-stu-id="9c662-197">Next you need a way to open the **ChatBotPanel** so that the user can interact with it.</span></span> <span data-ttu-id="9c662-198">Nella finestra della scena è possibile che tu abbia notato la presenza di un pulsante laterale *Chat Bot* nell'oggetto **MainMenu**. Sarà necessario usarlo per risolvere il problema.</span><span class="sxs-lookup"><span data-stu-id="9c662-198">From the Scene window you may have noticed that there is a *Chat Bot* side button on the **MainMenu** object, you will use it to solve this problem.</span></span>

<span data-ttu-id="9c662-199">In Hierarchy (Gerarchia) individua **RootMenu** > **MainMenu** > **SideButtonCollection** > **ButtonChatBot**, quindi in Inspector (Controllo) individua lo script *ButtonConfigHelper*.</span><span class="sxs-lookup"><span data-stu-id="9c662-199">In the Hierarchy locate **RootMenu** > **MainMenu** > **SideButtonCollection** > **ButtonChatBot** and locate in the Inspector the *ButtonConfigHelper* script.</span></span> <span data-ttu-id="9c662-200">Qui vedrai uno slot vuoto nel callback dell'evento **OnClick()** .</span><span class="sxs-lookup"><span data-stu-id="9c662-200">There you will see an empty slot on the **OnClick()** event callback.</span></span> <span data-ttu-id="9c662-201">Trascina e rilascia **ChatBotPanel** nello slot dell'evento, dall'elenco a discesa passa a *GameObject*, quindi scegli *SetActive (bool)* nel sottomenu e abilita la casella di controllo.</span><span class="sxs-lookup"><span data-stu-id="9c662-201">Drag and drop the **ChatBotPanel** to the event slot, from the dropdown list navigate *GameObject*, then select in the sub menu *SetActive (bool)* and enable the checkbox.</span></span>

![Unity con ButtonChatBot configurato](images/mr-learning-azure/tutorial5-section6-step1-4.png)

<span data-ttu-id="9c662-203">Ora il chat bot è visibile dal menu principale e la scena è pronta per l'uso.</span><span class="sxs-lookup"><span data-stu-id="9c662-203">Now the chat bot can be stared from the main menu and with that the scene is ready for use.</span></span>

### <a name="putting-the-bot-to-a-test"></a><span data-ttu-id="9c662-204">Esecuzione di un test con il bot</span><span class="sxs-lookup"><span data-stu-id="9c662-204">Putting the bot to a test</span></span>

#### <a name="asking-about-the-quantity-of-tracked-objects"></a><span data-ttu-id="9c662-205">Chiedere il numero di oggetti tracciati</span><span class="sxs-lookup"><span data-stu-id="9c662-205">Asking about the quantity of tracked objects</span></span>

<span data-ttu-id="9c662-206">Esegui il test innanzitutto chiedendo al bot quanti **oggetti tracciati** sono archiviati nel database.</span><span class="sxs-lookup"><span data-stu-id="9c662-206">First you test asking the bot how many **Tracked Objects** are stored in the database.</span></span>

> [!NOTE]
> <span data-ttu-id="9c662-207">Questa volta è necessario eseguire l'applicazione da HoloLens 2 perché i servizi come la *sintesi vocale* potrebbero non essere disponibili nel sistema.</span><span class="sxs-lookup"><span data-stu-id="9c662-207">This time you must run the application from the HoloLens 2 because services like *text-to-speech* may not be available on your system.</span></span>

<span data-ttu-id="9c662-208">Esegui l'applicazione in HoloLens 2 e fai clic sul pulsante *Chat Bot* accanto al menu principale.</span><span class="sxs-lookup"><span data-stu-id="9c662-208">Run the application on your HoloLens 2 and click on the *Chat Bot* button next to the main menu.</span></span>
<span data-ttu-id="9c662-209">Il bot visualizzerà il messaggio introduttivo. A questo punto chiedi **di quanti oggetti disponi**.</span><span class="sxs-lookup"><span data-stu-id="9c662-209">The bot will be greeting you, now ask **how many objects do we have?**</span></span>
<span data-ttu-id="9c662-210">Il bot dovrebbe indicare il numero e terminare la conversazione.</span><span class="sxs-lookup"><span data-stu-id="9c662-210">It should tell you the quantity and end the conversation.</span></span>

#### <a name="asking-about-a-tracked-object"></a><span data-ttu-id="9c662-211">Chiedere informazioni relative a un oggetto tracciato</span><span class="sxs-lookup"><span data-stu-id="9c662-211">Asking about a tracked object</span></span>

<span data-ttu-id="9c662-212">Ora esegui di nuovo l'applicazione e questa volta chiedi di **trovare un oggetto tracciato**. Il bot ti chiederà il nome, quindi dovrai rispondere con il termine "car" (automobile) o con il nome di un altro *oggetto tracciato* sicuramente presente nel database.</span><span class="sxs-lookup"><span data-stu-id="9c662-212">Now run the application again and this time ask **find me a tracked object**, the bot will be asking you the name to which you should respond with the "car" or the name of an other *Tracked Object* you know exists in the database.</span></span> <span data-ttu-id="9c662-213">Il bot indicherà i dettagli, ad esempio la descrizione e l'eventuale assegnazione di un ancoraggio nello spazio.</span><span class="sxs-lookup"><span data-stu-id="9c662-213">The bot will tell you details like description and if it has a spatial anchor assigned.</span></span>

> [!TIP]
> <span data-ttu-id="9c662-214">Prova a chiedere di un **oggetto tracciato** inesistente e senti come risponde il bot.</span><span class="sxs-lookup"><span data-stu-id="9c662-214">Try out asking for an **Tracked Objects** that does not exist and hear how the bot responds.</span></span>

## <a name="congratulations"></a><span data-ttu-id="9c662-215">Lezione completata</span><span class="sxs-lookup"><span data-stu-id="9c662-215">Congratulations</span></span>

<span data-ttu-id="9c662-216">In questa esercitazione hai appreso come usare Azure Bot Framework per interagire con l'applicazione tramite conversazione nel linguaggio naturale.</span><span class="sxs-lookup"><span data-stu-id="9c662-216">In this tutorial you learned how Azure Bot Framework can be used to interact with the application via conversation with natural language.</span></span> <span data-ttu-id="9c662-217">Si è imparato come sviluppare il bot e quali sono i diversi elementi che gli consentono di funzionare.</span><span class="sxs-lookup"><span data-stu-id="9c662-217">You learned how to develop your own bot and what all the moving pieces are to get it running,</span></span>

## <a name="conclusion"></a><span data-ttu-id="9c662-218">Conclusione</span><span class="sxs-lookup"><span data-stu-id="9c662-218">Conclusion</span></span>

<span data-ttu-id="9c662-219">Nel corso di questa serie di esercitazioni hai sperimentato in che modo i **servizi cloud di Azure** hanno consentito di introdurre nuove e interessanti funzionalità nella tua applicazione.</span><span class="sxs-lookup"><span data-stu-id="9c662-219">Through the course of this tutorial series you experienced how **Azure Cloud services** brought new and exciting features to your application.</span></span>
<span data-ttu-id="9c662-220">Ora puoi archiviare dati e immagini nel cloud con **Archiviazione di Azure**, usare **Visione personalizzata di Azure** per associare le immagini ed eseguire il training di un modello, riunire gli oggetti in un contesto locale con gli **ancoraggi nello spazio di Azure** e implementare **Azure Bot Framework con tecnologia LUIS** per aggiungere un bot conversazionale per un modello di interazione nuovo e naturale.</span><span class="sxs-lookup"><span data-stu-id="9c662-220">You can now store data and images in the cloud with **Azure Storage**, use **Azure Custom Vision** to associate images and train a model, bring objects to a local context with **Azure Spatial Anchors**, and implement **Azure Bot Framework powered by LUIS** to add a conversational bot for a new and natural interaction pattern.</span></span>
---
title: Integrazione del servizio Azure Bot con LUIS
description: Completa questo corso per apprendere come implementare il servizio Azure Bot e il riconoscimento del linguaggio naturale in un'applicazione HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens, hololens 2, servizio azure bot, luis, linguaggio naturale, bot conversazione, servizi cloud di azure, visione personalizzata di azure, Windows 10
ms.localizationpriority: high
ms.openlocfilehash: bade124dff639e6f30fb67039debfddef54a22db
ms.sourcegitcommit: 114c304a416bfe9d9b294c4adbb4c23cbe60ea4e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/15/2021
ms.locfileid: "114224525"
---
# <a name="5-integrating-azure-bot-service"></a>5. Integrazione del servizio Azure Bot

In questa esercitazione apprenderai come usare il **servizio Azure Bot** nell'applicazione demo **HoloLens 2** per aggiungere Language Understanding (LUIS), consentendo al bot di assistere l'utente durante la ricerca di **oggetti tracciati**. Si tratta di un'esercitazione in due parti, in cui nella prima parte creerai il bot tramite [Bot Composer](/composer/introduction) come soluzione senza codice e avrai una rapida descrizione della funzione di Azure che fornisce al bot i dati necessari. Nella seconda parte userai **BotManager (script)** nel progetto Unity per utilizzare il servizio Bot ospitato.

## <a name="objectives"></a>Obiettivi

## <a name="part-1"></a>Parte 1

* Apprendere le nozioni di base relative al servizio Azure Bot
* Apprendere come usare Bot Composer per creare un bot
* Apprendere come usare una funzione di Azure per fornire dati dall'archivio di Azure

## <a name="part-2"></a>Parte 2

* Apprendere come impostare la scena per l'uso del servizio Azure Bot in questo progetto
* Apprendere come impostare e trovare oggetti tramite conversazione con il bot

## <a name="understanding-azure-bot-service"></a>Informazioni sul servizio Azure Bot

Il **servizio Azure Bot** consente agli sviluppatori di creare bot intelligenti in grado di avere una conversazione naturale con gli utenti grazie a **LUIS**. Un bot conversazionale è un ottimo mezzo per espandere i modi in cui un utente può interagire con l'applicazione. Un bot può infatti fungere da knowledge base con [QnA Maker](/azure/bot-service/bot-builder-howto-qna?preserve-view=true&tabs=cs&view=azure-bot-service-4.0) per gestire una conversazione complessa con le potenzialità di [Language Understanding (LUIS)](/azure/bot-service/bot-builder-howto-v4-luis?preserve-view=true&tabs=csharp&view=azure-bot-service-4.0).

Scopri di più sul [servizio Azure Bot](/azure/bot-service/bot-service-overview-introduction?preserve-view=true&view=azure-bot-service-4.0).

## <a name="part-1---creating-the-bot"></a>Parte 1 - Creazione del bot

Prima di poter usare il bot nell'applicazione Unity, è necessario svilupparlo, fornirgli i dati e ospitarlo in **Azure**.
L'obiettivo del bot è quello di poter indicare quanti *oggetti tracciati* sono archiviati nel database, trovare un *oggetto tracciato* in base al nome e fornire all'utente alcune informazioni di base relative a tale oggetto.

### <a name="a-quick-look-into-tracked-objects-azure-function"></a>Rapida descrizione della funzione di Azure relativa agli oggetti tracciati

Stai per iniziare a creare il bot, ma per renderlo utile devi assegnargli una risorsa da cui possa eseguire il pull dei dati. Poiché il *bot* sarà in grado di contare il numero di **oggetti tracciati**, trovare oggetti specifici in base al nome e fornirne i dettagli, userai una semplice funzione di Azure che ha accesso all'**archivio tabelle di Azure**.

Scaricare il progetto della funzione di Azure Tracked Objects: [AzureFunction_TrackedObjectsService.zip](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-cloud-services-v2.4.0/AzureFunction_TrackedObjectsService.zip) ed estrarlo nel disco rigido.

Questa funzione di Azure dispone di due azioni, **Count** e **Find**, che possono essere richiamate tramite chiamate *GET* *HTTP* di base. Puoi esaminare il codice in **Visual Studio**.

Scopri di più sulle [funzioni di Azure](/azure/azure-functions/functions-overview).

La funzione **Count** esegue una query nell'**archivio tabelle** per recuperare tutti i **TrackedObject** dalla tabella: un concetto molto semplice. Dall'altra parte, la funzione **Find** accetta un parametro di query *name* dalla richiesta *GET*, esegue una query nell'**archivio tabelle** per trovare un **TrackedObject** corrispondente e restituisce un DTO come JSON.

Per distribuire questa **funzione di Azure** direttamente da **Visual Studio**, aprire la cartella AzureFunction_TrackedObjectsService scaricata e aprire il file con estensione **sln** corrente con la cartella AzureFunction_TrackedObjectsService visual ![ studio](images/mr-learning-azure/tutorial5-section3-step1-1.png)

Dopo aver caricato il file in Visual Studio, fare clic con il pulsante destro del mouse su **Tracked object sevice** (Oggetto tracciato) in Esplora soluzioni e selezionare Publish Publish Tracked object service (Pubblica servizio ![ oggetti tracciati)](images/mr-learning-azure/tutorial5-section3-step1-2.png)

Verrà visualizzato il popup di pubblicazione e verrà chiesto di selezionare azure come destinazione e fare clic sul **pulsante** Avanti

![Selezionare la piattaforma di destinazione](images/mr-learning-azure/tutorial5-section3-step1-3.png)

Nella destinazione specifica selezionare **App per le funzioni di Azure (Windows)** e fare clic sul **pulsante** Avanti

![Selezionare l'host di destinazione](images/mr-learning-azure/tutorial5-section3-step1-4.png)

Se non si è connessi ad Azure, accedere tramite Visual Studio e la finestra sarà simile a

![Selezionare o creare una funzione di Azure](images/mr-learning-azure/tutorial5-section3-step1-5.png)

Fare clic sul pulsante pulse per creare una nuova app per le funzioni nell'account Azure

![Creare una nuova app per le funzioni](images/mr-learning-azure/tutorial5-section3-step1-6.png)

* Per **Nome** immettere un nome appropriato per il servizio, ad esempio *TrackedObjectsService*
* Per **Tipo di piano** scegliere consumo
* Per **Località** scegliere una località vicina alla posizione fisica degli utenti dell'app, ad esempio *(Stati Uniti) Stati Uniti occidentali*
* Per **Gruppo di risorse** e **Archiviazione**, scegliere il gruppo di Azure e l'account di archiviazione corrispondenti creati in capitoli successivi.

Dopo aver creato l'app per le funzioni, **fare clic sul pulsante** Fine.

![Completare la creazione dell'app per le funzioni](images/mr-learning-azure/tutorial5-section3-step1-7.png)

Per aggiornare la stringa di connessione, **fare clic su 3 puntini nella** scheda di **hosting** e selezionare Gestisci **Servizio app di Azure impostazioni**

![aprire Impostazioni applicazione](images/mr-learning-azure/tutorial5-section3-step1-8.png)

Si aprirà **la finestra Impostazioni** di connessione dell'applicazione e si udirà la sostituzione di AzureStorageConnectionString sia per **Local** che **per Remote** con AzureStorageConnectionString. Dopo la sostituzione, fare clic su OK.

![aggiornare la stringa di connessione](images/mr-learning-azure/tutorial5-section3-step1-8a.png)

A questo punto, fare **clic sul pulsante** Pubblica per pubblicare la funzione e attendere la pubblicazione.

Al termine della pubblicazione, fare clic su Gestisci **in portale di Azure** nella sezione Azioni per  accedere a una funzione specifica nel portale di Azure e fare clic su Configurazione nella sezione *Impostazioni.* In **Impostazioni applicazione** devi fornire la *stringa di connessione* all'**archivio di Azure** in cui si trovano gli **oggetti tracciati**. Fai clic su **Nuova impostazione applicazione**, quindi come nome usa **AzureStorageConnectionString** e come valore fornisci la *stringa di connessione* corretta. Fai quindi clic su **Salva**. La **funzione di Azure** è ora pronta a servire il *bot* che creerai più avanti.

Per ottenere l'URL di count e Find, **selezionare Funzioni** nella *sezione* Funzioni. Qui è possibile trovare sia la funzione Count che la funzione Find, selezionare La funzione Count nella parte superiore è possibile trovare il *pulsante Get Function Url (Ottieni URL funzione).*
Seguire la stessa procedura per ottenere l'URL della funzione Find.

### <a name="creating-a-conversation-bot"></a>Creazione di un bot conversazionale

Esistono diversi modi per sviluppare un bot Bot Framework basato su un bot di conversazione. In questa lezione userai l'applicazione desktop [Bot Framework Composer](/composer/), ovvero una finestra di progettazione visiva ideale per lo sviluppo rapido.

Puoi scaricare le versioni più recenti dal [repository di GitHub](https://github.com/microsoft/BotFramework-Composer/releases). È disponibile per Windows, Mac e Linux.

Dopo aver installato **Bot Framework Composer**, avvia l'applicazione. Verrà visualizzata l'interfaccia seguente:

![Home di Bot Framework Composer](images/mr-learning-azure/tutorial5-section4-step1-1.png)

È stato preparato un progetto per la creazione di bot che fornisce le finestre di dialogo e i trigger necessari per questa esercitazione. Scaricare il progetto di Bot Framework Composer: [BotComposerProject_TrackedObjectsBot.zip](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-cloud-services-v2.4.0/BotComposerProject_TrackedObjectsBot.zip) ed estrarlo nel disco rigido.

Sulla barra superiore fai clic su **Open** (Apri) e seleziona il progetto Bot Framework scaricato, che è denominato **TrackedObjectsBot**. Dopo che il progetto viene caricato completamente, dovresti vedere che è pronto.

![Bot Framework Composer con il progetto TrackedObjectsBot aperto](images/mr-learning-azure/tutorial5-section4-step1-2.png)

Guardando il lato sinistro, puoi vedere il **pannello delle finestre di dialogo**. In tale area è presente una finestra di dialogo denominata **TrackedObjectsBot**, sotto il cui nome sono visibili diversi **trigger**.

Scopri di più sui [concetti relativi a Bot Framework](/composer/concept-dialog).

Questi trigger eseguono le operazioni descritte di seguito.

#### <a name="greeting"></a>Greeting (Messaggio introduttivo)

Questo è il punto di ingresso del chat *bot* ogni volta che un *utente* avvia una conversazione.

![Trigger di finestra di dialogo Greeting del progetto TrackedObjectsBot](images/mr-learning-azure/tutorial5-section4-step1-3.png)

#### <a name="askingforcount"></a>AskingForCount

Questa finestra di dialogo viene attivata quando l'*utente* chiede di contare tutti gli **oggetti tracciati**.
Le frasi trigger sono le seguenti:

>* count me all (conta tutto)
>* how many are stored (quanti sono archiviati)

![Trigger di finestra di dialogo AskForCount del progetto TrackedObjectsBot](images/mr-learning-azure/tutorial5-section4-step1-4.png)

Grazie a [LUIS](/composer/how-to-use-luis), non è necessario che l'*utente* esprima le frasi esattamente come farebbe in una conversazione naturale.

In questa finestra di dialogo il *bot* comunicherà anche con la funzione **Count** di Azure, per la quale più avanti sono disponibili altre informazioni.

#### <a name="unknown-intent"></a>Unknown Intent (Finalità sconosciuta)

Questa finestra di dialogo viene attivata se l'input dell'*utente* non si adatta ad altre condizioni di trigger e risponde chiedendo all'utente di provare a riformulare la domanda.

![Trigger di finestra di dialogo Unknown Intent del progetto TrackedObjectsBot](images/mr-learning-azure/tutorial5-section4-step1-5.png)

#### <a name="findentity"></a>FindEntity

L'ultima finestra di dialogo è più complessa perché correlata alla creazione di rami e all'archiviazione dei dati nella memoria *bots*.
Chiede all'utente il *nome* dell'**oggetto tracciato** per cui vuole ottenere altre informazioni, esegue una query per la funzione **Find** di Azure e usa la risposta per procedere con la conversazione.

![Trigger di finestra di dialogo FindEntity del progetto TrackedObjectsBot](images/mr-learning-azure/tutorial5-section4-step1-6.png)

Se l'**oggetto tracciato** non viene trovato, l'utente viene informato e la conversazione termina. Quando l'**oggetto tracciato** in questione viene trovato, vengono verificate e segnalate le proprietà disponibili.

### <a name="adapting-the-bot"></a>Adattamento del bot

I trigger **AskingForCount** e **FindEntity** devono comunicare con il back-end, pertanto devi aggiungere l'URL corretto della **funzione di Azure** distribuita in precedenza.

Nel pannello delle finestre di dialogo fai clic su **AskingForCount** e individua l'azione *Send an HTTP request* (Invia una richiesta HTTP). Qui puoi vedere il campo **URL** in cui è necessario specificare l'URL corretto per l'endpoint della funzione **Count**.

![Configurazione dell'endpoint del trigger di finestra di dialogo AskingForCount del progetto TrackedObjectsBot](images/mr-learning-azure/tutorial5-section5-step1-1.png)

Cerca infine il trigger **FindEntity** e individua l'azione *Send an HTTP request* (Invia una richiesta HTTP), quindi nel campo **URL** sostituisci l'URL corrente con l'endpoint della funzione **Find**.

![Configurazione dell'endpoint del trigger di finestra di dialogo FindEntity del progetto TrackedObjectsBot](images/mr-learning-azure/tutorial5-section5-step1-2.png)

Con tutti gli elementi impostati, ora sei pronto per distribuire il bot. Poiché Bot Framework Composer è installato, puoi pubblicare il bot direttamente da tale posizione.

Scopri di più su come [pubblicare un bot da Bot Composer](/composer/how-to-publish-bot).

> [!TIP]
> Se vuoi, puoi provare a usare il bot aggiungendo frasi trigger diverse, nuove risposte o altri rami di conversazione.

## <a name="part-2---putting-everything-together-in-unity"></a>Parte 2 - Integrazione di tutti gli elementi in Unity

### <a name="preparing-the-scene"></a>Preparazione della scena

Nella finestra Project (Progetto) passa alla cartella **Assets** (Asset)  > **MRTK.Tutorials.AzureCloudServices** > **Prefabs** (Prefab)  > **Manager**.

![Finestra Project di Unity con il prefab ChatBotManager selezionato](images/mr-learning-azure/tutorial5-section6-step1-1.png)

Da questa posizione, sposta il prefab **ChatBotManager** nella gerarchia della scena.

Una volta aggiunto ChatBotManager alla scena, fai clic sul componente **Chat Bot Manager** (Manager chat bot).
Nella finestra Inspector (Controllo) noterai che è presente un campo **Direct Line Secret Key** (Chiave privata Direct Line) vuoto da completare.

> [!TIP]
> Puoi recuperare la *chiave privata* dal portale di Azure cercando la risorsa di tipo **Registrazione canali bot** creata nella prima parte di questa esercitazione.

![Unity con il nuovo prefab ChatBotManager aggiunto ancora selezionato](images/mr-learning-azure/tutorial5-section6-step1-2.png)

A questo punto connetterai l'oggetto **ChatBotManager** al componente **ChatBotController** collegato all'oggetto **ChatBotPanel**. In Hierarchy (Gerarchia) seleziona **ChatBotPanel** per visualizzare un campo **Chat Bot Manager** (Manager chat bot) vuoto. Dalla gerarchia trascina l'oggetto **ChatBotManager** nel campo **Chat Bot Manager** (Manager chat bot) vuoto.

![Unity con ChatBotPanel configurato](images/mr-learning-azure/tutorial5-section6-step1-3.png)

A questo punto, è necessario un modo per aprire **ChatBotPanel** affinché l'utente possa interagire con esso. Nella finestra della scena è possibile che tu abbia notato la presenza di un pulsante laterale *Chat Bot* nell'oggetto **MainMenu**. Sarà necessario usarlo per risolvere il problema.

In Hierarchy (Gerarchia) individua **RootMenu** > **MainMenu** > **SideButtonCollection** > **ButtonChatBot**, quindi in Inspector (Controllo) individua lo script *ButtonConfigHelper*. Qui vedrai uno slot vuoto nel callback dell'evento **OnClick()** . Trascina e rilascia **ChatBotPanel** nello slot dell'evento, dall'elenco a discesa passa a *GameObject*, quindi scegli *SetActive (bool)* nel sottomenu e abilita la casella di controllo.

![Unity con ButtonChatBot configurato](images/mr-learning-azure/tutorial5-section6-step1-4.png)

Ora il chat bot è visibile dal menu principale e la scena è pronta per l'uso.

### <a name="putting-the-bot-to-a-test"></a>Esecuzione di un test con il bot

#### <a name="asking-about-the-quantity-of-tracked-objects"></a>Chiedere il numero di oggetti tracciati

Esegui il test innanzitutto chiedendo al bot quanti **oggetti tracciati** sono archiviati nel database.

> [!NOTE]
> Questa volta è necessario eseguire l'applicazione da HoloLens 2 perché i servizi come la *sintesi vocale* potrebbero non essere disponibili nel sistema.

Esegui l'applicazione in HoloLens 2 e fai clic sul pulsante *Chat Bot* accanto al menu principale.
Il bot visualizzerà il messaggio introduttivo. A questo punto chiedi **di quanti oggetti disponi**.
Il bot dovrebbe indicare il numero e terminare la conversazione.

#### <a name="asking-about-a-tracked-object"></a>Chiedere informazioni relative a un oggetto tracciato

Ora esegui di nuovo l'applicazione e questa volta chiedi di **trovare un oggetto tracciato**. Il bot ti chiederà il nome, quindi dovrai rispondere con il termine "car" (automobile) o con il nome di un altro *oggetto tracciato* sicuramente presente nel database. Il bot indicherà i dettagli, ad esempio la descrizione e l'eventuale assegnazione di un ancoraggio nello spazio.

> [!TIP]
> Prova a chiedere di un **oggetto tracciato** inesistente e senti come risponde il bot.

## <a name="congratulations"></a>Lezione completata

In questa esercitazione hai appreso come usare Azure Bot Framework per interagire con l'applicazione tramite conversazione nel linguaggio naturale. Si è imparato come sviluppare il bot e quali sono i diversi elementi che gli consentono di funzionare.

## <a name="conclusion"></a>Conclusione

Nel corso di questa serie di esercitazioni hai sperimentato in che modo i **servizi cloud di Azure** hanno consentito di introdurre nuove e interessanti funzionalità nella tua applicazione.
Ora puoi archiviare dati e immagini nel cloud con **Archiviazione di Azure**, usare **Visione personalizzata di Azure** per associare le immagini ed eseguire il training di un modello, riunire gli oggetti in un contesto locale con gli **ancoraggi nello spazio di Azure** e implementare **Azure Bot Framework con tecnologia LUIS** per aggiungere un bot conversazionale per un modello di interazione nuovo e naturale.
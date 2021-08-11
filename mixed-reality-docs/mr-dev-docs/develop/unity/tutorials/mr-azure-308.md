---
title: HoloLens (prima generazione) e Azure 308 - Notifiche tra dispositivi
description: Completare questo corso per informazioni su come implementare Hub di notifica di Azure, Funzioni di Azure e Archiviazione di Azure e tabelle all'interno di un'applicazione di realtà mista.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure, realtà mista, academy, unity, esercitazione, api, notifica, funzioni, tabelle, hub di notifica, hololens, immersive, vr, Windows 10, Visual Studio
ms.openlocfilehash: 01d096297a9fbe25d39b2846acd2ee89b50edcfd26456f3f20ccd2c9bc26b514
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115205531"
---
# <a name="hololens-1st-gen-and-azure-308-cross-device-notifications"></a>HoloLens (prima generazione) e Azure 308: Notifiche tra dispositivi

<br>

>[!NOTE]
>Le esercitazioni di Mixed Reality Academy sono state progettate in base a HoloLens (prima generazione) e ai visori VR immersive di realtà mista.  Pertanto, riteniamo importante lasciarle a disposizione degli sviluppatori a cui serve ancora materiale sussidiario per lo sviluppo di questi dispositivi.  Queste esercitazioni **_non_** verranno aggiornate con i set di strumenti o le interazioni più recenti usati per HoloLens 2.  Rimarranno invariate per consentire di continuare a lavorare sui dispositivi supportati. In futuro verrà pubblicata una nuova serie di esercitazioni che illustrano come sviluppare per HoloLens 2.  Questa comunicazione verrà aggiornata con un collegamento a tali esercitazioni al momento della pubblicazione.

<br>

![final product -start](images/AzureLabs-Lab8-00.png)

In questo corso si apprenderà come aggiungere funzionalità di Hub di notifica a un'applicazione di realtà mista usando Hub di notifica di Azure, Tabelle di Azure e Funzioni di Azure.

**Hub di notifica di Azure** è un servizio Microsoft che consente agli sviluppatori di inviare notifiche push mirate e personalizzate a qualsiasi piattaforma, tutte basate sul cloud. In questo modo gli sviluppatori possono comunicare con gli utenti finali o persino tra diverse applicazioni, a seconda dello scenario. Per altre informazioni, visitare la pagina **Hub di notifica di** [Azure](/azure/notification-hubs/notification-hubs-push-notification-overview).

**Funzioni di Azure** è un servizio Microsoft che consente agli sviluppatori di eseguire piccole parti di codice, "funzioni", in Azure. In questo modo è possibile delegare il lavoro al cloud, anziché all'applicazione locale, che può avere molti vantaggi. **Funzioni di Azure** supporta diversi linguaggi di sviluppo, tra cui \# \# C, F, Node.js, Java e PHP. Per altre informazioni, visitare la **Funzioni di Azure** [pagina](/azure/azure-functions/functions-overview).

**Tabelle di Azure** è un servizio cloud Microsoft che consente agli sviluppatori di archiviare dati non SQL strutturati nel cloud, rendendoli facilmente accessibili ovunque. Il servizio offre una progettazione senza schema, consentendo l'evoluzione delle tabelle in base alle esigenze e pertanto è molto flessibile. Per altre informazioni, visitare la pagina **Tabelle di** [Azure](/azure/cosmos-db/table-storage-overview)

Dopo aver completato questo corso, si avranno un'applicazione per visori VR immersive di realtà mista e un'applicazione per PC desktop, che sarà in grado di eseguire le operazioni seguenti:

1. L'app PC desktop consentirà all'utente di spostare un oggetto nello spazio 2D (X e Y), usando il mouse.

2. Lo spostamento di oggetti all'interno dell'app pc verrà inviato al cloud usando JSON, che sarà sotto forma di stringa, contenente un ID oggetto, un tipo e informazioni di trasformazione (coordinate X e Y). 

3. L'app di realtà mista, che ha una scena identica all'app desktop, riceverà notifiche relative al movimento degli oggetti dal servizio Hub di notifica ,che è stato appena aggiornato dall'app per PC desktop. 

4. Quando si riceve una notifica che conterrà l'ID oggetto, il tipo e le informazioni di trasformazione, l'app di realtà mista applierà le informazioni ricevute alla propria scena.

Nell'applicazione è necessario sapere come integrare i risultati con la progettazione. Questo corso è stato progettato per illustrare come integrare un servizio di Azure con unity Project. È compito dell'utente usare le conoscenze acquisite in questo corso per migliorare l'applicazione di realtà mista. Questo corso è un'esercitazione autonoma, che non coinvolge direttamente altri lab di realtà mista.

## <a name="device-support"></a>Supporto di dispositivi

<table>
<tr>
<th>Corso</th><th style="width:150px"> <a href="/hololens/hololens1-hardware">HoloLens</a></th><th style="width:150px"> <a href="../../../discover/immersive-headset-hardware-details.md">Visori VR immersive</a></th>
</tr><tr>
<td> MR e Azure 308: Notifiche tra più dispositivi</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> Anche se questo corso è in particolare in Windows Mixed Reality visori VR immersive, è anche possibile applicare ciò che si apprende in questo corso per Microsoft HoloLens. Man mano che si segue il corso, verranno visualizzati note sulle eventuali modifiche che potrebbe essere necessario applicare per supportare HoloLens. Quando si usa HoloLens, è possibile notare un'eco durante l'acquisizione vocale.

## <a name="prerequisites"></a>Prerequisiti

> [!NOTE]
> Questa esercitazione è destinata agli sviluppatori che hanno esperienza di base con Unity e C#. Tenere presente anche che i prerequisiti e le istruzioni scritte all'interno di questo documento rappresentano ciò che è stato testato e verificato al momento della stesura di questo documento (maggio 2018). È possibile usare il software più recente, come indicato nell'articolo Installare gli strumenti, anche se non si presuppone che le informazioni in questo corso corrispondano perfettamente a quelle disponibili nel software più recente rispetto a quanto elencato di seguito. [](../../install-the-tools.md)

Per questo corso è consigliabile usare l'hardware e il software seguenti:

- Un PC di sviluppo, [compatibile con le Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) per lo sviluppo di visori VR immersive
- [Windows 10 Fall Creators Update (o versione successiva) con la modalità sviluppatore abilitata](../../install-the-tools.md#installation-checklist)
- [L'SDK Windows 10 più recente](../../install-the-tools.md#installation-checklist)
- [Unity 2017.4](../../install-the-tools.md#installation-checklist)
- [Visual Studio 2017](../../install-the-tools.md#installation-checklist)
- Un [visore VR o](../../../discover/immersive-headset-hardware-details.md) un visore [Microsoft HoloLens](/hololens/hololens1-hardware) VR Windows Mixed Reality con la modalità sviluppatore abilitata
- Accesso a Internet per la configurazione di Azure e per l'accesso a Hub di notifica

## <a name="before-you-start"></a>Prima di iniziare

- Per evitare di riscontrare problemi durante la compilazione di questo progetto, è consigliabile creare il progetto indicato in questa esercitazione in una cartella radice o vicina alla radice (i percorsi di cartelle lunghi possono causare problemi in fase di compilazione).
- È necessario essere il proprietario del portale di Sviluppatore Microsoft e del portale di registrazione delle applicazioni. In caso contrario, non si avrà l'autorizzazione per accedere all'app [nel capitolo 2.](#chapter-2---retrieve-your-new-apps-credentials)

## <a name="chapter-1---create-an-application-on-the-microsoft-developer-portal"></a>Capitolo 1: Creare un'applicazione nel Sviluppatore Microsoft portale

Per usare il servizio Hub di notifica di **Azure,** è necessario creare un'applicazione nel portale di Sviluppatore Microsoft, perché l'applicazione dovrà essere registrata, in modo che possa inviare e ricevere notifiche.

1.  Accedere al portale [Sviluppatore Microsoft .](https://developer.microsoft.com/dashboard)

    > È necessario accedere al proprio account Microsoft.

2.  Nel dashboard fare clic **su Crea una nuova app.**

    ![creare un'app](images/AzureLabs-Lab8-01.png)

3.  Verrà visualizzata una finestra popup in cui è necessario riservare un nome per la nuova app. Nella casella di testo inserire un nome appropriato. Se il nome scelto è disponibile, verrà visualizzato un segno di spunta a destra della casella di testo. Dopo aver inserito un nome disponibile, fare clic sul pulsante **Reserve product name** (Riserva nome prodotto) in basso a sinistra nella finestra popup.

    ![invertire un nome](images/AzureLabs-Lab8-02.png)

4.  Dopo aver creato l'app, è possibile passare al capitolo successivo.

## <a name="chapter-2---retrieve-your-new-apps-credentials"></a>Capitolo 2: Recuperare le credenziali delle nuove app

Accedere al portale di registrazione delle applicazioni, in cui verrà elencata la nuova app, e recuperare le credenziali che verranno usate per configurare il servizio **Hub** di notifica all'interno del **portale di Azure.**

1.  Passare al portale [di registrazione delle applicazioni.](https://apps.dev.microsoft.com)

    ![portale di registrazione delle applicazioni](images/AzureLabs-Lab8-03.png)

    > [!WARNING] 
    > È necessario usare l'account Microsoft per accedere.  
    > Deve **trattarsi** dell'account Microsoft usato nel capitolo [precedente,](#chapter-1---create-an-application-on-the-microsoft-developer-portal)con il portale per sviluppatori Windows Store.

2.  L'app è presente nella **sezione Applicazioni.** Dopo aver trovato l'app, fare clic su di essa per visualizzare una nuova pagina con il nome dell'app e **registrazione.**

    ![l'app appena registrata](images/AzureLabs-Lab8-04.png)

3.  Scorrere verso il basso la pagina di registrazione per trovare la **sezione Segreti dell'applicazione** e il **SID pacchetto** per l'app. Copiare entrambi per l'uso con la configurazione **del servizio Hub di notifica di Azure** nel capitolo successivo.

    ![segreti dell'applicazione](images/AzureLabs-Lab8-05.png)

## <a name="chapter-3---setup-azure-portal-create-notification-hubs-service"></a>Capitolo 3 - Configurare il portale di Azure: creare il servizio Hub di notifica

Dopo aver recuperato le credenziali delle app, è necessario passare al portale di Azure, in cui verrà creato un servizio Hub di notifica di Azure.

1.  Accedere al portale [di Azure.](https://portal.azure.com)

    > [!NOTE] 
    > Se non si ha già un account Azure, è necessario crearne uno. Se si sta seguendo questa esercitazione in una situazione di classe o di lab, chiedere all'insegnante o a uno dei protori di assistenza per la configurazione del nuovo account.

2.  Dopo aver eseguito l'accesso, fare clic su **Nuovo** nell'angolo in alto a sinistra, cercare **Hub di** notifica e fare clic su **_Invio._**

    ![cercare hub di notifica](images/AzureLabs-Lab8-06.png)

    > [!NOTE] 
    > La parola ***Nuovo** _ potrebbe essere stata sostituita con _*Crea una risorsa**, nei portali più nuovi.

3.  La nuova pagina fornirà una descrizione del *servizio Hub di* notifica. Nella parte inferiore sinistra del prompt selezionare il **pulsante Crea** per creare un'associazione con questo servizio.

    ![creare un'istanza di Hub di notifica](images/AzureLabs-Lab8-07.png)

4.  Dopo aver fatto clic su ***Crea:***

    1.  Inserire il nome desiderato per questa istanza del servizio.

    2.  Specificare uno **spazio** dei nomi che sarà possibile associare a questa app.

    3.  Selezionare una **località.**

    4.  Scegliere un **gruppo di risorse** o crearne uno nuovo. Un gruppo di risorse consente di monitorare, controllare l'accesso, effettuare il provisioning e gestire la fatturazione per una raccolta di asset di Azure. È consigliabile mantenere tutti i servizi di Azure associati a un singolo progetto (ad esempio, questi lab) in un gruppo di risorse comune.

        > Per altre informazioni sui gruppi di risorse di Azure, fare clic su questo [collegamento per gestire un gruppo di risorse.](/azure/azure-resource-manager/resource-group-portal) 

    5.  Selezionare una sottoscrizione **appropriata.**

    6.  È anche necessario confermare di aver compreso i termini e le condizioni applicati al servizio.

    7. Selezionare **Crea**.

        ![Compilare i dettagli del servizio](images/AzureLabs-Lab8-08.png)

5.  Dopo aver fatto clic su **Crea**, sarà necessario attendere la creazione del servizio. L'operazione potrebbe richiedere un minuto.

6.  Una volta creata l'istanza del servizio, nel portale verrà visualizzata una notifica.

    ![notifica](images/AzureLabs-Lab8-09.png)

7.  Fare clic **sul pulsante Vai alla** risorsa nella notifica per esplorare la nuova istanza del servizio. Verrà visualizzata la nuova istanza del servizio **Hub di** notifica.

    ![Vai alla risorsa](images/AzureLabs-Lab8-10.png)
    
8.  Nella pagina di panoramica, a metà pagina, fare clic su **Windows (WNS).** Il pannello a destra verrà modificato per visualizzare due campi di testo, che richiedono il **SID** del pacchetto e la chiave di **sicurezza,** dall'app impostata in precedenza.

    ![servizio hub appena creato](images/AzureLabs-Lab8-11.png)

9. Dopo aver copiato i dettagli nei campi corretti, fare clic su **Salva** per ricevere una notifica quando l'hub di notifica è stato aggiornato correttamente.

    ![copiare i dettagli di sicurezza](images/AzureLabs-Lab8-12.png)

## <a name="chapter-4---setup-azure-portal-create-table-service"></a>Capitolo 4 - Configurare il portale di Azure: creare il servizio tabelle

Dopo aver creato l'istanza del servizio Hub di notifica, tornare al portale di Azure, in cui si creerà un servizio tabelle di Azure creando una risorsa Archiviazione servizio.

1.  Se non è già stato eseguito l'accesso, accedere al [portale di Azure.](https://portal.azure.com)

2.  Dopo aver eseguito l'accesso, **fare** clic su Nuovo nell'angolo in alto a **sinistra,** cercare Archiviazione account e fare clic su **Invio.**

    > [!NOTE] 
    > La parola ***Nuovo** _ potrebbe essere stata sostituita con _*Crea una risorsa**, nei portali più nuovi.

3.  Selezionare **Archiviazione account blob, file, tabella, coda** dall'elenco.

    ![cercare l'account di archiviazione](images/AzureLabs-Lab8-13.png)

4.  La nuova pagina fornirà una descrizione del servizio **Archiviazione account** utente. Nella parte inferiore sinistra del prompt selezionare il **pulsante Crea** per creare un'istanza del servizio.

    ![creare un'istanza di archiviazione](images/AzureLabs-Lab8-14.png)

5.  Dopo aver fatto clic su **Crea,** verrà visualizzato un pannello:

    1. Inserire il nome **desiderato per** questa istanza del servizio (deve essere tutto minuscolo).

    2. Per **Modello di distribuzione** fare clic su Gestione **risorse**.

    3.  Per **Tipo di account,** usando il menu a discesa, **selezionare Archiviazione (utilizzo generico v1).**

    4. Selezionare un percorso **appropriato.**
    
    5.  Per il menu **a** discesa Replica selezionare Archiviazione con ridondanza geografica e accesso in **lettura (RA-GRS).**

    6.  Per **Prestazioni** fare clic su **Standard.**

    7.  Nella sezione **Trasferimento sicuro obbligatorio** selezionare **Disabilitato.**

    8.  Nel menu **a** discesa Sottoscrizione selezionare una sottoscrizione appropriata.

    9.  Scegliere un **gruppo di risorse** o crearne uno nuovo. Un gruppo di risorse consente di monitorare, controllare l'accesso, effettuare il provisioning e gestire la fatturazione per una raccolta di asset di Azure. È consigliabile mantenere tutti i servizi di Azure associati a un singolo progetto (ad esempio, questi lab) in un gruppo di risorse comune.

        > Per altre informazioni sui gruppi di risorse di Azure, fare clic su questo [collegamento per gestire un gruppo di risorse.](/azure/azure-resource-manager/resource-group-portal)

    10. Lasciare **Reti virtuali** su **Disabilitato** se questa è un'opzione per l'utente.

    11. Fare clic su **Crea**.

        ![Compilare i dettagli di archiviazione](images/AzureLabs-Lab8-15.png)

6.  Dopo aver fatto clic su **Crea**, sarà necessario attendere la creazione del servizio. L'operazione potrebbe richiedere un minuto.

7.  Una volta creata l'istanza del servizio, nel portale verrà visualizzata una notifica. Fare clic sulle notifiche per esplorare la nuova istanza del servizio.

    ![notifica della nuova archiviazione](images/AzureLabs-Lab8-16.png)

8.  Fare clic **sul pulsante Vai alla** risorsa nella notifica per esplorare la nuova istanza del servizio. Verrà visualizzata la pagina di panoramica della nuova istanza Archiviazione Service.

    ![Vai alla risorsa](images/AzureLabs-Lab8-17.PNG)

9. Nella pagina di panoramica fare clic su Tabelle sul lato **destro.**
    
    ![](images/AzureLabs-Lab8-18.PNG)

10. Il pannello a destra verrà modificato per visualizzare le **informazioni sul** servizio tabelle, in cui è necessario aggiungere una nuova tabella. A tale scopo, fare clic **+** **sul pulsante** Tabella nell'angolo superiore sinistro.

    ![aprire tabelle](images/AzureLabs-Lab8-19.png)

11. Verrà visualizzata una nuova pagina, in cui è necessario immettere un nome **di tabella**. Si tratta del nome che verrà utilizzato per fare riferimento ai dati nell'applicazione nei capitoli successivi. Inserire un nome appropriato e fare clic su **OK.**

    ![creare una nuova tabella](images/AzureLabs-Lab8-20.png)    

12. Dopo aver creato la nuova tabella, sarà possibile visualizzare la tabella nella pagina **Servizio** tabelle (nella parte inferiore).

    ![nuova tabella creata](images/AzureLabs-Lab8-21.png)
    

## <a name="chapter-5---completing-the-azure-table-in-visual-studio"></a>Capitolo 5: Completamento della tabella di Azure in Visual Studio

Dopo la **configurazione dell'account** di archiviazione del servizio tabelle, è possibile aggiungevi dati, che verranno usati per archiviare e recuperare informazioni. La modifica delle tabelle può essere eseguita tramite **Visual Studio**.

1.  Aprire **Visual Studio**.

2.  Scegliere Visualizza dal menu  >  **Cloud Explorer**.

    ![aprire Cloud Explorer](images/AzureLabs-Lab8-22.png)

3.  Il **Cloud Explorer** verrà aperto come elemento ancorato (sii paziente, poiché il caricamento può richiedere tempo).

    > [!NOTE] 
    > Se la sottoscrizione usata per creare gli account *Archiviazione non* è visibile, assicurarsi di disporre di: 
    > - Accedere allo stesso account usato per il portale di Azure.
    > - Selezionare la sottoscrizione nella pagina Gestione account (potrebbe essere necessario applicare un filtro dalle impostazioni dell'account):  
    >
    >   ![trovare la sottoscrizione](images/AzureLabs-Lab8-22-5.png)

4.  Verranno visualizzati i servizi cloud di Azure. Trovare **Archiviazione account e** fare clic sulla freccia a sinistra per espandere gli account.

    ![aprire gli account di archiviazione](images/AzureLabs-Lab8-23.png)

5.  Dopo l'espansione, **l'account Archiviazione dovrebbe** essere disponibile. Fare clic sulla freccia a sinistra dello spazio di  archiviazione e quindi, una volta espansa, trovare Tabelle e fare clic sulla freccia accanto a tale tabella per visualizzare la tabella creata nell'ultimo capitolo.  Fare doppio clic su **Tabella**.

    ![aprire la tabella degli oggetti della scena](images/AzureLabs-Lab8-24.png)

6.  La tabella verrà aperta al centro della finestra Visual Studio finestra. Fare clic sull'icona della tabella **+** con il segno più.

    ![aggiungere una nuova tabella](images/AzureLabs-Lab8-25.png)

7.  Verrà visualizzata una finestra in cui viene richiesto di *aggiungere l'entità*. Verranno create tre entità in totale, ognuna con diverse proprietà. Si noterà che *PartitionKey* e *RowKey* sono già disponibili, in quanto vengono usati dalla tabella per trovare i dati. 

    ![partizione e chiave di riga](images/AzureLabs-Lab8-26.png)

8. Aggiornare il *valore di* **PartitionKey** e **RowKey** come indicato di seguito (ricordarsi di eseguire questa operazione per ogni proprietà di riga aggiunta, incrementando ogni volta RowKey):

    ![aggiungere i valori corretti](images/AzureLabs-Lab8-26-5.png)

9.  Fare **clic su Aggiungi** proprietà per aggiungere altre righe di dati. Fare in modo che la prima tabella vuota corrisponda alla tabella seguente.

10. Al termine, fare clic su **OK.**

    ![Al termine, fare clic su OK](images/AzureLabs-Lab8-27.png)

    > [!WARNING] 
    > Assicurarsi di aver modificato le **voci Type** delle **voci X**, **Y** e **Z** in **Double**. 

11. Si noterà che la tabella include ora una riga di dati. Fare di nuovo **+** clic sull'icona (segno più) per aggiungere un'altra entità.

    ![prima riga](images/AzureLabs-Lab8-27-5.png)

12. Creare una proprietà aggiuntiva e quindi impostare i valori della nuova entità in modo che corrispondano a quelli illustrati di seguito.

    ![aggiungere un cubo](images/AzureLabs-Lab8-28.png)

13. Ripetere l'ultimo passaggio per aggiungere un'altra entità. Impostare i valori per questa entità su quelli illustrati di seguito.

    ![add cilindro](images/AzureLabs-Lab8-29.png)

14. La tabella dovrebbe ora essere simile a quella riportata di seguito.

    ![tabella completata](images/AzureLabs-Lab8-30.png)

15. Questo capitolo è stato completato. Assicurarsi di salvare.

## <a name="chapter-6---create-an-azure-function-app"></a>Capitolo 6: Creare un'app per le funzioni di Azure

Creare un'app per le funzioni di Azure, che verrà chiamata dall'applicazione desktop per aggiornare il servizio **tabelle** e inviare una notifica tramite l'hub **di notifica.**

Prima di tutto, è necessario creare un file che consenta alla funzione di Azure di caricare le librerie necessarie.

1.  Aprire **Blocco note** (premere Windows chiave e digitare notepad).

    ![aprire il Blocco note](images/AzureLabs-Lab8-31.png)

2.  Dopo Blocco note, inserire al suo interno la struttura JSON seguente. Dopo aver eseguito questa operazione, salvarlo sul desktop **comeproject.jsin**. È importante che la denominazione sia corretta: assicurarsi che **NON abbia un'.txt** file. Questo file definisce le librerie che verranno usate dalla funzione, se sono state usate NuGet sarà familiare.

    ```json
    {
    "frameworks": {
        "net46":{
        "dependencies": {
            "WindowsAzure.Storage": "7.0.0",
            "Microsoft.Azure.NotificationHubs" : "1.0.9",
            "Microsoft.Azure.WebJobs.Extensions.NotificationHubs" :"1.1.0"
        }
        }
    }
    }
    ```

3.  Accedere al portale [di Azure.](https://portal.azure.com)

4.  Dopo aver eseguito l'accesso, fare clic su **Nuovo** nell'angolo in alto a sinistra e cercare **App per le** funzioni e premere **INVIO.**

    ![cercare l'app per le funzioni](images/AzureLabs-Lab8-32.png)

    > [!NOTE] 
    > La parola **Nuovo** potrebbe essere stata sostituita **con Crea una risorsa** nei portali più nuovi.

5.  La nuova pagina fornirà una descrizione del servizio app **per le** funzioni. Nella parte inferiore sinistra del prompt selezionare il **pulsante Crea** per creare un'associazione con questo servizio.

    ![istanza dell'app per le funzioni](images/AzureLabs-Lab8-33.png)

6.  Dopo aver fatto clic su **Crea,** compilare quanto segue:

    1. In **Nome app** inserire il nome desiderato per questa istanza del servizio.

    2. Selezionare una **Sottoscrizione**.

    3. Selezionare il piano tariffario appropriato. Se è la prima volta che si crea un servizio app per le **funzioni,** dovrebbe essere disponibile un livello gratuito.

    4. Scegliere un **gruppo di risorse** o crearne uno nuovo. Un gruppo di risorse consente di monitorare, controllare l'accesso, effettuare il provisioning e gestire la fatturazione per una raccolta di asset di Azure. È consigliabile mantenere tutti i servizi di Azure associati a un singolo progetto (ad esempio, questi lab) in un gruppo di risorse comune.

        > Per altre informazioni sui gruppi di risorse di Azure, fare clic su questo [collegamento per gestire un gruppo di risorse.](/azure/azure-resource-manager/resource-group-portal)

    5. Per **Sistema operativo** fare clic Windows, perché è la piattaforma prevista.

    6. Selezionare un **piano di hosting** . In questa esercitazione viene utilizzato un piano a **consumo.**

    7. Selezionare una **località** **(scegliere la stessa posizione dell'archiviazione creata nel passaggio precedente)**

    8. Per la **Archiviazione,** è necessario selezionare **il servizio Archiviazione creato nel passaggio precedente.**

    9. L'applicazione *non Insights* in questa app, quindi è possibile lasciarla **disattivata.**

    10. Fare clic su **Crea**.

        ![creare una nuova istanza](images/AzureLabs-Lab8-34.png)

7.  Dopo aver fatto clic su **Crea,** sarà necessario attendere la creazione del servizio. L'operazione potrebbe richiedere un minuto.

8.  Una volta creata l'istanza del servizio, nel portale verrà visualizzata una notifica.

    ![nuova notifica](images/AzureLabs-Lab8-35.png)

9.  Fare clic sulle notifiche per esplorare la nuova istanza del servizio.

10. Fare clic **sul pulsante Vai alla** risorsa nella notifica per esplorare la nuova istanza del servizio. 

    ![Vai alla risorsa](images/AzureLabs-Lab8-36.png)

11. Fare clic **+** sull'icona (segno più) *accanto a Funzioni* per creare un *nuovo*.

    ![add new function](images/AzureLabs-Lab8-37.png)

12. Nel pannello centrale verrà visualizzata la **finestra di** creazione della funzione. Ignorare le informazioni nella metà superiore del pannello e fare clic su **Funzione** personalizzata , che si trova nella parte inferiore (nell'area blu, come indicato di seguito).

    ![funzione personalizzata](images/AzureLabs-Lab8-38.png)

13. La nuova pagina all'interno della finestra mostrerà vari tipi di funzione. Scorrere verso il basso per visualizzare i tipi viola e fare clic **sull'elemento HTTP PUT.**

    ![http put link](images/AzureLabs-Lab8-39.png)

    > [!IMPORTANT]
    > Potrebbe essere necessario scorrere ulteriormente la pagina verso il basso (e questa immagine potrebbe non avere esattamente lo stesso aspetto, se sono stati evasi aggiornamenti del portale di Azure), ma si sta cercando un elemento denominato *HTTP PUT.*

14. Verrà **visualizzata la finestra HTTP PUT,** in cui è necessario configurare la funzione (vedere di seguito per l'immagine).

    1.  Per **Linguaggio,** usando il menu a discesa, selezionare C \# .

    2.  In **Nome immettere** un nome appropriato.

    3.  Nel menu **a discesa Livello** di autenticazione selezionare **Funzione**.

    4.  Per la **sezione Nome** tabella è necessario usare il nome esatto usato in precedenza per creare il servizio **tabelle,** inclusa la stessa lettera maiuscola.

    5.  Nella sezione **Archiviazione connessione all'account** di archiviazione usare il menu a discesa e selezionare l'account di archiviazione da questa posizione. Se non è presente, fare clic sul collegamento ipertestuale **Nuovo** accanto al titolo della sezione per visualizzare un altro pannello in cui deve essere elencato l'account di archiviazione.

        ![nuova archiviazione](images/AzureLabs-Lab8-40.png)

15. Fare **clic su** Crea per ricevere una notifica che indica che le impostazioni sono state aggiornate correttamente.

    ![Create Function](images/AzureLabs-Lab8-41.png)

16. Dopo aver **fatto clic** su Crea, si verrà reindirizzati all'editor di funzioni.

    ![aggiornare il codice della funzione](images/AzureLabs-Lab8-42.png)

17. Inserire il codice seguente nell'editor di funzioni (sostituendo il codice nella funzione ):

    ```csharp
    #r "Microsoft.WindowsAzure.Storage"

    using System;
    using Microsoft.WindowsAzure.Storage;
    using Microsoft.WindowsAzure.Storage.Table;
    using Microsoft.Azure.NotificationHubs;
    using Newtonsoft.Json;

    public static async Task Run(UnityGameObject gameObj, CloudTable table, IAsyncCollector<Notification> notification, TraceWriter log)
    {
        //RowKey of the table object to be changed
        string rowKey = gameObj.RowKey;

        //Retrieve the table object by its RowKey
        TableOperation operation = TableOperation.Retrieve<UnityGameObject>("UnityPartitionKey", rowKey); 

        TableResult result = table.Execute(operation);

        //Create a UnityGameObject so to set its parameters
        UnityGameObject existingGameObj = (UnityGameObject)result.Result; 

        existingGameObj.RowKey = rowKey;
        existingGameObj.X = gameObj.X;
        existingGameObj.Y = gameObj.Y;
        existingGameObj.Z = gameObj.Z;

        //Replace the table appropriate table Entity with the value of the UnityGameObject
        operation = TableOperation.Replace(existingGameObj); 

        table.Execute(operation);

        log.Verbose($"Updated object position");

        //Serialize the UnityGameObject
        string wnsNotificationPayload = JsonConvert.SerializeObject(existingGameObj);
        
        log.Info($"{wnsNotificationPayload}");

        var headers = new Dictionary<string, string>();

        headers["X-WNS-Type"] = @"wns/raw";

        //Send the raw notification to subscribed devices
        await notification.AddAsync(new WindowsNotification(wnsNotificationPayload, headers)); 

        log.Verbose($"Sent notification");
    }

    // This UnityGameObject represent a Table Entity
    public class UnityGameObject : TableEntity
    {
        public string Type { get; set; }
        public double X { get; set; }
        public double Y { get; set; }
        public double Z { get; set; }
        public string RowKey { get; set; }
    }
    ```

    > [!NOTE]
    > Usando le librerie incluse, la funzione riceve il nome e la posizione dell'oggetto spostato nella scena Unity (come oggetto C#, **denominato UnityGameObject).** Questo oggetto viene quindi usato per aggiornare i parametri dell'oggetto all'interno della tabella creata. A questo punto, la funzione effettua una chiamata al servizio Hub di notifica creato, che invia una notifica a tutte le applicazioni sottoscritte.

18. Dopo il codice, fare clic su **Salva**.

19. Fare quindi clic **\<** sull'icona a forma di freccia sul lato destro della pagina.

    ![aprire il pannello di caricamento](images/AzureLabs-Lab8-43.png)

20. Un pannello scorrerà da destra. Nel pannello fare clic su **Upload** per visualizzare un Visualizzatore file.

21. Individuare e fare clic sul **project.js** file creato in precedenza in **Blocco note** e quindi fare clic sul **pulsante** Apri. Questo file definisce le librerie che verranno usate dalla funzione.

    ![caricare json](images/AzureLabs-Lab8-44.png)

22. Dopo il caricamento, il file verrà visualizzato nel pannello a destra. Facendo clic su di esso verrà aperto nell'editor **di** funzioni. Deve essere **esattamente uguale** all'immagine successiva (sotto il passaggio 23).

23. Quindi, nel pannello a sinistra, sotto **Funzioni,** fare clic sul **collegamento Integrazione.**

    ![Funzione integrate](images/AzureLabs-Lab8-45.png)

24. Nella pagina successiva, nell'angolo superiore destro, fare clic su **Editor avanzato** (come indicato di seguito).

    ![editor avanzato aperto](images/AzureLabs-Lab8-46.png)

25. Un **function.jssul** file verrà aperto nel pannello centrale, che deve essere sostituito con il frammento di codice seguente. Definisce la funzione che si sta compilando e i parametri passati alla funzione.

    ```json
    {
    "bindings": [
        {
        "authLevel": "function",
        "type": "httpTrigger",
        "methods": [
            "get",
            "post"
        ],
        "name": "gameObj",
        "direction": "in"
        },
        {
        "type": "table",
        "name": "table",
        "tableName": "SceneObjectsTable",
        "connection": "mrnothubstorage_STORAGE",
        "direction": "in"
        },
        {
        "type": "notificationHub",
        "direction": "out",
        "name": "notification",
        "hubName": "MR_NotHub_ServiceInstance",
        "connection": "MRNotHubNS_DefaultFullSharedAccessSignature_NH",
        "platform": "wns"
        }
    ]
    }
    ```

26. L'editor dovrebbe ora essere simile all'immagine seguente:

    ![torna all'editor standard](images/AzureLabs-Lab8-47.png)

27. È possibile notare che i parametri di input appena inseriti potrebbero non corrispondere ai dettagli della tabella e dell'archiviazione e pertanto dovranno essere aggiornati con le informazioni. **Non eseguire questa operazione in questo** caso, come illustrato di seguito. È sufficiente fare **clic sul collegamento Editor** standard nell'angolo superiore destro della pagina per tornare indietro.

28. **Nell'editor Standard fare** clic su Tabella di Azure Archiviazione **(tabella)** in **Input.** 
    
    ![Input di tabella](images/AzureLabs-Lab8-47-5.png)

29. Assicurarsi che le informazioni **seguenti** corrispondano, perché potrebbero essere diverse (è disponibile un'immagine sotto la procedura seguente):

    1.  **Nome tabella:** nome della tabella creata all'interno del Archiviazione di Azure, servizio Tabelle.

    2.  **Archiviazione account: fare** **clic** su Nuovo , che viene visualizzato accanto al menu a discesa. Verrà visualizzato un pannello a destra della finestra.

        ![nuova archiviazione](images/AzureLabs-Lab8-48.png)

        1.  Selezionare **l'Archiviazione account**, creato in precedenza per ospitare le app **per le funzioni.**

        2. Si noterà che è stato **creato Archiviazione di** connessione dell'account.

        3. Al termine, assicurarsi **di** premere Salva.

    3.  La **pagina Input dovrebbe** ora corrispondere alla seguente, che mostra **le** informazioni.

        ![input completati](images/AzureLabs-Lab8-49.png)

30. Fare quindi clic su **Hub di notifica di Azure (notifica)** in **Output.** Assicurarsi che le informazioni seguenti corrispondano **alle** informazioni, perché potrebbero essere diverse (è disponibile un'immagine sotto la procedura seguente):

    1.  **Nome hub di** notifica: nome dell'istanza del servizio **Hub** di notifica creata in precedenza.

    2.  **Connessione dello spazio dei nomi di Hub di** notifica: fare clic su **Nuovo**, che viene visualizzato accanto al menu a discesa.

        ![controllare gli output](images/AzureLabs-Lab8-50.png)

    3. Verrà **visualizzata la** finestra popup Connessione (vedere l'immagine seguente), in cui è necessario selezionare lo spazio dei nomi dell'hub di notifica configurato in precedenza.  

    4. Selezionare il nome **dell'hub di** notifica dal menu a discesa centrale.

    5.  Impostare il menu **a** discesa Criteri su **DefaultFullSharedAccessSignature**.

    6. Fare clic **sul pulsante** Seleziona per tornare indietro.

        ![aggiornamento dell'output](images/AzureLabs-Lab8-51.png)

31.  La **pagina Output dovrebbe** ora corrispondere a quello riportato di seguito, ma con **le** informazioni. Assicurarsi di premere **Salva**.

> [!WARNING]
> *Non modificare direttamente il nome dell'hub* di notifica ( questa operazione deve essere eseguita usando il Editor avanzato **,** purché siano stati eseguiti correttamente i passaggi precedenti.

![output completati](images/AzureLabs-Lab8-50.png)

32. A questo punto, è necessario testare la funzione per assicurarsi che funzioni. Per eseguire questa operazione: 

    1. Passare ancora una volta alla pagina della funzione:

        ![output completati](images/AzureLabs-Lab8-50-1.png)

    2. Nella pagina della funzione fare clic sulla **scheda Test** all'estrema destra della pagina per aprire il *pannello Test:*

        ![output completati](images/AzureLabs-Lab8-50-2.png)

    3. Nella casella **di testo Corpo** richiesta del pannello incollare il codice seguente:

        ```
        {  
            "Type":null,
            "X":3,
            "Y":0,
            "Z":1,
            "PartitionKey":null,
            "RowKey":"Obj2",
            "Timestamp":"0001-01-01T00:00:00+00:00",
            "ETag":null
        }
        ```

    4. Dopo avere eseguito il codice di test, fare clic **sul pulsante Esegui** in basso a destra e il test verrà eseguito. I log di output del test verranno visualizzati nell'area della console, sotto il codice della funzione.

        ![output completati](images/AzureLabs-Lab8-50-3.png)

    > [!WARNING]
    > Se il test precedente ha esito negativo, è necessario verificare di aver seguito esattamente i passaggi precedenti, in particolare le impostazioni all'interno del **pannello di integrazione**. 

## <a name="chapter-7---set-up-desktop-unity-project"></a>Capitolo 7- Configurare Desktop Unity Project

> [!IMPORTANT]
> L'applicazione desktop che si sta creando non **funzionerà** nell'editor di Unity. Deve essere eseguito all'esterno dell'editor, dopo la compilazione dell'applicazione, usando Visual Studio (o l'applicazione distribuita). 

Di seguito è riportata una configurazione tipica per lo sviluppo con Unity e la realtà mista e, di conseguenza, è un buon modello per altri progetti.

Configurare e testare il visore immersivo di realtà mista.

> [!NOTE] 
> Per questo **corso non** saranno necessari controller di movimento. Se è necessario supporto per la configurazione del visore immersivo, seguire questo collegamento per configurare [Windows Mixed Reality](https://support.microsoft.com/help/4043101/windows-10-set-up-windows-mixed-reality).

1.  Aprire **Unity** e fare clic su **Nuovo**.

    ![nuovo progetto unity](images/AzureLabs-Lab8-52.png)

2.  È necessario specificare un nome Project Unity, inserire **UnityDesktopNotifHub.** Assicurarsi che il tipo di progetto sia impostato su **3D.** Impostare Percorso **su** un percorso appropriato per l'utente (tenere presente che più vicino alle directory radice è meglio). Fare quindi clic **su Crea progetto**.

    ![crea progetto](images/AzureLabs-Lab8-53.png)

3.  Con Unity aperto, è opportuno controllare che **l'editor di script predefinito** sia impostato su **Visual Studio**. Passare a **Modifica**  >  **preferenze** e quindi dalla nuova finestra passare a **Strumenti esterni**. Modificare **Editor script esterni** in Visual Studio **2017.** Chiudere la **finestra** Preferenze.

    ![impostare gli strumenti esterni di Visual Studio](images/AzureLabs-Lab8-54.png)

4.  Passare quindi a **File** Build Impostazioni e selezionare Universal Windows Platform e quindi fare clic sul pulsante Cambia piattaforma  >   per applicare la selezione.  

    ![passare da una piattaforma all'altro](images/AzureLabs-Lab8-55.png)

5.  Mentre si è ancora in **Compilazione**  >  **Impostazioni** file, assicurarsi che:

    1.  **Dispositivo di destinazione** impostato su **Qualsiasi dispositivo**

        > Questa applicazione sarà per il desktop, quindi deve essere **Qualsiasi dispositivo**

    2.  **Il tipo di** compilazione è impostato **su D3D**

    3.  **L'SDK** è impostato su **Più recente installato**

    4.  **Visual Studio Version è** impostato su **Latest installed (Versione più recente installata)**

    5.  **Compilazione ed esecuzione** è impostato su **Computer locale**

    6.  In questo caso, vale la pena salvare la scena e aggiungerla alla compilazione.

        1. A tale scopo, selezionare **Aggiungi scene aperte**. Verrà visualizzata una finestra di salvataggio.

            ![aggiungere scene aperte](images/AzureLabs-Lab8-56.png)

        2. Creare una nuova cartella per questa e qualsiasi  scena futura, quindi selezionare il pulsante Nuova cartella per creare una nuova cartella, deno come **Scenes**.

            ![nuova cartella scenes](images/AzureLabs-Lab8-57.png)

        3. Aprire la cartella **Scenes appena** creata e quindi nel campo di testo **Nome file:** digitare **NH Desktop \_ \_ Scene** e quindi premere **Salva**.

            ![nuovo NH_Desktop_Scene](images/AzureLabs-Lab8-58.png)

    7.  Le impostazioni rimanenti, in **Build Impostazioni**, devono essere lasciato come impostazioni predefinite per il momento.

6.  Nella stessa finestra fare  clic sul Impostazioni player per aprire il pannello correlato nello spazio in cui si trova **l'inspector.**

7.  In questo pannello è necessario verificare alcune impostazioni:

    1.  Nella scheda **Altro Impostazioni:**

        1.  **La versione del runtime di** scripting deve essere **sperimentale (equivalente a .NET 4.6)**

        2. **Il back-end di** scripting deve **essere .NET**

        3. **Il livello di compatibilità** api deve **essere .NET 4.6**

            ![4.6 versione net](images/AzureLabs-Lab8-59.png)

    2.  Nella scheda **Pubblicazione Impostazioni,** in **Funzionalità**, controllare:

        - **InternetClient**

            ![tick internet client](images/AzureLabs-Lab8-60.png)

8.  In **Build Impostazioni** Unity C Projects (Compila *progetti Unity C) \#* non è più in grigio. Selezionare la casella di controllo accanto a questa opzione.

9.  Chiudere la finestra **Build Settings** (Impostazioni compilazione).

10. Salvare la scena e salvare Project **di**  >  **salvataggio/salvataggio file**  >  **Project**.

    > [!IMPORTANT]
    > Se si vuole ignorare il componente *Unity Set up* per questo progetto (Desktop App) e continuare direttamente nel codice, è possibile scaricare questo file [unitypackage,](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20308%20-%20Cross-device%20notifications/Azure-MR-308-Desktop.unitypackage)importarlo nel progetto come pacchetto personalizzato e quindi continuare dal capitolo [9.](#chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project) [](https://docs.unity3d.com/Manual/AssetPackages.html)  Sarà comunque necessario aggiungere i componenti script.

## <a name="chapter-8---importing-the-dlls-in-unity"></a>Capitolo 8 - Importazione delle DLL in Unity

Si usa Archiviazione di Azure per Unity (che a sua volta sfrutta .NET SDK per Azure). Per altre informazioni, fare [clic su questo collegamento Archiviazione di Azure per Unity.](/sandbox/gamedev/unity/azure-storage-unity)

Esiste attualmente un problema noto in Unity che richiede la riconfigurazione dei plug-in dopo l'importazione. Questi passaggi (da 4 a 7 in questa sezione) non saranno più necessari dopo la risoluzione del bug.

Per importare l'SDK nel proprio progetto, assicurarsi di aver scaricato il file [**unitypackage**](https://aka.ms/azstorage-unitysdk) più recente da GitHub. Procedere quindi come segue:

1.  Aggiungere il **file .unitypackage** a Unity usando l'opzione di menu Pacchetto **personalizzato \> di \>** importazione asset.

2.  Nella casella **Importa pacchetto Unity** visualizzata è possibile selezionare tutti gli elementi in **_Plug-in_ \> ** *Archiviazione***.  Deselezionare tutto il resto, perché non è necessario per questo corso.

    ![importare nel pacchetto](images/AzureLabs-Lab8-61.png)

3.  Fare clic ***sul pulsante*** Importa per aggiungere gli elementi al progetto.

4.  Passare alla cartella **Archiviazione** in **Plug-in** nella Project e selezionare solo i plug-in *seguenti:*

    -   Microsoft.Data.Edm
    -   Microsoft.Data.OData
    -   Microsoft.WindowsAzure.Storage
    -   Newtonsoft.Json
    -   System.Spatial

![deselezionare Qualsiasi piattaforma](images/AzureLabs-Lab8-62.png)

5.  Con *questi plug-in specifici* selezionati, **deselezionare** **Qualsiasi** piattaforma e **deselezionare** **WSAPlayer** e quindi fare clic su **Applica**.

    ![applicare dll della piattaforma](images/AzureLabs-Lab8-63.png)

    > [!NOTE] 
    > Questi plug-in specifici vengono contrassegnati come da usare solo nell'editor di Unity. Questo perché nella cartella WSA sono presenti versioni diverse degli stessi plug-in che verranno usate dopo l'esportazione del progetto da Unity.

6.  Nella cartella **Archiviazione** plug-in selezionare solo:

    -   Microsoft.Data.Services.Client

        ![set don't process for DLLs](images/AzureLabs-Lab8-64.png)

7.  Selezionare la **casella Don't Process** (Non elaborare) in **Platform Impostazioni** e fare clic su **_Apply (Applica)._**

    ![non applicare alcuna elaborazione](images/AzureLabs-Lab8-65.png)

    > [!NOTE] 
    > Questo plug-in viene contrassegnato come "Non elaborare", perché il patcher dell'assembly Unity ha difficoltà a elaborare questo plug-in. Il plug-in continuerà a funzionare anche se non viene elaborato.

## <a name="chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project"></a>Capitolo 9: Creare la classe TableToScene nel progetto Desktop Unity

È ora necessario creare gli script contenenti il codice per eseguire questa applicazione.

Il primo script da creare è **TableToScene,** responsabile di:

-   Lettura di entità all'interno della tabella di Azure.
-   Usando i dati della tabella, determinare gli oggetti da generare e in quale posizione.

Il secondo script da creare è **CloudScene,** responsabile di:

-   Registrazione dell'evento click sinistro, per consentire all'utente di trascinare oggetti nella scena.
-   Serializzazione dei dati dell'oggetto da questa scena di Unity e invio all'app per le funzioni di Azure.

Per creare questa classe:

1.  Fare clic con il pulsante destro **del mouse** nella cartella Asset che si trova nel pannello Project, **Crea**  >  **cartella**. Assegnare alla cartella il nome **Scripts**.

    ![creare la cartella degli script](images/AzureLabs-Lab8-66.png)

    ![creare la cartella degli script 2](images/AzureLabs-Lab8-67.png)

2.  Fare doppio clic sulla cartella appena creata per aprirla.

3.  Fare clic con il pulsante destro del **mouse nella cartella Script** e scegliere **Crea**  >  **script C#.** Assegnare allo script **il nome TableToScene**.

    ![nuovo script c# ](images/AzureLabs-Lab8-68.png)
     ![ TableToScene rename](images/AzureLabs-Lab8-69.png)

4.  Fare doppio clic sullo script per aprirlo in Visual Studio 2017.

5.  Aggiungere gli spazi dei nomi seguenti:

    ```csharp
    using Microsoft.WindowsAzure.Storage;
    using Microsoft.WindowsAzure.Storage.Auth;
    using Microsoft.WindowsAzure.Storage.Table;
    using UnityEngine;
    ```

6.  All'interno della classe inserire le variabili seguenti:

    ```csharp
        /// <summary>    
        /// allows this class to behave like a singleton
        /// </summary>    
        public static TableToScene instance;

        /// <summary>    
        /// Insert here you Azure Storage name     
        /// </summary>    
        private string accountName = " -- Insert your Azure Storage name -- ";

        /// <summary>    
        /// Insert here you Azure Storage key    
        /// </summary>    
        private string accountKey = " -- Insert your Azure Storage key -- ";
    ```
    
    > [!NOTE] 
    > Sostituire **il valore accountName** con il nome del servizio Archiviazione di Azure e il valore **accountKey** con il valore della chiave presente nel servizio Archiviazione di Azure nel portale di Azure (vedere l'immagine seguente). 
    >
    > ![recuperare la chiave dell'account](images/AzureLabs-Lab8-70.png)

7.  Aggiungere ora i **metodi Start()** **e Awake()** per inizializzare la classe.

    ```csharp
        /// <summary>
        /// Triggers before initialization
        /// </summary>
        void Awake()
        {
            // static instance of this class
            instance = this;
        }

        /// <summary>
        /// Use this for initialization
        /// </summary>
        void Start()
        {  
            // Call method to populate the scene with new objects as 
            // pecified in the Azure Table
            PopulateSceneFromTableAsync();
        }
    ```

8.  **All'interno della classe TableToScene** aggiungere il metodo che recupererà i valori dalla tabella di Azure e li userà per generare le primitive appropriate nella scena.

    ```csharp
        /// <summary>    
        /// Populate the scene with new objects as specified in the Azure Table    
        /// </summary>    
        private async void PopulateSceneFromTableAsync()
        {
            // Obtain credentials for the Azure Storage
            StorageCredentials creds = new StorageCredentials(accountName, accountKey);

            // Storage account
            CloudStorageAccount account = new CloudStorageAccount(creds, useHttps: true);
            
            // Storage client
            CloudTableClient client = account.CreateCloudTableClient(); 
            
            // Table reference
            CloudTable table = client.GetTableReference("SceneObjectsTable");

            TableContinuationToken token = null;

            // Query the table for every existing Entity
            do
            {
                // Queries the whole table by breaking it into segments
                // (would happen only if the table had huge number of Entities)
                TableQuerySegment<AzureTableEntity> queryResult = await table.ExecuteQuerySegmentedAsync(new TableQuery<AzureTableEntity>(), token); 

                foreach (AzureTableEntity entity in queryResult.Results)
                {
                    GameObject newSceneGameObject = null;
                    Color newColor;

                    // check for the Entity Type and spawn in the scene the appropriate Primitive
                    switch (entity.Type)
                    {
                        case "Cube":
                            // Create a Cube in the scene
                            newSceneGameObject = GameObject.CreatePrimitive(PrimitiveType.Cube);
                            newColor = Color.blue;
                            break;

                        case "Sphere":
                            // Create a Sphere in the scene
                            newSceneGameObject = GameObject.CreatePrimitive(PrimitiveType.Sphere);
                            newColor = Color.red;
                            break;

                        case "Cylinder":
                            // Create a Cylinder in the scene
                            newSceneGameObject = GameObject.CreatePrimitive(PrimitiveType.Cylinder);
                            newColor = Color.yellow;
                            break;
                        default:
                            newColor = Color.white;
                            break;
                    }

                    newSceneGameObject.name = entity.RowKey;

                    newSceneGameObject.GetComponent<MeshRenderer>().material = new Material(Shader.Find("Diffuse"))
                    {
                        color = newColor
                    };

                    //check for the Entity X,Y,Z and move the Primitive at those coordinates
                    newSceneGameObject.transform.position = new Vector3((float)entity.X, (float)entity.Y, (float)entity.Z);
                }

                // if the token is null, it means there are no more segments left to query
                token = queryResult.ContinuationToken;
            }

            while (token != null);
        }
    ```

9.  **All'esterno della classe TableToScene** è necessario definire la classe usata dall'applicazione per serializzare e deserializzare le **entità tabella**.

    ```csharp
        /// <summary>
        /// This objects is used to serialize and deserialize the Azure Table Entity
        /// </summary>
        [System.Serializable]
        public class AzureTableEntity : TableEntity
        {
            public AzureTableEntity(string partitionKey, string rowKey)
                : base(partitionKey, rowKey) { }

            public AzureTableEntity() { }
            public string Type { get; set; }
            public double X { get; set; }
            public double Y { get; set; }
            public double Z { get; set; }
        }
    ```

10. Assicurarsi di salvare **prima** di tornare all'editor di Unity.

11. Fare clic **sulla fotocamera principale** nel pannello **Gerarchia,** in modo che le relative proprietà vengano visualizzate nel **controllo**.

12. Con la **cartella** Scripts aperta, selezionare il **file TableToScene** dello script e trascinarlo nella **fotocamera principale.** Il risultato dovrebbe essere il seguente:

    ![aggiungere uno script alla fotocamera principale](images/AzureLabs-Lab8-71.png)

## <a name="chapter-10---create-the-cloudscene-class-in-the-desktop-unity-project"></a>Capitolo 10 - Creare la classe CloudScene nel Project

Il secondo script da creare è **CloudScene,** responsabile di:

-   Registrazione dell'evento click sinistro, per consentire all'utente di trascinare oggetti nella scena.

-   Serializzazione dei dati dell'oggetto da questa scena di Unity e invio all'app per le funzioni di Azure.

Per creare il secondo script:

1.  Fare clic con il pulsante destro del **mouse nella cartella Script** , scegliere **Crea**, **Script C \#**. Assegnare allo script il **nome CloudScene**
    
    ![nuovo script c# ](images/AzureLabs-Lab8-72.png)
     ![ rinominare CloudScene](images/AzureLabs-Lab8-73.png)

2.  Aggiungere gli spazi dei nomi seguenti:

    ```csharp
    using Newtonsoft.Json;
    using System.Collections;
    using System.Text;
    using System.Threading.Tasks;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

3.  Inserire le variabili seguenti:

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static CloudScene instance;

        /// <summary>
        /// Insert here you Azure Function Url
        /// </summary>
        private string azureFunctionEndpoint = "--Insert here you Azure Function Endpoint--";

        /// <summary>
        /// Flag for object being moved
        /// </summary>
        private bool gameObjHasMoved;

        /// <summary>
        /// Transform of the object being dragged by the mouse
        /// </summary>
        private Transform gameObjHeld;

        /// <summary>
        /// Class hosted in the TableToScene script
        /// </summary>
        private AzureTableEntity azureTableEntity;
    ```

4.  Sostituire il **valore azureFunctionEndpoint** con l'URL dell'app per le funzioni di Azure disponibile nel servizio app per le funzioni di Azure, nel portale di Azure, come illustrato nell'immagine seguente:

    ![URL della funzione get](images/AzureLabs-Lab8-74.png)

5.  Aggiungere ora i **metodi Start()** **e Awake()** per inizializzare la classe.

    ```csharp
        /// <summary>
        /// Triggers before initialization
        /// </summary>
        void Awake()
        {
            // static instance of this class
            instance = this;
        }

        /// <summary>
        /// Use this for initialization
        /// </summary>
        void Start()
        {
            // initialise an AzureTableEntity
            azureTableEntity = new AzureTableEntity();
        }
    ```

6.  **All'interno del metodo Update()** aggiungere il codice seguente che rileverà l'input del mouse e il trascinamento, che a sua volta sposterà GameObjects nella scena. Se l'utente ha trascinato e rilasciato un oggetto, passerà il nome e le coordinate dell'oggetto al metodo **UpdateCloudScene(),** che chiamerà il servizio App per le funzioni di Azure, che aggiornerà la tabella di Azure e attiverà la notifica.

    ```csharp
        /// <summary>
        /// Update is called once per frame
        /// </summary>
        void Update()
        {
            //Enable Drag if button is held down
            if (Input.GetMouseButton(0))
            {
                // Get the mouse position
                Vector3 mousePosition = new Vector3(Input.mousePosition.x, Input.mousePosition.y, 10);

                Vector3 objPos = Camera.main.ScreenToWorldPoint(mousePosition);

                Ray ray = Camera.main.ScreenPointToRay(Input.mousePosition);

                RaycastHit hit;

                // Raycast from the current mouse position to the object overlapped by the mouse
                if (Physics.Raycast(ray, out hit))
                {
                    // update the position of the object "hit" by the mouse
                    hit.transform.position = objPos;

                    gameObjHasMoved = true;

                    gameObjHeld = hit.transform;
                }
            }

            // check if the left button mouse is released while holding an object
            if (Input.GetMouseButtonUp(0) && gameObjHasMoved)
            {
                gameObjHasMoved = false;

                // Call the Azure Function that will update the appropriate Entity in the Azure Table
                // and send a Notification to all subscribed Apps
                Debug.Log("Calling Azure Function");

                StartCoroutine(UpdateCloudScene(gameObjHeld.name, gameObjHeld.position.x, gameObjHeld.position.y, gameObjHeld.position.z));
            }
        }
    ```

7.  Aggiungere ora il **metodo UpdateCloudScene(),** come indicato di seguito:

    ```csharp
        private IEnumerator UpdateCloudScene(string objName, double xPos, double yPos, double zPos)
        {
            WWWForm form = new WWWForm();

            // set the properties of the AzureTableEntity
            azureTableEntity.RowKey = objName;

            azureTableEntity.X = xPos;

            azureTableEntity.Y = yPos;

            azureTableEntity.Z = zPos;

            // Serialize the AzureTableEntity object to be sent to Azure
            string jsonObject = JsonConvert.SerializeObject(azureTableEntity);

            using (UnityWebRequest www = UnityWebRequest.Post(azureFunctionEndpoint, jsonObject))
            {
                byte[] jsonToSend = new System.Text.UTF8Encoding().GetBytes(jsonObject);

                www.uploadHandler = new UploadHandlerRaw(jsonToSend);

                www.uploadHandler.contentType = "application/json";

                www.downloadHandler = new DownloadHandlerBuffer();

                www.SetRequestHeader("Content-Type", "application/json");

                yield return www.SendWebRequest();

                string response = www.responseCode.ToString();
            }
        }
    ```

8.  Salvare il codice e tornare a Unity

9.  Trascinare lo script **CloudScene** nella **fotocamera principale.** 

    1. Fare clic **sulla fotocamera principale** nel pannello **Gerarchia,** in modo che le relative proprietà vengano visualizzate nel **controllo**. 

    2. Con la **cartella** Scripts aperta, selezionare lo script **CloudScene** e trascinarlo nella **fotocamera principale.** Il risultato dovrebbe essere il seguente:

        > ![trascinare lo script cloud nella fotocamera principale](images/AzureLabs-Lab8-75.png)

## <a name="chapter-11---build-the-desktop-project-to-uwp"></a>Capitolo 11- Creare il desktop Project alla UWP

Tutti gli elementi necessari per la sezione Unity di questo progetto sono stati completati.

1.  Passare a **Build Impostazioni** (**File**  >  **Build Impostazioni**).

2.  Nella finestra **Compila Impostazioni** fare clic su **Compila**.

    ![progetto di compilazione](images/AzureLabs-Lab8-76.png)

3.  Verrà **visualizzata Esplora file** finestra di dialogo che richiede un percorso per la compilazione. Creare una nuova cartella (facendo clic **su Nuova cartella** nell'angolo superiore sinistro) e assegnare il nome **BUILDS**.

    ![nuova cartella per la compilazione](images/AzureLabs-Lab8-77.png)

    1.  Aprire la nuova **cartella BUILDS** e creare un'altra cartella (usando ancora una volta **Nuova** cartella) e assegnare il nome **NH \_ Desktop \_ App**.

        ![nome cartella NH_Desktop_App](images/AzureLabs-Lab8-78.png)

    2.  Con **\_ \_ l'app desktop NH** selezionata. fare **clic su Seleziona cartella**. La compilazione del progetto potrebbe richiedere circa un minuto.

4.  Dopo la compilazione, **Esplora file** verrà visualizzato il percorso del nuovo progetto. Non è necessario aprirlo, tuttavia, poiché è necessario creare prima l'altro progetto Unity, nei prossimi capitoli.


## <a name="chapter-12---set-up-mixed-reality-unity-project"></a>Capitolo 12 : Configurare Unity in realtà mista Project

Di seguito è riportata una configurazione tipica per lo sviluppo con la realtà mista e, di conseguenza, è un buon modello per altri progetti.

1.  Aprire **Unity** e fare clic su **Nuovo**.

    ![nuovo progetto unity](images/AzureLabs-Lab8-79.png)

2.  È ora necessario specificare un nome Project Unity, inserire **UnityMRNotifHub.** Assicurarsi che il tipo di progetto sia impostato su **3D.** Impostare Percorso **su** un percorso appropriato per l'utente (tenere presente che più vicino alle directory radice è meglio). Fare quindi clic **su Crea progetto**.

    ![nome UnityMRNotifHub](images/AzureLabs-Lab8-80.png)

3.  Con Unity aperto, è opportuno controllare che **l'editor di script predefinito** sia impostato su **Visual Studio**. Passare a **Modifica**  >  **preferenze** e quindi dalla nuova finestra passare a **Strumenti esterni**. Modificare **Editor script esterni** in Visual Studio **2017.** Chiudere la **finestra** Preferenze.

    ![impostare l'editor esterno su Vs](images/AzureLabs-Lab8-81.png)

4.  Passare quindi a **File** Build Impostazioni e impostare la piattaforma su Universal Windows Platform facendo clic  >   sul pulsante  **Cambia** piattaforma.

    ![Passare dalle piattaforme alla piattaforma UWP](images/AzureLabs-Lab8-82.png)

5.  Passare a **File**  >  **Build Impostazioni** (Compilazione file) e assicurarsi che:

    1.  **Dispositivo di destinazione** impostato su **Qualsiasi dispositivo**

        > Per il Microsoft HoloLens, impostare **Dispositivo di destinazione** su *HoloLens*.

    2.  **Il tipo di** compilazione è impostato **su D3D**

    3.  **L'SDK** è impostato su **Più recente installato**

    4.  **Visual Studio Version è** impostato su **Latest installed (Versione più recente installata)**

    5.  **Compilazione ed esecuzione** è impostato su **Computer locale**

    6.  In questo caso, vale la pena salvare la scena e aggiungerla alla compilazione.

        1. A tale scopo, selezionare **Aggiungi scene aperte**. Verrà visualizzata una finestra di salvataggio.

            ![aggiungere scene aperte](images/AzureLabs-Lab8-83.png)

        2. Creare una nuova cartella per questa e qualsiasi  scena futura, quindi selezionare il pulsante Nuova cartella per creare una nuova cartella, deno come **Scenes**.

            ![nuova cartella scenes](images/AzureLabs-Lab8-84.png)

        3. Aprire la cartella **Scenes appena** creata e quindi nel campo di testo **Nome file:** digitare **NH MR \_ \_ Scene** e quindi premere **Salva**.

            ![nuova scena - NH_MR_Scene](images/AzureLabs-Lab8-85.png)

    7.  Le impostazioni rimanenti, in **Build Impostazioni**, devono essere lasciato come impostazioni predefinite per il momento.

6.  Nella stessa finestra fare  clic sul Impostazioni player per aprire il pannello correlato nello spazio in cui si trova **l'inspector.**    

    ![aprire le impostazioni del lettore](images/AzureLabs-Lab8-86.png)

7.  In questo pannello è necessario verificare alcune impostazioni:

    1.  Nella scheda **Altro Impostazioni:**

        1.  **La versione del runtime di** scripting deve essere **sperimentale** (equivalente a .NET 4.6)
        2.  **Il back-end di** scripting deve **_essere .NET_**
        3.  **Il livello di compatibilità** api deve **essere .NET 4.6**

            ![Compatibilità con le API](images/AzureLabs-Lab8-87.png)

    2.  Più in basso nel pannello, in **XR Impostazioni** (disponibile sotto Pubblica **Impostazioni**), selezionare **Virtual Reality Supported**(Realtà virtuale supportata) e assicurarsi che sia aggiunto Windows Mixed Reality **SDK**

        ![aggiornare le impostazioni di xr](images/AzureLabs-Lab8-88.png)        

    3.  Nella scheda **Pubblicazione Impostazioni,** in **Funzionalità**, di tipo heck:

        - **InternetClient**           

            ![tick internet client](images/AzureLabs-Lab8-89.png)

8.  In **Build Impostazioni**, **Unity C# Projects** non è più in grigio: selezionare la casella di controllo accanto a questo.

9.  Dopo aver apportato queste modifiche, chiudere la finestra Impostazioni compilazione.

10. Salvare la scena e salvare Project **di**  >  **salvataggio/salvataggio file**  >  **Project**.

    > [!IMPORTANT]
    > Se si vuole ignorare il componente *Unity Set up* per questo progetto (app di realtà mista) e continuare direttamente [](https://docs.unity3d.com/Manual/AssetPackages.html)nel codice, è possibile scaricare questo [file unitypackage,](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20308%20-%20Cross-device%20notifications/Azure-MR-308-MR.unitypackage)importarlo nel progetto come pacchetto personalizzato e quindi continuare dal capitolo [14.](#chapter-14---creating-the-tabletoscene-class-in-the-mixed-reality-unity-project) Sarà comunque necessario aggiungere i componenti script.

### <a name="chapter-13---importing-the-dlls-in-the-mixed-reality-unity-project"></a>Capitolo 13 - Importazione delle DLL in Mixed Reality Unity Project

Verrà utilizzata la libreria Archiviazione di Azure per Unity (che usa .NET SDK per Azure). Seguire questo [collegamento per informazioni su come usare Archiviazione di Azure con Unity.](/sandbox/gamedev/unity/azure-storage-unity)
Esiste attualmente un problema noto in Unity che richiede la riconfigurazione dei plug-in dopo l'importazione. Questi passaggi (da 4 a 7 in questa sezione) non saranno più necessari dopo la risoluzione del bug.

Per importare l'SDK nel proprio progetto, assicurarsi di aver scaricato il file [con estensione unitypackage più recente.](https://aka.ms/azstorage-unitysdk) Procedere quindi come segue:

1.  Aggiungere il file con estensione unitypackage scaricato dall'esempio precedente a Unity usando l'opzione di menu Pacchetto personalizzato di importazione   >    >   asset.

2.  Nella casella **Importa pacchetto Unity** visualizzata è possibile selezionare tutti gli elementi in   >  **Plug-in Archiviazione**.

    ![importare un pacchetto](images/AzureLabs-Lab8-90.png)

3.  Fare clic **sul pulsante** Importa per aggiungere gli elementi al progetto.

4.  Passare alla cartella **Archiviazione** in **Plug-in** nella Project e selezionare solo i plug-in *seguenti:*

    -   Microsoft.Data.Edm
    -   Microsoft.Data.OData
    -   Microsoft.WindowsAzure.Storage
    -   Newtonsoft.Json
    -   System.Spatial

    ![selezionare i plug-in](images/AzureLabs-Lab8-91.png)

5.  Con *questi plug-in specifici* selezionati, **deselezionare** **Qualsiasi** piattaforma e **deselezionare** **WSAPlayer** e quindi fare clic su **Applica**.

    ![applicare le modifiche della piattaforma](images/AzureLabs-Lab8-92.png)

    > [!NOTE] 
    > Si contrassegnano questi specifici plug-in da usare solo nell'editor di Unity. Questo perché nella cartella WSA sono presenti versioni diverse degli stessi plug-in che verranno usate dopo l'esportazione del progetto da Unity.

6.  Nella cartella **Archiviazione** plug-in selezionare solo:

    -   Microsoft.Data.Services.Client

        ![selezionare il client dei servizi dati](images/AzureLabs-Lab8-93.png)

7.  Selezionare la **casella Don't Process** (Non elaborare) in **Platform Impostazioni** e fare clic su **Apply (Applica).**

    ![non elaborare](images/AzureLabs-Lab8-94.png)

    > [!NOTE] 
    > Si contrassegna questo plug-in "Non elaborare" perché il patcher dell'assembly Unity ha difficoltà a elaborare questo plug-in. Il plug-in continuerà a funzionare anche se non viene elaborato.

## <a name="chapter-14---creating-the-tabletoscene-class-in-the-mixed-reality-unity-project"></a>Capitolo 14 - Creazione della classe TableToScene nel progetto Unity di realtà mista

La **classe TableToScene** è identica a quella illustrata nel [capitolo 9.](#chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project) Creare la stessa classe nella realtà mista unity Project seguendo la stessa procedura illustrata [nel capitolo 9](#chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project).

Dopo aver completato questo capitolo, entrambi **i progetti Unity** avranno questa classe impostata sulla fotocamera principale.

## <a name="chapter-15---creating-the-notificationreceiver-class-in-the-mixed-reality-unity-project"></a>Capitolo 15 - Creazione della classe NotificationReceiver nella classe Unity di realtà mista Project

Il secondo script da creare è **NotificationReceiver,** responsabile di:

-   Registrazione dell'app con l'hub di notifica all'inizializzazione.
-   Ascolto delle notifiche provenienti dall'hub di notifica.
-   Deserializzazione dei dati dell'oggetto dalle notifiche ricevute.
-   Spostare gli oggetti GameObject nella scena, in base ai dati deserializzati.

Per creare lo script **NotificationReceiver:**

1.  Fare clic con il pulsante destro del **mouse nella cartella Script** , scegliere **Crea**, **Script C \#**. Assegnare allo script **il nome NotificationReceiver**.

    ![creare il nuovo nome dello script c# ](images/AzureLabs-Lab8-95.png)
     ![ NotificationReceiver](images/AzureLabs-Lab8-96.png)

2.  Fare doppio clic sullo script per aprirlo.

3.  Aggiungere gli spazi dei nomi seguenti:

    ```csharp
    //using Microsoft.WindowsAzure.Messaging;
    using Newtonsoft.Json;
    using System;
    using System.Collections;
    using UnityEngine;

    #if UNITY_WSA_10_0 && !UNITY_EDITOR
    using Windows.Networking.PushNotifications;
    #endif
    ```

4.  Inserire le variabili seguenti:

    ```csharp
        /// <summary>
        /// allows this class to behave like a singleton
        /// </summary>
        public static NotificationReceiver instance;

        /// <summary>
        /// Value set by the notification, new object position
        /// </summary>
        Vector3 newObjPosition;

        /// <summary>
        /// Value set by the notification, object name
        /// </summary>
        string gameObjectName;

        /// <summary>
        /// Value set by the notification, new object position
        /// </summary>
        bool notifReceived;

        /// <summary>
        /// Insert here your Notification Hub Service name 
        /// </summary>
        private string hubName = " -- Insert the name of your service -- ";

        /// <summary>
        /// Insert here your Notification Hub Service "Listen endpoint"
        /// </summary>
        private string hubListenEndpoint = "-Insert your Notification Hub Service Listen endpoint-";
    ```

5.  Sostituire il valore **hubName** con il nome del servizio hub di notifica e il valore **hubListenEndpoint** con il valore dell'endpoint disponibile nella scheda Criteri di accesso, Servizio Hub di notifica di Azure, nel portale di Azure (vedere l'immagine seguente).

    ![inserire l'endpoint dei criteri degli hub di notifica](images/AzureLabs-Lab8-97.png)

6.  Aggiungere ora i **metodi Start()** **e Awake()** per inizializzare la classe.

    ```csharp
        /// <summary>
        /// Triggers before initialization
        /// </summary>
        void Awake()
        {
            // static instance of this class
            instance = this;
        }

        /// <summary>
        /// Use this for initialization
        /// </summary>
        void Start()
        {
            // Register the App at launch
            InitNotificationsAsync();

            // Begin listening for notifications
            StartCoroutine(WaitForNotification());
        }
    ```

7.  Aggiungere il **metodo WaitForNotification** per consentire all'app di ricevere notifiche dalla libreria dell'hub di notifica senza conflitti con il thread principale:

    ```csharp
        /// <summary>
        /// This notification listener is necessary to avoid clashes 
        /// between the notification hub and the main thread   
        /// </summary>
        private IEnumerator WaitForNotification()
        {
            while (true)
            {
                // Checks for notifications each second
                yield return new WaitForSeconds(1f);

                if (notifReceived)
                {
                    // If a notification is arrived, moved the appropriate object to the new position
                    GameObject.Find(gameObjectName).transform.position = newObjPosition;

                    // Reset the flag
                    notifReceived = false;
                }
            }
        }
    ```

8.  Il metodo seguente, **InitNotificationAsync(),** registrerà l'applicazione con il servizio hub di notifica al momento dell'inizializzazione. Il codice viene commentato perché Unity non sarà in grado di compilare il progetto. I commenti verranno rimosso quando si importa il pacchetto Nuget di messaggistica di Azure in Visual Studio.

    ```csharp
        /// <summary>
        /// Register this application to the Notification Hub Service
        /// </summary>
        private async void InitNotificationsAsync()
        {
            // PushNotificationChannel channel = await PushNotificationChannelManager.CreatePushNotificationChannelForApplicationAsync();

            // NotificationHub hub = new NotificationHub(hubName, hubListenEndpoint);

            // Registration result = await hub.RegisterNativeAsync(channel.Uri);

            // If registration was successful, subscribe to Push Notifications
            // if (result.RegistrationId != null)
            // {
            //     Debug.Log($"Registration Successful: {result.RegistrationId}");
            //     channel.PushNotificationReceived += Channel_PushNotificationReceived;
            // }
        }
    ```

9.  Il gestore seguente, **Channel \_ PushNotificationReceived(),** verrà attivato ogni volta che viene ricevuta una notifica. Deserializza la notifica, che sarà l'entità tabella di Azure spostata nell'applicazione desktop, e quindi sposta il GameObject corrispondente nella scena MR nella stessa posizione. 
    
    > [!IMPORTANT]
    > Il codice viene commentato perché il codice fa riferimento alla libreria di Messaggistica di Azure, che verrà aggiunta dopo la compilazione del progetto Unity usando il Gestione pacchetti Nuget, all'interno Visual Studio. Di conseguenza, il progetto Unity non sarà in grado di compilare, a meno che non venga commentato. Tenere presente che, se si compila il progetto e quindi si vuole tornare a Unity, sarà necessario aggiungere nuovamente un **commento** al codice.

    ```csharp
        ///// <summary>
        ///// Handler called when a Push Notification is received
        ///// </summary>
        //private void Channel_PushNotificationReceived(PushNotificationChannel sender, PushNotificationReceivedEventArgs args)    
        //{
        //    Debug.Log("New Push Notification Received");
        //
        //    if (args.NotificationType == PushNotificationType.Raw)
        //    {
        //        //  Raw content of the Notification
        //        string jsonContent = args.RawNotification.Content;
        //
        //        // Deserialise the Raw content into an AzureTableEntity object
        //        AzureTableEntity ate = JsonConvert.DeserializeObject<AzureTableEntity>(jsonContent);
        //
        //        // The name of the Game Object to be moved
        //        gameObjectName = ate.RowKey;          
        //
        //        // The position where the Game Object has to be moved
        //        newObjPosition = new Vector3((float)ate.X, (float)ate.Y, (float)ate.Z);
        //
        //        // Flag thats a notification has been received
        //        notifReceived = true;
        //    }
        //}
    ```

10. Ricordarsi di salvare le modifiche prima di tornare all'editor di Unity.

11. Fare clic **sulla fotocamera principale** nel pannello **Gerarchia,** in modo che le relative proprietà vengano visualizzate nel **controllo**.

12. Con la **cartella** Script aperta, selezionare lo script **NotificationReceiver** e trascinarlo nella **fotocamera principale.** Il risultato dovrebbe essere il seguente:

    ![trascinare lo script del ricevitore di notifiche nella fotocamera](images/AzureLabs-Lab8-98.png)

    > [!NOTE]
    > Se si sviluppa questo per il Microsoft HoloLens, è necessario aggiornare il  componente **Fotocamera** della fotocamera principale, in modo che:
    > - Cancella flag: colore a tinta unita
    > - Sfondo: nero

## <a name="chapter-16---build-the-mixed-reality-project-to-uwp"></a>Capitolo 16- Creare il modello di realtà mista Project alla UWP

Questo capitolo è identico al processo di compilazione per il progetto precedente. Tutto il necessario per la sezione Unity di questo progetto è stato completato, quindi è il momento di compilarlo da Unity.

1.  Passare a **Build Impostazioni** ( **File**  >  **Build Impostazioni** ).

2.  Dal menu **Compila Impostazioni** assicurarsi che **Unity C# Projects*** sia selezionato (che consente di modificare gli script in questo progetto, dopo la compilazione).

3.  Al termine, fare clic su **Compila**.

    ![progetto di compilazione](images/AzureLabs-Lab8-99.png)

4.  Verrà **visualizzata Esplora file** finestra di dialogo che richiede un percorso per la compilazione. Creare una nuova cartella (facendo clic **su Nuova cartella** nell'angolo superiore sinistro) e assegnare il nome **BUILDS**.

    ![cartella create builds](images/AzureLabs-Lab8-100.png)

    1.  Aprire la nuova **cartella BUILDS** e creare un'altra cartella (usando ancora una volta **Nuova** cartella) e assegnare il nome **NH \_ MR \_ App**.

        ![creare NH_MR_Apps cartella](images/AzureLabs-Lab8-101.png)

    2.  Con **l'app NH \_ MR \_** selezionata. fare **clic su Seleziona cartella**. La compilazione del progetto potrebbe richiedere circa un minuto.

5.  Dopo la compilazione, **Esplora file** verrà aperta una finestra di dialogo nel percorso del nuovo progetto.



## <a name="chapter-17---add-nuget-packages-to-the-unitymrnotifhub-solution"></a>Capitolo 17 - Aggiungere NuGet alla soluzione UnityMRNotifHub

> [!WARNING] 
> Tenere presente che, dopo aver aggiunto i pacchetti NuGet seguenti (e aver decommentato il codice nel capitolo [successivo),](#chapter-18---edit-unitymrnotifhub-application-notificationreceiver-class)il codice, quando viene riaperto all'interno del Project Unity, presenterà errori. Se si vuole tornare indietro e continuare a modificare nell'editor di Unity, è necessario commentare il codice eroso e rimuovere di nuovo il commento in un secondo momento, quando si torna a Visual Studio. 

Dopo aver completato la compilazione di realtà mista, passare al progetto di realtà mista compilato e fare doppio clic sul file della soluzione (con estensione sln) all'interno di tale cartella per aprire la soluzione con Visual Studio 2017.
A questo punto è necessario aggiungere il pacchetto di NuGet **WindowsAzure.Messaging.managed.** si tratta di una libreria usata per ricevere notifiche dall'hub di notifica.

Per importare il NuGet seguente:

1.  Nella finestra **di Esplora soluzioni** fare clic con il pulsante destro del mouse sulla soluzione

2.  Fare clic **su Gestisci NuGet pacchetti**.

    ![aprire nuget manager](images/AzureLabs-Lab8-102.png)

3.  Selezionare la scheda ***Sfoglia** _ e cercare _*WindowsAzure.Messaging.managed**.

    ![trovare il pacchetto di messaggistica di Windows Azure](images/AzureLabs-Lab8-103.png)

4.  Selezionare il risultato (come illustrato di seguito) e nella finestra a destra selezionare la casella di controllo accanto a **Project**. Verrà visualizzato un segno di spunta nella casella di controllo accanto **Project**, insieme alla casella di controllo accanto al **progetto Assembly-CSharp** e **UnityMRNotifHub.**

    ![Selezionare tutti i progetti](images/AzureLabs-Lab8-104.png)

5.  La versione specificata **inizialmente potrebbe non** essere compatibile con questo progetto. Fare quindi clic sul menu a discesa accanto a **Versione** e quindi su **Versione 0.1.7.9** e infine su **Installa.**

6.  L'installazione del pacchetto NuGet completata. Trovare il codice commentato immesso nella **classe NotificationReceiver** e rimuovere i commenti.



## <a name="chapter-18---edit-unitymrnotifhub-application-notificationreceiver-class"></a>Capitolo 18 - Modificare l'applicazione UnityMRNotifHub, classe NotificationReceiver

Dopo aver aggiunto **il NuGet ,** sarà  necessario rimuovere il commento da parte del codice all'interno della **classe NotificationReceiver.**

ad esempio:

1. Lo spazio dei nomi nella parte superiore:

    ```csharp
    using Microsoft.WindowsAzure.Messaging;
    ```

2. Tutto il codice all'interno **del metodo InitNotificationsAsync():**

    ```csharp
        /// <summary>
        /// Register this application to the Notification Hub Service
        /// </summary>
        private async void InitNotificationsAsync()
        {
            PushNotificationChannel channel = await PushNotificationChannelManager.CreatePushNotificationChannelForApplicationAsync();

            NotificationHub hub = new NotificationHub(hubName, hubListenEndpoint);

            Registration result = await hub.RegisterNativeAsync(channel.Uri);

            // If registration was successful, subscribe to Push Notifications
            if (result.RegistrationId != null)
            {
                Debug.Log($"Registration Successful: {result.RegistrationId}");
                channel.PushNotificationReceived += Channel_PushNotificationReceived;
            }
        }
    ```

> [!WARNING]
> Il codice precedente contiene un commento: assicurarsi di non aver accidentalmente *decommentato* tale commento (perché il codice non verrà compilato se presente).

3. Infine, l'evento **Channel_PushNotificationReceived** seguente:

    ```csharp
        /// <summary>
        /// Handler called when a Push Notification is received
        /// </summary>
        private void Channel_PushNotificationReceived(PushNotificationChannel sender, PushNotificationReceivedEventArgs args)
        {
            Debug.Log("New Push Notification Received");

            if (args.NotificationType == PushNotificationType.Raw)
            {
                //  Raw content of the Notification
                string jsonContent = args.RawNotification.Content;

                // Deserialize the Raw content into an AzureTableEntity object
                AzureTableEntity ate = JsonConvert.DeserializeObject<AzureTableEntity>(jsonContent);

                // The name of the Game Object to be moved
                gameObjectName = ate.RowKey;

                // The position where the Game Object has to be moved
                newObjPosition = new Vector3((float)ate.X, (float)ate.Y, (float)ate.Z);

                // Flag thats a notification has been received
                notifReceived = true;
            }
        }
    ```

Senza aggiungere il commento, assicurarsi di salvare e quindi passare al capitolo successivo.

## <a name="chapter-19---associate-the-mixed-reality-project-to-the-store-app"></a>Capitolo 19 : Associare il progetto di realtà mista all'app dello Store

È ora necessario associare il progetto **di realtà** mista all'app dello Store creata all'inizio del lab.

1.  Aprire la soluzione.

2.  Fare clic con il pulsante destro del mouse sul Project app UWP nel pannello Esplora soluzioni, passare a **Store** e **Associare l'app con lo Store...**.

    ![open store association](images/AzureLabs-Lab8-105.png)

3.  Verrà visualizzata una nuova finestra denominata **Associa l'app al Windows Store.** Fare clic su **Avanti**.

    ![Passare alla schermata successiva](images/AzureLabs-Lab8-106.png)

4.  Verranno caricate tutte le applicazioni associate all'account a cui è stato eseguito l'accesso. Se non si è connessi al proprio account, è possibile **accedere** a questa pagina.

5.  Trovare il **nome dell'app** dello Store creato all'inizio di questa esercitazione e selezionarlo. Quindi fare clic su **Next**.

    ![trovare e selezionare il nome del negozio](images/AzureLabs-Lab8-107.png)

6.  Fare clic su **Associa**.

    ![Associare l'app](images/AzureLabs-Lab8-108.png)

7.  L'app è ora **associata** all'app dello Store. Questa operazione è necessaria per l'abilitazione delle notifiche.

## <a name="chapter-20---deploy-unitymrnotifhub-and-unitydesktopnotifhub-applications"></a>Capitolo 20 : Distribuire applicazioni UnityMRNotifHub e UnityDesktopNotifHub

Questo capitolo può essere più semplice con due persone, in quanto il risultato includerà entrambe le app in esecuzione, una in esecuzione sul desktop del computer e l'altra all'interno del visore VR immersive.

L'app visore VR immersive è in attesa di ricevere modifiche alla scena (modifiche di posizione dei GameObject locali) e l'app desktop appoggerà le modifiche alla scena locale (modifiche alla posizione), che verranno condivise con l'app MR. È opportuno distribuire prima l'app MR, seguita dall'app desktop, in modo che il ricevitore possa iniziare l'ascolto.

Per distribuire **l'app UnityMRNotifHub** nel computer locale:

1.  Aprire il file della soluzione dell'app **UnityMRNotifHub** in **Visual Studio 2017.**

2.  In **Piattaforma soluzione selezionare** **x86, Computer locale.**

3.  In Configurazione **soluzione selezionare** **Debug.**

    ![impostare la configurazione del progetto](images/AzureLabs-Lab8-109.png)

4.  Passare al **menu Compila e** fare clic su **Distribuisci soluzione** per eseguire il sideload dell'applicazione nel computer.

5.  L'app dovrebbe ora essere visualizzata nell'elenco delle app installate, pronte per l'avvio.

Per distribuire **l'app UnityDesktopNotifHub** nel computer locale:

1.  Aprire il file della soluzione **dell'app UnityDesktopNotifHub** in **Visual Studio 2017.**

2.  In **Piattaforma soluzione selezionare** **x86, Computer locale.**

3.  In Configurazione **soluzione selezionare** **Debug.**

    ![impostare la configurazione del progetto](images/AzureLabs-Lab8-110.png)

4.  Passare al **menu Compila e** fare clic su **Distribuisci soluzione** per eseguire il sideload dell'applicazione nel computer.

5.  L'app dovrebbe ora essere visualizzata nell'elenco delle app installate, pronte per l'avvio.

6.  Avviare l'applicazione di realtà mista, seguita dall'applicazione desktop.

Con entrambe le applicazioni in esecuzione, spostare un oggetto nella scena del desktop (usando il pulsante sinistro del mouse). Queste modifiche posizionali verranno apportate in locale, serializzate e inviate al servizio app per le funzioni. Il servizio app per le funzioni aggiornerà quindi la tabella insieme all'hub di notifica. Dopo aver ricevuto un aggiornamento, l'hub di notifica invierà i dati aggiornati direttamente a tutte le applicazioni registrate (in questo caso l'app visore VR immersive), che deserializza i dati in ingresso e applica i nuovi dati posizionali agli oggetti locali, spostandoli nella scena.


## <a name="your-finished-your-azure-notification-hubs-application"></a>L'applicazione Hub di notifica di Azure è stata completata
 
È stata creata un'app di realtà mista che sfrutta il servizio Hub di notifica di Azure e consente la comunicazione tra le app.
 
![final product -end](images/AzureLabs-Lab8-00.png)
 
## <a name="bonus-exercises"></a>Esercizi aggiuntivi

### <a name="exercise-1"></a>Esercizio 1

È possibile capire come modificare il colore dei GameObject e inviare la notifica ad altre app che visualizzano la scena?

### <a name="exercise-2"></a>Esercizio 2

È possibile aggiungere lo spostamento dei GameObject all'app MR e visualizzare la scena aggiornata nell'app desktop?
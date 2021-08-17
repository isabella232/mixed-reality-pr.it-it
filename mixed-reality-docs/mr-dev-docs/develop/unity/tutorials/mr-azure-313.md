---
title: HoloLens (prima generazione) e Azure 313 - Servizio hub IoT
description: Informazioni su come implementare il servizio hub Azure IoT in una macchina virtuale che esegue Ubuntu 16.4 e visualizzare i dati dei messaggi usando Microsoft HoloLens o visore VR.
author: drneil
ms.author: jemccull
ms.date: 07/11/2018
ms.topic: article
keywords: azure, realtà mista, academy, edge, iot edge, esercitazione, api, notifica, funzioni, tabelle, hololens, immersive, vr, iot, macchina virtuale, ubuntu, python, Windows 10, Visual Studio
ms.openlocfilehash: fbd793a5941a5fa1b236403672680aa7df375f8d
ms.sourcegitcommit: 191c3d89c034714377d09fa91c07cbaa81301bae
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "121905768"
---
# <a name="hololens-1st-gen-and-azure-313-iot-hub-service"></a>HoloLens (prima generazione) e Azure 313: Servizio hub IoT

>[!NOTE]
>Le esercitazioni di Mixed Reality Academy sono state progettate in base a HoloLens (prima generazione) e ai visori VR immersive di realtà mista.  Pertanto, riteniamo importante lasciarle a disposizione degli sviluppatori a cui serve ancora materiale sussidiario per lo sviluppo di questi dispositivi.  Queste esercitazioni **_non_** verranno aggiornate con i set di strumenti o le interazioni più recenti usati per HoloLens 2.  Rimarranno invariate per consentire di continuare a lavorare sui dispositivi supportati. In futuro verrà pubblicata una nuova serie di esercitazioni che illustrano come sviluppare per HoloLens 2.  Questa comunicazione verrà aggiornata con un collegamento a tali esercitazioni al momento della pubblicazione.

![risultato del corso](images/AzureLabs-Lab313-00.png)

In questo corso si apprenderà come implementare un servizio **hub** di Azure IoT in una macchina virtuale che esegue il sistema operativo Ubuntu 16.4. Verrà **quindi usata un'app** per le funzioni di Azure per ricevere messaggi dalla macchina virtuale Ubuntu e archiviare il risultato all'interno di un servizio **tabelle di Azure.** Sarà quindi possibile visualizzare questi  dati usando Power BI su Microsoft HoloLens visore VR immersive.

Il contenuto di  questo corso è applicabile ai dispositivi IoT Edge, anche se ai fini di questo corso l'attenzione sarà incentrata sull'ambiente di una macchina virtuale, in modo che l'accesso a un dispositivo perimetrale fisico non sia necessario.

Completando questo corso, si apprenderà come:

- Distribuire un **IoT Edge in** una macchina virtuale (sistema operativo Ubuntu 16), che rappresenterà il dispositivo IoT.
- Aggiungere un **modello di Azure Visione personalizzata Tensorflow** al modulo Edge, con il codice che analerà le immagini archiviate nel contenitore.
- Configurare il modulo per inviare il messaggio dei risultati dell'analisi al servizio **hub IoT.**
- Usare **un'app per le funzioni di Azure** per archiviare il messaggio all'interno di una tabella di **Azure.**
- Configurare le **Power BI** raccogliere il messaggio archiviato e creare un report.
- Visualizzare i dati dei messaggi IoT **all'interno Power BI**.

I servizi che verranno utilizzati includono:

- **Azure IoT Hub** è un servizio Microsoft Azure che consente agli sviluppatori di connettere, monitorare e gestire asset IoT. Per altre informazioni, visitare la [ **pagina Azure IoT Servizio Hub.**](https://azure.microsoft.com/services/iot-hub/)

- **Registro Azure Container** è un servizio Microsoft Azure che consente agli sviluppatori di archiviare immagini del contenitore per vari tipi di contenitori. Per altre informazioni, visitare la [ **pagina Registro Azure Container Service**](https://azure.microsoft.com/services/container-registry/).

- **L'app** per le funzioni di Azure Microsoft Azure servizio, che consente agli sviluppatori di eseguire piccole parti di codice, "funzioni", in Azure. In questo modo è possibile delegare il lavoro al cloud, anziché all'applicazione locale, che può avere molti vantaggi. **Funzioni di Azure** supporta diversi linguaggi di sviluppo, tra cui \# \# C, F, Node.js, Java e PHP. Per altre informazioni, visitare la [ **pagina Funzioni di Azure** .](/azure/azure-functions/functions-overview)

- **Archiviazione di Azure: Tables** è un servizio Microsoft Azure, che consente agli sviluppatori di archiviare dati strutturati, non SQL, nel cloud, rendendoli facilmente accessibili ovunque. Il servizio offre una progettazione senza schema, consentendo l'evoluzione delle tabelle in base alle esigenze e pertanto è molto flessibile. Per altre informazioni, visitare la pagina [ **Tabelle di Azure**](/azure/cosmos-db/table-storage-overview)

Questo corso illustra come configurare e usare il servizio hub IoT e quindi visualizzare una risposta fornita da un dispositivo. L'utente dovrà applicare questi concetti a una configurazione personalizzata del servizio hub IoT, che potrebbe essere compilata.

## <a name="device-support"></a>Supporto di dispositivi

<table>
<tr>
<th>Corso</th><th style="width:150px"> <a href="/hololens/hololens1-hardware">HoloLens</a></th><th style="width:150px"> <a href="../../../discover/immersive-headset-hardware-details.md">Visori VR immersive</a></th>
</tr><tr>
<td> MR e Azure 313: Servizio Hub IoT</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="prerequisites"></a>Prerequisiti

Per i prerequisiti più aggiornati per lo sviluppo con realtà mista, incluso il Microsoft HoloLens, vedere l'articolo Installare [gli](../../install-the-tools.md) strumenti.

> [!NOTE]
> Questa esercitazione è destinata agli sviluppatori che hanno esperienza di base con Python. Tenere presente anche che i prerequisiti e le istruzioni scritte all'interno di questo documento rappresentano ciò che è stato testato e verificato al momento della stesura di questo documento (luglio 2018). È possibile usare il software più recente, come indicato nell'articolo Installare gli strumenti, anche se non si presuppone che le informazioni contenute in questo corso corrispondano perfettamente a quelle disponibili nel software più recente rispetto a quelle elencate di seguito. [](../../install-the-tools.md)

Sono necessari i componenti hardware e software seguenti:

- Windows 10 Fall Creators Update (o versione successiva), **modalità sviluppatore abilitata**

    > [!WARNING]
    > Non è possibile eseguire una macchina virtuale usando Hyper-V in Windows 10 Home Edition.

- Windows 10 SDK (versione più recente)
- A HoloLens, **modalità sviluppatore abilitata**
- Visual Studio 2017.15.4 (usato solo per accedere all'istanza di Azure Cloud Explorer)
- Accesso a Internet per Azure e per il servizio hub IoT. Per altre informazioni, seguire questo collegamento [alla pagina del servizio hub IoT](https://azure.microsoft.com/services/iot-hub/)
- Un modello di Machine Learning. Se non si dispone di un modello pronto per l'uso, [è possibile usare il modello fornito con questo corso.](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20313%20-%20IoT%20Hub%20Service/Custom%20Vision%20Model.zip)
- **Software Hyper-V** abilitato nel computer Windows 10 di sviluppo.
- Una macchina virtuale che esegue Ubuntu (16.4 o 18.4), in esecuzione nel computer di sviluppo o in alternativa è possibile usare un computer separato che esegue Linux (Ubuntu 16.4 o 18.4). Per altre informazioni su come creare una macchina virtuale in Windows con Hyper-V, vedere il capitolo ["Prima di iniziare".](#before-you-start) (https://docs.microsoft.com/virtualization/hyper-v-on-windows/quick-start/quick-create-virtual-machine).  



### <a name="before-you-start"></a>Prima di iniziare

1. Configurare e testare l'HoloLens. Se è necessario supporto per la configurazione del HoloLens, [vedere l'articolo HoloLens configurazione.](/hololens/hololens-setup)
2. È buona idea eseguire  la  calibrazione e l'ottimizzazione dei sensori quando si inizia a sviluppare una nuova app HoloLens (a volte può essere utile eseguire tali attività per ogni utente).

Per informazioni sulla calibrazione, fare clic su questo [collegamento all'HoloLens calibrazione.](/hololens/hololens-calibration#hololens-2)

Per informazioni sull'ottimizzazione dei sensori, fare clic su questo collegamento [all'HoloLens sull'ottimizzazione dei sensori.](/hololens/hololens-updates)

3. Configurare la **macchina virtuale Ubuntu** **usando Hyper-V.** Le risorse seguenti sono utili per il processo.
    1.  Per prima cosa, seguire questo collegamento per scaricare [l'iso di Ubuntu 16.04.4 LTS (Xenial Xerus).](https://au.releases.ubuntu.com/16.04/) Selezionare **l'immagine desktop del PC a 64 bit (AMD64).**
    2.  Assicurarsi che **Hyper-V** sia abilitato nel computer Windows 10 virtuale. È possibile seguire questo collegamento per indicazioni [sull'installazione e l'abilitazione di Hyper-V in Windows 10](/virtualization/hyper-v-on-windows/quick-start/enable-hyper-v).
    3.  Avviare Hyper-V e creare una nuova macchina virtuale Ubuntu. È possibile seguire questo collegamento per [una guida dettagliata su come creare una macchina virtuale con Hyper-V.](/virtualization/hyper-v-on-windows/quick-start/create-virtual-machine) Quando viene richiesto di installare un sistema operativo da un file di immagine di **avvio,** selezionare l'immagine **ISO Ubuntu** scaricata in precedenza.

    > [!NOTE]
    > **L'uso della creazione rapida di Hyper-V** non è consigliato.  

## <a name="chapter-1---retrieve-the-custom-vision-model"></a>Capitolo 1: Recuperare il modello Visione personalizzata dati

Con questo corso si avrà accesso [a](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20313%20-%20IoT%20Hub%20Service/Custom%20Vision%20Model.zip) un modello di Visione personalizzata predefinito che rileva tastiere e mouse dalle immagini. Se si usa questa opzione, passare al [capitolo 2.](#chapter-2---the-container-registry-service)

È tuttavia possibile seguire questa procedura se si vuole usare un modello Visione personalizzata personalizzato:

1. Nel **Visione personalizzata Project** passare alla **scheda** Prestazioni.

    > [!WARNING]
    > Il modello deve usare un *dominio* compatto per esportare il modello. È possibile modificare il dominio dei modelli nelle impostazioni per il progetto.

    ![scheda prestazioni](images/AzureLabs-Lab313-01.png)

2. Selezionare **l'iterazione** da esportare e fare clic su **Esporta.** Verrà visualizzato un pannello.

    ![pannello esporta](images/AzureLabs-Lab313-02.png)

3. Nel pannello fare clic su **File Docker**.

    ![selezionare docker](images/AzureLabs-Lab313-03.png)

4. Fare clic su **Linux** nel menu a discesa e quindi fare clic su **Scarica.**

    ![Fare clic su Download](images/AzureLabs-Lab313-04.png)

5. Decomprimere il contenuto. Verrà utilizzato più avanti in questo corso.

## <a name="chapter-2---the-container-registry-service"></a>Capitolo 2- Servizio Registro Container

Il **servizio Registro Container** è il repository usato per ospitare i contenitori.

Il **servizio hub IoT** che verrà compilato e  utilizzato in questo corso fa riferimento al servizio Registro Container per ottenere i contenitori da distribuire nel dispositivo Edge.

1. Prima di tutto, [seguire questo collegamento al portale di Azure](https://portal.azure.com/)e accedere con le proprie credenziali.

2. Passare a **Crea una risorsa e** cercare Registro **Container.**

    ![registro contenitori](images/AzureLabs-Lab313-05.png)

3. Fare clic su **Crea**.

    ![](images/AzureLabs-Lab313-06.png)

4. Impostare i parametri di configurazione del servizio:

    1. Inserire un nome per il progetto, denominato **IoTCRegistry** in questo esempio.

    2. Scegliere un **gruppo di risorse** o crearne uno nuovo. Un gruppo di risorse consente di monitorare, controllare l'accesso, effettuare il provisioning e gestire la fatturazione per una raccolta di asset di Azure. È consigliabile mantenere tutti i servizi di Azure associati a un singolo progetto (ad esempio, questi corsi) in un gruppo di risorse comune.

    3. Impostare la posizione del servizio.

    4. Impostare **Utente amministratore** su **Abilita**.

    5. Impostare **SKU** su **Basic.** 

    ![](images/AzureLabs-Lab313-07.png)

5. Fare **clic** su Crea e attendere la creazione dei servizi. 

6. Quando viene visualizzata la notifica che informa dell'esito positivo della creazione del Registro *Container,* fare clic su **Vai** alla risorsa per essere reindirizzati alla pagina Del servizio.

    ![](images/AzureLabs-Lab313-08.png)

7. Nella pagina *Servizio Registro Container* fare clic su Chiavi di **accesso**.

8. Prendere nota (è possibile usare il Blocco note) dei parametri seguenti:
    1. **Server di accesso**
    2. **Nome utente**
    3. **Password**

    ![](images/AzureLabs-Lab313-09.png)

## <a name="chapter-3---the-iot-hub-service"></a>Capitolo 3: Servizio hub IoT

A questo punto si inizierà la creazione e la configurazione del **servizio hub IoT.**

1. Se non è già stato eseguito l'accesso, accedere al [portale di Azure.](https://portal.azure.com)

2.  Dopo aver effettuato l'accesso, fare clic su Crea una risorsa nell'angolo in alto **a** sinistra, cercare **Hub IoT** e fare clic su **Invio.**

 ![cercare l'account di archiviazione](images/AzureLabs-Lab313-10.png)

3.  La nuova pagina fornirà una descrizione del servizio **dell Archiviazione account** utente. Nella parte inferiore sinistra del prompt fare clic sul **pulsante Crea** per creare un'istanza del servizio.

    ![creare un'istanza di archiviazione](images/AzureLabs-Lab313-11.png)

4.  Dopo aver fatto clic su **Crea,** verrà visualizzato un pannello:

    1. Scegliere un **gruppo di risorse** o crearne uno nuovo. Un gruppo di risorse consente di monitorare, controllare l'accesso, effettuare il provisioning e gestire la fatturazione per una raccolta di asset di Azure. È consigliabile mantenere tutti i servizi di Azure associati a un singolo progetto (ad esempio, questi corsi) in un gruppo di risorse comune.

        > Per altre informazioni sui gruppi di risorse di Azure, fare clic su questo collegamento per [gestire un gruppo di risorse.](/azure/azure-resource-manager/resource-group-portal)


    2. Selezionare una località **appropriata** (usare la stessa località in tutti i servizi creati in questo corso).

    3. Inserire il nome **desiderato per** questa istanza del servizio.    

5.  Nella parte inferiore della pagina fare clic su **Avanti: Ridimensiona e ridimensiona**.

    ![creare un'istanza di archiviazione](images/AzureLabs-Lab313-12.png)

6.  In questa pagina selezionare il piano **tariffario** e il livello di scalabilità. Se si tratta della prima istanza del servizio hub IoT, dovrebbe essere disponibile un livello gratuito.  

7.  Fare clic **su Rivedi e crea.**

    ![creare un'istanza di archiviazione](images/AzureLabs-Lab313-13.png)

8.  Rivedere le impostazioni e fare clic su **Crea.**

    ![creare un'istanza di archiviazione](images/AzureLabs-Lab313-14.png)

9. Quando viene visualizzata la notifica che informa della corretta creazione del servizio *hub IoT,* fare clic su **Vai** alla risorsa per essere reindirizzati alla pagina Servizio.

    ![creare un'istanza di archiviazione](images/AzureLabs-Lab313-15.png)

10. Scorrere il pannello laterale a sinistra fino a visualizzare *Gestione automatica* dei dispositivi , fare clic su **IoT Edge**.

    ![creare un'istanza di archiviazione](images/AzureLabs-Lab313-16.png)

11. Nella finestra visualizzata a destra fare clic su Aggiungi IoT Edge **dispositivo**. Verrà visualizzato un pannello a destra.

12. Nel pannello fornire al nuovo dispositivo un **ID dispositivo** (nome a scelta). Fare quindi clic su **Salva**. Le *chiavi primaria* e *secondaria* verranno generate automaticamente, se la generazione automatica **è** selezionata.

    ![creare un'istanza di archiviazione](images/AzureLabs-Lab313-17.png)

13. Si tornerà alla sezione Dispositivi *IoT Edge,* in cui verrà elencato il nuovo dispositivo. Fare clic sul nuovo dispositivo (indicato in rosso nell'immagine seguente). 

    ![creare un'istanza di archiviazione](images/AzureLabs-Lab313-18.png)

14. Nella pagina *Dettagli dispositivo* visualizzata eseguire una copia della stringa di **connessione** (chiave primaria).

    ![creare un'istanza di archiviazione](images/AzureLabs-Lab313-19.png)

15. Tornare al pannello a sinistra e fare clic su Criteri *di accesso condiviso* per aprirlo. 

16. Nella pagina visualizzata fare clic su **iothubowner** per visualizzare un pannello a destra della schermata. 

17. Prendere nota (nell'Blocco note) della stringa di connessione **(chiave** primaria) per usarla in seguito durante l'impostazione della stringa *di* connessione sul dispositivo.

    ![creare un'istanza di archiviazione](images/AzureLabs-Lab313-20.png)

## <a name="chapter-4---setting-up-the-development-environment"></a>Capitolo 4 - Configurazione dell'ambiente di sviluppo

Per creare e distribuire moduli per *l'hub IoT Edge,* è necessario installare i componenti seguenti nel computer di sviluppo che esegue Windows 10:

1.  [Docker per Windows](https://store.docker.com/editions/community/docker-ce-desktop-windows), verrà chiesto di creare un account per poterlo scaricare. 

    [![scaricare Docker per Windows](images/AzureLabs-Lab313-21.png)](https://store.docker.com/editions/community/docker-ce-desktop-windows)

    > [!IMPORTANT]
    > Docker richiede *Windows 10 PRO,* *Enterprise 14393* o *Windows Server 2016 RTM* per l'esecuzione. Se si eseguono altre versioni di Windows 10, è possibile provare a installare Docker usando la casella [degli strumenti di Docker.](https://docs.docker.com/toolbox/toolbox_install_windows/)

2.  [Python 3.6](https://www.python.org/downloads/).

    [![scaricare Python 3.6](images/AzureLabs-Lab313-22.png)](https://www.python.org/downloads/)

3.  [Visual Studio Code (noto anche come VS Code)](https://code.visualstudio.com/download).

    [![Scaricare VS Code](images/AzureLabs-Lab313-23.png)](https://code.visualstudio.com/download)

Dopo aver installato il software indicato in precedenza, è necessario riavviare il computer.

## <a name="chapter-5---setting-up-the-ubuntu-environment"></a>Capitolo 5 - Configurazione dell'ambiente Ubuntu

A questo punto è possibile passare alla configurazione del dispositivo che **esegue il sistema operativo Ubuntu.** Per installare il software necessario, seguire questa procedura per distribuire i contenitori nella scheda:

> [!IMPORTANT]
> È necessario far precedere sempre i comandi del terminale **con sudo per** l'esecuzione come utente amministratore. Cioè:
> 
>   ```bash
>   sudo docker \<option> \<command> \<argument>
>   ```

1.  Aprire il **terminale Ubuntu** e usare il comando seguente per installare **pip**:

    > [! HINT] È possibile aprire *Terminale* molto facilmente usando i tasti di scelta rapida **CTRL+ALT+T.**

    ```bash
        sudo apt-get install python-pip
    ```

2.  In questo capitolo, terminale potrebbe richiedere l'autorizzazione per usare l'archiviazione del dispositivo e immettere **y/n** (sì o no), digitare **"y"** e quindi premere **INVIO** per accettare.

3.  Al termine del comando, usare il comando seguente per installare **curl**:

    ```bash
        sudo apt install curl
    ```

4.  Dopo aver installato **pip** e **curl,** usare il comando seguente per installare il **runtime di IoT Edge**, necessario per distribuire e controllare i moduli nella scheda:

    ```bash
        curl https://packages.microsoft.com/config/ubuntu/16.04/prod.list > ./microsoft-prod.list

        sudo cp ./microsoft-prod.list /etc/apt/sources.list.d/

        curl https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > microsoft.gpg

        sudo cp ./microsoft.gpg /etc/apt/trusted.gpg.d/

        sudo apt-get update

        sudo apt-get install moby-engine

        sudo apt-get install moby-cli

        sudo apt-get update

        sudo apt-get install iotedge
    ```

5. A questo punto verrà richiesto di aprire il file di configurazione di *runtime*, per inserire la stringa di connessione del dispositivo **,** di cui si è noti (nel Blocco note), durante la creazione del servizio hub **IoT** ( al passaggio [14,](#chapter-3---the-iot-hub-service)del capitolo 3). Eseguire la riga seguente nel terminale per aprire il file:

    ```bash
        sudo nano /etc/iotedge/config.yaml
    ```

6. Verrà visualizzato il file **config.yaml,** pronto per la modifica:

    > [!WARNING]
    > Quando si apre questo file, potrebbe generare confusione. Si modificherà il testo di questo file, all'interno del *terminale* stesso. 

    1.  Usare i tasti di direzione sulla tastiera per scorrere verso il basso (sarà necessario scorrere verso il basso un po' verso il basso), per raggiungere la riga che contiene":

        "**\<ADD DEVICE CONNECTION STRING HERE>**".

    2. Sostituire la riga , **incluse le parentesi quadre**, con la **stringa di connessione del** dispositivo di cui si è già fatto clic in precedenza.

7. Dopo avere premuta la stringa di connessione, premere i tasti **CTRL+X** per salvare il file. Verrà chiesto di confermare digitando **Y**. Premere quindi **INVIO** per confermare. Si tornerà al normale *terminale*. 

8. Dopo che tutti questi comandi sono stati eseguiti correttamente, sarà stato installato **IoT Edge Runtime** di . Una volta inizializzato, il runtime si avvia da solo ogni volta che il dispositivo viene acceso e si trova in background, in attesa della distribuzione dei moduli dal servizio **hub IoT.**

9.  Eseguire la riga di comando seguente per inizializzare *IoT Edge Runtime*:

    ```bash
        sudo systemctl restart iotedge
    ```

    > [!IMPORTANT]
    > Se si apportano modifiche al file yaml o all'installazione precedente, sarà necessario eseguire di nuovo la riga di riavvio precedente, all'interno di *Terminale*.

10. Controllare lo *IoT Edge runtime* eseguendo la riga di comando seguente. Il runtime dovrebbe essere visualizzato con lo **stato attivo (in esecuzione)** in verde.

    ```bash
        sudo systemctl status iotedge
    ```

11. Premere **CTRL+C** per uscire dalla pagina di stato. È possibile verificare che il *runtime IoT Edge estrae* correttamente i contenitori digitando il comando seguente:

    ```bash
        sudo docker ps
    ```

12. Verrà visualizzato un elenco con due (2) contenitori. Si tratta dei moduli predefiniti creati automaticamente dal servizio hub IoT (edgeAgent ed edgeHub). Dopo aver creato e distribuito i propri moduli, questi verranno visualizzati in questo elenco, sotto quelli predefiniti.

## <a name="chapter-6---install-the-extensions"></a>Capitolo 6- Installare le estensioni

> [!IMPORTANT]
> I successivi capitoli (6-9) devono essere eseguiti nel computer Windows 10 macchina virtuale.

1. Aprire **VS Code**.

2. Fare clic sul **pulsante Estensioni** (quadrato) sulla barra sinistra VS Code per aprire il **pannello Estensioni**.

3. Cercare e installare le estensioni seguenti (come illustrato nell'immagine seguente):

    1. Azure IoT Edge
    2. Azure IoT Toolkit
    3. Docker   

    ![Creare il contenitore](images/AzureLabs-Lab313-24.png)

4. Dopo aver installato le estensioni, chiudere e ria aprirle VS Code.

5. Dopo VS Code ancora una volta, passare a **Visualizza**  >  **terminale integrato.**

6. A questo punto si **installerà Cookiecutter**. Nel terminale eseguire il comando bash seguente:

    ```bash
        pip install --upgrade --user cookiecutter
    ```

    > [! HINT] In caso di problemi con questo comando: 
    >1. Riavviare VS Code e/o il computer.
    >2. Potrebbe essere necessario passare dal **terminale VS Code a** quello in uso per installare Python, ad esempio **PowerShell,** in particolare nel caso in cui l'ambiente Python sia già installato nel computer. Con il terminale aperto, il menu a discesa si trova sul lato destro del terminale.
     ![Creare il contenitore](images/AzureLabs-Lab313-24b.png) 
    >3. Assicurarsi che il **percorso di** installazione di Python sia aggiunto come **variabile di** ambiente nel computer. Cookiecutter deve far parte dello stesso percorso. Seguire questo collegamento [per altre informazioni sulle variabili di ambiente](/windows/win32/procthread/environment-variables), 

7. Al **termine dell'installazione di Cookiecutter,** è necessario riavviare il computer, in modo che **Cookiecutter** venga riconosciuto come comando, all'interno dell'ambiente del sistema.

## <a name="chapter-7---create-your-container-solution"></a>Capitolo 7: Creare la soluzione contenitore

A questo punto, è necessario creare il contenitore con il modulo di cui eseguire il push nel Registro *Container.* Dopo aver eseguito il push del contenitore, si userà il servizio *IoT Hub Edge* per distribuirlo nel dispositivo, che esegue il *runtime IoT Edge.*

1. Da VS Code fare clic su **Visualizza**  >  **riquadro comandi.**

2. Nella tavolozza cercare ed eseguire Azure IoT **Edge: Nuova soluzione IoT Edge.**

3. Passare a un percorso in cui si vuole creare la soluzione. Premere **INVIO** per accettare il percorso.

4. Assegnare un nome alla soluzione. Premere **INVIO** per confermare il nome specificato.

5. A questo punto verrà richiesto di scegliere il framework del modello per la soluzione. Fare clic **su Python Module (Modulo Python).** Premere **INVIO** per confermare questa scelta.

6. Assegnare un nome al modulo. Premere **INVIO** per confermare il nome del modulo. Assicurarsi di prendere nota del nome del modulo (con Blocco note) perché verrà usato in un secondo momento.

7. Si noterà che nella tavolozza verrà visualizzato un indirizzo predefinito del repository di immagini *Docker.* L'aspetto sarà simile al seguente:

    **localhost:5000/-NOME DEL MODULO-**. 

8. Eliminare **localhost:5000** e al suo  posto inserire l'indirizzo del **server** di accesso del registro contenitori, di cui si è avuto una notata durante la creazione del servizio Registro Container **(** nel passaggio 8 del capitolo [2).](#chapter-2---the-container-registry-service) Premere **INVIO** per confermare l'indirizzo.

9. A questo punto, verrà creata la soluzione contenente il modello per il modulo Python e la relativa struttura verrà visualizzata nella scheda Esplora di VS Code, sul lato sinistro della schermata. Se la **scheda Esplora** non è aperta, è possibile aprirla facendo clic sul pulsante in alto nella barra a sinistra.

    ![Creare il contenitore](images/AzureLabs-Lab313-25.png)

10. L'ultimo passaggio di questo capitolo consiste nel fare clic e aprire il  **file con** estensione env dalla scheda **Esplora** e aggiungere il nome utente e **la** **password** di Registro Container. Questo file viene ignorato da Git, ma durante la compilazione del contenitore, imposta le credenziali per accedere al **servizio Registro Container.**

    ![Creare il contenitore](images/AzureLabs-Lab313-26.png)

## <a name="chapter-8---editing-your-container-solution"></a>Capitolo 8- Modifica della soluzione contenitore

A questo punto si completerà la soluzione contenitore aggiornando i file seguenti:

- *script <span></span> Python con* estensione py principale.
- *requirements.txt*.
- *deployment.template.jsin*.
- *Dockerfile.amd64*

Si creerà quindi la *cartella images,* usata dallo script Python per verificare la corrispondenza delle immagini con *il modello Visione personalizzata.* Infine, si aggiungeranno il file *labels.txt,* per facilitare la lettura del modello, e il file *model.pb,* che è il modello.

1. Con VS Code aperto, passare alla cartella del modulo e cercare lo script denominato **main <span></span> .py**. Fare doppio clic per aprirlo.

2. Eliminare il contenuto del file e inserire il codice seguente:

    ```python
    # Copyright (c) Microsoft. All rights reserved.
    # Licensed under the MIT license. See LICENSE file in the project root for
    # full license information.

    import random
    import sched, time
    import sys
    import iothub_client
    from iothub_client import IoTHubModuleClient, IoTHubClientError, IoTHubTransportProvider
    from iothub_client import IoTHubMessage, IoTHubMessageDispositionResult, IoTHubError
    import json
    import os
    import tensorflow as tf
    import os
    from PIL import Image
    import numpy as np
    import cv2

    # messageTimeout - the maximum time in milliseconds until a message times out.
    # The timeout period starts at IoTHubModuleClient.send_event_async.
    # By default, messages do not expire.
    MESSAGE_TIMEOUT = 10000

    # global counters
    RECEIVE_CALLBACKS = 0
    SEND_CALLBACKS = 0

    TEMPERATURE_THRESHOLD = 25
    TWIN_CALLBACKS = 0

    # Choose HTTP, AMQP or MQTT as transport protocol.  Currently only MQTT is supported.
    PROTOCOL = IoTHubTransportProvider.MQTT


    # Callback received when the message that we're forwarding is processed.
    def send_confirmation_callback(message, result, user_context):
        global SEND_CALLBACKS
        print ( "Confirmation[%d] received for message with result = %s" % (user_context, result) )
        map_properties = message.properties()
        key_value_pair = map_properties.get_internals()
        print ( "    Properties: %s" % key_value_pair )
        SEND_CALLBACKS += 1
        print ( "    Total calls confirmed: %d" % SEND_CALLBACKS )


    def convert_to_opencv(image):
        # RGB -> BGR conversion is performed as well.
        r,g,b = np.array(image).T
        opencv_image = np.array([b,g,r]).transpose()
        return opencv_image

    def crop_center(img,cropx,cropy):
        h, w = img.shape[:2]
        startx = w//2-(cropx//2)
        starty = h//2-(cropy//2)
        return img[starty:starty+cropy, startx:startx+cropx]

    def resize_down_to_1600_max_dim(image):
        h, w = image.shape[:2]
        if (h < 1600 and w < 1600):
            return image

        new_size = (1600 * w // h, 1600) if (h > w) else (1600, 1600 * h // w)
        return cv2.resize(image, new_size, interpolation = cv2.INTER_LINEAR)

    def resize_to_256_square(image):
        h, w = image.shape[:2]
        return cv2.resize(image, (256, 256), interpolation = cv2.INTER_LINEAR)

    def update_orientation(image):
        exif_orientation_tag = 0x0112
        if hasattr(image, '_getexif'):
            exif = image._getexif()
            if (exif != None and exif_orientation_tag in exif):
                orientation = exif.get(exif_orientation_tag, 1)
                # orientation is 1 based, shift to zero based and flip/transpose based on 0-based values
                orientation -= 1
                if orientation >= 4:
                    image = image.transpose(Image.TRANSPOSE)
                if orientation == 2 or orientation == 3 or orientation == 6 or orientation == 7:
                    image = image.transpose(Image.FLIP_TOP_BOTTOM)
                if orientation == 1 or orientation == 2 or orientation == 5 or orientation == 6:
                    image = image.transpose(Image.FLIP_LEFT_RIGHT)
        return image


    def analyse(hubManager):

        messages_sent = 0;

        while True:
            #def send_message():
            print ("Load the model into the project")
            # These names are part of the model and cannot be changed.
            output_layer = 'loss:0'
            input_node = 'Placeholder:0'

            graph_def = tf.GraphDef()
            labels = []

            labels_filename = "labels.txt"
            filename = "model.pb"

            # Import the TF graph
            with tf.gfile.FastGFile(filename, 'rb') as f:
                graph_def.ParseFromString(f.read())
                tf.import_graph_def(graph_def, name='')

            # Create a list of labels
            with open(labels_filename, 'rt') as lf:
                for l in lf:
                    labels.append(l.strip())
            print ("Model loaded into the project")

            results_dic = dict()

            # create the JSON to be sent as a message
            json_message = ''

            # Iterate through images 
            print ("List of images to analyse:")
            for file in os.listdir('images'):
                print(file)

                image = Image.open("images/" + file)

                # Update orientation based on EXIF tags, if the file has orientation info.
                image = update_orientation(image)

                # Convert to OpenCV format
                image = convert_to_opencv(image)

                # If the image has either w or h greater than 1600 we resize it down respecting
                # aspect ratio such that the largest dimension is 1600
                image = resize_down_to_1600_max_dim(image)

                # We next get the largest center square
                h, w = image.shape[:2]
                min_dim = min(w,h)
                max_square_image = crop_center(image, min_dim, min_dim)

                # Resize that square down to 256x256
                augmented_image = resize_to_256_square(max_square_image)

                # The compact models have a network size of 227x227, the model requires this size.
                network_input_size = 227

                # Crop the center for the specified network_input_Size
                augmented_image = crop_center(augmented_image, network_input_size, network_input_size)

                try:
                    with tf.Session() as sess:     
                        prob_tensor = sess.graph.get_tensor_by_name(output_layer)
                        predictions, = sess.run(prob_tensor, {input_node: [augmented_image] })
                except Exception as identifier:
                    print ("Identifier error: ", identifier)

                print ("Print the highest probability label")
                highest_probability_index = np.argmax(predictions)
                print('FINAL RESULT! Classified as: ' + labels[highest_probability_index])

                l = labels[highest_probability_index]

                results_dic[file] = l

                # Or you can print out all of the results mapping labels to probabilities.
                label_index = 0
                for p in predictions:
                    truncated_probablity = np.float64(round(p,8))
                    print (labels[label_index], truncated_probablity)
                    label_index += 1

            print("Results dictionary")
            print(results_dic)

            json_message = json.dumps(results_dic)
            print("Json result")
            print(json_message)

            # Initialize a new message
            message = IoTHubMessage(bytearray(json_message, 'utf8'))
        
            hubManager.send_event_to_output("output1", message, 0)

            messages_sent += 1
            print("Message sent! - Total: " + str(messages_sent))      
            print('----------------------------')
            
            # This is the wait time before repeating the analysis
            # Currently set to 10 seconds
            time.sleep(10)


    class HubManager(object):
        
        def __init__(
                self,
                protocol=IoTHubTransportProvider.MQTT):
            self.client_protocol = protocol
            self.client = IoTHubModuleClient()
            self.client.create_from_environment(protocol)

            # set the time until a message times out
            self.client.set_option("messageTimeout", MESSAGE_TIMEOUT)

        # Forwards the message received onto the next stage in the process.
        def forward_event_to_output(self, outputQueueName, event, send_context):
            self.client.send_event_async(
                outputQueueName, event, send_confirmation_callback, send_context)

        def send_event_to_output(self, outputQueueName, event, send_context):
            self.client.send_event_async(outputQueueName, event, send_confirmation_callback, send_context)

    def main(protocol):
        try:
            hub_manager = HubManager(protocol)
            analyse(hub_manager)
            while True:
                time.sleep(1)

        except IoTHubError as iothub_error:
            print ( "Unexpected error %s from IoTHub" % iothub_error )
            return
        except KeyboardInterrupt:
            print ( "IoTHubModuleClient sample stopped" )

    if __name__ == '__main__':
        main(PROTOCOL)
    ```

3.  Aprire il file denominato **requirements.txt** e sostituirne il contenuto con il codice seguente:

    ```
    azure-iothub-device-client==1.4.0.0b3
    opencv-python==3.3.1.11
    tensorflow==1.8.0
    pillow==5.1.0
    ```

4.  Aprire il file denominato **deployment.template.jsin** e sostituirne il contenuto seguendo le linee guida seguenti:

    1. Poiché si avrà una propria struttura JSON univoca, sarà necessario modificarla manualmente anziché copiare un esempio. Per semplificare questa operazione, usare l'immagine seguente come guida.
    2. Le aree che avranno un aspetto diverso da quello dell'utente, ma che NON **è consigliabile modificare, sono evidenziate in giallo.**
    3. **Le sezioni da eliminare sono evidenziate in rosso.**
    4. Prestare attenzione a eliminare le parentesi quadre corrette e rimuovere anche le virgole.

        ![Creare il contenitore](images/AzureLabs-Lab313-27.png)

    5. Il codice JSON completato dovrebbe essere simile all'immagine seguente (tuttavia, con le differenze univoche: *nome utente/password/nome modulo/riferimenti al modulo):*

        ![Creare il contenitore](images/AzureLabs-Lab313-28.png)

5.  Aprire il file denominato **Dockerfile.amd64** e sostituirne il contenuto con il codice seguente:

    ```
    FROM ubuntu:xenial

    WORKDIR /app

    RUN apt-get update && \
        apt-get install -y --no-install-recommends libcurl4-openssl-dev python-pip libboost-python-dev && \
        rm -rf /var/lib/apt/lists/* 
    RUN pip install --upgrade pip
    RUN pip install setuptools

    COPY requirements.txt ./
    RUN pip install -r requirements.txt

    RUN pip install pillow
    RUN pip install numpy

    RUN apt-get update && apt-get install -y \ 
        pkg-config \
        python-dev \ 
        python-opencv \ 
        libopencv-dev \ 
        libav-tools  \ 
        libjpeg-dev \ 
        libpng-dev \ 
        libtiff-dev \ 
        libjasper-dev \ 
        python-numpy \ 
        python-pycurl \ 
        python-opencv


    RUN pip install opencv-python
    RUN pip install tensorflow
    RUN pip install --upgrade tensorflow

    COPY . .

    RUN useradd -ms /bin/bash moduleuser
    USER moduleuser

    CMD [ "python", "-u", "./main.py" ]

    ```

6.  Fare clic con il pulsante destro del mouse sulla cartella sotto i moduli **(con** il nome specificato in precedenza; nell'esempio più in basso si chiama *pythonmodule)* e fare clic su **Nuova cartella.** Assegnare alla cartella il **nome images**.

7.  All'interno della cartella aggiungere alcune immagini contenenti mouse o tastiera. Queste saranno le immagini che verranno analizzate dal modello Tensorflow.

    > [!WARNING]
    > Se si usa un modello personalizzato, sarà necessario modificarlo in modo da riflettere i propri dati dei modelli.

8.  Sarà ora necessario recuperare i **filelabels.txt** e **model.pb** dalla cartella del modello, scaricata in precedenza (o creata dal servizio **Visione personalizzata),** nel capitolo [1.](#chapter-1---retrieve-the-custom-vision-model) Dopo aver creato i file, posizionarli all'interno della soluzione, insieme agli altri file. Il risultato finale dovrebbe essere simile all'immagine seguente:

    ![Creare il contenitore](images/AzureLabs-Lab313-29.png)

## <a name="chapter-9---package-the-solution-as-a-container"></a>Capitolo 9: Creare un pacchetto della soluzione come contenitore

1.  A questo punto è possibile "creare un pacchetto" dei file come contenitore ed eseguire il push nel **Registro Azure Container**. In VS Code aprire il *terminale* integrato **(Visualizza** terminale integrato o CTRL) e usare la riga seguente per accedere a  >    + **\`** **Docker** (sostituire i valori del comando con le credenziali del Registro Azure Container ):

    ```bash
        docker login -u <ACR username> -p <ACR password> <ACR login server>
    ```

2. Fare clic con il pulsante destro del **mousedeployment.template.jsfile in** e scegliere Compila IoT Edge **soluzione**. Questo processo di compilazione richiede molto tempo (a seconda del dispositivo), quindi è necessario prepararsi ad attendere. Al termine del processo di compilazione, **verrà creatodeployment.jsfile** all'interno di una nuova cartella denominata **config**.

    ![creare la distribuzione](images/AzureLabs-Lab313-30.png)

3. Aprire di **nuovo il riquadro** comandi e cercare **Azure: Accedi.** Seguire le istruzioni usando le credenziali dell'account Azure. VS Code con l'opzione Copia e *apri,* che copierà il codice del dispositivo che sarà necessario a breve e aprirà il Web browser predefinito. Quando richiesto, incollare il codice del dispositivo per autenticare il computer.

    ![copiare e aprire](images/AzureLabs-Lab313-31.png)

4. Dopo l'accesso, nella parte inferiore  del pannello Esplora si noterà una nuova sezione denominata **Azure IoT Hub.** Fare clic su questa sezione per espanderla.

    ![dispositivo perimetrale](images/AzureLabs-Lab313-32.png)

5. Se il dispositivo non è disponibile, è necessario fare clic con il pulsante destro del mouse su Dispositivi *hub* Azure IoT e quindi scegliere Imposta stringa di **connessione hub IoT.** Si noti quindi che il **riquadro** comandi (nella parte superiore di VS Code), richiederà di immettere la stringa *di connessione*. Si tratta della *stringa di* connessione di cui si è stati notati alla fine del [capitolo 3.](#chapter-3---the-iot-hub-service) Premere **INVIO** dopo aver copiato la stringa.    

6. Il dispositivo dovrebbe essere caricato e visualizzato. Fare clic con il pulsante destro del mouse sul nome del dispositivo e quindi scegliere **Crea distribuzione per dispositivo singolo.**

    ![creare la distribuzione](images/AzureLabs-Lab313-33b.png)

7. Verrà visualizzato un *prompt Esplora file,* in cui è possibile passare alla cartella **config** e quindi selezionare ildeployment.js **nel** file. Con il file selezionato, fare clic sul **pulsante Select Edge Deployment Manifest (Seleziona manifesto distribuzione Edge).**

    ![creare la distribuzione](images/AzureLabs-Lab313-34.png)

8. A questo punto è stato fornito al servizio hub **IoT** il manifesto per distribuire il contenitore, come modulo, dal **Registro Azure Container ,** distribuerlo in modo efficace nel dispositivo.

9. Per visualizzare i messaggi inviati dal dispositivo all'hub IoT, fare di nuovo clic con il pulsante destro del mouse sul nome del dispositivo nella sezione Azure IoT Hub Devices (Dispositivi hub **di Azure IoT)** nel pannello **Explorer** e fare clic su Start Monitoring D2C Message (Avvia monitoraggio **messaggio D2C).** I messaggi inviati dal dispositivo verranno visualizzati nel terminale di Visual Studio. Sii paziente, poiché questa operazione potrebbe richiedere del tempo. Vedere il capitolo successivo per il debug e verificare se la distribuzione è riuscita.

Questo modulo ora scorrerà le immagini nella cartella **images** e le analerà, con ogni iterazione. Questa è ovviamente solo una dimostrazione di come usare il modello di Machine Learning di base in un ambiente IoT Edge dispositivo. 

Per espandere la funzionalità di questo esempio, è possibile procedere in diversi modi. Un modo potrebbe essere includere codice nel contenitore, che acquisisce le foto da una webcam connessa al dispositivo e salva le immagini nella cartella images. 

Un altro modo potrebbe essere la copia delle immagini dal dispositivo IoT nel contenitore. Un modo pratico per eseguire questa operazione è eseguire il comando seguente nel terminale del dispositivo IoT(ad esempio, una piccola app potrebbe eseguire il processo, se si vuole automatizzare il processo). È possibile testare questo comando eseguendolo manualmente dal percorso della cartella in cui sono archiviati i file:

```bash
    sudo docker cp <filename> <modulename>:/app/images/<a name of your choice>
```

## <a name="chapter-10---debugging-the-iot-edge-runtime"></a>Capitolo 10 - Debug del runtime IoT Edge runtime

Di seguito è riportato un elenco di righe di comando e suggerimenti che consentono di monitorare ed eseguire il debug dell'attività di messaggistica di *IoT Edge Runtime* dal dispositivo **Ubuntu.** 

- Controllare lo *stato IoT Edge runtime* eseguendo la riga di comando seguente:

    ```bash
        sudo systemctl status iotedge
    ```

    > [!NOTE]
    > Ricordarsi di premere **CTRL+C** per completare la visualizzazione dello stato.

- Elencare i contenitori attualmente distribuiti. Se il *servizio hub IoT* ha distribuito correttamente i contenitori, verranno visualizzati eseguendo la riga di comando seguente:

    ```bash
        sudo iotedge list
    ```

    Oppure

    ```bash
        sudo docker ps
    ```

    > [!NOTE]
    > Il codice precedente è un buon metodo per verificare se il modulo è stato distribuito correttamente, perché verrà visualizzato nell'elenco. In caso **contrario, verranno** visualizzati solo *edgeHub* *e edgeAgent.*

- Per visualizzare i log del codice di un contenitore, eseguire la riga di comando seguente:

    ```bash
        journalctl -u iotedge
    ```

**Comandi utili per gestire il IoT Edge runtime:**

-  Per eliminare tutti i contenitori nell'host:

    ```bash
        sudo docker rm -f $(sudo docker ps -aq)
    ```

-  Per arrestare il *IoT Edge runtime* di :

    ```bash
        sudo systemctl stop iotedge
    ```

## <a name="chapter-11---create-table-service"></a>Capitolo 11 - Creare un servizio tabelle 

Tornare al portale di Azure, in cui si creerà un servizio tabelle di Azure, creando una risorsa Archiviazione servizio.

1. Se non è già stato eseguito l'accesso, accedere al [portale di Azure.](https://portal.azure.com)

2. Dopo aver eseguito l'accesso, fare clic su Crea una risorsa , nell'angolo  in alto a sinistra, cercare **l'account Archiviazione** e premere INVIO per avviare la ricerca.

3. Una volta visualizzato, fare clic su **Archiviazione account: BLOB, file, tabelle, code** dall'elenco.

    ![cercare l'account di archiviazione](images/AzureLabs-Lab313-35.png)

4. La nuova pagina fornirà una descrizione del servizio **dell Archiviazione account** utente. Nella parte inferiore sinistra del prompt fare clic sul **pulsante Crea** per creare un'istanza del servizio.

    ![creare un'istanza di archiviazione](images/AzureLabs-Lab313-36.png)

5. Dopo aver fatto clic su **Crea,** verrà visualizzato un pannello:

    1. Inserire il nome **desiderato per** questa istanza del servizio ( deve essere *tutto minuscolo).*

    2. Per **Modello di distribuzione** fare clic su Gestione **risorse**.

    3. Per **Tipo di account**, nel menu a discesa fare clic su Archiviazione **(utilizzo generico v1).**

    4. Fare clic su un **percorso appropriato.**
    
    5. Per il menu **a** discesa Replica fare clic su Archiviazione con ridondanza geografica e accesso in **lettura (RA-GRS).**

    6. Per **Prestazioni** fare clic su **Standard.**

    7. Nella sezione **Trasferimento sicuro obbligatorio** fare clic su **Disabilitato.**

    8. Nel menu **a discesa Sottoscrizione** fare clic su una sottoscrizione appropriata.

    9. Scegliere un **gruppo di risorse** o crearne uno nuovo. Un gruppo di risorse consente di monitorare, controllare l'accesso, effettuare il provisioning e gestire la fatturazione per una raccolta di asset di Azure. È consigliabile mantenere tutti i servizi di Azure associati a un singolo progetto (ad esempio, questi corsi) in un gruppo di risorse comune.

        > Per altre informazioni sui gruppi di risorse di Azure, fare clic su questo collegamento per [gestire un gruppo di risorse.](/azure/azure-resource-manager/resource-group-portal)

    10. Lasciare **Reti virtuali** su **Disabilitato,** se questa è un'opzione per l'utente.

    11. Fare clic su **Crea**.

        ![Compilare i dettagli di archiviazione](images/AzureLabs-Lab313-37.png)

6. Dopo aver fatto clic su **Crea**, sarà necessario attendere la creazione del servizio. L'operazione potrebbe richiedere un minuto.

7. Una volta creata l'istanza del servizio, nel portale verrà visualizzata una notifica. Fare clic sulle notifiche per esplorare la nuova istanza del servizio.

    ![notifica della nuova archiviazione](images/AzureLabs-Lab313-38.png)

8. Fare clic **sul pulsante Vai** alla risorsa nella notifica per passare alla pagina di panoramica della nuova istanza Archiviazione Service.

    ![Vai alla risorsa](images/AzureLabs-Lab313-39.png)

9. Nella pagina di panoramica fare clic su Tabelle sul lato **destro.**
    
    ![tabelle](images/AzureLabs-Lab313-40.png)

10. Il pannello a destra verrà modificato per visualizzare le **informazioni del** servizio tabelle, in cui è necessario aggiungere una nuova tabella. A tale scopo, fare **clic sul pulsante +** Tabella nell'angolo superiore sinistro.

    ![aprire tabelle](images/AzureLabs-Lab313-41.png)

11. Verrà visualizzata una nuova pagina, in cui è necessario immettere un nome **di tabella**. Si tratta del nome che verrà utilizzato per fare riferimento ai dati nell'applicazione nei capitoli successivi (creazione di app per le funzioni e Power BI). Inserire **IoTMessages** come nome (è possibile sceglierne uno personalizzato, ricordarlo quando verrà usato più avanti in questo documento) e fare clic su **OK.** 

12. Dopo aver creato la nuova tabella, sarà possibile visualizzare la tabella nella pagina **Servizio** tabelle (nella parte inferiore).

    ![nuova tabella creata](images/AzureLabs-Lab313-42.png)  

13. A questo  punto fare clic su Chiavi di accesso e prendere una copia del nome **dell'account Archiviazione** e della chiave **(usando** il Blocco note). Questi valori verranno utilizzati più avanti in questo corso, durante la creazione dell'app per le funzioni di **Azure.**

    ![nuova tabella creata](images/AzureLabs-Lab313-43.png) 

14. Usando di nuovo il pannello a sinistra, scorrere fino alla sezione *Table Service* (Servizio tabelle) e fare clic su **Tables** (Tabelle) (o **Browse Tables**(Sfoglia tabelle) nei portali più nuovi) ed eseguire una copia dell'URL della tabella (usando il Blocco note).  Questo valore verrà utilizzato più avanti in questo corso, quando si collega la tabella **all'applicazione Power BI** dati.

    ![nuova tabella creata](images/AzureLabs-Lab313-44.png)

## <a name="chapter-12---completing-the-azure-table"></a>Capitolo 12 - Completamento della tabella di Azure

Dopo la **configurazione dell'account** di archiviazione del servizio tabelle, è possibile aggiungevi dati, che verranno usati per archiviare e recuperare informazioni. La modifica delle tabelle può essere eseguita tramite **Visual Studio**.

1. Aprire **Visual Studio** **(non Visual Studio Code).**

2. Scegliere Visualizza dal menu  >  **Cloud Explorer**.

    ![aprire Cloud Explorer](images/AzureLabs-Lab313-45.png)

3. Il **Cloud Explorer** verrà aperto come elemento ancorato (sii paziente, poiché il caricamento può richiedere tempo).

    > [!WARNING] 
    > Se la sottoscrizione usata per creare gli account *Archiviazione non* è visibile, assicurarsi di disporre di: 
    > - Accedere allo stesso account usato per il portale di Azure.
    > - Selezionare la sottoscrizione nella pagina Gestione account (potrebbe essere necessario applicare un filtro dalle impostazioni dell'account):  
    >
    >   ![trovare la sottoscrizione](images/AzureLabs-Lab313-46.png)

4. Verranno visualizzati i servizi cloud di Azure. Trovare **Archiviazione account e** fare clic sulla freccia a sinistra per espandere gli account.

    ![aprire gli account di archiviazione](images/AzureLabs-Lab313-47.png)

5. Dopo l'espansione, **l'account Archiviazione dovrebbe** essere disponibile. Fare clic sulla freccia a sinistra dello spazio di  archiviazione e quindi, una volta espansa, trovare Tabelle e fare clic sulla freccia accanto a tale tabella per visualizzare la tabella creata nell'ultimo capitolo.  Fare doppio clic sulla **tabella**.

6. La tabella verrà aperta al centro della finestra Visual Studio finestra. Fare clic sull'icona della tabella **+** con il segno più.

    ![aggiungere una nuova tabella](images/AzureLabs-Lab313-48.png)

7. Verrà visualizzata una finestra in cui viene richiesto di aggiungere *l'entità*. Si creerà una sola entità, anche se avrà tre proprietà. Si noterà che *PartitionKey* e *RowKey* sono già disponibili, in quanto vengono usati dalla tabella per trovare i dati. 

    ![partizione e chiave di riga](images/AzureLabs-Lab313-49.png)

8. Aggiornare i valori seguenti:

    - Nome: **PartitionKey**, Valore: **PK_IoTMessages** 

    - Nome: **RowKey**, Valore: **RK_1_IoTMessages** 

9. Fare quindi clic **su Aggiungi proprietà** (in basso a sinistra nella finestra *Aggiungi* entità) e aggiungere la proprietà seguente:

    - **MessageContent,** come *stringa,* lascia vuoto Il valore.

10. La tabella deve corrispondere a quella nell'immagine seguente:

    ![aggiungere i valori corretti](images/AzureLabs-Lab313-50.png)

    > [!NOTE] 
    > Il motivo per cui l'entità ha il numero 1 nella chiave di riga è perché potrebbe essere necessario aggiungere altri messaggi, se si vuole sperimentare ulteriormente con questo corso.

11. Al termine, fare clic su **OK.** La tabella è ora pronta per l'uso.

## <a name="chapter-13---create-an-azure-function-app"></a>Capitolo 13 - Creare un'app per le funzioni di Azure 

È ora possibile creare un'app per le funzioni di *Azure* che verrà chiamata dal servizio  *hub IoT* per archiviare i messaggi del dispositivo *IoT Edge* nel servizio tabelle creato nel capitolo precedente.

Prima di tutto, è necessario creare un file che consenta alla funzione di Azure di caricare le librerie necessarie.

1.  Aprire **Blocco note** (premere la Windows *chiave* e *digitare* notepad ).

    ![aprire blocco note](images/AzureLabs-Lab313-51.png)

2.  Con Blocco note aperta, inserire al suo interno la struttura JSON seguente. Dopo aver eseguito questa operazione, salvarlo sul desktop come **project.jsin**. Questo file definisce le librerie che verranno usate dalla funzione. Se è stato usato NuGet, avrà un aspetto familiare.
    
    > [!WARNING]
    > È importante che la denominazione sia corretta. assicurarsi che **NON abbia un'.txt** file. Per informazioni di riferimento, vedere di seguito:
    >
    > ![Salvataggio JSON](images/AzureLabs-Lab313-52.png)

    ```json
    {
    "frameworks": {
        "net46":{
        "dependencies": {
            "WindowsAzure.Storage": "9.2.0"
        }
        }
    }
    }
    ```

3.  Accedere al portale [di Azure.](https://portal.azure.com)

4.  Dopo aver eseguito l'accesso, fare clic su Crea una risorsa nell'angolo  superiore sinistro e cercare **App** per le funzioni e premere INVIO per eseguire la ricerca.  Fare *clic su App* per le funzioni nei risultati per aprire un nuovo pannello.

    ![cercare l'app per le funzioni](images/AzureLabs-Lab313-53.png)

5.  Il nuovo pannello fornirà una descrizione del **servizio app per le** funzioni. Nella parte inferiore sinistra di questo pannello fare clic sul **pulsante Crea** per creare un'associazione con questo servizio.

    ![Istanza dell'app per le funzioni](images/AzureLabs-Lab313-54.png)

6.  Dopo aver fatto clic su **Crea,** compilare quanto segue:

    1. Per **Nome app** inserire il nome desiderato per questa istanza del servizio.

    2. Selezionare una **Sottoscrizione**.

    3. Selezionare il piano tariffario appropriato, se questa è la prima volta che si crea un servizio **app** per le funzioni, sarà disponibile un piano gratuito.

    4. Scegliere un **gruppo di risorse** o crearne uno nuovo. Un gruppo di risorse consente di monitorare, controllare l'accesso, effettuare il provisioning e gestire la fatturazione per una raccolta di asset di Azure. È consigliabile mantenere tutti i servizi di Azure associati a un singolo progetto,ad esempio questi corsi, in un gruppo di risorse comune.

        > Per altre informazioni sui gruppi di risorse di Azure, seguire questo collegamento su [come gestire un gruppo di risorse.](/azure/azure-resource-manager/resource-group-portal)

    5. Per **Sistema operativo**, fare clic Windows, in quanto si tratta della piattaforma prevista.

    6. Selezionare un **piano di hosting** (questa esercitazione usa un piano a **consumo**).

    7. Selezionare un **percorso** (scegliere la stessa posizione dell'archiviazione creata nel passaggio precedente)

    8. Per la **Archiviazione,** è necessario selezionare il servizio Archiviazione **creato nel passaggio precedente.**

    9. L'applicazione *non* sarà Insights in questa app, quindi è possibile lasciarla **disattivata.**

    10. Fare clic su **Crea**.

        ![creare una nuova istanza](images/AzureLabs-Lab313-55.png)

7.  Dopo aver fatto clic su **Crea**, sarà necessario attendere la creazione del servizio, l'operazione potrebbe richiedere un minuto.

8.  Una volta creata l'istanza del servizio, nel portale verrà visualizzata una notifica.

    ![nuova notifica](images/AzureLabs-Lab313-56.png)

9.  Fare clic sulla notifica al termine della distribuzione.

10. Fare clic **sul pulsante Vai alla** risorsa nella notifica per esplorare la nuova istanza del servizio. 

    ![passare alla risorsa](images/AzureLabs-Lab313-57.png)

11. Sul lato sinistro del nuovo pannello fare clic sull'icona **+** (più) accanto a *Funzioni* per creare una nuova funzione.

    ![aggiungere una nuova funzione](images/AzureLabs-Lab313-58.png)

12. Nel pannello centrale verrà visualizzata **la finestra Creazione** funzione. Scorrere ulteriormente verso il basso e fare clic su **Funzione personalizzata**.

    ![funzione personalizzata](images/AzureLabs-Lab313-59.png)

13. Scorrere verso il basso nella pagina successiva fino a trovare **Hub IoT (Hub eventi)** e quindi fare clic su di esso.

    ![funzione personalizzata](images/AzureLabs-Lab313-60.png)

14. Nel pannello **Hub IoT (Hub eventi)** impostare **Linguaggio** su **C#** e quindi fare clic su **nuovo**.

    ![funzione personalizzata](images/AzureLabs-Lab313-61.png)

15. Nella finestra visualizzata verificare che l'hub **IoT** sia selezionato e che il nome del campo *Hub IoT* corrisponda al nome del servizio hub *IoT* creato in precedenza ( nel passaggio 8 del capitolo [3).](#chapter-3---the-iot-hub-service) Fare quindi clic **sul pulsante** Seleziona.

    ![funzione personalizzata](images/AzureLabs-Lab313-62.png)

16. Nel pannello **Hub IoT (Hub eventi)** fare clic su **Crea**.

    ![funzione personalizzata](images/AzureLabs-Lab313-63.png)

17. Si verrà reindirizzati all'editor di funzioni.

    ![funzione personalizzata](images/AzureLabs-Lab313-64.png)

18. Eliminare tutto il codice in esso in esso e sostituirlo con il codice seguente:

    ```csharp
    #r "Microsoft.WindowsAzure.Storage"
    #r "NewtonSoft.Json"

    using System;
    using Microsoft.WindowsAzure.Storage;
    using Microsoft.WindowsAzure.Storage.Table;
    using Newtonsoft.Json;
    using System.Threading.Tasks;

    public static async Task Run(string myIoTHubMessage, TraceWriter log)
    {
        log.Info($"C# IoT Hub trigger function processed a message: {myIoTHubMessage}");
        
        //RowKey of the table object to be changed
        string tableName = "IoTMessages";
        string tableURL = "https://iothubmrstorage.table.core.windows.net/IoTMessages";

        // If you did not name your Storage Service as suggested in the course, change the name here with the one you chose.
        string storageAccountName = "iotedgestor"; 

        string storageAccountKey = "<Insert your Storage Key here>";   

        string partitionKey = "PK_IoTMessages";
        string rowKey = "RK_1_IoTMessages";

        Microsoft.WindowsAzure.Storage.Auth.StorageCredentials storageCredentials =
            new Microsoft.WindowsAzure.Storage.Auth.StorageCredentials(storageAccountName, storageAccountKey);

        CloudStorageAccount storageAccount = new CloudStorageAccount(storageCredentials, true);

        // Create the table client.
        CloudTableClient tableClient = storageAccount.CreateCloudTableClient();

        // Get a reference to a table named "IoTMessages"
        CloudTable messageTable = tableClient.GetTableReference(tableName);

        //Retrieve the table object by its RowKey
        TableOperation operation = TableOperation.Retrieve<MessageEntity>(partitionKey, rowKey);
        TableResult result = await messageTable.ExecuteAsync(operation);

        //Create a MessageEntity so to set its parameters
        MessageEntity messageEntity = (MessageEntity)result.Result;

        messageEntity.MessageContent = myIoTHubMessage;
        messageEntity.PartitionKey = partitionKey;
        messageEntity.RowKey = rowKey;

        //Replace the table appropriate table Entity with the value of the MessageEntity Ccass structure.
        operation = TableOperation.Replace(messageEntity);

        // Execute the insert operation.
        await messageTable.ExecuteAsync(operation);
    }

    // This MessageEntity structure which will represent a Table Entity
    public class MessageEntity : TableEntity
    {
        public string Type { get; set; }
        public string MessageContent { get; set; }   
    }
    ```

19. Modificare le variabili seguenti, in modo che corrispondano ai valori appropriati ( valori **table** e **Archiviazione,** rispettivamente dai passaggi [11 e 13 del capitolo 11](#chapter-11---create-table-service)), che si trovano nell'account **Archiviazione**:

    - **tableName**, con il nome della **tabella** che si trova nell'Archiviazione **account**.
    - **tableURL** con l'URL della **tabella** che si trova nell'Archiviazione **account**.
    - **storageAccountName**, con il nome del valore corrispondente al nome **dell'Archiviazione Account.**
    - **storageAccountKey** con la chiave ottenuta nel servizio Archiviazione creato in precedenza.

    ![funzione personalizzata](images/AzureLabs-Lab313-65.png)

20. Dopo il codice, fare clic su **Salva**.

21. Fare quindi clic **\<** sull'icona (freccia) sul lato destro della pagina.

    ![funzione personalizzata](images/AzureLabs-Lab313-66.png)

22. Un pannello scorrerà da destra. In tale pannello fare clic su **Upload** e verrà visualizzato un *Browser* di file.

23. Individuare e fare clic sulproject.js **sul** file creato **in** precedenza Blocco note e quindi fare clic sul **pulsante** Apri. Questo file definisce le librerie che verranno usate dalla funzione.

    ![funzione personalizzata](images/AzureLabs-Lab313-67.png)

24. Dopo il caricamento, il file verrà visualizzato nel pannello a destra. Facendo clic su di esso verrà aperto all'interno **dell'editor di** funzioni. Deve avere **esattamente lo** stesso aspetto dell'immagine successiva.

    ![funzione personalizzata](images/AzureLabs-Lab313-68.png)

25. A questo punto sarebbe bene testare la funzionalità della funzione per archiviare il messaggio nella *tabella*. Nella parte superiore destra della finestra fare clic su **Test**.

    ![funzione personalizzata](images/AzureLabs-Lab313-69.png)

26. Inserire un messaggio nel corpo **della** richiesta , come illustrato nell'immagine precedente, e fare clic su **Esegui**. 

27. La funzione verrà eseguita, visualizzando lo stato del risultato (si noterà lo stato **verde 202 Accettato,** sopra la finestra *Output,* che indica che si è trattata di una chiamata riuscita):

    ![risultato dell'output](images/AzureLabs-Lab313-70.png)

## <a name="chapter-14---view-active-messages"></a>Capitolo 14 - Visualizzare i messaggi attivi

Se ora si apre Visual Studio **(non** Visual Studio Code), è possibile visualizzare il risultato del messaggio di test, perché verrà archiviato nell'area della stringa *MessageContent.*

![funzione personalizzata](images/AzureLabs-Lab313-71.png)

Con il servizio tabelle e l'app per le funzioni, i messaggi del dispositivo Ubuntu verranno visualizzati nella tabella *IoTMessages.* Se non è già in esecuzione, avviare di nuovo il dispositivo e sarà possibile visualizzare i messaggi di risultato dal dispositivo e dal modulo, all'interno della tabella, usando Visual Studio *Cloud Explorer*.

![visualizzare i dati](images/AzureLabs-Lab313-72.png)


## <a name="chapter-15---power-bi-setup"></a>Capitolo 15 - Power BI configurazione

Per visualizzare i dati dal dispositivo IOT, verrà Power BI **(versione** desktop) per raccogliere i dati dal *servizio* tabelle appena creato. La *HoloLens* di Power BI userà quindi i dati per visualizzare il risultato.

1.  Aprire il Microsoft Store in Windows 10 e cercare **Power BI Desktop**.

    ![Power BI](images/AzureLabs-Lab313-73.png)

2.  Scaricare l'applicazione. Al termine del download, aprirlo.

3.  Accedere a *Power BI* con il proprio **account Microsoft 365 .** È possibile che si venga reindirizzati a un browser per l'iscrizione. Dopo aver effettuato l'iscrizione, tornare all'app Power BI ed eseguire di nuovo l'accesso.

4.  Fare clic **su Ottieni dati** e quindi su **Altro...**.

    ![Power BI](images/AzureLabs-Lab313-74.png)

5.  Fare **clic su Azure,** **Tabella Archiviazione** Azure e quindi fare clic su **Connessione**.

    ![Power BI](images/AzureLabs-Lab313-75.png)

6.  Verrà richiesto di inserire **l'URL** della tabella raccolto in precedenza ( nel passaggio 13 del capitolo [11](#chapter-11---create-table-service)) durante la creazione del servizio tabelle. Dopo aver inserito l'URL, eliminare la parte del percorso che fa riferimento alla "sottocartella" della tabella (che in questo corso era IoTMessages). Il risultato finale dovrebbe essere come illustrato nell'immagine seguente. Fare quindi clic su **OK.**

    ![Power BI](images/AzureLabs-Lab313-76.png)

7.  Verrà richiesto di inserire la chiave **Archiviazione** specificata ( nel passaggio 11 del capitolo [11](#chapter-11---create-table-service)) in precedenza durante la creazione della tabella Archiviazione. Fare quindi clic **su Connessione**.

    ![Power BI](images/AzureLabs-Lab313-77.png)  

8. Verrà **visualizzato un pannello** strumento di navigazione, selezionare la casella accanto alla tabella e fare clic su **Carica.**

    ![Power BI](images/AzureLabs-Lab313-78.png)  

9. La tabella è stata caricata in Power BI, ma è necessaria una query per visualizzare i valori in essa. A tale scopo, fare clic con il pulsante destro del mouse sul nome della tabella che si trova nel pannello **CAMPI** sul lato destro della schermata. Fare quindi clic su **Modifica query.**

    ![Power BI](images/AzureLabs-Lab313-79.png) 

10. Verrà **editor di Power Query**  una nuova finestra che visualizza la tabella. Fare clic sulla parola **Record** *all'interno della colonna Contenuto* della tabella per visualizzare il contenuto archiviato.

    ![Power BI](images/AzureLabs-Lab313-80.png)    

11. Fare clic **su Into Table (Into Table)** in alto a sinistra nella finestra. 

    ![Power BI](images/AzureLabs-Lab313-81.png)

12. Fare clic **su Chiudi & Applica.**

    ![Power BI](images/AzureLabs-Lab313-82.png)

13. Al termine del caricamento della query, nel pannello **CAMPI,** sul lato destro della schermata, selezionare le caselle corrispondenti ai parametri **Name** e **Value** per visualizzare il contenuto della colonna **MessageContent.**

    ![Power BI](images/AzureLabs-Lab313-83.png)

14. Fare clic **sull'icona del disco** blu nella parte superiore sinistra della finestra per salvare il lavoro in una cartella di propria scelta.

    ![Power BI](images/AzureLabs-Lab313-84.png)

15. È ora possibile fare clic sul pulsante Pubblica per caricare la tabella nell'area di lavoro. Quando richiesto, fare clic su **Area di lavoro personale** e quindi su *Seleziona.* Attendere che il risultato dell'invio sia visualizzato correttamente.

    ![Power BI](images/AzureLabs-Lab313-85.png)

    ![Power BI](images/AzureLabs-Lab313-86.png)

> [!WARNING]
> Il capitolo seguente è HoloLens specifico. Power BI non è attualmente disponibile come applicazione immersiva, ma è possibile eseguire la versione desktop nel portale di Windows Mixed Reality (noto anche come Casa sulla scogliera), tramite l'app desktop.

## <a name="chapter-16---display-power-bi-data-on-hololens"></a>Capitolo 16: Visualizzare Power BI dati in HoloLens

1. Nel HoloLens accedere al Microsoft Store **,** toccando la relativa icona nell'elenco delle applicazioni.

    ![Power BI Hl](images/AzureLabs-Lab313-87.png)

2. Cercare e quindi scaricare **l'Power BI** applicazione.

    ![Power BI Hl](images/AzureLabs-Lab313-88.png)

3. Avviare **Power BI** dall'elenco delle applicazioni. 

4. **Power BI** potrebbe essere necessario accedere **all'account Microsoft 365.**

5. Una volta all'interno dell'app, l'area di lavoro dovrebbe essere visualizzata per impostazione predefinita, come illustrato nell'immagine seguente. In caso contrario, è sufficiente fare clic sull'icona dell'area di lavoro sul lato sinistro della finestra.

    ![Power BI Hl](images/AzureLabs-Lab313-89.png)

## <a name="your-finished-your-iot-hub-application"></a>L'applicazione dell'hub IoT è stata completata

La creazione di un servizio hub IoT con un dispositivo Virtual Machine Edge simulato è stata completata. Il dispositivo può comunicare i risultati di un modello di Machine Learning a un servizio tabelle di Azure, agevolato da un'app per le funzioni di Azure, che viene letta in Power BI e visualizzabile all'interno di un Microsoft HoloLens.
 
![Power BI](images/AzureLabs-Lab313-00.png)

## <a name="bonus-exercises"></a>Esercizi aggiuntivi

### <a name="exercise-1"></a>Esercizio 1

Espandere la struttura di messaggistica archiviata nella tabella e visualizzarla come grafico. Potrebbe essere necessario raccogliere più dati e archiviare i dati nella stessa tabella, per visualizzarli in un secondo momento.

### <a name="exercise-2"></a>Esercizio 2

Creare un modulo di acquisizione della fotocamera aggiuntivo da distribuire nella scheda IoT, in modo che possa acquisire immagini attraverso la fotocamera da analizzare.

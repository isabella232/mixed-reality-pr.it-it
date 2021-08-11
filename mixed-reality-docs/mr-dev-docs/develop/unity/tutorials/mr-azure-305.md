---
title: HoloLens (prima generazione) e Azure 305 - Funzioni e archiviazione
description: Completare questo corso per informazioni su come implementare Archiviazione di Azure e funzioni all'interno di un'applicazione di realtà mista.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure, mixed reality, academy, unity, tutorial, api, functions, storage, hololens, immersive, vr, Windows 10, Visual Studio
ms.openlocfilehash: 337b1d3fb23450325805237a6ba975861260760b7d37028b8d717bad99b9d233
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115193946"
---
# <a name="hololens-1st-gen-and-azure-305-functions-and-storage"></a>HoloLens (prima generazione) e Azure 305: Funzioni e archiviazione

<br>

>[!NOTE]
>Le esercitazioni di Mixed Reality Academy sono state progettate in base a HoloLens (prima generazione) e ai visori VR immersive di realtà mista.  Pertanto, riteniamo importante lasciarle a disposizione degli sviluppatori a cui serve ancora materiale sussidiario per lo sviluppo di questi dispositivi.  Queste esercitazioni **_non_** verranno aggiornate con i set di strumenti o le interazioni più recenti usati per HoloLens 2.  Rimarranno invariate per consentire di continuare a lavorare sui dispositivi supportati. In futuro verrà pubblicata una nuova serie di esercitazioni che illustrano come sviluppare per HoloLens 2.  Questa informativa verrà aggiornata con un collegamento a tali esercitazioni al momento della pubblicazione.

<br> 

![final product -start](images/AzureLabs-Lab5-00.png)

In questo corso si apprenderà come creare e usare Funzioni di Azure e archiviare i dati con una risorsa Archiviazione di Azure, all'interno di un'applicazione di realtà mista.

*Funzioni di Azure* è un servizio Microsoft che consente agli sviluppatori di eseguire piccole parti di codice, "funzioni", in Azure. Ciò consente di delegare il lavoro al cloud, anziché all'applicazione locale, che può avere molti vantaggi. *Funzioni di Azure* supporta diversi linguaggi di sviluppo, tra cui C \# , F , \# Node.js, Java e PHP. Per altre informazioni, vedere [l'articolo Funzioni di Azure .](/azure/azure-functions/functions-overview)

*Archiviazione di Azure* è un servizio cloud Microsoft, che consente agli sviluppatori di archiviare i dati, con l'assicurazione che sarà a disponibilità elevata, sicura, durevole, scalabile e ridondante. Ciò significa che Microsoft gestirà tutti i problemi di manutenzione e critici per l'utente. Per altre informazioni, vedere [l'articolo Archiviazione di Azure .](/azure/storage/common/storage-introduction)

Dopo aver completato questo corso, si avrà un'applicazione visore vr immersiva di realtà mista che sarà in grado di eseguire le operazioni seguenti:

1.  Consente all'utente di osservare una scena.
2.  Attiva la generazione di oggetti quando l'utente guarda un "pulsante" 3D.
3.  Gli oggetti generati verranno scelti da una funzione di Azure.
4.  Quando ogni oggetto viene generato, l'applicazione archivierà il tipo di oggetto in un file di *Azure,* che si trova in *Archiviazione di Azure*.
5.  Al secondo caricamento, i dati di File di *Azure* verranno recuperati e usati per riprodurre le azioni di generazione dall'istanza precedente dell'applicazione.

Nell'applicazione è necessario sapere come integrare i risultati con la progettazione. Questo corso è progettato per illustrare come integrare un servizio di Azure con il servizio Unity Project. È compito dell'utente usare le conoscenze acquisite da questo corso per migliorare l'applicazione di realtà mista.

## <a name="device-support"></a>Supporto di dispositivi

<table>
<tr>
<th>Corso</th><th style="width:150px"> <a href="/hololens/hololens1-hardware">HoloLens</a></th><th style="width:150px"> <a href="../../../discover/immersive-headset-hardware-details.md">Visori VR immersive</a></th>
</tr><tr>
<td>MR e Azure 305: Funzioni e archiviazione</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> Anche se questo corso è in Windows Mixed Reality visore vr immersive, è anche possibile applicare ciò che si apprende in questo corso per Microsoft HoloLens. Man mano che si segue il corso, verranno visualizzati note su eventuali modifiche che potrebbero essere necessarie per supportare HoloLens.

## <a name="prerequisites"></a>Prerequisiti

> [!NOTE]
> Questa esercitazione è progettata per sviluppatori con esperienza di base con Unity e C#. Tenere inoltre presente che i prerequisiti e le istruzioni scritte in questo documento rappresentano ciò che è stato testato e verificato al momento della scrittura (maggio 2018). È possibile usare il software più recente, come elencato nell'articolo installare gli strumenti, anche se non è consigliabile presumere che le informazioni in questo corso corrispondano perfettamente a quelle disponibili nel software più recente rispetto a quelle elencate di seguito. [](../../install-the-tools.md)

Per questo corso è consigliabile usare l'hardware e il software seguenti:

- Un PC di sviluppo, [compatibile con Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) per lo sviluppo di visori vr immersive
- [Windows 10 Fall Creators Update (o versione successiva) con la modalità sviluppatore abilitata](../../install-the-tools.md#installation-checklist)
- [L'SDK Windows 10 più recente](../../install-the-tools.md#installation-checklist)
- [Unity 2017.4](../../install-the-tools.md#installation-checklist)
- [Visual Studio 2017](../../install-the-tools.md#installation-checklist)
- Visore [Windows Mixed Reality vr o](../../../discover/immersive-headset-hardware-details.md) visore [Microsoft HoloLens](/hololens/hololens1-hardware) con la modalità sviluppatore abilitata
- Sottoscrizione a un account Azure per la creazione di risorse di Azure
- Accesso a Internet per l'installazione e il recupero dei dati di Azure

## <a name="before-you-start"></a>Prima di iniziare

Per evitare problemi durante la compilazione di questo progetto, è consigliabile creare il progetto indicato in questa esercitazione in una cartella radice o quasi radice (i percorsi di cartelle lunghe possono causare problemi in fase di compilazione).

## <a name="chapter-1---the-azure-portal"></a>Capitolo 1 - Portale di Azure

Per usare il **Archiviazione di Azure ,** è necessario creare e configurare un **account** Archiviazione nel portale di Azure.

1.  Accedere al portale [di Azure.](https://portal.azure.com)

    > [!NOTE]
    > Se non si dispone già di un account Azure, è necessario crearne uno. Se si sta seguendo questa esercitazione in una situazione di classe o di lab, chiedere all'insegnante o a uno dei prottori di assistenza per la configurazione del nuovo account.

2.  Dopo aver eseguito l'accesso, fare clic su **Nuovo** nell'angolo in alto a sinistra e cercare Archiviazione *account* e fare clic su **Invio.**

    ![ricerca di archiviazione di Azure](images/AzureLabs-Lab5-01.png)

    > [!NOTE]
    > La parola **Nuovo** potrebbe essere stata sostituita con **Crea una** risorsa nei portali più nuovi.

3.  La nuova pagina fornirà una descrizione del servizio *Archiviazione di Azure account.* Nella parte inferiore sinistra del prompt selezionare il **pulsante Crea** per creare un'associazione con questo servizio.

    ![creare un servizio](images/AzureLabs-Lab5-02.png)

4.  Dopo aver fatto clic su **Crea**:

    1.  Inserire un *nome* per l'account, tenere presente che questo campo accetta solo numeri e lettere minuscole.

    2.  Per *Modello di distribuzione* selezionare Gestione **risorse**.

    3.  Per *Tipo di account* selezionare Archiviazione **(utilizzo generico v1).**

    4.  Determinare *la posizione* per il gruppo di risorse (se si crea un nuovo gruppo di risorse). Il percorso si trova idealmente nell'area in cui verrebbe eseguita l'applicazione. Alcuni asset di Azure sono disponibili solo in determinate aree.

    5.  Per *Replica* selezionare **Read-access-geo-redundant storage (RA-GRS)**.

    6.  Per *Prestazioni* selezionare **Standard**.

    7.  Lasciare *Trasferimento sicuro obbligatorio* come **Disabilitato.**

    8.  Selezionare una *Sottoscrizione*.

    9. Scegliere un *gruppo di risorse* o crearne uno nuovo. Un gruppo di risorse consente di monitorare, controllare l'accesso, effettuare il provisioning e gestire la fatturazione per una raccolta di asset di Azure. È consigliabile mantenere tutti i servizi di Azure associati a un singolo progetto (ad esempio, questi lab) in un gruppo di risorse comune. 

        > Per altre informazioni sui gruppi di risorse di Azure, vedere [l'articolo gruppo di risorse](/azure/azure-resource-manager/resource-group-portal).

    10. È anche necessario verificare di aver compreso i termini e le condizioni applicati al servizio.

    11. Selezionare **Crea**.

        ![informazioni sul servizio di input](images/AzureLabs-Lab5-03.png)

5.  Dopo aver fatto clic su **Crea**, sarà necessario attendere la creazione del servizio, l'operazione potrebbe richiedere un minuto.

6.  Una volta creata l'istanza del servizio, nel portale verrà visualizzata una notifica.

    ![nuova notifica nel portale di Azure](images/AzureLabs-Lab5-04.png)

7.  Fare clic sulle notifiche per esplorare la nuova istanza del servizio.

    ![passare alla risorsa](images/AzureLabs-Lab5-05.png)

8.  Fare clic **sul pulsante Vai alla** risorsa nella notifica per esplorare la nuova istanza del servizio. Verrà eseguita la nuova istanza del servizio Archiviazione *account.*

    ![chiavi di accesso](images/AzureLabs-Lab5-06.png)

9.  Fare *clic su Chiavi di* accesso per visualizzare gli endpoint per questo servizio cloud. Usare *Blocco note* o simili, per copiare una delle chiavi per usarla in un secondo momento. Si noti anche il *valore Stringa* di connessione, che verrà usato nella classe *AzureServices,* che verrà creata in un secondo momento.

    ![copiare la stringa di connessione](images/AzureLabs-Lab5-07.png)

## <a name="chapter-2---setting-up-an-azure-function"></a>Capitolo 2 - Configurazione di una funzione di Azure

Si scriverà ora una **funzione di Azure**  nel servizio di Azure.

È possibile usare una funzione di **Azure** per eseguire quasi tutto ciò che si farebbe con una funzione classica nel codice, la differenza è che questa funzione è accessibile da qualsiasi applicazione che dispone di credenziali per accedere all'account Azure.

Per creare una funzione di Azure:

1.  Nel portale *di Azure* fare clic su **Nuovo** nell'angolo in alto a sinistra, cercare *App per* le funzioni e fare clic su **Invio.**

    ![creare un'app per le funzioni](images/AzureLabs-Lab5-08.png)

    > [!NOTE]
    > La parola **Nuovo** potrebbe essere stata sostituita con **Crea una** risorsa nei portali più nuovi.

2.  La nuova pagina fornirà una descrizione del servizio app per le *funzioni di Azure.* Nella parte inferiore sinistra del prompt selezionare il **pulsante Crea** per creare un'associazione con questo servizio.

    ![informazioni sull'app per le funzioni](images/AzureLabs-Lab5-09.png)

3.  Dopo aver fatto clic su **Crea:**

    1.  Specificare un Nome *app*. In questo caso è possibile usare solo lettere e numeri (sono consentite lettere maiuscole o minuscole).

    2.  Selezionare la sottoscrizione *preferita.*

    3. Scegliere un *gruppo di risorse* o crearne uno nuovo. Un gruppo di risorse consente di monitorare, controllare l'accesso, effettuare il provisioning e gestire la fatturazione per una raccolta di asset di Azure. È consigliabile mantenere tutti i servizi di Azure associati a un singolo progetto (ad esempio, questi lab) in un gruppo di risorse comune. 

        > Per altre informazioni sui gruppi di risorse di Azure, vedere [l'articolo sui gruppi di risorse.](/azure/azure-resource-manager/resource-group-portal)

    4.  Per questo esercizio, selezionare *Windows* come sistema **operativo scelto.**

    5.  Selezionare *Piano a consumo* per Piano di **hosting.**

    6.  Determinare *la località* per il gruppo di risorse (se si sta creando un nuovo gruppo di risorse). La posizione sarebbe idealmente nell'area in cui verrebbe eseguita l'applicazione. Alcuni asset di Azure sono disponibili solo in determinate aree. Per ottenere prestazioni ottimali, selezionare la stessa area dell'account di archiviazione.

    7.  Per *Archiviazione*, selezionare **Usa esistente** e quindi, usando il menu a discesa, trovare lo spazio di archiviazione creato in precedenza.

    8.  Lasciare *l'opzione Insights* per questo esercizio.

        ![Dettagli dell'app per le funzioni di input](images/AzureLabs-Lab5-10.png)

4.  Fare clic sul pulsante **Crea**.

5.  Dopo aver fatto clic su **Crea**, sarà necessario attendere la creazione del servizio. L'operazione potrebbe richiedere un minuto.

6.  Una volta creata l'istanza del servizio, nel portale verrà visualizzata una notifica.

    ![nuova notifica del portale di Azure](images/AzureLabs-Lab5-11.png)

7.  Fare clic sulle notifiche per esplorare la nuova istanza del servizio. 

    ![Passare all'app per le funzioni delle risorse](images/AzureLabs-Lab5-12.png)

8.  Fare clic **sul pulsante Vai alla** risorsa nella notifica per esplorare la nuova istanza del servizio. Si verrà portati alla nuova istanza del servizio *app* per le funzioni.

9.  Nel dashboard *dell'app* per le funzioni passare il puntatore del mouse su *Funzioni*, disponibile nel pannello a sinistra, quindi fare clic sul **simbolo + (segno** più).

    ![creare una nuova funzione](images/AzureLabs-Lab5-13.png)

10. Nella pagina successiva verificare che l'opzione **Webhook e API** sia selezionata e per Scegliere un linguaggio selezionare  **CSharp,** perché questo sarà il linguaggio usato per questa esercitazione. Infine, fare clic sul **pulsante Create this function (Crea questa** funzione).

    ![selezionare web hook csharp](images/AzureLabs-Lab5-14.png)

11. Dovrebbe essere visualizzata la tabella codici (run.csx). In caso contrario, fare clic sulla funzione appena creata nell'elenco Funzioni all'interno del pannello a sinistra.

    ![open new function](images/AzureLabs-Lab5-15.png)

12. Copiare il codice seguente nella funzione . Questa funzione restituirà semplicemente un numero intero casuale compreso tra 0 e 2 quando viene chiamato. Non preoccuparsi del codice esistente, è possibile incollarlo sopra di esso.

    ```csharp
        using System.Net;
        using System.Threading.Tasks;

        public static int Run(CustomObject req, TraceWriter log)
        {
            Random rnd = new Random();
            int randomInt = rnd.Next(0, 3);
            return randomInt;
        }

        public class CustomObject
        {
            public String name {get; set;}
        }
    ```

13. Selezionare **Save** (Salva).

14. Il risultato dovrebbe essere simile all'immagine seguente.

15. Fare clic **su Get function URL (Ottieni URL** funzione) e prendere nota *dell'endpoint* visualizzato. Sarà necessario inserirlo nella classe *AzureServices* che verrà creata più avanti in questo corso.

    ![Ottenere l'endpoint della funzione](images/AzureLabs-Lab5-16.png)

    ![Inserire l'endpoint della funzione](images/AzureLabs-Lab5-16-5.png)

## <a name="chapter-3---setting-up-the-unity-project"></a>Capitolo 3 - Configurazione del progetto Unity

Di seguito è riportata una configurazione tipica per lo sviluppo con realtà mista e, di conseguenza, è un buon modello per altri progetti.

Configurare e testare il visore VR immersive di realtà mista.

> [!NOTE]
> Per questo **corso non** saranno necessari controller del movimento. Se è necessario supporto per la configurazione del visore VR immersive, vedere [l'articolo sulla configurazione della realtà mista.](https://support.microsoft.com/help/4043101/windows-10-set-up-windows-mixed-reality)

1.  Aprire Unity e fare clic su **New (Nuovo).**

    ![Creare un nuovo progetto Unity](images/AzureLabs-Lab5-17.png)

2.  È ora necessario specificare un nome Project Unity. Inserire **MR_Azure_Functions**. Assicurarsi che il tipo di progetto sia impostato su **3D.** Impostare Il *percorso su* un percorso appropriato per l'utente(tenere presente che più vicino alle directory radice è meglio). Fare quindi clic **su Crea progetto**.

    ![Assegnare un nome al nuovo progetto Unity](images/AzureLabs-Lab5-18.png)

3.  Con Unity aperto, è opportuno controllare che l'editor di **script predefinito** sia impostato **su Visual Studio**. Passare a **Modifica**  >  **preferenze** e quindi dalla nuova finestra passare a **Strumenti esterni.** Modificare **External Script Editor in** Visual Studio **2017**. Chiudere la **finestra** Preferenze.

    ![impostare Visual Studio come editor di script](images/AzureLabs-Lab5-19.png)

4.  Passare quindi a **File** Build Impostazioni e passare alla piattaforma Universal Windows Platform facendo clic sul pulsante Switch Platform (Cambia  >   piattaforma).  

    ![Passare dalla piattaforma alla piattaforma uwp](images/AzureLabs-Lab5-20.png)

5.  Passare a **File**  >  **Build Impostazioni** (Compilazione file) e assicurarsi che:

    1. **Dispositivo di destinazione** è impostato su **Qualsiasi dispositivo.**

        > Per Microsoft HoloLens, impostare **Dispositivo di destinazione** *su HoloLens*.

    2. **Il tipo di** compilazione è impostato **su D3D**

    3. **L'SDK** è impostato su **Più recente installato**

    4. **Visual Studio versione è** impostata su **Versione più recente installata**

    5. **Build and Run (Compilazione** ed esecuzione) è impostato **su Local Machine (Computer locale)**

    6. Salvare la scena e aggiungerla alla compilazione.

        1.  A tale scopo, selezionare **Add Open Scenes (Aggiungi scene aperte).** Verrà visualizzata una finestra di salvataggio.

            ![aggiungere scene aperte](images/AzureLabs-Lab5-21.png)

        2.  Creare una nuova cartella per questa ed eventuali  scene future, quindi selezionare il pulsante Nuova cartella. Per creare una nuova cartella, assegnare alla nuova cartella il nome **Scenes**.

            ![creare la cartella scenes](images/AzureLabs-Lab5-22.png)

        3.  Aprire la cartella **Scenes appena** creata e quindi nel campo di testo **Nome file:** digitare **FunzioniScene** e quindi premere **Salva.**

            ![Salvare la scena delle funzioni](images/AzureLabs-Lab5-23.png)

6.  Le impostazioni rimanenti, in **Build Impostazioni**, per il momento devono essere lasciato come predefinite.

    ![Lasciare le impostazioni di compilazione predefinite](images/AzureLabs-Lab5-24.png)

7.  Nella finestra *build Impostazioni* fare clic sul pulsante **Player Impostazioni** per aprire il pannello correlato nello spazio in cui si trova *il controllo.*

    ![Impostazioni del lettore in Inspector](images/AzureLabs-Lab5-25.png)

8.  In questo pannello è necessario verificare alcune impostazioni:

    1.  Nella scheda **Altro Impostazioni:**

        1.  **La versione del runtime di** scripting deve essere **sperimentale** (equivalente a .NET 4.6), che attiverà la necessità di riavviare l'editor.
        2.  **Il back-end di** scripting deve **essere .NET**
        3.  **Il livello di compatibilità dell'API** **deve essere .NET 4.6**

    2.  **All'interno della Impostazioni** pubblicazione, in **Funzionalità** selezionare:
        
        -  **InternetClient**

            ![impostare le funzionalità](images/AzureLabs-Lab5-26.png)

    3.  Più in basso nel pannello, in **XR Impostazioni** (disponibile sotto **Publishing Impostazioni**), selezionare Virtual **Reality Supported**(Realtà virtuale supportata) e assicurarsi che sia stato aggiunto **Windows Mixed Reality SDK.**

        ![impostare le impostazioni XR](images/AzureLabs-Lab5-27.png)

9.  Tornare alla *compilazione Impostazioni* i *progetti C# Unity* non sono più disattivati; Selezionare la casella di controllo accanto a questo.

    ![Progetti c# tick](images/AzureLabs-Lab5-28.png)

10.  Chiudere la finestra Build Settings (Impostazioni di compilazione).

11. Salvare la scena e Project **(FILE**  >  **SAVE SCENE/FILE**  >  **SAVE PROJECT**).

## <a name="chapter-4---setup-main-camera"></a>Capitolo 4: Configurare la fotocamera principale

> [!IMPORTANT]
> Se si vuole ignorare i componenti *di configurazione* di Unity di questo corso e continuare direttamente con il codice, è possibile scaricare questo file con estensione [unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20305%20-%20Functions%20and%20storage/Azure-MR-305.unitypackage)e importarlo nel progetto come [pacchetto personalizzato.](https://docs.unity3d.com/Manual/AssetPackages.html) Conterrà anche le DLL del capitolo successivo. Dopo l'importazione, continuare [dal capitolo 7.](#chapter-7---create-the-azureservices-class) 

1.  Nel pannello *Hierarchy (Gerarchia)* è presente un oggetto denominato **Main Camera**(Fotocamera principale), che rappresenta il punto di vista "head" quando ci si trova "all'interno" dell'applicazione.

2.  Con il dashboard di Unity davanti all'utente, selezionare Main Camera GameObject ( **GameObject della fotocamera principale).** Si noterà che il pannello inspector *(in* genere disponibile a destra, all'interno del dashboard) mostrerà i vari componenti di *tale GameObject,* con *Transform* nella parte superiore, seguito da *Camera* e da altri componenti. Sarà necessario reimpostare la trasformazione della fotocamera principale, in modo che sia posizionata correttamente.

3.  A tale scopo, selezionare **l'icona** a forma di ingranaggio accanto al componente *Transform (Trasforma)* della fotocamera e selezionare **Reset (Reimposta).**

    ![reset transform](images/AzureLabs-Lab5-29.png)

4.  Aggiornare quindi il **componente Transform** in modo che sia simile al seguente:

    |         |    TRANSFORM - POSITION   |       |
    | :-----: | :-----------------------: | :----:|
    | **X**   | **S**                     | **Z** |
    | 0       | 1                         | 0     |    

    |       | TRASFORMAZIONE - ROTAZIONE |       |
    | :---: | :------------------: | :----:|
    | **X** | **S**                | **Z** |
    | 0     | 0                    | 0     |

    |       | TRANSFORM - SCALE |       |
    | :---: | :---------------: | :---: |
    | **X** | **S**             | **Z** |
    | 1     | 1                 | 1     |

    ![impostare la trasformazione della fotocamera](images/AzureLabs-Lab5-30.png)

## <a name="chapter-5---setting-up-the-unity-scene"></a>Capitolo 5 - Configurazione della scena unity

1.  Fare clic con il pulsante destro del mouse in un'area vuota del *pannello Gerarchia*, in **Oggetto 3D** aggiungere un **piano**.

    ![creare un nuovo piano](images/AzureLabs-Lab5-31.png)

2.  Con **l'oggetto Plane** selezionato, modifica i parametri seguenti nel *pannello Inspector (Controllo):*

    |       | TRANSFORM - POSITION |       |
    | :---: | :------------------: | :---: |
    | **X** | **S**                | **Z** |
    | 0     | 0                    | 4     |

    |       | TRANSFORM - SCALE |       |
    | :---: | :---------------: | :---: |
    | **X** | **S**             | **Z** |
    | 10    | 1                 | 10    |

    ![impostare la posizione e la scala del piano](images/AzureLabs-Lab5-32.png)

    ![visualizzazione della scena del piano](images/AzureLabs-Lab5-33.png)

3.  Fare clic con il pulsante destro del mouse in un'area vuota del *pannello Gerarchia*, in **Oggetto 3D** aggiungere un **cubo**.

    1.  Rinominare il cubo **in GazeButton** (con il cubo selezionato, premere 'F2').

    2.  Modificare i parametri seguenti nel *pannello inspector:*

        |       | TRANSFORM - POSITION |       |
        | :---: | :------------------: |:-----:|
        | **X** | **S**                | **Z** |
        | 0     | 3                    | 5     |


        ![impostare la trasformazione del pulsante sguardo fisso](images/AzureLabs-Lab5-34.png)

        ![visualizzazione della scena del pulsante sguardo fisso](images/AzureLabs-Lab5-35.png)

    3.  Fare clic sul **pulsante a** discesa Tag e fare clic su **Aggiungi tag** per aprire il riquadro & *livelli*.

        ![aggiungere un nuovo tag](images/AzureLabs-Lab5-36.png)

        ![selezionare più](images/AzureLabs-Lab5-37.png)

    4.  Selezionare il **pulsante + (segno più)** e nel campo New Tag Name (Nome nuovo *tag)* immettere **GazeButton** e premere **Save (Salva).**

        ![name new tag](images/AzureLabs-Lab5-38.png)

    5.  Fare clic **sull'oggetto GazeButton** nel pannello *Hierarchy (Gerarchia)* e nel pannello *Inspector (Controllo) assegnare* il tag **GazeButton appena** creato.

        ![Assegnare il pulsante sguardo fisso al nuovo tag](images/AzureLabs-Lab5-39.png)

4.  Fare clic con il pulsante destro del mouse sull'oggetto **GazeButton** nel pannello Hierarchy (Gerarchia) e aggiungere un **GameObject** vuoto (che verrà aggiunto come  *oggetto* figlio).

5.  Selezionare il nuovo oggetto e rinominarlo **ShapeSpawnPoint.**

    1.  Modificare i parametri seguenti nel *pannello inspector:*

        |       | TRANSFORM - POSITION |       |
        | :---: | :------------------: |:----: |
        | **X** |**S**                 | **Z** |
        | 0     | -1                   | 0     |

        ![aggiornare la trasformazione punto di generazione forma](images/AzureLabs-Lab5-40.png)

        ![Visualizzazione della scena del punto di generazione della forma](images/AzureLabs-Lab5-41.png)

6.  Si creerà quindi un **oggetto Testo 3D** per fornire commenti e suggerimenti sullo stato del servizio di Azure.

    Fare di nuovo clic con il pulsante destro del mouse su **GazeButton** nel pannello gerarchia e aggiungere un oggetto **3D Object**  >  **3D Text (Testo 3D oggetto 3D)** come *elemento figlio.*

    ![creare un nuovo oggetto testo 3D](images/AzureLabs-Lab5-42.png)

7.  Rinominare **l'oggetto 3D Text** in **AzureStatusText.**

8.  Modificare **l'oggetto Transform di AzureStatusText** come segue:

    |       | TRANSFORM - POSITION |       |
    | :---: | :------------------: | :---: |
    | **X** | **S**                | **Z** |
    | 0     | 0                    | -0,6  |

    |       | TRANSFORM - SCALE |       |
    | :---: | :---------------: | :---: |
    | **X** | **S**             | **Z** |
    | 0,1   | 0,1               | 0,1   |


    > [!NOTE]
    > Non c'è da preoccuparsi se sembra fuori dal centro, perché questo problema verrà risolto quando viene aggiornato il componente mesh di testo seguente.

9.  Modificare il **componente Mesh testo** in modo che corrisponda al seguente:

    ![impostare il componente mesh di testo](images/AzureLabs-Lab5-43.png)

    > [!TIP]
    > Il colore selezionato è hex color: **000000FF,** anche se è possibile sceglierne uno personalizzato, è sufficiente assicurarsi che sia leggibile.

10. La struttura del pannello gerarchia dovrebbe ora essere simile alla seguente:

    ![Mesh di testo nella gerarchia](images/AzureLabs-Lab5-43b.png)

10. La scena dovrebbe ora essere simile alla seguente:

    ![Mesh di testo nella visualizzazione scena](images/AzureLabs-Lab5-44.png)


## <a name="chapter-6---import-azure-storage-for-unity"></a>Capitolo 6 - Importare Archiviazione di Azure per Unity

Si usa Archiviazione di Azure per Unity ( che a sua volta sfrutta .NET SDK per Azure). Per altre informazioni, vedere [l'articolo Archiviazione di Azure per Unity.](/sandbox/gamedev/unity/azure-storage-unity)

Esiste attualmente un problema noto in Unity che richiede la riconfigurazione dei plug-in dopo l'importazione. Questi passaggi (da 4 a 7 in questa sezione) non saranno più necessari dopo la risoluzione del bug.

Per importare l'SDK nel proprio progetto, assicurarsi di aver scaricato la versione più recente di ['.unitypackage' da GitHub](https://aka.ms/azstorage-unitysdk). Procedere quindi come segue:

1.  Aggiungere il file **con estensione unitypackage** a Unity usando l'opzione di menu **Assets**  >  **Import Package**  >  **Custom Package (Importa pacchetto personalizzato** pacchetto asset).

2.  Nella casella **Import Unity Package (Importa** pacchetto Unity) visualizzata è possibile selezionare tutti gli elementi in **Plugin**  >  **Archiviazione**. Deselezionare tutti gli altri elementi, perché non sono necessari per questo corso.

    ![importare nel pacchetto](images/AzureLabs-Lab5-45.png)

3.  Fare clic **sul** pulsante Importa per aggiungere gli elementi al progetto.

4.  Passare alla cartella *Archiviazione* in *Plugins (Plug-in),* nella visualizzazione Project e selezionare solo i plug-in *seguenti:*

    -   Microsoft.Data.Edm
    -   Microsoft.Data.OData
    -   Microsoft.WindowsAzure.Storage
    -   Newtonsoft.Json
    -   System.Spatial

        ![Deselezionare Qualsiasi piattaforma](images/AzureLabs-Lab5-46.png)

5.  Con *questi plug-in specifici* selezionati, **deselezionare** *Any Platform (Qualsiasi* piattaforma) **e** *deselezionare WSAPlayer* e quindi fare clic su **Apply (Applica).**

    ![applicare le DLL della piattaforma](images/AzureLabs-Lab5-47.png)

    > [!NOTE]
    > Questi plug-in specifici vengono contrassegnati come da usare solo nell'editor di Unity. Ciò è dovuto al fatto che nella cartella WSA sono presenti versioni diverse degli stessi plug-in che verranno usati dopo l'esportazione del progetto da Unity.

6.  Nella cartella *Archiviazione* plug-in selezionare solo:

    -   Microsoft.Data.Services.Client

        ![set don't process for dlls](images/AzureLabs-Lab5-48.png)

7.  Selezionare la **casella Don't Process (Non** elaborare) in *Platform Impostazioni* e fare clic su **Apply (Applica).**

    ![non applicare alcuna elaborazione](images/AzureLabs-Lab5-49.png)

    > [!NOTE]
    > Il plug-in viene contrassegnato come "Non elaborare" perché il patcher di assembly Unity ha difficoltà a elaborare questo plug-in. Il plug-in continuerà a funzionare anche se non viene elaborato.

## <a name="chapter-7---create-the-azureservices-class"></a>Capitolo 7: Creare la classe AzureServices

La prima classe che si creerà è la *classe AzureServices.*

La *classe AzureServices* sarà responsabile di:

-   Archiviazione delle credenziali dell'account Azure.

-   Chiamata della funzione app Azure.

-   Il caricamento e il download del file di dati in Azure Cloud Archiviazione.

Per creare questa classe:

1.  Fare clic con il pulsante destro *del mouse nella* cartella Asset, che si trova nel pannello Project, **Crea**  >  **cartella**. Assegnare alla cartella il **nome Scripts**.

    ![creare una nuova cartella](images/AzureLabs-Lab5-50.png)

    ![cartella delle chiamate - script](images/AzureLabs-Lab5-51.png)

2.  Fare doppio clic sulla cartella appena creata per aprirla.

3.  Fare clic con il pulsante destro del mouse **all'interno della cartella Create**  >  **C# Script (Crea script C#).** Chiamare lo script *AzureServices*.

4.  Fare doppio clic sulla nuova *classe AzureServices* per aprirla con *Visual Studio*.

5.  Aggiungere gli spazi dei nomi seguenti all'inizio di *AzureServices:*

    ```csharp
        using System;
        using System.Threading.Tasks;
        using UnityEngine;
        using Microsoft.WindowsAzure.Storage;
        using Microsoft.WindowsAzure.Storage.File;
        using System.IO;
        using System.Net;
    ```

6.  Aggiungere i campi di controllo seguenti all'interno *della classe AzureServices:*

    ```csharp
        /// <summary>
        /// Provides Singleton-like behavior to this class.
        /// </summary>
        public static AzureServices instance;

        /// <summary>
        /// Reference Target for AzureStatusText Text Mesh object
        /// </summary>
        public TextMesh azureStatusText;
    ```

7.  Aggiungere quindi le variabili membro seguenti all'interno *della classe AzureServices:*

    ```csharp
        /// <summary>
        /// Holds the Azure Function endpoint - Insert your Azure Function
        /// Connection String here.
        /// </summary>

        private readonly string azureFunctionEndpoint = "--Insert here you AzureFunction Endpoint--";

        /// <summary>
        /// Holds the Storage Connection String - Insert your Azure Storage
        /// Connection String here.
        /// </summary>
        private readonly string storageConnectionString = "--Insert here you AzureStorage Connection String--";

        /// <summary>
        /// Name of the Cloud Share - Hosts directories.
        /// </summary>
        private const string fileShare = "fileshare";

        /// <summary>
        /// Name of a Directory within the Share
        /// </summary>
        private const string storageDirectory = "storagedirectory";

        /// <summary>
        /// The Cloud File
        /// </summary>
        private CloudFile shapeIndexCloudFile;

        /// <summary>
        /// The Linked Storage Account
        /// </summary>
        private CloudStorageAccount storageAccount;

        /// <summary>
        /// The Cloud Client
        /// </summary>
        private CloudFileClient fileClient;

        /// <summary>
        /// The Cloud Share - Hosts Directories
        /// </summary>
        private CloudFileShare share;

        /// <summary>
        /// The Directory in the share that will host the Cloud file
        /// </summary>
        private CloudFileDirectory dir;
    ```

    > [!IMPORTANT]
    > Assicurarsi di sostituire i valori *dell'endpoint* *e della stringa di* connessione con i valori dell'archiviazione di Azure, disponibili nel portale di Azure

8.  È ora necessario aggiungere il codice per i metodi *Awake()* e *Start().* Questi metodi verranno chiamati quando la classe inizializza:

    ```csharp
        private void Awake()
        {
            instance = this;
        }

        // Use this for initialization
        private void Start()
        {
            // Set the Status text to loading, whilst attempting connection to Azure.
            azureStatusText.text = "Loading...";
        }

        /// <summary>
        /// Call to the Azure Function App to request a Shape.
        /// </summary>
        public async void CallAzureFunctionForNextShape()
        {

        }
    ```

    > [!IMPORTANT]
    > Il codice per *CallAzureFunctionForNextShape()* verrà riempito in un [capitolo futuro.](#chapter-10---completing-the-azureservices-class)

9.  Eliminare il *metodo Update()* perché questa classe non lo userà.

10. Salvare le modifiche in Visual Studio e quindi tornare a Unity.

11. Fare clic e trascinare *la classe AzureServices* dalla cartella Scripts (Script) all'oggetto Main Camera (Fotocamera principale) nel *pannello Hierarchy (Gerarchia).*

12. Selezionare la fotocamera principale, quindi afferrare l'oggetto figlio **AzureStatusText** sotto l'oggetto **GazeButton** e posizionarlo all'interno del campo di destinazione di riferimento **AzureStatusText,** in *Inspector,* per fornire il riferimento allo script *AzureServices.*

    ![assegnare la destinazione di riferimento per il testo di stato di Azure](images/AzureLabs-Lab5-52.png)

## <a name="chapter-8---create-the-shapefactory-class"></a>Capitolo 8: Creare la classe ShapeFactory

Lo script successivo da creare è la *classe ShapeFactory.* Il ruolo di questa classe è creare una nuova forma, quando richiesto, e mantenere una cronologia delle forme create in un elenco cronologia *forme*. Ogni volta che viene creata una forma, *l'elenco* Cronologia forme viene aggiornato nella *classe AzureService* e quindi archiviato nel *Archiviazione di Azure*. All'avvio dell'applicazione, se viene trovato un file  archiviato nel *Archiviazione di Azure ,* l'elenco Cronologia forme viene recuperato e riprodotto, con l'oggetto Testo **3D** che indica se la forma generata deriva dall'archiviazione o è nuova.

Per creare questa classe:

1.  Passare alla cartella **Scripts** creata in precedenza.

2.  Fare clic con il pulsante destro del mouse **all'interno della cartella Create**  >  **C# Script (Crea script C#).** Chiamare lo script *ShapeFactory.*

3.  Fare doppio clic sul nuovo script *ShapeFactory* per aprirlo con *Visual Studio*.

4.  Verificare che la *classe ShapeFactory* includa gli spazi dei nomi seguenti:

    ```csharp
        using System.Collections.Generic;
        using UnityEngine;
    ```

5.  Aggiungere le variabili illustrate di seguito *alla classe ShapeFactory* e sostituire le funzioni *Start()* e *Awake()* con quelle riportate di seguito:

    ```csharp
        /// <summary>
        /// Provide this class Singleton-like behaviour
        /// </summary>
        [HideInInspector]
        public static ShapeFactory instance;

        /// <summary>
        /// Provides an Inspector exposed reference to ShapeSpawnPoint
        /// </summary>
        [SerializeField]
        public Transform spawnPoint;

        /// <summary>
        /// Shape History Index
        /// </summary>
        [HideInInspector]
        public List<int> shapeHistoryList;

        /// <summary>
        /// Shapes Enum for selecting required shape
        /// </summary>
        private enum Shapes { Cube, Sphere, Cylinder }

        private void Awake()
        {
            instance = this;
        }

        private void Start()
        {
            shapeHistoryList = new List<int>();
        }
    ```

6.  Il *metodo CreateShape()* genera le forme primitive, in base al parametro *integer* specificato. Il parametro booleano viene usato per specificare se la forma attualmente creata deriva dall'archiviazione o se è nuova. Inserire il codice seguente nella *classe ShapeFactory,* sotto i metodi precedenti:

    ```csharp
        /// <summary>
        /// Use the Shape Enum to spawn a new Primitive object in the scene
        /// </summary>
        /// <param name="shape">Enumerator Number for Shape</param>
        /// <param name="storageShape">Provides whether this is new or old</param>
        internal void CreateShape(int shape, bool storageSpace)
        {
            Shapes primitive = (Shapes)shape;
            GameObject newObject = null;
            string shapeText = storageSpace == true ? "Storage: " : "New: ";

            AzureServices.instance.azureStatusText.text = string.Format("{0}{1}", shapeText, primitive.ToString());

            switch (primitive)
            {
                case Shapes.Cube:
                newObject = GameObject.CreatePrimitive(PrimitiveType.Cube);
                break;

                case Shapes.Sphere:
                newObject = GameObject.CreatePrimitive(PrimitiveType.Sphere);
                break;

                case Shapes.Cylinder:
                newObject = GameObject.CreatePrimitive(PrimitiveType.Cylinder);
                break;
            }

            if (newObject != null)
            {
                newObject.transform.position = spawnPoint.position;

                newObject.transform.localScale = new Vector3(0.5f, 0.5f, 0.5f);

                newObject.AddComponent<Rigidbody>().useGravity = true;

                newObject.GetComponent<Renderer>().material.color = UnityEngine.Random.ColorHSV(0f, 1f, 1f, 1f, 0.5f, 1f);
            }
        }
    ```

7.  Assicurarsi di salvare le modifiche in Visual Studio prima di tornare a Unity.

8.  Nell'editor di Unity fare clic e trascinare la *classe ShapeFactory* dalla **cartella Scripts** all'oggetto Main **Camera (Fotocamera** principale) nel pannello Hierarchy *(Gerarchia).*

9. Con la fotocamera principale selezionata si noterà che il componente script *ShapeFactory* non ha il riferimento *Spawn Point (Genera* punto). Per risolvere il problema, trascinare **l'oggetto ShapeSpawnPoint** dal pannello *Gerarchia* alla destinazione **di riferimento spawn point.**

    ![Impostare la destinazione di riferimento di shape factory](images/AzureLabs-Lab5-53.png)

## <a name="chapter-9---create-the-gaze-class"></a>Capitolo 9 - Creare la classe Gaze

L'ultimo script da creare è la *classe Gaze.*

Questa classe è responsabile della creazione di **un raycast** che verrà proiettato in avanti dalla fotocamera principale, per rilevare l'oggetto che l'utente sta guardando. In questo caso, Raycast dovrà identificare se l'utente sta esaminando l'oggetto **GazeButton** nella scena e attivare un comportamento.

Per creare questa classe:

1.  Passare alla cartella **Scripts** creata in precedenza.

2.  Fare clic con il pulsante destro del mouse nel Project, **Crea**  >  **script C#.** Chiamare lo script *Gaze*.

3.  Fare doppio clic sul nuovo script *Gaze* per aprirlo con *Visual Studio.*

4.  Verificare che lo spazio dei nomi seguente sia incluso all'inizio dello script:

    ```csharp
        using UnityEngine;
    ```

5.  Aggiungere quindi le variabili seguenti all'interno *della classe Gaze:*

    ```csharp
        /// <summary>
        /// Provides Singleton-like behavior to this class.
        /// </summary>
        public static Gaze instance;

        /// <summary>
        /// The Tag which the Gaze will use to interact with objects. Can also be set in editor.
        /// </summary>
        public string InteractibleTag = "GazeButton";

        /// <summary>
        /// The layer which will be detected by the Gaze ('~0' equals everything).
        /// </summary>
        public LayerMask LayerMask = ~0;

        /// <summary>
        /// The Max Distance the gaze should travel, if it has not hit anything.
        /// </summary>
        public float GazeMaxDistance = 300;

        /// <summary>
        /// The size of the cursor, which will be created.
        /// </summary>
        public Vector3 CursorSize = new Vector3(0.05f, 0.05f, 0.05f);

        /// <summary>
        /// The color of the cursor - can be set in editor.
        /// </summary>
        public Color CursorColour = Color.HSVToRGB(0.0223f, 0.7922f, 1.000f);

        /// <summary>
        /// Provides when the gaze is ready to start working (based upon whether
        /// Azure connects successfully).
        /// </summary>
        internal bool GazeEnabled = false;

        /// <summary>
        /// The currently focused object.
        /// </summary>
        internal GameObject FocusedObject { get; private set; }

        /// <summary>
        /// The object which was last focused on.
        /// </summary>
        internal GameObject _oldFocusedObject { get; private set; }

        /// <summary>
        /// The info taken from the last hit.
        /// </summary>
        internal RaycastHit HitInfo { get; private set; }

        /// <summary>
        /// The cursor object.
        /// </summary>
        internal GameObject Cursor { get; private set; }

        /// <summary>
        /// Provides whether the raycast has hit something.
        /// </summary>
        internal bool Hit { get; private set; }

        /// <summary>
        /// This will store the position which the ray last hit.
        /// </summary>
        internal Vector3 Position { get; private set; }

        /// <summary>
        /// This will store the normal, of the ray from its last hit.
        /// </summary>
        internal Vector3 Normal { get; private set; }

        /// <summary>
        /// The start point of the gaze ray cast.
        /// </summary>
        private Vector3 _gazeOrigin;

        /// <summary>
        /// The direction in which the gaze should be.
        /// </summary>
        private Vector3 _gazeDirection;
    ```

> [!IMPORTANT]
> Alcune di queste variabili potranno essere modificate *nell'editor*.

6.  È ora necessario aggiungere il codice per i metodi *Awake()* e *Start().*

    ```csharp
        /// <summary>
        /// The method used after initialization of the scene, though before Start().
        /// </summary>
        private void Awake()
        {
            // Set this class to behave similar to singleton
            instance = this;
        }

        /// <summary>
        /// Start method used upon initialization.
        /// </summary>
        private void Start()
        {
            FocusedObject = null;
            Cursor = CreateCursor();
        }
    ```

7.  Aggiungere il codice seguente, che creerà un oggetto cursore all'inizio, insieme al metodo *Update(),* che eseguirà il metodo Raycast, insieme alla posizione in cui viene attivato o disattivato il valore booleano GazeEnabled:

    ```csharp
        /// <summary>
        /// Method to create a cursor object.
        /// </summary>
        /// <returns></returns>
        private GameObject CreateCursor()
        {
            GameObject newCursor = GameObject.CreatePrimitive(PrimitiveType.Sphere);
            newCursor.SetActive(false);

            // Remove the collider, so it doesn't block raycast.
            Destroy(newCursor.GetComponent<SphereCollider>());
            newCursor.transform.localScale = CursorSize;

            newCursor.GetComponent<MeshRenderer>().material = new Material(Shader.Find("Diffuse"))
            {
                color = CursorColour
            };

            newCursor.name = "Cursor";

            newCursor.SetActive(true);

            return newCursor;
        }

        /// <summary>
        /// Called every frame
        /// </summary>
        private void Update()
        {
            if(GazeEnabled == true)
            {
                _gazeOrigin = Camera.main.transform.position;

                _gazeDirection = Camera.main.transform.forward;

                UpdateRaycast();
            }
        }
    ```

8. Aggiungere quindi il *metodo UpdateRaycast(),* che proietta un Raycast e rileva la destinazione di hit.

    ```csharp
        private void UpdateRaycast()
        {
            // Set the old focused gameobject.
            _oldFocusedObject = FocusedObject;

            RaycastHit hitInfo;

            // Initialise Raycasting.
            Hit = Physics.Raycast(_gazeOrigin,
                _gazeDirection,
                out hitInfo,
                GazeMaxDistance, LayerMask);

            HitInfo = hitInfo;

            // Check whether raycast has hit.
            if (Hit == true)
            {
                Position = hitInfo.point;

                Normal = hitInfo.normal;

                // Check whether the hit has a collider.
                if (hitInfo.collider != null)
                {
                    // Set the focused object with what the user just looked at.
                    FocusedObject = hitInfo.collider.gameObject;
                }
                else
                {
                    // Object looked on is not valid, set focused gameobject to null.
                    FocusedObject = null;
                }
            }
            else
            {
                // No object looked upon, set focused gameobject to null.
                FocusedObject = null;

                // Provide default position for cursor.
                Position = _gazeOrigin + (_gazeDirection * GazeMaxDistance);

                // Provide a default normal.
                Normal = _gazeDirection;
            }

            // Lerp the cursor to the given position, which helps to stabilize the gaze.
            Cursor.transform.position = Vector3.Lerp(Cursor.transform.position, Position, 0.6f);

            // Check whether the previous focused object is this same 
            //    object. If so, reset the focused object.
            if (FocusedObject != _oldFocusedObject)
            {
                ResetFocusedObject();

                if (FocusedObject != null)
                {
                if (FocusedObject.CompareTag(InteractibleTag.ToString()))
                {
                        // Set the Focused object to green - success!
                        FocusedObject.GetComponent<Renderer>().material.color = Color.green;

                        // Start the Azure Function, to provide the next shape!
                        AzureServices.instance.CallAzureFunctionForNextShape();
                    }
                }
            }
        }
    ```

9. Infine, aggiungere il *metodo ResetFocusedObject(),* che attiva o disattiva il colore corrente degli oggetti GazeButton, indicando se sta creando o meno una nuova forma.

    ```csharp
        /// <summary>
        /// Reset the old focused object, stop the gaze timer, and send data if it
        /// is greater than one.
        /// </summary>
        private void ResetFocusedObject()
        {
            // Ensure the old focused object is not null.
            if (_oldFocusedObject != null)
            {
                if (_oldFocusedObject.CompareTag(InteractibleTag.ToString()))
                {
                    // Set the old focused object to red - its original state.
                    _oldFocusedObject.GetComponent<Renderer>().material.color = Color.red;
                }
            }
        }
    ```

10.  Salvare le modifiche in Visual Studio prima di tornare a Unity.

11.  Fare clic e *trascinare la* classe Gaze dalla cartella Script all'oggetto **Fotocamera** principale nel *pannello Gerarchia*.

## <a name="chapter-10---completing-the-azureservices-class"></a>Capitolo 10 - Completamento della classe AzureServices

Con gli altri script disponibili, è ora possibile *completare la* *classe AzureServices.* Questa operazione verrà ottenuta tramite:

1.  Aggiunta di un nuovo metodo denominato *CreateCloudIdentityAsync()* per configurare le variabili di autenticazione necessarie per la comunicazione con Azure.

    > Questo metodo verifica anche l'esistenza di un file archiviato in precedenza contenente l'elenco forme.
    >
    > **Se il file viene trovato,** disabilita lo sguardo dell'utente e attiva la creazione di forme, in base al modello di forme, come archiviato nel **file Archiviazione di Azure .** L'utente può visualizzarlo, perché la mesh di testo fornirà la visualizzazione "Archiviazione" o "Nuovo", a seconda dell'origine delle forme. 
    >
    > **Se non viene trovato alcun file,** verrà abilitato *lo sguardo* fisso , consentendo all'utente di creare forme quando osserva l'oggetto **GazeButton** nella scena.

    ```csharp
        /// <summary>
        /// Create the references necessary to log into Azure
        /// </summary>
        private async void CreateCloudIdentityAsync()
        {
            // Retrieve storage account information from connection string
            storageAccount = CloudStorageAccount.Parse(storageConnectionString);

            // Create a file client for interacting with the file service.
            fileClient = storageAccount.CreateCloudFileClient();

            // Create a share for organizing files and directories within the storage account.
            share = fileClient.GetShareReference(fileShare);

            await share.CreateIfNotExistsAsync();

            // Get a reference to the root directory of the share.
            CloudFileDirectory root = share.GetRootDirectoryReference();

            // Create a directory under the root directory
            dir = root.GetDirectoryReference(storageDirectory);

            await dir.CreateIfNotExistsAsync();

            //Check if the there is a stored text file containing the list
            shapeIndexCloudFile = dir.GetFileReference("TextShapeFile");

            if (!await shapeIndexCloudFile.ExistsAsync())
            {
                // File not found, enable gaze for shapes creation
                Gaze.instance.GazeEnabled = true;

                azureStatusText.text = "No Shape\nFile!";
            }
            else
            {
                // The file has been found, disable gaze and get the list from the file
                Gaze.instance.GazeEnabled = false;

                azureStatusText.text = "Shape File\nFound!";

                await ReplicateListFromAzureAsync();
            }
        }
    ```

2.  Il frammento di codice successivo è all'interno *del metodo Start().* in cui verrà effettuata una chiamata al *metodo CreateCloudIdentityAsync().* È possibile eseguire la copia sul metodo *Start()* corrente, con il codice seguente:

    ```csharp
        private void Start()
        {
            // Disable TLS cert checks only while in Unity Editor (until Unity adds support for TLS)
    #if UNITY_EDITOR
            ServicePointManager.ServerCertificateValidationCallback = delegate { return true; };
    #endif

            // Set the Status text to loading, whilst attempting connection to Azure.
            azureStatusText.text = "Loading...";

            //Creating the references necessary to log into Azure and check if the Storage Directory is empty
            CreateCloudIdentityAsync();
        }
    ```

3.  Compilare il codice per il *metodo CallAzureFunctionForNextShape()*. Si userà l'app per le funzioni *di Azure creata in precedenza* per richiedere un indice di forma. Dopo aver ricevuto la nuova forma, questo metodo invierà la forma alla *classe ShapeFactory* per creare la nuova forma nella scena. Usare il codice seguente per completare il corpo *di CallAzureFunctionForNextShape()*.

    ```csharp
        /// <summary>
        /// Call to the Azure Function App to request a Shape.
        /// </summary>
        public async void CallAzureFunctionForNextShape()
        {
            int azureRandomInt = 0;

            // Call Azure function
            HttpWebRequest webRequest = WebRequest.CreateHttp(azureFunctionEndpoint);

            WebResponse response = await webRequest.GetResponseAsync();

            // Read response as string
            using (Stream stream = response.GetResponseStream())
            {
                StreamReader reader = new StreamReader(stream);

                String responseString = reader.ReadToEnd();

                //parse result as integer
                Int32.TryParse(responseString, out azureRandomInt);
            }

            //add random int from Azure to the ShapeIndexList
            ShapeFactory.instance.shapeHistoryList.Add(azureRandomInt);

            ShapeFactory.instance.CreateShape(azureRandomInt, false);

            //Save to Azure storage
            await UploadListToAzureAsync();
        }
    ```

4.  Aggiungere un metodo per creare una stringa, concatenando i numeri interi archiviati nell'elenco della cronologia delle forme e salvando la stringa *nel Archiviazione di Azure File*.

    ```csharp
        /// <summary>
        /// Upload the locally stored List to Azure
        /// </summary>
        private async Task UploadListToAzureAsync()
        {
            // Uploading a local file to the directory created above
            string listToString = string.Join(",", ShapeFactory.instance.shapeHistoryList.ToArray());

            await shapeIndexCloudFile.UploadTextAsync(listToString);
        }
    ```

5.  Aggiungere un metodo per recuperare il testo archiviato nel file che si trova nel file *Archiviazione di Azure e* *deserializzarlo* in un elenco.

6.  Al termine di questo processo, il metodo abilita nuovamente lo sguardo in modo che l'utente possa aggiungere altre forme alla scena.

    ```csharp
        ///<summary>
        /// Get the List stored in Azure and use the data retrieved to replicate 
        /// a Shape creation pattern
        ///</summary>
        private async Task ReplicateListFromAzureAsync()
        {
            string azureTextFileContent = await shapeIndexCloudFile.DownloadTextAsync();

            string[] shapes = azureTextFileContent.Split(new char[] { ',' });

            foreach (string shape in shapes)
            {
                int i;

                Int32.TryParse(shape.ToString(), out i);

                ShapeFactory.instance.shapeHistoryList.Add(i);

                ShapeFactory.instance.CreateShape(i, true);

                await Task.Delay(500);
            }

            Gaze.instance.GazeEnabled = true;

            azureStatusText.text = "Load Complete!";
        }
    ```

7.  Salvare le modifiche in Visual Studio prima di tornare a Unity.

## <a name="chapter-11---build-the-uwp-solution"></a>Capitolo 11 - Compilare la soluzione UWP

Per avviare il processo di compilazione:

1.  Passare a **Compilazione**  >  **file Impostazioni**.

    ![Compilare l'app](images/AzureLabs-Lab5-54.png)

2.  Fare clic su **Compila**. Unity avvierà una *Esplora file,* in cui è necessario creare e quindi selezionare una cartella in cui compilare l'app. Creare la cartella e assegnare alla cartella il nome *App*. Quindi, con la *cartella App* selezionata, premere **Seleziona cartella**.

3.  Unity inizierà a compilare il progetto nella *cartella App.*

4.  Al termine della compilazione di Unity (potrebbe essere necessario del tempo), verrà aperta una finestra *Esplora file* nel percorso della compilazione (controllare la barra delle applicazioni, perché potrebbe non essere sempre visualizzata sopra le finestre, ma verrà notificata l'aggiunta di una nuova finestra).

## <a name="chapter-12---deploying-your-application"></a>Capitolo 12 - Distribuzione dell'applicazione

Per distribuire l'applicazione:

1.  Passare alla *cartella App* creata nell'ultimo [capitolo](#chapter-11---build-the-uwp-solution). Verrà visualizzato un file con il nome delle app, con *l'estensione*'.sln', su cui è necessario fare doppio clic, in modo da aprirlo all'interno Visual Studio .

2.  In **Piattaforma soluzione selezionare** **x86, Computer locale**.

3.  In **Configurazione soluzione selezionare** **Debug**.

    > Per il Microsoft HoloLens, potrebbe risultare più semplice impostare questa opzione su *Computer* remoto, in modo che non sia necessario eseguire il tethering al computer. Tuttavia, è necessario eseguire anche le operazioni seguenti:
    > - Conoscere **l'indirizzo IP** del HoloLens, disponibile in Impostazioni  >  **Network & Internet**  >  **Wi-Fi** Advanced  >  **Options**. L'indirizzo IPv4 è l'indirizzo da usare. 
    > - Assicurarsi **che la modalità sviluppatore** sia **attivata.** disponibile in **Impostazioni**  >  **Update & Security** For  >  **Developers**.

    ![distribuire la soluzione](images/AzureLabs-Lab5-55.png)

4.  Passare al menu **Compila** e fare clic su **Distribuisci soluzione** per eseguire il sideload dell'applicazione nel computer.

5.  L'app dovrebbe ora essere visualizzata nell'elenco delle app installate, pronte per essere avviate e testate.

## <a name="your-finished-azure-functions-and-storage-application"></a>L'applicazione Funzioni di Azure e Archiviazione completata

È stata compilata un'app di realtà mista che sfrutta i Funzioni di Azure e Archiviazione di Azure servizio. L'app sarà in grado di disegnare sui dati archiviati e fornire un'azione basata su tale dati.

![final product -end](images/AzureLabs-Lab5-00.png)

## <a name="bonus-exercises"></a>Esercizi aggiuntivi

### <a name="exercise-1"></a>Esercizio 1

Creare un secondo punto di generazione e registrare il punto di generazione da cui è stato creato un oggetto. Quando si carica il file di dati, riprodurre le forme da generare dal percorso in cui sono state create in origine.

### <a name="exercise-2"></a>Esercizio 2

Creare un modo per riavviare l'app, anziché doverla ria aprirla ogni volta. **Il caricamento di** scene è un buon punto di partenza. Dopo questa operazione, creare un modo per cancellare l'elenco archiviato *in* Archiviazione di Azure , in modo che possa essere reimpostato facilmente dall'app.
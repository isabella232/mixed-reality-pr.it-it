---
title: HoloLens (prima generazione) e Azure 307 - Machine Learning
description: Completare questo corso per imparare a implementare Azure Machine Learning Studio (versione classica) all'interno di un'applicazione di realtà mista.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure, realtà mista, academy, unity, esercitazione, API, Machine Learning, ml, Machine Learning Studio, hololens, immersive, vr, Windows 10, Visual Studio
ms.openlocfilehash: 062be48afb69bf2c4fa2eddcd816070d4d2575da7f06fe4464fa87f85676796b
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115199015"
---
# <a name="hololens-1st-gen-and-azure-307-machine-learning"></a>HoloLens (prima generazione) e Azure 307: Machine Learning

<br>

>[!NOTE]
>Le esercitazioni di Mixed Reality Academy sono state progettate in base a HoloLens (prima generazione) e ai visori VR immersive di realtà mista.  Pertanto, riteniamo importante lasciarle a disposizione degli sviluppatori a cui serve ancora materiale sussidiario per lo sviluppo di questi dispositivi.  Queste esercitazioni **_non_** verranno aggiornate con i set di strumenti o le interazioni più recenti usati per HoloLens 2.  Rimarranno invariate per consentire di continuare a lavorare sui dispositivi supportati. In futuro verrà pubblicata una nuova serie di esercitazioni che illustrano come sviluppare per HoloLens 2.  Questa comunicazione verrà aggiornata con un collegamento a tali esercitazioni al momento della pubblicazione.

<br>

![final product -start](images/AzureLabs-Lab7-0.png)

In questo corso si apprenderà come aggiungere funzionalità Machine Learning (ML) a un'applicazione di realtà mista usando Azure Machine Learning Studio (versione classica).

*Azure Machine Learning Studio (versione classica)* è un servizio Microsoft che offre agli sviluppatori un numero elevato di algoritmi di Machine Learning che possono essere utili per l'input, l'output, la preparazione e la visualizzazione dei dati. Da questi componenti è quindi possibile sviluppare un esperimento di analisi predittiva, eseguire l'iterazione su di esso e usarlo per eseguire il training del modello. Dopo il training, è possibile rendere operativo il modello all'interno del cloud di Azure, in modo che possa quindi segnare nuovi dati. Per altre informazioni, visitare [la pagina Azure Machine Learning Studio (versione classica).](https://azure.microsoft.com/services/machine-learning-studio/)

Dopo aver completato questo corso, si avrà un'applicazione per visori VR immersive di realtà mista e si sarà appreso come eseguire le operazioni seguenti:

1.  Fornire una tabella di dati di vendita *al portale di Azure Machine Learning Studio (versione classica)* e progettare un algoritmo per stimare le vendite future degli articoli più diffusi.
2.  Creare **un'Project Unity** che possa ricevere e interpretare i dati di stima dal ML servizio.
3.  Visualizzare visivamente i dati di predicazione all'interno del **Project Unity,** fornendo su uno scaffale gli articoli di vendita più diffusi.

Nell'applicazione è necessario sapere come integrare i risultati con la progettazione. Questo corso è stato progettato per illustrare come integrare un servizio di Azure con unity Project. È compito dell'utente usare le conoscenze acquisite in questo corso per migliorare l'applicazione di realtà mista.

Questo corso è un'esercitazione autonoma, che non coinvolge direttamente altri lab di realtà mista.

## <a name="device-support"></a>Supporto di dispositivi

<table>
<tr>
<th>Corso</th><th style="width:150px"> <a href="/hololens/hololens1-hardware">HoloLens</a></th><th style="width:150px"> <a href="../../../discover/immersive-headset-hardware-details.md">Visori VR immersive</a></th>
</tr><tr>
<td> MR e Azure 307: Machine Learning</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> Anche se questo corso è in particolare in Windows Mixed Reality visori VR immersive, è anche possibile applicare ciò che si apprende in questo corso per Microsoft HoloLens. Man mano che si segue il corso, verranno visualizzati note sulle eventuali modifiche che potrebbe essere necessario applicare per supportare HoloLens. Quando si usa HoloLens, è possibile notare un'eco durante l'acquisizione vocale.

## <a name="prerequisites"></a>Prerequisiti

> [!NOTE]
> Questa esercitazione è destinata agli sviluppatori che hanno esperienza di base con Unity e C#. Tenere presente anche che i prerequisiti e le istruzioni scritte all'interno di questo documento rappresentano ciò che è stato testato e verificato al momento della stesura di questo documento (maggio 2018). È possibile usare il software più recente, come indicato nell'articolo installare gli strumenti [,](../../install-the-tools.md)anche se non si deve presunire che le informazioni in questo corso corrispondano perfettamente a quelle disponibili nel software più recente rispetto a quanto elencato di seguito.

Per questo corso è consigliabile usare l'hardware e il software seguenti:

- Un PC di sviluppo, [compatibile con le Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) per lo sviluppo di visori VR immersive
- [Windows 10 Fall Creators Update (o versione successiva) con la modalità sviluppatore abilitata](../../install-the-tools.md#installation-checklist)
- [L'SDK Windows 10 più recente](../../install-the-tools.md#installation-checklist)
- [Unity 2017.4](../../install-the-tools.md#installation-checklist)
- [Visual Studio 2017](../../install-the-tools.md#installation-checklist)
- Un [visore VR o](../../../discover/immersive-headset-hardware-details.md) un visore [Microsoft HoloLens](/hololens/hololens1-hardware) VR Windows Mixed Reality con la modalità sviluppatore abilitata
- Accesso a Internet per l'installazione e il recupero ML Azure

## <a name="before-you-start"></a>Prima di iniziare

Per evitare di riscontrare problemi durante la compilazione di questo progetto, è consigliabile creare il progetto indicato in questa esercitazione in una cartella radice o quasi (i percorsi di cartelle lunghi possono causare problemi in fase di compilazione). 

## <a name="chapter-1---azure-storage-account-setup"></a>Capitolo 1- Configurazione Archiviazione di Azure account

Per usare l'API Translator Azure, è necessario configurare un'istanza del servizio in modo che sia resa disponibile per l'applicazione.
1.  Accedere al portale [di Azure.](https://portal.azure.com)

    > [!NOTE]
    > Se non si ha già un account Azure, è necessario crearne uno. Se si sta seguendo questa esercitazione in una situazione di classe o di lab, chiedere all'insegnante o a uno dei protori di assistenza per la configurazione del nuovo account.

2.  Dopo aver eseguito l'accesso, fare **clic Archiviazione account nel** menu a sinistra.

    ![Archiviazione di Azure Configurazione dell'account](images/AzureLabs-Lab7-1.png)

    > [!NOTE]
    > La parola **Nuovo** potrebbe essere stata sostituita **con Crea una risorsa** nei portali più nuovi.

3.  Nella scheda **Archiviazione Account** fare clic su **Aggiungi**.

    ![Archiviazione di Azure Configurazione dell'account](images/AzureLabs-Lab7-2.png)

4.  Nel pannello **Crea Archiviazione account:**

    1.  Inserire un **Nome** per l'account, tenere presente che questo campo accetta solo numeri e lettere minuscole.
    2.  Per **Modello di distribuzione selezionare** Gestione **risorse.**
    3.  Per **Tipo di account** selezionare Archiviazione **(utilizzo generico v1).**
    4.  Per **Prestazioni** selezionare **Standard**.
    5.  Per **Replica** selezionare **Archiviazione con ridondanza geografica e accesso in lettura (RA-GRS).**
    6.  Lasciare **Trasferimento sicuro obbligatorio** su **Disabilitato.**
    7.  Selezionare una **Sottoscrizione**.
    4. Scegliere un **gruppo di risorse** o crearne uno nuovo. Un gruppo di risorse consente di monitorare, controllare l'accesso, effettuare il provisioning e gestire la fatturazione per una raccolta di asset di Azure. È consigliabile mantenere tutti i servizi di Azure associati a un singolo progetto (ad esempio, questi lab) in un gruppo di risorse comune.

        > Per altre informazioni sui gruppi di risorse di Azure, vedere [l'articolo sui gruppi di risorse.](/azure/azure-resource-manager/resource-group-portal)
    
    5.  Determinare **la località** per il gruppo di risorse (se si sta creando un nuovo gruppo di risorse). La posizione sarebbe idealmente nell'area in cui verrebbe eseguita l'applicazione. Alcuni asset di Azure sono disponibili solo in determinate aree.

5.  È anche necessario confermare di aver compreso i termini e le condizioni applicati al servizio.

    ![Archiviazione di Azure Configurazione dell'account](images/AzureLabs-Lab7-3.png)

6.  Dopo aver fatto clic su **Crea**, sarà necessario attendere la creazione del servizio. L'operazione potrebbe richiedere un minuto.

7.  Una volta creata l'istanza del servizio, nel portale verrà visualizzata una notifica.

    ![Archiviazione di Azure Configurazione dell'account](images/AzureLabs-Lab7-4.png)

## <a name="chapter-2---the-azure-machine-learning-studio--classic"></a>Capitolo 2 - The Azure Machine Learning Studio (versione classica)

Per usare il *Azure Machine Learning*, è necessario configurare un'istanza del servizio Machine Learning in modo che sia disponibile per l'applicazione.

1.  Nel portale di Azure fare clic su **Nuovo** nell'angolo in alto a sinistra e cercare Machine Learning Studio Workspace (Area di lavoro **di Studio)** e premere **INVIO.**

    ![Azure Machine Learning Studio (versione classica)](images/AzureLabs-Lab7-5.png)

2.  La nuova pagina fornirà una descrizione del servizio dell'area **Machine Learning Studio.** Nella parte inferiore sinistra del prompt fare clic sul **pulsante Crea** per creare un'associazione con questo servizio.

3.  Dopo aver fatto clic su **Crea,** verrà visualizzato un pannello in cui è necessario fornire alcuni dettagli sul **nuovo servizio Machine Learning Studio:**

    1.  Inserire il nome **dell'area di lavoro desiderato** per questa istanza del servizio.

    2.  Selezionare una **Sottoscrizione**.

    3. Scegliere un **gruppo di risorse** o crearne uno nuovo. Un gruppo di risorse consente di monitorare, controllare l'accesso, effettuare il provisioning e gestire la fatturazione per una raccolta di asset di Azure. È consigliabile mantenere tutti i servizi di Azure associati a un singolo progetto (ad esempio, questi lab) in un gruppo di risorse comune. 

        > Per altre informazioni sui gruppi di risorse di Azure, vedere [l'articolo sui gruppi di risorse.](/azure/azure-resource-manager/resource-group-portal)

    4.  Determinare **la località** per il gruppo di risorse (se si sta creando un nuovo gruppo di risorse). La posizione sarebbe idealmente nell'area in cui verrebbe eseguita l'applicazione. Alcuni asset di Azure sono disponibili solo in determinate aree. È consigliabile usare lo stesso gruppo di risorse usato per creare il Archiviazione di Azure nel capitolo precedente.

    5.  Per la sezione Archiviazione account, fare clic su Usa esistente **,** quindi fare clic sul menu a discesa e quindi fare clic **sull'account** **Archiviazione** creato nell'ultimo capitolo.

    6.  Selezionare il piano **tariffario dell'area** di lavoro appropriato dal menu a discesa.

    7.  Nella sezione **Piano di servizio Web** fare clic su **Crea** **nuovo,** quindi inserire un nome nel campo di testo.

    8.  Nella sezione **Piano tariffario del piano di** servizio Web selezionare il piano tariffario preferito. Un livello di test di sviluppo denominato **DEVTEST Standard** dovrebbe essere disponibile gratuitamente.

    9.  È anche necessario confermare di aver compreso i termini e le condizioni applicati al servizio.

    10. Fare clic su **Crea**.

        ![Azure Machine Learning Studio (versione classica)](images/AzureLabs-Lab7-6.png)

4.  Dopo aver fatto clic su **Crea**, sarà necessario attendere la creazione del servizio. L'operazione potrebbe richiedere un minuto.

5.  Una volta creata l'istanza del servizio, nel portale verrà visualizzata una notifica.

    ![Azure Machine Learning Studio (versione classica)](images/AzureLabs-Lab7-7.png)

6.  Fare clic sulla notifica per esplorare la nuova istanza del servizio.

    ![Azure Machine Learning Studio (versione classica)](images/AzureLabs-Lab7-8.png)

7.  Fare clic **sul pulsante Vai alla** risorsa nella notifica per esplorare la nuova istanza del servizio.

8.  Nella pagina visualizzata, nella  sezione Collegamenti aggiuntivi, fare clic su Avvia **Machine Learning Studio** per indirizzare il browser al portale di **Machine Learning Studio.**

    ![Azure Machine Learning Studio (versione classica)](images/AzureLabs-Lab7-9.png)

9.  Usare il **pulsante Accedi** in alto a destra o al centro per accedere a Machine Learning Studio (versione classica).

    ![Azure Machine Learning Studio (versione classica)](images/AzureLabs-Lab7-10.png)


## <a name="chapter-3---the-machine-learning-studio-classic-dataset-setup"></a>Capitolo 3 - The Machine Learning Studio (versione classica): Configurazione del set di dati

Uno dei modi in Machine Learning algoritmi è l'analisi dei dati esistenti e quindi il tentativo di stimare i risultati futuri in base al set di dati esistente. Ciò significa in genere che maggiore è il numero di dati esistenti, migliore sarà la stima dei risultati futuri da parte dell'algoritmo.

Per questo corso viene fornita una tabella di esempio denominata [ProductsTableCSV e può essere scaricata qui.](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20307%20-%20Machine%20learning/MR%20and%20Azure%20307%20-%20Machine%20learning.zip)

> [!IMPORTANT]
> Il file .zip contiene sia **ProductsTableCSV** che **unitypackage,** necessari nel [capitolo 6.](#chapter-6---importing-the-mlproducts-unity-package) Questo pacchetto viene fornito anche all'interno del capitolo, anche se separato dal file CSV.

Questo set di dati di esempio contiene un record degli oggetti più venduti ogni ora di ogni giorno dell'anno 2017.
        
![The Machine Learning Studio (classic): Dataset setup (Configurazione del set di dati)](images/AzureLabs-Lab7-11.png)

Ad esempio, il giorno 1 del 2017, alle 13 (ora 13), l'articolo più venduto era salt e pepper.

Questa tabella di esempio contiene 9998 voci.

1.  Tornare al portale **di Machine Learning Studio (versione classica)** e aggiungere questa tabella come **set** di dati per il ML. A tale scopo, fare **clic sul pulsante +** Nuovo nell'angolo inferiore sinistro della schermata.

    ![The Machine Learning Studio (classic): Dataset setup (Configurazione del set di dati)](images/AzureLabs-Lab7-12.png)

2.  Una sezione verrà in alto dal basso e al suo interno è presente il pannello di spostamento a sinistra. Fare **clic su Set** di dati , quindi a destra di tale file, Da file **locale**.

    ![The Machine Learning Studio (classic): Dataset setup (Configurazione del set di dati)](images/AzureLabs-Lab7-13.png)

3.  Upload il nuovo **set di dati** seguendo questa procedura:

    1. Verrà visualizzata la finestra di caricamento, in cui è possibile **cercare** il nuovo set di dati nel disco rigido.

        ![The Machine Learning Studio (classic): Dataset setup (Configurazione del set di dati)](images/AzureLabs-Lab7-14.png)

    2.  Dopo aver selezionato e di nuovo nella finestra di caricamento, lasciare deselezionata la casella di controllo.

    3.  Nel campo di testo seguente immettere **ProductsTableCSV.csv** come nome per il set di dati (anche se deve essere aggiunto automaticamente).

    4.  Usando il menu a discesa **tipo**, selezionare **File CSV generico con un'intestazione (.csv).**

    5.  Premere il segno di spunta in basso a destra nella finestra di caricamento per caricare **il** set di dati.

## <a name="chapter-4---the-machine-learning-studio-classic-the-experiment"></a>Capitolo 4 - The Machine Learning Studio (versione classica): The Experiment

Prima di poter compilare il sistema di Machine Learning, è necessario creare un esperimento per convalidare la teoria sui dati. Con i risultati, si saprà se sono necessari più dati o se non esiste alcuna correlazione tra i dati e un possibile risultato.

Per iniziare a creare un esperimento:

1.  Fare di nuovo clic sul **pulsante + Nuovo** nella parte inferiore sinistra della pagina, quindi fare clic su Experiment Blank Experiment **(Esperimento**  >  **vuoto esperimento).**

    ![The Machine Learning Studio (classic): The Experiment](images/AzureLabs-Lab7-15.png)

2.  Verrà visualizzata una nuova pagina con un esperimento vuoto:

3.  Dal pannello a sinistra espandere **Saved Datasets** My Datasets (Set di dati salvati My Datasets) e trascinare  >   **ProductsTableCSV** nell'area **di disegno dell'esperimento.**

    ![The Machine Learning Studio (classic): The Experiment](images/AzureLabs-Lab7-16.png)

4.  Nel pannello a sinistra espandere **Esempio di trasformazione** dati e  >  **Dividi.** Trascinare quindi **l'elemento Split Data (Dividi** dati) in **nell'area di disegno dell'esperimento.** L'elemento Split Data (Dividi dati) suddividerà il set di dati in due parti. Una parte che verrà utilizzata per il training dell'algoritmo di Machine Learning. La seconda parte verrà usata per valutare l'accuratezza dell'algoritmo generato.

    ![The Machine Learning Studio (classic): The Experiment](images/AzureLabs-Lab7-17.png)

5.  Nel pannello destro (mentre l'elemento Split Data (Dividi dati) nell'area di disegno è selezionato, modificare Fraction of rows in the first output dataset (Frazione di righe nel primo set di dati di **output)** su **0,7.** I dati verranno suddivisi in due parti, la prima sarà il 70% dei dati e la seconda sarà il restante 30%. Per assicurarsi che i dati siano suddivisi in modo casuale, assicurarsi che la **casella di controllo Suddivisione** casuale rimanga selezionata.

    ![The Machine Learning Studio (classic): The Experiment](images/AzureLabs-Lab7-18.png)

6.  Trascinare una connessione dalla base **dell'elemento ProductsTableCSV** nell'area di disegno nella parte superiore dell'elemento Split Data . In questo modo si connetteranno gli elementi e si invierà l'output del set di dati **ProductsTableCSV** (i dati) all'input Split Data (Dividi dati).  

    ![The Machine Learning Studio (classic): The Experiment](images/AzureLabs-Lab7-19.png)

7.  Nel pannello **Experiments (Esperimenti)** a sinistra espandere **Machine Learning**  >  **Train (Training).** Trascinare **l'elemento Train Model** (Training modello) nell'area di disegno Experiment (Esperimento). L'area di disegno dovrebbe essere simile alla seguente.

    ![The Machine Learning Studio (classic): The Experiment](images/AzureLabs-Lab7-20.png)

8.  Dall'elemento ***in basso** a sinistra _ dell'elemento _ *Dividi* dati * trascinare una connessione nella parte **superiore destra** dell'elemento Train **Model (Training** modello). La prima suddivisione del 70% dal set di dati verrà usata dal modello di training per eseguire il training dell'algoritmo.

    ![The Machine Learning Studio (classic): The Experiment](images/AzureLabs-Lab7-21.png)

9.  Selezionare **l'elemento Train Model** (Training modello) nell'area di disegno e nel pannello **Proprietà** (sul lato destro della finestra del browser) fare clic sul pulsante Launch column selector (Avvia **selettore di** colonna).

10. Nella casella di testo digitare **product** e quindi premere **INVIO.** Il *prodotto* verrà impostato come colonna per il training delle stime. A questo punto, fare clic sul **segno di spunta** nell'angolo inferiore destro per chiudere la finestra di dialogo di selezione.

    ![The Machine Learning Studio (classic): The Experiment](images/AzureLabs-Lab7-22.png)

11. Si sta per eseguire il training di un  algoritmo di regressione logistica **multiclasse** per stimare il prodotto più venduto in base all'ora del giorno e alla data. Essula dall'ambito di questo documento per spiegare i dettagli dei diversi algoritmi forniti da Azure Machine Learning Studio. Per altre informazioni, vedere la scheda di Machine Learning [Algorithm Cheat (Informazioni](/azure/machine-learning/studio/algorithm-cheat-sheet) di base sull'algoritmo di Machine Learning)

12. Dal pannello degli elementi dell'esperimento a sinistra espandere Machine Learning Initialize Model Classification **(Inizializza** classificazione modello) e trascinare l'elemento  >    >   **Multiclass Logistic Regression (Regressione** logistica multiclasse) nell'area di disegno dell'esperimento.

13. Connessione'output, dalla parte inferiore della regressione logistica **multiclasse,** all'input in alto a sinistra dell'elemento **Train Model.**

    ![The Machine Learning Studio (classic): The Experiment](images/AzureLabs-Lab7-23.png)

14. Nell'elenco degli elementi dell'esperimento nel pannello a sinistra **espandere** Machine Learning Score (Punteggio) e trascinare l'elemento Score Model (Punteggio  >  modello) nell'area di disegno. 

15. Connessione'output, dalla parte inferiore di Train Model (Training **modello),** all'input in alto a sinistra di **Score Model (Punteggio modello).**

16. Connessione'output in basso a destra da **Split Data (Dividi dati)** all'input in alto a destra dell'elemento **Score Model (Punteggio** modello).

    ![The Machine Learning Studio (classic): The Experiment](images/AzureLabs-Lab7-24.png)

17. Nell'elenco di **elementi Experiment** (Esperimento) nel pannello a sinistra **espandere** Machine Learning Evaluate (Valuta) e trascinare  >   **l'elemento Evaluate Model** (Valuta modello) nell'area di disegno.

18. Connessione l'output del modello **di** punteggio all'input in alto a sinistra di **Evaluate Model**.

    ![The Machine Learning Studio (classic): The Experiment](images/AzureLabs-Lab7-25.png)

19. È stato creato il primo Machine Learning esperimento. È ora possibile salvare ed eseguire l'esperimento. Nel menu nella parte inferiore della pagina fare clic sul pulsante **Salva** per salvare l'esperimento e quindi fare clic su **Esegui** per avviare l'esperimento.

    ![The Machine Learning Studio (classic): The Experiment](images/AzureLabs-Lab7-26.png)

20. È possibile visualizzare lo **stato** dell'esperimento in alto a destra nell'area di disegno. Attendere alcuni istanti per il completamento dell'esperimento.

    > Se si dispone di un set di dati di grandi dimensioni (reale), è probabile che l'esecuzione dell'esperimento possa richiedere ore.

    ![The Machine Learning Studio (classic): The Experiment](images/AzureLabs-Lab7-27.png)

21. Fare clic con il pulsante **destro del mouse** sull'elemento Evaluate Model (Valuta modello) nell'area di disegno e dal menu di scelta rapida passare il puntatore del mouse su Evaluation Results **(Risultati** valutazione), quindi **selezionare Visualize (Visualizza).**

    ![The Machine Learning Studio (classic): The Experiment](images/AzureLabs-Lab7-28.png)

22. Verranno visualizzati i risultati della valutazione che mostrano i risultati stimati rispetto ai risultati effettivi. Viene utilizzato il 30% del set di dati originale, suddiviso in precedenza, per la valutazione del modello. È possibile vedere che i risultati non sono ottimali, idealmente il numero più alto in ogni riga è l'elemento evidenziato nelle colonne.

    ![The Machine Learning Studio (classic): The Experiment](images/AzureLabs-Lab7-29.png)

23. Chiudere **l'oggetto Results.**

24. Per usare il modello di Machine Learning appena con training, è necessario esporlo come **servizio Web**. A tale scopo, fare clic sulla voce di menu Set Up Web Service (Configura servizio **Web)** nel menu nella parte inferiore della pagina e fare clic su **Predictive Web Service (Servizio Web predittivo).**

    ![The Machine Learning Studio (classic): The Experiment](images/AzureLabs-Lab7-30.png)

25. Verrà creata una nuova scheda e il modello di training verrà unito per creare il nuovo servizio Web. 

26. Nel menu nella parte inferiore della pagina fare clic su **Salva** e quindi su **Esegui.** Lo stato verrà aggiornato nell'angolo superiore destro dell'area di disegno dell'esperimento.

    ![The Machine Learning Studio (classic): The Experiment](images/AzureLabs-Lab7-31.png)

27. Al termine dell'esecuzione, nella parte inferiore della pagina verrà visualizzato il pulsante Deploy **Web Service** (Distribuisci servizio Web). Si è pronti per distribuire il servizio Web. Fare **clic su Distribuisci** servizio Web (versione classica) nel menu nella parte inferiore della pagina.

    ![The Machine Learning Studio (classic): The Experiment](images/AzureLabs-Lab7-32.png)

    > Il browser potrebbe richiedere di consentire un popup, che dovrebbe essere **consentito,** anche se potrebbe essere necessario premere di nuovo Deploy Web Service (Distribuisci servizio **Web),** se la pagina di distribuzione non viene visualizzata. 

28. Dopo aver creato l'esperimento, si verrà reindirizzati a una **pagina Dashboard** in cui sarà visualizzata la chiave **API.** Copiarlo in un Blocco note per il momento, perché sarà necessario nel codice molto presto. Dopo aver specificato la chiave API, fare clic sul pulsante **RICHIESTA/RISPOSTA** nella **sezione Endpoint** predefinito sotto la chiave.

    ![The Machine Learning Studio (classic): The Experiment](images/AzureLabs-Lab7-33.png)

    > [!NOTE] 
    > Se si fa clic su Test in questa pagina, sarà possibile immettere i dati di input e visualizzare l'output. Immettere il **giorno e** **l'ora**. Lasciare vuota **la voce** del prodotto. Fare quindi clic sul **pulsante** Conferma. L'output nella parte inferiore della pagina mostrerà il codice JSON che rappresenta la probabilità che ogni prodotto sia la scelta desiderata.

29. Si aprirà una nuova pagina Web, che visualizza le istruzioni e alcuni esempi sulla struttura della richiesta richiesta da Machine Learning Studio (versione classica). Copiare **l'URI** della richiesta visualizzato in questa pagina nel Blocco note.

    ![The Machine Learning Studio (classic): The Experiment](images/AzureLabs-Lab7-34.png)

È stato creato un sistema di Machine Learning che fornisce il prodotto più probabile da vendere in base ai dati cronologici di acquisto, correlati all'ora del giorno e del giorno dell'anno.

Per chiamare il servizio Web, sono necessari l'URL per l'endpoint del servizio e una chiave API per il servizio. Fare clic sulla **scheda** Consume (Utilizzo) nel menu in alto.

Nella **pagina Informazioni** sul consumo verranno visualizzate le informazioni necessarie per chiamare il servizio Web dal codice. Copiare la chiave primaria **e l'URL** **richiesta-risposta.** Saranno necessari nel capitolo successivo.

## <a name="chapter-5---setting-up-the-unity-project"></a>Capitolo 5 - Configurazione del Project Unity

Configurare e testare il visore VR immersive di realtà mista.

> [!NOTE]
>  Per questo **corso non** saranno necessari controller del movimento. Se è necessario supporto per la configurazione del visore VR immersive, fare clic [qui.](https://support.microsoft.com/help/4043101/windows-10-set-up-windows-mixed-reality)

1.  Aprire **Unity** e creare un nuovo Project Unity **denominato MR \_ MachineLearning.** Assicurarsi che il tipo di progetto sia impostato su **3D.**

2.  Con Unity aperto, è opportuno controllare che l'editor di **script predefinito** sia impostato **su Visual Studio**. Passare a **Modifica**  >  **preferenze** e quindi dalla nuova finestra passare a **Strumenti esterni.** Modificare **External Script Editor in** Visual Studio **2017**. Chiudere la **finestra** Preferenze.

3.  Passare quindi a **File** Build Impostazioni e passare alla piattaforma Universal Windows Platform facendo clic sul pulsante Switch Platform (Cambia  >   piattaforma).  ****

4.  Assicurarsi anche che:

    1.  **Dispositivo di destinazione** è impostato su **Qualsiasi dispositivo.**

        > Per il Microsoft HoloLens, impostare **Dispositivo di destinazione** su *HoloLens*.

    2.  **Il tipo di** compilazione è impostato **su D3D.**

    3.  **L'SDK** è impostato su **Più recente installato.**

    4.  **Visual Studio è impostata** su **Versione più recente installata.**

    5.  **Build and Run (Compilazione** ed esecuzione) è **impostato su Local Machine (Computer locale).**

    6.  Non preoccuparsi di configurare Scenes in **questo** momento, perché vengono fornite in un secondo momento.

    7.  Per il momento, le impostazioni rimanenti dovrebbero rimanere come predefinite.

        ![Configurazione del Project Unity](images/AzureLabs-Lab7-35.png)

5.  Nella finestra **build Impostazioni** fare clic sul pulsante **Player Impostazioni** per aprire il pannello correlato nello spazio in cui si trova **il controllo.** 

6. In questo pannello è necessario verificare alcune impostazioni:

    1.  Nella scheda **Altro Impostazioni:**

        1.  **La versione** **del runtime di** scripting deve essere **sperimentale** (equivalente a .NET 4.6)

        2. **Il back-end di** scripting deve **_essere .NET_**

        3. **Il livello di compatibilità dell'API** **deve essere .NET 4.6**

            ![Configurazione del Project Unity](images/AzureLabs-Lab7-36.png)

    2.  **All'interno della Impostazioni** pubblicazione, in **Funzionalità** selezionare:

        - **InternetClient**

            ![Configurazione del Project Unity](images/AzureLabs-Lab7-37.png)

    3.  Più in basso nel pannello, in **XR Impostazioni** (disponibile sotto **Pubblica Impostazioni),** selezionare **Virtual Reality Supported**(Realtà virtuale supportata) e assicurarsi che sia stato aggiunto **Windows Mixed Reality SDK**

        ![Configurazione del Project Unity](images/AzureLabs-Lab7-38.png)

    

6.  Tornare alla **compilazione Impostazioni** i *progetti C# Unity* non sono più disattivati; Selezionare la casella di controllo accanto a questo. 

7.  Chiudere la finestra Build Settings (Impostazioni di compilazione).

8.  Salvare il Project (**FILE > SAVE PROJECT**).

## <a name="chapter-6---importing-the-mlproducts-unity-package"></a>Capitolo 6 - Importazione del pacchetto Unity MLProducts

Per questo corso, è necessario scaricare un pacchetto di asset Unity denominato [**Azure-MR-307.unitypackage.**](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20307%20-%20Machine%20learning/307-Scene-Setup.unitypackage) Questo pacchetto è completo di una scena, con tutti gli oggetti in tale precompilato, in modo da potersi concentrare sul funzionamento. Lo script **ShelfKeeper** viene fornito, anche se contiene solo le variabili pubbliche, ai fini della struttura di configurazione della scena. È necessario eseguire tutte le altre sezioni. 

Per importare questo pacchetto:

1.  Con il dashboard di Unity davanti all'utente, fare clic su **Assets (Asset)** nel menu nella parte superiore della schermata, quindi fare clic su **Import Package (Importa pacchetto), Custom Package (Pacchetto personalizzato).**

    ![Importazione del pacchetto Unity MLProducts](images/AzureLabs-Lab7-39.png)

2.  Usare la selezione file per selezionare il **pacchetto Azure-MR-307.unitypackage** e fare clic su **Apri.**

3.  Verrà visualizzato un elenco di componenti per questo asset. Confermare l'importazione facendo clic **su Importa.**

    ![Importazione del pacchetto Unity MLProducts](images/AzureLabs-Lab7-40.png)

4.  Al termine dell'importazione, si noterà che nel pannello di Project Unity **sono state Project nuove cartelle.** Si tratta dei modelli 3D e dei rispettivi materiali che fanno parte della scena pre-realizzata su cui si lavora. In questo corso si scriverà la maggior parte del codice.

    ![Importazione del pacchetto Unity MLProducts](images/AzureLabs-Lab7-41.png)

5.  Nella cartella **Project fare** clic sulla cartella **Scenes (Scene)** e fare doppio clic sulla scena all'interno **di (denominata MR_MachineLearningScene**). La scena verrà aperta (vedere l'immagine seguente). Se mancano i rombi rossi, è sufficiente fare clic sul **pulsante Gizmos** in alto a destra nel **pannello del gioco.**

    ![Importazione del pacchetto Unity MLProducts](images/AzureLabs-Lab7-44.png)

## <a name="chapter-7---checking-the-dlls-in-unity"></a>Capitolo 7 - Controllo delle DLL in Unity

Per sfruttare l'uso delle librerie JSON (usate per la serializzazione e la deserializzazione), è stata implementata una DLL Newtonsoft con il pacchetto che è stato creato. La libreria deve avere la configurazione corretta, anche se vale la pena controllarla, in particolare se si verificano problemi con il codice che non funziona. 

A tale scopo, procedere nel seguente modo:

-  Fare clic con il pulsante sinistro del mouse sul file Newtonsoft all'interno della cartella Plugins (Plug-in) ed esaminare il **pannello Inspector (Controllo).** Assicurarsi che **l'opzione Any Platform** (Qualsiasi piattaforma) sia selezionata. Passare alla **scheda UWP e** assicurarsi anche che **l'opzione Non elaborare** sia selezionata.

    ![Importazione delle DLL in Unity](images/AzureLabs-Lab7-48.png)

## <a name="chapter-8---create-the-shelfkeeper-class"></a>Capitolo 8 - Creare la classe ShelfKeeper

La **classe ShelfKeeper** ospita metodi che controllano l'interfaccia utente e i prodotti generati nella scena.

Come parte del pacchetto importato, questa classe sarà stata specificata, anche se è incompleta. È ora possibile completare la classe:

1.  Fare doppio clic sullo script **ShelfKeeper,** all'interno **della cartella Scripts,** per aprirlo **con Visual Studio 2017.**

2.  Sostituire tutto il codice esistente nello script con il codice seguente, che imposta l'ora e la data e dispone di un metodo per visualizzare un prodotto.

    ```csharp
    using UnityEngine;

    public class ShelfKeeper : MonoBehaviour
    {
        /// <summary>
        /// Provides this class Singleton-like behavior
        /// </summary>
        public static ShelfKeeper instance;

        /// <summary>
        /// Unity Inspector accessible Reference to the Text Mesh object needed for data
        /// </summary>
        public TextMesh dateText;

        /// <summary>
        /// Unity Inspector accessible Reference to the Text Mesh object needed for time
        /// </summary>
        public TextMesh timeText;

        /// <summary>
        /// Provides references to the spawn locations for the products prefabs
        /// </summary>
        public Transform[] spawnPoint;

        private void Awake()
        {
            instance = this;
        }

        /// <summary>
        /// Set the text of the date in the scene
        /// </summary>
        public void SetDate(string day, string month)
        {
            dateText.text = day + " " + month;
        }

        /// <summary>
        /// Set the text of the time in the scene
        /// </summary>
        public void SetTime(string hour)
        {
            timeText.text = hour + ":00";
        }

        /// <summary>
        /// Spawn a product on the shelf by providing the name and selling grade
        /// </summary>
        /// <param name="name"></param>
        /// <param name="sellingGrade">0 being the best seller</param>
        public void SpawnProduct(string name, int sellingGrade)
        {
            Instantiate(Resources.Load(name),
                spawnPoint[sellingGrade].transform.position, spawnPoint[sellingGrade].transform.rotation);
        }
    }
    ```

3.  Assicurarsi di salvare le modifiche in **Visual Studio** prima di tornare a **Unity.**

4.  Nell'editor di Unity verificare che la **classe ShelfKeeper** sia simile alla seguente:

    ![Creare la classe ShelfKeeper](images/AzureLabs-Lab7-51.png)

    > [!IMPORTANT]
    > Se lo script non ha le destinazioni di riferimento ,ad esempio *Date (Text Mesh),* è sufficiente trascinare gli oggetti corrispondenti dal pannello **Hierarchy**(Gerarchia) nei campi di destinazione. Vedere di seguito per una spiegazione, se necessario:
    > 
    > 1.  Aprire la **matrice Spawn Point** nello script del componente **ShelfKeeper** facendo clic con il pulsante sinistro del mouse. Verrà visualizzata una sottosezioni denominata **Size**, che indica le dimensioni della matrice. Digitare **3** nella casella di testo accanto a **Dimensioni** e premere **INVIO** e verranno creati tre slot sotto.
    > 2. **All'interno della gerarchia** espandere **l'oggetto Time Display** (Visualizzazione ora) facendo clic sulla freccia accanto a esso. Fare quindi clic **_sulla fotocamera principale_ _ *dall'interno di _* Hierarchy**, in modo che il **controllo** visualizza le relative informazioni.
    > 3. Selezionare la **fotocamera principale** nel pannello **Gerarchia**. Trascinare **gli oggetti** Data  **e** Ora  dal pannello Gerarchia negli  **slot**  Testo data e Testo ora all'interno del controllo della fotocamera principale nel componente **ShelfKeeper.**
    > 4. Trascinare **i punti di generazione** dal pannello **Gerarchia** (sotto l'oggetto *Shelf)* alle destinazioni di riferimento a **3**  elementi sotto la matrice **Spawn Point,** come illustrato nell'immagine.
    > 
    >     ![Creare la classe ShelfKeeper](images/AzureLabs-Lab7-52.png)

## <a name="chapter-9---create-the-productprediction-class"></a>Capitolo 9- Creare la classe ProductPrediction

La classe successiva che si creerà è **la classe ProductPrediction.**

Questa classe è responsabile di:

-   Esecuzione di query **sull Machine Learning service,** specificando la data e l'ora correnti.

-   Deserializzazione della risposta JSON in dati utilizzabili.

-   Interpretazione dei dati, recupero dei 3 prodotti consigliati.

-   Chiamata dei **metodi della classe ShelfKeeper** per visualizzare i dati nella scena.

Per creare questa classe:

1.  Passare alla cartella **Scripts** (Script) nel **pannello Project .**

2.  Fare clic con il pulsante destro del mouse **all'interno della** cartella Crea  >  **script C#.** Chiamare lo script **ProductPrediction**.

3.  Fare doppio clic sul nuovo script **ProductPrediction** per aprirlo con **Visual Studio 2017.**

4.  Se viene **visualizzata la finestra di dialogo Rilevata** modifica file, fare clic su * Ricarica *_soluzione_*.

5.  Aggiungere gli spazi dei nomi seguenti all'inizio della classe ProductPrediction:

    ```csharp
    using System;
    using System.Collections.Generic;
    using UnityEngine;
    using System.Linq;
    using Newtonsoft.Json;
    using UnityEngine.Networking;
    using System.Runtime.Serialization;
    using System.Collections;
    ```

6.  **All'interno della classe ProductPrediction** inserire i due oggetti seguenti, costituiti da una serie di classi annidate. Queste classi vengono usate per serializzare e deserializzare il codice JSON per il Machine Learning Service.

    ```csharp
        /// <summary>
        /// This object represents the Prediction request
        /// It host the day of the year and hour of the day
        /// The product must be left blank when serialising
        /// </summary>
        public class RootObject
        {
            public Inputs Inputs { get; set; }
        }

        public class Inputs
        {
            public Input1 input1 { get; set; }
        }

        public class Input1
        {
            public List<string> ColumnNames { get; set; }
            public List<List<string>> Values { get; set; }
        }
    ```

    ```csharp
        /// <summary>
        /// This object containing the deserialised Prediction result
        /// It host the list of the products
        /// and the likelihood of them being sold at current date and time
        /// </summary>
        public class Prediction
        {
            public Results Results { get; set; }
        }

        public class Results
        {
            public Output1 output1;
        }

        public class Output1
        {
            public string type;
            public Value value;
        }

        public class Value
        {
            public List<string> ColumnNames { get; set; }
            public List<List<string>> Values { get; set; }
        }
    ```

7.  Aggiungere quindi le variabili seguenti sopra il codice precedente (in modo che il codice correlato a JSON si trova nella parte inferiore dello script, sotto tutto il codice e fuori procedura):

    ```csharp
        /// <summary>
        /// The 'Primary Key' from your Machine Learning Portal
        /// </summary>
        private string authKey = "-- Insert your service authentication key here --";

        /// <summary>
        /// The 'Request-Response' Service Endpoint from your Machine Learning Portal
        /// </summary>
        private string serviceEndpoint = "-- Insert your service endpoint here --";

        /// <summary>
        /// The Hour as set in Windows
        /// </summary>
        private string thisHour;

        /// <summary>
        /// The Day, as set in Windows
        /// </summary>
        private string thisDay;

        /// <summary>
        /// The Month, as set in Windows
        /// </summary>
        private string thisMonth;

        /// <summary>
        /// The Numeric Day from current Date Conversion
        /// </summary>
        private string dayOfTheYear;

        /// <summary>
        /// Dictionary for holding the first (or default) provided prediction 
        /// from the Machine Learning Experiment
        /// </summary>    
        private Dictionary<string, string> predictionDictionary;

        /// <summary>
        /// List for holding product prediction with name and scores
        /// </summary>
        private List<KeyValuePair<string, double>> keyValueList;
    ```

    > [!IMPORTANT]
    > Assicurarsi di inserire la chiave **primaria e** **l'endpoint di richiesta-risposta,** dal portale Machine Learning, nelle variabili qui. Le immagini seguenti mostrano da dove si sarebbero presi la chiave e l'endpoint. 
    >  
    > ![The Machine Learning Studio (versione classica): l'esperimento](images/AzureLabs-Lab7-53-1.png)
    >
    > ![The Machine Learning Studio (versione classica): l'esperimento](images/AzureLabs-Lab7-53-2.png)

8.  Inserire questo codice nel **metodo Start().** Il **metodo Start()** viene chiamato quando la classe viene inizializzata:

    ```csharp
        void Start()
        {
            // Call to get the current date and time as set in Windows
            GetTodayDateAndTime();

            // Call to set the HOUR in the UI
            ShelfKeeper.instance.SetTime(thisHour);

            // Call to set the DATE in the UI
            ShelfKeeper.instance.SetDate(thisDay, thisMonth);

            // Run the method to Get Predication from Azure Machine Learning
            StartCoroutine(GetPrediction(thisHour, dayOfTheYear));
        }
    ```

9.  Di seguito è riportato il metodo che raccoglie la data e l'ora dal Windows e la converte in un formato che l'esperimento Machine Learning può usare per confrontare con i dati archiviati nella tabella.

    ```csharp
        /// <summary>
        /// Get current date and hour
        /// </summary>
        private void GetTodayDateAndTime()
        {
            // Get today date and time
            DateTime todayDate = DateTime.Now;

            // Extrapolate the HOUR
            thisHour = todayDate.Hour.ToString();

            // Extrapolate the DATE
            thisDay = todayDate.Day.ToString();
            thisMonth = todayDate.ToString("MMM");

            // Extrapolate the day of the year
            dayOfTheYear = todayDate.DayOfYear.ToString();
        }
    ```

10. È possibile **eliminare** il **metodo Update()** perché questa classe non lo userà.

11. Aggiungere il metodo seguente che comunicherà la data e l'ora correnti all'endpoint Machine Learning e riceverà una risposta in formato JSON.

    ```csharp
        private IEnumerator GetPrediction(string timeOfDay, string dayOfYear)
        {
            // Populate the request object 
            // Using current day of the year and hour of the day
            RootObject ro = new RootObject
            {
                Inputs = new Inputs
                {
                    input1 = new Input1
                    {
                        ColumnNames = new List<string>
                        {
                            "day",
                            "hour",
                        "product"
                        },
                        Values = new List<List<string>>()
                    }
                }
            };

            List<string> l = new List<string>
            {
                dayOfYear,
                timeOfDay,
                ""
            };

            ro.Inputs.input1.Values.Add(l);

            Debug.LogFormat("Score request built");

            // Serialize the request
            string json = JsonConvert.SerializeObject(ro);

            using (UnityWebRequest www = UnityWebRequest.Post(serviceEndpoint, "POST"))
            {
                byte[] jsonToSend = new System.Text.UTF8Encoding().GetBytes(json);
                www.uploadHandler = new UploadHandlerRaw(jsonToSend);

                www.downloadHandler = new DownloadHandlerBuffer();
                www.SetRequestHeader("Authorization", "Bearer " + authKey);
                www.SetRequestHeader("Content-Type", "application/json");
                www.SetRequestHeader("Accept", "application/json");

                yield return www.SendWebRequest();
                string response = www.downloadHandler.text;

                // Deserialize the response
                DataContractSerializer serializer;
                serializer = new DataContractSerializer(typeof(string));
                DeserialiseJsonResponse(response);
            }
        }
    ```

12. Aggiungere il metodo seguente, responsabile della deserializzazione della risposta JSON e della comunicazione del risultato della deserializzazione alla **classe ShelfKeeper.** Questo risultato sarà il nome dei tre elementi stimati per vendere di più alla data e all'ora correnti. Inserire il codice seguente nella **classe ProductPrediction,** sotto il metodo precedente.

    ```csharp
        /// <summary>
        /// Deserialize the response received from the Machine Learning portal
        /// </summary>
        public void DeserialiseJsonResponse(string jsonResponse)
        {
            // Deserialize JSON
            Prediction prediction = JsonConvert.DeserializeObject<Prediction>(jsonResponse);
            predictionDictionary = new Dictionary<string, string>();

            for (int i = 0; i < prediction.Results.output1.value.ColumnNames.Count; i++)
            {
                if (prediction.Results.output1.value.Values[0][i] != null)
                {
                    predictionDictionary.Add(prediction.Results.output1.value.ColumnNames[i], prediction.Results.output1.value.Values[0][i]);
                }
            }

            keyValueList = new List<KeyValuePair<string, double>>();

            // Strip all non-results, by adding only items of interest to the scoreList
            for (int i = 0; i < predictionDictionary.Count; i++)
            {
                KeyValuePair<string, string> pair = predictionDictionary.ElementAt(i);
                if (pair.Key.StartsWith("Scored Probabilities"))
                {
                    // Parse string as double then simplify the string key so to only have the item name
                    double scorefloat = 0f;
                    double.TryParse(pair.Value, out scorefloat);
                    string simplifiedName =
                        pair.Key.Replace("\"", "").Replace("Scored Probabilities for Class", "").Trim();
                    keyValueList.Add(new KeyValuePair<string, double>(simplifiedName, scorefloat));
                }
            }

            // Sort Predictions (results will be lowest to highest)
            keyValueList.Sort((x, y) => y.Value.CompareTo(x.Value));

            // Spawn the top three items, from the keyValueList, which we have sorted
            for (int i = 0; i < 3; i++)
            {
                ShelfKeeper.instance.SpawnProduct(keyValueList[i].Key, i);
            }

            // Clear lists in case of reuse
            keyValueList.Clear();
            predictionDictionary.Clear();
        }
    ```

13. Salvare **Visual Studio** e tornare a **Unity.**

14. Trascinare lo script **della classe ProductPrediction** dalla **cartella Script** nell'oggetto **Fotocamera** principale.

15. Salvare la scena e il **progetto File**  >  **Save Scene/File** Save  >  **Project**.

## <a name="chapter-10---build-the-uwp-solution"></a>Capitolo 10 - Creare la soluzione UWP

È ora possibile compilare il progetto come soluzione UWP, in modo che possa essere eseguito come applicazione autonoma.

Per compilare:

1.  Salvare la scena corrente facendo clic su **Salva**  >  **scene.**

2.  Passare a **File**  >  **Build Impostazioni**

3.  Selezionare la casella **Progetti C# di Unity** (questo è importante perché consentirà di modificare le classi dopo il completamento della compilazione).

4.  Fare clic **su Aggiungi scene aperte**,

5.  Fare clic su **Compila**.

    ![Compilare la soluzione UWP](images/AzureLabs-Lab7-54.png)

6.  Verrà richiesto di selezionare la cartella in cui si vuole compilare la soluzione.

7.  Creare una **cartella BUILDS** e all'interno di tale cartella creare un'altra cartella con un nome appropriato.

8.  Fare clic sulla nuova cartella e quindi su **Seleziona cartella** per iniziare la compilazione in tale percorso.

    ![Compilare la soluzione UWP](images/AzureLabs-Lab7-55.png)

    ![Compilare la soluzione UWP](images/AzureLabs-Lab7-56.png)

9.  Al termine della compilazione di Unity (potrebbe essere necessario del tempo), verrà aperta una finestra **Esplora file** nel percorso della compilazione (controllare la barra delle applicazioni, perché potrebbe non essere sempre visualizzata sopra le finestre, ma verrà notificata l'aggiunta di una nuova finestra).

## <a name="chapter-11---deploy-your-application"></a>Capitolo 11 - Distribuire l'applicazione

Per distribuire l'applicazione:

1.  Passare alla nuova build di Unity (cartella **App)** e aprire il file di soluzione con **Visual Studio**.

2.  Con Visual Studio aperto, è necessario ripristinare i pacchetti NuGet, che è possibile eseguire facendo clic con il pulsante destro del mouse sulla soluzione MachineLearningLab_Build, dal Esplora soluzioni (disponibile a destra di Visual Studio) e quindi scegliendo Ripristina pacchetti NuGet:

    ![Aggiungere pacchetti NuGet](images/AzureLabs-Lab7-57.png)

3.  In Configurazione soluzione selezionare **Debug**.

4.  In Piattaforma soluzione selezionare **x86**, **Computer locale**. 

    > Per il Microsoft HoloLens, potrebbe risultare più semplice impostare questa opzione su *Computer* remoto, in modo che non sia necessario eseguire il tethering al computer. Tuttavia, è necessario eseguire anche le operazioni seguenti:
    > - Conoscere **l'indirizzo IP** del HoloLens, disponibile nella Impostazioni > *Network & Internet > Wi-Fi > Opzioni avanzate*; IPv4 è l'indirizzo da usare. 
    > - Assicurarsi **che la modalità sviluppatore** sia **attivata.** disponibile in *Impostazioni > Update & Security > For developers*.

    ![Aggiungere pacchetti NuGet](images/AzureLabs-Lab7-58.png)

5.  Passare al **menu Compila e** fare clic su **Distribuisci soluzione** per eseguire il sideload dell'applicazione nel PC.

6.  L'app dovrebbe ora essere visualizzata nell'elenco delle app installate, pronte per l'avvio.

Quando si esegue l'applicazione Mixed Reality, verrà visualizzato il banco configurato nella scena unity e dall'inizializzazione verranno recuperati i dati impostati in Azure. I dati verranno deserializzati all'interno dell'applicazione e i tre risultati principali per la data e l'ora correnti verranno forniti visivamente, come tre modelli in panchina.


## <a name="your-finished-machine-learning-application"></a>L'applicazione Machine Learning completata
 
È stata creata un'app di realtà mista che sfrutta Azure Machine Learning per eseguire stime dei dati e visualizzarle nella scena.

![Aggiungere pacchetti NuGet](images/AzureLabs-Lab7-0.png)

## <a name="exercise"></a>Esercizio

**Esercizio 1**

Provare a usare l'ordinamento dell'applicazione e fare in modo che le tre stime più in basso vengano visualizzate sullo scaffale, perché anche questi dati potrebbero essere utili.

**Esercizio 2**

**L'uso di Tabelle** di Azure popola una nuova tabella con informazioni meteo e crea un nuovo esperimento usando i dati.
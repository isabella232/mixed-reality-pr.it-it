---
title: HoloLens (prima generazione) e Azure 310 - Rilevamento oggetti
description: Completare questo corso per informazioni su come eseguire il training e usare un modello di Machine Learning per riconoscere oggetti simili e la relativa posizione nel mondo reale.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure, visione personalizzata, rilevamento di oggetti, realtà mista, academy, unity, tutorial, api, hololens, Windows 10, Visual Studio
ms.openlocfilehash: 85a99b676f6765696524bc42adf257b3430c00cc955413b4c299ddb58502cefb
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115216653"
---
# <a name="hololens-1st-gen-and-azure-310-object-detection"></a>HoloLens (prima generazione) e Azure 310: Rilevamento oggetti

>[!NOTE]
>Le esercitazioni di Mixed Reality Academy sono state progettate in base a HoloLens (prima generazione) e ai visori VR immersive di realtà mista.  Pertanto, riteniamo importante lasciarle a disposizione degli sviluppatori a cui serve ancora materiale sussidiario per lo sviluppo di questi dispositivi.  Queste esercitazioni **_non_** verranno aggiornate con i set di strumenti o le interazioni più recenti usati per HoloLens 2.  Rimarranno invariate per consentire di continuare a lavorare sui dispositivi supportati. In futuro verrà pubblicata una nuova serie di esercitazioni che illustrano come sviluppare per HoloLens 2.  Questa informativa verrà aggiornata con un collegamento a tali esercitazioni al momento della pubblicazione.

<br>

In questo corso si apprenderà come riconoscere il contenuto visivo personalizzato e la relativa posizione spaziale all'interno di un'immagine fornita, usando le funzionalità "Rilevamento oggetti" di Azure Visione personalizzata in un'applicazione di realtà mista.

Questo servizio consente di eseguire il training di un modello di Machine Learning usando immagini oggetto. Si userà quindi il modello con training per riconoscere oggetti simili e approssimarne la posizione nel mondo reale, come fornito dall'acquisizione della fotocamera di Microsoft HoloLens o da una fotocamera che si connette a un PC per visori VR immersive.

![risultato del corso](images/AzureLabs-Lab310-00.png)

**Azure Visione personalizzata, Il rilevamento oggetti è** un servizio Microsoft che consente agli sviluppatori di creare classificatori di immagini personalizzati. Questi classificatori possono quindi essere usati con nuove immagini per rilevare gli oggetti all'interno della nuova immagine, fornendo limiti box **all'interno** dell'immagine stessa. Il servizio offre un portale online semplice, facile da usare per semplificare questo processo. Per altre informazioni, visitare i collegamenti seguenti:

* [Pagina Visione personalizzata azure](/azure/cognitive-services/custom-vision-service/home)
* [Limiti e quote](/azure/cognitive-services/custom-vision-service/limits-and-quotas)

Al termine di questo corso, si avrà un'applicazione di realtà mista che sarà in grado di eseguire le operazioni seguenti:

1. L'utente sarà in grado *di* osservare un oggetto di cui è stato creato il training usando il servizio Azure Visione personalizzata, Rilevamento oggetti. 
2. L'utente userà il *movimento Tocco* per acquisire un'immagine di ciò che sta osservando.
3. L'app invierà l'immagine al servizio Visione personalizzata Azure.
4. Verrà visualizzata una risposta dal servizio che visualizza il risultato del riconoscimento come testo spazio mondiale. Questa operazione verrà eseguita usando il rilevamento spaziale del Microsoft HoloLens, per comprendere la posizione mondiale dell'oggetto riconosciuto e quindi usando il *tag* associato a ciò che viene rilevato nell'immagine, per fornire il testo dell'etichetta.

Il corso illustra anche il caricamento manuale delle immagini, la creazione di tag e il training del servizio, per riconoscere oggetti diversi (nell'esempio fornito, una tazza), impostando la *casella* limite all'interno dell'immagine che si invia. 

> [!IMPORTANT]
> Dopo la creazione e l'uso dell'app, lo sviluppatore deve tornare al servizio Azure Visione personalizzata e identificare le stime effettuate dal servizio e determinare se sono corrette o meno (contrassegnando qualsiasi elemento che il servizio ha perso e modificando i recinti di *delimitazione).* È quindi possibile eseguire nuovamente il training del servizio, che aumenta la probabilità che riconosca gli oggetti reali.

Questo corso illustra come ottenere i risultati dal servizio Azure Visione personalizzata, Rilevamento oggetti, in un'applicazione di esempio basata su Unity. Sarà necessario applicare questi concetti a un'applicazione personalizzata che potrebbe essere compilata.

## <a name="device-support"></a>Supporto di dispositivi

<table>
<tr>
<th>Corso</th><th style="width:150px"> <a href="/hololens/hololens1-hardware">HoloLens</a></th><th style="width:150px"> <a href="../../../discover/immersive-headset-hardware-details.md">Visori VR immersive</a></th>
</tr><tr>
<td> MR e Azure 310: Rilevamento di oggetti</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="prerequisites"></a>Prerequisiti

> [!NOTE]
> Questa esercitazione è progettata per sviluppatori con esperienza di base con Unity e C#. Tenere inoltre presente che i prerequisiti e le istruzioni scritte all'interno di questo documento rappresentano ciò che è stato testato e verificato al momento della scrittura (luglio 2018). È possibile usare il software più recente, come elencato nell'articolo Installare gli strumenti, anche se non si deve presumere che le informazioni in questo corso corrispondano perfettamente a quelle disponibili nel software più recente rispetto a quelle elencate di seguito. [](../../install-the-tools.md)

Per questo corso è consigliabile usare l'hardware e il software seguenti:

- Un PC di sviluppo
- [Windows 10 Fall Creators Update (o versione successiva) con la modalità sviluppatore abilitata](/windows/mixed-reality/install-the-tools#installation-checklist-for-hololens)
- [L'SDK Windows 10 più recente](/windows/mixed-reality/install-the-tools#installation-checklist-for-hololens)
- [Unity 2017.4 LTS](/windows/mixed-reality/install-the-tools#installation-checklist-for-hololens)
- [Visual Studio 2017](/windows/mixed-reality/install-the-tools#installation-checklist-for-hololens)
- Un [Microsoft HoloLens](/windows/mixed-reality/hololens-hardware-details) con la modalità sviluppatore abilitata
- Accesso a Internet per l'installazione di Azure e il Visione personalizzata del servizio
-  È necessaria una serie di almeno quindici (15) immagini) per ogni oggetto che si Visione personalizzata riconoscere. Se lo si desidera, è possibile usare le immagini già fornite con questo corso, [una serie di tazze](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Cup%20Images.zip).

## <a name="before-you-start"></a>Prima di iniziare

1.  Per evitare problemi durante la compilazione di questo progetto, è consigliabile creare il progetto indicato in questa esercitazione in una cartella radice o quasi radice (i percorsi di cartelle lunghe possono causare problemi in fase di compilazione).
2.  Configurare e testare il HoloLens. Se è necessario supporto per la configurazione del HoloLens, visitare l'articolo HoloLens [setup .](/hololens/hololens-setup) 
3.  È buona idea eseguire calibrazione e ottimizzazione dei sensori quando si inizia a sviluppare una nuova app HoloLens (talvolta può essere utile per eseguire queste attività per ogni utente). 

Per informazioni sulla calibrazione, seguire questo [collegamento all'HoloLens calibrazione.](/hololens/hololens-calibration#hololens-2)

Per informazioni sull'ottimizzazione dei sensori, seguire questo [collegamento all'articolo HoloLens Sensor Tuning](/hololens/hololens-updates).

## <a name="chapter-1---the-custom-vision-portal"></a>Capitolo 1 - Portale Visione personalizzata

Per usare **il servizio Azure Visione personalizzata**, è necessario configurare un'istanza di per essere resa disponibile per l'applicazione.

1.  Passare [alla pagina principale Visione personalizzata **Service**](https://azure.microsoft.com/services/cognitive-services/custom-vision-service/).

2.  Fare clic su **Attività iniziali**.

    ![](images/AzureLabs-Lab310-01.png)

3.  Accedere al portale Visione personalizzata.

    ![](images/AzureLabs-Lab310-02.png)

4.  Se non si dispone già di un account Azure, è necessario crearne uno. Se si sta seguendo questa esercitazione in una situazione di classe o di lab, chiedere all'insegnante o a uno dei prottori di assistenza per la configurazione del nuovo account.

5.  Dopo aver eseguito l'accesso per la prima volta, verrà visualizzato il pannello *Condizioni per il* servizio. Fare clic sulla casella di *controllo per accettare i termini*. Fare quindi clic **su Accetto**.

    ![](images/AzureLabs-Lab310-03.png)

6.  Dopo aver accettato le condizioni, si è ora nella *sezione Progetti* personali. Fare clic **su Nuovo Project**.

    ![](images/AzureLabs-Lab310-04.png)

7.  Sul lato destro verrà visualizzata una scheda che richiede di specificare alcuni campi per il progetto.

    1.  Inserire un nome per il progetto

    2.  Inserire una descrizione per il progetto (**Facoltativo**)

    3.  Scegliere un **gruppo di risorse** o crearne uno nuovo. Un gruppo di risorse consente di monitorare, controllare l'accesso, effettuare il provisioning e gestire la fatturazione per una raccolta di asset di Azure. È consigliabile mantenere tutti i servizi di Azure associati a un singolo progetto,ad esempio questi corsi, in un gruppo di risorse comune.

        ![](images/AzureLabs-Lab310-05.png)

        > [!NOTE]
        > Per altre informazioni [sui gruppi di risorse di Azure, passare alla documentazione associata](/azure/azure-resource-manager/resource-group-portal)

    4.  Impostare **l'Project tipi di** oggetti **come Rilevamento oggetti (anteprima).**

8.  Al termine, fare clic su **Crea** progetto e si verrà reindirizzati alla pagina del progetto Visione personalizzata Service.


## <a name="chapter-2---training-your-custom-vision-project"></a>Capitolo 2 - Training del progetto Visione personalizzata

Una volta nel portale Visione personalizzata, l'obiettivo principale è eseguire il training del progetto per riconoscere oggetti specifici nelle immagini.

Sono necessarie almeno quindici (15) immagini per ogni oggetto che si vuole riconoscere dall'applicazione. È possibile usare le immagini fornite con questo corso ([una serie di tazze](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Cup%20Images.zip)).

Per eseguire il training Visione personalizzata progetto:

1.  Fare clic sul **+** pulsante accanto a **Tag**.

    ![](images/AzureLabs-Lab310-06.png)

2.  Aggiungere un **nome** per il tag che verrà usato per associare le immagini. In questo esempio si usano immagini di tazze per il riconoscimento, quindi è stato assegnato un nome al tag per questo, **Cup**. Al **termine, fare clic** su Salva.

    ![](images/AzureLabs-Lab310-07.png)

3.  Si noterà che **il tag** è stato aggiunto (potrebbe essere necessario ricaricare la pagina per la visualizzazione). 

    ![](images/AzureLabs-Lab310-08.png)

4.  Fare clic **su Aggiungi** immagini al centro della pagina.

    ![](images/AzureLabs-Lab310-09.png)

5.  Fare clic **su Sfoglia file locali** e individuare le immagini da caricare per un oggetto, con un minimo di 15 (15).

    > [!TIP]
    >  È possibile selezionare più immagini contemporaneamente, da caricare.

    ![](images/AzureLabs-Lab310-10.png)

6.  Premere **Upload file** dopo aver selezionato tutte le immagini con cui si vuole eseguire il training del progetto. Il caricamento dei file inizierà. Dopo aver visualizzato la conferma del caricamento, fare clic su **Fine.**

    ![](images/AzureLabs-Lab310-11.png)

7.  A questo punto le immagini vengono caricate, ma non contrassegnate.

    ![](images/AzureLabs-Lab310-12.png)

8.  Per contrassegnare le immagini, usare il mouse. Quando si passa il mouse sull'immagine, un'evidenziazione della selezione consente di disegnare automaticamente una selezione intorno all'oggetto. Se non è accurato, è possibile disegnarlo. A tale scopo, tenere premuto il pulsante sinistro del mouse e trascinare l'area di selezione per includere l'oggetto. 

    ![](images/AzureLabs-Lab310-13.png) 

9. Dopo la selezione dell'oggetto all'interno dell'immagine, verrà richiesto di aggiungere *tag di area.* Selezionare il tag creato in precedenza ('Cup', nell'esempio precedente) oppure, se si aggiungono altri tag, digitalo e fai clic sul **pulsante + (più).**

    ![](images/AzureLabs-Lab310-14.png) 

10. Per contrassegnare l'immagine successiva, è possibile fare clic sulla freccia a destra del pannello oppure chiudere il pannello dei tag (facendo clic sulla **X** nell'angolo superiore destro del pannello) e quindi fare clic sull'immagine successiva. Dopo aver pronto l'immagine successiva, ripetere la stessa procedura. Eseguire questa operazione per tutte le immagini caricate, fino a quando non vengono contrassegnate tutte. 

    > [!NOTE]
    >  È possibile selezionare più oggetti nella stessa immagine, come nell'immagine seguente: 
    > 
    > ![](images/AzureLabs-Lab310-15.png)

11. Dopo averli contrassegnati tutti,  fare clic sul pulsante con tag a sinistra dello schermo per visualizzare le immagini con tag. 

    ![](images/AzureLabs-Lab310-16.png)

12. A questo punto è possibile eseguire il training del servizio. Fare clic **sul pulsante** Train (Train) (Traina) per avviare la prima

    ![](images/AzureLabs-Lab310-17.png)

    ![](images/AzureLabs-Lab310-18.png)

13. Dopo la creazione, sarà possibile visualizzare due pulsanti denominati **Impostazione predefinita** e **URL stima**. Fare clic su **Make default first** (Rendi impostazione predefinita), quindi fare clic su Prediction URL **(URL stima).**

    ![](images/AzureLabs-Lab310-19.png)

    > [!NOTE] 
    > L'endpoint fornito da questo oggetto è impostato su qualsiasi *iterazione* sia stata contrassegnata come predefinita. Di conseguenza, se in un secondo momento si crea una nuova iterazione *e* la si aggiorna come impostazione predefinita, non sarà necessario modificare il codice.

14. Dopo aver fatto clic su PREDICTION **URL (URL** stima), aprire *Blocco note* e copiare e incollare **l'URL** (denominato anche **Prediction-Endpoint)** e **service prediction-key**, in modo da poterlo recuperare quando necessario in un secondo momento nel codice.

    ![](images/AzureLabs-Lab310-20.png)

## <a name="chapter-3---set-up-the-unity-project"></a>Capitolo 3 - Configurare il progetto Unity

Di seguito è riportata una configurazione tipica per lo sviluppo con la realtà mista e, di conseguenza, è un buon modello per altri progetti.

1.  Aprire **Unity** e fare clic su **Nuovo**.

    ![](images/AzureLabs-Lab310-21.png)

2.  È ora necessario specificare un nome di progetto Unity. Inserire **CustomVisionObjDetection**. Assicurarsi che il tipo di progetto sia impostato  su **3D** e impostare Percorso su un percorso appropriato per l'utente (tenere presente che più vicino alle directory radice è meglio). Fare quindi clic **su Crea progetto**.

    ![](images/AzureLabs-Lab310-22.png)

3.  Con Unity aperto, è opportuno controllare che **l'editor di script predefinito** sia impostato su **Visual Studio**. Passare a **Modifica*  >  *preferenze** e quindi dalla nuova finestra passare a **Strumenti esterni**. Modificare **Editor script esterni** in **Visual Studio**. Chiudere la **finestra** Preferenze.

    ![](images/AzureLabs-Lab310-23.png)

4.  Passare quindi a **File > Build Impostazioni** e  passare alla piattaforma Universal *Windows Platform* e quindi fare clic sul **pulsante Cambia** piattaforma.

    ![](images/AzureLabs-Lab310-24.png)

5.  Nella stessa **finestra Build Impostazioni** verificare che siano impostati gli elementi seguenti:

    1.  **Dispositivo di destinazione** impostato su **HoloLens**        
    2.  **Il tipo di** compilazione è impostato **su D3D**
    3.  **L'SDK** è impostato su **Più recente installato**
    4.  **Visual Studio Version è** impostato su **Latest installed (Versione più recente installata)**
    5.  **Compilazione ed esecuzione** è impostato su **Computer locale**            
    6.  Le impostazioni rimanenti, in **Build Impostazioni**, devono essere lasciato come impostazioni predefinite per il momento.

        ![](images/AzureLabs-Lab310-25.png)

6.  Nella stessa **finestra build Impostazioni** fare clic sul pulsante Player Impostazioni( Player **Impostazioni).** Verrà aperto il pannello correlato nello spazio in cui si trova **Inspector.**

7. In questo pannello è necessario verificare alcune impostazioni:

    1.  Nella scheda **Altro Impostazioni:**

        1.  **La versione del runtime di** scripting deve essere **sperimentale** (equivalente a .NET 4.6), che attiverà la necessità di riavviare l'editor.

        2. **Il back-end di** scripting deve **essere .NET.**

        3. **Il livello di compatibilità dell'API** **deve essere .NET 4.6.**

            ![](images/AzureLabs-Lab310-26.png)

    2.  Nella scheda **Pubblicazione Impostazioni,** in **Funzionalità**, controllare:

        1. **InternetClient**

        2.  **Webcam**

        3. **SpatialPerception**

            ![](images/AzureLabs-Lab310-27.png) ![](images/AzureLabs-Lab310-28.png)

    3.  Più in basso nel pannello, in **XR Impostazioni** (disponibile sotto Pubblica **Impostazioni),** selezionare **Virtual Reality Supported**(Realtà virtuale supportata), quindi assicurarsi che sia aggiunto Windows Mixed Reality **SDK.**

        ![](images/AzureLabs-Lab310-29.png)

8.  In **Build Impostazioni**, Unity C Projects (Progetti *Unity \# C)* non è più in grigio: selezionare la casella di controllo accanto a questo.

9.  Chiudere la finestra **Build Settings** (Impostazioni compilazione).

10. **Nell'editor** fare clic su **Modifica Project Impostazioni**  >    >  **grafica**.

    ![](images/AzureLabs-Lab310-30.png)

11. Nel pannello **Inspector (Controllo)** *Impostazioni* graphics (Grafica). Scorrere verso il basso fino a visualizzare una matrice denominata **Always Include Shaders**. Aggiungere uno slot aumentando la **variabile Size** di uno (in questo esempio era 8, quindi è stato fatto 9). Nell'ultima posizione della matrice verrà visualizzato un nuovo slot, come illustrato di seguito:

    ![](images/AzureLabs-Lab310-31.png)

12. Nello slot fare clic sul piccolo cerchio di destinazione accanto allo slot per aprire un elenco di shader. Cercare lo **shader Legacy Shaders/Transparent/Diffuse** e fare doppio clic su di esso. 

    ![](images/AzureLabs-Lab310-32.png)

## <a name="chapter-4---importing-the-customvisionobjdetection-unity-package"></a>Capitolo 4 - Importazione del pacchetto CustomVisionObjDetection Unity

Per questo corso viene fornito un pacchetto di asset Unity denominato **Azure-MR-310.unitypackage**. 

> [TIP] Tutti gli oggetti supportati da Unity, incluse le scene intere, possono essere inclusi in un file con estensione **unitypackage** e esportati/importati in altri progetti. È il modo più sicuro ed efficiente per spostare gli asset tra progetti **Unity diversi.**

È possibile trovare il [pacchetto Azure-MR-310](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Azure-MR-310.unitypackage)che è necessario scaricare qui.

1.  Con il dashboard unity davanti all'utente, fare clic su Asset **nel** menu nella parte superiore della schermata, quindi fare clic su Importa pacchetto > **pacchetto personalizzato**.

    ![](images/AzureLabs-Lab310-33.png)

2.  Usare la selezione file per selezionare il **pacchetto Azure-MR-310.unitypackage** e fare clic su **Apri**. Verrà visualizzato un elenco di componenti per questo asset. Confermare l'importazione facendo clic **sul pulsante** Importa.

    ![](images/AzureLabs-Lab310-34.png)

3.  Al termine dell'importazione, si noterà che le cartelle del pacchetto sono state aggiunte alla **cartella Assets.** Questo tipo di struttura di cartelle è tipico per un progetto Unity.

    ![](images/AzureLabs-Lab310-35.png)

    1.  La **cartella Materials** contiene il materiale usato dal **cursore sguardo fisso.** 

    2.  La **cartella Plugins** contiene la DLL Newtonsoft usata dal codice per deserializzare la risposta Web del servizio. Le due (2) versioni diverse contenute nella cartella e nella sottocartella sono necessarie per consentire l'uso e la compilazione della libreria sia dall'editor di Unity che dalla compilazione UWP. 

    3.  La **cartella Prefabs** contiene i prefab contenuti nella scena. Essi sono:

        1.  **GazeCursor**, il cursore usato nell'applicazione. Funzionerà insieme al prefab SpatialMapping per poter essere posizionato nella scena sopra gli oggetti fisici.
        2.  Etichetta **,** che è l'oggetto dell'interfaccia utente usato per visualizzare il tag dell'oggetto nella scena quando necessario.
        3.  **SpatialMapping**, ovvero l'oggetto che consente all'applicazione di usare la creazione di una mappa virtuale, usando il Microsoft HoloLens spaziale.

    4.  Cartella **Scenes** che attualmente contiene la scena predefinita per questo corso.

4.  Aprire la **cartella Scenes** nel **pannello Project** e fare doppio clic su **ObjDetectionScene** per caricare la scena che verrà utilizzata per questo corso.

    ![](images/AzureLabs-Lab310-36.png)

    > [!NOTE] 
    >  **Non è incluso codice**, il codice verrà scritto seguendo questo corso.

## <a name="chapter-5---create-the-customvisionanalyser-class"></a>Capitolo 5: Creare la classe CustomVisionAnalyser.

A questo punto è possibile scrivere codice. Si inizierà con la **classe CustomVisionAnalyser.**

> [!NOTE]
> Le chiamate al servizio **Visione personalizzata**, effettuate nel codice illustrato di seguito, vengono effettuate usando l'API **REST Visione personalizzata .** Usando questa funzionalità, si scoprirà come implementare e usare questa API (utile per comprendere come implementare qualcosa di simile in modo personalizzato). Tenere presente che Microsoft offre Visione personalizzata **SDK** che può essere usato anche per effettuare chiamate al servizio. Per altre informazioni, vedere [l'articolo Visione personalizzata SDK.](https://github.com/Microsoft/Cognitive-CustomVision-Windows/)

Questa classe è responsabile di:

- Caricamento dell'immagine più recente acquisita come matrice di byte.

- Invio della matrice di byte all'istanza **del servizio Azure Visione personalizzata per** l'analisi.

- Ricezione della risposta come stringa JSON.

- Deserializzazione della risposta  e passaggio della stima risultante alla **classe SceneOrganiser,** che si occuperà della modalità di visualizzazione della risposta.

Per creare questa classe:

1.  Fare clic con il pulsante destro **del mouse** nella cartella Asset , che si trova nel pannello **Project ,** quindi scegliere **Crea**  >  **cartella**. Chiamare la cartella **Scripts**.

    ![](images/AzureLabs-Lab310-37.png)

2.  Fare doppio clic sulla cartella appena creata per aprirla.

3.  Fare clic con il pulsante destro del mouse all'interno della cartella , **quindi scegliere Crea**  >  **\# script C**. Assegnare allo script **il nome CustomVisionAnalyser.**

4.  Fare doppio clic sul nuovo script **CustomVisionAnalyser** per aprirlo con **Visual Studio.**

5.  Assicurarsi di avere gli spazi dei nomi seguenti a cui viene fatto riferimento nella parte superiore del file:

    ```csharp
    using Newtonsoft.Json;
    using System.Collections;
    using System.IO;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

6.  Nella **classe CustomVisionAnalyser** aggiungere le variabili seguenti:

    ```csharp
        /// <summary>
        /// Unique instance of this class
        /// </summary>
        public static CustomVisionAnalyser Instance;

        /// <summary>
        /// Insert your prediction key here
        /// </summary>
        private string predictionKey = "- Insert your key here -";

        /// <summary>
        /// Insert your prediction endpoint here
        /// </summary>
        private string predictionEndpoint = "Insert your prediction endpoint here";

        /// <summary>
        /// Bite array of the image to submit for analysis
        /// </summary>
        [HideInInspector] public byte[] imageBytes;
    ```

    > [!NOTE]
    > Assicurarsi di inserire la **chiave di stima del servizio** nella variabile **predictionKey** e **prediction-endpoint** nella **variabile predictionEndpoint.** Sono stati copiati [in Blocco note precedente, nel capitolo 2, passaggio 14.](#chapter-2---training-your-custom-vision-project)

7.  È ora necessario aggiungere il codice per **Awake()** per inizializzare la variabile Instance:

    ```csharp
        /// <summary>
        /// Initializes this class
        /// </summary>
        private void Awake()
        {
            // Allows this instance to behave like a singleton
            Instance = this;
        }
    ```

8.  Aggiungere la coroutine (con il metodo **statico GetImageAsByteArray()** sottostante), che otterrà i risultati dell'analisi dell'immagine, acquisita dalla **classe ImageCapture.**

    > [!NOTE]
    > Nella coroutine **AnalyseImageCapture** è presente una chiamata alla **classe SceneOrganiser** che è ancora necessario creare. Pertanto, **lasciare tali righe commentate per il momento.**

    ```csharp    
        /// <summary>
        /// Call the Computer Vision Service to submit the image.
        /// </summary>
        public IEnumerator AnalyseLastImageCaptured(string imagePath)
        {
            Debug.Log("Analyzing...");

            WWWForm webForm = new WWWForm();

            using (UnityWebRequest unityWebRequest = UnityWebRequest.Post(predictionEndpoint, webForm))
            {
                // Gets a byte array out of the saved image
                imageBytes = GetImageAsByteArray(imagePath);

                unityWebRequest.SetRequestHeader("Content-Type", "application/octet-stream");
                unityWebRequest.SetRequestHeader("Prediction-Key", predictionKey);

                // The upload handler will help uploading the byte array with the request
                unityWebRequest.uploadHandler = new UploadHandlerRaw(imageBytes);
                unityWebRequest.uploadHandler.contentType = "application/octet-stream";

                // The download handler will help receiving the analysis from Azure
                unityWebRequest.downloadHandler = new DownloadHandlerBuffer();

                // Send the request
                yield return unityWebRequest.SendWebRequest();

                string jsonResponse = unityWebRequest.downloadHandler.text;

                Debug.Log("response: " + jsonResponse);

                // Create a texture. Texture size does not matter, since
                // LoadImage will replace with the incoming image size.
                //Texture2D tex = new Texture2D(1, 1);
                //tex.LoadImage(imageBytes);
                //SceneOrganiser.Instance.quadRenderer.material.SetTexture("_MainTex", tex);

                // The response will be in JSON format, therefore it needs to be deserialized
                //AnalysisRootObject analysisRootObject = new AnalysisRootObject();
                //analysisRootObject = JsonConvert.DeserializeObject<AnalysisRootObject>(jsonResponse);

                //SceneOrganiser.Instance.FinaliseLabel(analysisRootObject);
            }
        }

        /// <summary>
        /// Returns the contents of the specified image file as a byte array.
        /// </summary>
        static byte[] GetImageAsByteArray(string imageFilePath)
        {
            FileStream fileStream = new FileStream(imageFilePath, FileMode.Open, FileAccess.Read);

            BinaryReader binaryReader = new BinaryReader(fileStream);

            return binaryReader.ReadBytes((int)fileStream.Length);
        }
    ```

9. Eliminare i **metodi Start()** **e Update()** perché non verranno usati. 

10.  Assicurarsi di salvare le modifiche in **Visual Studio**, prima di tornare a **Unity.**

> [!IMPORTANT]
> Come accennato in precedenza, non preoccuparsi del codice che potrebbe sembrare che abbia un errore, perché presto verranno fornite altre classi, che risolveranno questi problemi.

## <a name="chapter-6---create-the-customvisionobjects-class"></a>Capitolo 6 - Creare la classe CustomVisionObjects

La classe che verrà creata ora è **la classe CustomVisionObjects.**

Questo script contiene diversi oggetti utilizzati da altre classi per serializzare e deserializzare le chiamate effettuate al Visione personalizzata servizio.

Per creare questa classe:

1.  Fare clic con il pulsante destro del **mouse all'interno della cartella** Script , quindi scegliere **Crea**  >  **\# script C**. Chiamare lo script **CustomVisionObjects.**

2.  Fare doppio clic sul nuovo script **CustomVisionObjects** per aprirlo con **Visual Studio.**

3.  Assicurarsi di avere gli spazi dei nomi seguenti a cui si fa riferimento all'inizio del file:

    ```csharp
    using System;
    using System.Collections.Generic;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

4.  Eliminare i **metodi Start()** **e Update()** all'interno **della classe CustomVisionObjects.** Questa classe dovrebbe ora essere vuota.

    > [!WARNING]
    > È importante seguire attentamente l'istruzione successiva. Se si inserendo le nuove dichiarazioni di classe all'interno della classe **CustomVisionObjects,** si riceveranno errori di compilazione nel capitolo [10,](#chapter-10---create-the-imagecapture-class)indicando che **AnalysisRootObject** e **BoundingBox** non sono stati trovati.

5.  Aggiungere le classi seguenti *all'esterno* **della classe CustomVisionObjects.** Questi oggetti vengono usati dalla libreria **Newtonsoft** per serializzare e deserializzare i dati della risposta:

    ```csharp
    // The objects contained in this script represent the deserialized version
    // of the objects used by this application 

    /// <summary>
    /// Web request object for image data
    /// </summary>
    class MultipartObject : IMultipartFormSection
    {
        public string sectionName { get; set; }

        public byte[] sectionData { get; set; }

        public string fileName { get; set; }

        public string contentType { get; set; }
    }

    /// <summary>
    /// JSON of all Tags existing within the project
    /// contains the list of Tags
    /// </summary> 
    public class Tags_RootObject
    {
        public List<TagOfProject> Tags { get; set; }
        public int TotalTaggedImages { get; set; }
        public int TotalUntaggedImages { get; set; }
    }

    public class TagOfProject
    {
        public string Id { get; set; }
        public string Name { get; set; }
        public string Description { get; set; }
        public int ImageCount { get; set; }
    }

    /// <summary>
    /// JSON of Tag to associate to an image
    /// Contains a list of hosting the tags,
    /// since multiple tags can be associated with one image
    /// </summary> 
    public class Tag_RootObject
    {
        public List<Tag> Tags { get; set; }
    }

    public class Tag
    {
        public string ImageId { get; set; }
        public string TagId { get; set; }
    }

    /// <summary>
    /// JSON of images submitted
    /// Contains objects that host detailed information about one or more images
    /// </summary> 
    public class ImageRootObject
    {
        public bool IsBatchSuccessful { get; set; }
        public List<SubmittedImage> Images { get; set; }
    }

    public class SubmittedImage
    {
        public string SourceUrl { get; set; }
        public string Status { get; set; }
        public ImageObject Image { get; set; }
    }

    public class ImageObject
    {
        public string Id { get; set; }
        public DateTime Created { get; set; }
        public int Width { get; set; }
        public int Height { get; set; }
        public string ImageUri { get; set; }
        public string ThumbnailUri { get; set; }
    }

    /// <summary>
    /// JSON of Service Iteration
    /// </summary> 
    public class Iteration
    {
        public string Id { get; set; }
        public string Name { get; set; }
        public bool IsDefault { get; set; }
        public string Status { get; set; }
        public string Created { get; set; }
        public string LastModified { get; set; }
        public string TrainedAt { get; set; }
        public string ProjectId { get; set; }
        public bool Exportable { get; set; }
        public string DomainId { get; set; }
    }

    /// <summary>
    /// Predictions received by the Service
    /// after submitting an image for analysis
    /// Includes Bounding Box
    /// </summary>
    public class AnalysisRootObject
    {
        public string id { get; set; }
        public string project { get; set; }
        public string iteration { get; set; }
        public DateTime created { get; set; }
        public List<Prediction> predictions { get; set; }
    }

    public class BoundingBox
    {
        public double left { get; set; }
        public double top { get; set; }
        public double width { get; set; }
        public double height { get; set; }
    }

    public class Prediction
    {
        public double probability { get; set; }
        public string tagId { get; set; }
        public string tagName { get; set; }
        public BoundingBox boundingBox { get; set; }
    }
    ```

6.  Assicurarsi di salvare le modifiche in **Visual Studio**, prima di tornare a **Unity.**

## <a name="chapter-7---create-the-spatialmapping-class"></a>Capitolo 7 - Creare la classe SpatialMapping

Questa classe imposta il **collisore** di mapping spaziale nella scena in modo da essere in grado di rilevare le collisioni tra oggetti virtuali e oggetti reali.

Per creare questa classe:

1.  Fare clic con il pulsante destro del **mouse all'interno della cartella** Script , quindi scegliere **Crea**  >  **\# script C**. Chiamare lo script **SpatialMapping.**

2.  Fare doppio clic sul nuovo script **SpatialMapping** per aprirlo con **Visual Studio.**

3.  Assicurarsi di avere gli spazi dei nomi seguenti a cui si fa riferimento sopra **la classe SpatialMapping:**

    ```csharp
    using UnityEngine;
    using UnityEngine.XR.WSA;
    ```

4.  Aggiungere quindi le variabili seguenti all'interno **della classe SpatialMapping,** sopra il **metodo Start():**

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static SpatialMapping Instance;

        /// <summary>
        /// Used by the GazeCursor as a property with the Raycast call
        /// </summary>
        internal static int PhysicsRaycastMask;

        /// <summary>
        /// The layer to use for spatial mapping collisions
        /// </summary>
        internal int physicsLayer = 31;

        /// <summary>
        /// Creates environment colliders to work with physics
        /// </summary>
        private SpatialMappingCollider spatialMappingCollider;
    ```

5.  Aggiungere **Le proprietà Awake()** **e Start():**

    ```csharp
        /// <summary>
        /// Initializes this class
        /// </summary>
        private void Awake()
        {
            // Allows this instance to behave like a singleton
            Instance = this;
        }

        /// <summary>
        /// Runs at initialization right after Awake method
        /// </summary>
        void Start()
        {
            // Initialize and configure the collider
            spatialMappingCollider = gameObject.GetComponent<SpatialMappingCollider>();
            spatialMappingCollider.surfaceParent = this.gameObject;
            spatialMappingCollider.freezeUpdates = false;
            spatialMappingCollider.layer = physicsLayer;

            // define the mask
            PhysicsRaycastMask = 1 << physicsLayer;

            // set the object as active one
            gameObject.SetActive(true);
        }
    ```

6.  Eliminare il **metodo Update().**

7.  Assicurarsi di salvare le modifiche in **Visual Studio**, prima di tornare a **Unity.**


## <a name="chapter-8---create-the-gazecursor-class"></a>Capitolo 8 - Creare la classe GazeCursor

Questa classe è responsabile della configurazione del cursore nella posizione corretta nello spazio reale, usando **spatialMappingCollider,** creato nel capitolo precedente.

Per creare questa classe:

1.  Fare clic con il pulsante destro del **mouse all'interno della cartella** Script , quindi scegliere **Crea**  >  **\# script C**. Chiamare lo script **GazeCursor**

2.  Fare doppio clic sul nuovo script **GazeCursor** per aprirlo con **Visual Studio.**

3.  Assicurarsi di avere lo spazio dei nomi seguente a cui si fa riferimento sopra la **classe GazeCursor:**

    ```csharp
    using UnityEngine;
    ```

4.  Aggiungere quindi la variabile seguente all'interno **della classe GazeCursor,** sopra il **metodo Start().** 

    ```csharp
        /// <summary>
        /// The cursor (this object) mesh renderer
        /// </summary>
        private MeshRenderer meshRenderer;
    ```

5.  Aggiornare il **metodo Start()** con il codice seguente:

    ```csharp
        /// <summary>
        /// Runs at initialization right after the Awake method
        /// </summary>
        void Start()
        {
            // Grab the mesh renderer that is on the same object as this script.
            meshRenderer = gameObject.GetComponent<MeshRenderer>();

            // Set the cursor reference
            SceneOrganiser.Instance.cursor = gameObject;
            gameObject.GetComponent<Renderer>().material.color = Color.green;

            // If you wish to change the size of the cursor you can do so here
            gameObject.transform.localScale = new Vector3(0.01f, 0.01f, 0.01f);
        }
    ```

6.  Aggiornare il **metodo Update()** con il codice seguente:

    ```csharp
        /// <summary>
        /// Update is called once per frame
        /// </summary>
        void Update()
        {
            // Do a raycast into the world based on the user's head position and orientation.
            Vector3 headPosition = Camera.main.transform.position;
            Vector3 gazeDirection = Camera.main.transform.forward;

            RaycastHit gazeHitInfo;
            if (Physics.Raycast(headPosition, gazeDirection, out gazeHitInfo, 30.0f, SpatialMapping.PhysicsRaycastMask))
            {
                // If the raycast hit a hologram, display the cursor mesh.
                meshRenderer.enabled = true;
                // Move the cursor to the point where the raycast hit.
                transform.position = gazeHitInfo.point;
                // Rotate the cursor to hug the surface of the hologram.
                transform.rotation = Quaternion.FromToRotation(Vector3.up, gazeHitInfo.normal);
            }
            else
            {
                // If the raycast did not hit a hologram, hide the cursor mesh.
                meshRenderer.enabled = false;
            }
        }
    ```

    > [!NOTE]
    > Non è necessario preoccuparsi dell'errore per la **classe SceneOrganiser** che non viene trovato, perché verrà creato nel capitolo successivo.

7. Assicurarsi di salvare le modifiche in **Visual Studio**, prima di tornare a **Unity.**

## <a name="chapter-9---create-the-sceneorganiser-class"></a>Capitolo 9: Creare la classe SceneOrganiser

Questa classe:

-   Configurare la *fotocamera principale* collegando i componenti appropriati.

-   Quando viene rilevato un oggetto, sarà responsabile del calcolo della posizione nel mondo reale e dell'posizionamento di un'etichetta **di** tag accanto all'oggetto con il nome **tag appropriato.**    

Per creare questa classe:

1.  Fare clic con il pulsante destro del **mouse all'interno della cartella** Script , quindi scegliere **Crea**  >  **\# script C**. Assegnare allo script **il nome SceneOrganiser**.

2.  Fare doppio clic sul nuovo script **SceneOrganiser** per aprirlo con **Visual Studio.**

3.  Assicurarsi di avere gli spazi dei nomi seguenti a cui si fa riferimento sopra **la classe SceneOrganiser:**

    ```csharp
    using System.Collections.Generic;
    using System.Linq;
    using UnityEngine;
    ```

4.  Aggiungere quindi le variabili seguenti all'interno **della classe SceneOrganiser,** sopra il **metodo Start():**

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static SceneOrganiser Instance;

        /// <summary>
        /// The cursor object attached to the Main Camera
        /// </summary>
        internal GameObject cursor;

        /// <summary>
        /// The label used to display the analysis on the objects in the real world
        /// </summary>
        public GameObject label;

        /// <summary>
        /// Reference to the last Label positioned
        /// </summary>
        internal Transform lastLabelPlaced;

        /// <summary>
        /// Reference to the last Label positioned
        /// </summary>
        internal TextMesh lastLabelPlacedText;

        /// <summary>
        /// Current threshold accepted for displaying the label
        /// Reduce this value to display the recognition more often
        /// </summary>
        internal float probabilityThreshold = 0.8f;

        /// <summary>
        /// The quad object hosting the imposed image captured
        /// </summary>
        private GameObject quad;

        /// <summary>
        /// Renderer of the quad object
        /// </summary>
        internal Renderer quadRenderer;
    ```

5.  Eliminare i **metodi Start()** **e Update().**

6.  Sotto le variabili aggiungere il **metodo Awake(),** che inizializza la classe e configura la scena.

    ```csharp
        /// <summary>
        /// Called on initialization
        /// </summary>
        private void Awake()
        {
            // Use this class instance as singleton
            Instance = this;

            // Add the ImageCapture class to this Gameobject
            gameObject.AddComponent<ImageCapture>();

            // Add the CustomVisionAnalyser class to this Gameobject
            gameObject.AddComponent<CustomVisionAnalyser>();

            // Add the CustomVisionObjects class to this Gameobject
            gameObject.AddComponent<CustomVisionObjects>();
        }
    ```

7.  Aggiungere il **metodo PlaceAnalysisLabel(),** che crea un'istanza dell'etichetta nella scena (che a questo punto è invisibile all'utente).  Inserisce anche il quad (anche invisibile) in cui viene posizionata l'immagine e si sovrappone al mondo reale. Questo è importante perché le coordinate della scatola recuperate dal servizio dopo l'analisi vengono tracciate in questo quad per determinare la posizione approssimativa dell'oggetto nel mondo reale. 

    ```csharp
        /// <summary>
        /// Instantiate a Label in the appropriate location relative to the Main Camera.
        /// </summary>
        public void PlaceAnalysisLabel()
        {
            lastLabelPlaced = Instantiate(label.transform, cursor.transform.position, transform.rotation);
            lastLabelPlacedText = lastLabelPlaced.GetComponent<TextMesh>();
            lastLabelPlacedText.text = "";
            lastLabelPlaced.transform.localScale = new Vector3(0.005f,0.005f,0.005f);

            // Create a GameObject to which the texture can be applied
            quad = GameObject.CreatePrimitive(PrimitiveType.Quad);
            quadRenderer = quad.GetComponent<Renderer>() as Renderer;
            Material m = new Material(Shader.Find("Legacy Shaders/Transparent/Diffuse"));
            quadRenderer.material = m;

            // Here you can set the transparency of the quad. Useful for debugging
            float transparency = 0f;
            quadRenderer.material.color = new Color(1, 1, 1, transparency);

            // Set the position and scale of the quad depending on user position
            quad.transform.parent = transform;
            quad.transform.rotation = transform.rotation;

            // The quad is positioned slightly forward in font of the user
            quad.transform.localPosition = new Vector3(0.0f, 0.0f, 3.0f);

            // The quad scale as been set with the following value following experimentation,  
            // to allow the image on the quad to be as precisely imposed to the real world as possible
            quad.transform.localScale = new Vector3(3f, 1.65f, 1f);
            quad.transform.parent = null;
        }
    ```

8.  Aggiungere il **metodo FinaliseLabel().** È responsabile di:

    *   Impostazione del *testo etichetta* con il *tag* della stima con la massima attendibilità.
    *   Chiamata del calcolo del *rettangolo di selezione sull'oggetto* quad, posizionato in precedenza, e posizionamento dell'etichetta nella scena.
    *   Regolare la profondità dell'etichetta usando un raycast verso il *rettangolo* di selezione, che dovrebbe entrare in conflitto con l'oggetto nel mondo reale.
    * Reimpostazione del processo di acquisizione per consentire all'utente di acquisire un'altra immagine.

    ```csharp
        /// <summary>
        /// Set the Tags as Text of the last label created. 
        /// </summary>
        public void FinaliseLabel(AnalysisRootObject analysisObject)
        {
            if (analysisObject.predictions != null)
            {
                lastLabelPlacedText = lastLabelPlaced.GetComponent<TextMesh>();
                // Sort the predictions to locate the highest one
                List<Prediction> sortedPredictions = new List<Prediction>();
                sortedPredictions = analysisObject.predictions.OrderBy(p => p.probability).ToList();
                Prediction bestPrediction = new Prediction();
                bestPrediction = sortedPredictions[sortedPredictions.Count - 1];

                if (bestPrediction.probability > probabilityThreshold)
                {
                    quadRenderer = quad.GetComponent<Renderer>() as Renderer;
                    Bounds quadBounds = quadRenderer.bounds;

                    // Position the label as close as possible to the Bounding Box of the prediction 
                    // At this point it will not consider depth
                    lastLabelPlaced.transform.parent = quad.transform;
                    lastLabelPlaced.transform.localPosition = CalculateBoundingBoxPosition(quadBounds, bestPrediction.boundingBox);

                    // Set the tag text
                    lastLabelPlacedText.text = bestPrediction.tagName;

                    // Cast a ray from the user's head to the currently placed label, it should hit the object detected by the Service.
                    // At that point it will reposition the label where the ray HL sensor collides with the object,
                    // (using the HL spatial tracking)
                    Debug.Log("Repositioning Label");
                    Vector3 headPosition = Camera.main.transform.position;
                    RaycastHit objHitInfo;
                    Vector3 objDirection = lastLabelPlaced.position;
                    if (Physics.Raycast(headPosition, objDirection, out objHitInfo, 30.0f,   SpatialMapping.PhysicsRaycastMask))
                    {
                        lastLabelPlaced.position = objHitInfo.point;
                    }
                }
            }
            // Reset the color of the cursor
            cursor.GetComponent<Renderer>().material.color = Color.green;

            // Stop the analysis process
            ImageCapture.Instance.ResetImageCapture();        
        }
    ```

9.  Aggiungere il **metodo CalculateBoundingBoxPosition(),** che ospita una serie  di calcoli necessari per convertire le coordinate del rettangolo di selezione recuperate dal servizio e ricrearle in modo proporzionale sul quad.

    ```csharp
        /// <summary>
        /// This method hosts a series of calculations to determine the position 
        /// of the Bounding Box on the quad created in the real world
        /// by using the Bounding Box received back alongside the Best Prediction
        /// </summary>
        public Vector3 CalculateBoundingBoxPosition(Bounds b, BoundingBox boundingBox)
        {
            Debug.Log($"BB: left {boundingBox.left}, top {boundingBox.top}, width {boundingBox.width}, height {boundingBox.height}");

            double centerFromLeft = boundingBox.left + (boundingBox.width / 2);
            double centerFromTop = boundingBox.top + (boundingBox.height / 2);
            Debug.Log($"BB CenterFromLeft {centerFromLeft}, CenterFromTop {centerFromTop}");

            double quadWidth = b.size.normalized.x;
            double quadHeight = b.size.normalized.y;
            Debug.Log($"Quad Width {b.size.normalized.x}, Quad Height {b.size.normalized.y}");

            double normalisedPos_X = (quadWidth * centerFromLeft) - (quadWidth/2);
            double normalisedPos_Y = (quadHeight * centerFromTop) - (quadHeight/2);

            return new Vector3((float)normalisedPos_X, (float)normalisedPos_Y, 0);
        }
    ```

10. Assicurarsi di salvare le modifiche in **Visual Studio**, prima di tornare a **Unity.**

    > [!IMPORTANT]
    > Prima di continuare, aprire la **classe CustomVisionAnalyser** e all'interno del metodo **AnalyseLastImageCaptured()** rimuovere il commento *dalle* righe seguenti:
    >
    >   ```csharp
    >   // Create a texture. Texture size does not matter, since 
    >   // LoadImage will replace with the incoming image size.
    >   Texture2D tex = new Texture2D(1, 1);
    >   tex.LoadImage(imageBytes);
    >   SceneOrganiser.Instance.quadRenderer.material.SetTexture("_MainTex", tex);
    >
    >   // The response will be in JSON format, therefore it needs to be deserialized
    >   AnalysisRootObject analysisRootObject = new AnalysisRootObject();
    >   analysisRootObject = JsonConvert.DeserializeObject<AnalysisRootObject>(jsonResponse);
    >
    >   SceneOrganiser.Instance.FinaliseLabel(analysisRootObject);
    >   ```

> [!NOTE]
> Non preoccuparsi del messaggio "Impossibile trovare" la classe **ImageCapture,** che verrà creato nel capitolo successivo.


## <a name="chapter-10---create-the-imagecapture-class"></a>Capitolo 10 - Creare la classe ImageCapture

La classe successiva che si creerà è **la classe ImageCapture.**

Questa classe è responsabile di:

*   Acquisizione di un'immagine con HoloLens fotocamera e archiviazione nella *cartella App.*
*   Gestione dei *movimenti tocco* da parte dell'utente.

Per creare questa classe:

1.  Passare alla cartella **Scripts** creata in precedenza.

2.  Fare clic con il pulsante destro del mouse all'interno della cartella , **quindi scegliere Crea** script  >  **C \#**. Assegnare allo script **il nome ImageCapture**.

3.  Fare doppio clic sul nuovo script **ImageCapture** per aprirlo con **Visual Studio.**

4.  Sostituire gli spazi dei nomi all'inizio del file con quanto segue:

    ```csharp
    using System;
    using System.IO;
    using System.Linq;
    using UnityEngine;
    using UnityEngine.XR.WSA.Input;
    using UnityEngine.XR.WSA.WebCam;
    ```

5.  Aggiungere quindi le variabili seguenti all'interno **della classe ImageCapture,** sopra il **metodo Start():**

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static ImageCapture Instance;

        /// <summary>
        /// Keep counts of the taps for image renaming
        /// </summary>
        private int captureCount = 0;

        /// <summary>
        /// Photo Capture object
        /// </summary>
        private PhotoCapture photoCaptureObject = null;

        /// <summary>
        /// Allows gestures recognition in HoloLens
        /// </summary>
        private GestureRecognizer recognizer;

        /// <summary>
        /// Flagging if the capture loop is running
        /// </summary>
        internal bool captureIsActive;
        
        /// <summary>
        /// File path of current analysed photo
        /// </summary>
        internal string filePath = string.Empty;
    ```

6.  È ora necessario aggiungere il codice per i metodi **Awake()** e **Start():**

    ```csharp
        /// <summary>
        /// Called on initialization
        /// </summary>
        private void Awake()
        {
            Instance = this;
        }

        /// <summary>
        /// Runs at initialization right after Awake method
        /// </summary>
        void Start()
        {
            // Clean up the LocalState folder of this application from all photos stored
            DirectoryInfo info = new DirectoryInfo(Application.persistentDataPath);
            var fileInfo = info.GetFiles();
            foreach (var file in fileInfo)
            {
                try
                {
                    file.Delete();
                }
                catch (Exception)
                {
                    Debug.LogFormat("Cannot delete file: ", file.Name);
                }
            } 

            // Subscribing to the Microsoft HoloLens API gesture recognizer to track user gestures
            recognizer = new GestureRecognizer();
            recognizer.SetRecognizableGestures(GestureSettings.Tap);
            recognizer.Tapped += TapHandler;
            recognizer.StartCapturingGestures();
        }
    ```

7.  Implementare un gestore che verrà chiamato quando si verifica un movimento tocco:

    ```csharp
        /// <summary>
        /// Respond to Tap Input.
        /// </summary>
        private void TapHandler(TappedEventArgs obj)
        {
            if (!captureIsActive)
            {
                captureIsActive = true;

                // Set the cursor color to red
                SceneOrganiser.Instance.cursor.GetComponent<Renderer>().material.color = Color.red;

                // Begin the capture loop
                Invoke("ExecuteImageCaptureAndAnalysis", 0);
            }
        }
    ```

    > [!IMPORTANT]
    > Quando il cursore **è verde,** significa che la fotocamera è disponibile per l'immagine. Quando il cursore **è rosso,** significa che la fotocamera è occupata.

8.  Aggiungere il metodo utilizzato dall'applicazione per avviare il processo di acquisizione dell'immagine e archiviare l'immagine:

    ```csharp
        /// <summary>
        /// Begin process of image capturing and send to Azure Custom Vision Service.
        /// </summary>
        private void ExecuteImageCaptureAndAnalysis()
        {
            // Create a label in world space using the ResultsLabel class 
            // Invisible at this point but correctly positioned where the image was taken
            SceneOrganiser.Instance.PlaceAnalysisLabel();

            // Set the camera resolution to be the highest possible
            Resolution cameraResolution = PhotoCapture.SupportedResolutions.OrderByDescending
                ((res) => res.width * res.height).First();
            Texture2D targetTexture = new Texture2D(cameraResolution.width, cameraResolution.height);

            // Begin capture process, set the image format
            PhotoCapture.CreateAsync(true, delegate (PhotoCapture captureObject)
            {
                photoCaptureObject = captureObject;

                CameraParameters camParameters = new CameraParameters
                {
                    hologramOpacity = 1.0f,
                    cameraResolutionWidth = targetTexture.width,
                    cameraResolutionHeight = targetTexture.height,
                    pixelFormat = CapturePixelFormat.BGRA32
                };

                // Capture the image from the camera and save it in the App internal folder
                captureObject.StartPhotoModeAsync(camParameters, delegate (PhotoCapture.PhotoCaptureResult result)
                {
                    string filename = string.Format(@"CapturedImage{0}.jpg", captureCount);
                    filePath = Path.Combine(Application.persistentDataPath, filename);          
                    captureCount++;              
                    photoCaptureObject.TakePhotoAsync(filePath, PhotoCaptureFileOutputFormat.JPG, OnCapturedPhotoToDisk);              
                });
            });
        }
    ```

9.  Aggiungere i gestori che verranno chiamati quando la foto è stata acquisita e per quando è pronta per l'analisi. Il risultato viene quindi passato a **CustomVisionAnalyser per** l'analisi.

    ```csharp
        /// <summary>
        /// Register the full execution of the Photo Capture. 
        /// </summary>
        void OnCapturedPhotoToDisk(PhotoCapture.PhotoCaptureResult result)
        {
            try
            {
                // Call StopPhotoMode once the image has successfully captured
                photoCaptureObject.StopPhotoModeAsync(OnStoppedPhotoMode);
            }
            catch (Exception e)
            {
                Debug.LogFormat("Exception capturing photo to disk: {0}", e.Message);
            }
        }

        /// <summary>
        /// The camera photo mode has stopped after the capture.
        /// Begin the image analysis process.
        /// </summary>
        void OnStoppedPhotoMode(PhotoCapture.PhotoCaptureResult result)
        {
            Debug.LogFormat("Stopped Photo Mode");
        
            // Dispose from the object in memory and request the image analysis 
            photoCaptureObject.Dispose();
            photoCaptureObject = null;

            // Call the image analysis
            StartCoroutine(CustomVisionAnalyser.Instance.AnalyseLastImageCaptured(filePath)); 
        }

        /// <summary>
        /// Stops all capture pending actions
        /// </summary>
        internal void ResetImageCapture()
        {
            captureIsActive = false;

            // Set the cursor color to green
            SceneOrganiser.Instance.cursor.GetComponent<Renderer>().material.color = Color.green;

            // Stop the capture loop if active
            CancelInvoke();
        }
    ```

10. Assicurarsi di salvare le modifiche in **Visual Studio**, prima di tornare a **Unity.**

## <a name="chapter-11---setting-up-the-scripts-in-the-scene"></a>Capitolo 11 - Configurazione degli script nella scena

Dopo aver scritto tutto il codice necessario per questo progetto, è il momento di configurare gli script nella scena e nei prefab per il corretto funzionamento.

1.  **All'interno dell'editor** di Unity, nel **pannello Hierarchy (Gerarchia)** selezionare **Main Camera (Fotocamera principale).**
2.  Nel pannello **Inspector (Controllo),** con la fotocamera principale selezionata, fai clic su **Add Component**(Aggiungi componente), quindi cerca sceneOrganiser script (Script **SceneOrganiser)** e fai doppio clic per aggiungerlo. 

    ![](images/AzureLabs-Lab310-38.png)

3.   Nel pannello **Project** aprire la cartella Prefab , trascinare il **prefab** **Etichetta** nell'area di input della destinazione di riferimento etichetta vuota, nello script **SceneOrganiser** appena aggiunto alla fotocamera principale, come illustrato nell'immagine seguente: 

    ![](images/AzureLabs-Lab310-39.png)

4.  Nel pannello **Hierarchy (Gerarchia)** selezionare **l'elemento figlio GazeCursor** della **fotocamera principale.**
5.  Nel pannello **Inspector (Controllo)** con **gazeCursor** selezionato fare clic su **Add Component**(Aggiungi componente), quindi cercare lo script **GazeCursor** e fare doppio clic su per aggiungerlo.

    ![](images/AzureLabs-Lab310-40.png)

6.  Anche in questo caso, **nel pannello Gerarchia** selezionare **l'elemento figlio SpatialMapping** della **fotocamera principale.**
7.  Nel pannello **Inspector (Controllo),** con **spatialMapping** selezionato, fare clic su **Add Component**(Aggiungi componente), quindi cercare SpatialMapping script (Script **SpatialMapping)** e fare doppio clic per aggiungerlo.

    ![](images/AzureLabs-Lab310-41.png)

Gli script rimanenti non impostati verranno aggiunti dal codice nello script **SceneOrganiser** durante il runtime.

## <a name="chapter-12---before-building"></a>Capitolo 12 - Prima della compilazione

Per eseguire un test completo dell'applicazione, è necessario eseguire il sideload nell'Microsoft HoloLens.

Prima di procedere, assicurarsi che:

-  Tutte le impostazioni indicate nel [capitolo 3](#chapter-3---set-up-the-unity-project) sono impostate correttamente.
- Lo script **SceneOrganiser** è collegato **all'oggetto Fotocamera** principale.
- Lo script **GazeCursor** è collegato **all'oggetto GazeCursor.**
- Lo script **SpatialMapping** è collegato **all'oggetto SpatialMapping.**
- Nel [capitolo 5](#chapter-5---create-the-customvisionanalyser-class), passaggio 6:

    - Assicurarsi di inserire la **chiave di stima del servizio** nella variabile **predictionKey.**
    - L'endpoint **di stima è stato** inserito nella **classe predictionEndpoint.**

## <a name="chapter-13---build-the-uwp-solution-and-sideload-your-application"></a>Capitolo 13- Compilare la soluzione UWP e sideload dell'applicazione

A questo punto è possibile compilare l'applicazione come soluzione UWP in cui sarà possibile eseguire la distribuzione nel Microsoft HoloLens. Per avviare il processo di compilazione:

1.  Passare a **File > Build Impostazioni**.

2.  Selezionare **Unity C \# Projects (Progetti Unity C).**

3.  Fare clic **su Aggiungi scene aperte**. Verrà aggiunta la scena attualmente aperta alla compilazione.

    ![](images/AzureLabs-Lab310-42.png)

4.  Fare clic su **Compila**. Unity avvierà una *Esplora file,* in cui è necessario creare e quindi selezionare una cartella in cui compilare l'app. Creare la cartella e assegnare alla cartella il nome **App**. Quindi, con la **cartella App** selezionata, fare clic su **Seleziona cartella**.

5.  Unity inizierà a compilare il progetto nella **cartella App.**

6.  Al termine della compilazione di Unity (potrebbe essere necessario del tempo), verrà aperta una finestra **Esplora file** nel percorso della compilazione (controllare la barra delle applicazioni, perché potrebbe non essere sempre visualizzata sopra le finestre, ma verrà notificata l'aggiunta di una nuova finestra).

7.  Per eseguire la distribuzione in Microsoft HoloLens, è necessario l'indirizzo IP del dispositivo (per la distribuzione remota) e assicurarsi che sia impostata anche la **modalità sviluppatore.** Per eseguire questa operazione:

    1.  Mentre si indossa il HoloLens, aprire il **Impostazioni**.

    2.  Passare a **Network & Internet** Wi-Fi Advanced Options (Opzioni avanzate  >  **Wi-Fi Internet)**  >  

    3.  Prendere nota **dell'indirizzo IPv4.**

    4.  Tornare quindi a Impostazioni **e** quindi a Update **& Security**  >  **for Developers**

    5.  Impostare **la modalità sviluppatore** *su*.

8.  Passare alla nuova build di Unity (cartella **App)** e aprire il file di soluzione con **Visual Studio**.

9.  In Configurazione soluzione selezionare **Debug**.

10. In Piattaforma soluzione selezionare **x86, Computer remoto**. Verrà richiesto di inserire l'indirizzo **IP** di un dispositivo remoto (la Microsoft HoloLens, in questo caso, che è stata notata).

    ![](images/AzureLabs-Lab310-43.png)

11. Passare al menu **Compila** e fare clic su **Distribuisci soluzione** per eseguire il sideload dell'applicazione nel HoloLens.

12. L'app dovrebbe ora essere visualizzata nell'elenco delle app installate nel Microsoft HoloLens, pronto per l'avvio.

### <a name="to-use-the-application"></a>Per usare l'applicazione:

* Esaminare un oggetto di cui è stato creato il training con il servizio **Azure Visione personalizzata,** rilevamento oggetti e usare il **movimento Tocco**.
* Se l'oggetto viene rilevato correttamente, verrà visualizzato un testo etichetta con spazio del mondo con il nome del tag. 

> [!IMPORTANT]
> Ogni volta che si acquisisce una foto e la si invia al servizio, è possibile tornare alla pagina Servizio ed eseguire nuovamente il training del servizio con le immagini appena acquisite. All'inizio, probabilmente sarà necessario correggere anche *i relimiti* per essere più accurati ed eseguire nuovamente il training del servizio.

> [!NOTE]
> Il testo etichetta inserito potrebbe non essere visualizzato vicino all'oggetto quando i sensori Microsoft HoloLens e/o SpatialTrackingComponent in Unity non posizionano i collisori appropriati, rispetto agli oggetti reali. Provare a usare l'applicazione su una superficie diversa, se questo è il caso.

## <a name="your-custom-vision-object-detection-application"></a>Applicazione Visione personalizzata, Rilevamento oggetti

È stata compilata un'app di realtà mista che sfrutta l'API rilevamento oggetti di Azure Visione personalizzata, in grado di riconoscere un oggetto da un'immagine e quindi fornire una posizione approssimativa per tale oggetto nello spazio 3D.

![](images/AzureLabs-Lab310-00.png)

## <a name="bonus-exercises"></a>Esercizi aggiuntivi

### <a name="exercise-1"></a>Esercizio 1

Aggiungendo all'etichetta di testo, usare un cubo semitrasparente per eseguire il wrapping dell'oggetto reale in un rettangolo di *selezione* 3D.

### <a name="exercise-2"></a>Esercizio 2

Eseguire il training del Visione personalizzata per riconoscere più oggetti.

### <a name="exercise-3"></a>Esercizio 3

Riprodurre un suono quando un oggetto viene riconosciuto.

### <a name="exercise-4"></a>Esercizio 4

Usare l'API per eseguire nuovamente il training del servizio con le stesse immagini analizzate dall'app, in modo da rendere il servizio più accurato (eseguire contemporaneamente sia la stima che il training).
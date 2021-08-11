---
title: HoloLens (prima generazione) e Azure 302 - Visione computer
description: Completa questo corso per imparare a riconoscere il contenuto visivo all'interno di un'immagine fornita, usando Azure Visione artificiale in un'applicazione di realtà mista.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure, realtà mista, academy, unity, esercitazione, API, visione computer, hololens, immersive, vr, Windows 10, Visual Studio
ms.openlocfilehash: 5cac40c2613187776ea9ec5ba1268f1422a084d32322e9c4aca6742ed75d05b2
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115226038"
---
# <a name="hololens-1st-gen-and-azure-302-computer-vision"></a>HoloLens (prima generazione) e Azure 302: Visione computer

<br>

>[!NOTE]
>Le esercitazioni di Mixed Reality Academy sono state progettate in base a HoloLens (prima generazione) e ai visori VR immersive di realtà mista.  Pertanto, riteniamo importante lasciarle a disposizione degli sviluppatori a cui serve ancora materiale sussidiario per lo sviluppo di questi dispositivi.  Queste esercitazioni **_non_** verranno aggiornate con i set di strumenti o le interazioni più recenti usati per HoloLens 2.  Rimarranno invariate per consentire di continuare a lavorare sui dispositivi supportati. In futuro verrà pubblicata una nuova serie di esercitazioni che illustrano come sviluppare per HoloLens 2.  Questa comunicazione verrà aggiornata con un collegamento a tali esercitazioni al momento della pubblicazione.

<br>

In questo corso si apprenderà come riconoscere il contenuto visivo all'interno di un'immagine fornita, usando le funzionalità di azure Visione artificiale in un'applicazione di realtà mista.

I risultati del riconoscimento verranno visualizzati come tag descrittivi. È possibile usare questo servizio senza dover eseguire il training di un modello di Machine Learning. Se l'implementazione richiede il training di un modello di Machine Learning, [vedere MR e Azure 302b.](mr-azure-302b.md)

![risultato del lab](images/AzureLabs-Lab2-000.png)

Microsoft Visione artificiale è un set di API progettate per fornire agli sviluppatori l'elaborazione e l'analisi delle immagini (con informazioni restituite), usando algoritmi avanzati, il tutto dal cloud. Gli sviluppatori caricano un'immagine o un URL di immagine e gli algoritmi dell'API Microsoft Visione artificiale analizzano il contenuto visivo in base agli input scelti dall'utente, che possono quindi restituire informazioni, tra cui l'identificazione del tipo e della qualità di un'immagine, il rilevamento dei visi umani (restituzione delle coordinate) e l'assegnazione di tag o la categorizzazione delle immagini. Per altre informazioni, visitare la pagina [dell'API Visione artificiale Azure](https://azure.microsoft.com/services/cognitive-services/computer-vision/).

Dopo aver completato questo corso, si avrà un'applicazione HoloLens realtà mista, che sarà in grado di eseguire le operazioni seguenti:

1.  Usando il movimento Tocco, la fotocamera del HoloLens acquisisce un'immagine.
2.  L'immagine verrà inviata al servizio API Visione artificiale Azure. 
3.  Gli oggetti riconosciuti verranno elencati in un semplice gruppo di interfaccia utente posizionato nella scena Unity.

Nell'applicazione è necessario sapere come integrare i risultati con la progettazione. Questo corso è stato progettato per illustrare come integrare un servizio di Azure con il progetto Unity. È compito dell'utente usare le conoscenze acquisite in questo corso per migliorare l'applicazione di realtà mista.

## <a name="device-support"></a>Supporto di dispositivi

<table>
<tr>
<th>Corso</th><th style="width:150px"> <a href="/hololens/hololens1-hardware">HoloLens</a></th><th style="width:150px"> <a href="../../../discover/immersive-headset-hardware-details.md">Visori VR immersive</a></th>
</tr><tr>
<td> MR e Azure 302: Visione artificiale</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> Anche se questo corso è in particolare in HoloLens, è anche possibile applicare le informazioni apprese in questo corso ai visori VR Windows Mixed Reality immersive. Poiché i visori VR immersive non hanno fotocamere accessibili, è necessaria una fotocamera esterna connessa al PC. Man mano che si segue il corso, si vedranno note sulle modifiche che potrebbe essere necessario apportare per supportare visori VR immersive.

## <a name="prerequisites"></a>Prerequisiti

> [!NOTE]
> Questa esercitazione è destinata agli sviluppatori che hanno esperienza di base con Unity e C#. Tenere inoltre presente che i prerequisiti e le istruzioni scritte all'interno di questo documento rappresentano ciò che è stato testato e verificato al momento della stesura di questo documento (maggio 2018). È possibile usare il software più recente, come indicato nell'articolo Installare gli strumenti, anche se non si presuppone che le informazioni contenute in questo corso corrispondano perfettamente a quelle disponibili nel software più recente rispetto a quelle elencate di seguito. [](../../install-the-tools.md)

Per questo corso è consigliabile usare l'hardware e il software seguenti:

- Un PC di sviluppo, [compatibile con le Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) per lo sviluppo di visori VR immersive
- [Windows 10 Fall Creators Update (o versione successiva) con la modalità sviluppatore abilitata](../../install-the-tools.md#installation-checklist)
- [L'SDK Windows 10 più recente](../../install-the-tools.md#installation-checklist)
- [Unity 2017.4](../../install-the-tools.md#installation-checklist)
- [Visual Studio 2017](../../install-the-tools.md#installation-checklist)
- Un [visore VR o](../../../discover/immersive-headset-hardware-details.md) un visore [Microsoft HoloLens](/hololens/hololens1-hardware) VR Windows Mixed Reality con la modalità sviluppatore abilitata
- Una fotocamera connessa al PC (per lo sviluppo di visori VR immersive)
- Accesso a Internet per l'installazione di Azure e il Visione artificiale'API

## <a name="before-you-start"></a>Prima di iniziare

1.  Per evitare di riscontrare problemi durante la compilazione di questo progetto, è consigliabile creare il progetto indicato in questa esercitazione in una cartella radice o quasi (i percorsi di cartelle lunghi possono causare problemi in fase di compilazione).
2.  Configurare e testare l'HoloLens. Se è necessario supporto per la configurazione del HoloLens, vedere [l'articolo HoloLens configurazione.](/hololens/hololens-setup) 
3.  È buona idea eseguire la calibrazione e l'ottimizzazione dei sensori quando si inizia a sviluppare una nuova app HoloLens (a volte può essere utile eseguire tali attività per ogni utente). 

Per informazioni sulla calibrazione, fare clic su questo [collegamento all'HoloLens calibrazione.](/hololens/hololens-calibration#hololens-2)

Per informazioni sull'ottimizzazione dei sensori, fare clic su questo collegamento [all'HoloLens sull'ottimizzazione dei sensori.](/hololens/hololens-updates)

## <a name="chapter-1--the-azure-portal"></a>Capitolo 1: Portale di Azure

Per usare il *Visione artificiale API* in Azure, è necessario configurare un'istanza del servizio in modo che sia resa disponibile per l'applicazione.

1.  Accedere prima di tutto al portale [di Azure.](https://portal.azure.com) 

    > [!NOTE]
    > Se non si ha già un account Azure, è necessario crearne uno. Se si sta seguendo questa esercitazione in una situazione di classe o di lab, chiedere all'insegnante o a uno dei protori di assistenza per la configurazione del nuovo account.

2.  Dopo aver eseguito l'accesso, fare clic su **Nuovo** nell'angolo in alto a sinistra, cercare *Visione artificiale aPI* e fare clic su **Invio.**

    ![Creare una nuova risorsa in Azure](images/AzureLabs-Lab2-00.png)

    > [!NOTE]
    > La parola **Nuovo** potrebbe essere stata sostituita **con Crea una risorsa** nei portali più nuovi.
 
3.  La nuova pagina fornirà una descrizione del servizio *VISIONE ARTIFICIALE API.* Nella parte inferiore sinistra di questa pagina selezionare il **pulsante Crea** per creare un'associazione con questo servizio.

    ![Informazioni sul servizio API Visione computer](images/AzureLabs-Lab2-01.png)
 
4.  Dopo aver fatto clic su **Crea:**

    1. Inserire il nome **desiderato per** questa istanza del servizio.
    2. Selezionare una **Sottoscrizione**.
    3. Selezionare il **piano tariffario** appropriato. Se questa è la prima volta che si crea un servizio *API Visione artificiale,* dovrebbe essere disponibile un livello gratuito (denominato F0).
    4. Scegliere un **gruppo di risorse** o crearne uno nuovo. Un gruppo di risorse consente di monitorare, controllare l'accesso, effettuare il provisioning e gestire la fatturazione per una raccolta di asset di Azure. È consigliabile mantenere tutti i servizi di Azure associati a un singolo progetto (ad esempio, questi lab) in un gruppo di risorse comune. 

        > Per altre informazioni sui gruppi di risorse di Azure, vedere [l'articolo sui gruppi di risorse.](/azure/azure-resource-manager/resource-group-portal)

    5. Determinare la località per il gruppo di risorse (se si sta creando un nuovo gruppo di risorse). La posizione sarebbe idealmente nell'area in cui verrebbe eseguita l'applicazione. Alcuni asset di Azure sono disponibili solo in determinate aree.

    6. È anche necessario confermare di aver compreso i termini e le condizioni applicati al servizio.
    7. Fare clic su Crea.

        ![Informazioni sulla creazione del servizio](images/AzureLabs-Lab2-02.png)

5.  Dopo aver fatto clic su **Crea**, sarà necessario attendere la creazione del servizio. L'operazione potrebbe richiedere un minuto.
6.  Una volta creata l'istanza del servizio, nel portale verrà visualizzata una notifica.

    ![Visualizzare la nuova notifica per il nuovo servizio](images/AzureLabs-Lab2-03.png) 
 
7.  Fare clic sulla notifica per esplorare la nuova istanza del servizio. 

    ![Selezionare il pulsante Vai alla risorsa.](images/AzureLabs-Lab2-04.png)
 
8. Fare clic **sul pulsante Vai alla** risorsa nella notifica per esplorare la nuova istanza del servizio. Verrà visualizzato il nuovo servizio API Visione artificiale istanza del servizio API. 

    ![Nuova immagine Visione artificiale servizio API](images/AzureLabs-Lab2-05.png)
 
9.  In questa esercitazione l'applicazione dovrà effettuare chiamate al servizio, operazione eseguita tramite la chiave di sottoscrizione del servizio.
10. Nella  pagina Avvio rapido del servizio *API Visione artificiale* passare al primo *passaggio,* Afferrare le chiavi e fare clic su **Chiavi.** A tale scopo, è anche possibile fare clic sul collegamento ipertestuale blu Chiavi, che si trova nel menu di spostamento dei servizi, con l'icona della chiave. Verranno così rivelate le chiavi *del servizio*.
11. Prendere una copia di una delle chiavi visualizzate, che sarà necessaria più avanti nel progetto. 

12. Tornare alla pagina *Avvio rapido e* recuperare l'endpoint. Tenere presente che il codice potrebbe essere diverso, a seconda dell'area (che in caso contrario sarà necessario apportare una modifica al codice in un secondo momento). Copiare questo endpoint per usarlo in un secondo momento:

    ![Nuovo servizio API Visione artificiale](images/AzureLabs-Lab2-05-5.png)

    > [!TIP]
    > È possibile controllare quali sono i vari endpoint [QUI.](https://westus.dev.cognitive.microsoft.com/docs/services/56f91f2d778daf23d8ec6739/operations/56f91f2e778daf14a499e1fa) 

## <a name="chapter-2--set-up-the-unity-project"></a>Capitolo 2: Configurare il progetto Unity

Di seguito è riportata una configurazione tipica per lo sviluppo con la realtà mista e, di conseguenza, è un buon modello per altri progetti.

1.  Aprire *Unity e* fare clic su New **(Nuovo).** 

    ![Avviare un nuovo progetto Unity.](images/AzureLabs-Lab2-06.png)

2.  È ora necessario specificare un nome Project Unity. Inserire **MR_ComputerVision**. Assicurarsi che il tipo di progetto sia impostato su **3D.** Impostare Il **percorso su** un percorso appropriato per l'utente(tenere presente che più vicino alle directory radice è meglio). Fare quindi clic **su Crea progetto**.

    ![Specificare i dettagli per il nuovo progetto Unity.](images/AzureLabs-Lab2-07.png)

3.  Con Unity aperto, è opportuno controllare che l'editor di **script predefinito** sia impostato **su Visual Studio**. Passare a **Modifica > preferenze** e quindi dalla nuova finestra passare a Strumenti **esterni.** Modificare **External Script Editor in** Visual Studio **2017**. Chiudere la **finestra** Preferenze.

    ![Aggiornare le preferenze dell'editor di script.](images/AzureLabs-Lab2-08.png)

4.  Passare quindi a **File > Build Impostazioni** e selezionare Universal Windows **Platform** e quindi fare clic sul pulsante **Switch Platform** (Cambia piattaforma) per applicare la selezione.

    ![Compilare Impostazioni finestra, passare dalla piattaforma alla piattaforma UWP.](images/AzureLabs-Lab2-10.png)

5.  Sempre in **File > Build Impostazioni** e assicurarsi che:

    1. **Dispositivo di destinazione** impostato su **HoloLens**

        > Per i visori VR immersive, impostare **Dispositivo di destinazione** su Qualsiasi *dispositivo.*

    2. **Il tipo di** compilazione è impostato **su D3D**
    3. **L'SDK** è impostato su **Più recente installato**
    4. **Visual Studio versione è** impostata su **Versione più recente installata**
    5. **Build and Run (Compilazione** ed esecuzione) è impostato **su Local Machine (Computer locale)**
    6. Salvare la scena e aggiungerla alla compilazione.

        1. A tale scopo, selezionare **Add Open Scenes (Aggiungi scene aperte).** Verrà visualizzata una finestra di salvataggio.
        
            ![Fare clic sul pulsante Aggiungi scene aperte](images/AzureLabs-Lab2-11.png)

        2. Creare una nuova cartella per questa ed eventuali  scene future, quindi selezionare il pulsante Nuova cartella. Per creare una nuova cartella, assegnare alla nuova cartella il nome **Scenes**.

            ![Creare una nuova cartella di script](images/AzureLabs-Lab2-12.png)

        3. Aprire la cartella **Scenes appena** creata e quindi nel campo di testo *Nome file*: digitare **MR_ComputerVisionScene** e quindi fare clic su **Salva.**

            ![Assegnare un nome alla nuova scena.](images/AzureLabs-Lab2-13.png)

            > Tenere presente che è necessario salvare le scene di Unity all'interno *della cartella Assets,* perché devono essere associate al Project Unity. La creazione della cartella scenes (e di altre cartelle simili) è un modo tipico per strutturare un progetto Unity.

    7. Le impostazioni rimanenti, in *Build Impostazioni*, per il momento devono essere lasciato come predefinite.

6. Nella finestra *build Impostazioni* fare clic sul pulsante **Player Impostazioni** per aprire il pannello correlato nello spazio in cui si trova *il controllo.* 

    ![Aprire le impostazioni del lettore.](images/AzureLabs-Lab2-14.png)

7. In questo pannello è necessario verificare alcune impostazioni:

    1. Nella scheda **Altro Impostazioni:**

        1. **La versione del runtime di** scripting deve essere **Stabile** (equivalente a .NET 3.5).
        2. **Il back-end di** scripting deve **essere .NET**
        3. **Il livello di compatibilità dell'API** **deve essere .NET 4.6**

            ![Aggiornare altre impostazioni.](images/AzureLabs-Lab2-15.png)
      
    2. **All'interno della Impostazioni** pubblicazione, in **Funzionalità** selezionare:

        1. **InternetClient**
        2. **Webcam**

            ![Aggiornamento delle impostazioni di pubblicazione.](images/AzureLabs-Lab2-16.png)

    3. Più in basso nel pannello, in **XR Impostazioni** (disponibile sotto **Pubblica Impostazioni),** selezionare **Virtual Reality Supported**(Realtà virtuale supportata) e assicurarsi che sia stato aggiunto **Windows Mixed Reality SDK.**

        ![Aggiornare il Impostazioni X R.](images/AzureLabs-Lab2-17.png)

8.  Tornare alla *compilazione Impostazioni* i _progetti C# Unity_ non sono più disattivati; Selezionare la casella di controllo accanto a questo. 
9.  Chiudere la finestra Build Settings (Impostazioni di compilazione).
10. Salvare la scena e Project **(FILE > SAVE SCENE/FILE > SAVE PROJECT**).

## <a name="chapter-3--main-camera-setup"></a>Capitolo 3: Configurazione della fotocamera principale

> [!IMPORTANT]
> Se si vuole ignorare il componente Di configurazione di *Unity* di questo corso e continuare direttamente con il [](https://docs.unity3d.com/Manual/AssetPackages.html)codice, è possibile scaricare questo file con estensione [unitypackage,](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302%20-%20Computer%20vision/Azure-MR-302.unitypackage)importarlo nel progetto come pacchetto personalizzato e quindi continuare dal capitolo [5.](#chapter-5--create-the-resultslabel-class)

1.  Nel pannello *Hierarchy (Gerarchia)* selezionare **Main Camera (Fotocamera principale).** 
2.  Una volta selezionato, sarà possibile visualizzare tutti i componenti della fotocamera **principale** nel pannello *inspector.*

    1. **L'oggetto Camera** deve essere denominato **Main Camera (si** noti l'ortografia).
    2. Il tag della **fotocamera principale** deve essere impostato su **MainCamera** (si noti l'ortografia).
    3. Assicurarsi che **Posizione trasformazione** sia impostato su **0, 0, 0**
    4. Impostare **Clear Flags (Cancella flag)** **su Solid Color (Colore** a tinta unita) (ignorare questa impostazione per il visore VR immersive).
    5. Impostare Colore **di sfondo** del componente fotocamera su **Nero, Alfa 0 (codice esadecimale: #00000000)** (ignorare questa impostazione per il visore VR immersive).

        ![Aggiornare i componenti della fotocamera.](images/AzureLabs-Lab2-18.png)
 
3.  Sarà quindi necessario creare un semplice oggetto "Cursor" collegato alla fotocamera **principale,** che consente di posizionare l'output di analisi delle immagini durante l'esecuzione dell'applicazione. Questo cursore determinerà il punto centrale dello stato attivo della fotocamera.

Per creare il cursore:

1.  Nel pannello *Hierarchy (Gerarchia)* fare clic con il pulsante destro **del mouse su Main Camera (Fotocamera principale).** In **3D Object (Oggetto 3D)** fare clic **su Sphere (Sfera).**

    ![Selezionare l'oggetto Cursore.](images/AzureLabs-Lab2-19.png)
 
2.  Rinominare **Sphere** in **Cursor** (fare doppio clic sull'oggetto Cursor o premere il pulsante della tastiera "F2" con l'oggetto selezionato) e assicurarsi che si trovi come elemento figlio della **fotocamera principale.**

3.  Nel pannello *Gerarchia fare* clic con il pulsante sinistro del **mouse sul cursore**. Con l'opzione Cursore selezionata, modificare le variabili seguenti nel *pannello Inspector (Controllo):*

    1. Impostare *Posizione trasformazione* su **0, 0, 5**
    2. Impostare Scala *su* **0,02, 0,02, 0,02**

        ![Aggiornare le proprietà Transform Position (Posizione trasformazione) e Scale (Scala).](images/AzureLabs-Lab2-20.png)
  
## <a name="chapter-4--setup-the-label-system"></a>Capitolo 4: Configurare il sistema di etichettatura

Dopo aver acquisito un'immagine con la fotocamera HoloLens, tale immagine verrà inviata all'istanza del servizio API di *Azure Visione artificiale* per l'analisi. 

I risultati di tale analisi saranno un elenco di oggetti riconosciuti denominati **Tag.** 

Si useranno le etichette (come testo 3D nello spazio mondiale) per visualizzare questi tag nella posizione in cui è stata scattata la foto.

La procedura seguente illustra come configurare **l'oggetto Label.**

1.  Fare clic con il pulsante destro del mouse in un punto qualsiasi del pannello gerarchia (la posizione non è importante a questo punto), in Oggetto **3D** aggiungere un testo **3D.** Assegnare il **nome LabelText**.

    ![Creare un oggetto Testo 3D.](images/AzureLabs-Lab2-21.png)
 
2.  Nel pannello *Hierarchy (Gerarchia)* fare clic con il pulsante destro **del mouse su LabelText.** Dopo aver **selezionato LabelText,** modificare le variabili seguenti nel *pannello Inspector*:

    1. Impostare **Posizione** su **0,0,0**
    2. Impostare Scale **(Scala)** **su 0.01, 0.01, 0.01**
    3. Nel componente **Mesh testo**:
    4. Sostituire tutto il testo **all'interno di Text** con "..."        
    5. Impostare **l'ancoraggio** **al centro**
    6. Impostare Allineamento **al** **centro**
    7. Impostare Dimensioni **scheda** su **4**
    8. Impostare Dimensioni **carattere** su **50**
    9. Impostare **Colore su** **#FFFFFFFF**

    ![Componente di testo](images/AzureLabs-Lab2-21-5.png)

3.  Trascinare **LabelText** da *Hierarchy Panel (Pannello gerarchia)* in Asset Folder *(Cartella asset)* all'interno *di Project Panel*. In questo modo **LabelText sarà** un prefab, in modo che sia possibile crearne un'istanza nel codice.

    ![Creare un prefab dell'oggetto LabelText.](images/AzureLabs-Lab2-22.png)
 
4.  È necessario eliminare **LabelText** dal pannello *della gerarchia,* in modo che non sia visualizzato nella scena di apertura. Poiché si tratta ora di un prefab, che verrà chiamato per le singole istanze dalla cartella Assets, non è necessario mantenerlo all'interno della scena. 
5.  La struttura dell'oggetto finale nel *pannello gerarchia* dovrebbe essere simile a quella illustrata nell'immagine seguente:

    ![Struttura finale del pannello della gerarchia.](images/AzureLabs-Lab2-23.png)

## <a name="chapter-5--create-the-resultslabel-class"></a>Capitolo 5: Creare la classe ResultsLabel

Il primo script da creare è la *classe ResultsLabel,* responsabile degli elementi seguenti: 

- Creazione delle etichette nello spazio mondo appropriato, rispetto alla posizione della fotocamera.
- Visualizzazione dei tag di Image Anaysis.

Per creare questa classe: 

1.  Fare clic con il pulsante destro *del mouse nel pannello Project,* quindi scegliere Crea > **cartella**. Assegnare alla cartella il nome **Scripts**. 

    ![Creare la cartella degli script.](images/AzureLabs-Lab2-24.png)

2.  Con la **cartella Scripts** create (Script) fare doppio clic su di essa per aprirla. All'interno di tale cartella fare clic con il pulsante destro del mouse e **scegliere Crea >** script **C#.** Assegnare allo script il *nome ResultsLabel*. 

3.  Fare doppio clic sul nuovo script *ResultsLabel* per aprirlo con **Visual Studio**.

4.  All'interno della classe inserire il codice seguente nella *classe ResultsLabel:*

    ```csharp
        using System.Collections.Generic;
        using UnityEngine;

        public class ResultsLabel : MonoBehaviour
        {   
            public static ResultsLabel instance;

            public GameObject cursor;

            public Transform labelPrefab;

            [HideInInspector]
            public Transform lastLabelPlaced;

            [HideInInspector]
            public TextMesh lastLabelPlacedText;

            private void Awake()
            {
                // allows this instance to behave like a singleton
                instance = this;
            }

            /// <summary>
            /// Instantiate a Label in the appropriate location relative to the Main Camera.
            /// </summary>
            public void CreateLabel()
            {
                lastLabelPlaced = Instantiate(labelPrefab, cursor.transform.position, transform.rotation);

                lastLabelPlacedText = lastLabelPlaced.GetComponent<TextMesh>();

                // Change the text of the label to show that has been placed
                // The final text will be set at a later stage
                lastLabelPlacedText.text = "Analysing...";
            }

            /// <summary>
            /// Set the Tags as Text of the last Label created. 
            /// </summary>
            public void SetTagsToLastLabel(Dictionary<string, float> tagsDictionary)
            {
                lastLabelPlacedText = lastLabelPlaced.GetComponent<TextMesh>();

                // At this point we go through all the tags received and set them as text of the label
                lastLabelPlacedText.text = "I see: \n";

                foreach (KeyValuePair<string, float> tag in tagsDictionary)
                {
                    lastLabelPlacedText.text += tag.Key + ", Confidence: " + tag.Value.ToString("0.00 \n");
                }    
            }
        }
    ```

6.  Assicurarsi di salvare le modifiche in *Visual Studio* prima di tornare a *Unity.*
7.  *Nell'editor di Unity* fare clic e trascinare la classe *ResultsLabel* dalla cartella **Scripts** all'oggetto **Fotocamera** principale nel *pannello Gerarchia*.
8.  Fare clic sulla **fotocamera principale** e osservare il *pannello Inspector*.

Si noterà che dallo script appena trascinato nella fotocamera sono presenti due campi: **Cursore** ed **Etichetta Prefab**.

9.  Trascinare l'oggetto **denominato Cursore** dal pannello *Gerarchia* nello slot **denominato Cursore**, come illustrato nell'immagine seguente.
10. Trascinare l'oggetto **denominato LabelText** dalla cartella *Assets* nel *pannello Project* nello slot denominato **Label Prefab**, come illustrato nell'immagine seguente. 

    ![Impostare le destinazioni di riferimento in Unity.](images/AzureLabs-Lab2-25.png)

## <a name="chapter-6--create-the-imagecapture-class"></a>Capitolo 6: Creare la classe ImageCapture

La classe successiva che si creerà è *la classe ImageCapture.* Questa classe è responsabile di:

-   Acquisizione di un'immagine usando HoloLens fotocamera e archiviazione nella cartella dell'app.
-   Acquisizione di movimenti tocco dall'utente.

Per creare questa classe: 

1.  Passare alla **cartella Scripts** creata in precedenza. 
2.  Fare clic con il pulsante destro del mouse **all'interno della cartella Create > C# Script**. Chiamare lo script *ImageCapture*. 
3.  Fare doppio clic sul nuovo script *ImageCapture* per aprirlo con **Visual Studio**.
4.  Aggiungere gli spazi dei nomi seguenti all'inizio del file:

    ```csharp
        using System.IO;
        using System.Linq;
        using UnityEngine;
        using UnityEngine.XR.WSA.Input;
        using UnityEngine.XR.WSA.WebCam;
    ```

5.  Aggiungere quindi le variabili seguenti all'interno *della classe ImageCapture,* sopra il *metodo Start():*

    ```csharp
        public static ImageCapture instance; 
        public int tapsCount;
        private PhotoCapture photoCaptureObject = null;
        private GestureRecognizer recognizer;
        private bool currentlyCapturing = false;
    ```
 
La **variabile tapsCount** archivierà il numero di movimenti di tocco acquisiti dall'utente. Questo numero viene usato nella denominazione delle immagini acquisite.

6.  È ora necessario aggiungere il codice per i metodi *Awake()* e *Start().* Questi vengono chiamati quando la classe viene inizializzata:

    ```csharp
        private void Awake()
        {
            // Allows this instance to behave like a singleton
            instance = this;
        }

        void Start()
        {
            // subscribing to the HoloLens API gesture recognizer to track user gestures
            recognizer = new GestureRecognizer();
            recognizer.SetRecognizableGestures(GestureSettings.Tap);
            recognizer.Tapped += TapHandler;
            recognizer.StartCapturingGestures();
        }
    ```

7.  Implementare un gestore che verrà chiamato quando si verifica un movimento Di tocco. 

    ```csharp
        /// <summary>
        /// Respond to Tap Input.
        /// </summary>
        private void TapHandler(TappedEventArgs obj)
        {
            // Only allow capturing, if not currently processing a request.
            if(currentlyCapturing == false)
            {
                currentlyCapturing = true;
            
                // increment taps count, used to name images when saving
                tapsCount++;

                // Create a label in world space using the ResultsLabel class
                ResultsLabel.instance.CreateLabel();

                // Begins the image capture and analysis procedure
                ExecuteImageCaptureAndAnalysis();
            }
        }
    ```
 
Il *metodo TapHandler()* incrementa il numero di tocchi acquisiti dall'utente e usa la posizione corrente del cursore per determinare dove posizionare una nuova etichetta.

Questo metodo chiama quindi il *metodo ExecuteImageCaptureAndAnalysis()* per iniziare la funzionalità principale dell'applicazione.

8.  Dopo che un'immagine è stata acquisita e archiviata, verranno chiamati i gestori seguenti. Se il processo ha esito positivo, il risultato viene passato a *VisionManager* (che è ancora necessario creare) per l'analisi.

    ```csharp
        /// <summary>
        /// Register the full execution of the Photo Capture. If successful, it will begin 
        /// the Image Analysis process.
        /// </summary>
        void OnCapturedPhotoToDisk(PhotoCapture.PhotoCaptureResult result)
        {
            // Call StopPhotoMode once the image has successfully captured
            photoCaptureObject.StopPhotoModeAsync(OnStoppedPhotoMode);
        }

        void OnStoppedPhotoMode(PhotoCapture.PhotoCaptureResult result)
        {
            // Dispose from the object in memory and request the image analysis 
            // to the VisionManager class
            photoCaptureObject.Dispose();
            photoCaptureObject = null;
            StartCoroutine(VisionManager.instance.AnalyseLastImageCaptured()); 
        }
    ```
 
9.  Aggiungere quindi il metodo utilizzato dall'applicazione per avviare il processo di acquisizione delle immagini e archiviare l'immagine.

    ```csharp    
        /// <summary>    
        /// Begin process of Image Capturing and send To Azure     
        /// Computer Vision service.   
        /// </summary>    
        private void ExecuteImageCaptureAndAnalysis()  
        {    
            // Set the camera resolution to be the highest possible    
            Resolution cameraResolution = PhotoCapture.SupportedResolutions.OrderByDescending((res) => res.width * res.height).First();    

            Texture2D targetTexture = new Texture2D(cameraResolution.width, cameraResolution.height);
    
            // Begin capture process, set the image format    
            PhotoCapture.CreateAsync(false, delegate (PhotoCapture captureObject)    
            {    
                photoCaptureObject = captureObject;    
                CameraParameters camParameters = new CameraParameters();    
                camParameters.hologramOpacity = 0.0f;    
                camParameters.cameraResolutionWidth = targetTexture.width;    
                camParameters.cameraResolutionHeight = targetTexture.height;    
                camParameters.pixelFormat = CapturePixelFormat.BGRA32;
    
                // Capture the image from the camera and save it in the App internal folder    
                captureObject.StartPhotoModeAsync(camParameters, delegate (PhotoCapture.PhotoCaptureResult result)
                {    
                    string filename = string.Format(@"CapturedImage{0}.jpg", tapsCount);
    
                    string filePath = Path.Combine(Application.persistentDataPath, filename);

                    VisionManager.instance.imagePath = filePath;
    
                    photoCaptureObject.TakePhotoAsync(filePath, PhotoCaptureFileOutputFormat.JPG, OnCapturedPhotoToDisk);

                    currentlyCapturing = false;
                });   
            });    
        }
    ```
 
> [!WARNING] 
> A questo punto si noterà un errore visualizzato nel pannello della *console dell'editor di Unity.* Questo perché il codice fa riferimento alla *classe VisionManager* che verrà creata nel capitolo successivo.

## <a name="chapter-7--call-to-azure-and-image-analysis"></a>Capitolo 7: Chiamata ad Azure e all'analisi delle immagini

L'ultimo script da creare è la *classe VisionManager.* 

Questa classe è responsabile di:

-   Caricamento dell'immagine più recente acquisita come matrice di byte.
-   Invio della matrice di byte all'istanza del *servizio API di Azure Visione artificiale* per l'analisi.
-   Ricezione della risposta come stringa JSON.
-   Deserializzare la risposta e passare i tag risultanti alla *classe ResultsLabel.*
 
Per creare questa classe:

1.  Fare doppio clic sulla **cartella** Script per aprirla. 
2.  Fare clic con il pulsante destro del **mouse nella cartella Script** e scegliere Crea > script **C#.** Assegnare allo script il *nome VisionManager*. 
3.  Fare doppio clic sul nuovo script per aprirlo con Visual Studio.
4.  Aggiornare gli spazi dei nomi in modo che siano uguali ai seguenti, nella parte superiore della *classe VisionManager:*

    ```csharp
        using System;
        using System.Collections;
        using System.Collections.Generic;
        using System.IO;
        using UnityEngine;
        using UnityEngine.Networking;
    ```
 
5.  Nella parte superiore dello *script,* all'interno della classe *VisionManager* (sopra  il *metodo Start()),* è ora necessario creare due classi che rappresenteranno la risposta JSON deserializzata da Azure:

    ```csharp
        [System.Serializable]
        public class TagData
        {
            public string name;
            public float confidence;
        }

        [System.Serializable]
        public class AnalysedObject
        {
            public TagData[] tags;
            public string requestId;
            public object metadata;
        }
    ```

    > [!NOTE] 
    > Per poter essere deserializzate con le librerie Unity, le classi *TagData* e *AnalysedObject* devono avere l'attributo *[System.Serializable]* aggiunto prima della dichiarazione.

6.  Nella classe VisionManager è necessario aggiungere le variabili seguenti:

    ```csharp
        public static VisionManager instance;

        // you must insert your service key here!    
        private string authorizationKey = "- Insert your key here -";    
        private const string ocpApimSubscriptionKeyHeader = "Ocp-Apim-Subscription-Key";
        private string visionAnalysisEndpoint = "https://westus.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags";   // This is where you need to update your endpoint, if you set your location to something other than west-us.
  
        internal byte[] imageBytes;

        internal string imagePath;
    ```

    > [!WARNING] 
    > Assicurarsi di inserire la **chiave di autenticazione** nella variabile **authorizationKey.** All'inizio di questo corso **sarà stata specificata** la chiave di autenticazione, capitolo [1.](#chapter-1--the-azure-portal)

    > [!WARNING] 
    > La **variabile visionAnalysisEndpoint** potrebbe essere diversa da quella specificata in questo esempio. **L'area Stati Uniti occidentali** si riferisce esclusivamente alle istanze del servizio create per l'area Stati Uniti occidentali. Aggiornare questa opzione con [l'URL dell'endpoint.](https://westus.dev.cognitive.microsoft.com/docs/services/56f91f2d778daf23d8ec6739/operations/56f91f2e778daf14a499e1fa) Di seguito sono riportati alcuni esempi di un aspetto simile al seguente:
    > - Europa occidentale: `https://westeurope.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags`
    > - Asia sud-orientale: `https://southeastasia.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags`
    > - Australia orientale: `https://australiaeast.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags`

7.  È ora necessario aggiungere il codice per Awake. 

    ```csharp
        private void Awake()
        {
            // allows this instance to behave like a singleton
            instance = this;
        }
    ```

8.  Aggiungere quindi la coroutine (con il metodo di flusso statico sottostante), che oquiderà i risultati dell'analisi dell'immagine acquisita dalla *classe ImageCapture.* 

    ```csharp
        /// <summary>
        /// Call the Computer Vision Service to submit the image.
        /// </summary>
        public IEnumerator AnalyseLastImageCaptured()
        {
            WWWForm webForm = new WWWForm();
            using (UnityWebRequest unityWebRequest = UnityWebRequest.Post(visionAnalysisEndpoint, webForm))
            {
                // gets a byte array out of the saved image
                imageBytes = GetImageAsByteArray(imagePath);
                unityWebRequest.SetRequestHeader("Content-Type", "application/octet-stream");
                unityWebRequest.SetRequestHeader(ocpApimSubscriptionKeyHeader, authorizationKey);

                // the download handler will help receiving the analysis from Azure
                unityWebRequest.downloadHandler = new DownloadHandlerBuffer();

                // the upload handler will help uploading the byte array with the request
                unityWebRequest.uploadHandler = new UploadHandlerRaw(imageBytes);
                unityWebRequest.uploadHandler.contentType = "application/octet-stream";

                yield return unityWebRequest.SendWebRequest();

                long responseCode = unityWebRequest.responseCode;     

                try
                {
                    string jsonResponse = null;
                    jsonResponse = unityWebRequest.downloadHandler.text;

                    // The response will be in Json format
                    // therefore it needs to be deserialized into the classes AnalysedObject and TagData
                    AnalysedObject analysedObject = new AnalysedObject();
                    analysedObject = JsonUtility.FromJson<AnalysedObject>(jsonResponse);

                    if (analysedObject.tags == null)
                    {
                        Debug.Log("analysedObject.tagData is null");
                    }
                    else
                    {
                        Dictionary<string, float> tagsDictionary = new Dictionary<string, float>();

                        foreach (TagData td in analysedObject.tags)
                        {
                            TagData tag = td as TagData;
                            tagsDictionary.Add(tag.name, tag.confidence);                            
                        }

                        ResultsLabel.instance.SetTagsToLastLabel(tagsDictionary);
                    }
                }
                catch (Exception exception)
                {
                    Debug.Log("Json exception.Message: " + exception.Message);
                }

                yield return null;
            }
        }
    ```

    ```csharp
        /// <summary>
        /// Returns the contents of the specified file as a byte array.
        /// </summary>
        private static byte[] GetImageAsByteArray(string imageFilePath)
        {
            FileStream fileStream = new FileStream(imageFilePath, FileMode.Open, FileAccess.Read);
            BinaryReader binaryReader = new BinaryReader(fileStream);
            return binaryReader.ReadBytes((int)fileStream.Length);
        }  
    ```

9.  Assicurarsi di salvare le modifiche in *Visual Studio* prima di tornare a *Unity.*
10. Nell'editor di Unity fare clic e trascinare le classi *VisionManager* e *ImageCapture* dalla cartella **Scripts** all'oggetto **Fotocamera** principale nel *pannello Gerarchia*. 

## <a name="chapter-8--before-building"></a>Capitolo 8 : Prima della compilazione

Per eseguire un test approfondito dell'applicazione, è necessario eseguire il sideload dell'applicazione HoloLens.
Prima di procedere, assicurarsi che:

-   Tutte le impostazioni indicate nel [capitolo 2](#chapter-2--set-up-the-unity-project) sono impostate correttamente. 
-   Tutti gli script sono collegati **all'oggetto Fotocamera** principale. 
-   Tutti i campi nel *pannello controllo fotocamera principale* vengono assegnati correttamente.
-   Assicurarsi di inserire la **chiave di autenticazione** nella variabile **authorizationKey.**
-   Assicurarsi di aver controllato anche l'endpoint nello script *VisionManager* e che sia allineato *all'area* (questo documento usa *west-us* per impostazione predefinita).

## <a name="chapter-9--build-the-uwp-solution-and-sideload-the-application"></a>Capitolo 9: Compilare la soluzione UWP e eseguire il sideload dell'applicazione
Tutto il necessario per la sezione Unity di questo progetto è stato completato, quindi è il momento di compilarlo da Unity.

1.  Passare a *Build Impostazioni* File >  -  **Build Impostazioni...**
2.  Nella finestra *Compila Impostazioni* fare clic su **Compila**.

    ![Compilazione dell'app da Unity](images/AzureLabs-Lab2-26.png)

3.  Se non è già presente, selezionare **Unity C# Projects**.
4.  Fare clic su **Compila**. Unity avvierà una *Esplora file,* in cui è necessario creare e quindi selezionare una cartella in cui compilare l'app. Creare la cartella e assegnare alla cartella il nome *App*. Quindi, con la *cartella App* selezionata, premere **Seleziona cartella**. 
5.  Unity inizierà a compilare il progetto nella *cartella App.* 
6.  Al termine della compilazione di Unity (potrebbe essere necessario del tempo), verrà aperta una finestra *Esplora file* nel percorso della compilazione (controllare la barra delle applicazioni, perché potrebbe non essere sempre visualizzata sopra le finestre, ma verrà notificata l'aggiunta di una nuova finestra).

## <a name="chapter-10--deploy-to-hololens"></a>Capitolo 10: Distribuire in HoloLens

Per eseguire la distribuzione HoloLens:

1.  Sarà necessario l'indirizzo IP del HoloLens (per la distribuzione remota) e per assicurarsi che il HoloLens sia in **modalità sviluppatore.** Per eseguire questa operazione:

    1. Mentre si indossa il HoloLens, aprire il **Impostazioni**.
    2. Passare a **Impostazioni & Internet > Wi-Fi > opzioni avanzate**
    3. Prendere nota **dell'indirizzo IPv4.**
    4. Tornare quindi a Impostazioni **e** quindi a Update & Security > for Developers (Aggiorna & Sicurezza > **per sviluppatori)** 
    5. Impostare la modalità sviluppatore attivata.

2.  Passare alla nuova build di Unity (cartella *App)* e aprire il file di soluzione con *Visual Studio*.
3.  In Configurazione soluzione selezionare **Debug**.
4.  In Piattaforma soluzione selezionare **x86**, **Computer remoto**. 

    ![Distribuire la soluzione da Visual Studio.](images/AzureLabs-Lab2-27.png)
 
5.  Passare al **menu Compila e** fare clic su **Distribuisci soluzione** per eseguire il sideload dell'applicazione nel HoloLens.
6.  L'app dovrebbe ora essere visualizzata nell'elenco delle app installate nel HoloLens, pronto per l'avvio.

> [!NOTE]
> Per eseguire la distribuzione in visore vr immersivo, impostare Piattaforma **soluzione** su *Computer* locale e impostare Configurazione su *Debug*, con *x86* come **Piattaforma**.  Quindi eseguire la distribuzione nel computer locale, usando il **menu Compila**, selezionando *Distribuisci soluzione*. 

## <a name="your-finished-computer-vision-api-application"></a>Applicazione API Visione artificiale completata

È stata compilata un'app di realtà mista che sfrutta l'API Visione artificiale di Azure per riconoscere gli oggetti reali e visualizzare l'attendibilità di ciò che è stato visto.

![risultato del lab](images/AzureLabs-Lab2-000.png)

## <a name="bonus-exercises"></a>Esercizi aggiuntivi

### <a name="exercise-1"></a>Esercizio 1

Proprio come è stato usato il *parametro Tags* (come indicato all'interno *dell'endpoint* usato all'interno di *VisionManager),* estendere l'app per rilevare altre informazioni. esaminare gli altri parametri a cui si ha accesso [qui.](https://westus.dev.cognitive.microsoft.com/docs/services/56f91f2d778daf23d8ec6739/operations/56f91f2e778daf14a499e1fa)

### <a name="exercise-2"></a>Esercizio 2

Visualizzare i dati di Azure restituiti, in modo più conversazionale e leggibile, nascondendo i numeri. Come se un bot parla con l'utente.
---
title: HoloLens (prima generazione) e Azure 302b - Visione personalizzata
description: Completare questo corso per informazioni su come eseguire il training di un modello di Machine Learning e quindi usare il modello con training per riconoscere oggetti simili all'interno di un'applicazione di realtà mista.
author: drneil
ms.author: jemccull
ms.date: 07/03/2018
ms.topic: article
keywords: azure, mixed reality, academy, unity, tutorial, api, custom vision, hololens, immersive, vr, Windows 10, Visual Studio
ms.openlocfilehash: 25f07dddf53cf8c279f99d230d1bd4d206a663eba884abc0dd32313bce4b7b43
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115217583"
---
# <a name="hololens-1st-gen-and-azure-302b-custom-vision"></a>HoloLens (prima generazione) e Azure 302b: Visione personalizzata

<br>

>[!NOTE]
>Le esercitazioni di Mixed Reality Academy sono state progettate in base a HoloLens (prima generazione) e ai visori VR immersive di realtà mista.  Pertanto, riteniamo importante lasciarle a disposizione degli sviluppatori a cui serve ancora materiale sussidiario per lo sviluppo di questi dispositivi.  Queste esercitazioni **_non_** verranno aggiornate con i set di strumenti o le interazioni più recenti usati per HoloLens 2.  Rimarranno invariate per consentire di continuare a lavorare sui dispositivi supportati. In futuro verrà pubblicata una nuova serie di esercitazioni che illustrano come sviluppare per HoloLens 2.  Questa informativa verrà aggiornata con un collegamento a tali esercitazioni al momento della pubblicazione.

<br>


In questo corso si apprenderà come riconoscere il contenuto visivo personalizzato all'interno di un'immagine fornita, usando le funzionalità Visione personalizzata azure in un'applicazione di realtà mista.

Questo servizio consente di eseguire il training di un modello di Machine Learning usando immagini oggetto. Si userà quindi il modello con training per riconoscere oggetti simili, come fornito dall'acquisizione della fotocamera di Microsoft HoloLens o da una fotocamera connessa al PC per visori VR immersive.

![risultato del corso](images/AzureLabs-Lab302b-00.png)

Azure Visione personalizzata è un servizio cognitivo Microsoft che consente agli sviluppatori di creare classificatori di immagini personalizzati. Questi classificatori possono quindi essere usati con nuove immagini per riconoscere o classificare gli oggetti all'interno della nuova immagine. Il servizio offre un portale online semplice, facile da usare per semplificare il processo. Per altre informazioni, visitare la pagina [del servizio azure Visione personalizzata](/azure/cognitive-services/custom-vision-service/home).

Al termine di questo corso, si avrà un'applicazione di realtà mista che sarà in grado di funzionare in due modalità:

-   **Modalità di analisi:** configurazione manuale del servizio Visione personalizzata caricando immagini, creando tag ed eseguire il training del servizio per riconoscere oggetti diversi (in questo caso mouse e tastiera). Si creerà quindi un'app HoloLens che acquisiscerà le immagini usando la fotocamera e tenterà di riconoscere tali oggetti nel mondo reale.

-   **Modalità di training:** si implementerà il codice che abiliterà una "modalità di training" nell'app. La modalità di training consente di acquisire immagini usando la fotocamera del HoloLens, caricare le immagini acquisite nel servizio ed eseguire il training del modello di visione personalizzata.

Questo corso illustra come ottenere i risultati dal servizio Visione personalizzata in un'applicazione di esempio basata su Unity. Sarà necessario applicare questi concetti a un'applicazione personalizzata che potrebbe essere compilata.

## <a name="device-support"></a>Supporto di dispositivi

<table>
<tr>
<th>Corso</th><th style="width:150px"> <a href="/hololens/hololens1-hardware">HoloLens</a></th><th style="width:150px"> <a href="../../../discover/immersive-headset-hardware-details.md">Visori VR immersive</a></th>
</tr><tr>
<td> MR e Azure 302b: Visione artificiale personalizzata</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> Anche se questo corso è in HoloLens, è anche possibile applicare ciò che si apprende in questo corso per Windows Mixed Reality visori vr immersivi. Poiché i visori VR immersive non hanno fotocamere accessibili, è necessaria una fotocamera esterna connessa al PC. Man mano che si segue il corso, verranno visualizzati note sulle modifiche che potrebbe essere necessario applicare per supportare visori VR immersive.

## <a name="prerequisites"></a>Prerequisiti

> [!NOTE]
> Questa esercitazione è progettata per sviluppatori con esperienza di base con Unity e C#. Tenere inoltre presente che i prerequisiti e le istruzioni scritte all'interno di questo documento rappresentano ciò che è stato testato e verificato al momento della scrittura (luglio 2018). È possibile usare il software più recente, come elencato nell'articolo Installare gli strumenti, anche se non si deve presumere che le informazioni in questo corso corrispondano perfettamente a quelle disponibili nel software più recente rispetto a quelle elencate di seguito. [](../../install-the-tools.md)

Per questo corso è consigliabile usare l'hardware e il software seguenti:

- Un PC di sviluppo, [compatibile con Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) per lo sviluppo di visori vr immersive
- [Windows 10 Fall Creators Update (o versione successiva) con la modalità sviluppatore abilitata](../../install-the-tools.md#installation-checklist)
- [L'SDK Windows 10 più recente](../../install-the-tools.md#installation-checklist)
- [Unity 2017.4](../../install-the-tools.md#installation-checklist)
- [Visual Studio 2017](../../install-the-tools.md#installation-checklist)
- Visore [Windows Mixed Reality vr o](../../../discover/immersive-headset-hardware-details.md) visore [Microsoft HoloLens](/hololens/hololens1-hardware) con la modalità sviluppatore abilitata
- Una fotocamera connessa al PC (per lo sviluppo di visori immersivi)
- Accesso a Internet per la configurazione di Azure e il Visione personalizzata'API
- Una serie di almeno cinque (5) immagini (dieci (10) consigliate) per ogni oggetto che si vuole riconoscere dal Visione personalizzata service. Se lo si desidera, è possibile usare [le immagini già fornite con questo corso (mouse del computer e tastiera). ](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/ComputerVision_Images.zip)

## <a name="before-you-start"></a>Prima di iniziare

1.  Per evitare problemi durante la compilazione di questo progetto, è consigliabile creare il progetto indicato in questa esercitazione in una cartella radice o quasi radice (i percorsi di cartelle lunghe possono causare problemi in fase di compilazione).
2.  Configurare e testare il HoloLens. Se è necessario supporto per la configurazione del HoloLens, visitare l'articolo HoloLens [setup .](/hololens/hololens-setup) 
3.  È buona idea eseguire calibrazione e ottimizzazione dei sensori quando si inizia a sviluppare una nuova app HoloLens (talvolta può essere utile per eseguire queste attività per ogni utente). 

Per informazioni sulla calibrazione, seguire questo [collegamento all'HoloLens calibrazione.](/hololens/hololens-calibration#hololens-2)

Per informazioni sull'ottimizzazione dei sensori, seguire questo [collegamento all'articolo HoloLens Sensor Tuning](/hololens/hololens-updates).

## <a name="chapter-1---the-custom-vision-service-portal"></a>Capitolo 1- Portale Visione personalizzata service

Per usare il *Visione personalizzata in* Azure, è necessario configurare un'istanza del servizio per essere resa disponibile per l'applicazione.

1.  Per prima [cosa, passare *alla Visione personalizzata principale del* servizio.](https://azure.microsoft.com/services/cognitive-services/custom-vision-service/)

2.  Fare clic sul **pulsante Informazioni di base.**

    ![Introduzione al servizio Visione personalizzata](images/AzureLabs-Lab302b-01.png)

3.  Accedere al portale *Visione personalizzata service.*

    ![Accedere al portale](images/AzureLabs-Lab302b-02.png)

    > [!NOTE]
    > Se non si dispone già di un account Azure, è necessario crearne uno. Se si sta seguendo questa esercitazione in una situazione di classe o di lab, chiedere all'insegnante o a uno dei prottori di assistenza per la configurazione del nuovo account.

4.  Dopo aver eseguito l'accesso per la prima volta, verrà visualizzato il pannello *Condizioni per il* servizio. Fare clic sulla casella di controllo per accettare le condizioni. Quindi fare clic su **Accetto**.

    ![Condizioni per il servizio](images/AzureLabs-Lab302b-03.png)

5.  Dopo aver accettato le Condizioni, si passa alla *sezione Progetti* del portale. Fare clic **su Nuovo Project**.

    ![Creare un nuovo progetto](images/AzureLabs-Lab302b-04.png)

6.  Sul lato destro verrà visualizzata una scheda che richiede di specificare alcuni campi per il progetto.

    1.  Inserire un *nome* per il progetto.

    2.  Inserire una *descrizione* per il progetto (*facoltativo*).

    3.  Scegliere un *gruppo di risorse* o crearne uno nuovo. Un gruppo di risorse consente di monitorare, controllare l'accesso, effettuare il provisioning e gestire la fatturazione per una raccolta di asset di Azure. È consigliabile mantenere tutti i servizi di Azure associati a un singolo progetto,ad esempio questi corsi, in un gruppo di risorse comune.

    4. Impostare i *tipi Project su* **Classificazione**
    
    5. Impostare *Domini su* **Generale**.

        ![Impostare i domini](images/AzureLabs-Lab302b-05.png)

        > Per altre informazioni sui gruppi di risorse di Azure, vedere [l'articolo gruppo di risorse](/azure/azure-resource-manager/resource-group-portal).

7.  Al termine, fare clic su **Crea** progetto , si verrà reindirizzati alla pagina del Visione personalizzata Service, project.

## <a name="chapter-2---training-your-custom-vision-project"></a>Capitolo 2 - Training del progetto Visione personalizzata

Una volta nel portale Visione personalizzata, l'obiettivo principale è eseguire il training del progetto per riconoscere oggetti specifici nelle immagini. Sono necessarie almeno cinque (5) immagini, anche se è preferibile scegliere dieci (10), per ogni oggetto che si vuole riconoscere dall'applicazione. [È possibile usare le immagini fornite con questo corso (mouse del computer e tastiera).](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/ComputerVision_Images.zip) 

Per eseguire il training del Visione personalizzata service:

1.  Fare clic sul **+** pulsante accanto a **Tag.**

    ![Aggiungere un nuovo tag](images/AzureLabs-Lab302b-06.png)

2.  Aggiungere il **nome** dell'oggetto che si vuole riconoscere. Fare clic su **Save**.

    ![Aggiungere il nome dell'oggetto e salvare](images/AzureLabs-Lab302b-07.png)

3.  Si noterà che **il tag** è stato aggiunto (potrebbe essere necessario ricaricare la pagina per la visualizzazione). Fare clic sulla casella di controllo accanto al nuovo tag, se non è già selezionato.

    ![Abilitare il nuovo tag](images/AzureLabs-Lab302b-08.png)

4.  Fare clic **su Aggiungi** immagini al centro della pagina.

    ![Aggiungere immagini](images/AzureLabs-Lab302b-09.png)

5.  Fare clic **su Sfoglia file locali** e cercare, quindi selezionare le immagini da caricare, con un minimo di cinque (5). Tenere presente che tutte queste immagini devono contenere l'oggetto di cui si sta training.

    > [!NOTE]
    >  È possibile selezionare più immagini contemporaneamente da caricare.

6.  Dopo aver visualizzato le immagini nella scheda, selezionare il tag appropriato nella **casella Tag** personali.

    ![Selezionare i tag](images/AzureLabs-Lab302b-10.png)

7.  Fare clic **su Upload file**. Verrà iniziato il caricamento dei file. Dopo aver visualizzato la conferma del caricamento, fare clic su **Fine.**

    ![Caricare i file](images/AzureLabs-Lab302b-11.png)

8.  Ripetere lo stesso processo per creare un nuovo **tag denominato** **Tastiera** e caricare le foto appropriate. Assicurarsi di **deselezionare** *Mouse dopo* aver creato i nuovi tag, in modo da visualizzare la finestra *Aggiungi* immagini.

9.  Dopo aver configurato entrambi i tag, fare clic su **Train (Training)** e la prima iterazione di training inizierà a compilare.

    ![Abilitare l'iterazione del training](images/AzureLabs-Lab302b-12.png)

10. Dopo la creazione, sarà possibile visualizzare due pulsanti denominati **Make default** (Rendi predefinito) e Prediction **URL (URL previsione).** Fare clic **su Make default first (Rendi** predefinito) e quindi su Prediction URL **(URL stima).**

    ![Impostare l'URL predefinito e quello di stima](images/AzureLabs-Lab302b-13.png)

    > [!NOTE] 
    > L'URL dell'endpoint fornito da questo oggetto è impostato su qualsiasi *iterazione* sia stata contrassegnata come predefinita. Di conseguenza, se in un secondo momento si crea una nuova iterazione *e* la si aggiorna come predefinita, non sarà necessario modificare il codice.

11. Dopo aver fatto clic su Prediction *URL (URL* stima), aprire *Blocco note* e copiare e incollare **l'URL** e **prediction-key,** in modo da poterlo recuperare quando necessario in un secondo momento nel codice.

    ![Copiare e incollare URL e Prediction-Key](images/AzureLabs-Lab302b-14.png)

12. Fare clic **sull'ingranaggio** in alto a destra nella schermata.

    ![Fare clic sull'icona a forma di ingranaggio per aprire le impostazioni](images/AzureLabs-Lab302b-15.png)

13. Copiare **la chiave di training** e incollarla in un Blocco note , *per* un uso successivo.

    ![Copiare la chiave di training](images/AzureLabs-Lab302b-16.png)

14. Copiare anche **il Project e** incollarlo nel file *Blocco note,* per usarlo in seguito.

    ![Copiare l'ID progetto](images/AzureLabs-Lab302b-16a.png)

## <a name="chapter-3---set-up-the-unity-project"></a>Capitolo 3: Configurare il progetto Unity

Di seguito è riportata una configurazione tipica per lo sviluppo con la realtà mista e, di conseguenza, è un buon modello per altri progetti.

1.  Aprire *Unity e* fare clic su New **(Nuovo).**

    ![Creare un nuovo progetto Unity](images/AzureLabs-Lab302b-17.png)

2.  È ora necessario specificare un nome di progetto Unity. Inserire **AzureCustomVision.** Assicurarsi che il modello di progetto sia impostato su **3D.** Impostare Il **percorso su** un percorso appropriato per l'utente(tenere presente che più vicino alle directory radice è meglio). Fare quindi clic **su Crea progetto**.

    ![Configurare le impostazioni del progetto](images/AzureLabs-Lab302b-18.png)

3.  Con Unity aperto, è opportuno controllare che l'editor di **script predefinito** sia impostato **su Visual Studio**. Passare a **Modifica*  >  *preferenze** e quindi dalla nuova finestra passare a **Strumenti esterni.** Modificare **External Script Editor in** Visual Studio **2017**. Chiudere la **finestra** Preferenze.

    ![Configurare strumenti esterni](images/AzureLabs-Lab302b-19.png)

4.  Passare quindi a **File > Build Impostazioni** e selezionare Universal Windows **Platform** e quindi fare clic sul pulsante **Switch Platform** (Cambia piattaforma) per applicare la selezione.

    ![Configurare le impostazioni di compilazione ](images/AzureLabs-Lab302b-20.png)

5.  Sempre in **File > build Impostazioni** e assicurarsi che:

    1.  **Il dispositivo di** destinazione è impostato **su HoloLens**

        > Per i visori VR immersive, impostare **Dispositivo di destinazione** su Qualsiasi *dispositivo.*
        
    2.  **Il tipo di** compilazione è impostato **su D3D**
    3.  **L'SDK** è impostato su **Più recente installato**
    4.  **Visual Studio versione è** impostata su **Versione più recente installata**
    5.  **Build and Run (Compilazione** ed esecuzione) è impostato **su Local Machine (Computer locale)**
    6.  Salvare la scena e aggiungerla alla compilazione. 

        1. A tale scopo, selezionare **Add Open Scenes (Aggiungi scene aperte).** Verrà visualizzata una finestra di salvataggio.

            ![Aggiungere la scena aperta all'elenco di compilazione](images/AzureLabs-Lab302b-21.png)

        2. Creare una nuova cartella per questa ed eventuali  scene future, quindi selezionare il pulsante Nuova cartella. Per creare una nuova cartella, assegnare alla nuova cartella il nome **Scenes**.

            ![Creare una nuova cartella della scena](images/AzureLabs-Lab302b-22.png)

        3. Aprire la cartella **Scenes appena** creata e quindi nel campo di testo *Nome file:* digitare **CustomVisionScene** e quindi fare clic su **Salva.**

            ![Assegnare un nome al nuovo file della scena](images/AzureLabs-Lab302b-23.png)

            > Tenere presente che è necessario salvare le scene di Unity all'interno *della cartella Assets,* perché devono essere associate al progetto Unity. La creazione della cartella scenes (e di altre cartelle simili) è un modo tipico per strutturare un progetto Unity.
            
    7.  Le impostazioni rimanenti, in *Build Impostazioni*, per il momento devono essere lasciato come predefinite.

        ![Impostazioni di compilazione predefinite](images/AzureLabs-Lab302b-24.png)

6.  Nella finestra *build Impostazioni* fare clic sul pulsante **Player Impostazioni** per aprire il pannello correlato nello spazio in cui si trova *il controllo.*

7. In questo pannello è necessario verificare alcune impostazioni:

    1.  Nella scheda **Altro Impostazioni:**

        1.  **La versione del runtime di** scripting deve essere sperimentale (equivalente a **.NET 4.6),** che attiverà la necessità di riavviare l'editor.

        2. **Il back-end di** scripting deve **essere .NET**

        3. **Il livello di compatibilità dell'API** **deve essere .NET 4.6**

        ![Impostare la compilare l'API](images/AzureLabs-Lab302b-25.png)

    2.  **All'interno della Impostazioni** pubblicazione, in **Funzionalità** selezionare:

        1. **InternetClient**

        2.  **Webcam**

        3. **Microfono**

        ![Configurare le impostazioni di pubblicazione](images/AzureLabs-Lab302b-26.png)

    3.  Più in basso nel pannello, in **XR Impostazioni** (disponibile sotto **Pubblica Impostazioni),** selezionare **Virtual Reality Supported**(Realtà virtuale supportata) e assicurarsi che sia stato aggiunto **Windows Mixed Reality SDK.**

    ![Configurare le impostazioni XR](images/AzureLabs-Lab302b-27.png)

8.  Tornare a *Build Impostazioni* Unity *C \# Projects* is no longer grayed (Compila progetti Unity C non è più in grigio). Selezionare la casella di controllo accanto a questa opzione.

9.  Chiudere la finestra Build Settings (Impostazioni di compilazione).

10.  Salvare la scena e il progetto (**FILE > SAVE SCENE/FILE > SAVE PROJECT**).


## <a name="chapter-4---importing-the-newtonsoft-dll-in-unity"></a>Capitolo 4 - Importazione della DLL Newtonsoft in Unity

> [!IMPORTANT]
> Se si vuole ignorare il componente Di configurazione di *Unity* di questo corso e continuare direttamente con il codice, scaricare il file [](https://docs.unity3d.com/Manual/AssetPackages.html) [Azure-MR-302b.unitypackage,](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/Azure-MR-302b.unitypackage)importarlo nel progetto come pacchetto personalizzato e quindi continuare dal capitolo [6.](#chapter-6---create-the-customvisionanalyser-class)

Questo corso richiede l'uso **della libreria Newtonsoft,** che è possibile aggiungere come DLL agli asset. Il pacchetto contenente [questa libreria può essere scaricato da questo collegamento.](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/NewtonsoftDLL.unitypackage)
Per importare la libreria Newtonsoft nel progetto, usare il pacchetto Unity fornito con questo corso.

1.  Aggiungere il *file con estensione unitypackage* a Unity usando l'opzione di menu **Assets*  >  *Import* *Package*  >  *Custom* *Package (Importa** pacchetto personalizzato di asset).

2.  Nella casella **Import Unity Package (Importa** pacchetto Unity) visualizzata verificare che sia selezionato tutto il contenuto di Plugins (e including) Plugins (Plug-in inclusi). 

    ![Importare tutti gli elementi del pacchetto](images/AzureLabs-Lab302b-28.png)

3.  Fare clic **sul** pulsante Importa per aggiungere gli elementi al progetto.

4.  Passare alla cartella **Newtonsoft** in **Plugins (Plug-in)** nella visualizzazione del progetto e selezionare il *Newtonsoft.Jssul plug-in*.

    ![Selezionare Newtonsoft plugin (Plug-in Newtonsoft)](images/AzureLabs-Lab302b-29.png)

5.  Con *lNewtonsoft.Js* del plug-in selezionato, assicurarsi che l'opzione Any **Platform** (Qualsiasi piattaforma) sia deselezionata, quindi assicurarsi che anche **WSAPlayer** sia deselezionato **e** quindi fare clic su Apply **(Applica).** Questa operazione viene eseguita solo per verificare che i file siano configurati correttamente.

    ![Configurare il plug-in Newtonsoft](images/AzureLabs-Lab302b-30.png)

    > [!NOTE]
    > Contrassegnare questi plug-in per configurarli in modo che siano usati solo nell'editor di Unity. Nella cartella WSA è presente un set diverso che verrà usato dopo l'esportazione del progetto da Unity.

6.  Successivamente, è necessario aprire la **cartella WSA** all'interno della **cartella Newtonsoft.** Verrà visualizzata una copia dello stesso file appena configurato. Selezionare il file e quindi nel controllo verificare che
    -   **Qualsiasi piattaforma** **è deselezionata** 
    -   **È selezionato** **solo WSAPlayer** 
    -   **L'opzione Non processo** è **selezionata**

    ![Configurare le impostazioni della piattaforma del plug-in Newtonsoft](images/AzureLabs-Lab302b-31.png)

## <a name="chapter-5---camera-setup"></a>Capitolo 5 - Configurazione della fotocamera

1.  Nel pannello Hierarchy (Gerarchia) selezionare *Main Camera (Fotocamera principale).*

2.  Dopo aver selezionato, sarà possibile visualizzare tutti i componenti della *fotocamera principale* nel pannello *Inspector*.

    1.  *L'oggetto fotocamera* deve essere denominato **Fotocamera principale** (si noti l'ortografia).

    2.  Il tag della **fotocamera principale** deve essere impostato su **MainCamera** (si noti l'ortografia).

    3.  Assicurarsi che **la posizione di** trasformazione sia impostata su **0, 0, 0**

    4.  Impostare **Clear Flags su** Solid Color **(Colore a tinta** unita) (ignorarlo per il visore vr immersivo).

    5.  Impostare colore **di sfondo** del componente della fotocamera su **Nero, Alfa 0 (Codice esadecimale: #00000000)** (ignorarlo per visore immersivo).

    ![Configurare le proprietà del componente Camera](images/AzureLabs-Lab302b-32.png)


## <a name="chapter-6---create-the-customvisionanalyser-class"></a>Capitolo 6: Creare la classe CustomVisionAnalyser.

A questo punto è possibile scrivere codice.

Si inizierà con la *classe CustomVisionAnalyser.*

> [!NOTE]
> Le chiamate al servizio **Visione personalizzata effettuate** nel codice seguente vengono effettuate usando l'API REST Visione personalizzata **.** Usando questa funzionalità, si scoprirà come implementare e usare questa API (utile per comprendere come implementare qualcosa di simile in modo personalizzato). Tenere presente che Microsoft offre un **VISIONE PERSONALIZZATA Service SDK** che può essere usato anche per effettuare chiamate al servizio. Per altre informazioni, vedere [l'articolo Visione personalizzata Service SDK.](https://github.com/Microsoft/Cognitive-CustomVision-Windows/)

Questa classe è responsabile di:

-   Caricamento dell'immagine più recente acquisita come matrice di byte.

-   Invio della matrice di byte all'istanza *del servizio Azure Visione personalizzata per* l'analisi.

-   Ricezione della risposta come stringa JSON.

-   Deserializzazione della risposta  e passaggio della stima risultante alla *classe SceneOrganiser,* che si occuperà della modalità di visualizzazione della risposta.

Per creare questa classe:

1.  Fare clic con il pulsante destro *del mouse* nella cartella Asset nel pannello *Project ,* quindi scegliere Crea > **cartella**. Chiamare la cartella **Scripts**.

    ![Creare la cartella degli script](images/AzureLabs-Lab302b-33.png)

2.  Fare doppio clic sulla cartella appena creata per aprirla.

3.  Fare clic con il pulsante destro del mouse all'interno della cartella , **quindi scegliere Crea**  >  **\# script C**. Assegnare allo script *il nome CustomVisionAnalyser*.

4.  Fare doppio clic sul nuovo script *CustomVisionAnalyser* per aprirlo con **Visual Studio**.

5.  Aggiornare gli spazi dei nomi nella parte superiore del file in modo che corrispondano ai seguenti:

    ```csharp
    using System.Collections;
    using System.IO;
    using UnityEngine;
    using UnityEngine.Networking;
    using Newtonsoft.Json;
    ```

6.  Nella *classe CustomVisionAnalyser* aggiungere le variabili seguenti:

    ```csharp
        /// <summary>
        /// Unique instance of this class
        /// </summary>
        public static CustomVisionAnalyser Instance;

        /// <summary>
        /// Insert your Prediction Key here
        /// </summary>
        private string predictionKey = "- Insert your key here -";

        /// <summary>
        /// Insert your prediction endpoint here
        /// </summary>
        private string predictionEndpoint = "Insert your prediction endpoint here";

        /// <summary>
        /// Byte array of the image to submit for analysis
        /// </summary>
        [HideInInspector] public byte[] imageBytes;
    ```

    > [!NOTE]
    > Assicurarsi di inserire la chiave **di stima** nella variabile **predictionKey** e nell'endpoint **di** stima nella **variabile predictionEndpoint.** Questi elementi sono stati *copiati Blocco note* nel corso.

7.  È ora necessario aggiungere il codice per **Awake()** per inizializzare la variabile Instance:

    ```csharp
        /// <summary>
        /// Initialises this class
        /// </summary>
        private void Awake()
        {
            // Allows this instance to behave like a singleton
            Instance = this;
        }
    ```

8.  Eliminare i metodi **Start()** **e Update()**.

9.  Aggiungere quindi la coroutine (con il metodo **statico GetImageAsByteArray()** sotto di essa), che otterrà i risultati dell'analisi dell'immagine acquisita dalla *classe ImageCapture.*

    > [!NOTE]
    > Nella coroutine **AnalyseImageCapture** è presente una chiamata alla classe *SceneOrganiser* che è ancora necessario creare. Pertanto, **lasciare le righe commentate per il momento.**

    ```csharp    
        /// <summary>
        /// Call the Computer Vision Service to submit the image.
        /// </summary>
        public IEnumerator AnalyseLastImageCaptured(string imagePath)
        {
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

                // The response will be in JSON format, therefore it needs to be deserialized    
    
                // The following lines refers to a class that you will build in later Chapters
                // Wait until then to uncomment these lines

                //AnalysisObject analysisObject = new AnalysisObject();
                //analysisObject = JsonConvert.DeserializeObject<AnalysisObject>(jsonResponse);
                //SceneOrganiser.Instance.SetTagsToLastLabel(analysisObject);
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

10.  Assicurarsi di salvare le modifiche in **Visual Studio** prima di tornare a **Unity.**

## <a name="chapter-7---create-the-customvisionobjects-class"></a>Capitolo 7- Creare la classe CustomVisionObjects

La classe che si creerà ora è *la classe CustomVisionObjects.*

Questo script contiene una serie di oggetti usati da altre classi per serializzare e deserializzare le chiamate effettuate al *Visione personalizzata Service*.

> [!WARNING]
> È importante prendere nota dell'endpoint fornito dal servizio Visione personalizzata, perché la struttura JSON seguente è stata impostata per l'utilizzo Visione personalizzata [*Prediction v2.0*](https://southcentralus.dev.cognitive.microsoft.com/docs/services/450e4ba4d72542e889d93fd7b8e960de/operations/5a6264bc40d86a0ef8b2c290). Se si ha una versione diversa, potrebbe essere necessario aggiornare la struttura seguente.

Per creare questa classe:

1.  Fare clic con il pulsante destro del **mouse nella cartella Script** , quindi scegliere **Crea**  >  **\# script C**. Chiamare lo script *CustomVisionObjects*.

2.  Fare doppio clic sul nuovo script **CustomVisionObjects** per aprirlo con **Visual Studio**.

3.  Aggiungere gli spazi dei nomi seguenti all'inizio del file:

    ```csharp
    using System;
    using System.Collections.Generic;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

4.  Eliminare i **metodi Start()** **e Update()** all'interno *della classe CustomVisionObjects.* Questa classe dovrebbe ora essere vuota.

5.  Aggiungere le classi seguenti **all'esterno** *della classe CustomVisionObjects.* Questi oggetti vengono usati dalla libreria *Newtonsoft* per serializzare e deserializzare i dati della risposta:

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
    /// JSON of Images submitted
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
    /// Predictions received by the Service after submitting an image for analysis
    /// </summary> 
    [Serializable]
    public class AnalysisObject
    {
        public List<Prediction> Predictions { get; set; }
    }

    [Serializable]
    public class Prediction
    {
        public string TagName { get; set; }
        public double Probability { get; set; }
    }
    ```

## <a name="chapter-8---create-the-voicerecognizer-class"></a>Capitolo 8 - Creare la classe VoiceRecognizer

Questa classe riconoscerà l'input vocale dell'utente.

Per creare questa classe:

1.  Fare clic con il pulsante destro del **mouse nella cartella Script** , quindi scegliere **Crea**  >  **\# script C**. Chiamare lo script *VoiceRecognizer*.

2.  Fare doppio clic sul nuovo script **VoiceRecognizer** per aprirlo con **Visual Studio**.

3.  Aggiungere gli spazi dei nomi seguenti sopra la *classe VoiceRecognizer:*

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.Linq;
    using UnityEngine;
    using UnityEngine.Windows.Speech;
    ```

4.  Aggiungere quindi le variabili seguenti all'interno *della classe VoiceRecognizer,* sopra il *metodo Start():*

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static VoiceRecognizer Instance;

        /// <summary>
        /// Recognizer class for voice recognition
        /// </summary>
        internal KeywordRecognizer keywordRecognizer;

        /// <summary>
        /// List of Keywords registered
        /// </summary>
        private Dictionary<string, Action> _keywords = new Dictionary<string, Action>();
    ```

5.  Aggiungere i **metodi Awake()** e  **Start(),** che configurano le parole chiave dell'utente da riconoscere quando si associa un tag a un'immagine:

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
        void Start ()
        {

            Array tagsArray = Enum.GetValues(typeof(CustomVisionTrainer.Tags));

            foreach (object tagWord in tagsArray)
            {
                _keywords.Add(tagWord.ToString(), () =>
                {
                    // When a word is recognized, the following line will be called
                    CustomVisionTrainer.Instance.VerifyTag(tagWord.ToString());
                });
            }

            _keywords.Add("Discard", () =>
            {
                // When a word is recognized, the following line will be called
                // The user does not want to submit the image
                // therefore ignore and discard the process
                ImageCapture.Instance.ResetImageCapture();
                keywordRecognizer.Stop();
            });

            //Create the keyword recognizer 
            keywordRecognizer = new KeywordRecognizer(_keywords.Keys.ToArray());

            // Register for the OnPhraseRecognized event 
            keywordRecognizer.OnPhraseRecognized += KeywordRecognizer_OnPhraseRecognized;
        }
    ```

6.  Eliminare il **metodo Update().**

7.  Aggiungere il gestore seguente, che viene chiamato ogni volta che viene riconosciuto l'input vocale:

    ```csharp    
        /// <summary>
        /// Handler called when a word is recognized
        /// </summary>
        private void KeywordRecognizer_OnPhraseRecognized(PhraseRecognizedEventArgs args)
        {
            Action keywordAction;
            // if the keyword recognized is in our dictionary, call that Action.
            if (_keywords.TryGetValue(args.text, out keywordAction))
            {
                keywordAction.Invoke();
            }
        }
    ```

8.  Assicurarsi di salvare le modifiche in **Visual Studio** prima di tornare a **Unity.**

> [!NOTE]
> Non è necessario preoccuparsi del codice che potrebbe sembrare avere un errore, perché presto verranno fornite altre classi, che risolveranno questi problemi.

## <a name="chapter-9---create-the-customvisiontrainer-class"></a>Capitolo 9 - Creare la classe CustomVisionTrainer

Questa classe concatena una serie di chiamate Web per eseguire il training *Visione personalizzata Service*. Ogni chiamata verrà illustrata in dettaglio proprio sopra il codice.

Per creare questa classe:

1.  Fare clic con il pulsante destro del **mouse nella cartella Script** , quindi scegliere **Crea**  >  **\# script C**. Chiamare lo script *CustomVisionTrainer*.

2.  Fare doppio clic sul nuovo script *CustomVisionTrainer* per aprirlo con **Visual Studio**.

3.  Aggiungere gli spazi dei nomi seguenti sopra *la classe CustomVisionTrainer:*

    ```csharp
    using Newtonsoft.Json;
    using System.Collections;
    using System.Collections.Generic;
    using System.IO;
    using System.Text;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

4.  Aggiungere quindi le variabili seguenti all'interno *della classe CustomVisionTrainer,* sopra il **metodo Start().** 

    > [!NOTE]
    > L'URL di training usato qui è disponibile nella documentazione *Visione personalizzata Training 1.2* e ha una struttura di: https://southcentralus.api.cognitive.microsoft.com/customvision/v1.2/Training/projects/{projectId}/  
    > Per altre informazioni, vedere l'API di riferimento [*Visione personalizzata Training v1.2*](https://southcentralus.dev.cognitive.microsoft.com/docs/services/f2d62aa3b93843d79e948fe87fa89554/operations/5a3044ee08fa5e06b890f11f).

    > [!WARNING]
    > È importante prendere nota dell'endpoint che il servizio Visione personalizzata fornisce per la modalità di training, poiché la struttura JSON usata (all'interno della classe **CustomVisionObjects)** è stata impostata per l'uso [*con Visione personalizzata Training v1.2.*](https://southcentralus.dev.cognitive.microsoft.com/docs/services/f2d62aa3b93843d79e948fe87fa89554/operations/5a3044ee08fa5e06b890f11f) Se si dispone di una versione diversa, potrebbe essere necessario aggiornare la *struttura Objects.*

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static CustomVisionTrainer Instance;

        /// <summary>
        /// Custom Vision Service URL root
        /// </summary>
        private string url = "https://southcentralus.api.cognitive.microsoft.com/customvision/v1.2/Training/projects/";

        /// <summary>
        /// Insert your prediction key here
        /// </summary>
        private string trainingKey = "- Insert your key here -";

        /// <summary>
        /// Insert your Project Id here
        /// </summary>
        private string projectId = "- Insert your Project Id here -";

        /// <summary>
        /// Byte array of the image to submit for analysis
        /// </summary>
        internal byte[] imageBytes;

        /// <summary>
        /// The Tags accepted
        /// </summary>
        internal enum Tags {Mouse, Keyboard}

        /// <summary>
        /// The UI displaying the training Chapters
        /// </summary>
        private TextMesh trainingUI_TextMesh;
    ```

    > [!IMPORTANT]
    > Assicurarsi di aggiungere il valore **della chiave di servizio** (chiave di training) e Project **id,** come specificato in precedenza. questi sono i valori [raccolti dal portale in precedenza nel corso (capitolo 2, passaggio 10 in poi).](#chapter-2---training-your-custom-vision-project)

5.  Aggiungere i metodi **Start()** e **Awake()** seguenti. Questi metodi vengono chiamati all'inizializzazione e contengono la chiamata per configurare l'interfaccia utente:

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
        private void Start()
        { 
            trainingUI_TextMesh = SceneOrganiser.Instance.CreateTrainingUI("TrainingUI", 0.04f, 0, 4, false);
        }
    ```

6.  Eliminare il **metodo Update().** Questa classe non sarà necessaria.

7.  Aggiungere il **metodo RequestTagSelection().** Questo metodo è il primo a essere chiamato quando un'immagine è stata acquisita e archiviata nel dispositivo ed è ora pronta per essere inviata *al servizio Visione personalizzata*, per il training. Questo metodo visualizza nell'interfaccia utente di training un set di parole chiave che l'utente può usare per contrassegnare l'immagine acquisita. Segnala anche alla classe *VoiceRecognizer* di iniziare ad ascoltare l'utente per l'input vocale.

    ```csharp
        internal void RequestTagSelection()
        {
            trainingUI_TextMesh.gameObject.SetActive(true);
            trainingUI_TextMesh.text = $" \nUse voice command \nto choose between the following tags: \nMouse\nKeyboard \nor say Discard";

            VoiceRecognizer.Instance.keywordRecognizer.Start();
        }
    ```

8.  Aggiungere il **metodo VerifyTag().** Questo metodo riceverà l'input vocale riconosciuto dalla **classe VoiceRecognizer** e ne verificherà la validità, quindi inizierà il processo di training.

    ```csharp
        /// <summary>
        /// Verify voice input against stored tags.
        /// If positive, it will begin the Service training process.
        /// </summary>
        internal void VerifyTag(string spokenTag)
        {
            if (spokenTag == Tags.Mouse.ToString() || spokenTag == Tags.Keyboard.ToString())
            {
                trainingUI_TextMesh.text = $"Tag chosen: {spokenTag}";
                VoiceRecognizer.Instance.keywordRecognizer.Stop();
                StartCoroutine(SubmitImageForTraining(ImageCapture.Instance.filePath, spokenTag));
            }
        }
    ```

9.  Aggiungere il **metodo SubmitImageForTraining().** Questo metodo avvia il processo di training Visione personalizzata Service. Il primo passaggio consiste nel recuperare **l'ID tag** dal servizio associato all'input vocale convalidato dall'utente. **L'ID tag** verrà quindi caricato insieme all'immagine.

    ```csharp
        /// <summary>
        /// Call the Custom Vision Service to submit the image.
        /// </summary>
        public IEnumerator SubmitImageForTraining(string imagePath, string tag)
        {
            yield return new WaitForSeconds(2);
            trainingUI_TextMesh.text = $"Submitting Image \nwith tag: {tag} \nto Custom Vision Service";
            string imageId = string.Empty;
            string tagId = string.Empty;

            // Retrieving the Tag Id relative to the voice input
            string getTagIdEndpoint = string.Format("{0}{1}/tags", url, projectId);
            using (UnityWebRequest www = UnityWebRequest.Get(getTagIdEndpoint))
            {
                www.SetRequestHeader("Training-Key", trainingKey);
                www.downloadHandler = new DownloadHandlerBuffer();
                yield return www.SendWebRequest();
                string jsonResponse = www.downloadHandler.text;

                Tags_RootObject tagRootObject = JsonConvert.DeserializeObject<Tags_RootObject>(jsonResponse);

                foreach (TagOfProject tOP in tagRootObject.Tags)
                {
                    if (tOP.Name == tag)
                    {
                        tagId = tOP.Id;
                    }             
                }
            }

            // Creating the image object to send for training
            List<IMultipartFormSection> multipartList = new List<IMultipartFormSection>();
            MultipartObject multipartObject = new MultipartObject();
            multipartObject.contentType = "application/octet-stream";
            multipartObject.fileName = "";
            multipartObject.sectionData = GetImageAsByteArray(imagePath);
            multipartList.Add(multipartObject);

            string createImageFromDataEndpoint = string.Format("{0}{1}/images?tagIds={2}", url, projectId, tagId);

            using (UnityWebRequest www = UnityWebRequest.Post(createImageFromDataEndpoint, multipartList))
            {
                // Gets a byte array out of the saved image
                imageBytes = GetImageAsByteArray(imagePath);           

                //unityWebRequest.SetRequestHeader("Content-Type", "application/octet-stream");
                www.SetRequestHeader("Training-Key", trainingKey);

                // The upload handler will help uploading the byte array with the request
                www.uploadHandler = new UploadHandlerRaw(imageBytes);

                // The download handler will help receiving the analysis from Azure
                www.downloadHandler = new DownloadHandlerBuffer();

                // Send the request
                yield return www.SendWebRequest();

                string jsonResponse = www.downloadHandler.text;

                ImageRootObject m = JsonConvert.DeserializeObject<ImageRootObject>(jsonResponse);
                imageId = m.Images[0].Image.Id;
            }
            trainingUI_TextMesh.text = "Image uploaded";
            StartCoroutine(TrainCustomVisionProject());
        }
    ```

10. Aggiungere il **metodo TrainCustomVisionProject().** Dopo che l'immagine è stata inviata e contrassegnata, questo metodo verrà chiamato. Verrà creata una nuova iterazione che verrà sottoposta a training con tutte le immagini precedenti inviate al servizio più l'immagine appena caricata. Al termine del training, questo metodo chiamerà un  metodo per impostare l'iterazione appena creata come **predefinita,** in modo che l'endpoint in uso per l'analisi sia l'iterazione con training più recente.

    ```csharp
        /// <summary>
        /// Call the Custom Vision Service to train the Service.
        /// It will generate a new Iteration in the Service
        /// </summary>
        public IEnumerator TrainCustomVisionProject()
        {
            yield return new WaitForSeconds(2);

            trainingUI_TextMesh.text = "Training Custom Vision Service";

            WWWForm webForm = new WWWForm();

            string trainProjectEndpoint = string.Format("{0}{1}/train", url, projectId);

            using (UnityWebRequest www = UnityWebRequest.Post(trainProjectEndpoint, webForm))
            {
                www.SetRequestHeader("Training-Key", trainingKey);
                www.downloadHandler = new DownloadHandlerBuffer();
                yield return www.SendWebRequest();
                string jsonResponse = www.downloadHandler.text;
                Debug.Log($"Training - JSON Response: {jsonResponse}");

                // A new iteration that has just been created and trained
                Iteration iteration = new Iteration();
                iteration = JsonConvert.DeserializeObject<Iteration>(jsonResponse);

                if (www.isDone)
                {
                    trainingUI_TextMesh.text = "Custom Vision Trained";

                    // Since the Service has a limited number of iterations available,
                    // we need to set the last trained iteration as default
                    // and delete all the iterations you dont need anymore
                    StartCoroutine(SetDefaultIteration(iteration)); 
                }
            }
        }
    ```

11. Aggiungere il **metodo SetDefaultIteration().** Questo metodo imposta l'iterazione creata in precedenza e con training su *Default*. Al termine, questo metodo dovrà eliminare l'iterazione precedente esistente nel servizio. Al momento della stesura di questo corso, nel servizio è consentito un limite massimo di dieci (10) iterazioni.

    ```csharp
        /// <summary>
        /// Set the newly created iteration as Default
        /// </summary>
        private IEnumerator SetDefaultIteration(Iteration iteration)
        {
            yield return new WaitForSeconds(5);
            trainingUI_TextMesh.text = "Setting default iteration";

            // Set the last trained iteration to default
            iteration.IsDefault = true;

            // Convert the iteration object as JSON
            string iterationAsJson = JsonConvert.SerializeObject(iteration);
            byte[] bytes = Encoding.UTF8.GetBytes(iterationAsJson);

            string setDefaultIterationEndpoint = string.Format("{0}{1}/iterations/{2}", 
                                                            url, projectId, iteration.Id);

            using (UnityWebRequest www = UnityWebRequest.Put(setDefaultIterationEndpoint, bytes))
            {
                www.method = "PATCH";
                www.SetRequestHeader("Training-Key", trainingKey);
                www.SetRequestHeader("Content-Type", "application/json");
                www.downloadHandler = new DownloadHandlerBuffer();

                yield return www.SendWebRequest();

                string jsonResponse = www.downloadHandler.text;

                if (www.isDone)
                {
                    trainingUI_TextMesh.text = "Default iteration is set \nDeleting Unused Iteration";
                    StartCoroutine(DeletePreviousIteration(iteration));
                }
            }
        }
    ```

12. Aggiungere il **metodo DeletePreviousIteration().** Questo metodo troverà ed eliminerà l'iterazione non predefinita precedente:

    ```csharp
        /// <summary>
        /// Delete the previous non-default iteration.
        /// </summary>
        public IEnumerator DeletePreviousIteration(Iteration iteration)
        {
            yield return new WaitForSeconds(5);

            trainingUI_TextMesh.text = "Deleting Unused \nIteration";

            string iterationToDeleteId = string.Empty;

            string findAllIterationsEndpoint = string.Format("{0}{1}/iterations", url, projectId);

            using (UnityWebRequest www = UnityWebRequest.Get(findAllIterationsEndpoint))
            {
                www.SetRequestHeader("Training-Key", trainingKey);
                www.downloadHandler = new DownloadHandlerBuffer();
                yield return www.SendWebRequest();

                string jsonResponse = www.downloadHandler.text;

                // The iteration that has just been trained
                List<Iteration> iterationsList = new List<Iteration>();
                iterationsList = JsonConvert.DeserializeObject<List<Iteration>>(jsonResponse);

                foreach (Iteration i in iterationsList)
                {
                    if (i.IsDefault != true)
                    {
                        Debug.Log($"Cleaning - Deleting iteration: {i.Name}, {i.Id}");
                        iterationToDeleteId = i.Id;
                        break;
                    }
                }
            }

            string deleteEndpoint = string.Format("{0}{1}/iterations/{2}", url, projectId, iterationToDeleteId);

            using (UnityWebRequest www2 = UnityWebRequest.Delete(deleteEndpoint))
            {
                www2.SetRequestHeader("Training-Key", trainingKey);
                www2.downloadHandler = new DownloadHandlerBuffer();
                yield return www2.SendWebRequest();
                string jsonResponse = www2.downloadHandler.text;

                trainingUI_TextMesh.text = "Iteration Deleted";
                yield return new WaitForSeconds(2);
                trainingUI_TextMesh.text = "Ready for next \ncapture";

                yield return new WaitForSeconds(2);
                trainingUI_TextMesh.text = "";
                ImageCapture.Instance.ResetImageCapture();
            }
        }
    ```

13. L'ultimo metodo da aggiungere in questa classe è **il metodo GetImageAsByteArray(),** usato nelle chiamate Web per convertire l'immagine acquisita in una matrice di byte.

    ```csharp
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

14. Assicurarsi di salvare le modifiche in **Visual Studio** prima di tornare a **Unity.**

## <a name="chapter-10---create-the-sceneorganiser-class"></a>Capitolo 10 - Creare la classe SceneOrganiser

Questa classe:

-   Creare un **oggetto Cursor** da collegare alla fotocamera principale.

-   Creare un **oggetto Label** che verrà visualizzato quando il servizio riconosce gli oggetti reali.

-   Configurare la fotocamera principale collegando i componenti appropriati.

-   In modalità **di** analisi, genera le etichette in fase di esecuzione, nello spazio mondo appropriato rispetto alla posizione della fotocamera principale e visualizza i dati ricevuti dal servizio Visione personalizzata.

-   Quando si è in **modalità training,** generare l'interfaccia utente che visualizza le diverse fasi del processo di training.

Per creare questa classe:

1.  Fare clic con il pulsante destro del **mouse all'interno della cartella** Script , quindi scegliere **Crea**  >  **\# script C**. Assegnare allo script *il nome SceneOrganiser*.

2.  Fare doppio clic sul nuovo script *SceneOrganiser* per aprirlo con **Visual Studio**.

3.  Sarà necessario un solo spazio dei nomi, rimuovere gli altri dalla classe *SceneOrganiser:*

    ```csharp
    using UnityEngine;
    ```

4.  Aggiungere quindi le variabili seguenti all'interno *della classe SceneOrganiser,* sopra il **metodo Start():**

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static SceneOrganiser Instance;

        /// <summary>
        /// The cursor object attached to the camera
        /// </summary>
        internal GameObject cursor;

        /// <summary>
        /// The label used to display the analysis on the objects in the real world
        /// </summary>
        internal GameObject label;

        /// <summary>
        /// Object providing the current status of the camera.
        /// </summary>
        internal TextMesh cameraStatusIndicator;

        /// <summary>
        /// Reference to the last label positioned
        /// </summary>
        internal Transform lastLabelPlaced;

        /// <summary>
        /// Reference to the last label positioned
        /// </summary>
        internal TextMesh lastLabelPlacedText;

        /// <summary>
        /// Current threshold accepted for displaying the label
        /// Reduce this value to display the recognition more often
        /// </summary>
        internal float probabilityThreshold = 0.5f;
    ```

5.  Eliminare i **metodi Start()** **e Update().**

6.  Subito sotto le variabili aggiungere il **metodo Awake(),** che inizializza la classe e configura la scena.

    ```csharp
        /// <summary>
        /// Called on initialization
        /// </summary>
        private void Awake()
        {
            // Use this class instance as singleton
            Instance = this;

            // Add the ImageCapture class to this GameObject
            gameObject.AddComponent<ImageCapture>();

            // Add the CustomVisionAnalyser class to this GameObject
            gameObject.AddComponent<CustomVisionAnalyser>();

            // Add the CustomVisionTrainer class to this GameObject
            gameObject.AddComponent<CustomVisionTrainer>();

            // Add the VoiceRecogniser class to this GameObject
            gameObject.AddComponent<VoiceRecognizer>();

            // Add the CustomVisionObjects class to this GameObject
            gameObject.AddComponent<CustomVisionObjects>();

            // Create the camera Cursor
            cursor = CreateCameraCursor();

            // Load the label prefab as reference
            label = CreateLabel();

            // Create the camera status indicator label, and place it above where predictions
            // and training UI will appear.
            cameraStatusIndicator = CreateTrainingUI("Status Indicator", 0.02f, 0.2f, 3, true);

            // Set camera status indicator to loading.
            SetCameraStatus("Loading");
        }
    ```

7.  Aggiungere ora il **metodo CreateCameraCursor()** che crea e posiziona il cursore Main Camera e il **metodo CreateLabel(),** che crea l'oggetto **Analysis Label.**

    ```csharp
        /// <summary>
        /// Spawns cursor for the Main Camera
        /// </summary>
        private GameObject CreateCameraCursor()
        {
            // Create a sphere as new cursor
            GameObject newCursor = GameObject.CreatePrimitive(PrimitiveType.Sphere);

            // Attach it to the camera
            newCursor.transform.parent = gameObject.transform;

            // Resize the new cursor
            newCursor.transform.localScale = new Vector3(0.02f, 0.02f, 0.02f);

            // Move it to the correct position
            newCursor.transform.localPosition = new Vector3(0, 0, 4);

            // Set the cursor color to red
            newCursor.GetComponent<Renderer>().material = new Material(Shader.Find("Diffuse"));
            newCursor.GetComponent<Renderer>().material.color = Color.green;

            return newCursor;
        }

        /// <summary>
        /// Create the analysis label object
        /// </summary>
        private GameObject CreateLabel()
        {
            // Create a sphere as new cursor
            GameObject newLabel = new GameObject();

            // Resize the new cursor
            newLabel.transform.localScale = new Vector3(0.01f, 0.01f, 0.01f);

            // Creating the text of the label
            TextMesh t = newLabel.AddComponent<TextMesh>();
            t.anchor = TextAnchor.MiddleCenter;
            t.alignment = TextAlignment.Center;
            t.fontSize = 50;
            t.text = "";

            return newLabel;
        }
    ```

8. Aggiungere il **metodo SetCameraStatus(),** che gestirà i messaggi destinati alla mesh di testo specificando lo stato della fotocamera.

    ```csharp
        /// <summary>
        /// Set the camera status to a provided string. Will be coloured if it matches a keyword.
        /// </summary>
        /// <param name="statusText">Input string</param>
        public void SetCameraStatus(string statusText)
        {
            if (string.IsNullOrEmpty(statusText) == false)
            {
                string message = "white";

                switch (statusText.ToLower())
                {
                    case "loading":
                        message = "yellow";
                        break;

                    case "ready":
                        message = "green";
                        break;

                    case "uploading image":
                        message = "red";
                        break;

                    case "looping capture":
                        message = "yellow";
                        break;

                    case "analysis":
                        message = "red";
                        break;
                }

                cameraStatusIndicator.GetComponent<TextMesh>().text = $"Camera Status:\n<color={message}>{statusText}..</color>";
            }
        }
    ```

9. Aggiungere i **metodi PlaceAnalysisLabel()** e **SetTagsToLastLabel(),** che generano e visualizzano i dati dal servizio Visione personalizzata nella scena.

    ```csharp
        /// <summary>
        /// Instantiate a label in the appropriate location relative to the Main Camera.
        /// </summary>
        public void PlaceAnalysisLabel()
        {
            lastLabelPlaced = Instantiate(label.transform, cursor.transform.position, transform.rotation);
            lastLabelPlacedText = lastLabelPlaced.GetComponent<TextMesh>();
        }

        /// <summary>
        /// Set the Tags as Text of the last label created. 
        /// </summary>
        public void SetTagsToLastLabel(AnalysisObject analysisObject)
        {
            lastLabelPlacedText = lastLabelPlaced.GetComponent<TextMesh>();

            if (analysisObject.Predictions != null)
            {
                foreach (Prediction p in analysisObject.Predictions)
                {
                    if (p.Probability > 0.02)
                    {
                        lastLabelPlacedText.text += $"Detected: {p.TagName} {p.Probability.ToString("0.00 \n")}";
                        Debug.Log($"Detected: {p.TagName} {p.Probability.ToString("0.00 \n")}");
                    }
                }
            }
        }
    ```

10. Infine, aggiungere il metodo **CreateTrainingUI(),** che genera l'interfaccia utente visualizzando le varie fasi del processo di training quando l'applicazione è in modalità training. Questo metodo verrà inoltre sfruttato per creare l'oggetto stato della fotocamera.

    ```csharp
        /// <summary>
        /// Create a 3D Text Mesh in scene, with various parameters.
        /// </summary>
        /// <param name="name">name of object</param>
        /// <param name="scale">scale of object (i.e. 0.04f)</param>
        /// <param name="yPos">height above the cursor (i.e. 0.3f</param>
        /// <param name="zPos">distance from the camera</param>
        /// <param name="setActive">whether the text mesh should be visible when it has been created</param>
        /// <returns>Returns a 3D text mesh within the scene</returns>
        internal TextMesh CreateTrainingUI(string name, float scale, float yPos, float zPos, bool setActive)
        {
            GameObject display = new GameObject(name, typeof(TextMesh));
            display.transform.parent = Camera.main.transform;
            display.transform.localPosition = new Vector3(0, yPos, zPos);
            display.SetActive(setActive);
            display.transform.localScale = new Vector3(scale, scale, scale);
            display.transform.rotation = new Quaternion();
            TextMesh textMesh = display.GetComponent<TextMesh>();
            textMesh.anchor = TextAnchor.MiddleCenter;
            textMesh.alignment = TextAlignment.Center;
            return textMesh;
        }
    ```

11. Assicurarsi di salvare le modifiche in **Visual Studio** prima di tornare a **Unity.**

> [!IMPORTANT]
> Prima di continuare, aprire la **classe CustomVisionAnalyser** e all'interno del metodo **AnalyseLastImageCaptured()** rimuovere il commento *dalle* righe seguenti:
>
> ```csharp
>   AnalysisObject analysisObject = new AnalysisObject();
>   analysisObject = JsonConvert.DeserializeObject<AnalysisObject>(jsonResponse);
>   SceneOrganiser.Instance.SetTagsToLastLabel(analysisObject);
> ```

## <a name="chapter-11---create-the-imagecapture-class"></a>Capitolo 11 - Creare la classe ImageCapture

La classe successiva che si creerà è *la classe ImageCapture.*

Questa classe è responsabile di:

-   Acquisizione di un'immagine con HoloLens fotocamera e archiviazione nella *cartella app.*

-   Gestione dei movimenti tocco da parte dell'utente.

-   Gestione del *valore Enum* che determina se l'applicazione verrà eseguita in *modalità di* analisi o *modalità di* training.

Per creare questa classe:

1.  Passare alla cartella **Scripts** creata in precedenza.

2.  Fare clic con il pulsante destro del mouse all'interno della **cartella , quindi scegliere > script C \#**. Assegnare allo script *il nome ImageCapture*.

3.  Fare doppio clic sul nuovo script **ImageCapture** per aprirlo con **Visual Studio**.

4.  Sostituire gli spazi dei nomi all'inizio del file con quanto segue:

    ```csharp
    using System;
    using System.IO;
    using System.Linq;
    using UnityEngine;
    using UnityEngine.XR.WSA.Input;
    using UnityEngine.XR.WSA.WebCam;
    ```

5.  Aggiungere quindi le variabili seguenti all'interno *della classe ImageCapture,* sopra il **metodo Start():**

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
        /// Loop timer
        /// </summary>
        private float secondsBetweenCaptures = 10f;

        /// <summary>
        /// Application main functionalities switch
        /// </summary>
        internal enum AppModes {Analysis, Training }
        
        /// <summary>
        /// Local variable for current AppMode
        /// </summary>
        internal AppModes AppMode { get; private set; }

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

            // Change this flag to switch between Analysis Mode and Training Mode 
            AppMode = AppModes.Training;
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

            // Subscribing to the HoloLens API gesture recognizer to track user gestures
            recognizer = new GestureRecognizer();
            recognizer.SetRecognizableGestures(GestureSettings.Tap);
            recognizer.Tapped += TapHandler;
            recognizer.StartCapturingGestures();

            SceneOrganiser.Instance.SetCameraStatus("Ready");
        }
    ```

7.  Implementare un gestore che verrà chiamato quando si verifica un movimento tocco.

    ```csharp
        /// <summary>
        /// Respond to Tap Input.
        /// </summary>
        private void TapHandler(TappedEventArgs obj)
        {
            switch (AppMode)
            {
                case AppModes.Analysis:
                    if (!captureIsActive)
                    {
                        captureIsActive = true;

                        // Set the cursor color to red
                        SceneOrganiser.Instance.cursor.GetComponent<Renderer>().material.color = Color.red;
                        
                        // Update camera status to looping capture.
                        SceneOrganiser.Instance.SetCameraStatus("Looping Capture");

                        // Begin the capture loop
                        InvokeRepeating("ExecuteImageCaptureAndAnalysis", 0, secondsBetweenCaptures);
                    }
                    else
                    {
                        // The user tapped while the app was analyzing 
                        // therefore stop the analysis process
                        ResetImageCapture();
                    }
                    break;

                case AppModes.Training:
                    if (!captureIsActive)
                    {
                        captureIsActive = true;

                        // Call the image capture
                        ExecuteImageCaptureAndAnalysis();

                        // Set the cursor color to red
                        SceneOrganiser.Instance.cursor.GetComponent<Renderer>().material.color = Color.red;

                        // Update camera status to uploading image.
                        SceneOrganiser.Instance.SetCameraStatus("Uploading Image");
                    }              
                    break;
            }     
        }
    ```

    > [!NOTE] 
    > In *modalità Analisi,* il **metodo TapHandler** funge da opzione per avviare o arrestare il ciclo di acquisizione di foto.
    >
    > In *modalità Training* acquisisce un'immagine dalla fotocamera.
    >
    > Quando il cursore è verde, significa che la fotocamera è disponibile per l'immagine.
    >
    > Quando il cursore è rosso, significa che la fotocamera è occupata.

8.  Aggiungere il metodo utilizzato dall'applicazione per avviare il processo di acquisizione dell'immagine e archiviare l'immagine.

    ```csharp
        /// <summary>
        /// Begin process of Image Capturing and send To Azure Custom Vision Service.
        /// </summary>
        private void ExecuteImageCaptureAndAnalysis()
        {
            // Update camera status to analysis.
            SceneOrganiser.Instance.SetCameraStatus("Analysis");

            // Create a label in world space using the SceneOrganiser class 
            // Invisible at this point but correctly positioned where the image was taken
            SceneOrganiser.Instance.PlaceAnalysisLabel();

            // Set the camera resolution to be the highest possible
            Resolution cameraResolution = PhotoCapture.SupportedResolutions.OrderByDescending((res) => res.width * res.height).First();

            Texture2D targetTexture = new Texture2D(cameraResolution.width, cameraResolution.height);

            // Begin capture process, set the image format
            PhotoCapture.CreateAsync(false, delegate (PhotoCapture captureObject)
            {
                photoCaptureObject = captureObject;

                CameraParameters camParameters = new CameraParameters
                {
                    hologramOpacity = 0.0f,
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

9.  Aggiungere i gestori che verranno chiamati quando la foto è stata acquisita e per quando è pronta per l'analisi. Il risultato viene quindi passato a *CustomVisionAnalyser* o *CustomVisionTrainer* a seconda della modalità in cui è impostato il codice.

    ```csharp
        /// <summary>
        /// Register the full execution of the Photo Capture. 
        /// </summary>
        void OnCapturedPhotoToDisk(PhotoCapture.PhotoCaptureResult result)
        {
                // Call StopPhotoMode once the image has successfully captured
                photoCaptureObject.StopPhotoModeAsync(OnStoppedPhotoMode);
        }


        /// <summary>
        /// The camera photo mode has stopped after the capture.
        /// Begin the Image Analysis process.
        /// </summary>
        void OnStoppedPhotoMode(PhotoCapture.PhotoCaptureResult result)
        {
            Debug.LogFormat("Stopped Photo Mode");
        
            // Dispose from the object in memory and request the image analysis 
            photoCaptureObject.Dispose();
            photoCaptureObject = null;

            switch (AppMode)
            {
                case AppModes.Analysis:
                    // Call the image analysis
                    StartCoroutine(CustomVisionAnalyser.Instance.AnalyseLastImageCaptured(filePath));
                    break;

                case AppModes.Training:
                    // Call training using captured image
                    CustomVisionTrainer.Instance.RequestTagSelection();
                    break;
            }
        }

        /// <summary>
        /// Stops all capture pending actions
        /// </summary>
        internal void ResetImageCapture()
        {
            captureIsActive = false;

            // Set the cursor color to green
            SceneOrganiser.Instance.cursor.GetComponent<Renderer>().material.color = Color.green;

            // Update camera status to ready.
            SceneOrganiser.Instance.SetCameraStatus("Ready");

            // Stop the capture loop if active
            CancelInvoke();
        }
    ```

10. Assicurarsi di salvare le modifiche in **Visual Studio** prima di tornare a **Unity.**

11. Ora che tutti gli script sono stati completati, tornare all'editor di Unity, quindi fare clic e trascinare la classe **SceneOrganiser** dalla cartella **Scripts** all'oggetto **Main Camera** (Fotocamera principale) nel pannello *Hierarchy (Gerarchia).*

## <a name="chapter-12---before-building"></a>Capitolo 12 - Prima della compilazione

Per eseguire un test completo dell'applicazione, è necessario eseguire il sideload nell'HoloLens.

Prima di procedere, verificare che:

- Tutte le impostazioni indicate nel [capitolo 2](#chapter-2---training-your-custom-vision-project) sono impostate correttamente.

- Tutti i campi della fotocamera **principale,** il pannello di controllo, vengono assegnati correttamente.

- Lo script **SceneOrganiser** è collegato **all'oggetto Main Camera.**

- Assicurarsi di inserire la **chiave di stima** nella variabile **predictionKey.**

- L'endpoint di **stima è stato** inserito nella variabile **predictionEndpoint.**

- La chiave di **training è stata** inserita nella variabile **trainingKey** della *classe CustomVisionTrainer.*

- L'ID **Project è stato** inserito nella variabile **projectId** della *classe CustomVisionTrainer.*

## <a name="chapter-13---build-and-sideload-your-application"></a>Capitolo 13: Compilare e sideload dell'applicazione

Per iniziare il *processo di* compilazione:

1.  Passare a **File > Build Impostazioni**.

2.  Selezionare **Unity C \# Projects (Progetti Unity C).**

3.  Fare clic su **Compila**. Unity avvierà una **Esplora file,** in cui è necessario creare e quindi selezionare una cartella in cui compilare l'app. Creare la cartella e assegnare alla cartella il nome **App**. Quindi, con la **cartella App** selezionata, fare clic su **Seleziona cartella**.

4.  Unity inizierà a compilare il progetto nella **cartella App.**

5.  Al termine della compilazione, Unity aprirà una finestra Esplora file nella posizione **della** compilazione(controllare la barra delle applicazioni, perché potrebbe non essere sempre visualizzata sopra le finestre, ma invierà una notifica dell'aggiunta di una nuova finestra).

Per eseguire la distribuzione HoloLens:

1.  Sarà necessario l'indirizzo IP del HoloLens (per la distribuzione remota) e per assicurarsi che l'HoloLens sia in **modalità sviluppatore.** Per eseguire questa operazione:

    1.  Mentre si è HoloLens, aprire il **Impostazioni**.

    2.  Passare a **Network & Internet** Wi-Fi Advanced Options (Opzioni avanzate  >  **wi-fi**  >  **Internet)**

    3.  Prendere nota **dell'indirizzo IPv4.**

    4.  Tornare quindi a **Impostazioni** e quindi a Update & Security for Developers **(Aggiorna sicurezza per**  >  **sviluppatori)**

    5.  Impostare **la modalità sviluppatore su**.

2.  Passare alla nuova build di Unity (la **cartella App)** e aprire il file della soluzione **con Visual Studio**.

3.  In Configurazione *soluzione selezionare* **Debug.**

4.  In *Piattaforma soluzione selezionare* **x86, Computer remoto.** Verrà richiesto di inserire **l'indirizzo IP** di un dispositivo remoto (il HoloLens, in questo caso, che è stato specificato.

    ![Indirizzo IP impostato](images/AzureLabs-Lab302b-34.png)

5. Passare al menu **Compila** e fare clic su **Distribuisci soluzione** per eseguire il sideload dell'applicazione nel HoloLens.

6. L'app dovrebbe ora essere visualizzata nell'elenco delle app installate nel HoloLens, pronto per l'avvio.

> [!NOTE]
> Per eseguire la distribuzione  in visore VR immersive,  impostare Piattaforma soluzione su Computer locale e impostare Configurazione su *Debug*, con *x86* come  **Piattaforma**. Eseguire quindi la distribuzione nel computer locale, usando la **voce di** menu Compila e selezionando *Distribuisci soluzione.* 

## <a name="to-use-the-application"></a>Per usare l'applicazione:

Per alternare la  funzionalità  dell'app tra la modalità training e la modalità stima, è necessario aggiornare la variabile **AppMode,** che si trova nel metodo **Awake()** all'interno *della classe ImageCapture.*

```
        // Change this flag to switch between Analysis mode and Training mode 
        AppMode = AppModes.Training;
```
oppure
```
        // Change this flag to switch between Analysis mode and Training mode 
        AppMode = AppModes.Analysis;
```

In *modalità training:*

- Esaminare mouse **o** tastiera **e** usare il **movimento Tocco**.

- Verrà quindi visualizzato un testo in cui viene chiesto di specificare un tag.

- Pronunciare **mouse** o **tastiera.**


In *modalità* Stima:

- Osservare un oggetto e usare il movimento **Tocco**.

- Verrà visualizzato testo che fornisce l'oggetto rilevato, con la probabilità più alta (normalizzata).

## <a name="chapter-14---evaluate-and-improve-your-custom-vision-model"></a>Capitolo 14- Valutare e migliorare il modello Visione personalizzata

Per rendere il servizio più accurato, è necessario continuare a eseguire il training del modello usato per la stima. Questa operazione viene eseguita usando la nuova applicazione, con le modalità di *training* e stima, con la seconda che richiede di visitare il portale, come viene trattato in questo capitolo.  Prepararsi a rivedere il portale più volte per migliorare continuamente il modello.

1. Accedere di nuovo al portale di Azure Visione personalizzata e, una volta nel progetto, selezionare la *scheda Predictions* (Stime) nella parte superiore centrale della pagina:

    ![Selezionare la scheda predictions (Stime)](images/AzureLabs-Lab302b-35.png)

2. Verranno visualizzate tutte le immagini inviate al servizio durante l'esecuzione dell'applicazione. Se si passa il mouse sulle immagini, verranno fornite le stime effettuate per tale immagine:

    ![Elenco di immagini di stima](images/AzureLabs-Lab302b-36.png)

3. Selezionare una delle immagini per aprirla. Una volta aperte, verranno visualizzati a destra le stime effettuate per l'immagine. Se le stime sono corrette e si vuole aggiungere questa immagine al modello di training del servizio, fare clic sulla casella di input *Tag* personali e selezionare il tag da associare. Al termine, fare clic sul *pulsante Salva e chiudi* in basso a destra e continuare con l'immagine successiva.

    ![Selezionare l'immagine da aprire](images/AzureLabs-Lab302b-37.png)

4. Quando si torna alla griglia delle immagini, si noterà che le immagini a cui sono stati aggiunti tag (e salvati) verranno rimosse. Se si trovano immagini che non hanno l'elemento con tag, è possibile eliminarle facendo clic sul segno di spunta sull'immagine (può farlo per diverse immagini) e quindi facendo clic su *Elimina* nell'angolo superiore destro della pagina della griglia. Nella finestra popup seguente è possibile fare clic rispettivamente su *Sì,* Elimina o *Su No* per confermare l'eliminazione o annullarla. 

    ![Eliminare le immagini](images/AzureLabs-Lab302b-38.png)

5. Quando si è pronti per continuare, fare clic sul pulsante *verde Train (Training)* in alto a destra. Il training del modello di servizio verrà ora creato con tutte le immagini fornite, in modo da renderlo più accurato. Al termine del training, assicurarsi di fare clic sul pulsante Make *default* (Rendi predefinito) ancora una volta, in modo che *l'URL* di stima continui a usare l'iterazione più aggiornata del servizio.

    ![Start training service model (Avvia modello di servizio ](images/AzureLabs-Lab302b-39.png) ![ di training) Selezionare l'opzione make default (Imposta come predefinito)](images/AzureLabs-Lab302b-40.png)

## <a name="your-finished-custom-vision-api-application"></a>Applicazione API Visione personalizzata completata

È stata compilata un'app di realtà mista che sfrutta l'API di Azure Visione personalizzata per riconoscere gli oggetti reali, eseguire il training del modello di servizio e visualizzare l'attendibilità di ciò che è stato visto.

![Esempio di progetto completato](images/AzureLabs-Lab302b-00.png)

## <a name="bonus-exercises"></a>Esercizi aggiuntivi

### <a name="exercise-1"></a>Esercizio 1

Eseguire il training **Visione personalizzata servizio per** riconoscere più oggetti.

### <a name="exercise-2"></a>Esercizio 2

Per espandere le informazioni apprese, completare gli esercizi seguenti:

Riprodurre un suono quando viene riconosciuto un oggetto.

### <a name="exercise-3"></a>Esercizio 3

Usare l'API per eseguire di nuovo il training del servizio con le stesse immagini analizzate dall'app, in modo da rendere il servizio più accurato (eseguire contemporaneamente sia previsioni che training).
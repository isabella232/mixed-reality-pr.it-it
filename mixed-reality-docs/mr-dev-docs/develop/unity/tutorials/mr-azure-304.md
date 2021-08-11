---
title: HoloLens (prima generazione) e Azure 304 - Riconoscimento del viso
description: Completa questo corso per informazioni su come implementare il riconoscimento volto di Azure in un'applicazione di realtà mista.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure, mixed reality, academy, unity, tutorial, api, riconoscimento del viso, hololens, immersive, vr, Windows 10, Visual Studio
ms.openlocfilehash: 2547b61669884c524fdd605240322dc9d568039b5a202d0a411317b0e83bd547
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115219562"
---
# <a name="hololens-1st-gen-and-azure-304-face-recognition"></a>HoloLens (prima generazione) e Azure 304: riconoscimento del viso

<br>

>[!NOTE]
>Le esercitazioni di Mixed Reality Academy sono state progettate in base a HoloLens (prima generazione) e ai visori VR immersive di realtà mista.  Pertanto, riteniamo importante lasciarle a disposizione degli sviluppatori a cui serve ancora materiale sussidiario per lo sviluppo di questi dispositivi.  Queste esercitazioni **_non_** verranno aggiornate con i set di strumenti o le interazioni più recenti usati per HoloLens 2.  Rimarranno invariate per consentire di continuare a lavorare sui dispositivi supportati. In futuro verrà pubblicata una nuova serie di esercitazioni che illustrano come sviluppare per HoloLens 2.  Questa informativa verrà aggiornata con un collegamento a tali esercitazioni al momento della pubblicazione.

<br>

![risultato del completamento del corso](images/AzureLabs-Lab4-00.png)

In questo corso si apprenderà come aggiungere funzionalità di riconoscimento del viso a un'applicazione di realtà mista, usando Servizi cognitivi di Azure, con l'API Viso Microsoft.

*L'API Viso* di Azure è un servizio Microsoft che offre agli sviluppatori gli algoritmi viso più avanzati, tutti nel cloud. *L'API Viso* ha due funzioni principali: rilevamento del viso con attributi e riconoscimento del viso. In questo modo gli sviluppatori possono semplicemente impostare un set di gruppi per i visi e quindi inviare immagini di query al servizio in un secondo momento, per determinare a chi appartiene un viso. Per altre informazioni, visitare la pagina [Riconoscimento facciale di Azure](https://azure.microsoft.com/services/cognitive-services/face/).

Dopo aver completato questo corso, si avrà un'applicazione HoloLens realtà mista, che sarà in grado di eseguire le operazioni seguenti:

1. Usare un **movimento tocco** per avviare l'acquisizione di un'immagine usando la fotocamera HoloLens integrata. 
2. Inviare l'immagine acquisita al *servizio API Viso di Azure.*
3. Ricevere i risultati dell'algoritmo *API Viso.*
4. Usare una semplice Interfaccia utente, per visualizzare il nome delle persone corrispondenti.

Verrà illustrato come ottenere i risultati dal servizio API Viso nell'applicazione di realtà mista basata su Unity.

Nell'applicazione è necessario sapere come integrare i risultati con la progettazione. Questo corso è progettato per illustrare come integrare un servizio di Azure con il servizio Unity Project. È compito dell'utente usare le conoscenze acquisite da questo corso per migliorare l'applicazione di realtà mista.

## <a name="device-support"></a>Supporto di dispositivi

<table>
<tr>
<th>Corso</th><th style="width:150px"> <a href="/hololens/hololens1-hardware">HoloLens</a></th><th style="width:150px"> <a href="../../../discover/immersive-headset-hardware-details.md">Visori VR immersive</a></th>
</tr><tr>
<td> MR e Azure 304: Riconoscimento del volto</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

> [!NOTE]
> Anche se questo corso è in HoloLens, è anche possibile applicare ciò che si apprende in questo corso per Windows Mixed Reality visori vr immersivi. Poiché i visori VR immersive non hanno fotocamere accessibili, è necessaria una fotocamera esterna connessa al PC. Man mano che si segue il corso, verranno visualizzati note sulle modifiche che potrebbe essere necessario applicare per supportare visori VR immersive.

## <a name="prerequisites"></a>Prerequisiti

> [!NOTE]
> Questa esercitazione è progettata per sviluppatori con esperienza di base con Unity e C#. Tenere inoltre presente che i prerequisiti e le istruzioni scritte in questo documento rappresentano ciò che è stato testato e verificato al momento della scrittura (maggio 2018). È possibile usare il software più recente, come elencato nell'articolo installare gli strumenti, anche se non è consigliabile presumere che le informazioni in questo corso corrispondano perfettamente a quelle disponibili nel software più recente rispetto a quelle elencate di seguito. [](../../install-the-tools.md)

Per questo corso è consigliabile usare l'hardware e il software seguenti:

- Un PC di sviluppo, [compatibile con Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) per lo sviluppo di visori vr immersive
- [Windows 10 Fall Creators Update (o versione successiva) con la modalità sviluppatore abilitata](../../install-the-tools.md)
- [L'SDK Windows 10 più recente](../../install-the-tools.md)
- [Unity 2017.4](../../install-the-tools.md)
- [Visual Studio 2017](../../install-the-tools.md)
- Visore [Windows Mixed Reality vr o](../../../discover/immersive-headset-hardware-details.md) visore [Microsoft HoloLens](/hololens/hololens1-hardware) con la modalità sviluppatore abilitata
- Una fotocamera connessa al PC (per lo sviluppo di visori immersivi)
- Accesso a Internet per la configurazione di Azure e il recupero dell'API Viso

## <a name="before-you-start"></a>Prima di iniziare

1.  Per evitare problemi durante la compilazione di questo progetto, è consigliabile creare il progetto indicato in questa esercitazione in una cartella radice o quasi radice (i percorsi di cartelle lunghe possono causare problemi in fase di compilazione).
2.  Configurare e testare il HoloLens. Se è necessario supporto per la configurazione del HoloLens, visitare l'articolo HoloLens [setup .](/hololens/hololens-setup) 
3.  È buona idea eseguire calibrazione e ottimizzazione dei sensori quando si inizia a sviluppare una nuova app HoloLens (talvolta può essere utile per eseguire queste attività per ogni utente). 

Per informazioni sulla calibrazione, seguire questo [collegamento all'HoloLens calibrazione.](/hololens/hololens-calibration#hololens-2)

Per informazioni sull'ottimizzazione dei sensori, seguire questo [collegamento all'articolo HoloLens Sensor Tuning](/hololens/hololens-updates).

## <a name="chapter-1---the-azure-portal"></a>Capitolo 1 - Portale di Azure

Per usare il *servizio API Viso* in Azure, è necessario configurare un'istanza del servizio per essere resa disponibile per l'applicazione.

1.  Accedere prima di tutto al portale [di Azure.](https://portal.azure.com) 

    > [!NOTE]
    > Se non si dispone già di un account Azure, è necessario crearne uno. Se si sta seguendo questa esercitazione in una situazione di classe o di lab, chiedere all'insegnante o a uno dei prottori di assistenza per la configurazione del nuovo account.

2.  Dopo aver eseguito l'accesso, fare clic su **Nuovo** nell'angolo in alto a sinistra e cercare *API Viso*, premere **INVIO.**

    ![cercare l'API viso](images/AzureLabs-Lab4-01.png)

    > [!NOTE]
    > La parola **Nuovo** potrebbe essere stata sostituita con **Crea una** risorsa nei portali più nuovi.

3.  La nuova pagina fornirà una descrizione del servizio *API Viso.* Nella parte inferiore sinistra del prompt selezionare il **pulsante Crea** per creare un'associazione con questo servizio.

    ![informazioni sull'API viso](images/AzureLabs-Lab4-02.png)

4.  Dopo aver fatto clic su **Crea**:

    1. Inserire il nome desiderato per questa istanza del servizio.

    2. Selezionare una sottoscrizione.

    3. Selezionare il piano tariffario appropriato, se questa è la prima volta che si crea un servizio *API Viso,* dovrebbe essere disponibile un piano gratuito (denominato F0).

    4. Scegliere un **gruppo di risorse** o crearne uno nuovo. Un gruppo di risorse consente di monitorare, controllare l'accesso, effettuare il provisioning e gestire la fatturazione per una raccolta di asset di Azure. È consigliabile mantenere tutti i servizi di Azure associati a un singolo progetto (ad esempio, questi lab) in un gruppo di risorse comune. 

        > Per altre informazioni sui gruppi di risorse di Azure, vedere [l'articolo gruppo di risorse](/azure/azure-resource-manager/resource-group-portal).

    5. L'app UWP Person **Maker,** che verrà utilizzata in un secondo momento, richiede l'uso di "Stati Uniti occidentali" per la posizione.

    6. È anche necessario verificare di aver compreso i termini e le condizioni applicati al servizio.

    7. Selezionare **Crea*.**

        ![creare il servizio API viso](images/AzureLabs-Lab4-03.png)

5.  Dopo aver fatto clic su **Crea*,** è necessario attendere la creazione del servizio. L'operazione potrebbe richiedere un minuto.

6.  Una volta creata l'istanza del servizio, nel portale verrà visualizzata una notifica.

    ![notifica di creazione del servizio](images/AzureLabs-Lab4-04.png)

7.  Fare clic sulle notifiche per esplorare la nuova istanza del servizio.

    ![passare alla notifica della risorsa](images/AzureLabs-Lab4-05.png)

8.  Quando si è pronti, fare **clic sul pulsante** Vai alla risorsa nella notifica per esplorare la nuova istanza del servizio.

    ![accedere ai tasti api viso](images/AzureLabs-Lab4-06.png)

9.  In questa esercitazione, l'applicazione dovrà effettuare chiamate al servizio, operazione eseguita tramite la sottoscrizione del servizio "chiave". Nella *pagina Avvio rapido,* del servizio *API Viso,* il primo punto è il numero 1, per *afferrare le chiavi.*

10. Nella pagina Servizio selezionare  il collegamento ipertestuale Chiavi blu (se  nella pagina Avvio rapido) o il collegamento Chiavi nel menu di spostamento dei servizi (a sinistra, denotato dall'icona "chiave"), per visualizzare le chiavi. 

    > [!NOTE] 
    > Prendere nota di una delle chiavi e proteggerla, perché sarà necessaria in un secondo momento.

## <a name="chapter-2---using-the-person-maker-uwp-application"></a>Capitolo 2 - Uso dell'applicazione UWP "Person Maker"

Assicurarsi di scaricare l'applicazione UWP precompilato denominata [Person Maker.](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20304%20-%20Face%20recognition/PersonMaker.zip) Questa app non è il prodotto finale per questo corso, ma solo uno strumento che consente di creare le voci di Azure su cui si baserà il progetto successivo.

**Person Maker** consente di creare voci di Azure, associate a persone e gruppi di persone. L'applicazione inserirà tutte le informazioni necessarie in un formato che potrà quindi essere usato in un secondo momento da FaceAPI per riconoscere i visi delle persone aggiunte. 

> [IMPORTANTE] **Person Maker** usa alcune limitazioni di base, per garantire che non si superi il numero di chiamate al servizio al minuto per il **livello di sottoscrizione gratuito**. Il testo verde nella parte superiore verrà modificato in rosso e verrà aggiornato come "ACTIVE" quando si verifica la limitazione. In questo caso, è sufficiente attendere l'applicazione (attenderà che possa continuare ad accedere al servizio viso, aggiornando come 'IN-ACTIVE' quando sarà possibile usarlo di nuovo).

Questa applicazione usa le *librerie Microsoft.ProjectOxford.Face,* che consentono di usare completamente l'API Viso. Questa libreria è disponibile gratuitamente come NuGet pacchetto. Per altre informazioni su questo e simili, vedere l'articolo di riferimento [sulle API](/azure/cognitive-services/face/apireference).

> [!NOTE] 
> Questi sono solo i passaggi necessari. Le istruzioni per eseguire queste operazioni sono più avanti nel documento. **L'app Person Maker** consente di:
>
> - Creare un *gruppo di* persone, ovvero un gruppo costituito da diverse persone che si desidera associare. Con l'account Azure è possibile ospitare più gruppi di persone.
>
> - Creare una *persona*, che è membro di un gruppo di persone. A ogni persona sono associate diverse *immagini* del viso.
>
> -  Assegnare *immagini del* viso a *una persona* per consentire al servizio API Viso di Azure di riconoscere una *persona* dal viso *corrispondente.*
>
> -  *Training* del *servizio API Viso di Azure*.

Tenere presente che per eseguire il training di questa app per riconoscere le persone, sono necessarie dieci (10) foto da vicino di ogni persona che si vuole aggiungere al gruppo di persone. L Windows 10 App Cam può essere utile per eseguire queste operazioni. È necessario assicurarsi che ogni foto sia chiara (evitare sfocature, offuscare o essere troppo distante dal soggetto), avere la foto in formato di file jpg o png, con dimensioni del file di immagine non superiori a **4 MB** e non inferiori a **1 KB.**

> [!NOTE]
> Se si segue questa esercitazione, non usare il proprio viso per il training, perché quando si HoloLens, non è possibile guardare se stessi. Usare il viso di un collega o di un collega.

Esecuzione **di Person Maker:**

1.  Aprire la **cartella PersonMaker** e fare doppio clic sulla *soluzione PersonMaker* per aprirla con *Visual Studio*.

2.  Quando la *soluzione PersonMaker* è aperta, assicurarsi che:

    1. La *configurazione della soluzione* è impostata su **Debug**.

    2. La *piattaforma della soluzione* è impostata su **x86**

    3. La *piattaforma di destinazione* è computer **locale.**

    4.  Potrebbe anche essere necessario ripristinare NuGet *pacchetti* (fare  clic con il pulsante destro del mouse sulla soluzione e **scegliere Ripristina** NuGet pacchetti ).

3.  Fare *clic su Computer locale* per avviare l'applicazione. Tenere presente che su schermi più piccoli tutto il contenuto potrebbe non essere visibile, anche se è possibile scorrere più in basso per visualizzarlo.

    ![Interfaccia utente di Person Maker](images/AzureLabs-Lab4-07.png)

4.  Inserire la **chiave di autenticazione di Azure,** che si dovrebbe avere, dal servizio API *Viso* all'interno di Azure.

5.  Inserisci:

    1. ID *da* assegnare al gruppo *di persone.* L'ID deve essere minuscolo, senza spazi. Prendere nota di questo ID, perché sarà necessario in un secondo momento nel progetto Unity.
    2. Nome *da* assegnare al gruppo *di persone* (può contenere spazi).


6.  Premere **il pulsante Crea gruppo di** persone. Sotto il pulsante dovrebbe essere visualizzato un messaggio di conferma.

> [!NOTE]
> Se si verifica un errore "Accesso negato", controllare la posizione impostata per il servizio di Azure. Come indicato in precedenza, questa app è progettata per "Stati Uniti occidentali".

> [!IMPORTANT]
> Si noterà che è  anche possibile fare clic sul pulsante Recupera un gruppo noto: questo è per se è già stato creato un gruppo di persone e si vuole usarlo, anziché crearne uno nuovo. Tenere presente che se si fa clic su Crea un *gruppo di* persone con un gruppo noto, verrà recuperato anche un gruppo.

7.  Inserire il *nome* della *persona* che si vuole creare.

    1. Fare clic **sul pulsante Crea** persona.

    2. Sotto il pulsante dovrebbe essere visualizzato un messaggio di conferma.

    3. Se si vuole eliminare una persona creata in precedenza, è possibile scrivere il nome nella casella di testo e premere **Elimina persona**

8.  Assicurarsi di conoscere la posizione di dieci (10) foto della persona che si vuole aggiungere al gruppo.

9.  Premere **Crea e apri cartella** per aprire Windows Explorer nella cartella associata alla persona. Aggiungere le dieci (10) immagini nella cartella. Devono essere in *formato JPG* *o PNG.*

10. Fare clic **su Invia ad Azure**. Un contatore mostrerà lo stato dell'invio, seguito da un messaggio al termine.

11. Al termine del contatore e visualizzato un messaggio di conferma, fare clic su Train to train your Service **(Training** per eseguire il training del servizio).

Al termine del processo, si è pronti per passare a Unity.

## <a name="chapter-3---set-up-the-unity-project"></a>Capitolo 3 - Configurare il progetto Unity

Di seguito è riportata una configurazione tipica per lo sviluppo con la realtà mista e, di conseguenza, è un buon modello per altri progetti.

1.  Aprire *Unity* e fare clic su **Nuovo**. 

    ![Avviare il nuovo progetto Unity.](images/AzureLabs-Lab4-08.png)

2.  È ora necessario specificare un nome Project Unity. Inserire **MR_FaceRecognition**. Assicurarsi che il tipo di progetto sia impostato su **3D.** Impostare Percorso **su** un percorso appropriato per l'utente (tenere presente che più vicino alle directory radice è meglio). Fare quindi clic **su Crea progetto**.

    ![Specificare i dettagli per il nuovo progetto Unity.](images/AzureLabs-Lab4-09.png)

3.  Con Unity aperto, è opportuno controllare che **l'editor di script predefinito** sia impostato su **Visual Studio**. Passare a **Modifica > preferenze** e quindi dalla nuova finestra passare a Strumenti **esterni**. Modificare **Editor script esterni** in Visual Studio **2017.** Chiudere la **finestra** Preferenze.

    ![Aggiornare le preferenze dell'editor di script.](images/AzureLabs-Lab4-10.png)

4.  Passare quindi a **File > Build Impostazioni** e passare alla piattaforma Universal Windows **Platform** facendo clic sul **pulsante Cambia** piattaforma.

    ![Compilare Impostazioni finestra, passare dalla piattaforma alla piattaforma UWP.](images/AzureLabs-Lab4-11.png)

5.  Passare a **File > Build Impostazioni** e assicurarsi che:

    1. **Dispositivo di destinazione** impostato su **HoloLens**

        > Per i visori immersivi, impostare **Dispositivo di destinazione** su Qualsiasi *dispositivo.*

    2. **Il tipo di** compilazione è impostato **su D3D**
    3. **L'SDK** è impostato su **Più recente installato**
    4. **Visual Studio Version è** impostato su **Latest installed (Versione più recente installata)**
    5. **Compilazione ed esecuzione** è impostato su **Computer locale**
    6. Salvare la scena e aggiungerla alla compilazione. 

        1. A tale scopo, selezionare **Aggiungi scene aperte**. Verrà visualizzata una finestra di salvataggio.

            ![Fare clic sul pulsante Aggiungi scene aperte](images/AzureLabs-Lab4-12.png)

        2. Selezionare il **pulsante Nuova cartella** per creare una nuova cartella e assegnare alla cartella il nome **Scenes**.

            ![Creare una nuova cartella di script](images/AzureLabs-Lab4-13.png)

        3. Aprire la cartella **Scenes appena** creata e quindi nel campo Di testo **Nome file** digitare **FaceRecScene** e quindi premere **Salva.**

            ![Assegnare un nome alla nuova scena.](images/AzureLabs-Lab4-14.png)

    7. Le impostazioni rimanenti, in *Build Impostazioni*, devono essere lasciato come impostazioni predefinite per il momento.

6. Nella finestra *Build Impostazioni* fare clic sul pulsante **Player Impostazioni** , verrà aperto il pannello correlato nello spazio in cui si trova *Inspector.* 

    ![Aprire le impostazioni del lettore.](images/AzureLabs-Lab4-15.png)

7. In questo pannello è necessario verificare alcune impostazioni:

    1. Nella scheda **Altro Impostazioni:**

        1. **La versione** **del runtime di** scripting deve essere **sperimentale** (equivalente a .NET 4.6). La modifica di questa impostazione determina la necessità di riavviare l'editor.
        2. **Il back-end di** scripting deve **essere .NET**
        3. **Il livello di compatibilità** api deve **essere .NET 4.6**

            ![Aggiornare altre impostazioni.](images/AzureLabs-Lab4-16.png)
      
    2. Nella scheda **Pubblicazione Impostazioni,** in **Funzionalità**, controllare:

        - **InternetClient**
        - **Webcam**

            ![Aggiornamento delle impostazioni di pubblicazione.](images/AzureLabs-Lab4-17.png)

    3. Più in basso nel pannello, in **XR Impostazioni** (disponibile sotto Pubblica **Impostazioni**), selezionare **Virtual Reality Supported**(Realtà virtuale supportata) e assicurarsi che sia stato aggiunto Windows Mixed Reality **SDK.**

        ![Aggiornare la versione X R Impostazioni.](images/AzureLabs-Lab4-18.png)

8.  In *Build Impostazioni*, **Unity C# Projects** non è più in grigio. selezionare la casella di controllo accanto a questo. 
9.  Chiudere la finestra Build Settings (Impostazioni di compilazione).
10. Salvare la scena e Project (**FILE > SAVE SCENE/FILE > SAVE PROJECT**).

## <a name="chapter-4---main-camera-setup"></a>Capitolo 4 - Configurazione della fotocamera principale

> [!IMPORTANT]
> Se si vuole ignorare il componente *Unity Set up* di questo corso e continuare direttamente nel codice, è possibile scaricare questo file [unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20304%20-%20Face%20recognition/Azure-MR-304.unitypackage)e importarlo nel progetto come [pacchetto personalizzato.](https://docs.unity3d.com/Manual/AssetPackages.html) Tenere presente che questo pacchetto include anche l'importazione della *DLL Newtonsoft,* trattata [nel capitolo 5](#chapter-5--import-the-newtonsoftjson-library). Dopo l'importazione, è possibile continuare dal [capitolo 6.](#chapter-6---create-the-faceanalysis-class)

1.  Nel pannello *Hierarchy* (Gerarchia) selezionare **Main Camera (Fotocamera principale).**

2.  Una volta selezionato, sarà possibile visualizzare tutti i componenti della fotocamera **principale** nel pannello *inspector.*

    1. **L'oggetto Camera** deve essere denominato **Main Camera (si** noti l'ortografia).

    2. Il tag della **fotocamera principale** deve essere impostato su **MainCamera** (si noti l'ortografia).

    3. Assicurarsi che **Posizione trasformazione** sia impostato su **0, 0, 0**

    4. Impostare **Cancella flag** su Colore a **tinta unita**

    5. Impostare il **colore** di sfondo del componente fotocamera **su Nero, Alfa 0 (codice esadecimale: #00000000)**

        ![configurare i componenti della fotocamera](images/AzureLabs-Lab4-19.png) 

## <a name="chapter-5--import-the-newtonsoftjson-library"></a>Capitolo 5: Importare il Newtonsoft.Jsnella libreria

> [!IMPORTANT]
> Se è stato importato il file ".unitypackage" [nell'ultimo capitolo,](#chapter-4---main-camera-setup)è possibile ignorare questo capitolo.

Per facilitare la deserializzazione e la serializzazione degli oggetti ricevuti e inviati al servizio Bot, è necessario scaricare ilNewtonsoft.Js *nella* libreria. In questo file di pacchetto Unity è disponibile una versione compatibile già organizzata con la struttura di cartelle [unity corretta.](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20304%20-%20Face%20recognition/newtonsoftDLL.unitypackage) 

Per importare la libreria:

1.  Scaricare il pacchetto Unity.
2.  Fare clic **su Assets (Asset),** **Import Package (Importa pacchetto),** **Custom Package (Pacchetto personalizzato).**

    ![Importare Newtonsoft.Jsin](images/AzureLabs-Lab4-20.png)

3.  Cercare il pacchetto Unity scaricato e fare clic su Apri.
4.  Assicurarsi che tutti i componenti del pacchetto siano selezionati e fare clic su **Importa.**

    ![Importare il Newtonsoft.Jsper gli asset](images/AzureLabs-Lab4-21.png)

## <a name="chapter-6---create-the-faceanalysis-class"></a>Capitolo 6- Creare la classe FaceAnalysis

Lo scopo della classe FaceAnalysis è ospitare i metodi necessari per comunicare con il servizio di riconoscimento volto di Azure. 

- Dopo aver inviato al servizio un'immagine di acquisizione, la analizzierà e identificherà i visi all'interno e determinerà se appartengono a una persona nota. 
- Se viene trovata una persona nota, questa classe ne visualizza il nome come testo dell'interfaccia utente nella scena.

Per creare la *classe FaceAnalysis:*

 1. Fare clic con il pulsante destro del mouse nella cartella *Assets* Project Pannello di controllo, quindi scegliere **Crea**  >  **cartella.** Chiamare la cartella **Scripts**. 

    ![Creare la classe FaceAnalysis.](images/AzureLabs-Lab4-22.png)

2.  Fare doppio clic sulla cartella appena creata per aprirla. 
3.  Fare clic con il pulsante destro del mouse all'interno della cartella , quindi **scegliere Crea**  >  **script C#.** Chiamare lo script *FaceAnalysis*. 
4.  Fare doppio clic sul nuovo script *FaceAnalysis* per aprirlo con Visual Studio 2017.
5.  Immettere gli spazi dei nomi seguenti sopra la *classe FaceAnalysis:*

    ```csharp
        using Newtonsoft.Json;
        using System.Collections;
        using System.Collections.Generic;
        using System.IO;
        using System.Text;
        using UnityEngine;
        using UnityEngine.Networking;
    ```

6.  È ora necessario aggiungere tutti gli oggetti usati per la deserializzazione. Questi oggetti devono essere aggiunti **all'esterno** dello script *FaceAnalysis* (sotto la parentesi graffa inferiore). 

    ```csharp
        /// <summary>
        /// The Person Group object
        /// </summary>
        public class Group_RootObject
        {
            public string personGroupId { get; set; }
            public string name { get; set; }
            public object userData { get; set; }
        }

        /// <summary>
        /// The Person Face object
        /// </summary>
        public class Face_RootObject
        {
            public string faceId { get; set; }
        }

        /// <summary>
        /// Collection of faces that needs to be identified
        /// </summary>
        public class FacesToIdentify_RootObject
        {
            public string personGroupId { get; set; }
            public List<string> faceIds { get; set; }
            public int maxNumOfCandidatesReturned { get; set; }
            public double confidenceThreshold { get; set; }
        }

        /// <summary>
        /// Collection of Candidates for the face
        /// </summary>
        public class Candidate_RootObject
        {
            public string faceId { get; set; }
            public List<Candidate> candidates { get; set; }
        }

        public class Candidate
        {
            public string personId { get; set; }
            public double confidence { get; set; }
        }

        /// <summary>
        /// Name and Id of the identified Person
        /// </summary>
        public class IdentifiedPerson_RootObject
        {
            public string personId { get; set; }
            public string name { get; set; }
        }
    ```
7. I *metodi Start()* *e Update()* non verranno usati, quindi eliminarli ora. 

8.  *All'interno della classe FaceAnalysis* aggiungere le variabili seguenti:

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static FaceAnalysis Instance;

        /// <summary>
        /// The analysis result text
        /// </summary>
        private TextMesh labelText;

        /// <summary>
        /// Bytes of the image captured with camera
        /// </summary>
        internal byte[] imageBytes;

        /// <summary>
        /// Path of the image captured with camera
        /// </summary>
        internal string imagePath;

        /// <summary>
        /// Base endpoint of Face Recognition Service
        /// </summary>
        const string baseEndpoint = "https://westus.api.cognitive.microsoft.com/face/v1.0/";

        /// <summary>
        /// Auth key of Face Recognition Service
        /// </summary>
        private const string key = "- Insert your key here -";

        /// <summary>
        /// Id (name) of the created person group 
        /// </summary>
        private const string personGroupId = "- Insert your group Id here -";
    ```

    > [!NOTE]
    > Sostituire la **chiave** e **personGroupId con** la chiave del servizio e l'ID del gruppo creato in precedenza.

9.  Aggiungere il *metodo Awake(),* che inizializza la classe , aggiungendo la classe *ImageCapture* alla fotocamera principale e chiama il metodo di creazione dell'etichetta:

    ```csharp
        /// <summary>
        /// Initialises this class
        /// </summary>
        private void Awake()
        {
            // Allows this instance to behave like a singleton
            Instance = this;

            // Add the ImageCapture Class to this Game Object
            gameObject.AddComponent<ImageCapture>();

            // Create the text label in the scene
            CreateLabel();
        }
    ```

10. Aggiungere il *metodo CreateLabel(),* che crea l'oggetto *Label* per visualizzare il risultato dell'analisi:

    ```csharp
        /// <summary>
        /// Spawns cursor for the Main Camera
        /// </summary>
        private void CreateLabel()
        {
            // Create a sphere as new cursor
            GameObject newLabel = new GameObject();

            // Attach the label to the Main Camera
            newLabel.transform.parent = gameObject.transform;
            
            // Resize and position the new cursor
            newLabel.transform.localScale = new Vector3(0.4f, 0.4f, 0.4f);
            newLabel.transform.position = new Vector3(0f, 3f, 60f);

            // Creating the text of the Label
            labelText = newLabel.AddComponent<TextMesh>();
            labelText.anchor = TextAnchor.MiddleCenter;
            labelText.alignment = TextAlignment.Center;
            labelText.tabSize = 4;
            labelText.fontSize = 50;
            labelText.text = ".";       
        }
    ```

11. Aggiungere i *metodi DetectFacesFromImage()* *e GetImageAsByteArray().* Il primo richiederà al servizio di riconoscimento del viso di rilevare qualsiasi possibile viso nell'immagine inviata, mentre il secondo è necessario per convertire l'immagine acquisita in una matrice di byte:

    ```csharp
        /// <summary>
        /// Detect faces from a submitted image
        /// </summary>
        internal IEnumerator DetectFacesFromImage()
        {
            WWWForm webForm = new WWWForm();
            string detectFacesEndpoint = $"{baseEndpoint}detect";

            // Change the image into a bytes array
            imageBytes = GetImageAsByteArray(imagePath);

            using (UnityWebRequest www = 
                UnityWebRequest.Post(detectFacesEndpoint, webForm))
            {
                www.SetRequestHeader("Ocp-Apim-Subscription-Key", key);
                www.SetRequestHeader("Content-Type", "application/octet-stream");
                www.uploadHandler.contentType = "application/octet-stream";
                www.uploadHandler = new UploadHandlerRaw(imageBytes);
                www.downloadHandler = new DownloadHandlerBuffer();

                yield return www.SendWebRequest();
                string jsonResponse = www.downloadHandler.text;
                Face_RootObject[] face_RootObject = 
                    JsonConvert.DeserializeObject<Face_RootObject[]>(jsonResponse);

                List<string> facesIdList = new List<string>();
                // Create a list with the face Ids of faces detected in image
                foreach (Face_RootObject faceRO in face_RootObject)
                {
                    facesIdList.Add(faceRO.faceId);
                    Debug.Log($"Detected face - Id: {faceRO.faceId}");
                }
                
                StartCoroutine(IdentifyFaces(facesIdList));
            }
        }

        /// <summary>
        /// Returns the contents of the specified file as a byte array.
        /// </summary>
        static byte[] GetImageAsByteArray(string imageFilePath)
        {
            FileStream fileStream = new FileStream(imageFilePath, FileMode.Open, FileAccess.Read);
            BinaryReader binaryReader = new BinaryReader(fileStream);
            return binaryReader.ReadBytes((int)fileStream.Length);
        }
    ```

12. Aggiungere il *metodo IdentifyFaces(),* che richiede al servizio di riconoscimento *volto* di identificare qualsiasi viso noto rilevato in precedenza nell'immagine inviata. La richiesta restituirà un ID della persona identificata, ma non il nome:

    ```csharp
        /// <summary>
        /// Identify the faces found in the image within the person group
        /// </summary>
        internal IEnumerator IdentifyFaces(List<string> listOfFacesIdToIdentify)
        {
            // Create the object hosting the faces to identify
            FacesToIdentify_RootObject facesToIdentify = new FacesToIdentify_RootObject();
            facesToIdentify.faceIds = new List<string>();
            facesToIdentify.personGroupId = personGroupId;
            foreach (string facesId in listOfFacesIdToIdentify)
            {
                facesToIdentify.faceIds.Add(facesId);
            }
            facesToIdentify.maxNumOfCandidatesReturned = 1;
            facesToIdentify.confidenceThreshold = 0.5;

            // Serialize to Json format
            string facesToIdentifyJson = JsonConvert.SerializeObject(facesToIdentify);
            // Change the object into a bytes array
            byte[] facesData = Encoding.UTF8.GetBytes(facesToIdentifyJson);

            WWWForm webForm = new WWWForm();
            string detectFacesEndpoint = $"{baseEndpoint}identify";

            using (UnityWebRequest www = UnityWebRequest.Post(detectFacesEndpoint, webForm))
            {
                www.SetRequestHeader("Ocp-Apim-Subscription-Key", key);
                www.SetRequestHeader("Content-Type", "application/json");
                www.uploadHandler.contentType = "application/json";
                www.uploadHandler = new UploadHandlerRaw(facesData);
                www.downloadHandler = new DownloadHandlerBuffer();

                yield return www.SendWebRequest();
                string jsonResponse = www.downloadHandler.text;
                Debug.Log($"Get Person - jsonResponse: {jsonResponse}");
                Candidate_RootObject [] candidate_RootObject = JsonConvert.DeserializeObject<Candidate_RootObject[]>(jsonResponse);

                // For each face to identify that ahs been submitted, display its candidate
                foreach (Candidate_RootObject candidateRO in candidate_RootObject)
                {
                    StartCoroutine(GetPerson(candidateRO.candidates[0].personId));
                    
                    // Delay the next "GetPerson" call, so all faces candidate are displayed properly
                    yield return new WaitForSeconds(3);
                }           
            }
        }
    ```

13. Aggiungere il *metodo GetPerson().* Fornendo l'ID persona, questo metodo richiede quindi al servizio di riconoscimento *volto* di restituire il nome della persona identificata:

    ```csharp
        /// <summary>
        /// Provided a personId, retrieve the person name associated with it
        /// </summary>
        internal IEnumerator GetPerson(string personId)
        {
            string getGroupEndpoint = $"{baseEndpoint}persongroups/{personGroupId}/persons/{personId}?";
            WWWForm webForm = new WWWForm();

            using (UnityWebRequest www = UnityWebRequest.Get(getGroupEndpoint))
            {
                www.SetRequestHeader("Ocp-Apim-Subscription-Key", key);
                www.downloadHandler = new DownloadHandlerBuffer();
                yield return www.SendWebRequest();
                string jsonResponse = www.downloadHandler.text;

                Debug.Log($"Get Person - jsonResponse: {jsonResponse}");
                IdentifiedPerson_RootObject identifiedPerson_RootObject = JsonConvert.DeserializeObject<IdentifiedPerson_RootObject>(jsonResponse);

                // Display the name of the person in the UI
                labelText.text = identifiedPerson_RootObject.name;
            }
        }
    ```

14.  Ricordarsi **di salvare** le modifiche prima di tornare all'editor di Unity.
15.  Nell'editor di Unity trascinare lo script FaceAnalysis dalla cartella Scripts (Script) del pannello Project all'oggetto Main Camera (Fotocamera principale) nel *pannello Hierarchy (Gerarchia).* Il nuovo componente script verrà aggiunto alla fotocamera principale. 

![Posizionare FaceAnalysis nella fotocamera principale](images/AzureLabs-Lab4-23.png)


## <a name="chapter-7---create-the-imagecapture-class"></a>Capitolo 7 - Creare la classe ImageCapture

Lo scopo della classe *ImageCapture* è quello di ospitare i metodi necessari per comunicare con il servizio di riconoscimento volto di *Azure* per analizzare l'immagine che verrà acquisite, identificando i visi in essa presenti e determinando se appartiene a una persona nota. Se viene trovata una persona nota, questa classe ne visualizza il nome come testo dell'interfaccia utente nella scena.

Per creare la *classe ImageCapture:*
 
1.  Fare clic con il pulsante destro **del mouse all'interno** della cartella Script creata in precedenza, quindi scegliere **Crea**, **Script C#.** Chiamare lo script *ImageCapture.* 
2.  Fare doppio clic sul nuovo script *ImageCapture* per aprirlo con Visual Studio 2017.
3.  Immettere gli spazi dei nomi seguenti sopra la classe ImageCapture:

    ```csharp
        using System.IO;
        using System.Linq;
        using UnityEngine;
        using UnityEngine.XR.WSA.Input;
        using UnityEngine.XR.WSA.WebCam;
    ```

4.  *All'interno della classe ImageCapture* aggiungere le variabili seguenti:

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static ImageCapture instance;

        /// <summary>
        /// Keeps track of tapCounts to name the captured images 
        /// </summary>
        private int tapsCount;

        /// <summary>
        /// PhotoCapture object used to capture images on HoloLens 
        /// </summary>
        private PhotoCapture photoCaptureObject = null;

        /// <summary>
        /// HoloLens class to capture user gestures
        /// </summary>
        private GestureRecognizer recognizer;
    ```

5.  Aggiungere i *metodi Awake()* e *Start()* necessari per inizializzare la classe e consentire all'HoloLens di acquisire i movimenti dell'utente:

    ```csharp
        /// <summary>
        /// Initialises this class
        /// </summary>
        private void Awake()
        {
            instance = this;
        }

        /// <summary>
        /// Called right after Awake
        /// </summary>
        void Start()
        {
            // Initialises user gestures capture 
            recognizer = new GestureRecognizer();
            recognizer.SetRecognizableGestures(GestureSettings.Tap);
            recognizer.Tapped += TapHandler;
            recognizer.StartCapturingGestures();
        }
    ```

6.  Aggiungere *tapHandler() che* viene chiamato quando l'utente esegue un *movimento Tap:*

    ```csharp
        /// <summary>
        /// Respond to Tap Input.
        /// </summary>
        private void TapHandler(TappedEventArgs obj)
        {
            tapsCount++;
            ExecuteImageCaptureAndAnalysis();
        }
    ```

7.  Aggiungere il *metodo ExecuteImageCaptureAndAnalysis()* che inizierà il processo di acquisizione dell'immagine:

    ```csharp
        /// <summary>
        /// Begin process of Image Capturing and send To Azure Computer Vision service.
        /// </summary>
        private void ExecuteImageCaptureAndAnalysis()
        {
            Resolution cameraResolution = PhotoCapture.SupportedResolutions.OrderByDescending
                ((res) => res.width * res.height).First();
            Texture2D targetTexture = new Texture2D(cameraResolution.width, cameraResolution.height);

            PhotoCapture.CreateAsync(false, delegate (PhotoCapture captureObject)
            {
                photoCaptureObject = captureObject;

                CameraParameters c = new CameraParameters();
                c.hologramOpacity = 0.0f;
                c.cameraResolutionWidth = targetTexture.width;
                c.cameraResolutionHeight = targetTexture.height;
                c.pixelFormat = CapturePixelFormat.BGRA32;

                captureObject.StartPhotoModeAsync(c, delegate (PhotoCapture.PhotoCaptureResult result)
                {
                    string filename = string.Format(@"CapturedImage{0}.jpg", tapsCount);
                    string filePath = Path.Combine(Application.persistentDataPath, filename);

                    // Set the image path on the FaceAnalysis class
                    FaceAnalysis.Instance.imagePath = filePath;

                    photoCaptureObject.TakePhotoAsync
                    (filePath, PhotoCaptureFileOutputFormat.JPG, OnCapturedPhotoToDisk);
                });
            });
        }
    ```

8.  Aggiungere i gestori che vengono chiamati quando il processo di acquisizione foto è stato completato:

    ```csharp
        /// <summary>
        /// Called right after the photo capture process has concluded
        /// </summary>
        void OnCapturedPhotoToDisk(PhotoCapture.PhotoCaptureResult result)
        {
            photoCaptureObject.StopPhotoModeAsync(OnStoppedPhotoMode);
        }

        /// <summary>
        /// Register the full execution of the Photo Capture. If successful, it will begin the Image Analysis process.
        /// </summary>
        void OnStoppedPhotoMode(PhotoCapture.PhotoCaptureResult result)
        {
            photoCaptureObject.Dispose();
            photoCaptureObject = null;

            // Request image caputer analysis
            StartCoroutine(FaceAnalysis.Instance.DetectFacesFromImage());
        }
    ```

9. Ricordarsi **di salvare** le modifiche prima di tornare all'editor di Unity.

## <a name="chapter-8---building-the-solution"></a>Capitolo 8 - Compilazione della soluzione

Per eseguire un test completo dell'applicazione, è necessario eseguire il sideload nell'HoloLens.

Prima di procedere, verificare che:

-   Tutte le impostazioni indicate nel capitolo 3 sono impostate correttamente. 
-   Lo script *FaceAnalysis* è collegato all'oggetto Main Camera. 
-   Sia la **chiave di autenticazione che** **l'ID gruppo** sono stati impostati all'interno dello script *FaceAnalysis.*

A questo punto si è pronti per compilare la soluzione. Dopo aver compilato la soluzione, si sarà pronti per distribuire l'applicazione.

Per iniziare il processo di compilazione:

1.  Salvare la scena corrente facendo clic su File, Salva.
2.  Passare a File, Compila Impostazioni e fare clic su Aggiungi scene aperte.
3.  Assicurarsi di selezionare Progetti C# unity.

    ![Distribuire la Visual Studio distribuzione](images/AzureLabs-Lab4-24.png)

4.  Fare clic su Compila. In questo caso, Unity avvierà una finestra Esplora file, in cui è necessario creare e quindi selezionare una cartella in cui compilare l'app. Creare la cartella ora, all'interno del progetto Unity, e chiamarla App. Quindi, con la cartella App selezionata, premere Seleziona cartella. 
5.  Unity inizierà a compilare il progetto, nella cartella App. 
6.  Al termine della compilazione di Unity (potrebbe essere necessario del tempo), verrà aperta una Esplora file nella posizione della compilazione.

    ![Distribuire la soluzione da Visual Studio](images/AzureLabs-Lab4-25.png)

7.  Aprire la cartella App e quindi aprire la nuova soluzione Project (come illustrato in precedenza, MR_FaceRecognition.sln).


## <a name="chapter-9---deploying-your-application"></a>Capitolo 9: Distribuzione dell'applicazione

Per eseguire la distribuzione HoloLens:

1.  Sarà necessario l'indirizzo IP del HoloLens (per la distribuzione remota) e per assicurarsi che l'HoloLens sia in **modalità sviluppatore.** Per eseguire questa operazione:

    1. Mentre si è HoloLens, aprire il **Impostazioni**.
    2. Passare a **Rete & Internet > Wi-Fi > Opzioni avanzate**
    3. Prendere nota **dell'indirizzo IPv4.**
    4. Tornare quindi a Impostazioni **e** quindi a Update & Security > for Developers (Aggiorna & security > **for Developers)** 
    5. Impostare modalità sviluppatore attivata.

2.  Passare alla nuova build di Unity (la *cartella App)* e aprire il file della soluzione *con Visual Studio*.
3.  In Configurazione soluzione selezionare **Debug.**
4.  In Piattaforma soluzione selezionare **x86**, **Computer remoto**. 

    ![Modificare la configurazione della soluzione](images/AzureLabs-Lab4-26.png)
 
5.  Passare al **menu Compila e fare** clic su **Distribuisci soluzione** per eseguire il sideload dell'applicazione nel HoloLens.
6.  L'app dovrebbe ora essere visualizzata nell'elenco delle app installate nel HoloLens, pronto per l'avvio.

> [!NOTE]
> Per eseguire la distribuzione in visore vr immersivo, impostare Piattaforma **soluzione** su *Computer* locale e impostare Configurazione su *Debug*, con *x86* come **Piattaforma**.  Quindi eseguire la distribuzione nel computer locale, usando il **menu Compila**, selezionando *Distribuisci soluzione*. 


## <a name="chapter-10---using-the-application"></a>Capitolo 10 - Uso dell'applicazione

1.  Quando si indossa HoloLens, avviare l'app.
2.  Esaminare la persona registrata con *l'API Viso*. Assicurarsi che:

    -  Il viso della persona non è troppo distante e chiaramente visibile
    -  L'illuminazione dell'ambiente non è troppo scura

3.  Usare il movimento tocco per acquisire l'immagine della persona.
4.  Attendere che l'app invii la richiesta di analisi e riceva una risposta.
5.  Se la persona è stata riconosciuta correttamente, il nome della persona verrà visualizzato come testo dell'interfaccia utente.
6.  È possibile ripetere il processo di acquisizione usando il movimento di tocco ogni pochi secondi.

## <a name="your-finished-azure-face-api-application"></a>Applicazione API Viso di Azure completata

È stata creata un'app di realtà mista che sfrutta il servizio Riconoscimento volto di Azure per rilevare i visi all'interno di un'immagine e identificare i visi noti.

![risultato del completamento del corso](images/AzureLabs-Lab4-00.png)

## <a name="bonus-exercises"></a>Esercizi aggiuntivi

### <a name="exercise-1"></a>Esercizio 1

**L'API Viso di Azure** è sufficientemente potente da rilevare fino a 64 visi in una singola immagine. Estendere l'applicazione, in modo che possa riconoscere due o tre visi, tra molte altre persone.

### <a name="exercise-2"></a>Esercizio 2

**L'API Viso di Azure** è anche in grado di fornire tutti i tipi di informazioni sugli attributi. Integrarlo nell'applicazione. Questo potrebbe essere ancora più interessante, se combinato con [l'API Emozioni](https://azure.microsoft.com/services/cognitive-services/emotion/).
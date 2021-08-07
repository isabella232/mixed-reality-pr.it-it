---
title: HoloLens (prima generazione) e Azure 311 - Microsoft Graph
description: Completa questo corso per imparare a sfruttare Microsoft Graph e connetterti ai dati che determinano la produttività, all'interno di un'applicazione di realtà mista.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure, realtà mista, academy, unity, esercitazione, api, microsoft graph, hololens, immersive, vr, Windows 10, Visual Studio
ms.openlocfilehash: 16fb7853d202c39399b48595a17e7e9b2edf224f18d5e315c5ddcf4a0054d8f7
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115215263"
---
# <a name="hololens-1st-gen-and-azure-311---microsoft-graph"></a>HoloLens (prima generazione) e Azure 311 - Microsoft Graph

>[!NOTE]
>Le esercitazioni di Mixed Reality Academy sono state progettate in base a HoloLens (prima generazione) e ai visori VR immersive di realtà mista.  Pertanto, riteniamo importante lasciarle a disposizione degli sviluppatori a cui serve ancora materiale sussidiario per lo sviluppo di questi dispositivi.  Queste esercitazioni **_non_** verranno aggiornate con i set di strumenti o le interazioni più recenti usati per HoloLens 2.  Rimarranno invariate per consentire di continuare a lavorare sui dispositivi supportati. In futuro verrà pubblicata una nuova serie di esercitazioni che illustrano come sviluppare per HoloLens 2.  Questa comunicazione verrà aggiornata con un collegamento a tali esercitazioni al momento della pubblicazione.

In questo corso si apprenderà come usare *Microsoft Graph* per accedere al proprio account Microsoft usando l'autenticazione sicura all'interno di un'applicazione di realtà mista. Sarà quindi possibile recuperare e visualizzare le riunioni pianificate nell'interfaccia dell'applicazione.

![](images/AzureLabs-Lab311-00.png)

*Microsoft Graph* è un set di API progettate per consentire l'accesso a molti dei servizi Microsoft. Microsoft descrive Microsoft Graph come una matrice di risorse connesse tramite relazioni, ovvero consente a un'applicazione di accedere a tutti i tipi di dati utente connessi. Per altre informazioni, visitare la [pagina Graph Microsoft](https://developer.microsoft.com/graph).

Lo sviluppo includerà la creazione di un'app in cui all'utente verrà richiesto di guardare e quindi toccare una sfera, che richiederà all'utente di accedere in modo sicuro a un account Microsoft. Dopo aver eseguito l'accesso al proprio account, l'utente potrà visualizzare un elenco di riunioni pianificate per il giorno.

Dopo aver completato questo corso, si avrà un'applicazione HoloLens realtà mista, che sarà in grado di eseguire le operazioni seguenti:

1.  Usando il movimento Tocco, toccare un oggetto, che richiederà all'utente di accedere a un account Microsoft (uscire dall'app per accedere e quindi accedere nuovamente all'app).
2.  Visualizzare un elenco di riunioni pianificate per il giorno. 

Nell'applicazione è necessario sapere come integrare i risultati con la progettazione. Questo corso è stato progettato per illustrare come integrare un servizio di Azure con il progetto Unity. È compito dell'utente usare le conoscenze acquisite in questo corso per migliorare l'applicazione di realtà mista.

## <a name="device-support"></a>Supporto di dispositivi

<table>
<tr>
<th>Corso</th><th style="width:150px"> <a href="/hololens/hololens1-hardware">HoloLens</a></th><th style="width:150px"> <a href="../../../discover/immersive-headset-hardware-details.md">Visori VR immersive</a></th>
</tr><tr>
<td> MR e Azure 311: Microsoft Graph</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="prerequisites"></a>Prerequisiti

> [!NOTE]
> Questa esercitazione è destinata agli sviluppatori che hanno esperienza di base con Unity e C#. Tenere presente anche che i prerequisiti e le istruzioni scritte all'interno di questo documento rappresentano ciò che è stato testato e verificato al momento della stesura di questo documento (luglio 2018). È possibile usare il software più recente, come indicato nell'articolo Installare gli strumenti, anche se non si presuppone che le informazioni contenute in questo corso corrispondano perfettamente a quelle disponibili nel software più recente rispetto a quelle elencate di seguito. [](../../install-the-tools.md)

Per questo corso è consigliabile usare l'hardware e il software seguenti:

- Un PC di sviluppo
- [Windows 10 Fall Creators Update (o versione successiva) con la modalità sviluppatore abilitata](../../install-the-tools.md#installation-checklist)
- [L'SDK Windows 10 più recente](../../install-the-tools.md#installation-checklist)
- [Unity 2017.4](../../install-the-tools.md#installation-checklist)
- [Visual Studio 2017](../../install-the-tools.md#installation-checklist)
- Un [Microsoft HoloLens](/hololens/hololens1-hardware) con la modalità sviluppatore abilitata
- Accesso a Internet per l'installazione di Azure e il recupero Graph microsoft
- Un account **Microsoft valido** (personale o aziendale o dell'istituto di istruzione)
- Alcune riunioni pianificate per il giorno corrente, usando lo stesso account Microsoft

### <a name="before-you-start"></a>Prima di iniziare

1.  Per evitare di riscontrare problemi durante la compilazione di questo progetto, è consigliabile creare il progetto indicato in questa esercitazione in una cartella radice o quasi (i percorsi di cartelle lunghi possono causare problemi in fase di compilazione).
2.  Configurare e testare l'HoloLens. Se è necessario supporto per la configurazione del HoloLens, vedere [l'articolo HoloLens configurazione.](/hololens/hololens-setup) 
3.  È buona idea eseguire la calibrazione e l'ottimizzazione dei sensori quando si inizia a sviluppare una nuova app HoloLens (a volte può essere utile eseguire tali attività per ogni utente). 

Per informazioni sulla calibrazione, fare clic su questo [collegamento all'HoloLens calibrazione.](/hololens/hololens-calibration#hololens-2)

Per informazioni sull'ottimizzazione dei sensori, fare clic su questo collegamento [all'HoloLens sull'ottimizzazione dei sensori.](/hololens/hololens-updates)

## <a name="chapter-1---create-your-app-in-the-application-registration-portal"></a>Capitolo 1: Creare l'app nel portale di registrazione delle applicazioni

Per iniziare, è necessario creare e registrare l'applicazione nel portale **di registrazione delle applicazioni.**

In questo capitolo è disponibile anche la chiave del servizio che consentirà di effettuare chiamate a *Microsoft Graph* accedere al contenuto dell'account.

1.  Passare al portale [di registrazione delle applicazioni Microsoft ed](https://apps.dev.microsoft.com) eseguire l'accesso con il proprio account Microsoft. Dopo aver eseguito l'accesso, si verrà reindirizzati al portale **di registrazione delle applicazioni.**

2.  Nella sezione **My applications (Applicazioni)** fare clic sul pulsante **Add an app (Aggiungi un'app).**

    ![](images/AzureLabs-Lab311-01.png)![](images/AzureLabs-Lab311-02.png)

    > [!IMPORTANT]
    > Il **portale di registrazione delle** applicazioni può avere un aspetto diverso, a seconda che si sia già lavorato con Microsoft *Graph*. Gli screenshot seguenti visualizzano queste diverse versioni.

3.  Aggiungere un nome per l'applicazione e fare clic su **Crea.**

    ![](images/AzureLabs-Lab311-03.png)

4.  Dopo aver creato l'applicazione, si verrà reindirizzati alla pagina principale dell'applicazione. Copiare **l'ID** applicazione e assicurarsi di prendere nota di questo valore in una posizione sicura, che verrà presto utilizzata nel codice.

    ![](images/AzureLabs-Lab311-04.png)

5.  Nella sezione **Piattaforme** verificare che sia **visualizzato Applicazione** nativa. In *caso non* fare clic su Add Platform **(Aggiungi** piattaforma) **e selezionare Native Application (Applicazione nativa).**

    ![](images/AzureLabs-Lab311-05.png)

6.  Scorrere verso il basso nella stessa pagina e nella sezione denominata **Microsoft Graph Autorizzazioni** è necessario aggiungere altre autorizzazioni per l'applicazione. Fare clic **su Aggiungi** accanto a **Autorizzazioni delegate.**

    ![](images/AzureLabs-Lab311-06.png)

7.  Poiché si vuole che l'applicazione accedono al calendario dell'utente, selezionare la casella **denominata Calendars.Read** e fare clic su **OK.**

    ![](images/AzureLabs-Lab311-07.png)

8.  Scorrere fino alla fine e fare clic sul **pulsante** Salva.

    ![](images/AzureLabs-Lab311-08.png)

9.  Il salvataggio verrà confermato ed è possibile disconnettersi dal portale **di registrazione delle applicazioni.**

## <a name="chapter-2---set-up-the-unity-project"></a>Capitolo 2: Configurare il progetto Unity

Di seguito è riportata una configurazione tipica per lo sviluppo con la realtà mista e, di conseguenza, è un buon modello per altri progetti.

1.  Aprire *Unity e* fare clic su New **(Nuovo).**

    ![](images/AzureLabs-Lab311-09.png)

2.  È necessario specificare un nome di progetto Unity. Inserire **MSGraphMR.** Assicurarsi che il modello di progetto sia impostato su **3D.** Impostare Il **percorso su** un percorso appropriato per l'utente(tenere presente che più vicino alle directory radice è meglio). Fare quindi clic **su Crea progetto**.

    ![](images/AzureLabs-Lab311-10.png)

3.  Con Unity aperto, è opportuno controllare che l'editor di **script predefinito** sia impostato **su Visual Studio**. Passare a **Modifica**  >  **preferenze** e quindi dalla nuova finestra passare a **Strumenti esterni.** Modificare **External Script Editor in** Visual Studio **2017**. Chiudere la **finestra** Preferenze.

    ![](images/AzureLabs-Lab311-11.png)

4.  Passare a **File** Build Impostazioni (Compilazione file) e selezionare  >   Universal Windows **Platform (Piattaforma Universal Windows),** quindi fare clic sul **pulsante Switch Platform** (Cambia piattaforma) per applicare la selezione.

    ![](images/AzureLabs-Lab311-12.png)

5.  Sempre in **Compilazione file**  >  **Impostazioni**, assicurarsi che:

    1. **Il dispositivo di** destinazione è impostato **su HoloLens**
    2. **Il tipo di** compilazione è impostato **su D3D**
    3. **L'SDK** è impostato su **Più recente installato**
    4. **Visual Studio versione è** impostata su **Versione più recente installata**
    5. **Build and Run (Compilazione** ed esecuzione) è impostato **su Local Machine (Computer locale)**
    6. Salvare la scena e aggiungerla alla compilazione.

        1. A tale scopo, selezionare **Add Open Scenes (Aggiungi scene aperte).** Verrà visualizzata una finestra di salvataggio.

            ![](images/AzureLabs-Lab311-13.png)

        2. Creare una nuova cartella per questa ed eventuali scene future. Selezionare il **pulsante Nuova** cartella. Per creare una nuova cartella, assegnare alla cartella il nome **Scenes**.

            ![](images/AzureLabs-Lab311-14.png)

        3. Aprire la cartella **Scenes appena** creata e quindi nel campo di testo *Nome file*: digitare **MR_ComputerVisionScene** e quindi fare clic su **Salva.**

            ![](images/AzureLabs-Lab311-15.png)

            > [!IMPORTANT] 
            > Tenere presente che è necessario salvare le scene di Unity all'interno *della cartella Assets,* perché devono essere associate al progetto Unity. La creazione della cartella scenes (e di altre cartelle simili) è un modo tipico per strutturare un progetto Unity.

    7.  Le impostazioni rimanenti, in *Build Impostazioni*, per il momento devono essere lasciato come predefinite.

6.  Nella finestra *build Impostazioni* fare clic sul pulsante **Player Impostazioni** (Impostazioni lettore). Verrà aperto il pannello correlato nello spazio in cui si trova *il* controllo. 

    ![](images/AzureLabs-Lab311-16.png)

7. In questo pannello è necessario verificare alcune impostazioni:

    1. Nella scheda **Altro Impostazioni:**

        1.  **La** **versione del runtime di** scripting deve essere **sperimentale** (equivalente a .NET 4.6), che attiverà la necessità di riavviare l'editor.

        2. **Il back-end di** scripting deve **essere .NET**

        3. **Il livello di compatibilità dell'API** **deve essere .NET 4.6**

            ![](images/AzureLabs-Lab311-17.png)

    2.  **All'interno della Impostazioni** pubblicazione, in **Funzionalità,** controllare:

        - **InternetClient**

            ![](images/AzureLabs-Lab311-18.png)

    3.  Più in basso nel pannello, in **XR Impostazioni** (disponibile sotto **Pubblica Impostazioni),** selezionare **Virtual Reality Supported**(Realtà virtuale supportata) e assicurarsi che sia stato aggiunto **Windows Mixed Reality SDK.**

        ![](images/AzureLabs-Lab311-19.png)

8.  Tornando alla *compilazione Impostazioni*, i *progetti C# Unity* non sono più disattivati; Selezionare la casella di controllo accanto a questo.

9.  Chiudere la finestra *Build Settings* (Impostazioni compilazione).

10.  Salvare la scena e il progetto **(FILE**  >  **SAVE SCENES/FILE**  >  **SAVE PROJECT**).

## <a name="chapter-3---import-libraries-in-unity"></a>Capitolo 3- Importare librerie in Unity

> [!IMPORTANT]
> Se si vuole ignorare il componente Di configurazione di *Unity* di questo corso e continuare direttamente con il codice, scaricare il file [](https://docs.unity3d.com/Manual/AssetPackages.html) [Azure-MR-311.unitypackage,](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20311%20-%20Microsoft%20Graph/Azure-MR-311.unitypackage)importarlo nel progetto come pacchetto personalizzato e quindi continuare dal capitolo [5.](#chapter-5---create-meetingsui-class)

Per usare *Microsoft Graph* all'interno di Unity, è necessario usare la DLL **Microsoft.Identity.Client.** È possibile usare Microsoft Graph SDK, tuttavia, richiederà l'aggiunta di un pacchetto NuGet dopo la compilazione del progetto Unity, ovvero la modifica del progetto dopo la compilazione. È considerato più semplice importare le DLL necessarie direttamente in Unity.

> [!NOTE]
> Esiste attualmente un problema noto in Unity che richiede la riconfigurazione dei plug-in dopo l'importazione. Questi passaggi (da 4 a 7 in questa sezione) non saranno più necessari dopo la risoluzione del bug.

Per *importare microsoft Graph* nel proprio progetto, [scaricare il file MSGraph_LabPlugins.zip .](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20311%20-%20Microsoft%20Graph/MSGraph_LabPlugins.unitypackage) Questo pacchetto è stato creato con versioni delle librerie che sono state testate.

Per altre informazioni su come aggiungere DLL personalizzate al progetto Unity, [fare clic su questo collegamento.](https://docs.unity3d.com/Manual/UsingDLL.html)

Per importare il pacchetto:

1.  Aggiungere il pacchetto Unity a Unity usando l'opzione di menu **Assets**  >  **Import Package** Custom  >  **Package (Importa** pacchetto personalizzato di asset). Selezionare il pacchetto appena scaricato.

2.  Nella casella **Import Unity Package (Importa** pacchetto Unity) visualizzata verificare che sia selezionato tutto il contenuto di Plugins (e including) Plugins (Plug-in inclusi). 

    ![](images/AzureLabs-Lab311-20.png)

3.  Fare clic **sul** pulsante Importa per aggiungere gli elementi al progetto.

4.  Passare alla cartella **MSGraph** in **Plugins (Plug-in)** nel *pannello Project e* selezionare il **plug-in denominato Microsoft.Identity.Client.**

    ![](images/AzureLabs-Lab311-21.png)

5.  Con il *plug-in* selezionato, assicurarsi che l'opzione **Any Platform** (Qualsiasi piattaforma) sia deselezionata, quindi assicurarsi che **anche WSAPlayer** sia deselezionato, quindi fare clic **su Apply (Applica).** Questa operazione viene eseguita solo per verificare che i file siano configurati correttamente.

    ![](images/AzureLabs-Lab311-22.png)

    > [!NOTE] 
    > Contrassegnare questi plug-in per configurarli in modo che siano usati solo nell'editor di Unity. Nella cartella WSA è presente un set diverso di DLL che verrà usato dopo l'esportazione del progetto da Unity come applicazione Windows universale.

6.  Successivamente, è necessario aprire la **cartella WSA** all'interno della **cartella MSGraph.** Verrà visualizzata una copia dello stesso file appena configurato. Selezionare il file e quindi nel controllo:

    -   Assicurarsi che **l'opzione Any Platform** **(Qualsiasi piattaforma)** sia deselezionata e che **sia selezionato** **solo** **WSAPlayer.**

    -   Assicurarsi **che l'SDK** sia impostato **su UWP** e **che il back-end di scripting** sia impostato su Dot **Net**

    -   Assicurarsi che **l'opzione Non elaborare** sia **selezionata.**

        ![](images/AzureLabs-Lab311-23.png)

7.  Fare clic su **Applica**.

## <a name="chapter-4---camera-setup"></a>Capitolo 4 - Configurazione della fotocamera

Durante questo capitolo verrà impostata la fotocamera principale della scena:

1.  Nel pannello *Hierarchy (Gerarchia)* selezionare **Main Camera (Fotocamera principale).**

2.  Una volta selezionato, sarà possibile visualizzare tutti i componenti della **fotocamera principale** nel pannello *Inspector (Controllo).*

    1.  **L'oggetto Camera** deve essere denominato **Main Camera (si** noti l'ortografia).

    2.  Il tag della **fotocamera principale** deve essere impostato su **MainCamera** (si noti l'ortografia).

    3.  Assicurarsi che **Posizione trasformazione** sia impostato su **0, 0, 0**

    4.  Impostare **Cancella flag** su Colore a **tinta unita**

    5.  Impostare il **colore di** sfondo del componente fotocamera **su Nero, Alfa 0** **(codice esadecimale: #00000000)**

        ![](images/AzureLabs-Lab311-24.png)

3.  La struttura dell'oggetto finale nel *pannello gerarchia* dovrebbe essere simile a quella illustrata nell'immagine seguente:

    ![](images/AzureLabs-Lab311-25.png)

## <a name="chapter-5---create-meetingsui-class"></a>Capitolo 5 - Creare la classe MeetingsUI

Il primo script da creare è **MeetingsUI,** responsabile dell'hosting e del popolamento dell'interfaccia utente dell'applicazione (messaggio di benvenuto, istruzioni e dettagli delle riunioni).

Per creare questa classe:

1.  Fare clic con il pulsante destro del mouse sulla cartella **Assets** *nel Project e* quindi scegliere **Crea**  >  **cartella.** Assegnare alla cartella il **nome Scripts**.

    ![](images/AzureLabs-Lab311-26.png)
    ![](images/AzureLabs-Lab311-27.png)

2.  Aprire la cartella **Script** e quindi, all'interno di tale cartella, fare clic con il pulsante destro **del mouse su Crea** script  >  **C#.** Assegnare allo script il **nome MeetingsUI.**

    ![](images/AzureLabs-Lab311-28.png)

3.  Fare doppio clic sul nuovo script **MeetingsUI** per aprirlo con *Visual Studio*.

4.  Inserire gli spazi dei nomi seguenti:

    ```csharp
    using System;
    using UnityEngine;
    ```

5.  All'interno della classe inserire le variabili seguenti:

    ```csharp    
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static MeetingsUI Instance;

        /// <summary>
        /// The 3D text of the scene
        /// </summary>
        private TextMesh _meetingDisplayTextMesh;
    ```

6.  Sostituire quindi il **metodo Start()** e aggiungere un **metodo Awake().** Questi verranno chiamati quando la classe inizializza:

    ```csharp    
        /// <summary>
        /// Called on initialization
        /// </summary>
        void Awake()
        {
            Instance = this;
        }

        /// <summary>
        /// Called on initialization, after Awake
        /// </summary>
        void Start ()
        {
            // Creating the text mesh within the scene
            _meetingDisplayTextMesh = CreateMeetingsDisplay();
        }
    ```

7.  Aggiungere i metodi responsabili della creazione *dell'interfaccia* utente delle riunioni e popolarla con le riunioni correnti quando richiesto:

    ```csharp    
        /// <summary>
        /// Set the welcome message for the user
        /// </summary>
        internal void WelcomeUser(string userName)
        {
            if(!string.IsNullOrEmpty(userName))
            {
                _meetingDisplayTextMesh.text = $"Welcome {userName}";
            }
            else 
            {
                _meetingDisplayTextMesh.text = "Welcome";
            }
        }

        /// <summary>
        /// Set up the parameters for the UI text
        /// </summary>
        /// <returns>Returns the 3D text in the scene</returns>
        private TextMesh CreateMeetingsDisplay()
        {
            GameObject display = new GameObject();
            display.transform.localScale = new Vector3(0.03f, 0.03f, 0.03f);
            display.transform.position = new Vector3(-3.5f, 2f, 9f);
            TextMesh textMesh = display.AddComponent<TextMesh>();
            textMesh.anchor = TextAnchor.MiddleLeft;
            textMesh.alignment = TextAlignment.Left;
            textMesh.fontSize = 80;
            textMesh.text = "Welcome! \nPlease gaze at the button" +
                "\nand use the Tap Gesture to display your meetings";

            return textMesh;
        }

        /// <summary>
        /// Adds a new Meeting in the UI by chaining the existing UI text
        /// </summary>
        internal void AddMeeting(string subject, DateTime dateTime, string location)
        {
            string newText = $"\n{_meetingDisplayTextMesh.text}\n\n Meeting,\nSubject: {subject},\nToday at {dateTime},\nLocation: {location}";

            _meetingDisplayTextMesh.text = newText;
        }
    ```

8. **Eliminare** il **metodo Update()** e **salvare le modifiche** in Visual Studio prima di tornare a Unity. 

## <a name="chapter-6---create-the-graph-class"></a>Capitolo 6- Creare la Graph personalizzata

Lo script successivo da creare è lo script **Graph.** Questo script è responsabile dell'esecuzione delle chiamate per autenticare l'utente e recuperare le riunioni pianificate per il giorno corrente dal calendario dell'utente.

Per creare questa classe:

1.  Fare doppio clic sulla **cartella Script** per aprirla.

2.  Fare clic con il pulsante destro del **mouse all'interno della** cartella Script e **scegliere Crea**  >  **script C#.** Assegnare allo script **il Graph**.

3.  Fare doppio clic sullo script per aprirlo con Visual Studio.

4.  Inserire gli spazi dei nomi seguenti:

    ```csharp
    using System.Collections.Generic;
    using UnityEngine;
    using Microsoft.Identity.Client;
    using System;
    using System.Threading.Tasks;
    
    #if !UNITY_EDITOR && UNITY_WSA
    using System.Net.Http;
    using System.Net.Http.Headers;
    using Windows.Storage;
    #endif
    ```

    > [!IMPORTANT]
    > Si noterà che parti del codice in questo script sono racchiuse tra direttive di precompilazione, allo scopo di evitare problemi con le librerie durante la compilazione della Visual Studio predefinita. [](https://docs.unity3d.com/Manual/PlatformDependentCompilation.html)

5.  Eliminare i **metodi Start()** **e Update()** perché non verranno usati.

6.  **All'Graph,** inserire gli oggetti seguenti, necessari per deserializzare l'oggetto JSON che rappresenta le riunioni pianificate giornaliere:

    ```csharp
    /// <summary>
    /// The object hosting the scheduled meetings
    /// </summary>
    [Serializable]
    public class Rootobject
    {
        public List<Value> value;
    }

    [Serializable]
    public class Value
    {
        public string subject { get; set; }
        public StartTime start { get; set; }
        public Location location { get; set; }
    }

    [Serializable]
    public class StartTime
    {
        public string dateTime;

        private DateTime? _startDateTime;
        public DateTime StartDateTime
        {
            get
            {
                if (_startDateTime != null)
                    return _startDateTime.Value;
                DateTime dt;
                DateTime.TryParse(dateTime, out dt);
                _startDateTime = dt;
                return _startDateTime.Value;
            }
        }
    }

    [Serializable]
    public class Location
    {
        public string displayName { get; set; }
    }
    ```

7.  Nella classe **Graph** aggiungere le variabili seguenti:

    ```csharp    
        /// <summary>
        /// Insert your Application Id here
        /// </summary>
        private string _appId = "-- Insert your Application Id here --";

        /// <summary>
        /// Application scopes, determine Microsoft Graph accessibility level to user account
        /// </summary>
        private IEnumerable<string> _scopes = new List<string>() { "User.Read", "Calendars.Read" };

        /// <summary>
        /// Microsoft Graph API, user reference
        /// </summary>
        private PublicClientApplication _client;

        /// <summary>
        /// Microsoft Graph API, authentication
        /// </summary>
        private AuthenticationResult _authResult;

    ```

    > [!NOTE]
    > Modificare il **valore appId** in modo che sia l'ID app specificato nel **[capitolo 1,](#chapter-1---create-your-app-in-the-application-registration-portal)passaggio 4.**  Questo valore deve essere uguale a quello visualizzato nel portale di registrazione **delle applicazioni,** nella pagina di registrazione dell'applicazione.

8.  Nella classe **Graph** aggiungere i metodi **SignInAsync()** e **AquireTokenAsync()**, che richiederanno all'utente di inserire le credenziali di accesso.

    ```csharp
        /// <summary>
        /// Begin the Sign In process using Microsoft Graph Library
        /// </summary>
        internal async void SignInAsync()
        {
    #if !UNITY_EDITOR && UNITY_WSA
            // Set up Grap user settings, determine if needs auth
            ApplicationDataContainer localSettings = ApplicationData.Current.LocalSettings;
            string userId = localSettings.Values["UserId"] as string;
            _client = new PublicClientApplication(_appId);

            // Attempt authentication
            _authResult = await AcquireTokenAsync(_client, _scopes, userId);

            // If authentication is successful, retrieve the meetings
            if (!string.IsNullOrEmpty(_authResult.AccessToken))
            {
                // Once Auth as been completed, find the meetings for the day
                await ListMeetingsAsync(_authResult.AccessToken);
            }
    #endif
        }

        /// <summary>
        /// Attempt to retrieve the Access Token by either retrieving
        /// previously stored credentials or by prompting user to Login
        /// </summary>
        private async Task<AuthenticationResult> AcquireTokenAsync(
            IPublicClientApplication app, IEnumerable<string> scopes, string userId)
        {
            IUser user = !string.IsNullOrEmpty(userId) ? app.GetUser(userId) : null;
            string userName = user != null ? user.Name : "null";

            // Once the User name is found, display it as a welcome message
            MeetingsUI.Instance.WelcomeUser(userName);

            // Attempt to Log In the user with a pre-stored token. Only happens
            // in case the user Logged In with this app on this device previously
            try
            {
                _authResult = await app.AcquireTokenSilentAsync(scopes, user);
            }
            catch (MsalUiRequiredException)
            {
                // Pre-stored token not found, prompt the user to log-in 
                try
                {
                    _authResult = await app.AcquireTokenAsync(scopes);
                }
                catch (MsalException msalex)
                {
                    Debug.Log($"Error Acquiring Token: {msalex.Message}");
                    return _authResult;
                }
            }
            
            MeetingsUI.Instance.WelcomeUser(_authResult.User.Name);

    #if !UNITY_EDITOR && UNITY_WSA
            ApplicationData.Current.LocalSettings.Values["UserId"] = 
            _authResult.User.Identifier;
    #endif
            return _authResult;
        }
    ```

9.  Aggiungere i due metodi seguenti:

    1.  **BuildTodayCalendarEndpoint(),** che compila l'URI specificando il giorno e l'intervallo di tempo in cui vengono recuperate le riunioni pianificate.

    2.  **ListMeetingsAsync(),** che richiede le riunioni pianificate da *Microsoft Graph*.

    ```csharp
        /// <summary>
        /// Build the endpoint to retrieve the meetings for the current day.
        /// </summary>
        /// <returns>Returns the Calendar Endpoint</returns>
        public string BuildTodayCalendarEndpoint()
        {
            DateTime startOfTheDay = DateTime.Today.AddDays(0);
            DateTime endOfTheDay = DateTime.Today.AddDays(1);
            DateTime startOfTheDayUTC = startOfTheDay.ToUniversalTime();
            DateTime endOfTheDayUTC = endOfTheDay.ToUniversalTime();

            string todayDate = startOfTheDayUTC.ToString("o");
            string tomorrowDate = endOfTheDayUTC.ToString("o");
            string todayCalendarEndpoint = string.Format(
                "https://graph.microsoft.com/v1.0/me/calendarview?startdatetime={0}&enddatetime={1}",
                todayDate,
                tomorrowDate);

            return todayCalendarEndpoint;
        }

        /// <summary>
        /// Request all the scheduled meetings for the current day.
        /// </summary>
        private async Task ListMeetingsAsync(string accessToken)
        {
    #if !UNITY_EDITOR && UNITY_WSA
            var http = new HttpClient();

            http.DefaultRequestHeaders.Authorization = 
            new AuthenticationHeaderValue("Bearer", accessToken);
            var response = await http.GetAsync(BuildTodayCalendarEndpoint());

            var jsonResponse = await response.Content.ReadAsStringAsync();

            Rootobject rootObject = new Rootobject();
            try
            {
                // Parse the JSON response.
                rootObject = JsonUtility.FromJson<Rootobject>(jsonResponse);

                // Sort the meeting list by starting time.
                rootObject.value.Sort((x, y) => DateTime.Compare(x.start.StartDateTime, y.start.StartDateTime));

                // Populate the UI with the meetings.
                for (int i = 0; i < rootObject.value.Count; i++)
                {
                    MeetingsUI.Instance.AddMeeting(rootObject.value[i].subject,
                                                rootObject.value[i].start.StartDateTime.ToLocalTime(),
                                                rootObject.value[i].location.displayName);
                }
            }
            catch (Exception ex)
            {
                Debug.Log($"Error = {ex.Message}");
                return;
            }
    #endif
        }
    ```

10. A questo punto è stato completato **Graph** script. **Salvare le modifiche** in Visual Studio prima di tornare a Unity.

## <a name="chapter-7---create-the-gazeinput-script"></a>Capitolo 7 - Creare lo script GazeInput

A questo punto si creerà **gazeInput.** Questa classe gestisce e tiene traccia dello sguardo dell'utente, usando un **raycast** proveniente dalla **fotocamera principale,** proiettato in avanti.

Per creare lo script:

1.  Fare doppio clic sulla **cartella Script** per aprirla.

2.  Fare clic con il pulsante destro del **mouse all'interno della** cartella Script e **scegliere Crea**  >  **script C#.** Assegnare allo script **il nome GazeInput**.

3.  Fare doppio clic sullo script per aprirlo con Visual Studio.

4.  Modificare il codice degli spazi dei nomi in modo che corrisponda a quello riportato di seguito, insieme all'aggiunta del tag '**\[ System.Serializable \]**' sopra la **classe GazeInput,** in modo che possa essere serializzato:

    ```csharp
    using UnityEngine;

    /// <summary>
    /// Class responsible for the User's Gaze interactions
    /// </summary>
    [System.Serializable]
    public class GazeInput : MonoBehaviour
    {
    ```

5.  **All'interno della classe GazeInput** aggiungere le variabili seguenti:

    ```csharp    
        [Tooltip("Used to compare whether an object is to be interacted with.")]
        internal string InteractibleTag = "SignInButton";

        /// <summary>
        /// Length of the gaze
        /// </summary>
        internal float GazeMaxDistance = 300;

        /// <summary>
        /// Object currently gazed
        /// </summary>
        internal GameObject FocusedObject { get; private set; }

        internal GameObject oldFocusedObject { get; private set; }

        internal RaycastHit HitInfo { get; private set; }

        /// <summary>
        /// Cursor object visible in the scene
        /// </summary>
        internal GameObject Cursor { get; private set; }

        internal bool Hit { get; private set; }

        internal Vector3 Position { get; private set; }

        internal Vector3 Normal { get; private set; }

        private Vector3 _gazeOrigin;

        private Vector3 _gazeDirection;
    ```

6.  Aggiungere il **metodo CreateCursor()** per creare HoloLens cursore nella scena e chiamare il metodo dal **metodo Start():**

    ```csharp    
        /// <summary>
        /// Start method used upon initialisation.
        /// </summary>
        internal virtual void Start()
        {
            FocusedObject = null;
            Cursor = CreateCursor();
        }

        /// <summary>
        /// Method to create a cursor object.
        /// </summary>
        internal GameObject CreateCursor()
        {
            GameObject newCursor = GameObject.CreatePrimitive(PrimitiveType.Sphere);
            newCursor.SetActive(false);
            // Remove the collider, so it doesn't block raycast.
            Destroy(newCursor.GetComponent<SphereCollider>());
            newCursor.transform.localScale = new Vector3(0.05f, 0.05f, 0.05f);
            Material mat = new Material(Shader.Find("Diffuse"));
            newCursor.GetComponent<MeshRenderer>().material = mat;
            mat.color = Color.HSVToRGB(0.0223f, 0.7922f, 1.000f);
            newCursor.SetActive(true);

            return newCursor;
        }
    ```

7.  I metodi seguenti abilitano lo sguardo fisso Raycast e tengono traccia degli oggetti con lo stato attivo.

    ```csharp
    /// <summary>
    /// Called every frame
    /// </summary>
    internal virtual void Update()
    {
        _gazeOrigin = Camera.main.transform.position;

        _gazeDirection = Camera.main.transform.forward;

        UpdateRaycast();
    }
    /// <summary>
    /// Reset the old focused object, stop the gaze timer, and send data if it
    /// is greater than one.
    /// </summary>
    private void ResetFocusedObject()
    {
        // Ensure the old focused object is not null.
        if (oldFocusedObject != null)
        {
            if (oldFocusedObject.CompareTag(InteractibleTag))
            {
                // Provide the 'Gaze Exited' event.
                oldFocusedObject.SendMessage("OnGazeExited", SendMessageOptions.DontRequireReceiver);
            }
        }
    }
    ```

    ```csharp
        private void UpdateRaycast()
        {
            // Set the old focused gameobject.
            oldFocusedObject = FocusedObject;
            RaycastHit hitInfo;

            // Initialise Raycasting.
            Hit = Physics.Raycast(_gazeOrigin,
                _gazeDirection,
                out hitInfo,
                GazeMaxDistance);
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

            // Check whether the previous focused object is this same. If so, reset the focused object.
            if (FocusedObject != oldFocusedObject)
            {
                ResetFocusedObject();
                if (FocusedObject != null)
                {
                    if (FocusedObject.CompareTag(InteractibleTag))
                    {
                        // Provide the 'Gaze Entered' event.
                        FocusedObject.SendMessage("OnGazeEntered", 
                            SendMessageOptions.DontRequireReceiver);
                    }
                }
            }
        }
    ```

8.  **Salvare le modifiche** in Visual Studio prima di tornare a Unity.

## <a name="chapter-8---create-the-interactions-class"></a>Capitolo 8: Creare la classe Interactions

A questo punto è necessario creare lo script **Interazioni,** responsabile di:

-   Gestione **dell'interazione tocco** e dello sguardo **fisso** della fotocamera, che consente all'utente di interagire con il "pulsante" di accesso nella scena.

-   Creazione dell'oggetto "pulsante" di accesso nella scena con cui l'utente può interagire.

Per creare lo script:

1.  Fare doppio clic sulla **cartella Script** per aprirla.

2.  Fare clic con il pulsante destro del **mouse all'interno della** cartella Script e **scegliere Crea**  >  **script C#.** Assegnare allo script **il nome Interactions**.

3.  Fare doppio clic sullo script per aprirlo con Visual Studio.

4.  Inserire gli spazi dei nomi seguenti:

    ```csharp
    using UnityEngine;
    using UnityEngine.XR.WSA.Input;
    ```

5.  Modificare l'ereditarietà **della classe Interaction** da *MonoBehaviour* a **GazeInput.**

    ~~Interazioni tra classi pubbliche: MonoBehaviour~~

    ```csharp
    public class Interactions : GazeInput
    ```

6.  **All'interno della classe** Interaction inserire la variabile seguente:

    ```csharp
        /// <summary>
        /// Allows input recognition with the HoloLens
        /// </summary>
        private GestureRecognizer _gestureRecognizer;
    ```

7.  Sostituire il **metodo Start.** si noti che si tratta di un metodo di override che chiama il metodo della classe Gaze di base. **Start()** verrà chiamato quando la classe viene inizializzata, registrando per il riconoscimento dell'input e creando il pulsante *di* accesso nella scena:

    ```csharp    
        /// <summary>
        /// Called on initialization, after Awake
        /// </summary>
        internal override void Start()
        {
            base.Start();

            // Register the application to recognize HoloLens user inputs
            _gestureRecognizer = new GestureRecognizer();
            _gestureRecognizer.SetRecognizableGestures(GestureSettings.Tap);
            _gestureRecognizer.Tapped += GestureRecognizer_Tapped;
            _gestureRecognizer.StartCapturingGestures();

            // Add the Graph script to this object
            gameObject.AddComponent<MeetingsUI>();
            CreateSignInButton();
        }
    ```

8.  Aggiungere il **metodo CreateSignInButton(),** che creerà un'istanza del pulsante *di* accesso nella scena e ne imposta le proprietà:

    ```csharp    
        /// <summary>
        /// Create the sign in button object in the scene
        /// and sets its properties
        /// </summary>
        void CreateSignInButton()
        {
            GameObject signInButton = GameObject.CreatePrimitive(PrimitiveType.Sphere);

            Material mat = new Material(Shader.Find("Diffuse"));
            signInButton.GetComponent<Renderer>().material = mat;
            mat.color = Color.blue;

            signInButton.transform.position = new Vector3(3.5f, 2f, 9f);
            signInButton.tag = "SignInButton";
            signInButton.AddComponent<Graph>();
        }
    ```

9.  Aggiungere il **metodo GestureRecognizer_Tapped(),** che risponde all'evento *utente Tap.*

    ```csharp   
        /// <summary>
        /// Detects the User Tap Input
        /// </summary>
        private void GestureRecognizer_Tapped(TappedEventArgs obj)
        {
            if(base.FocusedObject != null)
            {
                Debug.Log($"TAP on {base.FocusedObject.name}");
                base.FocusedObject.SendMessage("SignInAsync", SendMessageOptions.RequireReceiver);
            }
        }
    ```

10. **Eliminare** il **metodo Update()** e quindi **salvare le modifiche** in Visual Studio prima di tornare a Unity.

## <a name="chapter-9---set-up-the-script-references"></a>Capitolo 9- Configurare i riferimenti allo script

In questo capitolo è necessario inserire lo script **Interazioni** nella **fotocamera principale.** Lo script gestirà quindi l'inserimento degli altri script dove devono essere.

-  Dalla cartella **Scripts** (Script) nel *pannello Project ,* trascinare lo script **Interactions** (Interazioni) nell'oggetto **Main Camera (Fotocamera** principale), come illustrato di seguito.

    ![](images/AzureLabs-Lab311-29.png)

## <a name="chapter-10---setting-up-the-tag"></a>Capitolo 10 - Configurazione del tag

Il codice che gestisce lo sguardo fisso userà Il tag **SignInButton** per identificare l'oggetto con cui l'utente interagirà per accedere a *Microsoft Graph*.

Per creare il tag:

1.  Nell'editor di Unity fare clic sulla **fotocamera principale** nel pannello *Hierarchy (Gerarchia).*

2.  Nel pannello *Inspector (Controllo)* fai clic su MainCamera *Tag (Tag* **MainCamera)** per aprire un elenco a discesa. Fare clic **su Aggiungi tag...**

    ![](images/AzureLabs-Lab311-30.png)

3.  Fare clic sul **+** pulsante .

    ![](images/AzureLabs-Lab311-31.png)

4.  Scrivere Il nome del tag come **SignInButton e** fare clic su Salva.

    ![](images/AzureLabs-Lab311-32.png)

## <a name="chapter-11---build-the-unity-project-to-uwp"></a>Capitolo 11: Compilare il progetto Unity nella UWP

Tutti gli elementi necessari per la sezione Unity di questo progetto sono stati completati, quindi è il momento di compilarlo da Unity.

1.  Passare a *Build Impostazioni* (**File* > *Build Impostazioni**).

    ![](images/AzureLabs-Lab311-33.png)

2.  Se non è già presente, selezionare **Unity C Projects (Progetti C \# Unity).**

3.  Fare clic su **Compila**. Unity avvierà una **Esplora file,** in cui è necessario creare e quindi selezionare una cartella in cui compilare l'app. Creare la cartella e assegnare alla cartella il nome **App**. Quindi, con la **cartella App** selezionata, fare clic su **Seleziona cartella**.

4.  Unity inizierà a compilare il progetto nella **cartella App.**

5.  Al termine della compilazione, Unity aprirà una finestra **di Esplora file nella** posizione della compilazione(controllare la barra delle applicazioni, perché potrebbe non essere sempre visualizzata sopra le finestre, ma invierà una notifica dell'aggiunta di una nuova finestra).

## <a name="chapter-12---deploy-to-hololens"></a>Capitolo 12: Distribuire in HoloLens

Per eseguire la distribuzione HoloLens:

1.  Sarà necessario l'indirizzo IP del HoloLens (per la distribuzione remota) e per assicurarsi che l'HoloLens sia in **modalità sviluppatore.** Per eseguire questa operazione:

    1.  Mentre si è HoloLens, aprire il **Impostazioni**.

    2.  Passare a **Network & Internet** Wi-Fi Advanced Options (Opzioni avanzate  >  **Wi-Fi** per  >  **Internet)**

    3.  Prendere nota **dell'indirizzo IPv4.**

    4.  Tornare quindi a Impostazioni **e** quindi a Update & Security for Developers **(Aggiorna sicurezza per**  >  **sviluppatori)**

    5.  Impostare **la modalità sviluppatore su**.

2.  Passare alla nuova build di Unity (la **cartella App)** e aprire il file della soluzione **con Visual Studio**.

3.  In Configurazione **soluzione selezionare** **Debug.**

4.  In **Piattaforma soluzione selezionare** **x86, Computer remoto.** Verrà richiesto di inserire l'indirizzo **IP** di un dispositivo remoto (il HoloLens, in questo caso, che è stato specificato.

    ![](images/AzureLabs-Lab311-34.png)

5.  Passare al menu **Compila** e fare clic su **Distribuisci soluzione** per eseguire il sideload dell'applicazione nel HoloLens.

6.  L'app dovrebbe ora essere visualizzata nell'elenco delle app installate nel HoloLens, pronto per l'avvio.

## <a name="your-microsoft-graph-hololens-application"></a>Applicazione microsoft Graph HoloLens

Congratulazioni, hai creato un'app di realtà mista che sfrutta Microsoft Graph, per leggere e visualizzare i dati del calendario dell'utente.

![](images/AzureLabs-Lab311-00.png)

## <a name="bonus-exercises"></a>Esercizi aggiuntivi

### <a name="exercise-1"></a>Esercizio 1

Usare Microsoft Graph per visualizzare altre informazioni sull'utente

-   Indirizzo di posta elettronica/ numero di telefono/immagine del profilo dell'utente

### <a name="exercise-1"></a>Esercizio 1

Implementare il controllo vocale per esplorare l'interfaccia utente Graph Microsoft.
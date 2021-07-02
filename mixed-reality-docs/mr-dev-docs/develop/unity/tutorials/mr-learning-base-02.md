---
title: Inizializzazione del progetto e distribuzione della prima applicazione
description: In questo corso viene illustrato come configurare il progetto Unity per Mixed Reality Toolkit (MRTK) e come distribuirlo in HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens, MRTK, mixed reality toolkit, UWP, TextMeshPro,
ms.localizationpriority: high
ms.openlocfilehash: 7124650a59271b48b763719063411765b5457768
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2021
ms.locfileid: "113175810"
---
# <a name="2-initializing-your-project-and-deploying-your-first-application"></a>2. Inizializzazione del progetto e distribuzione della prima applicazione

In questa esercitazione apprenderai come creare un nuovo progetto Unity, come configurarlo per lo sviluppo Mixed Reality Toolkit (MRTK) e come importare MRTK. Verranno inoltre esaminati i processi di configurazione, compilazione e distribuzione di una scena Unity di base da Visual Studio a HoloLens 2. Dopo la distribuzione in HoloLens 2, dovrebbe essere visualizzata una mesh di mapping spaziale che copre le superfici percepite da HoloLens. Dovresti anche vedere indicatori sulle mani e sulle dita per il tracciamento delle mani e un contatore della frequenza dei fotogrammi per tenere sotto controllo le prestazioni dell'app.

## <a name="objectives"></a>Obiettivi

* Apprendere come configurare Unity per lo sviluppo per HoloLens
* Apprendere come compilare e distribuire l'app in HoloLens
* Sperimentare la mesh di mapping spaziale, le mesh manuali e il contatore della frequenza dei fotogrammi sul dispositivo HoloLens 2

### <a name="steps-overview"></a>Panoramica dei passaggi
:::row:::
    :::column:::
       ![Panoramica Passaggio 1 ](images/mr-learning-base/base-02-overview-step1.png) **1. Creare un nuovo progetto Unity**
    :::column-end:::
    :::column:::
       ![Panoramica Passaggio 2 ](images/mr-learning-base/base-02-overview-step2.png) **2. Importare MRTK nel progetto**
    :::column-end:::
    :::column:::
       ![Panoramica Passaggio 3 ](images/mr-learning-base/base-02-overview-step3.png) **3. Configurare una nuova scena con MRTK**
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::
       ![Panoramica Passaggio 4 ](images/mr-learning-base/base-02-overview-step4.png) **4. Compilare Unity Project**
    :::column-end:::
    :::column:::
       ![Panoramica Passaggio 5 ](images/mr-learning-base/base-02-overview-step5.png) **5. Compilare la Project UWP**
    :::column-end:::
    :::column:::
       ![Panoramica Passaggio 6 ](images/mr-learning-base/base-02-overview-step6.png) **6. Eseguire Project nel dispositivo**
    :::column-end:::
:::row-end:::

## <a name="creating-the-unity-project"></a>Creazione del progetto Unity

Avvia **Unity Hub**, seleziona la scheda **Projects** (Progetti) e fai clic sulla **freccia giù** accanto al pulsante **New** (Nuovo):

<img src="images/mr-learning-base/base-02-section1-step1-1.png" width="650px" alt="Unity Hub with New button highlighted">

Nell'elenco a discesa seleziona la **versione** di Unity specificata nella sezione [Prerequisiti](mr-learning-base-01.md#prerequisites):

<img src="images/mr-learning-base/base-02-section1-step1-2.png" width="650px" alt="Unity Hub with NEW version selector dropdown">


> [!TIP]
> Se la versione specifica di Unity non è disponibile in Unity Hub, puoi avviare l'installazione da <a href="https://unity3d.com/get-unity/download/archive" target="_blank">Download Archive</a> (Archivio download) di Unity.

Nella finestra Create a new project (Crea un nuovo progetto):

* Assicurati che in **Templates** (Modelli) sia impostata l'opzione **3D**
* Immetti un nome appropriato nel campo **Project Name** (Nome progetto), ad esempio _MRTK Tutorials_
* Nel campo **Location** (Percorso) scegli un percorso appropriato in cui archiviare il progetto, ad esempio _D:\MixedRealityLearning_
* Fai clic sul pulsante **Create** (Crea) per creare e avviare il nuovo progetto Unity

<img src="images/mr-learning-base/base-02-section1-step1-3.png" width="650px" alt="Unity Hub with Create a new project window filled out">

> [!CAUTION]
> Se lavori in Windows, tieni presente che è previsto un limite (MAX_PATH) di 255 caratteri per il percorso. Dovresti pertanto salvare il progetto Unity in prossimità della radice dell'unità.

Attendi che Unity crei il progetto:

<img src="images/mr-learning-base/base-02-section1-step1-4.png" width="650px" alt="Unity create new project in progress">

## <a name="switching-the-build-platform"></a>Passaggio a un'altra piattaforma di compilazione

Dal menu di Unity scegli **File** > **Build Settings** (Impostazioni di compilazione) per visualizzare la finestra corrispondente:

![Percorso del menu Build Settings... di Unity](images/mr-learning-base/base-02-section2-step1-1.png)

Nella finestra Build Impostazioni selezionare **Universal Windows Platform** e:

1. Impostare **Dispositivo di destinazione** su **HoloLens**
2. Impostare **Architettura** su **ARM 64** 
3. Impostare **Build Type** (Tipo di compilazione) su **D3D Project**
4. Impostare **Versione SDK di destinazione** su Versione più recente **installata**
5. Impostare **Versione minima della piattaforma** su **10.0.1024.0**
6. Impostare **Visual Studio versione più recente** **installata**
7. Impostare **Compila ed Esegui su** dispositivo **USB**
8. Impostare **Configurazione build** su **Versione** perché si sono noti problemi di prestazioni con debug
9. Fare clic sul pulsante Cambia piattaforma

![Unity Build Impostazioni con le impostazioni della piattaforma Windows universali impostate](images/mr-learning-base/base-02-section2-step1-2-openxr.png)

Attendi che Unity completi il passaggio all'altra piattaforma:

![Passaggio di Unity all'altra piattaforma in corso](images/mr-learning-base/base-02-section2-step1-3-openxr.png)

Al termine del passaggio della piattaforma da parte di Unity, fare clic sull'icona **x** per chiudere la Impostazioni compilazione.

## <a name="importing-the-mixed-reality-toolkit-and-configuring-the-unity-project"></a>Importazione del progetto Toolkit realtà mista e configurazione del progetto Unity

Per importare Toolkit realtà mista nel Project Unity Project è necessario usare lo strumento [funzionalità](../welcome-to-mr-feature-tool.md) realtà mista che consente agli sviluppatori di individuare, aggiornare e aggiungere pacchetti di funzionalità di realtà mista nei progetti Unity. È possibile cercare i pacchetti in base al nome o alla categoria, visualizzarne le dipendenze e persino visualizzare le modifiche proposte al file manifesto del progetto prima dell'importazione.

Scaricare la versione più recente di Mixed Reality Feature Tool dall'Area download [Microsoft](https://aka.ms/MRFeatureTool). Al termine del download, decomprimere il file e salvarlo sul desktop.

> [!NOTE]
> Prima di poter eseguire lo strumento di funzionalità di realtà mista, installare [il runtime di .NET 5.0](https://dotnet.microsoft.com/download/dotnet/thank-you/runtime-desktop-5.0.7-windows-x64-installer)

Aprire il file eseguibile **MixedRealityFeatureTool** dalla cartella scaricata per avviare Mixed Reality Feature Tool.  


<img src="images/mr-learning-base/base-02-section4-step1-1.png" width="750px" alt="Opening MixedRealityFeatureTool">

[!INCLUDE[](includes/importing-mrtk.md)]

## <a name="creating-the-scene-and-configuring-mrtk"></a>Creazione della scena e configurazione di MRTK

Nel menu Unity selezionare **File**  >  **Nuova scena**:

![Percorso del menu New Scene di Unity](images/mr-learning-base/base-02-section6-step1-1.png)

Nella finestra **Nuova scena** selezionare **Basic (incorporato)** e fare clic su **Crea** per creare una nuova scena:

![Finestra Nuova scena di Unity](images/mr-learning-base/base-02-section6-step1-1-newscene.png)

> [!NOTE]
> Lo screenshot precedente è della versione 2020 di Unity, se si  usa Unity 2019 quando si fa clic su Crea una nuova scena vuota.

Nel menu Unity selezionare **Realtà** mista Toolkit Aggiungi alla scena e  >    >  **Configura...** per aggiungere MRTK alla scena corrente:

![Percorso del menu Add to Scene and Configure... di Unity](images/mr-learning-base/base-02-section6-step1-2.png)

Con l'oggetto **MixedRealityToolkit** selezionato nella finestra Hierarchy (Gerarchia), nella finestra Inspector (Controllo) verifica che il profilo di configurazione di **Mixed Reality Toolkit** sia impostato su **DefaultMixedRealityToolkitConfigurationProfile**:

![Componente MixedRealityToolkit di Unity con DefaultMixedRealityTookitConfigurationProfile selezionato](images/mr-learning-base/base-02-section6-step1-3.png)

Dal menu di Unity scegli **File** > **Save As** (Salva con nome) per visualizzare la finestra Save Scene (Salva la scena):

![Percorso del menu Save As... di Unity](images/mr-learning-base/base-02-section6-step1-4.png)

Salvare la scena nel progetto in **Asset**  >  **Scenes**.

![Finestra Save Scene di Unity con il prompt di salvataggio](images/mr-learning-base/base-02-section6-step1-5.png)

## <a name="adding-hand-interaction-to-an-object"></a>Aggiunta dell'interazione manuale a un oggetto

Nel menu Unity selezionare **GameObject**  >  **3D Object**  >  **Cube** per aggiungere un oggetto cubo alla scena.

![Aggiunta di un cubo alla scena](images/mr-learning-base/base-02-section8-step1-1.png)

Fare clic **sull'oggetto** Cube nella finestra Hierarchy (Gerarchia), quindi nella finestra Inspector (Controllo) configurare **il componente Transform (Trasforma)** come indicato di seguito

* **Posizione:** X = 0, Y = -0,1, Z = 0,5
* **Rotation** (Rotazione): X = 0, Y = 0, Z = 0
* **Scala:** X = 0,1, Y = 0,1, Z = 0,1

1 unità Unity è di 1 metro. Le dimensioni del cubo sono state aggiornate a 10x10x10 cm, posizionate a 50 cm dalla posizione del visore (0,0,0). 10 cm sotto il livello dell'occhio per un'interazione comoda. 

Se si usa la scala predefinita (1,1,1), il cubo sarà troppo grande. Se si usa la posizione predefinita (0,0,0), il cubo verrà posizionato nella stessa posizione del visore e non sarà possibile visualizzare il cubo fino a quando non si passa all'indietro.

![Modifica delle informazioni di trasformazione](images/mr-learning-base/base-02-section8-step1-1b.png)

Per concentrarsi sugli oggetti nella scena, è possibile fare doppio clic **sull'oggetto Cubo** e quindi eseguire di nuovo lo zoom avanti leggermente. Oppure è possibile usare il tasto F per eseguire lo zoom e lo stato attivo sull'oggetto.

Per interagire e afferrare un oggetto con le mani tracciate, l'oggetto deve avere:
 * Componente collisore, ad **esempio Box Collider** (il cubo di Unity ha già un Collisore di box per impostazione predefinita)
 * Componente **Object Manipulator (Script)** (Manipolatore oggetti - script)
 * **Componente NearInteractionGrabbable(Script)**

Lo script **ObjectManipulator** di MRTK rende un oggetto mobile, scalabile e rotabile usando una o due mani. Questo script supporta il modello di input di manipolazione diretta in quanto consente all'utente di toccare gli ologrammi direttamente con le proprie mani.

Con il **cubo** ancora selezionato nella finestra Hierarchy (Gerarchia), nella finestra Inspector (Controllo) fare clic sul pulsante **Add Component** (Aggiungi componente), quindi cercare e selezionare **Object Manipulator** script (Manipolatore di oggetti) per aggiungere lo script Object Manipulator all'oggetto cubo.

![aggiunta dell'oggetto manupulator al cubo](images/mr-learning-base/base-02-section8-step1-2.PNG)

Ripetere la stessa operazione per aggiungere **lo script Near Interaction Grabbable** al cubo

![aggiunta di Near Interaction Grabable al cubo](images/mr-learning-base/base-02-section8-step1-3.PNG)

> [!NOTE]
> Quando si aggiunge un manipolatore di oggetti (script), in questo caso, Gestione vincoli (script) viene aggiunto automaticamente perché il manipolatore di oggetti (script) dipende da esso.

## <a name="testing-your-application-in-unity-editor-with-mrtk-input-simulation"></a>Test dell'applicazione nell'editor unity con simulazione di input MRTK

Con la simulazione di input di MRTK è possibile testare vari tipi di interazioni nell'editor di Unity senza compilare e distribuire in un dispositivo. In questo modo è possibile scorrere rapidamente le idee nel processo di progettazione e sviluppo. Usare combinazioni di tastiera e mouse per controllare gli input simulati.

Fare clic sul pulsante play (Riproduci) e immettere la modalità di riproduzione. Tenere premuto MAIUSC  **sinistro** o BARRA SPAZIATRICE per visualizzare il controller (mani simulate), lo spostamento del mouse sposterà il controller e potrà anche essere spostato più o più vicino alla fotocamera usando la rotellina del mouse. Quando il puntatore è posizionato sul cubo, tenere premuto **il pulsante sinistro del mouse** per afferrare l'oggetto Cube.

* Premere **i tasti W, A, S, D, Q, E** per spostare la fotocamera.
* Tenere premuto **il pulsante destro del mouse** e spostare il mouse per guardarsi attorno.
* Per visualizzare le mani simulate, premere **BARRA SPAZIATRICE (mano destra)** o **MAIUSC sinistro (mano sinistra)**
* Per mantenere le mani simulate nella visualizzazione, premere **il tasto T** o **Y**
* Per ruotare le mani simulate, tenere premuto **CTRL** e spostare il mouse

![Modalità di gioco](images/mr-learning-base/base-02-section8-step1-4.gif)


## <a name="building-your-application-to-your-hololens-2"></a>Compilazione dell'applicazione nel dispositivo HoloLens 2

### <a name="1-build-the-unity-project"></a>1. Compilare il progetto Unity

Dal menu di Unity scegli **File** > **Build Settings** (Impostazioni di compilazione) per visualizzare la finestra corrispondente.

Nella finestra Build Settings (Impostazioni di compilazione), fai clic sul pulsante **Add Open Scenes** (Aggiungi scene aperte) per aggiungere la scena corrente all'elenco **Scenes In Build** (Scene in compilazione) e quindi fai clic sul pulsante **Build** (Compila) per visualizzare la finestra Build Universal Windows Platform (Compilazione UWP):

![Finestra Build Settings di Unity con la piattaforma UWP selezionata](images/mr-learning-base/base-02-section9-step1-1.png)

Nella finestra Build Universal Windows Platform (Compilazione UWP), scegli un percorso appropriato in cui archiviare la compilazione, ad esempio _D:\MixedRealityLearning\Builds_, crea una nuova cartella e assegnale un nome adatto (ad esempio, _GettingStarted_) e quindi fai clic sul pulsante **Select Folder** (Seleziona cartella) per avviare il processo di compilazione:

![Finestra Build Settings di Unity con la finestra del prompt di selezione della cartella](images/mr-learning-base/base-02-section9-step1-2.png)

Attendi che Unity completi il processo di compilazione:

![Processo di compilazione di Unity in corso](images/mr-learning-base/base-02-section9-step1-3.png)

### <a name="2-build-and-deploy-the-application"></a>2. Compilare e distribuire l'applicazione

Al termine del processo di compilazione, Unity richiederà a Esplora file di Windows di aprire il percorso in cui è stata archiviata la compilazione. Spostati all'interno della cartella e fai doppio clic sul file della soluzione per aprirlo in Visual Studio:

![Esplora risorse con la soluzione di Visual Studio appena creata selezionata](images/mr-learning-base/base-02-section10-step1-1.png)

> [!NOTE]
> Se Visual Studio chiede di installare nuovi componenti, dedica qualche minuto a verificare di disporre di tutti i componenti indispensabili come specificato nella documentazione **[Installare gli strumenti](../../install-the-tools.md)** .

Configura Visual Studio per HoloLens selezionando la configurazione **Master** o **Release**, l'architettura **ARM64** e **Dispositivo** come destinazione:

![Visual Studio configurato per la distribuzione in HoloLens 2](images/mr-learning-base/base-02-section10-step1-2.png)

> [!TIP]
> Se esegui la distribuzione in HoloLens (1a generazione), seleziona l'architettura **x86**.

> [!NOTE]
> Per HoloLens, in genere la compilazione viene eseguita per l'architettura ARM. Esiste tuttavia un <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank"><strong>problema noto</strong></a> in Unity 2019.3 che causa errori quando viene selezionata l'architettura di compilazione ARM in Visual Studio. La soluzione consigliata consiste nel compilare per ARM64. Se questa opzione non è applicabile, passa a **Modifica > Impostazioni progetto > Player (Lettore) > Altre impostazioni** e disabilita **Graphics Jobs** (Processi grafici).

> [!NOTE]
> Se non viene visualizzata l'opzione Dispositivo come destinazione, potresti dover modificare il progetto di avvio per la soluzione di Visual Studio passando dal progetto IL2CPP al progetto UWP. A tale scopo, in Esplora soluzioni fai clic con il pulsante destro del mouse su NomeProgetto (Windows universale) e scegli **Imposta come progetto di avvio**.

Connetti HoloLens al computer e quindi seleziona **Debug** > **Avvia senza eseguire il debug** per eseguire la compilazione e la distribuzione nel dispositivo:

![Percorso del menu di avvio di Visual Studio senza debug](images/mr-learning-base/base-02-section10-step1-3.png)

> [!IMPORTANT]
> Prima della compilazione nel dispositivo, quest'ultimo deve essere in modalità sviluppatore e associato al computer di sviluppo. Per completare i due passaggi segui [queste istruzioni](../../platform-capabilities-and-apis/using-visual-studio.md).

> [!TIP]
> Puoi anche eseguire la distribuzione nell'[emulatore HoloLens](../../platform-capabilities-and-apis/using-the-hololens-emulator.md) o creare un [Pacchetto applicazione](/windows/uwp/packaging/packaging-uwp-apps) per il sideload.

Usando Avvia senza eseguire il debug, l'app viene avviata nel dispositivo senza collegare il debugger di Visual Studio.

Seleziona **Compila > Distribuisci soluzione** per eseguire la distribuzione nel dispositivo senza che l'app venga avviata automaticamente.

> [!NOTE]
>È possibile notare il profiler di diagnostica nell'app, che è possibile attivare o disattivare usando il comando vocale **"Attiva/Disattiva diagnostica".** È consigliabile mantenere visibile il profiler la maggior parte del tempo durante lo sviluppo per verificare quando le modifiche apportate all'app possono produrre effetti negativi sulle prestazioni. Le app HoloLens ad esempio devono [essere eseguite costantemente a 60 FPS](../../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md).

## <a name="congratulations"></a>Lezione completata

A questo punto hai distribuito la tua prima app per HoloLens. Una volta aperta l'app, dovrebbe essere visualizzato un oggetto Cube e dovrebbe essere possibile interagire con il cubo spostando il cubo e, mentre ci si sposta, si dovrebbe vedere una mesh di mapping spaziale che copre le superfici percepite dal HoloLens. Dovresti anche vedere indicatori sulle mani e sulle dita per il tracciamento delle mani e un contatore della frequenza dei fotogrammi per tenere sotto controllo le prestazioni dell'app. Queste funzionalità sono solo alcune delle parti fondamentali incluse in MRTK. Nelle esercitazioni successive aggiungerai contenuto alla scena per esplorare le funzionalità di HoloLens e MRTK.

> [!div class="nextstepaction"]
> [Esercitazione successiva: 3. Configurazione dei profili di MRTK](mr-learning-base-03.md)

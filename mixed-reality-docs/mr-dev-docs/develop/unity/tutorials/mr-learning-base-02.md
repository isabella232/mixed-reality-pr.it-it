---
title: Inizializzazione del progetto e distribuzione della prima applicazione
description: In questo corso viene illustrato come configurare il progetto Unity per Mixed Reality Toolkit (MRTK) e come distribuirlo in HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens, MRTK, mixed reality toolkit, UWP, TextMeshPro,
ms.localizationpriority: high
ms.openlocfilehash: c9cf580b1123002e9e8cdfd5c3914c3aa39e2825
ms.sourcegitcommit: 848b4b7bb8514c2e088a3a55512b1a8075d29093
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/07/2021
ms.locfileid: "107003130"
---
# <a name="2-initializing-your-project-and-deploying-your-first-application"></a>2. Inizializzazione del progetto e distribuzione della prima applicazione

In questa esercitazione apprenderai come creare un nuovo progetto Unity, come configurarlo per lo sviluppo <a href="https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/" target="_blank">Mixed Reality Toolkit (MRTK)</a> e come importare MRTK. Verranno inoltre esaminati i processi di configurazione, compilazione e distribuzione di una scena Unity di base da Visual Studio a HoloLens 2. Dopo la distribuzione in HoloLens 2, dovrebbe essere visualizzata una mesh di mapping spaziale che copre le superfici percepite da HoloLens. Dovresti anche vedere indicatori sulle mani e sulle dita per il tracciamento delle mani e un contatore della frequenza dei fotogrammi per tenere sotto controllo le prestazioni dell'app.

![MRTK](../../../develop/images/Unity_MRTK_MRFT_Flow.png)

## <a name="objectives"></a>Obiettivi

* Apprendere come configurare Unity per lo sviluppo per HoloLens
* Apprendere come compilare e distribuire l'app in HoloLens
* Sperimentare la mesh di mapping spaziale, le mesh manuali e il contatore della frequenza dei fotogrammi sul dispositivo HoloLens 2

## <a name="creating-the-unity-project"></a>Creazione del progetto Unity

Avvia **Unity Hub**, seleziona la scheda **Projects** (Progetti) e fai clic sulla **freccia giù** accanto al pulsante **New** (Nuovo):

![Unity Hub con il pulsante New evidenziato](images/mr-learning-base/base-02-section1-step1-1.png)

Nell'elenco a discesa seleziona la **versione** di Unity specificata nella sezione [Prerequisiti](mr-learning-base-01.md#prerequisites):

![Unity Hub con l'elenco a discesa per la seleziona della versione NEW](images/mr-learning-base/base-02-section1-step1-2.png)

> [!TIP]
> Se la versione specifica di Unity non è disponibile in Unity Hub, puoi avviare l'installazione da <a href="https://unity3d.com/get-unity/download/archive" target="_blank">Download Archive</a> (Archivio download) di Unity.

Nella finestra Create a new project (Crea un nuovo progetto):

* Assicurati che in **Templates** (Modelli) sia impostata l'opzione **3D**
* Immetti un nome appropriato nel campo **Project Name** (Nome progetto), ad esempio _MRTK Tutorials_
* Nel campo **Location** (Percorso) scegli un percorso appropriato in cui archiviare il progetto, ad esempio _D:\MixedRealityLearning_
* Fai clic sul pulsante **Create** (Crea) per creare e avviare il nuovo progetto Unity

![Unity Hub con la finestra Create a new project compilata](images/mr-learning-base/base-02-section1-step1-3.png)

> [!CAUTION]
> Se lavori in Windows, tieni presente che è previsto un limite (MAX_PATH) di 255 caratteri per il percorso. Dovresti pertanto salvare il progetto Unity in prossimità della radice dell'unità.

Attendi che Unity crei il progetto:

![Creazione di un nuovo progetto Unity in corso](images/mr-learning-base/base-02-section1-step1-4.png)

## <a name="switching-the-build-platform"></a>Passaggio a un'altra piattaforma di compilazione

[!INCLUDE[](includes/switching-build-platform.md)]

## <a name="importing-the-textmeshpro-essential-resources"></a>Importazione delle risorse essenziali TextMeshPro

Scegli **Window (Finestra)**  > **TextMeshPro** > **Import TMP Essential Resources** (Importa le risorse essenziali TMP) dal menu di Unity per aprire la finestra Import Unity Package (Importa pacchetto Unity):

![Percorso del menu Import TMP Essential Resources di Unity](images/mr-learning-base/base-02-section3-step1-1.png)

Nella finestra Import Unity Package (Importa il pacchetto Unity), fai clic sul pulsante **All** (Tutti) per assicurarti che vengano selezionati tutti gli asset e quindi fai clic sul pulsante **Import** (Importa) per importare gli asset:

![Finestra di importazione TMP Essential Resources di Unity](images/mr-learning-base/base-02-section3-step1-2.png)

> [!TIP]
> Le risorse essenziali TextMeshPro sono richieste dagli elementi dell'interfaccia utente di MRTK. Puoi ignorare questo passaggio se non prevedi di usare gli elementi dell'interfaccia utente di MRTK nel progetto.

## <a name="importing-the-mixed-reality-toolkit"></a>Importazione di Mixed Reality Toolkit

Per importare il Toolkit di realtà mista nel progetto Unity, è necessario usare [lo strumento per la funzionalità di realtà mista](../welcome-to-mr-feature-tool.md) che consente agli sviluppatori di individuare, aggiornare e aggiungere pacchetti di funzionalità di realtà mista in progetti Unity. È possibile cercare i pacchetti in base al nome o alla categoria, visualizzarne le dipendenze e persino visualizzare le modifiche proposte al file manifesto del progetto prima dell'importazione.

Scaricare la versione più recente dello strumento per le funzionalità di realtà mista dall' [area download Microsoft](https://aka.ms/MRFeatureTool), al termine del download, decomprimere il file e salvarlo sul desktop.

> [!NOTE]
> Prima di poter eseguire lo strumento per la funzionalità di realtà mista, installare il [runtime di .net 5,0](https://dotnet.microsoft.com/download/dotnet/5.0)

> [!NOTE]
> Lo strumento per la funzionalità di realtà mista attualmente viene eseguito solo in Windows. per MacOS, seguire questa [procedura](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html#1-get-the-latest-mrtk-unity-packages) per scaricare e importare il Toolkit di realtà mista nel progetto Unity.

Aprire il file eseguibile **MixedRealityFeatureTool** dalla cartella scaricata per avviare lo strumento della funzionalità di realtà mista.  

![Apertura di MixedRealityFeatureTool](images/mr-learning-base/base-02-section4-step1-1.png)


[!INCLUDE[](includes/importing-mrtk.md)]

## <a name="configuring-the-unity-project"></a>Configurazione del progetto Unity

### <a name="1-apply-the-mrtk-project-configurator-settings"></a>1. Applicare le impostazioni di MRTK Project Configurator (Configuratore del progetto MRTK)

Al termine dell'importazione del pacchetto dalla sezione precedente, viene visualizzata la finestra MRTK Project Configurator (Configuratore del progetto MRTK). In caso contrario, è possibile aprirlo manualmente passando a **Mixed Reality Toolkit** > **Utilities** (Utilità) > **Configure Unity Project** (Configura il progetto Unity):

![Percorso del menu Configure Unity Project di Unity](images/mr-learning-base/base-02-section5-step1-1.png)

Nella finestra MRTK Project Configurator (Configuratore del progetto MRTK) espandi la sezione **Modify Configurations** (Modifica configurazioni), verifica che tutte le opzioni siano selezionate e fai clic sul pulsante **Apply** (Applica) per applicare le impostazioni:

![Finestra MRTK Project Configurator di Unity](images/mr-learning-base/base-02-section5-step1-2.png)

> [!TIP]
> L'applicazione delle impostazioni predefinite di MRTK è facoltativa ma fortemente consigliata, poiché consente di configurare alcune impostazioni consigliate di Unity:

> * Set Single Pass Instanced rendering path (Imposta il percorso di rendering con istanze a singolo passaggio): migliora le prestazioni grafiche eseguendo la pipeline di rendering per entrambi gli occhi nella stessa chiamata di disegno. Per altre informazioni su questo argomento, è possibile fare riferimento alla sezione sul [rendering con istanze a singolo passaggio](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering) della documentazione di MRTK relativa alle [prestazioni](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering).
> * Set default Spatial Awareness layer (Imposta livello di consapevolezza spaziale predefinito): crea un livello di Unity denominato Spatial Awareness e configura MRTK per l'uso di questo livello per la mesh di consapevolezza spaziale. Per altre informazioni sui livelli di Unity, vedere la documentazione relativa alla <a href="https://docs.unity3d.com/Manual/Layers.html" target="_blank">personalizzazione dell'area di lavoro</a> di Unity.

### <a name="2-configure-additional-project-settings"></a>2. Configurare impostazioni di progetto aggiuntive

[!INCLUDE[](includes/configuring-additional-project-settings.md)]

## <a name="creating-the-scene-and-configuring-mrtk"></a>Creazione della scena e configurazione di MRTK

Scegli **File** > **New Scene** (Nuova scena) dal menu di Unity per creare una nuova scena:

![Percorso del menu New Scene di Unity](images/mr-learning-base/base-02-section6-step1-1.png)

Scegli **Mixed Reality Toolkit** > **Add to Scene and Configure...** (Aggiungi alla scena e configura) dal menu di Unity per aggiungere MRTK alla scena corrente:

![Percorso del menu Add to Scene and Configure... di Unity](images/mr-learning-base/base-02-section6-step1-2.png)

[!INCLUDE[](includes/changing-profile.md)]

Dal menu di Unity scegli **File** > **Save As** (Salva con nome) per visualizzare la finestra Save Scene (Salva la scena):

![Percorso del menu Save As... di Unity](images/mr-learning-base/base-02-section6-step1-4.png)

> [!TIP]
> La riduzione del formato profondità a 16 bit è facoltativa, ma consente di migliorare le prestazioni grafiche nel progetto. Per ulteriori informazioni su questo argomento, è possibile fare riferimento alla sezione   <a href="/windows/mixed-reality/mrtk-unity/performance/perf-getting-started.md#single-pass-instanced-rendering" target="_blank">  HoloLens (depth buffer sharing) </a> della documentazione  <a href="/windows/mixed-reality/mrtk-unity/performance/perf-getting-started.md#single-pass-instanced-rendering" target="_blank"> sulle prestazioni </a> di MRTK.

![Finestra Save Scene di Unity con il prompt di salvataggio](images/mr-learning-base/base-02-section6-step1-5.png)

## <a name="importing-the-tutorial-assets"></a>Importazione degli asset dell'esercitazione

Scaricare il pacchetto personalizzato Unity seguente:

* [MRTK. HoloLens2. Unity. Esercitations. assets. GettingStarted. 2.5.0.1. file unitypackage Tools](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.5.0/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.5.0.1.unitypackage)

Per importare un pacchetto personalizzato Unity, nel menu Unity selezionare **Asset**  >  **Import Package**  >  **Custom Package..** . per aprire il pacchetto di importazione... finestra

![Importazione di un pacchetto personalizzato](images/mr-learning-base/base-02-section7-step1-1.png)

Nel pacchetto di importazione... Selezionare il **MRTK. HoloLens2. Unity. Tutorials. assets. GettingStarted. 2.5.0.1. file unitypackage Tools** è stato scaricato e si fa clic sul pulsante Apri:

![Selezione di un pacchetto di asset](images/mr-learning-base/base-02-section7-step1-2.png)

Nella finestra Import Unity Package (Importa il pacchetto Unity), fai clic sul pulsante All (Tutti) per assicurarti che vengano selezionati tutti gli asset e quindi fai clic sul pulsante Import (Importa) per importare gli asset:

![Selezione di tutti gli asset da importare](images/mr-learning-base/base-02-section7-step1-3.png)

Dopo l'importazione degli asset dell'esercitazione, la finestra Project (Progetto) avrà un aspetto simile al seguente:

![Finestra del progetto Unity dopo l'importazione di asset](images/mr-learning-base/base-02-section7-step1-4.png)

## <a name="configuring-the-scene"></a>Configurazione della scena

Nella finestra del progetto passare al Asset > MRTK. Tutorials. GettingStarted > cartella prefabbricates:

Dalla finestra del progetto, fare clic e trascinare il prefabbricato **Cube** nella finestra gerarchia, quindi nella finestra di controllo configurare il componente **Transform** come indicato di seguito.

* **Posizione**: X = 0, Y = 0, Z = 0,5
* **Rotation** (Rotazione): X = 0, Y = 0, Z = 0
* **Scale** (Scala): X = 1, Y = 1, Z = 1

![Aggiunta del cubo alla scena](images/mr-learning-base/base-02-section8-step1-1.png)

Per concentrare l'attenzione sugli oggetti nella scena, è possibile fare doppio clic sull'oggetto **cubo** , quindi eseguire nuovamente lo zoom indietro:

Per interagire e acquisire un oggetto con le lancette rilevate, l'oggetto deve avere un componente Collider, ad esempio un componente di **Box Collider**, un componente di  **manipolazione degli oggetti (script)** e un componente **NearInteractionGrabbable (script)** .

Con il **cubo** ancora selezionato nella finestra gerarchia, nella finestra di controllo fare clic sul pulsante **Aggiungi componente** , quindi cercare e selezionare script **manipolatore oggetto** per aggiungere lo script del manipolatore di oggetti all'oggetto cubo.

![Aggiunta dell'oggetto manupulator al cubo](images/mr-learning-base/base-02-section8-step1-2.png)

Ripetere lo stesso per aggiungere lo **script near Interactionable di interazione** al cubo

![Aggiunta di near interactionable al cubo](images/mr-learning-base/base-02-section8-step1-3.png)

> [!NOTE]
> Quando si aggiunge un manipolatore di oggetti (script), in questo caso, il gestore di vincoli (script) viene aggiunto automaticamente perché il manipolatore di oggetti (script) dipende da esso.

> [!NOTE]
> Ai fini di questa esercitazione, i Collider sono già stati aggiunti all'oggetto Cube. Per altre informazioni sui collisori, puoi visitare la documentazione <a href="https://docs.unity3d.com/Manual/CollidersOverview.html" target="_blank">corrispondente</a> di Unity.

Per eseguire il test nell'editor di Unity, è possibile attivare la modalità di riproduzione e tenere premuto il **LeftShift** o **lo spazio** per abilitare il controller, il movimento del mouse sposterà il controller e anche può essere spostato più o più vicino alla fotocamera usando la rotellina del mouse. Quando il puntatore si trova sul cubo, premere e tenere premuto il **pulsante destro del mouse** per spostare l'oggetto cubo.

![Modalità di gioco](images/mr-learning-base/base-02-section8-step1-4.png)

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
>Potrebbe essere visibile nell'app il profiler di diagnostica, che può essere attivato o disattivato tramite il comando vocale **Toggle Diagnostics** (Attiva/Disattiva diagnostica). È consigliabile mantenere visibile il profiler la maggior parte del tempo durante lo sviluppo per verificare quando le modifiche apportate all'app possono produrre effetti negativi sulle prestazioni. Le app HoloLens ad esempio devono [essere eseguite costantemente a 60 FPS](../../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md).

## <a name="congratulations"></a>Lezione completata

A questo punto hai distribuito la tua prima app per HoloLens. Dopo che l'app è stata aperta, dovrebbe essere visualizzato un oggetto cubo davanti all'utente e dovrebbe essere in grado di interagire con il cubo spostando l'app e anche quando si procede in questo modo, verrà visualizzata una mesh di mapping spaziale che copre le superfici percepite dal HoloLens. Dovresti anche vedere indicatori sulle mani e sulle dita per il tracciamento delle mani e un contatore della frequenza dei fotogrammi per tenere sotto controllo le prestazioni dell'app. Queste funzionalità sono solo alcune delle parti fondamentali incluse in MRTK. Nelle esercitazioni successive aggiungerai contenuto alla scena per esplorare le funzionalità di HoloLens e MRTK.

> [!div class="nextstepaction"]
> [Esercitazione successiva: 3. Configurazione dei profili di MRTK](mr-learning-base-03.md)

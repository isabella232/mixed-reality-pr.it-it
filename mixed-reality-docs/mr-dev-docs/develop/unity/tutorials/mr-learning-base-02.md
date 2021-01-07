---
title: Esercitazioni di MRTK - 2. Inizializzazione del progetto e distribuzione della prima applicazione
description: In questo corso viene illustrato come configurare il progetto Unity per Mixed Reality Toolkit (MRTK) e come distribuirlo in HoloLens 2.
author: jessemcculloch
ms.author: v-vtieto
ms.date: 12/30/2020
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens, MRTK, mixed reality toolkit, UWP, TextMeshPro,
ms.localizationpriority: high
ms.openlocfilehash: ebf81b9b1ae1abb5001b88e0f2b2929c45c22d7f
ms.sourcegitcommit: 50d9afae479e418b885dc883ce88771292923f01
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/04/2021
ms.locfileid: "97859530"
---
# <a name="2-initializing-your-project-and-deploying-your-first-application"></a>2. Inizializzazione del progetto e distribuzione della prima applicazione

## <a name="overview"></a>Panoramica

In questa esercitazione apprenderai come creare un nuovo progetto Unity, come configurarlo per lo sviluppo <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank">Mixed Reality Toolkit (MRTK)</a> e come importare MRTK. Verranno inoltre esaminati i processi di configurazione, compilazione e distribuzione di una scena Unity di base da Visual Studio a HoloLens 2. Dopo la distribuzione in HoloLens 2, dovrebbe essere visualizzata una mesh di mapping spaziale che copre le superfici percepite da HoloLens. Dovresti anche vedere indicatori sulle mani e sulle dita per il tracciamento delle mani e un contatore della frequenza dei fotogrammi per tenere sotto controllo le prestazioni dell'app.

## <a name="objectives"></a>Obiettivi

* Apprendere come configurare Unity per lo sviluppo per HoloLens.
* Apprendere come compilare e distribuire l'app in HoloLens.
* Sperimentare la mesh di mapping spaziale, le mesh mano il contatore della frequenza dei fotogrammi sul dispositivo HoloLens 2.

## <a name="creating-the-unity-project"></a>Creazione del progetto Unity

1. Avviare **Unity Hub**, selezionare la scheda **Projects** (Progetti) e quindi fare clic sulla **freccia giù** accanto al pulsante **New** (Nuovo):

![Unity Hub in cui è evidenziata la freccia giù del pulsante "New" (Nuovo)](images/mr-learning-base/base-02-section1-step1-1.png)

2. Dal menu a discesa scegliere la versione di Unity specificata nella sezione [Prerequisiti](mr-learning-base-01.md#prerequisites):

![Selezionare la versione di Unity](images/mr-learning-base/base-02-section1-step1-2.png)

> [!TIP]
> Se la versione specifica di Unity non è disponibile in Unity Hub, puoi avviare l'installazione da <a href="https://unity3d.com/get-unity/download/archive" target="_blank">Download Archive</a> (Archivio download) di Unity.

3. Nella finestra **Create a new project** (Crea un nuovo progetto) eseguire queste operazioni:

    * Assicurarsi che in **Templates** (Modelli) sia impostata l'opzione **3D**.
    * Nella casella **Project Name** (Nome progetto) immettere un nome appropriato per il progetto, ad esempio "Esercitazioni di MRTK".
    * Fare clic sul pulsante con tre punti accanto a **Location** (Percorso) e quindi passare alla cartella in cui si intende salvare il progetto.

> [!CAUTION]
> Se lavori in Windows, tieni presente che è previsto un limite (MAX_PATH) di 255 caratteri per il percorso. È pertanto consigliabile salvare il progetto Unity in prossimità della radice dell'unità.

    * Fare clic sul pulsante **Create** (Crea). Il nuovo progetto Unity viene creato e avviato.

![Unity Hub con la finestra "Create a new project" (Crea un nuovo progetto) completata](images/mr-learning-base/base-02-section1-step1-3.png)

La barra di stato consente di restare aggiornati sullo stato di avanzamento.

![L'indicatore di stato di Unity consente di restare aggiornati sullo stato di "creazione del progetto"](images/mr-learning-base/base-02-section1-step1-4.png)

## <a name="switching-the-build-platform"></a>Passaggio a un'altra piattaforma di compilazione

1. Sulla barra dei menu scegliere **File** > **Build Settings** (Impostazioni di compilazione).

![Percorso del menu Build Settings... di Unity](images/mr-learning-base/base-02-section2-step1-1.png)

2. Nella finestra **Build Settings** (Impostazioni di compilazione) selezionare **Universal Windows Platform** (Piattaforma UWP) e quindi fare clic sul pulsante **Switch Platform** (Cambia piattaforma):

![Finestra Build Settings di Unity con la piattaforma UWP selezionata in sostituzione della piattaforma Standalone](images/mr-learning-base/base-02-section2-step1-2.png)

3. Attendere che venga completato il cambiamento di piattaforma e quindi chiudere la finestra **Build Settings** (Impostazioni di compilazione).

## <a name="importing-the-textmeshpro-essential-resources"></a>Importazione delle risorse essenziali TextMeshPro

Le risorse essenziali TextMeshPro sono richieste dagli elementi dell'interfaccia utente di MRTK. Se non si prevede di usare gli elementi dell'interfaccia utente di MRTK nel progetto, è possibile ignorare questo passaggio.

1. Sulla barra dei menu scegliere **Window** (Finestra) > **TextMeshPro** > **Import TMP Essential Resources** (Importa le risorse essenziali TMP).

![Percorso del menu Import TMP Essential Resources di Unity](images/mr-learning-base/base-02-section3-step1-1.png)

2. Nella finestra **Import Unity Package** (Importa il pacchetto Unity) fare clic sul pulsante **All** (Tutti) per assicurarsi che vengano selezionati tutti gli asset e quindi fare clic sul pulsante **Import** (Importa) per importare gli asset:

![Finestra di importazione TMP Essential Resources di Unity](images/mr-learning-base/base-02-section3-step1-2.png)

## <a name="importing-the-mixed-reality-toolkit"></a>Importazione di Mixed Reality Toolkit

1. Scarica il pacchetto personalizzato di Unity:

    [Microsoft.MixedReality.Toolkit.Unity.Foundation.2.4.0.unitypackage](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.4.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.4.0.unitypackage)

2. Sulla barra dei menu scegliere **Assets** (Asset) > **Import Package (Importa pacchetto)**  > **Custom Package** (Pacchetto personalizzato).
3. Nella finestra di dialogo **Import package** (Importa pacchetto) passare al percorso del pacchetto appena scaricato, selezionare il pacchetto e quindi fare clic sul pulsante **Open** (Apri).
4. Nella finestra **Import Unity Package** (Importa il pacchetto Unity) fare clic sul pulsante **All** (Tutti) per assicurarsi che vengano selezionati tutti gli asset e quindi fare clic sul pulsante **Import** (Importa) per importare gli asset.

## <a name="selecting-mrtk-and-project-settings"></a>Selezione delle impostazioni di MRTK e del progetto

Al termine dell'importazione del pacchetto dalla sezione precedente, viene visualizzata la finestra **MRTK Project Configurator** (Configuratore del progetto MRTK). In caso contrario, è possibile aprirlo manualmente passando a **Mixed Reality Toolkit** > **Utilities** (Utilità) > **Configure Unity Project** (Configura il progetto Unity):

![Percorso del menu Configure Unity Project di Unity](images/mr-learning-base/base-02-section5-step1-1.png)

1. Nella finestra **MRTK Project Configurator** (Configuratore del progetto MRTK) espandere la sezione **Modify Configurations** (Modifica configurazioni), se necessario, e quindi verificare che tutte le opzioni siano selezionate.

![Finestra MRTK Project Configurator (Configuratore del progetto MRTK) di Unity in cui è visualizzata la sezione Modify Configurations (Modifica configurazioni)](images/mr-learning-base/base-02-section5-step1-2.png)

2. Per applicare le impostazioni, fare clic sul pulsante **Apply** (Applica).

![Pulsante Apply (Applica) in MRTK](images/mr-learning-base/apply.png)

> [!NOTE]
> Viene usata la versione legacy di XR incorporata in Unity, invece del nuovo sistema di plug-in XR, perché il nuovo sistema non è completamente compatibile con le [versioni consigliate di Unity e MRTK](mr-learning-base-01.md#prerequisites) per questa serie di esercitazioni. Se vengono visualizzati avvisi relativi alla deprecazione di XR incorporata, è possibile ignorarli.

> [!TIP]
> L'applicazione delle impostazioni predefinite di MRTK è facoltativa ma fortemente consigliata, poiché consente di configurare alcune impostazioni consigliate di Unity:
>
> * Enable legacy XR (Abilita XR legacy): abilita VR per il progetto.
> * Set Single Pass Instanced rendering path (Imposta il percorso di rendering con istanze a singolo passaggio): migliora le prestazioni grafiche eseguendo la pipeline di rendering per entrambi gli occhi nella stessa chiamata di disegno. Per altre informazioni su questo argomento, è possibile fare riferimento alla sezione sul [rendering con istanze a singolo passaggio](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html#single-pass-instanced-rendering) della documentazione di MRTK relativa alle [prestazioni](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html).
> * Set default Spatial Awareness layer (Imposta livello di consapevolezza spaziale predefinito): crea un livello di Unity denominato Spatial Awareness e configura MRTK per l'uso di questo livello per la mesh di consapevolezza spaziale. Per altre informazioni sui livelli di Unity, vedere la documentazione relativa alla <a href="https://docs.unity3d.com/Manual/Layers.html" target="_blank">personalizzazione dell'area di lavoro</a> di Unity.

3. Sulla barra dei menu scegliere **Edit** (Modifica) > **Project Settings** (Impostazioni progetto).

4. Nella finestra **Project Settings** (Impostazioni progetto) selezionare **Player** (Lettore), fare clic sull'elenco a discesa **XR Settings** (Impostazioni XR) e quindi selezionare la casella accanto a **Virtual Reality Supported** (Realtà virtuale supportata):

![Finestra XR Settings(Impostazioni XR) di Unity in cui è visualizzata la casella Virtual Reality Supported (Realtà virtuale supportata)](images/mr-learning-base/base-02-section5-step2-2.png)

Viene importato Windows Mixed Reality SDK:

![Finestra XR Settings(Impostazioni XR) di Unity in cui è visualizzata la sezione Virtual Reality SDKs (Virtual Reality SDK)](images/mr-learning-base/mixed-reality-sdk.png)

Al termine dell'importazione di Windows Mixed Reality SDK, viene visualizzata di nuovo la finestra **MRTK Project Configurator** (Configuratore del progetto MRTK). In caso contrario, selezionare **Mixed Reality Toolkit** > **Utilities** (Utilità) > **Configure Unity Project** (Configura il progetto Unity) per aprirla.

5. Nella finestra **MRTK Project Configurator** (Configuratore del progetto MRTK) fare clic sull'elenco a discesa **Audio spatializer** (Spazializzatore audio) e quindi selezionare **MS HRTF Spatializer** (Spazializzatore MS HRTF).

![Finestra Project Settings (Impostazioni progetto) in cui sono visualizzate le opzioni Audio spatializer (Spazializzatore audio)](images/mr-learning-base/base-02-section5-step2-3.png)

6. Fare clic sul pulsante **Applica**. La finestra **MRTK Project Configurator** (Configuratore del progetto MRTK) viene chiusa.

    > [!TIP]
    > L'impostazione della proprietà Audio spatializer (Spazializzatore audio) è facoltativa, ma può migliorare l'esperienza audio nel progetto. Se si imposta questa proprietà su MS HRTF Spatializer, questo plug-in di spazializzatore verrà usato quando la proprietà AudioSource.spatialize di Unity è abilitata. Per altre informazioni su questo argomento, è possibile fare riferimento alle esercitazioni sull'audio spaziale.

7. Nella finestra **Project Settings** (Impostazioni progetto) fare clic sull'elenco a discesa **Depth Format** (Formato profondità) e quindi selezionare **16-bit depth** (Profondità a 16 bit):

    :::image type="content" source="images/mr-learning-base/base-02-section5-step2-4.png" alt-text="Area XR Settings (Impostazioni XR) di Unity in cui è selezionata l'opzione 16-bit depth (Profondità a 16 bit).":::

    > [!TIP]
    > La riduzione del formato profondità a 16 bit è facoltativa, ma consente di migliorare le prestazioni grafiche nel progetto. Per altre informazioni su questo argomento, è possibile fare riferimento alla sezione sulla [condivisione del buffer di intensità (HoloLens)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html#depth-buffer-sharing-hololens) della documentazione di MRTK relativa alle [prestazioni](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html).

8. Fare clic sull'elenco a discesa **Publishing Settings** (Impostazioni di pubblicazione) e quindi nella casella **Package name** (Nome pacchetto) immettere un nome appropriato, ad esempio "MRTK-Tutorials-Getting-Started".

    :::image type="content" source="images/mr-learning-base/base-02-section5-step2-5.png" alt-text="Finestra Publishing Settings (Impostazioni di pubblicazione) di Unity con il nome pacchetto configurato.":::

    **Nome pacchetto e nome prodotto**

    - Il valore di 'Package name' (Nome del pacchetto) è l'identificatore univoco dell'app. Creare questo identificatore prima di distribuire l'app per evitare di sovrascrivere app installate in precedenza.
    - Il valore di 'Product Name' (Nome del prodotto) è il nome visualizzato nel menu di avvio di HoloLens. Per semplificare l'individuazione dell'app durante lo sviluppo, è possibile anteporre un carattere di sottolineatura al nome in modo che compaia all'inizio dell'elenco.

    :::image type="content" source="images/mr-learning-base/product-name.png" alt-text="Finestra Project Settings (Impostazioni progetto) di Unity con il nome prodotto configurato.":::

9. Chiudere la finestra **Project Settings** (Impostazioni progetto).

## <a name="creating-and-configuring-the-scene"></a>Creazione e configurazione della scena

1. Sulla barra dei menu scegliere **File** > **New Scene** (Nuova scena).
2. Per aggiungere MRTK alla scena, sulla barra dei menu scegliere **Mixed Reality Toolkit** > **Add to Scene and Configure** (Aggiungi alla scena e configura).

    :::image type="content" source="images/mr-learning-base/base-02-section6-step1-2.png" alt-text="Percorso del menu Add to Scene and Configure (Aggiungi alla scena e configura) di Unity.":::

3. Nella finestra **Hierarchy** (Gerarchia) assicurarsi che sia selezionato l'oggetto **MixedRealityToolkit**.

    :::image type="content" source="images/mr-learning-base/select-mixed-reality-toolkit.png" alt-text="Assicurarsi che l'oggetto MixedRealityTookit sia selezionato.":::

4. Nella sezione **MixedRealityToolkit** della finestra **Inspector** (Controllo) verificare che il profilo di configurazione sia impostato su **DefaultMixedRealityToolkitConfigurationProfile**:

    :::image type="content" source="images/mr-learning-base/base-02-section6-step1-3.png" alt-text="Componente MixedRealityToolkit di Unity con DefaultMixedRealityTookitConfigurationProfile selezionato.":::

    > [!IMPORTANT]
    > Durante le attività di sviluppo per HoloLens viene usato in genere DefaultHoloLens2ConfigurationProfile. Tuttavia, per questa esercitazione si userà DefaultMixedRealityToolkitConfigurationProfile. Nell'esercitazione successiva, riguardante la [configurazione dei profili MRTK](mr-learning-base-03.md), si passerà a DefaultHoloLens2ConfigurationProfile.

5. Sulla barra dei menu scegliere **File** > **Save As** (Salva con nome).
6. Nella finestra di dialogo **Save scene** (Salva scena) passare alla cartella **Scenes** (Scene) del progetto. Nella casella **File name** (Nome file) assegnare alla scena un nome appropriato, ad esempio "\_GettingStarted\_", e quindi fare clic sul pulsante **Save** (Salva).

    :::image type="content" source="images/mr-learning-base/base-02-section6-step1-5.png" alt-text="Finestra del prompt di salvataggio della scena di Unity.":::

## <a name="building-and-deploying-to-your-hololens-2"></a>Compilazione e distribuzione in HoloLens 2

> Prima di compilare sul dispositivo, verificare quanto segue:
- Il dispositivo è in modalità sviluppatore.
- Il dispositivo è associato al computer di sviluppo. In caso contrario, verrà visualizzata la finestra di dialogo seguente in Visual Studio durante il processo di compilazione:

![Immissione del PIN per l'associazione dei dispositivi](images/mr-learning-base/pin-request.png)

 Per altre informazioni su entrambi questi passaggi, vedere [Uso di Visual Studio per la distribuzione e il debug](../../platform-capabilities-and-apis/using-visual-studio.md).

1. Sulla barra dei menu scegliere **File** > **Build Settings** (Impostazioni di compilazione).
2. Nella finestra **Build Settings** (Impostazioni di compilazione) fare clic sul pulsante **Add Open Scenes** (Aggiungi scene aperte) per aggiungere la scena corrente all'elenco **Scenes In Build** (Scene in compilazione).

![Aggiungere la scena corrente all'elenco "Scenes in Build" (Scene in compilazione)](images/mr-learning-base/base-02-section7-step1-1.png)

3. Fare clic sul pulsante **Build**.

    :::image type="content" source="images/mr-learning-base/build-button.png" alt-text="Fare clic sul pulsante Build.":::

4. Nella finestra di dialogo **Build Universal Windows Platform** (Compila piattaforma UWP) scegliere un percorso appropriato per memorizzare la build, ad esempio è possibile creare una cartella "Build" nella cartella "Esercitazioni di MRTK". Creare una nuova cartella e assegnarle un nome appropriato, ad esempio "GettingStarted", selezionare la cartella e quindi fare clic sul pulsante **Select Folder** (Seleziona cartella) per avviare il processo di compilazione.

    :::image type="content" source="images/mr-learning-base/base-02-section7-step1-2.png" alt-text="Finestra di compilazione di Unity in cui è visualizzata la cartella della build.":::

    Viene visualizzata una barra di stato che consente di restare aggiornati sullo stato di avanzamento della compilazione.

    :::image type="content" source="images/mr-learning-base/base-02-section7-step1-3.png" alt-text="Processo di compilazione di Unity in corso.":::

    > [!TIP]
    > Puoi anche eseguire la distribuzione nell'[emulatore HoloLens](../../platform-capabilities-and-apis/using-the-hololens-emulator.md) o creare un [Pacchetto applicazione](https://docs.microsoft.com/windows/uwp/packaging/packaging-uwp-apps) per il sideload.

5. Al termine del processo di compilazione, in Esplora file passare al percorso in cui è stata memorizzata la build e quindi fare doppio clic sul file della soluzione per aprirlo in Visual Studio:

    :::image type="content" source="images/mr-learning-base/base-02-section8-step1-1.png" alt-text="Esplora risorse in cui è selezionato il file appena creato per la soluzione di Visual Studio.":::

    > [!NOTE]
    > Se Visual Studio chiede di installare nuovi componenti, dedica qualche minuto a verificare di disporre di tutti i componenti indispensabili come specificato nella documentazione **[Installare gli strumenti](../../install-the-tools.md)** .

6. Configurare Visual Studio per HoloLens selezionando la configurazione **Master** o **Release**, l'architettura **ARM64** e **Dispositivo** come destinazione.

    > [!TIP]
    > Se esegui la distribuzione in HoloLens (1a generazione), seleziona l'architettura **x86**.

    :::image type="content" source="images/mr-learning-base/base-02-section8-step1-2.png" alt-text="Visual Studio configurato per la distribuzione in HoloLens 2.":::

    > [!NOTE]
    > Per HoloLens, in genere la compilazione viene eseguita per l'architettura ARM. Esiste tuttavia un <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank"><strong>problema noto</strong></a> in Unity 2019.3 che causa errori quando viene selezionata l'architettura di compilazione ARM in Visual Studio. La soluzione consigliata consiste nel compilare per ARM64. Se questa opzione non è applicabile, passa a **Modifica > Impostazioni progetto > Player (Lettore) > Altre impostazioni** e disabilita **Graphics Jobs** (Processi grafici).

    > [!NOTE]
    > Se non viene visualizzata l'opzione Dispositivo come destinazione, potresti dover modificare il progetto di avvio per la soluzione di Visual Studio passando dal progetto IL2CPP al progetto UWP. A tale scopo, in Esplora soluzioni fare clic con il pulsante destro del mouse su NomeProgetto (Windows universale) e quindi scegliere **Imposta come progetto di avvio**.

7. Connettere HoloLens al computer e quindi eseguire una di queste operazioni:
- Per compilare l'app, distribuirla in HoloLens e avviarla automaticamente senza il debugger di Visual Studio associato, pertanto sulla barra dei menu scegliere **Debug** > **Avvia senza eseguire il debug**.

    :::image type="content" source="images/mr-learning-base/base-02-section8-step1-3.png" alt-text="Percorso del menu di Visual Studio per l'avvio senza il debug.":::

- Per compilare e distribuire l'app in HoloLens senza però avviarla automaticamente, sulla barra dei menu scegliere **Compila > Distribuisci soluzione**.

    > [!NOTE]
    >Potrebbe essere visibile nell'app il profiler di diagnostica, che può essere attivato o disattivato tramite il comando vocale **Toggle Diagnostics** (Attiva/Disattiva diagnostica). È consigliabile mantenere visibile il profiler la maggior parte del tempo durante lo sviluppo per verificare quando le modifiche apportate all'app possono produrre effetti negativi sulle prestazioni. Le app HoloLens ad esempio devono [essere eseguite costantemente a 60 FPS](../../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md).

## <a name="congratulations"></a>Lezione completata

A questo punto hai distribuito la tua prima app per HoloLens. Esplorando, noterai una mesh di mapping spaziale che copre le superfici percepite da HoloLens. Dovresti anche vedere indicatori sulle mani e sulle dita per il tracciamento delle mani e un contatore della frequenza dei fotogrammi per tenere sotto controllo le prestazioni dell'app. Queste funzionalità sono solo alcune delle parti fondamentali incluse in MRTK. Nelle esercitazioni successive aggiungerai contenuto alla scena per esplorare le funzionalità di HoloLens e MRTK.

> [!div class="nextstepaction"]
> [Esercitazione successiva: 3. Configurazione dei profili di MRTK](mr-learning-base-03.md)

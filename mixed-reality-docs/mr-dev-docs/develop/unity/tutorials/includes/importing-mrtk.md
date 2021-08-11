---
ms.openlocfilehash: 7fd590713322c296cbbb14e133b1085aa27bb0197b70d1feca1ecb59ed61a3c7
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115201721"
---
# <a name="unity-2020--openxr"></a>[Unity 2020 + OpenXR](#tab/openxr)

Dopo **aver aperto MixedRealityFeatureTool,** fare clic su **Start** per iniziare a usare Mixed Reality Feature Tool.

<img src="../images/mr-learning-base/base-02-section4-step1-2.png" width="650px" alt="MixedRealityFeatureTool main screen">

Il primo passaggio consiste nel puntare lo strumento di funzionalità  di realtà mista al percorso **di Project** usando il pulsante con i puntini di sospensione, fare clic sul pulsante con i puntini di sospensione tre puntini accanto al percorso Project e passare alla cartella del progetto in Esplora risorse, ad esempio _D:\MixedRealityLearning\MRTK Tutorials_.

<img src="../images/mr-learning-base/base-02-section4-step1-3.png" width="650px" alt="Adding Unity Path for MixedRealityFeatureTool">

Dopo aver individuato la cartella del progetto, fare clic sul pulsante Apri per tornare a Strumento di funzionalità di realtà mista. Fare quindi clic su **Individua funzionalità**.

> [!NOTE]
> La finestra di dialogo visualizzata quando si esplora la cartella del progetto Unity contiene '_' come nome file. Per consentire la selezione della cartella, deve essere presente un valore per il nome file.

> [!Important]
> Lo strumento funzionalità realtà mista esegue la convalida per assicurarsi che sia stato indirizzato a una cartella del progetto Unity. La cartella deve contenere asset, pacchetti e Project Impostazioni cartelle.

Le funzionalità sono raggruppate per categoria per semplificare la ricerca, fare clic sull'elenco Toolkit di Realtà  mista per trovare i pacchetti relativi al Toolkit di realtà mista e fare clic sull'elenco a discesa Supporto piattaforma per trovare i pacchetti relativi **a** varie piattaforme di supporto.

<img src="../images/mr-learning-base/base-02-section4-step1-4-openxr.png" width="650px" alt="MixedRealityFeatureTool Discover Features">

Controllare **Mixed Reality Toolkit Foundation** e fare clic sull'elenco a discesa accanto a esso per selezionare **MRTK 2.7.2,** controllare anche **Mixed Reality OpenXR Plugin 1.0.0** e fare clic sull'elenco a discesa accanto a esso per selezionare la versione più recente disponibile, quindi fare clic sul pulsante Scarica funzionalità per scaricare i pacchetti selezionati. 

<img src="../images/mr-learning-base/base-02-section4-step1-5-openxr.png" width="650px" alt="MixedRealityFeatureTool Open MixedReality">

Fare quindi **clic sul** pulsante Convalida per convalidare il  pacchetto selezionato. Verrà visualizzata una finestra popup con il messaggio Nessun problema di convalida rilevato fare clic su **OK** per chiudere il popup e fare clic sul **pulsante** Importa.

<img src="../images/mr-learning-base/base-02-section4-step1-6-openxr.png" width="650px" alt="MixedRealityFeatureTool Select required package">


Fare clic **sul pulsante** Approva per aggiungere **il** Toolkit realtà mista al progetto.

<img src="../images/mr-learning-base/base-02-section4-step1-7-openxr.png" width="650px" alt="MixedRealityFeatureTool Validate package">

## <a name="configuring-the-unity-project"></a>Configurazione del progetto Unity

Dopo che Unity ha terminato l'importazione del pacchetto dalla sezione precedente, viene visualizzato un messaggio di avviso per riavviare l'editor unity per abilitare i back-end per il nuovo sistema plug-in, fare clic su **Sì**

<img src="../images/mr-learning-base/base-02-section5-step1-1-openxr.png" width="650px" alt="Unity Restart Option">

Dopo il riavvio di Unity, Project verrà visualizzata la finestra Configurator. In caso contrario, è possibile aprirlo manualmente in **Mixed Reality**  >  **Toolkit**  >  **Utilities**  >  **Configure Project for MRTK**:

![Aprire la finestra del configuratore di progetto MRTK](../images/mr-learning-base/base-02-section5-step1-2-openxr.png)

Fare clic **sul plug-in Unity OpenXR** per abilitare la gestione dei plug-in XR e aggiungere i pacchetti necessari al progetto.

![Aggiungere il plug-in OpenXR di Unity ](../images/mr-learning-base/base-02-section5-step1-3-openxr.png)

In questo modo verranno importati i pacchetti unity necessari per XR Plugin Management, dopo aver fatto clic su **Show XR Plug-In Management Impostazioni** in MRTK project Configurator (Mostra XR Plug-In Management Impostazioni nel configuratore di progetto MRTK).

![Mostra gestione Plug-In XR Impostazioni ](../images/mr-learning-base/base-02-section5-step1-4-openxr.png)

Verrà visualizzata **Project Impostazioni finestra**. Nella finestra Project Impostazioni in **Gestione plug-in XR** assicurarsi di essere in Impostazioni della piattaforma Windows universale (Windows logo). Assicurarsi anche che **l'opzione Inizializza XR all'avvio** sia selezionata, quindi fare clic sulla casella di controllo **OpenXR** e selezionare **Microsoft HoloLens set** di funzionalità per abilitarle.

![Abilitare Open XR](../images/mr-learning-base/base-02-section5-step1-5-openxr.png)

Dopo aver selezionato la casella di controllo OpenXR, MRTK Project Configurator visualizza il messaggio aggiornato con il pulsante **Impostazioni** testo. Fare **clic sul Impostazioni** applica. 

![Project Impostazioni finestra 1](../images/mr-learning-base/base-02-section5-step1-6-openxr.png)

Quando si fa clic su Applica Impostazioni, è possibile che venga visualizzato questo messaggio di errore nella console. È possibile procedere se si tratta dell'unico errore o non si verifica alcun errore.

![Messaggio di errore della comunicazione remota OpenXR](../images/mr-learning-base/base-02-section5-step1-6-openxr-Error.png)

Per convalidare la configurazione di OpenXR, fare **clic su OpenXR** **in Gestione plug-in XR** e controllare questi elementi:
* Modalità di invio della profondità: **profondità a 16 bit**
* Profili di interazione: **Microsoft Hand Interaction Profile**

![Project Impostazioni finestra 2](../images/mr-learning-base/base-02-section5-step1-7-openxr.png)

> [!TIP]
> La riduzione del formato profondità a 16 bit è facoltativa, ma consente di migliorare le prestazioni grafiche nel progetto. Per altre informazioni su questo argomento, è possibile fare riferimento alla sezione sulla <a href="/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering" target="_blank">condivisione del buffer di intensità (HoloLens)</a> della documentazione di MRTK relativa alle prestazioni.


Nella finestra **MRTK Project Configurator fare** clic su **Avanti,** quindi fare clic sul **pulsante** Applica per applicare le impostazioni. Se è stato chiuso, è possibile aprirlo manualmente in **Realtà mista**  >  **Toolkit**  >  **Utilità**  >  **Configurare Project per MRTK**)

![Project Impostazioni finestra 3](../images/mr-learning-base/base-02-section5-step1-8-openxr.png)

![Project Impostazioni finestra 4](../images/mr-learning-base/base-02-section5-step1-9-openxr.png)

Dopo aver fatto clic su Applica, Unity tenterà di riavviare per applicare il sistema di input, fare clic su **Applica** per riavviare l'editor di Unity

### <a name="configure-additional-project-settings"></a>Configurare impostazioni di progetto aggiuntive

Nel menu di Unity selezionare **Edit** > **Project Settings** (Modifica > Impostazioni progetto) per aprire la finestra Project Settings (Impostazioni progetto).

Nella finestra Project Settings (Impostazioni progetto) seleziona **Player (Lettore)**  > **Publishing Settings** (Impostazioni di pubblicazione) e quindi nel campo **Package name** (Nome del pacchetto) immetti un nome appropriato, ad esempio _MRTKTutorials-GettingStarted_:

![Unity Publishing Impostazioni. Nome pacchetto configurato](../images/mr-learning-base/base-02-section5-step2-2.png)

> [!NOTE]
> Il valore di 'Package name' (Nome del pacchetto) è l'identificatore univoco dell'app. Modifica questo identificatore prima di distribuire l'app per evitare di sovrascrivere app installate in precedenza.

> [!TIP]
> Il valore di 'Product Name' (Nome del prodotto) è il nome visualizzato nel menu di avvio di HoloLens. Per semplificare l'individuazione dell'app durante lo sviluppo, anteponi un carattere di sottolineatura al nome in modo che compaia all'inizio dell'elenco.

# <a name="unity-20192020--windows-xr-plugin"></a>[Unity 2019/2020 + Windows plug-in XR](#tab/winxr)

Dopo **aver aperto MixedRealityFeatureTool,** fare clic su **Start** per iniziare a usare Mixed Reality Feature Tool.

<img src="../images/mr-learning-base/base-02-section4-step1-2.png" width="650px" alt="MixedRealityFeatureTool main screen">

Il primo passaggio consiste nel puntare lo strumento di funzionalità  di realtà mista al percorso **di Project** usando il pulsante con i puntini di sospensione, fare clic sul pulsante con i puntini di sospensione tre puntini accanto al percorso Project e passare alla cartella del progetto in Esplora risorse, ad esempio _D:\MixedRealityLearning\MRTK Tutorials_.

<img src="../images/mr-learning-base/base-02-section4-step1-3.png" width="650px" alt="Adding Unity Path for MixedRealityFeatureTool">


Dopo aver individuato la cartella del progetto, fare clic sul pulsante Apri per tornare a Strumento di funzionalità di realtà mista. Fare quindi clic su **Individua funzionalità**.

> [!NOTE]
> La finestra di dialogo visualizzata quando si esplora la cartella del progetto Unity contiene '_' come nome file. Per consentire la selezione della cartella, deve essere presente un valore per il nome file.

> [!Important]
> Lo strumento funzionalità realtà mista esegue la convalida per assicurarsi che sia stato indirizzato a una cartella del progetto Unity. La cartella deve contenere asset, pacchetti e Project Impostazioni cartelle.

Le funzionalità sono raggruppate in base alla categoria per semplificare l'individuazione, fare clic **sull'elenco Toolkit** di Realtà mista per trovare i pacchetti relativi all'Toolkit.

<img src="../images/mr-learning-base/base-02-section4-step1-4.PNG" width="650px" alt="MixedRealityFeatureTool Discover Features">

Selezionare la casella **mixed reality Toolkit Foundation** e fare clic sull'elenco a discesa accanto a esso per selezionare  **MRTK 2.7.0,** quindi fare clic sul pulsante Ottieni funzionalità per scaricare i pacchetti selezionati.

<img src="../images/mr-learning-base/base-02-section4-step1-5.PNG" width="650px" alt="MixedRealityFeatureTool Open Mixed Reality">

Fare quindi **clic sul** pulsante Convalida per convalidare il  pacchetto selezionato. Verrà visualizzata una finestra popup con il messaggio Nessun problema di convalida rilevato fare clic su **OK** per chiudere il popup e fare clic sul **pulsante** Importa.

<img src="../images/mr-learning-base/base-02-section4-step1-6.PNG" width="650px" alt="MixedRealityFeatureTool Select required package">


Fare clic **sul pulsante** Approva per aggiungere **il** Toolkit realtà mista al progetto.

<img src="../images/mr-learning-base/base-02-section4-step1-7.PNG" width="650px" alt="MixedRealityFeatureTool Validate package">


## <a name="configuring-the-unity-project"></a>Configurazione del progetto Unity

Al termine dell'importazione del pacchetto dalla sezione precedente, viene visualizzata la finestra MRTK Project Configurator (Configuratore del progetto MRTK). In caso contrario, è possibile aprirlo manualmente in **Mixed Reality**  >  **Toolkit**  >  **Utilities**  >  **Configure Project for MRTK**:

![apertura dello strumento di configurazione MRTK](../images/mr-learning-base/base-02-section5-step1-1xrsdk.PNG)

Fare clic **su Plug-in Unity (non OpenXR)** incorporato per abilitare la gestione dei plug-in XR e aggiungere i pacchetti necessari al progetto.

![ Strumento di configurazione MRTK](../images/mr-learning-base/base-02-section5-step1-2xrsdk.PNG)

> [!NOTE]
> Lo screenshot precedente è di Unity 2020, se si usa Unity 2019 selezionare **XR SDK/XR Management**

Verranno importati i pacchetti unity necessari per XR Plugin Management, dopo aver fatto clic su **Show Impostazioni** in MRTK project Configurator (Mostra Impostazioni nel configuratore di progetto MRTK).

![Finestra delle impostazioni del lettore](../images/mr-learning-base/base-02-section5-step1-3xrsdk.PNG)

Verrà visualizzata Project Impostazioni finestra **,** nella finestra Project Impostazioni in **Gestione plug-in XR** Assicurarsi di essere presenti nelle impostazioni della piattaforma Universal Windows Anche Assicurarsi che l'opzione Inizializza **XR** all'avvio sia selezionata e selezionare Windows Mixed Reality **casella** di controllo.

![Finestra delle impostazioni del lettore Abilita Realtà mista-xrsdk](../images/mr-learning-base/base-02-section5-step1-4xrsdk.PNG)

Al termine dell'importazione di Windows Mixed Reality SDK, dovrebbe visualizzarsi di nuovo la finestra MRTK Project Configurator (Configuratore del progetto MRTK). In caso contrario, usa il menu di Unity per aprirla.

Nella finestra MRTK Project Configurator fare  clic su Avanti, quindi usare l'elenco a discesa Spazializzatore audio per selezionare lo spazializzatore **MS HRTF,** quindi fare clic sul pulsante Applica per applicare l'impostazione: 

![Configuratore di progetto MRTK-xrsdk](../images/mr-learning-base/base-02-section5-step1-5xrsdk.PNG)

> [!TIP]
> L'applicazione delle impostazioni predefinite di MRTK è facoltativa ma fortemente consigliata, poiché consente di configurare alcune impostazioni consigliate di Unity:

> * Set Single Pass Instanced rendering path (Imposta il percorso di rendering con istanze a singolo passaggio): migliora le prestazioni grafiche eseguendo la pipeline di rendering per entrambi gli occhi nella stessa chiamata di disegno. Per altre informazioni su questo argomento, è possibile fare riferimento alla sezione sul [rendering con istanze a singolo passaggio](/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering) della documentazione di MRTK relativa alle [prestazioni](/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering).
> * Set default Spatial Awareness layer (Imposta livello di consapevolezza spaziale predefinito): crea un livello di Unity denominato Spatial Awareness e configura MRTK per l'uso di questo livello per la mesh di consapevolezza spaziale. Per altre informazioni sui livelli di Unity, vedere la documentazione relativa alla <a href="https://docs.unity3d.com/Manual/Layers.html" target="_blank">personalizzazione dell'area di lavoro</a> di Unity.

> [!TIP]
> L'impostazione della proprietà Audio spatializer (Spazializzatore audio) è facoltativa, ma può migliorare l'esperienza audio nel progetto. Se si imposta questa proprietà su MS HRTF Spatializer, questo plug-in di spazializzatore verrà usato quando la proprietà AudioSource.spatialize di Unity è abilitata. Per altre informazioni su questo argomento, è possibile fare riferimento alle esercitazioni  <a href="//windows/mixed-reality/develop/unity/tutorials/unity-spatial-audio-ch1" target="_blank"> sull'audio spaziale</a>.

Fare clic su  **Avanti** e quindi fare clic su Fine nella finestra MRTK Project Configurator per completare la configurazione del progetto Unity per XRSDK.

### <a name="configure-additional-project-settings"></a>Configurare impostazioni di progetto aggiuntive

Dal menu di Unity scegli **Edit** (Modifica) > **Project Settings** (Impostazioni del progetto) per visualizzare la finestra corrispondente:

Nella finestra Project Impostazioni selezionare **Gestione plug-in XR** Windows Mixed Reality Runtime Impostazioni e quindi usare l'elenco a discesa Formato buffer di profondità per selezionare la profondità  >  **a**  >   **16 bit:** 

![Unity Abilita 16 profondità](../images/mr-learning-base/base-02-section5-step2-1xrsdk.PNG)

> [!TIP]
> La riduzione del formato di profondità a 16 bit è facoltativa, ma consente di migliorare le prestazioni grafiche nel progetto. Per altre informazioni su questo argomento, è possibile fare riferimento alla sezione sulla <a href="/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering" target="_blank">condivisione del buffer di intensità (HoloLens)</a> della documentazione di MRTK relativa alle prestazioni.

Nella finestra Project Settings (Impostazioni progetto) seleziona **Player (Lettore)**  > **Publishing Settings** (Impostazioni di pubblicazione) e quindi nel campo **Package name** (Nome del pacchetto) immetti un nome appropriato, ad esempio _MRTKTutorials-GettingStarted_:

![Unity Publishing Impostazioni. Nome pacchetto configurato](../images/mr-learning-base/base-02-section5-step2-2.png)

> [!NOTE]
> Il valore di 'Package name' (Nome del pacchetto) è l'identificatore univoco dell'app. Modifica questo identificatore prima di distribuire l'app per evitare di sovrascrivere app installate in precedenza.

> [!TIP]
> Il valore di 'Product Name' (Nome del prodotto) è il nome visualizzato nel menu di avvio di HoloLens. Per semplificare l'individuazione dell'app durante lo sviluppo, anteponi un carattere di sottolineatura al nome in modo che compaia all'inizio dell'elenco.

# <a name="legacy-wsa"></a>[Legacy WSA](#tab/wsa)

Dopo **aver aperto MixedRealityFeatureTool,** fare clic su **Start** per iniziare a usare Mixed Reality Feature Tool.

<img src="../images/mr-learning-base/base-02-section4-step1-2.png" width="650px" alt="MixedRealityFeatureTool main screen">

Il primo passaggio consiste nel puntare lo strumento di funzionalità  di realtà mista al percorso **Project** usando il pulsante con i puntini di sospensione, fare clic sul pulsante con i puntini di sospensione tre puntini accanto al percorso Project e passare alla cartella del progetto in Esplora risorse, ad esempio _D:\MixedRealityLearning\MRTK Tutorials_.

<img src="../images/mr-learning-base/base-02-section4-step1-3.png" width="650px" alt="Adding Unity Path for MixedRealityFeatureTool">

Dopo aver individuato la cartella del progetto, fare clic sul pulsante Apri per tornare a Strumento di funzionalità di realtà mista. Fare quindi clic su **Individua funzionalità**.

> [!NOTE]
> La finestra di dialogo visualizzata quando si esplora la cartella del progetto Unity contiene '_' come nome file. Per consentire la selezione della cartella, deve essere presente un valore per il nome file.

> [!Important]
> Lo strumento funzionalità realtà mista esegue la convalida per assicurarsi che sia stato indirizzato a una cartella del progetto Unity. La cartella deve contenere asset, pacchetti e Project Impostazioni cartelle.

Le funzionalità sono raggruppate in base alla categoria per semplificare l'individuazione, fare clic **sull'elenco Toolkit** di Realtà mista per trovare i pacchetti relativi all'Toolkit.

<img src="../images/mr-learning-base/base-02-section4-step1-4.PNG" width="650px" alt="MixedRealityFeatureTool Discover Features">

Selezionare **Mixed Reality Toolkit Foundation** e fare clic sull'elenco a discesa accanto a esso per selezionare **MRTK 2.7.0,** quindi fare clic sul pulsante Get **features** (Ottieni funzionalità) per scaricare i pacchetti selezionati.

<img src="../images/mr-learning-base/base-02-section4-step1-5.PNG" width="650px" alt="MixedRealityFeatureTool Open Mixed Reality">

Fare quindi clic **sul** pulsante Convalida per convalidare il pacchetto selezionato. Verrà visualizzata una finestra popup con il messaggio Nessun problema di convalida rilevato **fare** clic su **OK** per chiudere il popup e fare clic sul **pulsante** Importa.

<img src="../images/mr-learning-base/base-02-section4-step1-6.PNG" width="650px" alt="MixedRealityFeatureTool Select required package">

Fare clic **sul pulsante** Approva per aggiungere **il** Toolkit realtà mista al progetto.

<img src="../images/mr-learning-base/base-02-section4-step1-7.PNG" width="650px" alt="MixedRealityFeatureTool Validate package">


## <a name="configuring-the-unity-project"></a>Configurazione del progetto Unity

Al termine dell'importazione del pacchetto dalla sezione precedente, viene visualizzata la finestra MRTK Project Configurator (Configuratore del progetto MRTK). In caso contrario, è possibile aprirlo manualmente in **Mixed Reality**  >  **Toolkit**  >  **Utilities**  >  **Configure Project for MRTK**:

![Percorso del menu Configure Unity Project di Unity](../images/mr-learning-base/base-02-section5-step1-1.png)

Fare clic **su Legacy XR (XR** legacy) per abilitare Legacy XR e aggiungere i pacchetti necessari al progetto.

![s](../images/mr-learning-base/base-02-section5-step1-2.png)

Fare clic sul pulsante Avanti per abilitare le impostazioni della pipeline XR per Legacy XR.

![Finestra di configurazione di Unity MRTK](../images/mr-learning-base/base-02-section5-step1-3.PNG)

Nella finestra MRTK Project Configurator assicurarsi che tutte le opzioni  siano selezionate e usare anche l'elenco a  discesa Spazializzatore audio per selezionare lo spazializzatore **MS HRTF,** quindi fare clic sul pulsante Applica per applicare l'impostazione:

![Finestra di configurazione di MRTK](../images/mr-learning-base/base-02-section5-step1-4.PNG)

> [!TIP]
> L'applicazione delle impostazioni predefinite di MRTK è facoltativa ma fortemente consigliata, poiché consente di configurare alcune impostazioni consigliate di Unity:

> * Set Single Pass Instanced rendering path (Imposta il percorso di rendering con istanze a singolo passaggio): migliora le prestazioni grafiche eseguendo la pipeline di rendering per entrambi gli occhi nella stessa chiamata di disegno. Per altre informazioni su questo argomento, è possibile fare riferimento alla sezione sul [rendering con istanze a singolo passaggio](/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering) della documentazione di MRTK relativa alle [prestazioni](/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering).
> * Set default Spatial Awareness layer (Imposta livello di consapevolezza spaziale predefinito): crea un livello di Unity denominato Spatial Awareness e configura MRTK per l'uso di questo livello per la mesh di consapevolezza spaziale. Per altre informazioni sui livelli di Unity, vedere la documentazione relativa alla <a href="https://docs.unity3d.com/Manual/Layers.html" target="_blank">personalizzazione dell'area di lavoro</a> di Unity.

> [!TIP]
> L'impostazione della proprietà Audio spatializer (Spazializzatore audio) è facoltativa, ma può migliorare l'esperienza audio nel progetto. Se si imposta questa proprietà su MS HRTF Spatializer, questo plug-in di spazializzatore verrà usato quando la proprietà AudioSource.spatialize di Unity è abilitata. Per altre informazioni su questo argomento, è possibile fare riferimento alle esercitazioni  <a href="//windows/mixed-reality/develop/unity/tutorials/unity-spatial-audio-ch1" target="_blank"> sull'audio spaziale</a>.

Fare clic **su Avanti** e quindi **fare** clic sul pulsante Fine nella finestra Project Configurator di MRTK per completare la configurazione del progetto Unity per Legacy XR.

### <a name="configure-additional-project-settings"></a>Configurare impostazioni di progetto aggiuntive

Dal menu di Unity scegli **Edit** (Modifica) > **Project Settings** (Impostazioni del progetto) per visualizzare la finestra corrispondente:

Nella finestra Project Settings (Impostazioni progetto) seleziona **Player (Lettore)**  > **XR Settings** (Impostazioni XR) e quindi usa l'elenco a discesa **Depth Format** (Formato profondità) per selezionare **16-bit depth** (Profondità a 16 bit):

![Unity Abilita 16 profondità](../images/mr-learning-base/base-02-section5-step2-1.png)

> [!TIP]
> La riduzione del formato di profondità a 16 bit è facoltativa, ma consente di migliorare le prestazioni grafiche nel progetto. Per altre informazioni su questo argomento, è possibile fare riferimento alla sezione sulla <a href="/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering" target="_blank">condivisione del buffer di intensità (HoloLens)</a> della documentazione di MRTK relativa alle prestazioni.

Nella finestra Project Settings (Impostazioni progetto) seleziona **Player (Lettore)**  > **Publishing Settings** (Impostazioni di pubblicazione) e quindi nel campo **Package name** (Nome del pacchetto) immetti un nome appropriato, ad esempio _MRTKTutorials-GettingStarted_:

![Unity Publishing Impostazioni. Nome pacchetto configurato](../images/mr-learning-base/base-02-section5-step2-2.png)

> [!NOTE]
> Il valore di 'Package name' (Nome del pacchetto) è l'identificatore univoco dell'app. Modifica questo identificatore prima di distribuire l'app per evitare di sovrascrivere app installate in precedenza.

> [!TIP]
> Il valore di 'Product Name' (Nome del prodotto) è il nome visualizzato nel menu di avvio di HoloLens. Per semplificare l'individuazione dell'app durante lo sviluppo, anteponi un carattere di sottolineatura al nome in modo che compaia all'inizio dell'elenco.

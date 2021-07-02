---
ms.openlocfilehash: 2420e68a0753739111fc2c5eecfbd1da563f52c2
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2021
ms.locfileid: "113175909"
---
# <a name="unity-2020--openxr"></a>[Unity 2020 + OpenXR](#tab/openxr)

Dopo **aver aperto MixedRealityFeatureTool,** fare clic su **Start** per iniziare a usare Mixed Reality Feature Tool.

<img src="../images/mr-learning-base/base-02-section4-step1-2.png" width="650px" alt="MixedRealityFeatureTool main screen">

Il primo passaggio consiste nell'puntare Mixed Reality Feature Tool  al percorso **del Project** usando il pulsante con i puntini di sospensione, fare clic sul pulsante con i tre puntini di sospensione accanto al percorso del Project e passare alla cartella del progetto nello strumento di esplorazione, ad esempio _D:\MixedRealityLearning\MRTK Tutorials._

<img src="../images/mr-learning-base/base-02-section4-step1-3.png" width="650px" alt="Adding Unity Path for MixedRealityFeatureTool">

Dopo aver individuato la cartella del progetto, fai clic sul pulsante Apri per tornare a Mixed Reality Feature Tool (Strumento per le funzionalità di realtà mista). Fare quindi clic **su Individua funzionalità**.

> [!NOTE]
> La finestra di dialogo visualizzata quando si esplora la cartella del progetto Unity contiene "_" come nome del file. Per consentire la selezione della cartella, è necessario che sia presente un valore per il nome del file.

> [!Important]
> Lo strumento di funzionalità di realtà mista esegue la convalida per assicurarsi che sia stato indirizzato a una cartella di progetto Unity. La cartella deve contenere asset, pacchetti e Project Impostazioni cartelle.

Le funzionalità sono raggruppate per categoria per semplificare l'individuazione, fare clic sull'elenco a discesa mixed reality Toolkit (Realtà **mista)** per trovare i pacchetti relativi a Mixed Reality Toolkit e fare clic sull'elenco a discesa **Platform Support** (Supporto piattaforma) per trovare i pacchetti relativi alle varie piattaforme di supporto.

<img src="../images/mr-learning-base/base-02-section4-step1-4-openxr.png" width="650px" alt="MixedRealityFeatureTool Discover Features">

Controllare **Mixed Reality Toolkit Foundation** e fare clic sull'elenco a discesa accanto per selezionare **MRTK 2.7.2,** controllare anche **Mixed Reality OpenXR Plugin 1.0.0** e fare clic sull'elenco a discesa accanto per selezionare la versione più recente disponibile, quindi fare clic sul pulsante Get **features** (Ottieni funzionalità) per scaricare i pacchetti selezionati.

<img src="../images/mr-learning-base/base-02-section4-step1-5-openxr.png" width="650px" alt="MixedRealityFeatureTool Open MixedReality">

Fare quindi  clic sul pulsante Convalida per convalidare il  pacchetto selezionato. Verrà visualizzata una finestra popup con il messaggio Non sono stati rilevati problemi di convalida fare clic su **OK** per chiudere il popup e fare clic sul **pulsante** Importa.

<img src="../images/mr-learning-base/base-02-section4-step1-6-openxr.png" width="650px" alt="MixedRealityFeatureTool Select required package">


Fare clic **sul pulsante** Approva per aggiungere **la** Toolkit realtà mista al progetto.

<img src="../images/mr-learning-base/base-02-section4-step1-7-openxr.png" width="650px" alt="MixedRealityFeatureTool Validate package">

## <a name="configuring-the-unity-project"></a>Configurazione del progetto Unity

Dopo che Unity ha terminato l'importazione del pacchetto dalla sezione precedente, viene visualizzato un messaggio di avviso per riavviare l'editor di Unity per abilitare i back-end per il nuovo sistema plug-in, fare clic su **Yes (Sì)**

<img src="../images/mr-learning-base/base-02-section5-step1-1-openxr.png" width="650px" alt="Unity Restart Option">

Dopo il riavvio di Unity, Project visualizzata la finestra configuratore MRTK. In caso contrario, è possibile aprirlo manualmente selezionando **Mixed Reality** Toolkit Utilities Configure Project for MRTK (Configura Project  >    >    >  **per MRTK):**

![Aprire la finestra di configurazione del progetto MRTK](../images/mr-learning-base/base-02-section5-step1-2-openxr.png)

Fare clic **su Unity OpenXR Plugin (Plug-in OpenXR Unity)** per abilitare la gestione dei plug-in XR e aggiungere i pacchetti necessari al progetto.

![Aggiungere il plug-in OpenXR di Unity ](../images/mr-learning-base/base-02-section5-step1-3-openxr.png)

Verranno importati i pacchetti Unity necessari per XR Plugin Management. Al termine, fare clic su **Show XR Plug-In Management Impostazioni** in MRTK project Configurator (Mostra XR Plug-In Management Impostazioni configurator del progetto MRTK).

![Visualizzare il Plug-In di gestione Impostazioni XR ](../images/mr-learning-base/base-02-section5-step1-4-openxr.png)

Verrà visualizzata **Project Impostazioni finestra**. Nella finestra Project Impostazioni in **XR Plug-in Management (Gestione plug-in XR)** assicurarsi di essere nelle impostazioni di Universal Windows Platform (Windows logo). Assicurarsi anche che **l'opzione Initialize XR on Startup** (Inizializza XR all'avvio) sia selezionata, quindi fare clic sulla casella di controllo **OpenXR** e Microsoft HoloLens **set di funzionalità** per abilitarle.

![Abilitare Open XR](../images/mr-learning-base/base-02-section5-step1-5-openxr.png)

Dopo aver selezionato la casella di controllo OpenXR, nella finestra MRTK Project Configurator verrà visualizzato un messaggio aggiornato con il pulsante **Impostazioni** applica. Fare **clic sul Impostazioni** applica. 

![Project Impostazioni finestra 1](../images/mr-learning-base/base-02-section5-step1-6-openxr.png)

Quando si fa clic su Impostazioni, è possibile che venga visualizzato questo messaggio di errore nella console. È possibile procedere se si tratta dell'unico errore o se non si verifica alcun errore.

![Messaggio di errore di OpenXR Remoting](../images/mr-learning-base/base-02-section5-step1-6-openxr-Error.png)

Per convalidare la configurazione di OpenXR, fare clic **su OpenXR** **in XR Plug-in Management (Gestione plug-in XR)** e controllare questi elementi:
* Modalità di invio profondità: **profondità a 16 bit**
* Profili di interazione: **Profilo di interazione con la mano Microsoft**

![Project Impostazioni 2](../images/mr-learning-base/base-02-section5-step1-7-openxr.png)

> [!TIP]
> La riduzione del formato profondità a 16 bit è facoltativa, ma consente di migliorare le prestazioni grafiche nel progetto. Per altre informazioni su questo argomento, è possibile fare riferimento alla sezione sulla <a href="/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering" target="_blank">condivisione del buffer di intensità (HoloLens)</a> della documentazione di MRTK relativa alle prestazioni.


Nella finestra **MRTK Project Configurator** fare clic su **Avanti** e quindi sul **pulsante** Applica per applicare le impostazioni. Se è stata chiusa, è possibile aprirla manualmente selezionando **Realtà mista**  >  **Toolkit**  >  **Utilità**  >  **Configurare Project per MRTK**)

![Project Impostazioni Finestra 3](../images/mr-learning-base/base-02-section5-step1-8-openxr.png)

![Project Impostazioni 4](../images/mr-learning-base/base-02-section5-step1-9-openxr.png)

Dopo aver fatto clic su Apply (Applica), Unity tenterà di riavviare per applicare il sistema di input, quindi fare clic su **Apply (Applica)** per riavviare l'editor di Unity

### <a name="configure-additional-project-settings"></a>Configurare impostazioni di progetto aggiuntive

Nel menu di Unity selezionare **Edit** > **Project Settings** (Modifica > Impostazioni progetto) per aprire la finestra Project Settings (Impostazioni progetto).

Nella finestra Project Settings (Impostazioni progetto) seleziona **Player (Lettore)**  > **Publishing Settings** (Impostazioni di pubblicazione) e quindi nel campo **Package name** (Nome del pacchetto) immetti un nome appropriato, ad esempio _MRTKTutorials-GettingStarted_:

![Pubblicazione unity Impostazioni. Nome pacchetto configurato](../images/mr-learning-base/base-02-section5-step2-2.png)

> [!NOTE]
> Il valore di 'Package name' (Nome del pacchetto) è l'identificatore univoco dell'app. Modifica questo identificatore prima di distribuire l'app per evitare di sovrascrivere app installate in precedenza.

> [!TIP]
> Il valore di 'Product Name' (Nome del prodotto) è il nome visualizzato nel menu di avvio di HoloLens. Per semplificare l'individuazione dell'app durante lo sviluppo, anteponi un carattere di sottolineatura al nome in modo che compaia all'inizio dell'elenco.

# <a name="unity-20192020--windows-xr-plugin"></a>[Unity 2019/2020 + Windows plug-in XR](#tab/winxr)

Dopo **aver aperto MixedRealityFeatureTool,** fare clic su **Start** per iniziare a usare Mixed Reality Feature Tool.

<img src="../images/mr-learning-base/base-02-section4-step1-2.png" width="650px" alt="MixedRealityFeatureTool main screen">

Il primo passaggio consiste nell'puntare Mixed Reality Feature Tool  al percorso **del Project** usando il pulsante con i puntini di sospensione, fare clic sul pulsante con i tre puntini di sospensione accanto al percorso del Project e passare alla cartella del progetto nello strumento di esplorazione, ad esempio _D:\MixedRealityLearning\MRTK Tutorials._

<img src="../images/mr-learning-base/base-02-section4-step1-3.png" width="650px" alt="Adding Unity Path for MixedRealityFeatureTool">


Dopo aver individuato la cartella del progetto, fai clic sul pulsante Apri per tornare a Mixed Reality Feature Tool (Strumento per le funzionalità di realtà mista). Fare quindi clic **su Individua funzionalità**.

> [!NOTE]
> La finestra di dialogo visualizzata quando si esplora la cartella del progetto Unity contiene "_" come nome del file. Per consentire la selezione della cartella, è necessario che sia presente un valore per il nome del file.

> [!Important]
> Lo strumento di funzionalità di realtà mista esegue la convalida per assicurarsi che sia stato indirizzato a una cartella di progetto Unity. La cartella deve contenere asset, pacchetti e Project Impostazioni cartelle.

Le funzionalità sono raggruppate per categoria per semplificare l'individuazione, fare clic sull'elenco a discesa Toolkit mixed **reality (Realtà** mista) per trovare i pacchetti relativi al Toolkit.

<img src="../images/mr-learning-base/base-02-section4-step1-4.PNG" width="650px" alt="MixedRealityFeatureTool Discover Features">

Selezionare la casella **mixed reality Toolkit Foundation** e fare clic sull'elenco a discesa accanto per selezionare **MRTK 2.7.0** e quindi fare clic sul pulsante Get **features** (Ottieni funzionalità) per scaricare i pacchetti selezionati.

<img src="../images/mr-learning-base/base-02-section4-step1-5.PNG" width="650px" alt="MixedRealityFeatureTool Open Mixed Reality">

Fare quindi  clic sul pulsante Convalida per convalidare il  pacchetto selezionato. Verrà visualizzata una finestra popup con il messaggio Non sono stati rilevati problemi di convalida fare clic su **OK** per chiudere il popup e fare clic sul **pulsante** Importa.

<img src="../images/mr-learning-base/base-02-section4-step1-6.PNG" width="650px" alt="MixedRealityFeatureTool Select required package">


Fare clic **sul pulsante** Approva per aggiungere **la** Toolkit realtà mista al progetto.

<img src="../images/mr-learning-base/base-02-section4-step1-7.PNG" width="650px" alt="MixedRealityFeatureTool Validate package">


## <a name="configuring-the-unity-project"></a>Configurazione del progetto Unity

Al termine dell'importazione del pacchetto dalla sezione precedente, viene visualizzata la finestra MRTK Project Configurator (Configuratore del progetto MRTK). In caso contrario, è possibile aprirlo manualmente selezionando **Mixed Reality** Toolkit Utilities Configure Project for MRTK (Configura Project  >    >    >  **per MRTK):**

![apertura dello strumento di configurazione MRTK](../images/mr-learning-base/base-02-section5-step1-1xrsdk.PNG)

Fare clic **su Built-in Unity Plugin (non-OpenXR) (Plug-in Unity** incorporato ( non OpenXR) per abilitare la gestione dei plug-in XR e aggiungere i pacchetti necessari al progetto.

![ Strumento di configurazione MRTK](../images/mr-learning-base/base-02-section5-step1-2xrsdk.PNG)

> [!NOTE]
> Lo screenshot precedente è di Unity 2020. Se si usa Unity 2019, selezionare **XR SDK/XR Management**

Verranno importati i pacchetti Unity necessari per XR Plugin Management. Al termine, fare clic su **Show Impostazioni** in MRTK project Configurator (Mostra Impostazioni nel progetto MRTK Configurator).

![Finestra Delle impostazioni del lettore](../images/mr-learning-base/base-02-section5-step1-3xrsdk.PNG)

Verrà visualizzata Project Impostazioni finestra **,** nella finestra Project Impostazioni in **Gestione plug-in XR** Assicurarsi di essere nelle impostazioni della piattaforma Universal Windows Assicurarsi anche che l'opzione Inizializza **XR** all'avvio sia selezionata e selezionare Windows Mixed Reality **casella** di controllo.

![Finestra delle impostazioni del lettore Abilita Realtà mista-xrsdk](../images/mr-learning-base/base-02-section5-step1-4xrsdk.PNG)

Al termine dell'importazione di Windows Mixed Reality SDK, dovrebbe visualizzarsi di nuovo la finestra MRTK Project Configurator (Configuratore del progetto MRTK). In caso contrario, usa il menu di Unity per aprirla.

Nella finestra MRTK Project Configurator fare  clic su Next (Avanti), quindi usare l'elenco a discesa Audio spatializer (Spazializzatore audio) per selezionare **ms HRTF Spatializer (Spazializzatore MS HRTF),** quindi fare clic sul pulsante **Apply** (Applica) per applicare l'impostazione:

![Configurator-xrsdk del progetto MRTK](../images/mr-learning-base/base-02-section5-step1-5xrsdk.PNG)

> [!TIP]
> L'applicazione delle impostazioni predefinite di MRTK è facoltativa ma fortemente consigliata, poiché consente di configurare alcune impostazioni consigliate di Unity:

> * Set Single Pass Instanced rendering path (Imposta il percorso di rendering con istanze a singolo passaggio): migliora le prestazioni grafiche eseguendo la pipeline di rendering per entrambi gli occhi nella stessa chiamata di disegno. Per altre informazioni su questo argomento, è possibile fare riferimento alla sezione sul [rendering con istanze a singolo passaggio](/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering) della documentazione di MRTK relativa alle [prestazioni](/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering).
> * Set default Spatial Awareness layer (Imposta livello di consapevolezza spaziale predefinito): crea un livello di Unity denominato Spatial Awareness e configura MRTK per l'uso di questo livello per la mesh di consapevolezza spaziale. Per altre informazioni sui livelli di Unity, vedere la documentazione relativa alla <a href="https://docs.unity3d.com/Manual/Layers.html" target="_blank">personalizzazione dell'area di lavoro</a> di Unity.

> [!TIP]
> L'impostazione della proprietà Audio spatializer (Spazializzatore audio) è facoltativa, ma può migliorare l'esperienza audio nel progetto. Se si imposta questa proprietà su MS HRTF Spatializer, questo plug-in di spazializzatore verrà usato quando la proprietà AudioSource.spatialize di Unity è abilitata. Per altre informazioni su questo argomento, è possibile fare riferimento alle  <a href="//windows/mixed-reality/develop/unity/tutorials/unity-spatial-audio-ch1" target="_blank"> esercitazioni sull'audio spaziale</a>.

Fare clic **su Avanti** e quindi su **Fine** nella finestra MRTK Project Configurator per completare la configurazione del progetto Unity per XRSDK.

### <a name="configure-additional-project-settings"></a>Configurare impostazioni di progetto aggiuntive

Dal menu di Unity scegli **Edit** (Modifica) > **Project Settings** (Impostazioni del progetto) per visualizzare la finestra corrispondente:

Nella finestra Project Impostazioni selezionare **XR Plug-in Management** Windows Mixed Reality Runtime Impostazioni (Gestione plug-in XR Impostazioni Runtime) e quindi usare l'elenco a discesa Depth Buffer Format (Formato buffer di profondità) per selezionare la profondità  >    >   **a 16 bit:** 

![Abilitazione di Unity a 16 profondità](../images/mr-learning-base/base-02-section5-step2-1xrsdk.PNG)

> [!TIP]
> La riduzione del formato di profondità a 16 bit è facoltativa, ma consente di migliorare le prestazioni grafiche nel progetto. Per altre informazioni su questo argomento, è possibile fare riferimento alla sezione sulla <a href="/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering" target="_blank">condivisione del buffer di intensità (HoloLens)</a> della documentazione di MRTK relativa alle prestazioni.

Nella finestra Project Settings (Impostazioni progetto) seleziona **Player (Lettore)**  > **Publishing Settings** (Impostazioni di pubblicazione) e quindi nel campo **Package name** (Nome del pacchetto) immetti un nome appropriato, ad esempio _MRTKTutorials-GettingStarted_:

![Pubblicazione unity Impostazioni. Nome pacchetto configurato](../images/mr-learning-base/base-02-section5-step2-2.png)

> [!NOTE]
> Il valore di 'Package name' (Nome del pacchetto) è l'identificatore univoco dell'app. Modifica questo identificatore prima di distribuire l'app per evitare di sovrascrivere app installate in precedenza.

> [!TIP]
> Il valore di 'Product Name' (Nome del prodotto) è il nome visualizzato nel menu di avvio di HoloLens. Per semplificare l'individuazione dell'app durante lo sviluppo, anteponi un carattere di sottolineatura al nome in modo che compaia all'inizio dell'elenco.

# <a name="legacy-wsa"></a>[Legacy WSA](#tab/wsa)

Dopo **aver aperto MixedRealityFeatureTool,** fare clic su **Start** per iniziare a usare Mixed Reality Feature Tool.

<img src="../images/mr-learning-base/base-02-section4-step1-2.png" width="650px" alt="MixedRealityFeatureTool main screen">

Il primo passaggio consiste nell'puntare Mixed Reality Feature Tool  al percorso **del Project** usando il pulsante con i puntini di sospensione, fare clic sul pulsante con i tre puntini di sospensione accanto al percorso del Project e passare alla cartella del progetto nello strumento di esplorazione, ad esempio _D:\MixedRealityLearning\MRTK Tutorials._

<img src="../images/mr-learning-base/base-02-section4-step1-3.png" width="650px" alt="Adding Unity Path for MixedRealityFeatureTool">

Dopo aver individuato la cartella del progetto, fai clic sul pulsante Apri per tornare a Mixed Reality Feature Tool (Strumento per le funzionalità di realtà mista). Fare quindi clic **su Individua funzionalità**.

> [!NOTE]
> La finestra di dialogo visualizzata quando si esplora la cartella del progetto Unity contiene "_" come nome del file. Per consentire la selezione della cartella, è necessario che sia presente un valore per il nome del file.

> [!Important]
> Lo strumento di funzionalità di realtà mista esegue la convalida per assicurarsi che sia stato indirizzato a una cartella di progetto Unity. La cartella deve contenere asset, pacchetti e Project Impostazioni cartelle.

Le funzionalità sono raggruppate per categoria per semplificare l'individuazione, fare clic sull'elenco a discesa Toolkit mixed **reality (Realtà** mista) per trovare i pacchetti relativi al Toolkit.

<img src="../images/mr-learning-base/base-02-section4-step1-4.PNG" width="650px" alt="MixedRealityFeatureTool Discover Features">

Selezionare **Mixed Reality Toolkit Foundation** e fare clic sull'elenco a discesa accanto a esso per selezionare **MRTK 2.7.0** e quindi fare clic sul pulsante **Get features** (Ottieni funzionalità) per scaricare i pacchetti selezionati.

<img src="../images/mr-learning-base/base-02-section4-step1-5.PNG" width="650px" alt="MixedRealityFeatureTool Open Mixed Reality">

Fare quindi  clic sul pulsante Convalida per convalidare il  pacchetto selezionato. Verrà visualizzata una finestra popup con il messaggio Non sono stati rilevati problemi di convalida fare clic su **OK** per chiudere il popup e fare clic sul **pulsante** Importa.

<img src="../images/mr-learning-base/base-02-section4-step1-6.PNG" width="650px" alt="MixedRealityFeatureTool Select required package">

Fare clic **sul pulsante** Approva per aggiungere **la** Toolkit realtà mista al progetto.

<img src="../images/mr-learning-base/base-02-section4-step1-7.PNG" width="650px" alt="MixedRealityFeatureTool Validate package">


## <a name="configuring-the-unity-project"></a>Configurazione del progetto Unity

Al termine dell'importazione del pacchetto dalla sezione precedente, viene visualizzata la finestra MRTK Project Configurator (Configuratore del progetto MRTK). In caso contrario, è possibile aprirlo manualmente selezionando **Mixed Reality** Toolkit Utilities Configure Project for MRTK (Configura Project  >    >    >  **per MRTK):**

![Percorso del menu Configure Unity Project di Unity](../images/mr-learning-base/base-02-section5-step1-1.png)

Fare clic **su Legacy XR (XR** legacy) per abilitare Legacy XR (XR legacy) e aggiungere i pacchetti necessari al progetto.

![s](../images/mr-learning-base/base-02-section5-step1-2.png)

Fare clic sul pulsante Avanti per abilitare le impostazioni della pipeline XR per XR legacy.

![Finestra di configurazione di Unity MRTK](../images/mr-learning-base/base-02-section5-step1-3.PNG)

Nella finestra MRTK Project Configurator verificare che tutte le opzioni siano selezionate e usare anche l'elenco a  discesa **Spazializzatore** audio per selezionare l'spazializzatore **MS HRTF** e quindi fare clic sul pulsante Applica per applicare l'impostazione:

![Finestra di configurazione di MRTK](../images/mr-learning-base/base-02-section5-step1-4.PNG)

> [!TIP]
> L'applicazione delle impostazioni predefinite di MRTK è facoltativa ma fortemente consigliata, poiché consente di configurare alcune impostazioni consigliate di Unity:

> * Set Single Pass Instanced rendering path (Imposta il percorso di rendering con istanze a singolo passaggio): migliora le prestazioni grafiche eseguendo la pipeline di rendering per entrambi gli occhi nella stessa chiamata di disegno. Per altre informazioni su questo argomento, è possibile fare riferimento alla sezione sul [rendering con istanze a singolo passaggio](/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering) della documentazione di MRTK relativa alle [prestazioni](/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering).
> * Set default Spatial Awareness layer (Imposta livello di consapevolezza spaziale predefinito): crea un livello di Unity denominato Spatial Awareness e configura MRTK per l'uso di questo livello per la mesh di consapevolezza spaziale. Per altre informazioni sui livelli di Unity, vedere la documentazione relativa alla <a href="https://docs.unity3d.com/Manual/Layers.html" target="_blank">personalizzazione dell'area di lavoro</a> di Unity.

> [!TIP]
> L'impostazione della proprietà Audio spatializer (Spazializzatore audio) è facoltativa, ma può migliorare l'esperienza audio nel progetto. Se si imposta questa proprietà su MS HRTF Spatializer, questo plug-in di spazializzatore verrà usato quando la proprietà AudioSource.spatialize di Unity è abilitata. Per altre informazioni su questo argomento, è possibile fare riferimento alle  <a href="//windows/mixed-reality/develop/unity/tutorials/unity-spatial-audio-ch1" target="_blank"> esercitazioni sull'audio spaziale</a>.

Fare clic **su Avanti** e quindi sul pulsante **Done** (Fine) nella finestra MRTK Project Configurator per completare la configurazione del progetto Unity per Legacy XR.

### <a name="configure-additional-project-settings"></a>Configurare impostazioni di progetto aggiuntive

Dal menu di Unity scegli **Edit** (Modifica) > **Project Settings** (Impostazioni del progetto) per visualizzare la finestra corrispondente:

Nella finestra Project Settings (Impostazioni progetto) seleziona **Player (Lettore)**  > **XR Settings** (Impostazioni XR) e quindi usa l'elenco a discesa **Depth Format** (Formato profondità) per selezionare **16-bit depth** (Profondità a 16 bit):

![Abilitazione di Unity a 16 profondità](../images/mr-learning-base/base-02-section5-step2-1.png)

> [!TIP]
> La riduzione del formato di profondità a 16 bit è facoltativa, ma consente di migliorare le prestazioni grafiche nel progetto. Per altre informazioni su questo argomento, è possibile fare riferimento alla sezione sulla <a href="/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering" target="_blank">condivisione del buffer di intensità (HoloLens)</a> della documentazione di MRTK relativa alle prestazioni.

Nella finestra Project Settings (Impostazioni progetto) seleziona **Player (Lettore)**  > **Publishing Settings** (Impostazioni di pubblicazione) e quindi nel campo **Package name** (Nome del pacchetto) immetti un nome appropriato, ad esempio _MRTKTutorials-GettingStarted_:

![Pubblicazione unity Impostazioni. Nome pacchetto configurato](../images/mr-learning-base/base-02-section5-step2-2.png)

> [!NOTE]
> Il valore di 'Package name' (Nome del pacchetto) è l'identificatore univoco dell'app. Modifica questo identificatore prima di distribuire l'app per evitare di sovrascrivere app installate in precedenza.

> [!TIP]
> Il valore di 'Product Name' (Nome del prodotto) è il nome visualizzato nel menu di avvio di HoloLens. Per semplificare l'individuazione dell'app durante lo sviluppo, anteponi un carattere di sottolineatura al nome in modo che compaia all'inizio dell'elenco.

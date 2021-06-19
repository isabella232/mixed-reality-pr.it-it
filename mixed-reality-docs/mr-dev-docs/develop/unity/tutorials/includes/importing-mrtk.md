---
ms.openlocfilehash: 0c25f726c391c1485efab26828d2bfe4a6468f8b
ms.sourcegitcommit: bdf4babd13e021f41fb04cdb3611bb759bd77537
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2021
ms.locfileid: "112397045"
---
# <a name="unity-2020--openxr"></a>[Unity 2020 + OpenXR](#tab/openxr)

Dopo **aver aperto MixedRealityFeatureTool,** per  accedere alle  versioni di  anteprima fare clic su Impostazioni e abilitare Mostra versioni di anteprima nella scheda Funzionalità, quindi fare clic su **OK** per salvare le impostazioni.

![MixedRealityFeatureTool (anteprima)](../images/mr-learning-base/base-02-section4-step1-2-preview.PNG)

Fare clic su **Start (Avvia)** per iniziare a usare mixed reality feature tool (Strumento per le funzionalità di realtà mista).

![MixedRealityFeatureTool](../images/mr-learning-base/base-02-section4-step1-2.png)

Il primo passaggio consiste nel puntare Lo  strumento per  le funzionalità di realtà mista al percorso del progetto usando il pulsante con i puntini di sospensione, fare clic sul pulsante con i tre puntini di sospensione accanto al percorso del progetto e passare alla cartella del progetto nello strumento di esplorazione, ad esempio _D:\MixedRealityLearning\MRTK Tutorials._

![Aggiunta di un percorso Unity per MixedRealityFeatureTool](../images/mr-learning-base/base-02-section4-step1-3.png)

Dopo aver individuato la cartella del progetto, fai clic sul pulsante Apri per tornare a Mixed Reality Feature Tool (Strumento per le funzionalità di realtà mista). Fare quindi clic **su Individua funzionalità**.

> [!NOTE]
> La finestra di dialogo visualizzata quando si esplora la cartella del progetto Unity contiene "_" come nome del file. Per consentire la selezione della cartella, è necessario che sia presente un valore per il nome del file.

> [!Important]
> Lo strumento di funzionalità di realtà mista esegue la convalida per assicurarsi che sia stato indirizzato a una cartella di progetto Unity. La cartella deve contenere le cartelle Assets, Packages e Project Settings.

Le funzionalità sono raggruppate per categoria per semplificare l'individuazione, fai clic sull'elenco a discesa **Mixed Reality Toolkit** per trovare i pacchetti relativi a Mixed Reality Toolkit e fai clic sull'elenco a discesa Platform **Support** (Supporto piattaforma) per trovare i pacchetti relativi alle varie piattaforme di supporto.

![Funzionalità di individuazione di MixedRealityFeatureTool](../images/mr-learning-base/base-02-section4-step1-4-openxr.png)

Controlla **Mixed Reality Toolkit Foundation** e fai clic sull'elenco a discesa accanto a esso per selezionare **MRTK 2.7.0,** controlla anche **Mixed Reality OpenXR Plugin (Plug-in OpenXR** realtà mista) e fai clic sull'elenco a discesa accanto per selezionare la versione più recente disponibile, quindi fai clic sul pulsante **Get features** (Ottieni funzionalità) per scaricare i pacchetti selezionati.

![MixedRealityFeatureTool Open MixedReality](../images/mr-learning-base/base-02-section4-step1-5-openxr.PNG)

Fare quindi  clic sul pulsante Convalida per convalidare il  pacchetto selezionato. Verrà visualizzata una finestra popup con il messaggio Non sono stati rilevati problemi di convalida fare clic su **OK** per chiudere il popup e fare clic sul **pulsante** Importa.

![MixedRealityFeatureTool Selezionare il pacchetto richiesto](../images/mr-learning-base/base-02-section4-step1-6-OpenXR.PNG)

Fare clic **sul pulsante** Approva per aggiungere Mixed **Reality Toolkit** al progetto.

![Pacchetto MixedRealityFeatureTool Validate](../images/mr-learning-base/base-02-section4-step1-7-openxr.PNG)

## <a name="configuring-the-unity-project"></a>Configurazione del progetto Unity

Dopo che Unity ha terminato l'importazione del pacchetto dalla sezione precedente, viene visualizzato un messaggio di avviso per riavviare l'editor di Unity per abilitare i back-end per il nuovo sistema plug-in, fare clic su **Yes (Sì)**

![Opzione di riavvio di Unity](../images/mr-learning-base/base-02-section5-step1-1-openxr.PNG)

Dopo il riavvio di Unity verrà visualizzata la finestra MRTK Project Configurator (Configuratore progetto MRTK). In caso contrario, è possibile aprirlo manualmente selezionando **Mixed Reality** Toolkit Utilities Configure Project for MRTK (Mixed Reality  >  **Toolkit**  >  **Utilities**  >  **Configure Project for MRTK:**

![Aprire la finestra di configurazione del progetto MRTK](../images/mr-learning-base/base-02-section5-step1-2-openxr.png)

Fare clic **su Unity OpenXR Plugin (Plug-in OpenXR Unity)** per abilitare la gestione dei plug-in XR e aggiungere i pacchetti necessari al progetto.

![Aggiungere il plug-in OpenXR di Unity ](../images/mr-learning-base/base-02-section5-step1-3-openxr.PNG)

Verranno importati i pacchetti Unity necessari per XR Plugin Management. Al termine, fare clic su **Show XR Plug-In Management Settings** in MRTK project Configurator (Mostra impostazioni di gestione Plug-In XR nel progetto MRTK Configurator).

![Mostra impostazioni di Plug-In XR ](../images/mr-learning-base/base-02-section5-step1-4-openxr.PNG)

Verrà visualizzata la **finestra Impostazioni progetto**,

![Abilitare Open XR](../images/mr-learning-base/base-02-section5-step1-5-openxr.PNG)

Nella finestra Project Settings (Impostazioni progetto) in **XR Plug-in Management (Gestione plug-in XR)** assicurarsi che sia selezionata anche l'opzione piattaforma UWP (Universal Windows Platform) Initialize **XR on Startup** (Inizializza XR all'avvio), quindi selezionare la casella di controllo Open XR (Apri **XR)** e la casella di controllo Microsoft HoloLens **feature set (Set** di funzionalità) per abilitarle.

![Finestra Impostazioni progetto 1](../images/mr-learning-base/base-02-section5-step1-6-openxr.PNG)

Se viene visualizzata un'icona di avviso rossa accanto a **Plug-in OpenXR,** fare clic sull'icona e **selezionare Correggi tutto** prima di continuare. Per l'applicazione delle modifiche, potrebbe essere necessario riavviare l'editor di Unity.

![Finestra Impostazioni progetto 2](../images/mr-learning-base/base-02-section5-step1-7-openxr.PNG)

Dopo aver risolto tutti i problemi, chiudere la **finestra Impostazioni** progetto.

Nella barra dei menu passare a **Mixed Reality** >  **OpenXR Apply** recommended project settings for HoloLens 2 to get better app performance (Applica le impostazioni di progetto consigliate per la realtà mista per ottenere prestazioni migliori  >   dell'app).

![Finestra Impostazioni progetto 3](../images/mr-learning-base/base-02-section5-step1-8-openxr.PNG)

Usare il menu Unity per aprire MRTK Project Configurator. Nella finestra MRTK Project Configurator (Configuratore progetto MRTK) fare clic su **Next**(Avanti) e quindi sul pulsante **Apply (Applica)** per applicare le impostazioni:

![Finestra Impostazioni progetto 4](../images/mr-learning-base/base-02-section5-step1-9-openxr.png)

Dopo aver fatto clic su Applica, Unity tenterà di riavviare per applicare il sistema di input, fare clic su **Applica** per riavviare l'editor di Unity

![Finestra Impostazioni progetto 5](../images/mr-learning-base/base-02-section5-step1-10-openxr.PNG)

Dopo il riavvio di Unity, aprire MRTK Project Configurator dal menu di Unity e fare clic su **Next** (Avanti), quindi fare clic su **Done** (Fine) per completare la configurazione del progetto Unity per OpenXR.

### <a name="configure-additional-project-settings"></a>Configurare impostazioni di progetto aggiuntive

Dal menu di Unity scegli **Edit** (Modifica) > **Project Settings** (Impostazioni del progetto) per visualizzare la finestra corrispondente:

Nella finestra Project Settings (Impostazioni progetto) selezionare XR Plug-in Management OpenXR (OpenXR gestione **plug-in XR),** quindi usare l'elenco a discesa Depth Submission Mode (Modalità di invio profondità) per selezionare  >   **Depth 16-bit (Profondità a 16 bit):** 

![Abilitazione di Unity a 16 profondità](../images/mr-learning-base/base-02-section5-step2-1-openxr.PNG)

> [!TIP]
> La riduzione del formato di profondità a 16 bit è facoltativa, ma consente di migliorare le prestazioni grafiche nel progetto. Per altre informazioni su questo argomento, è possibile fare riferimento alla sezione sulla <a href="/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering" target="_blank">condivisione del buffer di intensità (HoloLens)</a> della documentazione di MRTK relativa alle prestazioni.

Nella finestra Project Settings (Impostazioni progetto) seleziona **Player (Lettore)**  > **Publishing Settings** (Impostazioni di pubblicazione) e quindi nel campo **Package name** (Nome del pacchetto) immetti un nome appropriato, ad esempio _MRTKTutorials-GettingStarted_:

![Impostazioni di pubblicazione di Unity. Nome pacchetto configurato](../images/mr-learning-base/base-02-section5-step2-2.png)

> [!NOTE]
> Il valore di 'Package name' (Nome del pacchetto) è l'identificatore univoco dell'app. Modifica questo identificatore prima di distribuire l'app per evitare di sovrascrivere app installate in precedenza.

> [!TIP]
> Il valore di 'Product Name' (Nome del prodotto) è il nome visualizzato nel menu di avvio di HoloLens. Per semplificare l'individuazione dell'app durante lo sviluppo, anteponi un carattere di sottolineatura al nome in modo che compaia all'inizio dell'elenco.

# <a name="unity-20192020--windows-xr-plugin"></a>[Unity 2019/2020 + Plug-in Windows XR](#tab/winxr)

Dopo **aver aperto MixedRealityFeatureTool,** per  accedere alle  versioni di  anteprima fare clic su Impostazioni e abilitare Mostra versioni di anteprima nella scheda Funzionalità, quindi fare clic su **OK** per salvare le impostazioni.

![MixedRealityFeatureTool per l'anteprima](../images/mr-learning-base/base-02-section4-step1-2-preview.PNG)

Fare quindi clic su **Start (Avvia)** per iniziare a usare mixed reality feature tool (Strumento per le funzionalità di realtà mista).

![MixedRealityFeatureTool ](../images/mr-learning-base/base-02-section4-step1-2.png)

Il primo passaggio consiste nel puntare Lo  strumento per  le funzionalità di realtà mista al percorso del progetto usando il pulsante con i puntini di sospensione, fare clic sul pulsante con i tre puntini di sospensione accanto al percorso del progetto e passare alla cartella del progetto nello strumento di esplorazione, ad esempio _D:\MixedRealityLearning\MRTK Tutorials._

![Aggiunta di un percorso Unity per MixedRealityFeatureTool](../images/mr-learning-base/base-02-section4-step1-3.png)

Dopo aver individuato la cartella del progetto, fai clic sul pulsante Apri per tornare a Mixed Reality Feature Tool (Strumento per le funzionalità di realtà mista). Fare quindi clic **su Individua funzionalità**.

> [!NOTE]
> La finestra di dialogo visualizzata quando si esplora la cartella del progetto Unity contiene "_" come nome del file. Per consentire la selezione della cartella, è necessario che sia presente un valore per il nome del file.

> [!Important]
> Lo strumento di funzionalità di realtà mista esegue la convalida per assicurarsi che sia stato indirizzato a una cartella di progetto Unity. La cartella deve contenere le cartelle Assets, Packages e Project Settings.

Le funzionalità sono raggruppate per categoria per semplificare l'individuazione. Fare clic sull'elenco a discesa **mixed reality toolkit** per trovare i pacchetti relativi a Mixed Reality Toolkit.

![Funzionalità di individuazione di MixedRealityFeatureTool](../images/mr-learning-base/base-02-section4-step1-4.PNG)

Seleziona la casella **per Mixed Reality Toolkit Foundation** e fai clic sull'elenco a discesa accanto per selezionare **MRTK 2.7.0** e quindi fai clic sul pulsante **Get features** (Ottieni funzionalità) per scaricare i pacchetti selezionati.

![MixedRealityFeatureTool Open MixedReality](../images/mr-learning-base/base-02-section4-step1-5.PNG)

Fare quindi  clic sul pulsante Convalida per convalidare il  pacchetto selezionato. Verrà visualizzata una finestra popup con il messaggio Non sono stati rilevati problemi di convalida fare clic su **OK** per chiudere il popup e fare clic sul **pulsante** Importa.

![MixedRealityFeatureTool Selezionare il pacchetto richiesto](../images/mr-learning-base/base-02-section4-step1-6.PNG)

Fare clic **sul pulsante** Approva per aggiungere Mixed **Reality Toolkit** al progetto.

![Pacchetto MixedRealityFeatureTool Validate](../images/mr-learning-base/base-02-section4-step1-7.PNG)

## <a name="configuring-the-unity-project"></a>Configurazione del progetto Unity

Al termine dell'importazione del pacchetto dalla sezione precedente, viene visualizzata la finestra MRTK Project Configurator (Configuratore del progetto MRTK). In caso contrario, è possibile aprirlo manualmente selezionando **Mixed Reality** Toolkit Utilities Configure Project for MRTK (Mixed Reality  >  **Toolkit**  >  **Utilities**  >  **Configure Project for MRTK:**

![apertura dello strumento di configurazione MRTK](../images/mr-learning-base/base-02-section5-step1-1xrsdk.PNG)

Fare clic **su Built-in Unity Plugin (non-OpenXR) (Plug-in Unity** incorporato ( non OpenXR) per abilitare la gestione dei plug-in XR e aggiungere i pacchetti necessari al progetto.

![ Strumento di configurazione MRTK](../images/mr-learning-base/base-02-section5-step1-2xrsdk.PNG)

> [!NOTE]
> Lo screenshot precedente è di Unity 2020. Se si usa Unity 2019, selezionare **XR SDK/XR Management**

Verranno importati i pacchetti Unity necessari per XR Plugin Management. Al termine, fare clic **su Show Settings** in MRTK project Configurator (Mostra impostazioni nel progetto MRTK Configurator).

![Finestra Player settings (Impostazioni lettore)](../images/mr-learning-base/base-02-section5-step1-3xrsdk.PNG)

Verrà visualizzata la finestra Project **Settings**(Impostazioni progetto), nella finestra Project Settings (Impostazioni progetto) in XR Plug-in piattaforma UWP (Universal Windows Platform) Management (Gestione **plug-in XR)** Assicurarsi che sia selezionata anche la casella di controllo Initialize **XR on Startup** (Inizializza XR **all'avvio)** e selezionare la casella di controllo Windows Mixed Reality.

![Finestra delle impostazioni del lettore Abilita Realtà mista-xrsdk](../images/mr-learning-base/base-02-section5-step1-4xrsdk.PNG)

Al termine dell'importazione di Windows Mixed Reality SDK, dovrebbe visualizzarsi di nuovo la finestra MRTK Project Configurator (Configuratore del progetto MRTK). In caso contrario, usa il menu di Unity per aprirla.

Nella finestra MRTK Project Configurator  (Configuratore progetto MRTK) fare clic su Next (Avanti), quindi usare l'elenco a discesa Audio spatializer (Spazializzatore audio) per selezionare **MS HRTF Spatializer (Spazializzatore MS HRTF),** quindi fare clic sul pulsante **Apply (Applica)** per applicare l'impostazione:

![Configurator-xrsdk del progetto MRTK](../images/mr-learning-base/base-02-section5-step1-5xrsdk.PNG)

> [!TIP]
> L'applicazione delle impostazioni predefinite di MRTK è facoltativa ma fortemente consigliata, poiché consente di configurare alcune impostazioni consigliate di Unity:

> * Set Single Pass Instanced rendering path (Imposta il percorso di rendering con istanze a singolo passaggio): migliora le prestazioni grafiche eseguendo la pipeline di rendering per entrambi gli occhi nella stessa chiamata di disegno. Per altre informazioni su questo argomento, è possibile fare riferimento alla sezione sul [rendering con istanze a singolo passaggio](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering) della documentazione di MRTK relativa alle [prestazioni](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering).
> * Set default Spatial Awareness layer (Imposta livello di consapevolezza spaziale predefinito): crea un livello di Unity denominato Spatial Awareness e configura MRTK per l'uso di questo livello per la mesh di consapevolezza spaziale. Per altre informazioni sui livelli di Unity, vedere la documentazione relativa alla <a href="https://docs.unity3d.com/Manual/Layers.html" target="_blank">personalizzazione dell'area di lavoro</a> di Unity.

> [!TIP]
> L'impostazione della proprietà Audio spatializer (Spazializzatore audio) è facoltativa, ma può migliorare l'esperienza audio nel progetto. Se si imposta questa proprietà su MS HRTF Spatializer, questo plug-in di spazializzatore verrà usato quando la proprietà AudioSource.spatialize di Unity è abilitata. Per altre informazioni su questo argomento, è possibile fare riferimento alle esercitazioni  <a href="//windows/mixed-reality/develop/unity/tutorials/unity-spatial-audio-ch1" target="_blank"> sull'audio spaziale</a>.

Fare clic **su Avanti** e quindi **fare** clic su Fine nella finestra MRTK Project Configurator per completare la configurazione del progetto Unity per XRSDK.

### <a name="configure-additional-project-settings"></a>Configurare impostazioni di progetto aggiuntive

Dal menu di Unity scegli **Edit** (Modifica) > **Project Settings** (Impostazioni del progetto) per visualizzare la finestra corrispondente:

Nella finestra Project Settings (Impostazioni progetto) selezionare XR Plug-in Management Windows Mixed Reality Runtime Settings (Impostazioni runtime **plug-in XR)** e quindi usare l'elenco a discesa Depth Buffer Format (Formato buffer di profondità) per selezionare la profondità  >    >   **a 16 bit:** 

![Unity Abilita 16 profondità](../images/mr-learning-base/base-02-section5-step2-1xrsdk.PNG)

> [!TIP]
> La riduzione del formato di profondità a 16 bit è facoltativa, ma consente di migliorare le prestazioni grafiche nel progetto. Per altre informazioni su questo argomento, è possibile fare riferimento alla sezione sulla <a href="/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering" target="_blank">condivisione del buffer di intensità (HoloLens)</a> della documentazione di MRTK relativa alle prestazioni.

Nella finestra Project Settings (Impostazioni progetto) seleziona **Player (Lettore)**  > **Publishing Settings** (Impostazioni di pubblicazione) e quindi nel campo **Package name** (Nome del pacchetto) immetti un nome appropriato, ad esempio _MRTKTutorials-GettingStarted_:

![Impostazioni di pubblicazione unity. Nome pacchetto configurato](../images/mr-learning-base/base-02-section5-step2-2.png)

> [!NOTE]
> Il valore di 'Package name' (Nome del pacchetto) è l'identificatore univoco dell'app. Modifica questo identificatore prima di distribuire l'app per evitare di sovrascrivere app installate in precedenza.

> [!TIP]
> Il valore di 'Product Name' (Nome del prodotto) è il nome visualizzato nel menu di avvio di HoloLens. Per semplificare l'individuazione dell'app durante lo sviluppo, anteponi un carattere di sottolineatura al nome in modo che compaia all'inizio dell'elenco.

# <a name="legacy-wsa"></a>[Legacy WSA](#tab/wsa)

Dopo **aver aperto MixedRealityFeatureTool,** per accedere alle versioni di anteprima fare clic su **Impostazioni** e abilitare **Mostra** versioni di anteprima nella scheda **Funzionalità,** quindi fare clic su **OK** per salvare le impostazioni.

![MixedRealityFeatureTool preview](../images/mr-learning-base/base-02-section4-step1-2-preview.PNG)

Fare clic su **Start per** iniziare a usare Mixed Reality Feature Tool.

![MixedRealityFeatureTool](../images/mr-learning-base/base-02-section4-step1-2.png)

Il primo passaggio consiste nel puntare lo  strumento di  funzionalità di realtà mista al percorso del progetto usando il pulsante con i puntini di sospensione, fare clic sul pulsante con i puntini di sospensione tre puntini accanto al percorso del progetto e passare alla cartella del progetto in Esplora risorse, ad esempio _D:\MixedRealityLearning\MRTK Tutorials_.

![Aggiunta del percorso Unity per MixedRealityFeatureTool](../images/mr-learning-base/base-02-section4-step1-3.png)

Dopo aver individuato la cartella del progetto, fare clic sul pulsante Apri per tornare a Strumento di funzionalità di realtà mista. Fare quindi clic su **Individua funzionalità**.

> [!NOTE]
> La finestra di dialogo visualizzata quando si esplora la cartella del progetto Unity contiene '_' come nome file. Per consentire la selezione della cartella, deve essere presente un valore per il nome file.

> [!Important]
> Lo strumento funzionalità realtà mista esegue la convalida per assicurarsi che sia stato indirizzato a una cartella del progetto Unity. La cartella deve contenere le cartelle Asset, Pacchetti e Impostazioni progetto.

Le funzionalità sono raggruppate per categoria per semplificare l'individuazione, fare clic sull'elenco a discesa **mixed reality toolkit** per trovare i pacchetti relativi a Mixed Reality Toolkit.

![Funzionalità di individuazione degli strumenti MixedRealityFeatureTool](../images/mr-learning-base/base-02-section4-step1-4.PNG)

Selezionare **Mixed Reality Toolkit Foundation** e fare clic sull'elenco a discesa accanto a esso per  selezionare **MRTK 2.7.0,** quindi fare clic sul pulsante Ottieni funzionalità per scaricare i pacchetti selezionati.

![MixedRealityFeatureTool Open MixedReality](../images/mr-learning-base/base-02-section4-step1-5.PNG)

Fare quindi clic **sul** pulsante Convalida per convalidare il pacchetto selezionato. Verrà visualizzata una finestra popup con il messaggio Nessun problema di convalida rilevato **fare** clic su **OK** per chiudere il popup e fare clic sul **pulsante** Importa.

![MixedRealityFeatureTool Selezionare il pacchetto richiesto](../images/mr-learning-base/base-02-section4-step1-6.PNG)

Fare clic **sul pulsante** Approva per aggiungere Mixed **Reality Toolkit** al progetto.

![Pacchetto MixedRealityFeatureTool Validate](../images/mr-learning-base/base-02-section4-step1-7.PNG)

## <a name="configuring-the-unity-project"></a>Configurazione del progetto Unity

Al termine dell'importazione del pacchetto dalla sezione precedente, viene visualizzata la finestra MRTK Project Configurator (Configuratore del progetto MRTK). In caso contrario, è possibile aprirlo manualmente in **Mixed Reality**  >  **Toolkit**  >  **Utilities**  >  **Configure Project for MRTK**:

![Percorso del menu Configure Unity Project di Unity](../images/mr-learning-base/base-02-section5-step1-1.png)

Fare clic **su Legacy XR (XR** legacy) per abilitare Legacy XR e aggiungere i pacchetti necessari al progetto.

![s](../images/mr-learning-base/base-02-section5-step1-2.png)

Fare clic sul pulsante Avanti per abilitare le impostazioni della pipeline XR per Legacy XR.

![Finestra di configurazione di Unity MRTK](../images/mr-learning-base/base-02-section5-step1-3.PNG)

Nella finestra MRTK Project Configurator verificare che tutte le opzioni siano selezionate e usare anche l'elenco a discesa **Spazializzatore** audio per selezionare lo spazializzatore **MS HRTF,** quindi fare clic sul pulsante Applica per applicare l'impostazione: 

![Finestra di configurazione di MRTK](../images/mr-learning-base/base-02-section5-step1-4.PNG)

> [!TIP]
> L'applicazione delle impostazioni predefinite di MRTK è facoltativa ma fortemente consigliata, poiché consente di configurare alcune impostazioni consigliate di Unity:

> * Set Single Pass Instanced rendering path (Imposta il percorso di rendering con istanze a singolo passaggio): migliora le prestazioni grafiche eseguendo la pipeline di rendering per entrambi gli occhi nella stessa chiamata di disegno. Per altre informazioni su questo argomento, è possibile fare riferimento alla sezione sul [rendering con istanze a singolo passaggio](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering) della documentazione di MRTK relativa alle [prestazioni](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering).
> * Set default Spatial Awareness layer (Imposta livello di consapevolezza spaziale predefinito): crea un livello di Unity denominato Spatial Awareness e configura MRTK per l'uso di questo livello per la mesh di consapevolezza spaziale. Per altre informazioni sui livelli di Unity, vedere la documentazione relativa alla <a href="https://docs.unity3d.com/Manual/Layers.html" target="_blank">personalizzazione dell'area di lavoro</a> di Unity.

> [!TIP]
> L'impostazione della proprietà Audio spatializer (Spazializzatore audio) è facoltativa, ma può migliorare l'esperienza audio nel progetto. Se si imposta questa proprietà su MS HRTF Spatializer, questo plug-in di spazializzatore verrà usato quando la proprietà AudioSource.spatialize di Unity è abilitata. Per altre informazioni su questo argomento, è possibile fare riferimento alle esercitazioni  <a href="//windows/mixed-reality/develop/unity/tutorials/unity-spatial-audio-ch1" target="_blank"> sull'audio spaziale</a>.

Fare clic **su Avanti** e quindi **fare** clic sul pulsante Fine nella finestra di MRTK Project Configurator per completare la configurazione del progetto Unity per Legacy XR.

### <a name="configure-additional-project-settings"></a>Configurare impostazioni di progetto aggiuntive

Dal menu di Unity scegli **Edit** (Modifica) > **Project Settings** (Impostazioni del progetto) per visualizzare la finestra corrispondente:

Nella finestra Project Settings (Impostazioni progetto) seleziona **Player (Lettore)**  > **XR Settings** (Impostazioni XR) e quindi usa l'elenco a discesa **Depth Format** (Formato profondità) per selezionare **16-bit depth** (Profondità a 16 bit):

![Unity Abilita 16 profondità](../images/mr-learning-base/base-02-section5-step2-1.png)

> [!TIP]
> La riduzione del formato di profondità a 16 bit è facoltativa, ma consente di migliorare le prestazioni grafiche nel progetto. Per altre informazioni su questo argomento, è possibile fare riferimento alla sezione sulla <a href="/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering" target="_blank">condivisione del buffer di intensità (HoloLens)</a> della documentazione di MRTK relativa alle prestazioni.

Nella finestra Project Settings (Impostazioni progetto) seleziona **Player (Lettore)**  > **Publishing Settings** (Impostazioni di pubblicazione) e quindi nel campo **Package name** (Nome del pacchetto) immetti un nome appropriato, ad esempio _MRTKTutorials-GettingStarted_:

![Impostazioni di pubblicazione unity. Nome pacchetto configurato](../images/mr-learning-base/base-02-section5-step2-2.png)

> [!NOTE]
> Il valore di 'Package name' (Nome del pacchetto) è l'identificatore univoco dell'app. Modifica questo identificatore prima di distribuire l'app per evitare di sovrascrivere app installate in precedenza.

> [!TIP]
> Il valore di 'Product Name' (Nome del prodotto) è il nome visualizzato nel menu di avvio di HoloLens. Per semplificare l'individuazione dell'app durante lo sviluppo, anteponi un carattere di sottolineatura al nome in modo che compaia all'inizio dell'elenco.

---
ms.openlocfilehash: d8d46da1a1a095074f059b53ebd997e1b6f89961
ms.sourcegitcommit: 95fbb851336b6c5977a2ce4d4ac10f0eeb0df31f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/24/2021
ms.locfileid: "107984403"
---
# <a name="unity-20192020--windows-xr-plugin"></a>[Unity 2019/2020 + Plug-in Windows XR](#tab/winxr)

Dal menu di Unity scegli **Edit** (Modifica) > **Project Settings** (Impostazioni del progetto) per visualizzare la finestra corrispondente:

![Percorso del menu Project Settings... di Unity](../images/mr-learning-base/base-02-section5-step2-1.png)

Nella finestra Project Settings (Impostazioni progetto) selezionare **XR Plug-in Management**  >  **Install XR Plug-in Management (Gestione plug-in XR XR)** per installare Gestione plug-in XR:

![Impostazioni di Unity XR](../images/mr-learning-base/base-02-section5-step2-2.png)

Al termine dell'installazione di Gestione plug-in XR in Unity. Assicurarsi di avere le impostazioni piattaforma UWP (Universal Windows Platform) e selezionare la casella di controllo **Inizializza XR** all'avvio **e Windows Mixed Reality** controllo.

![Unity XR Settings with add Windows Mixed Reality SDK](../images/mr-learning-base/base-02-section5-step2-2-1.png)

Al termine dell'importazione di Windows Mixed Reality SDK, dovrebbe visualizzarsi di nuovo la finestra MRTK Project Configurator (Configuratore del progetto MRTK). In caso contrario, usa il menu di Unity per aprirla.

Nella finestra MRTK Project Configurator (Configuratore del progetto MRTK) usa l'elenco a discesa **Audio spatializer** (Spazializzatore audio) per selezionare **MS HRTF Spatializer** e quindi fai clic sul pulsante **Apply** (Applica) per applicare l'impostazione:

![Impostazioni XR di Unity con Windows Mixed Reality SDK selezionato](../images/mr-learning-base/base-02-section5-step2-2-2.png)

> [!TIP]
>L'impostazione della proprietà Audio spatializer (Spazializzatore audio) è facoltativa, ma può migliorare l'esperienza audio nel progetto. Se si imposta questa proprietà su MS HRTF Spatializer, questo plug-in di spazializzatore verrà usato quando la proprietà AudioSource.spatialize di Unity è abilitata. Per altre informazioni su questo argomento, è possibile fare riferimento alle esercitazioni  <a href="https://docs.microsoft.com/windows/mixed-reality/develop/unity/tutorials/unity-spatial-audio-ch1" target="_blank"> sull'audio spaziale</a>.

Nella finestra Project Settings (Impostazioni progetto) selezionare XR Plug-in Management Windows Mixed Reality Runtime Settings (Impostazioni runtime **plug-in XR)** e quindi usare l'elenco a discesa Depth Buffer Format (Formato buffer di profondità) per selezionare la profondità  >    >   **a 16 bit:** 

![Impostazioni di pubblicazione unity con nome pacchetto evidenziato](../images/mr-learning-base/base-02-section5-step2-5-1.png)

> [!TIP]
> La riduzione del formato di profondità a 16 bit è facoltativa, ma consente di migliorare le prestazioni grafiche nel progetto. Per altre informazioni su questo argomento, è possibile fare riferimento alla sezione   <a href="https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#depth-buffer-sharing-hololens" target="_blank">  Depth buffer sharing (HoloLens) della </a> documentazione sulle prestazioni  <a href="https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/performance/perf-getting-started" target="_blank"> di </a> MRTK.

Nella finestra Project Settings (Impostazioni progetto) seleziona **Player (Lettore)**  > **Publishing Settings** (Impostazioni di pubblicazione) e quindi nel campo **Package name** (Nome del pacchetto) immetti un nome appropriato, ad esempio _MRTKTutorials-GettingStarted_:

![Impostazioni di pubblicazione unity con il nome del pacchetto](../images/mr-learning-base/base-02-section5-step2-7.png)

> [!NOTE]
> Il valore di 'Package name' (Nome del pacchetto) è l'identificatore univoco dell'app. Modifica questo identificatore prima di distribuire l'app per evitare di sovrascrivere app installate in precedenza.

> [!TIP]
> Il valore di 'Product Name' (Nome del prodotto) è il nome visualizzato nel menu di avvio di HoloLens. Per semplificare l'individuazione dell'app durante lo sviluppo, anteponi un carattere di sottolineatura al nome in modo che compaia all'inizio dell'elenco.

# <a name="unity-2020--openxr"></a>[Unity 2020 + OpenXR](#tab/openxr)

Dal menu di Unity scegli **Edit** (Modifica) > **Project Settings** (Impostazioni del progetto) per visualizzare la finestra corrispondente:

![Percorso del menu Project Settings... di Unity](../images/mr-learning-base/base-02-section5-step2-1.png)

Nella finestra Project Settings (Impostazioni progetto) selezionare **XR Plug-in Management**  >  **Install XR Plug-in Management (Gestione plug-in XR XR)** per installare Gestione plug-in XR:

![Impostazioni di Unity XR con l'opzione Install XR plug-in management (Installa gestione plug-in XR) selezionata](../images/mr-learning-base/base-02-section5-step2-2.png)

Al termine dell'installazione di Gestione plug-in XR in Unity. Assicurarsi di avere le impostazioni piattaforma UWP (Universal Windows Platform) e selezionare le caselle di controllo **Inizializza XR** all'avvio, **OpenXR** e Microsoft HoloLens **set di** funzionalità.

![Unity XR Settings with add OpenXR and Microsoft HoloLens features selectedd (Impostazioni XR unity con l'aggiunta di funzionalità OpenXR e Microsoft HoloLens selezionate)](../images/mr-learning-base/base-02-section5-step2-2-1-openxr.png)

>[!Important]
>Se accanto al plug-in OpenXR (anteprima) viene visualizzata un'icona di avviso rossa, fare clic sull'icona e selezionare Correggi tutto prima di continuare. Per l'applicazione delle modifiche potrebbe essere necessario riavviare l'editor di Unity.
>![Menu di convalida del progetto OpenXR con tutti i problemi selezionati da risolvere.](../images/mr-learning-base/base-02-section5-step2-openxr-3.png)

Nella barra dei menu nella parte superiore della schermata passare a **Mixed Reality> OpenXR > Apply recommended project settings for HoloLens 2** (Applica le impostazioni di progetto consigliate per HoloLens 2 per ottenere prestazioni migliori dell'app).

![Menu realtà mista con OpenXR e Applica le impostazioni di progetto consigliate per HoloLens 2 selezionato](../images/mr-learning-base/base-02-section5-step2-openxr-2.png)

Al termine dell'importazione dei file necessari in Unity, verrà visualizzata di nuovo la finestra MRTK Project Configurator (Configuratore progetto MRTK). In caso contrario, usa il menu di Unity per aprirla.

Nella finestra MRTK Project Configurator (Configuratore del progetto MRTK) usa l'elenco a discesa **Audio spatializer** (Spazializzatore audio) per selezionare **MS HRTF Spatializer** e quindi fai clic sul pulsante **Apply** (Applica) per applicare l'impostazione:

![Finestra di configurazione di MRTK con le opzioni predefinite selezionate](../images/mr-learning-base/base-02-section5-step2-2-2.png)

> [!TIP]
>L'impostazione della proprietà Audio spatializer (Spazializzatore audio) è facoltativa, ma può migliorare l'esperienza audio nel progetto. Se si imposta questa proprietà su MS HRTF Spatializer, questo plug-in di spazializzatore verrà usato quando la proprietà AudioSource.spatialize di Unity è abilitata. Per altre informazioni su questo argomento, è possibile fare riferimento alle  <a href="https://docs.microsoft.com/windows/mixed-reality/develop/unity/tutorials/unity-spatial-audio-ch1" target="_blank"> esercitazioni sull'audio spaziale</a>.


Nella finestra Project Settings (Impostazioni progetto) seleziona **Player (Lettore)**  > **Publishing Settings** (Impostazioni di pubblicazione) e quindi nel campo **Package name** (Nome del pacchetto) immetti un nome appropriato, ad esempio _MRTKTutorials-GettingStarted_:

![Impostazioni di pubblicazione di Unity](../images/mr-learning-base/base-02-section5-step2-7.png)

> [!NOTE]
> Il valore di 'Package name' (Nome del pacchetto) è l'identificatore univoco dell'app. Modifica questo identificatore prima di distribuire l'app per evitare di sovrascrivere app installate in precedenza.

> [!TIP]
> Il valore di 'Product Name' (Nome del prodotto) è il nome visualizzato nel menu di avvio di HoloLens. Per semplificare l'individuazione dell'app durante lo sviluppo, anteponi un carattere di sottolineatura al nome in modo che compaia all'inizio dell'elenco.

# <a name="legacy-wsa"></a>[Legacy WSA](#tab/wsa)

Dal menu di Unity scegli **Edit** (Modifica) > **Project Settings** (Impostazioni del progetto) per visualizzare la finestra corrispondente:

Nella finestra Project Settings (Impostazioni progetto) seleziona **Player** XR Settings (Impostazioni XR lettore), seleziona la casella di controllo  >   **Virual Reality Supported** (Realtà virtuale supportata), quindi fai clic sull'icona e seleziona Windows Mixed Reality per **+** aggiungere Windows Mixed Reality SDK:

![Unity XR Settings (Impostazioni XR Unity), Windows Mixed Reality SDK selezionato](../images/mr-learning-base/base-02-section5-step2-4.png)

Al termine dell'importazione di Windows Mixed Reality SDK, dovrebbe visualizzarsi di nuovo la finestra MRTK Project Configurator (Configuratore del progetto MRTK). In caso contrario, è possibile aprirlo manualmente dal menu di Unity selezionando **Mixed Reality Toolkit** Utilities Configure Unity Project (Utilità di Mixed Reality Toolkit - Configura progetto  >    >  **Unity)**

Nella finestra MRTK Project Configurator (Configuratore del progetto MRTK) usa l'elenco a discesa **Audio spatializer** (Spazializzatore audio) per selezionare **MS HRTF Spatializer** e quindi fai clic sul pulsante **Apply** (Applica) per applicare l'impostazione:

![Finestra di configurazione di MRTK](../images/mr-learning-base/base-02-section5-step2-5.png)

> [!TIP]
>L'impostazione della proprietà Audio spatializer (Spazializzatore audio) è facoltativa, ma può migliorare l'esperienza audio nel progetto. Se si imposta questa proprietà su MS HRTF Spatializer, questo plug-in di spazializzatore verrà usato quando la proprietà AudioSource.spatialize di Unity è abilitata. Per altre informazioni su questo argomento, vedere le esercitazioni  <a href="//windows/mixed-reality/develop/unity/tutorials/unity-spatial-audio-ch1" target="_blank"> sull'audio spaziale</a>.

Nella finestra Project Settings (Impostazioni progetto) seleziona **Player (Lettore)**  > **XR Settings** (Impostazioni XR) e quindi usa l'elenco a discesa **Depth Format** (Formato profondità) per selezionare **16-bit depth** (Profondità a 16 bit):

![Abilitazione di Unity a 16 profondità](../images/mr-learning-base/base-02-section5-step2-6.png)

> [!TIP]
> La riduzione del formato di profondità a 16 bit è facoltativa, ma consente di migliorare le prestazioni grafiche nel progetto. Per altre informazioni su questo argomento, è possibile fare riferimento alla sezione sulla <a href="/windows/mixed-reality/mrtk-unity/performance/perf-getting-started#single-pass-instanced-rendering" target="_blank">condivisione del buffer di intensità (HoloLens)</a> della documentazione di MRTK relativa alle prestazioni.

Nella finestra Project Settings (Impostazioni progetto) seleziona **Player (Lettore)**  > **Publishing Settings** (Impostazioni di pubblicazione) e quindi nel campo **Package name** (Nome del pacchetto) immetti un nome appropriato, ad esempio _MRTKTutorials-GettingStarted_:

![Impostazioni di pubblicazione di Unity. Nome pacchetto configurato](../images/mr-learning-base/base-02-section5-step2-7.png)

> [!NOTE]
> Il valore di 'Package name' (Nome del pacchetto) è l'identificatore univoco dell'app. Modifica questo identificatore prima di distribuire l'app per evitare di sovrascrivere app installate in precedenza.

> [!TIP]
> Il valore di 'Product Name' (Nome del prodotto) è il nome visualizzato nel menu di avvio di HoloLens. Per semplificare l'individuazione dell'app durante lo sviluppo, anteponi un carattere di sottolineatura al nome in modo che compaia all'inizio dell'elenco.

---
ms.openlocfilehash: 18921520cc9cd7cea3fb6957d3fad823103e3e3d
ms.sourcegitcommit: 4fb961beeebd158e2f65b7c714c5e471454400a3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/30/2021
ms.locfileid: "105983269"
---
# <a name="unity-20192020--windows-xr-plugin"></a>[Plug-in Unity 2019/2020 + Windows XR](#tab/winxr)

Dal menu di Unity scegli **Edit** (Modifica) > **Project Settings** (Impostazioni del progetto) per visualizzare la finestra corrispondente:

![Percorso del menu Project Settings... di Unity](../images/mr-learning-base/base-02-section5-step2-1.png)

Nella finestra Impostazioni progetto selezionare Gestione plug **-in XR**  >  **installa Gestione plug-in** di XR, per installare la gestione dei plug-in XR:

![Area XR Settings di Unity con Windows Mixed Reality SDK selezionato](../images/mr-learning-base/base-02-section5-step2-2.png)

Al termine dell'installazione della gestione dei plug-in di XR in Unity. Assicurarsi di essere in piattaforma UWP (Universal Windows Platform) impostazioni e selezionare la casella di controllo **Inizializza XR all'avvio** e la **realtà mista di Windows** .

![Area XR Settings di Unity con Windows Mixed Reality SDK selezionato](../images/mr-learning-base/base-02-section5-step2-2-1.png)

Al termine dell'importazione di Windows Mixed Reality SDK, dovrebbe visualizzarsi di nuovo la finestra MRTK Project Configurator (Configuratore del progetto MRTK). In caso contrario, usa il menu di Unity per aprirla.

Nella finestra MRTK Project Configurator (Configuratore del progetto MRTK) usa l'elenco a discesa **Audio spatializer** (Spazializzatore audio) per selezionare **MS HRTF Spatializer** e quindi fai clic sul pulsante **Apply** (Applica) per applicare l'impostazione:

![Area XR Settings di Unity con Windows Mixed Reality SDK selezionato](../images/mr-learning-base/base-02-section5-step2-2-2.png)

> [!TIP]
>L'impostazione della proprietà Audio spatializer (Spazializzatore audio) è facoltativa, ma può migliorare l'esperienza audio nel progetto. Se si imposta questa proprietà su MS HRTF Spatializer, questo plug-in di spazializzatore verrà usato quando la proprietà AudioSource.spatialize di Unity è abilitata. Per ulteriori informazioni su questo argomento, è possibile fare riferimento alle  <a href="https://docs.microsoft.com/en-us/windows/mixed-reality/develop/unity/tutorials/unity-spatial-audio-ch1" target="_blank"> esercitazioni audio spaziali</a>.

Nella finestra Impostazioni progetto selezionare **Gestione plug-in XR**  >  impostazioni di runtime di **Windows mixed realtà**  >  , quindi usare l'elenco a discesa **formato buffer di profondità** per selezionare la **profondità a 16 bit:**

![Finestra Project Settings di Unity con il nome del pacchetto configurato](../images/mr-learning-base/base-02-section5-step2-5-1.png)

> [!TIP]
> La riduzione del formato di profondità a 16 bit è facoltativa, ma consente di migliorare le prestazioni grafiche nel progetto. Per ulteriori informazioni su questo argomento, è possibile fare riferimento alla sezione   <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html#depth-buffer-sharing-hololens" target="_blank">  HoloLens (depth buffer sharing) </a> della documentazione  <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html" target="_blank"> sulle prestazioni </a> di MRTK.

Nella finestra Project Settings (Impostazioni progetto) seleziona **Player (Lettore)**  > **Publishing Settings** (Impostazioni di pubblicazione) e quindi nel campo **Package name** (Nome del pacchetto) immetti un nome appropriato, ad esempio _MRTKTutorials-GettingStarted_:

![Finestra Project Settings di Unity con il nome del pacchetto configurato](../images/mr-learning-base/base-02-section5-step2-7.png)

> [!NOTE]
> Il valore di 'Package name' (Nome del pacchetto) è l'identificatore univoco dell'app. Modifica questo identificatore prima di distribuire l'app per evitare di sovrascrivere app installate in precedenza.

> [!TIP]
> Il valore di 'Product Name' (Nome del prodotto) è il nome visualizzato nel menu di avvio di HoloLens. Per semplificare l'individuazione dell'app durante lo sviluppo, anteponi un carattere di sottolineatura al nome in modo che compaia all'inizio dell'elenco.

# <a name="legacy-wsa"></a>[WSA legacy](#tab/wsa)

Dal menu di Unity scegli **Edit** (Modifica) > **Project Settings** (Impostazioni del progetto) per visualizzare la finestra corrispondente:

Nella finestra Impostazioni progetto selezionare **lettore**  >  **XR impostazioni** e selezionare la casella di controllo **realtà virtuale supportata** , quindi fare clic sull' **+** icona e selezionare realtà mista di Windows per aggiungere l'SDK di realtà mista di Windows:

![Area XR Settings di Unity con Windows Mixed Reality SDK selezionato](../images/mr-learning-base/base-02-section5-step2-4.png)

Al termine dell'importazione di Windows Mixed Reality SDK, dovrebbe visualizzarsi di nuovo la finestra MRTK Project Configurator (Configuratore del progetto MRTK). In caso contrario, è possibile aprirlo manualmente dal menu di Unity passando a Utility del **Toolkit di realtà mista**  >    >  **configurare il progetto Unity**

Nella finestra MRTK Project Configurator (Configuratore del progetto MRTK) usa l'elenco a discesa **Audio spatializer** (Spazializzatore audio) per selezionare **MS HRTF Spatializer** e quindi fai clic sul pulsante **Apply** (Applica) per applicare l'impostazione:

![Area XR Settings di Unity con Windows Mixed Reality SDK selezionato](../images/mr-learning-base/base-02-section5-step2-5.png)

> [!TIP]
>L'impostazione della proprietà Audio spatializer (Spazializzatore audio) è facoltativa, ma può migliorare l'esperienza audio nel progetto. Se si imposta questa proprietà su MS HRTF Spatializer, questo plug-in di spazializzatore verrà usato quando la proprietà AudioSource.spatialize di Unity è abilitata. Per ulteriori informazioni su questo argomento, è possibile fare riferimento alle  <a href="//windows/mixed-reality/develop/unity/tutorials/unity-spatial-audio-ch1" target="_blank"> esercitazioni audio spaziali</a>.

Nella finestra Project Settings (Impostazioni progetto) seleziona **Player (Lettore)**  > **XR Settings** (Impostazioni XR) e quindi usa l'elenco a discesa **Depth Format** (Formato profondità) per selezionare **16-bit depth** (Profondità a 16 bit):

![Unity Abilita 16 profondità](../images/mr-learning-base/base-02-section5-step2-6.png)

> [!TIP]
> La riduzione del formato di profondità a 16 bit è facoltativa, ma consente di migliorare le prestazioni grafiche nel progetto. Per ulteriori informazioni su questo argomento, è possibile fare riferimento alla sezione   <a href="/windows/mixed-reality/mrtk-docs/performance/perf-getting-started.md#single-pass-instanced-rendering" target="_blank">  HoloLens (depth buffer sharing) </a> della documentazione  <a href="/windows/mixed-reality/mrtk-docs/performance/perf-getting-started.md#single-pass-instanced-rendering" target="_blank"> sulle prestazioni </a> di MRTK.

Nella finestra Project Settings (Impostazioni progetto) seleziona **Player (Lettore)**  > **Publishing Settings** (Impostazioni di pubblicazione) e quindi nel campo **Package name** (Nome del pacchetto) immetti un nome appropriato, ad esempio _MRTKTutorials-GettingStarted_:

![Finestra Project Settings di Unity con il nome del pacchetto configurato](../images/mr-learning-base/base-02-section5-step2-7.png)

> [!NOTE]
> Il valore di 'Package name' (Nome del pacchetto) è l'identificatore univoco dell'app. Modifica questo identificatore prima di distribuire l'app per evitare di sovrascrivere app installate in precedenza.

> [!TIP]
> Il valore di 'Product Name' (Nome del prodotto) è il nome visualizzato nel menu di avvio di HoloLens. Per semplificare l'individuazione dell'app durante lo sviluppo, anteponi un carattere di sottolineatura al nome in modo che compaia all'inizio dell'elenco.

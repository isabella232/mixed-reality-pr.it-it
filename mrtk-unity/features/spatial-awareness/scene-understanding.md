---
title: Informazioni sulla scena
description: descrive La comprensione della scena in MRTK
author: MaxWang-MS
ms.author: wangmax
ms.date: 05/27/2021
keywords: Unity, HoloLens, HoloLens 2, Realtà mista, sviluppo, MRTK, Scene Understanding
ms.openlocfilehash: 67a8b99a281b6deecd621edb5600578806812d8a
ms.sourcegitcommit: 86fafb3a7ac6a5f60340ae5041619e488223f4f0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/22/2021
ms.locfileid: "112449750"
---
# <a name="scene-understanding"></a>Informazioni sulla scena

[Scene Understanding](/windows/mixed-reality/scene-understanding) restituisce una rappresentazione semantica delle entità della scena e delle relative forme geometriche __HoloLens 2__ (HoloLens 1° generazione non è supportato).

Alcuni casi d'uso previsti di questa tecnologia sono:
* Posizionare gli oggetti sulla superficie più vicina di un certo tipo (ad esempio, parete e pavimento)
* Costruire una rete di navigazione per giochi in stile piattaforma
* Fornire la geometria descrittiva del motore di fisica come quad
* Accelerare lo sviluppo evitando la necessità di scrivere algoritmi simili

Scene Understanding è stato introdotto come __funzionalità sperimentale__ in MRTK 2.6. È integrato in MRTK come [osservatore spaziale](spatial-awareness-getting-started.md#register-observers) denominato [`WindowsSceneUnderstandingObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsSceneUnderstanding.Experimental.WindowsSceneUnderstandingObserver) . Scene Understanding funziona sia con la pipeline XR legacy che con la pipeline XR SDK (sia OpenXR (a partire da MRTK 2.7) che con il plug-in Windows XR. In entrambi i casi viene `WindowsSceneUnderstandingObserver` usato .

> [!NOTE] 
> L'uso di Scene Understanding nella comunicazione remota non è supportato.

## <a name="observer-overview"></a>Panoramica dell'osservatore

Quando richiesto, [`WindowsSceneUnderstandingObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsSceneUnderstanding.Experimental.WindowsSceneUnderstandingObserver) restituirà [SpatialAwarenessSceneObject](xref:Microsoft.MixedReality.Toolkit.Experimental.SpatialAwareness.SpatialAwarenessSceneObject) con attributi utili per l'applicazione per comprenderne l'ambiente circostante. La frequenza di osservazione, il tipo di oggetto restituito (ad esempio parete, pavimento) e altri comportamenti dell'osservatore dipendono dalla configurazione dell'osservatore tramite profilo. Ad esempio, se si desidera la maschera di occlusione, l'osservatore deve essere configurato per generare quad. La scena osservata può essere salvata come file serializzato che può essere caricato in un secondo momento per ricreare la scena in modalità di riproduzione dell'editor.

## <a name="setup"></a>Eseguire la configurazione

> [!IMPORTANT]
> Scene Understanding è supportato solo in HoloLens 2 e Unity 2019.4 e versioni successive.

1. Assicurarsi che la piattaforma sia impostata su UWP nelle impostazioni di compilazione.
1. Acquisire il pacchetto Scene Understanding tramite Lo strumento [di funzionalità di realtà mista](https://aka.ms/MRFeatureTool).

## <a name="using-scene-understanding"></a>Uso della comprensione della scena

Il modo più rapido per iniziare a usare Scene Understanding è quello di controllare la scena di esempio.

### <a name="scene-understanding-sample-scene"></a>Scena di esempio Di comprensione della scena

In Unity usare Esplora progetti per aprire il file di scena in `Examples/Experimental/SceneUnderstanding/Scenes/SceneUnderstandingExample.unity` e premere play!

::: moniker range="< mrtkunity-2021-05"
> [!IMPORTANT]
> Si applica solo a MRTK 2.6.0: quando si usa lo strumento di funzionalità di realtà mista o in caso contrario si esegue l'importazione tramite UPM, importare l'esempio Demos - SpatialAwareness prima di importare l'esempio Experimental - SceneUnderstanding a causa di un problema di dipendenza. Per altre informazioni, vedere questo problema di [GitHub.](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9431)

::: moniker-end
La scena illustra quanto segue:

* Visualizzazione degli oggetti scena osservati con nell'interfaccia utente dell'applicazione per la configurazione dell'osservatore
* Script `DemoSceneUnderstandingController` di esempio che illustra come modificare le impostazioni dell'osservatore e restare in ascolto degli eventi pertinenti
* Salvataggio dei dati della scena nel dispositivo per lo sviluppo offline
* Caricamento dei dati della scena salvati in precedenza (file con estensione bytes) per supportare il flusso di lavoro di sviluppo nell'editor

> [!IMPORTANT]
> Per impostazione `ShouldLoadFromFile` predefinita, la proprietà dell'osservatore è impostata su false. Per visualizzare la visualizzazione di una stanza di esempio [](#configuring-the-observer-service) serializzata, vedere la sezione configurazione del servizio osservatore riportata di seguito e impostare la proprietà su true nell'editor.
::: moniker range="< mrtkunity-2021-05"

> [!NOTE] 
> La scena di esempio è basata sulla pipeline XR legacy. Se si usa la pipeline di XR SDK, è necessario modificare i profili di conseguenza. Il profilo del sistema di comprensione della scena ( ) e `DemoSceneUnderstandingSystemProfile` i profili scene understanding observer ( e ) funzionano per `DefaultSceneUnderstandingObserverProfile` `DemoSceneUnderstandingObserverProfile` entrambe le pipeline.
::: moniker-end
::: moniker range="= mrtkunity-2021-05"

> [!NOTE] 
> La scena di esempio registra un `There is no active AsyncCoroutineRunner when an action is posted.` avviso in determinate circostanze a causa dell'ordine di inizializzazione/esecuzione del thread. Se è possibile verificare che il componente sia collegato al GameObject "Demo Controller" e che il `AsyncCoroutineRunner` componente/GameObject rimanga abilitato/attivo nella scena (caso predefinito), l'avviso può essere ignorato in tutta sicurezza. **Tuttavia, quando si crea una nuova scena con Scene Understanding, assicurarsi di creare un GameObject vuoto nella radice e associare lo script, in caso contrario La comprensione della scena potrebbe non `AsyncCoroutineRunner` funzionare correttamente.**
::: moniker-end

#### <a name="configuring-the-observer-service"></a>Configurazione del servizio observer

Selezionare l'oggetto gioco "MixedRealityToolkit" e controllare il controllo.

![Informazioni sulla scena sulla posizione nella gerarchia](../images/spatial-awareness/MRTKHierarchy.png)

![Posizione MRTK nel controllo](../images/spatial-awareness/MRTKLocation.png)

Queste opzioni consentono di configurare `WindowsSceneUnderstandingObserver` .

### <a name="example-script"></a>Script di esempio

Lo script di esempio _DemoSceneUnderstandingController.cs_ illustra i concetti principali relativi all'uso del servizio Scene Understanding.

* Sottoscrizione agli eventi di Scene Understanding
* Gestione degli eventi di comprensione della scena
* Configurazione di in `WindowsSceneUnderstandingObserver` fase di esecuzione

Gli interruttori sul pannello nella scena modificano il comportamento dell'osservatore di comprensione della scena chiamando le funzioni pubbliche di questo script di esempio.

Attivando *Instantiate Prefabs*, verrà illustrata la creazione di oggetti che si adattano a tutti [Gli oggetti SpatialAwarenessSceneObject,](xref:Microsoft.MixedReality.Toolkit.Experimental.SpatialAwareness.SpatialAwarenessSceneObject)raccolti in modo ordinato in un oggetto padre.

![opzioni del controller demo](../images/spatial-awareness/Controller.png)

### <a name="built-app-notes"></a>Note sull'app compilate

Compilare e distribuire in HoloLens nel modo standard. Dopo l'esecuzione, dovrebbe essere visualizzato un certo numero di pulsanti da riprodurre con le funzionalità.

Si noti che esistono alcuni problemi di esecuzione di query all'osservatore. Errore di configurazione di una richiesta di recupero nel payload dell'evento che non contiene i dati previsti. Ad esempio, se non si richiede quad, non saranno presenti trame di maschera di occlusione. Analogamente, non verrà visualizzata alcuna mesh mondiale se l'osservatore non è configurato per richiedere mesh. Lo `DemoSceneUnderstandingController` script si occupa di alcune di queste dipendenze, ma non di tutte.

È possibile accedere ai file di scena salvati tramite il [portale dei dispositivi](/windows/mixed-reality/using-the-windows-device-portal) all'indirizzo `User Folders/LocalAppData/[APP_NAME]/LocalState/PREFIX_yyyyMMdd_hhmmss.bytes` . Questi file di scena possono essere usati nell'editor specificandoli nel profilo osservatore disponibile nel controllo.

![Portale di dispositivi percorso del file di byte](../images/spatial-awareness/BytesInDevicePortal.png)

![Byte della scena serializzati nell'osservatore](../images/spatial-awareness/BytesLocationInObserver.png)

## <a name="see-also"></a>Vedere anche

* [Panoramica della comprensione della scena](/windows/mixed-reality/scene-understanding)
* [Panoramica di Scene Understanding SDK](/windows/mixed-reality/scene-understanding-sdk)
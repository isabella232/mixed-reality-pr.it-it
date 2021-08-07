---
title: Osservatore di comprensione della scena
description: descrive Scene Understanding in MRTK
author: MaxWang-MS
ms.author: wangmax
ms.date: 05/27/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, Scene Understanding
ms.openlocfilehash: bf6ceaf98f239e725de3e084bd1ca96a63abc6c28f2434e8ae84ba3f70ee025b
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115214363"
---
# <a name="scene-understanding-observer"></a>Osservatore di comprensione della scena

[Scene Understanding](/windows/mixed-reality/scene-understanding) restituisce una rappresentazione semantica delle entità della scena e delle relative forme geometriche __HoloLens 2__ (HoloLens prima generazione non è supportata).

Di seguito sono riportati alcuni casi d'uso previsti di questa tecnologia:
* Posizionare gli oggetti sulla superficie più vicina di un determinato tipo (ad esempio, le pareti e il piano)
* Costruire la mesh di spostamento per i giochi in stile piattaforma
* Fornire la geometria descrittiva del motore di fisica come quad
* Accelerare lo sviluppo evitando la necessità di scrivere algoritmi simili

Scene Understanding è stato introdotto come __funzionalità sperimentale__ in MRTK 2.6. È integrato in MRTK come [osservatore spaziale](spatial-awareness-getting-started.md#register-observers) denominato [`WindowsSceneUnderstandingObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsSceneUnderstanding.Experimental.WindowsSceneUnderstandingObserver) . Scene Understanding funziona sia con la pipeline legacy XR che con la pipeline XR SDK (sia OpenXR (a partire da MRTK 2.7) che con Windows XR Plugin. In entrambi i casi `WindowsSceneUnderstandingObserver` viene usato .

> [!NOTE] 
> L'uso di Scene Understanding nella comunicazione remota non è supportato.

## <a name="observer-overview"></a>Panoramica dell'osservatore

Quando richiesto, [`WindowsSceneUnderstandingObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsSceneUnderstanding.Experimental.WindowsSceneUnderstandingObserver) restituirà [SpatialAwarenessSceneObject](xref:Microsoft.MixedReality.Toolkit.Experimental.SpatialAwareness.SpatialAwarenessSceneObject) con attributi utili per l'applicazione per comprendere l'ambiente circostante. La frequenza di osservazione, il tipo di oggetto restituito (ad esempio, le pareti, il piano) e altri comportamenti dell'osservatore dipendono dalla configurazione dell'osservatore tramite il profilo. Ad esempio, se si desidera la maschera di occlusione, l'osservatore deve essere configurato per generare quad. La scena osservata può essere salvata come file serializzato che può essere caricato in un secondo momento per ricreare la scena in modalità di riproduzione dell'editor.

## <a name="setup"></a>Eseguire la configurazione

> [!IMPORTANT]
> Scene Understanding è supportato solo in HoloLens 2 e Unity 2019.4 e versioni successive.

1. Verificare che la piattaforma sia impostata su UWP nelle impostazioni di compilazione.
1. Acquisire il pacchetto Scene Understanding tramite [lo strumento di funzionalità di realtà mista](https://aka.ms/MRFeatureTool).

## <a name="using-scene-understanding"></a>Uso di Scene Understanding

Il modo più rapido per iniziare a usare Scene Understanding è vedere la scena di esempio.

### <a name="scene-understanding-sample-scene"></a>Scena di esempio scene Understanding

In Unity usare l'Project Explorer per aprire il file della scena in `Examples/Experimental/SceneUnderstanding/Scenes/SceneUnderstandingExample.unity` e premere play!

::: moniker range="< mrtkunity-2021-05"
> [!IMPORTANT]
> Si applica solo a MRTK 2.6.0: quando si usa lo strumento di funzionalità di realtà mista o si importa in altro modo tramite UPM, importare l'esempio Demos - SpatialAwareness prima di importare l'esempio Experimental - SceneUnderstanding a causa di un problema di dipendenza. Per altre [informazioni, GitHub questo problema.](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9431)

::: moniker-end
La scena illustra quanto segue:

* Visualizzazione degli oggetti scena osservati con nell'interfaccia utente dell'applicazione per la configurazione dell'osservatore
* Script `DemoSceneUnderstandingController` di esempio che illustra come modificare le impostazioni dell'osservatore e restare in ascolto degli eventi pertinenti
* Salvataggio dei dati della scena nel dispositivo per lo sviluppo offline
* Caricamento dei dati della scena salvati in precedenza (file con estensione bytes) per supportare il flusso di lavoro di sviluppo nell'editor

> [!IMPORTANT]
> Per impostazione `ShouldLoadFromFile` predefinita, la proprietà dell'osservatore è impostata su false. Per visualizzare una stanza di esempio serializzata, vedere [](#configuring-the-observer-service) la sezione configurazione del servizio osservatore riportata di seguito e impostare la proprietà su true nell'editor.
::: moniker range="< mrtkunity-2021-05"

> [!NOTE] 
> La scena di esempio è basata sulla pipeline XR legacy. Se si usa la pipeline XR SDK, è necessario modificare i profili di conseguenza. Il profilo Scene Understanding Spatial Awareness System ( ) e i profili `DemoSceneUnderstandingSystemProfile` Scene Understanding Observer ( e ) funzionano per `DefaultSceneUnderstandingObserverProfile` `DemoSceneUnderstandingObserverProfile` entrambe le pipeline.
::: moniker-end
::: moniker range="= mrtkunity-2021-05"

> [!NOTE] 
> La scena di esempio registra un avviso in determinate circostanze a `There is no active AsyncCoroutineRunner when an action is posted.` causa dell'ordine di inizializzazione/esecuzione del thread. Se puoi verificare che il componente sia collegato al GameObject "Demo Controller" e che il componente/GameObject rimanga abilitato/attivo nella scena (caso predefinito), l'avviso può essere tranquillamente `AsyncCoroutineRunner` ignorato. **Tuttavia, quando crei una nuova scena con Scene Understanding, assicurati di creare un GameObject vuoto nella radice e collega alla scena lo script, altrimenti Scene Understanding potrebbe non funzionare `AsyncCoroutineRunner` correttamente.**
::: moniker-end

#### <a name="configuring-the-observer-service"></a>Configurazione del servizio observer

Selezionare l'oggetto gioco "MixedRealityToolkit" e controllare il controllo.

![comprensione della posizione della scena nella gerarchia](../images/spatial-awareness/MRTKHierarchy.png)

![Posizione di MRTK in Inspector](../images/spatial-awareness/MRTKLocation.png)

Queste opzioni consentiranno a un utente di configurare `WindowsSceneUnderstandingObserver` .

### <a name="example-script"></a>Script di esempio

Lo script di _esempio DemoSceneUnderstandingController.cs_ illustra i concetti principali dell'uso del servizio Scene Understanding.

* Sottoscrizione di eventi scene understanding
* Gestione degli eventi di comprensione della scena
* Configurazione di in `WindowsSceneUnderstandingObserver` fase di esecuzione

Gli interruttori sul pannello nella scena modificano il comportamento dell'osservatore di comprensione della scena chiamando le funzioni pubbliche di questo script di esempio.

Attivando *Instantiate Prefabs*, verrà illustrata la creazione di oggetti che si adattano a tutti [gli SpatialAwarenessSceneObject,](xref:Microsoft.MixedReality.Toolkit.Experimental.SpatialAwareness.SpatialAwarenessSceneObject)raccolti in modo accurato in un oggetto padre.

![opzioni del controller demo](../images/spatial-awareness/Controller.png)

### <a name="built-app-notes"></a>Note sull'app compilata

Compilare e distribuire in HoloLens nel modo standard. Dopo l'esecuzione, dovrebbe apparire una serie di pulsanti per la riproduzione con le funzionalità.

Si noti che esistono alcuni problemi nell'esecuzione di query all'osservatore. Una configurazione errata di una richiesta di recupero ha come risultato il payload dell'evento che non contiene i dati previsti. Ad esempio, se non si richiedono quad, non saranno presenti trame maschera di occlusione. Analogamente, non verrà visualizzata alcuna mesh mondiale se l'osservatore non è configurato per richiedere mesh. Lo `DemoSceneUnderstandingController` script si occupa di alcune di queste dipendenze, ma non di tutte.

I file di scena salvati sono accessibili tramite il [portale dei dispositivi all'indirizzo](/windows/mixed-reality/using-the-windows-device-portal) `User Folders/LocalAppData/[APP_NAME]/LocalState/PREFIX_yyyyMMdd_hhmmss.bytes` . Questi file di scena possono essere usati nell'editor specificandoli nel profilo osservatore trovato nel controllo.

![Portale di dispositivi percorso del file di byte](../images/spatial-awareness/BytesInDevicePortal.png)

![Byte della scena serializzati nell'osservatore](../images/spatial-awareness/BytesLocationInObserver.png)

## <a name="see-also"></a>Vedere anche

* [Cenni preliminari sulla comprensione della scena](/windows/mixed-reality/scene-understanding)
* [Panoramica di Scene Understanding SDK](/windows/mixed-reality/scene-understanding-sdk)

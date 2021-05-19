---
title: Informazioni sulla scena
description: descrive Scene Understanding in MRTK
author: MaxWang-MS
ms.author: wangmax
ms.date: 03/02/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, Scene Understanding
ms.openlocfilehash: ac90359a71267dc64e659f446f35ec2510c42599
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143884"
---
# <a name="scene-understanding"></a>Informazioni sulla scena

[Scene Understanding](/windows/mixed-reality/scene-understanding) restituisce una rappresentazione semantica delle entità della scena e delle relative forme geometriche __in__ HoloLens 2 (HoloLens di prima generazione non è supportato).

Di seguito sono riportati alcuni casi d'uso previsti di questa tecnologia:
* Posizionare gli oggetti sulla superficie più vicina di un determinato tipo (ad esempio, le pareti e il piano)
* Costruire la mesh di spostamento per i giochi in stile piattaforma
* Fornire la geometria descrittiva del motore di fisica come quad
* Accelerare lo sviluppo evitando la necessità di scrivere algoritmi simili

Scene Understanding è disponibile come funzionalità __sperimentale__ a partire da MRTK 2.6. È integrato in MRTK come [osservatore spaziale](spatial-awareness-getting-started.md#register-observers) denominato [`WindowsSceneUnderstandingObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsSceneUnderstanding.Experimental.WindowsSceneUnderstandingObserver) . Scene Understanding funziona sia con la pipeline XR legacy che con la pipeline XR SDK. In entrambi i casi `WindowsSceneUnderstandingObserver` viene usato .

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

In Unity usare Project Explorer (Esplora progetti) per aprire il file della scena in `Examples/Experimental/SceneUnderstanding/Scenes/SceneUnderstandingExample.unity` e premere play!

> [!IMPORTANT]
> Quando si usa lo strumento di funzionalità di realtà mista o si esegue un'importazione tramite UPM, importare l'esempio Demos - SpatialAwareness prima di importare l'esempio Experimental - SceneUnderstanding a causa di un problema di dipendenza. Per altre informazioni, vedere questo problema di [GitHub.](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9431)

La scena illustra quanto segue:

* Visualizzazione degli oggetti scena osservati con nell'interfaccia utente dell'applicazione per la configurazione dell'osservatore
* Script `DemoSceneUnderstandingController` di esempio che illustra come modificare le impostazioni dell'osservatore e restare in ascolto degli eventi pertinenti
* Salvataggio dei dati della scena nel dispositivo per lo sviluppo offline
* Caricamento dei dati della scena salvati in precedenza (file con estensione bytes) per supportare il flusso di lavoro di sviluppo nell'editor

> [!NOTE] 
> La scena di esempio è basata sulla pipeline XR legacy. Se si usa la pipeline XR SDK, è necessario modificare i profili di conseguenza. Il profilo scene Understanding Spatial Awareness System ( ) e `DemoSceneUnderstandingSystemProfile` i profili Scene Understanding Observer ( e ) funzionano per `DefaultSceneUnderstandingObserverProfile` `DemoSceneUnderstandingObserverProfile` entrambe le pipeline.

#### <a name="configuring-the-observer-service"></a>Configurazione del servizio observer

Selezionare l'oggetto gioco "MixedRealityToolkit" e controllare il controllo.

![comprensione della posizione della scena nella gerarchia](../images/spatial-awareness/MRTKHierarchy.png)

![Posizione di MRTK in Inspector](../images/spatial-awareness/MRTKLocation.png)

Queste opzioni consentiranno a un utente di configurare `WindowsSceneUnderstandingObserver` .

### <a name="example-script"></a>Script di esempio

Lo script di _esempio DemoSceneUnderstandingController.cs_ illustra i concetti principali relativi all'uso del servizio Scene Understanding.

* Sottoscrizione di eventi scene understanding
* Gestione degli eventi di comprensione della scena
* Configurazione di in `WindowsSceneUnderstandingObserver` fase di esecuzione

Gli interruttori sul pannello nella scena modificano il comportamento dell'osservatore di comprensione della scena chiamando le funzioni pubbliche di questo script di esempio.

L'attivazione di Instantiate Prefabs (Crea istanze di *prefab)* illustra la creazione di oggetti che si adattano a tutti [gli spatialAwarenessSceneObject,](xref:Microsoft.MixedReality.Toolkit.Experimental.SpatialAwareness.SpatialAwarenessSceneObject)raccolti in modo accurato in un oggetto padre.

![opzioni del controller demo](../images/spatial-awareness/Controller.png)

### <a name="built-app-notes"></a>Note sull'app compilata

Compilare e distribuire in HoloLens in modo standard. Dopo l'esecuzione, dovrebbe apparire una serie di pulsanti per la riproduzione con le funzionalità.

Si noti che esistono alcuni problemi nell'esecuzione di query all'osservatore. Una configurazione errata di una richiesta di recupero ha come risultato il payload dell'evento che non contiene i dati previsti. Ad esempio, se non si richiedono quad, non saranno presenti trame maschera di occlusione. Analogamente, non verrà visualizzata alcuna mesh mondiale se l'osservatore non è configurato per richiedere mesh. Lo `DemoSceneUnderstandingController` script si occupa di alcune di queste dipendenze, ma non di tutte.

I file di scena salvati sono accessibili tramite il [portale dei dispositivi all'indirizzo](/windows/mixed-reality/using-the-windows-device-portal) `User Folders/LocalAppData/[APP_NAME]/LocalState/PREFIX_yyyyMMdd_hhmmss.bytes` . Questi file di scena possono essere usati nell'editor specificandoli nel profilo osservatore trovato nel controllo.

![Portale di dispositivi percorso del file di byte](../images/spatial-awareness/BytesInDevicePortal.png)

![Byte della scena serializzati nell'osservatore](../images/spatial-awareness/BytesLocationInObserver.png)

## <a name="see-also"></a>Vedere anche

* [Panoramica del mapping spaziale WMR](/windows/mixed-reality/scene-understanding)
* [Panoramica del mapping spaziale WMR](/windows/mixed-reality/scene-understanding-sdk)
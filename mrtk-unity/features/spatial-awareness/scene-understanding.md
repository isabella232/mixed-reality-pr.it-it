---
title: SceneUnderstanding
description: descrive la comprensione della scena in MRTK
author: MaxWang-MS
ms.author: wangmax
ms.date: 03/02/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, comprensione della scena
ms.openlocfilehash: 991c8152baa138d241b0454d08de267eeaefcb05
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2021
ms.locfileid: "104696158"
---
# <a name="scene-understanding"></a>Comprensione della scena

La [comprensione della scena](https://docs.microsoft.com/windows/mixed-reality/scene-understanding) restituisce una rappresentazione semantica delle entità della scena, oltre ai moduli geometrici in __HoloLens 2__ (HoloLens 1st Gen non è supportata).

Alcuni casi d'uso previsti di questa tecnologia sono:
* Posizionare oggetti sulla superficie più vicina di un determinato tipo (ad esempio, Wall e floor)
* Costruisci NAV-mesh per giochi in stile piattaforma
* Fornire la geometria intuitiva del motore di fisica come Quad
* Accelera lo sviluppo evitando la necessità di scrivere algoritmi simili

La comprensione della scena è disponibile come funzionalità __sperimentale__ a partire da MRTK 2,6. È integrato in MRTK come [osservatore spaziale](spatial-awareness-getting-started.md#register-observers) chiamato [`WindowsSceneUnderstandingObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsSceneUnderstanding.Experimental.WindowsSceneUnderstandingObserver) . La comprensione delle scene funziona sia con la pipeline XR legacy che con la pipeline SDK XR. In entrambi i casi `WindowsSceneUnderstandingObserver` viene usato.

## <a name="observer-overview"></a>Panoramica di Observer

Quando viene richiesto, [`WindowsSceneUnderstandingObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsSceneUnderstanding.Experimental.WindowsSceneUnderstandingObserver) restituirà [SpatialAwarenessSceneObject](xref:Microsoft.MixedReality.Toolkit.Experimental.SpatialAwareness.SpatialAwarenessSceneObject) con attributi utili per l'applicazione per comprenderne l'ambiente. La frequenza di osservazione, il tipo di oggetto restituito (ad esempio, Wall, floor) e altri comportamenti osservatore dipendono dalla configurazione dell'Observer tramite il profilo. Ad esempio, se si desidera la maschera di occlusione, è necessario configurare Observer per generare quad. La scena osservata può essere salvata come file serializzato che è possibile caricare in un secondo momento per ricreare la scena in modalità di riproduzione dell'editor.

## <a name="setup"></a>Configurazione

> [!IMPORTANT]
> La comprensione della scena è supportata solo in HoloLens 2 e Unity 2019,4 e versioni successive.

1. Verificare che la piattaforma sia impostata su UWP nelle impostazioni di compilazione.
1. Acquisire la scena informazioni sul pacchetto tramite [lo strumento funzionalità di realtà mista](https://aka.ms/MRFeatureTool).

## <a name="using-scene-understanding"></a>Uso della comprensione della scena

Il modo più rapido per iniziare a comprendere la scena è vedere la scena di esempio.

### <a name="scene-understanding-sample-scene"></a>Scena di esempio per la comprensione della scena

In Unity usare Esplora progetti per aprire il file della scena in `Examples/Experimental/SceneUnderstanding/Scenes/SceneUnderstandingExample.unity` e premere Play.

> [!IMPORTANT]
> Quando si usa lo strumento della funzionalità di realtà mista o si importa in altro modo tramite UPM, importare l'esempio Demos-SpatialAwareness prima di importare l'esempio Experimental-SceneUnderstanding a causa di un problema di dipendenza. Per ulteriori informazioni, vedere [questo problema di GitHub](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9431) .

La scena mostra quanto segue:

* Visualizzazione degli oggetti scena osservati con nell'interfaccia utente dell'applicazione per la configurazione dell'Observer
* Script di esempio `DemoSceneUnderstandingController` che illustra come modificare le impostazioni di Observer e ascoltare gli eventi rilevanti
* Salvataggio dei dati della scena nel dispositivo per lo sviluppo offline
* Caricamento dei dati della scena salvati in precedenza (file con estensione byte) per supportare il flusso di lavoro di sviluppo in-Editor

> [!NOTE] 
> La scena di esempio è basata sulla pipeline XR legacy. Se si usa la pipeline di XR SDK è necessario modificare i profili di conseguenza. La scena fornita informazioni sul profilo del sistema di riconoscimento spaziale ( `DemoSceneUnderstandingSystemProfile` ) e la scena informazioni sui profili Observer ( `DefaultSceneUnderstandingObserverProfile` e `DemoSceneUnderstandingObserverProfile` ) funzionano per entrambe le pipeline.

#### <a name="configuring-the-observer-service"></a>Configurazione del servizio Observer

Selezionare l'oggetto del gioco ' MixedRealityToolkit ' e controllare il controllo.

![posizione di comprensione della scena nella gerarchia](../images/spatial-awareness/MRTKHierarchy.png)

![Posizione MRTK in Inspector](../images/spatial-awareness/MRTKLocation.png)

Queste opzioni consentiranno di configurare il `WindowsSceneUnderstandingObserver` .

### <a name="example-script"></a>Script di esempio

Lo script di esempio _DemoSceneUnderstandingController. cs_ illustra i principali concetti relativi all'uso del servizio di informazioni sulla scena.

* Sottoscrizione degli eventi di comprensione della scena
* Gestione degli eventi di comprensione della scena
* Configurazione `WindowsSceneUnderstandingObserver` di in fase di esecuzione

Gli interruttori sul pannello nella scena modificano il comportamento dell'osservatore della scena, chiamando le funzioni pubbliche di questo script di esempio.

Quando si attiva la creazione di *un'istanza* dei predicati, viene illustrata la creazione di oggetti che si adattano a tutti [SpatialAwarenessSceneObject](xref:Microsoft.MixedReality.Toolkit.Experimental.SpatialAwareness.SpatialAwarenessSceneObject), raccolti in modo accurato in un oggetto padre.

![opzioni del controller demo](../images/spatial-awareness/Controller.png)

### <a name="built-app-notes"></a>Note app compilate

Compilare e distribuire in HoloLens in modo standard. Una volta eseguito, è necessario che venga visualizzato un numero di pulsanti per riprodurre le funzionalità.

Si noti che sono presenti alcune cadute nell'esecuzione di query nell'Observer. La configurazione errata di una richiesta di recupero genera il payload dell'evento che non contiene i dati previsti. Se, ad esempio, non è richiesta la presenza di quad, non sarà presente alcuna trama della maschera di occlusione. Analogamente, non verrà visualizzata alcuna mesh mondiale se l'Observer non è configurato per richiedere mesh. Lo `DemoSceneUnderstandingController` script si occupa di alcune di queste dipendenze, ma non di tutte.

È possibile accedere ai file di scena salvati tramite il [portale del dispositivo](https://docs.microsoft.com/windows/mixed-reality/using-the-windows-device-portal) all'indirizzo `User Folders/LocalAppData/[APP_NAME]/LocalState/PREFIX_yyyyMMdd_hhmmss.bytes` . Questi file di scena possono essere usati nell'editor specificando tali file nel profilo Observer trovato nel controllo.

![Percorso del file di byte del portale del dispositivo](../images/spatial-awareness/BytesInDevicePortal.png)

![Byte della scena serializzati nell'Observer](../images/spatial-awareness/BytesLocationInObserver.png)

## <a name="see-also"></a>Vedere anche

* https://docs.microsoft.com/windows/mixed-reality/scene-understanding
* https://docs.microsoft.com/windows/mixed-reality/scene-understanding-sdk

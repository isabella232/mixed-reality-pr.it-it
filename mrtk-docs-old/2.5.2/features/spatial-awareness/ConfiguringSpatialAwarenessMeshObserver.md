---
title: ConfiguringSpatialAwarenessMeshObserver
description: Come configurare l'osservatore della rete spaziale predefinita in MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: 0cc91c2440bacd7e4c5fdbb97f1aff15790478ec
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2021
ms.locfileid: "104690461"
---
# <a name="configuring-mesh-observers-for-device"></a>Configurazione degli osservatori mesh per il dispositivo

In questa guida viene illustrata la configurazione di un Observer mesh spaziale predefinito in MRTK che supporta la piattaforma di realtà mista di Windows (ad esempio HoloLens). L'implementazione predefinita fornita da Mixed Reality Toolkit è la classe [WindowsMixedRealitySpatialMeshObserver](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver) . Molte delle proprietà in questo articolo si applicano anche ad altre [implementazioni di Observer personalizzate](CreateDataProvider.md).

## <a name="profile-settings"></a>Impostazioni del profilo

I due elementi seguenti devono essere definiti per primi quando si configura un profilo osservatore mesh spaziale per il [sistema di riconoscimento spaziale](SpatialAwarenessGettingStarted.md).

1. Implementazione del tipo Observer concreto
1. elenco delle piattaforme supportate per l'esecuzione di questo Observer

> [!NOTE]
> Tutti gli osservatori devono estendere l'interfaccia [IMixedRealitySpatialAwarenessObserver](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver) .

![Impostazioni del profilo generale dell'osservatore mesh](../images/spatial-awareness/SpatialAwarenessMeshObserverProfile_TypesPlatforms.png)

### <a name="general-settings"></a>Impostazioni generali

![Impostazioni generali dell'osservatore mesh](../images/spatial-awareness/MeshObserverGeneralSettings.png)

**Comportamento di avvio**

Il comportamento di avvio specifica se l'Observer inizierà l'esecuzione quando ne viene creata la prima istanza. Le due opzioni sono:

* *Avvio automatico* : valore predefinito in base al quale l'Observer inizierà l'operazione dopo l'inizializzazione
* *Avvio manuale* : l'Observer rimarrà in attesa di essere indirizzato all'avvio

Se si usa l' *avvio manuale*, è necessario [riprenderle e sospenderle in fase di esecuzione tramite codice](UsageGuide.md#starting-and-stopping-mesh-observation).

**Intervallo di aggiornamento**

Tempo, in secondi, tra le richieste alla piattaforma per aggiornare i dati di rete spaziale. I valori tipici sono compresi nell'intervallo tra 0,1 e 5,0 secondi.

**Osservatore stazionario**

Indica se l'osservatore deve rimanere fisso o se deve essere spostato e aggiornato con l'utente. Se true, la *forma Observer* con volume definito dagli *extent di osservazione* rimarrà all'origine all'avvio. Se false, lo spazio Observer seguirà l'intestazione dell'utente come origine della forma.

Non verranno calcolati i dati mesh per nessuna area fisica all'esterno dello spazio Observer, come definito dalle proprietà seguenti: *è Stazional Observer*, * Observer Shape * * ed extent di *osservazione*.

**Forma Observer**

La forma Observer definisce il tipo di volume che l'osservatore mesh userà per osservare le maglie. Le opzioni supportate sono:

* *Cubo allineato asse* : forma rettangolare che rimane allineata con gli assi del sistema di coordinate globale, come determinato all'avvio dell'applicazione.
* *Cubo allineato all'utente* : forma rettangolare che ruota per l'allineamento con il sistema di coordinate locale degli utenti.
* *Sphere* : un volume sferico con un centro nell'origine dello spazio globale. Il valore X della proprietà *extent di osservazione* verrà usato come raggio della sfera.

**Extent di osservazione**

Gli extent di osservazione definiscono la distanza dal punto di osservazione in cui verranno osservate le maglie.

### <a name="physics-settings"></a>Impostazioni di fisica

![Impostazioni fisiche osservatore mesh](../images/spatial-awareness/MeshObserverPhysicsSettings.png)

**Livello di fisica**

Livello di fisica in cui verranno inseriti gli oggetti mesh spaziali per interagire con i sistemi di Unity e RayCast.

> [!NOTE]
> Il Toolkit di realtà mista riserva il *livello 31* per impostazione predefinita per l'uso da parte degli osservatori di consapevolezza spaziale.

**Ricalcola normali**

Specifica se l'osservatore mesh ricalcolerà le normalità della mesh che segue l'osservazione. Questa impostazione è disponibile per garantire che le applicazioni ricevano mesh contenenti dati normali validi sulle piattaforme che non le restituiscono con mesh.

### <a name="level-of-detail-settings"></a>Livello di impostazioni dettaglio

![Livello di osservazione mesh delle impostazioni dei dettagli](../images/spatial-awareness/MeshObserverLevelOfDetailSettings.png)

**Livello di dettaglio**

Specifica il livello di dettaglio (LOD) dei dati di mesh spaziali. I valori attualmente definiti sono grossolani, fini e personalizzati.

* *Grossolano* : pone un minore effetto sulle prestazioni dell'applicazione ed è un'ottima scelta per la ricerca di navigazione/piano.

* Impostazione con bilanciamento del *media* spesso utile per le esperienze che analizzano continuamente l'ambiente sia per funzionalità di grandi dimensioni, pavimenti che muri, oltre ai dettagli sull'occlusione.

* Con *precisione* , in genere si ha un maggiore effetto sulle prestazioni dell'applicazione ed è un'ottima opzione per le mesh di occlusione.

* *Personalizzata* : richiede all'applicazione di specificare la proprietà del *contatore triangoli/cubi* e consente alle applicazioni di ottimizzare l'accuratezza e l'effetto sulle prestazioni dell'osservatore mesh spaziale.

> [!NOTE]
> Non è garantito che tutti i valori dei *contatori triangoli/cubici* siano rispettati da tutte le piattaforme. La sperimentazione e la profilatura sono consigliate quando si usa un valore LOD personalizzato.

**Triangoli per misuratore cubico**

Valido quando si usa l'impostazione *personalizzata* per la proprietà **livello di dettaglio** e specifica la densità del triangolo per la mesh spaziale.

### <a name="display-settings"></a>Impostazioni schermo

![Impostazioni di visualizzazione Mesh Observer](../images/spatial-awareness/MeshObserverDisplaySettings.png)

**Opzione di visualizzazione**

Specifica la modalità di visualizzazione delle mesh spaziali da parte dell'osservatore. I valori supportati sono:

* *None* -Observer non eseguirà il rendering della mesh
* *Visible* : i dati mesh saranno visibili usando il *materiale visibile*
* *Occlusione* : i dati mesh verranno occluderei in scena usando il *materiale di occlusione*

![Selezionare l'implementazione del sistema di riconoscimento spaziale](../images/spatial-awareness/MRTK_SpatialAwareness_DisplayOptions.jpg)

Gli osservatori spaziali possono essere [ripresi o sospesi in fase di esecuzione tramite codice.](UsageGuide.md#starting-and-stopping-mesh-observation)

> [!WARNING]
> L'impostazione dell' *opzione di visualizzazione* su *None* **non impedisce l'** esecuzione dell'Observer. Se si desidera arrestare tutti gli osservatori, le applicazioni dovranno sospendere tutti gli osservatori tramite [`CoreServices.SpatialAwareness.SuspendObservers()`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessSystem.SuspendObservers)

**Materiale visibile**

Indica il materiale da usare quando si visualizza la mesh spaziale.

**Materiale occlusione**

Indica il materiale da usare per fare in modo che la mesh spaziale occludere gli ologrammi.

## <a name="see-also"></a>Vedi anche

* [Sistema di riconoscimento spaziale](SpatialAwarenessGettingStarted.md)
* [Configurazione del sistema di riconoscimento spaziale tramite codice](UsageGuide.md)
* [Documentazione dell'API IMixedRealitySpatialAwarenessObserver](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver)
* [Documentazione dell'API IMixedRealitySpatialAwarenessMeshObserver](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessMeshObserver)
* [Documentazione dell'API BaseSpatialObserver](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.BaseSpatialObserver)

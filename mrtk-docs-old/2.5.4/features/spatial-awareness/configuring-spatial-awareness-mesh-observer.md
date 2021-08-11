---
title: ConfigurazioneSpatialAwarenessMeshObserver
description: Come configurare l'osservatore di mesh spaziale predefinito in MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: 6ba7263b2c6eac703d62ec2533409587a2fbb05a97edeb1f295753e4e8882ed3
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115224003"
---
# <a name="configuring-mesh-observers-for-device"></a>Configurazione degli osservatori mesh per il dispositivo

Questa guida illustra in modo guidato la configurazione dell'osservatore di mesh spaziale predefinito in MRTK che supporta la piattaforma Windows Mixed Reality (ad esempio HoloLens). L'implementazione predefinita fornita dal Toolkit realtà mista è [la classe WindowsMixedRealitySpatialMeshObserver.](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver) Molte delle proprietà in questo articolo, tuttavia, si applicano ad altre [implementazioni observer personalizzate.](create-data-provider.md)

## <a name="profile-settings"></a>Impostazioni del profilo

I due elementi seguenti devono essere definiti per primi quando si configura un profilo osservatore della mesh spaziale per il [sistema di consapevolezza spaziale](spatial-awareness-getting-started.md).

1. Implementazione del tipo observer concreto
1. elenco delle piattaforme supportate per l'esecuzione di questo osservatore

> [!NOTE]
> Tutti gli osservatori devono estendere [l'interfaccia IMixedRealitySpatialAwarenessObserver.](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver)

![Tipi di piattaforma Impostazioni Mesh Observer](../images/spatial-awareness/SpatialAwarenessMeshObserverProfile_TypesPlatforms.png)

### <a name="general-settings"></a>Impostazioni generali

![Impostazioni generali dell'osservatore Impostazioni mesh](../images/spatial-awareness/MeshObserverGeneralSettings.png)

**Comportamento di avvio**

Il comportamento di avvio specifica se l'osservatore inizierà l'esecuzione alla prima creazione di un'istanza. Le due opzioni sono:

* *Avvio automatico:* valore predefinito in base al quale l'osservatore inizierà l'operazione dopo l'inizializzazione
* *Avvio manuale:* l'osservatore attenderà di essere indirizzato all'avvio

Se si usa *l'avvio* manuale, è [necessario riprenderli e sospenderli in fase di esecuzione tramite codice](usage-guide.md#starting-and-stopping-mesh-observation).

**Intervallo di aggiornamento**

Tempo, in secondi, tra le richieste alla piattaforma per aggiornare i dati della mesh spaziale. I valori tipici rientrano nell'intervallo di 0,1 e 5,0 secondi.

**Is Stationary Observer**

Indica se l'osservatore deve rimanere stazionaria o spostare e aggiornare con l'utente. Se true, la *forma osservatore* con volume definito da *Extent di osservazione* rimarrà all'origine all'avvio. Se false, lo spazio Observer seguirà la testa dell'utente come origine della forma.

Non verranno calcolati dati di mesh per alcuna area fisica esterna allo spazio Observer, come definito da queste proprietà: *Is Stationary Observer*, *Observer Shape** e *Observation Extents*.

**Forma osservatore**

La forma osservatore definisce il tipo di volume che l'osservatore di mesh userà durante l'osservazione delle mesh. Le opzioni supportate sono:

* *Cubo allineato all'asse:* forma rettangolare che rimane allineata agli assi del sistema di coordinate del mondo, come determinato all'avvio dell'applicazione.
* *Cubo allineato dall'utente:* forma rettangolare che ruota per allinearsi al sistema di coordinate locale degli utenti.
* *Sphere:* volume sferico con un centro all'origine dello spazio mondiale. Il valore X della *proprietà Observation Extents* verrà usato come raggio della sfera.

**Extent di osservazione**

Gli extent di osservazione definiscono la distanza dal punto di osservazione in cui verranno osservate le mesh.

### <a name="physics-settings"></a>Impostazioni di fisica

![Fisica osservatore mesh Impostazioni](../images/spatial-awareness/MeshObserverPhysicsSettings.png)

**Livello fisico**

Livello fisico su cui verranno posizionati gli oggetti mesh spaziale per interagire con i sistemi Unity Physics e RayCast.

> [!NOTE]
> Per impostazione predefinita, Toolkit realtà mista riserva *il livello 31* per l'uso da parte degli osservatori di consapevolezza spaziale.

**Ricalcolare le normali**

Specifica se l'osservatore di mesh ricalcolerà o meno le normali della mesh dopo l'osservazione. Questa impostazione è disponibile per garantire che le applicazioni ricevano mesh contenenti dati normali validi sulle piattaforme che non le restituiscono con mesh.

### <a name="level-of-detail-settings"></a>Impostazioni del livello di dettaglio

![Livello di dettaglio osservatore mesh Impostazioni](../images/spatial-awareness/MeshObserverLevelOfDetailSettings.png)

**Livello di dettaglio**

Specifica il livello di dettaglio (LOD) dei dati della mesh spaziale. I valori attualmente definiti sono Coarse, Fine e Custom.

* *Grossoleno: influisce* negativamente sulle prestazioni dell'applicazione ed è un'ottima scelta per la ricerca di spostamenti/piani.

* *Media:* impostazione bilanciata spesso utile per le esperienze che analizzano continuamente l'ambiente alla ricerca di caratteristiche di grandi dimensioni, piani e pareti, nonché dettagli di occlusione.

* *Fine:* in genere ha un impatto maggiore sulle prestazioni dell'applicazione ed è un'ottima opzione per le mesh di occlusione.

* *Personalizzato:* richiede all'applicazione di specificare la proprietà *Triangles/Cubic Meter* e consente alle applicazioni di ottimizzare l'accuratezza e l'impatto sulle prestazioni dell'osservatore della mesh spaziale.

> [!NOTE]
> Non è garantito che tutti i *valori triangles/cubic meter* siano rispettati da tutte le piattaforme. La sperimentazione e la profilatura sono altamente consigliate quando si usa un loD personalizzato.

**Triangoli per contatore cubico**

Valido quando si usa *l'impostazione* Personalizzata per **la proprietà Livello** di dettaglio e specifica la densità del triangolo per la mesh spaziale.

### <a name="display-settings"></a>Impostazioni schermo

![Visualizzazione osservatore mesh Impostazioni](../images/spatial-awareness/MeshObserverDisplaySettings.png)

**Opzione di visualizzazione**

Specifica la modalità di visualizzazione delle mesh spaziali da parte dell'osservatore. I valori supportati sono:

* *Nessuno -* Observer non eseguirà il rendering della mesh
* *Visibile:* i dati della mesh saranno visibili usando *il materiale visibile*
* *Occlusione:* i dati della mesh occludono gli elementi nella scena usando il *materiale di occlusione*

![Selezionare l'implementazione del sistema di consapevolezza spaziale](../images/spatial-awareness/MRTK_SpatialAwareness_DisplayOptions.jpg)

Gli osservatori spaziali possono essere [ripresi/sospesi in fase di esecuzione tramite codice.](usage-guide.md#starting-and-stopping-mesh-observation)

> [!WARNING]
> *L'impostazione dell'opzione* *di visualizzazione su Nessuno* NON interrompe **l'esecuzione** dell'osservatore. Se si desidera arrestare tutti gli osservatori, le applicazioni dovranno sospendere tutti gli osservatori tramite [`CoreServices.SpatialAwareness.SuspendObservers()`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessSystem.SuspendObservers)

**Materiale visibile**

Indica il materiale da usare durante la visualizzazione della mesh spaziale.

**Materiale di occlusione**

Indica il materiale da usare per fare in modo che la mesh spaziale oclude gli ologrammi.

## <a name="see-also"></a>Vedi anche

* [Spatial Awareness System](spatial-awareness-getting-started.md)
* [Configurazione del sistema di consapevolezza spaziale tramite codice](usage-guide.md)
* [Documentazione dell'API IMixedRealitySpatialAwarenessObserver](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver)
* [Documentazione dell'API IMixedRealitySpatialAwarenessMeshObserver](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessMeshObserver)
* [Documentazione dell'API BaseSpatialObserver](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.BaseSpatialObserver)

---
title: UsingGuide
description: vengono descritti i meccanismi e le API principali per configurare a livello di codice il sistema di riconoscimento spaziale
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: f1fd6620934c3936aa596eda52bab300a84a1acb
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2021
ms.locfileid: "104696078"
---
# <a name="configuring-mesh-observers-via-code"></a>Configurazione di osservatori mesh tramite codice

In questo articolo verranno illustrati alcuni dei principali meccanismi e API per configurare a livello di codice il [sistema di riconoscimento spaziale](spatial-awareness-getting-started.md) e i provider di dati dell' *osservatore mesh* correlati.

## <a name="accessing-mesh-observers"></a>Accesso agli osservatori mesh

Le classi Observer mesh che implementano l' [`IMixedRealitySpatialAwarenessMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessMeshObserver) interfaccia forniscono dati mesh specifici della piattaforma al sistema di riconoscimento spaziale. È possibile configurare più osservatori nel profilo di sensibilizzazione spaziale.

L'accesso ai provider di dati del sistema di riconoscimento spaziale è essenzialmente uguale a quello di qualsiasi altro servizio Toolkit di realtà mista. È necessario eseguire il cast del servizio di riconoscimento spaziale all' [`IMixedRealityDataProviderAccess`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProviderAccess) interfaccia per accedere tramite le `GetDataProvider<T>` API, che possono quindi essere utilizzate per accedere agli oggetti Observer mesh direttamente in fase di esecuzione.

```c#
// Use CoreServices to quickly get access to the IMixedRealitySpatialAwarenessSystem
var spatialAwarenessService = CoreServices.SpatialAwarenessSystem;

// Cast to the IMixedRealityDataProviderAccess to get access to the data providers
var dataProviderAccess = spatialAwarenessService as IMixedRealityDataProviderAccess;

var meshObserver = dataProviderAccess.GetDataProvider<IMixedRealitySpatialAwarenessMeshObserver>();
```

L' `CoreServices.GetSpatialAwarenessSystemDataProvider<T>()` Helper semplifica questo modello di accesso, come illustrato di seguito.

```c#
// Get the first Mesh Observer available, generally we have only one registered
var meshObserver = CoreServices.GetSpatialAwarenessSystemDataProvider<IMixedRealitySpatialAwarenessMeshObserver>();

// Get the SpatialObjectMeshObserver specifically
var meshObserverName = "Spatial Object Mesh Observer";
var spatialObjectMeshObserver = dataProviderAccess.GetDataProvider<IMixedRealitySpatialAwarenessMeshObserver>(meshObserverName);
```

## <a name="starting-and-stopping-mesh-observation"></a>Avvio e arresto dell'osservazione mesh

Una delle attività più comuni quando si lavora con il sistema di riconoscimento spaziale è la disattivazione o l'attivazione dinamica della funzionalità in fase di esecuzione. Questa operazione viene eseguita per Observer tramite le [`IMixedRealitySpatialAwarenessObserver.Resume`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver.Resume) [`IMixedRealitySpatialAwarenessObserver.Suspend`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver.Suspend) API e.

```c#
// Get the first Mesh Observer available, generally we have only one registered
var observer = CoreServices.GetSpatialAwarenessSystemDataProvider<IMixedRealitySpatialAwarenessMeshObserver>();

// Suspends observation of spatial mesh data
observer.Suspend();

// Resumes observation of spatial mesh data
observer.Resume();
```

Questa funzionalità del codice può essere semplificata anche tramite l'accesso diretto tramite il sistema di riconoscimento spaziale.

```c#
var meshObserverName = "Spatial Object Mesh Observer";
CoreServices.SpatialAwarenessSystem.ResumeObserver<IMixedRealitySpatialAwarenessMeshObserver>(meshObserverName);
```

### <a name="starting-and-stopping-all-mesh-observation"></a>Avvio e arresto di tutte le osservazioni sulla rete

È in genere consigliabile avviare/arrestare tutte le osservazioni di rete nell'applicazione. Questa operazione può essere eseguita tramite le API del sistema di riconoscimento spaziale utile [`ResumeObservers()`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessSystem.ResumeObservers) e [`SuspendObservers()`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessSystem.SuspendObservers) .

```c#
// Resume Mesh Observation from all Observers
CoreServices.SpatialAwarenessSystem.ResumeObservers();

// Suspend Mesh Observation from all Observers
CoreServices.SpatialAwarenessSystem.SuspendObservers();
```

## <a name="enumerating-and-accessing-the-meshes"></a>Enumerazione e accesso alle mesh

L'accesso alle mesh può essere eseguito per osservatore e quindi per l'enumerazione attraverso le maglie note a tale osservatore mesh tramite l' [`IMixedRealitySpatialAwarenessMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessMeshObserver) API.

Se è in esecuzione nell'editor, è possibile usare [`AssetDatabase.CreateAsset()`](https://docs.unity3d.com/ScriptReference/AssetDatabase.CreateAsset.html) per salvare l' `Mesh` oggetto in un file di asset.

Se è in esecuzione nel dispositivo, sono disponibili molti plug-in di community e di archiviazione per serializzare i `MeshFilter` dati in un tipo di file modello ([esempio obj](http://wiki.unity3d.com/index.php/ObjExporter)).

```c#
// Get the first Mesh Observer available, generally we have only one registered
var observer = CoreServices.GetSpatialAwarenessSystemDataProvider<IMixedRealitySpatialAwarenessMeshObserver>();

// Loop through all known Meshes
foreach (SpatialAwarenessMeshObject meshObject in observer.Meshes.Values)
{
    Mesh mesh = meshObject.Filter.mesh;
    // Do something with the Mesh object
}
```

## <a name="showing-and-hiding-the-spatial-mesh"></a>Visualizzazione e nascondere la mesh spaziale

È possibile nascondere/visualizzare a livello di codice le mesh usando il codice di esempio seguente:

```c#
// Get the first Mesh Observer available, generally we have only one registered
var observer = CoreServices.GetSpatialAwarenessSystemDataProvider<IMixedRealitySpatialAwarenessMeshObserver>();

// Set to not visible
observer.DisplayOption = SpatialAwarenessMeshDisplayOptions.None;

// Set to visible and the Occlusion material
observer.DisplayOption = SpatialAwarenessMeshDisplayOptions.Occlusion;
```

## <a name="registering-for-mesh-observation-events"></a>Registrazione per gli eventi di osservazione mesh

I componenti possono implementare `IMixedRealitySpatialAwarenessObservationHandler<SpatialAwarenessMeshObject>` e quindi registrarsi con il sistema di riconoscimento spaziale per ricevere eventi di osservazione della rete.

Lo `DemoSpatialMeshHandler` script (assets/MRTK/examples/Demos/SpatialAwareness/scripts) è un esempio utile e un punto di partenza per l'ascolto di eventi dell'osservatore mesh.

Si tratta di un esempio semplificato di script di *DemoSpatialMeshHandler* e di ascolto di un evento di osservazione mesh.

```c#
// Simplify type
using SpatialAwarenessHandler = IMixedRealitySpatialAwarenessObservationHandler<SpatialAwarenessMeshObject>;

public class MyMeshObservationExample : MonoBehaviour, SpatialAwarenessHandler
{
    private void OnEnable()
    {
        // Register component to listen for Mesh Observation events, typically done in OnEnable()
        CoreServices.SpatialAwarenessSystem.RegisterHandler<SpatialAwarenessHandler>(this);
    }

    private void OnDisable()
    {
        // Unregister component from Mesh Observation events, typically done in OnDisable()
        CoreServices.SpatialAwarenessSystem.UnregisterHandler<SpatialAwarenessHandler>(this);
    }

    public virtual void OnObservationAdded(MixedRealitySpatialAwarenessEventData<SpatialAwarenessMeshObject> eventData)
    {
        // Do stuff
    }

    public virtual void OnObservationUpdated(MixedRealitySpatialAwarenessEventData<SpatialAwarenessMeshObject> eventData)
    {
        // Do stuff
    }

    public virtual void OnObservationRemoved(MixedRealitySpatialAwarenessEventData<SpatialAwarenessMeshObject> eventData)
    {
        // Do stuff
    }
}
```

## <a name="see-also"></a>Vedi anche

- [Introduzione di consapevolezza spaziale](spatial-awareness-getting-started.md)
- [Configurazione dell'osservatore mesh di consapevolezza spaziale](configuring-spatial-awareness-mesh-observer.md)
- [Documentazione dell'API di riconoscimento spaziale](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness)

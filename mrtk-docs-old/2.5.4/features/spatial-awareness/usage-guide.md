---
title: UsingGuide
description: descrive i meccanismi chiave e le API per configurare a livello di codice il sistema di consapevolezza spaziale
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: 3a4b6ce17b87dba6155a9e020e41c800fd8ab86bc1b507e77e680fe9ec9a6687
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115225647"
---
# <a name="configuring-mesh-observers-via-code"></a>Configurazione degli osservatori mesh tramite codice

Questo articolo illustra alcuni dei meccanismi chiave e delle API per configurare a livello di codice il sistema [di](spatial-awareness-getting-started.md) consapevolezza spaziale e i provider di dati *di Mesh Observer* correlati.

## <a name="accessing-mesh-observers"></a>Accesso agli osservatori della mesh

Le classi dell'osservatore mesh che implementano l'interfaccia forniscono dati mesh specifici della [`IMixedRealitySpatialAwarenessMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessMeshObserver) piattaforma al sistema di consapevolezza spaziale. È possibile configurare più osservatori nel profilo Di consapevolezza spaziale.

L'accesso ai provider di dati del sistema di consapevolezza spaziale è principalmente lo stesso di qualsiasi altro servizio di Toolkit realtà mista. È necessario eseguire il cast del servizio Consapevolezza spaziale all'interfaccia per accedere tramite le API, che possono quindi essere utilizzate per accedere agli oggetti Osservatore mesh direttamente in [`IMixedRealityDataProviderAccess`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProviderAccess) `GetDataProvider<T>` fase di esecuzione.

```c#
// Use CoreServices to quickly get access to the IMixedRealitySpatialAwarenessSystem
var spatialAwarenessService = CoreServices.SpatialAwarenessSystem;

// Cast to the IMixedRealityDataProviderAccess to get access to the data providers
var dataProviderAccess = spatialAwarenessService as IMixedRealityDataProviderAccess;

var meshObserver = dataProviderAccess.GetDataProvider<IMixedRealitySpatialAwarenessMeshObserver>();
```

`CoreServices.GetSpatialAwarenessSystemDataProvider<T>()`L'helper semplifica questo modello di accesso, come illustrato di seguito.

```c#
// Get the first Mesh Observer available, generally we have only one registered
var meshObserver = CoreServices.GetSpatialAwarenessSystemDataProvider<IMixedRealitySpatialAwarenessMeshObserver>();

// Get the SpatialObjectMeshObserver specifically
var meshObserverName = "Spatial Object Mesh Observer";
var spatialObjectMeshObserver = dataProviderAccess.GetDataProvider<IMixedRealitySpatialAwarenessMeshObserver>(meshObserverName);
```

## <a name="starting-and-stopping-mesh-observation"></a>Avvio e arresto dell'osservazione della mesh

Una delle attività più comuni quando si utilizza il sistema di consapevolezza spaziale è disattivare/attivare dinamicamente la funzionalità in fase di esecuzione. Questa operazione viene eseguita per Observer tramite [`IMixedRealitySpatialAwarenessObserver.Resume`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver.Resume) le [`IMixedRealitySpatialAwarenessObserver.Suspend`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver.Suspend) API e .

```c#
// Get the first Mesh Observer available, generally we have only one registered
var observer = CoreServices.GetSpatialAwarenessSystemDataProvider<IMixedRealitySpatialAwarenessMeshObserver>();

// Suspends observation of spatial mesh data
observer.Suspend();

// Resumes observation of spatial mesh data
observer.Resume();
```

Questa funzionalità del codice può essere semplificata anche tramite l'accesso direttamente tramite il sistema di consapevolezza spaziale.

```c#
var meshObserverName = "Spatial Object Mesh Observer";
CoreServices.SpatialAwarenessSystem.ResumeObserver<IMixedRealitySpatialAwarenessMeshObserver>(meshObserverName);
```

### <a name="starting-and-stopping-all-mesh-observation"></a>Avvio e arresto di tutte le osservazioni della mesh

In genere è utile avviare/arrestare tutte le osservazioni di mesh nell'applicazione. Questa operazione può essere ottenuta tramite le utili API del sistema Di consapevolezza spaziale [`ResumeObservers()`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessSystem.ResumeObservers) e [`SuspendObservers()`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessSystem.SuspendObservers) .

```c#
// Resume Mesh Observation from all Observers
CoreServices.SpatialAwarenessSystem.ResumeObservers();

// Suspend Mesh Observation from all Observers
CoreServices.SpatialAwarenessSystem.SuspendObservers();
```

## <a name="enumerating-and-accessing-the-meshes"></a>Enumerazione e accesso alle mesh

L'accesso alle mesh può essere eseguito in base all'osservatore e quindi enumerando le mesh note a tale osservatore tramite [`IMixedRealitySpatialAwarenessMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessMeshObserver) l'API.

Se in esecuzione nell'editor, è possibile usare [`AssetDatabase.CreateAsset()`](https://docs.unity3d.com/ScriptReference/AssetDatabase.CreateAsset.html) per salvare `Mesh` l'oggetto in un file di asset.

Se in esecuzione nel dispositivo, sono disponibili molti plug-in della community e dell'archivio per serializzare i dati in un tipo `MeshFilter` di file modello([ObJ Example](http://wiki.unity3d.com/index.php/ObjExporter)).

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

È possibile nascondere/mostrare mesh a livello di codice usando il codice di esempio seguente:

```c#
// Get the first Mesh Observer available, generally we have only one registered
var observer = CoreServices.GetSpatialAwarenessSystemDataProvider<IMixedRealitySpatialAwarenessMeshObserver>();

// Set to not visible
observer.DisplayOption = SpatialAwarenessMeshDisplayOptions.None;

// Set to visible and the Occlusion material
observer.DisplayOption = SpatialAwarenessMeshDisplayOptions.Occlusion;
```

## <a name="registering-for-mesh-observation-events"></a>Registrazione per gli eventi di osservazione della mesh

I componenti possono implementare e quindi registrarsi con il sistema di consapevolezza `IMixedRealitySpatialAwarenessObservationHandler<SpatialAwarenessMeshObject>` spaziale per ricevere eventi di osservazione mesh.

Lo script (Assets/MRTK/Examples/Demos/SpatialAwareness/Scripts) è un esempio utile e un punto di partenza per l'ascolto degli `DemoSpatialMeshHandler` eventi di Mesh Observer.

Questo è un esempio semplificato dello script *DemoSpatialMeshHandler* e dell'ascolto degli eventi di Osservazione mesh.

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

- [Consapevolezza spaziale Attività iniziali](spatial-awareness-getting-started.md)
- [Configurazione dell'osservatore della mesh di consapevolezza spaziale](configuring-spatial-awareness-mesh-observer.md)
- [Documentazione dell'API Spatial Awareness](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness)

---
title: UsingGuide
description: vengono descritti i meccanismi e le API principali per configurare a livello di codice il sistema di riconoscimento spaziale
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: 89a345f43a5133b8a99cabab1abc15a6e8770a4d
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2021
ms.locfileid: "104689721"
---
# <a name="configuring-mesh-observers-via-code"></a><span data-ttu-id="9907d-104">Configurazione di osservatori mesh tramite codice</span><span class="sxs-lookup"><span data-stu-id="9907d-104">Configuring mesh observers via code</span></span>

<span data-ttu-id="9907d-105">In questo articolo verranno illustrati alcuni dei principali meccanismi e API per configurare a livello di codice il [sistema di riconoscimento spaziale](SpatialAwarenessGettingStarted.md) e i provider di dati dell' *osservatore mesh* correlati.</span><span class="sxs-lookup"><span data-stu-id="9907d-105">This article will discuss some of the key mechanisms and APIs to programmatically configure the [Spatial Awareness system](SpatialAwarenessGettingStarted.md) and related *Mesh Observer* data providers.</span></span>

## <a name="accessing-mesh-observers"></a><span data-ttu-id="9907d-106">Accesso agli osservatori mesh</span><span class="sxs-lookup"><span data-stu-id="9907d-106">Accessing mesh observers</span></span>

<span data-ttu-id="9907d-107">Le classi Observer mesh che implementano l' [`IMixedRealitySpatialAwarenessMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessMeshObserver) interfaccia forniscono dati mesh specifici della piattaforma al sistema di riconoscimento spaziale.</span><span class="sxs-lookup"><span data-stu-id="9907d-107">Mesh Observer classes that implement the [`IMixedRealitySpatialAwarenessMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessMeshObserver) interface provide platform-specific mesh data to the Spatial Awareness system.</span></span> <span data-ttu-id="9907d-108">È possibile configurare più osservatori nel profilo di sensibilizzazione spaziale.</span><span class="sxs-lookup"><span data-stu-id="9907d-108">Multiple Observers can be configured in the Spatial Awareness profile.</span></span>

<span data-ttu-id="9907d-109">L'accesso ai provider di dati del sistema di riconoscimento spaziale è essenzialmente uguale a quello di qualsiasi altro servizio Toolkit di realtà mista.</span><span class="sxs-lookup"><span data-stu-id="9907d-109">Accessing the data providers of the Spatial Awareness system is mostly the same as for any other Mixed Reality Toolkit service.</span></span> <span data-ttu-id="9907d-110">È necessario eseguire il cast del servizio di riconoscimento spaziale all' [`IMixedRealityDataProviderAccess`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProviderAccess) interfaccia per accedere tramite le `GetDataProvider<T>` API, che possono quindi essere utilizzate per accedere agli oggetti Observer mesh direttamente in fase di esecuzione.</span><span class="sxs-lookup"><span data-stu-id="9907d-110">The Spatial Awareness service must be casted to the [`IMixedRealityDataProviderAccess`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProviderAccess) interface to access via the `GetDataProvider<T>` APIs, which can then be utilized to access the Mesh Observer objects directly at runtime.</span></span>

```c#
// Use CoreServices to quickly get access to the IMixedRealitySpatialAwarenessSystem
var spatialAwarenessService = CoreServices.SpatialAwarenessSystem;

// Cast to the IMixedRealityDataProviderAccess to get access to the data providers
var dataProviderAccess = spatialAwarenessService as IMixedRealityDataProviderAccess;

var meshObserver = dataProviderAccess.GetDataProvider<IMixedRealitySpatialAwarenessMeshObserver>();
```

<span data-ttu-id="9907d-111">L' `CoreServices.GetSpatialAwarenessSystemDataProvider<T>()` Helper semplifica questo modello di accesso, come illustrato di seguito.</span><span class="sxs-lookup"><span data-stu-id="9907d-111">The `CoreServices.GetSpatialAwarenessSystemDataProvider<T>()` helper simplifies this access pattern as demonstrated below.</span></span>

```c#
// Get the first Mesh Observer available, generally we have only one registered
var meshObserver = CoreServices.GetSpatialAwarenessSystemDataProvider<IMixedRealitySpatialAwarenessMeshObserver>();

// Get the SpatialObjectMeshObserver specifically
var meshObserverName = "Spatial Object Mesh Observer";
var spatialObjectMeshObserver = dataProviderAccess.GetDataProvider<IMixedRealitySpatialAwarenessMeshObserver>(meshObserverName);
```

## <a name="starting-and-stopping-mesh-observation"></a><span data-ttu-id="9907d-112">Avvio e arresto dell'osservazione mesh</span><span class="sxs-lookup"><span data-stu-id="9907d-112">Starting and stopping mesh observation</span></span>

<span data-ttu-id="9907d-113">Una delle attività più comuni quando si lavora con il sistema di riconoscimento spaziale è la disattivazione o l'attivazione dinamica della funzionalità in fase di esecuzione.</span><span class="sxs-lookup"><span data-stu-id="9907d-113">One of the most common tasks when dealing with the Spatial Awareness system is turning the feature off/on dynamically at runtime.</span></span> <span data-ttu-id="9907d-114">Questa operazione viene eseguita per Observer tramite le [`IMixedRealitySpatialAwarenessObserver.Resume`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver.Resume) [`IMixedRealitySpatialAwarenessObserver.Suspend`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver.Suspend) API e.</span><span class="sxs-lookup"><span data-stu-id="9907d-114">This is done per Observer via the [`IMixedRealitySpatialAwarenessObserver.Resume`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver.Resume) and [`IMixedRealitySpatialAwarenessObserver.Suspend`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver.Suspend) APIs.</span></span>

```c#
// Get the first Mesh Observer available, generally we have only one registered
var observer = CoreServices.GetSpatialAwarenessSystemDataProvider<IMixedRealitySpatialAwarenessMeshObserver>();

// Suspends observation of spatial mesh data
observer.Suspend();

// Resumes observation of spatial mesh data
observer.Resume();
```

<span data-ttu-id="9907d-115">Questa funzionalità del codice può essere semplificata anche tramite l'accesso diretto tramite il sistema di riconoscimento spaziale.</span><span class="sxs-lookup"><span data-stu-id="9907d-115">This code functionality can also be simplified via access through the Spatial Awareness system directly.</span></span>

```c#
var meshObserverName = "Spatial Object Mesh Observer";
CoreServices.SpatialAwarenessSystem.ResumeObserver<IMixedRealitySpatialAwarenessMeshObserver>(meshObserverName);
```

### <a name="starting-and-stopping-all-mesh-observation"></a><span data-ttu-id="9907d-116">Avvio e arresto di tutte le osservazioni sulla rete</span><span class="sxs-lookup"><span data-stu-id="9907d-116">Starting and stopping all mesh observation</span></span>

<span data-ttu-id="9907d-117">È in genere consigliabile avviare/arrestare tutte le osservazioni di rete nell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="9907d-117">It is generally convenient to start/stop all mesh observation in the application.</span></span> <span data-ttu-id="9907d-118">Questa operazione può essere eseguita tramite le API del sistema di riconoscimento spaziale utile [`ResumeObservers()`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessSystem.ResumeObservers) e [`SuspendObservers()`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessSystem.SuspendObservers) .</span><span class="sxs-lookup"><span data-stu-id="9907d-118">This can be achieved through the helpful Spatial Awareness system APIs, [`ResumeObservers()`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessSystem.ResumeObservers) and [`SuspendObservers()`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessSystem.SuspendObservers).</span></span>

```c#
// Resume Mesh Observation from all Observers
CoreServices.SpatialAwarenessSystem.ResumeObservers();

// Suspend Mesh Observation from all Observers
CoreServices.SpatialAwarenessSystem.SuspendObservers();
```

## <a name="enumerating-and-accessing-the-meshes"></a><span data-ttu-id="9907d-119">Enumerazione e accesso alle mesh</span><span class="sxs-lookup"><span data-stu-id="9907d-119">Enumerating and accessing the meshes</span></span>

<span data-ttu-id="9907d-120">L'accesso alle mesh può essere eseguito per osservatore e quindi per l'enumerazione attraverso le maglie note a tale osservatore mesh tramite l' [`IMixedRealitySpatialAwarenessMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessMeshObserver) API.</span><span class="sxs-lookup"><span data-stu-id="9907d-120">Accessing the meshes can be done per Observer and then enumerating through the meshes known to that Mesh Observer via the [`IMixedRealitySpatialAwarenessMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessMeshObserver) API.</span></span>

<span data-ttu-id="9907d-121">Se è in esecuzione nell'editor, è possibile usare [`AssetDatabase.CreateAsset()`](https://docs.unity3d.com/ScriptReference/AssetDatabase.CreateAsset.html) per salvare l' `Mesh` oggetto in un file di asset.</span><span class="sxs-lookup"><span data-stu-id="9907d-121">If running in editor, one can use the [`AssetDatabase.CreateAsset()`](https://docs.unity3d.com/ScriptReference/AssetDatabase.CreateAsset.html) to save the `Mesh` object to an asset file.</span></span>

<span data-ttu-id="9907d-122">Se è in esecuzione nel dispositivo, sono disponibili molti plug-in di community e di archiviazione per serializzare i `MeshFilter` dati in un tipo di file modello ([esempio obj](http://wiki.unity3d.com/index.php/ObjExporter)).</span><span class="sxs-lookup"><span data-stu-id="9907d-122">If running on device, there are many community and store plugins available to serialize the `MeshFilter` data into a model file type([OBJ Example](http://wiki.unity3d.com/index.php/ObjExporter)).</span></span>

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

## <a name="showing-and-hiding-the-spatial-mesh"></a><span data-ttu-id="9907d-123">Visualizzazione e nascondere la mesh spaziale</span><span class="sxs-lookup"><span data-stu-id="9907d-123">Showing and hiding the spatial mesh</span></span>

<span data-ttu-id="9907d-124">È possibile nascondere/visualizzare a livello di codice le mesh usando il codice di esempio seguente:</span><span class="sxs-lookup"><span data-stu-id="9907d-124">It's possible to programmatically hide/show meshes using the sample code below:</span></span>

```c#
// Get the first Mesh Observer available, generally we have only one registered
var observer = CoreServices.GetSpatialAwarenessSystemDataProvider<IMixedRealitySpatialAwarenessMeshObserver>();

// Set to not visible
observer.DisplayOption = SpatialAwarenessMeshDisplayOptions.None;

// Set to visible and the Occlusion material
observer.DisplayOption = SpatialAwarenessMeshDisplayOptions.Occlusion;
```

## <a name="registering-for-mesh-observation-events"></a><span data-ttu-id="9907d-125">Registrazione per gli eventi di osservazione mesh</span><span class="sxs-lookup"><span data-stu-id="9907d-125">Registering for mesh observation events</span></span>

<span data-ttu-id="9907d-126">I componenti possono implementare `IMixedRealitySpatialAwarenessObservationHandler<SpatialAwarenessMeshObject>` e quindi registrarsi con il sistema di riconoscimento spaziale per ricevere eventi di osservazione della rete.</span><span class="sxs-lookup"><span data-stu-id="9907d-126">Components can implement the `IMixedRealitySpatialAwarenessObservationHandler<SpatialAwarenessMeshObject>` and then register with the Spatial Awareness system to receive Mesh Observation events.</span></span>

<span data-ttu-id="9907d-127">Lo `DemoSpatialMeshHandler` script (assets/MRTK/examples/Demos/SpatialAwareness/scripts) è un esempio utile e un punto di partenza per l'ascolto di eventi dell'osservatore mesh.</span><span class="sxs-lookup"><span data-stu-id="9907d-127">The `DemoSpatialMeshHandler` (Assets/MRTK/Examples/Demos/SpatialAwareness/Scripts) script is a useful example and starting point for listening to Mesh Observer events.</span></span>

<span data-ttu-id="9907d-128">Si tratta di un esempio semplificato di script di *DemoSpatialMeshHandler* e di ascolto di un evento di osservazione mesh.</span><span class="sxs-lookup"><span data-stu-id="9907d-128">This is a simplified example of *DemoSpatialMeshHandler* script and Mesh Observation event listening.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="9907d-129">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="9907d-129">See also</span></span>

- [<span data-ttu-id="9907d-130">Introduzione di consapevolezza spaziale</span><span class="sxs-lookup"><span data-stu-id="9907d-130">Spatial Awareness Getting Started</span></span>](SpatialAwarenessGettingStarted.md)
- [<span data-ttu-id="9907d-131">Configurazione dell'osservatore mesh di consapevolezza spaziale</span><span class="sxs-lookup"><span data-stu-id="9907d-131">Configuring the Spatial Awareness Mesh Observer</span></span>](ConfiguringSpatialAwarenessMeshObserver.md)
- [<span data-ttu-id="9907d-132">Documentazione dell'API di riconoscimento spaziale</span><span class="sxs-lookup"><span data-stu-id="9907d-132">Spatial Awareness API documentation</span></span>](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness)

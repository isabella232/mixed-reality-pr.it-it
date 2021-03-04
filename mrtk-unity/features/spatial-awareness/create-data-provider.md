---
title: CreateSpatialAwarenessDataProvider
description: viene descritto come creare provider di dati personalizzati in MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: 05bff204444c1196bab7155986ce10445381ad86
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/03/2021
ms.locfileid: "101782996"
---
# <a name="creating-a-spatial-awareness-system-data-provider"></a><span data-ttu-id="be30e-104">Creazione di un provider di dati di sistema di riconoscimento spaziale</span><span class="sxs-lookup"><span data-stu-id="be30e-104">Creating a spatial awareness system data provider</span></span>

<span data-ttu-id="be30e-105">Il sistema di riconoscimento spaziale è un sistema estensibile per fornire applicazioni con dati sugli ambienti reali.</span><span class="sxs-lookup"><span data-stu-id="be30e-105">The Spatial Awareness system is an extensible system for providing applications with data about real world environments.</span></span> <span data-ttu-id="be30e-106">Per aggiungere il supporto per una nuova piattaforma hardware o un nuovo tipo di dati di riconoscimento spaziale, potrebbe essere necessario un provider di dati personalizzato.</span><span class="sxs-lookup"><span data-stu-id="be30e-106">To add support for a new hardware platform or a new form of Spatial Awareness data, a custom data provider may be required.</span></span>

<span data-ttu-id="be30e-107">Questo articolo descrive come creare [provider di dati personalizzati](../../architecture/systems-extensions-providers.md), denominati anche osservatori spaziali, per il sistema di riconoscimento spaziale.</span><span class="sxs-lookup"><span data-stu-id="be30e-107">This article describes how to create [custom data providers](../../architecture/systems-extensions-providers.md), also called Spatial Observers, for the Spatial Awareness system.</span></span> <span data-ttu-id="be30e-108">Il codice di esempio illustrato di seguito è [`SpatialObjectMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserver) relativo all'implementazione della classe, [utile per il caricamento di dati mesh 3D nell'editor](spatial-object-mesh-observer.md).</span><span class="sxs-lookup"><span data-stu-id="be30e-108">The example code shown here is from the [`SpatialObjectMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserver) class implementation which is [useful for loading 3D mesh data in-editor](spatial-object-mesh-observer.md).</span></span>

> [!NOTE]
> <span data-ttu-id="be30e-109">Il codice sorgente completo usato in questo esempio si trova nella `Assets/MRTK/Providers/ObjectMeshObserver` cartella.</span><span class="sxs-lookup"><span data-stu-id="be30e-109">The complete source code used in this example can be found in the `Assets/MRTK/Providers/ObjectMeshObserver` folder.</span></span>

## <a name="namespace-and-folder-structure"></a><span data-ttu-id="be30e-110">Struttura dello spazio dei nomi e della cartella</span><span class="sxs-lookup"><span data-stu-id="be30e-110">Namespace and folder structure</span></span>

<span data-ttu-id="be30e-111">I provider di dati possono essere distribuiti in uno dei due modi seguenti:</span><span class="sxs-lookup"><span data-stu-id="be30e-111">Data providers can be distributed in one of two ways:</span></span>

1. <span data-ttu-id="be30e-112">Componenti aggiuntivi di terze parti</span><span class="sxs-lookup"><span data-stu-id="be30e-112">Third party add-ons</span></span>
1. <span data-ttu-id="be30e-113">Parte del Toolkit Microsoft Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="be30e-113">Part of the Microsoft Mixed Reality Toolkit</span></span>

<span data-ttu-id="be30e-114">Il processo di approvazione per gli invii di nuovi provider di dati alla MRTK varia a seconda del caso e verrà comunicato al momento della proposta iniziale di.</span><span class="sxs-lookup"><span data-stu-id="be30e-114">The approval process for submissions of new data providers to the MRTK will vary on a case-by-case basis and will be communicated at the time of the initial proposal.</span></span> <span data-ttu-id="be30e-115">È possibile inviare proposte creando un nuovo [problema relativo al tipo di *richiesta di funzionalità*](https://github.com/microsoft/MixedRealityToolkit-Unity/issues).</span><span class="sxs-lookup"><span data-stu-id="be30e-115">Proposals can be submitted by creating a new [*Feature Request* type issue](https://github.com/microsoft/MixedRealityToolkit-Unity/issues).</span></span>

### <a name="third-party-add-on"></a><span data-ttu-id="be30e-116">Componente aggiuntivo di terze parti</span><span class="sxs-lookup"><span data-stu-id="be30e-116">Third party add-on</span></span>

<span data-ttu-id="be30e-117">**Namespace**</span><span class="sxs-lookup"><span data-stu-id="be30e-117">**Namespace**</span></span>

<span data-ttu-id="be30e-118">È necessario che i provider di dati dispongano di uno spazio dei nomi per attenuare i potenziali conflitti di nomi.</span><span class="sxs-lookup"><span data-stu-id="be30e-118">Data providers are required to have a namespace to mitigate potential name collisions.</span></span> <span data-ttu-id="be30e-119">È consigliabile che lo spazio dei nomi includa i componenti seguenti.</span><span class="sxs-lookup"><span data-stu-id="be30e-119">It is recommended that the namespace includes the following components.</span></span>

- <span data-ttu-id="be30e-120">Nome della società che produce il componente aggiuntivo</span><span class="sxs-lookup"><span data-stu-id="be30e-120">Company name producing the add-on</span></span>
- <span data-ttu-id="be30e-121">Area funzionale</span><span class="sxs-lookup"><span data-stu-id="be30e-121">Feature area</span></span>

<span data-ttu-id="be30e-122">Ad esempio, un provider di dati di riconoscimento spaziale creato e spedito dalla società Contoso può essere *"contoso. MixedReality. Toolkit. SpatialAwareness"*.</span><span class="sxs-lookup"><span data-stu-id="be30e-122">For example, a Spatial Awareness data provider created and shipped by the Contoso company may be *"Contoso.MixedReality.Toolkit.SpatialAwareness"*.</span></span>

<span data-ttu-id="be30e-123">**Struttura di cartelle**</span><span class="sxs-lookup"><span data-stu-id="be30e-123">**Folder structure**</span></span>

<span data-ttu-id="be30e-124">È consigliabile che il codice sorgente per i provider di dati venga disposto in una gerarchia di cartelle, come illustrato nella figura seguente.</span><span class="sxs-lookup"><span data-stu-id="be30e-124">It is recommended that the source code for data providers be layed out in a folder hierarchy as shown in the following image.</span></span>

![Esempio di struttura di cartelle](../images/spatial-awareness/ExampleProviderFolderStructure.png)

<span data-ttu-id="be30e-126">Se la cartella *ContosoSpatialAwareness* contiene l'implementazione del provider di dati, la cartella dell' *Editor* contiene il controllo (e qualsiasi altro codice specifico dell'editor Unity) e la cartella *profili* contiene uno o più oggetti di script del profilo predefiniti.</span><span class="sxs-lookup"><span data-stu-id="be30e-126">Where the *ContosoSpatialAwareness* folder contains the implementation of the data provider, the *Editor* folder contains the inspector (and any other Unity editor specific code), and the *Profiles* folder contains one or more pre-made profile scriptable objects.</span></span>

### <a name="mrtk-submission"></a><span data-ttu-id="be30e-127">Invio MRTK</span><span class="sxs-lookup"><span data-stu-id="be30e-127">MRTK submission</span></span>

<span data-ttu-id="be30e-128">**Namespace**</span><span class="sxs-lookup"><span data-stu-id="be30e-128">**Namespace**</span></span>

<span data-ttu-id="be30e-129">Se un provider di dati del sistema di riconoscimento spaziale viene inviato al repository del Toolkit per la [realtà mista](https://github.com/Microsoft/MixedRealityToolkit-Unity), lo spazio dei nomi **deve** iniziare con Microsoft. MixedReality. Toolkit (ad esempio: *Microsoft. MixedReality. Toolkit. SpatialObjectMeshObserver*)</span><span class="sxs-lookup"><span data-stu-id="be30e-129">If a spatial awareness system data provider is being submitted to the [Mixed Reality Toolkit repository](https://github.com/Microsoft/MixedRealityToolkit-Unity), the namespace **must** begin with Microsoft.MixedReality.Toolkit (ex: *Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver*)</span></span>

 <span data-ttu-id="be30e-130">e il codice deve trovarsi in una cartella sotto MRTK/Providers (ad esempio, *MRTK/Providers/ObjectMeshObserver*).</span><span class="sxs-lookup"><span data-stu-id="be30e-130">and the code should be located in a folder beneath MRTK/Providers (ex: *MRTK/Providers/ObjectMeshObserver*).</span></span>

<span data-ttu-id="be30e-131">**Struttura di cartelle**</span><span class="sxs-lookup"><span data-stu-id="be30e-131">**Folder structure**</span></span>

<span data-ttu-id="be30e-132">Tutto il codice deve trovarsi in una cartella sotto MRTK/Providers (ad esempio, MRTK/Providers/ObjectMeshObserver).</span><span class="sxs-lookup"><span data-stu-id="be30e-132">All code should be located in a folder beneath MRTK/Providers (ex: MRTK/Providers/ObjectMeshObserver).</span></span>

## <a name="define-the-spatial-data-object"></a><span data-ttu-id="be30e-133">Definire l'oggetto dati spaziali</span><span class="sxs-lookup"><span data-stu-id="be30e-133">Define the spatial data object</span></span>

<span data-ttu-id="be30e-134">Il primo passaggio nella creazione di un provider di dati di riconoscimento spaziale consiste nel determinare il tipo di dati (ad esempio, mesh o piani) che fornirà alle applicazioni.</span><span class="sxs-lookup"><span data-stu-id="be30e-134">The first step in creating a Spatial Awareness data provider is determining the type of data (ex: meshes or planes) it will provide to applications.</span></span>

<span data-ttu-id="be30e-135">Tutti gli oggetti dati spaziali devono implementare l' [`IMixedRealitySpatialAwarenessObject`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObject) interfaccia.</span><span class="sxs-lookup"><span data-stu-id="be30e-135">All spatial data objects must implement the [`IMixedRealitySpatialAwarenessObject`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObject) interface.</span></span>

<span data-ttu-id="be30e-136">Mixed Reality Toolkit Foundation fornisce gli oggetti spaziali seguenti che possono essere usati o estesi nei nuovi provider di dati.</span><span class="sxs-lookup"><span data-stu-id="be30e-136">The Mixed Reality Toolkit foundation provides the following spatial objects that can be used or extended in new data providers.</span></span>

- [`BaseSpatialAwarenessObject`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.BaseSpatialAwarenessObject)
- [`SpatialAwarenessMeshObject`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.SpatialAwarenessMeshObject)
- [`SpatialAwarenessPlanarObject`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.SpatialAwarenessPlanarObject)

## <a name="implement-the-data-provider"></a><span data-ttu-id="be30e-137">Implementare il provider di dati</span><span class="sxs-lookup"><span data-stu-id="be30e-137">Implement the data provider</span></span>

### <a name="specify-interface-andor-base-class-inheritance"></a><span data-ttu-id="be30e-138">Specificare l'ereditarietà dell'interfaccia e/o della classe base</span><span class="sxs-lookup"><span data-stu-id="be30e-138">Specify interface and/or base class inheritance</span></span>

<span data-ttu-id="be30e-139">Tutti i provider di dati di riconoscimento spaziale devono implementare l' [`IMixedRealitySpatialAwarenessObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver) interfaccia, che specifica la funzionalità minima richiesta dal sistema di riconoscimento spaziale.</span><span class="sxs-lookup"><span data-stu-id="be30e-139">All Spatial Awareness data providers must implement the [`IMixedRealitySpatialAwarenessObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver) interface, which specifies the minimum functionality required by the Spatial Awareness system.</span></span> <span data-ttu-id="be30e-140">MRTK Foundation include la [`BaseSpatialObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.BaseSpatialObserver) classe che fornisce un'implementazione predefinita di questa funzionalità richiesta.</span><span class="sxs-lookup"><span data-stu-id="be30e-140">The MRTK foundation includes the [`BaseSpatialObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.BaseSpatialObserver) class which provides a default implementation of this required functionality.</span></span>

```c#
public class SpatialObjectMeshObserver :
    BaseSpatialObserver,
    IMixedRealitySpatialAwarenessMeshObserver,
    IMixedRealityCapabilityCheck
{ }
```

> [!NOTE]
> <span data-ttu-id="be30e-141">L' [`IMixedRealityCapabilityCheck`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityCapabilityCheck) interfaccia viene utilizzata dalla [`SpatialObjectMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserver) classe per indicare che fornisce supporto per la funzionalità SpatialAwarenessMesh.</span><span class="sxs-lookup"><span data-stu-id="be30e-141">The [`IMixedRealityCapabilityCheck`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityCapabilityCheck) interface is used by the [`SpatialObjectMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserver) class to indicate that it provides support for the SpatialAwarenessMesh capability.</span></span>

#### <a name="apply-the-mixedrealitydataprovider-attribute"></a><span data-ttu-id="be30e-142">Applicare l'attributo MixedRealityDataProvider</span><span class="sxs-lookup"><span data-stu-id="be30e-142">Apply the MixedRealityDataProvider attribute</span></span>

<span data-ttu-id="be30e-143">Un passaggio chiave per la creazione di un provider di dati di riconoscimento spaziale consiste nell'applicare l' [`MixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.MixedRealityDataProviderAttribute) attributo alla classe.</span><span class="sxs-lookup"><span data-stu-id="be30e-143">A key step in creating a Spatial Awareness data provider is to apply the [`MixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.MixedRealityDataProviderAttribute) attribute to the class.</span></span> <span data-ttu-id="be30e-144">Questo passaggio consente di impostare il profilo e le piattaforme predefiniti per il provider di dati, se selezionato nel profilo di sensibilizzazione spaziale, nonché il nome, il percorso della cartella e altro ancora.</span><span class="sxs-lookup"><span data-stu-id="be30e-144">This step enables setting the default profile and platform(s) for the data provider, when selected in the Spatial Awareness profile as well as Name, folder path, and more.</span></span>

```c#
[MixedRealityDataProvider(
    typeof(IMixedRealitySpatialAwarenessSystem),
    SupportedPlatforms.WindowsEditor | SupportedPlatforms.MacEditor | SupportedPlatforms.LinuxEditor,
    "Spatial Object Mesh Observer",
    "ObjectMeshObserver/Profiles/DefaultObjectMeshObserverProfile.asset",
    "MixedRealityToolkit.Providers")]
public class SpatialObjectMeshObserver :
    BaseSpatialObserver,
    IMixedRealitySpatialAwarenessMeshObserver,
    IMixedRealityCapabilityCheck
{ }
```

### <a name="implement-the-imixedrealitydataprovider-methods"></a><span data-ttu-id="be30e-145">Implementare i metodi IMixedRealityDataProvider</span><span class="sxs-lookup"><span data-stu-id="be30e-145">Implement the IMixedRealityDataProvider methods</span></span>

<span data-ttu-id="be30e-146">Una volta definita la classe, il passaggio successivo consiste nel fornire l'implementazione dell' [`IMixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) interfaccia.</span><span class="sxs-lookup"><span data-stu-id="be30e-146">Once the class has been defined, the next step is to provide the implementation of the [`IMixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) interface.</span></span>

> [!NOTE]
> <span data-ttu-id="be30e-147">La [`BaseSpatialObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.BaseSpatialObserver) classe, tramite la [`BaseService`](xref:Microsoft.MixedReality.Toolkit.BaseService) classe, fornisce solo le implementazioni vuote per i [`IMixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) metodi.</span><span class="sxs-lookup"><span data-stu-id="be30e-147">The [`BaseSpatialObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.BaseSpatialObserver) class, via the [`BaseService`](xref:Microsoft.MixedReality.Toolkit.BaseService) class, provides only an empty implementations for [`IMixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) methods.</span></span> <span data-ttu-id="be30e-148">I dettagli di questi metodi sono in genere specifici del provider di dati.</span><span class="sxs-lookup"><span data-stu-id="be30e-148">The details of these methods are generally data provider specific.</span></span>

<span data-ttu-id="be30e-149">I metodi che devono essere implementati dal provider di dati sono:</span><span class="sxs-lookup"><span data-stu-id="be30e-149">The methods that should be implemented by the data provider are:</span></span>

- `Destroy()`
- `Disable()`
- `Enable()`
- `Initialize()`
- `Reset()`
- `Update()`

### <a name="implement-the-data-provider-logic"></a><span data-ttu-id="be30e-150">Implementare la logica del provider di dati</span><span class="sxs-lookup"><span data-stu-id="be30e-150">Implement the data provider logic</span></span>

<span data-ttu-id="be30e-151">Il passaggio successivo consiste nell'aggiungere la logica del provider di dati implementando, ad esempio, l'interfaccia del provider di dati specifica [`IMixedRealitySpatialAwarenessMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessMeshObserver) .</span><span class="sxs-lookup"><span data-stu-id="be30e-151">The next step is to add the logic of the data provider by implementing the specific data provider interface, for example [`IMixedRealitySpatialAwarenessMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessMeshObserver).</span></span> <span data-ttu-id="be30e-152">Questa parte del provider di dati sarà in genere specifica della piattaforma.</span><span class="sxs-lookup"><span data-stu-id="be30e-152">This portion of the data provider will typically be platform specific.</span></span>

### <a name="observation-change-notifications"></a><span data-ttu-id="be30e-153">Notifiche delle modifiche di osservazione</span><span class="sxs-lookup"><span data-stu-id="be30e-153">Observation change notifications</span></span>

<span data-ttu-id="be30e-154">Per consentire alle applicazioni di rispondere alle modifiche apportate alla comprensione dell'ambiente del dispositivo, il provider di dati genera eventi di notifica come definito nell' [`IMixedRealitySpatialAwarenessObservationtHandler<T>`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObservationHandler`1) interfaccia.</span><span class="sxs-lookup"><span data-stu-id="be30e-154">To allow applications to respond to changes in the device's understanding of the environment, the data provider raises notification events as defined in the [`IMixedRealitySpatialAwarenessObservationtHandler<T>`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObservationHandler`1) interface.</span></span>

- `OnObservationAdded()`
- `OnObservationRemoved()`
- `OnObservationUpdated()`

 <span data-ttu-id="be30e-155">Il codice seguente degli [`SpatialObjectMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserver) esempi illustra la generazione e l'evento quando vengono aggiunti dati mesh.</span><span class="sxs-lookup"><span data-stu-id="be30e-155">The following code from the [`SpatialObjectMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserver) examples demonstrates raising and event when mesh data is added.</span></span>

```c#
// The data to be sent when mesh observation events occur.
// This member variable is initialized as part of the Initialize() method.
private MixedRealitySpatialAwarenessEventData<SpatialAwarenessMeshObject> meshEventData = null;

/// <summary>
/// Sends the observations using the mesh data contained within the configured 3D model.
/// </summary>
private void SendMeshObjects()
{
    if (!sendObservations) { return; }

    if (spatialMeshObject != null)
    {
        MeshFilter[] meshFilters = spatialMeshObject.GetComponentsInChildren<MeshFilter>();
        for (int i = 0; i < meshFilters.Length; i++)
        {
            SpatialAwarenessMeshObject meshObject = SpatialAwarenessMeshObject.Create(
                meshFilters[i].sharedMesh,
                MeshPhysicsLayer,
                $"Spatial Object Mesh {currentMeshId}",
                currentMeshId,
                ObservedObjectParent);

            meshObject.GameObject.transform.localPosition = meshFilters[i].transform.position;
            meshObject.GameObject.transform.localRotation = meshFilters[i].transform.rotation;

            ApplyMeshMaterial(meshObject);

            meshes.Add(currentMeshId, meshObject);

            // Initialize the meshEventData variable with data for the added event.
            meshEventData.Initialize(this, currentMeshId, meshObject);
            // Raise the event via the spatial awareness system.
            SpatialAwarenessSystem?.HandleEvent(meshEventData, OnMeshAdded);

            currentMeshId++;
        }
    }

    sendObservations = false;
}
```

> [!NOTE]
> <span data-ttu-id="be30e-156">La [`SpatialObjectMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserver) classe non genera `OnObservationUpdated` eventi perché il modello 3D viene caricato una sola volta.</span><span class="sxs-lookup"><span data-stu-id="be30e-156">The [`SpatialObjectMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserver) class does not raise `OnObservationUpdated` events since the 3D model is only loaded once.</span></span> <span data-ttu-id="be30e-157">L'implementazione nella [`WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver) classe fornisce un esempio di generazione di un `OnObservationUpdated` evento per una mesh osservata.</span><span class="sxs-lookup"><span data-stu-id="be30e-157">The implementation in the [`WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver) class provides an example of raising an `OnObservationUpdated` event for an observed mesh.</span></span>

### <a name="add-unity-profiler-instrumentation"></a><span data-ttu-id="be30e-158">Aggiungere la strumentazione del profiler Unity</span><span class="sxs-lookup"><span data-stu-id="be30e-158">Add Unity Profiler instrumentation</span></span>

<span data-ttu-id="be30e-159">Le prestazioni sono cruciali nelle applicazioni di realtà mista.</span><span class="sxs-lookup"><span data-stu-id="be30e-159">Performance is critical in mixed reality applications.</span></span> <span data-ttu-id="be30e-160">Ogni componente aggiunge una certa quantità di overhead per cui le applicazioni devono tenere conto.</span><span class="sxs-lookup"><span data-stu-id="be30e-160">Every component adds some amount of overhead for which applications must account.</span></span> <span data-ttu-id="be30e-161">A questo scopo, è importante che tutti i provider di dati di consapevolezza spaziale contengano la strumentazione del profiler di Unity nel ciclo interno e i percorsi di codice utilizzati di frequente</span><span class="sxs-lookup"><span data-stu-id="be30e-161">To this end, it is important that all spatial awareness data providers contain Unity Profiler instrumentation in inner loop and frequently utilized code paths.</span></span>

<span data-ttu-id="be30e-162">È consigliabile implementare il modello utilizzato da MRTK quando si instrumentano provider personalizzati.</span><span class="sxs-lookup"><span data-stu-id="be30e-162">It is recommended to implement the pattern utilized by the MRTK when instrumenting custom providers.</span></span>

```c#
        private static readonly ProfilerMarker UpdateObserverPerfMarker = new ProfilerMarker("[MRTK] WindowsMixedRealitySpatialMeshObserver.UpdateObserver");

        /// <summary>
        /// Requests updates from the surface observer.
        /// </summary>
        private void UpdateObserver()
        {
            using (UpdateObserverPerfMarker.Auto())
            {
                // Code to be measured.
            }
        }
```

> [!Note]
> <span data-ttu-id="be30e-163">Il nome utilizzato per identificare il marcatore del profiler è arbitrario.</span><span class="sxs-lookup"><span data-stu-id="be30e-163">The name used to identify the profiler marker is arbitrary.</span></span> <span data-ttu-id="be30e-164">MRTK usa il modello seguente.</span><span class="sxs-lookup"><span data-stu-id="be30e-164">The MRTK uses the following pattern.</span></span>
>
> <span data-ttu-id="be30e-165">"[Product] nomeclasse. MethodName-nota facoltativa"</span><span class="sxs-lookup"><span data-stu-id="be30e-165">"[product] className.methodName - optional note"</span></span>
>
> <span data-ttu-id="be30e-166">È consigliabile che i provider di dati personalizzati seguano un modello simile per semplificare l'identificazione di componenti e metodi specifici durante l'analisi delle tracce.</span><span class="sxs-lookup"><span data-stu-id="be30e-166">It is recommended that custom data providers follow a similar pattern to help simplify identification of specific components and methods when analyzing traces.</span></span>

## <a name="create-the-profile-and-inspector"></a><span data-ttu-id="be30e-167">Creare il profilo e il controllo</span><span class="sxs-lookup"><span data-stu-id="be30e-167">Create the profile and inspector</span></span>

<span data-ttu-id="be30e-168">Nel Toolkit per la realtà mista i provider di dati vengono configurati usando i [profili](../profiles/profiles.md).</span><span class="sxs-lookup"><span data-stu-id="be30e-168">In the Mixed Reality Toolkit, data providers are configured using [profiles](../profiles/profiles.md).</span></span>

### <a name="define-the-profile"></a><span data-ttu-id="be30e-169">Definire il profilo</span><span class="sxs-lookup"><span data-stu-id="be30e-169">Define the profile</span></span>

<span data-ttu-id="be30e-170">Il contenuto del profilo dovrebbe rispecchiare le proprietà accessibili del provider di dati (ad esempio, intervallo di aggiornamento).</span><span class="sxs-lookup"><span data-stu-id="be30e-170">Profile contents should mirror the accessible properties of the data provider (ex: update interval).</span></span> <span data-ttu-id="be30e-171">Tutte le proprietà configurabili dall'utente definite in ogni interfaccia devono essere contenute nel profilo.</span><span class="sxs-lookup"><span data-stu-id="be30e-171">All of the user configurable properties defined in each interface should be contained with the profile.</span></span>

<span data-ttu-id="be30e-172">Le classi base sono consigliate Se un nuovo provider di dati estende un provider esistente.</span><span class="sxs-lookup"><span data-stu-id="be30e-172">Base classes are encouraged if a new data provider extends an existing provider.</span></span> <span data-ttu-id="be30e-173">Ad esempio, [`SpatialObjectMeshObserverProfile`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserverProfile) estende per [`MixedRealitySpatialAwarenessMeshObserverProfile`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.MixedRealitySpatialAwarenessMeshObserverProfile) consentire ai clienti di fornire un modello 3D da utilizzare come dati dell'ambiente.</span><span class="sxs-lookup"><span data-stu-id="be30e-173">For example, the [`SpatialObjectMeshObserverProfile`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserverProfile) extends the [`MixedRealitySpatialAwarenessMeshObserverProfile`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.MixedRealitySpatialAwarenessMeshObserverProfile) to enable customers to provide a 3D model to be used as the environment data.</span></span>

```c#
[CreateAssetMenu(
    menuName = "Mixed Reality Toolkit/Profiles/Spatial Object Mesh Observer Profile",
    fileName = "SpatialObjectMeshObserverProfile",
    order = 100)]
public class SpatialObjectMeshObserverProfile : MixedRealitySpatialAwarenessMeshObserverProfile
{
    [SerializeField]
    [Tooltip("The model containing the desired mesh data.")]
    private GameObject spatialMeshObject = null;

    /// <summary>
    /// The model containing the desired mesh data.
    /// </summary>
    public GameObject SpatialMeshObject => spatialMeshObject;
}
```

<span data-ttu-id="be30e-174">L' `CreateAssetMenu` attributo può essere applicato alla classe del profilo per consentire ai clienti di creare un'istanza del profilo usando il menu **Crea** i  >    >  profili di **Toolkit di realtà mista**  >   .</span><span class="sxs-lookup"><span data-stu-id="be30e-174">The `CreateAssetMenu` attribute can be applied to the profile class to enable customers to create a profile instance using the **Create** > **Assets** > **Mixed Reality Toolkit** > **Profiles** menu.</span></span>

### <a name="implement-the-inspector"></a><span data-ttu-id="be30e-175">Implementare il controllo</span><span class="sxs-lookup"><span data-stu-id="be30e-175">Implement the inspector</span></span>

<span data-ttu-id="be30e-176">I controlli profilo sono l'interfaccia utente per la configurazione e la visualizzazione del contenuto del profilo.</span><span class="sxs-lookup"><span data-stu-id="be30e-176">Profile inspectors are the user interface for configuring and viewing profile contents.</span></span> <span data-ttu-id="be30e-177">Ogni controllo profilo deve estendere la [`BaseMixedRealityToolkitConfigurationProfileInspector`](xref:Microsoft.MixedReality.Toolkit.Editor.BaseMixedRealityToolkitConfigurationProfileInspector) classe.</span><span class="sxs-lookup"><span data-stu-id="be30e-177">Each profile inspector should extend the [`BaseMixedRealityToolkitConfigurationProfileInspector`](xref:Microsoft.MixedReality.Toolkit.Editor.BaseMixedRealityToolkitConfigurationProfileInspector) class.</span></span>

<span data-ttu-id="be30e-178">L' `CustomEditor` attributo informa Unity del tipo di asset a cui si applica il controllo.</span><span class="sxs-lookup"><span data-stu-id="be30e-178">The `CustomEditor` attribute informs Unity the type of asset to which the inspector applies.</span></span>

```c#
[CustomEditor(typeof(SpatialObjectMeshObserverProfile))]
public class SpatialObjectMeshObserverProfileInspector : BaseMixedRealityToolkitConfigurationProfileInspector
{ }
```

## <a name="create-assembly-definitions"></a><span data-ttu-id="be30e-179">Crea definizione/i assembly</span><span class="sxs-lookup"><span data-stu-id="be30e-179">Create assembly definition(s)</span></span>

<span data-ttu-id="be30e-180">Il Toolkit di realtà mista Usa i file di definizione di assembly (con[estensione asmdef](https://docs.unity3d.com/Manual/ScriptCompilationAssemblyDefinitionFiles.html)) per specificare le dipendenze tra i componenti e per aiutare Unity a ridurre i tempi di compilazione.</span><span class="sxs-lookup"><span data-stu-id="be30e-180">The Mixed Reality Toolkit uses assembly definition ([.asmdef](https://docs.unity3d.com/Manual/ScriptCompilationAssemblyDefinitionFiles.html)) files to specify dependencies between components as well as to assist Unity in reducing compilation time.</span></span>

<span data-ttu-id="be30e-181">Si consiglia di creare i file di definizione degli assembly per tutti i provider di dati e i relativi componenti dell'editor.</span><span class="sxs-lookup"><span data-stu-id="be30e-181">It is recommended that assembly definition files are created for all data providers and their editor components.</span></span>

<span data-ttu-id="be30e-182">Usando la [struttura di cartelle](#namespace-and-folder-structure) nell'esempio precedente, sono presenti due file. asmdef per il provider di dati ContosoSpatialAwareness.</span><span class="sxs-lookup"><span data-stu-id="be30e-182">Using the [folder structure](#namespace-and-folder-structure) in the earlier example, there would be two .asmdef files for the ContosoSpatialAwareness data provider.</span></span>

<span data-ttu-id="be30e-183">La prima definizione di assembly è per il provider di dati.</span><span class="sxs-lookup"><span data-stu-id="be30e-183">The first assembly definition is for the data provider.</span></span> <span data-ttu-id="be30e-184">Per questo esempio, viene chiamato ContosoSpatialAwareness e si trova nella cartella *ContosoSpatialAwareness* dell'esempio.</span><span class="sxs-lookup"><span data-stu-id="be30e-184">For this example, it will be called ContosoSpatialAwareness and will be located in the example's *ContosoSpatialAwareness* folder.</span></span> <span data-ttu-id="be30e-185">Questa definizione di assembly deve specificare una dipendenza da Microsoft. MixedReality. Toolkit e da tutti gli altri assembly da cui dipende.</span><span class="sxs-lookup"><span data-stu-id="be30e-185">This assembly definition must specify a dependency on Microsoft.MixedReality.Toolkit and any other assemblies upon which it depends.</span></span>

<span data-ttu-id="be30e-186">La definizione dell'assembly ContosoInputEditor specifica il controllo del profilo e qualsiasi codice specifico dell'editor.</span><span class="sxs-lookup"><span data-stu-id="be30e-186">The ContosoInputEditor assembly definition will specify the profile inspector and any editor specific code.</span></span> <span data-ttu-id="be30e-187">Questo file deve trovarsi nella cartella radice del codice dell'editor.</span><span class="sxs-lookup"><span data-stu-id="be30e-187">This file must be located in the root folder of the editor code.</span></span> <span data-ttu-id="be30e-188">In questo esempio il file si trova nella cartella *ContosoSpatialAwareness\Editor*</span><span class="sxs-lookup"><span data-stu-id="be30e-188">In this example, the file will be located in the *ContosoSpatialAwareness\Editor* folder.</span></span> <span data-ttu-id="be30e-189">Questa definizione di assembly conterrà un riferimento all'assembly ContosoSpatialAwareness, oltre a:</span><span class="sxs-lookup"><span data-stu-id="be30e-189">This assembly definition will contain a reference to the ContosoSpatialAwareness assembly as well as:</span></span>

- <span data-ttu-id="be30e-190">Microsoft. MixedReality. Toolkit</span><span class="sxs-lookup"><span data-stu-id="be30e-190">Microsoft.MixedReality.Toolkit</span></span>
- <span data-ttu-id="be30e-191">Microsoft. MixedReality. Toolkit. Editor. Inspectors</span><span class="sxs-lookup"><span data-stu-id="be30e-191">Microsoft.MixedReality.Toolkit.Editor.Inspectors</span></span>
- <span data-ttu-id="be30e-192">Microsoft. MixedReality. Toolkit. Editor. Utilities</span><span class="sxs-lookup"><span data-stu-id="be30e-192">Microsoft.MixedReality.Toolkit.Editor.Utilities</span></span>

## <a name="register-the-data-provider"></a><span data-ttu-id="be30e-193">Registrare il provider di dati</span><span class="sxs-lookup"><span data-stu-id="be30e-193">Register the data provider</span></span>

<span data-ttu-id="be30e-194">Una volta creato, il provider di dati può essere registrato con il sistema di riconoscimento spaziale da usare nell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="be30e-194">Once created, the data provider can be registered with the Spatial Awareness system to be used in the application.</span></span>

![Selezione dell'osservatore mesh dell'oggetto spaziale](../images/spatial-awareness/SelectObjectObserver.png)

## <a name="packaging-and-distribution"></a><span data-ttu-id="be30e-196">Creazione di pacchetti e distribuzione</span><span class="sxs-lookup"><span data-stu-id="be30e-196">Packaging and distribution</span></span>

<span data-ttu-id="be30e-197">I provider di dati distribuiti come componenti di terze parti presentano i dettagli specifici della creazione di pacchetti e della distribuzione, a seconda delle preferenze dello sviluppatore.</span><span class="sxs-lookup"><span data-stu-id="be30e-197">Data providers that are distributed as third party components have the specific details of packaging and distribution left to the preference of the developer.</span></span> <span data-ttu-id="be30e-198">Probabilmente, la soluzione più comune consiste nel generare un file con estensione file unitypackage Tools e distribuirlo tramite l'archivio risorse di Unity.</span><span class="sxs-lookup"><span data-stu-id="be30e-198">Likely, the most common solution will be to generate a .unitypackage and distribute via the Unity Asset Store.</span></span>

<span data-ttu-id="be30e-199">Se un provider di dati viene inviato e accettato come parte del pacchetto Microsoft Mixed Reality Toolkit, il team di Microsoft MRTK lo comprimerà e lo distribuirà come parte delle offerte di MRTK.</span><span class="sxs-lookup"><span data-stu-id="be30e-199">If a data provider is submitted and accepted as a part of the Microsoft Mixed Reality Toolkit package, the Microsoft MRTK team will package and distribute it as part of the MRTK offerings.</span></span>

## <a name="see-also"></a><span data-ttu-id="be30e-200">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="be30e-200">See also</span></span>

- [<span data-ttu-id="be30e-201">Sistema di riconoscimento spaziale</span><span class="sxs-lookup"><span data-stu-id="be30e-201">Spatial awareness system</span></span>](spatial-awareness-getting-started.md)
- [<span data-ttu-id="be30e-202">`IMixedRealitySpatialAwarenessObject` interfaccia</span><span class="sxs-lookup"><span data-stu-id="be30e-202">`IMixedRealitySpatialAwarenessObject` interface</span></span>](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObject)
- [<span data-ttu-id="be30e-203">`BaseSpatialAwarenessObject` classe</span><span class="sxs-lookup"><span data-stu-id="be30e-203">`BaseSpatialAwarenessObject` class</span></span>](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.BaseSpatialAwarenessObject)
- [<span data-ttu-id="be30e-204">`SpatialAwarenessMeshObject` classe</span><span class="sxs-lookup"><span data-stu-id="be30e-204">`SpatialAwarenessMeshObject` class</span></span>](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.SpatialAwarenessMeshObject)
- [<span data-ttu-id="be30e-205">`SpatialAwarenessPlanarObject` classe</span><span class="sxs-lookup"><span data-stu-id="be30e-205">`SpatialAwarenessPlanarObject` class</span></span>](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.SpatialAwarenessPlanarObject)
- [<span data-ttu-id="be30e-206">`IMixedRealitySpatialAwarenessObserver` interfaccia</span><span class="sxs-lookup"><span data-stu-id="be30e-206">`IMixedRealitySpatialAwarenessObserver` interface</span></span>](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver)
- [<span data-ttu-id="be30e-207">`BaseSpatialObserver` classe</span><span class="sxs-lookup"><span data-stu-id="be30e-207">`BaseSpatialObserver` class</span></span>](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.BaseSpatialObserver)
- [<span data-ttu-id="be30e-208">`IMixedRealitySpatialAwarenessMeshObserver` interfaccia</span><span class="sxs-lookup"><span data-stu-id="be30e-208">`IMixedRealitySpatialAwarenessMeshObserver` interface</span></span>](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessMeshObserver)
- [<span data-ttu-id="be30e-209">`IMixedRealityDataProvider` interfaccia</span><span class="sxs-lookup"><span data-stu-id="be30e-209">`IMixedRealityDataProvider` interface</span></span>](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider)
- [<span data-ttu-id="be30e-210">`IMixedRealityCapabilityCheck` interfaccia</span><span class="sxs-lookup"><span data-stu-id="be30e-210">`IMixedRealityCapabilityCheck` interface</span></span>](xref:Microsoft.MixedReality.Toolkit.IMixedRealityCapabilityCheck)

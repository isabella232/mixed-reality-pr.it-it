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
# <a name="creating-a-spatial-awareness-system-data-provider"></a>Creazione di un provider di dati di sistema di riconoscimento spaziale

Il sistema di riconoscimento spaziale è un sistema estensibile per fornire applicazioni con dati sugli ambienti reali. Per aggiungere il supporto per una nuova piattaforma hardware o un nuovo tipo di dati di riconoscimento spaziale, potrebbe essere necessario un provider di dati personalizzato.

Questo articolo descrive come creare [provider di dati personalizzati](../../architecture/systems-extensions-providers.md), denominati anche osservatori spaziali, per il sistema di riconoscimento spaziale. Il codice di esempio illustrato di seguito è [`SpatialObjectMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserver) relativo all'implementazione della classe, [utile per il caricamento di dati mesh 3D nell'editor](spatial-object-mesh-observer.md).

> [!NOTE]
> Il codice sorgente completo usato in questo esempio si trova nella `Assets/MRTK/Providers/ObjectMeshObserver` cartella.

## <a name="namespace-and-folder-structure"></a>Struttura dello spazio dei nomi e della cartella

I provider di dati possono essere distribuiti in uno dei due modi seguenti:

1. Componenti aggiuntivi di terze parti
1. Parte del Toolkit Microsoft Mixed Reality

Il processo di approvazione per gli invii di nuovi provider di dati alla MRTK varia a seconda del caso e verrà comunicato al momento della proposta iniziale di. È possibile inviare proposte creando un nuovo [problema relativo al tipo di *richiesta di funzionalità*](https://github.com/microsoft/MixedRealityToolkit-Unity/issues).

### <a name="third-party-add-on"></a>Componente aggiuntivo di terze parti

**Namespace**

È necessario che i provider di dati dispongano di uno spazio dei nomi per attenuare i potenziali conflitti di nomi. È consigliabile che lo spazio dei nomi includa i componenti seguenti.

- Nome della società che produce il componente aggiuntivo
- Area funzionale

Ad esempio, un provider di dati di riconoscimento spaziale creato e spedito dalla società Contoso può essere *"contoso. MixedReality. Toolkit. SpatialAwareness"*.

**Struttura di cartelle**

È consigliabile che il codice sorgente per i provider di dati venga disposto in una gerarchia di cartelle, come illustrato nella figura seguente.

![Esempio di struttura di cartelle](../images/spatial-awareness/ExampleProviderFolderStructure.png)

Se la cartella *ContosoSpatialAwareness* contiene l'implementazione del provider di dati, la cartella dell' *Editor* contiene il controllo (e qualsiasi altro codice specifico dell'editor Unity) e la cartella *profili* contiene uno o più oggetti di script del profilo predefiniti.

### <a name="mrtk-submission"></a>Invio MRTK

**Namespace**

Se un provider di dati del sistema di riconoscimento spaziale viene inviato al repository del Toolkit per la [realtà mista](https://github.com/Microsoft/MixedRealityToolkit-Unity), lo spazio dei nomi **deve** iniziare con Microsoft. MixedReality. Toolkit (ad esempio: *Microsoft. MixedReality. Toolkit. SpatialObjectMeshObserver*)

 e il codice deve trovarsi in una cartella sotto MRTK/Providers (ad esempio, *MRTK/Providers/ObjectMeshObserver*).

**Struttura di cartelle**

Tutto il codice deve trovarsi in una cartella sotto MRTK/Providers (ad esempio, MRTK/Providers/ObjectMeshObserver).

## <a name="define-the-spatial-data-object"></a>Definire l'oggetto dati spaziali

Il primo passaggio nella creazione di un provider di dati di riconoscimento spaziale consiste nel determinare il tipo di dati (ad esempio, mesh o piani) che fornirà alle applicazioni.

Tutti gli oggetti dati spaziali devono implementare l' [`IMixedRealitySpatialAwarenessObject`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObject) interfaccia.

Mixed Reality Toolkit Foundation fornisce gli oggetti spaziali seguenti che possono essere usati o estesi nei nuovi provider di dati.

- [`BaseSpatialAwarenessObject`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.BaseSpatialAwarenessObject)
- [`SpatialAwarenessMeshObject`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.SpatialAwarenessMeshObject)
- [`SpatialAwarenessPlanarObject`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.SpatialAwarenessPlanarObject)

## <a name="implement-the-data-provider"></a>Implementare il provider di dati

### <a name="specify-interface-andor-base-class-inheritance"></a>Specificare l'ereditarietà dell'interfaccia e/o della classe base

Tutti i provider di dati di riconoscimento spaziale devono implementare l' [`IMixedRealitySpatialAwarenessObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver) interfaccia, che specifica la funzionalità minima richiesta dal sistema di riconoscimento spaziale. MRTK Foundation include la [`BaseSpatialObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.BaseSpatialObserver) classe che fornisce un'implementazione predefinita di questa funzionalità richiesta.

```c#
public class SpatialObjectMeshObserver :
    BaseSpatialObserver,
    IMixedRealitySpatialAwarenessMeshObserver,
    IMixedRealityCapabilityCheck
{ }
```

> [!NOTE]
> L' [`IMixedRealityCapabilityCheck`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityCapabilityCheck) interfaccia viene utilizzata dalla [`SpatialObjectMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserver) classe per indicare che fornisce supporto per la funzionalità SpatialAwarenessMesh.

#### <a name="apply-the-mixedrealitydataprovider-attribute"></a>Applicare l'attributo MixedRealityDataProvider

Un passaggio chiave per la creazione di un provider di dati di riconoscimento spaziale consiste nell'applicare l' [`MixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.MixedRealityDataProviderAttribute) attributo alla classe. Questo passaggio consente di impostare il profilo e le piattaforme predefiniti per il provider di dati, se selezionato nel profilo di sensibilizzazione spaziale, nonché il nome, il percorso della cartella e altro ancora.

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

### <a name="implement-the-imixedrealitydataprovider-methods"></a>Implementare i metodi IMixedRealityDataProvider

Una volta definita la classe, il passaggio successivo consiste nel fornire l'implementazione dell' [`IMixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) interfaccia.

> [!NOTE]
> La [`BaseSpatialObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.BaseSpatialObserver) classe, tramite la [`BaseService`](xref:Microsoft.MixedReality.Toolkit.BaseService) classe, fornisce solo le implementazioni vuote per i [`IMixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) metodi. I dettagli di questi metodi sono in genere specifici del provider di dati.

I metodi che devono essere implementati dal provider di dati sono:

- `Destroy()`
- `Disable()`
- `Enable()`
- `Initialize()`
- `Reset()`
- `Update()`

### <a name="implement-the-data-provider-logic"></a>Implementare la logica del provider di dati

Il passaggio successivo consiste nell'aggiungere la logica del provider di dati implementando, ad esempio, l'interfaccia del provider di dati specifica [`IMixedRealitySpatialAwarenessMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessMeshObserver) . Questa parte del provider di dati sarà in genere specifica della piattaforma.

### <a name="observation-change-notifications"></a>Notifiche delle modifiche di osservazione

Per consentire alle applicazioni di rispondere alle modifiche apportate alla comprensione dell'ambiente del dispositivo, il provider di dati genera eventi di notifica come definito nell' [`IMixedRealitySpatialAwarenessObservationtHandler<T>`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObservationHandler`1) interfaccia.

- `OnObservationAdded()`
- `OnObservationRemoved()`
- `OnObservationUpdated()`

 Il codice seguente degli [`SpatialObjectMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserver) esempi illustra la generazione e l'evento quando vengono aggiunti dati mesh.

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
> La [`SpatialObjectMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserver) classe non genera `OnObservationUpdated` eventi perché il modello 3D viene caricato una sola volta. L'implementazione nella [`WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver) classe fornisce un esempio di generazione di un `OnObservationUpdated` evento per una mesh osservata.

### <a name="add-unity-profiler-instrumentation"></a>Aggiungere la strumentazione del profiler Unity

Le prestazioni sono cruciali nelle applicazioni di realtà mista. Ogni componente aggiunge una certa quantità di overhead per cui le applicazioni devono tenere conto. A questo scopo, è importante che tutti i provider di dati di consapevolezza spaziale contengano la strumentazione del profiler di Unity nel ciclo interno e i percorsi di codice utilizzati di frequente

È consigliabile implementare il modello utilizzato da MRTK quando si instrumentano provider personalizzati.

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
> Il nome utilizzato per identificare il marcatore del profiler è arbitrario. MRTK usa il modello seguente.
>
> "[Product] nomeclasse. MethodName-nota facoltativa"
>
> È consigliabile che i provider di dati personalizzati seguano un modello simile per semplificare l'identificazione di componenti e metodi specifici durante l'analisi delle tracce.

## <a name="create-the-profile-and-inspector"></a>Creare il profilo e il controllo

Nel Toolkit per la realtà mista i provider di dati vengono configurati usando i [profili](../profiles/profiles.md).

### <a name="define-the-profile"></a>Definire il profilo

Il contenuto del profilo dovrebbe rispecchiare le proprietà accessibili del provider di dati (ad esempio, intervallo di aggiornamento). Tutte le proprietà configurabili dall'utente definite in ogni interfaccia devono essere contenute nel profilo.

Le classi base sono consigliate Se un nuovo provider di dati estende un provider esistente. Ad esempio, [`SpatialObjectMeshObserverProfile`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserverProfile) estende per [`MixedRealitySpatialAwarenessMeshObserverProfile`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.MixedRealitySpatialAwarenessMeshObserverProfile) consentire ai clienti di fornire un modello 3D da utilizzare come dati dell'ambiente.

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

L' `CreateAssetMenu` attributo può essere applicato alla classe del profilo per consentire ai clienti di creare un'istanza del profilo usando il menu **Crea** i  >    >  profili di **Toolkit di realtà mista**  >   .

### <a name="implement-the-inspector"></a>Implementare il controllo

I controlli profilo sono l'interfaccia utente per la configurazione e la visualizzazione del contenuto del profilo. Ogni controllo profilo deve estendere la [`BaseMixedRealityToolkitConfigurationProfileInspector`](xref:Microsoft.MixedReality.Toolkit.Editor.BaseMixedRealityToolkitConfigurationProfileInspector) classe.

L' `CustomEditor` attributo informa Unity del tipo di asset a cui si applica il controllo.

```c#
[CustomEditor(typeof(SpatialObjectMeshObserverProfile))]
public class SpatialObjectMeshObserverProfileInspector : BaseMixedRealityToolkitConfigurationProfileInspector
{ }
```

## <a name="create-assembly-definitions"></a>Crea definizione/i assembly

Il Toolkit di realtà mista Usa i file di definizione di assembly (con[estensione asmdef](https://docs.unity3d.com/Manual/ScriptCompilationAssemblyDefinitionFiles.html)) per specificare le dipendenze tra i componenti e per aiutare Unity a ridurre i tempi di compilazione.

Si consiglia di creare i file di definizione degli assembly per tutti i provider di dati e i relativi componenti dell'editor.

Usando la [struttura di cartelle](#namespace-and-folder-structure) nell'esempio precedente, sono presenti due file. asmdef per il provider di dati ContosoSpatialAwareness.

La prima definizione di assembly è per il provider di dati. Per questo esempio, viene chiamato ContosoSpatialAwareness e si trova nella cartella *ContosoSpatialAwareness* dell'esempio. Questa definizione di assembly deve specificare una dipendenza da Microsoft. MixedReality. Toolkit e da tutti gli altri assembly da cui dipende.

La definizione dell'assembly ContosoInputEditor specifica il controllo del profilo e qualsiasi codice specifico dell'editor. Questo file deve trovarsi nella cartella radice del codice dell'editor. In questo esempio il file si trova nella cartella *ContosoSpatialAwareness\Editor* Questa definizione di assembly conterrà un riferimento all'assembly ContosoSpatialAwareness, oltre a:

- Microsoft. MixedReality. Toolkit
- Microsoft. MixedReality. Toolkit. Editor. Inspectors
- Microsoft. MixedReality. Toolkit. Editor. Utilities

## <a name="register-the-data-provider"></a>Registrare il provider di dati

Una volta creato, il provider di dati può essere registrato con il sistema di riconoscimento spaziale da usare nell'applicazione.

![Selezione dell'osservatore mesh dell'oggetto spaziale](../images/spatial-awareness/SelectObjectObserver.png)

## <a name="packaging-and-distribution"></a>Creazione di pacchetti e distribuzione

I provider di dati distribuiti come componenti di terze parti presentano i dettagli specifici della creazione di pacchetti e della distribuzione, a seconda delle preferenze dello sviluppatore. Probabilmente, la soluzione più comune consiste nel generare un file con estensione file unitypackage Tools e distribuirlo tramite l'archivio risorse di Unity.

Se un provider di dati viene inviato e accettato come parte del pacchetto Microsoft Mixed Reality Toolkit, il team di Microsoft MRTK lo comprimerà e lo distribuirà come parte delle offerte di MRTK.

## <a name="see-also"></a>Vedi anche

- [Sistema di riconoscimento spaziale](spatial-awareness-getting-started.md)
- [`IMixedRealitySpatialAwarenessObject` interfaccia](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObject)
- [`BaseSpatialAwarenessObject` classe](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.BaseSpatialAwarenessObject)
- [`SpatialAwarenessMeshObject` classe](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.SpatialAwarenessMeshObject)
- [`SpatialAwarenessPlanarObject` classe](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.SpatialAwarenessPlanarObject)
- [`IMixedRealitySpatialAwarenessObserver` interfaccia](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver)
- [`BaseSpatialObserver` classe](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.BaseSpatialObserver)
- [`IMixedRealitySpatialAwarenessMeshObserver` interfaccia](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessMeshObserver)
- [`IMixedRealityDataProvider` interfaccia](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider)
- [`IMixedRealityCapabilityCheck` interfaccia](xref:Microsoft.MixedReality.Toolkit.IMixedRealityCapabilityCheck)

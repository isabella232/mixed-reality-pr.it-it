---
title: CreateSpatialAwarenessDataProvider
description: descrive come creare provider di dati personalizzati in MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: 31c9e0e7eba39c55068212e064407364434d6ca7d4e56af00528147969648f60
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115196345"
---
# <a name="creating-a-spatial-awareness-system-data-provider"></a>Creazione di un provider di dati del sistema di riconoscimento spaziale

Il sistema Di consapevolezza spaziale è un sistema estendibile per fornire alle applicazioni dati sugli ambienti reali. Per aggiungere il supporto per una nuova piattaforma hardware o una nuova forma di dati di riconoscimento spaziale, potrebbe essere necessario un provider di dati personalizzato.

Questo articolo descrive come creare provider di dati [personalizzati,](../../architecture/systems-extensions-providers.md)denominati anche osservatori spaziali, per il sistema di consapevolezza spaziale. Il codice di esempio illustrato di seguito deriva dall'implementazione della classe , utile per il caricamento di dati mesh [`SpatialObjectMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserver) [3D nell'editor](spatial-object-mesh-observer.md).

> [!NOTE]
> Il codice sorgente completo usato in questo esempio è disponibile nella `Assets/MRTK/Providers/ObjectMeshObserver` cartella .

## <a name="namespace-and-folder-structure"></a>Spazio dei nomi e struttura di cartelle

I provider di dati possono essere distribuiti in uno dei due modi seguenti:

1. Componenti aggiuntivi di terze parti
1. Parte di Microsoft Mixed Reality Toolkit

Il processo di approvazione per l'invio di nuovi provider di dati al modulo MRTK varia caso per caso e verrà comunicato al momento della proposta iniziale. Le proposte possono essere inviate creando un nuovo problema relativo al [ *tipo di richiesta* di funzionalità](https://github.com/microsoft/MixedRealityToolkit-Unity/issues).

### <a name="third-party-add-on"></a>Componente aggiuntivo di terze parti

**Namespace**

I provider di dati devono disporre di uno spazio dei nomi per attenuare potenziali conflitti di nomi. È consigliabile che lo spazio dei nomi includa i componenti seguenti.

- Nome dell'azienda che produce il componente aggiuntivo
- Area funzionale

Ad esempio, un provider di dati spatial awareness creato e spedito dalla società Contoso può essere *"Contoso.MixedReality.Toolkit. SpatialAwareness"*.

**Struttura di cartelle**

È consigliabile che il codice sorgente per i provider di dati sia disponibile in una gerarchia di cartelle, come illustrato nell'immagine seguente.

![Esempio di struttura di cartelle](../images/spatial-awareness/ExampleProviderFolderStructure.png)

Dove la *cartella ContosoSpatialAwareness* contiene l'implementazione del provider di dati, la cartella *Editor* contiene il controllo (e qualsiasi altro codice specifico dell'editor unity) e la cartella *Profiles* contiene uno o più oggetti pre-creati per lo script del profilo.

### <a name="mrtk-submission"></a>Invio di MRTK

**Namespace**

Se un provider di dati del sistema di riconoscimento spaziale viene inviato [al repository Toolkit realtà](https://github.com/Microsoft/MixedRealityToolkit-Unity)mista, lo spazio dei nomi deve iniziare con Microsoft.MixedReality.  Toolkit (ad esempio: *Microsoft.MixedReality.Toolkit. SpatialObjectMeshObserver*)

 e il codice deve trovarsi in una cartella sotto MRTK/Providers (ad esempio: *MRTK/Providers/ObjectMeshObserver*).

**Struttura di cartelle**

Tutto il codice deve trovarsi in una cartella sotto MRTK/Providers (ad esempio: MRTK/Providers/ObjectMeshObserver).

## <a name="define-the-spatial-data-object"></a>Definire l'oggetto dati spaziali

Il primo passaggio per la creazione di un provider di dati spatial awareness consiste nel determinare il tipo di dati (ad esempio mesh o piani) che fornirà alle applicazioni.

Tutti gli oggetti dati spaziali devono implementare [`IMixedRealitySpatialAwarenessObject`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObject) l'interfaccia .

La base Toolkit realtà mista fornisce gli oggetti spaziali seguenti che possono essere usati o estesi nei nuovi provider di dati.

- [`BaseSpatialAwarenessObject`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.BaseSpatialAwarenessObject)
- [`SpatialAwarenessMeshObject`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.SpatialAwarenessMeshObject)
- [`SpatialAwarenessPlanarObject`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.SpatialAwarenessPlanarObject)

## <a name="implement-the-data-provider"></a>Implementare il provider di dati

### <a name="specify-interface-andor-base-class-inheritance"></a>Specificare l'ereditarietà dell'interfaccia e/o della classe di base

Tutti i provider di dati di riconoscimento spaziale devono implementare l'interfaccia , che [`IMixedRealitySpatialAwarenessObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver) specifica la funzionalità minima richiesta dal sistema di consapevolezza spaziale. La base MRTK include la [`BaseSpatialObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.BaseSpatialObserver) classe che fornisce un'implementazione predefinita di questa funzionalità richiesta.

```c#
public class SpatialObjectMeshObserver :
    BaseSpatialObserver,
    IMixedRealitySpatialAwarenessMeshObserver,
    IMixedRealityCapabilityCheck
{ }
```

> [!NOTE]
> [`IMixedRealityCapabilityCheck`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityCapabilityCheck)L'interfaccia viene utilizzata dalla classe per indicare che fornisce il supporto per la funzionalità [`SpatialObjectMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserver) SpatialAwarenessMesh.

#### <a name="apply-the-mixedrealitydataprovider-attribute"></a>Applicare l'attributo MixedRealityDataProvider

Un passaggio chiave per la creazione di un provider di dati Spatial Awareness consiste nell'applicare [`MixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.MixedRealityDataProviderAttribute) l'attributo alla classe . Questo passaggio abilita l'impostazione del profilo e della piattaforma predefiniti per il provider di dati, se selezionato nel profilo Di consapevolezza spaziale, nonché in Nome, percorso cartella e altro ancora.

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

Dopo aver definito la classe, il passaggio successivo consiste nel fornire l'implementazione [`IMixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) dell'interfaccia .

> [!NOTE]
> La [`BaseSpatialObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.BaseSpatialObserver) classe , tramite la classe , fornisce solo [`BaseService`](xref:Microsoft.MixedReality.Toolkit.BaseService) un'implementazione vuota per [`IMixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) i metodi . I dettagli di questi metodi sono in genere specifici del provider di dati.

I metodi che devono essere implementati dal provider di dati sono:

- `Destroy()`
- `Disable()`
- `Enable()`
- `Initialize()`
- `Reset()`
- `Update()`

### <a name="implement-the-data-provider-logic"></a>Implementare la logica del provider di dati

Il passaggio successivo consiste nell'aggiungere la logica del provider di dati implementando l'interfaccia del provider di dati specifica, ad esempio [`IMixedRealitySpatialAwarenessMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessMeshObserver) . Questa parte del provider di dati sarà in genere specifica della piattaforma.

### <a name="observation-change-notifications"></a>Notifiche di modifica dell'osservazione

Per consentire alle applicazioni di rispondere alle modifiche nella comprensione dell'ambiente del dispositivo, il provider di dati genera eventi di notifica come definito [`IMixedRealitySpatialAwarenessObservationtHandler<T>`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObservationHandler`1) nell'interfaccia.

- `OnObservationAdded()`
- `OnObservationRemoved()`
- `OnObservationUpdated()`

 Il codice seguente degli esempi [`SpatialObjectMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserver) illustra la generazione e l'evento quando vengono aggiunti dati mesh.

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
> La [`SpatialObjectMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserver) classe non genera eventi perché il modello `OnObservationUpdated` 3D viene caricato una sola volta. L'implementazione [`WindowsMixedRealitySpatialMeshObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver) nella classe fornisce un esempio di generazione di un evento per una mesh `OnObservationUpdated` osservata.

### <a name="add-unity-profiler-instrumentation"></a>Aggiungere la strumentazione del profiler Unity

Le prestazioni sono fondamentali nelle applicazioni di realtà mista. Ogni componente aggiunge una certa quantità di overhead di cui le applicazioni devono essere conto. A questo scopo, è importante che tutti i provider di dati di riconoscimento spaziale contengano strumentazione del profiler Unity nel ciclo interno e percorsi di codice usati di frequente.

È consigliabile implementare il modello utilizzato da MRTK durante la strumentazione di provider personalizzati.

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
> Il nome usato per identificare il marcatore del profiler è arbitrario. MrTK usa il modello seguente.
>
> "[product] className.methodName - nota facoltativa"
>
> È consigliabile che i provider di dati personalizzati seguano un modello simile per semplificare l'identificazione di componenti e metodi specifici durante l'analisi delle tracce.

## <a name="create-the-profile-and-inspector"></a>Creare il profilo e il controllo

Nel modello di realtà mista Toolkit i provider di dati vengono configurati tramite [profili](../profiles/profiles.md).

### <a name="define-the-profile"></a>Definire il profilo

Il contenuto del profilo deve rispecchiare le proprietà accessibili del provider di dati (ad esempio, intervallo di aggiornamento). Tutte le proprietà configurabili dall'utente definite in ogni interfaccia devono essere contenute nel profilo.

Le classi di base sono incoraggiate se un nuovo provider di dati estende un provider esistente. Ad esempio, estende per consentire ai clienti di fornire [`SpatialObjectMeshObserverProfile`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserverProfile) [`MixedRealitySpatialAwarenessMeshObserverProfile`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.MixedRealitySpatialAwarenessMeshObserverProfile) un modello 3D da usare come dati dell'ambiente.

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

L'attributo può essere applicato alla classe del profilo per consentire ai clienti di creare un'istanza del profilo usando il `CreateAssetMenu` menu Create   >  **Assets**  >  **Mixed Reality Toolkit** Profiles (Crea asset di realtà mista Toolkit  >  **profili).**

### <a name="implement-the-inspector"></a>Implementare il controllo

I controlli profilo sono l'interfaccia utente per la configurazione e la visualizzazione del contenuto del profilo. Ogni controllo del profilo deve estendere la [`BaseMixedRealityToolkitConfigurationProfileInspector`](xref:Microsoft.MixedReality.Toolkit.Editor.BaseMixedRealityToolkitConfigurationProfileInspector) classe .

`CustomEditor`L'attributo indica a Unity il tipo di asset a cui si applica il controllo.

```c#
[CustomEditor(typeof(SpatialObjectMeshObserverProfile))]
public class SpatialObjectMeshObserverProfileInspector : BaseMixedRealityToolkitConfigurationProfileInspector
{ }
```

## <a name="create-assembly-definitions"></a>Creare definizioni di assembly

L'Toolkit di realtà mista usa i file di definizione dell'assembly ([asmdef](https://docs.unity3d.com/Manual/ScriptCompilationAssemblyDefinitionFiles.html)) per specificare le dipendenze tra i componenti e per aiutare Unity a ridurre il tempo di compilazione.

È consigliabile creare file di definizione dell'assembly per tutti i provider di dati e i relativi componenti dell'editor.

Usando la [struttura di](#namespace-and-folder-structure) cartelle nell'esempio precedente, saranno presenti due file asmdef per il provider di dati ContosoSpatialAwareness.

La prima definizione di assembly è per il provider di dati. Per questo esempio, sarà denominato ContosoSpatialAwareness e si trova nella cartella *ContosoSpatialAwareness* dell'esempio. Questa definizione di assembly deve specificare una dipendenza da Microsoft.MixedReality. Toolkit e qualsiasi altro assembly da cui dipende.

La definizione dell'assembly ContosoInputEditor specificherà il controllo del profilo e qualsiasi codice specifico dell'editor. Questo file deve trovarsi nella cartella radice del codice dell'editor. In questo esempio il file si trova nella *cartella ContosoSpatialAwareness\Editor.* Questa definizione di assembly conterrà un riferimento all'assembly ContosoSpatialAwareness, nonché:

- Microsoft.MixedReality. Toolkit
- Microsoft.MixedReality. Toolkit. Editor.Inspectors
- Microsoft.MixedReality. Toolkit. Editor.Utilities

## <a name="register-the-data-provider"></a>Registrare il provider di dati

Dopo la creazione, il provider di dati può essere registrato con il sistema di riconoscimento spaziale da usare nell'applicazione.

![Selezione dell'osservatore della mesh di oggetti spaziali](../images/spatial-awareness/SelectObjectObserver.png)

## <a name="packaging-and-distribution"></a>Creazione di pacchetti e distribuzione

I provider di dati distribuiti come componenti di terze parti hanno i dettagli specifici della creazione di pacchetti e della distribuzione lasciati alle preferenze dello sviluppatore. È probabile che la soluzione più comune sia generare un file unitypackage e distribuirsi tramite Unity Asset Store.

Se un provider di dati viene inviato e accettato come parte del pacchetto Microsoft Mixed Reality Toolkit, il team di Microsoft MRTK lo inserirà e lo distribuirà come parte delle offerte MRTK.

## <a name="see-also"></a>Vedi anche

- [Sistema di consapevolezza spaziale](spatial-awareness-getting-started.md)
- [`IMixedRealitySpatialAwarenessObject` Interfaccia](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObject)
- [Classe `BaseSpatialAwarenessObject`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.BaseSpatialAwarenessObject)
- [Classe `SpatialAwarenessMeshObject`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.SpatialAwarenessMeshObject)
- [Classe `SpatialAwarenessPlanarObject`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.SpatialAwarenessPlanarObject)
- [`IMixedRealitySpatialAwarenessObserver` Interfaccia](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver)
- [Classe `BaseSpatialObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.BaseSpatialObserver)
- [`IMixedRealitySpatialAwarenessMeshObserver` Interfaccia](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessMeshObserver)
- [`IMixedRealityDataProvider` Interfaccia](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider)
- [`IMixedRealityCapabilityCheck` Interfaccia](xref:Microsoft.MixedReality.Toolkit.IMixedRealityCapabilityCheck)

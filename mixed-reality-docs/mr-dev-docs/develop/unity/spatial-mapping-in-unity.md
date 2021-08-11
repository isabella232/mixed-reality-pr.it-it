---
title: Mapping spaziale in Unity
description: Informazioni su come usare e gestire il rendering e la collisione con la geometria reale intorno all'utente nelle app di realtà mista Unity.
author: davidkline-ms
ms.author: davidkl
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, mapping spaziale, renderer, collisore, mesh, scansione, componente, visore VR di realtà mista, visore VR windows di realtà mista, visore VR di realtà virtuale, MRTK, realtà mista Toolkit
ms.openlocfilehash: 4c8d0598898b4717a624562340918f968bd26f1fcde72258907e4fce73bd8489
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115223106"
---
# <a name="spatial-mapping-in-unity"></a>Mapping spaziale in Unity

[il mapping](../../design/spatial-mapping.md) spaziale consente di recuperare mesh triangolare che rappresentano le superfici nel mondo intorno a HoloLens dispositivo. È possibile usare i dati di superficie per il posizionamento, l'occlusione e l'analisi della stanza per offrire ai progetti Unity una dose aggiuntiva di affezione.

Unity include il supporto completo per il mapping spaziale, che viene esposto agli sviluppatori nei modi seguenti:

1. Componenti di mapping spaziale disponibili in MixedRealityToolkit, che forniscono un percorso pratico e rapido per iniziare a usare il mapping spaziale
2. API di mapping spaziale di livello inferiore, che forniscono il controllo completo e consentono una personalizzazione più sofisticata specifica dell'applicazione

Per usare il mapping spaziale nell'app, è necessario impostare la funzionalità spatialPerception in AppxManifest.

## <a name="device-support"></a>Supporto di dispositivi

| Funzionalità | [HoloLens (prima generazione)](/hololens/hololens1-hardware) | [HoloLens 2](/hololens/hololens2-hardware) | [Visori VR immersive](../../discover/immersive-headset-hardware-details.md) |
| ---- | ---- | ---- | ---- |
| Mapping spaziale | ✔️ | ✔️ | ❌ |

## <a name="setting-the-spatialperception-capability"></a>Impostazione della funzionalità SpatialPerception

Per consentire a un'app di usare i dati di mapping spaziale, è necessario che la funzionalità SpatialPerception sia abilitata.

Come abilitare la funzionalità SpatialPerception:

1. Nell'editor di Unity aprire il riquadro **"Player Impostazioni"** (Modifica > Project Impostazioni > Lettore)
2. Selezionare la **scheda "Windows Store"**
3. Espandere **"Publishing Impostazioni"** e controllare la funzionalità **"SpatialPerception"** nell'elenco **"Capabilities" (Funzionalità)**

> [!NOTE]
> Se il progetto Unity è già stato esportato in una soluzione Visual Studio, è necessario eseguire l'esportazione in una nuova cartella o impostare manualmente questa funzionalità [in AppxManifest in Visual Studio](../native/spatial-mapping-in-directx.md#set-up-your-app-to-use-the-spatialperception-capability).

Il mapping spaziale richiede anche un valore MaxVersionTested di almeno 10.0.10586.0:

1. In Visual Studio fare clic con il pulsante destro del mouse su **Package.appxmanifest** nella Esplora soluzioni **e scegliere Visualizza codice**
2. Trovare la riga che specifica **TargetDeviceFamily** e modificare **MaxVersionTested="10.0.10240.0"** in **MaxVersionTested="10.0.10586.0"**
3. **Salvare** Package.appxmanifest.

## <a name="getting-started-with-unitys-built-in-spatial-mapping-components"></a>Introduzione ai componenti di mapping spaziale predefiniti di Unity

Unity offre due componenti per aggiungere facilmente il mapping spaziale all'app: **Spatial Mapping Renderer (Renderer** di mapping spaziale) e Spatial Mapping **Collider (Collisore di mapping spaziale).**

### <a name="spatial-mapping-renderer"></a>Renderer di mapping spaziale

Il renderer di mapping spaziale consente di visualizzare la mesh di mapping spaziale.

![Renderer di mapping spaziale in Unity](images/spatialmappingrenderer.png)

### <a name="spatial-mapping-collider"></a>Collisore di mapping spaziale

Il collisore di mapping spaziale consente l'interazione di contenuto olografico (o carattere), ad esempio fisica, con la mesh di mapping spaziale.

![Spatial Mapping Collider in Unity](images/spatialmappingcollider.png)

### <a name="using-the-built-in-spatial-mapping-components"></a>Uso dei componenti di mapping spaziale predefiniti

È possibile aggiungere entrambi i componenti all'app se si desidera visualizzare e interagire con le superfici fisiche.

Per usare questi due componenti nell'app Unity:

1. Selezionare un GameObject al centro dell'area in cui si desidera rilevare le mesh della superficie spaziale.
2. Nella finestra Inspector (Controllo) **add Component**  >  **XR** Spatial Mapping Collider (Collisore mapping spaziale XR  >   componente) **o Spatial Mapping Renderer (Renderer mapping spaziale).**

Per altre informazioni su come usare questi componenti, vedere il sito della <a href="https://docs.unity3d.com/Manual/SpatialMappingComponents.html" target="_blank">documentazione di Unity.</a>

### <a name="going-beyond-the-built-in-spatial-mapping-components"></a>Oltre i componenti di mapping spaziale predefiniti

Questi componenti semplificano il trascinamento della selezione per iniziare a usare il mapping spaziale.  Per andare oltre, è possibile esplorare due percorsi principali:

* Per eseguire la propria elaborazione mesh di livello inferiore, vedere la sezione seguente sull'API dello script di mapping spaziale di basso livello.
* Per eseguire un'analisi mesh di livello superiore, vedere la sezione seguente sulla libreria SpatialUnderstanding in <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/SpatialUnderstanding" target="_blank">MixedRealityToolkit.</a>

## <a name="using-the-low-level-unity-spatial-mapping-api"></a>Uso dell'API di mapping spaziale di Unity di basso livello

Se è necessario un maggiore controllo rispetto ai componenti Spatial Mapping Renderer (Renderer mapping spaziale) e Spatial Mapping Collider (Collisore di mapping spaziale), usare le API di mapping spaziale di basso livello.

**Spazio dei nomi:** *UnityEngine.XR.WSA*<br>
**Tipi:** *SurfaceObserver*, *SurfaceChange*, *SurfaceData*, *SurfaceId*

Nelle sezioni seguenti è stato descritto il flusso suggerito per un'applicazione che usa le API di mapping spaziale.

### <a name="set-up-the-surfaceobservers"></a>Configurare SurfaceObserver

Creare un'istanza di un oggetto SurfaceObserver per ogni area di spazio definita dall'applicazione per cui sono necessari dati di mapping spaziale.

```cs
SurfaceObserver surfaceObserver;

private void Start()
{
    surfaceObserver = new SurfaceObserver();
}
```

Specificare l'area di spazio per cui ogni oggetto SurfaceObserver fornirà i dati chiamando SetVolumeAsSphere, SetVolumeAsAxisAlignedBox, SetVolumeAsOrientedBox o SetVolumeAsFrustum. È possibile ridefinire l'area di spazio in futuro semplicemente chiamando di nuovo uno di questi metodi.

```cs
private void Start()
{
    surfaceObserver.SetVolumeAsAxisAlignedBox(Vector3.zero, new Vector3(3, 3, 3));
}
```

Quando chiami SurfaceObserver.Update(), devi fornire un gestore per ogni superficie spaziale nell'area di spazio di SurfaceObserver per cui il sistema di mapping spaziale ha nuove informazioni. Il gestore riceve per una superficie spaziale:

```cs
private void OnSurfaceChanged(SurfaceId surfaceId, SurfaceChange changeType, Bounds bounds, System.DateTime updateTime)
{
    // see Handling Surface Changes
}
```

### <a name="handling-surface-changes"></a>Gestione delle modifiche della superficie

Esistono diversi casi principali da gestire, aggiunti e aggiornati, che possono usare lo stesso percorso di codice e rimossi.

* Nei casi aggiunti e aggiornati, aggiungiamo o ottieniamo il GameObject che rappresenta questa mesh dal dizionario, creiamo uno struct SurfaceData con i componenti necessari, quindi chiamiamo RequestMeshDataAsync per popolare il GameObject con i dati della mesh e la posizione nella scena.
* Nel caso rimosso, il GameObject che rappresenta questa mesh viene rimosso dal dizionario ed eliminato definitivamente.

```cs
System.Collections.Generic.Dictionary<SurfaceId, GameObject> spatialMeshObjects =
    new System.Collections.Generic.Dictionary<SurfaceId, GameObject>();

private void OnSurfaceChanged(SurfaceId surfaceId, SurfaceChange changeType, Bounds bounds, System.DateTime updateTime)
{
    switch (changeType)
    {
        case SurfaceChange.Added:
        case SurfaceChange.Updated:
            if (!spatialMeshObjects.ContainsKey(surfaceId))
            {
                spatialMeshObjects[surfaceId] = new GameObject("spatial-mapping-" + surfaceId);
                spatialMeshObjects[surfaceId].transform.parent = this.transform;
                spatialMeshObjects[surfaceId].AddComponent<MeshRenderer>();
            }
            GameObject target = spatialMeshObjects[surfaceId];
            SurfaceData sd = new SurfaceData(
                // the surface id returned from the system
                surfaceId,
                // the mesh filter that is populated with the spatial mapping data for this mesh
                target.GetComponent<MeshFilter>() ?? target.AddComponent<MeshFilter>(),
                // the world anchor used to position the spatial mapping mesh in the world
                target.GetComponent<WorldAnchor>() ?? target.AddComponent<WorldAnchor>(),
                // the mesh collider that is populated with collider data for this mesh, if true is passed to bakeMeshes below
                target.GetComponent<MeshCollider>() ?? target.AddComponent<MeshCollider>(),
                // triangles per cubic meter requested for this mesh
                1000,
                // bakeMeshes - if true, the mesh collider is populated, if false, the mesh collider is empty.
                true
            );

            SurfaceObserver.RequestMeshAsync(sd, OnDataReady);
            break;
        case SurfaceChange.Removed:
            var obj = spatialMeshObjects[surfaceId];
            spatialMeshObjects.Remove(surfaceId);
            if (obj != null)
            {
                GameObject.Destroy(obj);
            }
            break;
        default:
            break;
    }
}
```

### <a name="handling-data-ready"></a>Gestione dei dati pronti

Il gestore OnDataReady riceve un oggetto SurfaceData. Gli oggetti WorldAnchor, MeshFilter e (facoltativamente) MeshCollider che contiene riflettono lo stato più recente della superficie spaziale associata. Facoltativamente, analizzare e/o [elaborare](../../design/spatial-mapping.md#mesh-processing) i dati della mesh accedendo al membro Mesh dell'oggetto MeshFilter. Eseguire il rendering della superficie spaziale con la mesh più recente e (facoltativamente) usarla per collisioni fisiche e raycast. È importante verificare che il contenuto di SurfaceData non sia Null.

### <a name="start-processing-on-updates"></a>Avviare l'elaborazione degli aggiornamenti

SurfaceObserver.Update() deve essere chiamato in un ritardo, non in ogni fotogramma.

```cs
void Start ()
{
    StartCoroutine(UpdateLoop());
}

IEnumerator UpdateLoop()
{
    var wait = new WaitForSeconds(2.5f);
    while(true)
    {
        surfaceObserver.Update(OnSurfaceChanged);
        yield return wait;
    }
}
```

## <a name="higher-level-mesh-analysis-spatial-understanding"></a>Analisi mesh di livello superiore: Comprensione spaziale

> [!CAUTION]
> Spatial Understanding è stato deprecato a favore di [Scene Understanding.](../../design/scene-understanding.md)

<a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">MixedRealityToolkit è</a> una raccolta di codice di utilità per lo sviluppo olografico basato sulle API olografiche di Unity.

### <a name="spatial-understanding"></a>Informazioni spaziali

Quando si posizionano gli ologrammi nel mondo fisico, è spesso consigliabile andare oltre i piani di mesh e superficie del mapping spaziale. Quando il posizionamento viene eseguito in modo procedurale, è consigliabile un livello superiore di comprensione dell'ambiente. Ciò richiede in genere di prendere decisioni sul piano, sul controsoffitto e sulle pareti. È anche possibile ottimizzare in base a un set di vincoli di posizionamento per determinare le posizioni fisiche più ottimali per gli oggetti olografici.

Durante lo sviluppo di Young Conker e Fragments, Asobo Studio ha dovuto affrontare questo problema sviluppando un risolutore di stanza. Ognuno di questi giochi aveva esigenze specifiche del gioco, ma condivideva la tecnologia di comprensione spaziale di base. La libreria HoloToolkit.SpatialUnderstanding incapsula questa tecnologia, consentendo di trovare rapidamente spazi vuoti sulle pareti, posizionare gli oggetti sul controsoffitto, identificare i caratteri posizionati e una miriade di altre query di comprensione spaziale.

Tutto il codice sorgente è incluso, consentendo di personalizzarlo in base alle proprie esigenze e condividere i miglioramenti con la community. Il codice per il risolutore C++ è stato incapsulato in una DLL UWP ed esposto a Unity con un calo nel prefab contenuto in MixedRealityToolkit.

### <a name="understanding-modules"></a>Informazioni sui moduli

Il modulo ha tre interfacce principali esposte: topologia per query semplici su superficie e spaziali, forma per il rilevamento degli oggetti e risolutore di posizionamento degli oggetti per il posizionamento basato su vincoli dei set di oggetti. Ogni modalità è illustrata di seguito. Oltre alle tre interfacce principali del modulo, è possibile usare un'interfaccia di ray casting per recuperare i tipi di superficie con tag e copiare una mesh di spazi di gioco personalizzata.

### <a name="ray-casting"></a>Ray Casting

Al termine dell'analisi della stanza, le etichette vengono generate internamente per superfici come il piano, il controsoffitto e le pareti. La funzione accetta un raggio e restituisce se il raggio entra in conflitto con una superficie nota e, in tal caso, le informazioni su tale superficie `PlayspaceRaycast` sotto forma di `RaycastResult` .

```cpp
struct RaycastResult
{
    enum SurfaceTypes
    {
        Invalid,    // No intersection
        Other,
        Floor,
        FloorLike,  // Not part of the floor topology,
                    //  but close to the floor and looks like the floor
        Platform,   // Horizontal platform between the ground and
                    //  the ceiling
        Ceiling,
        WallExternal,
        WallLike,   // Not part of the external wall surface,
                    //  but vertical surface that looks like a
                    //  wall structure
    };
    SurfaceTypes SurfaceType;
    float SurfaceArea;  // Zero if unknown
                        //  (i.e. if not part of the topology analysis)
    DirectX::XMFLOAT3 IntersectPoint;
    DirectX::XMFLOAT3 IntersectNormal;
};
```

Internamente, il raycast viene calcolato in base alla rappresentazione del voxel cubo da 8 cm calcolata dello spazio di riproduzione. Ogni voxel contiene un set di elementi di superficie con dati di topologia elaborati (d.a. surfel). Vengono confrontate le superfici contenute all'interno della cella voxel intersecata e viene usata la corrispondenza migliore per cercare le informazioni sulla topologia. Questi dati della topologia contengono l'etichettatura restituita sotto forma di enumerazione "SurfaceTypes", nonché la superficie di attacco della superficie intersecata.

Nell'esempio unity il cursore esegue il cast di un raggio per ogni frame. In primo luogo, contro i collisori di Unity. In secondo piano, rispetto alla rappresentazione del mondo del modulo di comprensione. Infine, anche in questo caso, gli elementi dell'interfaccia utente. In questa applicazione, l'interfaccia utente ottiene la priorità, dopo il risultato di comprensione e infine i collisori di Unity. SurfaceType viene segnalato come testo accanto al cursore.

![Il tipo di superficie viene etichettato accanto al cursore](images/su-raycastresults-300px.jpg)<br>
*Il tipo di superficie viene etichettato accanto al cursore*

### <a name="topology-queries"></a>Query sulla topologia

All'interno della DLL, gestione topologia gestisce l'etichettatura dell'ambiente. Come accennato in precedenza, gran parte dei dati viene archiviata all'interno di un volume voxel. Inoltre, la struttura "PlaySpaceInfos" viene usata per archiviare informazioni sullo spazio di gioco, tra cui l'allineamento del mondo (altri dettagli su questo di seguito), il pavimento e l'altezza del controsoffitto. L'euristica viene usata per determinare il pavimento, il controsoffitto e le pareti. Ad esempio, la superficie orizzontale più grande e più bassa con una superficie superiore a 1 m2 viene considerata il piano.

> [!NOTE]
> In questo processo viene usato anche il percorso della fotocamera durante il processo di analisi.

Un subset delle query esposte da Gestione topologia viene esposto tramite la DLL. Le query sulla topologia esposte sono le seguenti.

```cpp
QueryTopology_FindPositionsOnWalls
QueryTopology_FindLargePositionsOnWalls
QueryTopology_FindLargestWall
QueryTopology_FindPositionsOnFloor
QueryTopology_FindLargestPositionsOnFloor
QueryTopology_FindPositionsSittable
```

Ognuna delle query ha un set di parametri, specifico per il tipo di query. Nell'esempio seguente l'utente specifica l'altezza minima & larghezza del volume desiderato, l'altezza minima di posizionamento sopra il pavimento e la quantità minima di spazio davanti al volume. Tutte le misurazioni sono in metri.

```cpp
EXTERN_C __declspec(dllexport) int QueryTopology_FindPositionsOnWalls(
    _In_ float minHeightOfWallSpace,
    _In_ float minWidthOfWallSpace,
    _In_ float minHeightAboveFloor,
    _In_ float minFacingClearance,
    _In_ int locationCount,
    _Inout_ Dll_Interface::TopologyResult* locationData)
```

Ognuna di queste query accetta una matrice preallocato di strutture "TopologyResult". Il parametro "locationCount" specifica la lunghezza dell'oggetto passato nella matrice. Il valore restituito indica il numero di posizioni restituite. Questo numero non è mai maggiore del parametro "locationCount" passato.

"TopologyResult" contiene la posizione centrale del volume restituito, la direzione rivolta (ad esempio normale) e le dimensioni dello spazio trovato.

```cpp
struct TopologyResult
{
    DirectX::XMFLOAT3 position;
    DirectX::XMFLOAT3 normal;
    float width;
    float length;
};
```

> [!NOTE]
> Nell'esempio Unity ognuna di queste query è collegata a un pulsante nel pannello dell'interfaccia utente virtuale. L'esempio imposta come hard codes i parametri per ognuna di queste query in base a valori ragionevoli. Per altri esempi, vedere SpaceVisualizer.cs nel codice di esempio.

### <a name="shape-queries"></a>Query di forma

Nella dll, l'analizzatore di forme ("ShapeAnalyzer_W") usa l'analizzatore della topologia per la corrispondenza con le forme personalizzate definite dall'utente. L'esempio Unity definisce un set di forme ed espone i risultati tramite il menu di query in-app, all'interno della scheda della forma. L'intenzione è che l'utente possa definire le proprie query sulla forma degli oggetti e usarle in base alle esigenze dell'applicazione.

L'analisi della forma funziona solo su superfici orizzontali. Un divano, ad esempio, è definito dalla superficie della sella piana e dalla parte superiore piana del divano posteriore. La query di forma cerca due superfici di dimensioni, altezza e intervallo di aspetti specifici, con le due superfici allineate e connesse. Usando la terminologia delle API, il divano e la parte superiore posteriore sono componenti di forma e i requisiti di allineamento sono vincoli dei componenti di forma.

Di seguito è illustrata una query di esempio definita nell'esempio Unity (ShapeDefinition.cs) per gli oggetti "sittable".

```cs
shapeComponents = new List<ShapeComponent>()
{
    new ShapeComponent(
        new List<ShapeComponentConstraint>()
        {
            ShapeComponentConstraint.Create_SurfaceHeight_Between(0.2f, 0.6f),
            ShapeComponentConstraint.Create_SurfaceCount_Min(1),
            ShapeComponentConstraint.Create_SurfaceArea_Min(0.035f),
        }
    ),
};
AddShape("Sittable", shapeComponents);
```

Ogni query di forma è definita da un set di componenti della forma, ognuno con un set di vincoli di componente e un set di vincoli di forma che elencano le dipendenze tra i componenti. Questo esempio include tre vincoli in una singola definizione di componente e nessun vincolo di forma tra i componenti (poiché è presente un solo componente).

Al contrario, la forma del divano ha due componenti di forma e quattro vincoli di forma. I componenti sono identificati dal relativo indice nell'elenco dei componenti dell'utente (0 e 1 in questo esempio).

```cs
shapeConstraints = new List<ShapeConstraint>()
{
    ShapeConstraint.Create_RectanglesSameLength(0, 1, 0.6f),
    ShapeConstraint.Create_RectanglesParallel(0, 1),
    ShapeConstraint.Create_RectanglesAligned(0, 1, 0.3f),
    ShapeConstraint.Create_AtBackOf(1, 0),
};
```

Le funzioni wrapper vengono fornite nel modulo Unity per creare facilmente definizioni di forme personalizzate. L'elenco completo dei vincoli di componente e forma è disponibile in "SpatialUnderstandingDll.cs" all'interno delle strutture "ShapeComponentConstraint" e "ShapeConstraint".

![La forma del rettangolo si trova su questa superficie](images/su-shapequery-300px.jpg)<br>
*La forma del rettangolo si trova su questa superficie*

### <a name="object-placement-solver"></a>Risolutore di posizionamento oggetti

Il risolutore di posizionamento degli oggetti può essere usato per identificare le posizioni ideali nella stanza fisica in cui posizionare gli oggetti. Il risolutore troverà la posizione più adatta in base alle regole e ai vincoli dell'oggetto. Inoltre, le query sull'oggetto vengono mantenute fino a quando l'oggetto non viene rimosso con chiamate "Solver_RemoveObject" o "Solver_RemoveAllObjects", consentendo il posizionamento vincolato di più oggetti. Le query di posizionamento degli oggetti sono costituite da tre parti: tipo di posizionamento con parametri, un elenco di regole e un elenco di vincoli. Per eseguire una query, usare l'API seguente.

```cpp
public static int Solver_PlaceObject(
            [In] string objectName,
            [In] IntPtr placementDefinition,        // ObjectPlacementDefinition
            [In] int placementRuleCount,
            [In] IntPtr placementRules,             // ObjectPlacementRule
            [In] int constraintCount,
            [In] IntPtr placementConstraints,       // ObjectPlacementConstraint
            [Out] IntPtr placementResult)
```

Questa funzione accetta un nome di oggetto, una definizione di posizionamento e un elenco di regole e vincoli. I wrapper C# forniscono funzioni helper di costruzione per semplificare la costruzione di regole e vincoli. La definizione di posizionamento contiene il tipo di query, ad esempio uno dei seguenti.

```cpp
public enum PlacementType
{
    Place_OnFloor,
    Place_OnWall,
    Place_OnCeiling,
    Place_OnShape,
    Place_OnEdge,
    Place_OnFloorAndCeiling,
    Place_RandomInAir,
    Place_InMidAir,
    Place_UnderFurnitureEdge,
};
```

Ogni tipo di posizionamento ha un set di parametri univoci per il tipo. La struttura "ObjectPlacementDefinition" contiene un set di funzioni helper statiche per la creazione di queste definizioni. Ad esempio, per trovare una posizione in cui posizionare un oggetto sul pavimento, è possibile usare la funzione seguente. public static ObjectPlacementDefinition Create_OnFloor(Vector3 halfDims) Oltre al tipo di posizionamento, è possibile fornire un set di regole e vincoli. Le regole non possono essere violate. Le possibili posizioni di posizionamento che soddisfano il tipo e le regole vengono quindi ottimizzate in base al set di vincoli per selezionare la posizione ottimale. Ognuna delle regole e dei vincoli può essere creata dalle funzioni di creazione statiche fornite. Di seguito è riportata una funzione di costruzione di regole e vincoli di esempio.

```cs
public static ObjectPlacementRule Create_AwayFromPosition(
    Vector3 position, float minDistance)
public static ObjectPlacementConstraint Create_NearPoint(
    Vector3 position, float minDistance = 0.0f, float maxDistance = 0.0f)
```

La query di posizionamento degli oggetti seguente cerca un luogo in cui posizionare un cubo di mezzo metro sul bordo di una superficie, lontano da altri oggetti posizionati in precedenza e vicino al centro della stanza.

```cs
List<ObjectPlacementRule> rules =
    new List<ObjectPlacementRule>() {
        ObjectPlacementRule.Create_AwayFromOtherObjects(1.0f),
    };

List<ObjectPlacementConstraint> constraints =
    new List<ObjectPlacementConstraint> {
        ObjectPlacementConstraint.Create_NearCenter(),
    };

Solver_PlaceObject(
    “MyCustomObject”,
    new ObjectPlacementDefinition.Create_OnEdge(
        new Vector3(0.25f, 0.25f, 0.25f),
        new Vector3(0.25f, 0.25f, 0.25f)),
    rules.Count,
    UnderstandingDLL.PinObject(rules.ToArray()),
    constraints.Count,
    UnderstandingDLL.PinObject(constraints.ToArray()),
    UnderstandingDLL.GetStaticObjectPlacementResultPtr());
```

In caso di esito positivo, viene restituita una struttura "ObjectPlacementResult" contenente la posizione di posizionamento, le dimensioni e l'orientamento. Inoltre, la posizione viene aggiunta all'elenco interno della DLL di oggetti inseriti. Le query di posizionamento successive prenderanno in considerazione questo oggetto. Il file "LevelSolver.cs" nell'esempio Unity contiene altre query di esempio.

![Risultati del posizionamento degli oggetti](images/su-objectplacement-1000px.jpg)<br>
*Figura 3: Le caselle blu illustrano come viene restituito il risultato da tre query sul piano con le regole di posizione della fotocamera*

Quando si risolve la posizione di posizionamento di più oggetti necessari per uno scenario di livello o applicazione, risolvere prima di tutto oggetti indispensabili e di grandi dimensioni per ottimizzare la probabilità che sia possibile trovare uno spazio. L'ordine di posizionamento è importante. Se non è possibile trovare i posizionamenti degli oggetti, provare a eseguire configurazioni meno vincolate. La presenza di un set di configurazioni di fallback è fondamentale per supportare le funzionalità in molte configurazioni di stanza.

### <a name="room-scanning-process"></a>Processo di analisi della stanza

Anche se la soluzione di mapping spaziale fornita dal HoloLens è progettata per essere sufficientemente generica da soddisfare le esigenze dell'intera gamma di spazi problematici, il modulo di comprensione spaziale è stato creato per supportare le esigenze di due giochi specifici. La soluzione è strutturata in base a un processo specifico e a un set di presupposti, riepilogati di seguito.

```txt
Fixed size playspace – The user specifies the maximum playspace size in the init call.

One-time scan process –
    The process requires a discrete scanning phase where the user walks around,
    defining the playspace.
    Query functions will not function until after the scan has been finalized.
```

"painting" dello spazio di gioco guidato dall'utente: durante la fase di scansione, l'utente si sposta e guarda intorno al ritmo di riproduzione, disegnando in modo efficace le aree, che devono essere incluse. La mesh generata è importante per fornire commenti e suggerimenti durante questa fase. Configurazione di interni per la casa o l'ufficio: le funzioni di query sono progettate intorno a superfici piatte e pareti ad angolo retto. Si tratta di una limitazione soft. Durante la fase di analisi, tuttavia, viene completata un'analisi dell'asse primario per ottimizzare la trama della mesh lungo l'asse principale e secondario. Il file SpatialUnderstanding.cs incluso gestisce il processo della fase di analisi. Chiama le funzioni seguenti.

```txt
SpatialUnderstanding_Init – Called once at the start.

GeneratePlayspace_InitScan – Indicates that the scan phase should begin.

GeneratePlayspace_UpdateScan_DynamicScan –
    Called each frame to update the scanning process. The camera position and
    orientation is passed in and is used for the playspace painting process,
    described above.

GeneratePlayspace_RequestFinish –
    Called to finalize the playspace. This will use the areas “painted” during
    the scan phase to define and lock the playspace. The application can query
    statistics during the scanning phase as well as query the custom mesh for
    providing user feedback.

Import_UnderstandingMesh –
    During scanning, the “SpatialUnderstandingCustomMesh” behavior provided by
    the module and placed on the understanding prefab will periodically query the
    custom mesh generated by the process. In addition, this is done once more
    after scanning has been finalized.
```

Il flusso di analisi, guidato dal comportamento "SpatialUnderstanding" chiama InitScan, quindi UpdateScan per ogni frame. Quando la query sulle statistiche segnala una copertura ragionevole, l'utente può chiamare RequestFinish per indicare la fine della fase di analisi. UpdateScan continua a essere chiamato finché il valore restituito non indica che l'elaborazione della DLL è stata completata.

### <a name="understanding-mesh"></a>Informazioni sulla mesh

La dll di comprensione archivia internamente lo spazio di riproduzione come griglia di cubi voxel di dimensioni di 8 cm. Durante la parte iniziale dell'analisi, viene completata un'analisi dei componenti primaria per determinare gli assi della stanza. Internamente, archivia lo spazio voxel allineato a questi assi. Una mesh viene generata circa ogni secondo estraendo l'isosurface dal volume voxel.

![Mesh generata dal volume voxel](images/su-custommesh.jpg)<br>
*Mesh generata dal volume voxel*

## <a name="troubleshooting"></a>Risoluzione dei problemi

* Assicurarsi di aver impostato la [funzionalità SpatialPerception](#setting-the-spatialperception-capability)
* Quando il rilevamento viene perso, l'evento OnSurfaceChanged successivo rimuoverà tutte le mesh.

## <a name="spatial-mapping-in-mixed-reality-toolkit"></a>Mapping spaziale in realtà mista Toolkit

Per altre informazioni sull'uso di Mapping spaziale Toolkit realtà mista, vedere la sezione [sulla](/windows/mixed-reality/mrtk-unity/features/spatial-awareness/spatial-awareness-getting-started) consapevolezza spaziale della documentazione di MRTK.

## <a name="next-development-checkpoint"></a>Successivo checkpoint di sviluppo

Se si sta seguendo il percorso di sviluppo di Unity che è stato previsto, si stanno esplorando i blocchi predefiniti principali di MRTK. Da qui è possibile passare al blocco predefinito successivo:

> [!div class="nextstepaction"]
> [Text](text-in-unity.md)

In alternativa, passare alle API e funzionalità della piattaforma di realtà mista:

> [!div class="nextstepaction"]
> [Esperienze condivise](shared-experiences-in-unity.md)

È sempre possibile tornare ai [checkpoint per lo sviluppo con Unity](unity-development-overview.md#2-core-building-blocks) in qualsiasi momento.

## <a name="see-also"></a>Vedere anche

* [Sistemi di coordinate](../../design/coordinate-systems.md)
* [Sistemi di coordinate in Unity](coordinate-systems-in-unity.md)
* <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">MixedRealityToolkit</a>
* <a href="https://docs.unity3d.com/ScriptReference/MeshFilter.html" target="_blank">UnityEngine.MeshFilter</a>
* <a href="https://docs.unity3d.com/ScriptReference/MeshCollider.html" target="_blank">UnityEngine.MeshCollider</a>
* <a href="https://docs.unity3d.com/ScriptReference/Bounds.html" target="_blank">UnityEngine.Bounds</a>

---
title: SDK di comprensione della scena
description: Informazioni su come installare e usare Scene Understanding SDK, inclusi componenti, mesh e oggetti nelle app di realtà mista.
author: szymons
ms.author: szymons
ms.date: 12/14/2020
ms.topic: article
keywords: Comprensione della scena, mapping spaziale, Windows Mixed Reality, Unity
ms.openlocfilehash: d7547e1517583e3822a9ac9b54cbf0557cd7780c
ms.sourcegitcommit: 6f3b3aa31cc3acefba5fa3ac3ba579d9868a4fe4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/31/2021
ms.locfileid: "123246297"
---
# <a name="scene-understanding-sdk-overview"></a>Panoramica dell'SDK per la comprensione della scena

La comprensione della scena trasforma i dati del sensore dell'ambiente non strutturato che il dispositivo di realtà mista acquisisce e converte in una potente rappresentazione astratta. L'SDK funge da livello di comunicazione tra l'applicazione e il runtime scene understanding. Ha lo scopo di simulare costrutti standard esistenti, ad esempio grafici di scena 3D per rappresentazioni 3D, rettangoli e pannelli 2D per applicazioni 2D. Anche se i costrutti scene understanding verranno mappati a framework concreti, in generale SceneUnderstanding è indipendente dal framework che consente l'interoperabilità tra diversi framework che interagiscono con esso. Con l'evolversi della comprensione della scena, il ruolo dell'SDK è garantire che le nuove rappresentazioni e funzionalità continuino a essere esposte all'interno di un framework unificato. In questo documento verranno presentati innanzitutto concetti di alto livello che consentono di acquisire familiarità con l'ambiente di sviluppo/utilizzo e quindi fornire una documentazione più dettagliata per classi e costrutti specifici.

## <a name="where-do-i-get-the-sdk"></a>Dove si ottiene l'SDK?

SceneUnderstanding SDK è scaricabile tramite lo strumento [di funzionalità di realtà mista](../unity/welcome-to-mr-feature-tool.md).
<!--Unity Note-->
**Nota:** la versione più recente dipende dai pacchetti di anteprima ed è necessario abilitare i pacchetti non definitiva per visualizzarlo.

Per la versione 0.5.2022-rc e successive, Scene Understanding supporta le proiezioni del linguaggio per C# e C++ consentendo alle applicazioni di sviluppare applicazioni per piattaforme Win32 o UWP. A causa di questa versione, SceneUnderstanding supporta il supporto di unity nell'editor, che consente di usare SceneObserver solo per la comunicazione con HoloLens2. 
<!-- Unity Note: Since C++ is mentioned, it's not strictly Unity. Not sure about the C#. -->
SceneUnderstanding richiede Windows SDK versione 18362 o successiva. 

## <a name="conceptual-overview"></a>Panoramica dei concetti

### <a name="the-scene"></a>Scena

Il dispositivo di realtà mista integra costantemente le informazioni relative a ciò che vede nell'ambiente. Scene Understanding incanala tutte queste origini dati e produce un'unica astrazione coesiva. La comprensione della scena genera scene, che sono una composizione di [SceneObject che](scene-understanding-SDK.md#sceneobjects) rappresentano un'istanza di una singola cosa, ad esempio una parete,un controsoffitto/un piano. Gli oggetti scena stessi sono una composizione di [SceneComponents, che rappresentano parti più granulari che costituiscono questo SceneObject. Esempi di componenti sono quad e mesh, ma in futuro potrebbero rappresentare recinti di delimitazione, mesh di collisione, metadati e così via.

Il processo di conversione dei dati del sensore non elaborato in una scena è un'operazione potenzialmente costosa che potrebbe richiedere secondi per spazi medi (~10x10m) in minuti per spazi di grandi dimensioni (~50x50m) e quindi non è un'operazione calcolata dal dispositivo senza richiesta dell'applicazione. La generazione della scena viene invece attivata dall'applicazione su richiesta. La classe SceneObserver include metodi statici che consentono di calcolare o deserializzare una scena, che è quindi possibile enumerare o interagire. L'azione "Calcolo" viene eseguita su richiesta ed eseguita sulla CPU, ma in un processo separato (Mixed Reality Driver). Tuttavia, mentre si esegue il calcolo in un altro processo, i dati della scena risultanti vengono archiviati e gestiti nell'applicazione nell'oggetto Scene. 

Di seguito è riportato un diagramma che illustra questo flusso di processo e mostra esempi di due applicazioni che si interfacciano con il runtime scene understanding. 

![Diagramma di processo](images/SU-ProcessFlow.png)

Sul lato sinistro è presente un diagramma del runtime di realtà mista, che è sempre in esecuzione nel proprio processo. Questo runtime è responsabile dell'esecuzione del rilevamento dei dispositivi, del mapping spaziale e di altre operazioni utilizzate da Scene Understanding per comprendere e ragionare sul mondo che ti circonda. Sul lato destro del diagramma vengono mostrate due applicazioni teoriche che usano La comprensione della scena. Le prime interfacce dell'applicazione con MRTK<!--Unity Note-->, che usa Scene Understanding SDK internamente, la seconda app calcola e usa due istanze di scena separate. Tutte e tre le scene in questo diagramma generano istanze distinte delle scene, il driver non sta tracciando lo stato globale condiviso tra le applicazioni e gli oggetti scena in una scena non vengono trovati in un'altra. La comprensione della scena fornisce un meccanismo per tenere traccia nel tempo, ma questa operazione viene eseguita usando l'SDK. Il codice di rilevamento è già in esecuzione nell'SDK nel processo dell'app.

Poiché ogni scena archivia i dati nello spazio di memoria dell'applicazione, è possibile presupporre che tutte le funzioni dell'oggetto Scene o i relativi dati interni siano sempre eseguiti nel processo dell'applicazione.

### <a name="layout"></a>Layout

Per usare Scene Understanding, può essere utile conoscere e comprendere in che modo il runtime rappresenta i componenti in modo logico e fisico. La scena rappresenta i dati con un layout specifico che è stato scelto come semplice mantenendo una struttura sottostante che è soggetta a soddisfare i requisiti futuri senza la necessità di revisioni importanti. La scena esegue questa operazione archiviando tutti i componenti (blocchi predefiniti per tutti gli oggetti scena) in un elenco semplice e definendo gerarchia e composizione tramite riferimenti in cui componenti specifici fanno riferimento ad altri.

Di seguito viene presentato un esempio di struttura sia nella forma flat che nella forma logica.

<table>
<tr><th>Layout logico</th><th>Layout fisico</th></tr>
<tr>
<td>
<ul>
  Scene
  <ul>
  <li>SceneObject_1
    <ul>
      <li>SceneMesh_1</li>
      <li>SceneQuad_1</li>
      <li>SceneQuad_2</li>
    </ul>
  </li>
  <li>SceneObject_2
    <ul>
      <li>SceneQuad_1</li>
      <li>SceneQuad_3</li>
      </li></ul>
  </li>
  <li>SceneObject_3
    <ul>
      <li>SceneMesh_3</li>
    </ul>
  </ul>
</ul>
</td>
<td>
<ul>
  <li>SceneObject_1</li>
  <li>SceneObject_2</li>
  <li>SceneObject_3</li>
  <li>SceneQuad_1</li>
  <li>SceneQuad_2</li>
  <li>SceneQuad_3</li>
  <li>SceneMesh_1</li>
  <li>SceneMesh_2</li>
</ul>
</td>
</tr>
</table>

Questa figura evidenzia la differenza tra il layout fisico e logico della scena. A sinistra è visualizzato il layout gerarchico dei dati visualizzati dall'applicazione durante l'enumerazione della scena. A destra si può vedere che la scena è costituita da 12 componenti distinti accessibili singolarmente, se necessario. Quando si elabora una nuova scena, si prevede che le applicazioni passino logicamente a questa gerarchia, tuttavia quando si esegue il rilevamento tra gli aggiornamenti della scena, alcune applicazioni potrebbero essere interessate solo a componenti specifici condivisi tra due scene.

## <a name="api-overview"></a>Panoramica delle API

La sezione seguente offre una panoramica generale dei costrutti in Informazioni sulla scena. La lettura di questa sezione consente di comprendere come vengono rappresentate le scene e cosa fanno o vengono usati i vari componenti. La sezione successiva fornirà esempi di codice concreti e dettagli aggiuntivi che verranno illustrati in questa panoramica.

Tutti i tipi descritti di seguito si trovano nello spazio dei `Microsoft.MixedReality.SceneUnderstanding` nomi .

### <a name="scenecomponents"></a>SceneComponents

Ora che si comprende il layout logico delle scene, è possibile presentare il concetto di SceneComponents e il modo in cui vengono usati per comporre la gerarchia. SceneComponents è la scomposizione più granulare in SceneUnderstanding che rappresenta un singolo elemento principale, ad esempio una mesh, un quad o un rettangolo di selezione. SceneComponents sono elementi che possono essere aggiornati in modo indipendente e possono essere referenziati da altri SceneComponent, quindi hanno una singola proprietà globale, un ID univoco, che consentono questo tipo di meccanismo di rilevamento/riferimento. Gli ID vengono usati per la composizione logica della gerarchia della scena e per la persistenza degli oggetti (l'atto di aggiornare una scena rispetto a un'altra).

Se si considera ogni scena appena calcolata come distinta e si semplicemente enumerano tutti i dati al suo interno, gli ID sono per lo più trasparenti per l'utente. Tuttavia, se si prevede di tenere traccia dei componenti su più aggiornamenti, si useranno gli ID per indicizzare e trovare SceneComponents tra gli oggetti Scene.

### <a name="sceneobjects"></a>SceneObjects

SceneObject è un oggetto SceneComponent che rappresenta un'istanza di una "cosa", ad esempio una parete, un pavimento, un controsoffitto e così via. espresso dalla proprietà Kind. Gli oggetti SceneObject sono geometrici e hanno quindi funzioni e proprietà che rappresentano la loro posizione nello spazio, ma non contengono alcuna struttura geometrica o logica. SceneObjects fa invece riferimento ad altri SceneComponent, in particolare SceneQuads e SceneMeshes, che forniscono le varie rappresentazioni supportate dal sistema. Quando viene calcolata una nuova scena, è molto probabile che l'applicazione enumererà gli oggetti SceneObject della scena per elaborare ciò a cui è interessata.

SceneObjects può avere uno degli elementi seguenti:

<table>
<tr>
<th>SceneObjectKind</th> <th>Descrizione</th>
</tr>
<tr><td>Sfondo</td><td>SceneObject è noto per non <b>essere uno</b> degli altri tipi riconosciuti di oggetto scena. Questa classe non deve essere confusa con Unknown, dove Background non è noto per essere wall/floor/ceiling e così via... mentre sconosciuto non è ancora categorizzato.</b></td></tr>
<tr><td>Parete</td><td>Una parete fisica. Si presuppone che le pareti siano strutture ambientali inamovibili.</td></tr>
<tr><td>Piano</td><td>I piani sono superfici su cui si può andare a piedi. Nota: le scale non sono piani. Si noti anche che i piani presuppongono qualsiasi superficie a piedi e pertanto non esiste alcun presupposto esplicito di un piano singolare. Strutture a più livelli, rampe e così via... deve essere classificata come floor.</td></tr>
<tr><td>Ceiling</td><td>La superficie superiore di una stanza.</td></tr>
<tr><td>Piattaforma</td><td>Una superficie piana di grandi dimensioni su cui è possibile posizionare gli ologrammi. In genere rappresentano tabelle, controsoffi e altre superfici orizzontali di grandi dimensioni.</td></tr>
<tr><td>World</td><td>Etichetta riservata per i dati geometrici indipendente dall'etichettatura. La mesh generata impostando il flag di aggiornamento EnableWorldMesh verrà classificata come world.</td></tr>
<tr><td>Sconosciuto</td><td>Questo oggetto scena deve ancora essere classificato e assegnato a un tipo. Questo non deve essere confuso con Background, poiché questo oggetto potrebbe essere qualsiasi cosa, il sistema non ha ancora creato una classificazione sufficientemente solida per questo oggetto.</td></tr>
</tr>
</table>

### <a name="scenemesh"></a>SceneMesh

SceneMesh è un oggetto SceneComponent che approssima la geometria di oggetti geometrici arbitrari usando un elenco di triangoli. SceneMeshes viene usato in diversi contesti; possono rappresentare i componenti della struttura delle celle stagnate o come WorldMesh, che rappresenta la mesh di mapping spaziale non associata associata alla scena. I dati di indice e vertice forniti con ogni mesh utilizzano lo stesso layout familiare dei [buffer](/windows/win32/direct3d9/rendering-from-vertex-and-index-buffers) dei vertici e degli indici usati per il rendering delle mesh triangolare in tutte le API di rendering moderne. In Scene Understanding le mesh usano indici a 32 bit e potrebbero dover essere suddivise in blocchi per determinati motori di rendering.

#### <a name="winding-order-and-coordinate-systems"></a>Ordine di avvolgimento e sistemi di coordinate

Si prevede che tutte le mesh prodotte da Scene Understanding restituiranno mesh in un sistema Right-Handed coordinate usando l'ordine di avvolgimento in senso orario. 

Nota: le compilazioni del sistema operativo precedenti 191105 potrebbero avere un bug noto in cui le mesh "World" venivano restituite Counter-Clockwise un ordine di vento, che è stato successivamente risolto.

### <a name="scenequad"></a>SceneQuad

SceneQuad è un oggetto SceneComponent che rappresenta superfici 2D che occupano il mondo 3D. SceneQuads può essere usato in modo analogo a ARKit ARPlaneAnchor o ARCore Planes, ma offrono funzionalità più di alto livello come canvas 2D che possono essere usate da app flat o dall'esperienza utente aumentata. Sono disponibili API specifiche 2D per quad che rendono il posizionamento e il layout semplici da usare e lo sviluppo (ad eccezione del rendering) con quad dovrebbe essere più simile all'uso di canvas 2D rispetto alle mesh 3D.

#### <a name="scenequad-shape"></a>Forma SceneQuad

SceneQuads definisce una superficie rettangolare delimitata in 2d. SceneQuads rappresenta tuttavia superfici con forme arbitrarie e potenzialmente complesse, ad esempio una tabella a forma di ciambella. Per rappresentare la forma complessa della superficie di un quad, è possibile usare l'API GetSurfaceMask per eseguire il rendering della forma della superficie in un buffer di immagini specificato. Se anche l'oggetto SceneObject con il quad ha una mesh, i triangoli della mesh devono essere equivalenti a questa immagine sottoposta a rendering, entrambi rappresentano la geometria reale della superficie, in coordinate 2D o 3D.

## <a name="scene-understanding-sdk-details-and-reference"></a>Informazioni di riferimento e dettagli sull'SDK per la scena

> [!NOTE] 
> <!--Unity Note-->Quando si usa MRTK, si noti che l'utente interagirà con mrTK e pertanto potrebbe ignorare questa sezione nella maggior [`WindowsSceneUnderstandingObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsSceneUnderstanding.Experimental.WindowsSceneUnderstandingObserver) parte dei casi. Per altre informazioni, vedere la documentazione di [MRTK Scene Understanding.](/windows/mixed-reality/mrtk-unity/features/spatial-awareness/scene-understanding)

La sezione seguente consente di acquisire familiarità con le nozioni di base di SceneUnderstanding. Questa sezione contiene le nozioni di base, a questo punto è necessario avere un contesto sufficiente per esplorare le applicazioni di esempio per vedere come sceneUnderstanding viene usato in modo olistico.

### <a name="initialization"></a>Inizializzazione

Il primo passaggio per lavorare con SceneUnderstanding consiste nell'ottenere un riferimento a un oggetto Scene da parte dell'applicazione. Questa operazione può essere eseguita in uno dei due modi seguenti: una scena può essere calcolata dal driver o una scena esistente calcolata in passato può essere de serializzata. Quest'ultimo è utile per lavorare con SceneUnderstanding durante lo sviluppo, in cui le applicazioni e le esperienze possono essere prototipate rapidamente senza un dispositivo di realtà mista.

Le scene vengono calcolate usando sceneObserver. Prima di creare una scena, l'applicazione deve eseguire una query sul dispositivo per assicurarsi che supporti SceneUnderstanding, nonché per richiedere l'accesso utente per le informazioni necessarie a SceneUnderstanding.
<!--Unity Note-->
```cs
if (!SceneObserver.IsSupported())
{
    // Handle the error
}

// This call should grant the access we need.
await SceneObserver.RequestAccessAsync();
```

Se RequestAccessAsync() non viene chiamato, il calcolo di una nuova scena avrà esito negativo. Verrà quindi calcolata una nuova scena basata sul visore VR di realtà mista e con un raggio di 10 metri.

```cs
// Create Query settings for the scene update
SceneQuerySettings querySettings;

querySettings.EnableSceneObjectQuads = true;                                       // Requests that the scene updates quads.
querySettings.EnableSceneObjectMeshes = true;                                      // Requests that the scene updates watertight mesh data.
querySettings.EnableOnlyObservedSceneObjects = false;                              // Do not explicitly turn off quad inference.
querySettings.EnableWorldMesh = true;                                              // Requests a static version of the spatial mapping mesh.
querySettings.RequestedMeshLevelOfDetail = SceneMeshLevelOfDetail.Fine;            // Requests the finest LOD of the static spatial mapping mesh.

// Initialize a new Scene
Scene myScene = SceneObserver.ComputeAsync(querySettings, 10.0f).GetAwaiter().GetResult();
```

### <a name="initialization-from-data-also-known-as-the-pc-path"></a>Inizializzazione dai dati (nota anche come . il percorso del PC)

Anche se le scene possono essere calcolate per l'utilizzo diretto, possono anche essere calcolate in formato serializzato per un uso successivo. Questo si è dimostrato utile per lo sviluppo perché consente agli sviluppatori di lavorare e testare Scene Understanding senza la necessità di un dispositivo. L'azione di serializzazione di una scena è quasi identica al calcolo. I dati vengono restituiti all'applicazione anziché essere deserializzati localmente dall'SDK. È quindi possibile deserializzarlo manualmente o salvarlo per un uso futuro.

```cs
// Create Query settings for the scene update
SceneQuerySettings querySettings;

// Compute a scene but serialized as a byte array
SceneBuffer newSceneBuffer = SceneObserver.ComputeSerializedAsync(querySettings, 10.0f).GetAwaiter().GetResult();

// If we want to use it immediately we can de-serialize the scene ourselves
byte[] newSceneData = new byte[newSceneBuffer.Size];
newSceneBuffer.GetData(newSceneData);
Scene mySceneDeSerialized = Scene.Deserialize(newSceneData);

// Save newSceneData for later
```

### <a name="sceneobject-enumeration"></a>Enumerazione SceneObject

Ora che l'applicazione ha una scena, l'applicazione esamina e interagisce con SceneObjects. Questa operazione viene eseguita accedendo **alla proprietà SceneObjects:**

```cs
SceneObject firstFloor = null;

// Find the first floor object
foreach (var sceneObject in myScene.SceneObjects)
{
    if (sceneObject.Kind == SceneObjectKind.Floor)
    {
        firstFloor = sceneObject;
        break;
    }
}
```

### <a name="component-update-and-refinding-components"></a>Aggiornamento e perfezionamento dei componenti

Esiste un'altra funzione che recupera i componenti nella scena denominata ***FindComponent.*** Questa funzione è utile quando si aggiornano gli oggetti di rilevamento e li si trova in scene successive. Il codice seguente calcola una nuova scena rispetto a una scena precedente e quindi trova il piano nella nuova scena.

```cs
// Compute a new scene, and tell the system that we want to compute relative to the previous scene
Scene myNextScene = SceneObserver.ComputeAsync(querySettings, 10.0f, myScene).GetAwaiter().GetResult();

// Use the Id for the floor we found last time, and find it again
firstFloor = (SceneObject)myNextScene.FindComponent(firstFloor.Id);

if (firstFloor != null)
{
    // We found it again, we can now update the transforms of all objects we attached to this floor transform
}
```

## <a name="accessing-meshes-and-quads-from-scene-objects"></a>Accesso a mesh e quad da oggetti scena

Una volta trovati gli oggetti SceneObject, è molto probabile che l'applicazione voglia accedere ai dati contenuti nei quad/mesh da cui è composta. È possibile accedere a questi dati con le proprietà ***Quads** _ e _ *_Meshes_**. Il codice seguente enumera tutti i quad e le mesh dell'oggetto floor.

```cs

// Get the transform for the SceneObject
System.Numerics.Matrix4x4 objectToSceneOrigin = firstFloor.GetLocationAsMatrix();

// Enumerate quads
foreach (var quad in firstFloor.Quads)
{
    // Process quads
}

// Enumerate meshes
foreach (var mesh in firstFloor.Meshes)
{
    // Process meshes
}
```

Si noti che è l'oggetto SceneObject con la trasformazione relativa all'origine della scena. Ciò è dovuto al fatto che SceneObject rappresenta un'istanza di una "cosa" ed è localizzato nello spazio, i quad e le mesh rappresentano la geometria trasformata rispetto al relativo elemento padre. È possibile che SceneObject separati puntino allo stesso SceneMesh/SceneQuad SceneComponents ed è anche possibile che un Oggetto SceneObject abbia più sceneMesh/SceneQuad.

### <a name="dealing-with-transforms"></a>Gestione delle trasformazioni

Scene Understanding ha effettuato un tentativo intenzionale di allinearsi alle rappresentazioni tradizionali della scena 3D quando si gestiscono le trasformazioni. Ogni scena è quindi limitata a un singolo sistema di coordinate in modo molto simile alle rappresentazioni ambientali 3D più comuni. Ogni sceneObject fornisce la propria posizione rispetto al sistema di coordinate. Se l'applicazione ha a che fare con scene che estendono il limite di ciò che fornisce una singola origine, può ancorare SceneObject a SpatialAnchors o generare diverse scene e unirle tra loro, ma per semplicità si presuppone che le scene con dimensioni mance siano presenti nella propria origine localizzata da un NodeId definito da Scene.OriginSpatialGraphNodeId.
<!--Unity Note-->
Il codice Unity seguente, ad esempio, illustra come usare le API Perception Windows Unity per allineare i sistemi di coordinate. Vedere [SpatialCoordinateSystem](/uwp/api/windows.perception.spatial.spatialcoordinatesystem) e [SpatialGraphInteropPreview](/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview) per informazioni dettagliate sulle API per la percezione di Windows e Oggetti nativi di realtà mista [in Unity](/windows/mixed-reality/unity-xrdevice-advanced) per informazioni dettagliate su come ottenere un SpatialCoordinateSystem corrispondente all'origine del mondo unity.

```cs
private System.Numerics.Matrix4x4? GetSceneToUnityTransformAsMatrix4x4(SceneUnderstanding.Scene scene)
{

      System.Numerics.Matrix4x4? sceneToUnityTransform = System.Numerics.Matrix4x4.Identity;

      Windows.Perception.Spatial.SpatialCoordinateSystem sceneCoordinateSystem = Microsoft.Windows.Perception.Spatial.Preview.SpatialGraphInteropPreview.CreateCoordinateSystemForNode(scene.OriginSpatialGraphNodeId);
      HolograhicFrameData holoFrameData =  Marshal.PtrToStructure<HolograhicFrameData>(UnityEngine.XR.XRDevice.GetNativePtr());
      Windows.Perception.Spatial.SpatialCoordinateSystem unityCoordinateSystem = Microsoft.Windows.Perception.Spatial.SpatialCoordinateSystem.FromNativePtr(holoFrameData.ISpatialCoordinateSystemPtr);

      sceneToUnityTransform = sceneCoordinateSystem.TryGetTransformTo(unityCoordinateSystem);

      if(sceneToUnityTransform != null)
      {
          sceneToUnityTransform = ConvertRightHandedMatrix4x4ToLeftHanded(sceneToUnityTransform.Value);
      }
      else
      {
          return null;
      }

    return sceneToUnityTransform;
}
```

Ogni `SceneObject` oggetto ha una trasformazione, che viene quindi applicata a tale oggetto. In Unity si esegue la conversione in coordinate della mano destra e si assegnano trasformazioni locali nel modo seguente:

```cs
private System.Numerics.Matrix4x4 ConvertRightHandedMatrix4x4ToLeftHanded(System.Numerics.Matrix4x4 matrix)
{
    matrix.M13 = -matrix.M13;
    matrix.M23 = -matrix.M23;
    matrix.M43 = -matrix.M43;

    matrix.M31 = -matrix.M31;
    matrix.M32 = -matrix.M32;
    matrix.M34 = -matrix.M34;

    return matrix;
}

 private void SetUnityTransformFromMatrix4x4(Transform targetTransform, System.Numerics.Matrix4x4 matrix, bool updateLocalTransformOnly = false)
 {
    if(targetTransform == null)
    {
        return;
    }

    Vector3 unityTranslation;
    Quaternion unityQuat;
    Vector3 unityScale;

    System.Numerics.Vector3 vector3;
    System.Numerics.Quaternion quaternion;
    System.Numerics.Vector3 scale;

    System.Numerics.Matrix4x4.Decompose(matrix, out scale, out quaternion, out vector3);

    unityTranslation = new Vector3(vector3.X, vector3.Y, vector3.Z);
    unityQuat        = new Quaternion(quaternion.X, quaternion.Y, quaternion.Z, quaternion.W);
    unityScale       = new Vector3(scale.X, scale.Y, scale.Z);

    if(updateLocalTransformOnly)
    {
        targetTransform.localPosition = unityTranslation;
        targetTransform.localRotation = unityQuat;
    }
    else
    {
        targetTransform.SetPositionAndRotation(unityTranslation, unityQuat);
    }
}

// Assume we have an SU object called suObject and a unity equivalent unityObject

System.Numerics.Matrix4x4 converted4x4LocationMatrix = ConvertRightHandedMatrix4x4ToLeftHanded(suObject.GetLocationAsMatrix());
SetUnityTransformFromMatrix4x4(unityObject.transform, converted4x4LocationMatrix, true);
        
```

### <a name="quad"></a>Quad

I quad sono stati progettati per aiutare gli scenari di posizionamento 2D e devono essere pensati come estensioni agli elementi UX canvas 2D. Anche se i quad sono componenti di SceneObject e possono essere sottoposti a rendering in 3D, le API Quad presuppongono che i quad siano strutture 2D. Offrono informazioni come extent, forma e api per il posizionamento.

I quad hanno extent rettangolari, ma rappresentano superfici 2D a forma arbitraria. Per abilitare il posizionamento su queste superfici 2D che interagiscono con i quad dell'ambiente 3D, sono disponibili utilità che rendono possibile questa interazione. Scene Understanding offre attualmente due funzioni di questo tipo, **FindCentermostPlacement** **e GetSurfaceMask.** FindCentermostPlacement è un'API di alto livello che individua una posizione sul quad in cui è possibile posizionare un oggetto e tenterà di trovare la posizione migliore per l'oggetto assicurando che il rettangolo di selezione fornito rimanga sulla superficie sottostante.

> [!NOTE]
> Le coordinate dell'output sono relative al quad nello "spazio quad" con l'angolo superiore sinistro (x = 0, y = 0), esattamente come con altri tipi windows Rect. Assicurarsi di prendere in considerazione questo problema quando si lavora con le origini dei propri oggetti. 

L'esempio seguente mostra come trovare la posizione più al centro e ancorare un ologramma al quad.

```cs
// This code assumes you already have a "Root" object that attaches the Scene's Origin.

// Find the first quad
foreach (var sceneObject in myScene.SceneObjects)
{
    // Find a wall
    if (sceneObject.Kind == SceneObjectKind.Wall)
    {
        // Get the quad
        var quads = sceneObject.Quads;
        if (quads.Count > 0)
        {
            // Find a good location for a 1mx1m object  
            System.Numerics.Vector2 location;
            if (quads[0].FindCentermostPlacement(new System.Numerics.Vector2(1.0f, 1.0f), out location))
            {
                // We found one, anchor something to the transform
                // Step 1: Create a new game object for the quad itself as a child of the scene root
                // Step 2: Set the local transform from quads[0].Position and quads[0].Orientation
                // Step 3: Create your hologram and set it as a child of the quad's game object
                // Step 4: Set the hologram's local transform to a translation (location.x, location.y, 0)
            }
        }
    }
}
```

I passaggi da 1 a 4 dipendono fortemente dal framework o dall'implementazione specifici, ma i temi devono essere simili. È importante notare che il quad rappresenta semplicemente un piano 2D delimitato localizzato nello spazio. Facendo in modo che il motore/framework sappia dove si trova il quad e che radicei gli oggetti rispetto al quad, gli ologrammi verranno posizionati correttamente rispetto al mondo reale. 

<!-- 
// TODO: Add sample link when released
For more detailed information please see our samples on quads which show specific implementations.
-->

### <a name="mesh"></a>Mesh

Le mesh rappresentano rappresentazioni geometriche di oggetti o ambienti. Analogamente al [mapping](../../design/spatial-mapping.md)spaziale, i dati dell'indice mesh e dei vertici forniti con ogni mesh di superficie spaziale utilizzano lo stesso layout familiare dei buffer di vertici e indici usati per il rendering delle mesh triangolare in tutte le MODERNE API di rendering. Le posizioni dei vertici vengono fornite nel sistema di coordinate di `Scene` . Le API specifiche usate per fare riferimento a questi dati sono le seguenti:

```cs
void GetTriangleIndices(int[] indices);
void GetVertices(System.Numerics.Vector3[] vertices);
```

Il codice seguente fornisce un esempio di generazione di un elenco di triangoli dalla struttura mesh:

```cs
uint[] indices = new uint[mesh.TriangleIndexCount];
System.Numerics.Vector3[] positions = new System.Numerics.Vector3[mesh.VertexCount];

mesh.GetTriangleIndices(indices);
mesh.GetVertexPositions(positions);
```

I buffer di indice/vertice devono essere >= conteggi di indici/vertici, ma in caso contrario possono essere ridimensionati in modo arbitrario consentendo un riutilizzo efficiente della memoria.

### <a name="collidermesh"></a>ColliderMesh

Gli oggetti scena forniscono l'accesso ai dati della mesh e della mesh collisore tramite le proprietà Meshes e ColliderMeshes. Queste mesh corrisponderanno sempre, vale a dire che l'indice i della proprietà Meshes rappresenta la stessa geometria dell'indice i'th della proprietà ColliderMeshes. Se il runtime o l'oggetto supporta le mesh di collisore, si ottiene il poligono più basso e l'approssimazione dell'ordine più alto ed è consigliabile usare ColliderMeshes ovunque l'applicazione usi collisori. Se il sistema non supporta collisori, l'oggetto Mesh restituito in ColliderMeshes sarà lo stesso oggetto della mesh riducendo i vincoli di memoria.

## <a name="developing-with-scene-understanding"></a>Sviluppo con comprensione della scena

A questo punto, è necessario comprendere i blocchi predefiniti principali del runtime di comprensione della scena e dell'SDK. La maggior parte della potenza e della complessità si trova nei modelli di accesso, nell'interazione con framework 3D e in strumenti che possono essere scritti su queste API per eseguire attività più avanzate, ad esempio pianificazione spaziale, analisi delle camere, navigazione, fisica e così via. Ci auguriamo di acquisire questi esempi che dovrebbero guidare l'utente nella direzione corretta per rendere i tuoi scenari più luminosi. Se sono presenti esempi o scenari che non vengono affrontati, è possibile contattarci e proveremo a documentare/creare un prototipo di ciò che serve.

### <a name="where-can-i-get-sample-code"></a>Dove è possibile ottenere codice di esempio?
<!--Unity Note-->
Il codice di esempio di Scene Understanding per Unity è disponibile nella pagina [di esempio di Unity.](https://github.com/sceneunderstanding-microsoft/unitysample) Questa applicazione consente di comunicare con il dispositivo ed eseguire il rendering dei vari oggetti scena oppure di caricare una scena serializzata nel PC e di provare Scene Understanding senza un dispositivo.

### <a name="where-can-i-get-sample-scenes"></a>Dove è possibile ottenere scene di esempio?

Se hai holoLens2, puoi salvare qualsiasi scena acquisita salvando l'output di ComputeSerializedAsync nel file e deserializzandolo per comodità. 

Se non hai un dispositivo HoloLens2 ma vuoi usare Scene Understanding, dovrai scaricare una scena pre-acquisita. L'esempio Scene Understanding viene attualmente fornito con scene serializzate che possono essere scaricate e usate in base alle proprie esigenze. È possibile trovarli qui:

[Scene di esempio per la comprensione della scena](https://github.com/microsoft/MixedReality-SceneUnderstanding-Samples)

## <a name="see-also"></a>Vedere anche

* [Mapping spaziale](../../design/spatial-mapping.md)
* [Informazioni sulle scene](../../design/scene-understanding.md)
* [Esempio unity](https://github.com/microsoft/MixedReality-SceneUnderstanding-Samples)
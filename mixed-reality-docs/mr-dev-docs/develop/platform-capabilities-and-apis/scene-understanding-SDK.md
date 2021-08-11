---
title: SDK di comprensione della scena
description: Informazioni su come installare e usare Scene Understanding SDK, inclusi componenti, mesh e oggetti nelle app di realtà mista.
author: szymons
ms.author: szymons
ms.date: 12/14/2020
ms.topic: article
keywords: Comprensione della scena, mapping spaziale, Windows Mixed Reality, Unity
ms.openlocfilehash: 1b93f3137e1ac1309ee56e974a0fa33608114f16dfb65a13e369490f45d6beb3
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115193640"
---
# <a name="scene-understanding-sdk-overview"></a>Panoramica dell'SDK di comprensione della scena

La comprensione della scena trasforma i dati dei sensori dell'ambiente non strutturati che il dispositivo di realtà mista acquisisce e converte in una potente rappresentazione astratta. L'SDK funge da livello di comunicazione tra l'applicazione e il runtime scene understanding. Ha lo scopo di simulare i costrutti standard esistenti, ad esempio grafici di scena 3D per rappresentazioni 3D e rettangoli e pannelli 2D per applicazioni 2D. Mentre i costrutti simulare Scene Understanding verranno mappati a framework concreti, in generale SceneUnderstanding è indipendente dal framework, consentendo l'interoperabilità tra diversi framework che interagiscono con esso. Con l'evoluzione di Scene Understanding, il ruolo dell'SDK è garantire che le nuove rappresentazioni e funzionalità continuino a essere esposte all'interno di un framework unificato. In questo documento verranno presentati prima di tutto concetti generali che consentono di acquisire familiarità con l'ambiente/utilizzo di sviluppo e quindi fornire una documentazione più dettagliata per classi e costrutti specifici.

## <a name="where-do-i-get-the-sdk"></a>Dove è possibile ottenere l'SDK?

SceneUnderstanding SDK è scaricabile tramite lo strumento [di funzionalità di realtà mista](../unity/welcome-to-mr-feature-tool.md).

**Nota:** la versione più recente dipende dai pacchetti di anteprima e sarà necessario abilitare i pacchetti in versione non definitiva per visualizzarla.

Per la versione 0.5.2022-rc e versioni successive, Scene Understanding supporta le proiezioni del linguaggio per C# e C++ consentendo alle applicazioni di sviluppare applicazioni per piattaforme Win32 o UWP. A questa versione, SceneUnderstanding supporta unity nell'editor, a parte SceneObserver, che viene usato esclusivamente per comunicare con HoloLens2. 

SceneUnderstanding richiede Windows SDK versione 18362 o successiva. 

## <a name="conceptual-overview"></a>Panoramica dei concetti

### <a name="the-scene"></a>Scena

Il dispositivo di realtà mista integra costantemente informazioni su ciò che vede nell'ambiente. Scene Understanding imbuto tutte queste origini dati e produce un'unica astrazione coesa. Scene Understanding genera scene, che sono una composizione di [SceneObject che](scene-understanding-SDK.md#sceneobjects) rappresentano un'istanza di un singolo elemento, ad esempio una barriera,un controsoffitto o un piano. Gli oggetti scena stessi sono una composizione di [SceneComponents, che rappresentano parti più granulari che costituiscono questo SceneObject. Esempi di componenti sono i quad e le mesh, ma in futuro potrebbero rappresentare recinti di selezione, mesh di collisione, metadati e così via.

Il processo di conversione dei dati del sensore non elaborati in una scena è un'operazione potenzialmente costosa che potrebbe richiedere secondi per spazi medi (circa 10x10 m) in minuti per spazi di grandi dimensioni (circa 50x50 m) e quindi non è un'operazione che viene calcolata dal dispositivo senza richiesta dell'applicazione. La generazione della scena viene invece attivata dall'applicazione su richiesta. La classe SceneObserver include metodi statici che possono calcolare o deserializzare una scena, con cui è quindi possibile enumerare/interagire. L'azione "Calcolo" viene eseguita su richiesta ed eseguita sulla CPU, ma in un processo separato (il driver di realtà mista). Tuttavia, mentre si esegue il calcolo in un altro processo, i dati della scena risultanti vengono archiviati e gestiti nell'applicazione nell'oggetto Scene. 

Di seguito è riportato un diagramma che illustra questo flusso di processo e mostra esempi di due applicazioni che si interfacciano con il runtime scene understanding. 

![Diagramma del processo](images/SU-ProcessFlow.png)

Sul lato sinistro è presente un diagramma del runtime di realtà mista, che è sempre in esecuzione nel proprio processo. Questo runtime è responsabile dell'esecuzione del rilevamento dei dispositivi, del mapping spaziale e di altre operazioni che Scene Understanding usa per comprendere e comprendere il mondo che ti circonda. Sul lato destro del diagramma vengono mostrate due applicazioni teoriche che usano Scene Understanding. La prima applicazione si interfaccia con MRTK, che usa internamente Scene Understanding SDK, la seconda app calcola e usa due istanze di scena separate. Tutte e tre le scene in questo diagramma generano istanze distinte delle scene, il driver non verifica lo stato globale condiviso tra le applicazioni e gli oggetti scena in una scena non vengono trovati in un'altra. Scene Understanding fornisce un meccanismo per tenere traccia nel tempo, ma questa operazione viene eseguita usando l'SDK. Il codice di rilevamento è già in esecuzione nell'SDK nel processo dell'app.

Poiché ogni scena archivia i dati nello spazio di memoria dell'applicazione, è possibile presupporre che tutte le funzioni dell'oggetto Scene o i dati interni siano sempre eseguiti nel processo dell'applicazione.

### <a name="layout"></a>Layout

Per usare Scene Understanding, può essere utile conoscere e comprendere in che modo il runtime rappresenta i componenti in modo logico e fisico. La scena rappresenta i dati con un layout specifico che è stato scelto come semplice mantenendo una struttura sottostante che è responsabile di soddisfare i requisiti futuri senza dover eseguire revisioni importanti. La scena esegue questa operazione archiviando tutti i componenti (blocchi predefiniti per tutti gli oggetti scena) in un elenco semplice e definendo la gerarchia e la composizione tramite riferimenti in cui componenti specifici fanno riferimento ad altri.

Di seguito è riportato un esempio di struttura nella forma flat e logica.

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

Questa illustrazione evidenzia la differenza tra il layout fisico e logico della scena. A sinistra è visualizzato il layout gerarchico dei dati visualizzati dall'applicazione durante l'enumerazione della scena. A destra si può vedere che la scena è costituita da 12 componenti distinti accessibili singolarmente, se necessario. Quando si elabora una nuova scena, ci si aspetta che le applicazioni passino logicamente in questa gerarchia, tuttavia quando si esegue il rilevamento tra gli aggiornamenti della scena, alcune applicazioni potrebbero essere interessate solo a componenti specifici condivisi tra due scene.

## <a name="api-overview"></a>Panoramica delle API

La sezione seguente offre una panoramica generale dei costrutti in Scene Understanding. La lettura di questa sezione consente di comprendere come vengono rappresentate le scene e a cosa vengono usati i vari componenti. Nella sezione successiva verranno forniti esempi di codice concreti e dettagli aggiuntivi che verranno illustrati in questa panoramica.

Tutti i tipi descritti di seguito si trovano nello spazio dei `Microsoft.MixedReality.SceneUnderstanding` nomi .

### <a name="scenecomponents"></a>SceneComponents

Ora che si è compreso il layout logico delle scene, è ora possibile presentare il concetto di SceneComponents e come vengono usati per comporre la gerarchia. SceneComponents è la scomposizione più granulare in SceneUnderstanding che rappresenta un singolo elemento principale, ad esempio una mesh, un quad o un rettangolo di selezione. SceneComponents è un elemento che può essere aggiornato in modo indipendente e a cui possono fare riferimento altri oggetti SceneComponent, pertanto hanno una singola proprietà globale un ID univoco, che consentono questo tipo di meccanismo di rilevamento/riferimento. Gli ID vengono usati per la composizione logica della gerarchia della scena, nonché per la persistenza degli oggetti (l'azione di aggiornamento di una scena rispetto a un'altra). 

Se si tratta ogni scena appena calcolata come distinta e si enumerano semplicemente tutti i dati al suo interno, gli ID sono in gran parte trasparenti per l'utente. Tuttavia, se si prevede di tenere traccia dei componenti su diversi aggiornamenti, userai gli ID per indicizzare e trovare SceneComponents tra gli oggetti Scene.

### <a name="sceneobjects"></a>Oggetti SceneObject

SceneObject è un oggetto SceneComponent che rappresenta un'istanza di una "cosa", ad esempio una barriera, un piano, un controsoffitto e così via. espresso dalla relativa proprietà Kind. Gli oggetti SceneObject sono geometrici e pertanto hanno funzioni e proprietà che rappresentano la posizione nello spazio, ma non contengono strutture geometriche o logiche. SceneObjects fa invece riferimento ad altri oggetti SceneComponent, in particolare SceneQuads e SceneMeshes, che forniscono le varie rappresentazioni supportate dal sistema. Quando viene calcolata una nuova scena, l'applicazione enumererà probabilmente gli Oggetti Scena della scena per elaborare gli elementi a cui è interessata.

SceneObjects può avere uno degli elementi seguenti:

<table>
<tr>
<th>SceneObjectKind</th> <th>Descrizione</th>
</tr>
<tr><td>Sfondo</td><td>SceneObject non è noto come <b>uno</b> degli altri tipi riconosciuti di oggetto scena. Questa classe non deve essere confusa con Unknown, dove Background non è noto come wall/floor/ceiling e così via. mentre sconosciuto non è ancora stato categorizzato.</b></td></tr>
<tr><td>Parete</td><td>Una barriera fisica. Si presuppone che le pareti siano strutture ambientali mobili.</td></tr>
<tr><td>Piano</td><td>I piani sono superfici su cui si può andare. Nota: i piedini non sono piani. Si noti anche che i piani presuppongono qualsiasi superficie raggiungibile e pertanto non esiste alcun presupposto esplicito di un piano singolare. Strutture multi-livello, rampe e così via deve essere classificata come floor.</td></tr>
<tr><td>Ceiling</td><td>La superficie superiore di una stanza.</td></tr>
<tr><td>Piattaforma</td><td>Una superficie piana di grandi dimensioni su cui è possibile posizionare gli ologrammi. In genere rappresentano tabelle, controsoffitti e altre grandi superfici orizzontali.</td></tr>
<tr><td>World</td><td>Etichetta riservata per i dati geometrici indipendente dall'etichettatura. La mesh generata impostando il flag di aggiornamento EnableWorldMesh verrà classificata come mondo.</td></tr>
<tr><td>Sconosciuto</td><td>Questo oggetto scena deve ancora essere classificato e assegnato a un tipo. Questo non deve essere confuso con Background, poiché questo oggetto potrebbe essere qualsiasi cosa, il sistema non ha ancora creato una classificazione sufficientemente solida per questo oggetto.</td></tr>
</tr>
</table>

### <a name="scenemesh"></a>SceneMesh

SceneMesh è un oggetto SceneComponent che approssima la geometria di oggetti geometrici arbitrari usando un elenco di triangoli. SceneMeshes vengono usati in diversi contesti, possono rappresentare i componenti della struttura delle celle a tenuta stagna o come WorldMesh, che rappresenta la mesh di mapping spaziale non associato associata alla scena. I dati di indice e vertice forniti con ogni mesh utilizzano lo stesso layout familiare dei [buffer](/windows/win32/direct3d9/rendering-from-vertex-and-index-buffers) vertice e indice usati per il rendering delle mesh triangolo in tutte le MODERNE API di rendering. In Scene Understanding le mesh usano indici a 32 bit e possono essere suddivise in blocchi per determinati motori di rendering.

#### <a name="winding-order-and-coordinate-systems"></a>Ordine di avvolgimento e sistemi di coordinate

Tutte le mesh prodotte da Scene Understanding dovrebbero restituire mesh in un sistema Right-Handed coordinate usando l'ordine di avvolgimento in senso orario. 

Nota: le compilazioni del sistema operativo precedenti 191105 potrebbero avere un bug noto in cui le mesh "World" venivano restituite Counter-Clockwise ordine di avvolgimento, che è stato successivamente risolto.

### <a name="scenequad"></a>SceneQuad

SceneQuad è un oggetto SceneComponent che rappresenta le superfici 2d che occupano il mondo 3D. SceneQuads può essere usato in modo analogo a ARKit ARPlaneAnchor o ARCore Planes, ma offre funzionalità di alto livello come canvas 2D da usare dalle app flat o dall'esperienza utente aumentata. Vengono fornite API specifiche 2D per quad che rendono il posizionamento e il layout semplici da usare e lo sviluppo (ad eccezione del rendering) con quad dovrebbe essere più simile all'uso di aree di disegno 2d rispetto alle mesh 3D.

#### <a name="scenequad-shape"></a>Forma SceneQuad

SceneQuads definisce una superficie rettangolare delimitata in 2d. SceneQuads, tuttavia, rappresenta superfici con forme arbitrarie e potenzialmente complesse,ad esempio una tabella a forma di ciambella. Per rappresentare la forma complessa della superficie di un quad è possibile usare l'API GetSurfaceMask per eseguire il rendering della forma della superficie in un buffer di immagine specificato. Se anche l'oggetto SceneObject con il quad ha una mesh, i triangoli della mesh devono essere equivalenti a questa immagine sottoposta a rendering, entrambi rappresentano la geometria reale della superficie, in coordinate 2d o 3d.

## <a name="scene-understanding-sdk-details-and-reference"></a>Informazioni di riferimento e dettagli sull'SDK per la comprensione della scena

> [!NOTE] 
> Quando si usa MRTK, si noti che si interagirà con MRTK e pertanto è possibile ignorare questa sezione [`WindowsSceneUnderstandingObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsSceneUnderstanding.Experimental.WindowsSceneUnderstandingObserver) nella maggior parte dei casi. Per altre informazioni, vedere la [documentazione di MRTK Scene Understanding.](/windows/mixed-reality/mrtk-unity/features/spatial-awareness/scene-understanding)

La sezione seguente consente di acquisire familiarità con le nozioni di base di SceneUnderstanding. Questa sezione dovrebbe fornire le nozioni di base, a questo punto si dovrebbe avere un contesto sufficiente per esplorare le applicazioni di esempio per vedere come SceneUnderstanding viene usato in modo olistico.

### <a name="initialization"></a>Inizializzazione

Il primo passaggio per l'uso di SceneUnderstanding consiste nell'ottenere un riferimento a un oggetto Scene da parte dell'applicazione. Questa operazione può essere eseguita in due modi, una scena può essere calcolata dal driver o una scena esistente calcolata in passato può essere de-serializzata. Quest'ultimo è utile per lavorare con SceneUnderstanding durante lo sviluppo, in cui le applicazioni e le esperienze possono essere prototipate rapidamente senza un dispositivo di realtà mista.

Le scene vengono calcolate usando sceneObserver. Prima di creare una scena, l'applicazione deve eseguire una query sul dispositivo per assicurarsi che supporti SceneUnderstanding, nonché richiedere all'utente l'accesso per le informazioni necessarie a SceneUnderstanding.

```cs
if (!SceneObserver.IsSupported())
{
    // Handle the error
}

// This call should grant the access we need.
await SceneObserver.RequestAccessAsync();
```

Se RequestAccessAsync() non viene chiamato, il calcolo di una nuova scena avrà esito negativo. Verrà quindi calcolata una nuova scena che si radica intorno al visore di realtà mista e ha un raggio di 10 metri.

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

Sebbene le scene possano essere calcolate per l'utilizzo diretto, possono anche essere calcolate in formato serializzato per un uso successivo. Ciò si è dimostrato utile per lo sviluppo perché consente agli sviluppatori di lavorare e testare la comprensione delle scene senza la necessità di un dispositivo. L'azione di serializzazione di una scena è quasi identica al calcolo, i dati vengono restituiti all'applicazione anziché essere deserializzati localmente dall'SDK. È quindi possibile deserializzarlo manualmente o salvarlo per un uso futuro.

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

Ora che l'applicazione ha una scena, l'applicazione esamina e interagisce con SceneObjects. Questa operazione viene eseguita accedendo alla **proprietà SceneObjects:**

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

### <a name="component-update-and-refinding-components"></a>Componenti di aggiornamento e perfezionamento dei componenti

È presente un'altra funzione che recupera i componenti nella scena denominata ***FindComponent***. Questa funzione è utile quando si aggiornano gli oggetti di rilevamento e li si trova nelle scene successive. Il codice seguente calcola una nuova scena rispetto a una scena precedente e quindi trova il piano nella nuova scena.

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

Dopo aver individuato SceneObjects, è molto probabile che l'applicazione voglia accedere ai dati contenuti nei quad/mesh di cui è composta. Questi dati sono accessibili con le proprietà ***Quads** _ e _ *_Meshes_**. Il codice seguente enumera tutti i quad e le mesh dell'oggetto floor.

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

Si noti che è l'oggetto SceneObject con la trasformazione relativa all'origine della scena. Ciò è dovuto al fatto che SceneObject rappresenta un'istanza di una "cosa" ed è localizzato nello spazio, i quad e le mesh rappresentano la geometria trasformata rispetto al relativo elemento padre. È possibile che sceneobject separati fanno riferimento allo stesso SceneMesh/SceneQuad SceneComponents ed è anche possibile che un oggetto SceneObject abbia più sceneMesh/SceneQuad.

### <a name="dealing-with-transforms"></a>Gestione delle trasformazioni

La comprensione della scena ha effettuato un tentativo intenzionale di allinearsi alle rappresentazioni tradizionali della scena 3D quando si gestiscono le trasformazioni. Ogni scena è quindi limitata a un singolo sistema di coordinate molto simile alle rappresentazioni ambientali 3D più comuni. SceneObjects ognuno fornisce la propria posizione rispetto al sistema di coordinate. Se l'applicazione ha a che fare con scene che estendono il limite di ciò che fornisce una singola origine, può ancorare SceneObjects a SpatialAnchors o generare diverse scene e unirle, ma per semplicità si presuppone che nella propria origine esistano scene stagnanti localizzate da un NodeId definito da Scene.OriginSpatialGraphNodeId.

Il codice Unity seguente, ad esempio, illustra come usare le API Perception e Unity Windows per allineare i sistemi di coordinate. Per informazioni dettagliate sulle API perception di Windows e sugli oggetti nativi di realtà mista [in Unity,](/windows/mixed-reality/unity-xrdevice-advanced) vedere [SpatialCoordinateSystem](/uwp/api/windows.perception.spatial.spatialcoordinatesystem) e [SpatialGraphInteropPreview.](/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview)

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

Ognuno `SceneObject` ha una trasformazione, che viene quindi applicata a tale oggetto. In Unity si esegue la conversione in coordinate con mano destra e si assegnano trasformazioni locali nel modo seguente:

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

I quad sono stati progettati per consentire scenari di posizionamento 2D e devono essere pensati come estensioni agli elementi UX del canvas 2D. Anche se i quad sono componenti di SceneObject e possono essere sottoposti a rendering in 3D, le API Quad presuppongono che i quad siano strutture 2D. Offrono informazioni come extent, forma e forniscono API per il posizionamento.

I quad hanno extent rettangolari, ma rappresentano superfici 2D di forma arbitraria. Per abilitare il posizionamento su queste superfici 2D che interagiscono con l'ambiente 3D, i quad offrono utilità per rendere possibile questa interazione. Attualmente Scene Understanding offre due funzioni di questo tipo, **FindCentermostPlacement** **e GetSurfaceMask.** FindCentermostPlacement è un'API di alto livello che individua una posizione sul quad in cui è possibile posizionare un oggetto e tenterà di trovare la posizione migliore per l'oggetto garantendo che il rettangolo di selezione specificato rimanga sulla superficie sottostante.

> [!NOTE]
> Le coordinate dell'output sono relative al quad nello "spazio quad" con l'angolo superiore sinistro (x = 0, y = 0), proprio come con altri tipi windows Rect. Assicurarsi di prendere in considerazione questo problema quando si lavora con le origini dei propri oggetti. 

L'esempio seguente mostra come trovare la posizione più posizionata al centro e ancorare un ologramma al quad.

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

I passaggi da 1 a 4 dipendono fortemente dal framework/implementazione specifico, ma i temi devono essere simili. È importante notare che il quad rappresenta semplicemente un piano 2D delimitato localizzato nello spazio. Facendo in modo che il motore/framework sappia dove si trova il quad e radicando gli oggetti rispetto al quad, gli ologrammi verranno posizionati correttamente rispetto al mondo reale. 

<!-- 
// TODO: Add sample link when released
For more detailed information please see our samples on quads which show specific implementations.
-->

### <a name="mesh"></a>Mesh

Le mesh rappresentano rappresentazioni geometriche di oggetti o ambienti. Analogamente al [mapping](../../design/spatial-mapping.md)spaziale, i dati dell'indice mesh e dei vertici forniti con ogni mesh di superficie spaziale utilizzano lo stesso layout familiare dei buffer di vertici e di indice usati per il rendering delle mesh a triangolo in tutte le MODERNE API di rendering. Le posizioni dei vertici vengono fornite nel sistema di coordinate di `Scene` . Le API specifiche usate per fare riferimento a questi dati sono le seguenti:

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

I buffer indice/vertice devono essere >= conteggi indice/vertice, ma in caso contrario possono essere ridimensionati arbitrariamente consentendo un riutilizzo efficiente della memoria.

### <a name="collidermesh"></a>ColliderMesh

Gli oggetti scena forniscono l'accesso ai dati mesh e collider mesh tramite le proprietà Meshes e ColliderMeshes. Queste mesh corrisponderanno sempre, vale a dire che l'indice i'esimo della proprietà Meshes rappresenta la stessa geometria dell'indice i'esimo della proprietà ColliderMeshes. Se il runtime/oggetto supporta le mesh di collisore, è garantito che si otterrà il poligono più basso, l'approssimazione dell'ordine più alto ed è buona norma usare ColliderMeshes ovunque l'applicazione usi collider. Se il sistema non supporta collisori, l'oggetto Mesh restituito in ColliderMeshes sarà lo stesso oggetto della mesh che riduce i vincoli di memoria.

## <a name="developing-with-scene-understanding"></a>Sviluppo con comprensione della scena

A questo punto, è necessario comprendere i blocchi predefiniti principali del runtime di comprensione della scena e dell'SDK. La maggior parte della potenza e della complessità risiede nei modelli di accesso, nell'interazione con framework 3D e negli strumenti che possono essere scritti su queste API per eseguire attività più avanzate come la pianificazione spaziale, l'analisi delle camere, la navigazione, la fisica e così via. Ci auguriamo di acquisire questi elementi in esempi che dovrebbero essere guidati nella direzione corretta per far risplendere gli scenari. Se sono presenti esempi o scenari che non vengono indirizzati, è possibile contattarci e si proverà a documentare/creare un prototipo delle informazioni necessarie.

### <a name="where-can-i-get-sample-code"></a>Dove è possibile ottenere codice di esempio?

Il codice di esempio di Scene Understanding per Unity è disponibile nella pagina [Pagina di esempio di Unity.](https://github.com/sceneunderstanding-microsoft/unitysample) Questa applicazione consente di comunicare con il dispositivo ed eseguire il rendering dei vari oggetti scena oppure di caricare una scena serializzata nel PC e di sperimentare La comprensione della scena senza un dispositivo.

### <a name="where-can-i-get-sample-scenes"></a>Dove è possibile ottenere scene di esempio?

Se hai holoLens2, puoi salvare qualsiasi scena acquisita salvando l'output di ComputeSerializedAsync nel file e deserializzandolo per comodità. 

Se non hai un dispositivo HoloLens2 ma vuoi riprodurre con Scene Understanding, dovrai scaricare una scena pre-acquisita. L'esempio Scene Understanding viene attualmente fornito con scene serializzate che possono essere scaricate e usate in base alle proprie esigenze. È possibile trovarli qui:

[Scene di esempio per la comprensione della scena](https://github.com/microsoft/MixedReality-SceneUnderstanding-Samples)

## <a name="see-also"></a>Vedere anche

* [Mapping spaziale](../../design/spatial-mapping.md)
* [Informazioni sulle scene](../../design/scene-understanding.md)
* [Esempio unity](https://github.com/microsoft/MixedReality-SceneUnderstanding-Samples)
---
ms.openlocfilehash: df8dbe19b0a93e2452a8e0b677145bed42b05010
ms.sourcegitcommit: e51e18e443d73a74a9c0b86b3ca5748652cd1b24
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/16/2021
ms.locfileid: "103603385"
---
# <a name="unity-2020--openxr"></a>[Unity 2020 + OpenXR](#tab/openxr)

> [!NOTE]
> Questi ancoraggi devono essere salvati e caricati nello stesso dispositivo. L'archiviazione di ancoraggio tra dispositivi verrà supportata tramite ancoraggi spaziali di Azure in una versione futura.

``` cs
public class Microsoft.MixedReality.ARSubsystems.XRAnchorStore
{
    // A list of all persisted anchors, which can be loaded.
    public IReadOnlyList<string> PersistedAnchorNames { get; }

    // Clear all persisted anchors
    public void Clear();

    // Load a single persisted anchor by name. The ARAnchorManager will create this new anchor and report it in
    // the ARAnchorManager.anchorsChanged event. The TrackableId returned here is the same TrackableId the
    // ARAnchor will have when it is instantiated.
    public TrackableId LoadAnchor(string name);

    // Attempts to persist an existing ARAnchor with the given TrackableId to the local store. Returns true if
    // the storage is successful, false otherwise.
    public bool TryPersistAnchor(string name, TrackableId trackableId);

    // Removes a single persisted anchor from the anchor store. This will not affect any ARAnchors in the Unity
    // scene, only the anchors in storage.
    public void UnpersistAnchor(string name);
}
```

Per caricare XRAnchorStore, il plug-in fornisce un metodo di estensione in XRAnchorSubsystem, il sottosistema di un ARAnchorManager:

``` cs
public static Task<XRAnchorStore> LoadAnchorStoreAsync(this XRAnchorSubsystem anchorSubsystem)
```

Per usare questo metodo di estensione, accedervi dal sottosistema di ARAnchorManager come indicato di seguito:

``` cs
ARAnchorManager arAnchorManager = GetComponent<ARAnchorManager>();
XRAnchorStore anchorStore = await arAnchorManager.subsystem.LoadAnchorStoreAsync();
```

Per un esempio completo di come salvare in modo permanente/non permanente gli ancoraggi, vedere gli script di ancoraggio-> di esempio GameObject e AnchorsSample.cs nella scena di [esempio di plug-in realtà mista OpenXR](../openxr-getting-started.md#hololens-2-samples):

![Screenshot del pannello gerarchia aperto nell'editor di Unity con l'esempio Anchors evidenziato](../images/openxr-features-img-04.png)

![Screenshot del pannello Inspector aperto nell'editor di Unity con lo script di esempio Anchors evidenziato](../images/openxr-features-img-05.png)

# <a name="unity-20192020--windows-xr-plugin"></a>[Plug-in Unity 2019/2020 + Windows XR](#tab/winxr)

> [!NOTE]
> Questi ancoraggi devono essere salvati e caricati nello stesso dispositivo. L'archiviazione di ancoraggio tra dispositivi verrà supportata tramite ancoraggi spaziali di Azure in una versione futura.

``` cs
public class UnityEngine.XR.WindowsMR.XRAnchorStore
{
    // A list of all persisted anchors, which can be loaded.
    public IReadOnlyList<string> PersistedAnchorNames { get; }

    // Clear all persisted anchors
    public void Clear();

    // Load a single persisted anchor by name. The ARAnchorManager will create this new anchor and report it in
    // the ARAnchorManager.anchorsChanged event. The TrackableId returned here is the same TrackableId the
    // ARAnchor will have when it is instantiated.
    public TrackableId LoadAnchor(string name);

    // Attempts to persist an existing ARAnchor with the given TrackableId to the local store. Returns true if
    // the storage is successful, false otherwise.
    public bool TryPersistAnchor(TrackableId id, string name);

    // Removes a single persisted anchor from the anchor store. This will not affect any ARAnchors in the Unity
    // scene, only the anchors in storage.
    public void UnpersistAnchor(string name);
}
```

Per caricare il XRAnchorStore, il plug-in fornisce un metodo di estensione in XRReferencePointSubsystem (Unity 2019) o XRAnchorSubsystem (Unity 2020), il sottosistema di un ARReferencePointManager/ARAnchorManager:

``` cs
public static Task<XRAnchorStore> TryGetAnchorStoreAsync(this XRReferencePointSubsystem anchorSubsystem); // Unity 2019
public static Task<XRAnchorStore> TryGetAnchorStoreAsync(this XRAnchorSubsystem anchorSubsystem); // Unity 2020
```

Per usare questo metodo di estensione, accedervi dal sottosistema di ARAnchorManager come indicato di seguito per Unity 2019:

``` cs
ARReferencePointManager arReferencePointManager = GetComponent<ARReferencePointManager>();
XRAnchorStore anchorStore = await arReferencePointManager.subsystem.TryGetAnchorStoreAsync();
```

oppure per Unity 2020:

``` cs
ARAnchorManager arAnchorManager = GetComponent<ARAnchorManager>();
XRAnchorStore anchorStore = await arAnchorManager.subsystem.TryGetAnchorStoreAsync();
```

# <a name="legacy-wsa"></a>[WSA legacy](#tab/wsa)

**Spazio dei nomi:** *UnityEngine. XR. WSA. Persistence*<br>
**Classe:** *WorldAnchorStore*

Il WorldAnchorStore consentirà di rendere permanente il percorso di WorldAnchor tra le sessioni. Per rendere effettivamente permanente gli ologrammi tra le sessioni, è necessario tenere traccia separatamente dei GameObject che usano un particolare ancoraggio mondiale. Spesso è opportuno creare una radice GameObject con un ancoraggio globale e avere elementi figlio olografici ancorati con un offset della posizione locale.

Per caricare gli ologrammi dalle sessioni precedenti:

1. Ottenere il WorldAnchorStore
2. Caricare i dati dell'app correlati all'ancoraggio globale, che fornisce l'ID dell'ancoraggio globale
3. Caricare un ancoraggio globale dall'ID

Per salvare gli ologrammi per le sessioni future:

1. Ottenere il WorldAnchorStore
2. Salva un ancoraggio globale specificando un ID
3. Salva i dati dell'app correlati all'ancoraggio globale insieme a un ID

### <a name="getting-the-worldanchorstore"></a>Recupero di WorldAnchorStore

È consigliabile tenere un riferimento a WorldAnchorStore in modo da essere a conoscenza quando è pronto per eseguire un'operazione. Poiché si tratta di una chiamata asincrona, potenzialmente non appena viene avviata, si vuole chiamare:

```cs
WorldAnchorStore.GetAsync(StoreLoaded);
```

StoreLoaded in questo caso è il gestore per il completamento del caricamento di WorldAnchorStore:

```cs
private void StoreLoaded(WorldAnchorStore store)
{
    this.store = store;
}
```

È ora disponibile un riferimento a WorldAnchorStore, che verrà usato per salvare e caricare specifici ancoraggi internazionali.

### <a name="saving-a-worldanchor"></a>Salvataggio di un WorldAnchor

Per salvare, è sufficiente assegnare un nome a quello che si sta salvando e passarlo nel WorldAnchor ottenuto in precedenza quando si desidera salvare. Nota: il tentativo di salvare due ancoraggi nella stessa stringa avrà esito negativo (Store. Il salvataggio restituirà false. Eliminare il salvataggio precedente prima di salvare quello nuovo:

```cs
private void SaveGame()
{
    // Save data about holograms positioned by this world anchor
    if (!this.savedRoot) // Only Save the root once
    {
           this.savedRoot = this.store.Save("rootGameObject", anchor);
           Assert(this.savedRoot);
    }
}
```

### <a name="loading-a-worldanchor"></a>Caricamento di un WorldAnchor

E per caricare:

```cs
private void LoadGame()
{
    // Save data about holograms positioned by this world anchor
    this.savedRoot = this.store.Load("rootGameObject", rootGameObject);
    if (!this.savedRoot)
    {
        s// We didn't actually have the game root saved! We have to re-place our objects or start over
    }
}
```

È inoltre possibile utilizzare Store. Eliminare () per rimuovere un ancoraggio precedentemente salvato e archiviato. Deselezionare () per rimuovere tutti i dati salvati in precedenza.

### <a name="enumerating-existing-anchors"></a>Enumerazione degli ancoraggi esistenti

Per individuare gli ancoraggi precedentemente archiviati, chiamare GetAllIds.

```cs
string[] ids = this.store.GetAllIds();
for (int index = 0; index < ids.Length; index++)
{
    Debug.Log(ids[index]);
}
```

## <a name="building-a-world-scale-experience"></a>Creazione di un'esperienza su scala globale

**Spazio dei nomi:** *UnityEngine. XR. WSA*<br>
**Tipo:** *WorldAnchor*

Per esperienze reali su **scala mondiale** su HoloLens che consentono agli utenti di superare i 5 metri, sono necessarie nuove tecniche oltre a quelle usate per le esperienze su scala. Una tecnica chiave da usare consiste nel creare un [ancoraggio spaziale](../../../design/coordinate-systems.md#spatial-anchors) per bloccare un cluster di ologrammi con precisione sul posto nel mondo fisico, indipendentemente dalla distanza di roaming dell'utente e quindi [ritrovare gli ologrammi nelle sessioni successive](../../../design/coordinate-systems.md#spatial-anchor-persistence).

In Unity si crea un ancoraggio spaziale aggiungendo il componente **WorldAnchor** Unity a un GameObject.

### <a name="adding-a-world-anchor"></a>Aggiunta di un ancoraggio globale

Per aggiungere un ancoraggio globale, chiamare `AddComponent<WorldAnchor>()` sull'oggetto gioco con la trasformazione che si vuole ancorare nel mondo reale.

```cs
WorldAnchor anchor = gameObject.AddComponent<WorldAnchor>();
```

Questo è tutto. Questo oggetto Game verrà ora ancorato alla posizione corrente nel mondo fisico. è possibile che le coordinate internazionali del mondo Unity vengano modificate leggermente nel tempo per garantire l'allineamento fisico. Per trovare nuovamente questa posizione ancorata in una sessione di app futura, vedere [caricamento di un ancoraggio globale](#loading-a-worldanchor) .

### <a name="removing-a-world-anchor"></a>Rimozione di un ancoraggio globale

Se non si vuole più che il GameObject sia bloccato in una posizione fisica del mondo e non si intende trasferirlo in questo frame, è possibile chiamare semplicemente Destroy nel componente World Anchor.

```cs
Destroy(gameObject.GetComponent<WorldAnchor>());
```

Se si vuole spostare il GameObject in questo frame, è necessario chiamare DestroyImmediate.

```cs
DestroyImmediate(gameObject.GetComponent<WorldAnchor>());
```

### <a name="moving-a-world-anchored-gameobject"></a>Trasferimento di una GameObject ancorata globale

Non è possibile spostare GameObject mentre è presente un ancoraggio globale. Se è necessario spostare il GameObject di questo frame, è necessario:

1. DestroyImmediate il componente di ancoraggio globale
2. Spostare il GameObject
3. Aggiungere un nuovo componente di ancoraggio globale a GameObject.

```cs
DestroyImmediate(gameObject.GetComponent<WorldAnchor>());
gameObject.transform.position = new Vector3(0, 0, 2);
WorldAnchor anchor = gameObject.AddComponent<WorldAnchor>();
```

### <a name="handling-locatability-changes"></a>Gestione delle modifiche apportate a Locatability

Un WorldAnchor non può essere locatable nel mondo fisico in un determinato momento. In tal caso, Unity non aggiornerà la trasformazione dell'oggetto ancorato. Questo può cambiare anche durante l'esecuzione di un'app. Se non si gestisce la modifica in locatability, l'oggetto non verrà visualizzato nella posizione fisica corretta del mondo.

Per ricevere notifiche sulle modifiche apportate a locatability:

1. Sottoscrivere l'evento OnTrackingChanged
2. Gestisci evento

L'evento **OnTrackingChanged** verrà chiamato ogni volta che l'ancoraggio spaziale sottostante viene modificato tra uno stato di locatable e non locatable.

```cs
anchor.OnTrackingChanged += Anchor_OnTrackingChanged;
```

Gestire quindi l'evento:

```cs
private void Anchor_OnTrackingChanged(WorldAnchor self, bool located)
{
    // This simply activates/deactivates this object and all children when tracking changes
    self.gameObject.SetActiveRecursively(located);
}
```

Talvolta gli ancoraggi si trovano immediatamente. In questo caso, la proprietà individuata dell'ancoraggio verrà impostata su true quando AddComponent <WorldAnchor> () restituisce. Di conseguenza, l'evento OnTrackingChanged non verrà attivato. Un modello pulito consiste nel chiamare il gestore OnTrackingChanged con lo stato individuato iniziale dopo aver collegato un ancoraggio.

```cs
Anchor_OnTrackingChanged(anchor, anchor.isLocated);
```

## <a name="persisting-holograms-for-multiple-devices"></a>Mantenimento degli ologrammi per più dispositivi

È possibile usare gli <a href="/azure/spatial-anchors/overview" target="_blank">ancoraggi spaziali di Azure</a> per creare un ancoraggio cloud durevole da un WorldAnchor locale, che può essere individuato dall'app su più dispositivi HoloLens, iOS e Android, anche se questi dispositivi non sono presenti contemporaneamente.  Poiché gli ancoraggi cloud sono persistenti, più dispositivi nel tempo possono visualizzare il contenuto di cui è stato eseguito il rendering rispetto a tale ancoraggio nella stessa posizione fisica.

Per iniziare a creare esperienze condivise in Unity, provare le <a href="/azure/spatial-anchors/unity-overview" target="_blank">guide introduttive Unity Anchors di Azure</a>di 5 minuti.

Quando si è operativi con i Anchor spaziali di Azure, è possibile <a href="/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">creare e individuare ancoraggi in Unity</a>.

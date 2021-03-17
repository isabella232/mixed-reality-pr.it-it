---
ms.openlocfilehash: df8dbe19b0a93e2452a8e0b677145bed42b05010
ms.sourcegitcommit: e51e18e443d73a74a9c0b86b3ca5748652cd1b24
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/16/2021
ms.locfileid: "103603385"
---
# <a name="unity-2020--openxr"></a>[<span data-ttu-id="acb61-101">Unity 2020 + OpenXR</span><span class="sxs-lookup"><span data-stu-id="acb61-101">Unity 2020 + OpenXR</span></span>](#tab/openxr)

> [!NOTE]
> <span data-ttu-id="acb61-102">Questi ancoraggi devono essere salvati e caricati nello stesso dispositivo.</span><span class="sxs-lookup"><span data-stu-id="acb61-102">These anchors are to be saved and loaded on the same device.</span></span> <span data-ttu-id="acb61-103">L'archiviazione di ancoraggio tra dispositivi verrà supportata tramite ancoraggi spaziali di Azure in una versione futura.</span><span class="sxs-lookup"><span data-stu-id="acb61-103">Cross-device anchor storage will be supported through Azure Spatial Anchors in a future release.</span></span>

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

<span data-ttu-id="acb61-104">Per caricare XRAnchorStore, il plug-in fornisce un metodo di estensione in XRAnchorSubsystem, il sottosistema di un ARAnchorManager:</span><span class="sxs-lookup"><span data-stu-id="acb61-104">To load the XRAnchorStore, the plugin provides an extension method on the XRAnchorSubsystem, the subsystem of an ARAnchorManager:</span></span>

``` cs
public static Task<XRAnchorStore> LoadAnchorStoreAsync(this XRAnchorSubsystem anchorSubsystem)
```

<span data-ttu-id="acb61-105">Per usare questo metodo di estensione, accedervi dal sottosistema di ARAnchorManager come indicato di seguito:</span><span class="sxs-lookup"><span data-stu-id="acb61-105">To use this extension method, access it from an ARAnchorManager's subsystem as follows:</span></span>

``` cs
ARAnchorManager arAnchorManager = GetComponent<ARAnchorManager>();
XRAnchorStore anchorStore = await arAnchorManager.subsystem.LoadAnchorStoreAsync();
```

<span data-ttu-id="acb61-106">Per un esempio completo di come salvare in modo permanente/non permanente gli ancoraggi, vedere gli script di ancoraggio-> di esempio GameObject e AnchorsSample.cs nella scena di [esempio di plug-in realtà mista OpenXR](../openxr-getting-started.md#hololens-2-samples):</span><span class="sxs-lookup"><span data-stu-id="acb61-106">To see a full example of persisting / unpersisting anchors, check out the Anchors -> Anchors Sample GameObject and AnchorsSample.cs script in the [Mixed Reality OpenXR Plugin Sample Scene](../openxr-getting-started.md#hololens-2-samples):</span></span>

![Screenshot del pannello gerarchia aperto nell'editor di Unity con l'esempio Anchors evidenziato](../images/openxr-features-img-04.png)

![Screenshot del pannello Inspector aperto nell'editor di Unity con lo script di esempio Anchors evidenziato](../images/openxr-features-img-05.png)

# <a name="unity-20192020--windows-xr-plugin"></a>[<span data-ttu-id="acb61-109">Plug-in Unity 2019/2020 + Windows XR</span><span class="sxs-lookup"><span data-stu-id="acb61-109">Unity 2019/2020 + Windows XR Plugin</span></span>](#tab/winxr)

> [!NOTE]
> <span data-ttu-id="acb61-110">Questi ancoraggi devono essere salvati e caricati nello stesso dispositivo.</span><span class="sxs-lookup"><span data-stu-id="acb61-110">These anchors are to be saved and loaded on the same device.</span></span> <span data-ttu-id="acb61-111">L'archiviazione di ancoraggio tra dispositivi verrà supportata tramite ancoraggi spaziali di Azure in una versione futura.</span><span class="sxs-lookup"><span data-stu-id="acb61-111">Cross-device anchor storage will be supported through Azure Spatial Anchors in a future release.</span></span>

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

<span data-ttu-id="acb61-112">Per caricare il XRAnchorStore, il plug-in fornisce un metodo di estensione in XRReferencePointSubsystem (Unity 2019) o XRAnchorSubsystem (Unity 2020), il sottosistema di un ARReferencePointManager/ARAnchorManager:</span><span class="sxs-lookup"><span data-stu-id="acb61-112">To load the XRAnchorStore, the plugin provides an extension method on the XRReferencePointSubsystem (Unity 2019) or XRAnchorSubsystem (Unity 2020), the subsystem of an ARReferencePointManager/ARAnchorManager:</span></span>

``` cs
public static Task<XRAnchorStore> TryGetAnchorStoreAsync(this XRReferencePointSubsystem anchorSubsystem); // Unity 2019
public static Task<XRAnchorStore> TryGetAnchorStoreAsync(this XRAnchorSubsystem anchorSubsystem); // Unity 2020
```

<span data-ttu-id="acb61-113">Per usare questo metodo di estensione, accedervi dal sottosistema di ARAnchorManager come indicato di seguito per Unity 2019:</span><span class="sxs-lookup"><span data-stu-id="acb61-113">To use this extension method, access it from an ARAnchorManager's subsystem as follows for Unity 2019:</span></span>

``` cs
ARReferencePointManager arReferencePointManager = GetComponent<ARReferencePointManager>();
XRAnchorStore anchorStore = await arReferencePointManager.subsystem.TryGetAnchorStoreAsync();
```

<span data-ttu-id="acb61-114">oppure per Unity 2020:</span><span class="sxs-lookup"><span data-stu-id="acb61-114">or for Unity 2020:</span></span>

``` cs
ARAnchorManager arAnchorManager = GetComponent<ARAnchorManager>();
XRAnchorStore anchorStore = await arAnchorManager.subsystem.TryGetAnchorStoreAsync();
```

# <a name="legacy-wsa"></a>[<span data-ttu-id="acb61-115">WSA legacy</span><span class="sxs-lookup"><span data-stu-id="acb61-115">Legacy WSA</span></span>](#tab/wsa)

<span data-ttu-id="acb61-116">**Spazio dei nomi:** *UnityEngine. XR. WSA. Persistence*</span><span class="sxs-lookup"><span data-stu-id="acb61-116">**Namespace:** *UnityEngine.XR.WSA.Persistence*</span></span><br>
<span data-ttu-id="acb61-117">**Classe:** *WorldAnchorStore*</span><span class="sxs-lookup"><span data-stu-id="acb61-117">**Class:** *WorldAnchorStore*</span></span>

<span data-ttu-id="acb61-118">Il WorldAnchorStore consentirà di rendere permanente il percorso di WorldAnchor tra le sessioni.</span><span class="sxs-lookup"><span data-stu-id="acb61-118">The WorldAnchorStore will allow you to persist the location of WorldAnchor's across sessions.</span></span> <span data-ttu-id="acb61-119">Per rendere effettivamente permanente gli ologrammi tra le sessioni, è necessario tenere traccia separatamente dei GameObject che usano un particolare ancoraggio mondiale.</span><span class="sxs-lookup"><span data-stu-id="acb61-119">To actually persist holograms across sessions, you'll need to separately keep track of your GameObjects that use a particular world anchor.</span></span> <span data-ttu-id="acb61-120">Spesso è opportuno creare una radice GameObject con un ancoraggio globale e avere elementi figlio olografici ancorati con un offset della posizione locale.</span><span class="sxs-lookup"><span data-stu-id="acb61-120">It often makes sense to create a GameObject root with a world anchor and have children holograms anchored by it with a local position offset.</span></span>

<span data-ttu-id="acb61-121">Per caricare gli ologrammi dalle sessioni precedenti:</span><span class="sxs-lookup"><span data-stu-id="acb61-121">To load holograms from previous sessions:</span></span>

1. <span data-ttu-id="acb61-122">Ottenere il WorldAnchorStore</span><span class="sxs-lookup"><span data-stu-id="acb61-122">Get the WorldAnchorStore</span></span>
2. <span data-ttu-id="acb61-123">Caricare i dati dell'app correlati all'ancoraggio globale, che fornisce l'ID dell'ancoraggio globale</span><span class="sxs-lookup"><span data-stu-id="acb61-123">Load app data relating to the world anchor, which gives you the ID of the world anchor</span></span>
3. <span data-ttu-id="acb61-124">Caricare un ancoraggio globale dall'ID</span><span class="sxs-lookup"><span data-stu-id="acb61-124">Load a world anchor from its ID</span></span>

<span data-ttu-id="acb61-125">Per salvare gli ologrammi per le sessioni future:</span><span class="sxs-lookup"><span data-stu-id="acb61-125">To save holograms for future sessions:</span></span>

1. <span data-ttu-id="acb61-126">Ottenere il WorldAnchorStore</span><span class="sxs-lookup"><span data-stu-id="acb61-126">Get the WorldAnchorStore</span></span>
2. <span data-ttu-id="acb61-127">Salva un ancoraggio globale specificando un ID</span><span class="sxs-lookup"><span data-stu-id="acb61-127">Save a world anchor specifying an ID</span></span>
3. <span data-ttu-id="acb61-128">Salva i dati dell'app correlati all'ancoraggio globale insieme a un ID</span><span class="sxs-lookup"><span data-stu-id="acb61-128">Save app data relating to the world anchor along with an ID</span></span>

### <a name="getting-the-worldanchorstore"></a><span data-ttu-id="acb61-129">Recupero di WorldAnchorStore</span><span class="sxs-lookup"><span data-stu-id="acb61-129">Getting the WorldAnchorStore</span></span>

<span data-ttu-id="acb61-130">È consigliabile tenere un riferimento a WorldAnchorStore in modo da essere a conoscenza quando è pronto per eseguire un'operazione.</span><span class="sxs-lookup"><span data-stu-id="acb61-130">You'll want to keep a reference to the WorldAnchorStore so you know when it's ready to perform an operation.</span></span> <span data-ttu-id="acb61-131">Poiché si tratta di una chiamata asincrona, potenzialmente non appena viene avviata, si vuole chiamare:</span><span class="sxs-lookup"><span data-stu-id="acb61-131">Since this is an async call, potentially as soon as start up, you want to call:</span></span>

```cs
WorldAnchorStore.GetAsync(StoreLoaded);
```

<span data-ttu-id="acb61-132">StoreLoaded in questo caso è il gestore per il completamento del caricamento di WorldAnchorStore:</span><span class="sxs-lookup"><span data-stu-id="acb61-132">StoreLoaded in this case is our handler for when the WorldAnchorStore has completed loading:</span></span>

```cs
private void StoreLoaded(WorldAnchorStore store)
{
    this.store = store;
}
```

<span data-ttu-id="acb61-133">È ora disponibile un riferimento a WorldAnchorStore, che verrà usato per salvare e caricare specifici ancoraggi internazionali.</span><span class="sxs-lookup"><span data-stu-id="acb61-133">We now have a reference to the WorldAnchorStore, which we'll use to save and load specific World Anchors.</span></span>

### <a name="saving-a-worldanchor"></a><span data-ttu-id="acb61-134">Salvataggio di un WorldAnchor</span><span class="sxs-lookup"><span data-stu-id="acb61-134">Saving a WorldAnchor</span></span>

<span data-ttu-id="acb61-135">Per salvare, è sufficiente assegnare un nome a quello che si sta salvando e passarlo nel WorldAnchor ottenuto in precedenza quando si desidera salvare.</span><span class="sxs-lookup"><span data-stu-id="acb61-135">To save, we simply need to name what we are saving and pass it in the WorldAnchor we got before when we want to save.</span></span> <span data-ttu-id="acb61-136">Nota: il tentativo di salvare due ancoraggi nella stessa stringa avrà esito negativo (Store. Il salvataggio restituirà false.</span><span class="sxs-lookup"><span data-stu-id="acb61-136">Note: trying to save two anchors to the same string will fail (store.Save will return false).</span></span> <span data-ttu-id="acb61-137">Eliminare il salvataggio precedente prima di salvare quello nuovo:</span><span class="sxs-lookup"><span data-stu-id="acb61-137">Delete the previous save before saving the new one:</span></span>

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

### <a name="loading-a-worldanchor"></a><span data-ttu-id="acb61-138">Caricamento di un WorldAnchor</span><span class="sxs-lookup"><span data-stu-id="acb61-138">Loading a WorldAnchor</span></span>

<span data-ttu-id="acb61-139">E per caricare:</span><span class="sxs-lookup"><span data-stu-id="acb61-139">And to load:</span></span>

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

<span data-ttu-id="acb61-140">È inoltre possibile utilizzare Store. Eliminare () per rimuovere un ancoraggio precedentemente salvato e archiviato. Deselezionare () per rimuovere tutti i dati salvati in precedenza.</span><span class="sxs-lookup"><span data-stu-id="acb61-140">We additionally can use store.Delete() to remove an anchor we previously saved and store.Clear() to remove all previously saved data.</span></span>

### <a name="enumerating-existing-anchors"></a><span data-ttu-id="acb61-141">Enumerazione degli ancoraggi esistenti</span><span class="sxs-lookup"><span data-stu-id="acb61-141">Enumerating Existing Anchors</span></span>

<span data-ttu-id="acb61-142">Per individuare gli ancoraggi precedentemente archiviati, chiamare GetAllIds.</span><span class="sxs-lookup"><span data-stu-id="acb61-142">To discover previously stored anchors, call GetAllIds.</span></span>

```cs
string[] ids = this.store.GetAllIds();
for (int index = 0; index < ids.Length; index++)
{
    Debug.Log(ids[index]);
}
```

## <a name="building-a-world-scale-experience"></a><span data-ttu-id="acb61-143">Creazione di un'esperienza su scala globale</span><span class="sxs-lookup"><span data-stu-id="acb61-143">Building a world-scale experience</span></span>

<span data-ttu-id="acb61-144">**Spazio dei nomi:** *UnityEngine. XR. WSA*</span><span class="sxs-lookup"><span data-stu-id="acb61-144">**Namespace:** *UnityEngine.XR.WSA*</span></span><br>
<span data-ttu-id="acb61-145">**Tipo:** *WorldAnchor*</span><span class="sxs-lookup"><span data-stu-id="acb61-145">**Type:** *WorldAnchor*</span></span>

<span data-ttu-id="acb61-146">Per esperienze reali su **scala mondiale** su HoloLens che consentono agli utenti di superare i 5 metri, sono necessarie nuove tecniche oltre a quelle usate per le esperienze su scala.</span><span class="sxs-lookup"><span data-stu-id="acb61-146">For true **world-scale experiences** on HoloLens that let users wander beyond 5 meters, you'll need new techniques beyond those used for room-scale experiences.</span></span> <span data-ttu-id="acb61-147">Una tecnica chiave da usare consiste nel creare un [ancoraggio spaziale](../../../design/coordinate-systems.md#spatial-anchors) per bloccare un cluster di ologrammi con precisione sul posto nel mondo fisico, indipendentemente dalla distanza di roaming dell'utente e quindi [ritrovare gli ologrammi nelle sessioni successive](../../../design/coordinate-systems.md#spatial-anchor-persistence).</span><span class="sxs-lookup"><span data-stu-id="acb61-147">One key technique you'll use is to create a [spatial anchor](../../../design/coordinate-systems.md#spatial-anchors) to lock a cluster of holograms precisely in place in the physical world, no matter how far the user has roamed, and then [find those holograms again in later sessions](../../../design/coordinate-systems.md#spatial-anchor-persistence).</span></span>

<span data-ttu-id="acb61-148">In Unity si crea un ancoraggio spaziale aggiungendo il componente **WorldAnchor** Unity a un GameObject.</span><span class="sxs-lookup"><span data-stu-id="acb61-148">In Unity, you create a spatial anchor by adding the **WorldAnchor** Unity component to a GameObject.</span></span>

### <a name="adding-a-world-anchor"></a><span data-ttu-id="acb61-149">Aggiunta di un ancoraggio globale</span><span class="sxs-lookup"><span data-stu-id="acb61-149">Adding a World Anchor</span></span>

<span data-ttu-id="acb61-150">Per aggiungere un ancoraggio globale, chiamare `AddComponent<WorldAnchor>()` sull'oggetto gioco con la trasformazione che si vuole ancorare nel mondo reale.</span><span class="sxs-lookup"><span data-stu-id="acb61-150">To add a world anchor, call `AddComponent<WorldAnchor>()` on the game object with the transform you want to anchor in the real world.</span></span>

```cs
WorldAnchor anchor = gameObject.AddComponent<WorldAnchor>();
```

<span data-ttu-id="acb61-151">Questo è tutto.</span><span class="sxs-lookup"><span data-stu-id="acb61-151">That's it!</span></span> <span data-ttu-id="acb61-152">Questo oggetto Game verrà ora ancorato alla posizione corrente nel mondo fisico. è possibile che le coordinate internazionali del mondo Unity vengano modificate leggermente nel tempo per garantire l'allineamento fisico.</span><span class="sxs-lookup"><span data-stu-id="acb61-152">This game object will now be anchored to its current location in the physical world - you may see its Unity world coordinates adjust slightly over time to ensure that physical alignment.</span></span> <span data-ttu-id="acb61-153">Per trovare nuovamente questa posizione ancorata in una sessione di app futura, vedere [caricamento di un ancoraggio globale](#loading-a-worldanchor) .</span><span class="sxs-lookup"><span data-stu-id="acb61-153">Refer to [loading a world anchor](#loading-a-worldanchor) to find this anchored location again in a future app session.</span></span>

### <a name="removing-a-world-anchor"></a><span data-ttu-id="acb61-154">Rimozione di un ancoraggio globale</span><span class="sxs-lookup"><span data-stu-id="acb61-154">Removing a World Anchor</span></span>

<span data-ttu-id="acb61-155">Se non si vuole più che il GameObject sia bloccato in una posizione fisica del mondo e non si intende trasferirlo in questo frame, è possibile chiamare semplicemente Destroy nel componente World Anchor.</span><span class="sxs-lookup"><span data-stu-id="acb61-155">If you no longer want the GameObject locked to a physical world location and don't intend on moving it this frame, then you can just call Destroy on the World Anchor component.</span></span>

```cs
Destroy(gameObject.GetComponent<WorldAnchor>());
```

<span data-ttu-id="acb61-156">Se si vuole spostare il GameObject in questo frame, è necessario chiamare DestroyImmediate.</span><span class="sxs-lookup"><span data-stu-id="acb61-156">If you want to move the GameObject this frame, you need to call DestroyImmediate instead.</span></span>

```cs
DestroyImmediate(gameObject.GetComponent<WorldAnchor>());
```

### <a name="moving-a-world-anchored-gameobject"></a><span data-ttu-id="acb61-157">Trasferimento di una GameObject ancorata globale</span><span class="sxs-lookup"><span data-stu-id="acb61-157">Moving a World Anchored GameObject</span></span>

<span data-ttu-id="acb61-158">Non è possibile spostare GameObject mentre è presente un ancoraggio globale.</span><span class="sxs-lookup"><span data-stu-id="acb61-158">GameObject's cannot be moved while a World Anchor is on it.</span></span> <span data-ttu-id="acb61-159">Se è necessario spostare il GameObject di questo frame, è necessario:</span><span class="sxs-lookup"><span data-stu-id="acb61-159">If you need to move the GameObject this frame, you need to:</span></span>

1. <span data-ttu-id="acb61-160">DestroyImmediate il componente di ancoraggio globale</span><span class="sxs-lookup"><span data-stu-id="acb61-160">DestroyImmediate the World Anchor component</span></span>
2. <span data-ttu-id="acb61-161">Spostare il GameObject</span><span class="sxs-lookup"><span data-stu-id="acb61-161">Move the GameObject</span></span>
3. <span data-ttu-id="acb61-162">Aggiungere un nuovo componente di ancoraggio globale a GameObject.</span><span class="sxs-lookup"><span data-stu-id="acb61-162">Add a new World Anchor component to the GameObject.</span></span>

```cs
DestroyImmediate(gameObject.GetComponent<WorldAnchor>());
gameObject.transform.position = new Vector3(0, 0, 2);
WorldAnchor anchor = gameObject.AddComponent<WorldAnchor>();
```

### <a name="handling-locatability-changes"></a><span data-ttu-id="acb61-163">Gestione delle modifiche apportate a Locatability</span><span class="sxs-lookup"><span data-stu-id="acb61-163">Handling Locatability Changes</span></span>

<span data-ttu-id="acb61-164">Un WorldAnchor non può essere locatable nel mondo fisico in un determinato momento.</span><span class="sxs-lookup"><span data-stu-id="acb61-164">A WorldAnchor may not be locatable in the physical world at a point in time.</span></span> <span data-ttu-id="acb61-165">In tal caso, Unity non aggiornerà la trasformazione dell'oggetto ancorato.</span><span class="sxs-lookup"><span data-stu-id="acb61-165">If that occurs, Unity won't be updating the transform of the anchored object.</span></span> <span data-ttu-id="acb61-166">Questo può cambiare anche durante l'esecuzione di un'app.</span><span class="sxs-lookup"><span data-stu-id="acb61-166">This also can change while an app is running.</span></span> <span data-ttu-id="acb61-167">Se non si gestisce la modifica in locatability, l'oggetto non verrà visualizzato nella posizione fisica corretta del mondo.</span><span class="sxs-lookup"><span data-stu-id="acb61-167">Failure to handle the change in locatability will cause the object to not appear in the correct physical location in the world.</span></span>

<span data-ttu-id="acb61-168">Per ricevere notifiche sulle modifiche apportate a locatability:</span><span class="sxs-lookup"><span data-stu-id="acb61-168">To be notified about locatability changes:</span></span>

1. <span data-ttu-id="acb61-169">Sottoscrivere l'evento OnTrackingChanged</span><span class="sxs-lookup"><span data-stu-id="acb61-169">Subscribe to the OnTrackingChanged event</span></span>
2. <span data-ttu-id="acb61-170">Gestisci evento</span><span class="sxs-lookup"><span data-stu-id="acb61-170">Handle the event</span></span>

<span data-ttu-id="acb61-171">L'evento **OnTrackingChanged** verrà chiamato ogni volta che l'ancoraggio spaziale sottostante viene modificato tra uno stato di locatable e non locatable.</span><span class="sxs-lookup"><span data-stu-id="acb61-171">The **OnTrackingChanged** event will be called whenever the underlying spatial anchor changes between a state of being locatable vs. not being locatable.</span></span>

```cs
anchor.OnTrackingChanged += Anchor_OnTrackingChanged;
```

<span data-ttu-id="acb61-172">Gestire quindi l'evento:</span><span class="sxs-lookup"><span data-stu-id="acb61-172">Then handle the event:</span></span>

```cs
private void Anchor_OnTrackingChanged(WorldAnchor self, bool located)
{
    // This simply activates/deactivates this object and all children when tracking changes
    self.gameObject.SetActiveRecursively(located);
}
```

<span data-ttu-id="acb61-173">Talvolta gli ancoraggi si trovano immediatamente.</span><span class="sxs-lookup"><span data-stu-id="acb61-173">Sometimes anchors are located immediately.</span></span> <span data-ttu-id="acb61-174">In questo caso, la proprietà individuata dell'ancoraggio verrà impostata su true quando AddComponent <WorldAnchor> () restituisce.</span><span class="sxs-lookup"><span data-stu-id="acb61-174">In this case, this isLocated property of the anchor will be set to true when AddComponent<WorldAnchor>() returns.</span></span> <span data-ttu-id="acb61-175">Di conseguenza, l'evento OnTrackingChanged non verrà attivato.</span><span class="sxs-lookup"><span data-stu-id="acb61-175">As a result, the OnTrackingChanged event won't be triggered.</span></span> <span data-ttu-id="acb61-176">Un modello pulito consiste nel chiamare il gestore OnTrackingChanged con lo stato individuato iniziale dopo aver collegato un ancoraggio.</span><span class="sxs-lookup"><span data-stu-id="acb61-176">A clean pattern would be to call your OnTrackingChanged handler with the initial IsLocated state after attaching an anchor.</span></span>

```cs
Anchor_OnTrackingChanged(anchor, anchor.isLocated);
```

## <a name="persisting-holograms-for-multiple-devices"></a><span data-ttu-id="acb61-177">Mantenimento degli ologrammi per più dispositivi</span><span class="sxs-lookup"><span data-stu-id="acb61-177">Persisting holograms for multiple devices</span></span>

<span data-ttu-id="acb61-178">È possibile usare gli <a href="/azure/spatial-anchors/overview" target="_blank">ancoraggi spaziali di Azure</a> per creare un ancoraggio cloud durevole da un WorldAnchor locale, che può essere individuato dall'app su più dispositivi HoloLens, iOS e Android, anche se questi dispositivi non sono presenti contemporaneamente.</span><span class="sxs-lookup"><span data-stu-id="acb61-178">You can use <a href="/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> to create a durable cloud anchor from a local WorldAnchor, which your app can then locate across multiple HoloLens, iOS and Android devices, even if those devices aren't present together at the same time.</span></span>  <span data-ttu-id="acb61-179">Poiché gli ancoraggi cloud sono persistenti, più dispositivi nel tempo possono visualizzare il contenuto di cui è stato eseguito il rendering rispetto a tale ancoraggio nella stessa posizione fisica.</span><span class="sxs-lookup"><span data-stu-id="acb61-179">Because cloud anchors are persistent, multiple devices over time can each see content rendered relative to that anchor in the same physical location.</span></span>

<span data-ttu-id="acb61-180">Per iniziare a creare esperienze condivise in Unity, provare le <a href="/azure/spatial-anchors/unity-overview" target="_blank">guide introduttive Unity Anchors di Azure</a>di 5 minuti.</span><span class="sxs-lookup"><span data-stu-id="acb61-180">To get started building shared experiences in Unity, try out the 5-minute <a href="/azure/spatial-anchors/unity-overview" target="_blank">Azure Spatial Anchors Unity quickstarts</a>.</span></span>

<span data-ttu-id="acb61-181">Quando si è operativi con i Anchor spaziali di Azure, è possibile <a href="/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">creare e individuare ancoraggi in Unity</a>.</span><span class="sxs-lookup"><span data-stu-id="acb61-181">Once you're up and running with Azure Spatial Anchors, you can then <a href="/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">create and locate anchors in Unity</a>.</span></span>

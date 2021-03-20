---
ms.openlocfilehash: bb2df8c85dd05981c1438bdb076b0aad16c7efd7
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2021
ms.locfileid: "104719628"
---
# <a name="unity-2020--openxr"></a>[<span data-ttu-id="f5559-101">Unity 2020 + OpenXR</span><span class="sxs-lookup"><span data-stu-id="f5559-101">Unity 2020 + OpenXR</span></span>](#tab/openxr)

<span data-ttu-id="f5559-102">Un'API aggiuntiva denominata **XRAnchorStore** consente di salvare in modo permanente gli ancoraggi tra le sessioni.</span><span class="sxs-lookup"><span data-stu-id="f5559-102">An additional API called the **XRAnchorStore** enables anchors to be persisted between sessions.</span></span> <span data-ttu-id="f5559-103">XRAnchorStore è una rappresentazione degli ancoraggi salvati in un dispositivo.</span><span class="sxs-lookup"><span data-stu-id="f5559-103">The XRAnchorStore is a representation of the saved anchors on a device.</span></span> <span data-ttu-id="f5559-104">Gli ancoraggi possono essere salvati in permanenza da **ARAnchors** nella scena Unity, caricati dall'archiviazione in nuovi **ARAnchors** o eliminati dall'archivio.</span><span class="sxs-lookup"><span data-stu-id="f5559-104">Anchors can be persisted from **ARAnchors** in the Unity scene, loaded from storage into new **ARAnchors**, or deleted from storage.</span></span>

> [!NOTE]
> <span data-ttu-id="f5559-105">Questi ancoraggi devono essere salvati e caricati nello stesso dispositivo.</span><span class="sxs-lookup"><span data-stu-id="f5559-105">These anchors are to be saved and loaded on the same device.</span></span> <span data-ttu-id="f5559-106">L'archiviazione di ancoraggio tra dispositivi verrà supportata tramite ancoraggi spaziali di Azure in una versione futura.</span><span class="sxs-lookup"><span data-stu-id="f5559-106">Cross-device anchor storage will be supported through Azure Spatial Anchors in a future release.</span></span>

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

<span data-ttu-id="f5559-107">Per caricare XRAnchorStore, il plug-in fornisce un metodo di estensione in XRAnchorSubsystem, il sottosistema di un ARAnchorManager:</span><span class="sxs-lookup"><span data-stu-id="f5559-107">To load the XRAnchorStore, the plugin provides an extension method on the XRAnchorSubsystem, the subsystem of an ARAnchorManager:</span></span>

``` cs
public static Task<XRAnchorStore> LoadAnchorStoreAsync(this XRAnchorSubsystem anchorSubsystem)
```

<span data-ttu-id="f5559-108">Per usare questo metodo di estensione, accedervi dal sottosistema di ARAnchorManager come indicato di seguito:</span><span class="sxs-lookup"><span data-stu-id="f5559-108">To use this extension method, access it from an ARAnchorManager's subsystem as follows:</span></span>

``` cs
ARAnchorManager arAnchorManager = GetComponent<ARAnchorManager>();
XRAnchorStore anchorStore = await arAnchorManager.subsystem.LoadAnchorStoreAsync();
```

<span data-ttu-id="f5559-109">Per un esempio completo di come salvare in modo permanente/non permanente gli ancoraggi, vedere l'esempio ancoraggi-> ancoraggi di esempio GameObject e AnchorsSample. cs nella scena di [esempio di plug-in realtà mista OpenXR](../openxr-getting-started.md#hololens-2-samples):</span><span class="sxs-lookup"><span data-stu-id="f5559-109">To see a full example of persisting / unpersisting anchors, check out the Anchors -> Anchors Sample GameObject and AnchorsSample.cs script in the [Mixed Reality OpenXR Plugin Sample Scene](../openxr-getting-started.md#hololens-2-samples):</span></span>

![Screenshot del pannello gerarchia aperto nell'editor di Unity con l'esempio Anchors evidenziato](../images/openxr-features-img-04.png)

![Screenshot del pannello Inspector aperto nell'editor di Unity con lo script di esempio Anchors evidenziato](../images/openxr-features-img-05.png)

# <a name="unity-20192020--windows-xr-plugin"></a>[<span data-ttu-id="f5559-112">Plug-in Unity 2019/2020 + Windows XR</span><span class="sxs-lookup"><span data-stu-id="f5559-112">Unity 2019/2020 + Windows XR Plugin</span></span>](#tab/winxr)

<span data-ttu-id="f5559-113">Un'API denominata **XRAnchorStore** consente di salvare in modo permanente gli ancoraggi tra le sessioni.</span><span class="sxs-lookup"><span data-stu-id="f5559-113">An API called the **XRAnchorStore** enables anchors to be persisted between sessions.</span></span> <span data-ttu-id="f5559-114">XRAnchorStore è una rappresentazione degli ancoraggi salvati in un dispositivo.</span><span class="sxs-lookup"><span data-stu-id="f5559-114">The XRAnchorStore is a representation of the saved anchors on a device.</span></span> <span data-ttu-id="f5559-115">Gli ancoraggi possono essere salvati in permanenza da **ARAnchors** nella scena Unity, caricati dall'archiviazione in nuovi **ARAnchors** o eliminati dall'archivio.</span><span class="sxs-lookup"><span data-stu-id="f5559-115">Anchors can be persisted from **ARAnchors** in the Unity scene, loaded from storage into new **ARAnchors**, or deleted from storage.</span></span>

> [!NOTE]
> <span data-ttu-id="f5559-116">Questi ancoraggi devono essere salvati e caricati nello stesso dispositivo.</span><span class="sxs-lookup"><span data-stu-id="f5559-116">These anchors are to be saved and loaded on the same device.</span></span> <span data-ttu-id="f5559-117">L'archiviazione di ancoraggio tra dispositivi verrà supportata tramite ancoraggi spaziali di Azure in una versione futura.</span><span class="sxs-lookup"><span data-stu-id="f5559-117">Cross-device anchor storage will be supported through Azure Spatial Anchors in a future release.</span></span>

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

<span data-ttu-id="f5559-118">Per caricare il XRAnchorStore, il plug-in fornisce un metodo di estensione in XRReferencePointSubsystem (Unity 2019) o XRAnchorSubsystem (Unity 2020), il sottosistema di un ARReferencePointManager/ARAnchorManager:</span><span class="sxs-lookup"><span data-stu-id="f5559-118">To load the XRAnchorStore, the plugin provides an extension method on the XRReferencePointSubsystem (Unity 2019) or XRAnchorSubsystem (Unity 2020), the subsystem of an ARReferencePointManager/ARAnchorManager:</span></span>

``` cs
public static Task<XRAnchorStore> TryGetAnchorStoreAsync(this XRReferencePointSubsystem anchorSubsystem); // Unity 2019
public static Task<XRAnchorStore> TryGetAnchorStoreAsync(this XRAnchorSubsystem anchorSubsystem); // Unity 2020
```

<span data-ttu-id="f5559-119">Per usare questo metodo di estensione, accedervi dal sottosistema di ARAnchorManager come indicato di seguito per Unity 2019:</span><span class="sxs-lookup"><span data-stu-id="f5559-119">To use this extension method, access it from an ARAnchorManager's subsystem as follows for Unity 2019:</span></span>

``` cs
ARReferencePointManager arReferencePointManager = GetComponent<ARReferencePointManager>();
XRAnchorStore anchorStore = await arReferencePointManager.subsystem.TryGetAnchorStoreAsync();
```

<span data-ttu-id="f5559-120">oppure per Unity 2020:</span><span class="sxs-lookup"><span data-stu-id="f5559-120">or for Unity 2020:</span></span>

``` cs
ARAnchorManager arAnchorManager = GetComponent<ARAnchorManager>();
XRAnchorStore anchorStore = await arAnchorManager.subsystem.TryGetAnchorStoreAsync();
```

# <a name="legacy-wsa"></a>[<span data-ttu-id="f5559-121">WSA legacy</span><span class="sxs-lookup"><span data-stu-id="f5559-121">Legacy WSA</span></span>](#tab/wsa)

<span data-ttu-id="f5559-122">**WorldAnchorStore** è la chiave per la creazione di esperienze olografiche in cui gli ologrammi mantengono posizioni reali specifiche tra le istanze dell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="f5559-122">The **WorldAnchorStore** is the key to creating holographic experiences where holograms stay in specific real world positions across instances of the application.</span></span> <span data-ttu-id="f5559-123">Gli utenti possono quindi aggiungere singoli ologrammi ovunque si trovino e trovarli più avanti nello stesso punto rispetto a molti utilizzi dell'app.</span><span class="sxs-lookup"><span data-stu-id="f5559-123">Users can then pin individual holograms wherever they want, and find them later in the same spot over many uses of your app.</span></span>

<span data-ttu-id="f5559-124">**Spazio dei nomi:** *UnityEngine. XR. WSA. Persistence*</span><span class="sxs-lookup"><span data-stu-id="f5559-124">**Namespace:** *UnityEngine.XR.WSA.Persistence*</span></span><br>
<span data-ttu-id="f5559-125">**Classe:** *WorldAnchorStore*</span><span class="sxs-lookup"><span data-stu-id="f5559-125">**Class:** *WorldAnchorStore*</span></span>

<span data-ttu-id="f5559-126">Il WorldAnchorStore consentirà di rendere permanente il percorso di WorldAnchor tra le sessioni.</span><span class="sxs-lookup"><span data-stu-id="f5559-126">The WorldAnchorStore will allow you to persist the location of WorldAnchor's across sessions.</span></span> <span data-ttu-id="f5559-127">Per rendere effettivamente permanente gli ologrammi tra le sessioni, è necessario tenere traccia separatamente dei GameObject che usano un particolare ancoraggio mondiale.</span><span class="sxs-lookup"><span data-stu-id="f5559-127">To actually persist holograms across sessions, you'll need to separately keep track of your GameObjects that use a particular world anchor.</span></span> <span data-ttu-id="f5559-128">Spesso è opportuno creare una radice GameObject con un ancoraggio globale e avere elementi figlio olografici ancorati con un offset della posizione locale.</span><span class="sxs-lookup"><span data-stu-id="f5559-128">It often makes sense to create a GameObject root with a world anchor and have children holograms anchored by it with a local position offset.</span></span>

<span data-ttu-id="f5559-129">Per caricare gli ologrammi dalle sessioni precedenti:</span><span class="sxs-lookup"><span data-stu-id="f5559-129">To load holograms from previous sessions:</span></span>

1. <span data-ttu-id="f5559-130">Ottenere il WorldAnchorStore</span><span class="sxs-lookup"><span data-stu-id="f5559-130">Get the WorldAnchorStore</span></span>
2. <span data-ttu-id="f5559-131">Caricare i dati dell'app correlati all'ancoraggio globale, che fornisce l'ID dell'ancoraggio globale</span><span class="sxs-lookup"><span data-stu-id="f5559-131">Load app data relating to the world anchor, which gives you the ID of the world anchor</span></span>
3. <span data-ttu-id="f5559-132">Caricare un ancoraggio globale dall'ID</span><span class="sxs-lookup"><span data-stu-id="f5559-132">Load a world anchor from its ID</span></span>

<span data-ttu-id="f5559-133">Per salvare gli ologrammi per le sessioni future:</span><span class="sxs-lookup"><span data-stu-id="f5559-133">To save holograms for future sessions:</span></span>

1. <span data-ttu-id="f5559-134">Ottenere il WorldAnchorStore</span><span class="sxs-lookup"><span data-stu-id="f5559-134">Get the WorldAnchorStore</span></span>
2. <span data-ttu-id="f5559-135">Salva un ancoraggio globale specificando un ID</span><span class="sxs-lookup"><span data-stu-id="f5559-135">Save a world anchor specifying an ID</span></span>
3. <span data-ttu-id="f5559-136">Salva i dati dell'app correlati all'ancoraggio globale insieme a un ID</span><span class="sxs-lookup"><span data-stu-id="f5559-136">Save app data relating to the world anchor along with an ID</span></span>

### <a name="getting-the-worldanchorstore"></a><span data-ttu-id="f5559-137">Recupero di WorldAnchorStore</span><span class="sxs-lookup"><span data-stu-id="f5559-137">Getting the WorldAnchorStore</span></span>

<span data-ttu-id="f5559-138">È consigliabile tenere un riferimento a WorldAnchorStore in modo da essere a conoscenza quando è pronto per eseguire un'operazione.</span><span class="sxs-lookup"><span data-stu-id="f5559-138">You'll want to keep a reference to the WorldAnchorStore so you know when it's ready to perform an operation.</span></span> <span data-ttu-id="f5559-139">Poiché si tratta di una chiamata asincrona, potenzialmente non appena viene avviata, si vuole chiamare:</span><span class="sxs-lookup"><span data-stu-id="f5559-139">Since this is an async call, potentially as soon as start up, you want to call:</span></span>

```cs
WorldAnchorStore.GetAsync(StoreLoaded);
```

<span data-ttu-id="f5559-140">StoreLoaded in questo caso è il gestore per il completamento del caricamento di WorldAnchorStore:</span><span class="sxs-lookup"><span data-stu-id="f5559-140">StoreLoaded in this case is our handler for when the WorldAnchorStore has completed loading:</span></span>

```cs
private void StoreLoaded(WorldAnchorStore store)
{
    this.store = store;
}
```

<span data-ttu-id="f5559-141">È ora disponibile un riferimento a WorldAnchorStore, che verrà usato per salvare e caricare specifici ancoraggi internazionali.</span><span class="sxs-lookup"><span data-stu-id="f5559-141">We now have a reference to the WorldAnchorStore, which we'll use to save and load specific World Anchors.</span></span>

### <a name="saving-a-worldanchor"></a><span data-ttu-id="f5559-142">Salvataggio di un WorldAnchor</span><span class="sxs-lookup"><span data-stu-id="f5559-142">Saving a WorldAnchor</span></span>

<span data-ttu-id="f5559-143">Per salvare, è sufficiente assegnare un nome a quello che si sta salvando e passarlo nel WorldAnchor ottenuto in precedenza quando si desidera salvare.</span><span class="sxs-lookup"><span data-stu-id="f5559-143">To save, we simply need to name what we are saving and pass it in the WorldAnchor we got before when we want to save.</span></span> <span data-ttu-id="f5559-144">Nota: il tentativo di salvare due ancoraggi nella stessa stringa avrà esito negativo (Store. Il salvataggio restituirà false.</span><span class="sxs-lookup"><span data-stu-id="f5559-144">Note: trying to save two anchors to the same string will fail (store.Save will return false).</span></span> <span data-ttu-id="f5559-145">Eliminare il salvataggio precedente prima di salvare quello nuovo:</span><span class="sxs-lookup"><span data-stu-id="f5559-145">Delete the previous save before saving the new one:</span></span>

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

### <a name="loading-a-worldanchor"></a><span data-ttu-id="f5559-146">Caricamento di un WorldAnchor</span><span class="sxs-lookup"><span data-stu-id="f5559-146">Loading a WorldAnchor</span></span>

<span data-ttu-id="f5559-147">E per caricare:</span><span class="sxs-lookup"><span data-stu-id="f5559-147">And to load:</span></span>

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

<span data-ttu-id="f5559-148">È inoltre possibile utilizzare Store. Eliminare () per rimuovere un ancoraggio precedentemente salvato e archiviato. Deselezionare () per rimuovere tutti i dati salvati in precedenza.</span><span class="sxs-lookup"><span data-stu-id="f5559-148">We additionally can use store.Delete() to remove an anchor we previously saved and store.Clear() to remove all previously saved data.</span></span>

### <a name="enumerating-existing-anchors"></a><span data-ttu-id="f5559-149">Enumerazione degli ancoraggi esistenti</span><span class="sxs-lookup"><span data-stu-id="f5559-149">Enumerating Existing Anchors</span></span>

<span data-ttu-id="f5559-150">Per individuare gli ancoraggi precedentemente archiviati, chiamare GetAllIds.</span><span class="sxs-lookup"><span data-stu-id="f5559-150">To discover previously stored anchors, call GetAllIds.</span></span>

```cs
string[] ids = this.store.GetAllIds();
for (int index = 0; index < ids.Length; index++)
{
    Debug.Log(ids[index]);
}
```

## <a name="persisting-holograms-for-multiple-devices"></a><span data-ttu-id="f5559-151">Mantenimento degli ologrammi per più dispositivi</span><span class="sxs-lookup"><span data-stu-id="f5559-151">Persisting holograms for multiple devices</span></span>

<span data-ttu-id="f5559-152">È possibile usare gli <a href="/azure/spatial-anchors/overview" target="_blank">ancoraggi spaziali di Azure</a> per creare un ancoraggio cloud durevole da un WorldAnchor locale, che può essere individuato dall'app su più dispositivi HoloLens, iOS e Android, anche se questi dispositivi non sono presenti contemporaneamente.</span><span class="sxs-lookup"><span data-stu-id="f5559-152">You can use <a href="/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> to create a durable cloud anchor from a local WorldAnchor, which your app can then locate across multiple HoloLens, iOS and Android devices, even if those devices aren't present together at the same time.</span></span>  <span data-ttu-id="f5559-153">Poiché gli ancoraggi cloud sono persistenti, più dispositivi nel tempo possono visualizzare il contenuto di cui è stato eseguito il rendering rispetto a tale ancoraggio nella stessa posizione fisica.</span><span class="sxs-lookup"><span data-stu-id="f5559-153">Because cloud anchors are persistent, multiple devices over time can each see content rendered relative to that anchor in the same physical location.</span></span>

<span data-ttu-id="f5559-154">Per iniziare a creare esperienze condivise in Unity, provare le <a href="/azure/spatial-anchors/unity-overview" target="_blank">guide introduttive Unity Anchors di Azure</a>di 5 minuti.</span><span class="sxs-lookup"><span data-stu-id="f5559-154">To get started building shared experiences in Unity, try out the 5-minute <a href="/azure/spatial-anchors/unity-overview" target="_blank">Azure Spatial Anchors Unity quickstarts</a>.</span></span>

<span data-ttu-id="f5559-155">Quando si è operativi con i Anchor spaziali di Azure, è possibile <a href="/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">creare e individuare ancoraggi in Unity</a>.</span><span class="sxs-lookup"><span data-stu-id="f5559-155">Once you're up and running with Azure Spatial Anchors, you can then <a href="/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">create and locate anchors in Unity</a>.</span></span>

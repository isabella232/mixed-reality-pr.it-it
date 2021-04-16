---
ms.openlocfilehash: 25e42ba872764a98d4cb966b5a4922cc1dea0dc9
ms.sourcegitcommit: 3e36b2fbbcc250c49aaf8ca1b6133cf0e9db69fa
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2021
ms.locfileid: "107528818"
---
# <a name="world-locking-tools-recommended"></a>[<span data-ttu-id="8d297-101">Strumenti di blocco del mondo (scelta consigliata)</span><span class="sxs-lookup"><span data-stu-id="8d297-101">World Locking Tools (Recommended)</span></span>](#tab/wlt)

<span data-ttu-id="8d297-102">Per impostazione predefinita, World Locking Tools ripristina il sistema di coordinate di Unity rispetto al mondo fisico tra le sessioni.</span><span class="sxs-lookup"><span data-stu-id="8d297-102">By default, World Locking Tools will restore Unity's coordinate system relative to the physical world across sessions.</span></span> <span data-ttu-id="8d297-103">Ciò significa che per fare in modo che un ologramma venga visualizzato nello stesso posto nel mondo fisico dopo la chiusura e la ri-esecuzione dell'applicazione, l'ologramma deve avere di nuovo la stessa posizione.</span><span class="sxs-lookup"><span data-stu-id="8d297-103">This means that to have a hologram appear the same place in the physical world after quitting and re-running the application, the hologram only needs to have the same Pose again.</span></span>

![Componente del contesto di blocco del mondo nel controllo Unity](../../images/world-locking-tools-img-02.png)

<span data-ttu-id="8d297-105">Se l'applicazione richiede un controllo  più **fine,** il salvataggio automatico e il caricamento automatico possono essere disabilitati nel controllo e la persistenza gestita da uno script, come descritto nella sezione relativa alla persistenza [della documentazione](https://microsoft.github.io/MixedReality-WorldLockingTools-Unity/DocGen/Documentation/Concepts/Advanced/Persistence.html).</span><span class="sxs-lookup"><span data-stu-id="8d297-105">If the application needs finer control, **Auto-Save** and **Auto-Load** may be disabled in the inspector, and persistence managed from a script as described in the [persistence section of the documentation](https://microsoft.github.io/MixedReality-WorldLockingTools-Unity/DocGen/Documentation/Concepts/Advanced/Persistence.html).</span></span>

# <a name="aranchormanager"></a>[<span data-ttu-id="8d297-106">ARAnchorManager</span><span class="sxs-lookup"><span data-stu-id="8d297-106">ARAnchorManager</span></span>](#tab/anchorstore)

<span data-ttu-id="8d297-107">Un'API aggiuntiva denominata **XRAnchorStore consente** di rendere persistenti gli ancoraggi tra le sessioni.</span><span class="sxs-lookup"><span data-stu-id="8d297-107">An additional API called the **XRAnchorStore** enables anchors to be persisted between sessions.</span></span> <span data-ttu-id="8d297-108">XRAnchorStore è una rappresentazione degli ancoraggi salvati in un dispositivo.</span><span class="sxs-lookup"><span data-stu-id="8d297-108">The XRAnchorStore is a representation of the saved anchors on a device.</span></span> <span data-ttu-id="8d297-109">Gli ancoraggi possono essere resi persistenti dagli **ARAnchor** nella scena Unity, caricati dall'archiviazione in nuovi **ARAnchor** o eliminati dall'archiviazione.</span><span class="sxs-lookup"><span data-stu-id="8d297-109">Anchors can be persisted from **ARAnchors** in the Unity scene, loaded from storage into new **ARAnchors**, or deleted from storage.</span></span>

> [!NOTE]
> <span data-ttu-id="8d297-110">Questi ancoraggi devono essere salvati e caricati nello stesso dispositivo.</span><span class="sxs-lookup"><span data-stu-id="8d297-110">These anchors are to be saved and loaded on the same device.</span></span> <span data-ttu-id="8d297-111">L'archiviazione tra dispositivi di ancoraggio sarà supportata tramite Ancoraggi nello spazio di Azure in una versione futura.</span><span class="sxs-lookup"><span data-stu-id="8d297-111">Cross-device anchor storage will be supported through Azure Spatial Anchors in a future release.</span></span>

### <a name="namespaces"></a><span data-ttu-id="8d297-112">Spazi dei nomi</span><span class="sxs-lookup"><span data-stu-id="8d297-112">Namespaces</span></span>

<span data-ttu-id="8d297-113">Per **Unity 2020 e OpenXR:**</span><span class="sxs-lookup"><span data-stu-id="8d297-113">For **Unity 2020 and OpenXR**:</span></span> 

``` cs
using Microsoft.MixedReality.ARSubsystems.XRAnchorStore
```

<span data-ttu-id="8d297-114">o **Unity 2019/2020 + Plug-in XR di Windows:**</span><span class="sxs-lookup"><span data-stu-id="8d297-114">or **Unity 2019/2020 + Windows XR Plugin**:</span></span> 

```cs 
using UnityEngine.XR.WindowsMR.XRAnchorStore
```

### <a name="public-methods"></a><span data-ttu-id="8d297-115">Metodi pubblici</span><span class="sxs-lookup"><span data-stu-id="8d297-115">Public methods</span></span>

```cs 
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

### <a name="getting-an-anchor-store-reference"></a><span data-ttu-id="8d297-116">Recupero di un riferimento all'archivio di ancoraggio</span><span class="sxs-lookup"><span data-stu-id="8d297-116">Getting an anchor store reference</span></span> 

<span data-ttu-id="8d297-117">Per caricare XRAnchorStore con **Unity 2020 e OpenXR,** usare il metodo di estensione nel sottosistema XRAnchorSubsystem, il sottosistema di un ARAnchorManager:</span><span class="sxs-lookup"><span data-stu-id="8d297-117">To load the XRAnchorStore with **Unity 2020 and OpenXR**, use extension method on the XRAnchorSubsystem, the subsystem of an ARAnchorManager:</span></span>

``` cs
public static Task<XRAnchorStore> LoadAnchorStoreAsync(this XRAnchorSubsystem anchorSubsystem)
```

<span data-ttu-id="8d297-118">Per caricare XRAnchorStore con **Unity 2019/2020 e il plug-in Windows XR,** usare il metodo di estensione nel sistema XRReferencePointSubsystem (Unity 2019) o XRAnchorSubsystem (Unity 2020), il sottosistema di un ARReferencePointManager/ARAnchorManager:</span><span class="sxs-lookup"><span data-stu-id="8d297-118">To load the XRAnchorStore with **Unity 2019/2020 and the Windows XR Plugin**, use the extension method on the XRReferencePointSubsystem (Unity 2019) or XRAnchorSubsystem (Unity 2020), the subsystem of an ARReferencePointManager/ARAnchorManager:</span></span>

```cs
// Unity 2019 + Windows XR Plugin
public static Task<XRAnchorStore> TryGetAnchorStoreAsync(this XRReferencePointSubsystem anchorSubsystem);

// Unity 2020 + Windows XR Plugin
public static Task<XRAnchorStore> TryGetAnchorStoreAsync(this XRAnchorSubsystem anchorSubsystem);
```

### <a name="loading-an-anchor-store"></a><span data-ttu-id="8d297-119">Caricamento di un archivio di ancoraggio</span><span class="sxs-lookup"><span data-stu-id="8d297-119">Loading an anchor store</span></span>

<span data-ttu-id="8d297-120">Per caricare un archivio di ancoraggio in **Unity 2020 e OpenXR,** accedervi dal sottosistema aranchorManager come segue:</span><span class="sxs-lookup"><span data-stu-id="8d297-120">To load an anchor store in **Unity 2020 and OpenXR**, access it from an ARAnchorManager's subsystem as follows:</span></span>

``` cs
ARAnchorManager arAnchorManager = GetComponent<ARAnchorManager>();
XRAnchorStore anchorStore = await arAnchorManager.subsystem.LoadAnchorStoreAsync();
```

<span data-ttu-id="8d297-121">o con **Unity 2019/2020 e il plug-in Windows XR:**</span><span class="sxs-lookup"><span data-stu-id="8d297-121">or with **Unity 2019/2020 and the Windows XR Plugin**:</span></span>

``` cs
// Unity 2019
ARReferencePointManager arReferencePointManager = GetComponent<ARReferencePointManager>();
XRAnchorStore anchorStore = await arReferencePointManager.subsystem.TryGetAnchorStoreAsync();

// Unity 2020
ARAnchorManager arAnchorManager = GetComponent<ARAnchorManager>();
XRAnchorStore anchorStore = await arAnchorManager.subsystem.TryGetAnchorStoreAsync();
```

<span data-ttu-id="8d297-122">Per un esempio completo di ancoraggi persistenti/non persistenti, vedi lo script Anchors -> Anchors Sample GameObject e AnchorsSample.cs nella scena di esempio del plug-in [OpenXR](../../openxr-getting-started.md#hololens-2-samples)di Realtà mista:</span><span class="sxs-lookup"><span data-stu-id="8d297-122">To see a full example of persisting / unpersisting anchors, check out the Anchors -> Anchors Sample GameObject and AnchorsSample.cs script in the [Mixed Reality OpenXR Plugin Sample Scene](../../openxr-getting-started.md#hololens-2-samples):</span></span>

![Screenshot del pannello della gerarchia aperto nell'editor di Unity con l'esempio di ancoraggi evidenziato](../../images/openxr-features-img-04.png)

![Screenshot del pannello di controllo aperto nell'editor di Unity con lo script di esempio degli ancoraggi evidenziato](../../images/openxr-features-img-05.png)

# <a name="worldanchor"></a>[<span data-ttu-id="8d297-125">WorldAnchor</span><span class="sxs-lookup"><span data-stu-id="8d297-125">WorldAnchor</span></span>](#tab/worldanchor)

<span data-ttu-id="8d297-126">**WorldAnchorStore è** la chiave per creare esperienze olografiche in cui gli ologrammi rimangono in posizioni reali specifiche tra le istanze dell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="8d297-126">The **WorldAnchorStore** is the key to creating holographic experiences where holograms stay in specific real world positions across instances of the application.</span></span> <span data-ttu-id="8d297-127">Gli utenti possono quindi aggiungere singoli ologrammi dove vogliono e trovarli in un secondo momento nello stesso punto in molti usi dell'app.</span><span class="sxs-lookup"><span data-stu-id="8d297-127">Users can then pin individual holograms wherever they want, and find them later in the same spot over many uses of your app.</span></span>

<span data-ttu-id="8d297-128">**Spazio dei nomi:** *UnityEngine.XR.WSA.Persistence*</span><span class="sxs-lookup"><span data-stu-id="8d297-128">**Namespace:** *UnityEngine.XR.WSA.Persistence*</span></span><br>
<span data-ttu-id="8d297-129">**Classe:** *WorldAnchorStore*</span><span class="sxs-lookup"><span data-stu-id="8d297-129">**Class:** *WorldAnchorStore*</span></span>

<span data-ttu-id="8d297-130">WorldAnchorStore consente di rendere persistente la posizione di WorldAnchor tra le sessioni.</span><span class="sxs-lookup"><span data-stu-id="8d297-130">The WorldAnchorStore will allow you to persist the location of WorldAnchor's across sessions.</span></span> <span data-ttu-id="8d297-131">Per rendere effettivamente persistenti gli ologrammi tra le sessioni, dovrai tenere traccia separatamente dei GameObject che usano un ancoraggio mondo specifico.</span><span class="sxs-lookup"><span data-stu-id="8d297-131">To actually persist holograms across sessions, you'll need to separately keep track of your GameObjects that use a particular world anchor.</span></span> <span data-ttu-id="8d297-132">Spesso è opportuno creare una radice GameObject con un ancoraggio del mondo e fare in modo che gli ologrammi figlio vi ancoraggio con un offset di posizione locale.</span><span class="sxs-lookup"><span data-stu-id="8d297-132">It often makes sense to create a GameObject root with a world anchor and have children holograms anchored by it with a local position offset.</span></span>

<span data-ttu-id="8d297-133">Per caricare gli ologrammi dalle sessioni precedenti:</span><span class="sxs-lookup"><span data-stu-id="8d297-133">To load holograms from previous sessions:</span></span>

1. <span data-ttu-id="8d297-134">Ottenere WorldAnchorStore</span><span class="sxs-lookup"><span data-stu-id="8d297-134">Get the WorldAnchorStore</span></span>
2. <span data-ttu-id="8d297-135">Caricare i dati dell'app relativi all'ancoraggio del mondo, che fornisce l'ID dell'ancoraggio del mondo</span><span class="sxs-lookup"><span data-stu-id="8d297-135">Load app data relating to the world anchor, which gives you the ID of the world anchor</span></span>
3. <span data-ttu-id="8d297-136">Caricare un ancoraggio del mondo dal relativo ID</span><span class="sxs-lookup"><span data-stu-id="8d297-136">Load a world anchor from its ID</span></span>

<span data-ttu-id="8d297-137">Per salvare gli ologrammi per sessioni future:</span><span class="sxs-lookup"><span data-stu-id="8d297-137">To save holograms for future sessions:</span></span>

1. <span data-ttu-id="8d297-138">Ottenere WorldAnchorStore</span><span class="sxs-lookup"><span data-stu-id="8d297-138">Get the WorldAnchorStore</span></span>
2. <span data-ttu-id="8d297-139">Salvare un ancoraggio mondo specificando un ID</span><span class="sxs-lookup"><span data-stu-id="8d297-139">Save a world anchor specifying an ID</span></span>
3. <span data-ttu-id="8d297-140">Salvare i dati dell'app relativi all'ancoraggio del mondo insieme a un ID</span><span class="sxs-lookup"><span data-stu-id="8d297-140">Save app data relating to the world anchor along with an ID</span></span>

### <a name="getting-the-worldanchorstore"></a><span data-ttu-id="8d297-141">Recupero di WorldAnchorStore</span><span class="sxs-lookup"><span data-stu-id="8d297-141">Getting the WorldAnchorStore</span></span>

<span data-ttu-id="8d297-142">È necessario mantenere un riferimento a WorldAnchorStore per sapere quando è pronto per eseguire un'operazione.</span><span class="sxs-lookup"><span data-stu-id="8d297-142">You'll want to keep a reference to the WorldAnchorStore so you know when it's ready to perform an operation.</span></span> <span data-ttu-id="8d297-143">Poiché si tratta di una chiamata asincrona, potenzialmente non appena si avvia, si vuole chiamare:</span><span class="sxs-lookup"><span data-stu-id="8d297-143">Since this is an async call, potentially as soon as start up, you want to call:</span></span>

```cs
WorldAnchorStore.GetAsync(StoreLoaded);
```

<span data-ttu-id="8d297-144">StoreLoaded in questo caso è il gestore per quando WorldAnchorStore ha completato il caricamento:</span><span class="sxs-lookup"><span data-stu-id="8d297-144">StoreLoaded in this case is our handler for when the WorldAnchorStore has completed loading:</span></span>

```cs
private void StoreLoaded(WorldAnchorStore store)
{
    this.store = store;
}
```

<span data-ttu-id="8d297-145">È ora disponibile un riferimento a WorldAnchorStore, che verrà utilizzato per salvare e caricare ancoraggi del mondo specifici.</span><span class="sxs-lookup"><span data-stu-id="8d297-145">We now have a reference to the WorldAnchorStore, which we'll use to save and load specific World Anchors.</span></span>

### <a name="saving-a-worldanchor"></a><span data-ttu-id="8d297-146">Salvataggio di un oggetto WorldAnchor</span><span class="sxs-lookup"><span data-stu-id="8d297-146">Saving a WorldAnchor</span></span>

<span data-ttu-id="8d297-147">Per salvare, è sufficiente assegnare un nome a ciò che si sta salvando e passarlo all'oggetto WorldAnchor ottenuto in precedenza quando si vuole salvare.</span><span class="sxs-lookup"><span data-stu-id="8d297-147">To save, we simply need to name what we are saving and pass it in the WorldAnchor we got before when we want to save.</span></span> <span data-ttu-id="8d297-148">Nota: il tentativo di salvare due ancoraggi nella stessa stringa avrà esito negativo (archivio. Save restituirà false.</span><span class="sxs-lookup"><span data-stu-id="8d297-148">Note: trying to save two anchors to the same string will fail (store.Save will return false).</span></span> <span data-ttu-id="8d297-149">Eliminare il salvataggio precedente prima di salvare quello nuovo:</span><span class="sxs-lookup"><span data-stu-id="8d297-149">Delete the previous save before saving the new one:</span></span>

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

### <a name="loading-a-worldanchor"></a><span data-ttu-id="8d297-150">Caricamento di un oggetto WorldAnchor</span><span class="sxs-lookup"><span data-stu-id="8d297-150">Loading a WorldAnchor</span></span>

<span data-ttu-id="8d297-151">E per caricare:</span><span class="sxs-lookup"><span data-stu-id="8d297-151">And to load:</span></span>

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

<span data-ttu-id="8d297-152">È anche possibile usare l'archivio. Delete() per rimuovere un ancoraggio salvato e salvato in precedenza. Clear() per rimuovere tutti i dati salvati in precedenza.</span><span class="sxs-lookup"><span data-stu-id="8d297-152">We additionally can use store.Delete() to remove an anchor we previously saved and store.Clear() to remove all previously saved data.</span></span>

### <a name="enumerating-existing-anchors"></a><span data-ttu-id="8d297-153">Enumerazione di ancoraggi esistenti</span><span class="sxs-lookup"><span data-stu-id="8d297-153">Enumerating Existing Anchors</span></span>

<span data-ttu-id="8d297-154">Per individuare ancoraggi archiviati in precedenza, chiamare GetAllIds.</span><span class="sxs-lookup"><span data-stu-id="8d297-154">To discover previously stored anchors, call GetAllIds.</span></span>

```cs
string[] ids = this.store.GetAllIds();
for (int index = 0; index < ids.Length; index++)
{
    Debug.Log(ids[index]);
}
```

## <a name="persisting-holograms-for-multiple-devices"></a><span data-ttu-id="8d297-155">Salvataggio permanente di ologrammi per più dispositivi</span><span class="sxs-lookup"><span data-stu-id="8d297-155">Persisting holograms for multiple devices</span></span>

<span data-ttu-id="8d297-156">È possibile usare <a href="/azure/spatial-anchors/overview" target="_blank">Ancoraggi</a> nello stato di Azure per creare un ancoraggio cloud durevole da un WorldAnchor locale, che l'app può quindi individuare in più dispositivi HoloLens, iOS e Android, anche se questi dispositivi non sono presenti contemporaneamente.</span><span class="sxs-lookup"><span data-stu-id="8d297-156">You can use <a href="/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> to create a durable cloud anchor from a local WorldAnchor, which your app can then locate across multiple HoloLens, iOS and Android devices, even if those devices aren't present together at the same time.</span></span>  <span data-ttu-id="8d297-157">Poiché gli ancoraggi cloud sono persistenti, più dispositivi nel tempo possono visualizzare il rendering del contenuto relativo all'ancoraggio nella stessa posizione fisica.</span><span class="sxs-lookup"><span data-stu-id="8d297-157">Because cloud anchors are persistent, multiple devices over time can each see content rendered relative to that anchor in the same physical location.</span></span>

<span data-ttu-id="8d297-158">Per iniziare a creare esperienze condivise in Unity, provare le guide introduttive di <a href="/azure/spatial-anchors/unity-overview" target="_blank">Azure Spatial Anchors Unity di</a>5 minuti.</span><span class="sxs-lookup"><span data-stu-id="8d297-158">To get started building shared experiences in Unity, try out the 5-minute <a href="/azure/spatial-anchors/unity-overview" target="_blank">Azure Spatial Anchors Unity quickstarts</a>.</span></span>

<span data-ttu-id="8d297-159">Dopo aver eseguito le attività con Ancoraggi nello spazio di Azure, è possibile creare e individuare ancoraggi <a href="/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">in Unity.</a></span><span class="sxs-lookup"><span data-stu-id="8d297-159">Once you're up and running with Azure Spatial Anchors, you can then <a href="/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">create and locate anchors in Unity</a>.</span></span>

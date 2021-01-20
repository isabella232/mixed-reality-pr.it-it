---
title: Persistenza in Unity
description: La persistenza consente agli utenti di aggiungere singoli ologrammi ovunque si trovino e quindi di trovarli in un secondo momento rispetto a molti utilizzi dell'app.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: HoloLens, persistenza, Unity, auricolare realtà mista, auricolare di realtà mista di Windows, auricolare della realtà virtuale
ms.openlocfilehash: 7d12764dac2259388fe57d3924165783eab3dac5
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/20/2021
ms.locfileid: "98583493"
---
# <a name="persistence-in-unity"></a><span data-ttu-id="aacbc-104">Persistenza in Unity</span><span class="sxs-lookup"><span data-stu-id="aacbc-104">Persistence in Unity</span></span>

<span data-ttu-id="aacbc-105">**Spazio dei nomi:** *UnityEngine. XR. WSA. Persistence*</span><span class="sxs-lookup"><span data-stu-id="aacbc-105">**Namespace:** *UnityEngine.XR.WSA.Persistence*</span></span><br>
<span data-ttu-id="aacbc-106">**Classe:** *WorldAnchorStore*</span><span class="sxs-lookup"><span data-stu-id="aacbc-106">**Class:** *WorldAnchorStore*</span></span>

<span data-ttu-id="aacbc-107">WorldAnchorStore è la chiave per la creazione di esperienze olografiche in cui gli ologrammi mantengono posizioni reali specifiche tra le istanze dell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="aacbc-107">The WorldAnchorStore is the key to creating holographic experiences where holograms stay in specific real world positions across instances of the application.</span></span> <span data-ttu-id="aacbc-108">Gli utenti possono quindi aggiungere singoli ologrammi ovunque si trovino e trovarli più avanti nello stesso punto rispetto a molti utilizzi dell'app.</span><span class="sxs-lookup"><span data-stu-id="aacbc-108">Users can then pin individual holograms wherever they want, and find them later in the same spot over many uses of your app.</span></span>

## <a name="how-to-persist-holograms-across-sessions"></a><span data-ttu-id="aacbc-109">Come salvare in modo permanente gli ologrammi tra le sessioni</span><span class="sxs-lookup"><span data-stu-id="aacbc-109">How to persist holograms across sessions</span></span>

<span data-ttu-id="aacbc-110">Il WorldAnchorStore consentirà di rendere permanente il percorso di WorldAnchor tra le sessioni.</span><span class="sxs-lookup"><span data-stu-id="aacbc-110">The WorldAnchorStore will allow you to persist the location of WorldAnchor's across sessions.</span></span> <span data-ttu-id="aacbc-111">Per rendere effettivamente permanente gli ologrammi tra le sessioni, è necessario tenere traccia separatamente dei GameObject che usano un particolare ancoraggio mondiale.</span><span class="sxs-lookup"><span data-stu-id="aacbc-111">To actually persist holograms across sessions, you'll need to separately keep track of your GameObjects that use a particular world anchor.</span></span> <span data-ttu-id="aacbc-112">Spesso è opportuno creare una radice GameObject con un ancoraggio globale e avere elementi figlio olografici ancorati con un offset della posizione locale.</span><span class="sxs-lookup"><span data-stu-id="aacbc-112">It often makes sense to create a GameObject root with a world anchor and have children holograms anchored by it with a local position offset.</span></span>

<span data-ttu-id="aacbc-113">Per caricare gli ologrammi dalle sessioni precedenti:</span><span class="sxs-lookup"><span data-stu-id="aacbc-113">To load holograms from previous sessions:</span></span>
1. <span data-ttu-id="aacbc-114">Ottenere il WorldAnchorStore</span><span class="sxs-lookup"><span data-stu-id="aacbc-114">Get the WorldAnchorStore</span></span>
2. <span data-ttu-id="aacbc-115">Caricare i dati dell'app correlati all'ancoraggio globale, che fornisce l'ID dell'ancoraggio globale</span><span class="sxs-lookup"><span data-stu-id="aacbc-115">Load app data relating to the world anchor, which gives you the ID of the world anchor</span></span>
3. <span data-ttu-id="aacbc-116">Caricare un ancoraggio globale dall'ID</span><span class="sxs-lookup"><span data-stu-id="aacbc-116">Load a world anchor from its ID</span></span>

<span data-ttu-id="aacbc-117">Per salvare gli ologrammi per le sessioni future:</span><span class="sxs-lookup"><span data-stu-id="aacbc-117">To save holograms for future sessions:</span></span>
1. <span data-ttu-id="aacbc-118">Ottenere il WorldAnchorStore</span><span class="sxs-lookup"><span data-stu-id="aacbc-118">Get the WorldAnchorStore</span></span>
2. <span data-ttu-id="aacbc-119">Salva un ancoraggio globale specificando un ID</span><span class="sxs-lookup"><span data-stu-id="aacbc-119">Save a world anchor specifying an ID</span></span>
3. <span data-ttu-id="aacbc-120">Salva i dati dell'app correlati all'ancoraggio globale insieme a un ID</span><span class="sxs-lookup"><span data-stu-id="aacbc-120">Save app data relating to the world anchor along with an ID</span></span>

### <a name="getting-the-worldanchorstore"></a><span data-ttu-id="aacbc-121">Recupero di WorldAnchorStore</span><span class="sxs-lookup"><span data-stu-id="aacbc-121">Getting the WorldAnchorStore</span></span>

<span data-ttu-id="aacbc-122">È consigliabile tenere un riferimento a WorldAnchorStore in modo da essere a conoscenza quando è pronto per eseguire un'operazione.</span><span class="sxs-lookup"><span data-stu-id="aacbc-122">You'll want to keep a reference to the WorldAnchorStore so you know when it's ready to perform an operation.</span></span> <span data-ttu-id="aacbc-123">Poiché si tratta di una chiamata asincrona, potenzialmente non appena viene avviata, si vuole chiamare:</span><span class="sxs-lookup"><span data-stu-id="aacbc-123">Since this is an async call, potentially as soon as start up, you want to call:</span></span>

```
WorldAnchorStore.GetAsync(StoreLoaded);
```

<span data-ttu-id="aacbc-124">StoreLoaded in questo caso è il gestore per il completamento del caricamento di WorldAnchorStore:</span><span class="sxs-lookup"><span data-stu-id="aacbc-124">StoreLoaded in this case is our handler for when the WorldAnchorStore has completed loading:</span></span>

```
private void StoreLoaded(WorldAnchorStore store)
{
       this.store = store;
}
```

<span data-ttu-id="aacbc-125">È ora disponibile un riferimento a WorldAnchorStore, che verrà usato per salvare e caricare specifici ancoraggi internazionali.</span><span class="sxs-lookup"><span data-stu-id="aacbc-125">We now have a reference to the WorldAnchorStore, which we'll use to save and load specific World Anchors.</span></span>

### <a name="saving-a-worldanchor"></a><span data-ttu-id="aacbc-126">Salvataggio di un WorldAnchor</span><span class="sxs-lookup"><span data-stu-id="aacbc-126">Saving a WorldAnchor</span></span>

<span data-ttu-id="aacbc-127">Per salvare, è sufficiente assegnare un nome a quello che si sta salvando e passarlo nel WorldAnchor ottenuto in precedenza quando si desidera salvare.</span><span class="sxs-lookup"><span data-stu-id="aacbc-127">To save, we simply need to name what we are saving and pass it in the WorldAnchor we got before when we want to save.</span></span> <span data-ttu-id="aacbc-128">Nota: il tentativo di salvare due ancoraggi nella stessa stringa avrà esito negativo (Store. Il salvataggio restituirà false.</span><span class="sxs-lookup"><span data-stu-id="aacbc-128">Note: trying to save two anchors to the same string will fail (store.Save will return false).</span></span> <span data-ttu-id="aacbc-129">Eliminare il salvataggio precedente prima di salvare quello nuovo:</span><span class="sxs-lookup"><span data-stu-id="aacbc-129">Delete the previous save before saving the new one:</span></span>

```
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

### <a name="loading-a-worldanchor"></a><span data-ttu-id="aacbc-130">Caricamento di un WorldAnchor</span><span class="sxs-lookup"><span data-stu-id="aacbc-130">Loading a WorldAnchor</span></span>

<span data-ttu-id="aacbc-131">E per caricare:</span><span class="sxs-lookup"><span data-stu-id="aacbc-131">And to load:</span></span>

```
private void LoadGame()
{
       // Save data about holograms positioned by this world anchor
       this.savedRoot = this.store.Load("rootGameObject", rootGameObject);
       if (!this.savedRoot)
       {
              // We didn't actually have the game root saved! We have to re-place our objects or start over
       }
}
```

<span data-ttu-id="aacbc-132">È inoltre possibile utilizzare Store. Eliminare () per rimuovere un ancoraggio precedentemente salvato e archiviato. Deselezionare () per rimuovere tutti i dati salvati in precedenza.</span><span class="sxs-lookup"><span data-stu-id="aacbc-132">We additionally can use store.Delete() to remove an anchor we previously saved and store.Clear() to remove all previously saved data.</span></span>

### <a name="enumerating-existing-anchors"></a><span data-ttu-id="aacbc-133">Enumerazione degli ancoraggi esistenti</span><span class="sxs-lookup"><span data-stu-id="aacbc-133">Enumerating Existing Anchors</span></span>

<span data-ttu-id="aacbc-134">Per individuare gli ancoraggi precedentemente archiviati, chiamare GetAllIds.</span><span class="sxs-lookup"><span data-stu-id="aacbc-134">To discover previously stored anchors, call GetAllIds.</span></span>

```
string[] ids = this.store.GetAllIds();
for (int index = 0; index < ids.Length; index++)
{
        Debug.Log(ids[index]);
}
```

## <a name="persisting-holograms-for-multiple-devices"></a><span data-ttu-id="aacbc-135">Mantenimento degli ologrammi per più dispositivi</span><span class="sxs-lookup"><span data-stu-id="aacbc-135">Persisting holograms for multiple devices</span></span>

<span data-ttu-id="aacbc-136">È possibile usare gli <a href="/azure/spatial-anchors/overview" target="_blank">ancoraggi spaziali di Azure</a> per creare un ancoraggio cloud durevole da un WorldAnchor locale, che può essere individuato dall'app su più dispositivi HoloLens, iOS e Android, anche se questi dispositivi non sono presenti contemporaneamente.</span><span class="sxs-lookup"><span data-stu-id="aacbc-136">You can use <a href="/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> to create a durable cloud anchor from a local WorldAnchor, which your app can then locate across multiple HoloLens, iOS and Android devices, even if those devices aren't present together at the same time.</span></span>  <span data-ttu-id="aacbc-137">Poiché gli ancoraggi cloud sono persistenti, più dispositivi nel tempo possono visualizzare il contenuto di cui è stato eseguito il rendering rispetto a tale ancoraggio nella stessa posizione fisica.</span><span class="sxs-lookup"><span data-stu-id="aacbc-137">Because cloud anchors are persistent, multiple devices over time can each see content rendered relative to that anchor in the same physical location.</span></span>

<span data-ttu-id="aacbc-138">Per iniziare a creare esperienze condivise in Unity, provare le <a href="/azure/spatial-anchors/unity-overview" target="_blank">guide introduttive Unity Anchors di Azure</a>di 5 minuti.</span><span class="sxs-lookup"><span data-stu-id="aacbc-138">To get started building shared experiences in Unity, try out the 5-minute <a href="/azure/spatial-anchors/unity-overview" target="_blank">Azure Spatial Anchors Unity quickstarts</a>.</span></span>

<span data-ttu-id="aacbc-139">Quando si è operativi con i Anchor spaziali di Azure, è possibile <a href="/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">creare e individuare ancoraggi in Unity</a>.</span><span class="sxs-lookup"><span data-stu-id="aacbc-139">Once you're up and running with Azure Spatial Anchors, you can then <a href="/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">create and locate anchors in Unity</a>.</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="aacbc-140">Successivo checkpoint di sviluppo</span><span class="sxs-lookup"><span data-stu-id="aacbc-140">Next Development Checkpoint</span></span>

<span data-ttu-id="aacbc-141">Se si sta seguendo il percorso di checkpoint per lo sviluppo di Unity, è possibile esplorare i blocchi predefiniti di base della realtà mista.</span><span class="sxs-lookup"><span data-stu-id="aacbc-141">If you're following the Unity development checkpoint journey we've laid out, you're in the midst of exploring the Mixed Reality core building blocks.</span></span> <span data-ttu-id="aacbc-142">Da qui è possibile passare al blocco predefinito successivo:</span><span class="sxs-lookup"><span data-stu-id="aacbc-142">From here, you can continue to the next building block:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="aacbc-143">Mapping spaziale</span><span class="sxs-lookup"><span data-stu-id="aacbc-143">Spatial mapping</span></span>](spatial-mapping-in-unity.md)

<span data-ttu-id="aacbc-144">In alternativa, passare alle API e alle funzionalità della piattaforma di realtà mista:</span><span class="sxs-lookup"><span data-stu-id="aacbc-144">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="aacbc-145">Esperienze condivise</span><span class="sxs-lookup"><span data-stu-id="aacbc-145">Shared experiences</span></span>](shared-experiences-in-unity.md)

<span data-ttu-id="aacbc-146">È sempre possibile tornare ai [checkpoint per lo sviluppo con Unity](unity-development-overview.md#2-core-building-blocks) in qualsiasi momento.</span><span class="sxs-lookup"><span data-stu-id="aacbc-146">You can always go back to the [Unity development checkpoints](unity-development-overview.md#2-core-building-blocks) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="aacbc-147">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="aacbc-147">See Also</span></span>
* [<span data-ttu-id="aacbc-148">Persistenza di ancoraggio spaziale</span><span class="sxs-lookup"><span data-stu-id="aacbc-148">Spatial anchor persistence</span></span>](../../design/coordinate-systems.md#spatial-anchor-persistence)
* <span data-ttu-id="aacbc-149"><a href="/azure/spatial-anchors" target="_blank">Ancoraggi nello spazio di Azure</a></span><span class="sxs-lookup"><span data-stu-id="aacbc-149"><a href="/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a></span></span>
* <span data-ttu-id="aacbc-150"><a href="/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Azure Spatial Anchors SDK per Unity</a></span><span class="sxs-lookup"><span data-stu-id="aacbc-150"><a href="/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Azure Spatial Anchors SDK for Unity</a></span></span>
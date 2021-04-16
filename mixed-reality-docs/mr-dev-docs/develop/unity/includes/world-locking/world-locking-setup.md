---
ms.openlocfilehash: 6229b258233f7a80ef6530edd6eb94774a0e54cf
ms.sourcegitcommit: 3e36b2fbbcc250c49aaf8ca1b6133cf0e9db69fa
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2021
ms.locfileid: "107528814"
---
# <a name="world-locking-tools-recommended"></a>[<span data-ttu-id="110f3-101">Strumenti di blocco del mondo (scelta consigliata)</span><span class="sxs-lookup"><span data-stu-id="110f3-101">World Locking Tools (Recommended)</span></span>](#tab/wlt)

<span data-ttu-id="110f3-102">È consigliabile installare World Locking Tools usando il nuovo strumento di funzionalità di realtà mista.</span><span class="sxs-lookup"><span data-stu-id="110f3-102">We recommend installing World Locking Tools using the new Mixed Reality Feature Tool.</span></span> <span data-ttu-id="110f3-103">Dopo aver scaricato Mixed Reality Feature Tool dal collegamento seguente, selezionare la versione più recente di **WLT Core** nella **sezione World Locking Tools (Strumenti** di blocco del mondo):</span><span class="sxs-lookup"><span data-stu-id="110f3-103">Once you've downloaded the Mixed Reality Feature Tool from the link below, select the latest version of **WLT Core** from the **World Locking Tools** section:</span></span>

![Finestra di selezione delle funzionalità di Mixed Reality Feature Tool con gli strumenti di blocco del mondo selezionati](../../images/spatial-anchors-setup-img-01.png)

> [!div class="nextstepaction"]
> [<span data-ttu-id="110f3-105">Installare world locking tools con mr feature tool</span><span class="sxs-lookup"><span data-stu-id="110f3-105">Install World Locking Tools with the MR Feature Tool</span></span>](../../welcome-to-mr-feature-tool.md)

### <a name="automated-setup"></a><span data-ttu-id="110f3-106">Configurazione automatizzata</span><span class="sxs-lookup"><span data-stu-id="110f3-106">Automated setup</span></span>

<span data-ttu-id="110f3-107">Quando il progetto è pronto, eseguire l'utilità di configurazione della scena da **Mixed Reality Toolkit > Utilities > World Locking Tools:**</span><span class="sxs-lookup"><span data-stu-id="110f3-107">When your project is ready to go, run the configure scene utility from **Mixed Reality Toolkit > Utilities > World Locking Tools**:</span></span>

![Editor unity con il menu mixed reality toolkit selezionato](../../images/world-locking-configuration-img-01.jpeg)

> [!IMPORTANT]
> <span data-ttu-id="110f3-109">L'utilità Configura scena può essere rieseguita in qualsiasi momento.</span><span class="sxs-lookup"><span data-stu-id="110f3-109">The Configure scene utility can be rerun at any time.</span></span> <span data-ttu-id="110f3-110">Ad esempio, deve essere rieseguita se la destinazione AR è stata modificata da Legacy a XR SDK.</span><span class="sxs-lookup"><span data-stu-id="110f3-110">For example, it should be rerun if the AR target has been changed from Legacy to XR SDK.</span></span> <span data-ttu-id="110f3-111">Se la scena è già configurata correttamente, l'esecuzione dell'utilità non ha alcun effetto.</span><span class="sxs-lookup"><span data-stu-id="110f3-111">If the scene is already properly configured, running the utility has no effect.</span></span>

### <a name="visualizers"></a><span data-ttu-id="110f3-112">Visualizzatori</span><span class="sxs-lookup"><span data-stu-id="110f3-112">Visualizers</span></span>

<span data-ttu-id="110f3-113">Durante lo sviluppo iniziale, l'aggiunta di visualizzatori può essere utile per assicurarsi che WLT sia configurato e funzioni correttamente.</span><span class="sxs-lookup"><span data-stu-id="110f3-113">During early development, adding visualizers can be helpful to ensure WLT is setup and working properly.</span></span> <span data-ttu-id="110f3-114">Possono essere rimossi per le prestazioni di produzione o se per qualsiasi motivo non sono più necessari, usando l'utilità Rimuovi visualizzatori.</span><span class="sxs-lookup"><span data-stu-id="110f3-114">They can be removed for production performance, or if for any reason are no longer needed, using the Remove visualizers utility.</span></span> <span data-ttu-id="110f3-115">Altri dettagli sui visualizzatori sono disponibili nella documentazione [degli strumenti](https://microsoft.github.io/MixedReality-WorldLockingTools-Unity/DocGen/Documentation/HowTos/Tools.html#visualizers).</span><span class="sxs-lookup"><span data-stu-id="110f3-115">More details on the visualizers can be found in the [Tools documentation](https://microsoft.github.io/MixedReality-WorldLockingTools-Unity/DocGen/Documentation/HowTos/Tools.html#visualizers).</span></span>

# <a name="aranchormanager"></a>[<span data-ttu-id="110f3-116">ARAnchorManager</span><span class="sxs-lookup"><span data-stu-id="110f3-116">ARAnchorManager</span></span>](#tab/anchorstore)

<span data-ttu-id="110f3-117">Il plug-in OpenXR di realtà mista fornisce funzionalità di ancoraggio di base tramite un'implementazione di ARFoundation **ARAnchorManager di** Unity.</span><span class="sxs-lookup"><span data-stu-id="110f3-117">The Mixed Reality OpenXR Plugin supplies basic anchor functionality through an implementation of Unity’s ARFoundation **ARAnchorManager**.</span></span> <span data-ttu-id="110f3-118">Per informazioni di base su ARAnchors in ARFoundation, visita il manuale [arFoundation per AR Anchor Manager.](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/anchor-manager.html)</span><span class="sxs-lookup"><span data-stu-id="110f3-118">To learn the basics on ARAnchors in ARFoundation, visit the [ARFoundation Manual for AR Anchor Manager](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/anchor-manager.html).</span></span> 

# <a name="worldanchor"></a>[<span data-ttu-id="110f3-119">WorldAnchor</span><span class="sxs-lookup"><span data-stu-id="110f3-119">WorldAnchor</span></span>](#tab/worldanchor)

## <a name="building-a-world-scale-experience"></a><span data-ttu-id="110f3-120">Creazione di un'esperienza su scala globale</span><span class="sxs-lookup"><span data-stu-id="110f3-120">Building a world-scale experience</span></span>

<span data-ttu-id="110f3-121">**Spazio dei nomi:** *UnityEngine.XR.WSA*</span><span class="sxs-lookup"><span data-stu-id="110f3-121">**Namespace:** *UnityEngine.XR.WSA*</span></span><br>
<span data-ttu-id="110f3-122">**Tipo:** *WorldAnchor*</span><span class="sxs-lookup"><span data-stu-id="110f3-122">**Type:** *WorldAnchor*</span></span>

<span data-ttu-id="110f3-123">Per le **vere esperienze su** scala mondiale in HoloLens che consentono agli utenti di superare i 5 metri, sono necessarie nuove tecniche oltre quelle usate per le esperienze su larga scala.</span><span class="sxs-lookup"><span data-stu-id="110f3-123">For true **world-scale experiences** on HoloLens that let users wander beyond 5 meters, you'll need new techniques beyond those used for room-scale experiences.</span></span> <span data-ttu-id="110f3-124">Una tecnica chiave da usare consiste nel creare un [ancoraggio](../../../../design/coordinate-systems.md#spatial-anchors) spaziale per bloccare un cluster di ologrammi esattamente in posizione nel mondo fisico, indipendentemente dalla distanza di roaming dell'utente e quindi trovare di nuovo tali [ologrammi](../../../../design/coordinate-systems.md#spatial-anchor-persistence)nelle sessioni successive.</span><span class="sxs-lookup"><span data-stu-id="110f3-124">One key technique you'll use is to create a [spatial anchor](../../../../design/coordinate-systems.md#spatial-anchors) to lock a cluster of holograms precisely in place in the physical world, no matter how far the user has roamed, and then [find those holograms again in later sessions](../../../../design/coordinate-systems.md#spatial-anchor-persistence).</span></span>

<span data-ttu-id="110f3-125">In Unity si crea un ancoraggio spaziale aggiungendo il **componente WorldAnchor** Unity a gameobject.</span><span class="sxs-lookup"><span data-stu-id="110f3-125">In Unity, you create a spatial anchor by adding the **WorldAnchor** Unity component to a GameObject.</span></span>

### <a name="adding-a-world-anchor"></a><span data-ttu-id="110f3-126">Aggiunta di un ancoraggio mondo</span><span class="sxs-lookup"><span data-stu-id="110f3-126">Adding a World Anchor</span></span>

<span data-ttu-id="110f3-127">Per aggiungere un ancoraggio del mondo, chiamare `AddComponent<WorldAnchor>()` sull'oggetto di gioco con la trasformazione che si vuole ancorare nel mondo reale.</span><span class="sxs-lookup"><span data-stu-id="110f3-127">To add a world anchor, call `AddComponent<WorldAnchor>()` on the game object with the transform you want to anchor in the real world.</span></span>

```cs
WorldAnchor anchor = gameObject.AddComponent<WorldAnchor>();
```

<span data-ttu-id="110f3-128">Questo è tutto.</span><span class="sxs-lookup"><span data-stu-id="110f3-128">That's it!</span></span> <span data-ttu-id="110f3-129">Questo oggetto di gioco sarà ora ancorato alla posizione corrente nel mondo fisico. È possibile che le coordinate del mondo unity si aggireranno leggermente nel tempo per garantire l'allineamento fisico.</span><span class="sxs-lookup"><span data-stu-id="110f3-129">This game object will now be anchored to its current location in the physical world - you may see its Unity world coordinates adjust slightly over time to ensure that physical alignment.</span></span> <span data-ttu-id="110f3-130">Fare riferimento a [Caricamento di un ancoraggio mondo](#loading-a-worldanchor) per trovare di nuovo questa posizione ancorata in una sessione futura dell'app.</span><span class="sxs-lookup"><span data-stu-id="110f3-130">Refer to [loading a world anchor](#loading-a-worldanchor) to find this anchored location again in a future app session.</span></span>

### <a name="removing-a-world-anchor"></a><span data-ttu-id="110f3-131">Rimozione di un ancoraggio mondo</span><span class="sxs-lookup"><span data-stu-id="110f3-131">Removing a World Anchor</span></span>

<span data-ttu-id="110f3-132">Se non si vuole più che GameObject venga bloccato in una posizione fisica del mondo e non si intende spostarlo in questo frame, è sufficiente chiamare Destroy sul componente World Anchor.</span><span class="sxs-lookup"><span data-stu-id="110f3-132">If you no longer want the GameObject locked to a physical world location and don't intend on moving it this frame, then you can just call Destroy on the World Anchor component.</span></span>

```cs
Destroy(gameObject.GetComponent<WorldAnchor>());
```

<span data-ttu-id="110f3-133">Se si vuole spostare GameObject in questo frame, è invece necessario chiamare DestroyImmediate.</span><span class="sxs-lookup"><span data-stu-id="110f3-133">If you want to move the GameObject this frame, you need to call DestroyImmediate instead.</span></span>

```cs
DestroyImmediate(gameObject.GetComponent<WorldAnchor>());
```

### <a name="moving-a-world-anchored-gameobject"></a><span data-ttu-id="110f3-134">Spostamento di un oggetto GameObject ancorato al mondo</span><span class="sxs-lookup"><span data-stu-id="110f3-134">Moving a World Anchored GameObject</span></span>

<span data-ttu-id="110f3-135">Gli oggetti GameObject non possono essere spostati mentre è in esecuzione un ancoraggio mondo.</span><span class="sxs-lookup"><span data-stu-id="110f3-135">GameObject's cannot be moved while a World Anchor is on it.</span></span> <span data-ttu-id="110f3-136">Se è necessario spostare GameObject in questo frame, è necessario:</span><span class="sxs-lookup"><span data-stu-id="110f3-136">If you need to move the GameObject this frame, you need to:</span></span>

1. <span data-ttu-id="110f3-137">DestroyImmediate the World Anchor component</span><span class="sxs-lookup"><span data-stu-id="110f3-137">DestroyImmediate the World Anchor component</span></span>
2. <span data-ttu-id="110f3-138">Spostare GameObject</span><span class="sxs-lookup"><span data-stu-id="110f3-138">Move the GameObject</span></span>
3. <span data-ttu-id="110f3-139">Aggiungere un nuovo componente World Anchor a GameObject.</span><span class="sxs-lookup"><span data-stu-id="110f3-139">Add a new World Anchor component to the GameObject.</span></span>

```cs
DestroyImmediate(gameObject.GetComponent<WorldAnchor>());
gameObject.transform.position = new Vector3(0, 0, 2);
WorldAnchor anchor = gameObject.AddComponent<WorldAnchor>();
```

### <a name="handling-locatability-changes"></a><span data-ttu-id="110f3-140">Gestione delle modifiche di individuazione</span><span class="sxs-lookup"><span data-stu-id="110f3-140">Handling Locatability Changes</span></span>

<span data-ttu-id="110f3-141">Un Oggetto WorldAnchor potrebbe non essere localizzato nel mondo fisico in un momento nel tempo.</span><span class="sxs-lookup"><span data-stu-id="110f3-141">A WorldAnchor may not be locatable in the physical world at a point in time.</span></span> <span data-ttu-id="110f3-142">In questo caso, Unity non aggiorerà la trasformazione dell'oggetto ancorato.</span><span class="sxs-lookup"><span data-stu-id="110f3-142">If that occurs, Unity won't be updating the transform of the anchored object.</span></span> <span data-ttu-id="110f3-143">Questo può cambiare anche durante l'esecuzione di un'app.</span><span class="sxs-lookup"><span data-stu-id="110f3-143">This also can change while an app is running.</span></span> <span data-ttu-id="110f3-144">Se non si gestisce la modifica dell'individuabilità, l'oggetto non verrà visualizzato nella posizione fisica corretta nel mondo.</span><span class="sxs-lookup"><span data-stu-id="110f3-144">Failure to handle the change in locatability will cause the object to not appear in the correct physical location in the world.</span></span>

<span data-ttu-id="110f3-145">Per ricevere notifiche sulle modifiche di individuabilità:</span><span class="sxs-lookup"><span data-stu-id="110f3-145">To be notified about locatability changes:</span></span>

1. <span data-ttu-id="110f3-146">Sottoscrivere l'evento OnTrackingChanged</span><span class="sxs-lookup"><span data-stu-id="110f3-146">Subscribe to the OnTrackingChanged event</span></span>
2. <span data-ttu-id="110f3-147">Gestire l'evento</span><span class="sxs-lookup"><span data-stu-id="110f3-147">Handle the event</span></span>

<span data-ttu-id="110f3-148">**L'evento OnTrackingChanged** verrà chiamato ogni volta che l'ancoraggio nello spazio sottostante cambia tra uno stato di posizione e non di individuazione.</span><span class="sxs-lookup"><span data-stu-id="110f3-148">The **OnTrackingChanged** event will be called whenever the underlying spatial anchor changes between a state of being locatable vs. not being locatable.</span></span>

```cs
anchor.OnTrackingChanged += Anchor_OnTrackingChanged;
```

<span data-ttu-id="110f3-149">Gestire quindi l'evento :</span><span class="sxs-lookup"><span data-stu-id="110f3-149">Then handle the event:</span></span>

```cs
private void Anchor_OnTrackingChanged(WorldAnchor self, bool located)
{
    // This simply activates/deactivates this object and all children when tracking changes
    self.gameObject.SetActiveRecursively(located);
}
```

<span data-ttu-id="110f3-150">A volte gli ancoraggi si trovano immediatamente.</span><span class="sxs-lookup"><span data-stu-id="110f3-150">Sometimes anchors are located immediately.</span></span> <span data-ttu-id="110f3-151">In questo caso, questa proprietà isLocated dell'ancoraggio verrà impostata su true quando viene restituito AddComponent <WorldAnchor> ().</span><span class="sxs-lookup"><span data-stu-id="110f3-151">In this case, this isLocated property of the anchor will be set to true when AddComponent<WorldAnchor>() returns.</span></span> <span data-ttu-id="110f3-152">Di conseguenza, l'evento OnTrackingChanged non verrà attivato.</span><span class="sxs-lookup"><span data-stu-id="110f3-152">As a result, the OnTrackingChanged event won't be triggered.</span></span> <span data-ttu-id="110f3-153">Un modello pulito sarebbe chiamare il gestore OnTrackingChanged con lo stato IsLocated iniziale dopo aver collegato un ancoraggio.</span><span class="sxs-lookup"><span data-stu-id="110f3-153">A clean pattern would be to call your OnTrackingChanged handler with the initial IsLocated state after attaching an anchor.</span></span>

```cs
Anchor_OnTrackingChanged(anchor, anchor.isLocated);
```
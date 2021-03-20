---
ms.openlocfilehash: 05e2b87383bbc91b7fd8785230152e3549f4b22d
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2021
ms.locfileid: "104719896"
---
# <a name="unity-2020--openxr"></a>[<span data-ttu-id="be04b-101">Unity 2020 + OpenXR</span><span class="sxs-lookup"><span data-stu-id="be04b-101">Unity 2020 + OpenXR</span></span>](#tab/openxr)

<span data-ttu-id="be04b-102">Il plug-in di OpenXR realtà mista fornisce la funzionalità di ancoraggio di base tramite un'implementazione di ARFoundation **ARAnchorManager** di Unity.</span><span class="sxs-lookup"><span data-stu-id="be04b-102">The Mixed Reality OpenXR Plugin supplies basic anchor functionality through an implementation of Unity’s ARFoundation **ARAnchorManager**.</span></span> <span data-ttu-id="be04b-103">Per informazioni sulle nozioni di base su ARAnchors in ARFoundation, vedere il [Manuale di ARFoundation per AR Anchor Manager](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/anchor-manager.html).</span><span class="sxs-lookup"><span data-stu-id="be04b-103">To learn the basics on ARAnchors in ARFoundation, visit the [ARFoundation Manual for AR Anchor Manager](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/anchor-manager.html).</span></span> 

# <a name="unity-20192020--windows-xr-plugin"></a>[<span data-ttu-id="be04b-104">Plug-in Unity 2019/2020 + Windows XR</span><span class="sxs-lookup"><span data-stu-id="be04b-104">Unity 2019/2020 + Windows XR Plugin</span></span>](#tab/winxr)

<span data-ttu-id="be04b-105">Il plug-in di OpenXR realtà mista fornisce la funzionalità di ancoraggio di base tramite un'implementazione di ARFoundation **ARAnchorManager** di Unity.</span><span class="sxs-lookup"><span data-stu-id="be04b-105">The Mixed Reality OpenXR Plugin supplies basic anchor functionality through an implementation of Unity’s ARFoundation **ARAnchorManager**.</span></span> <span data-ttu-id="be04b-106">Per informazioni sulle nozioni di base su ARAnchors in ARFoundation, vedere il [Manuale di ARFoundation per AR Anchor Manager](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/anchor-manager.html).</span><span class="sxs-lookup"><span data-stu-id="be04b-106">To learn the basics on ARAnchors in ARFoundation, visit the [ARFoundation Manual for AR Anchor Manager](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/anchor-manager.html).</span></span>

# <a name="legacy-wsa"></a>[<span data-ttu-id="be04b-107">WSA legacy</span><span class="sxs-lookup"><span data-stu-id="be04b-107">Legacy WSA</span></span>](#tab/wsa)

## <a name="building-a-world-scale-experience"></a><span data-ttu-id="be04b-108">Creazione di un'esperienza su scala globale</span><span class="sxs-lookup"><span data-stu-id="be04b-108">Building a world-scale experience</span></span>

<span data-ttu-id="be04b-109">**Spazio dei nomi:** *UnityEngine. XR. WSA*</span><span class="sxs-lookup"><span data-stu-id="be04b-109">**Namespace:** *UnityEngine.XR.WSA*</span></span><br>
<span data-ttu-id="be04b-110">**Tipo:** *WorldAnchor*</span><span class="sxs-lookup"><span data-stu-id="be04b-110">**Type:** *WorldAnchor*</span></span>

<span data-ttu-id="be04b-111">Per esperienze reali su **scala mondiale** su HoloLens che consentono agli utenti di superare i 5 metri, sono necessarie nuove tecniche oltre a quelle usate per le esperienze su scala.</span><span class="sxs-lookup"><span data-stu-id="be04b-111">For true **world-scale experiences** on HoloLens that let users wander beyond 5 meters, you'll need new techniques beyond those used for room-scale experiences.</span></span> <span data-ttu-id="be04b-112">Una tecnica chiave da usare consiste nel creare un [ancoraggio spaziale](../../../design/coordinate-systems.md#spatial-anchors) per bloccare un cluster di ologrammi con precisione sul posto nel mondo fisico, indipendentemente dalla distanza di roaming dell'utente e quindi [ritrovare gli ologrammi nelle sessioni successive](../../../design/coordinate-systems.md#spatial-anchor-persistence).</span><span class="sxs-lookup"><span data-stu-id="be04b-112">One key technique you'll use is to create a [spatial anchor](../../../design/coordinate-systems.md#spatial-anchors) to lock a cluster of holograms precisely in place in the physical world, no matter how far the user has roamed, and then [find those holograms again in later sessions](../../../design/coordinate-systems.md#spatial-anchor-persistence).</span></span>

<span data-ttu-id="be04b-113">In Unity si crea un ancoraggio spaziale aggiungendo il componente **WorldAnchor** Unity a un GameObject.</span><span class="sxs-lookup"><span data-stu-id="be04b-113">In Unity, you create a spatial anchor by adding the **WorldAnchor** Unity component to a GameObject.</span></span>

### <a name="adding-a-world-anchor"></a><span data-ttu-id="be04b-114">Aggiunta di un ancoraggio globale</span><span class="sxs-lookup"><span data-stu-id="be04b-114">Adding a World Anchor</span></span>

<span data-ttu-id="be04b-115">Per aggiungere un ancoraggio globale, chiamare `AddComponent<WorldAnchor>()` sull'oggetto gioco con la trasformazione che si vuole ancorare nel mondo reale.</span><span class="sxs-lookup"><span data-stu-id="be04b-115">To add a world anchor, call `AddComponent<WorldAnchor>()` on the game object with the transform you want to anchor in the real world.</span></span>

```cs
WorldAnchor anchor = gameObject.AddComponent<WorldAnchor>();
```

<span data-ttu-id="be04b-116">Questo è tutto.</span><span class="sxs-lookup"><span data-stu-id="be04b-116">That's it!</span></span> <span data-ttu-id="be04b-117">Questo oggetto Game verrà ora ancorato alla posizione corrente nel mondo fisico. è possibile che le coordinate internazionali del mondo Unity vengano modificate leggermente nel tempo per garantire l'allineamento fisico.</span><span class="sxs-lookup"><span data-stu-id="be04b-117">This game object will now be anchored to its current location in the physical world - you may see its Unity world coordinates adjust slightly over time to ensure that physical alignment.</span></span> <span data-ttu-id="be04b-118">Per trovare nuovamente questa posizione ancorata in una sessione di app futura, vedere [caricamento di un ancoraggio globale](#loading-a-worldanchor) .</span><span class="sxs-lookup"><span data-stu-id="be04b-118">Refer to [loading a world anchor](#loading-a-worldanchor) to find this anchored location again in a future app session.</span></span>

### <a name="removing-a-world-anchor"></a><span data-ttu-id="be04b-119">Rimozione di un ancoraggio globale</span><span class="sxs-lookup"><span data-stu-id="be04b-119">Removing a World Anchor</span></span>

<span data-ttu-id="be04b-120">Se non si vuole più che il GameObject sia bloccato in una posizione fisica del mondo e non si intende trasferirlo in questo frame, è possibile chiamare semplicemente Destroy nel componente World Anchor.</span><span class="sxs-lookup"><span data-stu-id="be04b-120">If you no longer want the GameObject locked to a physical world location and don't intend on moving it this frame, then you can just call Destroy on the World Anchor component.</span></span>

```cs
Destroy(gameObject.GetComponent<WorldAnchor>());
```

<span data-ttu-id="be04b-121">Se si vuole spostare il GameObject in questo frame, è necessario chiamare DestroyImmediate.</span><span class="sxs-lookup"><span data-stu-id="be04b-121">If you want to move the GameObject this frame, you need to call DestroyImmediate instead.</span></span>

```cs
DestroyImmediate(gameObject.GetComponent<WorldAnchor>());
```

### <a name="moving-a-world-anchored-gameobject"></a><span data-ttu-id="be04b-122">Trasferimento di una GameObject ancorata globale</span><span class="sxs-lookup"><span data-stu-id="be04b-122">Moving a World Anchored GameObject</span></span>

<span data-ttu-id="be04b-123">Non è possibile spostare GameObject mentre è presente un ancoraggio globale.</span><span class="sxs-lookup"><span data-stu-id="be04b-123">GameObject's cannot be moved while a World Anchor is on it.</span></span> <span data-ttu-id="be04b-124">Se è necessario spostare il GameObject di questo frame, è necessario:</span><span class="sxs-lookup"><span data-stu-id="be04b-124">If you need to move the GameObject this frame, you need to:</span></span>

1. <span data-ttu-id="be04b-125">DestroyImmediate il componente di ancoraggio globale</span><span class="sxs-lookup"><span data-stu-id="be04b-125">DestroyImmediate the World Anchor component</span></span>
2. <span data-ttu-id="be04b-126">Spostare il GameObject</span><span class="sxs-lookup"><span data-stu-id="be04b-126">Move the GameObject</span></span>
3. <span data-ttu-id="be04b-127">Aggiungere un nuovo componente di ancoraggio globale a GameObject.</span><span class="sxs-lookup"><span data-stu-id="be04b-127">Add a new World Anchor component to the GameObject.</span></span>

```cs
DestroyImmediate(gameObject.GetComponent<WorldAnchor>());
gameObject.transform.position = new Vector3(0, 0, 2);
WorldAnchor anchor = gameObject.AddComponent<WorldAnchor>();
```

### <a name="handling-locatability-changes"></a><span data-ttu-id="be04b-128">Gestione delle modifiche apportate a Locatability</span><span class="sxs-lookup"><span data-stu-id="be04b-128">Handling Locatability Changes</span></span>

<span data-ttu-id="be04b-129">Un WorldAnchor non può essere locatable nel mondo fisico in un determinato momento.</span><span class="sxs-lookup"><span data-stu-id="be04b-129">A WorldAnchor may not be locatable in the physical world at a point in time.</span></span> <span data-ttu-id="be04b-130">In tal caso, Unity non aggiornerà la trasformazione dell'oggetto ancorato.</span><span class="sxs-lookup"><span data-stu-id="be04b-130">If that occurs, Unity won't be updating the transform of the anchored object.</span></span> <span data-ttu-id="be04b-131">Questo può cambiare anche durante l'esecuzione di un'app.</span><span class="sxs-lookup"><span data-stu-id="be04b-131">This also can change while an app is running.</span></span> <span data-ttu-id="be04b-132">Se non si gestisce la modifica in locatability, l'oggetto non verrà visualizzato nella posizione fisica corretta del mondo.</span><span class="sxs-lookup"><span data-stu-id="be04b-132">Failure to handle the change in locatability will cause the object to not appear in the correct physical location in the world.</span></span>

<span data-ttu-id="be04b-133">Per ricevere notifiche sulle modifiche apportate a locatability:</span><span class="sxs-lookup"><span data-stu-id="be04b-133">To be notified about locatability changes:</span></span>

1. <span data-ttu-id="be04b-134">Sottoscrivere l'evento OnTrackingChanged</span><span class="sxs-lookup"><span data-stu-id="be04b-134">Subscribe to the OnTrackingChanged event</span></span>
2. <span data-ttu-id="be04b-135">Gestisci evento</span><span class="sxs-lookup"><span data-stu-id="be04b-135">Handle the event</span></span>

<span data-ttu-id="be04b-136">L'evento **OnTrackingChanged** verrà chiamato ogni volta che l'ancoraggio spaziale sottostante viene modificato tra uno stato di locatable e non locatable.</span><span class="sxs-lookup"><span data-stu-id="be04b-136">The **OnTrackingChanged** event will be called whenever the underlying spatial anchor changes between a state of being locatable vs. not being locatable.</span></span>

```cs
anchor.OnTrackingChanged += Anchor_OnTrackingChanged;
```

<span data-ttu-id="be04b-137">Gestire quindi l'evento:</span><span class="sxs-lookup"><span data-stu-id="be04b-137">Then handle the event:</span></span>

```cs
private void Anchor_OnTrackingChanged(WorldAnchor self, bool located)
{
    // This simply activates/deactivates this object and all children when tracking changes
    self.gameObject.SetActiveRecursively(located);
}
```

<span data-ttu-id="be04b-138">Talvolta gli ancoraggi si trovano immediatamente.</span><span class="sxs-lookup"><span data-stu-id="be04b-138">Sometimes anchors are located immediately.</span></span> <span data-ttu-id="be04b-139">In questo caso, la proprietà individuata dell'ancoraggio verrà impostata su true quando AddComponent <WorldAnchor> () restituisce.</span><span class="sxs-lookup"><span data-stu-id="be04b-139">In this case, this isLocated property of the anchor will be set to true when AddComponent<WorldAnchor>() returns.</span></span> <span data-ttu-id="be04b-140">Di conseguenza, l'evento OnTrackingChanged non verrà attivato.</span><span class="sxs-lookup"><span data-stu-id="be04b-140">As a result, the OnTrackingChanged event won't be triggered.</span></span> <span data-ttu-id="be04b-141">Un modello pulito consiste nel chiamare il gestore OnTrackingChanged con lo stato individuato iniziale dopo aver collegato un ancoraggio.</span><span class="sxs-lookup"><span data-stu-id="be04b-141">A clean pattern would be to call your OnTrackingChanged handler with the initial IsLocated state after attaching an anchor.</span></span>

```cs
Anchor_OnTrackingChanged(anchor, anchor.isLocated);
```
---
title: Controller, puntatori e stato attivo
description: Interazione con controller, puntatori e stato attivo.
author: cDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, puntatori, controller
ms.openlocfilehash: b3e4438c1318abbc60606bcbca42854edae28167
ms.sourcegitcommit: 8b4c2b1aac83bc8adf46acfd92b564f899ef7735
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/30/2021
ms.locfileid: "113121619"
---
# <a name="controllers-pointers-and-focus"></a><span data-ttu-id="dc630-104">Controller, puntatori e stato attivo</span><span class="sxs-lookup"><span data-stu-id="dc630-104">Controllers, pointers, and focus</span></span>

<span data-ttu-id="dc630-105">Controller, puntatori e stato attivo sono concetti di livello superiore che si basano sulle basi stabilite dal sistema di input principale.</span><span class="sxs-lookup"><span data-stu-id="dc630-105">Controllers, pointers, and focus are higher-level concepts that build upon the foundation established by the core input system.</span></span> <span data-ttu-id="dc630-106">Insieme, forniscono una grande parte del meccanismo per l'interazione con gli oggetti nella scena.</span><span class="sxs-lookup"><span data-stu-id="dc630-106">Together, they provide a large portion of the mechanism for interacting with objects in the scene.</span></span>

## <a name="controllers"></a><span data-ttu-id="dc630-107">Controllers</span><span class="sxs-lookup"><span data-stu-id="dc630-107">Controllers</span></span>

<span data-ttu-id="dc630-108">I controller sono rappresentazioni di un controller fisico (6 gradi di libertà, mano articolata e così via).</span><span class="sxs-lookup"><span data-stu-id="dc630-108">Controllers are representations of a physical controller (6-degrees of freedom, articulated hand, etc).</span></span> <span data-ttu-id="dc630-109">Vengono creati dai gestori di dispositivi e sono responsabili della comunicazione con il sistema sottostante corrispondente e della traduzione di tali dati in dati ed eventi a forma di MRTK.</span><span class="sxs-lookup"><span data-stu-id="dc630-109">They are created by device managers and are responsible for communicating with the corresponding underlying system and translating that data into MRTK-shaped data and events.a</span></span>

<span data-ttu-id="dc630-110">Ad esempio, nella piattaforma Windows Mixed Reality, è un controller responsabile dell'interfaccia con le API di rilevamento della mano di Windows sottostanti per ottenere informazioni su giunzioni, pose e altre proprietà della [`WindowsMixedRealityArticulatedHand`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityArticulatedHand) mano. [](/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate)</span><span class="sxs-lookup"><span data-stu-id="dc630-110">For example, on the Windows Mixed Reality platform, the [`WindowsMixedRealityArticulatedHand`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityArticulatedHand) is a controller that is responsible for interfacing with the underlying Windows [hand tracking APIs](/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate) to get information about the joints, pose, and other properties of the hand.</span></span> <span data-ttu-id="dc630-111">È responsabile della trasformazione di questi dati in eventi MRTK pertinenti ,ad esempio chiamando RaisePoseInputChanged o RaiseHandJointsUpdated, e aggiornando il proprio stato interno in modo che le query per restituiranno i dati [`TryGetJointPose`](xref:Microsoft.MixedReality.Toolkit.Input.HandJointUtils.TryGetJointPose%2A) corretti.</span><span class="sxs-lookup"><span data-stu-id="dc630-111">It is responsible for turning this data into relevant MRTK events (for example, by calling RaisePoseInputChanged or RaiseHandJointsUpdated) and by updating its own internal state so that queries for [`TryGetJointPose`](xref:Microsoft.MixedReality.Toolkit.Input.HandJointUtils.TryGetJointPose%2A) will return correct data.</span></span>

<span data-ttu-id="dc630-112">In genere, il ciclo di vita di un controller comporta:</span><span class="sxs-lookup"><span data-stu-id="dc630-112">Generally, a controller's lifecycle will involve:</span></span>

1. <span data-ttu-id="dc630-113">Un controller viene creato da un gestore di dispositivi al rilevamento di una nuova origine( ad esempio, il gestore dei dispositivi rileva e inizia a rilevare una mano).</span><span class="sxs-lookup"><span data-stu-id="dc630-113">A controller gets created by a device manager upon detection of a new source (for example, the device manager detects and starts tracking a hand).</span></span>

2. <span data-ttu-id="dc630-114">Nel ciclo Update() del controller chiama il sistema API sottostante.</span><span class="sxs-lookup"><span data-stu-id="dc630-114">In the controller's Update() loop, it calls into its underlying API system.</span></span>

3. <span data-ttu-id="dc630-115">Nello stesso ciclo di aggiornamento, genera modifiche all'evento di input chiamando direttamente nel sistema di input principale stesso,ad esempio generando HandMeshUpdated o HandJointsUpdated.</span><span class="sxs-lookup"><span data-stu-id="dc630-115">In the same update loop, it raises input event changes by calling directly into the core input system itself (for example, raising HandMeshUpdated, or HandJointsUpdated).</span></span>

## <a name="pointers-and-focus"></a><span data-ttu-id="dc630-116">Puntatori e stato attivo</span><span class="sxs-lookup"><span data-stu-id="dc630-116">Pointers and focus</span></span>

<span data-ttu-id="dc630-117">I puntatori vengono usati per interagire con gli oggetti di gioco.</span><span class="sxs-lookup"><span data-stu-id="dc630-117">Pointers are used to interact with game objects.</span></span> <span data-ttu-id="dc630-118">Questa sezione descrive come vengono creati i puntatori, come vengono aggiornati e come determinano gli oggetti che sono nello stato attivo.</span><span class="sxs-lookup"><span data-stu-id="dc630-118">This section describes how pointers are created, how they get updated, and how they determine the object(s) that are in focus.</span></span> <span data-ttu-id="dc630-119">Verranno inoltre descritti i diversi tipi di puntatori esistenti e gli scenari in cui sono attivi.</span><span class="sxs-lookup"><span data-stu-id="dc630-119">It will also cover the different types of pointers that exist and the scenarios in which they are active.</span></span>

### <a name="pointer-categories"></a><span data-ttu-id="dc630-120">Categorie di puntatori</span><span class="sxs-lookup"><span data-stu-id="dc630-120">Pointer categories</span></span>

<span data-ttu-id="dc630-121">I puntatori rientrano in genere in una delle categorie seguenti:</span><span class="sxs-lookup"><span data-stu-id="dc630-121">Pointers generally fall into one of the following categories:</span></span>

- <span data-ttu-id="dc630-122">**Puntatori lontano**</span><span class="sxs-lookup"><span data-stu-id="dc630-122">**Far pointers**</span></span>

  <span data-ttu-id="dc630-123">Questi tipi di puntatori vengono usati per interagire con oggetti che sono lontani dall'utente (lontano è definito semplicemente "non vicino").</span><span class="sxs-lookup"><span data-stu-id="dc630-123">These types of pointers are used to interact with objects that are far away from the user (far away is defined as simply “not near”).</span></span> <span data-ttu-id="dc630-124">Questi tipi di puntatori in genere esereranno il cast di righe che possono andare lontano nel mondo e consentire all'utente di interagire e modificare gli oggetti che non sono immediatamente accanto a essi.</span><span class="sxs-lookup"><span data-stu-id="dc630-124">These types of pointers generally cast lines that can go far into the world and allow the user to interact with and manipulate objects that are not immediately next to them.</span></span>

- <span data-ttu-id="dc630-125">**Vicino ai puntatori**</span><span class="sxs-lookup"><span data-stu-id="dc630-125">**Near pointers**</span></span>

  <span data-ttu-id="dc630-126">Questi tipi di puntatori vengono usati per interagire con oggetti abbastanza vicini all'utente da afferrare, toccare e manipolare.</span><span class="sxs-lookup"><span data-stu-id="dc630-126">These types of pointers are used to interact with objects that are close enough to the user to grab, touch, and manipulate.</span></span> <span data-ttu-id="dc630-127">In genere, questi tipi di puntatori interagiscono con gli oggetti cercando gli oggetti nelle vicinanze (eseguendo il raycasting a piccole distanze, eseguendo il cast sferico alla ricerca di oggetti nelle vicinanze o enumerando elenchi di oggetti considerati afferrabili/toccabili).</span><span class="sxs-lookup"><span data-stu-id="dc630-127">Generally, these types of pointers interact with objects by looking for objects in the nearby vicinity (either by doing raycasting at small distances, doing spherical casting looking for objects in the vicinity, or enumerating lists of objects that are considered grabbable/touchable).</span></span>

- <span data-ttu-id="dc630-128">**Puntatori di teletrasporto**</span><span class="sxs-lookup"><span data-stu-id="dc630-128">**Teleport pointers**</span></span>

  <span data-ttu-id="dc630-129">Questi tipi di puntatori si collegano al sistema di teletrasporto per gestire lo spostamento dell'utente nella posizione di destinazione del puntatore.</span><span class="sxs-lookup"><span data-stu-id="dc630-129">These types of pointers plug into the teleportation system to handle moving the user to the location targeted by the pointer.</span></span>

## <a name="pointer-mediation"></a><span data-ttu-id="dc630-130">Mediazione dei puntatori</span><span class="sxs-lookup"><span data-stu-id="dc630-130">Pointer mediation</span></span>

<span data-ttu-id="dc630-131">Poiché un singolo controller può avere più puntatori (ad esempio, la mano articolata può avere puntatori di interazione sia vicino che lontano), esiste un componente responsabile della mediazione del puntatore che deve essere attivo.</span><span class="sxs-lookup"><span data-stu-id="dc630-131">Because a single controller can have multiple pointers (for example, the articulated hand can have both near and far interaction pointers), there exists a component that is responsible for mediating which pointer should be active.</span></span>

<span data-ttu-id="dc630-132">Ad esempio, quando la mano dell'utente si avvicina a un pulsante pressabile, l'oggetto dovrebbe smettere di essere visualizzato e [`ShellHandRayPointer`](xref:Microsoft.MixedReality.Toolkit.Input.ShellHandRayPointer) [`PokePointer`](xref:Microsoft.MixedReality.Toolkit.Input.PokePointer) l'oggetto deve essere attivato.</span><span class="sxs-lookup"><span data-stu-id="dc630-132">For example, as the user’s hand approaches a pressable button, the [`ShellHandRayPointer`](xref:Microsoft.MixedReality.Toolkit.Input.ShellHandRayPointer) should stop showing, and the [`PokePointer`](xref:Microsoft.MixedReality.Toolkit.Input.PokePointer) should be engaged.</span></span>

<span data-ttu-id="dc630-133">Viene gestito da , responsabile della determinazione dei puntatori attivi, in base [`DefaultPointerMediator`](xref:Microsoft.MixedReality.Toolkit.Input.DefaultPointerMediator) allo stato di tutti i puntatori.</span><span class="sxs-lookup"><span data-stu-id="dc630-133">This is handled by the [`DefaultPointerMediator`](xref:Microsoft.MixedReality.Toolkit.Input.DefaultPointerMediator), which is responsible for determining which pointers are active, based on the state of all pointers.</span></span> <span data-ttu-id="dc630-134">Una delle operazioni principali è disabilitare i puntatori lontano quando un puntatore vicino è vicino a un oggetto (vedere [`DefaultPointerMediator`](xref:Microsoft.MixedReality.Toolkit.Input.DefaultPointerMediator) ).</span><span class="sxs-lookup"><span data-stu-id="dc630-134">One of the key things this does is disable far pointers when a near pointer is close to an object (please see [`DefaultPointerMediator`](xref:Microsoft.MixedReality.Toolkit.Input.DefaultPointerMediator)).</span></span>

<span data-ttu-id="dc630-135">È possibile fornire un'implementazione alternativa del mediatore puntatore modificando la [`PointerMediator`](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityPointerProfile.PointerMediator) proprietà nel profilo del puntatore.</span><span class="sxs-lookup"><span data-stu-id="dc630-135">It's possible to provide an alternate implementation of the pointer mediator by changing the [`PointerMediator`](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityPointerProfile.PointerMediator) property on the pointer profile.</span></span>

### <a name="how-to-disable-pointers"></a><span data-ttu-id="dc630-136">Come disabilitare i puntatori</span><span class="sxs-lookup"><span data-stu-id="dc630-136">How to disable pointers</span></span>

<span data-ttu-id="dc630-137">Poiché il mediatore di puntatori esegue ogni frame, finisce per controllare lo stato attivo/inattivo di tutti i puntatori.</span><span class="sxs-lookup"><span data-stu-id="dc630-137">Because the pointer mediator runs every frame, it ends up controlling the active / inactive state of all pointers.</span></span> <span data-ttu-id="dc630-138">Pertanto, se si imposta la proprietà IsInteractionEnabled di un puntatore nel codice, il mediatore del puntatore verrà sovrascritto da ogni frame.</span><span class="sxs-lookup"><span data-stu-id="dc630-138">Therefore, if you set a pointer's IsInteractionEnabled property in code, it will get overwritten by the pointer mediator every frame.</span></span> <span data-ttu-id="dc630-139">È invece possibile specificare per [`PointerBehavior`](xref:Microsoft.MixedReality.Toolkit.Input.PointerBehavior) controllare se i puntatori devono essere spenti o spenti manualmente.</span><span class="sxs-lookup"><span data-stu-id="dc630-139">Instead, you can specify the [`PointerBehavior`](xref:Microsoft.MixedReality.Toolkit.Input.PointerBehavior) to control whether pointers should be on or off yourself.</span></span> <span data-ttu-id="dc630-140">Si noti che questa operazione funzionerà solo se si usa l'impostazione [`FocusProvider`](xref:Microsoft.MixedReality.Toolkit.Input.FocusProvider) predefinita e [`DefaultPointerMediator`](xref:Microsoft.MixedReality.Toolkit.Input.DefaultPointerMediator) in MRTK.</span><span class="sxs-lookup"><span data-stu-id="dc630-140">Note that this will only work if you are using the default [`FocusProvider`](xref:Microsoft.MixedReality.Toolkit.Input.FocusProvider) and [`DefaultPointerMediator`](xref:Microsoft.MixedReality.Toolkit.Input.DefaultPointerMediator) in MRTK.</span></span>

#### <a name="example-disable-hand-rays-in-mrtk"></a><span data-ttu-id="dc630-141">Esempio: Disabilitare i raggi della mano in MRTK</span><span class="sxs-lookup"><span data-stu-id="dc630-141">Example: Disable hand rays in MRTK</span></span>

<span data-ttu-id="dc630-142">Il codice seguente disattiva i raggi della mano in MRTK:</span><span class="sxs-lookup"><span data-stu-id="dc630-142">The following code will turn off the hand rays in MRTK:</span></span>

```c#
// Turn off all hand rays
PointerUtils.SetHandRayPointerBehavior(PointerBehavior.AlwaysOff);

// Turn off hand rays for the right hand only
PointerUtils.SetHandRayPointerBehavior(PointerBehavior.AlwaysOff, Handedness.Right);
```

<span data-ttu-id="dc630-143">Il codice seguente restituirà i raggi della mano al comportamento predefinito in MRTK:</span><span class="sxs-lookup"><span data-stu-id="dc630-143">The following code will return hand rays to their default behavior in MRTK:</span></span>

```c#
PointerUtils.SetHandRayPointerBehavior(PointerBehavior.Default);
```

<span data-ttu-id="dc630-144">Il codice seguente forza l'azione dei raggi della mano, indipendentemente dal fatto che sia vicino a un oggetto afferrabile:</span><span class="sxs-lookup"><span data-stu-id="dc630-144">The following code will force hand rays to be on, regardless if near a grabbable:</span></span>

```c#
// Turn off all hand rays
PointerUtils.SetHandRayPointerBehavior(PointerBehavior.AlwaysOn);
```

<span data-ttu-id="dc630-145">Per [`PointerUtils`](xref:Microsoft.MixedReality.Toolkit.Input.PointerUtils) altri [`TurnPointersOnOff`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.DisablePointersExample) esempi, vedere e .</span><span class="sxs-lookup"><span data-stu-id="dc630-145">See [`PointerUtils`](xref:Microsoft.MixedReality.Toolkit.Input.PointerUtils) and [`TurnPointersOnOff`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.DisablePointersExample) for more examples.</span></span>

### <a name="focusprovider"></a><span data-ttu-id="dc630-146">FocusProvider</span><span class="sxs-lookup"><span data-stu-id="dc630-146">FocusProvider</span></span>

<span data-ttu-id="dc630-147">è il workhorse responsabile dell'esecuzione dell'iter sull'elenco di tutti i puntatori e di descrizione dell'oggetto attivo [`FocusProvider`](xref:Microsoft.MixedReality.Toolkit.Input.FocusProvider) per ogni puntatore.</span><span class="sxs-lookup"><span data-stu-id="dc630-147">The [`FocusProvider`](xref:Microsoft.MixedReality.Toolkit.Input.FocusProvider) is the workhorse that is responsible for iterating over the list of all pointers and figuring out what the focused object is for each pointer.</span></span>

<span data-ttu-id="dc630-148">In ogni `Update()` chiamata verrà:</span><span class="sxs-lookup"><span data-stu-id="dc630-148">In each `Update()` call, this will:</span></span>

1. <span data-ttu-id="dc630-149">Aggiornare tutti i puntatori, eseguendo il raycasting e eseguendo il rilevamento degli hit come configurato dal puntatore stesso (ad esempio, il puntatore sphere potrebbe specificare SphereOverlap raycastMode, in modo che FocusProvider eserciti una collisione basata su sfera)</span><span class="sxs-lookup"><span data-stu-id="dc630-149">Update all of the pointers, by raycasting and doing hit detection as-configured by the pointer itself (for example, the sphere pointer could specify the SphereOverlap raycastMode, so FocusProvider will do a sphere-based collision)</span></span>

2. <span data-ttu-id="dc630-150">Aggiornare l'oggetto attivo in base al puntatore(ad esempio, se un oggetto ottiene lo stato attivo, attiva anche eventi per tali oggetti, se un oggetto perde lo stato attivo, attiva lo stato attivo perso e così via).</span><span class="sxs-lookup"><span data-stu-id="dc630-150">Update the focused object on a per-pointer basis (i.e. if an object gained focus, it would also trigger events to those object, if an object lost focus, it would trigger focus lost, etc).</span></span>

### <a name="pointer-configuration-and-lifecycle"></a><span data-ttu-id="dc630-151">Configurazione e ciclo di vita del puntatore</span><span class="sxs-lookup"><span data-stu-id="dc630-151">Pointer configuration and lifecycle</span></span>

<span data-ttu-id="dc630-152">[I puntatori possono essere configurati](../features/input/pointers.md) nella *sezione Puntatori* del profilo di sistema di input.</span><span class="sxs-lookup"><span data-stu-id="dc630-152">[Pointers can be configured](../features/input/pointers.md) in the *Pointers* section of the input system profile.</span></span>

<span data-ttu-id="dc630-153">La durata di un puntatore è in genere la seguente:</span><span class="sxs-lookup"><span data-stu-id="dc630-153">The lifetime of a pointer is generally the following:</span></span>

1. <span data-ttu-id="dc630-154">Un gestore di dispositivi rileverà la presenza di un controller.</span><span class="sxs-lookup"><span data-stu-id="dc630-154">A device manager will detect the presence of a controller.</span></span> <span data-ttu-id="dc630-155">Questo gestore di dispositivi creerà quindi il set di puntatori associati al controller tramite una chiamata a [`RequestPointers`](xref:Microsoft.MixedReality.Toolkit.Input.BaseInputDeviceManager) .</span><span class="sxs-lookup"><span data-stu-id="dc630-155">This device manager will then create the set of pointers associated with the controller via a call to [`RequestPointers`](xref:Microsoft.MixedReality.Toolkit.Input.BaseInputDeviceManager).</span></span>

2. <span data-ttu-id="dc630-156">FocusProvider, nel ciclo Update(), esegue l'iterazione su tutti i puntatori validi ed esegue la logica di rilevamento raycast o hit associata.</span><span class="sxs-lookup"><span data-stu-id="dc630-156">The FocusProvider, in its Update() loop, will iterate over all of the valid pointers and do the associated raycast or hit detection logic.</span></span> <span data-ttu-id="dc630-157">Viene usato per determinare l'oggetto con lo stato attivo da ogni particolare puntatore.</span><span class="sxs-lookup"><span data-stu-id="dc630-157">This is used to determine the object that is focused by each particular pointer.</span></span>

    - <span data-ttu-id="dc630-158">Poiché è possibile avere più origini di input attive contemporaneamente (ad esempio, due mani attive), è anche possibile avere più oggetti che hanno lo stato attivo contemporaneamente.</span><span class="sxs-lookup"><span data-stu-id="dc630-158">Because it's possible to have multiple sources of input active at the same time (for example, two hands active present), it's also possible to have multiple objects that have focus at the same time.</span></span>

3. <span data-ttu-id="dc630-159">Gestione dispositivi, dopo aver scoperto che un'origine del controller è stata persa, errerà i puntatori associati al controller perso.</span><span class="sxs-lookup"><span data-stu-id="dc630-159">The device manager, upon discovering that a controller source was lost, will tear down the pointers associated with the lost controller.</span></span>
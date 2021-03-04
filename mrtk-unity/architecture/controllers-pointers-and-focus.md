---
title: ControllersPointersAndFocus
description: Interazione con i controller, i puntatori e lo stato attivo.
author: cDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, puntatori, controller
ms.openlocfilehash: d35334672ba2b012c7f2040c94cfc7172cdb0cbb
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/03/2021
ms.locfileid: "101782350"
---
# <a name="controllers-pointers-and-focus"></a><span data-ttu-id="884a5-104">Controller, puntatori e stato attivo</span><span class="sxs-lookup"><span data-stu-id="884a5-104">Controllers, pointers, and focus</span></span>

<span data-ttu-id="884a5-105">I controller, i puntatori e lo stato attivo sono concetti di livello più alto che si basano sulle basi stabilite dal sistema di input di base.</span><span class="sxs-lookup"><span data-stu-id="884a5-105">Controllers, pointers, and focus are higher-level concepts that build upon the foundation established by the core input system.</span></span> <span data-ttu-id="884a5-106">Insieme, forniscono un'ampia parte del meccanismo per interagire con gli oggetti nella scena.</span><span class="sxs-lookup"><span data-stu-id="884a5-106">Together, they provide a large portion of the mechanism for interacting with objects in the scene.</span></span>

## <a name="controllers"></a><span data-ttu-id="884a5-107">Controllers</span><span class="sxs-lookup"><span data-stu-id="884a5-107">Controllers</span></span>

<span data-ttu-id="884a5-108">I controller sono rappresentazioni di un controller fisico (6 gradi di libertà, mano articolata e così via).</span><span class="sxs-lookup"><span data-stu-id="884a5-108">Controllers are representations of a physical controller (6-degrees of freedom, articulated hand, etc).</span></span> <span data-ttu-id="884a5-109">Sono creati da Gestione dispositivi e sono responsabili della comunicazione con il sistema sottostante corrispondente e della conversione dei dati in eventi e dati a forma di MRTK.</span><span class="sxs-lookup"><span data-stu-id="884a5-109">They are created by device managers and are responsible for communicating with the corresponding underlying system and translating that data into MRTK-shaped data and events.</span></span>

<span data-ttu-id="884a5-110">Nella piattaforma di realtà mista di Windows, ad esempio, [`WindowsMixedRealityArticulatedHand`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityArticulatedHand) è un controller responsabile dell'interazione con le [API di rilevamento manuale](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate) di Windows sottostanti per ottenere informazioni sui giunti, sulla posa e su altre proprietà della mano.</span><span class="sxs-lookup"><span data-stu-id="884a5-110">For example, on the Windows Mixed Reality platform, the [`WindowsMixedRealityArticulatedHand`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityArticulatedHand) is a controller that is responsible for interfacing with the underlying Windows [hand tracking APIs](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate) to get information about the joints, pose, and other properties of the hand.</span></span> <span data-ttu-id="884a5-111">È responsabile della trasformazione di questi dati in eventi MRTK rilevanti, ad esempio chiamando RaisePoseInputChanged o RaiseHandJointsUpdated, e aggiornando il proprio stato interno in modo che le query per [`TryGetJointPose`](xref:Microsoft.MixedReality.Toolkit.Input.HandJointUtils.TryGetJointPose(TrackedHandJoint,Handedness,MixedRealityPose@)) restituiscano i dati corretti.</span><span class="sxs-lookup"><span data-stu-id="884a5-111">It is responsible for turning this data into relevant MRTK events (for example, by calling RaisePoseInputChanged or RaiseHandJointsUpdated) and by updating its own internal state so that queries for [`TryGetJointPose`](xref:Microsoft.MixedReality.Toolkit.Input.HandJointUtils.TryGetJointPose(TrackedHandJoint,Handedness,MixedRealityPose@)) will return correct data.</span></span>

<span data-ttu-id="884a5-112">In genere, il ciclo di vita di un controller implica:</span><span class="sxs-lookup"><span data-stu-id="884a5-112">Generally, a controller's lifecycle will involve:</span></span>

1. <span data-ttu-id="884a5-113">Un controller viene creato da un gestore di dispositivi al rilevamento di una nuova origine (ad esempio, gestione dispositivi rileva e inizia a tenere traccia di una mano).</span><span class="sxs-lookup"><span data-stu-id="884a5-113">A controller gets created by a device manager upon detection of a new source (for example, the device manager detects and starts tracking a hand).</span></span>

2. <span data-ttu-id="884a5-114">Nel ciclo Update () del controller viene chiamato il sistema API sottostante.</span><span class="sxs-lookup"><span data-stu-id="884a5-114">In the controller's Update() loop, it calls into its underlying API system.</span></span>

3. <span data-ttu-id="884a5-115">Nello stesso ciclo di aggiornamento, genera modifiche all'evento di input chiamando direttamente nel sistema di input principale stesso (ad esempio, la generazione di HandMeshUpdated o HandJointsUpdated).</span><span class="sxs-lookup"><span data-stu-id="884a5-115">In the same update loop, it raises input event changes by calling directly into the core input system itself (for example, raising HandMeshUpdated, or HandJointsUpdated).</span></span>

## <a name="pointers-and-focus"></a><span data-ttu-id="884a5-116">Puntatori e stato attivo</span><span class="sxs-lookup"><span data-stu-id="884a5-116">Pointers and focus</span></span>

<span data-ttu-id="884a5-117">I puntatori vengono usati per interagire con gli oggetti di gioco.</span><span class="sxs-lookup"><span data-stu-id="884a5-117">Pointers are used to interact with game objects.</span></span> <span data-ttu-id="884a5-118">In questa sezione viene descritto il modo in cui vengono creati i puntatori, il modo in cui vengono aggiornati e il modo in cui determinano gli oggetti in stato attivo.</span><span class="sxs-lookup"><span data-stu-id="884a5-118">This section describes how pointers are created, how they get updated, and how they determine the object(s) that are in focus.</span></span> <span data-ttu-id="884a5-119">Verranno inoltre illustrati i diversi tipi di puntatori esistenti e gli scenari in cui sono attivi.</span><span class="sxs-lookup"><span data-stu-id="884a5-119">It will also cover the different types of pointers that exist and the scenarios in which they are active.</span></span>

### <a name="pointer-categories"></a><span data-ttu-id="884a5-120">Categorie di puntatori</span><span class="sxs-lookup"><span data-stu-id="884a5-120">Pointer categories</span></span>

<span data-ttu-id="884a5-121">I puntatori in genere rientrano in una delle categorie seguenti:</span><span class="sxs-lookup"><span data-stu-id="884a5-121">Pointers generally fall into one of the following categories:</span></span>

- <span data-ttu-id="884a5-122">**Puntatori a distanza**</span><span class="sxs-lookup"><span data-stu-id="884a5-122">**Far pointers**</span></span>

  <span data-ttu-id="884a5-123">Questi tipi di puntatori vengono usati per interagire con gli oggetti lontani dall'utente (l'esterno è definito semplicemente come "non vicino").</span><span class="sxs-lookup"><span data-stu-id="884a5-123">These types of pointers are used to interact with objects that are far away from the user (far away is defined as simply “not near”).</span></span> <span data-ttu-id="884a5-124">Questi tipi di puntatori in genere eseguono il cast delle linee che possono andare lontano nel mondo e consentono all'utente di interagire con gli oggetti che non sono immediatamente accanto a essi.</span><span class="sxs-lookup"><span data-stu-id="884a5-124">These types of pointers generally cast lines that can go far into the world and allow the user to interact with and manipulate objects that are not immediately next to them.</span></span>

- <span data-ttu-id="884a5-125">**Near puntatori**</span><span class="sxs-lookup"><span data-stu-id="884a5-125">**Near pointers**</span></span>

  <span data-ttu-id="884a5-126">Questi tipi di puntatori vengono usati per interagire con gli oggetti che sono sufficientemente vicini all'utente per acquisire, toccare e modificare.</span><span class="sxs-lookup"><span data-stu-id="884a5-126">These types of pointers are used to interact with objects that are close enough to the user to grab, touch, and manipulate.</span></span> <span data-ttu-id="884a5-127">In genere, questi tipi di puntatori interagiscono con gli oggetti cercando oggetti nelle vicinanze vicine (eseguendo Raycasting a distanze ridotte, eseguendo il cast sferico cercando gli oggetti in prossimità o enumerando elenchi di oggetti che sono considerati catturabili/toccabili).</span><span class="sxs-lookup"><span data-stu-id="884a5-127">Generally, these types of pointers interact with objects by looking for objects in the nearby vicinity (either by doing raycasting at small distances, doing spherical casting looking for objects in the vicinity, or enumerating lists of objects that are considered grabbable/touchable).</span></span>

- <span data-ttu-id="884a5-128">**Puntatori Teleport**</span><span class="sxs-lookup"><span data-stu-id="884a5-128">**Teleport pointers**</span></span>

  <span data-ttu-id="884a5-129">Questi tipi di puntatori si collegano al sistema di Teleportation per gestire lo spostamento dell'utente nella posizione di destinazione dell'indicatore di misura.</span><span class="sxs-lookup"><span data-stu-id="884a5-129">These types of pointers plug into the teleportation system to handle moving the user to the location targeted by the pointer.</span></span>

## <a name="pointer-mediation"></a><span data-ttu-id="884a5-130">Mediazione puntatore</span><span class="sxs-lookup"><span data-stu-id="884a5-130">Pointer mediation</span></span>

<span data-ttu-id="884a5-131">Poiché un singolo controller può avere più puntatori (ad esempio, la mano articolata può avere puntatori di interazione near e lontani), esiste un componente responsabile della mediazione del puntatore attivo.</span><span class="sxs-lookup"><span data-stu-id="884a5-131">Because a single controller can have multiple pointers (for example, the articulated hand can have both near and far interaction pointers), there exists a component that is responsible for mediating which pointer should be active.</span></span>

<span data-ttu-id="884a5-132">Ad esempio, quando la mano dell'utente si avvicina a un pulsante stampabile, [`ShellHandRayPointer`](xref:Microsoft.MixedReality.Toolkit.Input.ShellHandRayPointer) deve interrompere la visualizzazione e [`PokePointer`](xref:Microsoft.MixedReality.Toolkit.Input.PokePointer) deve essere attivato.</span><span class="sxs-lookup"><span data-stu-id="884a5-132">For example, as the user’s hand approaches a pressable button, the [`ShellHandRayPointer`](xref:Microsoft.MixedReality.Toolkit.Input.ShellHandRayPointer) should stop showing, and the [`PokePointer`](xref:Microsoft.MixedReality.Toolkit.Input.PokePointer) should be engaged.</span></span>

<span data-ttu-id="884a5-133">Questo è gestito da [`DefaultPointerMediator`](xref:Microsoft.MixedReality.Toolkit.Input.DefaultPointerMediator) , che è responsabile della determinazione dei puntatori attivi, in base allo stato di tutti i puntatori.</span><span class="sxs-lookup"><span data-stu-id="884a5-133">This is handled by the [`DefaultPointerMediator`](xref:Microsoft.MixedReality.Toolkit.Input.DefaultPointerMediator), which is responsible for determining which pointers are active, based on the state of all pointers.</span></span> <span data-ttu-id="884a5-134">Uno degli elementi chiave è la disabilitazione di puntatori lontani quando un puntatore vicino è vicino a un oggetto (vedere [`DefaultPointerMediator`](xref:Microsoft.MixedReality.Toolkit.Input.DefaultPointerMediator) ).</span><span class="sxs-lookup"><span data-stu-id="884a5-134">One of the key things this does is disable far pointers when a near pointer is close to an object (please see [`DefaultPointerMediator`](xref:Microsoft.MixedReality.Toolkit.Input.DefaultPointerMediator)).</span></span>

<span data-ttu-id="884a5-135">È possibile fornire un'implementazione alternativa del Mediator del puntatore modificando la [`PointerMediator`](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityPointerProfile.PointerMediator) proprietà sul profilo del puntatore.</span><span class="sxs-lookup"><span data-stu-id="884a5-135">It's possible to provide an alternate implementation of the pointer mediator by changing the [`PointerMediator`](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityPointerProfile.PointerMediator) property on the pointer profile.</span></span>

### <a name="how-to-disable-pointers"></a><span data-ttu-id="884a5-136">Come disabilitare i puntatori</span><span class="sxs-lookup"><span data-stu-id="884a5-136">How to disable pointers</span></span>

<span data-ttu-id="884a5-137">Poiché il Mediator del puntatore esegue ogni frame, termina il controllo dello stato attivo/inattivo di tutti i puntatori.</span><span class="sxs-lookup"><span data-stu-id="884a5-137">Because the pointer mediator runs every frame, it ends up controlling the active / inactive state of all pointers.</span></span> <span data-ttu-id="884a5-138">Se pertanto si imposta la proprietà IsInteractionEnabled di un puntatore nel codice, questa verrà sovrascritta dal Mediatore del puntatore a ogni frame.</span><span class="sxs-lookup"><span data-stu-id="884a5-138">Therefore, if you set a pointer's IsInteractionEnabled property in code, it will get overwritten by the pointer mediator every frame.</span></span> <span data-ttu-id="884a5-139">In alternativa, è possibile specificare [`PointerBehavior`](xref:Microsoft.MixedReality.Toolkit.Input.PointerBehavior) per controllare se i puntatori devono essere attivati o disattivati.</span><span class="sxs-lookup"><span data-stu-id="884a5-139">Instead, you can specify the [`PointerBehavior`](xref:Microsoft.MixedReality.Toolkit.Input.PointerBehavior) to control whether pointers should be on or off yourself.</span></span> <span data-ttu-id="884a5-140">Si noti che questo funzionerà solo se si usano le impostazioni predefinite [`FocusProvider`](xref:Microsoft.MixedReality.Toolkit.Input.FocusProvider) e [`DefaultPointerMediator`](xref:Microsoft.MixedReality.Toolkit.Input.DefaultPointerMediator) in MRTK.</span><span class="sxs-lookup"><span data-stu-id="884a5-140">Note that this will only work if you are using the default [`FocusProvider`](xref:Microsoft.MixedReality.Toolkit.Input.FocusProvider) and [`DefaultPointerMediator`](xref:Microsoft.MixedReality.Toolkit.Input.DefaultPointerMediator) in MRTK.</span></span>

#### <a name="example-disable-hand-rays-in-mrtk"></a><span data-ttu-id="884a5-141">Esempio: disabilitare i raggi mano in MRTK</span><span class="sxs-lookup"><span data-stu-id="884a5-141">Example: Disable hand rays in MRTK</span></span>

<span data-ttu-id="884a5-142">Il codice seguente disattiva i raggi mano in MRTK:</span><span class="sxs-lookup"><span data-stu-id="884a5-142">The following code will turn off the hand rays in MRTK:</span></span>

```c#
// Turn off all hand rays
PointerUtils.SetHandRayPointerBehavior(PointerBehavior.AlwaysOff);

// Turn off hand rays for the right hand only
PointerUtils.SetHandRayPointerBehavior(PointerBehavior.AlwaysOff, Handedness.Right);
```

<span data-ttu-id="884a5-143">Il codice seguente restituirà i raggi di mano al comportamento predefinito in MRTK:</span><span class="sxs-lookup"><span data-stu-id="884a5-143">The following code will return hand rays to their default behavior in MRTK:</span></span>

```c#
PointerUtils.SetHandRayPointerBehavior(PointerBehavior.Default);
```

<span data-ttu-id="884a5-144">Il codice seguente forza l'utilizzo dei raggi di mano, indipendentemente dal fatto che si avvicini a un'acquisizione:</span><span class="sxs-lookup"><span data-stu-id="884a5-144">The following code will force hand rays to be on, regardless if near a grabbable:</span></span>

```c#
// Turn off all hand rays
PointerUtils.SetHandRayPointerBehavior(PointerBehavior.AlwaysOn);
```

<span data-ttu-id="884a5-145">[`PointerUtils`](xref:Microsoft.MixedReality.Toolkit.Input.PointerUtils) [`TurnPointersOnOff`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.DisablePointersExample) Per altri esempi, vedere e.</span><span class="sxs-lookup"><span data-stu-id="884a5-145">See [`PointerUtils`](xref:Microsoft.MixedReality.Toolkit.Input.PointerUtils) and [`TurnPointersOnOff`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.DisablePointersExample) for more examples.</span></span>

### <a name="focusprovider"></a><span data-ttu-id="884a5-146">FocusProvider</span><span class="sxs-lookup"><span data-stu-id="884a5-146">FocusProvider</span></span>

<span data-ttu-id="884a5-147">[`FocusProvider`](xref:Microsoft.MixedReality.Toolkit.Input.FocusProvider)È il compito che è responsabile dell'iterazione dell'elenco di tutti i puntatori e di capire quale sia l'oggetto mirato per ogni puntatore.</span><span class="sxs-lookup"><span data-stu-id="884a5-147">The [`FocusProvider`](xref:Microsoft.MixedReality.Toolkit.Input.FocusProvider) is the workhorse that is responsible for iterating over the list of all pointers and figuring out what the focused object is for each pointer.</span></span>

<span data-ttu-id="884a5-148">In ogni `Update()` chiamata verrà:</span><span class="sxs-lookup"><span data-stu-id="884a5-148">In each `Update()` call, this will:</span></span>

1. <span data-ttu-id="884a5-149">Aggiornare tutti i puntatori, da Raycasting ed eseguire il rilevamento dei riscontri come configurati dal puntatore stesso. ad esempio, il puntatore a sfera potrebbe specificare SphereOverlap raycastMode, quindi FocusProvider eseguirà un conflitto basato su sfera)</span><span class="sxs-lookup"><span data-stu-id="884a5-149">Update all of the pointers, by raycasting and doing hit detection as-configured by the pointer itself (for example, the sphere pointer could specify the SphereOverlap raycastMode, so FocusProvider will do a sphere-based collision)</span></span>

2. <span data-ttu-id="884a5-150">Aggiornare l'oggetto con lo stato attivo per ogni puntatore (ad esempio, se un oggetto ha ottenuto lo stato attivo, genera anche gli eventi per tali oggetti, se un oggetto ha perso lo stato attivo, potrebbe attivare la perdita dello stato attivo e così via).</span><span class="sxs-lookup"><span data-stu-id="884a5-150">Update the focused object on a per-pointer basis (i.e. if an object gained focus, it would also trigger events to those object, if an object lost focus, it would trigger focus lost, etc).</span></span>

### <a name="pointer-configuration-and-lifecycle"></a><span data-ttu-id="884a5-151">Configurazione e ciclo di vita del puntatore</span><span class="sxs-lookup"><span data-stu-id="884a5-151">Pointer configuration and lifecycle</span></span>

<span data-ttu-id="884a5-152">I [puntatori possono essere configurati](../features/input/pointers.md) nella sezione *puntatori* del profilo di sistema di input.</span><span class="sxs-lookup"><span data-stu-id="884a5-152">[Pointers can be configured](../features/input/pointers.md) in the *Pointers* section of the input system profile.</span></span>

<span data-ttu-id="884a5-153">La durata di un puntatore è generalmente la seguente:</span><span class="sxs-lookup"><span data-stu-id="884a5-153">The lifetime of a pointer is generally the following:</span></span>

1. <span data-ttu-id="884a5-154">Una gestione dispositivi rileverà la presenza di un controller.</span><span class="sxs-lookup"><span data-stu-id="884a5-154">A device manager will detect the presence of a controller.</span></span> <span data-ttu-id="884a5-155">Questo gestore di dispositivi creerà quindi il set di puntatori associati al controller tramite una chiamata a [`RequestPointers`](xref:Microsoft.MixedReality.Toolkit.Input.BaseInputDeviceManager) .</span><span class="sxs-lookup"><span data-stu-id="884a5-155">This device manager will then create the set of pointers associated with the controller via a call to [`RequestPointers`](xref:Microsoft.MixedReality.Toolkit.Input.BaseInputDeviceManager).</span></span>

2. <span data-ttu-id="884a5-156">FocusProvider, nel ciclo di aggiornamento (), eseguirà l'iterazione di tutti i puntatori validi ed eseguirà la logica di rilevamento Raycast o hit associato.</span><span class="sxs-lookup"><span data-stu-id="884a5-156">The FocusProvider, in its Update() loop, will iterate over all of the valid pointers and do the associated raycast or hit detection logic.</span></span> <span data-ttu-id="884a5-157">Viene utilizzato per determinare l'oggetto che è stato concentrato da ogni particolare puntatore.</span><span class="sxs-lookup"><span data-stu-id="884a5-157">This is used to determine the object that is focused by each particular pointer.</span></span>

    - <span data-ttu-id="884a5-158">Poiché è possibile avere più origini di input attive allo stesso tempo (ad esempio, due mani attive presenti), è anche possibile avere più oggetti con lo stato attivo nello stesso momento.</span><span class="sxs-lookup"><span data-stu-id="884a5-158">Because it's possible to have multiple sources of input active at the same time (for example, two hands active present), it's also possible to have multiple objects that have focus at the same time.</span></span>

3. <span data-ttu-id="884a5-159">Gestione dispositivi, quando si scopre che un'origine del controller è stata persa, chiuderà i puntatori associati al controller perso.</span><span class="sxs-lookup"><span data-stu-id="884a5-159">The device manager, upon discovering that a controller source was lost, will tear down the pointers associated with the lost controller.</span></span>

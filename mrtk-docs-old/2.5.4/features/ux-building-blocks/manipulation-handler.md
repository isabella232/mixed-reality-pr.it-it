---
title: ManipulationHandler
description: Documentazione sul gestore di manipolazione in MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, manipolazione,
ms.openlocfilehash: f294516b7446934f4f390055644b32c99a564426
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/03/2021
ms.locfileid: "101781945"
---
# <a name="manipulation-handler"></a><span data-ttu-id="b9da2-104">Gestore di manipolazione</span><span class="sxs-lookup"><span data-stu-id="b9da2-104">Manipulation handler</span></span>

![Gestore di manipolazione](../images/manipulation-handler/MRTK_Manipulation_Main.png)

<span data-ttu-id="b9da2-106">Lo script *ManipulationHandler* consente a un oggetto di essere reso mobile, scalabile e girevole usando uno o due mani.</span><span class="sxs-lookup"><span data-stu-id="b9da2-106">The *ManipulationHandler* script allows for an object to be made movable, scalable, and rotatable using one or two hands.</span></span> <span data-ttu-id="b9da2-107">La manipolazione può essere limitata in modo da consentire solo determinati tipi di trasformazione.</span><span class="sxs-lookup"><span data-stu-id="b9da2-107">Manipulation can be restricted so that it only allows certain kinds of transformation.</span></span> <span data-ttu-id="b9da2-108">Lo script funziona con vari tipi di input, tra cui l'input mano articolato HoloLens 2, l'input del movimento HoloLens (primo generazione) e l'input del controller di movimento per auricolari immersivi.</span><span class="sxs-lookup"><span data-stu-id="b9da2-108">The script works with various types of inputs including HoloLens 2 articulated hand input, hand-rays, HoloLens (1st gen) gesture input, and immersive headset motion controller input.</span></span>

## <a name="how-to-use-the-manipulation-handler"></a><span data-ttu-id="b9da2-109">Come utilizzare il gestore di manipolazione</span><span class="sxs-lookup"><span data-stu-id="b9da2-109">How to use the manipulation handler</span></span>

<span data-ttu-id="b9da2-110">Aggiungere il `ManipulationHandler` componente script a un GameObject.</span><span class="sxs-lookup"><span data-stu-id="b9da2-110">Add the `ManipulationHandler` script component to a GameObject.</span></span> <span data-ttu-id="b9da2-111">Assicurarsi di aggiungere anche un Collider all'oggetto, associando i relativi limiti afferrabili.</span><span class="sxs-lookup"><span data-stu-id="b9da2-111">Make sure to also add a collider to the object, matching its grabbable bounds.</span></span>

<span data-ttu-id="b9da2-112">Per fare in modo che l'oggetto risponda all'input della mano quasi articolato, aggiungere `NearInteractionGrabbable` anche lo script.</span><span class="sxs-lookup"><span data-stu-id="b9da2-112">To make the object respond to near articulated hand input, add the `NearInteractionGrabbable` script as well.</span></span>

![Gestore di manipolazione](../images/manipulation-handler/MRTK_ManipulationHandler_Howto.png)

## <a name="inspector-properties"></a><span data-ttu-id="b9da2-114">Proprietà di Inspector</span><span class="sxs-lookup"><span data-stu-id="b9da2-114">Inspector properties</span></span>

<img src="../images/manipulation-handler/MRTK_ManipulationHandler_Structure.png" width="450" alt="Manipulation Handler structure">

<span data-ttu-id="b9da2-115">**Trasformazione host** Trasformazione che verrà trascinata.</span><span class="sxs-lookup"><span data-stu-id="b9da2-115">**Host Transform** Transform that will be dragged.</span></span> <span data-ttu-id="b9da2-116">Il valore predefinito è l'oggetto del componente.</span><span class="sxs-lookup"><span data-stu-id="b9da2-116">Defaults to the object of the component.</span></span>

<span data-ttu-id="b9da2-117">**Tipo di manipolazione** Specifica se l'oggetto può essere modificato usando una sola mano, due mani o entrambe.</span><span class="sxs-lookup"><span data-stu-id="b9da2-117">**Manipulation Type** Specifies whether the object can be manipulated using one hand, two hands, or both.</span></span>

* <span data-ttu-id="b9da2-118">*Una sola mano*</span><span class="sxs-lookup"><span data-stu-id="b9da2-118">*One handed only*</span></span>
* <span data-ttu-id="b9da2-119">*Due solo mano*</span><span class="sxs-lookup"><span data-stu-id="b9da2-119">*Two handed only*</span></span>
* <span data-ttu-id="b9da2-120">*Una e due passate*</span><span class="sxs-lookup"><span data-stu-id="b9da2-120">*One and Two handed*</span></span>

<span data-ttu-id="b9da2-121">**Tipo di manipolazione a due mano**</span><span class="sxs-lookup"><span data-stu-id="b9da2-121">**Two Handed Manipulation Type**</span></span>

* <span data-ttu-id="b9da2-122">*Scala*: è consentita solo la scalabilità.</span><span class="sxs-lookup"><span data-stu-id="b9da2-122">*Scale*: Only scaling is allowed.</span></span>
* <span data-ttu-id="b9da2-123">*Rotazione*: è consentita solo la rotazione.</span><span class="sxs-lookup"><span data-stu-id="b9da2-123">*Rotate*: Only rotation is allowed.</span></span>
* <span data-ttu-id="b9da2-124">*Sposta scala*: lo spostamento e il ridimensionamento sono consentiti.</span><span class="sxs-lookup"><span data-stu-id="b9da2-124">*Move Scale*: Moving and scaling is allowed.</span></span>
* <span data-ttu-id="b9da2-125">*Spostamento ruotare*: lo spostamento e la rotazione sono consentiti.</span><span class="sxs-lookup"><span data-stu-id="b9da2-125">*Move Rotate*: Moving and rotating is allowed.</span></span>
* <span data-ttu-id="b9da2-126">*Ridimensiona scala*: è consentito ruotare e ridimensionare.</span><span class="sxs-lookup"><span data-stu-id="b9da2-126">*Rotate Scale*: Rotating and scaling is allowed.</span></span>
* <span data-ttu-id="b9da2-127">*Sposta scala ruota*: lo spostamento, la rotazione e il ridimensionamento sono consentiti.</span><span class="sxs-lookup"><span data-stu-id="b9da2-127">*Move Rotate Scale*: Moving, rotating and scaling is allowed.</span></span>

![Gestore di manipolazione](../images/manipulation-handler/MRTK_ManipulationHandler_TwoHanded.jpg)

<span data-ttu-id="b9da2-129">**Consenti manipolazione a lungo** Specifica se è possibile eseguire la manipolazione utilizzando l'interazione con i puntatori.</span><span class="sxs-lookup"><span data-stu-id="b9da2-129">**Allow Far Manipulation** Specifies whether manipulation can be done using far interaction with pointers.</span></span>

<span data-ttu-id="b9da2-130">**Modalità di rotazione a una mano vicino** Specifica come si comporterà l'oggetto quando viene afferrato con una mano o un controller vicino a.</span><span class="sxs-lookup"><span data-stu-id="b9da2-130">**One Hand Rotation Mode Near** Specifies how the object will behave when it is being grabbed with one hand / controller near.</span></span>

<span data-ttu-id="b9da2-131">**Modalità di rotazione a una mano** Specifica come si comporterà l'oggetto quando viene afferrato con una mano/controller a distanza.</span><span class="sxs-lookup"><span data-stu-id="b9da2-131">**One Hand Rotation Mode Far** Specifies how the object will behave when it is being grabbed with one hand / controller at distance.</span></span>

<span data-ttu-id="b9da2-132">**Opzioni modalità rotazione a mano singola** Specifica il modo in cui l'oggetto verrà ruotato quando viene afferrato con una sola mano.</span><span class="sxs-lookup"><span data-stu-id="b9da2-132">**One Hand Rotation Mode Options** Specifies how the object will rotate when it is being grabbed with one hand.</span></span>

* <span data-ttu-id="b9da2-133">*Mantieni rotazione originale*: non ruota l'oggetto durante lo spostamento</span><span class="sxs-lookup"><span data-stu-id="b9da2-133">*Maintain original rotation*: Does not rotate object as it is being moved</span></span>
* <span data-ttu-id="b9da2-134">*Mantieni la rotazione per l'utente*: mantiene la rotazione originale dell'oggetto per l'asse X/Y per l'utente</span><span class="sxs-lookup"><span data-stu-id="b9da2-134">*Maintain rotation to user*: Maintains the object's original rotation for X/Y axis to the user</span></span>
* <span data-ttu-id="b9da2-135">*Allineamento di gravità mantenere la rotazione all'utente*: mantiene la rotazione originale dell'oggetto per l'utente, ma rende l'oggetto verticale.</span><span class="sxs-lookup"><span data-stu-id="b9da2-135">*Gravity aligned maintain rotation to user*: Maintains object's original rotation to user, but makes the object vertical.</span></span> <span data-ttu-id="b9da2-136">Utile per gli oggetti con un controllo Bounds.</span><span class="sxs-lookup"><span data-stu-id="b9da2-136">Useful for objects with a bounds control.</span></span>
* <span data-ttu-id="b9da2-137">*Utente viso*: assicura che l'oggetto faccia sempre fronte all'utente.</span><span class="sxs-lookup"><span data-stu-id="b9da2-137">*Face user*: Ensures object always faces the user.</span></span> <span data-ttu-id="b9da2-138">Utile per gli slate o i pannelli.</span><span class="sxs-lookup"><span data-stu-id="b9da2-138">Useful for slates/panels.</span></span>
* <span data-ttu-id="b9da2-139">*Faccia fuori dall'utente*: assicura che l'oggetto faccia sempre fronte all'utente.</span><span class="sxs-lookup"><span data-stu-id="b9da2-139">*Face away from user*: Ensures object always faces away from user.</span></span> <span data-ttu-id="b9da2-140">Utile per gli slate o i pannelli che sono configurati all'indietro.</span><span class="sxs-lookup"><span data-stu-id="b9da2-140">Useful for slates/panels that are configured backwards.</span></span>
* <span data-ttu-id="b9da2-141">*Ruota intorno al centro oggetti*: funziona solo per le mani o i controller articolati.</span><span class="sxs-lookup"><span data-stu-id="b9da2-141">*Rotate about object center*:  Only works for articulated hands/controllers.</span></span> <span data-ttu-id="b9da2-142">Ruotare l'oggetto usando la rotazione della mano o del controller, ma il punto centrale dell'oggetto.</span><span class="sxs-lookup"><span data-stu-id="b9da2-142">Rotate object using rotation of the hand/controller, but about the object center point.</span></span> <span data-ttu-id="b9da2-143">Utile per il controllo a distanza.</span><span class="sxs-lookup"><span data-stu-id="b9da2-143">Useful for inspecting at a distance.</span></span>
* <span data-ttu-id="b9da2-144">*Ruota intorno al punto di* controllo: funziona solo per le mani e i controller articolati.</span><span class="sxs-lookup"><span data-stu-id="b9da2-144">*Rotate about grab point*:  Only works for articulated hands/controllers.</span></span> <span data-ttu-id="b9da2-145">Ruotare l'oggetto come se fosse gestito da mano/controller.</span><span class="sxs-lookup"><span data-stu-id="b9da2-145">Rotate object as if it was being held by hand/controller.</span></span> <span data-ttu-id="b9da2-146">Utile per l'ispezione.</span><span class="sxs-lookup"><span data-stu-id="b9da2-146">Useful for inspection.</span></span>

<span data-ttu-id="b9da2-147">**Comportamento della versione** Quando viene rilasciato un oggetto, specificarne il comportamento di spostamento fisico.</span><span class="sxs-lookup"><span data-stu-id="b9da2-147">**Release Behavior** When an object is released, specify its physical movement behavior.</span></span> <span data-ttu-id="b9da2-148">Richiede che un componente rigidbody sia su tale oggetto.</span><span class="sxs-lookup"><span data-stu-id="b9da2-148">Requires a rigidbody component to be on that object.</span></span>

* <span data-ttu-id="b9da2-149">*Nothing*</span><span class="sxs-lookup"><span data-stu-id="b9da2-149">*Nothing*</span></span>
* <span data-ttu-id="b9da2-150">*Tutto*</span><span class="sxs-lookup"><span data-stu-id="b9da2-150">*Everything*</span></span>
* <span data-ttu-id="b9da2-151">*Mantieni velocità*</span><span class="sxs-lookup"><span data-stu-id="b9da2-151">*Keep Velocity*</span></span>
* <span data-ttu-id="b9da2-152">*Mantieni velocità angolare*</span><span class="sxs-lookup"><span data-stu-id="b9da2-152">*Keep Angular Velocity*</span></span>

<span data-ttu-id="b9da2-153">**Vincoli sulla rotazione** Specifica su quale asse ruotare l'oggetto quando si interagisce con.</span><span class="sxs-lookup"><span data-stu-id="b9da2-153">**Constraints on Rotation** Specifies on which axis the object will rotate when interacted with.</span></span>

* <span data-ttu-id="b9da2-154">*Nessuno*</span><span class="sxs-lookup"><span data-stu-id="b9da2-154">*None*</span></span>
* <span data-ttu-id="b9da2-155">*Solo asse X*</span><span class="sxs-lookup"><span data-stu-id="b9da2-155">*X-Axis Only*</span></span>
* <span data-ttu-id="b9da2-156">*Solo asse Y*</span><span class="sxs-lookup"><span data-stu-id="b9da2-156">*Y-Axis Only*</span></span>
* <span data-ttu-id="b9da2-157">*Solo asse Z*</span><span class="sxs-lookup"><span data-stu-id="b9da2-157">*Z-Axis Only*</span></span>

<span data-ttu-id="b9da2-158">**Usa spazio locale per il vincolo** Interruttore per passare tra l'applicazione di vincoli rispetto all'asse dello spazio globale o l'asse dello spazio locale.</span><span class="sxs-lookup"><span data-stu-id="b9da2-158">**Use Local Space For Constraint** A toggle to switch between applying constraints in respect to world-space axis, or local space axis.</span></span>

<span data-ttu-id="b9da2-159">**Vincoli sullo spostamento**</span><span class="sxs-lookup"><span data-stu-id="b9da2-159">**Constraints on Movement**</span></span>

* <span data-ttu-id="b9da2-160">*Nessuno*</span><span class="sxs-lookup"><span data-stu-id="b9da2-160">*None*</span></span>
* <span data-ttu-id="b9da2-161">*Correggi distanza da capo*</span><span class="sxs-lookup"><span data-stu-id="b9da2-161">*Fix distance from head*</span></span>

<span data-ttu-id="b9da2-162">**Smoothing attivo** Specifica se la smussatura è attiva.</span><span class="sxs-lookup"><span data-stu-id="b9da2-162">**Smoothing Active** Specifies whether smoothing is active.</span></span>

<span data-ttu-id="b9da2-163">**Uniformità della quantità di una mano** Quantità di smussatura da applicare allo spostamento, alla scala, alla rotazione.</span><span class="sxs-lookup"><span data-stu-id="b9da2-163">**Smoothing Amount One Hand** Amount of smoothing to apply to the movement, scale, rotation.</span></span> <span data-ttu-id="b9da2-164">L'uniformità di 0 significa nessuna smussatura.</span><span class="sxs-lookup"><span data-stu-id="b9da2-164">Smoothing of 0 means no smoothing.</span></span> <span data-ttu-id="b9da2-165">Il valore max significa nessuna modifica al valore.</span><span class="sxs-lookup"><span data-stu-id="b9da2-165">Max value means no change to value.</span></span>

## <a name="events"></a><span data-ttu-id="b9da2-166">Eventi</span><span class="sxs-lookup"><span data-stu-id="b9da2-166">Events</span></span>

<span data-ttu-id="b9da2-167">Il gestore di manipolazione fornisce gli eventi seguenti:</span><span class="sxs-lookup"><span data-stu-id="b9da2-167">Manipulation handler provides the following events:</span></span>

* <span data-ttu-id="b9da2-168">*OnManipulationStarted*: generato all'avvio della manipolazione.</span><span class="sxs-lookup"><span data-stu-id="b9da2-168">*OnManipulationStarted*: Fired when manipulation starts.</span></span>
* <span data-ttu-id="b9da2-169">*OnManipulationEnded*: viene attivato al termine della manipolazione.</span><span class="sxs-lookup"><span data-stu-id="b9da2-169">*OnManipulationEnded*: Fires when the manipulation ends.</span></span>
* <span data-ttu-id="b9da2-170">*OnHoverStarted*: viene attivato quando una mano o un controller passa il mouse sul manipolabile, quasi o lontano.</span><span class="sxs-lookup"><span data-stu-id="b9da2-170">*OnHoverStarted*: Fires when a hand / controller hovers the manipulatable, near or far.</span></span>
* <span data-ttu-id="b9da2-171">*OnHoverEnded*: viene attivato quando una mano o un controller Annulla il passaggio del mouse sul manipolabile, quasi o lontano.</span><span class="sxs-lookup"><span data-stu-id="b9da2-171">*OnHoverEnded*: Fires when a hand / controller un-hovers the manipulatable, near or far.</span></span>

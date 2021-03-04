---
title: README_ObjectManipulator
description: Come usare il manipolatore di oggetti in MRTK
author: thalbern
ms.author: bethalha
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, manipolazione degli oggetti,
ms.openlocfilehash: 0e315c62261febd535452fb21bde4d56a585b295
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/03/2021
ms.locfileid: "101783017"
---
# <a name="object-manipulator"></a><span data-ttu-id="80f96-104">Manipolatore di oggetti</span><span class="sxs-lookup"><span data-stu-id="80f96-104">Object manipulator</span></span>

![Manipolatore oggetto principale](Images/ManipulationHandler/MRTK_Manipulation_Main.png)

<span data-ttu-id="80f96-106">*ObjectManipulator* è il nuovo componente per il comportamento di manipolazione, disponibile in precedenza in *ManipulationHandler*.</span><span class="sxs-lookup"><span data-stu-id="80f96-106">The *ObjectManipulator* is the new component for manipulation behaviour, previously found in *ManipulationHandler*.</span></span> <span data-ttu-id="80f96-107">Il manipolatore di oggetti apporta diversi miglioramenti e semplificazioni.</span><span class="sxs-lookup"><span data-stu-id="80f96-107">The object manipulator makes a number of improvements and simplifications.</span></span> <span data-ttu-id="80f96-108">Questo componente sostituisce il gestore di manipolazione, che verrà deprecato.</span><span class="sxs-lookup"><span data-stu-id="80f96-108">This component is a replacement for the manipulation handler, which will be deprecated.</span></span>

<span data-ttu-id="80f96-109">Lo script *ObjectManipulator* rende un oggetto mobile, scalabile e girevole usando uno o due mani.</span><span class="sxs-lookup"><span data-stu-id="80f96-109">The *ObjectManipulator* script makes an object movable, scalable, and rotatable using one or two hands.</span></span> <span data-ttu-id="80f96-110">Il manipolatore di oggetti può essere configurato per controllare la modalità di risposta dell'oggetto a diversi input.</span><span class="sxs-lookup"><span data-stu-id="80f96-110">The object manipulator can be configured to control how the object will respond to various inputs.</span></span> <span data-ttu-id="80f96-111">Lo script dovrebbe funzionare con la maggior parte delle forme di interazione, ad esempio HoloLens 2, a mano articolata, HoloLens 2, raggi mano, HoloLens 1 sguardo e movimenti e input del controller di movimento dell'auricolare.</span><span class="sxs-lookup"><span data-stu-id="80f96-111">The script should work with most forms of interaction, such as HoloLens 2 articulated hand, HoloLens 2 hand rays, HoloLens 1 gaze and gestures and immersive headset motion controller input.</span></span>

## <a name="how-to-use-the-object-manipulator"></a><span data-ttu-id="80f96-112">Come utilizzare il manipolatore di oggetti</span><span class="sxs-lookup"><span data-stu-id="80f96-112">How to use the object manipulator</span></span>

<span data-ttu-id="80f96-113">Per usare il manipolatore di oggetti, aggiungere prima il `ObjectManipulator` componente script a un GameObject.</span><span class="sxs-lookup"><span data-stu-id="80f96-113">To use the object manipulator, first add the `ObjectManipulator` script component to a GameObject.</span></span> <span data-ttu-id="80f96-114">Assicurarsi di aggiungere anche un Collider all'oggetto, associando i relativi limiti afferrabili.</span><span class="sxs-lookup"><span data-stu-id="80f96-114">Make sure to also add a collider to the object, matching its grabbable bounds.</span></span>

<span data-ttu-id="80f96-115">Per fare in modo che l'oggetto risponda all'input della mano quasi articolato, aggiungere `NearInteractionGrabbable` anche lo script.</span><span class="sxs-lookup"><span data-stu-id="80f96-115">To make the object respond to near articulated hand input, add the `NearInteractionGrabbable` script as well.</span></span>

<span data-ttu-id="80f96-116">Il comportamento fisico può essere abilitato per il manipolatore di oggetti aggiungendo un componente rigidbody all'oggetto.</span><span class="sxs-lookup"><span data-stu-id="80f96-116">Physics behaviour can be enabled for the object manipulator by adding a rigidbody component to the object.</span></span> <span data-ttu-id="80f96-117">Il comportamento fisico abilitato aggiungendo questo componente viene discusso in modo più dettagliato in [*fisica e collisioni*](#physics-and-collisions).</span><span class="sxs-lookup"><span data-stu-id="80f96-117">Physics behaviour enabled by adding this component is discussed in greater detail in [*Physics and collisions*](#physics-and-collisions).</span></span>

<span data-ttu-id="80f96-118">Inoltre, la manipolazione può essere vincolata dall'aggiunta di componenti di [vincoli di manipolazione](#transform-constraints) all'oggetto.</span><span class="sxs-lookup"><span data-stu-id="80f96-118">As well as this, manipulation can be constrained by adding [manipulation constraint components](#transform-constraints) to the object.</span></span> <span data-ttu-id="80f96-119">Si tratta di componenti speciali che funzionano con la manipolazione e modificano in qualche modo il comportamento di manipolazione.</span><span class="sxs-lookup"><span data-stu-id="80f96-119">These are special components that work with manipulation and change the manipulation behaviour in some way.</span></span>

![Gestore di manipolazione](Images/ObjectManipulator/MRTK_ObjectManipulator_Howto.png)

## <a name="inspector-properties-and-fields"></a><span data-ttu-id="80f96-121">Proprietà e campi di Inspector</span><span class="sxs-lookup"><span data-stu-id="80f96-121">Inspector properties and fields</span></span>

<img src="Images/ObjectManipulator/MRTK_ObjectManipulator_Structure.png" width="450" alt="Object Manipulator Structure">

### <a name="general-properties"></a><span data-ttu-id="80f96-122">Proprietà generali</span><span class="sxs-lookup"><span data-stu-id="80f96-122">General properties</span></span>

#### <a name="host-transform"></a><span data-ttu-id="80f96-123">Trasformazione host</span><span class="sxs-lookup"><span data-stu-id="80f96-123">Host transform</span></span>

<span data-ttu-id="80f96-124">Trasformazione dell'oggetto che verrà modificato.</span><span class="sxs-lookup"><span data-stu-id="80f96-124">The object transform that will be manipulated.</span></span> <span data-ttu-id="80f96-125">Il valore predefinito è l'oggetto del componente.</span><span class="sxs-lookup"><span data-stu-id="80f96-125">Defaults to the object of the component.</span></span>

#### <a name="manipulation-type"></a><span data-ttu-id="80f96-126">Tipo di manipolazione</span><span class="sxs-lookup"><span data-stu-id="80f96-126">Manipulation type</span></span>

<span data-ttu-id="80f96-127">Specifica se l'oggetto può essere modificato usando una sola mano o due mani.</span><span class="sxs-lookup"><span data-stu-id="80f96-127">Specifies whether the object can be manipulated using one hand or two hands.</span></span> <span data-ttu-id="80f96-128">Poiché questa proprietà è un flag, è possibile selezionare entrambe le opzioni.</span><span class="sxs-lookup"><span data-stu-id="80f96-128">Because this property is a flag, both options can be selected.</span></span>

- <span data-ttu-id="80f96-129">*Uno gestito*: Abilita una manipolazione gestita se selezionata.</span><span class="sxs-lookup"><span data-stu-id="80f96-129">*One handed*: Enables one handed manipulation if selected.</span></span>
- <span data-ttu-id="80f96-130">*Due gestite*: Abilita due manipolazioni gestite, se selezionate.</span><span class="sxs-lookup"><span data-stu-id="80f96-130">*Two handed*: Enables two handed manipulation if selected.</span></span>

#### <a name="allow-far-manipulation"></a><span data-ttu-id="80f96-131">Consenti manipolazione a lungo</span><span class="sxs-lookup"><span data-stu-id="80f96-131">Allow far manipulation</span></span>

<span data-ttu-id="80f96-132">Specifica se è possibile eseguire la manipolazione utilizzando l'interazione con i puntatori.</span><span class="sxs-lookup"><span data-stu-id="80f96-132">Specifies whether manipulation can be done using far interaction with pointers.</span></span>

### <a name="one-handed-manipulation-properties"></a><span data-ttu-id="80f96-133">Proprietà di manipolazione a una mano</span><span class="sxs-lookup"><span data-stu-id="80f96-133">One handed manipulation properties</span></span>

#### <a name="one-hand-rotation-mode-near"></a><span data-ttu-id="80f96-134">Modalità di rotazione a una mano vicino</span><span class="sxs-lookup"><span data-stu-id="80f96-134">One hand rotation mode near</span></span>

<span data-ttu-id="80f96-135">Specifica come si comporterà l'oggetto quando viene afferrato con una mano vicino a.</span><span class="sxs-lookup"><span data-stu-id="80f96-135">Specifies how the object will behave when it is being grabbed with one hand near.</span></span> <span data-ttu-id="80f96-136">Queste opzioni funzionano solo per le mani articolate.</span><span class="sxs-lookup"><span data-stu-id="80f96-136">These options only work for articulated hands.</span></span>

- <span data-ttu-id="80f96-137">*Ruota intorno al centro oggetti*: l'oggetto ruota usando la rotazione della mano, ma il punto centrale dell'oggetto.</span><span class="sxs-lookup"><span data-stu-id="80f96-137">*Rotate about object center*: Object rotates using rotation of the hand, but about the object center point.</span></span> <span data-ttu-id="80f96-138">L'oggetto comparirà in modo che lo spostamento risulti minore durante la rotazione, ma potrebbe esserci una sensazione di disconnessione tra la mano e l'oggetto.</span><span class="sxs-lookup"><span data-stu-id="80f96-138">The object will appear to move less as it rotates, but there may be a feeling of disconnection between the hand and the object.</span></span> <span data-ttu-id="80f96-139">Più utile per l'interazione di gran lunga.</span><span class="sxs-lookup"><span data-stu-id="80f96-139">More useful for far interaction.</span></span>
- <span data-ttu-id="80f96-140">*Ruota intorno al punto di* controllo: ruotare l'oggetto con la mano del punto di controllo tra il pollice e il dito dell'indice.</span><span class="sxs-lookup"><span data-stu-id="80f96-140">*Rotate about grab point*: Rotate object with the hand about the grab point between the thumb and index finger.</span></span> <span data-ttu-id="80f96-141">Dovrebbe essere considerato come se l'oggetto fosse mantenuto a mano.</span><span class="sxs-lookup"><span data-stu-id="80f96-141">It should feel as if the object is being held by the hand.</span></span>

#### <a name="one-hand-rotation-mode-far"></a><span data-ttu-id="80f96-142">Modalità di rotazione a una mano</span><span class="sxs-lookup"><span data-stu-id="80f96-142">One hand rotation mode far</span></span>

<span data-ttu-id="80f96-143">Specifica come si comporterà l'oggetto quando viene afferrato con una sola mano alla distanza.</span><span class="sxs-lookup"><span data-stu-id="80f96-143">Specifies how the object will behave when it is being grabbed with one hand at distance.</span></span> <span data-ttu-id="80f96-144">Queste opzioni funzionano solo per le mani articolate.</span><span class="sxs-lookup"><span data-stu-id="80f96-144">These options only work for articulated hands.</span></span>

- <span data-ttu-id="80f96-145">*Ruotare about Object Center*: ruotare l'oggetto usando la rotazione della mano, ma il punto centrale dell'oggetto.</span><span class="sxs-lookup"><span data-stu-id="80f96-145">*Rotate about object center*: Rotate object using rotation of the hand, but about the object center point.</span></span> <span data-ttu-id="80f96-146">Utile per esaminare a distanza senza che il centro oggetti si sposti durante la rotazione dell'oggetto.</span><span class="sxs-lookup"><span data-stu-id="80f96-146">Useful for inspecting at a distance without the object center moving as the object rotates.</span></span>
- <span data-ttu-id="80f96-147">*Ruota intorno al punto di* recupero: ruotare l'oggetto usando la rotazione della mano, ma il punto di riscontro del raggio puntatore.</span><span class="sxs-lookup"><span data-stu-id="80f96-147">*Rotate about grab point*: Rotate object using rotation of the hand, but about the pointer ray hit point.</span></span> <span data-ttu-id="80f96-148">Utile per l'ispezione.</span><span class="sxs-lookup"><span data-stu-id="80f96-148">Useful for inspection.</span></span>

### <a name="two-handed-manipulation-properties"></a><span data-ttu-id="80f96-149">Due proprietà di manipolazione gestite</span><span class="sxs-lookup"><span data-stu-id="80f96-149">Two handed manipulation properties</span></span>

#### <a name="two-handed-manipulation-type"></a><span data-ttu-id="80f96-150">Tipo di manipolazione a due mano</span><span class="sxs-lookup"><span data-stu-id="80f96-150">Two handed manipulation type</span></span>

<span data-ttu-id="80f96-151">Specifica il modo in cui due manipolazioni a mano possono trasformare un oggetto.</span><span class="sxs-lookup"><span data-stu-id="80f96-151">Specifies how two hand manipulation can transform an object.</span></span> <span data-ttu-id="80f96-152">Poiché questa proprietà è un flag, è possibile selezionare qualsiasi numero di opzioni.</span><span class="sxs-lookup"><span data-stu-id="80f96-152">Because this property is a flag, any number of options can be selected.</span></span>

- <span data-ttu-id="80f96-153">*Move*: lo spostamento è consentito se selezionato.</span><span class="sxs-lookup"><span data-stu-id="80f96-153">*Move*: Moving is allowed if selected.</span></span>
- <span data-ttu-id="80f96-154">*Scala*: il ridimensionamento è consentito se selezionato.</span><span class="sxs-lookup"><span data-stu-id="80f96-154">*Scale*: Scaling is allowed if selected.</span></span>
- <span data-ttu-id="80f96-155">*Rotazione: la* rotazione è consentita se selezionata.</span><span class="sxs-lookup"><span data-stu-id="80f96-155">*Rotate*: Rotation is allowed if selected.</span></span>

![Gestore di manipolazione](Images/ManipulationHandler/MRTK_ManipulationHandler_TwoHanded.jpg)

### <a name="constraints"></a><span data-ttu-id="80f96-157">Vincoli</span><span class="sxs-lookup"><span data-stu-id="80f96-157">Constraints</span></span>

#### <a name="add-constraint"></a><span data-ttu-id="80f96-158">Aggiungi vincolo</span><span class="sxs-lookup"><span data-stu-id="80f96-158">Add constraint</span></span>

<span data-ttu-id="80f96-159">Questo pulsante consente di aggiungere un componente vincolo direttamente dal controllo del manipolatore di oggetti.</span><span class="sxs-lookup"><span data-stu-id="80f96-159">This button allows a constraint component to be added directly from the object manipulator inspector.</span></span> <span data-ttu-id="80f96-160">Tutti i vincoli in un progetto devono essere visibili qui.</span><span class="sxs-lookup"><span data-stu-id="80f96-160">All constraints in a project should be visible here.</span></span> <span data-ttu-id="80f96-161">Per altre informazioni, vedere [vincoli Transform](#transform-constraints) .</span><span class="sxs-lookup"><span data-stu-id="80f96-161">See [transform constraints](#transform-constraints) for more info.</span></span>

#### <a name="go-to-component"></a><span data-ttu-id="80f96-162">Vai al componente</span><span class="sxs-lookup"><span data-stu-id="80f96-162">Go to component</span></span>

<span data-ttu-id="80f96-163">Tutti i vincoli trovati nell'oggetto verranno elencati qui con un pulsante *Vai al componente* .</span><span class="sxs-lookup"><span data-stu-id="80f96-163">All constraints found on the object wil be listed here with a *Go to component* button.</span></span> <span data-ttu-id="80f96-164">Questo pulsante farà sì che il controllo scorra fino al componente del vincolo selezionato, in modo che possa essere configurato.</span><span class="sxs-lookup"><span data-stu-id="80f96-164">This button will cause the inspector to scroll to the selected constraint component so that it can be configured.</span></span>

### <a name="physics"></a><span data-ttu-id="80f96-165">Fisica</span><span class="sxs-lookup"><span data-stu-id="80f96-165">Physics</span></span>

#### <a name="release-behavior"></a><span data-ttu-id="80f96-166">Comportamento della versione</span><span class="sxs-lookup"><span data-stu-id="80f96-166">Release behavior</span></span>

<span data-ttu-id="80f96-167">Specificare le proprietà fisiche che un oggetto modificato deve tenere al rilascio.</span><span class="sxs-lookup"><span data-stu-id="80f96-167">Specify which physical properties a manipulated object should keep upon release.</span></span> <span data-ttu-id="80f96-168">Richiede che un componente rigidbody sia su tale oggetto.</span><span class="sxs-lookup"><span data-stu-id="80f96-168">Requires a rigidbody component to be on that object.</span></span> <span data-ttu-id="80f96-169">Poiché questa proprietà è un flag, è possibile selezionare entrambe le opzioni.</span><span class="sxs-lookup"><span data-stu-id="80f96-169">Because this property is a flag, both options can be selected.</span></span>

- <span data-ttu-id="80f96-170">*Mantieni velocità*: quando l'oggetto viene rilasciato, se questa opzione è selezionata, manterrà la velocità lineare.</span><span class="sxs-lookup"><span data-stu-id="80f96-170">*Keep Velocity*: When the object is released, if this option is selected it will keep its linear velocity.</span></span>
- <span data-ttu-id="80f96-171">*Mantieni velocità angolare*: quando l'oggetto viene rilasciato, se questa opzione è selezionata, manterrà la velocità angolare.</span><span class="sxs-lookup"><span data-stu-id="80f96-171">*Keep Angular Velocity*: When the object is released, if this option is selected it will keep its angular velocity.</span></span>

### <a name="smoothing"></a><span data-ttu-id="80f96-172">Definizione di movimenti uniformi</span><span class="sxs-lookup"><span data-stu-id="80f96-172">Smoothing</span></span>

#### <a name="smoothing-active"></a><span data-ttu-id="80f96-173">Smoothing attivo</span><span class="sxs-lookup"><span data-stu-id="80f96-173">Smoothing active</span></span>

<span data-ttu-id="80f96-174">Specifica se la smussatura è attiva.</span><span class="sxs-lookup"><span data-stu-id="80f96-174">Specifies whether smoothing is active.</span></span>

#### <a name="move-lerp-time"></a><span data-ttu-id="80f96-175">Sposta Lerp tempo</span><span class="sxs-lookup"><span data-stu-id="80f96-175">Move lerp time</span></span>

<span data-ttu-id="80f96-176">Quantità di smussatura da applicare allo spostamento.</span><span class="sxs-lookup"><span data-stu-id="80f96-176">Amount of smoothing to apply to the movement.</span></span> <span data-ttu-id="80f96-177">L'uniformità di 0 significa nessuna smussatura.</span><span class="sxs-lookup"><span data-stu-id="80f96-177">Smoothing of 0 means no smoothing.</span></span> <span data-ttu-id="80f96-178">Il valore max significa nessuna modifica al valore.</span><span class="sxs-lookup"><span data-stu-id="80f96-178">Max value means no change to value.</span></span>

#### <a name="rotate-lerp-time"></a><span data-ttu-id="80f96-179">Ruota Lerp tempo</span><span class="sxs-lookup"><span data-stu-id="80f96-179">Rotate lerp time</span></span>

<span data-ttu-id="80f96-180">Quantità di smussatura da applicare alla rotazione.</span><span class="sxs-lookup"><span data-stu-id="80f96-180">Amount of smoothing to apply to the rotation.</span></span> <span data-ttu-id="80f96-181">L'uniformità di 0 significa nessuna smussatura.</span><span class="sxs-lookup"><span data-stu-id="80f96-181">Smoothing of 0 means no smoothing.</span></span> <span data-ttu-id="80f96-182">Il valore max significa nessuna modifica al valore.</span><span class="sxs-lookup"><span data-stu-id="80f96-182">Max value means no change to value.</span></span>

#### <a name="scale-lerp-time"></a><span data-ttu-id="80f96-183">Ridimensionamento Lerp tempo</span><span class="sxs-lookup"><span data-stu-id="80f96-183">Scale lerp time</span></span>

<span data-ttu-id="80f96-184">Quantità di smussatura da applicare alla scala.</span><span class="sxs-lookup"><span data-stu-id="80f96-184">Amount of smoothing to apply to the scale.</span></span> <span data-ttu-id="80f96-185">L'uniformità di 0 significa nessuna smussatura.</span><span class="sxs-lookup"><span data-stu-id="80f96-185">Smoothing of 0 means no smoothing.</span></span> <span data-ttu-id="80f96-186">Il valore max significa nessuna modifica al valore.</span><span class="sxs-lookup"><span data-stu-id="80f96-186">Max value means no change to value.</span></span>

### <a name="manipulation-events"></a><span data-ttu-id="80f96-187">Eventi di manipolazione</span><span class="sxs-lookup"><span data-stu-id="80f96-187">Manipulation events</span></span>

<span data-ttu-id="80f96-188">Il gestore di manipolazione fornisce gli eventi seguenti:</span><span class="sxs-lookup"><span data-stu-id="80f96-188">Manipulation handler provides the following events:</span></span>

- <span data-ttu-id="80f96-189">*OnManipulationStarted*: generato all'avvio della manipolazione.</span><span class="sxs-lookup"><span data-stu-id="80f96-189">*OnManipulationStarted*: Fired when manipulation starts.</span></span>
- <span data-ttu-id="80f96-190">*OnManipulationEnded*: viene attivato al termine della manipolazione.</span><span class="sxs-lookup"><span data-stu-id="80f96-190">*OnManipulationEnded*: Fires when the manipulation ends.</span></span>
- <span data-ttu-id="80f96-191">*OnHoverStarted*: viene attivato quando una mano o un controller passa il mouse sul manipolabile, quasi o lontano.</span><span class="sxs-lookup"><span data-stu-id="80f96-191">*OnHoverStarted*: Fires when a hand / controller hovers the manipulatable, near or far.</span></span>
- <span data-ttu-id="80f96-192">*OnHoverEnded*: viene attivato quando una mano o un controller Annulla il passaggio del mouse sul manipolabile, quasi o lontano.</span><span class="sxs-lookup"><span data-stu-id="80f96-192">*OnHoverEnded*: Fires when a hand / controller un-hovers the manipulatable, near or far.</span></span>

<span data-ttu-id="80f96-193">L'ordine di attivazione dell'evento per la manipolazione è:</span><span class="sxs-lookup"><span data-stu-id="80f96-193">The event fire order for manipulation is:</span></span>

<span data-ttu-id="80f96-194">*OnHoverStarted*  ->  *OnManipulationStarted*  ->  *OnManipulationEnded*  ->  *OnHoverEnded*</span><span class="sxs-lookup"><span data-stu-id="80f96-194">*OnHoverStarted* -> *OnManipulationStarted* -> *OnManipulationEnded* -> *OnHoverEnded*</span></span>

<span data-ttu-id="80f96-195">Se non è presente alcuna manipolazione, si otterranno comunque gli eventi hover con l'ordine di incendio seguente:</span><span class="sxs-lookup"><span data-stu-id="80f96-195">If there is no manipulation, you will still get hover events with the following fire order:</span></span>

<span data-ttu-id="80f96-196">*OnHoverStarted*  ->  *OnHoverEnded*</span><span class="sxs-lookup"><span data-stu-id="80f96-196">*OnHoverStarted* -> *OnHoverEnded*</span></span>

## <a name="transform-constraints"></a><span data-ttu-id="80f96-197">Vincoli di trasformazione</span><span class="sxs-lookup"><span data-stu-id="80f96-197">Transform constraints</span></span>

<span data-ttu-id="80f96-198">I vincoli possono essere usati per limitare la manipolazione in qualche modo.</span><span class="sxs-lookup"><span data-stu-id="80f96-198">Constraints can be used to limit manipulation in some way.</span></span> <span data-ttu-id="80f96-199">Ad esempio, alcune applicazioni possono richiedere la rotazione, ma richiedono anche che l'oggetto rimanga verticale.</span><span class="sxs-lookup"><span data-stu-id="80f96-199">For example, some applications may require rotation, but also require that the object remain upright.</span></span> <span data-ttu-id="80f96-200">In questo caso, `RotationAxisConstraint` è possibile aggiungere un oggetto all'oggetto e usarlo per limitare la rotazione alla rotazione dell'asse y.</span><span class="sxs-lookup"><span data-stu-id="80f96-200">In this case, a `RotationAxisConstraint` can be added to the object and used to limit rotation to y-axis rotation.</span></span> <span data-ttu-id="80f96-201">MRTK fornisce una serie di vincoli, tutti descritti di seguito.</span><span class="sxs-lookup"><span data-stu-id="80f96-201">MRTK provides a number of constraints, all of which are described below.</span></span>

<span data-ttu-id="80f96-202">È anche possibile definire nuovi vincoli e usarli per creare un comportamento di manipolazione univoco che potrebbe essere necessario per alcune applicazioni.</span><span class="sxs-lookup"><span data-stu-id="80f96-202">It is also possible to define new constraints and use them to create unique manipulation behaviour that may be needed for some applications.</span></span> <span data-ttu-id="80f96-203">A tale scopo, creare uno script che erediti da [`TransformConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.TransformConstraint) e implementi la `ConstraintType` proprietà abstract e il `ApplyConstraint` metodo abstract.</span><span class="sxs-lookup"><span data-stu-id="80f96-203">To do this, create a script that inherits from [`TransformConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.TransformConstraint) and implement the abstract `ConstraintType` property and the abstract `ApplyConstraint` method.</span></span> <span data-ttu-id="80f96-204">Quando si aggiunge un nuovo vincolo all'oggetto, è necessario vincolare la manipolazione nel modo in cui è stato definito.</span><span class="sxs-lookup"><span data-stu-id="80f96-204">Upon adding a new constraint to the object, it should constrain manipulation in the way that was defined.</span></span> <span data-ttu-id="80f96-205">Questo nuovo vincolo dovrebbe essere visualizzato anche nei campi del [vincolo](#constraints)del manipolatore di oggetti.</span><span class="sxs-lookup"><span data-stu-id="80f96-205">This new constraint should also show in the object manipulator [constraint fields](#constraints).</span></span>

<span data-ttu-id="80f96-206">Tutti i vincoli forniti da MRTK condividono le proprietà seguenti:</span><span class="sxs-lookup"><span data-stu-id="80f96-206">All of the constraints provided by MRTK share the following properties:</span></span>

#### <a name="target-transform"></a><span data-ttu-id="80f96-207">Trasformazione destinazione</span><span class="sxs-lookup"><span data-stu-id="80f96-207">Target Transform</span></span>

<span data-ttu-id="80f96-208">Trasformazione dell'oggetto modificato sottoposto a vincoli.</span><span class="sxs-lookup"><span data-stu-id="80f96-208">Transform of the manipulated object being constrained.</span></span> <span data-ttu-id="80f96-209">Deve corrispondere alla [*trasformazione dell'host*](#host-transform)ObjectManipulator.</span><span class="sxs-lookup"><span data-stu-id="80f96-209">This should be the same as the ObjectManipulator [*Host transform*](#host-transform).</span></span> <span data-ttu-id="80f96-210">Il valore predefinito è l'oggetto del componente.</span><span class="sxs-lookup"><span data-stu-id="80f96-210">Defaults to the object of the component.</span></span>

#### <a name="hand-type"></a><span data-ttu-id="80f96-211">Tipo di mano</span><span class="sxs-lookup"><span data-stu-id="80f96-211">Hand Type</span></span>

<span data-ttu-id="80f96-212">Specifica se il vincolo viene utilizzato per una sola mano, due o entrambi i tipi di manipolazione.</span><span class="sxs-lookup"><span data-stu-id="80f96-212">Specifies whether the constraint is used for one handed, two handed or both kinds of manipulation.</span></span> <span data-ttu-id="80f96-213">Poiché questa proprietà è un flag, è possibile selezionare entrambe le opzioni.</span><span class="sxs-lookup"><span data-stu-id="80f96-213">Because this property is a flag, both options can be selected.</span></span>

- <span data-ttu-id="80f96-214">*Una sola mano*: il vincolo verrà usato durante una manipolazione gestita, se selezionato.</span><span class="sxs-lookup"><span data-stu-id="80f96-214">*One handed*: Constraint will be used during one handed manipulation if selected.</span></span>
- <span data-ttu-id="80f96-215">*Due passate*: il vincolo verrà usato durante due manipolazioni gestite, se selezionato.</span><span class="sxs-lookup"><span data-stu-id="80f96-215">*Two handed*: Constraint will be used during two handed manipulation if selected.</span></span>

#### <a name="proximity-type"></a><span data-ttu-id="80f96-216">Tipo di prossimità</span><span class="sxs-lookup"><span data-stu-id="80f96-216">Proximity Type</span></span>

<span data-ttu-id="80f96-217">Specifica se il vincolo viene utilizzato per i tipi di manipolazione near, di gran lunga o entrambi.</span><span class="sxs-lookup"><span data-stu-id="80f96-217">Specifies whether the constraint is used for near, far or both kinds of manipulation.</span></span> <span data-ttu-id="80f96-218">Poiché questa proprietà è un flag, è possibile selezionare entrambe le opzioni.</span><span class="sxs-lookup"><span data-stu-id="80f96-218">Because this property is a flag, both options can be selected.</span></span>

- <span data-ttu-id="80f96-219">*Near*: il vincolo verrà usato in prossimità della manipolazione, se selezionato.</span><span class="sxs-lookup"><span data-stu-id="80f96-219">*Near*: Constraint will be used during near manipulation if selected.</span></span>
- <span data-ttu-id="80f96-220">*Lontano*: il vincolo verrà usato durante la manipolazione di gran lunga se selezionato.</span><span class="sxs-lookup"><span data-stu-id="80f96-220">*Far*: Constraint will be used during far manipulation if selected.</span></span>

### <a name="faceuserconstraint"></a><span data-ttu-id="80f96-221">FaceUserConstraint</span><span class="sxs-lookup"><span data-stu-id="80f96-221">FaceUserConstraint</span></span>

<img src="Images/ObjectManipulator/MRTK_Constraint_FaceUser.gif" width="400" alt="Constraint face user">

<span data-ttu-id="80f96-222">Quando questo vincolo è associato a un oggetto, la rotazione sarà limitata in modo che l'oggetto faccia sempre fronte all'utente.</span><span class="sxs-lookup"><span data-stu-id="80f96-222">When this constraint is attached to an object, rotation will be limited so that object will always face the user.</span></span> <span data-ttu-id="80f96-223">Questa operazione è utile per gli slate o i pannelli.</span><span class="sxs-lookup"><span data-stu-id="80f96-223">This is useful for slates or panels.</span></span> <span data-ttu-id="80f96-224">Le proprietà per `FaceUserConstraint` sono le seguenti:</span><span class="sxs-lookup"><span data-stu-id="80f96-224">The properties for `FaceUserConstraint` are as follows:</span></span>

#### <a name="face-away"></a><span data-ttu-id="80f96-225">Faccia fuori</span><span class="sxs-lookup"><span data-stu-id="80f96-225">Face away</span></span>

<span data-ttu-id="80f96-226">L'oggetto viene rivolto dall'utente se true.</span><span class="sxs-lookup"><span data-stu-id="80f96-226">Object faces away from the user if true.</span></span>

### <a name="fixeddistanceconstraint"></a><span data-ttu-id="80f96-227">FixedDistanceConstraint</span><span class="sxs-lookup"><span data-stu-id="80f96-227">FixedDistanceConstraint</span></span>

<img src="Images/ObjectManipulator/MRTK_Constraint_FixedDistance.gif" width="400" alt="constraintt fixed distance">

<span data-ttu-id="80f96-228">Questo vincolo corregge la distanza tra l'oggetto modificato e un'altra trasformazione dell'oggetto all'avvio della manipolazione.</span><span class="sxs-lookup"><span data-stu-id="80f96-228">This constraint fixes the distance between the manipulated object and another object transform on manipulation start.</span></span> <span data-ttu-id="80f96-229">Questa operazione è utile per comportamenti come la correzione della distanza dall'oggetto modificato alla trasformazione Head.</span><span class="sxs-lookup"><span data-stu-id="80f96-229">This is useful for behaviour such as fixing the distance from the manipulated object to the head transform.</span></span> <span data-ttu-id="80f96-230">Le proprietà per `FixedDistanceConstraint` sono le seguenti:</span><span class="sxs-lookup"><span data-stu-id="80f96-230">The properties for `FixedDistanceConstraint` are as follows:</span></span>

#### <a name="constraint-transform"></a><span data-ttu-id="80f96-231">Trasformazione vincolo</span><span class="sxs-lookup"><span data-stu-id="80f96-231">Constraint transform</span></span>

<span data-ttu-id="80f96-232">Si tratta dell'altra trasformazione a cui l'oggetto modificato avrà una distanza fissa.</span><span class="sxs-lookup"><span data-stu-id="80f96-232">This is the other transform that the manipulated object will have a fixed distance to.</span></span> <span data-ttu-id="80f96-233">Il valore predefinito è la trasformazione della fotocamera.</span><span class="sxs-lookup"><span data-stu-id="80f96-233">Defaults to the camera transform.</span></span>

### <a name="fixedrotationtouserconstraint"></a><span data-ttu-id="80f96-234">FixedRotationToUserConstraint</span><span class="sxs-lookup"><span data-stu-id="80f96-234">FixedRotationToUserConstraint</span></span>

<img src="Images/ObjectManipulator/MRTK_Constraint_FixedRotationToUser.gif" width="400" alt="Fixed rotation to user">

<span data-ttu-id="80f96-235">Questo vincolo corregge la rotazione relativa tra l'utente e l'oggetto modificato durante la manipolazione.</span><span class="sxs-lookup"><span data-stu-id="80f96-235">This constraint fixes the relative rotation between the user and the manipulated object while it is being manipulated.</span></span> <span data-ttu-id="80f96-236">Questa operazione è utile per gli slate o i pannelli, in quanto assicura che l'oggetto modificato mostri sempre lo stesso aspetto all'utente, così come è stato fatto all'inizio della manipolazione.</span><span class="sxs-lookup"><span data-stu-id="80f96-236">This is useful for slates or panels as it ensures that the manipulated object always shows the same face to the user as it did at the start of manipulation.</span></span> <span data-ttu-id="80f96-237">Non `FixedRotationToUserConstraint` dispone di proprietà univoche.</span><span class="sxs-lookup"><span data-stu-id="80f96-237">The `FixedRotationToUserConstraint` does not have any unique properties.</span></span>

### <a name="fixedrotationtoworldconstraint"></a><span data-ttu-id="80f96-238">FixedRotationToWorldConstraint</span><span class="sxs-lookup"><span data-stu-id="80f96-238">FixedRotationToWorldConstraint</span></span>

<img src="Images/ObjectManipulator/MRTK_Constraint_FixedRotationToWorld.gif" width="400" alt="Fixed rotation to world">

<span data-ttu-id="80f96-239">Questo vincolo corregge la rotazione globale dell'oggetto modificato durante la manipolazione.</span><span class="sxs-lookup"><span data-stu-id="80f96-239">This constraint fixes the global rotation of the manipulated object while it is being manipulated.</span></span> <span data-ttu-id="80f96-240">Questa operazione può essere utile nei casi in cui non è necessario che la rotazione venga ripartita dalla manipolazione.</span><span class="sxs-lookup"><span data-stu-id="80f96-240">This can be useful in cases where no rotation should be imparted by manipulation.</span></span> <span data-ttu-id="80f96-241">Non `FixedRotationToWorldConstraint` dispone di proprietà univoche:</span><span class="sxs-lookup"><span data-stu-id="80f96-241">The `FixedRotationToWorldConstraint` does not have any unique properties:</span></span>

### <a name="maintainapparentsizeconstraint"></a><span data-ttu-id="80f96-242">MaintainApparentSizeConstraint</span><span class="sxs-lookup"><span data-stu-id="80f96-242">MaintainApparentSizeConstraint</span></span>

<img src="Images/ObjectManipulator/MRTK_Constraint_MaintainApparentSize.gif" width="400" alt="Maintain Apparent Size">

<span data-ttu-id="80f96-243">Quando questo vincolo è associato a un oggetto, indipendentemente dalla distanza dell'oggetto dall'utente, manterrà le stesse dimensioni apparenti per l'utente (ad esempio, prenderà la stessa proporzione del campo di visualizzazione dell'utente).</span><span class="sxs-lookup"><span data-stu-id="80f96-243">When this constraint is attached to an object, no matter how far the object is from the user, it will maintain the same apparent size to the user (i.e. it will take up the same proportion of the user's field of view).</span></span> <span data-ttu-id="80f96-244">Questa operazione può essere utilizzata per garantire che uno Slate o un pannello di testo rimanga leggibile durante la manipolazione.</span><span class="sxs-lookup"><span data-stu-id="80f96-244">This can be used to ensure that a slate or text panel remains readable while manipulating.</span></span> <span data-ttu-id="80f96-245">Non `MaintainApparentSizeConstraint` dispone di proprietà univoche:</span><span class="sxs-lookup"><span data-stu-id="80f96-245">The `MaintainApparentSizeConstraint` does not have any unique properties:</span></span>

### <a name="moveaxisconstraint"></a><span data-ttu-id="80f96-246">MoveAxisConstraint</span><span class="sxs-lookup"><span data-stu-id="80f96-246">MoveAxisConstraint</span></span>

<img src="Images/ObjectManipulator/MRTK_Constraint_MoveAxis.gif" width="400" alt="Constraint Move Axis">

<span data-ttu-id="80f96-247">Questo vincolo può essere usato per correggere gli assi che possono essere spostati in un oggetto modificato.</span><span class="sxs-lookup"><span data-stu-id="80f96-247">This constraint can be used to fix along which axes a manipulated object can be moved.</span></span> <span data-ttu-id="80f96-248">Questa operazione può essere utile per la modifica degli oggetti sulla superficie di un piano o lungo una linea.</span><span class="sxs-lookup"><span data-stu-id="80f96-248">This can be useful for manipulating objects over the surface of a plane, or along a line.</span></span> <span data-ttu-id="80f96-249">Le proprietà per `MoveAxisConstraint` sono le seguenti:</span><span class="sxs-lookup"><span data-stu-id="80f96-249">The properties for `MoveAxisConstraint` are as follows:</span></span>

#### <a name="constraint-on-movement"></a><span data-ttu-id="80f96-250">Vincolo durante lo spostamento</span><span class="sxs-lookup"><span data-stu-id="80f96-250">Constraint on movement</span></span>

<span data-ttu-id="80f96-251">Specifica gli assi su cui impedire lo spostamento.</span><span class="sxs-lookup"><span data-stu-id="80f96-251">Specifies which axes to prevent movement on.</span></span> <span data-ttu-id="80f96-252">Per impostazione predefinita, questi assi saranno globali anziché locali, ma è possibile modificarli sotto.</span><span class="sxs-lookup"><span data-stu-id="80f96-252">By default these axes will be global rather than local, but this can be changed below.</span></span> <span data-ttu-id="80f96-253">Poiché questa proprietà è un flag, è possibile selezionare qualsiasi numero di opzioni.</span><span class="sxs-lookup"><span data-stu-id="80f96-253">Because this property is a flag, any number of options can be selected.</span></span>

- <span data-ttu-id="80f96-254">*Asse x*: se selezionato, lo spostamento lungo l'asse x è vincolato.</span><span class="sxs-lookup"><span data-stu-id="80f96-254">*X Axis*: Movement along the x-axis is constrained if selected.</span></span>
- <span data-ttu-id="80f96-255">*Asse y*: se selezionato, lo spostamento lungo l'asse y è vincolato.</span><span class="sxs-lookup"><span data-stu-id="80f96-255">*Y Axis*: Movement along the y-axis is constrained if selected.</span></span>
- <span data-ttu-id="80f96-256">*Asse z*: lo spostamento lungo l'asse z è vincolato se selezionato.</span><span class="sxs-lookup"><span data-stu-id="80f96-256">*Z Axis*: Movement along the z-axis is constrained if selected.</span></span>

#### <a name="use-local-space-for-constraint"></a><span data-ttu-id="80f96-257">Usa spazio locale per il vincolo</span><span class="sxs-lookup"><span data-stu-id="80f96-257">Use local space for constraint</span></span>

<span data-ttu-id="80f96-258">Vincola gli assi di trasformazione locali dell'oggetto modificato se true.</span><span class="sxs-lookup"><span data-stu-id="80f96-258">Will constrain relative the manipulated object's local transform axes if true.</span></span> <span data-ttu-id="80f96-259">False per impostazione predefinita.</span><span class="sxs-lookup"><span data-stu-id="80f96-259">False by default.</span></span>

### <a name="rotationaxisconstraint"></a><span data-ttu-id="80f96-260">RotationAxisConstraint</span><span class="sxs-lookup"><span data-stu-id="80f96-260">RotationAxisConstraint</span></span>

<img src="Images/ObjectManipulator/MRTK_Constraint_RotationAxis.gif" width="400" alt="Constraint Rotation Axis">

<span data-ttu-id="80f96-261">Questo vincolo può essere usato per correggere gli assi che possono essere ruotati da un oggetto modificato.</span><span class="sxs-lookup"><span data-stu-id="80f96-261">This constraint can be used to fix about which axes a manipulated object can be rotated.</span></span> <span data-ttu-id="80f96-262">Questa operazione può essere utile per mantenere un oggetto manipolato verticalmente, ma che consente comunque di ruotare gli assi y, ad esempio.</span><span class="sxs-lookup"><span data-stu-id="80f96-262">This can be useful for keeping a manipulated object upright, but still allowing y-axis rotations, for example.</span></span> <span data-ttu-id="80f96-263">Le proprietà per `RotationAxisConstraint` sono le seguenti:</span><span class="sxs-lookup"><span data-stu-id="80f96-263">The properties for `RotationAxisConstraint` are as follows:</span></span>

#### <a name="constraint-on-rotation"></a><span data-ttu-id="80f96-264">Vincolo alla rotazione</span><span class="sxs-lookup"><span data-stu-id="80f96-264">Constraint on rotation</span></span>

<span data-ttu-id="80f96-265">Specifica gli assi per i quali impedire la rotazione.</span><span class="sxs-lookup"><span data-stu-id="80f96-265">Specifies which axes to prevent rotation about.</span></span> <span data-ttu-id="80f96-266">Per impostazione predefinita, questi assi saranno globali anziché locali, ma è possibile modificarli sotto.</span><span class="sxs-lookup"><span data-stu-id="80f96-266">By default these axes will be global rather than local, but this can be changed below.</span></span> <span data-ttu-id="80f96-267">Poiché questa proprietà è un flag, è possibile selezionare qualsiasi numero di opzioni.</span><span class="sxs-lookup"><span data-stu-id="80f96-267">Because this property is a flag, any number of options can be selected.</span></span>

- <span data-ttu-id="80f96-268">*Asse y*: la rotazione sull'asse y è vincolata se selezionata.</span><span class="sxs-lookup"><span data-stu-id="80f96-268">*Y Axis*: Rotation about the y-axis is constrained if selected.</span></span>
- <span data-ttu-id="80f96-269">*Asse z*: la rotazione sull'asse z è vincolata se selezionata.</span><span class="sxs-lookup"><span data-stu-id="80f96-269">*Z Axis*: Rotation about the z-axis is constrained if selected.</span></span>
- <span data-ttu-id="80f96-270">*Asse x*: la rotazione sull'asse x è vincolata se selezionata.</span><span class="sxs-lookup"><span data-stu-id="80f96-270">*X Axis*: Rotation about the x-axis is constrained if selected.</span></span>

#### <a name="use-local-space-for-constraint"></a><span data-ttu-id="80f96-271">Usa spazio locale per il vincolo</span><span class="sxs-lookup"><span data-stu-id="80f96-271">Use local space for constraint</span></span>

<span data-ttu-id="80f96-272">Vincola gli assi di trasformazione locali dell'oggetto modificato se true.</span><span class="sxs-lookup"><span data-stu-id="80f96-272">Will constrain relative the manipulated object's local transform axes if true.</span></span> <span data-ttu-id="80f96-273">False per impostazione predefinita.</span><span class="sxs-lookup"><span data-stu-id="80f96-273">False by default.</span></span>

### <a name="minmaxscaleconstraint"></a><span data-ttu-id="80f96-274">MinMaxScaleConstraint</span><span class="sxs-lookup"><span data-stu-id="80f96-274">MinMaxScaleConstraint</span></span>

<img src="Images/ObjectManipulator/MRTK_Constraint_MinMaxScale.gif" width="400" alt="MinMax Scale">

<span data-ttu-id="80f96-275">Questo vincolo consente di impostare i valori minimo e massimo per la scala dell'oggetto modificato.</span><span class="sxs-lookup"><span data-stu-id="80f96-275">This constraint allows minimum and maximum values to be set for the scale of the manipulated object.</span></span> <span data-ttu-id="80f96-276">Questa operazione è utile per impedire agli utenti di ridimensionare un oggetto troppo piccolo o troppo grande.</span><span class="sxs-lookup"><span data-stu-id="80f96-276">This is useful for preventing users from scaling an object too small or too large.</span></span> <span data-ttu-id="80f96-277">Le proprietà per `MinMaxScaleConstraint` sono le seguenti:</span><span class="sxs-lookup"><span data-stu-id="80f96-277">The properties for `MinMaxScaleConstraint` are as follows:</span></span>

#### <a name="scale-minimum"></a><span data-ttu-id="80f96-278">Dimensioni minime</span><span class="sxs-lookup"><span data-stu-id="80f96-278">Scale minimum</span></span>

<span data-ttu-id="80f96-279">Valore di scala minimo durante la manipolazione.</span><span class="sxs-lookup"><span data-stu-id="80f96-279">The minimum scale value during manipulation.</span></span>

#### <a name="scale-maximum"></a><span data-ttu-id="80f96-280">Scalabilità massima</span><span class="sxs-lookup"><span data-stu-id="80f96-280">Scale maximum</span></span>

<span data-ttu-id="80f96-281">Valore di scala massimo durante la manipolazione.</span><span class="sxs-lookup"><span data-stu-id="80f96-281">The maximum scale value during manipulation.</span></span>

#### <a name="relative-to-initial-state"></a><span data-ttu-id="80f96-282">Relativo allo stato iniziale</span><span class="sxs-lookup"><span data-stu-id="80f96-282">Relative to initial state</span></span>

<span data-ttu-id="80f96-283">Se true, i valori precedenti verranno interpretati come relativi alla scala iniziale degli oggetti.</span><span class="sxs-lookup"><span data-stu-id="80f96-283">If true, the values above will be interpreted as relative to the objects initial scale.</span></span> <span data-ttu-id="80f96-284">In caso contrario, verranno interpretati come valori di scala assoluti.</span><span class="sxs-lookup"><span data-stu-id="80f96-284">Otherwise they will be interpreted as absolute scale values.</span></span>

## <a name="physics-and-collisions"></a><span data-ttu-id="80f96-285">Fisica e collisioni</span><span class="sxs-lookup"><span data-stu-id="80f96-285">Physics and collisions</span></span>

<span data-ttu-id="80f96-286">Il comportamento fisico può essere abilitato aggiungendo un componente rigidbody allo stesso oggetto di un manipolatore di oggetti.</span><span class="sxs-lookup"><span data-stu-id="80f96-286">Physics behaviour can be enabled by adding a rigidbody component to the same object as an object manipulator.</span></span> <span data-ttu-id="80f96-287">Non solo questa operazione Abilita la configurazione del [comportamento di rilascio](#release-behavior) precedente, inoltre consente conflitti.</span><span class="sxs-lookup"><span data-stu-id="80f96-287">Not only does this enable configuration of [release behaviour](#release-behavior) above, it also enables collisions.</span></span> <span data-ttu-id="80f96-288">Senza un componente rigidbody, i conflitti non si comportano correttamente durante la manipolazione:</span><span class="sxs-lookup"><span data-stu-id="80f96-288">Without a rigidbody component, collisions don't behave correctly during manipulation:</span></span>

- <span data-ttu-id="80f96-289">I conflitti tra un oggetto modificato e un Collider statico (ovvero un oggetto con un Collider ma nessun rigidbody) non funzionano, l'oggetto modificato passa direttamente attraverso il Collider statico senza effetti.</span><span class="sxs-lookup"><span data-stu-id="80f96-289">Collisions between a manipulated object and a static collider (i.e. an object with a collider but no rigidbody) do not work, the manipulated object passes straight through the static collider unaffected.</span></span>
- <span data-ttu-id="80f96-290">Collisioni tra un oggetto modificato e un rigidbody (ad esempio</span><span class="sxs-lookup"><span data-stu-id="80f96-290">Collisions between a manipulated object and a rigidbody (i.e</span></span> <span data-ttu-id="80f96-291">un oggetto con un Collider e un rigidbody) fa sì che rigidbody abbia una risposta di collisione, ma la risposta è inattiva e non naturale.</span><span class="sxs-lookup"><span data-stu-id="80f96-291">an object with both a collider and a rigidbody) cause the rigidbody to have a collision response, but the response is jumpy and unnatural.</span></span> <span data-ttu-id="80f96-292">Non esiste inoltre alcuna risposta di collisione sull'oggetto modificato.</span><span class="sxs-lookup"><span data-stu-id="80f96-292">There is also no collision response on the manipulated object.</span></span>

<span data-ttu-id="80f96-293">Quando viene aggiunto un rigidbody, i conflitti dovrebbero funzionare correttamente.</span><span class="sxs-lookup"><span data-stu-id="80f96-293">When a rigidbody is added, collisions should work correctly.</span></span>

### <a name="without-rigidbody"></a><span data-ttu-id="80f96-294">Senza rigidbody</span><span class="sxs-lookup"><span data-stu-id="80f96-294">Without rigidbody</span></span>

<img src="Images/ObjectManipulator/MRTK_PhysicsManipulation_NoRigidbody.gif" width="500" alt="No Rigid Body">

### <a name="with-rigidbody"></a><span data-ttu-id="80f96-295">Con rigidbody</span><span class="sxs-lookup"><span data-stu-id="80f96-295">With rigidbody</span></span>

<img src="Images/ObjectManipulator/MRTK_PhysicsManipulation_Rigidbody.gif" width="500" alt="Rigid Body">

---
title: ObjectManipulator
description: Come usare il manipolatore di oggetti in MRTK
author: thalbern
ms.author: bethalha
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, manipolazione degli oggetti,
ms.openlocfilehash: 137472b4ef00003f11002f603ace83f953af1826
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2021
ms.locfileid: "104683784"
---
# <a name="object-manipulator"></a><span data-ttu-id="ab5ab-104">Manipolatore di oggetti</span><span class="sxs-lookup"><span data-stu-id="ab5ab-104">Object manipulator</span></span>

![Manipolatore di oggetti](../images/manipulation-handler/MRTK_Manipulation_Main.png)

<span data-ttu-id="ab5ab-106">*ObjectManipulator* è il nuovo componente per il comportamento di manipolazione, disponibile in precedenza in *ManipulationHandler*.</span><span class="sxs-lookup"><span data-stu-id="ab5ab-106">The *ObjectManipulator* is the new component for manipulation behaviour, previously found in *ManipulationHandler*.</span></span> <span data-ttu-id="ab5ab-107">Il manipolatore di oggetti apporta diversi miglioramenti e semplificazioni.</span><span class="sxs-lookup"><span data-stu-id="ab5ab-107">The object manipulator makes a number of improvements and simplifications.</span></span> <span data-ttu-id="ab5ab-108">Questo componente sostituisce il gestore di manipolazione, che verrà deprecato.</span><span class="sxs-lookup"><span data-stu-id="ab5ab-108">This component is a replacement for the manipulation handler, which will be deprecated.</span></span>

<span data-ttu-id="ab5ab-109">Lo script *ObjectManipulator* rende un oggetto mobile, scalabile e girevole usando uno o due mani.</span><span class="sxs-lookup"><span data-stu-id="ab5ab-109">The *ObjectManipulator* script makes an object movable, scalable, and rotatable using one or two hands.</span></span> <span data-ttu-id="ab5ab-110">Il manipolatore di oggetti può essere configurato per controllare la modalità di risposta dell'oggetto a diversi input.</span><span class="sxs-lookup"><span data-stu-id="ab5ab-110">The object manipulator can be configured to control how the object will respond to various inputs.</span></span> <span data-ttu-id="ab5ab-111">Lo script dovrebbe funzionare con la maggior parte delle forme di interazione, ad esempio HoloLens 2, a mano articolata, HoloLens 2, raggi mano, HoloLens 1 sguardo e movimenti e input del controller di movimento dell'auricolare.</span><span class="sxs-lookup"><span data-stu-id="ab5ab-111">The script should work with most forms of interaction, such as HoloLens 2 articulated hand, HoloLens 2 hand rays, HoloLens 1 gaze and gestures and immersive headset motion controller input.</span></span>

## <a name="how-to-use-the-object-manipulator"></a><span data-ttu-id="ab5ab-112">Come utilizzare il manipolatore di oggetti</span><span class="sxs-lookup"><span data-stu-id="ab5ab-112">How to use the object manipulator</span></span>

<span data-ttu-id="ab5ab-113">Per usare il manipolatore di oggetti, aggiungere prima il `ObjectManipulator` componente script a un GameObject.</span><span class="sxs-lookup"><span data-stu-id="ab5ab-113">To use the object manipulator, first add the `ObjectManipulator` script component to a GameObject.</span></span> <span data-ttu-id="ab5ab-114">Assicurarsi di aggiungere anche un Collider all'oggetto, associando i relativi limiti afferrabili.</span><span class="sxs-lookup"><span data-stu-id="ab5ab-114">Make sure to also add a collider to the object, matching its grabbable bounds.</span></span>

<span data-ttu-id="ab5ab-115">Per fare in modo che l'oggetto risponda all'input della mano quasi articolato, aggiungere `NearInteractionGrabbable` anche lo script.</span><span class="sxs-lookup"><span data-stu-id="ab5ab-115">To make the object respond to near articulated hand input, add the `NearInteractionGrabbable` script as well.</span></span>

<span data-ttu-id="ab5ab-116">Il comportamento fisico può essere abilitato per il manipolatore di oggetti aggiungendo un componente rigidbody all'oggetto.</span><span class="sxs-lookup"><span data-stu-id="ab5ab-116">Physics behaviour can be enabled for the object manipulator by adding a rigidbody component to the object.</span></span> <span data-ttu-id="ab5ab-117">Il comportamento fisico abilitato aggiungendo questo componente viene discusso in modo più dettagliato in [*fisica e collisioni*](#physics-and-collisions).</span><span class="sxs-lookup"><span data-stu-id="ab5ab-117">Physics behaviour enabled by adding this component is discussed in greater detail in [*Physics and collisions*](#physics-and-collisions).</span></span>

<span data-ttu-id="ab5ab-118">Inoltre, la manipolazione può essere vincolata dall'aggiunta di componenti di [vincoli di manipolazione](ConstraintManager.md#transform-constraints) all'oggetto.</span><span class="sxs-lookup"><span data-stu-id="ab5ab-118">As well as this, manipulation can be constrained by adding [manipulation constraint components](ConstraintManager.md#transform-constraints) to the object.</span></span> <span data-ttu-id="ab5ab-119">Si tratta di componenti speciali che funzionano con la manipolazione e modificano in qualche modo il comportamento di manipolazione.</span><span class="sxs-lookup"><span data-stu-id="ab5ab-119">These are special components that work with manipulation and change the manipulation behaviour in some way.</span></span>

![Gestore di manipolazione 1](../images/object-manipulator/MRTK_ObjectManipulator_Howto.png)

## <a name="inspector-properties-and-fields"></a><span data-ttu-id="ab5ab-121">Proprietà e campi di Inspector</span><span class="sxs-lookup"><span data-stu-id="ab5ab-121">Inspector properties and fields</span></span>

<img src="../images/object-manipulator/MRTK_ObjectManipulator_Structure.png" width="450" alt="Manupulator Structure">

### <a name="general-properties"></a><span data-ttu-id="ab5ab-122">Proprietà generali</span><span class="sxs-lookup"><span data-stu-id="ab5ab-122">General properties</span></span>

#### <a name="host-transform"></a><span data-ttu-id="ab5ab-123">Trasformazione host</span><span class="sxs-lookup"><span data-stu-id="ab5ab-123">Host transform</span></span>

<span data-ttu-id="ab5ab-124">Trasformazione dell'oggetto che verrà modificato.</span><span class="sxs-lookup"><span data-stu-id="ab5ab-124">The object transform that will be manipulated.</span></span> <span data-ttu-id="ab5ab-125">Il valore predefinito è l'oggetto del componente.</span><span class="sxs-lookup"><span data-stu-id="ab5ab-125">Defaults to the object of the component.</span></span>

#### <a name="manipulation-type"></a><span data-ttu-id="ab5ab-126">Tipo di manipolazione</span><span class="sxs-lookup"><span data-stu-id="ab5ab-126">Manipulation type</span></span>

<span data-ttu-id="ab5ab-127">Specifica se l'oggetto può essere modificato usando una sola mano o due mani.</span><span class="sxs-lookup"><span data-stu-id="ab5ab-127">Specifies whether the object can be manipulated using one hand or two hands.</span></span> <span data-ttu-id="ab5ab-128">Poiché questa proprietà è un flag, è possibile selezionare entrambe le opzioni.</span><span class="sxs-lookup"><span data-stu-id="ab5ab-128">Because this property is a flag, both options can be selected.</span></span>

- <span data-ttu-id="ab5ab-129">*Uno gestito*: Abilita una manipolazione gestita se selezionata.</span><span class="sxs-lookup"><span data-stu-id="ab5ab-129">*One handed*: Enables one handed manipulation if selected.</span></span>
- <span data-ttu-id="ab5ab-130">*Due gestite*: Abilita due manipolazioni gestite, se selezionate.</span><span class="sxs-lookup"><span data-stu-id="ab5ab-130">*Two handed*: Enables two handed manipulation if selected.</span></span>

#### <a name="allow-far-manipulation"></a><span data-ttu-id="ab5ab-131">Consenti manipolazione a lungo</span><span class="sxs-lookup"><span data-stu-id="ab5ab-131">Allow far manipulation</span></span>

<span data-ttu-id="ab5ab-132">Specifica se è possibile eseguire la manipolazione utilizzando l'interazione con i puntatori.</span><span class="sxs-lookup"><span data-stu-id="ab5ab-132">Specifies whether manipulation can be done using far interaction with pointers.</span></span>

### <a name="one-handed-manipulation-properties"></a><span data-ttu-id="ab5ab-133">Proprietà di manipolazione a una mano</span><span class="sxs-lookup"><span data-stu-id="ab5ab-133">One handed manipulation properties</span></span>

#### <a name="one-hand-rotation-mode-near"></a><span data-ttu-id="ab5ab-134">Modalità di rotazione a una mano vicino</span><span class="sxs-lookup"><span data-stu-id="ab5ab-134">One hand rotation mode near</span></span>

<span data-ttu-id="ab5ab-135">Specifica come si comporterà l'oggetto quando viene afferrato con una mano vicino a.</span><span class="sxs-lookup"><span data-stu-id="ab5ab-135">Specifies how the object will behave when it is being grabbed with one hand near.</span></span> <span data-ttu-id="ab5ab-136">Queste opzioni funzionano solo per le mani articolate.</span><span class="sxs-lookup"><span data-stu-id="ab5ab-136">These options only work for articulated hands.</span></span>

- <span data-ttu-id="ab5ab-137">*Ruota intorno al centro oggetti*: l'oggetto ruota usando la rotazione della mano, ma il punto centrale dell'oggetto.</span><span class="sxs-lookup"><span data-stu-id="ab5ab-137">*Rotate about object center*: Object rotates using rotation of the hand, but about the object center point.</span></span> <span data-ttu-id="ab5ab-138">L'oggetto comparirà in modo che lo spostamento risulti minore durante la rotazione, ma potrebbe esserci una sensazione di disconnessione tra la mano e l'oggetto.</span><span class="sxs-lookup"><span data-stu-id="ab5ab-138">The object will appear to move less as it rotates, but there may be a feeling of disconnection between the hand and the object.</span></span> <span data-ttu-id="ab5ab-139">Più utile per l'interazione di gran lunga.</span><span class="sxs-lookup"><span data-stu-id="ab5ab-139">More useful for far interaction.</span></span>
- <span data-ttu-id="ab5ab-140">*Ruota intorno al punto di* controllo: ruotare l'oggetto con la mano del punto di controllo tra il pollice e il dito dell'indice.</span><span class="sxs-lookup"><span data-stu-id="ab5ab-140">*Rotate about grab point*: Rotate object with the hand about the grab point between the thumb and index finger.</span></span> <span data-ttu-id="ab5ab-141">Dovrebbe essere considerato come se l'oggetto fosse mantenuto a mano.</span><span class="sxs-lookup"><span data-stu-id="ab5ab-141">It should feel as if the object is being held by the hand.</span></span>

#### <a name="one-hand-rotation-mode-far"></a><span data-ttu-id="ab5ab-142">Modalità di rotazione a una mano</span><span class="sxs-lookup"><span data-stu-id="ab5ab-142">One hand rotation mode far</span></span>

<span data-ttu-id="ab5ab-143">Specifica come si comporterà l'oggetto quando viene afferrato con una sola mano alla distanza.</span><span class="sxs-lookup"><span data-stu-id="ab5ab-143">Specifies how the object will behave when it is being grabbed with one hand at distance.</span></span> <span data-ttu-id="ab5ab-144">Queste opzioni funzionano solo per le mani articolate.</span><span class="sxs-lookup"><span data-stu-id="ab5ab-144">These options only work for articulated hands.</span></span>

- <span data-ttu-id="ab5ab-145">*Ruotare about Object Center*: ruotare l'oggetto usando la rotazione della mano, ma il punto centrale dell'oggetto.</span><span class="sxs-lookup"><span data-stu-id="ab5ab-145">*Rotate about object center*: Rotate object using rotation of the hand, but about the object center point.</span></span> <span data-ttu-id="ab5ab-146">Utile per esaminare a distanza senza che il centro oggetti si sposti durante la rotazione dell'oggetto.</span><span class="sxs-lookup"><span data-stu-id="ab5ab-146">Useful for inspecting at a distance without the object center moving as the object rotates.</span></span>
- <span data-ttu-id="ab5ab-147">*Ruota intorno al punto di* recupero: ruotare l'oggetto usando la rotazione della mano, ma il punto di riscontro del raggio puntatore.</span><span class="sxs-lookup"><span data-stu-id="ab5ab-147">*Rotate about grab point*: Rotate object using rotation of the hand, but about the pointer ray hit point.</span></span> <span data-ttu-id="ab5ab-148">Utile per l'ispezione.</span><span class="sxs-lookup"><span data-stu-id="ab5ab-148">Useful for inspection.</span></span>

### <a name="two-handed-manipulation-properties"></a><span data-ttu-id="ab5ab-149">Due proprietà di manipolazione gestite</span><span class="sxs-lookup"><span data-stu-id="ab5ab-149">Two handed manipulation properties</span></span>

#### <a name="two-handed-manipulation-type"></a><span data-ttu-id="ab5ab-150">Tipo di manipolazione a due mano</span><span class="sxs-lookup"><span data-stu-id="ab5ab-150">Two handed manipulation type</span></span>

<span data-ttu-id="ab5ab-151">Specifica il modo in cui due manipolazioni a mano possono trasformare un oggetto.</span><span class="sxs-lookup"><span data-stu-id="ab5ab-151">Specifies how two hand manipulation can transform an object.</span></span> <span data-ttu-id="ab5ab-152">Poiché questa proprietà è un flag, è possibile selezionare qualsiasi numero di opzioni.</span><span class="sxs-lookup"><span data-stu-id="ab5ab-152">Because this property is a flag, any number of options can be selected.</span></span>

- <span data-ttu-id="ab5ab-153">*Move*: lo spostamento è consentito se selezionato.</span><span class="sxs-lookup"><span data-stu-id="ab5ab-153">*Move*: Moving is allowed if selected.</span></span>
- <span data-ttu-id="ab5ab-154">*Scala*: il ridimensionamento è consentito se selezionato.</span><span class="sxs-lookup"><span data-stu-id="ab5ab-154">*Scale*: Scaling is allowed if selected.</span></span>
- <span data-ttu-id="ab5ab-155">*Rotazione: la* rotazione è consentita se selezionata.</span><span class="sxs-lookup"><span data-stu-id="ab5ab-155">*Rotate*: Rotation is allowed if selected.</span></span>

![Gestore di manipolazione 2](../images/manipulation-handler/MRTK_ManipulationHandler_TwoHanded.jpg)

### <a name="constraints"></a><span data-ttu-id="ab5ab-157">Vincoli</span><span class="sxs-lookup"><span data-stu-id="ab5ab-157">Constraints</span></span>

#### <a name="enable-constraints"></a><span data-ttu-id="ab5ab-158">Abilita vincoli</span><span class="sxs-lookup"><span data-stu-id="ab5ab-158">Enable constraints</span></span>

<span data-ttu-id="ab5ab-159">Questa impostazione consentirà di abilitare il [gestore di vincoli](ConstraintManager.md)collegati.</span><span class="sxs-lookup"><span data-stu-id="ab5ab-159">This setting will enable the linked [constraint manager](ConstraintManager.md).</span></span> <span data-ttu-id="ab5ab-160">Le modifiche alle trasformazioni verranno elaborate dai vincoli registrati per il [gestore di vincoli](ConstraintManager.md)selezionato.</span><span class="sxs-lookup"><span data-stu-id="ab5ab-160">Transform changes will be processed by constraints registered to the selected [constraint manager](ConstraintManager.md).</span></span>

#### <a name="constraint-manager"></a><span data-ttu-id="ab5ab-161">Gestione vincoli</span><span class="sxs-lookup"><span data-stu-id="ab5ab-161">Constraint manager</span></span>

<span data-ttu-id="ab5ab-162">L'elenco a discesa consente di selezionare qualsiasi [gestore di vincoli](ConstraintManager.md)associato.</span><span class="sxs-lookup"><span data-stu-id="ab5ab-162">The dropdown allows to select any of the attached [constraint managers](ConstraintManager.md).</span></span> <span data-ttu-id="ab5ab-163">Il manipolatore di oggetti garantisce la presenza di un [gestore di vincoli](ConstraintManager.md) sempre collegato.</span><span class="sxs-lookup"><span data-stu-id="ab5ab-163">Object manipulator ensures there's a [constraint manager](ConstraintManager.md) attached at all times.</span></span>
<span data-ttu-id="ab5ab-164">Si noti che più componenti dello stesso tipo vengono visualizzati con lo stesso nome in Unity.</span><span class="sxs-lookup"><span data-stu-id="ab5ab-164">Note that multiple components of the same type will show up under the same name in unity.</span></span> <span data-ttu-id="ab5ab-165">Per semplificare la distinzione tra più gestori di vincoli nello stesso oggetto, le opzioni disponibili visualizzeranno un hint per la configurazione del gestore di vincoli selezionato (selezione del vincolo manuale o automatica).</span><span class="sxs-lookup"><span data-stu-id="ab5ab-165">To make it easier to distinguish between multiple constraint managers on the same object, the available options will show a hint on the configuration of the selected constraint manager (manual or auto constraint selection).</span></span>

#### <a name="go-to-component"></a><span data-ttu-id="ab5ab-166">Vai al componente</span><span class="sxs-lookup"><span data-stu-id="ab5ab-166">Go to component</span></span>

<span data-ttu-id="ab5ab-167">La selezione di gestione vincoli viene fornita con un pulsante *Vai al componente* .</span><span class="sxs-lookup"><span data-stu-id="ab5ab-167">The constraint manager selection comes with a *Go to component* button.</span></span> <span data-ttu-id="ab5ab-168">Questo pulsante farà sì che il controllo Scorri fino al componente selezionato in modo che sia possibile configurarlo.</span><span class="sxs-lookup"><span data-stu-id="ab5ab-168">This button will cause the inspector to scroll to the selected component so that it can be configured.</span></span>

### <a name="physics"></a><span data-ttu-id="ab5ab-169">Fisica</span><span class="sxs-lookup"><span data-stu-id="ab5ab-169">Physics</span></span>

<span data-ttu-id="ab5ab-170">Le impostazioni in questa sezione vengono visualizzate solo quando l'oggetto include un componente RigidBody.</span><span class="sxs-lookup"><span data-stu-id="ab5ab-170">Settings in this section appear only when the object has a RigidBody component.</span></span>

#### <a name="release-behavior"></a><span data-ttu-id="ab5ab-171">Comportamento della versione</span><span class="sxs-lookup"><span data-stu-id="ab5ab-171">Release behavior</span></span>

<span data-ttu-id="ab5ab-172">Specificare le proprietà fisiche che un oggetto modificato deve tenere al rilascio.</span><span class="sxs-lookup"><span data-stu-id="ab5ab-172">Specify which physical properties a manipulated object should keep upon release.</span></span> <span data-ttu-id="ab5ab-173">Poiché questa proprietà è un flag, è possibile selezionare entrambe le opzioni.</span><span class="sxs-lookup"><span data-stu-id="ab5ab-173">Because this property is a flag, both options can be selected.</span></span>

- <span data-ttu-id="ab5ab-174">*Mantieni velocità*: quando l'oggetto viene rilasciato, se questa opzione è selezionata, manterrà la velocità lineare.</span><span class="sxs-lookup"><span data-stu-id="ab5ab-174">*Keep Velocity*: When the object is released, if this option is selected it will keep its linear velocity.</span></span>
- <span data-ttu-id="ab5ab-175">*Mantieni velocità angolare*: quando l'oggetto viene rilasciato, se questa opzione è selezionata, manterrà la velocità angolare.</span><span class="sxs-lookup"><span data-stu-id="ab5ab-175">*Keep Angular Velocity*: When the object is released, if this option is selected it will keep its angular velocity.</span></span>

#### <a name="use-forces-for-near-manipulation"></a><span data-ttu-id="ab5ab-176">USA Forces per la manipolazione quasi</span><span class="sxs-lookup"><span data-stu-id="ab5ab-176">Use forces for near manipulation</span></span>

<span data-ttu-id="ab5ab-177">Indica se vengono usate le forze di fisica per spostare l'oggetto quando si eseguono le modifiche più vicine.</span><span class="sxs-lookup"><span data-stu-id="ab5ab-177">Whether physics forces are used to move the object when performing near manipulations.</span></span> <span data-ttu-id="ab5ab-178">Se si imposta questa opzione su *false* , l'oggetto risulterà più connesso direttamente alla mano degli utenti.</span><span class="sxs-lookup"><span data-stu-id="ab5ab-178">Setting this to *false* will make the object feel more directly connected to the users hand.</span></span> <span data-ttu-id="ab5ab-179">L'impostazione di questa opzione su *true* rispetterà la massa e l'inerzia dell'oggetto, ma potrebbe essere considerato come se l'oggetto fosse connesso tramite una molla.</span><span class="sxs-lookup"><span data-stu-id="ab5ab-179">Setting this to *true* will honor the mass and inertia of the object, but may feel as though the object is connected through a spring.</span></span> <span data-ttu-id="ab5ab-180">Il valore predefinito è *false*.</span><span class="sxs-lookup"><span data-stu-id="ab5ab-180">The default is *false*.</span></span>

### <a name="smoothing"></a><span data-ttu-id="ab5ab-181">Definizione di movimenti uniformi</span><span class="sxs-lookup"><span data-stu-id="ab5ab-181">Smoothing</span></span>

#### <a name="smoothing-far"></a><span data-ttu-id="ab5ab-182">Smussamento lontano</span><span class="sxs-lookup"><span data-stu-id="ab5ab-182">Smoothing far</span></span>

<span data-ttu-id="ab5ab-183">Indica se la smussatura indipendente dalla frequenza dei fotogrammi è abilitata per le interazioni lontane.</span><span class="sxs-lookup"><span data-stu-id="ab5ab-183">Whether frame-rate independent smoothing is enabled for far interactions.</span></span> <span data-ttu-id="ab5ab-184">Per impostazione predefinita, la smussatura è abilitata.</span><span class="sxs-lookup"><span data-stu-id="ab5ab-184">Far smoothing is enabled by default.</span></span>

#### <a name="smoothing-near"></a><span data-ttu-id="ab5ab-185">Smussamento vicino</span><span class="sxs-lookup"><span data-stu-id="ab5ab-185">Smoothing near</span></span>

<span data-ttu-id="ab5ab-186">Se è abilitata la smussatura indipendente dalla frequenza dei frame per le interazioni near.</span><span class="sxs-lookup"><span data-stu-id="ab5ab-186">Whether frame-rate independent smoothing is enabled for near interactions.</span></span> <span data-ttu-id="ab5ab-187">Near smoothing è disabilitato per impostazione predefinita perché l'effetto può essere percepito come ' disconnected ' dalla mano.</span><span class="sxs-lookup"><span data-stu-id="ab5ab-187">Near smoothing is disabled by default because the effect may be perceived as being 'disconnected' from the hand.</span></span>

#### <a name="smoothing-active"></a><span data-ttu-id="ab5ab-188">Smoothing attivo</span><span class="sxs-lookup"><span data-stu-id="ab5ab-188">Smoothing active</span></span>

<span data-ttu-id="ab5ab-189">Obsoleto e verrà rimosso in una versione futura.</span><span class="sxs-lookup"><span data-stu-id="ab5ab-189">Obsolete and will be removed in a future version.</span></span> <span data-ttu-id="ab5ab-190">Le applicazioni devono usare SmoothingFar, SmoothingNear o una combinazione dei due.</span><span class="sxs-lookup"><span data-stu-id="ab5ab-190">Applications should use SmoothingFar, SmoothingNear or a combination of the two.</span></span>

#### <a name="move-lerp-time"></a><span data-ttu-id="ab5ab-191">Sposta Lerp tempo</span><span class="sxs-lookup"><span data-stu-id="ab5ab-191">Move lerp time</span></span>

<span data-ttu-id="ab5ab-192">Quantità di smussatura da applicare allo spostamento.</span><span class="sxs-lookup"><span data-stu-id="ab5ab-192">Amount of smoothing to apply to the movement.</span></span> <span data-ttu-id="ab5ab-193">L'uniformità di 0 significa nessuna smussatura.</span><span class="sxs-lookup"><span data-stu-id="ab5ab-193">Smoothing of 0 means no smoothing.</span></span> <span data-ttu-id="ab5ab-194">Il valore max significa nessuna modifica al valore.</span><span class="sxs-lookup"><span data-stu-id="ab5ab-194">Max value means no change to value.</span></span>

#### <a name="rotate-lerp-time"></a><span data-ttu-id="ab5ab-195">Ruota Lerp tempo</span><span class="sxs-lookup"><span data-stu-id="ab5ab-195">Rotate lerp time</span></span>

<span data-ttu-id="ab5ab-196">Quantità di smussatura da applicare alla rotazione.</span><span class="sxs-lookup"><span data-stu-id="ab5ab-196">Amount of smoothing to apply to the rotation.</span></span> <span data-ttu-id="ab5ab-197">L'uniformità di 0 significa nessuna smussatura.</span><span class="sxs-lookup"><span data-stu-id="ab5ab-197">Smoothing of 0 means no smoothing.</span></span> <span data-ttu-id="ab5ab-198">Il valore max significa nessuna modifica al valore.</span><span class="sxs-lookup"><span data-stu-id="ab5ab-198">Max value means no change to value.</span></span>

#### <a name="scale-lerp-time"></a><span data-ttu-id="ab5ab-199">Ridimensionamento Lerp tempo</span><span class="sxs-lookup"><span data-stu-id="ab5ab-199">Scale lerp time</span></span>

<span data-ttu-id="ab5ab-200">Quantità di smussatura da applicare alla scala.</span><span class="sxs-lookup"><span data-stu-id="ab5ab-200">Amount of smoothing to apply to the scale.</span></span> <span data-ttu-id="ab5ab-201">L'uniformità di 0 significa nessuna smussatura.</span><span class="sxs-lookup"><span data-stu-id="ab5ab-201">Smoothing of 0 means no smoothing.</span></span> <span data-ttu-id="ab5ab-202">Il valore max significa nessuna modifica al valore.</span><span class="sxs-lookup"><span data-stu-id="ab5ab-202">Max value means no change to value.</span></span>

### <a name="manipulation-events"></a><span data-ttu-id="ab5ab-203">Eventi di manipolazione</span><span class="sxs-lookup"><span data-stu-id="ab5ab-203">Manipulation events</span></span>

<span data-ttu-id="ab5ab-204">Il gestore di manipolazione fornisce gli eventi seguenti:</span><span class="sxs-lookup"><span data-stu-id="ab5ab-204">Manipulation handler provides the following events:</span></span>

- <span data-ttu-id="ab5ab-205">*OnManipulationStarted*: generato all'avvio della manipolazione.</span><span class="sxs-lookup"><span data-stu-id="ab5ab-205">*OnManipulationStarted*: Fired when manipulation starts.</span></span>
- <span data-ttu-id="ab5ab-206">*OnManipulationEnded*: viene attivato al termine della manipolazione.</span><span class="sxs-lookup"><span data-stu-id="ab5ab-206">*OnManipulationEnded*: Fires when the manipulation ends.</span></span>
- <span data-ttu-id="ab5ab-207">*OnHoverStarted*: viene attivato quando una mano o un controller passa il mouse sul manipolabile, quasi o lontano.</span><span class="sxs-lookup"><span data-stu-id="ab5ab-207">*OnHoverStarted*: Fires when a hand / controller hovers the manipulatable, near or far.</span></span>
- <span data-ttu-id="ab5ab-208">*OnHoverEnded*: viene attivato quando una mano o un controller Annulla il passaggio del mouse sul manipolabile, quasi o lontano.</span><span class="sxs-lookup"><span data-stu-id="ab5ab-208">*OnHoverEnded*: Fires when a hand / controller un-hovers the manipulatable, near or far.</span></span>

<span data-ttu-id="ab5ab-209">L'ordine di attivazione dell'evento per la manipolazione è:</span><span class="sxs-lookup"><span data-stu-id="ab5ab-209">The event fire order for manipulation is:</span></span>

<span data-ttu-id="ab5ab-210">*OnHoverStarted*  ->  *OnManipulationStarted*  ->  *OnManipulationEnded*  ->  *OnHoverEnded*</span><span class="sxs-lookup"><span data-stu-id="ab5ab-210">*OnHoverStarted* -> *OnManipulationStarted* -> *OnManipulationEnded* -> *OnHoverEnded*</span></span>

<span data-ttu-id="ab5ab-211">Se non è presente alcuna manipolazione, si otterranno comunque gli eventi hover con l'ordine di incendio seguente:</span><span class="sxs-lookup"><span data-stu-id="ab5ab-211">If there is no manipulation, you will still get hover events with the following fire order:</span></span>

<span data-ttu-id="ab5ab-212">*OnHoverStarted*  ->  *OnHoverEnded*</span><span class="sxs-lookup"><span data-stu-id="ab5ab-212">*OnHoverStarted* -> *OnHoverEnded*</span></span>

## <a name="physics-and-collisions"></a><span data-ttu-id="ab5ab-213">Fisica e collisioni</span><span class="sxs-lookup"><span data-stu-id="ab5ab-213">Physics and collisions</span></span>

<span data-ttu-id="ab5ab-214">Il comportamento fisico può essere abilitato aggiungendo un componente rigidbody allo stesso oggetto di un manipolatore di oggetti.</span><span class="sxs-lookup"><span data-stu-id="ab5ab-214">Physics behaviour can be enabled by adding a rigidbody component to the same object as an object manipulator.</span></span> <span data-ttu-id="ab5ab-215">Non solo questa operazione Abilita la configurazione del [comportamento di rilascio](#release-behavior) precedente, inoltre consente conflitti.</span><span class="sxs-lookup"><span data-stu-id="ab5ab-215">Not only does this enable configuration of [release behaviour](#release-behavior) above, it also enables collisions.</span></span> <span data-ttu-id="ab5ab-216">Senza un componente rigidbody, i conflitti non si comportano correttamente durante la manipolazione:</span><span class="sxs-lookup"><span data-stu-id="ab5ab-216">Without a rigidbody component, collisions don't behave correctly during manipulation:</span></span>

- <span data-ttu-id="ab5ab-217">I conflitti tra un oggetto modificato e un Collider statico (ovvero un oggetto con un Collider ma nessun rigidbody) non funzionano, l'oggetto modificato passa direttamente attraverso il Collider statico senza effetti.</span><span class="sxs-lookup"><span data-stu-id="ab5ab-217">Collisions between a manipulated object and a static collider (i.e. an object with a collider but no rigidbody) do not work, the manipulated object passes straight through the static collider unaffected.</span></span>
- <span data-ttu-id="ab5ab-218">Collisioni tra un oggetto modificato e un rigidbody (ad esempio</span><span class="sxs-lookup"><span data-stu-id="ab5ab-218">Collisions between a manipulated object and a rigidbody (i.e</span></span> <span data-ttu-id="ab5ab-219">un oggetto con un Collider e un rigidbody) fa sì che rigidbody abbia una risposta di collisione, ma la risposta è inattiva e non naturale.</span><span class="sxs-lookup"><span data-stu-id="ab5ab-219">an object with both a collider and a rigidbody) cause the rigidbody to have a collision response, but the response is jumpy and unnatural.</span></span> <span data-ttu-id="ab5ab-220">Non esiste inoltre alcuna risposta di collisione sull'oggetto modificato.</span><span class="sxs-lookup"><span data-stu-id="ab5ab-220">There is also no collision response on the manipulated object.</span></span>

<span data-ttu-id="ab5ab-221">Quando viene aggiunto un rigidbody, i conflitti dovrebbero funzionare correttamente.</span><span class="sxs-lookup"><span data-stu-id="ab5ab-221">When a rigidbody is added, collisions should work correctly.</span></span>

### <a name="without-rigidbody"></a><span data-ttu-id="ab5ab-222">Senza rigidbody</span><span class="sxs-lookup"><span data-stu-id="ab5ab-222">Without rigidbody</span></span>

<img src="../images/object-manipulator/MRTK_PhysicsManipulation_NoRigidbody.gif" width="500" alt="Not Rigid Body">

### <a name="with-rigidbody"></a><span data-ttu-id="ab5ab-223">Con rigidbody</span><span class="sxs-lookup"><span data-stu-id="ab5ab-223">With rigidbody</span></span>

<img src="../images/object-manipulator/MRTK_PhysicsManipulation_Rigidbody.gif" width="500" alt="Rigid Body">

## <a name="elastics-experimental"></a><span data-ttu-id="ab5ab-224">Elastici (sperimentale)</span><span class="sxs-lookup"><span data-stu-id="ab5ab-224">Elastics (Experimental)</span></span>

<span data-ttu-id="ab5ab-225">Gli elastici possono essere usati per la manipolazione di oggetti tramite il manipolatore di oggetti.</span><span class="sxs-lookup"><span data-stu-id="ab5ab-225">Elastics can be used when manipulating objects via object manipulator.</span></span> <span data-ttu-id="ab5ab-226">Si noti che il [sistema elastico](../elastics/ElasticSystem.md) è ancora in stato sperimentale.</span><span class="sxs-lookup"><span data-stu-id="ab5ab-226">Note that the [elastics system](../elastics/ElasticSystem.md) is still in experimental state.</span></span> <span data-ttu-id="ab5ab-227">Per abilitare gli elastici, collegare un componente di gestione elastici esistente o creare e collegare un nuovo gestore elastici tramite il `Add Elastics Manager` pulsante.</span><span class="sxs-lookup"><span data-stu-id="ab5ab-227">To enable elastics either link an existing elastics manager component or create and link a new elastics manager via the `Add Elastics Manager` button.</span></span>

<img src="../images/bounds-control/MRTK_BoundsControl_Elastics.png" width="450" alt="Bounds Control Elastics">

## <a name="see-also"></a><span data-ttu-id="ab5ab-228">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="ab5ab-228">See also</span></span>

- [<span data-ttu-id="ab5ab-229">Controllo dei limiti</span><span class="sxs-lookup"><span data-stu-id="ab5ab-229">Bounds control</span></span>](BoundsControl.md)
- [<span data-ttu-id="ab5ab-230">Gestione vincoli</span><span class="sxs-lookup"><span data-stu-id="ab5ab-230">Constraint manager</span></span>](ConstraintManager.md)
- [<span data-ttu-id="ab5ab-231">Finestra di migrazione</span><span class="sxs-lookup"><span data-stu-id="ab5ab-231">Migration window</span></span>](../tools/MigrationWindow.md)
- [<span data-ttu-id="ab5ab-232">Sistema elastici (sperimentale)</span><span class="sxs-lookup"><span data-stu-id="ab5ab-232">Elastics system (Experimental)</span></span>](../elastics/ElasticSystem.md)

---
title: Manipolatore di oggetti
description: Come usare il manipolatore di oggetti in MRTK
author: thalbern
ms.author: bethalha
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, manipolazione degli oggetti,
ms.openlocfilehash: f9b644c1447d6776389e227bfe49c27f82a3cf31
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176651"
---
# <a name="object-manipulator"></a><span data-ttu-id="544fe-104">Manipolatore di oggetti</span><span class="sxs-lookup"><span data-stu-id="544fe-104">Object manipulator</span></span>

![Manipolatore di oggetti](../images/manipulation-handler/MRTK_Manipulation_Main.png)

<span data-ttu-id="544fe-106">*ObjectManipulator è il* nuovo componente per il comportamento di manipolazione, disponibile in precedenza in *ManipulationHandler.*</span><span class="sxs-lookup"><span data-stu-id="544fe-106">The *ObjectManipulator* is the new component for manipulation behaviour, previously found in *ManipulationHandler*.</span></span> <span data-ttu-id="544fe-107">Il manipolatore di oggetti apporta una serie di miglioramenti e semplificazioni.</span><span class="sxs-lookup"><span data-stu-id="544fe-107">The object manipulator makes a number of improvements and simplifications.</span></span> <span data-ttu-id="544fe-108">Questo componente è una sostituzione per il gestore di manipolazione, che verrà deprecato.</span><span class="sxs-lookup"><span data-stu-id="544fe-108">This component is a replacement for the manipulation handler, which will be deprecated.</span></span>

<span data-ttu-id="544fe-109">Lo script *ObjectManipulator* rende un oggetto mobile, scalabile e rotabile usando una o due mani.</span><span class="sxs-lookup"><span data-stu-id="544fe-109">The *ObjectManipulator* script makes an object movable, scalable, and rotatable using one or two hands.</span></span> <span data-ttu-id="544fe-110">Il manipolatore di oggetti può essere configurato per controllare il modo in cui l'oggetto risponderà a vari input.</span><span class="sxs-lookup"><span data-stu-id="544fe-110">The object manipulator can be configured to control how the object will respond to various inputs.</span></span> <span data-ttu-id="544fe-111">Lo script dovrebbe funzionare con la maggior parte delle forme di interazione, ad esempio HoloLens 2 mano articolata, raggi della mano HoloLens 2, HoloLens 1 sguardo fisso e movimenti e l'input del controller del movimento del visore VR immersive.</span><span class="sxs-lookup"><span data-stu-id="544fe-111">The script should work with most forms of interaction, such as HoloLens 2 articulated hand, HoloLens 2 hand rays, HoloLens 1 gaze and gestures and immersive headset motion controller input.</span></span>

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Using-Object-Manipulator-in-Mixed-Reality-Toolkit/player]

## <a name="how-to-use-the-object-manipulator"></a><span data-ttu-id="544fe-112">Come usare il manipolatore di oggetti</span><span class="sxs-lookup"><span data-stu-id="544fe-112">How to use the object manipulator</span></span>

<span data-ttu-id="544fe-113">Per usare il manipolatore di oggetti, aggiungere prima di tutto il `ObjectManipulator` componente script a un GameObject.</span><span class="sxs-lookup"><span data-stu-id="544fe-113">To use the object manipulator, first add the `ObjectManipulator` script component to a GameObject.</span></span> <span data-ttu-id="544fe-114">Assicurarsi anche di aggiungere un collisore all'oggetto, corrispondente ai limiti afferrabili.</span><span class="sxs-lookup"><span data-stu-id="544fe-114">Make sure to also add a collider to the object, matching its grabbable bounds.</span></span>

<span data-ttu-id="544fe-115">Per fare in modo che l'oggetto risponda all'input della mano quasi articolato, aggiungere `NearInteractionGrabbable` anche lo script .</span><span class="sxs-lookup"><span data-stu-id="544fe-115">To make the object respond to near articulated hand input, add the `NearInteractionGrabbable` script as well.</span></span>

<span data-ttu-id="544fe-116">Il comportamento fisico può essere abilitato per il manipolatore di oggetti aggiungendo un componente rigidbody all'oggetto.</span><span class="sxs-lookup"><span data-stu-id="544fe-116">Physics behaviour can be enabled for the object manipulator by adding a rigidbody component to the object.</span></span> <span data-ttu-id="544fe-117">Il comportamento fisico abilitato con l'aggiunta di questo componente viene illustrato in modo più dettagliato in [*Fisica e collisioni.*](#physics-and-collisions)</span><span class="sxs-lookup"><span data-stu-id="544fe-117">Physics behaviour enabled by adding this component is discussed in greater detail in [*Physics and collisions*](#physics-and-collisions).</span></span>

<span data-ttu-id="544fe-118">Oltre a questo, la manipolazione può essere vincolata aggiungendo componenti [del vincolo di manipolazione](constraint-manager.md#transform-constraints) all'oggetto.</span><span class="sxs-lookup"><span data-stu-id="544fe-118">As well as this, manipulation can be constrained by adding [manipulation constraint components](constraint-manager.md#transform-constraints) to the object.</span></span> <span data-ttu-id="544fe-119">Si tratta di componenti speciali che funzionano con la manipolazione e modificano in qualche modo il comportamento di manipolazione.</span><span class="sxs-lookup"><span data-stu-id="544fe-119">These are special components that work with manipulation and change the manipulation behaviour in some way.</span></span>

![Uso del gestore di manipolazione nell'editor di Unity](../images/object-manipulator/MRTK_ObjectManipulator_Howto.png)

## <a name="inspector-properties-and-fields"></a><span data-ttu-id="544fe-121">Proprietà e campi del controllo</span><span class="sxs-lookup"><span data-stu-id="544fe-121">Inspector properties and fields</span></span>

<img src="../images/object-manipulator/MRTK_ObjectManipulator_Structure.png" width="450" alt="Object Manipulator Structure">

### <a name="general-properties"></a><span data-ttu-id="544fe-122">Proprietà generali</span><span class="sxs-lookup"><span data-stu-id="544fe-122">General properties</span></span>

#### <a name="host-transform"></a><span data-ttu-id="544fe-123">Trasformazione host</span><span class="sxs-lookup"><span data-stu-id="544fe-123">Host transform</span></span>

<span data-ttu-id="544fe-124">Trasformazione dell'oggetto che verrà modificato.</span><span class="sxs-lookup"><span data-stu-id="544fe-124">The object transform that will be manipulated.</span></span> <span data-ttu-id="544fe-125">Il valore predefinito è l'oggetto del componente.</span><span class="sxs-lookup"><span data-stu-id="544fe-125">Defaults to the object of the component.</span></span>

#### <a name="manipulation-type"></a><span data-ttu-id="544fe-126">Tipo di manipolazione</span><span class="sxs-lookup"><span data-stu-id="544fe-126">Manipulation type</span></span>

<span data-ttu-id="544fe-127">Specifica se l'oggetto può essere modificato usando una o due mani.</span><span class="sxs-lookup"><span data-stu-id="544fe-127">Specifies whether the object can be manipulated using one hand or two hands.</span></span> <span data-ttu-id="544fe-128">Poiché questa proprietà è un flag, è possibile selezionare entrambe le opzioni.</span><span class="sxs-lookup"><span data-stu-id="544fe-128">Because this property is a flag, both options can be selected.</span></span>

- <span data-ttu-id="544fe-129">*One handed (Una mano):* abilita la manipolazione con una mano, se selezionata.</span><span class="sxs-lookup"><span data-stu-id="544fe-129">*One handed*: Enables one handed manipulation if selected.</span></span>
- <span data-ttu-id="544fe-130">Two handed (Due *mani):* abilita la manipolazione a due mani, se selezionata.</span><span class="sxs-lookup"><span data-stu-id="544fe-130">*Two handed*: Enables two handed manipulation if selected.</span></span>

#### <a name="allow-far-manipulation"></a><span data-ttu-id="544fe-131">Consenti manipolazione da lontano</span><span class="sxs-lookup"><span data-stu-id="544fe-131">Allow far manipulation</span></span>

<span data-ttu-id="544fe-132">Specifica se la manipolazione può essere eseguita usando l'interazione da lontano con i puntatori.</span><span class="sxs-lookup"><span data-stu-id="544fe-132">Specifies whether manipulation can be done using far interaction with pointers.</span></span>

### <a name="one-handed-manipulation-properties"></a><span data-ttu-id="544fe-133">Proprietà di manipolazione con una mano</span><span class="sxs-lookup"><span data-stu-id="544fe-133">One handed manipulation properties</span></span>

#### <a name="one-hand-rotation-mode-near"></a><span data-ttu-id="544fe-134">Modalità di rotazione a una mano vicina</span><span class="sxs-lookup"><span data-stu-id="544fe-134">One hand rotation mode near</span></span>

<span data-ttu-id="544fe-135">Specifica il comportamento dell'oggetto quando viene afferrato con una mano vicina.</span><span class="sxs-lookup"><span data-stu-id="544fe-135">Specifies how the object will behave when it is being grabbed with one hand near.</span></span> <span data-ttu-id="544fe-136">Queste opzioni funzionano solo per le mani articolate.</span><span class="sxs-lookup"><span data-stu-id="544fe-136">These options only work for articulated hands.</span></span>

- <span data-ttu-id="544fe-137">*Ruota intorno al centro dell'oggetto:* l'oggetto ruota usando la rotazione della mano, ma intorno al punto centrale dell'oggetto.</span><span class="sxs-lookup"><span data-stu-id="544fe-137">*Rotate about object center*: Object rotates using rotation of the hand, but about the object center point.</span></span> <span data-ttu-id="544fe-138">L'oggetto apparirà meno spostato durante la rotazione, ma potrebbe esserci una sensazione di disconnessione tra la mano e l'oggetto.</span><span class="sxs-lookup"><span data-stu-id="544fe-138">The object will appear to move less as it rotates, but there may be a feeling of disconnection between the hand and the object.</span></span> <span data-ttu-id="544fe-139">Più utile per l'interazione da lontano.</span><span class="sxs-lookup"><span data-stu-id="544fe-139">More useful for far interaction.</span></span>
- <span data-ttu-id="544fe-140">*Ruotare intorno al punto di cattura:* ruotare l'oggetto con la mano intorno al punto di cattura tra il pollice e il dito indice.</span><span class="sxs-lookup"><span data-stu-id="544fe-140">*Rotate about grab point*: Rotate object with the hand about the grab point between the thumb and index finger.</span></span> <span data-ttu-id="544fe-141">Dovrebbe essere come se l'oggetto fosse tenuto dalla mano.</span><span class="sxs-lookup"><span data-stu-id="544fe-141">It should feel as if the object is being held by the hand.</span></span>

#### <a name="one-hand-rotation-mode-far"></a><span data-ttu-id="544fe-142">Modalità di rotazione a una mano da lontano</span><span class="sxs-lookup"><span data-stu-id="544fe-142">One hand rotation mode far</span></span>

<span data-ttu-id="544fe-143">Specifica il comportamento dell'oggetto quando viene afferrato con una mano alla distanza.</span><span class="sxs-lookup"><span data-stu-id="544fe-143">Specifies how the object will behave when it is being grabbed with one hand at distance.</span></span> <span data-ttu-id="544fe-144">Queste opzioni funzionano solo per le mani articolate.</span><span class="sxs-lookup"><span data-stu-id="544fe-144">These options only work for articulated hands.</span></span>

- <span data-ttu-id="544fe-145">*Ruotare intorno al centro dell'oggetto:* ruotare l'oggetto usando la rotazione della mano, ma intorno al punto centrale dell'oggetto.</span><span class="sxs-lookup"><span data-stu-id="544fe-145">*Rotate about object center*: Rotate object using rotation of the hand, but about the object center point.</span></span> <span data-ttu-id="544fe-146">Utile per controllare a una distanza senza spostare il centro dell'oggetto durante la rotazione dell'oggetto.</span><span class="sxs-lookup"><span data-stu-id="544fe-146">Useful for inspecting at a distance without the object center moving as the object rotates.</span></span>
- <span data-ttu-id="544fe-147">*Ruotare intorno al punto di afferrazione:* ruotare l'oggetto usando la rotazione della mano, ma intorno al punto di hit del raggio dell'indicatore di misura.</span><span class="sxs-lookup"><span data-stu-id="544fe-147">*Rotate about grab point*: Rotate object using rotation of the hand, but about the pointer ray hit point.</span></span> <span data-ttu-id="544fe-148">Utile per l'ispezione.</span><span class="sxs-lookup"><span data-stu-id="544fe-148">Useful for inspection.</span></span>

### <a name="two-handed-manipulation-properties"></a><span data-ttu-id="544fe-149">Proprietà di manipolazione a due mani</span><span class="sxs-lookup"><span data-stu-id="544fe-149">Two handed manipulation properties</span></span>

#### <a name="two-handed-manipulation-type"></a><span data-ttu-id="544fe-150">Tipo di manipolazione a due mani</span><span class="sxs-lookup"><span data-stu-id="544fe-150">Two handed manipulation type</span></span>

<span data-ttu-id="544fe-151">Specifica il modo in cui la manipolazione a due mani può trasformare un oggetto.</span><span class="sxs-lookup"><span data-stu-id="544fe-151">Specifies how two hand manipulation can transform an object.</span></span> <span data-ttu-id="544fe-152">Poiché questa proprietà è un flag, è possibile selezionare un numero qualsiasi di opzioni.</span><span class="sxs-lookup"><span data-stu-id="544fe-152">Because this property is a flag, any number of options can be selected.</span></span>

- <span data-ttu-id="544fe-153">*Move:* lo spostamento è consentito se selezionato.</span><span class="sxs-lookup"><span data-stu-id="544fe-153">*Move*: Moving is allowed if selected.</span></span>
- <span data-ttu-id="544fe-154">*Scalabilità:* il ridimensionamento è consentito se selezionato.</span><span class="sxs-lookup"><span data-stu-id="544fe-154">*Scale*: Scaling is allowed if selected.</span></span>
- <span data-ttu-id="544fe-155">*Ruota:* la rotazione è consentita se selezionata.</span><span class="sxs-lookup"><span data-stu-id="544fe-155">*Rotate*: Rotation is allowed if selected.</span></span>

![Gestore di manipolazione](../images/manipulation-handler/MRTK_ManipulationHandler_TwoHanded.jpg)

### <a name="constraints"></a><span data-ttu-id="544fe-157">Vincoli</span><span class="sxs-lookup"><span data-stu-id="544fe-157">Constraints</span></span>

#### <a name="enable-constraints"></a><span data-ttu-id="544fe-158">Abilitare i vincoli</span><span class="sxs-lookup"><span data-stu-id="544fe-158">Enable constraints</span></span>

<span data-ttu-id="544fe-159">Questa impostazione abiliterà la gestione [vincoli collegata.](constraint-manager.md)</span><span class="sxs-lookup"><span data-stu-id="544fe-159">This setting will enable the linked [constraint manager](constraint-manager.md).</span></span> <span data-ttu-id="544fe-160">Le modifiche di trasformazione verranno elaborate dai vincoli registrati nella gestione [vincoli selezionata.](constraint-manager.md)</span><span class="sxs-lookup"><span data-stu-id="544fe-160">Transform changes will be processed by constraints registered to the selected [constraint manager](constraint-manager.md).</span></span>

#### <a name="constraint-manager"></a><span data-ttu-id="544fe-161">Gestione vincoli</span><span class="sxs-lookup"><span data-stu-id="544fe-161">Constraint manager</span></span>

<span data-ttu-id="544fe-162">L'elenco a discesa consente di selezionare uno dei gestori [vincoli collegati.](constraint-manager.md)</span><span class="sxs-lookup"><span data-stu-id="544fe-162">The dropdown allows to select any of the attached [constraint managers](constraint-manager.md).</span></span> <span data-ttu-id="544fe-163">Il manipolatore di oggetti garantisce che sia [sempre collegato un](constraint-manager.md) gestore vincoli.</span><span class="sxs-lookup"><span data-stu-id="544fe-163">Object manipulator ensures there's a [constraint manager](constraint-manager.md) attached at all times.</span></span>
<span data-ttu-id="544fe-164">Si noti che più componenti dello stesso tipo verranno visualizzati con lo stesso nome in Unity.</span><span class="sxs-lookup"><span data-stu-id="544fe-164">Note that multiple components of the same type will show up under the same name in unity.</span></span> <span data-ttu-id="544fe-165">Per semplificare la distinzione tra più gestori vincoli nello stesso oggetto, nelle opzioni disponibili verrà visualizzato un hint per la configurazione della gestione vincoli selezionata (selezione manuale o automatica dei vincoli).</span><span class="sxs-lookup"><span data-stu-id="544fe-165">To make it easier to distinguish between multiple constraint managers on the same object, the available options will show a hint on the configuration of the selected constraint manager (manual or auto constraint selection).</span></span>

#### <a name="go-to-component"></a><span data-ttu-id="544fe-166">Vai al componente</span><span class="sxs-lookup"><span data-stu-id="544fe-166">Go to component</span></span>

<span data-ttu-id="544fe-167">La selezione di Gestione vincoli viene fornita con *un pulsante Vai al* componente.</span><span class="sxs-lookup"><span data-stu-id="544fe-167">The constraint manager selection comes with a *Go to component* button.</span></span> <span data-ttu-id="544fe-168">Questo pulsante fa scorrere il controllo fino al componente selezionato in modo che possa essere configurato.</span><span class="sxs-lookup"><span data-stu-id="544fe-168">This button will cause the inspector to scroll to the selected component so that it can be configured.</span></span>

### <a name="physics"></a><span data-ttu-id="544fe-169">Fisica</span><span class="sxs-lookup"><span data-stu-id="544fe-169">Physics</span></span>

<span data-ttu-id="544fe-170">Impostazioni in questa sezione vengono visualizzati solo quando l'oggetto ha un componente RigidBody.</span><span class="sxs-lookup"><span data-stu-id="544fe-170">Settings in this section appear only when the object has a RigidBody component.</span></span>

#### <a name="release-behavior"></a><span data-ttu-id="544fe-171">Comportamento di rilascio</span><span class="sxs-lookup"><span data-stu-id="544fe-171">Release behavior</span></span>

<span data-ttu-id="544fe-172">Specificare le proprietà fisiche che un oggetto modificato deve mantenere al momento del rilascio.</span><span class="sxs-lookup"><span data-stu-id="544fe-172">Specify which physical properties a manipulated object should keep upon release.</span></span> <span data-ttu-id="544fe-173">Poiché questa proprietà è un flag, è possibile selezionare entrambe le opzioni.</span><span class="sxs-lookup"><span data-stu-id="544fe-173">Because this property is a flag, both options can be selected.</span></span>

- <span data-ttu-id="544fe-174">*Mantieni velocità:* quando l'oggetto viene rilasciato, se questa opzione è selezionata, manterà la velocità lineare.</span><span class="sxs-lookup"><span data-stu-id="544fe-174">*Keep Velocity*: When the object is released, if this option is selected it will keep its linear velocity.</span></span>
- <span data-ttu-id="544fe-175">*Mantieni Angular velocità:* quando l'oggetto viene rilasciato, se questa opzione è selezionata, manterà la velocità angolare.</span><span class="sxs-lookup"><span data-stu-id="544fe-175">*Keep Angular Velocity*: When the object is released, if this option is selected it will keep its angular velocity.</span></span>

#### <a name="use-forces-for-near-manipulation"></a><span data-ttu-id="544fe-176">Usare le forze per la manipolazione da vicino</span><span class="sxs-lookup"><span data-stu-id="544fe-176">Use forces for near manipulation</span></span>

<span data-ttu-id="544fe-177">Indica se le forze fisiche vengono usate per spostare l'oggetto durante l'esecuzione di manipolazioni vicine.</span><span class="sxs-lookup"><span data-stu-id="544fe-177">Whether physics forces are used to move the object when performing near manipulations.</span></span> <span data-ttu-id="544fe-178">Impostando questo valore *su false,* l'oggetto sarà più direttamente connesso alla mano dell'utente.</span><span class="sxs-lookup"><span data-stu-id="544fe-178">Setting this to *false* will make the object feel more directly connected to the users hand.</span></span> <span data-ttu-id="544fe-179">L'impostazione di questa proprietà su *true* rispetta la massa e l'inerzia dell'oggetto, ma può sembrare che l'oggetto sia connesso tramite una spring.</span><span class="sxs-lookup"><span data-stu-id="544fe-179">Setting this to *true* will honor the mass and inertia of the object, but may feel as though the object is connected through a spring.</span></span> <span data-ttu-id="544fe-180">Il valore predefinito è *false*.</span><span class="sxs-lookup"><span data-stu-id="544fe-180">The default is *false*.</span></span>

### <a name="smoothing"></a><span data-ttu-id="544fe-181">Definizione di movimenti uniformi</span><span class="sxs-lookup"><span data-stu-id="544fe-181">Smoothing</span></span>

#### <a name="smoothing-far"></a><span data-ttu-id="544fe-182">Smussamento da lontano</span><span class="sxs-lookup"><span data-stu-id="544fe-182">Smoothing far</span></span>

<span data-ttu-id="544fe-183">Indica se la smussazione indipendente dalla frequenza dei fotogrammi è abilitata per le interazioni da lontano.</span><span class="sxs-lookup"><span data-stu-id="544fe-183">Whether frame-rate independent smoothing is enabled for far interactions.</span></span> <span data-ttu-id="544fe-184">L'arrotondamento di gran lunga è abilitato per impostazione predefinita.</span><span class="sxs-lookup"><span data-stu-id="544fe-184">Far smoothing is enabled by default.</span></span>

#### <a name="smoothing-near"></a><span data-ttu-id="544fe-185">Smussamento nelle vicinanze</span><span class="sxs-lookup"><span data-stu-id="544fe-185">Smoothing near</span></span>

<span data-ttu-id="544fe-186">Indica se la smussazione indipendente dalla frequenza dei fotogrammi è abilitata per le interazioni da vicino.</span><span class="sxs-lookup"><span data-stu-id="544fe-186">Whether frame-rate independent smoothing is enabled for near interactions.</span></span> <span data-ttu-id="544fe-187">La smussamento quasi è disabilitata per impostazione predefinita perché l'effetto può essere percepito come "disconnesso" dalla mano.</span><span class="sxs-lookup"><span data-stu-id="544fe-187">Near smoothing is disabled by default because the effect may be perceived as being 'disconnected' from the hand.</span></span>

#### <a name="smoothing-active"></a><span data-ttu-id="544fe-188">Smoothing attivo</span><span class="sxs-lookup"><span data-stu-id="544fe-188">Smoothing active</span></span>

<span data-ttu-id="544fe-189">Obsoleti e verranno rimossi in una versione futura.</span><span class="sxs-lookup"><span data-stu-id="544fe-189">Obsolete and will be removed in a future version.</span></span> <span data-ttu-id="544fe-190">Le applicazioni devono usare SmoothingFar, SmoothingNear o una combinazione dei due.</span><span class="sxs-lookup"><span data-stu-id="544fe-190">Applications should use SmoothingFar, SmoothingNear or a combination of the two.</span></span>

#### <a name="move-lerp-time"></a><span data-ttu-id="544fe-191">Tempo di spostamento del lerp</span><span class="sxs-lookup"><span data-stu-id="544fe-191">Move lerp time</span></span>

<span data-ttu-id="544fe-192">Quantità di smussamento da applicare al movimento.</span><span class="sxs-lookup"><span data-stu-id="544fe-192">Amount of smoothing to apply to the movement.</span></span> <span data-ttu-id="544fe-193">Smussamento di 0 significa nessuna smussamento.</span><span class="sxs-lookup"><span data-stu-id="544fe-193">Smoothing of 0 means no smoothing.</span></span> <span data-ttu-id="544fe-194">Il valore massimo indica che non viene apportata alcuna modifica al valore.</span><span class="sxs-lookup"><span data-stu-id="544fe-194">Max value means no change to value.</span></span>

#### <a name="rotate-lerp-time"></a><span data-ttu-id="544fe-195">Ruotare il tempo di lerp</span><span class="sxs-lookup"><span data-stu-id="544fe-195">Rotate lerp time</span></span>

<span data-ttu-id="544fe-196">Quantità di smussamento da applicare alla rotazione.</span><span class="sxs-lookup"><span data-stu-id="544fe-196">Amount of smoothing to apply to the rotation.</span></span> <span data-ttu-id="544fe-197">Smussamento di 0 significa nessuna smussamento.</span><span class="sxs-lookup"><span data-stu-id="544fe-197">Smoothing of 0 means no smoothing.</span></span> <span data-ttu-id="544fe-198">Il valore massimo indica che non viene apportata alcuna modifica al valore.</span><span class="sxs-lookup"><span data-stu-id="544fe-198">Max value means no change to value.</span></span>

#### <a name="scale-lerp-time"></a><span data-ttu-id="544fe-199">Ridimensionare il tempo di lerp</span><span class="sxs-lookup"><span data-stu-id="544fe-199">Scale lerp time</span></span>

<span data-ttu-id="544fe-200">Quantità di smussamento da applicare alla scala.</span><span class="sxs-lookup"><span data-stu-id="544fe-200">Amount of smoothing to apply to the scale.</span></span> <span data-ttu-id="544fe-201">L'arrotondamento di 0 significa nessuna smussamento.</span><span class="sxs-lookup"><span data-stu-id="544fe-201">Smoothing of 0 means no smoothing.</span></span> <span data-ttu-id="544fe-202">Il valore massimo indica che non viene apportata alcuna modifica al valore.</span><span class="sxs-lookup"><span data-stu-id="544fe-202">Max value means no change to value.</span></span>

### <a name="manipulation-events"></a><span data-ttu-id="544fe-203">Eventi di manipolazione</span><span class="sxs-lookup"><span data-stu-id="544fe-203">Manipulation events</span></span>

<span data-ttu-id="544fe-204">Il gestore di manipolazione fornisce gli eventi seguenti:</span><span class="sxs-lookup"><span data-stu-id="544fe-204">Manipulation handler provides the following events:</span></span>

- <span data-ttu-id="544fe-205">*OnManipulationStarted:* generato all'avvio della manipolazione.</span><span class="sxs-lookup"><span data-stu-id="544fe-205">*OnManipulationStarted*: Fired when manipulation starts.</span></span>
- <span data-ttu-id="544fe-206">*OnManipulationEnded:* viene generato al termine della manipolazione.</span><span class="sxs-lookup"><span data-stu-id="544fe-206">*OnManipulationEnded*: Fires when the manipulation ends.</span></span>
- <span data-ttu-id="544fe-207">*OnHoverStarted:* viene attivato quando una mano o un controller passa il puntatore del mouse sul manipolabile, vicino o lontano.</span><span class="sxs-lookup"><span data-stu-id="544fe-207">*OnHoverStarted*: Fires when a hand / controller hovers the manipulatable, near or far.</span></span>
- <span data-ttu-id="544fe-208">*OnHoverEnded:* viene attivato quando una mano o un controller annulla il passaggio del mouse sul manipolabile, vicino o lontano.</span><span class="sxs-lookup"><span data-stu-id="544fe-208">*OnHoverEnded*: Fires when a hand / controller un-hovers the manipulatable, near or far.</span></span>

<span data-ttu-id="544fe-209">L'ordine di generazione dell'evento per la manipolazione è:</span><span class="sxs-lookup"><span data-stu-id="544fe-209">The event fire order for manipulation is:</span></span>

<span data-ttu-id="544fe-210">*OnHoverStarted*  ->  *OnManipulationStarted*  ->  *OnManipulationEnded*  ->  *OnHoverEnded*</span><span class="sxs-lookup"><span data-stu-id="544fe-210">*OnHoverStarted* -> *OnManipulationStarted* -> *OnManipulationEnded* -> *OnHoverEnded*</span></span>

<span data-ttu-id="544fe-211">Se non è presente alcuna manipolazione, si otterrà comunque eventi hover con l'ordine di incendio seguente:</span><span class="sxs-lookup"><span data-stu-id="544fe-211">If there is no manipulation, you will still get hover events with the following fire order:</span></span>

<span data-ttu-id="544fe-212">*OnHoverStarted*  ->  *OnHoverEnded*</span><span class="sxs-lookup"><span data-stu-id="544fe-212">*OnHoverStarted* -> *OnHoverEnded*</span></span>

## <a name="physics-and-collisions"></a><span data-ttu-id="544fe-213">Fisica e collisioni</span><span class="sxs-lookup"><span data-stu-id="544fe-213">Physics and collisions</span></span>

<span data-ttu-id="544fe-214">Il comportamento fisico può essere abilitato aggiungendo un componente rigidbody allo stesso oggetto di un manipolatore di oggetti.</span><span class="sxs-lookup"><span data-stu-id="544fe-214">Physics behaviour can be enabled by adding a rigidbody component to the same object as an object manipulator.</span></span> <span data-ttu-id="544fe-215">Non solo abilita la configurazione del comportamento [di rilascio precedente,](#release-behavior) ma consente anche le collisioni.</span><span class="sxs-lookup"><span data-stu-id="544fe-215">Not only does this enable configuration of [release behaviour](#release-behavior) above, it also enables collisions.</span></span> <span data-ttu-id="544fe-216">Senza un componente rigidbody, le collisioni non si comportano correttamente durante la manipolazione:</span><span class="sxs-lookup"><span data-stu-id="544fe-216">Without a rigidbody component, collisions don't behave correctly during manipulation:</span></span>

- <span data-ttu-id="544fe-217">Le collisioni tra un oggetto manipolato e un collisore statico (ad esempio un oggetto con un collisore ma senza rigidbody) non funzionano, l'oggetto manipolato passa direttamente attraverso il collisore statico senza influenza.</span><span class="sxs-lookup"><span data-stu-id="544fe-217">Collisions between a manipulated object and a static collider (i.e. an object with a collider but no rigidbody) do not work, the manipulated object passes straight through the static collider unaffected.</span></span>
- <span data-ttu-id="544fe-218">Collisioni tra un oggetto manipolato e un rigidbody (ad esempio</span><span class="sxs-lookup"><span data-stu-id="544fe-218">Collisions between a manipulated object and a rigidbody (i.e</span></span> <span data-ttu-id="544fe-219">un oggetto con un collisore e un rigidbody) causa la risposta di collisione del rigidbody, ma la risposta è jumpy e innaturale.</span><span class="sxs-lookup"><span data-stu-id="544fe-219">an object with both a collider and a rigidbody) cause the rigidbody to have a collision response, but the response is jumpy and unnatural.</span></span> <span data-ttu-id="544fe-220">Non esiste inoltre alcuna risposta di collisione sull'oggetto modificato.</span><span class="sxs-lookup"><span data-stu-id="544fe-220">There is also no collision response on the manipulated object.</span></span>

<span data-ttu-id="544fe-221">Quando si aggiunge un rigidbody, le collisioni dovrebbero funzionare correttamente.</span><span class="sxs-lookup"><span data-stu-id="544fe-221">When a rigidbody is added, collisions should work correctly.</span></span>

### <a name="without-rigidbody"></a><span data-ttu-id="544fe-222">Senza rigidbody</span><span class="sxs-lookup"><span data-stu-id="544fe-222">Without rigidbody</span></span>

<img src="../images/object-manipulator/MRTK_PhysicsManipulation_NoRigidbody.gif" width="500" alt="No Rigid Body">

### <a name="with-rigidbody"></a><span data-ttu-id="544fe-223">Con rigidbody</span><span class="sxs-lookup"><span data-stu-id="544fe-223">With rigidbody</span></span>

<img src="../images/object-manipulator/MRTK_PhysicsManipulation_Rigidbody.gif" width="500" alt="Rigid Body">

## <a name="elastics-experimental"></a><span data-ttu-id="544fe-224">Elastici (sperimentale)</span><span class="sxs-lookup"><span data-stu-id="544fe-224">Elastics (Experimental)</span></span>

<span data-ttu-id="544fe-225">Gli elastici possono essere usati quando si modificano oggetti tramite il manipolatore di oggetti.</span><span class="sxs-lookup"><span data-stu-id="544fe-225">Elastics can be used when manipulating objects via object manipulator.</span></span> <span data-ttu-id="544fe-226">Si noti che il [sistema elastico](../experimental/elastic-system.md) è ancora in stato sperimentale.</span><span class="sxs-lookup"><span data-stu-id="544fe-226">Note that the [elastics system](../experimental/elastic-system.md) is still in experimental state.</span></span> <span data-ttu-id="544fe-227">Per abilitare gli elastici, collegare un componente di gestione elastici esistente oppure creare e collegare un nuovo gestore elastici tramite il `Add Elastics Manager` pulsante .</span><span class="sxs-lookup"><span data-stu-id="544fe-227">To enable elastics either link an existing elastics manager component or create and link a new elastics manager via the `Add Elastics Manager` button.</span></span>

<img src="../images/bounds-control/MRTK_BoundsControl_Elastics.png" width="450" alt="Bounds Control Elastics">

## <a name="see-also"></a><span data-ttu-id="544fe-228">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="544fe-228">See also</span></span>

- [<span data-ttu-id="544fe-229">Controllo Limiti</span><span class="sxs-lookup"><span data-stu-id="544fe-229">Bounds control</span></span>](bounds-control.md)
- [<span data-ttu-id="544fe-230">Gestione vincoli</span><span class="sxs-lookup"><span data-stu-id="544fe-230">Constraint manager</span></span>](constraint-manager.md)
- [<span data-ttu-id="544fe-231">Finestra di migrazione</span><span class="sxs-lookup"><span data-stu-id="544fe-231">Migration window</span></span>](../tools/migration-window.md)
- [<span data-ttu-id="544fe-232">Sistema elastico (sperimentale)</span><span class="sxs-lookup"><span data-stu-id="544fe-232">Elastics system (Experimental)</span></span>](../experimental/elastic-system.md)

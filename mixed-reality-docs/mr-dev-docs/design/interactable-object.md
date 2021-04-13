---
title: Oggetto che supporta interazioni
description: Informazioni su come attivare gli eventi, fornire segnali visivi e interagire con gli oggetti nelle applicazioni di realtà mista.
author: cre8ivepark
ms.author: v-hferrone
ms.date: 06/06/2019
ms.topic: article
keywords: Realtà mista, controlli, interazione, CUE, interfaccia utente, UX, auricolare realtà mista, auricolare di realtà mista, auricolare di realtà virtuale, HoloLens, MRTK, Toolkit realtà mista, audio
ms.openlocfilehash: 0e9f4dc09e3c4a4c38ffeb1a9042f39996918e36
ms.sourcegitcommit: 1c9035487270af76c6eaba11b11f6fc56c008135
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/13/2021
ms.locfileid: "107300466"
---
# <a name="interactable-object"></a><span data-ttu-id="c2a5d-104">Oggetto che supporta interazioni</span><span class="sxs-lookup"><span data-stu-id="c2a5d-104">Interactable object</span></span>

![Oggetti Interactible](images/UX_Hero_Interactable.jpg)

<span data-ttu-id="c2a5d-106">Un pulsante è a lungo una metafora usata per attivare un evento nel mondo astratto 2D.</span><span class="sxs-lookup"><span data-stu-id="c2a5d-106">A button has long been a metaphor used for triggering an event in the 2D abstract world.</span></span> <span data-ttu-id="c2a5d-107">Nel mondo della realtà mista tridimensionale, non dobbiamo più limitarci a questo mondo dell'astrazione.</span><span class="sxs-lookup"><span data-stu-id="c2a5d-107">In the three-dimensional mixed reality world, we don’t have to be confined to this world of abstraction anymore.</span></span> <span data-ttu-id="c2a5d-108">Qualsiasi elemento può essere un **oggetto interagibile** che attiva un evento.</span><span class="sxs-lookup"><span data-stu-id="c2a5d-108">Anything can be an **interactable object** that triggers an event.</span></span> <span data-ttu-id="c2a5d-109">Un oggetto interactabile può essere qualsiasi elemento da un Coffee Cup in una tabella a un fumetto a mezz'aria.</span><span class="sxs-lookup"><span data-stu-id="c2a5d-109">An interactable object can be anything from a coffee cup on a table to a balloon in midair.</span></span> <span data-ttu-id="c2a5d-110">Si usano ancora i pulsanti tradizionali in determinate situazioni, ad esempio nell'interfaccia utente della finestra di dialogo.</span><span class="sxs-lookup"><span data-stu-id="c2a5d-110">We still do make use of traditional buttons in certain situation such as in dialog UI.</span></span> <span data-ttu-id="c2a5d-111">La rappresentazione visiva del pulsante dipende dal contesto.</span><span class="sxs-lookup"><span data-stu-id="c2a5d-111">The visual representation of the button depends on the context.</span></span>

<br>

---

## <a name="important-properties-of-the-interactable-object"></a><span data-ttu-id="c2a5d-112">Proprietà importanti dell'oggetto interagibile</span><span class="sxs-lookup"><span data-stu-id="c2a5d-112">Important properties of the interactable object</span></span>

### <a name="visual-cues"></a><span data-ttu-id="c2a5d-113">Segnali visivi</span><span class="sxs-lookup"><span data-stu-id="c2a5d-113">Visual cues</span></span>

<span data-ttu-id="c2a5d-114">I segnali visivi sono segnali sensoriali della luce, ricevuti dall'occhio e elaborati dal sistema visivo durante la percezione visiva.</span><span class="sxs-lookup"><span data-stu-id="c2a5d-114">Visual cues are sensory cues from light, received by the eye, and processed by the visual system during visual perception.</span></span> <span data-ttu-id="c2a5d-115">Poiché il sistema visivo è dominante in molte specie, in particolare gli esseri umani, i segnali visivi rappresentano una grande fonte di informazioni in merito alla percezione del mondo.</span><span class="sxs-lookup"><span data-stu-id="c2a5d-115">Since the visual system is dominant in many species, especially humans, visual cues are a large source of information in how the world is perceived.</span></span>

<span data-ttu-id="c2a5d-116">Poiché gli oggetti olografici vengono combinati con l'ambiente reale in realtà mista, potrebbe essere difficile comprendere quali oggetti è possibile interagire.</span><span class="sxs-lookup"><span data-stu-id="c2a5d-116">Since the holographic objects are blended with the real-world environment in mixed reality, it could be difficult to understand which objects you can interact with.</span></span> <span data-ttu-id="c2a5d-117">Per tutti gli oggetti interagibili nell'esperienza, è importante fornire segnali visivi differenziati per ogni stato di input.</span><span class="sxs-lookup"><span data-stu-id="c2a5d-117">For any interactable objects in your experience, it's important to provide differentiated visual cues for each input state.</span></span> <span data-ttu-id="c2a5d-118">Ciò consente all'utente di comprendere quale parte dell'esperienza è interactabile e rende l'utente affidabile usando un metodo di interazione coerente.</span><span class="sxs-lookup"><span data-stu-id="c2a5d-118">This helps the user understand which part of your experience is interactable and makes the user confident by using a consistent interaction method.</span></span>

<br>

---

### <a name="far-interactions"></a><span data-ttu-id="c2a5d-119">Interazioni a distanza</span><span class="sxs-lookup"><span data-stu-id="c2a5d-119">Far interactions</span></span>

<span data-ttu-id="c2a5d-120">Per tutti gli oggetti che gli utenti possono interagire con lo sguardo, il raggio di mano e il raggio del controller di movimento, è consigliabile avere un segnale visivo diverso per questi tre stati di input:</span><span class="sxs-lookup"><span data-stu-id="c2a5d-120">For any objects that user can interact with gaze, hand ray, and motion controller's ray, we recommend having different visual cue for these three input states:</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="c2a5d-121">![Oggetto interactabile con stato predefinito](images/interactibleobject-states-default.jpg)</span><span class="sxs-lookup"><span data-stu-id="c2a5d-121">![Interactable object with default state](images/interactibleobject-states-default.jpg)</span></span><br>
       <span data-ttu-id="c2a5d-122">**Stato predefinito (osservazione)**</span><span class="sxs-lookup"><span data-stu-id="c2a5d-122">**Default (Observation) state**</span></span><br>
        <span data-ttu-id="c2a5d-123">Stato inattivo predefinito dell'oggetto.</span><span class="sxs-lookup"><span data-stu-id="c2a5d-123">Default idle state of the object.</span></span>
    <span data-ttu-id="c2a5d-124">Il cursore non è presente nell'oggetto.</span><span class="sxs-lookup"><span data-stu-id="c2a5d-124">The cursor isn't on the object.</span></span> <span data-ttu-id="c2a5d-125">La mano non è stata rilevata.</span><span class="sxs-lookup"><span data-stu-id="c2a5d-125">Hand isn't detected.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="c2a5d-126">![Oggetto interactabile con stato di destinazione e passaggio del mouse](images/interactibleobject-states-targeted.jpg)</span><span class="sxs-lookup"><span data-stu-id="c2a5d-126">![Interactable object with target and hover state](images/interactibleobject-states-targeted.jpg)</span></span><br>
        <span data-ttu-id="c2a5d-127">**Stato di destinazione (hover)**</span><span class="sxs-lookup"><span data-stu-id="c2a5d-127">**Targeted (Hover) state**</span></span><br>
        <span data-ttu-id="c2a5d-128">Quando l'oggetto è destinato a un cursore a sguardi, a una prossimità del dito o al puntatore del controller di movimento.</span><span class="sxs-lookup"><span data-stu-id="c2a5d-128">When the object is targeted with gaze cursor, finger proximity or motion controller's pointer.</span></span>
    <span data-ttu-id="c2a5d-129">Il cursore si trova sull'oggetto.</span><span class="sxs-lookup"><span data-stu-id="c2a5d-129">The cursor is on the object.</span></span> <span data-ttu-id="c2a5d-130">La mano è stata rilevata, pronta.</span><span class="sxs-lookup"><span data-stu-id="c2a5d-130">Hand is detected, ready.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="c2a5d-131">![Oggetto interactabile con stato premuto](images/interactibleobject-states-pressed.jpg)</span><span class="sxs-lookup"><span data-stu-id="c2a5d-131">![Interactable object with pressed state](images/interactibleobject-states-pressed.jpg)</span></span><br>
       <span data-ttu-id="c2a5d-132">**Stato premuto**</span><span class="sxs-lookup"><span data-stu-id="c2a5d-132">**Pressed state**</span></span><br>
        <span data-ttu-id="c2a5d-133">Quando l'oggetto viene premuto con un movimento di tocco aereo, premere il pulsante Seleziona del controller di movimento o del dito.</span><span class="sxs-lookup"><span data-stu-id="c2a5d-133">When the object is pressed with an air tap gesture, finger press or motion controller's select button.</span></span>
    <span data-ttu-id="c2a5d-134">Il cursore si trova sull'oggetto.</span><span class="sxs-lookup"><span data-stu-id="c2a5d-134">The cursor is on the object.</span></span> <span data-ttu-id="c2a5d-135">Viene rilevata una mano, aria toccata.</span><span class="sxs-lookup"><span data-stu-id="c2a5d-135">Hand is detected, air tapped.</span></span>
    :::column-end:::
:::row-end:::

<br>

---

<span data-ttu-id="c2a5d-136">È possibile usare tecniche come l'evidenziazione o il ridimensionamento per fornire segnali visivi per lo stato di input dell'utente.</span><span class="sxs-lookup"><span data-stu-id="c2a5d-136">You can use techniques such as highlighting or scaling to provide visual cues for the user’s input state.</span></span> <span data-ttu-id="c2a5d-137">In realtà mista, è possibile trovare esempi di visualizzazione di diversi Stati di input nel menu Start e con i pulsanti della barra delle applicazioni.</span><span class="sxs-lookup"><span data-stu-id="c2a5d-137">In mixed reality, you can find examples of visualizing different input states on the Start menu and with app bar buttons.</span></span> 

<span data-ttu-id="c2a5d-138">Ecco come appaiono questi stati in un **pulsante olografico**:</span><span class="sxs-lookup"><span data-stu-id="c2a5d-138">Here's what these states look like on a **holographic button**:</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="c2a5d-139">![Pulsante olografico in stato predefinito](images/MRTK_InteractableState-default.jpg)</span><span class="sxs-lookup"><span data-stu-id="c2a5d-139">![Holographic button in default state](images/MRTK_InteractableState-default.jpg)</span></span><br>
       <span data-ttu-id="c2a5d-140">**Stato predefinito (osservazione)**</span><span class="sxs-lookup"><span data-stu-id="c2a5d-140">**Default (Observation) state**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="c2a5d-141">![Pulsante olografico nello stato di destinazione e passaggio del mouse](images/MRTK_InteractableState-targeted.jpg)</span><span class="sxs-lookup"><span data-stu-id="c2a5d-141">![Holographic button in target and hover state](images/MRTK_InteractableState-targeted.jpg)</span></span><br>
        <span data-ttu-id="c2a5d-142">**Stato di destinazione (hover)**</span><span class="sxs-lookup"><span data-stu-id="c2a5d-142">**Targeted (Hover) state**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="c2a5d-143">![Pulsante olografico nello stato premuto](images/MRTK_InteractableState-pressed.jpg)</span><span class="sxs-lookup"><span data-stu-id="c2a5d-143">![Holographic button in pressed state](images/MRTK_InteractableState-pressed.jpg)</span></span><br>
       <span data-ttu-id="c2a5d-144">**Stato premuto**</span><span class="sxs-lookup"><span data-stu-id="c2a5d-144">**Pressed state**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

### <a name="near-interactions-direct"></a><span data-ttu-id="c2a5d-145">Near Interactions (Direct)</span><span class="sxs-lookup"><span data-stu-id="c2a5d-145">Near interactions (direct)</span></span> 

<span data-ttu-id="c2a5d-146">HoloLens 2 supporta l'input di rilevamento a mano articolato, che consente di interagire con gli oggetti.</span><span class="sxs-lookup"><span data-stu-id="c2a5d-146">HoloLens 2 supports articulated hand tracking input, which allows you to interact with objects.</span></span> <span data-ttu-id="c2a5d-147">Senza commenti e suggerimenti tattili e una profonda percezione della profondità, può essere difficile indicare la distanza della mano da un oggetto o se si sta toccando.</span><span class="sxs-lookup"><span data-stu-id="c2a5d-147">Without haptic feedback and perfect depth perception, it can be hard to tell how far away your hand is from an object or whether you're touching it.</span></span> <span data-ttu-id="c2a5d-148">È importante fornire segnali visivi sufficienti per comunicare lo stato dell'oggetto, in particolare lo stato delle mani in base a tale oggetto.</span><span class="sxs-lookup"><span data-stu-id="c2a5d-148">It's important to provide enough visual cues to communicate the state of the object, in particular the state of your hands based on that object.</span></span>

<span data-ttu-id="c2a5d-149">Usare il feedback visivo per comunicare gli Stati seguenti:</span><span class="sxs-lookup"><span data-stu-id="c2a5d-149">Use visual feedback to communicate the following states:</span></span>
* <span data-ttu-id="c2a5d-150">**Impostazione predefinita (osservazione)**: stato inattivo predefinito dell'oggetto.</span><span class="sxs-lookup"><span data-stu-id="c2a5d-150">**Default (Observation)**: Default idle state of the object.</span></span>
* <span data-ttu-id="c2a5d-151">**Hover**: quando una mano si avvicina a un ologramma, modificare gli oggetti visivi per comunicare che la mano è destinata a ologrammi.</span><span class="sxs-lookup"><span data-stu-id="c2a5d-151">**Hover**: When a hand is near a hologram, change visuals to communicate that hand is targeting hologram.</span></span> 
* <span data-ttu-id="c2a5d-152">**Distanza e punto di interazione**: la mano si avvicina a un ologramma, progetta commenti e suggerimenti per comunicare il punto di interazione proiettato e la distanza dall'oggetto del dito</span><span class="sxs-lookup"><span data-stu-id="c2a5d-152">**Distance and point of interaction**: As the hand approaches a hologram, design feedback to communicate the projected point of interaction, and how far from the object the finger is</span></span>
* <span data-ttu-id="c2a5d-153">**Inizio contatto**: modificare gli oggetti visivi (chiaro, colore) per comunicare che si è verificato un tocco</span><span class="sxs-lookup"><span data-stu-id="c2a5d-153">**Contact begins**: Change visuals (light, color) to communicate that a touch has occurred</span></span>
* <span data-ttu-id="c2a5d-154">**Colto**: modificare gli oggetti visivi (chiaro, colore) quando l'oggetto viene afferrato</span><span class="sxs-lookup"><span data-stu-id="c2a5d-154">**Grasped**: Change visuals (light, color) when the object is grasped</span></span>
* <span data-ttu-id="c2a5d-155">**Estremità del contatto**: modificare gli oggetti visivi (chiaro, colore) al termine del tocco</span><span class="sxs-lookup"><span data-stu-id="c2a5d-155">**Contact ends**: Change visuals (light, color) when touch has ended</span></span>

<br>

---

:::row:::
    :::column:::
        <span data-ttu-id="c2a5d-156">![Passaggio del mouse (lontano)](images/640px-interactibleobject-states-near-hover.jpg)</span><span class="sxs-lookup"><span data-stu-id="c2a5d-156">![Hover (Far)](images/640px-interactibleobject-states-near-hover.jpg)</span></span><br>
        <span data-ttu-id="c2a5d-157">**Passaggio del mouse (lontano)**</span><span class="sxs-lookup"><span data-stu-id="c2a5d-157">**Hover (Far)**</span></span><br>
        <span data-ttu-id="c2a5d-158">Evidenziazione basata sulla prossimità del manuale.</span><span class="sxs-lookup"><span data-stu-id="c2a5d-158">Highlighting based on the proximity of the hand.</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="c2a5d-159">![Passaggio del mouse (vicino)](images/640px-interactibleobject-states-near-hovernear.jpg)</span><span class="sxs-lookup"><span data-stu-id="c2a5d-159">![Hover (Near)](images/640px-interactibleobject-states-near-hovernear.jpg)</span></span><br>
        <span data-ttu-id="c2a5d-160">**Passaggio del mouse (vicino)**</span><span class="sxs-lookup"><span data-stu-id="c2a5d-160">**Hover (Near)**</span></span><br>
        <span data-ttu-id="c2a5d-161">Evidenziare le modifiche delle dimensioni in base alla distanza della mano.</span><span class="sxs-lookup"><span data-stu-id="c2a5d-161">Highlight size changes based on the distance to the hand.</span></span>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        <span data-ttu-id="c2a5d-162">![Tocco/pressione](images/640px-interactibleobject-states-near-press.jpg)</span><span class="sxs-lookup"><span data-stu-id="c2a5d-162">![Touch / press](images/640px-interactibleobject-states-near-press.jpg)</span></span><br>
        <span data-ttu-id="c2a5d-163">**Tocco/pressione**</span><span class="sxs-lookup"><span data-stu-id="c2a5d-163">**Touch / press**</span></span><br>
        <span data-ttu-id="c2a5d-164">Commenti visivi e audio.</span><span class="sxs-lookup"><span data-stu-id="c2a5d-164">Visual plus audio feedback.</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="c2a5d-165">![Comprendere](images/640px-interactibleobject-states-near-grasp.jpg)</span><span class="sxs-lookup"><span data-stu-id="c2a5d-165">![Grasp](images/640px-interactibleobject-states-near-grasp.jpg)</span></span><br>
        <span data-ttu-id="c2a5d-166">**Comprendere**</span><span class="sxs-lookup"><span data-stu-id="c2a5d-166">**Grasp**</span></span><br>
        <span data-ttu-id="c2a5d-167">Commenti visivi e audio.</span><span class="sxs-lookup"><span data-stu-id="c2a5d-167">Visual plus audio feedback.</span></span>
    :::column-end:::
:::row-end:::

<br>

<br>

---

<span data-ttu-id="c2a5d-168">Un [pulsante in HoloLens 2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html) è un esempio di visualizzazione dei diversi Stati di interazione di input:</span><span class="sxs-lookup"><span data-stu-id="c2a5d-168">A [button on HoloLens 2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html) is an example of how the different input interaction states are visualized:</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="c2a5d-169">![Valore predefinito](images/640px-interactibleobject-pressablebutton-default.jpg)</span><span class="sxs-lookup"><span data-stu-id="c2a5d-169">![Default](images/640px-interactibleobject-pressablebutton-default.jpg)</span></span><br>
        <span data-ttu-id="c2a5d-170">**Default**</span><span class="sxs-lookup"><span data-stu-id="c2a5d-170">**Default**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="c2a5d-171">![Passaggio del mouse](images/640px-interactibleobject-pressablebutton-hover.jpg)</span><span class="sxs-lookup"><span data-stu-id="c2a5d-171">![Hover](images/640px-interactibleobject-pressablebutton-hover.jpg)</span></span><br>
        <span data-ttu-id="c2a5d-172">**Passaggio del mouse**</span><span class="sxs-lookup"><span data-stu-id="c2a5d-172">**Hover**</span></span><br>
        <span data-ttu-id="c2a5d-173">Rivelare un effetto di illuminazione basato su prossimità.</span><span class="sxs-lookup"><span data-stu-id="c2a5d-173">Reveal a proximity-based lighting effect.</span></span>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        <span data-ttu-id="c2a5d-174">![Tocco](images/640px-interactibleobject-pressablebutton-touch.jpg)</span><span class="sxs-lookup"><span data-stu-id="c2a5d-174">![Touch](images/640px-interactibleobject-pressablebutton-touch.jpg)</span></span><br>
        <span data-ttu-id="c2a5d-175">**Tocco**</span><span class="sxs-lookup"><span data-stu-id="c2a5d-175">**Touch**</span></span><br>
        <span data-ttu-id="c2a5d-176">Mostra effetto Ripple.</span><span class="sxs-lookup"><span data-stu-id="c2a5d-176">Show ripple effect.</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="c2a5d-177">![Premere](images/640px-interactibleobject-pressablebutton-press.jpg)</span><span class="sxs-lookup"><span data-stu-id="c2a5d-177">![Press](images/640px-interactibleobject-pressablebutton-press.jpg)</span></span><br>
        <span data-ttu-id="c2a5d-178">**Premere**</span><span class="sxs-lookup"><span data-stu-id="c2a5d-178">**Press**</span></span><br>
        <span data-ttu-id="c2a5d-179">Spostare il pannello anteriore.</span><span class="sxs-lookup"><span data-stu-id="c2a5d-179">Move the front plate.</span></span>
    :::column-end:::
:::row-end:::

<br>

---

:::row:::
    :::column:::
        ### <a name="the-ring-visual-cue-on-hololens-2br"></a><span data-ttu-id="c2a5d-180">Il segnale visivo "Ring" su HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="c2a5d-180">The "ring" visual cue on HoloLens 2</span></span><br>
        <span data-ttu-id="c2a5d-181">In HoloLens 2 è presente un segnale visivo aggiuntivo che può aiutare la percezione dell'utente della profondità.</span><span class="sxs-lookup"><span data-stu-id="c2a5d-181">On HoloLens 2, there's an extra visual cue, which can help the user's perception of depth.</span></span> <span data-ttu-id="c2a5d-182">Un anello vicino alla loro parte viene visualizzato e ridimensionato quando il dito si avvicina all'oggetto.</span><span class="sxs-lookup"><span data-stu-id="c2a5d-182">A ring near their fingertip shows up and scales down as the fingertip gets closer to the object.</span></span> <span data-ttu-id="c2a5d-183">L'anello alla fine converge in un punto quando viene raggiunto lo stato premuto.</span><span class="sxs-lookup"><span data-stu-id="c2a5d-183">The ring eventually converges into a dot when the pressed state is reached.</span></span> <span data-ttu-id="c2a5d-184">Questa convenienza visiva consente all'utente di comprendere la distanza dall'oggetto.</span><span class="sxs-lookup"><span data-stu-id="c2a5d-184">This visual affordance helps the user understand how far they are from the object.</span></span><br>
        <br>
        <span data-ttu-id="c2a5d-185">*Ciclo video: esempio di feedback visivo basato sulla prossimità a un rettangolo di delimitazione*</span><span class="sxs-lookup"><span data-stu-id="c2a5d-185">*Video loop: Example of visual feedback based on proximity to a bounding box*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="c2a5d-186">![space](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="c2a5d-186">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="c2a5d-187">![Feedback visivo sulla prossimità della mano](images/HoloLens2_Proximity.gif)</span><span class="sxs-lookup"><span data-stu-id="c2a5d-187">![Visual feedback on hand proximity](images/HoloLens2_Proximity.gif)</span></span><br>
    :::column-end:::
:::row-end:::


<br>

---


### <a name="audio-cues"></a><span data-ttu-id="c2a5d-188">Segnali audio</span><span class="sxs-lookup"><span data-stu-id="c2a5d-188">Audio cues</span></span>

<span data-ttu-id="c2a5d-189">Per le interazioni dirette, il feedback audio appropriato può migliorare notevolmente l'esperienza utente.</span><span class="sxs-lookup"><span data-stu-id="c2a5d-189">For direct hand interactions, proper audio feedback can dramatically improve the user experience.</span></span> <span data-ttu-id="c2a5d-190">Usare il feedback audio per comunicare i segnali seguenti:</span><span class="sxs-lookup"><span data-stu-id="c2a5d-190">Use audio feedback to communicate the following cues:</span></span>
* <span data-ttu-id="c2a5d-191">**Inizio contatto**: riprodurre un suono quando inizia il tocco</span><span class="sxs-lookup"><span data-stu-id="c2a5d-191">**Contact begins**: Play sound when touch begins</span></span>
* <span data-ttu-id="c2a5d-192">**Terminazione contatto**: riprodurre un suono al termine del tocco</span><span class="sxs-lookup"><span data-stu-id="c2a5d-192">**Contact ends**: Play sound on touch end</span></span>
* <span data-ttu-id="c2a5d-193">**Inizio** avvio: riprodurre un suono quando viene avviata la cattura</span><span class="sxs-lookup"><span data-stu-id="c2a5d-193">**Grab begins**: Play sound when grab starts</span></span>
* <span data-ttu-id="c2a5d-194">**Estremità** di chiusura: riprodurre un suono quando termina la cattura</span><span class="sxs-lookup"><span data-stu-id="c2a5d-194">**Grab ends**: Play sound when grab ends</span></span>

<br>

---

:::row:::
    :::column:::
        ### <a name="voice-commandingbr"></a><span data-ttu-id="c2a5d-195">Esecuzione di comandi vocali</span><span class="sxs-lookup"><span data-stu-id="c2a5d-195">Voice commanding</span></span><br>
        <span data-ttu-id="c2a5d-196">Per tutti gli oggetti interagibili, è importante supportare opzioni di interazione alternative.</span><span class="sxs-lookup"><span data-stu-id="c2a5d-196">For any interactable objects, it's important to support alternative interaction options.</span></span> <span data-ttu-id="c2a5d-197">Per impostazione predefinita, è consigliabile che i [comandi vocali](../out-of-scope/voice-design.md) siano supportati per gli oggetti che possono interagire.</span><span class="sxs-lookup"><span data-stu-id="c2a5d-197">By default, we recommend that [voice commanding](../out-of-scope/voice-design.md) be supported for any objects that are interactable.</span></span> <span data-ttu-id="c2a5d-198">Per migliorare l'individuabilità, è anche possibile fornire una descrizione comando durante lo stato del passaggio del mouse.</span><span class="sxs-lookup"><span data-stu-id="c2a5d-198">To improve discoverability, you can also provide a tooltip during the hover state.</span></span><br>
        <br>
        <span data-ttu-id="c2a5d-199">*Image: descrizione comando per il comando Voice*</span><span class="sxs-lookup"><span data-stu-id="c2a5d-199">*Image: Tooltip for the voice command*</span></span>
    :::column-end:::
        :::column:::
       ![comando vocale](images/640px-interactibleobject-voicecommand.png)<br>
    :::column-end:::
:::row-end:::


<br>

---

## <a name="sizing-recommendations"></a><span data-ttu-id="c2a5d-201">Consigli sul ridimensionamento</span><span class="sxs-lookup"><span data-stu-id="c2a5d-201">Sizing recommendations</span></span>

<span data-ttu-id="c2a5d-202">Per assicurarsi che tutti gli oggetti interagibili possano essere facilmente modificati, è consigliabile assicurarsi che l'interoperabilità soddisfi le dimensioni minime in base alla distanza che viene effettuata dall'utente.</span><span class="sxs-lookup"><span data-stu-id="c2a5d-202">To ensure all interactable objects can easily be touched, we recommend making sure the interactable meets a minimum size based on the distance it's placed from the user.</span></span> <span data-ttu-id="c2a5d-203">L'angolo visivo è spesso misurato in gradi di Visual Arc. L'angolo visivo è basato sulla distanza tra gli occhi dell'utente e l'oggetto e rimane costante, mentre la dimensione fisica della destinazione può variare a seconda della distanza tra le modifiche apportate dall'utente.</span><span class="sxs-lookup"><span data-stu-id="c2a5d-203">The visual angle is often measured in degrees of visual arc. Visual angle is based on the distance between the user's eyes and the object and stays constant, while the physical size of the target may change as the distance from the user changes.</span></span> <span data-ttu-id="c2a5d-204">Per determinare le dimensioni fisiche necessarie di un oggetto in base alla distanza dall'utente, provare a usare un calcolo dell'angolo visivo come [questo](https://elvers.us/perception/visualAngle/).</span><span class="sxs-lookup"><span data-stu-id="c2a5d-204">To determine the necessary physical size of an object based on the distance from the user, try using a visual angle calculator such as [this one](https://elvers.us/perception/visualAngle/).</span></span>

<span data-ttu-id="c2a5d-205">Di seguito sono riportati i consigli per le dimensioni minime del contenuto interactabile.</span><span class="sxs-lookup"><span data-stu-id="c2a5d-205">Below are the recommendations for minimum sizes of interactable content.</span></span>

### <a name="target-size-for-direct-hand-interaction"></a><span data-ttu-id="c2a5d-206">Dimensioni di destinazione per l'interazione diretta con la mano</span><span class="sxs-lookup"><span data-stu-id="c2a5d-206">Target size for direct hand interaction</span></span>

| <span data-ttu-id="c2a5d-207">Distanza</span><span class="sxs-lookup"><span data-stu-id="c2a5d-207">Distance</span></span> | <span data-ttu-id="c2a5d-208">Angolo di visualizzazione</span><span class="sxs-lookup"><span data-stu-id="c2a5d-208">Viewing angle</span></span> | <span data-ttu-id="c2a5d-209">Dimensione</span><span class="sxs-lookup"><span data-stu-id="c2a5d-209">Size</span></span> |
|---------|---------|---------|
| <span data-ttu-id="c2a5d-210">45 cm</span><span class="sxs-lookup"><span data-stu-id="c2a5d-210">45 cm</span></span>  | <span data-ttu-id="c2a5d-211">non inferiore a 2 °</span><span class="sxs-lookup"><span data-stu-id="c2a5d-211">no smaller than 2°</span></span> | <span data-ttu-id="c2a5d-212">1,6 x 1,6 cm</span><span class="sxs-lookup"><span data-stu-id="c2a5d-212">1.6 x 1.6 cm</span></span> |

<span data-ttu-id="c2a5d-213">![Dimensioni di destinazione per l'interazione diretta con la mano](images/TargetSizingNear.jpg)</span><span class="sxs-lookup"><span data-stu-id="c2a5d-213">![Target size for direct hand interaction](images/TargetSizingNear.jpg)</span></span><br>
<span data-ttu-id="c2a5d-214">*Dimensioni di destinazione per l'interazione diretta con la mano*</span><span class="sxs-lookup"><span data-stu-id="c2a5d-214">*Target size for direct hand interaction*</span></span>

<br>

### <a name="target-size-for-buttons"></a><span data-ttu-id="c2a5d-215">Dimensioni di destinazione per i pulsanti</span><span class="sxs-lookup"><span data-stu-id="c2a5d-215">Target size for buttons</span></span>

<span data-ttu-id="c2a5d-216">Quando si creano i pulsanti per l'interazione diretta, si consiglia una dimensione minima maggiore di 3,2 x 3,2 cm per assicurarsi che lo spazio disponibile sia sufficiente per contenere un'icona e potenzialmente un testo.</span><span class="sxs-lookup"><span data-stu-id="c2a5d-216">When creating buttons for direct interaction, we recommend a larger minimum size of 3.2 x 3.2 cm to ensure that there's enough space to contain an icon and potentially some text.</span></span>

| <span data-ttu-id="c2a5d-217">Distanza</span><span class="sxs-lookup"><span data-stu-id="c2a5d-217">Distance</span></span> | <span data-ttu-id="c2a5d-218">Dimensione minima</span><span class="sxs-lookup"><span data-stu-id="c2a5d-218">Minimum size</span></span> |
|---------|---------|
| <span data-ttu-id="c2a5d-219">45 cm</span><span class="sxs-lookup"><span data-stu-id="c2a5d-219">45 cm</span></span>  | <span data-ttu-id="c2a5d-220">3,2 x 3,2 cm</span><span class="sxs-lookup"><span data-stu-id="c2a5d-220">3.2 x 3.2 cm</span></span> |

<span data-ttu-id="c2a5d-221">![Dimensioni di destinazione per i pulsanti](images/TargetSizingButtons.png)</span><span class="sxs-lookup"><span data-stu-id="c2a5d-221">![Target size for the buttons](images/TargetSizingButtons.png)</span></span><br>
<span data-ttu-id="c2a5d-222">*Dimensioni di destinazione per i pulsanti*</span><span class="sxs-lookup"><span data-stu-id="c2a5d-222">*Target size for the buttons*</span></span>

<br>

### <a name="target-size-for-hand-ray-or-gaze-interaction"></a><span data-ttu-id="c2a5d-223">Dimensioni di destinazione per l'interazione con raggio o sguardo</span><span class="sxs-lookup"><span data-stu-id="c2a5d-223">Target size for hand ray or gaze interaction</span></span>
| <span data-ttu-id="c2a5d-224">Distanza</span><span class="sxs-lookup"><span data-stu-id="c2a5d-224">Distance</span></span> | <span data-ttu-id="c2a5d-225">Angolo di visualizzazione</span><span class="sxs-lookup"><span data-stu-id="c2a5d-225">Viewing angle</span></span> | <span data-ttu-id="c2a5d-226">Dimensione</span><span class="sxs-lookup"><span data-stu-id="c2a5d-226">Size</span></span> |
|---------|---------|---------|
| <span data-ttu-id="c2a5d-227">2 m</span><span class="sxs-lookup"><span data-stu-id="c2a5d-227">2 m</span></span>  | <span data-ttu-id="c2a5d-228">non minore di 1 °</span><span class="sxs-lookup"><span data-stu-id="c2a5d-228">no smaller than 1°</span></span> | <span data-ttu-id="c2a5d-229">3,5 x 3,5 cm</span><span class="sxs-lookup"><span data-stu-id="c2a5d-229">3.5 x 3.5 cm</span></span> |

<span data-ttu-id="c2a5d-230">![Dimensioni di destinazione per l'interazione con raggio o sguardo](images/TargetSizingFar.jpg)</span><span class="sxs-lookup"><span data-stu-id="c2a5d-230">![Target size for hand ray or gaze interaction](images/TargetSizingFar.jpg)</span></span><br>
<span data-ttu-id="c2a5d-231">*Dimensioni di destinazione per l'interazione con raggio o sguardo*</span><span class="sxs-lookup"><span data-stu-id="c2a5d-231">*Target size for hand ray or gaze interaction*</span></span>

<br>

---

## <a name="interactable-object-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="c2a5d-232">Oggetto interactabile in MRTK (Mixed Reality Toolkit) per Unity</span><span class="sxs-lookup"><span data-stu-id="c2a5d-232">Interactable object in MRTK (Mixed Reality Toolkit) for Unity</span></span>

<span data-ttu-id="c2a5d-233">In **[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** è possibile usare lo script [**interactable**](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Interactable/Scripts) per fare in modo che gli oggetti rispondano a diversi tipi di Stati di interazione di input.</span><span class="sxs-lookup"><span data-stu-id="c2a5d-233">In **[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)**, you can use the script [**Interactable**](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Interactable/Scripts) to make objects respond to various types of input interaction states.</span></span> <span data-ttu-id="c2a5d-234">Supporta vari tipi di temi che consentono di definire gli Stati di visualizzazione controllando le proprietà dell'oggetto, ad esempio colore, dimensioni, materiale e shader.</span><span class="sxs-lookup"><span data-stu-id="c2a5d-234">It supports various types of themes that allow you define visual states by controlling object properties such as color, size, material, and shader.</span></span>

* [<span data-ttu-id="c2a5d-235">Con cui</span><span class="sxs-lookup"><span data-stu-id="c2a5d-235">Interactable</span></span>](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/interactable)
* [<span data-ttu-id="c2a5d-236">Button</span><span class="sxs-lookup"><span data-stu-id="c2a5d-236">Button</span></span>](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/button)
* [<span data-ttu-id="c2a5d-237">Scena degli esempi di interazione della mano</span><span class="sxs-lookup"><span data-stu-id="c2a5d-237">Hand interaction examples scene</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_HandInteractionExamples.md)

<span data-ttu-id="c2a5d-238">Lo shader standard di MixedRealityToolkit offre diverse opzioni, ad esempio la **luce vicina** , che consente di creare suggerimenti visivi e audio.</span><span class="sxs-lookup"><span data-stu-id="c2a5d-238">MixedRealityToolkit's Standard shader provides various options such as **proximity light** that helps you create visual and audio cues.</span></span>

* [<span data-ttu-id="c2a5d-239">Shader standard MRTK</span><span class="sxs-lookup"><span data-stu-id="c2a5d-239">MRTK Standard Shader</span></span>](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/rendering/mrtk-standard-shader)

<br>

---

## <a name="see-also"></a><span data-ttu-id="c2a5d-240">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="c2a5d-240">See also</span></span>

* [<span data-ttu-id="c2a5d-241">Cursori</span><span class="sxs-lookup"><span data-stu-id="c2a5d-241">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="c2a5d-242">Raggio della mano</span><span class="sxs-lookup"><span data-stu-id="c2a5d-242">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="c2a5d-243">Button</span><span class="sxs-lookup"><span data-stu-id="c2a5d-243">Button</span></span>](button.md)
* [<span data-ttu-id="c2a5d-244">Oggetto che supporta interazioni</span><span class="sxs-lookup"><span data-stu-id="c2a5d-244">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="c2a5d-245">Rettangolo di selezione e barra dell'app</span><span class="sxs-lookup"><span data-stu-id="c2a5d-245">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="c2a5d-246">Manipolazione</span><span class="sxs-lookup"><span data-stu-id="c2a5d-246">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="c2a5d-247">Menu a mano</span><span class="sxs-lookup"><span data-stu-id="c2a5d-247">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="c2a5d-248">Menu adiacente</span><span class="sxs-lookup"><span data-stu-id="c2a5d-248">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="c2a5d-249">Raccolta di oggetti</span><span class="sxs-lookup"><span data-stu-id="c2a5d-249">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="c2a5d-250">Comando vocale</span><span class="sxs-lookup"><span data-stu-id="c2a5d-250">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="c2a5d-251">Tastiera</span><span class="sxs-lookup"><span data-stu-id="c2a5d-251">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="c2a5d-252">Descrizione comando</span><span class="sxs-lookup"><span data-stu-id="c2a5d-252">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="c2a5d-253">Slate</span><span class="sxs-lookup"><span data-stu-id="c2a5d-253">Slate</span></span>](slate.md)
* [<span data-ttu-id="c2a5d-254">Dispositivo di scorrimento</span><span class="sxs-lookup"><span data-stu-id="c2a5d-254">Slider</span></span>](slider.md)
* [<span data-ttu-id="c2a5d-255">Shader</span><span class="sxs-lookup"><span data-stu-id="c2a5d-255">Shader</span></span>](shader.md)
* [<span data-ttu-id="c2a5d-256">Billboarding e tag-along</span><span class="sxs-lookup"><span data-stu-id="c2a5d-256">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="c2a5d-257">Visualizzazione dello stato</span><span class="sxs-lookup"><span data-stu-id="c2a5d-257">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="c2a5d-258">Magnetismo di superficie</span><span class="sxs-lookup"><span data-stu-id="c2a5d-258">Surface magnetism</span></span>](surface-magnetism.md)

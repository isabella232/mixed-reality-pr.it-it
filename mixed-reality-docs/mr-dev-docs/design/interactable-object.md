---
title: Oggetto che supporta interazioni
description: Un pulsante è a lungo una metafora usata per attivare un evento nel mondo astratto 2D. Nel mondo della realtà mista tridimensionale, non dobbiamo più limitarci a questo mondo dell'astrazione.
author: cre8ivepark
ms.author: v-hferrone
ms.date: 06/06/2019
ms.topic: article
keywords: Realtà mista, controlli, interazione, interfaccia utente, UX
ms.openlocfilehash: 6458f4b1c80c8606d07d610f509ed610a0ca4268
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/03/2020
ms.locfileid: "91684220"
---
# <a name="interactable-object"></a><span data-ttu-id="92725-105">Oggetto che supporta interazioni</span><span class="sxs-lookup"><span data-stu-id="92725-105">Interactable object</span></span>

![Oggetti Interactible](images/UX_Hero_Interactable.jpg)

<span data-ttu-id="92725-107">Un pulsante è a lungo una metafora usata per attivare un evento nel mondo astratto 2D.</span><span class="sxs-lookup"><span data-stu-id="92725-107">A button has long been a metaphor used for triggering an event in the 2D abstract world.</span></span> <span data-ttu-id="92725-108">Nel mondo della realtà mista tridimensionale, non dobbiamo più limitarci a questo mondo dell'astrazione.</span><span class="sxs-lookup"><span data-stu-id="92725-108">In the three-dimensional mixed reality world, we don’t have to be confined to this world of abstraction anymore.</span></span> <span data-ttu-id="92725-109">Qualsiasi elemento può essere un **oggetto interagibile** che attiva un evento.</span><span class="sxs-lookup"><span data-stu-id="92725-109">Anything can be an **interactable object** that triggers an event.</span></span> <span data-ttu-id="92725-110">Un oggetto interactabile può essere rappresentato da qualsiasi elemento da un caffè della tabella a un pallone in aria.</span><span class="sxs-lookup"><span data-stu-id="92725-110">An interactable object can be represented as anything from a coffee cup on the table to a balloon floating in the air.</span></span> <span data-ttu-id="92725-111">Si usano ancora i pulsanti tradizionali in determinate situazioni, ad esempio nell'interfaccia utente della finestra di dialogo.</span><span class="sxs-lookup"><span data-stu-id="92725-111">We still do make use of traditional buttons in certain situation such as in dialog UI.</span></span> <span data-ttu-id="92725-112">La rappresentazione visiva del pulsante dipende dal contesto.</span><span class="sxs-lookup"><span data-stu-id="92725-112">The visual representation of the button depends on the context.</span></span>

<br>

---


## <a name="important-properties-of-the-interactable-object"></a><span data-ttu-id="92725-113">Proprietà importanti dell'oggetto interagibile</span><span class="sxs-lookup"><span data-stu-id="92725-113">Important properties of the interactable object</span></span>

### <a name="visual-cues"></a><span data-ttu-id="92725-114">Segnali visivi</span><span class="sxs-lookup"><span data-stu-id="92725-114">Visual cues</span></span>

<span data-ttu-id="92725-115">I segnali visivi sono segnali sensoriali ricevuti dall'occhio sotto forma di luce ed elaborati dal sistema visuale durante la percezione visiva.</span><span class="sxs-lookup"><span data-stu-id="92725-115">Visual cues are sensory cues received by the eye in the form of light and processed by the visual system during visual perception.</span></span> <span data-ttu-id="92725-116">Poiché il sistema visivo è dominante in molte specie, in particolare gli esseri umani, i segnali visivi rappresentano una grande fonte di informazioni in merito alla percezione del mondo.</span><span class="sxs-lookup"><span data-stu-id="92725-116">Since the visual system is dominant in many species, especially humans, visual cues are a large source of information in how the world is perceived.</span></span>

<span data-ttu-id="92725-117">Poiché gli oggetti olografici vengono combinati con l'ambiente reale in realtà mista, potrebbe essere difficile comprendere quali oggetti è possibile interagire.</span><span class="sxs-lookup"><span data-stu-id="92725-117">Since the holographic objects are blended with the real-world environment in mixed reality, it could be difficult to understand which objects you can interact with.</span></span> <span data-ttu-id="92725-118">Per tutti gli oggetti interagibili nell'esperienza, è importante fornire segnali visivi differenziati per ogni stato di input.</span><span class="sxs-lookup"><span data-stu-id="92725-118">For any interactable objects in your experience, it is important to provide differentiated visual cues for each input state.</span></span> <span data-ttu-id="92725-119">Ciò consente all'utente di comprendere quale parte dell'esperienza è interactabile e rende l'utente affidabile usando un metodo di interazione coerente.</span><span class="sxs-lookup"><span data-stu-id="92725-119">This helps the user understand which part of your experience is interactable and makes the user confident by using a consistent interaction method.</span></span>

<br>

---

### <a name="far-interactions"></a><span data-ttu-id="92725-120">Interazioni a distanza</span><span class="sxs-lookup"><span data-stu-id="92725-120">Far interactions</span></span>

<span data-ttu-id="92725-121">Per tutti gli oggetti che gli utenti possono interagire con lo sguardo, il raggio di mano e il raggio del controller di movimento, è consigliabile avere un segnale visivo diverso per questi tre stati di input:</span><span class="sxs-lookup"><span data-stu-id="92725-121">For any objects that user can interact with gaze, hand ray, and motion controller's ray, we recommend to have different visual cue for these three input states:</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="92725-122">![interactibleobject-stati-predefinito](images/interactibleobject-states-default.jpg)</span><span class="sxs-lookup"><span data-stu-id="92725-122">![interactibleobject-states-default](images/interactibleobject-states-default.jpg)</span></span><br>
       <span data-ttu-id="92725-123">**Stato predefinito (osservazione)**</span><span class="sxs-lookup"><span data-stu-id="92725-123">**Default (Observation) state**</span></span><br>
        <span data-ttu-id="92725-124">Stato inattivo predefinito dell'oggetto.</span><span class="sxs-lookup"><span data-stu-id="92725-124">Default idle state of the object.</span></span>
    <span data-ttu-id="92725-125">Il cursore non si trova nell'oggetto.</span><span class="sxs-lookup"><span data-stu-id="92725-125">The cursor is not on the object.</span></span> <span data-ttu-id="92725-126">La mano non è stata rilevata.</span><span class="sxs-lookup"><span data-stu-id="92725-126">Hand is not detected.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="92725-127">![interactibleobject-stati di destinazione](images/interactibleobject-states-targeted.jpg)</span><span class="sxs-lookup"><span data-stu-id="92725-127">![interactibleobject-states-targeted](images/interactibleobject-states-targeted.jpg)</span></span><br>
        <span data-ttu-id="92725-128">**Stato di destinazione (hover)**</span><span class="sxs-lookup"><span data-stu-id="92725-128">**Targeted (Hover) state**</span></span><br>
        <span data-ttu-id="92725-129">Quando l'oggetto è destinato a un cursore a sguardi, a una prossimità del dito o al puntatore del controller di movimento.</span><span class="sxs-lookup"><span data-stu-id="92725-129">When the object is targeted with gaze cursor, finger proximity or motion controller's pointer.</span></span>
    <span data-ttu-id="92725-130">Il cursore si trova sull'oggetto.</span><span class="sxs-lookup"><span data-stu-id="92725-130">The cursor is on the object.</span></span> <span data-ttu-id="92725-131">La mano è stata rilevata, pronta.</span><span class="sxs-lookup"><span data-stu-id="92725-131">Hand is detected, ready.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="92725-132">![interactibleobject-stati-premuto](images/interactibleobject-states-pressed.jpg)</span><span class="sxs-lookup"><span data-stu-id="92725-132">![interactibleobject-states-pressed](images/interactibleobject-states-pressed.jpg)</span></span><br>
       <span data-ttu-id="92725-133">**Stato premuto**</span><span class="sxs-lookup"><span data-stu-id="92725-133">**Pressed state**</span></span><br>
        <span data-ttu-id="92725-134">Quando l'oggetto viene premuto con un movimento di tocco aereo, premere il pulsante Seleziona del controller di movimento o del dito.</span><span class="sxs-lookup"><span data-stu-id="92725-134">When the object is pressed with an air tap gesture, finger press or motion controller's select button.</span></span>
    <span data-ttu-id="92725-135">Il cursore si trova sull'oggetto.</span><span class="sxs-lookup"><span data-stu-id="92725-135">The cursor is on the object.</span></span> <span data-ttu-id="92725-136">Viene rilevata una mano, aria toccata.</span><span class="sxs-lookup"><span data-stu-id="92725-136">Hand is detected, air tapped.</span></span>
    :::column-end:::
:::row-end:::

<br>

---

<span data-ttu-id="92725-137">È possibile usare tecniche come l'evidenziazione o il ridimensionamento per fornire segnali visivi per lo stato di input dell'utente.</span><span class="sxs-lookup"><span data-stu-id="92725-137">You can use techniques such as highlighting or scaling to provide visual cues for the user’s input state.</span></span> <span data-ttu-id="92725-138">In realtà mista, è possibile trovare gli esempi di visualizzazione di diversi Stati di input nel menu Start e con i pulsanti della barra delle applicazioni.</span><span class="sxs-lookup"><span data-stu-id="92725-138">In mixed reality, you can find the examples of visualizing different input states on the Start menu and with app bar buttons.</span></span> 

<span data-ttu-id="92725-139">Ecco come appaiono questi stati in un **pulsante olografico** :</span><span class="sxs-lookup"><span data-stu-id="92725-139">Here is what these states look like on a **holographic button** :</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="92725-140">![interactibleobject-stati-predefinito](images/MRTK_InteractableState-default.jpg)</span><span class="sxs-lookup"><span data-stu-id="92725-140">![interactibleobject-states-default](images/MRTK_InteractableState-default.jpg)</span></span><br>
       <span data-ttu-id="92725-141">**Stato predefinito (osservazione)**</span><span class="sxs-lookup"><span data-stu-id="92725-141">**Default (Observation) state**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="92725-142">![interactibleobject-stati di destinazione](images/MRTK_InteractableState-targeted.jpg)</span><span class="sxs-lookup"><span data-stu-id="92725-142">![interactibleobject-states-targeted](images/MRTK_InteractableState-targeted.jpg)</span></span><br>
        <span data-ttu-id="92725-143">**Stato di destinazione (hover)**</span><span class="sxs-lookup"><span data-stu-id="92725-143">**Targeted (Hover) state**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="92725-144">![interactibleobject-stati-premuto](images/MRTK_InteractableState-pressed.jpg)</span><span class="sxs-lookup"><span data-stu-id="92725-144">![interactibleobject-states-pressed](images/MRTK_InteractableState-pressed.jpg)</span></span><br>
       <span data-ttu-id="92725-145">**Stato premuto**</span><span class="sxs-lookup"><span data-stu-id="92725-145">**Pressed state**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

### <a name="near-interactions-direct"></a><span data-ttu-id="92725-146">Near Interactions (Direct)</span><span class="sxs-lookup"><span data-stu-id="92725-146">Near interactions (direct)</span></span> 

<span data-ttu-id="92725-147">HoloLens 2 supporta l'input di rilevamento a mano articolato che consente di interagire con gli oggetti.</span><span class="sxs-lookup"><span data-stu-id="92725-147">HoloLens 2 supports articulated hand tracking input which allows you to interact with objects.</span></span> <span data-ttu-id="92725-148">Senza commenti e suggerimenti tattili e una profonda percezione della profondità, a volte può essere difficile capire quanto è lontana la mano da un oggetto o se lo si sta toccando.</span><span class="sxs-lookup"><span data-stu-id="92725-148">Without haptic feedback and perfect depth perception, it can sometimes be hard to tell how far away your hand is from an object or whether you are touching it.</span></span> <span data-ttu-id="92725-149">È importante fornire segnali visivi sufficienti per comunicare lo stato dell'oggetto e in particolare lo stato delle mani in relazione a tale oggetto.</span><span class="sxs-lookup"><span data-stu-id="92725-149">It is important to provide enough visual cues to communicate the state of the object and in particular the state of your hands in relation to that object.</span></span>

<span data-ttu-id="92725-150">Usare il feedback visivo per comunicare quanto segue:</span><span class="sxs-lookup"><span data-stu-id="92725-150">Use visual feedback to communicate the following:</span></span>
* <span data-ttu-id="92725-151">**Impostazione predefinita (osservazione)** : stato inattivo predefinito dell'oggetto.</span><span class="sxs-lookup"><span data-stu-id="92725-151">**Default (Observation)** : Default idle state of the object.</span></span>
* <span data-ttu-id="92725-152">**Hover** : quando una mano si avvicina a un ologramma, modificare gli oggetti visivi per comunicare che la mano è destinata a ologrammi.</span><span class="sxs-lookup"><span data-stu-id="92725-152">**Hover** : When a hand is near a hologram, change visuals to communicate that hand is targeting hologram.</span></span> 
* <span data-ttu-id="92725-153">**Distanza e punto di interazione** : poiché la mano si avvicina a un ologramma, progettare il feedback per comunicare il punto di interazione proiettato, oltre a quanto lontano dall'oggetto il dito</span><span class="sxs-lookup"><span data-stu-id="92725-153">**Distance and point of interaction** : As the hand approaches a hologram, design feedback to communicate the projected point of interaction, as well as how far from the object the finger is</span></span>
* <span data-ttu-id="92725-154">**Inizio contatto** : modificare gli oggetti visivi (chiaro, colore) per comunicare che si è verificato un tocco</span><span class="sxs-lookup"><span data-stu-id="92725-154">**Contact begins** : Change visuals (light, color) to communicate that a touch has occurred</span></span>
* <span data-ttu-id="92725-155">**Colto** : modificare gli oggetti visivi (chiaro, colore) quando l'oggetto viene afferrato</span><span class="sxs-lookup"><span data-stu-id="92725-155">**Grasped** : Change visuals (light, color) when the object is grasped</span></span>
* <span data-ttu-id="92725-156">**Estremità del contatto** : modificare gli oggetti visivi (chiaro, colore) al termine del tocco</span><span class="sxs-lookup"><span data-stu-id="92725-156">**Contact ends** : Change visuals (light, color) when touch has ended</span></span>

<br>

---

:::row:::
    :::column:::
        <span data-ttu-id="92725-157">![Passaggio del mouse (lontano)](images/640px-interactibleobject-states-near-hover.jpg)</span><span class="sxs-lookup"><span data-stu-id="92725-157">![Hover (Far)](images/640px-interactibleobject-states-near-hover.jpg)</span></span><br>
        <span data-ttu-id="92725-158">**Passaggio del mouse (lontano)**</span><span class="sxs-lookup"><span data-stu-id="92725-158">**Hover (Far)**</span></span><br>
        <span data-ttu-id="92725-159">Evidenziazione basata sulla prossimità del manuale.</span><span class="sxs-lookup"><span data-stu-id="92725-159">Highlighting based on the proximity of the hand.</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="92725-160">![Passaggio del mouse (vicino)](images/640px-interactibleobject-states-near-hovernear.jpg)</span><span class="sxs-lookup"><span data-stu-id="92725-160">![Hover (Near)](images/640px-interactibleobject-states-near-hovernear.jpg)</span></span><br>
        <span data-ttu-id="92725-161">**Passaggio del mouse (vicino)**</span><span class="sxs-lookup"><span data-stu-id="92725-161">**Hover (Near)**</span></span><br>
        <span data-ttu-id="92725-162">Evidenziare le modifiche delle dimensioni in base alla distanza della mano.</span><span class="sxs-lookup"><span data-stu-id="92725-162">Highlight size changes based on the distance to the hand.</span></span>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        <span data-ttu-id="92725-163">![Tocco/pressione](images/640px-interactibleobject-states-near-press.jpg)</span><span class="sxs-lookup"><span data-stu-id="92725-163">![Touch / press](images/640px-interactibleobject-states-near-press.jpg)</span></span><br>
        <span data-ttu-id="92725-164">**Tocco/pressione**</span><span class="sxs-lookup"><span data-stu-id="92725-164">**Touch / press**</span></span><br>
        <span data-ttu-id="92725-165">Commenti visivi e audio.</span><span class="sxs-lookup"><span data-stu-id="92725-165">Visual plus audio feedback.</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="92725-166">![Comprendere](images/640px-interactibleobject-states-near-grasp.jpg)</span><span class="sxs-lookup"><span data-stu-id="92725-166">![Grasp](images/640px-interactibleobject-states-near-grasp.jpg)</span></span><br>
        <span data-ttu-id="92725-167">**Comprendere**</span><span class="sxs-lookup"><span data-stu-id="92725-167">**Grasp**</span></span><br>
        <span data-ttu-id="92725-168">Commenti visivi e audio.</span><span class="sxs-lookup"><span data-stu-id="92725-168">Visual plus audio feedback.</span></span>
    :::column-end:::
:::row-end:::

<br>

<br>

---

<span data-ttu-id="92725-169">Un [pulsante in HoloLens 2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html) è un esempio di visualizzazione dei diversi Stati di interazione di input:</span><span class="sxs-lookup"><span data-stu-id="92725-169">A [button on HoloLens 2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html) is an example of how the different input interaction states are visualized:</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="92725-170">![Valore predefinito](images/640px-interactibleobject-pressablebutton-default.jpg)</span><span class="sxs-lookup"><span data-stu-id="92725-170">![Default](images/640px-interactibleobject-pressablebutton-default.jpg)</span></span><br>
        <span data-ttu-id="92725-171">**Default**</span><span class="sxs-lookup"><span data-stu-id="92725-171">**Default**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="92725-172">![Passaggio del mouse](images/640px-interactibleobject-pressablebutton-hover.jpg)</span><span class="sxs-lookup"><span data-stu-id="92725-172">![Hover](images/640px-interactibleobject-pressablebutton-hover.jpg)</span></span><br>
        <span data-ttu-id="92725-173">**Passaggio del mouse**</span><span class="sxs-lookup"><span data-stu-id="92725-173">**Hover**</span></span><br>
        <span data-ttu-id="92725-174">Rivelare un effetto di illuminazione basato su prossimità.</span><span class="sxs-lookup"><span data-stu-id="92725-174">Reveal a proximity-based lighting effect.</span></span>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        <span data-ttu-id="92725-175">![Tocco](images/640px-interactibleobject-pressablebutton-touch.jpg)</span><span class="sxs-lookup"><span data-stu-id="92725-175">![Touch](images/640px-interactibleobject-pressablebutton-touch.jpg)</span></span><br>
        <span data-ttu-id="92725-176">**Tocco**</span><span class="sxs-lookup"><span data-stu-id="92725-176">**Touch**</span></span><br>
        <span data-ttu-id="92725-177">Mostra effetto Ripple.</span><span class="sxs-lookup"><span data-stu-id="92725-177">Show ripple effect.</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="92725-178">![Premere](images/640px-interactibleobject-pressablebutton-press.jpg)</span><span class="sxs-lookup"><span data-stu-id="92725-178">![Press](images/640px-interactibleobject-pressablebutton-press.jpg)</span></span><br>
        <span data-ttu-id="92725-179">**Premere**</span><span class="sxs-lookup"><span data-stu-id="92725-179">**Press**</span></span><br>
        <span data-ttu-id="92725-180">Spostare il pannello anteriore.</span><span class="sxs-lookup"><span data-stu-id="92725-180">Move the front plate.</span></span>
    :::column-end:::
:::row-end:::

<br>

---

:::row:::
    :::column:::
        ### <a name="the-ring-visual-cue-on-hololens-2br"></a><span data-ttu-id="92725-181">Il segnale visivo "Ring" su HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="92725-181">The "ring" visual cue on HoloLens 2</span></span><br>
        <span data-ttu-id="92725-182">In HoloLens 2 è presente un segnale visivo aggiuntivo che può aiutare la percezione dell'utente della profondità.</span><span class="sxs-lookup"><span data-stu-id="92725-182">On HoloLens 2, there is an additional visual cue which can help the user's perception of depth.</span></span> <span data-ttu-id="92725-183">Un anello vicino alla loro parte viene visualizzato e ridimensionato quando il dito si avvicina all'oggetto.</span><span class="sxs-lookup"><span data-stu-id="92725-183">A ring near their fingertip shows up and scales down as the fingertip gets closer to the object.</span></span> <span data-ttu-id="92725-184">L'anello alla fine converge in un punto quando viene raggiunto lo stato premuto.</span><span class="sxs-lookup"><span data-stu-id="92725-184">The ring eventually converges into a dot when the pressed state is reached.</span></span> <span data-ttu-id="92725-185">Questa convenienza visiva consente all'utente di comprendere la distanza dall'oggetto.</span><span class="sxs-lookup"><span data-stu-id="92725-185">This visual affordance helps the user understand how far they are from the object.</span></span><br>
        <br>
        <span data-ttu-id="92725-186">*Ciclo video: esempio di feedback visivo basato sulla prossimità a un rettangolo di delimitazione*</span><span class="sxs-lookup"><span data-stu-id="92725-186">*Video loop: Example of visual feedback based on proximity to a bounding box*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="92725-187">![space](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="92725-187">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="92725-188">![Feedback visivo sulla prossimità della mano](images/HoloLens2_Proximity.gif)</span><span class="sxs-lookup"><span data-stu-id="92725-188">![Visual feedback on hand proximity](images/HoloLens2_Proximity.gif)</span></span><br>
    :::column-end:::
:::row-end:::


<br>

---


### <a name="audio-cues"></a><span data-ttu-id="92725-189">Segnali audio</span><span class="sxs-lookup"><span data-stu-id="92725-189">Audio cues</span></span>

<span data-ttu-id="92725-190">Per le interazioni dirette, il feedback audio appropriato può migliorare notevolmente l'esperienza utente.</span><span class="sxs-lookup"><span data-stu-id="92725-190">For direct hand interactions, proper audio feedback can dramatically improve the user experience.</span></span> <span data-ttu-id="92725-191">Usare il feedback audio per comunicare quanto segue:</span><span class="sxs-lookup"><span data-stu-id="92725-191">Use audio feedback to communicate the following:</span></span>
* <span data-ttu-id="92725-192">**Inizio contatto** : riprodurre un suono quando inizia il tocco</span><span class="sxs-lookup"><span data-stu-id="92725-192">**Contact begins** : Play sound when touch begins</span></span>
* <span data-ttu-id="92725-193">**Terminazione contatto** : riprodurre un suono al termine del tocco</span><span class="sxs-lookup"><span data-stu-id="92725-193">**Contact ends** : Play sound on touch end</span></span>
* <span data-ttu-id="92725-194">**Inizio** avvio: riprodurre un suono quando viene avviata la cattura</span><span class="sxs-lookup"><span data-stu-id="92725-194">**Grab begins** : Play sound when grab starts</span></span>
* <span data-ttu-id="92725-195">**Estremità** di chiusura: riprodurre un suono quando termina la cattura</span><span class="sxs-lookup"><span data-stu-id="92725-195">**Grab ends** : Play sound when grab ends</span></span>

<br>

---

:::row:::
    :::column:::
        ### <a name="voice-commandingbr"></a><span data-ttu-id="92725-196">Esecuzione di comandi vocali</span><span class="sxs-lookup"><span data-stu-id="92725-196">Voice commanding</span></span><br>
        <span data-ttu-id="92725-197">Per tutti gli oggetti interagibili, è importante supportare opzioni di interazione alternative.</span><span class="sxs-lookup"><span data-stu-id="92725-197">For any interactable objects, it is important to support alternative interaction options.</span></span> <span data-ttu-id="92725-198">Per impostazione predefinita, è consigliabile che i [comandi vocali](../out-of-scope/voice-design.md) siano supportati per gli oggetti che possono interagire.</span><span class="sxs-lookup"><span data-stu-id="92725-198">By default, we recommend that [voice commanding](../out-of-scope/voice-design.md) be supported for any objects that are interactable.</span></span> <span data-ttu-id="92725-199">Per migliorare l'individuabilità, è anche possibile fornire una descrizione comando durante lo stato del passaggio del mouse.</span><span class="sxs-lookup"><span data-stu-id="92725-199">To improve discoverability, you can also provide a tooltip during the hover state.</span></span><br>
        <br>
        <span data-ttu-id="92725-200">*Image: descrizione comando per il comando Voice*</span><span class="sxs-lookup"><span data-stu-id="92725-200">*Image: Tooltip for the voice command*</span></span>
    :::column-end:::
        :::column:::
       ![comando vocale](images/640px-interactibleobject-voicecommand.png)<br>
    :::column-end:::
:::row-end:::


<br>

---


## <a name="sizing-recommendations"></a><span data-ttu-id="92725-202">Consigli sul ridimensionamento</span><span class="sxs-lookup"><span data-stu-id="92725-202">Sizing recommendations</span></span> 

<span data-ttu-id="92725-203">Per garantire che tutti gli oggetti interagibili possano essere facilmente modificati dagli utenti, si consiglia di assicurarsi che l'interoperabilità soddisfi le dimensioni minime (l'angolo visivo spesso misurato in gradi di arco visivo) in base alla distanza in base alla quale viene posizionata dall'utente.</span><span class="sxs-lookup"><span data-stu-id="92725-203">To ensure that all interactable objects can easily be touched by users, we recommend that you make sure the interactable meets a minimum size (the visual angle often measured in degrees of visual arc) based on the distance it is placed from the user.</span></span> <span data-ttu-id="92725-204">L'angolo visivo è basato sulla distanza tra gli occhi dell'utente e l'oggetto e rimane costante, mentre la dimensione fisica della destinazione può variare a seconda della distanza tra le modifiche apportate dall'utente.</span><span class="sxs-lookup"><span data-stu-id="92725-204">Visual angle is based on the distance between the user's eyes and the object and stays constant, while the physical size of the target may change as the distance from the user changes.</span></span> <span data-ttu-id="92725-205">Per determinare le dimensioni fisiche necessarie di un oggetto in base alla distanza dall'utente, provare a usare un calcolo dell'angolo visivo come [questo](https://elvers.us/perception/visualAngle/).</span><span class="sxs-lookup"><span data-stu-id="92725-205">To determine the necessary physical size of an object based on the distance from the user, try using a visual angle calculator such as [this one](https://elvers.us/perception/visualAngle/).</span></span>

<span data-ttu-id="92725-206">Di seguito sono riportati i consigli per le dimensioni minime del contenuto interactabile.</span><span class="sxs-lookup"><span data-stu-id="92725-206">Below are the recommendations for minimum sizes of interactable content.</span></span>


### <a name="target-size-for-direct-hand-interaction"></a><span data-ttu-id="92725-207">Dimensioni di destinazione per l'interazione diretta con la mano</span><span class="sxs-lookup"><span data-stu-id="92725-207">Target size for direct hand interaction</span></span>

| <span data-ttu-id="92725-208">Distanza</span><span class="sxs-lookup"><span data-stu-id="92725-208">Distance</span></span> | <span data-ttu-id="92725-209">Angolo di visualizzazione</span><span class="sxs-lookup"><span data-stu-id="92725-209">Viewing angle</span></span> | <span data-ttu-id="92725-210">Dimensione</span><span class="sxs-lookup"><span data-stu-id="92725-210">Size</span></span> |
|---------|---------|---------|
| <span data-ttu-id="92725-211">45cm</span><span class="sxs-lookup"><span data-stu-id="92725-211">45cm</span></span>  | <span data-ttu-id="92725-212">non inferiore a 2 °</span><span class="sxs-lookup"><span data-stu-id="92725-212">no smaller than 2°</span></span> | <span data-ttu-id="92725-213">1,6 x 1,6 cm</span><span class="sxs-lookup"><span data-stu-id="92725-213">1.6 x 1.6 cm</span></span> |

<span data-ttu-id="92725-214">![Dimensioni di destinazione per l'interazione diretta con la mano](images/TargetSizingNear.jpg)</span><span class="sxs-lookup"><span data-stu-id="92725-214">![Target size for direct hand interaction](images/TargetSizingNear.jpg)</span></span><br>
<span data-ttu-id="92725-215">*Dimensioni di destinazione per l'interazione diretta con la mano*</span><span class="sxs-lookup"><span data-stu-id="92725-215">*Target size for direct hand interaction*</span></span>

<br>

### <a name="target-size-for-buttons"></a><span data-ttu-id="92725-216">Dimensioni di destinazione per i pulsanti</span><span class="sxs-lookup"><span data-stu-id="92725-216">Target size for buttons</span></span>

<span data-ttu-id="92725-217">Quando si creano i pulsanti per l'interazione diretta, si consiglia una dimensione minima maggiore di 3,2 x 3,2 cm per assicurarsi che lo spazio disponibile sia sufficiente per contenere un'icona e potenzialmente un testo.</span><span class="sxs-lookup"><span data-stu-id="92725-217">When creating buttons for direct interaction, we recommend a larger minimum size of 3.2 x 3.2 cm to ensure that there is enough space to contain an icon and potentially some text.</span></span>

| <span data-ttu-id="92725-218">Distanza</span><span class="sxs-lookup"><span data-stu-id="92725-218">Distance</span></span> | <span data-ttu-id="92725-219">Dimensione minima</span><span class="sxs-lookup"><span data-stu-id="92725-219">Minimum size</span></span> |
|---------|---------|
| <span data-ttu-id="92725-220">45cm</span><span class="sxs-lookup"><span data-stu-id="92725-220">45cm</span></span>  | <span data-ttu-id="92725-221">3,2 x 3,2 cm</span><span class="sxs-lookup"><span data-stu-id="92725-221">3.2 x 3.2 cm</span></span> |

<span data-ttu-id="92725-222">![Dimensioni di destinazione per i pulsanti](images/TargetSizingButtons.png)</span><span class="sxs-lookup"><span data-stu-id="92725-222">![Target size for the buttons](images/TargetSizingButtons.png)</span></span><br>
<span data-ttu-id="92725-223">*Dimensioni di destinazione per i pulsanti*</span><span class="sxs-lookup"><span data-stu-id="92725-223">*Target size for the buttons*</span></span>

<br>

### <a name="target-size-for-hand-ray-or-gaze-interaction"></a><span data-ttu-id="92725-224">Dimensioni di destinazione per l'interazione con raggio o sguardo</span><span class="sxs-lookup"><span data-stu-id="92725-224">Target size for hand ray or gaze interaction</span></span>
| <span data-ttu-id="92725-225">Distanza</span><span class="sxs-lookup"><span data-stu-id="92725-225">Distance</span></span> | <span data-ttu-id="92725-226">Angolo di visualizzazione</span><span class="sxs-lookup"><span data-stu-id="92725-226">Viewing angle</span></span> | <span data-ttu-id="92725-227">Dimensione</span><span class="sxs-lookup"><span data-stu-id="92725-227">Size</span></span> |
|---------|---------|---------|
| <span data-ttu-id="92725-228">2m</span><span class="sxs-lookup"><span data-stu-id="92725-228">2m</span></span>  | <span data-ttu-id="92725-229">non minore di 1 °</span><span class="sxs-lookup"><span data-stu-id="92725-229">no smaller than 1°</span></span> | <span data-ttu-id="92725-230">3,5 x 3,5 cm</span><span class="sxs-lookup"><span data-stu-id="92725-230">3.5 x 3.5 cm</span></span> |

<span data-ttu-id="92725-231">![Dimensioni di destinazione per l'interazione con raggio o sguardo](images/TargetSizingFar.jpg)</span><span class="sxs-lookup"><span data-stu-id="92725-231">![Target size for hand ray or gaze interaction](images/TargetSizingFar.jpg)</span></span><br>
<span data-ttu-id="92725-232">*Dimensioni di destinazione per l'interazione con raggio o sguardo*</span><span class="sxs-lookup"><span data-stu-id="92725-232">*Target size for hand ray or gaze interaction*</span></span>


<br>

---


## <a name="interactable-object-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="92725-233">Oggetto interactabile in MRTK (Mixed Reality Toolkit) per Unity</span><span class="sxs-lookup"><span data-stu-id="92725-233">Interactable object in MRTK (Mixed Reality Toolkit) for Unity</span></span>

<span data-ttu-id="92725-234">In **[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** è possibile usare lo script [**interactable**](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Interactable/Scripts) per fare in modo che gli oggetti rispondano a diversi tipi di Stati di interazione di input.</span><span class="sxs-lookup"><span data-stu-id="92725-234">In **[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** , you can use the script [**Interactable**](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Interactable/Scripts) to make objects respond to various types of input interaction states.</span></span> <span data-ttu-id="92725-235">Supporta vari tipi di temi che consentono di definire gli Stati di visualizzazione controllando le proprietà dell'oggetto, ad esempio colore, dimensioni, materiale e shader.</span><span class="sxs-lookup"><span data-stu-id="92725-235">It supports various types of themes that allows you define visual states by controlling object properties such as color, size, material, and shader.</span></span>

* [<span data-ttu-id="92725-236">Con cui</span><span class="sxs-lookup"><span data-stu-id="92725-236">Interactable</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html)
* [<span data-ttu-id="92725-237">Button</span><span class="sxs-lookup"><span data-stu-id="92725-237">Button</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html)
* [<span data-ttu-id="92725-238">Scena degli esempi di interazione della mano</span><span class="sxs-lookup"><span data-stu-id="92725-238">Hand interaction examples scene</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_HandInteractionExamples.md)

<span data-ttu-id="92725-239">Lo shader standard di MixedRealityToolkit offre diverse opzioni, ad esempio la **luce vicina** , che consente di creare suggerimenti visivi e audio.</span><span class="sxs-lookup"><span data-stu-id="92725-239">MixedRealityToolkit's Standard shader provides various options such as **proximity light** that helps you create visual and audio cues.</span></span>
* [<span data-ttu-id="92725-240">Shader standard MRTK</span><span class="sxs-lookup"><span data-stu-id="92725-240">MRTK Standard Shader</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Documentation/README_MRTKStandardShader.md)


<br>

---


## <a name="see-also"></a><span data-ttu-id="92725-241">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="92725-241">See also</span></span>

* [<span data-ttu-id="92725-242">Cursori</span><span class="sxs-lookup"><span data-stu-id="92725-242">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="92725-243">Raggio della mano</span><span class="sxs-lookup"><span data-stu-id="92725-243">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="92725-244">Button</span><span class="sxs-lookup"><span data-stu-id="92725-244">Button</span></span>](button.md)
* [<span data-ttu-id="92725-245">Oggetto che supporta interazioni</span><span class="sxs-lookup"><span data-stu-id="92725-245">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="92725-246">Rettangolo di selezione e barra dell'app</span><span class="sxs-lookup"><span data-stu-id="92725-246">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="92725-247">Manipolazione</span><span class="sxs-lookup"><span data-stu-id="92725-247">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="92725-248">Menu a mano</span><span class="sxs-lookup"><span data-stu-id="92725-248">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="92725-249">Menu adiacente</span><span class="sxs-lookup"><span data-stu-id="92725-249">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="92725-250">Raccolta di oggetti</span><span class="sxs-lookup"><span data-stu-id="92725-250">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="92725-251">Comando vocale</span><span class="sxs-lookup"><span data-stu-id="92725-251">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="92725-252">Tastiera</span><span class="sxs-lookup"><span data-stu-id="92725-252">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="92725-253">Descrizione comando</span><span class="sxs-lookup"><span data-stu-id="92725-253">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="92725-254">Slate</span><span class="sxs-lookup"><span data-stu-id="92725-254">Slate</span></span>](slate.md)
* [<span data-ttu-id="92725-255">Dispositivo di scorrimento</span><span class="sxs-lookup"><span data-stu-id="92725-255">Slider</span></span>](slider.md)
* [<span data-ttu-id="92725-256">Shader</span><span class="sxs-lookup"><span data-stu-id="92725-256">Shader</span></span>](shader.md)
* [<span data-ttu-id="92725-257">Billboarding e tag-along</span><span class="sxs-lookup"><span data-stu-id="92725-257">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="92725-258">Visualizzazione dello stato</span><span class="sxs-lookup"><span data-stu-id="92725-258">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="92725-259">Magnetismo di superficie</span><span class="sxs-lookup"><span data-stu-id="92725-259">Surface magnetism</span></span>](surface-magnetism.md)

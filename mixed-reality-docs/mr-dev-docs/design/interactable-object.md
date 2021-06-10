---
title: Oggetto che supporta interazioni
description: Informazioni su come attivare eventi, fornire segnali visivi e interagire con gli oggetti nelle applicazioni di realtà mista.
author: cre8ivepark
ms.author: v-hferrone
ms.date: 06/06/2019
ms.topic: article
keywords: Realtà mista, controlli, interazione, segnali, interfaccia utente, esperienza utente, visore VR di realtà mista, visore VR di realtà mista windows, visore VR di realtà virtuale, HoloLens, MRTK, Mixed Reality Toolkit, audio
ms.openlocfilehash: 8a68006d68b985f8d26a3d1a11e4d52fcfb5acb5
ms.sourcegitcommit: 9ae76b339968f035c703d9c1fe57ddecb33198e3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/27/2021
ms.locfileid: "110600440"
---
# <a name="interactable-object"></a><span data-ttu-id="15edf-104">Oggetto che supporta interazioni</span><span class="sxs-lookup"><span data-stu-id="15edf-104">Interactable object</span></span>

![Oggetti interactible](images/UX_Hero_Interactable.jpg)

<span data-ttu-id="15edf-106">Un pulsante è da tempo una metafora usata per attivare un evento nel mondo astratto 2D.</span><span class="sxs-lookup"><span data-stu-id="15edf-106">A button has long been a metaphor used for triggering an event in the 2D abstract world.</span></span> <span data-ttu-id="15edf-107">Nel mondo della realtà mista tridimensionale non è più necessario limitarsi a questo mondo di astrazione.</span><span class="sxs-lookup"><span data-stu-id="15edf-107">In the three-dimensional mixed reality world, we don’t have to be confined to this world of abstraction anymore.</span></span> <span data-ttu-id="15edf-108">Qualsiasi elemento può essere **un oggetto che può** interagire che attiva un evento.</span><span class="sxs-lookup"><span data-stu-id="15edf-108">Anything can be an **interactable object** that triggers an event.</span></span> <span data-ttu-id="15edf-109">Un oggetto che può interagire può essere qualsiasi cosa, da una tazzina da caffè su un tavolo a un balloon in midair.</span><span class="sxs-lookup"><span data-stu-id="15edf-109">An interactable object can be anything from a coffee cup on a table to a balloon in midair.</span></span> <span data-ttu-id="15edf-110">I pulsanti tradizionali vengono comunque utilizzati in determinate situazioni, ad esempio nell'interfaccia utente della finestra di dialogo.</span><span class="sxs-lookup"><span data-stu-id="15edf-110">We still do make use of traditional buttons in certain situation such as in dialog UI.</span></span> <span data-ttu-id="15edf-111">La rappresentazione visiva del pulsante dipende dal contesto.</span><span class="sxs-lookup"><span data-stu-id="15edf-111">The visual representation of the button depends on the context.</span></span>

<br>

---

## <a name="important-properties-of-the-interactable-object"></a><span data-ttu-id="15edf-112">Proprietà importanti dell'oggetto con interazione</span><span class="sxs-lookup"><span data-stu-id="15edf-112">Important properties of the interactable object</span></span>

### <a name="visual-cues"></a><span data-ttu-id="15edf-113">Visivi</span><span class="sxs-lookup"><span data-stu-id="15edf-113">Visual cues</span></span>

<span data-ttu-id="15edf-114">I segnali visivi sono segnali sensoriali provenienti dalla luce, ricevuti dall'occhio ed elaborati dal sistema visivo durante la percezione visiva.</span><span class="sxs-lookup"><span data-stu-id="15edf-114">Visual cues are sensory cues from light, received by the eye, and processed by the visual system during visual perception.</span></span> <span data-ttu-id="15edf-115">Poiché il sistema visivo è dominante in molte specie, in particolare gli esseri umani, i segnali visivi sono una grande fonte di informazioni sul modo in cui viene percepito il mondo.</span><span class="sxs-lookup"><span data-stu-id="15edf-115">Since the visual system is dominant in many species, especially humans, visual cues are a large source of information in how the world is perceived.</span></span>

<span data-ttu-id="15edf-116">Poiché gli oggetti olografici vengono misti con l'ambiente reale nella realtà mista, potrebbe essere difficile comprendere con quali oggetti è possibile interagire.</span><span class="sxs-lookup"><span data-stu-id="15edf-116">Since the holographic objects are blended with the real-world environment in mixed reality, it could be difficult to understand which objects you can interact with.</span></span> <span data-ttu-id="15edf-117">Per tutti gli oggetti che possono interagire nell'esperienza, è importante fornire segnali visivi differenziati per ogni stato di input.</span><span class="sxs-lookup"><span data-stu-id="15edf-117">For any interactable objects in your experience, it's important to provide differentiated visual cues for each input state.</span></span> <span data-ttu-id="15edf-118">Ciò consente all'utente di comprendere quale parte dell'esperienza può interagire e rende l'utente sicuro usando un metodo di interazione coerente.</span><span class="sxs-lookup"><span data-stu-id="15edf-118">This helps the user understand which part of your experience is interactable and makes the user confident by using a consistent interaction method.</span></span>

<br>

---

### <a name="far-interactions"></a><span data-ttu-id="15edf-119">Interazioni da lontano</span><span class="sxs-lookup"><span data-stu-id="15edf-119">Far interactions</span></span>

<span data-ttu-id="15edf-120">Per tutti gli oggetti che l'utente può interagire con lo sguardo fisso, il raggio della mano e il raggio del controller del movimento, è consigliabile avere un segnale visivo diverso per questi tre stati di input:</span><span class="sxs-lookup"><span data-stu-id="15edf-120">For any objects that user can interact with gaze, hand ray, and motion controller's ray, we recommend having different visual cue for these three input states:</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="15edf-121">![Oggetto con interazione con stato predefinito](images/interactibleobject-states-default.jpg)</span><span class="sxs-lookup"><span data-stu-id="15edf-121">![Interactable object with default state](images/interactibleobject-states-default.jpg)</span></span><br>
       <span data-ttu-id="15edf-122">**Stato predefinito (osservazione)**</span><span class="sxs-lookup"><span data-stu-id="15edf-122">**Default (Observation) state**</span></span><br>
        <span data-ttu-id="15edf-123">Stato di inattività predefinito dell'oggetto.</span><span class="sxs-lookup"><span data-stu-id="15edf-123">Default idle state of the object.</span></span>
    <span data-ttu-id="15edf-124">Il cursore non si trova sull'oggetto.</span><span class="sxs-lookup"><span data-stu-id="15edf-124">The cursor isn't on the object.</span></span> <span data-ttu-id="15edf-125">La mano non viene rilevata.</span><span class="sxs-lookup"><span data-stu-id="15edf-125">Hand isn't detected.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="15edf-126">![Oggetto con interazione con stato di destinazione e passaggio del mouse](images/interactibleobject-states-targeted.jpg)</span><span class="sxs-lookup"><span data-stu-id="15edf-126">![Interactable object with target and hover state](images/interactibleobject-states-targeted.jpg)</span></span><br>
        <span data-ttu-id="15edf-127">**Stato di destinazione (passaggio del mouse)**</span><span class="sxs-lookup"><span data-stu-id="15edf-127">**Targeted (Hover) state**</span></span><br>
        <span data-ttu-id="15edf-128">Quando l'oggetto è indirizzato con il cursore sguardo fisso, la prossimità del dito o il puntatore del controller del movimento.</span><span class="sxs-lookup"><span data-stu-id="15edf-128">When the object is targeted with gaze cursor, finger proximity or motion controller's pointer.</span></span>
    <span data-ttu-id="15edf-129">Il cursore si trova sull'oggetto .</span><span class="sxs-lookup"><span data-stu-id="15edf-129">The cursor is on the object.</span></span> <span data-ttu-id="15edf-130">La mano viene rilevata, pronta.</span><span class="sxs-lookup"><span data-stu-id="15edf-130">Hand is detected, ready.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="15edf-131">![Oggetto con interazione con stato premuto](images/interactibleobject-states-pressed.jpg)</span><span class="sxs-lookup"><span data-stu-id="15edf-131">![Interactable object with pressed state](images/interactibleobject-states-pressed.jpg)</span></span><br>
       <span data-ttu-id="15edf-132">**Stato premuto**</span><span class="sxs-lookup"><span data-stu-id="15edf-132">**Pressed state**</span></span><br>
        <span data-ttu-id="15edf-133">Quando l'oggetto viene premuto con un movimento di tocco, la pressione del dito o il pulsante di selezione del controller del movimento.</span><span class="sxs-lookup"><span data-stu-id="15edf-133">When the object is pressed with an air tap gesture, finger press or motion controller's select button.</span></span>
    <span data-ttu-id="15edf-134">Il cursore si trova sull'oggetto .</span><span class="sxs-lookup"><span data-stu-id="15edf-134">The cursor is on the object.</span></span> <span data-ttu-id="15edf-135">Viene rilevata la mano, viene toccata l'aria.</span><span class="sxs-lookup"><span data-stu-id="15edf-135">Hand is detected, air tapped.</span></span>
    :::column-end:::
:::row-end:::

<br>

---

<span data-ttu-id="15edf-136">È possibile usare tecniche come l'evidenziazione o il ridimensionamento per fornire segnali visivi per lo stato di input dell'utente.</span><span class="sxs-lookup"><span data-stu-id="15edf-136">You can use techniques such as highlighting or scaling to provide visual cues for the user’s input state.</span></span> <span data-ttu-id="15edf-137">Nella realtà mista è possibile trovare esempi di visualizzazione di stati di input diversi nel menu Start e con i pulsanti della barra dell'app.</span><span class="sxs-lookup"><span data-stu-id="15edf-137">In mixed reality, you can find examples of visualizing different input states on the Start menu and with app bar buttons.</span></span> 

<span data-ttu-id="15edf-138">Ecco l'aspetto di questi stati su un **pulsante olografico:**</span><span class="sxs-lookup"><span data-stu-id="15edf-138">Here's what these states look like on a **holographic button**:</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="15edf-139">![Pulsante olografico nello stato predefinito](images/MRTK_InteractableState-default.jpg)</span><span class="sxs-lookup"><span data-stu-id="15edf-139">![Holographic button in default state](images/MRTK_InteractableState-default.jpg)</span></span><br>
       <span data-ttu-id="15edf-140">**Stato predefinito (osservazione)**</span><span class="sxs-lookup"><span data-stu-id="15edf-140">**Default (Observation) state**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="15edf-141">![Pulsante olografico nello stato di destinazione e passaggio del mouse](images/MRTK_InteractableState-targeted.jpg)</span><span class="sxs-lookup"><span data-stu-id="15edf-141">![Holographic button in target and hover state](images/MRTK_InteractableState-targeted.jpg)</span></span><br>
        <span data-ttu-id="15edf-142">**Stato di destinazione (passaggio del mouse)**</span><span class="sxs-lookup"><span data-stu-id="15edf-142">**Targeted (Hover) state**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="15edf-143">![Pulsante olografico nello stato premuto](images/MRTK_InteractableState-pressed.jpg)</span><span class="sxs-lookup"><span data-stu-id="15edf-143">![Holographic button in pressed state](images/MRTK_InteractableState-pressed.jpg)</span></span><br>
       <span data-ttu-id="15edf-144">**Stato premuto**</span><span class="sxs-lookup"><span data-stu-id="15edf-144">**Pressed state**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

### <a name="near-interactions-direct"></a><span data-ttu-id="15edf-145">Interazioni near (diretta)</span><span class="sxs-lookup"><span data-stu-id="15edf-145">Near interactions (direct)</span></span> 

<span data-ttu-id="15edf-146">HoloLens 2 supporta l'input di tracciamento delle mani articolato, che consente di interagire con gli oggetti.</span><span class="sxs-lookup"><span data-stu-id="15edf-146">HoloLens 2 supports articulated hand tracking input, which allows you to interact with objects.</span></span> <span data-ttu-id="15edf-147">Senza feedback attico e percezione della profondità perfetta, può essere difficile stabilire quanto la mano è distante da un oggetto o se lo si sta toccando.</span><span class="sxs-lookup"><span data-stu-id="15edf-147">Without haptic feedback and perfect depth perception, it can be hard to tell how far away your hand is from an object or whether you're touching it.</span></span> <span data-ttu-id="15edf-148">È importante fornire segnali visivi sufficienti per comunicare lo stato dell'oggetto, in particolare lo stato delle mani in base a tale oggetto.</span><span class="sxs-lookup"><span data-stu-id="15edf-148">It's important to provide enough visual cues to communicate the state of the object, in particular the state of your hands based on that object.</span></span>

<span data-ttu-id="15edf-149">Usare il feedback visivo per comunicare gli stati seguenti:</span><span class="sxs-lookup"><span data-stu-id="15edf-149">Use visual feedback to communicate the following states:</span></span>
* <span data-ttu-id="15edf-150">**Predefinito (osservazione):** stato di inattività predefinito dell'oggetto.</span><span class="sxs-lookup"><span data-stu-id="15edf-150">**Default (Observation)**: Default idle state of the object.</span></span>
* <span data-ttu-id="15edf-151">**Passaggio** del mouse: quando una mano si trova vicino a un ologramma, modificare gli oggetti visivi per comunicare che la mano è la destinazione dell'ologramma.</span><span class="sxs-lookup"><span data-stu-id="15edf-151">**Hover**: When a hand is near a hologram, change visuals to communicate that hand is targeting hologram.</span></span> 
* <span data-ttu-id="15edf-152">**Distanza e punto di interazione:** quando la mano si avvicina a un ologramma, progettare il feedback per comunicare il punto di interazione proiettato e la distanza dall'oggetto del dito</span><span class="sxs-lookup"><span data-stu-id="15edf-152">**Distance and point of interaction**: As the hand approaches a hologram, design feedback to communicate the projected point of interaction, and how far from the object the finger is</span></span>
* <span data-ttu-id="15edf-153">**Inizio contatto:** modifica gli oggetti visivi (luce, colore) per comunicare che si è verificato un tocco</span><span class="sxs-lookup"><span data-stu-id="15edf-153">**Contact begins**: Change visuals (light, color) to communicate that a touch has occurred</span></span>
* <span data-ttu-id="15edf-154">**Afferrato:** modifica gli oggetti visivi (luce, colore) quando l'oggetto viene afferrato</span><span class="sxs-lookup"><span data-stu-id="15edf-154">**Grasped**: Change visuals (light, color) when the object is grasped</span></span>
* <span data-ttu-id="15edf-155">**Fine contatto:** modifica gli oggetti visivi (chiaro, colore) al termine del tocco</span><span class="sxs-lookup"><span data-stu-id="15edf-155">**Contact ends**: Change visuals (light, color) when touch has ended</span></span>

<br>

---

:::row:::
    :::column:::
        <span data-ttu-id="15edf-156">![Passaggio del mouse (lontano)](images/640px-interactibleobject-states-near-hover.jpg)</span><span class="sxs-lookup"><span data-stu-id="15edf-156">![Hover (Far)](images/640px-interactibleobject-states-near-hover.jpg)</span></span><br>
        <span data-ttu-id="15edf-157">**Passaggio del mouse (lontano)**</span><span class="sxs-lookup"><span data-stu-id="15edf-157">**Hover (Far)**</span></span><br>
        <span data-ttu-id="15edf-158">Evidenziazione basata sulla prossimità della mano.</span><span class="sxs-lookup"><span data-stu-id="15edf-158">Highlighting based on the proximity of the hand.</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="15edf-159">![Passaggio del mouse (vicino)](images/640px-interactibleobject-states-near-hovernear.jpg)</span><span class="sxs-lookup"><span data-stu-id="15edf-159">![Hover (Near)](images/640px-interactibleobject-states-near-hovernear.jpg)</span></span><br>
        <span data-ttu-id="15edf-160">**Passaggio del mouse (vicino)**</span><span class="sxs-lookup"><span data-stu-id="15edf-160">**Hover (Near)**</span></span><br>
        <span data-ttu-id="15edf-161">Le dimensioni dell'evidenziazione cambiano in base alla distanza dalla mano.</span><span class="sxs-lookup"><span data-stu-id="15edf-161">Highlight size changes based on the distance to the hand.</span></span>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        <span data-ttu-id="15edf-162">![Tocco/pressione](images/640px-interactibleobject-states-near-press.jpg)</span><span class="sxs-lookup"><span data-stu-id="15edf-162">![Touch / press](images/640px-interactibleobject-states-near-press.jpg)</span></span><br>
        <span data-ttu-id="15edf-163">**Tocco/pressione**</span><span class="sxs-lookup"><span data-stu-id="15edf-163">**Touch / press**</span></span><br>
        <span data-ttu-id="15edf-164">Feedback visivo e audio.</span><span class="sxs-lookup"><span data-stu-id="15edf-164">Visual plus audio feedback.</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="15edf-165">![Afferrare](images/640px-interactibleobject-states-near-grasp.jpg)</span><span class="sxs-lookup"><span data-stu-id="15edf-165">![Grasp](images/640px-interactibleobject-states-near-grasp.jpg)</span></span><br>
        <span data-ttu-id="15edf-166">**Afferrare**</span><span class="sxs-lookup"><span data-stu-id="15edf-166">**Grasp**</span></span><br>
        <span data-ttu-id="15edf-167">Feedback visivo e audio.</span><span class="sxs-lookup"><span data-stu-id="15edf-167">Visual plus audio feedback.</span></span>
    :::column-end:::
:::row-end:::

<br>

<br>

---

<span data-ttu-id="15edf-168">Un [pulsante in HoloLens 2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html) è un esempio di visualizzazione dei diversi stati di interazione di input:</span><span class="sxs-lookup"><span data-stu-id="15edf-168">A [button on HoloLens 2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html) is an example of how the different input interaction states are visualized:</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="15edf-169">![Valore predefinito](images/640px-interactibleobject-pressablebutton-default.jpg)</span><span class="sxs-lookup"><span data-stu-id="15edf-169">![Default](images/640px-interactibleobject-pressablebutton-default.jpg)</span></span><br>
        <span data-ttu-id="15edf-170">**Default**</span><span class="sxs-lookup"><span data-stu-id="15edf-170">**Default**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="15edf-171">![Passaggio del mouse](images/640px-interactibleobject-pressablebutton-hover.jpg)</span><span class="sxs-lookup"><span data-stu-id="15edf-171">![Hover](images/640px-interactibleobject-pressablebutton-hover.jpg)</span></span><br>
        <span data-ttu-id="15edf-172">**Passaggio del mouse**</span><span class="sxs-lookup"><span data-stu-id="15edf-172">**Hover**</span></span><br>
        <span data-ttu-id="15edf-173">Rivela un effetto di illuminazione basato sulla prossimità.</span><span class="sxs-lookup"><span data-stu-id="15edf-173">Reveal a proximity-based lighting effect.</span></span>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        <span data-ttu-id="15edf-174">![Tocco](images/640px-interactibleobject-pressablebutton-touch.jpg)</span><span class="sxs-lookup"><span data-stu-id="15edf-174">![Touch](images/640px-interactibleobject-pressablebutton-touch.jpg)</span></span><br>
        <span data-ttu-id="15edf-175">**Tocco**</span><span class="sxs-lookup"><span data-stu-id="15edf-175">**Touch**</span></span><br>
        <span data-ttu-id="15edf-176">Mostra effetto ondulato.</span><span class="sxs-lookup"><span data-stu-id="15edf-176">Show ripple effect.</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="15edf-177">![Premere](images/640px-interactibleobject-pressablebutton-press.jpg)</span><span class="sxs-lookup"><span data-stu-id="15edf-177">![Press](images/640px-interactibleobject-pressablebutton-press.jpg)</span></span><br>
        <span data-ttu-id="15edf-178">**Premere**</span><span class="sxs-lookup"><span data-stu-id="15edf-178">**Press**</span></span><br>
        <span data-ttu-id="15edf-179">Spostare il pannello anteriore.</span><span class="sxs-lookup"><span data-stu-id="15edf-179">Move the front plate.</span></span>
    :::column-end:::
:::row-end:::

<br>

---

:::row:::
    :::column:::
        ### <a name="the-ring-visual-cue-on-hololens-2br"></a><span data-ttu-id="15edf-180">Segnale visivo "anello" su HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="15edf-180">The "ring" visual cue on HoloLens 2</span></span><br>
        <span data-ttu-id="15edf-181">In HoloLens 2 è presente un segnale visivo aggiuntivo che può aiutare la percezione della profondità da parte dell'utente.</span><span class="sxs-lookup"><span data-stu-id="15edf-181">On HoloLens 2, there's an extra visual cue, which can help the user's perception of depth.</span></span> <span data-ttu-id="15edf-182">Un anello vicino alla punta del dito viene visualizzato e ridimensionato man mano che la punta del dito si avvicina all'oggetto.</span><span class="sxs-lookup"><span data-stu-id="15edf-182">A ring near their fingertip shows up and scales down as the fingertip gets closer to the object.</span></span> <span data-ttu-id="15edf-183">L'anello converge infine in un punto quando viene raggiunto lo stato premuto.</span><span class="sxs-lookup"><span data-stu-id="15edf-183">The ring eventually converges into a dot when the pressed state is reached.</span></span> <span data-ttu-id="15edf-184">Questo oggetto visivo consente all'utente di comprendere quanto sono distasi dall'oggetto.</span><span class="sxs-lookup"><span data-stu-id="15edf-184">This visual affordance helps the user understand how far they are from the object.</span></span><br>
        <br>
        <span data-ttu-id="15edf-185">*Ciclo video: esempio di feedback visivo basato sulla prossimità a un rettangolo di selezione*</span><span class="sxs-lookup"><span data-stu-id="15edf-185">*Video loop: Example of visual feedback based on proximity to a bounding box*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="15edf-186">![space](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="15edf-186">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="15edf-187">![Feedback visivo sulla prossimità manuale](images/HoloLens2_Proximity.gif)</span><span class="sxs-lookup"><span data-stu-id="15edf-187">![Visual feedback on hand proximity](images/HoloLens2_Proximity.gif)</span></span><br>
    :::column-end:::
:::row-end:::


<br>

---


### <a name="audio-cues"></a><span data-ttu-id="15edf-188">Segnali audio</span><span class="sxs-lookup"><span data-stu-id="15edf-188">Audio cues</span></span>

<span data-ttu-id="15edf-189">Per le interazioni con la mano diretta, un feedback audio appropriato può migliorare notevolmente l'esperienza utente.</span><span class="sxs-lookup"><span data-stu-id="15edf-189">For direct hand interactions, proper audio feedback can dramatically improve the user experience.</span></span> <span data-ttu-id="15edf-190">Usare il feedback audio per comunicare i segnali seguenti:</span><span class="sxs-lookup"><span data-stu-id="15edf-190">Use audio feedback to communicate the following cues:</span></span>
* <span data-ttu-id="15edf-191">**Inizio contatto:** riproduce l'audio all'inizio del tocco</span><span class="sxs-lookup"><span data-stu-id="15edf-191">**Contact begins**: Play sound when touch begins</span></span>
* <span data-ttu-id="15edf-192">**Fine contatto:** riprodurre l'audio all'estremità del tocco</span><span class="sxs-lookup"><span data-stu-id="15edf-192">**Contact ends**: Play sound on touch end</span></span>
* <span data-ttu-id="15edf-193">**Inizia a afferrare:** riproduci l'audio all'avvio della cattura</span><span class="sxs-lookup"><span data-stu-id="15edf-193">**Grab begins**: Play sound when grab starts</span></span>
* <span data-ttu-id="15edf-194">**Grab ends (Fine afferra):** riproduci l'audio al termine dell'afferrare</span><span class="sxs-lookup"><span data-stu-id="15edf-194">**Grab ends**: Play sound when grab ends</span></span>

<br>

---

:::row:::
    :::column:::
        ### <a name="voice-commandingbr"></a><span data-ttu-id="15edf-195">Esecuzione di comandi vocali</span><span class="sxs-lookup"><span data-stu-id="15edf-195">Voice commanding</span></span><br>
        <span data-ttu-id="15edf-196">Per tutti gli oggetti che possono interagire, è importante supportare opzioni di interazione alternative.</span><span class="sxs-lookup"><span data-stu-id="15edf-196">For any interactable objects, it's important to support alternative interaction options.</span></span> <span data-ttu-id="15edf-197">Per impostazione predefinita, è consigliabile [che l'esecuzione di comandi vocali](../out-of-scope/voice-design.md) sia supportata per tutti gli oggetti che possono interagire.</span><span class="sxs-lookup"><span data-stu-id="15edf-197">By default, we recommend that [voice commanding](../out-of-scope/voice-design.md) be supported for any objects that are interactable.</span></span> <span data-ttu-id="15edf-198">Per migliorare l'individuabilità, è anche possibile fornire una descrizione comando durante lo stato del passaggio del mouse.</span><span class="sxs-lookup"><span data-stu-id="15edf-198">To improve discoverability, you can also provide a tooltip during the hover state.</span></span><br>
        <br>
        <span data-ttu-id="15edf-199">*Immagine: Descrizione comando vocale*</span><span class="sxs-lookup"><span data-stu-id="15edf-199">*Image: Tooltip for the voice command*</span></span>
    :::column-end:::
        :::column:::
       ![comandi vocali](images/640px-interactibleobject-voicecommand.png)<br>
    :::column-end:::
:::row-end:::


<br>

---

## <a name="sizing-recommendations"></a><span data-ttu-id="15edf-201">Consigli sul ridimensionamento</span><span class="sxs-lookup"><span data-stu-id="15edf-201">Sizing recommendations</span></span>

<span data-ttu-id="15edf-202">Per garantire che tutti gli oggetti interagiscibili possano essere facilmente toccati, è consigliabile assicurarsi che l'oggetto interagiscibile soddisfi le dimensioni minime in base alla distanza che viene posta dall'utente.</span><span class="sxs-lookup"><span data-stu-id="15edf-202">To ensure all interactable objects can easily be touched, we recommend making sure the interactable meets a minimum size based on the distance it's placed from the user.</span></span> <span data-ttu-id="15edf-203">L'angolo visivo viene spesso misurato in gradi di arco visivo. L'angolo visivo si basa sulla distanza tra gli occhi dell'utente e l'oggetto e rimane costante, mentre le dimensioni fisiche della destinazione possono cambiare quando cambia la distanza dall'utente.</span><span class="sxs-lookup"><span data-stu-id="15edf-203">The visual angle is often measured in degrees of visual arc. Visual angle is based on the distance between the user's eyes and the object and stays constant, while the physical size of the target may change as the distance from the user changes.</span></span> <span data-ttu-id="15edf-204">Per determinare le dimensioni fisiche necessarie di un oggetto in base alla distanza dall'utente, provare a usare un calcolatore dell'angolo visivo come [questo](https://elvers.us/perception/visualAngle/).</span><span class="sxs-lookup"><span data-stu-id="15edf-204">To determine the necessary physical size of an object based on the distance from the user, try using a visual angle calculator such as [this one](https://elvers.us/perception/visualAngle/).</span></span>

<span data-ttu-id="15edf-205">Di seguito sono riportate le raccomandazioni per le dimensioni minime del contenuto interagiscibile.</span><span class="sxs-lookup"><span data-stu-id="15edf-205">Below are the recommendations for minimum sizes of interactable content.</span></span>

### <a name="target-size-for-direct-hand-interaction"></a><span data-ttu-id="15edf-206">Dimensioni di destinazione per l'interazione diretta con la mano</span><span class="sxs-lookup"><span data-stu-id="15edf-206">Target size for direct hand interaction</span></span>

| <span data-ttu-id="15edf-207">Distanza</span><span class="sxs-lookup"><span data-stu-id="15edf-207">Distance</span></span> | <span data-ttu-id="15edf-208">Angolo di visualizzazione</span><span class="sxs-lookup"><span data-stu-id="15edf-208">Viewing angle</span></span> | <span data-ttu-id="15edf-209">Dimensione</span><span class="sxs-lookup"><span data-stu-id="15edf-209">Size</span></span> |
|---------|---------|---------|
| <span data-ttu-id="15edf-210">45 cm</span><span class="sxs-lookup"><span data-stu-id="15edf-210">45 cm</span></span>  | <span data-ttu-id="15edf-211">non inferiore a 2°</span><span class="sxs-lookup"><span data-stu-id="15edf-211">no smaller than 2°</span></span> | <span data-ttu-id="15edf-212">1,6 x 1,6 cm</span><span class="sxs-lookup"><span data-stu-id="15edf-212">1.6 x 1.6 cm</span></span> |

<span data-ttu-id="15edf-213">![Dimensioni di destinazione per l'interazione diretta con la mano](images/TargetSizingNear.jpg)</span><span class="sxs-lookup"><span data-stu-id="15edf-213">![Target size for direct hand interaction](images/TargetSizingNear.jpg)</span></span><br>
<span data-ttu-id="15edf-214">*Dimensioni di destinazione per l'interazione diretta con la mano*</span><span class="sxs-lookup"><span data-stu-id="15edf-214">*Target size for direct hand interaction*</span></span>

<br>

### <a name="target-size-for-buttons"></a><span data-ttu-id="15edf-215">Dimensioni di destinazione per i pulsanti</span><span class="sxs-lookup"><span data-stu-id="15edf-215">Target size for buttons</span></span>

<span data-ttu-id="15edf-216">Quando si creano pulsanti per l'interazione diretta, è consigliabile avere dimensioni minime maggiori di 3,2 x 3,2 cm per assicurarsi che sia disponibile spazio sufficiente per contenere un'icona e potenzialmente del testo.</span><span class="sxs-lookup"><span data-stu-id="15edf-216">When creating buttons for direct interaction, we recommend a larger minimum size of 3.2 x 3.2 cm to ensure that there's enough space to contain an icon and potentially some text.</span></span>

| <span data-ttu-id="15edf-217">Distanza</span><span class="sxs-lookup"><span data-stu-id="15edf-217">Distance</span></span> | <span data-ttu-id="15edf-218">Dimensione minima</span><span class="sxs-lookup"><span data-stu-id="15edf-218">Minimum size</span></span> |
|---------|---------|
| <span data-ttu-id="15edf-219">45 cm</span><span class="sxs-lookup"><span data-stu-id="15edf-219">45 cm</span></span>  | <span data-ttu-id="15edf-220">3,2 x 3,2 cm</span><span class="sxs-lookup"><span data-stu-id="15edf-220">3.2 x 3.2 cm</span></span> |

<span data-ttu-id="15edf-221">![Dimensioni di destinazione per i pulsanti](images/TargetSizingButtons.png)</span><span class="sxs-lookup"><span data-stu-id="15edf-221">![Target size for the buttons](images/TargetSizingButtons.png)</span></span><br>
<span data-ttu-id="15edf-222">*Dimensioni di destinazione per i pulsanti*</span><span class="sxs-lookup"><span data-stu-id="15edf-222">*Target size for the buttons*</span></span>

<br>

### <a name="target-size-for-hand-ray-or-gaze-interaction"></a><span data-ttu-id="15edf-223">Dimensioni di destinazione per l'interazione con il raggio della mano o lo sguardo</span><span class="sxs-lookup"><span data-stu-id="15edf-223">Target size for hand ray or gaze interaction</span></span>
| <span data-ttu-id="15edf-224">Distanza</span><span class="sxs-lookup"><span data-stu-id="15edf-224">Distance</span></span> | <span data-ttu-id="15edf-225">Angolo di visualizzazione</span><span class="sxs-lookup"><span data-stu-id="15edf-225">Viewing angle</span></span> | <span data-ttu-id="15edf-226">Dimensione</span><span class="sxs-lookup"><span data-stu-id="15edf-226">Size</span></span> |
|---------|---------|---------|
| <span data-ttu-id="15edf-227">2 m</span><span class="sxs-lookup"><span data-stu-id="15edf-227">2 m</span></span>  | <span data-ttu-id="15edf-228">non inferiore a 1°</span><span class="sxs-lookup"><span data-stu-id="15edf-228">no smaller than 1°</span></span> | <span data-ttu-id="15edf-229">3,5 x 3,5 cm</span><span class="sxs-lookup"><span data-stu-id="15edf-229">3.5 x 3.5 cm</span></span> |

<span data-ttu-id="15edf-230">![Dimensioni di destinazione per l'interazione con il raggio della mano o lo sguardo](images/TargetSizingFar.jpg)</span><span class="sxs-lookup"><span data-stu-id="15edf-230">![Target size for hand ray or gaze interaction](images/TargetSizingFar.jpg)</span></span><br>
<span data-ttu-id="15edf-231">*Dimensioni di destinazione per l'interazione con il raggio della mano o lo sguardo*</span><span class="sxs-lookup"><span data-stu-id="15edf-231">*Target size for hand ray or gaze interaction*</span></span>

<br>

---

## <a name="interactable-object-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="15edf-232">Oggetto interagiscibile in MRTK (Mixed Reality Toolkit) per Unity</span><span class="sxs-lookup"><span data-stu-id="15edf-232">Interactable object in MRTK (Mixed Reality Toolkit) for Unity</span></span>

<span data-ttu-id="15edf-233">In **[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** è possibile usare lo script [**Interactable**](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Interactable/Scripts) per fare in modo che gli oggetti rispondano a vari tipi di stati di interazione di input.</span><span class="sxs-lookup"><span data-stu-id="15edf-233">In **[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)**, you can use the script [**Interactable**](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Interactable/Scripts) to make objects respond to various types of input interaction states.</span></span> <span data-ttu-id="15edf-234">Supporta vari tipi di temi che consentono di definire gli stati di visualizzazione controllando le proprietà dell'oggetto, ad esempio colore, dimensioni, materiale e shader.</span><span class="sxs-lookup"><span data-stu-id="15edf-234">It supports various types of themes that allow you define visual states by controlling object properties such as color, size, material, and shader.</span></span>

* [<span data-ttu-id="15edf-235">Interagibile</span><span class="sxs-lookup"><span data-stu-id="15edf-235">Interactable</span></span>](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/interactable)
* [<span data-ttu-id="15edf-236">Button</span><span class="sxs-lookup"><span data-stu-id="15edf-236">Button</span></span>](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/button)
* [<span data-ttu-id="15edf-237">Scena degli esempi di interazione manuale</span><span class="sxs-lookup"><span data-stu-id="15edf-237">Hand interaction examples scene</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_HandInteractionExamples.md)

<span data-ttu-id="15edf-238">Lo shader Standard di MixedRealityToolkit  offre varie opzioni, ad esempio la luce di prossimità, che consente di creare segnali visivi e audio.</span><span class="sxs-lookup"><span data-stu-id="15edf-238">MixedRealityToolkit's Standard shader provides various options such as **proximity light** that helps you create visual and audio cues.</span></span>

* [<span data-ttu-id="15edf-239">MRTK Standard Shader</span><span class="sxs-lookup"><span data-stu-id="15edf-239">MRTK Standard Shader</span></span>](/windows/mixed-reality/mrtk-unity/features/rendering/mrtk-standard-shader)

<br>

---

## <a name="see-also"></a><span data-ttu-id="15edf-240">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="15edf-240">See also</span></span>

* [<span data-ttu-id="15edf-241">Cursori</span><span class="sxs-lookup"><span data-stu-id="15edf-241">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="15edf-242">Raggio della mano</span><span class="sxs-lookup"><span data-stu-id="15edf-242">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="15edf-243">Button</span><span class="sxs-lookup"><span data-stu-id="15edf-243">Button</span></span>](button.md)
* [<span data-ttu-id="15edf-244">Oggetto che supporta interazioni</span><span class="sxs-lookup"><span data-stu-id="15edf-244">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="15edf-245">Rettangolo di selezione e barra dell'app</span><span class="sxs-lookup"><span data-stu-id="15edf-245">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="15edf-246">Manipolazione</span><span class="sxs-lookup"><span data-stu-id="15edf-246">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="15edf-247">Menu a mano</span><span class="sxs-lookup"><span data-stu-id="15edf-247">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="15edf-248">Menu adiacente</span><span class="sxs-lookup"><span data-stu-id="15edf-248">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="15edf-249">Raccolta di oggetti</span><span class="sxs-lookup"><span data-stu-id="15edf-249">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="15edf-250">Comando vocale</span><span class="sxs-lookup"><span data-stu-id="15edf-250">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="15edf-251">Tastiera</span><span class="sxs-lookup"><span data-stu-id="15edf-251">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="15edf-252">Descrizione comando</span><span class="sxs-lookup"><span data-stu-id="15edf-252">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="15edf-253">Slate</span><span class="sxs-lookup"><span data-stu-id="15edf-253">Slate</span></span>](slate.md)
* [<span data-ttu-id="15edf-254">Dispositivo di scorrimento</span><span class="sxs-lookup"><span data-stu-id="15edf-254">Slider</span></span>](slider.md)
* [<span data-ttu-id="15edf-255">Shader</span><span class="sxs-lookup"><span data-stu-id="15edf-255">Shader</span></span>](shader.md)
* [<span data-ttu-id="15edf-256">Billboarding e tag-along</span><span class="sxs-lookup"><span data-stu-id="15edf-256">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="15edf-257">Visualizzazione dello stato</span><span class="sxs-lookup"><span data-stu-id="15edf-257">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="15edf-258">Magnetismo di superficie</span><span class="sxs-lookup"><span data-stu-id="15edf-258">Surface magnetism</span></span>](surface-magnetism.md)
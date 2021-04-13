---
title: Manipolazione diretta con le mani
description: Informazioni sulla manipolazione diretta, un modello di input in cui gli utenti toccano gli ologrammi direttamente con le mani.
author: caseymeekhof
ms.author: cmeekhof
ms.date: 04/02/2019
ms.topic: article
ms.localizationpriority: high
keywords: Realtà mista, Sguardo fisso, selezione della destinazione con lo sguardo, interazione, progettazione, a portata di mano, HoloLens, visore VR realtà mista, visore VR di windows mixed reality, visore per realtà virtuale, MRTK, Mixed Reality Toolkit, pulsante, collisori, cubo di delimitazione, 2D, movimenti istintivi
ms.openlocfilehash: 555b27764d077332a2d8618672e6aed7def1dd3f
ms.sourcegitcommit: 1c9035487270af76c6eaba11b11f6fc56c008135
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/13/2021
ms.locfileid: "107300096"
---
# <a name="direct-manipulation-with-hands"></a><span data-ttu-id="72249-104">Manipolazione diretta con le mani</span><span class="sxs-lookup"><span data-stu-id="72249-104">Direct manipulation with hands</span></span>

![Pulsante](images/UX_Hero_Manipulation.jpg)

<span data-ttu-id="72249-106">La manipolazione diretta è un modello di input che consiste nel toccare gli ologrammi direttamente con le mani.</span><span class="sxs-lookup"><span data-stu-id="72249-106">Direct manipulation is an input model that involves touching holograms directly with your hands.</span></span> <span data-ttu-id="72249-107">L'idea alla base di questo concetto è che il comportamento degli oggetti deve essere uguale a quello che avrebbero nella realtà.</span><span class="sxs-lookup"><span data-stu-id="72249-107">The idea behind this concept is that objects behave just as they would in the real world.</span></span> <span data-ttu-id="72249-108">I pulsanti possono essere attivati semplicemente premendoli, gli oggetti possono essere selezionati afferrandoli e il contenuto 2D si comporta come un touchscreen virtuale.</span><span class="sxs-lookup"><span data-stu-id="72249-108">Buttons can be activated simply by pressing them, objects can be picked up by grabbing them, and 2D content behaves like a virtual touchscreen.</span></span> <span data-ttu-id="72249-109">La manipolazione diretta è basata sull'invito, ovvero è facile da usare.</span><span class="sxs-lookup"><span data-stu-id="72249-109">Direct manipulation is affordance-based, meaning it's user-friendly.</span></span> <span data-ttu-id="72249-110">Non esistono movimenti simbolici da insegnare agli utenti.</span><span class="sxs-lookup"><span data-stu-id="72249-110">There are no symbolic gestures to teach users.</span></span> <span data-ttu-id="72249-111">Tutte le interazioni avvengono intorno a un elemento visivo che è possibile toccare o afferrare.</span><span class="sxs-lookup"><span data-stu-id="72249-111">All interactions are built around a visual element that you can touch or grab.</span></span> <span data-ttu-id="72249-112">È considerata un modello di input "da vicino", in quanto è ideale per interagire con contenuto raggiungibile stendendo le braccia.</span><span class="sxs-lookup"><span data-stu-id="72249-112">It's considered a "near" input model in that it's best used for interacting with content within arms reach.</span></span>

## <a name="device-support"></a><span data-ttu-id="72249-113">Supporto di dispositivi</span><span class="sxs-lookup"><span data-stu-id="72249-113">Device support</span></span>

<table>
<colgroup>
    <col width="33%" />
    <col width="22%" />
    <col width="22%" />
    <col width="22%" />
</colgroup>
<tr>
     <td><span data-ttu-id="72249-114"><strong>Modello di input</strong></span><span class="sxs-lookup"><span data-stu-id="72249-114"><strong>Input model</strong></span></span></td>
     <td><span data-ttu-id="72249-115"><a href="/hololens/hololens1-hardware"><strong>HoloLens (prima generazione)</strong></a></span><span class="sxs-lookup"><span data-stu-id="72249-115"><a href="/hololens/hololens1-hardware"><strong>HoloLens (1st gen)</strong></a></span></span></td>
     <td><span data-ttu-id="72249-116"><a href="/hololens/hololens2-hardware"><strong>HoloLens 2</strong></a></span><span class="sxs-lookup"><span data-stu-id="72249-116"><a href="/hololens/hololens2-hardware"><strong>HoloLens 2</strong></a></span></span></td>
     <td><span data-ttu-id="72249-117"><a href="/windows/mixed-reality/immersive-headset-hardware-details"><strong>Visori VR immersive</strong></a></span><span class="sxs-lookup"><span data-stu-id="72249-117"><a href="/windows/mixed-reality/immersive-headset-hardware-details"><strong>Immersive headsets</strong></a></span></span></td>
</tr>
<tr>
     <td><span data-ttu-id="72249-118">Manipolazione diretta con le mani</span><span class="sxs-lookup"><span data-stu-id="72249-118">Direct manipulation with hands</span></span></td>
     <td><span data-ttu-id="72249-119">❌ Non supportata</span><span class="sxs-lookup"><span data-stu-id="72249-119">❌ Not supported</span></span></td>
     <td><span data-ttu-id="72249-120">✔️ Consigliata</span><span class="sxs-lookup"><span data-stu-id="72249-120">✔️ Recommended</span></span></td>
     <td><span data-ttu-id="72249-121">➕ Supportata.</span><span class="sxs-lookup"><span data-stu-id="72249-121">➕ Supported.</span></span>  <span data-ttu-id="72249-122">Per l'interfaccia utente, consigliamo invece <a href="point-and-commit.md">Puntamento e commit con le mani</a>.</span><span class="sxs-lookup"><span data-stu-id="72249-122">For UI, we recommend <a href="point-and-commit.md">point and commit with hands</a> instead.</span></span></td>
    
</tr>
</table>


<span data-ttu-id="72249-123">La manipolazione diretta è un modello di input principale in HoloLens 2 che usa il nuovo sistema di tracciamento delle mani articolato.</span><span class="sxs-lookup"><span data-stu-id="72249-123">Direct manipulation is a primary input model on HoloLens 2, which uses the new articulated hand-tracking system.</span></span> <span data-ttu-id="72249-124">Il modello di input è disponibile anche su visori VR immersive tramite l'uso di controller del movimento, ma non è consigliato come mezzo principale di interazione al di fuori della manipolazione di oggetti.</span><span class="sxs-lookup"><span data-stu-id="72249-124">The input model is also available on immersive headsets by using motion controllers, but isn't recommended as a primary means of interaction outside of object manipulation.</span></span> <span data-ttu-id="72249-125">La manipolazione diretta non è disponibile in HoloLens (prima generazione).</span><span class="sxs-lookup"><span data-stu-id="72249-125">Direct manipulation isn't available on HoloLens (1st gen).</span></span>

<br>

---

## <a name="collidable-fingertip"></a><span data-ttu-id="72249-126">Punta del dito di collisione</span><span class="sxs-lookup"><span data-stu-id="72249-126">Collidable fingertip</span></span>

<span data-ttu-id="72249-127">In HoloLens 2 le mani dell'utente vengono riconosciute e interpretate come modelli scheletrici delle mani sinistra e destra.</span><span class="sxs-lookup"><span data-stu-id="72249-127">On HoloLens 2, the user's hands are recognized and interpreted as left and right-hand skeletal models.</span></span> <span data-ttu-id="72249-128">Per implementare l'idea di toccare gli ologrammi direttamente con le mani, in teoria si potrebbero applicare cinque collisori alle cinque punte delle dita del modello scheletrico di ogni mano.</span><span class="sxs-lookup"><span data-stu-id="72249-128">To implement the idea of touching holograms directly with hands, ideally, five colliders could be attached to the five fingertips of each hand skeletal model.</span></span> <span data-ttu-id="72249-129">Tuttavia, a causa della mancanza di feedback tattili, 10 punte di dita di collisione possono causare collisioni inaspettate e imprevedibili con gli ologrammi.</span><span class="sxs-lookup"><span data-stu-id="72249-129">However, because of the lack of tactile feedback, 10 collidable fingertips can cause unexpected and unpredictable collisions with holograms.</span></span> 

<span data-ttu-id="72249-130">È consigliabile applicare solo un collisore a ogni dito indice.</span><span class="sxs-lookup"><span data-stu-id="72249-130">We suggest only putting a collider on each index finger.</span></span> <span data-ttu-id="72249-131">Le punte degli indici di collisione possono comunque fungere da punti tocco attivi per vari movimenti di tocco che coinvolgono altre dita.</span><span class="sxs-lookup"><span data-stu-id="72249-131">The collidable index fingertips can still serve as active touch points for diverse touch gestures involving other fingers.</span></span> <span data-ttu-id="72249-132">I movimenti di tocco includono la pressione con un dito, il tocco con un dito, la pressione con due dita e la pressione con cinque dita, come mostrato di seguito:</span><span class="sxs-lookup"><span data-stu-id="72249-132">Touch gestures include One-finger press, One-finger tap, Two-finger press, and Five-finger press, as shown below:</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="72249-133">![Punta del dito di collisione](images/Collidable-Fingertip.jpg)</span><span class="sxs-lookup"><span data-stu-id="72249-133">![collidable fingertip](images/Collidable-Fingertip.jpg)</span></span><br>
       <span data-ttu-id="72249-134">**Punta del dito di collisione**</span><span class="sxs-lookup"><span data-stu-id="72249-134">**Collidable fingertip**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="72249-135">![Pressione con un dito](images/Collidable-Fingertip-1-finger-press.jpg)</span><span class="sxs-lookup"><span data-stu-id="72249-135">![One-finger press](images/Collidable-Fingertip-1-finger-press.jpg)</span></span><br>
        <span data-ttu-id="72249-136">**Pressione con un dito**</span><span class="sxs-lookup"><span data-stu-id="72249-136">**One-finger press**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="72249-137">![Tocco con un dito](images/Collidable-Fingertip-1-finger-tap.jpg)</span><span class="sxs-lookup"><span data-stu-id="72249-137">![One-finger tap](images/Collidable-Fingertip-1-finger-tap.jpg)</span></span><br>
       <span data-ttu-id="72249-138">**Tocco con un dito**</span><span class="sxs-lookup"><span data-stu-id="72249-138">**One-finger tap**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="72249-139">![Pressione con cinque dita](images/Collidable-Fingertip-5-finger-press.jpg)</span><span class="sxs-lookup"><span data-stu-id="72249-139">![Five-finger press](images/Collidable-Fingertip-5-finger-press.jpg)</span></span><br>
       <span data-ttu-id="72249-140">**Pressione con cinque dita**</span><span class="sxs-lookup"><span data-stu-id="72249-140">**Five-finger press**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

### <a name="sphere-collider"></a><span data-ttu-id="72249-141">Collisore sfera</span><span class="sxs-lookup"><span data-stu-id="72249-141">Sphere collider</span></span>

<span data-ttu-id="72249-142">Invece di usare una forma generica casuale, è consigliabile usare un collisore sferico.</span><span class="sxs-lookup"><span data-stu-id="72249-142">Instead of using a random generic shape, we suggest you use a sphere collider.</span></span> <span data-ttu-id="72249-143">È possibile quindi eseguirne il rendering visivo per fornire segnali migliori per la destinazione più vicina.</span><span class="sxs-lookup"><span data-stu-id="72249-143">Then you can visually render it to provide better cues for near targeting.</span></span> <span data-ttu-id="72249-144">Il diametro della sfera deve corrispondere allo spessore del dito indice per aumentare l'accuratezza del tocco.</span><span class="sxs-lookup"><span data-stu-id="72249-144">The sphere's diameter should match the thickness of the index finger to increase touch accuracy.</span></span> <span data-ttu-id="72249-145">È più facile recuperare la variabile dello spessore di un dito chiamando l'API relativa alla mano.</span><span class="sxs-lookup"><span data-stu-id="72249-145">It's easier to retrieve the variable of finger thickness by calling the hand API.</span></span>

### <a name="fingertip-cursor"></a><span data-ttu-id="72249-146">Cursore punta del dito</span><span class="sxs-lookup"><span data-stu-id="72249-146">Fingertip cursor</span></span>

<span data-ttu-id="72249-147">Oltre al rendering di una sfera di collisione sulla punta dell'indice, è stato creato un cursore avanzato per la punta del dito per migliorare l'esperienza di selezione della destinazione da vicino.</span><span class="sxs-lookup"><span data-stu-id="72249-147">In addition to rendering a collidable sphere on the index fingertip, we've created an advanced fingertip cursor to achieve a better near-targeting experience.</span></span> <span data-ttu-id="72249-148">Si tratta di un cursore a forma di anello associato alla punta dell'indice.</span><span class="sxs-lookup"><span data-stu-id="72249-148">It's a donut-shaped cursor attached to the index fingertip.</span></span> <span data-ttu-id="72249-149">In base alla prossimità, reagisce in modo dinamico a una destinazione per l'orientamento e le dimensioni come indicato di seguito:</span><span class="sxs-lookup"><span data-stu-id="72249-149">According to proximity, it dynamically reacts to a target for orientation and size as detailed below:</span></span>

* <span data-ttu-id="72249-150">Quando un indice si sposta verso un ologramma, il cursore è sempre parallelo alla superficie dell'ologramma e si restringe gradualmente.</span><span class="sxs-lookup"><span data-stu-id="72249-150">When an index finger moves toward a hologram, the cursor is always parallel to the hologram's surface and gradually shrinks its size.</span></span>
* <span data-ttu-id="72249-151">Non appena il dito tocca la superficie, il cursore si riduce a un punto ed emette un evento tocco.</span><span class="sxs-lookup"><span data-stu-id="72249-151">As soon as the finger touches the surface, the cursor shrinks into a dot and emits a touch event.</span></span>

<span data-ttu-id="72249-152">Con il feedback interattivo, gli utenti possono eseguire attività di selezione della destinazione da vicino ad alta precisione, ad esempio l'attivazione di un collegamento ipertestuale o la pressione di un pulsante, come illustrato di seguito.</span><span class="sxs-lookup"><span data-stu-id="72249-152">With interactive feedback, users can achieve high precision near-targeting tasks, such as triggering a hyperlink or pressing a button as shown below.</span></span> 

:::row:::
    :::column:::
       <span data-ttu-id="72249-153">![Cursore punta del dito da lontano](images/Fingertip-cursor-far.jpg)</span><span class="sxs-lookup"><span data-stu-id="72249-153">![Fingertip cursor far](images/Fingertip-cursor-far.jpg)</span></span><br>
       <span data-ttu-id="72249-154">**Cursore punta del dito da lontano**</span><span class="sxs-lookup"><span data-stu-id="72249-154">**Fingertip cursor far**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="72249-155">![Cursore punta del dito da vicino](images/Fingertip-cursor-near.jpg)</span><span class="sxs-lookup"><span data-stu-id="72249-155">![Fingertip cursor near](images/Fingertip-cursor-near.jpg)</span></span><br>
        <span data-ttu-id="72249-156">**Cursore punta del dito da vicino**</span><span class="sxs-lookup"><span data-stu-id="72249-156">**Fingertip cursor near**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="72249-157">![Cursore punta del dito con contatto](images/Fingertip-cursor-contact.jpg)</span><span class="sxs-lookup"><span data-stu-id="72249-157">![Fingertip cursor contact](images/Fingertip-cursor-contact.jpg)</span></span><br>
       <span data-ttu-id="72249-158">**Cursore punta del dito con contatto**</span><span class="sxs-lookup"><span data-stu-id="72249-158">**Fingertip cursor contact**</span></span><br>
    :::column-end:::
:::row-end:::

<br>



## <a name="bounding-box-with-proximity-shader"></a><span data-ttu-id="72249-159">Cubo di delimitazione con shader prossimità</span><span class="sxs-lookup"><span data-stu-id="72249-159">Bounding box with proximity shader</span></span>

<span data-ttu-id="72249-160">L'ologramma stesso richiede anche la possibilità di fornire feedback audio e video per compensare la mancanza di feedback tattili.</span><span class="sxs-lookup"><span data-stu-id="72249-160">The hologram itself also requires the ability to provide both visual and audio feedback to compensate the lack of tactile feedback.</span></span> <span data-ttu-id="72249-161">Su questa esigenza si basa il concetto di cubo di delimitazione con shader prossimità.</span><span class="sxs-lookup"><span data-stu-id="72249-161">For that, we generate the concept of a bounding box with a proximity shader.</span></span> <span data-ttu-id="72249-162">Un cubo di delimitazione è un'area volumetrica minima che racchiude un oggetto 3D.</span><span class="sxs-lookup"><span data-stu-id="72249-162">A bounding box is a minimum volumetric area that encloses a 3D object.</span></span> <span data-ttu-id="72249-163">Il cubo di delimitazione è dotato di un meccanismo di rendering interattivo denominato shader prossimità.</span><span class="sxs-lookup"><span data-stu-id="72249-163">The bounding box has an interactive rendering mechanism called a proximity shader.</span></span> <span data-ttu-id="72249-164">Comportamento dello shader prossimità:</span><span class="sxs-lookup"><span data-stu-id="72249-164">The proximity shader behaves:</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="72249-165">![Posizionamento del dito (da lontano) con feedback visivo](images/bounding-box-with-proximity-shader-hover-far.jpg)</span><span class="sxs-lookup"><span data-stu-id="72249-165">![Hover (far) with visual feedback](images/bounding-box-with-proximity-shader-hover-far.jpg)</span></span><br>
       <span data-ttu-id="72249-166">**Posizionamento del dito (da lontano)**</span><span class="sxs-lookup"><span data-stu-id="72249-166">**Hover (far)**</span></span><br>
       <span data-ttu-id="72249-167">Quando l'indice è all'interno della portata, sulla superficie del cubo di delimitazione viene messo in evidenza un punto luminoso per la punta del dito.</span><span class="sxs-lookup"><span data-stu-id="72249-167">When the index finger is within a range, a fingertip spotlight is cast on the surface of the bounding box.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="72249-168">![Avvicinamento del dito con feedback visivo](images/bounding-box-with-proximity-shader-hover-near.jpg)</span><span class="sxs-lookup"><span data-stu-id="72249-168">![Hover (near) with visual feedback](images/bounding-box-with-proximity-shader-hover-near.jpg)</span></span><br>
        <span data-ttu-id="72249-169">**Avvicinamento del dito**</span><span class="sxs-lookup"><span data-stu-id="72249-169">**Hover (near)**</span></span><br>
        <span data-ttu-id="72249-170">Man mano che la punta del dito si avvicina alla superficie, il punto luminoso si restringe.</span><span class="sxs-lookup"><span data-stu-id="72249-170">When the fingertip gets closer to the surface, the spotlight shrinks.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="72249-171">![Inizio contatto](images/bounding-box-with-proximity-shader-begin-contact.jpg)</span><span class="sxs-lookup"><span data-stu-id="72249-171">![Contact begins](images/bounding-box-with-proximity-shader-begin-contact.jpg)</span></span><br>
       <span data-ttu-id="72249-172">**Inizio contatto**</span><span class="sxs-lookup"><span data-stu-id="72249-172">**Contact begins**</span></span><br>
       <span data-ttu-id="72249-173">Non appena la punta del dito tocca la superficie, l'intero cubo di delimitazione cambia colore o genera un effetto visivo per riflettere lo stato di tocco.</span><span class="sxs-lookup"><span data-stu-id="72249-173">As soon as the fingertip touches the surface, the entire bounding box changes color or generates visual effects to reflect the touch state.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="72249-174">![Fine contatto](images/bounding-box-with-proximity-shader-end-contact.jpg)</span><span class="sxs-lookup"><span data-stu-id="72249-174">![Contact ends](images/bounding-box-with-proximity-shader-end-contact.jpg)</span></span><br>
       <span data-ttu-id="72249-175">**Fine contatto**</span><span class="sxs-lookup"><span data-stu-id="72249-175">**Contact ends**</span></span><br>
       <span data-ttu-id="72249-176">È anche possibile attivare un effetto sonoro per migliorare il feedback del tocco visivo.</span><span class="sxs-lookup"><span data-stu-id="72249-176">A sound effect can also be activated to enhance the visual touch feedback.</span></span>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="pressable-button"></a><span data-ttu-id="72249-177">Pulsante a pressione</span><span class="sxs-lookup"><span data-stu-id="72249-177">Pressable button</span></span>

<span data-ttu-id="72249-178">Dotati di punta del dito di collisione, gli utenti sono ora pronti per interagire con un componente dell'interfaccia utente olografica di base, ovvero il pulsante a pressione.</span><span class="sxs-lookup"><span data-stu-id="72249-178">With a collidable fingertip, users are now ready to interact with a fundamental holographic UI component, such as a pressable button.</span></span> <span data-ttu-id="72249-179">Un pulsante a pressione è un pulsante olografico personalizzato per la pressione diretta con un dito.</span><span class="sxs-lookup"><span data-stu-id="72249-179">A pressable button is a holographic button tailored for a direct finger press.</span></span> <span data-ttu-id="72249-180">Anche in questo caso, a causa della mancanza di feedback tattili, un pulsante a pressione è dotato di un paio di meccanismi per ovviare ai problemi correlati al feedback tattile.</span><span class="sxs-lookup"><span data-stu-id="72249-180">Again, because of the lack of tactile feedback, a pressable button equips a couple mechanisms to tackle tactile feedback-related issues.</span></span>

* <span data-ttu-id="72249-181">Il primo meccanismo è un cubo di delimitazione con shader prossimità, descritto in dettaglio nella sezione precedente.</span><span class="sxs-lookup"><span data-stu-id="72249-181">The first mechanism is a bounding box with a proximity shader, which is detailed in the previous section.</span></span> <span data-ttu-id="72249-182">Serve per fornire un'idea più accurata di prossimità quando gli utenti si avvicinano ed entrano in contatto con un pulsante.</span><span class="sxs-lookup"><span data-stu-id="72249-182">It gives users a better sense of proximity when they approach and make contact with a button.</span></span>
* <span data-ttu-id="72249-183">Il secondo meccanismo è la depressione.</span><span class="sxs-lookup"><span data-stu-id="72249-183">The second mechanism is depression.</span></span> <span data-ttu-id="72249-184">La depressione crea un senso di pressione dopo che la punta di un dito entra in contatto con un pulsante.</span><span class="sxs-lookup"><span data-stu-id="72249-184">Depression creates a sense of pressing down after a fingertip contacts a button.</span></span> <span data-ttu-id="72249-185">Il meccanismo funziona in modo che il pulsante si muova in stretta relazione con la pressione del dito lungo l'asse di profondità.</span><span class="sxs-lookup"><span data-stu-id="72249-185">The mechanism ensures that the button tightly moves with the fingertip along the depth axis.</span></span> <span data-ttu-id="72249-186">Il pulsante può essere attivato quando raggiunge una profondità scelta (alla pressione) o quando lascia la profondità (al rilascio) dopo averla attraversata.</span><span class="sxs-lookup"><span data-stu-id="72249-186">The button can be triggered when it reaches a chosen depth (on press) or leaves the depth (on release) after passing through it.</span></span>
* <span data-ttu-id="72249-187">È consigliabile aggiungere l'effetto audio di attivazione del pulsante per migliorare il feedback.</span><span class="sxs-lookup"><span data-stu-id="72249-187">The sound effect should be added to enhance feedback when the button is triggered.</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="72249-188">![Pulsante a pressione (lontano)](images/pressable-button-far.jpg)</span><span class="sxs-lookup"><span data-stu-id="72249-188">![pressable button far](images/pressable-button-far.jpg)</span></span><br>
       <span data-ttu-id="72249-189">**Il dito è lontano**</span><span class="sxs-lookup"><span data-stu-id="72249-189">**Finger is far away**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="72249-190">![Pulsante a pressione (vicino)](images/pressable-button-approach.jpg)</span><span class="sxs-lookup"><span data-stu-id="72249-190">![pressable button near](images/pressable-button-approach.jpg)</span></span><br>
        <span data-ttu-id="72249-191">**Il dito si avvicina**</span><span class="sxs-lookup"><span data-stu-id="72249-191">**Finger approaches**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="72249-192">![Inizio del contatto con il pulsante a pressione](images/pressable-button-contact.jpg)</span><span class="sxs-lookup"><span data-stu-id="72249-192">![pressable button contact begins](images/pressable-button-contact.jpg)</span></span><br>
       <span data-ttu-id="72249-193">**Inizio contatto**</span><span class="sxs-lookup"><span data-stu-id="72249-193">**Contact begins**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="72249-194">![Pressione del pulsante a pressione](images/pressable-button-press.jpg)</span><span class="sxs-lookup"><span data-stu-id="72249-194">![pressable button press](images/pressable-button-press.jpg)</span></span><br>
       <span data-ttu-id="72249-195">**Pressione in profondità**</span><span class="sxs-lookup"><span data-stu-id="72249-195">**Press down**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="2d-slate-interaction"></a><span data-ttu-id="72249-196">Interazione con uno slate 2D</span><span class="sxs-lookup"><span data-stu-id="72249-196">2D slate interaction</span></span>

<span data-ttu-id="72249-197">Uno [slate](slate.md) 2D è un contenitore olografico usato per ospitare contenuti di app 2D, ad esempio un Web browser.</span><span class="sxs-lookup"><span data-stu-id="72249-197">A 2D [slate](slate.md) is a holographic container used to host 2D app content, such as a web browser.</span></span> <span data-ttu-id="72249-198">Il concetto di progettazione per l'interazione con uno slate 2D tramite manipolazione diretta corrisponde all'interazione con un touchscreen fisico.</span><span class="sxs-lookup"><span data-stu-id="72249-198">The design concept for interacting with a 2D slate via direct manipulation is the same as interacting with a physical touch screen.</span></span>

### <a name="to-interact-with-the-slate-contact"></a><span data-ttu-id="72249-199">Per interagire con il contatto tramite slate</span><span class="sxs-lookup"><span data-stu-id="72249-199">To interact with the slate contact</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="72249-200">![Tocco](images/2d-slate-interaction-touch.jpg)</span><span class="sxs-lookup"><span data-stu-id="72249-200">![Touch](images/2d-slate-interaction-touch.jpg)</span></span><br>
       <span data-ttu-id="72249-201">**Tocco**</span><span class="sxs-lookup"><span data-stu-id="72249-201">**Touch**</span></span><br>
       <span data-ttu-id="72249-202">Usa un indice per premere un pulsante o un collegamento ipertestuale.</span><span class="sxs-lookup"><span data-stu-id="72249-202">Use an index finger to press a hyperlink or a button.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="72249-203">![Scorrimento](images/2d-slate-interaction-scroll2.jpg)</span><span class="sxs-lookup"><span data-stu-id="72249-203">![Scroll](images/2d-slate-interaction-scroll2.jpg)</span></span><br>
        <span data-ttu-id="72249-204">**Scorrimento**</span><span class="sxs-lookup"><span data-stu-id="72249-204">**Scroll**</span></span><br>
        <span data-ttu-id="72249-205">Usa un indice per scorrere il contenuto dello slate verso l'alto o verso il basso.</span><span class="sxs-lookup"><span data-stu-id="72249-205">Use an index finger to scroll a slate content up and down.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="72249-206">![Zoom](images/2d-slate-interaction-zoom2.jpg)</span><span class="sxs-lookup"><span data-stu-id="72249-206">![Zoom](images/2d-slate-interaction-zoom2.jpg)</span></span><br>
       <span data-ttu-id="72249-207">**Zoom**</span><span class="sxs-lookup"><span data-stu-id="72249-207">**Zoom**</span></span><br>
       <span data-ttu-id="72249-208">L'utente usa i due indici per eseguire lo zoom avanti e indietro del contenuto dello slate in base al movimento relativo delle dita.</span><span class="sxs-lookup"><span data-stu-id="72249-208">The user's two index fingers are used to zoom in and out of the slate content, according to the relative motion of the fingers.</span></span>
    :::column-end:::
:::row-end:::


### <a name="for-manipulating-the-2d-slate-itself"></a><span data-ttu-id="72249-209">Per manipolare lo slate 2D</span><span class="sxs-lookup"><span data-stu-id="72249-209">For manipulating the 2D slate itself</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="72249-210">![Immagine che mostra la funzionalità di cattura e trascinamento](images/manipulate-2d-slate-move.jpg)</span><span class="sxs-lookup"><span data-stu-id="72249-210">![Graphic showing grab and drag feature](images/manipulate-2d-slate-move.jpg)</span></span><br>
       <span data-ttu-id="72249-211">**Spostamento**</span><span class="sxs-lookup"><span data-stu-id="72249-211">**Move**</span></span><br>
       <span data-ttu-id="72249-212">Sposta le mani verso angoli e i bordi per rivelare gli inviti di manipolazione più vicini.</span><span class="sxs-lookup"><span data-stu-id="72249-212">Move your hands toward corners and edges to reveal the closest manipulation affordances.</span></span> <span data-ttu-id="72249-213">Afferra la barra dell'ologramma nella parte superiore dello slate 2D per spostare l'intero slate.</span><span class="sxs-lookup"><span data-stu-id="72249-213">Grab the Holobar at the top of the 2D slate, which lets you move the whole slate.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="72249-214">![Immagine che mostra la funzionalità di ridimensionamento](images/manipulate-2d-slate-scale.jpg)</span><span class="sxs-lookup"><span data-stu-id="72249-214">![Graphic showing scale feature](images/manipulate-2d-slate-scale.jpg)</span></span><br>
        <span data-ttu-id="72249-215">**Ridimensionamento**</span><span class="sxs-lookup"><span data-stu-id="72249-215">**Scale**</span></span><br>
        <span data-ttu-id="72249-216">Afferrare gli inviti di manipolazione ed eseguire un ridimensionamento uniforme tramite gli inviti degli angoli.</span><span class="sxs-lookup"><span data-stu-id="72249-216">Grab the manipulation affordances and do uniform scaling through the corner affordances.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="72249-217">![Adatta il contenuto in modo dinamico](images/manipulate-2d-slate-reflow.jpg)</span><span class="sxs-lookup"><span data-stu-id="72249-217">![Reflow](images/manipulate-2d-slate-reflow.jpg)</span></span><br>
       <span data-ttu-id="72249-218">**Adatta il contenuto in modo dinamico**</span><span class="sxs-lookup"><span data-stu-id="72249-218">**Reflow**</span></span><br>
       <span data-ttu-id="72249-219">Afferrare gli inviti di manipolazione e adattare il contenuto dinamicamente tramite gli inviti dei bordi.</span><span class="sxs-lookup"><span data-stu-id="72249-219">Grab the manipulation affordances and do reflow via the edge affordances.</span></span>
    :::column-end:::
:::row-end:::

<br>

---


## <a name="3d-object-manipulation"></a><span data-ttu-id="72249-220">Manipolazione di oggetti 3D</span><span class="sxs-lookup"><span data-stu-id="72249-220">3D object manipulation</span></span>

<span data-ttu-id="72249-221">HoloLens 2 consente agli utenti di usare le mani per indirizzare e manipolare gli oggetti olografici 3D applicando un cubo di delimitazione a ogni oggetto 3D.</span><span class="sxs-lookup"><span data-stu-id="72249-221">HoloLens 2 lets users enable their hands to direct and manipulate 3D holographic objects by applying a bounding box to each 3D object.</span></span> <span data-ttu-id="72249-222">Il cubo di delimitazione fornisce una migliore percezione della profondità tramite lo shader prossimità.</span><span class="sxs-lookup"><span data-stu-id="72249-222">The bounding box provides better depth perception through its proximity shader.</span></span> <span data-ttu-id="72249-223">Con il cubo di delimitazione sono disponibili due approcci di progettazione per la manipolazione di oggetti 3D.</span><span class="sxs-lookup"><span data-stu-id="72249-223">With the bounding box, there are two design approaches for 3D object manipulation.</span></span>

### <a name="affordance-based-manipulation"></a><span data-ttu-id="72249-224">Manipolazione basata sugli inviti</span><span class="sxs-lookup"><span data-stu-id="72249-224">Affordance-based manipulation</span></span>

<span data-ttu-id="72249-225">Permette di manipolare l'oggetto 3D tramite un cubo di delimitazione e gli inviti di manipolazione intorno a esso.</span><span class="sxs-lookup"><span data-stu-id="72249-225">Affordance-base manipulation lets you manipulate the 3D object through a bounding box along with the manipulation affordances around it.</span></span> 

:::row:::
    :::column:::
       <span data-ttu-id="72249-226">![Immagine che mostra il cubo di delimitazione di un oggetto e la funzionalità di spostamento](images/3d-object-manipulation-move.jpg)</span><span class="sxs-lookup"><span data-stu-id="72249-226">![Graphic showing an objects bounding box and move feature](images/3d-object-manipulation-move.jpg)</span></span><br>
       <span data-ttu-id="72249-227">**Spostamento**</span><span class="sxs-lookup"><span data-stu-id="72249-227">**Move**</span></span><br>
       <span data-ttu-id="72249-228">Nel momento in cui la mano di un utente è vicina a un oggetto 3D, diventano visibili il cubo di delimitazione e l'invito più vicino.</span><span class="sxs-lookup"><span data-stu-id="72249-228">As soon as a user's hand is close to a 3D object, the bounding box, and the nearest affordance are revealed.</span></span> <span data-ttu-id="72249-229">Gli utenti possono afferrare il cubo di delimitazione per spostare l'intero oggetto.</span><span class="sxs-lookup"><span data-stu-id="72249-229">Users can grab the bounding box to move the whole object.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="72249-230">![Immagine che mostra l'utente che afferra un bordo di un oggetto per eseguire la rotazione](images/3d-object-manipulation-rotate.jpg)</span><span class="sxs-lookup"><span data-stu-id="72249-230">![Graphic showing user grabbing an objects edge to rotate](images/3d-object-manipulation-rotate.jpg)</span></span><br>
        <span data-ttu-id="72249-231">**Rotazione**</span><span class="sxs-lookup"><span data-stu-id="72249-231">**Rotate**</span></span><br>
        <span data-ttu-id="72249-232">Gli utenti possono afferrare gli inviti dei bordi per eseguire la rotazione.</span><span class="sxs-lookup"><span data-stu-id="72249-232">Users can grab the edge affordances to rotate.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="72249-233">![Immagine che mostra l'utente che afferra un angolo di un oggetto per eseguire il ridimensionamento](images/3d-object-manipulation-scale.jpg)</span><span class="sxs-lookup"><span data-stu-id="72249-233">![Graphic showing user grabbing an objects corner to scale](images/3d-object-manipulation-scale.jpg)</span></span><br>
       <span data-ttu-id="72249-234">**Ridimensionamento**</span><span class="sxs-lookup"><span data-stu-id="72249-234">**Scale**</span></span><br>
       <span data-ttu-id="72249-235">Gli utenti possono afferrare gli inviti degli angoli per eseguire un ridimensionamento uniforme.</span><span class="sxs-lookup"><span data-stu-id="72249-235">Users can grab the corner affordances to scale uniformly.</span></span>
    :::column-end:::
:::row-end:::

<br>


### <a name="non-affordance-based-manipulation"></a><span data-ttu-id="72249-236">Manipolazione non basata sugli inviti</span><span class="sxs-lookup"><span data-stu-id="72249-236">Non-affordance-based manipulation</span></span>

<span data-ttu-id="72249-237">Con questo tipo di manipolazione, non è associato alcun invito al cubo di delimitazione.</span><span class="sxs-lookup"><span data-stu-id="72249-237">Non-affordance-based manipulation doesn't attach affordance to the bounding box.</span></span> <span data-ttu-id="72249-238">Gli utenti possono solo visualizzare il cubo di delimitazione e quindi interagire direttamente con esso.</span><span class="sxs-lookup"><span data-stu-id="72249-238">Users can only reveal the bounding box, then directly interact with it.</span></span> <span data-ttu-id="72249-239">Se il cubo di delimitazione viene afferrato con una mano, lo spostamento e la rotazione dell'oggetto sono associati al movimento e all'orientamento della mano.</span><span class="sxs-lookup"><span data-stu-id="72249-239">If the bounding box is grabbed with one hand, the translation and rotation of the object are associated to motion and orientation of the hand.</span></span> <span data-ttu-id="72249-240">Quando l'oggetto viene afferrato con due mani, gli utenti possono spostarlo, ridimensionarlo e ruotarlo in base al relativi movimenti delle mani.</span><span class="sxs-lookup"><span data-stu-id="72249-240">When the object is grabbed with two hands, users can translate, scale, and rotate it according to relative motions of two hands.</span></span>

<span data-ttu-id="72249-241">Una manipolazione specifica richiede precisione.</span><span class="sxs-lookup"><span data-stu-id="72249-241">Specific manipulation requires precision.</span></span> <span data-ttu-id="72249-242">È consigliabile usare la **manipolazione basata sugli inviti**, poiché offre un elevato livello di granularità.</span><span class="sxs-lookup"><span data-stu-id="72249-242">We recommend that you use **affordance-based manipulation** because it provides a high level of granularity.</span></span> <span data-ttu-id="72249-243">Per una manipolazione flessibile, è consigliabile usare la **manipolazione non basata sugli inviti**, perché trasmette esperienze immediate e divertenti.</span><span class="sxs-lookup"><span data-stu-id="72249-243">For flexible manipulation, we recommend you use **non-affordance manipulation** as it allows for instant and playful experiences.</span></span>

<br>

---


## <a name="instinctual-gestures"></a><span data-ttu-id="72249-244">Movimenti istintivi</span><span class="sxs-lookup"><span data-stu-id="72249-244">Instinctual gestures</span></span>

<span data-ttu-id="72249-245">Con HoloLens (prima generazione) sono stati insegnati agli utenti un paio di movimenti predefiniti, ad esempio l'apertura della mano a fiore e la simulazione del tocco.</span><span class="sxs-lookup"><span data-stu-id="72249-245">With HoloLens (1st gen), we taught users a couple of predefined gestures, such as bloom and air tap.</span></span> <span data-ttu-id="72249-246">Per HoloLens 2 non viene richiesto agli utenti di memorizzare movimenti simbolici.</span><span class="sxs-lookup"><span data-stu-id="72249-246">For HoloLens 2, we don't ask users to memorize any symbolic gestures.</span></span> <span data-ttu-id="72249-247">Tutti i movimenti richiesti agli utenti per interagire con ologrammi e contenuti sono istintivi.</span><span class="sxs-lookup"><span data-stu-id="72249-247">All required user gestures, where users need to interact with holograms and content, are instinctual.</span></span> <span data-ttu-id="72249-248">Per ottenere il movimento istintivo è sufficiente guidare gli utenti a eseguire gesti in base a come sono progettati gli inviti dell'interfaccia utente.</span><span class="sxs-lookup"><span data-stu-id="72249-248">The way to achieve instinctual gestures is to help users perform gestures through the design of UI affordances.</span></span>

<span data-ttu-id="72249-249">Se ad esempio un oggetto o un punto di controllo deve essere afferrato avvicinando due dita, l'oggetto o il punto di controllo deve essere piccolo.</span><span class="sxs-lookup"><span data-stu-id="72249-249">For example, if we encourage the user to grab an object or a control point with a two finger pinch, the object or the control point should be small.</span></span> <span data-ttu-id="72249-250">Se si vuole che l'utente afferri con cinque dita, l'oggetto o il punto di controllo deve essere relativamente grande.</span><span class="sxs-lookup"><span data-stu-id="72249-250">If we want the user to do a five finger grab, the object or the control point should be relatively large.</span></span> <span data-ttu-id="72249-251">Come avviene per i pulsanti, un pulsante piccolo consentirebbe agli utenti di eseguire la pressione con un solo dito.</span><span class="sxs-lookup"><span data-stu-id="72249-251">Similar to buttons, a tiny button would limit users to press it with a single finger.</span></span> <span data-ttu-id="72249-252">Un pulsante grande inviterebbe gli utenti a fare pressione con i palmi.</span><span class="sxs-lookup"><span data-stu-id="72249-252">A large button would encourage users to press it with their palms.</span></span>


:::row:::
    :::column:::
       <span data-ttu-id="72249-253">![Figura che mostra l'utente che afferra un oggetto piccolo per eseguire lo spostamento](images/instinctual-gestures-smallobject.jpg)</span><span class="sxs-lookup"><span data-stu-id="72249-253">![Graphic showing user grabbing small object to move](images/instinctual-gestures-smallobject.jpg)</span></span><br>
       <span data-ttu-id="72249-254">**Oggetto piccolo**</span><span class="sxs-lookup"><span data-stu-id="72249-254">**Small object**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="72249-255">![Figura che mostra l'utente che afferra un oggetto medio per eseguire lo spostamento](images/instinctual-gestures-mediumobject.jpg)</span><span class="sxs-lookup"><span data-stu-id="72249-255">![Graphic showing user grabbing medium object to move](images/instinctual-gestures-mediumobject.jpg)</span></span><br>
        <span data-ttu-id="72249-256">**Oggetto medio**</span><span class="sxs-lookup"><span data-stu-id="72249-256">**Medium object**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="72249-257">![Figura che mostra l'utente che afferra un oggetto grande per eseguire lo spostamento](images/instinctual-gestures-largeobject.jpg)</span><span class="sxs-lookup"><span data-stu-id="72249-257">![Graphic showing user grabbing large object to move](images/instinctual-gestures-largeobject.jpg)</span></span><br>
       <span data-ttu-id="72249-258">**Oggetto grande**</span><span class="sxs-lookup"><span data-stu-id="72249-258">**Large object**</span></span><br>
    :::column-end:::
:::row-end:::


<br>

---

<br>

## <a name="symmetric-design-between-hands-and-6-dof-controllers"></a><span data-ttu-id="72249-259">Progettazione simmetrica tra mani e controller 6DoF</span><span class="sxs-lookup"><span data-stu-id="72249-259">Symmetric design between hands and 6 DoF controllers</span></span>

<span data-ttu-id="72249-260">Avrai notato che sono presenti simmetrie di interazione che è possibile tracciare tra le mani nella realtà aumentata (AR) e i controller del movimento nella realtà virtuale (VR).</span><span class="sxs-lookup"><span data-stu-id="72249-260">You may have noticed that there are interaction parallels we can draw between hands in AR and motion controllers in VR.</span></span> <span data-ttu-id="72249-261">Entrambi gli input possono essere usati per avviare manipolazioni dirette nei rispettivi ambienti.</span><span class="sxs-lookup"><span data-stu-id="72249-261">Both inputs can be used to trigger direct manipulations in their respective environments.</span></span> <span data-ttu-id="72249-262">In HoloLens 2 afferrare e trascinare con le mani a una distanza ravvicinata funziona praticamente come il pulsante usato per afferrare nei controller del movimento in WMR.</span><span class="sxs-lookup"><span data-stu-id="72249-262">In HoloLens 2, grabbing and dragging with hands at a close distance works much the same way as the grab button does on WMR motion controllers.</span></span> <span data-ttu-id="72249-263">In questo modo si offre una familiarità di interazione tra le due piattaforme che può rivelarsi utile se in futuro si decidesse di convertire l'applicazione da una piattaforma all'altra.</span><span class="sxs-lookup"><span data-stu-id="72249-263">This provides users with interaction familiarity between the two platforms, which might prove useful if you ever decide to port your application between platforms.</span></span>

<br>

---

## <a name="optimize-with-eye-tracking"></a><span data-ttu-id="72249-264">Ottimizzare con il tracciamento oculare</span><span class="sxs-lookup"><span data-stu-id="72249-264">Optimize with eye tracking</span></span>

<span data-ttu-id="72249-265">La manipolazione diretta può essere fantastica se funziona come previsto.</span><span class="sxs-lookup"><span data-stu-id="72249-265">Direct manipulation can feel magical if it works as intended.</span></span> <span data-ttu-id="72249-266">Ma può anche diventare frustrante se non riesci a spostare la mano in una direzione qualunque senza attivare involontariamente un ologramma.</span><span class="sxs-lookup"><span data-stu-id="72249-266">But it can also become frustrating if you can’t move your hand anywhere without unintentionally triggering a hologram.</span></span> <span data-ttu-id="72249-267">Il tracciamento oculare aiuta a identificare meglio l'intenzione dell'utente.</span><span class="sxs-lookup"><span data-stu-id="72249-267">Eye tracking potentially helps to better identify what the user’s intent is.</span></span>

* <span data-ttu-id="72249-268">**Quando**: per ridurre l'attivazione involontaria di una risposta di manipolazione.</span><span class="sxs-lookup"><span data-stu-id="72249-268">**When**: Reduce unintentionally triggering a manipulation response.</span></span> <span data-ttu-id="72249-269">Il tracciamento oculare consente di comprendere meglio l'attività in cui è attualmente impegnato un utente.</span><span class="sxs-lookup"><span data-stu-id="72249-269">Eye tracking allows for better understanding what a user is currently engaged with.</span></span>
<span data-ttu-id="72249-270">Si supponga ad esempio di essere impegnati nella lettura di un testo olografico (istruzioni) e di sporgersi per afferrare uno strumento di lavoro del mondo reale.</span><span class="sxs-lookup"><span data-stu-id="72249-270">For example, imagine you're reading through a holographic (instructional) text when reaching over to grab you real-world work tool.</span></span>

<span data-ttu-id="72249-271">In questo modo si sposta accidentalmente la mano su alcuni pulsanti olografici interattivi non notati prima</span><span class="sxs-lookup"><span data-stu-id="72249-271">By doing so, you accidentally move your hand across some interactive holographic buttons that you hadn't even noticed before.</span></span> <span data-ttu-id="72249-272">(forse perché erano fuori del campo visivo).</span><span class="sxs-lookup"><span data-stu-id="72249-272">For example, it  may be outside the user's field-of-view (FoV).</span></span>

<span data-ttu-id="72249-273">Se l'utente non ha guardato un ologramma per un periodo di tempo ma è stato rilevato un evento di tocco o cattura, è probabile che l'interazione non sia intenzionale.</span><span class="sxs-lookup"><span data-stu-id="72249-273">If the user hasn't looked at a hologram for a while, yet a touch or grasp event has been detected for it, the interaction is likely unintentional.</span></span>

* <span data-ttu-id="72249-274">**Quale**:  oltre alla gestione delle attivazioni false positive, un altro esempio include una migliore identificazione degli ologrammi da afferrare o toccare dal momento che il punto di intersezione preciso potrebbe non essere chiaro dalla tua prospettiva, soprattutto in presenza di più ologrammi ravvicinati.</span><span class="sxs-lookup"><span data-stu-id="72249-274">**Which one**:  Aside from addressing false positive activations, another example includes better identifying which holograms to grab or poke as the precise intersection point may not be clear from your perspective, especially if several holograms are positioned close to each other.</span></span>

  <span data-ttu-id="72249-275">Anche se il tracciamento oculare in HoloLens 2 presenta limiti relativamente all'accuratezza di determinazione dello sguardo, questa funzionalità può comunque essere utile per le interazioni da vicino a causa della disparità di profondità durante l'interazione con l'input mano.</span><span class="sxs-lookup"><span data-stu-id="72249-275">While eye tracking on HoloLens 2 has limitations based on how accurately it can determine your eye gaze, this can still be helpful for near interactions because of depth disparity when interacting with hand input.</span></span> <span data-ttu-id="72249-276">Ciò significa che talvolta è difficile determinare se la mano si trova dietro o davanti a un ologramma, ad esempio per afferrare con precisione un widget di manipolazione.</span><span class="sxs-lookup"><span data-stu-id="72249-276">This means it's sometimes difficult to determine whether your hand is behind or in front of a hologram to precisely grab a manipulation widget, for example.</span></span>

* <span data-ttu-id="72249-277">**Dove**: usa le informazioni su ciò che l'utente sta guardando con movimenti di lancio rapido.</span><span class="sxs-lookup"><span data-stu-id="72249-277">**Where to**: Use information about what a user is looking at with quick-throwing gestures.</span></span> <span data-ttu-id="72249-278">Afferra un ologramma e scaglialo verso la destinazione prevista.</span><span class="sxs-lookup"><span data-stu-id="72249-278">Grab a hologram and roughly toss it toward your intended destination.</span></span>  

    <span data-ttu-id="72249-279">Anche se questa soluzione a volte funziona correttamente, l'esecuzione rapida di movimenti della mano può avere come risultato destinazioni estremamente imprecise.</span><span class="sxs-lookup"><span data-stu-id="72249-279">While this sometimes works, quickly doing hand gestures may result in highly inaccurate destinations.</span></span> <span data-ttu-id="72249-280">Il tracciamento oculare tuttavia può migliorare l'accuratezza del movimento.</span><span class="sxs-lookup"><span data-stu-id="72249-280">However, eye tracking could improve the accuracy of the gesture.</span></span>

<br>

---

## <a name="manipulation-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="72249-281">Manipolazione in MRTK (Mixed Reality Toolkit) per Unity</span><span class="sxs-lookup"><span data-stu-id="72249-281">Manipulation in MRTK (Mixed Reality Toolkit) for Unity</span></span>
<span data-ttu-id="72249-282">Con **[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** è possibile ottenere facilmente un comportamento di manipolazione comune usando lo script **ObjectManipulator**.</span><span class="sxs-lookup"><span data-stu-id="72249-282">With **[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)**, you can easily achieve common manipulation behavior using the script **ObjectManipulator**.</span></span> <span data-ttu-id="72249-283">ObjectManipulator consente di afferrare e spostare gli oggetti direttamente con le mani o con il raggio della mano.</span><span class="sxs-lookup"><span data-stu-id="72249-283">With ObjectManipulator, you can grab and move objects directly with hands or with hand ray.</span></span> <span data-ttu-id="72249-284">Supporta anche la manipolazione a due mani per il ridimensionamento e la rotazione di un oggetto.</span><span class="sxs-lookup"><span data-stu-id="72249-284">It also supports two-handed manipulation for scaling and rotating an object.</span></span>

* [<span data-ttu-id="72249-285">MRTK - Manipolazione</span><span class="sxs-lookup"><span data-stu-id="72249-285">MRTK - Manipulation</span></span>](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/object-manipulator)

---

## <a name="see-also"></a><span data-ttu-id="72249-286">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="72249-286">See also</span></span>

* [<span data-ttu-id="72249-287">Puntamento con la testa e commit</span><span class="sxs-lookup"><span data-stu-id="72249-287">Head-gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="72249-288">Puntamento e commit con le mani</span><span class="sxs-lookup"><span data-stu-id="72249-288">Point and commit with hands</span></span>](point-and-commit.md)
* [<span data-ttu-id="72249-289">Interazioni istintive</span><span class="sxs-lookup"><span data-stu-id="72249-289">Instinctual interactions</span></span>](interaction-fundamentals.md)
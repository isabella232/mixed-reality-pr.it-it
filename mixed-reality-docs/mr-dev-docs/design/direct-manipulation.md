---
title: Manipolazione diretta con le mani
description: Informazioni sulla manipolazione diretta, un modello di input in cui gli utenti toccano gli ologrammi direttamente con le mani.
author: caseymeekhof
ms.author: cmeekhof
ms.date: 04/02/2019
ms.topic: article
ms.localizationpriority: high
keywords: Realtà mista, Sguardo fisso, selezione della destinazione con lo sguardo, interazione, progettazione, a portata di mano, HoloLens, visore VR realtà mista, visore VR di windows mixed reality, visore per realtà virtuale, MRTK, Mixed Reality Toolkit, pulsante, collisori, cubo di delimitazione, 2D, movimenti istintivi
ms.openlocfilehash: 9d572064f1c7ba02d8e739d1b731fae61e95d2df
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143411"
---
# <a name="direct-manipulation-with-hands"></a><span data-ttu-id="d78a0-104">Manipolazione diretta con le mani</span><span class="sxs-lookup"><span data-stu-id="d78a0-104">Direct manipulation with hands</span></span>

![Pulsante](images/UX_Hero_Manipulation.jpg)

<span data-ttu-id="d78a0-106">La manipolazione diretta è un modello di input che consiste nel toccare gli ologrammi direttamente con le mani.</span><span class="sxs-lookup"><span data-stu-id="d78a0-106">Direct manipulation is an input model that involves touching holograms directly with your hands.</span></span> <span data-ttu-id="d78a0-107">L'idea alla base di questo concetto è che il comportamento degli oggetti deve essere uguale a quello che avrebbero nella realtà.</span><span class="sxs-lookup"><span data-stu-id="d78a0-107">The idea behind this concept is that objects behave just as they would in the real world.</span></span> <span data-ttu-id="d78a0-108">I pulsanti possono essere attivati semplicemente premendoli, gli oggetti possono essere selezionati afferrandoli e il contenuto 2D si comporta come un touchscreen virtuale.</span><span class="sxs-lookup"><span data-stu-id="d78a0-108">Buttons can be activated simply by pressing them, objects can be picked up by grabbing them, and 2D content behaves like a virtual touchscreen.</span></span> <span data-ttu-id="d78a0-109">La manipolazione diretta è basata sull'invito, ovvero è facile da usare.</span><span class="sxs-lookup"><span data-stu-id="d78a0-109">Direct manipulation is affordance-based, meaning it's user-friendly.</span></span> <span data-ttu-id="d78a0-110">Non esistono movimenti simbolici da insegnare agli utenti.</span><span class="sxs-lookup"><span data-stu-id="d78a0-110">There are no symbolic gestures to teach users.</span></span> <span data-ttu-id="d78a0-111">Tutte le interazioni avvengono intorno a un elemento visivo che è possibile toccare o afferrare.</span><span class="sxs-lookup"><span data-stu-id="d78a0-111">All interactions are built around a visual element that you can touch or grab.</span></span> <span data-ttu-id="d78a0-112">È considerata un modello di input "da vicino", in quanto è ideale per interagire con contenuto raggiungibile stendendo le braccia.</span><span class="sxs-lookup"><span data-stu-id="d78a0-112">It's considered a "near" input model in that it's best used for interacting with content within arms reach.</span></span>

## <a name="device-support"></a><span data-ttu-id="d78a0-113">Supporto di dispositivi</span><span class="sxs-lookup"><span data-stu-id="d78a0-113">Device support</span></span>

<table>
<colgroup>
    <col width="33%" />
    <col width="22%" />
    <col width="22%" />
    <col width="22%" />
</colgroup>
<tr>
     <td><span data-ttu-id="d78a0-114"><strong>Modello di input</strong></span><span class="sxs-lookup"><span data-stu-id="d78a0-114"><strong>Input model</strong></span></span></td>
     <td><span data-ttu-id="d78a0-115"><a href="/hololens/hololens1-hardware"><strong>HoloLens (prima generazione)</strong></a></span><span class="sxs-lookup"><span data-stu-id="d78a0-115"><a href="/hololens/hololens1-hardware"><strong>HoloLens (1st gen)</strong></a></span></span></td>
     <td><span data-ttu-id="d78a0-116"><a href="/hololens/hololens2-hardware"><strong>HoloLens 2</strong></a></span><span class="sxs-lookup"><span data-stu-id="d78a0-116"><a href="/hololens/hololens2-hardware"><strong>HoloLens 2</strong></a></span></span></td>
     <td><span data-ttu-id="d78a0-117"><a href="/windows/mixed-reality/immersive-headset-hardware-details"><strong>Visori VR immersive</strong></a></span><span class="sxs-lookup"><span data-stu-id="d78a0-117"><a href="/windows/mixed-reality/immersive-headset-hardware-details"><strong>Immersive headsets</strong></a></span></span></td>
</tr>
<tr>
     <td><span data-ttu-id="d78a0-118">Manipolazione diretta con le mani</span><span class="sxs-lookup"><span data-stu-id="d78a0-118">Direct manipulation with hands</span></span></td>
     <td><span data-ttu-id="d78a0-119">❌ Non supportata</span><span class="sxs-lookup"><span data-stu-id="d78a0-119">❌ Not supported</span></span></td>
     <td><span data-ttu-id="d78a0-120">✔️ Consigliata</span><span class="sxs-lookup"><span data-stu-id="d78a0-120">✔️ Recommended</span></span></td>
     <td><span data-ttu-id="d78a0-121">➕ Supportata.</span><span class="sxs-lookup"><span data-stu-id="d78a0-121">➕ Supported.</span></span>  <span data-ttu-id="d78a0-122">Per l'interfaccia utente, consigliamo invece <a href="point-and-commit.md">Puntamento e commit con le mani</a>.</span><span class="sxs-lookup"><span data-stu-id="d78a0-122">For UI, we recommend <a href="point-and-commit.md">point and commit with hands</a> instead.</span></span></td>
    
</tr>
</table>


<span data-ttu-id="d78a0-123">La manipolazione diretta è un modello di input principale in HoloLens 2 che usa il nuovo sistema di tracciamento delle mani articolato.</span><span class="sxs-lookup"><span data-stu-id="d78a0-123">Direct manipulation is a primary input model on HoloLens 2, which uses the new articulated hand-tracking system.</span></span> <span data-ttu-id="d78a0-124">Il modello di input è disponibile anche su visori VR immersive tramite l'uso di controller del movimento, ma non è consigliato come mezzo principale di interazione al di fuori della manipolazione di oggetti.</span><span class="sxs-lookup"><span data-stu-id="d78a0-124">The input model is also available on immersive headsets by using motion controllers, but isn't recommended as a primary means of interaction outside of object manipulation.</span></span> <span data-ttu-id="d78a0-125">La manipolazione diretta non è disponibile in HoloLens (prima generazione).</span><span class="sxs-lookup"><span data-stu-id="d78a0-125">Direct manipulation isn't available on HoloLens (1st gen).</span></span>

<br>

---

## <a name="basic-hand-tracking-and-instinctual-interactions-demo"></a><span data-ttu-id="d78a0-126">Demo di base sul tracciamento delle mani e sulle interazioni istintivi</span><span class="sxs-lookup"><span data-stu-id="d78a0-126">Basic hand tracking and instinctual interactions demo</span></span>

<span data-ttu-id="d78a0-127">Per vedere i concetti di progettazione della testa e del tracciamento oculare in azione, vedere la demo di video Progettazione di [ologrammi - Tracciamento]() testa e tracciamento oculare di seguito.</span><span class="sxs-lookup"><span data-stu-id="d78a0-127">If you'd like to see Head and Eye Tracking design concepts in action, check out our [Designing Holograms - Head Tracking and Eye Tracking]() video demo below.</span></span> <span data-ttu-id="d78a0-128">Al termine, continuare per un approfondimento più dettagliato su argomenti specifici.</span><span class="sxs-lookup"><span data-stu-id="d78a0-128">When you've finished, continue on for a more detailed dive into specific topics.</span></span>

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Microsofts-Designing-Holograms-Hand-Tracking-Chapter/player]

## <a name="collidable-fingertip"></a><span data-ttu-id="d78a0-129">Punta del dito di collisione</span><span class="sxs-lookup"><span data-stu-id="d78a0-129">Collidable fingertip</span></span>

<span data-ttu-id="d78a0-130">In HoloLens 2 le mani dell'utente vengono riconosciute e interpretate come modelli scheletrici delle mani sinistra e destra.</span><span class="sxs-lookup"><span data-stu-id="d78a0-130">On HoloLens 2, the user's hands are recognized and interpreted as left and right-hand skeletal models.</span></span> <span data-ttu-id="d78a0-131">Per implementare l'idea di toccare gli ologrammi direttamente con le mani, in teoria si potrebbero applicare cinque collisori alle cinque punte delle dita del modello scheletrico di ogni mano.</span><span class="sxs-lookup"><span data-stu-id="d78a0-131">To implement the idea of touching holograms directly with hands, ideally, five colliders could be attached to the five fingertips of each hand skeletal model.</span></span> <span data-ttu-id="d78a0-132">Tuttavia, a causa della mancanza di feedback tattili, 10 punte di dita di collisione possono causare collisioni inaspettate e imprevedibili con gli ologrammi.</span><span class="sxs-lookup"><span data-stu-id="d78a0-132">However, because of the lack of tactile feedback, 10 collidable fingertips can cause unexpected and unpredictable collisions with holograms.</span></span> 

<span data-ttu-id="d78a0-133">È consigliabile applicare solo un collisore a ogni dito indice.</span><span class="sxs-lookup"><span data-stu-id="d78a0-133">We suggest only putting a collider on each index finger.</span></span> <span data-ttu-id="d78a0-134">Le punte degli indici di collisione possono comunque fungere da punti tocco attivi per vari movimenti di tocco che coinvolgono altre dita.</span><span class="sxs-lookup"><span data-stu-id="d78a0-134">The collidable index fingertips can still serve as active touch points for diverse touch gestures involving other fingers.</span></span> <span data-ttu-id="d78a0-135">I movimenti di tocco includono la pressione con un dito, il tocco con un dito, la pressione con due dita e la pressione con cinque dita, come mostrato di seguito:</span><span class="sxs-lookup"><span data-stu-id="d78a0-135">Touch gestures include One-finger press, One-finger tap, Two-finger press, and Five-finger press, as shown below:</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="d78a0-136">![Punta del dito di collisione](images/Collidable-Fingertip.jpg)</span><span class="sxs-lookup"><span data-stu-id="d78a0-136">![collidable fingertip](images/Collidable-Fingertip.jpg)</span></span><br>
       <span data-ttu-id="d78a0-137">**Punta del dito di collisione**</span><span class="sxs-lookup"><span data-stu-id="d78a0-137">**Collidable fingertip**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="d78a0-138">![Pressione con un dito](images/Collidable-Fingertip-1-finger-press.jpg)</span><span class="sxs-lookup"><span data-stu-id="d78a0-138">![One-finger press](images/Collidable-Fingertip-1-finger-press.jpg)</span></span><br>
        <span data-ttu-id="d78a0-139">**Pressione con un dito**</span><span class="sxs-lookup"><span data-stu-id="d78a0-139">**One-finger press**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="d78a0-140">![Tocco con un dito](images/Collidable-Fingertip-1-finger-tap.jpg)</span><span class="sxs-lookup"><span data-stu-id="d78a0-140">![One-finger tap](images/Collidable-Fingertip-1-finger-tap.jpg)</span></span><br>
       <span data-ttu-id="d78a0-141">**Tocco con un dito**</span><span class="sxs-lookup"><span data-stu-id="d78a0-141">**One-finger tap**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="d78a0-142">![Pressione con cinque dita](images/Collidable-Fingertip-5-finger-press.jpg)</span><span class="sxs-lookup"><span data-stu-id="d78a0-142">![Five-finger press](images/Collidable-Fingertip-5-finger-press.jpg)</span></span><br>
       <span data-ttu-id="d78a0-143">**Pressione con cinque dita**</span><span class="sxs-lookup"><span data-stu-id="d78a0-143">**Five-finger press**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

### <a name="sphere-collider"></a><span data-ttu-id="d78a0-144">Collisore sfera</span><span class="sxs-lookup"><span data-stu-id="d78a0-144">Sphere collider</span></span>

<span data-ttu-id="d78a0-145">Invece di usare una forma generica casuale, è consigliabile usare un collisore sferico.</span><span class="sxs-lookup"><span data-stu-id="d78a0-145">Instead of using a random generic shape, we suggest you use a sphere collider.</span></span> <span data-ttu-id="d78a0-146">È possibile quindi eseguirne il rendering visivo per fornire segnali migliori per la destinazione più vicina.</span><span class="sxs-lookup"><span data-stu-id="d78a0-146">Then you can visually render it to provide better cues for near targeting.</span></span> <span data-ttu-id="d78a0-147">Il diametro della sfera deve corrispondere allo spessore del dito indice per aumentare l'accuratezza del tocco.</span><span class="sxs-lookup"><span data-stu-id="d78a0-147">The sphere's diameter should match the thickness of the index finger to increase touch accuracy.</span></span> <span data-ttu-id="d78a0-148">È più facile recuperare la variabile dello spessore di un dito chiamando l'API relativa alla mano.</span><span class="sxs-lookup"><span data-stu-id="d78a0-148">It's easier to retrieve the variable of finger thickness by calling the hand API.</span></span>

### <a name="fingertip-cursor"></a><span data-ttu-id="d78a0-149">Cursore punta del dito</span><span class="sxs-lookup"><span data-stu-id="d78a0-149">Fingertip cursor</span></span>

<span data-ttu-id="d78a0-150">Oltre al rendering di una sfera di collisione sulla punta dell'indice, è stato creato un cursore avanzato per la punta del dito per migliorare l'esperienza di selezione della destinazione da vicino.</span><span class="sxs-lookup"><span data-stu-id="d78a0-150">In addition to rendering a collidable sphere on the index fingertip, we've created an advanced fingertip cursor to achieve a better near-targeting experience.</span></span> <span data-ttu-id="d78a0-151">Si tratta di un cursore a forma di anello associato alla punta dell'indice.</span><span class="sxs-lookup"><span data-stu-id="d78a0-151">It's a donut-shaped cursor attached to the index fingertip.</span></span> <span data-ttu-id="d78a0-152">In base alla prossimità, reagisce in modo dinamico a una destinazione per l'orientamento e le dimensioni come indicato di seguito:</span><span class="sxs-lookup"><span data-stu-id="d78a0-152">According to proximity, it dynamically reacts to a target for orientation and size as detailed below:</span></span>

* <span data-ttu-id="d78a0-153">Quando un indice si sposta verso un ologramma, il cursore è sempre parallelo alla superficie dell'ologramma e si restringe gradualmente.</span><span class="sxs-lookup"><span data-stu-id="d78a0-153">When an index finger moves toward a hologram, the cursor is always parallel to the hologram's surface and gradually shrinks its size.</span></span>
* <span data-ttu-id="d78a0-154">Non appena il dito tocca la superficie, il cursore si riduce a un punto ed emette un evento tocco.</span><span class="sxs-lookup"><span data-stu-id="d78a0-154">As soon as the finger touches the surface, the cursor shrinks into a dot and emits a touch event.</span></span>

<span data-ttu-id="d78a0-155">Con il feedback interattivo, gli utenti possono eseguire attività di selezione della destinazione da vicino ad alta precisione, ad esempio l'attivazione di un collegamento ipertestuale o la pressione di un pulsante, come illustrato di seguito.</span><span class="sxs-lookup"><span data-stu-id="d78a0-155">With interactive feedback, users can achieve high precision near-targeting tasks, such as triggering a hyperlink or pressing a button as shown below.</span></span> 

:::row:::
    :::column:::
       <span data-ttu-id="d78a0-156">![Cursore punta del dito da lontano](images/Fingertip-cursor-far.jpg)</span><span class="sxs-lookup"><span data-stu-id="d78a0-156">![Fingertip cursor far](images/Fingertip-cursor-far.jpg)</span></span><br>
       <span data-ttu-id="d78a0-157">**Cursore punta del dito da lontano**</span><span class="sxs-lookup"><span data-stu-id="d78a0-157">**Fingertip cursor far**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="d78a0-158">![Cursore punta del dito da vicino](images/Fingertip-cursor-near.jpg)</span><span class="sxs-lookup"><span data-stu-id="d78a0-158">![Fingertip cursor near](images/Fingertip-cursor-near.jpg)</span></span><br>
        <span data-ttu-id="d78a0-159">**Cursore punta del dito da vicino**</span><span class="sxs-lookup"><span data-stu-id="d78a0-159">**Fingertip cursor near**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="d78a0-160">![Cursore punta del dito con contatto](images/Fingertip-cursor-contact.jpg)</span><span class="sxs-lookup"><span data-stu-id="d78a0-160">![Fingertip cursor contact](images/Fingertip-cursor-contact.jpg)</span></span><br>
       <span data-ttu-id="d78a0-161">**Cursore punta del dito con contatto**</span><span class="sxs-lookup"><span data-stu-id="d78a0-161">**Fingertip cursor contact**</span></span><br>
    :::column-end:::
:::row-end:::

<br>



## <a name="bounding-box-with-proximity-shader"></a><span data-ttu-id="d78a0-162">Cubo di delimitazione con shader prossimità</span><span class="sxs-lookup"><span data-stu-id="d78a0-162">Bounding box with proximity shader</span></span>

<span data-ttu-id="d78a0-163">L'ologramma stesso richiede anche la possibilità di fornire feedback audio e video per compensare la mancanza di feedback tattili.</span><span class="sxs-lookup"><span data-stu-id="d78a0-163">The hologram itself also requires the ability to provide both visual and audio feedback to compensate the lack of tactile feedback.</span></span> <span data-ttu-id="d78a0-164">Su questa esigenza si basa il concetto di cubo di delimitazione con shader prossimità.</span><span class="sxs-lookup"><span data-stu-id="d78a0-164">For that, we generate the concept of a bounding box with a proximity shader.</span></span> <span data-ttu-id="d78a0-165">Un cubo di delimitazione è un'area volumetrica minima che racchiude un oggetto 3D.</span><span class="sxs-lookup"><span data-stu-id="d78a0-165">A bounding box is a minimum volumetric area that encloses a 3D object.</span></span> <span data-ttu-id="d78a0-166">Il cubo di delimitazione è dotato di un meccanismo di rendering interattivo denominato shader prossimità.</span><span class="sxs-lookup"><span data-stu-id="d78a0-166">The bounding box has an interactive rendering mechanism called a proximity shader.</span></span> <span data-ttu-id="d78a0-167">Comportamento dello shader prossimità:</span><span class="sxs-lookup"><span data-stu-id="d78a0-167">The proximity shader behaves:</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="d78a0-168">![Posizionamento del dito (da lontano) con feedback visivo](images/bounding-box-with-proximity-shader-hover-far.jpg)</span><span class="sxs-lookup"><span data-stu-id="d78a0-168">![Hover (far) with visual feedback](images/bounding-box-with-proximity-shader-hover-far.jpg)</span></span><br>
       <span data-ttu-id="d78a0-169">**Posizionamento del dito (da lontano)**</span><span class="sxs-lookup"><span data-stu-id="d78a0-169">**Hover (far)**</span></span><br>
       <span data-ttu-id="d78a0-170">Quando l'indice è all'interno della portata, sulla superficie del cubo di delimitazione viene messo in evidenza un punto luminoso per la punta del dito.</span><span class="sxs-lookup"><span data-stu-id="d78a0-170">When the index finger is within a range, a fingertip spotlight is cast on the surface of the bounding box.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="d78a0-171">![Avvicinamento del dito con feedback visivo](images/bounding-box-with-proximity-shader-hover-near.jpg)</span><span class="sxs-lookup"><span data-stu-id="d78a0-171">![Hover (near) with visual feedback](images/bounding-box-with-proximity-shader-hover-near.jpg)</span></span><br>
        <span data-ttu-id="d78a0-172">**Avvicinamento del dito**</span><span class="sxs-lookup"><span data-stu-id="d78a0-172">**Hover (near)**</span></span><br>
        <span data-ttu-id="d78a0-173">Man mano che la punta del dito si avvicina alla superficie, il punto luminoso si restringe.</span><span class="sxs-lookup"><span data-stu-id="d78a0-173">When the fingertip gets closer to the surface, the spotlight shrinks.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="d78a0-174">![Inizio contatto](images/bounding-box-with-proximity-shader-begin-contact.jpg)</span><span class="sxs-lookup"><span data-stu-id="d78a0-174">![Contact begins](images/bounding-box-with-proximity-shader-begin-contact.jpg)</span></span><br>
       <span data-ttu-id="d78a0-175">**Inizio contatto**</span><span class="sxs-lookup"><span data-stu-id="d78a0-175">**Contact begins**</span></span><br>
       <span data-ttu-id="d78a0-176">Non appena la punta del dito tocca la superficie, l'intero cubo di delimitazione cambia colore o genera un effetto visivo per riflettere lo stato di tocco.</span><span class="sxs-lookup"><span data-stu-id="d78a0-176">As soon as the fingertip touches the surface, the entire bounding box changes color or generates visual effects to reflect the touch state.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="d78a0-177">![Fine contatto](images/bounding-box-with-proximity-shader-end-contact.jpg)</span><span class="sxs-lookup"><span data-stu-id="d78a0-177">![Contact ends](images/bounding-box-with-proximity-shader-end-contact.jpg)</span></span><br>
       <span data-ttu-id="d78a0-178">**Fine contatto**</span><span class="sxs-lookup"><span data-stu-id="d78a0-178">**Contact ends**</span></span><br>
       <span data-ttu-id="d78a0-179">È anche possibile attivare un effetto sonoro per migliorare il feedback del tocco visivo.</span><span class="sxs-lookup"><span data-stu-id="d78a0-179">A sound effect can also be activated to enhance the visual touch feedback.</span></span>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="pressable-button"></a><span data-ttu-id="d78a0-180">Pulsante a pressione</span><span class="sxs-lookup"><span data-stu-id="d78a0-180">Pressable button</span></span>

<span data-ttu-id="d78a0-181">Dotati di punta del dito di collisione, gli utenti sono ora pronti per interagire con un componente dell'interfaccia utente olografica di base, ovvero il pulsante a pressione.</span><span class="sxs-lookup"><span data-stu-id="d78a0-181">With a collidable fingertip, users are now ready to interact with a fundamental holographic UI component, such as a pressable button.</span></span> <span data-ttu-id="d78a0-182">Un pulsante a pressione è un pulsante olografico personalizzato per la pressione diretta con un dito.</span><span class="sxs-lookup"><span data-stu-id="d78a0-182">A pressable button is a holographic button tailored for a direct finger press.</span></span> <span data-ttu-id="d78a0-183">Anche in questo caso, a causa della mancanza di feedback tattili, un pulsante a pressione è dotato di un paio di meccanismi per ovviare ai problemi correlati al feedback tattile.</span><span class="sxs-lookup"><span data-stu-id="d78a0-183">Again, because of the lack of tactile feedback, a pressable button equips a couple mechanisms to tackle tactile feedback-related issues.</span></span>

* <span data-ttu-id="d78a0-184">Il primo meccanismo è un cubo di delimitazione con shader prossimità, descritto in dettaglio nella sezione precedente.</span><span class="sxs-lookup"><span data-stu-id="d78a0-184">The first mechanism is a bounding box with a proximity shader, which is detailed in the previous section.</span></span> <span data-ttu-id="d78a0-185">Serve per fornire un'idea più accurata di prossimità quando gli utenti si avvicinano ed entrano in contatto con un pulsante.</span><span class="sxs-lookup"><span data-stu-id="d78a0-185">It gives users a better sense of proximity when they approach and make contact with a button.</span></span>
* <span data-ttu-id="d78a0-186">Il secondo meccanismo è la depressione.</span><span class="sxs-lookup"><span data-stu-id="d78a0-186">The second mechanism is depression.</span></span> <span data-ttu-id="d78a0-187">La depressione crea un senso di pressione dopo che la punta di un dito entra in contatto con un pulsante.</span><span class="sxs-lookup"><span data-stu-id="d78a0-187">Depression creates a sense of pressing down after a fingertip contacts a button.</span></span> <span data-ttu-id="d78a0-188">Il meccanismo funziona in modo che il pulsante si muova in stretta relazione con la pressione del dito lungo l'asse di profondità.</span><span class="sxs-lookup"><span data-stu-id="d78a0-188">The mechanism ensures that the button tightly moves with the fingertip along the depth axis.</span></span> <span data-ttu-id="d78a0-189">Il pulsante può essere attivato quando raggiunge una profondità scelta (alla pressione) o quando lascia la profondità (al rilascio) dopo averla attraversata.</span><span class="sxs-lookup"><span data-stu-id="d78a0-189">The button can be triggered when it reaches a chosen depth (on press) or leaves the depth (on release) after passing through it.</span></span>
* <span data-ttu-id="d78a0-190">È consigliabile aggiungere l'effetto audio di attivazione del pulsante per migliorare il feedback.</span><span class="sxs-lookup"><span data-stu-id="d78a0-190">The sound effect should be added to enhance feedback when the button is triggered.</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="d78a0-191">![Pulsante a pressione (lontano)](images/pressable-button-far.jpg)</span><span class="sxs-lookup"><span data-stu-id="d78a0-191">![pressable button far](images/pressable-button-far.jpg)</span></span><br>
       <span data-ttu-id="d78a0-192">**Il dito è lontano**</span><span class="sxs-lookup"><span data-stu-id="d78a0-192">**Finger is far away**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="d78a0-193">![Pulsante a pressione (vicino)](images/pressable-button-approach.jpg)</span><span class="sxs-lookup"><span data-stu-id="d78a0-193">![pressable button near](images/pressable-button-approach.jpg)</span></span><br>
        <span data-ttu-id="d78a0-194">**Il dito si avvicina**</span><span class="sxs-lookup"><span data-stu-id="d78a0-194">**Finger approaches**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="d78a0-195">![Inizio del contatto con il pulsante a pressione](images/pressable-button-contact.jpg)</span><span class="sxs-lookup"><span data-stu-id="d78a0-195">![pressable button contact begins](images/pressable-button-contact.jpg)</span></span><br>
       <span data-ttu-id="d78a0-196">**Inizio contatto**</span><span class="sxs-lookup"><span data-stu-id="d78a0-196">**Contact begins**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="d78a0-197">![Pressione del pulsante a pressione](images/pressable-button-press.jpg)</span><span class="sxs-lookup"><span data-stu-id="d78a0-197">![pressable button press](images/pressable-button-press.jpg)</span></span><br>
       <span data-ttu-id="d78a0-198">**Pressione in profondità**</span><span class="sxs-lookup"><span data-stu-id="d78a0-198">**Press down**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="2d-slate-interaction"></a><span data-ttu-id="d78a0-199">Interazione con uno slate 2D</span><span class="sxs-lookup"><span data-stu-id="d78a0-199">2D slate interaction</span></span>

<span data-ttu-id="d78a0-200">Uno [slate](slate.md) 2D è un contenitore olografico usato per ospitare contenuti di app 2D, ad esempio un Web browser.</span><span class="sxs-lookup"><span data-stu-id="d78a0-200">A 2D [slate](slate.md) is a holographic container used to host 2D app content, such as a web browser.</span></span> <span data-ttu-id="d78a0-201">Il concetto di progettazione per l'interazione con uno slate 2D tramite manipolazione diretta corrisponde all'interazione con un touchscreen fisico.</span><span class="sxs-lookup"><span data-stu-id="d78a0-201">The design concept for interacting with a 2D slate via direct manipulation is the same as interacting with a physical touch screen.</span></span>

### <a name="to-interact-with-the-slate-contact"></a><span data-ttu-id="d78a0-202">Per interagire con il contatto tramite slate</span><span class="sxs-lookup"><span data-stu-id="d78a0-202">To interact with the slate contact</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="d78a0-203">![Tocco](images/2d-slate-interaction-touch.jpg)</span><span class="sxs-lookup"><span data-stu-id="d78a0-203">![Touch](images/2d-slate-interaction-touch.jpg)</span></span><br>
       <span data-ttu-id="d78a0-204">**Tocco**</span><span class="sxs-lookup"><span data-stu-id="d78a0-204">**Touch**</span></span><br>
       <span data-ttu-id="d78a0-205">Usa un indice per premere un pulsante o un collegamento ipertestuale.</span><span class="sxs-lookup"><span data-stu-id="d78a0-205">Use an index finger to press a hyperlink or a button.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="d78a0-206">![Scorrimento](images/2d-slate-interaction-scroll2.jpg)</span><span class="sxs-lookup"><span data-stu-id="d78a0-206">![Scroll](images/2d-slate-interaction-scroll2.jpg)</span></span><br>
        <span data-ttu-id="d78a0-207">**Scorrimento**</span><span class="sxs-lookup"><span data-stu-id="d78a0-207">**Scroll**</span></span><br>
        <span data-ttu-id="d78a0-208">Usa un indice per scorrere il contenuto dello slate verso l'alto o verso il basso.</span><span class="sxs-lookup"><span data-stu-id="d78a0-208">Use an index finger to scroll a slate content up and down.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="d78a0-209">![Zoom](images/2d-slate-interaction-zoom2.jpg)</span><span class="sxs-lookup"><span data-stu-id="d78a0-209">![Zoom](images/2d-slate-interaction-zoom2.jpg)</span></span><br>
       <span data-ttu-id="d78a0-210">**Zoom**</span><span class="sxs-lookup"><span data-stu-id="d78a0-210">**Zoom**</span></span><br>
       <span data-ttu-id="d78a0-211">L'utente usa i due indici per eseguire lo zoom avanti e indietro del contenuto dello slate in base al movimento relativo delle dita.</span><span class="sxs-lookup"><span data-stu-id="d78a0-211">The user's two index fingers are used to zoom in and out of the slate content, according to the relative motion of the fingers.</span></span>
    :::column-end:::
:::row-end:::


### <a name="for-manipulating-the-2d-slate-itself"></a><span data-ttu-id="d78a0-212">Per manipolare lo slate 2D</span><span class="sxs-lookup"><span data-stu-id="d78a0-212">For manipulating the 2D slate itself</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="d78a0-213">![Immagine che mostra la funzionalità di cattura e trascinamento](images/manipulate-2d-slate-move.jpg)</span><span class="sxs-lookup"><span data-stu-id="d78a0-213">![Graphic showing grab and drag feature](images/manipulate-2d-slate-move.jpg)</span></span><br>
       <span data-ttu-id="d78a0-214">**Spostamento**</span><span class="sxs-lookup"><span data-stu-id="d78a0-214">**Move**</span></span><br>
       <span data-ttu-id="d78a0-215">Sposta le mani verso angoli e i bordi per rivelare gli inviti di manipolazione più vicini.</span><span class="sxs-lookup"><span data-stu-id="d78a0-215">Move your hands toward corners and edges to reveal the closest manipulation affordances.</span></span> <span data-ttu-id="d78a0-216">Afferra la barra dell'ologramma nella parte superiore dello slate 2D per spostare l'intero slate.</span><span class="sxs-lookup"><span data-stu-id="d78a0-216">Grab the Holobar at the top of the 2D slate, which lets you move the whole slate.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="d78a0-217">![Immagine che mostra la funzionalità di ridimensionamento](images/manipulate-2d-slate-scale.jpg)</span><span class="sxs-lookup"><span data-stu-id="d78a0-217">![Graphic showing scale feature](images/manipulate-2d-slate-scale.jpg)</span></span><br>
        <span data-ttu-id="d78a0-218">**Ridimensionamento**</span><span class="sxs-lookup"><span data-stu-id="d78a0-218">**Scale**</span></span><br>
        <span data-ttu-id="d78a0-219">Afferrare gli inviti di manipolazione ed eseguire un ridimensionamento uniforme tramite gli inviti degli angoli.</span><span class="sxs-lookup"><span data-stu-id="d78a0-219">Grab the manipulation affordances and do uniform scaling through the corner affordances.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="d78a0-220">![Adatta il contenuto in modo dinamico](images/manipulate-2d-slate-reflow.jpg)</span><span class="sxs-lookup"><span data-stu-id="d78a0-220">![Reflow](images/manipulate-2d-slate-reflow.jpg)</span></span><br>
       <span data-ttu-id="d78a0-221">**Adatta il contenuto in modo dinamico**</span><span class="sxs-lookup"><span data-stu-id="d78a0-221">**Reflow**</span></span><br>
       <span data-ttu-id="d78a0-222">Afferrare gli inviti di manipolazione e adattare il contenuto dinamicamente tramite gli inviti dei bordi.</span><span class="sxs-lookup"><span data-stu-id="d78a0-222">Grab the manipulation affordances and do reflow via the edge affordances.</span></span>
    :::column-end:::
:::row-end:::

<br>

---


## <a name="3d-object-manipulation"></a><span data-ttu-id="d78a0-223">Manipolazione di oggetti 3D</span><span class="sxs-lookup"><span data-stu-id="d78a0-223">3D object manipulation</span></span>

<span data-ttu-id="d78a0-224">HoloLens 2 consente agli utenti di usare le mani per indirizzare e manipolare gli oggetti olografici 3D applicando un cubo di delimitazione a ogni oggetto 3D.</span><span class="sxs-lookup"><span data-stu-id="d78a0-224">HoloLens 2 lets users enable their hands to direct and manipulate 3D holographic objects by applying a bounding box to each 3D object.</span></span> <span data-ttu-id="d78a0-225">Il cubo di delimitazione fornisce una migliore percezione della profondità tramite lo shader prossimità.</span><span class="sxs-lookup"><span data-stu-id="d78a0-225">The bounding box provides better depth perception through its proximity shader.</span></span> <span data-ttu-id="d78a0-226">Con il cubo di delimitazione sono disponibili due approcci di progettazione per la manipolazione di oggetti 3D.</span><span class="sxs-lookup"><span data-stu-id="d78a0-226">With the bounding box, there are two design approaches for 3D object manipulation.</span></span>

### <a name="affordance-based-manipulation"></a><span data-ttu-id="d78a0-227">Manipolazione basata sugli inviti</span><span class="sxs-lookup"><span data-stu-id="d78a0-227">Affordance-based manipulation</span></span>

<span data-ttu-id="d78a0-228">Permette di manipolare l'oggetto 3D tramite un cubo di delimitazione e gli inviti di manipolazione intorno a esso.</span><span class="sxs-lookup"><span data-stu-id="d78a0-228">Affordance-base manipulation lets you manipulate the 3D object through a bounding box along with the manipulation affordances around it.</span></span> 

:::row:::
    :::column:::
       <span data-ttu-id="d78a0-229">![Immagine che mostra il cubo di delimitazione di un oggetto e la funzionalità di spostamento](images/3d-object-manipulation-move.jpg)</span><span class="sxs-lookup"><span data-stu-id="d78a0-229">![Graphic showing an objects bounding box and move feature](images/3d-object-manipulation-move.jpg)</span></span><br>
       <span data-ttu-id="d78a0-230">**Spostamento**</span><span class="sxs-lookup"><span data-stu-id="d78a0-230">**Move**</span></span><br>
       <span data-ttu-id="d78a0-231">Nel momento in cui la mano di un utente è vicina a un oggetto 3D, diventano visibili il cubo di delimitazione e l'invito più vicino.</span><span class="sxs-lookup"><span data-stu-id="d78a0-231">As soon as a user's hand is close to a 3D object, the bounding box, and the nearest affordance are revealed.</span></span> <span data-ttu-id="d78a0-232">Gli utenti possono afferrare il cubo di delimitazione per spostare l'intero oggetto.</span><span class="sxs-lookup"><span data-stu-id="d78a0-232">Users can grab the bounding box to move the whole object.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="d78a0-233">![Immagine che mostra l'utente che afferra un bordo di un oggetto per eseguire la rotazione](images/3d-object-manipulation-rotate.jpg)</span><span class="sxs-lookup"><span data-stu-id="d78a0-233">![Graphic showing user grabbing an objects edge to rotate](images/3d-object-manipulation-rotate.jpg)</span></span><br>
        <span data-ttu-id="d78a0-234">**Rotazione**</span><span class="sxs-lookup"><span data-stu-id="d78a0-234">**Rotate**</span></span><br>
        <span data-ttu-id="d78a0-235">Gli utenti possono afferrare gli inviti dei bordi per eseguire la rotazione.</span><span class="sxs-lookup"><span data-stu-id="d78a0-235">Users can grab the edge affordances to rotate.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="d78a0-236">![Immagine che mostra l'utente che afferra un angolo di un oggetto per eseguire il ridimensionamento](images/3d-object-manipulation-scale.jpg)</span><span class="sxs-lookup"><span data-stu-id="d78a0-236">![Graphic showing user grabbing an objects corner to scale](images/3d-object-manipulation-scale.jpg)</span></span><br>
       <span data-ttu-id="d78a0-237">**Ridimensionamento**</span><span class="sxs-lookup"><span data-stu-id="d78a0-237">**Scale**</span></span><br>
       <span data-ttu-id="d78a0-238">Gli utenti possono afferrare gli inviti degli angoli per eseguire un ridimensionamento uniforme.</span><span class="sxs-lookup"><span data-stu-id="d78a0-238">Users can grab the corner affordances to scale uniformly.</span></span>
    :::column-end:::
:::row-end:::

<br>


### <a name="non-affordance-based-manipulation"></a><span data-ttu-id="d78a0-239">Manipolazione non basata sugli inviti</span><span class="sxs-lookup"><span data-stu-id="d78a0-239">Non-affordance-based manipulation</span></span>

<span data-ttu-id="d78a0-240">Con questo tipo di manipolazione, non è associato alcun invito al cubo di delimitazione.</span><span class="sxs-lookup"><span data-stu-id="d78a0-240">Non-affordance-based manipulation doesn't attach affordance to the bounding box.</span></span> <span data-ttu-id="d78a0-241">Gli utenti possono solo visualizzare il cubo di delimitazione e quindi interagire direttamente con esso.</span><span class="sxs-lookup"><span data-stu-id="d78a0-241">Users can only reveal the bounding box, then directly interact with it.</span></span> <span data-ttu-id="d78a0-242">Se il cubo di delimitazione viene afferrato con una mano, lo spostamento e la rotazione dell'oggetto sono associati al movimento e all'orientamento della mano.</span><span class="sxs-lookup"><span data-stu-id="d78a0-242">If the bounding box is grabbed with one hand, the translation and rotation of the object are associated to motion and orientation of the hand.</span></span> <span data-ttu-id="d78a0-243">Quando l'oggetto viene afferrato con due mani, gli utenti possono spostarlo, ridimensionarlo e ruotarlo in base al relativi movimenti delle mani.</span><span class="sxs-lookup"><span data-stu-id="d78a0-243">When the object is grabbed with two hands, users can translate, scale, and rotate it according to relative motions of two hands.</span></span>

<span data-ttu-id="d78a0-244">Una manipolazione specifica richiede precisione.</span><span class="sxs-lookup"><span data-stu-id="d78a0-244">Specific manipulation requires precision.</span></span> <span data-ttu-id="d78a0-245">È consigliabile usare la **manipolazione basata sugli inviti**, poiché offre un elevato livello di granularità.</span><span class="sxs-lookup"><span data-stu-id="d78a0-245">We recommend that you use **affordance-based manipulation** because it provides a high level of granularity.</span></span> <span data-ttu-id="d78a0-246">Per una manipolazione flessibile, è consigliabile usare la **manipolazione non basata sugli inviti**, perché trasmette esperienze immediate e divertenti.</span><span class="sxs-lookup"><span data-stu-id="d78a0-246">For flexible manipulation, we recommend you use **non-affordance manipulation** as it allows for instant and playful experiences.</span></span>

<br>

---


## <a name="instinctual-gestures"></a><span data-ttu-id="d78a0-247">Movimenti istintivi</span><span class="sxs-lookup"><span data-stu-id="d78a0-247">Instinctual gestures</span></span>

<span data-ttu-id="d78a0-248">Con HoloLens (prima generazione) sono stati insegnati agli utenti un paio di movimenti predefiniti, ad esempio l'apertura della mano a fiore e la simulazione del tocco.</span><span class="sxs-lookup"><span data-stu-id="d78a0-248">With HoloLens (1st gen), we taught users a couple of predefined gestures, such as bloom and air tap.</span></span> <span data-ttu-id="d78a0-249">Per HoloLens 2 non viene richiesto agli utenti di memorizzare movimenti simbolici.</span><span class="sxs-lookup"><span data-stu-id="d78a0-249">For HoloLens 2, we don't ask users to memorize any symbolic gestures.</span></span> <span data-ttu-id="d78a0-250">Tutti i movimenti richiesti agli utenti per interagire con ologrammi e contenuti sono istintivi.</span><span class="sxs-lookup"><span data-stu-id="d78a0-250">All required user gestures, where users need to interact with holograms and content, are instinctual.</span></span> <span data-ttu-id="d78a0-251">Per ottenere il movimento istintivo è sufficiente guidare gli utenti a eseguire gesti in base a come sono progettati gli inviti dell'interfaccia utente.</span><span class="sxs-lookup"><span data-stu-id="d78a0-251">The way to achieve instinctual gestures is to help users perform gestures through the design of UI affordances.</span></span>

<span data-ttu-id="d78a0-252">Se ad esempio un oggetto o un punto di controllo deve essere afferrato avvicinando due dita, l'oggetto o il punto di controllo deve essere piccolo.</span><span class="sxs-lookup"><span data-stu-id="d78a0-252">For example, if we encourage the user to grab an object or a control point with a two finger pinch, the object or the control point should be small.</span></span> <span data-ttu-id="d78a0-253">Se si vuole che l'utente afferri con cinque dita, l'oggetto o il punto di controllo deve essere relativamente grande.</span><span class="sxs-lookup"><span data-stu-id="d78a0-253">If we want the user to do a five finger grab, the object or the control point should be relatively large.</span></span> <span data-ttu-id="d78a0-254">Come avviene per i pulsanti, un pulsante piccolo consentirebbe agli utenti di eseguire la pressione con un solo dito.</span><span class="sxs-lookup"><span data-stu-id="d78a0-254">Similar to buttons, a tiny button would limit users to press it with a single finger.</span></span> <span data-ttu-id="d78a0-255">Un pulsante grande inviterebbe gli utenti a fare pressione con i palmi.</span><span class="sxs-lookup"><span data-stu-id="d78a0-255">A large button would encourage users to press it with their palms.</span></span>


:::row:::
    :::column:::
       <span data-ttu-id="d78a0-256">![Figura che mostra l'utente che afferra un oggetto piccolo per eseguire lo spostamento](images/instinctual-gestures-smallobject.jpg)</span><span class="sxs-lookup"><span data-stu-id="d78a0-256">![Graphic showing user grabbing small object to move](images/instinctual-gestures-smallobject.jpg)</span></span><br>
       <span data-ttu-id="d78a0-257">**Oggetto piccolo**</span><span class="sxs-lookup"><span data-stu-id="d78a0-257">**Small object**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="d78a0-258">![Figura che mostra l'utente che afferra un oggetto medio per eseguire lo spostamento](images/instinctual-gestures-mediumobject.jpg)</span><span class="sxs-lookup"><span data-stu-id="d78a0-258">![Graphic showing user grabbing medium object to move](images/instinctual-gestures-mediumobject.jpg)</span></span><br>
        <span data-ttu-id="d78a0-259">**Oggetto medio**</span><span class="sxs-lookup"><span data-stu-id="d78a0-259">**Medium object**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="d78a0-260">![Figura che mostra l'utente che afferra un oggetto grande per eseguire lo spostamento](images/instinctual-gestures-largeobject.jpg)</span><span class="sxs-lookup"><span data-stu-id="d78a0-260">![Graphic showing user grabbing large object to move](images/instinctual-gestures-largeobject.jpg)</span></span><br>
       <span data-ttu-id="d78a0-261">**Oggetto grande**</span><span class="sxs-lookup"><span data-stu-id="d78a0-261">**Large object**</span></span><br>
    :::column-end:::
:::row-end:::


<br>

---

<br>

## <a name="symmetric-design-between-hands-and-6-dof-controllers"></a><span data-ttu-id="d78a0-262">Progettazione simmetrica tra mani e controller 6DoF</span><span class="sxs-lookup"><span data-stu-id="d78a0-262">Symmetric design between hands and 6 DoF controllers</span></span>

<span data-ttu-id="d78a0-263">Avrai notato che sono presenti simmetrie di interazione che è possibile tracciare tra le mani nella realtà aumentata (AR) e i controller del movimento nella realtà virtuale (VR).</span><span class="sxs-lookup"><span data-stu-id="d78a0-263">You may have noticed that there are interaction parallels we can draw between hands in AR and motion controllers in VR.</span></span> <span data-ttu-id="d78a0-264">Entrambi gli input possono essere usati per avviare manipolazioni dirette nei rispettivi ambienti.</span><span class="sxs-lookup"><span data-stu-id="d78a0-264">Both inputs can be used to trigger direct manipulations in their respective environments.</span></span> <span data-ttu-id="d78a0-265">In HoloLens 2 afferrare e trascinare con le mani a una distanza ravvicinata funziona praticamente come il pulsante usato per afferrare nei controller del movimento in WMR.</span><span class="sxs-lookup"><span data-stu-id="d78a0-265">In HoloLens 2, grabbing and dragging with hands at a close distance works much the same way as the grab button does on WMR motion controllers.</span></span> <span data-ttu-id="d78a0-266">In questo modo si offre una familiarità di interazione tra le due piattaforme che può rivelarsi utile se in futuro si decidesse di convertire l'applicazione da una piattaforma all'altra.</span><span class="sxs-lookup"><span data-stu-id="d78a0-266">This provides users with interaction familiarity between the two platforms, which might prove useful if you ever decide to port your application between platforms.</span></span>

<br>

---

## <a name="optimize-with-eye-tracking"></a><span data-ttu-id="d78a0-267">Ottimizzare con il tracciamento oculare</span><span class="sxs-lookup"><span data-stu-id="d78a0-267">Optimize with eye tracking</span></span>

<span data-ttu-id="d78a0-268">La manipolazione diretta può essere fantastica se funziona come previsto.</span><span class="sxs-lookup"><span data-stu-id="d78a0-268">Direct manipulation can feel magical if it works as intended.</span></span> <span data-ttu-id="d78a0-269">Ma può anche diventare frustrante se non riesci a spostare la mano in una direzione qualunque senza attivare involontariamente un ologramma.</span><span class="sxs-lookup"><span data-stu-id="d78a0-269">But it can also become frustrating if you can’t move your hand anywhere without unintentionally triggering a hologram.</span></span> <span data-ttu-id="d78a0-270">Il tracciamento oculare aiuta a identificare meglio l'intenzione dell'utente.</span><span class="sxs-lookup"><span data-stu-id="d78a0-270">Eye tracking potentially helps to better identify what the user’s intent is.</span></span>

* <span data-ttu-id="d78a0-271">**Quando**: per ridurre l'attivazione involontaria di una risposta di manipolazione.</span><span class="sxs-lookup"><span data-stu-id="d78a0-271">**When**: Reduce unintentionally triggering a manipulation response.</span></span> <span data-ttu-id="d78a0-272">Il tracciamento oculare consente di comprendere meglio l'attività in cui è attualmente impegnato un utente.</span><span class="sxs-lookup"><span data-stu-id="d78a0-272">Eye tracking allows for better understanding what a user is currently engaged with.</span></span>
<span data-ttu-id="d78a0-273">Si supponga ad esempio di essere impegnati nella lettura di un testo olografico (istruzioni) e di sporgersi per afferrare uno strumento di lavoro del mondo reale.</span><span class="sxs-lookup"><span data-stu-id="d78a0-273">For example, imagine you're reading through a holographic (instructional) text when reaching over to grab you real-world work tool.</span></span>

<span data-ttu-id="d78a0-274">In questo modo si sposta accidentalmente la mano su alcuni pulsanti olografici interattivi non notati prima</span><span class="sxs-lookup"><span data-stu-id="d78a0-274">By doing so, you accidentally move your hand across some interactive holographic buttons that you hadn't even noticed before.</span></span> <span data-ttu-id="d78a0-275">(forse perché erano fuori del campo visivo).</span><span class="sxs-lookup"><span data-stu-id="d78a0-275">For example, it  may be outside the user's field-of-view (FoV).</span></span>

<span data-ttu-id="d78a0-276">Se l'utente non ha guardato un ologramma per un periodo di tempo ma è stato rilevato un evento di tocco o cattura, è probabile che l'interazione non sia intenzionale.</span><span class="sxs-lookup"><span data-stu-id="d78a0-276">If the user hasn't looked at a hologram for a while, yet a touch or grasp event has been detected for it, the interaction is likely unintentional.</span></span>

* <span data-ttu-id="d78a0-277">**Quale**:  oltre alla gestione delle attivazioni false positive, un altro esempio include una migliore identificazione degli ologrammi da afferrare o toccare dal momento che il punto di intersezione preciso potrebbe non essere chiaro dalla tua prospettiva, soprattutto in presenza di più ologrammi ravvicinati.</span><span class="sxs-lookup"><span data-stu-id="d78a0-277">**Which one**:  Aside from addressing false positive activations, another example includes better identifying which holograms to grab or poke as the precise intersection point may not be clear from your perspective, especially if several holograms are positioned close to each other.</span></span>

  <span data-ttu-id="d78a0-278">Anche se il tracciamento oculare in HoloLens 2 presenta limiti relativamente all'accuratezza di determinazione dello sguardo, questa funzionalità può comunque essere utile per le interazioni da vicino a causa della disparità di profondità durante l'interazione con l'input mano.</span><span class="sxs-lookup"><span data-stu-id="d78a0-278">While eye tracking on HoloLens 2 has limitations based on how accurately it can determine your eye gaze, this can still be helpful for near interactions because of depth disparity when interacting with hand input.</span></span> <span data-ttu-id="d78a0-279">Ciò significa che talvolta è difficile determinare se la mano si trova dietro o davanti a un ologramma, ad esempio per afferrare con precisione un widget di manipolazione.</span><span class="sxs-lookup"><span data-stu-id="d78a0-279">This means it's sometimes difficult to determine whether your hand is behind or in front of a hologram to precisely grab a manipulation widget, for example.</span></span>

* <span data-ttu-id="d78a0-280">**Dove**: usa le informazioni su ciò che l'utente sta guardando con movimenti di lancio rapido.</span><span class="sxs-lookup"><span data-stu-id="d78a0-280">**Where to**: Use information about what a user is looking at with quick-throwing gestures.</span></span> <span data-ttu-id="d78a0-281">Afferra un ologramma e scaglialo verso la destinazione prevista.</span><span class="sxs-lookup"><span data-stu-id="d78a0-281">Grab a hologram and roughly toss it toward your intended destination.</span></span>  

    <span data-ttu-id="d78a0-282">Anche se questa soluzione a volte funziona correttamente, l'esecuzione rapida di movimenti della mano può avere come risultato destinazioni estremamente imprecise.</span><span class="sxs-lookup"><span data-stu-id="d78a0-282">While this sometimes works, quickly doing hand gestures may result in highly inaccurate destinations.</span></span> <span data-ttu-id="d78a0-283">Il tracciamento oculare tuttavia può migliorare l'accuratezza del movimento.</span><span class="sxs-lookup"><span data-stu-id="d78a0-283">However, eye tracking could improve the accuracy of the gesture.</span></span>

<br>

---

## <a name="manipulation-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="d78a0-284">Manipolazione in MRTK (Mixed Reality Toolkit) per Unity</span><span class="sxs-lookup"><span data-stu-id="d78a0-284">Manipulation in MRTK (Mixed Reality Toolkit) for Unity</span></span>
<span data-ttu-id="d78a0-285">Con **[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** è possibile ottenere facilmente un comportamento di manipolazione comune usando lo script **ObjectManipulator**.</span><span class="sxs-lookup"><span data-stu-id="d78a0-285">With **[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)**, you can easily achieve common manipulation behavior using the script **ObjectManipulator**.</span></span> <span data-ttu-id="d78a0-286">ObjectManipulator consente di afferrare e spostare gli oggetti direttamente con le mani o con il raggio della mano.</span><span class="sxs-lookup"><span data-stu-id="d78a0-286">With ObjectManipulator, you can grab and move objects directly with hands or with hand ray.</span></span> <span data-ttu-id="d78a0-287">Supporta anche la manipolazione a due mani per il ridimensionamento e la rotazione di un oggetto.</span><span class="sxs-lookup"><span data-stu-id="d78a0-287">It also supports two-handed manipulation for scaling and rotating an object.</span></span>

* [<span data-ttu-id="d78a0-288">MRTK - Manipolazione</span><span class="sxs-lookup"><span data-stu-id="d78a0-288">MRTK - Manipulation</span></span>](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/object-manipulator)

---

## <a name="see-also"></a><span data-ttu-id="d78a0-289">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="d78a0-289">See also</span></span>

* [<span data-ttu-id="d78a0-290">Puntamento con la testa e commit</span><span class="sxs-lookup"><span data-stu-id="d78a0-290">Head-gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="d78a0-291">Puntamento e commit con le mani</span><span class="sxs-lookup"><span data-stu-id="d78a0-291">Point and commit with hands</span></span>](point-and-commit.md)
* [<span data-ttu-id="d78a0-292">Interazioni istintive</span><span class="sxs-lookup"><span data-stu-id="d78a0-292">Instinctual interactions</span></span>](interaction-fundamentals.md)
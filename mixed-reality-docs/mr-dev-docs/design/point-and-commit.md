---
title: Puntamento e commit con le mani
description: Informazioni di base sul modello di input puntamento e commit per il supporto dei movimenti nelle applicazioni di realtà mista.
author: caseymeekhof
ms.author: cmeekhof
ms.date: 04/05/2019
ms.topic: article
ms.localizationpriority: high
keywords: Realtà mista, interazione, progettazione, HoloLens, mani, da lontano, puntamento e commit, visore VR realtà mista, visore VR di windows mixed reality, visore per realtà virtuale, HoloLens, raggi della mano, manipolazione degli oggetti, MRTK, Mixed Reality Toolkit, DoF
ms.openlocfilehash: 3351a38cad99089a60555ffe450447fc5c356fdc
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/20/2021
ms.locfileid: "98583206"
---
# <a name="point-and-commit-with-hands"></a><span data-ttu-id="cc488-104">Puntamento e commit con le mani</span><span class="sxs-lookup"><span data-stu-id="cc488-104">Point and commit with hands</span></span>

![Cursori](images/UX_Hero_HandRay.jpg)

<span data-ttu-id="cc488-106">Puntamento e commit con le mani è un modello di input che consente agli utenti di puntare come destinazione, selezionare e manipolare contenuto 2D e 3D fuori portata.</span><span class="sxs-lookup"><span data-stu-id="cc488-106">Point and commit with hands is an input model that lets users target, select, and manipulate out of reach 2D and 3D content.</span></span> <span data-ttu-id="cc488-107">Questa tecnica di interazione "da lontano" è specifica della realtà mista perché le persone interagiscono naturalmente con il mondo reale in modo diverso.</span><span class="sxs-lookup"><span data-stu-id="cc488-107">This "far" interaction technique is unique to mixed reality because humans don't naturally interact with the real world that way.</span></span> <span data-ttu-id="cc488-108">Ad esempio, nel film di supereroi *X-Men* il personaggio [Magneto](https://en.wikipedia.org/wiki/Magneto_(comics)) è in grado di manipolare oggetti lontani a distanza con le sue mani.</span><span class="sxs-lookup"><span data-stu-id="cc488-108">For example, in the super hero movie, *X-Men*, the character [Magneto](https://en.wikipedia.org/wiki/Magneto_(comics)) can manipulate far objects in the distance with his hands.</span></span> <span data-ttu-id="cc488-109">Questa non è un'azione che gli esseri umani possono compiere nella realtà.</span><span class="sxs-lookup"><span data-stu-id="cc488-109">This isn't something humans can do in reality.</span></span> <span data-ttu-id="cc488-110">Sia in HoloLens (AR) che in Mixed Reality (MR) gli utenti vengono dotati della magica capacità di superare le barriere fisiche imposte dal mondo reale.</span><span class="sxs-lookup"><span data-stu-id="cc488-110">In both HoloLens (AR) and Mixed Reality (MR), we equip users with this magical power to break the physical constraint of the real world.</span></span> <span data-ttu-id="cc488-111">Si tratta non solo di un'esperienza olografica divertente, ma anche di uno scenario che rende le interazioni utente più efficaci ed efficienti.</span><span class="sxs-lookup"><span data-stu-id="cc488-111">Not only is it a fun holographic experience, but it also makes user interactions more effective and efficient.</span></span>

## <a name="device-support"></a><span data-ttu-id="cc488-112">Supporto di dispositivi</span><span class="sxs-lookup"><span data-stu-id="cc488-112">Device support</span></span>

<table>
<colgroup>
    <col width="33%" />
    <col width="22%" />
    <col width="22%" />
    <col width="22%" />
</colgroup>
<tr>
     <td><span data-ttu-id="cc488-113"><strong>Modello di input</strong></span><span class="sxs-lookup"><span data-stu-id="cc488-113"><strong>Input model</strong></span></span></td>
     <td><span data-ttu-id="cc488-114"><a href="/hololens/hololens1-hardware"><strong>HoloLens (prima generazione)</strong></a></span><span class="sxs-lookup"><span data-stu-id="cc488-114"><a href="/hololens/hololens1-hardware"><strong>HoloLens (1st gen)</strong></a></span></span></td>
     <td><span data-ttu-id="cc488-115"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="cc488-115"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
     <td><span data-ttu-id="cc488-116"><a href="../discover/immersive-headset-hardware-details.md"><strong>Visori VR immersive</strong></a></span><span class="sxs-lookup"><span data-stu-id="cc488-116"><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
</tr>
<tr>
     <td><span data-ttu-id="cc488-117">Puntamento e commit con le mani</span><span class="sxs-lookup"><span data-stu-id="cc488-117">Point and commit with hands</span></span></td>
     <td><span data-ttu-id="cc488-118">❌ Non supportato</span><span class="sxs-lookup"><span data-stu-id="cc488-118">❌ Not supported</span></span></td>
     <td><span data-ttu-id="cc488-119">✔️ Consigliato</span><span class="sxs-lookup"><span data-stu-id="cc488-119">✔️ Recommended</span></span></td>
     <td><span data-ttu-id="cc488-120">✔️ Consigliato</span><span class="sxs-lookup"><span data-stu-id="cc488-120">✔️ Recommended</span></span></td>
</tr>
</table>


<span data-ttu-id="cc488-121">_"Puntamento e commit con le mani"_ è una delle nuove funzionalità che si avvale dell'innovativo e articolato sistema di tracciamento delle mani.</span><span class="sxs-lookup"><span data-stu-id="cc488-121">_"Point and commit with hands"_ is one of the new features that use the new articulated hand-tracking system.</span></span> <span data-ttu-id="cc488-122">Questo modello di input è anche quello principalmente usato nei visori VR immersive mediante controller del movimento.</span><span class="sxs-lookup"><span data-stu-id="cc488-122">This input model is also the primary input model on immersive headsets by using motion controllers.</span></span>

<br>

---

## <a name="hand-rays"></a><span data-ttu-id="cc488-123">Raggi mano</span><span class="sxs-lookup"><span data-stu-id="cc488-123">Hand rays</span></span>

<span data-ttu-id="cc488-124">In HoloLens 2 abbiamo creato un raggio della mano che viene lanciato dal centro del palmo della mano dell'utente.</span><span class="sxs-lookup"><span data-stu-id="cc488-124">On HoloLens 2, we created a hand ray that shoots out from the center of the user's palm.</span></span> <span data-ttu-id="cc488-125">Questo raggio viene considerato come un'estensione della mano.</span><span class="sxs-lookup"><span data-stu-id="cc488-125">This ray is treated as an extension of the hand.</span></span> <span data-ttu-id="cc488-126">All'estremità del raggio viene visualizzato un cursore ad anello che indica il punto in cui il raggio interseca un oggetto di destinazione.</span><span class="sxs-lookup"><span data-stu-id="cc488-126">A donut-shaped cursor is attached to the end of the ray to indicate the location where the ray intersects with a target object.</span></span> <span data-ttu-id="cc488-127">L'oggetto su cui si posa il cursore può quindi ricevere i comandi gestuali dalla mano.</span><span class="sxs-lookup"><span data-stu-id="cc488-127">The object that the cursor lands on can then receive gestural commands from the hand.</span></span>

<span data-ttu-id="cc488-128">Tale comando gestuale di base viene attivato usando il pollice e l'indice per eseguire l'azione di simulazione del tocco.</span><span class="sxs-lookup"><span data-stu-id="cc488-128">This basic gestural command is triggered by using the thumb and index finger to do the air-tap action.</span></span> <span data-ttu-id="cc488-129">Usando il raggio della mano per il puntamento e la simulazione del tocco per il commit, gli utenti possono attivare un pulsante o un collegamento ipertestuale.</span><span class="sxs-lookup"><span data-stu-id="cc488-129">By using the hand ray to point and air tap to commit, users can activate a button or a hyperlink.</span></span> <span data-ttu-id="cc488-130">Con movimenti più compositi, gli utenti possono spostarsi nel contenuto Web e manipolare oggetti 3D a distanza.</span><span class="sxs-lookup"><span data-stu-id="cc488-130">With more composite gestures, users can navigating web content and manipulating 3D objects from a distance.</span></span> <span data-ttu-id="cc488-131">La progettazione visiva del raggio mano dovrebbe anche reagire a questi stati di puntamento e commit come descritto e mostrato di seguito:</span><span class="sxs-lookup"><span data-stu-id="cc488-131">The visual design of the hand ray should also react to these point and commit states, as described and shown below:</span></span> 

:::row:::
    :::column:::
        <span data-ttu-id="cc488-132">![Puntamento con raggi della mano](images/hand-rays-pointing.jpg)</span><span class="sxs-lookup"><span data-stu-id="cc488-132">![hand rays pointing](images/hand-rays-pointing.jpg)</span></span><br>
        <span data-ttu-id="cc488-133">**Stato di puntamento**</span><span class="sxs-lookup"><span data-stu-id="cc488-133">**Pointing state**</span></span><br>
        <span data-ttu-id="cc488-134">Nello stato di *puntamento* il raggio è una linea tratteggiata e il cursore ha una forma ad anello.</span><span class="sxs-lookup"><span data-stu-id="cc488-134">In the *pointing* state, the ray is a dash line and the cursor is a donut shape.</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="cc488-135">![Commit con raggi della mano](images/hand-rays-commit.jpg)</span><span class="sxs-lookup"><span data-stu-id="cc488-135">![hand rays commit](images/hand-rays-commit.jpg)</span></span><br>
        <span data-ttu-id="cc488-136">**Stato di commit**</span><span class="sxs-lookup"><span data-stu-id="cc488-136">**Commit state**</span></span><br>
        <span data-ttu-id="cc488-137">Nello stato di *commit* il raggio diventa una linea continua e il cursore si rimpicciolisce diventando un punto.</span><span class="sxs-lookup"><span data-stu-id="cc488-137">In the *commit* state, the ray turns into a solid line and the cursor shrinks to a dot.</span></span>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="transition-between-near-and-far"></a><span data-ttu-id="cc488-138">Transizione dall'interazione da vicino all'interazione da lontano</span><span class="sxs-lookup"><span data-stu-id="cc488-138">Transition between near and far</span></span>

<span data-ttu-id="cc488-139">Invece di usare movimenti specifici come il "puntamento con il dito indice" per indirizzare il raggio, quest'ultimo è stato progettato in modo da uscire dal centro del palmo della mano degli utenti.</span><span class="sxs-lookup"><span data-stu-id="cc488-139">Instead of using specific gestures like "pointing with index finger" to direct the ray, we designed the ray to comout out from the center of the users' palm.</span></span> <span data-ttu-id="cc488-140">In questo modo, le cinque dita sono state lasciate libere per eseguire movimenti più finalizzati alla manipolazione, ad esempio l'avvicinamento delle dita e la cattura.</span><span class="sxs-lookup"><span data-stu-id="cc488-140">This way, we've released and reserved the Five Fingers for more manipulative gestures like pinch and grab.</span></span> <span data-ttu-id="cc488-141">Grazie a tale progettazione, viene creato un unico modello mentale che usa esattamente la stessa serie di movimenti della mano per l'interazione da vicino e da lontano.</span><span class="sxs-lookup"><span data-stu-id="cc488-141">With this design, we create only one mental model - the same set of hand gestures are used for both near and far interaction.</span></span> <span data-ttu-id="cc488-142">Puoi usare lo stesso movimento di cattura per manipolare oggetti a distanze diverse.</span><span class="sxs-lookup"><span data-stu-id="cc488-142">You can use the same grab gesture to manipulate objects at different distances.</span></span> <span data-ttu-id="cc488-143">I raggi vengono richiamati automaticamente in base alla prossimità, come indicato di seguito:</span><span class="sxs-lookup"><span data-stu-id="cc488-143">The invocation of the rays is automatic and proximity-based as follows:</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="cc488-144">![Manipolazione da vicino](images/transition-near-manipulation.jpg)</span><span class="sxs-lookup"><span data-stu-id="cc488-144">![Near manipulation](images/transition-near-manipulation.jpg)</span></span><br>
        <span data-ttu-id="cc488-145">**Manipolazione da vicino**</span><span class="sxs-lookup"><span data-stu-id="cc488-145">**Near manipulation**</span></span><br>
        <span data-ttu-id="cc488-146">Se un oggetto è a portata di braccio (a una distanza di circa 50 cm), i raggi vengono disattivati automaticamente, incoraggiando l'uso dell'interazione da vicino.</span><span class="sxs-lookup"><span data-stu-id="cc488-146">When an object is within arm's length (roughly 50 cm), the rays are turned off automatically, encouraging near interaction.</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="cc488-147">![Manipolazione da lontano](images/transition-far-manipulation.jpg)</span><span class="sxs-lookup"><span data-stu-id="cc488-147">![Far manipulation](images/transition-far-manipulation.jpg)</span></span><br>
        <span data-ttu-id="cc488-148">**Manipolazione da lontano**</span><span class="sxs-lookup"><span data-stu-id="cc488-148">**Far manipulation**</span></span><br>
        <span data-ttu-id="cc488-149">Se l'oggetto si trova a una distanza superiore a 50 cm, i raggi vengono attivati.</span><span class="sxs-lookup"><span data-stu-id="cc488-149">When the object is farther than 50 cm, the rays are turned on.</span></span> <span data-ttu-id="cc488-150">La transizione deve avvenire fluidamente e senza problemi.</span><span class="sxs-lookup"><span data-stu-id="cc488-150">The transition should be smooth and seamless.</span></span>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="2d-slate-interaction"></a><span data-ttu-id="cc488-151">Interazione con uno slate 2D</span><span class="sxs-lookup"><span data-stu-id="cc488-151">2D slate interaction</span></span>

<span data-ttu-id="cc488-152">Uno slate 2D è un contenitore olografico che ospita contenuti di app 2D, ad esempio un Web browser.</span><span class="sxs-lookup"><span data-stu-id="cc488-152">A 2D slate is a holographic container hosting 2D app contents, such as a web browser.</span></span> <span data-ttu-id="cc488-153">Il concetto di progettazione per l'interazione da lontano con uno slate 2D prevede l'uso dei raggi mano per puntare una destinazione e della simulazione del tocco per effettuare la selezione.</span><span class="sxs-lookup"><span data-stu-id="cc488-153">The design concept for far interacting with a 2D slate is to use hand rays to target and air tap to select.</span></span> <span data-ttu-id="cc488-154">Dopo aver individuato la destinazione con un raggio mano, gli utenti possono simulare il tocco per attivare un collegamento ipertestuale o un pulsante.</span><span class="sxs-lookup"><span data-stu-id="cc488-154">After targeting with a hand ray, users can air tap to trigger a hyperlink or a button.</span></span> <span data-ttu-id="cc488-155">Possono usare una mano per "simulare il tocco e trascinare" in modo da scorrere verso l'alto e verso il basso il contenuto dello slate.</span><span class="sxs-lookup"><span data-stu-id="cc488-155">They can use one hand to "air tap and drag" to scroll slate content up and down.</span></span> <span data-ttu-id="cc488-156">Il movimento relativo associato all'uso di due mani per simulare il tocco e trascinare può causare lo zoom avanti e lo zoom indietro sul contenuto dello slate.</span><span class="sxs-lookup"><span data-stu-id="cc488-156">The relative motion of using two hands to air tap and drag can zoom in and out the slate content.</span></span>

<span data-ttu-id="cc488-157">Puntando il raggio mano sugli angoli e sui bordi, è possibile vedere l'invito di manipolazione più vicino.</span><span class="sxs-lookup"><span data-stu-id="cc488-157">Targeting the hand ray at the corners and edges reveals the closest manipulation affordance.</span></span> <span data-ttu-id="cc488-158">"Afferrando e trascinando" gli inviti di manipolazione, gli utenti possono eseguire un ridimensionamento uniforme tramite gli inviti degli angoli, nonché adattare automaticamente il contenuto dello slate tramite gli inviti dei bordi.</span><span class="sxs-lookup"><span data-stu-id="cc488-158">By "grab and drag" manipulation affordances, users can do uniform scaling through the corner affordances, and can reflow the slate via the edge affordances.</span></span> <span data-ttu-id="cc488-159">Afferrando e trascinando la barra dell'ologramma nella parte superiore dello slate 2D, gli utenti possono spostare l'intero slate.</span><span class="sxs-lookup"><span data-stu-id="cc488-159">Grabbing and dragging the holobar at the top of the 2D slate lets users move the entire slate.</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="cc488-160">![Interazione con uno slate 2D - clic](images/2d-slate-interaction-click.jpg)</span><span class="sxs-lookup"><span data-stu-id="cc488-160">![2d slate interaction click](images/2d-slate-interaction-click.jpg)</span></span><br>
       <span data-ttu-id="cc488-161">**Clic**</span><span class="sxs-lookup"><span data-stu-id="cc488-161">**Click**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="cc488-162">![Interazione con uno slate 2D - scorrimento](images/2d-slate-interaction-scroll.jpg)</span><span class="sxs-lookup"><span data-stu-id="cc488-162">![2d slate interaction scroll](images/2d-slate-interaction-scroll.jpg)</span></span><br>
        <span data-ttu-id="cc488-163">**Scorrimento**</span><span class="sxs-lookup"><span data-stu-id="cc488-163">**Scroll**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="cc488-164">![Interazione con uno slate 2D - zoom](images/2d-slate-interaction-zoom.jpg)</span><span class="sxs-lookup"><span data-stu-id="cc488-164">![2d slate interaction zoom](images/2d-slate-interaction-zoom.jpg)</span></span><br>
       <span data-ttu-id="cc488-165">**Zoom**</span><span class="sxs-lookup"><span data-stu-id="cc488-165">**Zoom**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

<span data-ttu-id="cc488-166">**Per la manipolazione dello slate 2D**</span><span class="sxs-lookup"><span data-stu-id="cc488-166">**For manipulating the 2D slate**</span></span><br>

* <span data-ttu-id="cc488-167">Gli utenti puntano il raggio mano sugli angoli o sui bordi per vedere l'invito di manipolazione più vicino.</span><span class="sxs-lookup"><span data-stu-id="cc488-167">Users point the hand ray at the corners or edges to reveal the closest manipulation affordance.</span></span> 
* <span data-ttu-id="cc488-168">Applicando un movimento di manipolazione all'invito, gli utenti possono eseguire un ridimensionamento uniforme tramite l'invito degli angoli, nonché adattare automaticamente il contenuto dello slate mediante l'invito dei bordi.</span><span class="sxs-lookup"><span data-stu-id="cc488-168">By applying a manipulation gesture on the affordance, users can do uniform scaling through the corner affordance, and can reflow the slate via the edge affordance.</span></span> 
* <span data-ttu-id="cc488-169">Applicando un movimento di manipolazione alla barra dell'ologramma nella parte superiore dello slate 2D, gli utenti possono spostare l'intero slate.</span><span class="sxs-lookup"><span data-stu-id="cc488-169">By applying a manipulation gesture on the holobar at the top of the 2D slate, users can move the entire slate.</span></span><br>

<br>

---

## <a name="3d-object-manipulation"></a><span data-ttu-id="cc488-170">Manipolazione di oggetti 3D</span><span class="sxs-lookup"><span data-stu-id="cc488-170">3D object manipulation</span></span>

<span data-ttu-id="cc488-171">Nella manipolazione diretta gli utenti possono manipolare gli oggetti 3D in due modi, ovvero con manipolazione basata sugli inviti e non basata sugli inviti.</span><span class="sxs-lookup"><span data-stu-id="cc488-171">In direct manipulation, there are two ways for users to manipulate 3D objects: affordance-based manipulation and non-affordance based manipulation.</span></span> <span data-ttu-id="cc488-172">Nel modello puntamento e commit gli utenti possono eseguire esattamente le stesse attività mediante i raggi delle mani.</span><span class="sxs-lookup"><span data-stu-id="cc488-172">In the point and commit model, users can achieve exactly the same tasks through the hand rays.</span></span> <span data-ttu-id="cc488-173">Non è necessario apprendere altre modalità.</span><span class="sxs-lookup"><span data-stu-id="cc488-173">No extra learning is needed.</span></span><br>

### <a name="affordance-based-manipulation"></a><span data-ttu-id="cc488-174">Manipolazione basata sugli inviti</span><span class="sxs-lookup"><span data-stu-id="cc488-174">Affordance-based manipulation</span></span>

<span data-ttu-id="cc488-175">Gli utenti usano i raggi mano per puntare e vedere il cubo di delimitazione e gli inviti di manipolazione.</span><span class="sxs-lookup"><span data-stu-id="cc488-175">Users use hand rays to point and reveal the bounding box and manipulation affordances.</span></span> <span data-ttu-id="cc488-176">Gli utenti possono applicare il movimento di manipolazione al cubo di delimitazione per spostare l'intero oggetto, agli inviti dei bordi per ruotare e agli inviti degli angoli per ridimensionare in modo uniforme.</span><span class="sxs-lookup"><span data-stu-id="cc488-176">Users can apply the manipulation gesture on the bounding box to move the whole object, on the edge affordances to rotate, and on the corner affordances to scale uniformly.</span></span> <br>

:::row:::
    :::column:::
       <span data-ttu-id="cc488-177">![Manipolazione di un oggetto 3D - spostamento da lontano](images/3d-object-manipulation-far-move.jpg)</span><span class="sxs-lookup"><span data-stu-id="cc488-177">![3d object manipulation far move](images/3d-object-manipulation-far-move.jpg)</span></span><br>
       <span data-ttu-id="cc488-178">**Sposta**</span><span class="sxs-lookup"><span data-stu-id="cc488-178">**Move**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="cc488-179">![Manipolazione di un oggetto 3D - rotazione da lontano](images/3d-object-manipulation-far-rotate.jpg)</span><span class="sxs-lookup"><span data-stu-id="cc488-179">![3d object manipulation far rotate](images/3d-object-manipulation-far-rotate.jpg)</span></span><br>
        <span data-ttu-id="cc488-180">**Ruota**</span><span class="sxs-lookup"><span data-stu-id="cc488-180">**Rotate**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="cc488-181">![Manipolazione di un oggetto 3D - ridimensionamento da lontano](images/3d-object-manipulation-far-scale.jpg)</span><span class="sxs-lookup"><span data-stu-id="cc488-181">![3d object manipulation far scale](images/3d-object-manipulation-far-scale.jpg)</span></span><br>
       <span data-ttu-id="cc488-182">**Ridimensiona**</span><span class="sxs-lookup"><span data-stu-id="cc488-182">**Scale**</span></span><br>
    :::column-end:::
:::row-end:::

### <a name="non-affordance-based-manipulation"></a><span data-ttu-id="cc488-183">Manipolazione non basata sugli inviti</span><span class="sxs-lookup"><span data-stu-id="cc488-183">Non-affordance-based manipulation</span></span>

<span data-ttu-id="cc488-184">Gli utenti puntano con i raggi mano per vedere il cubo di delimitazione e quindi vi applicano direttamente i movimenti di manipolazione.</span><span class="sxs-lookup"><span data-stu-id="cc488-184">Users point with hand rays to reveal the bounding box then directly apply manipulation gestures on it.</span></span> <span data-ttu-id="cc488-185">Con una mano, la traslazione e la rotazione dell'oggetto sono associati al movimento e all'orientamento della mano.</span><span class="sxs-lookup"><span data-stu-id="cc488-185">With one hand, the translation and rotation of the object are associated to motion and orientation of the hand.</span></span> <span data-ttu-id="cc488-186">Con due mani, gli utenti possono spostarlo, ridimensionarlo e ruotarlo in base ai movimenti relativi delle mani.</span><span class="sxs-lookup"><span data-stu-id="cc488-186">With two hands, users can translate, scale, and rotate it according to relative motions of two hands.</span></span><br>

<br>

---

## <a name="instinctual-gestures"></a><span data-ttu-id="cc488-187">Movimenti istintivi</span><span class="sxs-lookup"><span data-stu-id="cc488-187">Instinctual gestures</span></span>

<span data-ttu-id="cc488-188">Il concetto di movimenti istintivi per puntamento e commit è analogo a quello per la [manipolazione diretta con le mani](direct-manipulation.md).</span><span class="sxs-lookup"><span data-stu-id="cc488-188">The concept of instinctual gestures for point and commit is similar to that for [direct manipulation with hands](direct-manipulation.md).</span></span> <span data-ttu-id="cc488-189">I movimenti che gli utenti eseguono su un oggetto 3D dipendono dalla progettazione degli inviti dell'interfaccia utente.</span><span class="sxs-lookup"><span data-stu-id="cc488-189">The gestures users do on a 3D object are guided by the design of UI affordances.</span></span> <span data-ttu-id="cc488-190">Ad esempio, in presenza di un punto di controllo di piccole dimensioni gli utenti sono portati a usare il pollice e l'indice (ovvero ad avvicinare le dita), mentre davanti a un oggetto più grande possono decidere di afferrarlo usando tutte e cinque le dita.</span><span class="sxs-lookup"><span data-stu-id="cc488-190">For example, a small control point might motivate users to pinch with their thumb and index finger, while a user might want to use all Five Fingers to grab a larger object.</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="cc488-191">![Movimenti istintivi per un oggetto piccolo](images/instinctual-gestures-far-smallobject.jpg)</span><span class="sxs-lookup"><span data-stu-id="cc488-191">![instinctual gestures far small object](images/instinctual-gestures-far-smallobject.jpg)</span></span><br>
       <span data-ttu-id="cc488-192">**Oggetto piccolo**</span><span class="sxs-lookup"><span data-stu-id="cc488-192">**Small object**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="cc488-193">![Movimenti istintivi per un oggetto medio](images/instinctual-gestures-far-mediumobject.jpg)</span><span class="sxs-lookup"><span data-stu-id="cc488-193">![instinctual gestures far medium object](images/instinctual-gestures-far-mediumobject.jpg)</span></span><br>
        <span data-ttu-id="cc488-194">**Oggetto medio**</span><span class="sxs-lookup"><span data-stu-id="cc488-194">**Medium object**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="cc488-195">![Movimenti istintivi per un oggetto grande](images/instinctual-gestures-far-largeobject.jpg)</span><span class="sxs-lookup"><span data-stu-id="cc488-195">![instinctual gestures far large object](images/instinctual-gestures-far-largeobject.jpg)</span></span><br>
       <span data-ttu-id="cc488-196">**Oggetto grande**</span><span class="sxs-lookup"><span data-stu-id="cc488-196">**Large object**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="symmetric-design-between-hands-and-6-dof-controller"></a><span data-ttu-id="cc488-197">Progettazione simmetrica tra le due mani e controller 6DoF</span><span class="sxs-lookup"><span data-stu-id="cc488-197">Symmetric design between hands and 6 DoF controller</span></span> 

<span data-ttu-id="cc488-198">Il concetto di puntamento e commit per l'interazione da lontano è stato creato e definito per il Portale realtà mista (MRP).</span><span class="sxs-lookup"><span data-stu-id="cc488-198">The concept of point and commit for far interaction was created and defined for the Mixed Reality Portal (MRP).</span></span> <span data-ttu-id="cc488-199">In questo scenario l'utente usa un visore VR immersive e interagisce con gli oggetti 3D tramite controller del movimento.</span><span class="sxs-lookup"><span data-stu-id="cc488-199">In this scenario, a user wears an immersive headset and interacts with 3D objects via motion controllers.</span></span> <span data-ttu-id="cc488-200">Tali controller emettono raggi per il puntamento e la manipolazione degli oggetti lontani.</span><span class="sxs-lookup"><span data-stu-id="cc488-200">The motion controllers shoot out rays for pointing and manipulating far objects.</span></span> <span data-ttu-id="cc488-201">Sui controller sono presenti pulsanti che consentono di eseguire ulteriormente il commit di azioni diverse.</span><span class="sxs-lookup"><span data-stu-id="cc488-201">There are buttons on the controllers for further committing different actions.</span></span> <span data-ttu-id="cc488-202">Viene applicato il modello di interazione dei raggi, che vengono collegati a entrambe le mani.</span><span class="sxs-lookup"><span data-stu-id="cc488-202">We apply the interaction model of rays and attached them to both hands.</span></span> <span data-ttu-id="cc488-203">Grazie a questa progettazione simmetrica, gli utenti abituati a operare con il Portale realtà mista non dovranno apprendere un altro modello di interazione per il puntamento e la manipolazione da lontano quando usano HoloLens 2 e viceversa.</span><span class="sxs-lookup"><span data-stu-id="cc488-203">With this symmetric design, users who are familiar with MRP won't need to learn another interaction model for far pointing and manipulation when they use HoloLens 2, and the other way around.</span></span>    

:::row:::
    :::column:::
        <span data-ttu-id="cc488-204">![Progettazione simmetrica per raggi con controller](images/symmetric-design-for-rays-controllers.jpg)</span><span class="sxs-lookup"><span data-stu-id="cc488-204">![symmetric design for rays with controllers](images/symmetric-design-for-rays-controllers.jpg)</span></span><br>
        <span data-ttu-id="cc488-205">**Raggi del controller**</span><span class="sxs-lookup"><span data-stu-id="cc488-205">**Controller rays**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="cc488-206">![Progettazione simmetrica per raggi con le mani](images/symmetric-design-for-rays-hands.jpg)</span><span class="sxs-lookup"><span data-stu-id="cc488-206">![symmetric design for rays with hands](images/symmetric-design-for-rays-hands.jpg)</span></span><br>
        <span data-ttu-id="cc488-207">**Raggi della mano**</span><span class="sxs-lookup"><span data-stu-id="cc488-207">**Hand rays**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="hand-ray-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="cc488-208">Raggio della mano in MRTK (Mixed Reality Toolkit) per Unity</span><span class="sxs-lookup"><span data-stu-id="cc488-208">Hand ray in MRTK (Mixed Reality Toolkit) for Unity</span></span>

<span data-ttu-id="cc488-209">Per impostazione predefinita, MRTK fornisce un file prefab relativo al raggio della mano ([DefaultControllerPointer.prefab](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Prefabs/Pointers)) con lo stesso stato di visualizzazione del raggio della mano di sistema della shell.</span><span class="sxs-lookup"><span data-stu-id="cc488-209">By default, MRTK provides a hand ray prefab ([DefaultControllerPointer.prefab](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Prefabs/Pointers)) which has the same visual state as the shell's system hand ray.</span></span> <span data-ttu-id="cc488-210">Tale file viene assegnato in Pointers (Puntatori) nel profilo di input di MRTK.</span><span class="sxs-lookup"><span data-stu-id="cc488-210">It's assigned in MRTK's Input profile, under Pointers.</span></span> <span data-ttu-id="cc488-211">In un visore VR immersive gli stessi raggi vengono usati per i controller del movimento.</span><span class="sxs-lookup"><span data-stu-id="cc488-211">In an immersive headset, the same rays are used for the motion controllers.</span></span>

* [<span data-ttu-id="cc488-212">MRTK - Profilo del puntatore</span><span class="sxs-lookup"><span data-stu-id="cc488-212">MRTK - Pointer profile</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MixedRealityConfigurationGuide.html#pointer-configuration)
* [<span data-ttu-id="cc488-213">MRTK - Sistema di input</span><span class="sxs-lookup"><span data-stu-id="cc488-213">MRTK - Input system</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html)
* [<span data-ttu-id="cc488-214">MRTK - Puntatori</span><span class="sxs-lookup"><span data-stu-id="cc488-214">MRTK - Pointers</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Pointers.html)

---

## <a name="see-also"></a><span data-ttu-id="cc488-215">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="cc488-215">See also</span></span>
* [<span data-ttu-id="cc488-216">Manipolazione diretta con le mani</span><span class="sxs-lookup"><span data-stu-id="cc488-216">Direct manipulation with hands</span></span>](direct-manipulation.md)
* [<span data-ttu-id="cc488-217">Sguardo e commit</span><span class="sxs-lookup"><span data-stu-id="cc488-217">Gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="cc488-218">Mani - Manipolazione diretta</span><span class="sxs-lookup"><span data-stu-id="cc488-218">Hands - Direct manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="cc488-219">Mani - Movimenti</span><span class="sxs-lookup"><span data-stu-id="cc488-219">Hands - Gestures</span></span>](gaze-and-commit.md#composite-gestures)
* [<span data-ttu-id="cc488-220">Interazioni istintive</span><span class="sxs-lookup"><span data-stu-id="cc488-220">Instinctual interactions</span></span>](interaction-fundamentals.md)
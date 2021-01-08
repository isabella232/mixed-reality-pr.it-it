---
title: Puntamento con la testa e commit
description: Introduzione al modello di input Head-sguardi e commit, inclusi il ridimensionamento, la posizione e la stabilizzazione della destinazione.
author: caseymeekhof
ms.author: cmeekhof
ms.date: 03/31/2019
ms.topic: article
keywords: Realtà mista, sguardo, targeting, interazione, progettazione, cuffie per realtà mista, cuffie di realtà mista di Windows, headset di realtà virtuale, HoloLens, MRTK, Toolkit realtà mista, target, Focus, smoothing
ms.openlocfilehash: 13a040a8309d084fcfdbfa91cbd9d63b595b004a
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2021
ms.locfileid: "98009451"
---
# <a name="head-gaze-and-commit"></a><span data-ttu-id="e2aae-104">Puntamento con la testa e commit</span><span class="sxs-lookup"><span data-stu-id="e2aae-104">Head-gaze and commit</span></span>

<span data-ttu-id="e2aae-105">_Head-sguardi e commit_ sono un caso speciale del modello di input [sguardo e commit](gaze-and-commit.md) che prevede la destinazione di un oggetto con la direzione di un utente.</span><span class="sxs-lookup"><span data-stu-id="e2aae-105">_Head-gaze and commit_ is a special case of the [gaze and commit](gaze-and-commit.md) input model that involves targeting an object with a users head direction.</span></span> <span data-ttu-id="e2aae-106">È possibile agire sulla destinazione con un input secondario, ad esempio il tocco di movimento della mano o il comando vocale "Select".</span><span class="sxs-lookup"><span data-stu-id="e2aae-106">You can act on the target with a secondary input, such as the hand gesture air tap or "Select" voice command.</span></span> 

## <a name="device-support"></a><span data-ttu-id="e2aae-107">Supporto di dispositivi</span><span class="sxs-lookup"><span data-stu-id="e2aae-107">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="e2aae-108"><strong>Modello di input</strong></span><span class="sxs-lookup"><span data-stu-id="e2aae-108"><strong>Input model</strong></span></span></td>
        <td><span data-ttu-id="e2aae-109"><a href="../hololens-hardware-details.md"><strong>HoloLens (prima generazione)</strong></a></span><span class="sxs-lookup"><span data-stu-id="e2aae-109"><a href="../hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="e2aae-110"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="e2aae-110"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="e2aae-111"><a href="../discover/immersive-headset-hardware-details.md"><strong>Visori VR immersive</strong></a></span><span class="sxs-lookup"><span data-stu-id="e2aae-111"><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="e2aae-112">Puntamento con la testa e commit</span><span class="sxs-lookup"><span data-stu-id="e2aae-112">Head-gaze and commit</span></span></td>
        <td><span data-ttu-id="e2aae-113">✔️ Consigliata</span><span class="sxs-lookup"><span data-stu-id="e2aae-113">✔️ Recommended</span></span></td>
        <td><span data-ttu-id="e2aae-114">✔️ Consigliato (terza scelta - <a href="interaction-fundamentals.md">Vedi le altre opzioni</a>)</span><span class="sxs-lookup"><span data-stu-id="e2aae-114">✔️ Recommended (third choice - <a href="interaction-fundamentals.md">See the other options</a>)</span></span></td>
        <td><span data-ttu-id="e2aae-115">➕ Opzione alternativa</span><span class="sxs-lookup"><span data-stu-id="e2aae-115">➕ Alternate option</span></span></td>
    </tr>
</table>

---

## <a name="target-sizing-and-feedback"></a><span data-ttu-id="e2aae-116">Dimensioni della destinazione e feedback</span><span class="sxs-lookup"><span data-stu-id="e2aae-116">Target sizing and feedback</span></span>

<span data-ttu-id="e2aae-117">Il vettore di sguardi a capo è stato visualizzato ripetutamente per poter essere usato per obiettivi mirati, ma spesso funziona meglio per il targeting lordo, acquisendo obiettivi più grandi.</span><span class="sxs-lookup"><span data-stu-id="e2aae-117">The head gaze vector has been shown repeatedly to be usable for fine targeting, but often works best for gross targeting--acquiring larger targets.</span></span> <span data-ttu-id="e2aae-118">Le dimensioni di destinazione minime di 1 grado a 1,5 gradi consentono azioni utente riuscite nella maggior parte degli scenari, sebbene le destinazioni di 3 gradi consentano spesso una maggiore velocità.</span><span class="sxs-lookup"><span data-stu-id="e2aae-118">Minimum target sizes of 1 degree to 1.5 degrees allow successful user actions in most scenarios, though targets of 3 degrees often allow for greater speed.</span></span> <span data-ttu-id="e2aae-119">La dimensione che l'utente ha come destinazione è in realtà un'area 2D anche per gli elementi 3D, a seconda che la proiezione sia rivolta a tali elementi sia l'area di destinazione.</span><span class="sxs-lookup"><span data-stu-id="e2aae-119">The size that the user targets is effectively a 2D area even for 3D elements--whichever projection is facing them should be the targetable area.</span></span> <span data-ttu-id="e2aae-120">Fornire un segnale saliente che un elemento è "attivo" (che è destinato all'utente) è utile.</span><span class="sxs-lookup"><span data-stu-id="e2aae-120">Providing some salient cue that an element is "active" (that the user is targeting it) is helpful.</span></span> <span data-ttu-id="e2aae-121">Questo può includere trattamenti quali effetti "hover" visibili, evidenziazioni audio o clic oppure un chiaro allineamento di un cursore con un elemento.</span><span class="sxs-lookup"><span data-stu-id="e2aae-121">This can include treatments like visible "hover" effects, audio highlights or clicks, or clear alignment of a cursor with an element.</span></span>

<span data-ttu-id="e2aae-122">![Dimensioni ottimali della destinazione a una distanza di 2 metri](images/gazetargeting-size-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="e2aae-122">![Optimal target size at 2 meter distance](images/gazetargeting-size-1000px.jpg)</span></span><br>
<span data-ttu-id="e2aae-123">*Dimensioni di destinazione ottimali a distanza di 2 metri*</span><span class="sxs-lookup"><span data-stu-id="e2aae-123">*Optimal target size at 2-meter distance*</span></span>

<br>

<span data-ttu-id="e2aae-124">![Esempio di evidenziazione di un oggetto selezionato come destinazione con lo sguardo fisso](images/gazetargeting-highlighting-940px.jpg)</span><span class="sxs-lookup"><span data-stu-id="e2aae-124">![An example of highlighting a gaze targeted object](images/gazetargeting-highlighting-940px.jpg)</span></span><br>
<span data-ttu-id="e2aae-125">*Esempio di evidenziazione di un oggetto selezionato come destinazione con lo sguardo fisso*</span><span class="sxs-lookup"><span data-stu-id="e2aae-125">*An example of highlighting a gaze targeted object*</span></span>

## <a name="target-placement"></a><span data-ttu-id="e2aae-126">Posizionamento della destinazione</span><span class="sxs-lookup"><span data-stu-id="e2aae-126">Target placement</span></span>

<span data-ttu-id="e2aae-127">Spesso gli utenti non riescono a trovare gli elementi dell'interfaccia utente che si trovano troppo alta o bassa nel campo di visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="e2aae-127">Users often fail to find UI elements located either too high or low in their field of view.</span></span> <span data-ttu-id="e2aae-128">La maggior parte delle loro attenzioni si basa su aree intorno al proprio obiettivo principale, che è approssimativamente a livello di occhio.</span><span class="sxs-lookup"><span data-stu-id="e2aae-128">Most of their attention ends up on areas around their main focus, which is approximately at eye level.</span></span> <span data-ttu-id="e2aae-129">Può pertanto rivelarsi utile posizionare la maggior parte delle destinazioni in una fascia ragionevole attorno al livello degli occhi.</span><span class="sxs-lookup"><span data-stu-id="e2aae-129">Placing most targets in some reasonable band around eye level can help.</span></span> <span data-ttu-id="e2aae-130">Data la tendenza per gli utenti a concentrarsi su un'area visiva relativamente piccola in qualsiasi momento (il cono di attenzione della visione è approssimativamente di 10 gradi), raggruppare gli elementi dell'interfaccia in modo che siano correlati concettualmente possono usare comportamenti di concatenamento dell'attenzione da elemento a elemento quando un utente sposta il proprio sguardo attraverso un'area.</span><span class="sxs-lookup"><span data-stu-id="e2aae-130">Given the tendency for users to focus on a relatively small visual area at any time (the attentional cone of vision is roughly 10 degrees), grouping UI elements together to the degree they're related conceptually can use attention-chaining behaviors from item to item as a user moves their gaze through an area.</span></span> <span data-ttu-id="e2aae-131">Quando progetti l'interfaccia utente, tieni presente la grande differenza potenziale di campo visivo tra i visori HoloLens e i visori VR immersive.</span><span class="sxs-lookup"><span data-stu-id="e2aae-131">When designing UI, keep in mind the potential large variation in field of view between HoloLens and immersive headsets.</span></span>

<span data-ttu-id="e2aae-132">![Esempio di elementi dell'interfaccia utente raggruppati per facilitare la selezione della destinazione con lo sguardo fisso in Galaxy Explorer](images/gazetargeting-grouping-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="e2aae-132">![An example of grouped UI elements for easier gaze targeting in Galaxy Explorer](images/gazetargeting-grouping-1000px.jpg)</span></span><br>
<span data-ttu-id="e2aae-133">*Esempio di elementi dell'interfaccia utente raggruppati per facilitare la selezione della destinazione con lo sguardo fisso in Galaxy Explorer*</span><span class="sxs-lookup"><span data-stu-id="e2aae-133">*An example of grouped UI elements for easier gaze targeting in Galaxy Explorer*</span></span>

## <a name="improving-targeting-behaviors"></a><span data-ttu-id="e2aae-134">Miglioramento dei comportamenti di selezione della destinazione</span><span class="sxs-lookup"><span data-stu-id="e2aae-134">Improving targeting behaviors</span></span>

<span data-ttu-id="e2aae-135">Se è possibile determinare o approssimarsi in modo accurato gli obiettivi dell'utente, può essere utile accettare i tentativi di interazione Near Miss come se fossero destinati correttamente.</span><span class="sxs-lookup"><span data-stu-id="e2aae-135">If user intent to target something can be determined or closely approximated, it can be helpful to accept near miss interaction attempts as though they were targeted correctly.</span></span> <span data-ttu-id="e2aae-136">Ecco alcuni metodi efficaci che possono essere incorporati in esperienze di realtà mista:</span><span class="sxs-lookup"><span data-stu-id="e2aae-136">Here's a handful of successful methods that can be incorporated in mixed reality experiences:</span></span>

### <a name="head-gaze-stabilization-gravity-wells"></a><span data-ttu-id="e2aae-137">Stabilizzazione del puntamento con la testa ("pozzi di gravità")</span><span class="sxs-lookup"><span data-stu-id="e2aae-137">Head-gaze stabilization ("gravity wells")</span></span>

<span data-ttu-id="e2aae-138">Questa operazione deve essere attivata la maggior parte o tutto il tempo.</span><span class="sxs-lookup"><span data-stu-id="e2aae-138">This should be turned on most or all of the time.</span></span> <span data-ttu-id="e2aae-139">Questa tecnica consente di rimuovere le instabilità naturale e del collo che possono essere spostate dagli utenti a causa dei comportamenti di ricerca e di pronuncia.</span><span class="sxs-lookup"><span data-stu-id="e2aae-139">This technique removes the natural head and neck jitters that users might have as well movement because of looking and speaking behaviors.</span></span>

### <a name="closest-link-algorithms"></a><span data-ttu-id="e2aae-140">Algoritmi di collegamento più vicino</span><span class="sxs-lookup"><span data-stu-id="e2aae-140">Closest link algorithms</span></span>

<span data-ttu-id="e2aae-141">Questi algoritmi funzionano meglio in aree con contenuto interattivo sparse.</span><span class="sxs-lookup"><span data-stu-id="e2aae-141">These algorithms work best in areas with sparse interactive content.</span></span> <span data-ttu-id="e2aae-142">Se c'è una probabilità elevata che è possibile determinare ciò che un utente ha tentato di interagire, è possibile integrare le proprie capacità di destinazione supponendo un certo livello di INTENTITà.</span><span class="sxs-lookup"><span data-stu-id="e2aae-142">If there's a high probability that you can determine what a user was attempting to interact with, you can supplement their targeting abilities by assuming some level of intent.</span></span>

### <a name="backdating-and-postdating-actions"></a><span data-ttu-id="e2aae-143">Azioni di Ridata e di backdating</span><span class="sxs-lookup"><span data-stu-id="e2aae-143">Backdating and postdating actions</span></span>

<span data-ttu-id="e2aae-144">Questo meccanismo è utile per le attività che richiedono velocità.</span><span class="sxs-lookup"><span data-stu-id="e2aae-144">This mechanism is useful in tasks requiring speed.</span></span> <span data-ttu-id="e2aae-145">Quando un utente passa attraverso una serie di manovre mirate e di attivazione alla velocità, è utile presupporre un certo scopo.</span><span class="sxs-lookup"><span data-stu-id="e2aae-145">When a user is moving through a series of targeting and activation maneuvers at speed, it's useful to assume some intent.</span></span> <span data-ttu-id="e2aae-146">È utile anche per consentire la mancata procedura di azione sulle destinazioni in cui l'utente si è concentrato leggermente prima o leggermente dopo il tocco (50 ms prima/dopo è stato efficace nei test iniziali).</span><span class="sxs-lookup"><span data-stu-id="e2aae-146">It's also useful to allow missed steps to act on targets that the user had in focus slightly before or slightly after the tap (50 ms before/after was effective in early testing).</span></span>

### <a name="smoothing"></a><span data-ttu-id="e2aae-147">Definizione di movimenti uniformi</span><span class="sxs-lookup"><span data-stu-id="e2aae-147">Smoothing</span></span>

<span data-ttu-id="e2aae-148">Questo meccanismo è utile per i movimenti di percorso, riducendo il lieve jitter e le oscillazioni a causa delle caratteristiche di movimento della testa naturale.</span><span class="sxs-lookup"><span data-stu-id="e2aae-148">This mechanism is useful for pathing movements, reducing the slight jitter and wobbles because of natural head movement characteristics.</span></span> <span data-ttu-id="e2aae-149">Quando si smussano i movimenti del tracciato, è necessario arrotondare le dimensioni e la distanza dei movimenti anziché nel tempo.</span><span class="sxs-lookup"><span data-stu-id="e2aae-149">When smoothing over pathing motions, smooth by the size and distance of movements rather than over time.</span></span>

### <a name="magnetism"></a><span data-ttu-id="e2aae-150">Magnetismo</span><span class="sxs-lookup"><span data-stu-id="e2aae-150">Magnetism</span></span>

<span data-ttu-id="e2aae-151">Questo meccanismo può essere considerato come una versione più generale degli algoritmi di collegamento più vicini, ovvero disegnare un cursore verso una destinazione o semplicemente aumentare hitboxes, in modo visibile o meno, perché gli utenti si avvicinano a destinazioni potenziali usando una certa conoscenza del layout interattivo per migliorare l'approccio degli utenti.</span><span class="sxs-lookup"><span data-stu-id="e2aae-151">This mechanism can be thought of as a more general version of closest link algorithms--drawing a cursor toward a target or simply increasing hitboxes, whether visibly or not, as users approach likely targets by using some knowledge of the interactive layout to better approach user intent.</span></span> <span data-ttu-id="e2aae-152">Questo può essere potente per le destinazioni di piccole dimensioni.</span><span class="sxs-lookup"><span data-stu-id="e2aae-152">This can be powerful for small targets.</span></span>

### <a name="focus-stickiness"></a><span data-ttu-id="e2aae-153">Spostamento dello stato attivo in base all'elemento di interesse corrente</span><span class="sxs-lookup"><span data-stu-id="e2aae-153">Focus stickiness</span></span>

<span data-ttu-id="e2aae-154">Quando si determinano gli elementi interattivi adiacenti da assegnare, lo stato attivo alla viscosità dello stato attivo fornisce una distorsione all'elemento attualmente attivo.</span><span class="sxs-lookup"><span data-stu-id="e2aae-154">When determining which nearby interactive elements to give,  focus to, focus stickiness provides a bias to the element that is currently focused.</span></span> <span data-ttu-id="e2aae-155">Questo consente di ridurre i comportamenti di cambio dello stato attivo quando si esegue il mobile a un punto medio tra due elementi con rumore naturale.</span><span class="sxs-lookup"><span data-stu-id="e2aae-155">This helps reduce erratic focus switching behaviors when floating at a midpoint between two elements with natural noise.</span></span>

## <a name="see-also"></a><span data-ttu-id="e2aae-156">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="e2aae-156">See also</span></span>

* [<span data-ttu-id="e2aae-157">Interazione basata sullo sguardo</span><span class="sxs-lookup"><span data-stu-id="e2aae-157">Eye-based interaction</span></span>](eye-gaze-interaction.md)
* [<span data-ttu-id="e2aae-158">Sguardo fisso e attesa</span><span class="sxs-lookup"><span data-stu-id="e2aae-158">Gaze and dwell</span></span>](gaze-and-dwell.md)
* [<span data-ttu-id="e2aae-159">Mani - Manipolazione diretta</span><span class="sxs-lookup"><span data-stu-id="e2aae-159">Hands - Direct manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="e2aae-160">Mani - Movimenti</span><span class="sxs-lookup"><span data-stu-id="e2aae-160">Hands - Gestures</span></span>](gaze-and-commit.md#composite-gestures)
* [<span data-ttu-id="e2aae-161">Mani - Puntamento e commit</span><span class="sxs-lookup"><span data-stu-id="e2aae-161">Hands - Point and commit</span></span>](point-and-commit.md)
* [<span data-ttu-id="e2aae-162">Interazioni istintive</span><span class="sxs-lookup"><span data-stu-id="e2aae-162">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="e2aae-163">Input vocale</span><span class="sxs-lookup"><span data-stu-id="e2aae-163">Voice input</span></span>](voice-input.md)




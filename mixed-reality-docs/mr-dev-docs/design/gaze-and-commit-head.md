---
title: Puntamento con la testa e commit
description: Introduzione al modello di input head-gaze e commit, tra cui ridimensionamento, posizionamento e stabilizzazione della destinazione.
author: caseymeekhof
ms.author: cmeekhof
ms.date: 03/31/2019
ms.topic: article
keywords: Realtà mista, sguardo, targeting dello sguardo, interazione, progettazione, visore per realtà mista, visore per realtà mista windows, visore per realtà virtuale, HoloLens, MRTK, Mixed Reality Toolkit, destinazione, messa a fuoco, smoothing
ms.openlocfilehash: 74f963a6b450d1fb7f1302886a01c12cf79ce28a
ms.sourcegitcommit: 8f141a843bcfc57e1b18cc606292186b8ac72641
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/19/2021
ms.locfileid: "110196516"
---
# <a name="head-gaze-and-commit"></a><span data-ttu-id="8c9b9-104">Puntamento con la testa e commit</span><span class="sxs-lookup"><span data-stu-id="8c9b9-104">Head-gaze and commit</span></span>

<span data-ttu-id="8c9b9-105">_Head-gaze and commit_ è un caso speciale del modello di input [gaze and commit](gaze-and-commit.md) che prevede la destinazione di un oggetto con una direzione di testa degli utenti.</span><span class="sxs-lookup"><span data-stu-id="8c9b9-105">_Head-gaze and commit_ is a special case of the [gaze and commit](gaze-and-commit.md) input model that involves targeting an object with a users head direction.</span></span> <span data-ttu-id="8c9b9-106">È possibile agire sulla destinazione con un input secondario, ad esempio il tocco dell'aria del movimento della mano o il comando vocale "Seleziona".</span><span class="sxs-lookup"><span data-stu-id="8c9b9-106">You can act on the target with a secondary input, such as the hand gesture air tap or "Select" voice command.</span></span> 

## <a name="device-support"></a><span data-ttu-id="8c9b9-107">Supporto di dispositivi</span><span class="sxs-lookup"><span data-stu-id="8c9b9-107">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="8c9b9-108"><strong>Modello di input</strong></span><span class="sxs-lookup"><span data-stu-id="8c9b9-108"><strong>Input model</strong></span></span></td>
        <td><span data-ttu-id="8c9b9-109"><a href="/hololens/hololens1-hardware"><strong>HoloLens (prima generazione)</strong></a></span><span class="sxs-lookup"><span data-stu-id="8c9b9-109"><a href="/hololens/hololens1-hardware"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="8c9b9-110"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="8c9b9-110"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="8c9b9-111"><a href="../discover/immersive-headset-hardware-details.md"><strong>Visori VR immersive</strong></a></span><span class="sxs-lookup"><span data-stu-id="8c9b9-111"><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="8c9b9-112">Puntamento con la testa e commit</span><span class="sxs-lookup"><span data-stu-id="8c9b9-112">Head-gaze and commit</span></span></td>
        <td><span data-ttu-id="8c9b9-113">✔️ Consigliato</span><span class="sxs-lookup"><span data-stu-id="8c9b9-113">✔️ Recommended</span></span></td>
        <td><span data-ttu-id="8c9b9-114">✔️ Consigliato (terza scelta - <a href="interaction-fundamentals.md">Vedi le altre opzioni</a>)</span><span class="sxs-lookup"><span data-stu-id="8c9b9-114">✔️ Recommended (third choice - <a href="interaction-fundamentals.md">See the other options</a>)</span></span></td>
        <td><span data-ttu-id="8c9b9-115">➕ Opzione alternativa</span><span class="sxs-lookup"><span data-stu-id="8c9b9-115">➕ Alternate option</span></span></td>
    </tr>
</table>

---

## <a name="head-and-eye-tracking-design-concepts-demo"></a><span data-ttu-id="8c9b9-116">Demo dei concetti di progettazione del rilevamento oculare e della testa</span><span class="sxs-lookup"><span data-stu-id="8c9b9-116">Head and eye tracking design concepts demo</span></span>

<span data-ttu-id="8c9b9-117">Se si desidera vedere i concetti di progettazione di Head e Eye Tracking in azione, vedere la demo video **Designing Holograms - Head Tracking and Eye Tracking** (Progettazione di ologrammi - Rilevamento della testa e tracciamento oculare) di seguito.</span><span class="sxs-lookup"><span data-stu-id="8c9b9-117">If you'd like to see Head and Eye Tracking design concepts in action, check out our **Designing Holograms - Head Tracking and Eye Tracking** video demo below.</span></span> <span data-ttu-id="8c9b9-118">Al termine, continuare per un'analisi più dettagliata di argomenti specifici.</span><span class="sxs-lookup"><span data-stu-id="8c9b9-118">When you've finished, continue on for a more detailed dive into specific topics.</span></span>

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Microsofts-Designing-Holograms-Head-Tracking-and-Eye-Tracking-Chapter/player]

<span data-ttu-id="8c9b9-119">*Questo video è stato tratto dall'app "Designing Holograms" (Progettazione di ologrammi) HoloLens 2 app. Scaricare e usufruire dell'esperienza completa [qui.](https://aka.ms/dhapp)*</span><span class="sxs-lookup"><span data-stu-id="8c9b9-119">*This video was taken from the "Designing Holograms" HoloLens 2 app. Download and enjoy the full experience [here](https://aka.ms/dhapp).*</span></span>

## <a name="target-sizing-and-feedback"></a><span data-ttu-id="8c9b9-120">Dimensioni della destinazione e feedback</span><span class="sxs-lookup"><span data-stu-id="8c9b9-120">Target sizing and feedback</span></span>

<span data-ttu-id="8c9b9-121">Il vettore dello sguardo fisso della testa è stato ripetutamente indicato come utilizzabile per la destinazione fine, ma spesso funziona meglio per il targeting lordo, acquisendo obiettivi più grandi.</span><span class="sxs-lookup"><span data-stu-id="8c9b9-121">The head gaze vector has been shown repeatedly to be usable for fine targeting, but often works best for gross targeting--acquiring larger targets.</span></span> <span data-ttu-id="8c9b9-122">Le dimensioni minime di destinazione da 1 a 1,5 gradi consentono azioni utente riuscite nella maggior parte degli scenari, anche se le destinazioni di 3 gradi spesso consentono una maggiore velocità.</span><span class="sxs-lookup"><span data-stu-id="8c9b9-122">Minimum target sizes of 1 degree to 1.5 degrees allow successful user actions in most scenarios, though targets of 3 degrees often allow for greater speed.</span></span> <span data-ttu-id="8c9b9-123">Le dimensioni di destinazione dell'utente sono effettivamente un'area 2D anche per gli elementi 3D, a seconda della proiezione che li sta affrontando, deve essere l'area di destinazione.</span><span class="sxs-lookup"><span data-stu-id="8c9b9-123">The size that the user targets is effectively a 2D area even for 3D elements--whichever projection is facing them should be the targetable area.</span></span> <span data-ttu-id="8c9b9-124">È utile fornire un segnale saliente che un elemento è "attivo" (che l'utente sta indicando come destinazione).</span><span class="sxs-lookup"><span data-stu-id="8c9b9-124">Providing some salient cue that an element is "active" (that the user is targeting it) is helpful.</span></span> <span data-ttu-id="8c9b9-125">Può trattarsi di effetti visibili di "hover", evidenziazioni audio o clic o di un allineamento chiaro di un cursore con un elemento.</span><span class="sxs-lookup"><span data-stu-id="8c9b9-125">This can include treatments like visible "hover" effects, audio highlights or clicks, or clear alignment of a cursor with an element.</span></span>

<span data-ttu-id="8c9b9-126">![Dimensioni ottimali della destinazione a una distanza di 2 metri](images/gazetargeting-size-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="8c9b9-126">![Optimal target size at 2 meter distance](images/gazetargeting-size-1000px.jpg)</span></span><br>
<span data-ttu-id="8c9b9-127">*Dimensioni ottimali della destinazione a 2 metri di distanza*</span><span class="sxs-lookup"><span data-stu-id="8c9b9-127">*Optimal target size at 2-meter distance*</span></span>

<br>

<span data-ttu-id="8c9b9-128">![Esempio di evidenziazione di un oggetto selezionato come destinazione con lo sguardo fisso](images/gazetargeting-highlighting-940px.jpg)</span><span class="sxs-lookup"><span data-stu-id="8c9b9-128">![An example of highlighting a gaze targeted object](images/gazetargeting-highlighting-940px.jpg)</span></span><br>
<span data-ttu-id="8c9b9-129">*Esempio di evidenziazione di un oggetto selezionato come destinazione con lo sguardo fisso*</span><span class="sxs-lookup"><span data-stu-id="8c9b9-129">*An example of highlighting a gaze targeted object*</span></span>

## <a name="target-placement"></a><span data-ttu-id="8c9b9-130">Posizionamento della destinazione</span><span class="sxs-lookup"><span data-stu-id="8c9b9-130">Target placement</span></span>

<span data-ttu-id="8c9b9-131">Gli utenti spesso non riescono a trovare gli elementi dell'interfaccia utente che si trovano troppo in alto o in basso nel campo di visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="8c9b9-131">Users often fail to find UI elements located either too high or low in their field of view.</span></span> <span data-ttu-id="8c9b9-132">La maggior parte della loro attenzione finisce sulle aree intorno alla loro attenzione principale, che è approssimativamente a livello oculare.</span><span class="sxs-lookup"><span data-stu-id="8c9b9-132">Most of their attention ends up on areas around their main focus, which is approximately at eye level.</span></span> <span data-ttu-id="8c9b9-133">Può pertanto rivelarsi utile posizionare la maggior parte delle destinazioni in una fascia ragionevole attorno al livello degli occhi.</span><span class="sxs-lookup"><span data-stu-id="8c9b9-133">Placing most targets in some reasonable band around eye level can help.</span></span> <span data-ttu-id="8c9b9-134">Data la tendenza degli utenti a concentrarsi su un'area visiva relativamente piccola in qualsiasi momento (il cono di vista attento è di circa 10 gradi), il raggruppamento degli elementi dell'interfaccia utente nella misura concettuale in cui sono correlati può usare comportamenti di concatenamento dell'attenzione da elemento a elemento quando un utente sposta lo sguardo fisso in un'area.</span><span class="sxs-lookup"><span data-stu-id="8c9b9-134">Given the tendency for users to focus on a relatively small visual area at any time (the attentional cone of vision is roughly 10 degrees), grouping UI elements together to the degree they're related conceptually can use attention-chaining behaviors from item to item as a user moves their gaze through an area.</span></span> <span data-ttu-id="8c9b9-135">Quando progetti l'interfaccia utente, tieni presente la grande differenza potenziale di campo visivo tra i visori HoloLens e i visori VR immersive.</span><span class="sxs-lookup"><span data-stu-id="8c9b9-135">When designing UI, keep in mind the potential large variation in field of view between HoloLens and immersive headsets.</span></span>

<span data-ttu-id="8c9b9-136">![Esempio di elementi dell'interfaccia utente raggruppati per facilitare la selezione della destinazione con lo sguardo fisso in Galaxy Explorer](images/gazetargeting-grouping-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="8c9b9-136">![An example of grouped UI elements for easier gaze targeting in Galaxy Explorer](images/gazetargeting-grouping-1000px.jpg)</span></span><br>
<span data-ttu-id="8c9b9-137&quot;>*Esempio di elementi dell'interfaccia utente raggruppati per facilitare la selezione della destinazione con lo sguardo fisso in Galaxy Explorer*</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;8c9b9-137&quot;>*An example of grouped UI elements for easier gaze targeting in Galaxy Explorer*</span></span>

## <a name=&quot;improving-targeting-behaviors&quot;></a><span data-ttu-id=&quot;8c9b9-138&quot;>Miglioramento dei comportamenti di selezione della destinazione</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;8c9b9-138&quot;>Improving targeting behaviors</span></span>

<span data-ttu-id=&quot;8c9b9-139&quot;>Se l'intento dell'utente di specificare come destinazione un elemento può essere determinato o approssimato in modo molto approssimativo, può essere utile accettare tentativi di interazione quasi non riusciti come se fossero stati indirizzati correttamente.</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;8c9b9-139&quot;>If user intent to target something can be determined or closely approximated, it can be helpful to accept near miss interaction attempts as though they were targeted correctly.</span></span> <span data-ttu-id=&quot;8c9b9-140&quot;>Ecco alcuni metodi di successo che possono essere incorporati nelle esperienze di realtà mista:</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;8c9b9-140&quot;>Here's a handful of successful methods that can be incorporated in mixed reality experiences:</span></span>

### <a name=&quot;head-gaze-stabilization-gravity-wells&quot;></a><span data-ttu-id=&quot;8c9b9-141&quot;>Stabilizzazione del puntamento con la testa (&quot;pozzi di gravità")</span><span class="sxs-lookup"><span data-stu-id="8c9b9-141">Head-gaze stabilization ("gravity wells")</span></span>

<span data-ttu-id="8c9b9-142">Questa opzione deve essere attivata per la maggior parte o per tutto il tempo.</span><span class="sxs-lookup"><span data-stu-id="8c9b9-142">This should be turned on most or all of the time.</span></span> <span data-ttu-id="8c9b9-143">Questa tecnica rimuove gli instabilità naturali della testa e del collo che gli utenti potrebbero avere anche il movimento a causa dei comportamenti di aspetto e di pronuncia.</span><span class="sxs-lookup"><span data-stu-id="8c9b9-143">This technique removes the natural head and neck jitters that users might have as well movement because of looking and speaking behaviors.</span></span>

### <a name="closest-link-algorithms"></a><span data-ttu-id="8c9b9-144">Algoritmi di collegamento più vicino</span><span class="sxs-lookup"><span data-stu-id="8c9b9-144">Closest link algorithms</span></span>

<span data-ttu-id="8c9b9-145">Questi algoritmi funzionano meglio nelle aree con contenuto interattivo di tipo sparse.</span><span class="sxs-lookup"><span data-stu-id="8c9b9-145">These algorithms work best in areas with sparse interactive content.</span></span> <span data-ttu-id="8c9b9-146">Se esiste un'alta probabilità che sia possibile determinare con quale elemento un utente sta tentando di interagire, è possibile integrare le capacità di destinazione presupponendo un certo livello di finalità.</span><span class="sxs-lookup"><span data-stu-id="8c9b9-146">If there's a high probability that you can determine what a user was attempting to interact with, you can supplement their targeting abilities by assuming some level of intent.</span></span>

### <a name="backdating-and-postdating-actions"></a><span data-ttu-id="8c9b9-147">Backdating e postdating actions</span><span class="sxs-lookup"><span data-stu-id="8c9b9-147">Backdating and postdating actions</span></span>

<span data-ttu-id="8c9b9-148">Questo meccanismo è utile per le attività che richiedono velocità.</span><span class="sxs-lookup"><span data-stu-id="8c9b9-148">This mechanism is useful in tasks requiring speed.</span></span> <span data-ttu-id="8c9b9-149">Quando un utente sta passando attraverso una serie di richieste di destinazione e attivazione a velocità elevata, è utile presupporre una certa finalità.</span><span class="sxs-lookup"><span data-stu-id="8c9b9-149">When a user is moving through a series of targeting and activation maneuvers at speed, it's useful to assume some intent.</span></span> <span data-ttu-id="8c9b9-150">È anche utile consentire ai passaggi non esigibili di agire sulle destinazioni che l'utente aveva in stato di interesse leggermente prima o dopo il tocco (50 ms prima/dopo erano efficaci nei primi test).</span><span class="sxs-lookup"><span data-stu-id="8c9b9-150">It's also useful to allow missed steps to act on targets that the user had in focus slightly before or slightly after the tap (50 ms before/after was effective in early testing).</span></span>

### <a name="smoothing"></a><span data-ttu-id="8c9b9-151">Definizione di movimenti uniformi</span><span class="sxs-lookup"><span data-stu-id="8c9b9-151">Smoothing</span></span>

<span data-ttu-id="8c9b9-152">Questo meccanismo è utile per il pathing dei movimenti, riducendo i lievi instabilità e gli instabilità a causa delle caratteristiche naturali del movimento della testa.</span><span class="sxs-lookup"><span data-stu-id="8c9b9-152">This mechanism is useful for pathing movements, reducing the slight jitter and wobbles because of natural head movement characteristics.</span></span> <span data-ttu-id="8c9b9-153">Quando si smussa sui movimenti tracciati, smussare in base alle dimensioni e alla distanza dei movimenti anziché nel tempo.</span><span class="sxs-lookup"><span data-stu-id="8c9b9-153">When smoothing over pathing motions, smooth by the size and distance of movements rather than over time.</span></span>

### <a name="magnetism"></a><span data-ttu-id="8c9b9-154">Magnetismo</span><span class="sxs-lookup"><span data-stu-id="8c9b9-154">Magnetism</span></span>

<span data-ttu-id="8c9b9-155">Questo meccanismo può essere pensato come una versione più generale degli algoritmi di collegamento più vicini: il disegno di un cursore verso una destinazione o semplicemente l'aumento di hitbox, in modo visibile o meno, quando gli utenti si avvicinano alle destinazioni più probabili usando una certa conoscenza del layout interattivo per approcciare meglio la finalità dell'utente.</span><span class="sxs-lookup"><span data-stu-id="8c9b9-155">This mechanism can be thought of as a more general version of closest link algorithms--drawing a cursor toward a target or simply increasing hitboxes, whether visibly or not, as users approach likely targets by using some knowledge of the interactive layout to better approach user intent.</span></span> <span data-ttu-id="8c9b9-156">Ciò può essere efficace per destinazioni di piccole dimensioni.</span><span class="sxs-lookup"><span data-stu-id="8c9b9-156">This can be powerful for small targets.</span></span>

### <a name="focus-stickiness"></a><span data-ttu-id="8c9b9-157">Spostamento dello stato attivo in base all'elemento di interesse corrente</span><span class="sxs-lookup"><span data-stu-id="8c9b9-157">Focus stickiness</span></span>

<span data-ttu-id="8c9b9-158">Quando si determinano gli elementi interattivi vicini a cui assegnare lo stato attivo, l'aderenza dello stato attivo fornisce una distorsione all'elemento attualmente attivo.</span><span class="sxs-lookup"><span data-stu-id="8c9b9-158">When determining which nearby interactive elements to give,  focus to, focus stickiness provides a bias to the element that is currently focused.</span></span> <span data-ttu-id="8c9b9-159">Ciò consente di ridurre i comportamenti di cambio dello stato attivo irregolare quando si fluttua a un punto intermedio tra due elementi con disturbo naturale.</span><span class="sxs-lookup"><span data-stu-id="8c9b9-159">This helps reduce erratic focus switching behaviors when floating at a midpoint between two elements with natural noise.</span></span>

## <a name="see-also"></a><span data-ttu-id="8c9b9-160">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="8c9b9-160">See also</span></span>

* [<span data-ttu-id="8c9b9-161">Interazione basata sullo sguardo</span><span class="sxs-lookup"><span data-stu-id="8c9b9-161">Eye-based interaction</span></span>](eye-gaze-interaction.md)
* [<span data-ttu-id="8c9b9-162">Sguardo fisso e attesa</span><span class="sxs-lookup"><span data-stu-id="8c9b9-162">Gaze and dwell</span></span>](gaze-and-dwell.md)
* [<span data-ttu-id="8c9b9-163">Mani - Manipolazione diretta</span><span class="sxs-lookup"><span data-stu-id="8c9b9-163">Hands - Direct manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="8c9b9-164">Mani - Movimenti</span><span class="sxs-lookup"><span data-stu-id="8c9b9-164">Hands - Gestures</span></span>](gaze-and-commit.md#composite-gestures)
* [<span data-ttu-id="8c9b9-165">Mani - Puntamento e commit</span><span class="sxs-lookup"><span data-stu-id="8c9b9-165">Hands - Point and commit</span></span>](point-and-commit.md)
* [<span data-ttu-id="8c9b9-166">Interazioni istintive</span><span class="sxs-lookup"><span data-stu-id="8c9b9-166">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="8c9b9-167">Input vocale</span><span class="sxs-lookup"><span data-stu-id="8c9b9-167">Voice input</span></span>](voice-input.md)
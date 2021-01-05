---
title: Menu a mano
description: I menu a mano consentono agli utenti di visualizzare rapidamente l'interfaccia utente collegata manualmente per le funzioni usate di frequente.
author: nbarragan23
ms.author: nobarr
ms.date: 08/27/2019
ms.topic: article
keywords: mano, menu, pulsante, accesso rapido, layout, auricolare realtà mista, auricolare di realtà misto di Windows, auricolare realtà virtuale, HoloLens, MRTK, Toolkit realtà mista
ms.openlocfilehash: 77df5974f54323310a696ed6630fbdde0b0faeb0
ms.sourcegitcommit: d340303cda71c31e6c3320231473d623c0930d33
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/01/2021
ms.locfileid: "97847803"
---
# <a name="hand-menu"></a><span data-ttu-id="2edaf-104">Menu a mano</span><span class="sxs-lookup"><span data-stu-id="2edaf-104">Hand menu</span></span>

![Posizione della mano del lato ulnare](images/UX_Hero_HandMenu.jpg)

<span data-ttu-id="2edaf-106">Il menu a mano è uno dei modelli UX più esclusivi in HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="2edaf-106">The hand menu is one of the most unique UX patterns in HoloLens 2.</span></span> <span data-ttu-id="2edaf-107">Consente di visualizzare rapidamente l'interfaccia utente collegata manualmente.</span><span class="sxs-lookup"><span data-stu-id="2edaf-107">It allows you to quickly bring up hand-attached UI.</span></span> <span data-ttu-id="2edaf-108">Poiché è accessibile in qualsiasi momento e può essere visualizzato e nascosto facilmente, è ideale per le azioni rapide.</span><span class="sxs-lookup"><span data-stu-id="2edaf-108">Since it's accessible anytime and can be shown and hidden easily, it's great for quick actions.</span></span>

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4AJAg]

<span data-ttu-id="2edaf-109">Sono disponibili le procedure consigliate per l'uso dei menu a mano nell'elenco seguente.</span><span class="sxs-lookup"><span data-stu-id="2edaf-109">You'll find our recommended best practices for working with hand menus in the list below.</span></span> <span data-ttu-id="2edaf-110">È anche possibile trovare una scena di esempio che illustra il menu a mano in [MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_HandMenu.html).</span><span class="sxs-lookup"><span data-stu-id="2edaf-110">You can also find an example scene demonstrating the hand menu in [MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_HandMenu.html).</span></span>

<br>

---

## <a name="best-practices"></a><span data-ttu-id="2edaf-111">Procedure consigliate</span><span class="sxs-lookup"><span data-stu-id="2edaf-111">Best practices</span></span>

<span data-ttu-id="2edaf-112">**Mantieni il numero di pulsanti piccoli**</span><span class="sxs-lookup"><span data-stu-id="2edaf-112">**Keep the number of buttons small**</span></span> 

<span data-ttu-id="2edaf-113">A causa della distanza di chiusura tra un menu con blocco manuale e gli occhi e la tendenza per gli utenti a concentrarsi su un'area visiva relativamente piccola in qualsiasi momento (il cono di attenzione della visione è approssimativamente di 10 gradi), è consigliabile mantenere il numero di pulsanti piccoli.</span><span class="sxs-lookup"><span data-stu-id="2edaf-113">Because of the close distance between a hand-locked menu and the eyes, and the tendency for users to focus on a relatively small visual area at any time (the attentional cone of vision is roughly 10 degrees), we recommend keeping the number of buttons small.</span></span> <span data-ttu-id="2edaf-114">In base all'esplorazione, una colonna con tre pulsanti funziona bene mantenendo tutto il contenuto all'interno del campo di visualizzazione (FOV) anche quando un utente sposta le mani al centro di FOV.</span><span class="sxs-lookup"><span data-stu-id="2edaf-114">Based on our exploration, one column with three buttons works well by keeping all the content within the field of view (FOV) even when a user moves their hands to the center of the FOV.</span></span> 

<span data-ttu-id="2edaf-115">**Usare il menu a mano per l'azione rapida**</span><span class="sxs-lookup"><span data-stu-id="2edaf-115">**Use hand menu for quick action**</span></span> 

<span data-ttu-id="2edaf-116">La generazione di un ARM e la gestione della posizione possono causare un facile affaticamento del braccio.</span><span class="sxs-lookup"><span data-stu-id="2edaf-116">Raising an arm and maintaining the position could easily cause arm fatigue.</span></span> <span data-ttu-id="2edaf-117">Usare un metodo con blocco manuale per il menu che richiede una breve interazione.</span><span class="sxs-lookup"><span data-stu-id="2edaf-117">Use a hand-locked method for the menu requiring a short interaction.</span></span> <span data-ttu-id="2edaf-118">Se il menu è complesso e richiede tempi di interazione estesi, prendere in considerazione l'uso di un blocco globale o del corpo.</span><span class="sxs-lookup"><span data-stu-id="2edaf-118">If your menu is complex and requires extended interaction times, consider using world-locked or body-locked instead.</span></span> 

<span data-ttu-id="2edaf-119">**Angolo pulsante/pannello**</span><span class="sxs-lookup"><span data-stu-id="2edaf-119">**Button / Panel angle**</span></span>

<span data-ttu-id="2edaf-120">I menu devono essere posizionati sulla spalla opposta e al centro della testa: ciò consente a una mano naturale di interagire con il menu con la mano opposta, evitando eventuali posizioni scomode o scomode quando si toccano i pulsanti.</span><span class="sxs-lookup"><span data-stu-id="2edaf-120">Menus should billboard towards the opposite shoulder and middle of the head: This allows a natural hand move to interact with the menu with the opposite hand and avoids any awkward or uncomfortable hand positions when touching buttons.</span></span> 

<span data-ttu-id="2edaf-121">**Provare a supportare un'operazione a mano o senza mani**</span><span class="sxs-lookup"><span data-stu-id="2edaf-121">**Consider supporting one-handed or hands-free operation**</span></span>

<span data-ttu-id="2edaf-122">Non presupporre che entrambe le mani dell'utente siano sempre disponibili.</span><span class="sxs-lookup"><span data-stu-id="2edaf-122">Don't assume both of the user's hands are always available.</span></span> <span data-ttu-id="2edaf-123">Si consideri una vasta gamma di contesti quando una o entrambe le mani non sono disponibili e si verificano gli account di progettazione per tali situazioni.</span><span class="sxs-lookup"><span data-stu-id="2edaf-123">Consider a wide range of contexts when one or both hands aren't available, and make sure your design accounts for those situations.</span></span> <span data-ttu-id="2edaf-124">Per supportare un menu a mano singola, è possibile provare a eseguire la transizione della posizione del menu da Hand-locked a blocco globale quando viene eseguito il capovolgimento della mano (passa a una Palma).</span><span class="sxs-lookup"><span data-stu-id="2edaf-124">To support a one-handed hand menu, you can try transitioning the menu placement from hand-locked to world-locked when the hand flips (goes palm down).</span></span> <span data-ttu-id="2edaf-125">Per gli scenari senza praticità, provare a usare un comando vocale per richiamare il menu a forma di mano.</span><span class="sxs-lookup"><span data-stu-id="2edaf-125">For hands-free scenarios, consider using a voice command to invoke the hand menu.</span></span>

<span data-ttu-id="2edaf-126">**Evitare di aggiungere pulsanti vicino al polso (pulsante Home System)**</span><span class="sxs-lookup"><span data-stu-id="2edaf-126">**Avoid adding buttons near the wrist (system home button)**</span></span>

<span data-ttu-id="2edaf-127">Se i pulsanti del menu a mano sono posizionati troppo vicino al pulsante Home, è possibile che venga accidentalmente attivato durante l'interazione con il menu a mano.</span><span class="sxs-lookup"><span data-stu-id="2edaf-127">If the hand menu buttons are placed too close to the home button, it may accidentally trigger while interacting with the hand menu.</span></span>

<br>

## <a name="hand-menu-with-large-and-complex-ui-controls"></a><span data-ttu-id="2edaf-128">Menu a mano con controlli dell'interfaccia utente complessi e di grandi dimensioni</span><span class="sxs-lookup"><span data-stu-id="2edaf-128">Hand menu with large and complex UI controls</span></span>

<img src="images/HandMenu_SizeExample.png" alt="HoloLens perspective of a menu system that always faces the user" width="940px">
<span data-ttu-id="2edaf-129">È consigliabile limitare il numero di pulsanti o controlli dell'interfaccia utente nei menu collegati manualmente.</span><span class="sxs-lookup"><span data-stu-id="2edaf-129">It's recommended to limit the number of buttons or UI controls on hand-attached menus.</span></span> <span data-ttu-id="2edaf-130">Questo perché l'interazione estesa con un numero elevato di elementi dell'interfaccia utente può causare affaticamento ARM.</span><span class="sxs-lookup"><span data-stu-id="2edaf-130">This is because extended interaction with a large number of UI elements can cause arm fatigue.</span></span> <span data-ttu-id="2edaf-131">Se l'esperienza richiede un menu di grandi dimensioni, è possibile consentire all'utente di bloccare il menu in modo semplice.</span><span class="sxs-lookup"><span data-stu-id="2edaf-131">If your experience requires a large menu, provide an easy way for the user to world lock the menu.</span></span> <span data-ttu-id="2edaf-132">Una tecnica consigliata è quella di bloccare in tutto il mondo quando la mano scende o si capovolge dall'utente.</span><span class="sxs-lookup"><span data-stu-id="2edaf-132">One technique we recommend is to world-lock then menu when the hand drops or flips away from the user.</span></span> <span data-ttu-id="2edaf-133">Una seconda tecnica consiste nel consentire all'utente di acquisire direttamente il menu con l'altra parte.</span><span class="sxs-lookup"><span data-stu-id="2edaf-133">A second technique is to allow the user to directly grab the menu with the other hand.</span></span> <span data-ttu-id="2edaf-134">Quando l'utente rilascia il menu, il menu deve bloccare il mondo.</span><span class="sxs-lookup"><span data-stu-id="2edaf-134">When the user releases the menu, the menu should world lock.</span></span> <span data-ttu-id="2edaf-135">In questo modo, un utente può interagire con diversi elementi dell'interfaccia utente in modo confortevole e sicuro per un lungo periodo di tempo.</span><span class="sxs-lookup"><span data-stu-id="2edaf-135">This way, a user can interact with various UI elements comfortably and confidently over an extended period of time.</span></span> 

<span data-ttu-id="2edaf-136">Quando il menu è bloccato a livello globale, assicurarsi di fornire un modo per spostare il menu e chiudere il menu quando non è più necessario.</span><span class="sxs-lookup"><span data-stu-id="2edaf-136">When the menu is world-locked, make sure to provide a way to move the menu, and close the menu when it's no longer needed.</span></span> <span data-ttu-id="2edaf-137">Rendere il menu mobile fornendo handle sui lati o nella parte superiore del menu.</span><span class="sxs-lookup"><span data-stu-id="2edaf-137">Make the menu movable by providing handles on the sides or top of menu.</span></span> <span data-ttu-id="2edaf-138">Aggiungere un pulsante Chiudi per consentire la chiusura del menu.</span><span class="sxs-lookup"><span data-stu-id="2edaf-138">Add a close button to allow the menu to close.</span></span> <span data-ttu-id="2edaf-139">Consente di ristabilire la connessione del menu quando l'utente si trova in un altro momento.</span><span class="sxs-lookup"><span data-stu-id="2edaf-139">Allow for the menu to reattach to the hand when the user hand faces the user.</span></span> <span data-ttu-id="2edaf-140">Si consiglia inoltre di richiedere che gli utenti si trovino a loro disposizione per evitare le attivazioni false (vedere di seguito).</span><span class="sxs-lookup"><span data-stu-id="2edaf-140">We also recommend requiring that the users gaze at their hand to prevent false activations (see below).</span></span>

<span data-ttu-id="2edaf-141">**Menu di grandi dimensioni che mostra un problema di usabilità**</span><span class="sxs-lookup"><span data-stu-id="2edaf-141">**Large menu that shows a usability issue**</span></span>

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4AOPx]

<span data-ttu-id="2edaf-142">**Menu con blocco globale sulla selezione della mano**</span><span class="sxs-lookup"><span data-stu-id="2edaf-142">**World-locked menu on hand drop**</span></span>

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4AGZi]

<span data-ttu-id="2edaf-143">**Manuale di & pull per il menu di scelta rapida**</span><span class="sxs-lookup"><span data-stu-id="2edaf-143">**Manual grab & pull to world-lock the menu**</span></span>

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4AJAf]

## <a name="how-to-prevent-false-activation"></a><span data-ttu-id="2edaf-144">Come impedire l'attivazione falsa</span><span class="sxs-lookup"><span data-stu-id="2edaf-144">How to prevent false activation</span></span>

<span data-ttu-id="2edaf-145">Se si usa solo il Palm-up come un evento per attivare il menu a mano, è possibile che venga accidentalmente visualizzato quando non è necessario (falso positivo), perché le persone spostano le mani intenzionalmente (per la manipolazione delle comunicazioni e degli oggetti) e non intenzionalmente.</span><span class="sxs-lookup"><span data-stu-id="2edaf-145">If you use just palm-up as an event to trigger the hand menu, it may accidentally appear when you don't need it (false-positive), because people move their hands both intentionally (for communication and object manipulation) and unintentionally.</span></span> <span data-ttu-id="2edaf-146">Per ridurre le attivazioni false, aggiungere un passaggio aggiuntivo oltre all'evento di backup per richiamare il menu a forma di mano, ad esempio le dita completamente aperte, o l'utente che sta intenzionalmente guardando la mano.</span><span class="sxs-lookup"><span data-stu-id="2edaf-146">To reduce false activations, add an extra step besides the palm-up event to invoke the hand menu (such as fully opened fingers, or the user intentionally gazing at their hand).</span></span>

<span data-ttu-id="2edaf-147">**Richiedi Palma piatta**</span><span class="sxs-lookup"><span data-stu-id="2edaf-147">**Require Flat Palm**</span></span>

<span data-ttu-id="2edaf-148">Richiedendo una mano piatta aperta, è possibile impedire l'attivazione falsa che può verificarsi quando l'utente manipola oggetti o movimenti durante la comunicazione all'interno di un ambiente.</span><span class="sxs-lookup"><span data-stu-id="2edaf-148">By requiring a flat open hand, you can prevent false activation that might occur as the user manipulates objects or gestures while communicating within an environment.</span></span> 

<span data-ttu-id="2edaf-149">**Richiedi lo sguardo**</span><span class="sxs-lookup"><span data-stu-id="2edaf-149">**Require Gaze**</span></span>

<span data-ttu-id="2edaf-150">Richiedendo all'utente di guardare la mano (con lo sguardo o con lo sguardo), impedisce le attivazioni false a causa dell'impossibilità da parte dell'utente di indirizzare l'attenzione alla mano come passaggio di attivazione secondaria (con una soglia di distanza ottimizzabile usata per consentire la comodità dell'utente).</span><span class="sxs-lookup"><span data-stu-id="2edaf-150">By requiring the user to gaze at their hand (either with eye gaze or head gaze), it prevents false activations because of the user having to direct their attention to the hand as a secondary activation step (with a tunable distance threshold used to allow for user comfort).</span></span>  

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4Asn4]

---

## <a name="hand-menu-placement-best-practices"></a><span data-ttu-id="2edaf-151">Procedure consigliate per la selezione dei menu a mano</span><span class="sxs-lookup"><span data-stu-id="2edaf-151">Hand menu placement best practices</span></span>

<span data-ttu-id="2edaf-152">Nell'anatomia umana, il nervo ulnare è un nervo che viene eseguito in prossimità dell'osso ulna.</span><span class="sxs-lookup"><span data-stu-id="2edaf-152">In human anatomy, the ulnar nerve is a nerve that runs near the ulna bone.</span></span> <span data-ttu-id="2edaf-153">L'ulna è un osso lungo trovato sull'avambraccio che si estende dal gomito al dito più piccolo.</span><span class="sxs-lookup"><span data-stu-id="2edaf-153">The ulna is a long bone found in the forearm that stretches from the elbow to the smallest finger.</span></span>

<span data-ttu-id="2edaf-154">Di seguito sono riportate due località consigliate in base alle nostre esplorazioni:</span><span class="sxs-lookup"><span data-stu-id="2edaf-154">Below are two recommended placements based on our explorations:</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="2edaf-155">![Posizione della mano del lato ulnare all'interno di Palm](images/UlnarSideHandMenu.gif)</span><span class="sxs-lookup"><span data-stu-id="2edaf-155">![Ulnar side hand location inside palm](images/UlnarSideHandMenu.gif)</span></span><br>
        <span data-ttu-id="2edaf-156">**A. ulnare all'interno di Palm**</span><span class="sxs-lookup"><span data-stu-id="2edaf-156">**A. Ulnar inside palm**</span></span><br>
        <span data-ttu-id="2edaf-157">Questa posizione è affidabile perché le mani non si sovrappongono.</span><span class="sxs-lookup"><span data-stu-id="2edaf-157">This position is reliable because the hands don't overlap each other.</span></span> <span data-ttu-id="2edaf-158">Si tratta di un fattore fondamentale per il rilevamento e il rilevamento delle carte accurate.</span><span class="sxs-lookup"><span data-stu-id="2edaf-158">This is critical for accurate hand detection and tracking.</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="2edaf-159">![Posizione sulla mano del lato ulnare](images/UlnarAboveHandMenu.gif)</span><span class="sxs-lookup"><span data-stu-id="2edaf-159">![Ulnar side hand location above hand](images/UlnarAboveHandMenu.gif)</span></span><br>
        <span data-ttu-id="2edaf-160">**B. oltre la mano del ulnare**</span><span class="sxs-lookup"><span data-stu-id="2edaf-160">**B. Ulnar above hand**</span></span><br>
        <span data-ttu-id="2edaf-161">Questa posizione è comoda per gli utenti perché non è necessario aumentare il proprio ARM per interagire con il menu a mano.</span><span class="sxs-lookup"><span data-stu-id="2edaf-161">This location is comfortable for users because they don't need to raise their arm too much to interact with the hand menu.</span></span> <span data-ttu-id="2edaf-162">È consigliabile posizionare i menu **13 cm** sopra la Palma e allineare i pulsanti all'interno della palma ulnar.</span><span class="sxs-lookup"><span data-stu-id="2edaf-162">We recommend placing menus **13 cm** above the palm and align the buttons inside the ulnar palm.</span></span> [<span data-ttu-id="2edaf-163">Altre informazioni sulle dimensioni dei pulsanti ottimali</span><span class="sxs-lookup"><span data-stu-id="2edaf-163">Read more about the optimal button size</span></span>](interactable-object.md)<br>
        <br>
        <span data-ttu-id="2edaf-164">Per motivi tecnici, è consigliabile usare questa località con una sola implementazione necessaria: lo sviluppatore dovrà bloccare il menu una volta che l'utente si avvicina a una mano all'altra.</span><span class="sxs-lookup"><span data-stu-id="2edaf-164">For technical reasons, we recommend this location with one required implementation: the developer will need to freeze the menu once the user's opposite hand gets close to interacting with it.</span></span> <span data-ttu-id="2edaf-165">In questo modo si eviterà che nervosismo si sovrappongano e anche un targeting più rapido dei pulsanti.</span><span class="sxs-lookup"><span data-stu-id="2edaf-165">This will avoid jitteriness from overlapping hands and also allows for a faster targeting of the buttons.</span></span><br>
        <br>
        <span data-ttu-id="2edaf-166">Le fotocamere HoloLens 2 identificano le mani accuratamente quando sono separate tra loro.</span><span class="sxs-lookup"><span data-stu-id="2edaf-166">HoloLens 2 cameras identify hands accurately when they're separate from each other.</span></span> <span data-ttu-id="2edaf-167">Qualsiasi mano sovrapposta può causare la disattivazione dei menu a mano dalla posizione di ancoraggio.</span><span class="sxs-lookup"><span data-stu-id="2edaf-167">Any overlapping hands can cause hand menus move away from the anchor location.</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="menu-positions-that-arent-recommended"></a><span data-ttu-id="2edaf-168">Posizioni dei menu non consigliate</span><span class="sxs-lookup"><span data-stu-id="2edaf-168">Menu positions that aren't recommended</span></span>

<span data-ttu-id="2edaf-169">La ricerca degli utenti è stata eseguita con layout e percorsi di menu diversi. i percorsi dei menu seguenti **non sono consigliati**. trovare i svantaggi di ogni studio di seguito:</span><span class="sxs-lookup"><span data-stu-id="2edaf-169">We have done user research with different menus layouts and locations, the following menu locations are **NOT recommended**, find the cons of each study below:</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="2edaf-170">![Sopra ARM](images/AboveArm.gif)</span><span class="sxs-lookup"><span data-stu-id="2edaf-170">![Above arm](images/AboveArm.gif)</span></span><br>
        <span data-ttu-id="2edaf-171">**Sopra il ARM**</span><span class="sxs-lookup"><span data-stu-id="2edaf-171">**Above the arm**</span></span><br>
        <span data-ttu-id="2edaf-172">1-difficile mantenere il rilevamento della mano corretta</span><span class="sxs-lookup"><span data-stu-id="2edaf-172">1 - Difficult to maintain good hand tracking</span></span><br>
        <span data-ttu-id="2edaf-173">2-causa la fatica dell'utente a causa di una posizione non naturale</span><span class="sxs-lookup"><span data-stu-id="2edaf-173">2 - Causes user fatigue because of unnatural position</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="2edaf-174">![Sopra le dita](images/AboveFingers.gif)</span><span class="sxs-lookup"><span data-stu-id="2edaf-174">![Above fingers](images/AboveFingers.gif)</span></span><br>
        <span data-ttu-id="2edaf-175">**Sopra le dita**</span><span class="sxs-lookup"><span data-stu-id="2edaf-175">**Above fingers**</span></span><br>
        <span data-ttu-id="2edaf-176">affaticamento a 1 mano a causa del mantenimento della mano da molto tempo</span><span class="sxs-lookup"><span data-stu-id="2edaf-176">1 - Hand fatigue because of holding out hand for a long time</span></span><br>
        <span data-ttu-id="2edaf-177">problemi di rilevamento a due mani sull'indice e le dita centrali</span><span class="sxs-lookup"><span data-stu-id="2edaf-177">2 - Hand tracking issues on index and middle fingers</span></span>
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        <span data-ttu-id="2edaf-178">![Sopra il centro Palm](images/handCenter.gif)</span><span class="sxs-lookup"><span data-stu-id="2edaf-178">![Above center palm](images/handCenter.gif)</span></span><br>
        <span data-ttu-id="2edaf-179">**Sopra-centro Palm**</span><span class="sxs-lookup"><span data-stu-id="2edaf-179">**Above-center palm**</span></span><br>
        <span data-ttu-id="2edaf-180">problemi di rilevamento a una mano a causa di una sovrapposizione delle mani</span><span class="sxs-lookup"><span data-stu-id="2edaf-180">1 - Hand tracking issues because of overlapping hands</span></span><br>
        <span data-ttu-id="2edaf-181">affaticamento a due mani a causa del tempo di attesa lungo per interagire con i menu</span><span class="sxs-lookup"><span data-stu-id="2edaf-181">2 - Hand fatigue because of holding hands for long time to interact with menus</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="2edaf-182">![Parte superiore ](images/TopFingerTip.gif) della parte superiore **della mano**</span><span class="sxs-lookup"><span data-stu-id="2edaf-182">![Top Fingertip](images/TopFingerTip.gif) **Top fingertip**</span></span><br>
        <span data-ttu-id="2edaf-183">problemi di rilevamento a una mano</span><span class="sxs-lookup"><span data-stu-id="2edaf-183">1 - Hand tracking issues</span></span><br>
        <span data-ttu-id="2edaf-184">un affaticamento a 2 mano da tenere sotto la postura normale</span><span class="sxs-lookup"><span data-stu-id="2edaf-184">2 - Hand fatigue from holding hand above normal posture</span></span><br>
        <span data-ttu-id="2edaf-185">3-problemi durante la pressione di pulsanti con altre dita per errore a causa di spazio limitato tra le dita</span><span class="sxs-lookup"><span data-stu-id="2edaf-185">3 - Issues pressing buttons with other fingers by accident because of limited space between fingers</span></span>
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        <span data-ttu-id="2edaf-186">![Back of the ARM](images/BackOfTheArm.gif)</span><span class="sxs-lookup"><span data-stu-id="2edaf-186">![Back of the Arm](images/BackOfTheArm.gif)</span></span><br>
        <span data-ttu-id="2edaf-187">**Back of the ARM**</span><span class="sxs-lookup"><span data-stu-id="2edaf-187">**Back of the arm**</span></span><br>
        <span data-ttu-id="2edaf-188">1-è possibile attivare il pulsante Home per errore</span><span class="sxs-lookup"><span data-stu-id="2edaf-188">1 - Can trigger home button by accident</span></span><br>
        <span data-ttu-id="2edaf-189">2-posizione naturale o comoda</span><span class="sxs-lookup"><span data-stu-id="2edaf-189">2 - Not a natural or comfortable position</span></span>
    :::column-end:::
    :::column:::
    :::column-end:::
:::row-end:::

<br>

---

## <a name="hand-menu-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="2edaf-190">Menu a mano in MRTK (Mixed Reality Toolkit) per Unity</span><span class="sxs-lookup"><span data-stu-id="2edaf-190">Hand menu in MRTK (Mixed Reality Toolkit) for Unity</span></span>

<span data-ttu-id="2edaf-191">**[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** fornisce gli script e le scene di esempio per il menu a mano.</span><span class="sxs-lookup"><span data-stu-id="2edaf-191">**[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** provides scripts and example scenes for the hand menu.</span></span> <span data-ttu-id="2edaf-192">Lo script del Risolutore HandConstraintPalmUp consente di associare qualsiasi oggetto a mani con diverse opzioni configurabili.</span><span class="sxs-lookup"><span data-stu-id="2edaf-192">The HandConstraintPalmUp solver script allows you to attach any objects to the hands with various configurable options.</span></span> <span data-ttu-id="2edaf-193">Gli esempi di menu della mano di MRTK includono opzioni utili, ad esempio il requisito della palma piatta e lo sguardo per impedire l'attivazione falsa.</span><span class="sxs-lookup"><span data-stu-id="2edaf-193">MRTK's hand menu examples include useful options such as flat palm and gaze requirement for preventing false activation.</span></span>

* [<span data-ttu-id="2edaf-194">Documenti menu a mano</span><span class="sxs-lookup"><span data-stu-id="2edaf-194">Hand Menu Documentations</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_HandMenu.html)
* [<span data-ttu-id="2edaf-195">Scena di esempio del menu a mano</span><span class="sxs-lookup"><span data-stu-id="2edaf-195">Hand Menu Example Scene</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Assets/MRTK/Examples/Demos/HandTracking/Scenes/HandMenuExamples.unity)

<span data-ttu-id="2edaf-196">È possibile provare esempi di menu a mano in HoloLens 2 con l'App Hub esempi di MRTK.</span><span class="sxs-lookup"><span data-stu-id="2edaf-196">You can try hand menu examples in HoloLens 2 with MRTK Examples Hub app.</span></span> 
* [<span data-ttu-id="2edaf-197">Scena menu a mano nell'hub esempi MRTK</span><span class="sxs-lookup"><span data-stu-id="2edaf-197">Hand Menu Scene in MRTK Examples Hub</span></span>](https://www.microsoft.com/en-us/p/mrtk-examples-hub/9mv8c39l2sj4?activetab=pivot:overviewtab)

<br>

---

## <a name="see-also"></a><span data-ttu-id="2edaf-198">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="2edaf-198">See also</span></span>

* [<span data-ttu-id="2edaf-199">Cursori</span><span class="sxs-lookup"><span data-stu-id="2edaf-199">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="2edaf-200">Raggio della mano</span><span class="sxs-lookup"><span data-stu-id="2edaf-200">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="2edaf-201">Button</span><span class="sxs-lookup"><span data-stu-id="2edaf-201">Button</span></span>](button.md)
* [<span data-ttu-id="2edaf-202">Oggetto che supporta interazioni</span><span class="sxs-lookup"><span data-stu-id="2edaf-202">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="2edaf-203">Rettangolo di selezione e barra dell'app</span><span class="sxs-lookup"><span data-stu-id="2edaf-203">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="2edaf-204">Manipolazione</span><span class="sxs-lookup"><span data-stu-id="2edaf-204">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="2edaf-205">Menu a mano</span><span class="sxs-lookup"><span data-stu-id="2edaf-205">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="2edaf-206">Menu adiacente</span><span class="sxs-lookup"><span data-stu-id="2edaf-206">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="2edaf-207">Raccolta di oggetti</span><span class="sxs-lookup"><span data-stu-id="2edaf-207">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="2edaf-208">Comando vocale</span><span class="sxs-lookup"><span data-stu-id="2edaf-208">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="2edaf-209">Tastiera</span><span class="sxs-lookup"><span data-stu-id="2edaf-209">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="2edaf-210">Descrizione comando</span><span class="sxs-lookup"><span data-stu-id="2edaf-210">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="2edaf-211">Slate</span><span class="sxs-lookup"><span data-stu-id="2edaf-211">Slate</span></span>](slate.md)
* [<span data-ttu-id="2edaf-212">Dispositivo di scorrimento</span><span class="sxs-lookup"><span data-stu-id="2edaf-212">Slider</span></span>](slider.md)
* [<span data-ttu-id="2edaf-213">Shader</span><span class="sxs-lookup"><span data-stu-id="2edaf-213">Shader</span></span>](shader.md)
* [<span data-ttu-id="2edaf-214">Billboarding e tag-along</span><span class="sxs-lookup"><span data-stu-id="2edaf-214">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="2edaf-215">Visualizzazione dello stato</span><span class="sxs-lookup"><span data-stu-id="2edaf-215">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="2edaf-216">Magnetismo di superficie</span><span class="sxs-lookup"><span data-stu-id="2edaf-216">Surface magnetism</span></span>](surface-magnetism.md)

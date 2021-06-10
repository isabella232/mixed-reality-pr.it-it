---
title: Menu a mano
description: I menu a mano consentono agli utenti di visualizzare rapidamente l'interfaccia utente collegata a mano per le funzioni usate di frequente.
author: nbarragan23
ms.author: nobarr
ms.date: 08/27/2019
ms.topic: article
keywords: hand, menu, button, quick access, layout, mixed reality headset, windows mixed reality headset, virtual reality headset, HoloLens, MRTK, Mixed Reality Toolkit
ms.openlocfilehash: f007ada2d7a594f141d30a3619d4d80ac74621d8
ms.sourcegitcommit: 9ae76b339968f035c703d9c1fe57ddecb33198e3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/27/2021
ms.locfileid: "110600330"
---
# <a name="hand-menu"></a><span data-ttu-id="fa747-104">Menu a mano</span><span class="sxs-lookup"><span data-stu-id="fa747-104">Hand menu</span></span>

![Posizione sul lato Ulnar](images/UX_Hero_HandMenu.jpg)

<span data-ttu-id="fa747-106">Il menu a forma di mano è uno dei modelli di esperienza utente più univoci in HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="fa747-106">The hand menu is one of the most unique UX patterns in HoloLens 2.</span></span> <span data-ttu-id="fa747-107">Consente di visualizzare rapidamente l'interfaccia utente collegata a mano.</span><span class="sxs-lookup"><span data-stu-id="fa747-107">It allows you to quickly bring up hand-attached UI.</span></span> <span data-ttu-id="fa747-108">Poiché è accessibile in qualsiasi momento e può essere visualizzato e nascosto facilmente, è ideale per le azioni rapide.</span><span class="sxs-lookup"><span data-stu-id="fa747-108">Since it's accessible anytime and can be shown and hidden easily, it's great for quick actions.</span></span>

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4AJAg]

<span data-ttu-id="fa747-109">Le procedure consigliate per l'uso dei menu a mano sono disponibili nell'elenco seguente.</span><span class="sxs-lookup"><span data-stu-id="fa747-109">You'll find our recommended best practices for working with hand menus in the list below.</span></span> <span data-ttu-id="fa747-110">È anche possibile trovare una scena di esempio che illustra il menu a mano in [MRTK.](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/hand-menu)</span><span class="sxs-lookup"><span data-stu-id="fa747-110">You can also find an example scene demonstrating the hand menu in [MRTK](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/hand-menu).</span></span>

<br>

---

## <a name="best-practices"></a><span data-ttu-id="fa747-111">Procedure consigliate</span><span class="sxs-lookup"><span data-stu-id="fa747-111">Best practices</span></span>

<span data-ttu-id="fa747-112">**Mantenere ridotto il numero di pulsanti**</span><span class="sxs-lookup"><span data-stu-id="fa747-112">**Keep the number of buttons small**</span></span> 

<span data-ttu-id="fa747-113">A causa della distanza vicina tra un menu bloccato a mano e gli occhi e della tendenza degli utenti a concentrarsi su un'area visiva relativamente piccola in qualsiasi momento (il cono di vista attenzionale è di circa 10 gradi), è consigliabile mantenere ridotto il numero di pulsanti.</span><span class="sxs-lookup"><span data-stu-id="fa747-113">Because of the close distance between a hand-locked menu and the eyes, and the tendency for users to focus on a relatively small visual area at any time (the attentional cone of vision is roughly 10 degrees), we recommend keeping the number of buttons small.</span></span> <span data-ttu-id="fa747-114">In base all'esplorazione, una colonna con tre pulsanti funziona bene mantenendo tutto il contenuto all'interno del campo di visualizzazione anche quando un utente sposta le mani al centro della fov.</span><span class="sxs-lookup"><span data-stu-id="fa747-114">Based on our exploration, one column with three buttons works well by keeping all the content within the field of view (FOV) even when a user moves their hands to the center of the FOV.</span></span> 

<span data-ttu-id="fa747-115">**Usare il menu a mano per un'azione rapida**</span><span class="sxs-lookup"><span data-stu-id="fa747-115">**Use hand menu for quick action**</span></span> 

<span data-ttu-id="fa747-116">Alzare un arm e mantenere la posizione potrebbe facilmente causare l'affaticamento del mano.</span><span class="sxs-lookup"><span data-stu-id="fa747-116">Raising an arm and maintaining the position could easily cause arm fatigue.</span></span> <span data-ttu-id="fa747-117">Usare un metodo bloccato a mano per il menu che richiede una breve interazione.</span><span class="sxs-lookup"><span data-stu-id="fa747-117">Use a hand-locked method for the menu requiring a short interaction.</span></span> <span data-ttu-id="fa747-118">Se il menu è complesso e richiede tempi di interazione estesi, è consigliabile usare il blocco del mondo o il blocco del corpo.</span><span class="sxs-lookup"><span data-stu-id="fa747-118">If your menu is complex and requires extended interaction times, consider using world-locked or body-locked instead.</span></span> 

<span data-ttu-id="fa747-119">**Angolo pulsante/pannello**</span><span class="sxs-lookup"><span data-stu-id="fa747-119">**Button / Panel angle**</span></span>

<span data-ttu-id="fa747-120">I menu devono essere posizionati verso la fronte opposta e al centro della testa: ciò consente un movimento naturale della mano per interagire con il menu con la mano opposta ed evitare eventuali posizioni della mano difficili o difficili da toccare quando si toccano i pulsanti.</span><span class="sxs-lookup"><span data-stu-id="fa747-120">Menus should billboard towards the opposite shoulder and middle of the head: This allows a natural hand move to interact with the menu with the opposite hand and avoids any awkward or uncomfortable hand positions when touching buttons.</span></span> 

<span data-ttu-id="fa747-121">**Valutare la possibilità di supportare operazioni a una mano o a mani libere**</span><span class="sxs-lookup"><span data-stu-id="fa747-121">**Consider supporting one-handed or hands-free operation**</span></span>

<span data-ttu-id="fa747-122">Non presupporre che entrambe le mani dell'utente siano sempre disponibili.</span><span class="sxs-lookup"><span data-stu-id="fa747-122">Don't assume both of the user's hands are always available.</span></span> <span data-ttu-id="fa747-123">Prendere in considerazione un'ampia gamma di contesti quando una o entrambe le mani non sono disponibili e assicurarsi che la progettazione account per tali situazioni.</span><span class="sxs-lookup"><span data-stu-id="fa747-123">Consider a wide range of contexts when one or both hands aren't available, and make sure your design accounts for those situations.</span></span> <span data-ttu-id="fa747-124">Per supportare un menu con una mano, è possibile provare a eseguire la transizione del posizionamento del menu da mano bloccata a bloccata al mondo quando la mano capovolge (si inverte il palmo).</span><span class="sxs-lookup"><span data-stu-id="fa747-124">To support a one-handed hand menu, you can try transitioning the menu placement from hand-locked to world-locked when the hand flips (goes palm down).</span></span> <span data-ttu-id="fa747-125">Per gli scenari senza mani, è consigliabile usare un comando vocale per richiamare il menu a mano.</span><span class="sxs-lookup"><span data-stu-id="fa747-125">For hands-free scenarios, consider using a voice command to invoke the hand menu.</span></span>

<span data-ttu-id="fa747-126">**Evitare di aggiungere pulsanti accanto al vicino (pulsante Pagina iniziale del sistema)**</span><span class="sxs-lookup"><span data-stu-id="fa747-126">**Avoid adding buttons near the wrist (system home button)**</span></span>

<span data-ttu-id="fa747-127">Se i pulsanti del menu a mano sono posizionati troppo vicino al pulsante Pagina iniziale, è possibile che venga attivato accidentalmente durante l'interazione con il menu a mano.</span><span class="sxs-lookup"><span data-stu-id="fa747-127">If the hand menu buttons are placed too close to the home button, it may accidentally trigger while interacting with the hand menu.</span></span>

<br>

## <a name="hand-menu-with-large-and-complex-ui-controls"></a><span data-ttu-id="fa747-128">Menu a mano con controlli dell'interfaccia utente grandi e complessi</span><span class="sxs-lookup"><span data-stu-id="fa747-128">Hand menu with large and complex UI controls</span></span>

<img src="images/HandMenu_SizeExample.png" alt="HoloLens perspective of a menu system that always faces the user" width="940px">
<span data-ttu-id="fa747-129">È consigliabile limitare il numero di pulsanti o controlli dell'interfaccia utente nei menu collegati manualmente.</span><span class="sxs-lookup"><span data-stu-id="fa747-129">It's recommended to limit the number of buttons or UI controls on hand-attached menus.</span></span> <span data-ttu-id="fa747-130">Questo perché l'interazione estesa con un numero elevato di elementi dell'interfaccia utente può causare problemi di arm.</span><span class="sxs-lookup"><span data-stu-id="fa747-130">This is because extended interaction with a large number of UI elements can cause arm fatigue.</span></span> <span data-ttu-id="fa747-131">Se l'esperienza richiede un menu di grandi dimensioni, fornire all'utente un modo semplice per bloccare il menu.</span><span class="sxs-lookup"><span data-stu-id="fa747-131">If your experience requires a large menu, provide an easy way for the user to world lock the menu.</span></span> <span data-ttu-id="fa747-132">Una tecnica consigliata consiste nel bloccare il mondo e quindi nel menu quando la mano scende o si allontana dall'utente.</span><span class="sxs-lookup"><span data-stu-id="fa747-132">One technique we recommend is to world-lock then menu when the hand drops or flips away from the user.</span></span> <span data-ttu-id="fa747-133">Una seconda tecnica consiste nel consentire all'utente di afferrare direttamente il menu con l'altra mano.</span><span class="sxs-lookup"><span data-stu-id="fa747-133">A second technique is to allow the user to directly grab the menu with the other hand.</span></span> <span data-ttu-id="fa747-134">Quando l'utente rilascia il menu, il menu dovrebbe bloccarsi a livello mondiale.</span><span class="sxs-lookup"><span data-stu-id="fa747-134">When the user releases the menu, the menu should world lock.</span></span> <span data-ttu-id="fa747-135">In questo modo, un utente può interagire con vari elementi dell'interfaccia utente in modo semplice e sicuro per un lungo periodo di tempo.</span><span class="sxs-lookup"><span data-stu-id="fa747-135">This way, a user can interact with various UI elements comfortably and confidently over an extended period of time.</span></span> 

<span data-ttu-id="fa747-136">Quando il menu è bloccato a livello mondiale, assicurarsi di fornire un modo per spostare il menu e chiuderlo quando non è più necessario.</span><span class="sxs-lookup"><span data-stu-id="fa747-136">When the menu is world-locked, make sure to provide a way to move the menu, and close the menu when it's no longer needed.</span></span> <span data-ttu-id="fa747-137">Rendere il menu mobile fornendo punti di controllo sui lati o nella parte superiore del menu.</span><span class="sxs-lookup"><span data-stu-id="fa747-137">Make the menu movable by providing handles on the sides or top of menu.</span></span> <span data-ttu-id="fa747-138">Aggiungere un pulsante chiudi per consentire la chiusura del menu.</span><span class="sxs-lookup"><span data-stu-id="fa747-138">Add a close button to allow the menu to close.</span></span> <span data-ttu-id="fa747-139">Consentire il ricollegare il menu alla mano quando la mano dell'utente si trova di fronte all'utente.</span><span class="sxs-lookup"><span data-stu-id="fa747-139">Allow for the menu to reattach to the hand when the user hand faces the user.</span></span> <span data-ttu-id="fa747-140">È anche consigliabile che gli utenti fissano la mano per impedire attivazioni false (vedere di seguito).</span><span class="sxs-lookup"><span data-stu-id="fa747-140">We also recommend requiring that the users gaze at their hand to prevent false activations (see below).</span></span>

<span data-ttu-id="fa747-141">**Menu di grandi dimensioni che mostra un problema di usabilità**</span><span class="sxs-lookup"><span data-stu-id="fa747-141">**Large menu that shows a usability issue**</span></span>

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4AOPx]

<span data-ttu-id="fa747-142">**Menu a portata di mano bloccato**</span><span class="sxs-lookup"><span data-stu-id="fa747-142">**World-locked menu on hand drop**</span></span>

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4AGZi]

<span data-ttu-id="fa747-143">**Afferrare manualmente & il pull per bloccare il mondo nel menu**</span><span class="sxs-lookup"><span data-stu-id="fa747-143">**Manual grab & pull to world-lock the menu**</span></span>

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4AJAf]

## <a name="how-to-prevent-false-activation"></a><span data-ttu-id="fa747-144">Come impedire l'attivazione falsa</span><span class="sxs-lookup"><span data-stu-id="fa747-144">How to prevent false activation</span></span>

<span data-ttu-id="fa747-145">Se si usa solo palm-up come evento per attivare il menu della mano, è possibile che venga visualizzato accidentalmente quando non è necessario (falso positivo), perché le persone spostano le mani intenzionalmente (per la comunicazione e la manipolazione degli oggetti) e accidentalmente.</span><span class="sxs-lookup"><span data-stu-id="fa747-145">If you use just palm-up as an event to trigger the hand menu, it may accidentally appear when you don't need it (false-positive), because people move their hands both intentionally (for communication and object manipulation) and unintentionally.</span></span> <span data-ttu-id="fa747-146">Per ridurre le attivazioni false, aggiungi un passaggio aggiuntivo oltre all'evento palm-up per richiamare il menu della mano (ad esempio le dita completamente aperte o l'utente che guarda intenzionalmente la mano).</span><span class="sxs-lookup"><span data-stu-id="fa747-146">To reduce false activations, add an extra step besides the palm-up event to invoke the hand menu (such as fully opened fingers, or the user intentionally gazing at their hand).</span></span>

<span data-ttu-id="fa747-147">**Require Flat Palm**</span><span class="sxs-lookup"><span data-stu-id="fa747-147">**Require Flat Palm**</span></span>

<span data-ttu-id="fa747-148">Richiedendo una mano aperta piana, è possibile impedire l'attivazione falsa che potrebbe verificarsi quando l'utente modifica oggetti o movimenti durante la comunicazione all'interno di un ambiente.</span><span class="sxs-lookup"><span data-stu-id="fa747-148">By requiring a flat open hand, you can prevent false activation that might occur as the user manipulates objects or gestures while communicating within an environment.</span></span> 

<span data-ttu-id="fa747-149">**Richiedi sguardo fisso**</span><span class="sxs-lookup"><span data-stu-id="fa747-149">**Require Gaze**</span></span>

<span data-ttu-id="fa747-150">Richiedendo all'utente di guardare la mano (con sguardo fisso o sguardo con la testa), impedisce attivazioni false perché l'utente deve indirizzare l'attenzione alla mano come passaggio di attivazione secondario (con una soglia di distanza regolabile usata per consentire il comfort dell'utente).</span><span class="sxs-lookup"><span data-stu-id="fa747-150">By requiring the user to gaze at their hand (either with eye gaze or head gaze), it prevents false activations because of the user having to direct their attention to the hand as a secondary activation step (with a tunable distance threshold used to allow for user comfort).</span></span>  

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4Asn4]

---

## <a name="hand-menu-placement-best-practices"></a><span data-ttu-id="fa747-151">Procedure consigliate per il posizionamento dei menu a mano</span><span class="sxs-lookup"><span data-stu-id="fa747-151">Hand menu placement best practices</span></span>

<span data-ttu-id="fa747-152">Nell'anatomia umana, l'ulnar erre è un'esca che si trova vicino all'ulna.</span><span class="sxs-lookup"><span data-stu-id="fa747-152">In human anatomy, the ulnar nerve is a nerve that runs near the ulna bone.</span></span> <span data-ttu-id="fa747-153">L'ulna è un longino che si trova nell'avambraccio che si estende dal gomito al dito più piccolo.</span><span class="sxs-lookup"><span data-stu-id="fa747-153">The ulna is a long bone found in the forearm that stretches from the elbow to the smallest finger.</span></span>

<span data-ttu-id="fa747-154">Di seguito sono riportati due posizionamenti consigliati in base alle esplorazioni:</span><span class="sxs-lookup"><span data-stu-id="fa747-154">Below are two recommended placements based on our explorations:</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="fa747-155">![Posizione della mano laterale Ulnar all'interno del palmo](images/UlnarSideHandMenu.gif)</span><span class="sxs-lookup"><span data-stu-id="fa747-155">![Ulnar side hand location inside palm](images/UlnarSideHandMenu.gif)</span></span><br>
        <span data-ttu-id="fa747-156">**A. Ulnar inside palm**</span><span class="sxs-lookup"><span data-stu-id="fa747-156">**A. Ulnar inside palm**</span></span><br>
        <span data-ttu-id="fa747-157">Questa posizione è affidabile perché le mani non si sovrappongono.</span><span class="sxs-lookup"><span data-stu-id="fa747-157">This position is reliable because the hands don't overlap each other.</span></span> <span data-ttu-id="fa747-158">Questo è fondamentale per il rilevamento e il rilevamento delle mani accurati.</span><span class="sxs-lookup"><span data-stu-id="fa747-158">This is critical for accurate hand detection and tracking.</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="fa747-159">![Posizione sul lato Ulnar sopra la mano](images/UlnarAboveHandMenu.gif)</span><span class="sxs-lookup"><span data-stu-id="fa747-159">![Ulnar side hand location above hand](images/UlnarAboveHandMenu.gif)</span></span><br>
        <span data-ttu-id="fa747-160">**B. Ulnar sopra la mano**</span><span class="sxs-lookup"><span data-stu-id="fa747-160">**B. Ulnar above hand**</span></span><br>
        <span data-ttu-id="fa747-161">Questa posizione è comoda per gli utenti perché non è necessario alzare troppo le mani per interagire con il menu a mano.</span><span class="sxs-lookup"><span data-stu-id="fa747-161">This location is comfortable for users because they don't need to raise their arm too much to interact with the hand menu.</span></span> <span data-ttu-id="fa747-162">È consigliabile posizionare i menu **13 cm** sopra il palmo e allineare i pulsanti all'interno del palmo ulnar.</span><span class="sxs-lookup"><span data-stu-id="fa747-162">We recommend placing menus **13 cm** above the palm and align the buttons inside the ulnar palm.</span></span> [<span data-ttu-id="fa747-163">Altre informazioni sulle dimensioni ottimali dei pulsanti</span><span class="sxs-lookup"><span data-stu-id="fa747-163">Read more about the optimal button size</span></span>](interactable-object.md)<br>
        <br>
        <span data-ttu-id="fa747-164">Per motivi tecnici, è consigliabile usare questa posizione con un'implementazione obbligatoria: lo sviluppatore dovrà bloccare il menu quando la mano opposta dell'utente si avvicina all'interazione con esso.</span><span class="sxs-lookup"><span data-stu-id="fa747-164">For technical reasons, we recommend this location with one required implementation: the developer will need to freeze the menu once the user's opposite hand gets close to interacting with it.</span></span> <span data-ttu-id="fa747-165">In questo modo si evita l'instabilità delle mani sovrapposte e si consente anche una scelta più rapida dei pulsanti.</span><span class="sxs-lookup"><span data-stu-id="fa747-165">This will avoid jitteriness from overlapping hands and also allows for a faster targeting of the buttons.</span></span><br>
        <br>
        <span data-ttu-id="fa747-166">HoloLens 2 fotocamere identificano le mani in modo accurato quando sono separate l'una dall'altra.</span><span class="sxs-lookup"><span data-stu-id="fa747-166">HoloLens 2 cameras identify hands accurately when they're separate from each other.</span></span> <span data-ttu-id="fa747-167">Eventuali mani sovrapposte possono far sì che i menu delle mani si spostino dalla posizione di ancoraggio.</span><span class="sxs-lookup"><span data-stu-id="fa747-167">Any overlapping hands can cause hand menus move away from the anchor location.</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="menu-positions-that-arent-recommended"></a><span data-ttu-id="fa747-168">Posizioni dei menu non consigliate</span><span class="sxs-lookup"><span data-stu-id="fa747-168">Menu positions that aren't recommended</span></span>

<span data-ttu-id="fa747-169">Sono state eseguite ricerche degli utenti con layout e posizioni di menu diversi. Le posizioni di menu seguenti **NON** sono consigliate. Trovare i contro di ogni studio di seguito:</span><span class="sxs-lookup"><span data-stu-id="fa747-169">We have done user research with different menus layouts and locations, the following menu locations are **NOT recommended**, find the cons of each study below:</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="fa747-170">![Sopra arm](images/AboveArm.gif)</span><span class="sxs-lookup"><span data-stu-id="fa747-170">![Above arm](images/AboveArm.gif)</span></span><br>
        <span data-ttu-id="fa747-171">**Sopra il arm**</span><span class="sxs-lookup"><span data-stu-id="fa747-171">**Above the arm**</span></span><br>
        <span data-ttu-id="fa747-172">1 - Difficile mantenere un buon tracciamento delle mani</span><span class="sxs-lookup"><span data-stu-id="fa747-172">1 - Difficult to maintain good hand tracking</span></span><br>
        <span data-ttu-id="fa747-173">2 - Causa l'affaticamento dell'utente a causa di una posizione non naturale</span><span class="sxs-lookup"><span data-stu-id="fa747-173">2 - Causes user fatigue because of unnatural position</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="fa747-174">![Sopra le dita](images/AboveFingers.gif)</span><span class="sxs-lookup"><span data-stu-id="fa747-174">![Above fingers](images/AboveFingers.gif)</span></span><br>
        <span data-ttu-id="fa747-175">**Sopra le dita**</span><span class="sxs-lookup"><span data-stu-id="fa747-175">**Above fingers**</span></span><br>
        <span data-ttu-id="fa747-176">1 - Affaticamento della mano a causa della lunga attesa</span><span class="sxs-lookup"><span data-stu-id="fa747-176">1 - Hand fatigue because of holding out hand for a long time</span></span><br>
        <span data-ttu-id="fa747-177">2 - Problemi di tracciamento della mano sull'indice e sulle dita medie</span><span class="sxs-lookup"><span data-stu-id="fa747-177">2 - Hand tracking issues on index and middle fingers</span></span>
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        <span data-ttu-id="fa747-178">![Sopra il palmo centrale](images/handCenter.gif)</span><span class="sxs-lookup"><span data-stu-id="fa747-178">![Above center palm](images/handCenter.gif)</span></span><br>
        <span data-ttu-id="fa747-179">**Palmo sopra il centro**</span><span class="sxs-lookup"><span data-stu-id="fa747-179">**Above-center palm**</span></span><br>
        <span data-ttu-id="fa747-180">1 - Problemi di tracciamento della mano a causa della sovrapposizione delle mani</span><span class="sxs-lookup"><span data-stu-id="fa747-180">1 - Hand tracking issues because of overlapping hands</span></span><br>
        <span data-ttu-id="fa747-181">2 - Affaticamento della mano a causa della tenere le mani per molto tempo per interagire con i menu</span><span class="sxs-lookup"><span data-stu-id="fa747-181">2 - Hand fatigue because of holding hands for long time to interact with menus</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="fa747-182">![Punta del dito ](images/TopFingerTip.gif) **superiore Punta del dito superiore**</span><span class="sxs-lookup"><span data-stu-id="fa747-182">![Top Fingertip](images/TopFingerTip.gif) **Top fingertip**</span></span><br>
        <span data-ttu-id="fa747-183">1 - Problemi di tracciamento della mano</span><span class="sxs-lookup"><span data-stu-id="fa747-183">1 - Hand tracking issues</span></span><br>
        <span data-ttu-id="fa747-184">2 - Affaticamento della mano dalla mano al di sopra della normale postura</span><span class="sxs-lookup"><span data-stu-id="fa747-184">2 - Hand fatigue from holding hand above normal posture</span></span><br>
        <span data-ttu-id="fa747-185">3 - Problemi di pressione accidentale di pulsanti con altre dita a causa dello spazio limitato tra le dita</span><span class="sxs-lookup"><span data-stu-id="fa747-185">3 - Issues pressing buttons with other fingers by accident because of limited space between fingers</span></span>
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        <span data-ttu-id="fa747-186">![Parte posteriore dell'arm](images/BackOfTheArm.gif)</span><span class="sxs-lookup"><span data-stu-id="fa747-186">![Back of the Arm](images/BackOfTheArm.gif)</span></span><br>
        <span data-ttu-id="fa747-187">**Parte posteriore dell'arm**</span><span class="sxs-lookup"><span data-stu-id="fa747-187">**Back of the arm**</span></span><br>
        <span data-ttu-id="fa747-188">1 - Può attivare il pulsante Pagina iniziale per errore</span><span class="sxs-lookup"><span data-stu-id="fa747-188">1 - Can trigger home button by accident</span></span><br>
        <span data-ttu-id="fa747-189">2 - Posizione non naturale o comoda</span><span class="sxs-lookup"><span data-stu-id="fa747-189">2 - Not a natural or comfortable position</span></span>
    :::column-end:::
    :::column:::
    :::column-end:::
:::row-end:::

<br>

---

## <a name="hand-menu-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="fa747-190">Menu mano in MRTK (Mixed Reality Toolkit) per Unity</span><span class="sxs-lookup"><span data-stu-id="fa747-190">Hand menu in MRTK (Mixed Reality Toolkit) for Unity</span></span>

<span data-ttu-id="fa747-191">**[MRTK fornisce](https://github.com/Microsoft/MixedRealityToolkit-Unity)** script e scene di esempio per il menu a mano.</span><span class="sxs-lookup"><span data-stu-id="fa747-191">**[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** provides scripts and example scenes for the hand menu.</span></span> <span data-ttu-id="fa747-192">Lo script del risolutore HandConstraintPalmUp consente di collegare qualsiasi oggetto alle mani con varie opzioni configurabili.</span><span class="sxs-lookup"><span data-stu-id="fa747-192">The HandConstraintPalmUp solver script allows you to attach any objects to the hands with various configurable options.</span></span> <span data-ttu-id="fa747-193">Gli esempi di menu con la mano di MRTK includono opzioni utili, ad esempio il requisito del palmo piana e dello sguardo fisso per impedire l'attivazione falsa.</span><span class="sxs-lookup"><span data-stu-id="fa747-193">MRTK's hand menu examples include useful options such as flat palm and gaze requirement for preventing false activation.</span></span>

* [<span data-ttu-id="fa747-194">Documentazione del menu a mano</span><span class="sxs-lookup"><span data-stu-id="fa747-194">Hand Menu Documentations</span></span>](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/hand-menu)
* [<span data-ttu-id="fa747-195">Scena di esempio del menu a mano</span><span class="sxs-lookup"><span data-stu-id="fa747-195">Hand Menu Example Scene</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/main/Assets/MRTK/Examples/Demos/HandTracking/Scenes/HandMenuExamples.unity)

<span data-ttu-id="fa747-196">È possibile provare gli esempi di menu a mano in HoloLens 2'app Hub degli esempi di MRTK.</span><span class="sxs-lookup"><span data-stu-id="fa747-196">You can try hand menu examples in HoloLens 2 with MRTK Examples Hub app.</span></span>

* [<span data-ttu-id="fa747-197">Scena di menu manuale nell'hub degli esempi di MRTK</span><span class="sxs-lookup"><span data-stu-id="fa747-197">Hand Menu Scene in MRTK Examples Hub</span></span>](https://www.microsoft.com/p/mrtk-examples-hub/9mv8c39l2sj4?activetab=pivot:overviewtab)

<br>

---

## <a name="see-also"></a><span data-ttu-id="fa747-198">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="fa747-198">See also</span></span>

* [<span data-ttu-id="fa747-199">Cursori</span><span class="sxs-lookup"><span data-stu-id="fa747-199">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="fa747-200">Raggio della mano</span><span class="sxs-lookup"><span data-stu-id="fa747-200">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="fa747-201">Button</span><span class="sxs-lookup"><span data-stu-id="fa747-201">Button</span></span>](button.md)
* [<span data-ttu-id="fa747-202">Oggetto che supporta interazioni</span><span class="sxs-lookup"><span data-stu-id="fa747-202">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="fa747-203">Rettangolo di selezione e barra dell'app</span><span class="sxs-lookup"><span data-stu-id="fa747-203">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="fa747-204">Manipolazione</span><span class="sxs-lookup"><span data-stu-id="fa747-204">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="fa747-205">Menu a mano</span><span class="sxs-lookup"><span data-stu-id="fa747-205">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="fa747-206">Menu adiacente</span><span class="sxs-lookup"><span data-stu-id="fa747-206">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="fa747-207">Raccolta di oggetti</span><span class="sxs-lookup"><span data-stu-id="fa747-207">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="fa747-208">Comando vocale</span><span class="sxs-lookup"><span data-stu-id="fa747-208">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="fa747-209">Tastiera</span><span class="sxs-lookup"><span data-stu-id="fa747-209">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="fa747-210">Descrizione comando</span><span class="sxs-lookup"><span data-stu-id="fa747-210">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="fa747-211">Slate</span><span class="sxs-lookup"><span data-stu-id="fa747-211">Slate</span></span>](slate.md)
* [<span data-ttu-id="fa747-212">Dispositivo di scorrimento</span><span class="sxs-lookup"><span data-stu-id="fa747-212">Slider</span></span>](slider.md)
* [<span data-ttu-id="fa747-213">Shader</span><span class="sxs-lookup"><span data-stu-id="fa747-213">Shader</span></span>](shader.md)
* [<span data-ttu-id="fa747-214">Billboarding e tag-along</span><span class="sxs-lookup"><span data-stu-id="fa747-214">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="fa747-215">Visualizzazione dello stato</span><span class="sxs-lookup"><span data-stu-id="fa747-215">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="fa747-216">Magnetismo di superficie</span><span class="sxs-lookup"><span data-stu-id="fa747-216">Surface magnetism</span></span>](surface-magnetism.md)
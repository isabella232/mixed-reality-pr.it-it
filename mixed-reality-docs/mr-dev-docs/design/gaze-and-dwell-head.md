---
title: Puntamento con la testa e attesa
description: Introduzione a una panoramica del modello di input Head-sguardi e di residenza, inclusi scenari comuni e principi di progettazione.
author: hferrone
ms.author: v-hferrone
ms.date: 05/13/2019
ms.topic: article
keywords: Realtà mista, sguardo, abitato, interazione, progettazione, cuffie per realtà mista, cuffie per realtà mista, auricolare di realtà virtuale, HoloLens, MRTK, Toolkit Reality, UX, linee guida, visualizzazione elenco
ms.openlocfilehash: e70536b7247153979b8650ba1f5bcbe1a7cd08af
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/20/2021
ms.locfileid: "98582207"
---
# <a name="head-gaze-and-dwell"></a><span data-ttu-id="25c38-104">Puntamento con la testa e attesa</span><span class="sxs-lookup"><span data-stu-id="25c38-104">Head-gaze and dwell</span></span>

<span data-ttu-id="25c38-105">Quando le mani sono occupate con gli attrezzi e le parti, i movimenti possono risultare difficili o addirittura impossibili.</span><span class="sxs-lookup"><span data-stu-id="25c38-105">When hands are occupied with tools and parts, gestures can be tedious or impossible.</span></span> <span data-ttu-id="25c38-106">I comandi vocali, come i movimenti, possono non essere affidabili in determinati contesti, ad esempio in ambienti particolarmente rumorosi.</span><span class="sxs-lookup"><span data-stu-id="25c38-106">Voice commands, like gestures, can be unreliable in certain contexts, for example under excessively loud conditions.</span></span> <span data-ttu-id="25c38-107">Inoltre, l'uso della voce per controllare i computer, nonostante conosca una rapida diffusione, non è ancora una pratica comune ovunque.</span><span class="sxs-lookup"><span data-stu-id="25c38-107">Additionally, using voice to control computers isn't universally common, but it certainly is gaining steam!</span></span> <span data-ttu-id="25c38-108">Il modello di input puntamento con la testa e attesa offre un meccanismo già familiare e di facilissima gestione per lavorare in HoloLens con la testa sollevata e senza avere bisogno di usare le mani.</span><span class="sxs-lookup"><span data-stu-id="25c38-108">Head-gaze and dwell offers the most familiar and easy-to-master mechanism for working heads-up and hands-free on HoloLens.</span></span> <span data-ttu-id="25c38-109">Questo modello di input è anche affidabile al 100%, indipendentemente dall'interferenza di possibili rumori o da eventuali obblighi di restare in silenzio nell'ambiente operativo.</span><span class="sxs-lookup"><span data-stu-id="25c38-109">Additionally, head-gaze and dwell is 100% reliable independent of noise interference nor silence constraints in the operating environment.</span></span>

## <a name="scenarios"></a><span data-ttu-id="25c38-110">Scenari</span><span class="sxs-lookup"><span data-stu-id="25c38-110">Scenarios</span></span>

<span data-ttu-id="25c38-111">Il punto di partenza e l'abitazione sono ottimi negli scenari in cui le mani di una persona sono occupate da altre attività.</span><span class="sxs-lookup"><span data-stu-id="25c38-111">Head-gaze and dwell is great in scenarios where a person's hands are busy with other tasks.</span></span> <span data-ttu-id="25c38-112">Questa funzionalità è utile anche quando la voce non è del 100% affidabile o disponibile a causa di vincoli ambientali o sociali.</span><span class="sxs-lookup"><span data-stu-id="25c38-112">The feature is also useful when voice isn't 100% reliable or available because of environmental or social constraints.</span></span> <span data-ttu-id="25c38-113">Un buon esempio di questo tipo di situazioni è dato da una persona che indossa un dispositivo HoloLens per la sovrimpressione di informazioni di riferimento mentre ripara il motore di un'automobile.</span><span class="sxs-lookup"><span data-stu-id="25c38-113">A good example is a person wearing a HoloLens to overlay reference information while repairing a car engine.</span></span> <span data-ttu-id="25c38-114">Le sue mani sono occupate con gli attrezzi o devono sostenere il corpo mentre la persona si protende sul vano motore.</span><span class="sxs-lookup"><span data-stu-id="25c38-114">Their hands are busy with tools or supporting their body as they lean into the engine compartment.</span></span> <span data-ttu-id="25c38-115">L'autofficina è rumorosa a causa dei colpi e del ronzio costanti degli attrezzi da lavoro, quindi l'uso dei comandi vocali risulterebbe particolarmente difficoltoso.</span><span class="sxs-lookup"><span data-stu-id="25c38-115">The garage space is loud, with the constant banging and buzzing of tools, making voice commands difficult.</span></span> <span data-ttu-id="25c38-116">Head-sguardi e l'abitazione consentono all'utente che usa HoloLens di esplorare in modo sicuro il materiale di riferimento senza interrompere il flusso di lavoro.</span><span class="sxs-lookup"><span data-stu-id="25c38-116">Head-gaze and dwell allows the person using the HoloLens to confidently navigate their reference material without interrupting their workflow.</span></span> 

## <a name="device-support"></a><span data-ttu-id="25c38-117">Supporto di dispositivi</span><span class="sxs-lookup"><span data-stu-id="25c38-117">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="25c38-118"><strong>Modello di input</strong></span><span class="sxs-lookup"><span data-stu-id="25c38-118"><strong>Input model</strong></span></span></td>
        <td><span data-ttu-id="25c38-119"><a href="/hololens/hololens1-hardware"><strong>HoloLens (prima generazione)</strong></a></span><span class="sxs-lookup"><span data-stu-id="25c38-119"><a href="/hololens/hololens1-hardware"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="25c38-120"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="25c38-120"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="25c38-121"><a href="../discover/immersive-headset-hardware-details.md"><strong>Visori VR immersive</strong></a></span><span class="sxs-lookup"><span data-stu-id="25c38-121"><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="25c38-122">Puntamento con la testa e attesa</span><span class="sxs-lookup"><span data-stu-id="25c38-122">Head-gaze and dwell</span></span></td>
        <td><span data-ttu-id="25c38-123">✔️ Consigliato</span><span class="sxs-lookup"><span data-stu-id="25c38-123">✔️ Recommended</span></span></td>
        <td><span data-ttu-id="25c38-124">✔️ Consigliato</span><span class="sxs-lookup"><span data-stu-id="25c38-124">✔️ Recommended</span></span></td>
        <td><span data-ttu-id="25c38-125">✔️ Consigliato</span><span class="sxs-lookup"><span data-stu-id="25c38-125">✔️ Recommended</span></span></td>
    </tr>
</table>


## <a name="design-principles"></a><span data-ttu-id="25c38-126">Principi di progettazione</span><span class="sxs-lookup"><span data-stu-id="25c38-126">Design principles</span></span>

<span data-ttu-id="25c38-127">**Evitare di usare lo "sguardo fisso come un'arma"**</span><span class="sxs-lookup"><span data-stu-id="25c38-127">**Avoid "Gaze as a weapon"**</span></span>

<span data-ttu-id="25c38-128">Il puntamento con la testa e l'attesa richiedono un feedback visivo intuitivo, ma una mole eccessiva di feedback può produrre ansia.</span><span class="sxs-lookup"><span data-stu-id="25c38-128">Head-gaze and dwell requires visual feedback to be intuitive, but too much feedback can induce anxiety.</span></span> <span data-ttu-id="25c38-129">Il feedback dovrebbe aiutare gli utenti a conoscere gli elementi di destinazione, ma non a selezionarli in modo autonomo rispetto al loro scopo.</span><span class="sxs-lookup"><span data-stu-id="25c38-129">The feedback should help a user know what they're targeting, but not autoselect it against their intent.</span></span> <span data-ttu-id="25c38-130">Quando si leggono testo, icone ed etichette, è necessario fornire agli utenti il tempo necessario per l'assorbimento delle informazioni prima della selezione.</span><span class="sxs-lookup"><span data-stu-id="25c38-130">When reading text, icons, and labels, you need to provide users time to absorb the information before selecting.</span></span>
    
<span data-ttu-id="25c38-131">**Cercare di ottenere una velocità ottimale**</span><span class="sxs-lookup"><span data-stu-id="25c38-131">**Seek Goldilocks speed**</span></span>
    
<span data-ttu-id="25c38-132">Le interazioni di attesa possono avere timer diversi in base all'impatto sulla navigazione: le funzioni usate con maggiore frequenza in genere traggono vantaggio da tempi di riempimento più ridotti, mentre le funzioni più consequenziali possono trarre vantaggio da tempi di riempimento più lunghi.</span><span class="sxs-lookup"><span data-stu-id="25c38-132">Dwell interactions can have different timers based on impact of navigation - more frequently used functions will generally benefit from faster fill times, while more consequential functions may benefit from longer fill times.</span></span> <span data-ttu-id="25c38-133">Quando viene usato un effetto di riempimento per mostrare questi timer, le curve di animazione del colore di riempimento possono indurre positivamente la sensazione che i tempi di riempimento siano più rapidi.</span><span class="sxs-lookup"><span data-stu-id="25c38-133">When using a fill-effect to show these timers, animation curves of the fill color can positively influence a feeling of faster fill times.</span></span> <span data-ttu-id="25c38-134">Considera questi aspetti per consentire all'utente di prendere le sue decisioni scegliendo override della velocità di riempimento alta/media/bassa.</span><span class="sxs-lookup"><span data-stu-id="25c38-134">Consideration should be taken to enable user decision from fast/medium/slow fill speed overrides.</span></span>
    
<span data-ttu-id="25c38-135">**Evitare l'effetto yo-yo**</span><span class="sxs-lookup"><span data-stu-id="25c38-135">**Say no-no to yo-yo effect**</span></span>

<span data-ttu-id="25c38-136">L'effetto yo-yo è un modello di movimento Head scomodo che si verifica quando la posizione del contenuto e i controlli Head-sguardi/abitazione forzano la ricerca e la riduzione ripetuta degli utenti.</span><span class="sxs-lookup"><span data-stu-id="25c38-136">The yo-yo effect is an uncomfortable head movement pattern that happens when the content placement and head-gaze/dwell controls forces people to look up and down repeatedly.</span></span> <span data-ttu-id="25c38-137">Ad esempio, un elenco di spostamento con il pulsante di visualizzazione e il pulsante di disattivazione nella parte inferiore induce un ciclo di ricerca verso il basso, Cerca i risultati, Cerca giù per abitare e così via.</span><span class="sxs-lookup"><span data-stu-id="25c38-137">For example, a list nav with the head-gaze and dwell button at the bottom induces a loop of - look down to dwell, look up at results, look down to dwell, and so on.</span></span> <span data-ttu-id="25c38-138">Il modello risultante è scomodo, quindi è consigliabile posizionare i controlli di navigazione in una posizione centralizzata che richiede meno avanti e indietro.</span><span class="sxs-lookup"><span data-stu-id="25c38-138">The resulting pattern is uncomfortable, so we recommend placing navigation controls in a centralized location that requires less back-and-forth.</span></span> <span data-ttu-id="25c38-139">Il posizionamento dei pulsanti di permanenza in base ai relativi effetti diventa importante per la comodità.</span><span class="sxs-lookup"><span data-stu-id="25c38-139">Placement of dwell buttons based on their effects becomes important for comfort.</span></span>
<span data-ttu-id="25c38-140">s</span><span class="sxs-lookup"><span data-stu-id="25c38-140">s</span></span>
<br>

---

## <a name="ux-guidelines-and-best-practices"></a><span data-ttu-id="25c38-141">Linee guida e procedure consigliate per l'esperienza utente</span><span class="sxs-lookup"><span data-stu-id="25c38-141">UX Guidelines and best practices</span></span>

### <a name="target-sizes"></a><span data-ttu-id="25c38-142">Dimensioni delle destinazioni</span><span class="sxs-lookup"><span data-stu-id="25c38-142">Target sizes</span></span>

<span data-ttu-id="25c38-143">Per poter essere facilmente accessibili, le destinazioni Head-sguardi e di destinazione devono essere sufficientemente grandi da poter esaminare comodamente e contenere una sede alla destinazione per il tempo previsto.</span><span class="sxs-lookup"><span data-stu-id="25c38-143">To be easily accessible, head-gaze and dwell targets need to be large enough to look at comfortably, and hold one's head stable on the target for the prescribed time.</span></span> <span data-ttu-id="25c38-144">Per ottenere un'esperienza ottimale, è consigliabile utilizzare una dimensione minima di 2 gradi.</span><span class="sxs-lookup"><span data-stu-id="25c38-144">We recommend a minimum target size of 2 degrees to achieve the most comfortable experience.</span></span> 

### <a name="visual-feedback"></a><span data-ttu-id="25c38-145">Feedback visivo</span><span class="sxs-lookup"><span data-stu-id="25c38-145">Visual feedback</span></span>

<span data-ttu-id="25c38-146">Quando usi un riempimento radiale per rappresentare il timer di attesa, inizia dalla parte centrale del pulsante.</span><span class="sxs-lookup"><span data-stu-id="25c38-146">When using a radial fill to represent the dwell timer, start from the center of button.</span></span> <span data-ttu-id="25c38-147">Una risposta uniforme genera meno confusione di tante indicazioni diverse sui vari pulsanti.</span><span class="sxs-lookup"><span data-stu-id="25c38-147">A consistent response is less confusing than all different directions on different buttons.</span></span> 

  * <span data-ttu-id="25c38-148">Questa regola può essere interrotta anche per le interazioni direzionali (ad esempio, NAV su/giù/sinistra/destra e così via).</span><span class="sxs-lookup"><span data-stu-id="25c38-148">This rule can be broken though for directional interactions (for example, nav up/down/left/right, and so on).</span></span> <span data-ttu-id="25c38-149">Ad esempio, Microsoft Dynamics 365 Guides fa un'eccezione per AVANTI/INDIETRO, trattandosi di riempimenti sinistra-destra.</span><span class="sxs-lookup"><span data-stu-id="25c38-149">For example, Microsoft Dynamics 365 Guides makes an exception on NEXT/BACK being left right fills.</span></span>
  * <span data-ttu-id="25c38-150">Provare a invertire il riempimento radiale dall'esterno, per scenari come la disattivazione di un pulsante.</span><span class="sxs-lookup"><span data-stu-id="25c38-150">Consider inverting radial fill from outside, for scenarios like toggling off a button.</span></span> <span data-ttu-id="25c38-151">La sensazione opposta di premere un pulsante è un effetto visivo piacevole da mantenere.</span><span class="sxs-lookup"><span data-stu-id="25c38-151">The inverse feeling of pushing a button is a nice visual pattern to maintain.</span></span> 

### <a name="progressive-disclosure"></a><span data-ttu-id="25c38-152">Rivelazione progressiva</span><span class="sxs-lookup"><span data-stu-id="25c38-152">Progressive disclosure</span></span>

<span data-ttu-id="25c38-153">Con la rilevazione progressiva vengono mostrati solo i dettagli rilevanti in ciascuna fase di un'interazione.</span><span class="sxs-lookup"><span data-stu-id="25c38-153">Progressive disclosure means only showing as much detail as is relevant at each stage of an interaction.</span></span> <span data-ttu-id="25c38-154">Per l'abitazione, significa che la destinazione dell'abitazione viene rivelata in evidenza, ad esempio in un controllo elenco.</span><span class="sxs-lookup"><span data-stu-id="25c38-154">For dwell, that means the dwell target is revealed on highlight (for example, in a list control).</span></span>

 ### <a name="oversized-targets"></a><span data-ttu-id="25c38-155">Destinazioni di dimensioni eccessive</span><span class="sxs-lookup"><span data-stu-id="25c38-155">Oversized targets</span></span>

<span data-ttu-id="25c38-156">L'area di attesa può essere più grande dell'icona inattiva per agevolare l'uso, come nel caso del pulsante Indietro in Microsoft Dynamics 365 Guides.</span><span class="sxs-lookup"><span data-stu-id="25c38-156">Dwell region can be larger than inactive icon to make it easier to use, like the Back button in Microsoft Dynamics 365 Guides.</span></span>

### <a name="prevent-flickering-with-delayed-feedback"></a><span data-ttu-id="25c38-157">Evitare lo sfarfallio con un feedback ritardato</span><span class="sxs-lookup"><span data-stu-id="25c38-157">Prevent flickering with delayed feedback</span></span>

<span data-ttu-id="25c38-158">Aggiungi un breve ritardo prima di avviare il feedback visivo per evitare lo sfarfallio quando qualcuno passa su una destinazione di attesa.</span><span class="sxs-lookup"><span data-stu-id="25c38-158">Use a short delay before starting visual feedback to avoid flickering when someone passes over a dwell target.</span></span>
* <span data-ttu-id="25c38-159">Per i pulsanti interattivi con frequenza, è consigliabile ridurre il ritardo, in modo che l'applicazione ritenga nuovamente attiva.</span><span class="sxs-lookup"><span data-stu-id="25c38-159">For buttons interacted with frequently, keep the delay short so the application feels reactive.</span></span>
* <span data-ttu-id="25c38-160">Per i pulsanti che interagiscono con una frequenza infrequente, un ritardo più lungo può essere appropriato per evitare l'interfaccia.</span><span class="sxs-lookup"><span data-stu-id="25c38-160">For buttons that are interacted with infrequently, a longer delay can be appropriate to avoid the interface feeling twitchy.</span></span>

<br>

---

## <a name="ui-patterns"></a><span data-ttu-id="25c38-161">Modelli per l'interfaccia utente</span><span class="sxs-lookup"><span data-stu-id="25c38-161">UI patterns</span></span>

### <a name="high-frequency-buttons"></a><span data-ttu-id="25c38-162">Pulsanti usati frequentemente</span><span class="sxs-lookup"><span data-stu-id="25c38-162">High frequency buttons</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="25c38-163">I pulsanti ad alta frequenza sono pulsanti usati comunemente in un'applicazione.</span><span class="sxs-lookup"><span data-stu-id="25c38-163">High frequency buttons are buttons that are used commonly throughout an application.</span></span> <span data-ttu-id="25c38-164">Un buon esempio è rappresentato dai pulsanti Avanti e Indietro in Microsoft Dynamics 365 Guides.</span><span class="sxs-lookup"><span data-stu-id="25c38-164">A good example of these are the next and back buttons in Microsoft Dynamics 365 Guides.</span></span><br>
        <br>
        <span data-ttu-id="25c38-165">**Indicazioni**</span><span class="sxs-lookup"><span data-stu-id="25c38-165">**Recommendations**</span></span><br>
  * <span data-ttu-id="25c38-166">I pulsanti ad alta frequenza dovrebbero essere di grandi dimensioni, più facili da raggiungere con l'Head-sguardi</span><span class="sxs-lookup"><span data-stu-id="25c38-166">High frequency buttons should be large, easier to hit with head-gaze</span></span>
  * <span data-ttu-id="25c38-167">Rimanere vicino all'altezza degli occhi per evitare la pressione ergonomica.</span><span class="sxs-lookup"><span data-stu-id="25c38-167">Stay near eye height to avoid ergonomic straining.</span></span><br>
        <br>
<span data-ttu-id="25c38-168">*Immagine: pulsante Avanti per Microsoft Dynamics 365 guide*</span><span class="sxs-lookup"><span data-stu-id="25c38-168">*Image: Microsoft Dynamics 365 Guides next button*</span></span>
    :::column-end:::
        :::column:::
       ![Pulsante Avanti per Microsoft Dynamics 365 guide](images/GuideNextButton.png)<br>
    :::column-end:::
:::row-end:::

<br>

---


### <a name="low-frequency-buttons"></a><span data-ttu-id="25c38-170">Pulsanti usati raramente</span><span class="sxs-lookup"><span data-stu-id="25c38-170">Low frequency buttons</span></span>

<span data-ttu-id="25c38-171">I pulsanti con frequenza bassa sono pulsanti che non sono interagiti regolarmente con l'intera applicazione.</span><span class="sxs-lookup"><span data-stu-id="25c38-171">Low frequency buttons are buttons that aren't interacted with as regularly throughout the application.</span></span> <span data-ttu-id="25c38-172">Un buon esempio è rappresentato da un pulsante che consente di accedere al menu delle impostazioni o di cancellare tutto il lavoro svolto.</span><span class="sxs-lookup"><span data-stu-id="25c38-172">A good example might be a button to access the settings menu, or a button to clear all work.</span></span>

* <span data-ttu-id="25c38-173">Prova a posizionare questi pulsanti in modo che non intralcino i percorsi di puntamento con la testa di uso frequente per evitare che vengano attivati accidentalmente.</span><span class="sxs-lookup"><span data-stu-id="25c38-173">Try to keep these buttons out of the way of frequent head-gaze paths to avoid accidental activation.</span></span> 

<br>

---

### <a name="confirmations"></a><span data-ttu-id="25c38-174">Conferme</span><span class="sxs-lookup"><span data-stu-id="25c38-174">Confirmations</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="25c38-175">Quando un'azione ha un impatto significativo, ad esempio l'addebito dei costi, l'eliminazione del lavoro o l'avvio di un processo lungo, è utile confermare che una persona ha voluto selezionare un pulsante.</span><span class="sxs-lookup"><span data-stu-id="25c38-175">When an action has significant impact, like charging money, deleting work, or starting a long process, it's useful to confirm that a person meant to select a button.</span></span><br>
        <br>
        <span data-ttu-id="25c38-176">**Indicazioni**</span><span class="sxs-lookup"><span data-stu-id="25c38-176">**Recommendations**</span></span><br>
  * <span data-ttu-id="25c38-177">Mostra l'evidenziazione della selezione sul pulsante principale.</span><span class="sxs-lookup"><span data-stu-id="25c38-177">Show selection highlight on main button.</span></span>
  * <span data-ttu-id="25c38-178">Rivela la destinazione dell'attesa contemporaneamente all'evidenziazione della selezione.</span><span class="sxs-lookup"><span data-stu-id="25c38-178">Reveal dwell target at same time as selection highlight.</span></span>
  * <span data-ttu-id="25c38-179">Per il pulsante secondario, rivela la destinazione dell'attesa al momento del puntamento con la testa.</span><span class="sxs-lookup"><span data-stu-id="25c38-179">For the secondary button, reveal the dwell target on head-gaze.</span></span><br>
        <br>
<span data-ttu-id="25c38-180">*Immagine: finestra di conferma della Guida di Microsoft Dynamics 365*</span><span class="sxs-lookup"><span data-stu-id="25c38-180">*Image: Microsoft Dynamics 365 Guides confirmation dialog*</span></span>
    :::column-end:::
        :::column:::
       ![Finestra di conferma della Guida di Microsoft Dynamics 365](images/GuidesConfirmation.png)<br>
    :::column-end:::
:::row-end:::
        
<br>

---

### <a name="toggle-buttons"></a><span data-ttu-id="25c38-182">Interruttori</span><span class="sxs-lookup"><span data-stu-id="25c38-182">Toggle buttons</span></span>

<span data-ttu-id="25c38-183">Per funzionare correttamente, gli interruttori necessitano di una logica più sottile.</span><span class="sxs-lookup"><span data-stu-id="25c38-183">Toggle buttons require some nuanced logic to work properly.</span></span> <span data-ttu-id="25c38-184">Quando un utente si sofferma su un interruttore e lo attiva, deve uscire dal pulsante e quindi tornare a riavviare la logica di permanenza.</span><span class="sxs-lookup"><span data-stu-id="25c38-184">When a person dwells on a toggle button and activates it, they need to exit the button and then return to restart the dwell logic.</span></span> <span data-ttu-id="25c38-185">È importante che i pulsanti attivabili con lo stato attivo e inattivo siano deselezionati.</span><span class="sxs-lookup"><span data-stu-id="25c38-185">It's important that togglable buttons have a clear active versus inactive state.</span></span> 

<br>

---

### <a name="list-views"></a><span data-ttu-id="25c38-186">Visualizzazioni elenco</span><span class="sxs-lookup"><span data-stu-id="25c38-186">List views</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="25c38-187">Le visualizzazioni elenco presentano una particolare sfida per l'input di punta e di residenza.</span><span class="sxs-lookup"><span data-stu-id="25c38-187">List views present a particular challenge for head-gaze and dwell input.</span></span> <span data-ttu-id="25c38-188">Gli utenti possono eseguire la scansione del contenuto senza che sia simile a quello che si aggira intorno alle destinazioni di residenza.</span><span class="sxs-lookup"><span data-stu-id="25c38-188">People can scan the content without feeling like that have to tiptoe around the dwell targets.</span></span><br>
        <br>
<span data-ttu-id="25c38-189">**Indicazioni**</span><span class="sxs-lookup"><span data-stu-id="25c38-189">**Recommendations**</span></span><br>
  * <span data-ttu-id="25c38-190">Far evidenziare l'intera riga quando si è a capo, ma non inizia la permanenza, a meno che l'Head-sguardi si trovi nella destinazione di residenza specifica.</span><span class="sxs-lookup"><span data-stu-id="25c38-190">Have the entire row highlight when head-gazed but doesn’t begin dwell unless head-gaze is on the specific dwell target.</span></span>
  * <span data-ttu-id="25c38-191">Mostra solo la destinazione di residenza quando la riga viene evidenziata in modo da ridurre il rumore visivo.</span><span class="sxs-lookup"><span data-stu-id="25c38-191">Only show the dwell target when the row is highlighted to cut down on visual noise.</span></span>
  * <span data-ttu-id="25c38-192">Essere chiari e coerenti con la posizione delle destinazioni di residenza.</span><span class="sxs-lookup"><span data-stu-id="25c38-192">Be clear and consistent with the position of dwell targets.</span></span>
  * <span data-ttu-id="25c38-193">Non mostrare tutte le destinazioni di residenza in una sola volta per evitare l'interfaccia utente ripetitiva.</span><span class="sxs-lookup"><span data-stu-id="25c38-193">Don't show all dwell targets at once to avoid repetitive UI.</span></span>
  * <span data-ttu-id="25c38-194">Riutilizzare lo stesso modello il più spesso possibile per stabilire la familiarità con l'esperienza utente.</span><span class="sxs-lookup"><span data-stu-id="25c38-194">Reuse the same pattern as often as possible to establish UX familiarity.</span></span><br>
        <br>
<span data-ttu-id="25c38-195">*Immagine: elenco delle guide di Microsoft Dynamics 365*</span><span class="sxs-lookup"><span data-stu-id="25c38-195">*Image: Microsoft Dynamics 365 Guides list*</span></span>
    :::column-end:::
        :::column:::
       ![Elenco delle guide di Microsoft Dynamics 365](images/GuidesListView.png)<br>
    :::column-end:::
:::row-end:::

<br>

---
 
 ## <a name="see-also"></a><span data-ttu-id="25c38-197">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="25c38-197">See also</span></span>

* [<span data-ttu-id="25c38-198">Sguardo e commit</span><span class="sxs-lookup"><span data-stu-id="25c38-198">Gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="25c38-199">Mani - Manipolazione diretta</span><span class="sxs-lookup"><span data-stu-id="25c38-199">Hands - Direct manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="25c38-200">Mani - Movimenti</span><span class="sxs-lookup"><span data-stu-id="25c38-200">Hands - Gestures</span></span>](gaze-and-commit.md#composite-gestures)
* [<span data-ttu-id="25c38-201">Mani - Puntamento e commit</span><span class="sxs-lookup"><span data-stu-id="25c38-201">Hands - Point and commit</span></span>](point-and-commit.md)
* [<span data-ttu-id="25c38-202">Interazioni istintive</span><span class="sxs-lookup"><span data-stu-id="25c38-202">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="25c38-203">Input vocale</span><span class="sxs-lookup"><span data-stu-id="25c38-203">Voice input</span></span>](voice-input.md)
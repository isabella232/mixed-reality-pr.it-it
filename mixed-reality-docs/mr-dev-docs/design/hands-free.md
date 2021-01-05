---
title: Mani libere
description: Informazioni sulle problematiche che gli utenti possono affrontare con un'interfaccia di controllo e controllo e su diverse alternative gratuite.
author: hferrone
ms.author: v-hferrone
ms.date: 04/20/2019
ms.topic: article
keywords: Realtà mista, senza contatto, sguardi, obiettivi mirati, interazione, progettazione, cuffie per realtà mista, cuffie di realtà mista di Windows, cuffie per realtà virtuale, HoloLens, MRTK, Toolkit per realtà mista, input vocale, usabilità
ms.openlocfilehash: 2864e58fdd8a29ae8f981b42f50735eb13a50869
ms.sourcegitcommit: d340303cda71c31e6c3320231473d623c0930d33
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/01/2021
ms.locfileid: "97847685"
---
# <a name="hands-free"></a><span data-ttu-id="5437a-104">Mani libere</span><span class="sxs-lookup"><span data-stu-id="5437a-104">Hands-free</span></span>

## <a name="scenarios"></a><span data-ttu-id="5437a-105">Scenari</span><span class="sxs-lookup"><span data-stu-id="5437a-105">Scenarios</span></span>

<span data-ttu-id="5437a-106">Come descritto nella [Panoramica del modello di interazione](interaction-fundamentals.md), dopo aver identificato gli utenti e i relativi obiettivi, è possibile chiedersi quali sono le questioni ambientali o di situazione che potrebbero affrontare quando lavorano per svolgere le proprie attività.</span><span class="sxs-lookup"><span data-stu-id="5437a-106">As outlined in the [interaction model overview](interaction-fundamentals.md), once you've identified your users and their goals, ask yourself what environmental or situational challenges they might face as they work to accomplish their tasks.</span></span> <span data-ttu-id="5437a-107">Molti utenti, ad esempio, devono usare le proprie mani per realizzare gli obiettivi reali e avranno difficoltà a interagire con un'interfaccia basata su hands and controller.</span><span class="sxs-lookup"><span data-stu-id="5437a-107">For example, many users need to use their hands to accomplish their real-world goals, and they'll have difficulty interacting with a hands-and-controllers based interface.</span></span>

<span data-ttu-id="5437a-108">Ecco alcuni scenari specifici:</span><span class="sxs-lookup"><span data-stu-id="5437a-108">Some specific scenarios include:</span></span> 
* <span data-ttu-id="5437a-109">Farsi guidare nello svolgimento di un'attività mentre si hanno le mani occupate</span><span class="sxs-lookup"><span data-stu-id="5437a-109">Being guided through a task, while the user's hands are busy</span></span>
* <span data-ttu-id="5437a-110">Fare riferimento a materiali mentre si hanno le mani occupate</span><span class="sxs-lookup"><span data-stu-id="5437a-110">Referencing materials while the user's hands are busy</span></span>
* <span data-ttu-id="5437a-111">Affaticamento delle mani</span><span class="sxs-lookup"><span data-stu-id="5437a-111">Hand fatigue</span></span>
* <span data-ttu-id="5437a-112">Guanti che non consentono il tracciamento</span><span class="sxs-lookup"><span data-stu-id="5437a-112">Gloves that can't be tracked</span></span>
* <span data-ttu-id="5437a-113">Trasportare qualcosa con le mani</span><span class="sxs-lookup"><span data-stu-id="5437a-113">Carrying something in their hands</span></span>
* <span data-ttu-id="5437a-114">Imbarazzo sociale quando si usano movimenti a mano grande</span><span class="sxs-lookup"><span data-stu-id="5437a-114">Social awkwardness when using large hand gestures</span></span>
* <span data-ttu-id="5437a-115">Spazi ristretti</span><span class="sxs-lookup"><span data-stu-id="5437a-115">Tight spaces</span></span>

## <a name="hands-free-modalities"></a><span data-ttu-id="5437a-116">Modalità senza mani</span><span class="sxs-lookup"><span data-stu-id="5437a-116">Hands-free modalities</span></span>

### <a name="voice-input"></a>[<span data-ttu-id="5437a-117">Input vocale</span><span class="sxs-lookup"><span data-stu-id="5437a-117">Voice input</span></span>](voice-input.md)

<span data-ttu-id="5437a-118">L'uso della voce per il comando e il controllo di un'interfaccia offre un modo pratico per lavorare senza mani e per usare i tasti di scelta rapida per ignorare più passaggi, se lo si desidera.</span><span class="sxs-lookup"><span data-stu-id="5437a-118">Using your voice to command and control an interface offers a convenient way to operate hands-free and to use shortcuts to skip multiple steps if you want.</span></span> <span data-ttu-id="5437a-119">Con l'input vocale, l'utente può leggere il nome di qualsiasi pulsante per attivarlo _("visualizzarlo, pronunciarlo")_ e conversare con un agente digitale che può eseguire le attività.</span><span class="sxs-lookup"><span data-stu-id="5437a-119">With voice input, the user can read any button's name out loud to activate it _("see it, say it")_ and converse with a digital agent who can accomplish tasks for you.</span></span>

### <a name="gaze-and-dwell"></a>[<span data-ttu-id="5437a-120">Sguardo fisso e attesa</span><span class="sxs-lookup"><span data-stu-id="5437a-120">Gaze and dwell</span></span>](gaze-and-dwell.md)

<span data-ttu-id="5437a-121">In alcune situazioni senza problemi, l'uso della tua voce non è ideale o addirittura possibile.</span><span class="sxs-lookup"><span data-stu-id="5437a-121">In some hands-free situations, using your voice isn't ideal or even possible.</span></span> <span data-ttu-id="5437a-122">Gli ambienti di produzione, la privacy o le norme di social networking possono essere tutti vincoli.</span><span class="sxs-lookup"><span data-stu-id="5437a-122">Loud factory environments, privacy, or social norms can all be constraints.</span></span> <span data-ttu-id="5437a-123">Il modello di sguardo e di sosta consente all'utente di spostarsi in un'app senza alcun input aggiuntivo, a parte l'occhio o lo sguardo da capo: l'utente continua a guardare la destinazione e si sofferma per un istante per poterlo attivare.</span><span class="sxs-lookup"><span data-stu-id="5437a-123">The gaze + dwell model allows the user to navigate an app without any extra input aside from their eye or head gaze: The user simply keeps gazing (with their head or eyes) at the target and lingers there for a moment to activate it.</span></span> <span data-ttu-id="5437a-124">Per altre informazioni sulle singole considerazioni di progettazione per lo sguardo + l'abitazione, vedere [Eye-sguardi + soffermarsi](gaze-and-dwell-eyes.md) e [guardare a capo + soffermarsi](gaze-and-dwell-head.md).</span><span class="sxs-lookup"><span data-stu-id="5437a-124">To learn more about the individual design considerations for gaze + dwell, check out [eye-gaze + dwell](gaze-and-dwell-eyes.md) and [head-gaze + dwell](gaze-and-dwell-head.md).</span></span>

## <a name="transitioning-in-and-out-of-hands-free"></a><span data-ttu-id="5437a-125">Transizione all'interno e all'esterno di Hands-Free</span><span class="sxs-lookup"><span data-stu-id="5437a-125">Transitioning in and out of hands-free</span></span>

<span data-ttu-id="5437a-126">Per questi scenari, liberare le mani dall'interazione con gli ologrammi per i comandi e la navigazione può variare da un requisito assoluto per il funzionamento dell'applicazione, end-to-end, a un ulteriore vantaggio che l'utente può eseguire la transizione da e verso l'esterno in qualsiasi momento.</span><span class="sxs-lookup"><span data-stu-id="5437a-126">For these scenarios, freeing your hands from interacting with holograms for commanding and navigation can range from being an absolute requirement to operating the application, end-to-end, to an added convenience that the user can transition in and out of at any time.</span></span> 

<span data-ttu-id="5437a-127">Se per l'applicazione è necessario che venga sempre utilizzata la funzionalità hands-free, indipendentemente dal fatto che si utilizzi l'uso di Rest, i comandi vocali personalizzati o il singolo comando Voice "Select", assicurarsi di creare le sistemazioni appropriate nell'interfaccia utente.</span><span class="sxs-lookup"><span data-stu-id="5437a-127">If the application requires that it will always be used hands-free, whether by using dwell, custom voice commands, or the single voice command, "select", then make sure to make the appropriate accommodations in your UI.</span></span> 

<span data-ttu-id="5437a-128">Se l'utente di destinazione deve passare da una mano all'altra a propria discrezione, è importante tenere conto dei principi seguenti.</span><span class="sxs-lookup"><span data-stu-id="5437a-128">If your target user needs to switch from hands to hands-free at their discretion, then it's important to take the following principles into account.</span></span>

### <a name="assume-the-user-is-already-in-the-mode-that-they-want-to-switch-to"></a><span data-ttu-id="5437a-129">Si supponga che l'utente sia già nella modalità a cui si desidera passare</span><span class="sxs-lookup"><span data-stu-id="5437a-129">Assume the user is already in the mode that they want to switch to</span></span>
<span data-ttu-id="5437a-130">Ad esempio, se l'utente si trova in fabbrica, guardando un riferimento video sulla sua HoloLens e decide di prelevare una chiave per iniziare a lavorare, probabilmente inizierà a lavorare in modo pratico senza dover posizionare la chiave per premere un pulsante.</span><span class="sxs-lookup"><span data-stu-id="5437a-130">For instance, if the user is on the factory floor, watching a video reference on her HoloLens, and decides to pick up a wrench to start working, she most likely would start working in hands-free without having to put down the wrench to press a button.</span></span> <span data-ttu-id="5437a-131">Può richiamare una sessione vocale con un comando Voice, soffermarsi su un'interfaccia utente già visibile per iniziare a soffermarsi o pronunciare la parola "Select".</span><span class="sxs-lookup"><span data-stu-id="5437a-131">She can invoke a voice session with a voice command, dwell on an already-visible UI to begin dwell, or say the word "select".</span></span>

<span data-ttu-id="5437a-132">L'utente può:</span><span class="sxs-lookup"><span data-stu-id="5437a-132">The user can:</span></span> 
* <span data-ttu-id="5437a-133">Passa a vivavoce senza intervento</span><span class="sxs-lookup"><span data-stu-id="5437a-133">Switch to hands-free while hands-free</span></span>
* <span data-ttu-id="5437a-134">Passa a mano</span><span class="sxs-lookup"><span data-stu-id="5437a-134">Switch to hands with your hands</span></span>
* <span data-ttu-id="5437a-135">Passare al controller usando un controller</span><span class="sxs-lookup"><span data-stu-id="5437a-135">Switch to the controller using a controller</span></span> 

### <a name="create-redundant-ways-to-switch-modes"></a><span data-ttu-id="5437a-136">Creare modi ridondanti per cambiare modalità</span><span class="sxs-lookup"><span data-stu-id="5437a-136">Create redundant ways to switch modes</span></span>

<span data-ttu-id="5437a-137">Mentre il primo principio riguarda l'accesso, il secondo riguarda la disponibilità.</span><span class="sxs-lookup"><span data-stu-id="5437a-137">While the first principle is about access, the second one is about availability.</span></span> <span data-ttu-id="5437a-138">Non dovrebbe essere presente un unico modo per eseguire la transizione all'interno e all'esterno di una modalità.</span><span class="sxs-lookup"><span data-stu-id="5437a-138">There shouldn't just be a single way to transition in and out of a mode.</span></span> 

<span data-ttu-id="5437a-139">Di seguito sono riportati alcuni esempi:</span><span class="sxs-lookup"><span data-stu-id="5437a-139">Some examples would be:</span></span> 
* <span data-ttu-id="5437a-140">Pulsante per l'inizio delle interazioni vocali</span><span class="sxs-lookup"><span data-stu-id="5437a-140">A button to begin voice interactions</span></span>
* <span data-ttu-id="5437a-141">Un comando vocale a cui passare, usando l'Head-sguardi e l'abitazione</span><span class="sxs-lookup"><span data-stu-id="5437a-141">A voice command to transition to, using head-gaze and dwell</span></span>

### <a name="add-a-dash-of-drama"></a><span data-ttu-id="5437a-142">Aggiungere un trattino di dramma</span><span class="sxs-lookup"><span data-stu-id="5437a-142">Add a dash of drama</span></span>

<span data-ttu-id="5437a-143">Un commodity switch è molto importante.</span><span class="sxs-lookup"><span data-stu-id="5437a-143">A mode switch is a big deal.</span></span> <span data-ttu-id="5437a-144">È importante che, quando si verificano queste transizioni, siano uno esplicito, anche un cambio drammatico, per consentire all'utente di sapere cosa è successo.</span><span class="sxs-lookup"><span data-stu-id="5437a-144">It's important that when these transitions happen that they be an explicit, even a dramatic switch, to let the user know what happened.</span></span> 

## <a name="usability-checklist"></a><span data-ttu-id="5437a-145">Elenco di controllo dell'usabilità</span><span class="sxs-lookup"><span data-stu-id="5437a-145">Usability checklist</span></span>

<span data-ttu-id="5437a-146">**L'utente può eseguire tutte le operazioni e tutto ciò che si può fare senza alcun intervento end-to-end?**</span><span class="sxs-lookup"><span data-stu-id="5437a-146">**Can the user do everything and anything hands-free, end-to-end?**</span></span>
* <span data-ttu-id="5437a-147">Ogni interoperabilità deve essere Hands-Free accessibile</span><span class="sxs-lookup"><span data-stu-id="5437a-147">Every interactable should be accessible hands-free</span></span>
* <span data-ttu-id="5437a-148">Assicurarsi che sia presente una sostituzione per tutti i movimenti personalizzati, ad esempio il ridimensionamento, l'inserimento, il scorrimento, i colpetti e così via.</span><span class="sxs-lookup"><span data-stu-id="5437a-148">Ensure that there's a replacement for all custom gestures, such as resizing, placing, swipes, taps, and so on.</span></span>
* <span data-ttu-id="5437a-149">Assicurarsi che l'utente abbia il controllo della presenza, della posizione e del livello di dettaglio dell'interfaccia utente sempre</span><span class="sxs-lookup"><span data-stu-id="5437a-149">Ensure that the user has confident control of UI presence, placement, and verbosity always</span></span>
    * <span data-ttu-id="5437a-150">Recupero dell'interfaccia utente</span><span class="sxs-lookup"><span data-stu-id="5437a-150">Getting UI out of the way</span></span>
    * <span data-ttu-id="5437a-151">Indirizzamento dell'interfaccia utente fuori campo di visualizzazione (FOV)</span><span class="sxs-lookup"><span data-stu-id="5437a-151">Addressing UI that is out of field of view (FOV)</span></span>
    * <span data-ttu-id="5437a-152">Quanto vedo, dove, quando</span><span class="sxs-lookup"><span data-stu-id="5437a-152">How much I see, where, when</span></span>

<span data-ttu-id="5437a-153">**La meccanica dell'interazione viene insegnata e rafforzata con la affordances corretta?**</span><span class="sxs-lookup"><span data-stu-id="5437a-153">**Are the mechanics of the interaction being taught and reinforced with the right affordances?**</span></span>

<span data-ttu-id="5437a-154">Informazioni sull'utente...</span><span class="sxs-lookup"><span data-stu-id="5437a-154">Does the user understand ...</span></span>
* <span data-ttu-id="5437a-155">... Modalità di funzionamento</span><span class="sxs-lookup"><span data-stu-id="5437a-155">... What mode they are in?</span></span>
* <span data-ttu-id="5437a-156">... Cosa si può fare in questa modalità?</span><span class="sxs-lookup"><span data-stu-id="5437a-156">... What they can do in this mode?</span></span>
* <span data-ttu-id="5437a-157">... Qual è lo stato corrente?</span><span class="sxs-lookup"><span data-stu-id="5437a-157">... What is the current state?</span></span>
* <span data-ttu-id="5437a-158">... In che modo è possibile eseguire la transizione?</span><span class="sxs-lookup"><span data-stu-id="5437a-158">... How they can transition out?</span></span>
    
<span data-ttu-id="5437a-159">**L'interfaccia utente è ottimizzata per l'Hand-Free?**</span><span class="sxs-lookup"><span data-stu-id="5437a-159">**Is the UI optimized for hands-free?**</span></span>   

* <span data-ttu-id="5437a-160">Esempio: il affordances di abitazione non è integrato nei modelli 2D tipici</span><span class="sxs-lookup"><span data-stu-id="5437a-160">Example: Dwell affordances aren't built in to typical 2D patterns</span></span>
* <span data-ttu-id="5437a-161">Esempio: il targeting vocale è migliore con l'evidenziazione degli oggetti</span><span class="sxs-lookup"><span data-stu-id="5437a-161">Example: Voice targeting is better with object highlighting</span></span>
* <span data-ttu-id="5437a-162">Esempio: le interazioni vocali sono migliori con le didascalie che devono essere attivate</span><span class="sxs-lookup"><span data-stu-id="5437a-162">Example: Voice interactions are better with captions that need to be turned on</span></span>

## <a name="see-also"></a><span data-ttu-id="5437a-163">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="5437a-163">See also</span></span>

* [<span data-ttu-id="5437a-164">Tracciamento oculare in HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="5437a-164">Eye tracking on HoloLens 2</span></span>](eye-tracking.md)
* [<span data-ttu-id="5437a-165">Sguardo e commit</span><span class="sxs-lookup"><span data-stu-id="5437a-165">Gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="5437a-166">Sguardo fisso e attesa</span><span class="sxs-lookup"><span data-stu-id="5437a-166">Gaze and dwell</span></span>](gaze-and-dwell.md)
* [<span data-ttu-id="5437a-167">Mani - Manipolazione diretta</span><span class="sxs-lookup"><span data-stu-id="5437a-167">Hands - Direct manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="5437a-168">Mani - Movimenti</span><span class="sxs-lookup"><span data-stu-id="5437a-168">Hands - Gestures</span></span>](gaze-and-commit.md#composite-gestures)
* [<span data-ttu-id="5437a-169">Mani - Puntamento e commit</span><span class="sxs-lookup"><span data-stu-id="5437a-169">Hands - Point and commit</span></span>](point-and-commit.md)
* [<span data-ttu-id="5437a-170">Interazioni istintive</span><span class="sxs-lookup"><span data-stu-id="5437a-170">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="5437a-171">Input vocale</span><span class="sxs-lookup"><span data-stu-id="5437a-171">Voice input</span></span>](voice-input.md)

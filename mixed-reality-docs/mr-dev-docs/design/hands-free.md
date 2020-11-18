---
title: Mani libere
description: Informazioni sulle problematiche che gli utenti possono affrontare con un'interfaccia di controllo e controllo e su diverse alternative gratuite.
author: hferrone
ms.author: v-hferrone
ms.date: 04/20/2019
ms.topic: article
keywords: Realtà mista, senza contatto, sguardi, obiettivi mirati, interazione, progettazione, cuffie per realtà mista, cuffie di realtà mista di Windows, cuffie per realtà virtuale, HoloLens, MRTK, Toolkit per realtà mista, input vocale, usabilità
ms.openlocfilehash: 7f4d3a0ec8d2e7435f54164006a8bd122b1ebcba
ms.sourcegitcommit: 4f3ef057a285be2e260615e5d6c41f00d15d08f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2020
ms.locfileid: "94702137"
---
# <a name="hands-free"></a><span data-ttu-id="7a983-104">Mani libere</span><span class="sxs-lookup"><span data-stu-id="7a983-104">Hands-free</span></span>

## <a name="scenarios"></a><span data-ttu-id="7a983-105">Scenari</span><span class="sxs-lookup"><span data-stu-id="7a983-105">Scenarios</span></span>

<span data-ttu-id="7a983-106">Come descritto nella [Panoramica del modello di interazione](interaction-fundamentals.md), dopo aver identificato gli utenti e i relativi obiettivi, è possibile chiedersi quali sono le questioni ambientali o di situazione che potrebbero affrontare quando lavorano per svolgere le proprie attività.</span><span class="sxs-lookup"><span data-stu-id="7a983-106">As outlined in the [interaction model overview](interaction-fundamentals.md), once you have identified your users and their goals, ask yourself what environmental or situational challenges they might face as they work to accomplish their tasks.</span></span> <span data-ttu-id="7a983-107">Molti utenti, ad esempio, devono usare le proprie mani per realizzare gli obiettivi reali e avranno difficoltà a interagire con un'interfaccia basata su hands and controller.</span><span class="sxs-lookup"><span data-stu-id="7a983-107">For example, many users need to use their hands to accomplish their real-world goals, and they will have difficulty interacting with a hands-and-controllers based interface.</span></span> 

<span data-ttu-id="7a983-108">Ecco alcuni scenari specifici:</span><span class="sxs-lookup"><span data-stu-id="7a983-108">Some specific scenarios include:</span></span> 
* <span data-ttu-id="7a983-109">Farsi guidare nello svolgimento di un'attività mentre si hanno le mani occupate</span><span class="sxs-lookup"><span data-stu-id="7a983-109">Being guided through a task, while the user's hands are busy</span></span>
* <span data-ttu-id="7a983-110">Fare riferimento a materiali mentre si hanno le mani occupate</span><span class="sxs-lookup"><span data-stu-id="7a983-110">Referencing materials while the user's hands are busy</span></span>
* <span data-ttu-id="7a983-111">Affaticamento delle mani</span><span class="sxs-lookup"><span data-stu-id="7a983-111">Hand fatigue</span></span>
* <span data-ttu-id="7a983-112">Guanti che non consentono il tracciamento</span><span class="sxs-lookup"><span data-stu-id="7a983-112">Gloves that can't be tracked</span></span>
* <span data-ttu-id="7a983-113">Trasportare qualcosa con le mani</span><span class="sxs-lookup"><span data-stu-id="7a983-113">Carrying something in their hands</span></span>
* <span data-ttu-id="7a983-114">Imbarazzo sociale per eseguire movimenti a mano grande</span><span class="sxs-lookup"><span data-stu-id="7a983-114">Social awkwardness to perform large hand gestures</span></span>
* <span data-ttu-id="7a983-115">Spazi ristretti</span><span class="sxs-lookup"><span data-stu-id="7a983-115">Tight spaces</span></span>


## <a name="hands-free-modalities"></a><span data-ttu-id="7a983-116">Modalità senza mani</span><span class="sxs-lookup"><span data-stu-id="7a983-116">Hands-free modalities</span></span>

### <a name="voice-input"></a>[<span data-ttu-id="7a983-117">Input vocale</span><span class="sxs-lookup"><span data-stu-id="7a983-117">Voice input</span></span>](voice-input.md)

<span data-ttu-id="7a983-118">L'uso della tua voce per il comando e il controllo di un'interfaccia ti offre un modo pratico per lavorare senza mani e per usare i tasti di scelta rapida per ignorare in modo flessibile più passaggi, se necessario.</span><span class="sxs-lookup"><span data-stu-id="7a983-118">Using your voice to command and control an interface offers a convenient way to operate hands-free and to use shortcuts to flexibly skip multiple steps if desired.</span></span> <span data-ttu-id="7a983-119">Con l'input vocale, l'utente può semplicemente leggere il nome di un pulsante per attivarlo _("visualizzarlo, pronunciarlo")_ e conversare con un agente digitale che può eseguire le attività.</span><span class="sxs-lookup"><span data-stu-id="7a983-119">With voice input, the user can simply read any button's name out loud to activate it _("see it, say it")_ and converse with a digital agent who can accomplish tasks for you.</span></span>


### <a name="gaze-and-dwell"></a>[<span data-ttu-id="7a983-120">Sguardo fisso e attesa</span><span class="sxs-lookup"><span data-stu-id="7a983-120">Gaze and dwell</span></span>](gaze-and-dwell.md)

<span data-ttu-id="7a983-121">In alcune situazioni senza problemi, l'uso della tua voce non è ideale o addirittura possibile.</span><span class="sxs-lookup"><span data-stu-id="7a983-121">In some hands-free situations, using your voice is not ideal or even possible.</span></span> <span data-ttu-id="7a983-122">Gli ambienti di produzione, la privacy o le norme di social networking possono essere tutti vincoli.</span><span class="sxs-lookup"><span data-stu-id="7a983-122">Loud factory environments, privacy, or social norms can all be constraints.</span></span> <span data-ttu-id="7a983-123">Il modello di tipo sguardo + sosta consente all'utente di spostarsi in un'app senza alcun input aggiuntivo, oltre che da un occhio o da uno sguardo: l'utente continua a guardare la destinazione e indugia per un istante per poterlo attivare.</span><span class="sxs-lookup"><span data-stu-id="7a983-123">The gaze + dwell model allows the user to navigate an app without any additional input aside from their eye or head gaze: The user simply keeps gazing (with their head or eyes) at the target and lingers there for a moment to activate it.</span></span> <span data-ttu-id="7a983-124">Per altre informazioni sulle singole considerazioni di progettazione per lo sguardo + l'abitazione, vedere [Eye-sguardi + soffermarsi](gaze-and-dwell-eyes.md) e [guardare a capo + soffermarsi](gaze-and-dwell-head.md).</span><span class="sxs-lookup"><span data-stu-id="7a983-124">To learn more about the individual design considerations for gaze + dwell, check out [eye-gaze + dwell](gaze-and-dwell-eyes.md) and [head-gaze + dwell](gaze-and-dwell-head.md).</span></span>


## <a name="transitioning-in-and-out-of-hands-free"></a><span data-ttu-id="7a983-125">Transizione all'interno e all'esterno di Hands-Free</span><span class="sxs-lookup"><span data-stu-id="7a983-125">Transitioning in and out of hands-free</span></span>

<span data-ttu-id="7a983-126">Per questi scenari, liberare le mani dall'interazione con gli ologrammi per i comandi e la navigazione può variare da un requisito assoluto per il funzionamento dell'applicazione, end-to-end, a un ulteriore vantaggio che l'utente può eseguire la transizione da e verso l'esterno in qualsiasi momento.</span><span class="sxs-lookup"><span data-stu-id="7a983-126">For these scenarios, freeing your hands from interacting with holograms for commanding and navigation can range from being an absolute requirement to operating the application, end-to-end, to an added convenience that the user can transition in and out of at any time.</span></span> 

<span data-ttu-id="7a983-127">Se il requisito dell'applicazione è che verrà sempre usato senza intervento, sia che si tratti di un'abitazione, di comandi vocali personalizzati o del singolo comando Voice, "Select", assicurarsi di creare le sistemazioni appropriate nell'interfaccia utente.</span><span class="sxs-lookup"><span data-stu-id="7a983-127">If the requirement of the application is that it will always be used hands-free, whether by using dwell, custom voice commands, or the single voice command, "select", then make sure to make the appropriate accommodations in your UI.</span></span> 

<span data-ttu-id="7a983-128">Se l'utente di destinazione deve essere in grado di passare da una mano all'altra a loro discrezione, è importante tenere conto dei principi seguenti.</span><span class="sxs-lookup"><span data-stu-id="7a983-128">If your target user needs to be able to switch from hands to hands-free at their discretion, then it is important to take the following principles into account.</span></span>

### <a name="assume-the-user-is-already-in-the-mode-that-they-want-to-switch-to"></a><span data-ttu-id="7a983-129">Si supponga che l'utente sia già nella modalità a cui si desidera passare</span><span class="sxs-lookup"><span data-stu-id="7a983-129">Assume the user is already in the mode that they want to switch to</span></span>
<span data-ttu-id="7a983-130">Ad esempio, se l'utente si trova in fabbrica, guardando un riferimento video sulla sua HoloLens e decide di prelevare una chiave per iniziare a lavorare, probabilmente inizierà a lavorare in modo pratico senza dover posizionare la chiave per premere un pulsante.</span><span class="sxs-lookup"><span data-stu-id="7a983-130">For instance, if the user is on the factory floor, watching a video reference on her HoloLens, and decides to pick up a wrench to start working, she most likely would start working in hands-free without having to put down the wrench to press a button.</span></span> <span data-ttu-id="7a983-131">Dovrebbe essere in grado di richiamare una sessione vocale con un comando Voice, soffermarsi su un'interfaccia utente già visibile per iniziare a soffermarsi o pronunciare la parola "Select".</span><span class="sxs-lookup"><span data-stu-id="7a983-131">She should be able to invoke a voice session with a voice command, dwell on an already-visible UI to begin dwell, or say the word "select".</span></span>

<span data-ttu-id="7a983-132">L'utente deve avere la possibilità di:</span><span class="sxs-lookup"><span data-stu-id="7a983-132">The user should have the ability to:</span></span> 
* <span data-ttu-id="7a983-133">Passa a vivavoce senza intervento</span><span class="sxs-lookup"><span data-stu-id="7a983-133">Switch to hands-free while hands-free</span></span>
* <span data-ttu-id="7a983-134">Passa a mano</span><span class="sxs-lookup"><span data-stu-id="7a983-134">Switch to hands with your hands</span></span>
* <span data-ttu-id="7a983-135">Passare al controller usando un controller</span><span class="sxs-lookup"><span data-stu-id="7a983-135">Switch to the controller using a controller</span></span> 

### <a name="create-redundant-ways-to-switch-modes"></a><span data-ttu-id="7a983-136">Creare modi ridondanti per cambiare modalità</span><span class="sxs-lookup"><span data-stu-id="7a983-136">Create redundant ways to switch modes</span></span>
<span data-ttu-id="7a983-137">Mentre il primo principio riguarda l'accesso, il secondo riguarda la disponibilità.</span><span class="sxs-lookup"><span data-stu-id="7a983-137">While the first principle is about access, the second one is about availability.</span></span> <span data-ttu-id="7a983-138">Non dovrebbe essere presente un solo modo per eseguire la transizione all'interno e all'esterno di una modalità.</span><span class="sxs-lookup"><span data-stu-id="7a983-138">There should not just be a single way to transition in and out of a mode.</span></span> 

<span data-ttu-id="7a983-139">Di seguito sono riportati alcuni esempi:</span><span class="sxs-lookup"><span data-stu-id="7a983-139">Some examples would be:</span></span> 
* <span data-ttu-id="7a983-140">Pulsante per l'inizio delle interazioni vocali</span><span class="sxs-lookup"><span data-stu-id="7a983-140">A button to begin voice interactions</span></span>
* <span data-ttu-id="7a983-141">Un comando vocale a cui passare, usando l'Head-sguardi e l'abitazione</span><span class="sxs-lookup"><span data-stu-id="7a983-141">A voice command to transition to, using head-gaze and dwell</span></span>

### <a name="add-a-dash-of-drama"></a><span data-ttu-id="7a983-142">Aggiungere un trattino di dramma</span><span class="sxs-lookup"><span data-stu-id="7a983-142">Add a dash of drama</span></span>
<span data-ttu-id="7a983-143">Un cambio di modalità è molto importante, quando queste transizioni si verificano come uno esplicito, anche un cambio drammatico, per consentire all'utente di sapere cosa è successo.</span><span class="sxs-lookup"><span data-stu-id="7a983-143">A mode switch is a big deal--it is important that when these transitions happen that they be an explicit, even a dramatic switch, to let the user know what happened.</span></span> 


## <a name="usability-checklist"></a><span data-ttu-id="7a983-144">Elenco di controllo dell'usabilità</span><span class="sxs-lookup"><span data-stu-id="7a983-144">Usability checklist</span></span>

<span data-ttu-id="7a983-145">**L'utente può eseguire tutte le operazioni e tutto ciò che si può fare senza alcun intervento end-to-end?**</span><span class="sxs-lookup"><span data-stu-id="7a983-145">**Can the user do everything and anything hands-free, end-to-end?**</span></span>
* <span data-ttu-id="7a983-146">Ogni interoperabilità deve essere Hands-Free accessibile</span><span class="sxs-lookup"><span data-stu-id="7a983-146">Every interactable should be accessible hands-free</span></span>
* <span data-ttu-id="7a983-147">Assicurarsi che sia presente una sostituzione per tutti i movimenti personalizzati, ad esempio il ridimensionamento, l'inserimento, il scorrimento, i rubinetti e così via.</span><span class="sxs-lookup"><span data-stu-id="7a983-147">Ensure that there is a replacement for all custom gestures, such as resizing, placing, swipes, taps, etc.</span></span>
* <span data-ttu-id="7a983-148">Assicurarsi che l'utente abbia il controllo della presenza, della posizione e del livello di dettaglio dell'interfaccia utente in qualsiasi momento</span><span class="sxs-lookup"><span data-stu-id="7a983-148">Ensure that the user has confident control of UI presence, placement, and verbosity at all times</span></span>
    * <span data-ttu-id="7a983-149">Recupero dell'interfaccia utente</span><span class="sxs-lookup"><span data-stu-id="7a983-149">Getting UI out of the way</span></span>
    * <span data-ttu-id="7a983-150">Indirizzamento dell'interfaccia utente fuori campo di visualizzazione (FOV)</span><span class="sxs-lookup"><span data-stu-id="7a983-150">Addressing UI that is out of field of view (FOV)</span></span>
    * <span data-ttu-id="7a983-151">Quanto vedo, dove, quando</span><span class="sxs-lookup"><span data-stu-id="7a983-151">How much I see, where, when</span></span>

<span data-ttu-id="7a983-152">**La meccanica dell'interazione viene insegnata e rafforzata con la affordances corretta?**</span><span class="sxs-lookup"><span data-stu-id="7a983-152">**Are the mechanics of the interaction being taught and reinforced with the right affordances?**</span></span>

<span data-ttu-id="7a983-153">Informazioni sull'utente...</span><span class="sxs-lookup"><span data-stu-id="7a983-153">Does the user understand ...</span></span>
* <span data-ttu-id="7a983-154">... Modalità di funzionamento</span><span class="sxs-lookup"><span data-stu-id="7a983-154">... What mode they are in?</span></span>
* <span data-ttu-id="7a983-155">... Cosa si può fare in questa modalità?</span><span class="sxs-lookup"><span data-stu-id="7a983-155">... What they can do in this mode?</span></span>
* <span data-ttu-id="7a983-156">... Qual è lo stato corrente?</span><span class="sxs-lookup"><span data-stu-id="7a983-156">... What is the current state?</span></span>
* <span data-ttu-id="7a983-157">... In che modo è possibile eseguire la transizione?</span><span class="sxs-lookup"><span data-stu-id="7a983-157">... How they can transition out?</span></span>
    
<span data-ttu-id="7a983-158">**L'interfaccia utente è ottimizzata per l'Hand-Free?**</span><span class="sxs-lookup"><span data-stu-id="7a983-158">**Is the UI optimized for hands-free?**</span></span>   

* <span data-ttu-id="7a983-159">Esempio: i affordances di abitazione non sono incorporati nei modelli 2D tipici</span><span class="sxs-lookup"><span data-stu-id="7a983-159">Example: Dwell affordances are not built-in to typical 2D patterns</span></span>
* <span data-ttu-id="7a983-160">Esempio: il targeting vocale è migliore con l'evidenziazione degli oggetti</span><span class="sxs-lookup"><span data-stu-id="7a983-160">Example: Voice targeting is better with object highlighting</span></span>
* <span data-ttu-id="7a983-161">Esempio: le interazioni vocali sono migliori con le didascalie che devono essere attivate</span><span class="sxs-lookup"><span data-stu-id="7a983-161">Example: Voice interactions are better with captions that need to be turned on</span></span>


## <a name="see-also"></a><span data-ttu-id="7a983-162">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="7a983-162">See also</span></span>
* [<span data-ttu-id="7a983-163">Tracciamento oculare in HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="7a983-163">Eye tracking on HoloLens 2</span></span>](eye-tracking.md)
* [<span data-ttu-id="7a983-164">Sguardo e commit</span><span class="sxs-lookup"><span data-stu-id="7a983-164">Gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="7a983-165">Sguardo fisso e attesa</span><span class="sxs-lookup"><span data-stu-id="7a983-165">Gaze and dwell</span></span>](gaze-and-dwell.md)
* [<span data-ttu-id="7a983-166">Mani - Manipolazione diretta</span><span class="sxs-lookup"><span data-stu-id="7a983-166">Hands - Direct manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="7a983-167">Mani - Movimenti</span><span class="sxs-lookup"><span data-stu-id="7a983-167">Hands - Gestures</span></span>](gaze-and-commit.md#composite-gestures)
* [<span data-ttu-id="7a983-168">Mani - Puntamento e commit</span><span class="sxs-lookup"><span data-stu-id="7a983-168">Hands - Point and commit</span></span>](point-and-commit.md)
* [<span data-ttu-id="7a983-169">Interazioni istintive</span><span class="sxs-lookup"><span data-stu-id="7a983-169">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="7a983-170">Input vocale</span><span class="sxs-lookup"><span data-stu-id="7a983-170">Voice input</span></span>](voice-input.md)

---
title: Cursori
description: Un cursore, o un indicatore del vettore di destinazione, fornisce un feedback continuo all'utente per comprendere quali sono le intenzioni di HoloLens.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: HoloLens (1st Gen), HoloLens 2, realtà mista, cursori, targeting, sguardi, movimenti, cuffie per realtà mista, auricolare di realtà mista di Windows, auricolare in realtà virtuale, HoloLens, MRTK, Toolkit realtà mista, raggi, input
ms.openlocfilehash: 0b35c832e6d13ff10d14686909754de60b83fa23
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/03/2021
ms.locfileid: "101759417"
---
# <a name="cursors"></a><span data-ttu-id="1cd78-104">Cursori</span><span class="sxs-lookup"><span data-stu-id="1cd78-104">Cursors</span></span>

![Cursori](images/UX_Hero_Cursor.jpg)

<span data-ttu-id="1cd78-106">Un cursore fornisce un feedback continuo in base al punto in cui l'auricolare ritiene che lo stato attivo corrente degli utenti sia in un determinato momento.</span><span class="sxs-lookup"><span data-stu-id="1cd78-106">A cursor provides continuous feedback based on where the headset believes a users current focus is at a given time.</span></span> <span data-ttu-id="1cd78-107">Il feedback del cursore include l'area, l'ologramma o il punto dell'ambiente virtuale che risponde all'input.</span><span class="sxs-lookup"><span data-stu-id="1cd78-107">Cursor feedback includes what area, hologram, or point in the virtual environment responds to input.</span></span> <span data-ttu-id="1cd78-108">Anche se il cursore è una rappresentazione digitale del punto in cui il dispositivo riconosce l'attenzione dell'utente, non è uguale alla determinazione delle intenzioni dell'utente.</span><span class="sxs-lookup"><span data-stu-id="1cd78-108">Even though the cursor is a digital representation of where the device understands the user's attention to be, that's not the same as determining the user's intentions.</span></span> <span data-ttu-id="1cd78-109">Il feedback del cursore consente inoltre agli utenti di sapere quali risposte di sistema prevedere.</span><span class="sxs-lookup"><span data-stu-id="1cd78-109">The cursor feedback also lets users know what system responses to expect.</span></span> <span data-ttu-id="1cd78-110">È possibile usare il feedback per comunicare la loro intenzione al dispositivo, aumentando la confidenza degli utenti.</span><span class="sxs-lookup"><span data-stu-id="1cd78-110">You can use the feedback to communicate their intention to the device, which increases user confidence.</span></span>

<span data-ttu-id="1cd78-111">Sono disponibili tre tipi di cursori: **Finger, Ray** e **Head-sguardi**.</span><span class="sxs-lookup"><span data-stu-id="1cd78-111">There are 3 kinds of cursors: **finger, ray**, and **head-gaze**.</span></span> <span data-ttu-id="1cd78-112">Questi puntatori funzionano con diverse modalità di input in HoloLens, HoloLens 2 e auricolari immersivi.</span><span class="sxs-lookup"><span data-stu-id="1cd78-112">These pointing cursors work with different input modalities on HoloLens, HoloLens 2, and immersive headsets.</span></span> <span data-ttu-id="1cd78-113">Di seguito sono riportate informazioni aggiuntive sul tipo di cursore da usare per ogni tipo di modello di auricolare e interazione.</span><span class="sxs-lookup"><span data-stu-id="1cd78-113">Below is guidance on which type of cursor to use for each type of headset and interaction model.</span></span> <span data-ttu-id="1cd78-114">Nel Toolkit di realtà mista (MRTK) sono stati creati moduli per i cursori con trascinamento della selezione che consentono di creare l'esperienza di puntamento corretta.</span><span class="sxs-lookup"><span data-stu-id="1cd78-114">In the Mixed Reality Toolkit (MRTK), we've created drag-and-drop cursors modules to help you build the right pointing experience.</span></span>

## <a name="device-support"></a><span data-ttu-id="1cd78-115">Supporto di dispositivi</span><span class="sxs-lookup"><span data-stu-id="1cd78-115">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="1cd78-116"><strong>Funzionalità</strong></span><span class="sxs-lookup"><span data-stu-id="1cd78-116"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="1cd78-117"><a href="/hololens/hololens1-hardware"><strong>HoloLens (prima generazione)</strong></a></span><span class="sxs-lookup"><span data-stu-id="1cd78-117"><a href="/hololens/hololens1-hardware"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="1cd78-118"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="1cd78-118"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="1cd78-119"><a href="../discover/immersive-headset-hardware-details.md"><strong>Visori VR immersive</strong></a></span><span class="sxs-lookup"><span data-stu-id="1cd78-119"><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="1cd78-120">Cursore dito</span><span class="sxs-lookup"><span data-stu-id="1cd78-120">Finger cursor</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="1cd78-121">✔️</span><span class="sxs-lookup"><span data-stu-id="1cd78-121">✔️</span></span></td>
        <td>❌</td>
    </tr>
     <tr>
        <td><span data-ttu-id="1cd78-122">Cursore Ray</span><span class="sxs-lookup"><span data-stu-id="1cd78-122">Ray cursor</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="1cd78-123">✔️</span><span class="sxs-lookup"><span data-stu-id="1cd78-123">✔️</span></span></td>
        <td><span data-ttu-id="1cd78-124">✔️</span><span class="sxs-lookup"><span data-stu-id="1cd78-124">✔️</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="1cd78-125">Cursore Head-sguardi</span><span class="sxs-lookup"><span data-stu-id="1cd78-125">Head-gaze cursor</span></span></td>
        <td><span data-ttu-id="1cd78-126">✔️</span><span class="sxs-lookup"><span data-stu-id="1cd78-126">✔️</span></span></td>
        <td><span data-ttu-id="1cd78-127">✔️</span><span class="sxs-lookup"><span data-stu-id="1cd78-127">✔️</span></span></td>
        <td><span data-ttu-id="1cd78-128">✔️</span><span class="sxs-lookup"><span data-stu-id="1cd78-128">✔️</span></span></td>
    </tr>
</table>

## <a name="finger-cursor"></a><span data-ttu-id="1cd78-129">Cursore dito</span><span class="sxs-lookup"><span data-stu-id="1cd78-129">Finger cursor</span></span>

<span data-ttu-id="1cd78-130">Il cursore Finger è disponibile solo in HoloLens 2 per migliorare la modalità di interazione "[manipolazione diretta con mani](direct-manipulation.md)".</span><span class="sxs-lookup"><span data-stu-id="1cd78-130">The finger cursor is only available on the HoloLens 2 to enhance the "[direct manipulation with hands](direct-manipulation.md)" interaction mode.</span></span> <span data-ttu-id="1cd78-131">Sono stati collegati anelli ai suggerimenti di entrambi gli indici Fingers per comprendere meglio la posizione del dito.</span><span class="sxs-lookup"><span data-stu-id="1cd78-131">We've attached rings to the tips of both index fingers to better understand where the finger is pointing.</span></span> <span data-ttu-id="1cd78-132">La dimensione dell'anello si basa sulla prossimità del dito alla superficie dell'interfaccia utente, che si riduce a un piccolo punto quando il dito tocca l'interfaccia utente.</span><span class="sxs-lookup"><span data-stu-id="1cd78-132">The ring size is based on the proximity of the finger to the UI surface, which shrinks to a small dot when the finger touches the UI.</span></span> <span data-ttu-id="1cd78-133">Maggiore è il dito, minore è l'anello.</span><span class="sxs-lookup"><span data-stu-id="1cd78-133">The closer the finger, the smaller the ring.</span></span> <br>

<span data-ttu-id="1cd78-134">![cursore dito](images/finger-cursor.png)</span><span class="sxs-lookup"><span data-stu-id="1cd78-134">![finger cursor](images/finger-cursor.png)</span></span><br>
<span data-ttu-id="1cd78-135">**Stati feedback visivi del cursore dito** 1: l'anello si riduce a un punto.</span><span class="sxs-lookup"><span data-stu-id="1cd78-135">**Visual feedback states of finger cursor** 1: The ring shrinks to a dot.</span></span> <span data-ttu-id="1cd78-136">2: l'anello è allineato alla superficie.</span><span class="sxs-lookup"><span data-stu-id="1cd78-136">2: The ring aligns with surface.</span></span> <span data-ttu-id="1cd78-137">3: l'anello è perpendicolare al vettore del dito.</span><span class="sxs-lookup"><span data-stu-id="1cd78-137">3: The ring is perpendicular to finger vector.</span></span> <span data-ttu-id="1cd78-138">4: nessun anello.</span><span class="sxs-lookup"><span data-stu-id="1cd78-138">4: No ring.</span></span>

## <a name="ray-cursor"></a><span data-ttu-id="1cd78-139">Cursore Ray</span><span class="sxs-lookup"><span data-stu-id="1cd78-139">Ray cursor</span></span>

<span data-ttu-id="1cd78-140">I cursori raggio si allineano alla fine dei raggi di puntamento per consentire la manipolazione di oggetti fuori dalla portata di mano.</span><span class="sxs-lookup"><span data-stu-id="1cd78-140">Ray cursors attach to the end of far pointing rays to allow manipulation of objects that are out of hands-reach.</span></span> <span data-ttu-id="1cd78-141">Negli auricolari immersivi, i raggi vengono ritirati dai controller di movimento e terminano con i cursori a punti.</span><span class="sxs-lookup"><span data-stu-id="1cd78-141">In immersive headsets, the rays shoot out from motion controllers and end in dot cursors.</span></span> <span data-ttu-id="1cd78-142">In HoloLens 2 viene applicato il modello mentale di questi raggi del controller di movimento e i raggi mano progettati che hanno origine dalle palme e terminano con cursori a forma di anello coerenti con i cursori a dito usati nella manipolazione diretta.</span><span class="sxs-lookup"><span data-stu-id="1cd78-142">In HoloLens 2, we apply the mental model of these motion controller rays and designed hand rays that originate from the palms and end in ring-shaped cursors that are consistent with finger cursors used in direct manipulation.</span></span> <br>
:::row:::
    :::column:::
        <span data-ttu-id="1cd78-143">![Controller del cursore Ray](images/ray-cursor-controller.png)</span><span class="sxs-lookup"><span data-stu-id="1cd78-143">![Ray cursor controller](images/ray-cursor-controller.png)</span></span><br>
        <span data-ttu-id="1cd78-144">**Cursori Ray dei controller di movimento**</span><span class="sxs-lookup"><span data-stu-id="1cd78-144">**Ray cursors of motion controllers**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="1cd78-145">![Mano del cursore Ray](images/ray-cursor-hand.png)</span><span class="sxs-lookup"><span data-stu-id="1cd78-145">![Ray cursor hand](images/ray-cursor-hand.png)</span></span><br>
        <span data-ttu-id="1cd78-146">**Cursori raggio delle mani**</span><span class="sxs-lookup"><span data-stu-id="1cd78-146">**Ray cursors of hands**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="head-gaze-cursor"></a><span data-ttu-id="1cd78-147">Cursore Head-sguardi</span><span class="sxs-lookup"><span data-stu-id="1cd78-147">Head-gaze cursor</span></span>

<span data-ttu-id="1cd78-148">Il cursore Head-sguardi è un punto che si connette alla fine di un vettore di sguardi invisibili che usa la posizione e la rotazione dell'intestazione verso il punto.</span><span class="sxs-lookup"><span data-stu-id="1cd78-148">The head-gaze cursor is a dot that attaches to the end of an invisible head-gaze vector that uses the position and rotation of the head to point.</span></span> <span data-ttu-id="1cd78-149">Per eseguire le azioni, questo cursore di puntamento è associato a diversi input di commit, ad esempio il tocco aereo, i comandi vocali, l'abitazione e la pressione del pulsante.</span><span class="sxs-lookup"><span data-stu-id="1cd78-149">To execute actions, this pointing cursor is paired with various commit inputs such as air tap, voice commands, dwell, and button press.</span></span> <span data-ttu-id="1cd78-150">In HoloLens 2, il punto di partenza è meglio abbinato a qualsiasi input di commit che non è un rubinetto d'aria, in quanto si verifica un conflitto di interazione tra il tocco aereo e i raggi di mano.</span><span class="sxs-lookup"><span data-stu-id="1cd78-150">In HoloLens 2, head-gaze is best paired with any commit input that isn't air tap, as there will be interaction conflict between air tap and far hand rays.</span></span> <br>
:::row:::
    :::column:::
        <span data-ttu-id="1cd78-151">![Mano del cursore della testa](images/head-gaze-cursor-hand.png)</span><span class="sxs-lookup"><span data-stu-id="1cd78-151">![Head gaze cursor hand](images/head-gaze-cursor-hand.png)</span></span><br>
        <span data-ttu-id="1cd78-152">**Cursore Head-sguardi con movimento mano**</span><span class="sxs-lookup"><span data-stu-id="1cd78-152">**Head-gaze cursor with hand gesture**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="1cd78-153">![Voce cursore sguardo](images/head-gaze-cursor-voice.png)</span><span class="sxs-lookup"><span data-stu-id="1cd78-153">![Head gaze cursor voice](images/head-gaze-cursor-voice.png)</span></span><br>
        <span data-ttu-id="1cd78-154">**Cursore Head-sguardi con comando Voice**</span><span class="sxs-lookup"><span data-stu-id="1cd78-154">**Head-gaze cursor with voice command**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="cursor-customization-recommendations"></a><span data-ttu-id="1cd78-155">Suggerimenti sulla personalizzazione del cursore</span><span class="sxs-lookup"><span data-stu-id="1cd78-155">Cursor customization recommendations</span></span>

<span data-ttu-id="1cd78-156">Se si desidera personalizzare i comportamenti e le caratteristiche di feedback del cursore, di seguito sono riportate alcune indicazioni sulla progettazione:</span><span class="sxs-lookup"><span data-stu-id="1cd78-156">If you would like to customize the cursor feedback behaviors and appearances, here are some design recommendations:</span></span>

### <a name="cursor-scale"></a><span data-ttu-id="1cd78-157">Scala del cursore</span><span class="sxs-lookup"><span data-stu-id="1cd78-157">Cursor scale</span></span>

* <span data-ttu-id="1cd78-158">Il cursore non deve essere più grande delle destinazioni disponibili, consentendo agli utenti di interagire con facilità e di visualizzare il contenuto.</span><span class="sxs-lookup"><span data-stu-id="1cd78-158">The cursor should be no larger than the available targets, allowing users to easily interact with and view the content.</span></span>
* <span data-ttu-id="1cd78-159">A seconda dell'esperienza creata, il ridimensionamento del cursore mentre l'utente si trova è anche una considerazione importante.</span><span class="sxs-lookup"><span data-stu-id="1cd78-159">Depending on the experience you create, scaling the cursor as the user looks around is also an important consideration.</span></span> <span data-ttu-id="1cd78-160">Ad esempio, man mano che l'utente ha una maggiore esperienza nell'esperienza, il cursore non dovrebbe diventare troppo piccolo in modo che vada perduto.</span><span class="sxs-lookup"><span data-stu-id="1cd78-160">For example, as the user looks further away in your experience, the cursor shouldn't become too small such that it's lost.</span></span>
* <span data-ttu-id="1cd78-161">Quando si ridimensiona il cursore, prendere in considerazione l'applicazione di un'animazione soft mentre viene ridimensionata in modo da ottenere un senso organico.</span><span class="sxs-lookup"><span data-stu-id="1cd78-161">When scaling the cursor, consider applying a soft animation to it as it scales to give it an organic feeling.</span></span>
* <span data-ttu-id="1cd78-162">Evitare di ostacolare il contenuto.</span><span class="sxs-lookup"><span data-stu-id="1cd78-162">Avoid obstructing content.</span></span> <span data-ttu-id="1cd78-163">Gli ologrammi sono gli elementi che rendono memorabile l'esperienza e il cursore non dovrebbe allontanarsi da essi.</span><span class="sxs-lookup"><span data-stu-id="1cd78-163">Holograms are what make the experience memorable and the cursor shouldn't be taking away from them.</span></span>

### <a name="directionless-cursor-shape"></a><span data-ttu-id="1cd78-164">Forma cursore direzionale</span><span class="sxs-lookup"><span data-stu-id="1cd78-164">Directionless cursor shape</span></span>

* <span data-ttu-id="1cd78-165">Sebbene non esista una forma di cursore corretta, è consigliabile usare una forma senza direzione come un toro.</span><span class="sxs-lookup"><span data-stu-id="1cd78-165">Although there's no one right cursor shape, we recommend that you use a directionless shape like a torus.</span></span> <span data-ttu-id="1cd78-166">Un cursore che punta in una direzione, ad esempio un cursore a freccia tradizionale, potrebbe confondere l'utente in modo che sia sempre simile.</span><span class="sxs-lookup"><span data-stu-id="1cd78-166">A cursor that points in some direction (For example, a traditional arrow cursor) might confuse the user to always look that way.</span></span>
* <span data-ttu-id="1cd78-167">Un'eccezione è rappresentata dall'utilizzo del cursore per la comunicazione dell'istruzione di interazione con l'utente.</span><span class="sxs-lookup"><span data-stu-id="1cd78-167">An exception to this is when using the cursor to communicate interaction instruction to the user.</span></span> <span data-ttu-id="1cd78-168">Ad esempio, quando si ridimensionano gli ologrammi nel sistema operativo di realtà mista, il cursore include temporaneamente frecce che indicano all'utente come spostare la mano per ridimensionare l'ologramma.</span><span class="sxs-lookup"><span data-stu-id="1cd78-168">For example, when scaling holograms in the Mixed Reality OS, the cursor temporarily includes arrows that instructs the user on how to move their hand to scale the hologram.</span></span>

### <a name="look-and-feel"></a><span data-ttu-id="1cd78-169">Aspetto</span><span class="sxs-lookup"><span data-stu-id="1cd78-169">Look and feel</span></span>

* <span data-ttu-id="1cd78-170">Un cursore a forma di ciambella o toro funziona per molte applicazioni.</span><span class="sxs-lookup"><span data-stu-id="1cd78-170">A donut or torus shaped cursor works for many applications.</span></span>
* <span data-ttu-id="1cd78-171">Selezionare un colore e una forma che rappresenti al meglio l'esperienza che si sta creando.</span><span class="sxs-lookup"><span data-stu-id="1cd78-171">Pick a color and shape that best represents the experience you're creating.</span></span>
* <span data-ttu-id="1cd78-172">I cursori sono particolarmente soggetti alla [separazione dei colori](../develop/platform-capabilities-and-apis/hologram-stability.md#color-separation).</span><span class="sxs-lookup"><span data-stu-id="1cd78-172">Cursors are especially prone to [color separation](../develop/platform-capabilities-and-apis/hologram-stability.md#color-separation).</span></span>
* <span data-ttu-id="1cd78-173">Un piccolo cursore con opacità bilanciata mantiene informativo senza dominare la gerarchia visiva.</span><span class="sxs-lookup"><span data-stu-id="1cd78-173">A small cursor with balanced opacity keeps it informative without dominating the visual hierarchy.</span></span>
* <span data-ttu-id="1cd78-174">Tenere presente che l'uso di ombre o evidenziazioni dietro il cursore potrebbe ostacolare il contenuto e distrarre dall'attività.</span><span class="sxs-lookup"><span data-stu-id="1cd78-174">Be cognizant of using shadows or highlights behind your cursor as they might obstruct content and distract from the task at hand.</span></span>
* <span data-ttu-id="1cd78-175">I cursori devono allinearsi e abbracciare le superfici nell'app.</span><span class="sxs-lookup"><span data-stu-id="1cd78-175">Cursors should align to and hug the surfaces in your app.</span></span> <span data-ttu-id="1cd78-176">Gli utenti avranno la sensazione che il sistema sia in grado di individuare il punto in cui si trovano, ma anche che il sistema sia in grado di riconoscere il proprio ambiente.</span><span class="sxs-lookup"><span data-stu-id="1cd78-176">Users will have a feeling that the system can see where they're looking, but also that the system is aware of their surroundings.</span></span> <span data-ttu-id="1cd78-177">Ad esempio, il cursore nel sistema operativo di realtà mista è allineato alle superfici del mondo dell'utente, creando una sensazione di consapevolezza del mondo anche quando l'utente non guarda direttamente un ologramma.</span><span class="sxs-lookup"><span data-stu-id="1cd78-177">For example, the cursor in the Mixed Reality OS aligns to the surfaces of the user's world, creating a feeling of awareness of the world even when the user isn't looking directly at a hologram.</span></span>
* <span data-ttu-id="1cd78-178">Il blocco magnetico del cursore a un elemento interattivo quando è vicino all'utente può contribuire a migliorare la sicurezza che l'utente interagirà con tale elemento quando usa un'azione di selezione.</span><span class="sxs-lookup"><span data-stu-id="1cd78-178">Magnetically locking the cursor to an interactive element when it's close to the user can help improve confidence that user will interact with that element when they use a selection action.</span></span>

### <a name="visual-cues"></a><span data-ttu-id="1cd78-179">Segnali visivi</span><span class="sxs-lookup"><span data-stu-id="1cd78-179">Visual cues</span></span>

* <span data-ttu-id="1cd78-180">Se l'esperienza è incentrata su un solo ologramma, il cursore dovrebbe allinearsi e abbracciare solo tale ologramma e modificare la forma quando si è lontani dall'ologramma.</span><span class="sxs-lookup"><span data-stu-id="1cd78-180">If your experience is focused on a single hologram, your cursor should align and hug only that hologram and change shape when you look away from that hologram.</span></span> <span data-ttu-id="1cd78-181">Ciò può comportare all'utente che l'ologramma è interoperabile e può interagire con esso.</span><span class="sxs-lookup"><span data-stu-id="1cd78-181">This can convey to the user that the hologram is actionable and they can interact with it.</span></span>
* <span data-ttu-id="1cd78-182">Se l'applicazione usa il mapping spaziale, il cursore potrebbe allinearsi e abbracciare ogni superficie che vede.</span><span class="sxs-lookup"><span data-stu-id="1cd78-182">If your application uses spatial mapping, then your cursor could align and hug every surface it sees.</span></span> <span data-ttu-id="1cd78-183">In questo modo viene fornito un feedback agli utenti che HoloLens e l'applicazione possono visualizzare il proprio spazio.</span><span class="sxs-lookup"><span data-stu-id="1cd78-183">This gives feedback to the users that HoloLens and your application can see their space.</span></span> <span data-ttu-id="1cd78-184">Questo rafforza il fatto che gli ologrammi sono reali e in questo mondo e contribuiscono a colmare il divario tra il reale e il virtuale.</span><span class="sxs-lookup"><span data-stu-id="1cd78-184">This reinforces the fact that holograms are real and in our world and helps bridge the gap between real and virtual.</span></span>
* <span data-ttu-id="1cd78-185">Avere un'idea di cosa deve fare il cursore quando non sono presenti ologrammi o superfici in visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="1cd78-185">Have an idea of what the cursor should do when there are no holograms or surfaces in view.</span></span> <span data-ttu-id="1cd78-186">Il posizionamento a una distanza predeterminata davanti all'utente è un'opzione.</span><span class="sxs-lookup"><span data-stu-id="1cd78-186">Placing it at a predetermined distance in front of the user is one option.</span></span>

### <a name="possible-actions"></a><span data-ttu-id="1cd78-187">Azioni possibili</span><span class="sxs-lookup"><span data-stu-id="1cd78-187">Possible actions</span></span>

* <span data-ttu-id="1cd78-188">Il cursore può essere rappresentato da icone diverse per indicare le possibili azioni che possono essere eseguite da un ologramma, ad esempio il ridimensionamento o la rotazione.</span><span class="sxs-lookup"><span data-stu-id="1cd78-188">The cursor can be represented by different icons to convey possible actions a hologram can do, such as scaling or rotation.</span></span>
* <span data-ttu-id="1cd78-189">Aggiungere al cursore informazioni aggiuntive solo se significa qualcosa per l'utente.</span><span class="sxs-lookup"><span data-stu-id="1cd78-189">Only add extra information on the cursor if it means something to the user.</span></span> <span data-ttu-id="1cd78-190">In caso contrario, gli utenti potrebbero non osservare le modifiche dello stato o essere confuse dal cursore.</span><span class="sxs-lookup"><span data-stu-id="1cd78-190">Otherwise, users might either not notice the state changes or get confused by the cursor.</span></span>

### <a name="input-state"></a><span data-ttu-id="1cd78-191">Stato input</span><span class="sxs-lookup"><span data-stu-id="1cd78-191">Input state</span></span>

* <span data-ttu-id="1cd78-192">È possibile utilizzare il cursore per visualizzare lo stato o la finalità di input dell'utente.</span><span class="sxs-lookup"><span data-stu-id="1cd78-192">We could use the cursor to display the user's input state or intent.</span></span> <span data-ttu-id="1cd78-193">Ad esempio, è possibile visualizzare un'icona che informa l'utente che il sistema rileva lo stato della mano e che l'applicazione sa che è pronto a intervenire.</span><span class="sxs-lookup"><span data-stu-id="1cd78-193">For example, we could display an icon telling the user the system sees their hand state and that the application knows they're ready to take action.</span></span>
* <span data-ttu-id="1cd78-194">È anche possibile usare il cursore per mostrare agli utenti che i comandi vocali sono stati uditi dal sistema con una modifica del colore momentanea</span><span class="sxs-lookup"><span data-stu-id="1cd78-194">We could also use the cursor to show users that voice commands have been heard by the system via a momentary color change</span></span>

* <span data-ttu-id="1cd78-195">Gli Stati del cursore seguenti possono essere implementati in modi diversi.</span><span class="sxs-lookup"><span data-stu-id="1cd78-195">The following cursor states can be implemented in different ways.</span></span> <span data-ttu-id="1cd78-196">È possibile implementare questi stati diversi modellando il cursore come una macchina a Stati.</span><span class="sxs-lookup"><span data-stu-id="1cd78-196">You might implement these different states by modeling the cursor like a state machine.</span></span> <span data-ttu-id="1cd78-197">Ad esempio:</span><span class="sxs-lookup"><span data-stu-id="1cd78-197">For example:</span></span>
    * <span data-ttu-id="1cd78-198">Lo stato di inattività è il punto in cui viene visualizzato il cursore predefinito.</span><span class="sxs-lookup"><span data-stu-id="1cd78-198">Idle state is where you show the default cursor.</span></span>
    * <span data-ttu-id="1cd78-199">Lo stato pronto è quando è stata rilevata la mano dell'utente nella posizione pronta.</span><span class="sxs-lookup"><span data-stu-id="1cd78-199">Ready state is when you've detected the user's hand in the ready position.</span></span>
    * <span data-ttu-id="1cd78-200">Lo stato di interazione è quando l'utente sta eseguendo una particolare interazione.</span><span class="sxs-lookup"><span data-stu-id="1cd78-200">Interaction state is when the user is doing a particular interaction.</span></span>
    * <span data-ttu-id="1cd78-201">Lo stato delle azioni possibili o il passaggio del mouse è quando si conferiscono azioni possibili che possono essere eseguite su un ologramma.</span><span class="sxs-lookup"><span data-stu-id="1cd78-201">Possible Actions state or hover state is when you convey possible actions that can be performed on a hologram.</span></span>

<span data-ttu-id="1cd78-202">È anche possibile implementare questi stati in modo che possano visualizzare risorse dell'arte diverse quando si rilevano stati diversi.</span><span class="sxs-lookup"><span data-stu-id="1cd78-202">You could also implement these states in a skin-able manner to display different art assets when you detect different states.</span></span>

<br>

---

## <a name="going-cursor-free"></a><span data-ttu-id="1cd78-203">"Senza cursore"</span><span class="sxs-lookup"><span data-stu-id="1cd78-203">Going "cursor-free"</span></span>

<span data-ttu-id="1cd78-204">La progettazione senza cursore è consigliata quando il senso di immersione è un componente chiave di un'esperienza e quando si puntano interazioni (tramite sguardo e movimento) non è necessaria una precisione notevole.</span><span class="sxs-lookup"><span data-stu-id="1cd78-204">Designing without a cursor is recommended when the sense of immersion is a key component of an experience and when pointing interactions (through gaze and gesture) don't require great precision.</span></span> <span data-ttu-id="1cd78-205">Il sistema deve comunque soddisfare i requisiti normali di un cursore: fornire agli utenti un feedback continuo sulla comprensione del sistema che punta e aiutarli a comunicare le proprie intenzioni al sistema.</span><span class="sxs-lookup"><span data-stu-id="1cd78-205">The system still needs to meet the normal requirements of a cursor: providing users with continuous feedback on the system's understanding of their pointing, and helping them to communicate their intentions to the system.</span></span> <span data-ttu-id="1cd78-206">Questo può essere raggiungibile attraverso altre modifiche di stato evidenti.</span><span class="sxs-lookup"><span data-stu-id="1cd78-206">This may be achievable through other noticeable state changes.</span></span>

<br>

---

## <a name="cursor-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="1cd78-207">Cursore in MRTK (Mixed Reality Toolkit) per Unity</span><span class="sxs-lookup"><span data-stu-id="1cd78-207">Cursor in MRTK (Mixed Reality Toolkit) for Unity</span></span>

<span data-ttu-id="1cd78-208">Per impostazione predefinita, [MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity) fornisce una precostruzione del cursore ([DefaultCursor. prefabbricate](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Prefabs/Cursors)) che ha lo stesso stato di visualizzazione del cursore di sistema della shell.</span><span class="sxs-lookup"><span data-stu-id="1cd78-208">By default, [MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity) provides a cursor prefab([DefaultCursor.prefab](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Prefabs/Cursors)) which has the same visual state as the shell's system cursor.</span></span> <span data-ttu-id="1cd78-209">Tale file viene assegnato in Pointers (Puntatori) nel profilo di input di MRTK.</span><span class="sxs-lookup"><span data-stu-id="1cd78-209">It's assigned in MRTK's Input profile, under Pointers.</span></span> <span data-ttu-id="1cd78-210">È possibile sostituire o personalizzare questo cursore per la propria esperienza.</span><span class="sxs-lookup"><span data-stu-id="1cd78-210">You can replace/customize this cursor for your experience.</span></span> <span data-ttu-id="1cd78-211">Per l'esperienza con l'input di rilevamento degli occhi, MRTK fornisce anche EyeGazeCursor, che presenta un oggetto visivo sottile per ridurre al minimo la distrazione.</span><span class="sxs-lookup"><span data-stu-id="1cd78-211">For the experience with eye-tracking input, MRTK also provides EyeGazeCursor, which has subtle visual to minimize the distraction.</span></span>

* [<span data-ttu-id="1cd78-212">MRTK - Profilo del puntatore</span><span class="sxs-lookup"><span data-stu-id="1cd78-212">MRTK - Pointer profile</span></span>](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/mixed-reality-configuration-guide.md#pointer-configuration)
* [<span data-ttu-id="1cd78-213">MRTK - Sistema di input</span><span class="sxs-lookup"><span data-stu-id="1cd78-213">MRTK - Input system</span></span>](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/input/overview.md)
* [<span data-ttu-id="1cd78-214">MRTK - Puntatori</span><span class="sxs-lookup"><span data-stu-id="1cd78-214">MRTK - Pointers</span></span>](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/input/pointers.md)

---

## <a name="see-also"></a><span data-ttu-id="1cd78-215">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="1cd78-215">See also</span></span>

* [<span data-ttu-id="1cd78-216">Movimenti</span><span class="sxs-lookup"><span data-stu-id="1cd78-216">Gestures</span></span>](gaze-and-commit.md#composite-gestures)
* [<span data-ttu-id="1cd78-217">Puntamento con la testa e commit</span><span class="sxs-lookup"><span data-stu-id="1cd78-217">Head-gaze and commit</span></span>](gaze-and-commit.md)
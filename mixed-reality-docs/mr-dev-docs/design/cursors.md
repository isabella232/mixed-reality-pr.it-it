---
title: Cursori
description: Un cursore, o indicatore del vettore di destinazione, fornisce un feedback continuo per l'utente per comprendere ciò che HoloLens comprende sulle proprie intenzioni.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: HoloLens (prima generazione), HoloLens 2, realtà mista, cursori, destinazione, sguardo, movimenti, visore di realtà mista, visore di realtà mista windows, visore di realtà virtuale, HoloLens, MRTK, Mixed Reality Toolkit, raggi, input
ms.openlocfilehash: 829d7b3f766f848228946ee0a623f9f3013adca3
ms.sourcegitcommit: 9ae76b339968f035c703d9c1fe57ddecb33198e3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/27/2021
ms.locfileid: "110600380"
---
# <a name="cursors"></a><span data-ttu-id="8160f-104">Cursori</span><span class="sxs-lookup"><span data-stu-id="8160f-104">Cursors</span></span>

![Cursori](images/UX_Hero_Cursor.jpg)

<span data-ttu-id="8160f-106">Un cursore fornisce feedback continuo in base al punto in cui il visore ritiene che lo stato attivo corrente degli utenti sia in un determinato momento.</span><span class="sxs-lookup"><span data-stu-id="8160f-106">A cursor provides continuous feedback based on where the headset believes a users current focus is at a given time.</span></span> <span data-ttu-id="8160f-107">Il feedback del cursore include l'area, l'ologramma o il punto nell'ambiente virtuale che risponde all'input.</span><span class="sxs-lookup"><span data-stu-id="8160f-107">Cursor feedback includes what area, hologram, or point in the virtual environment responds to input.</span></span> <span data-ttu-id="8160f-108">Anche se il cursore è una rappresentazione digitale di dove il dispositivo comprende l'attenzione dell'utente, questo non è lo stesso di determinare le intenzioni dell'utente.</span><span class="sxs-lookup"><span data-stu-id="8160f-108">Even though the cursor is a digital representation of where the device understands the user's attention to be, that's not the same as determining the user's intentions.</span></span> <span data-ttu-id="8160f-109">Il feedback del cursore consente inoltre agli utenti di conoscere le risposte del sistema previste.</span><span class="sxs-lookup"><span data-stu-id="8160f-109">The cursor feedback also lets users know what system responses to expect.</span></span> <span data-ttu-id="8160f-110">È possibile usare i commenti e suggerimenti per comunicare l'intenzione al dispositivo, in modo da aumentare l'attendibilità degli utenti.</span><span class="sxs-lookup"><span data-stu-id="8160f-110">You can use the feedback to communicate their intention to the device, which increases user confidence.</span></span>

<span data-ttu-id="8160f-111">Sono disponibili tre tipi di cursori: **dito, raggio** e **sguardo alla testa.**</span><span class="sxs-lookup"><span data-stu-id="8160f-111">There are 3 kinds of cursors: **finger, ray**, and **head-gaze**.</span></span> <span data-ttu-id="8160f-112">Questi cursori di puntamento funzionano con diverse modalità di input in HoloLens, HoloLens 2 e visori immersivi.</span><span class="sxs-lookup"><span data-stu-id="8160f-112">These pointing cursors work with different input modalities on HoloLens, HoloLens 2, and immersive headsets.</span></span> <span data-ttu-id="8160f-113">Di seguito sono riportate indicazioni sul tipo di cursore da usare per ogni tipo di visore e modello di interazione.</span><span class="sxs-lookup"><span data-stu-id="8160f-113">Below is guidance on which type of cursor to use for each type of headset and interaction model.</span></span> <span data-ttu-id="8160f-114">In Mixed Reality Toolkit (MRTK) sono stati creati moduli di cursori di trascinamento della selezione per facilitare la creazione dell'esperienza di puntamento.</span><span class="sxs-lookup"><span data-stu-id="8160f-114">In the Mixed Reality Toolkit (MRTK), we've created drag-and-drop cursors modules to help you build the right pointing experience.</span></span>

## <a name="device-support"></a><span data-ttu-id="8160f-115">Supporto di dispositivi</span><span class="sxs-lookup"><span data-stu-id="8160f-115">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="8160f-116"><strong>Funzionalità</strong></span><span class="sxs-lookup"><span data-stu-id="8160f-116"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="8160f-117"><a href="/hololens/hololens1-hardware"><strong>HoloLens (prima generazione)</strong></a></span><span class="sxs-lookup"><span data-stu-id="8160f-117"><a href="/hololens/hololens1-hardware"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="8160f-118"><a href="/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="8160f-118"><a href="/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="8160f-119"><a href="../discover/immersive-headset-hardware-details.md"><strong>Visori VR immersive</strong></a></span><span class="sxs-lookup"><span data-stu-id="8160f-119"><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="8160f-120">Cursore del dito</span><span class="sxs-lookup"><span data-stu-id="8160f-120">Finger cursor</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="8160f-121">✔️</span><span class="sxs-lookup"><span data-stu-id="8160f-121">✔️</span></span></td>
        <td>❌</td>
    </tr>
     <tr>
        <td><span data-ttu-id="8160f-122">Cursore Ray</span><span class="sxs-lookup"><span data-stu-id="8160f-122">Ray cursor</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="8160f-123">✔️</span><span class="sxs-lookup"><span data-stu-id="8160f-123">✔️</span></span></td>
        <td><span data-ttu-id="8160f-124">✔️</span><span class="sxs-lookup"><span data-stu-id="8160f-124">✔️</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="8160f-125">Cursore con sguardo rivolto verso la testa</span><span class="sxs-lookup"><span data-stu-id="8160f-125">Head-gaze cursor</span></span></td>
        <td><span data-ttu-id="8160f-126">✔️</span><span class="sxs-lookup"><span data-stu-id="8160f-126">✔️</span></span></td>
        <td><span data-ttu-id="8160f-127">✔️</span><span class="sxs-lookup"><span data-stu-id="8160f-127">✔️</span></span></td>
        <td><span data-ttu-id="8160f-128">✔️</span><span class="sxs-lookup"><span data-stu-id="8160f-128">✔️</span></span></td>
    </tr>
</table>

## <a name="finger-cursor"></a><span data-ttu-id="8160f-129">Cursore del dito</span><span class="sxs-lookup"><span data-stu-id="8160f-129">Finger cursor</span></span>

<span data-ttu-id="8160f-130">Il cursore del dito è disponibile solo nel HoloLens 2 per migliorare la modalità di interazione " manipolazione diretta[con](direct-manipulation.md)le mani ".</span><span class="sxs-lookup"><span data-stu-id="8160f-130">The finger cursor is only available on the HoloLens 2 to enhance the "[direct manipulation with hands](direct-manipulation.md)" interaction mode.</span></span> <span data-ttu-id="8160f-131">Sono stati collegati anelli alle punte di entrambe le dita dell'indice per comprendere meglio dove punta il dito.</span><span class="sxs-lookup"><span data-stu-id="8160f-131">We've attached rings to the tips of both index fingers to better understand where the finger is pointing.</span></span> <span data-ttu-id="8160f-132">Le dimensioni dell'anello si basano sulla prossimità del dito alla superficie dell'interfaccia utente, che si riduce a un piccolo punto quando il dito tocca l'interfaccia utente.</span><span class="sxs-lookup"><span data-stu-id="8160f-132">The ring size is based on the proximity of the finger to the UI surface, which shrinks to a small dot when the finger touches the UI.</span></span> <span data-ttu-id="8160f-133">Più vicino è il dito, più piccolo è l'anello.</span><span class="sxs-lookup"><span data-stu-id="8160f-133">The closer the finger, the smaller the ring.</span></span> <br>

<span data-ttu-id="8160f-134">![Cursore dito](images/finger-cursor.png)</span><span class="sxs-lookup"><span data-stu-id="8160f-134">![finger cursor](images/finger-cursor.png)</span></span><br>
<span data-ttu-id="8160f-135">**Stati di feedback visivo del cursore dito** 1: l'anello si riduce a un punto.</span><span class="sxs-lookup"><span data-stu-id="8160f-135">**Visual feedback states of finger cursor** 1: The ring shrinks to a dot.</span></span> <span data-ttu-id="8160f-136">2: l'anello è allineato alla superficie.</span><span class="sxs-lookup"><span data-stu-id="8160f-136">2: The ring aligns with surface.</span></span> <span data-ttu-id="8160f-137">3: l'anello è perpendicolare al vettore delle dita.</span><span class="sxs-lookup"><span data-stu-id="8160f-137">3: The ring is perpendicular to finger vector.</span></span> <span data-ttu-id="8160f-138">4: Nessun anello.</span><span class="sxs-lookup"><span data-stu-id="8160f-138">4: No ring.</span></span>

## <a name="ray-cursor"></a><span data-ttu-id="8160f-139">Cursore Ray</span><span class="sxs-lookup"><span data-stu-id="8160f-139">Ray cursor</span></span>

<span data-ttu-id="8160f-140">I cursori di raggio si collegano alla fine dei raggi che puntano lontano per consentire la manipolazione di oggetti non raggiungibili.</span><span class="sxs-lookup"><span data-stu-id="8160f-140">Ray cursors attach to the end of far pointing rays to allow manipulation of objects that are out of hands-reach.</span></span> <span data-ttu-id="8160f-141">Nei visori immersivi, i raggi si distoglieno dai controller di movimento e terminano con cursori punto.</span><span class="sxs-lookup"><span data-stu-id="8160f-141">In immersive headsets, the rays shoot out from motion controllers and end in dot cursors.</span></span> <span data-ttu-id="8160f-142">In HoloLens 2, si applica il modello mentale di questi raggi controller del movimento e i raggi della mano progettati che provengono dai palmi e terminano in cursori a forma di anello coerenti con i cursori di dito usati nella manipolazione diretta.</span><span class="sxs-lookup"><span data-stu-id="8160f-142">In HoloLens 2, we apply the mental model of these motion controller rays and designed hand rays that originate from the palms and end in ring-shaped cursors that are consistent with finger cursors used in direct manipulation.</span></span> <br>
:::row:::
    :::column:::
        <span data-ttu-id="8160f-143">![Controller cursore Ray](images/ray-cursor-controller.png)</span><span class="sxs-lookup"><span data-stu-id="8160f-143">![Ray cursor controller](images/ray-cursor-controller.png)</span></span><br>
        <span data-ttu-id="8160f-144">**Cursori a raggi dei controller di movimento**</span><span class="sxs-lookup"><span data-stu-id="8160f-144">**Ray cursors of motion controllers**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="8160f-145">![Mano del cursore Ray](images/ray-cursor-hand.png)</span><span class="sxs-lookup"><span data-stu-id="8160f-145">![Ray cursor hand](images/ray-cursor-hand.png)</span></span><br>
        <span data-ttu-id="8160f-146">**Cursori di raggio delle mani**</span><span class="sxs-lookup"><span data-stu-id="8160f-146">**Ray cursors of hands**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="head-gaze-cursor"></a><span data-ttu-id="8160f-147">Cursore con sguardo rivolto verso la testa</span><span class="sxs-lookup"><span data-stu-id="8160f-147">Head-gaze cursor</span></span>

<span data-ttu-id="8160f-148">Il cursore con sguardo rivolto verso la testa è un punto che si collega alla fine di un vettore di punta invisibile che usa la posizione e la rotazione della testa verso il punto.</span><span class="sxs-lookup"><span data-stu-id="8160f-148">The head-gaze cursor is a dot that attaches to the end of an invisible head-gaze vector that uses the position and rotation of the head to point.</span></span> <span data-ttu-id="8160f-149">Per eseguire azioni, questo cursore di puntamento è associato a vari input di commit, ad esempio il tocco dell'aria, i comandi vocali, la sospensione e la pressione del pulsante.</span><span class="sxs-lookup"><span data-stu-id="8160f-149">To execute actions, this pointing cursor is paired with various commit inputs such as air tap, voice commands, dwell, and button press.</span></span> <span data-ttu-id="8160f-150">In HoloLens 2, lo sguardo alla testa è abbinato meglio a qualsiasi input di commit che non sia un tocco dell'aria, in quanto si verifica un conflitto di interazione tra il tocco dell'aria e i raggi di estrema mano.</span><span class="sxs-lookup"><span data-stu-id="8160f-150">In HoloLens 2, head-gaze is best paired with any commit input that isn't air tap, as there will be interaction conflict between air tap and far hand rays.</span></span> <br>
:::row:::
    :::column:::
        <span data-ttu-id="8160f-151">![Mano del cursore con lo sguardo rivolto verso la testa](images/head-gaze-cursor-hand.png)</span><span class="sxs-lookup"><span data-stu-id="8160f-151">![Head gaze cursor hand](images/head-gaze-cursor-hand.png)</span></span><br>
        <span data-ttu-id="8160f-152">**Cursore con sguardo rivolto verso la testa con movimento della mano**</span><span class="sxs-lookup"><span data-stu-id="8160f-152">**Head-gaze cursor with hand gesture**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="8160f-153">![Voce del cursore dello sguardo rivolto verso la testa](images/head-gaze-cursor-voice.png)</span><span class="sxs-lookup"><span data-stu-id="8160f-153">![Head gaze cursor voice](images/head-gaze-cursor-voice.png)</span></span><br>
        <span data-ttu-id="8160f-154">**Cursore head-gaze con comando vocale**</span><span class="sxs-lookup"><span data-stu-id="8160f-154">**Head-gaze cursor with voice command**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="cursor-customization-recommendations"></a><span data-ttu-id="8160f-155">Raccomandazioni per la personalizzazione del cursore</span><span class="sxs-lookup"><span data-stu-id="8160f-155">Cursor customization recommendations</span></span>

<span data-ttu-id="8160f-156">Per personalizzare i comportamenti e gli aspetti del feedback del cursore, ecco alcuni consigli di progettazione:</span><span class="sxs-lookup"><span data-stu-id="8160f-156">If you would like to customize the cursor feedback behaviors and appearances, here are some design recommendations:</span></span>

### <a name="cursor-scale"></a><span data-ttu-id="8160f-157">Scala del cursore</span><span class="sxs-lookup"><span data-stu-id="8160f-157">Cursor scale</span></span>

* <span data-ttu-id="8160f-158">Il cursore non deve essere più grande delle destinazioni disponibili, consentendo agli utenti di interagire facilmente con e visualizzare il contenuto.</span><span class="sxs-lookup"><span data-stu-id="8160f-158">The cursor should be no larger than the available targets, allowing users to easily interact with and view the content.</span></span>
* <span data-ttu-id="8160f-159">A seconda dell'esperienza creata, anche il ridimensionamento del cursore quando l'utente guarda intorno è una considerazione importante.</span><span class="sxs-lookup"><span data-stu-id="8160f-159">Depending on the experience you create, scaling the cursor as the user looks around is also an important consideration.</span></span> <span data-ttu-id="8160f-160">Ad esempio, man mano che l'utente guarda più lontano nell'esperienza, il cursore non deve diventare troppo piccolo in modo che sia perso.</span><span class="sxs-lookup"><span data-stu-id="8160f-160">For example, as the user looks further away in your experience, the cursor shouldn't become too small such that it's lost.</span></span>
* <span data-ttu-id="8160f-161">Quando si ridimensiona il cursore, è consigliabile applicarvi un'animazione soft man mano che viene ridimensionata per dare un'emozione organica.</span><span class="sxs-lookup"><span data-stu-id="8160f-161">When scaling the cursor, consider applying a soft animation to it as it scales to give it an organic feeling.</span></span>
* <span data-ttu-id="8160f-162">Evitare di ostruire il contenuto.</span><span class="sxs-lookup"><span data-stu-id="8160f-162">Avoid obstructing content.</span></span> <span data-ttu-id="8160f-163">Gli ologrammi sono ciò che rende l'esperienza facile da ricordare e il cursore non deve essere rimosso da essi.</span><span class="sxs-lookup"><span data-stu-id="8160f-163">Holograms are what make the experience memorable and the cursor shouldn't be taking away from them.</span></span>

### <a name="directionless-cursor-shape"></a><span data-ttu-id="8160f-164">Forma cursore senza direzione</span><span class="sxs-lookup"><span data-stu-id="8160f-164">Directionless cursor shape</span></span>

* <span data-ttu-id="8160f-165">Anche se non è presente una sola forma di cursore a destra, è consigliabile usare una forma senza direzione, ad esempio un toro.</span><span class="sxs-lookup"><span data-stu-id="8160f-165">Although there's no one right cursor shape, we recommend that you use a directionless shape like a torus.</span></span> <span data-ttu-id="8160f-166">Un cursore che punta in una direzione (ad esempio, un cursore a freccia tradizionale) potrebbe confondere l'utente in modo da avere sempre un aspetto simile.</span><span class="sxs-lookup"><span data-stu-id="8160f-166">A cursor that points in some direction (For example, a traditional arrow cursor) might confuse the user to always look that way.</span></span>
* <span data-ttu-id="8160f-167">Un'eccezione a questo problema si verifica quando si usa il cursore per comunicare l'istruzione di interazione all'utente.</span><span class="sxs-lookup"><span data-stu-id="8160f-167">An exception to this is when using the cursor to communicate interaction instruction to the user.</span></span> <span data-ttu-id="8160f-168">Ad esempio, quando si ridimensionano gli ologrammi nel sistema operativo Mixed Reality, il cursore include temporaneamente frecce che indica all'utente come spostare la mano per ridimensionare l'ologramma.</span><span class="sxs-lookup"><span data-stu-id="8160f-168">For example, when scaling holograms in the Mixed Reality OS, the cursor temporarily includes arrows that instructs the user on how to move their hand to scale the hologram.</span></span>

### <a name="look-and-feel"></a><span data-ttu-id="8160f-169">Aspetto</span><span class="sxs-lookup"><span data-stu-id="8160f-169">Look and feel</span></span>

* <span data-ttu-id="8160f-170">Un cursore a forma di ciambella o toro funziona per molte applicazioni.</span><span class="sxs-lookup"><span data-stu-id="8160f-170">A donut or torus shaped cursor works for many applications.</span></span>
* <span data-ttu-id="8160f-171">Selezionare un colore e una forma che rappresentino al meglio l'esperienza che si sta creando.</span><span class="sxs-lookup"><span data-stu-id="8160f-171">Pick a color and shape that best represents the experience you're creating.</span></span>
* <span data-ttu-id="8160f-172">I cursori sono particolarmente inclini alla [separazione dei colori.](../develop/platform-capabilities-and-apis/hologram-stability.md#color-separation)</span><span class="sxs-lookup"><span data-stu-id="8160f-172">Cursors are especially prone to [color separation](../develop/platform-capabilities-and-apis/hologram-stability.md#color-separation).</span></span>
* <span data-ttu-id="8160f-173">Un cursore di piccole dimensioni con opacità bilanciata lo mantiene informativo senza dominare la gerarchia visiva.</span><span class="sxs-lookup"><span data-stu-id="8160f-173">A small cursor with balanced opacity keeps it informative without dominating the visual hierarchy.</span></span>
* <span data-ttu-id="8160f-174">È importante usare ombreggiature o evidenziazioni dietro il cursore perché potrebbero ostacolare il contenuto e distrarre dall'attività a portata di mano.</span><span class="sxs-lookup"><span data-stu-id="8160f-174">Be cognizant of using shadows or highlights behind your cursor as they might obstruct content and distract from the task at hand.</span></span>
* <span data-ttu-id="8160f-175">I cursori devono essere allineati e abbracciati alle superfici nell'app.</span><span class="sxs-lookup"><span data-stu-id="8160f-175">Cursors should align to and hug the surfaces in your app.</span></span> <span data-ttu-id="8160f-176">Gli utenti avranno la consapevolezza che il sistema può vedere dove stanno cercando, ma anche che il sistema è a conoscenza dell'ambiente circostante.</span><span class="sxs-lookup"><span data-stu-id="8160f-176">Users will have a feeling that the system can see where they're looking, but also that the system is aware of their surroundings.</span></span> <span data-ttu-id="8160f-177">Ad esempio, il cursore nel sistema operativo realtà mista si allinea alle superfici del mondo dell'utente, creando una consapevolezza del mondo anche quando l'utente non guarda direttamente a un ologramma.</span><span class="sxs-lookup"><span data-stu-id="8160f-177">For example, the cursor in the Mixed Reality OS aligns to the surfaces of the user's world, creating a feeling of awareness of the world even when the user isn't looking directly at a hologram.</span></span>
* <span data-ttu-id="8160f-178">Il blocco magnetico del cursore su un elemento interattivo quando è vicino all'utente può contribuire a migliorare l'attendibilità dell'interazione dell'utente con tale elemento quando usa un'azione di selezione.</span><span class="sxs-lookup"><span data-stu-id="8160f-178">Magnetically locking the cursor to an interactive element when it's close to the user can help improve confidence that user will interact with that element when they use a selection action.</span></span>

### <a name="visual-cues"></a><span data-ttu-id="8160f-179">Visivi</span><span class="sxs-lookup"><span data-stu-id="8160f-179">Visual cues</span></span>

* <span data-ttu-id="8160f-180">Se l'esperienza è incentrata su un singolo ologramma, il cursore deve allinearsi e abbracciare solo l'ologramma e cambiare forma quando si guarda lontano da tale ologramma.</span><span class="sxs-lookup"><span data-stu-id="8160f-180">If your experience is focused on a single hologram, your cursor should align and hug only that hologram and change shape when you look away from that hologram.</span></span> <span data-ttu-id="8160f-181">Questo può comunicare all'utente che l'ologramma è fattibile e può interagire con esso.</span><span class="sxs-lookup"><span data-stu-id="8160f-181">This can convey to the user that the hologram is actionable and they can interact with it.</span></span>
* <span data-ttu-id="8160f-182">Se l'applicazione usa il mapping spaziale, il cursore potrebbe allinearsi e abbracciare ogni superficie visualizzata.</span><span class="sxs-lookup"><span data-stu-id="8160f-182">If your application uses spatial mapping, then your cursor could align and hug every surface it sees.</span></span> <span data-ttu-id="8160f-183">Ciò fornisce feedback agli utenti che HoloLens e l'applicazione possono visualizzare il proprio spazio.</span><span class="sxs-lookup"><span data-stu-id="8160f-183">This gives feedback to the users that HoloLens and your application can see their space.</span></span> <span data-ttu-id="8160f-184">Questo rinforza il fatto che gli ologrammi sono reali e nel nostro mondo e contribuisce a colmare il divario tra reale e virtuale.</span><span class="sxs-lookup"><span data-stu-id="8160f-184">This reinforces the fact that holograms are real and in our world and helps bridge the gap between real and virtual.</span></span>
* <span data-ttu-id="8160f-185">Avere un'idea di cosa deve fare il cursore quando non sono presenti ologrammi o superfici in vista.</span><span class="sxs-lookup"><span data-stu-id="8160f-185">Have an idea of what the cursor should do when there are no holograms or surfaces in view.</span></span> <span data-ttu-id="8160f-186">Posizionarlo a una distanza predeterminata davanti all'utente è un'opzione.</span><span class="sxs-lookup"><span data-stu-id="8160f-186">Placing it at a predetermined distance in front of the user is one option.</span></span>

### <a name="possible-actions"></a><span data-ttu-id="8160f-187">Azioni possibili</span><span class="sxs-lookup"><span data-stu-id="8160f-187">Possible actions</span></span>

* <span data-ttu-id="8160f-188">Il cursore può essere rappresentato da icone diverse per trasmettere le possibili azioni che un ologramma può eseguire, ad esempio il ridimensionamento o la rotazione.</span><span class="sxs-lookup"><span data-stu-id="8160f-188">The cursor can be represented by different icons to convey possible actions a hologram can do, such as scaling or rotation.</span></span>
* <span data-ttu-id="8160f-189">Aggiungere informazioni aggiuntive sul cursore solo se significa qualcosa per l'utente.</span><span class="sxs-lookup"><span data-stu-id="8160f-189">Only add extra information on the cursor if it means something to the user.</span></span> <span data-ttu-id="8160f-190">In caso contrario, gli utenti potrebbero non notare le modifiche dello stato o essere confusi dal cursore.</span><span class="sxs-lookup"><span data-stu-id="8160f-190">Otherwise, users might either not notice the state changes or get confused by the cursor.</span></span>

### <a name="input-state"></a><span data-ttu-id="8160f-191">Stato di input</span><span class="sxs-lookup"><span data-stu-id="8160f-191">Input state</span></span>

* <span data-ttu-id="8160f-192">È possibile usare il cursore per visualizzare lo stato o la finalità di input dell'utente.</span><span class="sxs-lookup"><span data-stu-id="8160f-192">We could use the cursor to display the user's input state or intent.</span></span> <span data-ttu-id="8160f-193">Ad esempio, è possibile visualizzare un'icona che indica all'utente che il sistema vede lo stato della mano e che l'applicazione sa di essere pronta a intervenire.</span><span class="sxs-lookup"><span data-stu-id="8160f-193">For example, we could display an icon telling the user the system sees their hand state and that the application knows they're ready to take action.</span></span>
* <span data-ttu-id="8160f-194">È anche possibile usare il cursore per mostrare agli utenti che i comandi vocali sono stati ascoltati dal sistema tramite una modifica momentanea del colore</span><span class="sxs-lookup"><span data-stu-id="8160f-194">We could also use the cursor to show users that voice commands have been heard by the system via a momentary color change</span></span>

* <span data-ttu-id="8160f-195">I seguenti stati del cursore possono essere implementati in modi diversi.</span><span class="sxs-lookup"><span data-stu-id="8160f-195">The following cursor states can be implemented in different ways.</span></span> <span data-ttu-id="8160f-196">È possibile implementare questi diversi stati modellando il cursore come una macchina a stati.</span><span class="sxs-lookup"><span data-stu-id="8160f-196">You might implement these different states by modeling the cursor like a state machine.</span></span> <span data-ttu-id="8160f-197">Ad esempio:</span><span class="sxs-lookup"><span data-stu-id="8160f-197">For example:</span></span>
    * <span data-ttu-id="8160f-198">Lo stato di inattività è il punto in cui viene visualizzato il cursore predefinito.</span><span class="sxs-lookup"><span data-stu-id="8160f-198">Idle state is where you show the default cursor.</span></span>
    * <span data-ttu-id="8160f-199">Lo stato Pronto è quando è stata rilevata la mano dell'utente nella posizione pronta.</span><span class="sxs-lookup"><span data-stu-id="8160f-199">Ready state is when you've detected the user's hand in the ready position.</span></span>
    * <span data-ttu-id="8160f-200">Lo stato di interazione è quando l'utente sta eseguendo una particolare interazione.</span><span class="sxs-lookup"><span data-stu-id="8160f-200">Interaction state is when the user is doing a particular interaction.</span></span>
    * <span data-ttu-id="8160f-201">Lo stato delle azioni possibili o lo stato del passaggio del mouse si verifica quando si comunicano le possibili azioni che possono essere eseguite su un ologramma.</span><span class="sxs-lookup"><span data-stu-id="8160f-201">Possible Actions state or hover state is when you convey possible actions that can be performed on a hologram.</span></span>

<span data-ttu-id="8160f-202">È anche possibile implementare questi stati in modo skin-able per visualizzare asset di grafica diversi quando si rilevano stati diversi.</span><span class="sxs-lookup"><span data-stu-id="8160f-202">You could also implement these states in a skin-able manner to display different art assets when you detect different states.</span></span>

<br>

---

## <a name="going-cursor-free"></a><span data-ttu-id="8160f-203">Andare "senza cursore"</span><span class="sxs-lookup"><span data-stu-id="8160f-203">Going "cursor-free"</span></span>

<span data-ttu-id="8160f-204">La progettazione senza cursore è consigliata quando il senso dell'immersione è un componente chiave di un'esperienza e quando le interazioni di puntamento (tramite lo sguardo fisso e il movimento) non richiedono una grande precisione.</span><span class="sxs-lookup"><span data-stu-id="8160f-204">Designing without a cursor is recommended when the sense of immersion is a key component of an experience and when pointing interactions (through gaze and gesture) don't require great precision.</span></span> <span data-ttu-id="8160f-205">Il sistema deve comunque soddisfare i normali requisiti di un cursore: fornire agli utenti un feedback continuo sulla comprensione del sistema e aiutare gli utenti a comunicare le proprie intenzioni al sistema.</span><span class="sxs-lookup"><span data-stu-id="8160f-205">The system still needs to meet the normal requirements of a cursor: providing users with continuous feedback on the system's understanding of their pointing, and helping them to communicate their intentions to the system.</span></span> <span data-ttu-id="8160f-206">Questa operazione può essere possibile tramite altre modifiche di stato evidenti.</span><span class="sxs-lookup"><span data-stu-id="8160f-206">This may be achievable through other noticeable state changes.</span></span>

<br>

---

## <a name="cursor-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="8160f-207">Cursore in MRTK (Mixed Reality Toolkit) per Unity</span><span class="sxs-lookup"><span data-stu-id="8160f-207">Cursor in MRTK (Mixed Reality Toolkit) for Unity</span></span>

<span data-ttu-id="8160f-208">Per impostazione predefinita, [MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity) fornisce un prefab del cursore([DefaultCursor.prefab](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Prefabs/Cursors)) che ha lo stesso stato di visualizzazione del cursore di sistema della shell.</span><span class="sxs-lookup"><span data-stu-id="8160f-208">By default, [MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity) provides a cursor prefab([DefaultCursor.prefab](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Prefabs/Cursors)) which has the same visual state as the shell's system cursor.</span></span> <span data-ttu-id="8160f-209">Tale file viene assegnato in Pointers (Puntatori) nel profilo di input di MRTK.</span><span class="sxs-lookup"><span data-stu-id="8160f-209">It's assigned in MRTK's Input profile, under Pointers.</span></span> <span data-ttu-id="8160f-210">È possibile sostituire/personalizzare questo cursore in base all'esperienza.</span><span class="sxs-lookup"><span data-stu-id="8160f-210">You can replace/customize this cursor for your experience.</span></span> <span data-ttu-id="8160f-211">Per l'esperienza con l'input di tracciamento oculare, MRTK offre anche EyeGazeCursor, che ha un oggetto visivo sottile per ridurre al minimo la distrazione.</span><span class="sxs-lookup"><span data-stu-id="8160f-211">For the experience with eye-tracking input, MRTK also provides EyeGazeCursor, which has subtle visual to minimize the distraction.</span></span>

* [<span data-ttu-id="8160f-212">MRTK - Profilo del puntatore</span><span class="sxs-lookup"><span data-stu-id="8160f-212">MRTK - Pointer profile</span></span>](/windows/mixed-reality/mrtk-unity/configuration/mixed-reality-configuration-guide#pointer-configuration)
* [<span data-ttu-id="8160f-213">MRTK - Sistema di input</span><span class="sxs-lookup"><span data-stu-id="8160f-213">MRTK - Input system</span></span>](/windows/mixed-reality/mrtk-unity/features/input/overview)
* [<span data-ttu-id="8160f-214">MRTK - Puntatori</span><span class="sxs-lookup"><span data-stu-id="8160f-214">MRTK - Pointers</span></span>](/windows/mixed-reality/mrtk-unity/features/input/pointers)

---

## <a name="see-also"></a><span data-ttu-id="8160f-215">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="8160f-215">See also</span></span>

* [<span data-ttu-id="8160f-216">Movimenti</span><span class="sxs-lookup"><span data-stu-id="8160f-216">Gestures</span></span>](gaze-and-commit.md#composite-gestures)
* [<span data-ttu-id="8160f-217">Puntamento con la testa e commit</span><span class="sxs-lookup"><span data-stu-id="8160f-217">Head-gaze and commit</span></span>](gaze-and-commit.md)
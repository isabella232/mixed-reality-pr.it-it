---
title: Che cos'è un ologramma?
description: HoloLens consente di visualizzare e interagire con ologrammi tridimensionali, oggetti fatti di luce e suono che appaiono nel mondo che ti circonda.
author: qianw211
ms.author: v-qianwen
ms.date: 07/09/2021
ms.topic: article
keywords: Windows Mixed Reality, HoloLens, ologrammi, progettazione, interazione, visore VR di realtà mista, visore VR windows di realtà mista, che cos'è la realtà aumentata
ms.openlocfilehash: bef2c378dcba54d3ed3da33262153f35d72c3cba
ms.sourcegitcommit: b0b49ad27a0d09eb0a3d5df0c766bb4b7bbd8208
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/12/2021
ms.locfileid: "113634332"
---
# <a name="what-is-a-hologram"></a><span data-ttu-id="c550e-104">Che cos'è un ologramma?</span><span class="sxs-lookup"><span data-stu-id="c550e-104">What is a hologram?</span></span>

<span data-ttu-id="c550e-105">HoloLens consente di visualizzare **gli ologrammi**, che sono oggetti di luce e suono che appaiono nel mondo intorno all'utente come oggetti reali.</span><span class="sxs-lookup"><span data-stu-id="c550e-105">HoloLens lets you view **holograms**, which are objects made of light and sound that appear in the world around you like real objects.</span></span> <span data-ttu-id="c550e-106">Ologrammi possibile rispondere a sguardo [fisso,](../design/gaze-and-commit.md) [movimenti](../design/gaze-and-commit.md#composite-gestures)e [comandi vocali](../design/voice-input.md).</span><span class="sxs-lookup"><span data-stu-id="c550e-106">Holograms can respond to your [gaze](../design/gaze-and-commit.md), [gestures](../design/gaze-and-commit.md#composite-gestures), and [voice commands](../design/voice-input.md).</span></span> <span data-ttu-id="c550e-107">Possono anche interagire con [le superfici reali intorno](../design/spatial-mapping.md) all'utente.</span><span class="sxs-lookup"><span data-stu-id="c550e-107">They can even interact with [real-world surfaces](../design/spatial-mapping.md) around you.</span></span> <span data-ttu-id="c550e-108">Ologrammi sono oggetti digitali che fanno parte del mondo.</span><span class="sxs-lookup"><span data-stu-id="c550e-108">Holograms are digital objects that are part of your world.</span></span>

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/MVXH5V8MVQo" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

<br>

## <a name="device-support"></a><span data-ttu-id="c550e-109">Supporto di dispositivi</span><span class="sxs-lookup"><span data-stu-id="c550e-109">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="c550e-110"><strong>Funzionalità</strong></span><span class="sxs-lookup"><span data-stu-id="c550e-110"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="c550e-111"><a href="/hololens/hololens1-hardware"><strong>HoloLens (prima generazione)</strong></a></span><span class="sxs-lookup"><span data-stu-id="c550e-111"><a href="/hololens/hololens1-hardware"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="c550e-112"><a href="/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="c550e-112"><a href="/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="c550e-113"><a href="../discover/immersive-headset-hardware-details.md"><strong>Visori VR immersive</strong></a></span><span class="sxs-lookup"><span data-stu-id="c550e-113"><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="c550e-114">Holograms (Ologrammi)</span><span class="sxs-lookup"><span data-stu-id="c550e-114">Holograms</span></span></td>
        <td><span data-ttu-id="c550e-115">✔️</span><span class="sxs-lookup"><span data-stu-id="c550e-115">✔️</span></span></td>
        <td><span data-ttu-id="c550e-116">✔️</span><span class="sxs-lookup"><span data-stu-id="c550e-116">✔️</span></span></td>
        <td>❌</td>
    </tr>
</table>

<br>

---

## <a name="a-hologram-is-made-of-light-and-sound"></a><span data-ttu-id="c550e-117">Un ologramma è costituito da luce e suono</span><span class="sxs-lookup"><span data-stu-id="c550e-117">A hologram is made of light and sound</span></span>

### <a name="light"></a><span data-ttu-id="c550e-118">Chiaro</span><span class="sxs-lookup"><span data-stu-id="c550e-118">Light</span></span>

<span data-ttu-id="c550e-119">Gli ologrammi HoloLens [visualizzati](../develop/platform-capabilities-and-apis/rendering.md) vengono visualizzati nella cornice olografica direttamente davanti agli occhi degli utenti.</span><span class="sxs-lookup"><span data-stu-id="c550e-119">The holograms that HoloLens [renders](../develop/platform-capabilities-and-apis/rendering.md) appear in the holographic frame directly in front of users' eyes.</span></span> <span data-ttu-id="c550e-120">Ologrammi aggiungere luce al mondo, il che significa che è possibile vedere sia la luce dal display che la luce dal mondo circostante.</span><span class="sxs-lookup"><span data-stu-id="c550e-120">Holograms add light to your world, which means that you see both the light from the display and the light from your surrounding world.</span></span> <span data-ttu-id="c550e-121">Poiché HoloLens usa uno schermo additivo che aggiunge luce, il colore nero verrà reso trasparente.</span><span class="sxs-lookup"><span data-stu-id="c550e-121">Since HoloLens uses an additive display that adds light, the black color will be rendered transparent.</span></span> 

<span data-ttu-id="c550e-122">Ologrammi possono avere aspetti e comportamenti molto diversi.</span><span class="sxs-lookup"><span data-stu-id="c550e-122">Holograms can have very different appearances and behaviors.</span></span> <span data-ttu-id="c550e-123">Alcuni sono realistici e solidi e altri sono di tipo ethereale ed ethereale.</span><span class="sxs-lookup"><span data-stu-id="c550e-123">Some are realistic and solid, and others are cartoonish and ethereal.</span></span> <span data-ttu-id="c550e-124">È possibile usare gli ologrammi per evidenziare le funzionalità nell'ambiente o usarle come elementi nell'interfaccia utente dell'app.</span><span class="sxs-lookup"><span data-stu-id="c550e-124">You can use holograms to highlight features in your environment or use them as elements in your app's user interface.</span></span>

![Mani che manipolano un ologramma](images/hologram-hands-940px.jpg)

### <a name="sound"></a><span data-ttu-id="c550e-126">Suoni</span><span class="sxs-lookup"><span data-stu-id="c550e-126">Sound</span></span>

<span data-ttu-id="c550e-127">Ologrammi può anche produrre [suoni](../design/spatial-sound.md), che sembrano derivare da una posizione specifica nell'ambiente.</span><span class="sxs-lookup"><span data-stu-id="c550e-127">Holograms can also produce [sounds](../design/spatial-sound.md), which appear to come from a specific place in your environment.</span></span> <span data-ttu-id="c550e-128">A HoloLens, il suono proviene da due altoparlanti che si trovano direttamente sopra la propria casa.</span><span class="sxs-lookup"><span data-stu-id="c550e-128">On HoloLens, sound comes from two speakers that are located directly above your ears.</span></span> <span data-ttu-id="c550e-129">Come i display olografici, gli altoparlanti sono additivi, introducendo nuovi suoni senza bloccare i suoni dell'ambiente.</span><span class="sxs-lookup"><span data-stu-id="c550e-129">Same as the holographic displays, the speakers are additive, introducing new sounds without blocking the sounds from your environment.</span></span>

## <a name="a-hologram-can-be-placed-in-the-world-or-tag-along-with-you"></a><span data-ttu-id="c550e-130">Un ologramma può essere inserito nel mondo o tag insieme all'utente</span><span class="sxs-lookup"><span data-stu-id="c550e-130">A hologram can be placed in the world or tag along with you</span></span>

<span data-ttu-id="c550e-131">Quando si ha una posizione fissa per un ologramma, è [possibile](../design/coordinate-systems.md) posizionarlo esattamente in quel punto del mondo.</span><span class="sxs-lookup"><span data-stu-id="c550e-131">When you have a fixed location for a hologram, you can [place](../design/coordinate-systems.md) it precisely at that point in the world.</span></span> <span data-ttu-id="c550e-132">L'ologramma appare stazionaria in base al mondo che ti circonda, proprio come un oggetto fisico.</span><span class="sxs-lookup"><span data-stu-id="c550e-132">As you walk around, the hologram appears stationary based on the world around you, just like a physical object.</span></span> <span data-ttu-id="c550e-133">Se usi un [ancoraggio nello](../design/coordinate-systems.md#spatial-anchors) spazio per bloccare l'oggetto, il sistema può anche ricordare dove l'hai lasciato quando torni in seguito.</span><span class="sxs-lookup"><span data-stu-id="c550e-133">If you use a [spatial anchor](../design/coordinate-systems.md#spatial-anchors) to pin the object, the system can even remember where you left it when you come back later.</span></span>

![Due uomini che usano il layout di Microsoft Dynamics 365 in uno spazio di vendita al dettaglio](images/HLS19_retailLayoutHologram_001-940px.jpg)

<span data-ttu-id="c550e-135">Alcuni ologrammi seguono invece l'utente.</span><span class="sxs-lookup"><span data-stu-id="c550e-135">Some holograms follow the user instead.</span></span> <span data-ttu-id="c550e-136">Si posizionano in base all'utente.</span><span class="sxs-lookup"><span data-stu-id="c550e-136">They position themselves based on the user.</span></span> <span data-ttu-id="c550e-137">È possibile scegliere di portare con se un ologramma e quindi posizionarlo sulla pareti quando si arriva a un'altra stanza.</span><span class="sxs-lookup"><span data-stu-id="c550e-137">You can choose to bring a hologram with you, and then place it on the wall once you get to another room.</span></span>

<span data-ttu-id="c550e-138">**Procedure consigliate**</span><span class="sxs-lookup"><span data-stu-id="c550e-138">**Best practices**</span></span>

* <span data-ttu-id="c550e-139">Alcuni scenari richiedono che gli ologrammi rimangano facilmente individuabili o visibili in tutta l'esperienza.</span><span class="sxs-lookup"><span data-stu-id="c550e-139">Some scenarios demand that holograms remain easily discoverable or visible throughout the experience.</span></span> <span data-ttu-id="c550e-140">Esistono due approcci generali a questo tipo di posizionamento.</span><span class="sxs-lookup"><span data-stu-id="c550e-140">There are two high-level approaches to this kind of positioning.</span></span> <span data-ttu-id="c550e-141">Verranno ora chiamate e **bloccate per la** visualizzazione **e bloccate dal corpo.**</span><span class="sxs-lookup"><span data-stu-id="c550e-141">Let's call them **display-locked** and **body-locked**.</span></span>
   * <span data-ttu-id="c550e-142">**Il contenuto visualizzato** bloccato è bloccato sul dispositivo di visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="c550e-142">**Display-locked** content is locked to the display device.</span></span> <span data-ttu-id="c550e-143">Questo tipo di contenuto è difficile per diversi motivi, tra cui una impressione innaturale di "clingyness" che rende molti utenti frustranti e vogliono "scrollarlo di dosso".</span><span class="sxs-lookup"><span data-stu-id="c550e-143">This type of content is tricky for several reasons, including an unnatural feeling of "clingyness" that makes many users frustrated and wanting to "shake it off."</span></span> <span data-ttu-id="c550e-144">In generale, i progettisti hanno trovato migliore per evitare il blocco della visualizzazione del contenuto.</span><span class="sxs-lookup"><span data-stu-id="c550e-144">In general, designers have found it better to avoid display-locking content.</span></span>
   * <span data-ttu-id="c550e-145">**Il contenuto bloccato** dal corpo può essere molto più pervaso.</span><span class="sxs-lookup"><span data-stu-id="c550e-145">**Body-locked** content can be far more forgiving.</span></span> <span data-ttu-id="c550e-146">Il blocco del corpo si verifica quando si esegue il tethering di un ologramma al corpo o al vettore di sguardo fisso dell'utente nello spazio 3D.</span><span class="sxs-lookup"><span data-stu-id="c550e-146">Body-locking is when you tether a hologram to the user's body or gaze vector in 3D space.</span></span> <span data-ttu-id="c550e-147">Molte esperienze hanno adottato un comportamento di blocco del corpo in cui l'ologramma segue lo sguardo dell'utente, che consente all'utente di ruotare il corpo e spostarsi nello spazio senza perdere l'ologramma.</span><span class="sxs-lookup"><span data-stu-id="c550e-147">Many experiences have adopted a body-locking behavior where the hologram follows the user's gaze, which allows the user to rotate their body and move through space without losing the hologram.</span></span> <span data-ttu-id="c550e-148">L'incorporamento di un ritardo consente ai movimenti dell'ologramma di essere più naturali.</span><span class="sxs-lookup"><span data-stu-id="c550e-148">Incorporating a delay helps the hologram movements to feel more natural.</span></span> <span data-ttu-id="c550e-149">Ad esempio, un'interfaccia utente di base del sistema operativo Windows Holographic usa una variazione nel blocco del corpo che segue lo sguardo dell'utente con un ritardo di tipo elastico mentre l'utente ruota la testa.</span><span class="sxs-lookup"><span data-stu-id="c550e-149">For example, some core UI of the Windows Holographic OS uses a variation on body-locking that follows the user's gaze with a gentle, elastic-like delay while the user turns their head.</span></span>
* <span data-ttu-id="c550e-150">Posizionare l'ologramma a una distanza di visualizzazione comoda in genere a circa 1-2 metri dalla testa.</span><span class="sxs-lookup"><span data-stu-id="c550e-150">Place the hologram at a comfortable viewing distance typically about 1-2 meters away from the head.</span></span>
* <span data-ttu-id="c550e-151">Consentire agli elementi di deviare se devono essere continuamente nella cornice olografica oppure provare a spostare il contenuto su un lato dello schermo quando l'utente cambia punto di vista.</span><span class="sxs-lookup"><span data-stu-id="c550e-151">Allow elements to drift if they must be continually in the holographic frame, or consider moving your content to one side of the display when the user changes their point of view.</span></span> <span data-ttu-id="c550e-152">Per altre informazioni, vedere [l'artilce di](../design/billboarding-and-tag-along.md) creazione di tag e di tag.</span><span class="sxs-lookup"><span data-stu-id="c550e-152">For more information, see the [billboarding and tag-along](../design/billboarding-and-tag-along.md) artilce.</span></span>

<span data-ttu-id="c550e-153">**Posizionare gli ologrammi nella zona ottimale, tra 1,25 m e 5 m**</span><span class="sxs-lookup"><span data-stu-id="c550e-153">**Place holograms in the optimal zone - between 1.25 m and 5 m**</span></span>

<span data-ttu-id="c550e-154">Due metri è la distanza di visualizzazione ottimale.</span><span class="sxs-lookup"><span data-stu-id="c550e-154">Two meters is the most optimal viewing distance.</span></span> <span data-ttu-id="c550e-155">L'esperienza inizierà a peggiorare man appena si avvicina di più di 1 contatore.</span><span class="sxs-lookup"><span data-stu-id="c550e-155">The experience will start to degrade as you get closer than 1 meter.</span></span> <span data-ttu-id="c550e-156">A distanze inferiori a 1 metro, gli ologrammi che si spostano regolarmente in profondità hanno maggiori probabilità di essere problematici rispetto agli ologrammi stazionari.</span><span class="sxs-lookup"><span data-stu-id="c550e-156">At distances less than 1 meter, holograms that regularly move in depth are more likely to be problematic than stationary holograms.</span></span> <span data-ttu-id="c550e-157">È consigliabile ritagliare o dissolvere normalmente il contenuto quando si avvicina troppo, in modo da non creare un'esperienza di visualizzazione disgraziata per l'utente.</span><span class="sxs-lookup"><span data-stu-id="c550e-157">Consider gracefully clipping or fading out your content when it gets too close, so you don't jar the user into an unpleasant viewing experience.</span></span>

![Distanza ottimale per il posizionamento degli ologrammi dall'utente.](images/distanceguiderendering-950px.png)

<br>

---

## <a name="a-hologram-interacts-with-you-and-your-world"></a><span data-ttu-id="c550e-159">Un ologramma interagisce con l'utente e il mondo</span><span class="sxs-lookup"><span data-stu-id="c550e-159">A hologram interacts with you and your world</span></span>

<span data-ttu-id="c550e-160">Ologrammi non riguardano solo la luce e il suono. sono anche una parte attiva del mondo.</span><span class="sxs-lookup"><span data-stu-id="c550e-160">Holograms aren't only about light and sound; they're also an active part of your world.</span></span> <span data-ttu-id="c550e-161">Sguardo fisso su un ologramma e movimento con la mano e un ologramma può iniziare a seguire l'utente.</span><span class="sxs-lookup"><span data-stu-id="c550e-161">Gaze at a hologram and gesture with your hand, and a hologram can start to follow you.</span></span> <span data-ttu-id="c550e-162">Assegnare un comando vocale e l'ologramma può rispondere.</span><span class="sxs-lookup"><span data-stu-id="c550e-162">Give a voice command, and the hologram can reply.</span></span>

![Gruppo di operatori pubblici che usano Microsoft HoloLens 2 per collaborare a un progetto di sviluppo di una centrale eolica](images/HLS19_governmentUtilitiesHologram_001-940px.jpg)

<span data-ttu-id="c550e-164">Ologrammi le interazioni personali che non sono possibili altrove.</span><span class="sxs-lookup"><span data-stu-id="c550e-164">Holograms enable personal interactions that aren't possible elsewhere.</span></span> <span data-ttu-id="c550e-165">Poiché il HoloLens sa dove si trova nel mondo, un carattere olografico può guardarti direttamente negli occhi e avviare una conversazione con te.</span><span class="sxs-lookup"><span data-stu-id="c550e-165">Because the HoloLens knows where it is in the world, a holographic character can look at you directly in the eyes and start a conversation with you.</span></span>

<span data-ttu-id="c550e-166">Un ologramma può anche interagire con l'ambiente circostante.</span><span class="sxs-lookup"><span data-stu-id="c550e-166">A hologram can also interact with your surroundings.</span></span> <span data-ttu-id="c550e-167">Ad esempio, è possibile posizionare una palla di gioco olografica sopra un tavolo.</span><span class="sxs-lookup"><span data-stu-id="c550e-167">For example, you can place a holographic bouncing ball above a table.</span></span> <span data-ttu-id="c550e-168">Quindi, con un [tocco d'aria,](../design/gaze-and-commit.md#composite-gestures)osservare il tocco della palla e fare rumore quando raggiunge il tavolo.</span><span class="sxs-lookup"><span data-stu-id="c550e-168">Then, with an [air tap](../design/gaze-and-commit.md#composite-gestures), watch the ball bounce, and make sound as it hits the table.</span></span>

<span data-ttu-id="c550e-169">Ologrammi possono essere occluse anche da oggetti reali.</span><span class="sxs-lookup"><span data-stu-id="c550e-169">Holograms can also be occluded by real-world objects.</span></span> <span data-ttu-id="c550e-170">Ad esempio, un carattere olografico potrebbe passare attraverso una porta e dietro una barriera, fuori dalla vista.</span><span class="sxs-lookup"><span data-stu-id="c550e-170">For example, a holographic character might walk through a door and behind a wall, out of your sight.</span></span>

<span data-ttu-id="c550e-171">**Suggerimenti per l'integrazione di ologrammi e il mondo reale**</span><span class="sxs-lookup"><span data-stu-id="c550e-171">**Tips for integrating holograms and the real world**</span></span>

* <span data-ttu-id="c550e-172">L'allineamento alle regole gravitazionali rende gli ologrammi più facili da correlare e più facilmente leggibili.</span><span class="sxs-lookup"><span data-stu-id="c550e-172">Aligning to gravitational rules makes holograms easier to relate to and more believable.</span></span> <span data-ttu-id="c550e-173">Ad esempio: posizionare un cane olografico a terra & un gatto sul tavolo invece di metterlo nello spazio.</span><span class="sxs-lookup"><span data-stu-id="c550e-173">For example: Place a holographic dog on the ground & a vase on the table rather than have them floating in space.</span></span>
* <span data-ttu-id="c550e-174">Molti progettisti hanno scoperto di poter integrare ologrammi più facilmente leggibili creando un'"ombreggiatura negativa" sulla superficie su cui si trova l'ologramma.</span><span class="sxs-lookup"><span data-stu-id="c550e-174">Many designers have found that they can integrate more believable holograms by creating a "negative shadow" on the surface that the hologram is sitting on.</span></span> <span data-ttu-id="c550e-175">A tale scopo, creano un alone debole sul terreno intorno all'ologramma e quindi sottraggono l'ombreggiatura dall'alone.</span><span class="sxs-lookup"><span data-stu-id="c550e-175">They do this by creating a soft glow on the ground around the hologram and then subtracting the "shadow" from the glow.</span></span> <span data-ttu-id="c550e-176">L'alone si integra con la luce del mondo reale.</span><span class="sxs-lookup"><span data-stu-id="c550e-176">The soft glow integrates with the light from the real world.</span></span> <span data-ttu-id="c550e-177">L'ombreggiatura viene usata per macinare l'ologramma nell'ambiente.</span><span class="sxs-lookup"><span data-stu-id="c550e-177">The shadow is used to ground the hologram in the environment.</span></span>

<br>

---

:::row:::
    :::column:::
        ## <a name="a-hologram-is-what-bryou-can-dream-upbr"></a><span data-ttu-id="c550e-178">Un ologramma è ciò che</span><span class="sxs-lookup"><span data-stu-id="c550e-178">A hologram is what</span></span> <br><span data-ttu-id="c550e-179">you can dream up</span><span class="sxs-lookup"><span data-stu-id="c550e-179">you can dream up</span></span><br>
        <span data-ttu-id="c550e-180">Gli sviluppatori olografici hanno la potenza di interrompere la creatività degli schermi 2D e del mondo che ti circonda.</span><span class="sxs-lookup"><span data-stu-id="c550e-180">As a holographic developer, you have the power to break your creativity out of 2D screens and into the world around you.</span></span><br><br>
        <span data-ttu-id="c550e-181">Che cosa *verrà* compilato?</span><span class="sxs-lookup"><span data-stu-id="c550e-181">What will *you* build?</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="c550e-182">![space](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="c550e-182">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="c550e-183">![Mondo immaginario olografico nel living](images/designoverview.jpg)</span><span class="sxs-lookup"><span data-stu-id="c550e-183">![Holographic imaginary world in living room](images/designoverview.jpg)</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="next-discovery-checkpoint"></a><span data-ttu-id="c550e-184">Prossima stazione di scoperta</span><span class="sxs-lookup"><span data-stu-id="c550e-184">Next Discovery Checkpoint</span></span>

<span data-ttu-id="c550e-185">Si sta esplorando il [percorso di](get-started-with-mr.md) individuazione che abbiamo strutturato ed esplorando le nozioni di base della realtà mista.</span><span class="sxs-lookup"><span data-stu-id="c550e-185">You're on the [discovery journey](get-started-with-mr.md) we've laid out, and exploring the basics of Mixed Reality.</span></span> <span data-ttu-id="c550e-186">Da qui è possibile continuare con l'argomento di base successivo:</span><span class="sxs-lookup"><span data-stu-id="c550e-186">From here, you can continue to the next foundational topic:</span></span> 

> [!div class="nextstepaction"]
> [<span data-ttu-id="c550e-187">Espandere il processo di progettazione</span><span class="sxs-lookup"><span data-stu-id="c550e-187">Expand your design process</span></span>](case-study-expanding-the-design-process-for-mixed-reality.md)
---
title: Input vocale
description: L'input vocale è un input di base per HoloLens e per le cuffie immersive in realtà mista di Windows. La voce può essere usata per i comandi, la dettatura, il Cortana e altro ancora.
author: hak0n
ms.author: hakons
ms.date: 10/03/2019
ms.topic: article
keywords: GGV, voce, Cortana, sintesi vocale, input, auricolare realtà mista, cuffia di realtà mista di Windows, auricolare realtà virtuale, HoloLens, MRTK, Toolkit realtà mista, sguardo
ms.openlocfilehash: 079a3d457da9403611d2f825dd6e599a4e9f0353
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/20/2021
ms.locfileid: "98583225"
---
# <a name="voice-input"></a><span data-ttu-id="3508b-105">Input vocale</span><span class="sxs-lookup"><span data-stu-id="3508b-105">Voice input</span></span>

![Input vocale](images/UX_Hero_VoiceCommand.jpg)

<span data-ttu-id="3508b-107">La voce è una delle forme di input chiave per HoloLens.</span><span class="sxs-lookup"><span data-stu-id="3508b-107">Voice is one of the key forms of input on HoloLens.</span></span> <span data-ttu-id="3508b-108">Consente di eseguire direttamente il comando di un ologramma senza dover usare i [movimenti di mano](gaze-and-commit.md#composite-gestures).</span><span class="sxs-lookup"><span data-stu-id="3508b-108">It allows you to directly command a hologram without having to use [hand gestures](gaze-and-commit.md#composite-gestures).</span></span> <span data-ttu-id="3508b-109">L'input vocale può essere un modo naturale di comunicare le intenzioni.</span><span class="sxs-lookup"><span data-stu-id="3508b-109">Voice input can be a natural way to communicate your intent.</span></span> <span data-ttu-id="3508b-110">La voce è particolarmente utile per attraversare interfacce complesse, perché consente agli utenti di tagliare i menu nidificati con un unico comando.</span><span class="sxs-lookup"><span data-stu-id="3508b-110">Voice is especially good at traversing complex interfaces, because it lets users cut through nested menus with one command.</span></span>

<span data-ttu-id="3508b-111">L'input vocale è alimentato dallo [stesso motore](/windows/uwp/design/input/speech-recognition) che supporta la sintesi vocale in tutte le _app di Windows universale_.</span><span class="sxs-lookup"><span data-stu-id="3508b-111">Voice input is powered by the [same engine](/windows/uwp/design/input/speech-recognition) that supports speech in all _Universal Windows Apps_.</span></span> <span data-ttu-id="3508b-112">In HoloLens il riconoscimento vocale funzionerà sempre nella lingua di visualizzazione di Windows configurata nelle impostazioni del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="3508b-112">On HoloLens, speech recognition will always function in the Windows display language configured in your device Settings.</span></span> 

<br>

## <a name="voice-and-gaze"></a><span data-ttu-id="3508b-113">Voice and sguardi</span><span class="sxs-lookup"><span data-stu-id="3508b-113">Voice and gaze</span></span>

<span data-ttu-id="3508b-114">Quando si usano i comandi vocali, è il tipico meccanismo di destinazione, con un cursore a "Select" o per il canale del comando a un'applicazione che si sta esaminando.</span><span class="sxs-lookup"><span data-stu-id="3508b-114">When you're using voice commands, head or eye gaze is the typical targeting mechanism, whether with a cursor to "select" or to channel your command to an application you're looking at.</span></span> <span data-ttu-id="3508b-115">Potrebbe non essere necessario visualizzare alcun cursore _("vedere il cursore")_.</span><span class="sxs-lookup"><span data-stu-id="3508b-115">It may not even be required to show any gaze cursor _("see it, say it")_.</span></span> <span data-ttu-id="3508b-116">Alcuni comandi vocali non richiedono una destinazione, ad esempio "go to Start" o "Hey Cortana".</span><span class="sxs-lookup"><span data-stu-id="3508b-116">Some voice commands don't require a target at all, such as "go to start" or "Hey Cortana."</span></span>

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/eHMkOpNUtR8" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>


## <a name="device-support"></a><span data-ttu-id="3508b-117">Supporto di dispositivi</span><span class="sxs-lookup"><span data-stu-id="3508b-117">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="3508b-118"><strong>Funzionalità</strong></span><span class="sxs-lookup"><span data-stu-id="3508b-118"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="3508b-119"><a href="/hololens/hololens1-hardware"><strong>HoloLens (prima generazione)</strong></a></span><span class="sxs-lookup"><span data-stu-id="3508b-119"><a href="/hololens/hololens1-hardware"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="3508b-120"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="3508b-120"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="3508b-121"><a href="../discover/immersive-headset-hardware-details.md"><strong>Visori VR immersive</strong></a></span><span class="sxs-lookup"><span data-stu-id="3508b-121"><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="3508b-122">Input vocale</span><span class="sxs-lookup"><span data-stu-id="3508b-122">Voice input</span></span></td>
        <td><span data-ttu-id="3508b-123">✔️</span><span class="sxs-lookup"><span data-stu-id="3508b-123">✔️</span></span></td>
        <td><span data-ttu-id="3508b-124">✔️</span><span class="sxs-lookup"><span data-stu-id="3508b-124">✔️</span></span></td>
        <td><span data-ttu-id="3508b-125">✔️ (con microfono)</span><span class="sxs-lookup"><span data-stu-id="3508b-125">✔️ (with microphone)</span></span></td>
    </tr>
</table>

## <a name="the-select-command"></a><span data-ttu-id="3508b-126">Comando "Select"</span><span class="sxs-lookup"><span data-stu-id="3508b-126">The "select" command</span></span>

<span data-ttu-id="3508b-127">**HoloLens (prima generazione)**</span><span class="sxs-lookup"><span data-stu-id="3508b-127">**HoloLens (1st gen)**</span></span>

<span data-ttu-id="3508b-128">Anche senza aggiungere in modo specifico il supporto vocale all'app, gli utenti possono attivare gli ologrammi semplicemente pronunciando il comando "Select" del comando "System Voice".</span><span class="sxs-lookup"><span data-stu-id="3508b-128">Even without specifically adding voice support to your app, your users can activate holograms simply by saying the system voice command "select".</span></span> <span data-ttu-id="3508b-129">Questo comportamento è identico a quello di un [rubinetto d'aria](gaze-and-commit.md#composite-gestures) su HoloLens, facendo clic sul pulsante Seleziona nel [HoloLens clic](/hololens/hololens1-clicker)oppure premendo il trigger in un [controller di movimento della realtà mista di Windows](motion-controllers.md).</span><span class="sxs-lookup"><span data-stu-id="3508b-129">This behaves the same as an [air tap](gaze-and-commit.md#composite-gestures) on HoloLens, pressing the select button on the [HoloLens clicker](/hololens/hololens1-clicker), or pressing the trigger on a [Windows Mixed Reality motion controller](motion-controllers.md).</span></span> <span data-ttu-id="3508b-130">Verrà visualizzato un suono e verrà visualizzata una descrizione comando con "Select" come conferma.</span><span class="sxs-lookup"><span data-stu-id="3508b-130">You'll hear a sound and see a tooltip with "select" appear as confirmation.</span></span> <span data-ttu-id="3508b-131">"Select" è abilitato da un algoritmo di rilevamento parole chiave a basso consumo, che significa che è possibile pronunciarlo in qualsiasi momento con un minimo di durata della batteria.</span><span class="sxs-lookup"><span data-stu-id="3508b-131">"Select" is enabled by a low-power keyword detection algorithm, which means you can say it anytime with minimal battery life impact.</span></span> <span data-ttu-id="3508b-132">È anche possibile pronunciare "Select" con le proprie mani.</span><span class="sxs-lookup"><span data-stu-id="3508b-132">You can even say "select" with your hands at your side.</span></span>

<br>

---

:::row:::
    :::column:::
        <span data-ttu-id="3508b-133">**HoloLens 2**</span><span class="sxs-lookup"><span data-stu-id="3508b-133">**HoloLens 2**</span></span><br><br>
        <span data-ttu-id="3508b-134">Per usare il comando voce "Select" in HoloLens 2, è necessario innanzitutto visualizzare il cursore di sguardi da usare come puntatore.</span><span class="sxs-lookup"><span data-stu-id="3508b-134">To use the "select" voice command in HoloLens 2, you first need to bring up the gaze cursor to use as a pointer.</span></span> <span data-ttu-id="3508b-135">Il comando per riportarlo è facile da ricordare, ovvero "Select".</span><span class="sxs-lookup"><span data-stu-id="3508b-135">The command to bring it up is easy to remember--just say, "select".</span></span><br><br>
        <span data-ttu-id="3508b-136">Per uscire dalla modalità, usare di nuovo le mani toccando aria, avvicinando un pulsante con le dita o usando il gesto del sistema.</span><span class="sxs-lookup"><span data-stu-id="3508b-136">To exit the mode, use your hands again by air tapping, approaching a button with your fingers, or using the system gesture.</span></span><br>
        <br> 
        <span data-ttu-id="3508b-137">*Image: pronunciare "Select" per utilizzare il comando Voice per la selezione*</span><span class="sxs-lookup"><span data-stu-id="3508b-137">*Image: Say "select" to use the voice command for selection*</span></span>
    :::column-end:::
        :::column:::
       ![Un utente può pronunciare "Select" per usare il comando Voice per una selezione.](images/kma-voice-select-00170.jpg)<br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="hey-cortana"></a><span data-ttu-id="3508b-139">Salve Cortana</span><span class="sxs-lookup"><span data-stu-id="3508b-139">Hey Cortana</span></span>

<span data-ttu-id="3508b-140">È possibile pronunciare "Hey Cortana" per visualizzare Cortana in qualsiasi momento.</span><span class="sxs-lookup"><span data-stu-id="3508b-140">You can say "Hey Cortana" to bring up Cortana at any time.</span></span> <span data-ttu-id="3508b-141">Non è necessario attendere che venga visualizzata per continuare a porre una domanda o fornire un'istruzione.</span><span class="sxs-lookup"><span data-stu-id="3508b-141">You don't have to wait for her to appear to continue asking her your question or giving her an instruction.</span></span> <span data-ttu-id="3508b-142">Ad esempio, provare a pronunciare "Hey Cortana, qual è il meteo?"</span><span class="sxs-lookup"><span data-stu-id="3508b-142">For example, try saying "Hey Cortana, what's the weather?"</span></span> <span data-ttu-id="3508b-143">come singola frase.</span><span class="sxs-lookup"><span data-stu-id="3508b-143">as a single sentence.</span></span> <span data-ttu-id="3508b-144">Per ulteriori informazioni su Cortana e sulle operazioni che è possibile eseguire, rivolgersi all'utente.</span><span class="sxs-lookup"><span data-stu-id="3508b-144">For more information about Cortana and what you can do, ask her!</span></span> <span data-ttu-id="3508b-145">Pronunciare "Hey Cortana, cosa posso dire?"</span><span class="sxs-lookup"><span data-stu-id="3508b-145">Say "Hey Cortana, what can I say?"</span></span> <span data-ttu-id="3508b-146">verrà quindi eseguito il pull di un elenco di comandi funzionanti e consigliati.</span><span class="sxs-lookup"><span data-stu-id="3508b-146">and she'll pull up a list of working and suggested commands.</span></span> <span data-ttu-id="3508b-147">Se si è già nell'app Cortana, selezionare **?**</span><span class="sxs-lookup"><span data-stu-id="3508b-147">If you're already in the Cortana app, select the **?**</span></span> <span data-ttu-id="3508b-148">icona sulla barra laterale per estrarre lo stesso menu.</span><span class="sxs-lookup"><span data-stu-id="3508b-148">icon on the sidebar to pull up this same menu.</span></span>

<span data-ttu-id="3508b-149">**Comandi specifici di HoloLens**</span><span class="sxs-lookup"><span data-stu-id="3508b-149">**HoloLens-specific commands**</span></span>
* <span data-ttu-id="3508b-150">"Cosa posso dire?"</span><span class="sxs-lookup"><span data-stu-id="3508b-150">"What can I say?"</span></span>
* <span data-ttu-id="3508b-151">"Vai a avvio"-anziché [Bloom](system-gesture.md#bloom) per visualizzare il [menu Start](../discover/navigating-the-windows-mixed-reality-home.md#start-menu)</span><span class="sxs-lookup"><span data-stu-id="3508b-151">"Go to Start" - instead of [bloom](system-gesture.md#bloom) to get to [Start Menu](../discover/navigating-the-windows-mixed-reality-home.md#start-menu)</span></span>
* <span data-ttu-id="3508b-152">"Avvia <app> "</span><span class="sxs-lookup"><span data-stu-id="3508b-152">"Launch <app>"</span></span>
* <span data-ttu-id="3508b-153">"Sposta <app> qui"</span><span class="sxs-lookup"><span data-stu-id="3508b-153">"Move <app> here"</span></span>
* <span data-ttu-id="3508b-154">"Scattare un'immagine"</span><span class="sxs-lookup"><span data-stu-id="3508b-154">"Take a picture"</span></span>
* <span data-ttu-id="3508b-155">"Avvia registrazione"</span><span class="sxs-lookup"><span data-stu-id="3508b-155">"Start recording"</span></span>
* <span data-ttu-id="3508b-156">"Arresta registrazione"</span><span class="sxs-lookup"><span data-stu-id="3508b-156">"Stop recording"</span></span>
* <span data-ttu-id="3508b-157">"Mostra raggio della mano"</span><span class="sxs-lookup"><span data-stu-id="3508b-157">"Show hand ray"</span></span>
* <span data-ttu-id="3508b-158">"Nascondi raggio di mano"</span><span class="sxs-lookup"><span data-stu-id="3508b-158">"Hide hand ray"</span></span>
* <span data-ttu-id="3508b-159">"Aumentare la luminosità"</span><span class="sxs-lookup"><span data-stu-id="3508b-159">"Increase the brightness"</span></span>
* <span data-ttu-id="3508b-160">"Riduzione della luminosità"</span><span class="sxs-lookup"><span data-stu-id="3508b-160">"Decrease the brightness"</span></span>
* <span data-ttu-id="3508b-161">"Aumento del volume"</span><span class="sxs-lookup"><span data-stu-id="3508b-161">"Increase the volume"</span></span>
* <span data-ttu-id="3508b-162">"Diminuisci volume"</span><span class="sxs-lookup"><span data-stu-id="3508b-162">"Decrease the volume"</span></span>
* <span data-ttu-id="3508b-163">"Mute" o "unmute"</span><span class="sxs-lookup"><span data-stu-id="3508b-163">"Mute" or "Unmute"</span></span>
* <span data-ttu-id="3508b-164">"Arresta il dispositivo"</span><span class="sxs-lookup"><span data-stu-id="3508b-164">"Shut down the device"</span></span>
* <span data-ttu-id="3508b-165">"Riavvia il dispositivo"</span><span class="sxs-lookup"><span data-stu-id="3508b-165">"Restart the device"</span></span>
* <span data-ttu-id="3508b-166">"Vai a sospensione"</span><span class="sxs-lookup"><span data-stu-id="3508b-166">"Go to sleep"</span></span>
* <span data-ttu-id="3508b-167">"Qual è il tempo?"</span><span class="sxs-lookup"><span data-stu-id="3508b-167">"What time is it?"</span></span>
* <span data-ttu-id="3508b-168">"Quanta batteria è rimasta?"</span><span class="sxs-lookup"><span data-stu-id="3508b-168">"How much battery do I have left?"</span></span>

<br>

---

:::row:::
    :::column:::
        ## <a name="see-it-say-itbr"></a><span data-ttu-id="3508b-169">"Vedere la voce"</span><span class="sxs-lookup"><span data-stu-id="3508b-169">"See It, Say It"</span></span><br>
        <span data-ttu-id="3508b-170">HoloLens dispone di un modello "See it, Say it" per l'input vocale, in cui le etichette sui pulsanti indicano agli utenti i comandi vocali che possono dire.</span><span class="sxs-lookup"><span data-stu-id="3508b-170">HoloLens has a "see it, say it" model for voice input, where labels on buttons tell users what voice commands they can say as well.</span></span> <span data-ttu-id="3508b-171">Ad esempio, quando si esamina una finestra dell'app in HoloLens (1st Gen), un utente può pronunciare il comando "Adjust" per modificare la posizione dell'app nel mondo.</span><span class="sxs-lookup"><span data-stu-id="3508b-171">For example, when looking at an app window in HoloLens (1st gen), a user can say "Adjust" command to adjust the position of the app in the world.</span></span><br>
        <br>
        <span data-ttu-id="3508b-172">*Image: un utente può pronunciare il comando "Adjust", che viene visualizzato nella barra dell'app per modificare la posizione dell'app*</span><span class="sxs-lookup"><span data-stu-id="3508b-172">*Image: A user can say the "Adjust" command, which they see in the App bar to adjust the position of the app*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="3508b-173">![space](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="3508b-173">![space](images/spacer-20x582.png)</span></span><br>
        <span data-ttu-id="3508b-174">![Quando si esamina una finestra o un ologramma dell'app, un utente può pronunciare il comando "Adjust" visualizzato nella barra dell'app per modificare la posizione dell'app nel mondo](images/microphone-600px.png)</span><span class="sxs-lookup"><span data-stu-id="3508b-174">![When looking at an app window or hologram, a user can say the "Adjust" command which they see in the App bar to adjust the position of the app in the world](images/microphone-600px.png)</span></span><br>
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        <span data-ttu-id="3508b-175">Quando le app seguono questa regola, gli utenti possono comprendere facilmente cosa dire per controllare il sistema.</span><span class="sxs-lookup"><span data-stu-id="3508b-175">When apps follow this rule, users can easily understand what to say to control the system.</span></span> <span data-ttu-id="3508b-176">Quando si guarda un pulsante in HoloLens (1st Gen), viene visualizzata una descrizione comando "Voice Rest" che viene visualizzata dopo un secondo se il pulsante è abilitato per la voce e visualizza il comando per comunicare con "premere".</span><span class="sxs-lookup"><span data-stu-id="3508b-176">While gazing at a button in HoloLens (1st gen), you'll see a "voice dwell" tooltip that comes up after a second if the button is voice-enabled and displays the command to speak to "press" it.</span></span> <span data-ttu-id="3508b-177">Per rivelare le descrizioni comandi vocali in HoloLens 2, visualizzare il cursore vocale digitando "Select" o "What Can Say" (vedere l'immagine).</span><span class="sxs-lookup"><span data-stu-id="3508b-177">To reveal voice tooltips in HoloLens 2, show the voice cursor by saying "select" or "What can I say" (See image).</span></span> <br>
        <br>
        <span data-ttu-id="3508b-178">*Image: i comandi "See it, Say it" vengono visualizzati sotto i pulsanti*</span><span class="sxs-lookup"><span data-stu-id="3508b-178">*Image: "See it, say it" commands appear below the buttons*</span></span>
    :::column-end:::
        :::column:::
       ![Vedere i comandi visualizzati sotto i pulsanti](images/voice-seeitsayit-600px.png)<br><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="voice-commands-for-fast-hologram-manipulation"></a><span data-ttu-id="3508b-180">Comandi vocali per la manipolazione rapida degli ologrammi</span><span class="sxs-lookup"><span data-stu-id="3508b-180">Voice commands for fast hologram manipulation</span></span>

<span data-ttu-id="3508b-181">Ci sono molti comandi vocali che è possibile usare quando si guarda un ologramma per eseguire rapidamente attività di manipolazione.</span><span class="sxs-lookup"><span data-stu-id="3508b-181">There are many voice commands you can say while gazing at a hologram to quickly do manipulation tasks.</span></span> <span data-ttu-id="3508b-182">Questi comandi vocali funzionano con gli oggetti Windows e 3D dell'app che sono stati inseriti nel mondo.</span><span class="sxs-lookup"><span data-stu-id="3508b-182">These voice commands work on app windows and 3D objects you've placed in the world.</span></span>

<span data-ttu-id="3508b-183">**Comandi di manipolazione ologramma**</span><span class="sxs-lookup"><span data-stu-id="3508b-183">**Hologram manipulation commands**</span></span>
* <span data-ttu-id="3508b-184">Mi faccia</span><span class="sxs-lookup"><span data-stu-id="3508b-184">Face me</span></span>
* <span data-ttu-id="3508b-185">Più grande | Migliorare</span><span class="sxs-lookup"><span data-stu-id="3508b-185">Bigger | Enhance</span></span>
* <span data-ttu-id="3508b-186">Più piccoli</span><span class="sxs-lookup"><span data-stu-id="3508b-186">Smaller</span></span>

<span data-ttu-id="3508b-187">In HoloLens 2 è inoltre possibile creare interazioni più naturali in combinazione con l'occhio, che fornisce implicitamente informazioni contestuali sugli elementi a cui si fa riferimento.</span><span class="sxs-lookup"><span data-stu-id="3508b-187">On HoloLens 2, you can also create more natural interactions in combination with eye-gaze, which implicitly provides contextual information about what you are referring to.</span></span> <span data-ttu-id="3508b-188">Ad esempio, è possibile esaminare un ologramma e pronunciare _il_ punto in cui si vuole posizionarlo e pronunciare " _qui_".</span><span class="sxs-lookup"><span data-stu-id="3508b-188">For example, you could look at a hologram and say "put _this_" and then look over where you want to place it and say "over _here_".</span></span>
<span data-ttu-id="3508b-189">In alternativa, è possibile esaminare una parte olografica in un computer complesso e pronunciare: "fornire ulteriori informazioni su _questo_".</span><span class="sxs-lookup"><span data-stu-id="3508b-189">Or you could look at a holographic part on a complex machine and say: "give me more information about _this_".</span></span>

## <a name="discovering-voice-commands"></a><span data-ttu-id="3508b-190">Individuazione di comandi vocali</span><span class="sxs-lookup"><span data-stu-id="3508b-190">Discovering voice commands</span></span>

<span data-ttu-id="3508b-191">Alcuni comandi, ad esempio i comandi per una manipolazione rapida precedente, possono essere nascosti.</span><span class="sxs-lookup"><span data-stu-id="3508b-191">Some commands, like the commands for fast manipulation above, can be hidden.</span></span> <span data-ttu-id="3508b-192">Per informazioni sui comandi che è possibile usare, osservare un oggetto e pronunciare "cosa si può dire?".</span><span class="sxs-lookup"><span data-stu-id="3508b-192">To learn about what commands you can use, gaze at an object and say, "what can I say?".</span></span> <span data-ttu-id="3508b-193">Viene visualizzato un elenco di comandi possibili.</span><span class="sxs-lookup"><span data-stu-id="3508b-193">A list of possible commands pops up.</span></span> <span data-ttu-id="3508b-194">È anche possibile usare il cursore Head sguardi per individuare e visualizzare le descrizioni comandi vocali per ogni pulsante davanti all'utente.</span><span class="sxs-lookup"><span data-stu-id="3508b-194">You can also use the head gaze cursor to look around and reveal the voice tooltips for each button in front of you.</span></span> 

<span data-ttu-id="3508b-195">Se si desidera un elenco completo, è sufficiente indicare "Mostra tutti i comandi" in qualsiasi momento.</span><span class="sxs-lookup"><span data-stu-id="3508b-195">If you want a complete list, just say, "Show all commands" anytime.</span></span> 

## <a name="dictation"></a><span data-ttu-id="3508b-196">Dettatura</span><span class="sxs-lookup"><span data-stu-id="3508b-196">Dictation</span></span>

<span data-ttu-id="3508b-197">Invece di digitare con le scelte [aeree](gaze-and-commit.md#composite-gestures), la dettatura vocale può essere più efficiente per inserire il testo in un'app.</span><span class="sxs-lookup"><span data-stu-id="3508b-197">Rather than typing with [air taps](gaze-and-commit.md#composite-gestures), voice dictation can be more efficient to enter text into an app.</span></span> <span data-ttu-id="3508b-198">Questo può accelerare significativamente l'input con minore impegno per l'utente.</span><span class="sxs-lookup"><span data-stu-id="3508b-198">This can greatly accelerate input with less effort for the user.</span></span>

<span data-ttu-id="3508b-199">![La dettatura vocale inizia selezionando il pulsante del microfono](images/micbuttonfordictation.png)</span><span class="sxs-lookup"><span data-stu-id="3508b-199">![Voice dictation starts by selecting the microphone button](images/micbuttonfordictation.png)</span></span><br>
<span data-ttu-id="3508b-200">*La dettatura vocale inizia selezionando il pulsante del microfono sulla tastiera*</span><span class="sxs-lookup"><span data-stu-id="3508b-200">*Voice dictation starts by selecting the microphone button on the keyboard*</span></span>

<span data-ttu-id="3508b-201">Quando la tastiera olografica è attiva, è possibile passare alla modalità di dettatura anziché alla digitazione.</span><span class="sxs-lookup"><span data-stu-id="3508b-201">Anytime the holographic keyboard is active, you can switch to dictation mode instead of typing.</span></span> <span data-ttu-id="3508b-202">Per iniziare, selezionare il microfono sul lato della casella input di testo.</span><span class="sxs-lookup"><span data-stu-id="3508b-202">Select the microphone on the side of the text input box to get started.</span></span>

## <a name="adding-voice-commands-to-your-app"></a><span data-ttu-id="3508b-203">Aggiunta di comandi vocali all'app</span><span class="sxs-lookup"><span data-stu-id="3508b-203">Adding voice commands to your app</span></span>

<span data-ttu-id="3508b-204">Valuta l'opportunità di aggiungere comandi vocali a un'esperienza che stai creando.</span><span class="sxs-lookup"><span data-stu-id="3508b-204">Consider adding voice commands to any experience that you build.</span></span> <span data-ttu-id="3508b-205">Voice è un potente strumento per controllare il sistema e le app.</span><span class="sxs-lookup"><span data-stu-id="3508b-205">Voice is a powerful way control the system and apps.</span></span> <span data-ttu-id="3508b-206">Poiché gli utenti parlano con tipi diversi di dialetti e accenti, la scelta corretta di parole chiave per il riconoscimento vocale garantisce che i comandi degli utenti vengano interpretati in modo non ambiguo.</span><span class="sxs-lookup"><span data-stu-id="3508b-206">Because users speak with different kinds of dialects and accents, proper choice of speech keywords will make sure your users' commands are interpreted unambiguously.</span></span>

### <a name="best-practices"></a><span data-ttu-id="3508b-207">Procedure consigliate</span><span class="sxs-lookup"><span data-stu-id="3508b-207">Best practices</span></span>

<span data-ttu-id="3508b-208">Di seguito vengono illustrate alcune procedure che semplificheranno il riconoscimento vocale.</span><span class="sxs-lookup"><span data-stu-id="3508b-208">Below are some practices that will aid in smooth speech recognition.</span></span>
* <span data-ttu-id="3508b-209">**Usa comandi concisi**. Quando possibile, scegli parole chiave di due o più sillabe.</span><span class="sxs-lookup"><span data-stu-id="3508b-209">**Use concise commands** - When possible, choose keywords of two or more syllables.</span></span> <span data-ttu-id="3508b-210">Le parole di una sillaba tendono a usare suoni di vocali differenti se pronunciate da persone con accenti diversi.</span><span class="sxs-lookup"><span data-stu-id="3508b-210">One-syllable words tend to use different vowel sounds when spoken by persons of different accents.</span></span> <span data-ttu-id="3508b-211">Esempio: "riprodurre video" è migliore di "riprodurre il video attualmente selezionato"</span><span class="sxs-lookup"><span data-stu-id="3508b-211">Example: "Play video" is better than "Play the currently selected video"</span></span>
* <span data-ttu-id="3508b-212">**Usare un vocabolario semplice** , ad esempio: "show note" è migliore di "Show manifest"</span><span class="sxs-lookup"><span data-stu-id="3508b-212">**Use simple vocabulary** - Example: "Show note" is better than "Show placard"</span></span>
* <span data-ttu-id="3508b-213">Assicurarsi che i **comandi non siano distruttivi** . Assicurarsi che le azioni del comando vocale non siano distruttive e che sia possibile annullarla in caso di un'altra persona che parla vicino all'utente accidentalmente un comando.</span><span class="sxs-lookup"><span data-stu-id="3508b-213">**Make sure commands are non-destructive** - Make sure any speech command actions are non-destructive and can easily be undone in case another person speaking near the user accidentally triggers a command.</span></span>
* <span data-ttu-id="3508b-214">**Evitare comandi audio simili** . evitare di registrare più comandi vocali che sembrano simili.</span><span class="sxs-lookup"><span data-stu-id="3508b-214">**Avoid similar sounding commands** - Avoid registering multiple speech commands that sound similar.</span></span> <span data-ttu-id="3508b-215">Esempio: "Mostra più" e "Mostra archivio" può essere un suono simile.</span><span class="sxs-lookup"><span data-stu-id="3508b-215">Example: "Show more" and "Show store" can be similar sounding.</span></span>
* <span data-ttu-id="3508b-216">**Annulla la registrazione dell'app quando non usa** -quando l'app non è in uno stato in cui un particolare comando vocale è valido, è consigliabile annullarne la registrazione in modo che gli altri comandi non siano confusi.</span><span class="sxs-lookup"><span data-stu-id="3508b-216">**Unregister your app when not it uses** - When your app isn't in a state in which a particular speech command is valid, consider unregistering it so that other commands aren't confused for that one.</span></span>
* <span data-ttu-id="3508b-217">**Esegui test con accenti diversi**. Testa l'app con utenti con accenti diversi.</span><span class="sxs-lookup"><span data-stu-id="3508b-217">**Test with different accents** - Test your app with users of different accents.</span></span>
* <span data-ttu-id="3508b-218">**Mantieni la coerenza dei comandi vocali**. Se "Indietro" porta alla pagina precedente, mantieni questo comportamento nelle applicazioni.</span><span class="sxs-lookup"><span data-stu-id="3508b-218">**Maintain voice command consistency** - If "Go back" goes to the previous page, maintain this behavior in your applications.</span></span>
* <span data-ttu-id="3508b-219">**Evitare di usare i comandi di sistema** : i comandi vocali seguenti sono riservati per il sistema, quindi evitare di usarli nelle applicazioni:</span><span class="sxs-lookup"><span data-stu-id="3508b-219">**Avoid using system commands** - The following voice commands are reserved for the system, so avoid using them in your applications:</span></span>
   * <span data-ttu-id="3508b-220">"Ehi Cortana"</span><span class="sxs-lookup"><span data-stu-id="3508b-220">"Hey Cortana"</span></span>
   * <span data-ttu-id="3508b-221">"Seleziona"</span><span class="sxs-lookup"><span data-stu-id="3508b-221">"Select"</span></span>
   * <span data-ttu-id="3508b-222">"Vai all'avvio"</span><span class="sxs-lookup"><span data-stu-id="3508b-222">"Go to start"</span></span>

### <a name="advantages-of-voice-input"></a><span data-ttu-id="3508b-223">Vantaggi dell'input vocale</span><span class="sxs-lookup"><span data-stu-id="3508b-223">Advantages of voice input</span></span>

<span data-ttu-id="3508b-224">L'input vocale è un modo naturale di comunicare le intenzioni.</span><span class="sxs-lookup"><span data-stu-id="3508b-224">Voice input is a natural way to communicate our intents.</span></span> <span data-ttu-id="3508b-225">La voce è particolarmente utile negli **attraversamenti** dell'interfaccia perché può aiutare gli utenti a tagliare più passaggi di un'interfaccia.</span><span class="sxs-lookup"><span data-stu-id="3508b-225">Voice is especially good at interface **traversals** because it can help users cut through multiple steps of an interface.</span></span> <span data-ttu-id="3508b-226">Un utente potrebbe dire "tornare indietro" guardando una pagina Web, anziché dover passare al pulsante indietro nell'app.</span><span class="sxs-lookup"><span data-stu-id="3508b-226">A user might say "go back" while looking at a webpage, instead of having to go up and hit the back button in the app.</span></span> <span data-ttu-id="3508b-227">Questo piccolo risparmio di tempo ha un forte **effetto emotivo** sulla percezione dell'esperienza dell'utente e offre una piccola superpotenza.</span><span class="sxs-lookup"><span data-stu-id="3508b-227">This small time saving has a powerful **emotional effect** on user’s perception of the experience and gives them a small amount superpower.</span></span> <span data-ttu-id="3508b-228">I comandi vocali rappresentano anche un pratico metodo di input quando hai le mani occupate oppure quando sei in modalità **multitasking**.</span><span class="sxs-lookup"><span data-stu-id="3508b-228">Using voice is also a convenient input method when we have our arms full or are **multi-tasking**.</span></span> <span data-ttu-id="3508b-229">Nei dispositivi in cui la digitazione su una tastiera è difficile, la **Dettatura vocale** può essere un metodo alternativo efficace per inserire il testo.</span><span class="sxs-lookup"><span data-stu-id="3508b-229">On devices where typing on a keyboard is difficult, **voice dictation** can be an efficient alternative way to input text.</span></span> <span data-ttu-id="3508b-230">Infine, in alcuni casi, quando l' **intervallo di accuratezza** per lo sguardo e il movimento sono limitati, Voice può contribuire a evitare ambiguità tra le finalità dell'utente.</span><span class="sxs-lookup"><span data-stu-id="3508b-230">Lastly, in some cases when the **range of accuracy** for gaze and gesture are limited, voice can help to disambiguate the user's intent.</span></span> 

<span data-ttu-id="3508b-231">**In che modo i comandi vocali possono rivelarsi utili per l'utente**</span><span class="sxs-lookup"><span data-stu-id="3508b-231">**How using voice can benefit the user**</span></span>
* <span data-ttu-id="3508b-232">Riducono i tempi: devono rendere l'obiettivo finale più efficiente.</span><span class="sxs-lookup"><span data-stu-id="3508b-232">Reduces time - it should make the end goal more efficient.</span></span>
* <span data-ttu-id="3508b-233">Riducono al minimo lo sforzo: devono rendere le attività più fluide e semplici.</span><span class="sxs-lookup"><span data-stu-id="3508b-233">Minimizes effort - it should make tasks more fluid and effortless.</span></span>
* <span data-ttu-id="3508b-234">Riducono il carico cognitivo: sono intuitivi e facili da imparare e ricordare.</span><span class="sxs-lookup"><span data-stu-id="3508b-234">Reduces cognitive load - it's intuitive, easy to learn, and remember.</span></span>
* <span data-ttu-id="3508b-235">È socialmente accettabile. dovrebbe adattarsi alle normative di comportamento della società.</span><span class="sxs-lookup"><span data-stu-id="3508b-235">It's socially acceptable - it should fit in with societal norms of behavior.</span></span>
* <span data-ttu-id="3508b-236">Rappresentano la routine: i comandi vocali possono facilmente diventare un comportamento abituale.</span><span class="sxs-lookup"><span data-stu-id="3508b-236">It's routine - voice can readily become a habitual behavior.</span></span>

### <a name="challenges-for-voice-input"></a><span data-ttu-id="3508b-237">Problemi per l'input vocale</span><span class="sxs-lookup"><span data-stu-id="3508b-237">Challenges for voice input</span></span>

<span data-ttu-id="3508b-238">Anche se l'input vocale è ideale per molte applicazioni diverse, presenta anche diverse problemi.</span><span class="sxs-lookup"><span data-stu-id="3508b-238">While voice input is great for many different applications, it also faces several challenges.</span></span> <span data-ttu-id="3508b-239">Comprendere i vantaggi e le esigenze per l'input vocale consente agli sviluppatori di app di prendere scelte più intelligenti per sapere come e quando usare l'input vocale e per creare un'esperienza ottimale per gli utenti.</span><span class="sxs-lookup"><span data-stu-id="3508b-239">Understanding both the advantages and challenges for voice input enables app developers to make smarter choices for how and when to use voice input and to create a great experience for their users.</span></span>

<span data-ttu-id="3508b-240">**Input vocale per il controllo di input continuo** Il controllo con granularità fine è uno di essi.</span><span class="sxs-lookup"><span data-stu-id="3508b-240">**Voice input for continuous input control** Fine-grained control is one of them.</span></span> <span data-ttu-id="3508b-241">Ad esempio, un utente potrebbe voler modificare il volume nella propria app musicale.</span><span class="sxs-lookup"><span data-stu-id="3508b-241">For example, a user might want to change their volume in their music app.</span></span> <span data-ttu-id="3508b-242">Può dire "più forte", ma non è chiaro quanto sia forte il sistema che deve creare il volume.</span><span class="sxs-lookup"><span data-stu-id="3508b-242">She can say "louder", but it's not clear how much louder the system is supposed to make the volume.</span></span> <span data-ttu-id="3508b-243">L'utente può affermare: "renderlo un po' più forte", ma è difficile quantificare "un po'".</span><span class="sxs-lookup"><span data-stu-id="3508b-243">The user could say: "Make it a little louder", but "a little" is difficult to quantify.</span></span> <span data-ttu-id="3508b-244">Lo stato di scalabilità o di ridimensionamento degli ologrammi con la voce è simile.</span><span class="sxs-lookup"><span data-stu-id="3508b-244">Moving or scaling holograms with voice is similarly difficult.</span></span> 

<span data-ttu-id="3508b-245">**Affidabilità del rilevamento dell'input vocale** Sebbene i sistemi di input vocali siano migliori e migliori, a volte potrebbero non essere in grado di ascoltare e interpretare un comando vocale.</span><span class="sxs-lookup"><span data-stu-id="3508b-245">**Reliability of voice input detection** While voice input systems become better and better, sometimes they may incorrectly hear and interpret a voice command.</span></span>
<span data-ttu-id="3508b-246">La chiave consiste nel risolvere il problema nell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="3508b-246">The key is to address the challenge in your application.</span></span> <span data-ttu-id="3508b-247">Fornire commenti e suggerimenti agli utenti quando il sistema è in ascolto e ciò che il sistema ha compreso chiarisce i potenziali problemi relativi alla sintesi vocale degli utenti.</span><span class="sxs-lookup"><span data-stu-id="3508b-247">Provide feedback to your users when the system is listening and what the system understood clarifies potential issues understanding the users' speech.</span></span>  

<span data-ttu-id="3508b-248">**Input vocale negli spazi condivisi** La voce potrebbe non essere socialmente accettabile negli spazi condivisi con altri utenti.</span><span class="sxs-lookup"><span data-stu-id="3508b-248">**Voice input in shared spaces** Voice may not be socially acceptable in spaces that you share with others.</span></span>
<span data-ttu-id="3508b-249">Ecco alcuni esempi:</span><span class="sxs-lookup"><span data-stu-id="3508b-249">Here are a few examples:</span></span>
* <span data-ttu-id="3508b-250">L'utente potrebbe non voler disturbare altri, ad esempio in una libreria non interattiva o in un ufficio condiviso</span><span class="sxs-lookup"><span data-stu-id="3508b-250">The user may not want to disturb others (for example, in a quiet library or shared office)</span></span>
* <span data-ttu-id="3508b-251">Gli utenti potrebbero sembrare imbarazzanti,</span><span class="sxs-lookup"><span data-stu-id="3508b-251">Users may feel awkward being seen talking to themselves in public,</span></span>
* <span data-ttu-id="3508b-252">Un utente potrebbe non essere scomodo a indicare un messaggio personale o riservato (incluse le password) mentre altri sono in ascolto</span><span class="sxs-lookup"><span data-stu-id="3508b-252">A user may feel uncomfortable dictating a personal or confidential message (including passwords) while others are listening</span></span>

<span data-ttu-id="3508b-253">**Input vocale di parole univoche o sconosciute** Le difficoltà per l'input vocale si verificano anche quando gli utenti impongono parole che potrebbero essere sconosciute al sistema, ad esempio nomi alternativi, parole slang specifiche o abbreviazioni.</span><span class="sxs-lookup"><span data-stu-id="3508b-253">**Voice input of unique or unknown words** Difficulties for voice input also come when users are dictating words that may be unknown to the system, such as nicknames, certain slang words, or abbreviations.</span></span> 

<span data-ttu-id="3508b-254">**Apprendimento di comandi vocali** Anche se l'obiettivo finale è quello di comunicare naturalmente con il sistema, spesso le app si basano su comandi vocali predefiniti specifici.</span><span class="sxs-lookup"><span data-stu-id="3508b-254">**Learning voice commands** While the ultimate goal is to naturally converse with your system, often apps still rely on specific pre-defined voice commands.</span></span>
<span data-ttu-id="3508b-255">Un problema associato a un set significativo di comandi vocali è come insegnarli senza sovraccaricare l'utente e come aiutarli a mantenerli.</span><span class="sxs-lookup"><span data-stu-id="3508b-255">A challenge associated with a significant set of voice commands is how to teach them without overloading the user and how to help the user to keep them.</span></span> 

<br>

---

### <a name="voice-feedback-states"></a><span data-ttu-id="3508b-256">Stati di feedback dei comandi vocali</span><span class="sxs-lookup"><span data-stu-id="3508b-256">Voice feedback states</span></span>

<span data-ttu-id="3508b-257">Quando i comandi vocali vengono applicati in modo corretto, l'utente capisce **cosa può dire e ottiene un feedback chiaro** a indicare che il sistema ha **recepito correttamente i comandi**.</span><span class="sxs-lookup"><span data-stu-id="3508b-257">When Voice is applied properly, the user understands **what they can say and get clear feedback** the system **heard them correctly**.</span></span> <span data-ttu-id="3508b-258">Questi due segnali fanno sì che l'utente si senta sicuro di usare i comandi vocali come input principale.</span><span class="sxs-lookup"><span data-stu-id="3508b-258">These two signals make the user feel confident in using Voice as a primary input.</span></span> <span data-ttu-id="3508b-259">Di seguito è riportato un diagramma che illustra che cosa accade al cursore quando l'input vocale viene riconosciuto e come tale risultato viene comunicato all'utente.</span><span class="sxs-lookup"><span data-stu-id="3508b-259">Below is a diagram showing what happens to the cursor when voice input is recognized and how it communicates that to the user.</span></span>


:::row:::
    :::column:::
       <span data-ttu-id="3508b-260">![1. stato del cursore normale](images/voicefeedbackstates-regular.jpg)</span><span class="sxs-lookup"><span data-stu-id="3508b-260">![1. Regular cursor state](images/voicefeedbackstates-regular.jpg)</span></span><br>
       <span data-ttu-id="3508b-261">**1. stato del cursore normale**</span><span class="sxs-lookup"><span data-stu-id="3508b-261">**1. Regular cursor state**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="3508b-262">![2. comunica il feedback vocale e scompare](images/voicefeedbackstates-voice.jpg)</span><span class="sxs-lookup"><span data-stu-id="3508b-262">![2. Communicates voice feedback and then disappears](images/voicefeedbackstates-voice.jpg)</span></span><br>
        <span data-ttu-id="3508b-263">**2. comunica il feedback vocale e scompare**</span><span class="sxs-lookup"><span data-stu-id="3508b-263">**2. Communicates voice feedback and then disappears**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="3508b-264">![3.</span><span class="sxs-lookup"><span data-stu-id="3508b-264">![\*3.</span></span> <span data-ttu-id="3508b-265">Stato normale del cursore](images/voicefeedbackstates-regular.jpg)</span><span class="sxs-lookup"><span data-stu-id="3508b-265">Regular cursor state](images/voicefeedbackstates-regular.jpg)</span></span><br>
       <span data-ttu-id="3508b-266">**3. torna allo stato normale del cursore**</span><span class="sxs-lookup"><span data-stu-id="3508b-266">**3. Returns to regular cursor state**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

<br>

## <a name="top-things-users-should-know-about-speech-in-mixed-reality"></a><span data-ttu-id="3508b-267">Nozioni di base sui comandi vocali che gli utenti devono conoscere per la realtà mista</span><span class="sxs-lookup"><span data-stu-id="3508b-267">Top things users should know about "speech" in mixed reality</span></span>

* <span data-ttu-id="3508b-268">Pronunciare **"Select"** mentre si sceglie come destinazione un pulsante (è possibile usarlo in qualsiasi punto per selezionare un pulsante).</span><span class="sxs-lookup"><span data-stu-id="3508b-268">Say **"Select"** while targeting a button (you can use this anywhere to select a button).</span></span>
* <span data-ttu-id="3508b-269">Puoi pronunciare il **nome dell'etichetta di un pulsante della barra dell'app** in alcune app per eseguire un'azione.</span><span class="sxs-lookup"><span data-stu-id="3508b-269">You can say the **label name of an app bar button** in some apps to take an action.</span></span> <span data-ttu-id="3508b-270">Ad esempio, quando si esamina un'app, un utente può pronunciare il comando "Remove" per rimuovere l'app dal mondo. in questo modo si evita di dover selezionare la propria mano.</span><span class="sxs-lookup"><span data-stu-id="3508b-270">For example, while looking at an app, a user can say the command "Remove" to remove the app from the world (this saves time from having to select it with your hand).</span></span>
* <span data-ttu-id="3508b-271">È possibile avviare Cortana in attesa dicendo **"Hey Cortana".**</span><span class="sxs-lookup"><span data-stu-id="3508b-271">You can start Cortana listening by saying **"Hey Cortana."**</span></span> <span data-ttu-id="3508b-272">Puoi porre domande ("Ehi Cortana, quanto è alta la Torre Eiffel?"), chiedere di aprire un'app ("Ehi Cortana, apri Netflix") o chiedere di visualizzare il menu di avvio ("Ehi Cortana, portami all'inizio") e altro ancora.</span><span class="sxs-lookup"><span data-stu-id="3508b-272">You can ask her questions ("Hey Cortana, how tall is the Eiffel tower"), tell her to open an app ("Hey Cortana, open Netflix"), or tell her to bring up the Start Menu ("Hey Cortana, take me home") and more.</span></span>

## <a name="common-questions-and-concerns-users-have-about-voice"></a><span data-ttu-id="3508b-273">Domande e dubbi comuni degli utenti sui comandi vocali</span><span class="sxs-lookup"><span data-stu-id="3508b-273">Common questions and concerns users have about voice</span></span>

* <span data-ttu-id="3508b-274">What can I say?</span><span class="sxs-lookup"><span data-stu-id="3508b-274">What can I say?</span></span>
* <span data-ttu-id="3508b-275">Come posso sapere se il sistema mi ha capito correttamente?</span><span class="sxs-lookup"><span data-stu-id="3508b-275">How do I know the system heard me correctly?</span></span>
   * <span data-ttu-id="3508b-276">Il sistema continua a interpretare i miei comandi vocali in modo errato.</span><span class="sxs-lookup"><span data-stu-id="3508b-276">The system keeps getting my voice commands wrong.</span></span>
   * <span data-ttu-id="3508b-277">Non reagisce quando pronuncio un comando vocale.</span><span class="sxs-lookup"><span data-stu-id="3508b-277">It doesn’t react when I give it a voice command.</span></span>
* <span data-ttu-id="3508b-278">Reagisce in modo non corretto quando pronuncio un comando vocale.</span><span class="sxs-lookup"><span data-stu-id="3508b-278">It reacts the wrong way when I give it a voice command.</span></span>
* <span data-ttu-id="3508b-279">Come posso indirizzare un comando vocale a una specifica app o un comando di app?</span><span class="sxs-lookup"><span data-stu-id="3508b-279">How do I target my voice to a specific app or app command?</span></span>
* <span data-ttu-id="3508b-280">Posso usare i comandi vocali per operazioni all'esterno del fotogramma olografico di HoloLens?</span><span class="sxs-lookup"><span data-stu-id="3508b-280">Can I use voice to command things out the holographic frame on HoloLens?</span></span>

## <a name="communication"></a><span data-ttu-id="3508b-281">Comunicazione</span><span class="sxs-lookup"><span data-stu-id="3508b-281">Communication</span></span>

<span data-ttu-id="3508b-282">Per le applicazioni che vogliono sfruttare le opzioni di elaborazione dell'input audio personalizzato fornite da HoloLens, è importante comprendere le diverse categorie di [flussi audio](/windows/win32/api/audiosessiontypes/ne-audiosessiontypes-audio_stream_category) che l'app può utilizzare.</span><span class="sxs-lookup"><span data-stu-id="3508b-282">For applications that want to take advantage of the customized audio input processing options provided by HoloLens, it's important to understand the various [audio stream categories](/windows/win32/api/audiosessiontypes/ne-audiosessiontypes-audio_stream_category) your app can consume.</span></span> <span data-ttu-id="3508b-283">Windows 10 supporta diverse categorie di flusso e HoloLens ne usa tre per consentire l'elaborazione personalizzata per ottimizzare la qualità audio del microfono personalizzata per la comunicazione vocale, la comunicazione e altro, che può essere usata per gli scenari di acquisizione audio dell'ambiente di ambiente (ovvero "videocamera").</span><span class="sxs-lookup"><span data-stu-id="3508b-283">Windows 10 supports several different stream categories and HoloLens makes use of three of these to enable custom processing to optimize the microphone audio quality tailored for speech, communication, and other, which can be used for ambient environment audio capture (that is, "camcorder") scenarios.</span></span>
* <span data-ttu-id="3508b-284">La categoria AudioCategory_Communications Stream è personalizzata per gli scenari di qualità della chiamata e di narrazione e fornisce al client un flusso audio mono a 16 kHz a 24 bit della voce dell'utente</span><span class="sxs-lookup"><span data-stu-id="3508b-284">The AudioCategory_Communications stream category is customized for call quality and narration scenarios and provides the client with a 16-kHz 24-bit mono audio stream of the user's voice</span></span>
* <span data-ttu-id="3508b-285">La categoria del flusso di AudioCategory_Speech è personalizzata per il motore di riconoscimento vocale HoloLens (Windows) e fornisce un flusso mono a 24 bit a 16 kHz della voce dell'utente.</span><span class="sxs-lookup"><span data-stu-id="3508b-285">The AudioCategory_Speech stream category is customized for the HoloLens (Windows) speech engine and provides it with a 16-kHz 24-bit mono stream of the user's voice.</span></span> <span data-ttu-id="3508b-286">Questa categoria può essere usata dai motori di sintesi vocale di terze parti, se necessario.</span><span class="sxs-lookup"><span data-stu-id="3508b-286">This category can be used by third-party speech engines if needed.</span></span>
* <span data-ttu-id="3508b-287">La categoria AudioCategory_Other Stream è personalizzata per la registrazione audio dell'ambiente di ambiente e fornisce al client un flusso audio stereo a 48 kHz a 24 bit.</span><span class="sxs-lookup"><span data-stu-id="3508b-287">The AudioCategory_Other stream category is customized for ambient environment audio recording and provides the client with a 48-kHz 24-bit stereo audio stream.</span></span>

<span data-ttu-id="3508b-288">Questa elaborazione audio è accelerata dall'hardware, il che significa che le funzionalità svuotano molto meno energia rispetto a quando la stessa elaborazione è stata eseguita sulla CPU HoloLens.</span><span class="sxs-lookup"><span data-stu-id="3508b-288">All this audio processing is hardware accelerated which means the features drain a lot less power than if the same processing was done on the HoloLens CPU.</span></span> <span data-ttu-id="3508b-289">Evitare di eseguire altre elaborazioni di input audio sulla CPU per ottimizzare la durata della batteria del sistema e sfruttare i vantaggi dell'elaborazione incorporata di input audio con offload.</span><span class="sxs-lookup"><span data-stu-id="3508b-289">Avoid running other audio input processing on the CPU to maximize system battery life and take advantage of the built-in, offloaded audio input processing.</span></span>

## <a name="languages"></a><span data-ttu-id="3508b-290">Linguaggi</span><span class="sxs-lookup"><span data-stu-id="3508b-290">Languages</span></span>

<span data-ttu-id="3508b-291">HoloLens 2 [supporta più lingue](/hololens/hololens2-language-support).</span><span class="sxs-lookup"><span data-stu-id="3508b-291">HoloLens 2 [supports multiple languages](/hololens/hololens2-language-support).</span></span> <span data-ttu-id="3508b-292">Tenere presente che i comandi vocali verranno sempre eseguiti nella lingua di visualizzazione del sistema anche se sono installate più tastiere o se le app tentano di creare un riconoscimento vocale in una lingua diversa.</span><span class="sxs-lookup"><span data-stu-id="3508b-292">Keep in mind that speech commands will always run in the system's display language even if multiple keyboards are installed or if apps attempt to create a speech recognizer in a different language.</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="3508b-293">Risoluzione dei problemi</span><span class="sxs-lookup"><span data-stu-id="3508b-293">Troubleshooting</span></span>

<span data-ttu-id="3508b-294">Se si verificano problemi con "Select" e "Hey Cortana", provare a passare a uno spazio più silenzioso, a disattivarsi dall'origine del rumore o a una voce più forte.</span><span class="sxs-lookup"><span data-stu-id="3508b-294">If you're having any issues using "select" and "Hey Cortana", try moving to a quieter space, turning away from the source of noise, or by speaking louder.</span></span> <span data-ttu-id="3508b-295">A questo punto, tutto il riconoscimento vocale in HoloLens viene ottimizzato e ottimizzato in modo specifico per gli altoparlanti nativi di Stati Uniti inglese.</span><span class="sxs-lookup"><span data-stu-id="3508b-295">At this time, all speech recognition on HoloLens is tuned and optimized specifically to native speakers of United States English.</span></span>

<span data-ttu-id="3508b-296">Per la versione 2017 di Windows Mixed Reality Developer Edition, la logica di gestione degli endpoint audio funzionerà correttamente (per sempre) dopo la disconnessione e l'accesso al desktop del PC dopo la connessione iniziale di HMD.</span><span class="sxs-lookup"><span data-stu-id="3508b-296">For the Windows Mixed Reality Developer Edition release 2017, the audio endpoint management logic will work fine (forever) after logging out and back in to the PC desktop after the initial HMD connection.</span></span> <span data-ttu-id="3508b-297">Prima della prima disconnessione/evento dopo aver attraversato la configurazione guidata di WMR, l'utente può riscontrare diversi problemi di funzionalità audio che variano da nessuna audio a nessuna modifica audio a seconda di come è stato configurato il sistema prima di connettere HMD per la prima volta.</span><span class="sxs-lookup"><span data-stu-id="3508b-297">Before that first sign out/in event after going through WMR OOBE, the user could experience various audio functionality issues ranging from no audio to no audio switching depending on how the system was set up before connecting the HMD for the first time.</span></span>

<br>

---

## <a name="voice-input-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="3508b-298">Input vocale in MRTK (Mixed Reality Toolkit) per Unity</span><span class="sxs-lookup"><span data-stu-id="3508b-298">Voice input in MRTK (Mixed Reality Toolkit) for Unity</span></span>
<span data-ttu-id="3508b-299">Con **[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)**, è possibile assegnare facilmente il comando Voice a tutti gli oggetti.</span><span class="sxs-lookup"><span data-stu-id="3508b-299">With **[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)**, you can easily assign voice command on any objects.</span></span> <span data-ttu-id="3508b-300">Usare **il profilo di input vocale** di MRTK per definire le parole chiave.</span><span class="sxs-lookup"><span data-stu-id="3508b-300">Use MRTK's **Speech Input Profile** to define your keywords.</span></span> <span data-ttu-id="3508b-301">Assegnando lo script **SpeechInputHandler** , è possibile fare in modo che qualsiasi oggetto risponda alle parole chiave definite nel profilo di input vocale.</span><span class="sxs-lookup"><span data-stu-id="3508b-301">By assigning **SpeechInputHandler** script, you can make any object respond to the keywords defined in the Speech Input Profile.</span></span> <span data-ttu-id="3508b-302">SpeechInputHandler fornisce anche un'etichetta di conferma vocale per migliorare la confidenza dell'utente.</span><span class="sxs-lookup"><span data-stu-id="3508b-302">SpeechInputHandler also provides speech confirmation label to improve the user's confidence.</span></span>

* [<span data-ttu-id="3508b-303">Comando MRTK-Voice</span><span class="sxs-lookup"><span data-stu-id="3508b-303">MRTK - Voice command</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Speech.html)

---

## <a name="see-also"></a><span data-ttu-id="3508b-304">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="3508b-304">See also</span></span>

* [<span data-ttu-id="3508b-305">Sguardo e commit</span><span class="sxs-lookup"><span data-stu-id="3508b-305">Gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="3508b-306">Interazioni istintive</span><span class="sxs-lookup"><span data-stu-id="3508b-306">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="3508b-307">Input vocale in DirectX</span><span class="sxs-lookup"><span data-stu-id="3508b-307">Voice input in DirectX</span></span>](../develop/native/voice-input-in-directx.md)
* [<span data-ttu-id="3508b-308">Input vocale in Unity</span><span class="sxs-lookup"><span data-stu-id="3508b-308">Voice input in Unity</span></span>](../develop/unity/voice-input-in-unity.md)
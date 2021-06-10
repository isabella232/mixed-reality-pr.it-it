---
title: Uso del riconoscimento vocale in Windows Mixed Reality
description: Informazioni su come usare l'input vocale per controllare comandi, oggetti 3D e dettatura nelle Windows Mixed Reality app.
author: hferrone
ms.author: v-hferrone
ms.date: 09/16/2020
ms.topic: article
keywords: Windows Mixed Reality, Realtà mista, Realtà virtuale, VR, MR, Feedback, Hub di Feedback, bug
appliesto:
- Windows 10
ms.openlocfilehash: 23e3ea9014612d5df8935552d7b767454b9eefa7
ms.sourcegitcommit: a5afc24a4887880e394ef57216b8fd9de9760004
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/28/2021
ms.locfileid: "110647023"
---
# <a name="using-speech-in-windows-mixed-reality"></a><span data-ttu-id="f70fa-104">Uso del riconoscimento vocale in Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="f70fa-104">Using Speech in Windows Mixed Reality</span></span>

<span data-ttu-id="f70fa-105">È possibile usare la voce per spostarsi Windows Mixed Reality più velocemente.</span><span class="sxs-lookup"><span data-stu-id="f70fa-105">You can use your voice to get around Windows Mixed Reality faster.</span></span> <span data-ttu-id="f70fa-106">Scattare una foto veloce, aprire un'app, persino teletrasportarsi senza un controller, è tutto a una parola.</span><span class="sxs-lookup"><span data-stu-id="f70fa-106">Taking a quick photo, opening an app, even teleporting without a controller are all a word away.</span></span> <span data-ttu-id="f70fa-107">Per un modo semplice di digitare, provare la modalità dettatura sulla tastiera di realtà mista.</span><span class="sxs-lookup"><span data-stu-id="f70fa-107">For an easy way to type, try dictation mode on the mixed reality keyboard.</span></span> 

<span data-ttu-id="f70fa-108">Problemi con il riconoscimento vocale?</span><span class="sxs-lookup"><span data-stu-id="f70fa-108">Having trouble with Speech?</span></span> [<span data-ttu-id="f70fa-109">Ottieni aiuto</span><span class="sxs-lookup"><span data-stu-id="f70fa-109">Get help</span></span>](using-wmr-faq.yml#speech-commands-aren-t-working)

<!-- NEED VIDEO: https://support.microsoft.com/en-us/help/4041322/windows-10-speech-in-windows-mixed-reality -->

> [!NOTE]
> * <span data-ttu-id="f70fa-110">Quando voce è attivata, Windows Mixed Reality è sempre in ascolto.</span><span class="sxs-lookup"><span data-stu-id="f70fa-110">When Speech is turned on, Windows Mixed Reality is always listening.</span></span> <span data-ttu-id="f70fa-111">Quando si è connessi a Internet, microsoft invia tutto ciò che si dice al cloud in modo che i servizi di riconoscimento vocale Microsoft possano riconoscere ancora di più i comandi.</span><span class="sxs-lookup"><span data-stu-id="f70fa-111">When you’re connected to the Internet, we send everything you say to the cloud so Microsoft speech services can recognize even more of your commands.</span></span>
> * <span data-ttu-id="f70fa-112">I comandi vocali non sono supportati in tutte le lingue.</span><span class="sxs-lookup"><span data-stu-id="f70fa-112">Speech commands are not supported in all languages.</span></span> <span data-ttu-id="f70fa-113">Altre informazioni</span><span class="sxs-lookup"><span data-stu-id="f70fa-113">Learn more</span></span>
> * <span data-ttu-id="f70fa-114">I visori e gli altoparlanti Bluetooth non sono supportati in Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="f70fa-114">Bluetooth headsets and speakers are not supported in Windows Mixed Reality.</span></span>

## <a name="see-it-say-it"></a><span data-ttu-id="f70fa-115">Guarda, parla</span><span class="sxs-lookup"><span data-stu-id="f70fa-115">See it, say it</span></span>

<span data-ttu-id="f70fa-116">Nella home Windows Mixed Reality, se viene visualizzata una parola, è spesso possibile usarla come comando vocale.</span><span class="sxs-lookup"><span data-stu-id="f70fa-116">In the Windows Mixed Reality home, if you see a word, you can often use it as a speech command.</span></span> <span data-ttu-id="f70fa-117">Ad esempio, pronunciare semplicemente il nome di un pulsante per selezionarlo.</span><span class="sxs-lookup"><span data-stu-id="f70fa-117">For instance, just say the name of a button to select it.</span></span> <span data-ttu-id="f70fa-118">Se non viene visualizzato un nome, posizionare il controller di movimento sul pulsante per scoprire cosa dire.</span><span class="sxs-lookup"><span data-stu-id="f70fa-118">If you don’t see a name, point your motion controller at the button to find out what to say.</span></span> <span data-ttu-id="f70fa-119">Per i gamepad Xbox, posizionare lo sguardo sul pulsante.</span><span class="sxs-lookup"><span data-stu-id="f70fa-119">For Xbox gamepads, rest your gaze on the button.</span></span>

## <a name="general-speech-commands"></a><span data-ttu-id="f70fa-120">Comandi vocali generali</span><span class="sxs-lookup"><span data-stu-id="f70fa-120">General speech commands</span></span>

<span data-ttu-id="f70fa-121">Usare i comandi vocali seguenti in Windows Mixed Reality per spostarsi più velocemente.</span><span class="sxs-lookup"><span data-stu-id="f70fa-121">Use the following speech commands throughout Windows Mixed Reality to get around faster.</span></span> <span data-ttu-id="f70fa-122">Alcuni comandi usano il cursore sguardo fisso, che verrà visualizzato pronunciando "select".</span><span class="sxs-lookup"><span data-stu-id="f70fa-122">Some commands use the gaze cursor, which you’ll bring up by saying “select.”</span></span>

| <span data-ttu-id="f70fa-123">Per</span><span class="sxs-lookup"><span data-stu-id="f70fa-123">To do this</span></span> | <span data-ttu-id="f70fa-124">Pronunciare questo</span><span class="sxs-lookup"><span data-stu-id="f70fa-124">Say this</span></span> |
| --- | --- |
| <span data-ttu-id="f70fa-125">Seleziona</span><span class="sxs-lookup"><span data-stu-id="f70fa-125">Select</span></span> | <span data-ttu-id="f70fa-126">Pronunciare "select" per visualizzare il cursore dello sguardo.</span><span class="sxs-lookup"><span data-stu-id="f70fa-126">Say “select” to bring up the gaze cursor.</span></span> <span data-ttu-id="f70fa-127">Quindi, ruotare la testa per posizionare il cursore sull'oggetto da selezionare e pronunciare di nuovo "seleziona".</span><span class="sxs-lookup"><span data-stu-id="f70fa-127">Then, turn your head to position the cursor on the thing you want to select, and say “select” again.</span></span> |
| <span data-ttu-id="f70fa-128">Aprire il menu Start</span><span class="sxs-lookup"><span data-stu-id="f70fa-128">Open the Start menu</span></span> | <span data-ttu-id="f70fa-129">Vai a Start</span><span class="sxs-lookup"><span data-stu-id="f70fa-129">Go to Start</span></span> |
| <span data-ttu-id="f70fa-130">Lasciare un'app immersiva</span><span class="sxs-lookup"><span data-stu-id="f70fa-130">Leave an immersive app</span></span> | <span data-ttu-id="f70fa-131">Pronunciare "Vai a Start" per visualizzare il menu delle azioni rapide e quindi "Home della realtà mista".</span><span class="sxs-lookup"><span data-stu-id="f70fa-131">Say "Go to Start" to bring up the quick actions menu, then say "Mixed reality home."</span></span> |
| <span data-ttu-id="f70fa-132">Attivare/disattivare torcia</span><span class="sxs-lookup"><span data-stu-id="f70fa-132">Turn Flashlight on/off</span></span> | <span data-ttu-id="f70fa-133">Torcia spenta/torcia spenta</span><span class="sxs-lookup"><span data-stu-id="f70fa-133">Flashlight on / Flashlight off</span></span> |
| <span data-ttu-id="f70fa-134">Teletrasporto</span><span class="sxs-lookup"><span data-stu-id="f70fa-134">Teleport</span></span> | <span data-ttu-id="f70fa-135">Ruotare la testa verso il luogo in cui si vuole andare e quindi pronunciare "teletrasporto".</span><span class="sxs-lookup"><span data-stu-id="f70fa-135">Turn your head toward the place you want to go, and then say “teleport.”</span></span> <span data-ttu-id="f70fa-136">Per una destinazione più precisa, prima di tutto pronunciare "select" per visualizzare il cursore dello sguardo fisso e quindi dire "teletrasporto".</span><span class="sxs-lookup"><span data-stu-id="f70fa-136">(For more precise targeting, first say “select” to bring up the gaze cursor, then say “teleport.”)</span></span> |
| <span data-ttu-id="f70fa-137">Svoltare a sinistra o a destra</span><span class="sxs-lookup"><span data-stu-id="f70fa-137">Turn to the left or right</span></span> | <span data-ttu-id="f70fa-138">Svolta a sinistra/a destra</span><span class="sxs-lookup"><span data-stu-id="f70fa-138">Turn left / turn right</span></span> |
| <span data-ttu-id="f70fa-139">Ruotare di 180 gradi</span><span class="sxs-lookup"><span data-stu-id="f70fa-139">Turn 180 degrees</span></span> | <span data-ttu-id="f70fa-140">Girati</span><span class="sxs-lookup"><span data-stu-id="f70fa-140">Turn around</span></span> |
| <span data-ttu-id="f70fa-141">Andare avanti</span><span class="sxs-lookup"><span data-stu-id="f70fa-141">Move forward</span></span> | <span data-ttu-id="f70fa-142">Andare avanti/andare avanti</span><span class="sxs-lookup"><span data-stu-id="f70fa-142">Move forward / walk forward</span></span> |
| <span data-ttu-id="f70fa-143">Eseguire il backup</span><span class="sxs-lookup"><span data-stu-id="f70fa-143">Back up</span></span> | <span data-ttu-id="f70fa-144">Tornare indietro/tornare indietro</span><span class="sxs-lookup"><span data-stu-id="f70fa-144">Move back / walk back</span></span> |
| <span data-ttu-id="f70fa-145">Spostarsi a sinistra</span><span class="sxs-lookup"><span data-stu-id="f70fa-145">Move to the left</span></span> | <span data-ttu-id="f70fa-146">Spostarsi a sinistra/a sinistra</span><span class="sxs-lookup"><span data-stu-id="f70fa-146">Move left / walk left</span></span> |
| <span data-ttu-id="f70fa-147">Spostarsi a destra</span><span class="sxs-lookup"><span data-stu-id="f70fa-147">Move to the right</span></span> | <span data-ttu-id="f70fa-148">Spostarsi a destra/a destra</span><span class="sxs-lookup"><span data-stu-id="f70fa-148">Move right / walk right</span></span> |

## <a name="3d-object-commands"></a><span data-ttu-id="f70fa-149">Comandi per oggetti 3D</span><span class="sxs-lookup"><span data-stu-id="f70fa-149">3D object commands</span></span>

<span data-ttu-id="f70fa-150">Osservare un oggetto 3D, un ologramma o una finestra dell'app per usare questi comandi:</span><span class="sxs-lookup"><span data-stu-id="f70fa-150">Gaze at a 3D object, hologram, or app window to use these commands:</span></span>

| <span data-ttu-id="f70fa-151">Per</span><span class="sxs-lookup"><span data-stu-id="f70fa-151">To do this</span></span> | <span data-ttu-id="f70fa-152">Pronunciare questo</span><span class="sxs-lookup"><span data-stu-id="f70fa-152">Say this</span></span> |
| --- | --- |
| <span data-ttu-id="f70fa-153">Ingrandirla</span><span class="sxs-lookup"><span data-stu-id="f70fa-153">Make it bigger</span></span> | <span data-ttu-id="f70fa-154">Grande</span><span class="sxs-lookup"><span data-stu-id="f70fa-154">Bigger</span></span> |
| <span data-ttu-id="f70fa-155">Renderlo più piccolo</span><span class="sxs-lookup"><span data-stu-id="f70fa-155">Make it smaller</span></span> | <span data-ttu-id="f70fa-156">Piccoli</span><span class="sxs-lookup"><span data-stu-id="f70fa-156">Smaller</span></span> |
| <span data-ttu-id="f70fa-157">Ruotarlo per viso</span><span class="sxs-lookup"><span data-stu-id="f70fa-157">Turn it to face you</span></span> | <span data-ttu-id="f70fa-158">Guardami</span><span class="sxs-lookup"><span data-stu-id="f70fa-158">Face me</span></span> |
| <span data-ttu-id="f70fa-159">Prepararsi per lo spostamento: seguirà lo sguardo</span><span class="sxs-lookup"><span data-stu-id="f70fa-159">Get it ready to move - it will follow your gaze</span></span> | <span data-ttu-id="f70fa-160">Sposta</span><span class="sxs-lookup"><span data-stu-id="f70fa-160">Move this</span></span> |
| <span data-ttu-id="f70fa-161">Posizionarlo al termine dell'operazione di spostamento</span><span class="sxs-lookup"><span data-stu-id="f70fa-161">Place it when you're done moving it</span></span> | <span data-ttu-id="f70fa-162">Posizione</span><span class="sxs-lookup"><span data-stu-id="f70fa-162">Place</span></span> |

## <a name="app-bar-commands"></a><span data-ttu-id="f70fa-163">Comandi della barra dell'app</span><span class="sxs-lookup"><span data-stu-id="f70fa-163">App bar commands</span></span>

<span data-ttu-id="f70fa-164">Osservare una finestra dell'app o un oggetto 3D per usare questi comandi:</span><span class="sxs-lookup"><span data-stu-id="f70fa-164">Gaze at an app window or a 3D object to use these commands:</span></span>

| <span data-ttu-id="f70fa-165">Per</span><span class="sxs-lookup"><span data-stu-id="f70fa-165">To do this</span></span> | <span data-ttu-id="f70fa-166">Pronunciare questo</span><span class="sxs-lookup"><span data-stu-id="f70fa-166">Say this</span></span> |
| --- | --- |
| <span data-ttu-id="f70fa-167">Chiudere un'app o un oggetto 3D</span><span class="sxs-lookup"><span data-stu-id="f70fa-167">Close an app or 3D object</span></span> | <span data-ttu-id="f70fa-168">Chiudi</span><span class="sxs-lookup"><span data-stu-id="f70fa-168">Close</span></span> |
| <span data-ttu-id="f70fa-169">Modificare un elemento (ridimensionamento o spostamento)</span><span class="sxs-lookup"><span data-stu-id="f70fa-169">Adjust something (resize or move)</span></span> | <span data-ttu-id="f70fa-170">Regolare</span><span class="sxs-lookup"><span data-stu-id="f70fa-170">Adjust</span></span> |
| <span data-ttu-id="f70fa-171">Interrompi regolazione</span><span class="sxs-lookup"><span data-stu-id="f70fa-171">Stop adjusting</span></span> | <span data-ttu-id="f70fa-172">Fine</span><span class="sxs-lookup"><span data-stu-id="f70fa-172">Done</span></span> |
| <span data-ttu-id="f70fa-173">Nascondere la barra dell'app in un oggetto 3D</span><span class="sxs-lookup"><span data-stu-id="f70fa-173">Hide the app bar on a 3D object</span></span> | <span data-ttu-id="f70fa-174">Nascondi menu</span><span class="sxs-lookup"><span data-stu-id="f70fa-174">Hide menu</span></span> |
| <span data-ttu-id="f70fa-175">Visualizzare la barra dell'app su un oggetto 3D</span><span class="sxs-lookup"><span data-stu-id="f70fa-175">Show the app bar on a 3D object</span></span> | <span data-ttu-id="f70fa-176">Mostra menu</span><span class="sxs-lookup"><span data-stu-id="f70fa-176">Show Menu</span></span> |
| <span data-ttu-id="f70fa-177">Tornare alla schermata o alla pagina precedente in un'app con un pulsante Torna indietro</span><span class="sxs-lookup"><span data-stu-id="f70fa-177">Go back to the previous screen or page in an app that has a Go back button</span></span>  | <span data-ttu-id="f70fa-178">Indietro</span><span class="sxs-lookup"><span data-stu-id="f70fa-178">Go back</span></span> |
| <span data-ttu-id="f70fa-179">Usare il controller Xbox come gamepad, anziché come controller di realtà mista, nell'app che si sta esaminando</span><span class="sxs-lookup"><span data-stu-id="f70fa-179">Use your Xbox controller as a gamepad, rather than as a mixed reality controller, in the app you’re looking at</span></span> | <span data-ttu-id="f70fa-180">Usa come game pad</span><span class="sxs-lookup"><span data-stu-id="f70fa-180">Use as gamepad</span></span> |
| <span data-ttu-id="f70fa-181">Usare il controller Xbox come controller di realtà mista (quando è stato utilizzato come gamepad)</span><span class="sxs-lookup"><span data-stu-id="f70fa-181">Use your Xbox controller as a mixed reality controller (when you’ve been using it as a gamepad)</span></span> | <span data-ttu-id="f70fa-182">Usa con sguardo fisso</span><span class="sxs-lookup"><span data-stu-id="f70fa-182">Use with gaze</span></span> |

## <a name="start-menu-commands"></a><span data-ttu-id="f70fa-183">menu Start comandi</span><span class="sxs-lookup"><span data-stu-id="f70fa-183">Start menu commands</span></span>

<span data-ttu-id="f70fa-184">Osservare l'menu Start per usare questi comandi:</span><span class="sxs-lookup"><span data-stu-id="f70fa-184">Gaze at the Start menu to use these commands:</span></span>

| <span data-ttu-id="f70fa-185">Per</span><span class="sxs-lookup"><span data-stu-id="f70fa-185">To do this</span></span> | <span data-ttu-id="f70fa-186">Pronunciare questo</span><span class="sxs-lookup"><span data-stu-id="f70fa-186">Say this</span></span> |
| --- | --- |
| <span data-ttu-id="f70fa-187">Passare all'elenco Tutte le app</span><span class="sxs-lookup"><span data-stu-id="f70fa-187">Go to the All Apps list</span></span> | <span data-ttu-id="f70fa-188">Tutte le app</span><span class="sxs-lookup"><span data-stu-id="f70fa-188">All apps</span></span> |
| <span data-ttu-id="f70fa-189">Spostarsi verso l'alto o verso il basso in Start o Tutte le app</span><span class="sxs-lookup"><span data-stu-id="f70fa-189">Move up or down on Start or All apps</span></span> | <span data-ttu-id="f70fa-190">Pagina su/giù</span><span class="sxs-lookup"><span data-stu-id="f70fa-190">Page up/down</span></span> |
| <span data-ttu-id="f70fa-191">Tornare alla menu Start da Tutte le app</span><span class="sxs-lookup"><span data-stu-id="f70fa-191">Go back to Start menu from All apps</span></span> | <span data-ttu-id="f70fa-192">Indietro</span><span class="sxs-lookup"><span data-stu-id="f70fa-192">Go back</span></span> |
| <span data-ttu-id="f70fa-193">Scatta una foto</span><span class="sxs-lookup"><span data-stu-id="f70fa-193">Take a photo</span></span> | <span data-ttu-id="f70fa-194">Fotocamera</span><span class="sxs-lookup"><span data-stu-id="f70fa-194">Camera</span></span> |
| <span data-ttu-id="f70fa-195">Creare un video</span><span class="sxs-lookup"><span data-stu-id="f70fa-195">Take a video</span></span> | <span data-ttu-id="f70fa-196">Video</span><span class="sxs-lookup"><span data-stu-id="f70fa-196">Video</span></span> |
| <span data-ttu-id="f70fa-197">Visualizzare la visualizzazione visore Portale realtà mista sul desktop</span><span class="sxs-lookup"><span data-stu-id="f70fa-197">Show the headset view in Mixed Reality Portal on your desktop</span></span> | <span data-ttu-id="f70fa-198">Anteprima</span><span class="sxs-lookup"><span data-stu-id="f70fa-198">Preview</span></span> |
| <span data-ttu-id="f70fa-199">Aprire il controllo del volume all'avvio</span><span class="sxs-lookup"><span data-stu-id="f70fa-199">Open the volume control on Start</span></span> | <span data-ttu-id="f70fa-200">Cambiare il volume</span><span class="sxs-lookup"><span data-stu-id="f70fa-200">Change volume</span></span> |
| <span data-ttu-id="f70fa-201">Disattiva audio</span><span class="sxs-lookup"><span data-stu-id="f70fa-201">Mute</span></span> | <span data-ttu-id="f70fa-202">Disattiva audio</span><span class="sxs-lookup"><span data-stu-id="f70fa-202">Mute</span></span> |
| <span data-ttu-id="f70fa-203">Unmute</span><span class="sxs-lookup"><span data-stu-id="f70fa-203">Unmute</span></span> | <span data-ttu-id="f70fa-204">Unmute</span><span class="sxs-lookup"><span data-stu-id="f70fa-204">Unmute</span></span> |
| <span data-ttu-id="f70fa-205">Chiudere il menu Start</span><span class="sxs-lookup"><span data-stu-id="f70fa-205">Close the Start menu</span></span> | <span data-ttu-id="f70fa-206">Chiudere o annullare</span><span class="sxs-lookup"><span data-stu-id="f70fa-206">Close or cancel</span></span> |

## <a name="hey-cortana-commands"></a><span data-ttu-id="f70fa-207">Comandi di Hey Cortana</span><span class="sxs-lookup"><span data-stu-id="f70fa-207">Hey Cortana commands</span></span>

<span data-ttu-id="f70fa-208">Pronunciare "Hey Cortana", quindi usare uno dei comandi seguenti:</span><span class="sxs-lookup"><span data-stu-id="f70fa-208">Say "Hey Cortana,” then use one of the following commands:</span></span>

| <span data-ttu-id="f70fa-209">Per</span><span class="sxs-lookup"><span data-stu-id="f70fa-209">To do this</span></span> | <span data-ttu-id="f70fa-210">Pronunciare questo</span><span class="sxs-lookup"><span data-stu-id="f70fa-210">Say this</span></span> |
| --- | --- |
| <span data-ttu-id="f70fa-211">Scoprire cosa si può dire a Cortana</span><span class="sxs-lookup"><span data-stu-id="f70fa-211">Find out what you can say to Cortana</span></span> | <span data-ttu-id="f70fa-212">What can I say?</span><span class="sxs-lookup"><span data-stu-id="f70fa-212">What can I say?</span></span> |
| <span data-ttu-id="f70fa-213">Aumentare/ridurre il volume</span><span class="sxs-lookup"><span data-stu-id="f70fa-213">Increase/decrease volume</span></span> | <span data-ttu-id="f70fa-214">Attivare/disattivare il volume</span><span class="sxs-lookup"><span data-stu-id="f70fa-214">Turn the volume up/down</span></span> |
| <span data-ttu-id="f70fa-215">Disattivare/riattivare l'audio</span><span class="sxs-lookup"><span data-stu-id="f70fa-215">Mute/unmute</span></span> | <span data-ttu-id="f70fa-216">Disattivare/riattivare l'audio</span><span class="sxs-lookup"><span data-stu-id="f70fa-216">Mute/unmute</span></span> |
| <span data-ttu-id="f70fa-217">Avviare un'app</span><span class="sxs-lookup"><span data-stu-id="f70fa-217">Start an app</span></span> | <span data-ttu-id="f70fa-218">Avvio [nome app]</span><span class="sxs-lookup"><span data-stu-id="f70fa-218">Launch [app name]</span></span> |
| <span data-ttu-id="f70fa-219">Aprire un sito Web in Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="f70fa-219">Open a website in Microsoft Edge</span></span> | <span data-ttu-id="f70fa-220">Aprire [nome del sito Web] (ad esempio, "open bing.com")</span><span class="sxs-lookup"><span data-stu-id="f70fa-220">Open [website name] (for example, “open bing.com”)</span></span> |
| <span data-ttu-id="f70fa-221">Scatta una foto</span><span class="sxs-lookup"><span data-stu-id="f70fa-221">Take a photo</span></span> | <span data-ttu-id="f70fa-222">Immagine</span><span class="sxs-lookup"><span data-stu-id="f70fa-222">Take picture</span></span> |
| <span data-ttu-id="f70fa-223">Avviare la registrazione di un video</span><span class="sxs-lookup"><span data-stu-id="f70fa-223">Start recording a video</span></span> | <span data-ttu-id="f70fa-224">Avvia registrazione</span><span class="sxs-lookup"><span data-stu-id="f70fa-224">Start recording</span></span> |
| <span data-ttu-id="f70fa-225">Interrompere la registrazione di un video</span><span class="sxs-lookup"><span data-stu-id="f70fa-225">Stop recording a video</span></span> | <span data-ttu-id="f70fa-226">Arrestare registrazione</span><span class="sxs-lookup"><span data-stu-id="f70fa-226">Stop recording</span></span> |
| <span data-ttu-id="f70fa-227">Visualizzare l'ora</span><span class="sxs-lookup"><span data-stu-id="f70fa-227">Show the time</span></span> | <span data-ttu-id="f70fa-228">Che ora è?</span><span class="sxs-lookup"><span data-stu-id="f70fa-228">What time is it?</span></span> |
| <span data-ttu-id="f70fa-229">Aprire il menu Start</span><span class="sxs-lookup"><span data-stu-id="f70fa-229">Open the Start menu</span></span> | <span data-ttu-id="f70fa-230">Aprire menu Start</span><span class="sxs-lookup"><span data-stu-id="f70fa-230">Open Start menu</span></span> |
| <span data-ttu-id="f70fa-231">Impostare un timer</span><span class="sxs-lookup"><span data-stu-id="f70fa-231">Set a timer</span></span> | <span data-ttu-id="f70fa-232">Impostare un timer</span><span class="sxs-lookup"><span data-stu-id="f70fa-232">Set a timer</span></span> |
| <span data-ttu-id="f70fa-233">Impostare un promemoria</span><span class="sxs-lookup"><span data-stu-id="f70fa-233">Set a reminder</span></span> | <span data-ttu-id="f70fa-234">Impostare un promemoria</span><span class="sxs-lookup"><span data-stu-id="f70fa-234">Set a reminder</span></span> |

> [!NOTE]
> * <span data-ttu-id="f70fa-235">Cortana non è disponibile in tutte le aree e lingue.</span><span class="sxs-lookup"><span data-stu-id="f70fa-235">Cortana is not available in all regions and languages.</span></span> <span data-ttu-id="f70fa-236">[Altre informazioni](https://support.microsoft.com/help/4026948)</span><span class="sxs-lookup"><span data-stu-id="f70fa-236">[Learn more](https://support.microsoft.com/help/4026948).</span></span>
> * <span data-ttu-id="f70fa-237">Se Cortana non risponde a "Hey Cortana", selezionare Impostazioni > **Privacy > Voce** e attivare il riconoscimento vocale online.</span><span class="sxs-lookup"><span data-stu-id="f70fa-237">If Cortana isn't responding to "Hey Cortana," select **Settings > Privacy > Speech** and make Online speech recognition is turned on.</span></span>
> * <span data-ttu-id="f70fa-238">Se si disattiva Cortana, i comandi vocali "Hey Cortana" non saranno disponibili, ma sarà comunque possibile usare altri comandi,ad esempio "select" e "teleport"</span><span class="sxs-lookup"><span data-stu-id="f70fa-238">If you turn Cortana off, "Hey Cortana" voice commands won't be available, but you'll still be able to use other commands (like "select" and "teleport")</span></span>

## <a name="keyboard-dictation"></a><span data-ttu-id="f70fa-239">Dettatura da tastiera</span><span class="sxs-lookup"><span data-stu-id="f70fa-239">Keyboard dictation</span></span>

<span data-ttu-id="f70fa-240">Passare alla modalità dettatura ogni volta che la tastiera è attiva per un modo semplice di digitare.</span><span class="sxs-lookup"><span data-stu-id="f70fa-240">Switch to dictation mode anytime the keyboard is active for an easy way to type.</span></span> <span data-ttu-id="f70fa-241">Selezionare il microfono sulla tastiera o semplicemente pronunciare "inizia a dettare" per iniziare.</span><span class="sxs-lookup"><span data-stu-id="f70fa-241">Select microphone  on the keyboard—or just say “start dictating”—to get started.</span></span>

> [!NOTE]
> <span data-ttu-id="f70fa-242">La tastiera di realtà mista è disponibile solo in inglese, ma è possibile usare la dettatura in una delle lingue [Windows Mixed Reality supportate.](other-questions.md#what-languages-are-supported-in-windows-mixed-reality)</span><span class="sxs-lookup"><span data-stu-id="f70fa-242">The mixed reality keyboard is only available in English, but you can use dictation in any of the supported [Windows Mixed Reality languages](other-questions.md#what-languages-are-supported-in-windows-mixed-reality).</span></span>

### <a name="keyboard-dictation-commands"></a><span data-ttu-id="f70fa-243">Comandi di dettatura da tastiera</span><span class="sxs-lookup"><span data-stu-id="f70fa-243">Keyboard dictation commands</span></span>

| <span data-ttu-id="f70fa-244">Per</span><span class="sxs-lookup"><span data-stu-id="f70fa-244">To do this</span></span> | <span data-ttu-id="f70fa-245">Pronunciare questo</span><span class="sxs-lookup"><span data-stu-id="f70fa-245">Say this</span></span> |
| --- | --- |
| <span data-ttu-id="f70fa-246">Chiudere la tastiera</span><span class="sxs-lookup"><span data-stu-id="f70fa-246">Close the keyboard</span></span> | <span data-ttu-id="f70fa-247">Chiudi</span><span class="sxs-lookup"><span data-stu-id="f70fa-247">Close</span></span> |
| <span data-ttu-id="f70fa-248">Avviare la dettatura</span><span class="sxs-lookup"><span data-stu-id="f70fa-248">Start dictation</span></span> | <span data-ttu-id="f70fa-249">Iniziare a dettare</span><span class="sxs-lookup"><span data-stu-id="f70fa-249">Start dictating</span></span> |
| <span data-ttu-id="f70fa-250">Interrompi dettatura</span><span class="sxs-lookup"><span data-stu-id="f70fa-250">Stop dictation</span></span> | <span data-ttu-id="f70fa-251">Interrompi dettatura</span><span class="sxs-lookup"><span data-stu-id="f70fa-251">Stop dictating</span></span> |
| <span data-ttu-id="f70fa-252">Eliminare i dati che sono stati dettati</span><span class="sxs-lookup"><span data-stu-id="f70fa-252">Delete what you've dictated</span></span> | <span data-ttu-id="f70fa-253">Elimina</span><span class="sxs-lookup"><span data-stu-id="f70fa-253">Delete that</span></span> |
| <span data-ttu-id="f70fa-254">Selezionare tutti gli elementi nella casella di dettatura</span><span class="sxs-lookup"><span data-stu-id="f70fa-254">Select everything in the dictation box</span></span> | <span data-ttu-id="f70fa-255">Seleziona tutto</span><span class="sxs-lookup"><span data-stu-id="f70fa-255">Select all</span></span> |

### <a name="punctuation"></a><span data-ttu-id="f70fa-256">Punteggiatura</span><span class="sxs-lookup"><span data-stu-id="f70fa-256">Punctuation</span></span>

<span data-ttu-id="f70fa-257">È necessario pronunciare i nomi della punteggiatura che si vuole usare.</span><span class="sxs-lookup"><span data-stu-id="f70fa-257">You’ll need to say the names of the punctuation you want to use.</span></span> <span data-ttu-id="f70fa-258">Ad esempio, si potrebbe dire "Hey **comma** what are you up to **question mark**".</span><span class="sxs-lookup"><span data-stu-id="f70fa-258">For instance, you might say "Hey **comma** what are you up to **question mark**."</span></span>

<span data-ttu-id="f70fa-259">Ecco le parole chiave di punteggiatura che è possibile usare:</span><span class="sxs-lookup"><span data-stu-id="f70fa-259">Here are the punctuation keywords you can use:</span></span>

* <span data-ttu-id="f70fa-260">Punto, virgola, punto interrogativo, punto esclamativo/punto esclamativo</span><span class="sxs-lookup"><span data-stu-id="f70fa-260">Period, comma, question mark, exclamation point/exclamation mark</span></span>
* <span data-ttu-id="f70fa-261">Nuova riga/nuovo paragrafo</span><span class="sxs-lookup"><span data-stu-id="f70fa-261">New line/new paragraph</span></span>
* <span data-ttu-id="f70fa-262">Punto e virgola, due punti</span><span class="sxs-lookup"><span data-stu-id="f70fa-262">Semicolon, colon</span></span>
* <span data-ttu-id="f70fa-263">Virgolette aperte, virgolette di chiusura</span><span class="sxs-lookup"><span data-stu-id="f70fa-263">Open quote(s), close quote(s)</span></span>
* <span data-ttu-id="f70fa-264">Hashtag, smiley/smiley face, frowny, winky</span><span class="sxs-lookup"><span data-stu-id="f70fa-264">Hashtag, smiley/smiley face, frowny, winky</span></span>
* <span data-ttu-id="f70fa-265">Dollaro, percentuale</span><span class="sxs-lookup"><span data-stu-id="f70fa-265">Dollar, percent</span></span>

<span data-ttu-id="f70fa-266">In alcuni casi è utile formulare alcune informazioni, ad esempio gli indirizzi di posta elettronica.</span><span class="sxs-lookup"><span data-stu-id="f70fa-266">Sometimes it's helpful to spell out things like email addresses.</span></span> <span data-ttu-id="f70fa-267">Ad esempio, per indicare example@outlook.com , si pronuncia "E X A M P L E at outlook dot-com".</span><span class="sxs-lookup"><span data-stu-id="f70fa-267">For instance, to dictate example@outlook.com, you'd say "E X A M P L E at outlook dot-com."</span></span>

<span data-ttu-id="f70fa-268">Per interrompere la dettatura, selezionare **Fine.**</span><span class="sxs-lookup"><span data-stu-id="f70fa-268">To stop dictating, select **Done**.</span></span>

## <a name="see-also"></a><span data-ttu-id="f70fa-269">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="f70fa-269">See also</span></span>

* [<span data-ttu-id="f70fa-270">Contattare la community</span><span class="sxs-lookup"><span data-stu-id="f70fa-270">Ask the community</span></span>](https://answers.microsoft.com)
* [<span data-ttu-id="f70fa-271">Contattaci per assistenza</span><span class="sxs-lookup"><span data-stu-id="f70fa-271">Contact us for support</span></span>](https://support.microsoft.com/contactus/)

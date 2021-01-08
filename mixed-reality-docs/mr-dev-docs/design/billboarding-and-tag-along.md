---
title: Billboarding e tag-along
description: Informazioni su come usare gli oggetti con il tabellone, che sempre si orientano a far fronte all'utente nelle applicazioni di realtà mista.
author: radicalad
ms.author: adlinv
ms.date: 03/21/2018
ms.topic: article
keywords: Realtà mista di Windows, Billboard, tag-along, cuffie per realtà mista, auricolare di realtà mista di Windows, headset di realtà virtuale, HoloLens, MRTK, Toolkit realtà mista
ms.openlocfilehash: 92caa1bcd325cefecc6d3820b819cecfce6fc09c
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2021
ms.locfileid: "98009612"
---
# <a name="billboarding-and-tag-along"></a><span data-ttu-id="a45c8-104">Billboarding e tag-along</span><span class="sxs-lookup"><span data-stu-id="a45c8-104">Billboarding and tag-along</span></span>

<br>

<img src="images/MRTK_TagAlong.gif" alt="HoloLens perspective of a menu system that always faces the user" width="940px">
<br>

## <a name="what-is-billboarding"></a><span data-ttu-id="a45c8-105">Che cos'è il tabellone?</span><span class="sxs-lookup"><span data-stu-id="a45c8-105">What is billboarding?</span></span>

<span data-ttu-id="a45c8-106">Il tabellone è un concetto di comportamento che può essere applicato a oggetti in realtà mista.</span><span class="sxs-lookup"><span data-stu-id="a45c8-106">Billboarding is a behavioral concept that can be applied to objects in mixed reality.</span></span> <span data-ttu-id="a45c8-107">Gli oggetti con il tabellone sono sempre orientati a fronte dell'utente.</span><span class="sxs-lookup"><span data-stu-id="a45c8-107">Objects with billboarding always orient themselves to face the user.</span></span> <span data-ttu-id="a45c8-108">I sistemi di testo e menu sono casi d'uso comuni, in cui gli oggetti statici inseriti nell'ambiente dell'utente (con blocco globale) sarebbero altrimenti nascosti o illeggibili quando gli utenti si spostano.</span><span class="sxs-lookup"><span data-stu-id="a45c8-108">Text and menu systems are common use cases, where static objects placed in the user's environment (world-locked) would be otherwise obscured or unreadable when users move around.</span></span>

<span data-ttu-id="a45c8-109">Gli oggetti con il tabellone abilitato possono essere ruotati liberamente nell'ambiente dell'utente.</span><span class="sxs-lookup"><span data-stu-id="a45c8-109">Objects with billboarding enabled can rotate freely in the user's environment.</span></span> <span data-ttu-id="a45c8-110">Possono anche essere vincolati a un singolo asse, a seconda delle considerazioni di progettazione.</span><span class="sxs-lookup"><span data-stu-id="a45c8-110">They can also be constrained to a single axis depending on design considerations.</span></span> <span data-ttu-id="a45c8-111">Tenere presente che gli oggetti di cui è stato effettuato il Billboard possono essere ritagliati o occludereti quando vengono posizionati troppo vicini ad altri oggetti o in HoloLens, troppo vicino alle superfici analizzate.</span><span class="sxs-lookup"><span data-stu-id="a45c8-111">Keep in mind, billboarded objects can clip or occlude themselves when placed too close to other objects, or in HoloLens, too close scanned surfaces.</span></span> <span data-ttu-id="a45c8-112">Per evitare questo problema, considerare il footprint totale che un oggetto può produrre quando ruotato sull'asse abilitato per il tabellone.</span><span class="sxs-lookup"><span data-stu-id="a45c8-112">To avoid this, think about the total footprint an object may produce when rotated on the axis enabled for billboarding.</span></span>

<br>

---
## <a name="what-is-a-tag-along"></a><span data-ttu-id="a45c8-113">Che cos'è un tag-along?</span><span class="sxs-lookup"><span data-stu-id="a45c8-113">What is a tag-along?</span></span>

<span data-ttu-id="a45c8-114">Tag-Along è un concetto di comportamento che può essere aggiunto agli ologrammi.</span><span class="sxs-lookup"><span data-stu-id="a45c8-114">Tag-along is a behavioral concept that can be added to holograms.</span></span> <span data-ttu-id="a45c8-115">Un oggetto tag-along tenta di rimanere in un intervallo che consente all'utente di interagire comodamente.</span><span class="sxs-lookup"><span data-stu-id="a45c8-115">A tag-along object attempts to stay in a range that allows the user to interact comfortably.</span></span>

<span data-ttu-id="a45c8-116">![Il pannello HoloLens Pins è un ottimo esempio del comportamento dei tag](images/tagalong-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="a45c8-116">![The HoloLens pins panel is a great example of how tag-along behaves](images/tagalong-1000px.jpg)</span></span><br>
<span data-ttu-id="a45c8-117">*Il menu Start di HoloLens è un ottimo esempio di comportamento di tag-along*</span><span class="sxs-lookup"><span data-stu-id="a45c8-117">*The HoloLens Start menu is a great example of tag-along behavior*</span></span>

<span data-ttu-id="a45c8-118">Gli oggetti tag-along hanno parametri, che possono ottimizzare il modo in cui si comportano.</span><span class="sxs-lookup"><span data-stu-id="a45c8-118">Tag-along objects have parameters, which can fine-tune the way they behave.</span></span> <span data-ttu-id="a45c8-119">Il contenuto può essere all'interno o all'esterno della linea di visione dell'utente mentre l'utente si sposta intorno all'ambiente.</span><span class="sxs-lookup"><span data-stu-id="a45c8-119">Content can be in or out of the user’s line of sight while the user moves around their environment.</span></span> <span data-ttu-id="a45c8-120">Quando si sposta, il contenuto tenta di rimanere all'interno della periferia dell'utente scorrendo verso il bordo della visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="a45c8-120">As you move, the content attempts to stay within the user’s periphery by sliding towards the edge of the view.</span></span> <span data-ttu-id="a45c8-121">Il contenuto potrebbe essere temporaneamente fuori dalla visualizzazione a seconda della velocità di trasferimento dell'utente.</span><span class="sxs-lookup"><span data-stu-id="a45c8-121">The content might be temporarily out of view depending on how quickly the user is moving.</span></span> <span data-ttu-id="a45c8-122">Quando l'utente guarda l'oggetto tag-along, viene visualizzato in modo più completo.</span><span class="sxs-lookup"><span data-stu-id="a45c8-122">When the user gazes towards the tag-along object, it comes more fully into view.</span></span> <span data-ttu-id="a45c8-123">Il contenuto è sempre un "colpo d'occhio" in modo che gli utenti non dimentichino mai la direzione in cui si trova il contenuto.</span><span class="sxs-lookup"><span data-stu-id="a45c8-123">Think of content always being "a glance away" so users never forget what direction their content is in.</span></span>

<span data-ttu-id="a45c8-124">I parametri aggiuntivi possono fare in modo che l'oggetto tag-along si trovi collegato alla testa dell'utente da un elastico.</span><span class="sxs-lookup"><span data-stu-id="a45c8-124">Extra parameters can make the tag-along object feel attached to the user's head by a rubber band.</span></span> <span data-ttu-id="a45c8-125">L'attenuazione dell'accelerazione o della decelerazione dà peso all'oggetto che lo rende più fisicamente presente.</span><span class="sxs-lookup"><span data-stu-id="a45c8-125">Dampening acceleration or deceleration gives weight to the object making it feel more physically present.</span></span> <span data-ttu-id="a45c8-126">Questo comportamento primaverile è un'offerta che consente all'utente di creare un modello mentale accurato del funzionamento dei tag.</span><span class="sxs-lookup"><span data-stu-id="a45c8-126">This spring behavior is an affordance that helps the user build an accurate mental model of how tag-along works.</span></span> <span data-ttu-id="a45c8-127">Audio consente di fornire altre indicazioni quando gli utenti dispongono di oggetti in modalità tag-along.</span><span class="sxs-lookup"><span data-stu-id="a45c8-127">Audio helps provide other cues for when users have objects in tag-along mode.</span></span> <span data-ttu-id="a45c8-128">L'audio deve rafforzare la velocità di spostamento; una rotazione a capo veloce dovrebbe offrire un effetto acustico più evidente, mentre l'esplorazione a una velocità naturale dovrebbe avere effetti audio minimi o non disponibili.</span><span class="sxs-lookup"><span data-stu-id="a45c8-128">Audio should reinforce the speed of movement; a fast head turn should provide a more noticeable sound effect, while walking at a natural speed should have minimal or no audio effects.</span></span>

<span data-ttu-id="a45c8-129">Proprio come il contenuto con blocco principale, gli oggetti tag-along possono rivelarsi opprimenti o nauseanti se si muovono in modo sfrenato o troppo lungo nella visualizzazione dell'utente.</span><span class="sxs-lookup"><span data-stu-id="a45c8-129">Just like truly head-locked content, tag-along objects can prove overwhelming or nauseating if they move wildly or spring too much in the user’s view.</span></span> <span data-ttu-id="a45c8-130">Quando un utente si trova, si interrompe rapidamente, i loro sensi indicano che sono stati arrestati.</span><span class="sxs-lookup"><span data-stu-id="a45c8-130">As a user looks around, then quickly stops, their senses tell them they've stopped.</span></span> <span data-ttu-id="a45c8-131">Il loro saldo informa che la loro testa è stata interrotta e la loro visione vede il mondo che smette di diventare.</span><span class="sxs-lookup"><span data-stu-id="a45c8-131">Their balance informs them that their head has stopped turning and their vision sees the world stop turning.</span></span> <span data-ttu-id="a45c8-132">Tuttavia, se il tag-along continua a essere spostato quando l'utente si arresta, può confonderne i sensi.</span><span class="sxs-lookup"><span data-stu-id="a45c8-132">However, if tag-along keeps on moving when the user has stopped, it may confuse their senses.</span></span>

<br>

---

## <a name="billboarding-and-tag-along-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="a45c8-133">Billboard e tag-along in MRTK (Mixed Reality Toolkit) per Unity</span><span class="sxs-lookup"><span data-stu-id="a45c8-133">Billboarding and Tag-along in MRTK (Mixed Reality Toolkit) for Unity</span></span>
<span data-ttu-id="a45c8-134">**[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** fornisce script per il comportamento di Billboard e tag-along.</span><span class="sxs-lookup"><span data-stu-id="a45c8-134">**[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** provides scripts for the Billboarding and tag-along behavior.</span></span> <span data-ttu-id="a45c8-135">Assegnare lo script Billboard.cs a qualsiasi oggetto per aggiungere il comportamento di Billboard e fare in modo che l'oggetto faccia sempre fronte all'utente.</span><span class="sxs-lookup"><span data-stu-id="a45c8-135">Assign the Billboard.cs script onto any object to add billboarding behavior and make the object always face you.</span></span> <span data-ttu-id="a45c8-136">Per aggiungere un comportamento tag-along, usare lo script RadialView.cs.</span><span class="sxs-lookup"><span data-stu-id="a45c8-136">To add tag-along behavior, use the RadialView.cs script.</span></span> <span data-ttu-id="a45c8-137">È possibile modificare varie opzioni, ad esempio lerping tempo, distanza e grado.</span><span class="sxs-lookup"><span data-stu-id="a45c8-137">You can adjust various options such as lerping time, distance, and degree.</span></span>

* [<span data-ttu-id="a45c8-138">MRTK-Risolutore viste radiali</span><span class="sxs-lookup"><span data-stu-id="a45c8-138">MRTK - Radial View Solver</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html#radialview)
* [<span data-ttu-id="a45c8-139">MRTK-script Billboard</span><span class="sxs-lookup"><span data-stu-id="a45c8-139">MRTK - Billboard script</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Scripts/Utilities/Billboard.cs)


<br>

---

## <a name="see-also"></a><span data-ttu-id="a45c8-140">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="a45c8-140">See also</span></span>

* [<span data-ttu-id="a45c8-141">Cursori</span><span class="sxs-lookup"><span data-stu-id="a45c8-141">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="a45c8-142">Raggio della mano</span><span class="sxs-lookup"><span data-stu-id="a45c8-142">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="a45c8-143">Button</span><span class="sxs-lookup"><span data-stu-id="a45c8-143">Button</span></span>](button.md)
* [<span data-ttu-id="a45c8-144">Oggetto che supporta interazioni</span><span class="sxs-lookup"><span data-stu-id="a45c8-144">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="a45c8-145">Rettangolo di selezione e barra dell'app</span><span class="sxs-lookup"><span data-stu-id="a45c8-145">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="a45c8-146">Manipolazione</span><span class="sxs-lookup"><span data-stu-id="a45c8-146">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="a45c8-147">Menu a mano</span><span class="sxs-lookup"><span data-stu-id="a45c8-147">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="a45c8-148">Menu adiacente</span><span class="sxs-lookup"><span data-stu-id="a45c8-148">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="a45c8-149">Raccolta di oggetti</span><span class="sxs-lookup"><span data-stu-id="a45c8-149">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="a45c8-150">Comando vocale</span><span class="sxs-lookup"><span data-stu-id="a45c8-150">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="a45c8-151">Tastiera</span><span class="sxs-lookup"><span data-stu-id="a45c8-151">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="a45c8-152">Descrizione comando</span><span class="sxs-lookup"><span data-stu-id="a45c8-152">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="a45c8-153">Slate</span><span class="sxs-lookup"><span data-stu-id="a45c8-153">Slate</span></span>](slate.md)
* [<span data-ttu-id="a45c8-154">Dispositivo di scorrimento</span><span class="sxs-lookup"><span data-stu-id="a45c8-154">Slider</span></span>](slider.md)
* [<span data-ttu-id="a45c8-155">Shader</span><span class="sxs-lookup"><span data-stu-id="a45c8-155">Shader</span></span>](shader.md)
* [<span data-ttu-id="a45c8-156">Billboarding e tag-along</span><span class="sxs-lookup"><span data-stu-id="a45c8-156">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="a45c8-157">Visualizzazione dello stato</span><span class="sxs-lookup"><span data-stu-id="a45c8-157">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="a45c8-158">Magnetismo di superficie</span><span class="sxs-lookup"><span data-stu-id="a45c8-158">Surface magnetism</span></span>](surface-magnetism.md)

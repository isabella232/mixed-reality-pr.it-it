---
title: Billboarding e tag-along
description: Informazioni su come usare gli oggetti con la creazione di oggetti, che si orientano sempre per affrontare l'utente in applicazioni di realtà mista.
author: radicalad
ms.author: adlinv
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, gioco di tag, tag, visore VR di realtà mista, visore VR di realtà mista windows, visore VR di realtà virtuale, HoloLens, MRTK, Mixed Reality Toolkit
ms.openlocfilehash: 0bd1ac2168284d714240c6775468a61ed3e665b8
ms.sourcegitcommit: 9ae76b339968f035c703d9c1fe57ddecb33198e3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/27/2021
ms.locfileid: "110600340"
---
# <a name="billboarding-and-tag-along"></a><span data-ttu-id="1933e-104">Billboarding e tag-along</span><span class="sxs-lookup"><span data-stu-id="1933e-104">Billboarding and tag-along</span></span>

<br>

<img src="images/MRTK_TagAlong.gif" alt="HoloLens perspective of a menu system that always faces the user" width="940px">
<br>

## <a name="what-is-billboarding"></a><span data-ttu-id="1933e-105">Che cos'è la distribuzione in più?</span><span class="sxs-lookup"><span data-stu-id="1933e-105">What is billboarding?</span></span>

<span data-ttu-id="1933e-106">L'organizzazione è un concetto comportamentale che può essere applicato agli oggetti nella realtà mista.</span><span class="sxs-lookup"><span data-stu-id="1933e-106">Billboarding is a behavioral concept that can be applied to objects in mixed reality.</span></span> <span data-ttu-id="1933e-107">Gli oggetti con l'eserezione si orientano sempre verso l'utente.</span><span class="sxs-lookup"><span data-stu-id="1933e-107">Objects with billboarding always orient themselves to face the user.</span></span> <span data-ttu-id="1933e-108">I sistemi di testo e menu sono casi d'uso comuni, in cui gli oggetti statici inseriti nell'ambiente dell'utente (bloccati nel mondo) verrebbero altrimenti nascosti o illeggibili quando gli utenti si spostano.</span><span class="sxs-lookup"><span data-stu-id="1933e-108">Text and menu systems are common use cases, where static objects placed in the user's environment (world-locked) would be otherwise obscured or unreadable when users move around.</span></span>

<span data-ttu-id="1933e-109">Gli oggetti con l'a capo automatico abilitato possono ruotare liberamente nell'ambiente dell'utente.</span><span class="sxs-lookup"><span data-stu-id="1933e-109">Objects with billboarding enabled can rotate freely in the user's environment.</span></span> <span data-ttu-id="1933e-110">Possono anche essere vincolati a un singolo asse a seconda delle considerazioni di progettazione.</span><span class="sxs-lookup"><span data-stu-id="1933e-110">They can also be constrained to a single axis depending on design considerations.</span></span> <span data-ttu-id="1933e-111">Tenere presente che gli oggetti con i recinti possono ritagliarsi o occludere se posizionati troppo vicini ad altri oggetti o in HoloLens, superfici analizzate troppo vicine.</span><span class="sxs-lookup"><span data-stu-id="1933e-111">Keep in mind, billboarded objects can clip or occlude themselves when placed too close to other objects, or in HoloLens, too close scanned surfaces.</span></span> <span data-ttu-id="1933e-112">Per evitare questo problema, pensare al footprint totale che un oggetto può produrre quando viene ruotato sull'asse abilitato per la rotazione.</span><span class="sxs-lookup"><span data-stu-id="1933e-112">To avoid this, think about the total footprint an object may produce when rotated on the axis enabled for billboarding.</span></span>

<br>

---
## <a name="what-is-a-tag-along"></a><span data-ttu-id="1933e-113">Che cos'è un tag-along?</span><span class="sxs-lookup"><span data-stu-id="1933e-113">What is a tag-along?</span></span>

<span data-ttu-id="1933e-114">Il tag-along è un concetto comportamentale che può essere aggiunto agli ologrammi.</span><span class="sxs-lookup"><span data-stu-id="1933e-114">Tag-along is a behavioral concept that can be added to holograms.</span></span> <span data-ttu-id="1933e-115">Un oggetto tag-along tenta di rimanere in un intervallo che consente all'utente di interagire comodamente.</span><span class="sxs-lookup"><span data-stu-id="1933e-115">A tag-along object attempts to stay in a range that allows the user to interact comfortably.</span></span>

<span data-ttu-id="1933e-116">![Il pannello dei pin di HoloLens è un ottimo esempio del comportamento dell'aggiunta di tag](images/tagalong-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="1933e-116">![The HoloLens pins panel is a great example of how tag-along behaves](images/tagalong-1000px.jpg)</span></span><br>
<span data-ttu-id="1933e-117">*L'menu Start HoloLens è un ottimo esempio di comportamento basato su tag*</span><span class="sxs-lookup"><span data-stu-id="1933e-117">*The HoloLens Start menu is a great example of tag-along behavior*</span></span>

<span data-ttu-id="1933e-118">Gli oggetti con tag hanno parametri che possono ottimizzare il comportamento.</span><span class="sxs-lookup"><span data-stu-id="1933e-118">Tag-along objects have parameters, which can fine-tune the way they behave.</span></span> <span data-ttu-id="1933e-119">Il contenuto può essere in movimento all'esterno o all'esterno della linea di vista dell'utente mentre l'utente si sposta all'esterno dell'ambiente.</span><span class="sxs-lookup"><span data-stu-id="1933e-119">Content can be in or out of the user’s line of sight while the user moves around their environment.</span></span> <span data-ttu-id="1933e-120">Mentre ci si sposta, il contenuto tenta di rimanere all'interno della periferia dell'utente scorrendo verso il bordo della visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="1933e-120">As you move, the content attempts to stay within the user’s periphery by sliding towards the edge of the view.</span></span> <span data-ttu-id="1933e-121">Il contenuto potrebbe essere temporaneamente fuori visualizzazione a seconda della velocità di spostamento dell'utente.</span><span class="sxs-lookup"><span data-stu-id="1933e-121">The content might be temporarily out of view depending on how quickly the user is moving.</span></span> <span data-ttu-id="1933e-122">Quando l'utente guarda verso l'oggetto tag-along, viene visualizzato in modo più completo.</span><span class="sxs-lookup"><span data-stu-id="1933e-122">When the user gazes towards the tag-along object, it comes more fully into view.</span></span> <span data-ttu-id="1933e-123">Si pensi a un contenuto sempre "a colpo d'occhio", in modo che gli utenti non dimentichino mai la direzione in cui si trova il contenuto.</span><span class="sxs-lookup"><span data-stu-id="1933e-123">Think of content always being "a glance away" so users never forget what direction their content is in.</span></span>

<span data-ttu-id="1933e-124">Parametri aggiuntivi possono fare in modo che l'oggetto lungo il tag sia collegato alla testa dell'utente da una banda di gomma.</span><span class="sxs-lookup"><span data-stu-id="1933e-124">Extra parameters can make the tag-along object feel attached to the user's head by a rubber band.</span></span> <span data-ttu-id="1933e-125">La riduzione dell'accelerazione o della decelerazione dà peso all'oggetto rendendolo più fisicamente presente.</span><span class="sxs-lookup"><span data-stu-id="1933e-125">Dampening acceleration or deceleration gives weight to the object making it feel more physically present.</span></span> <span data-ttu-id="1933e-126">Questo comportamento di spring è un affordance che consente all'utente di creare un modello psichiale accurato del funzionamento del tag-along.</span><span class="sxs-lookup"><span data-stu-id="1933e-126">This spring behavior is an affordance that helps the user build an accurate mental model of how tag-along works.</span></span> <span data-ttu-id="1933e-127">L'audio consente di fornire altri segnali quando gli utenti hanno oggetti in modalità tag-along.</span><span class="sxs-lookup"><span data-stu-id="1933e-127">Audio helps provide other cues for when users have objects in tag-along mode.</span></span> <span data-ttu-id="1933e-128">L'audio deve rafforzare la velocità di spostamento; Un turno rapido della testa dovrebbe fornire un effetto sonoro più evidente, mentre l'esecuzione a una velocità naturale dovrebbe avere effetti audio minimi o nessun effetto.</span><span class="sxs-lookup"><span data-stu-id="1933e-128">Audio should reinforce the speed of movement; a fast head turn should provide a more noticeable sound effect, while walking at a natural speed should have minimal or no audio effects.</span></span>

<span data-ttu-id="1933e-129">Proprio come il contenuto effettivamente bloccato con la testa, gli oggetti tag-along possono risultare travolgenti o inaspriti se si spostano in modo severo o sono troppo grandi nella visualizzazione dell'utente.</span><span class="sxs-lookup"><span data-stu-id="1933e-129">Just like truly head-locked content, tag-along objects can prove overwhelming or nauseating if they move wildly or spring too much in the user’s view.</span></span> <span data-ttu-id="1933e-130">Quando un utente si guarda attorno, si arresta rapidamente e il suo senso indica di essersi arrestato.</span><span class="sxs-lookup"><span data-stu-id="1933e-130">As a user looks around, then quickly stops, their senses tell them they've stopped.</span></span> <span data-ttu-id="1933e-131">Il loro equilibrio informa che la testa ha smesso di ruotare e che la loro visione vede il mondo smettere di ruotare.</span><span class="sxs-lookup"><span data-stu-id="1933e-131">Their balance informs them that their head has stopped turning and their vision sees the world stop turning.</span></span> <span data-ttu-id="1933e-132">Tuttavia, se il tag-along continua a spostarsi quando l'utente si è arrestato, potrebbe confondere i propri significati.</span><span class="sxs-lookup"><span data-stu-id="1933e-132">However, if tag-along keeps on moving when the user has stopped, it may confuse their senses.</span></span>

<br>

---

## <a name="billboarding-and-tag-along-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="1933e-133">Unione e tag-along in MRTK (Mixed Reality Toolkit) per Unity</span><span class="sxs-lookup"><span data-stu-id="1933e-133">Billboarding and Tag-along in MRTK (Mixed Reality Toolkit) for Unity</span></span>
<span data-ttu-id="1933e-134">**[MRTK fornisce](https://github.com/Microsoft/MixedRealityToolkit-Unity)** script per il comportamento di etichettatura e tag.</span><span class="sxs-lookup"><span data-stu-id="1933e-134">**[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** provides scripts for the Billboarding and tag-along behavior.</span></span> <span data-ttu-id="1933e-135">Assegnare lo script Manifesto.cs a qualsiasi oggetto per aggiungere un comportamento di controllo e fare in modo che l'oggetto si faccia sempre viso.</span><span class="sxs-lookup"><span data-stu-id="1933e-135">Assign the Billboard.cs script onto any object to add billboarding behavior and make the object always face you.</span></span> <span data-ttu-id="1933e-136">Per aggiungere un comportamento basato su tag, usare lo script RadialView.cs.</span><span class="sxs-lookup"><span data-stu-id="1933e-136">To add tag-along behavior, use the RadialView.cs script.</span></span> <span data-ttu-id="1933e-137">È possibile modificare varie opzioni, ad esempio il tempo di lerping, la distanza e il grado.</span><span class="sxs-lookup"><span data-stu-id="1933e-137">You can adjust various options such as lerping time, distance, and degree.</span></span>

* [<span data-ttu-id="1933e-138">MRTK - Risolutore di vista radiale</span><span class="sxs-lookup"><span data-stu-id="1933e-138">MRTK - Radial View Solver</span></span>](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/solvers/solver#radialview)
* [<span data-ttu-id="1933e-139">MRTK - Script di controllo</span><span class="sxs-lookup"><span data-stu-id="1933e-139">MRTK - Billboard script</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Scripts/Utilities/Billboard.cs)


<br>

---

## <a name="see-also"></a><span data-ttu-id="1933e-140">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="1933e-140">See also</span></span>

* [<span data-ttu-id="1933e-141">Cursori</span><span class="sxs-lookup"><span data-stu-id="1933e-141">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="1933e-142">Raggio della mano</span><span class="sxs-lookup"><span data-stu-id="1933e-142">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="1933e-143">Button</span><span class="sxs-lookup"><span data-stu-id="1933e-143">Button</span></span>](button.md)
* [<span data-ttu-id="1933e-144">Oggetto che supporta interazioni</span><span class="sxs-lookup"><span data-stu-id="1933e-144">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="1933e-145">Rettangolo di selezione e barra dell'app</span><span class="sxs-lookup"><span data-stu-id="1933e-145">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="1933e-146">Manipolazione</span><span class="sxs-lookup"><span data-stu-id="1933e-146">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="1933e-147">Menu a mano</span><span class="sxs-lookup"><span data-stu-id="1933e-147">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="1933e-148">Menu adiacente</span><span class="sxs-lookup"><span data-stu-id="1933e-148">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="1933e-149">Raccolta di oggetti</span><span class="sxs-lookup"><span data-stu-id="1933e-149">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="1933e-150">Comando vocale</span><span class="sxs-lookup"><span data-stu-id="1933e-150">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="1933e-151">Tastiera</span><span class="sxs-lookup"><span data-stu-id="1933e-151">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="1933e-152">Descrizione comando</span><span class="sxs-lookup"><span data-stu-id="1933e-152">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="1933e-153">Slate</span><span class="sxs-lookup"><span data-stu-id="1933e-153">Slate</span></span>](slate.md)
* [<span data-ttu-id="1933e-154">Dispositivo di scorrimento</span><span class="sxs-lookup"><span data-stu-id="1933e-154">Slider</span></span>](slider.md)
* [<span data-ttu-id="1933e-155">Shader</span><span class="sxs-lookup"><span data-stu-id="1933e-155">Shader</span></span>](shader.md)
* [<span data-ttu-id="1933e-156">Billboarding e tag-along</span><span class="sxs-lookup"><span data-stu-id="1933e-156">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="1933e-157">Visualizzazione dello stato</span><span class="sxs-lookup"><span data-stu-id="1933e-157">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="1933e-158">Magnetismo di superficie</span><span class="sxs-lookup"><span data-stu-id="1933e-158">Surface magnetism</span></span>](surface-magnetism.md)
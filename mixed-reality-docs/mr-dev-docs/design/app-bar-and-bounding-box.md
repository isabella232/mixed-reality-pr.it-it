---
title: Rettangolo di selezione e barra dell'app
description: La barra dell'app è un menu a livello di oggetto contenente una serie di pulsanti visualizzati sul bordo inferiore dei limiti di un ologramma.
author: radicalad
ms.author: adlinv
ms.date: 06/07/2019
ms.topic: article
keywords: Windows Mixed Reality, barra dell'app, rettangolo di selezione, visore per realtà mista, visore windows mixed reality, visore per realtà virtuale, HoloLens, MRTK, Mixed Reality Toolkit
ms.openlocfilehash: 5c437b303ec5462179a1ddf43687aa1653419b08
ms.sourcegitcommit: c65759b8d6465b6b13925cacab5af74443f7e6bd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/15/2021
ms.locfileid: "112110090"
---
# <a name="bounding-box-and-app-bar"></a><span data-ttu-id="a15dc-104">Rettangolo di selezione e barra dell'app</span><span class="sxs-lookup"><span data-stu-id="a15dc-104">Bounding box and App bar</span></span>
<span data-ttu-id="a15dc-105">![Il delimitazione è l'interfaccia standard per la manipolazione degli oggetti in realtà mista.](images/UX_Hero_BoundingBox.jpg)</span><span class="sxs-lookup"><span data-stu-id="a15dc-105">![Bounding is the standard interface for object manipulation in Mixed Reality.](images/UX_Hero_BoundingBox.jpg)</span></span><br>
<br>

## <a name="what-is-the-bounding-box"></a><span data-ttu-id="a15dc-106">Che cos'è il rettangolo di selezione?</span><span class="sxs-lookup"><span data-stu-id="a15dc-106">What is the Bounding box?</span></span>

<span data-ttu-id="a15dc-107">Il delimitazione è l'interfaccia standard per la manipolazione degli oggetti in realtà mista.</span><span class="sxs-lookup"><span data-stu-id="a15dc-107">Bounding is the standard interface for object manipulation in Mixed Reality.</span></span> <span data-ttu-id="a15dc-108">Questa funzionalità fornisce all'utente un segnale visivo che indica che l'oggetto è attualmente regolabile.</span><span class="sxs-lookup"><span data-stu-id="a15dc-108">This feature provides the user with a visual cue that the object is currently adjustable.</span></span> <span data-ttu-id="a15dc-109">Al HoloLens 2, il rettangolo di selezione funziona con la manipolazione diretta della mano e risponde alla prossimità del dito dell'utente.</span><span class="sxs-lookup"><span data-stu-id="a15dc-109">On HoloLens 2, the bounding box works with direct hand manipulation and responds to the user's finger's proximity.</span></span> <span data-ttu-id="a15dc-110">Mostra un feedback visivo per aiutare l'utente a percepire la distanza dall'oggetto.</span><span class="sxs-lookup"><span data-stu-id="a15dc-110">It shows visual feedback to help the user perceive the distance from the object.</span></span>

:::row:::
    :::column:::
        ### <a name="scaling-an-objectbr"></a><span data-ttu-id="a15dc-111">Ridimensionamento di un oggetto</span><span class="sxs-lookup"><span data-stu-id="a15dc-111">Scaling an object</span></span><br>
        <span data-ttu-id="a15dc-112">Gli angoli del rettangolo di selezione indicano all'utente che l'oggetto può essere ridimensionato.</span><span class="sxs-lookup"><span data-stu-id="a15dc-112">The corners of the bounding box tell the user that the object can scale.</span></span> <span data-ttu-id="a15dc-113">Gli handle seguono un modello ampiamente noto per la regolazione della scala.</span><span class="sxs-lookup"><span data-stu-id="a15dc-113">The handles follow a widely understood pattern for adjusting scale.</span></span> <span data-ttu-id="a15dc-114">Questo segnale visivo mostra agli utenti l'area totale dell'oggetto, anche se non è visibile all'esterno di una modalità di regolazione.</span><span class="sxs-lookup"><span data-stu-id="a15dc-114">This visual cue shows users the total area of the object – even if it’s not visible outside of an adjustment mode.</span></span> <span data-ttu-id="a15dc-115">Senza questa funzionalità, un oggetto agganciato a un altro oggetto o superficie può sembrare comportarsi come se ci fosse spazio intorno a esso che non dovrebbe essere presente.</span><span class="sxs-lookup"><span data-stu-id="a15dc-115">Without this feature, an object snapped to another object or surface may appear to behave like there was space around it that shouldn’t be there.</span></span><br>
        <br>
        <span data-ttu-id="a15dc-116">*Ciclo video: Ridimensionamento di un oggetto tramite rettangolo di selezione*</span><span class="sxs-lookup"><span data-stu-id="a15dc-116">*Video loop: Scaling an object via bounding box*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="a15dc-117">![space](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="a15dc-117">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="a15dc-118">![Punto di visualizzazione di HoloLens per ridimensionare un oggetto tramite rettangolo di selezione](images/HoloLens2_BoundingBox.gif)</span><span class="sxs-lookup"><span data-stu-id="a15dc-118">![HoloLens point-of-view of scaling an object via bounding box](images/HoloLens2_BoundingBox.gif)</span></span><br>
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        ### <a name="rotating-an-objectbr"></a><span data-ttu-id="a15dc-119">Rotazione di un oggetto</span><span class="sxs-lookup"><span data-stu-id="a15dc-119">Rotating an object</span></span><br>
        <span data-ttu-id="a15dc-120">Gli affordance rettangolari verticali sui bordi del rettangolo di selezione sono indicatori di rotazione.</span><span class="sxs-lookup"><span data-stu-id="a15dc-120">The vertical rectangular affordances on the edges of the bounding box are rotation indicators.</span></span> <span data-ttu-id="a15dc-121">In questo modo, l'utente può regolare in modo più fine gli ologrammi posizionati.</span><span class="sxs-lookup"><span data-stu-id="a15dc-121">This gives the user more fine adjustment over their placed holograms.</span></span> <span data-ttu-id="a15dc-122">Non solo possono regolare e ridimensionare, ma anche ruotare.</span><span class="sxs-lookup"><span data-stu-id="a15dc-122">Not only can they adjust and scale, but now rotate as well.</span></span><br>
        <br>
        <span data-ttu-id="a15dc-123">*Ciclo video: Rotazione di un oggetto tramite rettangolo di selezione*</span><span class="sxs-lookup"><span data-stu-id="a15dc-123">*Video loop: Rotating an object via bounding box*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="a15dc-124">![space](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="a15dc-124">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="a15dc-125">![Punto di visualizzazione di HoloLens per la rotazione di un oggetto tramite rettangolo di selezione](images/HoloLens2_BoundingBox_Rotate.gif)</span><span class="sxs-lookup"><span data-stu-id="a15dc-125">![HoloLens point-of-view of rotating an object via bounding box](images/HoloLens2_BoundingBox_Rotate.gif)</span></span><br>
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        ### <a name="visual-feedback-on-hand-proximity-on-hololens-2br"></a><span data-ttu-id="a15dc-126">Feedback visivo sulla prossimità della mano HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="a15dc-126">Visual feedback on hand proximity on HoloLens 2</span></span><br>
        <span data-ttu-id="a15dc-127">In HoloLens 2, c'è un ulteriore segnale visivo, che può aiutare la percezione della profondità dell'utente.</span><span class="sxs-lookup"><span data-stu-id="a15dc-127">On HoloLens 2, there's an extra visual cue, which can help the user's perception of depth.</span></span> <span data-ttu-id="a15dc-128">Un anello vicino alla punta del dito viene visualizzato e ridimensionato man mano che la punta del dito si avvicina all'oggetto.</span><span class="sxs-lookup"><span data-stu-id="a15dc-128">A ring near their fingertip shows up and scales down as the fingertip gets closer to the object.</span></span> <span data-ttu-id="a15dc-129">L'anello converge infine in un punto quando viene raggiunto lo stato premuto.</span><span class="sxs-lookup"><span data-stu-id="a15dc-129">The ring eventually converges into a dot when the pressed state is reached.</span></span> <span data-ttu-id="a15dc-130">Questo affordance visivo consente all'utente di comprendere la distanza dall'oggetto.</span><span class="sxs-lookup"><span data-stu-id="a15dc-130">This visual affordance helps the user understand how far they are from the object.</span></span><br>
        <br>
        <span data-ttu-id="a15dc-131">*Ciclo video: esempio di feedback visivo in base alla prossimità a un rettangolo di selezione*</span><span class="sxs-lookup"><span data-stu-id="a15dc-131">*Video loop: Example of visual feedback based on proximity to a bounding box*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="a15dc-132">![space](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="a15dc-132">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="a15dc-133">![Feedback visivo sulla prossimità della mano](images/HoloLens2_Proximity.gif)</span><span class="sxs-lookup"><span data-stu-id="a15dc-133">![Visual feedback on hand proximity](images/HoloLens2_Proximity.gif)</span></span><br>
    :::column-end:::
:::row-end:::

<br>

<span data-ttu-id="a15dc-134">**Per lo sviluppo di app Unity, vedere [Rettangolo di selezione in Mixed Reality Toolkit-Unity.](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/bounding-box)**</span><span class="sxs-lookup"><span data-stu-id="a15dc-134">**For Unity app development, see [Bounding box in the Mixed Reality Toolkit-Unity.](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/bounding-box)**</span></span>

<br>

---

## <a name="what-is-the-app-bar"></a><span data-ttu-id="a15dc-135">Che cos'è la barra dell'app?</span><span class="sxs-lookup"><span data-stu-id="a15dc-135">What is the App bar?</span></span>

<span data-ttu-id="a15dc-136">La barra dell'app è un menu a livello di oggetto, che contiene una serie di pulsanti visualizzati sul bordo inferiore dei limiti di un ologramma.</span><span class="sxs-lookup"><span data-stu-id="a15dc-136">The App bar is an object-level menu, which contains a series of buttons displayed on the bottom edge of a hologram's bounds.</span></span> <span data-ttu-id="a15dc-137">Questo modello viene comunemente usato per consentire agli utenti di rimuovere e regolare gli ologrammi.</span><span class="sxs-lookup"><span data-stu-id="a15dc-137">This pattern is commonly used to let users remove and adjust holograms.</span></span> <span data-ttu-id="a15dc-138">La barra dell'app è stata progettata principalmente come modo per gestire gli oggetti posizionati nell'ambiente di un utente.</span><span class="sxs-lookup"><span data-stu-id="a15dc-138">The App bar was designed primarily as a way to manage placed objects in a user's environment.</span></span> <span data-ttu-id="a15dc-139">Insieme al rettangolo di selezione, un utente ha il controllo completo su dove e come gli oggetti sono orientati nella realtà mista.</span><span class="sxs-lookup"><span data-stu-id="a15dc-139">Coupled with the bounding box, a user has full control over where and how objects are oriented in mixed reality.</span></span>

:::row:::
    :::column:::
        ### <a name="the-app-bar-follows-the-userbr"></a><span data-ttu-id="a15dc-140">La barra dell'app segue l'utente</span><span class="sxs-lookup"><span data-stu-id="a15dc-140">The App bar follows the user</span></span><br>
        <span data-ttu-id="a15dc-141">Poiché questo modello viene usato con oggetti bloccati a livello mondiale, quando un utente si sposta intorno all'oggetto, la barra dell'app verrà sempre visualizzata sul lato degli oggetti più vicino all'utente.</span><span class="sxs-lookup"><span data-stu-id="a15dc-141">Since this pattern is used with objects that are world locked, as a user moves around the object the App bar will always display on the objects' side closest to the user.</span></span> <span data-ttu-id="a15dc-142">Anche se non tecnicamente, questa funzionalità ottiene in modo efficace lo stesso risultato.</span><span class="sxs-lookup"><span data-stu-id="a15dc-142">While not technically billboarding, this feature effectively achieves the same result.</span></span> <span data-ttu-id="a15dc-143">Impedire la posizione di un utente per occludere o bloccare funzionalità altrimenti disponibili da una posizione diversa nel proprio ambiente.</span><span class="sxs-lookup"><span data-stu-id="a15dc-143">Preventing a user's position to occlude or block functionality that would otherwise be available from a different location in their environment.</span></span> <br>
        <br>
        <span data-ttu-id="a15dc-144">*Ciclo video: in giro per un ologramma, la barra dell'app segue*</span><span class="sxs-lookup"><span data-stu-id="a15dc-144">*Video loop: Walking around a hologram, the App bar follows*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="a15dc-145">![space](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="a15dc-145">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="a15dc-146">![In giro per un ologramma.</span><span class="sxs-lookup"><span data-stu-id="a15dc-146">![Walking around a hologram.</span></span> <span data-ttu-id="a15dc-147">Segue la barra dell'app.](images/HoloLens2_AppBarFollowing.gif)</span><span class="sxs-lookup"><span data-stu-id="a15dc-147">The App bar follows.](images/HoloLens2_AppBarFollowing.gif)</span></span><br>
    :::column-end:::
:::row-end:::

<br>


## <a name="bounding-box-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="a15dc-148">Rettangolo di selezione in MRTK (Mixed Reality Toolkit) per Unity</span><span class="sxs-lookup"><span data-stu-id="a15dc-148">Bounding box in MRTK (Mixed Reality Toolkit) for Unity</span></span>
<span data-ttu-id="a15dc-149">**[MRTK fornisce](https://github.com/Microsoft/MixedRealityToolkit-Unity)** script e prefab per il rettangolo di selezione e la barra dell'app.</span><span class="sxs-lookup"><span data-stu-id="a15dc-149">**[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** provides scripts and prefabs for the Bounding box and App bar.</span></span> <span data-ttu-id="a15dc-150">È possibile aggiungere un rettangolo di selezione assegnando lo script BoundingBox.cs a qualsiasi oggetto.</span><span class="sxs-lookup"><span data-stu-id="a15dc-150">You can add a Bounding box by assigning the BoundingBox.cs script onto any object.</span></span>

* [<span data-ttu-id="a15dc-151">MRTK - Rettangolo di selezione</span><span class="sxs-lookup"><span data-stu-id="a15dc-151">MRTK - Bounding Box</span></span>](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/bounding-box)


<br>

---


## <a name="see-also"></a><span data-ttu-id="a15dc-152">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="a15dc-152">See also</span></span>

* [<span data-ttu-id="a15dc-153">Cursori</span><span class="sxs-lookup"><span data-stu-id="a15dc-153">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="a15dc-154">Raggio della mano</span><span class="sxs-lookup"><span data-stu-id="a15dc-154">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="a15dc-155">Button</span><span class="sxs-lookup"><span data-stu-id="a15dc-155">Button</span></span>](button.md)
* [<span data-ttu-id="a15dc-156">Oggetto che supporta interazioni</span><span class="sxs-lookup"><span data-stu-id="a15dc-156">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="a15dc-157">Rettangolo di selezione e barra dell'app</span><span class="sxs-lookup"><span data-stu-id="a15dc-157">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="a15dc-158">Manipolazione</span><span class="sxs-lookup"><span data-stu-id="a15dc-158">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="a15dc-159">Menu a mano</span><span class="sxs-lookup"><span data-stu-id="a15dc-159">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="a15dc-160">Menu adiacente</span><span class="sxs-lookup"><span data-stu-id="a15dc-160">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="a15dc-161">Raccolta di oggetti</span><span class="sxs-lookup"><span data-stu-id="a15dc-161">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="a15dc-162">Comando vocale</span><span class="sxs-lookup"><span data-stu-id="a15dc-162">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="a15dc-163">Tastiera</span><span class="sxs-lookup"><span data-stu-id="a15dc-163">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="a15dc-164">Descrizione comando</span><span class="sxs-lookup"><span data-stu-id="a15dc-164">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="a15dc-165">Slate</span><span class="sxs-lookup"><span data-stu-id="a15dc-165">Slate</span></span>](slate.md)
* [<span data-ttu-id="a15dc-166">Dispositivo di scorrimento</span><span class="sxs-lookup"><span data-stu-id="a15dc-166">Slider</span></span>](slider.md)
* [<span data-ttu-id="a15dc-167">Shader</span><span class="sxs-lookup"><span data-stu-id="a15dc-167">Shader</span></span>](shader.md)
* [<span data-ttu-id="a15dc-168">Billboarding e tag-along</span><span class="sxs-lookup"><span data-stu-id="a15dc-168">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="a15dc-169">Visualizzazione dello stato</span><span class="sxs-lookup"><span data-stu-id="a15dc-169">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="a15dc-170">Magnetismo di superficie</span><span class="sxs-lookup"><span data-stu-id="a15dc-170">Surface magnetism</span></span>](surface-magnetism.md)
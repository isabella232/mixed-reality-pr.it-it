---
title: Pulsante
description: Informazioni su come attivare un'azione immediata con i pulsanti, uno dei componenti di base della realtà mista.
author: cre8ivepark
ms.author: dongpark
ms.date: 11/01/2019
ms.topic: article
keywords: Realtà mista, controlli, interazione, interfaccia utente, esperienza utente, visore per realtà mista, visore windows mixed reality, visore per realtà virtuale, HoloLens, MRTK, Mixed Reality Toolkit, pulsante
ms.openlocfilehash: ddad8b23950bddd03dd4024497c212d1cc950fb0
ms.sourcegitcommit: 9ae76b339968f035c703d9c1fe57ddecb33198e3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/27/2021
ms.locfileid: "110600370"
---
# <a name="button"></a><span data-ttu-id="c55b9-104">Button</span><span class="sxs-lookup"><span data-stu-id="c55b9-104">Button</span></span>

![Button](images/UX_Hero_Button.jpg)

<span data-ttu-id="c55b9-106">Un pulsante consente agli utenti di attivare azioni immediate in un'esperienza di realtà mista.</span><span class="sxs-lookup"><span data-stu-id="c55b9-106">A button lets your users trigger immediate actions in a mixed reality experience.</span></span> <span data-ttu-id="c55b9-107">In HoloLens 2, i pulsanti hanno suggerimenti visivi e convenienze che consentono di aumentare la confidenza dell'interazione con gli utenti.</span><span class="sxs-lookup"><span data-stu-id="c55b9-107">In HoloLens 2, buttons have visual cues and affordances that help increase interaction confidence with users.</span></span> 

:::row:::
    :::column:::
       <span data-ttu-id="c55b9-108">![Pulsante con l'effetto di luce di prossimità visualizzato](images/UX_Button_Affordance_ProximityLight.jpg)</span><span class="sxs-lookup"><span data-stu-id="c55b9-108">![Button with proximity light effect shown](images/UX_Button_Affordance_ProximityLight.jpg)</span></span><br>
       <span data-ttu-id="c55b9-109">**Luce di prossimità**</span><span class="sxs-lookup"><span data-stu-id="c55b9-109">**Proximity light**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="c55b9-110">![Pulsante selezionato con l'effetto evidenziazione dello stato attivo visualizzato](images/UX_Button_Affordance_FocusHighlight.jpg)</span><span class="sxs-lookup"><span data-stu-id="c55b9-110">![Button selected with focus highlight effect shown](images/UX_Button_Affordance_FocusHighlight.jpg)</span></span><br>
        <span data-ttu-id="c55b9-111">**Evidenziazione dello stato attivo**</span><span class="sxs-lookup"><span data-stu-id="c55b9-111">**Focus highlight**</span></span><br>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       <span data-ttu-id="c55b9-112">![Pulsante premuto con l'effetto della compressione della cella visualizzata](images/UX_Button_Affordance_Compression.jpg)</span><span class="sxs-lookup"><span data-stu-id="c55b9-112">![Button being pressed with compression cage effect shown](images/UX_Button_Affordance_Compression.jpg)</span></span><br>
       <span data-ttu-id="c55b9-113">**Compressione di una cella**</span><span class="sxs-lookup"><span data-stu-id="c55b9-113">**Compressing cage**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="c55b9-114">![Pulsante premuto con l'effetto trigger pulse visualizzato](images/UX_Button_Affordance_Pulse.jpg)</span><span class="sxs-lookup"><span data-stu-id="c55b9-114">![Button being pressed with trigger pulse effect shown](images/UX_Button_Affordance_Pulse.jpg)</span></span><br>
        <span data-ttu-id="c55b9-115">**Pulse on trigger**</span><span class="sxs-lookup"><span data-stu-id="c55b9-115">**Pulse on trigger**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="button-in-mrtkmixed-reality-toolkit-for-unity"></a><span data-ttu-id="c55b9-116">Pulsante in MRTK (Mixed Reality Toolkit) per Unity</span><span class="sxs-lookup"><span data-stu-id="c55b9-116">Button in MRTK(Mixed Reality Toolkit) for Unity</span></span>
<span data-ttu-id="c55b9-117">**[MRTK per Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity)** offre vari tipi di prefab dei pulsanti, inclusi i pulsanti di tipo shell per HoloLens 2 e HoloLens (prima generazione).</span><span class="sxs-lookup"><span data-stu-id="c55b9-117">**[MRTK for Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity)** provides various types of button prefabs, including shell-style buttons for HoloLens 2 and HoloLens (1st gen).</span></span> <span data-ttu-id="c55b9-118">Il prefab del pulsante HoloLens 2 contiene diverse opzioni dettagliate che consentono di migliorare l'attendibilità degli utenti:</span><span class="sxs-lookup"><span data-stu-id="c55b9-118">The HoloLens 2 button prefab contains several detailed affordances that help improve user confidence:</span></span>

* <span data-ttu-id="c55b9-119">Evidenziazione basata sulla prossimità</span><span class="sxs-lookup"><span data-stu-id="c55b9-119">Proximity-based highlight</span></span>
* <span data-ttu-id="c55b9-120">Compressione della cella anteriore</span><span class="sxs-lookup"><span data-stu-id="c55b9-120">Compressing front cage</span></span>
* <span data-ttu-id="c55b9-121">Effetto dell'impulso sul trigger.</span><span class="sxs-lookup"><span data-stu-id="c55b9-121">Pulse effect on trigger.</span></span>

* <span data-ttu-id="c55b9-122">Per altre istruzioni ed esempi personalizzati, vedere [MRTK - Pulsante.](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/button)</span><span class="sxs-lookup"><span data-stu-id="c55b9-122">Check out the [MRTK - Button](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/button) for more instructions and customized examples.</span></span>

<br>

---

## <a name="see-also"></a><span data-ttu-id="c55b9-123">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="c55b9-123">See also</span></span>

* [<span data-ttu-id="c55b9-124">Cursori</span><span class="sxs-lookup"><span data-stu-id="c55b9-124">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="c55b9-125">Raggio della mano</span><span class="sxs-lookup"><span data-stu-id="c55b9-125">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="c55b9-126">Button</span><span class="sxs-lookup"><span data-stu-id="c55b9-126">Button</span></span>](button.md)
* [<span data-ttu-id="c55b9-127">Oggetto che supporta interazioni</span><span class="sxs-lookup"><span data-stu-id="c55b9-127">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="c55b9-128">Rettangolo di selezione e barra dell'app</span><span class="sxs-lookup"><span data-stu-id="c55b9-128">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="c55b9-129">Manipolazione</span><span class="sxs-lookup"><span data-stu-id="c55b9-129">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="c55b9-130">Menu a mano</span><span class="sxs-lookup"><span data-stu-id="c55b9-130">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="c55b9-131">Menu adiacente</span><span class="sxs-lookup"><span data-stu-id="c55b9-131">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="c55b9-132">Raccolta di oggetti</span><span class="sxs-lookup"><span data-stu-id="c55b9-132">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="c55b9-133">Comando vocale</span><span class="sxs-lookup"><span data-stu-id="c55b9-133">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="c55b9-134">Tastiera</span><span class="sxs-lookup"><span data-stu-id="c55b9-134">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="c55b9-135">Descrizione comando</span><span class="sxs-lookup"><span data-stu-id="c55b9-135">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="c55b9-136">Slate</span><span class="sxs-lookup"><span data-stu-id="c55b9-136">Slate</span></span>](slate.md)
* [<span data-ttu-id="c55b9-137">Dispositivo di scorrimento</span><span class="sxs-lookup"><span data-stu-id="c55b9-137">Slider</span></span>](slider.md)
* [<span data-ttu-id="c55b9-138">Shader</span><span class="sxs-lookup"><span data-stu-id="c55b9-138">Shader</span></span>](shader.md)
* [<span data-ttu-id="c55b9-139">Billboarding e tag-along</span><span class="sxs-lookup"><span data-stu-id="c55b9-139">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="c55b9-140">Visualizzazione dello stato</span><span class="sxs-lookup"><span data-stu-id="c55b9-140">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="c55b9-141">Magnetismo di superficie</span><span class="sxs-lookup"><span data-stu-id="c55b9-141">Surface magnetism</span></span>](surface-magnetism.md)
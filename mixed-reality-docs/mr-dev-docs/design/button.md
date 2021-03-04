---
title: Pulsante
description: Viene illustrato come attivare un'azione immediata con i pulsanti, che è uno dei componenti fondamentali della realtà mista.
author: cre8ivepark
ms.author: dongpark
ms.date: 11/01/2019
ms.topic: article
keywords: Realtà mista, controlli, interazione, interfaccia utente, UX, cuffie per realtà mista, cuffie con realtà mista di Windows, auricolare realtà virtuale, HoloLens, MRTK, Toolkit realtà mista, pulsante
ms.openlocfilehash: 9e4d0637d8c10c3cd23bd2ee1369fd57137af795
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/03/2021
ms.locfileid: "101759427"
---
# <a name="button"></a><span data-ttu-id="32d70-104">Button</span><span class="sxs-lookup"><span data-stu-id="32d70-104">Button</span></span>

![Button](images/UX_Hero_Button.jpg)

<span data-ttu-id="32d70-106">Un pulsante consente agli utenti di attivare azioni immediate in un'esperienza di realtà mista.</span><span class="sxs-lookup"><span data-stu-id="32d70-106">A button lets your users trigger immediate actions in a mixed reality experience.</span></span> <span data-ttu-id="32d70-107">In HoloLens 2 i pulsanti hanno segnali visivi e affordances che consentono di aumentare la confidenza di interazione con gli utenti.</span><span class="sxs-lookup"><span data-stu-id="32d70-107">In HoloLens 2, buttons have visual cues and affordances that help increase interaction confidence with users.</span></span> 

:::row:::
    :::column:::
       <span data-ttu-id="32d70-108">![Pulsante con effetto di luce vicino visualizzato](images/UX_Button_Affordance_ProximityLight.jpg)</span><span class="sxs-lookup"><span data-stu-id="32d70-108">![Button with proximity light effect shown](images/UX_Button_Affordance_ProximityLight.jpg)</span></span><br>
       <span data-ttu-id="32d70-109">**Luce vicina**</span><span class="sxs-lookup"><span data-stu-id="32d70-109">**Proximity light**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="32d70-110">![Pulsante selezionato con effetto evidenziato attivo visualizzato](images/UX_Button_Affordance_FocusHighlight.jpg)</span><span class="sxs-lookup"><span data-stu-id="32d70-110">![Button selected with focus highlight effect shown](images/UX_Button_Affordance_FocusHighlight.jpg)</span></span><br>
        <span data-ttu-id="32d70-111">**Evidenziazione dello stato attivo**</span><span class="sxs-lookup"><span data-stu-id="32d70-111">**Focus highlight**</span></span><br>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       <span data-ttu-id="32d70-112">![Pulsante premuto con effetto della gabbia di compressione visualizzato](images/UX_Button_Affordance_Compression.jpg)</span><span class="sxs-lookup"><span data-stu-id="32d70-112">![Button being pressed with compression cage effect shown](images/UX_Button_Affordance_Compression.jpg)</span></span><br>
       <span data-ttu-id="32d70-113">**Compressione Cage**</span><span class="sxs-lookup"><span data-stu-id="32d70-113">**Compressing cage**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="32d70-114">![Pulsante premuto con effetto impulso trigger visualizzato](images/UX_Button_Affordance_Pulse.jpg)</span><span class="sxs-lookup"><span data-stu-id="32d70-114">![Button being pressed with trigger pulse effect shown](images/UX_Button_Affordance_Pulse.jpg)</span></span><br>
        <span data-ttu-id="32d70-115">**Pulse on trigger**</span><span class="sxs-lookup"><span data-stu-id="32d70-115">**Pulse on trigger**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="button-in-mrtkmixed-reality-toolkit-for-unity"></a><span data-ttu-id="32d70-116">Pulsante in MRTK (Mixed Reality Toolkit) per Unity</span><span class="sxs-lookup"><span data-stu-id="32d70-116">Button in MRTK(Mixed Reality Toolkit) for Unity</span></span>
<span data-ttu-id="32d70-117">**[MRTK per Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity)** offre diversi tipi di prefabbricati di pulsanti, inclusi i pulsanti di tipo Shell per HoloLens 2 e HoloLens (1a generazione).</span><span class="sxs-lookup"><span data-stu-id="32d70-117">**[MRTK for Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity)** provides various types of button prefabs, including shell-style buttons for HoloLens 2 and HoloLens (1st gen).</span></span> <span data-ttu-id="32d70-118">Il prefabbricato di HoloLens 2 Button contiene diversi affordances dettagliati che consentono di migliorare la confidenza degli utenti:</span><span class="sxs-lookup"><span data-stu-id="32d70-118">The HoloLens 2 button prefab contains several detailed affordances that help improve user confidence:</span></span>

* <span data-ttu-id="32d70-119">Evidenziazione basata su prossimità</span><span class="sxs-lookup"><span data-stu-id="32d70-119">Proximity-based highlight</span></span>
* <span data-ttu-id="32d70-120">Compressione della gabbia anteriore</span><span class="sxs-lookup"><span data-stu-id="32d70-120">Compressing front cage</span></span>
* <span data-ttu-id="32d70-121">Effetto impulsi sul trigger.</span><span class="sxs-lookup"><span data-stu-id="32d70-121">Pulse effect on trigger.</span></span>

* <span data-ttu-id="32d70-122">Per altre istruzioni ed esempi personalizzati, vedere il [pulsante MRTK](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/ux-building-blocks/button.md) .</span><span class="sxs-lookup"><span data-stu-id="32d70-122">Check out the [MRTK - Button](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/ux-building-blocks/button.md) for more instructions and customized examples.</span></span>

<br>

---

## <a name="see-also"></a><span data-ttu-id="32d70-123">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="32d70-123">See also</span></span>

* [<span data-ttu-id="32d70-124">Cursori</span><span class="sxs-lookup"><span data-stu-id="32d70-124">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="32d70-125">Raggio della mano</span><span class="sxs-lookup"><span data-stu-id="32d70-125">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="32d70-126">Button</span><span class="sxs-lookup"><span data-stu-id="32d70-126">Button</span></span>](button.md)
* [<span data-ttu-id="32d70-127">Oggetto che supporta interazioni</span><span class="sxs-lookup"><span data-stu-id="32d70-127">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="32d70-128">Rettangolo di selezione e barra dell'app</span><span class="sxs-lookup"><span data-stu-id="32d70-128">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="32d70-129">Manipolazione</span><span class="sxs-lookup"><span data-stu-id="32d70-129">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="32d70-130">Menu a mano</span><span class="sxs-lookup"><span data-stu-id="32d70-130">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="32d70-131">Menu adiacente</span><span class="sxs-lookup"><span data-stu-id="32d70-131">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="32d70-132">Raccolta di oggetti</span><span class="sxs-lookup"><span data-stu-id="32d70-132">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="32d70-133">Comando vocale</span><span class="sxs-lookup"><span data-stu-id="32d70-133">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="32d70-134">Tastiera</span><span class="sxs-lookup"><span data-stu-id="32d70-134">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="32d70-135">Descrizione comando</span><span class="sxs-lookup"><span data-stu-id="32d70-135">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="32d70-136">Slate</span><span class="sxs-lookup"><span data-stu-id="32d70-136">Slate</span></span>](slate.md)
* [<span data-ttu-id="32d70-137">Dispositivo di scorrimento</span><span class="sxs-lookup"><span data-stu-id="32d70-137">Slider</span></span>](slider.md)
* [<span data-ttu-id="32d70-138">Shader</span><span class="sxs-lookup"><span data-stu-id="32d70-138">Shader</span></span>](shader.md)
* [<span data-ttu-id="32d70-139">Billboarding e tag-along</span><span class="sxs-lookup"><span data-stu-id="32d70-139">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="32d70-140">Visualizzazione dello stato</span><span class="sxs-lookup"><span data-stu-id="32d70-140">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="32d70-141">Magnetismo di superficie</span><span class="sxs-lookup"><span data-stu-id="32d70-141">Surface magnetism</span></span>](surface-magnetism.md)

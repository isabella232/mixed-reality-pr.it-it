---
title: Shader
description: Informazioni sul modo in cui lo shader standard di Mixed Reality Toolkit offre diversi tipi di effetti visivi che possono essere usati con gli ologrammi nelle app per realtà mista.
author: cre8ivepark
ms.author: dongpark
ms.date: 11/01/2019
ms.topic: article
keywords: Realtà mista, controlli, interazione, interfaccia utente, UX, shader, auricolare realtà mista, auricolare di realtà mista, auricolare di realtà virtuale, HoloLens, MRTK, Toolkit realtà mista, effetti visivi
ms.openlocfilehash: 68e40c053f9557debf9ad22baf2f48a8e06a1bbb
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2021
ms.locfileid: "98008861"
---
# <a name="shader"></a><span data-ttu-id="1d957-104">Shader</span><span class="sxs-lookup"><span data-stu-id="1d957-104">Shader</span></span>

![Shader](images/UX_Hero_StandardShader.jpg)

<span data-ttu-id="1d957-106">Poiché gli oggetti olografici sono combinati con quelli fisici nell'ambiente reale, è importante fornire segnali visivi all'utente.</span><span class="sxs-lookup"><span data-stu-id="1d957-106">Since holographic objects are mixed with physical ones in the real environment, it's important to provide visual cues to the user.</span></span> <span data-ttu-id="1d957-107">Il Toolkit di realtà mista standard shader fornisce vari tipi di effetti visivi da usare con gli ologrammi.</span><span class="sxs-lookup"><span data-stu-id="1d957-107">The Mixed Reality Toolkit Standard shader provides various types of visual effects for use with holograms.</span></span> <span data-ttu-id="1d957-108">Il sistema di ombreggiatura usa un unico shader flessibile per ottenere oggetti visivi simili allo shader standard di Unity.</span><span class="sxs-lookup"><span data-stu-id="1d957-108">The shading system uses a single, flexible shader to achieve visuals similar to Unity's Standard Shader.</span></span> <span data-ttu-id="1d957-109">Lo shader implementa i [principi del sistema di progettazione Fluent](https://www.microsoft.com/design/fluent/#/) e continua a funzionare sui dispositivi di realtà mista.</span><span class="sxs-lookup"><span data-stu-id="1d957-109">The shader implements [Fluent Design System principles](https://www.microsoft.com/design/fluent/#/) and remains performant on mixed reality devices.</span></span>
<br>

## <a name="examples-of-visual-effects-using-mrtk-mixed-reality-toolkit-standard-shader"></a><span data-ttu-id="1d957-110">Esempi di effetti visivi con MRTK (Mixed Reality Toolkit) standard shader</span><span class="sxs-lookup"><span data-stu-id="1d957-110">Examples of visual effects using MRTK (Mixed Reality Toolkit) Standard shader</span></span> 
:::row:::
    :::column:::
       <span data-ttu-id="1d957-111">![Spostamento](images/UX_Button_Affordance_ProximityLight.jpg)</span><span class="sxs-lookup"><span data-stu-id="1d957-111">![Move](images/UX_Button_Affordance_ProximityLight.jpg)</span></span><br>
       <span data-ttu-id="1d957-112">**Luce vicina**</span><span class="sxs-lookup"><span data-stu-id="1d957-112">**Proximity light**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="1d957-113">![Rotazione](images/UX_Button_Affordance_FocusHighlight.jpg)</span><span class="sxs-lookup"><span data-stu-id="1d957-113">![Rotate](images/UX_Button_Affordance_FocusHighlight.jpg)</span></span><br>
        <span data-ttu-id="1d957-114">**Bordo chiaro**</span><span class="sxs-lookup"><span data-stu-id="1d957-114">**Border light**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="standard-shader-in-mrtk-for-unity"></a><span data-ttu-id="1d957-115">Shader standard in MRTK per Unity</span><span class="sxs-lookup"><span data-stu-id="1d957-115">Standard shader in MRTK for Unity</span></span>

* [<span data-ttu-id="1d957-116">MRTK-standard shader</span><span class="sxs-lookup"><span data-stu-id="1d957-116">MRTK - Standard shader</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_MRTKStandardShader.html)

<br>

---

## <a name="see-also"></a><span data-ttu-id="1d957-117">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="1d957-117">See also</span></span>

* [<span data-ttu-id="1d957-118">Cursori</span><span class="sxs-lookup"><span data-stu-id="1d957-118">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="1d957-119">Raggio della mano</span><span class="sxs-lookup"><span data-stu-id="1d957-119">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="1d957-120">Button</span><span class="sxs-lookup"><span data-stu-id="1d957-120">Button</span></span>](button.md)
* [<span data-ttu-id="1d957-121">Oggetto che supporta interazioni</span><span class="sxs-lookup"><span data-stu-id="1d957-121">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="1d957-122">Rettangolo di selezione e barra dell'app</span><span class="sxs-lookup"><span data-stu-id="1d957-122">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="1d957-123">Manipolazione</span><span class="sxs-lookup"><span data-stu-id="1d957-123">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="1d957-124">Menu a mano</span><span class="sxs-lookup"><span data-stu-id="1d957-124">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="1d957-125">Menu adiacente</span><span class="sxs-lookup"><span data-stu-id="1d957-125">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="1d957-126">Raccolta di oggetti</span><span class="sxs-lookup"><span data-stu-id="1d957-126">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="1d957-127">Comando vocale</span><span class="sxs-lookup"><span data-stu-id="1d957-127">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="1d957-128">Tastiera</span><span class="sxs-lookup"><span data-stu-id="1d957-128">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="1d957-129">Descrizione comando</span><span class="sxs-lookup"><span data-stu-id="1d957-129">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="1d957-130">Slate</span><span class="sxs-lookup"><span data-stu-id="1d957-130">Slate</span></span>](slate.md)
* [<span data-ttu-id="1d957-131">Dispositivo di scorrimento</span><span class="sxs-lookup"><span data-stu-id="1d957-131">Slider</span></span>](slider.md)
* [<span data-ttu-id="1d957-132">Billboarding e tag-along</span><span class="sxs-lookup"><span data-stu-id="1d957-132">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="1d957-133">Visualizzazione dello stato</span><span class="sxs-lookup"><span data-stu-id="1d957-133">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="1d957-134">Magnetismo di superficie</span><span class="sxs-lookup"><span data-stu-id="1d957-134">Surface magnetism</span></span>](surface-magnetism.md)

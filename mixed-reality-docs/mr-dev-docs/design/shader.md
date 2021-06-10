---
title: Shader
description: Informazioni su come lo shader Standard di Mixed Reality Toolkit offre vari tipi di effetti visivi che possono essere usati con gli ologrammi nelle app di realtà mista.
author: cre8ivepark
ms.author: dongpark
ms.date: 11/01/2019
ms.topic: article
keywords: Realtà mista, controlli, interazione, interfaccia utente, ux, shader, visore per realtà mista, visore windows mixed reality, visore per realtà virtuale, HoloLens, MRTK, Mixed Reality Toolkit, effetti visivi
ms.openlocfilehash: 9a60c5065ddb5bcf410bb43b318575da50f7ccf8
ms.sourcegitcommit: 9ae76b339968f035c703d9c1fe57ddecb33198e3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/27/2021
ms.locfileid: "110600180"
---
# <a name="shader"></a><span data-ttu-id="219c9-104">Shader</span><span class="sxs-lookup"><span data-stu-id="219c9-104">Shader</span></span>

![Shader](images/UX_Hero_StandardShader.jpg)

<span data-ttu-id="219c9-106">Poiché gli oggetti olografici sono misti a quelli fisici nell'ambiente reale, è importante fornire segnali visivi all'utente.</span><span class="sxs-lookup"><span data-stu-id="219c9-106">Since holographic objects are mixed with physical ones in the real environment, it's important to provide visual cues to the user.</span></span> <span data-ttu-id="219c9-107">Lo shader Standard di Mixed Reality Toolkit fornisce vari tipi di effetti visivi da usare con gli ologrammi.</span><span class="sxs-lookup"><span data-stu-id="219c9-107">The Mixed Reality Toolkit Standard shader provides various types of visual effects for use with holograms.</span></span> <span data-ttu-id="219c9-108">Il sistema di ombreggiatura usa un singolo shader flessibile per ottenere oggetti visivi simili allo shader Standard di Unity.</span><span class="sxs-lookup"><span data-stu-id="219c9-108">The shading system uses a single, flexible shader to achieve visuals similar to Unity's Standard Shader.</span></span> <span data-ttu-id="219c9-109">Lo shader implementa Fluent Design System [principi](https://www.microsoft.com/design/fluent/#/) e rimane performante nei dispositivi di realtà mista.</span><span class="sxs-lookup"><span data-stu-id="219c9-109">The shader implements [Fluent Design System principles](https://www.microsoft.com/design/fluent/#/) and remains performant on mixed reality devices.</span></span>
<br>

## <a name="examples-of-visual-effects-using-mrtk-mixed-reality-toolkit-standard-shader"></a><span data-ttu-id="219c9-110">Esempi di effetti visivi che usano lo shader STANDARD MRTK (Mixed Reality Toolkit)</span><span class="sxs-lookup"><span data-stu-id="219c9-110">Examples of visual effects using MRTK (Mixed Reality Toolkit) Standard shader</span></span> 
:::row:::
    :::column:::
       <span data-ttu-id="219c9-111">![Spostamento](images/UX_Button_Affordance_ProximityLight.jpg)</span><span class="sxs-lookup"><span data-stu-id="219c9-111">![Move](images/UX_Button_Affordance_ProximityLight.jpg)</span></span><br>
       <span data-ttu-id="219c9-112">**Luce di prossimità**</span><span class="sxs-lookup"><span data-stu-id="219c9-112">**Proximity light**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="219c9-113">![Rotazione](images/UX_Button_Affordance_FocusHighlight.jpg)</span><span class="sxs-lookup"><span data-stu-id="219c9-113">![Rotate](images/UX_Button_Affordance_FocusHighlight.jpg)</span></span><br>
        <span data-ttu-id="219c9-114">**Luce del bordo**</span><span class="sxs-lookup"><span data-stu-id="219c9-114">**Border light**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="standard-shader-in-mrtk-for-unity"></a><span data-ttu-id="219c9-115">Shader standard in MRTK per Unity</span><span class="sxs-lookup"><span data-stu-id="219c9-115">Standard shader in MRTK for Unity</span></span>

* [<span data-ttu-id="219c9-116">MRTK - Shader standard</span><span class="sxs-lookup"><span data-stu-id="219c9-116">MRTK - Standard shader</span></span>](/windows/mixed-reality/mrtk-unity/features/rendering/mrtk-standard-shader)

<br>

---

## <a name="see-also"></a><span data-ttu-id="219c9-117">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="219c9-117">See also</span></span>

* [<span data-ttu-id="219c9-118">Cursori</span><span class="sxs-lookup"><span data-stu-id="219c9-118">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="219c9-119">Raggio della mano</span><span class="sxs-lookup"><span data-stu-id="219c9-119">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="219c9-120">Button</span><span class="sxs-lookup"><span data-stu-id="219c9-120">Button</span></span>](button.md)
* [<span data-ttu-id="219c9-121">Oggetto che supporta interazioni</span><span class="sxs-lookup"><span data-stu-id="219c9-121">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="219c9-122">Rettangolo di selezione e barra dell'app</span><span class="sxs-lookup"><span data-stu-id="219c9-122">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="219c9-123">Manipolazione</span><span class="sxs-lookup"><span data-stu-id="219c9-123">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="219c9-124">Menu a mano</span><span class="sxs-lookup"><span data-stu-id="219c9-124">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="219c9-125">Menu adiacente</span><span class="sxs-lookup"><span data-stu-id="219c9-125">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="219c9-126">Raccolta di oggetti</span><span class="sxs-lookup"><span data-stu-id="219c9-126">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="219c9-127">Comando vocale</span><span class="sxs-lookup"><span data-stu-id="219c9-127">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="219c9-128">Tastiera</span><span class="sxs-lookup"><span data-stu-id="219c9-128">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="219c9-129">Descrizione comando</span><span class="sxs-lookup"><span data-stu-id="219c9-129">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="219c9-130">Slate</span><span class="sxs-lookup"><span data-stu-id="219c9-130">Slate</span></span>](slate.md)
* [<span data-ttu-id="219c9-131">Dispositivo di scorrimento</span><span class="sxs-lookup"><span data-stu-id="219c9-131">Slider</span></span>](slider.md)
* [<span data-ttu-id="219c9-132">Billboarding e tag-along</span><span class="sxs-lookup"><span data-stu-id="219c9-132">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="219c9-133">Visualizzazione dello stato</span><span class="sxs-lookup"><span data-stu-id="219c9-133">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="219c9-134">Magnetismo di superficie</span><span class="sxs-lookup"><span data-stu-id="219c9-134">Surface magnetism</span></span>](surface-magnetism.md)
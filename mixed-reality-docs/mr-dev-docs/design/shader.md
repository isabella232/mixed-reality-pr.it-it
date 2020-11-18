---
title: Shader
description: Lo shader standard MRTK fornisce vari tipi di effetti visivi che possono essere usati con gli ologrammi.
author: cre8ivepark
ms.author: dongpark
ms.date: 11/01/2019
ms.topic: article
keywords: Realtà mista, controlli, interazione, interfaccia utente, UX, shader, auricolare realtà mista, auricolare di realtà mista, auricolare di realtà virtuale, HoloLens, MRTK, Toolkit realtà mista, effetti visivi
ms.openlocfilehash: ced2d62f9304a8e6238febb8c485449f2e10b135
ms.sourcegitcommit: 4f3ef057a285be2e260615e5d6c41f00d15d08f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2020
ms.locfileid: "94703347"
---
# <a name="shader"></a><span data-ttu-id="a8a80-104">Shader</span><span class="sxs-lookup"><span data-stu-id="a8a80-104">Shader</span></span>

![Shader](images/UX_Hero_StandardShader.jpg)

<span data-ttu-id="a8a80-106">Poiché gli oggetti olografici sono combinati con quelli fisici nell'ambiente reale, è importante fornire segnali visivi all'utente.</span><span class="sxs-lookup"><span data-stu-id="a8a80-106">Since holographic objects are mixed with physical ones in the real environment, it's important to provide visual cues to the user.</span></span> <span data-ttu-id="a8a80-107">Lo shader standard MRTK fornisce vari tipi di effetti visivi che possono essere usati con gli ologrammi.</span><span class="sxs-lookup"><span data-stu-id="a8a80-107">The MRTK Standard shader provides various types of visual effects that can be used with holograms.</span></span> <span data-ttu-id="a8a80-108">Il sistema di ombreggiatura standard MRTK usa un unico shader flessibile che può ottenere oggetti visivi simili allo shader standard di Unity, implementa i [principi del sistema di progettazione Fluent](https://www.microsoft.com/design/fluent/#/)e continua a funzionare sui dispositivi di realtà mista.</span><span class="sxs-lookup"><span data-stu-id="a8a80-108">The MRTK Standard shading system utilizes a single, flexible shader that can achieve visuals similar to Unity's Standard Shader, implements [Fluent Design System principles](https://www.microsoft.com/design/fluent/#/), and remains performant on mixed reality devices.</span></span>
<br>

## <a name="examples-of-visual-effects-using-mrtk-standard-shader"></a><span data-ttu-id="a8a80-109">Esempi di effetti visivi con MRTK standard shader</span><span class="sxs-lookup"><span data-stu-id="a8a80-109">Examples of visual effects using MRTK Standard shader</span></span> 
:::row:::
    :::column:::
       <span data-ttu-id="a8a80-110">![Spostamento](images/UX_Button_Affordance_ProximityLight.jpg)</span><span class="sxs-lookup"><span data-stu-id="a8a80-110">![Move](images/UX_Button_Affordance_ProximityLight.jpg)</span></span><br>
       <span data-ttu-id="a8a80-111">**Luce vicina**</span><span class="sxs-lookup"><span data-stu-id="a8a80-111">**Proximity light**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="a8a80-112">![Rotazione](images/UX_Button_Affordance_FocusHighlight.jpg)</span><span class="sxs-lookup"><span data-stu-id="a8a80-112">![Rotate](images/UX_Button_Affordance_FocusHighlight.jpg)</span></span><br>
        <span data-ttu-id="a8a80-113">**Bordo chiaro**</span><span class="sxs-lookup"><span data-stu-id="a8a80-113">**Border light**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="mrtk-standard-shader-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="a8a80-114">Shader standard MRTK in MRTK (Toolkit realtà mista) per Unity</span><span class="sxs-lookup"><span data-stu-id="a8a80-114">MRTK Standard shader in MRTK (Mixed Reality Toolkit) for Unity</span></span>

* [<span data-ttu-id="a8a80-115">MRTK-standard shader</span><span class="sxs-lookup"><span data-stu-id="a8a80-115">MRTK - Standard shader</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_MRTKStandardShader.html)


<br>

---

## <a name="see-also"></a><span data-ttu-id="a8a80-116">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="a8a80-116">See also</span></span>

* [<span data-ttu-id="a8a80-117">Cursori</span><span class="sxs-lookup"><span data-stu-id="a8a80-117">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="a8a80-118">Raggio della mano</span><span class="sxs-lookup"><span data-stu-id="a8a80-118">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="a8a80-119">Button</span><span class="sxs-lookup"><span data-stu-id="a8a80-119">Button</span></span>](button.md)
* [<span data-ttu-id="a8a80-120">Oggetto che supporta interazioni</span><span class="sxs-lookup"><span data-stu-id="a8a80-120">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="a8a80-121">Rettangolo di selezione e barra dell'app</span><span class="sxs-lookup"><span data-stu-id="a8a80-121">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="a8a80-122">Manipolazione</span><span class="sxs-lookup"><span data-stu-id="a8a80-122">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="a8a80-123">Menu a mano</span><span class="sxs-lookup"><span data-stu-id="a8a80-123">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="a8a80-124">Menu adiacente</span><span class="sxs-lookup"><span data-stu-id="a8a80-124">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="a8a80-125">Raccolta di oggetti</span><span class="sxs-lookup"><span data-stu-id="a8a80-125">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="a8a80-126">Comando vocale</span><span class="sxs-lookup"><span data-stu-id="a8a80-126">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="a8a80-127">Tastiera</span><span class="sxs-lookup"><span data-stu-id="a8a80-127">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="a8a80-128">Descrizione comando</span><span class="sxs-lookup"><span data-stu-id="a8a80-128">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="a8a80-129">Slate</span><span class="sxs-lookup"><span data-stu-id="a8a80-129">Slate</span></span>](slate.md)
* [<span data-ttu-id="a8a80-130">Dispositivo di scorrimento</span><span class="sxs-lookup"><span data-stu-id="a8a80-130">Slider</span></span>](slider.md)
* [<span data-ttu-id="a8a80-131">Billboarding e tag-along</span><span class="sxs-lookup"><span data-stu-id="a8a80-131">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="a8a80-132">Visualizzazione dello stato</span><span class="sxs-lookup"><span data-stu-id="a8a80-132">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="a8a80-133">Magnetismo di superficie</span><span class="sxs-lookup"><span data-stu-id="a8a80-133">Surface magnetism</span></span>](surface-magnetism.md)

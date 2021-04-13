---
title: Shader
description: Informazioni sul modo in cui lo shader standard di Mixed Reality Toolkit offre diversi tipi di effetti visivi che possono essere usati con gli ologrammi nelle app per realtà mista.
author: cre8ivepark
ms.author: dongpark
ms.date: 11/01/2019
ms.topic: article
keywords: Realtà mista, controlli, interazione, interfaccia utente, UX, shader, auricolare realtà mista, auricolare di realtà mista, auricolare di realtà virtuale, HoloLens, MRTK, Toolkit realtà mista, effetti visivi
ms.openlocfilehash: 4bf8205ac9dfbd22a0deb9ffe796fd4e33a96f89
ms.sourcegitcommit: 1c9035487270af76c6eaba11b11f6fc56c008135
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/13/2021
ms.locfileid: "107300386"
---
# <a name="shader"></a><span data-ttu-id="d4bfd-104">Shader</span><span class="sxs-lookup"><span data-stu-id="d4bfd-104">Shader</span></span>

![Shader](images/UX_Hero_StandardShader.jpg)

<span data-ttu-id="d4bfd-106">Poiché gli oggetti olografici sono combinati con quelli fisici nell'ambiente reale, è importante fornire segnali visivi all'utente.</span><span class="sxs-lookup"><span data-stu-id="d4bfd-106">Since holographic objects are mixed with physical ones in the real environment, it's important to provide visual cues to the user.</span></span> <span data-ttu-id="d4bfd-107">Il Toolkit di realtà mista standard shader fornisce vari tipi di effetti visivi da usare con gli ologrammi.</span><span class="sxs-lookup"><span data-stu-id="d4bfd-107">The Mixed Reality Toolkit Standard shader provides various types of visual effects for use with holograms.</span></span> <span data-ttu-id="d4bfd-108">Il sistema di ombreggiatura usa un unico shader flessibile per ottenere oggetti visivi simili allo shader standard di Unity.</span><span class="sxs-lookup"><span data-stu-id="d4bfd-108">The shading system uses a single, flexible shader to achieve visuals similar to Unity's Standard Shader.</span></span> <span data-ttu-id="d4bfd-109">Lo shader implementa i [principi del sistema di progettazione Fluent](https://www.microsoft.com/design/fluent/#/) e continua a funzionare sui dispositivi di realtà mista.</span><span class="sxs-lookup"><span data-stu-id="d4bfd-109">The shader implements [Fluent Design System principles](https://www.microsoft.com/design/fluent/#/) and remains performant on mixed reality devices.</span></span>
<br>

## <a name="examples-of-visual-effects-using-mrtk-mixed-reality-toolkit-standard-shader"></a><span data-ttu-id="d4bfd-110">Esempi di effetti visivi con MRTK (Mixed Reality Toolkit) standard shader</span><span class="sxs-lookup"><span data-stu-id="d4bfd-110">Examples of visual effects using MRTK (Mixed Reality Toolkit) Standard shader</span></span> 
:::row:::
    :::column:::
       <span data-ttu-id="d4bfd-111">![Spostamento](images/UX_Button_Affordance_ProximityLight.jpg)</span><span class="sxs-lookup"><span data-stu-id="d4bfd-111">![Move](images/UX_Button_Affordance_ProximityLight.jpg)</span></span><br>
       <span data-ttu-id="d4bfd-112">**Luce vicina**</span><span class="sxs-lookup"><span data-stu-id="d4bfd-112">**Proximity light**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="d4bfd-113">![Rotazione](images/UX_Button_Affordance_FocusHighlight.jpg)</span><span class="sxs-lookup"><span data-stu-id="d4bfd-113">![Rotate](images/UX_Button_Affordance_FocusHighlight.jpg)</span></span><br>
        <span data-ttu-id="d4bfd-114">**Bordo chiaro**</span><span class="sxs-lookup"><span data-stu-id="d4bfd-114">**Border light**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="standard-shader-in-mrtk-for-unity"></a><span data-ttu-id="d4bfd-115">Shader standard in MRTK per Unity</span><span class="sxs-lookup"><span data-stu-id="d4bfd-115">Standard shader in MRTK for Unity</span></span>

* [<span data-ttu-id="d4bfd-116">MRTK-standard shader</span><span class="sxs-lookup"><span data-stu-id="d4bfd-116">MRTK - Standard shader</span></span>](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/rendering/mrtk-standard-shader)

<br>

---

## <a name="see-also"></a><span data-ttu-id="d4bfd-117">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="d4bfd-117">See also</span></span>

* [<span data-ttu-id="d4bfd-118">Cursori</span><span class="sxs-lookup"><span data-stu-id="d4bfd-118">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="d4bfd-119">Raggio della mano</span><span class="sxs-lookup"><span data-stu-id="d4bfd-119">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="d4bfd-120">Button</span><span class="sxs-lookup"><span data-stu-id="d4bfd-120">Button</span></span>](button.md)
* [<span data-ttu-id="d4bfd-121">Oggetto che supporta interazioni</span><span class="sxs-lookup"><span data-stu-id="d4bfd-121">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="d4bfd-122">Rettangolo di selezione e barra dell'app</span><span class="sxs-lookup"><span data-stu-id="d4bfd-122">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="d4bfd-123">Manipolazione</span><span class="sxs-lookup"><span data-stu-id="d4bfd-123">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="d4bfd-124">Menu a mano</span><span class="sxs-lookup"><span data-stu-id="d4bfd-124">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="d4bfd-125">Menu adiacente</span><span class="sxs-lookup"><span data-stu-id="d4bfd-125">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="d4bfd-126">Raccolta di oggetti</span><span class="sxs-lookup"><span data-stu-id="d4bfd-126">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="d4bfd-127">Comando vocale</span><span class="sxs-lookup"><span data-stu-id="d4bfd-127">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="d4bfd-128">Tastiera</span><span class="sxs-lookup"><span data-stu-id="d4bfd-128">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="d4bfd-129">Descrizione comando</span><span class="sxs-lookup"><span data-stu-id="d4bfd-129">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="d4bfd-130">Slate</span><span class="sxs-lookup"><span data-stu-id="d4bfd-130">Slate</span></span>](slate.md)
* [<span data-ttu-id="d4bfd-131">Dispositivo di scorrimento</span><span class="sxs-lookup"><span data-stu-id="d4bfd-131">Slider</span></span>](slider.md)
* [<span data-ttu-id="d4bfd-132">Billboarding e tag-along</span><span class="sxs-lookup"><span data-stu-id="d4bfd-132">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="d4bfd-133">Visualizzazione dello stato</span><span class="sxs-lookup"><span data-stu-id="d4bfd-133">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="d4bfd-134">Magnetismo di superficie</span><span class="sxs-lookup"><span data-stu-id="d4bfd-134">Surface magnetism</span></span>](surface-magnetism.md)

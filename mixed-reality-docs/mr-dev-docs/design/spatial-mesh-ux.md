---
title: Visualizzazione della mesh spaziale
description: Informazioni sulle linee guida di progettazione e sulla comprensione dell'ambiente fisico con la visualizzazione della mesh spaziale in MRTK.
author: cre8ivepark
ms.author: dongpark
ms.date: 06/19/2020
ms.topic: article
keywords: Realtà mista, HoloLens, controlli dell'interfaccia utente, interazione, interfaccia utente, UX Design, interfaccia utente spaziale, interazione spaziale, interfaccia utente 3D, esperienza utente 3D, visore per realtà mista, visore windows mixed reality, visore per realtà virtuale, HoloLens, MRTK, Mixed Reality Toolkit
ms.openlocfilehash: 5bdcba60f38ac67bbf0f394337735f4a2d4ec423
ms.sourcegitcommit: 9ae76b339968f035c703d9c1fe57ddecb33198e3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/27/2021
ms.locfileid: "110600630"
---
# <a name="spatial-mesh"></a><span data-ttu-id="56e15-104">Mesh spaziale</span><span class="sxs-lookup"><span data-stu-id="56e15-104">Spatial mesh</span></span>

![Mesh spaziale](images/MRTK_PulseShader_SpatialMesh.gif)

<span data-ttu-id="56e15-106">Gli utenti apprendono come un dispositivo percepirà e comprende l'ambiente fisico tramite la visualizzazione della mesh spaziale.</span><span class="sxs-lookup"><span data-stu-id="56e15-106">Users learn how a device perceives and understands the physical environment through spatial mesh visualization.</span></span> <span data-ttu-id="56e15-107">Una corretta visualizzazione della mesh spaziale può creare un'esperienza piacevole e magica fornendo al tempo stesso il contesto spaziale.</span><span class="sxs-lookup"><span data-stu-id="56e15-107">Proper spatial mesh visualization can create a delightful and magical experience while providing spatial context.</span></span>  

## <a name="design-guideline"></a><span data-ttu-id="56e15-108">Linee guida per la progettazione</span><span class="sxs-lookup"><span data-stu-id="56e15-108">Design guideline</span></span>

<span data-ttu-id="56e15-109">È importante consentire all'utente di concentrarsi e interagire con il contenuto.</span><span class="sxs-lookup"><span data-stu-id="56e15-109">It's important to allow the user to focus and interact with content.</span></span> <span data-ttu-id="56e15-110">La visualizzazione continua della mesh spaziale in background può distrarre.</span><span class="sxs-lookup"><span data-stu-id="56e15-110">Continuous visualization of the spatial mesh in the background can be distracting.</span></span> <span data-ttu-id="56e15-111">È consigliabile visualizzare l'ambiente con parsimonio, una sola volta nel lancio iniziale o quando l'utente mostra chiaramente di voler visualizzare la mesh ambientale selezionando lo spazio di destinazione e toccando l'aria.</span><span class="sxs-lookup"><span data-stu-id="56e15-111">We recommend visualizing the environment sparingly, either only once in the initial launch or when the user clearly shows they want to see the environmental mesh by targeting and air-tapping space.</span></span> <span data-ttu-id="56e15-112">È possibile osservare questo comportamento nel Portale realtà mista.</span><span class="sxs-lookup"><span data-stu-id="56e15-112">You can observe this behavior in the Mixed Reality Portal.</span></span>
<br>

## <a name="spatial-mesh-visualization-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="56e15-113">Visualizzazione della mesh spaziale in MRTK (Mixed Reality Toolkit) per Unity</span><span class="sxs-lookup"><span data-stu-id="56e15-113">Spatial mesh visualization in MRTK (Mixed Reality Toolkit) for Unity</span></span>

<span data-ttu-id="56e15-114">MRTK fornisce diversi materiali per la visualizzazione della mesh spaziale.</span><span class="sxs-lookup"><span data-stu-id="56e15-114">MRTK provides several materials for the spatial mesh visualization.</span></span>

- <span data-ttu-id="56e15-115">**MRTK_Wireframe.mat, MRTK_Wireframe.mat:** materiale mesh spaziale statico predefinito, che mostra i contorni della mesh senza animazione.</span><span class="sxs-lookup"><span data-stu-id="56e15-115">**MRTK_Wireframe.mat, MRTK_Wireframe.mat**: Default static spatial mesh material, which shows the mesh outlines without animation.</span></span> <span data-ttu-id="56e15-116">Questo materiale è utile a scopo di debug perché mostra l'intera geometria della mesh spaziale.</span><span class="sxs-lookup"><span data-stu-id="56e15-116">This material is useful for debugging purposes since it shows the entire spatial mesh geometries.</span></span> <span data-ttu-id="56e15-117">Tuttavia, non è consigliabile per la produzione.</span><span class="sxs-lookup"><span data-stu-id="56e15-117">However, it isn't recommended for production.</span></span>
<br>
<img src="images/SurfaceReconstruction.jpg" alt="Wireframe spatial mesh visualization" width="640px">

- <span data-ttu-id="56e15-118">**MRTK_SurfaceReconstruction.mat:** questo materiale offre un effetto di impulso animato sulla mesh spaziale.</span><span class="sxs-lookup"><span data-stu-id="56e15-118">**MRTK_SurfaceReconstruction.mat**: This material gives you an animated pulse effect on the spatial mesh.</span></span> <span data-ttu-id="56e15-119">È possibile usare questo materiale per visualizzare l'ambiente in un momento specifico o nell'input di tocco dell'utente.</span><span class="sxs-lookup"><span data-stu-id="56e15-119">You can use this material to visualize the environment at a specific moment or on the user's air-tap input.</span></span> <span data-ttu-id="56e15-120">Per **gli esempi, vedere Scena PulseShaderExamples.unity.**</span><span class="sxs-lookup"><span data-stu-id="56e15-120">See **PulseShaderExamples.unity** scene for the examples.</span></span>
<br>
<img src="images/MRTK_SRMesh_Pulse.jpg" alt="Pulse spatial mesh visualization" width="640px">

* <span data-ttu-id="56e15-121">Per altre informazioni, vedere [MRTK - Riconoscimento spaziale](/windows/mixed-reality/mrtk-unity/features/spatial-awareness/spatial-awareness-getting-started) e [MRTK - Pulse Shader.](/windows/mixed-reality/mrtk-unity/features/experimental/pulse-shader)</span><span class="sxs-lookup"><span data-stu-id="56e15-121">For more information, see [MRTK - Spatial Awareness](/windows/mixed-reality/mrtk-unity/features/spatial-awareness/spatial-awareness-getting-started) and [MRTK - Pulse Shader](/windows/mixed-reality/mrtk-unity/features/experimental/pulse-shader).</span></span>

<br>

---

## <a name="see-also"></a><span data-ttu-id="56e15-122">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="56e15-122">See also</span></span>

* [<span data-ttu-id="56e15-123">Cursori</span><span class="sxs-lookup"><span data-stu-id="56e15-123">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="56e15-124">Raggio della mano</span><span class="sxs-lookup"><span data-stu-id="56e15-124">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="56e15-125">Button</span><span class="sxs-lookup"><span data-stu-id="56e15-125">Button</span></span>](button.md)
* [<span data-ttu-id="56e15-126">Oggetto che supporta interazioni</span><span class="sxs-lookup"><span data-stu-id="56e15-126">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="56e15-127">Rettangolo di selezione e barra dell'app</span><span class="sxs-lookup"><span data-stu-id="56e15-127">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="56e15-128">Manipolazione</span><span class="sxs-lookup"><span data-stu-id="56e15-128">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="56e15-129">Menu a mano</span><span class="sxs-lookup"><span data-stu-id="56e15-129">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="56e15-130">Menu adiacente</span><span class="sxs-lookup"><span data-stu-id="56e15-130">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="56e15-131">Raccolta di oggetti</span><span class="sxs-lookup"><span data-stu-id="56e15-131">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="56e15-132">Comando vocale</span><span class="sxs-lookup"><span data-stu-id="56e15-132">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="56e15-133">Tastiera</span><span class="sxs-lookup"><span data-stu-id="56e15-133">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="56e15-134">Descrizione comando</span><span class="sxs-lookup"><span data-stu-id="56e15-134">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="56e15-135">Slate</span><span class="sxs-lookup"><span data-stu-id="56e15-135">Slate</span></span>](slate.md)
* [<span data-ttu-id="56e15-136">Dispositivo di scorrimento</span><span class="sxs-lookup"><span data-stu-id="56e15-136">Slider</span></span>](slider.md)
* [<span data-ttu-id="56e15-137">Shader</span><span class="sxs-lookup"><span data-stu-id="56e15-137">Shader</span></span>](shader.md)
* [<span data-ttu-id="56e15-138">Billboarding e tag-along</span><span class="sxs-lookup"><span data-stu-id="56e15-138">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="56e15-139">Visualizzazione dello stato</span><span class="sxs-lookup"><span data-stu-id="56e15-139">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="56e15-140">Magnetismo di superficie</span><span class="sxs-lookup"><span data-stu-id="56e15-140">Surface magnetism</span></span>](surface-magnetism.md)
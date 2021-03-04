---
title: Visualizzazione Mesh spaziale
description: Informazioni sulle linee guida di progettazione e sulla comprensione dell'ambiente fisico con la visualizzazione Mesh spaziale in MRTK.
author: cre8ivepark
ms.author: dongpark
ms.date: 06/19/2020
ms.topic: article
keywords: Realtà mista, HoloLens, controlli dell'interfaccia utente, interazione, interfaccia utente, UX, progettazione di UX, interfaccia utente spaziale, interazione spaziale, interfaccia utente 3D, UX 3D, auricolare in realtà mista, auricolare di realtà mista di Windows, auricolare della realtà virtuale, HoloLens, MRTK, Toolkit realtà mista
ms.openlocfilehash: 5e8ffbb90b1143cd4e11bf45a889c11c233232df
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/03/2021
ms.locfileid: "101759807"
---
# <a name="spatial-mesh"></a><span data-ttu-id="3d18b-104">Mesh spaziale</span><span class="sxs-lookup"><span data-stu-id="3d18b-104">Spatial mesh</span></span>

![Mesh spaziale](images/MRTK_PulseShader_SpatialMesh.gif)

<span data-ttu-id="3d18b-106">Gli utenti apprenderanno in che modo un dispositivo percepisce e riconosce l'ambiente fisico attraverso la visualizzazione Mesh spaziale.</span><span class="sxs-lookup"><span data-stu-id="3d18b-106">Users learn how a device perceives and understands the physical environment through spatial mesh visualization.</span></span> <span data-ttu-id="3d18b-107">Una visualizzazione Mesh spaziale corretta può creare un'esperienza deliziosa e magica e fornire contesto spaziale.</span><span class="sxs-lookup"><span data-stu-id="3d18b-107">Proper spatial mesh visualization can create a delightful and magical experience while providing spatial context.</span></span>  

## <a name="design-guideline"></a><span data-ttu-id="3d18b-108">Linee guida per la progettazione</span><span class="sxs-lookup"><span data-stu-id="3d18b-108">Design guideline</span></span>

<span data-ttu-id="3d18b-109">È importante consentire all'utente di concentrarsi e interagire con il contenuto.</span><span class="sxs-lookup"><span data-stu-id="3d18b-109">It's important to allow the user to focus and interact with content.</span></span> <span data-ttu-id="3d18b-110">La visualizzazione continua della mesh spaziale in background può essere distrazione.</span><span class="sxs-lookup"><span data-stu-id="3d18b-110">Continuous visualization of the spatial mesh in the background can be distracting.</span></span> <span data-ttu-id="3d18b-111">Si consiglia di visualizzare l'ambiente sporadicamente, solo una volta all'avvio iniziale o quando l'utente mostra chiaramente che desiderano visualizzare la mesh ambientale selezionando lo spazio per l'uso e il tocco di aria.</span><span class="sxs-lookup"><span data-stu-id="3d18b-111">We recommend visualizing the environment sparingly, either only once in the initial launch or when the user clearly shows they want to see the environmental mesh by targeting and air-tapping space.</span></span> <span data-ttu-id="3d18b-112">È possibile osservare questo comportamento nel portale per la realtà mista.</span><span class="sxs-lookup"><span data-stu-id="3d18b-112">You can observe this behavior in the Mixed Reality Portal.</span></span>
<br>

## <a name="spatial-mesh-visualization-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="3d18b-113">Visualizzazione Mesh spaziale in MRTK (Toolkit realtà mista) per Unity</span><span class="sxs-lookup"><span data-stu-id="3d18b-113">Spatial mesh visualization in MRTK (Mixed Reality Toolkit) for Unity</span></span>

<span data-ttu-id="3d18b-114">MRTK fornisce diversi materiali per la visualizzazione Mesh spaziale.</span><span class="sxs-lookup"><span data-stu-id="3d18b-114">MRTK provides several materials for the spatial mesh visualization.</span></span>

- <span data-ttu-id="3d18b-115">**MRTK_Wireframe. mat, MRTK_Wireframe. Mat**: materiale mesh spaziale statico predefinito, che mostra le strutture mesh senza animazione.</span><span class="sxs-lookup"><span data-stu-id="3d18b-115">**MRTK_Wireframe.mat, MRTK_Wireframe.mat**: Default static spatial mesh material, which shows the mesh outlines without animation.</span></span> <span data-ttu-id="3d18b-116">Questo materiale è utile a scopo di debug perché mostra le geometrie dell'intera mesh spaziale.</span><span class="sxs-lookup"><span data-stu-id="3d18b-116">This material is useful for debugging purposes since it shows the entire spatial mesh geometries.</span></span> <span data-ttu-id="3d18b-117">Tuttavia, non è consigliabile per la produzione.</span><span class="sxs-lookup"><span data-stu-id="3d18b-117">However, it isn't recommended for production.</span></span>
<br>
<img src="images/SurfaceReconstruction.jpg" alt="Wireframe spatial mesh visualization" width="640px">

- <span data-ttu-id="3d18b-118">**MRTK_SurfaceReconstruction. Mat**: questo materiale fornisce un effetto a impulsi animati sulla mesh spaziale.</span><span class="sxs-lookup"><span data-stu-id="3d18b-118">**MRTK_SurfaceReconstruction.mat**: This material gives you an animated pulse effect on the spatial mesh.</span></span> <span data-ttu-id="3d18b-119">È possibile usare questo materiale per visualizzare l'ambiente in un momento specifico o in base all'input del rubinetto dell'utente.</span><span class="sxs-lookup"><span data-stu-id="3d18b-119">You can use this material to visualize the environment at a specific moment or on the user's air-tap input.</span></span> <span data-ttu-id="3d18b-120">Vedere la scena **PulseShaderExamples. Unity** per gli esempi.</span><span class="sxs-lookup"><span data-stu-id="3d18b-120">See **PulseShaderExamples.unity** scene for the examples.</span></span>
<br>
<img src="images/MRTK_SRMesh_Pulse.jpg" alt="Pulse spatial mesh visualization" width="640px">
* <span data-ttu-id="3d18b-121">Per altre informazioni, vedere [MRTK-Spatial Awareness](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/spatial-awareness/spatial-awareness-getting-started.md) e [MRTK-Pulse shader](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/experimental/pulse-shader.md).</span><span class="sxs-lookup"><span data-stu-id="3d18b-121">For more information, see [MRTK - Spatial Awareness](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/spatial-awareness/spatial-awareness-getting-started.md) and [MRTK - Pulse Shader](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/experimental/pulse-shader.md).</span></span>

<br>

---

## <a name="see-also"></a><span data-ttu-id="3d18b-122">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="3d18b-122">See also</span></span>

* [<span data-ttu-id="3d18b-123">Cursori</span><span class="sxs-lookup"><span data-stu-id="3d18b-123">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="3d18b-124">Raggio della mano</span><span class="sxs-lookup"><span data-stu-id="3d18b-124">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="3d18b-125">Button</span><span class="sxs-lookup"><span data-stu-id="3d18b-125">Button</span></span>](button.md)
* [<span data-ttu-id="3d18b-126">Oggetto che supporta interazioni</span><span class="sxs-lookup"><span data-stu-id="3d18b-126">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="3d18b-127">Rettangolo di selezione e barra dell'app</span><span class="sxs-lookup"><span data-stu-id="3d18b-127">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="3d18b-128">Manipolazione</span><span class="sxs-lookup"><span data-stu-id="3d18b-128">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="3d18b-129">Menu a mano</span><span class="sxs-lookup"><span data-stu-id="3d18b-129">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="3d18b-130">Menu adiacente</span><span class="sxs-lookup"><span data-stu-id="3d18b-130">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="3d18b-131">Raccolta di oggetti</span><span class="sxs-lookup"><span data-stu-id="3d18b-131">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="3d18b-132">Comando vocale</span><span class="sxs-lookup"><span data-stu-id="3d18b-132">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="3d18b-133">Tastiera</span><span class="sxs-lookup"><span data-stu-id="3d18b-133">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="3d18b-134">Descrizione comando</span><span class="sxs-lookup"><span data-stu-id="3d18b-134">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="3d18b-135">Slate</span><span class="sxs-lookup"><span data-stu-id="3d18b-135">Slate</span></span>](slate.md)
* [<span data-ttu-id="3d18b-136">Dispositivo di scorrimento</span><span class="sxs-lookup"><span data-stu-id="3d18b-136">Slider</span></span>](slider.md)
* [<span data-ttu-id="3d18b-137">Shader</span><span class="sxs-lookup"><span data-stu-id="3d18b-137">Shader</span></span>](shader.md)
* [<span data-ttu-id="3d18b-138">Billboarding e tag-along</span><span class="sxs-lookup"><span data-stu-id="3d18b-138">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="3d18b-139">Visualizzazione dello stato</span><span class="sxs-lookup"><span data-stu-id="3d18b-139">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="3d18b-140">Magnetismo di superficie</span><span class="sxs-lookup"><span data-stu-id="3d18b-140">Surface magnetism</span></span>](surface-magnetism.md)

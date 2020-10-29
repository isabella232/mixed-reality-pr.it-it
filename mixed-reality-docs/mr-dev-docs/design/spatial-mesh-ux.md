---
title: Visualizzazione Mesh spaziale
author: cre8ivepark
ms.author: dongpark
ms.date: 06/19/2020
ms.topic: article
keywords: Realtà mista, HoloLens, controlli dell'interfaccia utente, interazione, interfaccia utente, UX, progettazione di UX, interfaccia utente spaziale, interazione spaziale, interfaccia utente 3D, UX 3D
ms.openlocfilehash: 2c811edc14fbcc7c917fe9fa724f1cab23179a96
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/03/2020
ms.locfileid: "91686092"
---
# <a name="spatial-mesh"></a><span data-ttu-id="50bfe-103">Mesh spaziale</span><span class="sxs-lookup"><span data-stu-id="50bfe-103">Spatial mesh</span></span>

![Mesh spaziale](images/MRTK_PulseShader_SpatialMesh.gif)

<span data-ttu-id="50bfe-105">Attraverso la visualizzazione Mesh spaziale, l'utente può apprendere in che modo un dispositivo percepisce e riconosce l'ambiente fisico.</span><span class="sxs-lookup"><span data-stu-id="50bfe-105">Through the spatial mesh visualization, the user can learn how a device perceives and understands the physical environment.</span></span> <span data-ttu-id="50bfe-106">Oltre a fornire il contesto spaziale, la visualizzazione Mesh spaziale corretta può creare un'esperienza deliziosa e magica.</span><span class="sxs-lookup"><span data-stu-id="50bfe-106">In addition to providing spatial context, proper spatial mesh visualization can create a delightful and magical experience.</span></span>  

## <a name="design-guideline"></a><span data-ttu-id="50bfe-107">Linee guida per la progettazione</span><span class="sxs-lookup"><span data-stu-id="50bfe-107">Design guideline</span></span>
<span data-ttu-id="50bfe-108">Poiché è importante consentire all'utente di concentrarsi e interagire con il contenuto, è possibile che la visualizzazione continua e ripetuta della mesh spaziale in background risulti distrazione.</span><span class="sxs-lookup"><span data-stu-id="50bfe-108">Since it's important to allow the user to focus and interact with content, continuous and repeated visualization of the spatial mesh in the background could be distracting.</span></span> <span data-ttu-id="50bfe-109">Si consiglia di visualizzare l'ambiente in modo sporadico, una sola volta all'avvio iniziale o quando l'utente mostra chiaramente l'intenzione di visualizzare la mesh ambientale selezionando lo spazio di destinazione e il tocco di aria.</span><span class="sxs-lookup"><span data-stu-id="50bfe-109">It is recommended to visualize the environment sparingly, either only once in the initial launch or when the user shows clear intention to see the environmental mesh by targeting and air-tapping space.</span></span> <span data-ttu-id="50bfe-110">È possibile osservare questo comportamento nella shell HoloLens.</span><span class="sxs-lookup"><span data-stu-id="50bfe-110">You can observe this behavior in the HoloLens shell.</span></span>
<br>


## <a name="spatial-mesh-visualization-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="50bfe-111">Visualizzazione Mesh spaziale in MRTK (Toolkit realtà mista) per Unity</span><span class="sxs-lookup"><span data-stu-id="50bfe-111">Spatial mesh visualization in MRTK (Mixed Reality Toolkit) for Unity</span></span>
<span data-ttu-id="50bfe-112">MRTK fornisce diversi materiali per la visualizzazione Mesh spaziale.</span><span class="sxs-lookup"><span data-stu-id="50bfe-112">MRTK provides several materials for the spatial mesh visualization.</span></span>

- <span data-ttu-id="50bfe-113">**MRTK_Wireframe. mat, MRTK_Wireframe. Mat** : materiale mesh spaziale statico predefinito che mostra le strutture mesh senza animazione.</span><span class="sxs-lookup"><span data-stu-id="50bfe-113">**MRTK_Wireframe.mat, MRTK_Wireframe.mat** : Default static spatial mesh material which shows the mesh outlines without animation.</span></span> <span data-ttu-id="50bfe-114">Questo materiale è utile a scopo di debug perché mostra le geometrie dell'intera mesh spaziale.</span><span class="sxs-lookup"><span data-stu-id="50bfe-114">This material is useful for debugging purposes since it shows the entire spatial mesh geometries.</span></span> <span data-ttu-id="50bfe-115">Tuttavia, non è consigliabile per la produzione.</span><span class="sxs-lookup"><span data-stu-id="50bfe-115">However, it is not recommended for production.</span></span>
<br>
<img src="images/SurfaceReconstruction.jpg" alt="Wireframe spatial mesh visualization" width="640px">

- <span data-ttu-id="50bfe-116">**MRTK_SurfaceReconstruction. Mat** : questo materiale fornisce un effetto a impulsi animati sulla mesh spaziale.</span><span class="sxs-lookup"><span data-stu-id="50bfe-116">**MRTK_SurfaceReconstruction.mat** : This material gives you an animated pulse effect on the spatial mesh.</span></span> <span data-ttu-id="50bfe-117">È possibile usare questo materiale per visualizzare l'ambiente in un momento specifico dell'esperienza o in base all'input dell'utente.</span><span class="sxs-lookup"><span data-stu-id="50bfe-117">You can use this material to visualize the environment at a specific moment of your experience or on the user's air-tap input.</span></span> <span data-ttu-id="50bfe-118">Vedere la scena **PulseShaderExamples. Unity** per gli esempi.</span><span class="sxs-lookup"><span data-stu-id="50bfe-118">See **PulseShaderExamples.unity** scene for the examples.</span></span>
<br>
<img src="images/MRTK_SRMesh_Pulse.jpg" alt="Pulse spatial mesh visualization" width="640px">
* <span data-ttu-id="50bfe-119">Per altri dettagli, vedere [MRTK-Spatial Awareness](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/SpatialAwareness/SpatialAwarenessGettingStarted.html) e [MRTK-Pulse shader](https://microsoft.github.io/MixedRealityToolkit-Unity/Assets/MRTK/SDK/Experimental/PulseShader/README.html) .</span><span class="sxs-lookup"><span data-stu-id="50bfe-119">Please see [MRTK - Spatial Awareness](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/SpatialAwareness/SpatialAwarenessGettingStarted.html) and [MRTK - Pulse Shader](https://microsoft.github.io/MixedRealityToolkit-Unity/Assets/MRTK/SDK/Experimental/PulseShader/README.html) for more details.</span></span>

<br>

---

## <a name="see-also"></a><span data-ttu-id="50bfe-120">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="50bfe-120">See also</span></span>

* [<span data-ttu-id="50bfe-121">Cursori</span><span class="sxs-lookup"><span data-stu-id="50bfe-121">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="50bfe-122">Raggio della mano</span><span class="sxs-lookup"><span data-stu-id="50bfe-122">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="50bfe-123">Button</span><span class="sxs-lookup"><span data-stu-id="50bfe-123">Button</span></span>](button.md)
* [<span data-ttu-id="50bfe-124">Oggetto che supporta interazioni</span><span class="sxs-lookup"><span data-stu-id="50bfe-124">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="50bfe-125">Rettangolo di selezione e barra dell'app</span><span class="sxs-lookup"><span data-stu-id="50bfe-125">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="50bfe-126">Manipolazione</span><span class="sxs-lookup"><span data-stu-id="50bfe-126">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="50bfe-127">Menu a mano</span><span class="sxs-lookup"><span data-stu-id="50bfe-127">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="50bfe-128">Menu adiacente</span><span class="sxs-lookup"><span data-stu-id="50bfe-128">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="50bfe-129">Raccolta di oggetti</span><span class="sxs-lookup"><span data-stu-id="50bfe-129">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="50bfe-130">Comando vocale</span><span class="sxs-lookup"><span data-stu-id="50bfe-130">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="50bfe-131">Tastiera</span><span class="sxs-lookup"><span data-stu-id="50bfe-131">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="50bfe-132">Descrizione comando</span><span class="sxs-lookup"><span data-stu-id="50bfe-132">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="50bfe-133">Slate</span><span class="sxs-lookup"><span data-stu-id="50bfe-133">Slate</span></span>](slate.md)
* [<span data-ttu-id="50bfe-134">Dispositivo di scorrimento</span><span class="sxs-lookup"><span data-stu-id="50bfe-134">Slider</span></span>](slider.md)
* [<span data-ttu-id="50bfe-135">Shader</span><span class="sxs-lookup"><span data-stu-id="50bfe-135">Shader</span></span>](shader.md)
* [<span data-ttu-id="50bfe-136">Billboarding e tag-along</span><span class="sxs-lookup"><span data-stu-id="50bfe-136">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="50bfe-137">Visualizzazione dello stato</span><span class="sxs-lookup"><span data-stu-id="50bfe-137">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="50bfe-138">Magnetismo di superficie</span><span class="sxs-lookup"><span data-stu-id="50bfe-138">Surface magnetism</span></span>](surface-magnetism.md)

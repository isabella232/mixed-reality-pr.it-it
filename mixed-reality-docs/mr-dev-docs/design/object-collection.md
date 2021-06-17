---
title: Raccolta di oggetti
description: La raccolta di oggetti è un controllo di layout che consente di definire il layout di una matrice di oggetti in una forma tridimensionale predefinita.
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, controlli, progettazione, visore per realtà mista, visore windows mixed reality, visore per realtà virtuale, HoloLens, raccolta di oggetti, 2D, 3D, MRTK, Mixed Reality Toolkit
ms.openlocfilehash: fd5629f58e092b33410c833885037582ba5ca4a1
ms.sourcegitcommit: c65759b8d6465b6b13925cacab5af74443f7e6bd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/15/2021
ms.locfileid: "112110137"
---
# <a name="object-collection"></a><span data-ttu-id="a8e7b-104">Raccolta di oggetti</span><span class="sxs-lookup"><span data-stu-id="a8e7b-104">Object collection</span></span>

![Raccolta di oggetti usata nella tabella periodica dell'app Elements](images/UX_Hero_ObjectCollection.jpg)<br>

<span data-ttu-id="a8e7b-106">La raccolta di oggetti è un controllo di layout che consente di definire il layout di una matrice di oggetti in una forma tridimensionale predefinita.</span><span class="sxs-lookup"><span data-stu-id="a8e7b-106">Object collection is a layout control, which helps you lay out an array of objects in a predefined three-dimensional shape.</span></span> <span data-ttu-id="a8e7b-107">Supporta vari stili di superficie: \*\*piano, cilindro, sfera e **radiale.**</span><span class="sxs-lookup"><span data-stu-id="a8e7b-107">It supports various surface styles - \*\*plane, cylinder, sphere, and **radial**.</span></span> <span data-ttu-id="a8e7b-108">È possibile regolare il raggio e le dimensioni degli oggetti e lo spazio tra di essi.</span><span class="sxs-lookup"><span data-stu-id="a8e7b-108">You can adjust the radius and size of the objects and the space between them.</span></span> <span data-ttu-id="a8e7b-109">La raccolta di oggetti supporta qualsiasi oggetto di Unity, sia 2D che 3D.</span><span class="sxs-lookup"><span data-stu-id="a8e7b-109">Object collection supports any object from Unity - both 2D and 3D.</span></span> <span data-ttu-id="a8e7b-110">In **[Mixed Reality Toolkit](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/object-collection)** sono stati creati script ed esempi di Unity che consentono di creare una raccolta di oggetti.</span><span class="sxs-lookup"><span data-stu-id="a8e7b-110">In the **[Mixed Reality Toolkit](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/object-collection)**, we have created Unity script and examples that will help you create an object collection.</span></span>

## <a name="object-collection-examples"></a><span data-ttu-id="a8e7b-111">Esempi di raccolta di oggetti</span><span class="sxs-lookup"><span data-stu-id="a8e7b-111">Object collection examples</span></span>

<span data-ttu-id="a8e7b-112">[La tabella periodica degli elementi è](../develop/unity/periodic-table-of-the-elements.md) un'app di esempio che illustra il funzionamento della raccolta di oggetti.</span><span class="sxs-lookup"><span data-stu-id="a8e7b-112">[Periodic Table of the Elements](../develop/unity/periodic-table-of-the-elements.md) is a sample app that demonstrates how Object collection works.</span></span> <span data-ttu-id="a8e7b-113">Usa la raccolta Object per impostare il disaserzione delle caselle degli elementi 3D in forme diverse.</span><span class="sxs-lookup"><span data-stu-id="a8e7b-113">It uses Object collection to lay out 3D chemical element boxes in different shapes.</span></span>

<span data-ttu-id="a8e7b-114">![Esempi di raccolta di oggetti illustrati nella tabella periodica dell'app Elements](images/periodictable-collections-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="a8e7b-114">![Object collection examples shown in the Periodic Table of the Elements app](images/periodictable-collections-1000px.jpg)</span></span><br>
<span data-ttu-id="a8e7b-115">*Esempi di raccolta di oggetti illustrati nella tabella periodica dell'app di esempio Elements*</span><span class="sxs-lookup"><span data-stu-id="a8e7b-115">*Object collection examples shown in the Periodic Table of the Elements sample app*</span></span>

### <a name="3d-objects"></a><span data-ttu-id="a8e7b-116">Oggetti 3D</span><span class="sxs-lookup"><span data-stu-id="a8e7b-116">3D objects</span></span>

<span data-ttu-id="a8e7b-117">È possibile usare la raccolta di oggetti per eseguire il disaser di oggetti 3D importati.</span><span class="sxs-lookup"><span data-stu-id="a8e7b-117">You can use Object collection to lay out imported 3D objects.</span></span> <span data-ttu-id="a8e7b-118">L'esempio seguente mostra un piano e un layout a cilindro di alcuni oggetti cattedra 3D.</span><span class="sxs-lookup"><span data-stu-id="a8e7b-118">The example below shows a plane and a cylinder layout of some 3D chair objects.</span></span>

<span data-ttu-id="a8e7b-119">![Esempi di layout di piano e cilindrico di oggetti 3D](images/objectcollection-3dobjects-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="a8e7b-119">![Examples of plane and cylindrical layouts of 3D objects](images/objectcollection-3dobjects-1000px.jpg)</span></span><br>
<span data-ttu-id="a8e7b-120">*Esempi di layout di piano e cilindrico di oggetti 3D*</span><span class="sxs-lookup"><span data-stu-id="a8e7b-120">*Examples of plane and cylindrical layouts of 3D objects*</span></span>

### <a name="2d-objects"></a><span data-ttu-id="a8e7b-121">Oggetti 2D</span><span class="sxs-lookup"><span data-stu-id="a8e7b-121">2D objects</span></span>

<span data-ttu-id="a8e7b-122">È anche possibile usare immagini 2D con la raccolta di oggetti.</span><span class="sxs-lookup"><span data-stu-id="a8e7b-122">You can also use 2D images with Object collection.</span></span> <span data-ttu-id="a8e7b-123">Gli esempi seguenti illustrano come visualizzare le immagini 2D in una griglia.</span><span class="sxs-lookup"><span data-stu-id="a8e7b-123">The examples below demonstrate how 2D images can be displayed in a grid.</span></span>

![Esempio di immagini 2D con raccolta Di oggetti](images/940px-layout-3dobjects-3.jpg)

<span data-ttu-id="a8e7b-125">![Esempi di utilizzo della raccolta di oggetti con immagini 2D](images/940px-layout-2dimages.jpg)</span><span class="sxs-lookup"><span data-stu-id="a8e7b-125">![Examples of using object collection with 2D images](images/940px-layout-2dimages.jpg)</span></span><br>
<span data-ttu-id="a8e7b-126">*Esempi di utilizzo della raccolta di oggetti con immagini 2D*</span><span class="sxs-lookup"><span data-stu-id="a8e7b-126">*Examples of using object collection with 2D images*</span></span>

<br>

---

## <a name="object-collection-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="a8e7b-127">Raccolta di oggetti in MRTK (Mixed Reality Toolkit) per Unity</span><span class="sxs-lookup"><span data-stu-id="a8e7b-127">Object collection in MRTK (Mixed Reality Toolkit) for Unity</span></span>

* [<span data-ttu-id="a8e7b-128">MRTK - Raccolta di oggetti</span><span class="sxs-lookup"><span data-stu-id="a8e7b-128">MRTK - Object collection</span></span>](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/object-collection)

<br>

---

## <a name="see-also"></a><span data-ttu-id="a8e7b-129">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="a8e7b-129">See also</span></span>

* [<span data-ttu-id="a8e7b-130">Cursori</span><span class="sxs-lookup"><span data-stu-id="a8e7b-130">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="a8e7b-131">Raggio della mano</span><span class="sxs-lookup"><span data-stu-id="a8e7b-131">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="a8e7b-132">Button</span><span class="sxs-lookup"><span data-stu-id="a8e7b-132">Button</span></span>](button.md)
* [<span data-ttu-id="a8e7b-133">Oggetto che supporta interazioni</span><span class="sxs-lookup"><span data-stu-id="a8e7b-133">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="a8e7b-134">Rettangolo di selezione e barra dell'app</span><span class="sxs-lookup"><span data-stu-id="a8e7b-134">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="a8e7b-135">Manipolazione</span><span class="sxs-lookup"><span data-stu-id="a8e7b-135">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="a8e7b-136">Menu a mano</span><span class="sxs-lookup"><span data-stu-id="a8e7b-136">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="a8e7b-137">Menu adiacente</span><span class="sxs-lookup"><span data-stu-id="a8e7b-137">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="a8e7b-138">Raccolta di oggetti</span><span class="sxs-lookup"><span data-stu-id="a8e7b-138">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="a8e7b-139">Comando vocale</span><span class="sxs-lookup"><span data-stu-id="a8e7b-139">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="a8e7b-140">Tastiera</span><span class="sxs-lookup"><span data-stu-id="a8e7b-140">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="a8e7b-141">Descrizione comando</span><span class="sxs-lookup"><span data-stu-id="a8e7b-141">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="a8e7b-142">Slate</span><span class="sxs-lookup"><span data-stu-id="a8e7b-142">Slate</span></span>](slate.md)
* [<span data-ttu-id="a8e7b-143">Dispositivo di scorrimento</span><span class="sxs-lookup"><span data-stu-id="a8e7b-143">Slider</span></span>](slider.md)
* [<span data-ttu-id="a8e7b-144">Shader</span><span class="sxs-lookup"><span data-stu-id="a8e7b-144">Shader</span></span>](shader.md)
* [<span data-ttu-id="a8e7b-145">Billboarding e tag-along</span><span class="sxs-lookup"><span data-stu-id="a8e7b-145">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="a8e7b-146">Visualizzazione dello stato</span><span class="sxs-lookup"><span data-stu-id="a8e7b-146">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="a8e7b-147">Magnetismo di superficie</span><span class="sxs-lookup"><span data-stu-id="a8e7b-147">Surface magnetism</span></span>](surface-magnetism.md)
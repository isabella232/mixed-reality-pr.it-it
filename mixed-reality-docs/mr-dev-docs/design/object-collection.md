---
title: Raccolta di oggetti
description: La raccolta di oggetti è un controllo di layout che consente di definire il layout di una matrice di oggetti in una forma tridimensionale predefinita.
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, controlli, progettazione, visore VR di realtà mista, visore VR di realtà mista windows, visore VR di realtà virtuale, HoloLens, raccolta di oggetti, 2D, 3D, MRTK, Mixed Reality Toolkit
ms.openlocfilehash: 9648f3bd22a09c53de2f903ed8ba0274c634db7c
ms.sourcegitcommit: 9ae76b339968f035c703d9c1fe57ddecb33198e3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/27/2021
ms.locfileid: "110600200"
---
# <a name="object-collection"></a><span data-ttu-id="036c7-104">Raccolta di oggetti</span><span class="sxs-lookup"><span data-stu-id="036c7-104">Object collection</span></span>

![Raccolta di oggetti usata nella tabella periodica dell'app Elements](images/UX_Hero_ObjectCollection.jpg)<br>

<span data-ttu-id="036c7-106">La raccolta di oggetti è un controllo di layout che consente di definire il layout di una matrice di oggetti in una forma tridimensionale predefinita.</span><span class="sxs-lookup"><span data-stu-id="036c7-106">Object collection is a layout control, which helps you lay out an array of objects in a predefined three-dimensional shape.</span></span> <span data-ttu-id="036c7-107">Supporta vari stili di superficie: \*\*piano, cilindro, sfera e **radiale.**</span><span class="sxs-lookup"><span data-stu-id="036c7-107">It supports various surface styles - \*\*plane, cylinder, sphere, and **radial**.</span></span> <span data-ttu-id="036c7-108">È possibile regolare il raggio e le dimensioni degli oggetti e lo spazio tra di essi.</span><span class="sxs-lookup"><span data-stu-id="036c7-108">You can adjust the radius and size of the objects and the space between them.</span></span> <span data-ttu-id="036c7-109">La raccolta di oggetti supporta qualsiasi oggetto di Unity, sia 2D che 3D.</span><span class="sxs-lookup"><span data-stu-id="036c7-109">Object collection supports any object from Unity - both 2D and 3D.</span></span> <span data-ttu-id="036c7-110">In **[Mixed Reality Toolkit](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectCollection.html)** sono stati creati script ed esempi di Unity che consentono di creare una raccolta di oggetti.</span><span class="sxs-lookup"><span data-stu-id="036c7-110">In the **[Mixed Reality Toolkit](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectCollection.html)**, we have created Unity script and examples that will help you create an object collection.</span></span>

## <a name="object-collection-examples"></a><span data-ttu-id="036c7-111">Esempi di raccolte di oggetti</span><span class="sxs-lookup"><span data-stu-id="036c7-111">Object collection examples</span></span>

<span data-ttu-id="036c7-112">[La tabella periodica degli elementi è un'app](../develop/unity/periodic-table-of-the-elements.md) di esempio che illustra il funzionamento della raccolta di oggetti.</span><span class="sxs-lookup"><span data-stu-id="036c7-112">[Periodic Table of the Elements](../develop/unity/periodic-table-of-the-elements.md) is a sample app that demonstrates how Object collection works.</span></span> <span data-ttu-id="036c7-113">Usa la raccolta di oggetti per creare il sistema di caselle degli elementi chimica 3D in forme diverse.</span><span class="sxs-lookup"><span data-stu-id="036c7-113">It uses Object collection to lay out 3D chemical element boxes in different shapes.</span></span>

<span data-ttu-id="036c7-114">![Esempi di raccolta di oggetti illustrati nella tabella periodica dell'app Elements](images/periodictable-collections-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="036c7-114">![Object collection examples shown in the Periodic Table of the Elements app](images/periodictable-collections-1000px.jpg)</span></span><br>
<span data-ttu-id="036c7-115">*Esempi di raccolta di oggetti illustrati nella tabella periodica dell'app di esempio Elements*</span><span class="sxs-lookup"><span data-stu-id="036c7-115">*Object collection examples shown in the Periodic Table of the Elements sample app*</span></span>

### <a name="3d-objects"></a><span data-ttu-id="036c7-116">Oggetti 3D</span><span class="sxs-lookup"><span data-stu-id="036c7-116">3D objects</span></span>

<span data-ttu-id="036c7-117">È possibile usare La raccolta di oggetti per impostare il timeout degli oggetti 3D importati.</span><span class="sxs-lookup"><span data-stu-id="036c7-117">You can use Object collection to lay out imported 3D objects.</span></span> <span data-ttu-id="036c7-118">L'esempio seguente mostra un piano e un layout a cilindro di alcuni oggetti 3D.</span><span class="sxs-lookup"><span data-stu-id="036c7-118">The example below shows a plane and a cylinder layout of some 3D chair objects.</span></span>

<span data-ttu-id="036c7-119">![Esempi di layout di piano e ciclici di oggetti 3D](images/objectcollection-3dobjects-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="036c7-119">![Examples of plane and cylindrical layouts of 3D objects](images/objectcollection-3dobjects-1000px.jpg)</span></span><br>
<span data-ttu-id="036c7-120">*Esempi di layout di piano e ciclici di oggetti 3D*</span><span class="sxs-lookup"><span data-stu-id="036c7-120">*Examples of plane and cylindrical layouts of 3D objects*</span></span>

### <a name="2d-objects"></a><span data-ttu-id="036c7-121">Oggetti 2D</span><span class="sxs-lookup"><span data-stu-id="036c7-121">2D objects</span></span>

<span data-ttu-id="036c7-122">È anche possibile usare immagini 2D con La raccolta di oggetti.</span><span class="sxs-lookup"><span data-stu-id="036c7-122">You can also use 2D images with Object collection.</span></span> <span data-ttu-id="036c7-123">Gli esempi seguenti illustrano come visualizzare le immagini 2D in una griglia.</span><span class="sxs-lookup"><span data-stu-id="036c7-123">The examples below demonstrate how 2D images can be displayed in a grid.</span></span>

![Esempio di immagini 2D con raccolta di oggetti](images/940px-layout-3dobjects-3.jpg)

<span data-ttu-id="036c7-125">![Esempi di uso della raccolta di oggetti con immagini 2D](images/940px-layout-2dimages.jpg)</span><span class="sxs-lookup"><span data-stu-id="036c7-125">![Examples of using object collection with 2D images](images/940px-layout-2dimages.jpg)</span></span><br>
<span data-ttu-id="036c7-126">*Esempi di uso della raccolta di oggetti con immagini 2D*</span><span class="sxs-lookup"><span data-stu-id="036c7-126">*Examples of using object collection with 2D images*</span></span>

<br>

---

## <a name="object-collection-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="036c7-127">Raccolta di oggetti in MRTK (Mixed Reality Toolkit) per Unity</span><span class="sxs-lookup"><span data-stu-id="036c7-127">Object collection in MRTK (Mixed Reality Toolkit) for Unity</span></span>

* [<span data-ttu-id="036c7-128">MRTK - Raccolta di oggetti</span><span class="sxs-lookup"><span data-stu-id="036c7-128">MRTK - Object collection</span></span>](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/object-collection)

<br>

---

## <a name="see-also"></a><span data-ttu-id="036c7-129">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="036c7-129">See also</span></span>

* [<span data-ttu-id="036c7-130">Cursori</span><span class="sxs-lookup"><span data-stu-id="036c7-130">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="036c7-131">Raggio della mano</span><span class="sxs-lookup"><span data-stu-id="036c7-131">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="036c7-132">Button</span><span class="sxs-lookup"><span data-stu-id="036c7-132">Button</span></span>](button.md)
* [<span data-ttu-id="036c7-133">Oggetto che supporta interazioni</span><span class="sxs-lookup"><span data-stu-id="036c7-133">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="036c7-134">Rettangolo di selezione e barra dell'app</span><span class="sxs-lookup"><span data-stu-id="036c7-134">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="036c7-135">Manipolazione</span><span class="sxs-lookup"><span data-stu-id="036c7-135">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="036c7-136">Menu a mano</span><span class="sxs-lookup"><span data-stu-id="036c7-136">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="036c7-137">Menu adiacente</span><span class="sxs-lookup"><span data-stu-id="036c7-137">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="036c7-138">Raccolta di oggetti</span><span class="sxs-lookup"><span data-stu-id="036c7-138">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="036c7-139">Comando vocale</span><span class="sxs-lookup"><span data-stu-id="036c7-139">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="036c7-140">Tastiera</span><span class="sxs-lookup"><span data-stu-id="036c7-140">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="036c7-141">Descrizione comando</span><span class="sxs-lookup"><span data-stu-id="036c7-141">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="036c7-142">Slate</span><span class="sxs-lookup"><span data-stu-id="036c7-142">Slate</span></span>](slate.md)
* [<span data-ttu-id="036c7-143">Dispositivo di scorrimento</span><span class="sxs-lookup"><span data-stu-id="036c7-143">Slider</span></span>](slider.md)
* [<span data-ttu-id="036c7-144">Shader</span><span class="sxs-lookup"><span data-stu-id="036c7-144">Shader</span></span>](shader.md)
* [<span data-ttu-id="036c7-145">Billboarding e tag-along</span><span class="sxs-lookup"><span data-stu-id="036c7-145">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="036c7-146">Visualizzazione dello stato</span><span class="sxs-lookup"><span data-stu-id="036c7-146">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="036c7-147">Magnetismo di superficie</span><span class="sxs-lookup"><span data-stu-id="036c7-147">Surface magnetism</span></span>](surface-magnetism.md)
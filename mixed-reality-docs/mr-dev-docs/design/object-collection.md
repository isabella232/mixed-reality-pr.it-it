---
title: Raccolta di oggetti
description: La raccolta di oggetti è un controllo di layout che consente di disporre una matrice di oggetti in una forma tridimensionale predefinita.
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Realtà mista di Windows, controlli, progettazione, cuffie per realtà mista, cuffie per realtà mista di Windows, headset di realtà virtuale, HoloLens, raccolta di oggetti, 2D, 3D, MRTK, Toolkit reality
ms.openlocfilehash: a459d03246b8df4c17d523f57ece54997849c209
ms.sourcegitcommit: d340303cda71c31e6c3320231473d623c0930d33
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/01/2021
ms.locfileid: "97847211"
---
# <a name="object-collection"></a><span data-ttu-id="6b108-104">Raccolta di oggetti</span><span class="sxs-lookup"><span data-stu-id="6b108-104">Object collection</span></span>

![Raccolta di oggetti usata nella tabella periodica dell'app elementi](images/UX_Hero_ObjectCollection.jpg)<br>

<span data-ttu-id="6b108-106">La raccolta di oggetti è un controllo di layout che consente di disporre una matrice di oggetti in una forma tridimensionale predefinita.</span><span class="sxs-lookup"><span data-stu-id="6b108-106">Object collection is a layout control, which helps you lay out an array of objects in a predefined three-dimensional shape.</span></span> <span data-ttu-id="6b108-107">Supporta diversi stili di superficie: \* \* piano, cilindro, sfera e **radiale**.</span><span class="sxs-lookup"><span data-stu-id="6b108-107">It supports various surface styles - \*\*plane, cylinder, sphere, and **radial**.</span></span> <span data-ttu-id="6b108-108">È possibile regolare il raggio e le dimensioni degli oggetti e lo spazio tra di essi.</span><span class="sxs-lookup"><span data-stu-id="6b108-108">You can adjust the radius and size of the objects and the space between them.</span></span> <span data-ttu-id="6b108-109">La raccolta di oggetti supporta qualsiasi oggetto da Unity, sia 2D che 3D.</span><span class="sxs-lookup"><span data-stu-id="6b108-109">Object collection supports any object from Unity - both 2D and 3D.</span></span> <span data-ttu-id="6b108-110">Nel **[Toolkit di realtà mista](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectCollection.html)** abbiamo creato script Unity ed esempi che consentiranno di creare una raccolta di oggetti.</span><span class="sxs-lookup"><span data-stu-id="6b108-110">In the **[Mixed Reality Toolkit](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectCollection.html)**, we have created Unity script and examples that will help you create an object collection.</span></span>

## <a name="object-collection-examples"></a><span data-ttu-id="6b108-111">Esempi di raccolta di oggetti</span><span class="sxs-lookup"><span data-stu-id="6b108-111">Object collection examples</span></span>

<span data-ttu-id="6b108-112">[La tabella periodica degli elementi](../develop/unity/periodic-table-of-the-elements.md) è un'applicazione di esempio che illustra il funzionamento della raccolta di oggetti.</span><span class="sxs-lookup"><span data-stu-id="6b108-112">[Periodic Table of the Elements](../develop/unity/periodic-table-of-the-elements.md) is a sample app that demonstrates how Object collection works.</span></span> <span data-ttu-id="6b108-113">Usa la raccolta di oggetti per disporre le caselle di elementi chimici 3D in forme diverse.</span><span class="sxs-lookup"><span data-stu-id="6b108-113">It uses Object collection to lay out 3D chemical element boxes in different shapes.</span></span>

<span data-ttu-id="6b108-114">![Esempi di raccolta di oggetti illustrati nella tabella periodica dell'app elementi](images/periodictable-collections-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="6b108-114">![Object collection examples shown in the Periodic Table of the Elements app](images/periodictable-collections-1000px.jpg)</span></span><br>
<span data-ttu-id="6b108-115">*Esempi di raccolta di oggetti illustrati nella tabella periodica dell'app di esempio Elements*</span><span class="sxs-lookup"><span data-stu-id="6b108-115">*Object collection examples shown in the Periodic Table of the Elements sample app*</span></span>

### <a name="3d-objects"></a><span data-ttu-id="6b108-116">oggetti 3D</span><span class="sxs-lookup"><span data-stu-id="6b108-116">3D objects</span></span>

<span data-ttu-id="6b108-117">È possibile usare la raccolta di oggetti per il layout degli oggetti 3D importati.</span><span class="sxs-lookup"><span data-stu-id="6b108-117">You can use Object collection to lay out imported 3D objects.</span></span> <span data-ttu-id="6b108-118">Nell'esempio seguente viene illustrato un piano e un layout cilindrico di alcuni oggetti della poltrona 3D.</span><span class="sxs-lookup"><span data-stu-id="6b108-118">The example below shows a plane and a cylinder layout of some 3D chair objects.</span></span>

<span data-ttu-id="6b108-119">![Esempi di layout piano e cilindrico degli oggetti 3D](images/objectcollection-3dobjects-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="6b108-119">![Examples of plane and cylindrical layouts of 3D objects](images/objectcollection-3dobjects-1000px.jpg)</span></span><br>
<span data-ttu-id="6b108-120">*Esempi di layout piano e cilindrico degli oggetti 3D*</span><span class="sxs-lookup"><span data-stu-id="6b108-120">*Examples of plane and cylindrical layouts of 3D objects*</span></span>

### <a name="2d-objects"></a><span data-ttu-id="6b108-121">oggetti 2D</span><span class="sxs-lookup"><span data-stu-id="6b108-121">2D objects</span></span>

<span data-ttu-id="6b108-122">È anche possibile usare immagini 2D con la raccolta di oggetti.</span><span class="sxs-lookup"><span data-stu-id="6b108-122">You can also use 2D images with Object collection.</span></span> <span data-ttu-id="6b108-123">Gli esempi seguenti illustrano in che modo le immagini 2D possono essere visualizzate in una griglia.</span><span class="sxs-lookup"><span data-stu-id="6b108-123">The examples below demonstrate how 2D images can be displayed in a grid.</span></span>

![Esempio di immagini 2D con raccolta di oggetti](images/940px-layout-3dobjects-3.jpg)

<span data-ttu-id="6b108-125">![Esempi di utilizzo della raccolta di oggetti con immagini 2D](images/940px-layout-2dimages.jpg)</span><span class="sxs-lookup"><span data-stu-id="6b108-125">![Examples of using object collection with 2D images](images/940px-layout-2dimages.jpg)</span></span><br>
<span data-ttu-id="6b108-126">*Esempi di utilizzo della raccolta di oggetti con immagini 2D*</span><span class="sxs-lookup"><span data-stu-id="6b108-126">*Examples of using object collection with 2D images*</span></span>

<br>

---

## <a name="object-collection-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="6b108-127">Raccolta di oggetti in MRTK (Mixed Reality Toolkit) per Unity</span><span class="sxs-lookup"><span data-stu-id="6b108-127">Object collection in MRTK (Mixed Reality Toolkit) for Unity</span></span>

* [<span data-ttu-id="6b108-128">MRTK-raccolta di oggetti</span><span class="sxs-lookup"><span data-stu-id="6b108-128">MRTK - Object collection</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectCollection.html)

<br>

---

## <a name="see-also"></a><span data-ttu-id="6b108-129">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="6b108-129">See also</span></span>

* [<span data-ttu-id="6b108-130">Cursori</span><span class="sxs-lookup"><span data-stu-id="6b108-130">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="6b108-131">Raggio della mano</span><span class="sxs-lookup"><span data-stu-id="6b108-131">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="6b108-132">Button</span><span class="sxs-lookup"><span data-stu-id="6b108-132">Button</span></span>](button.md)
* [<span data-ttu-id="6b108-133">Oggetto che supporta interazioni</span><span class="sxs-lookup"><span data-stu-id="6b108-133">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="6b108-134">Rettangolo di selezione e barra dell'app</span><span class="sxs-lookup"><span data-stu-id="6b108-134">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="6b108-135">Manipolazione</span><span class="sxs-lookup"><span data-stu-id="6b108-135">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="6b108-136">Menu a mano</span><span class="sxs-lookup"><span data-stu-id="6b108-136">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="6b108-137">Menu adiacente</span><span class="sxs-lookup"><span data-stu-id="6b108-137">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="6b108-138">Raccolta di oggetti</span><span class="sxs-lookup"><span data-stu-id="6b108-138">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="6b108-139">Comando vocale</span><span class="sxs-lookup"><span data-stu-id="6b108-139">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="6b108-140">Tastiera</span><span class="sxs-lookup"><span data-stu-id="6b108-140">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="6b108-141">Descrizione comando</span><span class="sxs-lookup"><span data-stu-id="6b108-141">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="6b108-142">Slate</span><span class="sxs-lookup"><span data-stu-id="6b108-142">Slate</span></span>](slate.md)
* [<span data-ttu-id="6b108-143">Dispositivo di scorrimento</span><span class="sxs-lookup"><span data-stu-id="6b108-143">Slider</span></span>](slider.md)
* [<span data-ttu-id="6b108-144">Shader</span><span class="sxs-lookup"><span data-stu-id="6b108-144">Shader</span></span>](shader.md)
* [<span data-ttu-id="6b108-145">Billboarding e tag-along</span><span class="sxs-lookup"><span data-stu-id="6b108-145">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="6b108-146">Visualizzazione dello stato</span><span class="sxs-lookup"><span data-stu-id="6b108-146">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="6b108-147">Magnetismo di superficie</span><span class="sxs-lookup"><span data-stu-id="6b108-147">Surface magnetism</span></span>](surface-magnetism.md)

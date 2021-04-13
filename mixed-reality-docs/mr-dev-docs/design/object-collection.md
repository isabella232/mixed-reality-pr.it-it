---
title: Raccolta di oggetti
description: La raccolta di oggetti è un controllo di layout che consente di disporre una matrice di oggetti in una forma tridimensionale predefinita.
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Realtà mista di Windows, controlli, progettazione, cuffie per realtà mista, cuffie per realtà mista di Windows, headset di realtà virtuale, HoloLens, raccolta di oggetti, 2D, 3D, MRTK, Toolkit reality
ms.openlocfilehash: 109dcd59a2b52a8eec82096c5aa88cd1070f5649
ms.sourcegitcommit: 1c9035487270af76c6eaba11b11f6fc56c008135
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/13/2021
ms.locfileid: "107299726"
---
# <a name="object-collection"></a><span data-ttu-id="f46da-104">Raccolta di oggetti</span><span class="sxs-lookup"><span data-stu-id="f46da-104">Object collection</span></span>

![Raccolta di oggetti usata nella tabella periodica dell'app elementi](images/UX_Hero_ObjectCollection.jpg)<br>

<span data-ttu-id="f46da-106">La raccolta di oggetti è un controllo di layout che consente di disporre una matrice di oggetti in una forma tridimensionale predefinita.</span><span class="sxs-lookup"><span data-stu-id="f46da-106">Object collection is a layout control, which helps you lay out an array of objects in a predefined three-dimensional shape.</span></span> <span data-ttu-id="f46da-107">Supporta diversi stili di superficie: \* \* piano, cilindro, sfera e **radiale**.</span><span class="sxs-lookup"><span data-stu-id="f46da-107">It supports various surface styles - \*\*plane, cylinder, sphere, and **radial**.</span></span> <span data-ttu-id="f46da-108">È possibile regolare il raggio e le dimensioni degli oggetti e lo spazio tra di essi.</span><span class="sxs-lookup"><span data-stu-id="f46da-108">You can adjust the radius and size of the objects and the space between them.</span></span> <span data-ttu-id="f46da-109">La raccolta di oggetti supporta qualsiasi oggetto da Unity, sia 2D che 3D.</span><span class="sxs-lookup"><span data-stu-id="f46da-109">Object collection supports any object from Unity - both 2D and 3D.</span></span> <span data-ttu-id="f46da-110">Nel **[Toolkit di realtà mista](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectCollection.html)** abbiamo creato script Unity ed esempi che consentiranno di creare una raccolta di oggetti.</span><span class="sxs-lookup"><span data-stu-id="f46da-110">In the **[Mixed Reality Toolkit](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectCollection.html)**, we have created Unity script and examples that will help you create an object collection.</span></span>

## <a name="object-collection-examples"></a><span data-ttu-id="f46da-111">Esempi di raccolta di oggetti</span><span class="sxs-lookup"><span data-stu-id="f46da-111">Object collection examples</span></span>

<span data-ttu-id="f46da-112">[La tabella periodica degli elementi](../develop/unity/periodic-table-of-the-elements.md) è un'applicazione di esempio che illustra il funzionamento della raccolta di oggetti.</span><span class="sxs-lookup"><span data-stu-id="f46da-112">[Periodic Table of the Elements](../develop/unity/periodic-table-of-the-elements.md) is a sample app that demonstrates how Object collection works.</span></span> <span data-ttu-id="f46da-113">Usa la raccolta di oggetti per disporre le caselle di elementi chimici 3D in forme diverse.</span><span class="sxs-lookup"><span data-stu-id="f46da-113">It uses Object collection to lay out 3D chemical element boxes in different shapes.</span></span>

<span data-ttu-id="f46da-114">![Esempi di raccolta di oggetti illustrati nella tabella periodica dell'app elementi](images/periodictable-collections-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="f46da-114">![Object collection examples shown in the Periodic Table of the Elements app](images/periodictable-collections-1000px.jpg)</span></span><br>
<span data-ttu-id="f46da-115">*Esempi di raccolta di oggetti illustrati nella tabella periodica dell'app di esempio Elements*</span><span class="sxs-lookup"><span data-stu-id="f46da-115">*Object collection examples shown in the Periodic Table of the Elements sample app*</span></span>

### <a name="3d-objects"></a><span data-ttu-id="f46da-116">oggetti 3D</span><span class="sxs-lookup"><span data-stu-id="f46da-116">3D objects</span></span>

<span data-ttu-id="f46da-117">È possibile usare la raccolta di oggetti per il layout degli oggetti 3D importati.</span><span class="sxs-lookup"><span data-stu-id="f46da-117">You can use Object collection to lay out imported 3D objects.</span></span> <span data-ttu-id="f46da-118">Nell'esempio seguente viene illustrato un piano e un layout cilindrico di alcuni oggetti della poltrona 3D.</span><span class="sxs-lookup"><span data-stu-id="f46da-118">The example below shows a plane and a cylinder layout of some 3D chair objects.</span></span>

<span data-ttu-id="f46da-119">![Esempi di layout piano e cilindrico degli oggetti 3D](images/objectcollection-3dobjects-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="f46da-119">![Examples of plane and cylindrical layouts of 3D objects](images/objectcollection-3dobjects-1000px.jpg)</span></span><br>
<span data-ttu-id="f46da-120">*Esempi di layout piano e cilindrico degli oggetti 3D*</span><span class="sxs-lookup"><span data-stu-id="f46da-120">*Examples of plane and cylindrical layouts of 3D objects*</span></span>

### <a name="2d-objects"></a><span data-ttu-id="f46da-121">oggetti 2D</span><span class="sxs-lookup"><span data-stu-id="f46da-121">2D objects</span></span>

<span data-ttu-id="f46da-122">È anche possibile usare immagini 2D con la raccolta di oggetti.</span><span class="sxs-lookup"><span data-stu-id="f46da-122">You can also use 2D images with Object collection.</span></span> <span data-ttu-id="f46da-123">Gli esempi seguenti illustrano in che modo le immagini 2D possono essere visualizzate in una griglia.</span><span class="sxs-lookup"><span data-stu-id="f46da-123">The examples below demonstrate how 2D images can be displayed in a grid.</span></span>

![Esempio di immagini 2D con raccolta di oggetti](images/940px-layout-3dobjects-3.jpg)

<span data-ttu-id="f46da-125">![Esempi di utilizzo della raccolta di oggetti con immagini 2D](images/940px-layout-2dimages.jpg)</span><span class="sxs-lookup"><span data-stu-id="f46da-125">![Examples of using object collection with 2D images](images/940px-layout-2dimages.jpg)</span></span><br>
<span data-ttu-id="f46da-126">*Esempi di utilizzo della raccolta di oggetti con immagini 2D*</span><span class="sxs-lookup"><span data-stu-id="f46da-126">*Examples of using object collection with 2D images*</span></span>

<br>

---

## <a name="object-collection-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="f46da-127">Raccolta di oggetti in MRTK (Mixed Reality Toolkit) per Unity</span><span class="sxs-lookup"><span data-stu-id="f46da-127">Object collection in MRTK (Mixed Reality Toolkit) for Unity</span></span>

* [<span data-ttu-id="f46da-128">MRTK-raccolta di oggetti</span><span class="sxs-lookup"><span data-stu-id="f46da-128">MRTK - Object collection</span></span>](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/object-collection)

<br>

---

## <a name="see-also"></a><span data-ttu-id="f46da-129">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="f46da-129">See also</span></span>

* [<span data-ttu-id="f46da-130">Cursori</span><span class="sxs-lookup"><span data-stu-id="f46da-130">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="f46da-131">Raggio della mano</span><span class="sxs-lookup"><span data-stu-id="f46da-131">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="f46da-132">Button</span><span class="sxs-lookup"><span data-stu-id="f46da-132">Button</span></span>](button.md)
* [<span data-ttu-id="f46da-133">Oggetto che supporta interazioni</span><span class="sxs-lookup"><span data-stu-id="f46da-133">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="f46da-134">Rettangolo di selezione e barra dell'app</span><span class="sxs-lookup"><span data-stu-id="f46da-134">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="f46da-135">Manipolazione</span><span class="sxs-lookup"><span data-stu-id="f46da-135">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="f46da-136">Menu a mano</span><span class="sxs-lookup"><span data-stu-id="f46da-136">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="f46da-137">Menu adiacente</span><span class="sxs-lookup"><span data-stu-id="f46da-137">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="f46da-138">Raccolta di oggetti</span><span class="sxs-lookup"><span data-stu-id="f46da-138">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="f46da-139">Comando vocale</span><span class="sxs-lookup"><span data-stu-id="f46da-139">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="f46da-140">Tastiera</span><span class="sxs-lookup"><span data-stu-id="f46da-140">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="f46da-141">Descrizione comando</span><span class="sxs-lookup"><span data-stu-id="f46da-141">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="f46da-142">Slate</span><span class="sxs-lookup"><span data-stu-id="f46da-142">Slate</span></span>](slate.md)
* [<span data-ttu-id="f46da-143">Dispositivo di scorrimento</span><span class="sxs-lookup"><span data-stu-id="f46da-143">Slider</span></span>](slider.md)
* [<span data-ttu-id="f46da-144">Shader</span><span class="sxs-lookup"><span data-stu-id="f46da-144">Shader</span></span>](shader.md)
* [<span data-ttu-id="f46da-145">Billboarding e tag-along</span><span class="sxs-lookup"><span data-stu-id="f46da-145">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="f46da-146">Visualizzazione dello stato</span><span class="sxs-lookup"><span data-stu-id="f46da-146">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="f46da-147">Magnetismo di superficie</span><span class="sxs-lookup"><span data-stu-id="f46da-147">Surface magnetism</span></span>](surface-magnetism.md)

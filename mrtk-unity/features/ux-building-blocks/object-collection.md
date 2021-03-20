---
title: ObjectCollection
description: Panoramica della raccolta di oggetti in MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, raccolta di oggetti,
ms.openlocfilehash: 5fb9eea82a7e6dd17aabea006378e790abeed3a3
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2021
ms.locfileid: "104689181"
---
# <a name="object-collection"></a><span data-ttu-id="7208e-104">Raccolta di oggetti</span><span class="sxs-lookup"><span data-stu-id="7208e-104">Object collection</span></span>

![Raccolta di oggetti](../images/object-collection/MRTK_ObjectCollection_Main.jpg)

<span data-ttu-id="7208e-106">La raccolta di oggetti è uno script che consente di definire una matrice di oggetti in forme tridimensionali predefinite.</span><span class="sxs-lookup"><span data-stu-id="7208e-106">Object collection is a script to help lay out an array of objects in predefined three-dimensional shapes.</span></span> <span data-ttu-id="7208e-107">Supporta diversi stili di superficie, ad esempio piano, cilindro, sfera e radiale.</span><span class="sxs-lookup"><span data-stu-id="7208e-107">It supports various surface styles including plane, cylinder, sphere, and radial.</span></span> <span data-ttu-id="7208e-108">Poiché supporta qualsiasi oggetto in Unity, può essere utilizzato per il layout di oggetti 2D e 3D.</span><span class="sxs-lookup"><span data-stu-id="7208e-108">Since it supports any object in Unity, it can be used to layout both 2D and 3D objects.</span></span>

## <a name="object-collection-scripts"></a><span data-ttu-id="7208e-109">Script della raccolta di oggetti</span><span class="sxs-lookup"><span data-stu-id="7208e-109">Object collection scripts</span></span>

- <span data-ttu-id="7208e-110">[`GridObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.GridObjectCollection) supporta i tipi di superficie a cilindri, piani, sfere e radiali</span><span class="sxs-lookup"><span data-stu-id="7208e-110">[`GridObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.GridObjectCollection) supports Cylinder, Plane, Sphere, Radial surface types</span></span>
- <span data-ttu-id="7208e-111">[`ScatterObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.ScatterObjectCollection) supporta la raccolta di stili sparsi</span><span class="sxs-lookup"><span data-stu-id="7208e-111">[`ScatterObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.ScatterObjectCollection) supports scattered style collection</span></span>  
- <span data-ttu-id="7208e-112">[`TileGridObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.TileGridObjectCollection) fornisce alcune opzioni aggiuntive a GridObjectCollection.</span><span class="sxs-lookup"><span data-stu-id="7208e-112">[`TileGridObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.TileGridObjectCollection) provides some additional options to GridObjectCollection.</span></span> <span data-ttu-id="7208e-113">**Nota:** TileGridObjectCollection non estende [`GridObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.GridObjectCollection) e presenta diversi bug (vedere il [problema 6237](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/6237)).</span><span class="sxs-lookup"><span data-stu-id="7208e-113">**Note:** TileGridObjectCollection does not extend [`GridObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.GridObjectCollection), and has several bugs (see [issue 6237](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/6237)).</span></span> <span data-ttu-id="7208e-114">È quindi consigliabile usare [`GridObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.GridObjectCollection) .</span><span class="sxs-lookup"><span data-stu-id="7208e-114">Therefore, it is recommended to use [`GridObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.GridObjectCollection).</span></span>

|![Raccolta oggetto griglia-cilindro](../images/object-collection/MRTK_ObjectCollectionCylinder.png) <span data-ttu-id="7208e-116">Raccolta oggetto griglia-cilindro</span><span class="sxs-lookup"><span data-stu-id="7208e-116">Grid Object Collection - Cylinder</span></span> | ![Raccolta di oggetti Grid-Sphere](../images/object-collection/MRTK_ObjectCollectionSphere.png) <span data-ttu-id="7208e-118">Raccolta di oggetti Grid-Sphere</span><span class="sxs-lookup"><span data-stu-id="7208e-118">Grid Object Collection - Sphere</span></span> |
|:--- | :--- |
|![Raccolta oggetti Grid-radiale](../images/object-collection/MRTK_ObjectCollectionRadial.png) <span data-ttu-id="7208e-120">Raccolta oggetti Grid-radiale</span><span class="sxs-lookup"><span data-stu-id="7208e-120">Grid Object Collection - Radial</span></span> | ![Raccolta oggetto griglia-piano](../images/object-collection/MRTK_ObjectCollectionPlane.png) <span data-ttu-id="7208e-122">Raccolta oggetto griglia-piano</span><span class="sxs-lookup"><span data-stu-id="7208e-122">Grid Object Collection - Plane</span></span> |
|![Raccolta di oggetti sparsi](../images/object-collection/MRTK_ObjectCollectionScattered.png) <span data-ttu-id="7208e-124">Raccolta di oggetti sparsi</span><span class="sxs-lookup"><span data-stu-id="7208e-124">Scattered Object Collection</span></span> | ![Raccolta oggetto griglia affiancata](../images/object-collection/MRTK_ObjectCollectionTileGrid.png) <span data-ttu-id="7208e-126">Raccolta oggetto griglia affiancata</span><span class="sxs-lookup"><span data-stu-id="7208e-126">Tile Grid Object Collection</span></span> |

## <a name="how-to-use-an-object-collection"></a><span data-ttu-id="7208e-127">Come usare una raccolta di oggetti</span><span class="sxs-lookup"><span data-stu-id="7208e-127">How to use an object collection</span></span>

<span data-ttu-id="7208e-128">Per creare una raccolta, creare un GameObject vuoto e assegnarvi uno degli script della raccolta di oggetti.</span><span class="sxs-lookup"><span data-stu-id="7208e-128">To create a collection, create an empty GameObject and assign one of the Object Collection scripts to it.</span></span> <span data-ttu-id="7208e-129">Qualsiasi oggetto può essere aggiunto come elemento figlio di GameObject.</span><span class="sxs-lookup"><span data-stu-id="7208e-129">Any object(s) can be added as a child of the GameObject.</span></span> <span data-ttu-id="7208e-130">Al termine dell'aggiunta degli oggetti figlio, fare clic sul pulsante *Aggiorna raccolta* nel pannello Inspector per generare la raccolta di oggetti.</span><span class="sxs-lookup"><span data-stu-id="7208e-130">Once finished adding child objects, click the *Update Collection* button in the inspector panel to generate the object collection.</span></span> <span data-ttu-id="7208e-131">Gli oggetti verranno disposti nella scena in base ai parametri della raccolta.</span><span class="sxs-lookup"><span data-stu-id="7208e-131">The objects will be laid out in the scene according to the collection parameters.</span></span> <span data-ttu-id="7208e-132">È possibile accedere alla raccolta di aggiornamenti anche tramite il codice.</span><span class="sxs-lookup"><span data-stu-id="7208e-132">Update Collection can be accessed through the code too.</span></span>

![Script della raccolta di oggetti](../images/object-collection/MRTK_ObjectCollectionScript.png)

## <a name="gridobjectcollection-content-alignment"></a><span data-ttu-id="7208e-134">`GridObjectCollection` allineamento del contenuto</span><span class="sxs-lookup"><span data-stu-id="7208e-134">`GridObjectCollection` content alignment</span></span>

<span data-ttu-id="7208e-135">Il contenuto di un GridObjectCollection può essere allineato in modo che l'oggetto padre sia ancorato alla parte superiore, centrale, inferiore e sinistro, al centro o a destra della raccolta.</span><span class="sxs-lookup"><span data-stu-id="7208e-135">The content in a GridObjectCollection can be aligned so that the parent object is anchored to the top/middle/bottom and left/center/right of the collection.</span></span> <span data-ttu-id="7208e-136">Usare la proprietà **Anchor** per specificare l'allineamento del contenuto.</span><span class="sxs-lookup"><span data-stu-id="7208e-136">Use the **anchor** property to specify content alignment.</span></span>

## <a name="gridobjectcollection-layout-order"></a><span data-ttu-id="7208e-137">`GridObjectCollection` ordine layout</span><span class="sxs-lookup"><span data-stu-id="7208e-137">`GridObjectCollection` layout order</span></span>

<span data-ttu-id="7208e-138">Usare il campo **layout** per specificare l'ordine di riga/colonna in cui sono disposti gli elementi figlio:</span><span class="sxs-lookup"><span data-stu-id="7208e-138">Use the **Layout** field to specify the row / column order that children are laid out:</span></span>

<span data-ttu-id="7208e-139">**Column then Row** -Children vengono prima disposti orizzontalmente (by column), quindi verticalmente (per riga).</span><span class="sxs-lookup"><span data-stu-id="7208e-139">**Column Then Row** - Children are first laid out by horizontally (by column), then vertically (by row).</span></span> <span data-ttu-id="7208e-140">Utilizzare **num colonne** (o proprietà colonne nel codice) per specificare il numero di colonne nella griglia.</span><span class="sxs-lookup"><span data-stu-id="7208e-140">Use **Num Columns** (or Columns property in code) to specify the number of columns in the grid.</span></span>

![Layout di riga della colonna](../images/object-collection/MRTK_ColumnThenRow.png)

<span data-ttu-id="7208e-142">**Row then column** -Children vengono inizialmente disposti verticalmente (per riga), quindi orizzontalmente (per colonne).</span><span class="sxs-lookup"><span data-stu-id="7208e-142">**Row Then Column** - Children are first laid out vertically (by row), then horizontally (by columns).</span></span> <span data-ttu-id="7208e-143">Per specificare il numero di righe nella griglia, utilizzare la proprietà **num Rows** (o Rows nel codice).</span><span class="sxs-lookup"><span data-stu-id="7208e-143">Use **Num Rows** (or Rows property in code) to specify the number of rows in the grid.</span></span>

![Layout di riga e di colonna](../images/object-collection/MRTK_RowThenColumn.png)

<span data-ttu-id="7208e-145">**Orizzontale** -gli elementi figlio sono disposti in una singola riga usando solo le colonne</span><span class="sxs-lookup"><span data-stu-id="7208e-145">**Horizontal** - Children are laid out in a single row using columns only</span></span>

<span data-ttu-id="7208e-146">Gli elementi figlio **verticali** sono disposti in una singola colonna usando solo le righe.</span><span class="sxs-lookup"><span data-stu-id="7208e-146">**Vertical** - Children are laid out in a single column using rows only.</span></span>

## <a name="object-collection-examples"></a><span data-ttu-id="7208e-147">Esempi di raccolta di oggetti</span><span class="sxs-lookup"><span data-stu-id="7208e-147">Object collection examples</span></span>

<span data-ttu-id="7208e-148">La `ObjectCollectionExamples` scena di esempio (assets/MRTK/examples/Demos/UX/Collections/Scenes/ObjectCollectionExamples. Unity) contiene diversi esempi di tipi di raccolta di oggetti.</span><span class="sxs-lookup"><span data-stu-id="7208e-148">The `ObjectCollectionExamples` (Assets/MRTK/Examples/Demos/UX/Collections/Scenes/ObjectCollectionExamples.unity) example scene contains various examples of object collection types.</span></span>

<span data-ttu-id="7208e-149">[La tabella periodica degli elementi](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable) è un'applicazione di esempio che illustra il funzionamento delle raccolte di oggetti.</span><span class="sxs-lookup"><span data-stu-id="7208e-149">[Periodic table of the elements](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable) is an example app that demonstrates how object collections work.</span></span> <span data-ttu-id="7208e-150">Usa la raccolta di oggetti per il layout delle caselle degli elementi 3D in forme diverse.</span><span class="sxs-lookup"><span data-stu-id="7208e-150">It uses object collection to layout the 3D element boxes in different shapes.</span></span>

## <a name="object-collection-types"></a><span data-ttu-id="7208e-151">Tipi di raccolte di oggetti</span><span class="sxs-lookup"><span data-stu-id="7208e-151">Object collection types</span></span>

<span data-ttu-id="7208e-152">**oggetti 3D**</span><span class="sxs-lookup"><span data-stu-id="7208e-152">**3D objects**</span></span>

<span data-ttu-id="7208e-153">Una raccolta di oggetti può essere usata per il layout degli oggetti 3D importati.</span><span class="sxs-lookup"><span data-stu-id="7208e-153">An object collection can be used to layout imported 3D objects.</span></span> <span data-ttu-id="7208e-154">Nell'esempio seguente vengono illustrati i layout piano e cilindrico degli oggetti modello di poltrona 3D utilizzando una raccolta.</span><span class="sxs-lookup"><span data-stu-id="7208e-154">The example below shows the plane and cylindrical layouts of 3D chair model objects using a collection.</span></span>

![Raccolta di oggetti 3D](../images/object-collection/MRTK_ObjectCollection_3DObjects.jpg)

<span data-ttu-id="7208e-156">**Oggetti 2D**</span><span class="sxs-lookup"><span data-stu-id="7208e-156">**2D Objects**</span></span>

<span data-ttu-id="7208e-157">Una raccolta di oggetti può essere anche costituita da immagini 2D.</span><span class="sxs-lookup"><span data-stu-id="7208e-157">An object collection can also be crated from 2D images.</span></span> <span data-ttu-id="7208e-158">Ad esempio, più immagini possono essere posizionate in uno stile griglia.</span><span class="sxs-lookup"><span data-stu-id="7208e-158">For example, multiple images can be placed in a grid style.</span></span>

![Raccolta di oggetti 2D](../images/object-collection/MRTK_ObjectCollection_Layout_2DImages.jpg)

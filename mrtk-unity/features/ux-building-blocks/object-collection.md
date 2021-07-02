---
title: Raccolta di oggetti
description: Panoramica della raccolta di oggetti in MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, raccolta di oggetti,
ms.openlocfilehash: 8390e9c4a7bd419f99a5c8c4af7e7a2eca1d8f3f
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177053"
---
# <a name="object-collection"></a><span data-ttu-id="e9609-104">Raccolta di oggetti</span><span class="sxs-lookup"><span data-stu-id="e9609-104">Object collection</span></span>

![Raccolta di oggetti](../images/object-collection/MRTK_ObjectCollection_Main.jpg)

<span data-ttu-id="e9609-106">La raccolta di oggetti è uno script che consente di definire una matrice di oggetti in forme tridimensionali predefinite.</span><span class="sxs-lookup"><span data-stu-id="e9609-106">Object collection is a script to help lay out an array of objects in predefined three-dimensional shapes.</span></span> <span data-ttu-id="e9609-107">Supporta vari stili di superficie, tra cui piano, cilindro, sfera e radiale.</span><span class="sxs-lookup"><span data-stu-id="e9609-107">It supports various surface styles including plane, cylinder, sphere, and radial.</span></span> <span data-ttu-id="e9609-108">Poiché supporta qualsiasi oggetto in Unity, può essere usato per il layout di oggetti 2D e 3D.</span><span class="sxs-lookup"><span data-stu-id="e9609-108">Since it supports any object in Unity, it can be used to layout both 2D and 3D objects.</span></span>

## <a name="object-collection-scripts"></a><span data-ttu-id="e9609-109">Script di raccolta di oggetti</span><span class="sxs-lookup"><span data-stu-id="e9609-109">Object collection scripts</span></span>

- <span data-ttu-id="e9609-110">[`GridObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.GridObjectCollection) supporta i tipi di superficie cilindro, piano, sfera e radiale</span><span class="sxs-lookup"><span data-stu-id="e9609-110">[`GridObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.GridObjectCollection) supports Cylinder, Plane, Sphere, Radial surface types</span></span>
- <span data-ttu-id="e9609-111">[`ScatterObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.ScatterObjectCollection) supporta la raccolta di stili sparsi</span><span class="sxs-lookup"><span data-stu-id="e9609-111">[`ScatterObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.ScatterObjectCollection) supports scattered style collection</span></span>  
- <span data-ttu-id="e9609-112">[`TileGridObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.TileGridObjectCollection) fornisce alcune opzioni aggiuntive a GridObjectCollection.</span><span class="sxs-lookup"><span data-stu-id="e9609-112">[`TileGridObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.TileGridObjectCollection) provides some additional options to GridObjectCollection.</span></span> <span data-ttu-id="e9609-113">**Nota:** TileGridObjectCollection non estende [`GridObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.GridObjectCollection) e presenta diversi bug (vedere il problema [6237).](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/6237)</span><span class="sxs-lookup"><span data-stu-id="e9609-113">**Note:** TileGridObjectCollection does not extend [`GridObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.GridObjectCollection), and has several bugs (see [issue 6237](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/6237)).</span></span> <span data-ttu-id="e9609-114">È pertanto consigliabile usare [`GridObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.GridObjectCollection) .</span><span class="sxs-lookup"><span data-stu-id="e9609-114">Therefore, it is recommended to use [`GridObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.GridObjectCollection).</span></span>

|![Raccolta di oggetti Grid - Cilindro](../images/object-collection/MRTK_ObjectCollectionCylinder.png) <span data-ttu-id="e9609-116">Raccolta di oggetti Grid - Cilindro</span><span class="sxs-lookup"><span data-stu-id="e9609-116">Grid Object Collection - Cylinder</span></span> | ![Raccolta di oggetti Grid - Sphere](../images/object-collection/MRTK_ObjectCollectionSphere.png) <span data-ttu-id="e9609-118">Raccolta di oggetti Grid - Sphere</span><span class="sxs-lookup"><span data-stu-id="e9609-118">Grid Object Collection - Sphere</span></span> |
|:--- | :--- |
|![Raccolta di oggetti Grid - Radial](../images/object-collection/MRTK_ObjectCollectionRadial.png) <span data-ttu-id="e9609-120">Raccolta di oggetti Grid - Radial</span><span class="sxs-lookup"><span data-stu-id="e9609-120">Grid Object Collection - Radial</span></span> | ![Raccolta di oggetti Grid - Piano](../images/object-collection/MRTK_ObjectCollectionPlane.png) <span data-ttu-id="e9609-122">Raccolta di oggetti Grid - Piano</span><span class="sxs-lookup"><span data-stu-id="e9609-122">Grid Object Collection - Plane</span></span> |
|![Raccolta di oggetti dispersi](../images/object-collection/MRTK_ObjectCollectionScattered.png) <span data-ttu-id="e9609-124">Raccolta di oggetti dispersi</span><span class="sxs-lookup"><span data-stu-id="e9609-124">Scattered Object Collection</span></span> | ![Raccolta di oggetti griglia affiancata](../images/object-collection/MRTK_ObjectCollectionTileGrid.png) <span data-ttu-id="e9609-126">Raccolta di oggetti griglia affiancata</span><span class="sxs-lookup"><span data-stu-id="e9609-126">Tile Grid Object Collection</span></span> |

## <a name="how-to-use-an-object-collection"></a><span data-ttu-id="e9609-127">Come usare una raccolta di oggetti</span><span class="sxs-lookup"><span data-stu-id="e9609-127">How to use an object collection</span></span>

<span data-ttu-id="e9609-128">Per creare una raccolta, creare un oggetto GameObject vuoto e assegnare uno degli script della raccolta di oggetti.</span><span class="sxs-lookup"><span data-stu-id="e9609-128">To create a collection, create an empty GameObject and assign one of the Object Collection scripts to it.</span></span> <span data-ttu-id="e9609-129">Qualsiasi oggetto può essere aggiunto come figlio di GameObject.</span><span class="sxs-lookup"><span data-stu-id="e9609-129">Any object(s) can be added as a child of the GameObject.</span></span> <span data-ttu-id="e9609-130">Al termine dell'aggiunta di oggetti figlio, fare clic *sul pulsante Update Collection (Aggiorna raccolta)* nel pannello inspector (Controllo) per generare la raccolta di oggetti.</span><span class="sxs-lookup"><span data-stu-id="e9609-130">Once finished adding child objects, click the *Update Collection* button in the inspector panel to generate the object collection.</span></span> <span data-ttu-id="e9609-131">Gli oggetti verranno disposti nella scena in base ai parametri della raccolta.</span><span class="sxs-lookup"><span data-stu-id="e9609-131">The objects will be laid out in the scene according to the collection parameters.</span></span> <span data-ttu-id="e9609-132">È possibile accedere a Update Collection anche tramite il codice.</span><span class="sxs-lookup"><span data-stu-id="e9609-132">Update Collection can be accessed through the code too.</span></span>

![Script della raccolta di oggetti](../images/object-collection/MRTK_ObjectCollectionScript.png)

## <a name="gridobjectcollection-content-alignment"></a><span data-ttu-id="e9609-134">`GridObjectCollection` allineamento del contenuto</span><span class="sxs-lookup"><span data-stu-id="e9609-134">`GridObjectCollection` content alignment</span></span>

<span data-ttu-id="e9609-135">Il contenuto in gridObjectCollection può essere allineato in modo che l'oggetto padre sia ancorato alla parte superiore/centrale/inferiore e a sinistra/centro/destra della raccolta.</span><span class="sxs-lookup"><span data-stu-id="e9609-135">The content in a GridObjectCollection can be aligned so that the parent object is anchored to the top/middle/bottom and left/center/right of the collection.</span></span> <span data-ttu-id="e9609-136">Usare la proprietà **anchor** per specificare l'allineamento del contenuto.</span><span class="sxs-lookup"><span data-stu-id="e9609-136">Use the **anchor** property to specify content alignment.</span></span>

## <a name="gridobjectcollection-layout-order"></a><span data-ttu-id="e9609-137">`GridObjectCollection` ordine di layout</span><span class="sxs-lookup"><span data-stu-id="e9609-137">`GridObjectCollection` layout order</span></span>

<span data-ttu-id="e9609-138">Usare il **campo Layout** per specificare l'ordine di riga/colonna in cui sono disposti gli elementi figlio:</span><span class="sxs-lookup"><span data-stu-id="e9609-138">Use the **Layout** field to specify the row / column order that children are laid out:</span></span>

<span data-ttu-id="e9609-139">**Colonna e quindi riga:** gli elementi figlio vengono prima disposti orizzontalmente (per colonna), quindi verticalmente (per riga).</span><span class="sxs-lookup"><span data-stu-id="e9609-139">**Column Then Row** - Children are first laid out by horizontally (by column), then vertically (by row).</span></span> <span data-ttu-id="e9609-140">Usare **Num Columns** (o la proprietà Columns nel codice) per specificare il numero di colonne nella griglia.</span><span class="sxs-lookup"><span data-stu-id="e9609-140">Use **Num Columns** (or Columns property in code) to specify the number of columns in the grid.</span></span>

![Layout di colonna e di riga](../images/object-collection/MRTK_ColumnThenRow.png)

<span data-ttu-id="e9609-142">**Riga e colonna: gli** elementi figlio vengono prima disposti verticalmente (per riga), quindi orizzontalmente (in base alle colonne).</span><span class="sxs-lookup"><span data-stu-id="e9609-142">**Row Then Column** - Children are first laid out vertically (by row), then horizontally (by columns).</span></span> <span data-ttu-id="e9609-143">Usare **num rows** (o la proprietà Rows nel codice) per specificare il numero di righe nella griglia.</span><span class="sxs-lookup"><span data-stu-id="e9609-143">Use **Num Rows** (or Rows property in code) to specify the number of rows in the grid.</span></span>

![Layout di righe e colonne](../images/object-collection/MRTK_RowThenColumn.png)

<span data-ttu-id="e9609-145">**Orizzontale:** gli elementi figlio vengono disposti in una singola riga usando solo colonne</span><span class="sxs-lookup"><span data-stu-id="e9609-145">**Horizontal** - Children are laid out in a single row using columns only</span></span>

<span data-ttu-id="e9609-146">**Verticale:** gli elementi figlio vengono disposti in una singola colonna usando solo righe.</span><span class="sxs-lookup"><span data-stu-id="e9609-146">**Vertical** - Children are laid out in a single column using rows only.</span></span>

## <a name="object-collection-examples"></a><span data-ttu-id="e9609-147">Esempi di raccolta di oggetti</span><span class="sxs-lookup"><span data-stu-id="e9609-147">Object collection examples</span></span>

<span data-ttu-id="e9609-148">La scena di esempio `ObjectCollectionExamples` (Assets/MRTK/Examples/Demos/UX/Collections/Scenes/ObjectCollectionExamples.unity) contiene vari esempi di tipi di raccolta di oggetti.</span><span class="sxs-lookup"><span data-stu-id="e9609-148">The `ObjectCollectionExamples` (Assets/MRTK/Examples/Demos/UX/Collections/Scenes/ObjectCollectionExamples.unity) example scene contains various examples of object collection types.</span></span>

<span data-ttu-id="e9609-149">[La tabella periodica degli elementi è un'app](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable) di esempio che illustra il funzionamento delle raccolte di oggetti.</span><span class="sxs-lookup"><span data-stu-id="e9609-149">[Periodic table of the elements](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable) is an example app that demonstrates how object collections work.</span></span> <span data-ttu-id="e9609-150">Usa la raccolta di oggetti per il layout delle caselle degli elementi 3D in forme diverse.</span><span class="sxs-lookup"><span data-stu-id="e9609-150">It uses object collection to layout the 3D element boxes in different shapes.</span></span>

## <a name="object-collection-types"></a><span data-ttu-id="e9609-151">Tipi di raccolta di oggetti</span><span class="sxs-lookup"><span data-stu-id="e9609-151">Object collection types</span></span>

<span data-ttu-id="e9609-152">**Oggetti 3D**</span><span class="sxs-lookup"><span data-stu-id="e9609-152">**3D objects**</span></span>

<span data-ttu-id="e9609-153">Una raccolta di oggetti può essere usata per il layout degli oggetti 3D importati.</span><span class="sxs-lookup"><span data-stu-id="e9609-153">An object collection can be used to layout imported 3D objects.</span></span> <span data-ttu-id="e9609-154">L'esempio seguente mostra il piano e i layout cilindrici degli oggetti modello di sedie 3D che usano una raccolta.</span><span class="sxs-lookup"><span data-stu-id="e9609-154">The example below shows the plane and cylindrical layouts of 3D chair model objects using a collection.</span></span>

![Raccolta di oggetti 3D](../images/object-collection/MRTK_ObjectCollection_3DObjects.jpg)

<span data-ttu-id="e9609-156">**Oggetti 2D**</span><span class="sxs-lookup"><span data-stu-id="e9609-156">**2D Objects**</span></span>

<span data-ttu-id="e9609-157">È anche possibile creare una raccolta di oggetti da immagini 2D.</span><span class="sxs-lookup"><span data-stu-id="e9609-157">An object collection can also be crated from 2D images.</span></span> <span data-ttu-id="e9609-158">Ad esempio, è possibile inserire più immagini in uno stile griglia.</span><span class="sxs-lookup"><span data-stu-id="e9609-158">For example, multiple images can be placed in a grid style.</span></span>

![Raccolta di oggetti 2D](../images/object-collection/MRTK_ObjectCollection_Layout_2DImages.jpg)

---
title: Raccolta di oggetti
description: Panoramica della raccolta di oggetti in MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, raccolta di oggetti,
ms.openlocfilehash: 6705bd7093dbcd81912153872e4fd07c703fc5c0b9c081e0287589a7c8e959ac
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115197556"
---
# <a name="object-collection"></a>Raccolta di oggetti

![Raccolta di oggetti](../images/object-collection/MRTK_ObjectCollection_Main.jpg)

La raccolta di oggetti è uno script che consente di creare una matrice di oggetti in forme tridimensionali predefinite. Supporta vari stili di superficie, tra cui piano, cilindro, sfera e radiale. Poiché supporta qualsiasi oggetto in Unity, può essere usato per il layout di oggetti 2D e 3D.

## <a name="object-collection-scripts"></a>Script di raccolta di oggetti

- [`GridObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.GridObjectCollection) supporta i tipi di superficie cilindro, piano, sfera, radiale
- [`ScatterObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.ScatterObjectCollection) supporta la raccolta di stili sparsi  
- [`TileGridObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.TileGridObjectCollection) offre alcune opzioni aggiuntive per GridObjectCollection. **Nota:** TileGridObjectCollection non estende [`GridObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.GridObjectCollection) e presenta diversi bug (vedere il problema [6237).](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/6237) Pertanto, è consigliabile usare [`GridObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.GridObjectCollection) .

|![Raccolta di oggetti Grid - Cilindro](../images/object-collection/MRTK_ObjectCollectionCylinder.png) Raccolta di oggetti Grid - Cilindro | ![Raccolta di oggetti Grid - Sphere](../images/object-collection/MRTK_ObjectCollectionSphere.png) Raccolta di oggetti Grid - Sphere |
|:--- | :--- |
|![Raccolta di oggetti Grid - Radial](../images/object-collection/MRTK_ObjectCollectionRadial.png) Raccolta di oggetti Grid - Radial | ![Raccolta di oggetti Grid - Piano](../images/object-collection/MRTK_ObjectCollectionPlane.png) Raccolta di oggetti Grid - Piano |
|![Raccolta di oggetti sparsi](../images/object-collection/MRTK_ObjectCollectionScattered.png) Raccolta di oggetti sparsi | ![Raccolta di oggetti Tile Grid](../images/object-collection/MRTK_ObjectCollectionTileGrid.png) Raccolta di oggetti Tile Grid |

## <a name="how-to-use-an-object-collection"></a>Come usare una raccolta di oggetti

Per creare una raccolta, creare un GameObject vuoto e assegnare uno degli script object collection. Qualsiasi oggetto può essere aggiunto come figlio di GameObject. Dopo aver aggiunto gli oggetti figlio, fare clic *sul pulsante Update Collection (Aggiorna* raccolta) nel pannello di controllo per generare la raccolta di oggetti. Gli oggetti verranno disposti nella scena in base ai parametri della raccolta. Update Collection è accessibile anche tramite il codice.

![Script della raccolta di oggetti](../images/object-collection/MRTK_ObjectCollectionScript.png)

## <a name="gridobjectcollection-content-alignment"></a>`GridObjectCollection` allineamento del contenuto

Il contenuto di gridObjectCollection può essere allineato in modo che l'oggetto padre sia ancorato alla parte superiore/centrale/inferiore e a sinistra/al centro/destra della raccolta. Usare la proprietà **anchor** per specificare l'allineamento del contenuto.

## <a name="gridobjectcollection-layout-order"></a>`GridObjectCollection` ordine di layout

Usare il **campo Layout** per specificare l'ordine di riga/colonna in cui sono disposti gli elementi figlio:

**Colonna quindi riga:** gli elementi figlio vengono prima disposti orizzontalmente (per colonna), quindi verticalmente (per riga). Usare **Num Columns** (o la proprietà Columns nel codice) per specificare il numero di colonne nella griglia.

![Layout delle colonne e delle righe](../images/object-collection/MRTK_ColumnThenRow.png)

**Riga quindi colonna:** gli elementi figlio vengono prima disposti verticalmente (per riga), quindi orizzontalmente (in base alle colonne). Usare **Num Rows** (o la proprietà Rows nel codice) per specificare il numero di righe nella griglia.

![Layout di righe e colonne](../images/object-collection/MRTK_RowThenColumn.png)

**Orizzontale:** gli elementi figlio vengono disposti in una singola riga usando solo colonne

**Verticale:** gli elementi figlio vengono disposti in una singola colonna usando solo righe.

## <a name="object-collection-examples"></a>Esempi di raccolte di oggetti

La scena di esempio `ObjectCollectionExamples` (Assets/MRTK/Examples/Demos/UX/Collections/Scenes/ObjectCollectionExamples.unity) contiene vari esempi di tipi di raccolta di oggetti.

[La tabella periodica degli elementi è un'app](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable) di esempio che illustra il funzionamento delle raccolte di oggetti. Usa la raccolta di oggetti per il layout delle caselle degli elementi 3D in forme diverse.

## <a name="object-collection-types"></a>Tipi di raccolta di oggetti

**Oggetti 3D**

Una raccolta di oggetti può essere usata per il layout degli oggetti 3D importati. L'esempio seguente illustra il piano e i layout cilindrici degli oggetti modello 3D che usano una raccolta .

![Raccolta di oggetti 3D](../images/object-collection/MRTK_ObjectCollection_3DObjects.jpg)

**Oggetti 2D**

È anche possibile creare una raccolta di oggetti da immagini 2D. Ad esempio, è possibile inserire più immagini in uno stile griglia.

![Raccolta di oggetti 2D](../images/object-collection/MRTK_ObjectCollection_Layout_2DImages.jpg)

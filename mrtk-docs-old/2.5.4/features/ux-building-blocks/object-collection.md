---
title: ObjectCollection
description: Panoramica della raccolta di oggetti in MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, raccolta di oggetti,
ms.openlocfilehash: d057fed9e6f86e49aaf6020651768a36b4b0a604
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/03/2021
ms.locfileid: "101781582"
---
# <a name="object-collection"></a>Raccolta di oggetti

![Raccolta di oggetti](../images/object-collection/MRTK_ObjectCollection_Main.jpg)

La raccolta di oggetti è uno script che consente di definire una matrice di oggetti in forme tridimensionali predefinite. Supporta diversi stili di superficie, ad esempio piano, cilindro, sfera e radiale. Poiché supporta qualsiasi oggetto in Unity, può essere utilizzato per il layout di oggetti 2D e 3D.

## <a name="object-collection-scripts"></a>Script della raccolta di oggetti

- [`GridObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.GridObjectCollection) supporta i tipi di superficie a cilindri, piani, sfere e radiali
- [`ScatterObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.ScatterObjectCollection) supporta la raccolta di stili sparsi  
- [`TileGridObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.TileGridObjectCollection) fornisce alcune opzioni aggiuntive a GridObjectCollection. **Nota:** TileGridObjectCollection non estende [`GridObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.GridObjectCollection) e presenta diversi bug (vedere il [problema 6237](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/6237)). È quindi consigliabile usare [`GridObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.GridObjectCollection) .

|![Raccolta oggetto griglia-cilindro](../images/object-collection/MRTK_ObjectCollectionCylinder.png) Raccolta oggetto griglia-cilindro | ![Raccolta di oggetti Grid-Sphere](../images/object-collection/MRTK_ObjectCollectionSphere.png) Raccolta di oggetti Grid-Sphere |
|:--- | :--- |
|![Raccolta oggetti Grid-radiale](../images/object-collection/MRTK_ObjectCollectionRadial.png) Raccolta oggetti Grid-radiale | ![Raccolta oggetto griglia-piano](../images/object-collection/MRTK_ObjectCollectionPlane.png) Raccolta oggetto griglia-piano |
|![Raccolta di oggetti sparsi](../images/object-collection/MRTK_ObjectCollectionScattered.png) Raccolta di oggetti sparsi | ![Raccolta oggetto griglia affiancata](../images/object-collection/MRTK_ObjectCollectionTileGrid.png) Raccolta oggetto griglia affiancata |

## <a name="how-to-use-an-object-collection"></a>Come usare una raccolta di oggetti

Per creare una raccolta, creare un GameObject vuoto e assegnarvi uno degli script della raccolta di oggetti. Qualsiasi oggetto può essere aggiunto come elemento figlio di GameObject. Al termine dell'aggiunta degli oggetti figlio, fare clic sul pulsante *Aggiorna raccolta* nel pannello Inspector per generare la raccolta di oggetti. Gli oggetti verranno disposti nella scena in base ai parametri della raccolta. È possibile accedere alla raccolta di aggiornamenti anche tramite il codice.

![Script della raccolta di oggetti](../images/object-collection/MRTK_ObjectCollectionScript.png)

## <a name="gridobjectcollection-content-alignment"></a>`GridObjectCollection` allineamento del contenuto

Il contenuto di un GridObjectCollection può essere allineato in modo che l'oggetto padre sia ancorato alla parte superiore, centrale, inferiore e sinistro, al centro o a destra della raccolta. Usare la proprietà **Anchor** per specificare l'allineamento del contenuto.

## <a name="gridobjectcollection-layout-order"></a>`GridObjectCollection` ordine layout

Usare il campo **layout** per specificare l'ordine di riga/colonna in cui sono disposti gli elementi figlio:

**Column then Row** -Children vengono prima disposti orizzontalmente (by column), quindi verticalmente (per riga). Utilizzare **num colonne** (o proprietà colonne nel codice) per specificare il numero di colonne nella griglia.

![Layout di riga della colonna](../images/object-collection/MRTK_ColumnThenRow.png)

**Row then column** -Children vengono inizialmente disposti verticalmente (per riga), quindi orizzontalmente (per colonne). Per specificare il numero di righe nella griglia, utilizzare la proprietà **num Rows** (o Rows nel codice).

![Layout di riga e di colonna](../images/object-collection/MRTK_RowThenColumn.png)

**Orizzontale** -gli elementi figlio sono disposti in una singola riga usando solo le colonne

Gli elementi figlio **verticali** sono disposti in una singola colonna usando solo le righe.

## <a name="object-collection-examples"></a>Esempi di raccolta di oggetti

La `ObjectCollectionExamples` scena di esempio (assets/MRTK/examples/Demos/UX/Collections/Scenes/ObjectCollectionExamples. Unity) contiene diversi esempi di tipi di raccolta di oggetti.

[La tabella periodica degli elementi](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable) è un'applicazione di esempio che illustra il funzionamento delle raccolte di oggetti. Usa la raccolta di oggetti per il layout delle caselle degli elementi 3D in forme diverse.

## <a name="object-collection-types"></a>Tipi di raccolte di oggetti

**oggetti 3D**

Una raccolta di oggetti può essere usata per il layout degli oggetti 3D importati. Nell'esempio seguente vengono illustrati i layout piano e cilindrico degli oggetti modello di poltrona 3D utilizzando una raccolta.

![Raccolta di oggetti 3D](../images/object-collection/MRTK_ObjectCollection_3DObjects.jpg)

**Oggetti 2D**

Una raccolta di oggetti può essere anche costituita da immagini 2D. Ad esempio, più immagini possono essere posizionate in uno stile griglia.

![Raccolta di oggetti 2D](../images/object-collection/MRTK_ObjectCollection_Layout_2DImages.jpg)

---
title: Utilità di scambio di asset
description: Documentazione sull'uso dell'utilità di scambio di asset in MRTK per Unity.
author: hferrone
ms.author: v-hferrone
ms.date: 03/9/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK
ms.openlocfilehash: 50ef252913575988b5f377dd9ff92f9e9ade3a72
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176161"
---
# <a name="asset-swap-utility"></a>Utilità di scambio di asset

Trovare e sostituire è onnipresente quando si lavora negli strumenti di creazione di testo e contenuto. Quando è necessario scambiare molti asset all'interno di una scena unity, è qui che l'oggetto [ScriptableObject](https://docs.unity3d.com/Manual/class-ScriptableObject.html) e l'editor [AssetSwapUtility](xref:Microsoft.MixedReality.Toolkit.Utilities.Editor.AssetSwapUtility) possono dare una mano. L'utilità è inclusa nel `Microsoft.MixedReality.Toolkit.Unity.Tools` pacchetto.

Salva tutte le azioni di ricerca e sostituzione come ScriptableObject in modo che sia trivalo scambiare avanti e indietro o salvare i "temi" di scambio per un `AssetSwapUtility` uso futuro.

## <a name="swapping-assets"></a>Scambio di asset

Lo scambio di asset è semplice dopo aver creato un `AssetSwapCollection` oggetto . Di seguito viene illustrato l'uso scambiando due cubi rossi con due sfera blu in una scena. Aggiungere prima di tutto due cubi rossi alla scena che usano il cubo Unity predefinito e il `MRTK_Standard_Red` materiale.

Per creare un `AssetSwapCollection` , passare a Mixed Reality Toolkit > Utilities > Asset Swap **Collection**. Con `AssetSwapCollection` l'opzione selezionata, compilare le proprietà come illustrato nell'immagine seguente:

![Raccolta di scambio di asset nell'editor di Unity](images/asset-swap-img-01.png)

Selezionare quindi "Blue Spheres" nell'elenco a discesa "Tema selezionato" e premere "Applica". Tutti i cubi rossi all'interno della scena devono essere sostituiti con le sfera blu.

![Raccolta di scambio di asset nell'editor di Unity con il tema selezionato evidenziato](images/asset-swap-img-02.png)

In questo esempio è stata eseguita una sostituzione completa della scena, ma è possibile sostituire parti della scena modificando la "modalità di selezione". È anche possibile tornare ai cubi rossi selezionando "Cubi rossi" nell'elenco a discesa "Tema selezionato" e premendo di nuovo "Applica".

> [!NOTE]
> È possibile scambiare qualsiasi tipo di asset, ad esempio file audio, tipi di carattere, prefab e così via. Eseguirà alcuni controlli di integrità per assicurarsi di passare `AssetSwapUtility` a tipi simili.

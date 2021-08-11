---
title: Utilità di scambio di asset
description: Documentazione sull'uso dell'utilità di scambio di asset in MRTK per Unity.
author: hferrone
ms.author: v-hferrone
ms.date: 03/9/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK
ms.openlocfilehash: 3322087f9027f46b39be07f5368cd8ae4ca875f206984fb823f9b1c8590f86f6
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115196271"
---
# <a name="asset-swap-utility"></a>Utilità di scambio di asset

La funzione Trova e sostituisci è molto utile quando si lavora con gli strumenti di creazione di testo e contenuto. Quando è necessario scambiare molti asset all'interno di una scena Unity, è qui che l'oggetto [ScriptableObject](https://docs.unity3d.com/Manual/class-ScriptableObject.html) e l'editor [AssetSwapUtility](xref:Microsoft.MixedReality.Toolkit.Utilities.Editor.AssetSwapUtility) possono dare una mano. L'utilità è inclusa nel `Microsoft.MixedReality.Toolkit.Unity.Tools` pacchetto.

salva tutte le azioni di ricerca e sostituzione come ScriptableObject in modo che sia trivalore scambiare avanti e indietro o salvare lo `AssetSwapUtility` scambio di "temi" per un uso futuro.

## <a name="swapping-assets"></a>Scambio di asset

Lo scambio di asset è semplice dopo aver creato un `AssetSwapCollection` oggetto . Di seguito viene illustrato l'uso scambiando due cubi rossi con due sphere blu in una scena. Aggiungere prima di tutto due cubi rossi alla scena che usano il cubo Unity predefinito e il `MRTK_Standard_Red` materiale.

Per creare un `AssetSwapCollection` , passare a Mixed Reality Toolkit > Utilities > Asset Swap **Collection**. Con `AssetSwapCollection` l'elemento selezionato compilare le proprietà come illustrato nell'immagine seguente:

![Raccolta di scambio di asset nell'editor di Unity](images/asset-swap-img-01.png)

Selezionare quindi "Blue Spheres" dall'elenco a discesa "Selected Theme" (Tema selezionato) e premere "Apply" (Applica). Tutti i cubi rossi all'interno della scena devono essere sostituiti con sphere blu.

![Raccolta di scambio di asset nell'editor di Unity con il tema selezionato evidenziato](images/asset-swap-img-02.png)

In questo esempio è stata eseguita una sostituzione completa della scena, ma è possibile sostituire parti della scena modificando la "Modalità di selezione". È anche possibile tornare ai cubi rossi selezionando "Cubi rossi" dall'elenco a discesa "Tema selezionato" e premendo di nuovo "Applica".

> [!NOTE]
> È possibile scambiare qualsiasi tipo di asset, ad esempio file audio, tipi di carattere, prefab e così via. Eseguirà `AssetSwapUtility` alcuni controlli di integrità per assicurarsi di passare a tipi simili.

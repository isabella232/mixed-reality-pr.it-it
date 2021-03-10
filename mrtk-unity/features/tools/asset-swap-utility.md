---
title: Utilità di scambio asset
description: Documentazione sull'uso di asset swap Utility in MRTK per Unity.
author: hferrone
ms.author: v-hferrone
ms.date: 03/9/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK
ms.openlocfilehash: bfdf0111d99f96c2b03f921da21368897d682d3d
ms.sourcegitcommit: ece91dbba40981720fe7e1a7c3b93e8b75ff71ba
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/10/2021
ms.locfileid: "102583191"
---
# <a name="asset-swap-utility"></a>Utilità di scambio asset

Trova e Sostituisci è onnipresente quando si lavora con gli strumenti di creazione di testo e di contenuto. Quando è necessario scambiare molti asset in una scena Unity, questo è il punto in cui il [ScriptableObject](https://docs.unity3d.com/Manual/class-ScriptableObject.html) di [AssetSwapUtility](xref:Microsoft.MixedReality.Toolkit.Utilities.Editor.AssetSwapUtility) e l'editor possono dare una mano. L'utilità è inclusa nel `Microsoft.MixedReality.Toolkit.Unity.Tools` pacchetto.

`AssetSwapUtility`Salva tutte le azioni di ricerca e sostituzione come ScriptableObject, in modo che sia trival eseguire lo swap avanti e indietro o salvare i "temi" per un uso futuro.

## <a name="swapping-assets"></a>Scambio di asset

Lo scambio di risorse è facile dopo aver creato un `AssetSwapCollection` . Per illustrare l'uso, è necessario scambiare due cubi rossi con due sfere blu in una scena. Aggiungere prima due cubi rossi alla scena che usano il cubo Unity predefinito e il `MRTK_Standard_Red` materiale.

Per creare un `AssetSwapCollection` , passare a **mixed reality Toolkit > Utilities > create asset swap Collection**. Con l' `AssetSwapCollection` opzione selezionato compila le proprietà come illustrato nell'immagine seguente:

![Raccolta asset swap nell'editor di Unity](images/asset-swap-img-01.png)

Selezionare quindi "sfere blu" dall'elenco a discesa "tema selezionato" e fare clic su "applica". Tutti i cubi rossi nella scena devono essere sostituiti con sfere blu.

![Raccolta asset swap nell'editor di Unity con tema selezionato evidenziato](images/asset-swap-img-02.png)

In questo esempio è stata eseguita una sostituzione completa della scena, ma è possibile sostituire parti della scena modificando la "modalità di selezione". È anche possibile eseguire lo swapping ai cubi rossi selezionando "cubi rossi" dall'elenco a discesa "tema selezionato" e ripetendo "Apply".

> [!NOTE]
> È possibile scambiare qualsiasi tipo di asset, ad esempio file audio, tipi di carattere, prefabbricati e così via. Il eseguirà `AssetSwapUtility` alcuni controlli di integrità per assicurarsi di eseguire lo scambio a tipi simili.
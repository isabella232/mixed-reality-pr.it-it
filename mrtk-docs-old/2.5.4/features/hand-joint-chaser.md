---
title: README_HandJointChaser
description: Hand joint chaser in MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: be7be3d2a37898ca8ceb0cbf9a51de58b6e25487cd17338bf0a5f55951d01eb5
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115213180"
---
# <a name="hand-joint-chaser-example"></a>Esempio di caccia a giunzione a mano

![In questa scena di esempio viene illustrato come usare solver per associare ](images/hand-joint-chaser/MRTK_HandJointChaser_Main.jpg) oggetti alle giunzioni delle mani.

## <a name="example-scene"></a>Scena di esempio

È possibile trovare la scena di **esempio HandJointChaserExample** nella `Assets/MRTK/Examples` cartella in `Demos/Input/Scenes/` .

## <a name="solver-handler"></a>Gestore del risolutore

Fare **clic su Oggetto tracciato a cui fare riferimento** e selezionare Mano **giunzione a sinistra** o **Giunzione mano destra.** Sarà possibile visualizzare l'elenco a discesa **Mano tracciata.** Nell'elenco a discesa è possibile selezionare un giunto specifico da rilevare. Questa scena di esempio usa il Risolutore visualizzazione radiale per fare in modo che un oggetto segua l'oggetto di destinazione. Per [altri dettagli,](ux-building-blocks/solvers/solver.md) vedere la pagina Risolutore.

![Risolutore di giunzione manuale](images/hand-joint-chaser/MRTK_Solver_HandJoint.jpg)

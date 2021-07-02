---
title: Inseguente giunzione mano
description: Hand Joint In MRTK (Inseguente mano in MRTK)
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: 0beac2dae5aa12cf07f193dab9a6db7bc7ddf2e5
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2021
ms.locfileid: "113175367"
---
# <a name="hand-joint-chaser"></a>Inseguente giunzione mano

![Hand Joint In questa ](../images/hand-joint-chaser/MRTK_HandJointChaser_Main.jpg) scena di esempio viene illustrato come usare solver per collegare oggetti alle giunzioni delle mani.

## <a name="example-scene"></a>Scena di esempio

È possibile trovare la scena di esempio **HandJointChaserExample** nella `Assets/MRTK/Examples` cartella in `Demos/Input/Scenes/` .

## <a name="solver-handler"></a>Gestore risolutore

Fare **clic su Tracked Object to Reference (Oggetto** tracciato a cui fare riferimento) e selezionare **Hand Joint Left (Mano giunzione** **sinistra) o Hand Joint Right (Giunzione mano destra).** Sarà possibile visualizzare l'elenco a discesa **Tracked Hand Joint (Giunzione mano** tracciata). Nell'elenco a discesa è possibile selezionare un comune specifico di cui tenere traccia. Questa scena di esempio usa il risolutore di visualizzazione radiale per fare in modo che un oggetto segua l'oggetto di destinazione. Per [altri dettagli,](../ux-building-blocks/solvers/solver.md) vedere la pagina Risolutore.

![Risolutore congiunto mano](../images/hand-joint-chaser/MRTK_Solver_HandJoint.jpg)

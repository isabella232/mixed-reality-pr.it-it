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
# <a name="hand-joint-chaser"></a><span data-ttu-id="996c8-104">Inseguente giunzione mano</span><span class="sxs-lookup"><span data-stu-id="996c8-104">Hand joint chaser</span></span>

<span data-ttu-id="996c8-105">![Hand Joint In questa ](../images/hand-joint-chaser/MRTK_HandJointChaser_Main.jpg) scena di esempio viene illustrato come usare solver per collegare oggetti alle giunzioni delle mani.</span><span class="sxs-lookup"><span data-stu-id="996c8-105">![Hand joint chasers](../images/hand-joint-chaser/MRTK_HandJointChaser_Main.jpg) This example scene demonstrates how to use Solver to attach objects to the hand joints.</span></span>

## <a name="example-scene"></a><span data-ttu-id="996c8-106">Scena di esempio</span><span class="sxs-lookup"><span data-stu-id="996c8-106">Example scene</span></span>

<span data-ttu-id="996c8-107">È possibile trovare la scena di esempio **HandJointChaserExample** nella `Assets/MRTK/Examples` cartella in `Demos/Input/Scenes/` .</span><span class="sxs-lookup"><span data-stu-id="996c8-107">You can find the example scene **HandJointChaserExample** scene in the `Assets/MRTK/Examples` folder under `Demos/Input/Scenes/`.</span></span>

## <a name="solver-handler"></a><span data-ttu-id="996c8-108">Gestore risolutore</span><span class="sxs-lookup"><span data-stu-id="996c8-108">Solver handler</span></span>

<span data-ttu-id="996c8-109">Fare **clic su Tracked Object to Reference (Oggetto** tracciato a cui fare riferimento) e selezionare **Hand Joint Left (Mano giunzione** **sinistra) o Hand Joint Right (Giunzione mano destra).**</span><span class="sxs-lookup"><span data-stu-id="996c8-109">Click **Tracked Object To Reference** and select **Hand Joint Left** or **Hand Joint Right**.</span></span> <span data-ttu-id="996c8-110">Sarà possibile visualizzare l'elenco a discesa **Tracked Hand Joint (Giunzione mano** tracciata).</span><span class="sxs-lookup"><span data-stu-id="996c8-110">You will be able to see **Tracked Hand Joint** drop down.</span></span> <span data-ttu-id="996c8-111">Nell'elenco a discesa è possibile selezionare un comune specifico di cui tenere traccia. Questa scena di esempio usa il risolutore di visualizzazione radiale per fare in modo che un oggetto segua l'oggetto di destinazione.</span><span class="sxs-lookup"><span data-stu-id="996c8-111">From the drop down list, you can select specific joint to track. This example scene uses Radial View Solver to make an object follow the target object.</span></span> <span data-ttu-id="996c8-112">Per [altri dettagli,](../ux-building-blocks/solvers/solver.md) vedere la pagina Risolutore.</span><span class="sxs-lookup"><span data-stu-id="996c8-112">See [Solver](../ux-building-blocks/solvers/solver.md) page for more details.</span></span>

![Risolutore congiunto mano](../images/hand-joint-chaser/MRTK_Solver_HandJoint.jpg)

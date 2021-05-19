---
title: Hand Joint Chaser
description: Hand joint chaser in MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realtà mista, sviluppo, MRTK,
ms.openlocfilehash: f9db1c4a2ca1959a35c541e87c9a4a01bc41637e
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144625"
---
# <a name="hand-joint-chaser-example"></a><span data-ttu-id="591c9-104">Esempio di caccia a giunzione a mano</span><span class="sxs-lookup"><span data-stu-id="591c9-104">Hand joint chaser example</span></span>

<span data-ttu-id="591c9-105">![In questa scena di esempio viene illustrato come usare solver per associare ](../images/hand-joint-chaser/MRTK_HandJointChaser_Main.jpg) oggetti alle giunzioni delle mani.</span><span class="sxs-lookup"><span data-stu-id="591c9-105">![Hand joint chasers](../images/hand-joint-chaser/MRTK_HandJointChaser_Main.jpg) This example scene demonstrates how to use Solver to attach objects to the hand joints.</span></span>

## <a name="example-scene"></a><span data-ttu-id="591c9-106">Scena di esempio</span><span class="sxs-lookup"><span data-stu-id="591c9-106">Example scene</span></span>

<span data-ttu-id="591c9-107">È possibile trovare la scena di **esempio HandJointChaserExample** nella `Assets/MRTK/Examples` cartella in `Demos/Input/Scenes/` .</span><span class="sxs-lookup"><span data-stu-id="591c9-107">You can find the example scene **HandJointChaserExample** scene in the `Assets/MRTK/Examples` folder under `Demos/Input/Scenes/`.</span></span>

## <a name="solver-handler"></a><span data-ttu-id="591c9-108">Gestore del risolutore</span><span class="sxs-lookup"><span data-stu-id="591c9-108">Solver handler</span></span>

<span data-ttu-id="591c9-109">Fare **clic su Oggetto tracciato a cui fare riferimento** e selezionare Mano **giunzione a sinistra** o **Giunzione mano destra.**</span><span class="sxs-lookup"><span data-stu-id="591c9-109">Click **Tracked Object To Reference** and select **Hand Joint Left** or **Hand Joint Right**.</span></span> <span data-ttu-id="591c9-110">Sarà possibile visualizzare l'elenco a discesa **Mano tracciata.**</span><span class="sxs-lookup"><span data-stu-id="591c9-110">You will be able to see **Tracked Hand Joint** drop down.</span></span> <span data-ttu-id="591c9-111">Nell'elenco a discesa è possibile selezionare un giunto specifico da rilevare. Questa scena di esempio usa il Risolutore visualizzazione radiale per fare in modo che un oggetto segua l'oggetto di destinazione.</span><span class="sxs-lookup"><span data-stu-id="591c9-111">From the drop down list, you can select specific joint to track. This example scene uses Radial View Solver to make an object follow the target object.</span></span> <span data-ttu-id="591c9-112">Per [altri dettagli,](../ux-building-blocks/solvers/solver.md) vedere la pagina Del risolutore.</span><span class="sxs-lookup"><span data-stu-id="591c9-112">See [Solver](../ux-building-blocks/solvers/solver.md) page for more details.</span></span>

![Risolutore di giunzione manuale](../images/hand-joint-chaser/MRTK_Solver_HandJoint.jpg)

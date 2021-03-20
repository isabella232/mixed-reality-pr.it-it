---
title: README_HandJointChaser
description: Chaser joint Hand in MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: 4e95f5a6f6019bed617bac55064c8c3984d9386e
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2021
ms.locfileid: "104702097"
---
# <a name="hand-joint-chaser-example"></a><span data-ttu-id="0e786-104">Esempio di intercettore misto mano</span><span class="sxs-lookup"><span data-stu-id="0e786-104">Hand joint chaser example</span></span>

<span data-ttu-id="0e786-105">![Inseguibili con giunzione manuale in ](images/hand-joint-chaser/MRTK_HandJointChaser_Main.jpg) questa scena di esempio viene illustrato come utilizzare il Risolutore per alleghi gli oggetti alle giunzioni di mano.</span><span class="sxs-lookup"><span data-stu-id="0e786-105">![Hand joint chasers](images/hand-joint-chaser/MRTK_HandJointChaser_Main.jpg) This example scene demonstrates how to use Solver to attach objects to the hand joints.</span></span>

## <a name="example-scene"></a><span data-ttu-id="0e786-106">Scena di esempio</span><span class="sxs-lookup"><span data-stu-id="0e786-106">Example scene</span></span>

<span data-ttu-id="0e786-107">È possibile trovare la scena **HandJointChaserExample** della scena di esempio nella `Assets/MRTK/Examples` cartella in `Demos/Input/Scenes/` .</span><span class="sxs-lookup"><span data-stu-id="0e786-107">You can find the example scene **HandJointChaserExample** scene in the `Assets/MRTK/Examples` folder under `Demos/Input/Scenes/`.</span></span>

## <a name="solver-handler"></a><span data-ttu-id="0e786-108">Gestore del Risolutore</span><span class="sxs-lookup"><span data-stu-id="0e786-108">Solver handler</span></span>

<span data-ttu-id="0e786-109">Fare clic su **oggetto rilevato per fare riferimento** e selezionare giunzione a **sinistra** o a **destra** congiunta.</span><span class="sxs-lookup"><span data-stu-id="0e786-109">Click **Tracked Object To Reference** and select **Hand Joint Left** or **Hand Joint Right**.</span></span> <span data-ttu-id="0e786-110">Sarà possibile visualizzare l'elenco a discesa della **giunzione a mano rilevata** .</span><span class="sxs-lookup"><span data-stu-id="0e786-110">You will be able to see **Tracked Hand Joint** drop down.</span></span> <span data-ttu-id="0e786-111">Dall'elenco a discesa è possibile selezionare una giunzione specifica da rilevare. In questa scena di esempio viene usato il Risolutore di viste radiali per rendere un oggetto che segue l'oggetto di destinazione.</span><span class="sxs-lookup"><span data-stu-id="0e786-111">From the drop down list, you can select specific joint to track. This example scene uses Radial View Solver to make an object follow the target object.</span></span> <span data-ttu-id="0e786-112">Per ulteriori informazioni, vedere la pagina [Risolutore](ux-building-blocks/solvers/solver.md) .</span><span class="sxs-lookup"><span data-stu-id="0e786-112">See [Solver](ux-building-blocks/solvers/solver.md) page for more details.</span></span>

![Risolutore giunto a mano](images/hand-joint-chaser/MRTK_Solver_HandJoint.jpg)

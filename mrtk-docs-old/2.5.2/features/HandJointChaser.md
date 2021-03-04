---
title: README_HandJointChaser
description: Chaser joint Hand in MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: 0790606ad8ac977d812bf47379c5cd6fdb5db489
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/03/2021
ms.locfileid: "101783250"
---
# <a name="hand-joint-chaser-example"></a><span data-ttu-id="b0b7c-104">Esempio di intercettore misto mano</span><span class="sxs-lookup"><span data-stu-id="b0b7c-104">Hand joint chaser example</span></span>

<span data-ttu-id="b0b7c-105">![Inseguibili con giunzione manuale in ](images/hand-joint-chaser/MRTK_HandJointChaser_Main.jpg) questa scena di esempio viene illustrato come utilizzare il Risolutore per alleghi gli oggetti alle giunzioni di mano.</span><span class="sxs-lookup"><span data-stu-id="b0b7c-105">![Hand joint chasers](images/hand-joint-chaser/MRTK_HandJointChaser_Main.jpg) This example scene demonstrates how to use Solver to attach objects to the hand joints.</span></span>

## <a name="example-scene"></a><span data-ttu-id="b0b7c-106">Scena di esempio</span><span class="sxs-lookup"><span data-stu-id="b0b7c-106">Example scene</span></span>

<span data-ttu-id="b0b7c-107">È possibile trovare la scena **HandJointChaserExample** della scena di esempio nella `Assets/MRTK/Examples` cartella in `Demos/Input/Scenes/` .</span><span class="sxs-lookup"><span data-stu-id="b0b7c-107">You can find the example scene **HandJointChaserExample** scene in the `Assets/MRTK/Examples` folder under `Demos/Input/Scenes/`.</span></span>

## <a name="solver-handler"></a><span data-ttu-id="b0b7c-108">Gestore del Risolutore</span><span class="sxs-lookup"><span data-stu-id="b0b7c-108">Solver handler</span></span>

<span data-ttu-id="b0b7c-109">Fare clic su **oggetto rilevato per fare riferimento** e selezionare giunzione a **sinistra** o a **destra** congiunta.</span><span class="sxs-lookup"><span data-stu-id="b0b7c-109">Click **Tracked Object To Reference** and select **Hand Joint Left** or **Hand Joint Right**.</span></span> <span data-ttu-id="b0b7c-110">Sarà possibile visualizzare l'elenco a discesa della **giunzione a mano rilevata** .</span><span class="sxs-lookup"><span data-stu-id="b0b7c-110">You will be able to see **Tracked Hand Joint** drop down.</span></span> <span data-ttu-id="b0b7c-111">Dall'elenco a discesa è possibile selezionare una giunzione specifica da rilevare. In questa scena di esempio viene usato il Risolutore di viste radiali per rendere un oggetto che segue l'oggetto di destinazione.</span><span class="sxs-lookup"><span data-stu-id="b0b7c-111">From the drop down list, you can select specific joint to track. This example scene uses Radial View Solver to make an object follow the target object.</span></span> <span data-ttu-id="b0b7c-112">Per ulteriori informazioni, vedere la pagina [Risolutore](ux-building-blocks/solvers/Solver.md) .</span><span class="sxs-lookup"><span data-stu-id="b0b7c-112">See [Solver](ux-building-blocks/solvers/Solver.md) page for more details.</span></span>

![Risolutore giunto a mano](images/hand-joint-chaser/MRTK_Solver_HandJoint.jpg)

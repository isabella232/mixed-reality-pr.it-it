---
title: InputState
description: Documentazione sugli stati di input in MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, InputState,
ms.openlocfilehash: 8035da588b16ef8f2149fd91abe9c811d317c114
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2021
ms.locfileid: "104694268"
---
# <a name="accessing-input-state-in-mrtk"></a><span data-ttu-id="41bc4-104">Accesso allo stato di input in MRTK</span><span class="sxs-lookup"><span data-stu-id="41bc4-104">Accessing input state in MRTK</span></span>

<span data-ttu-id="41bc4-105">È possibile eseguire una query direttamente sullo stato di tutti gli input in MRTK scorrendo i controller collegati alle origini di input.</span><span class="sxs-lookup"><span data-stu-id="41bc4-105">It's possible to directly query the state of all inputs in MRTK by iterating over the controllers attached to the input sources.</span></span> <span data-ttu-id="41bc4-106">MRTK fornisce anche metodi pratici per accedere alla posizione e alla rotazione degli occhi, delle mani, della testa e del controller di movimento.</span><span class="sxs-lookup"><span data-stu-id="41bc4-106">MRTK also provides convenience methods for accessing the position and rotation of the eyes, hands, head, and motion controller.</span></span>

<span data-ttu-id="41bc4-107">Vedere la scena InputDataExample per un esempio di esecuzione di query sull'input tramite iterazione sui controller e tramite la [`InputRayUtils`](xref:Microsoft.MixedReality.Toolkit.Input.InputRayUtils) classe.</span><span class="sxs-lookup"><span data-stu-id="41bc4-107">See the InputDataExample scene for an example of querying input both via iterating over controllers, and by using the [`InputRayUtils`](xref:Microsoft.MixedReality.Toolkit.Input.InputRayUtils) class.</span></span>

## <a name="example-access-position-rotation-of-head-hands-eyes-in-mrtk"></a><span data-ttu-id="41bc4-108">Esempio: posizione di accesso, rotazione di Head, Hands, Eyes in MRTK</span><span class="sxs-lookup"><span data-stu-id="41bc4-108">Example: Access position, rotation of head, hands, eyes in MRTK</span></span>

<span data-ttu-id="41bc4-109">[`InputRayUtils`](xref:Microsoft.MixedReality.Toolkit.Input.InputRayUtils)La classe di MRTK fornisce metodi pratici per accedere al raggio di mano, al raggio principale, al raggio d'occhio e ai raggi del controller di movimento.</span><span class="sxs-lookup"><span data-stu-id="41bc4-109">MRTK's [`InputRayUtils`](xref:Microsoft.MixedReality.Toolkit.Input.InputRayUtils) class provides convenience methods for accessing the hand ray, head ray, eye gaze ray, and motion controller rays.</span></span>

```c#
// Get the head ray
var headRay = InputRayUtils.GetHeadGazeRay();

// Get the right hand ray
Ray rightHandRay;
if(InputRayUtils.TryGetHandRay(Handedness.right, rightHandRay))
{
    // Right hand ray is available
}
else
{
    // Right hand ray is not available
}
```

## <a name="example-access-position-rotation-of-all-6dof-controllers-active-in-scene"></a><span data-ttu-id="41bc4-110">Esempio: posizione di accesso, rotazione di tutti i controller 6DOF attivi nella scena</span><span class="sxs-lookup"><span data-stu-id="41bc4-110">Example: Access position, rotation of all 6DOF controllers active in scene</span></span>

```c#
foreach(var controller in CoreServices.InputSystem.DetectedControllers)
{
    // Interactions for a controller is the list of inputs that this controller exposes
    foreach(MixedRealityInteractionMapping inputMapping in controller.Interactions)
    {
        // 6DOF controllers support the "SpatialPointer" type (pointing direction)
        // or "GripPointer" type (direction of the 6DOF controller)
        if (inputMapping.InputType == DeviceInputType.SpatialPointer)
        {
            Debug.Log("spatial pointer PositionData: " + inputMapping.PositionData);
            Debug.Log("spatial pointer RotationData: " + inputMapping.RotationData);
        }

        if (inputMapping.InputType == DeviceInputType.SpatialGrip)
        {
            Debug.Log("spatial grip PositionData: " + inputMapping.PositionData);
            Debug.Log("spatial grip RotationData: " + inputMapping.RotationData);
        }
    }
}
```

## <a name="see-also"></a><span data-ttu-id="41bc4-111">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="41bc4-111">See also</span></span>

- [<span data-ttu-id="41bc4-112">InputEvents</span><span class="sxs-lookup"><span data-stu-id="41bc4-112">InputEvents</span></span>](input-events.md)
- [<span data-ttu-id="41bc4-113">Pointers</span><span class="sxs-lookup"><span data-stu-id="41bc4-113">Pointers</span></span>](pointers.md)
- [<span data-ttu-id="41bc4-114">HandTracking</span><span class="sxs-lookup"><span data-stu-id="41bc4-114">HandTracking</span></span>](hand-tracking.md)

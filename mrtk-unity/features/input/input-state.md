---
title: Stato di input
description: Documentazione sugli stati di input in MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, InputState,
ms.openlocfilehash: 4c1bd115c63e25decf73c082546e75b0f276a7ef
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/19/2021
ms.locfileid: "110145258"
---
# <a name="accessing-input-state-in-mrtk"></a>Accesso allo stato di input in MRTK

È possibile eseguire direttamente una query sullo stato di tutti gli input in MRTK tramite l'iterazione dei controller collegati alle origini di input. MRTK offre anche metodi pratici per accedere alla posizione e alla rotazione di occhi, mani, testa e controller del movimento.

Vedere la scena InputDataExample per un esempio di esecuzione di query sull'input tramite l'iterazione dei controller e tramite la [`InputRayUtils`](xref:Microsoft.MixedReality.Toolkit.Input.InputRayUtils) classe .

## <a name="example-access-position-rotation-of-head-hands-eyes-in-mrtk"></a>Esempio: posizione di accesso, rotazione della testa, delle mani e degli occhi in MRTK

La classe di MRTK fornisce metodi pratici per accedere ai raggi della mano, del raggio della testa, del raggio dello sguardo fisso e dei raggi del [`InputRayUtils`](xref:Microsoft.MixedReality.Toolkit.Input.InputRayUtils) controller del movimento.

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

## <a name="example-access-position-rotation-of-all-6dof-controllers-active-in-scene"></a>Esempio: posizione di accesso, rotazione di tutti i controller 6DOF attivi nella scena

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

## <a name="see-also"></a>Vedi anche

- [InputEvents](input-events.md)
- [Pointers](pointers.md)
- [HandTracking](hand-tracking.md)

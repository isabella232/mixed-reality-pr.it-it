---
ms.openlocfilehash: c5775d29fb3934d324cceb6dc451e6588d15fe6d
ms.sourcegitcommit: 0db5777954697f1d738469363bbf385481204d24
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/27/2021
ms.locfileid: "105636358"
---
# <a name="mrtk"></a>[MRTK](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

MRTK attualmente non dispone di helper per la modalità di riprogettazione. Per ulteriori informazioni, vedere una delle altre schede.

# <a name="xr-sdk"></a>[SDK XR](#tab/xr)
<!-- NEVER CHANGE THE ABOVE LINE! -->

La modalità di riproiezione può essere configurata impostando [XRDisplaySubsystem. reprojectionMode](https://docs.unity3d.com/ScriptReference/XR.XRDisplaySubsystem-reprojectionMode.html) sul valore appropriato.

Se, ad esempio, si sta creando un' [esperienza di solo orientamento](../../../../design/coordinate-systems.md#building-an-orientation-only-or-seated-scale-experience) con contenuto rigidamente bloccato del corpo (ad esempio, il contenuto video di 360 gradi), è possibile impostare in modo esplicito la modalità di riproiezione su orientamento solo impostando il valore su [ReprojectionMode. OrientationOnly](https://docs.unity3d.com/ScriptReference/XR.XRDisplaySubsystem.ReprojectionMode.html).

# <a name="legacy-wsa"></a>[WSA legacy](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

La modalità di riproiezione può essere configurata impostando [HolographicSettings. ReprojectionMode](https://docs.unity3d.com/2018.4/Documentation/ScriptReference/XR.WSA.HolographicSettings.ReprojectionMode.html) sul valore appropriato.

Se, ad esempio, si sta creando un' [esperienza di solo orientamento](../../../../design/coordinate-systems.md#building-an-orientation-only-or-seated-scale-experience) con contenuto rigidamente bloccato del corpo (ad esempio, il contenuto video di 360 gradi), è possibile impostare in modo esplicito la modalità di riproiezione su orientamento solo impostando il valore su [HolographicReprojectionMode. OrientationOnly](https://docs.unity3d.com/2018.4/Documentation/ScriptReference/XR.WSA.HolographicSettings.HolographicReprojectionMode.html).
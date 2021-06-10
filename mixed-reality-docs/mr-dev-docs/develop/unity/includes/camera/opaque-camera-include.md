---
ms.openlocfilehash: 76f72ac81b677acabf98444f626b7a6b908c29fb
ms.sourcegitcommit: 719682f70a75f732b573442fae8987be1acaaf19
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/02/2021
ms.locfileid: "110748481"
---
# <a name="mrtk"></a>[MRTK](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

MRTK gestirà automaticamente impostazioni specifiche della fotocamera, in base [alla configurazione nel profilo del sistema di fotocamera.](/windows/mixed-reality/mrtk-unity/features/camera-system/camera-system-overview#display-settings)

**Spazio dei nomi:** *Microsoft.MixedReality.Toolkit.CameraSystem*<br>
**Tipo:** *MixedRealityCameraSystem*

Per controllare l'opacità della fotocamera, il sistema MixedRealityCamera [ha una `IsOpaque` proprietà](/dotnet/api/microsoft.mixedreality.toolkit.camerasystem.mixedrealitycamerasystem.isopaque).

```cs
CoreServices.CameraSystem.IsOpaque;
```

# <a name="xr-sdk"></a>[XR SDK](#tab/xr)
<!-- NEVER CHANGE THE ABOVE LINE! -->

**Spazio dei nomi:** *UnityEngine.XR*<br>
**Tipo:** *XRDisplaySubsystem*

È possibile usare il codice script per determinare in fase di esecuzione se il visore VR è immersive o olografico controllando [displayOpaque](https://docs.unity3d.com/ScriptReference/XR.XRDisplaySubsystem-displayOpaque.html) nell'oggetto [XRDisplaySubsystem](https://docs.unity3d.com/ScriptReference/XR.XRDisplaySubsystem.html)in esecuzione attivamente.

# <a name="legacy-wsa"></a>[Legacy WSA](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

**Spazio dei nomi:** *UnityEngine.XR.WSA*<br>
**Tipo:** *HolographicSettings*

È possibile usare il codice script per determinare in fase di esecuzione se il visore VR è immersive o olografico controllando [HolographicSettings.IsDisplayOpaque.](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.IsDisplayOpaque.html)
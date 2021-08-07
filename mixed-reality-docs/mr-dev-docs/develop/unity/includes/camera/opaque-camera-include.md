---
ms.openlocfilehash: 73aba70497323d406b5138eca9c7d2054b8d8b3cea6e82ef67e962a21876c280
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115212302"
---
# <a name="mrtk"></a>[MRTK](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

MRTK gestirà automaticamente impostazioni specifiche della fotocamera, in base alla [configurazione nel profilo di sistema della fotocamera.](/windows/mixed-reality/mrtk-unity/features/camera-system/camera-system-overview#display-settings)

**Spazio dei nomi:** *Microsoft.MixedReality.Toolkit. CameraSystem*<br>
**Tipo:** *MixedRealityCameraSystem*

Per controllare l'opacità della fotocamera, il sistema MixedRealityCamera ha [una `IsOpaque` proprietà](/dotnet/api/microsoft.mixedreality.toolkit.camerasystem.mixedrealitycamerasystem.isopaque).

```cs
CoreServices.CameraSystem.IsOpaque;
```

# <a name="xr-sdk"></a>[XR SDK](#tab/xr)
<!-- NEVER CHANGE THE ABOVE LINE! -->

**Spazio dei nomi:** *UnityEngine.XR*<br>
**Tipo:** *XRDisplaySubsystem*

È possibile usare il codice script per determinare in fase di esecuzione se il visore è immersivo o olografico controllando [displayOpaque](https://docs.unity3d.com/ScriptReference/XR.XRDisplaySubsystem-displayOpaque.html) nel sistema [XRDisplaySubsystem](https://docs.unity3d.com/ScriptReference/XR.XRDisplaySubsystem.html)in esecuzione.

# <a name="legacy-wsa"></a>[Legacy WSA](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

**Spazio dei nomi:** *UnityEngine.XR.WSA*<br>
**Tipo:** *HolographicSettings*

È possibile usare il codice script per determinare in fase di esecuzione se il visore è immersivo o olografico controllando [HolographicSettings.IsDisplayOpaque.](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.IsDisplayOpaque.html)
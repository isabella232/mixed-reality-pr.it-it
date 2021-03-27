---
ms.openlocfilehash: 0dfbe2cda2779c2eafe54b01d2d28e703444fd1a
ms.sourcegitcommit: 0db5777954697f1d738469363bbf385481204d24
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/27/2021
ms.locfileid: "105636369"
---
# <a name="mrtk"></a>[MRTK](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

MRTK gestirà automaticamente le impostazioni della fotocamera specifiche in base alla [configurazione nel profilo di sistema della fotocamera](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/camera-system/camera-system-overview#display-settings).

**Spazio dei nomi:** *Microsoft. MixedReality. Toolkit. CameraSystem*<br>
**Tipo:** *MixedRealityCameraSystem*

Per controllare l'opacità della fotocamera, il sistema MixedRealityCamera dispone di [una `IsOpaque` Proprietà](https://docs.microsoft.com/dotnet/api/microsoft.mixedreality.toolkit.camerasystem.mixedrealitycamerasystem.isopaque).

```cs
CoreServices.CameraSystem.IsOpaque;
```

# <a name="xr-sdk"></a>[SDK XR](#tab/xr)
<!-- NEVER CHANGE THE ABOVE LINE! -->

**Spazio dei nomi:** *UnityEngine. XR*<br>
**Tipo:** *XRDisplaySubsystem*

È possibile usare il codice di script per determinare in fase di esecuzione se l'auricolare è immersiva o olografica controllando [displayOpaque](https://docs.unity3d.com/ScriptReference/XR.XRDisplaySubsystem-displayOpaque.html) sul [XRDisplaySubsystem](https://docs.unity3d.com/ScriptReference/XR.XRDisplaySubsystem.html)in esecuzione attiva.

# <a name="legacy-wsa"></a>[WSA legacy](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

**Spazio dei nomi:** *UnityEngine. XR. WSA*<br>
**Tipo:** *HolographicSettings*

È possibile usare il codice di script per determinare in fase di esecuzione se l'auricolare è immersiva o olografica controllando [HolographicSettings. IsDisplayOpaque](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.IsDisplayOpaque.html).
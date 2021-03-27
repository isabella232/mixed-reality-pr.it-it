---
ms.openlocfilehash: 0dfbe2cda2779c2eafe54b01d2d28e703444fd1a
ms.sourcegitcommit: 0db5777954697f1d738469363bbf385481204d24
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/27/2021
ms.locfileid: "105636369"
---
# <a name="mrtk"></a>[<span data-ttu-id="1e78f-101">MRTK</span><span class="sxs-lookup"><span data-stu-id="1e78f-101">MRTK</span></span>](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="1e78f-102">MRTK gestirà automaticamente le impostazioni della fotocamera specifiche in base alla [configurazione nel profilo di sistema della fotocamera](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/camera-system/camera-system-overview#display-settings).</span><span class="sxs-lookup"><span data-stu-id="1e78f-102">MRTK will handle specific camera settings automatically, based on the [configuration in the camera system profile](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/camera-system/camera-system-overview#display-settings).</span></span>

<span data-ttu-id="1e78f-103">**Spazio dei nomi:** *Microsoft. MixedReality. Toolkit. CameraSystem*</span><span class="sxs-lookup"><span data-stu-id="1e78f-103">**Namespace:** *Microsoft.MixedReality.Toolkit.CameraSystem*</span></span><br>
<span data-ttu-id="1e78f-104">**Tipo:** *MixedRealityCameraSystem*</span><span class="sxs-lookup"><span data-stu-id="1e78f-104">**Type:** *MixedRealityCameraSystem*</span></span>

<span data-ttu-id="1e78f-105">Per controllare l'opacità della fotocamera, il sistema MixedRealityCamera dispone di [una `IsOpaque` Proprietà](https://docs.microsoft.com/dotnet/api/microsoft.mixedreality.toolkit.camerasystem.mixedrealitycamerasystem.isopaque).</span><span class="sxs-lookup"><span data-stu-id="1e78f-105">To check the camera's opaqueness, the MixedRealityCamera system has [an `IsOpaque` property](https://docs.microsoft.com/dotnet/api/microsoft.mixedreality.toolkit.camerasystem.mixedrealitycamerasystem.isopaque).</span></span>

```cs
CoreServices.CameraSystem.IsOpaque;
```

# <a name="xr-sdk"></a>[<span data-ttu-id="1e78f-106">SDK XR</span><span class="sxs-lookup"><span data-stu-id="1e78f-106">XR SDK</span></span>](#tab/xr)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="1e78f-107">**Spazio dei nomi:** *UnityEngine. XR*</span><span class="sxs-lookup"><span data-stu-id="1e78f-107">**Namespace:** *UnityEngine.XR*</span></span><br>
<span data-ttu-id="1e78f-108">**Tipo:** *XRDisplaySubsystem*</span><span class="sxs-lookup"><span data-stu-id="1e78f-108">**Type:** *XRDisplaySubsystem*</span></span>

<span data-ttu-id="1e78f-109">È possibile usare il codice di script per determinare in fase di esecuzione se l'auricolare è immersiva o olografica controllando [displayOpaque](https://docs.unity3d.com/ScriptReference/XR.XRDisplaySubsystem-displayOpaque.html) sul [XRDisplaySubsystem](https://docs.unity3d.com/ScriptReference/XR.XRDisplaySubsystem.html)in esecuzione attiva.</span><span class="sxs-lookup"><span data-stu-id="1e78f-109">You can use script code to determine at runtime whether the headset is immersive or holographic by checking [displayOpaque](https://docs.unity3d.com/ScriptReference/XR.XRDisplaySubsystem-displayOpaque.html) on the actively running [XRDisplaySubsystem](https://docs.unity3d.com/ScriptReference/XR.XRDisplaySubsystem.html).</span></span>

# <a name="legacy-wsa"></a>[<span data-ttu-id="1e78f-110">WSA legacy</span><span class="sxs-lookup"><span data-stu-id="1e78f-110">Legacy WSA</span></span>](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="1e78f-111">**Spazio dei nomi:** *UnityEngine. XR. WSA*</span><span class="sxs-lookup"><span data-stu-id="1e78f-111">**Namespace:** *UnityEngine.XR.WSA*</span></span><br>
<span data-ttu-id="1e78f-112">**Tipo:** *HolographicSettings*</span><span class="sxs-lookup"><span data-stu-id="1e78f-112">**Type:** *HolographicSettings*</span></span>

<span data-ttu-id="1e78f-113">È possibile usare il codice di script per determinare in fase di esecuzione se l'auricolare è immersiva o olografica controllando [HolographicSettings. IsDisplayOpaque](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.IsDisplayOpaque.html).</span><span class="sxs-lookup"><span data-stu-id="1e78f-113">You can use script code to determine at runtime whether the headset is immersive or holographic by checking [HolographicSettings.IsDisplayOpaque](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.IsDisplayOpaque.html).</span></span>
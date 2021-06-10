---
ms.openlocfilehash: 76f72ac81b677acabf98444f626b7a6b908c29fb
ms.sourcegitcommit: 719682f70a75f732b573442fae8987be1acaaf19
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/02/2021
ms.locfileid: "110748481"
---
# <a name="mrtk"></a>[<span data-ttu-id="32b74-101">MRTK</span><span class="sxs-lookup"><span data-stu-id="32b74-101">MRTK</span></span>](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="32b74-102">MRTK gestirà automaticamente impostazioni specifiche della fotocamera, in base [alla configurazione nel profilo del sistema di fotocamera.](/windows/mixed-reality/mrtk-unity/features/camera-system/camera-system-overview#display-settings)</span><span class="sxs-lookup"><span data-stu-id="32b74-102">MRTK will handle specific camera settings automatically, based on the [configuration in the camera system profile](/windows/mixed-reality/mrtk-unity/features/camera-system/camera-system-overview#display-settings).</span></span>

<span data-ttu-id="32b74-103">**Spazio dei nomi:** *Microsoft.MixedReality.Toolkit.CameraSystem*</span><span class="sxs-lookup"><span data-stu-id="32b74-103">**Namespace:** *Microsoft.MixedReality.Toolkit.CameraSystem*</span></span><br>
<span data-ttu-id="32b74-104">**Tipo:** *MixedRealityCameraSystem*</span><span class="sxs-lookup"><span data-stu-id="32b74-104">**Type:** *MixedRealityCameraSystem*</span></span>

<span data-ttu-id="32b74-105">Per controllare l'opacità della fotocamera, il sistema MixedRealityCamera [ha una `IsOpaque` proprietà](/dotnet/api/microsoft.mixedreality.toolkit.camerasystem.mixedrealitycamerasystem.isopaque).</span><span class="sxs-lookup"><span data-stu-id="32b74-105">To check the camera's opaqueness, the MixedRealityCamera system has [an `IsOpaque` property](/dotnet/api/microsoft.mixedreality.toolkit.camerasystem.mixedrealitycamerasystem.isopaque).</span></span>

```cs
CoreServices.CameraSystem.IsOpaque;
```

# <a name="xr-sdk"></a>[<span data-ttu-id="32b74-106">XR SDK</span><span class="sxs-lookup"><span data-stu-id="32b74-106">XR SDK</span></span>](#tab/xr)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="32b74-107">**Spazio dei nomi:** *UnityEngine.XR*</span><span class="sxs-lookup"><span data-stu-id="32b74-107">**Namespace:** *UnityEngine.XR*</span></span><br>
<span data-ttu-id="32b74-108">**Tipo:** *XRDisplaySubsystem*</span><span class="sxs-lookup"><span data-stu-id="32b74-108">**Type:** *XRDisplaySubsystem*</span></span>

<span data-ttu-id="32b74-109">È possibile usare il codice script per determinare in fase di esecuzione se il visore VR è immersive o olografico controllando [displayOpaque](https://docs.unity3d.com/ScriptReference/XR.XRDisplaySubsystem-displayOpaque.html) nell'oggetto [XRDisplaySubsystem](https://docs.unity3d.com/ScriptReference/XR.XRDisplaySubsystem.html)in esecuzione attivamente.</span><span class="sxs-lookup"><span data-stu-id="32b74-109">You can use script code to determine at runtime whether the headset is immersive or holographic by checking [displayOpaque](https://docs.unity3d.com/ScriptReference/XR.XRDisplaySubsystem-displayOpaque.html) on the actively running [XRDisplaySubsystem](https://docs.unity3d.com/ScriptReference/XR.XRDisplaySubsystem.html).</span></span>

# <a name="legacy-wsa"></a>[<span data-ttu-id="32b74-110">Legacy WSA</span><span class="sxs-lookup"><span data-stu-id="32b74-110">Legacy WSA</span></span>](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="32b74-111">**Spazio dei nomi:** *UnityEngine.XR.WSA*</span><span class="sxs-lookup"><span data-stu-id="32b74-111">**Namespace:** *UnityEngine.XR.WSA*</span></span><br>
<span data-ttu-id="32b74-112">**Tipo:** *HolographicSettings*</span><span class="sxs-lookup"><span data-stu-id="32b74-112">**Type:** *HolographicSettings*</span></span>

<span data-ttu-id="32b74-113">È possibile usare il codice script per determinare in fase di esecuzione se il visore VR è immersive o olografico controllando [HolographicSettings.IsDisplayOpaque.](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.IsDisplayOpaque.html)</span><span class="sxs-lookup"><span data-stu-id="32b74-113">You can use script code to determine at runtime whether the headset is immersive or holographic by checking [HolographicSettings.IsDisplayOpaque](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.IsDisplayOpaque.html).</span></span>
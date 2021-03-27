---
ms.openlocfilehash: c5775d29fb3934d324cceb6dc451e6588d15fe6d
ms.sourcegitcommit: 0db5777954697f1d738469363bbf385481204d24
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/27/2021
ms.locfileid: "105636358"
---
# <a name="mrtk"></a>[<span data-ttu-id="23ae5-101">MRTK</span><span class="sxs-lookup"><span data-stu-id="23ae5-101">MRTK</span></span>](#tab/mrtk)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="23ae5-102">MRTK attualmente non dispone di helper per la modalità di riprogettazione.</span><span class="sxs-lookup"><span data-stu-id="23ae5-102">MRTK doesn't currently have helpers for the reprojection mode.</span></span> <span data-ttu-id="23ae5-103">Per ulteriori informazioni, vedere una delle altre schede.</span><span class="sxs-lookup"><span data-stu-id="23ae5-103">Please see one of the other tabs for more information.</span></span>

# <a name="xr-sdk"></a>[<span data-ttu-id="23ae5-104">SDK XR</span><span class="sxs-lookup"><span data-stu-id="23ae5-104">XR SDK</span></span>](#tab/xr)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="23ae5-105">La modalità di riproiezione può essere configurata impostando [XRDisplaySubsystem. reprojectionMode](https://docs.unity3d.com/ScriptReference/XR.XRDisplaySubsystem-reprojectionMode.html) sul valore appropriato.</span><span class="sxs-lookup"><span data-stu-id="23ae5-105">The reprojection mode is configurable by setting [XRDisplaySubsystem.reprojectionMode](https://docs.unity3d.com/ScriptReference/XR.XRDisplaySubsystem-reprojectionMode.html) to the appropriate value.</span></span>

<span data-ttu-id="23ae5-106">Se, ad esempio, si sta creando un' [esperienza di solo orientamento](../../../../design/coordinate-systems.md#building-an-orientation-only-or-seated-scale-experience) con contenuto rigidamente bloccato del corpo (ad esempio, il contenuto video di 360 gradi), è possibile impostare in modo esplicito la modalità di riproiezione su orientamento solo impostando il valore su [ReprojectionMode. OrientationOnly](https://docs.unity3d.com/ScriptReference/XR.XRDisplaySubsystem.ReprojectionMode.html).</span><span class="sxs-lookup"><span data-stu-id="23ae5-106">For example, if you're building an [orientation-only experience](../../../../design/coordinate-systems.md#building-an-orientation-only-or-seated-scale-experience) with rigidly body-locked content (for example, 360-degree video content), you can explicitly set the reprojection mode to orientation only by setting it to [ReprojectionMode.OrientationOnly](https://docs.unity3d.com/ScriptReference/XR.XRDisplaySubsystem.ReprojectionMode.html).</span></span>

# <a name="legacy-wsa"></a>[<span data-ttu-id="23ae5-107">WSA legacy</span><span class="sxs-lookup"><span data-stu-id="23ae5-107">Legacy WSA</span></span>](#tab/wsa)
<!-- NEVER CHANGE THE ABOVE LINE! -->

<span data-ttu-id="23ae5-108">La modalità di riproiezione può essere configurata impostando [HolographicSettings. ReprojectionMode](https://docs.unity3d.com/2018.4/Documentation/ScriptReference/XR.WSA.HolographicSettings.ReprojectionMode.html) sul valore appropriato.</span><span class="sxs-lookup"><span data-stu-id="23ae5-108">The reprojection mode is configurable by setting [HolographicSettings.ReprojectionMode](https://docs.unity3d.com/2018.4/Documentation/ScriptReference/XR.WSA.HolographicSettings.ReprojectionMode.html) to the appropriate value.</span></span>

<span data-ttu-id="23ae5-109">Se, ad esempio, si sta creando un' [esperienza di solo orientamento](../../../../design/coordinate-systems.md#building-an-orientation-only-or-seated-scale-experience) con contenuto rigidamente bloccato del corpo (ad esempio, il contenuto video di 360 gradi), è possibile impostare in modo esplicito la modalità di riproiezione su orientamento solo impostando il valore su [HolographicReprojectionMode. OrientationOnly](https://docs.unity3d.com/2018.4/Documentation/ScriptReference/XR.WSA.HolographicSettings.HolographicReprojectionMode.html).</span><span class="sxs-lookup"><span data-stu-id="23ae5-109">For example, if you're building an [orientation-only experience](../../../../design/coordinate-systems.md#building-an-orientation-only-or-seated-scale-experience) with rigidly body-locked content (for example, 360-degree video content), you can explicitly set the reprojection mode to orientation only by setting it to [HolographicReprojectionMode.OrientationOnly](https://docs.unity3d.com/2018.4/Documentation/ScriptReference/XR.WSA.HolographicSettings.HolographicReprojectionMode.html).</span></span>
---
title: Oggetti nativi di realtà mista in Unity
description: Informazioni su come ottenere l'accesso agli oggetti nativi olografici sottostanti in Unity usando lo spazio dei nomi XR.
author: vladkol
ms.author: vladkol
ms.date: 02/25/2021
ms.topic: article
keywords: Unity, realtà mista, nativa, xrdevice, spatialcoordinatesystem, holographicframe, holographiccamera, ispatialcoordinatesystem, iholographicframe, iholographiccamera, getnativeptr, auricolare realtà mista, headset di realtà mista di Windows, auricolare della realtà virtuale
ms.openlocfilehash: c202c698fe55bcd3215850579166ebcb8d4b8910
ms.sourcegitcommit: 441ef99e6090081c6cd3aa88ed21e13e941f0cc6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/09/2021
ms.locfileid: "102475075"
---
# <a name="mixed-reality-native-interop-in-unity"></a><span data-ttu-id="72c84-104">Interoperabilità nativa in realtà mista in Unity</span><span class="sxs-lookup"><span data-stu-id="72c84-104">Mixed Reality native interop in Unity</span></span>

<span data-ttu-id="72c84-105">Ogni app di realtà mista [ottiene un HolographicSpace prima di iniziare a](../native/getting-a-holographicspace.md) ricevere i dati della fotocamera e i frame di rendering.</span><span class="sxs-lookup"><span data-stu-id="72c84-105">Every Mixed Reality app [gets a HolographicSpace](../native/getting-a-holographicspace.md) before it starts receiving camera data and rendering frames.</span></span> <span data-ttu-id="72c84-106">In Unity, il motore esegue automaticamente questi passaggi, gestendo gli oggetti olografici e aggiornando internamente come parte del ciclo di rendering.</span><span class="sxs-lookup"><span data-stu-id="72c84-106">In Unity, the engine takes care of those steps for you, handling Holographic objects and internally updating as part of its render loop.</span></span>

<span data-ttu-id="72c84-107">Negli scenari avanzati potrebbe tuttavia essere necessario ottenere l'accesso agli oggetti nativi sottostanti, ad esempio <a href="/uwp/api/windows.graphics.holographic.holographiccamera" target="_blank">HolographicCamera</a> e <a href="/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a>corrente.</span><span class="sxs-lookup"><span data-stu-id="72c84-107">However, in advanced scenarios you may need to get access to the underlying native objects, such as the <a href="/uwp/api/windows.graphics.holographic.holographiccamera" target="_blank">HolographicCamera</a> and current <a href="/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a>.</span></span>

[!INCLUDE[](includes/unity-native-ptrs.md)]

### <a name="unmarshaling-native-pointers"></a><span data-ttu-id="72c84-108">Unmarshalling di puntatori nativi</span><span class="sxs-lookup"><span data-stu-id="72c84-108">Unmarshaling native pointers</span></span>

<span data-ttu-id="72c84-109">Dopo avere ottenuto `IntPtr` da uno dei metodi precedenti (non necessario per MRTK), usare i frammenti di codice seguenti per effettuare il marshalling degli oggetti gestiti.</span><span class="sxs-lookup"><span data-stu-id="72c84-109">After obtaining the `IntPtr` from one of the methods above (not needed for MRTK), use the following code snippets to marshal them to managed objects.</span></span>

<span data-ttu-id="72c84-110">Se si usa [Microsoft. Windows. MixedReality. DotNetWinRT](https://www.nuget.org/packages/Microsoft.Windows.MixedReality.DotNetWinRT), è possibile costruire un oggetto gestito da un puntatore nativo usando il `FromNativePtr()` Metodo:</span><span class="sxs-lookup"><span data-stu-id="72c84-110">If you are using [Microsoft.Windows.MixedReality.DotNetWinRT](https://www.nuget.org/packages/Microsoft.Windows.MixedReality.DotNetWinRT), you can construct a managed object from a native pointer using the `FromNativePtr()` method:</span></span>

```cs
var worldOrigin = Microsoft.Windows.Perception.Spatial.SpatialCoordinateSystem.FromNativePtr(spatialCoordinateSystemPtr);
```

<span data-ttu-id="72c84-111">In caso contrario, utilizzare `Marshal.GetObjectForIUnknown()` ed eseguire il cast al tipo desiderato:</span><span class="sxs-lookup"><span data-stu-id="72c84-111">Otherwise, use `Marshal.GetObjectForIUnknown()` and cast to the type you want:</span></span>

```cs
#if ENABLE_WINMD_SUPPORT
var worldOrigin = Marshal.GetObjectForIUnknown(spatialCoordinateSystemPtr) as Windows.Perception.Spatial.SpatialCoordinateSystem;
#endif
```

### <a name="converting-between-coordinate-systems"></a><span data-ttu-id="72c84-112">Conversione tra sistemi di coordinate</span><span class="sxs-lookup"><span data-stu-id="72c84-112">Converting between coordinate systems</span></span>

<span data-ttu-id="72c84-113">Unity usa un sistema di coordinate di sinistra, mentre le API di percezione di Windows usano sistemi di coordinate di destra.</span><span class="sxs-lookup"><span data-stu-id="72c84-113">Unity uses a left-handed coordinate system, while the Windows Perception APIs use right-handed coordinate systems.</span></span> <span data-ttu-id="72c84-114">Per eseguire la conversione tra queste due convenzioni, è possibile usare gli helper seguenti:</span><span class="sxs-lookup"><span data-stu-id="72c84-114">To convert between these two conventions, you can use the following helpers:</span></span>

```cs
namespace NumericsConversion
{
    public static class NumericsConversionExtensions
    {
        public static UnityEngine.Vector3 ToUnity(this System.Numerics.Vector3 v) => new UnityEngine.Vector3(v.X, v.Y, -v.Z);
        public static UnityEngine.Quaternion ToUnity(this System.Numerics.Quaternion q) => new UnityEngine.Quaternion(q.X, q.Y, -q.Z, -q.W);
        public static UnityEngine.Matrix4x4 ToUnity(this System.Numerics.Matrix4x4 m) => new UnityEngine.Matrix4x4(
            new Vector4( m.M11,  m.M12, -m.M13,  m.M14),
            new Vector4( m.M21,  m.M22, -m.M23,  m.M24),
            new Vector4(-m.M31, -m.M32,  m.M33, -m.M34),
            new Vector4( m.M41,  m.M42, -m.M43,  m.M44));

        public static System.Numerics.Vector3 ToSystem(this UnityEngine.Vector3 v) => new System.Numerics.Vector3(v.x, v.y, -v.z);
        public static System.Numerics.Quaternion ToSystem(this UnityEngine.Quaternion q) => new System.Numerics.Quaternion(q.x, q.y, -q.z, -q.w);
        public static System.Numerics.Matrix4x4 ToSystem(this UnityEngine.Matrix4x4 m) => new System.Numerics.Matrix4x4(
            m.m00,  m.m10, -m.m20,  m.m30,
            m.m01,  m.m11, -m.m21,  m.m31,
           -m.m02, -m.m12,  m.m22, -m.m32,
            m.m03,  m.m13, -m.m23,  m.m33);
    }
}
```

### <a name="using-holographicframe-native-data"></a><span data-ttu-id="72c84-115">Uso di dati nativi HolographicFrame</span><span class="sxs-lookup"><span data-stu-id="72c84-115">Using HolographicFrame native data</span></span>

> [!NOTE]
> <span data-ttu-id="72c84-116">La modifica dello stato degli oggetti nativi ricevuti tramite HolographicFrameNativeData può causare un comportamento imprevedibile e gli artefatti di rendering, soprattutto se Unity ne causa anche lo stesso stato.</span><span class="sxs-lookup"><span data-stu-id="72c84-116">Changing the state of the native objects received via HolographicFrameNativeData may cause unpredictable behavior and rendering artifacts, especially if Unity also reasons about that same state.</span></span>  <span data-ttu-id="72c84-117">Ad esempio, non è necessario chiamare HolographicFrame. UpdateCurrentPrediction. in caso contrario, la stima di pose che Unity esegue il rendering con tale frame non sarà sincronizzata con la funzione prevista da Windows, riducendo la [stabilità dell'ologramma](../platform-capabilities-and-apis/hologram-stability.md).</span><span class="sxs-lookup"><span data-stu-id="72c84-117">For example, you should not call HolographicFrame.UpdateCurrentPrediction, or else the pose prediction that Unity renders with that frame will be out of sync with the pose that Windows is expecting, which will reduce [hologram stability](../platform-capabilities-and-apis/hologram-stability.md).</span></span>

<span data-ttu-id="72c84-118">Se è necessario accedere alle interfacce native a scopo di rendering o di debug, usare i dati di HolographicFrameNativeData nei plug-in nativi o nel codice C#.</span><span class="sxs-lookup"><span data-stu-id="72c84-118">If you need access to native interfaces for rendering or debugging purposes, use data from HolographicFrameNativeData in your native plugins or C# code.</span></span>

<span data-ttu-id="72c84-119">Di seguito è riportato un esempio di come è possibile usare HolographicFrameNativeData per ottenere la stima del frame corrente per il tempo del fotone usando le estensioni di XR SDK.</span><span class="sxs-lookup"><span data-stu-id="72c84-119">Here's an example of how you can use HolographicFrameNativeData to get the current frame's prediction for photon time using the XR SDK extensions.</span></span>

```cs
using System;
using System.Runtime.InteropServices;

public static bool GetCurrentFrameDateTime(out DateTime frameDateTime)
{
#if ENABLE_WINMD_SUPPORT
    IntPtr holographicFramePtr = UnityEngine.XR.WindowsMR.WindowsMREnvironment.CurrentHolographicRenderFrame;

    if (holographicFramePtr != IntPtr.Zero)
    {
        var holographicFrame = Marshal.GetObjectForIUnknown(holographicFramePtr) as Windows.Graphics.Holographic.HolographicFrame;
        frameDateTime = holographicFrame.CurrentPrediction.Timestamp.TargetTime.DateTime;
        return true;
    }
#endif

    frameDateTime = DateTime.MinValue;
    return false;
}
```

## <a name="see-also"></a><span data-ttu-id="72c84-120">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="72c84-120">See Also</span></span>

* [<span data-ttu-id="72c84-121">Uso dello spazio dei nomi Windows con le app Unity per HoloLens</span><span class="sxs-lookup"><span data-stu-id="72c84-121">Using the Windows namespace with Unity apps for HoloLens</span></span>](using-the-windows-namespace-with-unity-apps-for-hololens.md)
* <span data-ttu-id="72c84-122"><a href="/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">SpatialCoordinateSystem</a></span><span class="sxs-lookup"><span data-stu-id="72c84-122"><a href="/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">SpatialCoordinateSystem</a></span></span>
* <span data-ttu-id="72c84-123"><a href="/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a></span><span class="sxs-lookup"><span data-stu-id="72c84-123"><a href="/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a></span></span>
* <span data-ttu-id="72c84-124"><a href="/uwp/api/windows.graphics.holographic.holographiccamera" target="_blank">HolographicCamera</a></span><span class="sxs-lookup"><span data-stu-id="72c84-124"><a href="/uwp/api/windows.graphics.holographic.holographiccamera" target="_blank">HolographicCamera</a></span></span>
* [<span data-ttu-id="72c84-125">Rendering in DirectX</span><span class="sxs-lookup"><span data-stu-id="72c84-125">Rendering in DirectX</span></span>](../native/rendering-in-directx.md)

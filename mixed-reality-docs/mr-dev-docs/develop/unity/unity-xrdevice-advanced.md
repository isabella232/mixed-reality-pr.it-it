---
title: Oggetti nativi di realtà mista in Unity
description: Ottenere l'accesso agli oggetti nativi olografici sottostanti in Unity.
author: vladkol
ms.author: vladkol
ms.date: 05/20/2018
ms.topic: article
keywords: Unity, realtà mista, nativa, xrdevice, spatialcoordinatesystem, holographicframe, holographiccamera, ispatialcoordinatesystem, iholographicframe, iholographiccamera, getnativeptr, auricolare realtà mista, headset di realtà mista di Windows, auricolare della realtà virtuale
ms.openlocfilehash: 8dda1152da9705147ca3a057faadb9edd8428df6
ms.sourcegitcommit: 87b54c75044f433cfadda68ca71c1165608e2f4b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/10/2020
ms.locfileid: "97010592"
---
# <a name="mixed-reality-native-objects-in-unity"></a><span data-ttu-id="d722a-104">Oggetti nativi di realtà mista in Unity</span><span class="sxs-lookup"><span data-stu-id="d722a-104">Mixed Reality native objects in Unity</span></span>

<span data-ttu-id="d722a-105">Ogni app di realtà mista [ottiene un HolographicSpace prima di iniziare a](../native/getting-a-holographicspace.md) ricevere i dati della fotocamera e i frame di rendering.</span><span class="sxs-lookup"><span data-stu-id="d722a-105">Every Mixed Reality app [gets a HolographicSpace](../native/getting-a-holographicspace.md) before it starts receiving camera data and rendering frames.</span></span> <span data-ttu-id="d722a-106">In Unity, il motore esegue automaticamente questi passaggi, gestendo gli oggetti olografici e aggiornando internamente come parte del ciclo di rendering.</span><span class="sxs-lookup"><span data-stu-id="d722a-106">In Unity, the engine takes care of those steps for you, handling Holographic objects and internally updating as part of its render loop.</span></span>

<span data-ttu-id="d722a-107">Negli scenari avanzati potrebbe tuttavia essere necessario ottenere l'accesso agli oggetti nativi sottostanti, ad esempio <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera" target="_blank">HolographicCamera</a> e <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a>corrente.</span><span class="sxs-lookup"><span data-stu-id="d722a-107">However, in advanced scenarios you may need to get access to the underlying native objects, such as the <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera" target="_blank">HolographicCamera</a> and current <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a>.</span></span> <span data-ttu-id="d722a-108"><a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.html" target="_blank">UnityEngine. XR. XRDevice</a> fornisce l'accesso a questi oggetti nativi.</span><span class="sxs-lookup"><span data-stu-id="d722a-108"><a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.html" target="_blank">UnityEngine.XR.XRDevice</a> is what provides access to these native objects.</span></span>

## <a name="xrdevice"></a><span data-ttu-id="d722a-109">XRDevice</span><span class="sxs-lookup"><span data-stu-id="d722a-109">XRDevice</span></span> 

<span data-ttu-id="d722a-110">**Spazio dei nomi:** *UnityEngine. XR*</span><span class="sxs-lookup"><span data-stu-id="d722a-110">**Namespace:** *UnityEngine.XR*</span></span><br>
<span data-ttu-id="d722a-111">**Tipo:** *XRDevice*</span><span class="sxs-lookup"><span data-stu-id="d722a-111">**Type:** *XRDevice*</span></span>

<span data-ttu-id="d722a-112">Il tipo *XRDevice* consente di ottenere l'accesso agli oggetti nativi sottostanti usando il metodo <a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.GetNativePtr.html" target="_blank">GetNativePtr</a> .</span><span class="sxs-lookup"><span data-stu-id="d722a-112">The *XRDevice* type allows you to get access to underlying native objects using the <a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.GetNativePtr.html" target="_blank">GetNativePtr</a> method.</span></span> <span data-ttu-id="d722a-113">Il risultato restituito da GetNativePtr varia in base alle diverse piattaforme.</span><span class="sxs-lookup"><span data-stu-id="d722a-113">What GetNativePtr returns varies between different platforms.</span></span> <span data-ttu-id="d722a-114">Nel piattaforma UWP (Universal Windows Platform), quando la destinazione è Windows Mixed Reality XR SDK, XRDevice. GetNativePtr restituisce un puntatore (IntPtr) alla struttura seguente:</span><span class="sxs-lookup"><span data-stu-id="d722a-114">On the Universal Windows Platform, when targeting the Windows Mixed Reality XR SDK, XRDevice.GetNativePtr returns a pointer (IntPtr) to the following structure:</span></span> 

```cs
using System;
using System.Runtime.InteropServices;

[StructLayout(LayoutKind.Sequential)]
struct HolographicFrameNativeData
{
    public uint VersionNumber;
    public uint MaxNumberOfCameras;
    public IntPtr ISpatialCoordinateSystemPtr; // Windows::Perception::Spatial::ISpatialCoordinateSystem
    public IntPtr IHolographicFramePtr; // Windows::Graphics::Holographic::IHolographicFrame 
    public IntPtr IHolographicCameraPtr; // // Windows::Graphics::Holographic::IHolographicCamera
}
```
<span data-ttu-id="d722a-115">È possibile convertirlo in HolographicFrameNativeData usando il metodo Marshal. PtrToStructure:</span><span class="sxs-lookup"><span data-stu-id="d722a-115">You can convert it to HolographicFrameNativeData using Marshal.PtrToStructure method:</span></span>
```cs
var nativePtr = UnityEngine.XR.XRDevice.GetNativePtr();
HolographicFrameNativeData hfd = Marshal.PtrToStructure<HolographicFrameNativeData>(nativePtr);
```
<span data-ttu-id="d722a-116">***IHolographicCameraPtr** è una matrice di IntPtr sottoposta a marshalling come UnmanagedType. ByValArray con una lunghezza uguale a MaxNumberOfCameras*</span><span class="sxs-lookup"><span data-stu-id="d722a-116">***IHolographicCameraPtr** is an array of IntPtr marshaled as UnmanagedType.ByValArray with a length equal to MaxNumberOfCameras*</span></span> 

### <a name="unmarshaling-native-pointers"></a><span data-ttu-id="d722a-117">Unmarshalling di puntatori nativi</span><span class="sxs-lookup"><span data-stu-id="d722a-117">Unmarshaling native pointers</span></span>

<span data-ttu-id="d722a-118">Se si usa [Microsoft. Windows. MixedReality. DotNetWinRT](https://www.nuget.org/packages/Microsoft.Windows.MixedReality.DotNetWinRT), è possibile costruire un oggetto gestito da un puntatore nativo usando il `FromNativePtr()` Metodo:</span><span class="sxs-lookup"><span data-stu-id="d722a-118">If you are using [Microsoft.Windows.MixedReality.DotNetWinRT](https://www.nuget.org/packages/Microsoft.Windows.MixedReality.DotNetWinRT), you can construct a managed object from a native pointer using the `FromNativePtr()` method:</span></span>

```cs
var worldOrigin = Microsoft.Windows.Perception.Spatial.SpatialCoordinateSystem.FromNativePtr(hfd.ISpatialCoordinateSystemPtr);
```

<span data-ttu-id="d722a-119">In caso contrario, utilizzare `Marshal.GetObjectForIUnknown()` ed eseguire il cast al tipo desiderato:</span><span class="sxs-lookup"><span data-stu-id="d722a-119">Otherwise, use `Marshal.GetObjectForIUnknown()` and cast to the type you want:</span></span>

```cs
#if ENABLE_WINMD_SUPPORT
var worldOrigin = (Windows.Perception.Spatial.SpatialCoordinateSystem)Marshal.GetObjectForIUnknown(hfd.ISpatialCoordinateSystemPtr);
#endif
```

### <a name="converting-between-coordinate-systems"></a><span data-ttu-id="d722a-120">Conversione tra sistemi di coordinate</span><span class="sxs-lookup"><span data-stu-id="d722a-120">Converting between coordinate systems</span></span>

<span data-ttu-id="d722a-121">Unity usa un sistema di coordinate di sinistra, mentre le API di percezione di Windows usano sistemi di coordinate di destra.</span><span class="sxs-lookup"><span data-stu-id="d722a-121">Unity uses a left-handed coordinate system, while the Windows Perception APIs use right-handed coordinate systems.</span></span> <span data-ttu-id="d722a-122">Per eseguire la conversione tra queste due convenzioni, è possibile usare gli helper seguenti:</span><span class="sxs-lookup"><span data-stu-id="d722a-122">To convert between these two conventions, you can use the following helpers:</span></span>

```cs
namespace NumericsConversion
{
    public static class NumericsConversionExtensions
    {
        public static UnityEngine.Vector3 ToUnity(this System.Numerics.Vector3 v) => new UnityEngine.Vector3(v.X, v.Y, -v.Z);
        public static UnityEngine.Quaternion ToUnity(this System.Numerics.Quaternion q) => new UnityEngine.Quaternion(-q.X, -q.Y, q.Z, q.W);
        public static UnityEngine.Matrix4x4 ToUnity(this System.Numerics.Matrix4x4 m) => new UnityEngine.Matrix4x4(
            new Vector4( m.M11,  m.M12, -m.M13,  m.M14),
            new Vector4( m.M21,  m.M22, -m.M23,  m.M24),
            new Vector4(-m.M31, -m.M32,  m.M33, -m.M34),
            new Vector4( m.M41,  m.M42, -m.M43,  m.M44));

        public static System.Numerics.Vector3 ToSystem(this UnityEngine.Vector3 v) => new System.Numerics.Vector3(v.x, v.y, -v.z);
        public static System.Numerics.Quaternion ToSystem(this UnityEngine.Quaternion q) => new System.Numerics.Quaternion(-q.x, -q.y, q.z, q.w);
        public static System.Numerics.Matrix4x4 ToSystem(this UnityEngine.Matrix4x4 m) => new System.Numerics.Matrix4x4(
            m.m00,  m.m10, -m.m20,  m.m30,
            m.m01,  m.m11, -m.m21,  m.m31,
           -m.m02, -m.m12,  m.m22, -m.m32,
            m.m03,  m.m13, -m.m23,  m.m33);
    }
}
```

### <a name="using-holographicframe-native-data"></a><span data-ttu-id="d722a-123">Uso di dati nativi HolographicFrame</span><span class="sxs-lookup"><span data-stu-id="d722a-123">Using HolographicFrame native data</span></span>

> [!NOTE]
> <span data-ttu-id="d722a-124">La modifica dello stato degli oggetti nativi ricevuti tramite HolographicFrameNativeData può causare un comportamento imprevedibile e gli artefatti di rendering, soprattutto se Unity ne causa anche lo stesso stato.</span><span class="sxs-lookup"><span data-stu-id="d722a-124">Changing the state of the native objects received via HolographicFrameNativeData may cause unpredictable behaviour and rendering artifacts, especially if Unity also reasons about that same state.</span></span>  <span data-ttu-id="d722a-125">Ad esempio, non è necessario chiamare HolographicFrame. UpdateCurrentPrediction. in caso contrario, la stima di pose che Unity esegue il rendering con tale frame non sarà sincronizzata con la funzione prevista da Windows, riducendo la [stabilità dell'ologramma](../platform-capabilities-and-apis/hologram-stability.md).</span><span class="sxs-lookup"><span data-stu-id="d722a-125">For example, you should not call HolographicFrame.UpdateCurrentPrediction, or else the pose prediction that Unity renders with that frame will be out of sync with the pose that Windows is expecting, which will reduce [hologram stability](../platform-capabilities-and-apis/hologram-stability.md).</span></span>

<span data-ttu-id="d722a-126">Se è necessario accedere alle interfacce native a scopo di rendering o di debug, usare i dati di HolographicFrameNativeData nei plug-in nativi o nel codice C#.</span><span class="sxs-lookup"><span data-stu-id="d722a-126">If you need access to native interfaces for rendering or debugging purposes, use data from HolographicFrameNativeData in your native plugins or C# code.</span></span> 

<span data-ttu-id="d722a-127">Di seguito è riportato un esempio di come è possibile usare HolographicFrameNativeData per ottenere la stima del frame corrente per il tempo del fotone.</span><span class="sxs-lookup"><span data-stu-id="d722a-127">Here's an example of how you can use HolographicFrameNativeData to get the current frame's prediction for photon time.</span></span> 

```cs
using System;
using System.Runtime.InteropServices;

public static bool GetCurrentFrameDateTime(out DateTime frameDateTime)
{
#if (!UNITY_EDITOR && UNITY_WSA) || ENABLE_WINMD_SUPPORT
    IntPtr nativeStruct = UnityEngine.XR.XRDevice.GetNativePtr();

    if (nativeStruct != IntPtr.Zero)
    {
        HolographicFrameNativeData hfd = Marshal.PtrToStructure<HolographicFrameNativeData>(nativeStruct);

        if (hfd.IHolographicFramePtr != IntPtr.Zero)
        {
            var holographicFrame = (Windows.Graphics.Holographic.HolographicFrame)Marshal.GetObjectForIUnknown(hfd.IHolographicFramePtr);
            frameDateTime = holographicFrame.CurrentPrediction.Timestamp.TargetTime.DateTime;
            return true;
        }
    }

#endif

    frameDateTime = DateTime.MinValue;
    return false;
}

```

## <a name="see-also"></a><span data-ttu-id="d722a-128">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="d722a-128">See Also</span></span>
* [<span data-ttu-id="d722a-129">Uso dello spazio dei nomi Windows con le app Unity per HoloLens</span><span class="sxs-lookup"><span data-stu-id="d722a-129">Using the Windows namespace with Unity apps for HoloLens</span></span>](using-the-windows-namespace-with-unity-apps-for-hololens.md)
* <span data-ttu-id="d722a-130"><a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">SpatialCoordinateSystem</a></span><span class="sxs-lookup"><span data-stu-id="d722a-130"><a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">SpatialCoordinateSystem</a></span></span>
* <span data-ttu-id="d722a-131"><a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a></span><span class="sxs-lookup"><span data-stu-id="d722a-131"><a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a></span></span>
* <span data-ttu-id="d722a-132"><a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera" target="_blank">HolographicCamera</a></span><span class="sxs-lookup"><span data-stu-id="d722a-132"><a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera" target="_blank">HolographicCamera</a></span></span>
* [<span data-ttu-id="d722a-133">Rendering in DirectX</span><span class="sxs-lookup"><span data-stu-id="d722a-133">Rendering in DirectX</span></span>](../native/rendering-in-directx.md)

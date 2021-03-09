---
ms.openlocfilehash: 612168d7a1e56f74350ee8244e26e5ad886503c2
ms.sourcegitcommit: 441ef99e6090081c6cd3aa88ed21e13e941f0cc6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/09/2021
ms.locfileid: "102475076"
---
# <a name="mrtk"></a>[MRTK](#tab/mrtk)

## <a name="windowsmixedrealityutilities"></a>WindowsMixedRealityUtilities

**Spazio dei nomi:** *Microsoft. MixedReality. Toolkit. WindowsMixedReality*<br>
**Tipo:** *WindowsMixedRealityUtilities*

MRTK fornisce tipi già sottoposta a marshalling sia per la versione precedente di WSA che per XR SDK tramite la classe **WindowsMixedRealityUtilities** .

```cs
public static HolographicFrame CurrentHolographicFrame { get; }
public static SpatialCoordinateSystem SpatialCoordinateSystem { get; }
public static SpatialInteractionManager SpatialInteractionManager { get; }
```

# <a name="xr-sdk"></a>[SDK XR](#tab/xr)

## <a name="windowsmrenvironment"></a>WindowsMREnvironment

**Spazio dei nomi:** *UnityEngine. XR. WindowsMR*<br>
**Tipo:** *WindowsMREnvironment*

La classe statica **WindowsMREnvironment** fornisce l'accesso a diversi puntatori nativi.

```cs
public static IntPtr CurrentHolographicRenderFrame { get; } // Windows::Graphics::Holographic::IHolographicFrame
public static IntPtr HolographicSpace { get; } // Windows::Graphics::Holographic::IHolographicSpace
public static IntPtr OriginSpatialCoordinateSystem { get; } // Windows::Perception::Spatial::ISpatialCoordinateSystem
```

# <a name="legacy-wsa"></a>[WSA legacy](#tab/wsa)

## <a name="xrdevice"></a>XRDevice

**Spazio dei nomi:** *UnityEngine. XR*<br>
**Tipo:** *XRDevice*

Il tipo <a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.html" target="_blank">**XRDevice**</a> consente di ottenere l'accesso agli oggetti nativi sottostanti usando il metodo <a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.GetNativePtr.html" target="_blank">GetNativePtr</a> . Il risultato restituito da GetNativePtr varia in base alle diverse piattaforme. Nel piattaforma UWP (Universal Windows Platform) quando la destinazione è la realtà mista di Windows, XRDevice. GetNativePtr restituisce un puntatore (IntPtr) alla struttura seguente:

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
    public IntPtr IHolographicCameraPtr; // Windows::Graphics::Holographic::IHolographicCamera
}
```

È possibile convertirlo in HolographicFrameNativeData usando il metodo Marshal. PtrToStructure:

```cs
IntPtr nativePtr = UnityEngine.XR.XRDevice.GetNativePtr();
HolographicFrameNativeData hfd = Marshal.PtrToStructure<HolographicFrameNativeData>(nativePtr);
```

***IHolographicCameraPtr** è una matrice di IntPtr sottoposta a marshalling come UnmanagedType. ByValArray con una lunghezza uguale a MaxNumberOfCameras*

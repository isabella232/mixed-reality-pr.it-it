---
ms.openlocfilehash: 78296dd4e6667c34926c954774547b21a223c5f4b6635476c51046c7ca22cdc3
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115208402"
---
# <a name="mrtk"></a>[MRTK](#tab/mrtk)

## <a name="windowsmixedrealityutilities"></a>WindowsMixedRealityUtilities

**Spazio dei nomi:** *Microsoft.MixedReality.Toolkit. WindowsMixedReality*<br>
**Tipo:** *WindowsMixedRealityUtilities*

MRTK fornisce tipi già marshalling tra WSA legacy e XR SDK tramite la **classe WindowsMixedRealityUtilities.**

```cs
public static HolographicFrame CurrentHolographicFrame { get; }
public static SpatialCoordinateSystem SpatialCoordinateSystem { get; }
public static SpatialInteractionManager SpatialInteractionManager { get; }
```

# <a name="xr-sdk"></a>[XR SDK](#tab/xr)

## <a name="windowsmrenvironment"></a>WindowsMREnvironment

**Spazio dei nomi:** *UnityEngine.XR.WindowsMR*<br>
**Tipo:** *WindowsMREnvironment*

La classe **statica WindowsMREnvironment** fornisce l'accesso a diversi puntatori nativi.

```cs
public static IntPtr CurrentHolographicRenderFrame { get; } // Windows::Graphics::Holographic::IHolographicFrame
public static IntPtr HolographicSpace { get; } // Windows::Graphics::Holographic::IHolographicSpace
public static IntPtr OriginSpatialCoordinateSystem { get; } // Windows::Perception::Spatial::ISpatialCoordinateSystem
```

# <a name="legacy-wsa"></a>[Legacy WSA](#tab/wsa)

## <a name="xrdevice"></a>XRDevice

**Spazio dei nomi:** *UnityEngine.XR*<br>
**Tipo:** *XRDevice*

Il <a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.html" target="_blank">**tipo XRDevice**</a> consente di ottenere l'accesso agli oggetti nativi sottostanti usando il <a href="https://docs.unity3d.com/ScriptReference/XR.XRDevice.GetNativePtr.html" target="_blank">metodo GetNativePtr.</a> Il valore restituito da GetNativePtr varia a seconda delle diverse piattaforme. Nella piattaforma universal Windows quando la destinazione è Windows Mixed Reality, XRDevice.GetNativePtr restituisce un puntatore (IntPtr) alla struttura seguente:

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

È possibile convertirlo in HolographicFrameNativeData usando il metodo Marshal.PtrToStructure:

```cs
IntPtr nativePtr = UnityEngine.XR.XRDevice.GetNativePtr();
HolographicFrameNativeData hfd = Marshal.PtrToStructure<HolographicFrameNativeData>(nativePtr);
```

***IHolographicCameraPtr** è una matrice di IntPtr con marshalling come UnmanagedType.ByValArray con una lunghezza uguale a MaxNumberOfCameras*

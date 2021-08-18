---
ms.openlocfilehash: c3775dc73f41b822c233d8fc4ec62459e789b89f
ms.sourcegitcommit: 191c3d89c034714377d09fa91c07cbaa81301bae
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122261156"
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

# <a name="windows-xr-plugin"></a>[Windows Plug-in XR](#tab/xr)

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

***IHolographicCameraPtr** è una matrice di IntPtr con marshalling come UnmanagedType.ByValArray con lunghezza uguale a MaxNumberOfCameras*

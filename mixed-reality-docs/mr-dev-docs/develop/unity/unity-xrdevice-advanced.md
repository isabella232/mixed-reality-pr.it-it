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
# <a name="mixed-reality-native-interop-in-unity"></a>Interoperabilità nativa in realtà mista in Unity

Ogni app di realtà mista [ottiene un HolographicSpace prima di iniziare a](../native/getting-a-holographicspace.md) ricevere i dati della fotocamera e i frame di rendering. In Unity, il motore esegue automaticamente questi passaggi, gestendo gli oggetti olografici e aggiornando internamente come parte del ciclo di rendering.

Negli scenari avanzati potrebbe tuttavia essere necessario ottenere l'accesso agli oggetti nativi sottostanti, ad esempio <a href="/uwp/api/windows.graphics.holographic.holographiccamera" target="_blank">HolographicCamera</a> e <a href="/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a>corrente.

[!INCLUDE[](includes/unity-native-ptrs.md)]

### <a name="unmarshaling-native-pointers"></a>Unmarshalling di puntatori nativi

Dopo avere ottenuto `IntPtr` da uno dei metodi precedenti (non necessario per MRTK), usare i frammenti di codice seguenti per effettuare il marshalling degli oggetti gestiti.

Se si usa [Microsoft. Windows. MixedReality. DotNetWinRT](https://www.nuget.org/packages/Microsoft.Windows.MixedReality.DotNetWinRT), è possibile costruire un oggetto gestito da un puntatore nativo usando il `FromNativePtr()` Metodo:

```cs
var worldOrigin = Microsoft.Windows.Perception.Spatial.SpatialCoordinateSystem.FromNativePtr(spatialCoordinateSystemPtr);
```

In caso contrario, utilizzare `Marshal.GetObjectForIUnknown()` ed eseguire il cast al tipo desiderato:

```cs
#if ENABLE_WINMD_SUPPORT
var worldOrigin = Marshal.GetObjectForIUnknown(spatialCoordinateSystemPtr) as Windows.Perception.Spatial.SpatialCoordinateSystem;
#endif
```

### <a name="converting-between-coordinate-systems"></a>Conversione tra sistemi di coordinate

Unity usa un sistema di coordinate di sinistra, mentre le API di percezione di Windows usano sistemi di coordinate di destra. Per eseguire la conversione tra queste due convenzioni, è possibile usare gli helper seguenti:

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

### <a name="using-holographicframe-native-data"></a>Uso di dati nativi HolographicFrame

> [!NOTE]
> La modifica dello stato degli oggetti nativi ricevuti tramite HolographicFrameNativeData può causare un comportamento imprevedibile e gli artefatti di rendering, soprattutto se Unity ne causa anche lo stesso stato.  Ad esempio, non è necessario chiamare HolographicFrame. UpdateCurrentPrediction. in caso contrario, la stima di pose che Unity esegue il rendering con tale frame non sarà sincronizzata con la funzione prevista da Windows, riducendo la [stabilità dell'ologramma](../platform-capabilities-and-apis/hologram-stability.md).

Se è necessario accedere alle interfacce native a scopo di rendering o di debug, usare i dati di HolographicFrameNativeData nei plug-in nativi o nel codice C#.

Di seguito è riportato un esempio di come è possibile usare HolographicFrameNativeData per ottenere la stima del frame corrente per il tempo del fotone usando le estensioni di XR SDK.

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

## <a name="see-also"></a>Vedere anche

* [Uso dello spazio dei nomi Windows con le app Unity per HoloLens](using-the-windows-namespace-with-unity-apps-for-hololens.md)
* <a href="/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">SpatialCoordinateSystem</a>
* <a href="/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a>
* <a href="/uwp/api/windows.graphics.holographic.holographiccamera" target="_blank">HolographicCamera</a>
* [Rendering in DirectX](../native/rendering-in-directx.md)

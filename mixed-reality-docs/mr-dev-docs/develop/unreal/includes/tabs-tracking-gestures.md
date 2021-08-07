---
ms.openlocfilehash: fa21b1a5c3c89cf3c1c63c7ed8ebbdc3d8547661443853987ee3713e50c50e5c
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115187413"
---
# <a name="426"></a>[4.26](#tab/426)

### <a name="windows-mixed-reality"></a>Windows Mixed Reality

![Progetto di inizio riproduzione evento connesso per configurare la funzione dei movimenti](../images/unreal-hand-tracking-img-09.png)

È quindi necessario aggiungere il codice per sottoscrivere gli eventi seguenti:

![Progetto di Windows movimenti di tocco, tocco e manipolazione a sinistra dello Windows del tocco per l'input spaziale nel pannello ](../images/unreal/key-events.png)
 ![ dei dettagli](../images/unreal/key-events2.png)

### <a name="openxr"></a>OpenXR

In OpenXR gli eventi di movimento vengono registrati tramite la pipeline di input. Usando l'interazione manuale, il dispositivo può riconoscere automaticamente i movimenti Tocco e Tieni premuto, ma non gli altri. Sono denominati mapping OpenXRMsftHandInteraction Select e Grip. Non è necessario abilitare la sottoscrizione. È consigliabile dichiarare gli eventi in Project Impostazioni/Engine/Input, come illustrato di seguito:

![Screenshot dei mapping delle azioni OpenXR](../images/unreal-hand-tracking-img-12.png)

# <a name="425"></a>[4.25](#tab/425)

È possibile trovare la funzione Blueprint in in **Windows Mixed Reality Spatial Input (Input** spaziale) e la funzione C++ aggiungendo `WindowsMixedRealitySpatialInputFunctionLibrary.h` nel file di codice chiamante.

![Movimenti di acquisizione](../images/unreal/capture-gestures.png)

### <a name="enum"></a>Enumerazione
<!-- Deprecated
The `ESPatialInputAxisGestureType` enum describes spatial axis gestures and are [fully documented](../../out-of-scope/deprecated/holograms-211.md).
-->
Progetto:

![Tipo di movimento](../images/unreal/gesture-type.png)

C++:
```cpp
enum class ESpatialInputAxisGestureType : uint8
{
    None = 0,
    Manipulation = 1,
    Navigation = 2,
    NavigationRails = 3
};
```

### <a name="function"></a>Funzione
È possibile abilitare e disabilitare l'acquisizione movimenti con la `CaptureGestures` funzione . Quando un movimento abilitato attiva eventi di input, la funzione restituisce se l'acquisizione del movimento ha esito positivo e se `true` `false` si verifica un errore.

Progetto:

![Acquisizione movimenti BP](../images/unreal/capture-gestures-bp.png)

C++:
```cpp
static bool UWindowsMixedRealitySpatialInputFunctionLibrary::CaptureGestures(
    bool Tap = false,
    bool Hold = false,
    ESpatialInputAxisGestureType AxisGesture = ESpatialInputAxisGestureType::None,
    bool NavigationAxisX = true,
    bool NavigationAxisY = true,
    bool NavigationAxisZ = true);
```

Di seguito sono riportati gli eventi chiave, disponibili in Blueprints e C++: Key Events (Progetti e C++: ![ Eventi chiave).](../images/unreal/key-events.png)

![Eventi chiave 2](../images/unreal/key-events2.png)
```cpp
const FKey FSpatialInputKeys::TapGesture(TapGestureName);
const FKey FSpatialInputKeys::DoubleTapGesture(DoubleTapGestureName);
const FKey FSpatialInputKeys::HoldGesture(HoldGestureName);

const FKey FSpatialInputKeys::LeftTapGesture(LeftTapGestureName);
const FKey FSpatialInputKeys::LeftDoubleTapGesture(LeftDoubleTapGestureName);
const FKey FSpatialInputKeys::LeftHoldGesture(LeftHoldGestureName);

const FKey FSpatialInputKeys::RightTapGesture(RightTapGestureName);
const FKey FSpatialInputKeys::RightDoubleTapGesture(RightDoubleTapGestureName);
const FKey FSpatialInputKeys::RightHoldGesture(RightHoldGestureName);

const FKey FSpatialInputKeys::LeftManipulationGesture(LeftManipulationGestureName);
const FKey FSpatialInputKeys::LeftManipulationXGesture(LeftManipulationXGestureName);
const FKey FSpatialInputKeys::LeftManipulationYGesture(LeftManipulationYGestureName);
const FKey FSpatialInputKeys::LeftManipulationZGesture(LeftManipulationZGestureName);

const FKey FSpatialInputKeys::LeftNavigationGesture(LeftNavigationGestureName);
const FKey FSpatialInputKeys::LeftNavigationXGesture(LeftNavigationXGestureName);
const FKey FSpatialInputKeys::LeftNavigationYGesture(LeftNavigationYGestureName);
const FKey FSpatialInputKeys::LeftNavigationZGesture(LeftNavigationZGestureName);


const FKey FSpatialInputKeys::RightManipulationGesture(RightManipulationGestureName);
const FKey FSpatialInputKeys::RightManipulationXGesture(RightManipulationXGestureName);
const FKey FSpatialInputKeys::RightManipulationYGesture(RightManipulationYGestureName);
const FKey FSpatialInputKeys::RightManipulationZGesture(RightManipulationZGestureName);

const FKey FSpatialInputKeys::RightNavigationGesture(RightNavigationGestureName);
const FKey FSpatialInputKeys::RightNavigationXGesture(RightNavigationXGestureName);
const FKey FSpatialInputKeys::RightNavigationYGesture(RightNavigationYGestureName);
const FKey FSpatialInputKeys::RightNavigationZGesture(RightNavigationZGestureName);
```


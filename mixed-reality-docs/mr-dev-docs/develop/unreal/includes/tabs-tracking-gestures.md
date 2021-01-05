---
ms.openlocfilehash: 6b9223481ed909961dbb88d03e4b55ef68448525
ms.sourcegitcommit: 13ef9f89ee61fbfe547ecf5fdfdb97560a0de833
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2020
ms.locfileid: "97717915"
---
# <a name="426"></a>[4.26](#tab/426)

### <a name="windows-mixed-reality"></a>Windows Mixed Reality

![Progetto di inizio riproduzione connessione per la funzione configura movimenti](../images/unreal-hand-tracking-img-09.png)

Quindi, è necessario aggiungere il codice per sottoscrivere gli eventi seguenti:

![Progetto dello screenshot dei movimenti di input di input spaziali Windows, tap e Left Manipulation ](../images/unreal/key-events.png)
 ![ delle opzioni dei movimenti di tocco di input spaziali di Windows nel pannello dei dettagli](../images/unreal/key-events2.png)

### <a name="openxr"></a>OpenXR

In OpenXR, gli eventi di movimento vengono rilevati tramite la pipeline di input. Usando l'interazione manuale, il dispositivo può riconoscere automaticamente i movimenti Tap e di attesa, ma non gli altri. Sono denominati OpenXRMsftHandInteraction Select e i mapping del grip. Non è necessario abilitare la sottoscrizione, dichiarare gli eventi in impostazioni/motore/input del progetto, in modo analogo a quanto segue:

![Screenshot dei mapping delle azioni OpenXR](../images/unreal-hand-tracking-img-12.png)

# <a name="425"></a>[4.25](#tab/425)

È possibile trovare la funzione Blueprint in **input spaziale di realtà mista di Windows** e la funzione C++ aggiungendo `WindowsMixedRealitySpatialInputFunctionLibrary.h` nel file di codice chiamante.

![Acquisisci movimenti](../images/unreal/capture-gestures.png)

### <a name="enum"></a>Enumerazione
<!-- Deprecated
The `ESPatialInputAxisGestureType` enum describes spatial axis gestures and are [fully documented](../../out-of-scope/deprecated/holograms-211.md).
-->
Progetto

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
È possibile abilitare e disabilitare l'acquisizione di movimenti con la `CaptureGestures` funzione. Quando un movimento abilitato genera eventi di input, la funzione restituisce `true` se l'acquisizione del movimento riesce e `false` se si verifica un errore.

Progetto

![Movimenti di acquisizione BP](../images/unreal/capture-gestures-bp.png)

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

Di seguito sono riportati gli eventi chiave che è possibile trovare in progetti e C++: ![ eventi chiave](../images/unreal/key-events.png)

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


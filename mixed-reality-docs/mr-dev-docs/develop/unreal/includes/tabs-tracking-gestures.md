---
ms.openlocfilehash: 6b9223481ed909961dbb88d03e4b55ef68448525
ms.sourcegitcommit: 13ef9f89ee61fbfe547ecf5fdfdb97560a0de833
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2020
ms.locfileid: "97717915"
---
# <a name="426"></a>[<span data-ttu-id="e2b06-101">4.26</span><span class="sxs-lookup"><span data-stu-id="e2b06-101">4.26</span></span>](#tab/426)

### <a name="windows-mixed-reality"></a><span data-ttu-id="e2b06-102">Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="e2b06-102">Windows Mixed Reality</span></span>

![Progetto di inizio riproduzione connessione per la funzione configura movimenti](../images/unreal-hand-tracking-img-09.png)

<span data-ttu-id="e2b06-104">Quindi, è necessario aggiungere il codice per sottoscrivere gli eventi seguenti:</span><span class="sxs-lookup"><span data-stu-id="e2b06-104">Then you should add code to subscribe to the following events:</span></span>

<span data-ttu-id="e2b06-105">![Progetto dello screenshot dei movimenti di input di input spaziali Windows, tap e Left Manipulation ](../images/unreal/key-events.png)
 ![ delle opzioni dei movimenti di tocco di input spaziali di Windows nel pannello dei dettagli](../images/unreal/key-events2.png)</span><span class="sxs-lookup"><span data-stu-id="e2b06-105">![Blueprint of Windows spatial input hold, tap, and left manipulation gestures](../images/unreal/key-events.png)
![Screenshot of Windows spatial input tap gesture options in the details panel](../images/unreal/key-events2.png)</span></span>

### <a name="openxr"></a><span data-ttu-id="e2b06-106">OpenXR</span><span class="sxs-lookup"><span data-stu-id="e2b06-106">OpenXR</span></span>

<span data-ttu-id="e2b06-107">In OpenXR, gli eventi di movimento vengono rilevati tramite la pipeline di input.</span><span class="sxs-lookup"><span data-stu-id="e2b06-107">In OpenXR, gesture events are tracked through the input pipeline.</span></span> <span data-ttu-id="e2b06-108">Usando l'interazione manuale, il dispositivo può riconoscere automaticamente i movimenti Tap e di attesa, ma non gli altri.</span><span class="sxs-lookup"><span data-stu-id="e2b06-108">Using hand interaction, the device can automatically recognize Tap and Hold gestures, but not the others.</span></span> <span data-ttu-id="e2b06-109">Sono denominati OpenXRMsftHandInteraction Select e i mapping del grip.</span><span class="sxs-lookup"><span data-stu-id="e2b06-109">They are named as OpenXRMsftHandInteraction Select and Grip mappings.</span></span> <span data-ttu-id="e2b06-110">Non è necessario abilitare la sottoscrizione, dichiarare gli eventi in impostazioni/motore/input del progetto, in modo analogo a quanto segue:</span><span class="sxs-lookup"><span data-stu-id="e2b06-110">You don’t need to enable subscription, you should declare the events in Project Settings/Engine/Input, just like this:</span></span>

![Screenshot dei mapping delle azioni OpenXR](../images/unreal-hand-tracking-img-12.png)

# <a name="425"></a>[<span data-ttu-id="e2b06-112">4.25</span><span class="sxs-lookup"><span data-stu-id="e2b06-112">4.25</span></span>](#tab/425)

<span data-ttu-id="e2b06-113">È possibile trovare la funzione Blueprint in **input spaziale di realtà mista di Windows** e la funzione C++ aggiungendo `WindowsMixedRealitySpatialInputFunctionLibrary.h` nel file di codice chiamante.</span><span class="sxs-lookup"><span data-stu-id="e2b06-113">You can find the Blueprint function in under **Windows Mixed Reality Spatial Input**, and the C++ function by adding `WindowsMixedRealitySpatialInputFunctionLibrary.h` in your calling code file.</span></span>

![Acquisisci movimenti](../images/unreal/capture-gestures.png)

### <a name="enum"></a><span data-ttu-id="e2b06-115">Enumerazione</span><span class="sxs-lookup"><span data-stu-id="e2b06-115">Enum</span></span>
<!-- Deprecated
The `ESPatialInputAxisGestureType` enum describes spatial axis gestures and are [fully documented](../../out-of-scope/deprecated/holograms-211.md).
-->
<span data-ttu-id="e2b06-116">Progetto</span><span class="sxs-lookup"><span data-stu-id="e2b06-116">Blueprint:</span></span>

![Tipo di movimento](../images/unreal/gesture-type.png)

<span data-ttu-id="e2b06-118">C++:</span><span class="sxs-lookup"><span data-stu-id="e2b06-118">C++:</span></span>
```cpp
enum class ESpatialInputAxisGestureType : uint8
{
    None = 0,
    Manipulation = 1,
    Navigation = 2,
    NavigationRails = 3
};
```

### <a name="function"></a><span data-ttu-id="e2b06-119">Funzione</span><span class="sxs-lookup"><span data-stu-id="e2b06-119">Function</span></span>
<span data-ttu-id="e2b06-120">È possibile abilitare e disabilitare l'acquisizione di movimenti con la `CaptureGestures` funzione.</span><span class="sxs-lookup"><span data-stu-id="e2b06-120">You can enable and disable gesture capture with the `CaptureGestures` function.</span></span> <span data-ttu-id="e2b06-121">Quando un movimento abilitato genera eventi di input, la funzione restituisce `true` se l'acquisizione del movimento riesce e `false` se si verifica un errore.</span><span class="sxs-lookup"><span data-stu-id="e2b06-121">When an enabled gesture fires input events, the function returns `true` if gesture capture succeeded, and `false` if there's an error.</span></span>

<span data-ttu-id="e2b06-122">Progetto</span><span class="sxs-lookup"><span data-stu-id="e2b06-122">Blueprint:</span></span>

![Movimenti di acquisizione BP](../images/unreal/capture-gestures-bp.png)

<span data-ttu-id="e2b06-124">C++:</span><span class="sxs-lookup"><span data-stu-id="e2b06-124">C++:</span></span>
```cpp
static bool UWindowsMixedRealitySpatialInputFunctionLibrary::CaptureGestures(
    bool Tap = false,
    bool Hold = false,
    ESpatialInputAxisGestureType AxisGesture = ESpatialInputAxisGestureType::None,
    bool NavigationAxisX = true,
    bool NavigationAxisY = true,
    bool NavigationAxisZ = true);
```

<span data-ttu-id="e2b06-125">Di seguito sono riportati gli eventi chiave che è possibile trovare in progetti e C++: ![ eventi chiave](../images/unreal/key-events.png)</span><span class="sxs-lookup"><span data-stu-id="e2b06-125">The following are key events, which you can find in Blueprints and C++: ![Key Events](../images/unreal/key-events.png)</span></span>

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


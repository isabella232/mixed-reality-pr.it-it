---
ms.openlocfilehash: 9fdcbdfe115fa859081c28b768f9c213ac241d13
ms.sourcegitcommit: fbeff51cae92add88d2b960c9b7bbfb04d5a0291
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/10/2020
ms.locfileid: "97002675"
---
# <a name="425"></a>[<span data-ttu-id="8de0e-101">4.25</span><span class="sxs-lookup"><span data-stu-id="8de0e-101">4.25</span></span>](#tab/425)

<span data-ttu-id="8de0e-102">L' `EWMRHandKeypoint` enumerazione descrive la gerarchia ossea della mano.</span><span class="sxs-lookup"><span data-stu-id="8de0e-102">The `EWMRHandKeypoint` enum describes the Hand’s bone hierarchy.</span></span> <span data-ttu-id="8de0e-103">È possibile trovare ogni punto di riferimento della mano elencato nei progetti:</span><span class="sxs-lookup"><span data-stu-id="8de0e-103">You can find each hand keypoint listed in your Blueprints:</span></span>

![BP punto di riferimento della mano](../images/hand-keypoint-bp.png)

<span data-ttu-id="8de0e-105">L'enumerazione C++ completa è elencata di seguito:</span><span class="sxs-lookup"><span data-stu-id="8de0e-105">The full C++ enum is listed below:</span></span>
```cpp
enum class EWMRHandKeypoint : uint8
{
    Palm,
    Wrist,
    ThumbMetacarpal,
    ThumbProximal,
    ThumbDistal,
    ThumbTip,
    IndexMetacarpal,
    IndexProximal,
    IndexIntermediate,
    IndexDistal,
    IndexTip,
    MiddleMetacarpal,
    MiddleProximal,
    MiddleIntermediate,
    MiddleDistal,
    MiddleTip,
    RingMetacarpal,
    RingProximal,
    RingIntermediate,
    RingDistal,
    RingTip,
    LittleMetacarpal,
    LittleProximal,
    LittleIntermediate,
    LittleDistal,
    LittleTip
};
```

<span data-ttu-id="8de0e-106">È possibile trovare i valori numerici per ogni case enum nella tabella [Windows. Perception. people. HandJointKind](https://docs.microsoft.com/uwp/api/windows.perception.people.handjointkind) .</span><span class="sxs-lookup"><span data-stu-id="8de0e-106">You can find the numerical values for each enum case in the [Windows.Perception.People.HandJointKind](https://docs.microsoft.com/uwp/api/windows.perception.people.handjointkind) table.</span></span>

### <a name="supporting-hand-tracking"></a><span data-ttu-id="8de0e-107">Supporto del rilevamento della mano</span><span class="sxs-lookup"><span data-stu-id="8de0e-107">Supporting Hand Tracking</span></span>

<span data-ttu-id="8de0e-108">È possibile usare il rilevamento manuale nei progetti, aggiungendo supporto per il **rilevamento** manuale **> realtà mista di Windows**:</span><span class="sxs-lookup"><span data-stu-id="8de0e-108">You can use hand tracking in Blueprints by adding **Supports Hand Tracking** from **Hand Tracking > Windows Mixed Reality**:</span></span>

![Verifica della mano BP](../images/unreal/hand-tracking-bp.png)

<span data-ttu-id="8de0e-110">Questa funzione restituisce `true` se il rilevamento manuale è supportato nel dispositivo e `false` se il rilevamento manuale non è disponibile.</span><span class="sxs-lookup"><span data-stu-id="8de0e-110">This function returns `true` if hand tracking is supported on the device and `false` if hand tracking isn't available.</span></span>

![Supporta la verifica della mano BP](../images/unreal/supports-hand-tracking-bp.png)

<span data-ttu-id="8de0e-112">C++:</span><span class="sxs-lookup"><span data-stu-id="8de0e-112">C++:</span></span>

<span data-ttu-id="8de0e-113">Includere `WindowsMixedRealityHandTrackingFunctionLibrary.h`.</span><span class="sxs-lookup"><span data-stu-id="8de0e-113">Include `WindowsMixedRealityHandTrackingFunctionLibrary.h`.</span></span>

```cpp
static bool UWindowsMixedRealityHandTrackingFunctionLibrary::SupportsHandTracking()
```

### <a name="getting-hand-tracking"></a><span data-ttu-id="8de0e-114">Recupero del rilevamento della mano</span><span class="sxs-lookup"><span data-stu-id="8de0e-114">Getting Hand Tracking</span></span>

<span data-ttu-id="8de0e-115">È possibile utilizzare **GetHandJointTransform** per restituire i dati spaziali dalla mano.</span><span class="sxs-lookup"><span data-stu-id="8de0e-115">You can use **GetHandJointTransform** to return spatial data from the hand.</span></span> <span data-ttu-id="8de0e-116">I dati vengono aggiornati ogni frame, ma se ci si trova all'interno di un frame i valori restituiti vengono memorizzati nella cache.</span><span class="sxs-lookup"><span data-stu-id="8de0e-116">The data updates every frame, but if you're inside a frame the returned values are cached.</span></span> <span data-ttu-id="8de0e-117">Per motivi di prestazioni, non è consigliabile usare una logica intensa in questa funzione.</span><span class="sxs-lookup"><span data-stu-id="8de0e-117">It's not recommended to have heavy logic in this function for performance reasons.</span></span>

![Ottenere la trasformazione congiunta della mano](../images/unreal/get-hand-joint-transform.png)

<span data-ttu-id="8de0e-119">C++:</span><span class="sxs-lookup"><span data-stu-id="8de0e-119">C++:</span></span>
```cpp
static bool UWindowsMixedRealityHandTrackingFunctionLibrary::GetHandJointTransform(EControllerHand Hand, EWMRHandKeypoint Keypoint, FTransform& OutTransform, float& OutRadius)
```

<span data-ttu-id="8de0e-120">Ecco una suddivisione dei parametri della funzione di GetHandJointTransform:</span><span class="sxs-lookup"><span data-stu-id="8de0e-120">Here's a breakdown of GetHandJointTransform's function parameters:</span></span>

* <span data-ttu-id="8de0e-121">**Hand** : può essere il lato sinistro o destro dell'utente.</span><span class="sxs-lookup"><span data-stu-id="8de0e-121">**Hand** – can be the users left or right hand.</span></span>
* <span data-ttu-id="8de0e-122">**Punto di riferimento** : l'osso della mano.</span><span class="sxs-lookup"><span data-stu-id="8de0e-122">**Keypoint** – the bone of the hand.</span></span>
* <span data-ttu-id="8de0e-123">**Transform** : coordinate e orientamento della base dell'osso.</span><span class="sxs-lookup"><span data-stu-id="8de0e-123">**Transform** – coordinates and orientation of bone’s base.</span></span> <span data-ttu-id="8de0e-124">È possibile richiedere la base dell'osso successivo per ottenere i dati di trasformazione per la fine di un osso.</span><span class="sxs-lookup"><span data-stu-id="8de0e-124">You can request the base of the next bone to get the transform data for the end of a bone.</span></span> <span data-ttu-id="8de0e-125">Un osso Tip speciale fornisce la fine del valore distali.</span><span class="sxs-lookup"><span data-stu-id="8de0e-125">A special Tip bone gives end of distal.</span></span>
* <span data-ttu-id="8de0e-126">\* \* RADIUS: raggio della base dell'osso.</span><span class="sxs-lookup"><span data-stu-id="8de0e-126">\*\*Radius—radius of the base of the bone.</span></span>
* <span data-ttu-id="8de0e-127">\* \* Valore restituito: true se l'osso rileva il frame, false se l'osso non viene rilevato.</span><span class="sxs-lookup"><span data-stu-id="8de0e-127">\*\*Return Value—true if the bone is tracked this frame, false if the bone isn't tracked.</span></span>


# <a name="426"></a>[<span data-ttu-id="8de0e-128">4.26</span><span class="sxs-lookup"><span data-stu-id="8de0e-128">4.26</span></span>](#tab/426)

<span data-ttu-id="8de0e-129">La gerarchia è descritta da `EHandKeypoint` enum:</span><span class="sxs-lookup"><span data-stu-id="8de0e-129">The hierarchy is described by `EHandKeypoint` enum:</span></span>

![Immagine delle opzioni di Bluprint del punto di riferimento della mano](../images/hand-keypoint-bp.png)

<span data-ttu-id="8de0e-131">È possibile ottenere tutti questi dati dalle mani di un utente usando la funzione **Get Motion controller data** .</span><span class="sxs-lookup"><span data-stu-id="8de0e-131">You can get all this data from a user’s hands using the **Get Motion Controller Data** function.</span></span> <span data-ttu-id="8de0e-132">Questa funzione restituisce una struttura **XRMotionControllerData** .</span><span class="sxs-lookup"><span data-stu-id="8de0e-132">That function returns an **XRMotionControllerData** structure.</span></span> <span data-ttu-id="8de0e-133">Di seguito è riportato uno script di progetto di esempio che analizza la struttura XRMotionControllerData per ottenere le posizioni congiunte della mano e disegna un sistema di coordinate di debug in corrispondenza della posizione di ogni joint.</span><span class="sxs-lookup"><span data-stu-id="8de0e-133">Below is a sample Blueprint script that parses the XRMotionControllerData structure to get hand joint locations and draws a debug coordinate system at each joint’s location.</span></span>

![Progetto di Get sguardi data Function connesso a line Trace by Channel Function](../images/unreal-hand-tracking-img-03.png)

<span data-ttu-id="8de0e-135">È importante controllare se la struttura è valida e se è una mano.</span><span class="sxs-lookup"><span data-stu-id="8de0e-135">It's important to check if the structure is valid and that it's a hand.</span></span> <span data-ttu-id="8de0e-136">In caso contrario, è possibile ottenere un comportamento non definito nell'accesso a posizioni, rotazioni e matrici di raggi.</span><span class="sxs-lookup"><span data-stu-id="8de0e-136">Otherwise, you may get undefined behavior in access to positions, rotations, and radii arrays.</span></span>

---
ms.openlocfilehash: 18ccbf3e28eaa2f61157bd9585d633c987e9af48
ms.sourcegitcommit: 13ef9f89ee61fbfe547ecf5fdfdb97560a0de833
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2020
ms.locfileid: "97718217"
---
# <a name="426"></a>[<span data-ttu-id="7e210-101">4.26</span><span class="sxs-lookup"><span data-stu-id="7e210-101">4.26</span></span>](#tab/426)

<span data-ttu-id="7e210-102">Per ottenere i dati per i raggi di mano, è necessario usare la funzione Get Motion controller data della sezione precedente.</span><span class="sxs-lookup"><span data-stu-id="7e210-102">To get the data for the hand rays, you should use the Get Motion Controller Data function from the previous section.</span></span> <span data-ttu-id="7e210-103">La struttura restituita contiene due parametri che è possibile usare per creare un raggio della mano, la **posizione** e la **rotazione degli obiettivi**.</span><span class="sxs-lookup"><span data-stu-id="7e210-103">The returned structure contains two parameters you can use to create a hand ray – **Aim Position** and **Aim Rotation**.</span></span> <span data-ttu-id="7e210-104">Questi parametri formano un raggio diretto dal gomito.</span><span class="sxs-lookup"><span data-stu-id="7e210-104">These parameters form a ray directed by your elbow.</span></span> <span data-ttu-id="7e210-105">È necessario prenderli e trovare un ologramma a cui punta.</span><span class="sxs-lookup"><span data-stu-id="7e210-105">You should take them and find a hologram being pointed by.</span></span>

<span data-ttu-id="7e210-106">Di seguito è riportato un esempio di come determinare se un raggio di mano raggiunge un widget e imposta un risultato di hit personalizzato:</span><span class="sxs-lookup"><span data-stu-id="7e210-106">Below is an example of determining whether a hand ray hits a Widget and setting a custom hit result:</span></span>

![Progetto di Get Motion controller data Function](../images/unreal-hand-tracking-img-04.png) 

# <a name="425"></a>[<span data-ttu-id="7e210-108">4.25</span><span class="sxs-lookup"><span data-stu-id="7e210-108">4.25</span></span>](#tab/425)

<span data-ttu-id="7e210-109">Per utilizzare i raggi mano nei progetti, cercare le azioni in **HMD realtà mista di Windows**:</span><span class="sxs-lookup"><span data-stu-id="7e210-109">To use Hand Rays in Blueprints, search for any of the actions under **Windows Mixed Reality HMD**:</span></span>

![Raggi mano BP](../images/unreal/hand-rays-bp.png)

<span data-ttu-id="7e210-111">Per accedere ad essi in C++, includere nella `WindowsMixedRealityFunctionLibrary.h` parte superiore del file di codice chiamante.</span><span class="sxs-lookup"><span data-stu-id="7e210-111">To access them in C++, include `WindowsMixedRealityFunctionLibrary.h` to the top of your calling code file.</span></span>

### <a name="enum"></a><span data-ttu-id="7e210-112">Enumerazione</span><span class="sxs-lookup"><span data-stu-id="7e210-112">Enum</span></span>

<span data-ttu-id="7e210-113">È anche possibile accedere ai case di input in **EHMDInputControllerButtons**, che possono essere usati nei progetti:</span><span class="sxs-lookup"><span data-stu-id="7e210-113">You also have access to input cases under **EHMDInputControllerButtons**, which can be used in Blueprints:</span></span>

![Pulsanti del controller di input](../images/unreal/input-controller-buttons.png)

<span data-ttu-id="7e210-115">Per l'accesso in C++, usare la `EHMDInputControllerButtons` classe enum:</span><span class="sxs-lookup"><span data-stu-id="7e210-115">For access in C++, use the `EHMDInputControllerButtons` enum class:</span></span>
```cpp
enum class EHMDInputControllerButtons : uint8
{
    Select,
    Grasp,
//......
};
```

<span data-ttu-id="7e210-116">Di seguito è riportata una suddivisione dei due case enum applicabili:</span><span class="sxs-lookup"><span data-stu-id="7e210-116">Below is a breakdown of the two applicable enum cases:</span></span>

* <span data-ttu-id="7e210-117">**Selezionare** l'evento di selezione attivato dall'utente.</span><span class="sxs-lookup"><span data-stu-id="7e210-117">**Select** - User triggered Select event.</span></span>
    * <span data-ttu-id="7e210-118">Attivato in HoloLens 2 da aria-Tap, sguardo e commit, oppure con l' [input vocale](../unreal-voice-input.md) abilitato.</span><span class="sxs-lookup"><span data-stu-id="7e210-118">Triggered in HoloLens 2 by air-tap, gaze, and commit, or by saying “Select” with [voice input](../unreal-voice-input.md) enabled.</span></span>
* <span data-ttu-id="7e210-119">L' **evento di comprensione** attivato dall'utente.</span><span class="sxs-lookup"><span data-stu-id="7e210-119">**Grasp** - User triggered Grasp event.</span></span>
    * <span data-ttu-id="7e210-120">Attivato in HoloLens 2 chiudendo le dita dell'utente su un ologramma.</span><span class="sxs-lookup"><span data-stu-id="7e210-120">Triggered in HoloLens 2 by closing the user’s fingers on a hologram.</span></span>

<span data-ttu-id="7e210-121">È possibile accedere allo stato di rilevamento della mesh mano in C++ tramite l' `EHMDTrackingStatus` enumerazione illustrata di seguito:</span><span class="sxs-lookup"><span data-stu-id="7e210-121">You can access the tracking status of your hand mesh in C++ through the `EHMDTrackingStatus` enum shown below:</span></span>

```cpp
enum class EHMDTrackingStatus : uint8
{
    NotTracked,
    //......
    Tracked
};
```

<span data-ttu-id="7e210-122">Di seguito è riportata una suddivisione dei due case enum applicabili:</span><span class="sxs-lookup"><span data-stu-id="7e210-122">Below is a breakdown of the two applicable enum cases:</span></span>

* <span data-ttu-id="7e210-123">**NotTracked** : la mano non è visibile</span><span class="sxs-lookup"><span data-stu-id="7e210-123">**NotTracked** –- the hand isn’t visible</span></span>
* <span data-ttu-id="7e210-124">**Rilevato** : la mano viene rilevata completamente</span><span class="sxs-lookup"><span data-stu-id="7e210-124">**Tracked** –- the hand is fully tracked</span></span>

### <a name="struct"></a><span data-ttu-id="7e210-125">Struct</span><span class="sxs-lookup"><span data-stu-id="7e210-125">Struct</span></span>

<span data-ttu-id="7e210-126">Lo struct PointerPoseInfo può fornire informazioni sui dati della mano seguenti:</span><span class="sxs-lookup"><span data-stu-id="7e210-126">The PointerPoseInfo struct can give you information on the following hand data:</span></span>

* <span data-ttu-id="7e210-127">**Origin** : origine della mano</span><span class="sxs-lookup"><span data-stu-id="7e210-127">**Origin** – origin of the hand</span></span>
* <span data-ttu-id="7e210-128">**Direzione** : direzione della mano</span><span class="sxs-lookup"><span data-stu-id="7e210-128">**Direction** – direction of the hand</span></span>
* <span data-ttu-id="7e210-129">Vettore **attivo** della mano</span><span class="sxs-lookup"><span data-stu-id="7e210-129">**Up** – up vector of the hand</span></span>
* <span data-ttu-id="7e210-130">**Orientamento** -quaternione orientamento</span><span class="sxs-lookup"><span data-stu-id="7e210-130">**Orientation** – orientation quaternion</span></span>
* <span data-ttu-id="7e210-131">**Stato di rilevamento** -stato di rilevamento corrente</span><span class="sxs-lookup"><span data-stu-id="7e210-131">**Tracking Status** – current tracking status</span></span>

<span data-ttu-id="7e210-132">È possibile accedere allo struct PointerPoseInfo tramite i progetti, come illustrato di seguito:</span><span class="sxs-lookup"><span data-stu-id="7e210-132">You can access the PointerPoseInfo struct through Blueprints, as shown below:</span></span>

![Indicatore di posa indicatore BP](../images/unreal/pointer-pose-info-bp.png)

<span data-ttu-id="7e210-134">O con C++:</span><span class="sxs-lookup"><span data-stu-id="7e210-134">Or with C++:</span></span>

```cpp
struct FPointerPoseInfo
{
    FVector Origin;
    FVector Direction;
    FVector Up;
    FQuat Orientation;
    EHMDTrackingStatus TrackingStatus;
};
```

### <a name="functions"></a><span data-ttu-id="7e210-135">Funzioni</span><span class="sxs-lookup"><span data-stu-id="7e210-135">Functions</span></span>

<span data-ttu-id="7e210-136">Tutte le funzioni elencate di seguito possono essere chiamate in ogni frame, che consente il monitoraggio continuo.</span><span class="sxs-lookup"><span data-stu-id="7e210-136">All of the functions listed below can be called on every frame, which allows continuous monitoring.</span></span>

1. <span data-ttu-id="7e210-137">**Get Pointer post info** restituisce informazioni complete sulla direzione del raggio di mano nel frame corrente.</span><span class="sxs-lookup"><span data-stu-id="7e210-137">**Get Pointer Pose Info** returns complete information about the hand ray direction in the current frame.</span></span>

<span data-ttu-id="7e210-138">Progetto</span><span class="sxs-lookup"><span data-stu-id="7e210-138">Blueprint:</span></span>

![Ottenere le informazioni sulla posa del puntatore](../images/unreal/get-pointer-pose-info.png)

<span data-ttu-id="7e210-140">C++:</span><span class="sxs-lookup"><span data-stu-id="7e210-140">C++:</span></span>
```cpp
static FPointerPoseInfo UWindowsMixedRealityFunctionLibrary::GetPointerPoseInfo(EControllerHand hand);
```

2. <span data-ttu-id="7e210-141">**Viene** restituito true se la mano viene afferrata nel frame corrente.</span><span class="sxs-lookup"><span data-stu-id="7e210-141">**Is Grasped** returns true if the hand is grasped in the current frame.</span></span>

<span data-ttu-id="7e210-142">Progetto</span><span class="sxs-lookup"><span data-stu-id="7e210-142">Blueprint:</span></span>

![Viene afferrato BP](../images/unreal/is-grasped-bp.png)

<span data-ttu-id="7e210-144">C++:</span><span class="sxs-lookup"><span data-stu-id="7e210-144">C++:</span></span>
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsGrasped(EControllerHand hand);
```

3. <span data-ttu-id="7e210-145">**Is Select Pressed** restituisce true se l'utente ha attivato SELECT nel frame corrente.</span><span class="sxs-lookup"><span data-stu-id="7e210-145">**Is Select Pressed** returns true if the user triggered Select in the current frame.</span></span>

<span data-ttu-id="7e210-146">Progetto</span><span class="sxs-lookup"><span data-stu-id="7e210-146">Blueprint:</span></span>

![Seleziona BP premuto](../images/unreal/is-select-pressed-bp.png)

<span data-ttu-id="7e210-148">C++:</span><span class="sxs-lookup"><span data-stu-id="7e210-148">C++:</span></span>
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsSelectPressed(EControllerHand hand);
```

4. <span data-ttu-id="7e210-149">Il **pulsante è selezionato** restituisce true se l'evento o il pulsante viene attivato nel frame corrente.</span><span class="sxs-lookup"><span data-stu-id="7e210-149">**Is Button Clicked** returns true if the event or button is triggered in the current frame.</span></span>

<span data-ttu-id="7e210-150">Progetto</span><span class="sxs-lookup"><span data-stu-id="7e210-150">Blueprint:</span></span>

![Pulsante è selezionato BP](../images/unreal/is-button-clicked-bp.png)

<span data-ttu-id="7e210-152">C++:</span><span class="sxs-lookup"><span data-stu-id="7e210-152">C++:</span></span>
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsButtonClicked(EControllerHand hand, EHMDInputControllerButtons button);
```

5. <span data-ttu-id="7e210-153">**Ottenere** lo stato di rilevamento del controller restituisce lo stato di rilevamento nel frame corrente.</span><span class="sxs-lookup"><span data-stu-id="7e210-153">**Get Controller Tracking Status** returns the tracking status in the current frame.</span></span>

<span data-ttu-id="7e210-154">Progetto</span><span class="sxs-lookup"><span data-stu-id="7e210-154">Blueprint:</span></span>

![Ottenere lo stato di rilevamento del controller BP](../images/unreal/get-controller-tracking-status-bp.png)

<span data-ttu-id="7e210-156">C++:</span><span class="sxs-lookup"><span data-stu-id="7e210-156">C++:</span></span>
```cpp
static EHMDTrackingStatus UWindowsMixedRealityFunctionLibrary::GetControllerTrackingStatus(EControllerHand hand);
```
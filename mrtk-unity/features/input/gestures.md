---
title: Movimenti
description: Docummentation sui movimenti e sui relativi eventi in MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, movimenti,
ms.openlocfilehash: a26c7b9f51db2162daf2176e6d2125ffb6061c27
ms.sourcegitcommit: ac315c1d35f2b9c431e79bc3f1212215301bb867
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105550931"
---
# <a name="gestures"></a><span data-ttu-id="39ce9-104">Movimenti</span><span class="sxs-lookup"><span data-stu-id="39ce9-104">Gestures</span></span>

<span data-ttu-id="39ce9-105">I movimenti sono eventi di input basati su mani umane.</span><span class="sxs-lookup"><span data-stu-id="39ce9-105">Gestures are input events based on human hands.</span></span> <span data-ttu-id="39ce9-106">Esistono due tipi di dispositivi che generano eventi di input di movimento in MRTK:</span><span class="sxs-lookup"><span data-stu-id="39ce9-106">There are two types of devices that raise gesture input events in MRTK:</span></span>

- <span data-ttu-id="39ce9-107">Dispositivi di realtà mista di Windows, ad esempio HoloLens.</span><span class="sxs-lookup"><span data-stu-id="39ce9-107">Windows Mixed Reality devices such as HoloLens.</span></span> <span data-ttu-id="39ce9-108">Questo descrive i movimenti di pizzicotto ("rubinetto aereo") e i movimenti di tocco e mantenimento.</span><span class="sxs-lookup"><span data-stu-id="39ce9-108">This describes pinching motions ("Air Tap") and tap-and-hold gestures.</span></span>

  <span data-ttu-id="39ce9-109">Per ulteriori informazioni sui movimenti HoloLens, vedere la [documentazione sui movimenti di realtà mista di Windows](/windows/mixed-reality/gestures).</span><span class="sxs-lookup"><span data-stu-id="39ce9-109">For more information on HoloLens gestures see the [Windows Mixed Reality Gestures documentation](/windows/mixed-reality/gestures).</span></span>

  <span data-ttu-id="39ce9-110">[`WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityDeviceManager) esegue il wrapping di [Unity XR. WSA. Input. GestureRecognizer](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.GestureRecognizer.html) per utilizzare gli eventi di movimento di Unity dai dispositivi HoloLens.</span><span class="sxs-lookup"><span data-stu-id="39ce9-110">[`WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityDeviceManager) wraps the [Unity XR.WSA.Input.GestureRecognizer](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.GestureRecognizer.html) to consume Unity's gesture events from HoloLens devices.</span></span>

- <span data-ttu-id="39ce9-111">Dispositivi touchscreen.</span><span class="sxs-lookup"><span data-stu-id="39ce9-111">Touch screen devices.</span></span>

  <span data-ttu-id="39ce9-112">[`UnityTouchController`](xref:Microsoft.MixedReality.Toolkit.Input.UnityInput) esegue il wrapping della [classe Touch di Unity](https://docs.unity3d.com/ScriptReference/Touch.html) che supporta le schermate touch fisiche.</span><span class="sxs-lookup"><span data-stu-id="39ce9-112">[`UnityTouchController`](xref:Microsoft.MixedReality.Toolkit.Input.UnityInput) wraps the [Unity Touch class](https://docs.unity3d.com/ScriptReference/Touch.html) that supports physical touch screens.</span></span>

<span data-ttu-id="39ce9-113">Entrambe queste origini di input usano il profilo _Impostazioni movimenti_ per convertire rispettivamente gli eventi di tocco e movimento di Unity nelle [azioni di input](input-actions.md)di MRTK.</span><span class="sxs-lookup"><span data-stu-id="39ce9-113">Both of these input sources use the _Gesture Settings_ profile to translate Unity's Touch and Gesture events respectively into MRTK's [Input Actions](input-actions.md).</span></span> <span data-ttu-id="39ce9-114">Questo profilo si trova nel profilo _Impostazioni sistema di input_ .</span><span class="sxs-lookup"><span data-stu-id="39ce9-114">This profile can be found under the _Input System Settings_ profile.</span></span>

<img src="../images/input/GestureProfile.png" alt="Gesture Profile" style="max-width:100%;">

## <a name="gesture-events"></a><span data-ttu-id="39ce9-115">Eventi per i movimenti</span><span class="sxs-lookup"><span data-stu-id="39ce9-115">Gesture events</span></span>

<span data-ttu-id="39ce9-116">Gli eventi di movimento vengono ricevuti implementando una delle interfacce del gestore movimenti: [`IMixedRealityGestureHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGestureHandler) o [`IMixedRealityGestureHandler<TYPE>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGestureHandler`1) (vedere la tabella dei [gestori eventi](input-events.md)).</span><span class="sxs-lookup"><span data-stu-id="39ce9-116">Gesture events are received by implementing one of the gesture handler interfaces: [`IMixedRealityGestureHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGestureHandler) or [`IMixedRealityGestureHandler<TYPE>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGestureHandler`1) (see table of [event handlers](input-events.md)).</span></span>

<span data-ttu-id="39ce9-117">Vedere la [scena di esempio](#example-scene) per un'implementazione di esempio di un gestore eventi di movimento.</span><span class="sxs-lookup"><span data-stu-id="39ce9-117">See [Example Scene](#example-scene) for an example implementation of a gesture event handler.</span></span>

<span data-ttu-id="39ce9-118">Quando si implementa la versione generica, gli eventi *OnGestureCompleted* e *OnGestureUpdated* possono ricevere dati tipizzati dei tipi seguenti:</span><span class="sxs-lookup"><span data-stu-id="39ce9-118">When implementing the generic version, the *OnGestureCompleted* and *OnGestureUpdated* events can receive typed data of the following types:</span></span>

- <span data-ttu-id="39ce9-119">`Vector2` -movimento di posizione 2D.</span><span class="sxs-lookup"><span data-stu-id="39ce9-119">`Vector2` - 2D position gesture.</span></span> <span data-ttu-id="39ce9-120">Prodotto da touch screen per informarli [`deltaPosition`](https://docs.unity3d.com/ScriptReference/Touch-deltaPosition.html) .</span><span class="sxs-lookup"><span data-stu-id="39ce9-120">Produced by touch screens to inform of their [`deltaPosition`](https://docs.unity3d.com/ScriptReference/Touch-deltaPosition.html).</span></span>
- <span data-ttu-id="39ce9-121">`Vector3` -movimento di posizione 3D.</span><span class="sxs-lookup"><span data-stu-id="39ce9-121">`Vector3` - 3D position gesture.</span></span> <span data-ttu-id="39ce9-122">Prodotto da HoloLens per informare:</span><span class="sxs-lookup"><span data-stu-id="39ce9-122">Produced by HoloLens to inform of:</span></span>
  - <span data-ttu-id="39ce9-123">[`cumulativeDelta`](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.ManipulationUpdatedEventArgs-cumulativeDelta.html) di un evento di manipolazione</span><span class="sxs-lookup"><span data-stu-id="39ce9-123">[`cumulativeDelta`](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.ManipulationUpdatedEventArgs-cumulativeDelta.html) of a manipulation event</span></span>
  - <span data-ttu-id="39ce9-124">[`normalizedOffset`](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.NavigationUpdatedEventArgs-normalizedOffset.html) di un evento di navigazione</span><span class="sxs-lookup"><span data-stu-id="39ce9-124">[`normalizedOffset`](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.NavigationUpdatedEventArgs-normalizedOffset.html) of a navigation event</span></span>
- <span data-ttu-id="39ce9-125">`Quaternion` -movimento di rotazione 3D.</span><span class="sxs-lookup"><span data-stu-id="39ce9-125">`Quaternion` - 3D rotation gesture.</span></span> <span data-ttu-id="39ce9-126">Disponibile per le origini di input personalizzate ma non per quelle esistenti.</span><span class="sxs-lookup"><span data-stu-id="39ce9-126">Available to custom input sources but not currently produced by any of the existing ones.</span></span>
- <span data-ttu-id="39ce9-127">`MixedRealityPose` -Movimento di posizione/rotazione 3D combinato.</span><span class="sxs-lookup"><span data-stu-id="39ce9-127">`MixedRealityPose` - Combined 3D position/rotation gesture.</span></span> <span data-ttu-id="39ce9-128">Disponibile per le origini di input personalizzate ma non per quelle esistenti.</span><span class="sxs-lookup"><span data-stu-id="39ce9-128">Available to custom input sources but not currently produced by any of the existing ones.</span></span>

## <a name="order-of-events"></a><span data-ttu-id="39ce9-129">Ordine degli eventi</span><span class="sxs-lookup"><span data-stu-id="39ce9-129">Order of events</span></span>

<span data-ttu-id="39ce9-130">Esistono due catene principali di eventi, a seconda dell'input dell'utente:</span><span class="sxs-lookup"><span data-stu-id="39ce9-130">There are two principal chains of events, depending on user input:</span></span>

- <span data-ttu-id="39ce9-131">"Mantieni":</span><span class="sxs-lookup"><span data-stu-id="39ce9-131">"Hold":</span></span>
    1. <span data-ttu-id="39ce9-132">Tieni premuto il tocco:</span><span class="sxs-lookup"><span data-stu-id="39ce9-132">Hold tap:</span></span>
        - <span data-ttu-id="39ce9-133">Avvia _manipolazione_</span><span class="sxs-lookup"><span data-stu-id="39ce9-133">start _Manipulation_</span></span>
    1. <span data-ttu-id="39ce9-134">Mantieni il tocco oltre [HoldStartDuration](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityInputSimulationProfile.HoldStartDuration):</span><span class="sxs-lookup"><span data-stu-id="39ce9-134">Hold tap beyond [HoldStartDuration](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityInputSimulationProfile.HoldStartDuration):</span></span>
        - <span data-ttu-id="39ce9-135">inizio _attesa_</span><span class="sxs-lookup"><span data-stu-id="39ce9-135">start _Hold_</span></span>
    1. <span data-ttu-id="39ce9-136">Toccare versione:</span><span class="sxs-lookup"><span data-stu-id="39ce9-136">Release tap:</span></span>
        - <span data-ttu-id="39ce9-137">completa _attesa_</span><span class="sxs-lookup"><span data-stu-id="39ce9-137">complete _Hold_</span></span>
        - <span data-ttu-id="39ce9-138">_manipolazione_ completa</span><span class="sxs-lookup"><span data-stu-id="39ce9-138">complete _Manipulation_</span></span>

- <span data-ttu-id="39ce9-139">"Sposta":</span><span class="sxs-lookup"><span data-stu-id="39ce9-139">"Move":</span></span>
    1. <span data-ttu-id="39ce9-140">Tieni premuto il tocco:</span><span class="sxs-lookup"><span data-stu-id="39ce9-140">Hold tap:</span></span>
        - <span data-ttu-id="39ce9-141">Avvia _manipolazione_</span><span class="sxs-lookup"><span data-stu-id="39ce9-141">start _Manipulation_</span></span>
    1. <span data-ttu-id="39ce9-142">Mantieni il tocco oltre [HoldStartDuration](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityInputSimulationProfile.HoldStartDuration):</span><span class="sxs-lookup"><span data-stu-id="39ce9-142">Hold tap beyond [HoldStartDuration](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityInputSimulationProfile.HoldStartDuration):</span></span>
        - <span data-ttu-id="39ce9-143">inizio _attesa_</span><span class="sxs-lookup"><span data-stu-id="39ce9-143">start _Hold_</span></span>
    1. <span data-ttu-id="39ce9-144">Spostare la mano oltre [NavigationStartThreshold](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityInputSimulationProfile.NavigationStartThreshold):</span><span class="sxs-lookup"><span data-stu-id="39ce9-144">Move hand beyond [NavigationStartThreshold](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityInputSimulationProfile.NavigationStartThreshold):</span></span>
        - <span data-ttu-id="39ce9-145">Annulla _attesa_</span><span class="sxs-lookup"><span data-stu-id="39ce9-145">cancel _Hold_</span></span>
        - <span data-ttu-id="39ce9-146">Avvia _spostamento_</span><span class="sxs-lookup"><span data-stu-id="39ce9-146">start _Navigation_</span></span>
    1. <span data-ttu-id="39ce9-147">Toccare versione:</span><span class="sxs-lookup"><span data-stu-id="39ce9-147">Release tap:</span></span>
        - <span data-ttu-id="39ce9-148">_manipolazione_ completa</span><span class="sxs-lookup"><span data-stu-id="39ce9-148">complete _Manipulation_</span></span>
        - <span data-ttu-id="39ce9-149">_navigazione_ completa</span><span class="sxs-lookup"><span data-stu-id="39ce9-149">complete _Navigation_</span></span>

## <a name="example-scene"></a><span data-ttu-id="39ce9-150">Scena di esempio</span><span class="sxs-lookup"><span data-stu-id="39ce9-150">Example scene</span></span>

<span data-ttu-id="39ce9-151">La scena **HandInteractionGestureEventsExample** (assets/MRTK/examples/Demos/HandTracking/scenes) Mostra come usare il risultato del puntatore per generare un oggetto nella posizione di hit.</span><span class="sxs-lookup"><span data-stu-id="39ce9-151">The **HandInteractionGestureEventsExample** (Assets/MRTK/Examples/Demos/HandTracking/Scenes) scene shows how to use the pointer Result to spawn an object at the hit location.</span></span>

<span data-ttu-id="39ce9-152">Lo `GestureTester` script (assets/MRTK/examples/Demos/HandTracking/script) è un'implementazione di esempio per visualizzare gli eventi di movimento tramite GameObject.</span><span class="sxs-lookup"><span data-stu-id="39ce9-152">The `GestureTester` (Assets/MRTK/Examples/Demos/HandTracking/Script) script is an example implementation to visualize gesture events via GameObjects.</span></span> <span data-ttu-id="39ce9-153">Le funzioni del gestore modificano il colore degli oggetti indicatore e visualizzano l'ultimo evento registrato negli oggetti testo della scena.</span><span class="sxs-lookup"><span data-stu-id="39ce9-153">The handler functions change the color of indicator objects and display the last recorded event in text objects in the scene.</span></span>
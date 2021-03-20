---
title: Movimenti
description: Docummentation sui movimenti e sui relativi eventi in MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, movimenti,
ms.openlocfilehash: 8a91b2b79410809cde15cf3016d6d18f0ca95b57
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2021
ms.locfileid: "104684704"
---
# <a name="gestures"></a><span data-ttu-id="d9031-104">Movimenti</span><span class="sxs-lookup"><span data-stu-id="d9031-104">Gestures</span></span>

<span data-ttu-id="d9031-105">I movimenti sono eventi di input basati su mani umane.</span><span class="sxs-lookup"><span data-stu-id="d9031-105">Gestures are input events based on human hands.</span></span> <span data-ttu-id="d9031-106">Esistono due tipi di dispositivi che generano eventi di input di movimento in MRTK:</span><span class="sxs-lookup"><span data-stu-id="d9031-106">There are two types of devices that raise gesture input events in MRTK:</span></span>

- <span data-ttu-id="d9031-107">Dispositivi di realtà mista di Windows, ad esempio HoloLens.</span><span class="sxs-lookup"><span data-stu-id="d9031-107">Windows Mixed Reality devices such as HoloLens.</span></span> <span data-ttu-id="d9031-108">Questo descrive i movimenti di pizzicotto ("rubinetto aereo") e i movimenti di tocco e mantenimento.</span><span class="sxs-lookup"><span data-stu-id="d9031-108">This describes pinching motions ("Air Tap") and tap-and-hold gestures.</span></span>

  <span data-ttu-id="d9031-109">Per ulteriori informazioni sui movimenti HoloLens, vedere la [documentazione sui movimenti di realtà mista di Windows](https://docs.microsoft.com/windows/mixed-reality/gestures).</span><span class="sxs-lookup"><span data-stu-id="d9031-109">For more information on HoloLens gestures see the [Windows Mixed Reality Gestures documentation](https://docs.microsoft.com/windows/mixed-reality/gestures).</span></span>

  <span data-ttu-id="d9031-110">[`WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityDeviceManager) esegue il wrapping di [Unity XR. WSA. Input. GestureRecognizer](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.GestureRecognizer.html) per utilizzare gli eventi di movimento di Unity dai dispositivi HoloLens.</span><span class="sxs-lookup"><span data-stu-id="d9031-110">[`WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityDeviceManager) wraps the [Unity XR.WSA.Input.GestureRecognizer](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.GestureRecognizer.html) to consume Unity's gesture events from HoloLens devices.</span></span>

- <span data-ttu-id="d9031-111">Dispositivi touchscreen.</span><span class="sxs-lookup"><span data-stu-id="d9031-111">Touch screen devices.</span></span>

  <span data-ttu-id="d9031-112">[`UnityTouchController`](xref:Microsoft.MixedReality.Toolkit.Input.UnityInput) esegue il wrapping della [classe Touch di Unity](https://docs.unity3d.com/ScriptReference/Touch.html) che supporta le schermate touch fisiche.</span><span class="sxs-lookup"><span data-stu-id="d9031-112">[`UnityTouchController`](xref:Microsoft.MixedReality.Toolkit.Input.UnityInput) wraps the [Unity Touch class](https://docs.unity3d.com/ScriptReference/Touch.html) that supports physical touch screens.</span></span>

<span data-ttu-id="d9031-113">Entrambe queste origini di input usano il profilo _Impostazioni movimenti_ per convertire rispettivamente gli eventi di tocco e movimento di Unity nelle [azioni di input](input-actions.md)di MRTK.</span><span class="sxs-lookup"><span data-stu-id="d9031-113">Both of these input sources use the _Gesture Settings_ profile to translate Unity's Touch and Gesture events respectively into MRTK's [Input Actions](input-actions.md).</span></span> <span data-ttu-id="d9031-114">Questo profilo si trova nel profilo _Impostazioni sistema di input_ .</span><span class="sxs-lookup"><span data-stu-id="d9031-114">This profile can be found under the _Input System Settings_ profile.</span></span>

<img src="../images/input/GestureProfile.png" alt="Gesture Profile" style="max-width:100%;">

## <a name="gesture-events"></a><span data-ttu-id="d9031-115">Eventi per i movimenti</span><span class="sxs-lookup"><span data-stu-id="d9031-115">Gesture events</span></span>

<span data-ttu-id="d9031-116">Gli eventi di movimento vengono ricevuti implementando una delle interfacce del gestore movimenti: [`IMixedRealityGestureHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGestureHandler) o [`IMixedRealityGestureHandler<TYPE>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGestureHandler`1) (vedere la tabella dei [gestori eventi](input-events.md)).</span><span class="sxs-lookup"><span data-stu-id="d9031-116">Gesture events are received by implementing one of the gesture handler interfaces: [`IMixedRealityGestureHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGestureHandler) or [`IMixedRealityGestureHandler<TYPE>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGestureHandler`1) (see table of [event handlers](input-events.md)).</span></span>

<span data-ttu-id="d9031-117">Vedere la [scena di esempio](#example-scene) per un'implementazione di esempio di un gestore eventi di movimento.</span><span class="sxs-lookup"><span data-stu-id="d9031-117">See [Example Scene](#example-scene) for an example implementation of a gesture event handler.</span></span>

<span data-ttu-id="d9031-118">Quando si implementa la versione generica, gli eventi *OnGestureCompleted* e *OnGestureUpdated* possono ricevere dati tipizzati dei tipi seguenti:</span><span class="sxs-lookup"><span data-stu-id="d9031-118">When implementing the generic version, the *OnGestureCompleted* and *OnGestureUpdated* events can receive typed data of the following types:</span></span>

- <span data-ttu-id="d9031-119">`Vector2` -movimento di posizione 2D.</span><span class="sxs-lookup"><span data-stu-id="d9031-119">`Vector2` - 2D position gesture.</span></span> <span data-ttu-id="d9031-120">Prodotto da touch screen per informarli [`deltaPosition`](https://docs.unity3d.com/ScriptReference/Touch-deltaPosition.html) .</span><span class="sxs-lookup"><span data-stu-id="d9031-120">Produced by touch screens to inform of their [`deltaPosition`](https://docs.unity3d.com/ScriptReference/Touch-deltaPosition.html).</span></span>
- <span data-ttu-id="d9031-121">`Vector3` -movimento di posizione 3D.</span><span class="sxs-lookup"><span data-stu-id="d9031-121">`Vector3` - 3D position gesture.</span></span> <span data-ttu-id="d9031-122">Prodotto da HoloLens per informare:</span><span class="sxs-lookup"><span data-stu-id="d9031-122">Produced by HoloLens to inform of:</span></span>
  - <span data-ttu-id="d9031-123">[`cumulativeDelta`](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.ManipulationUpdatedEventArgs-cumulativeDelta.html) di un evento di manipolazione</span><span class="sxs-lookup"><span data-stu-id="d9031-123">[`cumulativeDelta`](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.ManipulationUpdatedEventArgs-cumulativeDelta.html) of a manipulation event</span></span>
  - <span data-ttu-id="d9031-124">[`normalizedOffset`](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.NavigationUpdatedEventArgs-normalizedOffset.html) di un evento di navigazione</span><span class="sxs-lookup"><span data-stu-id="d9031-124">[`normalizedOffset`](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.NavigationUpdatedEventArgs-normalizedOffset.html) of a navigation event</span></span>
- <span data-ttu-id="d9031-125">`Quaternion` -movimento di rotazione 3D.</span><span class="sxs-lookup"><span data-stu-id="d9031-125">`Quaternion` - 3D rotation gesture.</span></span> <span data-ttu-id="d9031-126">Disponibile per le origini di input personalizzate ma non per quelle esistenti.</span><span class="sxs-lookup"><span data-stu-id="d9031-126">Available to custom input sources but not currently produced by any of the existing ones.</span></span>
- <span data-ttu-id="d9031-127">`MixedRealityPose` -Movimento di posizione/rotazione 3D combinato.</span><span class="sxs-lookup"><span data-stu-id="d9031-127">`MixedRealityPose` - Combined 3D position/rotation gesture.</span></span> <span data-ttu-id="d9031-128">Disponibile per le origini di input personalizzate ma non per quelle esistenti.</span><span class="sxs-lookup"><span data-stu-id="d9031-128">Available to custom input sources but not currently produced by any of the existing ones.</span></span>

## <a name="order-of-events"></a><span data-ttu-id="d9031-129">Ordine degli eventi</span><span class="sxs-lookup"><span data-stu-id="d9031-129">Order of events</span></span>

<span data-ttu-id="d9031-130">Esistono due catene principali di eventi, a seconda dell'input dell'utente:</span><span class="sxs-lookup"><span data-stu-id="d9031-130">There are two principal chains of events, depending on user input:</span></span>

- <span data-ttu-id="d9031-131">"Mantieni":</span><span class="sxs-lookup"><span data-stu-id="d9031-131">"Hold":</span></span>
    1. <span data-ttu-id="d9031-132">Tieni premuto il tocco:</span><span class="sxs-lookup"><span data-stu-id="d9031-132">Hold tap:</span></span>
        - <span data-ttu-id="d9031-133">Avvia _manipolazione_</span><span class="sxs-lookup"><span data-stu-id="d9031-133">start _Manipulation_</span></span>
    1. <span data-ttu-id="d9031-134">Mantieni il tocco oltre [HoldStartDuration](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityInputSimulationProfile.HoldStartDuration):</span><span class="sxs-lookup"><span data-stu-id="d9031-134">Hold tap beyond [HoldStartDuration](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityInputSimulationProfile.HoldStartDuration):</span></span>
        - <span data-ttu-id="d9031-135">inizio _attesa_</span><span class="sxs-lookup"><span data-stu-id="d9031-135">start _Hold_</span></span>
    1. <span data-ttu-id="d9031-136">Toccare versione:</span><span class="sxs-lookup"><span data-stu-id="d9031-136">Release tap:</span></span>
        - <span data-ttu-id="d9031-137">completa _attesa_</span><span class="sxs-lookup"><span data-stu-id="d9031-137">complete _Hold_</span></span>
        - <span data-ttu-id="d9031-138">_manipolazione_ completa</span><span class="sxs-lookup"><span data-stu-id="d9031-138">complete _Manipulation_</span></span>

- <span data-ttu-id="d9031-139">"Sposta":</span><span class="sxs-lookup"><span data-stu-id="d9031-139">"Move":</span></span>
    1. <span data-ttu-id="d9031-140">Tieni premuto il tocco:</span><span class="sxs-lookup"><span data-stu-id="d9031-140">Hold tap:</span></span>
        - <span data-ttu-id="d9031-141">Avvia _manipolazione_</span><span class="sxs-lookup"><span data-stu-id="d9031-141">start _Manipulation_</span></span>
    1. <span data-ttu-id="d9031-142">Mantieni il tocco oltre [HoldStartDuration](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityInputSimulationProfile.HoldStartDuration):</span><span class="sxs-lookup"><span data-stu-id="d9031-142">Hold tap beyond [HoldStartDuration](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityInputSimulationProfile.HoldStartDuration):</span></span>
        - <span data-ttu-id="d9031-143">inizio _attesa_</span><span class="sxs-lookup"><span data-stu-id="d9031-143">start _Hold_</span></span>
    1. <span data-ttu-id="d9031-144">Spostare la mano oltre [NavigationStartThreshold](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityInputSimulationProfile.NavigationStartThreshold):</span><span class="sxs-lookup"><span data-stu-id="d9031-144">Move hand beyond [NavigationStartThreshold](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityInputSimulationProfile.NavigationStartThreshold):</span></span>
        - <span data-ttu-id="d9031-145">Annulla _attesa_</span><span class="sxs-lookup"><span data-stu-id="d9031-145">cancel _Hold_</span></span>
        - <span data-ttu-id="d9031-146">Avvia _spostamento_</span><span class="sxs-lookup"><span data-stu-id="d9031-146">start _Navigation_</span></span>
    1. <span data-ttu-id="d9031-147">Toccare versione:</span><span class="sxs-lookup"><span data-stu-id="d9031-147">Release tap:</span></span>
        - <span data-ttu-id="d9031-148">_manipolazione_ completa</span><span class="sxs-lookup"><span data-stu-id="d9031-148">complete _Manipulation_</span></span>
        - <span data-ttu-id="d9031-149">_navigazione_ completa</span><span class="sxs-lookup"><span data-stu-id="d9031-149">complete _Navigation_</span></span>

## <a name="example-scene"></a><span data-ttu-id="d9031-150">Scena di esempio</span><span class="sxs-lookup"><span data-stu-id="d9031-150">Example scene</span></span>

<span data-ttu-id="d9031-151">La scena **HandInteractionGestureEventsExample** (assets/MRTK/examples/Demos/HandTracking/scenes) Mostra come usare il risultato del puntatore per generare un oggetto nella posizione di hit.</span><span class="sxs-lookup"><span data-stu-id="d9031-151">The **HandInteractionGestureEventsExample** (Assets/MRTK/Examples/Demos/HandTracking/Scenes) scene shows how to use the pointer Result to spawn an object at the hit location.</span></span>

<span data-ttu-id="d9031-152">Lo `GestureTester` script (assets/MRTK/examples/Demos/HandTracking/script) è un'implementazione di esempio per visualizzare gli eventi di movimento tramite GameObject.</span><span class="sxs-lookup"><span data-stu-id="d9031-152">The `GestureTester` (Assets/MRTK/Examples/Demos/HandTracking/Script) script is an example implementation to visualize gesture events via GameObjects.</span></span> <span data-ttu-id="d9031-153">Le funzioni del gestore modificano il colore degli oggetti indicatore e visualizzano l'ultimo evento registrato negli oggetti testo della scena.</span><span class="sxs-lookup"><span data-stu-id="d9031-153">The handler functions change the color of indicator objects and display the last recorded event in text objects in the scene.</span></span>

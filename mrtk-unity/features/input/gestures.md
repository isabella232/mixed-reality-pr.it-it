---
title: Movimenti
description: Documentazione sui movimenti e i relativi eventi in MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, movimenti,
ms.openlocfilehash: 7bbc97ab5e23a69356d523c463aa37c013d70337
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176887"
---
# <a name="gestures"></a><span data-ttu-id="9a464-104">Movimenti</span><span class="sxs-lookup"><span data-stu-id="9a464-104">Gestures</span></span>

<span data-ttu-id="9a464-105">I movimenti sono eventi di input basati sulle mani umane.</span><span class="sxs-lookup"><span data-stu-id="9a464-105">Gestures are input events based on human hands.</span></span> <span data-ttu-id="9a464-106">Esistono due tipi di dispositivi che generano eventi di input movimenti in MRTK:</span><span class="sxs-lookup"><span data-stu-id="9a464-106">There are two types of devices that raise gesture input events in MRTK:</span></span>

- <span data-ttu-id="9a464-107">Windows Mixed Reality dispositivi, ad esempio HoloLens.</span><span class="sxs-lookup"><span data-stu-id="9a464-107">Windows Mixed Reality devices such as HoloLens.</span></span> <span data-ttu-id="9a464-108">Questo articolo descrive i movimenti di avvicinamento delle dita ("Tocco d'aria") e i movimenti di tocco e tenere premuto.</span><span class="sxs-lookup"><span data-stu-id="9a464-108">This describes pinching motions ("Air Tap") and tap-and-hold gestures.</span></span>

  <span data-ttu-id="9a464-109">Per altre informazioni sui movimenti HoloLens, vedere la [documentazione Windows Mixed Reality movimenti.](/windows/mixed-reality/gestures)</span><span class="sxs-lookup"><span data-stu-id="9a464-109">For more information on HoloLens gestures see the [Windows Mixed Reality Gestures documentation](/windows/mixed-reality/gestures).</span></span>

  <span data-ttu-id="9a464-110">[`WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityDeviceManager)esegue il wrapping [di Unity XR. Wsa. Input.GestureRecognizer](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.GestureRecognizer.html) per utilizzare gli eventi di movimento di Unity HoloLens dispositivi.</span><span class="sxs-lookup"><span data-stu-id="9a464-110">[`WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityDeviceManager) wraps the [Unity XR.WSA.Input.GestureRecognizer](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.GestureRecognizer.html) to consume Unity's gesture events from HoloLens devices.</span></span>

- <span data-ttu-id="9a464-111">Dispositivi touch screen.</span><span class="sxs-lookup"><span data-stu-id="9a464-111">Touch screen devices.</span></span>

  <span data-ttu-id="9a464-112">[`UnityTouchController`](xref:Microsoft.MixedReality.Toolkit.Input.UnityInput) esegue il wrapping [della classe Touch di Unity](https://docs.unity3d.com/ScriptReference/Touch.html) che supporta touch screen fisici.</span><span class="sxs-lookup"><span data-stu-id="9a464-112">[`UnityTouchController`](xref:Microsoft.MixedReality.Toolkit.Input.UnityInput) wraps the [Unity Touch class](https://docs.unity3d.com/ScriptReference/Touch.html) that supports physical touch screens.</span></span>

<span data-ttu-id="9a464-113">Entrambe queste origini di input usano il profilo _gesture Impostazioni_ per convertire rispettivamente gli eventi Touch e Gesture di Unity in Azioni di [input di](input-actions.md)MRTK.</span><span class="sxs-lookup"><span data-stu-id="9a464-113">Both of these input sources use the _Gesture Settings_ profile to translate Unity's Touch and Gesture events respectively into MRTK's [Input Actions](input-actions.md).</span></span> <span data-ttu-id="9a464-114">Questo profilo è disponibile nella pagina _Input System Impostazioni_ profile (Sistema di input).</span><span class="sxs-lookup"><span data-stu-id="9a464-114">This profile can be found under the _Input System Settings_ profile.</span></span>

<img src="../images/input/GestureProfile.png" alt="Gesture Profile" style="max-width:100%;">

## <a name="gesture-events"></a><span data-ttu-id="9a464-115">Eventi per i movimenti</span><span class="sxs-lookup"><span data-stu-id="9a464-115">Gesture events</span></span>

<span data-ttu-id="9a464-116">Gli eventi di movimento vengono ricevuti implementando una delle interfacce del gestore movimenti: [`IMixedRealityGestureHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGestureHandler) o [`IMixedRealityGestureHandler<TYPE>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGestureHandler`1) (vedere la tabella dei [gestori eventi](input-events.md)).</span><span class="sxs-lookup"><span data-stu-id="9a464-116">Gesture events are received by implementing one of the gesture handler interfaces: [`IMixedRealityGestureHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGestureHandler) or [`IMixedRealityGestureHandler<TYPE>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGestureHandler`1) (see table of [event handlers](input-events.md)).</span></span>

<span data-ttu-id="9a464-117">Vedere [Scena di esempio per](#example-scene) un'implementazione di esempio di un gestore eventi di movimento.</span><span class="sxs-lookup"><span data-stu-id="9a464-117">See [Example Scene](#example-scene) for an example implementation of a gesture event handler.</span></span>

<span data-ttu-id="9a464-118">Quando si implementa la versione generica, gli *eventi OnGestureCompleted* e *OnGestureUpdated* possono ricevere dati tipizzati dei tipi seguenti:</span><span class="sxs-lookup"><span data-stu-id="9a464-118">When implementing the generic version, the *OnGestureCompleted* and *OnGestureUpdated* events can receive typed data of the following types:</span></span>

- <span data-ttu-id="9a464-119">`Vector2` - Movimento di posizione 2D.</span><span class="sxs-lookup"><span data-stu-id="9a464-119">`Vector2` - 2D position gesture.</span></span> <span data-ttu-id="9a464-120">Prodotto dai touch screen per informare dell'oggetto [`deltaPosition`](https://docs.unity3d.com/ScriptReference/Touch-deltaPosition.html) .</span><span class="sxs-lookup"><span data-stu-id="9a464-120">Produced by touch screens to inform of their [`deltaPosition`](https://docs.unity3d.com/ScriptReference/Touch-deltaPosition.html).</span></span>
- <span data-ttu-id="9a464-121">`Vector3` - Movimento di posizione 3D.</span><span class="sxs-lookup"><span data-stu-id="9a464-121">`Vector3` - 3D position gesture.</span></span> <span data-ttu-id="9a464-122">Prodotto da HoloLens informazioni su:</span><span class="sxs-lookup"><span data-stu-id="9a464-122">Produced by HoloLens to inform of:</span></span>
  - <span data-ttu-id="9a464-123">[`cumulativeDelta`](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.ManipulationUpdatedEventArgs-cumulativeDelta.html) di un evento di manipolazione</span><span class="sxs-lookup"><span data-stu-id="9a464-123">[`cumulativeDelta`](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.ManipulationUpdatedEventArgs-cumulativeDelta.html) of a manipulation event</span></span>
  - <span data-ttu-id="9a464-124">[`normalizedOffset`](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.NavigationUpdatedEventArgs-normalizedOffset.html) di un evento di navigazione</span><span class="sxs-lookup"><span data-stu-id="9a464-124">[`normalizedOffset`](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.NavigationUpdatedEventArgs-normalizedOffset.html) of a navigation event</span></span>
- <span data-ttu-id="9a464-125">`Quaternion` - Movimento di rotazione 3D.</span><span class="sxs-lookup"><span data-stu-id="9a464-125">`Quaternion` - 3D rotation gesture.</span></span> <span data-ttu-id="9a464-126">Disponibile per le origini di input personalizzate, ma non attualmente prodotta da nessuna delle origini esistenti.</span><span class="sxs-lookup"><span data-stu-id="9a464-126">Available to custom input sources but not currently produced by any of the existing ones.</span></span>
- <span data-ttu-id="9a464-127">`MixedRealityPose` - Movimento combinato di posizione/rotazione 3D.</span><span class="sxs-lookup"><span data-stu-id="9a464-127">`MixedRealityPose` - Combined 3D position/rotation gesture.</span></span> <span data-ttu-id="9a464-128">Disponibile per le origini di input personalizzate, ma non attualmente prodotta da nessuna delle origini esistenti.</span><span class="sxs-lookup"><span data-stu-id="9a464-128">Available to custom input sources but not currently produced by any of the existing ones.</span></span>

## <a name="order-of-events"></a><span data-ttu-id="9a464-129">Ordine degli eventi</span><span class="sxs-lookup"><span data-stu-id="9a464-129">Order of events</span></span>

<span data-ttu-id="9a464-130">Esistono due catene principali di eventi, a seconda dell'input dell'utente:</span><span class="sxs-lookup"><span data-stu-id="9a464-130">There are two principal chains of events, depending on user input:</span></span>

- <span data-ttu-id="9a464-131">"Hold":</span><span class="sxs-lookup"><span data-stu-id="9a464-131">"Hold":</span></span>
    1. <span data-ttu-id="9a464-132">Tenere premuto il tocco:</span><span class="sxs-lookup"><span data-stu-id="9a464-132">Hold tap:</span></span>
        - <span data-ttu-id="9a464-133">avviare la _manipolazione_</span><span class="sxs-lookup"><span data-stu-id="9a464-133">start _Manipulation_</span></span>
    1. <span data-ttu-id="9a464-134">Tenere premuto il tocco [oltre HoldStartDuration:](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityInputSimulationProfile.HoldStartDuration)</span><span class="sxs-lookup"><span data-stu-id="9a464-134">Hold tap beyond [HoldStartDuration](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityInputSimulationProfile.HoldStartDuration):</span></span>
        - <span data-ttu-id="9a464-135">start _hold_</span><span class="sxs-lookup"><span data-stu-id="9a464-135">start _Hold_</span></span>
    1. <span data-ttu-id="9a464-136">Rilascio tocco:</span><span class="sxs-lookup"><span data-stu-id="9a464-136">Release tap:</span></span>
        - <span data-ttu-id="9a464-137">completare _il blocco_</span><span class="sxs-lookup"><span data-stu-id="9a464-137">complete _Hold_</span></span>
        - <span data-ttu-id="9a464-138">manipolazione _completa_</span><span class="sxs-lookup"><span data-stu-id="9a464-138">complete _Manipulation_</span></span>

- <span data-ttu-id="9a464-139">"Move":</span><span class="sxs-lookup"><span data-stu-id="9a464-139">"Move":</span></span>
    1. <span data-ttu-id="9a464-140">Tenere premuto il tocco:</span><span class="sxs-lookup"><span data-stu-id="9a464-140">Hold tap:</span></span>
        - <span data-ttu-id="9a464-141">avviare la _manipolazione_</span><span class="sxs-lookup"><span data-stu-id="9a464-141">start _Manipulation_</span></span>
    1. <span data-ttu-id="9a464-142">Tenere premuto il tocco [oltre HoldStartDuration:](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityInputSimulationProfile.HoldStartDuration)</span><span class="sxs-lookup"><span data-stu-id="9a464-142">Hold tap beyond [HoldStartDuration](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityInputSimulationProfile.HoldStartDuration):</span></span>
        - <span data-ttu-id="9a464-143">start _hold_</span><span class="sxs-lookup"><span data-stu-id="9a464-143">start _Hold_</span></span>
    1. <span data-ttu-id="9a464-144">Sposta mano oltre [NavigationStartThreshold:](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityInputSimulationProfile.NavigationStartThreshold)</span><span class="sxs-lookup"><span data-stu-id="9a464-144">Move hand beyond [NavigationStartThreshold](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityInputSimulationProfile.NavigationStartThreshold):</span></span>
        - <span data-ttu-id="9a464-145">cancel _Hold_</span><span class="sxs-lookup"><span data-stu-id="9a464-145">cancel _Hold_</span></span>
        - <span data-ttu-id="9a464-146">avviare la _navigazione_</span><span class="sxs-lookup"><span data-stu-id="9a464-146">start _Navigation_</span></span>
    1. <span data-ttu-id="9a464-147">Rilascio tocco:</span><span class="sxs-lookup"><span data-stu-id="9a464-147">Release tap:</span></span>
        - <span data-ttu-id="9a464-148">manipolazione _completa_</span><span class="sxs-lookup"><span data-stu-id="9a464-148">complete _Manipulation_</span></span>
        - <span data-ttu-id="9a464-149">Navigazione _completa_</span><span class="sxs-lookup"><span data-stu-id="9a464-149">complete _Navigation_</span></span>

## <a name="example-scene"></a><span data-ttu-id="9a464-150">Scena di esempio</span><span class="sxs-lookup"><span data-stu-id="9a464-150">Example scene</span></span>

<span data-ttu-id="9a464-151">La scena **HandInteractionGestureEventsExample** (Assets/MRTK/Examples/Demos/HandTracking/Scenes) mostra come usare il puntatore Result per generare un oggetto nella posizione di hit.</span><span class="sxs-lookup"><span data-stu-id="9a464-151">The **HandInteractionGestureEventsExample** (Assets/MRTK/Examples/Demos/HandTracking/Scenes) scene shows how to use the pointer Result to spawn an object at the hit location.</span></span>

<span data-ttu-id="9a464-152">Lo `GestureTester` script (Assets/MRTK/Examples/Demos/HandTracking/Script) è un'implementazione di esempio per visualizzare gli eventi di movimento tramite GameObject.</span><span class="sxs-lookup"><span data-stu-id="9a464-152">The `GestureTester` (Assets/MRTK/Examples/Demos/HandTracking/Script) script is an example implementation to visualize gesture events via GameObjects.</span></span> <span data-ttu-id="9a464-153">Le funzioni del gestore modificano il colore degli oggetti indicatore e visualizzano l'ultimo evento registrato negli oggetti di testo nella scena.</span><span class="sxs-lookup"><span data-stu-id="9a464-153">The handler functions change the color of indicator objects and display the last recorded event in text objects in the scene.</span></span>

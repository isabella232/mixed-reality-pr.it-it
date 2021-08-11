---
title: Movimenti
description: Docummentation on Gestures and its events in MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, movimenti,
ms.openlocfilehash: aeefc0f07d54adb0516f43833d23f27acd102c4d55f78e7bc770577653b7d1c8
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115190915"
---
# <a name="gestures"></a>Movimenti

I movimenti sono eventi di input basati sulle mani umane. Esistono due tipi di dispositivi che generano eventi di input dei movimenti in MRTK:

- Windows Mixed Reality dispositivi, ad esempio HoloLens. Vengono descritti i movimenti di avvicinamento delle dita ("Air Tap") e i movimenti di tocco e sospensione.

  Per altre informazioni sui movimenti HoloLens, vedere la [documentazione Windows Mixed Reality gestures](https://docs.microsoft.com/windows/mixed-reality/gestures).

  [`WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityDeviceManager)esegue il wrapping [di Unity XR. Wsa. Input.GestureRecognizer](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.GestureRecognizer.html) per utilizzare gli eventi di movimento di Unity HoloLens dispositivi.

- Dispositivi touch screen.

  [`UnityTouchController`](xref:Microsoft.MixedReality.Toolkit.Input.UnityInput) esegue il wrapping [della classe Unity Touch](https://docs.unity3d.com/ScriptReference/Touch.html) che supporta touch screen fisici.

Entrambe queste origini di input usano il profilo _di_ Impostazioni gesture per convertire rispettivamente gli eventi Touch e Gesture di Unity in Azioni [di input](input-actions.md)di MRTK. Questo profilo è disponibile nel _profilo_ Impostazioni input.

<img src="../images/input/GestureProfile.png" alt="Gesture Profile" style="max-width:100%;">

## <a name="gesture-events"></a>Eventi per i movimenti

Gli eventi di movimento vengono ricevuti implementando una delle interfacce del gestore movimenti: [`IMixedRealityGestureHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGestureHandler) o [`IMixedRealityGestureHandler<TYPE>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGestureHandler`1) (vedere la tabella [dei gestori eventi](input-events.md)).

Vedere [Scena di esempio](#example-scene) per un'implementazione di esempio di un gestore eventi di movimento.

Quando si implementa la versione generica, gli *eventi OnGestureCompleted* e *OnGestureUpdated* possono ricevere dati tipizzati dei tipi seguenti:

- `Vector2` - Movimento di posizione 2D. Prodotto da touch screen per informare dell'oggetto [`deltaPosition`](https://docs.unity3d.com/ScriptReference/Touch-deltaPosition.html) .
- `Vector3` - Movimento di posizione 3D. Prodotto da HoloLens informazioni su:
  - [`cumulativeDelta`](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.ManipulationUpdatedEventArgs-cumulativeDelta.html) di un evento di manipolazione
  - [`normalizedOffset`](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.NavigationUpdatedEventArgs-normalizedOffset.html) di un evento di navigazione
- `Quaternion` - Movimento di rotazione 3D. Disponibile per le origini di input personalizzate, ma non attualmente prodotte da nessuna delle origini esistenti.
- `MixedRealityPose` - Movimento combinato di posizione/rotazione 3D. Disponibile per le origini di input personalizzate, ma non attualmente prodotte da nessuna delle origini esistenti.

## <a name="order-of-events"></a>Ordine degli eventi

Esistono due catene principali di eventi, a seconda dell'input dell'utente:

- "Hold":
    1. Tenere premuto toccare:
        - avviare la _manipolazione_
    1. Tenere premuto toccare oltre [HoldStartDuration](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityInputSimulationProfile.HoldStartDuration):
        - start _hold (Avvia blocco)_
    1. Toccare Rilascia:
        - completare _l'esenzione_
        - manipolazione _completa_

- "Move":
    1. Tenere premuto toccare:
        - avviare la _manipolazione_
    1. Tenere premuto toccare oltre [HoldStartDuration](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityInputSimulationProfile.HoldStartDuration):
        - start _hold (Avvia blocco)_
    1. Spostare la mano oltre [NavigationStartThreshold](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityInputSimulationProfile.NavigationStartThreshold):
        - annullare _il blocco_
        - avviare _la navigazione_
    1. Toccare Rilascia:
        - manipolazione _completa_
        - completare _la navigazione_

## <a name="example-scene"></a>Scena di esempio

La scena **HandInteractionGestureEventsExample** (Assets/MRTK/Examples/Demos/HandTracking/Scenes) illustra come usare il puntatore Result per generare un oggetto nella posizione di hit.

Lo script (Assets/MRTK/Examples/Demos/HandTracking/Script) è un'implementazione di esempio per visualizzare gli eventi dei movimenti `GestureTester` tramite GameObjects. Le funzioni del gestore modificano il colore degli oggetti indicatore e visualizzano l'ultimo evento registrato negli oggetti di testo nella scena.

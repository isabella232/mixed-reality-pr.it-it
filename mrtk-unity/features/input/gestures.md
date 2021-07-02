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
# <a name="gestures"></a>Movimenti

I movimenti sono eventi di input basati sulle mani umane. Esistono due tipi di dispositivi che generano eventi di input movimenti in MRTK:

- Windows Mixed Reality dispositivi, ad esempio HoloLens. Questo articolo descrive i movimenti di avvicinamento delle dita ("Tocco d'aria") e i movimenti di tocco e tenere premuto.

  Per altre informazioni sui movimenti HoloLens, vedere la [documentazione Windows Mixed Reality movimenti.](/windows/mixed-reality/gestures)

  [`WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityDeviceManager)esegue il wrapping [di Unity XR. Wsa. Input.GestureRecognizer](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.GestureRecognizer.html) per utilizzare gli eventi di movimento di Unity HoloLens dispositivi.

- Dispositivi touch screen.

  [`UnityTouchController`](xref:Microsoft.MixedReality.Toolkit.Input.UnityInput) esegue il wrapping [della classe Touch di Unity](https://docs.unity3d.com/ScriptReference/Touch.html) che supporta touch screen fisici.

Entrambe queste origini di input usano il profilo _gesture Impostazioni_ per convertire rispettivamente gli eventi Touch e Gesture di Unity in Azioni di [input di](input-actions.md)MRTK. Questo profilo è disponibile nella pagina _Input System Impostazioni_ profile (Sistema di input).

<img src="../images/input/GestureProfile.png" alt="Gesture Profile" style="max-width:100%;">

## <a name="gesture-events"></a>Eventi per i movimenti

Gli eventi di movimento vengono ricevuti implementando una delle interfacce del gestore movimenti: [`IMixedRealityGestureHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGestureHandler) o [`IMixedRealityGestureHandler<TYPE>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGestureHandler`1) (vedere la tabella dei [gestori eventi](input-events.md)).

Vedere [Scena di esempio per](#example-scene) un'implementazione di esempio di un gestore eventi di movimento.

Quando si implementa la versione generica, gli *eventi OnGestureCompleted* e *OnGestureUpdated* possono ricevere dati tipizzati dei tipi seguenti:

- `Vector2` - Movimento di posizione 2D. Prodotto dai touch screen per informare dell'oggetto [`deltaPosition`](https://docs.unity3d.com/ScriptReference/Touch-deltaPosition.html) .
- `Vector3` - Movimento di posizione 3D. Prodotto da HoloLens informazioni su:
  - [`cumulativeDelta`](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.ManipulationUpdatedEventArgs-cumulativeDelta.html) di un evento di manipolazione
  - [`normalizedOffset`](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.NavigationUpdatedEventArgs-normalizedOffset.html) di un evento di navigazione
- `Quaternion` - Movimento di rotazione 3D. Disponibile per le origini di input personalizzate, ma non attualmente prodotta da nessuna delle origini esistenti.
- `MixedRealityPose` - Movimento combinato di posizione/rotazione 3D. Disponibile per le origini di input personalizzate, ma non attualmente prodotta da nessuna delle origini esistenti.

## <a name="order-of-events"></a>Ordine degli eventi

Esistono due catene principali di eventi, a seconda dell'input dell'utente:

- "Hold":
    1. Tenere premuto il tocco:
        - avviare la _manipolazione_
    1. Tenere premuto il tocco [oltre HoldStartDuration:](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityInputSimulationProfile.HoldStartDuration)
        - start _hold_
    1. Rilascio tocco:
        - completare _il blocco_
        - manipolazione _completa_

- "Move":
    1. Tenere premuto il tocco:
        - avviare la _manipolazione_
    1. Tenere premuto il tocco [oltre HoldStartDuration:](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityInputSimulationProfile.HoldStartDuration)
        - start _hold_
    1. Sposta mano oltre [NavigationStartThreshold:](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityInputSimulationProfile.NavigationStartThreshold)
        - cancel _Hold_
        - avviare la _navigazione_
    1. Rilascio tocco:
        - manipolazione _completa_
        - Navigazione _completa_

## <a name="example-scene"></a>Scena di esempio

La scena **HandInteractionGestureEventsExample** (Assets/MRTK/Examples/Demos/HandTracking/Scenes) mostra come usare il puntatore Result per generare un oggetto nella posizione di hit.

Lo `GestureTester` script (Assets/MRTK/Examples/Demos/HandTracking/Script) è un'implementazione di esempio per visualizzare gli eventi di movimento tramite GameObject. Le funzioni del gestore modificano il colore degli oggetti indicatore e visualizzano l'ultimo evento registrato negli oggetti di testo nella scena.

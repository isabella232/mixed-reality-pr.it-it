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
# <a name="gestures"></a>Movimenti

I movimenti sono eventi di input basati su mani umane. Esistono due tipi di dispositivi che generano eventi di input di movimento in MRTK:

- Dispositivi di realtà mista di Windows, ad esempio HoloLens. Questo descrive i movimenti di pizzicotto ("rubinetto aereo") e i movimenti di tocco e mantenimento.

  Per ulteriori informazioni sui movimenti HoloLens, vedere la [documentazione sui movimenti di realtà mista di Windows](https://docs.microsoft.com/windows/mixed-reality/gestures).

  [`WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityDeviceManager) esegue il wrapping di [Unity XR. WSA. Input. GestureRecognizer](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.GestureRecognizer.html) per utilizzare gli eventi di movimento di Unity dai dispositivi HoloLens.

- Dispositivi touchscreen.

  [`UnityTouchController`](xref:Microsoft.MixedReality.Toolkit.Input.UnityInput) esegue il wrapping della [classe Touch di Unity](https://docs.unity3d.com/ScriptReference/Touch.html) che supporta le schermate touch fisiche.

Entrambe queste origini di input usano il profilo _Impostazioni movimenti_ per convertire rispettivamente gli eventi di tocco e movimento di Unity nelle [azioni di input](input-actions.md)di MRTK. Questo profilo si trova nel profilo _Impostazioni sistema di input_ .

<img src="../images/input/GestureProfile.png" alt="Gesture Profile" style="max-width:100%;">

## <a name="gesture-events"></a>Eventi per i movimenti

Gli eventi di movimento vengono ricevuti implementando una delle interfacce del gestore movimenti: [`IMixedRealityGestureHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGestureHandler) o [`IMixedRealityGestureHandler<TYPE>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGestureHandler`1) (vedere la tabella dei [gestori eventi](input-events.md)).

Vedere la [scena di esempio](#example-scene) per un'implementazione di esempio di un gestore eventi di movimento.

Quando si implementa la versione generica, gli eventi *OnGestureCompleted* e *OnGestureUpdated* possono ricevere dati tipizzati dei tipi seguenti:

- `Vector2` -movimento di posizione 2D. Prodotto da touch screen per informarli [`deltaPosition`](https://docs.unity3d.com/ScriptReference/Touch-deltaPosition.html) .
- `Vector3` -movimento di posizione 3D. Prodotto da HoloLens per informare:
  - [`cumulativeDelta`](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.ManipulationUpdatedEventArgs-cumulativeDelta.html) di un evento di manipolazione
  - [`normalizedOffset`](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.NavigationUpdatedEventArgs-normalizedOffset.html) di un evento di navigazione
- `Quaternion` -movimento di rotazione 3D. Disponibile per le origini di input personalizzate ma non per quelle esistenti.
- `MixedRealityPose` -Movimento di posizione/rotazione 3D combinato. Disponibile per le origini di input personalizzate ma non per quelle esistenti.

## <a name="order-of-events"></a>Ordine degli eventi

Esistono due catene principali di eventi, a seconda dell'input dell'utente:

- "Mantieni":
    1. Tieni premuto il tocco:
        - Avvia _manipolazione_
    1. Mantieni il tocco oltre [HoldStartDuration](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityInputSimulationProfile.HoldStartDuration):
        - inizio _attesa_
    1. Toccare versione:
        - completa _attesa_
        - _manipolazione_ completa

- "Sposta":
    1. Tieni premuto il tocco:
        - Avvia _manipolazione_
    1. Mantieni il tocco oltre [HoldStartDuration](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityInputSimulationProfile.HoldStartDuration):
        - inizio _attesa_
    1. Spostare la mano oltre [NavigationStartThreshold](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityInputSimulationProfile.NavigationStartThreshold):
        - Annulla _attesa_
        - Avvia _spostamento_
    1. Toccare versione:
        - _manipolazione_ completa
        - _navigazione_ completa

## <a name="example-scene"></a>Scena di esempio

La scena **HandInteractionGestureEventsExample** (assets/MRTK/examples/Demos/HandTracking/scenes) Mostra come usare il risultato del puntatore per generare un oggetto nella posizione di hit.

Lo `GestureTester` script (assets/MRTK/examples/Demos/HandTracking/script) è un'implementazione di esempio per visualizzare gli eventi di movimento tramite GameObject. Le funzioni del gestore modificano il colore degli oggetti indicatore e visualizzano l'ultimo evento registrato negli oggetti testo della scena.

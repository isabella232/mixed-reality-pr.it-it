---
title: Slider
description: Panoramica dei dispositivi di scorrimento MRTK
author: RogPodge
ms.author: roliu
ms.date: 06/18/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, dispositivi di scorrimento,
ms.openlocfilehash: be19806e0202f6cb3ddcea1a80c2c40811aff4f2
ms.sourcegitcommit: e9661d3bab061f9499134226ef3b87751ec56277
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/22/2021
ms.locfileid: "112426877"
---
# <a name="sliders"></a>Dispositivi di scorrimento

![Esempio di dispositivo di scorrimento](../images/slider/MRTK_UX_Slider_Main.jpg)

I dispositivi di scorrimento sono componenti dell'interfaccia utente che consentono di modificare continuamente un valore spostando un dispositivo di scorrimento su una traccia. Attualmente il dispositivo di scorrimento avvicinamento delle dita può essere spostato afferrando direttamente il dispositivo di scorrimento, direttamente o a distanza. I dispositivi di scorrimento funzionano in AR e VR, usando controller del movimento, mani o movimenti e voce.

## <a name="example-scene"></a>Scena di esempio

È possibile trovare esempi nella scena **SliderExample** in `MRTK/Examples/Demos/UX/Slider/Scenes/` .

## <a name="how-to-use-sliders"></a>Come usare i dispositivi di scorrimento

Trascinare e rilasciare il prefab **PinchSlider** nella gerarchia della scena. Se si vuole modificare o creare un dispositivo di scorrimento personalizzato, ricordarsi di eseguire le operazioni seguenti:

- Assicurarsi che l'oggetto thumb abbia un collisore. Nel prefab PinchSlider il collisore è in `SliderThumb/Button_AnimationContainer/Slider_Button`
- Assicurati che l'oggetto contenente il collisore abbia anche un componente Near Interaction Grabbable (Afferrabile con interazione da vicino) se vuoi essere in grado di afferrare il dispositivo di scorrimento vicino.

È anche consigliabile usare la gerarchia seguente

- PinchSlider: contiene sliderComponent
  - TouchCollider: collisore contenente l'intera area selezionabile del dispositivo di scorrimento. Abilita il comportamento Blocca sulla posizione.
  - SliderThumb : contiene il cursore mobile
  - TrackVisuals : contiene la traccia e qualsiasi altro oggetto visivo
  - OtherVisuals - Contenente qualsiasi altro oggetto visivo

## <a name="slider-events"></a>Eventi dispositivo di scorrimento

I dispositivi di scorrimento espongono gli eventi seguenti:

- OnValueUpdated: viene chiamato ogni volta che cambia il valore del dispositivo di scorrimento
- OnInteractionStarted: chiamata quando l'utente afferra il dispositivo di scorrimento
- OnInteractionEnded: chiamata quando l'utente rilascia il dispositivo di scorrimento
- OnHoverEntered: viene chiamato quando la mano o il controller dell'utente passa il puntatore del mouse sul dispositivo di scorrimento, usando l'interazione da vicino o da lontano.
- OnHoverExited: viene chiamato quando la mano o il controller dell'utente non si trova più vicino al dispositivo di scorrimento.

## <a name="configuring-slider-bound-and-axis"></a>Configurazione del limite e dell'asse del dispositivo di scorrimento

È possibile spostare direttamente i punti iniziale e finale del dispositivo di scorrimento spostando i quadratini di ridimensionamento nella scena:

![Configurazione dei dispositivi di scorrimento](../images/sliders/MRTK_Sliders_Setup.png)

È anche possibile specificare l'asse (nello spazio locale) del dispositivo di scorrimento tramite il campo _Asse dispositivo di_ scorrimento

Se non è possibile usare i quadratini di ridimensionamento, è invece possibile specificare i punti di inizio e di fine del dispositivo di scorrimento tramite i campi _Distanza_ iniziale dispositivo di scorrimento e _Distanza fine dispositivo di scorrimento._ Specificano la posizione iniziale/finale del dispositivo di scorrimento come distanza dal centro del dispositivo di scorrimento, in coordinate locali. Ciò significa che, dopo aver impostato le distanze di inizio e di fine del dispositivo di scorrimento nel modo desiderato, è possibile ridimensionare il dispositivo di scorrimento in modo che sia più piccolo o più grande senza dover aggiornare le distanze di inizio e di fine.

## <a name="inspector-properties"></a>Proprietà del controllo

**Radice thumb** Gameobject che contiene il cursore del dispositivo di scorrimento.

**Blocca sulla posizione** Indica se il dispositivo di scorrimento si blocca sulla posizione designata sul dispositivo di scorrimento

**È toccabile** Indica se questo dispositivo di scorrimento può essere o meno controllabile tramite eventi di tocco

**Collisore del pollice** Collisore che controlla il cursore del dispositivo di scorrimento

**Collisore toccabile** Area del dispositivo di scorrimento che può essere toccata o selezionata quando Blocca in posizione è true.

**Valore dispositivo di scorrimento** Valore del dispositivo di scorrimento.

**Usare le divisioni dei passaggi del dispositivo di scorrimento** Controlla se il dispositivo di scorrimento viene incrementato in passaggi o continuamente.

**Divisioni passaggio dispositivo di scorrimento** Numero di suddivisioni in cui è suddiviso il dispositivo di scorrimento quando l'opzione Usa divisioni passaggio dispositivo di scorrimento è abilitata.

**Tenere traccia degli oggetti visivi** Gameobject che contiene gli oggetti visivi traccia desiderati che si spostano lungo il dispositivo di scorrimento.

**Segni di graduazione** Gameobject che contiene i segni di graduazione desiderati lungo il dispositivo di scorrimento.

**Oggetti visivi Thumb** Gameobject che contiene l'oggetto visivo thumb desiderato che si sposta lungo il dispositivo di scorrimento.

**Asse dispositivo di scorrimento** Asse lungo il dispositivo di scorrimento.

**Distanza iniziale dispositivo di scorrimento** Punto di inizio della traccia del dispositivo di scorrimento, come distanza dal centro lungo l'asse del dispositivo di scorrimento, in unità di spazio locali.

**Distanza di fine dispositivo di scorrimento** Punto in cui termina la traccia del dispositivo di scorrimento, come distanza dal centro lungo l'asse del dispositivo di scorrimento, in unità di spazio locali.

Quando l'utente aggiorna il valore dell'asse del dispositivo di scorrimento nell'editor, se si specifica Track Visuals (Rileva oggetti visivi) o Tick Visuals (Oggetti visivi tick), la trasformazione viene aggiornata.
In particolare, la posizione locale viene reimpostata e la rotazione locale viene impostata in modo da corrispondere all'orientamento dell'asse del dispositivo di scorrimento.
La scalabilità non viene modificata.
Se i segni di graduazione hanno un componente Grid Object Collection, Layout e CellWidth o CellHeight vengono aggiornati di conseguenza in modo che corrispondano all'asse del dispositivo di scorrimento.

## <a name="example-slider-configurations"></a>Esempio di configurazioni del dispositivo di scorrimento

Dispositivi di scorrimento continui con blocca sulla posizione ![ Dispositivi di scorrimento continui](https://user-images.githubusercontent.com/39840334/122488212-d410a400-cf91-11eb-8d31-fc7584ddc465.gif)

Dispositivi di scorrimento passo con blocca sulla posizione

![Dispositivi di scorrimento dei passaggi](https://user-images.githubusercontent.com/39840334/122488226-dc68df00-cf91-11eb-9459-89655bbb054d.gif)

Dispositivi di scorrimento tocco

![Dispositivi di scorrimento tocco](https://user-images.githubusercontent.com/39840334/122488221-d8d55800-cf91-11eb-91a1-bb12debe2797.gif)
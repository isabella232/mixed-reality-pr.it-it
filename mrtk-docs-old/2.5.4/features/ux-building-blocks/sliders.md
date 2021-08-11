---
title: Slider
description: Panoramica dei dispositivi di scorrimento MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, dispositivi di scorrimento,
ms.openlocfilehash: 40ff08c6685d34173acd569f85c35ee52e119c6764b8dd287c2c8120d3ef1f89
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115198589"
---
# <a name="sliders"></a>Dispositivi di scorrimento

![Esempio di dispositivo di scorrimento](../images/slider/MRTK_UX_Slider_Main.jpg)

I dispositivi di scorrimento sono componenti dell'interfaccia utente che consentono di modificare continuamente un valore spostando un dispositivo di scorrimento su una traccia. Attualmente il dispositivo di scorrimento avvicinamento delle dita può essere spostato afferrando direttamente il dispositivo di scorrimento, direttamente o a una distanza. I dispositivi di scorrimento funzionano su AR e VR, usando controller di movimento, mani o movimenti + voce.

## <a name="example-scene"></a>Scena di esempio

È possibile trovare esempi nella scena **SliderExample** in `MRTK/Examples/Demos/UX/Slider/Scenes/` .

## <a name="how-to-use-sliders"></a>Come usare i dispositivi di scorrimento

Trascinare e rilasciare il prefab **PinchSlider** nella gerarchia della scena. Se si vuole modificare o creare un dispositivo di scorrimento personalizzato, ricordarsi di eseguire le operazioni seguenti:

- Assicurarsi che l'oggetto thumb abbia un collisore. Nel prefab PinchSlider il collisore è in `SliderThumb/Button_AnimationContainer/Slider_Button`
- Assicurarsi che l'oggetto che contiene il collisore abbia anche un componente Near Interaction Grabbable su di esso, se si vuole essere in grado di afferrare il dispositivo di scorrimento vicino.

È anche consigliabile usare la gerarchia seguente

- PinchSlider : contiene sliderComponent
  - SliderThumb - Contiene il cursore mobile
  - TrackVisuals : contiene la traccia e qualsiasi altro oggetto visivo
  - OtherVisuals - Contenente qualsiasi altro oggetto visivo

## <a name="slider-events"></a>Eventi dispositivo di scorrimento

I dispositivi di scorrimento espongono gli eventi seguenti:

- OnValueUpdated: chiamato ogni volta che cambia il valore del dispositivo di scorrimento
- OnInteractionStarted: chiamato quando l'utente afferra il dispositivo di scorrimento
- OnInteractionEnded: chiamato quando l'utente rilascia il dispositivo di scorrimento
- OnHoverEntered: chiamato quando la mano o il controller dell'utente passa il puntatore del mouse sul dispositivo di scorrimento, usando un'interazione vicina o lontana.
- OnHoverExited: chiamato quando la mano/controller dell'utente non è più vicino al dispositivo di scorrimento.

## <a name="configuring-slider-bound-and-axis"></a>Configurazione del dispositivo di scorrimento e dell'asse

È possibile spostare direttamente i punti iniziale e finale del dispositivo di scorrimento spostando i punti di manipolazione nella scena:

![Configurazione dei dispositivi di scorrimento](../images/sliders/MRTK_Sliders_Setup.png)

È anche possibile specificare l'asse (nello spazio locale) del dispositivo di scorrimento tramite il _campo Asse dispositivo di_ scorrimento

Se non è possibile usare i punti di manipolazione, è invece possibile specificare i punti iniziale e finale del dispositivo di scorrimento tramite i campi _Distanza_ iniziale dispositivo di scorrimento e _Distanza fine dispositivo di scorrimento._ Questi valori specificano la posizione iniziale/finale del dispositivo di scorrimento come distanza dal centro del dispositivo di scorrimento, in coordinate locali. Ciò significa che dopo aver impostato le distanze iniziale e finale del dispositivo di scorrimento come si vuole, è possibile ridimensionare il dispositivo di scorrimento in modo che sia più piccolo o più grande senza dover aggiornare le distanze iniziale e finale.

## <a name="inspector-properties"></a>Proprietà del controllo

**Radice del cursore** Oggetto gameobject che contiene il dispositivo di scorrimento.

**Valore dispositivo di scorrimento** Valore del dispositivo di scorrimento.

**Tenere traccia degli oggetti visivi** Oggetto gameobject che contiene gli oggetti visivi traccia desiderati che si spostano lungo il dispositivo di scorrimento.

**Segni di graduazione** Oggetto gameobject che contiene i segni di graduazione desiderati che si spostano lungo il dispositivo di scorrimento.

**Oggetti visivi Thumb** Oggetto gameobject che contiene l'oggetto visivo thumb desiderato lungo il dispositivo di scorrimento.

**Asse dispositivo di scorrimento** Asse lungo il dispositivo di scorrimento.

**Distanza iniziale del dispositivo di scorrimento** Posizione in cui inizia la traccia del dispositivo di scorrimento, come distanza dal centro lungo l'asse del dispositivo di scorrimento, in unità di spazio locali.

**Distanza fine dispositivo di scorrimento** Posizione in cui termina la traccia del dispositivo di scorrimento, come distanza dal centro lungo l'asse del dispositivo di scorrimento, in unità di spazio locali.

Quando l'utente aggiorna il valore dell'asse del dispositivo di scorrimento nell'editor, se si specifica Rileva oggetti visivi o Segni di graduazione, la trasformazione viene aggiornata.
In particolare, la posizione locale viene reimpostata e la rotazione locale viene impostata in modo che corrisponda all'orientamento dell'asse del dispositivo di scorrimento.
La scalabilità non viene modificata.
Se i segni di graduazione hanno un componente Raccolta oggetti griglia, layout e CellWidth o CellHeight vengono aggiornati di conseguenza in modo che corrispondano all'asse del dispositivo di scorrimento.

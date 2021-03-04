---
title: README_Slider
description: Panoramica dei dispositivi di scorrimento MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, dispositivi di scorrimento,
ms.openlocfilehash: e8983ffcb1f59f231bb4791cd516f6b2dd70cab6
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/03/2021
ms.locfileid: "101782840"
---
# <a name="sliders"></a>Dispositivi di scorrimento

![Esempio di dispositivo di scorrimento](Images/Slider/MRTK_UX_Slider_Main.jpg)

I dispositivi di scorrimento sono componenti dell'interfaccia utente che consentono di modificare continuamente un valore spostando un dispositivo di scorrimento in una traccia. Attualmente, è possibile spostare il dispositivo di scorrimento a pizzico direttamente o a distanza. I dispositivi di scorrimento funzionano su AR e VR, usando i controller di movimento, le mani o il gesto e la voce.

## <a name="example-scene"></a>Scena di esempio

È possibile trovare esempi nella scena **SliderExample** in `MRTK/Examples/Demos/UX/Slider/Scenes/` .

## <a name="how-to-use-sliders"></a>Come usare i dispositivi di scorrimento

Trascinare e rilasciare il prefabbricato **PinchSlider** nella gerarchia della scena. Se si desidera modificare o creare il proprio dispositivo di scorrimento, ricordarsi di eseguire le operazioni seguenti:

- Verificare che l'oggetto Thumb disponga di un Collider. Nella prefabbricazione PinchSlider, il Collider è on `SliderThumb/Button_AnimationContainer/Slider_Button`
- Verificare che anche l'oggetto che contiene l'oggetto Collider disponga di un componente che può essere rilevabile in prossimità dell'interazione, se si desidera essere in grado di estrarre il dispositivo di scorrimento vicino a.

Si consiglia inoltre di utilizzare la seguente gerarchia

- PinchSlider-contiene sliderComponent
  - SliderThumb-contiene il pollice mobile
  - TrackVisuals-contenente la traccia e altri oggetti visivi
  - OtherVisuals-contenenti altri oggetti visivi

## <a name="slider-events"></a>Eventi Slider

I dispositivi di scorrimento espongono gli eventi seguenti:

- OnValueUpdated-chiamato ogni volta che viene modificato il valore del dispositivo di scorrimento
- OnInteractionStarted: viene chiamato quando l'utente estrae il dispositivo di scorrimento
- OnInteractionEnded: viene chiamato quando l'utente rilascia il dispositivo di scorrimento
- OnHoverEntered: viene chiamato quando l'utente o il controller passa il puntatore del mouse sul dispositivo di scorrimento, usando un'interazione vicina o di gran lunga.
- OnHoverExited: viene chiamato quando la mano o il controller dell'utente non è più vicino al dispositivo di scorrimento.

## <a name="configuring-slider-bound-and-axis"></a>Configurazione dell'asse e del limite del dispositivo di scorrimento

È possibile spostare direttamente i punti iniziale e finale del dispositivo di scorrimento spostando gli handle nella scena:

![Configurazione Slider](Images/Sliders/MRTK_Sliders_Setup.png)

È anche possibile specificare l'asse (nello spazio locale) del dispositivo di scorrimento tramite il campo dell' _asse del dispositivo di scorrimento_

Se non è possibile usare gli handle, è invece possibile specificare i punti iniziale e finale del dispositivo di scorrimento tramite i campi distanza _iniziale_ del dispositivo di scorrimento e _distanza di scorrimento_ . Che specificano la posizione iniziale/finale del dispositivo di scorrimento come distanza dal centro del dispositivo di scorrimento, in coordinate locali. Ciò significa che, una volta impostate le distanze di inizio e fine del dispositivo di scorrimento, è possibile ridimensionare il dispositivo di scorrimento in modo che sia più piccolo o più grande senza dover aggiornare le distanze di inizio e fine.

## <a name="inspector-properties"></a>Proprietà di Inspector

**Radice Thumb** GameObject che contiene il cursore del dispositivo di scorrimento.

**Valore dispositivo di scorrimento** Valore del dispositivo di scorrimento.

**Tenere traccia degli oggetti visivi** GameObject che contiene gli oggetti visivi di rilevamento desiderati che passano lungo il dispositivo di scorrimento.

**Segni di graduazione** GameObject che contiene i segni di graduazione desiderati che passano lungo il dispositivo di scorrimento.

Oggetti **visivi Thumb** GameObject che contiene l'oggetto visivo Thumb desiderato che va lungo il dispositivo di scorrimento.

**Asse del dispositivo di scorrimento** Asse in cui viene spostato il dispositivo di scorrimento.

**Distanza avvio dispositivo di scorrimento** Dove inizia la traccia del dispositivo di scorrimento, come distanza dal centro lungo l'asse del dispositivo di scorrimento, in unità di spazio locale.

**Distanza finale dispositivo di scorrimento** Dove la traccia del dispositivo di scorrimento termina, come distanza dal centro lungo l'asse del dispositivo di scorrimento, in unità di spazio locale.

Quando l'utente aggiorna il valore dell'asse del dispositivo di scorrimento nell'editor, se vengono specificati oggetti visivi di rilevamento o oggetti visivi di selezione, la relativa trasformazione viene aggiornata.
In particolare, la posizione locale viene reimpostata e la rotazione locale viene impostata in modo da corrispondere all'orientamento dell'asse del dispositivo di scorrimento.
La scalabilità non è stata modificata.
Se i segni di graduazione contengono un componente della raccolta di oggetti Grid, il layout e CellWidth o CellHeight vengono aggiornati di conseguenza in modo da corrispondere all'asse del dispositivo di scorrimento.

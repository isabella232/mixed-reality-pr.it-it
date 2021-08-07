---
title: Finestra di dialogo
description: Descrizione per i controlli finestra di dialogo.
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: c97057d3e82de36638c824c7ca11fc354a34c9fcf17d7d0165753f1dc88cc375
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115211641"
---
# <a name="dialog"></a>Finestra di dialogo

![Finestra di dialogo](../images/dialog/MRTK_UX_Dialog_Main.png)

I controlli finestra di dialogo sono sovrapposizioni dell'interfaccia utente che forniscono informazioni contestuali sull'app. Spesso richiedono un'azione da parte dell'utente. Usare finestre di dialogo per inviare notifiche agli utenti riguardo informazioni importanti, per chiedere conferma o per informazioni aggiuntive prima di completare un'azione.

## <a name="example-scene"></a>Scena di esempio

È possibile trovare esempi nella **scena DialogExample** in: [MRTK/Examples/Demo/UX/Dialog](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MRTK/Examples/Demos/UX/Dialog)

## <a name="how-to-use-dialog-control"></a>Come usare il controllo Dialog

MRTK fornisce tre prefab dialog:

- DialogSmall_192x96.prefab
- DialogMedium_192x128.prefab
- DialogLarge_192x192.prefab

Usare Dialog.Open() per aprire una nuova finestra di dialogo. Specificare il prefab della finestra di dialogo, il numero di pulsanti, il testo del titolo, il testo del messaggio, la distanza di posizionamento (vicino o lontano), le variabili aggiuntive. Nella finestra di dialogo sono disponibili le opzioni della finestra di dialogo "Conferma(pulsante singolo)" e "Scelta (due pulsanti)".

```c#
public static Dialog Open(GameObject dialogPrefab, DialogButtonType buttons, string title, string message, bool placeForNearInteraction, System.Object variable = null)
```

### <a name="example-of-opening-large-dialog-with-single-ok-button-placed-at-far-interaction-range-gaze-hand-ray-motion-controller"></a>Esempio di apertura di una finestra di dialogo di grandi dimensioni con un singolo pulsante "OK", posizionato all'intervallo di interazione lontano (sguardo fisso, raggio della mano, controller del movimento)

```c#
Dialog.Open(DialogPrefabLarge, DialogButtonType.OK, "Confirmation Dialog, Large, Far", "This is an example of a large dialog with only one button, placed at far interaction range", false);
```

### <a name="example-of-opening-small-dialog-with-single-ok-button-placed-at-near-interaction-range-direct-hand-interaction"></a>Esempio di apertura di una finestra di dialogo piccola con un singolo pulsante "OK", posizionato in prossimità dell'intervallo di interazione (interazione diretta)

```c#
Dialog.Open(DialogPrefabSmall, DialogButtonType.Yes | DialogButtonType.No, "Confirmation Dialog, Small, Far", "This is an example of a small dialog with a choice message, placed at near interaction range", true);
```

Per altri dettagli, vedere `DialogExampleController.cs` nella scena DialogExample.unity.

---
title: Finestra di dialogo
description: Descrizione per i controlli finestra di dialogo.
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: 5d63fcfe79a1c3b09c78f435cec3c2155b403795993f46628cf0f5743bfd42a7
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115203678"
---
# <a name="dialog"></a>Finestra di dialogo

![Finestra di dialogo](../images/dialog/MRTK_UX_Dialog_Main.png)

I controlli finestra di dialogo sono sovrimpressione dell'interfaccia utente che forniscono informazioni contestuali sull'app. Spesso richiedono un'azione da parte dell'utente. Usare finestre di dialogo per inviare notifiche agli utenti riguardo informazioni importanti, per chiedere conferma o per informazioni aggiuntive prima di completare un'azione.

## <a name="example-scene"></a>Scena di esempio

È possibile trovare esempi nella **scena DialogExample** in: [MRTK/Examples/Demo/UX/Dialog](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/main/Assets/MRTK/Examples/Demos/UX/Dialog)

## <a name="how-to-use-dialog-control"></a>Come usare il controllo Dialog

MRTK fornisce tre prefab di dialogo:

- DialogSmall_192x96.prefab
- DialogMedium_192x128.prefab
- DialogLarge_192x192.prefab

Usare Dialog.Open() per aprire una nuova finestra di dialogo. Specificare il prefab della finestra di dialogo, il numero di pulsanti, il testo del titolo, il testo del messaggio, la distanza di posizionamento (vicino o lontano), le variabili aggiuntive. Nella finestra di dialogo sono disponibili le opzioni della finestra di dialogo "Conferma (pulsante singolo)" e "Scelta (due pulsanti)".

```c#
public static Dialog Open(GameObject dialogPrefab, DialogButtonType buttons, string title, string message, bool placeForNearInteraction, System.Object variable = null)
```

### <a name="example-of-opening-a-large-dialog-with-a-single-ok-button-placed-at-far-interaction-range-gaze-hand-ray-motion-controller"></a>Esempio di apertura di una finestra di dialogo di grandi dimensioni con un singolo pulsante "OK", posizionato in corrispondenza dell'intervallo di interazione da lontano (sguardo fisso, raggio della mano, controller del movimento)

```c#
Dialog.Open(DialogPrefabLarge, DialogButtonType.OK, "Confirmation Dialog, Large, Far", "This is an example of a large dialog with only one button, placed at far interaction range", false);
```

### <a name="example-of-opening-a-small-dialog-containing-a-choice-message-for-the-user-placed-at-near-interaction-range-direct-hand-interaction"></a>Esempio di apertura di un dialogo piccolo contenente un messaggio di scelta per l'utente, posizionato in un intervallo di interazione vicino (interazione diretta)

```c#
Dialog.Open(DialogPrefabSmall, DialogButtonType.Yes | DialogButtonType.No, "Confirmation Dialog, Small, Near", "This is an example of a small dialog with a choice message, placed at near interaction range", true);
```

Per altri dettagli, vedere `DialogExampleController.cs` la scena DialogExample.unity.

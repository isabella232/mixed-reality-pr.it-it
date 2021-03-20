---
title: Finestra di dialogo
description: Descrizione per i controlli della finestra di dialogo.
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: 524a7febc791e56e84388c92debf1192f8b081ef
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2021
ms.locfileid: "104685654"
---
# <a name="dialog"></a>Finestra di dialogo

![Finestra di dialogo](../images/dialog/MRTK_UX_Dialog_Main.png)

I controlli della finestra di dialogo sono sovrapposizioni dell'interfaccia utente che forniscono informazioni sull'app contestuale. Spesso richiedono un'azione da parte dell'utente. Usare finestre di dialogo per inviare notifiche agli utenti riguardo informazioni importanti, per chiedere conferma o per informazioni aggiuntive prima di completare un'azione.

## <a name="example-scene"></a>Scena di esempio

È possibile trovare esempi nella scena **DialogExample** in: [MRTK/examples/demo/UX/Dialog](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MRTK/Examples/Demos/UX/Dialog)

## <a name="how-to-use-dialog-control"></a>Come usare il controllo finestra di dialogo

MRTK offre tre prefabbricati di finestre di dialogo:

- DialogSmall_192x96. prefabbricate
- DialogMedium_192x128. prefabbricate
- DialogLarge_192x192. prefabbricate

Usare dialog. Open () per aprire una nuova finestra di dialogo. Specificare la finestra di dialogo prefabbricata, il numero di pulsanti, il testo del titolo, il testo del messaggio, la distanza di posizionamento (quasi o lontano), le variabili aggiuntive) Nella finestra di dialogo sono disponibili le opzioni della finestra di dialogo ' conferma (pulsante singolo)' è scelta (due pulsanti)'.

```c#
public static Dialog Open(GameObject dialogPrefab, DialogButtonType buttons, string title, string message, bool placeForNearInteraction, System.Object variable = null)
```

### <a name="example-of-opening-large-dialog-with-single-ok-button-placed-at-far-interaction-range-gaze-hand-ray-motion-controller"></a>Esempio di apertura di una finestra di dialogo di grandi dimensioni con il pulsante singolo ' OK ', posizionato in corrispondenza dell'intervallo di interazione (sguardo, raggio di mano, controller di movimento)

```c#
Dialog.Open(DialogPrefabLarge, DialogButtonType.OK, "Confirmation Dialog, Large, Far", "This is an example of a large dialog with only one button, placed at far interaction range", false);
```

### <a name="example-of-opening-small-dialog-with-single-ok-button-placed-at-near-interaction-range-direct-hand-interaction"></a>Esempio di apertura di una finestra di dialogo di piccole dimensioni con il pulsante "OK", posizionata nell'intervallo di interazione near (interazione diretta)

```c#
Dialog.Open(DialogPrefabSmall, DialogButtonType.Yes | DialogButtonType.No, "Confirmation Dialog, Small, Far", "This is an example of a small dialog with a choice message, placed at near interaction range", true);
```

Per altri dettagli, vedere `DialogExampleController.cs` nella scena DialogExample. Unity.

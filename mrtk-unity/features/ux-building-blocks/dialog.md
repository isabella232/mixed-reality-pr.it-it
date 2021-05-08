---
title: Finestra di dialogo
description: Descrizione per i controlli finestra di dialogo.
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realtà mista, sviluppo, MRTK,
ms.openlocfilehash: 729c3f6a6b9bc63a498c5d76205a0730f52c678a
ms.sourcegitcommit: e89431d12b5fe480c9bc40e176023798fc35001b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/07/2021
ms.locfileid: "109489191"
---
# <a name="dialog"></a><span data-ttu-id="868c7-104">Finestra di dialogo</span><span class="sxs-lookup"><span data-stu-id="868c7-104">Dialog</span></span>

![Finestra di dialogo](../images/dialog/MRTK_UX_Dialog_Main.png)

<span data-ttu-id="868c7-106">I controlli finestra di dialogo sono sovrapposizioni dell'interfaccia utente che forniscono informazioni contestuali sull'app.</span><span class="sxs-lookup"><span data-stu-id="868c7-106">Dialog controls are UI overlays that provide contextual app information.</span></span> <span data-ttu-id="868c7-107">Spesso richiedono un'azione da parte dell'utente.</span><span class="sxs-lookup"><span data-stu-id="868c7-107">They often request some kind of action from the user.</span></span> <span data-ttu-id="868c7-108">Usare finestre di dialogo per inviare notifiche agli utenti riguardo informazioni importanti, per chiedere conferma o per informazioni aggiuntive prima di completare un'azione.</span><span class="sxs-lookup"><span data-stu-id="868c7-108">Use dialogs to notify users of important information or to request confirmation or additional info before an action can be completed.</span></span>

## <a name="example-scene"></a><span data-ttu-id="868c7-109">Scena di esempio</span><span class="sxs-lookup"><span data-stu-id="868c7-109">Example scene</span></span>

<span data-ttu-id="868c7-110">È possibile trovare esempi nella **scena DialogExample** in: [MRTK/Examples/Demo/UX/Dialog](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/main/Assets/MRTK/Examples/Demos/UX/Dialog)</span><span class="sxs-lookup"><span data-stu-id="868c7-110">You can find examples in the **DialogExample** scene under: [MRTK/Examples/Demo/UX/Dialog](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/main/Assets/MRTK/Examples/Demos/UX/Dialog)</span></span>

## <a name="how-to-use-dialog-control"></a><span data-ttu-id="868c7-111">Come usare il controllo Dialog</span><span class="sxs-lookup"><span data-stu-id="868c7-111">How to use Dialog control</span></span>

<span data-ttu-id="868c7-112">MRTK fornisce tre prefab dialog:</span><span class="sxs-lookup"><span data-stu-id="868c7-112">MRTK provides three Dialog prefabs:</span></span>

- <span data-ttu-id="868c7-113">DialogSmall_192x96.prefab</span><span class="sxs-lookup"><span data-stu-id="868c7-113">DialogSmall_192x96.prefab</span></span>
- <span data-ttu-id="868c7-114">DialogMedium_192x128.prefab</span><span class="sxs-lookup"><span data-stu-id="868c7-114">DialogMedium_192x128.prefab</span></span>
- <span data-ttu-id="868c7-115">DialogLarge_192x192.prefab</span><span class="sxs-lookup"><span data-stu-id="868c7-115">DialogLarge_192x192.prefab</span></span>

<span data-ttu-id="868c7-116">Usare Dialog.Open() per aprire una nuova finestra di dialogo.</span><span class="sxs-lookup"><span data-stu-id="868c7-116">Use Dialog.Open() to open a new dialog.</span></span> <span data-ttu-id="868c7-117">Specificare il prefab della finestra di dialogo, il numero di pulsanti, il testo del titolo, il testo del messaggio, la distanza di posizionamento (vicino o lontano), le variabili aggiuntive.</span><span class="sxs-lookup"><span data-stu-id="868c7-117">Specify the dialog prefab, number of buttons, title text, message text, placement distance(near or far), additional variables).</span></span> <span data-ttu-id="868c7-118">Nella finestra di dialogo sono disponibili le opzioni della finestra di dialogo "Conferma(pulsante singolo)" e "Scelta (due pulsanti)".</span><span class="sxs-lookup"><span data-stu-id="868c7-118">Dialog provides 'Confirmation(single button)' and 'Choice(two-buttons)' dialog options.</span></span>

```c#
public static Dialog Open(GameObject dialogPrefab, DialogButtonType buttons, string title, string message, bool placeForNearInteraction, System.Object variable = null)
```

### <a name="example-of-opening-a-large-dialog-with-a-single-ok-button-placed-at-far-interaction-range-gaze-hand-ray-motion-controller"></a><span data-ttu-id="868c7-119">Esempio di apertura di una finestra di dialogo di grandi dimensioni con un singolo pulsante "OK", posizionato in un intervallo di interazione lontano (sguardo fisso, raggio della mano, controller del movimento)</span><span class="sxs-lookup"><span data-stu-id="868c7-119">Example of opening a Large dialog with a single 'OK' button, placed at far interaction range (gaze, hand ray, motion controller)</span></span>

```c#
Dialog.Open(DialogPrefabLarge, DialogButtonType.OK, "Confirmation Dialog, Large, Far", "This is an example of a large dialog with only one button, placed at far interaction range", false);
```

### <a name="example-of-opening-a-small-dialog-containing-a-choice-message-for-the-user-placed-at-near-interaction-range-direct-hand-interaction"></a><span data-ttu-id="868c7-120">Esempio di apertura di un piccolo dialogo contenente un messaggio di scelta per l'utente, posizionato in prossimità dell'intervallo di interazione (interazione diretta)</span><span class="sxs-lookup"><span data-stu-id="868c7-120">Example of opening a Small dialog containing a choice message for the user, placed at near interaction range (direct hand interaction)</span></span>

```c#
Dialog.Open(DialogPrefabSmall, DialogButtonType.Yes | DialogButtonType.No, "Confirmation Dialog, Small, Near", "This is an example of a small dialog with a choice message, placed at near interaction range", true);
```

<span data-ttu-id="868c7-121">Per altri dettagli, vedere `DialogExampleController.cs` nella scena DialogExample.unity.</span><span class="sxs-lookup"><span data-stu-id="868c7-121">For more details, please see `DialogExampleController.cs` in DialogExample.unity scene.</span></span>

---
title: Finestra di dialogo
description: Descrizione per i controlli della finestra di dialogo.
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: aa054e304640ece2ee7346fc573ef869946c8905
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2021
ms.locfileid: "104690601"
---
# <a name="dialog"></a><span data-ttu-id="70c2e-104">Finestra di dialogo</span><span class="sxs-lookup"><span data-stu-id="70c2e-104">Dialog</span></span>

![Finestra di dialogo](../../images/dialog/MRTK_UX_Dialog_Main.png)

<span data-ttu-id="70c2e-106">I controlli della finestra di dialogo sono sovrapposizioni dell'interfaccia utente che forniscono informazioni sull'app contestuale.</span><span class="sxs-lookup"><span data-stu-id="70c2e-106">Dialog controls are UI overlays that provide contextual app information.</span></span> <span data-ttu-id="70c2e-107">Spesso richiedono un'azione da parte dell'utente.</span><span class="sxs-lookup"><span data-stu-id="70c2e-107">They often request some kind of action from the user.</span></span> <span data-ttu-id="70c2e-108">Usare finestre di dialogo per inviare notifiche agli utenti riguardo informazioni importanti, per chiedere conferma o per informazioni aggiuntive prima di completare un'azione.</span><span class="sxs-lookup"><span data-stu-id="70c2e-108">Use dialogs to notify users of important information or to request confirmation or additional info before an action can be completed.</span></span>

## <a name="example-scene"></a><span data-ttu-id="70c2e-109">Scena di esempio</span><span class="sxs-lookup"><span data-stu-id="70c2e-109">Example scene</span></span>

<span data-ttu-id="70c2e-110">È possibile trovare esempi nella scena **DialogExample** in: [MRTK/examples/Experimental/Dialog](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MRTK/SDK/Experimental/Dialog)</span><span class="sxs-lookup"><span data-stu-id="70c2e-110">You can find examples in the **DialogExample** scene under: [MRTK/Examples/Experimental/Dialog](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MRTK/SDK/Experimental/Dialog)</span></span>

## <a name="how-to-use-dialog-control"></a><span data-ttu-id="70c2e-111">Come usare il controllo finestra di dialogo</span><span class="sxs-lookup"><span data-stu-id="70c2e-111">How to use Dialog control</span></span>

<span data-ttu-id="70c2e-112">MRTK offre tre prefabbricati di finestre di dialogo:</span><span class="sxs-lookup"><span data-stu-id="70c2e-112">MRTK provides three Dialog prefabs:</span></span>

- <span data-ttu-id="70c2e-113">DialogSmall_192x96. prefabbricate</span><span class="sxs-lookup"><span data-stu-id="70c2e-113">DialogSmall_192x96.prefab</span></span>
- <span data-ttu-id="70c2e-114">DialogMedium_192x128. prefabbricate</span><span class="sxs-lookup"><span data-stu-id="70c2e-114">DialogMedium_192x128.prefab</span></span>
- <span data-ttu-id="70c2e-115">DialogLarge_192x192. prefabbricate</span><span class="sxs-lookup"><span data-stu-id="70c2e-115">DialogLarge_192x192.prefab</span></span>

<span data-ttu-id="70c2e-116">Usare dialog. Open () per aprire una nuova finestra di dialogo.</span><span class="sxs-lookup"><span data-stu-id="70c2e-116">Use Dialog.Open() to open a new dialog.</span></span> <span data-ttu-id="70c2e-117">Specificare la finestra di dialogo prefabbricata, il numero di pulsanti, il testo del titolo, il testo del messaggio, la distanza di posizionamento (quasi o lontano), le variabili aggiuntive)</span><span class="sxs-lookup"><span data-stu-id="70c2e-117">Specify the dialog prefab, number of buttons, title text, message text, placement distance(near or far), additional variables).</span></span> <span data-ttu-id="70c2e-118">Nella finestra di dialogo sono disponibili le opzioni della finestra di dialogo ' conferma (pulsante singolo)' è scelta (due pulsanti)'.</span><span class="sxs-lookup"><span data-stu-id="70c2e-118">Dialog provides 'Confirmation(single button)' and 'Choice(two-buttons)' dialog options.</span></span>

```c#
public static Dialog Open(GameObject dialogPrefab, DialogButtonType buttons, string title, string message, bool placeForNearInteraction, System.Object variable = null)
```

### <a name="example-of-opening-large-dialog-with-single-ok-button-placed-at-far-interaction-range-gaze-hand-ray-motion-controller"></a><span data-ttu-id="70c2e-119">Esempio di apertura di una finestra di dialogo di grandi dimensioni con il pulsante singolo ' OK ', posizionato in corrispondenza dell'intervallo di interazione (sguardo, raggio di mano, controller di movimento)</span><span class="sxs-lookup"><span data-stu-id="70c2e-119">Example of opening Large dialog with single 'OK' button, placed at far interaction range (gaze, hand ray, motion controller)</span></span>

```c#
Dialog.Open(DialogPrefabLarge, DialogButtonType.OK, "Confirmation Dialog, Large, Far", "This is an example of a large dialog with only one button, placed at far interaction range", false);
```

### <a name="example-of-opening-small-dialog-with-single-ok-button-placed-at-near-interaction-range-direct-hand-interaction"></a><span data-ttu-id="70c2e-120">Esempio di apertura di una finestra di dialogo di piccole dimensioni con il pulsante "OK", posizionata nell'intervallo di interazione near (interazione diretta)</span><span class="sxs-lookup"><span data-stu-id="70c2e-120">Example of opening Small dialog with single 'OK' button, placed at near interaction range (direct hand interaction)</span></span>

```c#
Dialog.Open(DialogPrefabSmall, DialogButtonType.Yes | DialogButtonType.No, "Confirmation Dialog, Small, Far", "This is an example of a small dialog with a choice message, placed at near interaction range", true);
```

<span data-ttu-id="70c2e-121">Per altri dettagli, vedere `DialogExampleController.cs` nella scena DialogExample. Unity.</span><span class="sxs-lookup"><span data-stu-id="70c2e-121">For more details, please see `DialogExampleController.cs` in DialogExample.unity scene.</span></span>

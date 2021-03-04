---
title: Finestra di dialogo
description: Descrizione per i controlli della finestra di dialogo.
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: 7c381cfd000d2f939889cffa8c4f2a47f0b4a2fe
ms.sourcegitcommit: 7a8fa3257a13635ddad77d963e49440f62c19774
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/04/2021
ms.locfileid: "101884068"
---
# <a name="dialog"></a><span data-ttu-id="551e3-104">Finestra di dialogo</span><span class="sxs-lookup"><span data-stu-id="551e3-104">Dialog</span></span>

![Finestra di dialogo](../images/dialog/MRTK_UX_Dialog_Main.png)

<span data-ttu-id="551e3-106">I controlli della finestra di dialogo sono sovrapposizioni dell'interfaccia utente che forniscono informazioni sull'app contestuale.</span><span class="sxs-lookup"><span data-stu-id="551e3-106">Dialog controls are UI overlays that provide contextual app information.</span></span> <span data-ttu-id="551e3-107">Spesso richiedono un'azione da parte dell'utente.</span><span class="sxs-lookup"><span data-stu-id="551e3-107">They often request some kind of action from the user.</span></span> <span data-ttu-id="551e3-108">Usare finestre di dialogo per inviare notifiche agli utenti riguardo informazioni importanti, per chiedere conferma o per informazioni aggiuntive prima di completare un'azione.</span><span class="sxs-lookup"><span data-stu-id="551e3-108">Use dialogs to notify users of important information or to request confirmation or additional info before an action can be completed.</span></span>

## <a name="example-scene"></a><span data-ttu-id="551e3-109">Scena di esempio</span><span class="sxs-lookup"><span data-stu-id="551e3-109">Example scene</span></span>

<span data-ttu-id="551e3-110">È possibile trovare esempi nella scena **DialogExample** in: [MRTK/examples/demo/UX/Dialog](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MRTK/Examples/Demos/UX/Dialog)</span><span class="sxs-lookup"><span data-stu-id="551e3-110">You can find examples in the **DialogExample** scene under: [MRTK/Examples/Demo/UX/Dialog](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MRTK/Examples/Demos/UX/Dialog)</span></span>

## <a name="how-to-use-dialog-control"></a><span data-ttu-id="551e3-111">Come usare il controllo finestra di dialogo</span><span class="sxs-lookup"><span data-stu-id="551e3-111">How to use Dialog control</span></span>

<span data-ttu-id="551e3-112">MRTK offre tre prefabbricati di finestre di dialogo:</span><span class="sxs-lookup"><span data-stu-id="551e3-112">MRTK provides three Dialog prefabs:</span></span>

- <span data-ttu-id="551e3-113">DialogSmall_192x96. prefabbricate</span><span class="sxs-lookup"><span data-stu-id="551e3-113">DialogSmall_192x96.prefab</span></span>
- <span data-ttu-id="551e3-114">DialogMedium_192x128. prefabbricate</span><span class="sxs-lookup"><span data-stu-id="551e3-114">DialogMedium_192x128.prefab</span></span>
- <span data-ttu-id="551e3-115">DialogLarge_192x192. prefabbricate</span><span class="sxs-lookup"><span data-stu-id="551e3-115">DialogLarge_192x192.prefab</span></span>

<span data-ttu-id="551e3-116">Usare dialog. Open () per aprire una nuova finestra di dialogo.</span><span class="sxs-lookup"><span data-stu-id="551e3-116">Use Dialog.Open() to open a new dialog.</span></span> <span data-ttu-id="551e3-117">Specificare la finestra di dialogo prefabbricata, il numero di pulsanti, il testo del titolo, il testo del messaggio, la distanza di posizionamento (quasi o lontano), le variabili aggiuntive)</span><span class="sxs-lookup"><span data-stu-id="551e3-117">Specify the dialog prefab, number of buttons, title text, message text, placement distance(near or far), additional variables).</span></span> <span data-ttu-id="551e3-118">Nella finestra di dialogo sono disponibili le opzioni della finestra di dialogo ' conferma (pulsante singolo)' è scelta (due pulsanti)'.</span><span class="sxs-lookup"><span data-stu-id="551e3-118">Dialog provides 'Confirmation(single button)' and 'Choice(two-buttons)' dialog options.</span></span>

```c#
public static Dialog Open(GameObject dialogPrefab, DialogButtonType buttons, string title, string message, bool placeForNearInteraction, System.Object variable = null)
```

### <a name="example-of-opening-large-dialog-with-single-ok-button-placed-at-far-interaction-range-gaze-hand-ray-motion-controller"></a><span data-ttu-id="551e3-119">Esempio di apertura di una finestra di dialogo di grandi dimensioni con il pulsante singolo ' OK ', posizionato in corrispondenza dell'intervallo di interazione (sguardo, raggio di mano, controller di movimento)</span><span class="sxs-lookup"><span data-stu-id="551e3-119">Example of opening Large dialog with single 'OK' button, placed at far interaction range (gaze, hand ray, motion controller)</span></span>

```c#
Dialog.Open(DialogPrefabLarge, DialogButtonType.OK, "Confirmation Dialog, Large, Far", "This is an example of a large dialog with only one button, placed at far interaction range", false);
```

### <a name="example-of-opening-small-dialog-with-single-ok-button-placed-at-near-interaction-range-direct-hand-interaction"></a><span data-ttu-id="551e3-120">Esempio di apertura di una finestra di dialogo di piccole dimensioni con il pulsante "OK", posizionata nell'intervallo di interazione near (interazione diretta)</span><span class="sxs-lookup"><span data-stu-id="551e3-120">Example of opening Small dialog with single 'OK' button, placed at near interaction range (direct hand interaction)</span></span>

```c#
Dialog.Open(DialogPrefabSmall, DialogButtonType.Yes | DialogButtonType.No, "Confirmation Dialog, Small, Far", "This is an example of a small dialog with a choice message, placed at near interaction range", true);
```

<span data-ttu-id="551e3-121">Per altri dettagli, vedere `DialogExampleController.cs` nella scena DialogExample. Unity.</span><span class="sxs-lookup"><span data-stu-id="551e3-121">For more details, please see `DialogExampleController.cs` in DialogExample.unity scene.</span></span>

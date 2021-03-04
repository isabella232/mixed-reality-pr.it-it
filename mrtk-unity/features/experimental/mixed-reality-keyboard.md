---
title: README_MixedRealityKeyboard
description: Descrizione su come usare la tastiera a realtà mista
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: aa2e4bd12c5a472a7d5f93d34a830d102e466bc9
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/03/2021
ms.locfileid: "101781595"
---
# <a name="mixed-reality-and-hololens-keyboard-helper-classes"></a><span data-ttu-id="131b0-104">Realtà mista e classi helper della tastiera HoloLens</span><span class="sxs-lookup"><span data-stu-id="131b0-104">Mixed Reality and HoloLens Keyboard Helper Classes</span></span>

<span data-ttu-id="131b0-105">In MRTK sono disponibili diversi componenti Helper sperimentali che consentono di avviare e leggere testo dalla [tastiera di sistema](../ux-building-blocks/system-keyboard.md).</span><span class="sxs-lookup"><span data-stu-id="131b0-105">MRTK provides several experimental helper components to assist with launching and reading text from the [System Keyboard](../ux-building-blocks/system-keyboard.md).</span></span>

<span data-ttu-id="131b0-106">Si noti che la tastiera di sistema si comporterà in base alle funzionalità della piattaforma di destinazione, ad esempio la tastiera in HoloLens 2 supporterà le interazioni con la mano diretta, mentre la tastiera su HoloLens (1a generazione) supporterà GGV<sup>[1](https://docs.microsoft.com/windows/mixed-reality/gaze)</sup>.</span><span class="sxs-lookup"><span data-stu-id="131b0-106">Note that the system keyboard will behave according to the target platform's capabilities, for example the keyboard on HoloLens 2 would support direct hand interactions, while the keyboard on HoloLens (1st gen) would support GGV<sup>[1](https://docs.microsoft.com/windows/mixed-reality/gaze)</sup>.</span></span> <span data-ttu-id="131b0-107">Inoltre, la tastiera di sistema non viene visualizzata quando si esegue la [comunicazione remota di Unity](../tools/holographic-remoting.md) dall'editor a un HoloLens.</span><span class="sxs-lookup"><span data-stu-id="131b0-107">Additionally, the system keyboard will not show up when performing [Unity Remoting](../tools/holographic-remoting.md) from the editor to a HoloLens.</span></span>

## <a name="mixedrealitykeyboard"></a><span data-ttu-id="131b0-108">MixedRealityKeyboard</span><span class="sxs-lookup"><span data-stu-id="131b0-108">MixedRealityKeyboard</span></span>

<span data-ttu-id="131b0-109">[`MixedRealityKeyboard`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.MixedRealityKeyboard) è un componente che fornisce metodi per l'avvio e la chiusura di una tastiera di sistema, nonché per l'interazione con il testo immesso dalla tastiera.</span><span class="sxs-lookup"><span data-stu-id="131b0-109">[`MixedRealityKeyboard`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.MixedRealityKeyboard) is a component that provides methods for launching and closing a system keyboard, as well as interacting with text entered by the keyboard.</span></span>  

### <a name="how-to-use"></a><span data-ttu-id="131b0-110">Uso</span><span class="sxs-lookup"><span data-stu-id="131b0-110">How to Use</span></span>

1. <span data-ttu-id="131b0-111">Alleghi il [`MixedRealityKeyboard`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.MixedRealityKeyboard) componente a qualsiasi oggetto.</span><span class="sxs-lookup"><span data-stu-id="131b0-111">Attach the [`MixedRealityKeyboard`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.MixedRealityKeyboard) component to any object.</span></span>
2. <span data-ttu-id="131b0-112">Chiamare `Show()` `Hide()` per visualizzare e nascondere la tastiera e gestire gli `OnShowKeyboard` eventi, `OnHideKeyboard` e `OnCommitText` per gestire quando la tastiera viene visualizzata, nascosta e quando viene premuto il tasto INVIO.</span><span class="sxs-lookup"><span data-stu-id="131b0-112">Call `Show()` `Hide()` to show and hide the keyboard, and handle the `OnShowKeyboard`, `OnHideKeyboard` and `OnCommitText` events to handle when the keyboard is shown, hidden, and when the enter key is pressed.</span></span>

## <a name="input-fields-tmp_keyboardinputfield-and-ui_keyboardinputfield"></a><span data-ttu-id="131b0-113">Campi di input TMP_KeyboardInputField e UI_KeyboardInputField</span><span class="sxs-lookup"><span data-stu-id="131b0-113">Input fields TMP_KeyboardInputField, and UI_KeyboardInputField</span></span>

<span data-ttu-id="131b0-114">Le [`TMP_KeyboardInputField`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.TMP_KeyboardInputField) [`UI_KeyboardInputField`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.UI_KeyboardInputField) classi e sono componenti che possono essere aggiunti ai campi di input di testo per richiamare automaticamente la tastiera di sistema quando si fa clic e aggiornare il contenuto del campo di input di testo quando l'utente immette il testo.</span><span class="sxs-lookup"><span data-stu-id="131b0-114">The [`TMP_KeyboardInputField`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.TMP_KeyboardInputField) and [`UI_KeyboardInputField`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.UI_KeyboardInputField) classes are components that can be added to text input fields to automatically invoke the system keyboard when clicked and update the text input field contents as the user enters text.</span></span>

### <a name="how-to-use"></a><span data-ttu-id="131b0-115">Uso</span><span class="sxs-lookup"><span data-stu-id="131b0-115">How to use</span></span>

1. <span data-ttu-id="131b0-116">Creare un campo di input sia per UnityUI che per TextMeshPro.</span><span class="sxs-lookup"><span data-stu-id="131b0-116">Create an input field for either UnityUI or TextMeshPro.</span></span>
2. <span data-ttu-id="131b0-117">Aggiungere il [`TMP_KeyboardInputField`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.TMP_KeyboardInputField) componente o corrispondente [`UI_KeyboardInputField`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.UI_KeyboardInputField) all'oggetto gioco campo di input.</span><span class="sxs-lookup"><span data-stu-id="131b0-117">Add the corresponding [`TMP_KeyboardInputField`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.TMP_KeyboardInputField) or [`UI_KeyboardInputField`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.UI_KeyboardInputField) component to the input field game object.</span></span>

<span data-ttu-id="131b0-118">I prefabbricati per i campi di input UnityUI e TextMeshPro (TMPro) sono disponibili in "Assets\MRTK\Experimental\MixedRealityKeyboard\Prefabs"</span><span class="sxs-lookup"><span data-stu-id="131b0-118">Prefabs for both UnityUI input fields and TextMeshPro (TMPro) input fields are available at "Assets\MRTK\Experimental\MixedRealityKeyboard\Prefabs"</span></span>

<span data-ttu-id="131b0-119">Un esempio di come usare TMP_KeyboardInputField e UI_KeyboardInputField è "Assets\MRTK\Examples\Experimental\MixedRealityKeyboard\Scenes\MixedRealityKeyboardExample.unity"</span><span class="sxs-lookup"><span data-stu-id="131b0-119">An example of how the to use TMP_KeyboardInputField and UI_KeyboardInputField is at "Assets\MRTK\Examples\Experimental\MixedRealityKeyboard\Scenes\MixedRealityKeyboardExample.unity"</span></span>

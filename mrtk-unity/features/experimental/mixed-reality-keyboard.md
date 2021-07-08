---
title: Tastiera realtà mista
description: descrizione su Come usare la tastiera di realtà mista
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: 6a33ed5b021e90cba56344f32a9c9a33e8fcc476
ms.sourcegitcommit: c260aed8a37855faf9575d968e615959a56a13fc
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/07/2021
ms.locfileid: "113466231"
---
# <a name="mixed-reality-and-hololens-keyboard-helper-classes"></a><span data-ttu-id="667bc-104">Realtà mista e HoloLens helper tastiera</span><span class="sxs-lookup"><span data-stu-id="667bc-104">Mixed Reality and HoloLens Keyboard Helper Classes</span></span>

<span data-ttu-id="667bc-105">MRTK fornisce diversi componenti helper sperimentali per facilitare l'avvio e la lettura di testo dalla [tastiera di sistema.](../ux-building-blocks/system-keyboard.md)</span><span class="sxs-lookup"><span data-stu-id="667bc-105">MRTK provides several experimental helper components to assist with launching and reading text from the [System Keyboard](../ux-building-blocks/system-keyboard.md).</span></span>

<span data-ttu-id="667bc-106">Si noti che la tastiera di sistema si comporterà in base alle funzionalità della piattaforma di destinazione, ad esempio la tastiera in HoloLens 2 supporterebbe le interazioni dirette con la mano, mentre la tastiera di HoloLens (prima generazione) supporterebbe GGV<sup>[1.](/windows/mixed-reality/gaze)</sup></span><span class="sxs-lookup"><span data-stu-id="667bc-106">Note that the system keyboard will behave according to the target platform's capabilities, for example the keyboard on HoloLens 2 would support direct hand interactions, while the keyboard on HoloLens (1st gen) would support GGV<sup>[1](/windows/mixed-reality/gaze)</sup>.</span></span> <span data-ttu-id="667bc-107">Inoltre, la tastiera di sistema non verrà visualizzato quando si esegue la comunicazione remota di [Unity](../tools/holographic-remoting.md) dall'editor a un HoloLens.</span><span class="sxs-lookup"><span data-stu-id="667bc-107">Additionally, the system keyboard will not show up when performing [Unity Remoting](../tools/holographic-remoting.md) from the editor to a HoloLens.</span></span>

## <a name="mixedrealitykeyboard"></a><span data-ttu-id="667bc-108">MixedRealityKeyboard</span><span class="sxs-lookup"><span data-stu-id="667bc-108">MixedRealityKeyboard</span></span>

<span data-ttu-id="667bc-109">[`MixedRealityKeyboard`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.MixedRealityKeyboard) è un componente che fornisce metodi per avviare e chiudere una tastiera di sistema, nonché per interagire con il testo immesso dalla tastiera.</span><span class="sxs-lookup"><span data-stu-id="667bc-109">[`MixedRealityKeyboard`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.MixedRealityKeyboard) is a component that provides methods for launching and closing a system keyboard, as well as interacting with text entered by the keyboard.</span></span>  

### <a name="how-to-use"></a><span data-ttu-id="667bc-110">Uso</span><span class="sxs-lookup"><span data-stu-id="667bc-110">How to Use</span></span>

1. <span data-ttu-id="667bc-111">Collegare il [`MixedRealityKeyboard`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.MixedRealityKeyboard) componente a qualsiasi oggetto.</span><span class="sxs-lookup"><span data-stu-id="667bc-111">Attach the [`MixedRealityKeyboard`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.MixedRealityKeyboard) component to any object.</span></span>
2. <span data-ttu-id="667bc-112">Chiamare per mostrare e nascondere la tastiera e gestire gli eventi , e da gestire quando la tastiera viene visualizzata, nascosta e quando viene `ShowKeyboard(string text = "", bool multiLine = false)` `HideKeyboard()` premuto il tasto `OnShowKeyboard` `OnHideKeyboard` `OnCommitText` INVIO.</span><span class="sxs-lookup"><span data-stu-id="667bc-112">Call `ShowKeyboard(string text = "", bool multiLine = false)` `HideKeyboard()` to show and hide the keyboard, and handle the `OnShowKeyboard`, `OnHideKeyboard` and `OnCommitText` events to handle when the keyboard is shown, hidden, and when the enter key is pressed.</span></span>

## <a name="input-fields-tmp_keyboardinputfield-and-ui_keyboardinputfield"></a><span data-ttu-id="667bc-113">Campi di TMP_KeyboardInputField e UI_KeyboardInputField</span><span class="sxs-lookup"><span data-stu-id="667bc-113">Input fields TMP_KeyboardInputField, and UI_KeyboardInputField</span></span>

<span data-ttu-id="667bc-114">Le classi e sono componenti che possono essere aggiunti ai campi di input di testo per richiamare automaticamente la tastiera di sistema quando si fa clic e aggiornare il contenuto del campo di input di testo quando l'utente [`TMP_KeyboardInputField`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.TMP_KeyboardInputField) [`UI_KeyboardInputField`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.UI_KeyboardInputField) immette il testo.</span><span class="sxs-lookup"><span data-stu-id="667bc-114">The [`TMP_KeyboardInputField`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.TMP_KeyboardInputField) and [`UI_KeyboardInputField`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.UI_KeyboardInputField) classes are components that can be added to text input fields to automatically invoke the system keyboard when clicked and update the text input field contents as the user enters text.</span></span>

### <a name="how-to-use"></a><span data-ttu-id="667bc-115">Uso</span><span class="sxs-lookup"><span data-stu-id="667bc-115">How to use</span></span>

1. <span data-ttu-id="667bc-116">Creare un campo di input per UnityUI o TextMeshPro.</span><span class="sxs-lookup"><span data-stu-id="667bc-116">Create an input field for either UnityUI or TextMeshPro.</span></span>
2. <span data-ttu-id="667bc-117">Aggiungere il componente [`TMP_KeyboardInputField`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.TMP_KeyboardInputField) o [`UI_KeyboardInputField`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.UI_KeyboardInputField) corrispondente all'oggetto gioco del campo di input.</span><span class="sxs-lookup"><span data-stu-id="667bc-117">Add the corresponding [`TMP_KeyboardInputField`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.TMP_KeyboardInputField) or [`UI_KeyboardInputField`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.UI_KeyboardInputField) component to the input field game object.</span></span>

<span data-ttu-id="667bc-118">I prefab sia per i campi di input UnityUI che per i campi di input TextMeshPro (TMPro) sono disponibili in "Assets\MRTK\Experimental\MixedRealityKeyboard\Prefabs"</span><span class="sxs-lookup"><span data-stu-id="667bc-118">Prefabs for both UnityUI input fields and TextMeshPro (TMPro) input fields are available at "Assets\MRTK\Experimental\MixedRealityKeyboard\Prefabs"</span></span>

<span data-ttu-id="667bc-119">Un esempio di come usare TMP_KeyboardInputField e UI_KeyboardInputField è "Assets\MRTK\Examples\Experimental\MixedRealityKeyboard\Scenes\MixedRealityKeyboardExample.unity"</span><span class="sxs-lookup"><span data-stu-id="667bc-119">An example of how the to use TMP_KeyboardInputField and UI_KeyboardInputField is at "Assets\MRTK\Examples\Experimental\MixedRealityKeyboard\Scenes\MixedRealityKeyboardExample.unity"</span></span>
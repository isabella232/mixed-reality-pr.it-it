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
# <a name="mixed-reality-and-hololens-keyboard-helper-classes"></a>Realtà mista e HoloLens helper tastiera

MRTK fornisce diversi componenti helper sperimentali per facilitare l'avvio e la lettura di testo dalla [tastiera di sistema.](../ux-building-blocks/system-keyboard.md)

Si noti che la tastiera di sistema si comporterà in base alle funzionalità della piattaforma di destinazione, ad esempio la tastiera in HoloLens 2 supporterebbe le interazioni dirette con la mano, mentre la tastiera di HoloLens (prima generazione) supporterebbe GGV<sup>[1.](/windows/mixed-reality/gaze)</sup> Inoltre, la tastiera di sistema non verrà visualizzato quando si esegue la comunicazione remota di [Unity](../tools/holographic-remoting.md) dall'editor a un HoloLens.

## <a name="mixedrealitykeyboard"></a>MixedRealityKeyboard

[`MixedRealityKeyboard`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.MixedRealityKeyboard) è un componente che fornisce metodi per avviare e chiudere una tastiera di sistema, nonché per interagire con il testo immesso dalla tastiera.  

### <a name="how-to-use"></a>Uso

1. Collegare il [`MixedRealityKeyboard`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.MixedRealityKeyboard) componente a qualsiasi oggetto.
2. Chiamare per mostrare e nascondere la tastiera e gestire gli eventi , e da gestire quando la tastiera viene visualizzata, nascosta e quando viene `ShowKeyboard(string text = "", bool multiLine = false)` `HideKeyboard()` premuto il tasto `OnShowKeyboard` `OnHideKeyboard` `OnCommitText` INVIO.

## <a name="input-fields-tmp_keyboardinputfield-and-ui_keyboardinputfield"></a>Campi di TMP_KeyboardInputField e UI_KeyboardInputField

Le classi e sono componenti che possono essere aggiunti ai campi di input di testo per richiamare automaticamente la tastiera di sistema quando si fa clic e aggiornare il contenuto del campo di input di testo quando l'utente [`TMP_KeyboardInputField`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.TMP_KeyboardInputField) [`UI_KeyboardInputField`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.UI_KeyboardInputField) immette il testo.

### <a name="how-to-use"></a>Uso

1. Creare un campo di input per UnityUI o TextMeshPro.
2. Aggiungere il componente [`TMP_KeyboardInputField`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.TMP_KeyboardInputField) o [`UI_KeyboardInputField`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.UI_KeyboardInputField) corrispondente all'oggetto gioco del campo di input.

I prefab sia per i campi di input UnityUI che per i campi di input TextMeshPro (TMPro) sono disponibili in "Assets\MRTK\Experimental\MixedRealityKeyboard\Prefabs"

Un esempio di come usare TMP_KeyboardInputField e UI_KeyboardInputField è "Assets\MRTK\Examples\Experimental\MixedRealityKeyboard\Scenes\MixedRealityKeyboardExample.unity"
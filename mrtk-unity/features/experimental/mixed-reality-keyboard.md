---
title: Tastiera di realtà mista
description: descrizione su Come usare la tastiera di realtà mista
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realtà mista, sviluppo, MRTK,
ms.openlocfilehash: 9fa81db9a71f1d0ce32bdd80a123eb072fc26fc5
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143391"
---
# <a name="mixed-reality-and-hololens-keyboard-helper-classes"></a>Classi helper della tastiera Di realtà mista e HoloLens

MRTK fornisce diversi componenti helper sperimentali per facilitare l'avvio e la lettura di testo dalla [tastiera di sistema.](../ux-building-blocks/system-keyboard.md)

Si noti che la tastiera di sistema si comporterà in base alle funzionalità della piattaforma di destinazione, ad esempio la tastiera su HoloLens 2 supporterebbe le interazioni di mano diretta, mentre la tastiera in HoloLens (prima generazione) supporterebbe GGV<sup>[1.](/windows/mixed-reality/gaze)</sup> Inoltre, la tastiera di sistema non verrà mostrata quando si esegue [Unity Remoting](../tools/holographic-remoting.md) dall'editor a un holoLens.

## <a name="mixedrealitykeyboard"></a>MixedRealityKeyboard

[`MixedRealityKeyboard`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.MixedRealityKeyboard) è un componente che fornisce metodi per l'avvio e la chiusura di una tastiera di sistema, nonché l'interazione con il testo immesso dalla tastiera.  

### <a name="how-to-use"></a>Uso

1. Associare [`MixedRealityKeyboard`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.MixedRealityKeyboard) il componente a qualsiasi oggetto.
2. Chiamare per visualizzare e nascondere la tastiera e gestire gli eventi e da gestire quando la tastiera viene visualizzata, nascosta e quando viene premuto `Show()` `Hide()` il tasto `OnShowKeyboard` `OnHideKeyboard` `OnCommitText` INVIO.

## <a name="input-fields-tmp_keyboardinputfield-and-ui_keyboardinputfield"></a>Campi di TMP_KeyboardInputField e UI_KeyboardInputField

Le classi e sono componenti che possono essere aggiunti ai campi di input di testo per richiamare automaticamente la tastiera di sistema quando si fa clic e aggiornare il contenuto del campo di input di testo quando l'utente [`TMP_KeyboardInputField`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.TMP_KeyboardInputField) [`UI_KeyboardInputField`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.UI_KeyboardInputField) immette testo.

### <a name="how-to-use"></a>Uso

1. Creare un campo di input per UnityUI o TextMeshPro.
2. Aggiungere il componente [`TMP_KeyboardInputField`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.TMP_KeyboardInputField) o [`UI_KeyboardInputField`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.UI_KeyboardInputField) corrispondente all'oggetto di gioco del campo di input.

I prefab per i campi di input unityUI e i campi di input TextMeshPro (TMPro) sono disponibili in "Assets\MRTK\Experimental\MixedRealityKeyboard\Prefabs"

Un esempio di come usare TMP_KeyboardInputField e UI_KeyboardInputField è in "Assets\MRTK\Examples\Experimental\MixedRealityKeyboard\Scenes\MixedRealityKeyboardExample.unity"
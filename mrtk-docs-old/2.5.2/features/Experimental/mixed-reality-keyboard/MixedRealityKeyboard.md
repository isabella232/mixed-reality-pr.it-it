---
title: README_MixedRealityKeyboard
description: Descrizione su come usare la tastiera a realtà mista
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: d470c886bbb7d94baf6dc7720ed1809298d80782
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/03/2021
ms.locfileid: "101782732"
---
# <a name="mixed-reality-and-hololens-keyboard-helper-classes"></a>Realtà mista e classi helper della tastiera HoloLens

In MRTK sono disponibili diversi componenti Helper sperimentali che consentono di avviare e leggere testo dalla [tastiera di sistema](../../SystemKeyboard.md).

Si noti che la tastiera di sistema si comporterà in base alle funzionalità della piattaforma di destinazione, ad esempio la tastiera in HoloLens 2 supporterà le interazioni con la mano diretta, mentre la tastiera su HoloLens (1a generazione) supporterà GGV<sup>[1](https://docs.microsoft.com/windows/mixed-reality/gaze)</sup>. Inoltre, la tastiera di sistema non viene visualizzata quando si esegue la [comunicazione remota di Unity](../../tools/HolographicRemoting.md) dall'editor a un HoloLens.

## <a name="mixedrealitykeyboard"></a>MixedRealityKeyboard

[`MixedRealityKeyboard`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.MixedRealityKeyboard) è un componente che fornisce metodi per l'avvio e la chiusura di una tastiera di sistema, nonché per l'interazione con il testo immesso dalla tastiera.  

### <a name="how-to-use"></a>Uso

1. Alleghi il [`MixedRealityKeyboard`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.MixedRealityKeyboard) componente a qualsiasi oggetto.
2. Chiamare `Show()` `Hide()` per visualizzare e nascondere la tastiera e gestire gli `OnShowKeyboard` eventi, `OnHideKeyboard` e `OnCommitText` per gestire quando la tastiera viene visualizzata, nascosta e quando viene premuto il tasto INVIO.

## <a name="input-fields-tmp_keyboardinputfield-and-ui_keyboardinputfield"></a>Campi di input TMP_KeyboardInputField e UI_KeyboardInputField

Le [`TMP_KeyboardInputField`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.TMP_KeyboardInputField) [`UI_KeyboardInputField`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.UI_KeyboardInputField) classi e sono componenti che possono essere aggiunti ai campi di input di testo per richiamare automaticamente la tastiera di sistema quando si fa clic e aggiornare il contenuto del campo di input di testo quando l'utente immette il testo.

### <a name="how-to-use"></a>Uso

1. Creare un campo di input sia per UnityUI che per TextMeshPro.
2. Aggiungere il [`TMP_KeyboardInputField`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.TMP_KeyboardInputField) componente o corrispondente [`UI_KeyboardInputField`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.UI_KeyboardInputField) all'oggetto gioco campo di input.

I prefabbricati per i campi di input UnityUI e TextMeshPro (TMPro) sono disponibili in "Assets\MRTK\Experimental\MixedRealityKeyboard\Prefabs"

Un esempio di come usare TMP_KeyboardInputField e UI_KeyboardInputField è "Assets\MRTK\Examples\Experimental\MixedRealityKeyboard\Scenes\MixedRealityKeyboardExample.unity"

---
title: SystemKeyBoard
description: Panoramica della lavagna delle chiavi di sistema in MRTK
author: maxwang-ms
ms.author: wangmax
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, tastiera di sistema,
ms.openlocfilehash: cd2fc0698194e4b33c469a27f1509c201434ab84
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/03/2021
ms.locfileid: "101781939"
---
# <a name="system-keyboard"></a>Tastiera di sistema

![Tastiera di sistema](../images/system-keyboard/MRTK_SystemKeyboard_Main.png)

Un'applicazione Unity può richiamare la tastiera di sistema in qualsiasi momento. Si noti che la tastiera di sistema si comporterà in base alle funzionalità della piattaforma di destinazione, ad esempio la tastiera in HoloLens 2 supporterà le interazioni con la mano diretta, mentre la tastiera su HoloLens (1a generazione) supporterà GGV (sguardi, movimenti e voce)<sup>[1](https://docs.microsoft.com/windows/mixed-reality/gaze)</sup>. Inoltre, la tastiera di sistema non viene visualizzata quando si esegue la [comunicazione remota di Unity](../tools/holographic-remoting.md) dall'editor a un HoloLens.

## <a name="how-to-invoke-the-system-keyboard"></a>Come richiamare la tastiera di sistema

```c#
public TouchScreenKeyboard keyboard;

...

public void OpenSystemKeyboard()
{
    keyboard = TouchScreenKeyboard.Open("", TouchScreenKeyboardType.Default, false, false, false, false);
}
```

## <a name="how-to-read-the-input"></a>Come leggere l'input

```c#
public TouchScreenKeyboard keyboard;

...

private void Update()
{
    if (keyboard != null)
    {
        keyboardText = keyboard.text;
        // Do stuff with keyboardText
    }
}
```

## <a name="system-keyboard-example"></a>Esempio di tastiera di sistema

È possibile vedere un semplice esempio di come visualizzare la tastiera di sistema in `MixedRealityKeyboard.cs` (assets/MRTK/SDK/Experimental/Features/UX/MixedRealityKeyboard. cs)

## <a name="see-also"></a>Vedere anche

- [Classi helper della tastiera a realtà mista](../experimental/mixed-reality-keyboard.md)

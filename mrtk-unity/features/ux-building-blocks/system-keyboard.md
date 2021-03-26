---
title: SystemKeyBoard
description: Panoramica della lavagna delle chiavi di sistema in MRTK
author: maxwang-ms
ms.author: wangmax
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, tastiera di sistema,
ms.openlocfilehash: 921527e53ce5bfc7b27cc6199abdf6759272c1b6
ms.sourcegitcommit: ac315c1d35f2b9c431e79bc3f1212215301bb867
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105550371"
---
# <a name="system-keyboard"></a>Tastiera di sistema

![Tastiera di sistema](../images/system-keyboard/MRTK_SystemKeyboard_Main.png)

Un'applicazione Unity può richiamare la tastiera di sistema in qualsiasi momento. Si noti che la tastiera di sistema si comporterà in base alle funzionalità della piattaforma di destinazione, ad esempio la tastiera in HoloLens 2 supporterà le interazioni con la mano diretta, mentre la tastiera su HoloLens (1a generazione) supporterà GGV (sguardi, movimenti e voce)<sup>[1](/windows/mixed-reality/gaze)</sup>. Inoltre, la tastiera di sistema non viene visualizzata quando si esegue la [comunicazione remota di Unity](../tools/holographic-remoting.md) dall'editor a un HoloLens.

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
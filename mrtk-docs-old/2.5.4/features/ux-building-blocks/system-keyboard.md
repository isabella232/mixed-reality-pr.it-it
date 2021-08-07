---
title: SystemKeyBoard
description: Panoramica della scheda delle chiavi di sistema in MRTK
author: maxwang-ms
ms.author: wangmax
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, tastiera di sistema,
ms.openlocfilehash: fed51da13a58f61c3b1d1ea9e99a23b124da81c6268d5da64e98e986f138a583
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115189239"
---
# <a name="system-keyboard"></a>Tastiera di sistema

![Tastiera di sistema](../images/system-keyboard/MRTK_SystemKeyboard_Main.png)

Un'applicazione Unity può richiamare la tastiera di sistema in qualsiasi momento. Si noti che la tastiera di sistema si comporterà in base alle funzionalità della piattaforma di destinazione, ad esempio la tastiera su HoloLens 2 supporterebbe le interazioni di mano diretta, mentre la tastiera in HoloLens (prima generazione) supporterebbe GGV (sguardo fisso, movimento e voce)<sup>[1.](https://docs.microsoft.com/windows/mixed-reality/gaze)</sup> Inoltre, la tastiera di sistema non verrà mostrata quando si esegue [Unity Remoting](../tools/holographic-remoting.md) dall'editor a un HoloLens.

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

È possibile visualizzare un semplice esempio di come visualizzare la tastiera di sistema in `MixedRealityKeyboard.cs` (Assets/MRTK/SDK/Experimental/Features/UX/MixedRealityKeyboard.cs)

## <a name="see-also"></a>Vedere anche

- [Classi helper tastiera di realtà mista](../experimental/mixed-reality-keyboard.md)

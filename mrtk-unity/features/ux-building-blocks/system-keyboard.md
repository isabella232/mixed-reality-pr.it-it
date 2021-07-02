---
title: Tastiera di sistema
description: Panoramica della scheda delle chiavi di sistema in MRTK
author: maxwang-ms
ms.author: wangmax
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, tastiera di sistema,
ms.openlocfilehash: 9b1db512a1a4e27a2c41e8e8b5752200c461ee6e
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176489"
---
# <a name="system-keyboard"></a><span data-ttu-id="dcd06-104">Tastiera di sistema</span><span class="sxs-lookup"><span data-stu-id="dcd06-104">System keyboard</span></span>

![Tastiera di sistema](../images/system-keyboard/MRTK_SystemKeyboard_Main.png)

<span data-ttu-id="dcd06-106">Un'applicazione Unity può richiamare la tastiera di sistema in qualsiasi momento.</span><span class="sxs-lookup"><span data-stu-id="dcd06-106">A Unity application can invoke the system keyboard at any time.</span></span> <span data-ttu-id="dcd06-107">Si noti che la tastiera di sistema si comporterà in base alle funzionalità della piattaforma di destinazione, ad esempio la tastiera su HoloLens 2 supporterebbe le interazioni di mano diretta, mentre la tastiera in HoloLens (prima generazione) supporterebbe GGV (sguardo fisso, movimento e voce)<sup>[1.](/windows/mixed-reality/gaze)</sup></span><span class="sxs-lookup"><span data-stu-id="dcd06-107">Note that the system keyboard will behave according to the target platform's capabilities, for example the keyboard on HoloLens 2 would support direct hand interactions, while the keyboard on HoloLens (1st gen) would support GGV (Gaze, Gesture, and Voice)<sup>[1](/windows/mixed-reality/gaze)</sup>.</span></span> <span data-ttu-id="dcd06-108">Inoltre, la tastiera di sistema non verrà mostrata quando si esegue [Unity Remoting](../tools/holographic-remoting.md) dall'editor a un HoloLens.</span><span class="sxs-lookup"><span data-stu-id="dcd06-108">Additionally, the system keyboard will not show up when performing [Unity Remoting](../tools/holographic-remoting.md) from the editor to a HoloLens.</span></span>

## <a name="how-to-invoke-the-system-keyboard"></a><span data-ttu-id="dcd06-109">Come richiamare la tastiera di sistema</span><span class="sxs-lookup"><span data-stu-id="dcd06-109">How to invoke the system keyboard</span></span>

```c#
public TouchScreenKeyboard keyboard;

...

public void OpenSystemKeyboard()
{
    keyboard = TouchScreenKeyboard.Open("", TouchScreenKeyboardType.Default, false, false, false, false);
}
```

## <a name="how-to-read-the-input"></a><span data-ttu-id="dcd06-110">Come leggere l'input</span><span class="sxs-lookup"><span data-stu-id="dcd06-110">How to read the input</span></span>

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

## <a name="system-keyboard-example"></a><span data-ttu-id="dcd06-111">Esempio di tastiera di sistema</span><span class="sxs-lookup"><span data-stu-id="dcd06-111">System keyboard example</span></span>

<span data-ttu-id="dcd06-112">È possibile visualizzare un semplice esempio di come visualizzare la tastiera di sistema in `MixedRealityKeyboard.cs` (Assets/MRTK/SDK/Experimental/Features/UX/MixedRealityKeyboard.cs)</span><span class="sxs-lookup"><span data-stu-id="dcd06-112">You can see a simple example of how to bring up system keyboard in `MixedRealityKeyboard.cs` (Assets/MRTK/SDK/Experimental/Features/UX/MixedRealityKeyboard.cs)</span></span>

## <a name="see-also"></a><span data-ttu-id="dcd06-113">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="dcd06-113">See Also</span></span>

- [<span data-ttu-id="dcd06-114">Classi helper tastiera di realtà mista</span><span class="sxs-lookup"><span data-stu-id="dcd06-114">Mixed Reality Keyboard Helper Classes</span></span>](../experimental/mixed-reality-keyboard.md)

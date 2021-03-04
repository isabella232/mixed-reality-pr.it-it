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
# <a name="system-keyboard"></a><span data-ttu-id="39de7-104">Tastiera di sistema</span><span class="sxs-lookup"><span data-stu-id="39de7-104">System keyboard</span></span>

![Tastiera di sistema](../images/system-keyboard/MRTK_SystemKeyboard_Main.png)

<span data-ttu-id="39de7-106">Un'applicazione Unity può richiamare la tastiera di sistema in qualsiasi momento.</span><span class="sxs-lookup"><span data-stu-id="39de7-106">A Unity application can invoke the system keyboard at any time.</span></span> <span data-ttu-id="39de7-107">Si noti che la tastiera di sistema si comporterà in base alle funzionalità della piattaforma di destinazione, ad esempio la tastiera in HoloLens 2 supporterà le interazioni con la mano diretta, mentre la tastiera su HoloLens (1a generazione) supporterà GGV (sguardi, movimenti e voce)<sup>[1](https://docs.microsoft.com/windows/mixed-reality/gaze)</sup>.</span><span class="sxs-lookup"><span data-stu-id="39de7-107">Note that the system keyboard will behave according to the target platform's capabilities, for example the keyboard on HoloLens 2 would support direct hand interactions, while the keyboard on HoloLens (1st gen) would support GGV (Gaze, Gesture, and Voice)<sup>[1](https://docs.microsoft.com/windows/mixed-reality/gaze)</sup>.</span></span> <span data-ttu-id="39de7-108">Inoltre, la tastiera di sistema non viene visualizzata quando si esegue la [comunicazione remota di Unity](../tools/holographic-remoting.md) dall'editor a un HoloLens.</span><span class="sxs-lookup"><span data-stu-id="39de7-108">Additionally, the system keyboard will not show up when performing [Unity Remoting](../tools/holographic-remoting.md) from the editor to a HoloLens.</span></span>

## <a name="how-to-invoke-the-system-keyboard"></a><span data-ttu-id="39de7-109">Come richiamare la tastiera di sistema</span><span class="sxs-lookup"><span data-stu-id="39de7-109">How to invoke the system keyboard</span></span>

```c#
public TouchScreenKeyboard keyboard;

...

public void OpenSystemKeyboard()
{
    keyboard = TouchScreenKeyboard.Open("", TouchScreenKeyboardType.Default, false, false, false, false);
}
```

## <a name="how-to-read-the-input"></a><span data-ttu-id="39de7-110">Come leggere l'input</span><span class="sxs-lookup"><span data-stu-id="39de7-110">How to read the input</span></span>

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

## <a name="system-keyboard-example"></a><span data-ttu-id="39de7-111">Esempio di tastiera di sistema</span><span class="sxs-lookup"><span data-stu-id="39de7-111">System keyboard example</span></span>

<span data-ttu-id="39de7-112">È possibile vedere un semplice esempio di come visualizzare la tastiera di sistema in `MixedRealityKeyboard.cs` (assets/MRTK/SDK/Experimental/Features/UX/MixedRealityKeyboard. cs)</span><span class="sxs-lookup"><span data-stu-id="39de7-112">You can see a simple example of how to bring up system keyboard in `MixedRealityKeyboard.cs` (Assets/MRTK/SDK/Experimental/Features/UX/MixedRealityKeyboard.cs)</span></span>

## <a name="see-also"></a><span data-ttu-id="39de7-113">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="39de7-113">See Also</span></span>

- [<span data-ttu-id="39de7-114">Classi helper della tastiera a realtà mista</span><span class="sxs-lookup"><span data-stu-id="39de7-114">Mixed Reality Keyboard Helper Classes</span></span>](../experimental/mixed-reality-keyboard.md)

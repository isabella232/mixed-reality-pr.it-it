---
title: README_SystemKeyBoard
description: Panoramica della lavagna delle chiavi di sistema in MRTK
author: maxwang-ms
ms.author: wangmax
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, tastiera di sistema,
ms.openlocfilehash: 71aadbd463ba245d5cadf5a8698b9787954beabf
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2021
ms.locfileid: "104694888"
---
# <a name="system-keyboard"></a><span data-ttu-id="eadfb-104">Tastiera di sistema</span><span class="sxs-lookup"><span data-stu-id="eadfb-104">System keyboard</span></span>

![Tastiera di sistema](Images/SystemKeyboard/MRTK_SystemKeyboard_Main.png)

<span data-ttu-id="eadfb-106">Un'applicazione Unity può richiamare la tastiera di sistema in qualsiasi momento.</span><span class="sxs-lookup"><span data-stu-id="eadfb-106">A Unity application can invoke the system keyboard at any time.</span></span> <span data-ttu-id="eadfb-107">Si noti che la tastiera di sistema si comporterà in base alle funzionalità della piattaforma di destinazione, ad esempio la tastiera in HoloLens 2 supporterà le interazioni con la mano diretta, mentre la tastiera su HoloLens (1a generazione) supporterà GGV (sguardi, movimenti e voce)<sup>[1](https://docs.microsoft.com/windows/mixed-reality/gaze)</sup>.</span><span class="sxs-lookup"><span data-stu-id="eadfb-107">Note that the system keyboard will behave according to the target platform's capabilities, for example the keyboard on HoloLens 2 would support direct hand interactions, while the keyboard on HoloLens (1st gen) would support GGV (Gaze, Gesture, and Voice)<sup>[1](https://docs.microsoft.com/windows/mixed-reality/gaze)</sup>.</span></span> <span data-ttu-id="eadfb-108">Inoltre, la tastiera di sistema non viene visualizzata quando si esegue la [comunicazione remota di Unity](Tools/HolographicRemoting.md) dall'editor a un HoloLens.</span><span class="sxs-lookup"><span data-stu-id="eadfb-108">Additionally, the system keyboard will not show up when performing [Unity Remoting](Tools/HolographicRemoting.md) from the editor to a HoloLens.</span></span>

## <a name="how-to-invoke-the-system-keyboard"></a><span data-ttu-id="eadfb-109">Come richiamare la tastiera di sistema</span><span class="sxs-lookup"><span data-stu-id="eadfb-109">How to invoke the system keyboard</span></span>

```c#
public TouchScreenKeyboard keyboard;

...

public void OpenSystemKeyboard()
{
    keyboard = TouchScreenKeyboard.Open("", TouchScreenKeyboardType.Default, false, false, false, false);
}
```

## <a name="how-to-read-the-input"></a><span data-ttu-id="eadfb-110">Come leggere l'input</span><span class="sxs-lookup"><span data-stu-id="eadfb-110">How to read the input</span></span>

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

## <a name="system-keyboard-example"></a><span data-ttu-id="eadfb-111">Esempio di tastiera di sistema</span><span class="sxs-lookup"><span data-stu-id="eadfb-111">System keyboard example</span></span>

<span data-ttu-id="eadfb-112">È possibile vedere un semplice esempio di come visualizzare la tastiera di sistema in `MixedRealityKeyboard.cs` (assets/MRTK/SDK/Experimental/Features/UX/MixedRealityKeyboard. cs)</span><span class="sxs-lookup"><span data-stu-id="eadfb-112">You can see a simple example of how to bring up system keyboard in `MixedRealityKeyboard.cs` (Assets/MRTK/SDK/Experimental/Features/UX/MixedRealityKeyboard.cs)</span></span>

## <a name="see-also"></a><span data-ttu-id="eadfb-113">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="eadfb-113">See Also</span></span>

- [<span data-ttu-id="eadfb-114">Classi helper della tastiera a realtà mista</span><span class="sxs-lookup"><span data-stu-id="eadfb-114">Mixed Reality Keyboard Helper Classes</span></span>](Experimental/MixedRealityKeyboard/README_MixedRealityKeyboard.md)

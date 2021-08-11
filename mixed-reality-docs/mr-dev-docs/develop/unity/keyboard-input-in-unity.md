---
title: Input da tastiera in Unity
description: Unity fornisce la classe TouchScreenKeyboard per accettare l'input da tastiera quando non è disponibile una tastiera fisica.
author: MaxWang-MS
ms.author: wangmax
ms.date: 03/30/2021
ms.topic: article
keywords: tastiera, input, unity, touchscreenkeyboard, visore di realtà mista, visore windows mixed reality, visore per realtà virtuale, visore HoloLens, HoloLens 2
ms.openlocfilehash: a7bd392036ca548fdd1f25581c8fc1910308909253f9c8df763e2039a32d3e9a
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115203853"
---
# <a name="keyboard-input-in-unity"></a>Input da tastiera in Unity

**Spazio dei nomi:** *UnityEngine*<br>
 **Tipo:** *[TouchScreenKeyboard](https://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.html)*

Sebbene HoloLens supporti molte forme di input, Bluetooth tastiere, la maggior parte delle applicazioni non può presupporre che tutti gli utenti avranno una tastiera fisica disponibile. Se l'applicazione richiede l'input di testo, è necessario inserire una qualche forma di tastiera su schermo.

Unity fornisce la *[classe TouchScreenKeyboard](https://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.html)* per accettare l'input da tastiera quando non è disponibile una tastiera fisica.

## <a name="hololens-system-keyboard-behavior-in-unity"></a>HoloLens comportamento della tastiera di sistema in Unity

In HoloLens, *TouchScreenKeyboard* sfrutta la tastiera su schermo del sistema e si sovrappone direttamente alla visualizzazione volumetrica dell'applicazione MR. L'esperienza è simile all'uso della tastiera nelle app predefinite di HoloLens. Si noti che la tastiera di sistema si comporterà in base alle funzionalità della piattaforma di destinazione, ad esempio la tastiera su HoloLens 2 supporterebbe le interazioni dirette con la mano, mentre la tastiera in HoloLens (prima generazione) supporterebbe GGV (sguardo fisso, movimento e voce). Inoltre, la tastiera di sistema non verrà visualizzato quando si esegue Unity Remoting dall'editor a un HoloLens.

## <a name="using-the-system-keyboard-in-your-unity-app"></a>Uso della tastiera di sistema nell'app Unity

### <a name="declare-the-keyboard"></a>Dichiarare la tastiera

Nella classe dichiarare una variabile per archiviare *TouchScreenKeyboard* e una variabile per contenere la stringa restituita dalla tastiera.

```cs
UnityEngine.TouchScreenKeyboard keyboard;
public static string keyboardText = "";
```

### <a name="invoke-the-keyboard"></a>Richiamare la tastiera

Quando si verifica un evento che richiede l'input da tastiera, usare quanto segue per visualizzare la tastiera.

```cs
keyboard = TouchScreenKeyboard.Open("text to edit");
```

È possibile usare parametri aggiuntivi passati nella funzione per controllare il comportamento della tastiera, ad esempio impostando il testo segnaposto o supportando `TouchScreenKeyboard.Open` la correzione automatica. Per l'elenco completo dei parametri, vedere la documentazione [di Unity.](https://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.Open.html)

### <a name="retrieve-typed-contents"></a>Recuperare il contenuto tipiato

Il contenuto può essere semplicemente recuperato chiamando `keyboard.text` . È possibile recuperare il contenuto per frame o solo quando la tastiera è chiusa.

```cs
keyboardText = keyboard.text;
```

## <a name="alternative-keyboard-options"></a>Opzioni alternative della tastiera

Oltre a usare direttamente la classe *TouchScreenKeyboard,* è anche possibile ottenere l'input dell'utente usando il campo di *input* dell'interfaccia utente di Unity o il campo di *input TextMeshPro.* È inoltre disponibile un'implementazione basata su *TouchScreenKeyboard* nella [scena HandInteractionExamples](/windows/mixed-reality/mrtk-unity/features/example-scenes/hand-interaction-examples) di [MRTK](/windows/mixed-reality/mrtk-unity) (sul lato sinistro è presente un esempio di interazione da tastiera).

## <a name="next-development-checkpoint"></a>Successivo checkpoint di sviluppo

Se si sta seguendo il percorso di sviluppo di Unity che è stato strutturato, si stanno esplorando le API e le funzionalità della piattaforma di realtà mista. Da qui è possibile continuare a [qualsiasi](unity-development-overview.md#3-advanced-features) argomento o passare direttamente alla distribuzione dell'app in un dispositivo o un emulatore.

> [!div class="nextstepaction"]
> [Distribuire in HoloLens o Windows Mixed Reality visori immersive](../platform-capabilities-and-apis/using-visual-studio.md)

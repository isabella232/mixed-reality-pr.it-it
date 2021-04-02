---
title: Input da tastiera in Unity
description: Unity fornisce la classe TouchScreenKeyboard per accettare l'input da tastiera quando non è disponibile una tastiera fisica.
author: MaxWang-MS
ms.author: wangmax
ms.date: 03/30/2021
ms.topic: article
keywords: tastiera, input, Unity, touchscreenkeyboard, cuffie per realtà mista, cuffia di realtà mista di Windows, cuffia virtuale reale, HoloLens, HoloLens 2
ms.openlocfilehash: 398a7c57dc701fc848fe9091949b45b2c1796987
ms.sourcegitcommit: e5bd72d8b92976a6590e0f59706a88e66374934c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/31/2021
ms.locfileid: "106098273"
---
# <a name="keyboard-input-in-unity"></a>Input da tastiera in Unity

**Spazio dei nomi:** *UnityEngine*<br>
 **Tipo**: *[TouchScreenKeyboard](https://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.html)*

Sebbene HoloLens supporti molte forme di input, incluse le tastiere Bluetooth, la maggior parte delle applicazioni non può presupporre che tutti gli utenti dispongano di una tastiera fisica disponibile. Se l'applicazione richiede un input di testo, è necessario specificare una qualsiasi forma di tastiera sullo schermo.

Unity fornisce la classe *[TouchScreenKeyboard](https://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.html)* per accettare l'input da tastiera quando non è disponibile una tastiera fisica.

## <a name="hololens-system-keyboard-behavior-in-unity"></a>Comportamento della tastiera di sistema HoloLens in Unity

In HoloLens, *TouchScreenKeyboard* sfrutta la tastiera su schermo del sistema e sovrappone direttamente alla visualizzazione volumetrica dell'applicazione Mr. L'esperienza è simile all'uso della tastiera nelle app predefinite di HoloLens. Si noti che la tastiera di sistema si comporterà in base alle funzionalità della piattaforma di destinazione, ad esempio la tastiera in HoloLens 2 supporterà le interazioni con la mano diretta, mentre la tastiera su HoloLens (1a generazione) supporterà GGV (sguardi, movimenti e voce). Inoltre, la tastiera di sistema non viene visualizzata quando si esegue la comunicazione remota di Unity dall'editor a un HoloLens.

## <a name="using-the-system-keyboard-in-your-unity-app"></a>Uso della tastiera di sistema nell'app Unity

### <a name="declare-the-keyboard"></a>Dichiarare la tastiera

Nella classe dichiarare una variabile per archiviare *TouchScreenKeyboard* e una variabile per contenere la stringa restituita dalla tastiera.

```cs
UnityEngine.TouchScreenKeyboard keyboard;
public static string keyboardText = "";
```

### <a name="invoke-the-keyboard"></a>Richiama la tastiera

Quando si verifica un evento che richiede l'input da tastiera, utilizzare il comando seguente per visualizzare la tastiera.

```cs
keyboard = TouchScreenKeyboard.Open("text to edit");
```

È possibile usare parametri aggiuntivi passati nella `TouchScreenKeyboard.Open` funzione per controllare il comportamento della tastiera, ad esempio l'impostazione del testo segnaposto o il supporto della correzione automatica. Per l'elenco completo dei parametri, vedere la [documentazione di Unity](https://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.Open.html).

### <a name="retrieve-typed-contents"></a>Recupera contenuto tipizzato

Il contenuto può essere semplicemente recuperato chiamando `keyboard.text` . È possibile recuperare il contenuto per frame o solo quando la tastiera viene chiusa.

```cs
keyboardText = keyboard.text;
```

## <a name="alternative-keyboard-options"></a>Opzioni di tastiera alternative

Oltre a usare direttamente la classe *TouchScreenKeyboard* , è possibile ottenere l'input dell'utente anche usando il *campo di input dell'interfaccia* utente di Unity o il campo di *input TextMeshPro*. Inoltre, esiste un'implementazione basata su *TouchScreenKeyboard* nella [scena HandInteractionExamples](/windows/mixed-reality/mrtk-unity/features/example-scenes/hand-interaction-examples) di [MRTK](/windows/mixed-reality/mrtk-unity) (è presente un esempio di interazione da tastiera sul lato sinistro).

## <a name="next-development-checkpoint"></a>Successivo checkpoint di sviluppo

Se si sta seguendo il percorso di sviluppo di Unity, è possibile esplorare le funzionalità e le API della piattaforma per la realtà mista. Da qui è possibile passare a qualsiasi [argomento](unity-development-overview.md#3-advanced-features) o passare direttamente alla distribuzione dell'app in un dispositivo o in un emulatore.

> [!div class="nextstepaction"]
> [Eseguire la distribuzione in HoloLens o in modalità mista di Windows per la realtà mista](../platform-capabilities-and-apis/using-visual-studio.md)

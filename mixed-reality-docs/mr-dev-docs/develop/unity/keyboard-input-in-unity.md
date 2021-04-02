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
# <a name="keyboard-input-in-unity"></a><span data-ttu-id="72a3c-104">Input da tastiera in Unity</span><span class="sxs-lookup"><span data-stu-id="72a3c-104">Keyboard input in Unity</span></span>

<span data-ttu-id="72a3c-105">**Spazio dei nomi:** *UnityEngine*</span><span class="sxs-lookup"><span data-stu-id="72a3c-105">**Namespace:** *UnityEngine*</span></span><br>
 <span data-ttu-id="72a3c-106">**Tipo**: *[TouchScreenKeyboard](https://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.html)*</span><span class="sxs-lookup"><span data-stu-id="72a3c-106">**Type**: *[TouchScreenKeyboard](https://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.html)*</span></span>

<span data-ttu-id="72a3c-107">Sebbene HoloLens supporti molte forme di input, incluse le tastiere Bluetooth, la maggior parte delle applicazioni non può presupporre che tutti gli utenti dispongano di una tastiera fisica disponibile.</span><span class="sxs-lookup"><span data-stu-id="72a3c-107">While HoloLens supports many forms of input including Bluetooth keyboards, most applications can't assume that all users will have a physical keyboard available.</span></span> <span data-ttu-id="72a3c-108">Se l'applicazione richiede un input di testo, è necessario specificare una qualsiasi forma di tastiera sullo schermo.</span><span class="sxs-lookup"><span data-stu-id="72a3c-108">If your application requires text input, some form of on-screen keyboard should be provided.</span></span>

<span data-ttu-id="72a3c-109">Unity fornisce la classe *[TouchScreenKeyboard](https://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.html)* per accettare l'input da tastiera quando non è disponibile una tastiera fisica.</span><span class="sxs-lookup"><span data-stu-id="72a3c-109">Unity provides the *[TouchScreenKeyboard](https://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.html)* class for accepting keyboard input when there's no physical keyboard available.</span></span>

## <a name="hololens-system-keyboard-behavior-in-unity"></a><span data-ttu-id="72a3c-110">Comportamento della tastiera di sistema HoloLens in Unity</span><span class="sxs-lookup"><span data-stu-id="72a3c-110">HoloLens system keyboard behavior in Unity</span></span>

<span data-ttu-id="72a3c-111">In HoloLens, *TouchScreenKeyboard* sfrutta la tastiera su schermo del sistema e sovrappone direttamente alla visualizzazione volumetrica dell'applicazione Mr.</span><span class="sxs-lookup"><span data-stu-id="72a3c-111">On HoloLens, the *TouchScreenKeyboard* leverages the system's on-screen keyboard and directly overlays on top of the volumetric view of your MR application.</span></span> <span data-ttu-id="72a3c-112">L'esperienza è simile all'uso della tastiera nelle app predefinite di HoloLens.</span><span class="sxs-lookup"><span data-stu-id="72a3c-112">The experience is similar to using keyboard in the built-in apps of HoloLens.</span></span> <span data-ttu-id="72a3c-113">Si noti che la tastiera di sistema si comporterà in base alle funzionalità della piattaforma di destinazione, ad esempio la tastiera in HoloLens 2 supporterà le interazioni con la mano diretta, mentre la tastiera su HoloLens (1a generazione) supporterà GGV (sguardi, movimenti e voce).</span><span class="sxs-lookup"><span data-stu-id="72a3c-113">Note that the system keyboard will behave according to the target platform's capabilities, for example the keyboard on HoloLens 2 would support direct hand interactions, while the keyboard on HoloLens (1st gen) would support GGV (Gaze, Gesture, and Voice).</span></span> <span data-ttu-id="72a3c-114">Inoltre, la tastiera di sistema non viene visualizzata quando si esegue la comunicazione remota di Unity dall'editor a un HoloLens.</span><span class="sxs-lookup"><span data-stu-id="72a3c-114">Additionally, the system keyboard will not show up when performing Unity Remoting from the editor to a HoloLens.</span></span>

## <a name="using-the-system-keyboard-in-your-unity-app"></a><span data-ttu-id="72a3c-115">Uso della tastiera di sistema nell'app Unity</span><span class="sxs-lookup"><span data-stu-id="72a3c-115">Using the system keyboard in your Unity app</span></span>

### <a name="declare-the-keyboard"></a><span data-ttu-id="72a3c-116">Dichiarare la tastiera</span><span class="sxs-lookup"><span data-stu-id="72a3c-116">Declare the keyboard</span></span>

<span data-ttu-id="72a3c-117">Nella classe dichiarare una variabile per archiviare *TouchScreenKeyboard* e una variabile per contenere la stringa restituita dalla tastiera.</span><span class="sxs-lookup"><span data-stu-id="72a3c-117">In the class, declare a variable to store the *TouchScreenKeyboard* and a variable to hold the string the keyboard returns.</span></span>

```cs
UnityEngine.TouchScreenKeyboard keyboard;
public static string keyboardText = "";
```

### <a name="invoke-the-keyboard"></a><span data-ttu-id="72a3c-118">Richiama la tastiera</span><span class="sxs-lookup"><span data-stu-id="72a3c-118">Invoke the keyboard</span></span>

<span data-ttu-id="72a3c-119">Quando si verifica un evento che richiede l'input da tastiera, utilizzare il comando seguente per visualizzare la tastiera.</span><span class="sxs-lookup"><span data-stu-id="72a3c-119">When an event occurs requesting keyboard input, use the following to show the keyboard.</span></span>

```cs
keyboard = TouchScreenKeyboard.Open("text to edit");
```

<span data-ttu-id="72a3c-120">È possibile usare parametri aggiuntivi passati nella `TouchScreenKeyboard.Open` funzione per controllare il comportamento della tastiera, ad esempio l'impostazione del testo segnaposto o il supporto della correzione automatica.</span><span class="sxs-lookup"><span data-stu-id="72a3c-120">You can use additional parameters passed into the `TouchScreenKeyboard.Open` function to control the behavior of the keyboard (e.g. setting placeholder text or supporting autocorrection).</span></span> <span data-ttu-id="72a3c-121">Per l'elenco completo dei parametri, vedere la [documentazione di Unity](https://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.Open.html).</span><span class="sxs-lookup"><span data-stu-id="72a3c-121">For the full list of parameters please refer to [Unity's documentation](https://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.Open.html).</span></span>

### <a name="retrieve-typed-contents"></a><span data-ttu-id="72a3c-122">Recupera contenuto tipizzato</span><span class="sxs-lookup"><span data-stu-id="72a3c-122">Retrieve typed contents</span></span>

<span data-ttu-id="72a3c-123">Il contenuto può essere semplicemente recuperato chiamando `keyboard.text` .</span><span class="sxs-lookup"><span data-stu-id="72a3c-123">The content can simply be retrieved by calling `keyboard.text`.</span></span> <span data-ttu-id="72a3c-124">È possibile recuperare il contenuto per frame o solo quando la tastiera viene chiusa.</span><span class="sxs-lookup"><span data-stu-id="72a3c-124">You may want to retrieve the content per frame or only when the keyboard is closed.</span></span>

```cs
keyboardText = keyboard.text;
```

## <a name="alternative-keyboard-options"></a><span data-ttu-id="72a3c-125">Opzioni di tastiera alternative</span><span class="sxs-lookup"><span data-stu-id="72a3c-125">Alternative keyboard options</span></span>

<span data-ttu-id="72a3c-126">Oltre a usare direttamente la classe *TouchScreenKeyboard* , è possibile ottenere l'input dell'utente anche usando il *campo di input dell'interfaccia* utente di Unity o il campo di *input TextMeshPro*.</span><span class="sxs-lookup"><span data-stu-id="72a3c-126">Besides using the *TouchScreenKeyboard* class directly, you can also get user input by using Unity's *UI Input Field* or *TextMeshPro Input Field*.</span></span> <span data-ttu-id="72a3c-127">Inoltre, esiste un'implementazione basata su *TouchScreenKeyboard* nella [scena HandInteractionExamples](/windows/mixed-reality/mrtk-unity/features/example-scenes/hand-interaction-examples) di [MRTK](/windows/mixed-reality/mrtk-unity) (è presente un esempio di interazione da tastiera sul lato sinistro).</span><span class="sxs-lookup"><span data-stu-id="72a3c-127">Additionally, there is an implementation based on *TouchScreenKeyboard* in the [HandInteractionExamples scene](/windows/mixed-reality/mrtk-unity/features/example-scenes/hand-interaction-examples) of [MRTK](/windows/mixed-reality/mrtk-unity) (there is a keyboard interaction sample on the left hand side).</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="72a3c-128">Successivo checkpoint di sviluppo</span><span class="sxs-lookup"><span data-stu-id="72a3c-128">Next Development Checkpoint</span></span>

<span data-ttu-id="72a3c-129">Se si sta seguendo il percorso di sviluppo di Unity, è possibile esplorare le funzionalità e le API della piattaforma per la realtà mista.</span><span class="sxs-lookup"><span data-stu-id="72a3c-129">If you're following the Unity development journey we've laid out, you're in the midst of exploring the Mixed Reality platform capabilities and APIs.</span></span> <span data-ttu-id="72a3c-130">Da qui è possibile passare a qualsiasi [argomento](unity-development-overview.md#3-advanced-features) o passare direttamente alla distribuzione dell'app in un dispositivo o in un emulatore.</span><span class="sxs-lookup"><span data-stu-id="72a3c-130">From here, you can continue to any [topic](unity-development-overview.md#3-advanced-features) or jump directly to deploying your app on a device or emulator.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="72a3c-131">Eseguire la distribuzione in HoloLens o in modalità mista di Windows per la realtà mista</span><span class="sxs-lookup"><span data-stu-id="72a3c-131">Deploy to HoloLens or Windows Mixed Reality immersive headsets</span></span>](../platform-capabilities-and-apis/using-visual-studio.md)

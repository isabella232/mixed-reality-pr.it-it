---
title: Input da tastiera in Unity
description: Unity fornisce la classe TouchScreenKeyboard per accettare l'input da tastiera quando non è disponibile una tastiera fisica.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: tastiera, input, Unity, touchscreenkeyboard, cuffie per realtà mista, cuffia di realtà mista di Windows, auricolare della realtà virtuale
ms.openlocfilehash: 90416f91a7de369ff97a2254fed4b3773724408b
ms.sourcegitcommit: be7473bbebc1872d8c9df6f2da837efd3279dee6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/15/2021
ms.locfileid: "98226410"
---
# <a name="keyboard-input-in-unity"></a><span data-ttu-id="1f53d-104">Input da tastiera in Unity</span><span class="sxs-lookup"><span data-stu-id="1f53d-104">Keyboard input in Unity</span></span>

<span data-ttu-id="1f53d-105">**Spazio dei nomi:** *UnityEngine*</span><span class="sxs-lookup"><span data-stu-id="1f53d-105">**Namespace:** *UnityEngine*</span></span><br>
 <span data-ttu-id="1f53d-106">**Tipo**: *[TouchScreenKeyboard](https://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.html)*</span><span class="sxs-lookup"><span data-stu-id="1f53d-106">**Type**: *[TouchScreenKeyboard](https://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.html)*</span></span>

<span data-ttu-id="1f53d-107">Sebbene HoloLens supporti molte forme di input, incluse le tastiere Bluetooth, la maggior parte delle applicazioni non può presupporre che tutti gli utenti dispongano di una tastiera fisica disponibile.</span><span class="sxs-lookup"><span data-stu-id="1f53d-107">While HoloLens supports many forms of input including Bluetooth keyboards, most applications can't assume that all users will have a physical keyboard available.</span></span> <span data-ttu-id="1f53d-108">Se l'applicazione richiede un input di testo, è necessario specificare una qualsiasi forma di tastiera sullo schermo.</span><span class="sxs-lookup"><span data-stu-id="1f53d-108">If your application requires text input, some form of on-screen keyboard should be provided.</span></span>

<span data-ttu-id="1f53d-109">Unity fornisce la classe *[TouchScreenKeyboard](https://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.html)* per accettare l'input da tastiera quando non è disponibile una tastiera fisica.</span><span class="sxs-lookup"><span data-stu-id="1f53d-109">Unity provides the *[TouchScreenKeyboard](https://docs.unity3d.com/ScriptReference/TouchScreenKeyboard.html)* class for accepting keyboard input when there's no physical keyboard available.</span></span>

## <a name="hololens-system-keyboard-behavior-in-unity"></a><span data-ttu-id="1f53d-110">Comportamento della tastiera di sistema HoloLens in Unity</span><span class="sxs-lookup"><span data-stu-id="1f53d-110">HoloLens system keyboard behavior in Unity</span></span>

<span data-ttu-id="1f53d-111">In HoloLens, *TouchScreenKeyboard* sfrutta la tastiera su schermo del sistema.</span><span class="sxs-lookup"><span data-stu-id="1f53d-111">On HoloLens, the *TouchScreenKeyboard* leverages the system's on-screen keyboard.</span></span> <span data-ttu-id="1f53d-112">La tastiera su schermo del sistema non può sovrapporsi a una visualizzazione volumetrica.</span><span class="sxs-lookup"><span data-stu-id="1f53d-112">The system's on-screen keyboard can't overlay on top of a volumetric view.</span></span> <span data-ttu-id="1f53d-113">Unity deve creare una visualizzazione XAML 2D secondaria per mostrare la tastiera e tornare alla visualizzazione volumetrica una volta inviato l'input.</span><span class="sxs-lookup"><span data-stu-id="1f53d-113">Unity has to create a secondary 2D XAML view to show the keyboard then return back to the volumetric view once input has been submitted.</span></span> <span data-ttu-id="1f53d-114">Il flusso utente sarà simile al seguente:</span><span class="sxs-lookup"><span data-stu-id="1f53d-114">The user flow goes like this:</span></span>
1. <span data-ttu-id="1f53d-115">L'utente esegue un'azione che causa il codice dell'app per chiamare *TouchScreenKeyboard*</span><span class="sxs-lookup"><span data-stu-id="1f53d-115">The user performs an action causing app code to call *TouchScreenKeyboard*</span></span>
    * <span data-ttu-id="1f53d-116">L'app è responsabile della sospensione dello stato dell'app prima della chiamata a *TouchScreenKeyboard*</span><span class="sxs-lookup"><span data-stu-id="1f53d-116">The app is responsible for pausing app state before calling *TouchScreenKeyboard*</span></span>
    * <span data-ttu-id="1f53d-117">L'app può terminare prima di tornare alla visualizzazione volumetrica</span><span class="sxs-lookup"><span data-stu-id="1f53d-117">The app may terminate before ever switching back to the volumetric view</span></span>
2. <span data-ttu-id="1f53d-118">Unity passa a una visualizzazione XAML 2D, che è posizionata automaticamente nel mondo</span><span class="sxs-lookup"><span data-stu-id="1f53d-118">Unity switches to a 2D XAML view, which is autoplaced in the world</span></span>
3. <span data-ttu-id="1f53d-119">L'utente immette il testo usando la tastiera di sistema e invia o Annulla</span><span class="sxs-lookup"><span data-stu-id="1f53d-119">The user enters text using the system keyboard and submits or cancels</span></span>
4. <span data-ttu-id="1f53d-120">Unity ritorna alla visualizzazione volumetrica</span><span class="sxs-lookup"><span data-stu-id="1f53d-120">Unity switches back to the volumetric view</span></span>
    * <span data-ttu-id="1f53d-121">L'app è responsabile della ripresa dello stato dell'app al termine della *TouchScreenKeyboard*</span><span class="sxs-lookup"><span data-stu-id="1f53d-121">The app is responsible for resuming app state when the *TouchScreenKeyboard* is done</span></span>
5. <span data-ttu-id="1f53d-122">Il testo inviato è disponibile in *TouchScreenKeyboard*</span><span class="sxs-lookup"><span data-stu-id="1f53d-122">Submitted text is available in the *TouchScreenKeyboard*</span></span>

### <a name="available-keyboard-views"></a><span data-ttu-id="1f53d-123">Visualizzazioni tastiera disponibili</span><span class="sxs-lookup"><span data-stu-id="1f53d-123">Available keyboard views</span></span>

<span data-ttu-id="1f53d-124">Sono disponibili sei diverse visualizzazioni tastiera:</span><span class="sxs-lookup"><span data-stu-id="1f53d-124">There are six different keyboard views available:</span></span>
* <span data-ttu-id="1f53d-125">Casella di testo a riga singola</span><span class="sxs-lookup"><span data-stu-id="1f53d-125">Single-line textbox</span></span>
* <span data-ttu-id="1f53d-126">Casella di testo a riga singola con titolo</span><span class="sxs-lookup"><span data-stu-id="1f53d-126">Single-line textbox with title</span></span>
* <span data-ttu-id="1f53d-127">Casella di testo a più righe</span><span class="sxs-lookup"><span data-stu-id="1f53d-127">Multi-line textbox</span></span>
* <span data-ttu-id="1f53d-128">Casella di testo a più righe con titolo</span><span class="sxs-lookup"><span data-stu-id="1f53d-128">Multi-line textbox with title</span></span>
* <span data-ttu-id="1f53d-129">Casella password a riga singola</span><span class="sxs-lookup"><span data-stu-id="1f53d-129">Single-line password box</span></span>
* <span data-ttu-id="1f53d-130">Casella password a riga singola con titolo</span><span class="sxs-lookup"><span data-stu-id="1f53d-130">Single-line password box with title</span></span>

## <a name="how-to-enable-the-system-keyboard-in-unity"></a><span data-ttu-id="1f53d-131">Come abilitare la tastiera di sistema in Unity</span><span class="sxs-lookup"><span data-stu-id="1f53d-131">How to enable the system keyboard in Unity</span></span>

<span data-ttu-id="1f53d-132">La tastiera di sistema HoloLens è disponibile solo per le applicazioni Unity esportate con il "tipo di compilazione UWP" impostato su "XAML".</span><span class="sxs-lookup"><span data-stu-id="1f53d-132">The HoloLens system keyboard is only available to Unity applications that are exported with the "UWP Build Type" set to "XAML".</span></span> <span data-ttu-id="1f53d-133">Quando si sceglie "XAML" come "tipo di compilazione UWP" su "D3D", si verificano compromessi.</span><span class="sxs-lookup"><span data-stu-id="1f53d-133">There are tradeoffs you make when you choose "XAML" as the "UWP Build Type" over "D3D".</span></span> <span data-ttu-id="1f53d-134">Se non si ha familiarità con questi compromessi, può essere utile esplorare una [soluzione di input alternativa](#alternative-keyboard-options) alla tastiera di sistema.</span><span class="sxs-lookup"><span data-stu-id="1f53d-134">If you aren't comfortable with those tradeoffs, you may wish to explore an [alternative input solution](#alternative-keyboard-options) to the system keyboard.</span></span>
1. <span data-ttu-id="1f53d-135">Aprire il menu **file** e selezionare **impostazioni di compilazione...**</span><span class="sxs-lookup"><span data-stu-id="1f53d-135">Open the **File** menu and select **Build Settings...**</span></span>
2. <span data-ttu-id="1f53d-136">Verificare che **la piattaforma** sia impostata su **Windows Store**, che l' **SDK** sia impostato su **Universal 10** e impostare il **tipo di compilazione UWP** su **XAML**.</span><span class="sxs-lookup"><span data-stu-id="1f53d-136">Ensure the **Platform** is set to **Windows Store**, the **SDK** is set to **Universal 10**, and set the **UWP Build Type** to **XAML**.</span></span>
3. <span data-ttu-id="1f53d-137">Nella finestra di dialogo **impostazioni di compilazione** selezionare il pulsante **Impostazioni lettore...**</span><span class="sxs-lookup"><span data-stu-id="1f53d-137">In the **Build Settings** dialog, select the **Player Settings...** button</span></span>
4. <span data-ttu-id="1f53d-138">Selezionare la scheda **impostazioni per Windows Store**</span><span class="sxs-lookup"><span data-stu-id="1f53d-138">Select the **Settings for Windows Store** tab</span></span>
5. <span data-ttu-id="1f53d-139">Espandi il gruppo **altre impostazioni**</span><span class="sxs-lookup"><span data-stu-id="1f53d-139">Expand the **Other Settings** group</span></span>
6. <span data-ttu-id="1f53d-140">Nella sezione **rendering** selezionare la casella di controllo **realtà virtuale supportata** per aggiungere un nuovo elenco **dispositivi di realtà virtuale**</span><span class="sxs-lookup"><span data-stu-id="1f53d-140">In the **Rendering** section, check the **Virtual Reality Supported** checkbox to add a new **Virtual Reality Devices** list</span></span>
7. <span data-ttu-id="1f53d-141">Assicurarsi che **Windows olografico** sia visualizzato nell'elenco degli SDK di realtà virtuale</span><span class="sxs-lookup"><span data-stu-id="1f53d-141">Ensure **Windows Holographic** appears in the list of Virtual Reality SDKs</span></span>

>[!NOTE]
><span data-ttu-id="1f53d-142">Se la compilazione non viene contrassegnata come realtà virtuale supportata con il dispositivo HoloLens, il progetto viene esportato come app XAML 2D.</span><span class="sxs-lookup"><span data-stu-id="1f53d-142">If you don't mark the build as Virtual Reality Supported with the HoloLens device, the project will export as a 2D XAML app.</span></span>

## <a name="using-the-system-keyboard-in-your-unity-app"></a><span data-ttu-id="1f53d-143">Uso della tastiera di sistema nell'app Unity</span><span class="sxs-lookup"><span data-stu-id="1f53d-143">Using the system keyboard in your Unity app</span></span>

### <a name="declare-the-keyboard"></a><span data-ttu-id="1f53d-144">Dichiarare la tastiera</span><span class="sxs-lookup"><span data-stu-id="1f53d-144">Declare the keyboard</span></span>

<span data-ttu-id="1f53d-145">Nella classe dichiarare una variabile per archiviare *TouchScreenKeyboard* e una variabile per contenere la stringa restituita dalla tastiera.</span><span class="sxs-lookup"><span data-stu-id="1f53d-145">In the class, declare a variable to store the *TouchScreenKeyboard* and a variable to hold the string the keyboard returns.</span></span>

```cs
UnityEngine.TouchScreenKeyboard keyboard;
public static string keyboardText = "";
```

### <a name="invoke-the-keyboard"></a><span data-ttu-id="1f53d-146">Richiama la tastiera</span><span class="sxs-lookup"><span data-stu-id="1f53d-146">Invoke the keyboard</span></span>

<span data-ttu-id="1f53d-147">Quando si verifica un evento che richiede l'input da tastiera, chiamare una di queste funzioni a seconda del tipo di input che si desidera utilizzare come titolo nel parametro textPlaceholder.</span><span class="sxs-lookup"><span data-stu-id="1f53d-147">When an event occurs requesting keyboard input, call one of these functions depending on the type of input you want using the title in the textPlaceholder parameter.</span></span>

```cs
// Single-line textbox
keyboard = TouchScreenKeyboard.Open("", TouchScreenKeyboardType.Default, false, false, false, false);

// Single-line textbox with title
keyboard = TouchScreenKeyboard.Open("", TouchScreenKeyboardType.Default, false, false, false, false, "Single-line title");

// Multi-line textbox
keyboard = TouchScreenKeyboard.Open("", TouchScreenKeyboardType.Default, false, true, false, false);

// Multi-line textbox with title
keyboard = TouchScreenKeyboard.Open("", TouchScreenKeyboardType.Default, false, true, false, false, "Multi-line Title");

// Single-line password box
keyboard = TouchScreenKeyboard.Open("", TouchScreenKeyboardType.Default, false, false, true, false);

// Single-line password box with title
keyboard = TouchScreenKeyboard.Open("", TouchScreenKeyboardType.Default, false, false, true, false, "Secure Single-line Title");
```

### <a name="retrieve-typed-contents"></a><span data-ttu-id="1f53d-148">Recupera contenuto tipizzato</span><span class="sxs-lookup"><span data-stu-id="1f53d-148">Retrieve typed contents</span></span>

<span data-ttu-id="1f53d-149">Nel ciclo di aggiornamento controllare se la tastiera ha ricevuto il nuovo input e archiviarlo per l'uso altrove.</span><span class="sxs-lookup"><span data-stu-id="1f53d-149">In the update loop, check if the keyboard received new input and store it for use elsewhere.</span></span>

```cs
if (TouchScreenKeyboard.visible == false && keyboard != null)
{
       if (keyboard.status == TouchScreenKeyboard.Status.Done)
       {
           keyboardText = keyboard.text;
           keyboard = null;
       }
}
```

## <a name="alternative-keyboard-options"></a><span data-ttu-id="1f53d-150">Opzioni di tastiera alternative</span><span class="sxs-lookup"><span data-stu-id="1f53d-150">Alternative keyboard options</span></span>

<span data-ttu-id="1f53d-151">Si comprende che la disattivazione di una visualizzazione volumetrica in una visualizzazione 2D non è il modo ideale per ottenere l'input di testo dall'utente.</span><span class="sxs-lookup"><span data-stu-id="1f53d-151">We understand that switching out of a volumetric view into a 2D view isn't the ideal way to get text input from the user.</span></span>

<span data-ttu-id="1f53d-152">Le alternative attuali per sfruttare la tastiera di sistema tramite Unity includono:</span><span class="sxs-lookup"><span data-stu-id="1f53d-152">The current alternatives to leveraging the system keyboard through Unity include:</span></span>
* <span data-ttu-id="1f53d-153">Uso della dettatura vocale per l'input (<b>Nota:</b> si tratta spesso di un errore soggetto a parole non trovate nel dizionario e non è adatto per l'immissione della password)</span><span class="sxs-lookup"><span data-stu-id="1f53d-153">Using speech dictation for input (<b>Note:</b> this is often error prone for words not found in the dictionary and isn't suitable for password entry)</span></span>
* <span data-ttu-id="1f53d-154">Creare una tastiera che funzioni nella visualizzazione esclusiva delle applicazioni</span><span class="sxs-lookup"><span data-stu-id="1f53d-154">Create a keyboard that works in your applications exclusive view</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="1f53d-155">Successivo checkpoint di sviluppo</span><span class="sxs-lookup"><span data-stu-id="1f53d-155">Next Development Checkpoint</span></span>

<span data-ttu-id="1f53d-156">Se si sta seguendo il percorso di sviluppo di Unity, è possibile esplorare le funzionalità e le API della piattaforma per la realtà mista.</span><span class="sxs-lookup"><span data-stu-id="1f53d-156">If you're following the Unity development journey we've laid out, you're in the midst of exploring the Mixed Reality platform capabilities and APIs.</span></span> <span data-ttu-id="1f53d-157">Da qui è possibile passare a qualsiasi [argomento](unity-development-overview.md#3-advanced-features) o passare direttamente alla distribuzione dell'app in un dispositivo o in un emulatore.</span><span class="sxs-lookup"><span data-stu-id="1f53d-157">From here, you can continue to any [topic](unity-development-overview.md#3-advanced-features) or jump directly to deploying your app on a device or emulator.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="1f53d-158">Eseguire la distribuzione in HoloLens o in modalità mista di Windows per la realtà mista</span><span class="sxs-lookup"><span data-stu-id="1f53d-158">Deploy to HoloLens or Windows Mixed Reality immersive headsets</span></span>](../platform-capabilities-and-apis/using-visual-studio.md)

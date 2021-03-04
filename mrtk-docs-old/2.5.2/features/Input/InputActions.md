---
title: InputActions
description: Documentazione per creare azioni di input in MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, InputActions,
ms.openlocfilehash: cc883aea25f90968ce9ee7eeb5488ac47432cefb
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/03/2021
ms.locfileid: "101782646"
---
# <a name="input-actions"></a><span data-ttu-id="e234b-104">Azioni di input</span><span class="sxs-lookup"><span data-stu-id="e234b-104">Input actions</span></span>

<span data-ttu-id="e234b-105">Le [**azioni di input**](InputActions.md) sono astrazioni rispetto a input non elaborati per semplificare l'isolamento della logica dell'applicazione dalle origini di input specifiche che producono un input.</span><span class="sxs-lookup"><span data-stu-id="e234b-105">[**Input Actions**](InputActions.md) are abstractions over raw inputs meant to help isolating application logic from the specific input sources producing an input.</span></span> <span data-ttu-id="e234b-106">Può essere utile, ad esempio, definire un'azione *Select* ed eseguirne il mapping con il pulsante sinistro del mouse, un pulsante in un gamepad e un trigger in un controller 6 DOF.</span><span class="sxs-lookup"><span data-stu-id="e234b-106">It can be useful, for example, to define a *Select* action and map it to the left mouse button, a button in a gamepad and a trigger in a 6 DOF controller.</span></span> <span data-ttu-id="e234b-107">È quindi possibile fare in modo che la logica dell'applicazione attenda gli eventi di azione *Select* input anziché tenere presente tutti i diversi input in grado di produrli.</span><span class="sxs-lookup"><span data-stu-id="e234b-107">You can then have your application logic listen for *Select* input action events instead of having to be aware of all the different inputs that can produce it.</span></span>

## <a name="creating-an-input-action"></a><span data-ttu-id="e234b-108">Creazione di un'azione di input</span><span class="sxs-lookup"><span data-stu-id="e234b-108">Creating an input action</span></span>

<span data-ttu-id="e234b-109">Le azioni di input vengono configurate nel **profilo azioni** di input, all'interno del *profilo del sistema di input* nel componente Toolkit di realtà mista, specificando un nome per l'azione e il tipo di input (vincolo dell'*asse*) a cui è possibile eseguire il mapping:</span><span class="sxs-lookup"><span data-stu-id="e234b-109">Input actions are configured in the **Input Actions Profile**, inside the *Input System Profile* in the Mixed Reality Toolkit component, specifying a name for the action and the type of inputs (*Axis Constraint*) it can be mapped to:</span></span>

<img src="../images/input/InputActions.png" style="max-width:100%;" alt="Input Action View">

<span data-ttu-id="e234b-110">Questi sono i valori usati più di frequente per il **vincolo AXIS**:</span><span class="sxs-lookup"><span data-stu-id="e234b-110">These are the most mostly commonly used values for **Axis Constraint**:</span></span>

<span data-ttu-id="e234b-111">Vincolo asse</span><span class="sxs-lookup"><span data-stu-id="e234b-111">Axis Constraint</span></span> | <span data-ttu-id="e234b-112">Descrizione</span><span class="sxs-lookup"><span data-stu-id="e234b-112">Description</span></span>
--- | ---
<span data-ttu-id="e234b-113">Digitale</span><span class="sxs-lookup"><span data-stu-id="e234b-113">Digital</span></span> | <span data-ttu-id="e234b-114">Input on/off come un pulsante binario in un gamepad o mouse.</span><span class="sxs-lookup"><span data-stu-id="e234b-114">On/off input like a binary button in a gamepad or mouse.</span></span>
<span data-ttu-id="e234b-115">Asse singolo</span><span class="sxs-lookup"><span data-stu-id="e234b-115">Single Axis</span></span> | <span data-ttu-id="e234b-116">Input analogico a asse singolo come un trigger analogico in un gamepad.</span><span class="sxs-lookup"><span data-stu-id="e234b-116">Single axis analogue input like an analog trigger in a gamepad.</span></span>
<span data-ttu-id="e234b-117">Asse doppio</span><span class="sxs-lookup"><span data-stu-id="e234b-117">Dual Axis</span></span> | <span data-ttu-id="e234b-118">Input analogico a doppio asse come un levetta.</span><span class="sxs-lookup"><span data-stu-id="e234b-118">Dual axis analogue input like a thumbstick.</span></span>
<span data-ttu-id="e234b-119">Sei DOF</span><span class="sxs-lookup"><span data-stu-id="e234b-119">Six Dof</span></span> | <span data-ttu-id="e234b-120">3D pose con conversione e rotazione come quella prodotta da 6 controller DOF.</span><span class="sxs-lookup"><span data-stu-id="e234b-120">3D pose with translation and rotation like the one produced by 6 DOF controllers.</span></span>

<span data-ttu-id="e234b-121">È possibile trovare l'elenco completo in [`AxisType`](xref:Microsoft.MixedReality.Toolkit.Utilities.AxisType) .</span><span class="sxs-lookup"><span data-stu-id="e234b-121">You can find the full list in [`AxisType`](xref:Microsoft.MixedReality.Toolkit.Utilities.AxisType).</span></span>

## <a name="mapping-input-to-actions"></a><span data-ttu-id="e234b-122">Mapping dell'input alle azioni</span><span class="sxs-lookup"><span data-stu-id="e234b-122">Mapping input to actions</span></span>

<span data-ttu-id="e234b-123">Il modo in cui si esegue il mapping di un input a un'azione dipende dal tipo di origine di input:</span><span class="sxs-lookup"><span data-stu-id="e234b-123">The way you map an input to and action depends on the type of the input source:</span></span>

### <a name="controller-input"></a><span data-ttu-id="e234b-124">Input del controller</span><span class="sxs-lookup"><span data-stu-id="e234b-124">Controller input</span></span>

<span data-ttu-id="e234b-125">Passare al **profilo di mapping di input del controller**, sotto il profilo di sistema di *input*.</span><span class="sxs-lookup"><span data-stu-id="e234b-125">Go to the **Controller Input Mapping Profile**, under the *Input System Profile*.</span></span> <span data-ttu-id="e234b-126">Qui sarà disponibile un elenco di tutti i controller supportati:</span><span class="sxs-lookup"><span data-stu-id="e234b-126">There you will find a list of all supported controllers:</span></span>

<img src="../images/input/ControllerInputMappingProfile.PNG" style="max-width:100%;" alt="Controller profile view">

<span data-ttu-id="e234b-127">Selezionare quello che si desidera configurare e verrà visualizzata una finestra di dialogo con tutti gli input del controller, consentendo di impostare un'azione per ognuno di essi:</span><span class="sxs-lookup"><span data-stu-id="e234b-127">Select the one you want to configure and a dialog window will appear with all the controller inputs, allowing you to set an action for each of them:</span></span>

<img src="../images/input/InputActionAssignment.PNG" style="max-width:100%;" alt="Input Assignment">

### <a name="speech-input"></a><span data-ttu-id="e234b-128">Input vocale</span><span class="sxs-lookup"><span data-stu-id="e234b-128">Speech input</span></span>

<span data-ttu-id="e234b-129">Nel **profilo del comando vocale**, sotto il *profilo di sistema di input*, è disponibile l'elenco dei comandi vocali attualmente definiti.</span><span class="sxs-lookup"><span data-stu-id="e234b-129">In the **Speech Command Profile**, under the *Input System Profile*, you'll find the list of currently defined speech commands.</span></span> <span data-ttu-id="e234b-130">Per eseguire il mapping di uno di essi a un'azione, è sufficiente selezionarlo nell'elenco a discesa *azione* .</span><span class="sxs-lookup"><span data-stu-id="e234b-130">To map one of them to an action, just select it in the *Action* drop down.</span></span>

<img src="../images/input/SpeechCommandsProfile.png" style="max-width:100%;" alt="Speech profile">

### <a name="gesture-input"></a><span data-ttu-id="e234b-131">Input movimento</span><span class="sxs-lookup"><span data-stu-id="e234b-131">Gesture input</span></span>

<span data-ttu-id="e234b-132">Il **profilo movimenti**, sotto il *profilo di sistema di input*, contiene tutti i movimenti definiti.</span><span class="sxs-lookup"><span data-stu-id="e234b-132">The **Gestures Profile**, under the *Input System Profile*, contains all defined gestures.</span></span> <span data-ttu-id="e234b-133">È possibile eseguire il mapping di ognuna di esse a un'azione selezionandola nell'elenco a discesa *azione* .</span><span class="sxs-lookup"><span data-stu-id="e234b-133">You can map each of them to an action by selecting it in the *Action* drop down.</span></span>

<img src="../images/input/GestureProfile.png" style="max-width:100%;" alt="Gesture Profile">

## <a name="handling-input-actions"></a><span data-ttu-id="e234b-134">Gestione delle azioni di input</span><span class="sxs-lookup"><span data-stu-id="e234b-134">Handling input actions</span></span>

> [!WARNING]
> <span data-ttu-id="e234b-135">Attualmente solo le azioni di input di tipo *digitale* possono essere gestite usando i metodi descritti in questa sezione.</span><span class="sxs-lookup"><span data-stu-id="e234b-135">Currently only input actions of *Digital* type can be handled using the methods described in this section.</span></span> <span data-ttu-id="e234b-136">Per gli altri tipi di azione, sarà necessario gestire direttamente gli eventi per gli input corrispondenti.</span><span class="sxs-lookup"><span data-stu-id="e234b-136">For other action types, you'll have to handle directly the events for the corresponding inputs instead.</span></span> <span data-ttu-id="e234b-137">Ad esempio, per gestire un'azione 6 DOF mappata agli input del controller, è necessario usare [`IMixedRealityGestureHandler<T>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGestureHandler`1) con T = [`MixedRealityPose`](xref:Microsoft.MixedReality.Toolkit.Utilities.MixedRealityPose) .</span><span class="sxs-lookup"><span data-stu-id="e234b-137">For example, to handle a 6 DOF action mapped to controller inputs, you'll have to use [`IMixedRealityGestureHandler<T>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGestureHandler`1) with T = [`MixedRealityPose`](xref:Microsoft.MixedReality.Toolkit.Utilities.MixedRealityPose).</span></span>

<span data-ttu-id="e234b-138">Il modo più semplice per gestire le azioni di input consiste nell'usare lo [`InputActionHandler`](xref:Microsoft.MixedReality.Toolkit.Input.InputActionHandler) script.</span><span class="sxs-lookup"><span data-stu-id="e234b-138">The easiest way to handle input actions is to make use of the [`InputActionHandler`](xref:Microsoft.MixedReality.Toolkit.Input.InputActionHandler) script.</span></span> <span data-ttu-id="e234b-139">In questo modo è possibile definire l'azione che si vuole ascoltare e rispondere agli eventi avviati e terminati con gli eventi di Unity.</span><span class="sxs-lookup"><span data-stu-id="e234b-139">This allows you to define the action you want to listen to and react to action started and ended events using Unity Events.</span></span>

<img src="../images/input/InputActionHandler.PNG" style="max-width:100%;" alt="Action Handler">

<span data-ttu-id="e234b-140">Se si desidera un maggiore controllo, è possibile implementare l' [`IMixedRealityInputActionHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputActionHandler) interfaccia direttamente nello script.</span><span class="sxs-lookup"><span data-stu-id="e234b-140">If you want more control, you can implement the [`IMixedRealityInputActionHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputActionHandler) interface directly in your script.</span></span> <span data-ttu-id="e234b-141">Per ulteriori informazioni sulla gestione degli eventi tramite interfacce del gestore, vedere la sezione [**eventi di input**](InputEvents.md) .</span><span class="sxs-lookup"><span data-stu-id="e234b-141">See the [**Input Events**](InputEvents.md) section for more details on event handling via handler interfaces.</span></span>

## <a name="examples"></a><span data-ttu-id="e234b-142">Esempio</span><span class="sxs-lookup"><span data-stu-id="e234b-142">Examples</span></span>

<span data-ttu-id="e234b-143">Vedere `MRTK/Examples/Demos/Input/Scenes/InputActions` per una scena di esempio che illustra come creare un'azione, eseguirne il mapping agli input del controller, del riconoscimento vocale e del movimento e usarla per ruotare un oggetto in un comando.</span><span class="sxs-lookup"><span data-stu-id="e234b-143">See `MRTK/Examples/Demos/Input/Scenes/InputActions` for an example scene showing how to create an action, map it to controller, speech and gesture inputs and use it to rotate an object on command.</span></span>

<img src="../images/input/InputActionsExample.PNG" style="max-width:100%;" alt="Action Example">
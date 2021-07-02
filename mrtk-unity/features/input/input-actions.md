---
title: Azioni di input
description: Documentazione per creare azioni di input in MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, InputActions,
ms.openlocfilehash: cf6ce2af304ee1cd706d0111d66a97018113fb09
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176808"
---
# <a name="input-actions"></a><span data-ttu-id="9ed64-104">Azioni di input</span><span class="sxs-lookup"><span data-stu-id="9ed64-104">Input actions</span></span>

<span data-ttu-id="9ed64-105">[**Le azioni di**](input-actions.md) input sono astrazioni su input non elaborati che consentono di isolare la logica dell'applicazione dalle origini di input specifiche che producono un input.</span><span class="sxs-lookup"><span data-stu-id="9ed64-105">[**Input Actions**](input-actions.md) are abstractions over raw inputs meant to help isolating application logic from the specific input sources producing an input.</span></span> <span data-ttu-id="9ed64-106">Può essere utile, ad esempio, definire un'azione *Select* e mapparla al pulsante sinistro del mouse, un pulsante in un game pad e un trigger in un controller DOF 6.</span><span class="sxs-lookup"><span data-stu-id="9ed64-106">It can be useful, for example, to define a *Select* action and map it to the left mouse button, a button in a gamepad and a trigger in a 6 DOF controller.</span></span> <span data-ttu-id="9ed64-107">È quindi possibile fare in modo che la logica dell'applicazione sia in ascolto degli eventi Select *input* action invece di dover conoscere tutti i diversi input che possono generarlo.</span><span class="sxs-lookup"><span data-stu-id="9ed64-107">You can then have your application logic listen for *Select* input action events instead of having to be aware of all the different inputs that can produce it.</span></span>

## <a name="creating-an-input-action"></a><span data-ttu-id="9ed64-108">Creazione di un'azione di input</span><span class="sxs-lookup"><span data-stu-id="9ed64-108">Creating an input action</span></span>

<span data-ttu-id="9ed64-109">Le azioni di input vengono configurate  nel profilo azioni di input all'interno del profilo del sistema di input nel componente Toolkit realtà mista, specificando un nome per l'azione e il tipo di input (*Vincolo* asse ) a cui è possibile eseguire il mapping:</span><span class="sxs-lookup"><span data-stu-id="9ed64-109">Input actions are configured in the **Input Actions Profile**, inside the *Input System Profile* in the Mixed Reality Toolkit component, specifying a name for the action and the type of inputs (*Axis Constraint*) it can be mapped to:</span></span>

<img src="../images/input/InputActions.png" alt="Input Action" style="max-width:100%;">

<span data-ttu-id="9ed64-110">Questi sono i valori usati più di frequente per **Il vincolo dell'asse:**</span><span class="sxs-lookup"><span data-stu-id="9ed64-110">These are the most mostly commonly used values for **Axis Constraint**:</span></span>

<span data-ttu-id="9ed64-111">Vincolo dell'asse</span><span class="sxs-lookup"><span data-stu-id="9ed64-111">Axis Constraint</span></span> | <span data-ttu-id="9ed64-112">Descrizione</span><span class="sxs-lookup"><span data-stu-id="9ed64-112">Description</span></span>
--- | ---
<span data-ttu-id="9ed64-113">Digitale</span><span class="sxs-lookup"><span data-stu-id="9ed64-113">Digital</span></span> | <span data-ttu-id="9ed64-114">Input on/off come un pulsante binario in un game pad o mouse.</span><span class="sxs-lookup"><span data-stu-id="9ed64-114">On/off input like a binary button in a gamepad or mouse.</span></span>
<span data-ttu-id="9ed64-115">Asse singolo</span><span class="sxs-lookup"><span data-stu-id="9ed64-115">Single Axis</span></span> | <span data-ttu-id="9ed64-116">Input analogo a un asse singolo come un trigger analogico in un game pad.</span><span class="sxs-lookup"><span data-stu-id="9ed64-116">Single axis analogue input like an analog trigger in a gamepad.</span></span>
<span data-ttu-id="9ed64-117">Asse doppio</span><span class="sxs-lookup"><span data-stu-id="9ed64-117">Dual Axis</span></span> | <span data-ttu-id="9ed64-118">Input analogo a doppio asse, ad esempio una levetta.</span><span class="sxs-lookup"><span data-stu-id="9ed64-118">Dual axis analogue input like a thumbstick.</span></span>
<span data-ttu-id="9ed64-119">Sei Dof</span><span class="sxs-lookup"><span data-stu-id="9ed64-119">Six Dof</span></span> | <span data-ttu-id="9ed64-120">Posizione 3D con traslazione e rotazione come quella prodotta da 6 controller DOF.</span><span class="sxs-lookup"><span data-stu-id="9ed64-120">3D pose with translation and rotation like the one produced by 6 DOF controllers.</span></span>

<span data-ttu-id="9ed64-121">È possibile trovare l'elenco completo in [`AxisType`](xref:Microsoft.MixedReality.Toolkit.Utilities.AxisType) .</span><span class="sxs-lookup"><span data-stu-id="9ed64-121">You can find the full list in [`AxisType`](xref:Microsoft.MixedReality.Toolkit.Utilities.AxisType).</span></span>

## <a name="mapping-input-to-actions"></a><span data-ttu-id="9ed64-122">Mapping dell'input alle azioni</span><span class="sxs-lookup"><span data-stu-id="9ed64-122">Mapping input to actions</span></span>

<span data-ttu-id="9ed64-123">Il modo in cui si esegue il mapping di un input a un'azione e dipende dal tipo di origine di input:</span><span class="sxs-lookup"><span data-stu-id="9ed64-123">The way you map an input to and action depends on the type of the input source:</span></span>

### <a name="controller-input"></a><span data-ttu-id="9ed64-124">Input del controller</span><span class="sxs-lookup"><span data-stu-id="9ed64-124">Controller input</span></span>

<span data-ttu-id="9ed64-125">Passare a Profilo **mapping input controller** in Profilo sistema di *input*.</span><span class="sxs-lookup"><span data-stu-id="9ed64-125">Go to the **Controller Input Mapping Profile**, under the *Input System Profile*.</span></span> <span data-ttu-id="9ed64-126">Qui è possibile trovare un elenco di tutti i controller supportati:</span><span class="sxs-lookup"><span data-stu-id="9ed64-126">There you will find a list of all supported controllers:</span></span>

<img src="../images/input/ControllerInputMappingProfile.PNG" alt="Input maping profile" style="max-width:100%;">

<span data-ttu-id="9ed64-127">Selezionare quella che si vuole configurare e verrà visualizzata una finestra di dialogo con tutti gli input del controller, consentendo di impostare un'azione per ognuno di essi:</span><span class="sxs-lookup"><span data-stu-id="9ed64-127">Select the one you want to configure and a dialog window will appear with all the controller inputs, allowing you to set an action for each of them:</span></span>

<img src="../images/input/InputActionAssignment.PNG" alt="Input Action Assignment" style="max-width:100%;">

### <a name="speech-input"></a><span data-ttu-id="9ed64-128">Input vocale</span><span class="sxs-lookup"><span data-stu-id="9ed64-128">Speech input</span></span>

<span data-ttu-id="9ed64-129">In **Speech Command Profile (Profilo** comando vocale) in *Input System Profile (Profilo* sistema di input) è disponibile l'elenco dei comandi vocali attualmente definiti.</span><span class="sxs-lookup"><span data-stu-id="9ed64-129">In the **Speech Command Profile**, under the *Input System Profile*, you'll find the list of currently defined speech commands.</span></span> <span data-ttu-id="9ed64-130">Per eseguire il mapping di uno di essi a un'azione, è sufficiente selezionarla *nell'elenco a discesa* Azione.</span><span class="sxs-lookup"><span data-stu-id="9ed64-130">To map one of them to an action, just select it in the *Action* drop down.</span></span>

<img src="../images/input/SpeechCommandsProfile.png" alt="Speech Commands profile" style="max-width:100%;">

### <a name="gesture-input"></a><span data-ttu-id="9ed64-131">Input del movimento</span><span class="sxs-lookup"><span data-stu-id="9ed64-131">Gesture input</span></span>

<span data-ttu-id="9ed64-132">Il **profilo Movimenti,** in *Profilo sistema di input,* contiene tutti i movimenti definiti.</span><span class="sxs-lookup"><span data-stu-id="9ed64-132">The **Gestures Profile**, under the *Input System Profile*, contains all defined gestures.</span></span> <span data-ttu-id="9ed64-133">È possibile eseguire il mapping di ognuno di essi a un'azione selezionandola *nell'elenco a discesa* Azione.</span><span class="sxs-lookup"><span data-stu-id="9ed64-133">You can map each of them to an action by selecting it in the *Action* drop down.</span></span>

<img src="../images/input/GestureProfile.png" alt="Gesture profile" style="max-width:100%;">

## <a name="handling-input-actions"></a><span data-ttu-id="9ed64-134">Gestione delle azioni di input</span><span class="sxs-lookup"><span data-stu-id="9ed64-134">Handling input actions</span></span>

> [!WARNING]
> <span data-ttu-id="9ed64-135">Attualmente solo le azioni di input *di tipo* Digitale possono essere gestite usando i metodi descritti in questa sezione.</span><span class="sxs-lookup"><span data-stu-id="9ed64-135">Currently only input actions of *Digital* type can be handled using the methods described in this section.</span></span> <span data-ttu-id="9ed64-136">Per altri tipi di azione, sarà invece necessario gestire direttamente gli eventi per gli input corrispondenti.</span><span class="sxs-lookup"><span data-stu-id="9ed64-136">For other action types, you'll have to handle directly the events for the corresponding inputs instead.</span></span> <span data-ttu-id="9ed64-137">Ad esempio, per gestire un'azione 6 DOF mappata agli input del controller, è necessario usare [`IMixedRealityGestureHandler<T>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGestureHandler`1) con T = [`MixedRealityPose`](xref:Microsoft.MixedReality.Toolkit.Utilities.MixedRealityPose) .</span><span class="sxs-lookup"><span data-stu-id="9ed64-137">For example, to handle a 6 DOF action mapped to controller inputs, you'll have to use [`IMixedRealityGestureHandler<T>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGestureHandler`1) with T = [`MixedRealityPose`](xref:Microsoft.MixedReality.Toolkit.Utilities.MixedRealityPose).</span></span>

<span data-ttu-id="9ed64-138">Il modo più semplice per gestire le azioni di input è usare lo [`InputActionHandler`](xref:Microsoft.MixedReality.Toolkit.Input.InputActionHandler) script.</span><span class="sxs-lookup"><span data-stu-id="9ed64-138">The easiest way to handle input actions is to make use of the [`InputActionHandler`](xref:Microsoft.MixedReality.Toolkit.Input.InputActionHandler) script.</span></span> <span data-ttu-id="9ed64-139">In questo modo è possibile definire l'azione su cui si vuole restare in ascolto e reagire agli eventi avviati e terminati tramite eventi unity.</span><span class="sxs-lookup"><span data-stu-id="9ed64-139">This allows you to define the action you want to listen to and react to action started and ended events using Unity Events.</span></span>

<img src="../images/input/InputActionHandler.PNG" alt="Acton Handler" style="max-width:100%;">

<span data-ttu-id="9ed64-140">Se si vuole un maggiore controllo, è possibile implementare [`IMixedRealityInputActionHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputActionHandler) l'interfaccia direttamente nello script.</span><span class="sxs-lookup"><span data-stu-id="9ed64-140">If you want more control, you can implement the [`IMixedRealityInputActionHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputActionHandler) interface directly in your script.</span></span> <span data-ttu-id="9ed64-141">Per altri [**dettagli sulla**](input-events.md) gestione degli eventi tramite le interfacce del gestore, vedere la sezione Eventi di input.</span><span class="sxs-lookup"><span data-stu-id="9ed64-141">See the [**Input Events**](input-events.md) section for more details on event handling via handler interfaces.</span></span>

## <a name="examples"></a><span data-ttu-id="9ed64-142">Esempio</span><span class="sxs-lookup"><span data-stu-id="9ed64-142">Examples</span></span>

<span data-ttu-id="9ed64-143">Vedere per una scena di esempio che illustra come creare un'azione, mapparla al controller, input vocali e movimenti e usarla per ruotare `MRTK/Examples/Demos/Input/Scenes/InputActions` un oggetto al comando.</span><span class="sxs-lookup"><span data-stu-id="9ed64-143">See `MRTK/Examples/Demos/Input/Scenes/InputActions` for an example scene showing how to create an action, map it to controller, speech and gesture inputs and use it to rotate an object on command.</span></span>

<img src="../images/input/InputActionsExample.PNG" alt="Input action example" style="max-width:100%;">

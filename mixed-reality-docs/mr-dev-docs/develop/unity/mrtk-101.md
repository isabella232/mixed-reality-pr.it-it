---
title: MRTK 101 - Uso di interazioni spaziali comuni
description: Come usare Mixed Reality Toolkit Unity per le interazioni di base per HoloLens 2, HoloLens, Windows Mixed Reality e Open VR.
author: cre8ivepark
ms.author: dongpark
ms.date: 08/27/2019
ms.topic: article
keywords: HoloLens, MRTK, Mixed Reality Toolkit, Windows Mixed Reality, progettazione, app di esempio, controlli, visore VR realtà mista, visore VR di windows mixed reality, visore per realtà virtuale
ms.localizationpriority: high
ms.openlocfilehash: ff3c6e055bca66fc5ad12548966140af8197235c
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2021
ms.locfileid: "98008941"
---
# <a name="mrtk-101-how-to-use-mixed-reality-toolkit-unity-for-common-spatial-interactions"></a><span data-ttu-id="dcbaa-104">MRTK 101: Come usare Mixed Reality Toolkit Unity per le interazioni spaziali comuni</span><span class="sxs-lookup"><span data-stu-id="dcbaa-104">MRTK 101: How to use Mixed Reality Toolkit Unity for common spatial interactions</span></span>

![MRTK](images/MRTK101/MRTK101Cover.png)

<span data-ttu-id="dcbaa-106">Informazioni su come usare MRTK per ottenere alcuni dei comuni modelli di interazione più diffusi per la realtà mista.</span><span class="sxs-lookup"><span data-stu-id="dcbaa-106">Learn about how to use MRTK to achieve some of the most widely used common interaction patterns in mixed reality.</span></span>

- <span data-ttu-id="dcbaa-107">Come simulare le interazioni di input nell'editor di Unity?</span><span class="sxs-lookup"><span data-stu-id="dcbaa-107">How to simulate input interactions in Unity editor?</span></span>
- <span data-ttu-id="dcbaa-108">Come afferrare e spostare un oggetto?</span><span class="sxs-lookup"><span data-stu-id="dcbaa-108">How to grab and move an object?</span></span>
- <span data-ttu-id="dcbaa-109">Come ridimensionare un oggetto?</span><span class="sxs-lookup"><span data-stu-id="dcbaa-109">How to resize an object?</span></span>
- <span data-ttu-id="dcbaa-110">Come spostare o ruotare un oggetto con precisione?</span><span class="sxs-lookup"><span data-stu-id="dcbaa-110">How to move or rotate an object with precision?</span></span>
- <span data-ttu-id="dcbaa-111">Come fare in modo che un oggetto risponda agli eventi di input?</span><span class="sxs-lookup"><span data-stu-id="dcbaa-111">How to make an object respond to input events?</span></span>
- <span data-ttu-id="dcbaa-112">Come aggiungere feedback visivo?</span><span class="sxs-lookup"><span data-stu-id="dcbaa-112">How to add visual feedback?</span></span>
- <span data-ttu-id="dcbaa-113">Come aggiungere feedback audio?</span><span class="sxs-lookup"><span data-stu-id="dcbaa-113">How to add audio feedback?</span></span>
- <span data-ttu-id="dcbaa-114">Come usare i prefab dei pulsanti nello stile di HoloLens 2?</span><span class="sxs-lookup"><span data-stu-id="dcbaa-114">How to use HoloLens 2 style button prefabs?</span></span>
- <span data-ttu-id="dcbaa-115">Come fare in modo che un oggetto ti segua?</span><span class="sxs-lookup"><span data-stu-id="dcbaa-115">How to make an object follow you?</span></span>
- <span data-ttu-id="dcbaa-116">Come fare in modo che un oggetto rimanga rivolto verso di te?</span><span class="sxs-lookup"><span data-stu-id="dcbaa-116">How to make an object face you?</span></span>

> [!NOTE]
> <span data-ttu-id="dcbaa-117">Questo articolo è stato aggiornato con le modifiche apportate in [MRTK v2.5.1](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/tag/v2.5.1).</span><span class="sxs-lookup"><span data-stu-id="dcbaa-117">This article has been updated to reflect the changes in [MRTK v2.5.1 release](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/tag/v2.5.1)</span></span>

<span data-ttu-id="dcbaa-118">Tutto il contenuto di questa pagina può essere testato nell'editor di Unity con la simulazione di input di MRTK.</span><span class="sxs-lookup"><span data-stu-id="dcbaa-118">All contents in this page can be tested in Unity editor with MRTK's Input Simulation.</span></span> <span data-ttu-id="dcbaa-119">Attenersi alla [Guida all'installazione di MRTK (GitHub)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html) per installare la versione più recente di MRTK se non si ha a disposizione.</span><span class="sxs-lookup"><span data-stu-id="dcbaa-119">If you haven't, follow [MRTK Installation Guide (GitHub)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html) to install the latest version of MRTK.</span></span>

## <a name="how-to-simulate-input-interactions-in-unity-editor"></a><span data-ttu-id="dcbaa-120">Come simulare le interazioni di input nell'editor di Unity?</span><span class="sxs-lookup"><span data-stu-id="dcbaa-120">How to simulate input interactions in Unity editor?</span></span>

<span data-ttu-id="dcbaa-121">MRTK supporta la simulazione di input nell'editor.</span><span class="sxs-lookup"><span data-stu-id="dcbaa-121">MRTK supports in-editor input simulation.</span></span> <span data-ttu-id="dcbaa-122">Eseguire la scena facendo clic sul pulsante Play di Unity e quindi usare i tasti seguenti per simulare l'input:</span><span class="sxs-lookup"><span data-stu-id="dcbaa-122">Run your scene by clicking Unity's play button, then use the following keys to simulate input:</span></span>
- <span data-ttu-id="dcbaa-123">Premi W, A, S, D per spostare la fotocamera.</span><span class="sxs-lookup"><span data-stu-id="dcbaa-123">Press W, A, S, D keys to move the camera.</span></span>
- <span data-ttu-id="dcbaa-124">Tieni premuto il pulsante destro del mouse e sposta il puntatore del mouse per guardarti attorno.</span><span class="sxs-lookup"><span data-stu-id="dcbaa-124">Hold the right mouse button and move the mouse to look around.</span></span>
- <span data-ttu-id="dcbaa-125">Premere la barra spaziatrice (mano destra) o il tasto MAIUSC di sinistra (mano sinistra) per visualizzare le mani simulate</span><span class="sxs-lookup"><span data-stu-id="dcbaa-125">Press Space bar(Right hand) or left Shift key(Left hand) to bring up the simulated hands</span></span>
- <span data-ttu-id="dcbaa-126">Premere il tasto T o Y per mantenere la visualizzazione delle mani simulate</span><span class="sxs-lookup"><span data-stu-id="dcbaa-126">Press T or Y keys to keep simulated hands in view</span></span>
- <span data-ttu-id="dcbaa-127">Premere Q o E (orizzontale) oppure R o F (verticale) per ruotare le mani simulate</span><span class="sxs-lookup"><span data-stu-id="dcbaa-127">Press Q or E(horizontal) / R or F(vertical) to rotate simulated hands</span></span>

<span data-ttu-id="dcbaa-128">Per altre informazioni sulla simulazione di input, vedere la [documentazione di MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/InputSimulation/InputSimulationService.html).</span><span class="sxs-lookup"><span data-stu-id="dcbaa-128">You can learn more about Input Simulation in the [MRTK documentation](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/InputSimulation/InputSimulationService.html).</span></span>

## <a name="how-to-grab-and-move-an-object"></a><span data-ttu-id="dcbaa-129">Come afferrare e spostare un oggetto?</span><span class="sxs-lookup"><span data-stu-id="dcbaa-129">How to grab and move an object?</span></span>

<span data-ttu-id="dcbaa-130">Associare gli script **ObjectManipulator.cs** e **NearInteractionGrabbable.cs** per rendere un oggetto afferrabile.</span><span class="sxs-lookup"><span data-stu-id="dcbaa-130">Attach the **ObjectManipulator.cs** and **NearInteractionGrabbable.cs** scripts to make an object grabbable.</span></span> <span data-ttu-id="dcbaa-131">ObjectManipulator supporta le interazioni da vicino e da lontano.</span><span class="sxs-lookup"><span data-stu-id="dcbaa-131">ObjectManipulator supports both near and far interactions.</span></span> <span data-ttu-id="dcbaa-132">È possibile afferrare e spostare un oggetto con l'input di tracciamento della mano articolata di HoloLens 2 (da vicino), il raggio della mano (da lontano), il raggio del controller del movimento (da lontano), il cursore dello sguardo e la simulazione del tocco di HoloLens (da lontano).</span><span class="sxs-lookup"><span data-stu-id="dcbaa-132">You can grab and move an object with HoloLens 2's articulated hand tracking input(near), hand ray(far), motion controller's beam(far), and HoloLens gaze cursor and air-tap(far).</span></span>

<br/><img alt="NearInteractionGrabbable and ObjectManipulator.cs assigned to an object" width="800" src="images/MRTK101/MRTK_ManipulationHandler.png">

<br/><img alt="NearInteractionGrabbable and ObjectManipulator.cs assigned to an object for grab and move" width="800" src="images/MRTK101/MRTK_GrabMove.gif">


## <a name="how-to-resize-an-object"></a><span data-ttu-id="dcbaa-133">Come ridimensionare un oggetto?</span><span class="sxs-lookup"><span data-stu-id="dcbaa-133">How to resize an object?</span></span>
<span data-ttu-id="dcbaa-134">**ObjectManipulator.cs** supporta il ridimensionamento e la rotazione a due mani.</span><span class="sxs-lookup"><span data-stu-id="dcbaa-134">**ObjectManipulator.cs** supports two-handed scale/rotation.</span></span> <span data-ttu-id="dcbaa-135">Lo script funziona con vari tipi di input, ad esempio l'input della mano articolata di HoloLens 2, l'input dello sguardo e del movimento di HoloLens 1 e l'input del controller del movimento del visore VR immersive di Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="dcbaa-135">The script works with various input types, such as HoloLens 2's articulated hand input, HoloLens 1's gaze + gesture input, and Windows Mixed Reality immersive headset's motion controller input.</span></span>

- [<span data-ttu-id="dcbaa-136">Altre informazioni su Object Manipulator nella documentazione di MRTK</span><span class="sxs-lookup"><span data-stu-id="dcbaa-136">Learn more about Object Manipulator in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectManipulator.html)

<br/><img alt="NearInteractionGrabbable and ObjectManipulator.cs assigned to an object for manipulation" width="800" src="images/MRTK101/MRTK_ManipulationHandler.gif">

## <a name="how-to-move-or-rotate-an-object-with-precision"></a><span data-ttu-id="dcbaa-137">Come spostare o ruotare un oggetto con precisione?</span><span class="sxs-lookup"><span data-stu-id="dcbaa-137">How to move or rotate an object with precision?</span></span>
<span data-ttu-id="dcbaa-138">Assegnare **BoundsControl.cs** a un oggetto in modo da usare il rettangolo di selezione che costituisce l'interfaccia per il ridimensionamento e la rotazione di un oggetto.</span><span class="sxs-lookup"><span data-stu-id="dcbaa-138">Assign **BoundsControl.cs** to an object to use Bounding Box, which is the interface for scaling and rotating an object.</span></span> <span data-ttu-id="dcbaa-139">Per impostazione predefinita, vengono visualizzati i quadratini e le linee blu nello stile di HoloLens 1.</span><span class="sxs-lookup"><span data-stu-id="dcbaa-139">By default, it shows HoloLens 1 style blue handles and wires.</span></span> <span data-ttu-id="dcbaa-140">Per usare i quadratini animati basati su prossimità nello stile di HoloLens 2, devi assegnare prefab e materiali.</span><span class="sxs-lookup"><span data-stu-id="dcbaa-140">To use HoloLens 2 style proximity-based animated handles, you need to assign prefabs and materials.</span></span> 

<br/><img alt="BoundsControl.cs assigned to an object image" width="800" src="images/MRTK101/MRTK_BoundingBox.png">

<br/><img alt="BoundsControl.cs assigned to an object gif" width="800" src="images/MRTK101/MRTK_BoundingBox.gif">

- [<span data-ttu-id="dcbaa-141">Altre informazioni su Bounds Control nella documentazione di MRTK</span><span class="sxs-lookup"><span data-stu-id="dcbaa-141">Learn more about Bounds Control in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundsControl.html)


## <a name="how-to-make-an-object-respond-to-input-events"></a><span data-ttu-id="dcbaa-142">Come fare in modo che un oggetto risponda agli eventi di input?</span><span class="sxs-lookup"><span data-stu-id="dcbaa-142">How to make an object respond to input events?</span></span>
<span data-ttu-id="dcbaa-143">Assegnare **PointerHandler.cs** a un oggetto.</span><span class="sxs-lookup"><span data-stu-id="dcbaa-143">Assign **PointerHandler.cs** to an object.</span></span> <span data-ttu-id="dcbaa-144">Nella finestra Inspector (Controllo) è possibile usare gli eventi OnPointerDown(), OnPointerUp(), OnPointerClicked(), OnPointerDragged(). Per usare questi eventi in uno script, implementare **IMixedRealityPointerHandler**.</span><span class="sxs-lookup"><span data-stu-id="dcbaa-144">In the inspector, you can use events OnPointerDown(), OnPointerUp(), OnPointerClicked(), OnPointerDragged() To use these events in a script, implement **IMixedRealityPointerHandler**.</span></span>

<br/><img alt="PointerHandler.cs assigned to an object image" width="800" src="images/MRTK101/MRTK_PointerHandler.png">

- [<span data-ttu-id="dcbaa-145">Altre informazioni sul sistema di input nella documentazione di MRTK</span><span class="sxs-lookup"><span data-stu-id="dcbaa-145">Learn more about Input System in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html)

## <a name="how-to-add-visual-feedback"></a><span data-ttu-id="dcbaa-146">Come aggiungere feedback visivo?</span><span class="sxs-lookup"><span data-stu-id="dcbaa-146">How to add visual feedback?</span></span>
<span data-ttu-id="dcbaa-147">Assegnare **Interactable.cs** a un oggetto.</span><span class="sxs-lookup"><span data-stu-id="dcbaa-147">Assign **Interactable.cs** to an object.</span></span> <span data-ttu-id="dcbaa-148">Nella finestra Inspector (Controllo) aggiungere l'oggetto di destinazione e creare un nuovo tema.</span><span class="sxs-lookup"><span data-stu-id="dcbaa-148">In the inspector, add target object and create a new theme.</span></span> <span data-ttu-id="dcbaa-149">Utilizzando i profili dei temi di Interact, puoi aggiungere facilmente feedback visivo a tutti gli stati di interazione di input disponibili.</span><span class="sxs-lookup"><span data-stu-id="dcbaa-149">Using Interactable's theme profiles, you can easily add visual feedback to all available input interaction states.</span></span>

<br/><img alt="Image of PointerHandler.cs assigned to an object" width="800" src="images/MRTK101/MRTK_Interactable.png">

<br/><img alt="Interactable gif" width="800" src="images/MRTK101/MRTK_Interactable.gif">


<span data-ttu-id="dcbaa-150">Interactable offre diversi tipi di temi, incluso il tema dello shader, che consente di controllare le proprietà dello shader in base allo stato di interazione.</span><span class="sxs-lookup"><span data-stu-id="dcbaa-150">Interactable provides various types of themes including the shader theme, which allows you to control properties of the shader per interaction state.</span></span>

- [<span data-ttu-id="dcbaa-151">Altre informazioni su Interactable nella documentazione di MRTK</span><span class="sxs-lookup"><span data-stu-id="dcbaa-151">Learn more about Interactable in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html)

<span data-ttu-id="dcbaa-152">Un altro componente importante per il feedback visivo è lo **shader Standard di MRTK**.</span><span class="sxs-lookup"><span data-stu-id="dcbaa-152">Another important building block for visual feedback is the **MRTK Standard Shader**.</span></span> <span data-ttu-id="dcbaa-153">Con questo shader puoi aggiungere facilmente effetti di feedback visivo, ad esempio una luce in movimento e una luce di prossimità.</span><span class="sxs-lookup"><span data-stu-id="dcbaa-153">With MRTK Standard Shader, you can easily add visual feedback effects such as hover light and proximity light.</span></span> <span data-ttu-id="dcbaa-154">Poiché lo shader MRTK Standard esegue meno calcoli rispetto allo shader Unity Standard, è possibile creare un'esperienza con ottime prestazioni.</span><span class="sxs-lookup"><span data-stu-id="dcbaa-154">Since MRTK Standard shader performs less computation than the Unity Standard shader, you can create a performant experience.</span></span>

<span data-ttu-id="dcbaa-155">Crea un nuovo materiale e seleziona lo shader "Mixed Reality Toolkit > Standard".</span><span class="sxs-lookup"><span data-stu-id="dcbaa-155">Create a new material and select the Shader 'Mixed Reality Toolkit > Standard'.</span></span> <span data-ttu-id="dcbaa-156">Puoi selezionare uno dei materiali esistenti che usano lo shader MRTK Standard.</span><span class="sxs-lookup"><span data-stu-id="dcbaa-156">Or you can pick one of the existing materials that use MRTK Standard Shader.</span></span>

<br/><img alt="MRTK Standard Shader image 1" width="400" src="images/MRTK101/MRTK_Shader0.png">
<br/><br/>
<img alt="MRTK Standard Shader image 2" width="800" src="images/MRTK101/MRTK_Shader1.png">

<img alt="MRTK Standard Shader image 3" width="800" src="images/MRTK101/MRTK_Shader.gif">


- [<span data-ttu-id="dcbaa-157">Altre informazioni sullo shader MRTK Standard nella documentazione di MRTK</span><span class="sxs-lookup"><span data-stu-id="dcbaa-157">Learn more about MRTK Standard Shader in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_MRTKStandardShader.html)

## <a name="how-to-add-audio-feedback"></a><span data-ttu-id="dcbaa-158">Come aggiungere feedback audio?</span><span class="sxs-lookup"><span data-stu-id="dcbaa-158">How to add audio feedback?</span></span>
<span data-ttu-id="dcbaa-159">Aggiungere **AudioSource** a un oggetto.</span><span class="sxs-lookup"><span data-stu-id="dcbaa-159">Add **AudioSource** to an object.</span></span> <span data-ttu-id="dcbaa-160">Successivamente, negli script che espongono eventi di input, ad esempio Interactable.cs o PointerHandler.cs, assegnare l'oggetto con AudioSource all'evento e selezionare **AudioSource.PlayOneShot()** .</span><span class="sxs-lookup"><span data-stu-id="dcbaa-160">Then, in the scripts that expose input events(e.g. Interactable.cs or PointerHandler.cs), assign the object with AudioSource to the event and select **AudioSource.PlayOneShot()**.</span></span> <span data-ttu-id="dcbaa-161">Puoi usare i clip audio oppure sceglierne uno dalle risorse audio di MRTK.</span><span class="sxs-lookup"><span data-stu-id="dcbaa-161">You can use your audio clips or choose one from MRTK's audio assets.</span></span>

<br/><img alt="Audio Source assigned to an object. AudioSource.PlayOneShot configured in the Interactable's OnPress() and OnRelease() events." width="800" src="images/MRTK101/MRTK_Audio.png">

## <a name="how-to-use-hololens-2-style-button-prefabs"></a><span data-ttu-id="dcbaa-162">Come usare i prefab dei pulsanti nello stile di HoloLens 2?</span><span class="sxs-lookup"><span data-stu-id="dcbaa-162">How to use HoloLens 2 style button prefabs?</span></span>
<span data-ttu-id="dcbaa-163">MRTK offre diversi tipi di pulsanti nello stile della shell (sistema operativo) di HoloLens 2, incluso feedback visivo come la luce di prossimità, l'effetto di compressione e un effetto ondulato sulla superficie del pulsante che migliora la fiducia dell'utente.</span><span class="sxs-lookup"><span data-stu-id="dcbaa-163">MRTK provides various types of HoloLens 2's shell (OS) style buttons, including visual feedback like proximity light, compressing box, and a ripple effect on the button surface that improve the user's confidence.</span></span>

<br/><img alt="Interactable button" width="800" src="images/MRTK101/MRTK_Button.gif">

<span data-ttu-id="dcbaa-164">Selezionare e trascinare nella scena uno dei **prefab dei pulsanti a pressione nello stile di HoloLens 2**.</span><span class="sxs-lookup"><span data-stu-id="dcbaa-164">Drag and drop one of the **HoloLens 2 style pressable button prefab** into your scene.</span></span> <span data-ttu-id="dcbaa-165">Il prefab usa lo script Interactable.cs introdotto in precedenza.</span><span class="sxs-lookup"><span data-stu-id="dcbaa-165">The prefab uses Interactable.cs introduced above.</span></span> <span data-ttu-id="dcbaa-166">Puoi usare gli eventi esposti, ad esempio OnClick(), in Interactable per attivare le azioni.</span><span class="sxs-lookup"><span data-stu-id="dcbaa-166">You can use exposed events such as OnClick() in the Interactable to trigger actions.</span></span>

<br/><img alt="HoloLens 2 Button Prefab" width="800" src="images/MRTK101/MRTK_Button.png">

- [<span data-ttu-id="dcbaa-167">Altre informazioni sui prefab dei pulsanti nella documentazione di MRTK</span><span class="sxs-lookup"><span data-stu-id="dcbaa-167">Learn more about Button prefabs in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html)

## <a name="how-to-make-an-object-follow-you"></a><span data-ttu-id="dcbaa-168">Come fare in modo che un oggetto ti segua?</span><span class="sxs-lookup"><span data-stu-id="dcbaa-168">How to make an object follow you?</span></span>
<span data-ttu-id="dcbaa-169">Assegnare lo script **RadialView.cs** o **Follow.cs** a un oggetto.</span><span class="sxs-lookup"><span data-stu-id="dcbaa-169">Assign **RadialView.cs** or **Follow.cs** script to an object.</span></span> <span data-ttu-id="dcbaa-170">Fa parte della serie di script Solver che consente di ottenere vari tipi di posizionamento degli oggetti nello spazio 3D.</span><span class="sxs-lookup"><span data-stu-id="dcbaa-170">It's part of the Solver script series that allows you to achieve various types of object positioning in 3D space.</span></span> <span data-ttu-id="dcbaa-171">Verrà aggiunto automaticamente **SolverHandler.cs**.</span><span class="sxs-lookup"><span data-stu-id="dcbaa-171">**SolverHandler.cs** will be automatically added.</span></span>
<span data-ttu-id="dcbaa-172">Di seguito è riportato un esempio di configurazione di RadialView per ottenere un comportamento di tipo "inseguimento lento graduale" proprio come con il menu di avvio della shell di HoloLens.</span><span class="sxs-lookup"><span data-stu-id="dcbaa-172">Below is an example of RadialView configuration to achieve 'lazy follow' tag-along behavior just like the Start menu in the HoloLens shell.</span></span> <span data-ttu-id="dcbaa-173">Puoi specificare la distanza minima/massima e i gradi di visualizzazione minimi/massimi.</span><span class="sxs-lookup"><span data-stu-id="dcbaa-173">You can specify the minimum/maximum distance and minimum/maximum view degrees.</span></span> <span data-ttu-id="dcbaa-174">L'esempio seguente mostra il posizionamento dell'oggetto a una distanza compresa tra 0,4 e 0,8 m e non oltre i 15°.</span><span class="sxs-lookup"><span data-stu-id="dcbaa-174">The example below shows positioning the object between 0.4 m and 0.8-m range within 15°.</span></span> <span data-ttu-id="dcbaa-175">Modifica i valori relativi al tempo di salto per rendere più veloce o più lento l'aggiornamento della posizione.</span><span class="sxs-lookup"><span data-stu-id="dcbaa-175">Adjust Lerp Time values to make the positional update faster or slower.</span></span>

<br/><img alt="MRTK Standard Shader for solver" width="400" src="images/MRTK101/MRTK_SolverRadialView.png">

<br/><img alt="Interactable radial solver" width="800" src="images/MRTK101/MRTK_RadialViewSolver.gif">

- [<span data-ttu-id="dcbaa-176">Altre informazioni sui Solver nella documentazione di MRTK</span><span class="sxs-lookup"><span data-stu-id="dcbaa-176">Learn more about Solvers in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html)

## <a name="how-to-make-an-object-face-you"></a><span data-ttu-id="dcbaa-177">Come fare in modo che un oggetto rimanga rivolto verso di te?</span><span class="sxs-lookup"><span data-stu-id="dcbaa-177">How to make an object face you?</span></span>
<span data-ttu-id="dcbaa-178">Assegnare lo script **Billboard.cs** a un oggetto.</span><span class="sxs-lookup"><span data-stu-id="dcbaa-178">Assign **Billboard.cs** script to an object.</span></span> <span data-ttu-id="dcbaa-179">In questo modo rimarrà sempre rivolto verso l'utente, qualunque sia la posizione di quest'ultimo.</span><span class="sxs-lookup"><span data-stu-id="dcbaa-179">It will always face you, whatever your position.</span></span> <span data-ttu-id="dcbaa-180">Puoi specificare l'opzione dell'asse pivot.</span><span class="sxs-lookup"><span data-stu-id="dcbaa-180">You can specify the pivot axis option.</span></span>

<br/><img alt="Image of Billboard.cs script assigned to an object with Pivot Axis option Y" width="800" src="images/MRTK101/MRTK_Billboard.png">

<br/><img alt="Billboard.cs script assigned to an object with Pivot Axis option Y" width="800" src="images/MRTK101/MRTK_Billboard.gif">


<span data-ttu-id="dcbaa-181">Sei pronto a creare esperienze straordinarie per la realtà mista?</span><span class="sxs-lookup"><span data-stu-id="dcbaa-181">Ready to create amazing experiences for mixed reality?</span></span> <span data-ttu-id="dcbaa-182">Visita le pagine seguenti e scopri di più su MRTK e sulla realtà mista.</span><span class="sxs-lookup"><span data-stu-id="dcbaa-182">Visit the pages below and learn more about MRTK and mixed reality.</span></span>

## <a name="about-the-author"></a><span data-ttu-id="dcbaa-183">Informazioni sull'autore</span><span class="sxs-lookup"><span data-stu-id="dcbaa-183">About the author</span></span>

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><span data-ttu-id="dcbaa-184"><b>Dong Yoon Park</b></span><span class="sxs-lookup"><span data-stu-id="dcbaa-184"><b>Dong Yoon Park</b></span></span><br><span data-ttu-id="dcbaa-185">Designer di esperienza utente @Microsoft</span><span class="sxs-lookup"><span data-stu-id="dcbaa-185">UX Designer @Microsoft</span></span></td>
</tr>
</table>

## <a name="next-development-checkpoint"></a><span data-ttu-id="dcbaa-186">Successivo checkpoint di sviluppo</span><span class="sxs-lookup"><span data-stu-id="dcbaa-186">Next Development Checkpoint</span></span>

<span data-ttu-id="dcbaa-187">Se si sta seguendo il percorso di checkpoint per lo sviluppo con Unity che abbiamo delineato, si stanno esplorando i blocchi predefiniti fondamentali in MRTK.</span><span class="sxs-lookup"><span data-stu-id="dcbaa-187">If you're following the Unity development checkpoint journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="dcbaa-188">Da qui è possibile passare al blocco predefinito successivo:</span><span class="sxs-lookup"><span data-stu-id="dcbaa-188">From here, you can continue to the next building block:</span></span> 

> [!div class="nextstepaction"]
> [<span data-ttu-id="dcbaa-189">Fotocamera</span><span class="sxs-lookup"><span data-stu-id="dcbaa-189">Camera</span></span>](camera-in-unity.md)

<span data-ttu-id="dcbaa-190">In alternativa, passare alle API e funzionalità della piattaforma di realtà mista:</span><span class="sxs-lookup"><span data-stu-id="dcbaa-190">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="dcbaa-191">Esperienze condivise</span><span class="sxs-lookup"><span data-stu-id="dcbaa-191">Shared experiences</span></span>](shared-experiences-in-unity.md)

<span data-ttu-id="dcbaa-192">È sempre possibile tornare ai [checkpoint per lo sviluppo con Unity](unity-development-overview.md#2-core-building-blocks) in qualsiasi momento.</span><span class="sxs-lookup"><span data-stu-id="dcbaa-192">You can always go back to the [Unity development checkpoints](unity-development-overview.md#2-core-building-blocks) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="dcbaa-193">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="dcbaa-193">See also</span></span>
* [<span data-ttu-id="dcbaa-194">Guida all'installazione di MRTK (GitHub)</span><span class="sxs-lookup"><span data-stu-id="dcbaa-194">MRTK Installation Guide (GitHub)</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html)
* [<span data-ttu-id="dcbaa-195">Mixed Reality Toolkit-Unity (MRTK) su GitHub</span><span class="sxs-lookup"><span data-stu-id="dcbaa-195">Mixed Reality Toolkit-Unity (MRTK) GitHub</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity)
* [<span data-ttu-id="dcbaa-196">Portale della documentazione di MRTK (GitHub)</span><span class="sxs-lookup"><span data-stu-id="dcbaa-196">MRTK Documentation Portal (GitHub)</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)
* [<span data-ttu-id="dcbaa-197">Linee guida per la portabilità da HoloToolkit a MRTK</span><span class="sxs-lookup"><span data-stu-id="dcbaa-197">HoloToolkit to MRTK Porting Guideline</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/HTKToMRTKPortingGuide.html)

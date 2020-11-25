---
title: MRTK 101 - Come usare Mixed Reality Toolkit Unity per le interazioni spaziali comuni (HoloLens 2, HoloLens, Windows Mixed Reality, Open VR)
description: Come usare Mixed Reality Toolkit Unity per le interazioni di base (HoloLens 2, HoloLens, Windows Mixed Reality, Open VR)
author: cre8ivepark
ms.author: dongpark
ms.date: 08/27/2019
ms.topic: article
keywords: HoloLens, MRTK, Mixed Reality Toolkit, Windows Mixed Reality, progettazione, app di esempio, controlli, visore VR realtà mista, visore VR di windows mixed reality, visore per realtà virtuale
ms.localizationpriority: high
ms.openlocfilehash: 95d8f8c52b226eda7ea1601feffc1464c2ea91c5
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2020
ms.locfileid: "94677531"
---
# <a name="mrtk-101-how-to-use-mixed-reality-toolkit-unity-for-common-spatial-interactions"></a><span data-ttu-id="f17c1-104">MRTK 101: Come usare Mixed Reality Toolkit Unity per le interazioni spaziali comuni</span><span class="sxs-lookup"><span data-stu-id="f17c1-104">MRTK 101: How to use Mixed Reality Toolkit Unity for common spatial interactions</span></span>
![MRTK](images/MRTK101/MRTK101Cover.png)

<span data-ttu-id="f17c1-106">Informazioni su come usare MRTK per ottenere alcuni dei comuni modelli di interazione più diffusi per la realtà mista.</span><span class="sxs-lookup"><span data-stu-id="f17c1-106">Learn about how to use MRTK to achieve some of the most widely used common interaction patterns in mixed reality.</span></span>

- <span data-ttu-id="f17c1-107">Come simulare le interazioni di input nell'editor di Unity?</span><span class="sxs-lookup"><span data-stu-id="f17c1-107">How to simulate input interactions in Unity editor?</span></span>
- <span data-ttu-id="f17c1-108">Come afferrare e spostare un oggetto?</span><span class="sxs-lookup"><span data-stu-id="f17c1-108">How to grab and move an object?</span></span>
- <span data-ttu-id="f17c1-109">Come ridimensionare un oggetto?</span><span class="sxs-lookup"><span data-stu-id="f17c1-109">How to resize an object?</span></span>
- <span data-ttu-id="f17c1-110">Come spostare o ruotare un oggetto con precisione?</span><span class="sxs-lookup"><span data-stu-id="f17c1-110">How to move or rotate an object with precision?</span></span>
- <span data-ttu-id="f17c1-111">Come fare in modo che un oggetto risponda agli eventi di input?</span><span class="sxs-lookup"><span data-stu-id="f17c1-111">How to make an object respond to input events?</span></span>
- <span data-ttu-id="f17c1-112">Come aggiungere feedback visivo?</span><span class="sxs-lookup"><span data-stu-id="f17c1-112">How to add visual feedback?</span></span>
- <span data-ttu-id="f17c1-113">Come aggiungere feedback audio?</span><span class="sxs-lookup"><span data-stu-id="f17c1-113">How to add audio feedback?</span></span>
- <span data-ttu-id="f17c1-114">Come usare i prefab dei pulsanti nello stile di HoloLens 2?</span><span class="sxs-lookup"><span data-stu-id="f17c1-114">How to use HoloLens 2 style button prefabs?</span></span>
- <span data-ttu-id="f17c1-115">Come fare in modo che un oggetto ti segua?</span><span class="sxs-lookup"><span data-stu-id="f17c1-115">How to make an object follow you?</span></span>
- <span data-ttu-id="f17c1-116">Come fare in modo che un oggetto rimanga rivolto verso di te?</span><span class="sxs-lookup"><span data-stu-id="f17c1-116">How to make an object face you?</span></span>

> [!NOTE]
> <span data-ttu-id="f17c1-117">Questo articolo è stato aggiornato con le modifiche apportate in [MRTK v2.5.1](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/tag/v2.5.1).</span><span class="sxs-lookup"><span data-stu-id="f17c1-117">This article has been updated to reflect the changes in [MRTK v2.5.1 release](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/tag/v2.5.1)</span></span>

<span data-ttu-id="f17c1-118">Tutto il contenuto di questa pagina può essere testato nell'editor di Unity con la simulazione di input di MRTK.</span><span class="sxs-lookup"><span data-stu-id="f17c1-118">All contents in this page can be tested in Unity editor with MRTK's Input Simulation.</span></span> <span data-ttu-id="f17c1-119">Attenersi alla [Guida all'installazione di MRTK (GitHub)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html) per installare la versione più recente di MRTK se non si ha a disposizione.</span><span class="sxs-lookup"><span data-stu-id="f17c1-119">If you haven't, follow [MRTK Installation Guide (GitHub)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html) to install the latest version of MRTK.</span></span>

## <a name="how-to-simulate-input-interactions-in-unity-editor"></a><span data-ttu-id="f17c1-120">Come simulare le interazioni di input nell'editor di Unity?</span><span class="sxs-lookup"><span data-stu-id="f17c1-120">How to simulate input interactions in Unity editor?</span></span>
<span data-ttu-id="f17c1-121">MRTK supporta la simulazione di input nell'editor.</span><span class="sxs-lookup"><span data-stu-id="f17c1-121">MRTK supports in-editor input simulation.</span></span> <span data-ttu-id="f17c1-122">È sufficiente eseguire la scena facendo clic sul pulsante di Unity per la riproduzione.</span><span class="sxs-lookup"><span data-stu-id="f17c1-122">Simply run your scene by clicking Unity's play button.</span></span> <span data-ttu-id="f17c1-123">Per simulare l'input, usa i tasti seguenti.</span><span class="sxs-lookup"><span data-stu-id="f17c1-123">Use these keys to simulate input.</span></span>
<span data-ttu-id="f17c1-124">Premi W, A, S, D per spostare la fotocamera.</span><span class="sxs-lookup"><span data-stu-id="f17c1-124">Press W, A, S, D keys to move the camera.</span></span>
<span data-ttu-id="f17c1-125">Tieni premuto il pulsante destro del mouse e sposta il puntatore del mouse per guardarti attorno.</span><span class="sxs-lookup"><span data-stu-id="f17c1-125">Hold the right mouse button and move the mouse to look around.</span></span>
<span data-ttu-id="f17c1-126">Per far comparire le mani simulate, premi la barra spaziatrice (mano destra) o il tasto MAIUSC sinistro (mano sinistra). Per mantenere le mani simulate nella visualizzazione, premi T o Y. Per ruotare le mani simulate, premi Q o E (orizzontale)/R o F (verticale).</span><span class="sxs-lookup"><span data-stu-id="f17c1-126">To bring up the simulated hands, press Space bar(Right hand) or left Shift key(Left hand) To keep simulated hands in the view, press T or Y key To rotate simulated hands, press Q or E(horizontal) / R or F(vertical)</span></span>

- [<span data-ttu-id="f17c1-127">Altre informazioni sulla simulazione di input nella documentazione di MRTK</span><span class="sxs-lookup"><span data-stu-id="f17c1-127">Learn more about Input Simulation in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/InputSimulation/InputSimulationService.html)


## <a name="how-to-grab-and-move-an-object"></a><span data-ttu-id="f17c1-128">Come afferrare e spostare un oggetto?</span><span class="sxs-lookup"><span data-stu-id="f17c1-128">How to grab and move an object?</span></span>
<span data-ttu-id="f17c1-129">Per rendere afferrabile un oggetto, assegna questi due script: **ObjectManipulator.cs** e **NearInteractionGrabbable.cs**(per afferrare l'oggetto direttamente con input di tracciamento della mano articolata). ObjectManipulator supporta sia le interazioni da vicino sia quelle da lontano.</span><span class="sxs-lookup"><span data-stu-id="f17c1-129">To make an object grabbable, assign these two scripts: **ObjectManipulator.cs** and **NearInteractionGrabbable.cs**(for direct grab with articulated hand tracking input) ObjectManipulator supports both near and far interactions.</span></span> <span data-ttu-id="f17c1-130">Puoi afferrare e spostare un oggetto con l'input di tracciamento della mano articolata di HoloLens 2 (da vicino), il raggio della mano (da lontano), il raggio del controller del movimento (da lontano), il cursore dello sguardo e la simulazione del tocco di HoloLens (da lontano).</span><span class="sxs-lookup"><span data-stu-id="f17c1-130">You can grab and move an object with HoloLens 2's articulated hand tracking input(near), hand ray(far), motion controller's beam(far), HoloLens gaze cursor & air-tap(far).</span></span>

<br/><img alt="NearInteractionGrabbable and ObjectManipulator.cs assigned to an object" width="800" src="images/MRTK101/MRTK_ManipulationHandler.png">

<br/><img alt="NearInteractionGrabbable and ObjectManipulator.cs assigned to an object for grab and move" width="800" src="images/MRTK101/MRTK_GrabMove.gif">


## <a name="how-to-resize-an-object"></a><span data-ttu-id="f17c1-131">Come ridimensionare un oggetto?</span><span class="sxs-lookup"><span data-stu-id="f17c1-131">How to resize an object?</span></span>
<span data-ttu-id="f17c1-132">**ObjectManipulator.cs** supporta il ridimensionamento e la rotazione a due mani.</span><span class="sxs-lookup"><span data-stu-id="f17c1-132">**ObjectManipulator.cs** supports two-handed scale/rotation.</span></span> <span data-ttu-id="f17c1-133">Questa operazione funziona con vari tipi di input, ad esempio l'input della mano articolata di HoloLens 2, l'input dello sguardo e del movimento di HoloLens 1 e l'input del controller del movimento del visore VR immersive di Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="f17c1-133">This works with various input types such as HoloLens 2's articulated hand input, HoloLens 1's gaze + gesture input, and Windows Mixed Reality immersive headset's motion controller input.</span></span>

- [<span data-ttu-id="f17c1-134">Altre informazioni su Object Manipulator nella documentazione di MRTK</span><span class="sxs-lookup"><span data-stu-id="f17c1-134">Learn more about Object Manipulator in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectManipulator.html)

<br/><img alt="NearInteractionGrabbable and ObjectManipulator.cs assigned to an object for manipulation" width="800" src="images/MRTK101/MRTK_ManipulationHandler.gif">

## <a name="how-to-move-or-rotate-an-object-with-precision"></a><span data-ttu-id="f17c1-135">Come spostare o ruotare un oggetto con precisione?</span><span class="sxs-lookup"><span data-stu-id="f17c1-135">How to move or rotate an object with precision?</span></span>
<span data-ttu-id="f17c1-136">Assegnare **BoundsControl.cs** a un oggetto in modo da usare il rettangolo di selezione che costituisce l'interfaccia per il ridimensionamento e la rotazione di un oggetto.</span><span class="sxs-lookup"><span data-stu-id="f17c1-136">Assign **BoundsControl.cs** to an object to use Bounding Box which is the interface for scaling and rotating an object.</span></span> <span data-ttu-id="f17c1-137">Per impostazione predefinita, vengono visualizzati i quadratini e le linee blu nello stile di HoloLens 1.</span><span class="sxs-lookup"><span data-stu-id="f17c1-137">By default, it shows HoloLens 1 style blue handles and wires.</span></span> <span data-ttu-id="f17c1-138">Per usare i quadratini animati basati su prossimità nello stile di HoloLens 2, devi assegnare prefab e materiali.</span><span class="sxs-lookup"><span data-stu-id="f17c1-138">To use HoloLens 2 style proximity-based animated handles, you need to assign prefabs and materials.</span></span> 

<br/><img alt="BoundsControl.cs assigned to an object image" width="800" src="images/MRTK101/MRTK_BoundingBox.png">

<br/><img alt="BoundsControl.cs assigned to an object gif" width="800" src="images/MRTK101/MRTK_BoundingBox.gif">

- [<span data-ttu-id="f17c1-139">Altre informazioni su Bounds Control nella documentazione di MRTK</span><span class="sxs-lookup"><span data-stu-id="f17c1-139">Learn more about Bounds Control in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundsControl.html)


## <a name="how-to-make-an-object-respond-to-input-events"></a><span data-ttu-id="f17c1-140">Come fare in modo che un oggetto risponda agli eventi di input?</span><span class="sxs-lookup"><span data-stu-id="f17c1-140">How to make an object respond to input events?</span></span>
<span data-ttu-id="f17c1-141">Assegnare **PointerHandler.cs** a un oggetto.</span><span class="sxs-lookup"><span data-stu-id="f17c1-141">Assign **PointerHandler.cs** to an object.</span></span> <span data-ttu-id="f17c1-142">Nella finestra Inspector (Controllo) sarà possibile usare gli eventi OnPointerDown(), OnPointerUp(), OnPointerClicked(), OnPointerDragged(). Per usare questi eventi in uno script, implementare **IMixedRealityPointerHandler**.</span><span class="sxs-lookup"><span data-stu-id="f17c1-142">In the inspector, you will be able to use events OnPointerDown(), OnPointerUp(), OnPointerClicked(), OnPointerDragged() To use these events in a script, implement **IMixedRealityPointerHandler**.</span></span>

<br/><img alt="PointerHandler.cs assigned to an object image" width="800" src="images/MRTK101/MRTK_PointerHandler.png">

- [<span data-ttu-id="f17c1-143">Altre informazioni sul sistema di input nella documentazione di MRTK</span><span class="sxs-lookup"><span data-stu-id="f17c1-143">Learn more about Input System in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html)

## <a name="how-to-add-visual-feedback"></a><span data-ttu-id="f17c1-144">Come aggiungere feedback visivo?</span><span class="sxs-lookup"><span data-stu-id="f17c1-144">How to add visual feedback?</span></span>
<span data-ttu-id="f17c1-145">Assegnare **Interactable.cs** a un oggetto.</span><span class="sxs-lookup"><span data-stu-id="f17c1-145">Assign **Interactable.cs** to an object.</span></span> <span data-ttu-id="f17c1-146">Nella finestra Inspector (Controllo) aggiungere l'oggetto di destinazione e creare un nuovo tema.</span><span class="sxs-lookup"><span data-stu-id="f17c1-146">In the inspector, add target object and create a new theme.</span></span> <span data-ttu-id="f17c1-147">Utilizzando i profili dei temi di Interact, puoi aggiungere facilmente feedback visivo a tutti gli stati di interazione di input disponibili.</span><span class="sxs-lookup"><span data-stu-id="f17c1-147">Using Interactable's theme profiles, you can easily add visual feedback to all available input interaction states.</span></span>

<br/><img alt="Image of PointerHandler.cs assigned to an object" width="800" src="images/MRTK101/MRTK_Interactable.png">

<br/><img alt="Interactable gif" width="800" src="images/MRTK101/MRTK_Interactable.gif">


<span data-ttu-id="f17c1-148">Interactable offre diversi tipi di temi, incluso il tema dello shader, che consente di controllare le proprietà dello shader in base allo stato di interazione.</span><span class="sxs-lookup"><span data-stu-id="f17c1-148">Interactable provides various types of themes including the shader theme which allows you to control properties of the shader per interaction state.</span></span>

- [<span data-ttu-id="f17c1-149">Altre informazioni su Interactable nella documentazione di MRTK</span><span class="sxs-lookup"><span data-stu-id="f17c1-149">Learn more about Interactable in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html)

<span data-ttu-id="f17c1-150">Un altro componente importante per il feedback visivo è lo **shader Standard di MRTK**.</span><span class="sxs-lookup"><span data-stu-id="f17c1-150">Another important building block for visual feedback is the **MRTK Standard Shader**.</span></span> <span data-ttu-id="f17c1-151">Con questo shader puoi aggiungere facilmente effetti di feedback visivo, ad esempio una luce in movimento e una luce di prossimità.</span><span class="sxs-lookup"><span data-stu-id="f17c1-151">With MRTK Standard Shader, you can easily add visual feedback effects such as hover light and proximity light.</span></span> <span data-ttu-id="f17c1-152">Poiché lo shader MRTK Standard esegue molti meno calcoli rispetto allo shader Unity Standard, puoi creare un'esperienza con ottime prestazioni.</span><span class="sxs-lookup"><span data-stu-id="f17c1-152">Since MRTK Standard shader performs significantly less computation than the Unity Standard shader, you can create a performant experience.</span></span>

<span data-ttu-id="f17c1-153">Crea un nuovo materiale e seleziona lo shader "Mixed Reality Toolkit > Standard".</span><span class="sxs-lookup"><span data-stu-id="f17c1-153">Create a new material and select the Shader 'Mixed Reality Toolkit > Standard'.</span></span> <span data-ttu-id="f17c1-154">Puoi selezionare uno dei materiali esistenti che usano lo shader MRTK Standard.</span><span class="sxs-lookup"><span data-stu-id="f17c1-154">Or you can pick one of the existing materials that use MRTK Standard Shader.</span></span>

<br/><img alt="MRTK Standard Shader image 1" width="400" src="images/MRTK101/MRTK_Shader0.png">
<br/><br/>
<img alt="MRTK Standard Shader image 2" width="800" src="images/MRTK101/MRTK_Shader1.png">

<img alt="MRTK Standard Shader image 3" width="800" src="images/MRTK101/MRTK_Shader.gif">


- [<span data-ttu-id="f17c1-155">Altre informazioni sullo shader MRTK Standard nella documentazione di MRTK</span><span class="sxs-lookup"><span data-stu-id="f17c1-155">Learn more about MRTK Standard Shader in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_MRTKStandardShader.html)

## <a name="how-to-add-audio-feedback"></a><span data-ttu-id="f17c1-156">Come aggiungere feedback audio?</span><span class="sxs-lookup"><span data-stu-id="f17c1-156">How to add audio feedback?</span></span>
<span data-ttu-id="f17c1-157">Aggiungere **AudioSource** a un oggetto.</span><span class="sxs-lookup"><span data-stu-id="f17c1-157">Add **AudioSource** to an object.</span></span> <span data-ttu-id="f17c1-158">Successivamente, negli script che espongono eventi di input, ad esempio Interactable.cs o PointerHandler.cs, assegnare l'oggetto con AudioSource all'evento e selezionare **AudioSource.PlayOneShot()** .</span><span class="sxs-lookup"><span data-stu-id="f17c1-158">Then, in the scripts that exposes input events(e.g. Interactable.cs or PointerHandler.cs), assign the object with AudioSource to the event and select **AudioSource.PlayOneShot()**.</span></span> <span data-ttu-id="f17c1-159">Puoi usare i clip audio oppure sceglierne uno dalle risorse audio di MRTK.</span><span class="sxs-lookup"><span data-stu-id="f17c1-159">You can use your audio clips or choose one from MRTK's audio assets.</span></span>

<br/><img alt="Audio Source assigned to an object. AudioSource.PlayOneShot configured in the Interactable's OnPress() and OnRelease() events." width="800" src="images/MRTK101/MRTK_Audio.png">

## <a name="how-to-use-hololens-2-style-button-prefabs"></a><span data-ttu-id="f17c1-160">Come usare i prefab dei pulsanti nello stile di HoloLens 2?</span><span class="sxs-lookup"><span data-stu-id="f17c1-160">How to use HoloLens 2 style button prefabs?</span></span>
<span data-ttu-id="f17c1-161">MRTK offre vari tipi di pulsanti nello stile della shell (sistema operativo) di HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="f17c1-161">MRTK provides various types of HoloLens 2's shell (OS) style buttons.</span></span> <span data-ttu-id="f17c1-162">Fornisce feedback visivi sofisticati, come luce di prossimità, effetto di compressione e un effetto ondulato sulla superficie del pulsante, che migliorano la fiducia dell'utente.</span><span class="sxs-lookup"><span data-stu-id="f17c1-162">It provides sophisticated visual feedbacks such as proximity light, compressing box, and a ripple effect on the button surface that improve the user's confidence.</span></span>

<br/><img alt="Interactable button" width="800" src="images/MRTK101/MRTK_Button.gif">

<span data-ttu-id="f17c1-163">È sufficiente selezionare e trascinare nella scena uno dei **prefab dei pulsanti a pressione nello stile di HoloLens 2**.</span><span class="sxs-lookup"><span data-stu-id="f17c1-163">Simply drag and drop one of the **HoloLens 2 style pressable button prefab** into your scene.</span></span> <span data-ttu-id="f17c1-164">Il prefab usa lo script Interactable.cs, che è stato introdotto in precedenza.</span><span class="sxs-lookup"><span data-stu-id="f17c1-164">The prefab uses Interactable.cs which is introduced above.</span></span> <span data-ttu-id="f17c1-165">Puoi usare gli eventi esposti, ad esempio OnClick(), in Interactable per attivare le azioni.</span><span class="sxs-lookup"><span data-stu-id="f17c1-165">You can use exposed events such as OnClick() in the Interactable to trigger actions.</span></span>

<br/><img alt="HoloLens 2 Button Prefab" width="800" src="images/MRTK101/MRTK_Button.png">

- [<span data-ttu-id="f17c1-166">Altre informazioni sui prefab dei pulsanti nella documentazione di MRTK</span><span class="sxs-lookup"><span data-stu-id="f17c1-166">Learn more about Button prefabs in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html)

## <a name="how-to-make-an-object-follow-you"></a><span data-ttu-id="f17c1-167">Come fare in modo che un oggetto ti segua?</span><span class="sxs-lookup"><span data-stu-id="f17c1-167">How to make an object follow you?</span></span>
<span data-ttu-id="f17c1-168">Assegnare lo script **RadialView.cs** o **Follow.cs** a un oggetto.</span><span class="sxs-lookup"><span data-stu-id="f17c1-168">Assign **RadialView.cs** or **Follow.cs** script to an object.</span></span> <span data-ttu-id="f17c1-169">Fa parte della serie di script Solver che consente di ottenere vari tipi di posizionamento degli oggetti nello spazio 3D.</span><span class="sxs-lookup"><span data-stu-id="f17c1-169">It is part of the Solver script series that allows you to achieve various types of object positioning in 3D space.</span></span> <span data-ttu-id="f17c1-170">Verrà aggiunto automaticamente **SolverHandler.cs**.</span><span class="sxs-lookup"><span data-stu-id="f17c1-170">**SolverHandler.cs** will be automatically added.</span></span>
<span data-ttu-id="f17c1-171">Di seguito è riportato un esempio di configurazione di RadialView per ottenere un comportamento di tipo "inseguimento lento graduale" proprio come con il menu di avvio della shell di HoloLens.</span><span class="sxs-lookup"><span data-stu-id="f17c1-171">Below is an example of RadialView configuration to achieve 'lazy follow' tag-along behavior just like the Start menu in the HoloLens shell.</span></span> <span data-ttu-id="f17c1-172">Puoi specificare la distanza minima/massima e i gradi di visualizzazione minimi/massimi.</span><span class="sxs-lookup"><span data-stu-id="f17c1-172">You can specify the minimum/maximum distance and minimum/maximum view degrees.</span></span> <span data-ttu-id="f17c1-173">L'esempio seguente mostra il posizionamento dell'oggetto in un intervallo compreso tra 0,4 e 0,8 m entro 15 gradi.</span><span class="sxs-lookup"><span data-stu-id="f17c1-173">The example below shows positioning the object between 0.4m and 0.8m range within 15°.</span></span> <span data-ttu-id="f17c1-174">Modifica i valori relativi al tempo di salto per rendere più veloce o più lento l'aggiornamento della posizione.</span><span class="sxs-lookup"><span data-stu-id="f17c1-174">Adjust Lerp Time values to make the positional update faster or slower.</span></span>

<br/><img alt="MRTK Standard Shader for solver" width="400" src="images/MRTK101/MRTK_SolverRadialView.png">

<br/><img alt="Interactable radial solver" width="800" src="images/MRTK101/MRTK_RadialViewSolver.gif">

- [<span data-ttu-id="f17c1-175">Altre informazioni sui Solver nella documentazione di MRTK</span><span class="sxs-lookup"><span data-stu-id="f17c1-175">Learn more about Solvers in the MRTK documentation</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html)

## <a name="how-to-make-an-object-face-you"></a><span data-ttu-id="f17c1-176">Come fare in modo che un oggetto rimanga rivolto verso di te?</span><span class="sxs-lookup"><span data-stu-id="f17c1-176">How to make an object face you?</span></span>
<span data-ttu-id="f17c1-177">Assegnare lo script **Billboard.cs** a un oggetto.</span><span class="sxs-lookup"><span data-stu-id="f17c1-177">Assign **Billboard.cs** script to an object.</span></span> <span data-ttu-id="f17c1-178">In questo modo sarà sempre rivolto verso di te, indipendentemente dalla posizione.</span><span class="sxs-lookup"><span data-stu-id="f17c1-178">It will always face you, regardless of your position.</span></span> <span data-ttu-id="f17c1-179">Puoi specificare l'opzione dell'asse pivot.</span><span class="sxs-lookup"><span data-stu-id="f17c1-179">You can specify the pivot axis option.</span></span>

<br/><img alt="Image of Billboard.cs script assigned to an object with Pivot Axis option Y" width="800" src="images/MRTK101/MRTK_Billboard.png">

<br/><img alt="Billboard.cs script assigned to an object with Pivot Axis option Y" width="800" src="images/MRTK101/MRTK_Billboard.gif">


<span data-ttu-id="f17c1-180">Sei pronto a creare esperienze straordinarie per la realtà mista?</span><span class="sxs-lookup"><span data-stu-id="f17c1-180">Ready to create amazing experiences for mixed reality?</span></span> <span data-ttu-id="f17c1-181">Visita le pagine seguenti e scopri di più su MRTK e sulla realtà mista.</span><span class="sxs-lookup"><span data-stu-id="f17c1-181">Visit the pages below and learn more about MRTK and mixed reality.</span></span>

## <a name="about-the-author"></a><span data-ttu-id="f17c1-182">Informazioni sull'autore</span><span class="sxs-lookup"><span data-stu-id="f17c1-182">About the author</span></span>

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><span data-ttu-id="f17c1-183"><b>Dong Yoon Park</b></span><span class="sxs-lookup"><span data-stu-id="f17c1-183"><b>Dong Yoon Park</b></span></span><br><span data-ttu-id="f17c1-184">Designer di esperienza utente @Microsoft</span><span class="sxs-lookup"><span data-stu-id="f17c1-184">UX Designer @Microsoft</span></span></td>
</tr>
</table>

## <a name="next-development-checkpoint"></a><span data-ttu-id="f17c1-185">Successivo checkpoint di sviluppo</span><span class="sxs-lookup"><span data-stu-id="f17c1-185">Next Development Checkpoint</span></span>

<span data-ttu-id="f17c1-186">Se si sta seguendo il percorso di checkpoint per lo sviluppo con Unity che abbiamo delineato, si stanno esplorando i blocchi predefiniti fondamentali in MRTK.</span><span class="sxs-lookup"><span data-stu-id="f17c1-186">If you're following the Unity development checkpoint journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="f17c1-187">Da qui è possibile passare al blocco predefinito successivo:</span><span class="sxs-lookup"><span data-stu-id="f17c1-187">From here, you can proceed to the next building block:</span></span> 

> [!div class="nextstepaction"]
> [<span data-ttu-id="f17c1-188">Fotocamera</span><span class="sxs-lookup"><span data-stu-id="f17c1-188">Camera</span></span>](camera-in-unity.md)

<span data-ttu-id="f17c1-189">In alternativa, passare alle API e funzionalità della piattaforma di realtà mista:</span><span class="sxs-lookup"><span data-stu-id="f17c1-189">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="f17c1-190">Esperienze condivise</span><span class="sxs-lookup"><span data-stu-id="f17c1-190">Shared experiences</span></span>](shared-experiences-in-unity.md)

<span data-ttu-id="f17c1-191">È sempre possibile tornare ai [checkpoint per lo sviluppo con Unity](unity-development-overview.md#2-core-building-blocks) in qualsiasi momento.</span><span class="sxs-lookup"><span data-stu-id="f17c1-191">You can always go back to the [Unity development checkpoints](unity-development-overview.md#2-core-building-blocks) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="f17c1-192">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="f17c1-192">See also</span></span>
* [<span data-ttu-id="f17c1-193">Guida all'installazione di MRTK (GitHub)</span><span class="sxs-lookup"><span data-stu-id="f17c1-193">MRTK Installation Guide (GitHub)</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html)
* [<span data-ttu-id="f17c1-194">Mixed Reality Toolkit-Unity (MRTK) su GitHub</span><span class="sxs-lookup"><span data-stu-id="f17c1-194">Mixed Reality Toolkit-Unity (MRTK) GitHub</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity)
* [<span data-ttu-id="f17c1-195">Portale della documentazione di MRTK (GitHub)</span><span class="sxs-lookup"><span data-stu-id="f17c1-195">MRTK Documentation Portal (GitHub)</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)
* [<span data-ttu-id="f17c1-196">Linee guida per la portabilità da HoloToolkit a MRTK</span><span class="sxs-lookup"><span data-stu-id="f17c1-196">HoloToolkit to MRTK Porting Guideline</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/HTKToMRTKPortingGuide.html)

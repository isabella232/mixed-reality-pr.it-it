---
title: ReleaseNotes
description: Release abbiend della versione corrente di MRTK
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: da70601a0e1d2fc2b383a9cbcfcb4b9dd2de4323
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/03/2021
ms.locfileid: "101782821"
---
# <a name="microsoft-mixed-reality-toolkit-250-release-notes"></a><span data-ttu-id="d4740-104">Note sulla versione di Microsoft Mixed Reality Toolkit 2.5.0</span><span class="sxs-lookup"><span data-stu-id="d4740-104">Microsoft Mixed Reality Toolkit 2.5.0 release notes</span></span>

- [<span data-ttu-id="d4740-105">Novità</span><span class="sxs-lookup"><span data-stu-id="d4740-105">What's new</span></span>](#whats-new)
- [<span data-ttu-id="d4740-106">Modifiche di rilievo</span><span class="sxs-lookup"><span data-stu-id="d4740-106">Breaking changes</span></span>](#breaking-changes)
- [<span data-ttu-id="d4740-107">Aggiornamento delle linee guida</span><span class="sxs-lookup"><span data-stu-id="d4740-107">Updating guidance</span></span>](../updates-deployment/Updating.md#upgrading-to-a-new-version-of-mrtk)
- [<span data-ttu-id="d4740-108">Problemi noti</span><span class="sxs-lookup"><span data-stu-id="d4740-108">Known issues</span></span>](#known-issues)

## <a name="whats-new"></a><span data-ttu-id="d4740-109">Novità</span><span class="sxs-lookup"><span data-stu-id="d4740-109">What's new</span></span>

### <a name="unity-package-manager-upm-support"></a><span data-ttu-id="d4740-110">Supporto di gestione pacchetti Unity (UPM)</span><span class="sxs-lookup"><span data-stu-id="d4740-110">Unity Package Manager (UPM) support</span></span>

<span data-ttu-id="d4740-111">Il Toolkit di realtà mista ora può essere gestito con gestione pacchetti Unity.</span><span class="sxs-lookup"><span data-stu-id="d4740-111">The Mixed Reality Toolkit can now be managed using the Unity Package Manager.</span></span>

![Pacchetto UPM MRTK Foundation](../features/Images/Packaging/MRTK_FoundationUPM.png)

> [!Note]
> <span data-ttu-id="d4740-113">Per importare i pacchetti UPM MRTK, è necessario eseguire alcuni passaggi manuali.</span><span class="sxs-lookup"><span data-stu-id="d4740-113">There are some manual steps required to import the MRTK UPM packages.</span></span> <span data-ttu-id="d4740-114">Per ulteriori informazioni, vedere il [Toolkit di realtà misto e gestione pacchetti Unity](usingupm.md) .</span><span class="sxs-lookup"><span data-stu-id="d4740-114">Please review [Mixed Reality Toolkit and Unity Package Manager](usingupm.md) for more information.</span></span>

### <a name="oculus-quest-xrsdk-support"></a><span data-ttu-id="d4740-115">Supporto per Oculus quest XRSDK</span><span class="sxs-lookup"><span data-stu-id="d4740-115">Oculus Quest XRSDK support</span></span>

<span data-ttu-id="d4740-116">MRTK supporta ora l'esecuzione di auricolari e controller di Oculus-quest usando la pipeline nativa di XR SDK.</span><span class="sxs-lookup"><span data-stu-id="d4740-116">MRTK now supports running Oculus Quest Headsets and Controllers using the native XR SDK pipeline.</span></span> <span data-ttu-id="d4740-117">Il rilevamento manuale è supportato anche con il [pacchetto Oculus Integration Unity](https://assetstore.unity.com/packages/tools/integration/oculus-integration-82022) grazie al lavoro di [Eric Provencher](https://twitter.com/prvncher) su MRTK-quest!</span><span class="sxs-lookup"><span data-stu-id="d4740-117">Hand tracking is also supported with the [Oculus Integration Unity package](https://assetstore.unity.com/packages/tools/integration/oculus-integration-82022) thanks to [Eric Provencher's](https://twitter.com/prvncher) work on MRTK-Quest!</span></span>

<span data-ttu-id="d4740-118">Per istruzioni su come distribuire il dispositivo in Oculus quest usando la nuova pipeline, vedere la Guida all' [installazione di Oculus quest](../features/CrossPlatform/OculusQuestMRTK.md) .</span><span class="sxs-lookup"><span data-stu-id="d4740-118">For instructions on how to deploy your device on the Oculus Quest using the new pipeline, see the [Oculus Quest Setup Guide](../features/CrossPlatform/OculusQuestMRTK.md)</span></span>

### <a name="scrolling-object-collection"></a><span data-ttu-id="d4740-119">Scorrimento della raccolta di oggetti</span><span class="sxs-lookup"><span data-stu-id="d4740-119">Scrolling Object Collection</span></span>

<span data-ttu-id="d4740-120">Il componente MRTK UX è stato aggiornato da una funzionalità sperimentale e offre maggiore libertà per il layout del contenuto 3D di diverse dimensioni con supporto aggiunto per gli oggetti che non dispongono di Collider collegati.</span><span class="sxs-lookup"><span data-stu-id="d4740-120">The MRTK UX component has been upgraded from an experimental feature and offers more freedom for layouting 3D content of different sizes with added support for objects that have no colliders attached.</span></span> <span data-ttu-id="d4740-121">È stata aggiunta anche una nuova opzione per disabilitare la maschera del contenuto, semplificando la creazione di prototipi.</span><span class="sxs-lookup"><span data-stu-id="d4740-121">A new option for disabling content masking was also added, making prototyping easier.</span></span>

<span data-ttu-id="d4740-122">Per ulteriori informazioni, vedere [scorrimento della raccolta di oggetti](../features/README_ScrollingObjectCollection.md) .</span><span class="sxs-lookup"><span data-stu-id="d4740-122">See [Scrolling Object Collection](../features/README_ScrollingObjectCollection.md) for more information.</span></span>

![Scorrimento della raccolta di oggetti](https://user-images.githubusercontent.com/16922045/94465118-51537900-01b7-11eb-8f8b-bf864a8fee03.gif)

### <a name="teleport-pointer-animation-handling-and-sound-improvements"></a><span data-ttu-id="d4740-124">Miglioramenti all'animazione, alla gestione e al suono del puntatore Teleport</span><span class="sxs-lookup"><span data-stu-id="d4740-124">Teleport pointer animation, handling, and sound improvements</span></span>

<span data-ttu-id="d4740-125">Il puntatore Teleport ora ha migliorato le animazioni e il feedback audio.</span><span class="sxs-lookup"><span data-stu-id="d4740-125">The teleport pointer now has improved animations and audio feedback.</span></span> <span data-ttu-id="d4740-126">È stata anche migliorata la gestione del puntatore Teleport, in modo da gestire la smussatura quando si passa dal puntatore a una superficie vicina a una superficie più lontana.</span><span class="sxs-lookup"><span data-stu-id="d4740-126">We also improved the handling of the teleport pointer so it handles smoother when transitioning from pointing at nearby surfaces to farther away surfaces.</span></span>

[https://streamable.com/3f222q](https://streamable.com/3f222q)

### <a name="input-simulation-cheat-sheet"></a><span data-ttu-id="d4740-127">Foglio informativo sulla simulazione di input</span><span class="sxs-lookup"><span data-stu-id="d4740-127">Input Simulation Cheat Sheet</span></span>

<span data-ttu-id="d4740-128">La scena HandInteractionExamples dispone ora di un collegamento configurabile per visualizzare una pagina della Guida per la simulazione di input</span><span class="sxs-lookup"><span data-stu-id="d4740-128">The HandInteractionExamples scene now has a configurable shortcut to show a help page for input simulation</span></span>

![Foglio informativo sulla simulazione di input](https://user-images.githubusercontent.com/13754172/93232433-dea8cd80-f7b4-11ea-8500-eaee202f606f.png)

### <a name="input-simulation-eye-gaze-with-mouse"></a><span data-ttu-id="d4740-130">Occhio simulazione di input con il mouse</span><span class="sxs-lookup"><span data-stu-id="d4740-130">Input Simulation Eye Gaze with mouse</span></span>

<span data-ttu-id="d4740-131">Gli utenti possono ora usare il mouse per simulare il rilevamento degli occhi.</span><span class="sxs-lookup"><span data-stu-id="d4740-131">Users can now use the Mouse for simulating eye tracking.</span></span> <span data-ttu-id="d4740-132">Vedere il `Eye Simulation Mode` campo nel profilo simulazione di input e impostarlo su mouse.</span><span class="sxs-lookup"><span data-stu-id="d4740-132">See the `Eye Simulation Mode` field in the input simulation profile and set it to Mouse.</span></span> <span data-ttu-id="d4740-133">Sostituisce il campo precedente `Simulate Eye Position`</span><span class="sxs-lookup"><span data-stu-id="d4740-133">This replaces the previous `Simulate Eye Position` field</span></span>

![Mouse con sguardo occhi](https://user-images.githubusercontent.com/39840334/87720928-892b5280-c76a-11ea-9411-73ab69fc756c.gif)

### <a name="input-simulation-motion-controller-in-editor-play-mode"></a><span data-ttu-id="d4740-135">Controller di movimento della simulazione di input in modalità di riproduzione dell'editor</span><span class="sxs-lookup"><span data-stu-id="d4740-135">Input Simulation Motion Controller in Editor Play Mode</span></span>

<span data-ttu-id="d4740-136">Gli utenti possono ora simulare il controller di movimento esattamente come le mani in modalità di riproduzione dell'editor.</span><span class="sxs-lookup"><span data-stu-id="d4740-136">Users can now simulate motion controller just like hands in editor play mode.</span></span> <span data-ttu-id="d4740-137">I pulsanti trigger, Acquisisci e menu sono attualmente supportati.</span><span class="sxs-lookup"><span data-stu-id="d4740-137">The trigger, grab and menu buttons are currently supported.</span></span>

### <a name="conical-grab-pointer"></a><span data-ttu-id="d4740-138">Puntatore a pinza conica</span><span class="sxs-lookup"><span data-stu-id="d4740-138">Conical Grab Pointer</span></span>

<span data-ttu-id="d4740-139">È ora possibile configurare i puntatori di cattura per eseguire una query per gli oggetti vicini usando un cono dal punto di recupero anziché una sfera.</span><span class="sxs-lookup"><span data-stu-id="d4740-139">Grab pointers can now be configured to query for nearby objects using a cone from the grab point rather than a sphere.</span></span> <span data-ttu-id="d4740-140">Questo comportamento è molto simile a quello dell'interfaccia predefinita Hololens 2, che esegue una query per gli oggetti vicini usando un cono.</span><span class="sxs-lookup"><span data-stu-id="d4740-140">This more closely resembles the behavior from the default Hololens 2 interface, which queries for nearby objects using a cone.</span></span> <span data-ttu-id="d4740-141">Il DefaultHoloLens2InputSystemProfile è stato anche regolato per usare il nuovo `ConicalGrabPointer` .</span><span class="sxs-lookup"><span data-stu-id="d4740-141">The DefaultHoloLens2InputSystemProfile has also been adjusted to use the new `ConicalGrabPointer`.</span></span>

![Puntatore a pinza conica](https://user-images.githubusercontent.com/39840334/82500569-72d58300-9aa8-11ea-8102-ec9a62832d4e.png)

### <a name="testutilities-package"></a><span data-ttu-id="d4740-143">Pacchetto TestUtilities</span><span class="sxs-lookup"><span data-stu-id="d4740-143">TestUtilities package</span></span>

<span data-ttu-id="d4740-144">È ora disponibile un pacchetto (Microsoft. MixedReality. Toolkit. Unity. TestUtilities. 2.5.0. file unitypackage Tools) che contiene l'infrastruttura di test PlayMode e TestMode utilizzata dal MRTK per creare test end-to-end.</span><span class="sxs-lookup"><span data-stu-id="d4740-144">There is now a package (Microsoft.MixedReality.Toolkit.Unity.TestUtilities.2.5.0.unitypackage) that contains the PlayMode and TestMode test infrastructure that the MRTK uses to create end-to-end tests.</span></span> <span data-ttu-id="d4740-145">Questa infrastruttura è stata molto utile per il team di MRTK e siamo entusiasti che i clienti lo usino per aggiungere il code coverage dei test ai propri progetti.</span><span class="sxs-lookup"><span data-stu-id="d4740-145">This infrastructure has been extremely handy for the MRTK team itself, and we're excited to have consumers use this to add test coverage to their own projects.</span></span>

<span data-ttu-id="d4740-146">Il codice seguente illustra come creare una mano di test, visualizzarla in una determinata posizione, spostarla, quindi pizzicarla e aprirla.</span><span class="sxs-lookup"><span data-stu-id="d4740-146">The following code shows how to create a test hand, show it at a certain location, move it around, and then pinch and open.</span></span>

```csharp
TestHand leftHand = new TestHand(Handedness.Left);
yield return leftHand.Show(new Vector3(-0.1f, -0.1f, 0.5f));
yield return leftHand.SetGesture(ArticulatedHandPose.GestureId.Pinch);
yield return leftHand.Move(new Vector3(0.2f, 0.2f, 0));
yield return leftHand.SetGesture(ArticulatedHandPose.GestureId.Open);
```

<span data-ttu-id="d4740-147">Per istruzioni su come scrivere un test usando questi TestUtilities, vedere la sezione relativa alla [scrittura](../Contributing/UnitTests.md#writing-tests) di test</span><span class="sxs-lookup"><span data-stu-id="d4740-147">For instructions on how to write a test using these TestUtilities, see this section on [writing tests](../Contributing/UnitTests.md#writing-tests)</span></span>

<span data-ttu-id="d4740-148">Per esempi di test esistenti che usano questa infrastruttura, vedere MRTK ' s [PlayModeTests](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MRTK/Tests/PlayModeTests)</span><span class="sxs-lookup"><span data-stu-id="d4740-148">For examples of existing tests that use this infrastructure, see MRTK's [PlayModeTests](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MRTK/Tests/PlayModeTests)</span></span>

### <a name="support-for-the-leap-motion-451-unity-modules"></a><span data-ttu-id="d4740-149">Supporto per i moduli Leap Motion 4.5.1 Unity</span><span class="sxs-lookup"><span data-stu-id="d4740-149">Support for the Leap Motion 4.5.1 Unity Modules</span></span>

<span data-ttu-id="d4740-150">È stato aggiunto il supporto per i moduli Leap Motion Unity versione 4.5.1 e il supporto per gli asset 4.4.0 è stato rimosso.</span><span class="sxs-lookup"><span data-stu-id="d4740-150">Support for the Leap Motion Unity Modules version 4.5.1 has been added and support for the 4.4.0 assets has been removed.</span></span> <span data-ttu-id="d4740-151">Le versioni attualmente supportate dei moduli Leap Motion Unity sono 4.5.0 e 4.5.1.</span><span class="sxs-lookup"><span data-stu-id="d4740-151">The current supported versions of the Leap Motion Unity Modules are 4.5.0 and 4.5.1.</span></span>

<span data-ttu-id="d4740-152">Per ulteriori informazioni, vedere [How to configure the Leap Motion Hand Tracking in MRTK](../features/CrossPlatform/LeapMotionMRTK.md) per altre informazioni.</span><span class="sxs-lookup"><span data-stu-id="d4740-152">There is also an additional step for initial Leap Motion integration, see [How to Configure the Leap Motion Hand Tracking in MRTK](../features/CrossPlatform/LeapMotionMRTK.md) for more information.</span></span>

### <a name="spatial-awareness-mesh-observer-better-handles-customization-of-materials"></a><span data-ttu-id="d4740-153">L'osservatore mesh di consapevolezza spaziale gestisce meglio la personalizzazione dei materiali</span><span class="sxs-lookup"><span data-stu-id="d4740-153">Spatial Awareness Mesh Observer better handles customization of materials</span></span>

<span data-ttu-id="d4740-154">Con questa versione, i `Windows Mixed Reality Spatial Mesh Observer` componenti e `Generic XR SDK Spatial Mesh Observer` hanno migliorato la gestione dei materiali visivi.</span><span class="sxs-lookup"><span data-stu-id="d4740-154">With this release, the `Windows Mixed Reality Spatial Mesh Observer` and the `Generic XR SDK Spatial Mesh Observer` components have improved visual material handling.</span></span> <span data-ttu-id="d4740-155">I materiali vengono ora conservati quando una mesh è stata aggiornata dall'Observer in cui, in precedenza, sono state reimpostate sul valore predefinito VisibleMaterial come configurato nel profilo.</span><span class="sxs-lookup"><span data-stu-id="d4740-155">Materials are now preserved when a mesh has been updated by the observer where, previously, they were reset to the default VisibleMaterial as configured in the profile.</span></span>

<span data-ttu-id="d4740-156">Ciò consente agli sviluppatori di modificare il materiale mesh senza sovrascrivere le modifiche in modo imprevisto.</span><span class="sxs-lookup"><span data-stu-id="d4740-156">This enables developers to alter the mesh material and not have the changes overwritten unexpectedly.</span></span>

### <a name="linkxml-created-in-the-mixedrealitytoolkitgenerated-folder"></a><span data-ttu-id="d4740-157">Link.xml creato nella cartella MixedRealityToolkit. generated</span><span class="sxs-lookup"><span data-stu-id="d4740-157">Link.xml created in the MixedRealityToolkit.Generated folder</span></span>

<span data-ttu-id="d4740-158">Con l'introduzione di MRTK Package Manager di Unity, MRTK scrive ora un `link.xml` file nella `Assets/MixedRealityToolkit.Generated` cartella, se non è presente alcun file.</span><span class="sxs-lookup"><span data-stu-id="d4740-158">With the introduction of Unity Package Manger MRTK, MRTK now writes a `link.xml` file to the `Assets/MixedRealityToolkit.Generated` folder, if none is present.</span></span> <span data-ttu-id="d4740-159">Si consiglia di aggiungere il file (e) da aggiungere `link.xml.meta` al controllo del codice sorgente.</span><span class="sxs-lookup"><span data-stu-id="d4740-159">It is recommended to add this file (and `link.xml.meta`) be added to source control.</span></span> <span data-ttu-id="d4740-160">Link.xml viene usato per influenzare la funzionalità di [rimozione del codice gestito](https://docs.unity3d.com/Manual/ManagedCodeStripping.html#LinkXML) del linker di Unity.</span><span class="sxs-lookup"><span data-stu-id="d4740-160">Link.xml is used to influence the [managed code stripping](https://docs.unity3d.com/Manual/ManagedCodeStripping.html#LinkXML) functionality of the Unity linker.</span></span>

<span data-ttu-id="d4740-161">Altre informazioni sul file MRTK link.xml sono disponibili nell'articolo relativo alla [rimozione di MRTK e codice gestito](../out-of-scope/MRTK_and_managed_code_stripping.md) .</span><span class="sxs-lookup"><span data-stu-id="d4740-161">More information on the MRTK link.xml file can be found in the [MRTK and managed code stripping](../out-of-scope/MRTK_and_managed_code_stripping.md) article.</span></span>

### <a name="unity-20193-mrtk-configuration-dialog-no-longer-attempts-to-enable-legacy-xr-support"></a><span data-ttu-id="d4740-162">Unity 2019.3 +: MRTK Configuration Dialog non tenta più di abilitare il supporto legacy XR</span><span class="sxs-lookup"><span data-stu-id="d4740-162">Unity 2019.3+: MRTK configuration dialog no longer attempts to enable legacy XR support</span></span>

<span data-ttu-id="d4740-163">Per evitare potenziali conflitti quando si usa la piattaforma XR di Unity, l'opzione per abilitare il supporto legacy XR è stata rimossa dalla finestra di dialogo di configurazione di MRTK.</span><span class="sxs-lookup"><span data-stu-id="d4740-163">To avoid potential conflicts when using Unity's XR Platform, the option to enable legacy XR support has been removed from the MRTK configuration dialog.</span></span> <span data-ttu-id="d4740-164">Se lo si desidera, è possibile abilitare il supporto legacy XR, in Unity 2019, usando **modifica**  >  **Impostazioni progetto**  >
 **lettore**  >  **XR impostazioni**  >  **realtà virtuale supportata**.</span><span class="sxs-lookup"><span data-stu-id="d4740-164">If desired, legacy XR support can be enabled, in Unity 2019, using **Edit** > **Project Settings** >
**Player** > **XR Settings** > **Virtual Reality Supported**.</span></span>

### <a name="reduction-in-initializeonload-overhead"></a><span data-ttu-id="d4740-165">Riduzione del sovraccarico del InitializeOnLoad</span><span class="sxs-lookup"><span data-stu-id="d4740-165">Reduction in InitializeOnLoad overhead</span></span>

<span data-ttu-id="d4740-166">Abbiamo lavorato per ridurre la quantità di lavoro eseguito nei gestori InitializeOnLoad, che dovrebbe causare miglioramenti nella velocità di sviluppo del ciclo interno.</span><span class="sxs-lookup"><span data-stu-id="d4740-166">We've been doing work to reduce the amount of work that runs in InitializeOnLoad handlers, which should lead to improvements in inner loop development speed.</span></span> <span data-ttu-id="d4740-167">I gestori InitializeOnLoad vengono eseguiti ogni volta che viene compilato uno script, prima di entrare in modalità di riproduzione e anche all'avvio dell'editor.</span><span class="sxs-lookup"><span data-stu-id="d4740-167">InitializeOnLoad handlers run every time a script is compiled, prior to entering play mode, and also at editor launch.</span></span> <span data-ttu-id="d4740-168">Questi gestori vengono ora eseguiti in un minor numero di casi, con conseguente miglioramento della velocità di risposta di Unity.</span><span class="sxs-lookup"><span data-stu-id="d4740-168">These handlers now run in far fewer cases, resulting in general Unity responsiveness improvements.</span></span>

<span data-ttu-id="d4740-169">In alcuni casi si è verificato un compromesso da effettuare:</span><span class="sxs-lookup"><span data-stu-id="d4740-169">In some cases there was a tradeoff that had to be made:</span></span>

- <span data-ttu-id="d4740-170">Vedere [Leap Motion Tracking Configuration](../features/CrossPlatform/LeapMotionMRTK.md) per il passaggio di integrazione aggiuntivo.</span><span class="sxs-lookup"><span data-stu-id="d4740-170">See [Leap Motion Hand Tracking Configuration](../features/CrossPlatform/LeapMotionMRTK.md) for the extra integration step.</span></span>
- <span data-ttu-id="d4740-171">Per chi usa ARFoundation, è ora disponibile un ulteriore passaggio manuale nei passaggi introduttivi.</span><span class="sxs-lookup"><span data-stu-id="d4740-171">For those who are using ARFoundation, there's now an additional manual step in its getting started steps.</span></span>
<span data-ttu-id="d4740-172">Per i nuovi passaggi, vedere [ARFoundation](../features/CrossPlatform/UsingARFoundation.md#install-required-packages) .</span><span class="sxs-lookup"><span data-stu-id="d4740-172">See [ARFoundation](../features/CrossPlatform/UsingARFoundation.md#install-required-packages) for the new steps.</span></span>
- <span data-ttu-id="d4740-173">Per coloro che useranno la [comunicazione remota olografica con la pipeline XR legacy](../features/Tools/HolographicRemoting.md#legacy-xr-setup-instructions) in HoloLens 2, è ora necessario eseguire un [passaggio manuale](../features/Tools/HolographicRemoting.md#dotnetwinrt_present-define-written-into-player-settings) .</span><span class="sxs-lookup"><span data-stu-id="d4740-173">For those who will be using [Holographic Remoting with legacy XR pipeline](../features/Tools/HolographicRemoting.md#legacy-xr-setup-instructions) on HoloLens 2, there is now a [manual step](../features/Tools/HolographicRemoting.md#dotnetwinrt_present-define-written-into-player-settings) to perform.</span></span>

### <a name="bounds-control-graduated"></a><span data-ttu-id="d4740-174">Graduazione del controllo dei limiti</span><span class="sxs-lookup"><span data-stu-id="d4740-174">Bounds control graduated</span></span>

<span data-ttu-id="d4740-175">![Il controllo dei limiti del controllo dei limiti è stato superato da quello ](../features/Images/BoundsControl/MRTK_BoundsControl_Main.png)
 [](../features/README_BoundsControl.md) sperimentale e include una serie di nuove funzionalità e tonnellate di correzioni di bug.</span><span class="sxs-lookup"><span data-stu-id="d4740-175">![Bounds control](../features/Images/BoundsControl/MRTK_BoundsControl_Main.png)
[Bounds control](../features/README_BoundsControl.md) graduated out of experimental and comes with a bunch of new features and tons of bug fixes.</span></span>
<span data-ttu-id="d4740-176">Ecco un elenco delle novità di questo aggiornamento:</span><span class="sxs-lookup"><span data-stu-id="d4740-176">Here a list of the highlights of this update:</span></span>

- <span data-ttu-id="d4740-177">le proprietà vengono suddivise in configurazioni che rendono più semplice la configurazione del controllo dei limiti</span><span class="sxs-lookup"><span data-stu-id="d4740-177">properties are split into configurations which makes it easier to set up bounds control</span></span>
- <span data-ttu-id="d4740-178">le configurazioni possono essere condivise tramite oggetti con script</span><span class="sxs-lookup"><span data-stu-id="d4740-178">configurations can be shared through scriptable objects</span></span>
- <span data-ttu-id="d4740-179">ogni proprietà di proprietà/script è configurabile in fase di esecuzione</span><span class="sxs-lookup"><span data-stu-id="d4740-179">every property / scriptable property is runtime configurable</span></span>
- <span data-ttu-id="d4740-180">il rig di controllo dei limiti non viene più ricreato nelle modifiche delle proprietà</span><span class="sxs-lookup"><span data-stu-id="d4740-180">bounds control rig isn't recreated on property changes anymore</span></span>
- <span data-ttu-id="d4740-181">supporto degli handle di traduzione</span><span class="sxs-lookup"><span data-stu-id="d4740-181">translation handles support</span></span>
- <span data-ttu-id="d4740-182">supporto completo dei vincoli tramite Gestione vincoli</span><span class="sxs-lookup"><span data-stu-id="d4740-182">full constraint support through constraint manager</span></span>
- <span data-ttu-id="d4740-183">integrazione di sistemi elastici (sperimentale)</span><span class="sxs-lookup"><span data-stu-id="d4740-183">elastics system integration (experimental)</span></span>

<span data-ttu-id="d4740-184">Il rettangolo di delimitazione precedente è ora deprecato ed è possibile aggiornare gli oggetti di gioco esistenti tramite il rettangolo di delimitazione [mediante lo strumento di migrazione](../features/Tools/MigrationWindow.md) o il [controllo riquadro](../features/README_BoundingBox.md#migrating-to-bounds-control).</span><span class="sxs-lookup"><span data-stu-id="d4740-184">The old bounding box is now deprecated and existing game objects using bounding box can be [upgraded using the migration tool](../features/Tools/MigrationWindow.md) or the [bounding box inspector](../features/README_BoundingBox.md#migrating-to-bounds-control).</span></span>

### <a name="constraint-manager-component"></a><span data-ttu-id="d4740-185">Componente Gestione vincoli</span><span class="sxs-lookup"><span data-stu-id="d4740-185">Constraint manager component</span></span>

<span data-ttu-id="d4740-186">È ora possibile usare i vincoli sia dal controllo dei limiti che dal manipolatore di oggetti tramite il nuovo [componente di gestione dei vincoli](../features/README_ConstraintManager.md).</span><span class="sxs-lookup"><span data-stu-id="d4740-186">Constraints can now be used by both, bounds control and object manipulator via the new [constraint manager component](../features/README_ConstraintManager.md).</span></span> <span data-ttu-id="d4740-187">Entrambi i componenti creeranno un gestore di vincoli per impostazione predefinita ed elaborerà automaticamente eventuali vincoli collegati.</span><span class="sxs-lookup"><span data-stu-id="d4740-187">Both components will create a constraint manager per default and process any attached constraints automatically.</span></span>

<span data-ttu-id="d4740-188">Inoltre, la gestione dei vincoli di comportamento automatico viene fornita con una modalità manuale che consente agli utenti di decidere quale vincolo deve essere elaborato.</span><span class="sxs-lookup"><span data-stu-id="d4740-188">Additionally to the automatic behavior constraint manager also comes with a manual mode that lets users decide which constraint should be processed.</span></span>
<span data-ttu-id="d4740-189">Per questo motivo il modo in cui vengono visualizzati i vincoli nel controllo proprietà è cambiato leggermente.</span><span class="sxs-lookup"><span data-stu-id="d4740-189">For this reason the way we display constraints in the property inspector changed a bit.</span></span>

<img src="../features/Images/ConstraintManager/ManualSelection.png" width="600" alt="Manual selection">

<span data-ttu-id="d4740-190">I vincoli applicati al componente sono ora visualizzati come un elenco nel componente Gestione vincoli, mentre il componente che usa Gestione vincoli ( [controllo dei limiti](../features/README_BoundsControl.md#constraint-system) o [manipolatore di oggetti](../features/README_ObjectManipulator.md#constraint-manager)) visualizzerà ora la modalità e la gestione dei vincoli selezionati (auto o Manual).</span><span class="sxs-lookup"><span data-stu-id="d4740-190">The constraints that are applied to the component are now shown as a list in the constraint manager component whereas the component using the constraint manager (either [bounds control](../features/README_BoundsControl.md#constraint-system) or [object manipulator](../features/README_ObjectManipulator.md#constraint-manager)) will now show the selected constraint manager and mode (auto or manual).</span></span>
<span data-ttu-id="d4740-191">Per altre informazioni, vedere la sezione [gestione dei vincoli](../features/README_ConstraintManager.md) nella documentazione.</span><span class="sxs-lookup"><span data-stu-id="d4740-191">For more information read the [constraint manager](../features/README_ConstraintManager.md) section in our docs.</span></span>

### <a name="hololens-2-button-material-update"></a><span data-ttu-id="d4740-192">Aggiornamento materiale del pulsante HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="d4740-192">HoloLens 2 Button material update</span></span>

<span data-ttu-id="d4740-193">Aggiornamento del materiale della gabbia anteriore del pulsante HoloLens 2 per rimuovere il colore nero in MRC.</span><span class="sxs-lookup"><span data-stu-id="d4740-193">Updated HoloLens 2 Button's front cage material to remove black color in MRC.</span></span>

![Aggiornamento materiale del pulsante HoloLens 2](https://user-images.githubusercontent.com/13754172/94341269-dcf7c900-0042-11eb-9028-e55abd2ead67.png)

### <a name="description-panel-update-movable-example-scene"></a><span data-ttu-id="d4740-195">Aggiornamento del pannello Descrizione, scena di esempio mobile</span><span class="sxs-lookup"><span data-stu-id="d4740-195">Description panel update, movable example scene</span></span>

<span data-ttu-id="d4740-196">Pannello Descrizione aggiornato.</span><span class="sxs-lookup"><span data-stu-id="d4740-196">Updated description panel.</span></span> <span data-ttu-id="d4740-197">(SceneDescriptionPanelRev. prefabbricate) la nuova progettazione offre una barra superiore afferrabile che consente all'utente di modificare o spostare l'intera scena.</span><span class="sxs-lookup"><span data-stu-id="d4740-197">(SceneDescriptionPanelRev.prefab) New design provides a grabbable top bar which allows the user to adjust/move the entire scene.</span></span>

![Aggiornamento pannello Descrizione](https://user-images.githubusercontent.com/13754172/91176366-28a21480-e71d-11ea-9e80-7e219595de9c.png)

### <a name="spatial-mesh-visualization---pulse-on-air-tap"></a><span data-ttu-id="d4740-199">Visualizzazione Mesh spaziale-Pulse on aria</span><span class="sxs-lookup"><span data-stu-id="d4740-199">Spatial mesh visualization - Pulse on air-tap</span></span>

<span data-ttu-id="d4740-200">Esempio di Pulse shader aggiornato per la mesh spaziale per la corrispondenza del comportamento della shell di HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="d4740-200">Updated pulse shader example for the spatial mesh to match HoloLens 2's shell behavior.</span></span>

![Pulse in aria](https://user-images.githubusercontent.com/13754172/90310153-d0536180-df29-11ea-939a-e9572d4f5670.gif)

### <a name="elastic-system---experimental"></a><span data-ttu-id="d4740-202">Sistema elastico: sperimentale</span><span class="sxs-lookup"><span data-stu-id="d4740-202">Elastic system - Experimental</span></span>

![System2 elastico](../features/Images/Elastics/Elastics_Main.gif)

<span data-ttu-id="d4740-204">MRTK include ora un [sistema di simulazione elastica](../features/Elastics/ElasticSystem.md) che include una vasta gamma di sottoclassi estendibili e flessibili, che offrono binding per le molle a quaternione 4-dimensionali, le molle di volume tridimensionali e i sistemi Spring lineare semplici.</span><span class="sxs-lookup"><span data-stu-id="d4740-204">MRTK now comes with an [elastic simulation system](../features/Elastics/ElasticSystem.md) that includes a wide variety of extensible and flexible subclasses, offering bindings for 4-dimensional quaternion springs, 3-dimensional volume springs and simple linear spring systems.</span></span>

<span data-ttu-id="d4740-205">Attualmente i componenti MRTK seguenti che supportano [Elastics Manager](xref:Microsoft.MixedReality.Toolkit.Experimental.Physics.ElasticsManager) possono sfruttare le funzionalità di elasticità:</span><span class="sxs-lookup"><span data-stu-id="d4740-205">Currently the following MRTK components supporting the [elastics manager](xref:Microsoft.MixedReality.Toolkit.Experimental.Physics.ElasticsManager) can leverage elastics functionality:</span></span>

- [<span data-ttu-id="d4740-206">Controllo dei limiti</span><span class="sxs-lookup"><span data-stu-id="d4740-206">Bounds control</span></span>](../features/README_BoundsControl.md#elastics-experimental)
- [<span data-ttu-id="d4740-207">Manipolatore di oggetti</span><span class="sxs-lookup"><span data-stu-id="d4740-207">Object manipulator</span></span>](../features/README_ObjectManipulator.md#elastics-experimental)  

<img src="https://user-images.githubusercontent.com/5544935/88151572-568cba00-cbaf-11ea-91c2-d6b51829b638.gif" width="38%" alt="Bounds control">
<img src="https://user-images.githubusercontent.com/5544935/88151578-58567d80-cbaf-11ea-8f96-d24f2cf0d6e9.gif" width="45.7%" alt="Boject manupulator">

### <a name="joystick-experimental"></a><span data-ttu-id="d4740-208">Joystick (sperimentale)</span><span class="sxs-lookup"><span data-stu-id="d4740-208">Joystick (Experimental)</span></span>

<span data-ttu-id="d4740-209">Esempio di interfaccia del joystick che può controllare un oggetto di destinazione di grandi dimensioni.</span><span class="sxs-lookup"><span data-stu-id="d4740-209">An example of joystick interface that can control a large target object.</span></span>

![Joystick](https://user-images.githubusercontent.com/43013191/86156887-769ef100-babb-11ea-85be-ed6a6aed89d2.png)

### <a name="color-picker-experimental"></a><span data-ttu-id="d4740-211">Selezione colori (sperimentale)</span><span class="sxs-lookup"><span data-stu-id="d4740-211">Color picker (Experimental)</span></span>

<span data-ttu-id="d4740-212">Controllo sperimentale che semplifica la modifica dei colori materiali per qualsiasi oggetto in fase di esecuzione.</span><span class="sxs-lookup"><span data-stu-id="d4740-212">An experimental control that makes it easy to change material colors on any object at runtime.</span></span>
<span data-ttu-id="d4740-213">![Selezione colori](https://user-images.githubusercontent.com/43013191/85468370-3b536e00-b561-11ea-812c-b3f7d43dd999.png)</span><span class="sxs-lookup"><span data-stu-id="d4740-213">![Color picker](https://user-images.githubusercontent.com/43013191/85468370-3b536e00-b561-11ea-812c-b3f7d43dd999.png)</span></span>

![Selezione colori](https://user-images.githubusercontent.com/43013191/85468994-fa0f8e00-b561-11ea-89f2-0810d1998518.png)

<br/><br/>

## <a name="breaking-changes"></a><span data-ttu-id="d4740-215">Modifiche che causano un'interruzione</span><span class="sxs-lookup"><span data-stu-id="d4740-215">Breaking changes</span></span>

### <a name="assembly-definition-files-changes"></a><span data-ttu-id="d4740-216">Modifiche ai file di definizione dell'assembly</span><span class="sxs-lookup"><span data-stu-id="d4740-216">Assembly Definition Files Changes</span></span>

<span data-ttu-id="d4740-217">Alcuni file asmdef vengono modificati e ora supportano solo Unity 2018.4.13 F1 o versioni successive.</span><span class="sxs-lookup"><span data-stu-id="d4740-217">Some asmdef files are changed and are now only supporting Unity 2018.4.13f1 or later.</span></span> <span data-ttu-id="d4740-218">Gli errori di compilazione vengono visualizzati quando upating MRTK 2,5 nelle versioni precedenti di Unity.</span><span class="sxs-lookup"><span data-stu-id="d4740-218">Compilation errors will show up when upating to MRTK 2.5 in earlier versions of Unity.</span></span> <span data-ttu-id="d4740-219">Per risolvere il problema, passare alla `Assets\MRTK\Providers\XRSDK\Microsoft.MixedReality.Toolkit.Providers.XRSDK.asmdef` finestra del progetto e rimuovere il riferimento mancante nel controllo.</span><span class="sxs-lookup"><span data-stu-id="d4740-219">This can be fixed by going to `Assets\MRTK\Providers\XRSDK\Microsoft.MixedReality.Toolkit.Providers.XRSDK.asmdef` in the project window and removing the missing reference in the inspector.</span></span> <span data-ttu-id="d4740-220">Ripetere questi passaggi con `Assets\MRTK\Providers\Oculus\XRSDK\Microsoft.MixedReality.Toolkit.Providers.XRSDK.Oculus.asmdef` e `Assets\MRTK\Providers\WindowsMixedReality\XRSDK\Microsoft.MixedReality.Toolkit.Providers.XRSDK.WMR.asmdef` .</span><span class="sxs-lookup"><span data-stu-id="d4740-220">Repeat those steps with `Assets\MRTK\Providers\Oculus\XRSDK\Microsoft.MixedReality.Toolkit.Providers.XRSDK.Oculus.asmdef` and `Assets\MRTK\Providers\WindowsMixedReality\XRSDK\Microsoft.MixedReality.Toolkit.Providers.XRSDK.WMR.asmdef`.</span></span> <span data-ttu-id="d4740-221">Nota è necessario annullare le modifiche sostituendo questi tre file asmdef con quelli originali, ovvero non modificati, durante l'aggiornamento a Unity 2019.</span><span class="sxs-lookup"><span data-stu-id="d4740-221">Note you must revert the changes by replacing those three asmdef files with original (i.e. unmodified) ones when upgrading to Unity 2019.</span></span>

### <a name="imixedrealitypointermediator"></a><span data-ttu-id="d4740-222">IMixedRealityPointerMediator</span><span class="sxs-lookup"><span data-stu-id="d4740-222">IMixedRealityPointerMediator</span></span>

<span data-ttu-id="d4740-223">Questa interfaccia è stata aggiornata per avere una nuova funzione:</span><span class="sxs-lookup"><span data-stu-id="d4740-223">This interface has been updated to have a new function:</span></span>

```csharp
void SetPointerPreferences(IPointerPreferences pointerPreferences);
```

<span data-ttu-id="d4740-224">Se si dispone di un Mediator del puntatore personalizzato che non esegue la sottoclasse DefaultPointerMediator, sarà necessario implementare questa nuova funzione.</span><span class="sxs-lookup"><span data-stu-id="d4740-224">If you have a custom pointer mediator that doesn't subclass DefaultPointerMediator, you will need to implement this new function.</span></span> <span data-ttu-id="d4740-225">Per ulteriori informazioni sui motivi dell'aggiunta, vedere [questo problema](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8243) .</span><span class="sxs-lookup"><span data-stu-id="d4740-225">See [this issue](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8243) for more background on why this was added.</span></span> <span data-ttu-id="d4740-226">Questo è stato aggiunto per garantire che le preferenze del puntatore vengano passate in modo esplicito al Mediator, invece di essere eseguite in modo implicito in base alla presenza di un costruttore che ha accettato un IPointerPreferences.</span><span class="sxs-lookup"><span data-stu-id="d4740-226">This was added to ensure that pointer preferences would be explicitly passed to the mediator, rather than having it be implicitly done based on the presence of a constructor that took a IPointerPreferences.</span></span>

### <a name="rest--device-portal-api"></a><span data-ttu-id="d4740-227">API portale Rest/dispositivo</span><span class="sxs-lookup"><span data-stu-id="d4740-227">Rest / Device Portal API</span></span>

<span data-ttu-id="d4740-228">La `UseSSL` proprietà statica è stata spostata da `Rest` a `DevicePortal` .</span><span class="sxs-lookup"><span data-stu-id="d4740-228">The `UseSSL` static property has been moved from `Rest` to `DevicePortal`.</span></span>

<span data-ttu-id="d4740-229">Se questa operazione è stata eseguita in precedenza...</span><span class="sxs-lookup"><span data-stu-id="d4740-229">If you did this previously...</span></span>

```csharp
Rest.UseSSL = true
```

<span data-ttu-id="d4740-230">Esegui ora...</span><span class="sxs-lookup"><span data-stu-id="d4740-230">Do this now...</span></span>

```csharp
DevicePortal.UseSSL = true
```

### <a name="linkxml"></a><span data-ttu-id="d4740-231">Link.xml</span><span class="sxs-lookup"><span data-stu-id="d4740-231">Link.xml</span></span>

<span data-ttu-id="d4740-232">Se un'applicazione utilizzava in precedenza la distribuzione NuGet di MRTK, il `link.xml` file è stato rimosso dal pacchetto di base.</span><span class="sxs-lookup"><span data-stu-id="d4740-232">If an application was previously using the NuGet distribution of the MRTK, the `link.xml` file has been removed from the Foundation package.</span></span> <span data-ttu-id="d4740-233">Per ripristinare le regole di conservazione del codice, aprendo il progetto in Unity una volta creerà un `link.xml` file predefinito in `Assets/MixedRealityToolkit.Generated` .</span><span class="sxs-lookup"><span data-stu-id="d4740-233">To restore code preservation rules, opening the project in Unity once will create a default `link.xml` file in `Assets/MixedRealityToolkit.Generated`.</span></span> <span data-ttu-id="d4740-234">È consigliabile aggiungere il file (e `link.xml.meta` ) al controllo del codice sorgente.</span><span class="sxs-lookup"><span data-stu-id="d4740-234">It is recommended that this file (and `link.xml.meta`) be added to source control.</span></span>

### <a name="transform-constraint-changes"></a><span data-ttu-id="d4740-235">Modifiche ai vincoli di trasformazione</span><span class="sxs-lookup"><span data-stu-id="d4740-235">Transform Constraint Changes</span></span>

<span data-ttu-id="d4740-236">La proprietà TargetTransform è stata contrassegnata come obsoleta perché non è stata usata dal sistema di vincoli.</span><span class="sxs-lookup"><span data-stu-id="d4740-236">TargetTransform property has been marked as obsolete as it wasn't used by constraint system.</span></span> <span data-ttu-id="d4740-237">La logica del vincolo è basata sulla trasformazione passata nei metodi Initialize e Apply.</span><span class="sxs-lookup"><span data-stu-id="d4740-237">Constraint logic is based on the transform passed into Initialize and Apply methods.</span></span> <span data-ttu-id="d4740-238">I vincoli utente derivati che si basano su questa proprietà possono memorizzare nella cache il TargetTransform nell'implementazione archiviando la trasformazione del componente vincolo per ottenere lo stesso comportamento.</span><span class="sxs-lookup"><span data-stu-id="d4740-238">Derived user constraints that rely on this property can cache the TargetTransform in their implementation by storing the transform of the constraint component to achieve the same behavior.</span></span>

<span data-ttu-id="d4740-239">Il tipo di dati iniziale archiviato del mondo `worldPoseOnManipulationStart` è stato modificato da MixedRealityPose a MixedRealityTransform, che include il valore della scala locale dell'oggetto modificato.</span><span class="sxs-lookup"><span data-stu-id="d4740-239">The stored initial world pose `worldPoseOnManipulationStart` data type has been changed from MixedRealityPose to MixedRealityTransform, which includes the local scale value of the manipulated object.</span></span> <span data-ttu-id="d4740-240">Con questa modifica non è più necessario memorizzare nella cache separatamente i valori di scala iniziali.</span><span class="sxs-lookup"><span data-stu-id="d4740-240">With this change it's not necessary to separately cache any initial scale values anymore.</span></span>

### <a name="new-property-in-imixedrealitydictationsystem"></a><span data-ttu-id="d4740-241">Nuova proprietà in IMixedRealityDictationSystem</span><span class="sxs-lookup"><span data-stu-id="d4740-241">New Property in IMixedRealityDictationSystem</span></span>

<span data-ttu-id="d4740-242">`AudioClip`È stata aggiunta una nuova proprietà all'interfaccia IMixedRealityDictationSystem.</span><span class="sxs-lookup"><span data-stu-id="d4740-242">A new property `AudioClip` has been added to the IMixedRealityDictationSystem interface.</span></span> <span data-ttu-id="d4740-243">La `AudioClip` proprietà consente l'accesso al clip audio associato alla sessione di dettatura corrente.</span><span class="sxs-lookup"><span data-stu-id="d4740-243">The `AudioClip` property enables access to the audio clip associated with the current dictation session.</span></span> <span data-ttu-id="d4740-244">Gli utenti devono implementare la proprietà nei rispettivi script che implementano l'interfaccia.</span><span class="sxs-lookup"><span data-stu-id="d4740-244">Users must implement the property in their scripts implementing the interface.</span></span>

### <a name="service-facades-turn-down"></a><span data-ttu-id="d4740-245">Le facciate del servizio si spengono</span><span class="sxs-lookup"><span data-stu-id="d4740-245">Service Facades turn down</span></span>

<span data-ttu-id="d4740-246">La [facciata dei servizi](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/06a06778e38da622b37cc299a93f16e143b7bdeb/Assets/MRTK/Core/Inspectors/MixedRealityToolkitFacadeHandler.cs) verrà disattivata in 2,5.</span><span class="sxs-lookup"><span data-stu-id="d4740-246">[Services facades](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/06a06778e38da622b37cc299a93f16e143b7bdeb/Assets/MRTK/Core/Inspectors/MixedRealityToolkitFacadeHandler.cs) are being turned down in 2.5.</span></span> <span data-ttu-id="d4740-247">Questa funzionalità è stata originariamente aggiunta per semplificare la configurazione dei profili MRTK (creando GameObject fasulli che rappresentavano ognuno dei servizi di MRTK).</span><span class="sxs-lookup"><span data-stu-id="d4740-247">This feature was originally added to make configuration of the MRTK profiles easier (by creating fake in-scene GameObjects that represented each of MRTK's services).</span></span> <span data-ttu-id="d4740-248">A lungo termine, vogliamo evitare la creazione di oggetti fittizi nel gioco e il tentativo di mantenerli sincronizzati (come la sincronizzazione dei dati e i problemi di origine di verità sono notoriamente difficili da scalare e ottenere a destra).</span><span class="sxs-lookup"><span data-stu-id="d4740-248">In the long run, we want to avoid creating fake in-game objects and trying to keep them in sync (as data sync and "source of truth" issues are notoriously difficult to scale and get right).</span></span>

<span data-ttu-id="d4740-249">In 2,5, i gestori della facciata del servizio sono conservati per garantire che l'aggiornamento del progetto venga eseguito senza problemi. tutte le facciate presenti nel progetto verranno eliminate dal gestore della facciata del servizio per assicurarsi che le scene aperte in 2,5 vengano automaticamente corrette.</span><span class="sxs-lookup"><span data-stu-id="d4740-249">In 2.5, the service facade handlers are kept around to ensure that project upgrade goes smoothly - any facades that exist in the project will be deleted by the service facade handler to ensure that scenes opened up in 2.5 get automatically fixed.</span></span>

<span data-ttu-id="d4740-250">Il codice rimanente associato alla funzionalità di facciata del servizio verrà rimosso in una versione futura.</span><span class="sxs-lookup"><span data-stu-id="d4740-250">The remaining code associated with the service facade feature will be removed in a future release.</span></span>

### <a name="addition-of-motion-controller-to-input-simulation-service"></a><span data-ttu-id="d4740-251">Aggiunta del controller di movimento al servizio di simulazione di input</span><span class="sxs-lookup"><span data-stu-id="d4740-251">Addition of Motion Controller to Input Simulation Service</span></span>

<span data-ttu-id="d4740-252">La simulazione del controller di movimento è ora disponibile nella modalità di riproduzione dell'editor lungo il lato della simulazione della mano esistente.</span><span class="sxs-lookup"><span data-stu-id="d4740-252">Motion Controller simulation is now offered in editor play mode along side the existing hand simulation.</span></span> <span data-ttu-id="d4740-253">Per abilitare questa modifica, molte funzioni/campi/proprietà correnti sono ora contrassegnate come obsolete e sono state `InputSimulationService.cs` `MixedRealityInputSimulationProfile.cs` apportate le modifiche più significative.</span><span class="sxs-lookup"><span data-stu-id="d4740-253">To enable this change, many current functions/fields/properties are now marked obsolete, with `InputSimulationService.cs` and `MixedRealityInputSimulationProfile.cs` getting the most significant changes.</span></span> <span data-ttu-id="d4740-254">La logica e il comportamento del codice pertinente rimangono in gran parte identici e la maggior parte delle funzioni obsolete e così via sono correlate alla sostituzione del riferimento a "Hand" con il termine più generico "controller", ad esempio da `DefaultHandSimulationMode` a `DefaultControllerSimulationMode` .</span><span class="sxs-lookup"><span data-stu-id="d4740-254">The logic and behavior of relevant code largely remain the same, and the majority of obsoleted functions etc. are related to replacing reference to "hand" to the more generic term "controller" (e.g. from `DefaultHandSimulationMode` to `DefaultControllerSimulationMode`).</span></span> <span data-ttu-id="d4740-255">Oltre a ottenere nuovi nomi, il tipo restituito di determinate nuove funzioni viene aggiornato in modo che corrisponda alla modifica del nome o del comportamento (ad esempio, `GetControllerDevice` in base all'origine `GetHandDevice` ora restituisce `BaseController` anziché `SimulatedHand` ).</span><span class="sxs-lookup"><span data-stu-id="d4740-255">Besides getting new names, the return type of certain new functions are updated to match the name/behavior change (e.g. `GetControllerDevice` based on the original `GetHandDevice` now returns `BaseController` instead of `SimulatedHand`).</span></span>

<span data-ttu-id="d4740-256">`IInputSimulationService` dispone ora di nuove proprietà `MotionControllerDataLeft` e `MotionControllerDataRight` .</span><span class="sxs-lookup"><span data-stu-id="d4740-256">`IInputSimulationService` now has new properties `MotionControllerDataLeft` and `MotionControllerDataRight`.</span></span> <span data-ttu-id="d4740-257">`MixedRealityInputSimulationProfile` include ora nuovi campi per il mapping della tastiera di determinati pulsanti del controller di movimento.</span><span class="sxs-lookup"><span data-stu-id="d4740-257">`MixedRealityInputSimulationProfile` now includes new fields for the keyboard mapping of certain motion controller buttons.</span></span>

## <a name="known-issues"></a><span data-ttu-id="d4740-258">Problemi noti</span><span class="sxs-lookup"><span data-stu-id="d4740-258">Known issues</span></span>

### <a name="cameracache-may-create-a-new-camera-on-shutdown"></a><span data-ttu-id="d4740-259">CameraCache può creare una nuova fotocamera alla chiusura</span><span class="sxs-lookup"><span data-stu-id="d4740-259">CameraCache may create a new camera on shutdown</span></span>

<span data-ttu-id="d4740-260">In alcune situazioni, ad esempio quando si usa il provider LeapMotion nell'editor di Unity, è possibile che CameraCache ricrei il MainCamera all'arresto.</span><span class="sxs-lookup"><span data-stu-id="d4740-260">In some situations (e.g. when using the LeapMotion provider in the Unity Editor), it is possible for the CameraCache to re-create the MainCamera on shutdown.</span></span> <span data-ttu-id="d4740-261">Per ulteriori informazioni, vedere [questo problema](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8459) .</span><span class="sxs-lookup"><span data-stu-id="d4740-261">Please see [this issue](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8459) for more information.</span></span>

### <a name="filenotfoundexception-when-examples-are-imported-via-unity-package-manager"></a><span data-ttu-id="d4740-262">FileNotFoundException quando vengono importati esempi tramite Gestione pacchetti Unity</span><span class="sxs-lookup"><span data-stu-id="d4740-262">FileNotFoundException when examples are imported via Unity Package Manager</span></span>

<span data-ttu-id="d4740-263">A seconda della lunghezza del percorso del progetto, l'importazione di esempi tramite Gestione pacchetti Unity può generare messaggi FileNotFoundException nella console di Unity.</span><span class="sxs-lookup"><span data-stu-id="d4740-263">Depending on the length of the project path, importing examples via Unity Package Manager may generate FileNotFoundException messages in the Unity Console.</span></span> <span data-ttu-id="d4740-264">La cui origine è il percorso del file "mancante" che supera MAX_PATH (256 caratteri).</span><span class="sxs-lookup"><span data-stu-id="d4740-264">The cause of this is the path to the "missing" file being longer than MAX_PATH (256 characters).</span></span> <span data-ttu-id="d4740-265">Per risolvere il progetto, abbreviare la lunghezza del percorso del progetto.</span><span class="sxs-lookup"><span data-stu-id="d4740-265">To resolve, please shorten the length of the project path.</span></span>

### <a name="no-spatializer-was-specified-the-application-will-not-support-spatial-sound"></a><span data-ttu-id="d4740-266">Non è stato specificato alcun Spatializer.</span><span class="sxs-lookup"><span data-stu-id="d4740-266">No spatializer was specified.</span></span> <span data-ttu-id="d4740-267">L'applicazione non supporterà il suono spaziale</span><span class="sxs-lookup"><span data-stu-id="d4740-267">The application will not support Spatial Sound</span></span>

<span data-ttu-id="d4740-268">Se non è configurato un Spatializer audio, viene visualizzato un avviso "nessun Spatializer specificato".</span><span class="sxs-lookup"><span data-stu-id="d4740-268">A "No spatializer was specified" warning will appear if an audio spatializer is not configured.</span></span> <span data-ttu-id="d4740-269">Questo problema può verificarsi se non è installato alcun pacchetto XR, perché Unity include spatializers in questi pacakges.</span><span class="sxs-lookup"><span data-stu-id="d4740-269">This can occur if no XR package is installed, as Unity includes spatializers in these pacakges.</span></span>

<span data-ttu-id="d4740-270">Per risolverlo, verificare quanto segue:</span><span class="sxs-lookup"><span data-stu-id="d4740-270">To resolve, please ensure that:</span></span>

- <span data-ttu-id="d4740-271">**Finestra**  >  di In **Gestione pacchetti** sono installati uno o più pacchetti XR</span><span class="sxs-lookup"><span data-stu-id="d4740-271">**Window** > **Package Manager** has one or more XR packages installed</span></span>
- <span data-ttu-id="d4740-272">Toolkit per realtà **mista**  >  **Utilità**  >  di **Configurare il progetto Unity** ed effettuare una selezione per **Spatializer audio**</span><span class="sxs-lookup"><span data-stu-id="d4740-272">**Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project** and make a selection for **Audio Spatializer**</span></span>

  ![Seleziona Apatializer audio](../features/Images/ReleaseNotes/SpatializerSelection.png)

### <a name="nullreferenceexception-object-reference-not-set-to-an-instance-of-an-object-scenetransitionserviceinitialize"></a><span data-ttu-id="d4740-274">NullReferenceException: riferimento all'oggetto non impostato su un'istanza di un oggetto (SceneTransitionService.Initialize)</span><span class="sxs-lookup"><span data-stu-id="d4740-274">NullReferenceException: Object reference not set to an instance of an object (SceneTransitionService.Initialize)</span></span>

<span data-ttu-id="d4740-275">In alcune situazioni, l'apertura `EyeTrackingDemo-00-RootScene` può causare un'eccezione NullReferenceException nel metodo Initialize della classe SceneTransitionService.</span><span class="sxs-lookup"><span data-stu-id="d4740-275">In some situations, opening `EyeTrackingDemo-00-RootScene` may cause a NullReferenceException in the Initialize method of the SceneTransitionService class.</span></span>
<span data-ttu-id="d4740-276">Questo errore è dovuto al fatto che il profilo di configurazione del servizio transizione della scena non è stato impostato.</span><span class="sxs-lookup"><span data-stu-id="d4740-276">This error is due to the Scene Transition Service's configuration profile being unset.</span></span> <span data-ttu-id="d4740-277">Per risolverlo, attenersi alla procedura seguente:</span><span class="sxs-lookup"><span data-stu-id="d4740-277">To resolve, please use the following steps:</span></span>

- <span data-ttu-id="d4740-278">Passare all' `MixedRealityToolkit` oggetto nella gerarchia</span><span class="sxs-lookup"><span data-stu-id="d4740-278">Navigate to the `MixedRealityToolkit` object in the Hierarchy</span></span>
- <span data-ttu-id="d4740-279">Nella finestra di controllo selezionare `Extensions`</span><span class="sxs-lookup"><span data-stu-id="d4740-279">In the Inspector window, select `Extensions`</span></span>
- <span data-ttu-id="d4740-280">Se non è espanso, espandere `Scene Transition Service`</span><span class="sxs-lookup"><span data-stu-id="d4740-280">If not expanded, expand `Scene Transition Service`</span></span>
- <span data-ttu-id="d4740-281">Impostare il valore di `Configuration Profile` su **MRTKExamplesHubSceneTransitionServiceProfile**</span><span class="sxs-lookup"><span data-stu-id="d4740-281">Set the value of `Configuration Profile` to **MRTKExamplesHubSceneTransitionServiceProfile**</span></span>

<img src="../features/Images/ReleaseNotes/FixSceneTransitionProfile.png" width="500px" alt="Fix scene transition">

### <a name="oculus-quest"></a><span data-ttu-id="d4740-282">Oculus-ricerca</span><span class="sxs-lookup"><span data-stu-id="d4740-282">Oculus Quest</span></span>

<span data-ttu-id="d4740-283">Attualmente esiste un problema noto per l'uso del [plug-in Oculus XR con quando si fa riferimento a piattaforme autonome](https://forum.unity.com/threads/unable-to-start-oculus-xr-plugin.913883/).</span><span class="sxs-lookup"><span data-stu-id="d4740-283">There is currently a known issue for using the [Oculus XR plugin with when targeting Standalone platforms](https://forum.unity.com/threads/unable-to-start-oculus-xr-plugin.913883/).</span></span>  <span data-ttu-id="d4740-284">Per gli aggiornamenti, vedere le note sulla versione, i forum e la registrazione di Oculus bug.</span><span class="sxs-lookup"><span data-stu-id="d4740-284">Check the Oculus bug tracker/forums/release notes for updates.</span></span>

<span data-ttu-id="d4740-285">Il bug è identificato da questo set di 3 errori:</span><span class="sxs-lookup"><span data-stu-id="d4740-285">The bug is signified with this set of 3 errors:</span></span>

![Errore del plug-in Oculus XR](https://forum.unity.com/attachments/erori-unity-png.644204/)

### <a name="unityui-and-textmeshpro"></a><span data-ttu-id="d4740-287">UnityUI e TextMeshPro</span><span class="sxs-lookup"><span data-stu-id="d4740-287">UnityUI and TextMeshPro</span></span>

<span data-ttu-id="d4740-288">Esiste un problema noto per le versioni più recenti di TextMeshPro (1.5.0 + o 2.1.1 +), in cui la dimensione del carattere predefinita per i menu a discesa e la spaziatura dei caratteri in grassetto è stata modificata.</span><span class="sxs-lookup"><span data-stu-id="d4740-288">There's a known issue for newer versions of TextMeshPro (1.5.0+ or 2.1.1+), where the default font size for dropdowns and bold font character spacing has been altered.</span></span>

![Immagine TMP](https://user-images.githubusercontent.com/68253937/93158069-4d582f00-f6c0-11ea-87ad-94d0ba3ba6e5.png)

<span data-ttu-id="d4740-290">Per risolvere il problema, è possibile effettuare il downgrade a una versione precedente di TextMeshPro.</span><span class="sxs-lookup"><span data-stu-id="d4740-290">This can be worked around by downgrading to an earlier version of TextMeshPro.</span></span> <span data-ttu-id="d4740-291">Per ulteriori informazioni, vedere la pagina relativa al [problema #8556](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8556) .</span><span class="sxs-lookup"><span data-stu-id="d4740-291">See [issue #8556](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/8556) for more details.</span></span>

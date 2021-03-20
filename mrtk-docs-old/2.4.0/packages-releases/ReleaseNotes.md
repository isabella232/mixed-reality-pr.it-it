---
title: ReleaseNotes
description: Release abbiend della versione corrente di MRTK
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
ms.localizationpriority: medium
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: 262beea344b7b6a73328e6987acb60610e814f60
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2021
ms.locfileid: "104687771"
---
# <a name="microsoft-mixed-reality-toolkit-release-notes"></a><span data-ttu-id="95e5c-104">Note sulla versione di Microsoft Mixed Reality Toolkit</span><span class="sxs-lookup"><span data-stu-id="95e5c-104">Microsoft Mixed Reality Toolkit release notes</span></span>

- [<span data-ttu-id="95e5c-105">Novità</span><span class="sxs-lookup"><span data-stu-id="95e5c-105">What's new</span></span>](#whats-new-in-240)
- [<span data-ttu-id="95e5c-106">Modifiche di rilievo</span><span class="sxs-lookup"><span data-stu-id="95e5c-106">Breaking changes</span></span>](#breaking-changes-in-240)
- [<span data-ttu-id="95e5c-107">Aggiornamento delle linee guida</span><span class="sxs-lookup"><span data-stu-id="95e5c-107">Updating guidance</span></span>](upgrading.md#upgrading-to-a-new-version-of-mrtk)
- [<span data-ttu-id="95e5c-108">Problemi noti</span><span class="sxs-lookup"><span data-stu-id="95e5c-108">Known issues</span></span>](#known-issues-in-240)

<span data-ttu-id="95e5c-109">Questa versione di Microsoft Mixed Reality Toolkit supporta i dispositivi e le piattaforme seguenti.</span><span class="sxs-lookup"><span data-stu-id="95e5c-109">This release of the Microsoft Mixed Reality Toolkit supports the following devices and platforms.</span></span>

- <span data-ttu-id="95e5c-110">Microsoft HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="95e5c-110">Microsoft HoloLens 2</span></span>
- <span data-ttu-id="95e5c-111">Microsoft HoloLens (1a generazione)</span><span class="sxs-lookup"><span data-stu-id="95e5c-111">Microsoft HoloLens (1st gen)</span></span>
- <span data-ttu-id="95e5c-112">Cuffie immersive della realtà mista di Windows</span><span class="sxs-lookup"><span data-stu-id="95e5c-112">Windows Mixed Reality Immersive headsets</span></span>
- <span data-ttu-id="95e5c-113">OpenVR</span><span class="sxs-lookup"><span data-stu-id="95e5c-113">OpenVR</span></span>
- <span data-ttu-id="95e5c-114">Sperimentale Piattaforma Unity 2019,3 XR</span><span class="sxs-lookup"><span data-stu-id="95e5c-114">(Experimental) Unity 2019.3 XR platform</span></span>
- <span data-ttu-id="95e5c-115">Mobile AR tramite Unity AR Foundation</span><span class="sxs-lookup"><span data-stu-id="95e5c-115">Mobile AR via Unity AR Foundation</span></span>
  - <span data-ttu-id="95e5c-116">Android</span><span class="sxs-lookup"><span data-stu-id="95e5c-116">Android</span></span>
  - <span data-ttu-id="95e5c-117">iOS</span><span class="sxs-lookup"><span data-stu-id="95e5c-117">iOS</span></span>
- <span data-ttu-id="95e5c-118">Tracciamento della mano Ultraleap</span><span class="sxs-lookup"><span data-stu-id="95e5c-118">Ultraleap Hand Tracking</span></span>

<span data-ttu-id="95e5c-119">Il software seguente è obbligatorio.</span><span class="sxs-lookup"><span data-stu-id="95e5c-119">The following software is required.</span></span>

- <span data-ttu-id="95e5c-120">[Microsoft Visual Studio](https://visualstudio.microsoft.com) (2017 o 2019) Community Edition o versione successiva</span><span class="sxs-lookup"><span data-stu-id="95e5c-120">[Microsoft Visual Studio](https://visualstudio.microsoft.com) (2017 or 2019) Community Edition or higher</span></span>
- <span data-ttu-id="95e5c-121">[Windows 10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk) 18362 o versione successiva (installato dal programma di installazione di Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="95e5c-121">[Windows 10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk) 18362 or later (installed by the Visual Studio Installer)</span></span>
- <span data-ttu-id="95e5c-122">[Unity](https://unity3d.com/get-unity/download) 2018,4 LTS o 2019 (2019,3 consigliato)</span><span class="sxs-lookup"><span data-stu-id="95e5c-122">[Unity](https://unity3d.com/get-unity/download) 2018.4 LTS or 2019 (2019.3 recommended)</span></span>

<span data-ttu-id="95e5c-123">**Scaricare**</span><span class="sxs-lookup"><span data-stu-id="95e5c-123">**Download**</span></span>

<span data-ttu-id="95e5c-124">[Microsoft. MixedReality. Toolkit. Unity. Foundation. 2.4.0. file unitypackage Tools](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.4.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.4.0.unitypackage) 
 [Microsoft. MixedReality. Toolkit. Unity. Extensions. 2.4.0. file unitypackage Tools](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.4.0/Microsoft.MixedReality.Toolkit.Unity.Extensions.2.4.0.unitypackage) 
 [Microsoft. MixedReality. Toolkit. Unity. examples. 2.4.0. file unitypackage Tools](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.4.0/Microsoft.MixedReality.Toolkit.Unity.Examples.2.4.0.unitypackage) 
 [Microsoft. MixedReality. Toolkit. Unity. Tools. 2.4.0. file unitypackage Tools](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.4.0/Microsoft.MixedReality.Toolkit.Unity.Tools.2.4.0.unitypackage)</span><span class="sxs-lookup"><span data-stu-id="95e5c-124">[Microsoft.MixedReality.Toolkit.Unity.Foundation.2.4.0.unitypackage](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.4.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.4.0.unitypackage)
[Microsoft.MixedReality.Toolkit.Unity.Extensions.2.4.0.unitypackage](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.4.0/Microsoft.MixedReality.Toolkit.Unity.Extensions.2.4.0.unitypackage)
[Microsoft.MixedReality.Toolkit.Unity.Examples.2.4.0.unitypackage](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.4.0/Microsoft.MixedReality.Toolkit.Unity.Examples.2.4.0.unitypackage)
[Microsoft.MixedReality.Toolkit.Unity.Tools.2.4.0.unitypackage](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.4.0/Microsoft.MixedReality.Toolkit.Unity.Tools.2.4.0.unitypackage)</span></span>

<span data-ttu-id="95e5c-125">Altri file sono disponibili nella pagina della [versione di GitHub](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/tag/v2.4.0)</span><span class="sxs-lookup"><span data-stu-id="95e5c-125">Other files can be found on the [GitHub release page](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/tag/v2.4.0)</span></span>

<span data-ttu-id="95e5c-126">**Requisiti di NuGet**</span><span class="sxs-lookup"><span data-stu-id="95e5c-126">**NuGet requirements**</span></span>

<span data-ttu-id="95e5c-127">Se si importano i [pacchetti NuGet del Toolkit per realtà mista](../reference-docs/MRTKNuGetPackage.md), è consigliabile utilizzare il seguente software.</span><span class="sxs-lookup"><span data-stu-id="95e5c-127">If importing the [Mixed Reality Toolkit NuGet packages](../reference-docs/MRTKNuGetPackage.md), the following software is recommended.</span></span>

- [<span data-ttu-id="95e5c-128">NuGet per Unity 2.0.0 o versione successiva</span><span class="sxs-lookup"><span data-stu-id="95e5c-128">NuGet for Unity 2.0.0 or newer</span></span>](https://github.com/GlitchEnzo/NuGetForUnity/releases/latest)

### <a name="whats-new-in-240"></a><span data-ttu-id="95e5c-129">Novità di 2.4.0</span><span class="sxs-lookup"><span data-stu-id="95e5c-129">What's new in 2.4.0</span></span>

<span data-ttu-id="95e5c-130">**Supporto di Ultraleap Hand Tracking**</span><span class="sxs-lookup"><span data-stu-id="95e5c-130">**Ultraleap Hand Tracking Support**</span></span>

<span data-ttu-id="95e5c-131">La [provider di dati di movimento intercalare](../features/CrossPlatform/LeapMotionMRTK.md) consente di tenere traccia della mano articolata per le applicazioni VR ed è utile anche per la prototipazione rapida dell'editor.</span><span class="sxs-lookup"><span data-stu-id="95e5c-131">The [Leap Motion Data Provider](../features/CrossPlatform/LeapMotionMRTK.md) enables articulated hand tracking for VR applications and is also useful for rapid prototyping in the editor.</span></span>  <span data-ttu-id="95e5c-132">Il provider di dati può essere configurato in modo da usare il controller di movimento Leap montato su un auricolare o posizionato su una scrivania.</span><span class="sxs-lookup"><span data-stu-id="95e5c-132">The data provider can be configured to use the Leap Motion Controller mounted on a headset or placed on a desk face up.</span></span>

<span data-ttu-id="95e5c-133">Per utilizzare questo provider di dati, è necessario un [controller di movimento Leap](https://www.ultraleap.com/product/leap-motion-controller/) .</span><span class="sxs-lookup"><span data-stu-id="95e5c-133">A [Leap Motion Controller](https://www.ultraleap.com/product/leap-motion-controller/) is required to use this data provider.</span></span>

![LeapMotionIntroGif](../features/Images/CrossPlatform/LeapMotion/LeapMotionSideBySide2.gif)

<span data-ttu-id="95e5c-135">**Finestra di migrazione**</span><span class="sxs-lookup"><span data-stu-id="95e5c-135">**Migration window**</span></span>

![Finestra di migrazione](../features/Images/MigrationWindow/MRTK_Migration_Window.png)

<span data-ttu-id="95e5c-137">MRTK ora è dotato di uno strumento di migrazione che consente di aggiornare i componenti deprecati alle versioni più recenti e di garantire il funzionamento del codice esistente anche quando MRTK apporta modifiche di rilievo.</span><span class="sxs-lookup"><span data-stu-id="95e5c-137">MRTK now comes with a migration tool that will help you upgrade deprecated components to their newer versions and to keep existing code working even as MRTK makes breaking changes.</span></span>

<span data-ttu-id="95e5c-138">**È in genere consigliabile eseguire lo strumento di migrazione dopo aver effettuato il pull di una nuova versione di MRTK** per garantire che la maggior parte del progetto verrà automaticamente adattata al codice MRTK più recente.</span><span class="sxs-lookup"><span data-stu-id="95e5c-138">**It is generally recommended to run the migration tool after pulling a new version of MRTK** to ensure that as much of your project will be auto-adjusted to the latest MRTK code.</span></span>

<span data-ttu-id="95e5c-139">La [finestra di migrazione](../features/Tools/MigrationWindow.md) si trova in "Mixed Reality Toolkit > Utilities > finestra di migrazione".</span><span class="sxs-lookup"><span data-stu-id="95e5c-139">The [migration window](../features/Tools/MigrationWindow.md) can be found in 'Mixed Reality Toolkit > Utilities > Migration Window'.</span></span> <span data-ttu-id="95e5c-140">Fa parte del pacchetto di **strumenti** .</span><span class="sxs-lookup"><span data-stu-id="95e5c-140">It it part of the **Tools** package.</span></span>

<span data-ttu-id="95e5c-141">Attualmente supporta:</span><span class="sxs-lookup"><span data-stu-id="95e5c-141">It currently supports:</span></span>

- <span data-ttu-id="95e5c-142">Aggiornamento di ManipulationHandler e BoundingBox alle versioni più recenti ObjectManipulator e BoundsControl.</span><span class="sxs-lookup"><span data-stu-id="95e5c-142">Upgrading ManipulationHandler and BoundingBox to their newer versions ObjectManipulator and BoundsControl.</span></span>
- <span data-ttu-id="95e5c-143">Aggiornamento delle icone dei pulsanti personalizzati per funzionare correttamente con il nuovo Helper config del pulsante.</span><span class="sxs-lookup"><span data-stu-id="95e5c-143">Updating custom button icons to work correctly with the new Button Config Helper.</span></span>

<span data-ttu-id="95e5c-144">Si noti che BoundsControl è ancora in fase sperimentale e pertanto le API o le proprietà potrebbero ancora cambiare nella versione successiva.</span><span class="sxs-lookup"><span data-stu-id="95e5c-144">Note that BoundsControl is still in experimental phase and therefore API or properties might still change in the next version.</span></span>

<span data-ttu-id="95e5c-145">**Modifiche al layout della cartella MRTK**</span><span class="sxs-lookup"><span data-stu-id="95e5c-145">**MRTK folder layout changes**</span></span>

<span data-ttu-id="95e5c-146">Questa versione di MRTK modifica il layout della struttura di cartelle MRTK.</span><span class="sxs-lookup"><span data-stu-id="95e5c-146">This version of MRTK modifies the layout of the MRTK folder structure.</span></span> <span data-ttu-id="95e5c-147">Questa modifica incapsula tutto il codice MRTK in una singola gerarchia di cartelle e riduce la lunghezza totale del percorso di tutti i file MRTK.</span><span class="sxs-lookup"><span data-stu-id="95e5c-147">This change encapsulates all MRTK code into a single folder hierarchy and reduces the total path length of all MRTK files.</span></span>

| <span data-ttu-id="95e5c-148">Cartella precedente</span><span class="sxs-lookup"><span data-stu-id="95e5c-148">Previous Folder</span></span> | <span data-ttu-id="95e5c-149">Nuova cartella</span><span class="sxs-lookup"><span data-stu-id="95e5c-149">New Folder</span></span> |
| --- | --- |
| <span data-ttu-id="95e5c-150">MixedRealityToolkit</span><span class="sxs-lookup"><span data-stu-id="95e5c-150">MixedRealityToolkit</span></span> | <span data-ttu-id="95e5c-151">MRTK\Core</span><span class="sxs-lookup"><span data-stu-id="95e5c-151">MRTK\Core</span></span> |
| <span data-ttu-id="95e5c-152">MixedRealityToolkit. examples</span><span class="sxs-lookup"><span data-stu-id="95e5c-152">MixedRealityToolkit.Examples</span></span> | <span data-ttu-id="95e5c-153">MRTK\Examples</span><span class="sxs-lookup"><span data-stu-id="95e5c-153">MRTK\Examples</span></span> |
| <span data-ttu-id="95e5c-154">MixedRealityToolkit. Extensions</span><span class="sxs-lookup"><span data-stu-id="95e5c-154">MixedRealityToolkit.Extensions</span></span> | <span data-ttu-id="95e5c-155">MRTK\Extensions</span><span class="sxs-lookup"><span data-stu-id="95e5c-155">MRTK\Extensions</span></span> |
| <span data-ttu-id="95e5c-156">MixedRealityToolkit. Providers</span><span class="sxs-lookup"><span data-stu-id="95e5c-156">MixedRealityToolkit.Providers</span></span> | <span data-ttu-id="95e5c-157">MRTK\Providers</span><span class="sxs-lookup"><span data-stu-id="95e5c-157">MRTK\Providers</span></span> |
| <span data-ttu-id="95e5c-158">MixedRealityToolkit. SDK</span><span class="sxs-lookup"><span data-stu-id="95e5c-158">MixedRealityToolkit.SDK</span></span> | <span data-ttu-id="95e5c-159">MRTK\SDK</span><span class="sxs-lookup"><span data-stu-id="95e5c-159">MRTK\SDK</span></span> |
| <span data-ttu-id="95e5c-160">MixedRealityToolkit. Services</span><span class="sxs-lookup"><span data-stu-id="95e5c-160">MixedRealityToolkit.Services</span></span> | <span data-ttu-id="95e5c-161">MRTK\Services</span><span class="sxs-lookup"><span data-stu-id="95e5c-161">MRTK\Services</span></span> |
| <span data-ttu-id="95e5c-162">MixedRealityToolkit. test</span><span class="sxs-lookup"><span data-stu-id="95e5c-162">MixedRealityToolkit.Tests</span></span> | <span data-ttu-id="95e5c-163">MRTK\Tests</span><span class="sxs-lookup"><span data-stu-id="95e5c-163">MRTK\Tests</span></span> |
| <span data-ttu-id="95e5c-164">MixedRealityToolkit. Tools</span><span class="sxs-lookup"><span data-stu-id="95e5c-164">MixedRealityToolkit.Tools</span></span> | <span data-ttu-id="95e5c-165">MRTK\Tools</span><span class="sxs-lookup"><span data-stu-id="95e5c-165">MRTK\Tools</span></span> |

> [!IMPORTANT]
> <span data-ttu-id="95e5c-166">`MixedRealityToolkit.Generated`Contiene i file generati dal cliente e rimane invariato.</span><span class="sxs-lookup"><span data-stu-id="95e5c-166">The `MixedRealityToolkit.Generated` contains customer generated files and remains unchanged.</span></span>

<span data-ttu-id="95e5c-167">**Casella degli strumenti MRTK**</span><span class="sxs-lookup"><span data-stu-id="95e5c-167">**MRTK Toolbox**</span></span>

![Casella degli strumenti MRTK](../features/Images/Tools/MRTKToolboxWindow.png)

<span data-ttu-id="95e5c-169">La [casella degli strumenti MRTK](../features/README_Toolbox.md) è un'utilità della finestra dell'editor di Unity che semplifica l'individuazione e la generazione di componenti prefabbricati di MRTK UX nella scena corrente.</span><span class="sxs-lookup"><span data-stu-id="95e5c-169">The [MRTK Toolbox](../features/README_Toolbox.md) is a Unity editor window utility that makes it easy to discover and spawn MRTK UX prefab components into the current scene.</span></span> <span data-ttu-id="95e5c-170">Gli elementi possono essere filtrati nella visualizzazione tramite la barra di ricerca nella parte superiore della finestra.</span><span class="sxs-lookup"><span data-stu-id="95e5c-170">Items can be filtered in view by using the search bar at the top of the window.</span></span> <span data-ttu-id="95e5c-171">La finestra casella degli strumenti è progettata per generare MRTK prefabbricati predefiniti nella scena corrente.</span><span class="sxs-lookup"><span data-stu-id="95e5c-171">The toolbox window is designed to spawn MRTK out-of-box prefabs into the current scene.</span></span>

<span data-ttu-id="95e5c-172">**Toccare per posizionare**</span><span class="sxs-lookup"><span data-stu-id="95e5c-172">**Tap to Place**</span></span>

<span data-ttu-id="95e5c-173">[Toccare per posizionare](../features/README_TapToPlace.md) è un componente di interazione molto usato per posizionare facilmente un oggetto gioco sulla superficie.</span><span class="sxs-lookup"><span data-stu-id="95e5c-173">[Tap to Place](../features/README_TapToPlace.md) is a far interaction component used to easily place a game object on surface.</span></span> <span data-ttu-id="95e5c-174">Toccare per posizionare usa una combinazione di due clic e movimento Head per inserire un oggetto.</span><span class="sxs-lookup"><span data-stu-id="95e5c-174">Tap to Place uses a combination of two clicks and head movement to place an object.</span></span>

![TapToPlace](../features/Images/Solver/TapToPlace/TapToPlaceIntroGif.gif)

<span data-ttu-id="95e5c-176">**Helper config Button aggiunto ai pulsanti** 
 ![ stampabili Button config helper ](https://user-images.githubusercontent.com/9789716/70167111-e3175600-167a-11ea-9c52-444509c06105.gif) questa nuova funzionalità semplifica la modifica dell'icona e del testo dei pulsanti.</span><span class="sxs-lookup"><span data-stu-id="95e5c-176">**Button Config Helper added to Pressable Buttons**
![Button Config Helper](https://user-images.githubusercontent.com/9789716/70167111-e3175600-167a-11ea-9c52-444509c06105.gif) This new feature makes it easy to change the icon and text of the buttons.</span></span> <span data-ttu-id="95e5c-177">L'icona supporta la trama del tipo di carattere SDF di quad, sprite e TextMesh Pro.</span><span class="sxs-lookup"><span data-stu-id="95e5c-177">Icon supports quad, sprite, and TextMesh Pro's SDF font texture.</span></span> <span data-ttu-id="95e5c-178">Per informazioni dettagliate, vedere la [documentazione del pulsante](../features/README_Button.md#how-to-change-the-icon-and-text) di MRTK.</span><span class="sxs-lookup"><span data-stu-id="95e5c-178">See MRTK's [Button documentation](../features/README_Button.md#how-to-change-the-icon-and-text) for the details.</span></span>

<span data-ttu-id="95e5c-179">**Nuovi pulsanti di alternanza di stile HoloLens 2-CheckBox, Switch, Radio**</span><span class="sxs-lookup"><span data-stu-id="95e5c-179">**New HoloLens 2-style Toggle Buttons - Checkbox, Switch, Radio**</span></span>
<br/><img src="https://user-images.githubusercontent.com/13754172/75299797-df631d80-57ea-11ea-8857-8ef647df0aca.gif" width="450" alt="Button Config Helper">
<br/><img src="https://user-images.githubusercontent.com/13754172/75299783-d6724c00-57ea-11ea-88b1-85e4a585212f.gif" width="450" alt="Pressabe button">

<span data-ttu-id="95e5c-180">**Miglioramenti del menu a mano**</span><span class="sxs-lookup"><span data-stu-id="95e5c-180">**Hand Menu Improvements**</span></span>

<span data-ttu-id="95e5c-181">Il menu a mano è stato adattato in molte applicazioni.</span><span class="sxs-lookup"><span data-stu-id="95e5c-181">Hand menu has been adapted in many applications.</span></span> <span data-ttu-id="95e5c-182">Uno dei principali problemi riscontrati è la falsa attivazione accidentale durante la manipolazione degli oggetti o l'interazione con altri contenuti e così via. È stata aggiunta una nuova opzione di attivazione dello sguardo a HandConstraintPalmUp. cs per impedire l'attivazione di false.</span><span class="sxs-lookup"><span data-stu-id="95e5c-182">One of the biggest issue we found is the accidental false activation while manipulating objects or interacting with other content, etc. New 'Gaze Activation' option added to HandConstraintPalmUp.cs to prevent false activations.</span></span> <span data-ttu-id="95e5c-183">Con questa opzione, il menu non viene visualizzato accidentalmente, fino a quando l'utente non guarda la mano.</span><span class="sxs-lookup"><span data-stu-id="95e5c-183">With this option, the menu does not accidentally show up, until the user look at the hand.</span></span><br/>
<span data-ttu-id="95e5c-184">![0416_HandMenu_02](https://user-images.githubusercontent.com/13754172/79507261-4aabbd80-7fec-11ea-95c4-6e3f4bd18c11.gif)</span><span class="sxs-lookup"><span data-stu-id="95e5c-184">![0416_HandMenu_02](https://user-images.githubusercontent.com/13754172/79507261-4aabbd80-7fec-11ea-95c4-6e3f4bd18c11.gif)</span></span>

<span data-ttu-id="95e5c-185">**Aggiornamento degli esempi di menu a mano**</span><span class="sxs-lookup"><span data-stu-id="95e5c-185">**Hand Menu Examples update**</span></span>

<span data-ttu-id="95e5c-186">Nuovo Esempio di interazione di menu di grandi dimensioni 1: selezionare & menu di pull per il blocco globale</span><span class="sxs-lookup"><span data-stu-id="95e5c-186">[New] Large menu interaction example 1: Grab & Pull menu to world-lock</span></span><br/>
<span data-ttu-id="95e5c-187">![0416_HandMenu_03](https://user-images.githubusercontent.com/13754172/79507983-90b55100-7fed-11ea-9062-630c892950cb.gif)</span><span class="sxs-lookup"><span data-stu-id="95e5c-187">![0416_HandMenu_03](https://user-images.githubusercontent.com/13754172/79507983-90b55100-7fed-11ea-9062-630c892950cb.gif)</span></span>

<span data-ttu-id="95e5c-188">Nuovo Esempio di interazione di menu di grandi dimensioni 2-blocco globale automatico a mano</span><span class="sxs-lookup"><span data-stu-id="95e5c-188">[New] Large menu interaction example 2 - Auto world-lock on hand drop</span></span><br/>
<span data-ttu-id="95e5c-189">![0416_HandMenu_04](https://user-images.githubusercontent.com/13754172/79508227-f9043280-7fed-11ea-995f-ac3cfe42fe65.gif)</span><span class="sxs-lookup"><span data-stu-id="95e5c-189">![0416_HandMenu_04](https://user-images.githubusercontent.com/13754172/79508227-f9043280-7fed-11ea-995f-ac3cfe42fe65.gif)</span></span>

<span data-ttu-id="95e5c-190">**Finestra di dialogo (sperimentale)**</span><span class="sxs-lookup"><span data-stu-id="95e5c-190">**Dialog (Experimental)**</span></span>
<br/><img src="../features/Images/Dialog/MRTK_UX_Dialog_Main.png" width="450" alt="UX Dialog Box">

<span data-ttu-id="95e5c-191">L'interfaccia utente della finestra di dialogo è stata trasferita da HoloToolkit con nuovi aggiornamenti di progettazione di tipo Shell HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="95e5c-191">Dialog UI has been ported over from HoloToolkit with new HoloLens 2 shell-style design updates.</span></span>

<span data-ttu-id="95e5c-192">**Ancoraggio (sperimentale)**</span><span class="sxs-lookup"><span data-stu-id="95e5c-192">**Dock (Experimental)**</span></span>
<br/><img src="https://user-images.githubusercontent.com/621574/76669327-65e86080-6548-11ea-85a3-f84f6b367f97.gif" width="450" alt="Dock">

<span data-ttu-id="95e5c-193">Questo controllo consente lo spostamento di oggetti all'interno e all'esterno di posizioni predeterminate, per la creazione di tavolozze, scaffali e barre di spostamento.</span><span class="sxs-lookup"><span data-stu-id="95e5c-193">This control enables moving objects in and out of predetermined positions, to create palettes, shelves and navigation bars.</span></span>

<span data-ttu-id="95e5c-194">**Marcatori del profiler Unity**</span><span class="sxs-lookup"><span data-stu-id="95e5c-194">**Unity Profiler markers**</span></span>

<span data-ttu-id="95e5c-195">Questa versione di MRTK ha aggiunto marcatori del profiler Unity al sistema di input e ai provider di dati.</span><span class="sxs-lookup"><span data-stu-id="95e5c-195">This version of MRTK has added Unity Profiler markers to the input system and data providers.</span></span> <span data-ttu-id="95e5c-196">Questi marcatori forniscono informazioni dettagliate sul punto in cui viene impiegato il tempo nel sistema di input MRTK che può essere usato per ottimizzare le applicazioni.</span><span class="sxs-lookup"><span data-stu-id="95e5c-196">These markers provide detailed information on where time is spent in the MRTK input system that can be used to help optimize applications.</span></span>

<span data-ttu-id="95e5c-197">I marcatori accettano il formato "[MRTK] ClassWithoutNamespace. Method".</span><span class="sxs-lookup"><span data-stu-id="95e5c-197">Markers take the format of "[MRTK] ClassWithoutNamespace.Method".</span></span>

![Marcatori Profiler](../features/Images/ReleaseNotes/ProfilerMarkers.png)

<span data-ttu-id="95e5c-199">**WindowsApiChecker: IsMethodAvailable (), IsPropertyAvailable () e IsTypeAvailable ()**</span><span class="sxs-lookup"><span data-stu-id="95e5c-199">**WindowsApiChecker: IsMethodAvailable(), IsPropertyAvailable() and IsTypeAvailable()**</span></span>

<span data-ttu-id="95e5c-200">Questa versione di MRTK aggiunge tre nuovi metodi alla [`WindowsApiChecker`](xref:Microsoft.MixedReality.Toolkit.Windows.Utilities.WindowsApiChecker) classe: `IsMethodAvailable` `IsPropertyAvailable` e `IsTypeAvailable` .</span><span class="sxs-lookup"><span data-stu-id="95e5c-200">This version of MRTK adds three new methods to the [`WindowsApiChecker`](xref:Microsoft.MixedReality.Toolkit.Windows.Utilities.WindowsApiChecker) class: `IsMethodAvailable`, `IsPropertyAvailable` and `IsTypeAvailable`.</span></span> <span data-ttu-id="95e5c-201">Questi metodi consentono di verificare il supporto delle funzionalità in Windows 10 e sono preferiti rispetto all'uso delle `UniversalApiContractV#_IsAvailable` Proprietà.</span><span class="sxs-lookup"><span data-stu-id="95e5c-201">These methods allow for checking for feature support on Windows 10 and are preferred over using the `UniversalApiContractV#_IsAvailable` properties.</span></span>

<span data-ttu-id="95e5c-202">**Helper per ottenere campi di input di testo che utilizzano MixedRealityKeyboard per UnityUI, TextMeshPro (sperimentale)**</span><span class="sxs-lookup"><span data-stu-id="95e5c-202">**Helpers to get text input fields working with MixedRealityKeyboard for UnityUI, TextMeshPro (Experimental)**</span></span>

<img src="https://user-images.githubusercontent.com/168492/77582981-86e07800-6e9d-11ea-86e5-bf2c0840296c.png" width="300" alt="MRTK Keyboard for unity" />

<span data-ttu-id="95e5c-203">Sono stati introdotti due componenti helper [`UI_KeyboardInputField`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.UI_KeyboardInputField) [`TMP_KeyboardInputField`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.TMP_KeyboardInputField) che possono essere aggiunti a campi di input di testo nell'interfaccia utente di Unity per consentire la visualizzazione della tastiera HoloLens 2 e Windows Mixed Reality quando si fa clic sui campi.</span><span class="sxs-lookup"><span data-stu-id="95e5c-203">We have introduced two helper components, [`UI_KeyboardInputField`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.UI_KeyboardInputField) and [`TMP_KeyboardInputField`](xref:Microsoft.MixedReality.Toolkit.Experimental.UI.TMP_KeyboardInputField) that can be added to text input fields in Unity UI to enable the HoloLens 2 and Windows Mixed Reality Keyboard to show up when the fields are clicked.</span></span>

<span data-ttu-id="95e5c-204">Per ulteriori informazioni, vedere gli [helper della tastiera per la realtà mista](../reference-docs/MixedRealityKeyboard/README_MixedRealityKeyboard.md).</span><span class="sxs-lookup"><span data-stu-id="95e5c-204">For more information, see - [Mixed Reality Keyboard Helpers](../reference-docs/MixedRealityKeyboard/README_MixedRealityKeyboard.md).</span></span>

<span data-ttu-id="95e5c-205">**Opzioni di allineamento della raccolta di oggetti Grid**</span><span class="sxs-lookup"><span data-stu-id="95e5c-205">**Grid Object Collection Alignment Options**</span></span>

<img src="https://user-images.githubusercontent.com/39840334/79289136-5c228780-7e7d-11ea-82b4-07959e42c3ed.gif" width="300" alt="Alignment Options" />

<span data-ttu-id="95e5c-206">È stata aggiunta la possibilità di scegliere il modo in cui gli elementi della griglia sono allineati, se sono allineati al centro o lungo l'asse sinistro/destro (asse superiore/inferiore quando si esegue la riga e il layout della colonna)</span><span class="sxs-lookup"><span data-stu-id="95e5c-206">We have added the ability to choose how the elements in the grid are aligned, whether they are aligned in the center or along the left/right axis (top/bottom axis when doing row then column layout)</span></span>

<span data-ttu-id="95e5c-207">**Modifiche all'ancoraggio della raccolta di oggetti Grid**</span><span class="sxs-lookup"><span data-stu-id="95e5c-207">**Grid Object Collection Anchor Changes**</span></span>

<img src="https://user-images.githubusercontent.com/39840334/79516745-17bff480-8001-11ea-8492-cfa953c451da.gif" width="300" alt="Anchor Changes" />

<span data-ttu-id="95e5c-208">Sono state apportate modifiche al comportamento della raccolta di oggetti Grid in linea con i comportamenti dei gruppi di layout di Unity allineando l'ancoraggio lungo l'asse centrale di un oggetto.</span><span class="sxs-lookup"><span data-stu-id="95e5c-208">We made changes to Grid Object Collection behavior to be more in line with Unity's layout group behaviors by aligning the anchor along an object's central axis.</span></span> <span data-ttu-id="95e5c-209">Il comportamento precedente della raccolta di oggetti Grid può essere attivato o disattivato con il `AnchorAlongAxis` campo.</span><span class="sxs-lookup"><span data-stu-id="95e5c-209">The old Grid Object Collection behavior can be toggled with the `AnchorAlongAxis` field.</span></span>

<span data-ttu-id="95e5c-210">**Controllo della fotocamera della simulazione di input adattato**</span><span class="sxs-lookup"><span data-stu-id="95e5c-210">**Adjusted input simulation camera control**</span></span>

<span data-ttu-id="95e5c-211">La velocità di controllo della fotocamera con la simulazione di input nell'editor è più lenta per un'esperienza più uniforme e ora è disconnessa da framerate.</span><span class="sxs-lookup"><span data-stu-id="95e5c-211">Camera control speed using in-editor input simulation is slower for a smoother experience and is now untied from framerate.</span></span> <span data-ttu-id="95e5c-212">Controllo rapido della fotocamera attivato ora con spostamento a destra anziché CTRL</span><span class="sxs-lookup"><span data-stu-id="95e5c-212">Fast camera control now activated with Right Shift instead of Right Ctrl</span></span>

<span data-ttu-id="95e5c-213">**Simulazione di input GGV senza intervento**</span><span class="sxs-lookup"><span data-stu-id="95e5c-213">**Hands-free GGV input simulation**</span></span>

<img src="https://user-images.githubusercontent.com/39840334/79164615-40908180-7d96-11ea-8195-6be34d4df8d6.gif" width="300" alt="Hands-free GGV input"/>

<span data-ttu-id="95e5c-214">È stata abilitata la possibilità di interagire con gli oggetti senza portare a termine il servizio di simulazione input dell'editor.</span><span class="sxs-lookup"><span data-stu-id="95e5c-214">We've enabled the ability to interact with objects without bringing hands within the in-editor input simulation service.</span></span> <span data-ttu-id="95e5c-215">Ruotare la fotocamera in modo che il cursore dello sguardo si trovi su un oggetto interagibile e fare clic sul pulsante sinistro del mouse per interagire con esso.</span><span class="sxs-lookup"><span data-stu-id="95e5c-215">Rotate the camera so that the gaze cursor is over an interactable object, and click on the left mouse button to interact with it.</span></span>

<span data-ttu-id="95e5c-216">**Helper config pulsante**</span><span class="sxs-lookup"><span data-stu-id="95e5c-216">**Button Config Helper**</span></span>

<img src="https://user-images.githubusercontent.com/168492/81211778-bb5d4e80-8f88-11ea-94c7-33cf265586df.png" width="300" alt="Button Config Helper" />

<span data-ttu-id="95e5c-217">Button config Helper è una funzionalità dell'editor che semplifica la personalizzazione dei pulsanti MRTK.</span><span class="sxs-lookup"><span data-stu-id="95e5c-217">The Button Config Helper is an editor feature that makes it easier to customize MRTK buttons.</span></span> <span data-ttu-id="95e5c-218">Ora è molto più semplice:</span><span class="sxs-lookup"><span data-stu-id="95e5c-218">It's now much easier to:</span></span>

- <span data-ttu-id="95e5c-219">Aggiornare il testo dell'etichetta del pulsante</span><span class="sxs-lookup"><span data-stu-id="95e5c-219">Update the button label text</span></span>
- <span data-ttu-id="95e5c-220">Aggiungere un listener di eventi click del pulsante</span><span class="sxs-lookup"><span data-stu-id="95e5c-220">Add a button click event listener</span></span>
- <span data-ttu-id="95e5c-221">Modificare l'icona del pulsante</span><span class="sxs-lookup"><span data-stu-id="95e5c-221">Change the button icon</span></span>

<span data-ttu-id="95e5c-222">**Selezione Spatializer audio nella finestra di dialogo di configurazione di MRTK**</span><span class="sxs-lookup"><span data-stu-id="95e5c-222">**Audio Spatializer Selection in MRTK configuration dialog**</span></span>

<span data-ttu-id="95e5c-223">È ora possibile specificare il Spatializer audio nella finestra di dialogo di configurazione di MRTK.</span><span class="sxs-lookup"><span data-stu-id="95e5c-223">The audio spatializer can now be specified in the MRTK configuration dialog.</span></span> <span data-ttu-id="95e5c-224">L'installazione di nuovi spatializers, ad esempio [Microsoft Spatializer](https://www.nuget.org/packages/Microsoft.SpatialAudio.Spatializer.Unity/), verrà riattivata per consentire una selezione semplificata.</span><span class="sxs-lookup"><span data-stu-id="95e5c-224">Installing new spatializers, such as the [Microsoft Spatializer](https://www.nuget.org/packages/Microsoft.SpatialAudio.Spatializer.Unity/), will re-prompt to allow for easy selection.</span></span>

![Configurazione di MRTK selezionare Spatializer](../features/Images/ReleaseNotes/SpatializerSelection.png)

<span data-ttu-id="95e5c-226">**Manipolatore di oggetti laureato in SDK**</span><span class="sxs-lookup"><span data-stu-id="95e5c-226">**Object manipulator graduated to SDK**</span></span>

![Manipolatore di oggetti](../features//Images/ManipulationHandler/MRTK_Manipulation_Main.png)

<span data-ttu-id="95e5c-228">ObjectManipulator è ora laureato in SDK e non è più una funzionalità sperimentale.</span><span class="sxs-lookup"><span data-stu-id="95e5c-228">ObjectManipulator now graduated to SDK and is no longer an experimental feature.</span></span> <span data-ttu-id="95e5c-229">Questo controllo sostituisce la classe ManipulationHandler esistente, che ora è deprecata.</span><span class="sxs-lookup"><span data-stu-id="95e5c-229">This control is replacing the existing ManipulationHandler class which is now deprecated.</span></span> <span data-ttu-id="95e5c-230">ObjectManipulator è dotato di un nuovo sistema di vincoli più flessibile e risponde correttamente alla fisica.</span><span class="sxs-lookup"><span data-stu-id="95e5c-230">ObjectManipulator comes with a new more flexible constraint system and correctly responds to physics.</span></span> <span data-ttu-id="95e5c-231">Un elenco completo di funzionalità e istruzioni per la configurazione sono disponibili nella [documentazione relativa al manipolatore di oggetti](../features/README_ObjectManipulator.md).</span><span class="sxs-lookup"><span data-stu-id="95e5c-231">A full feature list and guide how to set up can be found in [object manipulator documentation](../features/README_ObjectManipulator.md).</span></span>
<span data-ttu-id="95e5c-232">Gli utenti possono sfruttare la nuova [finestra di migrazione](../features/Tools/MigrationWindow.md) per aggiornare la GameObject esistente usando ManipulationHandler a ObjectManipulator</span><span class="sxs-lookup"><span data-stu-id="95e5c-232">Users can take advantage of the new [migration window](../features/Tools/MigrationWindow.md) to upgrade their existing gameobject using ManipulationHandler to ObjectManipulator</span></span>

<span data-ttu-id="95e5c-233">**Miglioramenti del controllo dei limiti**</span><span class="sxs-lookup"><span data-stu-id="95e5c-233">**Bounds control improvements**</span></span>

<span data-ttu-id="95e5c-234">Il code coverage del test è stato notevolmente aumentato per il controllo dei limiti di questa versione ed è stato risolto uno dei principali punti deboli degli utenti del riquadro: il controllo dei limiti ora non ricreerà più gli oggetti visivi nelle modifiche di configurazione.</span><span class="sxs-lookup"><span data-stu-id="95e5c-234">We extensively increased test coverage for bounds control this version and addressed one of the biggest pain points of users of bounding box: bounds control will now no longer recreate its visuals on configuration changes.</span></span> <span data-ttu-id="95e5c-235">Ora supporta anche la riconfigurazione di qualsiasi proprietà durante il Runtime.</span><span class="sxs-lookup"><span data-stu-id="95e5c-235">Also it now supports reconfiguring any property during runtime.</span></span> <span data-ttu-id="95e5c-236">Inoltre, le proprietà DrawTetherWhenManipulating e HandlesIgnoreCollider sono ora configurabili per tipo di handle.</span><span class="sxs-lookup"><span data-stu-id="95e5c-236">Also the properties DrawTetherWhenManipulating and HandlesIgnoreCollider are now configurable per handle type.</span></span>

### <a name="breaking-changes-in-240"></a><span data-ttu-id="95e5c-237">Modifiche di rilievo in 2.4.0</span><span class="sxs-lookup"><span data-stu-id="95e5c-237">Breaking changes in 2.4.0</span></span>

<span data-ttu-id="95e5c-238">**API sguardi occhi**</span><span class="sxs-lookup"><span data-stu-id="95e5c-238">**Eye Gaze API**</span></span>

<span data-ttu-id="95e5c-239">La `UseEyeTracking` proprietà dall' `GazeProvider` implementazione di `IMixedRealityEyeGazeProvider` è stata rinominata in `IsEyeTrackingEnabled` .</span><span class="sxs-lookup"><span data-stu-id="95e5c-239">The `UseEyeTracking` property from `GazeProvider` implementation of `IMixedRealityEyeGazeProvider` was renamed to `IsEyeTrackingEnabled`.</span></span>

<span data-ttu-id="95e5c-240">Se questa operazione è stata eseguita in precedenza...</span><span class="sxs-lookup"><span data-stu-id="95e5c-240">If you did this previously...</span></span>

```csharp
if (CoreServices.InputSystem.GazeProvider is GazeProvider gazeProvider)
{
    gazeProvider.UseEyeTracking = true;
}
```

<span data-ttu-id="95e5c-241">Esegui ora...</span><span class="sxs-lookup"><span data-stu-id="95e5c-241">Do this now...</span></span>

```csharp
if (CoreServices.InputSystem.GazeProvider is GazeProvider gazeProvider)
{
    gazeProvider.IsEyeTrackingEnabled = true;
}
```

<span data-ttu-id="95e5c-242">**Configurazione degli sguardi**</span><span class="sxs-lookup"><span data-stu-id="95e5c-242">**Eye gaze setup**</span></span>

<span data-ttu-id="95e5c-243">Questa versione di MRTK modifica i passaggi necessari per l'installazione di Eye sguardi.</span><span class="sxs-lookup"><span data-stu-id="95e5c-243">This version of MRTK modifies the steps required for eye gaze setup.</span></span> <span data-ttu-id="95e5c-244">È possibile trovare la casella di controllo _' IsEyeTrackingEnabled '_ nelle impostazioni di sguardi del profilo puntatore di input.</span><span class="sxs-lookup"><span data-stu-id="95e5c-244">The _'IsEyeTrackingEnabled'_ checkbox can be found in the gaze settings of the input pointer profile.</span></span> <span data-ttu-id="95e5c-245">Se si seleziona questa casella, verrà abilitato lo sguardo basato sull'occhio, anziché lo sguardo predefinito basato sulla testa.</span><span class="sxs-lookup"><span data-stu-id="95e5c-245">Checking this box will enable eye based gaze, rather then the default head based gaze.</span></span>

<span data-ttu-id="95e5c-246">Per ulteriori informazioni su queste modifiche e istruzioni complete per la configurazione della verifica degli occhi, vedere l'articolo relativo alla [Verifica](../features/EyeTracking/EyeTracking_BasicSetup.md) degli occhi.</span><span class="sxs-lookup"><span data-stu-id="95e5c-246">For more information on these changes and complete instructions for eye tracking setup, please see the [eye tracking](../features/EyeTracking/EyeTracking_BasicSetup.md) article.</span></span>

### <a name="known-issues-in-240"></a><span data-ttu-id="95e5c-247">Problemi noti in 2.4.0</span><span class="sxs-lookup"><span data-stu-id="95e5c-247">Known issues in 2.4.0</span></span>

<span data-ttu-id="95e5c-248">**La finestra di dialogo MRTK Configurator non Mostra ' Abilita MSBuild per Unity ' in Unity 2019,3**</span><span class="sxs-lookup"><span data-stu-id="95e5c-248">**MRTK Configurator dialog does not show 'Enable MSBuild for Unity' in Unity 2019.3**</span></span>

<span data-ttu-id="95e5c-249">Esiste un problema per cui l'abilitazione di MSBuild per Unity in 2019,3 può comportare un ciclo infinito di ripristino dei pacchetti ([#7239](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/7239)).</span><span class="sxs-lookup"><span data-stu-id="95e5c-249">An issue exists where enabling MSBuild for Unity in 2019.3 may result in an infinite loop restoring packages ([#7239](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/7239)).</span></span>

<span data-ttu-id="95e5c-250">Come soluzione alternativa, è possibile importare il pacchetto Microsoft. Windows. DotNetWinRT usando [NuGet per Unity](https://github.com/GlitchEnzo/NuGetForUnity/releases/latest).</span><span class="sxs-lookup"><span data-stu-id="95e5c-250">As a workaround, the Microsoft.Windows.DotNetWinRT package can be imported using [NuGet for Unity](https://github.com/GlitchEnzo/NuGetForUnity/releases/latest).</span></span>

<span data-ttu-id="95e5c-251">**Versione dell'assembly duplicata e più assembly precompilati Unity 2018,4**</span><span class="sxs-lookup"><span data-stu-id="95e5c-251">**Duplicate Assembly Version and Multiple Precompiled Assemblies Unity 2018.4**</span></span>

<span data-ttu-id="95e5c-252">Se la piattaforma è cambiata da autonomo a UWP e quindi di nuovo a autonomo in Unity 2018,4, potrebbero essere presenti gli errori seguenti nella console:</span><span class="sxs-lookup"><span data-stu-id="95e5c-252">If the platform is switched from Standalone to UWP and then back to Standalone in Unity 2018.4, the following errors might be in the console:</span></span>

```
PrecompiledAssemblyException: Multiple precompiled assemblies with the same name Microsoft.Windows.MixedReality.DotNetWinRT.dll included for the current platform. Only one assembly with the same name is allowed per platform. Assembly paths
```

```
Assets\MRTK\Examples\Demos\HandTracking\Scenes\Utilities\InspectorFields\AssemblyInfo.cs(6,12): error CS0579: Duplicate 'AssemblyVersion' attribute
```

<span data-ttu-id="95e5c-253">Questi errori sono causati da problemi nel processo di eliminazione con MSBuildForUnity.</span><span class="sxs-lookup"><span data-stu-id="95e5c-253">These errors are due to issues in the deletion process with MSBuildForUnity.</span></span>  <span data-ttu-id="95e5c-254">Per risolvere il problema, mentre si è in modalità autonoma, eliminare la cartella dipendenze nella radice degli asset e riavviare Unity.</span><span class="sxs-lookup"><span data-stu-id="95e5c-254">To resolve the issue, while in Standalone, delete the Dependencies folder at the root of Assets and restart unity.</span></span>

<span data-ttu-id="95e5c-255">Per altri dettagli, vedere il [problema 7948](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/7948).</span><span class="sxs-lookup"><span data-stu-id="95e5c-255">For a more details see [Issue 7948](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/7948).</span></span>

<span data-ttu-id="95e5c-256">**Applicazioni visualizzate come lavagna 2D in Unity 2019,3**</span><span class="sxs-lookup"><span data-stu-id="95e5c-256">**Applications appearing as a 2D slate on Unity 2019.3**</span></span>

<span data-ttu-id="95e5c-257">Quando si usa Unity 2019,3, l'abilitazione del supporto di XR non configura un SDK (legacy) o un plug-in predefinito (XR Management).</span><span class="sxs-lookup"><span data-stu-id="95e5c-257">When using Unity 2019.3, enabling XR support does not configure a default SDK (legacy) or plugin (XR Mangement).</span></span> <span data-ttu-id="95e5c-258">Di conseguenza, le applicazioni sono vincolate a uno Slate 2D.</span><span class="sxs-lookup"><span data-stu-id="95e5c-258">This results in applications being constrained to a 2D slate.</span></span> <span data-ttu-id="95e5c-259">Per informazioni dettagliate sulla risoluzione, vedere l' [articolo compilazione e distribuzione di MRTK](../updates-deployment/BuildAndDeploy.md#unity-20193-and-hololens).</span><span class="sxs-lookup"><span data-stu-id="95e5c-259">Details on resolving this can be found in the [Building and Deploying MRTK article](../updates-deployment/BuildAndDeploy.md#unity-20193-and-hololens).</span></span>

<span data-ttu-id="95e5c-260">**Unity 2019,3: architettura di compilazione ARM**</span><span class="sxs-lookup"><span data-stu-id="95e5c-260">**Unity 2019.3: ARM build architecture**</span></span>

<span data-ttu-id="95e5c-261">Si è verificato un [problema noto](https://issuetracker.unity3d.com/issues/enabling-graphics-jobs-in-2019-dot-3-x-results-in-a-crash-or-nothing-rendering-on-hololens-2) in unity 2019,3 che causa errori quando si seleziona ARM come architettura di compilazione in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="95e5c-261">There is a [known issue](https://issuetracker.unity3d.com/issues/enabling-graphics-jobs-in-2019-dot-3-x-results-in-a-crash-or-nothing-rendering-on-hololens-2) in Unity 2019.3 that causes errors when selecting ARM as the build architecture in Visual Studio.</span></span> <span data-ttu-id="95e5c-262">La soluzione consigliata consiste nel compilare per ARM64.</span><span class="sxs-lookup"><span data-stu-id="95e5c-262">The recommended work around is to build for ARM64.</span></span> <span data-ttu-id="95e5c-263">Se questa opzione non è possibile, disabilitare i **processi grafici** in **modifica**  >  **Impostazioni progetto**  >  **lettore**  >  **altre impostazioni**.</span><span class="sxs-lookup"><span data-stu-id="95e5c-263">If that is not an option, please disable **Graphics Jobs** in **Edit** > **Project Settings** > **Player** > **Other Settings**.</span></span> <span data-ttu-id="95e5c-264">Per ulteriori informazioni [, vedere compilazione e distribuzione](../updates-deployment/BuildAndDeploy.md#unity-20193-and-hololens).</span><span class="sxs-lookup"><span data-stu-id="95e5c-264">For more information see [Building and Deploying](../updates-deployment/BuildAndDeploy.md#unity-20193-and-hololens).</span></span>

<span data-ttu-id="95e5c-265">**Swapping del profilo di runtime**</span><span class="sxs-lookup"><span data-stu-id="95e5c-265">**Runtime profile swapping**</span></span>

<span data-ttu-id="95e5c-266">MRTK non supporta completamente lo swapping del profilo in fase di esecuzione.</span><span class="sxs-lookup"><span data-stu-id="95e5c-266">MRTK does not fully support profile swapping at runtime.</span></span> <span data-ttu-id="95e5c-267">Questa funzionalità viene esaminata per una versione futura.</span><span class="sxs-lookup"><span data-stu-id="95e5c-267">This feature is being investigated for a future release.</span></span> <span data-ttu-id="95e5c-268">Per ulteriori informazioni, vedere i problemi [4289](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/4289), [5465](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/5465) e [5466](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/5466) .</span><span class="sxs-lookup"><span data-stu-id="95e5c-268">Please see issues [4289](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/4289), [5465](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/5465) and [5466](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/5466) for more information.</span></span>

<span data-ttu-id="95e5c-269">**Unity 2018: back-end .NET ed AR Foundation**</span><span class="sxs-lookup"><span data-stu-id="95e5c-269">**Unity 2018: .NET Backend and AR Foundation**</span></span>

<span data-ttu-id="95e5c-270">Si è verificato un problema in Unity 2018, in cui la compilazione di un progetto piattaforma UWP (Universal Windows Platform) usando il back-end di scripting .NET, il pacchetto di Unity AR Foundation avrà esito negativo.</span><span class="sxs-lookup"><span data-stu-id="95e5c-270">There is an issue in Unity 2018 where, building a Universal Windows Platform project using the .NET scripting backend, the Unity AR Foundation package will fail.</span></span>

<span data-ttu-id="95e5c-271">Per risolvere il problema, eseguire una delle operazioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="95e5c-271">To work around this issue, please perform one of the following steps:</span></span>

- <span data-ttu-id="95e5c-272">Passare il back-end di scripting a IL2CPP</span><span class="sxs-lookup"><span data-stu-id="95e5c-272">Switch the scripting backend to IL2CPP</span></span>
- <span data-ttu-id="95e5c-273">Nella finestra impostazioni di compilazione deselezionare \* \* Unity progetti C# "</span><span class="sxs-lookup"><span data-stu-id="95e5c-273">In the Build Settings window, uncheck \*\*Unity C# Projects"</span></span>

---
title: MRTK Examples Hub
description: Panoramica sulle scene di esempio in MRTK
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: b7a55e46b2c283b5a75395b9e99874af6020a171
ms.sourcegitcommit: 912fa204ef79e9b973eab9b862846ba5ed5cd69f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/16/2021
ms.locfileid: "114282001"
---
# <a name="mrtk-examples-hub"></a><span data-ttu-id="b2bc9-104">MRTK Examples Hub</span><span class="sxs-lookup"><span data-stu-id="b2bc9-104">MRTK Examples Hub</span></span>

![MRTK Examples Hub](../images/examples-hub/MRTK_ExamplesHub.png)

<span data-ttu-id="b2bc9-106">MrTK Examples Hub è una scena Unity che semplifica l'esperienza di più scene.</span><span class="sxs-lookup"><span data-stu-id="b2bc9-106">MRTK Examples Hub is a Unity scene that makes it easy to experience multiple scenes.</span></span> <span data-ttu-id="b2bc9-107">Usa il sistema scene di MRTK per caricare & scaricare le scene.</span><span class="sxs-lookup"><span data-stu-id="b2bc9-107">It uses MRTK's Scene System to load & unload the scenes.</span></span>

<span data-ttu-id="b2bc9-108">**MRTKExamplesHub.unity è** la scena del contenitore con componenti condivisi, tra cui ``MixedRealityToolkit`` e ``MixedRealityPlayspace`` .</span><span class="sxs-lookup"><span data-stu-id="b2bc9-108">**MRTKExamplesHub.unity** is the container scene that has shared components including ``MixedRealityToolkit`` and ``MixedRealityPlayspace``.</span></span> <span data-ttu-id="b2bc9-109">**La scena MRTKExamplesHubMainMenu.unity** include i pulsanti del cubo.</span><span class="sxs-lookup"><span data-stu-id="b2bc9-109">**MRTKExamplesHubMainMenu.unity** scene has the cube buttons.</span></span>

## <a name="prerequisite"></a><span data-ttu-id="b2bc9-110">Prerequisito</span><span class="sxs-lookup"><span data-stu-id="b2bc9-110">Prerequisite</span></span>

<span data-ttu-id="b2bc9-111">MrTK Examples Hub usa [scene transition service](../extensions/scene-transition-service.md) e script correlati.</span><span class="sxs-lookup"><span data-stu-id="b2bc9-111">MRTK Examples Hub uses [Scene Transition Service](../extensions/scene-transition-service.md) and related scripts.</span></span> <span data-ttu-id="b2bc9-112">Se si usa MRTK tramite pacchetti Unity, **importare Microsoft.MixedReality.Toolkit. Unity.Extensions.x.x.x.unitypackage** che fa parte dei pacchetti [di versione](https://github.com/microsoft/MixedRealityToolkit-Unity/releases).</span><span class="sxs-lookup"><span data-stu-id="b2bc9-112">If you are using MRTK through Unity packages, please import **Microsoft.MixedReality.Toolkit.Unity.Extensions.x.x.x.unitypackage** which is part of the [release packages](https://github.com/microsoft/MixedRealityToolkit-Unity/releases).</span></span> <span data-ttu-id="b2bc9-113">Se si usa MRTK tramite il clone del repository, nel progetto dovrebbe essere già presente la cartella **MRTK/Extensions.**</span><span class="sxs-lookup"><span data-stu-id="b2bc9-113">If you are using MRTK through the repository clone, you should already have the **MRTK/Extensions** folder in your project.</span></span>

## <a name="mrtkexampleshub-scene-and-the-scene-system"></a><span data-ttu-id="b2bc9-114">Scena MRTKExamplesHub e sistema della scena</span><span class="sxs-lookup"><span data-stu-id="b2bc9-114">MRTKExamplesHub scene and the scene system</span></span>

<span data-ttu-id="b2bc9-115">Aprire **MRTKExamplesHub.unity** che si trova in Si tratta di una scena vuota con `MRTK/Examples/Experimental/Demos/ExamplesHub/Scenes/` MixedRealityToolkit, MixedRealityPlayspace e LoadHubOnStartup.</span><span class="sxs-lookup"><span data-stu-id="b2bc9-115">Open **MRTKExamplesHub.unity** which is located at `MRTK/Examples/Experimental/Demos/ExamplesHub/Scenes/` It is an empty scene with MixedRealityToolkit, MixedRealityPlayspace and LoadHubOnStartup.</span></span> <span data-ttu-id="b2bc9-116">Questa scena è configurata per l'uso del sistema di scena di MRTK.</span><span class="sxs-lookup"><span data-stu-id="b2bc9-116">This scene is configured to use MRTK's Scene System.</span></span> <span data-ttu-id="b2bc9-117">Fare `MixedRealitySceneSystem` clic in MixedRealityToolkit.</span><span class="sxs-lookup"><span data-stu-id="b2bc9-117">Click `MixedRealitySceneSystem` under MixedRealityToolkit.</span></span> <span data-ttu-id="b2bc9-118">Verranno visualizzate le informazioni del sistema della scena nel pannello Inspector (Controllo).</span><span class="sxs-lookup"><span data-stu-id="b2bc9-118">It will display the Scene System's information in the Inspector panel.</span></span>

<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_Hierarchy.png" width="300" alt="Example Hub Hierarchy">
<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_Inspector1.png" width="450" alt="Inspector 1">

<span data-ttu-id="b2bc9-119">Nella parte inferiore del controllo viene visualizzato l'elenco delle scene definite nel profilo del sistema della scena.</span><span class="sxs-lookup"><span data-stu-id="b2bc9-119">On the bottom of the Inspector, it displays the list of the scenes defined in the Scene System Profile.</span></span> <span data-ttu-id="b2bc9-120">È possibile fare clic sui nomi delle scene per caricarle/scaricarle.</span><span class="sxs-lookup"><span data-stu-id="b2bc9-120">You can click the scene names to load/unload them.</span></span>

<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_Inspector2.png" width="550" alt="Inspector 2">
<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem3.png" alt="Scene system 3"><span data-ttu-id="b2bc9-121">Esempio di caricamento _della scena MRTKExamplesHub_ facendo clic sul nome della scena nell'elenco.</span><span class="sxs-lookup"><span data-stu-id="b2bc9-121">Example of loading _MRTKExamplesHub_ scene by clicking the scene name in the list.</span></span>
<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem4.png" alt="Scene system 4"><span data-ttu-id="b2bc9-122">Esempio di caricamento _della scena HandInteractionExamples._</span><span class="sxs-lookup"><span data-stu-id="b2bc9-122">Example of loading _HandInteractionExamples_ scene.</span></span>
<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem5.png" alt="Scene system 5">
<span data-ttu-id="b2bc9-123">Esempio di caricamento di più scene.</span><span class="sxs-lookup"><span data-stu-id="b2bc9-123">Example of loading multiple scenes.</span></span>

## <a name="running-the-scene"></a><span data-ttu-id="b2bc9-124">Esecuzione della scena</span><span class="sxs-lookup"><span data-stu-id="b2bc9-124">Running the scene</span></span>

<span data-ttu-id="b2bc9-125">La scena funziona sia nella modalità di gioco di Unity che nel dispositivo.</span><span class="sxs-lookup"><span data-stu-id="b2bc9-125">The scene works in both Unity's game mode and on device.</span></span> <span data-ttu-id="b2bc9-126">Eseguire la **scena MRTKExamplesHub** nell'editor di Unity e usare la simulazione di input di MRTK per interagire con il contenuto della scena.</span><span class="sxs-lookup"><span data-stu-id="b2bc9-126">Run the **MRTKExamplesHub** scene in the Unity editor and use MRTK's input simulation to interact with the scene contents.</span></span> <span data-ttu-id="b2bc9-127">Per compilare e distribuire, è sufficiente compilare la scena **MRTKExamplesHub** con altre scene incluse nell'elenco del sistema di scena.</span><span class="sxs-lookup"><span data-stu-id="b2bc9-127">To build and deploy, simply build **MRTKExamplesHub** scene with other scenes that are included in the Scene System's list.</span></span> <span data-ttu-id="b2bc9-128">Il controllo semplifica anche l'aggiunta di scene al controllo di Impostazioni.</span><span class="sxs-lookup"><span data-stu-id="b2bc9-128">The inspector also makes it easy to add scenes to the Build Settings.</span></span> <span data-ttu-id="b2bc9-129">Nella finestra di Impostazioni assicurarsi che la scena **MRTKExamplesHub** si trova all'inizio dell'elenco in corrispondenza dell'indice 0.</span><span class="sxs-lookup"><span data-stu-id="b2bc9-129">In the Building Settings, make sure **MRTKExamplesHub** scene is on the top of the list at index 0.</span></span>

<img src="../images/examples-hub/MRTK_ExamplesHub_BuildSettings.png" width="450" alt="Build settings">

## <a name="how-mrtkexampleshub-loads-a-scene"></a><span data-ttu-id="b2bc9-130">Come MRTKExamplesHub carica una scena</span><span class="sxs-lookup"><span data-stu-id="b2bc9-130">How MRTKExamplesHub loads a scene</span></span>

<span data-ttu-id="b2bc9-131">Nella **scena MRTKExamplesHub** è possibile trovare il ``ExamplesHubButton`` prefab.</span><span class="sxs-lookup"><span data-stu-id="b2bc9-131">In the **MRTKExamplesHub** scene, you can find the ``ExamplesHubButton`` prefab.</span></span>
<span data-ttu-id="b2bc9-132">Nel prefab è presente un oggetto **FrontPlate** che contiene ``Interactable`` .</span><span class="sxs-lookup"><span data-stu-id="b2bc9-132">There is a **FrontPlate** object in the prefab which contains ``Interactable``.</span></span>
<span data-ttu-id="b2bc9-133">Usando l'evento ``OnClick()`` e di Interactable, viene attivata la funzione ``OnTouch()`` LoadContent() dello script **LoadContent(** dello script **LoadContent).**</span><span class="sxs-lookup"><span data-stu-id="b2bc9-133">Using the Interactable's ``OnClick()`` and ``OnTouch()`` event, it triggers the **LoadContentScene** script's **LoadContent()** function.</span></span>
<span data-ttu-id="b2bc9-134">Nel controllo dello script **LoadContentScene** è possibile definire il nome della scena da caricare.</span><span class="sxs-lookup"><span data-stu-id="b2bc9-134">In the **LoadContentScene** script's Inspector, you can define the scene name to load.</span></span>

<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem6.png" alt="Scene system 6">
<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem8.png" width="450" alt="Scene System 8">
<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem7.png" width="450" alt="Scene System 7">

<span data-ttu-id="b2bc9-135">Lo script usa la funzione LoadContent() del sistema della scena per caricare la scena.</span><span class="sxs-lookup"><span data-stu-id="b2bc9-135">The script uses the Scene System's LoadContent() function to load the scene.</span></span>
<span data-ttu-id="b2bc9-136">Per altri [dettagli, vedere](../scene-system/scene-system-getting-started.md) la pagina Scene System (Sistema scena).</span><span class="sxs-lookup"><span data-stu-id="b2bc9-136">Please refer to the [Scene System](../scene-system/scene-system-getting-started.md) page for more details.</span></span>

```c#
MixedRealityToolkit.SceneSystem.LoadContent(contentName, loadSceneMode);
```

## <a name="returning-to-the-main-menu-scene"></a><span data-ttu-id="b2bc9-137">Tornare alla scena del menu principale</span><span class="sxs-lookup"><span data-stu-id="b2bc9-137">Returning to the main menu scene</span></span>

<span data-ttu-id="b2bc9-138">Per tornare alla scena del menu principale (scena MRTKExamplesHubMainMenu), puoi usare lo stesso metodo Scene `LoadContent()` System.</span><span class="sxs-lookup"><span data-stu-id="b2bc9-138">To return to the main menu scene (MRTKExamplesHubMainMenu scene), you can use the same Scene System `LoadContent()` method.</span></span> <span data-ttu-id="b2bc9-139">**ToggleFeaturesPanelExamplesHub.prefab** fornisce il pulsante "Home" che contiene lo script **LoadContentScene.**</span><span class="sxs-lookup"><span data-stu-id="b2bc9-139">The **ToggleFeaturesPanelExamplesHub.prefab** provides the 'Home' button which contains the **LoadContentScene** script.</span></span> <span data-ttu-id="b2bc9-140">Usare questo prefab o fornire un pulsante Pagina iniziale personalizzato in ogni scena per consentire all'utente di tornare alla scena principale.</span><span class="sxs-lookup"><span data-stu-id="b2bc9-140">Use this prefab or provide a custom home button in each scene to allow the user to return to the main scene.</span></span> <span data-ttu-id="b2bc9-141">È possibile inserire **ToggleFeaturesPanelExamplesHub.prefab** nella scena **MRTKExamplesHub** per renderlo sempre visibile perché **MRTKExamplesHub** è una scena contenitore condivisa.</span><span class="sxs-lookup"><span data-stu-id="b2bc9-141">One can put the **ToggleFeaturesPanelExamplesHub.prefab** in the **MRTKExamplesHub** scene to make it always visible since **MRTKExamplesHub** is a shared container scene.</span></span> <span data-ttu-id="b2bc9-142">Assicurati di nascondere/disattivare **ToggleFeaturesPanel.prefab** in ogni scena di esempio.</span><span class="sxs-lookup"><span data-stu-id="b2bc9-142">Make sure to hide/deactivate **ToggleFeaturesPanel.prefab** in each example scene.</span></span>

<img src="../images/examples-hub/MRTK_ExamplesHubToggleFeaturesPanel.png" alt="Toggle feature Panel">

<img src="../images/examples-hub/MRTK_ExamplesHubHomeButton.png" width="450" alt="Example Hub home button">

## <a name="adding-additional-buttons"></a><span data-ttu-id="b2bc9-143">Aggiunta di altri pulsanti</span><span class="sxs-lookup"><span data-stu-id="b2bc9-143">Adding additional buttons</span></span>

<span data-ttu-id="b2bc9-144">**Nell'oggetto CubeCollection** duplicare (o aggiungere) i prefab _ExampleHubButton_ e fare clic su **Update Collection (Aggiorna** raccolta) in `GridObjectCollection` .</span><span class="sxs-lookup"><span data-stu-id="b2bc9-144">In the **CubeCollection** object, duplicate (or add) _ExampleHubButton_ prefabs and click **Update Collection** in the `GridObjectCollection`.</span></span>
<span data-ttu-id="b2bc9-145">Il layout del cilindro verrà aggiornato in base al nuovo numero totale di pulsanti.</span><span class="sxs-lookup"><span data-stu-id="b2bc9-145">This will update the cylinder layout based on the new total number of buttons.</span></span>
<span data-ttu-id="b2bc9-146">Per altri [dettagli, vedere](../ux-building-blocks/object-collection.md) la pagina Raccolta di oggetti.</span><span class="sxs-lookup"><span data-stu-id="b2bc9-146">Please refer to the [Object Collection](../ux-building-blocks/object-collection.md) page for more details.</span></span>

<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem9.png" alt="Scene System 9">
<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem10.png" alt="Scene System 10">

<span data-ttu-id="b2bc9-147">Dopo aver aggiunto i pulsanti, aggiornare il nome della scena nello script **LoadContentScene** (illustrato in precedenza).</span><span class="sxs-lookup"><span data-stu-id="b2bc9-147">After adding the buttons, update the scene name in the **LoadContentScene** script(explained above).</span></span>
<span data-ttu-id="b2bc9-148">Aggiungere altre scene al profilo del sistema della scena.</span><span class="sxs-lookup"><span data-stu-id="b2bc9-148">Add additional scenes to the Scene System's profile.</span></span>

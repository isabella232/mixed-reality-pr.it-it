---
title: README_ExampleHub
description: Panoramica su scene di esempio in MRTK
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: ed3d14022ab3594714178698f8ef27f49381583f
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2021
ms.locfileid: "104695138"
---
# <a name="mrtk-examples-hub"></a><span data-ttu-id="b1dd8-104">MRTK Examples Hub</span><span class="sxs-lookup"><span data-stu-id="b1dd8-104">MRTK Examples Hub</span></span>

![MRTK Examples Hub](Images/ExamplesHub/MRTK_ExamplesHub.png)

<span data-ttu-id="b1dd8-106">L'hub esempi di MRTK è una scena Unity che semplifica l'esperienza di più scene.</span><span class="sxs-lookup"><span data-stu-id="b1dd8-106">MRTK Examples Hub is a Unity scene that makes it easy to experience multiple scenes.</span></span> <span data-ttu-id="b1dd8-107">Usa il sistema di scena di MRTK per caricare & scaricare le scene.</span><span class="sxs-lookup"><span data-stu-id="b1dd8-107">It uses MRTK's Scene System to load & unload the scenes.</span></span>

<span data-ttu-id="b1dd8-108">**MRTKExamplesHub. Unity** è la scena del contenitore con componenti condivisi ``MixedRealityToolkit`` , tra cui e ``MixedRealityPlayspace`` .</span><span class="sxs-lookup"><span data-stu-id="b1dd8-108">**MRTKExamplesHub.unity** is the container scene that has shared components including ``MixedRealityToolkit`` and ``MixedRealityPlayspace``.</span></span> <span data-ttu-id="b1dd8-109">La scena **MRTKExamplesHubMainMenu. Unity** contiene i pulsanti del cubo.</span><span class="sxs-lookup"><span data-stu-id="b1dd8-109">**MRTKExamplesHubMainMenu.unity** scene has the cube buttons.</span></span>

## <a name="prerequisite"></a><span data-ttu-id="b1dd8-110">Prerequisito</span><span class="sxs-lookup"><span data-stu-id="b1dd8-110">Prerequisite</span></span>

<span data-ttu-id="b1dd8-111">L'hub esempi di MRTK usa il [servizio di transizione della scena](Extensions/SceneTransitionService/SceneTransitionServiceOverview.md) e gli script correlati.</span><span class="sxs-lookup"><span data-stu-id="b1dd8-111">MRTK Examples Hub uses [Scene Transition Service](Extensions/SceneTransitionService/SceneTransitionServiceOverview.md) and related scripts.</span></span> <span data-ttu-id="b1dd8-112">Se si usa MRTK tramite i pacchetti Unity, importare **Microsoft. MixedReality. Toolkit. Unity. Extensions. x** . x.x. x. file unitypackage Tools che fa parte dei [pacchetti di versione](https://github.com/microsoft/MixedRealityToolkit-Unity/releases).</span><span class="sxs-lookup"><span data-stu-id="b1dd8-112">If you are using MRTK through Unity packages, please import **Microsoft.MixedReality.Toolkit.Unity.Extensions.x.x.x.unitypackage** which is part of the [release packages](https://github.com/microsoft/MixedRealityToolkit-Unity/releases).</span></span> <span data-ttu-id="b1dd8-113">Se si usa MRTK tramite il clone del repository, è necessario che nel progetto sia già presente la cartella **MRTK/Extensions** .</span><span class="sxs-lookup"><span data-stu-id="b1dd8-113">If you are using MRTK through the repository clone, you should already have the **MRTK/Extensions** folder in your project.</span></span>

## <a name="mrtkexampleshub-scene-and-the-scene-system"></a><span data-ttu-id="b1dd8-114">Scena MRTKExamplesHub e sistema di scena</span><span class="sxs-lookup"><span data-stu-id="b1dd8-114">MRTKExamplesHub scene and the scene system</span></span>

<span data-ttu-id="b1dd8-115">Aprire **MRTKExamplesHub. Unity** , che si trova in `MRTK/Examples/Experimental/Demos/ExamplesHub/Scenes/` una scena vuota con MixedRealityToolkit, MixedRealityPlayspace e LoadHubOnStartup.</span><span class="sxs-lookup"><span data-stu-id="b1dd8-115">Open **MRTKExamplesHub.unity** which is located at `MRTK/Examples/Experimental/Demos/ExamplesHub/Scenes/` It is an empty scene with MixedRealityToolkit, MixedRealityPlayspace and LoadHubOnStartup.</span></span> <span data-ttu-id="b1dd8-116">Questa scena è configurata per l'uso del sistema di scena di MRTK.</span><span class="sxs-lookup"><span data-stu-id="b1dd8-116">This scene is configured to use MRTK's Scene System.</span></span> <span data-ttu-id="b1dd8-117">Fare clic `MixedRealitySceneSystem` sotto MixedRealityToolkit.</span><span class="sxs-lookup"><span data-stu-id="b1dd8-117">Click `MixedRealitySceneSystem` under MixedRealityToolkit.</span></span> <span data-ttu-id="b1dd8-118">Visualizzerà le informazioni del sistema di scena nel pannello Inspector.</span><span class="sxs-lookup"><span data-stu-id="b1dd8-118">It will display the Scene System's information in the Inspector panel.</span></span>

<br/><br/><img src="Images/ExamplesHub/MRTK_ExamplesHub_Hierarchy.png" width="300" alt="Hierarchy Example">
<br/><br/><img src="Images/ExamplesHub/MRTK_ExamplesHub_Inspector1.png" width="450" alt="Inspetor 1">

<span data-ttu-id="b1dd8-119">Nella parte inferiore del controllo viene visualizzato l'elenco delle scene definite nel profilo di sistema della scena.</span><span class="sxs-lookup"><span data-stu-id="b1dd8-119">On the bottom of the Inspector, it displays the list of the scenes defined in the Scene System Profile.</span></span> <span data-ttu-id="b1dd8-120">È possibile fare clic sui nomi delle scene per caricarli/scaricarli.</span><span class="sxs-lookup"><span data-stu-id="b1dd8-120">You can click the scene names to load/unload them.</span></span>

<br/><br/><img src="Images/ExamplesHub/MRTK_ExamplesHub_Inspector2.png" width="550" alt="Inspector 2">
<br/><br/><img src="Images/ExamplesHub/MRTK_ExamplesHub_SceneSystem3.png" alt="Scene System 3"><span data-ttu-id="b1dd8-121">Esempio di caricamento della scena _MRTKExamplesHub_ facendo clic sul nome della scena nell'elenco.</span><span class="sxs-lookup"><span data-stu-id="b1dd8-121">Example of loading _MRTKExamplesHub_ scene by clicking the scene name in the list.</span></span>
<br/><br/><img src="Images/ExamplesHub/MRTK_ExamplesHub_SceneSystem4.png" alt="Scene System 4"><span data-ttu-id="b1dd8-122">Esempio di caricamento della scena _HandInteractionExamples_ .</span><span class="sxs-lookup"><span data-stu-id="b1dd8-122">Example of loading _HandInteractionExamples_ scene.</span></span>
<br/><br/><img src="Images/ExamplesHub/MRTK_ExamplesHub_SceneSystem5.png" alt="Scene System 5">
<span data-ttu-id="b1dd8-123">Esempio di caricamento di più scene.</span><span class="sxs-lookup"><span data-stu-id="b1dd8-123">Example of loading multiple scenes.</span></span>

## <a name="running-the-scene"></a><span data-ttu-id="b1dd8-124">Esecuzione della scena</span><span class="sxs-lookup"><span data-stu-id="b1dd8-124">Running the scene</span></span>

<span data-ttu-id="b1dd8-125">La scena funziona sia nella modalità di gioco di Unity che nel dispositivo.</span><span class="sxs-lookup"><span data-stu-id="b1dd8-125">The scene works in both Unity's game mode and on device.</span></span> <span data-ttu-id="b1dd8-126">Eseguire la scena **MRTKExamplesHub** nell'editor di Unity e usare la simulazione di input di MRTK per interagire con il contenuto della scena.</span><span class="sxs-lookup"><span data-stu-id="b1dd8-126">Run the **MRTKExamplesHub** scene in the Unity editor and use MRTK's input simulation to interact with the scene contents.</span></span> <span data-ttu-id="b1dd8-127">Per compilare e distribuire, è sufficiente compilare la scena **MRTKExamplesHub** con altre scene incluse nell'elenco del sistema di scena.</span><span class="sxs-lookup"><span data-stu-id="b1dd8-127">To build and deploy, simply build **MRTKExamplesHub** scene with other scenes that are included in the Scene System's list.</span></span> <span data-ttu-id="b1dd8-128">Il controllo consente inoltre di aggiungere facilmente le scene alle impostazioni di compilazione.</span><span class="sxs-lookup"><span data-stu-id="b1dd8-128">The inspector also makes it easy to add scenes to the Build Settings.</span></span> <span data-ttu-id="b1dd8-129">Nelle impostazioni di compilazione assicurarsi che la scena **MRTKExamplesHub** si trovi nella parte superiore dell'elenco in corrispondenza dell'indice 0.</span><span class="sxs-lookup"><span data-stu-id="b1dd8-129">In the Building Settings, make sure **MRTKExamplesHub** scene is on the top of the list at index 0.</span></span>

<img src="Images/ExamplesHub/MRTK_ExamplesHub_BuildSettings.png" width="450" alt="Build Settings">

## <a name="how-mrtkexampleshub-loads-a-scene"></a><span data-ttu-id="b1dd8-130">Come MRTKExamplesHub carica una scena</span><span class="sxs-lookup"><span data-stu-id="b1dd8-130">How MRTKExamplesHub loads a scene</span></span>

<span data-ttu-id="b1dd8-131">Nella scena **MRTKExamplesHub** è possibile trovare il ``ExamplesHubButton`` prefabbricato.</span><span class="sxs-lookup"><span data-stu-id="b1dd8-131">In the **MRTKExamplesHub** scene, you can find the ``ExamplesHubButton`` prefab.</span></span>
<span data-ttu-id="b1dd8-132">Nel prefabbricato è presente un oggetto **coperchio** che contiene ``Interactable`` .</span><span class="sxs-lookup"><span data-stu-id="b1dd8-132">There is a **FrontPlate** object in the prefab which contains ``Interactable``.</span></span>
<span data-ttu-id="b1dd8-133">Utilizzando l'evento interactable ``OnClick()`` ``OnTouch()`` , viene attivata la funzione **LoadContent ()** dello script **LoadContentScene** .</span><span class="sxs-lookup"><span data-stu-id="b1dd8-133">Using the Interactable's ``OnClick()`` and ``OnTouch()`` event, it triggers the **LoadContentScene** script's **LoadContent()** function.</span></span>
<span data-ttu-id="b1dd8-134">Nel controllo dello script **LoadContentScene** è possibile definire il nome della scena da caricare.</span><span class="sxs-lookup"><span data-stu-id="b1dd8-134">In the **LoadContentScene** script's Inspector, you can define the scene name to load.</span></span>

<br/><br/><img src="Images/ExamplesHub/MRTK_ExamplesHub_SceneSystem6.png" alt="Scene System 6">
<br/><br/><img src="Images/ExamplesHub/MRTK_ExamplesHub_SceneSystem8.png" width="450" alt="Scene System 8">
<br/><br/><img src="Images/ExamplesHub/MRTK_ExamplesHub_SceneSystem7.png" width="450" alt="Scene System 7">

<span data-ttu-id="b1dd8-135">Lo script usa la funzione LoadContent () del sistema di scena per caricare la scena.</span><span class="sxs-lookup"><span data-stu-id="b1dd8-135">The script uses the Scene System's LoadContent() function to load the scene.</span></span>
<span data-ttu-id="b1dd8-136">Per altri dettagli, vedere la pagina del [sistema della scena](SceneSystem/SceneSystemGettingStarted.md) .</span><span class="sxs-lookup"><span data-stu-id="b1dd8-136">Please refer to the [Scene System](SceneSystem/SceneSystemGettingStarted.md) page for more details.</span></span>

```c#
MixedRealityToolkit.SceneSystem.LoadContent(contentName, loadSceneMode);
```

## <a name="returning-to-the-main-menu-scene"></a><span data-ttu-id="b1dd8-137">Tornare alla scena del menu principale</span><span class="sxs-lookup"><span data-stu-id="b1dd8-137">Returning to the main menu scene</span></span>

<span data-ttu-id="b1dd8-138">Per tornare alla scena del menu principale (scena MRTKExamplesHubMainMenu), è possibile usare lo stesso metodo di sistema della scena `LoadContent()` .</span><span class="sxs-lookup"><span data-stu-id="b1dd8-138">To return to the main menu scene (MRTKExamplesHubMainMenu scene), you can use the same Scene System `LoadContent()` method.</span></span> <span data-ttu-id="b1dd8-139">Il **ToggleFeaturesPanelExamplesHub. prefabbricate** fornisce il pulsante "Home" che contiene lo script **LoadContentScene** .</span><span class="sxs-lookup"><span data-stu-id="b1dd8-139">The **ToggleFeaturesPanelExamplesHub.prefab** provides the 'Home' button which contains the **LoadContentScene** script.</span></span> <span data-ttu-id="b1dd8-140">Usare questa prefabbricata o fornire un pulsante Home personalizzato in ogni scena per consentire all'utente di tornare alla scena principale.</span><span class="sxs-lookup"><span data-stu-id="b1dd8-140">Use this prefab or provide a custom home button in each scene to allow the user to return to the main scene.</span></span> <span data-ttu-id="b1dd8-141">È possibile inserire il **ToggleFeaturesPanelExamplesHub. prefabric** nella scena **MRTKExamplesHub** per renderlo sempre visibile perché **MRTKExamplesHub** è una scena di contenitori condivisi.</span><span class="sxs-lookup"><span data-stu-id="b1dd8-141">One can put the **ToggleFeaturesPanelExamplesHub.prefab** in the **MRTKExamplesHub** scene to make it always visible since **MRTKExamplesHub** is a shared container scene.</span></span> <span data-ttu-id="b1dd8-142">Assicurarsi di nascondere/disattivare **ToggleFeaturesPanel. prefabbricate** in ogni scena di esempio.</span><span class="sxs-lookup"><span data-stu-id="b1dd8-142">Make sure to hide/deactivate **ToggleFeaturesPanel.prefab** in each example scene.</span></span>

<img src="Images/ExamplesHub/MRTK_ExamplesHubToggleFeaturesPanel.png" alt="Toggle feature panel 1">

<img src="Images/ExamplesHub/MRTK_ExamplesHubHomeButton.png" width="450" alt="Home Button 1">

## <a name="adding-additional-buttons"></a><span data-ttu-id="b1dd8-143">Aggiunta di pulsanti aggiuntivi</span><span class="sxs-lookup"><span data-stu-id="b1dd8-143">Adding additional buttons</span></span>

<span data-ttu-id="b1dd8-144">Nell'oggetto **CubeCollection** duplicare (o aggiungere) i prefabbricati _ExampleHubButton_ e fare clic su **Aggiorna raccolta** in `GridObjectCollection` .</span><span class="sxs-lookup"><span data-stu-id="b1dd8-144">In the **CubeCollection** object, duplicate (or add) _ExampleHubButton_ prefabs and click **Update Collection** in the `GridObjectCollection`.</span></span>
<span data-ttu-id="b1dd8-145">Il layout del cilindro verrà aggiornato in base al nuovo numero totale di pulsanti.</span><span class="sxs-lookup"><span data-stu-id="b1dd8-145">This will update the cylinder layout based on the new total number of buttons.</span></span>
<span data-ttu-id="b1dd8-146">Per ulteriori informazioni, fare riferimento alla pagina [raccolta oggetti](README_ObjectCollection.md) .</span><span class="sxs-lookup"><span data-stu-id="b1dd8-146">Please refer to the [Object Collection](README_ObjectCollection.md) page for more details.</span></span>

<br/><br/><img src="Images/ExamplesHub/MRTK_ExamplesHub_SceneSystem9.png" alt="Scene System 9">
<br/><br/><img src="Images/ExamplesHub/MRTK_ExamplesHub_SceneSystem10.png" alt="Scene System 10">

<span data-ttu-id="b1dd8-147">Dopo aver aggiunto i pulsanti, aggiornare il nome della scena nello script **LoadContentScene** (illustrato in precedenza).</span><span class="sxs-lookup"><span data-stu-id="b1dd8-147">After adding the buttons, update the scene name in the **LoadContentScene** script(explained above).</span></span>
<span data-ttu-id="b1dd8-148">Aggiungere altre scene al profilo del sistema della scena.</span><span class="sxs-lookup"><span data-stu-id="b1dd8-148">Add additional scenes to the Scene System's profile.</span></span>

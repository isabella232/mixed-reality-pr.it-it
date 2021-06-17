---
title: Interazione con oggetti 3D
description: Questa esercitazione illustra come usare Mixed Reality Toolkit (MRTK) per interagire con gli oggetti 3D nelle app di realtà mista e manipolarli.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens, MRTK, mixed reality toolkit, UWP, interazioni tra oggetti, controlli limiti
ms.localizationpriority: high
ms.openlocfilehash: cbf2bbf78a34cfdd4856b7b8d192e4ac7c2f0154
ms.sourcegitcommit: c65759b8d6465b6b13925cacab5af74443f7e6bd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/15/2021
ms.locfileid: "112110269"
---
# <a name="7-interacting-with-3d-objects"></a><span data-ttu-id="84349-104">7. Interazione con oggetti 3D</span><span class="sxs-lookup"><span data-stu-id="84349-104">7. Interacting with 3D objects</span></span>

<span data-ttu-id="84349-105">In questa esercitazione apprenderai come abilitare la manipolazione da vicino e da lontano degli oggetti 3D e limitare i tipi di manipolazione consentiti.</span><span class="sxs-lookup"><span data-stu-id="84349-105">In this tutorial, you will learn how to enable near and far manipulation of 3D objects and limit the allowed types of manipulation.</span></span> <span data-ttu-id="84349-106">Si apprenderà anche come aggiungere il controllo dei limiti intorno agli oggetti 3D per semplificare il controllo della manipolazione degli oggetti.</span><span class="sxs-lookup"><span data-stu-id="84349-106">You will also learn how to add bounds control around 3D objects to make it easier to control the object manipulation.</span></span>

## <a name="objectives"></a><span data-ttu-id="84349-107">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="84349-107">Objectives</span></span>

* <span data-ttu-id="84349-108">Apprendere come configurare gli oggetti 3D in modo che sia possibile interagire con essi</span><span class="sxs-lookup"><span data-stu-id="84349-108">Learn how to configure 3D objects so they can be interacted with</span></span>
* <span data-ttu-id="84349-109">Informazioni su come aggiungere il controllo dei limiti agli oggetti 3D</span><span class="sxs-lookup"><span data-stu-id="84349-109">Learn how to add bounds control to 3D objects</span></span>

## <a name="manipulating-3d-objects"></a><span data-ttu-id="84349-110">Manipolazione di oggetti 3D</span><span class="sxs-lookup"><span data-stu-id="84349-110">Manipulating 3D objects</span></span>

<span data-ttu-id="84349-111">In questa sezione aggiungerai la possibilità di manipolare tutte le parti rover organizzate sul tavolo durante l'esercitazione [Posizionamento degli oggetti nella scena](mr-learning-base-04.md).</span><span class="sxs-lookup"><span data-stu-id="84349-111">In this section, you will add the ability to manipulate all the Rover parts you organized on the table during the [Positioning objects in the scene](mr-learning-base-04.md) tutorial.</span></span>

<span data-ttu-id="84349-112">Di seguito sono elencati i passaggi principali da eseguire per ottenere questo risultato:</span><span class="sxs-lookup"><span data-stu-id="84349-112">The main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="84349-113">Aggiungere il componente Object Manipulator (Script) (Manipolatore oggetti - script) a tutti gli oggetti parte</span><span class="sxs-lookup"><span data-stu-id="84349-113">Add the Object Manipulator (Script) component to all the part objects</span></span>
2. <span data-ttu-id="84349-114">Aggiungere il componente NearInteractionGrabbable a tutti gli oggetti parte</span><span class="sxs-lookup"><span data-stu-id="84349-114">Add the NearInteractionGrabbable component to all the part objects</span></span>
3. <span data-ttu-id="84349-115">Configurare il componente Object Manipulator (Script) (Manipolatore oggetti - script)</span><span class="sxs-lookup"><span data-stu-id="84349-115">Configure the Object Manipulator (Script) component</span></span>

> [!NOTE]
> <span data-ttu-id="84349-116">Per poter **manipolare un oggetto**, è necessario che l'oggetto abbia i componenti seguenti:</span><span class="sxs-lookup"><span data-stu-id="84349-116">To be able to **manipulate an object**, the object must have the following components:</span></span>
>
> * <span data-ttu-id="84349-117">Componente **Collider** (Collisore), ad esempio un collisore cuboide</span><span class="sxs-lookup"><span data-stu-id="84349-117">**Collider** component, for example, a Box Collider</span></span>
> * <span data-ttu-id="84349-118">Componente **Object Manipulator (Script)** (Manipolatore oggetti - script)</span><span class="sxs-lookup"><span data-stu-id="84349-118">**Object Manipulator (Script)** component</span></span>
>
> <span data-ttu-id="84349-119">Per poter **manipolare** e **afferrare un oggetto con le mani tracciate**, è necessario che l'oggetto abbia i componenti seguenti:</span><span class="sxs-lookup"><span data-stu-id="84349-119">To be able to **manipulate** and **grab an object with tracked hands**, the object must have the following components:</span></span>
>
> * <span data-ttu-id="84349-120">Componente **Collider** (Collisore), ad esempio un collisore cuboide</span><span class="sxs-lookup"><span data-stu-id="84349-120">**Collider** component, for example, a Box Collider</span></span>
> * <span data-ttu-id="84349-121">Componente **Object Manipulator (Script)** (Manipolatore oggetti - script)</span><span class="sxs-lookup"><span data-stu-id="84349-121">**Object Manipulator (Script)** component</span></span>
> * <span data-ttu-id="84349-122">Componente **NearInteractionGrabbable**</span><span class="sxs-lookup"><span data-stu-id="84349-122">**NearInteractionGrabbable** component</span></span>

<span data-ttu-id="84349-123">Configurerai inoltre Rover Explorer (Esplora rover) in modo che sia possibile posizionare le parti rover sul rover per renderlo un assembly di rover completo.</span><span class="sxs-lookup"><span data-stu-id="84349-123">Additionally, you will configure the Rover Explorer so that you can place the rover parts on to the Rover to make it a complete rover assembly.</span></span>

<span data-ttu-id="84349-124">Nella finestra Hierarchy (Gerarchia) espandi l'oggetto RoverExplorer > **RoverParts** e seleziona tutti i relativi oggetti parte rover figlio e l'oggetto **RoverAssembly**, quindi nella finestra Inspector (Controllo) usa il pulsante **Add Component** (Aggiungi componente) per aggiungere i componenti seguenti a tutti gli oggetti selezionati:</span><span class="sxs-lookup"><span data-stu-id="84349-124">In the Hierarchy window, expand the RoverExplorer > **RoverParts** object and select all its child rover part objects and the **RoverAssembly** object, then in the Inspector window, use the **Add Component** button to add the following components to all the selected objects:</span></span>

* <span data-ttu-id="84349-125">Componente **Object Manipulator (Script)** (Manipolatore oggetti - script)</span><span class="sxs-lookup"><span data-stu-id="84349-125">**Object Manipulator (Script)** component</span></span>
* <span data-ttu-id="84349-126">Componente **NearInteractionGrabbable**</span><span class="sxs-lookup"><span data-stu-id="84349-126">**NearInteractionGrabbable** component</span></span>
* <span data-ttu-id="84349-127">Componente **Part Assembly Controller (Script)** (Controllo assembly parti - script)</span><span class="sxs-lookup"><span data-stu-id="84349-127">**Part Assembly Controller (Script)** component</span></span>

![Unity con RoverAssembly e tutti gli oggetti parte rover selezionati e i componenti aggiunti](images/mr-learning-base/base-07-section1-step1-1.png)

> [!TIP]
> <span data-ttu-id="84349-129">Per selezionare più oggetti non adiacenti, tieni premuto CTRL mentre usi il mouse per selezionare un oggetto.</span><span class="sxs-lookup"><span data-stu-id="84349-129">To select multiple objects that are not next to each other, press-and-hold the CTRL key while using the mouse to select any object.</span></span>

> [!NOTE]
> <span data-ttu-id="84349-130">Quando si aggiunge un manipolatore di oggetti (script), in questo caso, Gestione vincoli (script) viene aggiunto automaticamente perché il manipolatore di oggetti (script) dipende da esso.</span><span class="sxs-lookup"><span data-stu-id="84349-130">When you add a Object Manipulator (Script), in this case, the Constraint Manager (Script) is automatically added because Object Manipulator (Script) depends on it.</span></span>

> [!NOTE]
> <span data-ttu-id="84349-131">Ai fini di questa esercitazione, i collisori sono già stati aggiunti alle parti rover.</span><span class="sxs-lookup"><span data-stu-id="84349-131">For the purpose of this tutorial, colliders have already been added to the rover parts.</span></span> <span data-ttu-id="84349-132">Per altre informazioni sui collisori, puoi visitare la documentazione <a href="https://docs.unity3d.com/Manual/CollidersOverview.html" target="_blank">corrispondente</a> di Unity.</span><span class="sxs-lookup"><span data-stu-id="84349-132">To learn more about colliders, you can visit Unity's <a href="https://docs.unity3d.com/Manual/CollidersOverview.html" target="_blank">Collider</a> documentation.</span></span>

> [!NOTE]
> <span data-ttu-id="84349-133">Part Assembly Controller (Script) (Controllo assembly parti - script) non fa parte di MRTK, ma è stato incluso negli asset dell'esercitazione.</span><span class="sxs-lookup"><span data-stu-id="84349-133">The Part Assembly Controller (Script) is not part of the MRTK but was included with the tutorial assets.</span></span>

<span data-ttu-id="84349-134">Con tutti gli oggetti parte rover e l'oggetto RoverAssembly ancora selezionati, nella finestra Inspector (Controllo) configura il componente **Object Manipulator (Script)** (Manipolatore oggetti - script) come indicato di seguito:</span><span class="sxs-lookup"><span data-stu-id="84349-134">With all the rover part objects and the RoverAssembly object still selected, in the Inspector window, configure the **Object Manipulator (Script)** component as follows:</span></span>

* <span data-ttu-id="84349-135">Dall'elenco a discesa **Two Handed Manipulation Type** (Tipo di manipolazione a due mani) deseleziona Scale (Scala) in modo che siano abilitate solo le opzioni **Move** (Sposta) e **Rotate** (Ruota)</span><span class="sxs-lookup"><span data-stu-id="84349-135">From the **Two Handed Manipulation Type** dropdown, uncheck the Scale, so only **Move** and **Rotate** is enabled</span></span>

![Unity con Two Handed Manipulation Type configurato](images/mr-learning-base/base-07-section1-step1-2.png)

> [!NOTE]
> <span data-ttu-id="84349-137">A questo punto hai abilitato la manipolazione per tutti gli oggetti parte rover e per l'oggetto RoverAssembly.</span><span class="sxs-lookup"><span data-stu-id="84349-137">At this point, you have enabled object manipulation for all the rover part objects and the RoverAssembly object.</span></span>

<span data-ttu-id="84349-138">Nella finestra Project (Progetto) passa alla **cartella Packages**  >  **Mixed Reality Toolkit Standard Assets** Audio (Pacchetti Mixed Reality Toolkit Standard Assets  >  **Audio)** per individuare le clip audio:</span><span class="sxs-lookup"><span data-stu-id="84349-138">In the Project window, navigate to **Packages** > **Mixed Reality Toolkit Standard Assets** > **Audio** folder to locate the audio clips:</span></span>

![Finestra Project di Unity con la cartella Audio selezionata](images/mr-learning-base/base-07-section1-step1-3.png)

<span data-ttu-id="84349-140">Nella finestra Hierarchy (Gerarchia) seleziona di nuovo gli **oggetti parte rover** e quindi nella finestra Inspector (Controllo) usa il pulsante **Add Component** (Aggiungi componente) per aggiungere il componente **Audio Sources** (Origini audio) e configuralo come indicato di seguito:</span><span class="sxs-lookup"><span data-stu-id="84349-140">In the Hierarchy window, reselect all the **rover part objects**, then in the Inspector window, use the **Add Component** button to add the **Audio Sources** component and configure it as follows:</span></span>

* <span data-ttu-id="84349-141">Assegna il clip audio **MRTK_Scale_Start** al campo **AudioClip**</span><span class="sxs-lookup"><span data-stu-id="84349-141">Assign the **MRTK_Scale_Start** audio clip to the **AudioClip** field</span></span>
* <span data-ttu-id="84349-142">Deseleziona la casella di controllo **Play On Awake** (Riproduci quando operativo)</span><span class="sxs-lookup"><span data-stu-id="84349-142">Uncheck the **Play On Awake** checkbox</span></span>
* <span data-ttu-id="84349-143">Modifica il campo **Spatial Blend** (Blend spaziale) impostandolo su 1</span><span class="sxs-lookup"><span data-stu-id="84349-143">Change **Spatial Blend** to 1</span></span>

![Unity con tutte le parti rover selezionate e il componente Audio Source aggiunto e configurato](images/mr-learning-base/base-07-section1-step1-4.png)

<span data-ttu-id="84349-145">Nella finestra Hierarchy (Gerarchia) espandi l'oggetto > RoverModel_PlacementHints_XRay > **Parts_PlacementHints** RoverAssembly per visualizzare tutti gli oggetti suggerimento di posizionamento, quindi seleziona la parte rover Camera_part RoverParts > **Camera_Part** e configura il componente **Part Assembly Controller (Script) come** indicato di seguito:</span><span class="sxs-lookup"><span data-stu-id="84349-145">In the Hierarchy window, expand the RoverAssembly > RoverModel_PlacementHints_XRay > **Parts_PlacementHints** object to reveal all of the placement hint objects, then select the Camera_part rover part, RoverParts > **Camera_Part**, and configure the **Part Assembly Controller (Script)** component as follows:</span></span>

* <span data-ttu-id="84349-146">Assegna l'oggetto **Camera_PlacementHint** al campo **Location To Place** (Punto di posizionamento)</span><span class="sxs-lookup"><span data-stu-id="84349-146">Assign the **Camera_PlacementHint** object to the **Location To Place** field</span></span>

![Unity con il componente PartAssemblyController di Camera_Part configurato](images/mr-learning-base/base-07-section1-step1-5.png)

<span data-ttu-id="84349-148">**Ripeti** questo passaggio per ognuno degli oggetti parte rover rimanenti e per l'oggetto RoverAssembly per configurare il componente **Part Assembly Controller (Script)** (Controllo assembly parti - script) come indicato di seguito:</span><span class="sxs-lookup"><span data-stu-id="84349-148">**Repeat** this step for each of the remaining rover part objects and the RoverAssembly object to configure the **Part Assembly Controller (Script)** component as follows:</span></span>

* <span data-ttu-id="84349-149">Per **Generator_Part**, assegna l'oggetto **Generator_PlacementHint** al campo **Location To Place** (Punto di posizionamento)</span><span class="sxs-lookup"><span data-stu-id="84349-149">For the **Generator_Part**, assign the **Generator_PlacementHint** object to the **Location To Place** field</span></span>
* <span data-ttu-id="84349-150">Per **Lights_Part**, assegna l'oggetto **Lights_PlacementHint** al campo **Location To Place** (Punto di posizionamento)</span><span class="sxs-lookup"><span data-stu-id="84349-150">For the **Lights_Part**, assign the **Lights_PlacementHint** object to the **Location To Place** field</span></span>
* <span data-ttu-id="84349-151">Per **UHFAntenna_Part**, assegna l'oggetto **UHFAntenna_PlacementHint** al campo **Location To Place** (Punto di posizionamento)</span><span class="sxs-lookup"><span data-stu-id="84349-151">For the **UHFAntenna_Part**, assign the **UHFAntenna_PlacementHint** object to the **Location To Place** field</span></span>
* <span data-ttu-id="84349-152">Per **Spectrometer_Part**, assegna l'oggetto **Spectrometer_PlacementHint** al campo **Location To Place** (Punto di posizionamento)</span><span class="sxs-lookup"><span data-stu-id="84349-152">For the **Spectrometer_Part**, assign the **Spectrometer_PlacementHint** object to the **Location To Place** field</span></span>
* <span data-ttu-id="84349-153">Per **RoverAssembly**, assegna l'oggetto stesso., ovvero l'oggetto **RoverAssembly** stesso, al campo **Location To Place** (Punto di posizionamento)</span><span class="sxs-lookup"><span data-stu-id="84349-153">For the **RoverAssembly**, assign the object itself, i.e. the same **RoverAssembly** object, to the **Location To Place** field</span></span>

<span data-ttu-id="84349-154">Nella finestra Hierarchy (Gerarchia) seleziona l'oggetto pulsante RoverExplorer > Buttons (Pulsanti) > **Reset** (Reimposta) e quindi nella finestra Inspector (Controllo) configura l'evento **OnClick ()** con supporto per interazioni come indicato di seguito:</span><span class="sxs-lookup"><span data-stu-id="84349-154">In the Hierarchy window, select the RoverExplorer > Buttons > **Reset** button object, then in the Inspector window, configure the Interactable **OnClick ()** event as follows:</span></span>

* <span data-ttu-id="84349-155">Assegna l'oggetto **RoverAssembly** al campo **None (Object)** (Nessuno - Oggetto)</span><span class="sxs-lookup"><span data-stu-id="84349-155">Assign the **RoverAssembly** object to the **None (Object)** field</span></span>
* <span data-ttu-id="84349-156">Dall'elenco a discesa **No Function** (Nessuna funzione) seleziona **PartAssemblyController** > **ResetPlacement ()** per impostare questa funzione come l'azione da eseguire quando viene attivato l'evento</span><span class="sxs-lookup"><span data-stu-id="84349-156">From the **No Function** dropdown, select **PartAssemblyController** > **ResetPlacement ()** to set this function as the action to be executed when the event is triggered</span></span>

![Unity con l'evento OnClick dell'oggetto pulsante Reset configurato](images/mr-learning-base/base-07-section1-step1-6.png)

<span data-ttu-id="84349-158">Se attivi ora la modalità di gioco, puoi usare l'interazione da vicino o da lontano per posizionare le parti rover sul rover.</span><span class="sxs-lookup"><span data-stu-id="84349-158">If you now enter Game mode, you can use near or far interaction to place the rover parts on to the Rover.</span></span> <span data-ttu-id="84349-159">Quando è vicina al suggerimento di posizionamento corrispondente, la parte si blocca in posizione e diventa parte del rover.</span><span class="sxs-lookup"><span data-stu-id="84349-159">Once the part is close to the corresponding placement hint, it will snap into place and become part of the Rover.</span></span> <span data-ttu-id="84349-160">Per reimpostare i posizionamenti, puoi scegliere il pulsante Reset (Reimposta):</span><span class="sxs-lookup"><span data-stu-id="84349-160">To reset the placements, you can press the Reset button:</span></span>

![Visualizzazione suddivisa della modalità di riproduzione in Unity con il pulsante Reset selezionato](images/mr-learning-base/base-07-section1-step1-7.png)

<span data-ttu-id="84349-162">Per altre informazioni sul componente Object Manipulator (Manipolatore oggetti) e sulle relative proprietà associate, puoi visitare la guida su [tale componente](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/object-manipulator) nel [portale della documentazione di MRTK](/windows/mixed-reality/mrtk-unity/).</span><span class="sxs-lookup"><span data-stu-id="84349-162">To learn more about the Object Manipulator component and its associated properties, you can visit the [Object Manipulator](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/object-manipulator) guide in the [MRTK Documentation Portal](/windows/mixed-reality/mrtk-unity/).</span></span>

## <a name="adding-bounds-control"></a><span data-ttu-id="84349-163">Aggiunta del controllo Bounds</span><span class="sxs-lookup"><span data-stu-id="84349-163">Adding Bounds Control</span></span>

<span data-ttu-id="84349-164">Controllo limiti rende più semplice e intuitivo modificare gli oggetti con una mano per l'interazione da vicino e da lontano fornendo handle che possono essere usati per il ridimensionamento e la rotazione.</span><span class="sxs-lookup"><span data-stu-id="84349-164">Bounds Control makes it easier and more intuitive to manipulate objects with one hand for both near and far interaction by providing handles that can be used for scaling and rotating.</span></span>

<span data-ttu-id="84349-165">In questo esempio si aggiungerà un boundsControl all'oggetto RoverExplorer in modo che l'intera esperienza possa essere facilmente spostata, ruotata e ridimensionata.</span><span class="sxs-lookup"><span data-stu-id="84349-165">In this example, you will add a BoundsControl to the RoverExplorer object so the whole experience can easily be moved, rotated, and scaled.</span></span> <span data-ttu-id="84349-166">Inoltre, si configurerà il menu in modo da poter attivare e disattivare il controllo Limiti.</span><span class="sxs-lookup"><span data-stu-id="84349-166">Additionally, you will configure the Menu so you can turn the Bounds Control on and off.</span></span>

<span data-ttu-id="84349-167">Nella finestra Hierarchy (Gerarchia) seleziona l'oggetto **RoverExplorer**, quindi nella finestra Inspector (Controllo) usa il pulsante **Add Component** (Aggiungi componente) per aggiungere i componenti seguenti:</span><span class="sxs-lookup"><span data-stu-id="84349-167">In the Hierarchy window, select the **RoverExplorer** object, then in the Inspector window, use the **Add Component** button to add the following components:</span></span>

* <span data-ttu-id="84349-168">**Componente BoundsControl**</span><span class="sxs-lookup"><span data-stu-id="84349-168">**BoundsControl** component</span></span>
* <span data-ttu-id="84349-169">Componente **Object Manipulator (Script)** (Manipolatore oggetti - script)</span><span class="sxs-lookup"><span data-stu-id="84349-169">**Object Manipulator (Script)** component</span></span>

<span data-ttu-id="84349-170">Deselezionare **quindi la** casella di controllo accanto a tutti i componenti per renderli **disabilitati per** impostazione predefinita:</span><span class="sxs-lookup"><span data-stu-id="84349-170">Then **uncheck** the checkbox next to all the components to make them **disabled** by default:</span></span>

![Unity con l'oggetto RoverExplorer selezionato e i componenti aggiunti e disabilitati](images/mr-learning-base/base-07-section2-step1-1.png)

> [!NOTE]
> <span data-ttu-id="84349-172">La visualizzazione Controllo limiti viene creata in fase di esecuzione e, pertanto, non è visibile prima di entrare nella modalità di gioco.</span><span class="sxs-lookup"><span data-stu-id="84349-172">The Bounds Control visualization is created at runtime and, therefore, not visible before you enter Game mode.</span></span>

> [!NOTE]
> <span data-ttu-id="84349-173">Il manipolatore di oggetti (script) aggiunge automaticamente Gestione vincoli (script)</span><span class="sxs-lookup"><span data-stu-id="84349-173">The Object Manipulator (Script) automatically adds Constraint Manager (Script)</span></span>

<span data-ttu-id="84349-174">Nella finestra Hierarchy (Gerarchia) espandi l'oggetto Menu > **ButtonCollection** per visualizzare i quattro pulsanti e rinomina il terzo pulsante **BoundsControl_Enable**, quindi nella finestra Inspector (Controllo) configura il componente **Button Config Helper (Script) (Helper** configurazione pulsanti - Script) come indicato di seguito:</span><span class="sxs-lookup"><span data-stu-id="84349-174">In the Hierarchy window, expand the Menu > **ButtonCollection** object to reveal the four buttons and rename the third button to **BoundsControl_Enable**, then in the Inspector window, configure the **Button Config Helper (Script)** component as follows:</span></span>

* <span data-ttu-id="84349-175">Imposta **Main Label Text** (Testo etichetta principale) su **Enable** (Abilita)</span><span class="sxs-lookup"><span data-stu-id="84349-175">Change the **Main Label Text** to **Enable**</span></span>
* <span data-ttu-id="84349-176">Assegna l'oggetto **RoverExplorer** al campo **None (Object)** (Nessuno - Oggetto)</span><span class="sxs-lookup"><span data-stu-id="84349-176">Assign the **RoverExplorer** object to the **None (Object)** field</span></span>
* <span data-ttu-id="84349-177">**Nell'elenco a discesa No Function** (Nessuna funzione) selezionare **BoundsControl**  >  **bool Enabled** per aggiornare il valore di questa proprietà quando viene attivato l'evento</span><span class="sxs-lookup"><span data-stu-id="84349-177">From the **No Function** dropdown, select **BoundsControl** > **bool Enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="84349-178">Verifica che la casella di controllo dell'argomento sia **selezionata**</span><span class="sxs-lookup"><span data-stu-id="84349-178">Verify that the argument checkbox is **checked**</span></span>
* <span data-ttu-id="84349-179">Fai clic sull'icona **+** piccola per aggiungere un altro evento</span><span class="sxs-lookup"><span data-stu-id="84349-179">Click the small **+** icon to add another event</span></span>
* <span data-ttu-id="84349-180">Assegna l'oggetto **RoverExplorer** al campo **None (Object)** (Nessuno - Oggetto)</span><span class="sxs-lookup"><span data-stu-id="84349-180">Assign the **RoverExplorer** object to the **None (Object)** field</span></span>
* <span data-ttu-id="84349-181">Dall'elenco a discesa **No Function** (Nessuna funzione) seleziona **ObjectManipulator** > **bool Enabled** per aggiornare il valore di questa proprietà quando viene attivato l'evento</span><span class="sxs-lookup"><span data-stu-id="84349-181">From the **No Function** dropdown, select **ObjectManipulator** > **bool Enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="84349-182">Verifica che la casella di controllo dell'argomento sia **selezionata**</span><span class="sxs-lookup"><span data-stu-id="84349-182">Verify that the argument checkbox is **checked**</span></span>
* <span data-ttu-id="84349-183">Lasciare **l'icona** dell'icona "cubo con controllo limiti"</span><span class="sxs-lookup"><span data-stu-id="84349-183">Leave the **Icon** as the 'cube with bounds control' icon</span></span>

![Unity con l BoundsControl_Enable o object button selezionato e il componente Button Config Helper configurato](images/mr-learning-base/base-07-section2-step1-2.png)

<span data-ttu-id="84349-185">Rinominare l'ultimo pulsante BoundsControl_Disable , quindi nella finestra Inspector (Controllo) configurare il componente **Button Config Helper (Script) (Helper configurazione** pulsanti - Script) come indicato di seguito:</span><span class="sxs-lookup"><span data-stu-id="84349-185">Rename the forth and last button to **BoundsControl_Disable**, then in the Inspector window, configure the **Button Config Helper (Script)** component as follows:</span></span>

* <span data-ttu-id="84349-186">Imposta **Main Label Text** (Testo etichetta principale) su **Disable** (Disabilita)</span><span class="sxs-lookup"><span data-stu-id="84349-186">Change the **Main Label Text** to **Disable**</span></span>
* <span data-ttu-id="84349-187">Assegna l'oggetto **RoverExplorer** al campo **None (Object)** (Nessuno - Oggetto)</span><span class="sxs-lookup"><span data-stu-id="84349-187">Assign the **RoverExplorer** object to the **None (Object)** field</span></span>
* <span data-ttu-id="84349-188">**Nell'elenco a discesa No Function** (Nessuna funzione) selezionare **BoundsControl**  >  **bool Enabled** per aggiornare il valore di questa proprietà quando viene attivato l'evento</span><span class="sxs-lookup"><span data-stu-id="84349-188">From the **No Function** dropdown, select **BoundsControl** > **bool Enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="84349-189">Verificare che la casella di controllo dell'argomento sia **deselezionata**</span><span class="sxs-lookup"><span data-stu-id="84349-189">Verify that the argument checkbox is **unchecked**</span></span>
* <span data-ttu-id="84349-190">Fai clic sull'icona **+** piccola per aggiungere un altro evento</span><span class="sxs-lookup"><span data-stu-id="84349-190">Click the small **+** icon to add another event</span></span>
* <span data-ttu-id="84349-191">Assegna l'oggetto **RoverExplorer** al campo **None (Object)** (Nessuno - Oggetto)</span><span class="sxs-lookup"><span data-stu-id="84349-191">Assign the **RoverExplorer** object to the **None (Object)** field</span></span>
* <span data-ttu-id="84349-192">Dall'elenco a discesa **No Function** (Nessuna funzione) seleziona **ObjectManipulator** > **bool Enabled** per aggiornare il valore di questa proprietà quando viene attivato l'evento</span><span class="sxs-lookup"><span data-stu-id="84349-192">From the **No Function** dropdown, select **ObjectManipulator** > **bool Enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="84349-193">Verifica che la casella di controllo dell'argomento sia **deselezionata**</span><span class="sxs-lookup"><span data-stu-id="84349-193">Verify that the argument checkbox is **unchecked**</span></span>
* <span data-ttu-id="84349-194">Modificare **l'icona** con l'icona del controllo cubo con limiti</span><span class="sxs-lookup"><span data-stu-id="84349-194">Change the **Icon** to the 'cube with bounds control" icon</span></span>

![Unity con l BoundsControl_Disable o object button selezionato e il componente Button Config Helper configurato](images/mr-learning-base/base-07-section2-step1-3.png)

<span data-ttu-id="84349-196">Se ora si passa alla modalità di gioco e si abilita il controllo limiti facendo clic sul pulsante Abilita, è possibile usare l'interazione da vicino o da lontano per spostare, ruotare e ridimensionare il controllo limiti e usare il pulsante Disabilita per disabilitare di nuovo il controllo limiti:</span><span class="sxs-lookup"><span data-stu-id="84349-196">If you now enter Game mode and enable the Bounds Control by clicking the Enable button, you can use near or far interaction to move, rotate, and scale the Bounds Control, and use the Disable button to disable the Bounds Control again:</span></span>

![Doppia visualizzazione della modalità di riproduzione unity con il controllo Bounds modificato](images/mr-learning-base/base-07-section2-step1-4.png)

<span data-ttu-id="84349-198">Per altre informazioni sul componente Bounds Control e sulle proprietà associate, è possibile visitare la guida [Bounds Control](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/bounds-control) (Controllo limiti) nel portale [della documentazione di MRTK.](/windows/mixed-reality/mrtk-unity/)</span><span class="sxs-lookup"><span data-stu-id="84349-198">To learn more about the Bounds Control component and its associated properties, you can visit the [Bounds Control](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/bounds-control) guide in the [MRTK Documentation Portal](/windows/mixed-reality/mrtk-unity/).</span></span>

## <a name="congratulations"></a><span data-ttu-id="84349-199">Lezione completata</span><span class="sxs-lookup"><span data-stu-id="84349-199">Congratulations</span></span>

<span data-ttu-id="84349-200">In questa esercitazione hai appreso come abilitare la manipolazione da vicino e da lontano degli oggetti 3D e limitare i tipi di manipolazione consentiti.</span><span class="sxs-lookup"><span data-stu-id="84349-200">In this tutorial, you learned how to enable near and far manipulation for 3D objects and how to limit the allowed types of manipulation.</span></span> <span data-ttu-id="84349-201">Si è anche appreso come aggiungere il controllo Bounds intorno agli oggetti 3D per semplificare il controllo della manipolazione degli oggetti.</span><span class="sxs-lookup"><span data-stu-id="84349-201">You also learned how to add Bounds Control around 3D objects to make it easier to control the object manipulation.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="84349-202">Esercitazione successiva: 8. Uso del tracciamento oculare</span><span class="sxs-lookup"><span data-stu-id="84349-202">Next Tutorial: 8. Using eye-tracking</span></span>](mr-learning-base-08.md)
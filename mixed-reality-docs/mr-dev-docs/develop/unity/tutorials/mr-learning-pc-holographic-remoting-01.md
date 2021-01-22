---
title: Introduzione a Holographic Remoting per PC
description: In questo corso viene illustrato come trasmettere in remoto le applicazioni di realtà mista da PC a HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 07/29/2020
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens, holographic remoting per PC, descrizioni comandi, tracciamento oculare
ms.localizationpriority: high
ms.openlocfilehash: d8c7de8a93a32107afe67a1d0375612ab6245be9
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/20/2021
ms.locfileid: "98581963"
---
# <a name="1-getting-started-with-pc-holographic-remoting"></a><span data-ttu-id="066bd-104">1. Introduzione a Holographic Remoting per PC</span><span class="sxs-lookup"><span data-stu-id="066bd-104">1. Getting started with PC Holographic Remoting</span></span>

<span data-ttu-id="066bd-105">Queste sono le esercitazioni su HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="066bd-105">Welcome to the HoloLens 2 tutorials.</span></span> <span data-ttu-id="066bd-106">In questa serie di esercitazioni in due parti verrà illustrato come creare una dimostrazione dell'esperienza di realtà mista e come creare un'app per PC per Holographic Remoting.</span><span class="sxs-lookup"><span data-stu-id="066bd-106">In this two-part tutorial series, you will learn how to create a mixed reality experience demonstration and how to create a PC app for Holographic Remoting.</span></span>

<span data-ttu-id="066bd-107">In questa esercitazione verrà illustrato come creare un'esperienza di realtà mista.</span><span class="sxs-lookup"><span data-stu-id="066bd-107">In this tutorial, you'll learn how to create a mixed reality experience.</span></span> <span data-ttu-id="066bd-108">Verranno infatti illustrati gli elementi dell'interfaccia utente e le funzionalità di manipolazione del modello 3D, ritaglio del modello e tracciamento oculare.</span><span class="sxs-lookup"><span data-stu-id="066bd-108">It will demonstrate UI elements, 3D model manipulation, model clipping, and eye-tracking features.</span></span>

<span data-ttu-id="066bd-109">Nella seconda esercitazione, [Creare un'applicazione per Holographic Remoting](mr-learning-pc-holographic-remoting-02.md), apprenderai come creare un'app per PC per Holographic Remoting.</span><span class="sxs-lookup"><span data-stu-id="066bd-109">In the second tutorial, [Create a Holographic Remoting application](mr-learning-pc-holographic-remoting-02.md), you will learn how to create a PC app for Holographic Remoting.</span></span> <span data-ttu-id="066bd-110">Apprenderai inoltre come effettuare la connessione a HoloLens 2 in qualsiasi momento, fornendo un modo per visualizzare il contenuto 3D in realtà mista.</span><span class="sxs-lookup"><span data-stu-id="066bd-110">And connect to HoloLens 2 at any point, providing a way to visualize 3D content in mixed reality.</span></span>

## <a name="objectives"></a><span data-ttu-id="066bd-111">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="066bd-111">Objectives</span></span>

* <span data-ttu-id="066bd-112">Importare gli asset e configurare la scena</span><span class="sxs-lookup"><span data-stu-id="066bd-112">Import assets and set up the scene</span></span>
* <span data-ttu-id="066bd-113">Interagire con gli ologrammi usando pulsanti ed elementi dell'interfaccia utente</span><span class="sxs-lookup"><span data-stu-id="066bd-113">Interact with holograms using UI elements and buttons</span></span>
* <span data-ttu-id="066bd-114">Configurare gli oggetti 3D per la funzionalità di ritaglio</span><span class="sxs-lookup"><span data-stu-id="066bd-114">Configure 3D objects for the clipping feature</span></span>
* <span data-ttu-id="066bd-115">Apprendere come attivare le descrizioni comandi con il tracciamento oculare</span><span class="sxs-lookup"><span data-stu-id="066bd-115">Learn about activating tooltips with eye-tracking</span></span>

## <a name="prerequisites"></a><span data-ttu-id="066bd-116">Prerequisiti</span><span class="sxs-lookup"><span data-stu-id="066bd-116">Prerequisites</span></span>

* <span data-ttu-id="066bd-117">Un PC Windows 10 configurato in cui siano [installati gli strumenti](../../install-the-tools.md) corretti</span><span class="sxs-lookup"><span data-stu-id="066bd-117">A Windows 10 PC configured with the correct [tools installed](../../install-the-tools.md)</span></span>
* <span data-ttu-id="066bd-118">Conoscenza della programmazione C# di base</span><span class="sxs-lookup"><span data-stu-id="066bd-118">Basic c# programming knowledge</span></span>
* <span data-ttu-id="066bd-119">Un dispositivo HoloLens 2 [configurato per lo sviluppo](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)</span><span class="sxs-lookup"><span data-stu-id="066bd-119">A HoloLens 2 device [configured for development](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)</span></span>
* <span data-ttu-id="066bd-120"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> con Unity 2019 LTS installato e il modulo di supporto per la compilazione UWP (Universal Windows Platform) aggiunto</span><span class="sxs-lookup"><span data-stu-id="066bd-120"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019 LTS mounted, and the Universal Windows Platform Build Support module added</span></span>

<span data-ttu-id="066bd-121">Prima di proseguire, è **consigliabile** completare la serie di [Esercitazioni introduttive](mr-learning-base-01.md) o alcune esperienze pregresse di base con Unity e MRTK.</span><span class="sxs-lookup"><span data-stu-id="066bd-121">We **strongly recommend** completing the [Getting started](mr-learning-base-01.md) tutorials series or some basic prior experience with Unity and MRTK before continuing.</span></span>

> [!IMPORTANT]
> * <span data-ttu-id="066bd-122">La versione di Unity consigliata per questa serie di esercitazioni è Unity 2019 LTS.</span><span class="sxs-lookup"><span data-stu-id="066bd-122">The recommended Unity version for this tutorial series is Unity 2019 LTS.</span></span> <span data-ttu-id="066bd-123">Questa istruzione sostituisce gli eventuali requisiti o suggerimenti relativi alla versione di Unity indicati negli argomenti visualizzabili facendo clic sui collegamenti dei prerequisiti sopra riportati.</span><span class="sxs-lookup"><span data-stu-id="066bd-123">It supersedes any Unity version requirements or recommendations stated in the prerequisites linked above.</span></span>
> * <span data-ttu-id="066bd-124">Holographic Remoting con i progetti MRTK funzionerà solo con XR legacy.</span><span class="sxs-lookup"><span data-stu-id="066bd-124">Holographic Remoting with MRTK projects will only work with legacy XR.</span></span> <span data-ttu-id="066bd-125">L'SDK di XR non è attualmente supportato.</span><span class="sxs-lookup"><span data-stu-id="066bd-125">XR SDK is not supported at this time.</span></span>

## <a name="creating-and-preparing-the-unity-project"></a><span data-ttu-id="066bd-126">Creazione e preparazione del progetto Unity</span><span class="sxs-lookup"><span data-stu-id="066bd-126">Creating and preparing the Unity project</span></span>

<span data-ttu-id="066bd-127">In questa sezione creerai un nuovo progetto Unity per prepararti allo sviluppo con MRTK.</span><span class="sxs-lookup"><span data-stu-id="066bd-127">In this section, you will create a new Unity project and get it ready for MRTK development.</span></span>

<span data-ttu-id="066bd-128">A questo scopo, segui prima l'esercitazione [Inizializzazione del progetto e prima applicazione](mr-learning-base-02.md), escluse le istruzioni della sezione [Compilare l'applicazione nel dispositivo](mr-learning-base-02.md#building-your-application-to-your-hololens-2), che include i passaggi seguenti:</span><span class="sxs-lookup"><span data-stu-id="066bd-128">For this, first follow the [Initializing your project and first application](mr-learning-base-02.md), excluding the [Build your application to your device](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions, which includes the following steps:</span></span>

1. <span data-ttu-id="066bd-129">[Creazione del progetto Unity](mr-learning-base-02.md#creating-the-unity-project) e assegnazione di un nome appropriato, ad esempio *MRTK Tutorials*</span><span class="sxs-lookup"><span data-stu-id="066bd-129">[Creating the Unity project](mr-learning-base-02.md#creating-the-unity-project) and give it a suitable name, for example, *MRTK Tutorials*</span></span>

2. [<span data-ttu-id="066bd-130">Passaggio a un'altra piattaforma di compilazione</span><span class="sxs-lookup"><span data-stu-id="066bd-130">Switching the build platform</span></span>](mr-learning-base-02.md#switching-the-build-platform)

3. [<span data-ttu-id="066bd-131">Importazione delle risorse essenziali TextMeshPro</span><span class="sxs-lookup"><span data-stu-id="066bd-131">Importing the TextMeshPro Essential Resources</span></span>](mr-learning-base-02.md#importing-the-textmeshpro-essential-resources)

4. [<span data-ttu-id="066bd-132">Importazione di Mixed Reality Toolkit</span><span class="sxs-lookup"><span data-stu-id="066bd-132">Importing the Mixed Reality Toolkit</span></span>](mr-learning-base-02.md#importing-the-mixed-reality-toolkit)

5. [<span data-ttu-id="066bd-133">Configurazione del progetto Unity</span><span class="sxs-lookup"><span data-stu-id="066bd-133">Configuring the Unity project</span></span>](mr-learning-base-02.md#configuring-the-unity-project)

6. <span data-ttu-id="066bd-134">[Creazione e impostazione della scena](mr-learning-base-02.md#creating-and-configuring-the-scene) e assegnazione di un nome appropriato, ad esempio **PC Holographic Remoting**</span><span class="sxs-lookup"><span data-stu-id="066bd-134">[Creating and setting the scene](mr-learning-base-02.md#creating-and-configuring-the-scene) and give the scene a suitable name, for example, **PC Holographic Remoting**</span></span>

<span data-ttu-id="066bd-135">Segui quindi le istruzioni riportate in [Modifica delle opzioni di visualizzazione di consapevolezza spaziale](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) per impostare **DefaultHoloLens2ConfigurationProfile** come profilo di configurazione MRTK per la scena.</span><span class="sxs-lookup"><span data-stu-id="066bd-135">Then follow the [Changing the Spatial Awareness Display Option](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) instructions to change the MRTK configuration profile for your scene to the **DefaultHoloLens2ConfigurationProfile**.</span></span> <span data-ttu-id="066bd-136">Modifica le opzioni di visualizzazione per la mesh di consapevolezza spaziale impostando **Occlusion** (Occlusione).</span><span class="sxs-lookup"><span data-stu-id="066bd-136">Change the display options for the spatial awareness mesh to **Occlusion**.</span></span>

## <a name="importing-the-tutorial-assets"></a><span data-ttu-id="066bd-137">Importazione degli asset dell'esercitazione</span><span class="sxs-lookup"><span data-stu-id="066bd-137">Importing the tutorial assets</span></span>

<span data-ttu-id="066bd-138">Scarica e **importa** [MRTK.Tutorials.PCHolographicRemoting.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/pc-holographic-remoting-v2.4.0/MRTK.Tutorials.PCHolographicRemoting.unitypackage).</span><span class="sxs-lookup"><span data-stu-id="066bd-138">Download and **import** the [MRTK.Tutorials.PCHolographicRemoting.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/pc-holographic-remoting-v2.4.0/MRTK.Tutorials.PCHolographicRemoting.unitypackage).</span></span>

>[!TIP]
> <span data-ttu-id="066bd-139">Per rivedere la procedura di importazione di un pacchetto personalizzato di Unity, puoi fare riferimento alle istruzioni contenute in [Importare Mixed Reality Toolkit](./mr-learning-base-02.md#importing-the-mixed-reality-toolkit).</span><span class="sxs-lookup"><span data-stu-id="066bd-139">For a reminder on how to import a Unity custom package, you can refer to the [Import the Mixed Reality Toolkit](./mr-learning-base-02.md#importing-the-mixed-reality-toolkit) instructions.</span></span>

<span data-ttu-id="066bd-140">Dopo l'importazione degli asset dell'esercitazione, la finestra Project (Progetto) avrà un aspetto simile al seguente:</span><span class="sxs-lookup"><span data-stu-id="066bd-140">After importing the tutorial assets, your Project window should look similar to this:</span></span>

![Finestre Hierarchy, Scene e Project di Unity dopo l'importazione degli asset dell'esercitazione](images/mrlearning-pc-holographic-remoting/Tutorial1-Section2-Step1-1.png)

## <a name="configuring-and-preparing-the-scene"></a><span data-ttu-id="066bd-142">Configurazione e preparazione della scena</span><span class="sxs-lookup"><span data-stu-id="066bd-142">Configuring and preparing the scene</span></span>

<span data-ttu-id="066bd-143">In questa sezione preparerai la scena aggiungendo alcuni dei prefab dell'esercitazione.</span><span class="sxs-lookup"><span data-stu-id="066bd-143">In this section, you will prepare the scene by adding some of the tutorial prefabs.</span></span>

<span data-ttu-id="066bd-144">Nella finestra Project (Progetto) passa alla cartella **Assets** (Asset)  > **MRTK.Tutorials.PCHolograhicRemoting** > **Prefabs** (Prefab).</span><span class="sxs-lookup"><span data-stu-id="066bd-144">In the Project window, navigate to **Assets** > **MRTK.Tutorials.PCHolograhicRemoting** > **Prefabs** folder.</span></span> <span data-ttu-id="066bd-145">Tenendo premuto il pulsante CTRL, fai clic sui sei prefab riportati di seguito.</span><span class="sxs-lookup"><span data-stu-id="066bd-145">While holding down the CTRL button, click on the below six prefabs.</span></span>

* <span data-ttu-id="066bd-146">ButtonParent</span><span class="sxs-lookup"><span data-stu-id="066bd-146">ButtonParent</span></span>
* <span data-ttu-id="066bd-147">ClippingObjects</span><span class="sxs-lookup"><span data-stu-id="066bd-147">ClippingObjects</span></span>
* <span data-ttu-id="066bd-148">HandSpatialMapButton</span><span class="sxs-lookup"><span data-stu-id="066bd-148">HandSpatialMapButton</span></span>
* <span data-ttu-id="066bd-149">Istruzioni</span><span class="sxs-lookup"><span data-stu-id="066bd-149">Instructions</span></span>
* <span data-ttu-id="066bd-150">ModelParent</span><span class="sxs-lookup"><span data-stu-id="066bd-150">ModelParent</span></span>
* <span data-ttu-id="066bd-151">Piattaforma</span><span class="sxs-lookup"><span data-stu-id="066bd-151">Platform</span></span>

![Unity con prefab da aggiungere alla scena selezionata](images/mrlearning-pc-holographic-remoting/Tutorial1-Section3-Step1-1.png)

<span data-ttu-id="066bd-153">Trascina e rilascia questi modelli dalla cartella dei prefab nella **finestra Hierarchy** (Gerarchia).</span><span class="sxs-lookup"><span data-stu-id="066bd-153">Drag-and-drop these models from the prefabs folder into the **Hierarchy window**.</span></span>

![Unity con i prefab appena aggiunti ancora selezionati](images/mrlearning-pc-holographic-remoting/Tutorial1-Section3-Step1-2.png)

<span data-ttu-id="066bd-155">Per concentrarti sugli oggetti nella scena, puoi fare doppio clic sull'oggetto **ModelParent** e quindi fare di nuovo leggermente zoom avanti:</span><span class="sxs-lookup"><span data-stu-id="066bd-155">To focus in on the objects in the scene, you can double-click on the **ModelParent** object, and then zoom slightly in again:</span></span>

![Unity con l'oggetto ModelParent nello stato attivo](images/mrlearning-pc-holographic-remoting/Tutorial1-Section3-Step1-3.png)

> [!TIP]
> <span data-ttu-id="066bd-157">Se trovi che le icone grandi nella scena, come quelle a forma di "T", siano motivo di distrazione, puoi nasconderle <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">disattivando i gizmo</a>.</span><span class="sxs-lookup"><span data-stu-id="066bd-157">If you find the large icons in your scene, such as, the large framed 'T' icons distracting, you can hide these by <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">toggling the Gizmos</a> to the off position.</span></span>

## <a name="configuring-the-buttons-to-operate-the-scene"></a><span data-ttu-id="066bd-158">Configurazione dei pulsanti per il funzionamento della scena</span><span class="sxs-lookup"><span data-stu-id="066bd-158">Configuring the buttons to operate the scene</span></span>

<span data-ttu-id="066bd-159">In questa sezione aggiungerai nella scena gli script per creare eventi pulsante a dimostrazione delle nozioni di base sul passaggio a un altro modello e sulla funzionalità di ritaglio.</span><span class="sxs-lookup"><span data-stu-id="066bd-159">In this section, you will add scripts into the scene to create button events demonstrating the fundamentals of model switching and clipping functionality.</span></span>

### <a name="1-configuring-the-interactable-script-component"></a><span data-ttu-id="066bd-160">1. Configurazione del componente Interactable (Script) (Con supporto per interazioni - Script)</span><span class="sxs-lookup"><span data-stu-id="066bd-160">1. Configuring the Interactable (Script) component</span></span>

<span data-ttu-id="066bd-161">Nella finestra Hierarchy (Gerarchia) espandi l'oggetto **ButtonParent** e seleziona **NextButton**.</span><span class="sxs-lookup"><span data-stu-id="066bd-161">In the Hierarchy window, expand the **ButtonParent** object and select the **NextButton**.</span></span> <span data-ttu-id="066bd-162">Nella finestra Inspector (Controllo) individua il componente **Interactable (Script)** (Con supporto per interazioni - Script) e fai clic sull'icona **+** sotto l'evento **OnClick ()** .</span><span class="sxs-lookup"><span data-stu-id="066bd-162">In the Inspector window, locate the **Interactable (Script)** component and click on **+** icon under **OnClick ()** event.</span></span>

![Unity con l'evento OnClick di NextButton aggiunto](images/mrlearning-pc-holographic-remoting/Tutorial1-Section4-Step1-1.png)

<span data-ttu-id="066bd-164">Con l'oggetto **NextButton** ancora selezionato nella finestra Hierarchy (Gerarchia), fai clic e trascina l'oggetto **ButtonParent** dalla finestra Hierarchy (Gerarchia) nel campo **None (Object)** (Nessuno - Oggetto) vuoto dell'evento appena aggiunto per fare in modo che l'oggetto ButtonParent rimanga in ascolto dell'evento di clic del pulsante attivato a partire da questo pulsante:</span><span class="sxs-lookup"><span data-stu-id="066bd-164">With the **NextButton** object still selected in the Hierarchy window, click-and-drag the **ButtonParent** object from the Hierarchy window into the empty **None (Object)** field of the event you just added to make the ButtonParent object listen for button click event from this button:</span></span>

![Unity con il listener di eventi OnClick di NextButton configurato](images/mrlearning-pc-holographic-remoting/Tutorial1-Section4-Step1-2.png)

<span data-ttu-id="066bd-166">Fai clic sull'elenco a discesa **No Function** (Nessuna funzione) dello stesso evento.</span><span class="sxs-lookup"><span data-stu-id="066bd-166">Click the **No Function** dropdown of the same event.</span></span> <span data-ttu-id="066bd-167">Seleziona quindi **ViewButtonControl** > **NextModel ()** per impostare la funzione **NextModel ()** come l'azione che viene attivata quando l'evento di pulsante premuto viene attivato a partire da questo pulsante:</span><span class="sxs-lookup"><span data-stu-id="066bd-167">Then select **ViewButtonControl** > **NextModel ()** to set the **NextModel ()** function as the action that is triggered when the button pressed events is fired from this button:</span></span>

![Unity con il percorso di selezione dell'azione dell'evento OnClick di NextButton](images/mrlearning-pc-holographic-remoting/Tutorial1-Section4-Step1-3.png)

### <a name="2-configuring-the-remaining-buttons"></a><span data-ttu-id="066bd-169">2. Configurazione dei pulsanti rimanenti</span><span class="sxs-lookup"><span data-stu-id="066bd-169">2. Configuring the remaining buttons</span></span>

<span data-ttu-id="066bd-170">Per ognuno dei pulsanti rimanenti, completa il processo descritto in precedenza per assegnare funzioni agli eventi **OnClick ()** :</span><span class="sxs-lookup"><span data-stu-id="066bd-170">For each of the remaining buttons, complete the process outlined above to assign functions to the **OnClick ()** events:</span></span>

* <span data-ttu-id="066bd-171">Per l'oggetto PreviousButton, assegna la funzione **ViewButtonControl** > **PreviousModel ()** .</span><span class="sxs-lookup"><span data-stu-id="066bd-171">For PreviousButton object, assign the **ViewButtonContro** l > **PreviousModel ()** function.</span></span>

* <span data-ttu-id="066bd-172">Per ClippingButton, seleziona la funzione **ToggleButton** > **ToggleClipping ()** .</span><span class="sxs-lookup"><span data-stu-id="066bd-172">For ClippingButton select **ToggleButton** > **ToggleClipping ()** function.</span></span>

### <a name="3-configuring-the-view-button-control-script--and-toggle-button-script-components"></a><span data-ttu-id="066bd-173">3. Configurazione dei componenti View Button Control (Script) (Controllo pulsante di visualizzazione - Script) e Toggle Button (Script) (Interruttore - Script)</span><span class="sxs-lookup"><span data-stu-id="066bd-173">3. Configuring the View Button Control (Script)  and Toggle Button (Script) components</span></span>

<span data-ttu-id="066bd-174">Ora i pulsanti sono configurati per illustrare il funzionamento del passaggio a un altro modello e la funzionalità di ritaglio.</span><span class="sxs-lookup"><span data-stu-id="066bd-174">Now your buttons are configured to demonstrate the model switching and clipping functionality.</span></span> <span data-ttu-id="066bd-175">È il momento di aggiungere modelli 3D e gli oggetti di ritaglio allo script.</span><span class="sxs-lookup"><span data-stu-id="066bd-175">It is time to add 3D models and the clipping objects to the script.</span></span>

<span data-ttu-id="066bd-176">Per la dimostrazione sono stati forniti sei modelli 3D diversi. Espandere \**_ModelParentobject_* _ per esporre questi modelli 3D.</span><span class="sxs-lookup"><span data-stu-id="066bd-176">We have provided six different 3D models for demonstration, expand the \**_ModelParentobject_* _ to expose these 3D models.</span></span>

<span data-ttu-id="066bd-177">Con l'oggetto ButtonParent ancora selezionato nella finestra Hierarchy (Gerarchia), individuare nella finestra Inspector (Controllo) il componente _ *View Button Control (Script)* \* (Controllo pulsante di visualizzazione - Script) ed espandere la variabile **Models** (Modelli).</span><span class="sxs-lookup"><span data-stu-id="066bd-177">With the ButtonParent object still selected in the Hierarchy window, in the Inspector window, locate the _ *View Button Control (Script)*\* component and expand the **Models** variable.</span></span>

<span data-ttu-id="066bd-178">Nel campo **Size** (Dimensione) immetti il numero di modelli 3D che vuoi avere nella scena.</span><span class="sxs-lookup"><span data-stu-id="066bd-178">In the **Size** field, enter the number of 3D models you would like to have in your scene.</span></span> <span data-ttu-id="066bd-179">In questo caso, 6.</span><span class="sxs-lookup"><span data-stu-id="066bd-179">In this case, it would be six.</span></span> <span data-ttu-id="066bd-180">Verranno creati i campi per l'aggiunta di nuovi modelli 3D.</span><span class="sxs-lookup"><span data-stu-id="066bd-180">It will create fields for adding new 3D models.</span></span>

![Unity con i campi del componente di script ViewButtonControl](images/mrlearning-pc-holographic-remoting/Tutorial1-Section4-Step3-1.png)

<span data-ttu-id="066bd-182">Trascina e rilascia ogni oggetto figlio dell'oggetto ModelParent in questi campi.</span><span class="sxs-lookup"><span data-stu-id="066bd-182">Drag and drop each child object of ModelParent Object into these fields.</span></span>

![Unity con i campi del componente di script ViewButtonControl configurati](images/mrlearning-pc-holographic-remoting/Tutorial1-Section4-Step3-2.png)

<span data-ttu-id="066bd-184">Trascina e rilascia l'oggetto **ClippingObjects** dalla finestra Hierarchy (Gerarchia) nel campo **Clipping Object** (Oggetto di ritaglio) del componente **Toggle Button (Script)** (Interruttore - Script).</span><span class="sxs-lookup"><span data-stu-id="066bd-184">Drag and drop the  **ClippingObjects** object from the Hierarchy window to the  **Toggle Button (Script)** component **Clipping Object** field.</span></span>
>[!NOTE]
><span data-ttu-id="066bd-185">Rimani solo nell'oggetto padre del pulsante.</span><span class="sxs-lookup"><span data-stu-id="066bd-185">Stay in button parent object only.</span></span>

![Unity con il campo del componente di script ToggleButton configurato](images/mrlearning-pc-holographic-remoting/Tutorial1-Section4-Step3-3.png)

<span data-ttu-id="066bd-187">Nella finestra Hierarchy (Gerarchia) seleziona il prefab **ClippingObjects** e abilitalo nella finestra Inspector (Controllo) per attivare gli oggetti di ritaglio.</span><span class="sxs-lookup"><span data-stu-id="066bd-187">In the Hierarchy window, select the **ClippingObjects** prefab and enable it in the Inspector window to turn on the Clipping objects.</span></span>

## <a name="configuring-the-clipping-objects-to-enable-clipping-feature"></a><span data-ttu-id="066bd-188">Configurazione degli oggetti di ritaglio per abilitare la funzionalità di ritaglio</span><span class="sxs-lookup"><span data-stu-id="066bd-188">Configuring the clipping objects to enable clipping feature</span></span>

<span data-ttu-id="066bd-189">In questa sezione aggiungerai il renderer degli oggetti figlio dell'oggetto MarsCuriosityRover in un singolo oggetto di ritaglio per illustrare il funzionamento del ritaglio del modello MarsCuriosityRover.</span><span class="sxs-lookup"><span data-stu-id="066bd-189">In this section, you will add MarsCuriosityRover object's child objects renderer into an individual clipping object to demonstrate the clipping of the MarsCuriosityRover model.</span></span>

<span data-ttu-id="066bd-190">Nella finestra Hierarchy (Gerarchia) espandi l'oggetto **ClippingObjects** per esporre i tre diversi oggetti di ritaglio che userai in questo progetto.</span><span class="sxs-lookup"><span data-stu-id="066bd-190">In the Hierarchy window, expand the **ClippingObjects** object to expose the three different clipping objects that you will be using in this project.</span></span>

<span data-ttu-id="066bd-191">Per configurare l'oggetto **ClippingSphere**, fai clic su di esso e nella finestra Inspector (Controllo) individua il componente **Clipping Sphere (Script)** (Sfera di ritaglio - Script).</span><span class="sxs-lookup"><span data-stu-id="066bd-191">To configure the **ClippingSphere** object, click on it, and in the Inspector window, locate the **Clipping Sphere (Script)** component.</span></span> <span data-ttu-id="066bd-192">Nel campo della dimensione immetti il numero di renderer che è necessario aggiungere per il modello 3D.</span><span class="sxs-lookup"><span data-stu-id="066bd-192">Enter the number of renderers in the size field that you need to add for your 3D model.</span></span> <span data-ttu-id="066bd-193">In questo caso, aggiungi 10 per gli oggetti figlio di MarsCuriosityRover.</span><span class="sxs-lookup"><span data-stu-id="066bd-193">In this case, add 10 for MarsCuriosityRover child objects.</span></span> <span data-ttu-id="066bd-194">Verranno creati i campi per l'aggiunta dei renderer. Trascina e rilascia gli oggetti modello figlio dell'oggetto MarsCuriosityRover in questi campi.</span><span class="sxs-lookup"><span data-stu-id="066bd-194">It will create fields for adding renderers, drag and drop MarsCuriosityRover Object's child model objects into these fields.</span></span>

![Unity con i campi del componente di script ClippingSphere configurati](images/mrlearning-pc-holographic-remoting/Tutorial1-Section5-Step1-1.png)

<span data-ttu-id="066bd-196">Segui lo stesso processo e aggiungi i renderer degli oggetti figlio di MarsCuriosityRover agli oggetti **ClippingBox** e **ClippingPlane**.</span><span class="sxs-lookup"><span data-stu-id="066bd-196">Follow the same process and add MarsCuriosityRover's child objects renderers to the **ClippingBox** and **ClippingPlane** objects.</span></span>

<span data-ttu-id="066bd-197">In questa esercitazione verrà usato solo il modello MarsCuriosityRover per illustrare la funzionalità di ritaglio.</span><span class="sxs-lookup"><span data-stu-id="066bd-197">In this tutorial, only the MarsCuriosityRover model will be used for demonstrating the clipping feature.</span></span> <span data-ttu-id="066bd-198">Sono state comunque aggiunte funzionalità di ritaglio anche ad altri modelli, aumentando la dimensione del renderer, e sono stati aggiunti i singoli renderer mesh corrispondenti.</span><span class="sxs-lookup"><span data-stu-id="066bd-198">They were adding clipping features to more models, increasing the size of the renderer, and adding their individual mesh renderers.</span></span>

## <a name="configuring-eye-tracking-to-highlight-tooltips"></a><span data-ttu-id="066bd-199">Configurazione del tracciamento oculare per evidenziare le descrizioni comandi</span><span class="sxs-lookup"><span data-stu-id="066bd-199">Configuring eye-tracking to highlight tooltips</span></span>

<span data-ttu-id="066bd-200">In questa sezione esaminerai come abilitare il tracciamento oculare nel tuo progetto.</span><span class="sxs-lookup"><span data-stu-id="066bd-200">In this section, you will explore how to enable eye tracking in your project.</span></span> <span data-ttu-id="066bd-201">Ad esempio, implementerai la funzionalità per evidenziare le descrizioni comandi associate alle parti di MarsCuriosityRover quando le guardi e per nasconderle quando distogli lo sguardo da esse.</span><span class="sxs-lookup"><span data-stu-id="066bd-201">For example, you will implement the functionality to highlight tooltips attached to MarsCuriosityRover's parts while looking at them and hiding them, while you are looking away from them.</span></span>

### <a name="1-identify-target-objects-and-associated-tooltips"></a><span data-ttu-id="066bd-202">1. Identificare gli oggetti di destinazione e le descrizioni comandi associate</span><span class="sxs-lookup"><span data-stu-id="066bd-202">1. Identify target objects and associated tooltips</span></span>

<span data-ttu-id="066bd-203">Nella finestra Hierarchy (Gerarchia) seleziona l'oggetto ModelParent.</span><span class="sxs-lookup"><span data-stu-id="066bd-203">In the Hierarchy window, select the ModelParent object.</span></span> <span data-ttu-id="066bd-204">Espandere **_MarsCuriosity -> Rover_ *_ per trovare cinque parti principali di MarsCuriosityRover: _* POI-Camera**, **POI-Wheels**, **POI-Antenna**, **POI-Spectrometer**, **POI-RUHF Antenna**.</span><span class="sxs-lookup"><span data-stu-id="066bd-204">Expand the \**_MarsCuriosity -> Rover_*_ to find five main parts of the MarsCuriosityRover: _\* POI-Camera\*\*, **POI-Wheels**, **POI-Antena**, **POI-Spectrometer**, **POI-RUHF Antenna**.</span></span>

* <span data-ttu-id="066bd-205">Osserva cinque oggetti descrizione comando corrispondenti associati a parti di MarsCuriosityRover nella finestra Hierarchy (Gerarchia).</span><span class="sxs-lookup"><span data-stu-id="066bd-205">Observe five corresponding tooltip objects associated with MarsCuriosityRover parts in the Hierarchy window.</span></span>
* <span data-ttu-id="066bd-206">Configurerai questi oggetti per evidenziare l'esperienza quando guardi le parti di MarsCuriosityRover.</span><span class="sxs-lookup"><span data-stu-id="066bd-206">You will be configuring these objects to highlight the experience when you look at the MarsCuriosityRover parts.</span></span>

![Unity con l'oggetto Rover selezionato ed espanso](images/mrlearning-pc-holographic-remoting/Tutorial1-Section6-Step1-1.png)

### <a name="2-implement-while-looking-at-target-----on-look-away--events"></a><span data-ttu-id="066bd-208">2. Implementare gli eventi Looking At Target () (Mentre viene guardata la destinazione) e On Look Away () (Quando viene distolto lo sguardo)</span><span class="sxs-lookup"><span data-stu-id="066bd-208">2. Implement While Looking At Target ()  &  On Look Away () events</span></span>

<span data-ttu-id="066bd-209">Nella finestra Hierarchy (Gerarchia) selezionare l'oggetto \***POI-Camera** _.</span><span class="sxs-lookup"><span data-stu-id="066bd-209">In the Hierarchy window, select the \***POI-Camera** _ object.</span></span> <span data-ttu-id="066bd-210">Nella finestra Inspector (Controllo) individuare il componente _ *Eye Tracking Target (Script)* \* (Destinazione tracciamento oculare - Script) e configurare gli eventi **While Looking At Target ()** (Mentre viene guardata la destinazione) & **On Look Away ()** (Quando viene distolto lo sguardo) come indicato di seguito:</span><span class="sxs-lookup"><span data-stu-id="066bd-210">In the Inspector window, locate the _ *Eye Tracking Target (Script)*\* component and configure the **While Looking At Target ()** & **On Look Away ()** events as follows:</span></span>

* <span data-ttu-id="066bd-211">Al campo **None (Object)** (Nessuno - Oggetto) assegna l'oggetto **POI-Camera ToolTip**</span><span class="sxs-lookup"><span data-stu-id="066bd-211">To **None (Object)** field, assign the **POI-Camera ToolTip** object</span></span>
* <span data-ttu-id="066bd-212">Dall'elenco a discesa **No Function** (Nessuna funzione) dell'evento **While Looking At Target ()** (Mentre viene guardata la destinazione) seleziona **GameObject** > **SetActive (bool).**</span><span class="sxs-lookup"><span data-stu-id="066bd-212">From **No Function** dropdown of **While Looking At Target ()** event, select **GameObject** > **SetActive (bool).**</span></span> <span data-ttu-id="066bd-213">Seleziona la **casella di controllo** sottostante per evidenziare la descrizione comando come l'azione che viene attivata quando guardi l'oggetto di destinazione.</span><span class="sxs-lookup"><span data-stu-id="066bd-213">Select the **Checkbox** under it to highlight the tooltip as the action that is triggered when you look at the target object.</span></span>

![Unity con la configurazione dell'evento WhileLookingAtTarget di EyeTrackingTarget in corso](images/mrlearning-pc-holographic-remoting/Tutorial1-Section6-Step2-1.png)

* <span data-ttu-id="066bd-215">Segui lo stesso processo e fai clic sull'elenco a discesa **No Function** (Nessuna funzione) del listener di eventi **On Look Away ()** (Quando viene distolto lo sguardo).</span><span class="sxs-lookup"><span data-stu-id="066bd-215">Follow the same process and click on the **No Function** dropdown of the **On Look Away ()** event listener.</span></span> <span data-ttu-id="066bd-216">Seleziona quindi **GameObject** > **SetActive (bool**) e lascia vuota la **casella di controllo** per nascondere la descrizione comando come l'azione che viene attivata quando distogli lo sguardo dall'oggetto di destinazione.</span><span class="sxs-lookup"><span data-stu-id="066bd-216">Then select **GameObject** > **SetActive (bool**) and leave the **Checkbox** empty to hide the tooltip as the action that is triggered when you look away from the target object.</span></span>

![Unity con l'evento OnLookAway di EyeTrackingTarget configurato](images/mrlearning-pc-holographic-remoting/Tutorial1-Section6-Step2-2.png)

<span data-ttu-id="066bd-218">Segui lo stesso processo e assegna i rispettivi oggetti descrizione comando agli eventi **While Looking At Target ()** (Mentre viene guardata la destinazione) & **On Look Away ()** (Quando viene distolto lo sguardo) delle parti corrispondenti di **MarsCuriosityRover**.</span><span class="sxs-lookup"><span data-stu-id="066bd-218">Follow the same process and assign respective tooltip objects to their same **MarsCuriosityRover** parts **While Looking At Target ()** & **On Look Away ()** events.</span></span>

<span data-ttu-id="066bd-219">Per abilitare il tracciamento oculare, segui queste [linee guida](/windows/mixed-reality/mrlearning-base-ch5#5-enable-simulated-eye-tracking-for-in-editor-simulations).</span><span class="sxs-lookup"><span data-stu-id="066bd-219">To enable eye tracking, please follow these [guidelines](/windows/mixed-reality/mrlearning-base-ch5#5-enable-simulated-eye-tracking-for-in-editor-simulations).</span></span>

## <a name="congratulations"></a><span data-ttu-id="066bd-220">Lezione completata</span><span class="sxs-lookup"><span data-stu-id="066bd-220">Congratulations</span></span>

<span data-ttu-id="066bd-221">In questa esercitazione hai appreso come creare un'esperienza di realtà mista con la dimostrazione del funzionamento degli elementi dell'interfaccia utente e delle funzionalità di manipolazione del modello 3D, di ritaglio del modello e di tracciamento oculare.</span><span class="sxs-lookup"><span data-stu-id="066bd-221">In this tutorial, you learned to build a mixed reality experience demonstrating UI elements, 3D model manipulation, model clipping, and eye-tracking features.</span></span> <span data-ttu-id="066bd-222">Nell'esercitazione sono stati forniti NextButton e PreviousButton che ti consentono di esplorare l'esperienza di visualizzazione del modello 3D.</span><span class="sxs-lookup"><span data-stu-id="066bd-222">The tutorial provided you with NextButton and PreviousButton that let you explore the 3D model viewer experience.</span></span> <span data-ttu-id="066bd-223">Con ClippingObjectButton hai attivato gli oggetti di ritaglio e visto come opera la funzionalità di ritaglio.</span><span class="sxs-lookup"><span data-stu-id="066bd-223">The ClippingObjectButton made you turn on clipping objects and experience clipping feature.</span></span> <span data-ttu-id="066bd-224">Nell'esercitazione è stato inoltre fornito un elemento di tracciamento oculare che consente di evidenziare le descrizioni comandi nell'esperienza.</span><span class="sxs-lookup"><span data-stu-id="066bd-224">The tutorial also provided you with an eye-tracking element to enable highlighting the tooltips in the experience.</span></span>

<span data-ttu-id="066bd-225">Nella lezione successiva apprenderai come creare un'applicazione per Holographic Remoting per PC per connettere HoloLens 2 in qualsiasi momento, offrendo un modo per visualizzare il contenuto 3D in realtà mista.</span><span class="sxs-lookup"><span data-stu-id="066bd-225">In the next lesson, you will learn how to create a Holographic Remoting application for PC to connect HoloLens 2 at any point, providing a way to Visualize 3D content in mixed reality.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="066bd-226">Lezione successiva: 2. Creare un'applicazione per Holographic Remoting</span><span class="sxs-lookup"><span data-stu-id="066bd-226">Next Lesson: 2. Create Holographic Remoting application</span></span>](mr-learning-pc-holographic-remoting-02.md)
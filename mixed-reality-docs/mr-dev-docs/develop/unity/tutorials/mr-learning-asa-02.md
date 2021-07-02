---
title: Introduzione ad Ancoraggi nello spazio di Azure
description: In questo corso viene illustrato come usare Ancoraggi nello spazio di Azure per ancorare oggetti in un'applicazione di realtà mista.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens, MRTK, mixed reality toolkit, UWP, ancoraggi nello spazio di Azure
ms.localizationpriority: high
ms.openlocfilehash: eddde9b827dcf2a2f054f48a50f38946e5d98533
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2021
ms.locfileid: "113175577"
---
# <a name="2-getting-started-with-azure-spatial-anchors"></a><span data-ttu-id="580ff-104">2. Introduzione ad Ancoraggi nello spazio di Azure</span><span class="sxs-lookup"><span data-stu-id="580ff-104">2. Getting started with Azure Spatial Anchors</span></span>

<span data-ttu-id="580ff-105">In questa esercitazione esaminerai i diversi passaggi necessari per avviare e arrestare una sessione di ancoraggi nello spazio di Azure e per creare, caricare e scaricare in un singolo dispositivo gli ancoraggi nello spazio di Azure.</span><span class="sxs-lookup"><span data-stu-id="580ff-105">In this tutorial, you will explore the various steps required to start and stop an Azure Spatial Anchors session and to create, upload, and download Azure Spatial Anchors on a single device.</span></span>

## <a name="objectives"></a><span data-ttu-id="580ff-106">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="580ff-106">Objectives</span></span>

* <span data-ttu-id="580ff-107">Scopri le nozioni fondamentali sullo sviluppo con Ancoraggi nello spazio di Azure per HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="580ff-107">Learn the fundamentals of developing with Azure Spatial Anchors for HoloLens 2</span></span>
* <span data-ttu-id="580ff-108">Apprendi come creare ancoraggi nello spazio e recuperarli da Azure</span><span class="sxs-lookup"><span data-stu-id="580ff-108">Learn how to create spatial anchors and fetch them from Azure</span></span>

## <a name="creating-and-preparing-the-unity-project"></a><span data-ttu-id="580ff-109">Creazione e preparazione del progetto Unity</span><span class="sxs-lookup"><span data-stu-id="580ff-109">Creating and preparing the Unity project</span></span>

<span data-ttu-id="580ff-110">In questa sezione creerai un nuovo progetto Unity per prepararti allo sviluppo con MRTK.</span><span class="sxs-lookup"><span data-stu-id="580ff-110">In this section, you will create a new Unity project and get it ready for MRTK development.</span></span>

<span data-ttu-id="580ff-111">Seguire prima l'esercitazione [Inizializzazione del progetto e distribuzione della prima applicazione](mr-learning-base-02.md), escluse le istruzioni della sezione [Compilare l'applicazione nel dispositivo](mr-learning-base-02.md#building-your-application-to-your-hololens-2). L'esercitazione include i passaggi seguenti:</span><span class="sxs-lookup"><span data-stu-id="580ff-111">First, follow the [Initializing your project and deploying your first application](mr-learning-base-02.md), excluding the [Build your application to your device](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions, which includes the following steps:</span></span>

1. <span data-ttu-id="580ff-112">[Creazione del progetto Unity](mr-learning-base-02.md#creating-the-unity-project) e assegnazione di un nome appropriato, ad esempio *MRTK Tutorials*</span><span class="sxs-lookup"><span data-stu-id="580ff-112">[Creating the Unity project](mr-learning-base-02.md#creating-the-unity-project) and give it a suitable name, for example, *MRTK Tutorials*</span></span>
2. [<span data-ttu-id="580ff-113">Passaggio a un'altra piattaforma di compilazione</span><span class="sxs-lookup"><span data-stu-id="580ff-113">Switching the build platform</span></span>](mr-learning-base-02.md#switching-the-build-platform)
3. [<span data-ttu-id="580ff-114">Importazione delle risorse essenziali TextMeshPro</span><span class="sxs-lookup"><span data-stu-id="580ff-114">Importing the TextMeshPro Essential Resources</span></span>](mr-learning-base-04.md#importing-the-textmeshpro-essential-resources)
4. [<span data-ttu-id="580ff-115">Importazione del progetto Toolkit realtà mista e configurazione del progetto Unity</span><span class="sxs-lookup"><span data-stu-id="580ff-115">Importing the Mixed Reality Toolkit and Configuring the Unity project</span></span>](mr-learning-base-02.md#importing-the-mixed-reality-toolkit-and-configuring-the-unity-project)
5. <span data-ttu-id="580ff-116">[Creazione e configurazione della scena](mr-learning-base-02.md#creating-the-scene-and-configuring-mrtk) e assegnazione di un nome appropriato, ad esempio *AzureSpatialAnchors*</span><span class="sxs-lookup"><span data-stu-id="580ff-116">[Creating and configuring the scene](mr-learning-base-02.md#creating-the-scene-and-configuring-mrtk) and give the scene a suitable name, for example, *AzureSpatialAnchors*</span></span>

<span data-ttu-id="580ff-117">Seguire quindi [](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) le istruzioni relative alla modifica dell'opzione di visualizzazione della consapevolezza spaziale per assicurarsi che il profilo di configurazione MRTK per la scena sia **DefaultHoloLens2ConfigurationProfile** e modificare le opzioni di visualizzazione per la mesh di riconoscimento spaziale in **Occlusion**.</span><span class="sxs-lookup"><span data-stu-id="580ff-117">Then follow the [Changing the Spatial Awareness Display Option](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) instructions to ensure the MRTK configuration profile for your scene is **DefaultHoloLens2ConfigurationProfile**  and change the display options for the spatial awareness mesh to **Occlusion**.</span></span>

## <a name="installing-inbuilt-unity-packages-and-importing-the-tutorial-assets"></a><span data-ttu-id="580ff-118">Installazione di pacchetti Unity predefiniti e importazione degli asset dell'esercitazione</span><span class="sxs-lookup"><span data-stu-id="580ff-118">Installing inbuilt Unity packages and Importing the tutorial assets</span></span>

[!INCLUDE[](includes/installing-packages-for-asa.md)]

## <a name="preparing-the-scene"></a><span data-ttu-id="580ff-119">Preparazione della scena</span><span class="sxs-lookup"><span data-stu-id="580ff-119">Preparing the scene</span></span>

<span data-ttu-id="580ff-120">In questa sezione preparerai la scena aggiungendo alcuni dei prefab dell'esercitazione.</span><span class="sxs-lookup"><span data-stu-id="580ff-120">In this section, you will prepare the scene by adding some of the tutorial prefabs.</span></span>

<span data-ttu-id="580ff-121">Nella finestra Project (Progetto) passa ad **Assets (Asset)**  > **MRTK.Tutorials.AzureSpeechServices** > **Prefabs** (Prefab) e quindi fai clic e trascina i prefab seguenti sulla finestra Hierarchy (Gerarchia) per aggiungerli alla scena:</span><span class="sxs-lookup"><span data-stu-id="580ff-121">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.AzureSpatialAnchors** > **Prefabs** folder, then click-and-drag the following prefabs into the Hierarchy window to add them to your scene:</span></span>

* <span data-ttu-id="580ff-122">Prefab **ButtonParent**</span><span class="sxs-lookup"><span data-stu-id="580ff-122">**ButtonParent** prefabs</span></span>
* <span data-ttu-id="580ff-123">Prefab **DebugWindow**</span><span class="sxs-lookup"><span data-stu-id="580ff-123">**DebugWindow** prefabs</span></span>
* <span data-ttu-id="580ff-124">Prefab **Instructions**</span><span class="sxs-lookup"><span data-stu-id="580ff-124">**Instructions** prefabs</span></span>
* <span data-ttu-id="580ff-125">Prefab **ParentAnchor**</span><span class="sxs-lookup"><span data-stu-id="580ff-125">**ParentAnchor** prefabs</span></span>

![Unity con i prefab appena aggiunti selezionati](images/mr-learning-asa/asa-02-section4-step1-1.png)

> [!TIP]
> <span data-ttu-id="580ff-127">Se trovi che le icone grandi nella scena, come quelle a forma di "T", siano motivo di distrazione, puoi nasconderle <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">disattivando il menu Gizmos</a>, come mostrato nell'immagine precedente.</span><span class="sxs-lookup"><span data-stu-id="580ff-127">If you find the large icons in your scene, for example, the large framed 'T' icons distracting, you can hide these by <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">toggling the Gizmos</a> to the off position, as shown in the image above.</span></span>

<span data-ttu-id="580ff-128">Selezionare **l'oggetto MixedRealityToolkit** nella finestra Hierarchy (Gerarchia) e usare il pulsante **Add Component** (Aggiungi componente) nella finestra Inspector (Controllo) per aggiungere i componenti seguenti:</span><span class="sxs-lookup"><span data-stu-id="580ff-128">Select **MixedRealityToolkit** object in the Hierarchy window, use the **Add Component** button in the Inspector window to add the following components:</span></span>

* <span data-ttu-id="580ff-129">AR Anchor Manager (Script)</span><span class="sxs-lookup"><span data-stu-id="580ff-129">AR Anchor Manager (Script)</span></span>
* <span data-ttu-id="580ff-130">DisableDiagnosticsSystem (Script)</span><span class="sxs-lookup"><span data-stu-id="580ff-130">DisableDiagnosticsSystem (Script)</span></span>

![<span data-ttu-id="580ff-131">Oggetto MixedRealityToolkit di Unity con i componenti AR Anchor Manager e DisableDiagnosticsSystem aggiunti</span><span class="sxs-lookup"><span data-stu-id="580ff-131">Unity MixedRealityToolkit object with AR Anchor Manager and DisableDiagnosticsSystem components added</span></span> ](images/mr-learning-asa/asa-02-section4-step1-2.PNG)

> [!WARNING]
> <span data-ttu-id="580ff-132">Si è verificato un problema noto con ASA v2.9.0 e v2.10.0-preview.1 che richiede che nella scena siano inseriti due oggetti aggiuntivi.</span><span class="sxs-lookup"><span data-stu-id="580ff-132">There is a known issue with ASA v2.9.0 and v2.10.0-preview.1 that requires two additional objects to be placed in the scene.</span></span> <span data-ttu-id="580ff-133">Usare il pulsante **Aggiungi** componente nella finestra del controllo per aggiungere un ar Camera Manager (Script) e una sessione AR (Script) all'oggetto **MixedRealityToolkit.**</span><span class="sxs-lookup"><span data-stu-id="580ff-133">Please use the **Add Component** button in the inspector window to add an AR Camera Manager (Script) and an AR Session (Script) to the **MixedRealityToolkit** object.</span></span> <span data-ttu-id="580ff-134">Assicurarsi di disabilitare la fotocamera creata automaticamente durante l'aggiunta di AR Camera Manager (Script) deselezionando la casella di controllo accanto all'oggetto Camera nella finestra del controllo.</span><span class="sxs-lookup"><span data-stu-id="580ff-134">Be sure to disable the Camera that is created automatically while adding the AR Camera Manager (Script) by unchecking the checkbox next to the Camera object in the inspector window.</span></span> <span data-ttu-id="580ff-135">Questo problema verrà risolto nella versione completa di ASA v2.10.0.</span><span class="sxs-lookup"><span data-stu-id="580ff-135">This issue will be addressed in the full release of ASA v2.10.0.</span></span>
> 

> [!NOTE]
> <span data-ttu-id="580ff-136">Quando si aggiunge il componente AR Anchor Manager (Script), il componente AR Session Origin (Script) viene aggiunto automaticamente perché è richiesto dal componente AR Anchor Manager (Script).</span><span class="sxs-lookup"><span data-stu-id="580ff-136">When you add the AR Anchor Manager (Script) component, the AR Session Origin (Script) component is automatically added because it is required by the AR Anchor Manager (Script) component.</span></span>

## <a name="configuring-the-buttons-to-operate-the-scene"></a><span data-ttu-id="580ff-137">Configurazione dei pulsanti per il funzionamento della scena</span><span class="sxs-lookup"><span data-stu-id="580ff-137">Configuring the buttons to operate the scene</span></span>

<span data-ttu-id="580ff-138">In questa sezione aggiungerai script alla scena per creare una serie di eventi Button che illustrano le nozioni fondamentali sul comportamento degli ancoraggi locali e degli ancoraggi nello spazio di Azure in un'app.</span><span class="sxs-lookup"><span data-stu-id="580ff-138">In this section, you will add scripts to the scene to create a series of button events that demonstrate the fundamentals of how both local anchors and Azure Spatial Anchors behave in an app.</span></span>

<span data-ttu-id="580ff-139">Nella finestra Hierarchy (Gerarchia) espandi l'oggetto **ButtonParent** e seleziona il primo oggetto figlio denominato **StartAzureSession**. Nella finestra Inspector (Controllo) configura l'evento **On Click ()** (Al clic) del componente **Button Config Helper (Script)** (Helper configurazione pulsanti - script) come indicato di seguito:</span><span class="sxs-lookup"><span data-stu-id="580ff-139">In the Hierarchy window, expand the **ButtonParent** object and select the first child object named **StartAzureSession**, in the Inspector window, configure the **Button Config Helper (Script)** component's **On Click ()** event as follows:</span></span>

* <span data-ttu-id="580ff-140">Assegna l'oggetto **ParentAnchor** al campo **None (Object)** (Nessuno - Oggetto)</span><span class="sxs-lookup"><span data-stu-id="580ff-140">Assign the **ParentAnchor** object to the **None (Object)** field</span></span>
* <span data-ttu-id="580ff-141">Dall'elenco a discesa **No Function** (Nessuna funzione) seleziona **AnchorModuleScript** > **StartAzureSession ()** per impostare questa funzione come l'azione da eseguire quando viene attivato l'evento</span><span class="sxs-lookup"><span data-stu-id="580ff-141">From the **No Function** dropdown, select **AnchorModuleScript** > **StartAzureSession ()** to set this function as the action to be executed when the event is triggered</span></span>

![Unity con l'evento OnClick del pulsante StartAzureSession configurato](images/mr-learning-asa/asa-02-section5-step1-1.png)

<span data-ttu-id="580ff-143">Nella finestra Hierarchy (Gerarchia) seleziona il pulsante successivo denominato **StopAzureSession** e quindi nella finestra Inspector (Controllo) configura l'evento **On Click ()** (Al clic) del componente **Button Config Helper (Script)** (Helper configurazione pulsanti - script) come indicato di seguito:</span><span class="sxs-lookup"><span data-stu-id="580ff-143">In the Hierarchy window, select the next button named **StopAzureSession**, then in the Inspector window, configure the **Button Config Helper (Script)** component's **On Click ()** event as follows:</span></span>

* <span data-ttu-id="580ff-144">Assegna l'oggetto **ParentAnchor** al campo **None (Object)** (Nessuno - Oggetto)</span><span class="sxs-lookup"><span data-stu-id="580ff-144">Assign the **ParentAnchor** object to the **None (Object)** field</span></span>
* <span data-ttu-id="580ff-145">Dall'elenco a discesa **No Function** (Nessuna funzione) seleziona **AnchorModuleScript** > **StopAzureSession ()** per impostare questa funzione come l'azione da eseguire quando viene attivato l'evento</span><span class="sxs-lookup"><span data-stu-id="580ff-145">From the **No Function** dropdown, select **AnchorModuleScript** > **StopAzureSession ()** to set this function as the action to be executed when the event is triggered</span></span>

![Unity con l'evento OnClick del pulsante StopAzureSession configurato](images/mr-learning-asa/asa-02-section5-step1-2.png)

<span data-ttu-id="580ff-147">Nella finestra Hierarchy (Gerarchia) seleziona il pulsante successivo denominato **CreateAzureAnchor** e quindi nella finestra Inspector (Controllo) configura l'evento **On Click ()** (Al clic) del componente **Button Config Helper (Script)** (Helper configurazione pulsanti - script) come indicato di seguito:</span><span class="sxs-lookup"><span data-stu-id="580ff-147">In the Hierarchy window, select the next button named **CreateAzureAnchor**, then in the Inspector window, configure the **Button Config Helper (Script)** component's **On Click ()** event as follows:</span></span>

* <span data-ttu-id="580ff-148">Assegna l'oggetto **ParentAnchor** al campo **None (Object)** (Nessuno - Oggetto)</span><span class="sxs-lookup"><span data-stu-id="580ff-148">Assign the **ParentAnchor** object to the **None (Object)** field</span></span>
* <span data-ttu-id="580ff-149">Dall'elenco a discesa **No Function** (Nessuna funzione) seleziona **AnchorModuleScript** > **CreateAzureAnchor ()** per impostare questa funzione come l'azione da eseguire quando viene attivato l'evento</span><span class="sxs-lookup"><span data-stu-id="580ff-149">From the **No Function** dropdown, select **AnchorModuleScript** > **CreateAzureAnchor ()** to set this function as the action to be executed when the event is triggered</span></span>
* <span data-ttu-id="580ff-150">Assegna l'oggetto **ParentAnchor** al campo **None (Game Object)** (Nessuno - Oggetto gioco) vuoto per impostarlo come argomento della funzione CreateAzureAnchor ()</span><span class="sxs-lookup"><span data-stu-id="580ff-150">Assign the **ParentAnchor** object to the empty **None (Game Object)** field to make it the argument for the CreateAzureAnchor () function</span></span>

![Unity con l'evento OnClick del pulsante CreateAzureAnchor configurato](images/mr-learning-asa/asa-02-section5-step1-3.png)

<span data-ttu-id="580ff-152">Nella finestra Hierarchy (Gerarchia) seleziona il pulsante successivo denominato **RemoveLocalAnchor** e quindi nella finestra Inspector (Controllo) configura l'evento **On Click ()** (Al clic) del componente **Button Config Helper (Script)** (Helper configurazione pulsanti - script) come indicato di seguito:</span><span class="sxs-lookup"><span data-stu-id="580ff-152">In the Hierarchy window, select the next button named **RemoveLocalAnchor**,then in the Inspector window, configure the **Button Config Helper (Script)** component's **On Click ()** event as follows:</span></span>

* <span data-ttu-id="580ff-153">Assegna l'oggetto **ParentAnchor** al campo **None (Object)** (Nessuno - Oggetto)</span><span class="sxs-lookup"><span data-stu-id="580ff-153">Assign the **ParentAnchor** object to the **None (Object)** field</span></span>
* <span data-ttu-id="580ff-154">Dall'elenco a discesa **No Function** (Nessuna funzione) seleziona **AnchorModuleScript** > **RemoveLocalAnchor ()** per impostare questa funzione come l'azione da eseguire quando viene attivato l'evento</span><span class="sxs-lookup"><span data-stu-id="580ff-154">From the **No Function** dropdown, select **AnchorModuleScript** > **RemoveLocalAnchor ()** to set this function as the action to be executed when the event is triggered</span></span>
* <span data-ttu-id="580ff-155">Assegna l'oggetto **ParentAnchor** al campo vuoto **None (Game Object)** (Nessuno - Oggetto gioco) per impostarlo come argomento della funzione RemoveLocalAnchor ()</span><span class="sxs-lookup"><span data-stu-id="580ff-155">Assign the **ParentAnchor** object to the empty **None (Game Object)** field to make it the argument for the RemoveLocalAnchor () function</span></span>

![Unity con l'evento OnClick del pulsante RemoveLocalAnchor configurato](images/mr-learning-asa/asa-02-section5-step1-4.png)

<span data-ttu-id="580ff-157">Nella finestra Hierarchy (Gerarchia) seleziona il pulsante successivo denominato **FindAzureAnchor** e quindi nella finestra Inspector (Controllo) configura l'evento **On Click ()** (Al clic) del componente **Button Config Helper (Script)** (Helper configurazione pulsanti - script) come indicato di seguito:</span><span class="sxs-lookup"><span data-stu-id="580ff-157">In the Hierarchy window, select the next button named **FindAzureAnchor**,then in the Inspector window, configure the **Button Config Helper (Script)** component's **On Click ()** event as follows:</span></span>

* <span data-ttu-id="580ff-158">Assegna l'oggetto **ParentAnchor** al campo **None (Object)** (Nessuno - Oggetto)</span><span class="sxs-lookup"><span data-stu-id="580ff-158">Assign the **ParentAnchor** object to the **None (Object)** field</span></span>
* <span data-ttu-id="580ff-159">Dall'elenco a discesa **No Function** (Nessuna funzione) seleziona **AnchorModuleScript** > **FindAzureAnchor ()** per impostare questa funzione come l'azione da eseguire quando viene attivato l'evento</span><span class="sxs-lookup"><span data-stu-id="580ff-159">From the **No Function** dropdown, select **AnchorModuleScript** > **FindAzureAnchor ()** to set this function as the action to be executed when the event is triggered</span></span>

![Unity con l'evento OnClick del pulsante FindAzureAnchor configurato](images/mr-learning-asa/asa-02-section5-step1-5.png)

<span data-ttu-id="580ff-161">Nella finestra Hierarchy (Gerarchia) seleziona il pulsante successivo denominato **DeleteAzureAnchor** e quindi nella finestra Inspector (Controllo) configura l'evento **On Click ()** (Al clic) del componente **Button Config Helper (Script)** (Helper configurazione pulsanti - script) come indicato di seguito:</span><span class="sxs-lookup"><span data-stu-id="580ff-161">In the Hierarchy window, select the next button named **DeleteAzureAnchor**, then in the Inspector window, configure the **Button Config Helper (Script)** component's **On Click ()** event as follows:</span></span>

* <span data-ttu-id="580ff-162">Assegna l'oggetto **ParentAnchor** al campo **None (Object)** (Nessuno - Oggetto)</span><span class="sxs-lookup"><span data-stu-id="580ff-162">Assign the **ParentAnchor** object to the **None (Object)** field</span></span>
* <span data-ttu-id="580ff-163">Dall'elenco a discesa **No Function** (Nessuna funzione) seleziona **AnchorModuleScript** > **DeleteAzureAnchor ()** per impostare questa funzione come l'azione da eseguire quando viene attivato l'evento</span><span class="sxs-lookup"><span data-stu-id="580ff-163">From the **No Function** dropdown, select **AnchorModuleScript** > **DeleteAzureAnchor ()** to set this function as the action to be executed when the event is triggered</span></span>

![Unity con l'evento OnClick del pulsante DeleteAzureAnchor configurato](images/mr-learning-asa/asa-02-section5-step1-6.png)

## <a name="connecting-the-scene-to-the-azure-resource"></a><span data-ttu-id="580ff-165">Connessione della scena alla risorsa di Azure</span><span class="sxs-lookup"><span data-stu-id="580ff-165">Connecting the scene to the Azure resource</span></span>

<span data-ttu-id="580ff-166">Nella finestra Hierarchy (Gerarchia) seleziona l'oggetto **ParentAnchor** e quindi nella finestra Inspector (Controllo) individua il componente **Spatial Anchor Manager (Script)** (Gestione ancoraggi nello spazio - script).</span><span class="sxs-lookup"><span data-stu-id="580ff-166">In the Hierarchy window, select the **ParentAnchor** object, then in the Inspector window, locate the **Spatial Anchor Manager (Script)** component.</span></span> <span data-ttu-id="580ff-167">Configura la sezione **Credentials** (Credenziali) con le credenziali dell'account di ancoraggi nello spazio di Azure creato in fase di definizione dei [Prerequisiti](mr-learning-asa-01.md#prerequisites) per questa serie di esercitazioni:</span><span class="sxs-lookup"><span data-stu-id="580ff-167">Configure the **Credentials** section with the credentials from the Azure Spatial Anchors account created as part of the [Prerequisites](mr-learning-asa-01.md#prerequisites) for this tutorial series:</span></span>

* <span data-ttu-id="580ff-168">Nel campo **Spatial Anchors Account ID** (ID account Ancoraggi nello spazio) incolla il valore di **Account ID** (ID account) del tuo account di Ancoraggi nello spazio di Azure</span><span class="sxs-lookup"><span data-stu-id="580ff-168">In the **Spatial Anchors Account ID** field, paste the **Account ID** from your Azure Spatial Anchors account</span></span>
* <span data-ttu-id="580ff-169">Nel campo **Spatial Anchors Account Key** (Chiave account Ancoraggi nello spazio) incolla il valore di **Access Key** (Chiave di accesso) primario o secondario del tuo account di Ancoraggi nello spazio di Azure</span><span class="sxs-lookup"><span data-stu-id="580ff-169">In the **Spatial Anchors Account Key** field, paste the primary or secondary **Access Key** from your Azure Spatial Anchors account</span></span>
* <span data-ttu-id="580ff-170">Nel campo **Dominio account ancoraggi** nello stato spaziale incollare il dominio **dell'account** dall'account Ancoraggi nello stato di Azure</span><span class="sxs-lookup"><span data-stu-id="580ff-170">In the **Spatial Anchors Account Domain** field, paste the **Account Domain** from your Azure Spatial Anchors account</span></span>

![Unity con Spatial Anchor Manager configurato](images/mr-learning-asa/asa-02-section6-step1-1.png)

## <a name="trying-the-basic-behaviors-of-azure-spatial-anchors"></a><span data-ttu-id="580ff-172">Test dei comportamenti di base di Ancoraggi nello spazio di Azure</span><span class="sxs-lookup"><span data-stu-id="580ff-172">Trying the basic behaviors of Azure Spatial Anchors</span></span>

<span data-ttu-id="580ff-173">Poiché non è possibile eseguire ancoraggi nello spazio di Azure in Unity, per testare la funzionalità di questo servizio devi compilare il progetto e distribuire l'app nel tuo dispositivo.</span><span class="sxs-lookup"><span data-stu-id="580ff-173">Azure Spatial Anchors can not run in Unity, so to test the Azure Spatial Anchors functionality, you need to build the project and deploy the app to your device.</span></span>

> [!TIP]
> <span data-ttu-id="580ff-174">Per rivedere la procedura di compilazione e distribuzione di un progetto Unity in HoloLens 2, puoi fare riferimento alle istruzioni riportate in [Compilazione dell'applicazione nel dispositivo HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2).</span><span class="sxs-lookup"><span data-stu-id="580ff-174">For a reminder on how to build and deploy your Unity project to HoloLens 2, you can refer to the [Building your application to your HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions.</span></span>

<span data-ttu-id="580ff-175">Quando l'app è in esecuzione nel dispositivo, segui le istruzioni visualizzate nel pannello Azure Spatial Anchor Tutorial Instructions (Istruzioni per l'esercitazione su ancoraggi nello spazio di Azure):</span><span class="sxs-lookup"><span data-stu-id="580ff-175">When the app runs on your device, follow the on-screen instructions displayed on the Azure Spatial Anchor Tutorial Instructions panel:</span></span>

1. <span data-ttu-id="580ff-176">Sposta il cubo in un'altra posizione</span><span class="sxs-lookup"><span data-stu-id="580ff-176">Move the cube to a different location</span></span>
2. <span data-ttu-id="580ff-177">Avvia la sessione di Azure</span><span class="sxs-lookup"><span data-stu-id="580ff-177">Start Azure Session</span></span>
3. <span data-ttu-id="580ff-178">Crea l'ancoraggio di Azure (viene creato un ancoraggio nella posizione del cubo)</span><span class="sxs-lookup"><span data-stu-id="580ff-178">Create Azure Anchor (creates an anchor at the location of the cube).</span></span>
4. <span data-ttu-id="580ff-179">Arresta la sessione di Azure</span><span class="sxs-lookup"><span data-stu-id="580ff-179">Stop Azure Session</span></span>
5. <span data-ttu-id="580ff-180">Rimuovi l'ancoraggio locale (consente all'utente di spostare il cubo)</span><span class="sxs-lookup"><span data-stu-id="580ff-180">Remove Local Anchor (allows the user to move the cube)</span></span>
6. <span data-ttu-id="580ff-181">Sposta il cubo altrove</span><span class="sxs-lookup"><span data-stu-id="580ff-181">Move the cube somewhere else</span></span>
7. <span data-ttu-id="580ff-182">Avvia la sessione di Azure</span><span class="sxs-lookup"><span data-stu-id="580ff-182">Start Azure Session</span></span>
8. <span data-ttu-id="580ff-183">Trova l'ancoraggio di Azure (il cubo viene collocato nella posizione del passaggio 3)</span><span class="sxs-lookup"><span data-stu-id="580ff-183">Find Azure Anchor (positions the cube at the location from step 3)</span></span>
9. <span data-ttu-id="580ff-184">Elimina l'ancoraggio di Azure</span><span class="sxs-lookup"><span data-stu-id="580ff-184">Delete Azure Anchor</span></span>
10. <span data-ttu-id="580ff-185">Arresta la sessione di Azure</span><span class="sxs-lookup"><span data-stu-id="580ff-185">Stop Azure session</span></span>

![Unity con l'oggetto Instructions selezionato](images/mr-learning-asa/asa-02-section7-step1-1.png)

> [!CAUTION]
> <span data-ttu-id="580ff-187">Poiché per gli ancoraggi nello spazio di Azure viene usato Internet per salvare e caricare i dati di ancoraggio, assicurati che il dispositivo sia connesso a Internet.</span><span class="sxs-lookup"><span data-stu-id="580ff-187">Azure Spatial Anchors uses the internet to save and load the anchor data, so make sure your device is connected to the internet.</span></span>

## <a name="anchoring-an-experience"></a><span data-ttu-id="580ff-188">Ancoraggio di un'esperienza</span><span class="sxs-lookup"><span data-stu-id="580ff-188">Anchoring an experience</span></span>

<span data-ttu-id="580ff-189">Nelle sezioni precedenti hai appreso le nozioni fondamentali di Ancoraggi nello spazio di Azure.</span><span class="sxs-lookup"><span data-stu-id="580ff-189">In the previous sections, you learned the fundamentals of Azure Spatial Anchors.</span></span> <span data-ttu-id="580ff-190">È stato usato un cubo per rappresentare e visualizzare l'oggetto gioco padre con l'ancoraggio collegato.</span><span class="sxs-lookup"><span data-stu-id="580ff-190">We used a cube to represent and visualize the parent game object with the attached anchor.</span></span> <span data-ttu-id="580ff-191">In questa sezione apprenderai come ancorare un'intera esperienza inserendola come figlio dell'oggetto ParentAnchor.</span><span class="sxs-lookup"><span data-stu-id="580ff-191">In this section, you will learn how to anchor an entire experience by placing it as a child of the ParentAnchor object.</span></span>

<span data-ttu-id="580ff-192">Nella finestra Hierarchy (Gerarchia) seleziona l'oggetto **ParentAnchor** e quindi nella finestra Inspector (Controllo) configura i componenti **Transform** (Trasformazione) come segue:</span><span class="sxs-lookup"><span data-stu-id="580ff-192">In the Hierarchy window, select the **ParentAnchor** object, then in the Inspector window, configure the **Transform** components as follows:</span></span>

* <span data-ttu-id="580ff-193">Imposta **Scale X** (Scala X) su 1,1</span><span class="sxs-lookup"><span data-stu-id="580ff-193">Change **Scale X** to 1.1</span></span>
* <span data-ttu-id="580ff-194">Imposta **Scale Z** (Scala Z) su 1,1</span><span class="sxs-lookup"><span data-stu-id="580ff-194">Change **Scale Z** to 1.1</span></span>

![Unity con l'oggetto ParentAnchor selezionato, posizionato e ridimensionato](images/mr-learning-asa/asa-02-section8-step1-1.png)

<span data-ttu-id="580ff-196">Nella finestra Project (Progetto) passa alla cartella **Assets (Asset)**  > **MRTK.Tutorials.GettingStarted** > **Prefabs (Prefab)**  > **Rover** e quindi fai clic e trascina il prefab **RoverExplorer_Complete** sulla finestra Hierarchy (Gerarchia) per aggiungerlo alla scena:</span><span class="sxs-lookup"><span data-stu-id="580ff-196">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** > **Rover** folder, then click-and-drag the **RoverExplorer_Complete** prefab into the Hierarchy window to add it to the scene:</span></span>

![Unity con il prefab RoverExplorer_Complete appena aggiunto selezionato](images/mr-learning-asa/asa-02-section8-step1-2.png)

<span data-ttu-id="580ff-198">Con l'oggetto RoverModule_Complete appena aggiunto ancora selezionato nella finestra Hierarchy (Gerarchia), trascinalo sull'oggetto **ParentAnchor** per configurarlo come figlio dell'oggetto ParentAnchor:</span><span class="sxs-lookup"><span data-stu-id="580ff-198">With the newly added RoverModule_Complete object still selected in the Hierarchy window, drag it onto the **ParentAnchor** object to make it a child of the ParentAnchor object:</span></span>

![Unity con l'oggetto RoverExplorer_Complete impostato come elemento figlio di ParentAnchor](images/mr-learning-asa/asa-02-section8-step1-3.png)

<span data-ttu-id="580ff-200">Se ora ricompili il progetto e distribuisci l'app nel dispositivo, puoi riposizionare l'intera esperienza Rover Explorer (Esplora rover) spostando il cubo ridimensionato.</span><span class="sxs-lookup"><span data-stu-id="580ff-200">If you now rebuild the project and deploy the app to your device, you can now reposition the entire Rover Explorer experience by moving the resized cube.</span></span>

> [!TIP]
> <span data-ttu-id="580ff-201">Un'ampia gamma di flussi di esperienza utente per il riposizionamento delle esperienze, tra cui l'uso di un oggetto di riposizionamento (ad esempio il cubo usato in questa esercitazione), l'uso di un pulsante per attivare o disattivare un controllo dei limiti che circonda l'esperienza, l'uso di gizmo di posizione e rotazione e altro ancora.</span><span class="sxs-lookup"><span data-stu-id="580ff-201">A variety of user experience flows for repositioning experiences, including the use of a repositioning object (such as the cube used in this tutorial), the use of a button to toggle a bounds control that surrounds the experience, the use of position and rotation gizmos, and more.</span></span>

## <a name="congratulations"></a><span data-ttu-id="580ff-202">Lezione completata</span><span class="sxs-lookup"><span data-stu-id="580ff-202">Congratulations</span></span>

<span data-ttu-id="580ff-203">In questa esercitazione hai appreso le nozioni fondamentali di Ancoraggi nello spazio di Azure.</span><span class="sxs-lookup"><span data-stu-id="580ff-203">In this tutorial, you learned the fundamentals of Azure Spatial Anchors.</span></span> <span data-ttu-id="580ff-204">In questa esercitazione hai usato diversi pulsanti per esaminare i vari passaggi da seguire per avviare e arrestare una sessione di ancoraggi nello spazio di Azure</span><span class="sxs-lookup"><span data-stu-id="580ff-204">This tutorial provided you with several buttons to let you explore the various steps required to start and stop an Azure Spatial Anchors session.</span></span> <span data-ttu-id="580ff-205">e per creare, caricare e scaricare gli ancoraggi nello spazio di Azure in un singolo dispositivo.</span><span class="sxs-lookup"><span data-stu-id="580ff-205">Also, to create, upload, and download Azure Spatial Anchors on a single device.</span></span>

<span data-ttu-id="580ff-206">Nell'esercitazione successiva apprenderai come salvare gli ID di ancoraggio di Azure in HoloLens 2 per il recupero, anche dopo il riavvio dell'app, e come trasferire gli ID di ancoraggio tra più dispositivi per ottenere l'allineamento nello spazio.</span><span class="sxs-lookup"><span data-stu-id="580ff-206">In the next tutorial, you will learn how to save Azure anchor IDs to your HoloLens 2 for retrieval, even after the app is restarted, and how to transfer anchor IDs between multiple devices to achieve spatial alignment.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="580ff-207">Esercitazione successiva: 3. Salvataggio, recupero e condivisione di Ancoraggi nello spazio di Azure</span><span class="sxs-lookup"><span data-stu-id="580ff-207">Next Tutorial: 3. Saving, retrieving and sharing Azure Spatial Anchors</span></span>](mr-learning-asa-03.md)

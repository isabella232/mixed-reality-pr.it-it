---
title: Configurazione di Photon Unity Networking
description: In questo corso viene illustrato come implementare Photon Unity Network in un'applicazione di realtà mista per HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens, funzionalità multiutente, Photon, MRTK, mixed reality toolkit, UWP, ancoraggi nello spazio di Azure, PUN
ms.localizationpriority: high
ms.openlocfilehash: 372cb7c9516a994cb7c3da1efb6cade792e862d1
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2021
ms.locfileid: "99590313"
---
# <a name="2-setting-up-photon-unity-networking"></a><span data-ttu-id="a4080-104">2. Configurazione di Photon Unity Networking</span><span class="sxs-lookup"><span data-stu-id="a4080-104">2. Setting up Photon Unity Networking</span></span>

<span data-ttu-id="a4080-105">In questa esercitazione si preparerà l'ambiente per la creazione di un'esperienza condivisa tramite Photon Unity Networking (PUN).</span><span class="sxs-lookup"><span data-stu-id="a4080-105">In this tutorial, you will prepare for creating a shared experience using Photon Unity Networking (PUN).</span></span> <span data-ttu-id="a4080-106">Si apprenderà come creare un'app PUN, importare asset di PUN nel progetto Unity e connettere il progetto Unity all'app PUN.</span><span class="sxs-lookup"><span data-stu-id="a4080-106">You will learn how to create a PUN app, import PUN assets into your Unity project, and connect your Unity project to the PUN app.</span></span>

## <a name="objectives"></a><span data-ttu-id="a4080-107">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="a4080-107">Objectives</span></span>

* <span data-ttu-id="a4080-108">Imparare a creare un'app PUN</span><span class="sxs-lookup"><span data-stu-id="a4080-108">Learn how to create a PUN app</span></span>
* <span data-ttu-id="a4080-109">Imparare a trovare e importare gli asset di PUN</span><span class="sxs-lookup"><span data-stu-id="a4080-109">Learn how to find and import the PUN assets</span></span>
* <span data-ttu-id="a4080-110">Imparare a connettere il progetto Unity all'app PUN</span><span class="sxs-lookup"><span data-stu-id="a4080-110">Learn how to connect your Unity project to the PUN app</span></span>

## <a name="creating-and-preparing-the-unity-project"></a><span data-ttu-id="a4080-111">Creazione e preparazione del progetto Unity</span><span class="sxs-lookup"><span data-stu-id="a4080-111">Creating and preparing the Unity project</span></span>

<span data-ttu-id="a4080-112">In questa sezione creerai un nuovo progetto Unity per prepararti allo sviluppo con MRTK.</span><span class="sxs-lookup"><span data-stu-id="a4080-112">In this section, you will create a new Unity project and get it ready for MRTK development.</span></span>

<span data-ttu-id="a4080-113">Seguire prima l'esercitazione [Inizializzazione del progetto e distribuzione della prima applicazione](mr-learning-base-02.md), escluse le istruzioni della sezione [Compilare l'applicazione nel dispositivo](mr-learning-base-02.md#building-your-application-to-your-hololens-2). L'esercitazione include i passaggi seguenti:</span><span class="sxs-lookup"><span data-stu-id="a4080-113">First, follow the [Initializing your project and deploying your first application](mr-learning-base-02.md), excluding the [Build your application to your device](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions, which includes the following steps:</span></span>

1. <span data-ttu-id="a4080-114">[Creazione del progetto Unity](mr-learning-base-02.md#creating-the-unity-project) e assegnazione di un nome appropriato, ad esempio *MRTK Tutorials*</span><span class="sxs-lookup"><span data-stu-id="a4080-114">[Creating the Unity project](mr-learning-base-02.md#creating-the-unity-project) and give it a suitable name, for example, *MRTK Tutorials*</span></span>
2. [<span data-ttu-id="a4080-115">Passaggio a un'altra piattaforma di compilazione</span><span class="sxs-lookup"><span data-stu-id="a4080-115">Switching the build platform</span></span>](mr-learning-base-02.md#switching-the-build-platform)
3. [<span data-ttu-id="a4080-116">Importazione delle risorse essenziali TextMeshPro</span><span class="sxs-lookup"><span data-stu-id="a4080-116">Importing the TextMeshPro Essential Resources</span></span>](mr-learning-base-02.md#importing-the-textmeshpro-essential-resources)
4. [<span data-ttu-id="a4080-117">Importazione di Mixed Reality Toolkit</span><span class="sxs-lookup"><span data-stu-id="a4080-117">Importing the Mixed Reality Toolkit</span></span>](mr-learning-base-02.md#importing-the-mixed-reality-toolkit)
5. [<span data-ttu-id="a4080-118">Configurazione del progetto Unity</span><span class="sxs-lookup"><span data-stu-id="a4080-118">Configuring the Unity project</span></span>](mr-learning-base-02.md#configuring-the-unity-project)
6. <span data-ttu-id="a4080-119">[Creazione e configurazione della scena](mr-learning-base-02.md#creating-and-configuring-the-scene) e assegnazione di un nome appropriato, ad esempio *MultiUserCapabilities*</span><span class="sxs-lookup"><span data-stu-id="a4080-119">[Creating and configuring the scene](mr-learning-base-02.md#creating-and-configuring-the-scene) and give the scene a suitable name, for example, *MultiUserCapabilities*</span></span>

<span data-ttu-id="a4080-120">Seguire quindi le istruzioni riportate in [Modifica delle opzioni di visualizzazione di consapevolezza spaziale](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) per:</span><span class="sxs-lookup"><span data-stu-id="a4080-120">Then follow the [Changing the Spatial Awareness Display Option](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) instructions to:</span></span>

1. <span data-ttu-id="a4080-121">Impostare **MRTK configuration profile** (Profilo di configurazione di MRTK) su **DefaultHoloLens2ConfigurationProfile**</span><span class="sxs-lookup"><span data-stu-id="a4080-121">Change the **MRTK configuration profile** for to the **DefaultHoloLens2ConfigurationProfile**</span></span>
1. <span data-ttu-id="a4080-122">Impostare le **opzioni di visualizzazione mesh di consapevolezza spaziale** su **Occlusion** (Occlusione).</span><span class="sxs-lookup"><span data-stu-id="a4080-122">Change the **spatial awareness mesh display options** to **Occlusion**.</span></span>

## <a name="enabling-additional-capabilities"></a><span data-ttu-id="a4080-123">Abilitazione delle funzionalità aggiuntive</span><span class="sxs-lookup"><span data-stu-id="a4080-123">Enabling additional capabilities</span></span>

<span data-ttu-id="a4080-124">Dal menu Unity scegli **Edit** > **Project Settings...** (Modifica > Impostazioni del progetto) per aprire la finestra Project Settings (Impostazioni del progetto) e quindi individua la sezione **Player** >  **Publishing Settings** (Lettore > Impostazioni di pubblicazione):</span><span class="sxs-lookup"><span data-stu-id="a4080-124">In the Unity menu, select **Edit** > **Project Settings...** to open the Player Settings window, then locate the **Player** >  **Publishing Settings** section:</span></span>

![Impostazioni del lettore di Unity](images/mr-learning-sharing/sharing-02-section2-step1-1.png)

<span data-ttu-id="a4080-126">In **Publishing Settings** (Impostazioni di pubblicazione) scorrere verso il basso fino alla sezione **Capabilities** (Funzionalità) e verificare che siano abilitate le funzionalità **InternetClient**, **Microphone**, **SpatialPerception**, e **GazeInput**, abilitate al passaggio [Configurazione del progetto Unity](mr-learning-base-02.md#configuring-the-unity-project) precedente.</span><span class="sxs-lookup"><span data-stu-id="a4080-126">In the  **Publishing Settings**, scroll down to the **Capabilities** section and double-check that the **InternetClient**, **Microphone**, **SpatialPerception**, and **GazeInput** capabilities, which you enabled during the [Configuring the Unity project](mr-learning-base-02.md#configuring-the-unity-project) step above, are enabled.</span></span>

<span data-ttu-id="a4080-127">Abilitare quindi le funzionalità aggiuntive seguenti:</span><span class="sxs-lookup"><span data-stu-id="a4080-127">Then enable the following additional capabilities:</span></span>

* <span data-ttu-id="a4080-128">Funzionalità **InternetClientServer**</span><span class="sxs-lookup"><span data-stu-id="a4080-128">**InternetClientServer** capability</span></span>
* <span data-ttu-id="a4080-129">Funzionalità **PrivateNetworkClientServer**</span><span class="sxs-lookup"><span data-stu-id="a4080-129">**PrivateNetworkClientServer** capability</span></span>

![Impostazione delle funzionalità di Unity](images/mr-learning-sharing/sharing-02-section2-step1-2.png)

## <a name="installing-inbuilt-unity-packages"></a><span data-ttu-id="a4080-131">Installazione di pacchetti di Unity incorporati</span><span class="sxs-lookup"><span data-stu-id="a4080-131">Installing inbuilt Unity packages</span></span>

<span data-ttu-id="a4080-132">Scegliere **Window** > **Package Manager** (Finestra > Gestione pacchetti) dal menu Unity per aprire la finestra Package Manager(Gestione pacchetti) e quindi selezionare **AR Foundation** e fare clic sul pulsante **Install** (Installa) per installare il pacchetto:</span><span class="sxs-lookup"><span data-stu-id="a4080-132">In the Unity menu, select **Window** > **Package Manager** to open the Package Manager window, then select **AR Foundation** and click the **Install** button to install the package:</span></span>

![Package Manager di Unity con AR Foundation selezionato](images/mr-learning-sharing/sharing-02-section3-step1-1.png)

> [!NOTE]
> <span data-ttu-id="a4080-134">Si sta installando il pacchetto AR Foundation richiesto da Azure Spatial Anchors SDK, che verrà importato nella sezione successiva.</span><span class="sxs-lookup"><span data-stu-id="a4080-134">You are installing the AR Foundation package because it is required by the Azure Spatial Anchors SDK you will import in the next section.</span></span>

## <a name="importing-the-tutorial-assets"></a><span data-ttu-id="a4080-135">Importazione degli asset dell'esercitazione</span><span class="sxs-lookup"><span data-stu-id="a4080-135">Importing the tutorial assets</span></span>

<span data-ttu-id="a4080-136">Aggiungere AzurespatialAnchors SDK V 2.7.1 nel progetto Unity, per aggiungere i pacchetti, seguire questa [esercitazione](https://docs.microsoft.com/en-us/azure/spatial-anchors/how-tos/setup-unity-project?tabs=UPMPackage)</span><span class="sxs-lookup"><span data-stu-id="a4080-136">Add AzurespatialAnchors SDK V2.7.1 into your unity project, to add the packages please follow this [tutorial](https://docs.microsoft.com/en-us/azure/spatial-anchors/how-tos/setup-unity-project?tabs=UPMPackage)</span></span>


<span data-ttu-id="a4080-137">Scarica e **importa** i pacchetti personalizzati di Unity seguenti, **nell'ordine in cui sono elencati**:</span><span class="sxs-lookup"><span data-stu-id="a4080-137">Download and **import** the following Unity custom packages **in the order they are listed**:</span></span>
 
* [<span data-ttu-id="a4080-138">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage</span><span class="sxs-lookup"><span data-stu-id="a4080-138">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.4.0/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage)
* [<span data-ttu-id="a4080-139">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.4.0.unitypackage</span><span class="sxs-lookup"><span data-stu-id="a4080-139">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.4.0.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-spatial-anchors-v2.4.0/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.4.0.unitypackage)
* [<span data-ttu-id="a4080-140">MRTK.HoloLens2.Unity.Tutorials.Assets.MultiUserCapabilities.2.4.0.unitypackage</span><span class="sxs-lookup"><span data-stu-id="a4080-140">MRTK.HoloLens2.Unity.Tutorials.Assets.MultiUserCapabilities.2.4.0.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/multi-user-capabilities-v2.4.0/MRTK.HoloLens2.Unity.Tutorials.Assets.MultiUserCapabilities.2.4.0.unitypackage)

<span data-ttu-id="a4080-141">Dopo l'importazione degli asset dell'esercitazione, la finestra Project (Progetto) avrà un aspetto simile al seguente:</span><span class="sxs-lookup"><span data-stu-id="a4080-141">After you have imported the tutorial assets your Project window should look similar to this:</span></span>

![Finestre Hierarchy, Scene e Project di Unity dopo l'importazione degli asset dell'esercitazione](images/mr-learning-sharing/sharing-02-section4-step1-1.png)

> [!TIP]
> <span data-ttu-id="a4080-143">Per un promemoria su come importare un pacchetto personalizzato Unity, è possibile fare riferimento alle istruzioni relative all' [importazione delle risorse dell'esercitazione](mr-learning-base-04.md#importing-the-tutorial-assets) .</span><span class="sxs-lookup"><span data-stu-id="a4080-143">For a reminder on how to import a Unity custom package, you can refer to the [Importing the tutorial assets](mr-learning-base-04.md#importing-the-tutorial-assets) instructions.</span></span>

> [!NOTE]
> <span data-ttu-id="a4080-144">Dopo aver importato il pacchetto di asset dell'esercitazione MultiUserCapabilities, nella finestra della console verranno visualizzati alcuni errori [CS0246](/dotnet/csharp/language-reference/compiler-messages/cs0246) che indicano che manca il tipo o lo spazio dei nomi.</span><span class="sxs-lookup"><span data-stu-id="a4080-144">After importing the MultiUserCapabilities tutorial assets package, you will see several [CS0246](/dotnet/csharp/language-reference/compiler-messages/cs0246) errors in the Console window stating that the type or namespace is missing.</span></span> <span data-ttu-id="a4080-145">Si tratta di un comportamento previsto, che verrà risolto nella prossima sezione quando verranno importati gli asset di PUN.</span><span class="sxs-lookup"><span data-stu-id="a4080-145">This is expected and will be resolved in the next section when you import the PUN assets.</span></span>

## <a name="importing-the-pun-assets"></a><span data-ttu-id="a4080-146">Importazione degli asset di PUN</span><span class="sxs-lookup"><span data-stu-id="a4080-146">Importing the PUN assets</span></span>

<span data-ttu-id="a4080-147">Nel menu di Unity selezionare **Window** > **Asset Store** (Finestra > Store degli asset) per aprire la finestra Asset Store (Store degli asset), cercare e selezionare **PUN 2 - FREE** (PUN 2 - GRATUITO) in Exit Games (Giochi in uscita) e fare clic sul pulsante **Download** (Scarica) per scaricare il pacchetto di asset nell'account Unity.</span><span class="sxs-lookup"><span data-stu-id="a4080-147">In the Unity menu, select **Window** > **Asset Store** to open the Asset Store window, search for and select **PUN 2 - FREE** from Exit Games, click the **Download** button to download the asset package to your Unity account.</span></span>

<span data-ttu-id="a4080-148">Al termine del download, fai clic sul pulsante **Import** (Importa) per aprire la finestra Import Unity Package (Importa pacchetto Unity):</span><span class="sxs-lookup"><span data-stu-id="a4080-148">When the download is complete, click the **Import** button to open the Import Unity Package window:</span></span>

![Unity Asset Store con PUN 2 - Free](images/mr-learning-sharing/sharing-02-section5-step1-1.png)

<span data-ttu-id="a4080-150">Nella finestra Import Unity Package (Importa il pacchetto Unity), fai clic sul pulsante **All** (Tutti) per assicurarti che vengano selezionati tutti gli asset e quindi fai clic sul pulsante **Import** (Importa) per importare gli asset:</span><span class="sxs-lookup"><span data-stu-id="a4080-150">In the Import Unity Package window, click the **All** button to ensure all the assets are selected, then click the **Import** button to import the assets:</span></span>

![Unity con la finestra per l'importazione di PUN 2](images/mr-learning-sharing/sharing-02-section5-step1-2.png)

<span data-ttu-id="a4080-152">Dopo che Unity ha completato il processo di importazione, verrà visualizzata la finestra PUN Wizard (Creazione guidata PUN) con il menu PUN Setup (Configurazione PUN) caricato. Per il momento puoi ignorare o chiudere questa finestra:</span><span class="sxs-lookup"><span data-stu-id="a4080-152">Once Unity has completed the import process, the Pun Wizard window will appear with the PUN Setup menu loaded, you can ignore or close this window for now:</span></span>

![Unity con la finestra per la configurazione di PUN 2](images/mr-learning-sharing/sharing-02-section5-step1-3.png)

## <a name="creating-the-pun-application"></a><span data-ttu-id="a4080-154">Creazione dell'applicazione PUN</span><span class="sxs-lookup"><span data-stu-id="a4080-154">Creating the PUN application</span></span>

<span data-ttu-id="a4080-155">In questa sezione si creerà un account Photon, se non esiste già, e una nuova app PUN.</span><span class="sxs-lookup"><span data-stu-id="a4080-155">In this section, you will create a Photon account, if you don't already have one, and create a new PUN app.</span></span>

<span data-ttu-id="a4080-156">Passa al <a href="https://dashboard.photonengine.com/account/signin" target="_blank">dashboard</a> di Photon ed esegui l'accesso se hai già un account che vuoi usare. In caso contrario, fai clic sul collegamento **Create One** (Creane uno) e segui le istruzioni per la registrazione di un nuovo account:</span><span class="sxs-lookup"><span data-stu-id="a4080-156">Navigate to the Photon <a href="https://dashboard.photonengine.com/account/signin" target="_blank">dashboard</a> and sign in if you already have an account you want to use, otherwise, click the **Create One** link and follow the instructions to register a new account:</span></span>

![Pagina di accesso di Photon](images/mr-learning-sharing/sharing-02-section6-step1-1.png)

<span data-ttu-id="a4080-158">Una volta eseguito l'accesso, fai clic sul pulsante **Create a New App** (Crea una nuova app):</span><span class="sxs-lookup"><span data-stu-id="a4080-158">Once signed in, click the **Create a New App** button:</span></span>

![Pagina di benvenuto del dashboard Photon](images/mr-learning-sharing/sharing-02-section6-step1-2.png)

<span data-ttu-id="a4080-160">Nella pagina Create a New Application (Crea una nuova applicazione) immetti i valori seguenti:</span><span class="sxs-lookup"><span data-stu-id="a4080-160">On the Create a New Application page, enter the following values:</span></span>

* <span data-ttu-id="a4080-161">In Photon Type (Tipo Photon) selezionare PUN</span><span class="sxs-lookup"><span data-stu-id="a4080-161">For Photon Type, select PUN</span></span>
* <span data-ttu-id="a4080-162">In Name (Nome) immetti un nome appropriato, ad esempio _MRTK Tutorials_</span><span class="sxs-lookup"><span data-stu-id="a4080-162">For Name, enter a suitable name, for example, _MRTK Tutorials_</span></span>
* <span data-ttu-id="a4080-163">In Description (Descrizione) immetti facoltativamente una descrizione appropriata</span><span class="sxs-lookup"><span data-stu-id="a4080-163">For Description, optionally enter a suitable description</span></span>
* <span data-ttu-id="a4080-164">In Url lascia il campo vuoto</span><span class="sxs-lookup"><span data-stu-id="a4080-164">For Url, leave the field empty</span></span>

<span data-ttu-id="a4080-165">Fare quindi clic sul pulsante **Create** (Crea) per creare la nuova app:</span><span class="sxs-lookup"><span data-stu-id="a4080-165">Then click the **Create** button to create the new app:</span></span>

![Pagina per la creazione dell'applicazione Photon](images/mr-learning-sharing/sharing-02-section6-step1-3.png)

<span data-ttu-id="a4080-167">Al termine del processo di creazione, nel dashboard verrà visualizzata la nuova app PUN:</span><span class="sxs-lookup"><span data-stu-id="a4080-167">Once Photon has finished the creation process, the new PUN app will appear on your dashboard:</span></span>

![Pagina dell'applicazione Photon](images/mr-learning-sharing/sharing-02-section6-step1-4.png)

## <a name="connecting-the-unity-project-to-the-pun-application"></a><span data-ttu-id="a4080-169">Connessione del progetto Unity all'applicazione PUN</span><span class="sxs-lookup"><span data-stu-id="a4080-169">Connecting the Unity project to the PUN application</span></span>

<span data-ttu-id="a4080-170">In questa sezione si connetterà il progetto Unity all'app PUN creata nella sezione precedente.</span><span class="sxs-lookup"><span data-stu-id="a4080-170">In this section, you will connect your Unity project to the PUN app you created in the previous section.</span></span>

<span data-ttu-id="a4080-171">Nel dashboard di Photon fai clic sul campo **App ID** (ID app) per visualizzare l'ID dell'app e quindi copialo negli Appunti:</span><span class="sxs-lookup"><span data-stu-id="a4080-171">On the Photon dashboard, click the **App ID** field to reveal the app ID, then copy it to your clipboard:</span></span>

![Pagina dell'applicazione Photon con App Id selezionato](images/mr-learning-sharing/sharing-02-section7-step1-1.png)

<span data-ttu-id="a4080-173">Nel menu di Unity seleziona **Window** (Finestra) > **Photon Unity Networking** > **PUN Wizard** (Creazione guidata PUN) per aprire la finestra PUN Wizard (Creazione guidata PUN), fai clic sul pulsante **Setup Project** (Configura progetto) per aprire il menu PUN Setup (Configurazione PUN) ed esegui la configurazione nel modo seguente:</span><span class="sxs-lookup"><span data-stu-id="a4080-173">In the Unity menu, select **Window** > **Photon Unity Networking** > **PUN Wizard** to open the Pun Wizard window, click the **Setup Project** button to open the PUN Setup menu, and configure it as follows:</span></span>

* <span data-ttu-id="a4080-174">Nel campo **AppId or Email** (ID app o e-mail) incolla l'ID dell'app PUN copiato nel passaggio precedente</span><span class="sxs-lookup"><span data-stu-id="a4080-174">In the **AppId or Email** field, paste the PUN app ID you copied in the previous step</span></span>

<span data-ttu-id="a4080-175">Fai quindi clic sul pulsante **Setup Project** (Configura progetto) per applicare l'ID dell'app:</span><span class="sxs-lookup"><span data-stu-id="a4080-175">Then click the **Setup Project** button to apply the app ID:</span></span>

![Finestra PUN Setup di Unity con AppId compilato](images/mr-learning-sharing/sharing-02-section7-step1-2.png)

<span data-ttu-id="a4080-177">Dopo che Unity ha terminato il processo di configurazione di PUN, nel menu PUN Setup (Configurazione PUN) verrà visualizzato il messaggio **Done!** (Fatto)</span><span class="sxs-lookup"><span data-stu-id="a4080-177">Once Unity has finished the PUN setup process, the PUN Setup menu will display the message **Done!**</span></span> <span data-ttu-id="a4080-178">e nella finestra Project (Progetto) verrà selezionato automaticamente l'asset **PhotonServerSettings**, in modo che le relative proprietà siano visualizzate nella finestra Inspector (Controllo):</span><span class="sxs-lookup"><span data-stu-id="a4080-178">and automatically select the **PhotonServerSettings** asset in the Project window, so its properties are displayed in the Inspector window:</span></span>

![Finestra PUN Setup di Unity con Setup Project applicato](images/mr-learning-sharing/sharing-02-section7-step1-3.png)

## <a name="congratulations"></a><span data-ttu-id="a4080-180">Lezione completata</span><span class="sxs-lookup"><span data-stu-id="a4080-180">Congratulations</span></span>

<span data-ttu-id="a4080-181">È stata creata un'app PUN ed è stata connessa al progetto Unity.</span><span class="sxs-lookup"><span data-stu-id="a4080-181">You have successfully created a PUN app and connected it to your Unity project.</span></span> <span data-ttu-id="a4080-182">Il passaggio successivo consiste nel consentire connessioni con altri utenti, in modo che ogni utente possa visualizzare il lavoro svolto dagli altri.</span><span class="sxs-lookup"><span data-stu-id="a4080-182">Your next step is to allow connections with other users so that multiple users can see each other.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="a4080-183">Esercitazione successiva: 3. Connessione di più utenti</span><span class="sxs-lookup"><span data-stu-id="a4080-183">Next Tutorial: 3. Connecting multiple users</span></span>](mr-learning-sharing-03.md)
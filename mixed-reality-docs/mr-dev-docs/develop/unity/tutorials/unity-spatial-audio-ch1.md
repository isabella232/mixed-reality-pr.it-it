---
title: Esercitazioni sull'audio spaziale - 1. Aggiunta di audio spaziale al progetto
description: Aggiungere il plug-in Microsoft Spatializer al progetto Unity per accedere HoloLens 2 offload hardware HRTF.
author: kegodin
ms.author: v-hferrone
ms.date: 02/05/2021
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens2, audio spaziale, MRTK, mixed reality toolkit, UWP, Windows 10, HRTF, funzione di trasferimento correlata alla testa, riverbero, Spazialista Microsoft
ms.openlocfilehash: 112531a3248461a5b380ad4b93de34545a2f2c3f
ms.sourcegitcommit: b4fd969b9c2e6313aa728b0dbee4b25014668720
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/04/2021
ms.locfileid: "111403362"
---
# <a name="1-adding-spatial-audio-to-your-unity-project"></a><span data-ttu-id="f4399-105">1. Aggiunta di audio spaziale al progetto Unity</span><span class="sxs-lookup"><span data-stu-id="f4399-105">1. Adding Spatial audio to your Unity project</span></span>

## <a name="overview"></a><span data-ttu-id="f4399-106">Panoramica</span><span class="sxs-lookup"><span data-stu-id="f4399-106">Overview</span></span>

<span data-ttu-id="f4399-107">Benvenuti nell'esercitazione sull'audio spaziale per Unity in HoloLens2.</span><span class="sxs-lookup"><span data-stu-id="f4399-107">Welcome to the spatial audio tutorial for Unity on HoloLens2.</span></span> <span data-ttu-id="f4399-108">In questa serie di esercitazioni si apprenderà come usare l'offload della funzione di trasferimento correlato alla testa (HRTF) in HoloLens 2 e Come abilitare il riverbero quando si usa l'offload HRTF.</span><span class="sxs-lookup"><span data-stu-id="f4399-108">Through this tutorial series, you will learn how to use head-related transfer function (HRTF) offload on HoloLens 2 and How to enable reverb when using HRTF offload.</span></span>

<span data-ttu-id="f4399-109">Il [repository GitHub di Microsoft Spatializer](https://github.com/microsoft/spatialaudio-unity) include un progetto Unity completato di questa sequenza di esercitazioni.</span><span class="sxs-lookup"><span data-stu-id="f4399-109">The [Microsoft Spatializer GitHub repository](https://github.com/microsoft/spatialaudio-unity) has a completed Unity project of this tutorial sequence.</span></span>

<span data-ttu-id="f4399-110">Per comprendere cosa significa spazializzare i suoni usando tecnologie di spazializzazione basate su HRTF e consigli su quando può essere utile, vedere Spatial Sound Design (Progettazione dei suoni [spaziali).](/windows/mixed-reality/spatial-sound-design)</span><span class="sxs-lookup"><span data-stu-id="f4399-110">For an understanding of what it means to spatialize sounds using HRTF-based spatialization technologies and recommendations for when it can be helpful, see [spatial sound design](/windows/mixed-reality/spatial-sound-design).</span></span>

## <a name="what-is-hrtf-offload"></a><span data-ttu-id="f4399-111">Che cos'è l'offload HRTF?</span><span class="sxs-lookup"><span data-stu-id="f4399-111">What is HRTF offload?</span></span>

<span data-ttu-id="f4399-112">L'elaborazione audio con algoritmi basati su HRTF richiede una grande quantità di calcoli specializzati.</span><span class="sxs-lookup"><span data-stu-id="f4399-112">Processing audio using HRTF-based algorithms requires a large amount of specialized computation.</span></span> <span data-ttu-id="f4399-113">HoloLens 2 include hardware dedicato che può essere utilizzato per evitare il carico di lavoro del processore dell'applicazione, "offload" dell'elaborazione di algoritmi basati su HRTF.</span><span class="sxs-lookup"><span data-stu-id="f4399-113">HoloLens 2 includes dedicated hardware that can be utilized to avoid burdening the application processor, thus "offloading" the processing of HRTF-based algorithms.</span></span>  <span data-ttu-id="f4399-114">Il plug-in microsoft spatializer offre un modo semplice per l'applicazione di sfruttare l'hardware HRTF dedicato, in modo che l'applicazione possa usare più processori dell'applicazione per operazioni diverse dall'audio spaziale.</span><span class="sxs-lookup"><span data-stu-id="f4399-114">The Microsoft spatializer plugin provides an easy way for your application to take advantage of the dedicated HRTF hardware so your application can use more of the application processor for operations other than spatial audio.</span></span>

## <a name="objectives"></a><span data-ttu-id="f4399-115">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="f4399-115">Objectives</span></span>

* <span data-ttu-id="f4399-116">Importazione e abilitazione del plug-in microsoft spatializer</span><span class="sxs-lookup"><span data-stu-id="f4399-116">Importing and Enabling Microsoft spatializer plugin</span></span>
* <span data-ttu-id="f4399-117">Abilitazione dell'audio spaziale nella workstation per sviluppatori</span><span class="sxs-lookup"><span data-stu-id="f4399-117">Enabling Spatial audio on your developer workstation</span></span>

## <a name="prerequisites"></a><span data-ttu-id="f4399-118">Prerequisiti</span><span class="sxs-lookup"><span data-stu-id="f4399-118">Prerequisites</span></span>

* <span data-ttu-id="f4399-119">Un PC Windows 10 configurato in cui siano [installati gli strumenti](../../install-the-tools.md) corretti</span><span class="sxs-lookup"><span data-stu-id="f4399-119">A Windows 10 PC configured with the correct [tools installed](../../install-the-tools.md)</span></span>
* <span data-ttu-id="f4399-120">Conoscenza della programmazione C# di base</span><span class="sxs-lookup"><span data-stu-id="f4399-120">Basic c# programming knowledge</span></span>
* <span data-ttu-id="f4399-121">Un dispositivo HoloLens 2 [configurato per lo sviluppo](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)</span><span class="sxs-lookup"><span data-stu-id="f4399-121">A HoloLens 2 device [configured for development](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)</span></span>
* <span data-ttu-id="f4399-122"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> con Unity 2020/2019 LTS montato e il modulo piattaforma UWP (Universal Windows Platform) Build Support aggiunto</span><span class="sxs-lookup"><span data-stu-id="f4399-122"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2020/2019 LTS mounted, and the Universal Windows Platform Build Support module added</span></span>

<span data-ttu-id="f4399-123">È **consigliabile** completare la serie [di](mr-learning-base-01.md) esercitazioni introduttive o avere un'esperienza di base precedente con Unity e MRTK prima di continuare.</span><span class="sxs-lookup"><span data-stu-id="f4399-123">We **strongly recommend** completing the [Getting started](mr-learning-base-01.md) tutorials series or having some basic prior experience with Unity and MRTK before continuing.</span></span>

> [!Important]
> <span data-ttu-id="f4399-124">Questa serie di esercitazioni supporta Unity 2020 LTS (attualmente 2020.3.x) se si usa Open XR o Windows XR Plugin e anche Unity 2019 LTS (attualmente 2019.4.x) se si usa WSA legacy o Windows XR Plugin.</span><span class="sxs-lookup"><span data-stu-id="f4399-124">This tutorial series supports Unity 2020 LTS(currently 2020.3.x) if you are using Open XR or Windows XR Plugin and also Unity 2019 LTS (currently 2019.4.x) if you are using Legacy WSA or Windows XR Plugin.</span></span> <span data-ttu-id="f4399-125">Questa istruzione sostituisce gli eventuali requisiti relativi alla versione di Unity indicati negli argomenti visualizzabili facendo clic sui collegamenti dei prerequisiti sopra riportati.</span><span class="sxs-lookup"><span data-stu-id="f4399-125">This supersedes any Unity version requirements stated in the prerequisites linked above.</span></span>

## <a name="creating-and-preparing-the-unity-project"></a><span data-ttu-id="f4399-126">Creazione e preparazione del progetto Unity</span><span class="sxs-lookup"><span data-stu-id="f4399-126">Creating and preparing the Unity project</span></span>

<span data-ttu-id="f4399-127">In questa sezione creerai un nuovo progetto Unity per prepararti allo sviluppo con MRTK.</span><span class="sxs-lookup"><span data-stu-id="f4399-127">In this section, you will create a new Unity project and get it ready for MRTK development.</span></span>

<span data-ttu-id="f4399-128">A questo scopo, segui prima l'esercitazione [Inizializzazione del progetto e prima applicazione](mr-learning-base-02.md), escluse le istruzioni della sezione [Compilare l'applicazione nel dispositivo](mr-learning-base-02.md#building-your-application-to-your-hololens-2), che include i passaggi seguenti:</span><span class="sxs-lookup"><span data-stu-id="f4399-128">For this, first follow the [Initializing your project and first application](mr-learning-base-02.md), excluding the [Build your application to your device](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions, which includes the following steps:</span></span>

1. <span data-ttu-id="f4399-129">[Creazione del progetto Unity](mr-learning-base-02.md#creating-the-unity-project) e assegnazione di un nome appropriato, ad esempio *MRTK Tutorials*</span><span class="sxs-lookup"><span data-stu-id="f4399-129">[Creating the Unity project](mr-learning-base-02.md#creating-the-unity-project) and give it a suitable name, for example, *MRTK Tutorials*</span></span>

1. [<span data-ttu-id="f4399-130">Passaggio a un'altra piattaforma di compilazione</span><span class="sxs-lookup"><span data-stu-id="f4399-130">Switching the build platform</span></span>](mr-learning-base-02.md#configuring-the-unity-project)

1. [<span data-ttu-id="f4399-131">Importazione delle risorse essenziali TextMeshPro</span><span class="sxs-lookup"><span data-stu-id="f4399-131">Importing the TextMeshPro Essential Resources</span></span>](mr-learning-base-02.md#importing-the-textmeshpro-essential-resources)

1. [<span data-ttu-id="f4399-132">Importazione di Mixed Reality Toolkit e configurazione del progetto Unity</span><span class="sxs-lookup"><span data-stu-id="f4399-132">Importing the Mixed Reality Toolkit and Configuring the Unity project</span></span>](mr-learning-base-02.md#importing-the-mixed-reality-toolkit-and-configuring-the-unity-project)

1. <span data-ttu-id="f4399-133">[Creazione e configurazione della scena e](mr-learning-base-02.md#creating-the-scene-and-configuring-mrtk) assegnare alla scena un nome appropriato, ad esempio *SpatialAudio*</span><span class="sxs-lookup"><span data-stu-id="f4399-133">[Creating and configuring the scene](mr-learning-base-02.md#creating-the-scene-and-configuring-mrtk) and give the scene a suitable name, for example, *SpatialAudio*</span></span>

<span data-ttu-id="f4399-134">Segui quindi [](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) le istruzioni riportate in Modifica dell'opzione di visualizzazione della consapevolezza spaziale per assicurarti che il profilo di configurazione di MRTK per la scena sia **DefaultHoloLens2ConfigurationProfile** e modifica le opzioni di visualizzazione per la mesh di consapevolezza spaziale in **Occlusion**.</span><span class="sxs-lookup"><span data-stu-id="f4399-134">Then follow the [Changing the Spatial Awareness Display Option](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) instructions to ensure the MRTK configuration profile for your scene is **DefaultHoloLens2ConfigurationProfile** and change the display options for the spatial awareness mesh to **Occlusion**.</span></span>

## <a name="adding-microsoft-spatializer-to-the-project"></a><span data-ttu-id="f4399-135">Aggiunta di Microsoft Spatializer al progetto</span><span class="sxs-lookup"><span data-stu-id="f4399-135">Adding Microsoft Spatializer to the Project</span></span>

<span data-ttu-id="f4399-136">Scaricare e importare  <a href="https://github.com/microsoft/spatialaudio-unity/releases/download/v1.0.18/Microsoft.SpatialAudio.Spatializer.Unity.1.0.18.unitypackage" target="_blank">Microsoft.SpatialAudio.Spatializer.Unity.1.0.18.unitypackage </a></span><span class="sxs-lookup"><span data-stu-id="f4399-136">Download and import the Microsoft Spatializer  <a href="https://github.com/microsoft/spatialaudio-unity/releases/download/v1.0.18/Microsoft.SpatialAudio.Spatializer.Unity.1.0.18.unitypackage" target="_blank">Microsoft.SpatialAudio.Spatializer.Unity.1.0.18.unitypackage </a></span></span>

>[!TIP]
> <span data-ttu-id="f4399-137">Per un promemoria su come importare un pacchetto personalizzato di Unity, vedere le istruzioni relative all'importazione degli [asset dell'esercitazione.](mr-learning-base-02.md#importing-the-tutorial-assets)</span><span class="sxs-lookup"><span data-stu-id="f4399-137">For a reminder on how to import a Unity custom package, you can refer to the [Importing the tutorial assets](mr-learning-base-02.md#importing-the-tutorial-assets) instructions.</span></span>

## <a name="enable-the-microsoft-spatializer-plugin"></a><span data-ttu-id="f4399-138">Abilitare il plug-in Microsoft Spatializer</span><span class="sxs-lookup"><span data-stu-id="f4399-138">Enable the Microsoft Spatializer plugin</span></span>

<span data-ttu-id="f4399-139">Dopo aver importato Microsoft **Spatializer** nel progetto Unity, verrà visualizzata la finestra **MRTK Project Configurator(Configuratore progetto MRTK),** usare l'elenco a discesa **Spazializzatore audio** per selezionare l'utilità di spazializzatore Microsoft e quindi fare clic sul pulsante Applica per applicare l'impostazione:</span><span class="sxs-lookup"><span data-stu-id="f4399-139">Once you import the Microsoft Spatializer into your unity project, **MRTK Project Configurator** window will appear, use the **Audio spatializer** dropdown to select the **Microsoft Spatializer**, then click the Apply button to apply the setting:</span></span>

![Configuratore di progetti MRTK](images/spatial-audio/spatial-audio-01-section3-step1-1.PNG)

<span data-ttu-id="f4399-141">È anche possibile abilitare manualmente Microsoft Spatializer: Open **Edit -> Project Settings -> Audio** e modificare **Spatializer Plugin (Plug-in** spazializzatore Microsoft) in "Microsoft Spatializer".</span><span class="sxs-lookup"><span data-stu-id="f4399-141">you can also manually enable the Microsoft Spatializer: Open **Edit -> Project Settings -> Audio**, and change **Spatializer Plugin** to "Microsoft Spatializer".</span></span>

![Impostazioni del progetto che mostra il plug-in dello spazializzatore](images/spatial-audio/spatial-audio-01-section3-step1-2.PNG)

## <a name="enable-spatial-audio-on-your-workstation"></a><span data-ttu-id="f4399-143">Abilitare l'audio spaziale nella workstation</span><span class="sxs-lookup"><span data-stu-id="f4399-143">Enable spatial audio on your workstation</span></span>

<span data-ttu-id="f4399-144">Nelle versioni desktop di Windows l'audio spaziale è disabilitato per impostazione predefinita.</span><span class="sxs-lookup"><span data-stu-id="f4399-144">On desktop versions of Windows, spatial audio is disabled by default.</span></span> <span data-ttu-id="f4399-145">Abilitarla facendo clic con il pulsante destro del mouse sull'icona del volume nella barra delle applicazioni.</span><span class="sxs-lookup"><span data-stu-id="f4399-145">Enable it by right-clicking on the volume icon in the task bar.</span></span> <span data-ttu-id="f4399-146">Per ottenere la migliore rappresentazione di ciò che si HoloLens 2, scegliere Audio spaziale **-> Windows Sonic per cuffie**.</span><span class="sxs-lookup"><span data-stu-id="f4399-146">To get the best representation of what you'll hear on HoloLens 2, choose **Spatial sound -> Windows Sonic for Headphones**.</span></span>

![Impostazioni audio spaziali del desktop](images/spatial-audio/spatial-audio-01-section4-step1-1.PNG)

> [!NOTE]
> <span data-ttu-id="f4399-148">Questa impostazione è necessaria solo se si prevede di testare il progetto nell'editor di Unity.</span><span class="sxs-lookup"><span data-stu-id="f4399-148">This setting is only required if you plan to test your project in the Unity editor.</span></span>

## <a name="congratulations"></a><span data-ttu-id="f4399-149">Lezione completata</span><span class="sxs-lookup"><span data-stu-id="f4399-149">Congratulations</span></span>

<span data-ttu-id="f4399-150">In questa esercitazione si è appreso come importare e abilitare il plug-in Microsoft Spatializer e come abilitare l'audio spaziale nella workstation.</span><span class="sxs-lookup"><span data-stu-id="f4399-150">In this tutorial you have learnt how to Import and enable the Microsoft Spatializer plugin and also to enable the spatial audio on your workstation.</span></span>
<span data-ttu-id="f4399-151">Nell'esercitazione successiva si apprenderà come aggiungere audio spaziale nel progetto Unity.</span><span class="sxs-lookup"><span data-stu-id="f4399-151">In the next tutorial you will learn how to add spatial audio in the unity project.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="f4399-152">Esercitazione successiva: 2. Spazializzazione dei suoni di interazione dei pulsanti</span><span class="sxs-lookup"><span data-stu-id="f4399-152">Next Tutorial: 2. Spatializing button interaction sounds</span></span>](unity-spatial-audio-ch2.md)

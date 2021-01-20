---
title: Esercitazioni audio spaziali-1. Aggiunta di audio spaziale al progetto
description: Aggiungere il plug-in Microsoft Spatializer al progetto Unity per accedere a HoloLens 2 HRTF hardware offload.
author: kegodin
ms.author: v-hferrone
ms.date: 12/01/2019
ms.topic: article
keywords: realtà mista, Unity, esercitazione, hololens2, audio spaziale, MRTK, Toolkit per realtà mista, UWP, Windows 10, HRTF, funzione di trasferimento relativa alla testa, Reverb, Microsoft Spatializer
ms.openlocfilehash: 1eb2913f1953e334cfe75b786f96bb51a9852fc5
ms.sourcegitcommit: a56a551ebc59529a3683fe6db90d59f982ab0b45
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/19/2021
ms.locfileid: "98578450"
---
# <a name="1-adding-spatial-audio-to-your-unity-project"></a><span data-ttu-id="42bc4-105">1. aggiunta di audio spaziale al progetto Unity</span><span class="sxs-lookup"><span data-stu-id="42bc4-105">1. Adding Spatial audio to your Unity project</span></span>

## <a name="overview"></a><span data-ttu-id="42bc4-106">Panoramica</span><span class="sxs-lookup"><span data-stu-id="42bc4-106">Overview</span></span>

<span data-ttu-id="42bc4-107">Benvenuti nell'esercitazione sull'audio spaziale per Unity in HoloLens2.</span><span class="sxs-lookup"><span data-stu-id="42bc4-107">Welcome to the spatial audio tutorial for Unity on HoloLens2.</span></span> <span data-ttu-id="42bc4-108">Con questa serie di esercitazioni si apprenderà come usare l'offload della funzione di trasferimento Head-Related (HRTF) in HoloLens 2 e come abilitare il riverbero quando si usa l'offload HRTF.</span><span class="sxs-lookup"><span data-stu-id="42bc4-108">Through this tutorial series, you will learn how to use head-related transfer function (HRTF) offload on HoloLens 2 and How to enable reverb when using HRTF offload.</span></span>

<span data-ttu-id="42bc4-109">Il [repository GitHub Microsoft Spatializer](https://github.com/microsoft/spatialaudio-unity) include un progetto Unity completato di questa sequenza di esercitazione.</span><span class="sxs-lookup"><span data-stu-id="42bc4-109">The [Microsoft Spatializer GitHub repository](https://github.com/microsoft/spatialaudio-unity) has a completed Unity project of this tutorial sequence.</span></span>

<span data-ttu-id="42bc4-110">Per informazioni su ciò che significa spatialize i suoni usando le tecnologie di spazializzazione basate su HRTF e consigli per quando può essere utile, vedere [progettazione di suoni spaziali](https://docs.microsoft.com/windows/mixed-reality/spatial-sound-design).</span><span class="sxs-lookup"><span data-stu-id="42bc4-110">For an understanding of what it means to spatialize sounds using HRTF-based spatialization technologies and recommendations for when it can be helpful, see [spatial sound design](https://docs.microsoft.com/windows/mixed-reality/spatial-sound-design).</span></span>

## <a name="what-is-hrtf-offload"></a><span data-ttu-id="42bc4-111">Che cos'è HRTF offload?</span><span class="sxs-lookup"><span data-stu-id="42bc4-111">What is HRTF offload?</span></span>

<span data-ttu-id="42bc4-112">L'elaborazione di audio con algoritmi basati su HRTF richiede una grande quantità di calcoli specializzati.</span><span class="sxs-lookup"><span data-stu-id="42bc4-112">Processing audio using HRTF-based algorithms requires a large amount of specialized computation.</span></span> <span data-ttu-id="42bc4-113">HoloLens 2 include hardware dedicato che può essere utilizzato per evitare di sovraccaricare il processore di applicazioni, quindi "offload" dell'elaborazione degli algoritmi basati su HRTF.</span><span class="sxs-lookup"><span data-stu-id="42bc4-113">HoloLens 2 includes dedicated hardware that can be utilized to avoid burdening the application processor, thus "offloading" the processing of HRTF-based algorithms.</span></span>  <span data-ttu-id="42bc4-114">Il plug-in Microsoft Spatializer offre un modo semplice per consentire all'applicazione di sfruttare i vantaggi dell'hardware HRTF dedicato, in modo che l'applicazione possa usare più processori di applicazioni per operazioni diverse dall'audio spaziale.</span><span class="sxs-lookup"><span data-stu-id="42bc4-114">The Microsoft spatializer plugin provides an easy way for your application to take advantage of the dedicated HRTF hardware so your application can use more of the application processor for operations other than spatial audio.</span></span>

## <a name="objectives"></a><span data-ttu-id="42bc4-115">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="42bc4-115">Objectives</span></span>

* <span data-ttu-id="42bc4-116">Importazione e abilitazione del plug-in Microsoft Spatializer</span><span class="sxs-lookup"><span data-stu-id="42bc4-116">Importing and Enabling Microsoft spatializer plugin</span></span>
* <span data-ttu-id="42bc4-117">Abilitazione dell'audio spaziale nella workstation per sviluppatori</span><span class="sxs-lookup"><span data-stu-id="42bc4-117">Enabling Spatial audio on your developer workstation</span></span>

## <a name="prerequisites"></a><span data-ttu-id="42bc4-118">Prerequisiti</span><span class="sxs-lookup"><span data-stu-id="42bc4-118">Prerequisites</span></span>

* <span data-ttu-id="42bc4-119">Un PC Windows 10 configurato in cui siano [installati gli strumenti](../../install-the-tools.md) corretti</span><span class="sxs-lookup"><span data-stu-id="42bc4-119">A Windows 10 PC configured with the correct [tools installed](../../install-the-tools.md)</span></span>
* <span data-ttu-id="42bc4-120">Conoscenza della programmazione C# di base</span><span class="sxs-lookup"><span data-stu-id="42bc4-120">Basic c# programming knowledge</span></span>
* <span data-ttu-id="42bc4-121">Un dispositivo HoloLens 2 [configurato per lo sviluppo](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)</span><span class="sxs-lookup"><span data-stu-id="42bc4-121">A HoloLens 2 device [configured for development](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)</span></span>
* <span data-ttu-id="42bc4-122"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> con Unity 2019 LTS installato e il modulo di supporto per la compilazione UWP (Universal Windows Platform) aggiunto</span><span class="sxs-lookup"><span data-stu-id="42bc4-122"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019 LTS mounted, and the Universal Windows Platform Build Support module added</span></span>

<span data-ttu-id="42bc4-123">Prima di continuare, è **consigliabile** completare la serie di esercitazioni [introduttive](mr-learning-base-01.md) oppure avere un'esperienza di base precedente con Unity e MRTK.</span><span class="sxs-lookup"><span data-stu-id="42bc4-123">We **strongly recommend** completing the [Getting started](mr-learning-base-01.md) tutorials series or having some basic prior experience with Unity and MRTK before continuing.</span></span>

> [!IMPORTANT]
>
> * <span data-ttu-id="42bc4-124">La versione di Unity consigliata per questa serie di esercitazioni è Unity 2019 LTS.</span><span class="sxs-lookup"><span data-stu-id="42bc4-124">The recommended Unity version for this tutorial series is Unity 2019 LTS.</span></span> <span data-ttu-id="42bc4-125">Questa istruzione sostituisce gli eventuali requisiti o suggerimenti relativi alla versione di Unity indicati negli argomenti visualizzabili facendo clic sui collegamenti dei prerequisiti sopra riportati.</span><span class="sxs-lookup"><span data-stu-id="42bc4-125">It supersedes any Unity version requirements or recommendations stated in the prerequisites linked above.</span></span>

## <a name="creating-and-preparing-the-unity-project"></a><span data-ttu-id="42bc4-126">Creazione e preparazione del progetto Unity</span><span class="sxs-lookup"><span data-stu-id="42bc4-126">Creating and preparing the Unity project</span></span>

<span data-ttu-id="42bc4-127">In questa sezione creerai un nuovo progetto Unity per prepararti allo sviluppo con MRTK.</span><span class="sxs-lookup"><span data-stu-id="42bc4-127">In this section, you will create a new Unity project and get it ready for MRTK development.</span></span>

<span data-ttu-id="42bc4-128">A questo scopo, segui prima l'esercitazione [Inizializzazione del progetto e prima applicazione](mr-learning-base-02.md), escluse le istruzioni della sezione [Compilare l'applicazione nel dispositivo](mr-learning-base-02.md#building-your-application-to-your-hololens-2), che include i passaggi seguenti:</span><span class="sxs-lookup"><span data-stu-id="42bc4-128">For this, first follow the [Initializing your project and first application](mr-learning-base-02.md), excluding the [Build your application to your device](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions, which includes the following steps:</span></span>

1. <span data-ttu-id="42bc4-129">[Creazione del progetto Unity](mr-learning-base-02.md#creating-the-unity-project) e assegnazione di un nome appropriato, ad esempio *MRTK Tutorials*</span><span class="sxs-lookup"><span data-stu-id="42bc4-129">[Creating the Unity project](mr-learning-base-02.md#creating-the-unity-project) and give it a suitable name, for example, *MRTK Tutorials*</span></span>

1. [<span data-ttu-id="42bc4-130">Passaggio a un'altra piattaforma di compilazione</span><span class="sxs-lookup"><span data-stu-id="42bc4-130">Switching the build platform</span></span>](mr-learning-base-02.md#configuring-the-unity-project)

1. [<span data-ttu-id="42bc4-131">Importazione delle risorse essenziali TextMeshPro</span><span class="sxs-lookup"><span data-stu-id="42bc4-131">Importing the TextMeshPro Essential Resources</span></span>](mr-learning-base-02.md#importing-the-textmeshpro-essential-resources)

1. [<span data-ttu-id="42bc4-132">Importazione di Mixed Reality Toolkit</span><span class="sxs-lookup"><span data-stu-id="42bc4-132">Importing the Mixed Reality Toolkit</span></span>](mr-learning-base-02.md#importing-the-mixed-reality-toolkit)

1. [<span data-ttu-id="42bc4-133">Configurazione del progetto Unity</span><span class="sxs-lookup"><span data-stu-id="42bc4-133">Configuring the Unity project</span></span>](mr-learning-base-02.md#configuring-the-unity-project)

1. <span data-ttu-id="42bc4-134">[Creazione e impostazione della scena](mr-learning-base-02.md#creating-and-configuring-the-scene) e assegnare alla scena un nome appropriato, ad esempio *SpatialAudio*</span><span class="sxs-lookup"><span data-stu-id="42bc4-134">[Creating and setting the scene](mr-learning-base-02.md#creating-and-configuring-the-scene) and give the scene a suitable name, for example, *SpatialAudio*</span></span>

<span data-ttu-id="42bc4-135">Quindi, seguire le istruzioni per la [modifica delle opzioni di visualizzazione di riconoscimento spaziale](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) per verificare che il profilo di configurazione MRTK per la scena sia **DefaultXRSDKConfigurationProfile** e modificare le opzioni di visualizzazione per la mesh di riconoscimento spaziale in **occlusione**.</span><span class="sxs-lookup"><span data-stu-id="42bc4-135">Then follow the [Changing the Spatial Awareness Display Option](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) instructions to ensure the MRTK configuration profile for your scene is **DefaultXRSDKConfigurationProfile** and change the display options for the spatial awareness mesh to **Occlusion**.</span></span>

## <a name="adding-microsoft-spatializer-to-the-project"></a><span data-ttu-id="42bc4-136">Aggiunta di Microsoft Spatializer al progetto</span><span class="sxs-lookup"><span data-stu-id="42bc4-136">Adding Microsoft Spatializer to the Project</span></span>

<span data-ttu-id="42bc4-137">Scaricare e importare Microsoft Spatializer  <a href="https://github.com/microsoft/spatialaudio-unity/releases/download/v1.0.18/Microsoft.SpatialAudio.Spatializer.Unity.1.0.18.unitypackage" target="_blank">Microsoft. SpatialAudio. Spatializer. Unity. 1.0.18. file unitypackage Tools </a></span><span class="sxs-lookup"><span data-stu-id="42bc4-137">Download and import the Microsoft Spatializer  <a href="https://github.com/microsoft/spatialaudio-unity/releases/download/v1.0.18/Microsoft.SpatialAudio.Spatializer.Unity.1.0.18.unitypackage" target="_blank">Microsoft.SpatialAudio.Spatializer.Unity.1.0.18.unitypackage </a></span></span>

>[!TIP]
> <span data-ttu-id="42bc4-138">Per rivedere la procedura di importazione di un pacchetto personalizzato di Unity, puoi fare riferimento alle istruzioni contenute in [Importare Mixed Reality Toolkit](../../../mrlearning-base-ch1.md#import-the-mixed-reality-toolkit).</span><span class="sxs-lookup"><span data-stu-id="42bc4-138">For a reminder on how to import a Unity custom package, you can refer to the [Import the Mixed Reality Toolkit](../../../mrlearning-base-ch1.md#import-the-mixed-reality-toolkit) instructions.</span></span>

## <a name="enable-the-microsoft-spatializer-plugin"></a><span data-ttu-id="42bc4-139">Abilitare il plug-in Microsoft Spatializer</span><span class="sxs-lookup"><span data-stu-id="42bc4-139">Enable the Microsoft Spatializer plugin</span></span>

<span data-ttu-id="42bc4-140">Dopo aver importato **Microsoft Spatializer** , è necessario abilitarlo.</span><span class="sxs-lookup"><span data-stu-id="42bc4-140">After importing the **Microsoft Spatializer** you need to enable it.</span></span> <span data-ttu-id="42bc4-141">Aprire **modifica-> impostazioni progetto-> audio** e modificare il **plug** -in Spatializer in "Microsoft Spatializer".</span><span class="sxs-lookup"><span data-stu-id="42bc4-141">Open **Edit -> Project Settings -> Audio**, and change **Spatializer Plugin** to "Microsoft Spatializer".</span></span>

![Impostazioni del progetto che mostrano il plug-in Spatializer](images/spatial-audio/spatial-audio-01-section3-step1-1.png)

## <a name="enable-spatial-audio-on-your-workstation"></a><span data-ttu-id="42bc4-143">Abilitare l'audio spaziale nella workstation</span><span class="sxs-lookup"><span data-stu-id="42bc4-143">Enable spatial audio on your workstation</span></span>

<span data-ttu-id="42bc4-144">Nelle versioni desktop di Windows, l'audio spaziale è disabilitato per impostazione predefinita.</span><span class="sxs-lookup"><span data-stu-id="42bc4-144">On desktop versions of Windows, spatial audio is disabled by default.</span></span> <span data-ttu-id="42bc4-145">Per abilitarla, fare clic con il pulsante destro del mouse sull'icona del volume sulla barra delle applicazioni.</span><span class="sxs-lookup"><span data-stu-id="42bc4-145">Enable it by right-clicking on the volume icon in the task bar.</span></span> <span data-ttu-id="42bc4-146">Per ottenere la migliore rappresentazione di ciò che è possibile sentire in HoloLens 2, scegliere **audio spaziale > Windows Sonic per le cuffie**.</span><span class="sxs-lookup"><span data-stu-id="42bc4-146">To get the best representation of what you'll hear on HoloLens 2, choose **Spatial sound -> Windows Sonic for Headphones**.</span></span>

![Impostazioni audio spaziali desktop](images/spatial-audio/spatial-audio-01-section4-step1-1.png)

> [!NOTE]
> <span data-ttu-id="42bc4-148">Questa impostazione è necessaria solo se si prevede di testare il progetto nell'editor di Unity.</span><span class="sxs-lookup"><span data-stu-id="42bc4-148">This setting is only required if you plan to test your project in the Unity editor.</span></span>

## <a name="congratulations"></a><span data-ttu-id="42bc4-149">Lezione completata</span><span class="sxs-lookup"><span data-stu-id="42bc4-149">Congratulations</span></span>

<span data-ttu-id="42bc4-150">In questa esercitazione è stato illustrato come importare e abilitare il plug-in Microsoft Spatializer e anche per abilitare l'audio spaziale nella workstation.</span><span class="sxs-lookup"><span data-stu-id="42bc4-150">In this tutorial you have learnt how to Import and enable the Microsoft Spatializer plugin and also to enable the spatial audio on your workstation.</span></span>
<span data-ttu-id="42bc4-151">Nell'esercitazione successiva si apprenderà come aggiungere audio spaziale nel progetto Unity.</span><span class="sxs-lookup"><span data-stu-id="42bc4-151">In the next tutorial you will learn how to add spatial audio in the unity project.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="42bc4-152">Esercitazione successiva: 2. suoni di interazione con il pulsante Spatializing</span><span class="sxs-lookup"><span data-stu-id="42bc4-152">Next Tutorial: 2. Spatializing button interaction sounds</span></span>](unity-spatial-audio-ch2.md)

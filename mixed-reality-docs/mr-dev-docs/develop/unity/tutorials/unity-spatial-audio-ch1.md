---
title: Esercitazioni audio spaziali-1. Aggiunta di audio spaziale al progetto
description: Aggiungere il plug-in Microsoft Spatializer al progetto Unity per accedere a HoloLens 2 HRTF hardware offload.
author: kegodin
ms.author: v-hferrone
ms.date: 12/01/2019
ms.topic: article
keywords: realtà mista, Unity, esercitazione, hololens2, audio spaziale, MRTK, Toolkit per realtà mista, UWP, Windows 10, HRTF, funzione di trasferimento relativa alla testa, Reverb, Microsoft Spatializer
ms.openlocfilehash: 8790c4c62ab4c1b2b9e9f9c5c6fe0583b9e36545
ms.sourcegitcommit: fbeff51cae92add88d2b960c9b7bbfb04d5a0291
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/10/2020
ms.locfileid: "97002506"
---
# <a name="adding-spatial-audio-to-your-unity-project"></a><span data-ttu-id="8fda4-105">Aggiunta di audio spaziale al progetto Unity</span><span class="sxs-lookup"><span data-stu-id="8fda4-105">Adding spatial audio to your Unity project</span></span>

<span data-ttu-id="8fda4-106">Benvenuti nell'esercitazione sull'audio spaziale per Unity in HoloLens2.</span><span class="sxs-lookup"><span data-stu-id="8fda4-106">Welcome to the spatial audio tutorial for Unity on HoloLens2.</span></span> <span data-ttu-id="8fda4-107">Questa sequenza di esercitazione Mostra:</span><span class="sxs-lookup"><span data-stu-id="8fda4-107">This tutorial sequence shows:</span></span>
* <span data-ttu-id="8fda4-108">Come usare l'offload della funzione di trasferimento delle intestazioni (HRTF) in HoloLens 2 in Unity</span><span class="sxs-lookup"><span data-stu-id="8fda4-108">How to use head-related transfer function (HRTF) offload on HoloLens 2 in Unity</span></span>
* <span data-ttu-id="8fda4-109">Come abilitare il riverbero quando si usa l'offload HRTF</span><span class="sxs-lookup"><span data-stu-id="8fda4-109">How to enable reverb when using HRTF offload</span></span>

<span data-ttu-id="8fda4-110">Il [repository GitHub Microsoft Spatializer](https://github.com/microsoft/spatialaudio-unity) include un progetto Unity completato di questa sequenza di esercitazione.</span><span class="sxs-lookup"><span data-stu-id="8fda4-110">The [Microsoft Spatializer GitHub repository](https://github.com/microsoft/spatialaudio-unity) has a completed Unity project of this tutorial sequence.</span></span> 

<span data-ttu-id="8fda4-111">Per informazioni su ciò che significa spatialize i suoni usando le tecnologie di spazializzazione basate su HRTF e consigli per quando può essere utile, vedere [progettazione di suoni spaziali](https://docs.microsoft.com/windows/mixed-reality/spatial-sound-design).</span><span class="sxs-lookup"><span data-stu-id="8fda4-111">For an understanding about what it means to spatialize sounds using HRTF-based spatialization technologies and recommendations for when it can be helpful, see [spatial sound design](https://docs.microsoft.com/windows/mixed-reality/spatial-sound-design).</span></span>

## <a name="what-is-hrtf-offload"></a><span data-ttu-id="8fda4-112">Che cos'è HRTF offload?</span><span class="sxs-lookup"><span data-stu-id="8fda4-112">What is HRTF offload?</span></span>
<span data-ttu-id="8fda4-113">L'elaborazione di audio con algoritmi basati su HRTF richiede una grande quantità di calcoli specializzati.</span><span class="sxs-lookup"><span data-stu-id="8fda4-113">Processing audio using HRTF-based algorithms requires a large amount of specialized computation.</span></span> <span data-ttu-id="8fda4-114">HoloLens 2 include hardware dedicato che può essere utilizzato per evitare di sovraccaricare il processore di applicazioni, quindi "offload" dell'elaborazione degli algoritmi basati su HRTF.</span><span class="sxs-lookup"><span data-stu-id="8fda4-114">HoloLens 2 includes dedicated hardware that can be utilized to avoid burdening the application processor, thus "offloading" the processing of HRTF-based algorithms.</span></span>  <span data-ttu-id="8fda4-115">Il plug-in Microsoft Spatializer offre un modo semplice per consentire all'applicazione di sfruttare i vantaggi dell'hardware HRTF dedicato, in modo che l'applicazione possa usare più processori di applicazioni per operazioni diverse dall'audio spaziale.</span><span class="sxs-lookup"><span data-stu-id="8fda4-115">The Microsoft spatializer plugin provides an easy way for your application to take advantage of the dedicated HRTF hardware so your application can use more of the application processor for operations other than spatial audio.</span></span>

## <a name="objectives"></a><span data-ttu-id="8fda4-116">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="8fda4-116">Objectives</span></span>
<span data-ttu-id="8fda4-117">In questo primo capitolo, verranno illustrate le operazioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="8fda4-117">In this first chapter, you'll:</span></span>
* <span data-ttu-id="8fda4-118">Creare un progetto Unity e importare MRTK</span><span class="sxs-lookup"><span data-stu-id="8fda4-118">Create a Unity project and import MRTK</span></span>
* <span data-ttu-id="8fda4-119">Importare il plug-in Microsoft Spatializer</span><span class="sxs-lookup"><span data-stu-id="8fda4-119">Import the Microsoft spatializer plugin</span></span>
* <span data-ttu-id="8fda4-120">Abilitare il plug-in Microsoft Spatializer</span><span class="sxs-lookup"><span data-stu-id="8fda4-120">Enable the Microsoft spatializer plugin</span></span>
* <span data-ttu-id="8fda4-121">Abilitare l'audio spaziale nella workstation per sviluppatori</span><span class="sxs-lookup"><span data-stu-id="8fda4-121">Enable spatial audio on your developer workstation</span></span>

## <a name="create-a-project-and-add-nuget-for-unity"></a><span data-ttu-id="8fda4-122">Creare un progetto e aggiungere NuGet per Unity</span><span class="sxs-lookup"><span data-stu-id="8fda4-122">Create a project and add NuGet for Unity</span></span>
<span data-ttu-id="8fda4-123">Iniziare con un progetto Unity vuoto, quindi aggiungere e configurare NuGet per Unity:</span><span class="sxs-lookup"><span data-stu-id="8fda4-123">Start with an empty Unity project, then add and configure NuGet for Unity:</span></span>
1. <span data-ttu-id="8fda4-124">Scaricare la versione più recente di [NuGetForUnity. file unitypackage Tools](https://github.com/GlitchEnzo/NuGetForUnity/releases/latest)</span><span class="sxs-lookup"><span data-stu-id="8fda4-124">Download the latest [NuGetForUnity .unitypackage](https://github.com/GlitchEnzo/NuGetForUnity/releases/latest)</span></span>
2. <span data-ttu-id="8fda4-125">Nella barra dei menu di Unity fare clic su **Asset-> importa pacchetto-> pacchetto personalizzato...** e installare il pacchetto NuGetForUnity:</span><span class="sxs-lookup"><span data-stu-id="8fda4-125">In the Unity menu bar, click **Assets -> Import Package -> Custom Package...** and install the NuGetForUnity package:</span></span>

![Importa pacchetto personalizzato](images/spatial-audio/import-custom-package.png)

## <a name="add-the-windows-mixed-reality-package"></a><span data-ttu-id="8fda4-127">Aggiungere il pacchetto di realtà mista di Windows</span><span class="sxs-lookup"><span data-stu-id="8fda4-127">Add the Windows Mixed Reality package</span></span>
<span data-ttu-id="8fda4-128">Il supporto della realtà mista di Windows in Unity 2019 e versioni successive è incluso in un pacchetto facoltativo.</span><span class="sxs-lookup"><span data-stu-id="8fda4-128">Windows Mixed Reality support in Unity 2019 and later is contained in an optional package.</span></span> <span data-ttu-id="8fda4-129">Per aggiungerlo al progetto, aprire **Gestione pacchetti di > finestra** dalla barra dei menu di Unity:</span><span class="sxs-lookup"><span data-stu-id="8fda4-129">To add it to your project, open **Window -> Package Manager** from the Unity menu bar:</span></span>

![Menu di gestione pacchetti](images/spatial-audio/package-manager-menu.png)

<span data-ttu-id="8fda4-131">Individuare e installare il pacchetto di **realtà mista di Windows** :</span><span class="sxs-lookup"><span data-stu-id="8fda4-131">Then find and install the **Windows Mixed Reality** package:</span></span>

![Finestra di gestione pacchetti](images/spatial-audio/package-manager-window.png)

## <a name="install-mrtk-and-microsoft-spatializer"></a><span data-ttu-id="8fda4-133">Installare MRTK e Microsoft Spatializer</span><span class="sxs-lookup"><span data-stu-id="8fda4-133">Install MRTK and Microsoft Spatializer</span></span>
<span data-ttu-id="8fda4-134">Usando NuGet per Unity, installare i plug-in MRTK e Microsoft Spatializer:</span><span class="sxs-lookup"><span data-stu-id="8fda4-134">Using NuGet for Unity, install the MRTK and Microsoft Spatializer plugins:</span></span>
1. <span data-ttu-id="8fda4-135">Nella barra dei menu di Unity fare clic su **NuGet-> Gestisci pacchetti NuGet**.</span><span class="sxs-lookup"><span data-stu-id="8fda4-135">In the Unity menu bar, click on **NuGet -> Manage NuGet Packages**.</span></span>

![Gestisci pacchetti NuGet](images/spatial-audio/manage-nuget-packages.png)

2. <span data-ttu-id="8fda4-137">Nella casella di **ricerca** immettere "Microsoft. MixedReality. Toolkit" e installare il pacchetto MRTK Core: **Microsoft. MixedReality. Toolkit. Foundation**</span><span class="sxs-lookup"><span data-stu-id="8fda4-137">In the **Search** box, enter "Microsoft.MixedReality.Toolkit" and install the MRTK core package: **Microsoft.MixedReality.Toolkit.Foundation**</span></span>

![Pacchetto NuGet MRTK](images/spatial-audio/mrtk-nuget-package.png)

<span data-ttu-id="8fda4-139">Il [pacchetto NuGet MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MRTKNuGetPackage.html) dispone di contesto e dettagli aggiuntivi.</span><span class="sxs-lookup"><span data-stu-id="8fda4-139">[MRTK NuGet Package](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MRTKNuGetPackage.html) has additional context and details.</span></span>

4. <span data-ttu-id="8fda4-140">Nella casella di **ricerca** immettere "Microsoft. SpatialAudio" e installare il pacchetto Microsoft Spatializer: **Microsoft. SpatialAudio. Spatializer. Unity**</span><span class="sxs-lookup"><span data-stu-id="8fda4-140">In the **Search** box, enter "Microsoft.SpatialAudio" and install the Microsoft Spatializer package: **Microsoft.SpatialAudio.Spatializer.Unity**</span></span>

![Spatializer plug-in NuGet](images/spatial-audio/spatializer-plugin-nuget.png)

## <a name="set-up-mrtk-in-your-project"></a><span data-ttu-id="8fda4-142">Configurare MRTK nel progetto</span><span class="sxs-lookup"><span data-stu-id="8fda4-142">Set up MRTK in your project</span></span>

1. <span data-ttu-id="8fda4-143">Aprire la finestra impostazioni di compilazione passando a **file-> impostazioni di compilazione**.</span><span class="sxs-lookup"><span data-stu-id="8fda4-143">Open the Build Settings window by going to **File -> Build Settings**.</span></span>

2. <span data-ttu-id="8fda4-144">Selezionare il _piattaforma UWP (Universal Windows Platform)_ e fare clic su **Cambia piattaforma**.</span><span class="sxs-lookup"><span data-stu-id="8fda4-144">Select the _Universal Windows Platform_ and click **Switch Platform**.</span></span>

3. <span data-ttu-id="8fda4-145">Fare clic su **Impostazioni lettore** nella **finestra di compilazione** per aprire le proprietà **delle impostazioni del lettore** nel riquadro **controllo** .</span><span class="sxs-lookup"><span data-stu-id="8fda4-145">Click **Player Settings** in the **Build Window** to open the **Player Settings** properties in the **Inspector** pane.</span></span>
    * <span data-ttu-id="8fda4-146">In **Impostazioni XR** selezionare la casella di controllo **Virtual Reality supported**</span><span class="sxs-lookup"><span data-stu-id="8fda4-146">Under **XR Settings**, check the **Virtual Reality Supported** checkbox</span></span>
    * <span data-ttu-id="8fda4-147">In **Impostazioni XR**, modificare la **modalità di rendering stereo** in **Single Pass istanza**.</span><span class="sxs-lookup"><span data-stu-id="8fda4-147">Under **XR Settings**, change the **Stereo Rendering Mode** to **Single Pass Instanced**.</span></span>
    * <span data-ttu-id="8fda4-148">In **impostazioni di pubblicazione** selezionare la casella di controllo **percezione spaziale** nella sezione **funzionalità**</span><span class="sxs-lookup"><span data-stu-id="8fda4-148">Under **Publishing Settings**, check the **Spatial Perception** checkbox in the **Capabilities** section</span></span>

4. <span data-ttu-id="8fda4-149">Sulla barra dei menu fare clic su **Toolkit realtà mista-> Aggiungi a scena e configura..**</span><span class="sxs-lookup"><span data-stu-id="8fda4-149">On the menu bar, click **Mixed Reality Toolkit -> Add to Scene and Configure..**</span></span> <span data-ttu-id="8fda4-150">per aggiungere MRTK alla scena.</span><span class="sxs-lookup"><span data-stu-id="8fda4-150">to add MRTK to your scene.</span></span>

<span data-ttu-id="8fda4-151">Per altre istruzioni, ad esempio su come compilare l'app e distribuirla in un HoloLens 2, vedere [il capitolo 1 del modulo di base per la formazione di Mr Learning](../../../mrlearning-base-ch1.md).</span><span class="sxs-lookup"><span data-stu-id="8fda4-151">For additional guidance, including how to build your app and deploy to a HoloLens 2, see [Chapter 1 of the MR Learning Base Module](../../../mrlearning-base-ch1.md).</span></span>

## <a name="enable-the-microsoft-spatializer-plugin"></a><span data-ttu-id="8fda4-152">Abilitare il plug-in Microsoft Spatializer</span><span class="sxs-lookup"><span data-stu-id="8fda4-152">Enable the Microsoft Spatializer plugin</span></span>
<span data-ttu-id="8fda4-153">Abilitare il plug-in **Microsoft Spatializer** .</span><span class="sxs-lookup"><span data-stu-id="8fda4-153">Enable the **Microsoft Spatializer** plugin.</span></span> <span data-ttu-id="8fda4-154">Aprire **modifica-> impostazioni progetto-> audio** e modificare il **plug** -in Spatializer in "Microsoft Spatializer".</span><span class="sxs-lookup"><span data-stu-id="8fda4-154">Open **Edit -> Project Settings -> Audio**, and change **Spatializer Plugin** to "Microsoft Spatializer".</span></span> <span data-ttu-id="8fda4-155">La sezione **audio** delle **impostazioni del progetto** sarà ora simile alla seguente:</span><span class="sxs-lookup"><span data-stu-id="8fda4-155">The **Audio** section of the **Project Settings** will now look like this:</span></span>

![Impostazioni del progetto che mostrano il plug-in Spatializer](images/spatial-audio/project-settings.png)

## <a name="enable-spatial-audio-on-your-workstation"></a><span data-ttu-id="8fda4-157">Abilitare l'audio spaziale nella workstation</span><span class="sxs-lookup"><span data-stu-id="8fda4-157">Enable spatial audio on your workstation</span></span>
<span data-ttu-id="8fda4-158">Nelle versioni desktop di Windows, l'audio spaziale è disabilitato per impostazione predefinita.</span><span class="sxs-lookup"><span data-stu-id="8fda4-158">On desktop versions of Windows, spatial audio is disabled by default.</span></span> <span data-ttu-id="8fda4-159">Per abilitarla, fare clic con il pulsante destro del mouse sull'icona del volume sulla barra delle applicazioni.</span><span class="sxs-lookup"><span data-stu-id="8fda4-159">Enable it by right-clicking on the volume icon in the task bar.</span></span> <span data-ttu-id="8fda4-160">Per ottenere la migliore rappresentazione di ciò che è possibile sentire in HoloLens 2, scegliere **audio spaziale > Windows Sonic per le cuffie**.</span><span class="sxs-lookup"><span data-stu-id="8fda4-160">To get the best representation of what you'll hear on HoloLens 2, choose **Spatial sound -> Windows Sonic for Headphones**.</span></span>

![Impostazioni audio spaziali desktop](images/spatial-audio/desktop-audio-settings.png)

> [!NOTE]
> <span data-ttu-id="8fda4-162">Questa impostazione è necessaria solo se si prevede di testare il progetto nell'editor di Unity.</span><span class="sxs-lookup"><span data-stu-id="8fda4-162">This setting is only required if you plan to test your project in the Unity editor.</span></span>

## <a name="next-steps"></a><span data-ttu-id="8fda4-163">Passaggi successivi</span><span class="sxs-lookup"><span data-stu-id="8fda4-163">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="8fda4-164">Unità audio spaziale capitolo 2</span><span class="sxs-lookup"><span data-stu-id="8fda4-164">Unity spatial audio chapter 2</span></span>](unity-spatial-audio-ch2.md)


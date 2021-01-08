---
title: Aggiunta di audio spaziale al progetto
description: Aggiungere il plug-in Microsoft Spatializer al progetto Unity per accedere a HoloLens 2 HRTF hardware offload.
author: kegodin
ms.author: v-hferrone
ms.date: 12/01/2019
ms.topic: article
keywords: realtà mista, Unity, esercitazione, hololens2, audio spaziale, MRTK, Toolkit per realtà mista, UWP, Windows 10, HRTF, funzione di trasferimento relativa alla testa, Reverb, Microsoft Spatializer
ms.openlocfilehash: 80bf19e8a091bd241e28afff0a42c13ca72e1d45
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2021
ms.locfileid: "98007471"
---
# <a name="adding-spatial-audio-to-your-unity-project"></a><span data-ttu-id="78082-104">Aggiunta di audio spaziale al progetto Unity</span><span class="sxs-lookup"><span data-stu-id="78082-104">Adding spatial audio to your Unity project</span></span>

<span data-ttu-id="78082-105">Benvenuti nell'esercitazione sull'audio spaziale per Unity in HoloLens2.</span><span class="sxs-lookup"><span data-stu-id="78082-105">Welcome to the spatial audio tutorial for Unity on HoloLens2.</span></span> <span data-ttu-id="78082-106">Questa sequenza di esercitazione Mostra:</span><span class="sxs-lookup"><span data-stu-id="78082-106">This tutorial sequence shows:</span></span>
* <span data-ttu-id="78082-107">Come usare l'offload della funzione di trasferimento delle intestazioni (HRTF) in HoloLens 2 in Unity</span><span class="sxs-lookup"><span data-stu-id="78082-107">How to use head-related transfer function (HRTF) offload on HoloLens 2 in Unity</span></span>
* <span data-ttu-id="78082-108">Come abilitare il riverbero quando si usa l'offload HRTF</span><span class="sxs-lookup"><span data-stu-id="78082-108">How to enable reverb when using HRTF offload</span></span>

<span data-ttu-id="78082-109">Il [repository GitHub Microsoft Spatializer](https://github.com/microsoft/spatialaudio-unity) include un progetto Unity completato di questa sequenza di esercitazione.</span><span class="sxs-lookup"><span data-stu-id="78082-109">The [Microsoft Spatializer GitHub repository](https://github.com/microsoft/spatialaudio-unity) has a completed Unity project of this tutorial sequence.</span></span> 

<span data-ttu-id="78082-110">Per informazioni su ciò che significa spatialize i suoni usando le tecnologie di spazializzazione basate su HRTF e consigli per quando può essere utile, vedere [progettazione di suoni spaziali](https://docs.microsoft.com/windows/mixed-reality/spatial-sound-design).</span><span class="sxs-lookup"><span data-stu-id="78082-110">For an understanding about what it means to spatialize sounds using HRTF-based spatialization technologies and recommendations for when it can be helpful, see [spatial sound design](https://docs.microsoft.com/windows/mixed-reality/spatial-sound-design).</span></span>

## <a name="what-is-hrtf-offload"></a><span data-ttu-id="78082-111">Che cos'è HRTF offload?</span><span class="sxs-lookup"><span data-stu-id="78082-111">What is HRTF offload?</span></span>

<span data-ttu-id="78082-112">L'elaborazione di audio con algoritmi basati su HRTF richiede una grande quantità di calcoli specializzati.</span><span class="sxs-lookup"><span data-stu-id="78082-112">Processing audio using HRTF-based algorithms requires a large amount of specialized computation.</span></span> <span data-ttu-id="78082-113">HoloLens 2 include hardware dedicato che può essere utilizzato per evitare di sovraccaricare il processore di applicazioni, quindi "offload" dell'elaborazione degli algoritmi basati su HRTF.</span><span class="sxs-lookup"><span data-stu-id="78082-113">HoloLens 2 includes dedicated hardware that can be utilized to avoid burdening the application processor, thus "offloading" the processing of HRTF-based algorithms.</span></span>  <span data-ttu-id="78082-114">Il plug-in Microsoft Spatializer offre un modo semplice per consentire all'applicazione di sfruttare i vantaggi dell'hardware HRTF dedicato, in modo che l'applicazione possa usare più processori di applicazioni per operazioni diverse dall'audio spaziale.</span><span class="sxs-lookup"><span data-stu-id="78082-114">The Microsoft spatializer plugin provides an easy way for your application to take advantage of the dedicated HRTF hardware so your application can use more of the application processor for operations other than spatial audio.</span></span>

## <a name="objectives"></a><span data-ttu-id="78082-115">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="78082-115">Objectives</span></span>

<span data-ttu-id="78082-116">In questo primo capitolo, verranno illustrate le operazioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="78082-116">In this first chapter, you'll:</span></span>
* <span data-ttu-id="78082-117">Creare un progetto Unity e importare MRTK</span><span class="sxs-lookup"><span data-stu-id="78082-117">Create a Unity project and import MRTK</span></span>
* <span data-ttu-id="78082-118">Importare il plug-in Microsoft Spatializer</span><span class="sxs-lookup"><span data-stu-id="78082-118">Import the Microsoft spatializer plugin</span></span>
* <span data-ttu-id="78082-119">Abilitare il plug-in Microsoft Spatializer</span><span class="sxs-lookup"><span data-stu-id="78082-119">Enable the Microsoft spatializer plugin</span></span>
* <span data-ttu-id="78082-120">Abilitare l'audio spaziale nella workstation per sviluppatori</span><span class="sxs-lookup"><span data-stu-id="78082-120">Enable spatial audio on your developer workstation</span></span>

## <a name="create-a-project-and-add-nuget-for-unity"></a><span data-ttu-id="78082-121">Creare un progetto e aggiungere NuGet per Unity</span><span class="sxs-lookup"><span data-stu-id="78082-121">Create a project and add NuGet for Unity</span></span>

<span data-ttu-id="78082-122">Iniziare con un progetto Unity vuoto, quindi aggiungere e configurare NuGet per Unity:</span><span class="sxs-lookup"><span data-stu-id="78082-122">Start with an empty Unity project, then add and configure NuGet for Unity:</span></span>
1. <span data-ttu-id="78082-123">Scaricare la versione più recente di [NuGetForUnity. file unitypackage Tools](https://github.com/GlitchEnzo/NuGetForUnity/releases/latest)</span><span class="sxs-lookup"><span data-stu-id="78082-123">Download the latest [NuGetForUnity .unitypackage](https://github.com/GlitchEnzo/NuGetForUnity/releases/latest)</span></span>
2. <span data-ttu-id="78082-124">Nella barra dei menu di Unity fare clic su **Asset-> importa pacchetto-> pacchetto personalizzato...** e installare il pacchetto NuGetForUnity:</span><span class="sxs-lookup"><span data-stu-id="78082-124">In the Unity menu bar, click **Assets -> Import Package -> Custom Package...** and install the NuGetForUnity package:</span></span>

![Importa pacchetto personalizzato](images/spatial-audio/import-custom-package.png)

## <a name="add-the-windows-mixed-reality-package"></a><span data-ttu-id="78082-126">Aggiungere il pacchetto di realtà mista di Windows</span><span class="sxs-lookup"><span data-stu-id="78082-126">Add the Windows Mixed Reality package</span></span>

<span data-ttu-id="78082-127">Il supporto della realtà mista di Windows in Unity 2019 e versioni successive è incluso in un pacchetto facoltativo.</span><span class="sxs-lookup"><span data-stu-id="78082-127">Windows Mixed Reality support in Unity 2019 and later is contained in an optional package.</span></span> <span data-ttu-id="78082-128">Per aggiungerlo al progetto, aprire **Gestione pacchetti di > finestra** dalla barra dei menu di Unity:</span><span class="sxs-lookup"><span data-stu-id="78082-128">To add it to your project, open **Window -> Package Manager** from the Unity menu bar:</span></span>

![Menu di gestione pacchetti](images/spatial-audio/package-manager-menu.png)

<span data-ttu-id="78082-130">Individuare e installare il pacchetto di **realtà mista di Windows** :</span><span class="sxs-lookup"><span data-stu-id="78082-130">Then find and install the **Windows Mixed Reality** package:</span></span>

![Finestra di gestione pacchetti](images/spatial-audio/package-manager-window.png)

## <a name="install-mrtk-and-microsoft-spatializer"></a><span data-ttu-id="78082-132">Installare MRTK e Microsoft Spatializer</span><span class="sxs-lookup"><span data-stu-id="78082-132">Install MRTK and Microsoft Spatializer</span></span>

<span data-ttu-id="78082-133">Usando NuGet per Unity, installare i plug-in MRTK e Microsoft Spatializer:</span><span class="sxs-lookup"><span data-stu-id="78082-133">Using NuGet for Unity, install the MRTK and Microsoft Spatializer plugins:</span></span>
1. <span data-ttu-id="78082-134">Nella barra dei menu di Unity fare clic su **NuGet-> Gestisci pacchetti NuGet**.</span><span class="sxs-lookup"><span data-stu-id="78082-134">In the Unity menu bar, click on **NuGet -> Manage NuGet Packages**.</span></span>

![Gestisci pacchetti NuGet](images/spatial-audio/manage-nuget-packages.png)

2. <span data-ttu-id="78082-136">Nella casella di **ricerca** immettere "Microsoft. MixedReality. Toolkit" e installare il pacchetto MRTK Core: **Microsoft. MixedReality. Toolkit. Foundation**</span><span class="sxs-lookup"><span data-stu-id="78082-136">In the **Search** box, enter "Microsoft.MixedReality.Toolkit" and install the MRTK core package: **Microsoft.MixedReality.Toolkit.Foundation**</span></span>

![Pacchetto NuGet MRTK](images/spatial-audio/mrtk-nuget-package.png)

<span data-ttu-id="78082-138">Il [pacchetto NuGet MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MRTKNuGetPackage.html) dispone di contesto e dettagli aggiuntivi.</span><span class="sxs-lookup"><span data-stu-id="78082-138">[MRTK NuGet Package](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MRTKNuGetPackage.html) has additional context and details.</span></span>

4. <span data-ttu-id="78082-139">Nella casella di **ricerca** immettere "Microsoft. SpatialAudio" e installare il pacchetto Microsoft Spatializer: **Microsoft. SpatialAudio. Spatializer. Unity**</span><span class="sxs-lookup"><span data-stu-id="78082-139">In the **Search** box, enter "Microsoft.SpatialAudio" and install the Microsoft Spatializer package: **Microsoft.SpatialAudio.Spatializer.Unity**</span></span>

![Spatializer plug-in NuGet](images/spatial-audio/spatializer-plugin-nuget.png)

## <a name="set-up-mrtk-in-your-project"></a><span data-ttu-id="78082-141">Configurare MRTK nel progetto</span><span class="sxs-lookup"><span data-stu-id="78082-141">Set up MRTK in your project</span></span>

1. <span data-ttu-id="78082-142">Aprire la finestra impostazioni di compilazione passando a **file-> impostazioni di compilazione**.</span><span class="sxs-lookup"><span data-stu-id="78082-142">Open the Build Settings window by going to **File -> Build Settings**.</span></span>

2. <span data-ttu-id="78082-143">Selezionare il _piattaforma UWP (Universal Windows Platform)_ e fare clic su **Cambia piattaforma**.</span><span class="sxs-lookup"><span data-stu-id="78082-143">Select the _Universal Windows Platform_ and click **Switch Platform**.</span></span>

3. <span data-ttu-id="78082-144">Fare clic su **Impostazioni lettore** nella **finestra di compilazione** per aprire le proprietà **delle impostazioni del lettore** nel riquadro **controllo** .</span><span class="sxs-lookup"><span data-stu-id="78082-144">Click **Player Settings** in the **Build Window** to open the **Player Settings** properties in the **Inspector** pane.</span></span>
    * <span data-ttu-id="78082-145">In **Impostazioni XR** selezionare la casella di controllo **Virtual Reality supported**</span><span class="sxs-lookup"><span data-stu-id="78082-145">Under **XR Settings**, check the **Virtual Reality Supported** checkbox</span></span>
    * <span data-ttu-id="78082-146">In **Impostazioni XR**, modificare la **modalità di rendering stereo** in **Single Pass istanza**.</span><span class="sxs-lookup"><span data-stu-id="78082-146">Under **XR Settings**, change the **Stereo Rendering Mode** to **Single Pass Instanced**.</span></span>
    * <span data-ttu-id="78082-147">In **impostazioni di pubblicazione** selezionare la casella di controllo **percezione spaziale** nella sezione **funzionalità**</span><span class="sxs-lookup"><span data-stu-id="78082-147">Under **Publishing Settings**, check the **Spatial Perception** checkbox in the **Capabilities** section</span></span>

4. <span data-ttu-id="78082-148">Sulla barra dei menu fare clic su **Toolkit realtà mista-> Aggiungi a scena e configura..**</span><span class="sxs-lookup"><span data-stu-id="78082-148">On the menu bar, click **Mixed Reality Toolkit -> Add to Scene and Configure..**</span></span> <span data-ttu-id="78082-149">per aggiungere MRTK alla scena.</span><span class="sxs-lookup"><span data-stu-id="78082-149">to add MRTK to your scene.</span></span>

<span data-ttu-id="78082-150">Per altre istruzioni, ad esempio su come compilare l'app e distribuirla in un HoloLens 2, vedere [il capitolo 1 del modulo di base per la formazione di Mr Learning](../../../mrlearning-base-ch1.md).</span><span class="sxs-lookup"><span data-stu-id="78082-150">For additional guidance, including how to build your app and deploy to a HoloLens 2, see [Chapter 1 of the MR Learning Base Module](../../../mrlearning-base-ch1.md).</span></span>

## <a name="enable-the-microsoft-spatializer-plugin"></a><span data-ttu-id="78082-151">Abilitare il plug-in Microsoft Spatializer</span><span class="sxs-lookup"><span data-stu-id="78082-151">Enable the Microsoft Spatializer plugin</span></span>

<span data-ttu-id="78082-152">Abilitare il plug-in **Microsoft Spatializer** .</span><span class="sxs-lookup"><span data-stu-id="78082-152">Enable the **Microsoft Spatializer** plugin.</span></span> <span data-ttu-id="78082-153">Aprire **modifica-> impostazioni progetto-> audio** e modificare il **plug** -in Spatializer in "Microsoft Spatializer".</span><span class="sxs-lookup"><span data-stu-id="78082-153">Open **Edit -> Project Settings -> Audio**, and change **Spatializer Plugin** to "Microsoft Spatializer".</span></span> <span data-ttu-id="78082-154">La sezione **audio** delle **impostazioni del progetto** sarà ora simile alla seguente:</span><span class="sxs-lookup"><span data-stu-id="78082-154">The **Audio** section of the **Project Settings** will now look like this:</span></span>

![Impostazioni del progetto che mostrano il plug-in Spatializer](images/spatial-audio/project-settings.png)

## <a name="enable-spatial-audio-on-your-workstation"></a><span data-ttu-id="78082-156">Abilitare l'audio spaziale nella workstation</span><span class="sxs-lookup"><span data-stu-id="78082-156">Enable spatial audio on your workstation</span></span>

<span data-ttu-id="78082-157">Nelle versioni desktop di Windows, l'audio spaziale è disabilitato per impostazione predefinita.</span><span class="sxs-lookup"><span data-stu-id="78082-157">On desktop versions of Windows, spatial audio is disabled by default.</span></span> <span data-ttu-id="78082-158">Per abilitarla, fare clic con il pulsante destro del mouse sull'icona del volume sulla barra delle applicazioni.</span><span class="sxs-lookup"><span data-stu-id="78082-158">Enable it by right-clicking on the volume icon in the task bar.</span></span> <span data-ttu-id="78082-159">Per ottenere la migliore rappresentazione di ciò che è possibile sentire in HoloLens 2, scegliere **audio spaziale > Windows Sonic per le cuffie**.</span><span class="sxs-lookup"><span data-stu-id="78082-159">To get the best representation of what you'll hear on HoloLens 2, choose **Spatial sound -> Windows Sonic for Headphones**.</span></span>

![Impostazioni audio spaziali desktop](images/spatial-audio/desktop-audio-settings.png)

> [!NOTE]
> <span data-ttu-id="78082-161">Questa impostazione è necessaria solo se si prevede di testare il progetto nell'editor di Unity.</span><span class="sxs-lookup"><span data-stu-id="78082-161">This setting is only required if you plan to test your project in the Unity editor.</span></span>

## <a name="next-steps"></a><span data-ttu-id="78082-162">Passaggi successivi</span><span class="sxs-lookup"><span data-stu-id="78082-162">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="78082-163">Unità audio spaziale capitolo 2</span><span class="sxs-lookup"><span data-stu-id="78082-163">Unity spatial audio chapter 2</span></span>](unity-spatial-audio-ch2.md)


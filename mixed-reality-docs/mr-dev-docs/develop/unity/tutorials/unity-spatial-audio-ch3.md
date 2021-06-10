---
title: Esercitazioni sull'audio spaziale - 3. Spazializzazione dell'audio da un video
description: Importare un asset video nel progetto Unity e spazializzare l'audio dal video.
author: kegodin
ms.author: v-hferrone
ms.date: 02/05/2021
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens2, spatial audio, MRTK, mixed reality toolkit, UWP, Windows 10, HRTF, head-related transfer function, reverb, Microsoft Spatializer, video importing, Video Player
ms.openlocfilehash: 60b70fc3b7f49f5b39138a218f93c0b37f29b9d9
ms.sourcegitcommit: 4a6c26615d52776bdc4faab70391592092a471fc
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2021
ms.locfileid: "110712879"
---
# <a name="3-spatializing-audio-from-a-video"></a><span data-ttu-id="d259f-105">3. Spazializzazione dell'audio da un video</span><span class="sxs-lookup"><span data-stu-id="d259f-105">3. Spatializing audio from a video</span></span>

## <a name="overview"></a><span data-ttu-id="d259f-106">Panoramica</span><span class="sxs-lookup"><span data-stu-id="d259f-106">Overview</span></span>

<span data-ttu-id="d259f-107">In questa esercitazione si apprenderà come spazializzare l'audio da un'origine video e testarlo nell'editor unity e HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="d259f-107">In this tutorial, you will learn how to spatialize audio from an video source and test this in the unity editor and HoloLens 2.</span></span>

## <a name="objectives"></a><span data-ttu-id="d259f-108">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="d259f-108">Objectives</span></span>

* <span data-ttu-id="d259f-109">Importare un video e aggiungere un lettore video</span><span class="sxs-lookup"><span data-stu-id="d259f-109">Import a video and add a Video Player</span></span>
* <span data-ttu-id="d259f-110">Riprodurre il video in un quadrangolare</span><span class="sxs-lookup"><span data-stu-id="d259f-110">Play the video onto a quadrangle</span></span>
* <span data-ttu-id="d259f-111">Instradare l'audio dal video al quadrangolare e spazializzare l'audio</span><span class="sxs-lookup"><span data-stu-id="d259f-111">Route audio from the video to the quadrangle, and spatialize the audio</span></span>

## <a name="import-a-video-and-add-a-video-player-to-the-scene"></a><span data-ttu-id="d259f-112">Importare un video e aggiungere un lettore video alla scena</span><span class="sxs-lookup"><span data-stu-id="d259f-112">Import a video and add a Video Player to the Scene</span></span>

<span data-ttu-id="d259f-113">Per questa esercitazione usare È possibile usare [questo video dal progetto](https://github.com/microsoft/spatialaudio-unity/blob/develop/Samples/MicrosoftSpatializerSample/Assets/Microsoft%20HoloLens%20-%20Spatial%20Sound-PTPvx7mDon4.mp4?raw=true) di esempio di audio spaziale.</span><span class="sxs-lookup"><span data-stu-id="d259f-113">For this tutorial use You can use [this video](https://github.com/microsoft/spatialaudio-unity/blob/develop/Samples/MicrosoftSpatializerSample/Assets/Microsoft%20HoloLens%20-%20Spatial%20Sound-PTPvx7mDon4.mp4?raw=true) from the spatial audio sample project.</span></span>

<span data-ttu-id="d259f-114">Per importare Video nel progetto unity.</span><span class="sxs-lookup"><span data-stu-id="d259f-114">To import Video into the unity project.</span></span> <span data-ttu-id="d259f-115">Nel menu Unity selezionare **Asset**  >  **Import New Asset Importing** 
 ![ Asset](images/spatial-audio/spatial-audio-03-section1-step1-1.PNG)</span><span class="sxs-lookup"><span data-stu-id="d259f-115">in the Unity menu select **Asset** > **Import New Asset**
![Importing Asset](images/spatial-audio/spatial-audio-03-section1-step1-1.PNG)</span></span>

<span data-ttu-id="d259f-116">Nella finestra **Importa nuovo** asset selezionare il file **Microsoft HoloLens - Spatial Sound-PTPvx7mDon4** scaricato e fare clic sul pulsante Apri per importare l'asset nel progetto: </span><span class="sxs-lookup"><span data-stu-id="d259f-116">In the **Import New Asset...** window, select the **Microsoft HoloLens - Spatial Sound-PTPvx7mDon4** file you downloaded and click the **Open** button to import the asset into the project:</span></span>

![Selezione dell'asset](images/spatial-audio/spatial-audio-03-section1-step1-2.PNG)

<span data-ttu-id="d259f-118">La regolazione delle impostazioni di qualità nel clip video può garantire una riproduzione uniforme HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="d259f-118">Adjusting the quality settings on the video clip can ensure smooth playback on HoloLens 2.</span></span> <span data-ttu-id="d259f-119">Selezionare il file video nella finestra **Progetto** e nella finestra Controllo del file video eseguire **l'override** delle impostazioni per Le **app di Windows Store** e:</span><span class="sxs-lookup"><span data-stu-id="d259f-119">Select the video file in the **Project** window and in the Inspector window of the video file, **override** the settings for **Windows Store Apps**, and:</span></span>

* <span data-ttu-id="d259f-120">Abilita **transcodifica**</span><span class="sxs-lookup"><span data-stu-id="d259f-120">Enable **Transcode**</span></span>
* <span data-ttu-id="d259f-121">Impostare **Codec** su H264</span><span class="sxs-lookup"><span data-stu-id="d259f-121">Set **Codec** to H264</span></span>
* <span data-ttu-id="d259f-122">Impostare **La modalità a velocità in bit** su Bassa</span><span class="sxs-lookup"><span data-stu-id="d259f-122">Set **Bitrate Mode** to Low</span></span>
* <span data-ttu-id="d259f-123">Impostare **Qualità spaziale su** Media Qualità spaziale</span><span class="sxs-lookup"><span data-stu-id="d259f-123">Set **Spatial Quality** to Medium Spatial Quality</span></span>

<span data-ttu-id="d259f-124">Dopo queste modifiche, fare clic su Applica per modificare l'impostazione della qualità nel clip video.</span><span class="sxs-lookup"><span data-stu-id="d259f-124">After these adjustments, click on Apply to change the quality setting on the video clip.</span></span>

![Modifica della proprietà video](images/spatial-audio/spatial-audio-03-section1-step1-3.PNG)

<span data-ttu-id="d259f-126">Fare clic con il pulsante destro del mouse su Hierarchy **(Gerarchia),** selezionare  >  **Video Video Player (Lettore video video)** per aggiungere il componente Lettore video.</span><span class="sxs-lookup"><span data-stu-id="d259f-126">Right click on the Hierarchy, Select **Video** > **Video Player** to add Video player component.</span></span>

![Aggiungere un lettore video](images/spatial-audio/spatial-audio-03-section1-step1-4.PNG)

## <a name="play-video-onto-a-quadrangle"></a><span data-ttu-id="d259f-128">Riprodurre video in un quadrangolare</span><span class="sxs-lookup"><span data-stu-id="d259f-128">Play video onto a quadrangle</span></span>

<span data-ttu-id="d259f-129">Per **eseguire il rendering del** video, l'oggetto Lettore video richiede un oggetto gioco con trama.</span><span class="sxs-lookup"><span data-stu-id="d259f-129">The **Video Player** object needs a textured game object to render the video.</span></span>

<span data-ttu-id="d259f-130">Fare clic con il pulsante destro del mouse su Hierarchy (Gerarchia), selezionare 3D Object Quad (Quad oggetto **3D)** per  >   creare un quad e configurare il relativo **componente Transform** (Trasforma) come indicato di seguito:</span><span class="sxs-lookup"><span data-stu-id="d259f-130">Right click the Hierarchy , Select **3D Object** > **Quad** to create a quad and configure its **Transform** component as follows:</span></span>

* <span data-ttu-id="d259f-131">**Posizione:** X = 0, Y = 0, Z = 2</span><span class="sxs-lookup"><span data-stu-id="d259f-131">**Position**: X = 0, Y = 0, Z = 2</span></span>
* <span data-ttu-id="d259f-132">**Rotation** (Rotazione): X = 0, Y = 0, Z = 0</span><span class="sxs-lookup"><span data-stu-id="d259f-132">**Rotation**: X = 0, Y = 0, Z = 0</span></span>
* <span data-ttu-id="d259f-133">**Scala:** X = 1,28, Y = 0,72, Z = 1</span><span class="sxs-lookup"><span data-stu-id="d259f-133">**Scale**: X = 1.28, Y = 0.72, Z = 1</span></span>

![Aggiungere un quad](images/spatial-audio/spatial-audio-03-section2-step1-1.PNG)

<span data-ttu-id="d259f-135">A questo punto è necessario trameare  il **quad** con il video. Nella finestra Progetto fare clic con il pulsante destro del mouse e scegliere Crea trama di rendering per creare un componente Trama di rendering, immettere un nome appropriato per la trama di rendering, ad esempio  >   Trama _audio_ spaziale:</span><span class="sxs-lookup"><span data-stu-id="d259f-135">Now you need to texture the **Quad** with the video, In the **Project** window, right-click and choose **Create** > **Render Texture** to create a Render Texture component, enter a suitable name to the Render Texture for example, _Spatial Audio Texture_:</span></span>

![Creare una trama di rendering](images/spatial-audio/spatial-audio-03-section2-step1-2.PNG)

<span data-ttu-id="d259f-137">Selezionare Trama **di rendering** e nella finestra Controllo impostare la proprietà **Dimensioni** in modo che corrisponda alla risoluzione nativa del video di 1280x720.</span><span class="sxs-lookup"><span data-stu-id="d259f-137">Select the **Render Texture** and in the Inspector window set the **Size** property to match the video's native resolution of 1280x720.</span></span> <span data-ttu-id="d259f-138">Quindi, per garantire prestazioni di rendering ottimali HoloLens 2, impostare la proprietà **Depth Buffer** su **Almeno 16 bit di profondità.**</span><span class="sxs-lookup"><span data-stu-id="d259f-138">Then, to ensure good rendering performance on HoloLens 2, set the **Depth Buffer** property to **At least 16 bits depth**.</span></span>

![Proprietà trama di rendering](images/spatial-audio/spatial-audio-03-section2-step1-3.PNG)

<span data-ttu-id="d259f-140">Usare quindi render texture **spatial audio texture (Trama audio spaziale** di rendering) creata come trama per il **quad**:</span><span class="sxs-lookup"><span data-stu-id="d259f-140">Next, use the created Render Texture **Spatial Audio Texture** as the texture for the **Quad**:</span></span>

1. <span data-ttu-id="d259f-141">Trascinare **la trama audio** spaziale dalla finestra **Progetto** al **quad** nella gerarchia per aggiungere la trama di rendering al quad</span><span class="sxs-lookup"><span data-stu-id="d259f-141">Drag the **Spatial Audio Texture** from the **Project** window onto the **Quad** in the Hierarchy to add the Render Texture to the Quad</span></span>
2. <span data-ttu-id="d259f-142">Per garantire prestazioni ottimali nel HoloLens 2, selezionare Quad nella gerarchia e nella finestra Inspector (Controllo) per lo shader selezionare **Mixed Reality Toolkit** Standard Shader (Shader standard di Mixed Reality  >   Toolkit).</span><span class="sxs-lookup"><span data-stu-id="d259f-142">To ensure good performance on HoloLens 2, select Quad in the Hierarchy and in the Inspector window for shader select the **Mixed Reality Toolkit** > **Standard** Shader.</span></span>

![Proprietà trama quadrupla](images/spatial-audio/spatial-audio-03-section2-step1-4.PNG)

<span data-ttu-id="d259f-144">Per impostare **Lettore video e** **Trama di** rendering per  riprodurre il video clip, selezionare il lettore **video** nella gerarchia e nella finestra **Inspector (Controllo).**</span><span class="sxs-lookup"><span data-stu-id="d259f-144">To set **Video Player** and **Render Texture** to play the video clip, select the **Video Player** in the **Hierarchy** and in the **Inspector** window,</span></span>

* <span data-ttu-id="d259f-145">Impostare la **proprietà Clip video** sul file video scaricato 'Microsoft HoloLens - Spatial Sound-PTPvx7mDon4'</span><span class="sxs-lookup"><span data-stu-id="d259f-145">Set the **Video Clip** property to the downloaded video file 'Microsoft HoloLens - Spatial Sound-PTPvx7mDon4'</span></span>
* <span data-ttu-id="d259f-146">Selezionare la **casella di controllo** Ciclo</span><span class="sxs-lookup"><span data-stu-id="d259f-146">Check the **Loop** checkbox</span></span>
* <span data-ttu-id="d259f-147">Impostare **Trama di destinazione** sulla nuova trama di rendering Trama audio **spaziale**</span><span class="sxs-lookup"><span data-stu-id="d259f-147">Set **Target Texture** to your new render texture **Spatial Audio Texture**</span></span>

![Proprietà del lettore video](images/spatial-audio/spatial-audio-03-section2-step1-5.PNG)

## <a name="spatialize-the-audio-from-the-video"></a><span data-ttu-id="d259f-149">Spazializzare l'audio dal video</span><span class="sxs-lookup"><span data-stu-id="d259f-149">Spatialize the audio from the video</span></span>

<span data-ttu-id="d259f-150">Nella finestra Hierarchy (Gerarchia) selezionare **Quad** object (Oggetto Quad), quindi nella finestra Inspector (Controllo) usare il pulsante **Add Component** (Aggiungi componente) per aggiungere **l'origine audio** a cui instradare l'audio dal video.</span><span class="sxs-lookup"><span data-stu-id="d259f-150">In the Hierarchy window, select **Quad** object, then in the Inspector window, use the **Add Component** button to add **Audio Source** to which you'll route the audio from the video.</span></span>

<span data-ttu-id="d259f-151">In **Origine audio**:</span><span class="sxs-lookup"><span data-stu-id="d259f-151">In the **Audio Source**:</span></span>

* <span data-ttu-id="d259f-152">Impostare **Output** sul **mixer audio spaziale**</span><span class="sxs-lookup"><span data-stu-id="d259f-152">Set **Output** to the **Spatial Audio Mixer**</span></span>
* <span data-ttu-id="d259f-153">Selezionare la **casella Spazializza**</span><span class="sxs-lookup"><span data-stu-id="d259f-153">Check the **Spatialize** box</span></span>
* <span data-ttu-id="d259f-154">Spostare il **dispositivo di scorrimento Fusione** spaziale su 1 (3D)</span><span class="sxs-lookup"><span data-stu-id="d259f-154">Move the **Spatial Blend** slider to 1 (3D)</span></span>

![Controllo origine audio quad](images/spatial-audio/spatial-audio-03-section3-step1-1.PNG)

<span data-ttu-id="d259f-156">Per impostare il lettore video in modo che instradare l'audio all'origine **audio,** selezionare Il lettore **video** nella finestra Gerarchia e in Lettore video in Controllo apportare le modifiche seguenti.</span><span class="sxs-lookup"><span data-stu-id="d259f-156">To set the Video Player to route its audio to the **Audio Source**, select the **Video Player** In the Hierarchy window, and in Video Player object in the Inspector do the following changes.</span></span>

* <span data-ttu-id="d259f-157">Impostare la **modalità di output audio** su Origine **audio**</span><span class="sxs-lookup"><span data-stu-id="d259f-157">Set the **Audio Output Mode** to **Audio Source**</span></span>
* <span data-ttu-id="d259f-158">Impostare la **proprietà Origine** audio sul **quad**</span><span class="sxs-lookup"><span data-stu-id="d259f-158">Set the **Audio Source** property to the **Quad**</span></span>

![Origine audio del set di lettore video](images/spatial-audio/spatial-audio-03-section3-step1-2.PNG)

> [!TIP]
> <span data-ttu-id="d259f-160">Per rivedere la procedura di compilazione e distribuzione di un progetto Unity in HoloLens 2, fare riferimento alle istruzioni riportate in [Compilazione dell'app nel dispositivo HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2).</span><span class="sxs-lookup"><span data-stu-id="d259f-160">For a reminder on how to build and deploy your Unity project to HoloLens 2, you can refer to the [Building your app to your HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions.</span></span>

## <a name="congratulations"></a><span data-ttu-id="d259f-161">Lezione completata</span><span class="sxs-lookup"><span data-stu-id="d259f-161">Congratulations</span></span>

<span data-ttu-id="d259f-162">In questa esercitazione si è appreso come spazializzare l'audio da un'origine video Provare l'app in un HoloLens 2 o nell'editor di Unity.</span><span class="sxs-lookup"><span data-stu-id="d259f-162">In this tutorial, you have learned how to spatialize audio from an video source Try out your app on a HoloLens 2 or in the Unity editor.</span></span> <span data-ttu-id="d259f-163">Il video verrà visualizzato e sentito e l'audio del video verrà spazializzato.</span><span class="sxs-lookup"><span data-stu-id="d259f-163">You'll see and hear the video, and the audio from the video is spatialized.</span></span>

<span data-ttu-id="d259f-164">Nell'esercitazione successiva si apprenderà come abilitare e disabilitare la spazializzazione in fase di esecuzione</span><span class="sxs-lookup"><span data-stu-id="d259f-164">In the next tutorial you will learn how to Enable and disable spatialization at run time</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="d259f-165">Esercitazione successiva: 4. Abilitazione e disabilitazione della spazializzazione in fase di esecuzione</span><span class="sxs-lookup"><span data-stu-id="d259f-165">Next Tutorial: 4. Enabling and disabling spatialization at run time</span></span>](unity-spatial-audio-ch4.md)

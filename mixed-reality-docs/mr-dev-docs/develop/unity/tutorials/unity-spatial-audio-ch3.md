---
title: Esercitazioni audio spaziali-3. Spazializzazione dell'audio da un video
description: Importare un asset video nel progetto Unity e spatialize l'audio dal video.
author: kegodin
ms.author: v-hferrone
ms.date: 02/05/2021
ms.topic: article
keywords: realtà mista, Unity, esercitazione, hololens2, audio spaziale, MRTK, Toolkit per realtà mista, UWP, Windows 10, HRTF, funzione di trasferimento relativa alla testa, Reverb, Microsoft Spatializer, importazione video, lettore video
ms.openlocfilehash: 876918c3e886fae6cd2066d84c55a6e158e4c773
ms.sourcegitcommit: 68140e9ce84e69a99c2b3d970c7b8f2927a7fc93
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/05/2021
ms.locfileid: "99590053"
---
# <a name="3-spatializing-audio-from-a-video"></a><span data-ttu-id="67298-105">3. Spazializzazione dell'audio da un video</span><span class="sxs-lookup"><span data-stu-id="67298-105">3. Spatializing audio from a video</span></span>

## <a name="overview"></a><span data-ttu-id="67298-106">Panoramica</span><span class="sxs-lookup"><span data-stu-id="67298-106">Overview</span></span>

<span data-ttu-id="67298-107">In questa esercitazione si apprenderà come spatialize audio da un'origine video e come testarlo nell'editor di Unity e in HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="67298-107">In this tutorial, you will learn how to spatialize audio from an video source and test this in the unity editor and HoloLens 2.</span></span>

## <a name="objectives"></a><span data-ttu-id="67298-108">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="67298-108">Objectives</span></span>

* <span data-ttu-id="67298-109">Importare un video e aggiungere un lettore video</span><span class="sxs-lookup"><span data-stu-id="67298-109">Import a video and add a Video Player</span></span>
* <span data-ttu-id="67298-110">Riprodurre il video su un quadrilatero</span><span class="sxs-lookup"><span data-stu-id="67298-110">Play the video onto a quadrangle</span></span>
* <span data-ttu-id="67298-111">Indirizzare l'audio dal video al quadrilatero e spatialize l'audio</span><span class="sxs-lookup"><span data-stu-id="67298-111">Route audio from the video to the quadrangle, and spatialize the audio</span></span>

## <a name="import-a-video-and-add-a-video-player-to-the-scene"></a><span data-ttu-id="67298-112">Importa un video e Aggiungi un lettore video alla scena</span><span class="sxs-lookup"><span data-stu-id="67298-112">Import a video and add a Video Player to the Scene</span></span>

<span data-ttu-id="67298-113">Per questa esercitazione è possibile usare [questo video](https://github.com/microsoft/spatialaudio-unity/blob/develop/Samples/MicrosoftSpatializerSample/Assets/Microsoft%20HoloLens%20-%20Spatial%20Sound-PTPvx7mDon4.mp4?raw=true) dal progetto di esempio di audio spaziale.</span><span class="sxs-lookup"><span data-stu-id="67298-113">For this tutorial use You can use [this video](https://github.com/microsoft/spatialaudio-unity/blob/develop/Samples/MicrosoftSpatializerSample/Assets/Microsoft%20HoloLens%20-%20Spatial%20Sound-PTPvx7mDon4.mp4?raw=true) from the spatial audio sample project.</span></span>

<span data-ttu-id="67298-114">Per importare video nel progetto Unity.</span><span class="sxs-lookup"><span data-stu-id="67298-114">To import Video into the unity project.</span></span> <span data-ttu-id="67298-115">nel menu di Unity selezionare **Asset**  >  **Importa nuovo** asset 
 ![ importazione asset](images/spatial-audio/spatial-audio-03-section1-step1-1.png)</span><span class="sxs-lookup"><span data-stu-id="67298-115">in the Unity menu select **Asset** > **Import New Asset**
![Importing Asset](images/spatial-audio/spatial-audio-03-section1-step1-1.png)</span></span>

<span data-ttu-id="67298-116">Nella finestra **Importa nuovo asset...** selezionare il file **Microsoft HoloLens-Spatial Sound-PTPvx7mDon4** scaricato e fare clic sul pulsante **Apri** per importare l'asset nel progetto:</span><span class="sxs-lookup"><span data-stu-id="67298-116">In the **Import New Asset...** window, select the **Microsoft HoloLens - Spatial Sound-PTPvx7mDon4** file you downloaded and click the **Open** button to import the asset into the project:</span></span>

![Selezione asset](images/spatial-audio/spatial-audio-03-section1-step1-2.png)

<span data-ttu-id="67298-118">La regolazione delle impostazioni di qualità nel clip video può garantire la riproduzione uniforme in HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="67298-118">Adjusting the quality settings on the video clip can ensure smooth playback on HoloLens 2.</span></span> <span data-ttu-id="67298-119">Selezionare il file video nella finestra del **progetto** e nella finestra di controllo del file video, **sostituire** le impostazioni per le **app di Windows Store** e:</span><span class="sxs-lookup"><span data-stu-id="67298-119">Select the video file in the **Project** window and in the Inspector window of the video file, **override** the settings for **Windows Store Apps**, and:</span></span>

* <span data-ttu-id="67298-120">Abilita **transcodifica**</span><span class="sxs-lookup"><span data-stu-id="67298-120">Enable **Transcode**</span></span>
* <span data-ttu-id="67298-121">Imposta **codec** su H264</span><span class="sxs-lookup"><span data-stu-id="67298-121">Set **Codec** to H264</span></span>
* <span data-ttu-id="67298-122">Impostare la **Modalità bitrate** su low</span><span class="sxs-lookup"><span data-stu-id="67298-122">Set **Bitrate Mode** to Low</span></span>
* <span data-ttu-id="67298-123">Impostare la **qualità spaziale** su una qualità media spaziale</span><span class="sxs-lookup"><span data-stu-id="67298-123">Set **Spatial Quality** to Medium Spatial Quality</span></span>

<span data-ttu-id="67298-124">Dopo queste modifiche, fare clic su Applica per modificare l'impostazione qualità nel clip video.</span><span class="sxs-lookup"><span data-stu-id="67298-124">After these adjustments, click on Apply to change the quality setting on the video clip.</span></span>

![Modifica proprietà video](images/spatial-audio/spatial-audio-03-section1-step1-3.png)

<span data-ttu-id="67298-126">Fare clic con il pulsante destro del mouse sulla gerarchia e selezionare **video**  >  **video player** per aggiungere il componente lettore video.</span><span class="sxs-lookup"><span data-stu-id="67298-126">Right click on the Hierarchy, Select **Video** > **Video Player** to add Video player component.</span></span>

![Aggiungi lettore video](images/spatial-audio/spatial-audio-03-section1-step1-4.png)

## <a name="play-video-onto-a-quadrangle"></a><span data-ttu-id="67298-128">Riprodurre video su un quadrilatero</span><span class="sxs-lookup"><span data-stu-id="67298-128">Play video onto a quadrangle</span></span>

<span data-ttu-id="67298-129">L'oggetto **Player video** necessita di un oggetto gioco con trama per il rendering del video.</span><span class="sxs-lookup"><span data-stu-id="67298-129">The **Video Player** object needs a textured game object to render the video.</span></span>

<span data-ttu-id="67298-130">Fare clic con il pulsante destro del mouse sulla gerarchia, selezionare **oggetto 3D**  >  **Quad** per creare un quad e configurarne il componente **Transform** come indicato di seguito:</span><span class="sxs-lookup"><span data-stu-id="67298-130">Right click the Hierarchy , Select **3D Object** > **Quad** to create a quad and configure its **Transform** component as follows:</span></span>

* <span data-ttu-id="67298-131">**Posizione**: X = 0, Y = 0, Z = 2</span><span class="sxs-lookup"><span data-stu-id="67298-131">**Position**: X = 0, Y = 0, Z = 2</span></span>
* <span data-ttu-id="67298-132">**Rotation** (Rotazione): X = 0, Y = 0, Z = 0</span><span class="sxs-lookup"><span data-stu-id="67298-132">**Rotation**: X = 0, Y = 0, Z = 0</span></span>
* <span data-ttu-id="67298-133">**Scala**: X = 1,28, Y = 0,72, Z = 1</span><span class="sxs-lookup"><span data-stu-id="67298-133">**Scale**: X = 1.28, Y = 0.72, Z = 1</span></span>

![Aggiungere un quad](images/spatial-audio/spatial-audio-03-section2-step1-1.png)

<span data-ttu-id="67298-135">A questo punto è necessario creare una trama del **Quad** con il video, nella finestra del **progetto** , fare clic con il pulsante destro del mouse e scegliere **Crea**  >  **trama di rendering** per creare un componente di trama di rendering, immettere un nome appropriato per la trama di rendering, ad esempio, _trama audio spaziale_:</span><span class="sxs-lookup"><span data-stu-id="67298-135">Now you need to texture the **Quad** with the video, In the **Project** window, right-click and choose **Create** > **Render Texture** to create a Render Texture component, enter a suitable name to the Render Texture for example, _Spatial Audio Texture_:</span></span>

![Crea trama di rendering](images/spatial-audio/spatial-audio-03-section2-step1-2.png)

<span data-ttu-id="67298-137">Selezionare la **trama di rendering** e nella finestra di controllo impostare la proprietà **dimensioni** in modo che corrisponda alla risoluzione nativa del video 1280x720.</span><span class="sxs-lookup"><span data-stu-id="67298-137">Select the **Render Texture** and in the Inspector window set the **Size** property to match the video's native resolution of 1280x720.</span></span> <span data-ttu-id="67298-138">Quindi, per garantire prestazioni di rendering ottimali in HoloLens 2, impostare la proprietà **depth buffer** su almeno **16 bit di profondità**.</span><span class="sxs-lookup"><span data-stu-id="67298-138">Then, to ensure good rendering performance on HoloLens 2, set the **Depth Buffer** property to **At least 16 bits depth**.</span></span>

![Proprietà trama di rendering](images/spatial-audio/spatial-audio-03-section2-step1-3.png)

<span data-ttu-id="67298-140">Successivamente, usare la trama dell' **audio spaziale** di rendering creata come trama per il **Quad**:</span><span class="sxs-lookup"><span data-stu-id="67298-140">Next, use the created Render Texture **Spatial Audio Texture** as the texture for the **Quad**:</span></span>

1. <span data-ttu-id="67298-141">Trascinare la **trama audio spaziale** dalla finestra del **progetto** nel **Quad** della gerarchia per aggiungere la trama di rendering al quad</span><span class="sxs-lookup"><span data-stu-id="67298-141">Drag the **Spatial Audio Texture** from the **Project** window onto the **Quad** in the Hierarchy to add the Render Texture to the Quad</span></span>
2. <span data-ttu-id="67298-142">Per garantire prestazioni ottimali in HoloLens 2, selezionare quad nella gerarchia e nella finestra di controllo per shader selezionare lo shader standard di **mixed reality Toolkit**  >   .</span><span class="sxs-lookup"><span data-stu-id="67298-142">To ensure good performance on HoloLens 2, select Quad in the Hierarchy and in the Inspector window for shader select the **Mixed Reality Toolkit** > **Standard** Shader.</span></span>

![Proprietà trama quad](images/spatial-audio/spatial-audio-03-section2-step1-4.png)

<span data-ttu-id="67298-144">Per impostare il **lettore video** e la **trama di rendering** per riprodurre il clip video, selezionare il **lettore video** nella **gerarchia** e nella finestra di **controllo** ,</span><span class="sxs-lookup"><span data-stu-id="67298-144">To set **Video Player** and **Render Texture** to play the video clip, select the **Video Player** in the **Hierarchy** and in the **Inspector** window,</span></span>

* <span data-ttu-id="67298-145">Impostare la proprietà **video clip** sul file video scaricato ' Microsoft HoloLens-Spatial Sound-PTPvx7mDon4'</span><span class="sxs-lookup"><span data-stu-id="67298-145">Set the **Video Clip** property to the downloaded video file 'Microsoft HoloLens - Spatial Sound-PTPvx7mDon4'</span></span>
* <span data-ttu-id="67298-146">Casella di controllo **ciclo**</span><span class="sxs-lookup"><span data-stu-id="67298-146">Check the **Loop** checkbox</span></span>
* <span data-ttu-id="67298-147">Imposta la **trama di destinazione** sulla nuova trama dell' **audio spaziale** della trama di rendering</span><span class="sxs-lookup"><span data-stu-id="67298-147">Set **Target Texture** to your new render texture **Spatial Audio Texture**</span></span>

![Proprietà lettore video](images/spatial-audio/spatial-audio-03-section2-step1-5.png)

## <a name="spatialize-the-audio-from-the-video"></a><span data-ttu-id="67298-149">Spatialize l'audio dal video</span><span class="sxs-lookup"><span data-stu-id="67298-149">Spatialize the audio from the video</span></span>

<span data-ttu-id="67298-150">Nella finestra gerarchia selezionare oggetto **Quad** , quindi nella finestra di controllo usare il pulsante **Aggiungi componente** per aggiungere l' **origine audio** a cui indirizzare l'audio dal video.</span><span class="sxs-lookup"><span data-stu-id="67298-150">In the Hierarchy window, select **Quad** object, then in the Inspector window, use the **Add Component** button to add **Audio Source** to which you'll route the audio from the video.</span></span>

<span data-ttu-id="67298-151">Nell' **origine audio**:</span><span class="sxs-lookup"><span data-stu-id="67298-151">In the **Audio Source**:</span></span>

* <span data-ttu-id="67298-152">Imposta **output** sul **mixer audio spaziale**</span><span class="sxs-lookup"><span data-stu-id="67298-152">Set **Output** to the **Spatial Audio Mixer**</span></span>
* <span data-ttu-id="67298-153">Controllare la casella **Spatialize**</span><span class="sxs-lookup"><span data-stu-id="67298-153">Check the **Spatialize** box</span></span>
* <span data-ttu-id="67298-154">Spostare il dispositivo di scorrimento di **Blend spaziale** su 1 (3D)</span><span class="sxs-lookup"><span data-stu-id="67298-154">Move the **Spatial Blend** slider to 1 (3D)</span></span>

![Controllo origine audio quad](images/spatial-audio/spatial-audio-03-section3-step1-1.png)

<span data-ttu-id="67298-156">Per impostare il lettore video in modo da instradare l'audio all' **origine audio**, selezionare il **lettore video** nella finestra gerarchia e nell'oggetto video player del controllo eseguire le modifiche seguenti.</span><span class="sxs-lookup"><span data-stu-id="67298-156">To set the Video Player to route its audio to the **Audio Source**, select the **Video Player** In the Hierarchy window, and in Video Player object in the Inspector do the following changes.</span></span>

* <span data-ttu-id="67298-157">Impostare la **modalità di output audio** su **origine audio**</span><span class="sxs-lookup"><span data-stu-id="67298-157">Set the **Audio Output Mode** to **Audio Source**</span></span>
* <span data-ttu-id="67298-158">Impostare la proprietà di **origine audio** sul **Quad**</span><span class="sxs-lookup"><span data-stu-id="67298-158">Set the **Audio Source** property to the **Quad**</span></span>

![Origine audio del set di lettori video](images/spatial-audio/spatial-audio-03-section3-step1-2.png)

> [!TIP]
> <span data-ttu-id="67298-160">Per rivedere la procedura di compilazione e distribuzione di un progetto Unity in HoloLens 2, fare riferimento alle istruzioni riportate in [Compilazione dell'app nel dispositivo HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2).</span><span class="sxs-lookup"><span data-stu-id="67298-160">For a reminder on how to build and deploy your Unity project to HoloLens 2, you can refer to the [Building your app to your HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions.</span></span>

## <a name="congratulations"></a><span data-ttu-id="67298-161">Lezione completata</span><span class="sxs-lookup"><span data-stu-id="67298-161">Congratulations</span></span>

<span data-ttu-id="67298-162">In questa esercitazione si è appreso come spatialize audio da un'origine video provare l'app in un HoloLens 2 o nell'editor di Unity.</span><span class="sxs-lookup"><span data-stu-id="67298-162">In this tutorial, you have learned how to spatialize audio from an video source Try out your app on a HoloLens 2 or in the Unity editor.</span></span> <span data-ttu-id="67298-163">Il video viene visualizzato e l'audio del video è spaziale.</span><span class="sxs-lookup"><span data-stu-id="67298-163">You'll see and hear the video, and the audio from the video is spatialized.</span></span>

<span data-ttu-id="67298-164">Nell'esercitazione successiva si apprenderà come abilitare e disabilitare la spazializzazione in fase di esecuzione</span><span class="sxs-lookup"><span data-stu-id="67298-164">In the next tutorial you will learn how to Enable and disable spatialization at run time</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="67298-165">Esercitazione successiva: 4. Abilitazione e disabilitazione della spazializzazione in fase di esecuzione</span><span class="sxs-lookup"><span data-stu-id="67298-165">Next Tutorial: 4. Enabling and disabling spatialization at run time</span></span>](unity-spatial-audio-ch4.md)

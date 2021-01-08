---
title: Spazializzazione dell'audio da un video
description: Informazioni su come importare un asset video nel progetto di realtà mista Unity e spatialize l'audio dal video.
author: kegodin
ms.author: v-hferrone
ms.date: 12/01/2019
ms.topic: article
keywords: realtà mista, Unity, esercitazione, hololens2, audio spaziale, MRTK, Toolkit per realtà mista, UWP, Windows 10, HRTF, funzione di trasferimento relativa alla testa, Reverb, Microsoft Spatializer, importazione video, lettore video
ms.openlocfilehash: 211d1e32a8137444d0f33d442a60067dcd77ca36
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2021
ms.locfileid: "98007412"
---
# <a name="spatializing-audio-from-a-video"></a><span data-ttu-id="2ee52-104">Spazializzazione dell'audio da un video</span><span class="sxs-lookup"><span data-stu-id="2ee52-104">Spatializing audio from a video</span></span>

<span data-ttu-id="2ee52-105">In questo terzo capitolo del modulo audio spaziale delle esercitazioni di HoloLens 2 Unity è possibile:</span><span class="sxs-lookup"><span data-stu-id="2ee52-105">In this 3rd chapter of the spatial audio module of the HoloLens 2 Unity tutorials, you'll:</span></span>
* <span data-ttu-id="2ee52-106">Importare un video e aggiungere un lettore video</span><span class="sxs-lookup"><span data-stu-id="2ee52-106">Import a video and add a Video Player</span></span>
* <span data-ttu-id="2ee52-107">Riprodurre il video su un quadrilatero</span><span class="sxs-lookup"><span data-stu-id="2ee52-107">Play the video onto a quadrangle</span></span>
* <span data-ttu-id="2ee52-108">Indirizzare l'audio dal video al quadrilatero e spatialize l'audio</span><span class="sxs-lookup"><span data-stu-id="2ee52-108">Route audio from the video to the quadrangle, and spatialize the audio</span></span>

## <a name="import-a-video-and-add-a-video-player"></a><span data-ttu-id="2ee52-109">Importare un video e aggiungere un lettore video</span><span class="sxs-lookup"><span data-stu-id="2ee52-109">Import a video and add a Video Player</span></span>

<span data-ttu-id="2ee52-110">Trascinare un file video nel riquadro **progetto** del progetto Unity.</span><span class="sxs-lookup"><span data-stu-id="2ee52-110">Drag a video file into the **Project** pane in your Unity project.</span></span> <span data-ttu-id="2ee52-111">È possibile utilizzare [questo video](https://github.com/microsoft/spatialaudio-unity/blob/develop/Samples/MicrosoftSpatializerSample/Assets/Microsoft%20HoloLens%20-%20Spatial%20Sound-PTPvx7mDon4.mp4?raw=true) dal progetto di esempio di audio spaziale.</span><span class="sxs-lookup"><span data-stu-id="2ee52-111">You can use [this video](https://github.com/microsoft/spatialaudio-unity/blob/develop/Samples/MicrosoftSpatializerSample/Assets/Microsoft%20HoloLens%20-%20Spatial%20Sound-PTPvx7mDon4.mp4?raw=true) from the spatial audio sample project.</span></span>

![Cartella asset con video](images/spatial-audio/assets-folder-with-video.png)

<span data-ttu-id="2ee52-113">La regolazione delle impostazioni di qualità nel clip video può garantire la riproduzione uniforme in HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="2ee52-113">Adjusting the quality settings on the video clip can ensure smooth playback on HoloLens 2.</span></span> <span data-ttu-id="2ee52-114">Fare clic sul file video nel riquadro **progetto** .</span><span class="sxs-lookup"><span data-stu-id="2ee52-114">Click on the video file in the **Project** pane.</span></span> <span data-ttu-id="2ee52-115">Quindi, nel riquadro **Inspector** per il file video, sostituire le impostazioni per le app di Windows Store e:</span><span class="sxs-lookup"><span data-stu-id="2ee52-115">Then in the **Inspector** pane for the video file, override the settings for Windows Store Apps, and:</span></span>
* <span data-ttu-id="2ee52-116">Abilita **transcodifica**</span><span class="sxs-lookup"><span data-stu-id="2ee52-116">Enable **Transcode**</span></span>
* <span data-ttu-id="2ee52-117">Imposta **codec** su H264</span><span class="sxs-lookup"><span data-stu-id="2ee52-117">Set **Codec** to H264</span></span>
* <span data-ttu-id="2ee52-118">Impostare la **Modalità bitrate** su low</span><span class="sxs-lookup"><span data-stu-id="2ee52-118">Set **Bitrate Mode** to Low</span></span>
* <span data-ttu-id="2ee52-119">Impostare la **qualità spaziale** su una qualità media spaziale</span><span class="sxs-lookup"><span data-stu-id="2ee52-119">Set **Spatial Quality** to Medium Spatial Quality</span></span>

<span data-ttu-id="2ee52-120">Dopo queste modifiche, il riquadro **Inspector** per il file video sarà simile al seguente:</span><span class="sxs-lookup"><span data-stu-id="2ee52-120">After these adjustments, the **Inspector** pane for the video file will look like this:</span></span>

![Riquadro proprietà video](images/spatial-audio/video-property-pane.png)

<span data-ttu-id="2ee52-122">Successivamente, aggiungere un oggetto **lettore video** alla **gerarchia** facendo clic con il pulsante destro del mouse sul riquadro **gerarchia** e scegliendo **video-> lettore video**:</span><span class="sxs-lookup"><span data-stu-id="2ee52-122">Next, add a **Video Player** object to the **Hierarchy** by right-clicking on the **Hierarchy** pane and choosing **Video -> Video Player**:</span></span>

![Lettore video nella gerarchia](images/spatial-audio/video-player-in-hierarchy.png)

## <a name="play-video-onto-a-quadrangle"></a><span data-ttu-id="2ee52-124">Riprodurre video su un quadrilatero</span><span class="sxs-lookup"><span data-stu-id="2ee52-124">Play video onto a quadrangle</span></span>

<span data-ttu-id="2ee52-125">L'oggetto **Player video** necessita di un oggetto gioco con trama su cui eseguire il rendering del video.</span><span class="sxs-lookup"><span data-stu-id="2ee52-125">The **Video Player** object needs a textured game object on which to render the video.</span></span> <span data-ttu-id="2ee52-126">Per prima cosa, aggiungere un **Quad** alla **gerarchia** facendo clic con il pulsante destro del mouse sul riquadro **gerarchia** e scegliendo **oggetto 3D-> Quad**:</span><span class="sxs-lookup"><span data-stu-id="2ee52-126">First, add a **Quad** to your **Hierarchy** by right-clicking on the **Hierarchy** pane and choosing **3D Object -> Quad**:</span></span>

![Aggiungere Quad alla gerarchia](images/spatial-audio/add-quad-to-hierarchy.png)

<span data-ttu-id="2ee52-128">Per assicurarsi che il **Quad** venga visualizzato davanti all'utente all'avvio dell'applicazione, impostare la proprietà **position** del **Quad** su (0, 0, 2) e la proprietà **scale** su (1,28, 0,72, 1).</span><span class="sxs-lookup"><span data-stu-id="2ee52-128">To ensure the **Quad** appears in front of the user when the application starts, set the **Position** property of the **Quad** to (0, 0, 2), and the **Scale** property to (1.28, 0.72, 1).</span></span> <span data-ttu-id="2ee52-129">Una volta apportate queste modifiche, il componente **Transform** nel riquadro **Inspector** per il **Quad** sarà simile al seguente:</span><span class="sxs-lookup"><span data-stu-id="2ee52-129">After these changes, the **Transform** component on the **Inspector** pane for the **Quad** will look like this:</span></span>

![Trasformazione quad](images/spatial-audio/quad-transform.png)

<span data-ttu-id="2ee52-131">Per creare una trama del **Quad** con video, creare una nuova **trama di rendering**.</span><span class="sxs-lookup"><span data-stu-id="2ee52-131">To texture the **Quad** with video, create a new **Render Texture**.</span></span> <span data-ttu-id="2ee52-132">Nel riquadro **progetto** , fare clic con il pulsante destro del mouse e scegliere **Crea-> trama di rendering**:</span><span class="sxs-lookup"><span data-stu-id="2ee52-132">In the **Project** pane, right-click and choose **Create -> Render Texture**:</span></span>

![Crea trama di rendering](images/spatial-audio/create-render-texture.png)

<span data-ttu-id="2ee52-134">Nel riquadro **Inspector** della trama di **rendering** impostare la proprietà **size** in modo che corrisponda alla risoluzione nativa del video 1280x720.</span><span class="sxs-lookup"><span data-stu-id="2ee52-134">On the **Inspector** pane of the **Render Texture**, set the **Size** property to match the video's native resolution of 1280x720.</span></span> <span data-ttu-id="2ee52-135">Quindi, per garantire prestazioni di rendering ottimali in HoloLens 2, impostare la proprietà **depth buffer** su almeno **16 bit di profondità**.</span><span class="sxs-lookup"><span data-stu-id="2ee52-135">Then, to ensure good rendering performance on HoloLens 2, set the **Depth Buffer** property to **At least 16 bits depth**.</span></span> <span data-ttu-id="2ee52-136">Dopo queste impostazioni, il riquadro **Inspector** per la **trama di rendering** sarà simile al seguente:</span><span class="sxs-lookup"><span data-stu-id="2ee52-136">After these settings, the **Inspector** pane for the **Render Texture** will look like this:</span></span>

![Proprietà trama di rendering](images/spatial-audio/render-texture-properties.png)

<span data-ttu-id="2ee52-138">Usare quindi la nuova **trama di rendering** come trama per il **Quad**:</span><span class="sxs-lookup"><span data-stu-id="2ee52-138">Next, use your new **Render Texture** as the texture for the **Quad**:</span></span>
1. <span data-ttu-id="2ee52-139">Trascinare la **trama di rendering** dal riquadro **progetto** al **quadrato** della **gerarchia**</span><span class="sxs-lookup"><span data-stu-id="2ee52-139">Drag the **Render Texture** from the **Project** pane onto the **Quad** in the **Hierarchy**</span></span>
2. <span data-ttu-id="2ee52-140">Per garantire prestazioni ottimali in HoloLens 2, nel riquadro **Inspector** per il **Quad** selezionare lo **shader standard del Toolkit di realtà mista**.</span><span class="sxs-lookup"><span data-stu-id="2ee52-140">To ensure good performance on HoloLens 2, on the **Inspector** pane for the **Quad**, select the **Mixed Reality Toolkit Standard Shader**.</span></span>

<span data-ttu-id="2ee52-141">Con queste impostazioni, il componente **trama** nel riquadro **Inspector** per il **Quad** sarà simile al seguente:</span><span class="sxs-lookup"><span data-stu-id="2ee52-141">With these settings, the **Texture** component on the **Inspector** pane for the **Quad** will look like this:</span></span>

![Proprietà trama quad](images/spatial-audio/quad-texture-properties.png)

<span data-ttu-id="2ee52-143">Per impostare il nuovo **lettore video** e il **rendering della trama** per riprodurre il clip video, aprire il riquadro **Inspector** per il **lettore video** e:</span><span class="sxs-lookup"><span data-stu-id="2ee52-143">To set your new **Video Player** and **Render Texture** to play your video clip, open the **Inspector** pane for the **Video Player** and:</span></span>
* <span data-ttu-id="2ee52-144">Imposta la proprietà **video clip** sul file video</span><span class="sxs-lookup"><span data-stu-id="2ee52-144">Set the **Video Clip** property to your video file</span></span>
* <span data-ttu-id="2ee52-145">Casella di controllo **ciclo**</span><span class="sxs-lookup"><span data-stu-id="2ee52-145">Check the **Loop** checkbox</span></span>
* <span data-ttu-id="2ee52-146">Imposta la **trama di destinazione** sulla nuova trama di rendering</span><span class="sxs-lookup"><span data-stu-id="2ee52-146">Set **Target Texture** to your new render texture</span></span>

<span data-ttu-id="2ee52-147">Il riquadro **Inspector** per il **lettore video** sarà ora simile al seguente:</span><span class="sxs-lookup"><span data-stu-id="2ee52-147">The **Inspector** pane for the **Video Player** will now look like this:</span></span>

![Proprietà lettore video](images/spatial-audio/video-player-properties.png)

## <a name="spatialize-the-audio-from-the-video"></a><span data-ttu-id="2ee52-149">Spatialize l'audio dal video</span><span class="sxs-lookup"><span data-stu-id="2ee52-149">Spatialize the audio from the video</span></span>

<span data-ttu-id="2ee52-150">Nel riquadro **Inspector** per il **Quad** creare un' **origine audio** a cui indirizzare l'audio dal video:</span><span class="sxs-lookup"><span data-stu-id="2ee52-150">In the **Inspector** pane for the **Quad**, create an **Audio Source** to which you'll route the audio from the video:</span></span>
* <span data-ttu-id="2ee52-151">Fare clic su **Aggiungi componente** nella parte inferiore del riquadro</span><span class="sxs-lookup"><span data-stu-id="2ee52-151">Click **Add Component** at the bottom of the pane</span></span>
* <span data-ttu-id="2ee52-152">Aggiungere un' **origine audio**</span><span class="sxs-lookup"><span data-stu-id="2ee52-152">Add an **Audio Source**</span></span>

<span data-ttu-id="2ee52-153">Quindi, nell' **origine audio**:</span><span class="sxs-lookup"><span data-stu-id="2ee52-153">Then, on the **Audio Source**:</span></span>
* <span data-ttu-id="2ee52-154">Impostare l' **output** sul mixer</span><span class="sxs-lookup"><span data-stu-id="2ee52-154">Set **Output** to your mixer</span></span>
* <span data-ttu-id="2ee52-155">Controllare la casella **Spatialize**</span><span class="sxs-lookup"><span data-stu-id="2ee52-155">Check the **Spatialize** box</span></span>
* <span data-ttu-id="2ee52-156">Spostare il dispositivo di scorrimento di **Blend spaziale** su 1 (3D)</span><span class="sxs-lookup"><span data-stu-id="2ee52-156">Move the **Spatial Blend** slider to 1 (3D)</span></span>

<span data-ttu-id="2ee52-157">Una volta apportate queste modifiche, il componente di **origine audio** nel riquadro **Inspector** per il **Quad** sarà simile al seguente:</span><span class="sxs-lookup"><span data-stu-id="2ee52-157">After these changes, the **Audio Source** component on the **Inspector** pane for the **Quad** will look like this:</span></span>

![Controllo origine audio quad](images/spatial-audio/quad-audio-source-inspector.png)

<span data-ttu-id="2ee52-159">Per impostare il **lettore video** in modo da instradare l'audio all' **origine audio** sul **Quad**, aprire il riquadro **Inspector** per il **lettore video** e:</span><span class="sxs-lookup"><span data-stu-id="2ee52-159">To set the **Video Player** to route its audio to the **Audio Source** on the **Quad**, open the **Inspector** pane for the **Video Player** and:</span></span>
* <span data-ttu-id="2ee52-160">Impostare la **modalità di output audio** su' Audio source '</span><span class="sxs-lookup"><span data-stu-id="2ee52-160">Set the **Audio Output Mode** to 'Audio Source'</span></span>
* <span data-ttu-id="2ee52-161">Impostare la proprietà di **origine audio** sul quad</span><span class="sxs-lookup"><span data-stu-id="2ee52-161">Set the **Audio Source** property to your Quad</span></span>

<span data-ttu-id="2ee52-162">Dopo queste modifiche, il riquadro **Inspector** per il **lettore video** sarà simile al seguente:</span><span class="sxs-lookup"><span data-stu-id="2ee52-162">After these changes, the **Inspector** pane for the **Video Player** will look like this:</span></span>

![Origine audio del set di lettori video](images/spatial-audio/video-player-set-audio-source.png)

## <a name="next-steps"></a><span data-ttu-id="2ee52-164">Passaggi successivi</span><span class="sxs-lookup"><span data-stu-id="2ee52-164">Next steps</span></span>

<span data-ttu-id="2ee52-165">Provare l'app in un HoloLens 2 o nell'editor di Unity.</span><span class="sxs-lookup"><span data-stu-id="2ee52-165">Try out your app on a HoloLens 2 or in the Unity editor.</span></span> <span data-ttu-id="2ee52-166">Potrai visualizzare e ascoltare il video e l'audio del video sarà spaziali.</span><span class="sxs-lookup"><span data-stu-id="2ee52-166">You'll see and hear the video, and the audio from the video will be spatialized.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="2ee52-167">Capitolo 4</span><span class="sxs-lookup"><span data-stu-id="2ee52-167">Chapter 4</span></span>](unity-spatial-audio-ch4.md) 


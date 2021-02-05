---
title: Esercitazioni audio spaziali-2. Spazializzazione dei suoni di interazione del pulsante
description: Aggiungere un pulsante al progetto e spatialize i suoni di interazione dei pulsanti.
author: kegodin
ms.author: v-hferrone
ms.date: 02/05/2021
ms.topic: article
keywords: realtà mista, Unity, esercitazione, hololens2, audio spaziale, MRTK, Toolkit per realtà mista, UWP, Windows 10, HRTF, funzione di trasferimento correlato alla testa, riverbero, Microsoft Spatializer, prefabbricati, curva del volume
ms.openlocfilehash: 12d159cb162cbf136483f7be94b0d297319a0737
ms.sourcegitcommit: 68140e9ce84e69a99c2b3d970c7b8f2927a7fc93
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/05/2021
ms.locfileid: "99590763"
---
# <a name="2-spatializing-button-interaction-sounds"></a><span data-ttu-id="35844-105">2. Spazializzazione dei suoni di interazione del pulsante</span><span class="sxs-lookup"><span data-stu-id="35844-105">2. Spatializing button interaction sounds</span></span>

## <a name="overview"></a><span data-ttu-id="35844-106">Panoramica</span><span class="sxs-lookup"><span data-stu-id="35844-106">Overview</span></span>

<span data-ttu-id="35844-107">In questa esercitazione si apprenderà come spatialize i suoni di interazione dei pulsanti e come usare un clip audio per testare l'interazione con i pulsanti spaziali.</span><span class="sxs-lookup"><span data-stu-id="35844-107">In this tutorial, you will learn how to spatialize the button interaction sounds and also learn how to use an audio clip to test spatialized button interaction.</span></span>  

## <a name="objectives"></a><span data-ttu-id="35844-108">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="35844-108">Objectives</span></span>

* <span data-ttu-id="35844-109">Aggiungi e Spatialize i suoni dei clic del pulsante</span><span class="sxs-lookup"><span data-stu-id="35844-109">Add and Spatialize the button click sounds</span></span>

## <a name="add-a-button"></a><span data-ttu-id="35844-110">Aggiungere un pulsante</span><span class="sxs-lookup"><span data-stu-id="35844-110">Add a button</span></span>

<span data-ttu-id="35844-111">Per aggiungere il prefabbricato dei pulsanti, nella finestra del **progetto** selezionare **pacchetti** e digitare "PressableButtonHoloLens2" nella barra di ricerca.</span><span class="sxs-lookup"><span data-stu-id="35844-111">To add the Button prefab, in the **Project** window, select **Packages** and type "PressableButtonHoloLens2" in the search bar.</span></span>

![Prefabbricato Button negli asset](images/spatial-audio/spatial-audio-02-section1-step1-1.png)

<span data-ttu-id="35844-113">Il prefabbricato del pulsante è la voce rappresentata da un'icona blu.</span><span class="sxs-lookup"><span data-stu-id="35844-113">The button prefab is the entry represented by a blue icon.</span></span> <span data-ttu-id="35844-114">Fare clic e trascinare il prefabbricato **PressableButtonHoloLens2** nella gerarchia.</span><span class="sxs-lookup"><span data-stu-id="35844-114">Click and drag the **PressableButtonHoloLens2** prefab into the Hierarchy.</span></span> <span data-ttu-id="35844-115">Con l'oggetto **PressableButtonHoloLens2** ancora selezionato, nella finestra di controllo configurare il componente **Transform** come indicato di seguito:</span><span class="sxs-lookup"><span data-stu-id="35844-115">With the **PressableButtonHoloLens2** object still selected, in the Inspector window, configure the **Transform** component as follows:</span></span>

* <span data-ttu-id="35844-116">**Posizione**: X = 0, Y =-0,4, Z = 2</span><span class="sxs-lookup"><span data-stu-id="35844-116">**Position**: X = 0, Y = -0.4, Z = 2</span></span>
* <span data-ttu-id="35844-117">**Rotation** (Rotazione): X = 0, Y = 0, Z = 0</span><span class="sxs-lookup"><span data-stu-id="35844-117">**Rotation**: X = 0, Y = 0, Z = 0</span></span>
* <span data-ttu-id="35844-118">**Scale** (Scala): X = 1, Y = 1, Z = 1</span><span class="sxs-lookup"><span data-stu-id="35844-118">**Scale**: X = 1, Y = 1, Z = 1</span></span>

![Trasformazione pulsante](images/spatial-audio/spatial-audio-02-section1-step1-2.png)

<span data-ttu-id="35844-120">Per concentrarsi sugli oggetti nella scena, è possibile fare doppio clic sull'oggetto **PressableButtonHoloLens2** e quindi eseguire di nuovo lo zoom:</span><span class="sxs-lookup"><span data-stu-id="35844-120">To focus in on the objects in the scene, you can double-click on the **PressableButtonHoloLens2** object, and then zoom slightly in again:</span></span>

## <a name="spatialize-button-feedback"></a><span data-ttu-id="35844-121">Commenti e suggerimenti sul pulsante Spatialize</span><span class="sxs-lookup"><span data-stu-id="35844-121">Spatialize button feedback</span></span>

<span data-ttu-id="35844-122">In questo passaggio si spatialize il feedback audio per il pulsante.</span><span class="sxs-lookup"><span data-stu-id="35844-122">In this step, you'll spatialize the audio feedback for the button.</span></span> <span data-ttu-id="35844-123">Per suggerimenti sulla progettazione correlati, vedere [progettazione di suoni spaziali](../../../design/spatial-sound-design.md).</span><span class="sxs-lookup"><span data-stu-id="35844-123">For related design suggestions, see [spatial sound design](../../../design/spatial-sound-design.md).</span></span>

<span data-ttu-id="35844-124">Nella finestra **mixer audio** è possibile definire le destinazioni denominate **gruppi di mixer** per la riproduzione audio dai componenti di **origine audio** .</span><span class="sxs-lookup"><span data-stu-id="35844-124">In the **Audio Mixer** window you will define destinations called **Mixer Groups**, for audio playback from **Audio Source** components.</span></span>

<span data-ttu-id="35844-125">Per aprire la finestra **mixer audio** , nel menu Unity scegliere **finestra**  >  **audio** audio  >  **mixer**: ![ Apri finestra mixer audio](images/spatial-audio/spatial-audio-02-section2-step1-1.png)</span><span class="sxs-lookup"><span data-stu-id="35844-125">To open the **Audio Mixer** window, In the Unity menu, select **Window** > **Audio** > **Audio Mixer**: ![Open Audio Mixer Window](images/spatial-audio/spatial-audio-02-section2-step1-1.png)</span></span>

 <span data-ttu-id="35844-126">Per creare un **mixer** , fare clic su "+" accanto a **mixer** e immettere un nome adatto al mixer, ad esempio il _mixer audio spaziale_.</span><span class="sxs-lookup"><span data-stu-id="35844-126">Create a **Mixer** by clicking the '+' next to **Mixers** and enter a suitable name to the Mixer for example, _Spatial Audio Mixer_.</span></span> <span data-ttu-id="35844-127">Il nuovo mixer includerà un **gruppo** predefinito denominato **Master**.</span><span class="sxs-lookup"><span data-stu-id="35844-127">The new mixer will include a default **Group** called **Master**.</span></span>

![Pannello mixer con primo mixer](images/spatial-audio/spatial-audio-02-section2-step1-2.png)

> [!NOTE]
> <span data-ttu-id="35844-129">Fino a quando non viene abilitato il riverbero nel [quinto capitolo: uso di Reverb per aggiungere la distanza all'audio spaziale](unity-spatial-audio-ch5.md), il contatore del volume del mixer non Mostra l'attività per i suoni riprodotti tramite Microsoft Spatializer</span><span class="sxs-lookup"><span data-stu-id="35844-129">Until reverb is enabled in [5th Chapter: Using reverb to add distance to spatial audio](unity-spatial-audio-ch5.md), the mixer's volume meter doesn't show activity for sounds played through the Microsoft Spatializer</span></span>

<span data-ttu-id="35844-130">Nella finestra gerarchia selezionare il **PressableButtonHoloLens2** quindi nella finestra di controllo trovare il componente di **origine audio** e configurare il componente di origine audio come indicato di seguito:</span><span class="sxs-lookup"><span data-stu-id="35844-130">In the Hierarchy window, select the **PressableButtonHoloLens2** then in the Inspector window find the **Audio Source** component and Configure the Audio Source component as follows:</span></span>

1. <span data-ttu-id="35844-131">Per la proprietà **output** , fare clic sul selettore e scegliere il **mixer** creato.</span><span class="sxs-lookup"><span data-stu-id="35844-131">For the **Output** property, click the selector and choose the **Mixer** that you created.</span></span>
2. <span data-ttu-id="35844-132">Selezionare la casella di controllo **Spatialize** .</span><span class="sxs-lookup"><span data-stu-id="35844-132">Check the **Spatialize** checkbox.</span></span>
3. <span data-ttu-id="35844-133">Spostare il dispositivo di scorrimento **Blend spaziale** su 3D (1).</span><span class="sxs-lookup"><span data-stu-id="35844-133">Move the **Spatial Blend** slider to 3D (1).</span></span>

![Origine audio pulsante](images/spatial-audio/spatial-audio-02-section2-step1-3.png)

> [!NOTE]
> <span data-ttu-id="35844-135">Se si sposta **Blend spaziale** in 1 (3D) senza selezionare la casella di controllo **Spatialize** , Unity utilizzerà il relativo Spatializer di panoramica anziché **Microsoft Spatializer** con HRTFs.</span><span class="sxs-lookup"><span data-stu-id="35844-135">If you move **Spatial Blend** to 1 (3D) without checking the **Spatialize** checkbox, Unity will use its panning spatializer, instead of the **Microsoft Spatializer** with HRTFs.</span></span>

## <a name="adjust-the-volume-curve"></a><span data-ttu-id="35844-136">Modificare la curva del volume</span><span class="sxs-lookup"><span data-stu-id="35844-136">Adjust the Volume curve</span></span>

<span data-ttu-id="35844-137">Per impostazione predefinita, Unity attenua i suoni spaziali Man mano che si ottengono più lontano dal listener.</span><span class="sxs-lookup"><span data-stu-id="35844-137">By default, Unity will attenuate spatialized sounds as they get farther from the listener.</span></span> <span data-ttu-id="35844-138">Quando questa attenuazione viene applicata ai suoni di feedback interazione, l'interfaccia può diventare più difficile da usare.</span><span class="sxs-lookup"><span data-stu-id="35844-138">When this attenuation is applied to interaction feedback sounds, the interface can become more difficult to use.</span></span>

<span data-ttu-id="35844-139">Per disabilitare questa attenuazione, è necessario modificare la curva del **volume** nel componente di **origine audio** .</span><span class="sxs-lookup"><span data-stu-id="35844-139">To disable this attenuation, you need to adjust the **Volume** curve In the **Audio Source** component.</span></span>

<span data-ttu-id="35844-140">Nella finestra gerarchia selezionare il **PressableButtonHoloLens2** quindi nella finestra di controllo passare a impostazioni audio **3D origine audio**  >   e configurare come segue:</span><span class="sxs-lookup"><span data-stu-id="35844-140">In the Hierarchy window, select the **PressableButtonHoloLens2** then in the Inspector window navigate to  **Audio Source** > **3D Sound Settings** and Configure as follows:</span></span>

1. <span data-ttu-id="35844-141">Impostare la proprietà **volume attenuazione** su attenuazione lineare</span><span class="sxs-lookup"><span data-stu-id="35844-141">Set the **Volume Rolloff** property to Linear Rolloff</span></span>
2. <span data-ttu-id="35844-142">Trascinare l'endpoint sulla curva del **volume** (la curva rossa) da' 0' sull'asse y fino a' 1'</span><span class="sxs-lookup"><span data-stu-id="35844-142">Drag the endpoint on the **Volume** curve (the red curve) from '0' on the y axis up to '1'</span></span>
3. <span data-ttu-id="35844-143">Per regolare la forma della curva del **volume** in modo che sia piatta, trascinare il controllo forma curva bianca in modo che sia parallelo all'asse X</span><span class="sxs-lookup"><span data-stu-id="35844-143">To adjust the shape of the **Volume** curve to be flat, drag the white curve shape control to be parallel to the X axis</span></span>

![Impostazioni suono 3D pulsante](images/spatial-audio/spatial-audio-02-section3-step1-1.png)

## <a name="testing-the-spatialize-audio"></a><span data-ttu-id="35844-145">Test dell'audio spatialize</span><span class="sxs-lookup"><span data-stu-id="35844-145">Testing the spatialize audio</span></span>

<span data-ttu-id="35844-146">Per testare l'audio spatialize nell'editor di Unity, è necessario aggiungere una clip audio nel componente **origine audio** con l'opzione **ciclo** archiviato nell'oggetto **PressableButtonHoloLens2** .</span><span class="sxs-lookup"><span data-stu-id="35844-146">To test the spatialize audio in the unity editor you have to add an audio clip in the **Audio Source** component with **Loop** option checked in on **PressableButtonHoloLens2** object.</span></span>

<span data-ttu-id="35844-147">In modalità di riproduzione spostare l'oggetto **PressableButtonHoloLens2** da sinistra a destra e confrontare con e senza audio spaziale abilitato sulla workstation.</span><span class="sxs-lookup"><span data-stu-id="35844-147">In the play mode move the **PressableButtonHoloLens2** object from left to right and compare with and without spatial audio enabled on your workstation.</span></span> <span data-ttu-id="35844-148">È anche possibile modificare le impostazioni di origine audio per i test:</span><span class="sxs-lookup"><span data-stu-id="35844-148">You can also change the Audio Source settings for testing by:</span></span>

* <span data-ttu-id="35844-149">Trasferimento della proprietà di **Blend spaziale** tra 0-1 (audio 2D non spaziale e 3D con spaziali)</span><span class="sxs-lookup"><span data-stu-id="35844-149">Moving the **Spatial Blend** property between 0 - 1 (2D non-spatialized and 3D spatialized sound)</span></span>
* <span data-ttu-id="35844-150">Verifica e deselezione della proprietà **Spatialize**</span><span class="sxs-lookup"><span data-stu-id="35844-150">Checking and unchecking the **Spatialize** property</span></span>

<span data-ttu-id="35844-151">Provare l'app in HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="35844-151">Try out the app on HoloLens 2.</span></span> <span data-ttu-id="35844-152">Nell'app è possibile fare clic sul pulsante e sentire i suoni di interazione dei pulsanti spaziali.</span><span class="sxs-lookup"><span data-stu-id="35844-152">In the app, you can click the button and hear the spatialized button interaction sounds.</span></span>

> [!TIP]
> <span data-ttu-id="35844-153">Per rivedere la procedura di compilazione e distribuzione di un progetto Unity in HoloLens 2, fare riferimento alle istruzioni riportate in [Compilazione dell'app nel dispositivo HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2).</span><span class="sxs-lookup"><span data-stu-id="35844-153">For a reminder on how to build and deploy your Unity project to HoloLens 2, you can refer to the [Building your app to your HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions.</span></span>

## <a name="congratulations"></a><span data-ttu-id="35844-154">Lezione completata</span><span class="sxs-lookup"><span data-stu-id="35844-154">Congratulations</span></span>

<span data-ttu-id="35844-155">In questa esercitazione è stato illustrato come spatialize i suoni di interazione dei pulsanti e come usare un clip audio per testare l'interazione con i pulsanti spaziali.</span><span class="sxs-lookup"><span data-stu-id="35844-155">In this tutorial you have learnt to spatialize the button interaction sounds and to use an audio clip to test spatialized button interaction.</span></span> <span data-ttu-id="35844-156">Nell'esercitazione successiva si apprenderà come spatialize audio da un'origine video.</span><span class="sxs-lookup"><span data-stu-id="35844-156">In the next tutorial you will learn how to spatialize audio from an video source.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="35844-157">Esercitazione successiva: 3. Spatializing audio da un video</span><span class="sxs-lookup"><span data-stu-id="35844-157">Next Tutorial: 3. Spatializing audio from a video</span></span>](unity-spatial-audio-ch3.md)

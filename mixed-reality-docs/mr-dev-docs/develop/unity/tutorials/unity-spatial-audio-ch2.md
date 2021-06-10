---
title: Esercitazioni sull'audio spaziale - 2. Spazializzazione dei suoni di interazione del pulsante
description: Aggiungere un pulsante al progetto e spazializzare i suoni di interazione del pulsante.
author: kegodin
ms.author: v-hferrone
ms.date: 02/05/2021
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens2, spatial audio, MRTK, mixed reality toolkit, UWP, Windows 10, HRTF, head-related transfer function, reverb, Microsoft Spatializer, prefabs, volume curve
ms.openlocfilehash: f3f2faf8220eaebcc674bcf02a45d99d58169076
ms.sourcegitcommit: 4a6c26615d52776bdc4faab70391592092a471fc
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2021
ms.locfileid: "110712808"
---
# <a name="2-spatializing-button-interaction-sounds"></a><span data-ttu-id="d633e-105">2. Spazializzazione dei suoni di interazione del pulsante</span><span class="sxs-lookup"><span data-stu-id="d633e-105">2. Spatializing button interaction sounds</span></span>

## <a name="overview"></a><span data-ttu-id="d633e-106">Panoramica</span><span class="sxs-lookup"><span data-stu-id="d633e-106">Overview</span></span>

<span data-ttu-id="d633e-107">In questa esercitazione si apprenderà come spazializzare i suoni di interazione del pulsante e come usare un clip audio per testare l'interazione con il pulsante spazializzato.</span><span class="sxs-lookup"><span data-stu-id="d633e-107">In this tutorial, you will learn how to spatialize the button interaction sounds and also learn how to use an audio clip to test spatialized button interaction.</span></span>  

## <a name="objectives"></a><span data-ttu-id="d633e-108">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="d633e-108">Objectives</span></span>

* <span data-ttu-id="d633e-109">Aggiungere e spazializzare i suoni di clic del pulsante</span><span class="sxs-lookup"><span data-stu-id="d633e-109">Add and Spatialize the button click sounds</span></span>

## <a name="add-a-button"></a><span data-ttu-id="d633e-110">Aggiungere un pulsante</span><span class="sxs-lookup"><span data-stu-id="d633e-110">Add a button</span></span>

<span data-ttu-id="d633e-111">Per aggiungere il prefab pulsante, nella finestra **Progetto** selezionare **Pacchetti** e digitare "PressableButtonHoloLens2" nella barra di ricerca.</span><span class="sxs-lookup"><span data-stu-id="d633e-111">To add the Button prefab, in the **Project** window, select **Packages** and type "PressableButtonHoloLens2" in the search bar.</span></span>

![Prefab dei pulsanti in Asset](images/spatial-audio/spatial-audio-02-section1-step1-1.PNG)

<span data-ttu-id="d633e-113">Il prefab del pulsante è la voce rappresentata da un'icona blu.</span><span class="sxs-lookup"><span data-stu-id="d633e-113">The button prefab is the entry represented by a blue icon.</span></span> <span data-ttu-id="d633e-114">Fare clic e trascinare il prefab **PressableButtonHoloLens2** nella gerarchia.</span><span class="sxs-lookup"><span data-stu-id="d633e-114">Click and drag the **PressableButtonHoloLens2** prefab into the Hierarchy.</span></span> <span data-ttu-id="d633e-115">Con **l'oggetto PressableButtonHoloLens2** ancora selezionato, nella finestra Inspector configurare **il componente Transform** come indicato di seguito:</span><span class="sxs-lookup"><span data-stu-id="d633e-115">With the **PressableButtonHoloLens2** object still selected, in the Inspector window, configure the **Transform** component as follows:</span></span>

* <span data-ttu-id="d633e-116">**Posizione:** X = 0, Y = -0,4, Z = 2</span><span class="sxs-lookup"><span data-stu-id="d633e-116">**Position**: X = 0, Y = -0.4, Z = 2</span></span>
* <span data-ttu-id="d633e-117">**Rotation** (Rotazione): X = 0, Y = 0, Z = 0</span><span class="sxs-lookup"><span data-stu-id="d633e-117">**Rotation**: X = 0, Y = 0, Z = 0</span></span>
* <span data-ttu-id="d633e-118">**Scale** (Scala): X = 1, Y = 1, Z = 1</span><span class="sxs-lookup"><span data-stu-id="d633e-118">**Scale**: X = 1, Y = 1, Z = 1</span></span>

![Trasformazione pulsante](images/spatial-audio/spatial-audio-02-section1-step1-2.PNG)

<span data-ttu-id="d633e-120">Per concentrarsi sugli oggetti nella scena, è possibile fare doppio clic sull'oggetto **PressableButtonHoloLens2** e quindi eseguire di nuovo lo zoom avanti leggermente:</span><span class="sxs-lookup"><span data-stu-id="d633e-120">To focus in on the objects in the scene, you can double-click on the **PressableButtonHoloLens2** object, and then zoom slightly in again:</span></span>

## <a name="spatialize-button-feedback"></a><span data-ttu-id="d633e-121">Commenti e suggerimenti sui pulsanti Spazializza</span><span class="sxs-lookup"><span data-stu-id="d633e-121">Spatialize button feedback</span></span>

<span data-ttu-id="d633e-122">In questo passaggio si spazializzerà il feedback audio per il pulsante.</span><span class="sxs-lookup"><span data-stu-id="d633e-122">In this step, you'll spatialize the audio feedback for the button.</span></span> <span data-ttu-id="d633e-123">Per suggerimenti di progettazione correlati, vedere [Progettazione del suono spaziale.](../../../design/spatial-sound-design.md)</span><span class="sxs-lookup"><span data-stu-id="d633e-123">For related design suggestions, see [spatial sound design](../../../design/spatial-sound-design.md).</span></span>

<span data-ttu-id="d633e-124">Nella finestra **Mixer audio** si definiranno le destinazioni denominate **Gruppi mixer**, per la riproduzione audio dai **componenti origine** audio.</span><span class="sxs-lookup"><span data-stu-id="d633e-124">In the **Audio Mixer** window you will define destinations called **Mixer Groups**, for audio playback from **Audio Source** components.</span></span>

<span data-ttu-id="d633e-125">Per aprire la **finestra Mixer** audio, nel menu Unity selezionare **Mixer** audio finestra  >    >  : Apri ![ finestra mixer audio](images/spatial-audio/spatial-audio-02-section2-step1-1.PNG)</span><span class="sxs-lookup"><span data-stu-id="d633e-125">To open the **Audio Mixer** window, In the Unity menu, select **Window** > **Audio** > **Audio Mixer**: ![Open Audio Mixer Window](images/spatial-audio/spatial-audio-02-section2-step1-1.PNG)</span></span>

 <span data-ttu-id="d633e-126">Creare un **mixer** facendo clic su "+" accanto a **Mixer** e immettendo un nome appropriato per il mixer, ad esempio _Mixer audio spaziale._</span><span class="sxs-lookup"><span data-stu-id="d633e-126">Create a **Mixer** by clicking the '+' next to **Mixers** and enter a suitable name to the Mixer for example, _Spatial Audio Mixer_.</span></span> <span data-ttu-id="d633e-127">Il nuovo mixer includerà un gruppo **predefinito** denominato **Master**.</span><span class="sxs-lookup"><span data-stu-id="d633e-127">The new mixer will include a default **Group** called **Master**.</span></span>

![Pannello mixer con primo mixer](images/spatial-audio/spatial-audio-02-section2-step1-2.PNG)

> [!NOTE]
> <span data-ttu-id="d633e-129">Fino a quando il riverbero non viene abilitato nel [5° capitolo:](unity-spatial-audio-ch5.md)Uso del riverbero per aggiungere la distanza all'audio spaziale, il misuratore del volume del mixer non mostra l'attività per i suoni riprodotti tramite Microsoft Spatializer</span><span class="sxs-lookup"><span data-stu-id="d633e-129">Until reverb is enabled in [5th Chapter: Using reverb to add distance to spatial audio](unity-spatial-audio-ch5.md), the mixer's volume meter doesn't show activity for sounds played through the Microsoft Spatializer</span></span>

<span data-ttu-id="d633e-130">Nella finestra Hierarchy (Gerarchia) selezionare **PressableButtonHoloLens2** e quindi nella finestra Inspector (Controllo) trovare il componente Audio Source (Origine **audio)** e Configure the Audio Source component (Configura origine audio) come indicato di seguito:</span><span class="sxs-lookup"><span data-stu-id="d633e-130">In the Hierarchy window, select the **PressableButtonHoloLens2** then in the Inspector window find the **Audio Source** component and Configure the Audio Source component as follows:</span></span>

1. <span data-ttu-id="d633e-131">Per la **proprietà Output** fare clic sul selettore e scegliere il **mixer** creato.</span><span class="sxs-lookup"><span data-stu-id="d633e-131">For the **Output** property, click the selector and choose the **Mixer** that you created.</span></span>
2. <span data-ttu-id="d633e-132">Selezionare la **casella di controllo Spazializza.**</span><span class="sxs-lookup"><span data-stu-id="d633e-132">Check the **Spatialize** checkbox.</span></span>
3. <span data-ttu-id="d633e-133">Spostare il **dispositivo di scorrimento Fusione** spaziale su 3D (1).</span><span class="sxs-lookup"><span data-stu-id="d633e-133">Move the **Spatial Blend** slider to 3D (1).</span></span>

![Origine audio del pulsante](images/spatial-audio/spatial-audio-02-section2-step1-3.PNG)

> [!NOTE]
> <span data-ttu-id="d633e-135">Se si sposta **Spatial Blend** su 1 (3D) senza selezionare la casella di controllo **Spatialize,** Unity userà il suo spazializzatore di panoramica, anziché **Microsoft Spatializer** con HRTFs.</span><span class="sxs-lookup"><span data-stu-id="d633e-135">If you move **Spatial Blend** to 1 (3D) without checking the **Spatialize** checkbox, Unity will use its panning spatializer, instead of the **Microsoft Spatializer** with HRTFs.</span></span>

## <a name="adjust-the-volume-curve"></a><span data-ttu-id="d633e-136">Regolare la curva del volume</span><span class="sxs-lookup"><span data-stu-id="d633e-136">Adjust the Volume curve</span></span>

<span data-ttu-id="d633e-137">Per impostazione predefinita, Unity attenua i suoni spazializzati quando si allontanano dal listener.</span><span class="sxs-lookup"><span data-stu-id="d633e-137">By default, Unity will attenuate spatialized sounds as they get farther from the listener.</span></span> <span data-ttu-id="d633e-138">Quando questa attenuazione viene applicata ai suoni di feedback dell'interazione, l'interfaccia può diventare più difficile da usare.</span><span class="sxs-lookup"><span data-stu-id="d633e-138">When this attenuation is applied to interaction feedback sounds, the interface can become more difficult to use.</span></span>

<span data-ttu-id="d633e-139">Per disabilitare questa attenuazione, è necessario regolare la **curva del volume** nel componente **Origine** audio.</span><span class="sxs-lookup"><span data-stu-id="d633e-139">To disable this attenuation, you need to adjust the **Volume** curve In the **Audio Source** component.</span></span>

<span data-ttu-id="d633e-140">Nella finestra Hierarchy (Gerarchia) selezionare **PressableButtonHoloLens2** e quindi nella finestra Inspector (Controllo) passare a **Audio Source** 3D Sound Settings (Impostazioni audio  >  **3D)** e Configure (Configura) come indicato di seguito:</span><span class="sxs-lookup"><span data-stu-id="d633e-140">In the Hierarchy window, select the **PressableButtonHoloLens2** then in the Inspector window navigate to  **Audio Source** > **3D Sound Settings** and Configure as follows:</span></span>

1. <span data-ttu-id="d633e-141">Impostare la **proprietà Rolloff del** volume su Rolloff lineare</span><span class="sxs-lookup"><span data-stu-id="d633e-141">Set the **Volume Rolloff** property to Linear Rolloff</span></span>
2. <span data-ttu-id="d633e-142">Trascinare l'endpoint sulla **curva volume** (curva rossa) da "0" sull'asse y fino a "1"</span><span class="sxs-lookup"><span data-stu-id="d633e-142">Drag the endpoint on the **Volume** curve (the red curve) from '0' on the y axis up to '1'</span></span>
3. <span data-ttu-id="d633e-143">Per regolare la forma della curva **volume** in modo che sia piana, trascinare il controllo della forma della curva bianca in modo che sia parallelo all'asse X</span><span class="sxs-lookup"><span data-stu-id="d633e-143">To adjust the shape of the **Volume** curve to be flat, drag the white curve shape control to be parallel to the X axis</span></span>

![Impostazioni del suono 3D del pulsante](images/spatial-audio/spatial-audio-02-section3-step1-1.PNG)

## <a name="testing-the-spatialize-audio"></a><span data-ttu-id="d633e-145">Test dell'audio spazializza</span><span class="sxs-lookup"><span data-stu-id="d633e-145">Testing the spatialize audio</span></span>

<span data-ttu-id="d633e-146">Per testare l'audio spazializzabile nell'editor unity, è necessario aggiungere un clip audio nel componente **Origine** audio con **l'opzione Ciclo** selezionata nell'oggetto **PressableButtonHoloLens2.**</span><span class="sxs-lookup"><span data-stu-id="d633e-146">To test the spatialize audio in the unity editor you have to add an audio clip in the **Audio Source** component with **Loop** option checked in on **PressableButtonHoloLens2** object.</span></span>

<span data-ttu-id="d633e-147">In modalità di riproduzione spostare **l'oggetto PressableButtonHoloLens2** da sinistra a destra e confrontare con e senza audio spaziale abilitato nella workstation.</span><span class="sxs-lookup"><span data-stu-id="d633e-147">In the play mode move the **PressableButtonHoloLens2** object from left to right and compare with and without spatial audio enabled on your workstation.</span></span> <span data-ttu-id="d633e-148">È anche possibile modificare le impostazioni di Origine audio per i test:</span><span class="sxs-lookup"><span data-stu-id="d633e-148">You can also change the Audio Source settings for testing by:</span></span>

* <span data-ttu-id="d633e-149">Spostamento della **proprietà Spatial Blend** tra 0 e 1 (suono 2D non spazializzato e 3D spazializzato)</span><span class="sxs-lookup"><span data-stu-id="d633e-149">Moving the **Spatial Blend** property between 0 - 1 (2D non-spatialized and 3D spatialized sound)</span></span>
* <span data-ttu-id="d633e-150">Controllo e deselezione della **proprietà Spatialize**</span><span class="sxs-lookup"><span data-stu-id="d633e-150">Checking and unchecking the **Spatialize** property</span></span>

<span data-ttu-id="d633e-151">Provare l'app HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="d633e-151">Try out the app on HoloLens 2.</span></span> <span data-ttu-id="d633e-152">Nell'app è possibile fare clic sul pulsante e ascoltare i suoni di interazione dei pulsanti spazializzati.</span><span class="sxs-lookup"><span data-stu-id="d633e-152">In the app, you can click the button and hear the spatialized button interaction sounds.</span></span>

> [!TIP]
> <span data-ttu-id="d633e-153">Per rivedere la procedura di compilazione e distribuzione di un progetto Unity in HoloLens 2, fare riferimento alle istruzioni riportate in [Compilazione dell'app nel dispositivo HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2).</span><span class="sxs-lookup"><span data-stu-id="d633e-153">For a reminder on how to build and deploy your Unity project to HoloLens 2, you can refer to the [Building your app to your HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions.</span></span>

## <a name="congratulations"></a><span data-ttu-id="d633e-154">Lezione completata</span><span class="sxs-lookup"><span data-stu-id="d633e-154">Congratulations</span></span>

<span data-ttu-id="d633e-155">In questa esercitazione si è appreso come spazializzare i suoni di interazione del pulsante e usare un clip audio per testare l'interazione con il pulsante spazializzato.</span><span class="sxs-lookup"><span data-stu-id="d633e-155">In this tutorial you have learnt to spatialize the button interaction sounds and to use an audio clip to test spatialized button interaction.</span></span> <span data-ttu-id="d633e-156">Nell'esercitazione successiva si apprenderà come spazializzare l'audio da un'origine video.</span><span class="sxs-lookup"><span data-stu-id="d633e-156">In the next tutorial you will learn how to spatialize audio from an video source.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="d633e-157">Esercitazione successiva: 3. Spazializzazione dell'audio da un video</span><span class="sxs-lookup"><span data-stu-id="d633e-157">Next Tutorial: 3. Spatializing audio from a video</span></span>](unity-spatial-audio-ch3.md)

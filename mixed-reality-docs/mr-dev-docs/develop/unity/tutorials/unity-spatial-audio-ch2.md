---
title: Spazializzazione dei suoni di interazione del pulsante
description: Informazioni su come aggiungere un pulsante e spatialize i suoni di interazione dei pulsanti in un'applicazione di realtà mista.
author: kegodin
ms.author: v-hferrone
ms.date: 12/01/2019
ms.topic: article
keywords: realtà mista, Unity, esercitazione, hololens2, audio spaziale, MRTK, Toolkit per realtà mista, UWP, Windows 10, HRTF, funzione di trasferimento correlato alla testa, riverbero, Microsoft Spatializer, prefabbricati, curva del volume
ms.openlocfilehash: 1f54ba8cab55ba375a6b1499796761ae02b03a02
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2021
ms.locfileid: "98007361"
---
# <a name="spatializing-button-interaction-sounds"></a><span data-ttu-id="4f384-104">Spazializzazione dei suoni di interazione del pulsante</span><span class="sxs-lookup"><span data-stu-id="4f384-104">Spatializing button interaction sounds</span></span>

## <a name="objectives"></a><span data-ttu-id="4f384-105">Obiettivi</span><span class="sxs-lookup"><span data-stu-id="4f384-105">Objectives</span></span>

<span data-ttu-id="4f384-106">In questo secondo capitolo del modulo audio spaziale delle esercitazioni di HoloLens 2 è possibile:</span><span class="sxs-lookup"><span data-stu-id="4f384-106">In this second chapter of the spatial audio module of the HoloLens 2 tutorials, you'll:</span></span>
* <span data-ttu-id="4f384-107">Aggiungere un pulsante</span><span class="sxs-lookup"><span data-stu-id="4f384-107">Add a button</span></span>
* <span data-ttu-id="4f384-108">Spatialize i suoni dei clic del pulsante</span><span class="sxs-lookup"><span data-stu-id="4f384-108">Spatialize the button click sounds</span></span>

## <a name="add-a-button"></a><span data-ttu-id="4f384-109">Aggiungere un pulsante</span><span class="sxs-lookup"><span data-stu-id="4f384-109">Add a button</span></span>

<span data-ttu-id="4f384-110">Nel riquadro **progetto** selezionare **Asset** e digitare "PressableButtonHoloLens2" nella barra di ricerca:</span><span class="sxs-lookup"><span data-stu-id="4f384-110">In the **Project** pane, select **Assets** and type "PressableButtonHoloLens2" in the search bar:</span></span>

![Prefabbricato Button negli asset](images/spatial-audio/button-prefab-in-assets.png)

<span data-ttu-id="4f384-112">Il prefabbricato del pulsante è la voce rappresentata da un'icona blu, anziché da un'icona bianca.</span><span class="sxs-lookup"><span data-stu-id="4f384-112">The button prefab is the entry represented by a blue icon, rather than a white icon.</span></span> <span data-ttu-id="4f384-113">Trascinare il prefabbricato denominato **PressableButtonHoloLens2** nel riquadro **gerarchia** .</span><span class="sxs-lookup"><span data-stu-id="4f384-113">Drag the prefab named **PressableButtonHoloLens2** into the **Hierarchy** pane.</span></span> <span data-ttu-id="4f384-114">Nel riquadro **Inspector** del pulsante nuovo impostare la proprietà **position** su (0,-0,4, 2) in modo che venga visualizzata davanti all'utente all'avvio dell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="4f384-114">In the **Inspector** pane for your new button, set the **Position** property to (0, -0.4, 2) so that it will appear in front of the user when the application starts.</span></span> <span data-ttu-id="4f384-115">Il componente **Transform** del pulsante sarà simile al seguente:</span><span class="sxs-lookup"><span data-stu-id="4f384-115">The **Transform** component of the button will look like this:</span></span>

![Trasformazione pulsante](images/spatial-audio/button-transform.png)

## <a name="spatialize-button-feedback"></a><span data-ttu-id="4f384-117">Commenti e suggerimenti sul pulsante Spatialize</span><span class="sxs-lookup"><span data-stu-id="4f384-117">Spatialize button feedback</span></span>

<span data-ttu-id="4f384-118">In questo passaggio si spatialize il feedback audio per il pulsante.</span><span class="sxs-lookup"><span data-stu-id="4f384-118">In this step, you'll spatialize the audio feedback for the button.</span></span> <span data-ttu-id="4f384-119">Per suggerimenti sulla progettazione correlati, vedere [progettazione di suoni spaziali](../../../design/spatial-sound-design.md).</span><span class="sxs-lookup"><span data-stu-id="4f384-119">For related design suggestions, see [spatial sound design](../../../design/spatial-sound-design.md).</span></span> 

<span data-ttu-id="4f384-120">Il riquadro **mixer audio** è il punto in cui definire le destinazioni, denominate **gruppi di mixer**, per la riproduzione audio dai componenti di **origine audio** .</span><span class="sxs-lookup"><span data-stu-id="4f384-120">The **Audio Mixer** pane is where you'll define destinations, called **Mixer Groups**, for audio playback from **Audio Source** components.</span></span> 
* <span data-ttu-id="4f384-121">Aprire il riquadro **mixer audio** dalla barra dei menu usando la **finestra > audio-> Audio Mixer**</span><span class="sxs-lookup"><span data-stu-id="4f384-121">Open the **Audio Mixer** pane from the menu bar using **Window -> Audio -> Audio Mixer**</span></span>
* <span data-ttu-id="4f384-122">Per creare un **mixer** , fare clic su "+" accanto a **mixer**.</span><span class="sxs-lookup"><span data-stu-id="4f384-122">Create a **Mixer** by clicking the '+' next to **Mixers**.</span></span> <span data-ttu-id="4f384-123">Il nuovo mixer includerà un **gruppo** predefinito denominato **Master**.</span><span class="sxs-lookup"><span data-stu-id="4f384-123">The new mixer will include a default **Group** called **Master**.</span></span>

<span data-ttu-id="4f384-124">Il riquadro del **mixer** sarà ora simile al seguente:</span><span class="sxs-lookup"><span data-stu-id="4f384-124">Your **Mixer** pane will now look like this:</span></span>

![Pannello mixer con primo mixer](images/spatial-audio/mixer-panel-with-first-mixer.png)

> [!NOTE]
> <span data-ttu-id="4f384-126">Fino a quando non viene abilitato il riverbero nel [capitolo 5](unity-spatial-audio-ch5.md), il contatore del volume del mixer non Mostra l'attività per i suoni riprodotti tramite Microsoft Spatializer</span><span class="sxs-lookup"><span data-stu-id="4f384-126">Until reverb is enabled in [Chapter 5](unity-spatial-audio-ch5.md), the mixer's volume meter doesn't show activity for sounds played through the Microsoft Spatializer</span></span>

<span data-ttu-id="4f384-127">Fare clic su **PressableButtonHoloLens2** nel riquadro **gerarchia** .</span><span class="sxs-lookup"><span data-stu-id="4f384-127">Click the **PressableButtonHoloLens2** in the **Hierarchy** pane.</span></span> <span data-ttu-id="4f384-128">Nel riquadro **Inspector** :</span><span class="sxs-lookup"><span data-stu-id="4f384-128">In the **Inspector** pane:</span></span>
1. <span data-ttu-id="4f384-129">Trovare il componente di **origine audio**</span><span class="sxs-lookup"><span data-stu-id="4f384-129">Find the **Audio Source** component</span></span>
2. <span data-ttu-id="4f384-130">Per la proprietà **output** , fare clic sul selettore e scegliere il mixer</span><span class="sxs-lookup"><span data-stu-id="4f384-130">For the **Output** property, click the selector and choose your mixer</span></span>
3. <span data-ttu-id="4f384-131">Selezionare la casella di controllo **Spatialize**</span><span class="sxs-lookup"><span data-stu-id="4f384-131">Check the **Spatialize** checkbox</span></span>
4. <span data-ttu-id="4f384-132">Spostare il dispositivo di scorrimento **Blend spaziale** su 3D (1).</span><span class="sxs-lookup"><span data-stu-id="4f384-132">Move the **Spatial Blend** slider to 3D (1).</span></span>

> [!NOTE]
> <span data-ttu-id="4f384-133">Nelle versioni di Unity precedenti alla 2019, la casella di controllo ' Spatialize ' si trova nella parte inferiore del riquadro **Inspector** per l' **origine audio**.</span><span class="sxs-lookup"><span data-stu-id="4f384-133">In versions of Unity prior to 2019, the 'Spatialize' checkbox is at the bottom of the **Inspector** pane for the **Audio Source**.</span></span>

<span data-ttu-id="4f384-134">Dopo queste modifiche, il componente di **origine audio** del **PressableButtonHoloLens2** sarà simile al seguente:</span><span class="sxs-lookup"><span data-stu-id="4f384-134">After these changes, the **Audio Source** component of your **PressableButtonHoloLens2** will look like this:</span></span>

![Origine audio pulsante](images/spatial-audio/button-audio-source.png)

> [!NOTE]
> <span data-ttu-id="4f384-136">Se si sposta **Blend spaziale** in 1 (3D) senza selezionare la casella di controllo **Spatialize** , Unity utilizzerà il relativo Spatializer di panoramica anziché **Microsoft Spatializer** con HRTFs.</span><span class="sxs-lookup"><span data-stu-id="4f384-136">If you move **Spatial Blend** to 1 (3D) without checking the **Spatialize** checkbox, Unity will use its panning spatializer, instead of the **Microsoft Spatializer** with HRTFs.</span></span>

## <a name="adjust-the-volume-curve"></a><span data-ttu-id="4f384-137">Modificare la curva del volume</span><span class="sxs-lookup"><span data-stu-id="4f384-137">Adjust the Volume curve</span></span>

<span data-ttu-id="4f384-138">Per impostazione predefinita, Unity attenua i suoni spaziali Man mano che si ottengono più lontano dal listener.</span><span class="sxs-lookup"><span data-stu-id="4f384-138">By default, Unity will attenuate spatialized sounds as they get farther from the listener.</span></span> <span data-ttu-id="4f384-139">Quando questa attenuazione viene applicata ai suoni di feedback interazione, l'interfaccia può diventare più difficile da usare.</span><span class="sxs-lookup"><span data-stu-id="4f384-139">When this attenuation is applied to interaction feedback sounds, the interface can become more difficult to use.</span></span>

<span data-ttu-id="4f384-140">Per disabilitare questa attenuazione, modificare la curva del **volume** .</span><span class="sxs-lookup"><span data-stu-id="4f384-140">To disable this attenuation, adjust the **Volume** curve.</span></span> <span data-ttu-id="4f384-141">Nel componente **origine audio** del riquadro **Inspector** per **PressableButtonHoloLens2** è presente una sezione denominata **impostazioni audio 3D**.</span><span class="sxs-lookup"><span data-stu-id="4f384-141">In the **Audio Source** component of the **Inspector** pane for the **PressableButtonHoloLens2**, there is a section called **3D Sound Settings**.</span></span> <span data-ttu-id="4f384-142">In questa sezione:</span><span class="sxs-lookup"><span data-stu-id="4f384-142">In that section:</span></span>
1. <span data-ttu-id="4f384-143">Impostare la proprietà **volume attenuazione** su Linear</span><span class="sxs-lookup"><span data-stu-id="4f384-143">Set the **Volume Rolloff** property to Linear</span></span>
2. <span data-ttu-id="4f384-144">Trascinare l'endpoint sulla curva del **volume** (la curva rossa) da' 0' sull'asse y fino a' 1'</span><span class="sxs-lookup"><span data-stu-id="4f384-144">Drag the endpoint on the **Volume** curve (the red curve) from '0' on the y axis up to '1'</span></span>
3. <span data-ttu-id="4f384-145">Per regolare la forma della curva del **volume** in modo che sia piatta, trascinare il controllo forma curva bianca in modo che sia parallelo all'asse X</span><span class="sxs-lookup"><span data-stu-id="4f384-145">To adjust the shape of the **Volume** curve to be flat, drag the white curve shape control to be parallel to the X axis</span></span>

<span data-ttu-id="4f384-146">Una volta apportate queste modifiche, la sezione **impostazioni audio 3D** delle proprietà di **origine audio** del **PressableButtonHoloLens2** sarà simile alla seguente:</span><span class="sxs-lookup"><span data-stu-id="4f384-146">After these changes, the **3D Sound Settings** section of the **Audio Source** properties of the **PressableButtonHoloLens2** will look like this:</span></span>

![Impostazioni suono 3D pulsante](images/spatial-audio/button-3d-sound-settings.png)

## <a name="testing-the-spatialize-audio"></a><span data-ttu-id="4f384-148">Test dell'audio spatialize</span><span class="sxs-lookup"><span data-stu-id="4f384-148">Testing the spatialize audio</span></span>

<span data-ttu-id="4f384-149">Provare a testare i nuovi suoni di interazione con i pulsanti spaziali:</span><span class="sxs-lookup"><span data-stu-id="4f384-149">Feel free to test out the new spatialized button interaction sounds:</span></span>

* <span data-ttu-id="4f384-150">Immettere la modalità di gioco nell'editor di Unity, idealmente con un esempio di audio con loop nella scena</span><span class="sxs-lookup"><span data-stu-id="4f384-150">Enter game mode in the Unity editor, ideally with a looped audio sample in the scene</span></span>
* <span data-ttu-id="4f384-151">Spostare l'oggetto con l'origine audio da sinistra a destra e confrontare con e senza la funzionalità audio spaziale abilitata.</span><span class="sxs-lookup"><span data-stu-id="4f384-151">Move the object with the audio source from left to right and compare with and without spatial audio enabled.</span></span> <span data-ttu-id="4f384-152">È possibile modificare le impostazioni di origine audio per i test:</span><span class="sxs-lookup"><span data-stu-id="4f384-152">You can change the Audio Source settings for testing by:</span></span>
    * <span data-ttu-id="4f384-153">Trasferimento della proprietà di Blend spaziale tra 0-1 (audio 2D non spaziale e 3D con spaziali)</span><span class="sxs-lookup"><span data-stu-id="4f384-153">Moving the Spatial Blend property between 0 - 1 (2D non-spatialized and 3D spatialized sound)</span></span>
    * <span data-ttu-id="4f384-154">Verifica e deselezione della proprietà Spatialize</span><span class="sxs-lookup"><span data-stu-id="4f384-154">Checking and unchecking the Spatialize property</span></span>

## <a name="next-steps"></a><span data-ttu-id="4f384-155">Passaggi successivi</span><span class="sxs-lookup"><span data-stu-id="4f384-155">Next steps</span></span>

<span data-ttu-id="4f384-156">Provare l'app in un HoloLens 2 o nell'editor di Unity.</span><span class="sxs-lookup"><span data-stu-id="4f384-156">Try out your app on a HoloLens 2, or in the Unity editor.</span></span> <span data-ttu-id="4f384-157">Nell'app è possibile toccare il pulsante e sentire i suoni di interazione dei pulsanti spaziali.</span><span class="sxs-lookup"><span data-stu-id="4f384-157">In the app, you can touch the button and hear the spatialized button interaction sounds.</span></span>

<span data-ttu-id="4f384-158">Quando si esegue il test nell'editor di Unity, premere la barra spaziatrice e scorrere con la rotellina di scorrimento per attivare la simulazione manuale.</span><span class="sxs-lookup"><span data-stu-id="4f384-158">When testing in the Unity editor, press the space bar and scroll with the scroll wheel to activate hand simulation.</span></span> <span data-ttu-id="4f384-159">Per ulteriori informazioni, vedere la [documentazione di MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html#using-the-in-editor-hand-input-simulation-to-test-a-scene).</span><span class="sxs-lookup"><span data-stu-id="4f384-159">For more info, see the [MRTK documentation](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html#using-the-in-editor-hand-input-simulation-to-test-a-scene).</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="4f384-160">Capitolo 3</span><span class="sxs-lookup"><span data-stu-id="4f384-160">Chapter 3</span></span>](unity-spatial-audio-ch3.md)


---
title: Input vocale in Unreal
description: Informazioni su come configurare e usare l'input vocale, i mapping vocale e il riconoscimento in app Real realtà mista per i dispositivi HoloLens 2.
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
keywords: Realtà mista di Windows, Unreal, Unreal Engine 4, UE4, HoloLens 2, Voice, input vocale, riconoscimento vocale, realtà mista, sviluppo, funzionalità, documentazione, guide, ologrammi, sviluppo di giochi, cuffie per realtà mista, cuffia di realtà mista di Windows, Headset della realtà virtuale
ms.openlocfilehash: 466b41c522e95f9fe3d618ad221dde8ccd925634
ms.sourcegitcommit: a688bf0f1b796e4860f8252e852be79053937088
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/14/2021
ms.locfileid: "98205836"
---
# <a name="voice-input-in-unreal"></a><span data-ttu-id="3b82e-104">Input vocale in Unreal</span><span class="sxs-lookup"><span data-stu-id="3b82e-104">Voice Input in Unreal</span></span>

<span data-ttu-id="3b82e-105">L'input vocale in Unreal consente di interagire con un ologramma senza dover usare i movimenti della mano ed è supportato solo HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="3b82e-105">Voice input in Unreal allows you to interact with a hologram without having to use hand gestures and is only supported HoloLens 2.</span></span> <span data-ttu-id="3b82e-106">L'input vocale in HoloLens 2 è alimentato dallo stesso motore che supporta la sintesi vocale in tutte le altre app di Windows universale, ma Unreal usa un motore più limitato per elaborare l'input vocale.</span><span class="sxs-lookup"><span data-stu-id="3b82e-106">Voice input on HoloLens 2 is powered by the same engine that supports speech in all other Universal Windows Apps, but Unreal uses a more limited engine to process voice input.</span></span> <span data-ttu-id="3b82e-107">In questo modo è possibile limitare le funzionalità di input vocali in Unreal ai mapping di riconoscimento vocale predefiniti, descritte nelle sezioni seguenti.</span><span class="sxs-lookup"><span data-stu-id="3b82e-107">This limits voice input features in Unreal to predefined speech mappings, which are covered in the following sections.</span></span> 

## <a name="enabling-speech-recognition"></a><span data-ttu-id="3b82e-108">Abilitazione del riconoscimento vocale</span><span class="sxs-lookup"><span data-stu-id="3b82e-108">Enabling Speech Recognition</span></span>

<span data-ttu-id="3b82e-109">Se si usa un plug-in realtà misto di Windows, l'input vocale non richiede alcuna API della realtà mista di Windows speciale; si basa sull'API di mapping di [input](https://docs.unrealengine.com/Gameplay/Input/index.html) Unreal Engine 4 esistente.</span><span class="sxs-lookup"><span data-stu-id="3b82e-109">If you use Windows Mixed Reality Plugin, Voice input doesn’t require any special Windows Mixed Reality APIs; it's built on the existing Unreal Engine 4 [Input](https://docs.unrealengine.com/Gameplay/Input/index.html) mapping API.</span></span> <span data-ttu-id="3b82e-110">Se si usa OpenXR, è necessario installare anche il plug-in [Microsoft OpenXR](https://github.com/microsoft/Microsoft-OpenXR-Unreal).</span><span class="sxs-lookup"><span data-stu-id="3b82e-110">If you use OpenXR, you should additionally install [Microsoft OpenXR plugin](https://github.com/microsoft/Microsoft-OpenXR-Unreal).</span></span> 

<span data-ttu-id="3b82e-111">Per abilitare il riconoscimento vocale in HoloLens:</span><span class="sxs-lookup"><span data-stu-id="3b82e-111">To enable speech recognition on HoloLens:</span></span>
1. <span data-ttu-id="3b82e-112">Selezionare **Impostazioni progetto > piattaforma > funzionalità di > HoloLens** e abilitare il **microfono**.</span><span class="sxs-lookup"><span data-stu-id="3b82e-112">Select **Project Settings > Platform > HoloLens > Capabilities** and enable **Microphone**.</span></span> 
2. <span data-ttu-id="3b82e-113">Il riconoscimento vocale è stato abilitato in **impostazioni > Privacy > vocale** e selezionare **inglese**.</span><span class="sxs-lookup"><span data-stu-id="3b82e-113">Enabled speech recognition in **Settings > Privacy > Speech** and select **English**.</span></span>

> [!NOTE]
> <span data-ttu-id="3b82e-114">Il riconoscimento vocale funziona sempre nella lingua di visualizzazione di Windows configurata nell'app **Impostazioni** .</span><span class="sxs-lookup"><span data-stu-id="3b82e-114">Speech recognition always functions in the Windows display language configured in the **Settings** app.</span></span> <span data-ttu-id="3b82e-115">È inoltre consigliabile abilitare il **riconoscimento vocale online** per la qualità del servizio migliore.</span><span class="sxs-lookup"><span data-stu-id="3b82e-115">It’s recommended that you also enable **Online speech recognition** for the best service quality.</span></span>

![Impostazioni di riconoscimento vocale Windows](images/unreal/speech-recognition-settings.png)

3. <span data-ttu-id="3b82e-117">Una finestra di dialogo viene visualizzata quando l'applicazione inizia per la prima volta a richiedere se si vuole abilitare il microfono.</span><span class="sxs-lookup"><span data-stu-id="3b82e-117">A dialog will show up when the application first starts to ask if you want to enable the microphone.</span></span> <span data-ttu-id="3b82e-118">Se **si seleziona Sì** , viene avviato l'input vocale nell'app.</span><span class="sxs-lookup"><span data-stu-id="3b82e-118">Selecting **Yes** starts voice input in the app.</span></span>

## <a name="adding-speech-mappings"></a><span data-ttu-id="3b82e-119">Aggiunta di mapping vocale</span><span class="sxs-lookup"><span data-stu-id="3b82e-119">Adding Speech Mappings</span></span>

<span data-ttu-id="3b82e-120">La connessione vocale all'azione è un passaggio importante quando si usa l'input vocale.</span><span class="sxs-lookup"><span data-stu-id="3b82e-120">Connecting speech to action is an important step when using voice input.</span></span> <span data-ttu-id="3b82e-121">Questi mapping monitorano l'app per le parole chiave vocali che un utente potrebbe pronunciare, quindi avviare un'azione collegata.</span><span class="sxs-lookup"><span data-stu-id="3b82e-121">These mappings monitor the app for speech keywords that a user might say, then fire off a linked action.</span></span> <span data-ttu-id="3b82e-122">È possibile trovare mapping vocale per:</span><span class="sxs-lookup"><span data-stu-id="3b82e-122">You can find Speech Mappings by:</span></span>
1. <span data-ttu-id="3b82e-123">Selezionare **modifica > impostazioni progetto**, scorrere fino alla sezione **motore** e fare clic su **input**.</span><span class="sxs-lookup"><span data-stu-id="3b82e-123">Selecting **Edit > Project Settings**, scrolling to the **Engine** section, and clicking **Input**.</span></span>

<span data-ttu-id="3b82e-124">Per aggiungere un nuovo mapping vocale per un comando Jump:</span><span class="sxs-lookup"><span data-stu-id="3b82e-124">To add a new Speech Mapping for a jump command:</span></span>
1. <span data-ttu-id="3b82e-125">Selezionare l' **+** icona accanto agli **elementi della matrice** e compilare i valori seguenti:</span><span class="sxs-lookup"><span data-stu-id="3b82e-125">Select the **+** icon next to **Array elements** and fill out the following values:</span></span>
    * <span data-ttu-id="3b82e-126">**jumpWord** per **nome azione**</span><span class="sxs-lookup"><span data-stu-id="3b82e-126">**jumpWord** for **Action Name**</span></span>
    * <span data-ttu-id="3b82e-127">**passa** alla **parola chiave Speech**</span><span class="sxs-lookup"><span data-stu-id="3b82e-127">**jump** for **Speech Keyword**</span></span>

> [!NOTE]
> <span data-ttu-id="3b82e-128">Tutte le parole o le frasi brevi possono essere utilizzate come parola chiave.</span><span class="sxs-lookup"><span data-stu-id="3b82e-128">Any English word(s) or short sentence(s) can be used as a keyword.</span></span> 

![Impostazioni di input del motore UE4](images/unreal/engine-input.png)

<span data-ttu-id="3b82e-130">I mapping vocale possono essere usati come componenti di input come mapping di azioni o assi o come nodi del progetto nel grafico eventi.</span><span class="sxs-lookup"><span data-stu-id="3b82e-130">Speech Mappings can be used as Input components like Action or Axis Mappings or as blueprint nodes in the Event Graph.</span></span> <span data-ttu-id="3b82e-131">Ad esempio, è possibile collegare il comando Jump per stampare due log diversi a seconda del momento in cui viene pronunciata la parola:</span><span class="sxs-lookup"><span data-stu-id="3b82e-131">For example, you could link the jump command to print out two different logs depending on when the word is spoken:</span></span>

1. <span data-ttu-id="3b82e-132">Fare doppio clic su un progetto per aprirlo nel **grafico eventi**.</span><span class="sxs-lookup"><span data-stu-id="3b82e-132">Double-click a blueprint to open it in the **Event Graph**.</span></span>
2. <span data-ttu-id="3b82e-133">**Fare clic con il pulsante destro del mouse** e cercare il **nome dell'azione** del mapping vocale (in questo caso **JumpWord**), quindi premere **invio** per aggiungere un nodo **azione di input** al grafico.</span><span class="sxs-lookup"><span data-stu-id="3b82e-133">**Right-click** and search for the **Action Name** of your speech mapping (in this case **jumpWord**), then hit **Enter** to add an **Input Action** node to the graph.</span></span>
3. <span data-ttu-id="3b82e-134">Trascinare e rilasciare il pin **premuto** nel nodo della **stringa di stampa** come illustrato nell'immagine seguente.</span><span class="sxs-lookup"><span data-stu-id="3b82e-134">Drag and drop the **Pressed** pin to **Print String** node as shown in the image below.</span></span> <span data-ttu-id="3b82e-135">È possibile lasciare vuoto il pin **rilasciato** e non eseguire alcuna operazione per i mapping vocale.</span><span class="sxs-lookup"><span data-stu-id="3b82e-135">You can leave the **Released** pin empty, it won't execute anything for speech mappings.</span></span>
 
![Azione semplice per la voce](images/unreal/voice-input-img-03.png)

4. <span data-ttu-id="3b82e-137">Riprodurre l'app, pronunciare il Word **Jump** e guardare la console per stampare i log.</span><span class="sxs-lookup"><span data-stu-id="3b82e-137">Play the app, say the word **jump**, and watch the console print out the logs!</span></span>

<span data-ttu-id="3b82e-138">Questa è tutta la configurazione necessaria per iniziare ad aggiungere input voce alle app HoloLens in Unreal.</span><span class="sxs-lookup"><span data-stu-id="3b82e-138">That's all the setup you'll need to start adding voice input to your HoloLens apps in Unreal.</span></span> <span data-ttu-id="3b82e-139">È possibile trovare altre informazioni sulla voce e sull'interattività nei collegamenti seguenti e assicurarsi di considerare l'esperienza che si sta creando per gli utenti.</span><span class="sxs-lookup"><span data-stu-id="3b82e-139">You can find more information on speech and interactivity at the links below, and be sure to think about the experience you're creating for your users.</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="3b82e-140">Successivo checkpoint di sviluppo</span><span class="sxs-lookup"><span data-stu-id="3b82e-140">Next Development Checkpoint</span></span>

<span data-ttu-id="3b82e-141">Se si sta seguendo il percorso di sviluppo non reale, si sta per iniziare a esplorare le funzionalità e le API della piattaforma di realtà mista:</span><span class="sxs-lookup"><span data-stu-id="3b82e-141">If you're following the Unreal development journey we've laid out, you're next task is exploring the Mixed Reality platform capabilities and APIs:</span></span> 

> [!div class="nextstepaction"]
> [<span data-ttu-id="3b82e-142">Fotocamera HoloLens</span><span class="sxs-lookup"><span data-stu-id="3b82e-142">HoloLens camera</span></span>](unreal-hololens-camera.md)

<span data-ttu-id="3b82e-143">È sempre possibile tornare ai [checkpoint per lo sviluppo con Unreal](unreal-development-overview.md#2-core-building-blocks) in qualsiasi momento.</span><span class="sxs-lookup"><span data-stu-id="3b82e-143">You can always go back to the [Unreal development checkpoints](unreal-development-overview.md#2-core-building-blocks) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="3b82e-144">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="3b82e-144">See also</span></span>
* [<span data-ttu-id="3b82e-145">Input vocale</span><span class="sxs-lookup"><span data-stu-id="3b82e-145">Voice Input</span></span>](../../design/voice-input.md)
* [<span data-ttu-id="3b82e-146">Sguardo e commit</span><span class="sxs-lookup"><span data-stu-id="3b82e-146">Gaze and commit</span></span>](../../design/gaze-and-commit.md)
* [<span data-ttu-id="3b82e-147">Interazioni istintive</span><span class="sxs-lookup"><span data-stu-id="3b82e-147">Instinctual interactions</span></span>](../../design/interaction-fundamentals.md)


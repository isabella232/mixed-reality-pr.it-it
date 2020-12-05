---
title: Input vocale
description: Esercitazione sulla configurazione e l'uso dell'input vocale in HoloLens 2 e Unreal Engine
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
keywords: Realtà mista di Windows, Unreal, Unreal Engine 4, UE4, HoloLens 2, Voice, input vocale, riconoscimento vocale, realtà mista, sviluppo, funzionalità, documentazione, guide, ologrammi, sviluppo di giochi, cuffie per realtà mista, cuffia di realtà mista di Windows, Headset della realtà virtuale
ms.openlocfilehash: 504a2d978e3c9bc698e8edd11ea8a4d6be13795a
ms.sourcegitcommit: 32cb81eee976e73cd661c2b347691c37865a60bc
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/04/2020
ms.locfileid: "96609752"
---
# <a name="voice-input-in-unreal"></a><span data-ttu-id="16faf-104">Input vocale in Unreal</span><span class="sxs-lookup"><span data-stu-id="16faf-104">Voice Input in Unreal</span></span>

<span data-ttu-id="16faf-105">L'input vocale in Unreal consente di interagire con un ologramma senza dover usare i movimenti della mano ed è supportato solo HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="16faf-105">Voice input in Unreal allows you to interact with a hologram without having to use hand gestures and is only supported HoloLens 2.</span></span> <span data-ttu-id="16faf-106">L'input vocale in HoloLens 2 è alimentato dallo stesso motore che supporta la sintesi vocale in tutte le altre app di Windows universale, ma Unreal usa un motore più limitato per elaborare l'input vocale.</span><span class="sxs-lookup"><span data-stu-id="16faf-106">Voice input on HoloLens 2 is powered by the same engine that supports speech in all other Universal Windows Apps, but Unreal uses a more limited engine to process voice input.</span></span> <span data-ttu-id="16faf-107">In questo modo è possibile limitare le funzionalità di input vocali in Unreal ai mapping di riconoscimento vocale predefiniti, descritte nelle sezioni seguenti.</span><span class="sxs-lookup"><span data-stu-id="16faf-107">This limits voice input features in Unreal to predefined speech mappings, which are covered in the following sections.</span></span> 

## <a name="enabling-speech-recognition"></a><span data-ttu-id="16faf-108">Abilitazione del riconoscimento vocale</span><span class="sxs-lookup"><span data-stu-id="16faf-108">Enabling Speech Recognition</span></span>

<span data-ttu-id="16faf-109">Per abilitare il riconoscimento vocale in HoloLens:</span><span class="sxs-lookup"><span data-stu-id="16faf-109">To enable speech recognition on HoloLens:</span></span>
1. <span data-ttu-id="16faf-110">Selezionare **Impostazioni progetto > piattaforma > funzionalità di > HoloLens** e abilitare il **microfono**.</span><span class="sxs-lookup"><span data-stu-id="16faf-110">Select **Project Settings > Platform > HoloLens > Capabilities** and enable **Microphone**.</span></span> 
2. <span data-ttu-id="16faf-111">Il riconoscimento vocale è stato abilitato in **impostazioni > Privacy > vocale** e selezionare **inglese**.</span><span class="sxs-lookup"><span data-stu-id="16faf-111">Enabled speech recognition in **Settings > Privacy > Speech** and select **English**.</span></span>

> [!NOTE]
> <span data-ttu-id="16faf-112">Il riconoscimento vocale funziona sempre nella lingua di visualizzazione di Windows configurata nell'app **Impostazioni** .</span><span class="sxs-lookup"><span data-stu-id="16faf-112">Speech recognition always functions in the Windows display language configured in the **Settings** app.</span></span> <span data-ttu-id="16faf-113">È inoltre consigliabile abilitare il **riconoscimento vocale online** per la qualità del servizio migliore.</span><span class="sxs-lookup"><span data-stu-id="16faf-113">It’s recommended that you also enable **Online speech recognition** for the best service quality.</span></span>

![Impostazioni di riconoscimento vocale Windows](images/unreal/speech-recognition-settings.png)

3. <span data-ttu-id="16faf-115">Una finestra di dialogo viene visualizzata quando l'applicazione inizia per la prima volta a richiedere se si vuole abilitare il microfono.</span><span class="sxs-lookup"><span data-stu-id="16faf-115">A dialog will show up when the application first starts to ask if you want to enable the microphone.</span></span> <span data-ttu-id="16faf-116">Se **si seleziona Sì** , viene avviato l'input vocale nell'app.</span><span class="sxs-lookup"><span data-stu-id="16faf-116">Selecting **Yes** starts voice input in the app.</span></span>

<span data-ttu-id="16faf-117">L'input vocale non richiede alcuna API della realtà mista di Windows speciale; si basa sull'API di mapping di [input](https://docs.unrealengine.com/Gameplay/Input/index.html) Unreal Engine 4 esistente.</span><span class="sxs-lookup"><span data-stu-id="16faf-117">Voice input doesn’t require any special Windows Mixed Reality APIs; it's built on the existing Unreal Engine 4 [Input](https://docs.unrealengine.com/Gameplay/Input/index.html) mapping API.</span></span> 

## <a name="adding-speech-mappings"></a><span data-ttu-id="16faf-118">Aggiunta di mapping vocale</span><span class="sxs-lookup"><span data-stu-id="16faf-118">Adding Speech Mappings</span></span>

<span data-ttu-id="16faf-119">La connessione vocale all'azione è un passaggio importante quando si usa l'input vocale.</span><span class="sxs-lookup"><span data-stu-id="16faf-119">Connecting speech to action is an important step when using voice input.</span></span> <span data-ttu-id="16faf-120">Questi mapping monitorano l'app per le parole chiave vocali che un utente potrebbe pronunciare, quindi avviare un'azione collegata.</span><span class="sxs-lookup"><span data-stu-id="16faf-120">These mappings monitor the app for speech keywords that a user might say, then fire off a linked action.</span></span> <span data-ttu-id="16faf-121">È possibile trovare mapping vocale per:</span><span class="sxs-lookup"><span data-stu-id="16faf-121">You can find Speech Mappings by:</span></span>
1. <span data-ttu-id="16faf-122">Selezionare **modifica > impostazioni progetto**, scorrere fino alla sezione **motore** e fare clic su **input**.</span><span class="sxs-lookup"><span data-stu-id="16faf-122">Selecting **Edit > Project Settings**, scrolling to the **Engine** section, and clicking **Input**.</span></span>

<span data-ttu-id="16faf-123">Per aggiungere un nuovo mapping vocale per un comando Jump:</span><span class="sxs-lookup"><span data-stu-id="16faf-123">To add a new Speech Mapping for a jump command:</span></span>
1. <span data-ttu-id="16faf-124">Selezionare l' **+** icona accanto agli **elementi della matrice** e compilare i valori seguenti:</span><span class="sxs-lookup"><span data-stu-id="16faf-124">Select the **+** icon next to **Array elements** and fill out the following values:</span></span>
    * <span data-ttu-id="16faf-125">**jumpWord** per **nome azione**</span><span class="sxs-lookup"><span data-stu-id="16faf-125">**jumpWord** for **Action Name**</span></span>
    * <span data-ttu-id="16faf-126">**passa** alla **parola chiave Speech**</span><span class="sxs-lookup"><span data-stu-id="16faf-126">**jump** for **Speech Keyword**</span></span>

> [!NOTE]
> <span data-ttu-id="16faf-127">Tutte le parole o le frasi brevi possono essere utilizzate come parola chiave.</span><span class="sxs-lookup"><span data-stu-id="16faf-127">Any English word(s) or short sentence(s) can be used as a keyword.</span></span> 

![Impostazioni di input del motore UE4](images/unreal/engine-input.png)

<span data-ttu-id="16faf-129">I mapping vocale possono essere usati come componenti di input come mapping di azioni o assi o come nodi del progetto nel grafico eventi.</span><span class="sxs-lookup"><span data-stu-id="16faf-129">Speech Mappings can be used as Input components like Action or Axis Mappings or as blueprint nodes in the Event Graph.</span></span> <span data-ttu-id="16faf-130">Ad esempio, è possibile collegare il comando Jump per stampare due log diversi a seconda del momento in cui viene pronunciata la parola:</span><span class="sxs-lookup"><span data-stu-id="16faf-130">For example, you could link the jump command to print out two different logs depending on when the word is spoken:</span></span>

1. <span data-ttu-id="16faf-131">Fare doppio clic su un progetto per aprirlo nel **grafico eventi**.</span><span class="sxs-lookup"><span data-stu-id="16faf-131">Double-click a blueprint to open it in the **Event Graph**.</span></span>
2. <span data-ttu-id="16faf-132">**Fare clic con il pulsante destro del mouse** e cercare il **nome dell'azione** del mapping vocale (in questo caso **JumpWord**), quindi premere **invio** per aggiungere un nodo **azione di input** al grafico.</span><span class="sxs-lookup"><span data-stu-id="16faf-132">**Right-click** and search for the **Action Name** of your speech mapping (in this case **jumpWord**), then hit **Enter** to add an **Input Action** node to the graph.</span></span>
3. <span data-ttu-id="16faf-133">Trascinare e rilasciare il pin **premuto** nel nodo della **stringa di stampa** come illustrato nell'immagine seguente.</span><span class="sxs-lookup"><span data-stu-id="16faf-133">Drag and drop the **Pressed** pin to **Print String** node as shown in the image below.</span></span> <span data-ttu-id="16faf-134">È possibile lasciare vuoto il pin **rilasciato** e non eseguire alcuna operazione per i mapping vocale.</span><span class="sxs-lookup"><span data-stu-id="16faf-134">You can leave the **Released** pin empty, it won't execute anything for speech mappings.</span></span>
 
![Azione semplice per la voce](images/unreal/voice-input-img-03.png)

4. <span data-ttu-id="16faf-136">Riprodurre l'app, pronunciare il Word **Jump** e guardare la console per stampare i log.</span><span class="sxs-lookup"><span data-stu-id="16faf-136">Play the app, say the word **jump**, and watch the console print out the logs!</span></span>

<span data-ttu-id="16faf-137">Questa è tutta la configurazione necessaria per iniziare ad aggiungere input voce alle app HoloLens in Unreal.</span><span class="sxs-lookup"><span data-stu-id="16faf-137">That's all the setup you'll need to start adding voice input to your HoloLens apps in Unreal.</span></span> <span data-ttu-id="16faf-138">È possibile trovare altre informazioni sulla voce e sull'interattività nei collegamenti seguenti e assicurarsi di considerare l'esperienza che si sta creando per gli utenti.</span><span class="sxs-lookup"><span data-stu-id="16faf-138">You can find more information on speech and interactivity at the links below, and be sure to think about the experience you're creating for your users.</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="16faf-139">Successivo checkpoint di sviluppo</span><span class="sxs-lookup"><span data-stu-id="16faf-139">Next Development Checkpoint</span></span>

<span data-ttu-id="16faf-140">Se si sta seguendo il percorso di sviluppo non reale, si sta per iniziare a esplorare le funzionalità e le API della piattaforma di realtà mista:</span><span class="sxs-lookup"><span data-stu-id="16faf-140">If you're following the Unreal development journey we've laid out, you're next task is exploring the Mixed Reality platform capabilities and APIs:</span></span> 

> [!div class="nextstepaction"]
> [<span data-ttu-id="16faf-141">Fotocamera HoloLens</span><span class="sxs-lookup"><span data-stu-id="16faf-141">HoloLens camera</span></span>](unreal-hololens-camera.md)

<span data-ttu-id="16faf-142">È sempre possibile tornare ai [checkpoint per lo sviluppo con Unreal](unreal-development-overview.md#2-core-building-blocks) in qualsiasi momento.</span><span class="sxs-lookup"><span data-stu-id="16faf-142">You can always go back to the [Unreal development checkpoints](unreal-development-overview.md#2-core-building-blocks) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="16faf-143">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="16faf-143">See also</span></span>
* [<span data-ttu-id="16faf-144">Input vocale</span><span class="sxs-lookup"><span data-stu-id="16faf-144">Voice Input</span></span>](../../design/voice-input.md)
* [<span data-ttu-id="16faf-145">Sguardo e commit</span><span class="sxs-lookup"><span data-stu-id="16faf-145">Gaze and commit</span></span>](../../design/gaze-and-commit.md)
* [<span data-ttu-id="16faf-146">Interazioni istintive</span><span class="sxs-lookup"><span data-stu-id="16faf-146">Instinctual interactions</span></span>](../../design/interaction-fundamentals.md)


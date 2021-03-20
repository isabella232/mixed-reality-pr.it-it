---
title: Dettatura
description: Docummentation su come registrare clip audio e ottenere una trascrizione in MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: 15ee2b5f636e9f1e0a235b1e7fdef15cda28ed36
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2021
ms.locfileid: "104680614"
---
# <a name="dictation"></a><span data-ttu-id="849fe-104">Dettatura</span><span class="sxs-lookup"><span data-stu-id="849fe-104">Dictation</span></span>

<span data-ttu-id="849fe-105">La dettatura consente agli utenti di registrare clip audio e ottenere una trascrizione.</span><span class="sxs-lookup"><span data-stu-id="849fe-105">Dictation allows users to record audio clips and obtain a transcription.</span></span> <span data-ttu-id="849fe-106">Per usarlo, verificare che nel *profilo di sistema di input* sia registrato un sistema di dettatura.</span><span class="sxs-lookup"><span data-stu-id="849fe-106">To use it make sure that a dictation system is registered in the *Input System Profile*.</span></span> <span data-ttu-id="849fe-107">Il **provider di input di dettatura di Windows** è il sistema di dettatura fornito in modalità predefinita, ma è possibile creare sistemi di dettatura alternativi [`IMixedRealityDictationSystem`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityDictationSystem) .</span><span class="sxs-lookup"><span data-stu-id="849fe-107">**Windows Dictation Input Provider** is the dictation system provided out of the box but alternative dictation systems can be created implementing [`IMixedRealityDictationSystem`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityDictationSystem).</span></span>

## <a name="requirements"></a><span data-ttu-id="849fe-108">Requisiti</span><span class="sxs-lookup"><span data-stu-id="849fe-108">Requirements</span></span>

<span data-ttu-id="849fe-109">Il sistema di dettatura USA [DictationRecognizer](https://docs.unity3d.com/ScriptReference/Windows.Speech.DictationRecognizer.html) di Unity, che a sua volta usa le API di riconoscimento vocale di Windows sottostanti per gestire la dettatura.</span><span class="sxs-lookup"><span data-stu-id="849fe-109">The dictation system uses Unity's [DictationRecognizer](https://docs.unity3d.com/ScriptReference/Windows.Speech.DictationRecognizer.html) which itself uses the underlying Windows speech APIs for handling dictation.</span></span> <span data-ttu-id="849fe-110">Si noti che questo implica che questa funzionalità è presente solo nelle piattaforme basate su Windows.</span><span class="sxs-lookup"><span data-stu-id="849fe-110">Note that this implies that this feature is only present on Windows-based platforms.</span></span>

<span data-ttu-id="849fe-111">L'utilizzo del sistema di dettatura richiede le funzionalità dell'applicazione "client Internet" e "microfono" nella [sezione PlayerSettings-capabilities](https://docs.unity3d.com/Manual/class-PlayerSettingsWSA.html#Capabilities).</span><span class="sxs-lookup"><span data-stu-id="849fe-111">Usage of the Dictation system requires both the "Internet Client" and "Microphone" application capabilities in the [PlayerSettings - Capabilities section](https://docs.unity3d.com/Manual/class-PlayerSettingsWSA.html#Capabilities).</span></span>
<span data-ttu-id="849fe-112">Vedere la [documentazione di realtà mista di Windows](https://docs.microsoft.com/windows/mixed-reality/voice-input-in-unity#dictation) per altri dettagli sull'input vocale in Unity.</span><span class="sxs-lookup"><span data-stu-id="849fe-112">See [Windows Mixed Reality Documentation](https://docs.microsoft.com/windows/mixed-reality/voice-input-in-unity#dictation) for more details on voice input in Unity.</span></span>

## <a name="configuration"></a><span data-ttu-id="849fe-113">Configurazione</span><span class="sxs-lookup"><span data-stu-id="849fe-113">Configuration</span></span>

<img src="../images/input/DictationDataProvider.png" width="80%" class="center" alt="Dictation Data Provider">

<span data-ttu-id="849fe-114">Dopo aver configurato un servizio di dettatura, è possibile usare lo [`DictationHandler`](xref:Microsoft.MixedReality.Toolkit.Input.DictationHandler) script per avviare e arrestare la registrazione delle sessioni e ottenere i risultati della trascrizione tramite UnityEvents.</span><span class="sxs-lookup"><span data-stu-id="849fe-114">Once you have a dictation service set up, you can use the [`DictationHandler`](xref:Microsoft.MixedReality.Toolkit.Input.DictationHandler) script to start and stop recording sessions and obtain the transcription results via UnityEvents.</span></span>

<img src="../images/input/DictationHandler.png" width="80%" class="center" alt="Dictation Handler">

- <span data-ttu-id="849fe-115">L' **ipotesi di dettatura** viene generata quando l'utente parla con trascrizioni iniziali e approssimative dell'audio acquisite finora.</span><span class="sxs-lookup"><span data-stu-id="849fe-115">**Dictation Hypothesis** is raised as the user speaks with early, rough transcriptions of the audio captured so far.</span></span>
- <span data-ttu-id="849fe-116">Il **risultato della dettatura** viene generato alla fine di ogni frase, ad esempio quando l'utente esegue la sospensione, con la trascrizione finale dell'audio acquisita finora.</span><span class="sxs-lookup"><span data-stu-id="849fe-116">**Dictation Result** is raised at the end of each sentence (i.e. when the user pauses) with the final transcription of the audio captured so far.</span></span>
- <span data-ttu-id="849fe-117">La **Dettatura completa** viene generata alla fine della sessione di registrazione con la trascrizione finale completa dell'audio.</span><span class="sxs-lookup"><span data-stu-id="849fe-117">**Dictation Complete** is raised at the end of the recording session with the full, final transcription of the audio.</span></span>
- <span data-ttu-id="849fe-118">L' **errore di dettatura** viene generato per segnalare gli errori nel servizio di dettatura.</span><span class="sxs-lookup"><span data-stu-id="849fe-118">**Dictation Error** is raised to inform of errors in the dictation service.</span></span> <span data-ttu-id="849fe-119">La trascrizione in questo caso contiene una descrizione dell'errore.</span><span class="sxs-lookup"><span data-stu-id="849fe-119">The transcription in this case contains a description of the error.</span></span>

## <a name="example-scene"></a><span data-ttu-id="849fe-120">Scena di esempio</span><span class="sxs-lookup"><span data-stu-id="849fe-120">Example scene</span></span>

<span data-ttu-id="849fe-121">La scena di **Dettatura** in `MRTK/Examples/Demos/Input/Scenes/Dictation` Mostra lo `DictationHandler` script in uso.</span><span class="sxs-lookup"><span data-stu-id="849fe-121">**Dictation** scene in `MRTK/Examples/Demos/Input/Scenes/Dictation` shows the `DictationHandler` script in use.</span></span> <span data-ttu-id="849fe-122">Se è necessario un maggiore controllo, è possibile estendere questo script o creare un'implementazione personalizzata [`IMixedRealityDictationHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityDictationHandler) per ricevere direttamente gli eventi di dettatura.</span><span class="sxs-lookup"><span data-stu-id="849fe-122">If you need more control, you can either extend this script or create your own implementing [`IMixedRealityDictationHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityDictationHandler) to receive dictation events directly.</span></span>

<img src="../images/input/DictationDemo.png" width="80%" class="center" alt="Dictation Demo">

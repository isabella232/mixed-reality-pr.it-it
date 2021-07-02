---
title: Dettatura
description: Documentazione su come registrare clip audio e ottenere una trascrizione in MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: 520a667cc4b41f5e8f4373a7c901eb2458cd2d17
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176471"
---
# <a name="dictation"></a><span data-ttu-id="1ae8c-104">Dettatura</span><span class="sxs-lookup"><span data-stu-id="1ae8c-104">Dictation</span></span>

<span data-ttu-id="1ae8c-105">La dettatura consente agli utenti di registrare clip audio e ottenere una trascrizione.</span><span class="sxs-lookup"><span data-stu-id="1ae8c-105">Dictation allows users to record audio clips and obtain a transcription.</span></span> <span data-ttu-id="1ae8c-106">Per usarlo, assicurarsi che un sistema di dettatura sia registrato nel profilo *di sistema di input*.</span><span class="sxs-lookup"><span data-stu-id="1ae8c-106">To use it make sure that a dictation system is registered in the *Input System Profile*.</span></span> <span data-ttu-id="1ae8c-107">**Windows provider di input** di dettatura è il sistema di dettatura fornito in modo predefinito, ma è possibile creare sistemi di dettatura alternativi implementando [`IMixedRealityDictationSystem`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityDictationSystem) .</span><span class="sxs-lookup"><span data-stu-id="1ae8c-107">**Windows Dictation Input Provider** is the dictation system provided out of the box but alternative dictation systems can be created implementing [`IMixedRealityDictationSystem`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityDictationSystem).</span></span>

## <a name="requirements"></a><span data-ttu-id="1ae8c-108">Requisiti</span><span class="sxs-lookup"><span data-stu-id="1ae8c-108">Requirements</span></span>

<span data-ttu-id="1ae8c-109">Il sistema di dettatura usa [DictationRecognizer](https://docs.unity3d.com/ScriptReference/Windows.Speech.DictationRecognizer.html) di Unity, che usa a sua Windows api vocali sottostanti per la gestione della dettatura.</span><span class="sxs-lookup"><span data-stu-id="1ae8c-109">The dictation system uses Unity's [DictationRecognizer](https://docs.unity3d.com/ScriptReference/Windows.Speech.DictationRecognizer.html) which itself uses the underlying Windows speech APIs for handling dictation.</span></span> <span data-ttu-id="1ae8c-110">Si noti che ciò implica che questa funzionalità è presente solo nelle Windows basate su dispositivi mobili.</span><span class="sxs-lookup"><span data-stu-id="1ae8c-110">Note that this implies that this feature is only present on Windows-based platforms.</span></span>

<span data-ttu-id="1ae8c-111">L'utilizzo del sistema di dettatura richiede sia le funzionalità dell'applicazione "Internet Client" che "Microfono" nella sezione [PlayerSettings - Capabilities](https://docs.unity3d.com/Manual/class-PlayerSettingsWSA.html#Capabilities).</span><span class="sxs-lookup"><span data-stu-id="1ae8c-111">Usage of the Dictation system requires both the "Internet Client" and "Microphone" application capabilities in the [PlayerSettings - Capabilities section](https://docs.unity3d.com/Manual/class-PlayerSettingsWSA.html#Capabilities).</span></span>
<span data-ttu-id="1ae8c-112">Per [altri dettagli sull'input](/windows/mixed-reality/voice-input-in-unity#dictation) vocale in Unity, vedere la documentazione di Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="1ae8c-112">See [Windows Mixed Reality Documentation](/windows/mixed-reality/voice-input-in-unity#dictation) for more details on voice input in Unity.</span></span>

## <a name="configuration"></a><span data-ttu-id="1ae8c-113">Configurazione</span><span class="sxs-lookup"><span data-stu-id="1ae8c-113">Configuration</span></span>

<img src="../images/input/DictationDataProvider.png" width="80%" class="center" alt="Data provider">

<span data-ttu-id="1ae8c-114">Dopo aver configurato un servizio di dettatura, è possibile usare lo script per avviare e arrestare la registrazione delle sessioni e ottenere i risultati della trascrizione [`DictationHandler`](xref:Microsoft.MixedReality.Toolkit.Input.DictationHandler) tramite UnityEvents.</span><span class="sxs-lookup"><span data-stu-id="1ae8c-114">Once you have a dictation service set up, you can use the [`DictationHandler`](xref:Microsoft.MixedReality.Toolkit.Input.DictationHandler) script to start and stop recording sessions and obtain the transcription results via UnityEvents.</span></span>

<img src="../images/input/DictationHandler.png" width="80%" alt="Dictation Handler" class="center">

- <span data-ttu-id="1ae8c-115">**L'ipotesi di dettatura** viene generata quando l'utente parla con trascrizioni approssimative e iniziali dell'audio acquisito finora.</span><span class="sxs-lookup"><span data-stu-id="1ae8c-115">**Dictation Hypothesis** is raised as the user speaks with early, rough transcriptions of the audio captured so far.</span></span>
- <span data-ttu-id="1ae8c-116">**Il risultato della dettatura** viene generato alla fine di ogni frase ,ad esempio quando l'utente viene sospeso, con la trascrizione finale dell'audio acquisito finora.</span><span class="sxs-lookup"><span data-stu-id="1ae8c-116">**Dictation Result** is raised at the end of each sentence (i.e. when the user pauses) with the final transcription of the audio captured so far.</span></span>
- <span data-ttu-id="1ae8c-117">**La dettatura completa** viene generata alla fine della sessione di registrazione con la trascrizione finale completa dell'audio.</span><span class="sxs-lookup"><span data-stu-id="1ae8c-117">**Dictation Complete** is raised at the end of the recording session with the full, final transcription of the audio.</span></span>
- <span data-ttu-id="1ae8c-118">**L'errore di** dettatura viene generato per informare degli errori nel servizio di dettatura.</span><span class="sxs-lookup"><span data-stu-id="1ae8c-118">**Dictation Error** is raised to inform of errors in the dictation service.</span></span> <span data-ttu-id="1ae8c-119">La trascrizione in questo caso contiene una descrizione dell'errore.</span><span class="sxs-lookup"><span data-stu-id="1ae8c-119">The transcription in this case contains a description of the error.</span></span>

## <a name="example-scene"></a><span data-ttu-id="1ae8c-120">Scena di esempio</span><span class="sxs-lookup"><span data-stu-id="1ae8c-120">Example scene</span></span>

<span data-ttu-id="1ae8c-121">**La scena di dettatura** in `MRTK/Examples/Demos/Input/Scenes/Dictation` mostra lo script in `DictationHandler` uso.</span><span class="sxs-lookup"><span data-stu-id="1ae8c-121">**Dictation** scene in `MRTK/Examples/Demos/Input/Scenes/Dictation` shows the `DictationHandler` script in use.</span></span> <span data-ttu-id="1ae8c-122">Se è necessario un maggiore controllo, è possibile estendere questo script o creare un'implementazione propria per ricevere direttamente gli [`IMixedRealityDictationHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityDictationHandler) eventi di dettatura.</span><span class="sxs-lookup"><span data-stu-id="1ae8c-122">If you need more control, you can either extend this script or create your own implementing [`IMixedRealityDictationHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityDictationHandler) to receive dictation events directly.</span></span>

<img src="../images/input/DictationDemo.png" width="80%" alt="Dictation Demo" class="center">

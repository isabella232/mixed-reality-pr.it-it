---
title: Input vocale in Unity
description: Informazioni su come Unity espone tre modi per aggiungere input vocale, riconoscimento vocale e dettatura all'Windows Mixed Reality appliazione.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Input vocale, KeywordRecognizer, GrammarRecognizer, microfono, dettatura, voce, visore per realtà mista, visore windows mixed reality, visore per realtà virtuale, MRTK, Mixed Reality Toolkit
ms.openlocfilehash: 6b040443606e05843f85b2f74f5ea812daafba31
ms.sourcegitcommit: e89431d12b5fe480c9bc40e176023798fc35001b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/07/2021
ms.locfileid: "109489201"
---
# <a name="voice-input-in-unity"></a><span data-ttu-id="a02f7-104">Input vocale in Unity</span><span class="sxs-lookup"><span data-stu-id="a02f7-104">Voice input in Unity</span></span>

> [!CAUTION]
> <span data-ttu-id="a02f7-105">Prima di iniziare, è consigliabile usare il plug-in Unity per Cognitive Speech Services SDK.</span><span class="sxs-lookup"><span data-stu-id="a02f7-105">Before starting, consider using the Unity plug-in for the Cognitive Speech Services SDK.</span></span> <span data-ttu-id="a02f7-106">Il plug-in offre risultati migliori per l'accuratezza della voce e un facile accesso alla decodifica vocale, oltre a funzionalità vocali avanzate come dialogo, interazione basata sulle finalità, traduzione, sintesi vocale e riconoscimento vocale in linguaggio naturale.</span><span class="sxs-lookup"><span data-stu-id="a02f7-106">The plugin has better Speech Accuracy results and easy access to speech-to-text decode, as well as advanced speech features like dialog, intent based interaction, translation, text-to-speech synthesis, and natural language speech recognition.</span></span> <span data-ttu-id="a02f7-107">Per iniziare, vedere l'esempio [e la documentazione](/azure/cognitive-services/speech-service/quickstart-csharp-unity).</span><span class="sxs-lookup"><span data-stu-id="a02f7-107">To get started, check out the [sample and documentation](/azure/cognitive-services/speech-service/quickstart-csharp-unity).</span></span>

<span data-ttu-id="a02f7-108">Unity espone tre modi per aggiungere [input vocale](../../design/voice-input.md) all'applicazione Unity, i primi due dei quali sono tipi di PhraseRecognizer:</span><span class="sxs-lookup"><span data-stu-id="a02f7-108">Unity exposes three ways to add [Voice input](../../design/voice-input.md) to your Unity application, the first two of which are types of PhraseRecognizer:</span></span>
* <span data-ttu-id="a02f7-109">Fornisce `KeywordRecognizer` all'app una matrice di comandi stringa per l'ascolto</span><span class="sxs-lookup"><span data-stu-id="a02f7-109">The `KeywordRecognizer` supplies your app with an array of string commands to listen for</span></span>
* <span data-ttu-id="a02f7-110">fornisce `GrammarRecognizer` all'app un file SRGS che definisce una grammatica specifica per l'ascolto</span><span class="sxs-lookup"><span data-stu-id="a02f7-110">The `GrammarRecognizer` gives your app an SRGS file defining a specific grammar to listen for</span></span>
* <span data-ttu-id="a02f7-111">consente all'app di restare in ascolto di qualsiasi parola e fornire all'utente una nota o `DictationRecognizer` un'altra visualizzazione del parlato</span><span class="sxs-lookup"><span data-stu-id="a02f7-111">The `DictationRecognizer` lets your app listen for any word and provide the user with a note or other display of their speech</span></span>

> [!NOTE]
> <span data-ttu-id="a02f7-112">La dettatura e il riconoscimento delle frasi non possono essere gestiti contemporaneamente.</span><span class="sxs-lookup"><span data-stu-id="a02f7-112">Dictation and phrase recognition can't be handled at the same time.</span></span> <span data-ttu-id="a02f7-113">Se è attivo un oggetto GrammarRecognizer o KeywordRecognizer, un oggetto DictationRecognizer non può essere attivo e viceversa.</span><span class="sxs-lookup"><span data-stu-id="a02f7-113">If a GrammarRecognizer or KeywordRecognizer is active, a DictationRecognizer can't be active and vice versa.</span></span>

## <a name="enabling-the-capability-for-voice"></a><span data-ttu-id="a02f7-114">Abilitazione della funzionalità per Voice</span><span class="sxs-lookup"><span data-stu-id="a02f7-114">Enabling the capability for Voice</span></span>

<span data-ttu-id="a02f7-115">La **funzionalità Microfono** deve essere dichiarata perché un'app usi l'input vocale.</span><span class="sxs-lookup"><span data-stu-id="a02f7-115">The **Microphone** capability must be declared for an app to use Voice input.</span></span>
1. <span data-ttu-id="a02f7-116">Nell'editor di Unity passare a **Modifica impostazioni > progetto > Lettore**</span><span class="sxs-lookup"><span data-stu-id="a02f7-116">In the Unity Editor, navigate to **Edit > Project Settings > Player**</span></span>
2. <span data-ttu-id="a02f7-117">Selezionare la **scheda Windows Store**</span><span class="sxs-lookup"><span data-stu-id="a02f7-117">Select the **Windows Store** tab</span></span>
3. <span data-ttu-id="a02f7-118">Nella sezione **Impostazioni di > funzionalità** selezionare la **funzionalità** Microfono</span><span class="sxs-lookup"><span data-stu-id="a02f7-118">In the **Publishing Settings > Capabilities** section, check the **Microphone** capability</span></span>
4. <span data-ttu-id="a02f7-119">Concedere le autorizzazioni all'app per l'accesso al microfono nel dispositivo HoloLens</span><span class="sxs-lookup"><span data-stu-id="a02f7-119">Grant permissions to the app for microphone access on your HoloLens device</span></span>
    * <span data-ttu-id="a02f7-120">Verrà richiesto di eseguire questa operazione all'avvio del dispositivo, ma se si è fatto clic accidentalmente su "no" è possibile modificare le autorizzazioni nelle impostazioni del dispositivo</span><span class="sxs-lookup"><span data-stu-id="a02f7-120">You'll be asked to do this on device startup, but if you accidentally clicked "no" you can change the permissions in the device settings</span></span>

## <a name="phrase-recognition"></a><span data-ttu-id="a02f7-121">Riconoscimento di frasi</span><span class="sxs-lookup"><span data-stu-id="a02f7-121">Phrase Recognition</span></span>

<span data-ttu-id="a02f7-122">Per consentire all'app di restare in ascolto di frasi specifiche pronunciate dall'utente e quindi eseguire alcune azioni, è necessario:</span><span class="sxs-lookup"><span data-stu-id="a02f7-122">To enable your app to listen for specific phrases spoken by the user then take some action, you need to:</span></span>
1. <span data-ttu-id="a02f7-123">Specificare le frasi da ascoltare usando `KeywordRecognizer` o `GrammarRecognizer`</span><span class="sxs-lookup"><span data-stu-id="a02f7-123">Specify which phrases to listen for using a `KeywordRecognizer` or `GrammarRecognizer`</span></span>
2. <span data-ttu-id="a02f7-124">Gestire `OnPhraseRecognized` l'evento ed eseguire un'azione corrispondente alla frase riconosciuta</span><span class="sxs-lookup"><span data-stu-id="a02f7-124">Handle the `OnPhraseRecognized` event and take action corresponding to the phrase recognized</span></span>

### <a name="keywordrecognizer"></a><span data-ttu-id="a02f7-125">KeywordRecognizer</span><span class="sxs-lookup"><span data-stu-id="a02f7-125">KeywordRecognizer</span></span>

<span data-ttu-id="a02f7-126">**Spazio dei nomi:** *UnityEngine.Windows.Speech*</span><span class="sxs-lookup"><span data-stu-id="a02f7-126">**Namespace:** *UnityEngine.Windows.Speech*</span></span><br>
<span data-ttu-id="a02f7-127">**Tipi:** *KeywordRecognizer,* *PhraseRecognizedEventArgs,* *SpeechError,* *SpeechSystemStatus*</span><span class="sxs-lookup"><span data-stu-id="a02f7-127">**Types:** *KeywordRecognizer*, *PhraseRecognizedEventArgs*, *SpeechError*, *SpeechSystemStatus*</span></span>

<span data-ttu-id="a02f7-128">Per salvare alcune sequenze di tasti, sono necessarie alcune istruzioni using:</span><span class="sxs-lookup"><span data-stu-id="a02f7-128">We'll need a few using statements to save some keystrokes:</span></span>

```
using UnityEngine.Windows.Speech;
using System.Collections.Generic;
using System.Linq;
```

<span data-ttu-id="a02f7-129">Aggiungere quindi alcuni campi alla classe per archiviare il riconoscimento e il dizionario delle azioni >parola chiave:</span><span class="sxs-lookup"><span data-stu-id="a02f7-129">Then let's add a few fields to your class to store the recognizer and keyword->action dictionary:</span></span>

```
KeywordRecognizer keywordRecognizer;
Dictionary<string, System.Action> keywords = new Dictionary<string, System.Action>();
```

<span data-ttu-id="a02f7-130">Aggiungere ora una parola chiave al dizionario, ad esempio in di un `Start()` metodo.</span><span class="sxs-lookup"><span data-stu-id="a02f7-130">Now add a keyword to the dictionary, for example in of a `Start()` method.</span></span> <span data-ttu-id="a02f7-131">In questo esempio viene aggiunta la parola chiave "activate":</span><span class="sxs-lookup"><span data-stu-id="a02f7-131">We're adding the "activate" keyword in this example:</span></span>

```
//Create keywords for keyword recognizer
keywords.Add("activate", () =>
{
    // action to be performed when this keyword is spoken
});
```

<span data-ttu-id="a02f7-132">Creare il riconoscitore di parole chiave e indicare ciò che si vuole riconoscere:</span><span class="sxs-lookup"><span data-stu-id="a02f7-132">Create the keyword recognizer and tell it what we want to recognize:</span></span>

```
keywordRecognizer = new KeywordRecognizer(keywords.Keys.ToArray());
```

<span data-ttu-id="a02f7-133">Registrarsi ora per `OnPhraseRecognized` l'evento</span><span class="sxs-lookup"><span data-stu-id="a02f7-133">Now register for the `OnPhraseRecognized` event</span></span>

```
keywordRecognizer.OnPhraseRecognized += KeywordRecognizer_OnPhraseRecognized;
```

<span data-ttu-id="a02f7-134">Un gestore di esempio è:</span><span class="sxs-lookup"><span data-stu-id="a02f7-134">An example handler is:</span></span>

```
private void KeywordRecognizer_OnPhraseRecognized(PhraseRecognizedEventArgs args)
{
    System.Action keywordAction;
    // if the keyword recognized is in our dictionary, call that Action.
    if (keywords.TryGetValue(args.text, out keywordAction))
    {
        keywordAction.Invoke();
    }
}
```

<span data-ttu-id="a02f7-135">Infine, iniziare a riconoscersi.</span><span class="sxs-lookup"><span data-stu-id="a02f7-135">Finally, start recognizing!</span></span>

```
keywordRecognizer.Start();
```

### <a name="grammarrecognizer"></a><span data-ttu-id="a02f7-136">GrammarRecognizer</span><span class="sxs-lookup"><span data-stu-id="a02f7-136">GrammarRecognizer</span></span>

<span data-ttu-id="a02f7-137">**Spazio dei nomi:** *UnityEngine.Windows.Speech*</span><span class="sxs-lookup"><span data-stu-id="a02f7-137">**Namespace:** *UnityEngine.Windows.Speech*</span></span><br>
<span data-ttu-id="a02f7-138">**Tipi:** *GrammarRecognizer,* *PhraseRecognizedEventArgs,* *SpeechError,* *SpeechSystemStatus*</span><span class="sxs-lookup"><span data-stu-id="a02f7-138">**Types**: *GrammarRecognizer*, *PhraseRecognizedEventArgs*, *SpeechError*, *SpeechSystemStatus*</span></span>

<span data-ttu-id="a02f7-139">GrammarRecognizer viene usato se si specifica la grammatica di riconoscimento tramite SRGS.</span><span class="sxs-lookup"><span data-stu-id="a02f7-139">The GrammarRecognizer is used if you're specifying your recognition grammar using SRGS.</span></span> <span data-ttu-id="a02f7-140">Ciò può essere utile se l'app ha più di poche parole chiave, se vuoi riconoscere frasi più complesse o se vuoi attivare e disattivare facilmente set di comandi.</span><span class="sxs-lookup"><span data-stu-id="a02f7-140">This can be useful if your app has more than just a few keywords, if you want to recognize more complex phrases, or if you want to easily turn on and off sets of commands.</span></span> <span data-ttu-id="a02f7-141">Per informazioni sul formato di file, vedere: Creare grammatiche [usando SRGS XML.](/previous-versions/office/developer/speech-technologies/hh378349(v=office.14))</span><span class="sxs-lookup"><span data-stu-id="a02f7-141">See: [Create Grammars Using SRGS XML](/previous-versions/office/developer/speech-technologies/hh378349(v=office.14)) for file format information.</span></span>

<span data-ttu-id="a02f7-142">Dopo aver creato la grammatica SRGS, che si trova nel progetto in una [cartella StreamingAssets:](https://docs.unity3d.com/Manual/StreamingAssets.html)</span><span class="sxs-lookup"><span data-stu-id="a02f7-142">Once you have your SRGS grammar, and it is in your project in a [StreamingAssets folder](https://docs.unity3d.com/Manual/StreamingAssets.html):</span></span>

```
<PROJECT_ROOT>/Assets/StreamingAssets/SRGS/myGrammar.xml
```

<span data-ttu-id="a02f7-143">Creare un `GrammarRecognizer` oggetto e passarlo al percorso del file SRGS:</span><span class="sxs-lookup"><span data-stu-id="a02f7-143">Create a `GrammarRecognizer` and pass it the path to your SRGS file:</span></span>

```
private GrammarRecognizer grammarRecognizer;
grammarRecognizer = new GrammarRecognizer(Application.streamingDataPath + "/SRGS/myGrammar.xml");
```

<span data-ttu-id="a02f7-144">Registrarsi ora per `OnPhraseRecognized` l'evento</span><span class="sxs-lookup"><span data-stu-id="a02f7-144">Now register for the `OnPhraseRecognized` event</span></span>

```
grammarRecognizer.OnPhraseRecognized += grammarRecognizer_OnPhraseRecognized;
```

<span data-ttu-id="a02f7-145">Si otterrà un callback contenente le informazioni specificate nella grammatica SRGS, che è possibile gestire in modo appropriato.</span><span class="sxs-lookup"><span data-stu-id="a02f7-145">You'll get a callback containing information specified in your SRGS grammar, which you can handle appropriately.</span></span> <span data-ttu-id="a02f7-146">La maggior parte delle informazioni importanti verrà fornita nella `semanticMeanings` matrice.</span><span class="sxs-lookup"><span data-stu-id="a02f7-146">Most of the important information will be provided in the `semanticMeanings` array.</span></span>

```
private void Grammar_OnPhraseRecognized(PhraseRecognizedEventArgs args)
{
    SemanticMeaning[] meanings = args.semanticMeanings;
    // do something
}
```

<span data-ttu-id="a02f7-147">Infine, iniziare a riconoscere.</span><span class="sxs-lookup"><span data-stu-id="a02f7-147">Finally, start recognizing!</span></span>

```
grammarRecognizer.Start();
```

## <a name="dictation"></a><span data-ttu-id="a02f7-148">Dettatura</span><span class="sxs-lookup"><span data-stu-id="a02f7-148">Dictation</span></span>

<span data-ttu-id="a02f7-149">**Spazio dei nomi:** *UnityEngine.Windows.Speech*</span><span class="sxs-lookup"><span data-stu-id="a02f7-149">**Namespace:** *UnityEngine.Windows.Speech*</span></span><br>
<span data-ttu-id="a02f7-150">**Tipi:** *DictationRecognizer,* *SpeechError,* *SpeechSystemStatus*</span><span class="sxs-lookup"><span data-stu-id="a02f7-150">**Types**: *DictationRecognizer*, *SpeechError*, *SpeechSystemStatus*</span></span>

<span data-ttu-id="a02f7-151">Usare per `DictationRecognizer` convertire il riconoscimento vocale dell'utente in testo.</span><span class="sxs-lookup"><span data-stu-id="a02f7-151">Use the `DictationRecognizer` to convert the user's speech to text.</span></span> <span data-ttu-id="a02f7-152">DictationRecognizer espone la funzionalità [di](../../design/voice-input.md#dictation) dettatura e supporta la registrazione e l'ascolto di eventi di ipotesi e frasi completate, in modo da poter inviare commenti e suggerimenti all'utente durante la parola e successivamente.</span><span class="sxs-lookup"><span data-stu-id="a02f7-152">The DictationRecognizer exposes [dictation](../../design/voice-input.md#dictation) functionality and supports registering and listening for hypothesis and phrase completed events, so you can give feedback to your user both while they speak and afterwards.</span></span> <span data-ttu-id="a02f7-153">`Start()` i `Stop()` metodi e abilitano e disabilitano rispettivamente il riconoscimento della dettatura.</span><span class="sxs-lookup"><span data-stu-id="a02f7-153">`Start()` and `Stop()` methods respectively enable and disable dictation recognition.</span></span> <span data-ttu-id="a02f7-154">Dopo essere stato eseguito con il sistema di riconoscimento, deve essere eliminato usando `Dispose()` per rilasciare le risorse utilizzate.</span><span class="sxs-lookup"><span data-stu-id="a02f7-154">Once done with the recognizer, it should be disposed using `Dispose()` to release the resources it uses.</span></span> <span data-ttu-id="a02f7-155">Rilascerà automaticamente queste risorse durante l'operazione di Garbage Collection a un costo aggiuntivo per le prestazioni se non vengono rilasciate prima.</span><span class="sxs-lookup"><span data-stu-id="a02f7-155">It will release these resources automatically during garbage collection at an extra performance cost if they aren't released before that.</span></span>

<span data-ttu-id="a02f7-156">Per iniziare a usare la dettatura sono necessari solo alcuni passaggi:</span><span class="sxs-lookup"><span data-stu-id="a02f7-156">There are only a few steps needed to get started with dictation:</span></span>
1. <span data-ttu-id="a02f7-157">Creare un nuovo `DictationRecognizer`</span><span class="sxs-lookup"><span data-stu-id="a02f7-157">Create a new `DictationRecognizer`</span></span>
2. <span data-ttu-id="a02f7-158">Gestire gli eventi di dettatura</span><span class="sxs-lookup"><span data-stu-id="a02f7-158">Handle Dictation events</span></span>
3. <span data-ttu-id="a02f7-159">Avviare DictationRecognizer</span><span class="sxs-lookup"><span data-stu-id="a02f7-159">Start the DictationRecognizer</span></span>

### <a name="enabling-the-capability-for-dictation"></a><span data-ttu-id="a02f7-160">Abilitazione della funzionalità per la dettatura</span><span class="sxs-lookup"><span data-stu-id="a02f7-160">Enabling the capability for dictation</span></span>

<span data-ttu-id="a02f7-161">Le **funzionalità Internet Client** e **Microfono** devono essere dichiarate perché un'app usi la dettatura:</span><span class="sxs-lookup"><span data-stu-id="a02f7-161">The **Internet Client** and **Microphone** capabilities must be declared for an app to use dictation:</span></span>
1. <span data-ttu-id="a02f7-162">Nell'editor di Unity passare a **Modifica impostazioni > progetto > Lettore**</span><span class="sxs-lookup"><span data-stu-id="a02f7-162">In the Unity Editor, go to **Edit > Project Settings > Player**</span></span>
2. <span data-ttu-id="a02f7-163">Selezionare nella scheda **Windows Store**</span><span class="sxs-lookup"><span data-stu-id="a02f7-163">Select on the **Windows Store** tab</span></span>
3. <span data-ttu-id="a02f7-164">Nella sezione **Publishing Settings > Capabilities (Impostazioni di** > funzionalità) controllare la funzionalità **InternetClient**</span><span class="sxs-lookup"><span data-stu-id="a02f7-164">In the **Publishing Settings > Capabilities** section, check the **InternetClient** capability</span></span>
    * <span data-ttu-id="a02f7-165">Facoltativamente, se il microfono non è già stato abilitato, controllare la **funzionalità** Microfono</span><span class="sxs-lookup"><span data-stu-id="a02f7-165">Optionally, if you didn't already enable the microphone, check the **Microphone** capability</span></span>
4. <span data-ttu-id="a02f7-166">Concedere all'app le autorizzazioni per l'accesso al microfono nel dispositivo HoloLens, se non è già stato fatto</span><span class="sxs-lookup"><span data-stu-id="a02f7-166">Grant permissions to the app for microphone access on your HoloLens device if you haven't already</span></span>
    * <span data-ttu-id="a02f7-167">Verrà richiesto di eseguire questa operazione all'avvio del dispositivo, ma se si fa clic accidentalmente su "No" è possibile modificare le autorizzazioni nelle impostazioni del dispositivo</span><span class="sxs-lookup"><span data-stu-id="a02f7-167">You'll be asked to do this on device startup, but if you accidentally clicked "no" you can change the permissions in the device settings</span></span>

### <a name="dictationrecognizer"></a><span data-ttu-id="a02f7-168">DictationRecognizer</span><span class="sxs-lookup"><span data-stu-id="a02f7-168">DictationRecognizer</span></span>

<span data-ttu-id="a02f7-169">Creare un oggetto DictationRecognizer in questo modo:</span><span class="sxs-lookup"><span data-stu-id="a02f7-169">Create a DictationRecognizer like so:</span></span>

```
dictationRecognizer = new DictationRecognizer();
```

<span data-ttu-id="a02f7-170">Esistono quattro eventi di dettatura che possono essere sottoscritti e gestiti per implementare il comportamento di dettatura.</span><span class="sxs-lookup"><span data-stu-id="a02f7-170">There are four dictation events that can be subscribed to and handled to implement dictation behavior.</span></span>
1. `DictationResult`
2. `DictationComplete`
3. `DictationHypothesis`
4. `DictationError`

<span data-ttu-id="a02f7-171">**DictationResult**</span><span class="sxs-lookup"><span data-stu-id="a02f7-171">**DictationResult**</span></span>

<span data-ttu-id="a02f7-172">Questo evento viene generato dopo la pausa dell'utente, in genere alla fine di una frase.</span><span class="sxs-lookup"><span data-stu-id="a02f7-172">This event is fired after the user pauses, typically at the end of a sentence.</span></span> <span data-ttu-id="a02f7-173">La stringa riconosciuta completa viene restituita qui.</span><span class="sxs-lookup"><span data-stu-id="a02f7-173">The full recognized string is returned here.</span></span>

<span data-ttu-id="a02f7-174">Per prima cosa, sottoscrivere `DictationResult` l'evento:</span><span class="sxs-lookup"><span data-stu-id="a02f7-174">First, subscribe to the `DictationResult` event:</span></span>

```
dictationRecognizer.DictationResult += DictationRecognizer_DictationResult;
```

<span data-ttu-id="a02f7-175">Gestire quindi il callback DictationResult:</span><span class="sxs-lookup"><span data-stu-id="a02f7-175">Then handle the DictationResult callback:</span></span>

```
private void DictationRecognizer_DictationResult(string text, ConfidenceLevel confidence)
{
    // do something
}
```

<span data-ttu-id="a02f7-176">**DictationHypothesis**</span><span class="sxs-lookup"><span data-stu-id="a02f7-176">**DictationHypothesis**</span></span>

<span data-ttu-id="a02f7-177">Questo evento viene generato continuamente mentre l'utente sta parlando.</span><span class="sxs-lookup"><span data-stu-id="a02f7-177">This event is fired continuously while the user is talking.</span></span> <span data-ttu-id="a02f7-178">Mentre il riconoscitore è in ascolto, fornisce il testo di ciò che ha sentito finora.</span><span class="sxs-lookup"><span data-stu-id="a02f7-178">As the recognizer listens, it provides text of what it's heard so far.</span></span>

<span data-ttu-id="a02f7-179">Per prima cosa, sottoscrivere `DictationHypothesis` l'evento:</span><span class="sxs-lookup"><span data-stu-id="a02f7-179">First, subscribe to the `DictationHypothesis` event:</span></span>

```
dictationRecognizer.DictationHypothesis += DictationRecognizer_DictationHypothesis;
```

<span data-ttu-id="a02f7-180">Gestire quindi il callback DictationHypothesis:</span><span class="sxs-lookup"><span data-stu-id="a02f7-180">Then handle the DictationHypothesis callback:</span></span>

```
private void DictationRecognizer_DictationHypothesis(string text)
{
    // do something
}
```

<span data-ttu-id="a02f7-181">**Completamento dettatura**</span><span class="sxs-lookup"><span data-stu-id="a02f7-181">**DictationComplete**</span></span>

<span data-ttu-id="a02f7-182">Questo evento viene generato quando il riconoscimento si arresta, indipendentemente dal fatto che venga chiamato Stop(), si verifichi un timeout o un altro errore.</span><span class="sxs-lookup"><span data-stu-id="a02f7-182">This event is fired when the recognizer stops, whether from Stop() being called, a timeout occurring, or some other error.</span></span>

<span data-ttu-id="a02f7-183">Per prima cosa, sottoscrivere `DictationComplete` l'evento:</span><span class="sxs-lookup"><span data-stu-id="a02f7-183">First, subscribe to the `DictationComplete` event:</span></span>

```
dictationRecognizer.DictationComplete += DictationRecognizer_DictationComplete;
```

<span data-ttu-id="a02f7-184">Gestire quindi il callback DictationComplete:</span><span class="sxs-lookup"><span data-stu-id="a02f7-184">Then handle the DictationComplete callback:</span></span>

```
private void DictationRecognizer_DictationComplete(DictationCompletionCause cause)
{
   // do something
}
```

<span data-ttu-id="a02f7-185">**DictationError**</span><span class="sxs-lookup"><span data-stu-id="a02f7-185">**DictationError**</span></span>

<span data-ttu-id="a02f7-186">Questo evento viene generato quando si verifica un errore.</span><span class="sxs-lookup"><span data-stu-id="a02f7-186">This event is fired when an error occurs.</span></span>

<span data-ttu-id="a02f7-187">Prima di tutto, sottoscrivere `DictationError` l'evento:</span><span class="sxs-lookup"><span data-stu-id="a02f7-187">First, subscribe to the `DictationError` event:</span></span>

```
dictationRecognizer.DictationError += DictationRecognizer_DictationError;
```

<span data-ttu-id="a02f7-188">Gestire quindi il callback DictationError:</span><span class="sxs-lookup"><span data-stu-id="a02f7-188">Then handle the DictationError callback:</span></span>

```
private void DictationRecognizer_DictationError(string error, int hresult)
{
    // do something
}
```

<span data-ttu-id="a02f7-189">Dopo aver sottoscritto e gestito gli eventi di dettatura di cui si è a cuore, avviare il riconoscimento della dettatura per iniziare a ricevere gli eventi.</span><span class="sxs-lookup"><span data-stu-id="a02f7-189">Once you've subscribed and handled the dictation events that you care about, start the dictation recognizer to begin receiving events.</span></span>

```
dictationRecognizer.Start();
```

<span data-ttu-id="a02f7-190">Se non si vuole più mantenere il dictationRecognizer in giro, è necessario annullare la sottoscrizione agli eventi ed eliminare il dictationRecognizer.</span><span class="sxs-lookup"><span data-stu-id="a02f7-190">If you no longer want to keep the DictationRecognizer around, you need to unsubscribe from the events and Dispose the DictationRecognizer.</span></span>

```
dictationRecognizer.DictationResult -= DictationRecognizer_DictationResult;
dictationRecognizer.DictationComplete -= DictationRecognizer_DictationComplete ;
dictationRecognizer.DictationHypothesis -= DictationRecognizer_DictationHypothesis ;
dictationRecognizer.DictationError -= DictationRecognizer_DictationError ;
dictationRecognizer.Dispose();
```

<span data-ttu-id="a02f7-191">**Suggerimenti**</span><span class="sxs-lookup"><span data-stu-id="a02f7-191">**Tips**</span></span>
* <span data-ttu-id="a02f7-192">`Start()` i `Stop()` metodi e abilitano e disabilitano rispettivamente il riconoscimento della dettatura.</span><span class="sxs-lookup"><span data-stu-id="a02f7-192">`Start()` and `Stop()` methods respectively enable and disable dictation recognition.</span></span>
* <span data-ttu-id="a02f7-193">Dopo essere stato eseguito con il sistema di riconoscimento, deve essere eliminato usando `Dispose()` per rilasciare le risorse utilizzate.</span><span class="sxs-lookup"><span data-stu-id="a02f7-193">Once done with the recognizer, it must be disposed using `Dispose()` to release the resources it uses.</span></span> <span data-ttu-id="a02f7-194">Rilascerà automaticamente queste risorse durante l'operazione di Garbage Collection a un costo aggiuntivo per le prestazioni se non vengono rilasciate prima.</span><span class="sxs-lookup"><span data-stu-id="a02f7-194">It will release these resources automatically during garbage collection at an extra performance cost if they aren't released before that.</span></span>
* <span data-ttu-id="a02f7-195">I timeout si verificano dopo un periodo di tempo impostato.</span><span class="sxs-lookup"><span data-stu-id="a02f7-195">Timeouts occur after a set period of time.</span></span> <span data-ttu-id="a02f7-196">È possibile verificare questi timeout `DictationComplete` nell'evento .</span><span class="sxs-lookup"><span data-stu-id="a02f7-196">You can check for these timeouts in the `DictationComplete` event.</span></span> <span data-ttu-id="a02f7-197">È necessario tenere presenti due timeout:</span><span class="sxs-lookup"><span data-stu-id="a02f7-197">There are two timeouts to be aware of:</span></span>
   1. <span data-ttu-id="a02f7-198">Se il riconoscitore viene avviato e non riceve audio per i primi cinque secondi, si verifica il timeout.</span><span class="sxs-lookup"><span data-stu-id="a02f7-198">If the recognizer starts and doesn't hear any audio for the first five seconds, it will time out.</span></span>
   2. <span data-ttu-id="a02f7-199">Se il riconoscitore ha dato un risultato, ma riceve il silenzio per 20 secondi, si verifica il timeout.</span><span class="sxs-lookup"><span data-stu-id="a02f7-199">If the recognizer has given a result, but then hears silence for 20 seconds, it will time out.</span></span>

## <a name="using-both-phrase-recognition-and-dictation"></a><span data-ttu-id="a02f7-200">Uso sia del riconoscimento delle frasi che della dettatura</span><span class="sxs-lookup"><span data-stu-id="a02f7-200">Using both Phrase Recognition and Dictation</span></span>

<span data-ttu-id="a02f7-201">Se si vuole usare sia il riconoscimento delle frasi che la dettatura nell'app, è necessario arrestare completamente uno prima di poter avviare l'altro.</span><span class="sxs-lookup"><span data-stu-id="a02f7-201">If you want to use both phrase recognition and dictation in your app, you'll need to fully shut one down before you can start the other.</span></span> <span data-ttu-id="a02f7-202">Se sono in esecuzione più KeywordRecognizer, è possibile arrestarli tutti contemporaneamente con:</span><span class="sxs-lookup"><span data-stu-id="a02f7-202">If you have multiple KeywordRecognizers running, you can shut them all down at once with:</span></span>

```
PhraseRecognitionSystem.Shutdown();
```

<span data-ttu-id="a02f7-203">È possibile chiamare per ripristinare lo stato precedente di tutti i riconoscitori dopo l'arresto di `Restart()` DictationRecognizer:</span><span class="sxs-lookup"><span data-stu-id="a02f7-203">You can call `Restart()` to restore all recognizers to their previous state after the DictationRecognizer has stopped:</span></span>

```
PhraseRecognitionSystem.Restart();
```

<span data-ttu-id="a02f7-204">È anche possibile avviare un KeywordRecognizer, che riavvierà anche PhraseRecognitionSystem.</span><span class="sxs-lookup"><span data-stu-id="a02f7-204">You could also just start a KeywordRecognizer, which will restart the PhraseRecognitionSystem as well.</span></span>

## <a name="voice-input-in-mixed-reality-toolkit"></a><span data-ttu-id="a02f7-205">Input vocale in Mixed Reality Toolkit</span><span class="sxs-lookup"><span data-stu-id="a02f7-205">Voice input in Mixed Reality Toolkit</span></span>

<span data-ttu-id="a02f7-206">È possibile trovare esempi di MRTK per l'input vocale nelle scene demo seguenti:</span><span class="sxs-lookup"><span data-stu-id="a02f7-206">You can find MRTK examples for voice input in the following demo scenes:</span></span>
* [<span data-ttu-id="a02f7-207">Dettatura</span><span class="sxs-lookup"><span data-stu-id="a02f7-207">Dictation</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/main/Assets/MRTK/Examples/Demos/Input/Scenes/Dictation)
* [<span data-ttu-id="a02f7-208">Voce</span><span class="sxs-lookup"><span data-stu-id="a02f7-208">Speech</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/main/Assets/MRTK/Examples/Demos/Input/Scenes/Speech)

## <a name="next-development-checkpoint"></a><span data-ttu-id="a02f7-209">Successivo checkpoint di sviluppo</span><span class="sxs-lookup"><span data-stu-id="a02f7-209">Next Development Checkpoint</span></span>

<span data-ttu-id="a02f7-210">Se si sta seguendo il percorso di checkpoint per lo sviluppo unity che abbiamo stabilito, l'attività successiva è esplorare le API e le funzionalità della piattaforma realtà mista:</span><span class="sxs-lookup"><span data-stu-id="a02f7-210">If you're following the Unity development checkpoint journey we've laid out, you're next task is exploring the Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="a02f7-211">Esperienze condivise</span><span class="sxs-lookup"><span data-stu-id="a02f7-211">Shared experiences</span></span>](shared-experiences-in-unity.md)

<span data-ttu-id="a02f7-212">È sempre possibile tornare ai [checkpoint per lo sviluppo con Unity](unity-development-overview.md#2-core-building-blocks) in qualsiasi momento.</span><span class="sxs-lookup"><span data-stu-id="a02f7-212">You can always go back to the [Unity development checkpoints](unity-development-overview.md#2-core-building-blocks) at any time.</span></span>
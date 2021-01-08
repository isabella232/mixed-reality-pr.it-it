---
title: Input vocale in Unity
description: Scopri in che modo Unity espone tre modi per aggiungere input vocale, riconoscimento vocale e dettatura all'applicazione di realtà mista Windows.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Input vocale, KeywordRecognizer, GrammarRecognizer, microfono, dettatura, voce, auricolare realtà mista, cuffia di realtà mista di Windows, auricolare realtà virtuale, MRTK, Toolkit realtà mista
ms.openlocfilehash: d07909bbf05ff882eb0a4b6123c39eae9280e3e8
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2021
ms.locfileid: "98009801"
---
# <a name="voice-input-in-unity"></a><span data-ttu-id="993df-104">Input vocale in Unity</span><span class="sxs-lookup"><span data-stu-id="993df-104">Voice input in Unity</span></span>

>[!NOTE]
><span data-ttu-id="993df-105">Anziché le informazioni riportate di seguito, si consiglia di usare il plug-in di Unity per l'SDK cognitive Speech Services che offre risultati di accuratezza vocale molto migliori e consente di accedere facilmente a decodifica di sintesi vocale e funzionalità avanzate di riconoscimento vocale, ad esempio dialogo, interazione basata su finalità, traduzione, sintesi vocale e riconoscimento vocale linguaggio naturale.</span><span class="sxs-lookup"><span data-stu-id="993df-105">Instead of the below information, consider using the Unity plug-in for the Cognitive Speech Services SDK which has much better Speech Accuracy results and provides easy access to speech-to-text decode and advanced speech features like dialog, intent based interaction, translation, text-to-speech synthesis and natural language speech recognition.</span></span> <span data-ttu-id="993df-106">Trovare l'esempio e la documentazione qui: https://docs.microsoft.com//azure/cognitive-services/speech-service/quickstart-csharp-unity</span><span class="sxs-lookup"><span data-stu-id="993df-106">Find the sample and documentaion here: https://docs.microsoft.com//azure/cognitive-services/speech-service/quickstart-csharp-unity</span></span>   

<span data-ttu-id="993df-107">Unity espone tre modi per aggiungere [input vocale](../../design/voice-input.md) all'applicazione Unity.</span><span class="sxs-lookup"><span data-stu-id="993df-107">Unity exposes three ways to add [Voice input](../../design/voice-input.md) to your Unity application.</span></span>

<span data-ttu-id="993df-108">Con KeywordRecognizer (uno dei due tipi di PhraseRecognizers), all'app può essere assegnata una matrice di comandi stringa da ascoltare.</span><span class="sxs-lookup"><span data-stu-id="993df-108">With the KeywordRecognizer (one of two types of PhraseRecognizers), your app can be given an array of string commands to listen for.</span></span> <span data-ttu-id="993df-109">Con GrammarRecognizer (l'altro tipo di PhraseRecognizer), all'app può essere assegnato un file SRGS che definisce una grammatica specifica per l'ascolto.</span><span class="sxs-lookup"><span data-stu-id="993df-109">With the GrammarRecognizer (the other type of PhraseRecognizer), your app can be given an SRGS file defining a specific grammar to listen for.</span></span> <span data-ttu-id="993df-110">Con la DictationRecognizer, l'app può restare in ascolto di qualsiasi parola e fornire all'utente una nota o un'altra visualizzazione del riconoscimento vocale.</span><span class="sxs-lookup"><span data-stu-id="993df-110">With the DictationRecognizer, your app can listen for any word and provide the user with a note or other display of their speech.</span></span>

>[!NOTE]
><span data-ttu-id="993df-111">Solo i riconoscimenti di dettatura o di frase possono essere gestiti in una sola volta.</span><span class="sxs-lookup"><span data-stu-id="993df-111">Only dictation or phrase recognition can be handled at once.</span></span> <span data-ttu-id="993df-112">Ciò significa che se GrammarRecognizer o KeywordRecognizer è attivo, un DictationRecognizer non può essere attivo e viceversa.</span><span class="sxs-lookup"><span data-stu-id="993df-112">That means if a GrammarRecognizer or KeywordRecognizer is active, a DictationRecognizer can not be active and vice versa.</span></span>

## <a name="enabling-the-capability-for-voice"></a><span data-ttu-id="993df-113">Abilitazione della funzionalità per la voce</span><span class="sxs-lookup"><span data-stu-id="993df-113">Enabling the capability for Voice</span></span>

<span data-ttu-id="993df-114">Per usare l'input vocale, è necessario dichiarare la funzionalità **Microphone** per un'app.</span><span class="sxs-lookup"><span data-stu-id="993df-114">The **Microphone** capability must be declared for an app to use Voice input.</span></span>
1. <span data-ttu-id="993df-115">Nell'editor di Unity passare a Impostazioni lettore passando a "modifica > impostazioni progetto > lettore"</span><span class="sxs-lookup"><span data-stu-id="993df-115">In the Unity Editor, go to the player settings by navigating to "Edit > Project Settings > Player"</span></span>
2. <span data-ttu-id="993df-116">Selezionare nella scheda "Windows Store"</span><span class="sxs-lookup"><span data-stu-id="993df-116">Select on the "Windows Store" tab</span></span>
3. <span data-ttu-id="993df-117">Nella sezione "impostazioni di pubblicazione > funzionalità" controllare la funzionalità del **microfono**</span><span class="sxs-lookup"><span data-stu-id="993df-117">In the "Publishing Settings > Capabilities" section, check the **Microphone** capability</span></span>

## <a name="phrase-recognition"></a><span data-ttu-id="993df-118">Riconoscimento di frasi</span><span class="sxs-lookup"><span data-stu-id="993df-118">Phrase Recognition</span></span>

<span data-ttu-id="993df-119">Per consentire all'app di restare in ascolto di frasi specifiche pronunciate dall'utente, è necessario eseguire le operazioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="993df-119">To enable your app to listen for specific phrases spoken by the user then take some action, you need to:</span></span>
1. <span data-ttu-id="993df-120">Specificare le frasi da ascoltare tramite KeywordRecognizer o GrammarRecognizer</span><span class="sxs-lookup"><span data-stu-id="993df-120">Specify which phrases to listen for using a KeywordRecognizer or GrammarRecognizer</span></span>
2. <span data-ttu-id="993df-121">Gestire l'evento OnPhraseRecognized ed eseguire un'azione corrispondente alla frase riconosciuta</span><span class="sxs-lookup"><span data-stu-id="993df-121">Handle the OnPhraseRecognized event and take action corresponding to the phrase recognized</span></span>

### <a name="keywordrecognizer"></a><span data-ttu-id="993df-122">KeywordRecognizer</span><span class="sxs-lookup"><span data-stu-id="993df-122">KeywordRecognizer</span></span>

<span data-ttu-id="993df-123">**Spazio dei nomi:** *UnityEngine. Windows. Speech*</span><span class="sxs-lookup"><span data-stu-id="993df-123">**Namespace:** *UnityEngine.Windows.Speech*</span></span><br>
<span data-ttu-id="993df-124">**Tipi:** *KeywordRecognizer*, *PhraseRecognizedEventArgs*, *SpeechError*, *SpeechSystemStatus*</span><span class="sxs-lookup"><span data-stu-id="993df-124">**Types:** *KeywordRecognizer*, *PhraseRecognizedEventArgs*, *SpeechError*, *SpeechSystemStatus*</span></span>

<span data-ttu-id="993df-125">Sono necessarie alcune istruzioni using per salvare alcune sequenze di tasti:</span><span class="sxs-lookup"><span data-stu-id="993df-125">We'll need a few using statements to save some keystrokes:</span></span>

```
using UnityEngine.Windows.Speech;
using System.Collections.Generic;
using System.Linq;
```

<span data-ttu-id="993df-126">Aggiungere quindi alcuni campi alla classe per archiviare il riconoscimento e la parola chiave >dizionario azione:</span><span class="sxs-lookup"><span data-stu-id="993df-126">Then let's add a few fields to your class to store the recognizer and keyword->action dictionary:</span></span>

```
KeywordRecognizer keywordRecognizer;
Dictionary<string, System.Action> keywords = new Dictionary<string, System.Action>();
```

<span data-ttu-id="993df-127">Aggiungere ora una parola chiave al dizionario, ad esempio in un metodo Start ().</span><span class="sxs-lookup"><span data-stu-id="993df-127">Now add a keyword to the dictionary, for example in of a Start() method.</span></span> <span data-ttu-id="993df-128">In questo esempio viene aggiunta la parola chiave "Activate":</span><span class="sxs-lookup"><span data-stu-id="993df-128">We're adding the "activate" keyword in this example:</span></span>

```
//Create keywords for keyword recognizer
keywords.Add("activate", () =>
{
    // action to be performed when this keyword is spoken
});
```

<span data-ttu-id="993df-129">Creare la parola chiave Recognizer e indicare cosa si vuole riconoscere:</span><span class="sxs-lookup"><span data-stu-id="993df-129">Create the keyword recognizer and tell it what we want to recognize:</span></span>

```
keywordRecognizer = new KeywordRecognizer(keywords.Keys.ToArray());
```

<span data-ttu-id="993df-130">Registrati ora per l'evento OnPhraseRecognized</span><span class="sxs-lookup"><span data-stu-id="993df-130">Now register for the OnPhraseRecognized event</span></span>

```
keywordRecognizer.OnPhraseRecognized += KeywordRecognizer_OnPhraseRecognized;
```

<span data-ttu-id="993df-131">Un gestore di esempio è:</span><span class="sxs-lookup"><span data-stu-id="993df-131">An example handler is:</span></span>

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

<span data-ttu-id="993df-132">Infine, iniziare a riconoscere.</span><span class="sxs-lookup"><span data-stu-id="993df-132">Finally, start recognizing!</span></span>

```
keywordRecognizer.Start();
```

### <a name="grammarrecognizer"></a><span data-ttu-id="993df-133">GrammarRecognizer</span><span class="sxs-lookup"><span data-stu-id="993df-133">GrammarRecognizer</span></span>

<span data-ttu-id="993df-134">**Spazio dei nomi:** *UnityEngine. Windows. Speech*</span><span class="sxs-lookup"><span data-stu-id="993df-134">**Namespace:** *UnityEngine.Windows.Speech*</span></span><br>
<span data-ttu-id="993df-135">**Tipi**: *GrammarRecognizer*, *PhraseRecognizedEventArgs*, *SpeechError*, *SpeechSystemStatus*</span><span class="sxs-lookup"><span data-stu-id="993df-135">**Types**: *GrammarRecognizer*, *PhraseRecognizedEventArgs*, *SpeechError*, *SpeechSystemStatus*</span></span>

<span data-ttu-id="993df-136">GrammarRecognizer viene usato se si specifica la grammatica di riconoscimento usando SRGS.</span><span class="sxs-lookup"><span data-stu-id="993df-136">The GrammarRecognizer is used if you're specifying your recognition grammar using SRGS.</span></span> <span data-ttu-id="993df-137">Questo può essere utile se l'app ha più di poche parole chiave, se si desidera riconoscere frasi più complesse o se si desidera attivare e disattivare facilmente i set di comandi.</span><span class="sxs-lookup"><span data-stu-id="993df-137">This can be useful if your app has more than just a few keywords, if you want to recognize more complex phrases, or if you want to easily turn on and off sets of commands.</span></span> <span data-ttu-id="993df-138">Vedere: [creare grammatiche con SRGS XML](https://msdn.microsoft.com/library/hh378349(v=office.14).aspx) per informazioni sul formato di file.</span><span class="sxs-lookup"><span data-stu-id="993df-138">See: [Create Grammars Using SRGS XML](https://msdn.microsoft.com/library/hh378349(v=office.14).aspx) for file format information.</span></span>

<span data-ttu-id="993df-139">Una volta completata la grammatica SRGS, questa si trova nel progetto in una [cartella StreamingAssets](https://docs.unity3d.com/Manual/StreamingAssets.html):</span><span class="sxs-lookup"><span data-stu-id="993df-139">Once you have your SRGS grammar, and it is in your project in a [StreamingAssets folder](https://docs.unity3d.com/Manual/StreamingAssets.html):</span></span>

```
<PROJECT_ROOT>/Assets/StreamingAssets/SRGS/myGrammar.xml
```

<span data-ttu-id="993df-140">Creare un GrammarRecognizer e passargli il percorso del file SRGS:</span><span class="sxs-lookup"><span data-stu-id="993df-140">Create a GrammarRecognizer and pass it the path to your SRGS file:</span></span>

```
private GrammarRecognizer grammarRecognizer;
grammarRecognizer = new GrammarRecognizer(Application.streamingDataPath + "/SRGS/myGrammar.xml");
```

<span data-ttu-id="993df-141">Registrati ora per l'evento OnPhraseRecognized</span><span class="sxs-lookup"><span data-stu-id="993df-141">Now register for the OnPhraseRecognized event</span></span>

```
grammarRecognizer.OnPhraseRecognized += grammarRecognizer_OnPhraseRecognized;
```

<span data-ttu-id="993df-142">Si otterrà un callback contenente le informazioni specificate nella grammatica SRGS, che è possibile gestire in modo appropriato.</span><span class="sxs-lookup"><span data-stu-id="993df-142">You'll get a callback containing information specified in your SRGS grammar, which you can handle appropriately.</span></span> <span data-ttu-id="993df-143">La maggior parte delle informazioni importanti verranno fornite nella matrice semanticMeanings.</span><span class="sxs-lookup"><span data-stu-id="993df-143">Most of the important information will be provided in the semanticMeanings array.</span></span>

```
private void Grammar_OnPhraseRecognized(PhraseRecognizedEventArgs args)
{
    SemanticMeaning[] meanings = args.semanticMeanings;
    // do something
}
```

<span data-ttu-id="993df-144">Infine, iniziare a riconoscere.</span><span class="sxs-lookup"><span data-stu-id="993df-144">Finally, start recognizing!</span></span>

```
grammarRecognizer.Start();
```

## <a name="dictation"></a><span data-ttu-id="993df-145">Dettatura</span><span class="sxs-lookup"><span data-stu-id="993df-145">Dictation</span></span>

<span data-ttu-id="993df-146">**Spazio dei nomi:** *UnityEngine. Windows. Speech*</span><span class="sxs-lookup"><span data-stu-id="993df-146">**Namespace:** *UnityEngine.Windows.Speech*</span></span><br>
<span data-ttu-id="993df-147">**Tipi**: *DictationRecognizer*, *SpeechError*, *SpeechSystemStatus*</span><span class="sxs-lookup"><span data-stu-id="993df-147">**Types**: *DictationRecognizer*, *SpeechError*, *SpeechSystemStatus*</span></span>

<span data-ttu-id="993df-148">Usare DictationRecognizer per convertire il riconoscimento vocale dell'utente in testo.</span><span class="sxs-lookup"><span data-stu-id="993df-148">Use the DictationRecognizer to convert the user's speech to text.</span></span> <span data-ttu-id="993df-149">DictationRecognizer espone la funzionalità di [Dettatura](../../design/voice-input.md#dictation) e supporta la registrazione e l'ascolto di eventi di ipotesi completati e frasi completate, in modo che sia possibile inviare commenti e suggerimenti all'utente sia durante la loro pronuncia che in seguito.</span><span class="sxs-lookup"><span data-stu-id="993df-149">The DictationRecognizer exposes [dictation](../../design/voice-input.md#dictation) functionality and supports registering and listening for hypothesis and phrase completed events, so you can give feedback to your user both while they speak and afterwards.</span></span> <span data-ttu-id="993df-150">I metodi Start () e stop () rispettivamente abilitano e disabilitano il riconoscimento della dettatura.</span><span class="sxs-lookup"><span data-stu-id="993df-150">Start() and Stop() methods respectively enable and disable dictation recognition.</span></span> <span data-ttu-id="993df-151">Una volta terminato con il riconoscimento, è necessario eliminarlo utilizzando il metodo Dispose () per rilasciare le risorse utilizzate.</span><span class="sxs-lookup"><span data-stu-id="993df-151">Once done with the recognizer, it should be disposed using Dispose() method to release the resources it uses.</span></span> <span data-ttu-id="993df-152">Queste risorse verranno rilasciate automaticamente durante Garbage Collection a un costo aggiuntivo in termini di prestazioni, se non vengono rilasciate prima.</span><span class="sxs-lookup"><span data-stu-id="993df-152">It will release these resources automatically during garbage collection at an additional performance cost if they aren't released before that.</span></span>

<span data-ttu-id="993df-153">Per iniziare a usare la dettatura sono necessari solo alcuni passaggi:</span><span class="sxs-lookup"><span data-stu-id="993df-153">There are only a few steps needed to get started with dictation:</span></span>
1. <span data-ttu-id="993df-154">Creare un nuovo DictationRecognizer</span><span class="sxs-lookup"><span data-stu-id="993df-154">Create a new DictationRecognizer</span></span>
2. <span data-ttu-id="993df-155">Gestisci eventi di dettatura</span><span class="sxs-lookup"><span data-stu-id="993df-155">Handle Dictation events</span></span>
3. <span data-ttu-id="993df-156">Avviare il DictationRecognizer</span><span class="sxs-lookup"><span data-stu-id="993df-156">Start the DictationRecognizer</span></span>

### <a name="enabling-the-capability-for-dictation"></a><span data-ttu-id="993df-157">Abilitazione della funzionalità per la dettatura</span><span class="sxs-lookup"><span data-stu-id="993df-157">Enabling the capability for dictation</span></span>

<span data-ttu-id="993df-158">La funzionalità "client Internet", insieme alla funzionalità "microfono" indicata in precedenza, deve essere dichiarata per poter sfruttare la dettatura per un'app.</span><span class="sxs-lookup"><span data-stu-id="993df-158">The "Internet Client" capability, along with the "Microphone" capability mentioned above, must be declared for an app to leverage dictation.</span></span>
1. <span data-ttu-id="993df-159">Nell'editor di Unity passare alle impostazioni del lettore passando alla pagina "Edit > Project Settings > Player"</span><span class="sxs-lookup"><span data-stu-id="993df-159">In the Unity Editor, go to the player settings by navigating to "Edit > Project Settings > Player" page</span></span>
2. <span data-ttu-id="993df-160">Selezionare nella scheda "Windows Store"</span><span class="sxs-lookup"><span data-stu-id="993df-160">Select on the "Windows Store" tab</span></span>
3. <span data-ttu-id="993df-161">Nella sezione "impostazioni di pubblicazione > funzionalità" controllare la funzionalità **internetClient**</span><span class="sxs-lookup"><span data-stu-id="993df-161">In the "Publishing Settings > Capabilities" section, check the **InternetClient** capability</span></span>

### <a name="dictationrecognizer"></a><span data-ttu-id="993df-162">DictationRecognizer</span><span class="sxs-lookup"><span data-stu-id="993df-162">DictationRecognizer</span></span>

<span data-ttu-id="993df-163">Creare un DictationRecognizer come segue:</span><span class="sxs-lookup"><span data-stu-id="993df-163">Create a DictationRecognizer like so:</span></span>

```
dictationRecognizer = new DictationRecognizer();
```

<span data-ttu-id="993df-164">Sono disponibili quattro eventi di dettatura che è possibile sottoscrivere e gestire per implementare il comportamento di dettatura.</span><span class="sxs-lookup"><span data-stu-id="993df-164">There are four dictation events that can be subscribed to and handled to implement dictation behavior.</span></span>
1. <span data-ttu-id="993df-165">DictationResult</span><span class="sxs-lookup"><span data-stu-id="993df-165">DictationResult</span></span>
2. <span data-ttu-id="993df-166">DictationComplete</span><span class="sxs-lookup"><span data-stu-id="993df-166">DictationComplete</span></span>
3. <span data-ttu-id="993df-167">DictationHypothesis</span><span class="sxs-lookup"><span data-stu-id="993df-167">DictationHypothesis</span></span>
4. <span data-ttu-id="993df-168">DictationError</span><span class="sxs-lookup"><span data-stu-id="993df-168">DictationError</span></span>

<span data-ttu-id="993df-169">**DictationResult**</span><span class="sxs-lookup"><span data-stu-id="993df-169">**DictationResult**</span></span>

<span data-ttu-id="993df-170">Questo evento viene generato dopo la sospensione dell'utente, in genere alla fine di una frase.</span><span class="sxs-lookup"><span data-stu-id="993df-170">This event is fired after the user pauses, typically at the end of a sentence.</span></span> <span data-ttu-id="993df-171">La stringa riconosciuta completa viene restituita qui.</span><span class="sxs-lookup"><span data-stu-id="993df-171">The full recognized string is returned here.</span></span>

<span data-ttu-id="993df-172">Prima di tutto, sottoscrivere l'evento DictationResult:</span><span class="sxs-lookup"><span data-stu-id="993df-172">First, subscribe to the DictationResult event:</span></span>

```
dictationRecognizer.DictationResult += DictationRecognizer_DictationResult;
```

<span data-ttu-id="993df-173">Gestire quindi il callback di DictationResult:</span><span class="sxs-lookup"><span data-stu-id="993df-173">Then handle the DictationResult callback:</span></span>

```
private void DictationRecognizer_DictationResult(string text, ConfidenceLevel confidence)
{
    // do something
}
```

<span data-ttu-id="993df-174">**DictationHypothesis**</span><span class="sxs-lookup"><span data-stu-id="993df-174">**DictationHypothesis**</span></span>

<span data-ttu-id="993df-175">Questo evento viene generato continuamente mentre l'utente sta parlando.</span><span class="sxs-lookup"><span data-stu-id="993df-175">This event is fired continuously while the user is talking.</span></span> <span data-ttu-id="993df-176">Quando il riconoscimento è in ascolto, fornisce il testo di ciò che è stato udito finora.</span><span class="sxs-lookup"><span data-stu-id="993df-176">As the recognizer listens, it provides text of what it's heard so far.</span></span>

<span data-ttu-id="993df-177">Prima di tutto, sottoscrivere l'evento DictationHypothesis:</span><span class="sxs-lookup"><span data-stu-id="993df-177">First, subscribe to the DictationHypothesis event:</span></span>

```
dictationRecognizer.DictationHypothesis += DictationRecognizer_DictationHypothesis;
```

<span data-ttu-id="993df-178">Gestire quindi il callback di DictationHypothesis:</span><span class="sxs-lookup"><span data-stu-id="993df-178">Then handle the DictationHypothesis callback:</span></span>

```
private void DictationRecognizer_DictationHypothesis(string text)
{
    // do something
}
```

<span data-ttu-id="993df-179">**DictationComplete**</span><span class="sxs-lookup"><span data-stu-id="993df-179">**DictationComplete**</span></span>

<span data-ttu-id="993df-180">Questo evento viene generato quando il riconoscimento viene arrestato, da Stop () chiamato, da un timeout che si verifica o da un altro errore.</span><span class="sxs-lookup"><span data-stu-id="993df-180">This event is fired when the recognizer stops, whether from Stop() being called, a timeout occurring, or some other error.</span></span>

<span data-ttu-id="993df-181">Prima di tutto, sottoscrivere l'evento DictationComplete:</span><span class="sxs-lookup"><span data-stu-id="993df-181">First, subscribe to the DictationComplete event:</span></span>

```
dictationRecognizer.DictationComplete += DictationRecognizer_DictationComplete;
```

<span data-ttu-id="993df-182">Gestire quindi il callback di DictationComplete:</span><span class="sxs-lookup"><span data-stu-id="993df-182">Then handle the DictationComplete callback:</span></span>

```
private void DictationRecognizer_DictationComplete(DictationCompletionCause cause)
{
   // do something
}
```

<span data-ttu-id="993df-183">**DictationError**</span><span class="sxs-lookup"><span data-stu-id="993df-183">**DictationError**</span></span>

<span data-ttu-id="993df-184">Questo evento viene generato quando si verifica un errore.</span><span class="sxs-lookup"><span data-stu-id="993df-184">This event is fired when an error occurs.</span></span>

<span data-ttu-id="993df-185">Prima di tutto, sottoscrivere l'evento DictationError:</span><span class="sxs-lookup"><span data-stu-id="993df-185">First, subscribe to the DictationError event:</span></span>

```
dictationRecognizer.DictationError += DictationRecognizer_DictationError;
```

<span data-ttu-id="993df-186">Gestire quindi il callback di DictationError:</span><span class="sxs-lookup"><span data-stu-id="993df-186">Then handle the DictationError callback:</span></span>

```
private void DictationRecognizer_DictationError(string error, int hresult)
{
    // do something
}
```

<span data-ttu-id="993df-187">Una volta sottoscritti e gestiti gli eventi di dettatura a cui si è interessati, avviare il riconoscimento della dettatura per iniziare a ricevere gli eventi.</span><span class="sxs-lookup"><span data-stu-id="993df-187">Once you've subscribed and handled the dictation events that you care about, start the dictation recognizer to begin receiving events.</span></span>

```
dictationRecognizer.Start();
```

<span data-ttu-id="993df-188">Se non si desidera più proteggere il DictationRecognizer, è necessario annullare la sottoscrizione agli eventi ed eliminare il DictationRecognizer.</span><span class="sxs-lookup"><span data-stu-id="993df-188">If you no longer want to keep the DictationRecognizer around, you need to unsubscribe from the events and Dispose the DictationRecognizer.</span></span>

```
dictationRecognizer.DictationResult -= DictationRecognizer_DictationResult;
dictationRecognizer.DictationComplete -= DictationRecognizer_DictationComplete ;
dictationRecognizer.DictationHypothesis -= DictationRecognizer_DictationHypothesis ;
dictationRecognizer.DictationError -= DictationRecognizer_DictationError ;
dictationRecognizer.Dispose();
```

<span data-ttu-id="993df-189">**Suggerimenti**</span><span class="sxs-lookup"><span data-stu-id="993df-189">**Tips**</span></span>
* <span data-ttu-id="993df-190">I metodi Start () e stop () rispettivamente abilitano e disabilitano il riconoscimento della dettatura.</span><span class="sxs-lookup"><span data-stu-id="993df-190">Start() and Stop() methods respectively enable and disable dictation recognition.</span></span>
* <span data-ttu-id="993df-191">Una volta terminato con il riconoscimento, è necessario eliminarlo utilizzando il metodo Dispose () per rilasciare le risorse utilizzate.</span><span class="sxs-lookup"><span data-stu-id="993df-191">Once done with the recognizer, it must be disposed using Dispose() method to release the resources it uses.</span></span> <span data-ttu-id="993df-192">Queste risorse verranno rilasciate automaticamente durante Garbage Collection a un costo aggiuntivo in termini di prestazioni, se non vengono rilasciate prima.</span><span class="sxs-lookup"><span data-stu-id="993df-192">It will release these resources automatically during garbage collection at an additional performance cost if they aren't released before that.</span></span>
* <span data-ttu-id="993df-193">I timeout si verificano dopo un determinato periodo di tempo.</span><span class="sxs-lookup"><span data-stu-id="993df-193">Timeouts occur after a set period of time.</span></span> <span data-ttu-id="993df-194">È possibile verificare questi timeout nell'evento DictationComplete.</span><span class="sxs-lookup"><span data-stu-id="993df-194">You can check for these timeouts in the DictationComplete event.</span></span> <span data-ttu-id="993df-195">È necessario tenere presenti due timeout:</span><span class="sxs-lookup"><span data-stu-id="993df-195">There are two timeouts to be aware of:</span></span>
   1. <span data-ttu-id="993df-196">Se il riconoscimento viene avviato e non viene sentito alcun audio per i primi cinque secondi, si verifica il timeout.</span><span class="sxs-lookup"><span data-stu-id="993df-196">If the recognizer starts and doesn't hear any audio for the first five seconds, it will time out.</span></span>
   2. <span data-ttu-id="993df-197">Se il riconoscimento ha dato un risultato, ma in questo caso rileva il silenzio per 20 secondi, si verifichi un timeout.</span><span class="sxs-lookup"><span data-stu-id="993df-197">If the recognizer has given a result, but then hears silence for 20 seconds, it will time out.</span></span>

## <a name="using-both-phrase-recognition-and-dictation"></a><span data-ttu-id="993df-198">Uso sia del riconoscimento delle frasi che della dettatura</span><span class="sxs-lookup"><span data-stu-id="993df-198">Using both Phrase Recognition and Dictation</span></span>

<span data-ttu-id="993df-199">Se si vuole usare sia il riconoscimento delle frasi che la dettatura nell'app, è necessario chiudere completamente una volta prima di poter avviare l'altra.</span><span class="sxs-lookup"><span data-stu-id="993df-199">If you want to use both phrase recognition and dictation in your app, you'll need to fully shut one down before you can start the other.</span></span> <span data-ttu-id="993df-200">Se sono in esecuzione più KeywordRecognizers, è possibile arrestarli tutti contemporaneamente con:</span><span class="sxs-lookup"><span data-stu-id="993df-200">If you have multiple KeywordRecognizers running, you can shut them all down at once with:</span></span>

```
PhraseRecognitionSystem.Shutdown();
```

<span data-ttu-id="993df-201">Per ripristinare lo stato precedente di tutti i riconoscitori, dopo l'arresto di DictationRecognizer, è possibile chiamare:</span><span class="sxs-lookup"><span data-stu-id="993df-201">In order to restore all recognizers to their previous state, after the DictationRecognizer has stopped, you can call:</span></span>

```
PhraseRecognitionSystem.Restart();
```

<span data-ttu-id="993df-202">È anche possibile avviare solo un KeywordRecognizer, che riavvia anche il PhraseRecognitionSystem.</span><span class="sxs-lookup"><span data-stu-id="993df-202">You could also just start a KeywordRecognizer, which will restart the PhraseRecognitionSystem as well.</span></span>

## <a name="using-the-microphone-helper"></a><span data-ttu-id="993df-203">Uso dell'helper del microfono</span><span class="sxs-lookup"><span data-stu-id="993df-203">Using the microphone helper</span></span>

<span data-ttu-id="993df-204">Il Toolkit di realtà mista in GitHub contiene una classe helper del microfono per suggerire agli sviluppatori se è presente un microfono utilizzabile nel sistema.</span><span class="sxs-lookup"><span data-stu-id="993df-204">The Mixed Reality Toolkit on GitHub contains a microphone helper class to hint at developers if there's a usable microphone on the system.</span></span> <span data-ttu-id="993df-205">Uno di questi casi è quello in cui si vuole controllare se è presente il microfono nel sistema prima di visualizzare gli hint di interazione vocale nell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="993df-205">One use for it's where one would want to check if there's microphone on system before showing any speech interaction hints in the application.</span></span>

<span data-ttu-id="993df-206">Lo script Helper Microphone è disponibile nella [cartella input/script/Utilities](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Scripts/Utilities/MicrophoneHelper.cs).</span><span class="sxs-lookup"><span data-stu-id="993df-206">The microphone helper script can be found in the [Input/Scripts/Utilities folder](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Scripts/Utilities/MicrophoneHelper.cs).</span></span> <span data-ttu-id="993df-207">Il repository GitHub contiene anche un [piccolo esempio](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/Input/Scripts/MicrophoneHelperSample.cs) che illustra come usare l'helper.</span><span class="sxs-lookup"><span data-stu-id="993df-207">The GitHub repo also contains a [small sample](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/Input/Scripts/MicrophoneHelperSample.cs) demonstrating how to use the helper.</span></span>

## <a name="voice-input-in-mixed-reality-toolkit"></a><span data-ttu-id="993df-208">Input vocale nel Toolkit per realtà mista</span><span class="sxs-lookup"><span data-stu-id="993df-208">Voice input in Mixed Reality Toolkit</span></span>
<span data-ttu-id="993df-209">È possibile trovare gli esempi dell'input vocale in questa scena.</span><span class="sxs-lookup"><span data-stu-id="993df-209">You can find the examples of the voice input in this scene.</span></span>

- [<span data-ttu-id="993df-210">HoloToolkit-Examples/input/Scenes/SpeechInputSource. Unity</span><span class="sxs-lookup"><span data-stu-id="993df-210">HoloToolkit-Examples/Input/Scenes/SpeechInputSource.unity</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/Input/Scenes/SpeechInputSource.unity)

## <a name="next-development-checkpoint"></a><span data-ttu-id="993df-211">Successivo checkpoint di sviluppo</span><span class="sxs-lookup"><span data-stu-id="993df-211">Next Development Checkpoint</span></span>

<span data-ttu-id="993df-212">Se si segue il percorso di checkpoint per lo sviluppo di Unity, l'attività successiva consiste nell'esplorare le API e le funzionalità della piattaforma di realtà mista:</span><span class="sxs-lookup"><span data-stu-id="993df-212">If you're following the Unity development checkpoint journey we've laid out, you're next task is exploring the Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="993df-213">Esperienze condivise</span><span class="sxs-lookup"><span data-stu-id="993df-213">Shared experiences</span></span>](shared-experiences-in-unity.md)

<span data-ttu-id="993df-214">È sempre possibile tornare ai [checkpoint per lo sviluppo con Unity](unity-development-overview.md#2-core-building-blocks) in qualsiasi momento.</span><span class="sxs-lookup"><span data-stu-id="993df-214">You can always go back to the [Unity development checkpoints](unity-development-overview.md#2-core-building-blocks) at any time.</span></span>

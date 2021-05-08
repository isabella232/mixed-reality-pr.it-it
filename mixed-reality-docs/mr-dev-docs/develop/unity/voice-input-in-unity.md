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
# <a name="voice-input-in-unity"></a>Input vocale in Unity

> [!CAUTION]
> Prima di iniziare, è consigliabile usare il plug-in Unity per Cognitive Speech Services SDK. Il plug-in offre risultati migliori per l'accuratezza della voce e un facile accesso alla decodifica vocale, oltre a funzionalità vocali avanzate come dialogo, interazione basata sulle finalità, traduzione, sintesi vocale e riconoscimento vocale in linguaggio naturale. Per iniziare, vedere l'esempio [e la documentazione](/azure/cognitive-services/speech-service/quickstart-csharp-unity).

Unity espone tre modi per aggiungere [input vocale](../../design/voice-input.md) all'applicazione Unity, i primi due dei quali sono tipi di PhraseRecognizer:
* Fornisce `KeywordRecognizer` all'app una matrice di comandi stringa per l'ascolto
* fornisce `GrammarRecognizer` all'app un file SRGS che definisce una grammatica specifica per l'ascolto
* consente all'app di restare in ascolto di qualsiasi parola e fornire all'utente una nota o `DictationRecognizer` un'altra visualizzazione del parlato

> [!NOTE]
> La dettatura e il riconoscimento delle frasi non possono essere gestiti contemporaneamente. Se è attivo un oggetto GrammarRecognizer o KeywordRecognizer, un oggetto DictationRecognizer non può essere attivo e viceversa.

## <a name="enabling-the-capability-for-voice"></a>Abilitazione della funzionalità per Voice

La **funzionalità Microfono** deve essere dichiarata perché un'app usi l'input vocale.
1. Nell'editor di Unity passare a **Modifica impostazioni > progetto > Lettore**
2. Selezionare la **scheda Windows Store**
3. Nella sezione **Impostazioni di > funzionalità** selezionare la **funzionalità** Microfono
4. Concedere le autorizzazioni all'app per l'accesso al microfono nel dispositivo HoloLens
    * Verrà richiesto di eseguire questa operazione all'avvio del dispositivo, ma se si è fatto clic accidentalmente su "no" è possibile modificare le autorizzazioni nelle impostazioni del dispositivo

## <a name="phrase-recognition"></a>Riconoscimento di frasi

Per consentire all'app di restare in ascolto di frasi specifiche pronunciate dall'utente e quindi eseguire alcune azioni, è necessario:
1. Specificare le frasi da ascoltare usando `KeywordRecognizer` o `GrammarRecognizer`
2. Gestire `OnPhraseRecognized` l'evento ed eseguire un'azione corrispondente alla frase riconosciuta

### <a name="keywordrecognizer"></a>KeywordRecognizer

**Spazio dei nomi:** *UnityEngine.Windows.Speech*<br>
**Tipi:** *KeywordRecognizer,* *PhraseRecognizedEventArgs,* *SpeechError,* *SpeechSystemStatus*

Per salvare alcune sequenze di tasti, sono necessarie alcune istruzioni using:

```
using UnityEngine.Windows.Speech;
using System.Collections.Generic;
using System.Linq;
```

Aggiungere quindi alcuni campi alla classe per archiviare il riconoscimento e il dizionario delle azioni >parola chiave:

```
KeywordRecognizer keywordRecognizer;
Dictionary<string, System.Action> keywords = new Dictionary<string, System.Action>();
```

Aggiungere ora una parola chiave al dizionario, ad esempio in di un `Start()` metodo. In questo esempio viene aggiunta la parola chiave "activate":

```
//Create keywords for keyword recognizer
keywords.Add("activate", () =>
{
    // action to be performed when this keyword is spoken
});
```

Creare il riconoscitore di parole chiave e indicare ciò che si vuole riconoscere:

```
keywordRecognizer = new KeywordRecognizer(keywords.Keys.ToArray());
```

Registrarsi ora per `OnPhraseRecognized` l'evento

```
keywordRecognizer.OnPhraseRecognized += KeywordRecognizer_OnPhraseRecognized;
```

Un gestore di esempio è:

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

Infine, iniziare a riconoscersi.

```
keywordRecognizer.Start();
```

### <a name="grammarrecognizer"></a>GrammarRecognizer

**Spazio dei nomi:** *UnityEngine.Windows.Speech*<br>
**Tipi:** *GrammarRecognizer,* *PhraseRecognizedEventArgs,* *SpeechError,* *SpeechSystemStatus*

GrammarRecognizer viene usato se si specifica la grammatica di riconoscimento tramite SRGS. Ciò può essere utile se l'app ha più di poche parole chiave, se vuoi riconoscere frasi più complesse o se vuoi attivare e disattivare facilmente set di comandi. Per informazioni sul formato di file, vedere: Creare grammatiche [usando SRGS XML.](/previous-versions/office/developer/speech-technologies/hh378349(v=office.14))

Dopo aver creato la grammatica SRGS, che si trova nel progetto in una [cartella StreamingAssets:](https://docs.unity3d.com/Manual/StreamingAssets.html)

```
<PROJECT_ROOT>/Assets/StreamingAssets/SRGS/myGrammar.xml
```

Creare un `GrammarRecognizer` oggetto e passarlo al percorso del file SRGS:

```
private GrammarRecognizer grammarRecognizer;
grammarRecognizer = new GrammarRecognizer(Application.streamingDataPath + "/SRGS/myGrammar.xml");
```

Registrarsi ora per `OnPhraseRecognized` l'evento

```
grammarRecognizer.OnPhraseRecognized += grammarRecognizer_OnPhraseRecognized;
```

Si otterrà un callback contenente le informazioni specificate nella grammatica SRGS, che è possibile gestire in modo appropriato. La maggior parte delle informazioni importanti verrà fornita nella `semanticMeanings` matrice.

```
private void Grammar_OnPhraseRecognized(PhraseRecognizedEventArgs args)
{
    SemanticMeaning[] meanings = args.semanticMeanings;
    // do something
}
```

Infine, iniziare a riconoscere.

```
grammarRecognizer.Start();
```

## <a name="dictation"></a>Dettatura

**Spazio dei nomi:** *UnityEngine.Windows.Speech*<br>
**Tipi:** *DictationRecognizer,* *SpeechError,* *SpeechSystemStatus*

Usare per `DictationRecognizer` convertire il riconoscimento vocale dell'utente in testo. DictationRecognizer espone la funzionalità [di](../../design/voice-input.md#dictation) dettatura e supporta la registrazione e l'ascolto di eventi di ipotesi e frasi completate, in modo da poter inviare commenti e suggerimenti all'utente durante la parola e successivamente. `Start()` i `Stop()` metodi e abilitano e disabilitano rispettivamente il riconoscimento della dettatura. Dopo essere stato eseguito con il sistema di riconoscimento, deve essere eliminato usando `Dispose()` per rilasciare le risorse utilizzate. Rilascerà automaticamente queste risorse durante l'operazione di Garbage Collection a un costo aggiuntivo per le prestazioni se non vengono rilasciate prima.

Per iniziare a usare la dettatura sono necessari solo alcuni passaggi:
1. Creare un nuovo `DictationRecognizer`
2. Gestire gli eventi di dettatura
3. Avviare DictationRecognizer

### <a name="enabling-the-capability-for-dictation"></a>Abilitazione della funzionalità per la dettatura

Le **funzionalità Internet Client** e **Microfono** devono essere dichiarate perché un'app usi la dettatura:
1. Nell'editor di Unity passare a **Modifica impostazioni > progetto > Lettore**
2. Selezionare nella scheda **Windows Store**
3. Nella sezione **Publishing Settings > Capabilities (Impostazioni di** > funzionalità) controllare la funzionalità **InternetClient**
    * Facoltativamente, se il microfono non è già stato abilitato, controllare la **funzionalità** Microfono
4. Concedere all'app le autorizzazioni per l'accesso al microfono nel dispositivo HoloLens, se non è già stato fatto
    * Verrà richiesto di eseguire questa operazione all'avvio del dispositivo, ma se si fa clic accidentalmente su "No" è possibile modificare le autorizzazioni nelle impostazioni del dispositivo

### <a name="dictationrecognizer"></a>DictationRecognizer

Creare un oggetto DictationRecognizer in questo modo:

```
dictationRecognizer = new DictationRecognizer();
```

Esistono quattro eventi di dettatura che possono essere sottoscritti e gestiti per implementare il comportamento di dettatura.
1. `DictationResult`
2. `DictationComplete`
3. `DictationHypothesis`
4. `DictationError`

**DictationResult**

Questo evento viene generato dopo la pausa dell'utente, in genere alla fine di una frase. La stringa riconosciuta completa viene restituita qui.

Per prima cosa, sottoscrivere `DictationResult` l'evento:

```
dictationRecognizer.DictationResult += DictationRecognizer_DictationResult;
```

Gestire quindi il callback DictationResult:

```
private void DictationRecognizer_DictationResult(string text, ConfidenceLevel confidence)
{
    // do something
}
```

**DictationHypothesis**

Questo evento viene generato continuamente mentre l'utente sta parlando. Mentre il riconoscitore è in ascolto, fornisce il testo di ciò che ha sentito finora.

Per prima cosa, sottoscrivere `DictationHypothesis` l'evento:

```
dictationRecognizer.DictationHypothesis += DictationRecognizer_DictationHypothesis;
```

Gestire quindi il callback DictationHypothesis:

```
private void DictationRecognizer_DictationHypothesis(string text)
{
    // do something
}
```

**Completamento dettatura**

Questo evento viene generato quando il riconoscimento si arresta, indipendentemente dal fatto che venga chiamato Stop(), si verifichi un timeout o un altro errore.

Per prima cosa, sottoscrivere `DictationComplete` l'evento:

```
dictationRecognizer.DictationComplete += DictationRecognizer_DictationComplete;
```

Gestire quindi il callback DictationComplete:

```
private void DictationRecognizer_DictationComplete(DictationCompletionCause cause)
{
   // do something
}
```

**DictationError**

Questo evento viene generato quando si verifica un errore.

Prima di tutto, sottoscrivere `DictationError` l'evento:

```
dictationRecognizer.DictationError += DictationRecognizer_DictationError;
```

Gestire quindi il callback DictationError:

```
private void DictationRecognizer_DictationError(string error, int hresult)
{
    // do something
}
```

Dopo aver sottoscritto e gestito gli eventi di dettatura di cui si è a cuore, avviare il riconoscimento della dettatura per iniziare a ricevere gli eventi.

```
dictationRecognizer.Start();
```

Se non si vuole più mantenere il dictationRecognizer in giro, è necessario annullare la sottoscrizione agli eventi ed eliminare il dictationRecognizer.

```
dictationRecognizer.DictationResult -= DictationRecognizer_DictationResult;
dictationRecognizer.DictationComplete -= DictationRecognizer_DictationComplete ;
dictationRecognizer.DictationHypothesis -= DictationRecognizer_DictationHypothesis ;
dictationRecognizer.DictationError -= DictationRecognizer_DictationError ;
dictationRecognizer.Dispose();
```

**Suggerimenti**
* `Start()` i `Stop()` metodi e abilitano e disabilitano rispettivamente il riconoscimento della dettatura.
* Dopo essere stato eseguito con il sistema di riconoscimento, deve essere eliminato usando `Dispose()` per rilasciare le risorse utilizzate. Rilascerà automaticamente queste risorse durante l'operazione di Garbage Collection a un costo aggiuntivo per le prestazioni se non vengono rilasciate prima.
* I timeout si verificano dopo un periodo di tempo impostato. È possibile verificare questi timeout `DictationComplete` nell'evento . È necessario tenere presenti due timeout:
   1. Se il riconoscitore viene avviato e non riceve audio per i primi cinque secondi, si verifica il timeout.
   2. Se il riconoscitore ha dato un risultato, ma riceve il silenzio per 20 secondi, si verifica il timeout.

## <a name="using-both-phrase-recognition-and-dictation"></a>Uso sia del riconoscimento delle frasi che della dettatura

Se si vuole usare sia il riconoscimento delle frasi che la dettatura nell'app, è necessario arrestare completamente uno prima di poter avviare l'altro. Se sono in esecuzione più KeywordRecognizer, è possibile arrestarli tutti contemporaneamente con:

```
PhraseRecognitionSystem.Shutdown();
```

È possibile chiamare per ripristinare lo stato precedente di tutti i riconoscitori dopo l'arresto di `Restart()` DictationRecognizer:

```
PhraseRecognitionSystem.Restart();
```

È anche possibile avviare un KeywordRecognizer, che riavvierà anche PhraseRecognitionSystem.

## <a name="voice-input-in-mixed-reality-toolkit"></a>Input vocale in Mixed Reality Toolkit

È possibile trovare esempi di MRTK per l'input vocale nelle scene demo seguenti:
* [Dettatura](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/main/Assets/MRTK/Examples/Demos/Input/Scenes/Dictation)
* [Voce](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/main/Assets/MRTK/Examples/Demos/Input/Scenes/Speech)

## <a name="next-development-checkpoint"></a>Successivo checkpoint di sviluppo

Se si sta seguendo il percorso di checkpoint per lo sviluppo unity che abbiamo stabilito, l'attività successiva è esplorare le API e le funzionalità della piattaforma realtà mista:

> [!div class="nextstepaction"]
> [Esperienze condivise](shared-experiences-in-unity.md)

È sempre possibile tornare ai [checkpoint per lo sviluppo con Unity](unity-development-overview.md#2-core-building-blocks) in qualsiasi momento.
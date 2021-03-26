---
title: Input vocale in Unity
description: Scopri in che modo Unity espone tre modi per aggiungere input vocale, riconoscimento vocale e dettatura all'applicazione di realtà mista Windows.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Input vocale, KeywordRecognizer, GrammarRecognizer, microfono, dettatura, voce, auricolare realtà mista, cuffia di realtà mista di Windows, auricolare realtà virtuale, MRTK, Toolkit realtà mista
ms.openlocfilehash: c062289a1a26365528a86761b6b68a9a24041f7c
ms.sourcegitcommit: ac315c1d35f2b9c431e79bc3f1212215301bb867
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105550381"
---
# <a name="voice-input-in-unity"></a>Input vocale in Unity

> [!CAUTION]
> Prima di iniziare, provare a usare il plug-in di Unity per cognitive Speech Services SDK. Il plug-in offre risultati di accuratezza del riconoscimento vocale e accesso facile alla decodifica di sintesi vocale, oltre a funzionalità avanzate di riconoscimento vocale come finestre di dialogo, interazione basata su finalità, traduzione, sintesi di sintesi vocale e riconoscimento vocale in linguaggio naturale. Per iniziare, vedere l' [esempio e la documentazione](/azure/cognitive-services/speech-service/quickstart-csharp-unity).

Unity espone tre modi per aggiungere [input vocale](../../design/voice-input.md) all'applicazione Unity, i primi due dei quali sono i tipi di PhraseRecognizer:
* `KeywordRecognizer`Fornisce all'app una matrice di comandi stringa da ascoltare
* `GrammarRecognizer`Fornisce all'app un file SRGS che definisce una grammatica specifica da ascoltare
* `DictationRecognizer`Consente all'app di restare in ascolto di qualsiasi parola e fornire all'utente una nota o un'altra visualizzazione del riconoscimento vocale

> [!NOTE]
> La dettatura e il riconoscimento di frasi non possono essere gestiti contemporaneamente. Se GrammarRecognizer o KeywordRecognizer è attivo, un DictationRecognizer non può essere attivo e viceversa.

## <a name="enabling-the-capability-for-voice"></a>Abilitazione della funzionalità per la voce

Per usare l'input vocale, è necessario dichiarare la funzionalità **Microphone** per un'app.
1. Nell'editor di Unity passare a **modifica > impostazioni progetto > lettore**
2. Selezionare la scheda **Windows Store**
3. Nella sezione **impostazioni di pubblicazione > funzionalità** selezionare la funzionalità del **microfono**
4. Concedere le autorizzazioni all'app per l'accesso al microfono nel dispositivo HoloLens
    * Verrà richiesto di eseguire questa operazione all'avvio del dispositivo, ma se è stato fatto clic su "No" è possibile modificare le autorizzazioni nelle impostazioni del dispositivo

## <a name="phrase-recognition"></a>Riconoscimento di frasi

Per consentire all'app di restare in ascolto di frasi specifiche pronunciate dall'utente, è necessario eseguire le operazioni seguenti:
1. Specificare le frasi da ascoltare tramite `KeywordRecognizer` o `GrammarRecognizer`
2. Gestire l' `OnPhraseRecognized` evento ed eseguire un'azione corrispondente alla frase riconosciuta

### <a name="keywordrecognizer"></a>KeywordRecognizer

**Spazio dei nomi:** *UnityEngine. Windows. Speech*<br>
**Tipi:** *KeywordRecognizer*, *PhraseRecognizedEventArgs*, *SpeechError*, *SpeechSystemStatus*

Sono necessarie alcune istruzioni using per salvare alcune sequenze di tasti:

```
using UnityEngine.Windows.Speech;
using System.Collections.Generic;
using System.Linq;
```

Aggiungere quindi alcuni campi alla classe per archiviare il riconoscimento e la parola chiave >dizionario azione:

```
KeywordRecognizer keywordRecognizer;
Dictionary<string, System.Action> keywords = new Dictionary<string, System.Action>();
```

Aggiungere ora una parola chiave al dizionario, ad esempio in un `Start()` metodo. In questo esempio viene aggiunta la parola chiave "Activate":

```
//Create keywords for keyword recognizer
keywords.Add("activate", () =>
{
    // action to be performed when this keyword is spoken
});
```

Creare la parola chiave Recognizer e indicare cosa si vuole riconoscere:

```
keywordRecognizer = new KeywordRecognizer(keywords.Keys.ToArray());
```

Ora registrarsi per l' `OnPhraseRecognized` evento

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

Infine, iniziare a riconoscere.

```
keywordRecognizer.Start();
```

### <a name="grammarrecognizer"></a>GrammarRecognizer

**Spazio dei nomi:** *UnityEngine. Windows. Speech*<br>
**Tipi**: *GrammarRecognizer*, *PhraseRecognizedEventArgs*, *SpeechError*, *SpeechSystemStatus*

GrammarRecognizer viene usato se si specifica la grammatica di riconoscimento usando SRGS. Questo può essere utile se l'app ha più di poche parole chiave, se si desidera riconoscere frasi più complesse o se si desidera attivare e disattivare facilmente i set di comandi. Vedere: [creare grammatiche con SRGS XML](/previous-versions/office/developer/speech-technologies/hh378349(v=office.14)) per informazioni sul formato di file.

Una volta completata la grammatica SRGS, questa si trova nel progetto in una [cartella StreamingAssets](https://docs.unity3d.com/Manual/StreamingAssets.html):

```
<PROJECT_ROOT>/Assets/StreamingAssets/SRGS/myGrammar.xml
```

Creare un oggetto `GrammarRecognizer` e passargli il percorso del file SRGS:

```
private GrammarRecognizer grammarRecognizer;
grammarRecognizer = new GrammarRecognizer(Application.streamingDataPath + "/SRGS/myGrammar.xml");
```

Ora registrarsi per l' `OnPhraseRecognized` evento

```
grammarRecognizer.OnPhraseRecognized += grammarRecognizer_OnPhraseRecognized;
```

Si otterrà un callback contenente le informazioni specificate nella grammatica SRGS, che è possibile gestire in modo appropriato. La maggior parte delle informazioni importanti verranno fornite nell' `semanticMeanings` Array.

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

**Spazio dei nomi:** *UnityEngine. Windows. Speech*<br>
**Tipi**: *DictationRecognizer*, *SpeechError*, *SpeechSystemStatus*

Usare `DictationRecognizer` per convertire il riconoscimento vocale dell'utente in testo. DictationRecognizer espone la funzionalità di [Dettatura](../../design/voice-input.md#dictation) e supporta la registrazione e l'ascolto di eventi di ipotesi completati e frasi completate, in modo che sia possibile inviare commenti e suggerimenti all'utente sia durante la loro pronuncia che in seguito. `Start()` i `Stop()` metodi e consentono rispettivamente di abilitare e disabilitare il riconoscimento della dettatura. Una volta terminato con il riconoscimento, è necessario eliminarlo utilizzando `Dispose()` per rilasciare le risorse utilizzate. Queste risorse verranno rilasciate automaticamente durante Garbage Collection a un costo aggiuntivo in termini di prestazioni, se non vengono rilasciate prima.

Per iniziare a usare la dettatura sono necessari solo alcuni passaggi:
1. Crea nuovo `DictationRecognizer`
2. Gestisci eventi di dettatura
3. Avviare il DictationRecognizer

### <a name="enabling-the-capability-for-dictation"></a>Abilitazione della funzionalità per la dettatura

Le funzionalità client e **microfono** **Internet** devono essere dichiarate affinché un'app usi la dettatura:
1. Nell'editor di Unity passare a **Edit > Project Settings > Player**
2. Selezionare nella scheda **Windows Store**
3. Nella sezione **impostazioni di pubblicazione > funzionalità** selezionare la funzionalità **internetClient**
    * Facoltativamente, se non è già stato abilitato il microfono, controllare la funzionalità del **microfono**
4. Concedere all'app le autorizzazioni per l'accesso al microfono nel dispositivo HoloLens, se non è già stato fatto
    * Verrà richiesto di eseguire questa operazione all'avvio del dispositivo, ma se è stato fatto clic su "No" è possibile modificare le autorizzazioni nelle impostazioni del dispositivo

### <a name="dictationrecognizer"></a>DictationRecognizer

Creare un DictationRecognizer come segue:

```
dictationRecognizer = new DictationRecognizer();
```

Sono disponibili quattro eventi di dettatura che è possibile sottoscrivere e gestire per implementare il comportamento di dettatura.
1. `DictationResult`
2. `DictationComplete`
3. `DictationHypothesis`
4. `DictationError`

**DictationResult**

Questo evento viene generato dopo la sospensione dell'utente, in genere alla fine di una frase. La stringa riconosciuta completa viene restituita qui.

Prima di tutto, sottoscrivere l' `DictationResult` evento:

```
dictationRecognizer.DictationResult += DictationRecognizer_DictationResult;
```

Gestire quindi il callback di DictationResult:

```
private void DictationRecognizer_DictationResult(string text, ConfidenceLevel confidence)
{
    // do something
}
```

**DictationHypothesis**

Questo evento viene generato continuamente mentre l'utente sta parlando. Quando il riconoscimento è in ascolto, fornisce il testo di ciò che è stato udito finora.

Prima di tutto, sottoscrivere l' `DictationHypothesis` evento:

```
dictationRecognizer.DictationHypothesis += DictationRecognizer_DictationHypothesis;
```

Gestire quindi il callback di DictationHypothesis:

```
private void DictationRecognizer_DictationHypothesis(string text)
{
    // do something
}
```

**DictationComplete**

Questo evento viene generato quando il riconoscimento viene arrestato, da Stop () chiamato, da un timeout che si verifica o da un altro errore.

Prima di tutto, sottoscrivere l' `DictationComplete` evento:

```
dictationRecognizer.DictationComplete += DictationRecognizer_DictationComplete;
```

Gestire quindi il callback di DictationComplete:

```
private void DictationRecognizer_DictationComplete(DictationCompletionCause cause)
{
   // do something
}
```

**DictationError**

Questo evento viene generato quando si verifica un errore.

Prima di tutto, sottoscrivere l' `DictationError` evento:

```
dictationRecognizer.DictationError += DictationRecognizer_DictationError;
```

Gestire quindi il callback di DictationError:

```
private void DictationRecognizer_DictationError(string error, int hresult)
{
    // do something
}
```

Una volta sottoscritti e gestiti gli eventi di dettatura a cui si è interessati, avviare il riconoscimento della dettatura per iniziare a ricevere gli eventi.

```
dictationRecognizer.Start();
```

Se non si desidera più proteggere il DictationRecognizer, è necessario annullare la sottoscrizione agli eventi ed eliminare il DictationRecognizer.

```
dictationRecognizer.DictationResult -= DictationRecognizer_DictationResult;
dictationRecognizer.DictationComplete -= DictationRecognizer_DictationComplete ;
dictationRecognizer.DictationHypothesis -= DictationRecognizer_DictationHypothesis ;
dictationRecognizer.DictationError -= DictationRecognizer_DictationError ;
dictationRecognizer.Dispose();
```

**Suggerimenti**
* `Start()` i `Stop()` metodi e consentono rispettivamente di abilitare e disabilitare il riconoscimento della dettatura.
* Una volta terminato con il riconoscimento, è necessario eliminarlo utilizzando `Dispose()` per rilasciare le risorse utilizzate. Queste risorse verranno rilasciate automaticamente durante Garbage Collection a un costo aggiuntivo in termini di prestazioni, se non vengono rilasciate prima.
* I timeout si verificano dopo un determinato periodo di tempo. È possibile verificare la presenza di questi timeout nell' `DictationComplete` evento. È necessario tenere presenti due timeout:
   1. Se il riconoscimento viene avviato e non viene sentito alcun audio per i primi cinque secondi, si verifica il timeout.
   2. Se il riconoscimento ha dato un risultato, ma in questo caso rileva il silenzio per 20 secondi, si verifichi un timeout.

## <a name="using-both-phrase-recognition-and-dictation"></a>Uso sia del riconoscimento delle frasi che della dettatura

Se si vuole usare sia il riconoscimento delle frasi che la dettatura nell'app, è necessario chiudere completamente una volta prima di poter avviare l'altra. Se sono in esecuzione più KeywordRecognizers, è possibile arrestarli tutti contemporaneamente con:

```
PhraseRecognitionSystem.Shutdown();
```

È possibile chiamare `Restart()` per ripristinare lo stato precedente di tutti i riconoscitori dopo l'arresto di DictationRecognizer:

```
PhraseRecognitionSystem.Restart();
```

È anche possibile avviare solo un KeywordRecognizer, che riavvia anche il PhraseRecognitionSystem.

## <a name="voice-input-in-mixed-reality-toolkit"></a>Input vocale nel Toolkit per realtà mista

Gli esempi di MRTK per l'input vocale sono disponibili nelle scene demo seguenti:
* [Dettatura](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MRTK/Examples/Demos/Input/Scenes/Dictation)
* [Voce](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MRTK/Examples/Demos/Input/Scenes/Speech)

## <a name="next-development-checkpoint"></a>Successivo checkpoint di sviluppo

Se si segue il percorso di checkpoint per lo sviluppo di Unity, l'attività successiva consiste nell'esplorare le API e le funzionalità della piattaforma di realtà mista:

> [!div class="nextstepaction"]
> [Esperienze condivise](shared-experiences-in-unity.md)

È sempre possibile tornare ai [checkpoint per lo sviluppo con Unity](unity-development-overview.md#2-core-building-blocks) in qualsiasi momento.
---
title: Input vocale in DirectX
description: Illustra come implementare comandi vocali e il riconoscimento di frasi e frasi di piccole dimensioni in un'app DirectX per Windows Mixed Reality.
author: mikeriches
ms.author: mriches
ms.date: 08/04/2020
ms.topic: article
keywords: procedura dettagliata, comando vocale, frase, riconoscimento, riconoscimento vocale, directx, piattaforma, cortana, realtà mista di Windows
ms.openlocfilehash: e30d5c2101bed4b613111b6131a3e94d654c3ff5b1e913f4d8e275ffc1a2776a
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115221841"
---
# <a name="voice-input-in-directx"></a>Input vocale in DirectX

> [!NOTE]
> Questo articolo è correlato alle API native WinRT legacy.  Per i nuovi progetti di app native, è consigliabile usare **[l'API OpenXR](openxr-getting-started.md)**.

Questo articolo illustra come implementare i comandi [vocali e](../../design/voice-input.md) il riconoscimento di frasi piccole e frasi in un'app DirectX per Windows Mixed Reality.

>[!NOTE]
>I frammenti di codice in questo articolo usano C++/CX anziché C++17 conforme a C++/WinRT, che viene usato nel modello di progetto [olografico C++.](creating-a-holographic-directx-project.md)  I concetti sono equivalenti per un progetto C++/WinRT, ma è necessario tradurre il codice.

## <a name="use-speechrecognizer-for-continuous-speech-recognition"></a>Usare SpeechRecognizer per il riconoscimento vocale continuo

Questa sezione descrive come usare il riconoscimento vocale continuo per abilitare i comandi vocali nell'app. Questa procedura guidata usa il codice [dell'esempio HolographicVoiceInput.](https://go.microsoft.com/fwlink/p/?LinkId=844964) Quando l'esempio è in esecuzione, pronunciare il nome di uno dei comandi di colore registrati per modificare il colore del cubo rotante.

Creare prima di tutto una *nuova Windows::Media::SpeechRecognition::SpeechRecognizer.*

Da *HolographicVoiceInputSampleMain::CreateSpeechConstraintsForCurrentState*:

```
m_speechRecognizer = ref new SpeechRecognizer();
```

Creare un elenco di comandi vocali per il riconoscimento vocale per l'ascolto. In questo caso si costruisce un set di comandi per modificare il colore di un ologramma. Per praticità, verranno creati anche i dati che verranno utilizzati per i comandi in un secondo momento.

```
m_speechCommandList = ref new Platform::Collections::Vector<String^>();
   m_speechCommandData.clear();
   m_speechCommandList->Append(StringReference(L"white"));
   m_speechCommandData.push_back(float4(1.f, 1.f, 1.f, 1.f));
   m_speechCommandList->Append(StringReference(L"grey"));
   m_speechCommandData.push_back(float4(0.5f, 0.5f, 0.5f, 1.f));
   m_speechCommandList->Append(StringReference(L"green"));
   m_speechCommandData.push_back(float4(0.f, 1.f, 0.f, 1.f));
   m_speechCommandList->Append(StringReference(L"black"));
   m_speechCommandData.push_back(float4(0.1f, 0.1f, 0.1f, 1.f));
   m_speechCommandList->Append(StringReference(L"red"));
   m_speechCommandData.push_back(float4(1.f, 0.f, 0.f, 1.f));
   m_speechCommandList->Append(StringReference(L"yellow"));
   m_speechCommandData.push_back(float4(1.f, 1.f, 0.f, 1.f));
   m_speechCommandList->Append(StringReference(L"aquamarine"));
   m_speechCommandData.push_back(float4(0.f, 1.f, 1.f, 1.f));
   m_speechCommandList->Append(StringReference(L"blue"));
   m_speechCommandData.push_back(float4(0.f, 0.f, 1.f, 1.f));
   m_speechCommandList->Append(StringReference(L"purple"));
   m_speechCommandData.push_back(float4(1.f, 0.f, 1.f, 1.f));
```

È possibile usare parole fonetiche che potrebbero non essere presenti in un dizionario per specificare i comandi.

```
m_speechCommandList->Append(StringReference(L"SpeechRecognizer"));
   m_speechCommandData.push_back(float4(0.5f, 0.1f, 1.f, 1.f));
```

Per caricare l'elenco di comandi nell'elenco di vincoli per il riconoscimento vocale, usare un [oggetto SpeechRecognitionListConstraint.](/uwp/api/Windows.Media.SpeechRecognition.SpeechRecognitionListConstraint)

```
SpeechRecognitionListConstraint^ spConstraint = ref new SpeechRecognitionListConstraint(m_speechCommandList);
   m_speechRecognizer->Constraints->Clear();
   m_speechRecognizer->Constraints->Append(spConstraint);
   create_task(m_speechRecognizer->CompileConstraintsAsync()).then([this](SpeechRecognitionCompilationResult^ compilationResult)
   {
       if (compilationResult->Status == SpeechRecognitionResultStatus::Success)
       {
           m_speechRecognizer->ContinuousRecognitionSession->StartAsync();
       }
       else
       {
           // Handle errors here.
       }
   });
```

Sottoscrivere [l'evento ResultGenerated](/uwp/api/Windows.Media.SpeechRecognition.SpeechContinuousRecognitionSession) nella [sessione SpeechContinuousRecognitionSession del riconoscimento vocale.](/uwp/api/Windows.Media.SpeechRecognition.SpeechContinuousRecognitionSession) Questo evento invia una notifica all'app quando uno dei comandi è stato riconosciuto.

```
m_speechRecognizer->ContinuousRecognitionSession->ResultGenerated +=
       ref new TypedEventHandler<SpeechContinuousRecognitionSession^, SpeechContinuousRecognitionResultGeneratedEventArgs^>(
           std::bind(&HolographicVoiceInputSampleMain::OnResultGenerated, this, _1, _2)
           );
```

Il *gestore dell'evento OnResultGenerated* riceve i dati dell'evento in un'istanza [speechContinuousRecognitionResultGeneratedEventArgs.](/uwp/api/Windows.Media.SpeechRecognition.SpeechContinuousRecognitionResultGeneratedEventArgs) Se l'attendibilità è maggiore della soglia definita, l'app dovrebbe notare che l'evento si è verificato. Salvare i dati dell'evento in modo che sia possibile usarli in un ciclo di aggiornamento successivo.

Da *HolographicVoiceInputSampleMain.cpp:*

```
// Change the cube color, if we get a valid result.
   void HolographicVoiceInputSampleMain::OnResultGenerated(SpeechContinuousRecognitionSession ^sender, SpeechContinuousRecognitionResultGeneratedEventArgs ^args)
   {
       if (args->Result->RawConfidence > 0.5f)
       {
           m_lastCommand = args->Result->Text;
       }
   }
```

Nel codice di esempio viene modificato il colore del cubo dell'ologramma rotante in base al comando dell'utente.

Da *HolographicVoiceInputSampleMain::Update*:

```
// Check for new speech input since the last frame.
   if (m_lastCommand != nullptr)
   {
       auto command = m_lastCommand;
       m_lastCommand = nullptr;

       int i = 0;
       for each (auto& iter in m_speechCommandList)
       {
           if (iter == command)
           {
               m_spinningCubeRenderer->SetColor(m_speechCommandData[i]);
               break;
           }

           ++i;
       }
   }
```

## <a name="use-one-shot-recognition"></a>Usare il riconoscimento "one-shot"

È possibile configurare un sistema di riconoscimento vocale per l'ascolto di frasi o frasi parlate dall'utente. In questo caso, viene applicato *un oggetto SpeechRecognitionTopicConstraint* che indica al sistema di riconoscimento vocale il tipo di input previsto. Ecco un flusso di lavoro dell'app per questo scenario:
1. L'app crea SpeechRecognizer, fornisce prompt dell'interfaccia utente e inizia ad ascoltare un comando parlato.
2. L'utente pronuncia una frase o una frase.
3. Viene eseguito il riconoscimento vocale dell'utente e viene restituito un risultato all'app. A questo punto, l'app deve fornire un prompt dell'interfaccia utente per indicare che si è verificato il riconoscimento.
4. A seconda del livello di confidenza a cui si vuole rispondere e del livello di attendibilità del risultato del riconoscimento vocale, l'app può elaborare il risultato e rispondere in base alle esigenze.

Questa sezione descrive come creare un oggetto SpeechRecognizer, compilare il vincolo e restare in ascolto dell'input vocale.

Il codice seguente compila il vincolo dell'argomento, che in questo caso è ottimizzato per la ricerca Web.

```
auto constraint = ref new SpeechRecognitionTopicConstraint(SpeechRecognitionScenario::WebSearch, L"webSearch");
   m_speechRecognizer->Constraints->Clear();
   m_speechRecognizer->Constraints->Append(constraint);
   return create_task(m_speechRecognizer->CompileConstraintsAsync())
       .then([this](task<SpeechRecognitionCompilationResult^> previousTask)
   {
```

Se la compilazione ha esito positivo, è possibile continuare con il riconoscimento vocale.

```
try
       {
           SpeechRecognitionCompilationResult^ compilationResult = previousTask.get();

           // Check to make sure that the constraints were in a proper format and the recognizer was able to compile it.
           if (compilationResult->Status == SpeechRecognitionResultStatus::Success)
           {
               // If the compilation succeeded, we can start listening for the user's spoken phrase or sentence.
               create_task(m_speechRecognizer->RecognizeAsync()).then([this](task<SpeechRecognitionResult^>& previousTask)
               {
```

Il risultato viene quindi restituito all'app. Se il risultato è abbastanza sicuro, è possibile elaborare il comando. Questo esempio di codice elabora i risultati con attendibilità minima media.

```
try
                   {
                       auto result = previousTask.get();

                       if (result->Status != SpeechRecognitionResultStatus::Success)
                       {
                           PrintWstringToDebugConsole(
                               std::wstring(L"Speech recognition was not successful: ") +
                               result->Status.ToString()->Data() +
                               L"\n"
                               );
                       }

                       // In this example, we look for at least medium confidence in the speech result.
                       if ((result->Confidence == SpeechRecognitionConfidence::High) ||
                           (result->Confidence == SpeechRecognitionConfidence::Medium))
                       {
                           // If the user said a color name anywhere in their phrase, it will be recognized in the
                           // Update loop; then, the cube will change color.
                           m_lastCommand = result->Text;

                           PrintWstringToDebugConsole(
                               std::wstring(L"Speech phrase was: ") +
                               m_lastCommand->Data() +
                               L"\n"
                               );
                       }
                       else
                       {
                           PrintWstringToDebugConsole(
                               std::wstring(L"Recognition confidence not high enough: ") +
                               result->Confidence.ToString()->Data() +
                               L"\n"
                               );
                       }
                   }
```

Ogni volta che si usa il riconoscimento vocale, cercare le eccezioni che potrebbero indicare che l'utente ha disattivato il microfono nelle impostazioni di privacy del sistema. Questa operazione può verificarsi durante l'inizializzazione o il riconoscimento.

```
catch (Exception^ exception)
                   {
                       // Note that if you get an "Access is denied" exception, you might need to enable the microphone
                       // privacy setting on the device and/or add the microphone capability to your app manifest.

                       PrintWstringToDebugConsole(
                           std::wstring(L"Speech recognizer error: ") +
                           exception->ToString()->Data() +
                           L"\n"
                           );
                   }
               });

               return true;
           }
           else
           {
               OutputDebugStringW(L"Could not initialize predefined grammar speech engine!\n");

               // Handle errors here.
               return false;
           }
       }
       catch (Exception^ exception)
       {
           // Note that if you get an "Access is denied" exception, you might need to enable the microphone
           // privacy setting on the device and/or add the microphone capability to your app manifest.

           PrintWstringToDebugConsole(
               std::wstring(L"Exception while trying to initialize predefined grammar speech engine:") +
               exception->Message->Data() +
               L"\n"
               );

           // Handle exceptions here.
           return false;
       }
   });
```

> [!NOTE]
> Esistono diversi [speechRecognitionScenarios](/uwp/api/Windows.Media.SpeechRecognition.SpeechRecognitionScenario) predefiniti che è possibile usare per ottimizzare il riconoscimento vocale.

* Per ottimizzare la dettatura, usare lo scenario di dettatura.<br/>
   ```
   // Compile the dictation topic constraint, which optimizes for speech dictation.
   auto dictationConstraint = ref new SpeechRecognitionTopicConstraint(SpeechRecognitionScenario::Dictation, "dictation");
   m_speechRecognizer->Constraints->Append(dictationConstraint);
   ```

* Per le ricerche Web vocali, usare il vincolo dello scenario specifico del Web seguente.

   ```
   // Add a web search topic constraint to the recognizer.
   auto webSearchConstraint = ref new SpeechRecognitionTopicConstraint(SpeechRecognitionScenario::WebSearch, "webSearch");
   speechRecognizer->Constraints->Append(webSearchConstraint);
   ```

* Usare il vincolo del modulo per compilare i moduli. In questo caso, è meglio applicare la propria grammatica ottimizzata per la compilazione del modulo.

   ```
   // Add a form constraint to the recognizer.
   auto formConstraint = ref new SpeechRecognitionTopicConstraint(SpeechRecognitionScenario::FormFilling, "formFilling");
   speechRecognizer->Constraints->Append(formConstraint );
   ```
* È possibile fornire la propria grammatica nel formato SRGS.

## <a name="use-continuous-recognition"></a>Usare il riconoscimento continuo

Per lo scenario di dettatura continua, vedere l'esempio di Windows 10 di codice vocale [UWP.](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpeechRecognitionAndSynthesis/cpp/Scenario_ContinuousDictation.xaml.cpp)

## <a name="handle-quality-degradation"></a>Gestire la riduzione della qualità

Le condizioni ambientali talvolta interferiscono con il riconoscimento vocale. Ad esempio, la stanza potrebbe essere troppo rumorosa o l'utente potrebbe parlare troppo forte. Quando possibile, l'API riconoscimento vocale fornisce informazioni sulle condizioni che hanno causato la riduzione della qualità. Queste informazioni vengono inserite nell'app tramite un evento WinRT. Nell'esempio seguente viene illustrato come sottoscrivere questo evento.

```
m_speechRecognizer->RecognitionQualityDegrading +=
       ref new TypedEventHandler<SpeechRecognizer^, SpeechRecognitionQualityDegradingEventArgs^>(
           std::bind(&HolographicVoiceInputSampleMain::OnSpeechQualityDegraded, this, _1, _2)
           );
```

Nell'esempio di codice si scrivono le informazioni sulle condizioni nella console di debug. Un'app potrebbe voler fornire commenti e suggerimenti all'utente tramite l'interfaccia utente, la sintesi vocale e un altro metodo. Oppure potrebbe essere necessario comportarsi in modo diverso quando la voce viene interrotta da una riduzione temporanea della qualità.

```
void HolographicSpeechPromptSampleMain::OnSpeechQualityDegraded(SpeechRecognizer^ recognizer, SpeechRecognitionQualityDegradingEventArgs^ args)
   {
       switch (args->Problem)
       {
       case SpeechRecognitionAudioProblem::TooFast:
           OutputDebugStringW(L"The user spoke too quickly.\n");
           break;

       case SpeechRecognitionAudioProblem::TooSlow:
           OutputDebugStringW(L"The user spoke too slowly.\n");
           break;

       case SpeechRecognitionAudioProblem::TooQuiet:
           OutputDebugStringW(L"The user spoke too softly.\n");
           break;

       case SpeechRecognitionAudioProblem::TooLoud:
           OutputDebugStringW(L"The user spoke too loudly.\n");
           break;

       case SpeechRecognitionAudioProblem::TooNoisy:
           OutputDebugStringW(L"There is too much noise in the signal.\n");
           break;

       case SpeechRecognitionAudioProblem::NoSignal:
           OutputDebugStringW(L"There is no signal.\n");
           break;

       case SpeechRecognitionAudioProblem::None:
       default:
           OutputDebugStringW(L"An error was reported with no information.\n");
           break;
       }
   }
```

Se non si usano classi di riferimento per creare l'app DirectX, è necessario annullare la sottoscrizione all'evento prima di rilasciare o ricreare il riconoscimento vocale. HolographicSpeechPromptSample include una routine per arrestare il riconoscimento e annullare la sottoscrizione agli eventi.

```
Concurrency::task<void> HolographicSpeechPromptSampleMain::StopCurrentRecognizerIfExists()
   {
       return create_task([this]()
       {
           if (m_speechRecognizer != nullptr)
           {
               return create_task(m_speechRecognizer->StopRecognitionAsync()).then([this]()
               {
                   m_speechRecognizer->RecognitionQualityDegrading -= m_speechRecognitionQualityDegradedToken;

                   if (m_speechRecognizer->ContinuousRecognitionSession != nullptr)
                   {
                       m_speechRecognizer->ContinuousRecognitionSession->ResultGenerated -= m_speechRecognizerResultEventToken;
                   }
               });
           }
           else
           {
               return create_task([this]() { m_speechRecognizer = nullptr; });
           }
       });
   }
```

## <a name="use-speech-synthesis-to-provide-audible-prompts"></a>Usare la sintesi vocale per fornire prompt udibili

Gli esempi di riconoscimento vocale olografico usano la sintesi vocale per fornire istruzioni udibili all'utente. Questa sezione illustra come creare un esempio di voce sintetizzata e quindi riprodurlo tramite le API audio HRTF.

Quando si richiede l'input di frasi, è consigliabile fornire prompt vocali personalizzati. Le richieste possono anche indicare quando i comandi vocali possono essere pronunciati per uno scenario di riconoscimento continuo. L'esempio seguente illustra come usare un sintetizzatore vocale a tale scopo. È anche possibile usare un clip vocale preregistrato, un'interfaccia utente visiva o un altro indicatore di cosa dire, ad esempio negli scenari in cui la richiesta non è dinamica.

Creare prima di tutto l'oggetto SpeechSynthesizer.

```
auto speechSynthesizer = ref new Windows::Media::SpeechSynthesis::SpeechSynthesizer();
```

È necessaria anche una stringa che includa il testo da sintetizzare.

```
// Phrase recognition works best when requesting a phrase or sentence.
   StringReference voicePrompt = L"At the prompt: Say a phrase, asking me to change the cube to a specific color.";
```

La sintesi vocale viene sintetizzata in modo asincrono tramite SynthesizeTextToStreamAsync. In questo caso, si avvia un'attività asincrona per sintetizzare il parlato.

```
create_task(speechSynthesizer->SynthesizeTextToStreamAsync(voicePrompt), task_continuation_context::use_current())
       .then([this, speechSynthesizer](task<Windows::Media::SpeechSynthesis::SpeechSynthesisStream^> synthesisStreamTask)
   {
       try
       {
```

La sintesi vocale viene inviata come flusso di byte. È possibile usare tale flusso di byte per inizializzare una voce XAudio2. Per gli esempi di codice olografico, viene riprodotto come effetto audio HRTF.

```
Windows::Media::SpeechSynthesis::SpeechSynthesisStream^ stream = synthesisStreamTask.get();

           auto hr = m_speechSynthesisSound.Initialize(stream, 0);
           if (SUCCEEDED(hr))
           {
               m_speechSynthesisSound.SetEnvironment(HrtfEnvironment::Small);
               m_speechSynthesisSound.Start();

               // Amount of time to pause after the audio prompt is complete, before listening
               // for speech input.
               static const float bufferTime = 0.15f;

               // Wait until the prompt is done before listening.
               m_secondsUntilSoundIsComplete = m_speechSynthesisSound.GetDuration() + bufferTime;
               m_waitingForSpeechPrompt = true;
           }
       }
```

Come per il riconoscimento vocale, la sintesi vocale genera un'eccezione in caso di problemi.

```
catch (Exception^ exception)
       {
           PrintWstringToDebugConsole(
               std::wstring(L"Exception while trying to synthesize speech: ") +
               exception->Message->Data() +
               L"\n"
               );

           // Handle exceptions here.
       }
   });
```

## <a name="see-also"></a>Vedi anche
* [Progettazione di app per il riconoscimento vocale](/windows/uwp/design/input/speech-interactions)
* [Esempio di SpeechRecognitionAndSynthesis](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/SpeechRecognitionAndSynthesis)
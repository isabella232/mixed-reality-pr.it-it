---
title: Input vocale in DirectX
description: Viene illustrato come implementare i comandi vocali e il riconoscimento di frasi e frasi brevi in un'app DirectX per la realtà mista di Windows.
author: mikeriches
ms.author: mriches
ms.date: 08/04/2020
ms.topic: article
keywords: procedura dettagliata, comando vocale, frase, riconoscimento, sintesi vocale, DirectX, piattaforma, Cortana, realtà mista di Windows
ms.openlocfilehash: 5f7ed587b474d147c0b13e4896a89f655f8dc30b
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/20/2021
ms.locfileid: "98583745"
---
# <a name="voice-input-in-directx"></a><span data-ttu-id="e6a3f-104">Input vocale in DirectX</span><span class="sxs-lookup"><span data-stu-id="e6a3f-104">Voice input in DirectX</span></span>

> [!NOTE]
> <span data-ttu-id="e6a3f-105">Questo articolo si riferisce alle API native di WinRT legacy.</span><span class="sxs-lookup"><span data-stu-id="e6a3f-105">This article relates to the legacy WinRT native APIs.</span></span>  <span data-ttu-id="e6a3f-106">Per i nuovi progetti di app native, è consigliabile usare l' **[API OpenXR](openxr-getting-started.md)**.</span><span class="sxs-lookup"><span data-stu-id="e6a3f-106">For new native app projects, we recommend using the **[OpenXR API](openxr-getting-started.md)**.</span></span>

<span data-ttu-id="e6a3f-107">Questo articolo illustra come implementare i [comandi vocali](../../design/voice-input.md) e il riconoscimento di frasi brevi e frasi in un'app DirectX per la realtà mista di Windows.</span><span class="sxs-lookup"><span data-stu-id="e6a3f-107">This article explains how to implement [voice commands](../../design/voice-input.md) plus small-phrase and sentence recognition in a DirectX app for Windows Mixed Reality.</span></span>

>[!NOTE]
><span data-ttu-id="e6a3f-108">I frammenti di codice in questo articolo usano C++/CX anziché C++/WinRT conforme a C + 17, usato nel [modello di progetto olografico c++](creating-a-holographic-directx-project.md).</span><span class="sxs-lookup"><span data-stu-id="e6a3f-108">The code snippets in this article use C++/CX rather than C++17-compliant C++/WinRT, which is used in the [C++ holographic project template](creating-a-holographic-directx-project.md).</span></span>  <span data-ttu-id="e6a3f-109">I concetti sono equivalenti per un progetto C++/WinRT, ma è necessario tradurre il codice.</span><span class="sxs-lookup"><span data-stu-id="e6a3f-109">The concepts are equivalent for a C++/WinRT project, but you need to translate the code.</span></span>

## <a name="use-speechrecognizer-for-continuous-speech-recognition"></a><span data-ttu-id="e6a3f-110">Usare SpeechRecognizer per il riconoscimento vocale continuo</span><span class="sxs-lookup"><span data-stu-id="e6a3f-110">Use SpeechRecognizer for continuous speech recognition</span></span>

<span data-ttu-id="e6a3f-111">Questa sezione descrive come usare il riconoscimento vocale continuo per abilitare i comandi vocali nell'app.</span><span class="sxs-lookup"><span data-stu-id="e6a3f-111">This section describes how to use continuous speech recognition to enable voice commands in your app.</span></span> <span data-ttu-id="e6a3f-112">Questa procedura dettagliata usa il codice dell'esempio [HolographicVoiceInput](https://go.microsoft.com/fwlink/p/?LinkId=844964) .</span><span class="sxs-lookup"><span data-stu-id="e6a3f-112">This walk-through uses code from the [HolographicVoiceInput](https://go.microsoft.com/fwlink/p/?LinkId=844964) sample.</span></span> <span data-ttu-id="e6a3f-113">Quando l'esempio è in esecuzione, pronunciare il nome di uno dei comandi colorati registrati per modificare il colore del cubo rotante.</span><span class="sxs-lookup"><span data-stu-id="e6a3f-113">When the sample is running, speak the name of one of the registered color commands to change the color of the spinning cube.</span></span>

<span data-ttu-id="e6a3f-114">Per prima cosa, creare una nuova istanza di *Windows:: media:: sintesi vocale:: SpeechRecognizer* .</span><span class="sxs-lookup"><span data-stu-id="e6a3f-114">First, create a new *Windows::Media::SpeechRecognition::SpeechRecognizer* instance.</span></span>

<span data-ttu-id="e6a3f-115">Da *HolographicVoiceInputSampleMain:: CreateSpeechConstraintsForCurrentState*:</span><span class="sxs-lookup"><span data-stu-id="e6a3f-115">From *HolographicVoiceInputSampleMain::CreateSpeechConstraintsForCurrentState*:</span></span>

```
m_speechRecognizer = ref new SpeechRecognizer();
```

<span data-ttu-id="e6a3f-116">Creare un elenco di comandi vocali per il riconoscimento da ascoltare.</span><span class="sxs-lookup"><span data-stu-id="e6a3f-116">Create a list of speech commands for the recognizer to listen for.</span></span> <span data-ttu-id="e6a3f-117">Qui viene costruito un set di comandi per modificare il colore di un ologramma.</span><span class="sxs-lookup"><span data-stu-id="e6a3f-117">Here, we construct a set of commands to change the color of a hologram.</span></span> <span data-ttu-id="e6a3f-118">Per praticità, vengono creati anche i dati che verranno usati per i comandi in un secondo momento.</span><span class="sxs-lookup"><span data-stu-id="e6a3f-118">For convenience, we also create the data that we'll use for the commands later.</span></span>

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

<span data-ttu-id="e6a3f-119">È possibile usare parole fonetiche che potrebbero non essere presenti in un dizionario per specificare i comandi.</span><span class="sxs-lookup"><span data-stu-id="e6a3f-119">You can use phonetic words that might not be in a dictionary to specify commands.</span></span>

```
m_speechCommandList->Append(StringReference(L"SpeechRecognizer"));
   m_speechCommandData.push_back(float4(0.5f, 0.1f, 1.f, 1.f));
```

<span data-ttu-id="e6a3f-120">Per caricare l'elenco di comandi nell'elenco di vincoli per il riconoscimento vocale, usare un oggetto [SpeechRecognitionListConstraint](/uwp/api/Windows.Media.SpeechRecognition.SpeechRecognitionListConstraint) .</span><span class="sxs-lookup"><span data-stu-id="e6a3f-120">To load the commands list into the list of constraints for the speech recognizer, use a [SpeechRecognitionListConstraint](/uwp/api/Windows.Media.SpeechRecognition.SpeechRecognitionListConstraint) object.</span></span>

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

<span data-ttu-id="e6a3f-121">Sottoscrivere l'evento [ResultGenerated](/uwp/api/Windows.Media.SpeechRecognition.SpeechContinuousRecognitionSession) sulla [SpeechContinuousRecognitionSession](/uwp/api/Windows.Media.SpeechRecognition.SpeechContinuousRecognitionSession)del riconoscimento vocale.</span><span class="sxs-lookup"><span data-stu-id="e6a3f-121">Subscribe to the [ResultGenerated](/uwp/api/Windows.Media.SpeechRecognition.SpeechContinuousRecognitionSession) event on the speech recognizer's [SpeechContinuousRecognitionSession](/uwp/api/Windows.Media.SpeechRecognition.SpeechContinuousRecognitionSession).</span></span> <span data-ttu-id="e6a3f-122">Questo evento invia una notifica all'app quando uno dei comandi è stato riconosciuto.</span><span class="sxs-lookup"><span data-stu-id="e6a3f-122">This event notifies your app when one of your commands has been recognized.</span></span>

```
m_speechRecognizer->ContinuousRecognitionSession->ResultGenerated +=
       ref new TypedEventHandler<SpeechContinuousRecognitionSession^, SpeechContinuousRecognitionResultGeneratedEventArgs^>(
           std::bind(&HolographicVoiceInputSampleMain::OnResultGenerated, this, _1, _2)
           );
```

<span data-ttu-id="e6a3f-123">Il gestore dell'evento *OnResultGenerated* riceve i dati dell'evento in un'istanza di [SpeechContinuousRecognitionResultGeneratedEventArgs](/uwp/api/Windows.Media.SpeechRecognition.SpeechContinuousRecognitionResultGeneratedEventArgs) .</span><span class="sxs-lookup"><span data-stu-id="e6a3f-123">Your *OnResultGenerated* event handler receives event data in a [SpeechContinuousRecognitionResultGeneratedEventArgs](/uwp/api/Windows.Media.SpeechRecognition.SpeechContinuousRecognitionResultGeneratedEventArgs) instance.</span></span> <span data-ttu-id="e6a3f-124">Se la confidenza è maggiore della soglia definita, l'applicazione deve tenere presente che si è verificato l'evento.</span><span class="sxs-lookup"><span data-stu-id="e6a3f-124">If the confidence is greater than the threshold you defined, your app should note that the event happened.</span></span> <span data-ttu-id="e6a3f-125">Salvare i dati dell'evento in modo che sia possibile utilizzarli in un ciclo di aggiornamento successivo.</span><span class="sxs-lookup"><span data-stu-id="e6a3f-125">Save the event data so that you can use it in a later update loop.</span></span>

<span data-ttu-id="e6a3f-126">Da *HolographicVoiceInputSampleMain. cpp*:</span><span class="sxs-lookup"><span data-stu-id="e6a3f-126">From *HolographicVoiceInputSampleMain.cpp*:</span></span>

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

<span data-ttu-id="e6a3f-127">Nel codice di esempio, viene modificato il colore del cubo dell'ologramma rotante in base al comando dell'utente.</span><span class="sxs-lookup"><span data-stu-id="e6a3f-127">In our example code, we change the color of the spinning hologram cube according to the user's command.</span></span>

<span data-ttu-id="e6a3f-128">Da *HolographicVoiceInputSampleMain:: Update*:</span><span class="sxs-lookup"><span data-stu-id="e6a3f-128">From *HolographicVoiceInputSampleMain::Update*:</span></span>

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

## <a name="use-one-shot-recognition"></a><span data-ttu-id="e6a3f-129">Usa il riconoscimento "One-Shot"</span><span class="sxs-lookup"><span data-stu-id="e6a3f-129">Use "one-shot" recognition</span></span>

<span data-ttu-id="e6a3f-130">È possibile configurare un riconoscimento vocale per ascoltare frasi o frasi pronunciate dall'utente.</span><span class="sxs-lookup"><span data-stu-id="e6a3f-130">You can configure a speech recognizer to listen for phrases or sentences that the user speaks.</span></span> <span data-ttu-id="e6a3f-131">In questo caso, viene applicato un *SpeechRecognitionTopicConstraint* che indica al riconoscimento vocale il tipo di input previsto.</span><span class="sxs-lookup"><span data-stu-id="e6a3f-131">In this case, we apply a *SpeechRecognitionTopicConstraint* that tells the speech recognizer what type of input to expect.</span></span> <span data-ttu-id="e6a3f-132">Ecco un flusso di lavoro dell'app per questo scenario:</span><span class="sxs-lookup"><span data-stu-id="e6a3f-132">Here's an app workflow for this scenario:</span></span>
1. <span data-ttu-id="e6a3f-133">L'app crea il SpeechRecognizer, fornisce prompt dell'interfaccia utente e inizia l'ascolto di un comando parlato.</span><span class="sxs-lookup"><span data-stu-id="e6a3f-133">Your app creates the SpeechRecognizer, provides UI prompts, and starts listening for a spoken command.</span></span>
2. <span data-ttu-id="e6a3f-134">L'utente pronuncia una frase o una frase.</span><span class="sxs-lookup"><span data-stu-id="e6a3f-134">The user speaks a phrase or sentence.</span></span>
3. <span data-ttu-id="e6a3f-135">Il riconoscimento della voce dell'utente si verifica e viene restituito un risultato all'app.</span><span class="sxs-lookup"><span data-stu-id="e6a3f-135">Recognition of the user's speech occurs, and a result is returned to the app.</span></span> <span data-ttu-id="e6a3f-136">A questo punto, l'app deve fornire un prompt dell'interfaccia utente per indicare che si è verificato il riconoscimento.</span><span class="sxs-lookup"><span data-stu-id="e6a3f-136">At this point, your app should provide a UI prompt to indicate that recognition has occurred.</span></span>
4. <span data-ttu-id="e6a3f-137">A seconda del livello di confidenza a cui si desidera rispondere e del livello di confidenza del risultato del riconoscimento vocale, l'app può elaborare il risultato e rispondere nel modo appropriato.</span><span class="sxs-lookup"><span data-stu-id="e6a3f-137">Depending on the confidence level that you want to respond to and the confidence level of the speech recognition result, your app can process the result and respond as appropriate.</span></span>

<span data-ttu-id="e6a3f-138">Questa sezione descrive come creare un SpeechRecognizer, compilare il vincolo e restare in ascolto dell'input vocale.</span><span class="sxs-lookup"><span data-stu-id="e6a3f-138">This section describes how to create a SpeechRecognizer, compile the constraint, and listen for speech input.</span></span>

<span data-ttu-id="e6a3f-139">Il codice seguente compila il vincolo dell'argomento, che in questo caso è ottimizzato per la ricerca Web.</span><span class="sxs-lookup"><span data-stu-id="e6a3f-139">The following code compiles the topic constraint, which in this case is optimized for web search.</span></span>

```
auto constraint = ref new SpeechRecognitionTopicConstraint(SpeechRecognitionScenario::WebSearch, L"webSearch");
   m_speechRecognizer->Constraints->Clear();
   m_speechRecognizer->Constraints->Append(constraint);
   return create_task(m_speechRecognizer->CompileConstraintsAsync())
       .then([this](task<SpeechRecognitionCompilationResult^> previousTask)
   {
```

<span data-ttu-id="e6a3f-140">Se la compilazione ha esito positivo, è possibile continuare con il riconoscimento vocale.</span><span class="sxs-lookup"><span data-stu-id="e6a3f-140">If compilation succeeds, we can continue with speech recognition.</span></span>

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

<span data-ttu-id="e6a3f-141">Il risultato viene quindi restituito all'app.</span><span class="sxs-lookup"><span data-stu-id="e6a3f-141">The result is then returned to the app.</span></span> <span data-ttu-id="e6a3f-142">Se il risultato è sufficientemente sicuro, è possibile elaborare il comando.</span><span class="sxs-lookup"><span data-stu-id="e6a3f-142">If we're confident enough in the result, we can process the command.</span></span> <span data-ttu-id="e6a3f-143">Questo esempio di codice elabora i risultati con almeno una confidenza media.</span><span class="sxs-lookup"><span data-stu-id="e6a3f-143">This code example processes results with at least medium confidence.</span></span>

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

<span data-ttu-id="e6a3f-144">Quando si usa il riconoscimento vocale, controllare le eccezioni che potrebbero indicare che l'utente ha disattivato il microfono nelle impostazioni relative alla privacy del sistema.</span><span class="sxs-lookup"><span data-stu-id="e6a3f-144">Whenever you use speech recognition, watch for exceptions that could indicate that the user has turned off the microphone in the system privacy settings.</span></span> <span data-ttu-id="e6a3f-145">Questo problema può verificarsi durante l'inizializzazione o il riconoscimento.</span><span class="sxs-lookup"><span data-stu-id="e6a3f-145">This can happen during initialization or recognition.</span></span>

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
> <span data-ttu-id="e6a3f-146">Sono disponibili diversi [SpeechRecognitionScenarios](/uwp/api/Windows.Media.SpeechRecognition.SpeechRecognitionScenario) predefiniti che è possibile usare per ottimizzare il riconoscimento vocale.</span><span class="sxs-lookup"><span data-stu-id="e6a3f-146">There are several predefined [SpeechRecognitionScenarios](/uwp/api/Windows.Media.SpeechRecognition.SpeechRecognitionScenario) that you can use to optimize speech recognition.</span></span>

* <span data-ttu-id="e6a3f-147">Per ottimizzare la dettatura, utilizzare lo scenario di dettatura.</span><span class="sxs-lookup"><span data-stu-id="e6a3f-147">To optimize for dictation, use the dictation scenario.</span></span><br/>
   ```
   // Compile the dictation topic constraint, which optimizes for speech dictation.
   auto dictationConstraint = ref new SpeechRecognitionTopicConstraint(SpeechRecognitionScenario::Dictation, "dictation");
   m_speechRecognizer->Constraints->Append(dictationConstraint);
   ```

* <span data-ttu-id="e6a3f-148">Per le ricerche web vocali, utilizzare il seguente vincolo di scenario specifico per il Web.</span><span class="sxs-lookup"><span data-stu-id="e6a3f-148">For speech web searches, use the following web-specific scenario constraint.</span></span>

   ```
   // Add a web search topic constraint to the recognizer.
   auto webSearchConstraint = ref new SpeechRecognitionTopicConstraint(SpeechRecognitionScenario::WebSearch, "webSearch");
   speechRecognizer->Constraints->Append(webSearchConstraint);
   ```

* <span data-ttu-id="e6a3f-149">Utilizzare il vincolo form per compilare i moduli.</span><span class="sxs-lookup"><span data-stu-id="e6a3f-149">Use the form constraint to fill out forms.</span></span> <span data-ttu-id="e6a3f-150">In questo caso, è preferibile applicare la propria grammatica ottimizzata per compilare il modulo.</span><span class="sxs-lookup"><span data-stu-id="e6a3f-150">In this case, it's best to apply your own grammar that's optimized for filling out the form.</span></span>

   ```
   // Add a form constraint to the recognizer.
   auto formConstraint = ref new SpeechRecognitionTopicConstraint(SpeechRecognitionScenario::FormFilling, "formFilling");
   speechRecognizer->Constraints->Append(formConstraint );
   ```
* <span data-ttu-id="e6a3f-151">È possibile fornire la propria grammatica nel formato SRGS.</span><span class="sxs-lookup"><span data-stu-id="e6a3f-151">You can provide your own grammar in the SRGS format.</span></span>

## <a name="use-continuous-recognition"></a><span data-ttu-id="e6a3f-152">Usa il riconoscimento continuo</span><span class="sxs-lookup"><span data-stu-id="e6a3f-152">Use continuous recognition</span></span>

<span data-ttu-id="e6a3f-153">Per lo scenario di dettatura continua, vedere l' [esempio di codice di riconoscimento vocale di Windows 10 UWP](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpeechRecognitionAndSynthesis/cpp/Scenario_ContinuousDictation.xaml.cpp).</span><span class="sxs-lookup"><span data-stu-id="e6a3f-153">For the continuous-dictation scenario, see the [Windows 10 UWP speech code sample](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpeechRecognitionAndSynthesis/cpp/Scenario_ContinuousDictation.xaml.cpp).</span></span>

## <a name="handle-quality-degradation"></a><span data-ttu-id="e6a3f-154">Gestione della riduzione della qualità</span><span class="sxs-lookup"><span data-stu-id="e6a3f-154">Handle quality degradation</span></span>

<span data-ttu-id="e6a3f-155">Le condizioni ambientali talvolta interferiscono con il riconoscimento vocale.</span><span class="sxs-lookup"><span data-stu-id="e6a3f-155">Environmental conditions sometimes interfere with speech recognition.</span></span> <span data-ttu-id="e6a3f-156">Ad esempio, la stanza potrebbe essere troppo rumorosa o l'utente potrebbe parlare troppo forte.</span><span class="sxs-lookup"><span data-stu-id="e6a3f-156">For example, the room might be too noisy, or the user might speak too loudly.</span></span> <span data-ttu-id="e6a3f-157">Quando possibile, l'API riconoscimento vocale fornisce informazioni sulle condizioni che hanno causato la riduzione della qualità.</span><span class="sxs-lookup"><span data-stu-id="e6a3f-157">Whenever possible, the speech recognition API provides information about the conditions that caused the quality degradation.</span></span> <span data-ttu-id="e6a3f-158">Queste informazioni vengono inserite nell'app tramite un evento WinRT.</span><span class="sxs-lookup"><span data-stu-id="e6a3f-158">This information is pushed to your app through a WinRT event.</span></span> <span data-ttu-id="e6a3f-159">Nell'esempio seguente viene illustrato come sottoscrivere questo evento.</span><span class="sxs-lookup"><span data-stu-id="e6a3f-159">The following example shows  how to subscribe to this event.</span></span>

```
m_speechRecognizer->RecognitionQualityDegrading +=
       ref new TypedEventHandler<SpeechRecognizer^, SpeechRecognitionQualityDegradingEventArgs^>(
           std::bind(&HolographicVoiceInputSampleMain::OnSpeechQualityDegraded, this, _1, _2)
           );
```

<span data-ttu-id="e6a3f-160">Nell'esempio di codice vengono scritte le informazioni sulle condizioni nella console di debug.</span><span class="sxs-lookup"><span data-stu-id="e6a3f-160">In our code sample, we write the conditions information to the debug console.</span></span> <span data-ttu-id="e6a3f-161">Un'app potrebbe voler fornire feedback all'utente tramite l'interfaccia utente, la sintesi vocale e un altro metodo.</span><span class="sxs-lookup"><span data-stu-id="e6a3f-161">An app might want to provide feedback to the user through the UI, speech synthesis, and another method.</span></span> <span data-ttu-id="e6a3f-162">In alternativa, potrebbe essere necessario comportarsi in modo diverso quando il discorso viene interrotto da una riduzione temporanea della qualità.</span><span class="sxs-lookup"><span data-stu-id="e6a3f-162">Or it might need to behave differently when speech is interrupted by a temporary reduction in quality.</span></span>

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

<span data-ttu-id="e6a3f-163">Se non si usano le classi di riferimento per creare l'app DirectX, è necessario annullare la sottoscrizione all'evento prima di rilasciare o ricreare il riconoscimento vocale.</span><span class="sxs-lookup"><span data-stu-id="e6a3f-163">If you're not using ref classes to create your DirectX app, you must unsubscribe from the event before you release or recreate your speech recognizer.</span></span> <span data-ttu-id="e6a3f-164">HolographicSpeechPromptSample dispone di una routine per arrestare il riconoscimento e annullare la sottoscrizione agli eventi.</span><span class="sxs-lookup"><span data-stu-id="e6a3f-164">The HolographicSpeechPromptSample has a routine to stop recognition and unsubscribe from events.</span></span>

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

## <a name="use-speech-synthesis-to-provide-audible-prompts"></a><span data-ttu-id="e6a3f-165">Usare la sintesi vocale per fornire richieste acustiche</span><span class="sxs-lookup"><span data-stu-id="e6a3f-165">Use speech synthesis to provide audible prompts</span></span>

<span data-ttu-id="e6a3f-166">Gli esempi di riconoscimento vocale olografico usano la sintesi vocale per fornire istruzioni acustiche all'utente.</span><span class="sxs-lookup"><span data-stu-id="e6a3f-166">The holographic speech samples use speech synthesis to provide audible instructions to the user.</span></span> <span data-ttu-id="e6a3f-167">Questa sezione illustra come creare un esempio di voce sintetizzata e riprodurlo con le API HRTF audio.</span><span class="sxs-lookup"><span data-stu-id="e6a3f-167">This section shows how to create a synthesized voice sample  and then play it back through the HRTF audio APIs.</span></span>

<span data-ttu-id="e6a3f-168">Quando si richiede l'input di frasi, è consigliabile fornire le proprie richieste di riconoscimento vocale.</span><span class="sxs-lookup"><span data-stu-id="e6a3f-168">We recommend providing your own speech prompts when you request phrase input.</span></span> <span data-ttu-id="e6a3f-169">I prompt possono anche indicare quando è possibile pronunciare i comandi vocali per uno scenario di riconoscimento continuo.</span><span class="sxs-lookup"><span data-stu-id="e6a3f-169">Prompts can also help indicate when speech commands can be spoken for a continuous-recognition scenario.</span></span> <span data-ttu-id="e6a3f-170">Nell'esempio seguente viene illustrato come utilizzare un sintetizzatore vocale a tale scopo.</span><span class="sxs-lookup"><span data-stu-id="e6a3f-170">The following example demonstrates how to use a speech synthesizer to do this.</span></span> <span data-ttu-id="e6a3f-171">È anche possibile usare un clip vocale pre-registrato, un'interfaccia utente visiva o un altro indicatore degli elementi da pronunciare, ad esempio negli scenari in cui il messaggio di richiesta non è dinamico.</span><span class="sxs-lookup"><span data-stu-id="e6a3f-171">You could also use a pre-recorded voice clip, a visual UI, or another indicator of what to say, for example in scenarios where the prompt isn't dynamic.</span></span>

<span data-ttu-id="e6a3f-172">Per prima cosa, creare l'oggetto SpeechSynthesizer.</span><span class="sxs-lookup"><span data-stu-id="e6a3f-172">First, create the SpeechSynthesizer object.</span></span>

```
auto speechSynthesizer = ref new Windows::Media::SpeechSynthesis::SpeechSynthesizer();
```

<span data-ttu-id="e6a3f-173">È anche necessaria una stringa che includa il testo da sintetizzare.</span><span class="sxs-lookup"><span data-stu-id="e6a3f-173">You also need a string that includes the text to  synthesize.</span></span>

```
// Phrase recognition works best when requesting a phrase or sentence.
   StringReference voicePrompt = L"At the prompt: Say a phrase, asking me to change the cube to a specific color.";
```

<span data-ttu-id="e6a3f-174">Il riconoscimento vocale viene sintetizzato in modo asincrono tramite SynthesizeTextToStreamAsync.</span><span class="sxs-lookup"><span data-stu-id="e6a3f-174">Speech is synthesized asynchronously through SynthesizeTextToStreamAsync.</span></span> <span data-ttu-id="e6a3f-175">Qui viene avviata un'attività asincrona per sintetizzare il discorso.</span><span class="sxs-lookup"><span data-stu-id="e6a3f-175">Here, we start an async task to synthesize the speech.</span></span>

```
create_task(speechSynthesizer->SynthesizeTextToStreamAsync(voicePrompt), task_continuation_context::use_current())
       .then([this, speechSynthesizer](task<Windows::Media::SpeechSynthesis::SpeechSynthesisStream^> synthesisStreamTask)
   {
       try
       {
```

<span data-ttu-id="e6a3f-176">La sintesi vocale viene inviata come flusso di byte.</span><span class="sxs-lookup"><span data-stu-id="e6a3f-176">The speech synthesis is sent as a byte stream.</span></span> <span data-ttu-id="e6a3f-177">È possibile usare il flusso di byte per inizializzare una voce XAudio2.</span><span class="sxs-lookup"><span data-stu-id="e6a3f-177">We can use that byte stream to initialize an XAudio2 voice.</span></span> <span data-ttu-id="e6a3f-178">Per gli esempi di codice olografico, viene riprodotto come effetto audio HRTF.</span><span class="sxs-lookup"><span data-stu-id="e6a3f-178">For our holographic code samples, we play it back as an HRTF audio effect.</span></span>

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

<span data-ttu-id="e6a3f-179">Come per il riconoscimento vocale, la sintesi vocale genera un'eccezione se si verifica un errore.</span><span class="sxs-lookup"><span data-stu-id="e6a3f-179">As with speech recognition, speech synthesis throws an exception if something goes wrong.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="e6a3f-180">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="e6a3f-180">See also</span></span>
* [<span data-ttu-id="e6a3f-181">Progettazione di app vocali</span><span class="sxs-lookup"><span data-stu-id="e6a3f-181">Speech app design</span></span>](/windows/uwp/design/input/speech-interactions)
* [<span data-ttu-id="e6a3f-182">Esempio SpeechRecognitionAndSynthesis</span><span class="sxs-lookup"><span data-stu-id="e6a3f-182">SpeechRecognitionAndSynthesis sample</span></span>](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/SpeechRecognitionAndSynthesis)
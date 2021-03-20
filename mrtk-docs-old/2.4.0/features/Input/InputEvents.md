---
title: InputEvents
description: Documentazione per InputEvents in MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
ms.localizationpriority: medium
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, eventi,
ms.openlocfilehash: 7e2e9fa162a97fe73b6d335c0c129eb50442dedb
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2021
ms.locfileid: "104682774"
---
# <a name="input-events"></a><span data-ttu-id="0b869-104">Eventi di input</span><span class="sxs-lookup"><span data-stu-id="0b869-104">Input events</span></span>

<span data-ttu-id="0b869-105">L'elenco seguente descrive tutte le interfacce degli eventi di input disponibili che devono essere implementate da un componente monobehavior personalizzato.</span><span class="sxs-lookup"><span data-stu-id="0b869-105">The list below outlines all available input event interfaces to be implemented by a custom MonoBehaviour component.</span></span> <span data-ttu-id="0b869-106">Queste interfacce verranno chiamate dal sistema di input MRTK per gestire la logica dell'app personalizzata in base alle interazioni di input dell'utente.</span><span class="sxs-lookup"><span data-stu-id="0b869-106">These interfaces will be called by the MRTK input system to handle custom app logic based on user input interactions.</span></span> <span data-ttu-id="0b869-107">[Gli eventi di input del puntatore](pointers.md#pointer-event-interfaces) vengono gestiti in modo leggermente diverso rispetto ai tipi di evento di input standard seguenti.</span><span class="sxs-lookup"><span data-stu-id="0b869-107">[Pointer input events](pointers.md#pointer-event-interfaces) are handled slightly differently than the standard input event types below.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="0b869-108">Per impostazione predefinita, uno script riceverà gli eventi di input solo se il GameObject è attivo da un puntatore o un elemento padre di un GameObject nello stato attivo.</span><span class="sxs-lookup"><span data-stu-id="0b869-108">By default, a script will receive input events only if it is the GameObject in focus by a pointer or parent of a GameObject in focus.</span></span>

| <span data-ttu-id="0b869-109">Gestore</span><span class="sxs-lookup"><span data-stu-id="0b869-109">Handler</span></span> | <span data-ttu-id="0b869-110">Eventi</span><span class="sxs-lookup"><span data-stu-id="0b869-110">Events</span></span> | <span data-ttu-id="0b869-111">Descrizione</span><span class="sxs-lookup"><span data-stu-id="0b869-111">Description</span></span> |
| --- | :---: | --- |
| [`IMixedRealitySourceStateHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySourceStateHandler) | <span data-ttu-id="0b869-112">Origine rilevata/persa</span><span class="sxs-lookup"><span data-stu-id="0b869-112">Source Detected / Lost</span></span> | <span data-ttu-id="0b869-113">Generato quando viene rilevata o persa un'origine di input, ad esempio quando viene rilevata una mano articolata o ne viene persa la traccia.</span><span class="sxs-lookup"><span data-stu-id="0b869-113">Raised when an input source is detected/lost, like when an articulated hand is detected or lost track of.</span></span> |
| [`IMixedRealitySourcePoseHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySourcePoseHandler) | <span data-ttu-id="0b869-114">Modifica dell'origine modificata</span><span class="sxs-lookup"><span data-stu-id="0b869-114">Source Pose Changed</span></span> | <span data-ttu-id="0b869-115">Generato in base alle modifiche apportate all'origine.</span><span class="sxs-lookup"><span data-stu-id="0b869-115">Raised on source pose changes.</span></span> <span data-ttu-id="0b869-116">La posa di origine rappresenta la causa generale dell'origine di input.</span><span class="sxs-lookup"><span data-stu-id="0b869-116">The source pose represents the general pose of the input source.</span></span> <span data-ttu-id="0b869-117">Le pose specifiche, ad esempio il grip o il puntatore che si pongono in un sei controller DOF, possono essere ottenute tramite `IMixedRealityInputHandler<MixedRealityPose>` .</span><span class="sxs-lookup"><span data-stu-id="0b869-117">Specific poses, like the grip or pointer pose in a six DOF controller, can be obtained via `IMixedRealityInputHandler<MixedRealityPose>`.</span></span> |
| [`IMixedRealityInputHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler) | <span data-ttu-id="0b869-118">Input inattivo/alto</span><span class="sxs-lookup"><span data-stu-id="0b869-118">Input Down / Up</span></span> | <span data-ttu-id="0b869-119">Generato in merito a modifiche apportate a input binari come pulsanti.</span><span class="sxs-lookup"><span data-stu-id="0b869-119">Raised on changes to binary inputs like buttons.</span></span> |
| [`IMixedRealityInputHandler<T>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler`1) | <span data-ttu-id="0b869-120">Input modificato</span><span class="sxs-lookup"><span data-stu-id="0b869-120">Input Changed</span></span> | <span data-ttu-id="0b869-121">Generato in base alle modifiche apportate agli input del tipo specificato.</span><span class="sxs-lookup"><span data-stu-id="0b869-121">Raised on changes to inputs of the given type.</span></span> <span data-ttu-id="0b869-122">**T** può assumere i valori seguenti:</span><span class="sxs-lookup"><span data-stu-id="0b869-122">**T** can take the following values:</span></span> <br/> <span data-ttu-id="0b869-123">- *float* (ad esempio, restituisce un trigger analogo)</span><span class="sxs-lookup"><span data-stu-id="0b869-123">- *float* (e.g returns analog trigger)</span></span><br/> <span data-ttu-id="0b869-124">- *Vector2* (ad esempio, restituisce la direzione del levetta del gamepad)</span><span class="sxs-lookup"><span data-stu-id="0b869-124">- *Vector2* (e.g returns gamepad thumbstick direction)</span></span> <br/> <span data-ttu-id="0b869-125">- *Vector3* (ad esempio, la posizione di ritorno del dispositivo rilevato)</span><span class="sxs-lookup"><span data-stu-id="0b869-125">- *Vector3* (e.g return position of tracked device)</span></span> <br/> <span data-ttu-id="0b869-126">- *Quaternione* (ad esempio, restituisce l'orientamento del dispositivo rilevato)</span><span class="sxs-lookup"><span data-stu-id="0b869-126">- *Quaternion* (e.g returns orientation of tracked device)</span></span><br/> <span data-ttu-id="0b869-127">- [MixedRealityPose](xref:Microsoft.MixedReality.Toolkit.Utilities.MixedRealityPose) (ad esempio, restituisce un dispositivo completamente rilevato)</span><span class="sxs-lookup"><span data-stu-id="0b869-127">- [MixedRealityPose](xref:Microsoft.MixedReality.Toolkit.Utilities.MixedRealityPose) (e.g. returns fully tracked device)</span></span> |
| [`IMixedRealitySpeechHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySpeechHandler) | <span data-ttu-id="0b869-128">Parola chiave Speech riconosciuta</span><span class="sxs-lookup"><span data-stu-id="0b869-128">Speech Keyword Recognized</span></span> | <span data-ttu-id="0b869-129">Generato al riconoscimento di una delle parole chiave configurate nel *profilo dei comandi vocali*.</span><span class="sxs-lookup"><span data-stu-id="0b869-129">Raised on recognition of one of the keywords configured in the *Speech Commands Profile*.</span></span> |
| [`IMixedRealityDictationHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityDictationHandler) | <span data-ttu-id="0b869-130">Dettatura</span><span class="sxs-lookup"><span data-stu-id="0b869-130">Dictation</span></span><br/> <span data-ttu-id="0b869-131">Hypothesis</span><span class="sxs-lookup"><span data-stu-id="0b869-131">Hypothesis</span></span> <br/> <span data-ttu-id="0b869-132">Risultato</span><span class="sxs-lookup"><span data-stu-id="0b869-132">Result</span></span> <br/> <span data-ttu-id="0b869-133">Operazione completata</span><span class="sxs-lookup"><span data-stu-id="0b869-133">Complete</span></span> <br/> <span data-ttu-id="0b869-134">Errore</span><span class="sxs-lookup"><span data-stu-id="0b869-134">Error</span></span> | <span data-ttu-id="0b869-135">Generato da sistemi di dettatura per segnalare i risultati di una sessione di dettatura.</span><span class="sxs-lookup"><span data-stu-id="0b869-135">Raised by dictation systems to report the results of a dictation session.</span></span> |
| [`IMixedRealityGestureHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGestureHandler) | <span data-ttu-id="0b869-136">Eventi movimento su:</span><span class="sxs-lookup"><span data-stu-id="0b869-136">Gesture events on:</span></span> <br/> <span data-ttu-id="0b869-137">Avviato</span><span class="sxs-lookup"><span data-stu-id="0b869-137">Started</span></span> <br/> <span data-ttu-id="0b869-138">Aggiornato</span><span class="sxs-lookup"><span data-stu-id="0b869-138">Updated</span></span> <br/> <span data-ttu-id="0b869-139">Completato</span><span class="sxs-lookup"><span data-stu-id="0b869-139">Completed</span></span> <br/> <span data-ttu-id="0b869-140">Cancellati</span><span class="sxs-lookup"><span data-stu-id="0b869-140">Canceled</span></span> | <span data-ttu-id="0b869-141">Generato al rilevamento del movimento.</span><span class="sxs-lookup"><span data-stu-id="0b869-141">Raised on gesture detection.</span></span> |
| [`IMixedRealityGestureHandler<T>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGestureHandler`1) | <span data-ttu-id="0b869-142">Gesto aggiornato/completato</span><span class="sxs-lookup"><span data-stu-id="0b869-142">Gesture Updated / Completed</span></span> | <span data-ttu-id="0b869-143">Generato al rilevamento di movimenti contenenti dati aggiuntivi del tipo specificato.</span><span class="sxs-lookup"><span data-stu-id="0b869-143">Raised on detection of gestures containing additional data of the given type.</span></span> <span data-ttu-id="0b869-144">Per informazioni dettagliate sui valori possibili per **T**, vedere [**eventi di movimento**](Gestures.md#gesture-events) .</span><span class="sxs-lookup"><span data-stu-id="0b869-144">See [**gesture events**](Gestures.md#gesture-events) for details on possible values for **T**.</span></span> |
| [`IMixedRealityHandJointHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHandJointHandler) | <span data-ttu-id="0b869-145">Giunzioni della mano aggiornate</span><span class="sxs-lookup"><span data-stu-id="0b869-145">Hand Joints Updated</span></span> | <span data-ttu-id="0b869-146">Generato da controller della mano articolati quando vengono aggiornati i giunti di mano.</span><span class="sxs-lookup"><span data-stu-id="0b869-146">Raised by articulated hand controllers when hand joints are updated.</span></span> |
| [`IMixedRealityHandMeshHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHandMeshHandler) | <span data-ttu-id="0b869-147">Mesh a mano aggiornata</span><span class="sxs-lookup"><span data-stu-id="0b869-147">Hand Mesh Updated</span></span> | <span data-ttu-id="0b869-148">Generato da controller della mano articolati quando viene aggiornata una mesh mano.</span><span class="sxs-lookup"><span data-stu-id="0b869-148">Raised by articulated hand controllers when a hand mesh is updated.</span></span> |
| [`IMixedRealityInputActionHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputActionHandler) | <span data-ttu-id="0b869-149">Azione avviata/terminata</span><span class="sxs-lookup"><span data-stu-id="0b869-149">Action Started / Ended</span></span> | <span data-ttu-id="0b869-150">Raise per indicare l'inizio e la fine dell'azione per gli input mappati alle azioni.</span><span class="sxs-lookup"><span data-stu-id="0b869-150">Raise to indicate action start and end for inputs mapped to actions.</span></span> |

## <a name="input-events-in-action"></a><span data-ttu-id="0b869-151">Eventi di input in azione</span><span class="sxs-lookup"><span data-stu-id="0b869-151">Input events in action</span></span>

<span data-ttu-id="0b869-152">A livello di script, gli eventi di input possono essere utilizzati implementando una delle interfacce del gestore eventi illustrate nella tabella precedente.</span><span class="sxs-lookup"><span data-stu-id="0b869-152">At the script level, input events can be consumed by implementing one of the event handler interfaces shown in the table above.</span></span> <span data-ttu-id="0b869-153">Quando viene generato un evento di input tramite un'interazione dell'utente, si verifica quanto segue:</span><span class="sxs-lookup"><span data-stu-id="0b869-153">When an input event fires via a user interaction, the following takes place:</span></span>

1. <span data-ttu-id="0b869-154">Il sistema di input MRTK rileva che si è verificato un evento di input.</span><span class="sxs-lookup"><span data-stu-id="0b869-154">The MRTK input system recognizes that an input event has occurred.</span></span>
1. <span data-ttu-id="0b869-155">Il sistema di input MRTK genera la funzione di interfaccia pertinente dell'evento di input in tutti i [gestori di input globali registrati](#register-for-global-input-events)</span><span class="sxs-lookup"><span data-stu-id="0b869-155">The MRTK input system fires the relevant interface function of the input event to all [registered global input handlers](#register-for-global-input-events)</span></span>
1. <span data-ttu-id="0b869-156">Per ogni puntatore attivo registrato con il sistema di input:</span><span class="sxs-lookup"><span data-stu-id="0b869-156">For every active pointer registered with the input system:</span></span>
    1. <span data-ttu-id="0b869-157">Il sistema di input determina quale GameObject è attivo per il puntatore corrente.</span><span class="sxs-lookup"><span data-stu-id="0b869-157">The input system determines which GameObject is in focus for the current pointer.</span></span>
    1. <span data-ttu-id="0b869-158">Il sistema di input usa il [sistema di eventi di Unity](https://docs.unity3d.com/Manual/EventSystem.html) per attivare la funzione di interfaccia pertinente per tutti i componenti corrispondenti nel GameObject attivo.</span><span class="sxs-lookup"><span data-stu-id="0b869-158">The input system utilizes [Unity's event system](https://docs.unity3d.com/Manual/EventSystem.html) to fire the relevant interface function for all matching components on the focused GameObject.</span></span>
    1. <span data-ttu-id="0b869-159">Se in qualsiasi momento un evento di input è stato [contrassegnato come usato](#how-to-stop-input-events), il processo terminerà e nessun altro GameObject riceverà i callback.</span><span class="sxs-lookup"><span data-stu-id="0b869-159">If at any point an input event has been [marked as used](#how-to-stop-input-events), the process will end and no further GameObjects will receive callbacks.</span></span>
        - <span data-ttu-id="0b869-160">Esempio: i componenti che implementano l'interfaccia [`IMixedRealitySpeechHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySpeechHandler) verranno cercati quando viene riconosciuto un comando vocale.</span><span class="sxs-lookup"><span data-stu-id="0b869-160">Example: Components implementing the interface [`IMixedRealitySpeechHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySpeechHandler) will be searched for when a speech command is recognized.</span></span>
        - <span data-ttu-id="0b869-161">Nota: il sistema di eventi Unity verrà propagato per eseguire una ricerca nel GameObject padre se non sono stati trovati componenti corrispondenti all'interfaccia desiderata nell'GameObject corrente.</span><span class="sxs-lookup"><span data-stu-id="0b869-161">Note: The Unity event system will bubble up to search the parent GameObject if no components matching the desired interface are found on the current GameObject.</span></span>
1. <span data-ttu-id="0b869-162">Se non viene registrato alcun gestore di input globale e non viene trovato alcun GameObject con un componente/interfaccia corrispondente, il sistema di input chiamerà ogni gestore di input di fallback registrato</span><span class="sxs-lookup"><span data-stu-id="0b869-162">If no global input handlers are registered and no GameObject is found with a matching component/interface, then the input system will call each fallback registered input handler</span></span>

> [!NOTE]
> <span data-ttu-id="0b869-163">[Gli eventi di input del puntatore](pointers.md#pointer-event-interfaces) vengono gestiti in modo leggermente diverso rispetto alle interfacce degli eventi di input elencate in precedenza.</span><span class="sxs-lookup"><span data-stu-id="0b869-163">[Pointer input events](pointers.md#pointer-event-interfaces) are handled in a slightly different manner than the input event interfaces listed above.</span></span> <span data-ttu-id="0b869-164">In particolare, gli eventi di input del puntatore vengono gestiti solo dal GameObject attivo dal puntatore che ha attivato l'evento di input, nonché da eventuali gestori di input globali.</span><span class="sxs-lookup"><span data-stu-id="0b869-164">In particular, pointer input events are handled only by the GameObject in focus by the pointer that fired the input event - as well as any global input handlers.</span></span> <span data-ttu-id="0b869-165">Gli eventi di input normali vengono gestiti da GameObject in stato attivo per tutti i puntatori attivi.</span><span class="sxs-lookup"><span data-stu-id="0b869-165">Regular input events are handled by GameObjects in focus for all active pointers.</span></span>

### <a name="input-event-interface-example"></a><span data-ttu-id="0b869-166">Esempio di interfaccia evento di input</span><span class="sxs-lookup"><span data-stu-id="0b869-166">Input event interface example</span></span>

<span data-ttu-id="0b869-167">Il codice seguente illustra l'uso dell' [`IMixedRealitySpeechHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySpeechHandler) interfaccia.</span><span class="sxs-lookup"><span data-stu-id="0b869-167">The code below demonstrates use of the [`IMixedRealitySpeechHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySpeechHandler) interface.</span></span> <span data-ttu-id="0b869-168">Quando l'utente indica le parole "più piccole" o "più grandi", concentrandosi su un GameObject con questa `ShowHideSpeechHandler` classe, il GameObject verrà ridimensionato a metà o due volte.</span><span class="sxs-lookup"><span data-stu-id="0b869-168">When the user says the words "smaller" or "bigger" while focusing on a GameObject with this `ShowHideSpeechHandler` class, the GameObject will scale itself by half or twice as much.</span></span>

```c#
public class ShowHideSpeechHandler : MonoBehaviour, IMixedRealitySpeechHandler
{
    ...

    void IMixedRealitySpeechHandler.OnSpeechKeywordRecognized(SpeechEventData eventData)
    {
        if (eventData.Command.Keyword == "smaller")
        {
            transform.localScale *= 0.5f;
        }
        else if (eventData.Command.Keyword == "bigger")
        {
            transform.localScale *= 2.0f;
        }
    }
}
```

> [!NOTE]
> <span data-ttu-id="0b869-169">[`IMixedRealitySpeechHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySpeechHandler) per gli eventi di input è necessario che le parole chiave desiderate siano pre-registrate nel [profilo dei comandi vocali MRTK](Speech.md).</span><span class="sxs-lookup"><span data-stu-id="0b869-169">[`IMixedRealitySpeechHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySpeechHandler) input events require that the desired keywords are pre-registered in the [MRTK Speech Commands Profile](Speech.md).</span></span>

## <a name="register-for-global-input-events"></a><span data-ttu-id="0b869-170">Registra per gli eventi di input globali</span><span class="sxs-lookup"><span data-stu-id="0b869-170">Register for global input events</span></span>

<span data-ttu-id="0b869-171">Per creare un componente che rimane in ascolto di eventi di input globali, indipendentemente da quale GameObject potrebbe essere attivo, un componente deve registrarsi con il sistema di input.</span><span class="sxs-lookup"><span data-stu-id="0b869-171">To create a component that listens for global input events, disregarding what GameObject may be in focus, a component must register itself with the Input System.</span></span> <span data-ttu-id="0b869-172">Una volta effettuata la registrazione, tutte le istanze di questo monocomportamento riceveranno gli eventi di input insieme a qualsiasi GameObject attualmente attivo e ad altri listener registrati a livello globale.</span><span class="sxs-lookup"><span data-stu-id="0b869-172">Once registered, any instances of this MonoBehaviour will receive input events along with any GameObject(s) currently in focus and other global registered listeners.</span></span>

<span data-ttu-id="0b869-173">Se un evento di input è stato [contrassegnato come usato](#how-to-stop-input-events), i gestori registrati globali riceveranno comunque tutti i callback.</span><span class="sxs-lookup"><span data-stu-id="0b869-173">If an input event has been [marked as used](#how-to-stop-input-events), global registered handlers will still all receive callbacks.</span></span> <span data-ttu-id="0b869-174">Tuttavia, nessun GameObject con stato attivo riceverà l'evento.</span><span class="sxs-lookup"><span data-stu-id="0b869-174">However, no focused GameObjects will receive the event.</span></span>

### <a name="global-input-registration-example"></a><span data-ttu-id="0b869-175">Esempio di registrazione di input globale</span><span class="sxs-lookup"><span data-stu-id="0b869-175">Global input registration example</span></span>

```c#
public class GlobalHandListenerExample : MonoBehaviour,
    IMixedRealitySourceStateHandler, // Handle source detected and lost
    IMixedRealityHandJointHandler // handle joint position updates for hands
{
    private void OnEnable()
    {
        // Instruct Input System that we would like to receive all input events of type
        // IMixedRealitySourceStateHandler and IMixedRealityHandJointHandler
        CoreServices.InputSystem?.RegisterHandler<IMixedRealitySourceStateHandler>(this);
        CoreServices.InputSystem?.RegisterHandler<IMixedRealityHandJointHandler>(this);
    }

    private void OnDisable()
    {
        // This component is being destroyed
        // Instruct the Input System to disregard us for input event handling
        CoreServices.InputSystem?.UnregisterHandler<IMixedRealitySourceStateHandler>(this);
        CoreServices.InputSystem?.UnregisterHandler<IMixedRealityHandJointHandler>(this);
    }

    // IMixedRealitySourceStateHandler interface
    public void OnSourceDetected(SourceStateEventData eventData)
    {
        var hand = eventData.Controller as IMixedRealityHand;

        // Only react to articulated hand input sources
        if (hand != null)
        {
            Debug.Log("Source detected: " + hand.ControllerHandedness);
        }
    }

    public void OnSourceLost(SourceStateEventData eventData)
    {
        var hand = eventData.Controller as IMixedRealityHand;

        // Only react to articulated hand input sources
        if (hand != null)
        {
            Debug.Log("Source lost: " + hand.ControllerHandedness);
        }
    }

    public void OnHandJointsUpdated(
                InputEventData<IDictionary<TrackedHandJoint, MixedRealityPose>> eventData)
    {
        MixedRealityPose palmPose;
        if (eventData.InputData.TryGetValue(TrackedHandJoint.Palm, out palmPose))
        {
            Debug.Log("Hand Joint Palm Updated: " + palmPose.Position);
        }
    }
}
```

## <a name="register-for-fallback-input-events"></a><span data-ttu-id="0b869-176">Registra per gli eventi di input di fallback</span><span class="sxs-lookup"><span data-stu-id="0b869-176">Register for fallback input events</span></span>

<span data-ttu-id="0b869-177">I gestori di input di fallback sono simili ai gestori di input globali registrati, ma vengono considerati come ultima risorsa per la gestione degli eventi di input.</span><span class="sxs-lookup"><span data-stu-id="0b869-177">Fallback input handlers are similar to registered global input handlers but are treated as a last resort for input event handling.</span></span> <span data-ttu-id="0b869-178">Solo se non sono stati trovati gestori di input globali e nessun GameObject è attivo, verranno utilizzati i gestori di input di fallback.</span><span class="sxs-lookup"><span data-stu-id="0b869-178">Only if no global input handlers were found and no GameObjects are in focus will fallback input handlers be leveraged.</span></span>

### <a name="fallback-input-handler-example"></a><span data-ttu-id="0b869-179">Esempio di gestore di input di fallback</span><span class="sxs-lookup"><span data-stu-id="0b869-179">Fallback input handler example</span></span>

```c#
public class GlobalHandListenerExample : MonoBehaviour,
    IMixedRealitySourceStateHandler // Handle source detected and lost
{
    private void OnEnable()
    {
        CoreServices.InputSystem?.PushFallbackInputHandler(this);
    }

    private void OnDisable()
    {
        CoreServices.InputSystem?.PopFallbackInputHandler();
    }

    // IMixedRealitySourceStateHandler interface
    public void OnSourceDetected(SourceStateEventData eventData)
    {
        ...
    }

    public void OnSourceLost(SourceStateEventData eventData)
    {
        ...
    }
}
```

## <a name="how-to-stop-input-events"></a><span data-ttu-id="0b869-180">Come arrestare gli eventi di input</span><span class="sxs-lookup"><span data-stu-id="0b869-180">How to stop input events</span></span>

<span data-ttu-id="0b869-181">Ogni interfaccia dell'evento di input fornisce un [`BaseInputEventData`](xref:Microsoft.MixedReality.Toolkit.Input.BaseInputEventData) oggetto dati come parametro per ogni funzione nell'interfaccia.</span><span class="sxs-lookup"><span data-stu-id="0b869-181">Every input event interface provides a [`BaseInputEventData`](xref:Microsoft.MixedReality.Toolkit.Input.BaseInputEventData) data object as a parameter to each function on the interface.</span></span> <span data-ttu-id="0b869-182">Questo oggetto dati di evento si estende dall'oggetto di Unity [`AbstractEventData`](https://docs.unity3d.com/2019.1/Documentation/ScriptReference/EventSystems.AbstractEventData.html) .</span><span class="sxs-lookup"><span data-stu-id="0b869-182">This event data object extends from Unity's own [`AbstractEventData`](https://docs.unity3d.com/2019.1/Documentation/ScriptReference/EventSystems.AbstractEventData.html).</span></span>

<span data-ttu-id="0b869-183">Per arrestare la propagazione di un evento di input attraverso l'esecuzione [come indicato](#input-events-in-action), un componente può chiamare [`AbstractEventData.Use()`](https://docs.unity3d.com/2019.1/Documentation/ScriptReference/EventSystems.AbstractEventData.Use.html) per contrassegnare l'evento come usato.</span><span class="sxs-lookup"><span data-stu-id="0b869-183">In order to stop an input event from propagating through its execution [as outlined](#input-events-in-action), a component can call [`AbstractEventData.Use()`](https://docs.unity3d.com/2019.1/Documentation/ScriptReference/EventSystems.AbstractEventData.Use.html) to mark the event as used.</span></span> <span data-ttu-id="0b869-184">Questo impedirà a qualsiasi altro GameObject di ricevere l'evento di input corrente, ad eccezione dei gestori di input globali.</span><span class="sxs-lookup"><span data-stu-id="0b869-184">This will stop any other GameObjects from receiving the current input event, with the exception of global input handlers.</span></span>

> [!NOTE]
> <span data-ttu-id="0b869-185">Un componente che chiama il `Use()` Metodo arresterà la ricezione da parte di altri GameObject.</span><span class="sxs-lookup"><span data-stu-id="0b869-185">A component that calls the `Use()` method will stop other GameObjects from receiving it.</span></span> <span data-ttu-id="0b869-186">Tuttavia, altri componenti sul GameObject corrente riceveranno comunque l'evento di input e attiveranno le funzioni di interfaccia correlate.</span><span class="sxs-lookup"><span data-stu-id="0b869-186">However, other components on the current GameObject will still receive the input event and fire any related interface functions.</span></span>

## <a name="see-also"></a><span data-ttu-id="0b869-187">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="0b869-187">See also</span></span>

- [<span data-ttu-id="0b869-188">Puntatori</span><span class="sxs-lookup"><span data-stu-id="0b869-188">Pointers</span></span>](Pointers.md)
- [<span data-ttu-id="0b869-189">Voce</span><span class="sxs-lookup"><span data-stu-id="0b869-189">Speech</span></span>](Speech.md)
- [<span data-ttu-id="0b869-190">Stato input</span><span class="sxs-lookup"><span data-stu-id="0b869-190">Input State</span></span>](InputState.md)

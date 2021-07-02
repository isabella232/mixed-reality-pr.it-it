---
title: Eventi di input
description: Documentazione per InputEvents in MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, eventi,
ms.openlocfilehash: c8871aa575e2aa4507e9dbbdcc8bdf0fc0604633
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176778"
---
# <a name="input-events"></a><span data-ttu-id="3f1c1-104">Eventi di input</span><span class="sxs-lookup"><span data-stu-id="3f1c1-104">Input events</span></span>

<span data-ttu-id="3f1c1-105">L'elenco seguente descrive tutte le interfacce di eventi di input disponibili che devono essere implementate da un componente MonoBehaviour personalizzato.</span><span class="sxs-lookup"><span data-stu-id="3f1c1-105">The list below outlines all available input event interfaces to be implemented by a custom MonoBehaviour component.</span></span> <span data-ttu-id="3f1c1-106">Queste interfacce verranno chiamate dal sistema di input MRTK per gestire la logica dell'app personalizzata in base alle interazioni di input dell'utente.</span><span class="sxs-lookup"><span data-stu-id="3f1c1-106">These interfaces will be called by the MRTK input system to handle custom app logic based on user input interactions.</span></span> <span data-ttu-id="3f1c1-107">[Gli eventi di input](pointers.md#pointer-event-interfaces) del puntatore vengono gestiti in modo leggermente diverso rispetto ai tipi di evento di input standard riportati di seguito.</span><span class="sxs-lookup"><span data-stu-id="3f1c1-107">[Pointer input events](pointers.md#pointer-event-interfaces) are handled slightly differently than the standard input event types below.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="3f1c1-108">Per impostazione predefinita, uno script riceverà gli eventi di input solo se è il GameObject nello stato attivo da un puntatore o da un elemento padre di un GameObject nello stato attivo.</span><span class="sxs-lookup"><span data-stu-id="3f1c1-108">By default, a script will receive input events only if it is the GameObject in focus by a pointer or parent of a GameObject in focus.</span></span>

| <span data-ttu-id="3f1c1-109">Gestore</span><span class="sxs-lookup"><span data-stu-id="3f1c1-109">Handler</span></span> | <span data-ttu-id="3f1c1-110">Eventi</span><span class="sxs-lookup"><span data-stu-id="3f1c1-110">Events</span></span> | <span data-ttu-id="3f1c1-111">Descrizione</span><span class="sxs-lookup"><span data-stu-id="3f1c1-111">Description</span></span> |
| --- | :---: | --- |
| [`IMixedRealitySourceStateHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySourceStateHandler) | <span data-ttu-id="3f1c1-112">Origine rilevata/persa</span><span class="sxs-lookup"><span data-stu-id="3f1c1-112">Source Detected / Lost</span></span> | <span data-ttu-id="3f1c1-113">Generato quando viene rilevata o persa un'origine di input, ad esempio quando viene rilevata o smarrita una mano articolata.</span><span class="sxs-lookup"><span data-stu-id="3f1c1-113">Raised when an input source is detected/lost, like when an articulated hand is detected or lost track of.</span></span> |
| [`IMixedRealitySourcePoseHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySourcePoseHandler) | <span data-ttu-id="3f1c1-114">Modifica della posizione di origine</span><span class="sxs-lookup"><span data-stu-id="3f1c1-114">Source Pose Changed</span></span> | <span data-ttu-id="3f1c1-115">Generato in base alle modifiche della posizione di origine.</span><span class="sxs-lookup"><span data-stu-id="3f1c1-115">Raised on source pose changes.</span></span> <span data-ttu-id="3f1c1-116">La posizione di origine rappresenta la posizione generale dell'origine di input.</span><span class="sxs-lookup"><span data-stu-id="3f1c1-116">The source pose represents the general pose of the input source.</span></span> <span data-ttu-id="3f1c1-117">È possibile ottenere posizioni specifiche, ad esempio la manopola o la posizione dell'indicatore di misura in un controller DOF a sei, tramite `IMixedRealityInputHandler<MixedRealityPose>` .</span><span class="sxs-lookup"><span data-stu-id="3f1c1-117">Specific poses, like the grip or pointer pose in a six DOF controller, can be obtained via `IMixedRealityInputHandler<MixedRealityPose>`.</span></span> |
| [`IMixedRealityInputHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler) | <span data-ttu-id="3f1c1-118">Input verso il basso o verso l'alto</span><span class="sxs-lookup"><span data-stu-id="3f1c1-118">Input Down / Up</span></span> | <span data-ttu-id="3f1c1-119">Generato in base alle modifiche apportate agli input binari come i pulsanti.</span><span class="sxs-lookup"><span data-stu-id="3f1c1-119">Raised on changes to binary inputs like buttons.</span></span> |
| [`IMixedRealityInputHandler<T>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler`1) | <span data-ttu-id="3f1c1-120">Input modificato</span><span class="sxs-lookup"><span data-stu-id="3f1c1-120">Input Changed</span></span> | <span data-ttu-id="3f1c1-121">Generato in base alle modifiche apportate agli input del tipo specificato.</span><span class="sxs-lookup"><span data-stu-id="3f1c1-121">Raised on changes to inputs of the given type.</span></span> <span data-ttu-id="3f1c1-122">**T** può assumere i valori seguenti:</span><span class="sxs-lookup"><span data-stu-id="3f1c1-122">**T** can take the following values:</span></span> <br/> <span data-ttu-id="3f1c1-123">- *float* (ad esempio restituisce un trigger analogo)</span><span class="sxs-lookup"><span data-stu-id="3f1c1-123">- *float* (e.g returns analog trigger)</span></span><br/> <span data-ttu-id="3f1c1-124">- *Vector2* (ad esempio restituisce la direzione del levetta del game pad)</span><span class="sxs-lookup"><span data-stu-id="3f1c1-124">- *Vector2* (e.g returns gamepad thumbstick direction)</span></span> <br/> <span data-ttu-id="3f1c1-125">- *Vector3* (ad esempio la posizione restituita del dispositivo tracciato)</span><span class="sxs-lookup"><span data-stu-id="3f1c1-125">- *Vector3* (e.g return position of tracked device)</span></span> <br/> <span data-ttu-id="3f1c1-126">- *Quaternione* (ad esempio restituisce l'orientamento del dispositivo tracciato)</span><span class="sxs-lookup"><span data-stu-id="3f1c1-126">- *Quaternion* (e.g returns orientation of tracked device)</span></span><br/> <span data-ttu-id="3f1c1-127">- [MixedRealityPose](xref:Microsoft.MixedReality.Toolkit.Utilities.MixedRealityPose) (ad esempio restituisce un dispositivo completamente monitorato)</span><span class="sxs-lookup"><span data-stu-id="3f1c1-127">- [MixedRealityPose](xref:Microsoft.MixedReality.Toolkit.Utilities.MixedRealityPose) (e.g. returns fully tracked device)</span></span> |
| [`IMixedRealitySpeechHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySpeechHandler) | <span data-ttu-id="3f1c1-128">Riconoscimento della parola chiave di Riconoscimento vocale</span><span class="sxs-lookup"><span data-stu-id="3f1c1-128">Speech Keyword Recognized</span></span> | <span data-ttu-id="3f1c1-129">Generato al riconoscimento di una delle parole chiave configurate nel profilo *dei comandi vocali.*</span><span class="sxs-lookup"><span data-stu-id="3f1c1-129">Raised on recognition of one of the keywords configured in the *Speech Commands Profile*.</span></span> |
| [`IMixedRealityDictationHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityDictationHandler) | <span data-ttu-id="3f1c1-130">Dettatura</span><span class="sxs-lookup"><span data-stu-id="3f1c1-130">Dictation</span></span><br/> <span data-ttu-id="3f1c1-131">Hypothesis</span><span class="sxs-lookup"><span data-stu-id="3f1c1-131">Hypothesis</span></span> <br/> <span data-ttu-id="3f1c1-132">Result</span><span class="sxs-lookup"><span data-stu-id="3f1c1-132">Result</span></span> <br/> <span data-ttu-id="3f1c1-133">Operazione completata</span><span class="sxs-lookup"><span data-stu-id="3f1c1-133">Complete</span></span> <br/> <span data-ttu-id="3f1c1-134">Errore</span><span class="sxs-lookup"><span data-stu-id="3f1c1-134">Error</span></span> | <span data-ttu-id="3f1c1-135">Generato dai sistemi di dettatura per segnalare i risultati di una sessione di dettatura.</span><span class="sxs-lookup"><span data-stu-id="3f1c1-135">Raised by dictation systems to report the results of a dictation session.</span></span> |
| [`IMixedRealityGestureHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGestureHandler) | <span data-ttu-id="3f1c1-136">Eventi di movimento in:</span><span class="sxs-lookup"><span data-stu-id="3f1c1-136">Gesture events on:</span></span> <br/> <span data-ttu-id="3f1c1-137">Avviato</span><span class="sxs-lookup"><span data-stu-id="3f1c1-137">Started</span></span> <br/> <span data-ttu-id="3f1c1-138">Aggiornato</span><span class="sxs-lookup"><span data-stu-id="3f1c1-138">Updated</span></span> <br/> <span data-ttu-id="3f1c1-139">Completato</span><span class="sxs-lookup"><span data-stu-id="3f1c1-139">Completed</span></span> <br/> <span data-ttu-id="3f1c1-140">Cancellati</span><span class="sxs-lookup"><span data-stu-id="3f1c1-140">Canceled</span></span> | <span data-ttu-id="3f1c1-141">Generato al rilevamento dei movimenti.</span><span class="sxs-lookup"><span data-stu-id="3f1c1-141">Raised on gesture detection.</span></span> |
| [`IMixedRealityGestureHandler<T>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGestureHandler`1) | <span data-ttu-id="3f1c1-142">Movimento aggiornato/completato</span><span class="sxs-lookup"><span data-stu-id="3f1c1-142">Gesture Updated / Completed</span></span> | <span data-ttu-id="3f1c1-143">Generato al rilevamento di movimenti contenenti dati aggiuntivi del tipo specificato.</span><span class="sxs-lookup"><span data-stu-id="3f1c1-143">Raised on detection of gestures containing additional data of the given type.</span></span> <span data-ttu-id="3f1c1-144">Vedere [**eventi di movimento**](gestures.md#gesture-events) per informazioni dettagliate sui valori possibili per **T**.</span><span class="sxs-lookup"><span data-stu-id="3f1c1-144">See [**gesture events**](gestures.md#gesture-events) for details on possible values for **T**.</span></span> |
| [`IMixedRealityHandJointHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHandJointHandler) | <span data-ttu-id="3f1c1-145">Hand Joints Updated</span><span class="sxs-lookup"><span data-stu-id="3f1c1-145">Hand Joints Updated</span></span> | <span data-ttu-id="3f1c1-146">Generato da controller della mano articolati quando vengono aggiornati i giunzioni delle mani.</span><span class="sxs-lookup"><span data-stu-id="3f1c1-146">Raised by articulated hand controllers when hand joints are updated.</span></span> |
| [`IMixedRealityHandMeshHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHandMeshHandler) | <span data-ttu-id="3f1c1-147">Hand Mesh Updated</span><span class="sxs-lookup"><span data-stu-id="3f1c1-147">Hand Mesh Updated</span></span> | <span data-ttu-id="3f1c1-148">Generato da controller della mano articolati quando viene aggiornata una mesh manuale.</span><span class="sxs-lookup"><span data-stu-id="3f1c1-148">Raised by articulated hand controllers when a hand mesh is updated.</span></span> |
| [`IMixedRealityInputActionHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputActionHandler) | <span data-ttu-id="3f1c1-149">Azione avviata/terminata</span><span class="sxs-lookup"><span data-stu-id="3f1c1-149">Action Started / Ended</span></span> | <span data-ttu-id="3f1c1-150">Genera per indicare l'inizio e la fine dell'azione per gli input di cui è stato eseguito il mapping alle azioni.</span><span class="sxs-lookup"><span data-stu-id="3f1c1-150">Raise to indicate action start and end for inputs mapped to actions.</span></span> |

## <a name="input-events-in-action"></a><span data-ttu-id="3f1c1-151">Eventi di input in azione</span><span class="sxs-lookup"><span data-stu-id="3f1c1-151">Input events in action</span></span>

<span data-ttu-id="3f1c1-152">A livello di script, gli eventi di input possono essere utilizzati implementando una delle interfacce del gestore eventi illustrate nella tabella precedente.</span><span class="sxs-lookup"><span data-stu-id="3f1c1-152">At the script level, input events can be consumed by implementing one of the event handler interfaces shown in the table above.</span></span> <span data-ttu-id="3f1c1-153">Quando un evento di input viene generato tramite un'interazione dell'utente, si verifica quanto segue:</span><span class="sxs-lookup"><span data-stu-id="3f1c1-153">When an input event fires via a user interaction, the following takes place:</span></span>

1. <span data-ttu-id="3f1c1-154">Il sistema di input MRTK riconosce che si è verificato un evento di input.</span><span class="sxs-lookup"><span data-stu-id="3f1c1-154">The MRTK input system recognizes that an input event has occurred.</span></span>
1. <span data-ttu-id="3f1c1-155">Il sistema di input MRTK genera la funzione di interfaccia pertinente dell'evento di input per tutti [i gestori di input globali registrati](#register-for-global-input-events)</span><span class="sxs-lookup"><span data-stu-id="3f1c1-155">The MRTK input system fires the relevant interface function of the input event to all [registered global input handlers](#register-for-global-input-events)</span></span>
1. <span data-ttu-id="3f1c1-156">Per ogni puntatore attivo registrato con il sistema di input:</span><span class="sxs-lookup"><span data-stu-id="3f1c1-156">For every active pointer registered with the input system:</span></span>
    1. <span data-ttu-id="3f1c1-157">Il sistema di input determina quale GameObject è attivo per il puntatore corrente.</span><span class="sxs-lookup"><span data-stu-id="3f1c1-157">The input system determines which GameObject is in focus for the current pointer.</span></span>
    1. <span data-ttu-id="3f1c1-158">Il sistema di input usa il sistema di eventi [di Unity per](https://docs.unity3d.com/Manual/EventSystem.html) impostare la funzione di interfaccia pertinente per tutti i componenti corrispondenti nel GameObject con lo stato attivo.</span><span class="sxs-lookup"><span data-stu-id="3f1c1-158">The input system utilizes [Unity's event system](https://docs.unity3d.com/Manual/EventSystem.html) to fire the relevant interface function for all matching components on the focused GameObject.</span></span>
    1. <span data-ttu-id="3f1c1-159">Se in qualsiasi momento un evento di input è stato contrassegnato come [usato,](#how-to-stop-input-events)il processo terminerà e nessun altro GameObject riceverà callback.</span><span class="sxs-lookup"><span data-stu-id="3f1c1-159">If at any point an input event has been [marked as used](#how-to-stop-input-events), the process will end and no further GameObjects will receive callbacks.</span></span>
        - <span data-ttu-id="3f1c1-160">Esempio: i componenti che implementano [`IMixedRealitySpeechHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySpeechHandler) l'interfaccia verranno cercati quando viene riconosciuto un comando vocale.</span><span class="sxs-lookup"><span data-stu-id="3f1c1-160">Example: Components implementing the interface [`IMixedRealitySpeechHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySpeechHandler) will be searched for when a speech command is recognized.</span></span>
        - <span data-ttu-id="3f1c1-161">Nota: il sistema di eventi Unity verrà visualizzato per cercare il GameObject padre se non vengono trovati componenti corrispondenti all'interfaccia desiderata nell'oggetto GameObject corrente.</span><span class="sxs-lookup"><span data-stu-id="3f1c1-161">Note: The Unity event system will bubble up to search the parent GameObject if no components matching the desired interface are found on the current GameObject.</span></span>
1. <span data-ttu-id="3f1c1-162">Se non è registrato alcun gestore di input globale e non viene trovato alcun GameObject con un componente/interfaccia corrispondente, il sistema di input chiamerà ogni gestore di input registrato di fallback</span><span class="sxs-lookup"><span data-stu-id="3f1c1-162">If no global input handlers are registered and no GameObject is found with a matching component/interface, then the input system will call each fallback registered input handler</span></span>

> [!NOTE]
> <span data-ttu-id="3f1c1-163">[Gli eventi di input](pointers.md#pointer-event-interfaces) del puntatore vengono gestiti in modo leggermente diverso rispetto alle interfacce degli eventi di input elencate in precedenza.</span><span class="sxs-lookup"><span data-stu-id="3f1c1-163">[Pointer input events](pointers.md#pointer-event-interfaces) are handled in a slightly different manner than the input event interfaces listed above.</span></span> <span data-ttu-id="3f1c1-164">In particolare, gli eventi di input del puntatore vengono gestiti solo dal GameObject nello stato attivo dal puntatore che ha attivato l'evento di input, nonché da qualsiasi gestore di input globale.</span><span class="sxs-lookup"><span data-stu-id="3f1c1-164">In particular, pointer input events are handled only by the GameObject in focus by the pointer that fired the input event - as well as any global input handlers.</span></span> <span data-ttu-id="3f1c1-165">Gli eventi di input regolari vengono gestiti da GameObject nello stato attivo per tutti i puntatori attivi.</span><span class="sxs-lookup"><span data-stu-id="3f1c1-165">Regular input events are handled by GameObjects in focus for all active pointers.</span></span>

### <a name="input-event-interface-example"></a><span data-ttu-id="3f1c1-166">Esempio di interfaccia eventi di input</span><span class="sxs-lookup"><span data-stu-id="3f1c1-166">Input event interface example</span></span>

<span data-ttu-id="3f1c1-167">Il codice seguente illustra l'uso [`IMixedRealitySpeechHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySpeechHandler) dell'interfaccia .</span><span class="sxs-lookup"><span data-stu-id="3f1c1-167">The code below demonstrates use of the [`IMixedRealitySpeechHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySpeechHandler) interface.</span></span> <span data-ttu-id="3f1c1-168">Quando l'utente dice le parole "più piccole" o "più grandi" concentrandosi su un GameObject con questa classe, il GameObject si ridimensiona dime o `ShowHideSpeechHandler` due volte.</span><span class="sxs-lookup"><span data-stu-id="3f1c1-168">When the user says the words "smaller" or "bigger" while focusing on a GameObject with this `ShowHideSpeechHandler` class, the GameObject will scale itself by half or twice as much.</span></span>

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
> <span data-ttu-id="3f1c1-169">[`IMixedRealitySpeechHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySpeechHandler)Gli eventi di input richiedono che le parole chiave desiderate siano pre-registrate in [MRTK Speech Commands Profile.](speech.md)</span><span class="sxs-lookup"><span data-stu-id="3f1c1-169">[`IMixedRealitySpeechHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySpeechHandler) input events require that the desired keywords are pre-registered in the [MRTK Speech Commands Profile](speech.md).</span></span>

## <a name="register-for-global-input-events"></a><span data-ttu-id="3f1c1-170">Registrarsi per eventi di input globali</span><span class="sxs-lookup"><span data-stu-id="3f1c1-170">Register for global input events</span></span>

<span data-ttu-id="3f1c1-171">Per creare un componente che rimane in ascolto di eventi di input globali, ignorando il GameObject che potrebbe essere attivo, un componente deve registrarsi con il sistema di input.</span><span class="sxs-lookup"><span data-stu-id="3f1c1-171">To create a component that listens for global input events, disregarding what GameObject may be in focus, a component must register itself with the Input System.</span></span> <span data-ttu-id="3f1c1-172">Dopo la registrazione, tutte le istanze di questo MonoBehaviour riceveranno gli eventi di input insieme a tutti i GameObject attualmente in stato attivo e ad altri listener registrati a livello globale.</span><span class="sxs-lookup"><span data-stu-id="3f1c1-172">Once registered, any instances of this MonoBehaviour will receive input events along with any GameObject(s) currently in focus and other global registered listeners.</span></span>

<span data-ttu-id="3f1c1-173">Se un evento di input è stato [contrassegnato come usato,](#how-to-stop-input-events)i gestori registrati globali riceveranno comunque tutti i callback.</span><span class="sxs-lookup"><span data-stu-id="3f1c1-173">If an input event has been [marked as used](#how-to-stop-input-events), global registered handlers will still all receive callbacks.</span></span> <span data-ttu-id="3f1c1-174">Tuttavia, nessun GameObject con stato attivo riceverà l'evento.</span><span class="sxs-lookup"><span data-stu-id="3f1c1-174">However, no focused GameObjects will receive the event.</span></span>

### <a name="global-input-registration-example"></a><span data-ttu-id="3f1c1-175">Esempio di registrazione dell'input globale</span><span class="sxs-lookup"><span data-stu-id="3f1c1-175">Global input registration example</span></span>

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

## <a name="register-for-fallback-input-events"></a><span data-ttu-id="3f1c1-176">Registrarsi per gli eventi di input di fallback</span><span class="sxs-lookup"><span data-stu-id="3f1c1-176">Register for fallback input events</span></span>

<span data-ttu-id="3f1c1-177">I gestori di input di fallback sono simili ai gestori di input globali registrati, ma vengono considerati come ultima risorsa per la gestione degli eventi di input.</span><span class="sxs-lookup"><span data-stu-id="3f1c1-177">Fallback input handlers are similar to registered global input handlers but are treated as a last resort for input event handling.</span></span> <span data-ttu-id="3f1c1-178">Solo se non sono stati trovati gestori di input globali e non sono presenti GameObject nello stato attivo, verranno sfruttati i gestori di input di fallback.</span><span class="sxs-lookup"><span data-stu-id="3f1c1-178">Only if no global input handlers were found and no GameObjects are in focus will fallback input handlers be leveraged.</span></span>

### <a name="fallback-input-handler-example"></a><span data-ttu-id="3f1c1-179">Esempio di gestore di input di fallback</span><span class="sxs-lookup"><span data-stu-id="3f1c1-179">Fallback input handler example</span></span>

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

## <a name="how-to-stop-input-events"></a><span data-ttu-id="3f1c1-180">Come arrestare gli eventi di input</span><span class="sxs-lookup"><span data-stu-id="3f1c1-180">How to stop input events</span></span>

<span data-ttu-id="3f1c1-181">Ogni interfaccia dell'evento di input [`BaseInputEventData`](xref:Microsoft.MixedReality.Toolkit.Input.BaseInputEventData) fornisce un oggetto dati come parametro a ogni funzione nell'interfaccia.</span><span class="sxs-lookup"><span data-stu-id="3f1c1-181">Every input event interface provides a [`BaseInputEventData`](xref:Microsoft.MixedReality.Toolkit.Input.BaseInputEventData) data object as a parameter to each function on the interface.</span></span> <span data-ttu-id="3f1c1-182">Questo oggetto dati dell'evento si estende dall'oggetto di [`AbstractEventData`](https://docs.unity3d.com/2019.1/Documentation/ScriptReference/EventSystems.AbstractEventData.html) Unity.</span><span class="sxs-lookup"><span data-stu-id="3f1c1-182">This event data object extends from Unity's own [`AbstractEventData`](https://docs.unity3d.com/2019.1/Documentation/ScriptReference/EventSystems.AbstractEventData.html).</span></span>

<span data-ttu-id="3f1c1-183">Per arrestare la propagazione di un evento di input tramite la relativa esecuzione, come descritto [in](#input-events-in-action), un componente può chiamare per [`AbstractEventData.Use()`](https://docs.unity3d.com/2019.1/Documentation/ScriptReference/EventSystems.AbstractEventData.Use.html) contrassegnare l'evento come usato.</span><span class="sxs-lookup"><span data-stu-id="3f1c1-183">In order to stop an input event from propagating through its execution [as outlined](#input-events-in-action), a component can call [`AbstractEventData.Use()`](https://docs.unity3d.com/2019.1/Documentation/ScriptReference/EventSystems.AbstractEventData.Use.html) to mark the event as used.</span></span> <span data-ttu-id="3f1c1-184">In questo modo qualsiasi altro GameObject non riceverà l'evento di input corrente, ad eccezione dei gestori di input globali.</span><span class="sxs-lookup"><span data-stu-id="3f1c1-184">This will stop any other GameObjects from receiving the current input event, with the exception of global input handlers.</span></span>

> [!NOTE]
> <span data-ttu-id="3f1c1-185">Un componente che chiama il `Use()` metodo impedirà ad altri GameObject di riceverlo.</span><span class="sxs-lookup"><span data-stu-id="3f1c1-185">A component that calls the `Use()` method will stop other GameObjects from receiving it.</span></span> <span data-ttu-id="3f1c1-186">Tuttavia, gli altri componenti nell'oggetto GameObject corrente riceveranno comunque l'evento di input e generano le funzioni di interfaccia correlate.</span><span class="sxs-lookup"><span data-stu-id="3f1c1-186">However, other components on the current GameObject will still receive the input event and fire any related interface functions.</span></span>

## <a name="see-also"></a><span data-ttu-id="3f1c1-187">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="3f1c1-187">See also</span></span>

- [<span data-ttu-id="3f1c1-188">Puntatori</span><span class="sxs-lookup"><span data-stu-id="3f1c1-188">Pointers</span></span>](pointers.md)
- [<span data-ttu-id="3f1c1-189">Voce</span><span class="sxs-lookup"><span data-stu-id="3f1c1-189">Speech</span></span>](speech.md)
- [<span data-ttu-id="3f1c1-190">Stato di input</span><span class="sxs-lookup"><span data-stu-id="3f1c1-190">Input State</span></span>](input-state.md)

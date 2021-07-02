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
# <a name="input-events"></a>Eventi di input

L'elenco seguente descrive tutte le interfacce di eventi di input disponibili che devono essere implementate da un componente MonoBehaviour personalizzato. Queste interfacce verranno chiamate dal sistema di input MRTK per gestire la logica dell'app personalizzata in base alle interazioni di input dell'utente. [Gli eventi di input](pointers.md#pointer-event-interfaces) del puntatore vengono gestiti in modo leggermente diverso rispetto ai tipi di evento di input standard riportati di seguito.

> [!IMPORTANT]
> Per impostazione predefinita, uno script riceverà gli eventi di input solo se è il GameObject nello stato attivo da un puntatore o da un elemento padre di un GameObject nello stato attivo.

| Gestore | Eventi | Descrizione |
| --- | :---: | --- |
| [`IMixedRealitySourceStateHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySourceStateHandler) | Origine rilevata/persa | Generato quando viene rilevata o persa un'origine di input, ad esempio quando viene rilevata o smarrita una mano articolata. |
| [`IMixedRealitySourcePoseHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySourcePoseHandler) | Modifica della posizione di origine | Generato in base alle modifiche della posizione di origine. La posizione di origine rappresenta la posizione generale dell'origine di input. È possibile ottenere posizioni specifiche, ad esempio la manopola o la posizione dell'indicatore di misura in un controller DOF a sei, tramite `IMixedRealityInputHandler<MixedRealityPose>` . |
| [`IMixedRealityInputHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler) | Input verso il basso o verso l'alto | Generato in base alle modifiche apportate agli input binari come i pulsanti. |
| [`IMixedRealityInputHandler<T>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler`1) | Input modificato | Generato in base alle modifiche apportate agli input del tipo specificato. **T** può assumere i valori seguenti: <br/> - *float* (ad esempio restituisce un trigger analogo)<br/> - *Vector2* (ad esempio restituisce la direzione del levetta del game pad) <br/> - *Vector3* (ad esempio la posizione restituita del dispositivo tracciato) <br/> - *Quaternione* (ad esempio restituisce l'orientamento del dispositivo tracciato)<br/> - [MixedRealityPose](xref:Microsoft.MixedReality.Toolkit.Utilities.MixedRealityPose) (ad esempio restituisce un dispositivo completamente monitorato) |
| [`IMixedRealitySpeechHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySpeechHandler) | Riconoscimento della parola chiave di Riconoscimento vocale | Generato al riconoscimento di una delle parole chiave configurate nel profilo *dei comandi vocali.* |
| [`IMixedRealityDictationHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityDictationHandler) | Dettatura<br/> Hypothesis <br/> Result <br/> Operazione completata <br/> Errore | Generato dai sistemi di dettatura per segnalare i risultati di una sessione di dettatura. |
| [`IMixedRealityGestureHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGestureHandler) | Eventi di movimento in: <br/> Avviato <br/> Aggiornato <br/> Completato <br/> Cancellati | Generato al rilevamento dei movimenti. |
| [`IMixedRealityGestureHandler<T>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGestureHandler`1) | Movimento aggiornato/completato | Generato al rilevamento di movimenti contenenti dati aggiuntivi del tipo specificato. Vedere [**eventi di movimento**](gestures.md#gesture-events) per informazioni dettagliate sui valori possibili per **T**. |
| [`IMixedRealityHandJointHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHandJointHandler) | Hand Joints Updated | Generato da controller della mano articolati quando vengono aggiornati i giunzioni delle mani. |
| [`IMixedRealityHandMeshHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHandMeshHandler) | Hand Mesh Updated | Generato da controller della mano articolati quando viene aggiornata una mesh manuale. |
| [`IMixedRealityInputActionHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputActionHandler) | Azione avviata/terminata | Genera per indicare l'inizio e la fine dell'azione per gli input di cui è stato eseguito il mapping alle azioni. |

## <a name="input-events-in-action"></a>Eventi di input in azione

A livello di script, gli eventi di input possono essere utilizzati implementando una delle interfacce del gestore eventi illustrate nella tabella precedente. Quando un evento di input viene generato tramite un'interazione dell'utente, si verifica quanto segue:

1. Il sistema di input MRTK riconosce che si è verificato un evento di input.
1. Il sistema di input MRTK genera la funzione di interfaccia pertinente dell'evento di input per tutti [i gestori di input globali registrati](#register-for-global-input-events)
1. Per ogni puntatore attivo registrato con il sistema di input:
    1. Il sistema di input determina quale GameObject è attivo per il puntatore corrente.
    1. Il sistema di input usa il sistema di eventi [di Unity per](https://docs.unity3d.com/Manual/EventSystem.html) impostare la funzione di interfaccia pertinente per tutti i componenti corrispondenti nel GameObject con lo stato attivo.
    1. Se in qualsiasi momento un evento di input è stato contrassegnato come [usato,](#how-to-stop-input-events)il processo terminerà e nessun altro GameObject riceverà callback.
        - Esempio: i componenti che implementano [`IMixedRealitySpeechHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySpeechHandler) l'interfaccia verranno cercati quando viene riconosciuto un comando vocale.
        - Nota: il sistema di eventi Unity verrà visualizzato per cercare il GameObject padre se non vengono trovati componenti corrispondenti all'interfaccia desiderata nell'oggetto GameObject corrente.
1. Se non è registrato alcun gestore di input globale e non viene trovato alcun GameObject con un componente/interfaccia corrispondente, il sistema di input chiamerà ogni gestore di input registrato di fallback

> [!NOTE]
> [Gli eventi di input](pointers.md#pointer-event-interfaces) del puntatore vengono gestiti in modo leggermente diverso rispetto alle interfacce degli eventi di input elencate in precedenza. In particolare, gli eventi di input del puntatore vengono gestiti solo dal GameObject nello stato attivo dal puntatore che ha attivato l'evento di input, nonché da qualsiasi gestore di input globale. Gli eventi di input regolari vengono gestiti da GameObject nello stato attivo per tutti i puntatori attivi.

### <a name="input-event-interface-example"></a>Esempio di interfaccia eventi di input

Il codice seguente illustra l'uso [`IMixedRealitySpeechHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySpeechHandler) dell'interfaccia . Quando l'utente dice le parole "più piccole" o "più grandi" concentrandosi su un GameObject con questa classe, il GameObject si ridimensiona dime o `ShowHideSpeechHandler` due volte.

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
> [`IMixedRealitySpeechHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySpeechHandler)Gli eventi di input richiedono che le parole chiave desiderate siano pre-registrate in [MRTK Speech Commands Profile.](speech.md)

## <a name="register-for-global-input-events"></a>Registrarsi per eventi di input globali

Per creare un componente che rimane in ascolto di eventi di input globali, ignorando il GameObject che potrebbe essere attivo, un componente deve registrarsi con il sistema di input. Dopo la registrazione, tutte le istanze di questo MonoBehaviour riceveranno gli eventi di input insieme a tutti i GameObject attualmente in stato attivo e ad altri listener registrati a livello globale.

Se un evento di input è stato [contrassegnato come usato,](#how-to-stop-input-events)i gestori registrati globali riceveranno comunque tutti i callback. Tuttavia, nessun GameObject con stato attivo riceverà l'evento.

### <a name="global-input-registration-example"></a>Esempio di registrazione dell'input globale

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

## <a name="register-for-fallback-input-events"></a>Registrarsi per gli eventi di input di fallback

I gestori di input di fallback sono simili ai gestori di input globali registrati, ma vengono considerati come ultima risorsa per la gestione degli eventi di input. Solo se non sono stati trovati gestori di input globali e non sono presenti GameObject nello stato attivo, verranno sfruttati i gestori di input di fallback.

### <a name="fallback-input-handler-example"></a>Esempio di gestore di input di fallback

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

## <a name="how-to-stop-input-events"></a>Come arrestare gli eventi di input

Ogni interfaccia dell'evento di input [`BaseInputEventData`](xref:Microsoft.MixedReality.Toolkit.Input.BaseInputEventData) fornisce un oggetto dati come parametro a ogni funzione nell'interfaccia. Questo oggetto dati dell'evento si estende dall'oggetto di [`AbstractEventData`](https://docs.unity3d.com/2019.1/Documentation/ScriptReference/EventSystems.AbstractEventData.html) Unity.

Per arrestare la propagazione di un evento di input tramite la relativa esecuzione, come descritto [in](#input-events-in-action), un componente può chiamare per [`AbstractEventData.Use()`](https://docs.unity3d.com/2019.1/Documentation/ScriptReference/EventSystems.AbstractEventData.Use.html) contrassegnare l'evento come usato. In questo modo qualsiasi altro GameObject non riceverà l'evento di input corrente, ad eccezione dei gestori di input globali.

> [!NOTE]
> Un componente che chiama il `Use()` metodo impedirà ad altri GameObject di riceverlo. Tuttavia, gli altri componenti nell'oggetto GameObject corrente riceveranno comunque l'evento di input e generano le funzioni di interfaccia correlate.

## <a name="see-also"></a>Vedere anche

- [Puntatori](pointers.md)
- [Voce](speech.md)
- [Stato di input](input-state.md)

---
title: InputEvents
description: Documentazione per InputEvents in MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, eventi,
ms.openlocfilehash: 2fa16d44a7658b7f55c8352b67bcd074b937f9cf
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/03/2021
ms.locfileid: "101781611"
---
# <a name="input-events"></a>Eventi di input

L'elenco seguente descrive tutte le interfacce degli eventi di input disponibili che devono essere implementate da un componente monobehavior personalizzato. Queste interfacce verranno chiamate dal sistema di input MRTK per gestire la logica dell'app personalizzata in base alle interazioni di input dell'utente. [Gli eventi di input del puntatore](pointers.md#pointer-event-interfaces) vengono gestiti in modo leggermente diverso rispetto ai tipi di evento di input standard seguenti.

> [!IMPORTANT]
> Per impostazione predefinita, uno script riceverà gli eventi di input solo se il GameObject è attivo da un puntatore o un elemento padre di un GameObject nello stato attivo.

| Gestore | Eventi | Descrizione |
| --- | :---: | --- |
| [`IMixedRealitySourceStateHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySourceStateHandler) | Origine rilevata/persa | Generato quando viene rilevata o persa un'origine di input, ad esempio quando viene rilevata una mano articolata o ne viene persa la traccia. |
| [`IMixedRealitySourcePoseHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySourcePoseHandler) | Modifica dell'origine modificata | Generato in base alle modifiche apportate all'origine. La posa di origine rappresenta la causa generale dell'origine di input. Le pose specifiche, ad esempio il grip o il puntatore che si pongono in un sei controller DOF, possono essere ottenute tramite `IMixedRealityInputHandler<MixedRealityPose>` . |
| [`IMixedRealityInputHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler) | Input inattivo/alto | Generato in merito a modifiche apportate a input binari come pulsanti. |
| [`IMixedRealityInputHandler<T>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler`1) | Input modificato | Generato in base alle modifiche apportate agli input del tipo specificato. **T** può assumere i valori seguenti: <br/> - *float* (ad esempio, restituisce un trigger analogo)<br/> - *Vector2* (ad esempio, restituisce la direzione del levetta del gamepad) <br/> - *Vector3* (ad esempio, la posizione di ritorno del dispositivo rilevato) <br/> - *Quaternione* (ad esempio, restituisce l'orientamento del dispositivo rilevato)<br/> - [MixedRealityPose](xref:Microsoft.MixedReality.Toolkit.Utilities.MixedRealityPose) (ad esempio, restituisce un dispositivo completamente rilevato) |
| [`IMixedRealitySpeechHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySpeechHandler) | Parola chiave Speech riconosciuta | Generato al riconoscimento di una delle parole chiave configurate nel *profilo dei comandi vocali*. |
| [`IMixedRealityDictationHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityDictationHandler) | Dettatura<br/> Hypothesis <br/> Risultato <br/> Operazione completata <br/> Errore | Generato da sistemi di dettatura per segnalare i risultati di una sessione di dettatura. |
| [`IMixedRealityGestureHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGestureHandler) | Eventi movimento su: <br/> Avviato <br/> Aggiornato <br/> Completato <br/> Cancellati | Generato al rilevamento del movimento. |
| [`IMixedRealityGestureHandler<T>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGestureHandler`1) | Gesto aggiornato/completato | Generato al rilevamento di movimenti contenenti dati aggiuntivi del tipo specificato. Per informazioni dettagliate sui valori possibili per **T**, vedere [**eventi di movimento**](gestures.md#gesture-events) . |
| [`IMixedRealityHandJointHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHandJointHandler) | Giunzioni della mano aggiornate | Generato da controller della mano articolati quando vengono aggiornati i giunti di mano. |
| [`IMixedRealityHandMeshHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHandMeshHandler) | Mesh a mano aggiornata | Generato da controller della mano articolati quando viene aggiornata una mesh mano. |
| [`IMixedRealityInputActionHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputActionHandler) | Azione avviata/terminata | Raise per indicare l'inizio e la fine dell'azione per gli input mappati alle azioni. |

## <a name="input-events-in-action"></a>Eventi di input in azione

A livello di script, gli eventi di input possono essere utilizzati implementando una delle interfacce del gestore eventi illustrate nella tabella precedente. Quando viene generato un evento di input tramite un'interazione dell'utente, si verifica quanto segue:

1. Il sistema di input MRTK rileva che si è verificato un evento di input.
1. Il sistema di input MRTK genera la funzione di interfaccia pertinente dell'evento di input in tutti i [gestori di input globali registrati](#register-for-global-input-events)
1. Per ogni puntatore attivo registrato con il sistema di input:
    1. Il sistema di input determina quale GameObject è attivo per il puntatore corrente.
    1. Il sistema di input usa il [sistema di eventi di Unity](https://docs.unity3d.com/Manual/EventSystem.html) per attivare la funzione di interfaccia pertinente per tutti i componenti corrispondenti nel GameObject attivo.
    1. Se in qualsiasi momento un evento di input è stato [contrassegnato come usato](#how-to-stop-input-events), il processo terminerà e nessun altro GameObject riceverà i callback.
        - Esempio: i componenti che implementano l'interfaccia [`IMixedRealitySpeechHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySpeechHandler) verranno cercati quando viene riconosciuto un comando vocale.
        - Nota: il sistema di eventi Unity verrà propagato per eseguire una ricerca nel GameObject padre se non sono stati trovati componenti corrispondenti all'interfaccia desiderata nell'GameObject corrente.
1. Se non viene registrato alcun gestore di input globale e non viene trovato alcun GameObject con un componente/interfaccia corrispondente, il sistema di input chiamerà ogni gestore di input di fallback registrato

> [!NOTE]
> [Gli eventi di input del puntatore](pointers.md#pointer-event-interfaces) vengono gestiti in modo leggermente diverso rispetto alle interfacce degli eventi di input elencate in precedenza. In particolare, gli eventi di input del puntatore vengono gestiti solo dal GameObject attivo dal puntatore che ha attivato l'evento di input, nonché da eventuali gestori di input globali. Gli eventi di input normali vengono gestiti da GameObject in stato attivo per tutti i puntatori attivi.

### <a name="input-event-interface-example"></a>Esempio di interfaccia evento di input

Il codice seguente illustra l'uso dell' [`IMixedRealitySpeechHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySpeechHandler) interfaccia. Quando l'utente indica le parole "più piccole" o "più grandi", concentrandosi su un GameObject con questa `ShowHideSpeechHandler` classe, il GameObject verrà ridimensionato a metà o due volte.

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
> [`IMixedRealitySpeechHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySpeechHandler) per gli eventi di input è necessario che le parole chiave desiderate siano pre-registrate nel [profilo dei comandi vocali MRTK](speech.md).

## <a name="register-for-global-input-events"></a>Registra per gli eventi di input globali

Per creare un componente che rimane in ascolto di eventi di input globali, indipendentemente da quale GameObject potrebbe essere attivo, un componente deve registrarsi con il sistema di input. Una volta effettuata la registrazione, tutte le istanze di questo monocomportamento riceveranno gli eventi di input insieme a qualsiasi GameObject attualmente attivo e ad altri listener registrati a livello globale.

Se un evento di input è stato [contrassegnato come usato](#how-to-stop-input-events), i gestori registrati globali riceveranno comunque tutti i callback. Tuttavia, nessun GameObject con stato attivo riceverà l'evento.

### <a name="global-input-registration-example"></a>Esempio di registrazione di input globale

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

## <a name="register-for-fallback-input-events"></a>Registra per gli eventi di input di fallback

I gestori di input di fallback sono simili ai gestori di input globali registrati, ma vengono considerati come ultima risorsa per la gestione degli eventi di input. Solo se non sono stati trovati gestori di input globali e nessun GameObject è attivo, verranno utilizzati i gestori di input di fallback.

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

Ogni interfaccia dell'evento di input fornisce un [`BaseInputEventData`](xref:Microsoft.MixedReality.Toolkit.Input.BaseInputEventData) oggetto dati come parametro per ogni funzione nell'interfaccia. Questo oggetto dati di evento si estende dall'oggetto di Unity [`AbstractEventData`](https://docs.unity3d.com/2019.1/Documentation/ScriptReference/EventSystems.AbstractEventData.html) .

Per arrestare la propagazione di un evento di input attraverso l'esecuzione [come indicato](#input-events-in-action), un componente può chiamare [`AbstractEventData.Use()`](https://docs.unity3d.com/2019.1/Documentation/ScriptReference/EventSystems.AbstractEventData.Use.html) per contrassegnare l'evento come usato. Questo impedirà a qualsiasi altro GameObject di ricevere l'evento di input corrente, ad eccezione dei gestori di input globali.

> [!NOTE]
> Un componente che chiama il `Use()` Metodo arresterà la ricezione da parte di altri GameObject. Tuttavia, altri componenti sul GameObject corrente riceveranno comunque l'evento di input e attiveranno le funzioni di interfaccia correlate.

## <a name="see-also"></a>Vedi anche

- [Puntatori](pointers.md)
- [Voce](speech.md)
- [Stato input](input-state.md)

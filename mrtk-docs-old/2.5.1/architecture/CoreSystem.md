---
title: CoreSystem
description: Sistema di input, gestione dispositivi e provider di dati in MRTK
author: cDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, eventi
ms.openlocfilehash: 4605a36dc22136acebe47ea32b07f5012d55c3b1
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/03/2021
ms.locfileid: "101782025"
---
# <a name="core-system"></a>Sistema principale

Il fulcro del sistema di input è [InputSystem](../features/input/Overview.md), ovvero un servizio responsabile dell'inizializzazione e della gestione di tutte le funzionalità correlate all'input associate al MRTK.

> [!NOTE]
> Si presuppone che i lettori abbiano già letto e abbiano una conoscenza di base della sezione [terminologia](Terminology.md) .

Questo servizio è responsabile di:

- Lettura del [profilo di sistema di input](../configuration/MixedRealityConfigurationGuide.md#input-system-settings)
- Avvio dei [provider di dati](../features/input/InputProviders.md) configurati, ad esempio `Windows Mixed Reality Device Manager` e `OpenVR Device Manager` .
- Creazione di un'istanza di [GazeProvider](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGazeProvider), che è un componente responsabile della fornitura di informazioni sugli sguardi di stile HoloLens (1a generazione) oltre alle informazioni sugli sguardi dello stile di HoloLens 2.
- Creazione di un'istanza di [FocusProvider](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityFocusProvider), che è un componente responsabile della determinazione degli oggetti con lo stato attivo. Questa operazione viene descritta più dettagliatamente nella sezione [puntatori e stato attivo](ControllersPointersAndFocus.md#pointers-and-focus) della documentazione.
- Fornire punti di registrazione per tutti gli eventi di input (come [listener globali](#global-listeners)).
- Fornire funzionalità di invio di eventi per gli eventi di input.

## <a name="input-events"></a>Eventi di input

Gli eventi di input vengono in genere generati in due canali diversi:

### <a name="objects-in-focus"></a>Oggetti con stato attivo

Gli eventi possono essere inviati direttamente a un GameObject con lo stato attivo. Ad esempio, un oggetto potrebbe avere uno script che implementa [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler) .
Questo oggetto riceve gli eventi di tocco quando si è concentrati su una mano vicina. Questi tipi di eventi passano alla gerarchia GameObject fino a trovare un GameObject in grado di gestire l'evento.

Questa operazione viene eseguita utilizzando [ExecuteHierarchy](https://docs.unity3d.com/ScriptReference/EventSystems.ExecuteEvents.ExecuteHierarchy.html) all'interno dell'implementazione del sistema di input predefinito.

### <a name="global-listeners"></a>Listener globali

Gli eventi possono essere inviati a listener globali. È possibile registrare tutti gli eventi di input usando l'interfaccia del sistema di input [`IMixedRealityEventSystem`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityEventSystem) . È consigliabile usare il metodo [RegisterHandler](xref:Microsoft.MixedReality.Toolkit.IMixedRealityEventSystem.RegisterHandler``1(IEventSystemHandler)) per la registrazione per gli eventi globali. la funzione deprecata provocherà la `Register` notifica di tutti gli eventi di input da parte dei listener, anziché solo eventi di input di un determinato tipo (in cui il tipo è definito dall'interfaccia eventi).

Si noti che i [listener di fallback](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityInputSystem.PushFallbackInputHandler(GameObject)) sono un altro tipo di listener globali che sono sconsigliati perché riceveranno ogni singolo evento di input che non è stato gestito altrove nella scena.

### <a name="order-of-event-dispatch"></a>Ordine di invio eventi

In genere, gli eventi vengono inviati ai listener nel modo seguente. Si noti che se uno dei passaggi seguenti contrassegna l'evento come [gestito](https://docs.unity3d.com/ScriptReference/EventSystems.AbstractEventData-used.html), il processo di invio dell'evento viene interrotto.

1. L'evento viene inviato ai listener globali.
2. L'evento viene inviato alle finestre di dialogo modali dell'oggetto attivo.
3. L'evento viene inviato all'oggetto con lo stato attivo.
4. L'evento viene inviato ai listener di fallback.

## <a name="device-managers-and-data-providers"></a>Gestione dispositivi e provider di dati

Queste entità sono responsabili dell'interazione con le API di livello inferiore, ad esempio le API di realtà mista di Windows o delle API OpenVR, e la conversione dei dati da tali sistemi in quelli che soddisfano le astrazioni di input di livello superiore di MRTK. Sono responsabili del rilevamento, della creazione e della gestione del ciclo di vita dei [controller](ControllersPointersAndFocus.md#controllers).

Il flusso di base di una gestione dispositivi comporta:

1. Viene creata un'istanza di gestione dispositivi dal servizio di sistema di input.
2. Gestione dispositivi viene registrato con il sistema sottostante (ad esempio, la gestione dei dispositivi con la realtà mista di Windows viene registrata per gli eventi di [input](../features/input/InputEvents.md) e di [movimento](../features/input/Gestures.md#gesture-events) .
3. Crea controller che individua dal sistema sottostante (ad esempio, il provider potrebbe rilevare la presenza di mani articolate)
4. Nel ciclo di aggiornamento () chiamare UpdateController () per eseguire il polling del nuovo stato del sistema sottostante e aggiornare la relativa rappresentazione del controller.

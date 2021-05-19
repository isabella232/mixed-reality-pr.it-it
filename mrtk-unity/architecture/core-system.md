---
title: Sistema di base
description: Sistema di input, gestori di dispositivi e provider di dati in MRTK
author: cDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, eventi
ms.openlocfilehash: 12719a6c749a03648d4f75e9e6461b85cc9ab275
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144296"
---
# <a name="core-system"></a>Sistema di base

Il centro del sistema di input è [InputSystem,](../features/input/overview.md)un servizio responsabile dell'inizializzazione e del funzionamento di tutte le funzionalità correlate all'input associate a MRTK.

> [!NOTE]
> Si presuppone che i lettori hanno già letto e hanno una conoscenza di base della [sezione terminologia.](terminology.md)

Questo servizio è responsabile di:

- Lettura del profilo [di sistema di input](../configuration/mixed-reality-configuration-guide.md#input-system-settings)
- Avvio dei provider [di dati configurati](../features/input/input-providers.md) , ad esempio e `Windows Mixed Reality Device Manager` `OpenVR Device Manager` .
- Creazione di un'istanza di [GazeProvider,](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGazeProvider)che è un componente responsabile della fornitura di informazioni sullo sguardo della testa dello stile HoloLens (prima generazione), oltre a HoloLens 2 informazioni sullo sguardo oculare.
- Creazione di un'istanza [di FocusProvider](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityFocusProvider), che è un componente responsabile della determinazione degli oggetti con stato attivo. Questa operazione è descritta in modo più approfondito nella sezione [puntatori](controllers-pointers-and-focus.md#pointers-and-focus) e stato attivo della documentazione.
- Fornire punti di registrazione per tutti gli eventi di input [(come listener globali).](#global-listeners)
- Fornire funzionalità di invio di eventi per tali eventi di input.

## <a name="input-events"></a>Eventi di input

Gli eventi di input vengono in genere generati in due canali diversi:

### <a name="objects-in-focus"></a>Oggetti nello stato attivo

Gli eventi possono essere inviati direttamente a un GameObject con lo stato attivo. Ad esempio, un oggetto potrebbe avere uno script che implementa [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler) .
Questo oggetto otterrà eventi di tocco quando viene selezionato da una mano vicina. Questi tipi di eventi passano "verso l'alto" nella gerarchia GameObject finché non trova un GameObject in grado di gestire l'evento.

Questa operazione viene eseguita usando [ExecuteHierarchy dall'interno](https://docs.unity3d.com/ScriptReference/EventSystems.ExecuteEvents.ExecuteHierarchy.html) dell'implementazione del sistema di input predefinita.

### <a name="global-listeners"></a>Listener globali

Gli eventi possono essere inviati a listener globali. È possibile eseguire la registrazione per tutti gli eventi di input usando l'interfaccia del sistema di [`IMixedRealityEventSystem`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityEventSystem) input. È consigliabile usare il metodo [RegisterHandler](xref:Microsoft.MixedReality.Toolkit.IMixedRealityEventSystem.RegisterHandler%2A) per la registrazione per gli eventi globali. La funzione deprecata invierà ai listener la notifica di TUTTI gli eventi di input, anziché solo gli eventi di input di un determinato tipo (in cui il tipo è definito dall'interfaccia `Register` eventi).

Si noti che i listener di [fallback](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityInputSystem.PushFallbackInputHandler%2A) sono un altro tipo di listener globali che sono anche sconsigliati perché riceveranno ogni singolo evento di input che non è stato gestito altrove nella scena.

### <a name="order-of-event-dispatch"></a>Ordine di invio degli eventi

In genere, gli eventi vengono inviati ai listener nel modo seguente. Si noti che se uno dei passaggi seguenti contrassegna l'evento [come](https://docs.unity3d.com/ScriptReference/EventSystems.AbstractEventData-used.html)gestito, il processo di invio degli eventi si arresta.

1. L'evento viene inviato ai listener globali.
2. L'evento viene inviato alle finestre di dialogo modali dell'oggetto con lo stato attivo.
3. L'evento viene inviato all'oggetto con lo stato attivo.
4. L'evento viene inviato ai listener di fallback.

## <a name="device-managers-and-data-providers"></a>Gestori di dispositivi e provider di dati

Queste entità sono responsabili dell'interfacciamento con LE API di livello inferiore (ad esempio API Windows Mixed Reality o API OpenVR) e della conversione dei dati da tali sistemi in quelle che si adattano alle astrazioni di input di livello superiore di MRTK. Sono responsabili del rilevamento, della creazione e della gestione della durata dei [controller](controllers-pointers-and-focus.md#controllers).

Il flusso di base di un gestore di dispositivi prevede:

1. Gestione dispositivi viene creata un'istanza dal servizio di sistema di input.
2. Gestione dispositivi si registra con il sistema sottostante(ad esempio, Windows Mixed Reality gestione dispositivi si registrerà per gli eventi [di input](../features/input/input-events.md) [e](../features/input/gestures.md#gesture-events) movimento.
3. Crea controller individuati dal sistema sottostante (ad esempio il provider può rilevare la presenza di mani articolate)
4. Nel ciclo Update() chiamare UpdateController() per eseguire il polling del nuovo stato del sistema sottostante e aggiornare la relativa rappresentazione del controller.

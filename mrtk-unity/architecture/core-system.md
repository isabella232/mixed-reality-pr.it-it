---
title: Sistema core
description: Sistema di input, gestori di dispositivi e provider di dati in MRTK
author: cDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, eventi
ms.openlocfilehash: ff4c23b796374940de1a1de6b72e08702d6fd24f79234e8ef80dc1210d13d103
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115190181"
---
# <a name="core-system"></a>Sistema core

Alla base del sistema di input c'è [InputSystem,](../features/input/overview.md)un servizio responsabile dell'inizializzazione e del funzionamento di tutte le funzionalità correlate all'input associate a MRTK.

> [!NOTE]
> Si presuppone che i lettori hanno già letto e hanno una conoscenza di base della [sezione terminologia.](terminology.md)

Questo servizio è responsabile di:

- Lettura del profilo [del sistema di input](../configuration/mixed-reality-configuration-guide.md#input-system-settings)
- Avvio dei provider [di dati configurati](../features/input/input-providers.md) , ad esempio e `Windows Mixed Reality Device Manager` `OpenVR Device Manager` .
- Creazione di un'istanza di [GazeProvider,](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityGazeProvider)che è un componente responsabile di fornire informazioni sullo sguardo fisso con la testa in stile HoloLens (prima generazione), oltre HoloLens 2 informazioni sullo sguardo fisso.
- Creazione di un'istanza [di FocusProvider](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityFocusProvider), che è un componente responsabile della determinazione degli oggetti con lo stato attivo. Questa operazione è descritta in modo più approfondito nella [sezione puntatori e stato](controllers-pointers-and-focus.md#pointers-and-focus) attivo della documentazione.
- Fornire punti di registrazione per tutti gli eventi di input [(come listener globali).](#global-listeners)
- Fornire funzionalità di invio degli eventi per tali eventi di input.

## <a name="input-events"></a>Eventi di input

Gli eventi di input vengono in genere generati in due canali diversi:

### <a name="objects-in-focus"></a>Oggetti con stato attivo

Gli eventi possono essere inviati direttamente a un GameObject con lo stato attivo. Ad esempio, un oggetto potrebbe avere uno script che implementa [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler) .
Questo oggetto otterrà gli eventi di tocco quando viene selezionato da una mano vicina. Questi tipi di eventi passano verso l'alto nella gerarchia di GameObject fino a trovare un GameObject in grado di gestire l'evento.

Questa operazione viene eseguita usando [ExecuteHierarchy](https://docs.unity3d.com/ScriptReference/EventSystems.ExecuteEvents.ExecuteHierarchy.html) dall'implementazione del sistema di input predefinito.

### <a name="global-listeners"></a>Listener globali

Gli eventi possono essere inviati a listener globali. È possibile eseguire la registrazione per tutti gli eventi di input usando l'interfaccia del sistema di [`IMixedRealityEventSystem`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityEventSystem) input. È consigliabile usare il metodo [RegisterHandler](xref:Microsoft.MixedReality.Toolkit.IMixedRealityEventSystem.RegisterHandler%2A) per la registrazione per gli eventi globali. La funzione deprecata causerà la notifica di tutti gli eventi di input ai listener, anziché solo degli eventi di input di un determinato tipo (dove il tipo è definito dall'interfaccia `Register` eventi).

Si noti che i listener di [fallback](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityInputSystem.PushFallbackInputHandler%2A) sono un altro tipo di listener globali che sono sconsigliati perché riceveranno ogni singolo evento di input che non è stato gestito altrove nella scena.

### <a name="order-of-event-dispatch"></a>Ordine di invio dell'evento

In genere, gli eventi vengono inviati ai listener nel modo seguente. Si noti che se uno dei passaggi seguenti contrassegna l'evento [come](https://docs.unity3d.com/ScriptReference/EventSystems.AbstractEventData-used.html)gestito, il processo di invio dell'evento si arresta.

1. L'evento viene inviato ai listener globali.
2. L'evento viene inviato alle finestre di dialogo modali dell'oggetto con lo stato attivo.
3. L'evento viene inviato all'oggetto con lo stato attivo.
4. L'evento viene inviato ai listener di fallback.

## <a name="device-managers-and-data-providers"></a>Gestori di dispositivi e provider di dati

Queste entità sono responsabili dell'interfacciamento con API di livello inferiore (ad esempio API Windows Mixed Reality o API OpenVR) e della conversione dei dati da tali sistemi in api che rientrano nelle astrazioni di input di livello superiore di MRTK. Sono responsabili del rilevamento, della creazione e della gestione della durata dei [controller](controllers-pointers-and-focus.md#controllers).

Il flusso di base di una gestione dispositivi prevede:

1. Gestione dispositivi viene creata dal servizio di sistema di input.
2. Gestione dispositivi si registra con il sistema sottostante (ad esempio, il Windows Mixed Reality verrà registrato per gli eventi [di input](../features/input/input-events.md) [e](../features/input/gestures.md#gesture-events) movimento.
3. Crea controller che individua dal sistema sottostante (ad esempio, il provider può rilevare la presenza di mani articolate)
4. Nel ciclo Update() chiamare UpdateController() per eseguire il polling del nuovo stato del sistema sottostante e aggiornare la relativa rappresentazione del controller.

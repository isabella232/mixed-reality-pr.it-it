---
title: Feature_Contribution_Process
description: documentazione per l'aggiunta di funzionalità a MRTK.
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: afc20c9764fe7fa8d10b10bdc34d952e657a20a6
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2021
ms.locfileid: "104683474"
---
# <a name="feature-contribution-process"></a>Processo di contributo delle funzionalità

> [!WARNING]
> 10/1/2019: Questa pagina è deprecata perché fornisce linee guida per contribuire ai sistemi di grandi dimensioni a MRTK prima della versione 2,0. Dopo la versione 2,0, le modifiche di grandi dimensioni devono essere eseguite con maggiore attenzione e il processo per questa operazione non è ancora stato deciso. Si prevede che la maggior parte dei contributi MRTK abbia modifiche molto più piccole rispetto a quanto illustrato qui.

L'aggiunta di funzionalità al Toolkit di realtà mista (MRTK) è suddivisa in alcuni passaggi di iterazione, quindi i gestori possono avere tempo per rivedere e garantire la corretta esecuzione del processo. Prima di iniziare, assicurarsi di esaminare l'elenco dei [requisiti delle funzionalità](#new-feature-requirements) .

## <a name="process"></a>Processo

Il processo seguente è stato elaborato per garantire che tutti i nuovi lavori siano conformi agli standard e all'architettura aggiornati definiti per MRTK, che sono stati definiti come segue:

1. [Aprire una nuova proposta e le attività correlate](#new-proposal)
2. [Inviare una bozza o una struttura dell'architettura](#architecture-draft)
3. [Esaminare e finalizzare la documentazione dell'architettura](#architecture-documentation)
4. [Inviare una richiesta pull implementando le interfacce delle funzionalità di base e il riferimento all'evento (se applicabile)](#core-implementation)
5. [Inviare una richiesta pull per implementare gli eventuali componenti SDK necessari](#sdk-implementation)
6. [Inviare una richiesta pull che implementa demo di funzionalità o esempi di scalabilità completa](#example-implementation)

### <a name="new-proposal"></a>Nuova proposta

Per iniziare, aprire una nuova proposta o un'attività che descrive la funzionalità o il problema che si vuole risolvere. Descrivere l'approccio e il modo in cui si inserisce nella versione del Toolkit di realtà mista di destinazione. Questo consentirà a tutti di discutere sulla proposta e, eventualmente, di identificare alcuni potenziali problemi prima dell'avvio di qualsiasi lavoro.

Le nuove proposte verranno esaminate e discusse durante le riunioni settimanali della spedizione e se viene accettata una proposta, verranno create e assegnate attività aggiuntive.

### <a name="architecture-draft"></a>Bozza di architettura

La prima attività dopo che la proposta iniziale è stata accettata, sarà la bozza del documento di architettura iniziale per la funzionalità o il lavoro da eseguire. Questo documento deve essere in genere costituito da una o due pagine e include una panoramica di alto livello della funzionalità e il modo in cui sarà correlato ad altre parti del Toolkit di realtà mista.

* Il progetto deve essere facile da utilizzare con le aree principali evidenziate.
* La bozza deve includere un elenco di interfacce di base proposte, profili di configurazione e Datum di evento.
* Il progetto deve includere una semplice rappresentazione grafica dell'architettura proposta.

Assicurarsi che l'architettura della funzionalità sia conforme ai [nuovi requisiti di funzionalità](#new-feature-requirements) impostati dall'architettura MRTK di base.

>TODO: aggiungere un collegamento al modello bozza dell'architettura

Al termine della bozza, questo può essere aggiunto al problema della proposta/attività in GitHub per la revisione finale pubblica.

### <a name="architecture-documentation"></a>Documentazione sull'architettura

Una volta accettata l'architettura bozza, è possibile effettuare richieste pull aggiuntive per inviare i documenti di architettura completa finale al repository.

>TODO: aggiungere un collegamento al modello di architettura completo

Una volta approvato il documento di architettura, possono essere eseguiti solo i primi invii di codice.

Lo sviluppo può iniziare nel ramo privato e essere completato normalmente. Tuttavia, le richieste pull di riferimento al progetto MRTK di base devono essere inviate in fasi per garantire che la revisione e l'approvazione siano uniformi, e che le modifiche di base non influiscano sulle altre funzionalità.

### <a name="core-implementation"></a>Implementazione di base

Il lavoro iniziale da inviare consiste nell'implementare:

* Definizioni
* Interfacce
* Profili di configurazione
* Dati dell'evento

Se necessario, è possibile aggiornare il documento di architettura per allinearlo alle modifiche apportate all'implementazione.

Assicurarsi che tutti gli unit test esistenti e tutti i nuovi test vengano superati prima dell'invio.

### <a name="sdk-implementation"></a>Implementazione di SDK

Una volta che gli eventi e le interfacce principali vengono uniti allo sviluppo, è possibile inviare lavoro per i componenti SDK.  Aggiunta dell'implementazione concreta della funzionalità e test sulle piattaforme e unit test supportati.

### <a name="example-implementation"></a>Implementazione di esempio

Una volta che i componenti SDK sono Stati Uniti, è possibile inviare qualsiasi scena demo o aggiornamento alle scene di esempio.

* Demo per evidenziare funzionalità e dimostrazione specifiche
* Esempi sono esempi di apprendimento della scena di lavoro completo

## <a name="new-feature-requirements"></a>Nuovi requisiti delle funzionalità

La maggior parte delle implementazioni delle funzionalità può essere suddivisa in tre parti principali:

1. [Gestione funzionalità](#manager-implementation-requirements)
2. [Dati dell'evento](#event-data-implementation-requirements) (facoltativo)
3. [Gestore di funzionalità](#handler-implementation-requirements) (facoltativo)

### <a name="manager-implementation-requirements"></a>Requisiti di implementazione del responsabile

* Definizioni di assembly per il codice esterno alla `MRTK/Core` cartella.
  * In questo modo le funzionalità sono indipendenti e non hanno dipendenze con altre funzionalità.
* Essere definito utilizzando un'interfaccia presente in `MRTK/Core/Definitions/<FeatureName>System` .
* Un'implementazione di gestione concreta di una funzionalità deve ereditare direttamente da `BaseManager` o `MixedRealityEventManager` se genera eventi.
* Un'implementazione di gestione concreta di una funzionalità dovrebbe configurare e verificare che la scena sia pronta per il sistema in uso in `Initialize` .
* Un responsabile concreto di una funzionalità dovrebbe anche pulire dopo aver rimosso qualsiasi elemento creato nella scena in `Destroy` .
* Essere registrato con il responsabile della realtà mista.
  * Se la funzionalità è una funzionalità di base, deve essere codificata in `MixedRealityToolkit` e `CoreServices` e aggiunta a `MixedRealityConfigurationProfile` .
    * Ciò include la possibilità di specificare un'implementazione concreta tramite l'elenco a discesa usando `SystemType` .
    * Le funzionalità devono disporre di un profilo di configurazione che deriva da un oggetto con script.
    * Un profilo di configurazione predefinito che si trova in `MRTK/SDK/Profiles` e deve essere assegnato nel profilo di configurazione predefinito per il gestore di realtà misto
  * Se questa funzionalità **non** è una funzionalità di base, è necessario registrarla utilizzando il profilo di configurazione del servizio di estensione e implementare `IMixedRealityExtensionService` .
* In è disponibile un'implementazione predefinita `MRTK/Services/<FeatureName>`
* Gli eventi che possono essere generati con il sistema devono essere definiti nell'interfaccia, con tutti i parametri obbligatori per inizializzare i dati dell'evento.

### <a name="event-data-implementation-requirements"></a>Requisiti di implementazione dei dati degli eventi

I dati dell'evento definiscono esattamente quali dati devono essere ricevuti dal gestore dall'evento.

* Tutti i riferimenti all'evento per la funzionalità devono essere definiti in `MixedRealityToolkit/EventDatum/<FeatureName>` .
* Tutte le nuove classi di dati degli eventi devono ereditare da `GenericBaseEventData`

### <a name="handler-implementation-requirements"></a>Requisiti di implementazione del gestore

L'interfaccia del gestore definisce ogni evento di cui un componente deve essere in ascolto e i tipi di dati passati. Gli utenti finali implementeranno l'interfaccia per eseguire la logica in base ai dati degli eventi ricevuti.

* Le interfacce del gestore devono essere definite in `MixedRealityToolkit/Interfaces/<FeatureName>System/Handlers` .
* Le interfacce del gestore devono ereditare da `UnityEngine.EventSystems.IEventSystemHandler`
* Per impostazione predefinita, acconsentire esplicitamente. Per ricevere gli eventi dal sistema, è necessario che il gestore si registri con il sistema per la ricezione degli eventi.

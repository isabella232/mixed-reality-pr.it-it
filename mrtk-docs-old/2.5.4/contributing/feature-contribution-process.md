---
title: Feature_Contribution_Process
description: documentazione per l'aggiunta di funzionalità a MRTK.
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: 3d9cc25c8a69e5b2b5acc31e758d747d4a6f3015b30da7f49a055a20535f3150
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115192541"
---
# <a name="feature-contribution-process"></a>Processo di contributo alle funzionalità

> [!WARNING]
> 10/1/2019: questa pagina è deprecata perché fornisce linee guida per contribuire a sistemi di grandi dimensioni a MRTK prima della versione 2.0. Dopo la versione 2.0, le modifiche di grandi dimensioni devono essere eseguite con maggiore attenzione e il processo non è ancora deciso. Si prevede che la maggior parte dei contributi di MRTK abbia modifiche molto più piccole rispetto a quelle trattate qui.

L'aggiunta di funzionalità a Mixed Reality Toolkit (MRTK) è suddivisa in pochi passaggi di iterazione, in modo che i maintainer possano avere tempo per esaminare e verificare che il processo funzioni senza problemi. Assicurarsi di esaminare l'elenco dei requisiti [delle funzionalità](#new-feature-requirements) prima di iniziare.

## <a name="process"></a>Processo

Il processo seguente è stato definito per garantire che tutto il nuovo lavoro sia conforme agli standard e all'architettura aggiornati definiti per MRTK, come segue:

1. [Aprire una nuova proposta e le attività correlate](#new-proposal)
2. [Inviare una bozza o una struttura dell'architettura](#architecture-draft)
3. [Esaminare e finalizzare la documentazione sull'architettura](#architecture-documentation)
4. [Inviare una richiesta pull che implementa le interfacce di funzionalità di base e il datum dell'evento (se applicabile)](#core-implementation)
5. [Inviare una richiesta pull implementando tutti i componenti SDK necessari](#sdk-implementation)
6. [Inviare una richiesta pull Implementazione di demo di funzionalità o esempi di scalabilità completa](#example-implementation)

### <a name="new-proposal"></a>Nuova proposta

Per iniziare, aprire una nuova proposta o attività che descrive la funzionalità o il problema che si vuole risolvere. Descrivere l'approccio e il modo in cui si inserisce nella versione del Toolkit di destinazione. In questo modo tutti potranno discutere della proposta e, possibilmente, identificare alcuni potenziali insidie prima dell'avvio di qualsiasi lavoro.

Le nuove proposte verranno esaminate e discusse durante le riunioni settimanali della sala di spedizione e, se viene accettata una proposta, verranno quindi create e assegnate attività supplementari.

### <a name="architecture-draft"></a>Bozza dell'architettura

La prima attività dopo l'accettazione della proposta iniziale sarà la bozza del documento di architettura iniziale per la funzionalità o il lavoro da eseguire. Questo documento deve essere in genere lungo una o due pagine e includere una panoramica generale della funzionalità e del modo in cui sarà correlata ad altre parti del modello di realtà Toolkit.

* La bozza deve essere facile da usare con le aree chiave evidenziate.
* La bozza deve includere un elenco delle interfacce principali proposte, dei profili di configurazione e dei dati degli eventi.
* La bozza deve includere un semplice grafico dell'architettura proposta.

Assicurarsi che l'architettura della funzionalità sia conforme ai nuovi requisiti [di funzionalità](#new-feature-requirements) impostati dall'architettura CORE MRTK.

>TODO: Aggiungere un collegamento al modello bozza dell'architettura

Una volta completata la bozza, questo può essere aggiunto al problema proposta/attività GitHub per la revisione pubblica finale.

### <a name="architecture-documentation"></a>Documentazione sull'architettura

Una volta accettata la bozza dell'architettura, è possibile inviare al repository richieste pull aggiuntive per inviare i documenti completi finali sull'architettura.

>TODO: Aggiungere un collegamento al modello di architettura completo

Dopo l'approvazione del documento di architettura, è possibile eseguire i primi invii di codice.

Lo sviluppo può iniziare nel proprio ramo privato e completarlo come di consueto, tuttavia, le richieste pull inviate al progetto MRTK principale devono essere inviate in più fasi per garantire che la revisione e l'approvazione siano uniformi quanto lo sono (e assicurarsi che le modifiche di base non influiscono su altre funzionalità)

### <a name="core-implementation"></a>Implementazione di base

Il lavoro iniziale da inviare è implementare:

* Definizioni
* Interfacce
* Profili di configurazione
* Dati dell'evento

Se necessario, il documento dell'architettura può essere aggiornato per allinearsi a eventuali modifiche all'implementazione.

Assicurarsi che tutti gli unit test esistenti e i nuovi test siano tutti superati prima dell'invio.

### <a name="sdk-implementation"></a>Implementazione dell'SDK

Dopo aver unito le interfacce di base e gli eventi allo sviluppo, è possibile inviare il lavoro per i componenti DELL'SDK.  Aggiunta dell'implementazione concreta della funzionalità e test sulle piattaforme e gli unit test supportati.

### <a name="example-implementation"></a>Implementazione di esempio

Dopo aver unito i componenti DELL'SDK, è possibile inviare eventuali scene demo o aggiornamenti alle scene di esempio.

* Le demo sono relative all'evidenziazione e alla dimostrazione di funzionalità specifiche
* Esempi sono esempi di apprendimento completo della scena di lavoro

## <a name="new-feature-requirements"></a>Nuovi requisiti delle funzionalità

La maggior parte delle implementazioni di funzionalità può essere suddivisa in 3 parti principali:

1. [Gestione funzionalità](#manager-implementation-requirements)
2. [Dati evento](#event-data-implementation-requirements) (facoltativo)
3. [Gestore di funzionalità](#handler-implementation-requirements) (facoltativo)

### <a name="manager-implementation-requirements"></a>Requisiti di implementazione del manager

* Definizioni di assembly per codice esterno alla `MRTK/Core` cartella.
  * In questo modo le funzionalità sono indipendenti e non hanno dipendenze da altre funzionalità.
* Essere definito usando un'interfaccia disponibile in `MRTK/Core/Definitions/<FeatureName>System` .
* L'implementazione concreta del gestore di una funzionalità deve ereditare direttamente da `BaseManager` o `MixedRealityEventManager` se genererà eventi.
* L'implementazione concreta del gestore di una funzionalità deve configurare e verificare che la scena sia pronta per l'uso da parte del sistema in `Initialize` .
* Il gestore concreto di una funzionalità deve anche eseguire la pulizia dopo la rimozione di qualsiasi elemento creato nella scena in `Destroy` .
* Essere registrati con Mixed Reality Manager.
  * Se la funzionalità è una funzionalità di base, deve essere hard coded in `MixedRealityToolkit` e e aggiunta a `CoreServices` `MixedRealityConfigurationProfile` .
    * Ciò include la possibilità di specificare un'implementazione concreta tramite l'elenco a discesa usando `SystemType` .
    * Le funzionalità devono avere un profilo di configurazione che deriva da un oggetto gestibile da script.
    * Un profilo di configurazione predefinito che si trova in `MRTK/SDK/Profiles` e deve essere assegnato nel profilo di configurazione predefinito per Mixed Reality Manager
  * Se questa funzionalità non **è una** funzionalità di base, deve essere registrata usando il profilo di configurazione del servizio di estensione e implementare `IMixedRealityExtensionService` .
* Avere un'implementazione predefinita in `MRTK/Services/<FeatureName>`
* Gli eventi che possono essere generati con il sistema devono essere definiti nell'interfaccia , con tutti i parametri obbligatori per l'inizializzazione dei dati dell'evento.

### <a name="event-data-implementation-requirements"></a>Requisiti di implementazione dei dati degli eventi

I dati dell'evento definiscono esattamente i dati che il gestore deve ricevere dall'evento.

* Tutti i dati degli eventi per la funzionalità devono essere definiti in `MixedRealityToolkit/EventDatum/<FeatureName>` .
* Tutte le nuove classi di dati evento devono ereditare da `GenericBaseEventData`

### <a name="handler-implementation-requirements"></a>Requisiti di implementazione del gestore

L'interfaccia del gestore definisce ogni evento che un componente deve essere in ascolto e i tipi di dati passati. Gli utenti finali implementeranno l'interfaccia per eseguire la logica in base ai dati dell'evento ricevuti.

* Le interfacce del gestore devono essere definite in `MixedRealityToolkit/Interfaces/<FeatureName>System/Handlers` .
* Le interfacce del gestore devono ereditare da `UnityEngine.EventSystems.IEventSystemHandler`
* Consenso esplicito per impostazione predefinita. Per ricevere eventi dal sistema, il gestore dovrà registrarsi con il sistema per ricevere tali eventi.

---
title: BreakingChanges
description: criteri riguardanti le modifiche di rilievo nella MRTK.
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: fb4ed438a6dcb6af2d0e421453f98ce62c8f22ea
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/03/2021
ms.locfileid: "101783721"
---
# <a name="breaking-changes"></a>Modifiche che causano un'interruzione

I consumer di MRTK dipendono dalla presenza di una superficie dell'API Release-to-release stabile, in modo che possano eseguire aggiornamenti al MRTK senza dover apportare modifiche di rilievo a grandi dimensioni ogni volta.

In questa pagina vengono descritti i criteri correnti riguardanti le modifiche di rilievo apportate alla MRTK, insieme ad alcuni obiettivi a lungo termine su come migliorare la gestione del compromesso tra la riduzione delle modifiche di rilievo e la possibilità di apportare le modifiche tecniche a lungo termine al codice.

## <a name="what-is-a-breaking-change"></a>Che cos'è una modifica di rilievo?

Una modifica è una modifica di rilievo se soddisfa tutte le condizioni nell' [elenco a](#list-a) e soddisfa tutte le condizioni nell' [elenco B](#list-b)

### <a name="list-a"></a>Elencare un

- L'aggiunta, la rimozione o l'aggiornamento di qualsiasi membro o funzione di qualsiasi interfaccia (o rimozione/ridenominazione dell'intera interfaccia).
- Rimozione, aggiornamento (modifica del tipo/definizione, rendendo privato o interno) qualsiasi membro o funzione della classe protetta o pubblica. (o rimozione/ridenominazione dell'intera classe).
- Modifica dell'ordine degli eventi generati da una classe.
- Ridenominazione di qualsiasi SerializedField privato (senza un tag FormerlySerializedAs corrispondente) o di una proprietà pubblica in un ScriptableObject (in particolare modifiche ai profili).
- Modifica del tipo di un campo in un ScriptableObject (in particolare modifiche ai profili).
- Aggiornamenti allo spazio dei nomi o asmdefs di qualsiasi classe o interfaccia.
- Rimozione di qualsiasi prefabbricata o rimozione di uno script nell'oggetto di primo livello di una prefabbricata.

### <a name="list-b"></a>Elenco B

- L'asset in questione si trova nel pacchetto Foundation, ovvero in una delle cartelle seguenti:

  - MRTK/Core
  - MRTK/provider/
  - MRTK/servizi/
  - MRTK/SDK/
  - MRTK/estensioni

- L'asset in questione non appartiene allo spazio dei nomi sperimentale.

> [!IMPORTANT]
> Tutti gli asset che si trovano nel pacchetto degli esempi (ad esempio, parte di MRTK/examples/Folder) sono soggetti a modifiche in qualsiasi momento, poiché le risorse sono progettate per essere copiate e visualizzate dai consumer come "implementazioni di riferimento", ma non fanno parte del set principale di API e asset. Gli asset nello spazio dei nomi sperimentale (o più in generale, le funzionalità contrassegnate come sperimentali) sono quelli che vengono pubblicati prima che siano state eseguite tutte le operazioni di diligenza (ad esempio, test, iterazione UX, documentazione) e pubblicate in anticipo per ricevere commenti e suggerimenti prima.  Tuttavia, poiché non dispongono di test e documentazione e perché probabilmente non sono state rimosse tutte le interazioni e le progettazioni, le si pubblicano in uno stato in cui il pubblico dovrebbe presumere che possano e cambieranno, ovvero verranno modificati, completamente rimossi e così via.
>
> Per ulteriori informazioni, vedere [funzionalità sperimentali](../Contributing/ExperimentalFeatures.md) .

Poiché la superficie di attacco per le modifiche di rilievo è molto grande, è importante notare che la presenza di una regola assoluta che indica che non sono state apportate modifiche significative potrebbe essere un problema che può essere risolto in modo sano con una modifica di rilievo. Per un altro modo, l'unico modo per ottenere una "nessuna modifica di rilievo" è quello di non avere alcuna modifica.

Il nostro criterio permanente consiste nell'evitare di apportare modifiche di rilievo, se possibile, ed eseguire questa operazione solo se la modifica accumula un notevole valore a lungo termine del cliente o del Framework.

## <a name="what-to-do-about-breaking-changes"></a>Operazioni da eseguire per le modifiche di rilievo

Se è possibile eseguire un'operazione senza una modifica sostanziale e senza compromettere la struttura a lungo termine e la redditività della funzionalità, non eseguire la modifica sostanziale. Se non esiste un altro modo, i criteri correnti consentono di valutare ogni singola modifica di rilievo, per comprendere se il vantaggio derivante dall'adozione della modifica supera il costo del consumatore di assorbire la modifica. Si tratta di un dibattito su ciò che vale la pena e sugli elementi che in genere non si verificano nella richiesta pull o nel problema.

Cosa può accadere qui in diversi bucket:

### <a name="the-breaking-change-adds-value-but-could-be-written-in-a-way-that-isnt-breaking"></a>La modifica di rilievo aggiunge valore ma potrebbe essere scritta in un modo che non si interrompe

[Questa](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/4882) richiesta pull, ad esempio, ha aggiunto una nuova funzionalità inizialmente scritta in un modo in cui è stata modificata un'interfaccia esistente, che è stata quindi riscritta dove la funzionalità è stata suddivisa come interfaccia personalizzata. Si tratta in genere del migliore risultato possibile. Non tentare di forzare una modifica in un modulo senza interruzioni se questa operazione comprometterebbe la redditività o la struttura della funzionalità a lungo termine.

### <a name="the-breaking-change-adds-sufficient-value-to-the-customer-that-its-worth-doing"></a>La modifica di rilievo aggiunge un valore sufficiente al cliente che vale la pena

Documentare le modifiche di rilievo e fornire la migliore mitigazione (ad esempio, procedure descrittive per eseguire la migrazione o migliorare gli strumenti che verranno automaticamente migrati per il cliente). Ogni versione può contenere una piccola quantità di modifiche che vengono interrotte, che devono essere sempre documentate in docs come è stato fatto in [questa](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/4858)richiesta pull. Se è già presente una guida alla migrazione 2. x. x → 2. x +1. x + 1, aggiungere istruzioni o strumenti a tale documento. Se non esiste, crearlo.

### <a name="the-breaking-change-adds-value-but-the-customer-pain-would-be-too-high"></a>La modifica di rilievo aggiunge un valore, ma il dolore del cliente è troppo elevato

Non vengono creati tutti i tipi di modifiche di rilievo. alcuni sono molto più dolorosi che altri, in base alla nostra esperienza e in base alle esperienze dei clienti. Ad esempio, le modifiche alle interfacce possono essere penose. Tuttavia, se la modifica di rilievo è una condizione in cui è improbabile che un cliente abbia esteso/implementato in passato (il sistema di visualizzazione diagnostica, ad esempio), il costo effettivo è probabilmente minimo per niente. Tuttavia, se la modifica è il tipo di un campo in un ScriptableObject (ad esempio, in uno dei profili di base di MRTK), è probabile che si verifichi un notevole dolore dei clienti. I clienti hanno già clonato il profilo predefinito, i profili di Unione/aggiornamento possono essere estremamente difficili da eseguire manualmente (ad esempio, tramite un editor di testo durante l'esecuzione del merge) e la Ricopia del profilo predefinito e la riconfigurazione di tutti gli elementi è molto probabile che si verifichino regressioni difficili da eseguire.

Queste modifiche devono essere riportate sullo scaffale fino a quando non esiste un ramo che consentirà di apportare modifiche significative (insieme a un valore significativo che fornirà ai clienti un motivo per l'aggiornamento). Questo ramo attualmente non esiste. Nelle prossime riunioni di pianificazione dell'iterazione, verrà esaminato il set di modifiche/problemi che erano "troppo importanti" per verificare se è stata raggiunta una massa critica per rendere ragionevole la ricerca di un set di modifiche contemporaneamente. Si noti che è pericoloso creare un ramo "tutto ciò che è consentito" senza che venga eseguita la diligenza a causa delle risorse di progettazione limitate e del fatto che è necessario suddividere i test e la convalida tra questi due. È necessario essere uno scopo chiaro e una data di inizio e di fine con comunicazione corretta di un ramo esistente.

## <a name="long-term-management-of-breaking-changes"></a>Gestione a lungo termine delle modifiche di rilievo

A lungo termine, è consigliabile cercare di ridurre l'ambito di una modifica sostanziale aumentando il set di condizioni nell' [elenco B](#list-b). Il set di elementi nell' [elenco a](#list-a) sarà sempre tecnicamente in fase di suddivisione per il set di file e di asset ritenuti "public API Surface". Il modo in cui possiamo ottenere una maggiore libertà per l'iterazione, ovvero modificare i dettagli di implementazione interni, semplificando il refactoring e la condivisione del codice tra più classi e così via, è più esplicito su quali parti del codice sono la superficie ufficiale, anziché i dettagli di implementazione.

Una delle cose che abbiamo già fatto è il concetto di una funzionalità "sperimentale", che appartiene allo spazio dei nomi sperimentale, che potrebbe non avere test/documentazione e che è disponibile pubblicamente, ma che può essere rimossa e aggiornata senza preavviso. Questo ha consentito di aggiungere nuove funzionalità prima di ottenere un feedback precedente, ma non di essere immediatamente collegato alla relativa superficie API (perché la superficie dell'API potrebbe non essere completamente pensata).

### <a name="other-examples-of-things-that-could-help-in-the-future"></a>Altri esempi di elementi che potrebbero essere utili in futuro

- Utilizzo della [parola chiave internal](https://docs.microsoft.com/dotnet/csharp/language-reference/keywords/internal).
  Questo consentirebbe di avere codice condiviso all'interno degli assembly (per ridurre la duplicazione del codice) senza rendere le cose pubbliche a utenti esterni.
- Creazione di uno spazio dei nomi "interno" (ad esempio Microsoft. MixedReality. Toolkit. Internal. Utilities), in cui viene documentato pubblicamente che qualsiasi elemento contenuto in tale spazio dei nomi interno è soggetto a modifiche in qualsiasi momento e potrebbe essere rimosso e così via. Questa operazione è simile alla modalità con cui le librerie di intestazioni C++ utilizzeranno gli spazi dei nomi:: interni per nascondere i dettagli di implementazione.

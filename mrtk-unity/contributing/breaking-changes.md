---
title: Modifiche che causano un'interruzione
description: Criteri relativi alle modifiche di rilievo in MRTK.
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: 4cd5e0b085a182377aacdf35e1298ad1180ee641
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177275"
---
# <a name="breaking-changes"></a>Modifiche che causano un'interruzione

I consumer di MRTK dipendono dalla presenza di una superficie api da rilascio a versione stabile, in modo che possano eseguire aggiornamenti a MRTK senza dover apportare modifiche importanti ogni volta.

Questa pagina descrive i criteri correnti relativi alle modifiche di rilievo nel codice MRTK, insieme ad alcuni obiettivi a lungo termine relativi al modo in cui è possibile gestire meglio il compromesso tra mantenere basse le modifiche di rilievo e poter apportare le modifiche tecniche a lungo termine giuste al codice.

## <a name="what-is-a-breaking-change"></a>Che cos'è una modifica di rilievo?

Una modifica è una modifica che causa un'interruzione se soddisfa una qualsiasi delle condizioni nell'elenco [A](#list-a) AND soddisfa tutte le condizioni nell'elenco [B](#list-b)

### <a name="list-a"></a>Elenco A

- Aggiunta, rimozione o aggiornamento di qualsiasi membro o funzione di qualsiasi interfaccia (o rimozione/ridenominazione dell'intera interfaccia).
- La rimozione, l'aggiornamento (modifica di tipo/definizione, rendendo privato o interno) di qualsiasi membro o funzione di classe protetta o pubblica. (o rimozione/ridenominazione dell'intera classe).
- Modifica nell'ordine degli eventi generati da una classe .
- Ridenominazione di un serializedField privato (senza un tag FormerlySerializedAs corrispondente) o di una proprietà pubblica in uno ScriptableObject (in particolare le modifiche ai profili).
- Modifica del tipo di un campo in un oggetto ScriptableObject (in particolare modifiche ai profili).
- Aggiornamenti allo spazio dei nomi o agli asmdef di qualsiasi classe o interfaccia.
- Rimozione di qualsiasi prefab o rimozione di uno script nell'oggetto di primo livello di un prefab.

### <a name="list-b"></a>Elenco B

- L'asset in questione si trova nel pacchetto di base, ovvero si trova in una delle cartelle seguenti:

  - MRTK/Core
  - MRTK/Providers/
  - MRTK/Services/
  - MRTK/SDK/
  - MRTK/Extensions

- L'asset in questione non appartiene allo spazio dei nomi sperimentale.

> [!IMPORTANT]
> Qualsiasi asset che si trova nel pacchetto degli esempi (ad esempio, parte della cartella MRTK/Examples/ ) è soggetto a modifiche in qualsiasi momento, poiché gli asset sono progettati per essere copiati e visualizzati dai consumer come "implementazioni di riferimento", ma non fanno parte del set principale di API e asset. Gli asset nello spazio dei nomi sperimentale (o più in generale le funzionalità etichettate come sperimentali) sono quelli che vengono pubblicati prima che siano state eseguite tutte le due diligence (ad esempio test, iterazione dell'esperienza utente, documentazione) e che vengono pubblicati in anticipo per ottenere feedback prima.  Tuttavia, poiché non hanno test e documentazione e, poiché probabilmente non sono state rimosse tutte le interazioni e le progettazioni, vengono pubblicate in uno stato in cui il pubblico deve presupporre che possano e cambieranno (ad esempio, essere modificati, rimossi completamente e così via).
>
> Per [altre informazioni, vedere](../contributing/experimental-features.md) Funzionalità sperimentali.

Poiché la superficie di attacco per le modifiche di rilievo è molto grande, è importante notare che la presenza di una regola assoluta che indica che "nessuna modifica di rilievo" sarebbe impossibile. Potrebbero esserci problemi che possono essere risolti solo in modo corretto con una modifica di rilievo. In altre parole, l'unico modo in cui si potrebbe effettivamente avere "nessuna modifica di rilievo" è non avere alcuna modifica.

Il nostro criterio permanente è evitare di apportare modifiche di rilievo, se possibile, e farlo solo se la modifica accumula un valore significativo a lungo termine del cliente o del framework.

## <a name="what-to-do-about-breaking-changes"></a>Cosa fare per le modifiche di rilievo

Se è possibile eseguire un'operazione senza una modifica di rilievo e senza compromettere la struttura a lungo termine e la fattibilità della funzionalità, non eseguire la modifica di rilievo. Se non esiste altro modo, il criterio corrente è valutare ogni singola modifica che causa un'interruzione, per capire se il vantaggio derivante dall'applicazione della modifica è superiore al costo per il consumatore di assorbire la modifica. Discutere su ciò che vale la pena fare e su ciò che non è in genere avviene nella richiesta pull o nella discussione stessa del problema.

Ciò che può accadere in questo caso è suddiviso in diversi bucket:

### <a name="the-breaking-change-adds-value-but-could-be-written-in-a-way-that-isnt-breaking"></a>La modifica di rilievo aggiunge valore, ma può essere scritta in modo che non si interrompe

Ad [esempio,](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/4882) questa richiesta pull ha aggiunto una nuova funzionalità scritta inizialmente in modo che si interrompeva, modificava un'interfaccia esistente, ma che era stata riscritta in cui la funzionalità era suddivisa come propria interfaccia. Questo è in genere il miglior risultato possibile. Non tentare di forzare una modifica in un modulo non di rilievo se questa operazione compromette la redditività a lungo termine o la struttura della funzionalità.

### <a name="the-breaking-change-adds-sufficient-value-to-the-customer-that-its-worth-doing"></a>La modifica di rilievo aggiunge al cliente un valore sufficiente che vale la pena eseguire

Documentare le modifiche di rilievo e fornire la migliore mitigazione possibile, ad esempio passaggi prescrittivi su come eseguire la migrazione o, meglio ancora, strumenti che eseguiranno automaticamente la migrazione per il cliente. Ogni versione può contenere una piccola quantità di modifiche che causano un'interruzione, che devono essere sempre documentate nella documentazione, come è stato fatto in [questa richiesta pull.](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/4858) Se è già presente una guida alla migrazione 2.x.x→2.x+1.x+1, aggiungere istruzioni o strumenti a tale documento. Se non esiste, crearlo.

### <a name="the-breaking-change-adds-value-but-the-customer-pain-would-be-too-high"></a>La modifica di rilievo aggiunge valore, ma il mal di cliente sarebbe troppo alto

Non tutti i tipi di modifiche che causano un'interruzione sono uguali. Alcuni sono molto più complessi che altri, in base all'esperienza e alle esperienze dei clienti. Ad esempio, le modifiche alle interfacce possono risultare insoddificabili, ma se la modifica di rilievo è quella in cui è improbabile che un cliente abbia esteso/implementato in passato (ad esempio il sistema di visualizzazione diagnostica), il costo effettivo è probabilmente basso o nulla. Tuttavia, se la modifica è il tipo di un campo in uno ScriptableObject (ad esempio, in uno dei profili principali di MRTK), è probabile che ciò causerà enormi problemi per i clienti. I clienti hanno già clonato il profilo predefinito, l'unione/aggiornamento dei profili può essere estremamente difficile da eseguire manualmente (ad esempio tramite un editor di testo durante il periodo di unione) e la copia del profilo predefinito e la riconfigurazione manuale di tutti gli elementi possono causare regressioni difficili da eseguire.

Queste modifiche devono essere rimettite sullo scaffale fino a quando non esiste un ramo che consentirà modifiche che causano un'interruzione significativa (insieme a un valore significativo che offrirà ai clienti un motivo per eseguire l'aggiornamento). Tale ramo non esiste attualmente. Nelle prossime riunioni di pianificazione delle iterazioni verrà esaminato il set di modifiche/problemi che erano "troppo importanti" per verificare se è stata raggiunta una massa critica per rendere ragionevole la ricerca di un set di modifiche in una sola volta. Si noti che è pericoloso creare un ramo "tutto è consentito" senza dover eseguire la due diligence a causa delle risorse di progettazione limitate disponibili e del fatto che è necessario suddividere i test e la convalida tra questi due. Deve esserci uno scopo chiaro e una data di inizio e di fine ben comunicata di un ramo di questo tipo quando esiste.

## <a name="long-term-management-of-breaking-changes"></a>Gestione a lungo termine delle modifiche che causano un'interruzione

A lungo termine, è consigliabile ridurre l'ambito di una modifica che causa un'interruzione aumentando il set di condizioni [nell'elenco B.](#list-b) In futuro il set di elementi nell'elenco [A](#list-a) sarà sempre tecnicamente di rilievo per il set di file e asset che si ritiene essere nella "superficie dell'API pubblica". Il modo in cui è possibile ottenere un po' più di libertà per l'iterazione (ad esempio, la modifica dei dettagli di implementazione interna, consentendo un refactoring più semplice e la condivisione del codice tra più classi e così via) è quello di essere più espliciti su quali parti del codice sono superficie ufficiale, anziché dettagli di implementazione.

Una cosa che è già stata fatta è introdurre il concetto di funzionalità "sperimentale" (appartiene allo spazio dei nomi sperimentale, potrebbe non avere test/documentazione e può esistere pubblicamente, ma può essere rimossa e aggiornata senza avviso). Questo ha dato la libertà di aggiungere nuove funzionalità prima per ottenere commenti e suggerimenti precedenti, ma non essere immediatamente associati alla superficie api (perché potrebbe non essere stata pensata completamente la superficie dell'API).

### <a name="other-examples-of-things-that-could-help-in-the-future"></a>Altri esempi di elementi che potrebbero essere utili in futuro

- Utilizzo della parola [chiave interna](/dotnet/csharp/language-reference/keywords/internal).
  Ciò consentirebbe di avere codice condiviso all'interno dei propri assembly (per ridurre la duplicazione del codice) senza rendere pubbliche le informazioni agli utenti esterni.
- Creazione di uno spazio dei nomi "interno", ad esempio Microsoft.MixedReality.Toolkit. Internal.Utilities), in cui si documenta pubblicamente che qualsiasi elemento contenuto in tale spazio dei nomi interno è soggetto a modifiche in qualsiasi momento e potrebbe essere rimosso e così via. Questo è simile al modo in cui le librerie di intestazione C++ useranno gli spazi dei nomi ::internal per nascondere i dettagli di implementazione.

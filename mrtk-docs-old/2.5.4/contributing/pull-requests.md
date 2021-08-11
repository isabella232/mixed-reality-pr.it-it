---
title: Richieste pull
description: Dettagli relativi alle richieste pull.
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, richiesta pull,
ms.openlocfilehash: 0e2018236458a4f1df9945ac3bc243a733e20b869aeb5adf1d69c8628ef9467c
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115204381"
---
# <a name="pull-requests"></a>Richieste pull

## <a name="prerequisites"></a>Prerequisiti

Se non si è mai contribuito a un progetto Microsoft in precedenza, potrebbe essere richiesto di firmare un contratto di licenza [per i contributi.](https://cla.microsoft.com/)
Un commento nella richiesta pull consente di sapere se lo si desidera.

> [!IMPORTANT]
> I dipendenti Microsoft che non sono membri dell'organizzazione Microsoft in [GitHub](https://github.com/Microsoft)possono collegare gli account Microsoft e GitHub sulla rete virtuale visitando [Open Source](https://opensource.microsoft.com/) in Microsoft prima di iniziare la richiesta pull. Ci sono alcune cose da fare in anticipo.

## <a name="creating-a-pull-request"></a>Creazione di una richiesta pull

Quando si è pronti per inviare una richiesta pull, [creare una richiesta pull](https://github.com/microsoft/MixedRealityToolkit-Unity/compare/mrtk_development...mrtk_development?expand=1) per il ramo [mrtk_development](https://github.com/microsoft/mixedrealitytoolkit-unity/tree/mrtk_development) destinazione.

Leggere le linee guida e assicurarsi che la richiesta pull soddisfi le linee guida.

* Assicurarsi di fare riferimento a qualsiasi problema/richiesta di funzionalità o attività a cui è correlata la richiesta pull.
* Controllare che la richiesta pull contenga solo file/modifiche correlate alla richiesta pull.
* Controllare che la documentazione sia aggiornata e inclusa. Controllare che tutti i campi pubblici hanno commenti.
* Se si aggiunge una nuova funzionalità, verificare che i test siano inclusi per convalidare la funzionalità (vedere [UnitTests).](../contributing/unit-tests.md)
* Se si corregge un bug, scrivere un test per verificare la correzione di bug.

I revisori del progetto esaminano le modifiche. L'obiettivo è esaminare tutte le modifiche entro tre giorni lavorativi. Risolvere eventuali commenti di revisione, eseguire il push nel ramo dell'argomento e pubblicare un commento per informarci che ci sono nuovi commenti da rivedere.

> [!NOTE]
> Tutte le richieste pull inviate al progetto verranno esaminate anche in base alla guida agli standard di codifica [MRTK,](../contributing/coding-guidelines.md)quindi è necessario esaminarne le informazioni prima di inviare la richiesta pull per garantire un processo uniforme.

## <a name="pull-request-guidelines"></a>Linee guida per le richieste pull

Queste linee guida si basano sulle [procedure di progettazione di Google.](https://google.github.io/eng-practices/review/developer/small-cls.html)

### <a name="keep-pull-requests-small"></a>Mantenere piccole le richieste pull

Le PR più piccole vengono esaminate più rapidamente e accuratamente, hanno meno probabilità di introdurre bug, sono più facili da eseguire il rollback e più facili da unire.

Le richieste pull devono essere sufficientemente piccole da essere esaminate da un tecnico in meno di 30 minuti. Provare a apportare una modifica minima che indirizzi solo un elemento. Se è necessario creare una richiesta pull di grandi dimensioni, suddividerla in più richiesta pull che passano nel ramo locale o in un ramo di funzionalità di MRTK. Evitare di aggiungere nuovi asset (ad esempio file fbx, obj) e di usare di nuovo gli asset esistenti.

### <a name="tests-should-be-added-in-the-same-pr-as-your-fix--feature-except-for-emergencies"></a>I test devono essere aggiunti nella stessa richiesta pull della correzione o della funzionalità, ad eccezione delle emergenze

I test sono il modo migliore per garantire che le modifiche non regredino nel codice esistente, ma è anche facile dimenticare i test quando si inviano richieste pull. Richiedere l'intervento dell'utente con la richiesta pull è un ottimo modo per assicurarsi che i test siano scritti.

A ogni funzionalità e correzione di bug devono essere associati test. Se non si ha la competenza o il tempo necessario per scrivere un test, creare un problema per scrivere i test e contrassegnarli con l'etichetta Considera per **iterazione corrente**.

### <a name="documentation-should-be-added-in-the-same-pull-request-as-a-fix--feature"></a>La documentazione deve essere aggiunta nella stessa richiesta pull di una funzionalità/correzione

La maggior parte degli sviluppatori cerca prima di tutto la documentazione, non il codice, quando si comprende come usare una funzionalità. Assicurarsi che la documentazione sia aggiornata rende molto più semplice per gli utenti usare e usare MRTK.  La documentazione deve sempre essere in bundle con il pull correlato per garantire che gli elementi rimangano aggiornati e coerenti.

Assicurarsi che ogni campo pubblico, metodo e proprietà abbia commenti di riepilogo con barra tripla, in modo che il sito docfx possa generare descrizioni per campi/metodi. [](https://dotnet.github.io/docfx/spec/triple_slash_comments_spec.html) Se necessario, aggiornare i file markdown nella cartella Documentazione.

### <a name="pull-request-descriptions-should-clearly-and-completely-describe-changes"></a>Le descrizioni delle richieste pull devono descrivere in modo chiaro e completo le modifiche

Descrizioni chiare e complete delle richieste pull assicurano che i revisori comprendano ciò che stanno esaminando.

Se si aggiungono funzionalità che contengono l'esperienza utente, aggiungere un'immagine/gif della funzionalità che si sta modificando. [Di seguito è riportato un buon esempio.](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/4532) Un altro suggerimento è quello di avere una gif di Before e After, [ad esempio in questa richiesta pull.](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/5896) Uno strumento consigliato per la generazione di gif dalle acquisizioni di schermate [è ScreenToGif.](https://www.screentogif.com/)

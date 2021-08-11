---
title: Richieste pull
description: Dettagli relativi alle GitHub pull.
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, richiesta pull,
ms.openlocfilehash: ffaba25a42566d6e48be7db2c5b599443b24831f8f353fe1bd59beb062a7b87e
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115200115"
---
# <a name="pull-requests"></a>Richieste pull

## <a name="prerequisites"></a>Prerequisiti

Se in precedenza non hai contribuito a un progetto Microsoft, ti potrebbe essere richiesto di firmare un contratto di licenza [per contributi.](https://cla.microsoft.com/)
Un commento nella richiesta pull consente di sapere se si è in questo caso.

> [!IMPORTANT]
> Se si è un dipendente Microsoft e non si è membri dell'organizzazione [Microsoft in GitHub,](https://github.com/Microsoft)collegare gli account Microsoft e GitHub su corpnet visitando [Open Source](https://opensource.microsoft.com/) in Microsoft prima di avviare la richiesta pull. È necessario eseguire alcune fasi del processo in anticipo.

## <a name="creating-a-pull-request"></a>Creazione di una richiesta pull

Quando si è pronti per inviare una richiesta pull, [creare una richiesta pull](https://github.com/microsoft/MixedRealityToolkit-Unity/compare/main...main?expand=1) per il [ramo](https://github.com/microsoft/mixedrealitytoolkit-unity/tree/main) principale. Per le correzioni di bug durante un periodo di stabilizzazione della versione, cercare il ramo `prerelease/*` più recente. Le nuove funzionalità devono sempre essere disponibili in `main` .

Leggere le linee guida e assicurarsi che la richiesta pull soddisfi le linee guida.

* Assicurarsi di fare riferimento a qualsiasi richiesta di problema/funzionalità o attività a cui si riferisce la richiesta pull.
* Controllare che la richiesta pull contenga solo file/modifiche correlate alla richiesta pull.
* Verificare che la documentazione sia aggiornata e inclusa. Controllare che tutti i campi pubblici hanno commenti.
* Se si aggiunge una nuova funzionalità, verificare che i test siano inclusi per convalidare la funzionalità (vedere [UnitTests](../contributing/unit-tests.md)).
* Se si corregge un bug, scrivere un test per verificare la correzione del bug.

I mantenitori del progetto rivedranno le modifiche. L'obiettivo è esaminare tutte le modifiche entro tre giorni lavorativi. Risolvere eventuali commenti di revisione, eseguire il push nel ramo dell'argomento e pubblicare un commento che informa che sono disponibili nuovi commenti da esaminare.

> [!NOTE]
> Tutte le richieste pull inviate al progetto verranno anche esaminate in base alla guida agli standard di codifica [MRTK,](../contributing/coding-guidelines.md)quindi è necessario esaminarne le informazioni prima di inviare la richiesta pull per garantire un processo uniforme.

## <a name="pull-request-guidelines"></a>Linee guida per le richieste pull

Queste linee guida si basano sulle [procedure di progettazione di Google.](https://google.github.io/eng-practices/review/developer/small-cls.html)

### <a name="keep-pull-requests-small"></a>Mantenere piccole le richieste pull

Le PR più piccole vengono esaminate in modo più rapido e approfondito, hanno meno probabilità di introdurre bug, più facile da eseguire il rollback e più facili da unire.

Le richieste pull devono essere sufficientemente piccole da poter essere esaminate da un tecnico in meno di 30 minuti. Provare a apportare una modifica minima che indirizzi solo una cosa. Se è necessario creare una richiesta pull di grandi dimensioni, suddividerla in più PR che vanno nel ramo locale o in un ramo di funzionalità di MRTK. Evitare di aggiungere nuovi asset (ad esempio fbx, file obj) e invece di usare di nuovo gli asset esistenti.

### <a name="tests-should-be-added-in-the-same-pr-as-your-fix--feature-except-for-emergencies"></a>I test devono essere aggiunti nella stessa richiesta pull della correzione/funzionalità, ad eccezione delle emergenze

I test sono il modo migliore per garantire che le modifiche non regredino il codice esistente, ma è anche facile dimenticare i test quando si inviano richieste pull. Richiedere che i test esercitino la richiesta pull è un ottimo modo per garantire che i test siano scritti.

A ogni funzionalità e correzione di bug devono essere associati test. Se non si ha la competenza o il tempo necessario per scrivere un test, creare un problema per scrivere i test e contrassegnarli con l'etichetta Considera per **iterazione corrente**.

### <a name="documentation-should-be-added-in-the-same-pull-request-as-a-fix--feature"></a>La documentazione deve essere aggiunta nella stessa richiesta pull di una correzione/funzionalità

La maggior parte degli sviluppatori cerca prima di tutto la documentazione, non il codice, quando si comprende come usare una funzionalità. Assicurarsi che la documentazione sia aggiornata rende molto più semplice per gli utenti usare e affidarsi a MRTK.  La documentazione deve sempre essere in bundle con il pull correlato per garantire che gli elementi rimangano aggiornati e coerenti.

Assicurarsi che ogni campo pubblico, metodo, proprietà abbia commenti di riepilogo con tripla barra, in modo che il sito docfx possa generare descrizioni per campi/metodi. [](https://dotnet.github.io/docfx/spec/triple_slash_comments_spec.html) Se necessario, aggiornare i file markdown nella cartella Documentazione.

### <a name="pull-request-descriptions-should-clearly-and-completely-describe-changes"></a>Le descrizioni delle richieste pull devono descrivere in modo chiaro e completo le modifiche

Descrizioni chiare e complete delle richieste pull assicurano ai revisori di comprendere cosa stanno esaminando.

Se si aggiungono funzionalità che contengono l'esperienza utente, aggiungere un'immagine/gif della funzionalità che si sta modificando. [Di seguito è riportato un buon esempio.](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/4532) Un altro suggerimento è quello di avere una gif di Prima e Dopo, [ad esempio in questa richiesta pull.](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/5896) Uno strumento consigliato per la generazione di gif dalle acquisizioni di schermate è [ScreenToGif](https://www.screentogif.com/).

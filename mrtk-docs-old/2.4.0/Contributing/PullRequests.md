---
title: PullRequests
description: Dettagli relativi alle richieste pull.
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
ms.localizationpriority: medium
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, PR,
ms.openlocfilehash: 7cf276d32a008c2d8cf4c899b9de3d62ae370bd9
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2021
ms.locfileid: "104684364"
---
# <a name="pull-requests"></a>Richieste pull

## <a name="prerequisites"></a>Prerequisiti

Se non si è mai contribuito a un progetto Microsoft, è possibile che venga richiesto di firmare un [contratto di licenza](https://cla.microsoft.com/)per i contributi.
Un commento nella richiesta pull indica se si esegue questa operazione.

> [!IMPORTANT]
> Se sei un dipendente Microsoft e non sei membro dell' [organizzazione Microsoft su GitHub](https://github.com/Microsoft), collega gli account Microsoft e GitHub in corpnet visitando [Open Source presso Microsoft](https://opensource.microsoft.com/) prima di iniziare la richiesta pull. È necessario eseguire alcune operazioni in anticipo.

## <a name="creating-a-pull-request"></a>Creazione di una richiesta pull

Quando si è pronti per inviare una richiesta pull, [creare una richiesta pull](https://github.com/microsoft/MixedRealityToolkit-Unity/compare/mrtk_development...mrtk_development?expand=1) destinata al ramo [mrtk_development](https://github.com/microsoft/mixedrealitytoolkit-unity/tree/mrtk_development) .

Leggere le linee guida e assicurarsi che la richiesta pull soddisfi le linee guida.

* Assicurarsi di fare riferimento a qualsiasi richiesta di problema/funzionalità o a un'attività a cui si riferisce la richiesta pull.
* Verificare che la richiesta pull contenga solo file/modifiche correlati alla richiesta pull.
* Controllare che la documentazione sia aggiornata e inclusa. Selezionare tutti i campi pubblici con commenti.
* Se si aggiunge una nuova funzionalità, verificare che i test siano inclusi per convalidare la funzionalità (vedere [UnitTests](UnitTests.md)).
* Se si corregge un bug, scrivere un test per verificare la correzione di bug.

I gestori del progetto verificheranno le modifiche apportate. Si intende esaminare tutte le modifiche entro tre giorni lavorativi. Rivolgersi a eventuali commenti di revisione, effettuare il push al ramo dell'argomento e pubblicare un commento che informa che sono presenti nuovi elementi da rivedere.

> [!NOTE]
> Tutte le richieste pull inviate al progetto verranno anche esaminate in base alla [Guida agli standard di codifica di MRTK](CodingGuidelines.md), pertanto è necessario esaminarle prima di inviare la richiesta pull per garantire un processo uniforme.

## <a name="pull-request-guidelines"></a>Linee guida per richieste pull

Queste linee guida sono basate sulle [procedure di progettazione di Google](https://google.github.io/eng-practices/review/developer/small-cls.html).

### <a name="keep-pull-requests-small"></a>Mantieni dimensioni ridotte richieste pull

Le richieste pull più piccole vengono esaminate in modo più rapido e approfondito, è meno probabile che introducano bug, più facili da ripristinare e più semplici da unire.

Le richieste pull dovrebbero essere sufficientemente piccole da consentire a un tecnico di esaminarle in meno di 30 minuti. Provare a apportare una modifica minima che indirizzi solo una cosa. Se è necessario creare una richiesta pull di grandi dimensioni, suddividerla in diverse richieste pull che si trovino nel branch locale o in un branch di funzionalità di MRTK. Evitare di aggiungere nuovi asset (ad esempio, FBX, file obj) e di usare invece gli asset esistenti.

### <a name="tests-should-be-added-in-the-same-pr-as-your-fix--feature-except-for-emergencies"></a>I test devono essere aggiunti nella stessa richiesta pull della correzione/funzionalità, ad eccezione delle emergenze

I test rappresentano il modo migliore per garantire che le modifiche non regressionino il codice esistente, ma è anche facile dimenticare i test quando si inviano richieste pull. Richiedere l'uso della richiesta pull è un ottimo modo per assicurarsi che i test vengano scritti.

A ogni funzionalità e correzione di bug devono essere associati test. Se non si ha la competenza o il tempo per scrivere un test, creare un problema per scrivere i test e contrassegnarli con l'etichetta **considera per l'iterazione corrente**.

### <a name="documentation-should-be-added-in-the-same-pull-request-as-a-fix--feature"></a>La documentazione deve essere aggiunta nella stessa richiesta pull di una correzione/funzionalità

La maggior parte degli sviluppatori esamina prima di tutto la documentazione, non il codice, quando si comprende come usare una funzionalità. Garantire che la documentazione sia aggiornata rende molto più semplice per gli utenti utilizzare e utilizzare MRTK.  Per garantire che gli elementi rimangano aggiornati e coerenti, la documentazione deve sempre essere inclusa nel pull correlato.

Verificare che ogni proprietà di campo pubblico, metodo, abbia [commenti di riepilogo barra tripla](https://dotnet.github.io/docfx/spec/triple_slash_comments_spec.html) , in modo che il sito docfx possa generare descrizioni per i campi o i metodi. Se necessario, aggiornare i file Markdown nella cartella della documentazione.

### <a name="pull-request-descriptions-should-clearly-and-completely-describe-changes"></a>Le descrizioni delle richieste pull devono descrivere in modo chiaro e completo le modifiche

Le descrizioni chiare e complete delle richieste pull assicurano che i revisori conoscano le informazioni che stanno esaminando.

Se si aggiungono funzionalità che contengono UX, aggiungere un'immagine o un gif della funzionalità in corso di modifica. [Ecco un esempio valido](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/4532). Un altro suggerimento è avere un gif di before e After, [ad esempio in questa richiesta pull](https://github.com/microsoft/MixedRealityToolkit-Unity/pull/5896). Uno strumento consigliato per la generazione di gif da screenshot è [ScreenToGif](https://www.screentogif.com/).

---
title: Roadmap
description: documentazione per la struttura della roadmap di MRTK.
author: polar-kev
ms.author: kesemple
ms.date: 03/03/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK
ms.openlocfilehash: 53cf7ffe786ea5cb650bfd04ff8d42d5bdd7cf09
ms.sourcegitcommit: 7a8fa3257a13635ddad77d963e49440f62c19774
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/04/2021
ms.locfileid: "101883126"
---
# <a name="roadmap"></a>Roadmap

Questo documento descrive la roadmap del Toolkit di realtà mista. Si noti che di seguito sono riportate le stime dei lavori nelle date di sviluppo e di destinazione.

## <a name="current-release"></a>Versione corrente

Microsoft Mixed Reality Toolkit v 2.6

## <a name="upcoming-releases"></a>Prossime versioni

| Prodotto | Descrizione | Sequenza temporale | Lavagna del progetto |
| --- | --- | --- | --- |
| [MRTK V 2.7](#270) | Iterazione successiva di MRTK | Maggio 2021 | https://github.com/microsoft/MixedRealityToolkit-Unity/milestone/14 |

Le versioni sono incentrate sui temi (ad esempio, aree funzionali di grandi dimensioni) e sono pianificati per essere eseguiti approssimativamente ogni 8-12 settimane.

I dettagli della versione, inclusi gli elementi di backlog, sono reperibili nelle [pagine dell'attività cardine di GitHub](https://github.com/Microsoft/MixedRealityToolkit-Unity/milestones). Il set completo di problemi aperti è disponibile anche in [GitHub](https://github.com/microsoft/MixedRealityToolkit-Unity/issues).

## <a name="mixed-reality-toolkit-mrtk-roadmap"></a>Guida di orientamento a Mixed Reality Toolkit (MRTK)

Il Toolkit per la realtà mista è progettato per essere cross MR/AR/VR/XR Platform by Design. Il Toolkit supporta attualmente Unity 2019.4. x e Unity 2018.4. x.

> Quando Unity rilascia un prodotto LTS (supporto a lungo termine), il Toolkit di realtà mista viene aggiornato alla versione LTS. Sebbene il Toolkit di realtà mista venga eseguito nella versione più recente del ramo Tech non beta (ad esempio, 2020,1), non è ufficialmente supportato.

### <a name="270"></a>2.7.0

Attualmente stiamo pianificando la versione 2.7.0 e avrai a disposizione più aggiornamenti.
Per lo stato più recente della versione, visitare la pagina relativa all' [attività cardine](https://github.com/microsoft/MixedRealityToolkit-Unity/milestone/14).

Stato: pianificazione

Sequenza temporale di destinazione: 2021 maggio

Temi:

- Stability 
- Espansione della piattaforma: OpenXR
- Esperienza dell'utente
- Formazione per sviluppatori
- Packaging

**Stabilità**

La qualità e la stabilità sono la massima priorità per questo e tutte le versioni di Microsoft Mixed Reality Toolkit. Si continuerà ad assegnare una priorità ai problemi dei clienti e dei partner che influiscano sulla stabilità dei componenti di MRTK.

**Espansione della piattaforma: OpenXR**

Il team di MRTK supporta il futuro aperto della realtà mista tramite [OpenXR](https://techcommunity.microsoft.com/t5/mixed-reality-blog/moving-forward-to-openxr/ba-p/1825672). Il supporto per OpenXR è attualmente in fase di sviluppo, con supporto di anteprima iniziale rilasciato in MRTK 2.5.2.

**Esperienza utente**

Stiamo ascoltando i tuoi commenti e suggerimenti su MRTK e abbiamo continuato a pianificare:

- Correzioni di bug
- Semplificazione della comprensione per i controlli UX MRTK
- Parità della shell HoloLens
- Test per garantire che le funzionalità non regressione

**Formazione per sviluppatori**

È stata eseguita la migrazione della documentazione per gli sviluppatori da GitHub a una nuova piattaforma docs. Microsoft vuole ricevere commenti e suggerimenti per poter continuare a migliorare l'esperienza di documentazione per gli sviluppatori.
Attualmente sono disponibili [esercitazioni di MRTK](https://docs.microsoft.com/windows/mixed-reality/develop/unity/tutorials) che si trovano in una sezione diversa di docs realtà mista. Queste esercitazioni verranno migrate per vivere con il resto della documentazione di MRTK. 

**Packaging**

Lo [strumento per la funzionalità di realtà mista](https://docs.microsoft.com/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool) è un nuovo modo per gli sviluppatori di individuare, aggiornare e aggiungere pacchetti di funzionalità di realtà mista in progetti Unity. È possibile cercare i pacchetti in base al nome o alla categoria, visualizzarne le dipendenze e persino visualizzare le modifiche proposte al file manifesto del progetto prima dell'importazione. Si prevede di apportare aggiornamenti allo strumento per le funzionalità di realtà mista quando si rispondono alle richieste di funzionalità e ai bug.

## <a name="backlog"></a>Backlog

Nell'elenco seguente sono illustrati alcuni degli investimenti principali che il team di MRTK intende adottare.

- Espansione della piattaforma
- Estendibilità
- Modularità
- Funzionalità di accesso facilitato
- Miglioramenti della globalizzazione
- Supporto del servizio cloud
- Strumenti

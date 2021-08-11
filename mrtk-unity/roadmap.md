---
title: Roadmap
description: documentazione per la struttura della roadmap di MRTK.
author: polar-kev
ms.author: kesemple
ms.date: 03/03/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK
ms.openlocfilehash: b591d3ed7bd3c470bdf5b9598864f35963fb99a9957c5ceefdd1417372a3b97e
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115203233"
---
# <a name="roadmap"></a>Roadmap

Questo documento illustra la roadmap del modello di realtà mista Toolkit. Si noti che quanto segue riflette il lavoro in fase di sviluppo e le date di destinazione riflettono le stime.

## <a name="current-release"></a>Versione corrente

Microsoft Mixed Reality Toolkit v2.6

## <a name="upcoming-releases"></a>Versioni future

| Prodotto | Descrizione | Sequenza temporale | Project scheda |
| --- | --- | --- | --- |
| [MRTK V2.7](#270) | Iterazione successiva di MRTK | Maggio 2021 | https://github.com/microsoft/MixedRealityToolkit-Unity/milestone/14 |

Le versioni sono centrate sui temi (ad esempio aree di funzionalità di grandi dimensioni) e sono pianificate per essere eseguite circa ogni 8-12 settimane.

I dettagli sulla versione, inclusi gli elementi di backlog, sono disponibili nelle pagine delle attività [cardine GitHub attività cardine.](https://github.com/Microsoft/MixedRealityToolkit-Unity/milestones) Il set completo di problemi aperti è disponibile anche in [GitHub](https://github.com/microsoft/MixedRealityToolkit-Unity/issues).

## <a name="mixed-reality-toolkit-mrtk-roadmap"></a>Guida di orientamento Toolkit realtà mista (MRTK)

L'Toolkit di realtà mista è progettato per essere multipiattaforma MR/AR/VR/XR. Il toolkit attualmente supporta Unity 2019.4.x e Unity 2018.4.x.

> Quando Unity rilascia un prodotto LTS (Supporto a lungo termine), l'Toolkit realtà mista verrà aggiornato alla versione LTS. Anche se l'Toolkit mixed reality viene eseguito nella versione tech branch più recente non beta (ad esempio, 2020.1) di Unity, non è ufficialmente supportata.

### <a name="270"></a>2.7.0

È in corso la pianificazione della versione 2.7.0 e presto saranno disponibili altri aggiornamenti.
Per lo stato più recente della versione, visitare la pagina [attività cardine](https://github.com/microsoft/MixedRealityToolkit-Unity/milestone/14).

Stato: Pianificazione

Sequenza temporale di destinazione: maggio 2021

Temi:

- Stability 
- Espansione della piattaforma: OpenXR
- Esperienza dell'utente
- Formazione per sviluppatori
- Packaging

**Stabilità**

La qualità e la stabilità sono la priorità principale per questa e tutte le versioni di Microsoft Mixed Reality Toolkit versioni. Microsoft continuerà a classificare in ordine di priorità i problemi relativi a clienti e partner che influiscono sulla stabilità dei componenti MRTK.

**Espansione della piattaforma: OpenXR**

Il team MRTK supporta il futuro aperto della realtà mista tramite [OpenXR.](https://techcommunity.microsoft.com/t5/mixed-reality-blog/moving-forward-to-openxr/ba-p/1825672) Il supporto per OpenXR è attualmente in fase di sviluppo, con il supporto dell'anteprima iniziale rilasciato in MRTK 2.5.2.

**Esperienza utente**

Stiamo ascoltando i commenti e suggerimenti su MRTK e sono stati continuati i piani per:

- Correzioni di bug
- Semplificare la comprensione dei controlli dell'esperienza utente MRTK
- HoloLens Parità della shell
- Test per garantire che le funzionalità non regredino

**Formazione per sviluppatori**

È stata eseguita la migrazione della documentazione per sviluppatori da GitHub a una nuova piattaforma di documentazione. Microsoft vuole ricevere commenti e suggerimenti in modo da poter continuare a migliorare l'esperienza della documentazione per gli sviluppatori.
Attualmente sono disponibili [esercitazioni su MRTK](/windows/mixed-reality/develop/unity/tutorials) disponibili in un'altra sezione della documentazione sulla realtà mista. Verrà eseguita la migrazione di queste esercitazioni per l'esecuzione del resto della documentazione di MRTK. 

**Packaging**

[Lo strumento funzionalità realtà mista](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool) è un nuovo modo per consentire agli sviluppatori di individuare, aggiornare e aggiungere pacchetti di funzionalità di realtà mista nei progetti Unity. È possibile cercare i pacchetti in base al nome o alla categoria, visualizzarne le dipendenze e persino visualizzare le modifiche proposte al file manifesto del progetto prima dell'importazione. Microsoft intende apportare aggiornamenti a Mixed Reality Feature Tool in risposta alle richieste di funzionalità e ai bug.

## <a name="backlog"></a>Backlog

L'elenco seguente evidenzia alcuni degli investimenti chiave che il team di MRTK intende intraprendere.

- Espansione della piattaforma
- Estendibilità
- Modularità
- Funzionalità di accessibilità
- Miglioramenti della globalizzazione
- Supporto del servizio cloud
- Strumenti

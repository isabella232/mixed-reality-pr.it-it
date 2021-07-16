---
title: Contribuire a MRTK
description: Come contribuire alla realtà mista Toolkit
author: polar-kev
ms.author: kesemple
ms.date: 03/17/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, report sui bug,
ms.openlocfilehash: b79f69cbb6dea1201c88d9fd1a354967ce40735e
ms.sourcegitcommit: 912fa204ef79e9b973eab9b862846ba5ed5cd69f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/16/2021
ms.locfileid: "114282041"
---
# <a name="contributing-to-mrtk"></a>Contribuire a MRTK

The Mixed Reality Toolkit (MRTK) accolta con favore i contributi della community. Tutte le modifiche siano piccole o grandi, devono rispettare gli standard di codifica [MRTK,](coding-guidelines.md)quindi assicurarsi di avere familiarità con queste modifiche durante lo sviluppo per evitare ritardi durante la revisione della modifica.

In caso di domande, contattare il canale [mixed-reality-toolkit in Slack.](https://holodevelopers.slack.com/messages/C2H4HT858)
È possibile partecipare alla community di Slack tramite il [mittente dell'invito automatico.](https://holodevelopersslack.azurewebsites.net/)

## <a name="submission-process"></a>Processo di invio

Sono disponibili diversi percorsi per consentire agli sviluppatori di contribuire alla Toolkit di realtà mista, il tutto a partire dalla creazione [di un nuovo problema](https://github.com/Microsoft/MixedRealityToolkit-Unity/issues/new/choose).

<img src="../features/images/contributing/SelectIssueType.png" width="600" alt="Select Issue Type">

Da qui si file:

- **Segnalazione di bug-** Problema di funzionalità con uno dei componenti Toolkit realtà mista
- **Problema relativo alla** documentazione - Problema con la documentazione Toolkit [realtà mista](https://microsoft.github.io/MixedRealityToolkit-Unity)
- **Richiesta di funzionalità:** proposta per una nuova funzionalità Toolkit realtà mista

## <a name="proposing-feature-requests"></a>Proposta di richieste di funzionalità

Quando si richiede una nuova funzionalità Toolkit realtà mista, è importante documentare il vantaggio/problema del cliente da risolvere. Dopo l'invio, una richiesta di funzionalità verrà esaminata e discussa in GitHub. Si consiglia una discussione aperta e costruttiva su ogni proposta di funzionalità per garantire che il lavoro sia vantaggioso per un ampio segmento di clienti.

Per evitare di dover rielaborare la funzionalità, è in genere consigliabile che lo sviluppo della funzionalità non inizi durante la fase di revisione. Molte volte, il processo di revisione della community individua uno o più problemi che possono richiedere modifiche significative nell'implementazione proposta.

> [!NOTE]
> Se si vuole lavorare su un elemento già esistente nel backlog, è possibile usare tale elemento di lavoro come proposta. Assicurarsi anche di impostare come commento l'attività che notifica ai mantenitori che si sta lavorando per completarla.

## <a name="contribution-process"></a>Processo di contribuzione

Per iniziare, è sufficiente seguire questa procedura:

1. Creare il fork del repository. Fare clic sul pulsante "Fork" in alto a destra nella pagina e seguire il flusso.
1. Creare un ramo nel fork (al di fuori del [ramo principale)](https://github.com/microsoft/mixedrealitytoolkit-unity/tree/main) per semplificare l'isolamento delle modifiche fino a quando non si è pronti per l'invio. Per le correzioni di bug durante un periodo di stabilizzazione della versione, cercare il ramo `prerelease/*` più recente. Le nuove funzionalità devono sempre essere disponibili in `main` .

Se non si ha una nuova versione del flusso di lavoro Git, [vedere questa introduzione da GitHub.](https://guides.github.com/activities/hello-world/)

Quando si aggiunge una funzionalità o una correzione di bug, seguire questa procedura:

1. Implementare la funzionalità o la correzione di bug. Le istruzioni per la compilazione e la distribuzione di MRTK sono disponibili in [Deploying to Hololens and WMR devices (Distribuzione in dispositivi Hololens e WMR).](../supported-devices/wmr-mrtk.md) Ricordarsi di seguire le [linee guida per la codifica](../contributing/coding-guidelines.md).
1. Se si aggiunge una funzionalità, aggiungere anche una scena di esempio che ne illustra la funzionalità.
1. Se si aggiunge una funzionalità sperimentale, la scrittura di test e documentazione non è necessaria. Seguire invece le linee [guida per le funzionalità sperimentali.](../contributing/experimental-features.md)
1. Aggiungere test per verificare la funzionalità o la correzione di bug. Le istruzioni per la scrittura e l'esecuzione di test sono disponibili in [UnitTests](../contributing/unit-tests.md).
1. Assicurarsi che il codice e le funzionalità siano documentati come descritto nelle linee guida [della documentazione](../contributing/documentation-guide.md).
1. Assicurarsi che il codice funzioni come previsto in tutte le piattaforme. Per [l'elenco delle](../release-notes/mrtk-26-release-notes.md) piattaforme supportate, vedere Note sulla versione. Per Windows progetti UWP, il codice deve essere [conforme a WACK.](https://developer.microsoft.com/windows/develop/app-certification-kit) A tale scopo, generare una soluzione Visual Studio, fare clic con il pulsante destro del mouse sul progetto. **Archiviare**  >  **Creare pacchetti dell'app**. Seguire le richieste ed eseguire i test WACK. Assicurarsi che tutti riescano.
1. Quando si effettua una [richiesta pull,](../contributing/pull-requests.md) seguire le istruzioni riportate in Richieste pull.

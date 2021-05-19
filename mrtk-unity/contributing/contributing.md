---
title: Contribuire a MRTK
description: Come contribuire a Mixed Reality Toolkit
author: polar-kev
ms.author: kesemple
ms.date: 03/17/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, report sui bug,
ms.openlocfilehash: 8132c39a2bac7ae0926f125a6362e411100c8406
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144512"
---
# <a name="contributing"></a>Contributo

Mixed Reality Toolkit (MRTK) è il benvenuto ai contributi della community. Tutte le modifiche, di piccole o grandi dimensioni, devono essere conformi agli standard di codifica [MRTK,](coding-guidelines.md)quindi assicurarsi di avere familiarità con queste modifiche durante lo sviluppo per evitare ritardi durante la revisione della modifica.

In caso di domande, contattare il canale [mixed-reality-toolkit su Slack.](https://holodevelopers.slack.com/messages/C2H4HT858)
È possibile partecipare alla community di Slack tramite il [mittente dell'invito automatico](https://holodevelopersslack.azurewebsites.net/).

## <a name="submission-process"></a>Processo di invio

Sono disponibili diversi percorsi per consentire agli sviluppatori di contribuire a Mixed Reality Toolkit, il tutto a partire [dalla creazione di un nuovo problema.](https://github.com/Microsoft/MixedRealityToolkit-Unity/issues/new/choose)

<img src="../features/images/contributing/SelectIssueType.png" width="600" alt="Select Issue Type">

Da qui è possibile file:

- **Report sui bug:** problema di funzionalità con uno dei componenti di Mixed Reality Toolkit
- **Problema della documentazione** - Problema con la documentazione di Mixed Reality [Toolkit](https://microsoft.github.io/MixedRealityToolkit-Unity)
- **Richiesta di funzionalità:** proposta per una nuova funzionalità di Mixed Reality Toolkit

## <a name="proposing-feature-requests"></a>Richieste di funzionalità di richiesta

Quando si richiede una nuova funzionalità di Mixed Reality Toolkit, è importante documentare il vantaggio/problema da risolvere per i clienti. Una volta inviata, una richiesta di funzionalità verrà esaminata e discussa in GitHub. Si consiglia di discutere apertamente e concisa di ogni proposta di funzionalità per garantire che il lavoro sia vantaggioso per un ampio segmento di clienti.

Per evitare di dover rielaborare la funzionalità, è in genere consigliabile che lo sviluppo della funzionalità non inizi durante la fase di revisione. In molti casi, il processo di revisione della community individua uno o più problemi che potrebbero richiedere modifiche significative nell'implementazione proposta.

> [!NOTE]
> Se si vuole lavorare su un elemento già esistente nel backlog, è possibile usare tale elemento di lavoro come proposta. Assicurarsi anche di commentare l'attività notificando ai maintainer che si sta lavorando per completarla.

## <a name="contribution-process"></a>Processo di contributo

Per iniziare, è sufficiente seguire questa procedura:

1. Creare una fork del repository. Fare clic sul pulsante "Fork" in alto a destra nella pagina e seguire il flusso.
1. Creare un ramo nel fork (fuori dal [ramo](https://github.com/microsoft/mixedrealitytoolkit-unity/tree/main) principale) per semplificare l'isolamento delle modifiche fino a quando non è pronto per l'invio. Per le correzioni di bug durante un periodo di stabilizzazione del rilascio, cercare il ramo più `prerelease/*` recente. Le nuove funzionalità devono sempre essere disponibili in `main` .

Se non si ha di nuovo il flusso di lavoro Git, [vedere questa introduzione da GitHub.](https://guides.github.com/activities/hello-world/)

Quando si aggiunge una funzionalità o una correzione di bug, seguire questa procedura:

1. Implementare la funzionalità o la correzione di bug. Le istruzioni per la compilazione e la distribuzione di MRTK sono disponibili in [Deploying to Hololens and WMR devices (Distribuzione in dispositivi Hololens e WMR).](../supported-devices/wmr-mrtk.md) Ricordarsi di seguire le [linee guida per la scrittura del codice.](../contributing/coding-guidelines.md)
1. Se si aggiunge una funzionalità, aggiungere anche una scena di esempio che illustra la funzionalità.
1. Se si aggiunge una funzionalità sperimentale, la scrittura di test e documentazione non è necessaria. Seguire invece le linee [guida per le funzionalità sperimentali.](../contributing/experimental-features.md)
1. Aggiungere test per verificare la funzionalità o la correzione di bug. Le istruzioni per la scrittura e l'esecuzione di test sono [disponibili in UnitTests.](../contributing/unit-tests.md)
1. Assicurarsi che il codice e le funzionalità siano documentati come descritto in Linee guida [per la documentazione.](../contributing/documentation-guide.md)
1. Verificare che il codice funzioni come previsto in tutte le piattaforme. Per [l'elenco delle](../release-notes/mrtk-26-release-notes.md) piattaforme supportate, vedere Note sulla versione. Per i progetti UWP di Windows, il codice deve essere [conforme a WACK.](https://developer.microsoft.com/windows/develop/app-certification-kit) A tale scopo, generare una soluzione Visual Studio, fare clic con il pulsante destro del mouse sul progetto. **Store**  >  **Creare pacchetti dell'app**. Seguire le istruzioni ed eseguire i test WACK. Assicurarsi che tutti gli elementi riescano.
1. Seguire le istruzioni in [Richieste pull quando](../contributing/pull-requests.md) si effettua una richiesta pull.

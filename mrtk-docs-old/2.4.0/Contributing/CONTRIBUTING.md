---
title: PARTECIPANTI
description: Community che contribuisce a MRTK.
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
ms.localizationpriority: medium
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, report sui bug,
ms.openlocfilehash: 45a4919cfdefc15dc32a6a0db0a4d83a7da51bcf
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2021
ms.locfileid: "104684444"
---
# <a name="contributing"></a>Contributo

Il Toolkit di realtà mista (MRTK) accoglie i contributi della community. Tutte le modifiche sono piccole o grandi, devono rispettare gli [standard di codifica MRTK](CodingGuidelines.md), quindi assicurarsi di avere familiarità con questi ultimi durante lo sviluppo per evitare ritardi durante la revisione della modifica.

Per eventuali domande, contattare il [canale Mixed-Reality-Toolkit in slack](https://holodevelopers.slack.com/messages/C2H4HT858).
È possibile partecipare alla community di Slack tramite il [mittente dell'invito automatico](https://holodevelopersslack.azurewebsites.net/).

## <a name="submission-process"></a>Processo di invio

Sono disponibili diversi percorsi per consentire agli sviluppatori di contribuire al Toolkit di realtà mista, che inizia con la [creazione di un nuovo problema](https://github.com/Microsoft/MixedRealityToolkit-Unity/issues/new/choose).

<img src="../features/Images/Contributing/SelectIssueType.png" width="600" alt="Submission process">

Da qui è possibile file:

- **Segnalazione di bug** : problema di funzionalità con uno dei componenti del Toolkit di realtà mista
- **Problema di documentazione** -problema con la [documentazione](https://microsoft.github.io/MixedRealityToolkit-Unity) di Mixed Reality Toolkit
- **Richiesta di funzionalità** : proposta per una nuova funzionalità del Toolkit per realtà mista

## <a name="proposing-feature-requests"></a>Proposte richieste di funzionalità

Quando si richiede una nuova funzionalità di Toolkit per realtà mista, è importante documentare il vantaggio del cliente o il problema da risolvere. Una volta inviata, una richiesta di funzionalità verrà esaminata e discussa in GitHub. Invitiamo la discussione aperta e costruttiva di ogni proposta di funzionalità per garantire che il lavoro sia vantaggioso per un segmento elevato di clienti.

Per evitare di dover rielaborare la funzionalità, è in genere consigliabile che lo sviluppo della funzionalità non venga avviato durante la fase di revisione. Spesso il processo di revisione della community individua uno o più problemi che potrebbero richiedere modifiche significative nell'implementazione proposta.

> [!NOTE]
> Se si desidera lavorare su un elemento già esistente nel backlog, è possibile utilizzare tale elemento di lavoro come proposta. Assicurarsi anche di commentare i gestori che inviano notifiche all'attività che si sta lavorando per il completamento.

## <a name="contribution-process"></a>Processo di contributo

Per iniziare, è sufficiente seguire questa procedura:

1. Creare una copia tramite fork del repository. Fai clic sul pulsante "fork" nella parte superiore destra della pagina e segui il flusso.
1. Creare un ramo nel fork (all'esterno del ramo [mrtk_development](https://github.com/microsoft/mixedrealitytoolkit-unity/tree/mrtk_development) ) per semplificare l'isolamento delle modifiche fino a quando non sono pronte per l'invio. Per la HoloToolkit legacy usare il ramo [htk_development](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_development) .

Se non si ha familiarità con il flusso di lavoro git, [vedere questa introduzione da GitHub](https://guides.github.com/activities/hello-world/).

Quando si aggiunge una correzione di bug o una funzionalità, attenersi alla seguente procedura:

1. Implementare la correzione o la funzionalità di bug. Le istruzioni per la compilazione e la distribuzione di MRTK sono disponibili in [BuildAndDeploy](../updates-deployment/BuildAndDeploy.md). Ricordarsi di seguire le [linee guida](../Contributing/CodingGuidelines.md)per la codifica.
1. Se si aggiunge una funzionalità, aggiungere anche una scena di esempio in cui viene illustrata la funzionalità.
1. Se si aggiunge una funzionalità sperimentale, non è necessario scrivere test e documentazione. Seguire invece le [linee guida per le funzionalità sperimentali](ExperimentalFeatures.md).
1. Aggiungere i test per verificare la correzione di bug/funzionalità. Le istruzioni per la scrittura e l'esecuzione di test si trovano in [UnitTests](UnitTests.md).
1. Verificare che il codice e le funzionalità siano documentati come descritto nelle [linee guida della documentazione](DocumentationGuide.md).
1. Verificare che il codice funzioni come previsto in tutte le piattaforme. Per l'elenco delle piattaforme supportate, vedere le [Note sulla versione](../packages-releases/ReleaseNotes.md) . Per i progetti UWP Windows, il codice deve essere [conforme](https://developer.microsoft.com/windows/develop/app-certification-kit). A tale scopo, generare una soluzione di Visual Studio, fare clic con il pulsante destro del mouse su progetto; **Archivio**  >  di **Creare pacchetti dell'applicazione**. Seguire le istruzioni ed eseguire i test. Assicurarsi che tutti abbiano esito positivo.
1. Seguire le istruzioni in [richieste pull](PullRequests.md) quando si effettua una richiesta pull.

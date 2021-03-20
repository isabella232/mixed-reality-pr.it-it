---
title: Importazione di funzionalità
description: Informazioni su come importare e installare le funzionalità dallo strumento di funzionalità di MR per lo sviluppo di HoloLens e VR.
author: davidkline-ms
ms.author: v-hferrone
ms.date: 03/04/2021
ms.topic: article
ms.localizationpriority: high
keywords: aggiornamento, strumenti, attività iniziali, nozioni di base, unity, visual studio, toolkit, visore VR realtà mista, visore VR di windows mixed reality, visore per realtà virtuale, installazione, Windows, HoloLens, emulatore, unreal, openxr
ms.openlocfilehash: 0d9139835b9eb4e3e5ce3d1f378c56a4724bfa55
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2021
ms.locfileid: "102230819"
---
# <a name="importing-features"></a>Importazione di funzionalità

Una volta scaricate, le funzionalità possono essere esaminate e importate nel progetto Unity. In questo passaggio la finestra dell'applicazione dovrebbe essere simile all'immagine seguente:

![Importazione di funzionalità](images/FeatureToolImport.png)

## <a name="features-list"></a>Elenco di funzionalità

L'elenco delle **funzionalità** contiene la raccolta di pacchetti selezionati durante l'individuazione. È possibile selezionare o deselezionare ogni funzionalità prima dell'importazione. I dettagli del pacchetto possono essere visualizzati usando il collegamento **Dettagli** riportato di seguito

![Elenco di funzionalità](images/FeaturesList.png)

## <a name="required-dependencies-list"></a>Elenco dipendenze obbligatorie

L'elenco **dipendenze necessarie** contiene i pacchetti necessari per il funzionamento di una o più delle funzionalità selezionate. Questo elenco conterrà anche le dipendenze delle dipendenze. Ogni dipendenza può essere selezionata o deselezionata prima dell'importazione. I dettagli del pacchetto possono essere visualizzati usando il collegamento **Dettagli** riportato di seguito

![Elenco dipendenze](images/RequiredDependencyList.png)

> [!NOTE]
> La deselezione delle dipendenze richieste genererà uno o più errori di dipendenza mancanti durante il caricamento del progetto in Unity. Queste funzionalità non saranno utilizzabili nel progetto.

## <a name="validating-selections"></a>Convalida di selezioni

Si consiglia vivamente di convalidare le selezioni delle funzionalità prima dell'importazione. Questo passaggio solleverà eventuali problemi che potrebbero impedire la riuscita dello sviluppo del progetto.

![Problemi di convalida](images/ValidationIssues.png)

Lo strumento per la funzionalità di realtà mista fornisce due risoluzioni automatiche di problemi, descritte nelle sezioni seguenti, e l'opzione per annullare e risolvere i problemi manualmente.

### <a name="enable-dependencies"></a>Abilita dipendenze

Il pulsante **Abilita dipendenze** selezionerà automaticamente le dipendenze mancanti. Questo vale per le dipendenze che sono state selezionate in modo esplicito (visualizzate nell'elenco delle **funzionalità** ) e quelle che sono state selezionate in modo implicito in base ai requisiti delle funzionalità selezionate.

### <a name="disable-features"></a>Disabilitare le funzionalità

Selezionando **Disabilita funzionalità** verrà automaticamente deselezionata una funzionalità che dipende da una o più dipendenze deselezionate. Questo vale per i pacchetti di dipendenza selezionati in modo implicito e le funzionalità selezionate in modo esplicito.

## <a name="importing"></a>Importazione

Selezionare **Importa** per aggiungere le funzionalità selezionate e fornire l' [approvazione finale](reviewing-changes.md) prima di aggiornare il progetto di destinazione.

> [!IMPORTANT]
> Se si verifica un problema di convalida durante l'importazione, verrà visualizzato un messaggio di avviso. È consigliabile selezionare No, fare clic su **convalida** e risolvere i problemi presentati.
>
> ![Continua con i problemi di convalida](images/ValidationContinueAnyway.png)

## <a name="going-back-to-the-previous-step"></a>Tornando al passaggio precedente

Dalle **funzionalità di importazione**, lo strumento della funzionalità di realtà mista consente di tornare all' [individuazione](discovering-features.md). Selezionare **Torna indietro** per scaricare altri pacchetti di funzionalità.

## <a name="see-also"></a>Vedi anche

- [Strumento per la funzionalità di realtà mista](welcome-to-mr-feature-tool.md)
- [Individuazione e acquisizione](discovering-features.md)
- [Visualizzazione dei dettagli del pacchetto di funzionalità](viewing-package-details.md)
- [Revisione e approvazione delle modifiche del progetto](reviewing-changes.md)
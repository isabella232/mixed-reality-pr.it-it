---
title: Importazione di funzionalità
description: Informazioni su come importare e installare le funzionalità da MR Feature Tool per lo HoloLens e la realtà virtuale.
author: davidkline-ms
ms.author: v-hferrone
ms.date: 03/04/2021
ms.topic: article
ms.localizationpriority: high
keywords: aggiornamento, strumenti, attività iniziali, nozioni di base, unity, visual studio, toolkit, visore VR realtà mista, visore VR di windows mixed reality, visore per realtà virtuale, installazione, Windows, HoloLens, emulatore, unreal, openxr
ms.openlocfilehash: 6cf3712ce8029695076ceaec4191df53eb72789c62568206c056f1afc6c04c3b
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115225789"
---
# <a name="importing-features"></a>Importazione di funzionalità

Una volta scaricate, le funzionalità possono essere esaminate e importate nel progetto Unity. In questo passaggio la finestra dell'applicazione dovrebbe essere simile all'immagine seguente:

![Importazione di funzionalità](images/FeatureToolImport.png)

## <a name="features-list"></a>Elenco di funzionalità

**L'elenco** Funzionalità contiene la raccolta di pacchetti selezionati durante l'individuazione. Ogni funzionalità può essere selezionata o deselezionata prima dell'importazione. I dettagli del pacchetto possono essere visualizzati usando il **collegamento Dettagli** illustrato di seguito

![Elenco di funzionalità](images/FeaturesList.png)

## <a name="required-dependencies-list"></a>Elenco delle dipendenze necessarie

**L'elenco Dipendenze** necessarie contiene i pacchetti necessari per il funzionamento di una o più funzionalità selezionate. Questo elenco conterrà anche le dipendenze delle dipendenze. Ogni dipendenza può essere selezionata o deselezionata prima dell'importazione. I dettagli del pacchetto possono essere visualizzati usando il **collegamento Dettagli** illustrato di seguito

![Elenco delle dipendenze](images/RequiredDependencyList.png)

> [!NOTE]
> Se si deselezionano le dipendenze necessarie, si verificano uno o più errori di dipendenza mancanti durante il caricamento del progetto in Unity. Queste funzionalità non saranno utilizzabili nel progetto.

## <a name="validating-selections"></a>Convalida delle selezioni

È consigliabile convalidare le selezioni di funzionalità prima dell'importazione. Questo passaggio genererà eventuali problemi che potrebbero ostacolare il successo dello sviluppo del progetto.

![Problemi di convalida](images/ValidationIssues.png)

Lo strumento per le funzionalità di realtà mista offre due risoluzioni automatiche dei problemi, descritte nelle sezioni seguenti, e l'opzione per annullare e risolvere i problemi manualmente.

### <a name="enable-dependencies"></a>Abilitare le dipendenze

Il **pulsante Abilita dipendenze** selezionerà automaticamente le dipendenze mancanti. Ciò vale per le dipendenze selezionate in  modo esplicito (visualizzate nell'elenco Funzionalità) e quelle selezionate in modo implicito in base ai requisiti delle funzionalità selezionate.

### <a name="disable-features"></a>Disabilitare le funzionalità

Se **si seleziona Disabilita** funzionalità, tutte le funzionalità che dipendono da una o più dipendenze che sono state deselezionate verranno deselezionate automaticamente. Questo vale per i pacchetti di dipendenze selezionati in modo implicito e le funzionalità selezionate in modo esplicito.

## <a name="importing"></a>Importazione

Selezionare **Importa** per aggiungere le funzionalità selezionate e dare [l'approvazione finale prima](reviewing-changes.md) di aggiornare il progetto di destinazione.

> [!IMPORTANT]
> Se durante l'importazione rimane un problema di convalida, verrà visualizzato un messaggio di avviso. È consigliabile selezionare No, fare clic su **Convalida e** risolvere eventuali problemi presentati.
>
> ![Continuare con i problemi di convalida](images/ValidationContinueAnyway.png)

## <a name="going-back-to-the-previous-step"></a>Tornare al passaggio precedente

Da **Importa funzionalità,** lo strumento di funzionalità di realtà mista consente di tornare all'individuazione. [](discovering-features.md) Selezionare **Torna indietro per** scaricare altri pacchetti di funzionalità.

## <a name="see-also"></a>Vedi anche

- [Introduzione a Mixed Reality Feature Tool](welcome-to-mr-feature-tool.md)
- [Individuazione e acquisizione](discovering-features.md)
- [Visualizzazione dei dettagli del pacchetto di funzionalità](viewing-package-details.md)
- [Revisione e approvazione delle modifiche del progetto](reviewing-changes.md)
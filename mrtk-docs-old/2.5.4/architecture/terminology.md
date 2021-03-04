---
title: Terminologia
description: Sistema di input diversa in MRTK.
author: cDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, input,
ms.openlocfilehash: 555f84b10e35e905b1c05a640f075c7d0394fad4
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/03/2021
ms.locfileid: "101783789"
---
# <a name="input-system"></a>Sistema di input

Il sistema di input è uno dei sistemi più grandi per tutte le funzionalità offerte da MRTK.
Molti elementi all'interno del Toolkit si basano su di esso (puntatori, messa a fuoco, prefabbricati). Il codice all'interno del sistema di input è quello che consente le interazioni naturali, ad esempio il recupero e la rotazione tra le diverse piattaforme.

Il sistema di input presenta alcuni dei propri termini che è opportuno definire:

- **Provider di dati**

    Le impostazioni di input nel profilo di input contengono riferimenti a entità note come provider di dati, un'altra parola che ne descrive i gestori di dispositivi. Si tratta di componenti il cui processo consiste nell'estendere il sistema di input MRTK tramite l'interazione con un sistema sottostante specifico. Un esempio di provider è il provider di realtà mista di Windows, il cui compito consiste nel comunicare con le API di realtà mista di Windows sottostanti e quindi tradurre i dati da tali API in concetti di input specifici di MRTK di seguito. Un altro esempio è il provider OpenVR, il cui processo consiste nel comunicare con la versione astratta di Unity delle API OpenVR e quindi tradurre i dati in concetti di input MRTK.

- **Controller**

    Rappresentazione di un controller fisico (se si tratta di un controller a 6 gradi di libertà, una mano di tipo HoloLens con supporto per i movimenti, una mano completamente articolata, un controller di movimento LEAP e così via). I controller vengono generati da Gestione dispositivi (ad esempio, WMR Device Manager genera un controller e ne gestisce la durata quando si verifica una mano articolata).

- **Puntatore**

    I controller usano i puntatori per interagire con gli oggetti di gioco. Il puntatore near Interaction, ad esempio, è responsabile del rilevamento quando la mano (ovvero un controller) si avvicina a oggetti che si annunciano come supporto di "near Interaction". Altri esempi per i puntatori sono la teleportazione o i puntatori a distanza (ovvero il puntatore del raggio della mano della Shell) che usano raycasts per interagire con il contenuto che è più lungo della lunghezza delle armi dell'utente.

    I puntatori vengono creati da Gestione dispositivi e quindi collegati a un'origine di input. Per ottenere tutti i puntatori per un controller, eseguire le operazioni seguenti: `controller.InputSource.Pointers`

    Si noti che un controller può essere associato a molti puntatori diversi contemporaneamente. Per assicurarsi che questo non determini il caos, c'è un Mediator del puntatore che controlla i puntatori che possono essere attivi. ad esempio, il Mediator Disabilita i puntatori di interazione di disparità quando viene rilevata l'interazione vicina.

- **Lo stato attivo**

    Gli eventi del puntatore vengono inviati agli oggetti nello **stato attivo**. La selezione dello stato attivo può variare in base al tipo di puntatore; un puntatore a raggio mano userà raycasts, mentre un puntatore poke utilizzerà spherecasts. Un oggetto deve implementare IMixedRealityFocusHandler per ricevere lo stato attivo. È possibile registrare globalmente un oggetto per ricevere eventi puntatore non filtrati, ma questo approccio non è consigliato.

    Il componente che aggiorna quali oggetti sono in stato attivo è [FocusProvider](xref:Microsoft.MixedReality.Toolkit.Input.FocusProvider)

- **Cursore**

    Entità associata a un puntatore che fornisce indicazioni visive aggiuntive intorno all'interazione del puntatore. Ad esempio, il FingerCursor eseguirà il rendering di un anello intorno al dito e potrà ruotare tale anello quando il dito si avvicina agli oggetti "near interactable". Un puntatore può essere associato a un singolo cursore al momento.

- **Interazione e manipolazione**

    Gli oggetti possono essere contrassegnati con uno script di interazione o manipolazione. Potrebbe trattarsi di un oggetto o di un [`Interactable`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) elemento simile a [`NearInteractionGrabbable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionGrabbable) / [`ManipulationHandler`](xref:Microsoft.MixedReality.Toolkit.UI.ManipulationHandler) .

    Ad esempio, NearInteractionGrabbable e NearInteractionTouchable consentono determinati puntatori (in particolare vicino ai puntatori di interazione) per individuare gli oggetti su cui è possibile concentrarsi.

    Interactable e ManipulationHandler sono esempi di componenti che ascoltano gli eventi del puntatore per modificare gli oggetti visivi dell'interfaccia utente o spostare/ridimensionare/ruotare gli oggetti di gioco.

L'immagine seguente acquisisce la build di alto livello (dal basso verso l'alto) dello stack di input MRTK:

![Diagramma del sistema di input](../features/images/input/MRTK_InputSystem.png)

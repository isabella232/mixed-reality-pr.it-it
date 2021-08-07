---
title: Terminologia
description: Termini del sistema di input diversi in MRTK.
author: cDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, input,
ms.openlocfilehash: 8046501fdab0a7594800a75ad0306a131adaaa6924ffa870c299571cbd4d8e13
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115211158"
---
# <a name="input-system"></a>Sistema di input

Il sistema di input è uno dei sistemi più grandi di tutte le funzionalità offerte da MRTK.
Molti elementi all'interno del toolkit si basano su di esso (puntatori, messa a fuoco, prefab). Il codice all'interno del sistema di input è ciò che consente interazioni naturali, ad esempio afferrare e ruotare tra piattaforme diverse.

Il sistema di input ha una terminologia propria che vale la pena definire:

- **Provider di dati**

    Le impostazioni di input nel profilo di input hanno riferimenti a entità note come provider di dati, un'altra parola che descrive che si tratta di gestori di dispositivi. Si tratta di componenti il cui compito è estendere il sistema di input MRTK tramite l'interfaccia con un sistema sottostante specifico. Un esempio di provider è il provider Windows Mixed Reality, il cui compito è quello di parlare con le API Windows Mixed Reality sottostanti e quindi tradurre i dati da tali API in concetti di input specifici di MRTK di seguito. Un altro esempio è il provider OpenVR (il cui compito è quello di parlare con la versione astratta da Unity delle API OpenVR e quindi tradurre i dati in concetti di input MRTK).

- **Controller**

    Rappresentazione di un controller fisico (che si tratta di un controller di 6 gradi di libertà, una mano HoloLens 1 stile con supporto dei movimenti, una mano completamente articolata, un controller di movimento intercalare e così via). I controller vengono generati da gestori di dispositivi(ad esempio, gestione dispositivi WMR genera un controller e ne gestisce la durata quando viene visualizzata una mano articolata).

- **Puntatore**

    I controller usano i puntatori per interagire con gli oggetti di gioco. Ad esempio, il puntatore di interazione vicino è responsabile del rilevamento quando la mano (che è un controller) è vicina agli oggetti che annunciano se stessi come supporto di "interazione vicina". Altri esempi per i puntatori sono i puntatori di teletrasporto o lontano (ad esempio, il puntatore a raggi della mano della shell) che usano raggi di distanza per interagire con contenuto più lungo della lunghezza delle braci da parte dell'utente.

    I puntatori vengono creati da Gestione dispositivi e quindi collegati a un'origine di input. Per ottenere tutti i puntatori per un controller, eseguire le seguenti operazione: `controller.InputSource.Pointers`

    Si noti che un controller può essere associato contemporaneamente a molti puntatori diversi. Per garantire che ciò non si dedivi nel caos, esiste un mediatore di puntatori che controlla quali puntatori possono essere attivi (ad esempio, il mediatore disabilita i puntatori di interazione lontano quando viene rilevata un'interazione vicina).

- **Focus**

    Gli eventi puntatore vengono inviati agli oggetti nello **stato attivo.** La selezione dello stato attivo varia in base al tipo di puntatore. un puntatore a raggi a mano userà raycast, mentre un puntatore poke userà spherecast. Un oggetto deve implementare IMixedRealityFocusHandler per ricevere lo stato attivo. È possibile registrare a livello globale un oggetto per ricevere eventi puntatore non filtrati, ma questo approccio non è consigliato.

    Il componente che aggiorna gli oggetti in stato attivo è [FocusProvider](xref:Microsoft.MixedReality.Toolkit.Input.FocusProvider)

- **Cursore**

    Entità associata a un puntatore che fornisce suggerimenti visivi aggiuntivi sull'interazione del puntatore. Ad esempio, FingerCursor eseguirà il rendering di un anello intorno al dito e potrebbe ruotare l'anello quando il dito è vicino a oggetti "vicino all'interazione". Un puntatore può essere associato a un singolo cursore alla volta.

- **Interazione e manipolazione**

    Gli oggetti possono essere contrassegnati con uno script di interazione o manipolazione. Può trattarsi di tramite [`Interactable`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) , o qualcosa di simile a [`NearInteractionGrabbable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionGrabbable) / [`ManipulationHandler`](xref:Microsoft.MixedReality.Toolkit.UI.ManipulationHandler) .

    Ad esempio, NearInteractionGrabbable e NearInteractionTouchable consentono a determinati puntatori (in particolare vicino ai puntatori di interazione) di sapere su quali oggetti è possibile concentrarsi.

    Interactable e ManipulationHandler sono esempi di componenti che sono in ascolto degli eventi puntatore per modificare gli oggetti visivi dell'interfaccia utente o spostare/ridimensionare/ruotare gli oggetti di gioco.

L'immagine seguente acquisisce l'accumulo di alto livello (dal basso verso l'alto) dello stack di input MRTK:

![Diagramma del sistema di input](../features/images/input/MRTK_InputSystem.png)

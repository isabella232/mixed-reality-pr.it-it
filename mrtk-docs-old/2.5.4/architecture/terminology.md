---
title: Terminologia
description: Sistema di input diffrent in MRTK.
author: cDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, input,
ms.openlocfilehash: e13dd23b33690039839ad66d8b0e3235a7238fc6118927dbce51065e01aae3ee
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115201823"
---
# <a name="input-system"></a>Sistema di input

Il sistema di input è uno dei sistemi più grandi di tutte le funzionalità offerte da MRTK.
Molti elementi all'interno del toolkit si basano su di esso (puntatori, stato attivo, prefab). Il codice all'interno del sistema di input consente interazioni naturali, ad esempio afferrare e ruotare tra piattaforme diverse.

Il sistema di input ha una terminologia propria che vale la pena definire:

- **Provider di dati**

    Le impostazioni di input nel profilo di input hanno riferimenti a entità note come provider di dati, un'altra parola che descrive che si tratta di gestori di dispositivi. Si tratta di componenti il cui compito è quello di estendere il sistema di input MRTK tramite l'interfaccia con un sistema sottostante specifico. Un esempio di provider è il provider Windows Mixed Reality, il cui compito è quello di parlare con le API Windows Mixed Reality sottostanti e quindi convertire i dati da tali API in concetti di input specifici di MRTK riportati di seguito. Un altro esempio è il provider OpenVR (il cui compito è quello di parlare con la versione astratta da Unity delle API OpenVR e quindi convertire i dati in concetti di input MRTK).

- **Controller**

    Rappresentazione di un controller fisico (che si tratta di un controller a 6 gradi di libertà, una mano di tipo HoloLens 1 con supporto del movimento, una mano completamente articolata, un controller di movimento intercalare e così via). I controller vengono generati da gestori di dispositivi, ad esempio gestione dispositivi WMR genera un controller e ne gestisce la durata quando viene visualizzata una mano articolata.

- **Puntatore**

    I controller usano i puntatori per interagire con gli oggetti gioco. Ad esempio, il puntatore di interazione da vicino è responsabile del rilevamento quando la mano (che è un controller) è vicina agli oggetti che si annunciano come supporto dell'"interazione da vicino". Altri esempi di puntatori sono il teletrasporto o i puntatori da lontano (ad esempio, l'indicatore di misura del raggio della mano della shell) che usano raycast di distanza per interagire con contenuti più lunghi della lunghezza delle mani da parte dell'utente.

    I puntatori vengono creati da Gestione dispositivi e quindi collegati a un'origine di input. Per ottenere tutti i puntatori per un controller, eseguire: `controller.InputSource.Pointers`

    Si noti che un controller può essere associato a molti puntatori diversi contemporaneamente. Per assicurarsi che non si diffondono nel chaos, è disponibile un mediatore di puntatori che controlla quali puntatori possono essere attivi (ad esempio, il mediatore disabiliterà i puntatori di interazione da lontano quando viene rilevata l'interazione da vicino).

- **Focus**

    Gli eventi del puntatore vengono inviati agli oggetti nello **stato attivo.** La selezione dello stato attivo varia in base al tipo di puntatore. Un indicatore di misura del raggio della mano userà raycast, mentre un puntatore poke userà spherecast. Un oggetto deve implementare IMixedRealityFocusHandler per ricevere lo stato attivo. È possibile registrare a livello globale un oggetto per ricevere eventi puntatore non filtrati, ma questo approccio non è consigliato.

    Il componente che aggiorna gli oggetti con lo stato attivo è [FocusProvider](xref:Microsoft.MixedReality.Toolkit.Input.FocusProvider)

- **Cursore**

    Entità associata a un puntatore che fornisce suggerimenti visivi aggiuntivi sull'interazione del puntatore. Ad esempio, FingerCursor esegue il rendering di un anello intorno al dito e può ruotare l'anello quando il dito è vicino a oggetti "near interactable". Un puntatore può essere associato a un singolo cursore alla volta.

- **Interazione e manipolazione**

    Gli oggetti possono essere contrassegnati con uno script di interazione o manipolazione. Può trattarsi di tramite [`Interactable`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) o un elemento simile a [`NearInteractionGrabbable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionGrabbable) / [`ManipulationHandler`](xref:Microsoft.MixedReality.Toolkit.UI.ManipulationHandler) .

    Ad esempio, NearInteractionGrabbable e NearInteractionTouchable consentono a determinati puntatori (in particolare i puntatori di interazione da vicino) di sapere su quali oggetti è possibile concentrarsi.

    Interactable e ManipulationHandler sono esempi di componenti che sono in ascolto di eventi puntatore per modificare gli oggetti visivi dell'interfaccia utente o spostare/ridimensionare/ruotare gli oggetti gioco.

L'immagine seguente acquisisce la compilazione di alto livello (dal basso verso l'alto) dello stack di input MRTK:

![Diagramma del sistema di input](../features/images/input/MRTK_InputSystem.png)

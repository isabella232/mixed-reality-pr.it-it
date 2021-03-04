---
title: ManipulationHandler
description: Documentazione sul gestore di manipolazione in MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, manipolazione,
ms.openlocfilehash: f294516b7446934f4f390055644b32c99a564426
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/03/2021
ms.locfileid: "101781945"
---
# <a name="manipulation-handler"></a>Gestore di manipolazione

![Gestore di manipolazione](../images/manipulation-handler/MRTK_Manipulation_Main.png)

Lo script *ManipulationHandler* consente a un oggetto di essere reso mobile, scalabile e girevole usando uno o due mani. La manipolazione può essere limitata in modo da consentire solo determinati tipi di trasformazione. Lo script funziona con vari tipi di input, tra cui l'input mano articolato HoloLens 2, l'input del movimento HoloLens (primo generazione) e l'input del controller di movimento per auricolari immersivi.

## <a name="how-to-use-the-manipulation-handler"></a>Come utilizzare il gestore di manipolazione

Aggiungere il `ManipulationHandler` componente script a un GameObject. Assicurarsi di aggiungere anche un Collider all'oggetto, associando i relativi limiti afferrabili.

Per fare in modo che l'oggetto risponda all'input della mano quasi articolato, aggiungere `NearInteractionGrabbable` anche lo script.

![Gestore di manipolazione](../images/manipulation-handler/MRTK_ManipulationHandler_Howto.png)

## <a name="inspector-properties"></a>Proprietà di Inspector

<img src="../images/manipulation-handler/MRTK_ManipulationHandler_Structure.png" width="450" alt="Manipulation Handler structure">

**Trasformazione host** Trasformazione che verrà trascinata. Il valore predefinito è l'oggetto del componente.

**Tipo di manipolazione** Specifica se l'oggetto può essere modificato usando una sola mano, due mani o entrambe.

* *Una sola mano*
* *Due solo mano*
* *Una e due passate*

**Tipo di manipolazione a due mano**

* *Scala*: è consentita solo la scalabilità.
* *Rotazione*: è consentita solo la rotazione.
* *Sposta scala*: lo spostamento e il ridimensionamento sono consentiti.
* *Spostamento ruotare*: lo spostamento e la rotazione sono consentiti.
* *Ridimensiona scala*: è consentito ruotare e ridimensionare.
* *Sposta scala ruota*: lo spostamento, la rotazione e il ridimensionamento sono consentiti.

![Gestore di manipolazione](../images/manipulation-handler/MRTK_ManipulationHandler_TwoHanded.jpg)

**Consenti manipolazione a lungo** Specifica se è possibile eseguire la manipolazione utilizzando l'interazione con i puntatori.

**Modalità di rotazione a una mano vicino** Specifica come si comporterà l'oggetto quando viene afferrato con una mano o un controller vicino a.

**Modalità di rotazione a una mano** Specifica come si comporterà l'oggetto quando viene afferrato con una mano/controller a distanza.

**Opzioni modalità rotazione a mano singola** Specifica il modo in cui l'oggetto verrà ruotato quando viene afferrato con una sola mano.

* *Mantieni rotazione originale*: non ruota l'oggetto durante lo spostamento
* *Mantieni la rotazione per l'utente*: mantiene la rotazione originale dell'oggetto per l'asse X/Y per l'utente
* *Allineamento di gravità mantenere la rotazione all'utente*: mantiene la rotazione originale dell'oggetto per l'utente, ma rende l'oggetto verticale. Utile per gli oggetti con un controllo Bounds.
* *Utente viso*: assicura che l'oggetto faccia sempre fronte all'utente. Utile per gli slate o i pannelli.
* *Faccia fuori dall'utente*: assicura che l'oggetto faccia sempre fronte all'utente. Utile per gli slate o i pannelli che sono configurati all'indietro.
* *Ruota intorno al centro oggetti*: funziona solo per le mani o i controller articolati. Ruotare l'oggetto usando la rotazione della mano o del controller, ma il punto centrale dell'oggetto. Utile per il controllo a distanza.
* *Ruota intorno al punto di* controllo: funziona solo per le mani e i controller articolati. Ruotare l'oggetto come se fosse gestito da mano/controller. Utile per l'ispezione.

**Comportamento della versione** Quando viene rilasciato un oggetto, specificarne il comportamento di spostamento fisico. Richiede che un componente rigidbody sia su tale oggetto.

* *Nothing*
* *Tutto*
* *Mantieni velocità*
* *Mantieni velocità angolare*

**Vincoli sulla rotazione** Specifica su quale asse ruotare l'oggetto quando si interagisce con.

* *Nessuno*
* *Solo asse X*
* *Solo asse Y*
* *Solo asse Z*

**Usa spazio locale per il vincolo** Interruttore per passare tra l'applicazione di vincoli rispetto all'asse dello spazio globale o l'asse dello spazio locale.

**Vincoli sullo spostamento**

* *Nessuno*
* *Correggi distanza da capo*

**Smoothing attivo** Specifica se la smussatura è attiva.

**Uniformità della quantità di una mano** Quantità di smussatura da applicare allo spostamento, alla scala, alla rotazione. L'uniformità di 0 significa nessuna smussatura. Il valore max significa nessuna modifica al valore.

## <a name="events"></a>Eventi

Il gestore di manipolazione fornisce gli eventi seguenti:

* *OnManipulationStarted*: generato all'avvio della manipolazione.
* *OnManipulationEnded*: viene attivato al termine della manipolazione.
* *OnHoverStarted*: viene attivato quando una mano o un controller passa il mouse sul manipolabile, quasi o lontano.
* *OnHoverEnded*: viene attivato quando una mano o un controller Annulla il passaggio del mouse sul manipolabile, quasi o lontano.

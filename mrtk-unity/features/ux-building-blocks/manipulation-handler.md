---
title: Gestore di manipolazione
description: Documentazione sul gestore di manipolazione in MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, manipolazione,
ms.openlocfilehash: 179ef40ba054b0fda3b13e9d578905eb064a58ab
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176628"
---
# <a name="manipulation-handler"></a>Gestore di manipolazione

![Gestore di manipolazione](../images/manipulation-handler/MRTK_Manipulation_Main.png)

Lo script *ManipulationHandler* consente di impostare un oggetto in modo che sia mobile, scalabile e ruotabile usando una o due mani. La manipolazione può essere limitata in modo da consentire solo determinati tipi di trasformazione. Lo script funziona con vari tipi di input, tra cui l'input della mano articolato HoloLens 2 i raggi della mano, l'input del movimento di HoloLens (prima generazione) e l'input del controller del movimento del visore VR immersive.

## <a name="how-to-use-the-manipulation-handler"></a>Come usare il gestore di manipolazione

Aggiungere il `ManipulationHandler` componente script a un GameObject. Assicurarsi anche di aggiungere un collisore all'oggetto, corrispondente ai limiti afferrabili.

Per fare in modo che l'oggetto risponda all'input della mano quasi articolato, aggiungere `NearInteractionGrabbable` anche lo script .

![Uso del gestore di manipolazione nell'editor di Unity](../images/manipulation-handler/MRTK_ManipulationHandler_Howto.png)

## <a name="inspector-properties"></a>Proprietà del controllo

<img src="../images/manipulation-handler/MRTK_ManipulationHandler_Structure.png" width="450" alt="Manipulation Handler structure">

**Trasformazione host** Trasformazione che verrà trascinata. Il valore predefinito è l'oggetto del componente.

**Tipo di manipolazione** Specifica se l'oggetto può essere modificato usando una mano, due mani o entrambe.

* *Solo una mano*
* *Solo a due mani*
* *Una e due mani*

**Tipo di manipolazione a due mani**

* *Scalabilità:* è consentito solo il ridimensionamento.
* *Ruota:* è consentita solo la rotazione.
* *Sposta scala:* lo spostamento e il ridimensionamento sono consentiti.
* *Sposta rotazione:* lo spostamento e la rotazione sono consentiti.
* *Ruotare la scala:* la rotazione e il ridimensionamento sono consentiti.
* *Move Rotate Scale (Sposta scala* di rotazione): lo spostamento, la rotazione e il ridimensionamento sono consentiti.

![Gestore di manipolazione](../images/manipulation-handler/MRTK_ManipulationHandler_TwoHanded.jpg)

**Consenti manipolazione da lontano** Specifica se la manipolazione può essere eseguita usando l'interazione da lontano con i puntatori.

**Modalità di rotazione a una mano nelle vicinanze** Specifica il comportamento dell'oggetto quando viene afferrato con una mano o un controller vicino.

**Modalità di rotazione a una mano da lontano** Specifica il comportamento dell'oggetto quando viene afferrato con una mano/controller a distanza.

**Opzioni della modalità rotazione a una mano** Specifica la modalità di rotazione dell'oggetto quando viene afferrato con una mano.

* *Mantieni rotazione originale:* non ruota l'oggetto mentre viene spostato
* *Mantieni la rotazione per* l'utente: mantiene la rotazione originale dell'oggetto per l'asse X/Y per l'utente
* *La gravità allineata mantiene la rotazione* all'utente: mantiene la rotazione originale dell'oggetto all'utente, ma rende l'oggetto verticale. Utile per gli oggetti con un controllo limiti.
* *Utente viso:* garantisce che l'oggetto sia sempre di fronte all'utente. Utile per slate/pannelli.
* *Face away from user (Viso lontano* dall'utente): garantisce che l'oggetto sia sempre lontano dall'utente. Utile per slate/pannelli configurati all'indietro.
* *Ruotare intorno al centro dell'oggetto:* funziona solo per mani/controller articolati. Ruotare l'oggetto usando la rotazione della mano/controller, ma intorno al punto centrale dell'oggetto. Utile per ispezionare a distanza.
* *Ruotare intorno al punto di* cattura: funziona solo per mani/controller articolati. Ruotare l'oggetto come se fosse in mano/controller. Utile per l'ispezione.

**Comportamento di rilascio** Quando un oggetto viene rilasciato, specificarne il comportamento di spostamento fisico. Richiede che un componente rigidbody sia in tale oggetto.

* *Nothing*
* *Tutto*
* *Mantenere la velocità*
* *Mantenere Angular velocità*

**Vincoli sulla rotazione** Specifica l'asse con cui l'oggetto ruota quando interagisce.

* *Nessuno*
* *Solo asse X*
* *Solo asse Y*
* *Solo asse Z*

**Usare lo spazio locale per il vincolo** Interruttore per passare dall'applicazione di vincoli rispetto all'asse dello spazio del mondo o all'asse dello spazio locale.

**Vincoli sullo spostamento**

* *Nessuno*
* *Correggere la distanza dalla testa*

**Smoothing Active** Specifica se la smussazione è attiva.

**Smoothing Amount One Hand** Quantità di smussamento da applicare a movimento, scala e rotazione. Smussamento di 0 significa nessuna smussamento. Il valore massimo indica che non viene apportata alcuna modifica al valore.

## <a name="events"></a>Eventi

Il gestore di manipolazione fornisce gli eventi seguenti:

* *OnManipulationStarted: generato* all'avvio della manipolazione.
* *OnManipulationEnded:* viene generato al termine della manipolazione.
* *OnHoverStarted:* viene attivato quando una mano/controller passa il puntatore del mouse sul manipolabile, vicino o lontano.
* *OnHoverEnded:* viene attivato quando una mano/controller sposta il puntatore del mouse sul manipolabile, vicino o lontano.

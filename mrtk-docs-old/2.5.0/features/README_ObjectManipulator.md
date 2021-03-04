---
title: README_ObjectManipulator
description: Come usare il manipolatore di oggetti in MRTK
author: thalbern
ms.author: bethalha
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, manipolazione degli oggetti,
ms.openlocfilehash: bcfb4708ceafb74fd656a355857829cec5c9f7e3
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/03/2021
ms.locfileid: "101783115"
---
# <a name="object-manipulator"></a>Manipolatore di oggetti

![Manipolatore oggetto principale](Images/ManipulationHandler/MRTK_Manipulation_Main.png)

*ObjectManipulator* è il nuovo componente per il comportamento di manipolazione, disponibile in precedenza in *ManipulationHandler*. Il manipolatore di oggetti apporta diversi miglioramenti e semplificazioni. Questo componente sostituisce il gestore di manipolazione, che verrà deprecato.

Lo script *ObjectManipulator* rende un oggetto mobile, scalabile e girevole usando uno o due mani. Il manipolatore di oggetti può essere configurato per controllare la modalità di risposta dell'oggetto a diversi input. Lo script dovrebbe funzionare con la maggior parte delle forme di interazione, ad esempio HoloLens 2, a mano articolata, HoloLens 2, raggi mano, HoloLens 1 sguardo e movimenti e input del controller di movimento dell'auricolare.

## <a name="how-to-use-the-object-manipulator"></a>Come utilizzare il manipolatore di oggetti

Per usare il manipolatore di oggetti, aggiungere prima il `ObjectManipulator` componente script a un GameObject. Assicurarsi di aggiungere anche un Collider all'oggetto, associando i relativi limiti afferrabili.

Per fare in modo che l'oggetto risponda all'input della mano quasi articolato, aggiungere `NearInteractionGrabbable` anche lo script.

Il comportamento fisico può essere abilitato per il manipolatore di oggetti aggiungendo un componente rigidbody all'oggetto. Il comportamento fisico abilitato aggiungendo questo componente viene discusso in modo più dettagliato in [*fisica e collisioni*](#physics-and-collisions).

Inoltre, la manipolazione può essere vincolata dall'aggiunta di componenti di [vincoli di manipolazione](README_ConstraintManager.md#transform-constraints) all'oggetto. Si tratta di componenti speciali che funzionano con la manipolazione e modificano in qualche modo il comportamento di manipolazione.

![Procedura per il gestore della manipolazione](Images/ObjectManipulator/MRTK_ObjectManipulator_Howto.png)

## <a name="inspector-properties-and-fields"></a>Proprietà e campi di Inspector

<img src="Images/ObjectManipulator/MRTK_ObjectManipulator_Structure.png" width="450" alt="Object Manipulator Structure">

### <a name="general-properties"></a>Proprietà generali

#### <a name="host-transform"></a>Trasformazione host

Trasformazione dell'oggetto che verrà modificato. Il valore predefinito è l'oggetto del componente.

#### <a name="manipulation-type"></a>Tipo di manipolazione

Specifica se l'oggetto può essere modificato usando una sola mano o due mani. Poiché questa proprietà è un flag, è possibile selezionare entrambe le opzioni.

- *Uno gestito*: Abilita una manipolazione gestita se selezionata.
- *Due gestite*: Abilita due manipolazioni gestite, se selezionate.

#### <a name="allow-far-manipulation"></a>Consenti manipolazione a lungo

Specifica se è possibile eseguire la manipolazione utilizzando l'interazione con i puntatori.

### <a name="one-handed-manipulation-properties"></a>Proprietà di manipolazione a una mano

#### <a name="one-hand-rotation-mode-near"></a>Modalità di rotazione a una mano vicino

Specifica come si comporterà l'oggetto quando viene afferrato con una mano vicino a. Queste opzioni funzionano solo per le mani articolate.

- *Ruota intorno al centro oggetti*: l'oggetto ruota usando la rotazione della mano, ma il punto centrale dell'oggetto. L'oggetto comparirà in modo che lo spostamento risulti minore durante la rotazione, ma potrebbe esserci una sensazione di disconnessione tra la mano e l'oggetto. Più utile per l'interazione di gran lunga.
- *Ruota intorno al punto di* controllo: ruotare l'oggetto con la mano del punto di controllo tra il pollice e il dito dell'indice. Dovrebbe essere considerato come se l'oggetto fosse mantenuto a mano.

#### <a name="one-hand-rotation-mode-far"></a>Modalità di rotazione a una mano

Specifica come si comporterà l'oggetto quando viene afferrato con una sola mano alla distanza. Queste opzioni funzionano solo per le mani articolate.

- *Ruotare about Object Center*: ruotare l'oggetto usando la rotazione della mano, ma il punto centrale dell'oggetto. Utile per esaminare a distanza senza che il centro oggetti si sposti durante la rotazione dell'oggetto.
- *Ruota intorno al punto di* recupero: ruotare l'oggetto usando la rotazione della mano, ma il punto di riscontro del raggio puntatore. Utile per l'ispezione.

### <a name="two-handed-manipulation-properties"></a>Due proprietà di manipolazione gestite

#### <a name="two-handed-manipulation-type"></a>Tipo di manipolazione a due mano

Specifica il modo in cui due manipolazioni a mano possono trasformare un oggetto. Poiché questa proprietà è un flag, è possibile selezionare qualsiasi numero di opzioni.

- *Move*: lo spostamento è consentito se selezionato.
- *Scala*: il ridimensionamento è consentito se selezionato.
- *Rotazione: la* rotazione è consentita se selezionata.

![Gestore di manipolazione due gestiti](Images/ManipulationHandler/MRTK_ManipulationHandler_TwoHanded.jpg)

### <a name="constraints"></a>Vincoli

#### <a name="enable-constraints"></a>Abilita vincoli

Questa impostazione consentirà di abilitare il [gestore di vincoli](README_ConstraintManager.md)collegati. Le modifiche alle trasformazioni verranno elaborate dai vincoli registrati per il [gestore di vincoli](README_ConstraintManager.md)selezionato.

#### <a name="constraint-manager"></a>Gestione vincoli

L'elenco a discesa consente di selezionare qualsiasi [gestore di vincoli](README_ConstraintManager.md)associato. Il manipolatore di oggetti garantisce la presenza di un [gestore di vincoli](README_ConstraintManager.md) sempre collegato.
Si noti che più componenti dello stesso tipo vengono visualizzati con lo stesso nome in Unity. Per semplificare la distinzione tra più gestori di vincoli nello stesso oggetto, le opzioni disponibili visualizzeranno un hint per la configurazione del gestore di vincoli selezionato (selezione del vincolo manuale o automatica).

#### <a name="go-to-component"></a>Vai al componente

La selezione di gestione vincoli viene fornita con un pulsante *Vai al componente* . Questo pulsante farà sì che il controllo Scorri fino al componente selezionato in modo che sia possibile configurarlo.

### <a name="physics"></a>Fisica

Le impostazioni in questa sezione vengono visualizzate solo quando l'oggetto include un componente RigidBody.

#### <a name="release-behavior"></a>Comportamento della versione

Specificare le proprietà fisiche che un oggetto modificato deve tenere al rilascio. Poiché questa proprietà è un flag, è possibile selezionare entrambe le opzioni.

- *Mantieni velocità*: quando l'oggetto viene rilasciato, se questa opzione è selezionata, manterrà la velocità lineare.
- *Mantieni velocità angolare*: quando l'oggetto viene rilasciato, se questa opzione è selezionata, manterrà la velocità angolare.

#### <a name="use-forces-for-near-manipulation"></a>USA Forces per la manipolazione quasi

Indica se vengono usate le forze di fisica per spostare l'oggetto quando si eseguono le modifiche più vicine. Se si imposta questa opzione su *false* , l'oggetto risulterà più connesso direttamente alla mano degli utenti. L'impostazione di questa opzione su *true* rispetterà la massa e l'inerzia dell'oggetto, ma potrebbe essere considerato come se l'oggetto fosse connesso tramite una molla. Il valore predefinito è *false*.

### <a name="smoothing"></a>Definizione di movimenti uniformi

#### <a name="smoothing-far"></a>Smussamento lontano

Indica se la smussatura indipendente dalla frequenza dei fotogrammi è abilitata per le interazioni lontane. Per impostazione predefinita, la smussatura è abilitata.

#### <a name="smoothing-near"></a>Smussamento vicino

Se è abilitata la smussatura indipendente dalla frequenza dei frame per le interazioni near. Near smoothing è disabilitato per impostazione predefinita perché l'effetto può essere percepito come ' disconnected ' dalla mano.

#### <a name="smoothing-active"></a>Smoothing attivo

Obsoleto e verrà rimosso in una versione futura. Le applicazioni devono usare SmoothingFar, SmoothingNear o una combinazione dei due.

#### <a name="move-lerp-time"></a>Sposta Lerp tempo

Quantità di smussatura da applicare allo spostamento. L'uniformità di 0 significa nessuna smussatura. Il valore max significa nessuna modifica al valore.

#### <a name="rotate-lerp-time"></a>Ruota Lerp tempo

Quantità di smussatura da applicare alla rotazione. L'uniformità di 0 significa nessuna smussatura. Il valore max significa nessuna modifica al valore.

#### <a name="scale-lerp-time"></a>Ridimensionamento Lerp tempo

Quantità di smussatura da applicare alla scala. L'uniformità di 0 significa nessuna smussatura. Il valore max significa nessuna modifica al valore.

### <a name="manipulation-events"></a>Eventi di manipolazione

Il gestore di manipolazione fornisce gli eventi seguenti:

- *OnManipulationStarted*: generato all'avvio della manipolazione.
- *OnManipulationEnded*: viene attivato al termine della manipolazione.
- *OnHoverStarted*: viene attivato quando una mano o un controller passa il mouse sul manipolabile, quasi o lontano.
- *OnHoverEnded*: viene attivato quando una mano o un controller Annulla il passaggio del mouse sul manipolabile, quasi o lontano.

L'ordine di attivazione dell'evento per la manipolazione è:

*OnHoverStarted*  ->  *OnManipulationStarted*  ->  *OnManipulationEnded*  ->  *OnHoverEnded*

Se non è presente alcuna manipolazione, si otterranno comunque gli eventi hover con l'ordine di incendio seguente:

*OnHoverStarted*  ->  *OnHoverEnded*

## <a name="physics-and-collisions"></a>Fisica e collisioni

Il comportamento fisico può essere abilitato aggiungendo un componente rigidbody allo stesso oggetto di un manipolatore di oggetti. Non solo questa operazione Abilita la configurazione del [comportamento di rilascio](#release-behavior) precedente, inoltre consente conflitti. Senza un componente rigidbody, i conflitti non si comportano correttamente durante la manipolazione:

- I conflitti tra un oggetto modificato e un Collider statico (ovvero un oggetto con un Collider ma nessun rigidbody) non funzionano, l'oggetto modificato passa direttamente attraverso il Collider statico senza effetti.
- Collisioni tra un oggetto modificato e un rigidbody (ad esempio un oggetto con un Collider e un rigidbody) fa sì che rigidbody abbia una risposta di collisione, ma la risposta è inattiva e non naturale. Non esiste inoltre alcuna risposta di collisione sull'oggetto modificato.

Quando viene aggiunto un rigidbody, i conflitti dovrebbero funzionare correttamente.

### <a name="without-rigidbody"></a>Senza rigidbody

<img src="Images/ObjectManipulator/MRTK_PhysicsManipulation_NoRigidbody.gif" width="500" alt="No Riged body">

### <a name="with-rigidbody"></a>Con rigidbody

<img src="Images/ObjectManipulator/MRTK_PhysicsManipulation_Rigidbody.gif" width="500" alt="Rigid Body">

## <a name="elastics-experimental"></a>Elastici (sperimentale)

Gli elastici possono essere usati per la manipolazione di oggetti tramite il manipolatore di oggetti. Si noti che il [sistema elastico](Elastics/ElasticSystem.md) è ancora in stato sperimentale. Per abilitare gli elastici, collegare un componente di gestione elastici esistente o creare e collegare un nuovo gestore elastici tramite il `Add Elastics Manager` pulsante.

<img src="Images/BoundsControl/MRTK_BoundsControl_Elastics.png" width="450" alt="Elastics Bounds control">

## <a name="see-also"></a>Vedi anche

- [Controllo dei limiti](README_BoundsControl.md)
- [Gestione vincoli](README_ConstraintManager.md)
- [Finestra di migrazione](Tools/MigrationWindow.md)
- [Sistema elastici (sperimentale)](Elastics/ElasticSystem.md)

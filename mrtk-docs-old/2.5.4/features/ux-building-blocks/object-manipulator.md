---
title: ObjectManipulator
description: Come usare il manipolatore di oggetti in MRTK
author: thalbern
ms.author: bethalha
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, manipolazione degli oggetti,
ms.openlocfilehash: 19cea7bf3cc74ba7936a9eeca624f681043db53fc3776c6c84aadfd2a2e6da01
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115202611"
---
# <a name="object-manipulator"></a>Manipolatore di oggetti

![Manipolatore di oggetti](../images/manipulation-handler/MRTK_Manipulation_Main.png)

*ObjectManipulator è il* nuovo componente per il comportamento di manipolazione, disponibile in precedenza in *ManipulationHandler.* Il manipolatore di oggetti apporta una serie di miglioramenti e semplificazioni. Questo componente è una sostituzione per il gestore di manipolazione, che verrà deprecato.

Lo script *ObjectManipulator* rende un oggetto mobile, scalabile e rotabile usando una o due mani. Il manipolatore di oggetti può essere configurato per controllare il modo in cui l'oggetto risponderà a vari input. Lo script dovrebbe funzionare con la maggior parte delle forme di interazione, ad esempio HoloLens 2 mano articolata, raggi della mano HoloLens 2, HoloLens 1 sguardo fisso e movimenti e l'input del controller del movimento del visore VR immersive.

## <a name="how-to-use-the-object-manipulator"></a>Come usare il manipolatore di oggetti

Per usare il manipolatore di oggetti, aggiungere prima di tutto il `ObjectManipulator` componente script a un GameObject. Assicurarsi anche di aggiungere un collisore all'oggetto, corrispondente ai limiti afferrabili.

Per fare in modo che l'oggetto risponda all'input della mano quasi `NearInteractionGrabbable` articolato, aggiungere anche lo script .

Il comportamento fisico può essere abilitato per il manipolatore di oggetti aggiungendo un componente rigidbody all'oggetto. Il comportamento fisico abilitato con l'aggiunta di questo componente viene illustrato in modo più dettagliato in [*Fisica e collisioni.*](#physics-and-collisions)

Oltre a questo, la manipolazione può essere vincolata aggiungendo componenti [del vincolo di manipolazione](constraint-manager.md#transform-constraints) all'oggetto. Si tratta di componenti speciali che funzionano con la manipolazione e modificano in qualche modo il comportamento di manipolazione.

![Gestore di manipolazione](../images/object-manipulator/MRTK_ObjectManipulator_Howto.png)

## <a name="inspector-properties-and-fields"></a>Proprietà e campi del controllo

<img src="../images/object-manipulator/MRTK_ObjectManipulator_Structure.png" width="450" alt="Object Manipulator Structure">

### <a name="general-properties"></a>Proprietà generali

#### <a name="host-transform"></a>Trasformazione host

Trasformazione dell'oggetto che verrà modificato. Il valore predefinito è l'oggetto del componente.

#### <a name="manipulation-type"></a>Tipo di manipolazione

Specifica se l'oggetto può essere modificato usando una o due mani. Poiché questa proprietà è un flag, è possibile selezionare entrambe le opzioni.

- *One handed (Una mano):* abilita la manipolazione con una mano, se selezionata.
- Two handed (Due *mani):* abilita la manipolazione a due mani, se selezionata.

#### <a name="allow-far-manipulation"></a>Consenti manipolazione da lontano

Specifica se la manipolazione può essere eseguita usando l'interazione da lontano con i puntatori.

### <a name="one-handed-manipulation-properties"></a>Proprietà di manipolazione con una mano

#### <a name="one-hand-rotation-mode-near"></a>Modalità di rotazione a una mano vicina

Specifica il comportamento dell'oggetto quando viene afferrato con una mano vicina. Queste opzioni funzionano solo per le mani articolate.

- *Ruota intorno al centro dell'oggetto:* l'oggetto ruota usando la rotazione della mano, ma intorno al punto centrale dell'oggetto. L'oggetto apparirà meno spostato durante la rotazione, ma potrebbe esserci una sensazione di disconnessione tra la mano e l'oggetto. Più utile per l'interazione da lontano.
- *Ruotare intorno al punto di cattura:* ruotare l'oggetto con la mano intorno al punto di cattura tra il pollice e il dito indice. Dovrebbe essere come se l'oggetto fosse tenuto dalla mano.

#### <a name="one-hand-rotation-mode-far"></a>Modalità di rotazione a una mano da lontano

Specifica il comportamento dell'oggetto quando viene afferrato con una mano alla distanza. Queste opzioni funzionano solo per le mani articolate.

- *Ruotare intorno al centro dell'oggetto:* ruotare l'oggetto usando la rotazione della mano, ma intorno al punto centrale dell'oggetto. Utile per controllare a una distanza senza spostare il centro dell'oggetto durante la rotazione dell'oggetto.
- *Ruotare intorno al punto di afferrazione:* ruotare l'oggetto usando la rotazione della mano, ma intorno al punto di hit del raggio dell'indicatore di misura. Utile per l'ispezione.

### <a name="two-handed-manipulation-properties"></a>Proprietà di manipolazione a due mani

#### <a name="two-handed-manipulation-type"></a>Tipo di manipolazione a due mani

Specifica il modo in cui la manipolazione a due mani può trasformare un oggetto. Poiché questa proprietà è un flag, è possibile selezionare un numero qualsiasi di opzioni.

- *Move:* lo spostamento è consentito se selezionato.
- *Scalabilità:* il ridimensionamento è consentito se selezionato.
- *Ruota:* la rotazione è consentita se selezionata.

![Gestore di manipolazione](../images/manipulation-handler/MRTK_ManipulationHandler_TwoHanded.jpg)

### <a name="constraints"></a>Vincoli

#### <a name="enable-constraints"></a>Abilitare i vincoli

Questa impostazione abiliterà la gestione [vincoli collegata.](constraint-manager.md) Le modifiche di trasformazione verranno elaborate dai vincoli registrati nella gestione [vincoli selezionata.](constraint-manager.md)

#### <a name="constraint-manager"></a>Gestione vincoli

L'elenco a discesa consente di selezionare uno dei gestori [vincoli collegati.](constraint-manager.md) Il manipolatore di oggetti garantisce che sia [sempre collegato un](constraint-manager.md) gestore vincoli.
Si noti che più componenti dello stesso tipo verranno visualizzati con lo stesso nome in Unity. Per semplificare la distinzione tra più gestori vincoli nello stesso oggetto, nelle opzioni disponibili verrà visualizzato un hint per la configurazione della gestione vincoli selezionata (selezione manuale o automatica dei vincoli).

#### <a name="go-to-component"></a>Vai al componente

La selezione di Gestione vincoli viene fornita con *un pulsante Vai al* componente. Questo pulsante fa scorrere il controllo fino al componente selezionato in modo che possa essere configurato.

### <a name="physics"></a>Fisica

Impostazioni in questa sezione vengono visualizzati solo quando l'oggetto ha un componente RigidBody.

#### <a name="release-behavior"></a>Comportamento di rilascio

Specificare le proprietà fisiche che un oggetto modificato deve mantenere al momento del rilascio. Poiché questa proprietà è un flag, è possibile selezionare entrambe le opzioni.

- *Keep Velocity*(Mantieni velocità): quando l'oggetto viene rilasciato, se questa opzione è selezionata mantiene la velocità lineare.
- *Mantieni Angular velocità:* quando l'oggetto viene rilasciato, se questa opzione è selezionata, manterà la velocità angolare.

#### <a name="use-forces-for-near-manipulation"></a>Usare le forze per la manipolazione da vicino

Indica se le forze fisiche vengono usate per spostare l'oggetto durante l'esecuzione di manipolazioni vicine. Impostando questo valore *su false,* l'oggetto sarà più direttamente connesso alla mano dell'utente. L'impostazione di questa proprietà su *true* rispetta la massa e l'inerzia dell'oggetto, ma può sembrare che l'oggetto sia connesso tramite una spring. Il valore predefinito è *false*.

### <a name="smoothing"></a>Definizione di movimenti uniformi

#### <a name="smoothing-far"></a>Smussamento da lontano

Indica se la smussazione indipendente dalla frequenza dei fotogrammi è abilitata per le interazioni da lontano. L'arrotondamento di gran lunga è abilitato per impostazione predefinita.

#### <a name="smoothing-near"></a>Smussamento nelle vicinanze

Indica se la smussazione indipendente dalla frequenza dei fotogrammi è abilitata per le interazioni da vicino. La smussamento quasi è disabilitata per impostazione predefinita perché l'effetto può essere percepito come "disconnesso" dalla mano.

#### <a name="smoothing-active"></a>Smoothing attivo

Obsoleti e verranno rimossi in una versione futura. Le applicazioni devono usare SmoothingFar, SmoothingNear o una combinazione dei due.

#### <a name="move-lerp-time"></a>Tempo di spostamento del lerp

Quantità di smussamento da applicare al movimento. Smussamento di 0 significa nessuna smussamento. Il valore massimo indica che non viene apportata alcuna modifica al valore.

#### <a name="rotate-lerp-time"></a>Ruotare il tempo di lerp

Quantità di smussamento da applicare alla rotazione. Smussamento di 0 significa nessuna smussamento. Il valore massimo indica che non viene apportata alcuna modifica al valore.

#### <a name="scale-lerp-time"></a>Ridimensionare il tempo di lerp

Quantità di smussamento da applicare alla scala. Smussamento di 0 significa nessuna smussamento. Il valore massimo indica che non viene apportata alcuna modifica al valore.

### <a name="manipulation-events"></a>Eventi di manipolazione

Il gestore di manipolazione fornisce gli eventi seguenti:

- *OnManipulationStarted: generato* all'avvio della manipolazione.
- *OnManipulationEnded:* viene generato al termine della manipolazione.
- *OnHoverStarted:* viene attivato quando una mano/controller passa il puntatore del mouse sul manipolabile, vicino o lontano.
- *OnHoverEnded:* viene attivato quando una mano/controller sposta il puntatore del mouse sul manipolabile, vicino o lontano.

L'ordine di generazione degli eventi per la manipolazione è:

*OnHoverStarted*  ->  *OnManipulationStarted*  ->  *OnManipulationEnded*  ->  *OnHoverEnded*

Se non è presente alcuna manipolazione, si otterrà comunque un evento al passaggio del mouse con l'ordine di incendio seguente:

*OnHoverStarted*  ->  *OnHoverEnded*

## <a name="physics-and-collisions"></a>Fisica e collisioni

Il comportamento fisico può essere abilitato aggiungendo un componente rigidbody allo stesso oggetto di un manipolatore di oggetti. Non solo abilita la configurazione del comportamento [di rilascio](#release-behavior) precedente, ma abilita anche le collisioni. Senza un componente rigidbody, le collisioni non si comportano correttamente durante la manipolazione:

- Le collisioni tra un oggetto manipolato e un collisore statico (ad esempio un oggetto con un collisore ma senza rigidbody) non funzionano, l'oggetto manipolato passa direttamente attraverso il collisore statico senza essere interessato.
- Collisioni tra un oggetto modificato e un rigidbody (ad esempio un oggetto con un collisore e un rigidbody) causano una risposta di collisione al rigidbody, ma la risposta è jumpy e innaturale. Non esiste inoltre alcuna risposta di collisione sull'oggetto modificato.

Quando viene aggiunto un rigidbody, le collisioni dovrebbero funzionare correttamente.

### <a name="without-rigidbody"></a>Senza rigidbody

<img src="../images/object-manipulator/MRTK_PhysicsManipulation_NoRigidbody.gif" width="500" alt="No Rigid Body">

### <a name="with-rigidbody"></a>Con rigidbody

<img src="../images/object-manipulator/MRTK_PhysicsManipulation_Rigidbody.gif" width="500" alt="Rigid Body">

## <a name="elastics-experimental"></a>Elastics (sperimentale)

Gli elastici possono essere usati quando si modificano gli oggetti tramite il manipolatore di oggetti. Si noti che il [sistema elastico](../elastics/elastic-system.md) è ancora in stato sperimentale. Per abilitare gli elastici, collegare un componente di gestione elastici esistente oppure creare e collegare un nuovo gestore elastici tramite il `Add Elastics Manager` pulsante .

<img src="../images/bounds-control/MRTK_BoundsControl_Elastics.png" width="450" alt="Bounds Control Elastics">

## <a name="see-also"></a>Vedi anche

- [Controllo Limiti](bounds-control.md)
- [Gestione vincoli](constraint-manager.md)
- [Finestra di migrazione](../tools/migration-window.md)
- [Sistema elastico (sperimentale)](../elastics/elastic-system.md)

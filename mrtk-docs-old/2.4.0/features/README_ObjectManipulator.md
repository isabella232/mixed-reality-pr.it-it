---
title: README_ObjectManipulator
description: Come usare il manipolatore di oggetti in MRTK
author: thalbern
ms.author: bethalha
ms.date: 01/12/2021
ms.localizationpriority: medium
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, manipolazione degli oggetti,
ms.openlocfilehash: c09371a9a4abe425065eca008efb08295a952bce
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2021
ms.locfileid: "104684254"
---
# <a name="object-manipulator"></a>Manipolatore di oggetti

![Manipolatore oggetto principale](Images/ManipulationHandler/MRTK_Manipulation_Main.png)

*ObjectManipulator* è il nuovo componente per il comportamento di manipolazione, disponibile in precedenza in *ManipulationHandler*. Il manipolatore di oggetti apporta diversi miglioramenti e semplificazioni. Questo componente sostituisce il gestore di manipolazione, che verrà deprecato.

Lo script *ObjectManipulator* rende un oggetto mobile, scalabile e girevole usando uno o due mani. Il manipolatore di oggetti può essere configurato per controllare la modalità di risposta dell'oggetto a diversi input. Lo script dovrebbe funzionare con la maggior parte delle forme di interazione, ad esempio HoloLens 2, a mano articolata, HoloLens 2, raggi mano, HoloLens 1 sguardo e movimenti e input del controller di movimento dell'auricolare.

## <a name="how-to-use-the-object-manipulator"></a>Come utilizzare il manipolatore di oggetti

Per usare il manipolatore di oggetti, aggiungere prima il `ObjectManipulator` componente script a un GameObject. Assicurarsi di aggiungere anche un Collider all'oggetto, associando i relativi limiti afferrabili.

Per fare in modo che l'oggetto risponda all'input della mano quasi articolato, aggiungere `NearInteractionGrabbable` anche lo script.

Il comportamento fisico può essere abilitato per il manipolatore di oggetti aggiungendo un componente rigidbody all'oggetto. Il comportamento fisico abilitato aggiungendo questo componente viene discusso in modo più dettagliato in [*fisica e collisioni*](#physics-and-collisions).

Inoltre, la manipolazione può essere vincolata dall'aggiunta di componenti di [vincoli di manipolazione](#transform-constraints) all'oggetto. Si tratta di componenti speciali che funzionano con la manipolazione e modificano in qualche modo il comportamento di manipolazione.

![Gestore di manipolazione](Images/ObjectManipulator/MRTK_ObjectManipulator_Howto.png)

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

![Gestore di manipolazione](Images/ManipulationHandler/MRTK_ManipulationHandler_TwoHanded.jpg)

### <a name="constraints"></a>Vincoli

#### <a name="add-constraint"></a>Aggiungi vincolo

Questo pulsante consente di aggiungere un componente vincolo direttamente dal controllo del manipolatore di oggetti. Tutti i vincoli in un progetto devono essere visibili qui. Per altre informazioni, vedere [vincoli Transform](#transform-constraints) .

#### <a name="go-to-component"></a>Vai al componente

Tutti i vincoli trovati nell'oggetto verranno elencati qui con un pulsante *Vai al componente* . Questo pulsante farà sì che il controllo scorra fino al componente del vincolo selezionato, in modo che possa essere configurato.

### <a name="physics"></a>Fisica

#### <a name="release-behavior"></a>Comportamento della versione

Specificare le proprietà fisiche che un oggetto modificato deve tenere al rilascio. Richiede che un componente rigidbody sia su tale oggetto. Poiché questa proprietà è un flag, è possibile selezionare entrambe le opzioni.

- *Mantieni velocità*: quando l'oggetto viene rilasciato, se questa opzione è selezionata, manterrà la velocità lineare.
- *Mantieni velocità angolare*: quando l'oggetto viene rilasciato, se questa opzione è selezionata, manterrà la velocità angolare.

### <a name="smoothing"></a>Definizione di movimenti uniformi

#### <a name="smoothing-active"></a>Smoothing attivo

Specifica se la smussatura è attiva.

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

## <a name="transform-constraints"></a>Vincoli di trasformazione

I vincoli possono essere usati per limitare la manipolazione in qualche modo. Ad esempio, alcune applicazioni possono richiedere la rotazione, ma richiedono anche che l'oggetto rimanga verticale. In questo caso, `RotationAxisConstraint` è possibile aggiungere un oggetto all'oggetto e usarlo per limitare la rotazione alla rotazione dell'asse y. MRTK fornisce una serie di vincoli, tutti descritti di seguito.

È anche possibile definire nuovi vincoli e usarli per creare un comportamento di manipolazione univoco che potrebbe essere necessario per alcune applicazioni. A tale scopo, creare uno script che erediti da [`TransformConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.TransformConstraint) e implementi la `ConstraintType` proprietà abstract e il `ApplyConstraint` metodo abstract. Quando si aggiunge un nuovo vincolo all'oggetto, è necessario vincolare la manipolazione nel modo in cui è stato definito. Questo nuovo vincolo dovrebbe essere visualizzato anche nei campi del [vincolo](#constraints)del manipolatore di oggetti.

Tutti i vincoli forniti da MRTK condividono le proprietà seguenti:

#### <a name="target-transform"></a>Trasformazione destinazione

Trasformazione dell'oggetto modificato sottoposto a vincoli. Deve corrispondere alla [*trasformazione dell'host*](#host-transform)ObjectManipulator. Il valore predefinito è l'oggetto del componente.

#### <a name="hand-type"></a>Tipo di mano

Specifica se il vincolo viene utilizzato per una sola mano, due o entrambi i tipi di manipolazione. Poiché questa proprietà è un flag, è possibile selezionare entrambe le opzioni.

- *Una sola mano*: il vincolo verrà usato durante una manipolazione gestita, se selezionato.
- *Due passate*: il vincolo verrà usato durante due manipolazioni gestite, se selezionato.

#### <a name="proximity-type"></a>Tipo di prossimità

Specifica se il vincolo viene utilizzato per i tipi di manipolazione near, di gran lunga o entrambi. Poiché questa proprietà è un flag, è possibile selezionare entrambe le opzioni.

- *Near*: il vincolo verrà usato in prossimità della manipolazione, se selezionato.
- *Lontano*: il vincolo verrà usato durante la manipolazione di gran lunga se selezionato.

### <a name="faceuserconstraint"></a>FaceUserConstraint

<img src="Images/ObjectManipulator/MRTK_Constraint_FaceUser.gif" width="400" alt="Constraint face user">

Quando questo vincolo è associato a un oggetto, la rotazione sarà limitata in modo che l'oggetto faccia sempre fronte all'utente. Questa operazione è utile per gli slate o i pannelli. Le proprietà per `FaceUserConstraint` sono le seguenti:

#### <a name="face-away"></a>Faccia fuori

L'oggetto viene rivolto dall'utente se true.

### <a name="fixeddistanceconstraint"></a>FixedDistanceConstraint

<img src="Images/ObjectManipulator/MRTK_Constraint_FixedDistance.gif" width="400" alt="constraintt fixed distance">

Questo vincolo corregge la distanza tra l'oggetto modificato e un'altra trasformazione dell'oggetto all'avvio della manipolazione. Questa operazione è utile per comportamenti come la correzione della distanza dall'oggetto modificato alla trasformazione Head. Le proprietà per `FixedDistanceConstraint` sono le seguenti:

#### <a name="constraint-transform"></a>Trasformazione vincolo

Si tratta dell'altra trasformazione a cui l'oggetto modificato avrà una distanza fissa. Il valore predefinito è la trasformazione della fotocamera.

### <a name="fixedrotationtouserconstraint"></a>FixedRotationToUserConstraint

<img src="Images/ObjectManipulator/MRTK_Constraint_FixedRotationToUser.gif" width="400" alt="Fixed rotation to user">

Questo vincolo corregge la rotazione relativa tra l'utente e l'oggetto modificato durante la manipolazione. Questa operazione è utile per gli slate o i pannelli, in quanto assicura che l'oggetto modificato mostri sempre lo stesso aspetto all'utente, così come è stato fatto all'inizio della manipolazione. Non `FixedRotationToUserConstraint` dispone di proprietà univoche.

### <a name="fixedrotationtoworldconstraint"></a>FixedRotationToWorldConstraint

<img src="Images/ObjectManipulator/MRTK_Constraint_FixedRotationToWorld.gif" width="400" alt="Fixed rotation to world">

Questo vincolo corregge la rotazione globale dell'oggetto modificato durante la manipolazione. Questa operazione può essere utile nei casi in cui non è necessario che la rotazione venga ripartita dalla manipolazione. Non `FixedRotationToWorldConstraint` dispone di proprietà univoche:

### <a name="maintainapparentsizeconstraint"></a>MaintainApparentSizeConstraint

<img src="Images/ObjectManipulator/MRTK_Constraint_MaintainApparentSize.gif" width="400" alt="Maintain Apparent Size">

Quando questo vincolo è associato a un oggetto, indipendentemente dalla distanza dell'oggetto dall'utente, manterrà le stesse dimensioni apparenti per l'utente (ad esempio, prenderà la stessa proporzione del campo di visualizzazione dell'utente). Questa operazione può essere utilizzata per garantire che uno Slate o un pannello di testo rimanga leggibile durante la manipolazione. Non `MaintainApparentSizeConstraint` dispone di proprietà univoche:

### <a name="moveaxisconstraint"></a>MoveAxisConstraint

<img src="Images/ObjectManipulator/MRTK_Constraint_MoveAxis.gif" width="400" alt="Constraint Move Axis">

Questo vincolo può essere usato per correggere gli assi che possono essere spostati in un oggetto modificato. Questa operazione può essere utile per la modifica degli oggetti sulla superficie di un piano o lungo una linea. Le proprietà per `MoveAxisConstraint` sono le seguenti:

#### <a name="constraint-on-movement"></a>Vincolo durante lo spostamento

Specifica gli assi su cui impedire lo spostamento. Per impostazione predefinita, questi assi saranno globali anziché locali, ma è possibile modificarli sotto. Poiché questa proprietà è un flag, è possibile selezionare qualsiasi numero di opzioni.

- *Asse x*: se selezionato, lo spostamento lungo l'asse x è vincolato.
- *Asse y*: se selezionato, lo spostamento lungo l'asse y è vincolato.
- *Asse z*: lo spostamento lungo l'asse z è vincolato se selezionato.

#### <a name="use-local-space-for-constraint"></a>Usa spazio locale per il vincolo

Vincola gli assi di trasformazione locali dell'oggetto modificato se true. False per impostazione predefinita.

### <a name="rotationaxisconstraint"></a>RotationAxisConstraint

<img src="Images/ObjectManipulator/MRTK_Constraint_RotationAxis.gif" width="400" alt="Constraint Rotation Axis">

Questo vincolo può essere usato per correggere gli assi che possono essere ruotati da un oggetto modificato. Questa operazione può essere utile per mantenere un oggetto manipolato verticalmente, ma che consente comunque di ruotare gli assi y, ad esempio. Le proprietà per `RotationAxisConstraint` sono le seguenti:

#### <a name="constraint-on-rotation"></a>Vincolo alla rotazione

Specifica gli assi per i quali impedire la rotazione. Per impostazione predefinita, questi assi saranno globali anziché locali, ma è possibile modificarli sotto. Poiché questa proprietà è un flag, è possibile selezionare qualsiasi numero di opzioni.

- *Asse y*: la rotazione sull'asse y è vincolata se selezionata.
- *Asse z*: la rotazione sull'asse z è vincolata se selezionata.
- *Asse x*: la rotazione sull'asse x è vincolata se selezionata.

#### <a name="use-local-space-for-constraint"></a>Usa spazio locale per il vincolo

Vincola gli assi di trasformazione locali dell'oggetto modificato se true. False per impostazione predefinita.

### <a name="minmaxscaleconstraint"></a>MinMaxScaleConstraint

<img src="Images/ObjectManipulator/MRTK_Constraint_MinMaxScale.gif" width="400" alt="MinMax Scale">

Questo vincolo consente di impostare i valori minimo e massimo per la scala dell'oggetto modificato. Questa operazione è utile per impedire agli utenti di ridimensionare un oggetto troppo piccolo o troppo grande. Le proprietà per `MinMaxScaleConstraint` sono le seguenti:

#### <a name="scale-minimum"></a>Dimensioni minime

Valore di scala minimo durante la manipolazione.

#### <a name="scale-maximum"></a>Scalabilità massima

Valore di scala massimo durante la manipolazione.

#### <a name="relative-to-initial-state"></a>Relativo allo stato iniziale

Se true, i valori precedenti verranno interpretati come relativi alla scala iniziale degli oggetti. In caso contrario, verranno interpretati come valori di scala assoluti.

## <a name="physics-and-collisions"></a>Fisica e collisioni

Il comportamento fisico può essere abilitato aggiungendo un componente rigidbody allo stesso oggetto di un manipolatore di oggetti. Non solo questa operazione Abilita la configurazione del [comportamento di rilascio](#release-behavior) precedente, inoltre consente conflitti. Senza un componente rigidbody, i conflitti non si comportano correttamente durante la manipolazione:

- I conflitti tra un oggetto modificato e un Collider statico (ovvero un oggetto con un Collider ma nessun rigidbody) non funzionano, l'oggetto modificato passa direttamente attraverso il Collider statico senza effetti.
- Collisioni tra un oggetto modificato e un rigidbody (ad esempio un oggetto con un Collider e un rigidbody) fa sì che rigidbody abbia una risposta di collisione, ma la risposta è inattiva e non naturale. Non esiste inoltre alcuna risposta di collisione sull'oggetto modificato.

Quando viene aggiunto un rigidbody, i conflitti dovrebbero funzionare correttamente.

### <a name="without-rigidbody"></a>Senza rigidbody

<img src="Images/ObjectManipulator/MRTK_PhysicsManipulation_NoRigidbody.gif" width="500" alt="No Rigid Body">

### <a name="with-rigidbody"></a>Con rigidbody

<img src="Images/ObjectManipulator/MRTK_PhysicsManipulation_Rigidbody.gif" width="500" alt="Rigid Body">

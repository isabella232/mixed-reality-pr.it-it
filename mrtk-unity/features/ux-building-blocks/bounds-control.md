---
title: Controllo Limiti
description: Panoramica sul controllo Bounds in MRTK
author: thalbern
ms.author: bethalha
ms.date: 01/12/2021
keywords: Unity,HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, controllo dei limiti,
ms.openlocfilehash: 3abefd142753c34c9126d71cde77ebca0b40f1f9b7a81b5815777b9e938e172a
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115217184"
---
# <a name="bounds-control"></a>Controllo Limiti

![Controllo Limiti](../images/bounds-control/MRTK_BoundsControl_Main.png)

*BoundsControl è* il nuovo componente per il comportamento di manipolazione, disponibile in precedenza in *BoundingBox*. Il controllo limiti apporta una serie di miglioramenti e semplificazioni nella configurazione e aggiunge nuove funzionalità. Questo componente è una sostituzione del rettangolo di selezione, che verrà deprecato.

Lo [`BoundsControl.cs`](xref:Microsoft.MixedReality.Toolkit.UI.BoundsControl) script fornisce funzionalità di base per la trasformazione di oggetti in realtà mista. Un controllo limiti visualizza una casella intorno all'ologramma per indicare che è possibile interagire con esso. I quadratini di ridimensionamento sugli angoli e sui bordi della casella consentono di ridimensionare, ruotare o tradurre l'oggetto. Il controllo dei limiti reagisce anche all'input dell'utente. In HoloLens 2, ad esempio, il controllo limiti risponde alla prossimità delle dita, fornendo un feedback visivo che consente di percepire la distanza dall'oggetto. Tutte le interazioni e gli oggetti visivi possono essere facilmente personalizzati.

## <a name="example-scene"></a>Scena di esempio

Nella scena sono disponibili esempi di configurazioni di controllo dei `BoundsControlExamples` limiti.

<img src="../images/bounds-control/MRTK_BoundsControl_Examples.png" alt="Bounds control Example">

## <a name="inspector-properties"></a>Proprietà del controllo

### <a name="target-object"></a>Oggetti di destinazione

Questa proprietà specifica quale oggetto verrà trasformato dalla manipolazione del controllo dei limiti. Se non è impostato alcun oggetto, per impostazione predefinita viene utilizzato l'oggetto proprietario.

### <a name="activation-behavior"></a>Comportamento di attivazione

Sono disponibili diverse opzioni per attivare l'interfaccia di controllo dei limiti.

* *Attiva all'avvio:* il controllo Limiti diventa visibile all'avvio della scena.
* *Attiva per prossimità:* il controllo Limiti diventa visibile quando una mano articolata è vicina all'oggetto.
* *Attiva per puntatore:* il controllo Limiti diventa visibile quando è destinato a un puntatore a raggi della mano.
* *Attiva per prossimità e* puntatore: il controllo Limiti diventa visibile quando è destinato a un puntatore a raggi della mano o una mano articolata è vicina all'oggetto.
* *Attiva manualmente:* il controllo Limiti non diventa visibile automaticamente. È possibile attivarlo manualmente tramite uno script accedendo alla proprietà boundsControl.Active.

### <a name="bounds-override"></a>Override dei limiti

Imposta un collisore di box dall'oggetto per il calcolo dei limiti.

### <a name="box-padding"></a>Riempimento della casella

Aggiunge una spaziatura interna ai limiti del collisore utilizzata per calcolare gli extent del controllo. Ciò influirà non solo sull'interazione, ma anche sugli oggetti visivi.

### <a name="flatten-axis"></a>Appiattire l'asse

Indica se il controllo è appiattito in uno degli assi, rendendolo 2 dimensionale e non consentire la manipolazione lungo tale asse. Questa funzionalità può essere usata per oggetti sottili come ardesia.
Se l'opzione Flatten axis è impostata su *Flatten Auto,* lo script selezionerà automaticamente l'asse con l'estensione più piccola come asse appiattito.

### <a name="smoothing"></a>Definizione di movimenti uniformi

La sezione smoothing consente di configurare il comportamento di smoothing per la scala e la rotazione del controllo.

### <a name="visuals"></a>Oggetti visivi

L'aspetto del controllo dei limiti può essere configurato modificando una delle configurazioni degli oggetti visivi corrispondenti.
Le configurazioni visive sono oggetti collegati o inline che possono essere creati tramite script e sono descritte in modo più dettagliato nella sezione [dell'oggetto di configurazione](#configuration-objects).

## <a name="configuration-objects"></a>Oggetti di configurazione

Il controllo include un set di oggetti di configurazione che possono essere archiviati come oggetti con script e condivisi tra istanze o prefab diversi. Le configurazioni possono essere condivise e collegate come singoli file di asset modificabili tramite script o asset annidati che possono essere script all'interno di prefab. È anche possibile definire altre configurazioni direttamente nell'istanza senza collegarsi a un asset esterno o annidabile tramite script.

Il controllo dei limiti indicherà se una configurazione è condivisa o inline come parte dell'istanza corrente visualizzando un messaggio nella finestra di ispezione proprietà. Inoltre, le istanze condivise non saranno modificabili direttamente nella finestra delle proprietà del controllo limiti, ma l'asset a cui si collega deve essere modificato direttamente per evitare modifiche accidentali nelle configurazioni condivise.

Attualmente il controllo dei limiti offre opzioni di oggetti di configurazione per le funzionalità seguenti:

* Selettori
  * [Quadratini di ridimensionamento](#scale-handles-configuration)
  * [Punti di manipolazione di rotazione](#rotation-handles-configuration)
  * [Handle di conversione](#translation-handles-configuration)
* [Collegamenti/Wireframe](#links-configuration-wireframe)
* [Visualizzazione della casella](#box-configuration)
* [Effetto prossimità](#proximity-effect-configuration)

### <a name="box-configuration"></a>Configurazione di Box

La configurazione della casella è responsabile del rendering di una casella a tinta unita con limiti definiti tramite la dimensione del collisore e la spaziatura interna della casella. È possibile configurare le proprietà seguenti:

* **Materiale della scatola:** definisce il materiale applicato alla casella sottoposta a rendering quando non viene applicata alcuna interazione. Il rendering di una casella verrà eseguito solo se questo materiale è impostato.
* **Materiale afferrato da box:** materiale per la scatola quando l'utente interagisce con il controllo afferrando tramite l'interazione vicina o lontana.
* **Scala di visualizzazione dell'asse** appiattito: scala applicata alla visualizzazione della casella se uno degli assi è [appiattito.](#flatten-axis)

### <a name="scale-handles-configuration"></a>Configurazione degli handle di scalabilità

Questo pannello delle proprietà consente di modificare il comportamento e la visualizzazione degli handle di scala del controllo dei limiti.

* **Materiale di gestione:** materiale applicato alle maniglie.
* **Maniglia materiale afferrato:** materiale applicato alla maniglia afferrata.
* **Handle prefab**: prefab facoltativo per l'handle di scala. Se non è impostata, MRTK userà un cubo come impostazione predefinita.
* **Handle size**: dimensione del quadratino di ridimensionamento.
* **Riempimento collisore:** spaziatura interna da aggiungere al collisore della maniglia.
* **Disegna tether durante la manipolazione:** quando attiva disegna una linea tether dal punto di inizio dell'interazione alla posizione corrente della mano o del puntatore.
* **Handle ignora collisore:** se un collisore viene collegato qui, gli handle ignoreranno qualsiasi collisione con questo collisore.
* **Handle slate prefab**: prefab da usare per l'handle quando il controllo viene appiattito.
* **Mostra handle di scala:** controlla la visibilità dell'handle.
* **Comportamento della scala:** può essere impostato su scala uniforme o non uniforme.

### <a name="rotation-handles-configuration"></a>Configurazione degli handle di rotazione

Questa configurazione definisce il comportamento dell'handle di rotazione.

* **Materiale di gestione:** materiale applicato alle maniglie.
* **Maniglia materiale afferrato:** materiale applicato alla maniglia afferrata.
* **Handle prefab**: prefab facoltativo per l'handle. Se non è impostata, MRTK userà una sfera come impostazione predefinita.
* **Dimensioni dell'handle:** dimensioni dell'handle.
* **Riempimento collisore:** spaziatura interna da aggiungere al collisore della maniglia.
* **Disegna tether durante la manipolazione:** quando attiva disegna una linea tether dal punto di inizio dell'interazione alla posizione corrente della mano o del puntatore.
* **Handle ignora collisore:** se un collisore viene collegato qui, gli handle ignoreranno qualsiasi collisione con questo collisore.
* **Gestire il tipo di collisore prefab:** tipo di collisore da usare con l'handle creato.
* **Mostra handle per X**: controlla la visibilità dell'handle per l'asse X.
* **Mostra handle per Y**: controlla la visibilità dell'handle per l'asse Y.
* **Mostra handle per Z**: controlla la visibilità dell'handle per l'asse Z.

### <a name="translation-handles-configuration"></a>Configurazione degli handle di conversione

Consente di abilitare e configurare gli handle di conversione per il controllo dei limiti. Si noti che gli handle di conversione sono disabilitati per impostazione predefinita.

* **Materiale di gestione:** materiale applicato alle maniglie.
* **Maniglia materiale afferrato:** materiale applicato alla maniglia afferrata.
* **Handle prefab**: prefab facoltativo per l'handle. Se non è impostata, MRTK userà una sfera come impostazione predefinita.
* **Dimensioni dell'handle:** dimensioni dell'handle.
* **Riempimento collisore:** spaziatura interna da aggiungere al collisore della maniglia.
* **Disegna tether durante la manipolazione:** quando attiva disegna una linea tether dal punto di inizio dell'interazione alla posizione corrente della mano o del puntatore.
* **Handle ignorano collisore:** se un collisore viene collegato qui, gli handle ignoreranno qualsiasi collisione con questo collisore.
* **Gestire il tipo di collisore prefab:** tipo di collisore da usare con l'handle creato.
* **Mostra handle per X:** controlla la visibilità dell'handle per l'asse X.
* **Mostra handle per Y:** controlla la visibilità dell'handle per l'asse Y.
* **Mostra handle per Z:** controlla la visibilità dell'handle per l'asse Z.

### <a name="links-configuration-wireframe"></a>Configurazione dei collegamenti (wireframe)

La configurazione dei collegamenti abilita la funzionalità wireframe del controllo dei limiti. È possibile configurare le proprietà seguenti:

* **Wireframe material (Materiale wireframe):** materiale applicato alla mesh wireframe.
* **Raggio bordo wireframe:** spessore del wireframe.
* **Forma wireframe:** la forma del wireframe può essere cubica o ciclica.
* **Mostra wireframe:** controlla la visibilità del wireframe.

### <a name="proximity-effect-configuration"></a>Configurazione dell'effetto di prossimità

Mostra e nasconde i quadratini di ridimensionamento con animazione in base alla distanza dalle mani. Include un'animazione in due passaggi per il ridimensionamento. I valori predefiniti sono impostati HoloLens 2 comportamento dello stile.

<img src="../images/bounds-control/MRTK_BoundsControl_Proximity.png" alt="Bounds control Proximity">

* **Effetto di prossimità attivo:** abilita l'attivazione dell'handle basata sulla prossimità
* **Prossimità media dell'oggetto:** distanza per il ridimensionamento del primo passaggio
* **Prossimità di chiusura dell'oggetto:** distanza per il ridimensionamento del secondo passaggio
* **Far Scale**(Scala da lontano): valore di scala predefinito dell'asset del punto di controllo quando le mani non sono in grado di interagire con il controllo dei limiti (distanza definita in precedenza da "Handle Medium Proximity" (Gestisci prossimità media). Usare 0 per nascondere l'handle per impostazione predefinita)
* **Scala media:** valore di scala dell'asset del punto di manipolazione quando le mani si trovano all'interno dell'intervallo dell'interazione di controllo dei limiti (distanza definita in precedenza da 'Handle Close Proximity'. Usare 1 per visualizzare le dimensioni normali
* **Close Scale (Scala** di chiusura): ridimensionare il valore dell'asset del punto di controllo quando le mani si trovano all'interno dell'intervallo dell'interazione di afferramento (distanza definita in precedenza da "Handle Close Proximity" (Gestisci prossimità di chiusura). Usare 1.x per visualizzare dimensioni maggiori)
* **Far Grow Rate (Velocità** di crescita da lontano): valuta la scalabilità di un oggetto con scala di prossimità quando la mano passa da una prossimità media a un'altra.
* **Velocità di crescita media:** valutare la scalabilità di un oggetto con scala di prossimità quando la mano passa da media a vicina.
* **Close Grow Rate (Frequenza** di crescita di chiusura): valuta la scala di un oggetto con scala di prossimità quando la mano si sposta dalla prossimità al centro dell'oggetto.

## <a name="constraint-system"></a>Sistema di vincoli

Il controllo limiti supporta l'uso di Gestione vincoli [per](constraint-manager.md) limitare o modificare il comportamento di traslazione, rotazione o ridimensionamento mentre si usano i punti di controllo dei limiti.

Il controllo proprietà mostrerà tutti i gestori vincoli disponibili collegati allo stesso oggetto gioco in un elenco a discesa con un'opzione per scorrere ed evidenziare il gestore vincoli selezionato.

<img src="../images/bounds-control/MRTK_BoundsControl_Constraints.png" width="450" alt="Bounds control Constraints">

## <a name="events"></a>Eventi

Il controllo Limiti fornisce gli eventi seguenti. Questo esempio usa questi eventi per riprodurre commenti e suggerimenti audio.

* **Rotate Started :** attivato all'avvio della rotazione.
* **Rotate Stopped (Ruota arrestata):** attivato quando la rotazione si arresta.
* **Ridimensionamento avviato:** viene generato all'avvio del ridimensionamento.
* **Ridimensionamento arrestato:** viene generato quando il ridimensionamento si arresta.
* **Translate Started**: viene generato all'avvio della traduzione.
* **Translate Stopped**(Traduci arrestato): viene generato all'arresto della traduzione.

<img src="../images/bounds-control/MRTK_BoundsControl_Events.png" width="450" alt="Bounds control Events">

## <a name="elastics-experimental"></a>Elastics (sperimentale)

Gli elastici possono essere usati quando si modificano gli oggetti tramite il controllo dei limiti. Si noti che il [sistema elastico](../experimental/elastic-system.md) è ancora in stato sperimentale. Per abilitare gli elastici, collegare un componente di gestione elastici esistente oppure creare e collegare un nuovo gestore elastici tramite il `Add Elastics Manager` pulsante .

<img src="../images/bounds-control/MRTK_BoundsControl_Elastics.png" width="450" alt="Bounds control Elastics">

## <a name="handle-styles"></a>Gestire gli stili

Per impostazione predefinita, quando si assegna solo lo script, verrà visualizzato [`BoundsControl.cs`](xref:Microsoft.MixedReality.Toolkit.UI.BoundsControl) l'handle HoloLens stile di prima generazione. Per usare i HoloLens 2 di stile, è necessario assegnare prefab e materiali di gestione adeguati.

![Stili dei quadratini di ridimensionamento del controllo Bounds 2](../images/bounds-control/MRTK_BoundsControl_HandleStyles1.png)

Di seguito sono riportati i prefab, i materiali e i valori di ridimensionamento per i punti HoloLens 2 di controllo dei limiti di stile. È possibile trovare questo esempio nella `BoundsControlExamples` scena .

<img src="../images/bounds-control/MRTK_BoundsControl_HandleStyles2.png" width="450" alt="Bounds control HandleStyles">

### <a name="handles-setup-for-hololens-2-style"></a>Handle (configurazione per lo HoloLens 2 personalizzato)

* **Handle Material**: BoundingBoxHandleWhite.mat
* **Handle Grabbed Material**:BoundingBoxHandleBlueGrabbed.mat
* **Prefab handle di scalabilità:** MRTK_BoundingBox_ScaleHandle.prefab
* **Scale Handle Slate Prefab**: MRTK_BoundingBox_ScaleHandle_Slate.prefab
* **Dimensioni handle di scala:** 0,016 (1,6 cm)
* **Scale Handle Collider Padding**:0.016 (rende il collisore afferrabile leggermente più grande dell'oggetto visivo handle)
* **Prefab handle di rotazione:** MRTK_BoundingBox_RotateHandle.prefab
* **Dimensioni handle di rotazione:** 0,016
* **Rotation Handle Collider Padding**:0.016 (rende il collisore afferrabile leggermente più grande dell'oggetto visivo handle)

## <a name="transformation-changes-with-object-manipulator"></a>Modifiche della trasformazione con il manipolatore di oggetti

Un controllo limiti può essere usato in combinazione con [`ObjectManipulator.cs`](object-manipulator.md) per consentire determinati tipi di manipolazione (ad esempio spostamento dell'oggetto) senza utilizzare handle. Il gestore di manipolazione supporta interazioni con una e due mani. [Il tracciamento](../input/hand-tracking.md) delle mani può essere usato per interagire con un oggetto da vicino.

<img src="../images/bounds-control/MRTK_BoundsControl_ObjectManipulator.png" width="450" alt="Bounds control Object Manipulator">

Per fare in modo che i bordi di controllo dei limiti si comportino allo stesso modo quando vengono spostati usando l'interazione da lontano di , è consigliabile connettere rispettivamente i relativi eventi per On Manipulation Started On Manipulation Ended a , come illustrato nello [`ObjectManipulator`](object-manipulator.md)   /   `BoundsControl.HighlightWires`  /  `BoundsControl.UnhighlightWires` screenshot precedente.

## <a name="how-to-add-and-configure-a-bounds-control-using-unity-inspector"></a>Come aggiungere e configurare un controllo limiti usando Unity Inspector

1. Aggiungere Box Collider a un oggetto
2. Assegnare `BoundsControl` uno script a un oggetto
3. Configurare le opzioni, ad esempio i metodi di attivazione (vedere la [sezione Proprietà di controllo](#inspector-properties) più avanti)
4. (Facoltativo) Assegnare prefab e materiali per un controllo HoloLens 2 limiti di stile personalizzati (vedere la sezione [Gestire gli stili più](#handle-styles) avanti)

> [!NOTE]
> Usare *il campo Target Object* (Oggetto di destinazione) e *Bounds Override (Override* limiti) nel controllo per assegnare oggetti e collisori specifici nell'oggetto con più componenti figlio.

![Controllo Bounds](../images/bounds-control/MRTK_BoundsControl_Assign.png)

## <a name="how-to-add-and-configure-a-bounds-control-in-the-code"></a>Come aggiungere e configurare un controllo limiti nel codice

1. Creare un'istanza del gameobject del cubo

    ```c#
    GameObject cube = GameObject.CreatePrimitive(PrimitiveType.Cube);
    ```

1. Assegnare `BoundsControl` uno script a un oggetto con collisore usando AddComponent<>()

    ```c#
    private BoundsControl boundsControl;
    boundsControl = cube.AddComponent<BoundsControl>();
    ```

1. Configurare le opzioni direttamente nel controllo o tramite una delle configurazioni che è possibile creare tramite script [(vedere](#inspector-properties) la sezione Proprietà e configurazioni del controllo [più](#configuration-objects) avanti)

    ```c#
    // Change activation method
    boundsControl.BoundsControlActivation = BoundsControlActivationType.ActivateByProximityAndPointer;
    // Make the scale handles large
    boundsControl.ScaleHandlesConfig.HandleSize = 0.1f;
    // Hide rotation handles for x axis
    boundsControl.RotationHandlesConfig.ShowRotationHandleForX = false;
    ```

1. (Facoltativo) Assegnare prefab e materiali per un controllo HoloLens 2 dei limiti dello stile. Questa operazione richiede comunque assegnazioni tramite il controllo perché i materiali e i prefab devono essere caricati dinamicamente.

> [!NOTE]
> Non è consigliabile usare la cartella 'Resources' di Unity o [Shader.Find]( https://docs.unity3d.com/ScriptReference/Shader.Find.html) per il caricamento dinamico degli shader, perché le permutazioni degli shader potrebbero non essere presenti in fase di esecuzione.

```c#
BoxDisplayConfiguration boxConfiguration = boundsControl.BoxDisplayConfig;
boxConfiguration.BoxMaterial = [Assign BoundingBox.mat]
boxConfiguration.BoxGrabbedMaterial = [Assign BoundingBoxGrabbed.mat]
ScaleHandlesConfiguration scaleHandleConfiguration = boundsControl.ScaleHandlesConfig;
scaleHandleConfiguration.HandleMaterial = [Assign BoundingBoxHandleWhite.mat]
scaleHandleConfiguration.HandleGrabbedMaterial = [Assign BoundingBoxHandleBlueGrabbed.mat]
scaleHandleConfiguration.HandlePrefab = [Assign MRTK_BoundingBox_ScaleHandle.prefab]
scaleHandleConfiguration.HandleSlatePrefab = [Assign MRTK_BoundingBox_ScaleHandle_Slate.prefab]
scaleHandleConfiguration.HandleSize = 0.016f;
scaleHandleConfiguration.ColliderPadding = 0.016f;
RotationHandlesConfiguration rotationHandleConfiguration = boundsControl.RotationHandlesConfig;
rotationHandleConfiguration.HandleMaterial = [Assign BoundingBoxHandleWhite.mat]
rotationHandleConfiguration.HandleGrabbedMaterial = [Assign BoundingBoxHandleBlueGrabbed.mat]
rotationHandleConfiguration.HandlePrefab = [Assign MRTK_BoundingBox_RotateHandle.prefab]
rotationHandleConfiguration.HandleSize = 0.016f;
rotationHandleConfiguration.ColliderPadding = 0.016f;
```

### <a name="example-set-minimum-maximum-bounds-control-scale-using-minmaxscaleconstraint"></a>Esempio: Impostare la scala di controllo dei limiti minimi e massimi usando MinMaxScaleConstraint

Per impostare la scala minima e massima, collegare [`MinMaxScaleConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.MinMaxScaleConstraint) un oggetto al controllo. Poiché il controllo limiti collega e attiva automaticamente la gestione vincoli, MinMaxScaleConstraint verrà applicato automaticamente alle modifiche della trasformazione dopo che è stato collegato e configurato.

È anche possibile usare MinMaxScaleConstraint per impostare la scala minima e massima per [`ObjectManipulator`](xref:Microsoft.MixedReality.Toolkit.UI.ObjectManipulator) .

```c#
GameObject cube = GameObject.CreatePrimitive(PrimitiveType.Cube);
bcontrol = cube.AddComponent<BoundsControl>();
// Important: BoundsControl creates a constraint manager on start if one does not exist.
// There's no need to manually attach a constraint manager.
MinMaxScaleConstraint scaleConstraint = bcontrol.gameObject.AddComponent<MinMaxScaleConstraint>();
scaleConstraint.ScaleMinimum = 1f;
scaleConstraint.ScaleMaximum = 2f;
```

## <a name="example-add-bounds-control-around-a-game-object"></a>Esempio: Aggiungere il controllo limiti intorno a un oggetto gioco

Per aggiungere un controllo limiti intorno a un oggetto, è sufficiente `BoundsControl` aggiungere un componente:

```c#
private void PutABoundsControlAroundIt(GameObject target)
{
   target.AddComponent<BoundsControl>();
}
```

## <a name="migrating-from-bounding-box"></a>Migrazione dal rettangolo di selezione

I prefab e [](bounding-box.md) le istanze esistenti che usano il rettangolo [](../tools/migration-window.md) di selezione possono essere aggiornati al nuovo controllo limiti tramite la finestra di migrazione che fa parte del pacchetto di strumenti MRTK.

Per l'aggiornamento di singole istanze del rettangolo di selezione è disponibile anche un'opzione di migrazione all'interno del controllo proprietà del componente.

<img src="../images/bounds-control/MRTK_BoundsControl_Migrate.png" width="450" alt="Bounds control Migrate">

## <a name="see-also"></a>Vedi anche

* [Manipolatore di oggetti](object-manipulator.md)
* [Gestione vincoli](constraint-manager.md)
* [Finestra di migrazione](../tools/migration-window.md)
* [Sistema elastico (sperimentale)](../experimental/elastic-system.md)

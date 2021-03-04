---
title: BoundsControl
description: Panoramica sul controllo dei limiti in MRTK
author: thalbern
ms.author: bethalha
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, controllo dei limiti,
ms.openlocfilehash: 56e2afd21ed7b3a70d3070eaac96abed939753b9
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/03/2021
ms.locfileid: "101781863"
---
# <a name="bounds-control"></a>Controllo dei limiti

![Controllo dei limiti](../images/bounds-control/MRTK_BoundsControl_Main.png)

*BoundsControl* è il nuovo componente per il comportamento di manipolazione, disponibile in precedenza in *BoundingBox*. Il controllo dei limiti apporta diversi miglioramenti e semplificazioni nell'installazione e aggiunge nuove funzionalità. Questo componente sostituisce il rettangolo di delimitazione, che verrà deprecato.

Lo [`BoundsControl.cs`](xref:Microsoft.MixedReality.Toolkit.UI.BoundsControl) script fornisce funzionalità di base per la trasformazione di oggetti in realtà mista. Un controllo Bounds visualizzerà una casella intorno all'ologramma per indicare che è possibile interagire con. Gli handle sugli angoli e sui bordi della casella consentono il ridimensionamento, la rotazione o la conversione dell'oggetto. Il controllo dei limiti reagisce anche all'input dell'utente. In HoloLens 2, ad esempio, il controllo dei limiti risponde alla prossimità del dito, fornendo commenti visivi per facilitare la percezione della distanza dall'oggetto. Tutte le interazioni e gli oggetti visivi possono essere facilmente personalizzati.

## <a name="example-scene"></a>Scena di esempio

È possibile trovare esempi di configurazioni di controllo dei limiti nella `BoundsControlExamples` scena.

<img src="../images/bounds-control/MRTK_BoundsControl_Examples.png" alt="Bounds control Example">

## <a name="inspector-properties"></a>Proprietà di Inspector

### <a name="target-object"></a>Oggetti di destinazione

Questa proprietà specifica quale oggetto verrà trasformato dalla manipolazione del controllo dei limiti. Se nessun oggetto è Setit, il valore predefinito è l'oggetto proprietario.

### <a name="activation-behavior"></a>Comportamento di attivazione

Sono disponibili diverse opzioni per attivare l'interfaccia di controllo dei limiti.

* *Attiva all'avvio*: il controllo dei limiti diventa visibile una volta avviata la scena.
* *Activate by prossimità*: il controllo dei limiti diventa visibile quando una mano articolata è vicina all'oggetto.
* *Activate by Pointer*: il controllo dei limiti diventa visibile quando è di destinazione di un puntatore di raggio.
* *Activate by prossimità e Pointer*: il controllo dei limiti diventa visibile quando è di destinazione di un puntatore a mano o una mano articolata è vicina all'oggetto.
* *Attiva manualmente*: il controllo dei limiti non diventa visibile automaticamente. È possibile attivarla manualmente tramite uno script accedendo alla proprietà boundsControl. Active.

### <a name="bounds-override"></a>Override dei limiti

Imposta un Collider di box dall'oggetto per il calcolo dei limiti.

### <a name="box-padding"></a>Riempimento Box

Aggiunge una spaziatura interna ai limiti del Collider utilizzati per calcolare gli extent del controllo. Questo influirà non solo sull'interazione, ma anche sugli oggetti visivi.

### <a name="flatten-axis"></a>Asse Flat

Indica se il controllo è bidimensionale in uno degli assi, rendendolo 2 dimensionale e non consente la manipolazione lungo tale asse. Questa funzionalità può essere usata per oggetti Thin come Slate.
Se l'asse appiattito è impostato su *appiattimento automatico* , lo script sceglierà automaticamente l'asse con l'extent più piccolo come asse bidimensionale.

### <a name="smoothing"></a>Definizione di movimenti uniformi

La sezione smoothing consente di configurare il comportamento di smussatura per la scala e la rotazione del controllo.

### <a name="visuals"></a>Oggetti visivi

L'aspetto del controllo dei limiti può essere configurato modificando una delle configurazioni degli oggetti visivi corrispondenti.
Le configurazioni visive sono oggetti collegati o con script inline e sono descritti in modo più dettagliato nella [sezione oggetto di configurazione](#configuration-objects).

## <a name="configuration-objects"></a>Oggetti di configurazione

Il controllo include un set di oggetti di configurazione che possono essere archiviati come oggetti configurabili tramite script e condivisi tra istanze diverse o prefabbricati. Le configurazioni possono essere condivise e collegate come singoli file di asset gestibili tramite script o asset annidabili tramite script all'interno di prefabbricati. È anche possibile definire altre configurazioni direttamente nell'istanza senza eseguire il collegamento a un asset con script esterno o annidato.

Il controllo dei limiti indicherà se una configurazione è condivisa o inline come parte dell'istanza corrente visualizzando un messaggio nel controllo proprietà. Inoltre, le istanze condivise non saranno modificabili direttamente nella finestra delle proprietà del controllo dei limiti, ma l'asset a cui è collegato deve essere direttamente modificati per evitare modifiche accidentali nelle configurazioni condivise.

Il controllo attualmente associato offre le opzioni degli oggetti di configurazione per le seguenti funzionalità:

* Selettori
  * [Quadratini di ridimensionamento](#scale-handles-configuration)
  * [Handle di rotazione](#rotation-handles-configuration)
  * [Handle di traduzione](#translation-handles-configuration)
* [Collegamenti/wireframe](#links-configuration-wireframe)
* [Visualizzazione box](#box-configuration)
* [Effetto di prossimità](#proximity-effect-configuration)

### <a name="box-configuration"></a>Configurazione box

La configurazione box è responsabile del rendering di una casella a tinta unita con i limiti definiti tramite le dimensioni del Collider e la spaziatura interna. È possibile configurare le proprietà seguenti:

* **Box Material**: definisce il materiale applicato alla casella di cui è stato eseguito il rendering quando non si verifica alcuna interazione. Se questo materiale è impostato, verrà eseguito il rendering di una casella.
* **Materiale afferrato da box**: materiale per la casella quando l'utente interagisce con il controllo afferrando un'interazione quasi o lontano.
* **Scala di visualizzazione dell'asse Flat**: una scala applicata alla casella viene visualizzata se uno degli assi è [bidimensionale](#flatten-axis).

### <a name="scale-handles-configuration"></a>Configurazione degli handle di scala

Questo cassetto delle proprietà consente di modificare il comportamento e la visualizzazione degli handle di ridimensionamento del controllo dei limiti.

* **Gestione materiale**: materiale applicato agli handle.
* **Gestire il materiale afferrato**: materiale applicato al punto di manipolazione.
* **Gestione prefabbricata**: precostruzione facoltativa per il quadratino di ridimensionamento. Se non è impostato, MRTK utilizzerà un cubo come predefinito.
* **Dimensioni handle**: dimensioni del quadratino di ridimensionamento.
* **Riempimento del Collider**: riempimento da aggiungere al Collider dell'handle.
* Crea il **tethering quando si modifica**: quando attivo crea una linea di tethering dal punto di inizio dell'interazione alla posizione corrente o al puntatore.
* **Handles ignora Collider**: se un Collider viene collegato qui, gli handle ignoreranno eventuali conflitti con questo Collider.
* **Gestire la prefabbricata dello Slate**: prefabbricato da usare per l'handle quando il controllo è bidimensionale.
* **Mostra quadratini di ridimensionamento**: controlla la visibilità dell'handle.
* **Comportamento della scalabilità**: può essere impostato su una scala uniforme o non uniforme.

### <a name="rotation-handles-configuration"></a>Configurazione handle di rotazione

Questa configurazione definisce il comportamento dell'handle di rotazione.

* **Gestione materiale**: materiale applicato agli handle.
* **Gestire il materiale afferrato**: materiale applicato al punto di manipolazione.
* **Gestisci prefabbricati**: precostruzione facoltativa per l'handle. Se non è impostato, MRTK utilizzerà una sfera come predefinita.
* **Dimensioni handle**: dimensioni dell'handle.
* **Riempimento del Collider**: riempimento da aggiungere al Collider dell'handle.
* Crea il **tethering quando si modifica**: quando attivo crea una linea di tethering dal punto di inizio dell'interazione alla posizione corrente o al puntatore.
* **Handles ignora Collider**: se un Collider viene collegato qui, gli handle ignoreranno eventuali conflitti con questo Collider.
* **Gestisci tipo di Collider prefabbricato**: tipo di Collider da usare con l'handle creato.
* **Mostra handle per x**: controlla la visibilità dell'handle per l'asse x.
* **Mostra handle per y**: controlla la visibilità dell'handle per l'asse y.
* **Mostra handle per z**: controlla la visibilità dell'handle per l'asse z.

### <a name="translation-handles-configuration"></a>Gestione della configurazione

Consente di abilitare e configurare gli handle di conversione per il controllo dei limiti. Si noti che gli handle di conversione sono disabilitati per impostazione predefinita.

* **Gestione materiale**: materiale applicato agli handle.
* **Gestire il materiale afferrato**: materiale applicato al punto di manipolazione.
* **Gestisci prefabbricati**: precostruzione facoltativa per l'handle. Se non è impostato, MRTK utilizzerà una sfera come predefinita.
* **Dimensioni handle**: dimensioni dell'handle.
* **Riempimento del Collider**: riempimento da aggiungere al Collider dell'handle.
* Crea il **tethering quando si modifica**: quando attivo crea una linea di tethering dal punto di inizio dell'interazione alla posizione corrente o al puntatore.
* **Handles ignora Collider**: se un Collider viene collegato qui, gli handle ignoreranno eventuali conflitti con questo Collider.
* **Gestisci tipo di Collider prefabbricato**: tipo di Collider da usare con l'handle creato.
* **Mostra handle per x**: controlla la visibilità dell'handle per l'asse x.
* **Mostra handle per y**: controlla la visibilità dell'handle per l'asse y.
* **Mostra handle per z**: controlla la visibilità dell'handle per l'asse z.

### <a name="links-configuration-wireframe"></a>Configurazione collegamenti (wireframe)

La configurazione dei collegamenti consente la funzionalità wireframe del controllo dei limiti. È possibile configurare le proprietà seguenti:

* **Wireframe Material**: materiale applicato alla mesh wireframe.
* **Raggio perimetrale wireframe**: spessore del wireframe.
* **Forma wireframe**: la forma del wireframe può essere cubica o cilindrica.
* **Mostra wireframe**: controlla la visibilità del wireframe.

### <a name="proximity-effect-configuration"></a>Configurazione degli effetti di prossimità

Mostra e nasconde gli handle con animazione in base alla distanza delle lancette. Ha un'animazione di ridimensionamento in due passaggi. Le impostazioni predefinite sono impostate sul comportamento dello stile HoloLens 2.

<img src="../images/bounds-control/MRTK_BoundsControl_Proximity.png" alt="Bounds control Proximity">

* **Effetto di prossimità attivo**: Abilita l'attivazione dell'handle basata sulla prossimità
* **Prossimità dell'oggetto**: distanza per il ridimensionamento del primo passaggio
* **Prossimità dell'oggetto**: distanza per la scala del secondo passaggio
* **Scalabilità orizzontale**: valore di scala predefinito dell'asset dell'handle quando le mani non rientrano nell'intervallo dell'interazione del controllo dei limiti (distanza definita in precedenza da' handle media prossimità'). Utilizzare 0 per nascondere l'handle per impostazione predefinita)
* **Scala media**: valore di scala dell'asset dell'handle quando le lancette sono comprese nell'intervallo di interazione del controllo dei limiti (distanza definita in precedenza da' handle Close prossimità'). Utilizzare 1 per mostrare le dimensioni normali)
* **Close scale**: valore di scala dell'asset dell'handle quando le lancette sono comprese nell'intervallo dell'interazione di cattura (distanza definita in precedenza da' handle Close prossimità'. Usare 1. x per visualizzare dimensioni maggiori)
* **Tasso di crescita molto** maggiore: la velocità di un oggetto con scalabilità di prossimità viene ridimensionata quando la mano passa da media a prossimità.
* **Velocità di crescita media**: la velocità di un oggetto con scalabilità ridotta viene ridimensionata quando la mano passa dalla prossimità media alla chiusura.
* **Frequenza di aumento delle dimensioni**: frequenza di ridimensionamento di un oggetto con scalabilità in caso di spostamento della mano da prossimità a centro oggetti.

## <a name="constraint-system"></a>Sistema di vincoli

Il controllo dei limiti supporta l'utilizzo di [Gestione vincoli](constraint-manager.md) per limitare o modificare il comportamento di conversione, rotazione o scalabilità durante l'utilizzo di handle di controllo dei limiti.

Il controllo proprietà mostrerà tutti i gestori di vincoli disponibili collegati allo stesso oggetto gioco in un elenco a discesa con un'opzione per scorrere ed evidenziare il gestore di vincoli selezionato.

<img src="../images/bounds-control/MRTK_BoundsControl_Constraints.png" width="450" alt="Bounds control Constraints">

## <a name="events"></a>Eventi

Il controllo dei limiti fornisce gli eventi seguenti. Questo esempio usa questi eventi per riprodurre commenti audio.

* **Rotazione avviata**: attivata all'avvio della rotazione.
* **Rotazione arrestata**: generata quando viene arrestata la rotazione.
* **Scale started**: viene attivato all'avvio del ridimensionamento.
* **Scale Stopped**: viene attivato quando si arresta il ridimensionamento.
* **Translate started**: viene attivato all'avvio della conversione.
* **Translate Stopped**: viene attivato quando la conversione viene arrestata.

<img src="../images/bounds-control/MRTK_BoundsControl_Events.png" width="450" alt="Bounds control Events">

## <a name="elastics-experimental"></a>Elastici (sperimentale)

Gli elastici possono essere usati per la manipolazione di oggetti tramite il controllo dei limiti. Si noti che il [sistema elastico](../elastics/elastic-system.md) è ancora in stato sperimentale. Per abilitare gli elastici, collegare un componente di gestione elastici esistente o creare e collegare un nuovo gestore elastici tramite il `Add Elastics Manager` pulsante.

<img src="../images/bounds-control/MRTK_BoundsControl_Elastics.png" width="450" alt="Bounds control Elastics">

## <a name="handle-styles"></a>Stili di gestione

Per impostazione predefinita, quando si assegna semplicemente lo [`BoundsControl.cs`](xref:Microsoft.MixedReality.Toolkit.UI.BoundsControl) script, verrà visualizzato l'handle dello stile HoloLens 1st Gen. Per usare gli handle di stile HoloLens 2, è necessario assegnare i materiali e i prefabbricati di handle appropriati.

![Stili di handle di controllo dei limiti 2](../images/bounds-control/MRTK_BoundsControl_HandleStyles1.png)

Di seguito sono riportati i prefabbricati, i materiali e i valori di ridimensionamento per gli handle di controllo dei limiti di stile HoloLens 2. Questo esempio è reperibile nella `BoundsControlExamples` scena.

<img src="../images/bounds-control/MRTK_BoundsControl_HandleStyles2.png" width="450" alt="Bounds control HandleStyles">

### <a name="handles-setup-for-hololens-2-style"></a>Handle (impostazione per lo stile HoloLens 2)

* **Gestione del materiale**: BoundingBoxHandleWhite. Mat
* **Gestire il materiale afferrato**: BoundingBoxHandleBlueGrabbed. Mat
* **Dimensioni prefabbricate del quadratino di ridimensionamento**: MRTK_BoundingBox_ScaleHandle
* **Ridimensionare il quadratino di tabulazione**: MRTK_BoundingBox_ScaleHandle_Slate. prefabbricate
* **Dimensioni del quadratino di ridimensionamento**: 0,016 (1,6 cm)
* **Riempimento del Collider del gestore di scalabilità**: 0,016 (rende l'oggetto Collider afferrabile leggermente più grande rispetto alla gestione degli oggetti visivi)
* **Maniglie prefabbricate di rotazione**: MRTK_BoundingBox_RotateHandle
* **Dimensioni handle di rotazione**: 0,016
* **Riempimento del Collider dell'handle di rotazione**: 0,016 (rende l'oggetto Collider afferrabile leggermente più grande rispetto alla gestione degli oggetti visivi)

## <a name="transformation-changes-with-object-manipulator"></a>Modifiche alla trasformazione con manipolatore oggetti

Un controllo Bounds può essere usato in combinazione con [`ObjectManipulator.cs`](object-manipulator.md) per consentire determinati tipi di manipolazione, ad esempio lo stato di un oggetto viene spostato senza utilizzare handle. Il gestore di manipolazione supporta entrambe le interazioni con una e due gestite. Il [rilevamento manuale](../input/hand-tracking.md) può essere usato per interagire con un oggetto alla chiusura.

<img src="../images/bounds-control/MRTK_BoundsControl_ObjectManipulator.png" width="450" alt="Bounds control Object Manipulator">

Affinché i bordi del controllo dei limiti si comportino allo stesso modo quando lo si trasferisce usando l' [`ObjectManipulator`](object-manipulator.md) interazione molto, si consiglia di connettere gli eventi per in fase di manipolazione *avviata* alla  /  *manipolazione* `BoundsControl.HighlightWires`  /  `BoundsControl.UnhighlightWires` rispettivamente, come illustrato nella schermata precedente.

## <a name="how-to-add-and-configure-a-bounds-control-using-unity-inspector"></a>Come aggiungere e configurare un controllo dei limiti con Unity Inspector

1. Aggiungi box Collider a un oggetto
2. Assegnare `BoundsControl` uno script a un oggetto
3. Configurare le opzioni, ad esempio i metodi di attivazione (vedere la sezione [proprietà di controllo](#inspector-properties) più avanti)
4. Opzionale Assegnare prefabbricati e materiali per un controllo dei limiti di stile HoloLens 2 (vedere la sezione [stili di handle](#handle-styles) riportata di seguito)

> [!NOTE]
> Utilizzare l' *oggetto di destinazione* e il campo di override dei *limiti* nel controllo per assegnare un oggetto e un Collider specifici nell'oggetto con più componenti figlio.

![Controllo dei limiti](../images/bounds-control/MRTK_BoundsControl_Assign.png)

## <a name="how-to-add-and-configure-a-bounds-control-in-the-code"></a>Come aggiungere e configurare un controllo dei limiti nel codice

1. Creare un'istanza del cubo GameObject

    ```c#
    GameObject cube = GameObject.CreatePrimitive(PrimitiveType.Cube);
    ```

1. Assegnare `BoundsControl` uno script a un oggetto con Collider, usando AddComponent<> ()

    ```c#
    private BoundsControl boundsControl;
    boundsControl = cube.AddComponent<BoundsControl>();
    ```

1. Configurare le opzioni direttamente nel controllo o tramite una delle configurazioni con script (vedere la sezione [Proprietà](#inspector-properties) e [configurazioni](#configuration-objects) di Inspector di seguito)

    ```c#
    // Change activation method
    boundsControl.BoundsControlActivation = BoundsControlActivationType.ActivateByProximityAndPointer;
    // Make the scale handles large
    boundsControl.ScaleHandlesConfig.HandleSize = 0.1f;
    // Hide rotation handles for x axis
    boundsControl.RotationHandlesConfig.ShowRotationHandleForX = false;
    ```

1. Opzionale Assegnare prefabbricati e materiali per un controllo dei limiti di stile HoloLens 2. Questa operazione richiede comunque le assegnazioni tramite il controllo, poiché i materiali e i prefabbricati devono essere caricati dinamicamente.

> [!NOTE]
> Uso della cartella ' Resources ' di Unity o dello [shader.]( https://docs.unity3d.com/ScriptReference/Shader.Find.html) non è consigliabile trovare per il caricamento dinamico degli shader perché le permutazioni dello shader potrebbero mancare in fase di esecuzione.

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

### <a name="example-set-minimum-maximum-bounds-control-scale-using-minmaxscaleconstraint"></a>Esempio: impostare la scala del controllo dei limiti minimo e massimo con MinMaxScaleConstraint

Per impostare la scala minima e massima, alleghi un [`MinMaxScaleConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.MinMaxScaleConstraint) al controllo. Poiché il controllo dei limiti collega automaticamente e attiva Gestione vincoli, il MinMaxScaleConstraint verrà automaticamente applicato alle modifiche della trasformazione dopo che è stato collegato e configurato.

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

## <a name="example-add-bounds-control-around-a-game-object"></a>Esempio: aggiungere un controllo Bounds intorno a un oggetto Game

Per aggiungere un controllo dei limiti intorno a un oggetto, è sufficiente aggiungervi un `BoundsControl` componente:

```c#
private void PutABoundsControlAroundIt(GameObject target)
{
   target.AddComponent<BoundsControl>();
}
```

## <a name="migrating-from-bounding-box"></a>Migrazione da un rettangolo di delimitazione

I prefissi e le istanze esistenti che usano il rettangolo di [delimitazione](bounding-box.md) possono essere aggiornati al nuovo controllo dei limiti tramite la [finestra di migrazione](../tools/migration-window.md) che fa parte del pacchetto di strumenti MRTK.

Per l'aggiornamento di singole istanze del rettangolo di delimitazione è disponibile anche un'opzione di migrazione all'interno del controllo proprietà del componente.

<img src="../images/bounds-control/MRTK_BoundsControl_Migrate.png" width="450" alt="Bounds control Migrate">

## <a name="see-also"></a>Vedi anche

* [Manipolatore di oggetti](object-manipulator.md)
* [Gestione vincoli](constraint-manager.md)
* [Finestra di migrazione](../tools/migration-window.md)
* [Sistema elastici (sperimentale)](../elastics/elastic-system.md)

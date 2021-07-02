---
title: Rettangolo di selezione
description: Panoramica di Bounding Box in MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, bounding box
ms.openlocfilehash: e8e3587ba871e127590a975b688a70db337daa19
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177546"
---
# <a name="bounding-box"></a>Rettangolo di selezione

![Rettangolo di selezione](../images/bounding-box/MRTK_BoundingBox_Main.png)

> [!NOTE]
> Il rettangolo di selezione è deprecato e sostituito dal relativo controllo [dei limiti successivo.](bounds-control.md) Usare [una delle opzioni di migrazione per](#migrating-to-bounds-control) aggiornare gli oggetti di gioco esistenti.

Lo [`BoundingBox.cs`](xref:Microsoft.MixedReality.Toolkit.UI.BoundingBox) script fornisce funzionalità di base per la trasformazione di oggetti in realtà mista. Un rettangolo di selezione mostrerà un cubo intorno all'ologramma per indicare che è possibile interagire con esso. Gli handle sugli angoli e sui bordi del cubo consentono di ridimensionare o ruotare l'oggetto. Il rettangolo di selezione reagisce anche all'input dell'utente. In HoloLens 2, ad esempio, il rettangolo di selezione risponde alla prossimità delle dita, fornendo un feedback visivo che consente di percepire la distanza dall'oggetto. Tutte le interazioni e gli oggetti visivi possono essere facilmente personalizzati.

Per altre informazioni, vedere [Rettangolo di selezione e Barra dell'app](/windows/mixed-reality/app-bar-and-bounding-box) nella Windows Dev Center.

## <a name="example-scene"></a>Scena di esempio

Nella scena sono disponibili esempi di configurazioni del rettangolo di `BoundingBoxExamples` selezione.

<img src="../images/bounding-box/MRTK_BoundingBox_Examples.png" alt="Bounding Box Examples">

## <a name="how-to-add-and-configure-a-bounding-box-using-unity-inspector"></a>Come aggiungere e configurare un rettangolo di selezione usando Unity Inspector

1. Aggiungere Box Collider a un oggetto
2. Assegnare `BoundingBox` uno script a un oggetto
3. Configurare opzioni, ad esempio i metodi di attivazione (vedere la [sezione Proprietà del controllo riportata](#inspector-properties) di seguito)
4. (Facoltativo) Assegnare prefab e materiali per un HoloLens 2 di selezione dello stile (vedere la sezione [Gestire gli stili](#handle-styles) più avanti)

> [!NOTE]
> Usare *il campo Target Object* e *Bounds Override* nel controllo per assegnare un oggetto specifico e un collisore nell'oggetto con più componenti figlio.

![Rettangolo di selezione 1](../images/bounding-box/MRTK_BoundingBox_Assign.png)

## <a name="how-to-add-and-configure-a-bounding-box-in-the-code"></a>Come aggiungere e configurare un rettangolo di selezione nel codice

1. Creare un'istanza del cubo GameObject

    ```c#
    GameObject cube = GameObject.CreatePrimitive(PrimitiveType.Cube);
    ```

1. Assegnare `BoundingBox` uno script a un oggetto con collisore usando AddComponent<>()

    ```c#
    private BoundingBox bbox;
    bbox = cube.AddComponent<BoundingBox>();
    ```

1. Configurare le opzioni (vedere la [sezione Proprietà del controllo riportata](#inspector-properties) di seguito)

    ```c#
    // Make the scale handles large
    bbox.ScaleHandleSize = 0.1f;
    // Hide rotation handles
    bbox.ShowRotationHandleForX = false;
    bbox.ShowRotationHandleForY = false;
    bbox.ShowRotationHandleForZ = false;
    ```

1. (Facoltativo) Assegnare prefab e materiali per un HoloLens 2 rettangolo di selezione dello stile. Ciò richiede comunque assegnazioni tramite il controllo poiché i materiali e i prefab devono essere caricati dinamicamente.

> [!NOTE]
> L'uso della cartella 'Resources' di [Unity o shader.Find]( https://docs.unity3d.com/ScriptReference/Shader.Find.html) per il caricamento dinamico degli shader non è consigliato perché le permutazioni dello shader potrebbero mancare in fase di esecuzione.

```c#
bbox.BoxMaterial = [Assign BoundingBox.mat]
bbox.BoxGrabbedMaterial = [Assign BoundingBoxGrabbed.mat]
bbox.HandleMaterial = [Assign BoundingBoxHandleWhite.mat]
bbox.HandleGrabbedMaterial = [Assign BoundingBoxHandleBlueGrabbed.mat]
bbox.ScaleHandlePrefab = [Assign MRTK_BoundingBox_ScaleHandle.prefab]
bbox.ScaleHandleSlatePrefab = [Assign MRTK_BoundingBox_ScaleHandle_Slate.prefab]
bbox.ScaleHandleSize = 0.016f;
bbox.ScaleHandleColliderPadding = 0.016f;
bbox.RotationHandleSlatePrefab = [Assign MRTK_BoundingBox_RotateHandle.prefab]
bbox.RotationHandleSize = 0.016f;
bbox.RotateHandleColliderPadding = 0.016f;
```

### <a name="example-set-minimum-maximum-bounding-box-scale-using-minmaxscaleconstraint"></a>Esempio: Impostare la scala minima e massima del rettangolo di selezione usando MinMaxScaleConstraint

Per impostare la scala minima e massima, usare [`MinMaxScaleConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.MinMaxScaleConstraint) . È anche possibile usare MinMaxScaleConstraint per impostare la scala minima e massima per [`ManipulationHandler`](xref:Microsoft.MixedReality.Toolkit.UI.ManipulationHandler) .

```c#
GameObject cube = GameObject.CreatePrimitive(PrimitiveType.Cube);
bbox = cube.AddComponent<BoundingBox>();
// Important: BoundingBox creates a scale handler on start if one does not exist
// do not use AddComponent, as that will create a  duplicate handler that will not be used
MinMaxScaleConstraint scaleConstraint = bbox.gameObject.GetComponent<MinMaxScaleConstraint>();
scaleConstraint.ScaleMinimum = 1f;
scaleConstraint.ScaleMaximum = 2f;
```

## <a name="example-add-bounding-box-around-a-game-object"></a>Esempio: Aggiungere un rettangolo di selezione intorno a un oggetto gioco

Per aggiungere un rettangolo di selezione intorno a un oggetto, è sufficiente aggiungere un `BoundingBox` componente:

```c#
private void PutABoxAroundIt(GameObject target)
{
   target.AddComponent<BoundingBox>();
}
```

## <a name="inspector-properties"></a>Proprietà del controllo

### <a name="target-object"></a>Oggetti di destinazione

Questa proprietà specifica quale oggetto verrà trasformato dalla manipolazione del rettangolo di selezione. Se non è impostato alcun oggetto, il rettangolo di selezione viene impostato per impostazione predefinita sull'oggetto proprietario.

### <a name="bounds-override"></a>Override dei limiti

Imposta un collisore di box dall'oggetto per il calcolo dei limiti.

### <a name="activation-behavior"></a>Comportamento di attivazione

Sono disponibili diverse opzioni per attivare l'interfaccia del rettangolo di selezione.

* *Attiva all'avvio:* il rettangolo di selezione diventa visibile dopo l'avvio della scena.
* *Attiva per prossimità:* il rettangolo di selezione diventa visibile quando una mano articolata è vicina all'oggetto.
* *Attiva per puntatore:* il rettangolo di selezione diventa visibile quando è destinato a un puntatore a raggi della mano.
* *Attiva manualmente:* il rettangolo di selezione non diventa visibile automaticamente. È possibile attivarlo manualmente tramite uno script accedendo alla proprietà boundingBox.Active.

### <a name="scale-minimum"></a>Scalabilità minima

Scala minima consentita. Questa proprietà è deprecata ed è preferibile aggiungere uno [`MinMaxScaleConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.MinMaxScaleConstraint) script. Se si aggiunge questo script, la scala minima verrà prelevata da esso anziché dal rettangolo di selezione.

### <a name="scale-maximum"></a>Scalabilità massima

Scala massima consentita. Questa proprietà è deprecata ed è preferibile aggiungere uno [`MinMaxScaleConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.MinMaxScaleConstraint) script. Se si aggiunge questo script, la scala massima verrà prelevata da esso anziché dal rettangolo di selezione.

### <a name="box-display"></a>Visualizzazione della casella

Varie opzioni di visualizzazione del rettangolo di selezione.

Se l'opzione Asse appiattimento è impostata su *Flatten Auto,* lo script non consente la manipolazione lungo l'asse con l'estensione più piccola. Il risultato è un rettangolo di selezione 2D, usato in genere per gli oggetti thin.

### <a name="handles"></a>Selettori

È possibile assegnare il materiale e il prefab per eseguire l'override dello stile dell'handle. Se non vengono assegnati handle, verranno visualizzati nello stile predefinito.

## <a name="events"></a>Eventi

Il rettangolo di selezione fornisce gli eventi seguenti. Questo esempio usa questi eventi per riprodurre commenti e suggerimenti audio.

* **Ruota avviata:** attivato all'avvio della rotazione.
* **Ruota terminata:** attivato al termine della rotazione.
* **Ridimensionamento avviato:** viene generato all'avvio del ridimensionamento.
* **Ridimensionamento terminato:** viene generato quando termina il ridimensionamento.

<img src="../images/bounding-box/MRTK_BoundingBox_Events.png" width="450" alt="Events">

## <a name="handle-styles"></a>Gestire gli stili

Per impostazione predefinita, quando si assegna solo lo script, verrà visualizzato l'handle del HoloLens [`BoundingBox.cs`](xref:Microsoft.MixedReality.Toolkit.UI.BoundingBox) di prima generazione. Per usare HoloLens 2 di stile, è necessario assegnare prefab e materiali di gestione adeguati.

![Stili dei quadratini di selezione](../images/bounding-box/MRTK_BoundingBox_HandleStyles1.png)

Di seguito sono riportati i prefab, i materiali e i valori di scala per i punti HoloLens 2 rettangolo di selezione dello stile. È possibile trovare questo esempio nella `BoundingBoxExamples` scena .

<img src="../images/bounding-box/MRTK_BoundingBox_HandleStyles2.png" width="450" alt="HandStyles 2">

### <a name="handles-setup-for-hololens-2-style"></a>Handle (configurazione per HoloLens 2 stile)

* **Handle Material**: BoundingBoxHandleWhite.mat
* **Handle Grabbed Material**: BoundingBoxHandleBlueGrabbed.mat
* **Prefab dell'handle** di scala: MRTK_BoundingBox_ScaleHandle.prefab
* **Scale Handle Slate Prefab**: MRTK_BoundingBox_ScaleHandle_Slate.prefab
* **Dimensioni dell'handle di** scala: 0,016 (1,6 cm)
* **Scale Handle Collider Padding**: 0,016 (rende il collisore afferrabile leggermente più grande dell'oggetto visivo handle)
* **Prefab dell'handle** di rotazione: MRTK_BoundingBox_RotateHandle.prefab
* **Dimensioni dell'handle di** rotazione: 0,016
* **Rotation Handle Collider Padding**: 0,016 (rende il collisore afferrabile leggermente più grande dell'oggetto visivo handle)

### <a name="proximity-setup-for-hololens-2-style"></a>Prossimità (configurazione per lo stile HoloLens 2)

Mostrare e nascondere i quadratini di ridimensionamento con l'animazione in base alla distanza dalle mani. Ha un'animazione in scala in due passaggi.

<img src="../images/bounding-box/MRTK_BoundingBox_Proximity.png" alt="Proximity">

* **Effetto di prossimità attivo:** abilitare l'attivazione dell'handle basato sulla prossimità
* **Gestire la prossimità media:** distanza per il ridimensionamento del primo passaggio
* **Gestire la prossimità di chiusura:** distanza per il ridimensionamento del secondo passaggio
* **Scalabilità estrema:** valore di scala predefinito dell'asset handle quando le mani non sono all'interno dell'intervallo dell'interazione del rettangolo di selezione (distanza definita in precedenza da 'Handle Medium Proximity'. Usare 0 per nascondere l'handle per impostazione predefinita)
* **Scala media:** valore di scala dell'asset handle quando le mani si trovano entro l'intervallo dell'interazione del rettangolo di selezione (distanza definita in precedenza da 'Handle Close Proximity'. Usare 1 per visualizzare le dimensioni normali)
* **Scala di chiusura:** ridimensionare il valore dell'asset handle quando le mani si trovano entro l'intervallo dell'interazione di afferramento (distanza definita in precedenza da 'Handle Close Proximity'. Usare 1.x per visualizzare dimensioni maggiori)

## <a name="making-an-object-movable-with-manipulation-handler"></a>Rendere mobile un oggetto con il gestore di manipolazione

Un rettangolo di selezione può essere combinato con [`ManipulationHandler.cs`](manipulation-handler.md) per rendere l'oggetto mobile usando l'interazione da lontano. Il gestore di manipolazione supporta interazioni con una e due mani. [Il tracciamento](../input/hand-tracking.md) delle mani può essere usato per interagire con un oggetto da vicino.

<img src="../images/bounding-box/MRTK_BoundingBox_ManipulationHandler.png" width="450" alt="Manipulation Handler">

Per fare in modo che i bordi del rettangolo di selezione si comportino allo stesso modo quando lo si sposta usando l'interazione da lontano di , è consigliabile connettere rispettivamente i relativi eventi per On Manipulation Started On Manipulation Ended a , come illustrato nello [`ManipulationHandler`](manipulation-handler.md)   /   `BoundingBox.HighlightWires`  /  `BoundingBox.UnhighlightWires` screenshot precedente.

## <a name="migrating-to-bounds-control"></a>Migrazione al controllo dei limiti

I prefab e [](bounding-box.md) le istanze esistenti che usano il rettangolo [](../tools/migration-window.md) di selezione possono essere aggiornati al nuovo controllo limiti tramite la finestra di migrazione che fa parte del pacchetto di strumenti MRTK.

Per l'aggiornamento di singole istanze del rettangolo di selezione è disponibile anche un'opzione di migrazione all'interno del controllo proprietà del componente.

<img src="../images/bounds-control/MRTK_BoundsControl_Migrate.png" width="450" alt="Bounds Control Migrate">

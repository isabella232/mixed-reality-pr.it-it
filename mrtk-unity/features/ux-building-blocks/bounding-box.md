---
title: Rettangolo di selezione
description: Panoramica del rettangolo di selezione in MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, rettangolo di selezione
ms.openlocfilehash: fa1ace9d7aaf547ee677accfc4254ce9c64aebdfa6a01f11962812b058bc9ceb
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115214213"
---
# <a name="bounding-box"></a>Rettangolo di selezione

![Rettangolo di selezione](../images/bounding-box/MRTK_BoundingBox_Main.png)

> [!NOTE]
> Il rettangolo di selezione è deprecato e sostituito dal controllo [dei limiti del successore](bounds-control.md). Usare [una delle opzioni di migrazione per aggiornare](#migrating-to-bounds-control) gli oggetti gioco esistenti.

Lo [`BoundingBox.cs`](xref:Microsoft.MixedReality.Toolkit.UI.BoundingBox) script fornisce funzionalità di base per la trasformazione di oggetti nella realtà mista. Un rettangolo di selezione mostrerà un cubo intorno all'ologramma per indicare che è possibile interagire con esso. Gli handle sugli angoli e sui bordi del cubo consentono di ridimensionare o ruotare l'oggetto. Il rettangolo di selezione reagisce anche all'input dell'utente. In HoloLens 2, ad esempio, il rettangolo di selezione risponde alla prossimità del dito, fornendo un feedback visivo che consente di cepire la distanza dall'oggetto. Tutte le interazioni e gli oggetti visivi possono essere facilmente personalizzati.

Per altre informazioni, vedere [Rettangolo di selezione e Barra dell'app](/windows/mixed-reality/app-bar-and-bounding-box) nella Windows Dev Center.

## <a name="example-scene"></a>Scena di esempio

È possibile trovare esempi di configurazioni del rettangolo di selezione nella `BoundingBoxExamples` scena.

<img src="../images/bounding-box/MRTK_BoundingBox_Examples.png" alt="Bounding Box Examples">

## <a name="how-to-add-and-configure-a-bounding-box-using-unity-inspector"></a>Come aggiungere e configurare un rettangolo di selezione con Unity Inspector

1. Aggiungere Box Collider a un oggetto
2. Assegnare `BoundingBox` uno script a un oggetto
3. Configurare le opzioni, ad esempio i metodi di attivazione (vedere la [sezione Proprietà di controllo](#inspector-properties) più avanti)
4. (Facoltativo) Assegnare prefab e materiali per un HoloLens 2 delimitatore di stile personalizzato (vedere la sezione [Gestire gli stili più](#handle-styles) avanti)

> [!NOTE]
> Usare *il campo Target Object* (Oggetto di destinazione) e *Bounds Override (Override* limiti) nel controllo per assegnare oggetti e collisori specifici nell'oggetto con più componenti figlio.

![Rettangolo di selezione 1](../images/bounding-box/MRTK_BoundingBox_Assign.png)

## <a name="how-to-add-and-configure-a-bounding-box-in-the-code"></a>Come aggiungere e configurare un rettangolo di selezione nel codice

1. Creare un'istanza del gameobject del cubo

    ```c#
    GameObject cube = GameObject.CreatePrimitive(PrimitiveType.Cube);
    ```

1. Assegnare `BoundingBox` uno script a un oggetto con collisore usando AddComponent<>()

    ```c#
    private BoundingBox bbox;
    bbox = cube.AddComponent<BoundingBox>();
    ```

1. Configurare le opzioni (vedere la [sezione Proprietà del controllo](#inspector-properties) più avanti)

    ```c#
    // Make the scale handles large
    bbox.ScaleHandleSize = 0.1f;
    // Hide rotation handles
    bbox.ShowRotationHandleForX = false;
    bbox.ShowRotationHandleForY = false;
    bbox.ShowRotationHandleForZ = false;
    ```

1. (Facoltativo) Assegnare prefab e materiali per un HoloLens 2 di selezione dello stile. Questa operazione richiede comunque assegnazioni tramite il controllo perché i materiali e i prefab devono essere caricati dinamicamente.

> [!NOTE]
> Non è consigliabile usare la cartella 'Resources' di Unity o [Shader.Find]( https://docs.unity3d.com/ScriptReference/Shader.Find.html) per il caricamento dinamico degli shader, perché le permutazioni degli shader potrebbero non essere presenti in fase di esecuzione.

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

Per impostare la scalabilità minima e massima, usare [`MinMaxScaleConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.MinMaxScaleConstraint) . È anche possibile usare MinMaxScaleConstraint per impostare la scala minima e massima per [`ManipulationHandler`](xref:Microsoft.MixedReality.Toolkit.UI.ManipulationHandler) .

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

Per aggiungere un rettangolo di selezione intorno a un oggetto, è sufficiente `BoundingBox` aggiungere un componente:

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
* *Attiva in base all'indicatore* di misura: il rettangolo di selezione diventa visibile quando è destinato a un indicatore di misura del raggio della mano.
* *Attiva manualmente:* il rettangolo di selezione non diventa visibile automaticamente. È possibile attivarlo manualmente tramite uno script accedendo alla proprietà boundingBox.Active.

### <a name="scale-minimum"></a>Scalabilità minima

Scala minima consentita. Questa proprietà è deprecata ed è preferibile aggiungere uno [`MinMaxScaleConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.MinMaxScaleConstraint) script. Se questo script viene aggiunto, verrà prelevata la scala minima anziché dal rettangolo di selezione.

### <a name="scale-maximum"></a>Scalabilità massima

Scala massima consentita. Questa proprietà è deprecata ed è preferibile aggiungere uno [`MinMaxScaleConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.MinMaxScaleConstraint) script. Se si aggiunge questo script, verrà prelevata la scala massima anziché dal rettangolo di selezione.

### <a name="box-display"></a>Visualizzazione della casella

Varie opzioni di visualizzazione del rettangolo di selezione.

Se l'opzione Flatten Axis (Appiatti asse) è impostata su *Flatten Auto*(Appiatti automaticamente), lo script non consente la manipolazione lungo l'asse con l'estensione più piccola. Il risultato è un rettangolo di selezione 2D, che viene in genere usato per gli oggetti thin.

### <a name="handles"></a>Selettori

È possibile assegnare il materiale e il prefab per eseguire l'override dello stile dell'handle. Se non viene assegnato alcun handle, verranno visualizzati nello stile predefinito.

## <a name="events"></a>Eventi

Il rettangolo di selezione fornisce gli eventi seguenti. Questo esempio usa questi eventi per riprodurre commenti e suggerimenti audio.

* **Rotate Started :** attivato all'avvio della rotazione.
* **Rotate Ended**: attivato al termine della rotazione.
* **Ridimensionamento avviato:** viene generato all'avvio del ridimensionamento.
* **Ridimensionamento terminato:** viene generato al termine del ridimensionamento.

<img src="../images/bounding-box/MRTK_BoundingBox_Events.png" width="450" alt="Events">

## <a name="handle-styles"></a>Gestire gli stili

Per impostazione predefinita, quando si assegna solo lo script, verrà visualizzato [`BoundingBox.cs`](xref:Microsoft.MixedReality.Toolkit.UI.BoundingBox) l'handle HoloLens stile di prima generazione. Per usare i HoloLens 2 di stile, è necessario assegnare prefab e materiali di gestione adeguati.

![Stili dei quadratini di selezione](../images/bounding-box/MRTK_BoundingBox_HandleStyles1.png)

Di seguito sono riportati i prefab, i materiali e i valori di ridimensionamento per i punti HoloLens 2 quadratini del rettangolo di selezione dello stile. È possibile trovare questo esempio nella `BoundingBoxExamples` scena .

<img src="../images/bounding-box/MRTK_BoundingBox_HandleStyles2.png" width="450" alt="HandStyles 2">

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

### <a name="proximity-setup-for-hololens-2-style"></a>Prossimità (configurazione per lo HoloLens 2 personalizzato)

Mostra e nasconde i quadratini di ridimensionamento con animazione in base alla distanza dalle mani. Include un'animazione in due passaggi per il ridimensionamento.

<img src="../images/bounding-box/MRTK_BoundingBox_Proximity.png" alt="Proximity">

* **Effetto di prossimità attivo:** abilita l'attivazione dell'handle basata sulla prossimità
* **Gestire la prossimità media:** distanza per il ridimensionamento del primo passaggio
* **Gestire la prossimità di chiusura:** distanza per il ridimensionamento del secondo passaggio
* **Far Scale**(Scala da lontano): valore di scala predefinito dell'asset del punto di manipolazione quando le mani non sono in grado di interagire con il rettangolo di selezione (distanza definita in precedenza da "Handle Medium Proximity" (Gestisci prossimità media). Usare 0 per nascondere l'handle per impostazione predefinita)
* **Scala media:** valore di scala dell'asset del punto di manipolazione quando le mani sono all'interno dell'intervallo dell'interazione del rettangolo di selezione (distanza definita in precedenza da 'Handle Close Proximity'. Usare 1 per visualizzare le dimensioni normali
* **Close Scale (Scala** di chiusura): ridimensionare il valore dell'asset del punto di controllo quando le mani si trovano all'interno dell'intervallo dell'interazione di afferramento (distanza definita in precedenza da "Handle Close Proximity" (Gestisci prossimità di chiusura). Usare 1.x per visualizzare dimensioni maggiori)

## <a name="making-an-object-movable-with-manipulation-handler"></a>Rendere mobile un oggetto con il gestore di manipolazione

Un rettangolo di selezione può essere combinato con [`ManipulationHandler.cs`](manipulation-handler.md) per rendere l'oggetto mobile usando l'interazione da lontano. Il gestore di manipolazione supporta entrambe le interazioni a una e a due mani. [Il tracciamento](../input/hand-tracking.md) manuale può essere usato per interagire con un oggetto da vicino.

<img src="../images/bounding-box/MRTK_BoundingBox_ManipulationHandler.png" width="450" alt="Manipulation Handler">

Per fare in modo che i bordi del rettangolo di selezione si comportino allo stesso modo quando lo si sposta usando [`ManipulationHandler`](manipulation-handler.md) l'interazione all'estrema distanza, è consigliabile connettere rispettivamente i relativi eventi per On *Manipulation Started*  /  *On Manipulation Ended* a, come illustrato nello `BoundingBox.HighlightWires`  /  `BoundingBox.UnhighlightWires` screenshot precedente.

## <a name="migrating-to-bounds-control"></a>Migrazione al controllo dei limiti

I prefab e le istanze esistenti che usano [il rettangolo](bounding-box.md) [](../tools/migration-window.md) di selezione possono essere aggiornati al nuovo controllo limiti tramite la finestra di migrazione che fa parte del pacchetto di strumenti MRTK.

Per l'aggiornamento di singole istanze del rettangolo di selezione è disponibile anche un'opzione di migrazione all'interno del controllo proprietà del componente.

<img src="../images/bounds-control/MRTK_BoundsControl_Migrate.png" width="450" alt="Bounds Control Migrate">

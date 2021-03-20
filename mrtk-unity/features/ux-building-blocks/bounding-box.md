---
title: BoundingBox
description: Panoramica sul riquadro delimitatore in MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, rettangolo di delimitazione
ms.openlocfilehash: 864432349d31c5d0e8b8032a7ed0939e345521df
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2021
ms.locfileid: "104702257"
---
# <a name="bounding-box"></a>Rettangolo di selezione

![Rettangolo di selezione](../images/bounding-box/MRTK_BoundingBox_Main.png)

> [!NOTE]
> Il rettangolo di delimitazione è deprecato e sostituito dal [controllo dei limiti](bounds-control.md)successivi. Usare [una delle opzioni di migrazione](#migrating-to-bounds-control) per aggiornare gli oggetti del gioco esistente.

Lo [`BoundingBox.cs`](xref:Microsoft.MixedReality.Toolkit.UI.BoundingBox) script fornisce funzionalità di base per la trasformazione di oggetti in realtà mista. Un rettangolo di delimitazione mostrerà un cubo intorno all'ologramma per indicare che è possibile interagire con. Gli handle sugli angoli e sui bordi del cubo consentono di ridimensionare o ruotare l'oggetto. Il rettangolo di delimitazione reagisce anche all'input dell'utente. In HoloLens 2, ad esempio, il rettangolo di delimitazione risponde alla prossimità del dito, fornendo commenti visivi per facilitare la percezione della distanza dall'oggetto. Tutte le interazioni e gli oggetti visivi possono essere facilmente personalizzati.

Per ulteriori informazioni, vedere il [riquadro delimitatore e la barra delle applicazioni](https://docs.microsoft.com/windows/mixed-reality/app-bar-and-bounding-box) in Windows Dev Center.

## <a name="example-scene"></a>Scena di esempio

È possibile trovare esempi di configurazioni dei box di delimitazione nella `BoundingBoxExamples` scena.

<img src="../images/bounding-box/MRTK_BoundingBox_Examples.png" alt="Bounding Box Examples">

## <a name="how-to-add-and-configure-a-bounding-box-using-unity-inspector"></a>Come aggiungere e configurare un rettangolo di delimitazione con Unity Inspector

1. Aggiungi box Collider a un oggetto
2. Assegnare `BoundingBox` uno script a un oggetto
3. Configurare le opzioni, ad esempio i metodi di attivazione (vedere la sezione [proprietà di controllo](#inspector-properties) più avanti)
4. Opzionale Assegnare prefabbricati e materiali per un rettangolo di delimitazione dello stile HoloLens 2 (vedere la sezione [stili handle](#handle-styles) più avanti)

> [!NOTE]
> Utilizzare l' *oggetto di destinazione* e il campo di override dei *limiti* nel controllo per assegnare un oggetto e un Collider specifici nell'oggetto con più componenti figlio.

![Rettangolo di delimitazione 1](../images/bounding-box/MRTK_BoundingBox_Assign.png)

## <a name="how-to-add-and-configure-a-bounding-box-in-the-code"></a>Come aggiungere e configurare un rettangolo di delimitazione nel codice

1. Creare un'istanza del cubo GameObject

    ```c#
    GameObject cube = GameObject.CreatePrimitive(PrimitiveType.Cube);
    ```

1. Assegnare `BoundingBox` uno script a un oggetto con Collider, usando AddComponent<> ()

    ```c#
    private BoundingBox bbox;
    bbox = cube.AddComponent<BoundingBox>();
    ```

1. Opzioni di configurazione (vedere la sezione [proprietà di controllo](#inspector-properties) più avanti)

    ```c#
    // Make the scale handles large
    bbox.ScaleHandleSize = 0.1f;
    // Hide rotation handles
    bbox.ShowRotationHandleForX = false;
    bbox.ShowRotationHandleForY = false;
    bbox.ShowRotationHandleForZ = false;
    ```

1. Opzionale Assegnare prefabbricati e materiali per un rettangolo di delimitazione dello stile HoloLens 2. Questa operazione richiede comunque le assegnazioni tramite il controllo, poiché i materiali e i prefabbricati devono essere caricati dinamicamente.

> [!NOTE]
> Uso della cartella ' Resources ' di Unity o dello [shader.]( https://docs.unity3d.com/ScriptReference/Shader.Find.html) non è consigliabile trovare per il caricamento dinamico degli shader perché le permutazioni dello shader potrebbero mancare in fase di esecuzione.

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

### <a name="example-set-minimum-maximum-bounding-box-scale-using-minmaxscaleconstraint"></a>Esempio: impostare la scala minima e massima del rettangolo di delimitazione usando MinMaxScaleConstraint

Per impostare la scala minima e massima, utilizzare [`MinMaxScaleConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.MinMaxScaleConstraint) . È anche possibile usare MinMaxScaleConstraint per impostare la scala minima e massima per [`ManipulationHandler`](xref:Microsoft.MixedReality.Toolkit.UI.ManipulationHandler) .

```c#
GameObject cube = GameObject.CreatePrimitive(PrimitiveType.Cube);
bbox = cube.AddComponent<BoundingBox>();
// Important: BoundingBox creates a scale handler on start if one does not exist
// do not use AddComponent, as that will create a  duplicate handler that will not be used
MinMaxScaleConstraint scaleConstraint = bbox.gameObject.GetComponent<MinMaxScaleConstraint>();
scaleConstraint.ScaleMinimum = 1f;
scaleConstraint.ScaleMaximum = 2f;
```

## <a name="example-add-bounding-box-around-a-game-object"></a>Esempio: aggiungere un rettangolo di delimitazione intorno a un oggetto Game

Per aggiungere un rettangolo di delimitazione intorno a un oggetto, è sufficiente aggiungervi un `BoundingBox` componente:

```c#
private void PutABoxAroundIt(GameObject target)
{
   target.AddComponent<BoundingBox>();
}
```

## <a name="inspector-properties"></a>Proprietà di Inspector

### <a name="target-object"></a>Oggetti di destinazione

Questa proprietà specifica quale oggetto verrà trasformato dalla manipolazione del rettangolo di delimitazione. Se non è impostato alcun oggetto, il rettangolo di delimitazione viene impostato sul valore predefinito dell'oggetto proprietario.

### <a name="bounds-override"></a>Override dei limiti

Imposta un Collider di box dall'oggetto per il calcolo dei limiti.

### <a name="activation-behavior"></a>Comportamento di attivazione

Sono disponibili diverse opzioni per attivare l'interfaccia del rettangolo di delimitazione.

* *Attiva all'inizio*: il rettangolo di delimitazione diventa visibile dopo l'avvio della scena.
* *Attiva per prossimità*: il rettangolo di delimitazione diventa visibile quando una mano articolata è vicina all'oggetto.
* *Activate by Pointer*: il rettangolo di delimitazione diventa visibile quando è di destinazione di un puntatore a mano.
* *Attiva manualmente*: il rettangolo di delimitazione non diventa visibile automaticamente. È possibile attivarla manualmente tramite uno script accedendo alla proprietà boundingBox. Active.

### <a name="scale-minimum"></a>Dimensioni minime

Scala minima consentita. Questa proprietà è deprecata ed è preferibile aggiungere uno [`MinMaxScaleConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.MinMaxScaleConstraint) script. Se lo script viene aggiunto, la scala minima verrà ricavata da essa anziché dal rettangolo di delimitazione.

### <a name="scale-maximum"></a>Scalabilità massima

Scala massima consentita. Questa proprietà è deprecata ed è preferibile aggiungere uno [`MinMaxScaleConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.MinMaxScaleConstraint) script. Se lo script viene aggiunto, la scala massima verrà ricavata da essa anziché dal rettangolo di delimitazione.

### <a name="box-display"></a>Visualizzazione box

Diverse opzioni di visualizzazione del rettangolo di delimitazione.

Se l'asse appiattito è impostato su *Flat auto*, lo script non consentirà la manipolazione lungo l'asse con l'extent più piccolo. In questo modo si ottiene un rettangolo di delimitazione 2D, che in genere viene utilizzato per gli oggetti thin.

### <a name="handles"></a>Selettori

È possibile assegnare il materiale e la prefabbricato per eseguire l'override dello stile dell'handle. Se non viene assegnato alcun handle, questi verranno visualizzati nello stile predefinito.

## <a name="events"></a>Eventi

Il rettangolo di delimitazione fornisce gli eventi seguenti. Questo esempio usa questi eventi per riprodurre commenti audio.

* **Rotazione avviata**: attivata all'avvio della rotazione.
* **Rotazione terminata**: attivata al termine della rotazione.
* **Scale started**: viene attivato all'avvio del ridimensionamento.
* **Scale ended**: viene attivato quando il ridimensionamento termina.

<img src="../images/bounding-box/MRTK_BoundingBox_Events.png" width="450" alt="Events">

## <a name="handle-styles"></a>Stili di gestione

Per impostazione predefinita, quando si assegna semplicemente lo [`BoundingBox.cs`](xref:Microsoft.MixedReality.Toolkit.UI.BoundingBox) script, verrà visualizzato l'handle dello stile HoloLens 1st Gen. Per usare gli handle di stile HoloLens 2, è necessario assegnare i materiali e i prefabbricati di handle appropriati.

![Stili dell'handle del rettangolo di delimitazione](../images/bounding-box/MRTK_BoundingBox_HandleStyles1.png)

Di seguito sono riportati i prefabbricati, i materiali e i valori di scala per gli handle del rettangolo di delimitazione dello stile HoloLens 2. Questo esempio è reperibile nella `BoundingBoxExamples` scena.

<img src="../images/bounding-box/MRTK_BoundingBox_HandleStyles2.png" width="450" alt="HandStyles 2">

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

### <a name="proximity-setup-for-hololens-2-style"></a>Prossimità (impostazione per lo stile HoloLens 2)

Mostra e nasconde gli handle con animazione in base alla distanza delle lancette. Ha un'animazione di ridimensionamento in due passaggi.

<img src="../images/bounding-box/MRTK_BoundingBox_Proximity.png" alt="Proximity">

* **Effetto di prossimità attivo**: Abilita l'attivazione dell'handle basata sulla prossimità
* **Gestisci prossimità media**: distanza per la scalabilità del primo passaggio
* **Handle vicino prossimità**: distanza per la scala del secondo passaggio
* **Scalabilità più ampia**: valore di scala predefinito dell'asset dell'handle quando le mani non rientrano nell'intervallo dell'interazione del rettangolo di selezione (distanza definita in precedenza da' handle media prossimità'). Utilizzare 0 per nascondere l'handle per impostazione predefinita)
* **Scala media**: valore di scala dell'asset dell'handle quando le lancette sono comprese nell'intervallo di interazione del rettangolo di selezione (distanza definita in precedenza da' handle Close prossimità'. Utilizzare 1 per mostrare le dimensioni normali)
* **Close scale**: valore di scala dell'asset dell'handle quando le lancette sono comprese nell'intervallo dell'interazione di cattura (distanza definita in precedenza da' handle Close prossimità'. Usare 1. x per visualizzare dimensioni maggiori)

## <a name="making-an-object-movable-with-manipulation-handler"></a>Rendere un oggetto mobile con il gestore di manipolazione

Un rettangolo di delimitazione può essere combinato con [`ManipulationHandler.cs`](manipulation-handler.md) per rendere l'oggetto mobile usando un'interazione di gran lunga. Il gestore di manipolazione supporta entrambe le interazioni con una e due gestite. Il [rilevamento manuale](../input/hand-tracking.md) può essere usato per interagire con un oggetto alla chiusura.

<img src="../images/bounding-box/MRTK_BoundingBox_ManipulationHandler.png" width="450" alt="Manipulation Handler">

Affinché i bordi del riquadro delimitatore si comportino allo stesso modo quando lo si usa [`ManipulationHandler`](manipulation-handler.md) , è consigliabile connettere gli eventi per in fase di *manipolazione avviata* alla  /  *manipolazione* `BoundingBox.HighlightWires`  /  `BoundingBox.UnhighlightWires` rispettivamente, come illustrato nella schermata precedente.

## <a name="migrating-to-bounds-control"></a>Migrazione al controllo dei limiti

I prefissi e le istanze esistenti che usano il rettangolo di [delimitazione](bounding-box.md) possono essere aggiornati al nuovo controllo dei limiti tramite la [finestra di migrazione](../tools/migration-window.md) che fa parte del pacchetto di strumenti MRTK.

Per l'aggiornamento di singole istanze del rettangolo di delimitazione è disponibile anche un'opzione di migrazione all'interno del controllo proprietà del componente.

<img src="../images/bounds-control/MRTK_BoundsControl_Migrate.png" width="450" alt="Bounds Control Migrate">

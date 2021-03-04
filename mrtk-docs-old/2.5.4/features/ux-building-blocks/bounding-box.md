---
title: BoundingBox
description: Panoramica sul riquadro delimitatore in MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, rettangolo di delimitazione
ms.openlocfilehash: 37cbd21736e0f32acf0b3b8f836da0526d6f3b13
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/03/2021
ms.locfileid: "101783165"
---
# <a name="bounding-box"></a><span data-ttu-id="bae4b-104">Rettangolo di selezione</span><span class="sxs-lookup"><span data-stu-id="bae4b-104">Bounding box</span></span>

![Rettangolo di selezione](../images/bounding-box/MRTK_BoundingBox_Main.png)

> [!NOTE]
> <span data-ttu-id="bae4b-106">Il rettangolo di delimitazione è deprecato e sostituito dal [controllo dei limiti](bounds-control.md)successivi.</span><span class="sxs-lookup"><span data-stu-id="bae4b-106">Bounding box is deprecated and replaced by its successor [bounds control](bounds-control.md).</span></span> <span data-ttu-id="bae4b-107">Usare [una delle opzioni di migrazione](#migrating-to-bounds-control) per aggiornare gli oggetti del gioco esistente.</span><span class="sxs-lookup"><span data-stu-id="bae4b-107">Use [one of the migration options](#migrating-to-bounds-control) to upgrade existing game objects.</span></span>

<span data-ttu-id="bae4b-108">Lo [`BoundingBox.cs`](xref:Microsoft.MixedReality.Toolkit.UI.BoundingBox) script fornisce funzionalità di base per la trasformazione di oggetti in realtà mista.</span><span class="sxs-lookup"><span data-stu-id="bae4b-108">The [`BoundingBox.cs`](xref:Microsoft.MixedReality.Toolkit.UI.BoundingBox) script provides basic functionality for transforming objects in mixed reality.</span></span> <span data-ttu-id="bae4b-109">Un rettangolo di delimitazione mostrerà un cubo intorno all'ologramma per indicare che è possibile interagire con.</span><span class="sxs-lookup"><span data-stu-id="bae4b-109">A bounding box will show a cube around the hologram to indicate that it can be interacted with.</span></span> <span data-ttu-id="bae4b-110">Gli handle sugli angoli e sui bordi del cubo consentono di ridimensionare o ruotare l'oggetto.</span><span class="sxs-lookup"><span data-stu-id="bae4b-110">Handles on the corners and edges of the cube allow scaling or rotating the object.</span></span> <span data-ttu-id="bae4b-111">Il rettangolo di delimitazione reagisce anche all'input dell'utente.</span><span class="sxs-lookup"><span data-stu-id="bae4b-111">The bounding box also reacts to user input.</span></span> <span data-ttu-id="bae4b-112">In HoloLens 2, ad esempio, il rettangolo di delimitazione risponde alla prossimità del dito, fornendo commenti visivi per facilitare la percezione della distanza dall'oggetto.</span><span class="sxs-lookup"><span data-stu-id="bae4b-112">On HoloLens 2, for example, the bounding box responds to finger proximity, providing visual feedback to help perceive the distance from the object.</span></span> <span data-ttu-id="bae4b-113">Tutte le interazioni e gli oggetti visivi possono essere facilmente personalizzati.</span><span class="sxs-lookup"><span data-stu-id="bae4b-113">All interactions and visuals can be easily customized.</span></span>

<span data-ttu-id="bae4b-114">Per ulteriori informazioni, vedere il [riquadro delimitatore e la barra delle applicazioni](https://docs.microsoft.com/windows/mixed-reality/app-bar-and-bounding-box) in Windows Dev Center.</span><span class="sxs-lookup"><span data-stu-id="bae4b-114">For more information, see [Bounding box and App bar](https://docs.microsoft.com/windows/mixed-reality/app-bar-and-bounding-box) in the Windows Dev Center.</span></span>

## <a name="example-scene"></a><span data-ttu-id="bae4b-115">Scena di esempio</span><span class="sxs-lookup"><span data-stu-id="bae4b-115">Example scene</span></span>

<span data-ttu-id="bae4b-116">È possibile trovare esempi di configurazioni dei box di delimitazione nella `BoundingBoxExamples` scena.</span><span class="sxs-lookup"><span data-stu-id="bae4b-116">You can find examples of bounding box configurations in the `BoundingBoxExamples` scene.</span></span>

<img src="../images/bounding-box/MRTK_BoundingBox_Examples.png" alt="Bounding Box Examples">

## <a name="how-to-add-and-configure-a-bounding-box-using-unity-inspector"></a><span data-ttu-id="bae4b-117">Come aggiungere e configurare un rettangolo di delimitazione con Unity Inspector</span><span class="sxs-lookup"><span data-stu-id="bae4b-117">How to add and configure a bounding box using Unity Inspector</span></span>

1. <span data-ttu-id="bae4b-118">Aggiungi box Collider a un oggetto</span><span class="sxs-lookup"><span data-stu-id="bae4b-118">Add Box Collider to an object</span></span>
2. <span data-ttu-id="bae4b-119">Assegnare `BoundingBox` uno script a un oggetto</span><span class="sxs-lookup"><span data-stu-id="bae4b-119">Assign `BoundingBox` script to an object</span></span>
3. <span data-ttu-id="bae4b-120">Configurare le opzioni, ad esempio i metodi di attivazione (vedere la sezione [proprietà di controllo](#inspector-properties) più avanti)</span><span class="sxs-lookup"><span data-stu-id="bae4b-120">Configure options, such as 'Activation' methods (see [Inspector properties](#inspector-properties) section below)</span></span>
4. <span data-ttu-id="bae4b-121">Opzionale Assegnare prefabbricati e materiali per un rettangolo di delimitazione dello stile HoloLens 2 (vedere la sezione [stili handle](#handle-styles) più avanti)</span><span class="sxs-lookup"><span data-stu-id="bae4b-121">(Optional) Assign prefabs and materials for a HoloLens 2 style bounding box (see [Handle styles](#handle-styles) section below)</span></span>

> [!NOTE]
> <span data-ttu-id="bae4b-122">Utilizzare l' *oggetto di destinazione* e il campo di override dei *limiti* nel controllo per assegnare un oggetto e un Collider specifici nell'oggetto con più componenti figlio.</span><span class="sxs-lookup"><span data-stu-id="bae4b-122">Use *Target Object* and *Bounds Override* field in the inspector to assign specific object and collider in the object with multiple child components.</span></span>

![Rettangolo di delimitazione 1](../images/bounding-box/MRTK_BoundingBox_Assign.png)

## <a name="how-to-add-and-configure-a-bounding-box-in-the-code"></a><span data-ttu-id="bae4b-124">Come aggiungere e configurare un rettangolo di delimitazione nel codice</span><span class="sxs-lookup"><span data-stu-id="bae4b-124">How to add and configure a bounding box in the code</span></span>

1. <span data-ttu-id="bae4b-125">Creare un'istanza del cubo GameObject</span><span class="sxs-lookup"><span data-stu-id="bae4b-125">Instantiate cube GameObject</span></span>

    ```c#
    GameObject cube = GameObject.CreatePrimitive(PrimitiveType.Cube);
    ```

1. <span data-ttu-id="bae4b-126">Assegnare `BoundingBox` uno script a un oggetto con Collider, usando AddComponent<> ()</span><span class="sxs-lookup"><span data-stu-id="bae4b-126">Assign `BoundingBox` script to an object with collider, using AddComponent<>()</span></span>

    ```c#
    private BoundingBox bbox;
    bbox = cube.AddComponent<BoundingBox>();
    ```

1. <span data-ttu-id="bae4b-127">Opzioni di configurazione (vedere la sezione [proprietà di controllo](#inspector-properties) più avanti)</span><span class="sxs-lookup"><span data-stu-id="bae4b-127">Configure options (see [Inspector properties](#inspector-properties) section below)</span></span>

    ```c#
    // Make the scale handles large
    bbox.ScaleHandleSize = 0.1f;
    // Hide rotation handles
    bbox.ShowRotationHandleForX = false;
    bbox.ShowRotationHandleForY = false;
    bbox.ShowRotationHandleForZ = false;
    ```

1. <span data-ttu-id="bae4b-128">Opzionale Assegnare prefabbricati e materiali per un rettangolo di delimitazione dello stile HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="bae4b-128">(Optional) Assign prefabs and materials for a HoloLens 2 style bounding box.</span></span> <span data-ttu-id="bae4b-129">Questa operazione richiede comunque le assegnazioni tramite il controllo, poiché i materiali e i prefabbricati devono essere caricati dinamicamente.</span><span class="sxs-lookup"><span data-stu-id="bae4b-129">This still requires assignments through the inspector since the materials and prefabs should be dynamically loaded.</span></span>

> [!NOTE]
> <span data-ttu-id="bae4b-130">Uso della cartella ' Resources ' di Unity o dello [shader.]( https://docs.unity3d.com/ScriptReference/Shader.Find.html) non è consigliabile trovare per il caricamento dinamico degli shader perché le permutazioni dello shader potrebbero mancare in fase di esecuzione.</span><span class="sxs-lookup"><span data-stu-id="bae4b-130">Using Unity's 'Resources' folder or [Shader.Find]( https://docs.unity3d.com/ScriptReference/Shader.Find.html) for dynamically loading shaders is not recommended since shader permutations may be missing at runtime.</span></span>

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

### <a name="example-set-minimum-maximum-bounding-box-scale-using-minmaxscaleconstraint"></a><span data-ttu-id="bae4b-131">Esempio: impostare la scala minima e massima del rettangolo di delimitazione usando MinMaxScaleConstraint</span><span class="sxs-lookup"><span data-stu-id="bae4b-131">Example: Set minimum, maximum bounding box scale using MinMaxScaleConstraint</span></span>

<span data-ttu-id="bae4b-132">Per impostare la scala minima e massima, utilizzare [`MinMaxScaleConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.MinMaxScaleConstraint) .</span><span class="sxs-lookup"><span data-stu-id="bae4b-132">To set the minimum and maximum scale, use the [`MinMaxScaleConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.MinMaxScaleConstraint).</span></span> <span data-ttu-id="bae4b-133">È anche possibile usare MinMaxScaleConstraint per impostare la scala minima e massima per [`ManipulationHandler`](xref:Microsoft.MixedReality.Toolkit.UI.ManipulationHandler) .</span><span class="sxs-lookup"><span data-stu-id="bae4b-133">You can also use MinMaxScaleConstraint to set minimum and maximum scale for [`ManipulationHandler`](xref:Microsoft.MixedReality.Toolkit.UI.ManipulationHandler).</span></span>

```c#
GameObject cube = GameObject.CreatePrimitive(PrimitiveType.Cube);
bbox = cube.AddComponent<BoundingBox>();
// Important: BoundingBox creates a scale handler on start if one does not exist
// do not use AddComponent, as that will create a  duplicate handler that will not be used
MinMaxScaleConstraint scaleConstraint = bbox.gameObject.GetComponent<MinMaxScaleConstraint>();
scaleConstraint.ScaleMinimum = 1f;
scaleConstraint.ScaleMaximum = 2f;
```

## <a name="example-add-bounding-box-around-a-game-object"></a><span data-ttu-id="bae4b-134">Esempio: aggiungere un rettangolo di delimitazione intorno a un oggetto Game</span><span class="sxs-lookup"><span data-stu-id="bae4b-134">Example: Add bounding box around a game object</span></span>

<span data-ttu-id="bae4b-135">Per aggiungere un rettangolo di delimitazione intorno a un oggetto, è sufficiente aggiungervi un `BoundingBox` componente:</span><span class="sxs-lookup"><span data-stu-id="bae4b-135">To add a bounding box around an object, simply add a `BoundingBox` component to it:</span></span>

```c#
private void PutABoxAroundIt(GameObject target)
{
   target.AddComponent<BoundingBox>();
}
```

## <a name="inspector-properties"></a><span data-ttu-id="bae4b-136">Proprietà di Inspector</span><span class="sxs-lookup"><span data-stu-id="bae4b-136">Inspector properties</span></span>

### <a name="target-object"></a><span data-ttu-id="bae4b-137">Oggetti di destinazione</span><span class="sxs-lookup"><span data-stu-id="bae4b-137">Target object</span></span>

<span data-ttu-id="bae4b-138">Questa proprietà specifica quale oggetto verrà trasformato dalla manipolazione del rettangolo di delimitazione.</span><span class="sxs-lookup"><span data-stu-id="bae4b-138">This property specifies which object will get transformed by the bounding box manipulation.</span></span> <span data-ttu-id="bae4b-139">Se non è impostato alcun oggetto, il rettangolo di delimitazione viene impostato sul valore predefinito dell'oggetto proprietario.</span><span class="sxs-lookup"><span data-stu-id="bae4b-139">If no object is set, the bounding box defaults to the owner object.</span></span>

### <a name="bounds-override"></a><span data-ttu-id="bae4b-140">Override dei limiti</span><span class="sxs-lookup"><span data-stu-id="bae4b-140">Bounds override</span></span>

<span data-ttu-id="bae4b-141">Imposta un Collider di box dall'oggetto per il calcolo dei limiti.</span><span class="sxs-lookup"><span data-stu-id="bae4b-141">Sets a box collider from the object for bounds computation.</span></span>

### <a name="activation-behavior"></a><span data-ttu-id="bae4b-142">Comportamento di attivazione</span><span class="sxs-lookup"><span data-stu-id="bae4b-142">Activation behavior</span></span>

<span data-ttu-id="bae4b-143">Sono disponibili diverse opzioni per attivare l'interfaccia del rettangolo di delimitazione.</span><span class="sxs-lookup"><span data-stu-id="bae4b-143">There are several options to activate the bounding box interface.</span></span>

* <span data-ttu-id="bae4b-144">*Attiva all'inizio*: il rettangolo di delimitazione diventa visibile dopo l'avvio della scena.</span><span class="sxs-lookup"><span data-stu-id="bae4b-144">*Activate On Start*: Bounding box becomes visible once the scene is started.</span></span>
* <span data-ttu-id="bae4b-145">*Attiva per prossimità*: il rettangolo di delimitazione diventa visibile quando una mano articolata è vicina all'oggetto.</span><span class="sxs-lookup"><span data-stu-id="bae4b-145">*Activate By Proximity*: Bounding box becomes visible when an articulated hand is close to the object.</span></span>
* <span data-ttu-id="bae4b-146">*Activate by Pointer*: il rettangolo di delimitazione diventa visibile quando è di destinazione di un puntatore a mano.</span><span class="sxs-lookup"><span data-stu-id="bae4b-146">*Activate By Pointer*: Bounding box becomes visible when it is targeted by a hand-ray pointer.</span></span>
* <span data-ttu-id="bae4b-147">*Attiva manualmente*: il rettangolo di delimitazione non diventa visibile automaticamente.</span><span class="sxs-lookup"><span data-stu-id="bae4b-147">*Activate Manually*: Bounding box does not become visible automatically.</span></span> <span data-ttu-id="bae4b-148">È possibile attivarla manualmente tramite uno script accedendo alla proprietà boundingBox. Active.</span><span class="sxs-lookup"><span data-stu-id="bae4b-148">You can manually activate it through a script by accessing the boundingBox.Active property.</span></span>

### <a name="scale-minimum"></a><span data-ttu-id="bae4b-149">Dimensioni minime</span><span class="sxs-lookup"><span data-stu-id="bae4b-149">Scale minimum</span></span>

<span data-ttu-id="bae4b-150">Scala minima consentita.</span><span class="sxs-lookup"><span data-stu-id="bae4b-150">The minimum allowed scale.</span></span> <span data-ttu-id="bae4b-151">Questa proprietà è deprecata ed è preferibile aggiungere uno [`MinMaxScaleConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.MinMaxScaleConstraint) script.</span><span class="sxs-lookup"><span data-stu-id="bae4b-151">This property is deprecated and it is preferable to add a [`MinMaxScaleConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.MinMaxScaleConstraint) script.</span></span> <span data-ttu-id="bae4b-152">Se lo script viene aggiunto, la scala minima verrà ricavata da essa anziché dal rettangolo di delimitazione.</span><span class="sxs-lookup"><span data-stu-id="bae4b-152">If this script is added, the minimum scale will be taken from it instead of from the bounding box.</span></span>

### <a name="scale-maximum"></a><span data-ttu-id="bae4b-153">Scalabilità massima</span><span class="sxs-lookup"><span data-stu-id="bae4b-153">Scale maximum</span></span>

<span data-ttu-id="bae4b-154">Scala massima consentita.</span><span class="sxs-lookup"><span data-stu-id="bae4b-154">The maximum allowed scale.</span></span> <span data-ttu-id="bae4b-155">Questa proprietà è deprecata ed è preferibile aggiungere uno [`MinMaxScaleConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.MinMaxScaleConstraint) script.</span><span class="sxs-lookup"><span data-stu-id="bae4b-155">This property is deprecated and it is preferable to add a [`MinMaxScaleConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.MinMaxScaleConstraint) script.</span></span> <span data-ttu-id="bae4b-156">Se lo script viene aggiunto, la scala massima verrà ricavata da essa anziché dal rettangolo di delimitazione.</span><span class="sxs-lookup"><span data-stu-id="bae4b-156">If this script is added, the maximum scale will be taken from it instead of from the bounding box.</span></span>

### <a name="box-display"></a><span data-ttu-id="bae4b-157">Visualizzazione box</span><span class="sxs-lookup"><span data-stu-id="bae4b-157">Box display</span></span>

<span data-ttu-id="bae4b-158">Diverse opzioni di visualizzazione del rettangolo di delimitazione.</span><span class="sxs-lookup"><span data-stu-id="bae4b-158">Various bounding box visualization options.</span></span>

<span data-ttu-id="bae4b-159">Se l'asse appiattito è impostato su *Flat auto*, lo script non consentirà la manipolazione lungo l'asse con l'extent più piccolo.</span><span class="sxs-lookup"><span data-stu-id="bae4b-159">If Flatten Axis is set to *Flatten Auto*, the script will disallow manipulation along the axis with the smallest extent.</span></span> <span data-ttu-id="bae4b-160">In questo modo si ottiene un rettangolo di delimitazione 2D, che in genere viene utilizzato per gli oggetti thin.</span><span class="sxs-lookup"><span data-stu-id="bae4b-160">This results in a 2D bounding box, which is usually used for thin objects.</span></span>

### <a name="handles"></a><span data-ttu-id="bae4b-161">Selettori</span><span class="sxs-lookup"><span data-stu-id="bae4b-161">Handles</span></span>

<span data-ttu-id="bae4b-162">È possibile assegnare il materiale e la prefabbricato per eseguire l'override dello stile dell'handle.</span><span class="sxs-lookup"><span data-stu-id="bae4b-162">You can assign the material and prefab to override the handle style.</span></span> <span data-ttu-id="bae4b-163">Se non viene assegnato alcun handle, questi verranno visualizzati nello stile predefinito.</span><span class="sxs-lookup"><span data-stu-id="bae4b-163">If no handles are assigned, they will be displayed in the default style.</span></span>

## <a name="events"></a><span data-ttu-id="bae4b-164">Eventi</span><span class="sxs-lookup"><span data-stu-id="bae4b-164">Events</span></span>

<span data-ttu-id="bae4b-165">Il rettangolo di delimitazione fornisce gli eventi seguenti.</span><span class="sxs-lookup"><span data-stu-id="bae4b-165">Bounding box provides the following events.</span></span> <span data-ttu-id="bae4b-166">Questo esempio usa questi eventi per riprodurre commenti audio.</span><span class="sxs-lookup"><span data-stu-id="bae4b-166">This example uses these events to play audio feedback.</span></span>

* <span data-ttu-id="bae4b-167">**Rotazione avviata**: attivata all'avvio della rotazione.</span><span class="sxs-lookup"><span data-stu-id="bae4b-167">**Rotate Started**: Fired when rotation starts.</span></span>
* <span data-ttu-id="bae4b-168">**Rotazione terminata**: attivata al termine della rotazione.</span><span class="sxs-lookup"><span data-stu-id="bae4b-168">**Rotate Ended**: Fired when rotation ends.</span></span>
* <span data-ttu-id="bae4b-169">**Scale started**: viene attivato all'avvio del ridimensionamento.</span><span class="sxs-lookup"><span data-stu-id="bae4b-169">**Scale Started**: Fires when scaling starts.</span></span>
* <span data-ttu-id="bae4b-170">**Scale ended**: viene attivato quando il ridimensionamento termina.</span><span class="sxs-lookup"><span data-stu-id="bae4b-170">**Scale Ended**: Fires when scaling ends.</span></span>

<img src="../images/bounding-box/MRTK_BoundingBox_Events.png" width="450" alt="Events">

## <a name="handle-styles"></a><span data-ttu-id="bae4b-171">Stili di gestione</span><span class="sxs-lookup"><span data-stu-id="bae4b-171">Handle styles</span></span>

<span data-ttu-id="bae4b-172">Per impostazione predefinita, quando si assegna semplicemente lo [`BoundingBox.cs`](xref:Microsoft.MixedReality.Toolkit.UI.BoundingBox) script, verrà visualizzato l'handle dello stile HoloLens 1st Gen.</span><span class="sxs-lookup"><span data-stu-id="bae4b-172">By default, when you just assign the [`BoundingBox.cs`](xref:Microsoft.MixedReality.Toolkit.UI.BoundingBox) script, it will show the handle of the HoloLens 1st gen style.</span></span> <span data-ttu-id="bae4b-173">Per usare gli handle di stile HoloLens 2, è necessario assegnare i materiali e i prefabbricati di handle appropriati.</span><span class="sxs-lookup"><span data-stu-id="bae4b-173">To use HoloLens 2 style handles, you need to assign proper handle prefabs and materials.</span></span>

![Stili dell'handle del rettangolo di delimitazione](../images/bounding-box/MRTK_BoundingBox_HandleStyles1.png)

<span data-ttu-id="bae4b-175">Di seguito sono riportati i prefabbricati, i materiali e i valori di scala per gli handle del rettangolo di delimitazione dello stile HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="bae4b-175">Below are the prefabs, materials, and the scaling values for the HoloLens 2 style bounding box handles.</span></span> <span data-ttu-id="bae4b-176">Questo esempio è reperibile nella `BoundingBoxExamples` scena.</span><span class="sxs-lookup"><span data-stu-id="bae4b-176">You can find this example in the `BoundingBoxExamples` scene.</span></span>

<img src="../images/bounding-box/MRTK_BoundingBox_HandleStyles2.png" width="450" alt="HandStyles 2">

### <a name="handles-setup-for-hololens-2-style"></a><span data-ttu-id="bae4b-177">Handle (impostazione per lo stile HoloLens 2)</span><span class="sxs-lookup"><span data-stu-id="bae4b-177">Handles (Setup for HoloLens 2 style)</span></span>

* <span data-ttu-id="bae4b-178">**Gestione del materiale**: BoundingBoxHandleWhite. Mat</span><span class="sxs-lookup"><span data-stu-id="bae4b-178">**Handle Material**: BoundingBoxHandleWhite.mat</span></span>
* <span data-ttu-id="bae4b-179">**Gestire il materiale afferrato**: BoundingBoxHandleBlueGrabbed. Mat</span><span class="sxs-lookup"><span data-stu-id="bae4b-179">**Handle Grabbed Material**: BoundingBoxHandleBlueGrabbed.mat</span></span>
* <span data-ttu-id="bae4b-180">**Dimensioni prefabbricate del quadratino di ridimensionamento**: MRTK_BoundingBox_ScaleHandle</span><span class="sxs-lookup"><span data-stu-id="bae4b-180">**Scale Handle Prefab**: MRTK_BoundingBox_ScaleHandle.prefab</span></span>
* <span data-ttu-id="bae4b-181">**Ridimensionare il quadratino di tabulazione**: MRTK_BoundingBox_ScaleHandle_Slate. prefabbricate</span><span class="sxs-lookup"><span data-stu-id="bae4b-181">**Scale Handle Slate Prefab**: MRTK_BoundingBox_ScaleHandle_Slate.prefab</span></span>
* <span data-ttu-id="bae4b-182">**Dimensioni del quadratino di ridimensionamento**: 0,016 (1,6 cm)</span><span class="sxs-lookup"><span data-stu-id="bae4b-182">**Scale Handle Size**: 0.016 (1.6cm)</span></span>
* <span data-ttu-id="bae4b-183">**Riempimento del Collider del gestore di scalabilità**: 0,016 (rende l'oggetto Collider afferrabile leggermente più grande rispetto alla gestione degli oggetti visivi)</span><span class="sxs-lookup"><span data-stu-id="bae4b-183">**Scale Handle Collider Padding**: 0.016 (makes the grabbable collider slightly bigger than handle visual)</span></span>
* <span data-ttu-id="bae4b-184">**Maniglie prefabbricate di rotazione**: MRTK_BoundingBox_RotateHandle</span><span class="sxs-lookup"><span data-stu-id="bae4b-184">**Rotation Handle Prefab**: MRTK_BoundingBox_RotateHandle.prefab</span></span>
* <span data-ttu-id="bae4b-185">**Dimensioni handle di rotazione**: 0,016</span><span class="sxs-lookup"><span data-stu-id="bae4b-185">**Rotation Handle Size**: 0.016</span></span>
* <span data-ttu-id="bae4b-186">**Riempimento del Collider dell'handle di rotazione**: 0,016 (rende l'oggetto Collider afferrabile leggermente più grande rispetto alla gestione degli oggetti visivi)</span><span class="sxs-lookup"><span data-stu-id="bae4b-186">**Rotation Handle Collider Padding**: 0.016 (makes the grabbable collider slightly bigger than handle visual)</span></span>

### <a name="proximity-setup-for-hololens-2-style"></a><span data-ttu-id="bae4b-187">Prossimità (impostazione per lo stile HoloLens 2)</span><span class="sxs-lookup"><span data-stu-id="bae4b-187">Proximity (Setup for HoloLens 2 style)</span></span>

<span data-ttu-id="bae4b-188">Mostra e nasconde gli handle con animazione in base alla distanza delle lancette.</span><span class="sxs-lookup"><span data-stu-id="bae4b-188">Show and hide the handles with animation based on the distance to the hands.</span></span> <span data-ttu-id="bae4b-189">Ha un'animazione di ridimensionamento in due passaggi.</span><span class="sxs-lookup"><span data-stu-id="bae4b-189">It has two-step scaling animation.</span></span>

<img src="../images/bounding-box/MRTK_BoundingBox_Proximity.png" alt="Proximity">

* <span data-ttu-id="bae4b-190">**Effetto di prossimità attivo**: Abilita l'attivazione dell'handle basata sulla prossimità</span><span class="sxs-lookup"><span data-stu-id="bae4b-190">**Proximity Effect Active**: Enable proximity-based handle activation</span></span>
* <span data-ttu-id="bae4b-191">**Gestisci prossimità media**: distanza per la scalabilità del primo passaggio</span><span class="sxs-lookup"><span data-stu-id="bae4b-191">**Handle Medium Proximity**: Distance for the 1st step scaling</span></span>
* <span data-ttu-id="bae4b-192">**Handle vicino prossimità**: distanza per la scala del secondo passaggio</span><span class="sxs-lookup"><span data-stu-id="bae4b-192">**Handle Close Proximity**: Distance for the 2nd step scaling</span></span>
* <span data-ttu-id="bae4b-193">**Scalabilità più ampia**: valore di scala predefinito dell'asset dell'handle quando le mani non rientrano nell'intervallo dell'interazione del rettangolo di selezione (distanza definita in precedenza da' handle media prossimità').</span><span class="sxs-lookup"><span data-stu-id="bae4b-193">**Far Scale**: Default scale value of the handle asset when the hands are out of range of the bounding box interaction (distance defined above by 'Handle Medium Proximity'.</span></span> <span data-ttu-id="bae4b-194">Utilizzare 0 per nascondere l'handle per impostazione predefinita)</span><span class="sxs-lookup"><span data-stu-id="bae4b-194">Use 0 to hide handle by default)</span></span>
* <span data-ttu-id="bae4b-195">**Scala media**: valore di scala dell'asset dell'handle quando le lancette sono comprese nell'intervallo di interazione del rettangolo di selezione (distanza definita in precedenza da' handle Close prossimità'.</span><span class="sxs-lookup"><span data-stu-id="bae4b-195">**Medium Scale**: Scale value of the handle asset when the hands are within range of the bounding box interaction (distance defined above by 'Handle Close Proximity'.</span></span> <span data-ttu-id="bae4b-196">Utilizzare 1 per mostrare le dimensioni normali)</span><span class="sxs-lookup"><span data-stu-id="bae4b-196">Use 1 to show normal size)</span></span>
* <span data-ttu-id="bae4b-197">**Close scale**: valore di scala dell'asset dell'handle quando le lancette sono comprese nell'intervallo dell'interazione di cattura (distanza definita in precedenza da' handle Close prossimità'.</span><span class="sxs-lookup"><span data-stu-id="bae4b-197">**Close Scale**: Scale value of the handle asset when the hands are within range of the grab interaction (distance defined above by 'Handle Close Proximity'.</span></span> <span data-ttu-id="bae4b-198">Usare 1. x per visualizzare dimensioni maggiori)</span><span class="sxs-lookup"><span data-stu-id="bae4b-198">Use 1.x to show bigger size)</span></span>

## <a name="making-an-object-movable-with-manipulation-handler"></a><span data-ttu-id="bae4b-199">Rendere un oggetto mobile con il gestore di manipolazione</span><span class="sxs-lookup"><span data-stu-id="bae4b-199">Making an object movable with manipulation handler</span></span>

<span data-ttu-id="bae4b-200">Un rettangolo di delimitazione può essere combinato con [`ManipulationHandler.cs`](manipulation-handler.md) per rendere l'oggetto mobile usando un'interazione di gran lunga.</span><span class="sxs-lookup"><span data-stu-id="bae4b-200">A bounding box can be combined with [`ManipulationHandler.cs`](manipulation-handler.md) to make the object movable using far interaction.</span></span> <span data-ttu-id="bae4b-201">Il gestore di manipolazione supporta entrambe le interazioni con una e due gestite.</span><span class="sxs-lookup"><span data-stu-id="bae4b-201">The manipulation handler supports both one and two-handed interactions.</span></span> <span data-ttu-id="bae4b-202">Il [rilevamento manuale](../input/hand-tracking.md) può essere usato per interagire con un oggetto alla chiusura.</span><span class="sxs-lookup"><span data-stu-id="bae4b-202">[Hand tracking](../input/hand-tracking.md) can be used to interact with an object up close.</span></span>

<img src="../images/bounding-box/MRTK_BoundingBox_ManipulationHandler.png" width="450" alt="Manipulation Handler">

<span data-ttu-id="bae4b-203">Affinché i bordi del riquadro delimitatore si comportino allo stesso modo quando lo si usa [`ManipulationHandler`](manipulation-handler.md) , è consigliabile connettere gli eventi per in fase di *manipolazione avviata* alla  /  *manipolazione* `BoundingBox.HighlightWires`  /  `BoundingBox.UnhighlightWires` rispettivamente, come illustrato nella schermata precedente.</span><span class="sxs-lookup"><span data-stu-id="bae4b-203">In order for the bounding box edges to behave the same way when moving it using [`ManipulationHandler`](manipulation-handler.md)'s far interaction, it is advised to connect its events for *On Manipulation Started* / *On Manipulation Ended* to `BoundingBox.HighlightWires` / `BoundingBox.UnhighlightWires` respectively, as shown in the screenshot above.</span></span>

## <a name="migrating-to-bounds-control"></a><span data-ttu-id="bae4b-204">Migrazione al controllo dei limiti</span><span class="sxs-lookup"><span data-stu-id="bae4b-204">Migrating to bounds control</span></span>

<span data-ttu-id="bae4b-205">I prefissi e le istanze esistenti che usano il rettangolo di [delimitazione](bounding-box.md) possono essere aggiornati al nuovo controllo dei limiti tramite la [finestra di migrazione](../tools/migration-window.md) che fa parte del pacchetto di strumenti MRTK.</span><span class="sxs-lookup"><span data-stu-id="bae4b-205">Existing prefabs and instances using [bounding box](bounding-box.md) can be upgraded to the new bounds control via the [migration window](../tools/migration-window.md) which is part of the MRTK tools package.</span></span>

<span data-ttu-id="bae4b-206">Per l'aggiornamento di singole istanze del rettangolo di delimitazione è disponibile anche un'opzione di migrazione all'interno del controllo proprietà del componente.</span><span class="sxs-lookup"><span data-stu-id="bae4b-206">For upgrading individual instances of bounding box there's also an a migration option inside the property inspector of the component.</span></span>

<img src="../images/bounds-control/MRTK_BoundsControl_Migrate.png" width="450" alt="Bounds Control Migrate">

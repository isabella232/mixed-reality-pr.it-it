---
title: README_BoundingBox
description: Panoramica sul riquadro delimitatore in MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, rettangolo di delimitazione
ms.openlocfilehash: bc63e9a0f85f4fa632677ec06deda9b410ae310d
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/03/2021
ms.locfileid: "101782703"
---
# <a name="bounding-box"></a><span data-ttu-id="82177-104">Rettangolo di selezione</span><span class="sxs-lookup"><span data-stu-id="82177-104">Bounding box</span></span>

![Casella principale del rettangolo di delimitazione](Images/BoundingBox/MRTK_BoundingBox_Main.png)

<span data-ttu-id="82177-106">Lo [`BoundingBox.cs`](xref:Microsoft.MixedReality.Toolkit.UI.BoundingBox) script fornisce funzionalità di base per la trasformazione di oggetti in realtà mista.</span><span class="sxs-lookup"><span data-stu-id="82177-106">The [`BoundingBox.cs`](xref:Microsoft.MixedReality.Toolkit.UI.BoundingBox) script provides basic functionality for transforming objects in mixed reality.</span></span> <span data-ttu-id="82177-107">Un rettangolo di delimitazione mostrerà un cubo intorno all'ologramma per indicare che è possibile interagire con.</span><span class="sxs-lookup"><span data-stu-id="82177-107">A bounding box will show a cube around the hologram to indicate that it can be interacted with.</span></span> <span data-ttu-id="82177-108">Gli handle sugli angoli e sui bordi del cubo consentono di ridimensionare o ruotare l'oggetto.</span><span class="sxs-lookup"><span data-stu-id="82177-108">Handles on the corners and edges of the cube allow scaling or rotating the object.</span></span> <span data-ttu-id="82177-109">Il rettangolo di delimitazione reagisce anche all'input dell'utente.</span><span class="sxs-lookup"><span data-stu-id="82177-109">The bounding box also reacts to user input.</span></span> <span data-ttu-id="82177-110">In HoloLens 2, ad esempio, il rettangolo di delimitazione risponde alla prossimità del dito, fornendo commenti visivi per facilitare la percezione della distanza dall'oggetto.</span><span class="sxs-lookup"><span data-stu-id="82177-110">On HoloLens 2, for example, the bounding box responds to finger proximity, providing visual feedback to help perceive the distance from the object.</span></span> <span data-ttu-id="82177-111">Tutte le interazioni e gli oggetti visivi possono essere facilmente personalizzati.</span><span class="sxs-lookup"><span data-stu-id="82177-111">All interactions and visuals can be easily customized.</span></span>

<span data-ttu-id="82177-112">Per ulteriori informazioni, vedere il [riquadro delimitatore e la barra delle applicazioni](https://docs.microsoft.com/windows/mixed-reality/app-bar-and-bounding-box) in Windows Dev Center.</span><span class="sxs-lookup"><span data-stu-id="82177-112">For more information, see [Bounding box and App bar](https://docs.microsoft.com/windows/mixed-reality/app-bar-and-bounding-box) in the Windows Dev Center.</span></span>

## <a name="example-scene"></a><span data-ttu-id="82177-113">Scena di esempio</span><span class="sxs-lookup"><span data-stu-id="82177-113">Example scene</span></span>

<span data-ttu-id="82177-114">È possibile trovare esempi di configurazioni dei box di delimitazione nella `BoundingBoxExamples` scena.</span><span class="sxs-lookup"><span data-stu-id="82177-114">You can find examples of bounding box configurations in the `BoundingBoxExamples` scene.</span></span>

<img src="Images/BoundingBox/MRTK_BoundingBox_Examples.png" alt="Example Scene">

## <a name="how-to-add-and-configure-a-bounding-box-using-unity-inspector"></a><span data-ttu-id="82177-115">Come aggiungere e configurare un rettangolo di delimitazione con Unity Inspector</span><span class="sxs-lookup"><span data-stu-id="82177-115">How to add and configure a bounding box using Unity Inspector</span></span>

1. <span data-ttu-id="82177-116">Aggiungi box Collider a un oggetto</span><span class="sxs-lookup"><span data-stu-id="82177-116">Add Box Collider to an object</span></span>
2. <span data-ttu-id="82177-117">Assegnare `BoundingBox` uno script a un oggetto</span><span class="sxs-lookup"><span data-stu-id="82177-117">Assign `BoundingBox` script to an object</span></span>
3. <span data-ttu-id="82177-118">Configurare le opzioni, ad esempio i metodi di attivazione (vedere la sezione [proprietà di controllo](#inspector-properties) più avanti)</span><span class="sxs-lookup"><span data-stu-id="82177-118">Configure options, such as 'Activation' methods (see [Inspector properties](#inspector-properties) section below)</span></span>
4. <span data-ttu-id="82177-119">Opzionale Assegnare prefabbricati e materiali per un rettangolo di delimitazione dello stile HoloLens 2 (vedere la sezione [stili handle](#handle-styles) più avanti)</span><span class="sxs-lookup"><span data-stu-id="82177-119">(Optional) Assign prefabs and materials for a HoloLens 2 style bounding box (see [Handle styles](#handle-styles) section below)</span></span>

> [!NOTE]
> <span data-ttu-id="82177-120">Utilizzare l' *oggetto di destinazione* e il campo di override dei *limiti* nel controllo per assegnare un oggetto e un Collider specifici nell'oggetto con più componenti figlio.</span><span class="sxs-lookup"><span data-stu-id="82177-120">Use *Target Object* and *Bounds Override* field in the inspector to assign specific object and collider in the object with multiple child components.</span></span>

![Assegnazione del rettangolo di delimitazione](Images/BoundingBox/MRTK_BoundingBox_Assign.png)

## <a name="how-to-add-and-configure-a-bounding-box-in-the-code"></a><span data-ttu-id="82177-122">Come aggiungere e configurare un rettangolo di delimitazione nel codice</span><span class="sxs-lookup"><span data-stu-id="82177-122">How to add and configure a bounding box in the code</span></span>

1. <span data-ttu-id="82177-123">Creare un'istanza del cubo GameObject</span><span class="sxs-lookup"><span data-stu-id="82177-123">Instantiate cube GameObject</span></span>

    ```c#
    GameObject cube = GameObject.CreatePrimitive(PrimitiveType.Cube);
    ```

1. <span data-ttu-id="82177-124">Assegnare `BoundingBox` uno script a un oggetto con Collider, usando AddComponent<> ()</span><span class="sxs-lookup"><span data-stu-id="82177-124">Assign `BoundingBox` script to an object with collider, using AddComponent<>()</span></span>

    ```c#
    private BoundingBox bbox;
    bbox = cube.AddComponent<BoundingBox>();
    ```

1. <span data-ttu-id="82177-125">Opzioni di configurazione (vedere la sezione [proprietà di controllo](#inspector-properties) più avanti)</span><span class="sxs-lookup"><span data-stu-id="82177-125">Configure options (see [Inspector properties](#inspector-properties) section below)</span></span>

    ```c#
    // Make the scale handles large
    bbox.ScaleHandleSize = 0.1f;
    // Hide rotation handles
    bbox.ShowRotationHandleForX = false;
    bbox.ShowRotationHandleForY = false;
    bbox.ShowRotationHandleForZ = false;
    ```

1. <span data-ttu-id="82177-126">Opzionale Assegnare prefabbricati e materiali per un rettangolo di delimitazione dello stile HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="82177-126">(Optional) Assign prefabs and materials for a HoloLens 2 style bounding box.</span></span> <span data-ttu-id="82177-127">Questa operazione richiede comunque le assegnazioni tramite il controllo, poiché i materiali e i prefabbricati devono essere caricati dinamicamente.</span><span class="sxs-lookup"><span data-stu-id="82177-127">This still requires assignments through the inspector since the materials and prefabs should be dynamically loaded.</span></span>

> [!NOTE]
> <span data-ttu-id="82177-128">Uso della cartella ' Resources ' di Unity o dello [shader.]( https://docs.unity3d.com/ScriptReference/Shader.Find.html) non è consigliabile trovare per il caricamento dinamico degli shader perché le permutazioni dello shader potrebbero mancare in fase di esecuzione.</span><span class="sxs-lookup"><span data-stu-id="82177-128">Using Unity's 'Resources' folder or [Shader.Find]( https://docs.unity3d.com/ScriptReference/Shader.Find.html) for dynamically loading shaders is not recommended since shader permutations may be missing at runtime.</span></span>

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

### <a name="example-set-minimum-maximum-bounding-box-scale-using-minmaxscaleconstraint"></a><span data-ttu-id="82177-129">Esempio: impostare la scala minima e massima del rettangolo di delimitazione usando MinMaxScaleConstraint</span><span class="sxs-lookup"><span data-stu-id="82177-129">Example: Set minimum, maximum bounding box scale using MinMaxScaleConstraint</span></span>

<span data-ttu-id="82177-130">Per impostare la scala minima e massima, utilizzare [`MinMaxScaleConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.MinMaxScaleConstraint) .</span><span class="sxs-lookup"><span data-stu-id="82177-130">To set the minimum and maximum scale, use the [`MinMaxScaleConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.MinMaxScaleConstraint).</span></span> <span data-ttu-id="82177-131">È anche possibile usare MinMaxScaleConstraint per impostare la scala minima e massima per [`ManipulationHandler`](xref:Microsoft.MixedReality.Toolkit.UI.ManipulationHandler) .</span><span class="sxs-lookup"><span data-stu-id="82177-131">You can also use MinMaxScaleConstraint to set minimum and maximum scale for [`ManipulationHandler`](xref:Microsoft.MixedReality.Toolkit.UI.ManipulationHandler).</span></span>

```c#
GameObject cube = GameObject.CreatePrimitive(PrimitiveType.Cube);
bbox = cube.AddComponent<BoundingBox>();
// Important: BoundingBox creates a scale handler on start if one does not exist
// do not use AddComponent, as that will create a  duplicate handler that will not be used
MinMaxScaleConstraint scaleConstraint = bbox.gameObject.GetComponent<MinMaxScaleConstraint>();
scaleConstraint.ScaleMinimum = 1f;
scaleConstraint.ScaleMaximum = 2f;
```

## <a name="example-add-bounding-box-around-a-game-object"></a><span data-ttu-id="82177-132">Esempio: aggiungere un rettangolo di delimitazione intorno a un oggetto Game</span><span class="sxs-lookup"><span data-stu-id="82177-132">Example: Add bounding box around a game object</span></span>

<span data-ttu-id="82177-133">Per aggiungere un rettangolo di delimitazione intorno a un oggetto, è sufficiente aggiungervi un `BoundingBox` componente:</span><span class="sxs-lookup"><span data-stu-id="82177-133">To add a bounding box around an object, simply add a `BoundingBox` component to it:</span></span>

```c#
private void PutABoxAroundIt(GameObject target)
{
   target.AddComponent<BoundingBox>();
}
```

## <a name="inspector-properties"></a><span data-ttu-id="82177-134">Proprietà di Inspector</span><span class="sxs-lookup"><span data-stu-id="82177-134">Inspector properties</span></span>

### <a name="target-object"></a><span data-ttu-id="82177-135">Oggetti di destinazione</span><span class="sxs-lookup"><span data-stu-id="82177-135">Target object</span></span>

<span data-ttu-id="82177-136">Questa proprietà specifica quale oggetto verrà trasformato dalla manipolazione del rettangolo di delimitazione.</span><span class="sxs-lookup"><span data-stu-id="82177-136">This property specifies which object will get transformed by the bounding box manipulation.</span></span> <span data-ttu-id="82177-137">Se non è impostato alcun oggetto, il rettangolo di delimitazione viene impostato sul valore predefinito dell'oggetto proprietario.</span><span class="sxs-lookup"><span data-stu-id="82177-137">If no object is set, the bounding box defaults to the owner object.</span></span>

### <a name="bounds-override"></a><span data-ttu-id="82177-138">Override dei limiti</span><span class="sxs-lookup"><span data-stu-id="82177-138">Bounds override</span></span>

<span data-ttu-id="82177-139">Imposta un Collider di box dall'oggetto per il calcolo dei limiti.</span><span class="sxs-lookup"><span data-stu-id="82177-139">Sets a box collider from the object for bounds computation.</span></span>

### <a name="activation-behavior"></a><span data-ttu-id="82177-140">Comportamento di attivazione</span><span class="sxs-lookup"><span data-stu-id="82177-140">Activation behavior</span></span>

<span data-ttu-id="82177-141">Sono disponibili diverse opzioni per attivare l'interfaccia del rettangolo di delimitazione.</span><span class="sxs-lookup"><span data-stu-id="82177-141">There are several options to activate the bounding box interface.</span></span>

* <span data-ttu-id="82177-142">*Attiva all'inizio*: il rettangolo di delimitazione diventa visibile dopo l'avvio della scena.</span><span class="sxs-lookup"><span data-stu-id="82177-142">*Activate On Start*: Bounding box becomes visible once the scene is started.</span></span>
* <span data-ttu-id="82177-143">*Attiva per prossimità*: il rettangolo di delimitazione diventa visibile quando una mano articolata è vicina all'oggetto.</span><span class="sxs-lookup"><span data-stu-id="82177-143">*Activate By Proximity*: Bounding box becomes visible when an articulated hand is close to the object.</span></span>
* <span data-ttu-id="82177-144">*Activate by Pointer*: il rettangolo di delimitazione diventa visibile quando è di destinazione di un puntatore a mano.</span><span class="sxs-lookup"><span data-stu-id="82177-144">*Activate By Pointer*: Bounding box becomes visible when it is targeted by a hand-ray pointer.</span></span>
* <span data-ttu-id="82177-145">*Attiva manualmente*: il rettangolo di delimitazione non diventa visibile automaticamente.</span><span class="sxs-lookup"><span data-stu-id="82177-145">*Activate Manually*: Bounding box does not become visible automatically.</span></span> <span data-ttu-id="82177-146">È possibile attivarla manualmente tramite uno script accedendo alla proprietà boundingBox. Active.</span><span class="sxs-lookup"><span data-stu-id="82177-146">You can manually activate it through a script by accessing the boundingBox.Active property.</span></span>

### <a name="scale-minimum"></a><span data-ttu-id="82177-147">Dimensioni minime</span><span class="sxs-lookup"><span data-stu-id="82177-147">Scale minimum</span></span>

<span data-ttu-id="82177-148">Scala minima consentita.</span><span class="sxs-lookup"><span data-stu-id="82177-148">The minimum allowed scale.</span></span> <span data-ttu-id="82177-149">Questa proprietà è deprecata ed è preferibile aggiungere uno [`MinMaxScaleConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.MinMaxScaleConstraint) script.</span><span class="sxs-lookup"><span data-stu-id="82177-149">This property is deprecated and it is preferable to add a [`MinMaxScaleConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.MinMaxScaleConstraint) script.</span></span> <span data-ttu-id="82177-150">Se lo script viene aggiunto, la scala minima verrà ricavata da essa anziché dal rettangolo di delimitazione.</span><span class="sxs-lookup"><span data-stu-id="82177-150">If this script is added, the minimum scale will be taken from it instead of from the bounding box.</span></span>

### <a name="scale-maximum"></a><span data-ttu-id="82177-151">Scalabilità massima</span><span class="sxs-lookup"><span data-stu-id="82177-151">Scale maximum</span></span>

<span data-ttu-id="82177-152">Scala massima consentita.</span><span class="sxs-lookup"><span data-stu-id="82177-152">The maximum allowed scale.</span></span> <span data-ttu-id="82177-153">Questa proprietà è deprecata ed è preferibile aggiungere uno [`MinMaxScaleConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.MinMaxScaleConstraint) script.</span><span class="sxs-lookup"><span data-stu-id="82177-153">This property is deprecated and it is preferable to add a [`MinMaxScaleConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.MinMaxScaleConstraint) script.</span></span> <span data-ttu-id="82177-154">Se lo script viene aggiunto, la scala massima verrà ricavata da essa anziché dal rettangolo di delimitazione.</span><span class="sxs-lookup"><span data-stu-id="82177-154">If this script is added, the maximum scale will be taken from it instead of from the bounding box.</span></span>

### <a name="box-display"></a><span data-ttu-id="82177-155">Visualizzazione box</span><span class="sxs-lookup"><span data-stu-id="82177-155">Box display</span></span>

<span data-ttu-id="82177-156">Diverse opzioni di visualizzazione del rettangolo di delimitazione.</span><span class="sxs-lookup"><span data-stu-id="82177-156">Various bounding box visualization options.</span></span>

<span data-ttu-id="82177-157">Se l'asse appiattito è impostato su *Flat auto*, lo script non consentirà la manipolazione lungo l'asse con l'extent più piccolo.</span><span class="sxs-lookup"><span data-stu-id="82177-157">If Flatten Axis is set to *Flatten Auto*, the script will disallow manipulation along the axis with the smallest extent.</span></span> <span data-ttu-id="82177-158">In questo modo si ottiene un rettangolo di delimitazione 2D, che in genere viene utilizzato per gli oggetti thin.</span><span class="sxs-lookup"><span data-stu-id="82177-158">This results in a 2D bounding box, which is usually used for thin objects.</span></span>

### <a name="handles"></a><span data-ttu-id="82177-159">Selettori</span><span class="sxs-lookup"><span data-stu-id="82177-159">Handles</span></span>

<span data-ttu-id="82177-160">È possibile assegnare il materiale e la prefabbricato per eseguire l'override dello stile dell'handle.</span><span class="sxs-lookup"><span data-stu-id="82177-160">You can assign the material and prefab to override the handle style.</span></span> <span data-ttu-id="82177-161">Se non viene assegnato alcun handle, questi verranno visualizzati nello stile predefinito.</span><span class="sxs-lookup"><span data-stu-id="82177-161">If no handles are assigned, they will be displayed in the default style.</span></span>

## <a name="events"></a><span data-ttu-id="82177-162">Eventi</span><span class="sxs-lookup"><span data-stu-id="82177-162">Events</span></span>

<span data-ttu-id="82177-163">Il rettangolo di delimitazione fornisce gli eventi seguenti.</span><span class="sxs-lookup"><span data-stu-id="82177-163">Bounding box provides the following events.</span></span> <span data-ttu-id="82177-164">Questo esempio usa questi eventi per riprodurre commenti audio.</span><span class="sxs-lookup"><span data-stu-id="82177-164">This example uses these events to play audio feedback.</span></span>

* <span data-ttu-id="82177-165">**Rotazione avviata**: attivata all'avvio della rotazione.</span><span class="sxs-lookup"><span data-stu-id="82177-165">**Rotate Started**: Fired when rotation starts.</span></span>
* <span data-ttu-id="82177-166">**Rotazione terminata**: attivata al termine della rotazione.</span><span class="sxs-lookup"><span data-stu-id="82177-166">**Rotate Ended**: Fired when rotation ends.</span></span>
* <span data-ttu-id="82177-167">**Scale started**: viene attivato al termine del ridimensionamento.</span><span class="sxs-lookup"><span data-stu-id="82177-167">**Scale Started**: Fires when scaling ends.</span></span>
* <span data-ttu-id="82177-168">**Scale ended**: viene attivato quando il ridimensionamento termina.</span><span class="sxs-lookup"><span data-stu-id="82177-168">**Scale Ended**: Fires when scaling ends.</span></span>

<img src="Images/BoundingBox/MRTK_BoundingBox_Events.png" width="450" alt="Bounding Box Events">

## <a name="handle-styles"></a><span data-ttu-id="82177-169">Stili di gestione</span><span class="sxs-lookup"><span data-stu-id="82177-169">Handle styles</span></span>

<span data-ttu-id="82177-170">Per impostazione predefinita, quando si assegna semplicemente lo [`BoundingBox.cs`](xref:Microsoft.MixedReality.Toolkit.UI.BoundingBox) script, verrà visualizzato l'handle dello stile HoloLens 1st Gen.</span><span class="sxs-lookup"><span data-stu-id="82177-170">By default, when you just assign the [`BoundingBox.cs`](xref:Microsoft.MixedReality.Toolkit.UI.BoundingBox) script, it will show the handle of the HoloLens 1st gen style.</span></span> <span data-ttu-id="82177-171">Per usare gli handle di stile HoloLens 2, è necessario assegnare i materiali e i prefabbricati di handle appropriati.</span><span class="sxs-lookup"><span data-stu-id="82177-171">To use HoloLens 2 style handles, you need to assign proper handle prefabs and materials.</span></span>

![Stili dell'handle del rettangolo di delimitazione 1](Images/BoundingBox/MRTK_BoundingBox_HandleStyles1.png)

<span data-ttu-id="82177-173">Di seguito sono riportati i prefabbricati, i materiali e i valori di scala per gli handle del rettangolo di delimitazione dello stile HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="82177-173">Below are the prefabs, materials, and the scaling values for the HoloLens 2 style bounding box handles.</span></span> <span data-ttu-id="82177-174">Questo esempio è reperibile nella `BoundingBoxExamples` scena.</span><span class="sxs-lookup"><span data-stu-id="82177-174">You can find this example in the `BoundingBoxExamples` scene.</span></span>

<img src="Images/BoundingBox/MRTK_BoundingBox_HandleStyles2.png" width="450" alt="HandelStyles 2">

### <a name="handles-setup-for-hololens-2-style"></a><span data-ttu-id="82177-175">Handle (impostazione per lo stile HoloLens 2)</span><span class="sxs-lookup"><span data-stu-id="82177-175">Handles (Setup for HoloLens 2 style)</span></span>

* <span data-ttu-id="82177-176">**Gestione del materiale**: BoundingBoxHandleWhite. Mat</span><span class="sxs-lookup"><span data-stu-id="82177-176">**Handle Material**: BoundingBoxHandleWhite.mat</span></span>
* <span data-ttu-id="82177-177">**Gestire il materiale afferrato**: BoundingBoxHandleBlueGrabbed. Mat</span><span class="sxs-lookup"><span data-stu-id="82177-177">**Handle Grabbed Material**: BoundingBoxHandleBlueGrabbed.mat</span></span>
* <span data-ttu-id="82177-178">**Dimensioni prefabbricate del quadratino di ridimensionamento**: MRTK_BoundingBox_ScaleHandle</span><span class="sxs-lookup"><span data-stu-id="82177-178">**Scale Handle Prefab**: MRTK_BoundingBox_ScaleHandle.prefab</span></span>
* <span data-ttu-id="82177-179">**Ridimensionare il quadratino di tabulazione**: MRTK_BoundingBox_ScaleHandle_Slate. prefabbricate</span><span class="sxs-lookup"><span data-stu-id="82177-179">**Scale Handle Slate Prefab**: MRTK_BoundingBox_ScaleHandle_Slate.prefab</span></span>
* <span data-ttu-id="82177-180">**Dimensioni del quadratino di ridimensionamento**: 0,016 (1,6 cm)</span><span class="sxs-lookup"><span data-stu-id="82177-180">**Scale Handle Size**: 0.016 (1.6cm)</span></span>
* <span data-ttu-id="82177-181">**Riempimento del Collider del gestore di scalabilità**: 0,016 (rende l'oggetto Collider afferrabile leggermente più grande rispetto alla gestione degli oggetti visivi)</span><span class="sxs-lookup"><span data-stu-id="82177-181">**Scale Handle Collider Padding**: 0.016 (makes the grabbable collider slightly bigger than handle visual)</span></span>
* <span data-ttu-id="82177-182">**Maniglie prefabbricate di rotazione**: MRTK_BoundingBox_RotateHandle</span><span class="sxs-lookup"><span data-stu-id="82177-182">**Rotation Handle Prefab**: MRTK_BoundingBox_RotateHandle.prefab</span></span>
* <span data-ttu-id="82177-183">**Dimensioni handle di rotazione**: 0,016</span><span class="sxs-lookup"><span data-stu-id="82177-183">**Rotation Handle Size**: 0.016</span></span>
* <span data-ttu-id="82177-184">**Riempimento del Collider dell'handle di rotazione**: 0,016 (rende l'oggetto Collider afferrabile leggermente più grande rispetto alla gestione degli oggetti visivi)</span><span class="sxs-lookup"><span data-stu-id="82177-184">**Rotation Handle Collider Padding**: 0.016 (makes the grabbable collider slightly bigger than handle visual)</span></span>

### <a name="proximity-setup-for-hololens-2-style"></a><span data-ttu-id="82177-185">Prossimità (impostazione per lo stile HoloLens 2)</span><span class="sxs-lookup"><span data-stu-id="82177-185">Proximity (Setup for HoloLens 2 style)</span></span>

<span data-ttu-id="82177-186">Mostra e nasconde gli handle con animazione in base alla distanza delle lancette.</span><span class="sxs-lookup"><span data-stu-id="82177-186">Show and hide the handles with animation based on the distance to the hands.</span></span> <span data-ttu-id="82177-187">Ha un'animazione di ridimensionamento in due passaggi.</span><span class="sxs-lookup"><span data-stu-id="82177-187">It has two-step scaling animation.</span></span>

<img src="Images/BoundingBox/MRTK_BoundingBox_Proximity.png" alt="Proximity">

* <span data-ttu-id="82177-188">**Effetto di prossimità attivo**: Abilita l'attivazione dell'handle basata sulla prossimità</span><span class="sxs-lookup"><span data-stu-id="82177-188">**Proximity Effect Active**: Enable proximity-based handle activation</span></span>
* <span data-ttu-id="82177-189">**Gestisci prossimità media**: distanza per la scalabilità del primo passaggio</span><span class="sxs-lookup"><span data-stu-id="82177-189">**Handle Medium Proximity**: Distance for the 1st step scaling</span></span>
* <span data-ttu-id="82177-190">**Handle vicino prossimità**: distanza per la scala del secondo passaggio</span><span class="sxs-lookup"><span data-stu-id="82177-190">**Handle Close Proximity**: Distance for the 2nd step scaling</span></span>
* <span data-ttu-id="82177-191">**Scalabilità più ampia**: valore di scala predefinito dell'asset dell'handle quando le mani non rientrano nell'intervallo dell'interazione del rettangolo di selezione (distanza definita in precedenza da' handle media prossimità').</span><span class="sxs-lookup"><span data-stu-id="82177-191">**Far Scale**: Default scale value of the handle asset when the hands are out of range of the bounding box interaction (distance defined above by 'Handle Medium Proximity'.</span></span> <span data-ttu-id="82177-192">Utilizzare 0 per nascondere l'handle per impostazione predefinita)</span><span class="sxs-lookup"><span data-stu-id="82177-192">Use 0 to hide handle by default)</span></span>
* <span data-ttu-id="82177-193">**Scala media**: valore di scala dell'asset dell'handle quando le lancette sono comprese nell'intervallo di interazione del rettangolo di selezione (distanza definita in precedenza da' handle Close prossimità'.</span><span class="sxs-lookup"><span data-stu-id="82177-193">**Medium Scale**: Scale value of the handle asset when the hands are within range of the bounding box interaction (distance defined above by 'Handle Close Proximity'.</span></span> <span data-ttu-id="82177-194">Utilizzare 1 per mostrare le dimensioni normali)</span><span class="sxs-lookup"><span data-stu-id="82177-194">Use 1 to show normal size)</span></span>
* <span data-ttu-id="82177-195">**Close scale**: valore di scala dell'asset dell'handle quando le lancette sono comprese nell'intervallo dell'interazione di cattura (distanza definita in precedenza da' handle Close prossimità'.</span><span class="sxs-lookup"><span data-stu-id="82177-195">**Close Scale**: Scale value of the handle asset when the hands are within range of the grab interaction (distance defined above by 'Handle Close Proximity'.</span></span> <span data-ttu-id="82177-196">Usare 1. x per visualizzare dimensioni maggiori)</span><span class="sxs-lookup"><span data-stu-id="82177-196">Use 1.x to show bigger size)</span></span>

## <a name="making-an-object-movable-with-manipulation-handler"></a><span data-ttu-id="82177-197">Rendere un oggetto mobile con il gestore di manipolazione</span><span class="sxs-lookup"><span data-stu-id="82177-197">Making an object movable with manipulation handler</span></span>

<span data-ttu-id="82177-198">Un rettangolo di delimitazione può essere combinato con [`ManipulationHandler.cs`](README_ManipulationHandler.md) per rendere l'oggetto mobile usando un'interazione di gran lunga.</span><span class="sxs-lookup"><span data-stu-id="82177-198">A bounding box can be combined with [`ManipulationHandler.cs`](README_ManipulationHandler.md) to make the object movable using far interaction.</span></span> <span data-ttu-id="82177-199">Il gestore di manipolazione supporta entrambe le interazioni con una e due gestite.</span><span class="sxs-lookup"><span data-stu-id="82177-199">The manipulation handler supports both one and two-handed interactions.</span></span> <span data-ttu-id="82177-200">Il [rilevamento manuale](Input/HandTracking.md) può essere usato per interagire con un oggetto alla chiusura.</span><span class="sxs-lookup"><span data-stu-id="82177-200">[Hand tracking](Input/HandTracking.md) can be used to interact with an object up close.</span></span>

<img src="Images/BoundingBox/MRTK_BoundingBox_ManipulationHandler.png" width="450" alt="Manipulation Handler">

<span data-ttu-id="82177-201">Affinché i bordi del riquadro delimitatore si comportino allo stesso modo quando lo si usa [`ManipulationHandler`](README_ManipulationHandler.md) , è consigliabile connettere gli eventi per in fase di *manipolazione avviata* alla  /  *manipolazione* `BoundingBox.HighlightWires`  /  `BoundingBox.UnhighlightWires` rispettivamente, come illustrato nella schermata precedente.</span><span class="sxs-lookup"><span data-stu-id="82177-201">In order for the bounding box edges to behave the same way when moving it using [`ManipulationHandler`](README_ManipulationHandler.md)'s far interaction, it is advised to connect its events for *On Manipulation Started* / *On Manipulation Ended* to `BoundingBox.HighlightWires` / `BoundingBox.UnhighlightWires` respectively, as shown in the screenshot above.</span></span>

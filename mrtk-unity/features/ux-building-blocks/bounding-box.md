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
# <a name="bounding-box"></a><span data-ttu-id="a7114-104">Rettangolo di selezione</span><span class="sxs-lookup"><span data-stu-id="a7114-104">Bounding box</span></span>

![Rettangolo di selezione](../images/bounding-box/MRTK_BoundingBox_Main.png)

> [!NOTE]
> <span data-ttu-id="a7114-106">Il rettangolo di selezione è deprecato e sostituito dal relativo controllo [dei limiti successivo.](bounds-control.md)</span><span class="sxs-lookup"><span data-stu-id="a7114-106">Bounding box is deprecated and replaced by its successor [bounds control](bounds-control.md).</span></span> <span data-ttu-id="a7114-107">Usare [una delle opzioni di migrazione per](#migrating-to-bounds-control) aggiornare gli oggetti di gioco esistenti.</span><span class="sxs-lookup"><span data-stu-id="a7114-107">Use [one of the migration options](#migrating-to-bounds-control) to upgrade existing game objects.</span></span>

<span data-ttu-id="a7114-108">Lo [`BoundingBox.cs`](xref:Microsoft.MixedReality.Toolkit.UI.BoundingBox) script fornisce funzionalità di base per la trasformazione di oggetti in realtà mista.</span><span class="sxs-lookup"><span data-stu-id="a7114-108">The [`BoundingBox.cs`](xref:Microsoft.MixedReality.Toolkit.UI.BoundingBox) script provides basic functionality for transforming objects in mixed reality.</span></span> <span data-ttu-id="a7114-109">Un rettangolo di selezione mostrerà un cubo intorno all'ologramma per indicare che è possibile interagire con esso.</span><span class="sxs-lookup"><span data-stu-id="a7114-109">A bounding box will show a cube around the hologram to indicate that it can be interacted with.</span></span> <span data-ttu-id="a7114-110">Gli handle sugli angoli e sui bordi del cubo consentono di ridimensionare o ruotare l'oggetto.</span><span class="sxs-lookup"><span data-stu-id="a7114-110">Handles on the corners and edges of the cube allow scaling or rotating the object.</span></span> <span data-ttu-id="a7114-111">Il rettangolo di selezione reagisce anche all'input dell'utente.</span><span class="sxs-lookup"><span data-stu-id="a7114-111">The bounding box also reacts to user input.</span></span> <span data-ttu-id="a7114-112">In HoloLens 2, ad esempio, il rettangolo di selezione risponde alla prossimità delle dita, fornendo un feedback visivo che consente di percepire la distanza dall'oggetto.</span><span class="sxs-lookup"><span data-stu-id="a7114-112">On HoloLens 2, for example, the bounding box responds to finger proximity, providing visual feedback to help perceive the distance from the object.</span></span> <span data-ttu-id="a7114-113">Tutte le interazioni e gli oggetti visivi possono essere facilmente personalizzati.</span><span class="sxs-lookup"><span data-stu-id="a7114-113">All interactions and visuals can be easily customized.</span></span>

<span data-ttu-id="a7114-114">Per altre informazioni, vedere [Rettangolo di selezione e Barra dell'app](/windows/mixed-reality/app-bar-and-bounding-box) nella Windows Dev Center.</span><span class="sxs-lookup"><span data-stu-id="a7114-114">For more information, see [Bounding box and App bar](/windows/mixed-reality/app-bar-and-bounding-box) in the Windows Dev Center.</span></span>

## <a name="example-scene"></a><span data-ttu-id="a7114-115">Scena di esempio</span><span class="sxs-lookup"><span data-stu-id="a7114-115">Example scene</span></span>

<span data-ttu-id="a7114-116">Nella scena sono disponibili esempi di configurazioni del rettangolo di `BoundingBoxExamples` selezione.</span><span class="sxs-lookup"><span data-stu-id="a7114-116">You can find examples of bounding box configurations in the `BoundingBoxExamples` scene.</span></span>

<img src="../images/bounding-box/MRTK_BoundingBox_Examples.png" alt="Bounding Box Examples">

## <a name="how-to-add-and-configure-a-bounding-box-using-unity-inspector"></a><span data-ttu-id="a7114-117">Come aggiungere e configurare un rettangolo di selezione usando Unity Inspector</span><span class="sxs-lookup"><span data-stu-id="a7114-117">How to add and configure a bounding box using Unity Inspector</span></span>

1. <span data-ttu-id="a7114-118">Aggiungere Box Collider a un oggetto</span><span class="sxs-lookup"><span data-stu-id="a7114-118">Add Box Collider to an object</span></span>
2. <span data-ttu-id="a7114-119">Assegnare `BoundingBox` uno script a un oggetto</span><span class="sxs-lookup"><span data-stu-id="a7114-119">Assign `BoundingBox` script to an object</span></span>
3. <span data-ttu-id="a7114-120">Configurare opzioni, ad esempio i metodi di attivazione (vedere la [sezione Proprietà del controllo riportata](#inspector-properties) di seguito)</span><span class="sxs-lookup"><span data-stu-id="a7114-120">Configure options, such as 'Activation' methods (see [Inspector properties](#inspector-properties) section below)</span></span>
4. <span data-ttu-id="a7114-121">(Facoltativo) Assegnare prefab e materiali per un HoloLens 2 di selezione dello stile (vedere la sezione [Gestire gli stili](#handle-styles) più avanti)</span><span class="sxs-lookup"><span data-stu-id="a7114-121">(Optional) Assign prefabs and materials for a HoloLens 2 style bounding box (see [Handle styles](#handle-styles) section below)</span></span>

> [!NOTE]
> <span data-ttu-id="a7114-122">Usare *il campo Target Object* e *Bounds Override* nel controllo per assegnare un oggetto specifico e un collisore nell'oggetto con più componenti figlio.</span><span class="sxs-lookup"><span data-stu-id="a7114-122">Use *Target Object* and *Bounds Override* field in the inspector to assign specific object and collider in the object with multiple child components.</span></span>

![Rettangolo di selezione 1](../images/bounding-box/MRTK_BoundingBox_Assign.png)

## <a name="how-to-add-and-configure-a-bounding-box-in-the-code"></a><span data-ttu-id="a7114-124">Come aggiungere e configurare un rettangolo di selezione nel codice</span><span class="sxs-lookup"><span data-stu-id="a7114-124">How to add and configure a bounding box in the code</span></span>

1. <span data-ttu-id="a7114-125">Creare un'istanza del cubo GameObject</span><span class="sxs-lookup"><span data-stu-id="a7114-125">Instantiate cube GameObject</span></span>

    ```c#
    GameObject cube = GameObject.CreatePrimitive(PrimitiveType.Cube);
    ```

1. <span data-ttu-id="a7114-126">Assegnare `BoundingBox` uno script a un oggetto con collisore usando AddComponent<>()</span><span class="sxs-lookup"><span data-stu-id="a7114-126">Assign `BoundingBox` script to an object with collider, using AddComponent<>()</span></span>

    ```c#
    private BoundingBox bbox;
    bbox = cube.AddComponent<BoundingBox>();
    ```

1. <span data-ttu-id="a7114-127">Configurare le opzioni (vedere la [sezione Proprietà del controllo riportata](#inspector-properties) di seguito)</span><span class="sxs-lookup"><span data-stu-id="a7114-127">Configure options (see [Inspector properties](#inspector-properties) section below)</span></span>

    ```c#
    // Make the scale handles large
    bbox.ScaleHandleSize = 0.1f;
    // Hide rotation handles
    bbox.ShowRotationHandleForX = false;
    bbox.ShowRotationHandleForY = false;
    bbox.ShowRotationHandleForZ = false;
    ```

1. <span data-ttu-id="a7114-128">(Facoltativo) Assegnare prefab e materiali per un HoloLens 2 rettangolo di selezione dello stile.</span><span class="sxs-lookup"><span data-stu-id="a7114-128">(Optional) Assign prefabs and materials for a HoloLens 2 style bounding box.</span></span> <span data-ttu-id="a7114-129">Ciò richiede comunque assegnazioni tramite il controllo poiché i materiali e i prefab devono essere caricati dinamicamente.</span><span class="sxs-lookup"><span data-stu-id="a7114-129">This still requires assignments through the inspector since the materials and prefabs should be dynamically loaded.</span></span>

> [!NOTE]
> <span data-ttu-id="a7114-130">L'uso della cartella 'Resources' di [Unity o shader.Find]( https://docs.unity3d.com/ScriptReference/Shader.Find.html) per il caricamento dinamico degli shader non è consigliato perché le permutazioni dello shader potrebbero mancare in fase di esecuzione.</span><span class="sxs-lookup"><span data-stu-id="a7114-130">Using Unity's 'Resources' folder or [Shader.Find]( https://docs.unity3d.com/ScriptReference/Shader.Find.html) for dynamically loading shaders is not recommended since shader permutations may be missing at runtime.</span></span>

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

### <a name="example-set-minimum-maximum-bounding-box-scale-using-minmaxscaleconstraint"></a><span data-ttu-id="a7114-131">Esempio: Impostare la scala minima e massima del rettangolo di selezione usando MinMaxScaleConstraint</span><span class="sxs-lookup"><span data-stu-id="a7114-131">Example: Set minimum, maximum bounding box scale using MinMaxScaleConstraint</span></span>

<span data-ttu-id="a7114-132">Per impostare la scala minima e massima, usare [`MinMaxScaleConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.MinMaxScaleConstraint) .</span><span class="sxs-lookup"><span data-stu-id="a7114-132">To set the minimum and maximum scale, use the [`MinMaxScaleConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.MinMaxScaleConstraint).</span></span> <span data-ttu-id="a7114-133">È anche possibile usare MinMaxScaleConstraint per impostare la scala minima e massima per [`ManipulationHandler`](xref:Microsoft.MixedReality.Toolkit.UI.ManipulationHandler) .</span><span class="sxs-lookup"><span data-stu-id="a7114-133">You can also use MinMaxScaleConstraint to set minimum and maximum scale for [`ManipulationHandler`](xref:Microsoft.MixedReality.Toolkit.UI.ManipulationHandler).</span></span>

```c#
GameObject cube = GameObject.CreatePrimitive(PrimitiveType.Cube);
bbox = cube.AddComponent<BoundingBox>();
// Important: BoundingBox creates a scale handler on start if one does not exist
// do not use AddComponent, as that will create a  duplicate handler that will not be used
MinMaxScaleConstraint scaleConstraint = bbox.gameObject.GetComponent<MinMaxScaleConstraint>();
scaleConstraint.ScaleMinimum = 1f;
scaleConstraint.ScaleMaximum = 2f;
```

## <a name="example-add-bounding-box-around-a-game-object"></a><span data-ttu-id="a7114-134">Esempio: Aggiungere un rettangolo di selezione intorno a un oggetto gioco</span><span class="sxs-lookup"><span data-stu-id="a7114-134">Example: Add bounding box around a game object</span></span>

<span data-ttu-id="a7114-135">Per aggiungere un rettangolo di selezione intorno a un oggetto, è sufficiente aggiungere un `BoundingBox` componente:</span><span class="sxs-lookup"><span data-stu-id="a7114-135">To add a bounding box around an object, simply add a `BoundingBox` component to it:</span></span>

```c#
private void PutABoxAroundIt(GameObject target)
{
   target.AddComponent<BoundingBox>();
}
```

## <a name="inspector-properties"></a><span data-ttu-id="a7114-136">Proprietà del controllo</span><span class="sxs-lookup"><span data-stu-id="a7114-136">Inspector properties</span></span>

### <a name="target-object"></a><span data-ttu-id="a7114-137">Oggetti di destinazione</span><span class="sxs-lookup"><span data-stu-id="a7114-137">Target object</span></span>

<span data-ttu-id="a7114-138">Questa proprietà specifica quale oggetto verrà trasformato dalla manipolazione del rettangolo di selezione.</span><span class="sxs-lookup"><span data-stu-id="a7114-138">This property specifies which object will get transformed by the bounding box manipulation.</span></span> <span data-ttu-id="a7114-139">Se non è impostato alcun oggetto, il rettangolo di selezione viene impostato per impostazione predefinita sull'oggetto proprietario.</span><span class="sxs-lookup"><span data-stu-id="a7114-139">If no object is set, the bounding box defaults to the owner object.</span></span>

### <a name="bounds-override"></a><span data-ttu-id="a7114-140">Override dei limiti</span><span class="sxs-lookup"><span data-stu-id="a7114-140">Bounds override</span></span>

<span data-ttu-id="a7114-141">Imposta un collisore di box dall'oggetto per il calcolo dei limiti.</span><span class="sxs-lookup"><span data-stu-id="a7114-141">Sets a box collider from the object for bounds computation.</span></span>

### <a name="activation-behavior"></a><span data-ttu-id="a7114-142">Comportamento di attivazione</span><span class="sxs-lookup"><span data-stu-id="a7114-142">Activation behavior</span></span>

<span data-ttu-id="a7114-143">Sono disponibili diverse opzioni per attivare l'interfaccia del rettangolo di selezione.</span><span class="sxs-lookup"><span data-stu-id="a7114-143">There are several options to activate the bounding box interface.</span></span>

* <span data-ttu-id="a7114-144">*Attiva all'avvio:* il rettangolo di selezione diventa visibile dopo l'avvio della scena.</span><span class="sxs-lookup"><span data-stu-id="a7114-144">*Activate On Start*: Bounding box becomes visible once the scene is started.</span></span>
* <span data-ttu-id="a7114-145">*Attiva per prossimità:* il rettangolo di selezione diventa visibile quando una mano articolata è vicina all'oggetto.</span><span class="sxs-lookup"><span data-stu-id="a7114-145">*Activate By Proximity*: Bounding box becomes visible when an articulated hand is close to the object.</span></span>
* <span data-ttu-id="a7114-146">*Attiva per puntatore:* il rettangolo di selezione diventa visibile quando è destinato a un puntatore a raggi della mano.</span><span class="sxs-lookup"><span data-stu-id="a7114-146">*Activate By Pointer*: Bounding box becomes visible when it is targeted by a hand-ray pointer.</span></span>
* <span data-ttu-id="a7114-147">*Attiva manualmente:* il rettangolo di selezione non diventa visibile automaticamente.</span><span class="sxs-lookup"><span data-stu-id="a7114-147">*Activate Manually*: Bounding box does not become visible automatically.</span></span> <span data-ttu-id="a7114-148">È possibile attivarlo manualmente tramite uno script accedendo alla proprietà boundingBox.Active.</span><span class="sxs-lookup"><span data-stu-id="a7114-148">You can manually activate it through a script by accessing the boundingBox.Active property.</span></span>

### <a name="scale-minimum"></a><span data-ttu-id="a7114-149">Scalabilità minima</span><span class="sxs-lookup"><span data-stu-id="a7114-149">Scale minimum</span></span>

<span data-ttu-id="a7114-150">Scala minima consentita.</span><span class="sxs-lookup"><span data-stu-id="a7114-150">The minimum allowed scale.</span></span> <span data-ttu-id="a7114-151">Questa proprietà è deprecata ed è preferibile aggiungere uno [`MinMaxScaleConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.MinMaxScaleConstraint) script.</span><span class="sxs-lookup"><span data-stu-id="a7114-151">This property is deprecated and it is preferable to add a [`MinMaxScaleConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.MinMaxScaleConstraint) script.</span></span> <span data-ttu-id="a7114-152">Se si aggiunge questo script, la scala minima verrà prelevata da esso anziché dal rettangolo di selezione.</span><span class="sxs-lookup"><span data-stu-id="a7114-152">If this script is added, the minimum scale will be taken from it instead of from the bounding box.</span></span>

### <a name="scale-maximum"></a><span data-ttu-id="a7114-153">Scalabilità massima</span><span class="sxs-lookup"><span data-stu-id="a7114-153">Scale maximum</span></span>

<span data-ttu-id="a7114-154">Scala massima consentita.</span><span class="sxs-lookup"><span data-stu-id="a7114-154">The maximum allowed scale.</span></span> <span data-ttu-id="a7114-155">Questa proprietà è deprecata ed è preferibile aggiungere uno [`MinMaxScaleConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.MinMaxScaleConstraint) script.</span><span class="sxs-lookup"><span data-stu-id="a7114-155">This property is deprecated and it is preferable to add a [`MinMaxScaleConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.MinMaxScaleConstraint) script.</span></span> <span data-ttu-id="a7114-156">Se si aggiunge questo script, la scala massima verrà prelevata da esso anziché dal rettangolo di selezione.</span><span class="sxs-lookup"><span data-stu-id="a7114-156">If this script is added, the maximum scale will be taken from it instead of from the bounding box.</span></span>

### <a name="box-display"></a><span data-ttu-id="a7114-157">Visualizzazione della casella</span><span class="sxs-lookup"><span data-stu-id="a7114-157">Box display</span></span>

<span data-ttu-id="a7114-158">Varie opzioni di visualizzazione del rettangolo di selezione.</span><span class="sxs-lookup"><span data-stu-id="a7114-158">Various bounding box visualization options.</span></span>

<span data-ttu-id="a7114-159">Se l'opzione Asse appiattimento è impostata su *Flatten Auto,* lo script non consente la manipolazione lungo l'asse con l'estensione più piccola.</span><span class="sxs-lookup"><span data-stu-id="a7114-159">If Flatten Axis is set to *Flatten Auto*, the script will disallow manipulation along the axis with the smallest extent.</span></span> <span data-ttu-id="a7114-160">Il risultato è un rettangolo di selezione 2D, usato in genere per gli oggetti thin.</span><span class="sxs-lookup"><span data-stu-id="a7114-160">This results in a 2D bounding box, which is usually used for thin objects.</span></span>

### <a name="handles"></a><span data-ttu-id="a7114-161">Selettori</span><span class="sxs-lookup"><span data-stu-id="a7114-161">Handles</span></span>

<span data-ttu-id="a7114-162">È possibile assegnare il materiale e il prefab per eseguire l'override dello stile dell'handle.</span><span class="sxs-lookup"><span data-stu-id="a7114-162">You can assign the material and prefab to override the handle style.</span></span> <span data-ttu-id="a7114-163">Se non vengono assegnati handle, verranno visualizzati nello stile predefinito.</span><span class="sxs-lookup"><span data-stu-id="a7114-163">If no handles are assigned, they will be displayed in the default style.</span></span>

## <a name="events"></a><span data-ttu-id="a7114-164">Eventi</span><span class="sxs-lookup"><span data-stu-id="a7114-164">Events</span></span>

<span data-ttu-id="a7114-165">Il rettangolo di selezione fornisce gli eventi seguenti.</span><span class="sxs-lookup"><span data-stu-id="a7114-165">Bounding box provides the following events.</span></span> <span data-ttu-id="a7114-166">Questo esempio usa questi eventi per riprodurre commenti e suggerimenti audio.</span><span class="sxs-lookup"><span data-stu-id="a7114-166">This example uses these events to play audio feedback.</span></span>

* <span data-ttu-id="a7114-167">**Ruota avviata:** attivato all'avvio della rotazione.</span><span class="sxs-lookup"><span data-stu-id="a7114-167">**Rotate Started**: Fired when rotation starts.</span></span>
* <span data-ttu-id="a7114-168">**Ruota terminata:** attivato al termine della rotazione.</span><span class="sxs-lookup"><span data-stu-id="a7114-168">**Rotate Ended**: Fired when rotation ends.</span></span>
* <span data-ttu-id="a7114-169">**Ridimensionamento avviato:** viene generato all'avvio del ridimensionamento.</span><span class="sxs-lookup"><span data-stu-id="a7114-169">**Scale Started**: Fires when scaling starts.</span></span>
* <span data-ttu-id="a7114-170">**Ridimensionamento terminato:** viene generato quando termina il ridimensionamento.</span><span class="sxs-lookup"><span data-stu-id="a7114-170">**Scale Ended**: Fires when scaling ends.</span></span>

<img src="../images/bounding-box/MRTK_BoundingBox_Events.png" width="450" alt="Events">

## <a name="handle-styles"></a><span data-ttu-id="a7114-171">Gestire gli stili</span><span class="sxs-lookup"><span data-stu-id="a7114-171">Handle styles</span></span>

<span data-ttu-id="a7114-172">Per impostazione predefinita, quando si assegna solo lo script, verrà visualizzato l'handle del HoloLens [`BoundingBox.cs`](xref:Microsoft.MixedReality.Toolkit.UI.BoundingBox) di prima generazione.</span><span class="sxs-lookup"><span data-stu-id="a7114-172">By default, when you just assign the [`BoundingBox.cs`](xref:Microsoft.MixedReality.Toolkit.UI.BoundingBox) script, it will show the handle of the HoloLens 1st gen style.</span></span> <span data-ttu-id="a7114-173">Per usare HoloLens 2 di stile, è necessario assegnare prefab e materiali di gestione adeguati.</span><span class="sxs-lookup"><span data-stu-id="a7114-173">To use HoloLens 2 style handles, you need to assign proper handle prefabs and materials.</span></span>

![Stili dei quadratini di selezione](../images/bounding-box/MRTK_BoundingBox_HandleStyles1.png)

<span data-ttu-id="a7114-175">Di seguito sono riportati i prefab, i materiali e i valori di scala per i punti HoloLens 2 rettangolo di selezione dello stile.</span><span class="sxs-lookup"><span data-stu-id="a7114-175">Below are the prefabs, materials, and the scaling values for the HoloLens 2 style bounding box handles.</span></span> <span data-ttu-id="a7114-176">È possibile trovare questo esempio nella `BoundingBoxExamples` scena .</span><span class="sxs-lookup"><span data-stu-id="a7114-176">You can find this example in the `BoundingBoxExamples` scene.</span></span>

<img src="../images/bounding-box/MRTK_BoundingBox_HandleStyles2.png" width="450" alt="HandStyles 2">

### <a name="handles-setup-for-hololens-2-style"></a><span data-ttu-id="a7114-177">Handle (configurazione per HoloLens 2 stile)</span><span class="sxs-lookup"><span data-stu-id="a7114-177">Handles (Setup for HoloLens 2 style)</span></span>

* <span data-ttu-id="a7114-178">**Handle Material**: BoundingBoxHandleWhite.mat</span><span class="sxs-lookup"><span data-stu-id="a7114-178">**Handle Material**: BoundingBoxHandleWhite.mat</span></span>
* <span data-ttu-id="a7114-179">**Handle Grabbed Material**: BoundingBoxHandleBlueGrabbed.mat</span><span class="sxs-lookup"><span data-stu-id="a7114-179">**Handle Grabbed Material**: BoundingBoxHandleBlueGrabbed.mat</span></span>
* <span data-ttu-id="a7114-180">**Prefab dell'handle** di scala: MRTK_BoundingBox_ScaleHandle.prefab</span><span class="sxs-lookup"><span data-stu-id="a7114-180">**Scale Handle Prefab**: MRTK_BoundingBox_ScaleHandle.prefab</span></span>
* <span data-ttu-id="a7114-181">**Scale Handle Slate Prefab**: MRTK_BoundingBox_ScaleHandle_Slate.prefab</span><span class="sxs-lookup"><span data-stu-id="a7114-181">**Scale Handle Slate Prefab**: MRTK_BoundingBox_ScaleHandle_Slate.prefab</span></span>
* <span data-ttu-id="a7114-182">**Dimensioni dell'handle di** scala: 0,016 (1,6 cm)</span><span class="sxs-lookup"><span data-stu-id="a7114-182">**Scale Handle Size**: 0.016 (1.6cm)</span></span>
* <span data-ttu-id="a7114-183">**Scale Handle Collider Padding**: 0,016 (rende il collisore afferrabile leggermente più grande dell'oggetto visivo handle)</span><span class="sxs-lookup"><span data-stu-id="a7114-183">**Scale Handle Collider Padding**: 0.016 (makes the grabbable collider slightly bigger than handle visual)</span></span>
* <span data-ttu-id="a7114-184">**Prefab dell'handle** di rotazione: MRTK_BoundingBox_RotateHandle.prefab</span><span class="sxs-lookup"><span data-stu-id="a7114-184">**Rotation Handle Prefab**: MRTK_BoundingBox_RotateHandle.prefab</span></span>
* <span data-ttu-id="a7114-185">**Dimensioni dell'handle di** rotazione: 0,016</span><span class="sxs-lookup"><span data-stu-id="a7114-185">**Rotation Handle Size**: 0.016</span></span>
* <span data-ttu-id="a7114-186">**Rotation Handle Collider Padding**: 0,016 (rende il collisore afferrabile leggermente più grande dell'oggetto visivo handle)</span><span class="sxs-lookup"><span data-stu-id="a7114-186">**Rotation Handle Collider Padding**: 0.016 (makes the grabbable collider slightly bigger than handle visual)</span></span>

### <a name="proximity-setup-for-hololens-2-style"></a><span data-ttu-id="a7114-187">Prossimità (configurazione per lo stile HoloLens 2)</span><span class="sxs-lookup"><span data-stu-id="a7114-187">Proximity (Setup for HoloLens 2 style)</span></span>

<span data-ttu-id="a7114-188">Mostrare e nascondere i quadratini di ridimensionamento con l'animazione in base alla distanza dalle mani.</span><span class="sxs-lookup"><span data-stu-id="a7114-188">Show and hide the handles with animation based on the distance to the hands.</span></span> <span data-ttu-id="a7114-189">Ha un'animazione in scala in due passaggi.</span><span class="sxs-lookup"><span data-stu-id="a7114-189">It has two-step scaling animation.</span></span>

<img src="../images/bounding-box/MRTK_BoundingBox_Proximity.png" alt="Proximity">

* <span data-ttu-id="a7114-190">**Effetto di prossimità attivo:** abilitare l'attivazione dell'handle basato sulla prossimità</span><span class="sxs-lookup"><span data-stu-id="a7114-190">**Proximity Effect Active**: Enable proximity-based handle activation</span></span>
* <span data-ttu-id="a7114-191">**Gestire la prossimità media:** distanza per il ridimensionamento del primo passaggio</span><span class="sxs-lookup"><span data-stu-id="a7114-191">**Handle Medium Proximity**: Distance for the 1st step scaling</span></span>
* <span data-ttu-id="a7114-192">**Gestire la prossimità di chiusura:** distanza per il ridimensionamento del secondo passaggio</span><span class="sxs-lookup"><span data-stu-id="a7114-192">**Handle Close Proximity**: Distance for the 2nd step scaling</span></span>
* <span data-ttu-id="a7114-193">**Scalabilità estrema:** valore di scala predefinito dell'asset handle quando le mani non sono all'interno dell'intervallo dell'interazione del rettangolo di selezione (distanza definita in precedenza da 'Handle Medium Proximity'.</span><span class="sxs-lookup"><span data-stu-id="a7114-193">**Far Scale**: Default scale value of the handle asset when the hands are out of range of the bounding box interaction (distance defined above by 'Handle Medium Proximity'.</span></span> <span data-ttu-id="a7114-194">Usare 0 per nascondere l'handle per impostazione predefinita)</span><span class="sxs-lookup"><span data-stu-id="a7114-194">Use 0 to hide handle by default)</span></span>
* <span data-ttu-id="a7114-195">**Scala media:** valore di scala dell'asset handle quando le mani si trovano entro l'intervallo dell'interazione del rettangolo di selezione (distanza definita in precedenza da 'Handle Close Proximity'.</span><span class="sxs-lookup"><span data-stu-id="a7114-195">**Medium Scale**: Scale value of the handle asset when the hands are within range of the bounding box interaction (distance defined above by 'Handle Close Proximity'.</span></span> <span data-ttu-id="a7114-196">Usare 1 per visualizzare le dimensioni normali)</span><span class="sxs-lookup"><span data-stu-id="a7114-196">Use 1 to show normal size)</span></span>
* <span data-ttu-id="a7114-197">**Scala di chiusura:** ridimensionare il valore dell'asset handle quando le mani si trovano entro l'intervallo dell'interazione di afferramento (distanza definita in precedenza da 'Handle Close Proximity'.</span><span class="sxs-lookup"><span data-stu-id="a7114-197">**Close Scale**: Scale value of the handle asset when the hands are within range of the grab interaction (distance defined above by 'Handle Close Proximity'.</span></span> <span data-ttu-id="a7114-198">Usare 1.x per visualizzare dimensioni maggiori)</span><span class="sxs-lookup"><span data-stu-id="a7114-198">Use 1.x to show bigger size)</span></span>

## <a name="making-an-object-movable-with-manipulation-handler"></a><span data-ttu-id="a7114-199">Rendere mobile un oggetto con il gestore di manipolazione</span><span class="sxs-lookup"><span data-stu-id="a7114-199">Making an object movable with manipulation handler</span></span>

<span data-ttu-id="a7114-200">Un rettangolo di selezione può essere combinato con [`ManipulationHandler.cs`](manipulation-handler.md) per rendere l'oggetto mobile usando l'interazione da lontano.</span><span class="sxs-lookup"><span data-stu-id="a7114-200">A bounding box can be combined with [`ManipulationHandler.cs`](manipulation-handler.md) to make the object movable using far interaction.</span></span> <span data-ttu-id="a7114-201">Il gestore di manipolazione supporta interazioni con una e due mani.</span><span class="sxs-lookup"><span data-stu-id="a7114-201">The manipulation handler supports both one and two-handed interactions.</span></span> <span data-ttu-id="a7114-202">[Il tracciamento](../input/hand-tracking.md) delle mani può essere usato per interagire con un oggetto da vicino.</span><span class="sxs-lookup"><span data-stu-id="a7114-202">[Hand tracking](../input/hand-tracking.md) can be used to interact with an object up close.</span></span>

<img src="../images/bounding-box/MRTK_BoundingBox_ManipulationHandler.png" width="450" alt="Manipulation Handler">

<span data-ttu-id="a7114-203">Per fare in modo che i bordi del rettangolo di selezione si comportino allo stesso modo quando lo si sposta usando l'interazione da lontano di , è consigliabile connettere rispettivamente i relativi eventi per On Manipulation Started On Manipulation Ended a , come illustrato nello [`ManipulationHandler`](manipulation-handler.md)   /   `BoundingBox.HighlightWires`  /  `BoundingBox.UnhighlightWires` screenshot precedente.</span><span class="sxs-lookup"><span data-stu-id="a7114-203">In order for the bounding box edges to behave the same way when moving it using [`ManipulationHandler`](manipulation-handler.md)'s far interaction, it is advised to connect its events for *On Manipulation Started* / *On Manipulation Ended* to `BoundingBox.HighlightWires` / `BoundingBox.UnhighlightWires` respectively, as shown in the screenshot above.</span></span>

## <a name="migrating-to-bounds-control"></a><span data-ttu-id="a7114-204">Migrazione al controllo dei limiti</span><span class="sxs-lookup"><span data-stu-id="a7114-204">Migrating to bounds control</span></span>

<span data-ttu-id="a7114-205">I prefab e [](bounding-box.md) le istanze esistenti che usano il rettangolo [](../tools/migration-window.md) di selezione possono essere aggiornati al nuovo controllo limiti tramite la finestra di migrazione che fa parte del pacchetto di strumenti MRTK.</span><span class="sxs-lookup"><span data-stu-id="a7114-205">Existing prefabs and instances using [bounding box](bounding-box.md) can be upgraded to the new bounds control via the [migration window](../tools/migration-window.md) which is part of the MRTK tools package.</span></span>

<span data-ttu-id="a7114-206">Per l'aggiornamento di singole istanze del rettangolo di selezione è disponibile anche un'opzione di migrazione all'interno del controllo proprietà del componente.</span><span class="sxs-lookup"><span data-stu-id="a7114-206">For upgrading individual instances of bounding box there's also an a migration option inside the property inspector of the component.</span></span>

<img src="../images/bounds-control/MRTK_BoundsControl_Migrate.png" width="450" alt="Bounds Control Migrate">

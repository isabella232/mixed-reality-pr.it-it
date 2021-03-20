---
title: README_BoundsControl
description: Panoramica sul controllo dei limiti in MRTK
author: thalbern
ms.author: bethalha
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, controllo dei limiti,
ms.openlocfilehash: a99a18f37a981e977d16b84eaa45b27b957d68ec
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2021
ms.locfileid: "104695248"
---
# <a name="bounds-control"></a><span data-ttu-id="68473-104">Controllo dei limiti</span><span class="sxs-lookup"><span data-stu-id="68473-104">Bounds control</span></span>

![Controllo dei limiti principale](Images/BoundsControl/MRTK_BoundsControl_Main.png)

<span data-ttu-id="68473-106">*BoundsControl* è il nuovo componente per il comportamento di manipolazione, disponibile in precedenza in *BoundingBox*.</span><span class="sxs-lookup"><span data-stu-id="68473-106">*BoundsControl* is the new component for manipulation behaviour, previously found in *BoundingBox*.</span></span> <span data-ttu-id="68473-107">Il controllo dei limiti apporta diversi miglioramenti e semplificazioni nell'installazione e aggiunge nuove funzionalità.</span><span class="sxs-lookup"><span data-stu-id="68473-107">Bounds control makes a number of improvements and simplifications in setup and adds new features.</span></span> <span data-ttu-id="68473-108">Questo componente sostituisce il rettangolo di delimitazione, che verrà deprecato.</span><span class="sxs-lookup"><span data-stu-id="68473-108">This component is a replacement for the bounding box, which will be deprecated.</span></span>

<span data-ttu-id="68473-109">Lo [`BoundsControl.cs`](xref:Microsoft.MixedReality.Toolkit.UI.BoundsControl) script fornisce funzionalità di base per la trasformazione di oggetti in realtà mista.</span><span class="sxs-lookup"><span data-stu-id="68473-109">The [`BoundsControl.cs`](xref:Microsoft.MixedReality.Toolkit.UI.BoundsControl) script provides basic functionality for transforming objects in mixed reality.</span></span> <span data-ttu-id="68473-110">Un controllo Bounds visualizzerà una casella intorno all'ologramma per indicare che è possibile interagire con.</span><span class="sxs-lookup"><span data-stu-id="68473-110">A bounds control will show a box around the hologram to indicate that it can be interacted with.</span></span> <span data-ttu-id="68473-111">Gli handle sugli angoli e sui bordi della casella consentono il ridimensionamento, la rotazione o la conversione dell'oggetto.</span><span class="sxs-lookup"><span data-stu-id="68473-111">Handles on the corners and edges of the box allow scaling, rotating or translating the object.</span></span> <span data-ttu-id="68473-112">Il controllo dei limiti reagisce anche all'input dell'utente.</span><span class="sxs-lookup"><span data-stu-id="68473-112">The bounds control also reacts to user input.</span></span> <span data-ttu-id="68473-113">In HoloLens 2, ad esempio, il controllo dei limiti risponde alla prossimità del dito, fornendo commenti visivi per facilitare la percezione della distanza dall'oggetto.</span><span class="sxs-lookup"><span data-stu-id="68473-113">On HoloLens 2, for example, the bounds control responds to finger proximity, providing visual feedback to help perceive the distance from the object.</span></span> <span data-ttu-id="68473-114">Tutte le interazioni e gli oggetti visivi possono essere facilmente personalizzati.</span><span class="sxs-lookup"><span data-stu-id="68473-114">All interactions and visuals can be easily customized.</span></span>

## <a name="example-scene"></a><span data-ttu-id="68473-115">Scena di esempio</span><span class="sxs-lookup"><span data-stu-id="68473-115">Example scene</span></span>

<span data-ttu-id="68473-116">È possibile trovare esempi di configurazioni di controllo dei limiti nella `BoundsControlExamples` scena.</span><span class="sxs-lookup"><span data-stu-id="68473-116">You can find examples of bounds control configurations in the `BoundsControlExamples` scene.</span></span>

<img src="Images/BoundsControl/MRTK_BoundsControl_Examples.png" alt="Bounds control Example">

## <a name="inspector-properties"></a><span data-ttu-id="68473-117">Proprietà di Inspector</span><span class="sxs-lookup"><span data-stu-id="68473-117">Inspector properties</span></span>

### <a name="target-object"></a><span data-ttu-id="68473-118">Oggetti di destinazione</span><span class="sxs-lookup"><span data-stu-id="68473-118">Target object</span></span>

<span data-ttu-id="68473-119">Questa proprietà specifica quale oggetto verrà trasformato dalla manipolazione del controllo dei limiti.</span><span class="sxs-lookup"><span data-stu-id="68473-119">This property specifies which object will get transformed by the bounds control manipulation.</span></span> <span data-ttu-id="68473-120">Se nessun oggetto è Setit, il valore predefinito è l'oggetto proprietario.</span><span class="sxs-lookup"><span data-stu-id="68473-120">If no object is setit defaults to the owner object.</span></span>

### <a name="activation-behavior"></a><span data-ttu-id="68473-121">Comportamento di attivazione</span><span class="sxs-lookup"><span data-stu-id="68473-121">Activation behavior</span></span>

<span data-ttu-id="68473-122">Sono disponibili diverse opzioni per attivare l'interfaccia di controllo dei limiti.</span><span class="sxs-lookup"><span data-stu-id="68473-122">There are several options to activate the bounds control interface.</span></span>

* <span data-ttu-id="68473-123">*Attiva all'avvio*: il controllo dei limiti diventa visibile una volta avviata la scena.</span><span class="sxs-lookup"><span data-stu-id="68473-123">*Activate On Start*: Bounds control becomes visible once the scene is started.</span></span>
* <span data-ttu-id="68473-124">*Activate by prossimità*: il controllo dei limiti diventa visibile quando una mano articolata è vicina all'oggetto.</span><span class="sxs-lookup"><span data-stu-id="68473-124">*Activate By Proximity*: Bounds control becomes visible when an articulated hand is close to the object.</span></span>
* <span data-ttu-id="68473-125">*Activate by Pointer*: il controllo dei limiti diventa visibile quando è di destinazione di un puntatore di raggio.</span><span class="sxs-lookup"><span data-stu-id="68473-125">*Activate By Pointer*: Bounds control becomes visible when it is targeted by a hand-ray pointer.</span></span>
* <span data-ttu-id="68473-126">*Activate by prossimità e Pointer*: il controllo dei limiti diventa visibile quando è di destinazione di un puntatore a mano o una mano articolata è vicina all'oggetto.</span><span class="sxs-lookup"><span data-stu-id="68473-126">*Activate By Proximity and Pointer*: Bounds control becomes visible when it is targeted by a hand-ray pointer or an articulated hand is close to the object.</span></span>
* <span data-ttu-id="68473-127">*Attiva manualmente*: il controllo dei limiti non diventa visibile automaticamente.</span><span class="sxs-lookup"><span data-stu-id="68473-127">*Activate Manually*: Bounds control does not become visible automatically.</span></span> <span data-ttu-id="68473-128">È possibile attivarla manualmente tramite uno script accedendo alla proprietà boundsControl. Active.</span><span class="sxs-lookup"><span data-stu-id="68473-128">You can manually activate it through a script by accessing the boundsControl.Active property.</span></span>

### <a name="bounds-override"></a><span data-ttu-id="68473-129">Override dei limiti</span><span class="sxs-lookup"><span data-stu-id="68473-129">Bounds override</span></span>

<span data-ttu-id="68473-130">Imposta un Collider di box dall'oggetto per il calcolo dei limiti.</span><span class="sxs-lookup"><span data-stu-id="68473-130">Sets a box collider from the object for bounds computation.</span></span>

### <a name="box-padding"></a><span data-ttu-id="68473-131">Riempimento Box</span><span class="sxs-lookup"><span data-stu-id="68473-131">Box padding</span></span>

<span data-ttu-id="68473-132">Aggiunge una spaziatura interna ai limiti del Collider utilizzati per calcolare gli extent del controllo.</span><span class="sxs-lookup"><span data-stu-id="68473-132">Adds a padding to the collider bounds used to calculate the extents of the control.</span></span> <span data-ttu-id="68473-133">Questo influirà non solo sull'interazione, ma anche sugli oggetti visivi.</span><span class="sxs-lookup"><span data-stu-id="68473-133">This will influence not only interaction but also impact the visuals.</span></span>

### <a name="flatten-axis"></a><span data-ttu-id="68473-134">Asse Flat</span><span class="sxs-lookup"><span data-stu-id="68473-134">Flatten axis</span></span>

<span data-ttu-id="68473-135">Indica se il controllo è bidimensionale in uno degli assi, rendendolo 2 dimensionale e non consente la manipolazione lungo tale asse.</span><span class="sxs-lookup"><span data-stu-id="68473-135">Indicates whether the control is flattened in one of the axes, making it 2 dimensional and disallowing manipulation along that axis.</span></span> <span data-ttu-id="68473-136">Questa funzionalità può essere usata per oggetti Thin come Slate.</span><span class="sxs-lookup"><span data-stu-id="68473-136">This feature can be used for thin objects like slates.</span></span>
<span data-ttu-id="68473-137">Se l'asse appiattito è impostato su *appiattimento automatico* , lo script sceglierà automaticamente l'asse con l'extent più piccolo come asse bidimensionale.</span><span class="sxs-lookup"><span data-stu-id="68473-137">If flatten axis is set to *Flatten Auto* the script will automatically pick the axis with the smallest extent as flatten axis.</span></span>

### <a name="smoothing"></a><span data-ttu-id="68473-138">Definizione di movimenti uniformi</span><span class="sxs-lookup"><span data-stu-id="68473-138">Smoothing</span></span>

<span data-ttu-id="68473-139">La sezione smoothing consente di configurare il comportamento di smussatura per la scala e la rotazione del controllo.</span><span class="sxs-lookup"><span data-stu-id="68473-139">The smoothing section allows to configure smoothing behavior for scale and rotate of the control.</span></span>

### <a name="visuals"></a><span data-ttu-id="68473-140">Oggetti visivi</span><span class="sxs-lookup"><span data-stu-id="68473-140">Visuals</span></span>

<span data-ttu-id="68473-141">L'aspetto del controllo dei limiti può essere configurato modificando una delle configurazioni degli oggetti visivi corrispondenti.</span><span class="sxs-lookup"><span data-stu-id="68473-141">The appearance of bounds control can be configured by modifying one of the corresponding visuals configurations.</span></span>
<span data-ttu-id="68473-142">Le configurazioni visive sono oggetti collegati o con script inline e sono descritti in modo più dettagliato nella [sezione oggetto di configurazione](#configuration-objects).</span><span class="sxs-lookup"><span data-stu-id="68473-142">Visual configurations are either linked or inlined scriptable objects and are described in more detail in the [configuration object section](#configuration-objects).</span></span>

## <a name="configuration-objects"></a><span data-ttu-id="68473-143">Oggetti di configurazione</span><span class="sxs-lookup"><span data-stu-id="68473-143">Configuration Objects</span></span>

<span data-ttu-id="68473-144">Il controllo include un set di oggetti di configurazione che possono essere archiviati come oggetti configurabili tramite script e condivisi tra istanze diverse o prefabbricati.</span><span class="sxs-lookup"><span data-stu-id="68473-144">The control comes with a set of configuration objects that can be stored as scriptable objects and shared between different instances or prefabs.</span></span> <span data-ttu-id="68473-145">Le configurazioni possono essere condivise e collegate come singoli file di asset gestibili tramite script o asset annidabili tramite script all'interno di prefabbricati.</span><span class="sxs-lookup"><span data-stu-id="68473-145">Configurations can be shared and linked either as individual scriptable asset files or nested scriptable assets inside of prefabs.</span></span> <span data-ttu-id="68473-146">È anche possibile definire altre configurazioni direttamente nell'istanza senza eseguire il collegamento a un asset con script esterno o annidato.</span><span class="sxs-lookup"><span data-stu-id="68473-146">Further configurations can also be defined directly on the instance without linking to an external or nested scriptable asset.</span></span>

<span data-ttu-id="68473-147">Il controllo dei limiti indicherà se una configurazione è condivisa o inline come parte dell'istanza corrente visualizzando un messaggio nel controllo proprietà.</span><span class="sxs-lookup"><span data-stu-id="68473-147">The bounds control inspector will indicate whether a configuration is shared or inlined as part of the current instance by showing a message in the property inspector.</span></span> <span data-ttu-id="68473-148">Inoltre, le istanze condivise non saranno modificabili direttamente nella finestra delle proprietà del controllo dei limiti, ma l'asset a cui è collegato deve essere direttamente modificati per evitare modifiche accidentali nelle configurazioni condivise.</span><span class="sxs-lookup"><span data-stu-id="68473-148">In addition shared instances won't be editable directly in the bounds control property window itself, but instead the asset it's linking to has to be directly modfied to avoid any accidental changes on shared configurations.</span></span>

<span data-ttu-id="68473-149">Il controllo attualmente associato offre le opzioni degli oggetti di configurazione per le seguenti funzionalità:</span><span class="sxs-lookup"><span data-stu-id="68473-149">Currently bounds control offers configuration objects options for the following features:</span></span>

* <span data-ttu-id="68473-150">Selettori</span><span class="sxs-lookup"><span data-stu-id="68473-150">Handles</span></span>
  * [<span data-ttu-id="68473-151">Quadratini di ridimensionamento</span><span class="sxs-lookup"><span data-stu-id="68473-151">Scale handles</span></span>](#scale-handles-configuration)
  * [<span data-ttu-id="68473-152">Handle di rotazione</span><span class="sxs-lookup"><span data-stu-id="68473-152">Rotation handles</span></span>](#rotation-handles-configuration)
  * [<span data-ttu-id="68473-153">Handle di traduzione</span><span class="sxs-lookup"><span data-stu-id="68473-153">Translation handles</span></span>](#translation-handles-configuration)
* [<span data-ttu-id="68473-154">Collegamenti/wireframe</span><span class="sxs-lookup"><span data-stu-id="68473-154">Links / Wireframe</span></span>](#Links-configuration-wireframe)
* [<span data-ttu-id="68473-155">Visualizzazione box</span><span class="sxs-lookup"><span data-stu-id="68473-155">Box display</span></span>](#box-configuration)
* [<span data-ttu-id="68473-156">Effetto di prossimità</span><span class="sxs-lookup"><span data-stu-id="68473-156">Proximity effect</span></span>](#proximity-effect-configuration)

### <a name="box-configuration"></a><span data-ttu-id="68473-157">Configurazione box</span><span class="sxs-lookup"><span data-stu-id="68473-157">Box configuration</span></span>

<span data-ttu-id="68473-158">La configurazione box è responsabile del rendering di una casella a tinta unita con i limiti definiti tramite le dimensioni del Collider e la spaziatura interna.</span><span class="sxs-lookup"><span data-stu-id="68473-158">The box configuration is responsible for rendering a solid box with bounds defined via collider size and box padding.</span></span> <span data-ttu-id="68473-159">È possibile configurare le proprietà seguenti:</span><span class="sxs-lookup"><span data-stu-id="68473-159">The following properties can be set up:</span></span>

* <span data-ttu-id="68473-160">**Box Material**: definisce il materiale applicato alla casella di cui è stato eseguito il rendering quando non si verifica alcuna interazione.</span><span class="sxs-lookup"><span data-stu-id="68473-160">**Box material**: defines the material applied to the rendered box when no interaction takes place.</span></span> <span data-ttu-id="68473-161">Se questo materiale è impostato, verrà eseguito il rendering di una casella.</span><span class="sxs-lookup"><span data-stu-id="68473-161">A box will only be rendered if this material is set.</span></span>
* <span data-ttu-id="68473-162">**Materiale afferrato da box**: materiale per la casella quando l'utente interagisce con il controllo afferrando un'interazione quasi o lontano.</span><span class="sxs-lookup"><span data-stu-id="68473-162">**Box grabbed material**: material for the box when the user interacts with the control by grabbing via near or far interaction.</span></span>
* <span data-ttu-id="68473-163">**Scala di visualizzazione dell'asse Flat**: una scala applicata alla casella viene visualizzata se uno degli assi è [bidimensionale](#flatten-axis).</span><span class="sxs-lookup"><span data-stu-id="68473-163">**Flatten axis display scale**: a scale that is applied to the box display if one of the axes is [flattened](#flatten-axis).</span></span>

### <a name="scale-handles-configuration"></a><span data-ttu-id="68473-164">Configurazione degli handle di scala</span><span class="sxs-lookup"><span data-stu-id="68473-164">Scale handles configuration</span></span>

<span data-ttu-id="68473-165">Questo cassetto delle proprietà consente di modificare il comportamento e la visualizzazione degli handle di ridimensionamento del controllo dei limiti.</span><span class="sxs-lookup"><span data-stu-id="68473-165">This property drawer allows to modify behavior and visualization of scale handles of bounds control.</span></span>

* <span data-ttu-id="68473-166">**Gestione materiale**: materiale applicato agli handle.</span><span class="sxs-lookup"><span data-stu-id="68473-166">**Handle material**: material applied to the handles.</span></span>
* <span data-ttu-id="68473-167">**Gestire il materiale afferrato**: materiale applicato al punto di manipolazione.</span><span class="sxs-lookup"><span data-stu-id="68473-167">**Handle grabbed material**: material applied to the grabbed handle.</span></span>
* <span data-ttu-id="68473-168">**Gestione prefabbricata**: precostruzione facoltativa per il quadratino di ridimensionamento.</span><span class="sxs-lookup"><span data-stu-id="68473-168">**Handle prefab**: optional prefab for the scale handle.</span></span> <span data-ttu-id="68473-169">Se non è impostato, MRTK utilizzerà un cubo come predefinito.</span><span class="sxs-lookup"><span data-stu-id="68473-169">If non is set MRTK will use a cube as default.</span></span>
* <span data-ttu-id="68473-170">**Dimensioni handle**: dimensioni del quadratino di ridimensionamento.</span><span class="sxs-lookup"><span data-stu-id="68473-170">**Handle size**: size of the scale handle.</span></span>
* <span data-ttu-id="68473-171">**Riempimento del Collider**: riempimento da aggiungere al Collider dell'handle.</span><span class="sxs-lookup"><span data-stu-id="68473-171">**Collider padding**: padding to add to the handle collider.</span></span>
* <span data-ttu-id="68473-172">Crea il **tethering quando si modifica**: quando attivo crea una linea di tethering dal punto di inizio dell'interazione alla posizione corrente o al puntatore.</span><span class="sxs-lookup"><span data-stu-id="68473-172">**Draw tether when manipulating**: when active will draw a tether line from point of start of interaction to current hand or pointer position.</span></span>
* <span data-ttu-id="68473-173">**Handles ignora Collider**: se un Collider viene collegato qui, gli handle ignoreranno eventuali conflitti con questo Collider.</span><span class="sxs-lookup"><span data-stu-id="68473-173">**Handles ignore collider**: if a collider gets linked here, handles will ignore any collision with this collider.</span></span>
* <span data-ttu-id="68473-174">**Gestire la prefabbricata dello Slate**: prefabbricato da usare per l'handle quando il controllo è bidimensionale.</span><span class="sxs-lookup"><span data-stu-id="68473-174">**Handle slate prefab**: prefab to use for the handle when the control is flattened.</span></span>
* <span data-ttu-id="68473-175">**Mostra quadratini di ridimensionamento**: controlla la visibilità dell'handle.</span><span class="sxs-lookup"><span data-stu-id="68473-175">**Show scale handles**: controls visibility of the handle.</span></span>
* <span data-ttu-id="68473-176">**Comportamento della scalabilità**: può essere impostato su una scala uniforme o non uniforme.</span><span class="sxs-lookup"><span data-stu-id="68473-176">**Scale behavior**: can be set to uniform or non-uniform scaling.</span></span>

### <a name="rotation-handles-configuration"></a><span data-ttu-id="68473-177">Configurazione handle di rotazione</span><span class="sxs-lookup"><span data-stu-id="68473-177">Rotation handles configuration</span></span>

<span data-ttu-id="68473-178">Questa configurazione definisce il comportamento dell'handle di rotazione.</span><span class="sxs-lookup"><span data-stu-id="68473-178">This configuration defines the rotation handle behavior.</span></span>

* <span data-ttu-id="68473-179">**Gestione materiale**: materiale applicato agli handle.</span><span class="sxs-lookup"><span data-stu-id="68473-179">**Handle material**: material applied to the handles.</span></span>
* <span data-ttu-id="68473-180">**Gestire il materiale afferrato**: materiale applicato al punto di manipolazione.</span><span class="sxs-lookup"><span data-stu-id="68473-180">**Handle grabbed material**: material applied to the grabbed handle.</span></span>
* <span data-ttu-id="68473-181">**Gestisci prefabbricati**: precostruzione facoltativa per l'handle.</span><span class="sxs-lookup"><span data-stu-id="68473-181">**Handle prefab**: optional prefab for the handle.</span></span> <span data-ttu-id="68473-182">Se non è impostato, MRTK utilizzerà una sfera come predefinita.</span><span class="sxs-lookup"><span data-stu-id="68473-182">If non is set MRTK will use a sphere as default.</span></span>
* <span data-ttu-id="68473-183">**Dimensioni handle**: dimensioni dell'handle.</span><span class="sxs-lookup"><span data-stu-id="68473-183">**Handle size**: size of the handle.</span></span>
* <span data-ttu-id="68473-184">**Riempimento del Collider**: riempimento da aggiungere al Collider dell'handle.</span><span class="sxs-lookup"><span data-stu-id="68473-184">**Collider padding**: padding to add to the handle collider.</span></span>
* <span data-ttu-id="68473-185">Crea il **tethering quando si modifica**: quando attivo crea una linea di tethering dal punto di inizio dell'interazione alla posizione corrente o al puntatore.</span><span class="sxs-lookup"><span data-stu-id="68473-185">**Draw tether when manipulating**: when active will draw a tether line from point of start of interaction to current hand or pointer position.</span></span>
* <span data-ttu-id="68473-186">**Handles ignora Collider**: se un Collider viene collegato qui, gli handle ignoreranno eventuali conflitti con questo Collider.</span><span class="sxs-lookup"><span data-stu-id="68473-186">**Handles ignore collider**: if a collider gets linked here, handles will ignore any collision with this collider.</span></span>
* <span data-ttu-id="68473-187">**Gestisci tipo di Collider prefabbricato**: tipo di Collider da usare con l'handle creato.</span><span class="sxs-lookup"><span data-stu-id="68473-187">**Handle prefab collider type**: collider type to be used with the created handle.</span></span>
* <span data-ttu-id="68473-188">**Mostra handle per x**: controlla la visibilità dell'handle per l'asse x.</span><span class="sxs-lookup"><span data-stu-id="68473-188">**Show handle for X**: controls visibility of the handle for X axis.</span></span>
* <span data-ttu-id="68473-189">**Mostra handle per y**: controlla la visibilità dell'handle per l'asse y.</span><span class="sxs-lookup"><span data-stu-id="68473-189">**Show handle for Y**: controls visibility of the handle for Y axis.</span></span>
* <span data-ttu-id="68473-190">**Mostra handle per z**: controlla la visibilità dell'handle per l'asse z.</span><span class="sxs-lookup"><span data-stu-id="68473-190">**Show handle for Z**: controls visibility of the handle for Z axis.</span></span>

### <a name="translation-handles-configuration"></a><span data-ttu-id="68473-191">Gestione della configurazione</span><span class="sxs-lookup"><span data-stu-id="68473-191">Translation handles configuration</span></span>

<span data-ttu-id="68473-192">Consente di abilitare e configurare gli handle di conversione per il controllo dei limiti.</span><span class="sxs-lookup"><span data-stu-id="68473-192">Allows enabling and configuring translation handles for bounds control.</span></span> <span data-ttu-id="68473-193">Si noti che gli handle di conversione sono disabilitati per impostazione predefinita.</span><span class="sxs-lookup"><span data-stu-id="68473-193">Note that translation handles are disabled per default.</span></span>

* <span data-ttu-id="68473-194">**Gestione materiale**: materiale applicato agli handle.</span><span class="sxs-lookup"><span data-stu-id="68473-194">**Handle material**: material applied to the handles.</span></span>
* <span data-ttu-id="68473-195">**Gestire il materiale afferrato**: materiale applicato al punto di manipolazione.</span><span class="sxs-lookup"><span data-stu-id="68473-195">**Handle grabbed material**: material applied to the grabbed handle.</span></span>
* <span data-ttu-id="68473-196">**Gestisci prefabbricati**: precostruzione facoltativa per l'handle.</span><span class="sxs-lookup"><span data-stu-id="68473-196">**Handle prefab**: optional prefab for the handle.</span></span> <span data-ttu-id="68473-197">Se non è impostato, MRTK utilizzerà una sfera come predefinita.</span><span class="sxs-lookup"><span data-stu-id="68473-197">If non is set MRTK will use a sphere as default.</span></span>
* <span data-ttu-id="68473-198">**Dimensioni handle**: dimensioni dell'handle.</span><span class="sxs-lookup"><span data-stu-id="68473-198">**Handle size**: size of the handle.</span></span>
* <span data-ttu-id="68473-199">**Riempimento del Collider**: riempimento da aggiungere al Collider dell'handle.</span><span class="sxs-lookup"><span data-stu-id="68473-199">**Collider padding**: padding to add to the handle collider.</span></span>
* <span data-ttu-id="68473-200">Crea il **tethering quando si modifica**: quando attivo crea una linea di tethering dal punto di inizio dell'interazione alla posizione corrente o al puntatore.</span><span class="sxs-lookup"><span data-stu-id="68473-200">**Draw tether when manipulating**: when active will draw a tether line from point of start of interaction to current hand or pointer position.</span></span>
* <span data-ttu-id="68473-201">**Handles ignora Collider**: se un Collider viene collegato qui, gli handle ignoreranno eventuali conflitti con questo Collider.</span><span class="sxs-lookup"><span data-stu-id="68473-201">**Handles ignore collider**: if a collider gets linked here, handles will ignore any collision with this collider.</span></span>
* <span data-ttu-id="68473-202">**Gestisci tipo di Collider prefabbricato**: tipo di Collider da usare con l'handle creato.</span><span class="sxs-lookup"><span data-stu-id="68473-202">**Handle prefab collider type**: collider type to be used with the created handle.</span></span>
* <span data-ttu-id="68473-203">**Mostra handle per x**: controlla la visibilità dell'handle per l'asse x.</span><span class="sxs-lookup"><span data-stu-id="68473-203">**Show handle for X**: controls visibility of the handle for X axis.</span></span>
* <span data-ttu-id="68473-204">**Mostra handle per y**: controlla la visibilità dell'handle per l'asse y.</span><span class="sxs-lookup"><span data-stu-id="68473-204">**Show handle for Y**: controls visibility of the handle for Y axis.</span></span>
* <span data-ttu-id="68473-205">**Mostra handle per z**: controlla la visibilità dell'handle per l'asse z.</span><span class="sxs-lookup"><span data-stu-id="68473-205">**Show handle for Z**: controls visibility of the handle for Z axis.</span></span>

### <a name="links-configuration-wireframe"></a><span data-ttu-id="68473-206">Configurazione collegamenti (wireframe)</span><span class="sxs-lookup"><span data-stu-id="68473-206">Links configuration (wireframe)</span></span>

<span data-ttu-id="68473-207">La configurazione dei collegamenti consente la funzionalità wireframe del controllo dei limiti.</span><span class="sxs-lookup"><span data-stu-id="68473-207">The links configuration enables the wireframe feature of bounds control.</span></span> <span data-ttu-id="68473-208">È possibile configurare le proprietà seguenti:</span><span class="sxs-lookup"><span data-stu-id="68473-208">The following properties can be configured:</span></span>

* <span data-ttu-id="68473-209">**Wireframe Material**: materiale applicato alla mesh wireframe.</span><span class="sxs-lookup"><span data-stu-id="68473-209">**Wireframe material**: the material applied to the wireframe mesh.</span></span>
* <span data-ttu-id="68473-210">**Raggio perimetrale wireframe**: spessore del wireframe.</span><span class="sxs-lookup"><span data-stu-id="68473-210">**Wireframe edge radius**: the thickness of the wireframe.</span></span>
* <span data-ttu-id="68473-211">**Forma wireframe**: la forma del wireframe può essere cubica o cilindrica.</span><span class="sxs-lookup"><span data-stu-id="68473-211">**Wireframe shape**: shape of the wireframe can by either cubic or cylindrical.</span></span>
* <span data-ttu-id="68473-212">**Mostra wireframe**: controlla la visibilità del wireframe.</span><span class="sxs-lookup"><span data-stu-id="68473-212">**Show wireframe**: controls visibility of the wireframe.</span></span>

### <a name="proximity-effect-configuration"></a><span data-ttu-id="68473-213">Configurazione degli effetti di prossimità</span><span class="sxs-lookup"><span data-stu-id="68473-213">Proximity effect configuration</span></span>

<span data-ttu-id="68473-214">Mostra e nasconde gli handle con animazione in base alla distanza delle lancette.</span><span class="sxs-lookup"><span data-stu-id="68473-214">Show and hide the handles with animation based on the distance to the hands.</span></span> <span data-ttu-id="68473-215">Ha un'animazione di ridimensionamento in due passaggi.</span><span class="sxs-lookup"><span data-stu-id="68473-215">It has two-step scaling animation.</span></span> <span data-ttu-id="68473-216">Le impostazioni predefinite sono impostate sul comportamento dello stile Hololens 2.</span><span class="sxs-lookup"><span data-stu-id="68473-216">Defaults are set to Hololens 2 style behavior.</span></span>

<img src="Images/BoundsControl/MRTK_BoundsControl_Proximity.png" alt="Bounds control Proximity">

* <span data-ttu-id="68473-217">**Effetto di prossimità attivo**: Abilita l'attivazione dell'handle basata sulla prossimità</span><span class="sxs-lookup"><span data-stu-id="68473-217">**Proximity Effect Active**: Enable proximity-based handle activation</span></span>
* <span data-ttu-id="68473-218">**Prossimità dell'oggetto**: distanza per il ridimensionamento del primo passaggio</span><span class="sxs-lookup"><span data-stu-id="68473-218">**Object Medium Proximity**: Distance for the 1st step scaling</span></span>
* <span data-ttu-id="68473-219">**Prossimità dell'oggetto**: distanza per la scala del secondo passaggio</span><span class="sxs-lookup"><span data-stu-id="68473-219">**Object Close Proximity**: Distance for the 2nd step scaling</span></span>
* <span data-ttu-id="68473-220">**Scalabilità orizzontale**: valore di scala predefinito dell'asset dell'handle quando le mani non rientrano nell'intervallo dell'interazione del controllo dei limiti (distanza definita in precedenza da' handle media prossimità').</span><span class="sxs-lookup"><span data-stu-id="68473-220">**Far Scale**: Default scale value of the handle asset when the hands are out of range of the bounds control interaction (distance defined above by 'Handle Medium Proximity'.</span></span> <span data-ttu-id="68473-221">Utilizzare 0 per nascondere l'handle per impostazione predefinita)</span><span class="sxs-lookup"><span data-stu-id="68473-221">Use 0 to hide handle by default)</span></span>
* <span data-ttu-id="68473-222">**Scala media**: valore di scala dell'asset dell'handle quando le lancette sono comprese nell'intervallo di interazione del controllo dei limiti (distanza definita in precedenza da' handle Close prossimità').</span><span class="sxs-lookup"><span data-stu-id="68473-222">**Medium Scale**: Scale value of the handle asset when the hands are within range of the bounds control interaction (distance defined above by 'Handle Close Proximity'.</span></span> <span data-ttu-id="68473-223">Utilizzare 1 per mostrare le dimensioni normali)</span><span class="sxs-lookup"><span data-stu-id="68473-223">Use 1 to show normal size)</span></span>
* <span data-ttu-id="68473-224">**Close scale**: valore di scala dell'asset dell'handle quando le lancette sono comprese nell'intervallo dell'interazione di cattura (distanza definita in precedenza da' handle Close prossimità'.</span><span class="sxs-lookup"><span data-stu-id="68473-224">**Close Scale**: Scale value of the handle asset when the hands are within range of the grab interaction (distance defined above by 'Handle Close Proximity'.</span></span> <span data-ttu-id="68473-225">Usare 1. x per visualizzare dimensioni maggiori)</span><span class="sxs-lookup"><span data-stu-id="68473-225">Use 1.x to show bigger size)</span></span>
* <span data-ttu-id="68473-226">**Tasso di crescita molto** maggiore: la velocità di un oggetto con scalabilità di prossimità viene ridimensionata quando la mano passa da media a prossimità.</span><span class="sxs-lookup"><span data-stu-id="68473-226">**Far Grow Rate**: Rate a proximity scaled object scales when the hand moves from medium to far proximity.</span></span>
* <span data-ttu-id="68473-227">**Velocità di crescita media**: la velocità di un oggetto con scalabilità ridotta viene ridimensionata quando la mano passa dalla prossimità media alla chiusura.</span><span class="sxs-lookup"><span data-stu-id="68473-227">**Medium Grow Rate**: Rate a proximity scaled object scales when the hand moves from medium to close proximity.</span></span>
* <span data-ttu-id="68473-228">**Frequenza di aumento delle dimensioni**: frequenza di ridimensionamento di un oggetto con scalabilità in caso di spostamento della mano da prossimità a centro oggetti.</span><span class="sxs-lookup"><span data-stu-id="68473-228">**Close Grow Rate**: Rate a proximity scaled object scales when the hand moves from close proximity to object center.</span></span>

## <a name="constraint-system"></a><span data-ttu-id="68473-229">Sistema di vincoli</span><span class="sxs-lookup"><span data-stu-id="68473-229">Constraint System</span></span>

<span data-ttu-id="68473-230">Il controllo dei limiti supporta l'utilizzo di [Gestione vincoli](README_ConstraintManager.md) per limitare o modificare il comportamento di conversione, rotazione o scalabilità durante l'utilizzo di handle di controllo dei limiti.</span><span class="sxs-lookup"><span data-stu-id="68473-230">Bounds control supports using the [constraint manager](README_ConstraintManager.md) to limit or modify translation, rotation or scaling behavior while using bounds control handles.</span></span>

<span data-ttu-id="68473-231">Il controllo proprietà mostrerà tutti i gestori di vincoli disponibili collegati allo stesso oggetto gioco in un dropwdown con un'opzione per scorrere ed evidenziare il gestore di vincoli selezionato.</span><span class="sxs-lookup"><span data-stu-id="68473-231">The property inspector will show all available constraint managers attached to the same game object in a dropwdown with an option to scroll and highlight the selected constraint manager.</span></span>

<img src="Images/BoundsControl/MRTK_BoundsControl_Constraints.png" width="450" alt="Bounds control Constraints">

## <a name="events"></a><span data-ttu-id="68473-232">Eventi</span><span class="sxs-lookup"><span data-stu-id="68473-232">Events</span></span>

<span data-ttu-id="68473-233">Il controllo dei limiti fornisce gli eventi seguenti.</span><span class="sxs-lookup"><span data-stu-id="68473-233">Bounds control provides the following events.</span></span> <span data-ttu-id="68473-234">Questo esempio usa questi eventi per riprodurre commenti audio.</span><span class="sxs-lookup"><span data-stu-id="68473-234">This example uses these events to play audio feedback.</span></span>

* <span data-ttu-id="68473-235">**Rotazione avviata**: attivata all'avvio della rotazione.</span><span class="sxs-lookup"><span data-stu-id="68473-235">**Rotate Started**: Fired when rotation starts.</span></span>
* <span data-ttu-id="68473-236">**Rotazione arrestata**: generata quando viene arrestata la rotazione.</span><span class="sxs-lookup"><span data-stu-id="68473-236">**Rotate Stopped**: Fired when rotation stops.</span></span>
* <span data-ttu-id="68473-237">**Scale started**: viene attivato all'avvio del ridimensionamento.</span><span class="sxs-lookup"><span data-stu-id="68473-237">**Scale Started**: Fires when scaling starts.</span></span>
* <span data-ttu-id="68473-238">**Scale Stopped**: viene attivato quando si arresta il ridimensionamento.</span><span class="sxs-lookup"><span data-stu-id="68473-238">**Scale Stopped**: Fires when scaling stops.</span></span>
* <span data-ttu-id="68473-239">**Translate started**: viene attivato all'avvio della conversione.</span><span class="sxs-lookup"><span data-stu-id="68473-239">**Translate Started**: Fires when translation starts.</span></span>
* <span data-ttu-id="68473-240">**Translate Stopped**: viene attivato quando la conversione viene arrestata.</span><span class="sxs-lookup"><span data-stu-id="68473-240">**Translate Stopped**: Fires when translation stops.</span></span>

<img src="Images/BoundsControl/MRTK_BoundsControl_Events.png" width="450" alt="Bounds control Events">

## <a name="elastics-experimental"></a><span data-ttu-id="68473-241">Elastici (sperimentale)</span><span class="sxs-lookup"><span data-stu-id="68473-241">Elastics (Experimental)</span></span>

<span data-ttu-id="68473-242">Gli elastici possono essere usati per la manipolazione di oggetti tramite il controllo dei limiti.</span><span class="sxs-lookup"><span data-stu-id="68473-242">Elastics can be used when manipulating objects via bounds control.</span></span> <span data-ttu-id="68473-243">Si noti che il [sistema elastico](Elastics/ElasticSystem.md) è ancora in stato sperimentale.</span><span class="sxs-lookup"><span data-stu-id="68473-243">Note that the [elastics system](Elastics/ElasticSystem.md) is still in experimental state.</span></span> <span data-ttu-id="68473-244">Per abilitare gli elastici, collegare un componente di gestione elastici esistente o creare e collegare un nuovo gestore elastici tramite il `Add Elastics Manager` pulsante.</span><span class="sxs-lookup"><span data-stu-id="68473-244">To enable elastics either link an existing elastics manager component or create and link a new elastics manager via the `Add Elastics Manager` button.</span></span>

<img src="Images/BoundsControl/MRTK_BoundsControl_Elastics.png" width="450" alt="Bounds control Elastics">

## <a name="handle-styles"></a><span data-ttu-id="68473-245">Stili di gestione</span><span class="sxs-lookup"><span data-stu-id="68473-245">Handle styles</span></span>

<span data-ttu-id="68473-246">Per impostazione predefinita, quando si assegna semplicemente lo [`BoundsControl.cs`](xref:Microsoft.MixedReality.Toolkit.UI.BoundsControl) script, verrà visualizzato l'handle dello stile HoloLens 1st Gen.</span><span class="sxs-lookup"><span data-stu-id="68473-246">By default, when you just assign the [`BoundsControl.cs`](xref:Microsoft.MixedReality.Toolkit.UI.BoundsControl) script, it will show the handle of the HoloLens 1st gen style.</span></span> <span data-ttu-id="68473-247">Per usare gli handle di stile HoloLens 2, è necessario assegnare i materiali e i prefabbricati di handle appropriati.</span><span class="sxs-lookup"><span data-stu-id="68473-247">To use HoloLens 2 style handles, you need to assign proper handle prefabs and materials.</span></span>

![Stile handle di controllo dei limiti 1](Images/BoundsControl/MRTK_BoundsControl_HandleStyles1.png)

<span data-ttu-id="68473-249">Di seguito sono riportati i prefabbricati, i materiali e i valori di ridimensionamento per gli handle di controllo dei limiti di stile HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="68473-249">Below are the prefabs, materials, and the scaling values for the HoloLens 2 style bounds control handles.</span></span> <span data-ttu-id="68473-250">Questo esempio è reperibile nella `BoundsControlExamples` scena.</span><span class="sxs-lookup"><span data-stu-id="68473-250">You can find this example in the `BoundsControlExamples` scene.</span></span>

<img src="Images/BoundsControl/MRTK_BoundsControl_HandleStyles2.png" width="450" alt="Bounds control Handlestyles 2">

### <a name="handles-setup-for-hololens-2-style"></a><span data-ttu-id="68473-251">Handle (impostazione per lo stile HoloLens 2)</span><span class="sxs-lookup"><span data-stu-id="68473-251">Handles (Setup for HoloLens 2 style)</span></span>

* <span data-ttu-id="68473-252">**Gestione del materiale**: BoundingBoxHandleWhite. Mat</span><span class="sxs-lookup"><span data-stu-id="68473-252">**Handle Material**: BoundingBoxHandleWhite.mat</span></span>
* <span data-ttu-id="68473-253">**Gestire il materiale afferrato**: BoundingBoxHandleBlueGrabbed. Mat</span><span class="sxs-lookup"><span data-stu-id="68473-253">**Handle Grabbed Material**: BoundingBoxHandleBlueGrabbed.mat</span></span>
* <span data-ttu-id="68473-254">**Dimensioni prefabbricate del quadratino di ridimensionamento**: MRTK_BoundingBox_ScaleHandle</span><span class="sxs-lookup"><span data-stu-id="68473-254">**Scale Handle Prefab**: MRTK_BoundingBox_ScaleHandle.prefab</span></span>
* <span data-ttu-id="68473-255">**Ridimensionare il quadratino di tabulazione**: MRTK_BoundingBox_ScaleHandle_Slate. prefabbricate</span><span class="sxs-lookup"><span data-stu-id="68473-255">**Scale Handle Slate Prefab**: MRTK_BoundingBox_ScaleHandle_Slate.prefab</span></span>
* <span data-ttu-id="68473-256">**Dimensioni del quadratino di ridimensionamento**: 0,016 (1,6 cm)</span><span class="sxs-lookup"><span data-stu-id="68473-256">**Scale Handle Size**: 0.016 (1.6cm)</span></span>
* <span data-ttu-id="68473-257">**Riempimento del Collider del gestore di scalabilità**: 0,016 (rende l'oggetto Collider afferrabile leggermente più grande rispetto alla gestione degli oggetti visivi)</span><span class="sxs-lookup"><span data-stu-id="68473-257">**Scale Handle Collider Padding**: 0.016 (makes the grabbable collider slightly bigger than handle visual)</span></span>
* <span data-ttu-id="68473-258">**Maniglie prefabbricate di rotazione**: MRTK_BoundingBox_RotateHandle</span><span class="sxs-lookup"><span data-stu-id="68473-258">**Rotation Handle Prefab**: MRTK_BoundingBox_RotateHandle.prefab</span></span>
* <span data-ttu-id="68473-259">**Dimensioni handle di rotazione**: 0,016</span><span class="sxs-lookup"><span data-stu-id="68473-259">**Rotation Handle Size**: 0.016</span></span>
* <span data-ttu-id="68473-260">**Riempimento del Collider dell'handle di rotazione**: 0,016 (rende l'oggetto Collider afferrabile leggermente più grande rispetto alla gestione degli oggetti visivi)</span><span class="sxs-lookup"><span data-stu-id="68473-260">**Rotation Handle Collider Padding**: 0.016 (makes the grabbable collider slightly bigger than handle visual)</span></span>

## <a name="transformation-changes-with-object-manipulator"></a><span data-ttu-id="68473-261">Modifiche alla trasformazione con manipolatore oggetti</span><span class="sxs-lookup"><span data-stu-id="68473-261">Transformation changes with object manipulator</span></span>

<span data-ttu-id="68473-262">Un controllo Bounds può essere usato in combinazione con [`ObjectManipulator.cs`](README_ObjectManipulator.md) per consentire determinati tipi di manipolazione, ad esempio</span><span class="sxs-lookup"><span data-stu-id="68473-262">A bounds control can be used in combination with [`ObjectManipulator.cs`](README_ObjectManipulator.md) to allow for certain types of manipulation (eg.</span></span> <span data-ttu-id="68473-263">lo stato di un oggetto viene spostato senza utilizzare handle.</span><span class="sxs-lookup"><span data-stu-id="68473-263">moving the object) without using handles.</span></span> <span data-ttu-id="68473-264">Il gestore di manipolazione supporta entrambe le interazioni con una e due gestite.</span><span class="sxs-lookup"><span data-stu-id="68473-264">The manipulation handler supports both one and two-handed interactions.</span></span> <span data-ttu-id="68473-265">Il [rilevamento manuale](Input/HandTracking.md) può essere usato per interagire con un oggetto alla chiusura.</span><span class="sxs-lookup"><span data-stu-id="68473-265">[Hand tracking](Input/HandTracking.md) can be used to interact with an object up close.</span></span>

<img src="Images/BoundsControl/MRTK_BoundsControl_ObjectManipulator.png" width="450" alt="Bounds control Object Manipulator">

<span data-ttu-id="68473-266">Affinché i bordi del controllo dei limiti si comportino allo stesso modo quando lo si trasferisce usando l' [`ObjectManipulator`](README_ObjectManipulator.md) interazione molto, si consiglia di connettere gli eventi per in fase di manipolazione *avviata* alla  /  *manipolazione* `BoundsControl.HighlightWires`  /  `BoundsControl.UnhighlightWires` rispettivamente, come illustrato nella schermata precedente.</span><span class="sxs-lookup"><span data-stu-id="68473-266">In order for the bounds control edges to behave the same way when moving it using [`ObjectManipulator`](README_ObjectManipulator.md)'s far interaction, it is advised to connect its events for *On Manipulation Started* / *On Manipulation Ended* to `BoundsControl.HighlightWires` / `BoundsControl.UnhighlightWires` respectively, as shown in the screenshot above.</span></span>

## <a name="how-to-add-and-configure-a-bounds-control-using-unity-inspector"></a><span data-ttu-id="68473-267">Come aggiungere e configurare un controllo dei limiti con Unity Inspector</span><span class="sxs-lookup"><span data-stu-id="68473-267">How to add and configure a bounds control using Unity Inspector</span></span>

1. <span data-ttu-id="68473-268">Aggiungi box Collider a un oggetto</span><span class="sxs-lookup"><span data-stu-id="68473-268">Add Box Collider to an object</span></span>
2. <span data-ttu-id="68473-269">Assegnare `BoundsControl` uno script a un oggetto</span><span class="sxs-lookup"><span data-stu-id="68473-269">Assign `BoundsControl` script to an object</span></span>
3. <span data-ttu-id="68473-270">Configurare le opzioni, ad esempio i metodi di attivazione (vedere la sezione [proprietà di controllo](#inspector-properties) più avanti)</span><span class="sxs-lookup"><span data-stu-id="68473-270">Configure options, such as 'Activation' methods (see [Inspector properties](#inspector-properties) section below)</span></span>
4. <span data-ttu-id="68473-271">Opzionale Assegnare prefabbricati e materiali per un controllo dei limiti di stile HoloLens 2 (vedere la sezione [stili di handle](#handle-styles) riportata di seguito)</span><span class="sxs-lookup"><span data-stu-id="68473-271">(Optional) Assign prefabs and materials for a HoloLens 2 style bounds control (see [Handle styles](#handle-styles) section below)</span></span>

> [!NOTE]
> <span data-ttu-id="68473-272">Utilizzare l' *oggetto di destinazione* e il campo di override dei *limiti* nel controllo per assegnare un oggetto e un Collider specifici nell'oggetto con più componenti figlio.</span><span class="sxs-lookup"><span data-stu-id="68473-272">Use *Target Object* and *Bounds Override* field in the inspector to assign specific object and collider in the object with multiple child components.</span></span>

![Assegnazione controllo limiti](Images/BoundsControl/MRTK_BoundsControl_Assign.png)

## <a name="how-to-add-and-configure-a-bounds-control-in-the-code"></a><span data-ttu-id="68473-274">Come aggiungere e configurare un controllo dei limiti nel codice</span><span class="sxs-lookup"><span data-stu-id="68473-274">How to add and configure a bounds control in the code</span></span>

1. <span data-ttu-id="68473-275">Creare un'istanza del cubo GameObject</span><span class="sxs-lookup"><span data-stu-id="68473-275">Instantiate cube GameObject</span></span>

    ```c#
    GameObject cube = GameObject.CreatePrimitive(PrimitiveType.Cube);
    ```

1. <span data-ttu-id="68473-276">Assegnare `BoundsControl` uno script a un oggetto con Collider, usando AddComponent<> ()</span><span class="sxs-lookup"><span data-stu-id="68473-276">Assign `BoundsControl` script to an object with collider, using AddComponent<>()</span></span>

    ```c#
    private BoundsControl boundsControl;
    boundsControl = cube.AddComponent<BoundsControl>();
    ```

1. <span data-ttu-id="68473-277">Configurare le opzioni direttamente nel controllo o tramite una delle configurazioni con script (vedere la sezione [Proprietà](#inspector-properties) e [configurazioni](#configuration-objects) di Inspector di seguito)</span><span class="sxs-lookup"><span data-stu-id="68473-277">Configure options either directly on the control or via one of the scriptable configurations (see [Inspector properties](#inspector-properties) and [Configurations](#configuration-objects) section below)</span></span>

    ```c#
    // Change activation method
    boundsControl.BoundsControlActivation = BoundsControlActivationType.ActivateByProximityAndPointer;
    // Make the scale handles large
    boundsControl.ScaleHandlesConfig.HandleSize = 0.1f;
    // Hide rotation handles for x axis
    boundsControl.RotationHandlesConfig.ShowRotationHandleForX = false;
    ```

1. <span data-ttu-id="68473-278">Opzionale Assegnare prefabbricati e materiali per un controllo dei limiti di stile HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="68473-278">(Optional) Assign prefabs and materials for a HoloLens 2 style bounds control.</span></span> <span data-ttu-id="68473-279">Questa operazione richiede comunque le assegnazioni tramite il controllo, poiché i materiali e i prefabbricati devono essere caricati dinamicamente.</span><span class="sxs-lookup"><span data-stu-id="68473-279">This still requires assignments through the inspector since the materials and prefabs should be dynamically loaded.</span></span>

> [!NOTE]
> <span data-ttu-id="68473-280">Uso della cartella ' Resources ' di Unity o dello [shader.]( https://docs.unity3d.com/ScriptReference/Shader.Find.html) non è consigliabile trovare per il caricamento dinamico degli shader perché le permutazioni dello shader potrebbero mancare in fase di esecuzione.</span><span class="sxs-lookup"><span data-stu-id="68473-280">Using Unity's 'Resources' folder or [Shader.Find]( https://docs.unity3d.com/ScriptReference/Shader.Find.html) for dynamically loading shaders is not recommended since shader permutations may be missing at runtime.</span></span>

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

### <a name="example-set-minimum-maximum-bounds-control-scale-using-minmaxscaleconstraint"></a><span data-ttu-id="68473-281">Esempio: impostare la scala del controllo dei limiti minimo e massimo con MinMaxScaleConstraint</span><span class="sxs-lookup"><span data-stu-id="68473-281">Example: Set minimum, maximum bounds control scale using MinMaxScaleConstraint</span></span>

<span data-ttu-id="68473-282">Per impostare la scala minima e massima, aggiungere un [`MinMaxScaleConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.MinMaxScaleConstraint) alla constrol.</span><span class="sxs-lookup"><span data-stu-id="68473-282">To set the minimum and maximum scale, attach a [`MinMaxScaleConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.MinMaxScaleConstraint) to your constrol.</span></span> <span data-ttu-id="68473-283">Poiché il controllo dei limiti collega automaticamente e attiva Gestione vincoli, il MinMaxScaleConstraint verrà automaticamente applicato alle modifiche della trasformazione dopo che è stato collegato e configurato.</span><span class="sxs-lookup"><span data-stu-id="68473-283">As bounds control automatically attaches and activates constraint manager the MinMaxScaleConstraint will be automatically applied to the transformation changes once it's attached and configured.</span></span>

<span data-ttu-id="68473-284">È anche possibile usare MinMaxScaleConstraint per impostare la scala minima e massima per [`ObjectManipulator`](xref:Microsoft.MixedReality.Toolkit.UI.ObjectManipulator) .</span><span class="sxs-lookup"><span data-stu-id="68473-284">You can also use MinMaxScaleConstraint to set minimum and maximum scale for [`ObjectManipulator`](xref:Microsoft.MixedReality.Toolkit.UI.ObjectManipulator).</span></span>

```c#
GameObject cube = GameObject.CreatePrimitive(PrimitiveType.Cube);
bcontrol = cube.AddComponent<BoundsControl>();
// Important: BoundsControl creates a constraint manager on start if one does not exist.
// There's no need to manually attach a constraint manager.
MinMaxScaleConstraint scaleConstraint = bcontrol.gameObject.AddComponent<MinMaxScaleConstraint>();
scaleConstraint.ScaleMinimum = 1f;
scaleConstraint.ScaleMaximum = 2f;
```

## <a name="example-add-bounds-control-around-a-game-object"></a><span data-ttu-id="68473-285">Esempio: aggiungere un controllo Bounds intorno a un oggetto Game</span><span class="sxs-lookup"><span data-stu-id="68473-285">Example: Add bounds control around a game object</span></span>

<span data-ttu-id="68473-286">Per aggiungere un controllo dei limiti intorno a un oggetto, è sufficiente aggiungervi un `BoundsControl` componente:</span><span class="sxs-lookup"><span data-stu-id="68473-286">To add a bounds control around an object, simply add a `BoundsControl` component to it:</span></span>

```c#
private void PutABoundsControlAroundIt(GameObject target)
{
   target.AddComponent<BoundsControl>();
}
```

## <a name="migrating-from-bounding-box"></a><span data-ttu-id="68473-287">Migrazione da un rettangolo di delimitazione</span><span class="sxs-lookup"><span data-stu-id="68473-287">Migrating from Bounding Box</span></span>

<span data-ttu-id="68473-288">I prefissi e le istanze esistenti che usano il rettangolo di [delimitazione](README_BoundingBox.md) possono essere aggiornati al nuovo controllo dei limiti tramite la [finestra di migrazione](Tools/MigrationWindow.md) che fa parte del pacchetto di strumenti MRTK.</span><span class="sxs-lookup"><span data-stu-id="68473-288">Existing prefabs and instances using [bounding box](README_BoundingBox.md) can be upgraded to the new bounds control via the [migration window](Tools/MigrationWindow.md) which is part of the MRTK tools package.</span></span>

<span data-ttu-id="68473-289">Per l'aggiornamento di singole istanze del rettangolo di delimitazione è disponibile anche un'opzione di migrazione all'interno del controllo proprietà del componente.</span><span class="sxs-lookup"><span data-stu-id="68473-289">For upgrading individual instances of bounding box there's also an a migration option inside the property inspector of the component.</span></span>

<img src="Images/BoundsControl/MRTK_BoundsControl_Migrate.png" width="450" alt="Migration to Bounds control">

## <a name="see-also"></a><span data-ttu-id="68473-290">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="68473-290">See also</span></span>

* [<span data-ttu-id="68473-291">Manipolatore di oggetti</span><span class="sxs-lookup"><span data-stu-id="68473-291">Object manipulator</span></span>](README_ObjectManipulator.md)
* [<span data-ttu-id="68473-292">Gestione vincoli</span><span class="sxs-lookup"><span data-stu-id="68473-292">Constraint manager</span></span>](README_ConstraintManager.md)
* [<span data-ttu-id="68473-293">Finestra di migrazione</span><span class="sxs-lookup"><span data-stu-id="68473-293">Migration window</span></span>](Tools/MigrationWindow.md)
* [<span data-ttu-id="68473-294">Sistema elastici (sperimentale)</span><span class="sxs-lookup"><span data-stu-id="68473-294">Elastics system (Experimental)</span></span>](Elastics/ElasticSystem.md)

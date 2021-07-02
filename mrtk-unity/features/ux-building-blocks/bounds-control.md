---
title: Controllo Limiti
description: Panoramica sul controllo Bounds in MRTK
author: thalbern
ms.author: bethalha
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, controllo limiti,
ms.openlocfilehash: f5f5e1f463f741eb23f75c9826034b8974baf947
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176459"
---
# <a name="bounds-control"></a><span data-ttu-id="bbdbf-104">Controllo Limiti</span><span class="sxs-lookup"><span data-stu-id="bbdbf-104">Bounds control</span></span>

![Controllo Limiti](../images/bounds-control/MRTK_BoundsControl_Main.png)

<span data-ttu-id="bbdbf-106">*BoundsControl è* il nuovo componente per il comportamento di manipolazione, disponibile in precedenza in *BoundingBox.*</span><span class="sxs-lookup"><span data-stu-id="bbdbf-106">*BoundsControl* is the new component for manipulation behaviour, previously found in *BoundingBox*.</span></span> <span data-ttu-id="bbdbf-107">Il controllo dei limiti apporta una serie di miglioramenti e semplificazioni nella configurazione e aggiunge nuove funzionalità.</span><span class="sxs-lookup"><span data-stu-id="bbdbf-107">Bounds control makes a number of improvements and simplifications in setup and adds new features.</span></span> <span data-ttu-id="bbdbf-108">Questo componente è una sostituzione del rettangolo di selezione, che verrà deprecato.</span><span class="sxs-lookup"><span data-stu-id="bbdbf-108">This component is a replacement for the bounding box, which will be deprecated.</span></span>

<span data-ttu-id="bbdbf-109">Lo [`BoundsControl.cs`](xref:Microsoft.MixedReality.Toolkit.UI.BoundsControl) script fornisce funzionalità di base per la trasformazione di oggetti nella realtà mista.</span><span class="sxs-lookup"><span data-stu-id="bbdbf-109">The [`BoundsControl.cs`](xref:Microsoft.MixedReality.Toolkit.UI.BoundsControl) script provides basic functionality for transforming objects in mixed reality.</span></span> <span data-ttu-id="bbdbf-110">Un controllo limiti mostrerà una casella intorno all'ologramma per indicare che è possibile interagire con esso.</span><span class="sxs-lookup"><span data-stu-id="bbdbf-110">A bounds control will show a box around the hologram to indicate that it can be interacted with.</span></span> <span data-ttu-id="bbdbf-111">I quadratini di ridimensionamento sugli angoli e sui bordi della casella consentono di ridimensionare, ruotare o traslare l'oggetto.</span><span class="sxs-lookup"><span data-stu-id="bbdbf-111">Handles on the corners and edges of the box allow scaling, rotating or translating the object.</span></span> <span data-ttu-id="bbdbf-112">Il controllo dei limiti reagisce anche all'input dell'utente.</span><span class="sxs-lookup"><span data-stu-id="bbdbf-112">The bounds control also reacts to user input.</span></span> <span data-ttu-id="bbdbf-113">In HoloLens 2, ad esempio, il controllo dei limiti risponde alla prossimità del dito, fornendo un feedback visivo che consente di percepire la distanza dall'oggetto.</span><span class="sxs-lookup"><span data-stu-id="bbdbf-113">On HoloLens 2, for example, the bounds control responds to finger proximity, providing visual feedback to help perceive the distance from the object.</span></span> <span data-ttu-id="bbdbf-114">Tutte le interazioni e gli oggetti visivi possono essere facilmente personalizzati.</span><span class="sxs-lookup"><span data-stu-id="bbdbf-114">All interactions and visuals can be easily customized.</span></span>

## <a name="example-scene"></a><span data-ttu-id="bbdbf-115">Scena di esempio</span><span class="sxs-lookup"><span data-stu-id="bbdbf-115">Example scene</span></span>

<span data-ttu-id="bbdbf-116">È possibile trovare esempi di configurazioni di controllo dei limiti nella `BoundsControlExamples` scena.</span><span class="sxs-lookup"><span data-stu-id="bbdbf-116">You can find examples of bounds control configurations in the `BoundsControlExamples` scene.</span></span>

<img src="../images/bounds-control/MRTK_BoundsControl_Examples.png" alt="Bounds control Example">

## <a name="inspector-properties"></a><span data-ttu-id="bbdbf-117">Proprietà del controllo</span><span class="sxs-lookup"><span data-stu-id="bbdbf-117">Inspector properties</span></span>

### <a name="target-object"></a><span data-ttu-id="bbdbf-118">Oggetti di destinazione</span><span class="sxs-lookup"><span data-stu-id="bbdbf-118">Target object</span></span>

<span data-ttu-id="bbdbf-119">Questa proprietà specifica quale oggetto verrà trasformato dalla manipolazione del controllo dei limiti.</span><span class="sxs-lookup"><span data-stu-id="bbdbf-119">This property specifies which object will get transformed by the bounds control manipulation.</span></span> <span data-ttu-id="bbdbf-120">Se non è impostato alcun oggetto, per impostazione predefinita viene utilizzato l'oggetto proprietario.</span><span class="sxs-lookup"><span data-stu-id="bbdbf-120">If no object is set, it defaults to the owner object.</span></span>

### <a name="activation-behavior"></a><span data-ttu-id="bbdbf-121">Comportamento di attivazione</span><span class="sxs-lookup"><span data-stu-id="bbdbf-121">Activation behavior</span></span>

<span data-ttu-id="bbdbf-122">Sono disponibili diverse opzioni per attivare l'interfaccia del controllo dei limiti.</span><span class="sxs-lookup"><span data-stu-id="bbdbf-122">There are several options to activate the bounds control interface.</span></span>

* <span data-ttu-id="bbdbf-123">*Attiva all'avvio:* il controllo Limiti diventa visibile dopo l'avvio della scena.</span><span class="sxs-lookup"><span data-stu-id="bbdbf-123">*Activate On Start*: Bounds control becomes visible once the scene is started.</span></span>
* <span data-ttu-id="bbdbf-124">*Attiva per prossimità:* il controllo Limiti diventa visibile quando una mano articolata è vicina all'oggetto.</span><span class="sxs-lookup"><span data-stu-id="bbdbf-124">*Activate By Proximity*: Bounds control becomes visible when an articulated hand is close to the object.</span></span>
* <span data-ttu-id="bbdbf-125">*Attiva in base al* puntatore: il controllo Limiti diventa visibile quando è destinato a un indicatore di misura del raggio della mano.</span><span class="sxs-lookup"><span data-stu-id="bbdbf-125">*Activate By Pointer*: Bounds control becomes visible when it is targeted by a hand-ray pointer.</span></span>
* <span data-ttu-id="bbdbf-126">*Attiva per prossimità e* puntatore: il controllo Limiti diventa visibile quando è indirizzato da un puntatore a raggi della mano o quando una mano articolata è vicina all'oggetto.</span><span class="sxs-lookup"><span data-stu-id="bbdbf-126">*Activate By Proximity and Pointer*: Bounds control becomes visible when it is targeted by a hand-ray pointer or an articulated hand is close to the object.</span></span>
* <span data-ttu-id="bbdbf-127">*Attiva manualmente:* il controllo Limiti non diventa visibile automaticamente.</span><span class="sxs-lookup"><span data-stu-id="bbdbf-127">*Activate Manually*: Bounds control does not become visible automatically.</span></span> <span data-ttu-id="bbdbf-128">È possibile attivarlo manualmente tramite uno script accedendo alla proprietà boundsControl.Active.</span><span class="sxs-lookup"><span data-stu-id="bbdbf-128">You can manually activate it through a script by accessing the boundsControl.Active property.</span></span>

### <a name="bounds-override"></a><span data-ttu-id="bbdbf-129">Override dei limiti</span><span class="sxs-lookup"><span data-stu-id="bbdbf-129">Bounds override</span></span>

<span data-ttu-id="bbdbf-130">Imposta un collisore di box dall'oggetto per il calcolo dei limiti.</span><span class="sxs-lookup"><span data-stu-id="bbdbf-130">Sets a box collider from the object for bounds computation.</span></span>

### <a name="box-padding"></a><span data-ttu-id="bbdbf-131">Riempimento della casella</span><span class="sxs-lookup"><span data-stu-id="bbdbf-131">Box padding</span></span>

<span data-ttu-id="bbdbf-132">Aggiunge una spaziatura interna ai limiti del collisore utilizzata per calcolare gli extent del controllo.</span><span class="sxs-lookup"><span data-stu-id="bbdbf-132">Adds a padding to the collider bounds used to calculate the extents of the control.</span></span> <span data-ttu-id="bbdbf-133">Ciò influirà non solo sull'interazione, ma anche sugli oggetti visivi.</span><span class="sxs-lookup"><span data-stu-id="bbdbf-133">This will influence not only interaction but also impact the visuals.</span></span>

### <a name="flatten-axis"></a><span data-ttu-id="bbdbf-134">Appiattire l'asse</span><span class="sxs-lookup"><span data-stu-id="bbdbf-134">Flatten axis</span></span>

<span data-ttu-id="bbdbf-135">Indica se il controllo è bidimensionale in uno degli assi, rendendolo bidimensionale e non consente la manipolazione lungo tale asse.</span><span class="sxs-lookup"><span data-stu-id="bbdbf-135">Indicates whether the control is flattened in one of the axes, making it 2 dimensional and disallowing manipulation along that axis.</span></span> <span data-ttu-id="bbdbf-136">Questa funzionalità può essere usata per gli oggetti thin, ad esempio gli slate.</span><span class="sxs-lookup"><span data-stu-id="bbdbf-136">This feature can be used for thin objects like slates.</span></span>
<span data-ttu-id="bbdbf-137">Se l'opzione Asse appiattimento è impostata su *Appiatti automaticamente,* lo script selezionerà automaticamente l'asse con l'estensione più piccola come asse appiattito.</span><span class="sxs-lookup"><span data-stu-id="bbdbf-137">If flatten axis is set to *Flatten Auto* the script will automatically pick the axis with the smallest extent as flatten axis.</span></span>

### <a name="smoothing"></a><span data-ttu-id="bbdbf-138">Definizione di movimenti uniformi</span><span class="sxs-lookup"><span data-stu-id="bbdbf-138">Smoothing</span></span>

<span data-ttu-id="bbdbf-139">La sezione smoothing consente di configurare il comportamento di smussamento per la scala e la rotazione del controllo.</span><span class="sxs-lookup"><span data-stu-id="bbdbf-139">The smoothing section allows to configure smoothing behavior for scale and rotate of the control.</span></span>

### <a name="visuals"></a><span data-ttu-id="bbdbf-140">Oggetti visivi</span><span class="sxs-lookup"><span data-stu-id="bbdbf-140">Visuals</span></span>

<span data-ttu-id="bbdbf-141">L'aspetto del controllo dei limiti può essere configurato modificando una delle configurazioni degli oggetti visivi corrispondenti.</span><span class="sxs-lookup"><span data-stu-id="bbdbf-141">The appearance of bounds control can be configured by modifying one of the corresponding visuals configurations.</span></span>
<span data-ttu-id="bbdbf-142">Le configurazioni degli oggetti visivi sono oggetti collegati o inline che possono essere creati tramite script e sono descritte in modo più dettagliato nella sezione [relativa all'oggetto di configurazione](#configuration-objects).</span><span class="sxs-lookup"><span data-stu-id="bbdbf-142">Visual configurations are either linked or inlined scriptable objects and are described in more detail in the [configuration object section](#configuration-objects).</span></span>

## <a name="configuration-objects"></a><span data-ttu-id="bbdbf-143">Oggetti di configurazione</span><span class="sxs-lookup"><span data-stu-id="bbdbf-143">Configuration Objects</span></span>

<span data-ttu-id="bbdbf-144">Il controllo viene fornito con un set di oggetti di configurazione che possono essere archiviati come oggetti gestibili da script e condivisi tra istanze o prefab diversi.</span><span class="sxs-lookup"><span data-stu-id="bbdbf-144">The control comes with a set of configuration objects that can be stored as scriptable objects and shared between different instances or prefabs.</span></span> <span data-ttu-id="bbdbf-145">Le configurazioni possono essere condivise e collegate come singoli file di asset gestibili tramite script o asset annidati gestibili tramite script all'interno di prefab.</span><span class="sxs-lookup"><span data-stu-id="bbdbf-145">Configurations can be shared and linked either as individual scriptable asset files or nested scriptable assets inside of prefabs.</span></span> <span data-ttu-id="bbdbf-146">È anche possibile definire altre configurazioni direttamente nell'istanza senza collegarsi a un asset esterno o annidabile tramite script.</span><span class="sxs-lookup"><span data-stu-id="bbdbf-146">Further configurations can also be defined directly on the instance without linking to an external or nested scriptable asset.</span></span>

<span data-ttu-id="bbdbf-147">Il controllo dei limiti indicherà se una configurazione è condivisa o inline come parte dell'istanza corrente visualizzando un messaggio nel controllo proprietà.</span><span class="sxs-lookup"><span data-stu-id="bbdbf-147">The bounds control inspector will indicate whether a configuration is shared or inlined as part of the current instance by showing a message in the property inspector.</span></span> <span data-ttu-id="bbdbf-148">Inoltre, le istanze condivise non saranno modificabili direttamente nella finestra delle proprietà del controllo dei limiti, ma l'asset a cui si collega deve essere modificato direttamente per evitare modifiche accidentali nelle configurazioni condivise.</span><span class="sxs-lookup"><span data-stu-id="bbdbf-148">In addition shared instances won't be editable directly in the bounds control property window itself, but instead the asset it's linking to has to be directly modfied to avoid any accidental changes on shared configurations.</span></span>

<span data-ttu-id="bbdbf-149">Attualmente il controllo dei limiti offre opzioni per gli oggetti di configurazione per le funzionalità seguenti:</span><span class="sxs-lookup"><span data-stu-id="bbdbf-149">Currently bounds control offers configuration objects options for the following features:</span></span>

* <span data-ttu-id="bbdbf-150">Selettori</span><span class="sxs-lookup"><span data-stu-id="bbdbf-150">Handles</span></span>
  * [<span data-ttu-id="bbdbf-151">Handle di scalabilità</span><span class="sxs-lookup"><span data-stu-id="bbdbf-151">Scale handles</span></span>](#scale-handles-configuration)
  * [<span data-ttu-id="bbdbf-152">Handle di rotazione</span><span class="sxs-lookup"><span data-stu-id="bbdbf-152">Rotation handles</span></span>](#rotation-handles-configuration)
  * [<span data-ttu-id="bbdbf-153">Handle di conversione</span><span class="sxs-lookup"><span data-stu-id="bbdbf-153">Translation handles</span></span>](#translation-handles-configuration)
* [<span data-ttu-id="bbdbf-154">Collegamenti/Wireframe</span><span class="sxs-lookup"><span data-stu-id="bbdbf-154">Links / Wireframe</span></span>](#links-configuration-wireframe)
* [<span data-ttu-id="bbdbf-155">Visualizzazione della casella</span><span class="sxs-lookup"><span data-stu-id="bbdbf-155">Box display</span></span>](#box-configuration)
* [<span data-ttu-id="bbdbf-156">Effetto di prossimità</span><span class="sxs-lookup"><span data-stu-id="bbdbf-156">Proximity effect</span></span>](#proximity-effect-configuration)

### <a name="box-configuration"></a><span data-ttu-id="bbdbf-157">Configurazione di Box</span><span class="sxs-lookup"><span data-stu-id="bbdbf-157">Box configuration</span></span>

<span data-ttu-id="bbdbf-158">La configurazione della scatola è responsabile del rendering di una casella a tinta unita con limiti definiti tramite la dimensione del collisore e la spaziatura interna della scatola.</span><span class="sxs-lookup"><span data-stu-id="bbdbf-158">The box configuration is responsible for rendering a solid box with bounds defined via collider size and box padding.</span></span> <span data-ttu-id="bbdbf-159">È possibile configurare le proprietà seguenti:</span><span class="sxs-lookup"><span data-stu-id="bbdbf-159">The following properties can be set up:</span></span>

* <span data-ttu-id="bbdbf-160">**Materiale della scatola:** definisce il materiale applicato alla casella sottoposta a rendering quando non viene applicata alcuna interazione.</span><span class="sxs-lookup"><span data-stu-id="bbdbf-160">**Box material**: defines the material applied to the rendered box when no interaction takes place.</span></span> <span data-ttu-id="bbdbf-161">Il rendering di una casella verrà eseguito solo se questo materiale è impostato.</span><span class="sxs-lookup"><span data-stu-id="bbdbf-161">A box will only be rendered if this material is set.</span></span>
* <span data-ttu-id="bbdbf-162">**Materiale afferrato da box:** materiale per la scatola quando l'utente interagisce con il controllo afferrando tramite interazione da vicino o da lontano.</span><span class="sxs-lookup"><span data-stu-id="bbdbf-162">**Box grabbed material**: material for the box when the user interacts with the control by grabbing via near or far interaction.</span></span>
* <span data-ttu-id="bbdbf-163">**Scala di visualizzazione dell'asse** appiattito: scala applicata alla visualizzazione della casella se uno degli assi è [appiattito.](#flatten-axis)</span><span class="sxs-lookup"><span data-stu-id="bbdbf-163">**Flatten axis display scale**: a scale that is applied to the box display if one of the axes is [flattened](#flatten-axis).</span></span>

### <a name="scale-handles-configuration"></a><span data-ttu-id="bbdbf-164">Configurazione degli handle di scalabilità</span><span class="sxs-lookup"><span data-stu-id="bbdbf-164">Scale handles configuration</span></span>

<span data-ttu-id="bbdbf-165">Questo pannello delle proprietà consente di modificare il comportamento e la visualizzazione degli handle di scala del controllo limiti.</span><span class="sxs-lookup"><span data-stu-id="bbdbf-165">This property drawer allows to modify behavior and visualization of scale handles of bounds control.</span></span>

* <span data-ttu-id="bbdbf-166">**Handle material**: materiale applicato agli handle.</span><span class="sxs-lookup"><span data-stu-id="bbdbf-166">**Handle material**: material applied to the handles.</span></span>
* <span data-ttu-id="bbdbf-167">**Gestire il materiale afferrato:** materiale applicato al quadratino afferrato.</span><span class="sxs-lookup"><span data-stu-id="bbdbf-167">**Handle grabbed material**: material applied to the grabbed handle.</span></span>
* <span data-ttu-id="bbdbf-168">**Gestire il prefab:** prefab facoltativo per l'handle di scalabilità.</span><span class="sxs-lookup"><span data-stu-id="bbdbf-168">**Handle prefab**: optional prefab for the scale handle.</span></span> <span data-ttu-id="bbdbf-169">Se non è impostato, MRTK userà un cubo come predefinito.</span><span class="sxs-lookup"><span data-stu-id="bbdbf-169">If non is set MRTK will use a cube as default.</span></span>
* <span data-ttu-id="bbdbf-170">**Dimensioni handle:** dimensioni dell'handle di scala.</span><span class="sxs-lookup"><span data-stu-id="bbdbf-170">**Handle size**: size of the scale handle.</span></span>
* <span data-ttu-id="bbdbf-171">**Riempimento collisore:** spaziatura interna da aggiungere al collisore del punto di manipolazione.</span><span class="sxs-lookup"><span data-stu-id="bbdbf-171">**Collider padding**: padding to add to the handle collider.</span></span>
* <span data-ttu-id="bbdbf-172">**Disegna tether durante la manipolazione:** quando attiva disegna una linea tether dal punto di inizio dell'interazione alla posizione corrente della mano o dell'indicatore di misura.</span><span class="sxs-lookup"><span data-stu-id="bbdbf-172">**Draw tether when manipulating**: when active will draw a tether line from point of start of interaction to current hand or pointer position.</span></span>
* <span data-ttu-id="bbdbf-173">**Handle ignorano collisore:** se un collisore viene collegato qui, gli handle ignoreranno qualsiasi collisione con questo collisore.</span><span class="sxs-lookup"><span data-stu-id="bbdbf-173">**Handles ignore collider**: if a collider gets linked here, handles will ignore any collision with this collider.</span></span>
* <span data-ttu-id="bbdbf-174">**Gestire il prefab dello slate:** prefab da usare per l'handle quando il controllo è appiattito.</span><span class="sxs-lookup"><span data-stu-id="bbdbf-174">**Handle slate prefab**: prefab to use for the handle when the control is flattened.</span></span>
* <span data-ttu-id="bbdbf-175">**Mostra handle di scala:** controlla la visibilità dell'handle.</span><span class="sxs-lookup"><span data-stu-id="bbdbf-175">**Show scale handles**: controls visibility of the handle.</span></span>
* <span data-ttu-id="bbdbf-176">**Comportamento della scalabilità:** può essere impostato su un ridimensionamento uniforme o non uniforme.</span><span class="sxs-lookup"><span data-stu-id="bbdbf-176">**Scale behavior**: can be set to uniform or non-uniform scaling.</span></span>

### <a name="rotation-handles-configuration"></a><span data-ttu-id="bbdbf-177">Configurazione degli handle di rotazione</span><span class="sxs-lookup"><span data-stu-id="bbdbf-177">Rotation handles configuration</span></span>

<span data-ttu-id="bbdbf-178">Questa configurazione definisce il comportamento dell'handle di rotazione.</span><span class="sxs-lookup"><span data-stu-id="bbdbf-178">This configuration defines the rotation handle behavior.</span></span>

* <span data-ttu-id="bbdbf-179">**Handle material**: materiale applicato agli handle.</span><span class="sxs-lookup"><span data-stu-id="bbdbf-179">**Handle material**: material applied to the handles.</span></span>
* <span data-ttu-id="bbdbf-180">**Gestire il materiale afferrato:** materiale applicato al quadratino afferrato.</span><span class="sxs-lookup"><span data-stu-id="bbdbf-180">**Handle grabbed material**: material applied to the grabbed handle.</span></span>
* <span data-ttu-id="bbdbf-181">**Gestire il prefab:** prefab facoltativo per l'handle.</span><span class="sxs-lookup"><span data-stu-id="bbdbf-181">**Handle prefab**: optional prefab for the handle.</span></span> <span data-ttu-id="bbdbf-182">Se non è impostato, MRTK userà una sfera come valore predefinito.</span><span class="sxs-lookup"><span data-stu-id="bbdbf-182">If non is set MRTK will use a sphere as default.</span></span>
* <span data-ttu-id="bbdbf-183">**Dimensione dell'handle:** dimensioni dell'handle.</span><span class="sxs-lookup"><span data-stu-id="bbdbf-183">**Handle size**: size of the handle.</span></span>
* <span data-ttu-id="bbdbf-184">**Riempimento collisore:** spaziatura interna da aggiungere al collisore del punto di manipolazione.</span><span class="sxs-lookup"><span data-stu-id="bbdbf-184">**Collider padding**: padding to add to the handle collider.</span></span>
* <span data-ttu-id="bbdbf-185">**Disegna tether durante la manipolazione:** quando attiva disegna una linea tether dal punto di inizio dell'interazione alla posizione corrente della mano o dell'indicatore di misura.</span><span class="sxs-lookup"><span data-stu-id="bbdbf-185">**Draw tether when manipulating**: when active will draw a tether line from point of start of interaction to current hand or pointer position.</span></span>
* <span data-ttu-id="bbdbf-186">**Handle ignorano collisore:** se un collisore viene collegato qui, gli handle ignoreranno qualsiasi collisione con questo collisore.</span><span class="sxs-lookup"><span data-stu-id="bbdbf-186">**Handles ignore collider**: if a collider gets linked here, handles will ignore any collision with this collider.</span></span>
* <span data-ttu-id="bbdbf-187">**Gestire il tipo di collisore prefab:** tipo di collisore da usare con l'handle creato.</span><span class="sxs-lookup"><span data-stu-id="bbdbf-187">**Handle prefab collider type**: collider type to be used with the created handle.</span></span>
* <span data-ttu-id="bbdbf-188">**Mostra handle per X:** controlla la visibilità dell'handle per l'asse X.</span><span class="sxs-lookup"><span data-stu-id="bbdbf-188">**Show handle for X**: controls visibility of the handle for X axis.</span></span>
* <span data-ttu-id="bbdbf-189">**Mostra handle per Y:** controlla la visibilità dell'handle per l'asse Y.</span><span class="sxs-lookup"><span data-stu-id="bbdbf-189">**Show handle for Y**: controls visibility of the handle for Y axis.</span></span>
* <span data-ttu-id="bbdbf-190">**Mostra handle per Z:** controlla la visibilità dell'handle per l'asse Z.</span><span class="sxs-lookup"><span data-stu-id="bbdbf-190">**Show handle for Z**: controls visibility of the handle for Z axis.</span></span>

### <a name="translation-handles-configuration"></a><span data-ttu-id="bbdbf-191">Configurazione degli handle di conversione</span><span class="sxs-lookup"><span data-stu-id="bbdbf-191">Translation handles configuration</span></span>

<span data-ttu-id="bbdbf-192">Consente l'abilitazione e la configurazione degli handle di conversione per il controllo dei limiti.</span><span class="sxs-lookup"><span data-stu-id="bbdbf-192">Allows enabling and configuring translation handles for bounds control.</span></span> <span data-ttu-id="bbdbf-193">Si noti che gli handle di conversione sono disabilitati per impostazione predefinita.</span><span class="sxs-lookup"><span data-stu-id="bbdbf-193">Note that translation handles are disabled per default.</span></span>

* <span data-ttu-id="bbdbf-194">**Handle material**: materiale applicato agli handle.</span><span class="sxs-lookup"><span data-stu-id="bbdbf-194">**Handle material**: material applied to the handles.</span></span>
* <span data-ttu-id="bbdbf-195">**Gestire il materiale afferrato:** materiale applicato al quadratino afferrato.</span><span class="sxs-lookup"><span data-stu-id="bbdbf-195">**Handle grabbed material**: material applied to the grabbed handle.</span></span>
* <span data-ttu-id="bbdbf-196">**Gestire il prefab:** prefab facoltativo per l'handle.</span><span class="sxs-lookup"><span data-stu-id="bbdbf-196">**Handle prefab**: optional prefab for the handle.</span></span> <span data-ttu-id="bbdbf-197">Se non è impostato, MRTK userà una sfera come valore predefinito.</span><span class="sxs-lookup"><span data-stu-id="bbdbf-197">If non is set MRTK will use a sphere as default.</span></span>
* <span data-ttu-id="bbdbf-198">**Dimensione dell'handle:** dimensioni dell'handle.</span><span class="sxs-lookup"><span data-stu-id="bbdbf-198">**Handle size**: size of the handle.</span></span>
* <span data-ttu-id="bbdbf-199">**Riempimento collisore:** spaziatura interna da aggiungere al collisore del punto di manipolazione.</span><span class="sxs-lookup"><span data-stu-id="bbdbf-199">**Collider padding**: padding to add to the handle collider.</span></span>
* <span data-ttu-id="bbdbf-200">**Disegna tether durante la manipolazione:** quando attiva disegna una linea tether dal punto di inizio dell'interazione alla posizione corrente della mano o dell'indicatore di misura.</span><span class="sxs-lookup"><span data-stu-id="bbdbf-200">**Draw tether when manipulating**: when active will draw a tether line from point of start of interaction to current hand or pointer position.</span></span>
* <span data-ttu-id="bbdbf-201">**Handle ignora collisore:** se un collisore viene collegato qui, gli handle ignoreranno qualsiasi collisione con questo collisore.</span><span class="sxs-lookup"><span data-stu-id="bbdbf-201">**Handles ignore collider**: if a collider gets linked here, handles will ignore any collision with this collider.</span></span>
* <span data-ttu-id="bbdbf-202">**Gestire il tipo di collisore prefab:** tipo di collisore da usare con l'handle creato.</span><span class="sxs-lookup"><span data-stu-id="bbdbf-202">**Handle prefab collider type**: collider type to be used with the created handle.</span></span>
* <span data-ttu-id="bbdbf-203">**Mostra handle per X**: controlla la visibilità dell'handle per l'asse X.</span><span class="sxs-lookup"><span data-stu-id="bbdbf-203">**Show handle for X**: controls visibility of the handle for X axis.</span></span>
* <span data-ttu-id="bbdbf-204">**Mostra handle per Y**: controlla la visibilità dell'handle per l'asse Y.</span><span class="sxs-lookup"><span data-stu-id="bbdbf-204">**Show handle for Y**: controls visibility of the handle for Y axis.</span></span>
* <span data-ttu-id="bbdbf-205">**Mostra handle per Z**: controlla la visibilità dell'handle per l'asse Z.</span><span class="sxs-lookup"><span data-stu-id="bbdbf-205">**Show handle for Z**: controls visibility of the handle for Z axis.</span></span>

### <a name="links-configuration-wireframe"></a><span data-ttu-id="bbdbf-206">Configurazione dei collegamenti (wireframe)</span><span class="sxs-lookup"><span data-stu-id="bbdbf-206">Links configuration (wireframe)</span></span>

<span data-ttu-id="bbdbf-207">La configurazione dei collegamenti abilita la funzionalità wireframe del controllo dei limiti.</span><span class="sxs-lookup"><span data-stu-id="bbdbf-207">The links configuration enables the wireframe feature of bounds control.</span></span> <span data-ttu-id="bbdbf-208">È possibile configurare le proprietà seguenti:</span><span class="sxs-lookup"><span data-stu-id="bbdbf-208">The following properties can be configured:</span></span>

* <span data-ttu-id="bbdbf-209">**Materiale wireframe:** materiale applicato alla mesh wireframe.</span><span class="sxs-lookup"><span data-stu-id="bbdbf-209">**Wireframe material**: the material applied to the wireframe mesh.</span></span>
* <span data-ttu-id="bbdbf-210">**Raggio del bordo wireframe:** spessore del wireframe.</span><span class="sxs-lookup"><span data-stu-id="bbdbf-210">**Wireframe edge radius**: the thickness of the wireframe.</span></span>
* <span data-ttu-id="bbdbf-211">**Forma wireframe:** la forma del wireframe può essere cubica o cilindrica.</span><span class="sxs-lookup"><span data-stu-id="bbdbf-211">**Wireframe shape**: shape of the wireframe can by either cubic or cylindrical.</span></span>
* <span data-ttu-id="bbdbf-212">**Mostra wireframe:** controlla la visibilità del wireframe.</span><span class="sxs-lookup"><span data-stu-id="bbdbf-212">**Show wireframe**: controls visibility of the wireframe.</span></span>

### <a name="proximity-effect-configuration"></a><span data-ttu-id="bbdbf-213">Configurazione dell'effetto di prossimità</span><span class="sxs-lookup"><span data-stu-id="bbdbf-213">Proximity effect configuration</span></span>

<span data-ttu-id="bbdbf-214">Mostrare e nascondere i quadratini di ridimensionamento con l'animazione in base alla distanza dalle mani.</span><span class="sxs-lookup"><span data-stu-id="bbdbf-214">Show and hide the handles with animation based on the distance to the hands.</span></span> <span data-ttu-id="bbdbf-215">Ha un'animazione in scala in due passaggi.</span><span class="sxs-lookup"><span data-stu-id="bbdbf-215">It has two-step scaling animation.</span></span> <span data-ttu-id="bbdbf-216">Le impostazioni predefinite sono impostate su HoloLens 2 comportamento dello stile.</span><span class="sxs-lookup"><span data-stu-id="bbdbf-216">Defaults are set to HoloLens 2 style behavior.</span></span>

<img src="../images/bounds-control/MRTK_BoundsControl_Proximity.png" alt="Bounds control Proximity">

* <span data-ttu-id="bbdbf-217">**Effetto di prossimità attivo:** abilitare l'attivazione dell'handle basato sulla prossimità</span><span class="sxs-lookup"><span data-stu-id="bbdbf-217">**Proximity Effect Active**: Enable proximity-based handle activation</span></span>
* <span data-ttu-id="bbdbf-218">**Prossimità media dell'oggetto:** distanza per il ridimensionamento del primo passaggio</span><span class="sxs-lookup"><span data-stu-id="bbdbf-218">**Object Medium Proximity**: Distance for the 1st step scaling</span></span>
* <span data-ttu-id="bbdbf-219">**Prossimità di chiusura dell'oggetto:** distanza per il ridimensionamento del secondo passaggio</span><span class="sxs-lookup"><span data-stu-id="bbdbf-219">**Object Close Proximity**: Distance for the 2nd step scaling</span></span>
* <span data-ttu-id="bbdbf-220">**Scalabilità lontano:** valore di scala predefinito dell'asset handle quando le mani non sono al di fuori dell'intervallo dell'interazione di controllo dei limiti (distanza definita in precedenza da 'Handle Medium Proximity'.</span><span class="sxs-lookup"><span data-stu-id="bbdbf-220">**Far Scale**: Default scale value of the handle asset when the hands are out of range of the bounds control interaction (distance defined above by 'Handle Medium Proximity'.</span></span> <span data-ttu-id="bbdbf-221">Usare 0 per nascondere l'handle per impostazione predefinita)</span><span class="sxs-lookup"><span data-stu-id="bbdbf-221">Use 0 to hide handle by default)</span></span>
* <span data-ttu-id="bbdbf-222">**Scala media:** ridimensionare il valore dell'asset handle quando le mani sono entro l'intervallo dell'interazione di controllo dei limiti (distanza definita in precedenza da 'Handle Close Proximity'.</span><span class="sxs-lookup"><span data-stu-id="bbdbf-222">**Medium Scale**: Scale value of the handle asset when the hands are within range of the bounds control interaction (distance defined above by 'Handle Close Proximity'.</span></span> <span data-ttu-id="bbdbf-223">Usare 1 per visualizzare le dimensioni normali)</span><span class="sxs-lookup"><span data-stu-id="bbdbf-223">Use 1 to show normal size)</span></span>
* <span data-ttu-id="bbdbf-224">**Scala di chiusura:** ridimensionare il valore dell'asset handle quando le mani si trovano entro l'intervallo dell'interazione di afferramento (distanza definita in precedenza da 'Handle Close Proximity'.</span><span class="sxs-lookup"><span data-stu-id="bbdbf-224">**Close Scale**: Scale value of the handle asset when the hands are within range of the grab interaction (distance defined above by 'Handle Close Proximity'.</span></span> <span data-ttu-id="bbdbf-225">Usare 1.x per visualizzare dimensioni maggiori)</span><span class="sxs-lookup"><span data-stu-id="bbdbf-225">Use 1.x to show bigger size)</span></span>
* <span data-ttu-id="bbdbf-226">**Frequenza di crescita elevata:** valutare la scalabilità di un oggetto con scalabilità di prossimità quando la mano passa da una prossimità media a un'altra.</span><span class="sxs-lookup"><span data-stu-id="bbdbf-226">**Far Grow Rate**: Rate a proximity scaled object scales when the hand moves from medium to far proximity.</span></span>
* <span data-ttu-id="bbdbf-227">**Velocità di crescita media:** valutare la scalabilità di un oggetto con scalabilità di prossimità quando la mano passa da media a prossimità vicina.</span><span class="sxs-lookup"><span data-stu-id="bbdbf-227">**Medium Grow Rate**: Rate a proximity scaled object scales when the hand moves from medium to close proximity.</span></span>
* <span data-ttu-id="bbdbf-228">**Close Grow Rate**(Frequenza di crescita di chiusura): valutare la scalabilità di un oggetto con scala di prossimità quando la mano passa dalla prossimità al centro dell'oggetto.</span><span class="sxs-lookup"><span data-stu-id="bbdbf-228">**Close Grow Rate**: Rate a proximity scaled object scales when the hand moves from close proximity to object center.</span></span>

## <a name="constraint-system"></a><span data-ttu-id="bbdbf-229">Sistema di vincoli</span><span class="sxs-lookup"><span data-stu-id="bbdbf-229">Constraint System</span></span>

<span data-ttu-id="bbdbf-230">Il controllo Limiti supporta l'uso di Gestione [vincoli per](constraint-manager.md) limitare o modificare il comportamento di traslazione, rotazione o ridimensionamento durante l'uso di handle di controllo dei limiti.</span><span class="sxs-lookup"><span data-stu-id="bbdbf-230">Bounds control supports using the [constraint manager](constraint-manager.md) to limit or modify translation, rotation or scaling behavior while using bounds control handles.</span></span>

<span data-ttu-id="bbdbf-231">Il controllo delle proprietà mostra tutti i gestori vincoli disponibili associati allo stesso oggetto di gioco in un elenco a discesa con un'opzione per scorrere ed evidenziare il gestore vincoli selezionato.</span><span class="sxs-lookup"><span data-stu-id="bbdbf-231">The property inspector will show all available constraint managers attached to the same game object in a dropdown with an option to scroll and highlight the selected constraint manager.</span></span>

<img src="../images/bounds-control/MRTK_BoundsControl_Constraints.png" width="450" alt="Bounds control Constraints">

## <a name="events"></a><span data-ttu-id="bbdbf-232">Eventi</span><span class="sxs-lookup"><span data-stu-id="bbdbf-232">Events</span></span>

<span data-ttu-id="bbdbf-233">Il controllo Bounds fornisce gli eventi seguenti.</span><span class="sxs-lookup"><span data-stu-id="bbdbf-233">Bounds control provides the following events.</span></span> <span data-ttu-id="bbdbf-234">Questo esempio usa questi eventi per riprodurre commenti e suggerimenti audio.</span><span class="sxs-lookup"><span data-stu-id="bbdbf-234">This example uses these events to play audio feedback.</span></span>

* <span data-ttu-id="bbdbf-235">**Ruota avviata:** attivato all'avvio della rotazione.</span><span class="sxs-lookup"><span data-stu-id="bbdbf-235">**Rotate Started**: Fired when rotation starts.</span></span>
* <span data-ttu-id="bbdbf-236">**Ruota arrestata:** attivato all'arresto della rotazione.</span><span class="sxs-lookup"><span data-stu-id="bbdbf-236">**Rotate Stopped**: Fired when rotation stops.</span></span>
* <span data-ttu-id="bbdbf-237">**Ridimensionamento avviato:** viene generato all'avvio del ridimensionamento.</span><span class="sxs-lookup"><span data-stu-id="bbdbf-237">**Scale Started**: Fires when scaling starts.</span></span>
* <span data-ttu-id="bbdbf-238">**Ridimensionamento arrestato:** viene generato quando il ridimensionamento si arresta.</span><span class="sxs-lookup"><span data-stu-id="bbdbf-238">**Scale Stopped**: Fires when scaling stops.</span></span>
* <span data-ttu-id="bbdbf-239">**Translate Started**: viene generato all'avvio della traduzione.</span><span class="sxs-lookup"><span data-stu-id="bbdbf-239">**Translate Started**: Fires when translation starts.</span></span>
* <span data-ttu-id="bbdbf-240">**Traduci arrestato:** viene generato quando la traduzione viene interrotta.</span><span class="sxs-lookup"><span data-stu-id="bbdbf-240">**Translate Stopped**: Fires when translation stops.</span></span>

<img src="../images/bounds-control/MRTK_BoundsControl_Events.png" width="450" alt="Bounds control Events">

## <a name="elastics-experimental"></a><span data-ttu-id="bbdbf-241">Elastici (sperimentale)</span><span class="sxs-lookup"><span data-stu-id="bbdbf-241">Elastics (Experimental)</span></span>

<span data-ttu-id="bbdbf-242">Gli elastici possono essere usati quando si modificano oggetti tramite il controllo dei limiti.</span><span class="sxs-lookup"><span data-stu-id="bbdbf-242">Elastics can be used when manipulating objects via bounds control.</span></span> <span data-ttu-id="bbdbf-243">Si noti che il [sistema elastico](../experimental/elastic-system.md) è ancora in stato sperimentale.</span><span class="sxs-lookup"><span data-stu-id="bbdbf-243">Note that the [elastics system](../experimental/elastic-system.md) is still in experimental state.</span></span> <span data-ttu-id="bbdbf-244">Per abilitare gli elastici, collegare un componente di gestione elastici esistente oppure creare e collegare un nuovo gestore elastici tramite il `Add Elastics Manager` pulsante .</span><span class="sxs-lookup"><span data-stu-id="bbdbf-244">To enable elastics either link an existing elastics manager component or create and link a new elastics manager via the `Add Elastics Manager` button.</span></span>

<img src="../images/bounds-control/MRTK_BoundsControl_Elastics.png" width="450" alt="Bounds control Elastics">

## <a name="handle-styles"></a><span data-ttu-id="bbdbf-245">Gestire gli stili</span><span class="sxs-lookup"><span data-stu-id="bbdbf-245">Handle styles</span></span>

<span data-ttu-id="bbdbf-246">Per impostazione predefinita, quando si assegna solo lo script, verrà visualizzato l'handle del HoloLens [`BoundsControl.cs`](xref:Microsoft.MixedReality.Toolkit.UI.BoundsControl) di prima generazione.</span><span class="sxs-lookup"><span data-stu-id="bbdbf-246">By default, when you just assign the [`BoundsControl.cs`](xref:Microsoft.MixedReality.Toolkit.UI.BoundsControl) script, it will show the handle of the HoloLens 1st gen style.</span></span> <span data-ttu-id="bbdbf-247">Per usare HoloLens 2 di stile, è necessario assegnare prefab e materiali di gestione adeguati.</span><span class="sxs-lookup"><span data-stu-id="bbdbf-247">To use HoloLens 2 style handles, you need to assign proper handle prefabs and materials.</span></span>

![Stili degli handle del controllo Bounds 2](../images/bounds-control/MRTK_BoundsControl_HandleStyles1.png)

<span data-ttu-id="bbdbf-249">Di seguito sono riportati i prefab, i materiali e i valori di ridimensionamento HoloLens 2 di controllo dei limiti di stile.</span><span class="sxs-lookup"><span data-stu-id="bbdbf-249">Below are the prefabs, materials, and the scaling values for the HoloLens 2 style bounds control handles.</span></span> <span data-ttu-id="bbdbf-250">È possibile trovare questo esempio nella `BoundsControlExamples` scena .</span><span class="sxs-lookup"><span data-stu-id="bbdbf-250">You can find this example in the `BoundsControlExamples` scene.</span></span>

<img src="../images/bounds-control/MRTK_BoundsControl_HandleStyles2.png" width="450" alt="Bounds control HandleStyles">

### <a name="handles-setup-for-hololens-2-style"></a><span data-ttu-id="bbdbf-251">Handle (configurazione per HoloLens 2 stile)</span><span class="sxs-lookup"><span data-stu-id="bbdbf-251">Handles (Setup for HoloLens 2 style)</span></span>

* <span data-ttu-id="bbdbf-252">**Handle Material**: BoundingBoxHandleWhite.mat</span><span class="sxs-lookup"><span data-stu-id="bbdbf-252">**Handle Material**: BoundingBoxHandleWhite.mat</span></span>
* <span data-ttu-id="bbdbf-253">**Handle Grabbed Material**: BoundingBoxHandleBlueGrabbed.mat</span><span class="sxs-lookup"><span data-stu-id="bbdbf-253">**Handle Grabbed Material**: BoundingBoxHandleBlueGrabbed.mat</span></span>
* <span data-ttu-id="bbdbf-254">**Prefab dell'handle** di scala: MRTK_BoundingBox_ScaleHandle.prefab</span><span class="sxs-lookup"><span data-stu-id="bbdbf-254">**Scale Handle Prefab**: MRTK_BoundingBox_ScaleHandle.prefab</span></span>
* <span data-ttu-id="bbdbf-255">**Scale Handle Slate Prefab**: MRTK_BoundingBox_ScaleHandle_Slate.prefab</span><span class="sxs-lookup"><span data-stu-id="bbdbf-255">**Scale Handle Slate Prefab**: MRTK_BoundingBox_ScaleHandle_Slate.prefab</span></span>
* <span data-ttu-id="bbdbf-256">**Dimensioni dell'handle di** scala: 0,016 (1,6 cm)</span><span class="sxs-lookup"><span data-stu-id="bbdbf-256">**Scale Handle Size**: 0.016 (1.6cm)</span></span>
* <span data-ttu-id="bbdbf-257">**Scale Handle Collider Padding**: 0,016 (rende il collisore afferrabile leggermente più grande dell'oggetto visivo handle)</span><span class="sxs-lookup"><span data-stu-id="bbdbf-257">**Scale Handle Collider Padding**: 0.016 (makes the grabbable collider slightly bigger than handle visual)</span></span>
* <span data-ttu-id="bbdbf-258">**Prefab dell'handle** di rotazione: MRTK_BoundingBox_RotateHandle.prefab</span><span class="sxs-lookup"><span data-stu-id="bbdbf-258">**Rotation Handle Prefab**: MRTK_BoundingBox_RotateHandle.prefab</span></span>
* <span data-ttu-id="bbdbf-259">**Dimensioni dell'handle di** rotazione: 0,016</span><span class="sxs-lookup"><span data-stu-id="bbdbf-259">**Rotation Handle Size**: 0.016</span></span>
* <span data-ttu-id="bbdbf-260">**Rotation Handle Collider Padding**: 0,016 (rende il collisore afferrabile leggermente più grande dell'oggetto visivo handle)</span><span class="sxs-lookup"><span data-stu-id="bbdbf-260">**Rotation Handle Collider Padding**: 0.016 (makes the grabbable collider slightly bigger than handle visual)</span></span>

## <a name="transformation-changes-with-object-manipulator"></a><span data-ttu-id="bbdbf-261">Modifiche di trasformazione con il manipolatore di oggetti</span><span class="sxs-lookup"><span data-stu-id="bbdbf-261">Transformation changes with object manipulator</span></span>

<span data-ttu-id="bbdbf-262">Un controllo dei limiti può essere usato in combinazione con [`ObjectManipulator.cs`](object-manipulator.md) per consentire determinati tipi di manipolazione (ad esempio.</span><span class="sxs-lookup"><span data-stu-id="bbdbf-262">A bounds control can be used in combination with [`ObjectManipulator.cs`](object-manipulator.md) to allow for certain types of manipulation (eg.</span></span> <span data-ttu-id="bbdbf-263">spostamento dell'oggetto) senza usare handle.</span><span class="sxs-lookup"><span data-stu-id="bbdbf-263">moving the object) without using handles.</span></span> <span data-ttu-id="bbdbf-264">Il gestore di manipolazione supporta entrambe le interazioni a una e a due mani.</span><span class="sxs-lookup"><span data-stu-id="bbdbf-264">The manipulation handler supports both one and two-handed interactions.</span></span> <span data-ttu-id="bbdbf-265">[Il tracciamento](../input/hand-tracking.md) manuale può essere usato per interagire con un oggetto da vicino.</span><span class="sxs-lookup"><span data-stu-id="bbdbf-265">[Hand tracking](../input/hand-tracking.md) can be used to interact with an object up close.</span></span>

<img src="../images/bounds-control/MRTK_BoundsControl_ObjectManipulator.png" width="450" alt="Bounds control Object Manipulator">

<span data-ttu-id="bbdbf-266">Per fare in modo che i bordi di controllo dei limiti si comportino allo stesso modo quando lo si sposta usando l'interazione lontano, è consigliabile connettere i relativi eventi rispettivamente per On [`ObjectManipulator`](object-manipulator.md) *Manipulation Started* On  /  *Manipulation Ended* a, come illustrato nello `BoundsControl.HighlightWires`  /  `BoundsControl.UnhighlightWires` screenshot precedente.</span><span class="sxs-lookup"><span data-stu-id="bbdbf-266">In order for the bounds control edges to behave the same way when moving it using [`ObjectManipulator`](object-manipulator.md)'s far interaction, it is advised to connect its events for *On Manipulation Started* / *On Manipulation Ended* to `BoundsControl.HighlightWires` / `BoundsControl.UnhighlightWires` respectively, as shown in the screenshot above.</span></span>

## <a name="how-to-add-and-configure-a-bounds-control-using-unity-inspector"></a><span data-ttu-id="bbdbf-267">Come aggiungere e configurare un controllo limiti usando Unity Inspector</span><span class="sxs-lookup"><span data-stu-id="bbdbf-267">How to add and configure a bounds control using Unity Inspector</span></span>

1. <span data-ttu-id="bbdbf-268">Aggiungere Box Collider a un oggetto</span><span class="sxs-lookup"><span data-stu-id="bbdbf-268">Add Box Collider to an object</span></span>
2. <span data-ttu-id="bbdbf-269">Assegnare `BoundsControl` uno script a un oggetto</span><span class="sxs-lookup"><span data-stu-id="bbdbf-269">Assign `BoundsControl` script to an object</span></span>
3. <span data-ttu-id="bbdbf-270">Configurare opzioni, ad esempio i metodi di attivazione (vedere la [sezione Proprietà del controllo riportata](#inspector-properties) di seguito)</span><span class="sxs-lookup"><span data-stu-id="bbdbf-270">Configure options, such as 'Activation' methods (see [Inspector properties](#inspector-properties) section below)</span></span>
4. <span data-ttu-id="bbdbf-271">(Facoltativo) Assegnare prefab e materiali per un controllo HoloLens 2 limiti di stile (vedere la [sezione Gestire gli stili](#handle-styles) più avanti)</span><span class="sxs-lookup"><span data-stu-id="bbdbf-271">(Optional) Assign prefabs and materials for a HoloLens 2 style bounds control (see [Handle styles](#handle-styles) section below)</span></span>

> [!NOTE]
> <span data-ttu-id="bbdbf-272">Usare *il campo Target Object* e *Bounds Override* nel controllo per assegnare un oggetto specifico e un collisore nell'oggetto con più componenti figlio.</span><span class="sxs-lookup"><span data-stu-id="bbdbf-272">Use *Target Object* and *Bounds Override* field in the inspector to assign specific object and collider in the object with multiple child components.</span></span>

![Controllo Bounds](../images/bounds-control/MRTK_BoundsControl_Assign.png)

## <a name="how-to-add-and-configure-a-bounds-control-in-the-code"></a><span data-ttu-id="bbdbf-274">Come aggiungere e configurare un controllo limiti nel codice</span><span class="sxs-lookup"><span data-stu-id="bbdbf-274">How to add and configure a bounds control in the code</span></span>

1. <span data-ttu-id="bbdbf-275">Creare un'istanza del cubo GameObject</span><span class="sxs-lookup"><span data-stu-id="bbdbf-275">Instantiate cube GameObject</span></span>

    ```c#
    GameObject cube = GameObject.CreatePrimitive(PrimitiveType.Cube);
    ```

1. <span data-ttu-id="bbdbf-276">Assegnare `BoundsControl` uno script a un oggetto con collisore usando AddComponent<>()</span><span class="sxs-lookup"><span data-stu-id="bbdbf-276">Assign `BoundsControl` script to an object with collider, using AddComponent<>()</span></span>

    ```c#
    private BoundsControl boundsControl;
    boundsControl = cube.AddComponent<BoundsControl>();
    ```

1. <span data-ttu-id="bbdbf-277">Configurare le opzioni direttamente nel controllo o tramite una delle configurazioni che possono essere configurate tramite script [(vedere](#inspector-properties) la sezione Proprietà e configurazioni del controllo [riportata di](#configuration-objects) seguito)</span><span class="sxs-lookup"><span data-stu-id="bbdbf-277">Configure options either directly on the control or via one of the scriptable configurations (see [Inspector properties](#inspector-properties) and [Configurations](#configuration-objects) section below)</span></span>

    ```c#
    // Change activation method
    boundsControl.BoundsControlActivation = BoundsControlActivationType.ActivateByProximityAndPointer;
    // Make the scale handles large
    boundsControl.ScaleHandlesConfig.HandleSize = 0.1f;
    // Hide rotation handles for x axis
    boundsControl.RotationHandlesConfig.ShowRotationHandleForX = false;
    ```

1. <span data-ttu-id="bbdbf-278">(Facoltativo) Assegnare prefab e materiali per un controllo HoloLens 2 limiti di stile.</span><span class="sxs-lookup"><span data-stu-id="bbdbf-278">(Optional) Assign prefabs and materials for a HoloLens 2 style bounds control.</span></span> <span data-ttu-id="bbdbf-279">Ciò richiede comunque assegnazioni tramite il controllo poiché i materiali e i prefab devono essere caricati dinamicamente.</span><span class="sxs-lookup"><span data-stu-id="bbdbf-279">This still requires assignments through the inspector since the materials and prefabs should be dynamically loaded.</span></span>

> [!NOTE]
> <span data-ttu-id="bbdbf-280">L'uso della cartella 'Resources' di [Unity o shader.Find]( https://docs.unity3d.com/ScriptReference/Shader.Find.html) per il caricamento dinamico degli shader non è consigliato perché le permutazioni dello shader potrebbero mancare in fase di esecuzione.</span><span class="sxs-lookup"><span data-stu-id="bbdbf-280">Using Unity's 'Resources' folder or [Shader.Find]( https://docs.unity3d.com/ScriptReference/Shader.Find.html) for dynamically loading shaders is not recommended since shader permutations may be missing at runtime.</span></span>

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

### <a name="example-set-minimum-maximum-bounds-control-scale-using-minmaxscaleconstraint"></a><span data-ttu-id="bbdbf-281">Esempio: Impostare la scala di controllo dei limiti minimi e massimi usando MinMaxScaleConstraint</span><span class="sxs-lookup"><span data-stu-id="bbdbf-281">Example: Set minimum, maximum bounds control scale using MinMaxScaleConstraint</span></span>

<span data-ttu-id="bbdbf-282">Per impostare la scala minima e massima, collegare un [`MinMaxScaleConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.MinMaxScaleConstraint) oggetto al controllo .</span><span class="sxs-lookup"><span data-stu-id="bbdbf-282">To set the minimum and maximum scale, attach a [`MinMaxScaleConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.MinMaxScaleConstraint) to your control.</span></span> <span data-ttu-id="bbdbf-283">Poiché il controllo dei limiti associa e attiva automaticamente il gestore vincoli, MinMaxScaleConstraint verrà applicato automaticamente alle modifiche della trasformazione dopo che è stato collegato e configurato.</span><span class="sxs-lookup"><span data-stu-id="bbdbf-283">As bounds control automatically attaches and activates constraint manager the MinMaxScaleConstraint will be automatically applied to the transformation changes once it's attached and configured.</span></span>

<span data-ttu-id="bbdbf-284">È anche possibile usare MinMaxScaleConstraint per impostare la scala minima e massima per [`ObjectManipulator`](xref:Microsoft.MixedReality.Toolkit.UI.ObjectManipulator) .</span><span class="sxs-lookup"><span data-stu-id="bbdbf-284">You can also use MinMaxScaleConstraint to set minimum and maximum scale for [`ObjectManipulator`](xref:Microsoft.MixedReality.Toolkit.UI.ObjectManipulator).</span></span>

```c#
GameObject cube = GameObject.CreatePrimitive(PrimitiveType.Cube);
bcontrol = cube.AddComponent<BoundsControl>();
// Important: BoundsControl creates a constraint manager on start if one does not exist.
// There's no need to manually attach a constraint manager.
MinMaxScaleConstraint scaleConstraint = bcontrol.gameObject.AddComponent<MinMaxScaleConstraint>();
scaleConstraint.ScaleMinimum = 1f;
scaleConstraint.ScaleMaximum = 2f;
```

## <a name="example-add-bounds-control-around-a-game-object"></a><span data-ttu-id="bbdbf-285">Esempio: Aggiungere un controllo limiti intorno a un oggetto gioco</span><span class="sxs-lookup"><span data-stu-id="bbdbf-285">Example: Add bounds control around a game object</span></span>

<span data-ttu-id="bbdbf-286">Per aggiungere un controllo limiti intorno a un oggetto, è sufficiente aggiungere un `BoundsControl` componente:</span><span class="sxs-lookup"><span data-stu-id="bbdbf-286">To add a bounds control around an object, simply add a `BoundsControl` component to it:</span></span>

```c#
private void PutABoundsControlAroundIt(GameObject target)
{
   target.AddComponent<BoundsControl>();
}
```

## <a name="migrating-from-bounding-box"></a><span data-ttu-id="bbdbf-287">Migrazione da Bounding Box</span><span class="sxs-lookup"><span data-stu-id="bbdbf-287">Migrating from Bounding Box</span></span>

<span data-ttu-id="bbdbf-288">I prefab e le istanze esistenti che usano [il rettangolo](bounding-box.md) [](../tools/migration-window.md) di selezione possono essere aggiornati al nuovo controllo limiti tramite la finestra di migrazione che fa parte del pacchetto di strumenti MRTK.</span><span class="sxs-lookup"><span data-stu-id="bbdbf-288">Existing prefabs and instances using [bounding box](bounding-box.md) can be upgraded to the new bounds control via the [migration window](../tools/migration-window.md) which is part of the MRTK tools package.</span></span>

<span data-ttu-id="bbdbf-289">Per l'aggiornamento di singole istanze del rettangolo di selezione è disponibile anche un'opzione di migrazione all'interno del controllo proprietà del componente.</span><span class="sxs-lookup"><span data-stu-id="bbdbf-289">For upgrading individual instances of bounding box there's also an a migration option inside the property inspector of the component.</span></span>

<img src="../images/bounds-control/MRTK_BoundsControl_Migrate.png" width="450" alt="Bounds control Migrate">

## <a name="see-also"></a><span data-ttu-id="bbdbf-290">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="bbdbf-290">See also</span></span>

* [<span data-ttu-id="bbdbf-291">Manipolatore di oggetti</span><span class="sxs-lookup"><span data-stu-id="bbdbf-291">Object manipulator</span></span>](object-manipulator.md)
* [<span data-ttu-id="bbdbf-292">Gestione vincoli</span><span class="sxs-lookup"><span data-stu-id="bbdbf-292">Constraint manager</span></span>](constraint-manager.md)
* [<span data-ttu-id="bbdbf-293">Finestra di migrazione</span><span class="sxs-lookup"><span data-stu-id="bbdbf-293">Migration window</span></span>](../tools/migration-window.md)
* [<span data-ttu-id="bbdbf-294">Sistema elastico (sperimentale)</span><span class="sxs-lookup"><span data-stu-id="bbdbf-294">Elastics system (Experimental)</span></span>](../experimental/elastic-system.md)

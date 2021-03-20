---
title: ConfiguringSpatialAwarenessMeshObserver
description: Come configurare l'osservatore della rete spaziale predefinita in MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: 84ba719ca931dbb06809377a31d0b69f3ac63e33
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2021
ms.locfileid: "104693438"
---
# <a name="configuring-mesh-observers-for-device"></a><span data-ttu-id="d7926-104">Configurazione degli osservatori mesh per il dispositivo</span><span class="sxs-lookup"><span data-stu-id="d7926-104">Configuring mesh observers for device</span></span>

<span data-ttu-id="d7926-105">In questa guida viene illustrata la configurazione di un Observer mesh spaziale predefinito in MRTK che supporta la piattaforma di realtà mista di Windows (ad esempio</span><span class="sxs-lookup"><span data-stu-id="d7926-105">This guide will walk through configuring the out-of-box Spatial Mesh Observer in MRTK which supports the Windows Mixed Reality platform (i.e</span></span> <span data-ttu-id="d7926-106">HoloLens).</span><span class="sxs-lookup"><span data-stu-id="d7926-106">HoloLens).</span></span> <span data-ttu-id="d7926-107">L'implementazione predefinita fornita da Mixed Reality Toolkit è la classe [WindowsMixedRealitySpatialMeshObserver](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver) .</span><span class="sxs-lookup"><span data-stu-id="d7926-107">The default implementation provided by the Mixed Reality Toolkit is the [WindowsMixedRealitySpatialMeshObserver](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver) class.</span></span> <span data-ttu-id="d7926-108">Molte delle proprietà in questo articolo si applicano anche ad altre [implementazioni di Observer personalizzate](create-data-provider.md).</span><span class="sxs-lookup"><span data-stu-id="d7926-108">Many of the properties in this article though apply for other [custom Observer implementations](create-data-provider.md).</span></span>

## <a name="profile-settings"></a><span data-ttu-id="d7926-109">Impostazioni del profilo</span><span class="sxs-lookup"><span data-stu-id="d7926-109">Profile settings</span></span>

<span data-ttu-id="d7926-110">I due elementi seguenti devono essere definiti per primi quando si configura un profilo osservatore mesh spaziale per il [sistema di riconoscimento spaziale](spatial-awareness-getting-started.md).</span><span class="sxs-lookup"><span data-stu-id="d7926-110">The following two items must be defined first when configuring a Spatial Mesh Observer profile for the [Spatial Awareness system](spatial-awareness-getting-started.md).</span></span>

1. <span data-ttu-id="d7926-111">Implementazione del tipo Observer concreto</span><span class="sxs-lookup"><span data-stu-id="d7926-111">The concrete observer type implementation</span></span>
1. <span data-ttu-id="d7926-112">elenco delle piattaforme supportate per l'esecuzione di questo Observer</span><span class="sxs-lookup"><span data-stu-id="d7926-112">list of supported platform(s) to run this observer</span></span>

> [!NOTE]
> <span data-ttu-id="d7926-113">Tutti gli osservatori devono estendere l'interfaccia [IMixedRealitySpatialAwarenessObserver](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver) .</span><span class="sxs-lookup"><span data-stu-id="d7926-113">All observers must extend the [IMixedRealitySpatialAwarenessObserver](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver) interface.</span></span>

![Tipi di piattaforma delle impostazioni generali dell'Observer mesh](../images/spatial-awareness/SpatialAwarenessMeshObserverProfile_TypesPlatforms.png)

### <a name="general-settings"></a><span data-ttu-id="d7926-115">Impostazioni generali</span><span class="sxs-lookup"><span data-stu-id="d7926-115">General settings</span></span>

![Impostazioni generali delle impostazioni genral di mesh Observer](../images/spatial-awareness/MeshObserverGeneralSettings.png)

<span data-ttu-id="d7926-117">**Comportamento di avvio**</span><span class="sxs-lookup"><span data-stu-id="d7926-117">**Startup Behavior**</span></span>

<span data-ttu-id="d7926-118">Il comportamento di avvio specifica se l'Observer inizierà l'esecuzione quando ne viene creata la prima istanza.</span><span class="sxs-lookup"><span data-stu-id="d7926-118">The startup behavior specifies whether the observer will begin running when first instantiated.</span></span> <span data-ttu-id="d7926-119">Le due opzioni sono:</span><span class="sxs-lookup"><span data-stu-id="d7926-119">The two options are:</span></span>

* <span data-ttu-id="d7926-120">*Avvio automatico* : valore predefinito in base al quale l'Observer inizierà l'operazione dopo l'inizializzazione</span><span class="sxs-lookup"><span data-stu-id="d7926-120">*Auto Start* - The default value whereby the observer will begin operation after initialization</span></span>
* <span data-ttu-id="d7926-121">*Avvio manuale* : l'Observer rimarrà in attesa di essere indirizzato all'avvio</span><span class="sxs-lookup"><span data-stu-id="d7926-121">*Manual Start* - The Observer will wait to be directed to start</span></span>

<span data-ttu-id="d7926-122">Se si usa l' *avvio manuale*, è necessario [riprenderle e sospenderle in fase di esecuzione tramite codice](usage-guide.md#starting-and-stopping-mesh-observation).</span><span class="sxs-lookup"><span data-stu-id="d7926-122">If using *Manual Start*, one must [resume and suspend them at runtime via code](usage-guide.md#starting-and-stopping-mesh-observation).</span></span>

<span data-ttu-id="d7926-123">**Intervallo di aggiornamento**</span><span class="sxs-lookup"><span data-stu-id="d7926-123">**Update Interval**</span></span>

<span data-ttu-id="d7926-124">Tempo, in secondi, tra le richieste alla piattaforma per aggiornare i dati di rete spaziale.</span><span class="sxs-lookup"><span data-stu-id="d7926-124">The time, in seconds, between requests to the platform to update spatial mesh data.</span></span> <span data-ttu-id="d7926-125">I valori tipici sono compresi nell'intervallo tra 0,1 e 5,0 secondi.</span><span class="sxs-lookup"><span data-stu-id="d7926-125">Typical values fall in the range of 0.1 and 5.0 seconds.</span></span>

<span data-ttu-id="d7926-126">**Osservatore stazionario**</span><span class="sxs-lookup"><span data-stu-id="d7926-126">**Is Stationary Observer**</span></span>

<span data-ttu-id="d7926-127">Indica se l'osservatore deve rimanere fisso o se deve essere spostato e aggiornato con l'utente.</span><span class="sxs-lookup"><span data-stu-id="d7926-127">Indicates whether or not the observer is to remain stationary or to move and update with the user.</span></span> <span data-ttu-id="d7926-128">Se true, la *forma Observer* con volume definito dagli *extent di osservazione* rimarrà all'origine all'avvio.</span><span class="sxs-lookup"><span data-stu-id="d7926-128">If true, the *Observer Shape* with volume defined by *Observation Extents* will remain at the origin on startup.</span></span> <span data-ttu-id="d7926-129">Se false, lo spazio Observer seguirà l'intestazione dell'utente come origine della forma.</span><span class="sxs-lookup"><span data-stu-id="d7926-129">If false, the Observer space will follow the user's head as the shape's origin.</span></span>

<span data-ttu-id="d7926-130">Non verranno calcolati i dati mesh per nessuna area fisica all'esterno dello spazio Observer, come definito dalle proprietà seguenti: *è Stazional Observer*, \* Observer Shape \* \* ed extent di *osservazione*.</span><span class="sxs-lookup"><span data-stu-id="d7926-130">There will be no mesh data calculated for any physical area outside of the Observer space as defined by these properties: *Is Stationary Observer*, \*Observer Shape\*\*, and *Observation Extents*.</span></span>

<span data-ttu-id="d7926-131">**Forma Observer**</span><span class="sxs-lookup"><span data-stu-id="d7926-131">**Observer Shape**</span></span>

<span data-ttu-id="d7926-132">La forma Observer definisce il tipo di volume che l'osservatore mesh userà per osservare le maglie.</span><span class="sxs-lookup"><span data-stu-id="d7926-132">The observer shape defines the type of volume that the mesh observer will use when observing meshes.</span></span> <span data-ttu-id="d7926-133">Le opzioni supportate sono:</span><span class="sxs-lookup"><span data-stu-id="d7926-133">The supported options are:</span></span>

* <span data-ttu-id="d7926-134">*Cubo allineato asse* : forma rettangolare che rimane allineata con gli assi del sistema di coordinate globale, come determinato all'avvio dell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="d7926-134">*Axis Aligned Cube* - Rectangular shape that stays aligned with the axes of the world coordinate system, as determined at application startup.</span></span>
* <span data-ttu-id="d7926-135">*Cubo allineato all'utente* : forma rettangolare che ruota per l'allineamento con il sistema di coordinate locale degli utenti.</span><span class="sxs-lookup"><span data-stu-id="d7926-135">*User Aligned Cube* - Rectangular shape that rotates to align with the users local coordinate system.</span></span>
* <span data-ttu-id="d7926-136">*Sphere* : un volume sferico con un centro nell'origine dello spazio globale.</span><span class="sxs-lookup"><span data-stu-id="d7926-136">*Sphere* - A spherical volume with a center at the world space origin.</span></span> <span data-ttu-id="d7926-137">Il valore X della proprietà *extent di osservazione* verrà usato come raggio della sfera.</span><span class="sxs-lookup"><span data-stu-id="d7926-137">The X value of the *Observation Extents* property will be used as the radius of the sphere.</span></span>

<span data-ttu-id="d7926-138">**Extent di osservazione**</span><span class="sxs-lookup"><span data-stu-id="d7926-138">**Observation Extents**</span></span>

<span data-ttu-id="d7926-139">Gli extent di osservazione definiscono la distanza dal punto di osservazione in cui verranno osservate le maglie.</span><span class="sxs-lookup"><span data-stu-id="d7926-139">The observation extents define the distance from the observation point that meshes will be observed.</span></span>

### <a name="physics-settings"></a><span data-ttu-id="d7926-140">Impostazioni di fisica</span><span class="sxs-lookup"><span data-stu-id="d7926-140">Physics settings</span></span>

![Impostazioni fisiche osservatore mesh](../images/spatial-awareness/MeshObserverPhysicsSettings.png)

<span data-ttu-id="d7926-142">**Livello di fisica**</span><span class="sxs-lookup"><span data-stu-id="d7926-142">**Physics Layer**</span></span>

<span data-ttu-id="d7926-143">Livello di fisica in cui verranno inseriti gli oggetti mesh spaziali per interagire con i sistemi di Unity e RayCast.</span><span class="sxs-lookup"><span data-stu-id="d7926-143">The physics layer on which spatial mesh objects will be placed in order to interact with the Unity Physics and RayCast systems.</span></span>

> [!NOTE]
> <span data-ttu-id="d7926-144">Il Toolkit di realtà mista riserva il *livello 31* per impostazione predefinita per l'uso da parte degli osservatori di consapevolezza spaziale.</span><span class="sxs-lookup"><span data-stu-id="d7926-144">The Mixed Reality Toolkit reserves *layer 31* by default for use by Spatial Awareness observers.</span></span>

<span data-ttu-id="d7926-145">**Ricalcola normali**</span><span class="sxs-lookup"><span data-stu-id="d7926-145">**Recalculate Normals**</span></span>

<span data-ttu-id="d7926-146">Specifica se l'osservatore mesh ricalcolerà le normalità della mesh che segue l'osservazione.</span><span class="sxs-lookup"><span data-stu-id="d7926-146">Specifies whether or not the mesh observer will recalculate the normals of the mesh following observation.</span></span> <span data-ttu-id="d7926-147">Questa impostazione è disponibile per garantire che le applicazioni ricevano mesh contenenti dati normali validi sulle piattaforme che non le restituiscono con mesh.</span><span class="sxs-lookup"><span data-stu-id="d7926-147">This setting is available to ensure applications receive meshes that contain valid normals data on platforms that do not return them with meshes.</span></span>

### <a name="level-of-detail-settings"></a><span data-ttu-id="d7926-148">Livello di impostazioni dettaglio</span><span class="sxs-lookup"><span data-stu-id="d7926-148">Level of detail settings</span></span>

![Livello di osservazione mesh delle impostazioni dei dettagli](../images/spatial-awareness/MeshObserverLevelOfDetailSettings.png)

<span data-ttu-id="d7926-150">**Livello di dettaglio**</span><span class="sxs-lookup"><span data-stu-id="d7926-150">**Level of Detail**</span></span>

<span data-ttu-id="d7926-151">Specifica il livello di dettaglio (LOD) dei dati di mesh spaziali.</span><span class="sxs-lookup"><span data-stu-id="d7926-151">Specifies the level of detail (LOD) of the spatial mesh data.</span></span> <span data-ttu-id="d7926-152">I valori attualmente definiti sono grossolani, fini e personalizzati.</span><span class="sxs-lookup"><span data-stu-id="d7926-152">Currently defined values are Coarse, Fine and Custom.</span></span>

* <span data-ttu-id="d7926-153">*Grossolano* : pone un minore effetto sulle prestazioni dell'applicazione ed è un'ottima scelta per la ricerca di navigazione/piano.</span><span class="sxs-lookup"><span data-stu-id="d7926-153">*Coarse* - Places a smaller impact on application performance and is an excellent choice for navigation/plane finding.</span></span>

* <span data-ttu-id="d7926-154">Impostazione con bilanciamento del *media* spesso utile per le esperienze che analizzano continuamente l'ambiente sia per funzionalità di grandi dimensioni, pavimenti che muri, oltre ai dettagli sull'occlusione.</span><span class="sxs-lookup"><span data-stu-id="d7926-154">*Medium* - Balanced setting often useful for experiences that continually scan the environment for both large features, floors and walls, as well as occlusion details.</span></span>

* <span data-ttu-id="d7926-155">Con *precisione* , in genere si ha un maggiore effetto sulle prestazioni dell'applicazione ed è un'ottima opzione per le mesh di occlusione.</span><span class="sxs-lookup"><span data-stu-id="d7926-155">*Fine* - Generally exacts a higher impact on application performance and is a great option for occlusion meshes.</span></span>

* <span data-ttu-id="d7926-156">*Personalizzata* : richiede all'applicazione di specificare la proprietà del *contatore triangoli/cubi* e consente alle applicazioni di ottimizzare l'accuratezza e l'effetto sulle prestazioni dell'osservatore mesh spaziale.</span><span class="sxs-lookup"><span data-stu-id="d7926-156">*Custom* - Requires the application to specify the *Triangles / Cubic Meter* property and allows applications to tune the accuracy vs. performance impact of the spatial mesh observer.</span></span>

> [!NOTE]
> <span data-ttu-id="d7926-157">Non è garantito che tutti i valori dei *contatori triangoli/cubici* siano rispettati da tutte le piattaforme.</span><span class="sxs-lookup"><span data-stu-id="d7926-157">It is not guaranteed that all *Triangles/Cubic Meter* values are honored by all platforms.</span></span> <span data-ttu-id="d7926-158">La sperimentazione e la profilatura sono consigliate quando si usa un valore LOD personalizzato.</span><span class="sxs-lookup"><span data-stu-id="d7926-158">Experimentation and profiling is highly recommended when using a custom LOD.</span></span>

<span data-ttu-id="d7926-159">**Triangoli per misuratore cubico**</span><span class="sxs-lookup"><span data-stu-id="d7926-159">**Triangles per Cubic Meter**</span></span>

<span data-ttu-id="d7926-160">Valido quando si usa l'impostazione *personalizzata* per la proprietà **livello di dettaglio** e specifica la densità del triangolo per la mesh spaziale.</span><span class="sxs-lookup"><span data-stu-id="d7926-160">Valid when using the *Custom* setting for the **Level of Detail** property and specifies the triangle density for the spatial mesh.</span></span>

### <a name="display-settings"></a><span data-ttu-id="d7926-161">Impostazioni schermo</span><span class="sxs-lookup"><span data-stu-id="d7926-161">Display settings</span></span>

![Impostazioni di visualizzazione Mesh Observer](../images/spatial-awareness/MeshObserverDisplaySettings.png)

<span data-ttu-id="d7926-163">**Opzione di visualizzazione**</span><span class="sxs-lookup"><span data-stu-id="d7926-163">**Display Option**</span></span>

<span data-ttu-id="d7926-164">Specifica la modalità di visualizzazione delle mesh spaziali da parte dell'osservatore.</span><span class="sxs-lookup"><span data-stu-id="d7926-164">Specifies how spatial meshes are to be displayed by the observer.</span></span> <span data-ttu-id="d7926-165">I valori supportati sono:</span><span class="sxs-lookup"><span data-stu-id="d7926-165">Supported values are:</span></span>

* <span data-ttu-id="d7926-166">*None* -Observer non eseguirà il rendering della mesh</span><span class="sxs-lookup"><span data-stu-id="d7926-166">*None* - Observer will not render the mesh</span></span>
* <span data-ttu-id="d7926-167">*Visible* : i dati mesh saranno visibili usando il *materiale visibile*</span><span class="sxs-lookup"><span data-stu-id="d7926-167">*Visible* - Mesh data will be visible using the *Visible Material*</span></span>
* <span data-ttu-id="d7926-168">*Occlusione* : i dati mesh verranno occluderei in scena usando il *materiale di occlusione*</span><span class="sxs-lookup"><span data-stu-id="d7926-168">*Occlusion* - Mesh data will be occlude items in scene using the *Occlusion Material*</span></span>

![Selezionare l'implementazione del sistema di riconoscimento spaziale](../images/spatial-awareness/MRTK_SpatialAwareness_DisplayOptions.jpg)

<span data-ttu-id="d7926-170">Gli osservatori spaziali possono essere [ripresi o sospesi in fase di esecuzione tramite codice.](usage-guide.md#starting-and-stopping-mesh-observation)</span><span class="sxs-lookup"><span data-stu-id="d7926-170">Spatial Observers can be [resumed/suspended at runtime via code.](usage-guide.md#starting-and-stopping-mesh-observation)</span></span>

> [!WARNING]
> <span data-ttu-id="d7926-171">L'impostazione dell' *opzione di visualizzazione* su *None* **non impedisce l'** esecuzione dell'Observer.</span><span class="sxs-lookup"><span data-stu-id="d7926-171">Setting *Display Option* to *None* does **NOT** stop the observer from running.</span></span> <span data-ttu-id="d7926-172">Se si desidera arrestare tutti gli osservatori, le applicazioni dovranno sospendere tutti gli osservatori tramite [`CoreServices.SpatialAwareness.SuspendObservers()`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessSystem.SuspendObservers)</span><span class="sxs-lookup"><span data-stu-id="d7926-172">If you wish to stop all observers, applications will need to suspend all observers via [`CoreServices.SpatialAwareness.SuspendObservers()`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessSystem.SuspendObservers)</span></span>

<span data-ttu-id="d7926-173">**Materiale visibile**</span><span class="sxs-lookup"><span data-stu-id="d7926-173">**Visible Material**</span></span>

<span data-ttu-id="d7926-174">Indica il materiale da usare quando si visualizza la mesh spaziale.</span><span class="sxs-lookup"><span data-stu-id="d7926-174">Indicates the material to be used when visualizing the spatial mesh.</span></span>

<span data-ttu-id="d7926-175">**Materiale occlusione**</span><span class="sxs-lookup"><span data-stu-id="d7926-175">**Occlusion Material**</span></span>

<span data-ttu-id="d7926-176">Indica il materiale da usare per fare in modo che la mesh spaziale occludere gli ologrammi.</span><span class="sxs-lookup"><span data-stu-id="d7926-176">Indicates the material to be used to cause the spatial mesh to occlude holograms.</span></span>

## <a name="see-also"></a><span data-ttu-id="d7926-177">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="d7926-177">See also</span></span>

* [<span data-ttu-id="d7926-178">Sistema di riconoscimento spaziale</span><span class="sxs-lookup"><span data-stu-id="d7926-178">Spatial Awareness System</span></span>](spatial-awareness-getting-started.md)
* [<span data-ttu-id="d7926-179">Configurazione del sistema di riconoscimento spaziale tramite codice</span><span class="sxs-lookup"><span data-stu-id="d7926-179">Configuring Spatial Awareness system via Code</span></span>](usage-guide.md)
* [<span data-ttu-id="d7926-180">Documentazione dell'API IMixedRealitySpatialAwarenessObserver</span><span class="sxs-lookup"><span data-stu-id="d7926-180">IMixedRealitySpatialAwarenessObserver API documentation</span></span>](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver)
* [<span data-ttu-id="d7926-181">Documentazione dell'API IMixedRealitySpatialAwarenessMeshObserver</span><span class="sxs-lookup"><span data-stu-id="d7926-181">IMixedRealitySpatialAwarenessMeshObserver API documentation</span></span>](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessMeshObserver)
* [<span data-ttu-id="d7926-182">Documentazione dell'API BaseSpatialObserver</span><span class="sxs-lookup"><span data-stu-id="d7926-182">BaseSpatialObserver API documentation</span></span>](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.BaseSpatialObserver)

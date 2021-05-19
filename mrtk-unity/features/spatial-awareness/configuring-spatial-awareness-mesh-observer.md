---
title: Configurazione dell'osservatore della mesh di consapevolezza spaziale
description: Come configurare l'osservatore di mesh spaziale predefinito in MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: 0d71a32d76624698e78b8123f427ddefc08f3d0b
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144964"
---
# <a name="configuring-mesh-observers-for-device"></a><span data-ttu-id="1ce1a-104">Configurazione degli osservatori mesh per il dispositivo</span><span class="sxs-lookup"><span data-stu-id="1ce1a-104">Configuring mesh observers for device</span></span>

<span data-ttu-id="1ce1a-105">Questa guida illustra la configurazione dell'osservatore di mesh spaziale predefinito in MRTK che supporta la piattaforma di Windows Mixed Reality (ad esempio</span><span class="sxs-lookup"><span data-stu-id="1ce1a-105">This guide will walk through configuring the out-of-box Spatial Mesh Observer in MRTK which supports the Windows Mixed Reality platform (i.e</span></span> <span data-ttu-id="1ce1a-106">HoloLens).</span><span class="sxs-lookup"><span data-stu-id="1ce1a-106">HoloLens).</span></span> <span data-ttu-id="1ce1a-107">L'implementazione predefinita fornita da Mixed Reality Toolkit è [la classe WindowsMixedRealitySpatialMeshObserver.](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver)</span><span class="sxs-lookup"><span data-stu-id="1ce1a-107">The default implementation provided by the Mixed Reality Toolkit is the [WindowsMixedRealitySpatialMeshObserver](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver) class.</span></span> <span data-ttu-id="1ce1a-108">Molte delle proprietà in questo articolo, tuttavia, si applicano ad altre [implementazioni observer personalizzate.](create-data-provider.md)</span><span class="sxs-lookup"><span data-stu-id="1ce1a-108">Many of the properties in this article though apply for other [custom Observer implementations](create-data-provider.md).</span></span>

## <a name="profile-settings"></a><span data-ttu-id="1ce1a-109">Impostazioni del profilo</span><span class="sxs-lookup"><span data-stu-id="1ce1a-109">Profile settings</span></span>

<span data-ttu-id="1ce1a-110">I due elementi seguenti devono essere definiti per primi quando si configura un profilo osservatore della mesh spaziale per il [sistema di consapevolezza spaziale](spatial-awareness-getting-started.md).</span><span class="sxs-lookup"><span data-stu-id="1ce1a-110">The following two items must be defined first when configuring a Spatial Mesh Observer profile for the [Spatial Awareness system](spatial-awareness-getting-started.md).</span></span>

1. <span data-ttu-id="1ce1a-111">Implementazione del tipo observer concreto</span><span class="sxs-lookup"><span data-stu-id="1ce1a-111">The concrete observer type implementation</span></span>
1. <span data-ttu-id="1ce1a-112">elenco delle piattaforme supportate per l'esecuzione di questo osservatore</span><span class="sxs-lookup"><span data-stu-id="1ce1a-112">list of supported platform(s) to run this observer</span></span>

> [!NOTE]
> <span data-ttu-id="1ce1a-113">Tutti gli osservatori devono estendere [l'interfaccia IMixedRealitySpatialAwarenessObserver.](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver)</span><span class="sxs-lookup"><span data-stu-id="1ce1a-113">All observers must extend the [IMixedRealitySpatialAwarenessObserver](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver) interface.</span></span>

![Tipi di piattaforma delle impostazioni generali di Mesh Observer](../images/spatial-awareness/SpatialAwarenessMeshObserverProfile_TypesPlatforms.png)

### <a name="general-settings"></a><span data-ttu-id="1ce1a-115">Impostazioni generali</span><span class="sxs-lookup"><span data-stu-id="1ce1a-115">General settings</span></span>

![Impostazioni generali dell'osservatore mesh Impostazioni genrali](../images/spatial-awareness/MeshObserverGeneralSettings.png)

<span data-ttu-id="1ce1a-117">**Comportamento di avvio**</span><span class="sxs-lookup"><span data-stu-id="1ce1a-117">**Startup Behavior**</span></span>

<span data-ttu-id="1ce1a-118">Il comportamento di avvio specifica se l'osservatore inizierà l'esecuzione alla prima creazione di un'istanza.</span><span class="sxs-lookup"><span data-stu-id="1ce1a-118">The startup behavior specifies whether the observer will begin running when first instantiated.</span></span> <span data-ttu-id="1ce1a-119">Le due opzioni sono:</span><span class="sxs-lookup"><span data-stu-id="1ce1a-119">The two options are:</span></span>

* <span data-ttu-id="1ce1a-120">*Avvio automatico:* valore predefinito in base al quale l'osservatore inizierà l'operazione dopo l'inizializzazione</span><span class="sxs-lookup"><span data-stu-id="1ce1a-120">*Auto Start* - The default value whereby the observer will begin operation after initialization</span></span>
* <span data-ttu-id="1ce1a-121">*Avvio manuale:* l'osservatore attenderà di essere indirizzato all'avvio</span><span class="sxs-lookup"><span data-stu-id="1ce1a-121">*Manual Start* - The Observer will wait to be directed to start</span></span>

<span data-ttu-id="1ce1a-122">Se si usa *l'avvio* manuale, è [necessario riprenderli e sospenderli in fase di esecuzione tramite codice](usage-guide.md#starting-and-stopping-mesh-observation).</span><span class="sxs-lookup"><span data-stu-id="1ce1a-122">If using *Manual Start*, one must [resume and suspend them at runtime via code](usage-guide.md#starting-and-stopping-mesh-observation).</span></span>

<span data-ttu-id="1ce1a-123">**Intervallo di aggiornamento**</span><span class="sxs-lookup"><span data-stu-id="1ce1a-123">**Update Interval**</span></span>

<span data-ttu-id="1ce1a-124">Tempo, in secondi, tra le richieste alla piattaforma per aggiornare i dati della mesh spaziale.</span><span class="sxs-lookup"><span data-stu-id="1ce1a-124">The time, in seconds, between requests to the platform to update spatial mesh data.</span></span> <span data-ttu-id="1ce1a-125">I valori tipici rientrano nell'intervallo di 0,1 e 5,0 secondi.</span><span class="sxs-lookup"><span data-stu-id="1ce1a-125">Typical values fall in the range of 0.1 and 5.0 seconds.</span></span>

<span data-ttu-id="1ce1a-126">**Is Stationary Observer**</span><span class="sxs-lookup"><span data-stu-id="1ce1a-126">**Is Stationary Observer**</span></span>

<span data-ttu-id="1ce1a-127">Indica se l'osservatore deve rimanere stazionaria o spostare e aggiornare con l'utente.</span><span class="sxs-lookup"><span data-stu-id="1ce1a-127">Indicates whether or not the observer is to remain stationary or to move and update with the user.</span></span> <span data-ttu-id="1ce1a-128">Se true, la *forma osservatore* con volume definito da *Extent di osservazione* rimarrà all'origine all'avvio.</span><span class="sxs-lookup"><span data-stu-id="1ce1a-128">If true, the *Observer Shape* with volume defined by *Observation Extents* will remain at the origin on startup.</span></span> <span data-ttu-id="1ce1a-129">Se false, lo spazio Observer seguirà la testa dell'utente come origine della forma.</span><span class="sxs-lookup"><span data-stu-id="1ce1a-129">If false, the Observer space will follow the user's head as the shape's origin.</span></span>

<span data-ttu-id="1ce1a-130">Non verranno calcolati dati di mesh per alcuna area fisica esterna allo spazio Observer, come definito da queste proprietà: *Is Stationary Observer*, *Observer Shape*\* e *Observation Extents*.</span><span class="sxs-lookup"><span data-stu-id="1ce1a-130">There will be no mesh data calculated for any physical area outside of the Observer space as defined by these properties: *Is Stationary Observer*, \*Observer Shape\*\*, and *Observation Extents*.</span></span>

<span data-ttu-id="1ce1a-131">**Forma osservatore**</span><span class="sxs-lookup"><span data-stu-id="1ce1a-131">**Observer Shape**</span></span>

<span data-ttu-id="1ce1a-132">La forma osservatore definisce il tipo di volume che l'osservatore di mesh userà durante l'osservazione delle mesh.</span><span class="sxs-lookup"><span data-stu-id="1ce1a-132">The observer shape defines the type of volume that the mesh observer will use when observing meshes.</span></span> <span data-ttu-id="1ce1a-133">Le opzioni supportate sono:</span><span class="sxs-lookup"><span data-stu-id="1ce1a-133">The supported options are:</span></span>

* <span data-ttu-id="1ce1a-134">*Cubo allineato all'asse:* forma rettangolare che rimane allineata agli assi del sistema di coordinate del mondo, come determinato all'avvio dell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="1ce1a-134">*Axis Aligned Cube* - Rectangular shape that stays aligned with the axes of the world coordinate system, as determined at application startup.</span></span>
* <span data-ttu-id="1ce1a-135">*Cubo allineato dall'utente:* forma rettangolare che ruota per allinearsi al sistema di coordinate locale degli utenti.</span><span class="sxs-lookup"><span data-stu-id="1ce1a-135">*User Aligned Cube* - Rectangular shape that rotates to align with the users local coordinate system.</span></span>
* <span data-ttu-id="1ce1a-136">*Sphere:* volume sferico con un centro all'origine dello spazio mondiale.</span><span class="sxs-lookup"><span data-stu-id="1ce1a-136">*Sphere* - A spherical volume with a center at the world space origin.</span></span> <span data-ttu-id="1ce1a-137">Il valore X della *proprietà Observation Extents* verrà usato come raggio della sfera.</span><span class="sxs-lookup"><span data-stu-id="1ce1a-137">The X value of the *Observation Extents* property will be used as the radius of the sphere.</span></span>

<span data-ttu-id="1ce1a-138">**Extent di osservazione**</span><span class="sxs-lookup"><span data-stu-id="1ce1a-138">**Observation Extents**</span></span>

<span data-ttu-id="1ce1a-139">Gli extent di osservazione definiscono la distanza dal punto di osservazione in cui verranno osservate le mesh.</span><span class="sxs-lookup"><span data-stu-id="1ce1a-139">The observation extents define the distance from the observation point that meshes will be observed.</span></span>

### <a name="physics-settings"></a><span data-ttu-id="1ce1a-140">Impostazioni di fisica</span><span class="sxs-lookup"><span data-stu-id="1ce1a-140">Physics settings</span></span>

![Impostazioni fisiche dell'osservatore mesh](../images/spatial-awareness/MeshObserverPhysicsSettings.png)

<span data-ttu-id="1ce1a-142">**Livello fisico**</span><span class="sxs-lookup"><span data-stu-id="1ce1a-142">**Physics Layer**</span></span>

<span data-ttu-id="1ce1a-143">Livello fisico su cui verranno posizionati gli oggetti mesh spaziale per interagire con i sistemi Unity Physics e RayCast.</span><span class="sxs-lookup"><span data-stu-id="1ce1a-143">The physics layer on which spatial mesh objects will be placed in order to interact with the Unity Physics and RayCast systems.</span></span>

> [!NOTE]
> <span data-ttu-id="1ce1a-144">Mixed Reality Toolkit riserva il *livello 31* per impostazione predefinita per l'uso da parte degli osservatori di Consapevolezza spaziale.</span><span class="sxs-lookup"><span data-stu-id="1ce1a-144">The Mixed Reality Toolkit reserves *layer 31* by default for use by Spatial Awareness observers.</span></span>

<span data-ttu-id="1ce1a-145">**Ricalcolare le normali**</span><span class="sxs-lookup"><span data-stu-id="1ce1a-145">**Recalculate Normals**</span></span>

<span data-ttu-id="1ce1a-146">Specifica se l'osservatore mesh ricalcolerà o meno le normali della mesh dopo l'osservazione.</span><span class="sxs-lookup"><span data-stu-id="1ce1a-146">Specifies whether or not the mesh observer will recalculate the normals of the mesh following observation.</span></span> <span data-ttu-id="1ce1a-147">Questa impostazione è disponibile per garantire che le applicazioni ricevano mesh che contengono dati normali validi su piattaforme che non le restituiscono con mesh.</span><span class="sxs-lookup"><span data-stu-id="1ce1a-147">This setting is available to ensure applications receive meshes that contain valid normals data on platforms that do not return them with meshes.</span></span>

### <a name="level-of-detail-settings"></a><span data-ttu-id="1ce1a-148">Impostazioni del livello di dettaglio</span><span class="sxs-lookup"><span data-stu-id="1ce1a-148">Level of detail settings</span></span>

![Impostazioni del livello di dettaglio dell'osservatore mesh](../images/spatial-awareness/MeshObserverLevelOfDetailSettings.png)

<span data-ttu-id="1ce1a-150">**Livello di dettaglio**</span><span class="sxs-lookup"><span data-stu-id="1ce1a-150">**Level of Detail**</span></span>

<span data-ttu-id="1ce1a-151">Specifica il livello di dettaglio (LOD) dei dati della mesh spaziale.</span><span class="sxs-lookup"><span data-stu-id="1ce1a-151">Specifies the level of detail (LOD) of the spatial mesh data.</span></span> <span data-ttu-id="1ce1a-152">I valori attualmente definiti sono Grosso, Fine e Personalizzato.</span><span class="sxs-lookup"><span data-stu-id="1ce1a-152">Currently defined values are Coarse, Fine and Custom.</span></span>

* <span data-ttu-id="1ce1a-153">*Grosso modo: consente di* avere un impatto minore sulle prestazioni dell'applicazione ed è una scelta eccellente per la ricerca di navigazione/piano.</span><span class="sxs-lookup"><span data-stu-id="1ce1a-153">*Coarse* - Places a smaller impact on application performance and is an excellent choice for navigation/plane finding.</span></span>

* <span data-ttu-id="1ce1a-154">*Media:* impostazione bilanciata spesso utile per le esperienze che analizzano continuamente l'ambiente alla ricerca di caratteristiche, piani e pareti di grandi dimensioni, nonché dettagli di occlusione.</span><span class="sxs-lookup"><span data-stu-id="1ce1a-154">*Medium* - Balanced setting often useful for experiences that continually scan the environment for both large features, floors and walls, as well as occlusion details.</span></span>

* <span data-ttu-id="1ce1a-155">*Fine:* in genere ha un impatto maggiore sulle prestazioni dell'applicazione ed è un'ottima opzione per le mesh di occlusione.</span><span class="sxs-lookup"><span data-stu-id="1ce1a-155">*Fine* - Generally exacts a higher impact on application performance and is a great option for occlusion meshes.</span></span>

* <span data-ttu-id="1ce1a-156">*Personalizzato:* richiede all'applicazione di specificare la proprietà *Triangles/Cubic Meter* e consente alle applicazioni di ottimizzare l'accuratezza e l'impatto sulle prestazioni dell'osservatore della mesh spaziale.</span><span class="sxs-lookup"><span data-stu-id="1ce1a-156">*Custom* - Requires the application to specify the *Triangles / Cubic Meter* property and allows applications to tune the accuracy vs. performance impact of the spatial mesh observer.</span></span>

> [!NOTE]
> <span data-ttu-id="1ce1a-157">Non è garantito che tutti i *valori triangles/cubic meter* siano rispettati da tutte le piattaforme.</span><span class="sxs-lookup"><span data-stu-id="1ce1a-157">It is not guaranteed that all *Triangles/Cubic Meter* values are honored by all platforms.</span></span> <span data-ttu-id="1ce1a-158">La sperimentazione e la profilatura sono altamente consigliate quando si usa un LOD personalizzato.</span><span class="sxs-lookup"><span data-stu-id="1ce1a-158">Experimentation and profiling is highly recommended when using a custom LOD.</span></span>

<span data-ttu-id="1ce1a-159">**Triangoli per contatore cubo**</span><span class="sxs-lookup"><span data-stu-id="1ce1a-159">**Triangles per Cubic Meter**</span></span>

<span data-ttu-id="1ce1a-160">Valido quando si usa *l'impostazione Personalizzata* per **la proprietà Livello** di dettaglio e specifica la densità del triangolo per la mesh spaziale.</span><span class="sxs-lookup"><span data-stu-id="1ce1a-160">Valid when using the *Custom* setting for the **Level of Detail** property and specifies the triangle density for the spatial mesh.</span></span>

### <a name="display-settings"></a><span data-ttu-id="1ce1a-161">Impostazioni schermo</span><span class="sxs-lookup"><span data-stu-id="1ce1a-161">Display settings</span></span>

![Impostazioni di visualizzazione dell'osservatore mesh](../images/spatial-awareness/MeshObserverDisplaySettings.png)

<span data-ttu-id="1ce1a-163">**Opzione di visualizzazione**</span><span class="sxs-lookup"><span data-stu-id="1ce1a-163">**Display Option**</span></span>

<span data-ttu-id="1ce1a-164">Specifica la modalità di visualizzazione delle mesh spaziali da parte dell'osservatore.</span><span class="sxs-lookup"><span data-stu-id="1ce1a-164">Specifies how spatial meshes are to be displayed by the observer.</span></span> <span data-ttu-id="1ce1a-165">I valori supportati sono:</span><span class="sxs-lookup"><span data-stu-id="1ce1a-165">Supported values are:</span></span>

* <span data-ttu-id="1ce1a-166">*Nessuno-* Observer non eseguirà il rendering della mesh</span><span class="sxs-lookup"><span data-stu-id="1ce1a-166">*None* - Observer will not render the mesh</span></span>
* <span data-ttu-id="1ce1a-167">*Visibile:* i dati della mesh saranno visibili usando *il materiale visibile*</span><span class="sxs-lookup"><span data-stu-id="1ce1a-167">*Visible* - Mesh data will be visible using the *Visible Material*</span></span>
* <span data-ttu-id="1ce1a-168">*Occlusione:* i dati della mesh occludono gli elementi nella scena usando il *materiale di occlusione*</span><span class="sxs-lookup"><span data-stu-id="1ce1a-168">*Occlusion* - Mesh data will be occlude items in scene using the *Occlusion Material*</span></span>

![Selezionare l'implementazione del sistema di consapevolezza spaziale](../images/spatial-awareness/MRTK_SpatialAwareness_DisplayOptions.jpg)

<span data-ttu-id="1ce1a-170">Gli osservatori spaziali possono [essere ripresi/sospesi in fase di esecuzione tramite codice.](usage-guide.md#starting-and-stopping-mesh-observation)</span><span class="sxs-lookup"><span data-stu-id="1ce1a-170">Spatial Observers can be [resumed/suspended at runtime via code.](usage-guide.md#starting-and-stopping-mesh-observation)</span></span>

> [!WARNING]
> <span data-ttu-id="1ce1a-171">*L'impostazione dell'opzione* Di visualizzazione *su Nessuno* **NON arresta** l'esecuzione dell'osservatore.</span><span class="sxs-lookup"><span data-stu-id="1ce1a-171">Setting *Display Option* to *None* does **NOT** stop the observer from running.</span></span> <span data-ttu-id="1ce1a-172">Se si desidera arrestare tutti gli osservatori, le applicazioni dovranno sospendere tutti gli osservatori tramite [`CoreServices.SpatialAwareness.SuspendObservers()`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessSystem.SuspendObservers)</span><span class="sxs-lookup"><span data-stu-id="1ce1a-172">If you wish to stop all observers, applications will need to suspend all observers via [`CoreServices.SpatialAwareness.SuspendObservers()`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessSystem.SuspendObservers)</span></span>

<span data-ttu-id="1ce1a-173">**Materiale visibile**</span><span class="sxs-lookup"><span data-stu-id="1ce1a-173">**Visible Material**</span></span>

<span data-ttu-id="1ce1a-174">Indica il materiale da usare per la visualizzazione della mesh spaziale.</span><span class="sxs-lookup"><span data-stu-id="1ce1a-174">Indicates the material to be used when visualizing the spatial mesh.</span></span>

<span data-ttu-id="1ce1a-175">**Materiale di occlusione**</span><span class="sxs-lookup"><span data-stu-id="1ce1a-175">**Occlusion Material**</span></span>

<span data-ttu-id="1ce1a-176">Indica il materiale da usare per fare in modo che la mesh spaziale ocluda gli ologrammi.</span><span class="sxs-lookup"><span data-stu-id="1ce1a-176">Indicates the material to be used to cause the spatial mesh to occlude holograms.</span></span>

## <a name="see-also"></a><span data-ttu-id="1ce1a-177">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="1ce1a-177">See also</span></span>

* [<span data-ttu-id="1ce1a-178">Sistema di consapevolezza spaziale</span><span class="sxs-lookup"><span data-stu-id="1ce1a-178">Spatial Awareness System</span></span>](spatial-awareness-getting-started.md)
* [<span data-ttu-id="1ce1a-179">Configurazione del sistema di riconoscimento spaziale tramite codice</span><span class="sxs-lookup"><span data-stu-id="1ce1a-179">Configuring Spatial Awareness system via Code</span></span>](usage-guide.md)
* [<span data-ttu-id="1ce1a-180">Documentazione dell'API IMixedRealitySpatialAwarenessObserver</span><span class="sxs-lookup"><span data-stu-id="1ce1a-180">IMixedRealitySpatialAwarenessObserver API documentation</span></span>](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver)
* [<span data-ttu-id="1ce1a-181">Documentazione dell'API IMixedRealitySpatialAwarenessMeshObserver</span><span class="sxs-lookup"><span data-stu-id="1ce1a-181">IMixedRealitySpatialAwarenessMeshObserver API documentation</span></span>](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessMeshObserver)
* [<span data-ttu-id="1ce1a-182">Documentazione dell'API BaseSpatialObserver</span><span class="sxs-lookup"><span data-stu-id="1ce1a-182">BaseSpatialObserver API documentation</span></span>](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.BaseSpatialObserver)

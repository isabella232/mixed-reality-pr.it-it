---
title: Informazioni sulla scena
description: descrive Scene Understanding in MRTK
author: MaxWang-MS
ms.author: wangmax
ms.date: 03/02/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, Scene Understanding
ms.openlocfilehash: ac90359a71267dc64e659f446f35ec2510c42599
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143884"
---
# <a name="scene-understanding"></a><span data-ttu-id="774fd-104">Informazioni sulla scena</span><span class="sxs-lookup"><span data-stu-id="774fd-104">Scene Understanding</span></span>

<span data-ttu-id="774fd-105">[Scene Understanding](/windows/mixed-reality/scene-understanding) restituisce una rappresentazione semantica delle entità della scena e delle relative forme geometriche __in__ HoloLens 2 (HoloLens di prima generazione non è supportato).</span><span class="sxs-lookup"><span data-stu-id="774fd-105">[Scene Understanding](/windows/mixed-reality/scene-understanding) returns a semantic representation of scene entities as well as their geometric forms on __HoloLens 2__ (HoloLens 1st Gen is not supported).</span></span>

<span data-ttu-id="774fd-106">Di seguito sono riportati alcuni casi d'uso previsti di questa tecnologia:</span><span class="sxs-lookup"><span data-stu-id="774fd-106">Some expected use cases of this technology are:</span></span>
* <span data-ttu-id="774fd-107">Posizionare gli oggetti sulla superficie più vicina di un determinato tipo (ad esempio, le pareti e il piano)</span><span class="sxs-lookup"><span data-stu-id="774fd-107">Place objects on nearest surface of a certain kind (e.g. wall and floor)</span></span>
* <span data-ttu-id="774fd-108">Costruire la mesh di spostamento per i giochi in stile piattaforma</span><span class="sxs-lookup"><span data-stu-id="774fd-108">Construct nav-mesh for platform style games</span></span>
* <span data-ttu-id="774fd-109">Fornire la geometria descrittiva del motore di fisica come quad</span><span class="sxs-lookup"><span data-stu-id="774fd-109">Provide physics engine friendly geometry as quads</span></span>
* <span data-ttu-id="774fd-110">Accelerare lo sviluppo evitando la necessità di scrivere algoritmi simili</span><span class="sxs-lookup"><span data-stu-id="774fd-110">Accelerate development by avoiding the need to write similar algorithms</span></span>

<span data-ttu-id="774fd-111">Scene Understanding è disponibile come funzionalità __sperimentale__ a partire da MRTK 2.6.</span><span class="sxs-lookup"><span data-stu-id="774fd-111">Scene Understanding is available as an __experimental__ feature starting from MRTK 2.6.</span></span> <span data-ttu-id="774fd-112">È integrato in MRTK come [osservatore spaziale](spatial-awareness-getting-started.md#register-observers) denominato [`WindowsSceneUnderstandingObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsSceneUnderstanding.Experimental.WindowsSceneUnderstandingObserver) .</span><span class="sxs-lookup"><span data-stu-id="774fd-112">It is integrated into MRTK as a [spatial observer](spatial-awareness-getting-started.md#register-observers) called [`WindowsSceneUnderstandingObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsSceneUnderstanding.Experimental.WindowsSceneUnderstandingObserver).</span></span> <span data-ttu-id="774fd-113">Scene Understanding funziona sia con la pipeline XR legacy che con la pipeline XR SDK.</span><span class="sxs-lookup"><span data-stu-id="774fd-113">Scene Understanding works both with the Legacy XR pipeline and the XR SDK pipeline.</span></span> <span data-ttu-id="774fd-114">In entrambi i casi `WindowsSceneUnderstandingObserver` viene usato .</span><span class="sxs-lookup"><span data-stu-id="774fd-114">In both cases the `WindowsSceneUnderstandingObserver` is used.</span></span>

## <a name="observer-overview"></a><span data-ttu-id="774fd-115">Panoramica dell'osservatore</span><span class="sxs-lookup"><span data-stu-id="774fd-115">Observer overview</span></span>

<span data-ttu-id="774fd-116">Quando richiesto, [`WindowsSceneUnderstandingObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsSceneUnderstanding.Experimental.WindowsSceneUnderstandingObserver) restituirà [SpatialAwarenessSceneObject](xref:Microsoft.MixedReality.Toolkit.Experimental.SpatialAwareness.SpatialAwarenessSceneObject) con attributi utili per l'applicazione per comprendere l'ambiente circostante.</span><span class="sxs-lookup"><span data-stu-id="774fd-116">When asked, the [`WindowsSceneUnderstandingObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsSceneUnderstanding.Experimental.WindowsSceneUnderstandingObserver) will return [SpatialAwarenessSceneObject](xref:Microsoft.MixedReality.Toolkit.Experimental.SpatialAwareness.SpatialAwarenessSceneObject) with attributes useful for the application to understand its surroundings.</span></span> <span data-ttu-id="774fd-117">La frequenza di osservazione, il tipo di oggetto restituito (ad esempio, le pareti, il piano) e altri comportamenti dell'osservatore dipendono dalla configurazione dell'osservatore tramite il profilo.</span><span class="sxs-lookup"><span data-stu-id="774fd-117">The observation frequency, returned object type (e.g. wall, floor) and other observer behaviors are dependent on the configuration of the observer via profile.</span></span> <span data-ttu-id="774fd-118">Ad esempio, se si desidera la maschera di occlusione, l'osservatore deve essere configurato per generare quad.</span><span class="sxs-lookup"><span data-stu-id="774fd-118">For instance, if the occlusion mask is desired the observer must be configured to generate quads.</span></span> <span data-ttu-id="774fd-119">La scena osservata può essere salvata come file serializzato che può essere caricato in un secondo momento per ricreare la scena in modalità di riproduzione dell'editor.</span><span class="sxs-lookup"><span data-stu-id="774fd-119">The observed scene can be saved as serialized file that can be later loaded to recreate the scene in editor play mode.</span></span>

## <a name="setup"></a><span data-ttu-id="774fd-120">Eseguire la configurazione</span><span class="sxs-lookup"><span data-stu-id="774fd-120">Setup</span></span>

> [!IMPORTANT]
> <span data-ttu-id="774fd-121">Scene Understanding è supportato solo in HoloLens 2 e Unity 2019.4 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="774fd-121">Scene Understanding is only supported on HoloLens 2 and Unity 2019.4 and higher.</span></span>

1. <span data-ttu-id="774fd-122">Verificare che la piattaforma sia impostata su UWP nelle impostazioni di compilazione.</span><span class="sxs-lookup"><span data-stu-id="774fd-122">Ensure the platform is set to UWP in build settings.</span></span>
1. <span data-ttu-id="774fd-123">Acquisire il pacchetto Scene Understanding tramite [lo strumento di funzionalità di realtà mista](https://aka.ms/MRFeatureTool).</span><span class="sxs-lookup"><span data-stu-id="774fd-123">Acquire the Scene Understanding package via [Mixed Reality Feature Tool](https://aka.ms/MRFeatureTool).</span></span>

## <a name="using-scene-understanding"></a><span data-ttu-id="774fd-124">Uso di Scene Understanding</span><span class="sxs-lookup"><span data-stu-id="774fd-124">Using Scene Understanding</span></span>

<span data-ttu-id="774fd-125">Il modo più rapido per iniziare a usare Scene Understanding è vedere la scena di esempio.</span><span class="sxs-lookup"><span data-stu-id="774fd-125">The quickest way to get started with Scene Understanding is to check out the sample scene.</span></span>

### <a name="scene-understanding-sample-scene"></a><span data-ttu-id="774fd-126">Scena di esempio scene Understanding</span><span class="sxs-lookup"><span data-stu-id="774fd-126">Scene Understanding sample scene</span></span>

<span data-ttu-id="774fd-127">In Unity usare Project Explorer (Esplora progetti) per aprire il file della scena in `Examples/Experimental/SceneUnderstanding/Scenes/SceneUnderstandingExample.unity` e premere play!</span><span class="sxs-lookup"><span data-stu-id="774fd-127">In Unity, use the Project Explorer to open the scene file in `Examples/Experimental/SceneUnderstanding/Scenes/SceneUnderstandingExample.unity` and press play!</span></span>

> [!IMPORTANT]
> <span data-ttu-id="774fd-128">Quando si usa lo strumento di funzionalità di realtà mista o si esegue un'importazione tramite UPM, importare l'esempio Demos - SpatialAwareness prima di importare l'esempio Experimental - SceneUnderstanding a causa di un problema di dipendenza.</span><span class="sxs-lookup"><span data-stu-id="774fd-128">When using the Mixed Reality Feature Tool or otherwise importing via UPM, please import the Demos - SpatialAwareness sample before importing the Experimental - SceneUnderstanding sample due to a dependency issue.</span></span> <span data-ttu-id="774fd-129">Per altre informazioni, vedere questo problema di [GitHub.](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9431)</span><span class="sxs-lookup"><span data-stu-id="774fd-129">Please see [this GitHub issue](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9431) for more information.</span></span>

<span data-ttu-id="774fd-130">La scena illustra quanto segue:</span><span class="sxs-lookup"><span data-stu-id="774fd-130">The scene demonstrates the following:</span></span>

* <span data-ttu-id="774fd-131">Visualizzazione degli oggetti scena osservati con nell'interfaccia utente dell'applicazione per la configurazione dell'osservatore</span><span class="sxs-lookup"><span data-stu-id="774fd-131">Visualization of observed Scene Objects with in application UI for configuring the observer</span></span>
* <span data-ttu-id="774fd-132">Script `DemoSceneUnderstandingController` di esempio che illustra come modificare le impostazioni dell'osservatore e restare in ascolto degli eventi pertinenti</span><span class="sxs-lookup"><span data-stu-id="774fd-132">Example `DemoSceneUnderstandingController` script that shows how to change observer settings and listen to relevant events</span></span>
* <span data-ttu-id="774fd-133">Salvataggio dei dati della scena nel dispositivo per lo sviluppo offline</span><span class="sxs-lookup"><span data-stu-id="774fd-133">Saving scene data to device for offline development</span></span>
* <span data-ttu-id="774fd-134">Caricamento dei dati della scena salvati in precedenza (file con estensione bytes) per supportare il flusso di lavoro di sviluppo nell'editor</span><span class="sxs-lookup"><span data-stu-id="774fd-134">Loading previously saved scene data (.bytes files) to support in-editor development workflow</span></span>

> [!NOTE] 
> <span data-ttu-id="774fd-135">La scena di esempio è basata sulla pipeline XR legacy.</span><span class="sxs-lookup"><span data-stu-id="774fd-135">The sample scene is based on the Legacy XR pipeline.</span></span> <span data-ttu-id="774fd-136">Se si usa la pipeline XR SDK, è necessario modificare i profili di conseguenza.</span><span class="sxs-lookup"><span data-stu-id="774fd-136">If you are using the XR SDK pipeline you should modify the profiles accordingly.</span></span> <span data-ttu-id="774fd-137">Il profilo scene Understanding Spatial Awareness System ( ) e `DemoSceneUnderstandingSystemProfile` i profili Scene Understanding Observer ( e ) funzionano per `DefaultSceneUnderstandingObserverProfile` `DemoSceneUnderstandingObserverProfile` entrambe le pipeline.</span><span class="sxs-lookup"><span data-stu-id="774fd-137">The provided Scene Understanding Spatial Awareness System profile (`DemoSceneUnderstandingSystemProfile`) and the Scene Understanding Observer profiles (`DefaultSceneUnderstandingObserverProfile` and `DemoSceneUnderstandingObserverProfile`) works for both pipelines.</span></span>

#### <a name="configuring-the-observer-service"></a><span data-ttu-id="774fd-138">Configurazione del servizio observer</span><span class="sxs-lookup"><span data-stu-id="774fd-138">Configuring the observer service</span></span>

<span data-ttu-id="774fd-139">Selezionare l'oggetto gioco "MixedRealityToolkit" e controllare il controllo.</span><span class="sxs-lookup"><span data-stu-id="774fd-139">Select the 'MixedRealityToolkit' game object and check the inspector.</span></span>

![comprensione della posizione della scena nella gerarchia](../images/spatial-awareness/MRTKHierarchy.png)

![Posizione di MRTK in Inspector](../images/spatial-awareness/MRTKLocation.png)

<span data-ttu-id="774fd-142">Queste opzioni consentiranno a un utente di configurare `WindowsSceneUnderstandingObserver` .</span><span class="sxs-lookup"><span data-stu-id="774fd-142">These options will allow one to configure the `WindowsSceneUnderstandingObserver`.</span></span>

### <a name="example-script"></a><span data-ttu-id="774fd-143">Script di esempio</span><span class="sxs-lookup"><span data-stu-id="774fd-143">Example script</span></span>

<span data-ttu-id="774fd-144">Lo script di _esempio DemoSceneUnderstandingController.cs_ illustra i concetti principali relativi all'uso del servizio Scene Understanding.</span><span class="sxs-lookup"><span data-stu-id="774fd-144">The example script _DemoSceneUnderstandingController.cs_ demonstrates the major concepts in working with the Scene Understanding service.</span></span>

* <span data-ttu-id="774fd-145">Sottoscrizione di eventi scene understanding</span><span class="sxs-lookup"><span data-stu-id="774fd-145">Subscribing to Scene Understanding events</span></span>
* <span data-ttu-id="774fd-146">Gestione degli eventi di comprensione della scena</span><span class="sxs-lookup"><span data-stu-id="774fd-146">Handling Scene Understanding events</span></span>
* <span data-ttu-id="774fd-147">Configurazione di in `WindowsSceneUnderstandingObserver` fase di esecuzione</span><span class="sxs-lookup"><span data-stu-id="774fd-147">Configuring the `WindowsSceneUnderstandingObserver` at runtime</span></span>

<span data-ttu-id="774fd-148">Gli interruttori sul pannello nella scena modificano il comportamento dell'osservatore di comprensione della scena chiamando le funzioni pubbliche di questo script di esempio.</span><span class="sxs-lookup"><span data-stu-id="774fd-148">The toggles on the panel in the scene change the behavior of scene understanding observer by calling public functions of this sample script.</span></span>

<span data-ttu-id="774fd-149">L'attivazione di Instantiate Prefabs (Crea istanze di *prefab)* illustra la creazione di oggetti che si adattano a tutti [gli spatialAwarenessSceneObject,](xref:Microsoft.MixedReality.Toolkit.Experimental.SpatialAwareness.SpatialAwarenessSceneObject)raccolti in modo accurato in un oggetto padre.</span><span class="sxs-lookup"><span data-stu-id="774fd-149">Turning on *Instantiate Prefabs*, will demonstrate creating objects that size to fit themselves to all [SpatialAwarenessSceneObject](xref:Microsoft.MixedReality.Toolkit.Experimental.SpatialAwareness.SpatialAwarenessSceneObject), gathered neatly under a parent object.</span></span>

![opzioni del controller demo](../images/spatial-awareness/Controller.png)

### <a name="built-app-notes"></a><span data-ttu-id="774fd-151">Note sull'app compilata</span><span class="sxs-lookup"><span data-stu-id="774fd-151">Built app notes</span></span>

<span data-ttu-id="774fd-152">Compilare e distribuire in HoloLens in modo standard.</span><span class="sxs-lookup"><span data-stu-id="774fd-152">Build and deploy to HoloLens in the standard way.</span></span> <span data-ttu-id="774fd-153">Dopo l'esecuzione, dovrebbe apparire una serie di pulsanti per la riproduzione con le funzionalità.</span><span class="sxs-lookup"><span data-stu-id="774fd-153">Once running, a number of buttons should appear to play with the features.</span></span>

<span data-ttu-id="774fd-154">Si noti che esistono alcuni problemi nell'esecuzione di query all'osservatore.</span><span class="sxs-lookup"><span data-stu-id="774fd-154">Note, their are some pit falls in making queries to the observer.</span></span> <span data-ttu-id="774fd-155">Una configurazione errata di una richiesta di recupero ha come risultato il payload dell'evento che non contiene i dati previsti.</span><span class="sxs-lookup"><span data-stu-id="774fd-155">Misconfiguration of a fetch request result in your event payload not containing the expected data.</span></span> <span data-ttu-id="774fd-156">Ad esempio, se non si richiedono quad, non saranno presenti trame maschera di occlusione.</span><span class="sxs-lookup"><span data-stu-id="774fd-156">For example, if one doesn't request quads, then no occlusion mask textures will be present.</span></span> <span data-ttu-id="774fd-157">Analogamente, non verrà visualizzata alcuna mesh mondiale se l'osservatore non è configurato per richiedere mesh.</span><span class="sxs-lookup"><span data-stu-id="774fd-157">Like wise, no world mesh will appear if the observer is not configured to request meshes.</span></span> <span data-ttu-id="774fd-158">Lo `DemoSceneUnderstandingController` script si occupa di alcune di queste dipendenze, ma non di tutte.</span><span class="sxs-lookup"><span data-stu-id="774fd-158">The `DemoSceneUnderstandingController` script takes care of some of these dependencies, but not all.</span></span>

<span data-ttu-id="774fd-159">I file di scena salvati sono accessibili tramite il [portale dei dispositivi all'indirizzo](/windows/mixed-reality/using-the-windows-device-portal) `User Folders/LocalAppData/[APP_NAME]/LocalState/PREFIX_yyyyMMdd_hhmmss.bytes` .</span><span class="sxs-lookup"><span data-stu-id="774fd-159">Saved scene files can be accessed through the [device portal](/windows/mixed-reality/using-the-windows-device-portal) at `User Folders/LocalAppData/[APP_NAME]/LocalState/PREFIX_yyyyMMdd_hhmmss.bytes`.</span></span> <span data-ttu-id="774fd-160">Questi file di scena possono essere usati nell'editor specificandoli nel profilo osservatore trovato nel controllo.</span><span class="sxs-lookup"><span data-stu-id="774fd-160">These scene files can be used in editor by specifying them in the observer profile found in the inspector.</span></span>

![Portale di dispositivi percorso del file di byte](../images/spatial-awareness/BytesInDevicePortal.png)

![Byte della scena serializzati nell'osservatore](../images/spatial-awareness/BytesLocationInObserver.png)

## <a name="see-also"></a><span data-ttu-id="774fd-163">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="774fd-163">See Also</span></span>

* [<span data-ttu-id="774fd-164">Panoramica del mapping spaziale WMR</span><span class="sxs-lookup"><span data-stu-id="774fd-164">Spatial Mapping Overview WMR</span></span>](/windows/mixed-reality/scene-understanding)
* [<span data-ttu-id="774fd-165">Panoramica del mapping spaziale WMR</span><span class="sxs-lookup"><span data-stu-id="774fd-165">Spatial Mapping Overview WMR</span></span>](/windows/mixed-reality/scene-understanding-sdk)
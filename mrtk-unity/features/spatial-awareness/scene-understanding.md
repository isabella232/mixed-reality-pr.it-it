---
title: SceneUnderstanding
description: descrive la comprensione della scena in MRTK
author: MaxWang-MS
ms.author: wangmax
ms.date: 03/02/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, comprensione della scena
ms.openlocfilehash: c8f82de2418b199220261fbae034acb3e5640362
ms.sourcegitcommit: 7a8fa3257a13635ddad77d963e49440f62c19774
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/04/2021
ms.locfileid: "101884062"
---
# <a name="scene-understanding"></a><span data-ttu-id="6698c-104">Comprensione della scena</span><span class="sxs-lookup"><span data-stu-id="6698c-104">Scene Understanding</span></span>

<span data-ttu-id="6698c-105">La [comprensione della scena](https://docs.microsoft.com/windows/mixed-reality/scene-understanding) restituisce una rappresentazione semantica delle entità della scena, oltre ai moduli geometrici in __HoloLens 2__ (HoloLens 1st Gen non è supportata).</span><span class="sxs-lookup"><span data-stu-id="6698c-105">[Scene Understanding](https://docs.microsoft.com/windows/mixed-reality/scene-understanding) returns a semantic representation of scene entities as well as their geometric forms on __HoloLens 2__ (HoloLens 1st Gen is not supported).</span></span>

<span data-ttu-id="6698c-106">Alcuni casi d'uso previsti di questa tecnologia sono:</span><span class="sxs-lookup"><span data-stu-id="6698c-106">Some expected use cases of this technology are:</span></span>
* <span data-ttu-id="6698c-107">Posizionare oggetti sulla superficie più vicina di un determinato tipo (ad esempio, Wall e floor)</span><span class="sxs-lookup"><span data-stu-id="6698c-107">Place objects on nearest surface of a certain kind (e.g. wall and floor)</span></span>
* <span data-ttu-id="6698c-108">Costruisci NAV-mesh per giochi in stile piattaforma</span><span class="sxs-lookup"><span data-stu-id="6698c-108">Construct nav-mesh for platform style games</span></span>
* <span data-ttu-id="6698c-109">Fornire la geometria intuitiva del motore di fisica come Quad</span><span class="sxs-lookup"><span data-stu-id="6698c-109">Provide physics engine friendly geometry as quads</span></span>
* <span data-ttu-id="6698c-110">Accelera lo sviluppo evitando la necessità di scrivere algoritmi simili</span><span class="sxs-lookup"><span data-stu-id="6698c-110">Accelerate development by avoiding the need to write similar algorithms</span></span>

<span data-ttu-id="6698c-111">La comprensione della scena è disponibile come funzionalità __sperimentale__ a partire da MRTK 2,6.</span><span class="sxs-lookup"><span data-stu-id="6698c-111">Scene Understanding is available as an __experimental__ feature starting from MRTK 2.6.</span></span> <span data-ttu-id="6698c-112">È integrato in MRTK come [osservatore spaziale](spatial-awareness-getting-started.md#register-observers) chiamato [`WindowsSceneUnderstandingObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsSceneUnderstanding.Experimental.WindowsSceneUnderstandingObserver) .</span><span class="sxs-lookup"><span data-stu-id="6698c-112">It is integrated into MRTK as a [spatial observer](spatial-awareness-getting-started.md#register-observers) called [`WindowsSceneUnderstandingObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsSceneUnderstanding.Experimental.WindowsSceneUnderstandingObserver).</span></span> <span data-ttu-id="6698c-113">La comprensione delle scene funziona sia con la pipeline XR legacy che con la pipeline SDK XR.</span><span class="sxs-lookup"><span data-stu-id="6698c-113">Scene Understanding works both with the Legacy XR pipeline and the XR SDK pipeline.</span></span> <span data-ttu-id="6698c-114">In entrambi i casi `WindowsSceneUnderstandingObserver` viene usato.</span><span class="sxs-lookup"><span data-stu-id="6698c-114">In both cases the `WindowsSceneUnderstandingObserver` is used.</span></span>

## <a name="observer-overview"></a><span data-ttu-id="6698c-115">Panoramica di Observer</span><span class="sxs-lookup"><span data-stu-id="6698c-115">Observer overview</span></span>

<span data-ttu-id="6698c-116">Quando viene richiesto, [`WindowsSceneUnderstandingObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsSceneUnderstanding.Experimental.WindowsSceneUnderstandingObserver) restituirà [SpatialAwarenessSceneObject](xref:Microsoft.MixedReality.Toolkit.Experimental.SpatialAwareness.SpatialAwarenessSceneObject) con attributi utili per l'applicazione per comprenderne l'ambiente.</span><span class="sxs-lookup"><span data-stu-id="6698c-116">When asked, the [`WindowsSceneUnderstandingObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsSceneUnderstanding.Experimental.WindowsSceneUnderstandingObserver) will return [SpatialAwarenessSceneObject](xref:Microsoft.MixedReality.Toolkit.Experimental.SpatialAwareness.SpatialAwarenessSceneObject) with attributes useful for the application to understand its surroundings.</span></span> <span data-ttu-id="6698c-117">La frequenza di osservazione, il tipo di oggetto restituito (ad esempio, Wall, floor) e altri comportamenti osservatore dipendono dalla configurazione dell'Observer tramite il profilo.</span><span class="sxs-lookup"><span data-stu-id="6698c-117">The observation frequency, returned object type (e.g. wall, floor) and other observer behaviors are dependent on the configuration of the observer via profile.</span></span> <span data-ttu-id="6698c-118">Ad esempio, se si desidera la maschera di occlusione, è necessario configurare Observer per generare quad.</span><span class="sxs-lookup"><span data-stu-id="6698c-118">For instance, if the occlusion mask is desired the observer must be configured to generate quads.</span></span> <span data-ttu-id="6698c-119">La scena osservata può essere salvata come file serializzato che è possibile caricare in un secondo momento per ricreare la scena in modalità di riproduzione dell'editor.</span><span class="sxs-lookup"><span data-stu-id="6698c-119">The observed scene can be saved as serialized file that can be later loaded to recreate the scene in editor play mode.</span></span>

## <a name="setup"></a><span data-ttu-id="6698c-120">Configurazione</span><span class="sxs-lookup"><span data-stu-id="6698c-120">Setup</span></span>

1. <span data-ttu-id="6698c-121">Verificare che la piattaforma sia impostata su UWP nelle impostazioni di compilazione.</span><span class="sxs-lookup"><span data-stu-id="6698c-121">Ensure the platform is set to UWP in build settings.</span></span>
1. <span data-ttu-id="6698c-122">Acquisire la scena informazioni sul pacchetto tramite [lo strumento funzionalità di realtà mista](https://aka.ms/MRFeatureTool).</span><span class="sxs-lookup"><span data-stu-id="6698c-122">Acquire the Scene Understanding package via [Mixed Reality Feature Tool](https://aka.ms/MRFeatureTool).</span></span>

## <a name="using-scene-understanding"></a><span data-ttu-id="6698c-123">Uso della comprensione della scena</span><span class="sxs-lookup"><span data-stu-id="6698c-123">Using Scene Understanding</span></span>

<span data-ttu-id="6698c-124">Il modo più rapido per iniziare a comprendere la scena è vedere la scena di esempio.</span><span class="sxs-lookup"><span data-stu-id="6698c-124">The quickest way to get started with Scene Understanding is to check out the sample scene.</span></span>

### <a name="scene-understanding-sample-scene"></a><span data-ttu-id="6698c-125">Scena di esempio per la comprensione della scena</span><span class="sxs-lookup"><span data-stu-id="6698c-125">Scene Understanding sample scene</span></span>

<span data-ttu-id="6698c-126">In Unity usare Esplora progetti per aprire il file della scena in `Examples/Experimental/SceneUnderstanding/Scenes/SceneUnderstandingExample.unity` e premere Play.</span><span class="sxs-lookup"><span data-stu-id="6698c-126">In Unity, use the Project Explorer to open the scene file in `Examples/Experimental/SceneUnderstanding/Scenes/SceneUnderstandingExample.unity` and press play!</span></span>

<span data-ttu-id="6698c-127">La scena mostra quanto segue:</span><span class="sxs-lookup"><span data-stu-id="6698c-127">The scene demonstrates the following:</span></span>

* <span data-ttu-id="6698c-128">Visualizzazione degli oggetti scena osservati con nell'interfaccia utente dell'applicazione per la configurazione dell'Observer</span><span class="sxs-lookup"><span data-stu-id="6698c-128">Visualization of observed Scene Objects with in application UI for configuring the observer</span></span>
* <span data-ttu-id="6698c-129">Script di esempio `DemoSceneUnderstandingController` che illustra come modificare le impostazioni di Observer e ascoltare gli eventi rilevanti</span><span class="sxs-lookup"><span data-stu-id="6698c-129">Example `DemoSceneUnderstandingController` script that shows how to change observer settings and listen to relevant events</span></span>
* <span data-ttu-id="6698c-130">Salvataggio dei dati della scena nel dispositivo per lo sviluppo offline</span><span class="sxs-lookup"><span data-stu-id="6698c-130">Saving scene data to device for offline development</span></span>
* <span data-ttu-id="6698c-131">Caricamento dei dati della scena salvati in precedenza (file con estensione byte) per supportare il flusso di lavoro di sviluppo in-Editor</span><span class="sxs-lookup"><span data-stu-id="6698c-131">Loading previously saved scene data (.bytes files) to support in-editor development workflow</span></span>

> [!NOTE] 
> <span data-ttu-id="6698c-132">La scena di esempio è basata sulla pipeline XR legacy.</span><span class="sxs-lookup"><span data-stu-id="6698c-132">The sample scene is based on the Legacy XR pipeline.</span></span> <span data-ttu-id="6698c-133">Se si usa la pipeline di XR SDK è necessario modificare i profili di conseguenza.</span><span class="sxs-lookup"><span data-stu-id="6698c-133">If you are using the XR SDK pipeline you should modify the profiles accordingly.</span></span> <span data-ttu-id="6698c-134">La scena fornita informazioni sul profilo del sistema di riconoscimento spaziale ( `DemoSceneUnderstandingSystemProfile` ) e la scena informazioni sui profili Observer ( `DefaultSceneUnderstandingObserverProfile` e `DemoSceneUnderstandingObserverProfile` ) funzionano per entrambe le pipeline.</span><span class="sxs-lookup"><span data-stu-id="6698c-134">The provided Scene Understanding Spatial Awareness System profile (`DemoSceneUnderstandingSystemProfile`) and the Scene Understanding Observer profiles (`DefaultSceneUnderstandingObserverProfile` and `DemoSceneUnderstandingObserverProfile`) works for both pipelines.</span></span>

#### <a name="configuring-the-observer-service"></a><span data-ttu-id="6698c-135">Configurazione del servizio Observer</span><span class="sxs-lookup"><span data-stu-id="6698c-135">Configuring the observer service</span></span>

<span data-ttu-id="6698c-136">Selezionare l'oggetto del gioco ' MixedRealityToolkit ' e controllare il controllo.</span><span class="sxs-lookup"><span data-stu-id="6698c-136">Select the 'MixedRealityToolkit' game object and check the inspector.</span></span>

![posizione di comprensione della scena in gerarchia](../images/spatial-awareness/MRTKHierarchy.png)

![posizione MRKT in Inspector](../images/spatial-awareness/MRTKLocation.png)

<span data-ttu-id="6698c-139">Queste opzioni consentiranno di configurare il `WindowsSceneUnderstandingObserver` .</span><span class="sxs-lookup"><span data-stu-id="6698c-139">These options will allow one to configure the `WindowsSceneUnderstandingObserver`.</span></span>

### <a name="example-script"></a><span data-ttu-id="6698c-140">Script di esempio</span><span class="sxs-lookup"><span data-stu-id="6698c-140">Example script</span></span>

<span data-ttu-id="6698c-141">Lo script di esempio _DemoSceneUnderstandingController.cs_ illustra i principali concetti relativi all'uso del servizio di informazioni sulla scena.</span><span class="sxs-lookup"><span data-stu-id="6698c-141">The example script _DemoSceneUnderstandingController.cs_ demonstrates the major concepts in working with the Scene Understanding service.</span></span>

* <span data-ttu-id="6698c-142">Sottoscrizione degli eventi di comprensione della scena</span><span class="sxs-lookup"><span data-stu-id="6698c-142">Subscribing to Scene Understanding events</span></span>
* <span data-ttu-id="6698c-143">Gestione degli eventi di comprensione della scena</span><span class="sxs-lookup"><span data-stu-id="6698c-143">Handling Scene Understanding events</span></span>
* <span data-ttu-id="6698c-144">Configurazione `WindowsSceneUnderstandingObserver` di in fase di esecuzione</span><span class="sxs-lookup"><span data-stu-id="6698c-144">Configuring the `WindowsSceneUnderstandingObserver` at runtime</span></span>

<span data-ttu-id="6698c-145">Gli interruttori sul pannello nella scena modificano il comportamento dell'osservatore della scena, chiamando le funzioni pubbliche di questo script di esempio.</span><span class="sxs-lookup"><span data-stu-id="6698c-145">The toggles on the panel in the scene change the behavior of scene understanding observer by calling public functions of this sample script.</span></span>

<span data-ttu-id="6698c-146">Quando si attiva la creazione di *un'istanza* dei predicati, viene illustrata la creazione di oggetti che si adattano a tutti [SpatialAwarenessSceneObject](xref:Microsoft.MixedReality.Toolkit.Experimental.SpatialAwareness.SpatialAwarenessSceneObject), raccolti in modo accurato in un oggetto padre.</span><span class="sxs-lookup"><span data-stu-id="6698c-146">Turning on *Instantiate Prefabs*, will demonstrate creating objects that size to fit themselves to all [SpatialAwarenessSceneObject](xref:Microsoft.MixedReality.Toolkit.Experimental.SpatialAwareness.SpatialAwarenessSceneObject), gathered neatly under a parent object.</span></span>

![opzioni del controller demo](../images/spatial-awareness/Controller.png)

### <a name="built-app-notes"></a><span data-ttu-id="6698c-148">Note app compilate</span><span class="sxs-lookup"><span data-stu-id="6698c-148">Built app notes</span></span>

<span data-ttu-id="6698c-149">Compilare e distribuire in HoloLens in modo standard.</span><span class="sxs-lookup"><span data-stu-id="6698c-149">Build and deploy to HoloLens in the standard way.</span></span> <span data-ttu-id="6698c-150">Una volta eseguito, è necessario che venga visualizzato un numero di pulsanti per riprodurre le funzionalità.</span><span class="sxs-lookup"><span data-stu-id="6698c-150">Once running, a number of buttons should appear to play with the features.</span></span>

<span data-ttu-id="6698c-151">Si noti che sono presenti alcune cadute nell'esecuzione di query nell'Observer.</span><span class="sxs-lookup"><span data-stu-id="6698c-151">Note, their are some pit falls in making queries to the observer.</span></span> <span data-ttu-id="6698c-152">La configurazione errata di una richiesta di recupero genera il payload dell'evento che non contiene i dati previsti.</span><span class="sxs-lookup"><span data-stu-id="6698c-152">Misconfiguration of a fetch request result in your event payload not containing the expected data.</span></span> <span data-ttu-id="6698c-153">Se, ad esempio, un doesnt richiede quad, non saranno presenti trame della maschera di occlusione.</span><span class="sxs-lookup"><span data-stu-id="6698c-153">For example, if one dosen't request quads, then no occlusion mask textures will be present.</span></span> <span data-ttu-id="6698c-154">Analogamente, non verrà visualizzata alcuna mesh mondiale se l'Observer non è configurato per richiedere mesh.</span><span class="sxs-lookup"><span data-stu-id="6698c-154">Like wise, no world mesh will appear if the observer is not configured to request meshes.</span></span> <span data-ttu-id="6698c-155">Lo `DemoSceneUnderstandingController` script si occupa di alcune di queste dipendenze, ma non di tutte.</span><span class="sxs-lookup"><span data-stu-id="6698c-155">The `DemoSceneUnderstandingController` script takes care of some of these dependencies, but not all.</span></span>

<span data-ttu-id="6698c-156">È possibile accedere ai file di scena salvati tramite il [portale del dispositivo](https://docs.microsoft.com/windows/mixed-reality/using-the-windows-device-portal) all'indirizzo `User Folders/LocalAppData/[APP_NAME]/LocalState/PREFIX_yyyyMMdd_hhmmss.bytes` .</span><span class="sxs-lookup"><span data-stu-id="6698c-156">Saved scene files can be accessed through the [device portal](https://docs.microsoft.com/windows/mixed-reality/using-the-windows-device-portal) at `User Folders/LocalAppData/[APP_NAME]/LocalState/PREFIX_yyyyMMdd_hhmmss.bytes`.</span></span> <span data-ttu-id="6698c-157">Questi file di scena possono essere usati nell'editor specificando tali file nel profilo Observer trovato nel controllo.</span><span class="sxs-lookup"><span data-stu-id="6698c-157">These scene files can be used in editor by specifying them in the observer profile found in the inspector.</span></span>

![Percorso del file di byte del portale del dispositivo](../images/spatial-awareness/BytesInDevicePortal.png)

![Byte della scena serializzati nell'Observer](../images/spatial-awareness/BytesLocationInObserver.png)

## <a name="see-also"></a><span data-ttu-id="6698c-160">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="6698c-160">See Also</span></span>

* https://docs.microsoft.com/windows/mixed-reality/scene-understanding
* https://docs.microsoft.com/windows/mixed-reality/scene-understanding-sdk

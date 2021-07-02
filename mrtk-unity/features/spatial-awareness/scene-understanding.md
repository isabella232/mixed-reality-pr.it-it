---
title: Osservatore di comprensione della scena
description: descrive La comprensione della scena in MRTK
author: MaxWang-MS
ms.author: wangmax
ms.date: 05/27/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, comprensione della scena
ms.openlocfilehash: d5430e7885055a550347c4ccebc1452f68125922
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176231"
---
# <a name="scene-understanding-observer"></a><span data-ttu-id="62756-104">Osservatore di comprensione della scena</span><span class="sxs-lookup"><span data-stu-id="62756-104">Scene understanding observer</span></span>

<span data-ttu-id="62756-105">[La comprensione della](/windows/mixed-reality/scene-understanding) scena restituisce una rappresentazione semantica delle entità della scena e delle __relative__ forme geometriche HoloLens 2 (HoloLens prima generazione non è supportata).</span><span class="sxs-lookup"><span data-stu-id="62756-105">[Scene Understanding](/windows/mixed-reality/scene-understanding) returns a semantic representation of scene entities as well as their geometric forms on __HoloLens 2__ (HoloLens 1st Gen is not supported).</span></span>

<span data-ttu-id="62756-106">Alcuni casi d'uso previsti di questa tecnologia sono:</span><span class="sxs-lookup"><span data-stu-id="62756-106">Some expected use cases of this technology are:</span></span>
* <span data-ttu-id="62756-107">Posizionare gli oggetti sulla superficie più vicina di un certo tipo (ad esempio, parete e pavimento)</span><span class="sxs-lookup"><span data-stu-id="62756-107">Place objects on nearest surface of a certain kind (e.g. wall and floor)</span></span>
* <span data-ttu-id="62756-108">Costruire una rete di navigazione per giochi in stile piattaforma</span><span class="sxs-lookup"><span data-stu-id="62756-108">Construct nav-mesh for platform style games</span></span>
* <span data-ttu-id="62756-109">Fornire la geometria descrittiva del motore di fisica come quad</span><span class="sxs-lookup"><span data-stu-id="62756-109">Provide physics engine friendly geometry as quads</span></span>
* <span data-ttu-id="62756-110">Accelerare lo sviluppo evitando la necessità di scrivere algoritmi simili</span><span class="sxs-lookup"><span data-stu-id="62756-110">Accelerate development by avoiding the need to write similar algorithms</span></span>

<span data-ttu-id="62756-111">Scene Understanding è stata introdotta come __funzionalità sperimentale__ in MRTK 2.6.</span><span class="sxs-lookup"><span data-stu-id="62756-111">Scene Understanding is introduced as an __experimental__ feature in MRTK 2.6.</span></span> <span data-ttu-id="62756-112">È integrato in MRTK come [osservatore spaziale](spatial-awareness-getting-started.md#register-observers) denominato [`WindowsSceneUnderstandingObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsSceneUnderstanding.Experimental.WindowsSceneUnderstandingObserver) .</span><span class="sxs-lookup"><span data-stu-id="62756-112">It is integrated into MRTK as a [spatial observer](spatial-awareness-getting-started.md#register-observers) called [`WindowsSceneUnderstandingObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsSceneUnderstanding.Experimental.WindowsSceneUnderstandingObserver).</span></span> <span data-ttu-id="62756-113">Scene Understanding funziona sia con la pipeline XR legacy che con la pipeline XR SDK (sia OpenXR (a partire da MRTK 2.7) che con il plug-in XR Windows XR).</span><span class="sxs-lookup"><span data-stu-id="62756-113">Scene Understanding works both with the Legacy XR pipeline and the XR SDK pipeline (both OpenXR (starting from MRTK 2.7) and Windows XR Plugin).</span></span> <span data-ttu-id="62756-114">In entrambi i casi viene `WindowsSceneUnderstandingObserver` usato .</span><span class="sxs-lookup"><span data-stu-id="62756-114">In both cases the `WindowsSceneUnderstandingObserver` is used.</span></span>

> [!NOTE] 
> <span data-ttu-id="62756-115">L'uso di Scene Understanding nella comunicazione remota non è supportato.</span><span class="sxs-lookup"><span data-stu-id="62756-115">Using Scene Understanding in Remoting is not supported.</span></span>

## <a name="observer-overview"></a><span data-ttu-id="62756-116">Panoramica dell'osservatore</span><span class="sxs-lookup"><span data-stu-id="62756-116">Observer overview</span></span>

<span data-ttu-id="62756-117">Quando richiesto, [`WindowsSceneUnderstandingObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsSceneUnderstanding.Experimental.WindowsSceneUnderstandingObserver) restituirà [SpatialAwarenessSceneObject](xref:Microsoft.MixedReality.Toolkit.Experimental.SpatialAwareness.SpatialAwarenessSceneObject) con attributi utili per l'applicazione per comprenderne l'ambiente circostante.</span><span class="sxs-lookup"><span data-stu-id="62756-117">When asked, the [`WindowsSceneUnderstandingObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsSceneUnderstanding.Experimental.WindowsSceneUnderstandingObserver) will return [SpatialAwarenessSceneObject](xref:Microsoft.MixedReality.Toolkit.Experimental.SpatialAwareness.SpatialAwarenessSceneObject) with attributes useful for the application to understand its surroundings.</span></span> <span data-ttu-id="62756-118">La frequenza di osservazione, il tipo di oggetto restituito (ad esempio parete, pavimento) e altri comportamenti dell'osservatore dipendono dalla configurazione dell'osservatore tramite profilo.</span><span class="sxs-lookup"><span data-stu-id="62756-118">The observation frequency, returned object type (e.g. wall, floor) and other observer behaviors are dependent on the configuration of the observer via profile.</span></span> <span data-ttu-id="62756-119">Ad esempio, se si desidera utilizzare la maschera di occlusione, l'osservatore deve essere configurato per generare quad.</span><span class="sxs-lookup"><span data-stu-id="62756-119">For instance, if the occlusion mask is desired the observer must be configured to generate quads.</span></span> <span data-ttu-id="62756-120">La scena osservata può essere salvata come file serializzato che può essere caricato in un secondo momento per ricreare la scena in modalità di riproduzione dell'editor.</span><span class="sxs-lookup"><span data-stu-id="62756-120">The observed scene can be saved as serialized file that can be later loaded to recreate the scene in editor play mode.</span></span>

## <a name="setup"></a><span data-ttu-id="62756-121">Configurazione</span><span class="sxs-lookup"><span data-stu-id="62756-121">Setup</span></span>

> [!IMPORTANT]
> <span data-ttu-id="62756-122">Scene Understanding è supportato solo in HoloLens 2 e Unity 2019.4 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="62756-122">Scene Understanding is only supported on HoloLens 2 and Unity 2019.4 and higher.</span></span>

1. <span data-ttu-id="62756-123">Assicurarsi che la piattaforma sia impostata su UWP nelle impostazioni di compilazione.</span><span class="sxs-lookup"><span data-stu-id="62756-123">Ensure the platform is set to UWP in build settings.</span></span>
1. <span data-ttu-id="62756-124">Acquisire il pacchetto Scene Understanding tramite Lo strumento [di funzionalità di realtà mista](https://aka.ms/MRFeatureTool).</span><span class="sxs-lookup"><span data-stu-id="62756-124">Acquire the Scene Understanding package via [Mixed Reality Feature Tool](https://aka.ms/MRFeatureTool).</span></span>

## <a name="using-scene-understanding"></a><span data-ttu-id="62756-125">Uso della comprensione della scena</span><span class="sxs-lookup"><span data-stu-id="62756-125">Using Scene Understanding</span></span>

<span data-ttu-id="62756-126">Il modo più rapido per iniziare a usare Scene Understanding è quello di controllare la scena di esempio.</span><span class="sxs-lookup"><span data-stu-id="62756-126">The quickest way to get started with Scene Understanding is to check out the sample scene.</span></span>

### <a name="scene-understanding-sample-scene"></a><span data-ttu-id="62756-127">Scena di esempio Di comprensione della scena</span><span class="sxs-lookup"><span data-stu-id="62756-127">Scene Understanding sample scene</span></span>

<span data-ttu-id="62756-128">In Unity usare il Project Explorer per aprire il file di scena in `Examples/Experimental/SceneUnderstanding/Scenes/SceneUnderstandingExample.unity` e premere play!</span><span class="sxs-lookup"><span data-stu-id="62756-128">In Unity, use the Project Explorer to open the scene file in `Examples/Experimental/SceneUnderstanding/Scenes/SceneUnderstandingExample.unity` and press play!</span></span>

::: moniker range="< mrtkunity-2021-05"
> [!IMPORTANT]
> <span data-ttu-id="62756-129">Si applica solo a MRTK 2.6.0: quando si usa lo strumento di funzionalità di realtà mista o in caso contrario si esegue l'importazione tramite UPM, importare l'esempio Demos - SpatialAwareness prima di importare l'esempio Experimental - SceneUnderstanding a causa di un problema di dipendenza.</span><span class="sxs-lookup"><span data-stu-id="62756-129">Only applies to MRTK 2.6.0 - When using the Mixed Reality Feature Tool or otherwise importing via UPM, please import the Demos - SpatialAwareness sample before importing the Experimental - SceneUnderstanding sample due to a dependency issue.</span></span> <span data-ttu-id="62756-130">Per altre [informazioni, GitHub questo](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9431) problema.</span><span class="sxs-lookup"><span data-stu-id="62756-130">Please see [this GitHub issue](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/9431) for more information.</span></span>

::: moniker-end
<span data-ttu-id="62756-131">La scena illustra quanto segue:</span><span class="sxs-lookup"><span data-stu-id="62756-131">The scene demonstrates the following:</span></span>

* <span data-ttu-id="62756-132">Visualizzazione degli oggetti scena osservati con nell'interfaccia utente dell'applicazione per la configurazione dell'osservatore</span><span class="sxs-lookup"><span data-stu-id="62756-132">Visualization of observed Scene Objects with in application UI for configuring the observer</span></span>
* <span data-ttu-id="62756-133">Script `DemoSceneUnderstandingController` di esempio che illustra come modificare le impostazioni dell'osservatore e restare in ascolto di eventi pertinenti</span><span class="sxs-lookup"><span data-stu-id="62756-133">Example `DemoSceneUnderstandingController` script that shows how to change observer settings and listen to relevant events</span></span>
* <span data-ttu-id="62756-134">Salvataggio dei dati della scena nel dispositivo per lo sviluppo offline</span><span class="sxs-lookup"><span data-stu-id="62756-134">Saving scene data to device for offline development</span></span>
* <span data-ttu-id="62756-135">Caricamento dei dati della scena salvati in precedenza (file con estensione bytes) per supportare il flusso di lavoro di sviluppo nell'editor</span><span class="sxs-lookup"><span data-stu-id="62756-135">Loading previously saved scene data (.bytes files) to support in-editor development workflow</span></span>

> [!IMPORTANT]
> <span data-ttu-id="62756-136">Per impostazione `ShouldLoadFromFile` predefinita, la proprietà dell'osservatore è impostata su false.</span><span class="sxs-lookup"><span data-stu-id="62756-136">By default the `ShouldLoadFromFile` property of the observer is set to false.</span></span> <span data-ttu-id="62756-137">Per visualizzare la visualizzazione di una stanza di esempio [](#configuring-the-observer-service) serializzata, vedere la sezione configurazione del servizio osservatore riportata di seguito e impostare la proprietà su true nell'editor.</span><span class="sxs-lookup"><span data-stu-id="62756-137">In order to see the visualization of a serialized sample room, please refer to the [configuring observer service](#configuring-the-observer-service) section below and set the property to true in the editor.</span></span>
::: moniker range="< mrtkunity-2021-05"

> [!NOTE] 
> <span data-ttu-id="62756-138">La scena di esempio è basata sulla pipeline XR legacy.</span><span class="sxs-lookup"><span data-stu-id="62756-138">The sample scene is based on the Legacy XR pipeline.</span></span> <span data-ttu-id="62756-139">Se si usa la pipeline di XR SDK, è necessario modificare i profili di conseguenza.</span><span class="sxs-lookup"><span data-stu-id="62756-139">If you are using the XR SDK pipeline you should modify the profiles accordingly.</span></span> <span data-ttu-id="62756-140">Il profilo di sistema Scene Understanding Spatial Awareness System ( ) e `DemoSceneUnderstandingSystemProfile` i profili scene Understanding Observer ( e ) funzionano per `DefaultSceneUnderstandingObserverProfile` `DemoSceneUnderstandingObserverProfile` entrambe le pipeline.</span><span class="sxs-lookup"><span data-stu-id="62756-140">The provided Scene Understanding Spatial Awareness System profile (`DemoSceneUnderstandingSystemProfile`) and the Scene Understanding Observer profiles (`DefaultSceneUnderstandingObserverProfile` and `DemoSceneUnderstandingObserverProfile`) works for both pipelines.</span></span>
::: moniker-end
::: moniker range="= mrtkunity-2021-05"

> [!NOTE] 
> <span data-ttu-id="62756-141">La scena di esempio registra un `There is no active AsyncCoroutineRunner when an action is posted.` avviso in determinate circostanze a causa dell'ordine di inizializzazione/esecuzione del thread.</span><span class="sxs-lookup"><span data-stu-id="62756-141">The sample scene logs a `There is no active AsyncCoroutineRunner when an action is posted.` warning under certain circumstance due to the initialization/thread execution order.</span></span> <span data-ttu-id="62756-142">Se è possibile verificare che il componente sia collegato al GameObject "Demo Controller" e che il `AsyncCoroutineRunner` componente/GameObject rimanga abilitato/attivo nella scena (caso predefinito), l'avviso può essere ignorato in tutta sicurezza.</span><span class="sxs-lookup"><span data-stu-id="62756-142">If you can confirm the `AsyncCoroutineRunner` component is attached to the "Demo Controller" GameObject and the component/GameObject stay enabled/active in the scene (the default case), the warning can be safely ignored.</span></span> <span data-ttu-id="62756-143">**Tuttavia, quando si crea una nuova scena con Scene Understanding, assicurarsi di creare un GameObject vuoto nella radice e associare lo script, in caso contrario La comprensione della scena potrebbe non `AsyncCoroutineRunner` funzionare correttamente.**</span><span class="sxs-lookup"><span data-stu-id="62756-143">**However, when creating a new scene with Scene Understanding please make sure to create an empty GameObject at root and attach the `AsyncCoroutineRunner` script to it, otherwise Scene Understanding may not function properly.**</span></span>
::: moniker-end

#### <a name="configuring-the-observer-service"></a><span data-ttu-id="62756-144">Configurazione del servizio observer</span><span class="sxs-lookup"><span data-stu-id="62756-144">Configuring the observer service</span></span>

<span data-ttu-id="62756-145">Selezionare l'oggetto gioco "MixedRealityToolkit" e controllare il controllo.</span><span class="sxs-lookup"><span data-stu-id="62756-145">Select the 'MixedRealityToolkit' game object and check the inspector.</span></span>

![Informazioni sulla scena sulla posizione nella gerarchia](../images/spatial-awareness/MRTKHierarchy.png)

![Posizione MRTK nel controllo](../images/spatial-awareness/MRTKLocation.png)

<span data-ttu-id="62756-148">Queste opzioni consentono di configurare `WindowsSceneUnderstandingObserver` .</span><span class="sxs-lookup"><span data-stu-id="62756-148">These options will allow one to configure the `WindowsSceneUnderstandingObserver`.</span></span>

### <a name="example-script"></a><span data-ttu-id="62756-149">Script di esempio</span><span class="sxs-lookup"><span data-stu-id="62756-149">Example script</span></span>

<span data-ttu-id="62756-150">Lo script di esempio _DemoSceneUnderstandingController.cs_ illustra i concetti principali relativi all'uso del servizio Scene Understanding.</span><span class="sxs-lookup"><span data-stu-id="62756-150">The example script _DemoSceneUnderstandingController.cs_ demonstrates the major concepts in working with the Scene Understanding service.</span></span>

* <span data-ttu-id="62756-151">Sottoscrizione agli eventi di Scene Understanding</span><span class="sxs-lookup"><span data-stu-id="62756-151">Subscribing to Scene Understanding events</span></span>
* <span data-ttu-id="62756-152">Gestione degli eventi di comprensione della scena</span><span class="sxs-lookup"><span data-stu-id="62756-152">Handling Scene Understanding events</span></span>
* <span data-ttu-id="62756-153">Configurazione di in `WindowsSceneUnderstandingObserver` fase di esecuzione</span><span class="sxs-lookup"><span data-stu-id="62756-153">Configuring the `WindowsSceneUnderstandingObserver` at runtime</span></span>

<span data-ttu-id="62756-154">Gli interruttori sul pannello nella scena modificano il comportamento dell'osservatore di comprensione della scena chiamando le funzioni pubbliche di questo script di esempio.</span><span class="sxs-lookup"><span data-stu-id="62756-154">The toggles on the panel in the scene change the behavior of scene understanding observer by calling public functions of this sample script.</span></span>

<span data-ttu-id="62756-155">Attivando *Instantiate Prefabs*, verrà illustrata la creazione di oggetti che si adattano a tutti [Gli oggetti SpatialAwarenessSceneObject,](xref:Microsoft.MixedReality.Toolkit.Experimental.SpatialAwareness.SpatialAwarenessSceneObject)raccolti in modo ordinato in un oggetto padre.</span><span class="sxs-lookup"><span data-stu-id="62756-155">Turning on *Instantiate Prefabs*, will demonstrate creating objects that size to fit themselves to all [SpatialAwarenessSceneObject](xref:Microsoft.MixedReality.Toolkit.Experimental.SpatialAwareness.SpatialAwarenessSceneObject), gathered neatly under a parent object.</span></span>

![opzioni del controller demo](../images/spatial-awareness/Controller.png)

### <a name="built-app-notes"></a><span data-ttu-id="62756-157">Note sull'app compilate</span><span class="sxs-lookup"><span data-stu-id="62756-157">Built app notes</span></span>

<span data-ttu-id="62756-158">Compilare e distribuire in HoloLens nel modo standard.</span><span class="sxs-lookup"><span data-stu-id="62756-158">Build and deploy to HoloLens in the standard way.</span></span> <span data-ttu-id="62756-159">Dopo l'esecuzione, dovrebbe essere visualizzato un certo numero di pulsanti da riprodurre con le funzionalità.</span><span class="sxs-lookup"><span data-stu-id="62756-159">Once running, a number of buttons should appear to play with the features.</span></span>

<span data-ttu-id="62756-160">Si noti che esistono alcuni problemi di esecuzione di query all'osservatore.</span><span class="sxs-lookup"><span data-stu-id="62756-160">Note, their are some pit falls in making queries to the observer.</span></span> <span data-ttu-id="62756-161">Errore di configurazione di una richiesta di recupero nel payload dell'evento che non contiene i dati previsti.</span><span class="sxs-lookup"><span data-stu-id="62756-161">Misconfiguration of a fetch request result in your event payload not containing the expected data.</span></span> <span data-ttu-id="62756-162">Ad esempio, se non si richiede quad, non saranno presenti trame di maschera di occlusione.</span><span class="sxs-lookup"><span data-stu-id="62756-162">For example, if one doesn't request quads, then no occlusion mask textures will be present.</span></span> <span data-ttu-id="62756-163">Analogamente, non verrà visualizzata alcuna mesh mondiale se l'osservatore non è configurato per richiedere mesh.</span><span class="sxs-lookup"><span data-stu-id="62756-163">Like wise, no world mesh will appear if the observer is not configured to request meshes.</span></span> <span data-ttu-id="62756-164">Lo `DemoSceneUnderstandingController` script si occupa di alcune di queste dipendenze, ma non di tutte.</span><span class="sxs-lookup"><span data-stu-id="62756-164">The `DemoSceneUnderstandingController` script takes care of some of these dependencies, but not all.</span></span>

<span data-ttu-id="62756-165">È possibile accedere ai file di scena salvati tramite il [portale dei dispositivi](/windows/mixed-reality/using-the-windows-device-portal) all'indirizzo `User Folders/LocalAppData/[APP_NAME]/LocalState/PREFIX_yyyyMMdd_hhmmss.bytes` .</span><span class="sxs-lookup"><span data-stu-id="62756-165">Saved scene files can be accessed through the [device portal](/windows/mixed-reality/using-the-windows-device-portal) at `User Folders/LocalAppData/[APP_NAME]/LocalState/PREFIX_yyyyMMdd_hhmmss.bytes`.</span></span> <span data-ttu-id="62756-166">Questi file di scena possono essere usati nell'editor specificandoli nel profilo osservatore disponibile nel controllo.</span><span class="sxs-lookup"><span data-stu-id="62756-166">These scene files can be used in editor by specifying them in the observer profile found in the inspector.</span></span>

![Portale di dispositivi percorso del file di byte](../images/spatial-awareness/BytesInDevicePortal.png)

![Byte della scena serializzati nell'osservatore](../images/spatial-awareness/BytesLocationInObserver.png)

## <a name="see-also"></a><span data-ttu-id="62756-169">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="62756-169">See Also</span></span>

* [<span data-ttu-id="62756-170">Panoramica della comprensione della scena</span><span class="sxs-lookup"><span data-stu-id="62756-170">Scene Understanding Overview</span></span>](/windows/mixed-reality/scene-understanding)
* [<span data-ttu-id="62756-171">Panoramica di Scene Understanding SDK</span><span class="sxs-lookup"><span data-stu-id="62756-171">Scene Understanding SDK Overview</span></span>](/windows/mixed-reality/scene-understanding-sdk)

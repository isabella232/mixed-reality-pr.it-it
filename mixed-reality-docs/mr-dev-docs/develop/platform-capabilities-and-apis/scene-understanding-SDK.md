---
title: SDK di comprensione della scena
description: Informazioni su come installare e usare Scene Understanding SDK, inclusi componenti, mesh e oggetti nelle app di realtà mista.
author: szymons
ms.author: szymons
ms.date: 12/14/2020
ms.topic: article
keywords: Comprensione della scena, mapping spaziale, Windows Mixed Reality, Unity
ms.openlocfilehash: dee561e49a9457aa35c44037f4573caaefd00f2a
ms.sourcegitcommit: 86fafb3a7ac6a5f60340ae5041619e488223f4f0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/22/2021
ms.locfileid: "112449730"
---
# <a name="scene-understanding-sdk-overview"></a><span data-ttu-id="bde8b-104">Panoramica dell'SDK per la comprensione della scena</span><span class="sxs-lookup"><span data-stu-id="bde8b-104">Scene understanding SDK overview</span></span>

<span data-ttu-id="bde8b-105">La comprensione della scena trasforma i dati del sensore dell'ambiente non strutturato che il dispositivo di realtà mista acquisisce e converte in una potente rappresentazione astratta.</span><span class="sxs-lookup"><span data-stu-id="bde8b-105">Scene understanding transforms the unstructured environment sensor data that your Mixed Reality device captures and converts it into a powerful abstract representation.</span></span> <span data-ttu-id="bde8b-106">L'SDK funge da livello di comunicazione tra l'applicazione e il runtime scene understanding.</span><span class="sxs-lookup"><span data-stu-id="bde8b-106">The SDK acts as the communication layer between your application and the Scene Understanding runtime.</span></span> <span data-ttu-id="bde8b-107">Ha lo scopo di simulare costrutti standard esistenti, ad esempio grafici di scena 3D per rappresentazioni 3D, rettangoli e pannelli 2D per applicazioni 2D.</span><span class="sxs-lookup"><span data-stu-id="bde8b-107">It's aimed to mimic existing standard constructs, such as 3D scene graphs for 3D representations, and 2D rectangles and panels for 2D applications.</span></span> <span data-ttu-id="bde8b-108">Anche se i costrutti di simulare Scene Understanding verranno mappati a framework concreti, in generale SceneUnderstanding è indipendente dal framework che consente l'interoperabilità tra diversi framework che interagiscono con esso.</span><span class="sxs-lookup"><span data-stu-id="bde8b-108">While the constructs Scene Understanding mimics will map to concrete frameworks, in general SceneUnderstanding is framework agnostic allowing for interoperability between varied frameworks that interact with it.</span></span> <span data-ttu-id="bde8b-109">Con l'evolversi della comprensione della scena, il ruolo dell'SDK è garantire che le nuove rappresentazioni e funzionalità continuino a essere esposte in un framework unificato.</span><span class="sxs-lookup"><span data-stu-id="bde8b-109">As Scene Understanding evolves the role of the SDK is to ensure new representations and capabilities continue to be exposed within a unified framework.</span></span> <span data-ttu-id="bde8b-110">In questo documento verranno presentati prima concetti di alto livello che consentono di acquisire familiarità con l'ambiente di sviluppo/utilizzo e quindi fornire una documentazione più dettagliata per classi e costrutti specifici.</span><span class="sxs-lookup"><span data-stu-id="bde8b-110">In this document, we will first introduce high-level concepts that will help you get familiar with the development environment/usage and then provide more detailed documentation for specific classes and constructs.</span></span>

## <a name="where-do-i-get-the-sdk"></a><span data-ttu-id="bde8b-111">Dove si ottiene l'SDK?</span><span class="sxs-lookup"><span data-stu-id="bde8b-111">Where do I get the SDK?</span></span>

<span data-ttu-id="bde8b-112">SceneUnderstanding SDK è scaricabile tramite lo strumento [di funzionalità di realtà mista](../unity/welcome-to-mr-feature-tool.md).</span><span class="sxs-lookup"><span data-stu-id="bde8b-112">The SceneUnderstanding SDK is downloadable via the [Mixed Reality Feature Tool](../unity/welcome-to-mr-feature-tool.md).</span></span>

<span data-ttu-id="bde8b-113">**Nota:** la versione più recente dipende dai pacchetti di anteprima ed è necessario abilitare i pacchetti non definitiva per visualizzarlo.</span><span class="sxs-lookup"><span data-stu-id="bde8b-113">**Note:** the latest release depends on preview packages and you'll need to enable pre-release packages to see it.</span></span>

<span data-ttu-id="bde8b-114">Per la versione 0.5.2022-rc e successive, Scene Understanding supporta le proiezioni del linguaggio per C# e C++ consentendo alle applicazioni di sviluppare applicazioni per piattaforme Win32 o UWP.</span><span class="sxs-lookup"><span data-stu-id="bde8b-114">For version 0.5.2022-rc and later, Scene Understanding supports language projections for C# and C++ allowing applications to develop applications for Win32 or UWP platforms.</span></span> <span data-ttu-id="bde8b-115">A causa di questa versione, SceneUnderstanding supporta il supporto di unity nell'editor, che consente di usare SceneObserver solo per la comunicazione con HoloLens2.</span><span class="sxs-lookup"><span data-stu-id="bde8b-115">As of this version, SceneUnderstanding supports unity in-editor support barring the SceneObserver, which is used solely for communicating with HoloLens2.</span></span> 

<span data-ttu-id="bde8b-116">SceneUnderstanding richiede Windows SDK versione 18362 o successiva.</span><span class="sxs-lookup"><span data-stu-id="bde8b-116">SceneUnderstanding requires Windows SDK version 18362 or higher.</span></span> 

## <a name="conceptual-overview"></a><span data-ttu-id="bde8b-117">Panoramica dei concetti</span><span class="sxs-lookup"><span data-stu-id="bde8b-117">Conceptual Overview</span></span>

### <a name="the-scene"></a><span data-ttu-id="bde8b-118">Scena</span><span class="sxs-lookup"><span data-stu-id="bde8b-118">The Scene</span></span>

<span data-ttu-id="bde8b-119">Il dispositivo di realtà mista integra costantemente le informazioni relative a ciò che vede nell'ambiente.</span><span class="sxs-lookup"><span data-stu-id="bde8b-119">Your mixed reality device is constantly integrating information about what it sees in your environment.</span></span> <span data-ttu-id="bde8b-120">Scene Understanding incanala tutte queste origini dati e produce un'unica astrazione coesiva.</span><span class="sxs-lookup"><span data-stu-id="bde8b-120">Scene Understanding funnels all of these data sources and produces one single cohesive abstraction.</span></span> <span data-ttu-id="bde8b-121">La comprensione della scena genera scene, che sono una composizione di [SceneObject che](scene-understanding-SDK.md#sceneobjects) rappresentano un'istanza di una singola cosa, ad esempio una parete,un controsoffitto/un piano. Gli oggetti scena stessi sono una composizione di [SceneComponents, che rappresentano parti più granulari che costituiscono questo SceneObject.</span><span class="sxs-lookup"><span data-stu-id="bde8b-121">Scene Understanding generates Scenes, which are a composition of [SceneObjects](scene-understanding-SDK.md#sceneobjects) that represent an instance of a single thing, (for example, a wall/ceiling/floor.) Scene Objects themselves are a composition of [SceneComponents, which represent more granular pieces that make up this SceneObject.</span></span> <span data-ttu-id="bde8b-122">Esempi di componenti sono quad e mesh, ma in futuro potrebbero rappresentare recinti di delimitazione, mesh di collisione, metadati e così via.</span><span class="sxs-lookup"><span data-stu-id="bde8b-122">Examples of components are quads and meshes, but in the future could represent bounding boxes, collision meshes, metadata etc.</span></span>

<span data-ttu-id="bde8b-123">Il processo di conversione dei dati del sensore non elaborato in una scena è un'operazione potenzialmente costosa che potrebbe richiedere secondi per spazi medi (~10x10m) in minuti per spazi di grandi dimensioni (~50x50m) e quindi non è un'operazione calcolata dal dispositivo senza richiesta dell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="bde8b-123">The process of converting the raw sensor data into a Scene is a potentially expensive operation that could take seconds for medium spaces (~10x10m) to minutes for large spaces (~50x50m) and therefore it is not something that is being computed by the device without application request.</span></span> <span data-ttu-id="bde8b-124">La generazione della scena viene invece attivata dall'applicazione su richiesta.</span><span class="sxs-lookup"><span data-stu-id="bde8b-124">Instead, Scene generation is triggered by your application on demand.</span></span> <span data-ttu-id="bde8b-125">La classe SceneObserver include metodi statici che possono calcolare o deserializzare una scena, che è quindi possibile enumerare o interagire.</span><span class="sxs-lookup"><span data-stu-id="bde8b-125">The SceneObserver class has static methods that can Compute or Deserialize a scene, which you can then enumerate/interact with.</span></span> <span data-ttu-id="bde8b-126">L'azione "Calcolo" viene eseguita su richiesta ed eseguita sulla CPU, ma in un processo separato (Mixed Reality Driver).</span><span class="sxs-lookup"><span data-stu-id="bde8b-126">The "Compute" action is executed on-demand and executes on the CPU but in a separate process (the Mixed Reality Driver).</span></span> <span data-ttu-id="bde8b-127">Tuttavia, mentre si esegue il calcolo in un altro processo, i dati della scena risultanti vengono archiviati e gestiti nell'applicazione nell'oggetto Scene.</span><span class="sxs-lookup"><span data-stu-id="bde8b-127">However, while we do compute in another process the resulting Scene data is stored and maintained in your application in the Scene object.</span></span> 

<span data-ttu-id="bde8b-128">Di seguito è riportato un diagramma che illustra questo flusso di processo e mostra esempi di due applicazioni che si interfacciano con il runtime scene understanding.</span><span class="sxs-lookup"><span data-stu-id="bde8b-128">Below is a diagram that illustrates this process flow and shows examples of two applications interfacing with the Scene Understanding runtime.</span></span> 

![Diagramma di processo](images/SU-ProcessFlow.png)

<span data-ttu-id="bde8b-130">Sul lato sinistro è presente un diagramma del runtime di realtà mista, sempre in esecuzione nel proprio processo.</span><span class="sxs-lookup"><span data-stu-id="bde8b-130">On the left-hand side is a diagram of the mixed reality runtime, which is always on and running in its own process.</span></span> <span data-ttu-id="bde8b-131">Questo runtime è responsabile dell'esecuzione del rilevamento dei dispositivi, del mapping spaziale e di altre operazioni utilizzate da Scene Understanding per comprendere e ragionare sul mondo che ti circonda.</span><span class="sxs-lookup"><span data-stu-id="bde8b-131">This runtime is responsible for performing device tracking, spatial mapping, and other operations that Scene Understanding uses to understand and reason about the world around you.</span></span> <span data-ttu-id="bde8b-132">Sul lato destro del diagramma vengono mostrate due applicazioni teoriche che usano La comprensione della scena.</span><span class="sxs-lookup"><span data-stu-id="bde8b-132">On the right side of the diagram, we show two theoretical applications that make use of Scene Understanding.</span></span> <span data-ttu-id="bde8b-133">La prima interfaccia dell'applicazione con MRTK, che usa Scene Understanding SDK internamente, la seconda app calcola e usa due istanze di scena separate.</span><span class="sxs-lookup"><span data-stu-id="bde8b-133">The first application interfaces with MRTK, which uses the Scene Understanding SDK internally, the second app computes and uses two separate scene instances.</span></span> <span data-ttu-id="bde8b-134">Tutte e tre le scene in questo diagramma generano istanze distinte delle scene, il driver non sta tracciando lo stato globale condiviso tra le applicazioni e gli oggetti scena in una scena non vengono trovati in un'altra.</span><span class="sxs-lookup"><span data-stu-id="bde8b-134">All three Scenes in this diagram generate distinct instances of the scenes, the driver isn't tracking global state that is shared between applications and Scene Objects in one scene aren't found in another.</span></span> <span data-ttu-id="bde8b-135">La comprensione della scena fornisce un meccanismo per tenere traccia nel tempo, ma questa operazione viene eseguita usando l'SDK.</span><span class="sxs-lookup"><span data-stu-id="bde8b-135">Scene Understanding does provide a mechanism to track over time, but this is done using the SDK.</span></span> <span data-ttu-id="bde8b-136">Il codice di rilevamento è già in esecuzione nell'SDK nel processo dell'app.</span><span class="sxs-lookup"><span data-stu-id="bde8b-136">Tracking code is already running in the SDK in your app's process.</span></span>

<span data-ttu-id="bde8b-137">Poiché ogni scena archivia i dati nello spazio di memoria dell'applicazione, è possibile presupporre che tutte le funzioni dell'oggetto Scene o i dati interni siano sempre eseguiti nel processo dell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="bde8b-137">Because each Scene stores it's data in your application's memory space, you can assume that all function of the Scene object or it's internal data is always executed in your application's process.</span></span>

### <a name="layout"></a><span data-ttu-id="bde8b-138">Layout</span><span class="sxs-lookup"><span data-stu-id="bde8b-138">Layout</span></span>

<span data-ttu-id="bde8b-139">Per usare Scene Understanding, può essere utile conoscere e comprendere in che modo il runtime rappresenta i componenti in modo logico e fisico.</span><span class="sxs-lookup"><span data-stu-id="bde8b-139">To work with Scene Understanding, it may be valuable to know and understand how the runtime represents components logically and physically.</span></span> <span data-ttu-id="bde8b-140">La scena rappresenta i dati con un layout specifico che è stato scelto per essere semplice, mantenendo una struttura sottostante che è soggetta a soddisfare i requisiti futuri senza la necessità di revisioni importanti.</span><span class="sxs-lookup"><span data-stu-id="bde8b-140">The Scene represents data with a specific layout that was chosen to be simple while maintaining an underlying structure that is pliable to meet future requirements without needing major revisions.</span></span> <span data-ttu-id="bde8b-141">La scena esegue questa operazione archiviando tutti i componenti (blocchi predefiniti per tutti gli oggetti scena) in un elenco semplice e definendo gerarchia e composizione tramite riferimenti in cui componenti specifici fanno riferimento ad altri.</span><span class="sxs-lookup"><span data-stu-id="bde8b-141">The Scene does this by storing all Components (building blocks for all Scene Objects) in a flat list and defining hierarchy and composition through references where specific components reference others.</span></span>

<span data-ttu-id="bde8b-142">Di seguito viene presentato un esempio di struttura sia nella forma flat che nella forma logica.</span><span class="sxs-lookup"><span data-stu-id="bde8b-142">Below we present an example of a structure in both its flat and logical form.</span></span>

<table>
<tr><th><span data-ttu-id="bde8b-143">Layout logico</span><span class="sxs-lookup"><span data-stu-id="bde8b-143">Logical Layout</span></span></th><th><span data-ttu-id="bde8b-144">Layout fisico</span><span class="sxs-lookup"><span data-stu-id="bde8b-144">Physical Layout</span></span></th></tr>
<tr>
<td>
<ul>
  <span data-ttu-id="bde8b-145">Scene</span><span class="sxs-lookup"><span data-stu-id="bde8b-145">Scene</span></span>
  <ul>
  <li><span data-ttu-id="bde8b-146">SceneObject_1</span><span class="sxs-lookup"><span data-stu-id="bde8b-146">SceneObject_1</span></span>
    <ul>
      <li><span data-ttu-id="bde8b-147">SceneMesh_1</span><span class="sxs-lookup"><span data-stu-id="bde8b-147">SceneMesh_1</span></span></li>
      <li><span data-ttu-id="bde8b-148">SceneQuad_1</span><span class="sxs-lookup"><span data-stu-id="bde8b-148">SceneQuad_1</span></span></li>
      <li><span data-ttu-id="bde8b-149">SceneQuad_2</span><span class="sxs-lookup"><span data-stu-id="bde8b-149">SceneQuad_2</span></span></li>
    </ul>
  </li>
  <li><span data-ttu-id="bde8b-150">SceneObject_2</span><span class="sxs-lookup"><span data-stu-id="bde8b-150">SceneObject_2</span></span>
    <ul>
      <li><span data-ttu-id="bde8b-151">SceneQuad_1</span><span class="sxs-lookup"><span data-stu-id="bde8b-151">SceneQuad_1</span></span></li>
      <li><span data-ttu-id="bde8b-152">SceneQuad_3</span><span class="sxs-lookup"><span data-stu-id="bde8b-152">SceneQuad_3</span></span></li>
      </li></ul>
  </li>
  <li><span data-ttu-id="bde8b-153">SceneObject_3</span><span class="sxs-lookup"><span data-stu-id="bde8b-153">SceneObject_3</span></span>
    <ul>
      <li><span data-ttu-id="bde8b-154">SceneMesh_3</span><span class="sxs-lookup"><span data-stu-id="bde8b-154">SceneMesh_3</span></span></li>
    </ul>
  </ul>
</ul>
</td>
<td>
<ul>
  <li><span data-ttu-id="bde8b-155">SceneObject_1</span><span class="sxs-lookup"><span data-stu-id="bde8b-155">SceneObject_1</span></span></li>
  <li><span data-ttu-id="bde8b-156">SceneObject_2</span><span class="sxs-lookup"><span data-stu-id="bde8b-156">SceneObject_2</span></span></li>
  <li><span data-ttu-id="bde8b-157">SceneObject_3</span><span class="sxs-lookup"><span data-stu-id="bde8b-157">SceneObject_3</span></span></li>
  <li><span data-ttu-id="bde8b-158">SceneQuad_1</span><span class="sxs-lookup"><span data-stu-id="bde8b-158">SceneQuad_1</span></span></li>
  <li><span data-ttu-id="bde8b-159">SceneQuad_2</span><span class="sxs-lookup"><span data-stu-id="bde8b-159">SceneQuad_2</span></span></li>
  <li><span data-ttu-id="bde8b-160">SceneQuad_3</span><span class="sxs-lookup"><span data-stu-id="bde8b-160">SceneQuad_3</span></span></li>
  <li><span data-ttu-id="bde8b-161">SceneMesh_1</span><span class="sxs-lookup"><span data-stu-id="bde8b-161">SceneMesh_1</span></span></li>
  <li><span data-ttu-id="bde8b-162">SceneMesh_2</span><span class="sxs-lookup"><span data-stu-id="bde8b-162">SceneMesh_2</span></span></li>
</ul>
</td>
</tr>
</table>

<span data-ttu-id="bde8b-163">Questa figura evidenzia la differenza tra il layout fisico e logico della scena.</span><span class="sxs-lookup"><span data-stu-id="bde8b-163">This illustration highlights the difference between the physical and logical layout of the Scene.</span></span> <span data-ttu-id="bde8b-164">A sinistra è visualizzato il layout gerarchico dei dati visualizzati dall'applicazione durante l'enumerazione della scena.</span><span class="sxs-lookup"><span data-stu-id="bde8b-164">On the left, we see the hierarchical layout of the data that your application sees when enumerating the scene.</span></span> <span data-ttu-id="bde8b-165">A destra si può vedere che la scena è costituita da 12 componenti distinti accessibili singolarmente, se necessario.</span><span class="sxs-lookup"><span data-stu-id="bde8b-165">On the right, we see that the scene is comprised of 12 distinct components that are accessible individually if necessary.</span></span> <span data-ttu-id="bde8b-166">Quando si elabora una nuova scena, si prevede che le applicazioni passino logicamente a questa gerarchia, tuttavia quando si esegue il rilevamento tra gli aggiornamenti della scena, alcune applicazioni potrebbero essere interessate solo a componenti specifici condivisi tra due scene.</span><span class="sxs-lookup"><span data-stu-id="bde8b-166">When processing a new scene, we expect applications to walk this hierarchy logically, however when tracking between scene updates, some applications may only be interested in targeting specific components that are shared between two scenes.</span></span>

## <a name="api-overview"></a><span data-ttu-id="bde8b-167">Panoramica delle API</span><span class="sxs-lookup"><span data-stu-id="bde8b-167">API overview</span></span>

<span data-ttu-id="bde8b-168">La sezione seguente offre una panoramica generale dei costrutti in Informazioni sulla scena.</span><span class="sxs-lookup"><span data-stu-id="bde8b-168">The following section provides a high-level overview of the constructs in Scene Understanding.</span></span> <span data-ttu-id="bde8b-169">La lettura di questa sezione consente di comprendere il modo in cui vengono rappresentate le scene e le attività dei vari componenti.</span><span class="sxs-lookup"><span data-stu-id="bde8b-169">Reading this section will give you an  understanding of how scenes are represented, and what the various components do/are used for.</span></span> <span data-ttu-id="bde8b-170">La sezione successiva fornirà esempi di codice concreti e dettagli aggiuntivi che verranno illustrati in questa panoramica.</span><span class="sxs-lookup"><span data-stu-id="bde8b-170">The next section will provide concrete code examples and additional details that are glossed over in this overview.</span></span>

<span data-ttu-id="bde8b-171">Tutti i tipi descritti di seguito si trovano nello spazio `Microsoft.MixedReality.SceneUnderstanding` dei nomi .</span><span class="sxs-lookup"><span data-stu-id="bde8b-171">All of the types described below reside in the `Microsoft.MixedReality.SceneUnderstanding` namespace.</span></span>

### <a name="scenecomponents"></a><span data-ttu-id="bde8b-172">SceneComponents</span><span class="sxs-lookup"><span data-stu-id="bde8b-172">SceneComponents</span></span>

<span data-ttu-id="bde8b-173">Ora che si comprende il layout logico delle scene, è ora possibile presentare il concetto di SceneComponents e il modo in cui vengono usate per comporre la gerarchia.</span><span class="sxs-lookup"><span data-stu-id="bde8b-173">Now that you understand the logical layout of scenes we can now present the concept of SceneComponents and how they're used to compose hierarchy.</span></span> <span data-ttu-id="bde8b-174">SceneComponents è la scomposizione più granulare in SceneUnderstanding che rappresenta un singolo elemento principale, ad esempio una mesh, un quad o un rettangolo di selezione.</span><span class="sxs-lookup"><span data-stu-id="bde8b-174">SceneComponents are the most granular decompositions in SceneUnderstanding representing a single core thing, for example, a mesh or a quad or a bounding box.</span></span> <span data-ttu-id="bde8b-175">SceneComponents sono elementi che possono essere aggiornati in modo indipendente e possono essere referenziati da altri SceneComponent, quindi hanno una singola proprietà globale un ID univoco, che consentono questo tipo di meccanismo di rilevamento/riferimento.</span><span class="sxs-lookup"><span data-stu-id="bde8b-175">SceneComponents are things that can update independently and can be referenced by other SceneComponents, hence they have a single global property a unique ID, that allow for this type of tracking/referencing mechanism.</span></span> <span data-ttu-id="bde8b-176">Gli ID vengono usati per la composizione logica della gerarchia della scena e per la persistenza degli oggetti (l'atto di aggiornare una scena rispetto a un'altra).</span><span class="sxs-lookup"><span data-stu-id="bde8b-176">Ids are used for the logical composition of scene hierarchy as well as object persistence (the act of updating one scene relative to another.)</span></span> 

<span data-ttu-id="bde8b-177">Se si considera ogni scena appena calcolata come distinta e si semplicemente enumerano tutti i dati al suo interno, gli ID sono in gran parte trasparenti per l'utente.</span><span class="sxs-lookup"><span data-stu-id="bde8b-177">If you're treating every newly computed scene as being distinct, and simply enumerating all data within it then Ids are largely transparent to you.</span></span> <span data-ttu-id="bde8b-178">Tuttavia, se si prevede di tenere traccia dei componenti su diversi aggiornamenti, si useranno gli ID per indicizzare e trovare SceneComponents tra gli oggetti Scene.</span><span class="sxs-lookup"><span data-stu-id="bde8b-178">However, if you're planning to track components over several updates you'll use the Ids to index and find SceneComponents between Scene objects.</span></span>

### <a name="sceneobjects"></a><span data-ttu-id="bde8b-179">SceneObjects</span><span class="sxs-lookup"><span data-stu-id="bde8b-179">SceneObjects</span></span>

<span data-ttu-id="bde8b-180">SceneObject è un oggetto SceneComponent che rappresenta un'istanza di una "cosa", ad esempio una parete, un pavimento, un controsoffitto e così via. espresso dalla proprietà Kind.</span><span class="sxs-lookup"><span data-stu-id="bde8b-180">A SceneObject is a SceneComponent that represents an instance of a "thing" for example, a wall, a floor, a ceiling, etc.... expressed by their Kind property.</span></span> <span data-ttu-id="bde8b-181">Gli oggetti SceneObject sono geometrici e hanno quindi funzioni e proprietà che rappresentano la loro posizione nello spazio, ma non contengono alcuna struttura geometrica o logica.</span><span class="sxs-lookup"><span data-stu-id="bde8b-181">SceneObjects are geometric, and therefore have functions and properties that represent their location in space, however they don't contain any geometric or logical structure.</span></span> <span data-ttu-id="bde8b-182">SceneObjects fa invece riferimento ad altri SceneComponent, in particolare SceneQuads e SceneMeshes, che forniscono le varie rappresentazioni supportate dal sistema.</span><span class="sxs-lookup"><span data-stu-id="bde8b-182">Instead, SceneObjects reference other SceneComponents, specifically SceneQuads, and SceneMeshes, which provide the varied representations that are supported by the system.</span></span> <span data-ttu-id="bde8b-183">Quando viene calcolata una nuova scena, è molto probabile che l'applicazione enumererà gli oggetti SceneObject della scena per elaborare ciò a cui è interessata.</span><span class="sxs-lookup"><span data-stu-id="bde8b-183">When a new scene is computed, your application will most likely enumerate the Scene's SceneObjects to process what it's interested in.</span></span>

<span data-ttu-id="bde8b-184">SceneObjects può avere uno degli elementi seguenti:</span><span class="sxs-lookup"><span data-stu-id="bde8b-184">SceneObjects can have any one of the following:</span></span>

<table>
<tr>
<th><span data-ttu-id="bde8b-185">SceneObjectKind</span><span class="sxs-lookup"><span data-stu-id="bde8b-185">SceneObjectKind</span></span></th> <th><span data-ttu-id="bde8b-186">Descrizione</span><span class="sxs-lookup"><span data-stu-id="bde8b-186">Description</span></span></th>
</tr>
<tr><td><span data-ttu-id="bde8b-187">Sfondo</span><span class="sxs-lookup"><span data-stu-id="bde8b-187">Background</span></span></td><td><span data-ttu-id="bde8b-188">SceneObject è noto per non <b>essere uno</b> degli altri tipi riconosciuti di oggetto scena.</span><span class="sxs-lookup"><span data-stu-id="bde8b-188">The SceneObject is known to be <b>not</b> one of the other recognized kinds of scene object.</span></span> <span data-ttu-id="bde8b-189">Questa classe non deve essere confusa con Unknown, dove Background non è noto per essere wall/floor/ceiling e così via... mentre sconosciuto non è ancora categorizzato.</span><span class="sxs-lookup"><span data-stu-id="bde8b-189">This class shouldn't be confused with Unknown where Background is known not to be wall/floor/ceiling etc.... while unknown isn't yet categorized.</span></span></b></td></tr>
<tr><td><span data-ttu-id="bde8b-190">Parete</span><span class="sxs-lookup"><span data-stu-id="bde8b-190">Wall</span></span></td><td><span data-ttu-id="bde8b-191">Una parete fisica.</span><span class="sxs-lookup"><span data-stu-id="bde8b-191">A physical wall.</span></span> <span data-ttu-id="bde8b-192">Si presuppone che le pareti siano strutture ambientali inamovibili.</span><span class="sxs-lookup"><span data-stu-id="bde8b-192">Walls are assumed to be immovable environmental structures.</span></span></td></tr>
<tr><td><span data-ttu-id="bde8b-193">Piano</span><span class="sxs-lookup"><span data-stu-id="bde8b-193">Floor</span></span></td><td><span data-ttu-id="bde8b-194">I piani sono superfici su cui si può andare a piedi.</span><span class="sxs-lookup"><span data-stu-id="bde8b-194">Floors are any surfaces on which one can walk.</span></span> <span data-ttu-id="bde8b-195">Nota: le scale non sono piani.</span><span class="sxs-lookup"><span data-stu-id="bde8b-195">Note: stairs aren't floors.</span></span> <span data-ttu-id="bde8b-196">Si noti anche che i piani presuppongono qualsiasi superficie a piedi e pertanto non esiste alcun presupposto esplicito di un piano singolare.</span><span class="sxs-lookup"><span data-stu-id="bde8b-196">Also note, that floors assume any walkable surface and therefore there's no explicit assumption of a singular floor.</span></span> <span data-ttu-id="bde8b-197">Strutture a più livelli, rampe e così via... deve essere classificata come floor.</span><span class="sxs-lookup"><span data-stu-id="bde8b-197">Multi-level structures, ramps etc.... should all classify as floor.</span></span></td></tr>
<tr><td><span data-ttu-id="bde8b-198">Ceiling</span><span class="sxs-lookup"><span data-stu-id="bde8b-198">Ceiling</span></span></td><td><span data-ttu-id="bde8b-199">La superficie superiore di una stanza.</span><span class="sxs-lookup"><span data-stu-id="bde8b-199">The upper surface of a room.</span></span></td></tr>
<tr><td><span data-ttu-id="bde8b-200">Piattaforma</span><span class="sxs-lookup"><span data-stu-id="bde8b-200">Platform</span></span></td><td><span data-ttu-id="bde8b-201">Una superficie piana di grandi dimensioni su cui è possibile posizionare gli ologrammi.</span><span class="sxs-lookup"><span data-stu-id="bde8b-201">A large flat surface on which you could place holograms.</span></span> <span data-ttu-id="bde8b-202">In genere rappresentano tabelle, controsoffi e altre superfici orizzontali di grandi dimensioni.</span><span class="sxs-lookup"><span data-stu-id="bde8b-202">These tend to represent tables, countertops, and other large horizontal surfaces.</span></span></td></tr>
<tr><td><span data-ttu-id="bde8b-203">World</span><span class="sxs-lookup"><span data-stu-id="bde8b-203">World</span></span></td><td><span data-ttu-id="bde8b-204">Etichetta riservata per i dati geometrici indipendente dall'etichettatura.</span><span class="sxs-lookup"><span data-stu-id="bde8b-204">A reserved label for geometric data that is agnostic to labeling.</span></span> <span data-ttu-id="bde8b-205">La mesh generata impostando il flag di aggiornamento EnableWorldMesh verrà classificata come world.</span><span class="sxs-lookup"><span data-stu-id="bde8b-205">The mesh generated by setting the EnableWorldMesh update flag would be classified as world.</span></span></td></tr>
<tr><td><span data-ttu-id="bde8b-206">Sconosciuto</span><span class="sxs-lookup"><span data-stu-id="bde8b-206">Unknown</span></span></td><td><span data-ttu-id="bde8b-207">Questo oggetto scena deve ancora essere classificato e assegnato a un tipo.</span><span class="sxs-lookup"><span data-stu-id="bde8b-207">This scene object has yet to be classified and assigned a kind.</span></span> <span data-ttu-id="bde8b-208">Questo non deve essere confuso con Background, poiché questo oggetto potrebbe essere qualsiasi cosa, il sistema non ha ancora creato una classificazione sufficientemente solida per questo oggetto.</span><span class="sxs-lookup"><span data-stu-id="bde8b-208">This shouldn't be confused with Background, as this object could be anything, the system has just not come up with a strong enough classification for it yet.</span></span></td></tr>
</tr>
</table>

### <a name="scenemesh"></a><span data-ttu-id="bde8b-209">SceneMesh</span><span class="sxs-lookup"><span data-stu-id="bde8b-209">SceneMesh</span></span>

<span data-ttu-id="bde8b-210">SceneMesh è un oggetto SceneComponent che approssima la geometria di oggetti geometrici arbitrari usando un elenco di triangoli.</span><span class="sxs-lookup"><span data-stu-id="bde8b-210">A SceneMesh is a SceneComponent that approximates the geometry of arbitrary geometric objects using a triangle list.</span></span> <span data-ttu-id="bde8b-211">SceneMeshes viene usato in diversi contesti, possono rappresentare i componenti della struttura delle celle stagna o come WorldMesh, che rappresenta la mesh di mapping spaziale non associata alla scena.</span><span class="sxs-lookup"><span data-stu-id="bde8b-211">SceneMeshes are used in several different contexts, they can represent components of the watertight cell structure or as the WorldMesh, which represents the unbounded spatial mapping mesh associated with the Scene.</span></span> <span data-ttu-id="bde8b-212">I dati di indice e vertice forniti con ogni mesh utilizzano lo stesso layout familiare dei [buffer](/windows/win32/direct3d9/rendering-from-vertex-and-index-buffers) dei vertici e degli indici usati per il rendering delle mesh triangolare in tutte le API di rendering moderne.</span><span class="sxs-lookup"><span data-stu-id="bde8b-212">The index and vertex data provided with each mesh uses the same familiar layout as the [vertex and index buffers](/windows/win32/direct3d9/rendering-from-vertex-and-index-buffers) that are used for rendering triangle meshes in all modern rendering APIs.</span></span> <span data-ttu-id="bde8b-213">In Scene Understanding le mesh usano indici a 32 bit e potrebbero dover essere suddivise in blocchi per determinati motori di rendering.</span><span class="sxs-lookup"><span data-stu-id="bde8b-213">In Scene Understanding, meshes use 32-bit indices and may need to be broken up into chunks for certain rendering engines.</span></span>

#### <a name="winding-order-and-coordinate-systems"></a><span data-ttu-id="bde8b-214">Ordine di avvolgimento e sistemi di coordinate</span><span class="sxs-lookup"><span data-stu-id="bde8b-214">Winding Order and Coordinate Systems</span></span>

<span data-ttu-id="bde8b-215">Si prevede che tutte le mesh prodotte da Scene Understanding restituiranno mesh in un sistema Right-Handed coordinate usando l'ordine di avvolgimento in senso orario.</span><span class="sxs-lookup"><span data-stu-id="bde8b-215">All meshes produced by Scene Understanding are expected to return meshes in a Right-Handed coordinate system using clockwise winding order.</span></span> 

<span data-ttu-id="bde8b-216">Nota: le compilazioni del sistema operativo precedenti Counter-Clockwise .191105 potrebbero avere un bug noto in cui le mesh "World" venivano restituite in ordine di vento, che è stato successivamente risolto.</span><span class="sxs-lookup"><span data-stu-id="bde8b-216">Note: OS builds prior to .191105 may have a known bug where "World" meshes were returning in Counter-Clockwise winding order, which has subsequently been fixed.</span></span>

### <a name="scenequad"></a><span data-ttu-id="bde8b-217">SceneQuad</span><span class="sxs-lookup"><span data-stu-id="bde8b-217">SceneQuad</span></span>

<span data-ttu-id="bde8b-218">SceneQuad è un oggetto SceneComponent che rappresenta superfici 2D che occupano il mondo 3D.</span><span class="sxs-lookup"><span data-stu-id="bde8b-218">A SceneQuad is a SceneComponent that represents 2d surfaces that occupy the 3d world.</span></span> <span data-ttu-id="bde8b-219">SceneQuads può essere usato in modo analogo a ARKit ARPlaneAnchor o ARCore Planes, ma offrono funzionalità più di alto livello come canvas 2D che possono essere usate da app flat o dall'esperienza utente aumentata.</span><span class="sxs-lookup"><span data-stu-id="bde8b-219">SceneQuads can be used similarly to ARKit ARPlaneAnchor or ARCore Planes but they offer more high-level functionality as 2d canvases to be used by flat apps, or augmented UX.</span></span> <span data-ttu-id="bde8b-220">Sono disponibili API specifiche 2D per quad che rendono il posizionamento e il layout semplici da usare e lo sviluppo (ad eccezione del rendering) con quad dovrebbe essere più simile all'uso di canvas 2D rispetto alle mesh 3D.</span><span class="sxs-lookup"><span data-stu-id="bde8b-220">2D specific APIs are provided for quads that make placement and layout simple to use, and developing (with the exception of rendering) with quads should feel more akin to working with 2d canvases than 3d meshes.</span></span>

#### <a name="scenequad-shape"></a><span data-ttu-id="bde8b-221">Forma SceneQuad</span><span class="sxs-lookup"><span data-stu-id="bde8b-221">SceneQuad shape</span></span>

<span data-ttu-id="bde8b-222">SceneQuads definisce una superficie rettangolare delimitata in 2d.</span><span class="sxs-lookup"><span data-stu-id="bde8b-222">SceneQuads define a bounded rectangular surface in 2d.</span></span> <span data-ttu-id="bde8b-223">SceneQuads rappresenta tuttavia superfici con forme arbitrarie e potenzialmente complesse, ad esempio una tabella a forma di ciambella. Per rappresentare la forma complessa della superficie di un quad, è possibile usare l'API GetSurfaceMask per eseguire il rendering della forma della superficie in un buffer di immagini specificato.</span><span class="sxs-lookup"><span data-stu-id="bde8b-223">However, SceneQuads are representing surfaces with arbitrary and potentially complex shapes (e.g. a donut shaped table.) To represent the complex shape of the surface of a quad you may use the GetSurfaceMask API to render the shape of the surface onto an image buffer you provide.</span></span> <span data-ttu-id="bde8b-224">Se anche l'oggetto SceneObject con il quad ha una mesh, i triangoli della mesh devono essere equivalenti a questa immagine sottoposta a rendering, entrambi rappresentano la geometria reale della superficie, in coordinate 2D o 3D.</span><span class="sxs-lookup"><span data-stu-id="bde8b-224">If the SceneObject that has the quad also has a mesh, the mesh triangles should be equivalent to this rendered image, they both represent real geometry of the surface, either in 2d or 3d coordinates.</span></span>

## <a name="scene-understanding-sdk-details-and-reference"></a><span data-ttu-id="bde8b-225">Informazioni di riferimento e dettagli sull'SDK per la scena</span><span class="sxs-lookup"><span data-stu-id="bde8b-225">Scene understanding SDK details and reference</span></span>

> [!NOTE] 
> <span data-ttu-id="bde8b-226">Quando si usa MRTK, si noti che l'utente interagirà con mrTK e pertanto potrebbe ignorare questa sezione nella maggior [`WindowsSceneUnderstandingObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsSceneUnderstanding.Experimental.WindowsSceneUnderstandingObserver) parte dei casi.</span><span class="sxs-lookup"><span data-stu-id="bde8b-226">When using MRTK, please note you will be interacting with MRTK's [`WindowsSceneUnderstandingObserver`](xref:Microsoft.MixedReality.Toolkit.WindowsSceneUnderstanding.Experimental.WindowsSceneUnderstandingObserver) and thus may skip this section under most circumstances.</span></span> <span data-ttu-id="bde8b-227">Per altre informazioni, vedere la documentazione di [MRTK Scene Understanding.](/windows/mixed-reality/mrtk-unity/features/spatial-awareness/scene-understanding)</span><span class="sxs-lookup"><span data-stu-id="bde8b-227">Please refer to the [MRTK Scene Understanding docs](/windows/mixed-reality/mrtk-unity/features/spatial-awareness/scene-understanding) for more information.</span></span>

<span data-ttu-id="bde8b-228">La sezione seguente consente di acquisire familiarità con le nozioni di base di SceneUnderstanding.</span><span class="sxs-lookup"><span data-stu-id="bde8b-228">The following section will help get you familiar with the basics of SceneUnderstanding.</span></span> <span data-ttu-id="bde8b-229">Questa sezione contiene le nozioni di base, a questo punto è necessario avere un contesto sufficiente per esplorare le applicazioni di esempio per vedere come sceneUnderstanding viene usato in modo olistico.</span><span class="sxs-lookup"><span data-stu-id="bde8b-229">This section should provide you with the basics, at which point you should have enough context to browse through the sample applications to see how SceneUnderstanding is used holistically.</span></span>

### <a name="initialization"></a><span data-ttu-id="bde8b-230">Inizializzazione</span><span class="sxs-lookup"><span data-stu-id="bde8b-230">Initialization</span></span>

<span data-ttu-id="bde8b-231">Il primo passaggio per lavorare con SceneUnderstanding consiste nell'ottenere un riferimento a un oggetto Scene da parte dell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="bde8b-231">The first step to working with SceneUnderstanding is for your application to gain reference to a Scene object.</span></span> <span data-ttu-id="bde8b-232">Questa operazione può essere eseguita in uno dei due modi seguenti: una scena può essere calcolata dal driver o una scena esistente calcolata in passato può essere de serializzata.</span><span class="sxs-lookup"><span data-stu-id="bde8b-232">This can be done in one of two ways, a Scene can either be computed by the driver, or an existing Scene that was computed in the past can be de-serialized.</span></span> <span data-ttu-id="bde8b-233">Quest'ultimo è utile per lavorare con SceneUnderstanding durante lo sviluppo, in cui le applicazioni e le esperienze possono essere prototipate rapidamente senza un dispositivo di realtà mista.</span><span class="sxs-lookup"><span data-stu-id="bde8b-233">The latter is useful for working with SceneUnderstanding during development, where applications and experiences can be prototyped quickly without a mixed reality device.</span></span>

<span data-ttu-id="bde8b-234">Le scene vengono calcolate usando sceneObserver.</span><span class="sxs-lookup"><span data-stu-id="bde8b-234">Scenes are computed using a SceneObserver.</span></span> <span data-ttu-id="bde8b-235">Prima di creare una scena, l'applicazione deve eseguire una query sul dispositivo per assicurarsi che supporti SceneUnderstanding, nonché per richiedere l'accesso utente per le informazioni necessarie a SceneUnderstanding.</span><span class="sxs-lookup"><span data-stu-id="bde8b-235">Before creating a Scene, your application should query your device to ensure that it supports SceneUnderstanding, as well as to request user access for information that SceneUnderstanding needs.</span></span>

```cs
if (!SceneObserver.IsSupported())
{
    // Handle the error
}

// This call should grant the access we need.
await SceneObserver.RequestAccessAsync();
```

<span data-ttu-id="bde8b-236">Se RequestAccessAsync() non viene chiamato, il calcolo di una nuova scena avrà esito negativo.</span><span class="sxs-lookup"><span data-stu-id="bde8b-236">If RequestAccessAsync() is not called, computing a new Scene will fail.</span></span> <span data-ttu-id="bde8b-237">Verrà quindi calcolata una nuova scena basata sul visore VR di realtà mista e con un raggio di 10 metri.</span><span class="sxs-lookup"><span data-stu-id="bde8b-237">Next we will compute a new scene that's rooted around the Mixed Reality headset and has a 10-meter radius.</span></span>

```cs
// Create Query settings for the scene update
SceneQuerySettings querySettings;

querySettings.EnableSceneObjectQuads = true;                                       // Requests that the scene updates quads.
querySettings.EnableSceneObjectMeshes = true;                                      // Requests that the scene updates watertight mesh data.
querySettings.EnableOnlyObservedSceneObjects = false;                              // Do not explicitly turn off quad inference.
querySettings.EnableWorldMesh = true;                                              // Requests a static version of the spatial mapping mesh.
querySettings.RequestedMeshLevelOfDetail = SceneMeshLevelOfDetail.Fine;            // Requests the finest LOD of the static spatial mapping mesh.

// Initialize a new Scene
Scene myScene = SceneObserver.ComputeAsync(querySettings, 10.0f).GetAwaiter().GetResult();
```

### <a name="initialization-from-data-also-known-as-the-pc-path"></a><span data-ttu-id="bde8b-238">Inizializzazione dai dati (nota anche come .</span><span class="sxs-lookup"><span data-stu-id="bde8b-238">Initialization from Data (also known as.</span></span> <span data-ttu-id="bde8b-239">il percorso del PC)</span><span class="sxs-lookup"><span data-stu-id="bde8b-239">the PC Path)</span></span>

<span data-ttu-id="bde8b-240">Anche se le scene possono essere calcolate per l'utilizzo diretto, possono anche essere calcolate in formato serializzato per un uso successivo.</span><span class="sxs-lookup"><span data-stu-id="bde8b-240">While Scenes can be computed for direct consumption, they can also be computed in serialized form for later use.</span></span> <span data-ttu-id="bde8b-241">Questo si è dimostrato utile per lo sviluppo perché consente agli sviluppatori di lavorare e testare Scene Understanding senza la necessità di un dispositivo.</span><span class="sxs-lookup"><span data-stu-id="bde8b-241">This has proven to be useful for development as it allows developers to work in and test Scene Understanding without the need for a device.</span></span> <span data-ttu-id="bde8b-242">L'azione di serializzazione di una scena è quasi identica al calcolo. I dati vengono restituiti all'applicazione anziché essere deserializzati localmente dall'SDK.</span><span class="sxs-lookup"><span data-stu-id="bde8b-242">The act of serializing a scene is nearly identical to computing it, the data is returned to your application instead of being deserialized locally by the SDK.</span></span> <span data-ttu-id="bde8b-243">È quindi possibile deserializzarlo manualmente o salvarlo per un uso futuro.</span><span class="sxs-lookup"><span data-stu-id="bde8b-243">You may then deserialize it yourself or save it for future use.</span></span>

```cs
// Create Query settings for the scene update
SceneQuerySettings querySettings;

// Compute a scene but serialized as a byte array
SceneBuffer newSceneBuffer = SceneObserver.ComputeSerializedAsync(querySettings, 10.0f).GetAwaiter().GetResult();

// If we want to use it immediately we can de-serialize the scene ourselves
byte[] newSceneData = new byte[newSceneBuffer.Size];
newSceneBuffer.GetData(newSceneData);
Scene mySceneDeSerialized = Scene.Deserialize(newSceneData);

// Save newSceneData for later
```

### <a name="sceneobject-enumeration"></a><span data-ttu-id="bde8b-244">Enumerazione SceneObject</span><span class="sxs-lookup"><span data-stu-id="bde8b-244">SceneObject Enumeration</span></span>

<span data-ttu-id="bde8b-245">Ora che l'applicazione ha una scena, l'applicazione esamina e interagisce con SceneObjects.</span><span class="sxs-lookup"><span data-stu-id="bde8b-245">Now that your application has a scene, your application will be looking at and interacting with SceneObjects.</span></span> <span data-ttu-id="bde8b-246">Questa operazione viene eseguita accedendo **alla proprietà SceneObjects:**</span><span class="sxs-lookup"><span data-stu-id="bde8b-246">This is done by accessing the **SceneObjects** property:</span></span>

```cs
SceneObject firstFloor = null;

// Find the first floor object
foreach (var sceneObject in myScene.SceneObjects)
{
    if (sceneObject.Kind == SceneObjectKind.Floor)
    {
        firstFloor = sceneObject;
        break;
    }
}
```

### <a name="component-update-and-refinding-components"></a><span data-ttu-id="bde8b-247">Aggiornamento e perfezionamento dei componenti</span><span class="sxs-lookup"><span data-stu-id="bde8b-247">Component update and refinding components</span></span>

<span data-ttu-id="bde8b-248">Esiste un'altra funzione che recupera i componenti nella scena denominata ***FindComponent.***</span><span class="sxs-lookup"><span data-stu-id="bde8b-248">There's another function that retrieves components in the Scene called ***FindComponent***.</span></span> <span data-ttu-id="bde8b-249">Questa funzione è utile quando si aggiornano gli oggetti di rilevamento e li si trova in scene successive.</span><span class="sxs-lookup"><span data-stu-id="bde8b-249">This function is useful when updating tracking objects and finding them in later scenes.</span></span> <span data-ttu-id="bde8b-250">Il codice seguente calcola una nuova scena rispetto a una scena precedente e quindi trova il piano nella nuova scena.</span><span class="sxs-lookup"><span data-stu-id="bde8b-250">The following code will compute a new scene relative to a previous scene and then find the floor in the new scene.</span></span>

```cs
// Compute a new scene, and tell the system that we want to compute relative to the previous scene
Scene myNextScene = SceneObserver.ComputeAsync(querySettings, 10.0f, myScene).GetAwaiter().GetResult();

// Use the Id for the floor we found last time, and find it again
firstFloor = (SceneObject)myNextScene.FindComponent(firstFloor.Id);

if (firstFloor != null)
{
    // We found it again, we can now update the transforms of all objects we attached to this floor transform
}
```

## <a name="accessing-meshes-and-quads-from-scene-objects"></a><span data-ttu-id="bde8b-251">Accesso a mesh e quad da oggetti scena</span><span class="sxs-lookup"><span data-stu-id="bde8b-251">Accessing Meshes and Quads from Scene Objects</span></span>

<span data-ttu-id="bde8b-252">Dopo aver trovato sceneObject, è molto probabile che l'applicazione voglia accedere ai dati contenuti nei quad/mesh da cui è composta.</span><span class="sxs-lookup"><span data-stu-id="bde8b-252">Once SceneObjects have been found your application will most likely want to access the data that is contained in the quads/meshes that it is composed of.</span></span> <span data-ttu-id="bde8b-253">È possibile accedere a questi dati con le proprietà \***Quads** _ e _ \*_Meshes_\*\*.</span><span class="sxs-lookup"><span data-stu-id="bde8b-253">This data is accessed with the ***Quads** _ and _ *_Meshes_** properties.</span></span> <span data-ttu-id="bde8b-254">Il codice seguente enumera tutti i quad e le mesh dell'oggetto floor.</span><span class="sxs-lookup"><span data-stu-id="bde8b-254">The following code will enumerate all quads and meshes of our floor object.</span></span>

```cs

// Get the transform for the SceneObject
System.Numerics.Matrix4x4 objectToSceneOrigin = firstFloor.GetLocationAsMatrix();

// Enumerate quads
foreach (var quad in firstFloor.Quads)
{
    // Process quads
}

// Enumerate meshes
foreach (var mesh in firstFloor.Meshes)
{
    // Process meshes
}
```

<span data-ttu-id="bde8b-255">Si noti che è l'oggetto SceneObject che ha la trasformazione relativa all'origine della scena.</span><span class="sxs-lookup"><span data-stu-id="bde8b-255">Notice that it's the SceneObject that has the transform that is relative to the Scene origin.</span></span> <span data-ttu-id="bde8b-256">Ciò è dovuto al fatto che SceneObject rappresenta un'istanza di una "cosa" ed è localizzato nello spazio, i quad e le mesh rappresentano la geometria trasformata rispetto all'elemento padre.</span><span class="sxs-lookup"><span data-stu-id="bde8b-256">This is because the SceneObject represents an instance of a "thing" and is locatable in space, the quads, and meshes represent geometry that is transformed relative to their parent.</span></span> <span data-ttu-id="bde8b-257">È possibile che sceneObject separati puntino allo stesso SceneMesh/SceneQuad SceneComponents ed è anche possibile che un Oggetto SceneObject abbia più sceneMesh/SceneQuad.</span><span class="sxs-lookup"><span data-stu-id="bde8b-257">It's possible for separate SceneObjects to reference the same SceneMesh/SceneQuad SceneComponents, and it's also possible that a SceneObject has more than one SceneMesh/SceneQuad.</span></span>

### <a name="dealing-with-transforms"></a><span data-ttu-id="bde8b-258">Gestione delle trasformazioni</span><span class="sxs-lookup"><span data-stu-id="bde8b-258">Dealing with Transforms</span></span>

<span data-ttu-id="bde8b-259">Scene Understanding ha effettuato un tentativo intenzionale di allinearsi alle rappresentazioni tradizionali della scena 3D quando si gestiscono le trasformazioni.</span><span class="sxs-lookup"><span data-stu-id="bde8b-259">Scene Understanding has made a deliberate attempt to align with traditional 3D scene representations when dealing with transforms.</span></span> <span data-ttu-id="bde8b-260">Ogni scena è quindi limitata a un singolo sistema di coordinate in modo molto simile alla maggior parte delle rappresentazioni ambientali 3D più comuni.</span><span class="sxs-lookup"><span data-stu-id="bde8b-260">Each Scene is therefore confined to a single coordinate system much like most common 3D environmental representations.</span></span> <span data-ttu-id="bde8b-261">Ogni sceneObject fornisce la propria posizione rispetto al sistema di coordinate.</span><span class="sxs-lookup"><span data-stu-id="bde8b-261">SceneObjects each provide their location relative to that coordinate system.</span></span> <span data-ttu-id="bde8b-262">Se l'applicazione ha a che fare con scene che estendono il limite di ciò che fornisce una singola origine, può ancorare SceneObject a SpatialAnchors oppure generare diverse scene e unirle tra loro, ma per semplicità si presuppone che le scene con dimensioni mance siano presenti nella propria origine localizzata da un NodeId definito da Scene.OriginSpatialGraphNodeId.</span><span class="sxs-lookup"><span data-stu-id="bde8b-262">If your application is dealing with Scenes that stretch the limit of what a single origin provides it can anchor SceneObjects to SpatialAnchors, or generate several scenes and merge them together, but for simplicity we assume that watertight scenes exist in their own origin that's localized by one NodeId defined by Scene.OriginSpatialGraphNodeId.</span></span>

<span data-ttu-id="bde8b-263">Il codice Unity seguente, ad esempio, illustra come usare Windows Perception e le API Unity per allineare i sistemi di coordinate.</span><span class="sxs-lookup"><span data-stu-id="bde8b-263">The following Unity code, for example, shows how to use Windows Perception and Unity APIs to align coordinate systems together.</span></span> <span data-ttu-id="bde8b-264">Vedere [SpatialCoordinateSystem](/uwp/api/windows.perception.spatial.spatialcoordinatesystem) e [SpatialGraphInteropPreview](/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview) per informazioni dettagliate sulle API Di percezione di Windows e Oggetti nativi di realtà mista [in Unity](/windows/mixed-reality/unity-xrdevice-advanced) per informazioni dettagliate su come ottenere un SpatialCoordinateSystem corrispondente all'origine mondiale di Unity.</span><span class="sxs-lookup"><span data-stu-id="bde8b-264">See [SpatialCoordinateSystem](/uwp/api/windows.perception.spatial.spatialcoordinatesystem) and [SpatialGraphInteropPreview](/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview) for details on the Windows Perception APIs, and [Mixed Reality native objects in Unity](/windows/mixed-reality/unity-xrdevice-advanced) for details on obtaining a SpatialCoordinateSystem that corresponds to Unity's world origin.</span></span>

```cs
private System.Numerics.Matrix4x4? GetSceneToUnityTransformAsMatrix4x4(SceneUnderstanding.Scene scene)
{

      System.Numerics.Matrix4x4? sceneToUnityTransform = System.Numerics.Matrix4x4.Identity;

      Windows.Perception.Spatial.SpatialCoordinateSystem sceneCoordinateSystem = Microsoft.Windows.Perception.Spatial.Preview.SpatialGraphInteropPreview.CreateCoordinateSystemForNode(scene.OriginSpatialGraphNodeId);
      HolograhicFrameData holoFrameData =  Marshal.PtrToStructure<HolograhicFrameData>(UnityEngine.XR.XRDevice.GetNativePtr());
      Windows.Perception.Spatial.SpatialCoordinateSystem unityCoordinateSystem = Microsoft.Windows.Perception.Spatial.SpatialCoordinateSystem.FromNativePtr(holoFrameData.ISpatialCoordinateSystemPtr);

      sceneToUnityTransform = sceneCoordinateSystem.TryGetTransformTo(unityCoordinateSystem);

      if(sceneToUnityTransform != null)
      {
          sceneToUnityTransform = ConvertRightHandedMatrix4x4ToLeftHanded(sceneToUnityTransform.Value);
      }
      else
      {
          return null;
      }

    return sceneToUnityTransform;
}
```

<span data-ttu-id="bde8b-265">Ogni `SceneObject` oggetto ha una trasformazione, che viene quindi applicata a tale oggetto.</span><span class="sxs-lookup"><span data-stu-id="bde8b-265">Each `SceneObject` has a transform, which is then applied to that object.</span></span> <span data-ttu-id="bde8b-266">In Unity si esegue la conversione in coordinate della mano destra e si assegnano trasformazioni locali nel modo seguente:</span><span class="sxs-lookup"><span data-stu-id="bde8b-266">In Unity we convert to right handed coordinates and assign local transforms as so:</span></span>

```cs
private System.Numerics.Matrix4x4 ConvertRightHandedMatrix4x4ToLeftHanded(System.Numerics.Matrix4x4 matrix)
{
    matrix.M13 = -matrix.M13;
    matrix.M23 = -matrix.M23;
    matrix.M43 = -matrix.M43;

    matrix.M31 = -matrix.M31;
    matrix.M32 = -matrix.M32;
    matrix.M34 = -matrix.M34;

    return matrix;
}

 private void SetUnityTransformFromMatrix4x4(Transform targetTransform, System.Numerics.Matrix4x4 matrix, bool updateLocalTransformOnly = false)
 {
    if(targetTransform == null)
    {
        return;
    }

    Vector3 unityTranslation;
    Quaternion unityQuat;
    Vector3 unityScale;

    System.Numerics.Vector3 vector3;
    System.Numerics.Quaternion quaternion;
    System.Numerics.Vector3 scale;

    System.Numerics.Matrix4x4.Decompose(matrix, out scale, out quaternion, out vector3);

    unityTranslation = new Vector3(vector3.X, vector3.Y, vector3.Z);
    unityQuat        = new Quaternion(quaternion.X, quaternion.Y, quaternion.Z, quaternion.W);
    unityScale       = new Vector3(scale.X, scale.Y, scale.Z);

    if(updateLocalTransformOnly)
    {
        targetTransform.localPosition = unityTranslation;
        targetTransform.localRotation = unityQuat;
    }
    else
    {
        targetTransform.SetPositionAndRotation(unityTranslation, unityQuat);
    }
}

// Assume we have an SU object called suObject and a unity equivalent unityObject

System.Numerics.Matrix4x4 converted4x4LocationMatrix = ConvertRightHandedMatrix4x4ToLeftHanded(suObject.GetLocationAsMatrix());
SetUnityTransformFromMatrix4x4(unityObject.transform, converted4x4LocationMatrix, true);
        
```

### <a name="quad"></a><span data-ttu-id="bde8b-267">Quad</span><span class="sxs-lookup"><span data-stu-id="bde8b-267">Quad</span></span>

<span data-ttu-id="bde8b-268">I quad sono stati progettati per aiutare gli scenari di posizionamento 2D e devono essere pensati come estensioni agli elementi UX canvas 2D.</span><span class="sxs-lookup"><span data-stu-id="bde8b-268">Quads were designed to help 2D placement scenarios and should be thought of as extensions to 2D canvas UX elements.</span></span> <span data-ttu-id="bde8b-269">Anche se i quad sono componenti di SceneObject e possono essere sottoposti a rendering in 3D, le API Quad presuppongono che i quad siano strutture 2D.</span><span class="sxs-lookup"><span data-stu-id="bde8b-269">While Quads are components of SceneObjects and can be rendered in 3D, the Quad APIs themselves assume Quads are 2D structures.</span></span> <span data-ttu-id="bde8b-270">Offrono informazioni come extent, forma e api per il posizionamento.</span><span class="sxs-lookup"><span data-stu-id="bde8b-270">They offer information such as extent, shape, and provide APIs for placement.</span></span>

<span data-ttu-id="bde8b-271">I quad hanno extent rettangolari, ma rappresentano superfici 2D a forma arbitraria.</span><span class="sxs-lookup"><span data-stu-id="bde8b-271">Quads have rectangular extents, but they represent arbitrarily shaped 2D surfaces.</span></span> <span data-ttu-id="bde8b-272">Per abilitare il posizionamento su queste superfici 2D che interagiscono con i quad dell'ambiente 3D, sono disponibili utilità che rendono possibile questa interazione.</span><span class="sxs-lookup"><span data-stu-id="bde8b-272">To enable placement on these 2D surfaces that interact with the 3D environment quads offer utilities to make this interaction possible.</span></span> <span data-ttu-id="bde8b-273">Scene Understanding offre attualmente due funzioni di questo tipo, **FindCentermostPlacement** **e GetSurfaceMask.**</span><span class="sxs-lookup"><span data-stu-id="bde8b-273">Currently Scene Understanding provides two such functions, **FindCentermostPlacement** and **GetSurfaceMask**.</span></span> <span data-ttu-id="bde8b-274">FindCentermostPlacement è un'API di alto livello che individua una posizione sul quad in cui è possibile posizionare un oggetto e tenterà di trovare la posizione migliore per l'oggetto, assicurando che il rettangolo di selezione fornito rimanga sulla superficie sottostante.</span><span class="sxs-lookup"><span data-stu-id="bde8b-274">FindCentermostPlacement is a high-level API that locates a position on the quad where an object can be placed and will try to find the best location for your object guaranteeing that the bounding box you provide will stay on the underlying surface.</span></span>

> [!NOTE]
> <span data-ttu-id="bde8b-275">Le coordinate dell'output sono relative al quad nello "spazio quad" con l'angolo superiore sinistro (x = 0, y = 0), esattamente come con altri tipi windows Rect.</span><span class="sxs-lookup"><span data-stu-id="bde8b-275">The coordinates of the output are relative to the quad in "quad space" with the top left corner being (x = 0, y = 0), just as it would be with other windows Rect types.</span></span> <span data-ttu-id="bde8b-276">Assicurarsi di prendere in considerazione questo problema quando si lavora con le origini dei propri oggetti.</span><span class="sxs-lookup"><span data-stu-id="bde8b-276">Be sure to take this into account when working with the origins of your own objects.</span></span> 

<span data-ttu-id="bde8b-277">L'esempio seguente mostra come trovare la posizione più al centro e ancorare un ologramma al quad.</span><span class="sxs-lookup"><span data-stu-id="bde8b-277">The following example shows how to find the centermost placeable location and anchor a hologram to the quad.</span></span>

```cs
// This code assumes you already have a "Root" object that attaches the Scene's Origin.

// Find the first quad
foreach (var sceneObject in myScene.SceneObjects)
{
    // Find a wall
    if (sceneObject.Kind == SceneObjectKind.Wall)
    {
        // Get the quad
        var quads = sceneObject.Quads;
        if (quads.Count > 0)
        {
            // Find a good location for a 1mx1m object  
            System.Numerics.Vector2 location;
            if (quads[0].FindCentermostPlacement(new System.Numerics.Vector2(1.0f, 1.0f), out location))
            {
                // We found one, anchor something to the transform
                // Step 1: Create a new game object for the quad itself as a child of the scene root
                // Step 2: Set the local transform from quads[0].Position and quads[0].Orientation
                // Step 3: Create your hologram and set it as a child of the quad's game object
                // Step 4: Set the hologram's local transform to a translation (location.x, location.y, 0)
            }
        }
    }
}
```

<span data-ttu-id="bde8b-278">I passaggi da 1 a 4 dipendono altamente dal framework o dall'implementazione specifici, ma i temi devono essere simili.</span><span class="sxs-lookup"><span data-stu-id="bde8b-278">Steps 1-4 are highly dependent on your particular framework/implementation, but the themes should be similar.</span></span> <span data-ttu-id="bde8b-279">È importante notare che il quad rappresenta semplicemente un piano 2D delimitato localizzato nello spazio.</span><span class="sxs-lookup"><span data-stu-id="bde8b-279">It's important to note that the Quad simply represents a bounded 2D plane that is localized in space.</span></span> <span data-ttu-id="bde8b-280">Facendo in modo che il motore/framework sappia dove si trova il quad e che radicei gli oggetti rispetto al quad, gli ologrammi verranno posizionati correttamente rispetto al mondo reale.</span><span class="sxs-lookup"><span data-stu-id="bde8b-280">By having your engine/framework know where the quad is and rooting your objects relative to the quad, your holograms will be located correctly with respect to the real world.</span></span> 

<!-- 
// TODO: Add sample link when released
For more detailed information please see our samples on quads which show specific implementations.
-->

### <a name="mesh"></a><span data-ttu-id="bde8b-281">Mesh</span><span class="sxs-lookup"><span data-stu-id="bde8b-281">Mesh</span></span>

<span data-ttu-id="bde8b-282">Le mesh rappresentano rappresentazioni geometriche di oggetti o ambienti.</span><span class="sxs-lookup"><span data-stu-id="bde8b-282">Meshes represent geometric representations of objects or environments.</span></span> <span data-ttu-id="bde8b-283">Analogamente al [mapping](../../design/spatial-mapping.md)spaziale, i dati dell'indice di mesh e dei vertici forniti con ogni mesh di superficie spaziale utilizzano lo stesso layout familiare dei buffer dei vertici e degli indici usati per il rendering delle mesh triangolare in tutte le API di rendering moderne.</span><span class="sxs-lookup"><span data-stu-id="bde8b-283">Much like [spatial mapping](../../design/spatial-mapping.md), mesh index and vertex data provided with each spatial surface mesh uses the same familiar layout as the vertex and index buffers that are used for rendering triangle meshes in all modern rendering APIs.</span></span> <span data-ttu-id="bde8b-284">Le posizioni dei vertici vengono fornite nel sistema di coordinate di `Scene` .</span><span class="sxs-lookup"><span data-stu-id="bde8b-284">Vertex positions are provided in the coordinate system of the `Scene`.</span></span> <span data-ttu-id="bde8b-285">Le API specifiche usate per fare riferimento a questi dati sono le seguenti:</span><span class="sxs-lookup"><span data-stu-id="bde8b-285">The specific APIs used to reference this data are as follows:</span></span>

```cs
void GetTriangleIndices(int[] indices);
void GetVertices(System.Numerics.Vector3[] vertices);
```

<span data-ttu-id="bde8b-286">Il codice seguente fornisce un esempio di generazione di un elenco di triangoli dalla struttura mesh:</span><span class="sxs-lookup"><span data-stu-id="bde8b-286">The following code provides an example of generating a triangle list from the mesh structure:</span></span>

```cs
uint[] indices = new uint[mesh.TriangleIndexCount];
System.Numerics.Vector3[] positions = new System.Numerics.Vector3[mesh.VertexCount];

mesh.GetTriangleIndices(indices);
mesh.GetVertexPositions(positions);
```

<span data-ttu-id="bde8b-287">I buffer di indice/vertice devono essere >= conteggi di indici/vertici, ma in caso contrario possono essere ridimensionati in modo arbitrario consentendo un riutilizzo efficiente della memoria.</span><span class="sxs-lookup"><span data-stu-id="bde8b-287">The index/vertex buffers must be >= the index/vertex counts, but otherwise can be arbitrarily sized allowing for efficient memory reuse.</span></span>

### <a name="collidermesh"></a><span data-ttu-id="bde8b-288">ColliderMesh</span><span class="sxs-lookup"><span data-stu-id="bde8b-288">ColliderMesh</span></span>

<span data-ttu-id="bde8b-289">Gli oggetti scena forniscono l'accesso ai dati della mesh e della mesh collisore tramite le proprietà Meshes e ColliderMeshes.</span><span class="sxs-lookup"><span data-stu-id="bde8b-289">Scene objects provide access to mesh and collider mesh data via the Meshes and ColliderMeshes properties.</span></span> <span data-ttu-id="bde8b-290">Queste mesh corrisponderanno sempre, vale a dire che l'indice i della proprietà Meshes rappresenta la stessa geometria dell'indice i'th della proprietà ColliderMeshes.</span><span class="sxs-lookup"><span data-stu-id="bde8b-290">These meshes will always match, meaning that the i'th index of the Meshes property represents the same geometry as the i'th index of the ColliderMeshes property.</span></span> <span data-ttu-id="bde8b-291">Se il runtime o l'oggetto supporta le mesh di collisore, si ottiene il poligono più basso e l'approssimazione dell'ordine più alto ed è consigliabile usare ColliderMeshes ovunque l'applicazione usi collisori.</span><span class="sxs-lookup"><span data-stu-id="bde8b-291">If the runtime/object supports collider meshes, you are guaranteed to get the lowest polygon, highest order approximation and it's good practice to use ColliderMeshes wherever your application would use colliders.</span></span> <span data-ttu-id="bde8b-292">Se il sistema non supporta collisori, l'oggetto Mesh restituito in ColliderMeshes sarà lo stesso oggetto della mesh riducendo i vincoli di memoria.</span><span class="sxs-lookup"><span data-stu-id="bde8b-292">If the system does not support colliders the Mesh object returned in ColliderMeshes will be the same object as the mesh reducing memory constraints.</span></span>

## <a name="developing-with-scene-understanding"></a><span data-ttu-id="bde8b-293">Sviluppo con comprensione della scena</span><span class="sxs-lookup"><span data-stu-id="bde8b-293">Developing with scene understanding</span></span>

<span data-ttu-id="bde8b-294">A questo punto, è necessario comprendere i blocchi predefiniti principali del runtime di comprensione della scena e dell'SDK.</span><span class="sxs-lookup"><span data-stu-id="bde8b-294">At this point, you should understand the core building blocks of the scene understanding runtime and SDK.</span></span> <span data-ttu-id="bde8b-295">La maggior parte della potenza e della complessità risiede nei modelli di accesso, nell'interazione con framework 3D e in strumenti che possono essere scritti su queste API per eseguire attività più avanzate, ad esempio pianificazione spaziale, analisi delle camere, navigazione, fisica e così via.</span><span class="sxs-lookup"><span data-stu-id="bde8b-295">The bulk of the power and complexity lies in access patterns, interaction with 3D frameworks, and tools that can be written on top of these APIs to do more advanced tasks like spatial planning, room analysis, navigation, physics, and so on.</span></span> <span data-ttu-id="bde8b-296">Ci auguriamo di acquisire questi esempi che dovrebbero guidare l'utente nella direzione corretta per rendere i tuoi scenari più luminosi.</span><span class="sxs-lookup"><span data-stu-id="bde8b-296">We hope to capture these in samples that should hopefully guide you in the proper direction to make your scenarios shine.</span></span> <span data-ttu-id="bde8b-297">Se sono presenti esempi o scenari che non vengono affrontati, è possibile contattarci e proveremo a documentare/creare un prototipo di ciò che serve.</span><span class="sxs-lookup"><span data-stu-id="bde8b-297">If there are samples or scenarios we aren't addressing, let us know and we'll try to document/prototype what you need.</span></span>

### <a name="where-can-i-get-sample-code"></a><span data-ttu-id="bde8b-298">Dove è possibile ottenere codice di esempio?</span><span class="sxs-lookup"><span data-stu-id="bde8b-298">Where can I get sample code?</span></span>

<span data-ttu-id="bde8b-299">Il codice di esempio scene Understanding per Unity è disponibile nella pagina [di esempio di Unity.](https://github.com/sceneunderstanding-microsoft/unitysample)</span><span class="sxs-lookup"><span data-stu-id="bde8b-299">Scene Understanding sample code for Unity can be found on our [Unity Sample Page](https://github.com/sceneunderstanding-microsoft/unitysample) page.</span></span> <span data-ttu-id="bde8b-300">Questa applicazione consente di comunicare con il dispositivo ed eseguire il rendering dei vari oggetti scena oppure di caricare una scena serializzata nel PC e di sperimentare Scene Understanding senza un dispositivo.</span><span class="sxs-lookup"><span data-stu-id="bde8b-300">This application will allow you to communicate with your device and render the various scene objects, or, it will allow you to load a serialized scene on your PC and allow you to experience Scene Understanding without a device.</span></span>

### <a name="where-can-i-get-sample-scenes"></a><span data-ttu-id="bde8b-301">Dove è possibile ottenere scene di esempio?</span><span class="sxs-lookup"><span data-stu-id="bde8b-301">Where can I get sample scenes?</span></span>

<span data-ttu-id="bde8b-302">Se hai un dispositivo HoloLens2, puoi salvare qualsiasi scena acquisita salvando l'output di ComputeSerializedAsync nel file e deserializzarlo per comodità.</span><span class="sxs-lookup"><span data-stu-id="bde8b-302">If you have a HoloLens2, you can save any scene you've captured by saving the output of ComputeSerializedAsync to file and deserializing it at your own convenience.</span></span> 

<span data-ttu-id="bde8b-303">Se non hai un dispositivo HoloLens2 ma vuoi riprodurre con Scene Understanding, dovrai scaricare una scena pre-acquisita.</span><span class="sxs-lookup"><span data-stu-id="bde8b-303">If you don't have a HoloLens2 device but want to play with Scene Understanding, you'll need to download a pre-captured scene.</span></span> <span data-ttu-id="bde8b-304">L'esempio Scene Understanding viene attualmente fornito con scene serializzate che possono essere scaricate e usate in base alle proprie esigenze.</span><span class="sxs-lookup"><span data-stu-id="bde8b-304">The Scene Understanding sample currently ships with serialized scenes that can be downloaded and used at your own convenience.</span></span> <span data-ttu-id="bde8b-305">È possibile trovarli qui:</span><span class="sxs-lookup"><span data-stu-id="bde8b-305">You can find them here:</span></span>

[<span data-ttu-id="bde8b-306">Scene di esempio per la comprensione della scena</span><span class="sxs-lookup"><span data-stu-id="bde8b-306">Scene Understanding Sample Scenes</span></span>](https://github.com/microsoft/MixedReality-SceneUnderstanding-Samples)

## <a name="see-also"></a><span data-ttu-id="bde8b-307">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="bde8b-307">See also</span></span>

* [<span data-ttu-id="bde8b-308">Mapping spaziale</span><span class="sxs-lookup"><span data-stu-id="bde8b-308">Spatial mapping</span></span>](../../design/spatial-mapping.md)
* [<span data-ttu-id="bde8b-309">Informazioni sulle scene</span><span class="sxs-lookup"><span data-stu-id="bde8b-309">Scene understanding</span></span>](../../design/scene-understanding.md)
* [<span data-ttu-id="bde8b-310">Esempio unity</span><span class="sxs-lookup"><span data-stu-id="bde8b-310">Unity Sample</span></span>](https://github.com/microsoft/MixedReality-SceneUnderstanding-Samples)
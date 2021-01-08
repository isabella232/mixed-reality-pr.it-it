---
title: Scenario di comprensione dell'SDK
description: Informazioni su come installare e usare la scena Understanding SDK, inclusi componenti, mesh e oggetti nelle app per realtà mista.
author: szymons
ms.author: szymons
ms.date: 12/14/2020
ms.topic: article
keywords: Comprensione della scena, mapping spaziale, realtà mista di Windows, Unity
ms.openlocfilehash: 9520ad604125705c60624254b097de5fc93021ec
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2021
ms.locfileid: "98009381"
---
# <a name="scene-understanding-sdk-overview"></a><span data-ttu-id="936c0-104">Panoramica dell'SDK per la comprensione della scena</span><span class="sxs-lookup"><span data-stu-id="936c0-104">Scene understanding SDK overview</span></span>

<span data-ttu-id="936c0-105">La comprensione della scena trasforma i dati dei sensori di ambiente non strutturati che il dispositivo della realtà mista acquisisce e li converte in una rappresentazione astratta potente.</span><span class="sxs-lookup"><span data-stu-id="936c0-105">Scene understanding transforms the unstructured environment sensor data that your Mixed Reality device captures and converts it into a powerful abstract representation.</span></span> <span data-ttu-id="936c0-106">L'SDK funge da livello di comunicazione tra l'applicazione e la scena che comprende il Runtime.</span><span class="sxs-lookup"><span data-stu-id="936c0-106">The SDK acts as the communication layer between your application and the Scene Understanding runtime.</span></span> <span data-ttu-id="936c0-107">Ha lo scopo di simulare costrutti standard esistenti, ad esempio grafici della scena 3D per le rappresentazioni 3D e rettangoli e pannelli 2D per le applicazioni 2D.</span><span class="sxs-lookup"><span data-stu-id="936c0-107">It's aimed to mimic existing standard constructs, such as 3D scene graphs for 3D representations, and 2D rectangles and panels for 2D applications.</span></span> <span data-ttu-id="936c0-108">Mentre la scena dei costrutti che comprendono le simulazioni verrà mappata a Framework concreti, in generale SceneUnderstanding è un Framework agnostico che consente l'interoperabilità tra diversi Framework che interagiscono con essa.</span><span class="sxs-lookup"><span data-stu-id="936c0-108">While the constructs Scene Understanding mimics will map to concrete frameworks, in general SceneUnderstanding is framework agnostic allowing for interoperability between varied frameworks that interact with it.</span></span> <span data-ttu-id="936c0-109">Poiché la comprensione della scena evolve il ruolo dell'SDK è garantire che le nuove rappresentazioni e funzionalità continuino a essere esposte in un framework unificato.</span><span class="sxs-lookup"><span data-stu-id="936c0-109">As Scene Understanding evolves the role of the SDK is to ensure new representations and capabilities continue to be exposed within a unified framework.</span></span> <span data-ttu-id="936c0-110">In questo documento si introdurranno innanzitutto concetti di alto livello che consentiranno di acquisire familiarità con l'ambiente di sviluppo o l'utilizzo e quindi fornire una documentazione più dettagliata per classi e costrutti specifici.</span><span class="sxs-lookup"><span data-stu-id="936c0-110">In this document, we will first introduce high-level concepts that will help you get familiar with the development environment/usage and then provide more detailed documentation for specific classes and constructs.</span></span>

## <a name="where-do-i-get-the-sdk"></a><span data-ttu-id="936c0-111">Dove è possibile ottenere l'SDK?</span><span class="sxs-lookup"><span data-stu-id="936c0-111">Where do I get the SDK?</span></span>

<span data-ttu-id="936c0-112">SceneUnderstanding SDK è scaricabile tramite NuGet.</span><span class="sxs-lookup"><span data-stu-id="936c0-112">The SceneUnderstanding SDK is downloadable via NuGet.</span></span>

[<span data-ttu-id="936c0-113">SDK di SceneUnderstanding</span><span class="sxs-lookup"><span data-stu-id="936c0-113">SceneUnderstanding SDK</span></span>](https://www.nuget.org/packages/Microsoft.MixedReality.SceneUnderstanding/)

<span data-ttu-id="936c0-114">**Nota:** la versione più recente dipende dai pacchetti di anteprima ed è necessario abilitare i pacchetti in versione non definitiva per visualizzarli.</span><span class="sxs-lookup"><span data-stu-id="936c0-114">**Note:** the latest release depends on preview packages and you'll need to enable pre-release packages to see it.</span></span>

<span data-ttu-id="936c0-115">Per la versione 0.5.2022-RC e versioni successive, la comprensione della scena supporta le proiezioni di linguaggio per C# e C++ che consentono alle applicazioni di sviluppare applicazioni per piattaforme Win32 o UWP.</span><span class="sxs-lookup"><span data-stu-id="936c0-115">For version 0.5.2022-rc and later, Scene Understanding supports language projections for C# and C++ allowing applications to develop applications for Win32 or UWP platforms.</span></span> <span data-ttu-id="936c0-116">A partire da questa versione, SceneUnderstanding supporta Unity support in-Editor, che blocca SceneObserver, usato esclusivamente per la comunicazione con HoloLens2.</span><span class="sxs-lookup"><span data-stu-id="936c0-116">As of this version, SceneUnderstanding supports unity in-editor support barring the SceneObserver, which is used solely for communicating with HoloLens2.</span></span> 

<span data-ttu-id="936c0-117">SceneUnderstanding richiede Windows SDK versione 18362 o successiva.</span><span class="sxs-lookup"><span data-stu-id="936c0-117">SceneUnderstanding requires Windows SDK version 18362 or higher.</span></span> 

<span data-ttu-id="936c0-118">Se si usa l'SDK in un progetto Unity, usare [NuGet per Unity](https://github.com/GlitchEnzo/NuGetForUnity) per installare il pacchetto nel progetto.</span><span class="sxs-lookup"><span data-stu-id="936c0-118">If you're using the SDK in a Unity project, use [NuGet for Unity](https://github.com/GlitchEnzo/NuGetForUnity) to install the package into your project.</span></span>

## <a name="conceptual-overview"></a><span data-ttu-id="936c0-119">Panoramica dei concetti</span><span class="sxs-lookup"><span data-stu-id="936c0-119">Conceptual Overview</span></span>

### <a name="the-scene"></a><span data-ttu-id="936c0-120">Scena</span><span class="sxs-lookup"><span data-stu-id="936c0-120">The Scene</span></span>

<span data-ttu-id="936c0-121">Il dispositivo di realtà mista sta integrando costantemente le informazioni relative a ciò che viene visualizzato nell'ambiente in uso.</span><span class="sxs-lookup"><span data-stu-id="936c0-121">Your mixed reality device is constantly integrating information about what it sees in your environment.</span></span> <span data-ttu-id="936c0-122">La comprensione della scena incanala tutte queste origini dati e produce un'unica astrazione coesiva.</span><span class="sxs-lookup"><span data-stu-id="936c0-122">Scene Understanding funnels all of these data sources and produces one single cohesive abstraction.</span></span> <span data-ttu-id="936c0-123">La comprensione della scena genera scene, ovvero una composizione di [SceneObjects](scene-understanding-SDK.md#sceneobjects) che rappresenta un'istanza di un singolo elemento, ad esempio una parete/soffitto/piano. Gli oggetti scena stessi sono una composizione di [SceneComponents, che rappresenta parti più granulari che compongono questo SceneObject.</span><span class="sxs-lookup"><span data-stu-id="936c0-123">Scene Understanding generates Scenes, which are a composition of [SceneObjects](scene-understanding-SDK.md#sceneobjects) that represent an instance of a single thing, (for example, a wall/ceiling/floor.) Scene Objects themselves are a composition of [SceneComponents, which represent more granular pieces that make up this SceneObject.</span></span> <span data-ttu-id="936c0-124">Esempi di componenti sono i quad e i mesh, ma in futuro potrebbero rappresentare i rettangoli di delimitazione, le mesh dei conflitti, i metadati e così via.</span><span class="sxs-lookup"><span data-stu-id="936c0-124">Examples of components are quads and meshes, but in the future could represent bounding boxes, collision meshes, metadata etc.</span></span>

<span data-ttu-id="936c0-125">Il processo di conversione dei dati dei sensori non elaborati in una scena è un'operazione potenzialmente costosa che può richiedere secondi per spazi medi (~ 10x10m) a minuti per spazi di grandi dimensioni (~ 50x50m) e pertanto non è un elemento che viene calcolato dal dispositivo senza richiesta di applicazione.</span><span class="sxs-lookup"><span data-stu-id="936c0-125">The process of converting the raw sensor data into a Scene is a potentially expensive operation that could take seconds for medium spaces (~10x10m) to minutes for large spaces (~50x50m) and therefore it is not something that is being computed by the device without application request.</span></span> <span data-ttu-id="936c0-126">La generazione della scena viene invece attivata dall'applicazione su richiesta.</span><span class="sxs-lookup"><span data-stu-id="936c0-126">Instead, Scene generation is triggered by your application on demand.</span></span> <span data-ttu-id="936c0-127">La classe SceneObserver dispone di metodi statici che consentono di calcolare o deserializzare una scena, con cui è possibile enumerare/interagire.</span><span class="sxs-lookup"><span data-stu-id="936c0-127">The SceneObserver class has static methods that can Compute or Deserialize a scene, which you can then enumerate/interact with.</span></span> <span data-ttu-id="936c0-128">L'azione "calcolo" viene eseguita su richiesta ed eseguita sulla CPU, ma in un processo separato (il driver della realtà mista).</span><span class="sxs-lookup"><span data-stu-id="936c0-128">The "Compute" action is executed on-demand and executes on the CPU but in a separate process (the Mixed Reality Driver).</span></span> <span data-ttu-id="936c0-129">Tuttavia, mentre si esegue il calcolo in un altro processo, i dati della scena risultanti vengono archiviati e conservati nell'applicazione nell'oggetto scena.</span><span class="sxs-lookup"><span data-stu-id="936c0-129">However, while we do compute in another process the resulting Scene data is stored and maintained in your application in the Scene object.</span></span> 

<span data-ttu-id="936c0-130">Di seguito è riportato un diagramma che illustra il flusso del processo e Mostra esempi di due applicazioni che si confrontano con la scena Understanding Runtime.</span><span class="sxs-lookup"><span data-stu-id="936c0-130">Below is a diagram that illustrates this process flow and shows examples of two applications interfacing with the Scene Understanding runtime.</span></span> 

![Diagramma di processo](images/SU-ProcessFlow.png)

<span data-ttu-id="936c0-132">Sul lato sinistro è presente un diagramma del runtime di realtà mista, che è sempre attivo e in esecuzione nel proprio processo.</span><span class="sxs-lookup"><span data-stu-id="936c0-132">On the left-hand side is a diagram of the mixed reality runtime, which is always on and running in its own process.</span></span> <span data-ttu-id="936c0-133">Questo runtime è responsabile dell'esecuzione del rilevamento dei dispositivi, del mapping spaziale e di altre operazioni che la comprensione della scena USA per comprendere e ragionare in tutto il mondo.</span><span class="sxs-lookup"><span data-stu-id="936c0-133">This runtime is responsible for performing device tracking, spatial mapping, and other operations that Scene Understanding uses to understand and reason about the world around you.</span></span> <span data-ttu-id="936c0-134">Sul lato destro del diagramma sono illustrate due applicazioni teoriche che fanno uso della comprensione della scena.</span><span class="sxs-lookup"><span data-stu-id="936c0-134">On the right side of the diagram, we show two theoretical applications that make use of Scene Understanding.</span></span> <span data-ttu-id="936c0-135">La prima interfaccia dell'applicazione con MRTK, che usa la scena Understanding SDK internamente, la seconda app calcola e usa due istanze separate della scena.</span><span class="sxs-lookup"><span data-stu-id="936c0-135">The first application interfaces with MRTK, which uses the Scene Understanding SDK internally, the second app computes and uses two separate scene instances.</span></span> <span data-ttu-id="936c0-136">Tutte e tre le scene in questo diagramma generano istanze distinte delle scene, il driver non tiene traccia dello stato globale condiviso tra le applicazioni e gli oggetti scena in un'unica scena non è stato trovato in un altro.</span><span class="sxs-lookup"><span data-stu-id="936c0-136">All three Scenes in this diagram generate distinct instances of the scenes, the driver isn't tracking global state that is shared between applications and Scene Objects in one scene aren't found in another.</span></span> <span data-ttu-id="936c0-137">La comprensione della scena fornisce un meccanismo per tenere traccia nel tempo, ma questa operazione viene eseguita tramite l'SDK.</span><span class="sxs-lookup"><span data-stu-id="936c0-137">Scene Understanding does provide a mechanism to track over time, but this is done using the SDK.</span></span> <span data-ttu-id="936c0-138">Il codice di rilevamento è già in esecuzione nell'SDK nel processo dell'app.</span><span class="sxs-lookup"><span data-stu-id="936c0-138">Tracking code is already running in the SDK in your app's process.</span></span>

<span data-ttu-id="936c0-139">Poiché ogni scena archivia i dati nello spazio di memoria dell'applicazione, si può presupporre che tutte le funzioni dell'oggetto scene o dei dati interni vengano sempre eseguite nel processo dell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="936c0-139">Because each Scene stores it's data in your application's memory space, you can assume that all function of the Scene object or it's internal data is always executed in your application's process.</span></span>

### <a name="layout"></a><span data-ttu-id="936c0-140">Layout</span><span class="sxs-lookup"><span data-stu-id="936c0-140">Layout</span></span>

<span data-ttu-id="936c0-141">Per lavorare con la comprensione della scena, può essere utile conoscere e comprendere il modo in cui il runtime rappresenta i componenti in modo logico e fisico.</span><span class="sxs-lookup"><span data-stu-id="936c0-141">To work with Scene Understanding, it may be valuable to know and understand how the runtime represents components logically and physically.</span></span> <span data-ttu-id="936c0-142">La scena rappresenta i dati con un layout specifico che è stato scelto per essere semplice mantenendo una struttura sottostante flessibile per soddisfare i requisiti futuri senza che siano necessarie revisioni principali.</span><span class="sxs-lookup"><span data-stu-id="936c0-142">The Scene represents data with a specific layout that was chosen to be simple while maintaining an underlying structure that is pliable to meet future requirements without needing major revisions.</span></span> <span data-ttu-id="936c0-143">Questa operazione viene eseguita archiviando tutti i componenti (elementi di base per tutti gli oggetti della scena) in un elenco semplice e definendo la gerarchia e la composizione tramite riferimenti in cui componenti specifici fanno riferimento ad altri.</span><span class="sxs-lookup"><span data-stu-id="936c0-143">The Scene does this by storing all Components (building blocks for all Scene Objects) in a flat list and defining hierarchy and composition through references where specific components reference others.</span></span>

<span data-ttu-id="936c0-144">Di seguito viene presentato un esempio di una struttura sia nel formato flat che nella forma logica.</span><span class="sxs-lookup"><span data-stu-id="936c0-144">Below we present an example of a structure in both its flat and logical form.</span></span>

<table>
<tr><th><span data-ttu-id="936c0-145">Layout logico</span><span class="sxs-lookup"><span data-stu-id="936c0-145">Logical Layout</span></span></th><th><span data-ttu-id="936c0-146">Layout fisico</span><span class="sxs-lookup"><span data-stu-id="936c0-146">Physical Layout</span></span></th></tr>
<tr>
<td>
<ul>
  <span data-ttu-id="936c0-147">Scene</span><span class="sxs-lookup"><span data-stu-id="936c0-147">Scene</span></span>
  <ul>
  <li><span data-ttu-id="936c0-148">SceneObject_1</span><span class="sxs-lookup"><span data-stu-id="936c0-148">SceneObject_1</span></span>
    <ul>
      <li><span data-ttu-id="936c0-149">SceneMesh_1</span><span class="sxs-lookup"><span data-stu-id="936c0-149">SceneMesh_1</span></span></li>
      <li><span data-ttu-id="936c0-150">SceneQuad_1</span><span class="sxs-lookup"><span data-stu-id="936c0-150">SceneQuad_1</span></span></li>
      <li><span data-ttu-id="936c0-151">SceneQuad_2</span><span class="sxs-lookup"><span data-stu-id="936c0-151">SceneQuad_2</span></span></li>
    </ul>
  </li>
  <li><span data-ttu-id="936c0-152">SceneObject_2</span><span class="sxs-lookup"><span data-stu-id="936c0-152">SceneObject_2</span></span>
    <ul>
      <li><span data-ttu-id="936c0-153">SceneQuad_1</span><span class="sxs-lookup"><span data-stu-id="936c0-153">SceneQuad_1</span></span></li>
      <li><span data-ttu-id="936c0-154">SceneQuad_3</span><span class="sxs-lookup"><span data-stu-id="936c0-154">SceneQuad_3</span></span></li>
      </li></ul>
  </li>
  <li><span data-ttu-id="936c0-155">SceneObject_3</span><span class="sxs-lookup"><span data-stu-id="936c0-155">SceneObject_3</span></span>
    <ul>
      <li><span data-ttu-id="936c0-156">SceneMesh_3</span><span class="sxs-lookup"><span data-stu-id="936c0-156">SceneMesh_3</span></span></li>
    </ul>
  </ul>
</ul>
</td>
<td>
<ul>
  <li><span data-ttu-id="936c0-157">SceneObject_1</span><span class="sxs-lookup"><span data-stu-id="936c0-157">SceneObject_1</span></span></li>
  <li><span data-ttu-id="936c0-158">SceneObject_2</span><span class="sxs-lookup"><span data-stu-id="936c0-158">SceneObject_2</span></span></li>
  <li><span data-ttu-id="936c0-159">SceneObject_3</span><span class="sxs-lookup"><span data-stu-id="936c0-159">SceneObject_3</span></span></li>
  <li><span data-ttu-id="936c0-160">SceneQuad_1</span><span class="sxs-lookup"><span data-stu-id="936c0-160">SceneQuad_1</span></span></li>
  <li><span data-ttu-id="936c0-161">SceneQuad_2</span><span class="sxs-lookup"><span data-stu-id="936c0-161">SceneQuad_2</span></span></li>
  <li><span data-ttu-id="936c0-162">SceneQuad_3</span><span class="sxs-lookup"><span data-stu-id="936c0-162">SceneQuad_3</span></span></li>
  <li><span data-ttu-id="936c0-163">SceneMesh_1</span><span class="sxs-lookup"><span data-stu-id="936c0-163">SceneMesh_1</span></span></li>
  <li><span data-ttu-id="936c0-164">SceneMesh_2</span><span class="sxs-lookup"><span data-stu-id="936c0-164">SceneMesh_2</span></span></li>
</ul>
</td>
</tr>
</table>

<span data-ttu-id="936c0-165">In questa illustrazione viene evidenziata la differenza tra il layout fisico e logico della scena.</span><span class="sxs-lookup"><span data-stu-id="936c0-165">This illustration highlights the difference between the physical and logical layout of the Scene.</span></span> <span data-ttu-id="936c0-166">A sinistra viene visualizzato il layout gerarchico dei dati visualizzati dall'applicazione durante l'enumerazione della scena.</span><span class="sxs-lookup"><span data-stu-id="936c0-166">On the left, we see the hierarchical layout of the data that your application sees when enumerating the scene.</span></span> <span data-ttu-id="936c0-167">A destra si noterà che la scena è costituita da 12 componenti distinti, se necessario, accessibili singolarmente.</span><span class="sxs-lookup"><span data-stu-id="936c0-167">On the right, we see that the scene is comprised of 12 distinct components that are accessible individually if necessary.</span></span> <span data-ttu-id="936c0-168">Quando si elabora una nuova scena, si prevede che le applicazioni analizzino logicamente questa gerarchia. Tuttavia, durante il rilevamento tra gli aggiornamenti della scena, alcune applicazioni potrebbero essere interessate solo a specifici componenti condivisi tra due scene.</span><span class="sxs-lookup"><span data-stu-id="936c0-168">When processing a new scene, we expect applications to walk this hierarchy logically, however when tracking between scene updates, some applications may only be interested in targeting specific components that are shared between two scenes.</span></span>

## <a name="api-overview"></a><span data-ttu-id="936c0-169">Panoramica delle API</span><span class="sxs-lookup"><span data-stu-id="936c0-169">API overview</span></span>

<span data-ttu-id="936c0-170">Nella sezione seguente viene fornita una panoramica di alto livello dei costrutti nella comprensione della scena.</span><span class="sxs-lookup"><span data-stu-id="936c0-170">The following section provides a high-level overview of the constructs in Scene Understanding.</span></span> <span data-ttu-id="936c0-171">Leggendo questa sezione si apprenderà a comprendere come vengono rappresentate le scene e quali sono i vari componenti usati per.</span><span class="sxs-lookup"><span data-stu-id="936c0-171">Reading this section will give you an  understanding of how scenes are represented, and what the various components do/are used for.</span></span> <span data-ttu-id="936c0-172">La sezione successiva fornirà esempi di codice concreti e dettagli aggiuntivi che verranno descritti in questa panoramica.</span><span class="sxs-lookup"><span data-stu-id="936c0-172">The next section will provide concrete code examples and additional details that are glossed over in this overview.</span></span>

<span data-ttu-id="936c0-173">Tutti i tipi descritti di seguito si trovano nello `Microsoft.MixedReality.SceneUnderstanding` spazio dei nomi.</span><span class="sxs-lookup"><span data-stu-id="936c0-173">All of the types described below reside in the `Microsoft.MixedReality.SceneUnderstanding` namespace.</span></span>

### <a name="scenecomponents"></a><span data-ttu-id="936c0-174">SceneComponents</span><span class="sxs-lookup"><span data-stu-id="936c0-174">SceneComponents</span></span>

<span data-ttu-id="936c0-175">Dopo aver compreso il layout logico delle scene, è ora possibile presentare il concetto di SceneComponents e il modo in cui vengono usate per comporre la gerarchia.</span><span class="sxs-lookup"><span data-stu-id="936c0-175">Now that you understand the logical layout of scenes we can now present the concept of SceneComponents and how they're used to compose hierarchy.</span></span> <span data-ttu-id="936c0-176">SceneComponents sono le scomposizione più granulari in SceneUnderstanding che rappresentano una singola cosa principale, ad esempio una mesh o un quad o un rettangolo di delimitazione.</span><span class="sxs-lookup"><span data-stu-id="936c0-176">SceneComponents are the most granular decompositions in SceneUnderstanding representing a single core thing, for example, a mesh or a quad or a bounding box.</span></span> <span data-ttu-id="936c0-177">SceneComponents sono elementi che possono essere aggiornati in modo indipendente ed è possibile farvi riferimento da altri SceneComponents, di conseguenza hanno un'unica proprietà globale un ID univoco, che consente questo tipo di meccanismo di rilevamento/riferimento.</span><span class="sxs-lookup"><span data-stu-id="936c0-177">SceneComponents are things that can update independently and can be referenced by other SceneComponents, hence they have a single global property a unique ID, that allow for this type of tracking/referencing mechanism.</span></span> <span data-ttu-id="936c0-178">Gli ID vengono usati per la composizione logica della gerarchia della scena e per la persistenza degli oggetti, ovvero l'operazione di aggiornamento di una scena rispetto a un'altra.</span><span class="sxs-lookup"><span data-stu-id="936c0-178">Ids are used for the logical composition of scene hierarchy as well as object persistence (the act of updating one scene relative to another.)</span></span> 

<span data-ttu-id="936c0-179">Se si tratta di una nuova scena calcolata come distinta e si sta semplicemente enumerando tutti i dati al suo interno, gli ID sono in gran parte trasparenti.</span><span class="sxs-lookup"><span data-stu-id="936c0-179">If you're treating every newly computed scene as being distinct, and simply enumerating all data within it then Ids are largely transparent to you.</span></span> <span data-ttu-id="936c0-180">Tuttavia, se si prevede di tenere traccia dei componenti in diversi aggiornamenti, si useranno gli ID per indicizzare e trovare SceneComponents tra gli oggetti scena.</span><span class="sxs-lookup"><span data-stu-id="936c0-180">However, if you're planning to track components over several updates you'll use the Ids to index and find SceneComponents between Scene objects.</span></span>

### <a name="sceneobjects"></a><span data-ttu-id="936c0-181">SceneObjects</span><span class="sxs-lookup"><span data-stu-id="936c0-181">SceneObjects</span></span>

<span data-ttu-id="936c0-182">Un SceneObject è un SceneComponent che rappresenta un'istanza di un elemento "Thing", ad esempio un muro, un piano, un soffitto e così via... espressa dalla relativa proprietà Kind.</span><span class="sxs-lookup"><span data-stu-id="936c0-182">A SceneObject is a SceneComponent that represents an instance of a "thing" for example, a wall, a floor, a ceiling, etc.... expressed by their Kind property.</span></span> <span data-ttu-id="936c0-183">SceneObjects sono geometriche e quindi hanno funzioni e proprietà che rappresentano la loro posizione nello spazio, ma non contengono alcuna struttura geometrica o logica.</span><span class="sxs-lookup"><span data-stu-id="936c0-183">SceneObjects are geometric, and therefore have functions and properties that represent their location in space, however they don't contain any geometric or logical structure.</span></span> <span data-ttu-id="936c0-184">SceneObjects, invece, fanno riferimento ad altri SceneComponents, in particolare SceneQuads e SceneMeshes, che forniscono le varie rappresentazioni supportate dal sistema.</span><span class="sxs-lookup"><span data-stu-id="936c0-184">Instead, SceneObjects reference other SceneComponents, specifically SceneQuads, and SceneMeshes, which provide the varied representations that are supported by the system.</span></span> <span data-ttu-id="936c0-185">Quando viene calcolata una nuova scena, l'applicazione enumera in modo più probabile la SceneObjects della scena per elaborare gli elementi interessati.</span><span class="sxs-lookup"><span data-stu-id="936c0-185">When a new scene is computed, your application will most likely enumerate the Scene's SceneObjects to process what it's interested in.</span></span>

<span data-ttu-id="936c0-186">SceneObjects può avere uno dei seguenti elementi:</span><span class="sxs-lookup"><span data-stu-id="936c0-186">SceneObjects can have any one of the following:</span></span>

<table>
<tr>
<th><span data-ttu-id="936c0-187">SceneObjectKind</span><span class="sxs-lookup"><span data-stu-id="936c0-187">SceneObjectKind</span></span></th> <th><span data-ttu-id="936c0-188">Descrizione</span><span class="sxs-lookup"><span data-stu-id="936c0-188">Description</span></span></th>
</tr>
<tr><td><span data-ttu-id="936c0-189">Sfondo</span><span class="sxs-lookup"><span data-stu-id="936c0-189">Background</span></span></td><td><span data-ttu-id="936c0-190">Il SceneObject <b>non</b> è noto come uno degli altri tipi di oggetto scena riconosciuti.</span><span class="sxs-lookup"><span data-stu-id="936c0-190">The SceneObject is known to be <b>not</b> one of the other recognized kinds of scene object.</span></span> <span data-ttu-id="936c0-191">Questa classe non deve essere confusa con uno sconosciuto, in cui lo sfondo non è a parete/piano/soffitto e così via... mentre Unknown non è ancora stato categorizzato.</span><span class="sxs-lookup"><span data-stu-id="936c0-191">This class shouldn't be confused with Unknown where Background is known not to be wall/floor/ceiling etc.... while unknown isn't yet categorized.</span></span></b></td></tr>
<tr><td><span data-ttu-id="936c0-192">Parete</span><span class="sxs-lookup"><span data-stu-id="936c0-192">Wall</span></span></td><td><span data-ttu-id="936c0-193">Una parete fisica.</span><span class="sxs-lookup"><span data-stu-id="936c0-193">A physical wall.</span></span> <span data-ttu-id="936c0-194">Si presuppone che i muri siano strutture ambientali non mobili.</span><span class="sxs-lookup"><span data-stu-id="936c0-194">Walls are assumed to be immovable environmental structures.</span></span></td></tr>
<tr><td><span data-ttu-id="936c0-195">Piano</span><span class="sxs-lookup"><span data-stu-id="936c0-195">Floor</span></span></td><td><span data-ttu-id="936c0-196">I piani sono superfici in cui è possibile spostarsi.</span><span class="sxs-lookup"><span data-stu-id="936c0-196">Floors are any surfaces on which one can walk.</span></span> <span data-ttu-id="936c0-197">Nota: le scale non sono piani.</span><span class="sxs-lookup"><span data-stu-id="936c0-197">Note: stairs aren't floors.</span></span> <span data-ttu-id="936c0-198">Si noti inoltre che le pavimentazioni presuppongono una superficie a cui è possibile spostarsi e pertanto non esiste alcun presupposto esplicito di un pavimento singolare.</span><span class="sxs-lookup"><span data-stu-id="936c0-198">Also note, that floors assume any walkable surface and therefore there's no explicit assumption of a singular floor.</span></span> <span data-ttu-id="936c0-199">Strutture a più livelli, rampe e così via... deve essere classificata come floor.</span><span class="sxs-lookup"><span data-stu-id="936c0-199">Multi-level structures, ramps etc.... should all classify as floor.</span></span></td></tr>
<tr><td><span data-ttu-id="936c0-200">Ceiling</span><span class="sxs-lookup"><span data-stu-id="936c0-200">Ceiling</span></span></td><td><span data-ttu-id="936c0-201">Superficie superiore di una stanza.</span><span class="sxs-lookup"><span data-stu-id="936c0-201">The upper surface of a room.</span></span></td></tr>
<tr><td><span data-ttu-id="936c0-202">Piattaforma</span><span class="sxs-lookup"><span data-stu-id="936c0-202">Platform</span></span></td><td><span data-ttu-id="936c0-203">Una superficie piana grande su cui posizionare gli ologrammi.</span><span class="sxs-lookup"><span data-stu-id="936c0-203">A large flat surface on which you could place holograms.</span></span> <span data-ttu-id="936c0-204">Che tendono a rappresentare tabelle, piani di ridimensionamento e altre superfici orizzontali di grandi dimensioni.</span><span class="sxs-lookup"><span data-stu-id="936c0-204">These tend to represent tables, countertops, and other large horizontal surfaces.</span></span></td></tr>
<tr><td><span data-ttu-id="936c0-205">World</span><span class="sxs-lookup"><span data-stu-id="936c0-205">World</span></span></td><td><span data-ttu-id="936c0-206">Etichetta riservata per i dati geometrici indipendenti dall'assegnazione di etichette.</span><span class="sxs-lookup"><span data-stu-id="936c0-206">A reserved label for geometric data that is agnostic to labeling.</span></span> <span data-ttu-id="936c0-207">La mesh generata impostando il flag di aggiornamento EnableWorldMesh verrebbe classificato come World.</span><span class="sxs-lookup"><span data-stu-id="936c0-207">The mesh generated by setting the EnableWorldMesh update flag would be classified as world.</span></span></td></tr>
<tr><td><span data-ttu-id="936c0-208">Sconosciuto</span><span class="sxs-lookup"><span data-stu-id="936c0-208">Unknown</span></span></td><td><span data-ttu-id="936c0-209">Questo oggetto scena deve ancora essere classificato e assegnato un tipo.</span><span class="sxs-lookup"><span data-stu-id="936c0-209">This scene object has yet to be classified and assigned a kind.</span></span> <span data-ttu-id="936c0-210">Questa operazione non deve essere confusa con background, perché questo oggetto può essere qualsiasi cosa, il sistema non ha ancora una classificazione sufficientemente sicura.</span><span class="sxs-lookup"><span data-stu-id="936c0-210">This shouldn't be confused with Background, as this object could be anything, the system has just not come up with a strong enough classification for it yet.</span></span></td></tr>
</tr>
</table>

### <a name="scenemesh"></a><span data-ttu-id="936c0-211">SceneMesh</span><span class="sxs-lookup"><span data-stu-id="936c0-211">SceneMesh</span></span>

<span data-ttu-id="936c0-212">Un SceneMesh è un SceneComponent che approssima la geometria degli oggetti geometrici arbitrari usando un elenco di triangolo.</span><span class="sxs-lookup"><span data-stu-id="936c0-212">A SceneMesh is a SceneComponent that approximates the geometry of arbitrary geometric objects using a triangle list.</span></span> <span data-ttu-id="936c0-213">SceneMeshes vengono usati in diversi contesti, possono rappresentare i componenti della struttura di celle stagne o come WorldMesh, che rappresenta la mesh di mapping spaziale senza limiti associata alla scena.</span><span class="sxs-lookup"><span data-stu-id="936c0-213">SceneMeshes are used in several different contexts, they can represent components of the watertight cell structure or as the WorldMesh, which represents the unbounded spatial mapping mesh associated with the Scene.</span></span> <span data-ttu-id="936c0-214">I dati relativi a indici e vertici forniti con ogni mesh utilizzano lo stesso layout familiare dei [buffer di vertice e di indice](https://msdn.microsoft.com/library/windows/desktop/bb147325%28v=vs.85%29.aspx) utilizzati per il rendering di mesh triangolari in tutte le moderne API di rendering.</span><span class="sxs-lookup"><span data-stu-id="936c0-214">The index and vertex data provided with each mesh uses the same familiar layout as the [vertex and index buffers](https://msdn.microsoft.com/library/windows/desktop/bb147325%28v=vs.85%29.aspx) that are used for rendering triangle meshes in all modern rendering APIs.</span></span> <span data-ttu-id="936c0-215">Nella comprensione della scena, le maglie usano indici a 32 bit e potrebbero dover essere suddivise in blocchi per determinati motori di rendering.</span><span class="sxs-lookup"><span data-stu-id="936c0-215">In Scene Understanding, meshes use 32-bit indices and may need to be broken up into chunks for certain rendering engines.</span></span>

#### <a name="winding-order-and-coordinate-systems"></a><span data-ttu-id="936c0-216">Ordine di avvolgimento e sistemi di coordinate</span><span class="sxs-lookup"><span data-stu-id="936c0-216">Winding Order and Coordinate Systems</span></span>

<span data-ttu-id="936c0-217">Tutte le mesh prodotte dalla comprensione della scena dovrebbero restituire mesh in un sistema di coordinate Right-Handed usando l'ordine di avvolgimento in senso orario.</span><span class="sxs-lookup"><span data-stu-id="936c0-217">All meshes produced by Scene Understanding are expected to return meshes in a Right-Handed coordinate system using clockwise winding order.</span></span> 

<span data-ttu-id="936c0-218">Nota: le compilazioni del sistema operativo precedenti a. 191105 possono avere un bug noto in cui le mesh "World" stavano restituendo in Counter-Clockwise ordine di avvolgimento, che in seguito è stato risolto.</span><span class="sxs-lookup"><span data-stu-id="936c0-218">Note: OS builds prior to .191105 may have a known bug where "World" meshes were returning in Counter-Clockwise winding order, which has subsequently been fixed.</span></span>

### <a name="scenequad"></a><span data-ttu-id="936c0-219">SceneQuad</span><span class="sxs-lookup"><span data-stu-id="936c0-219">SceneQuad</span></span>

<span data-ttu-id="936c0-220">Un SceneQuad è un SceneComponent che rappresenta le superfici 2D che occupano il mondo 3D.</span><span class="sxs-lookup"><span data-stu-id="936c0-220">A SceneQuad is a SceneComponent that represents 2d surfaces that occupy the 3d world.</span></span> <span data-ttu-id="936c0-221">SceneQuads può essere usato in modo analogo ai piani ARKit ARPlaneAnchor o ARCore, ma offre funzionalità più avanzate come Canvas 2D da usare con le app flat o UX potenziato.</span><span class="sxs-lookup"><span data-stu-id="936c0-221">SceneQuads can be used similarly to ARKit ARPlaneAnchor or ARCore Planes but they offer more high-level functionality as 2d canvases to be used by flat apps, or augmented UX.</span></span> <span data-ttu-id="936c0-222">sono disponibili API specifiche 2D per i quad che semplificano l'uso del posizionamento e del layout e lo sviluppo (ad eccezione del rendering) con i quad dovrebbe essere più simile all'utilizzo di Canvas 2D rispetto alle mesh 3D.</span><span class="sxs-lookup"><span data-stu-id="936c0-222">2D specific APIs are provided for quads that make placement and layout simple to use, and developing (with the exception of rendering) with quads should feel more akin to working with 2d canvases than 3d meshes.</span></span>

#### <a name="scenequad-shape"></a><span data-ttu-id="936c0-223">Forma SceneQuad</span><span class="sxs-lookup"><span data-stu-id="936c0-223">SceneQuad shape</span></span>

<span data-ttu-id="936c0-224">SceneQuads definire una superficie rettangolare delimitata in 2D.</span><span class="sxs-lookup"><span data-stu-id="936c0-224">SceneQuads define a bounded rectangular surface in 2d.</span></span> <span data-ttu-id="936c0-225">Tuttavia, SceneQuads rappresentano le superfici con forme arbitrarie e potenzialmente complesse, ad esempio una tabella con forma di anello. Per rappresentare la forma complessa della superficie di un quad, è possibile usare l'API GetSurfaceMask per eseguire il rendering della forma della superficie in un buffer di immagine fornito.</span><span class="sxs-lookup"><span data-stu-id="936c0-225">However, SceneQuads are representing surfaces with arbitrary and potentially complex shapes (e.g. a donut shaped table.) To represent the complex shape of the surface of a quad you may use the GetSurfaceMask API to render the shape of the surface onto an image buffer you provide.</span></span> <span data-ttu-id="936c0-226">Se anche il SceneObject con il quad ha una mesh, i triangoli di mesh devono essere equivalenti a questa immagine sottoposta a rendering, entrambi rappresentano la geometria reale della superficie, in coordinate 2D o 3D.</span><span class="sxs-lookup"><span data-stu-id="936c0-226">If the SceneObject that has the quad also has a mesh, the mesh triangles should be equivalent to this rendered image, they both represent real geometry of the surface, either in 2d or 3d coordinates.</span></span>

## <a name="scene-understanding-sdk-details-and-reference"></a><span data-ttu-id="936c0-227">Informazioni dettagliate e informazioni di riferimento sull'SDK della scena</span><span class="sxs-lookup"><span data-stu-id="936c0-227">Scene understanding SDK details and reference</span></span>

<span data-ttu-id="936c0-228">La sezione seguente consente di acquisire familiarità con le nozioni di base di SceneUnderstanding.</span><span class="sxs-lookup"><span data-stu-id="936c0-228">The following section will help get you familiar with the basics of SceneUnderstanding.</span></span> <span data-ttu-id="936c0-229">In questa sezione vengono fornite le nozioni di base, a questo punto è necessario disporre di un contesto sufficiente per esplorare le applicazioni di esempio per vedere come SceneUnderstanding viene usato in modo olistico.</span><span class="sxs-lookup"><span data-stu-id="936c0-229">This section should provide you with the basics, at which point you should have enough context to browse through the sample applications to see how SceneUnderstanding is used holistically.</span></span>

### <a name="initialization"></a><span data-ttu-id="936c0-230">Inizializzazione</span><span class="sxs-lookup"><span data-stu-id="936c0-230">Initialization</span></span>

<span data-ttu-id="936c0-231">Il primo passaggio per lavorare con SceneUnderstanding è che l'applicazione ottenga un riferimento a un oggetto scena.</span><span class="sxs-lookup"><span data-stu-id="936c0-231">The first step to working with SceneUnderstanding is for your application to gain reference to a Scene object.</span></span> <span data-ttu-id="936c0-232">Questa operazione può essere eseguita in uno dei due modi seguenti, una scena può essere calcolata dal driver o una scena esistente calcolata in passato può essere deserializzata.</span><span class="sxs-lookup"><span data-stu-id="936c0-232">This can be done in one of two ways, a Scene can either be computed by the driver, or an existing Scene that was computed in the past can be de-serialized.</span></span> <span data-ttu-id="936c0-233">Quest'ultimo è utile per lavorare con SceneUnderstanding durante lo sviluppo, in cui le applicazioni e le esperienze possono essere prototipate rapidamente senza un dispositivo di realtà mista.</span><span class="sxs-lookup"><span data-stu-id="936c0-233">The latter is useful for working with SceneUnderstanding during development, where applications and experiences can be prototyped quickly without a mixed reality device.</span></span>

<span data-ttu-id="936c0-234">Le scene vengono calcolate usando un SceneObserver.</span><span class="sxs-lookup"><span data-stu-id="936c0-234">Scenes are computed using a SceneObserver.</span></span> <span data-ttu-id="936c0-235">Prima di creare una scena, l'applicazione deve eseguire una query sul dispositivo per assicurarsi che supporti SceneUnderstanding, oltre a richiedere l'accesso utente per le informazioni necessarie a SceneUnderstanding.</span><span class="sxs-lookup"><span data-stu-id="936c0-235">Before creating a Scene, your application should query your device to ensure that it supports SceneUnderstanding, as well as to request user access for information that SceneUnderstanding needs.</span></span>

```cs
if (!SceneObserver.IsSupported())
{
    // Handle the error
}

// This call should grant the access we need.
await SceneObserver.RequestAccessAsync();
```

<span data-ttu-id="936c0-236">Se RequestAccessAsync () non viene chiamato, il calcolo di una nuova scena avrà esito negativo.</span><span class="sxs-lookup"><span data-stu-id="936c0-236">If RequestAccessAsync() is not called, computing a new Scene will fail.</span></span> <span data-ttu-id="936c0-237">Successivamente, verrà calcolata una nuova scena che è radicata intorno all'auricolare della realtà mista e ha un raggio di 10 metri.</span><span class="sxs-lookup"><span data-stu-id="936c0-237">Next we will compute a new scene that's rooted around the Mixed Reality headset and has a 10-meter radius.</span></span>

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

### <a name="initialization-from-data-also-known-as-the-pc-path"></a><span data-ttu-id="936c0-238">Inizializzazione dai dati, nota anche come.</span><span class="sxs-lookup"><span data-stu-id="936c0-238">Initialization from Data (also known as.</span></span> <span data-ttu-id="936c0-239">Percorso PC)</span><span class="sxs-lookup"><span data-stu-id="936c0-239">the PC Path)</span></span>

<span data-ttu-id="936c0-240">Mentre le scene possono essere calcolate per il consumo diretto, possono anche essere calcolate in formato serializzato per un uso successivo.</span><span class="sxs-lookup"><span data-stu-id="936c0-240">While Scenes can be computed for direct consumption, they can also be computed in serialized form for later use.</span></span> <span data-ttu-id="936c0-241">Questo è risultato utile per lo sviluppo in quanto consente agli sviluppatori di lavorare e testare la comprensione della scena senza la necessità di un dispositivo.</span><span class="sxs-lookup"><span data-stu-id="936c0-241">This has proven to be useful for development as it allows developers to work in and test Scene Understanding without the need for a device.</span></span> <span data-ttu-id="936c0-242">L'azione di serializzazione di una scena è quasi identica a quella di elaborazione. i dati vengono restituiti all'applicazione anziché essere deserializzati localmente dall'SDK.</span><span class="sxs-lookup"><span data-stu-id="936c0-242">The act of serializing a scene is nearly identical to computing it, the data is returned to your application instead of being deserialized locally by the SDK.</span></span> <span data-ttu-id="936c0-243">Sarà quindi possibile deserializzarlo manualmente o salvarlo per un uso futuro.</span><span class="sxs-lookup"><span data-stu-id="936c0-243">You may then deserialize it yourself or save it for future use.</span></span>

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

### <a name="sceneobject-enumeration"></a><span data-ttu-id="936c0-244">Enumerazione SceneObject</span><span class="sxs-lookup"><span data-stu-id="936c0-244">SceneObject Enumeration</span></span>

<span data-ttu-id="936c0-245">Ora che l'applicazione ha una scena, l'applicazione verrà esaminata e interagirà con SceneObjects.</span><span class="sxs-lookup"><span data-stu-id="936c0-245">Now that your application has a scene, your application will be looking at and interacting with SceneObjects.</span></span> <span data-ttu-id="936c0-246">Questa operazione viene eseguita accedendo alla proprietà **SceneObjects** :</span><span class="sxs-lookup"><span data-stu-id="936c0-246">This is done by accessing the **SceneObjects** property:</span></span>

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

### <a name="component-update-and-refinding-components"></a><span data-ttu-id="936c0-247">Componenti di aggiornamento e riricerca dei componenti</span><span class="sxs-lookup"><span data-stu-id="936c0-247">Component update and refinding components</span></span>

<span data-ttu-id="936c0-248">Esiste un'altra funzione che recupera i componenti nella scena denominata \**_findComponent_* _.</span><span class="sxs-lookup"><span data-stu-id="936c0-248">There's another function that retrieves components in the Scene called \**_FindComponent_* _.</span></span> <span data-ttu-id="936c0-249">Questa funzione è utile quando si aggiornano gli oggetti di rilevamento e li si trova nelle scene successive.</span><span class="sxs-lookup"><span data-stu-id="936c0-249">This function is useful when updating tracking objects and finding them in later scenes.</span></span> <span data-ttu-id="936c0-250">Il codice seguente consente di calcolare una nuova scena rispetto a una scena precedente e quindi di trovare il piano nella nuova scena.</span><span class="sxs-lookup"><span data-stu-id="936c0-250">The following code will compute a new scene relative to a previous scene and then find the floor in the new scene.</span></span>

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

## <a name="accessing-meshes-and-quads-from-scene-objects"></a><span data-ttu-id="936c0-251">Accesso a mesh e quad da oggetti scene</span><span class="sxs-lookup"><span data-stu-id="936c0-251">Accessing Meshes and Quads from Scene Objects</span></span>

<span data-ttu-id="936c0-252">Una volta rilevate SceneObjects, è probabile che l'applicazione acceda ai dati contenuti nei Quad/mesh di cui è composta.</span><span class="sxs-lookup"><span data-stu-id="936c0-252">Once SceneObjects have been found your application will most likely want to access the data that is contained in the quads/meshes that it is composed of.</span></span> <span data-ttu-id="936c0-253">Questi dati sono accessibili con le proprietà _*_Quad_*_ e _*_mesh_*_ .</span><span class="sxs-lookup"><span data-stu-id="936c0-253">This data is accessed with the _*_Quads_*_ and _*_Meshes_*_ properties.</span></span> <span data-ttu-id="936c0-254">Il codice seguente enumera tutti i quad e le maglie dell'oggetto Floor.</span><span class="sxs-lookup"><span data-stu-id="936c0-254">The following code will enumerate all quads and meshes of our floor object.</span></span>

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

<span data-ttu-id="936c0-255">Si noti che si tratta del SceneObject con la trasformazione rispetto all'origine della scena.</span><span class="sxs-lookup"><span data-stu-id="936c0-255">Notice that it's the SceneObject that has the transform that is relative to the Scene origin.</span></span> <span data-ttu-id="936c0-256">Ciò è dovuto al fatto che SceneObject rappresenta un'istanza di una "cosa" ed è locatable nello spazio, i quad e le mesh rappresentano la geometria che viene trasformata in relazione all'elemento padre.</span><span class="sxs-lookup"><span data-stu-id="936c0-256">This is because the SceneObject represents an instance of a "thing" and is locatable in space, the quads, and meshes represent geometry that is transformed relative to their parent.</span></span> <span data-ttu-id="936c0-257">È possibile che SceneObjects separate facciano riferimento allo stesso SceneMesh/SceneQuad SceneComponents ed è anche possibile che un SceneObject disponga di più di un SceneMesh/SceneQuad.</span><span class="sxs-lookup"><span data-stu-id="936c0-257">It's possible for separate SceneObjects to reference the same SceneMesh/SceneQuad SceneComponents, and it's also possible that a SceneObject has more than one SceneMesh/SceneQuad.</span></span>

### <a name="dealing-with-transforms"></a><span data-ttu-id="936c0-258">Gestione delle trasformazioni</span><span class="sxs-lookup"><span data-stu-id="936c0-258">Dealing with Transforms</span></span>

<span data-ttu-id="936c0-259">La comprensione della scena ha effettuato un tentativo intenzionale di allinearsi alle rappresentazioni tradizionali della scena 3D quando si gestiscono le trasformazioni.</span><span class="sxs-lookup"><span data-stu-id="936c0-259">Scene Understanding has made a deliberate attempt to align with traditional 3D scene representations when dealing with transforms.</span></span> <span data-ttu-id="936c0-260">Ogni scena è quindi confinata a un singolo sistema di coordinate, in modo analogo alla maggior parte delle rappresentazioni ambientali 3D.</span><span class="sxs-lookup"><span data-stu-id="936c0-260">Each Scene is therefore confined to a single coordinate system much like most common 3D environmental representations.</span></span> <span data-ttu-id="936c0-261">SceneObjects forniscono il percorso relativo al sistema di coordinate.</span><span class="sxs-lookup"><span data-stu-id="936c0-261">SceneObjects each provide their location relative to that coordinate system.</span></span> <span data-ttu-id="936c0-262">Se l'applicazione sta affrontando scenari che estendono il limite di una singola origine, può ancorare SceneObjects a SpatialAnchors o generare diverse scene e unirle, ma per semplicità si presuppone che esistano scene ermetiche nella propria origine localizzata da un NodeId definito da scene. OriginSpatialGraphNodeId.</span><span class="sxs-lookup"><span data-stu-id="936c0-262">If your application is dealing with Scenes that stretch the limit of what a single origin provides it can anchor SceneObjects to SpatialAnchors, or generate several scenes and merge them together, but for simplicity we assume that watertight scenes exist in their own origin that's localized by one NodeId defined by Scene.OriginSpatialGraphNodeId.</span></span>

<span data-ttu-id="936c0-263">Il codice Unity seguente, ad esempio, Mostra come usare la percezione di Windows e le API Unity per allineare i sistemi di coordinate.</span><span class="sxs-lookup"><span data-stu-id="936c0-263">The following Unity code, for example, shows how to use Windows Perception and Unity APIs to align coordinate systems together.</span></span> <span data-ttu-id="936c0-264">Vedere [SpatialCoordinateSystem](https://docs.microsoft.com//uwp/api/windows.perception.spatial.spatialcoordinatesystem) e [SpatialGraphInteropPreview](https://docs.microsoft.com//uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview) per informazioni dettagliate sulle API di percezione di Windows e sugli [oggetti nativi della realtà mista in Unity](https://docs.microsoft.com//windows/mixed-reality/unity-xrdevice-advanced) per informazioni dettagliate su come ottenere un SpatialCoordinateSystem che corrisponda all'origine mondiale di Unity.</span><span class="sxs-lookup"><span data-stu-id="936c0-264">See [SpatialCoordinateSystem](https://docs.microsoft.com//uwp/api/windows.perception.spatial.spatialcoordinatesystem) and [SpatialGraphInteropPreview](https://docs.microsoft.com//uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview) for details on the Windows Perception APIs, and [Mixed Reality native objects in Unity](https://docs.microsoft.com//windows/mixed-reality/unity-xrdevice-advanced) for details on obtaining a SpatialCoordinateSystem that corresponds to Unity's world origin.</span></span>

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

<span data-ttu-id="936c0-265">Ogni `SceneObject` ha una trasformazione, che viene quindi applicata a tale oggetto.</span><span class="sxs-lookup"><span data-stu-id="936c0-265">Each `SceneObject` has a transform, which is then applied to that object.</span></span> <span data-ttu-id="936c0-266">In Unity si converte in coordinate corrette e si assegnano trasformazioni locali come segue:</span><span class="sxs-lookup"><span data-stu-id="936c0-266">In Unity we convert to right handed coordinates and assign local transforms as so:</span></span>

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

### <a name="quad"></a><span data-ttu-id="936c0-267">Quad</span><span class="sxs-lookup"><span data-stu-id="936c0-267">Quad</span></span>

<span data-ttu-id="936c0-268">I quad sono stati progettati per aiutare gli scenari di selezione host 2D e dovrebbero essere considerati estensioni per gli elementi UX di Canvas 2D.</span><span class="sxs-lookup"><span data-stu-id="936c0-268">Quads were designed to help 2D placement scenarios and should be thought of as extensions to 2D canvas UX elements.</span></span> <span data-ttu-id="936c0-269">Mentre i quad sono componenti di SceneObjects e possono essere sottoposti a rendering in 3D, le API quadre presuppongono quad sono strutture 2D.</span><span class="sxs-lookup"><span data-stu-id="936c0-269">While Quads are components of SceneObjects and can be rendered in 3D, the Quad APIs themselves assume Quads are 2D structures.</span></span> <span data-ttu-id="936c0-270">Offrono informazioni come extent, Shape e forniscono API per la selezione host.</span><span class="sxs-lookup"><span data-stu-id="936c0-270">They offer information such as extent, shape, and provide APIs for placement.</span></span>

<span data-ttu-id="936c0-271">I quad hanno extent rettangolari, ma rappresentano superfici 2D a forma arbitraria.</span><span class="sxs-lookup"><span data-stu-id="936c0-271">Quads have rectangular extents, but they represent arbitrarily shaped 2D surfaces.</span></span> <span data-ttu-id="936c0-272">Per abilitare la selezione host in queste superfici 2D che interagiscono con i quad dell'ambiente 3D offrono utilità per rendere possibile questa interazione.</span><span class="sxs-lookup"><span data-stu-id="936c0-272">To enable placement on these 2D surfaces that interact with the 3D environment quads offer utilities to make this interaction possible.</span></span> <span data-ttu-id="936c0-273">Attualmente la comprensione della scena fornisce due funzioni di questo tipo: _ *FindCentermostPlacement*\* e **GetSurfaceMask**.</span><span class="sxs-lookup"><span data-stu-id="936c0-273">Currently Scene Understanding provides two such functions, _ *FindCentermostPlacement*\* and **GetSurfaceMask**.</span></span> <span data-ttu-id="936c0-274">FindCentermostPlacement è un'API di alto livello che individua una posizione nel quad in cui è possibile posizionare un oggetto e tenterà di individuare la posizione migliore per l'oggetto, garantendo che il rettangolo di delimitazione fornito rimarrà sulla superficie sottostante.</span><span class="sxs-lookup"><span data-stu-id="936c0-274">FindCentermostPlacement is a high-level API that locates a position on the quad where an object can be placed and will try to find the best location for your object guaranteeing that the bounding box you provide will stay on the underlying surface.</span></span>

> [!NOTE]
> <span data-ttu-id="936c0-275">Le coordinate dell'output sono relative al quad in "Quad Space" con l'angolo superiore sinistro (x = 0, y = 0), esattamente come per gli altri tipi Rect di Windows.</span><span class="sxs-lookup"><span data-stu-id="936c0-275">The coordinates of the output are relative to the quad in "quad space" with the top left corner being (x = 0, y = 0), just as it would be with other windows Rect types.</span></span> <span data-ttu-id="936c0-276">Assicurarsi di tenere conto di questo quando si lavora con le origini dei propri oggetti.</span><span class="sxs-lookup"><span data-stu-id="936c0-276">Be sure to take this into account when working with the origins of your own objects.</span></span> 

<span data-ttu-id="936c0-277">Nell'esempio seguente viene illustrato come trovare la posizione posizionabile effettuare e come ancorare un ologramma al quad.</span><span class="sxs-lookup"><span data-stu-id="936c0-277">The following example shows how to find the centermost placeable location and anchor a hologram to the quad.</span></span>

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

<span data-ttu-id="936c0-278">I passaggi 1-4 dipendono in modo estremamente da un particolare Framework/implementazione, ma i temi dovrebbero essere simili.</span><span class="sxs-lookup"><span data-stu-id="936c0-278">Steps 1-4 are highly dependent on your particular framework/implementation, but the themes should be similar.</span></span> <span data-ttu-id="936c0-279">È importante notare che il quad rappresenta semplicemente un piano 2D con binding localizzato nello spazio.</span><span class="sxs-lookup"><span data-stu-id="936c0-279">It's important to note that the Quad simply represents a bounded 2D plane that is localized in space.</span></span> <span data-ttu-id="936c0-280">Se il motore/Framework sa dove si trova il quad e si radicano gli oggetti rispetto al quad, gli ologrammi saranno posizionati correttamente rispetto al mondo reale.</span><span class="sxs-lookup"><span data-stu-id="936c0-280">By having your engine/framework know where the quad is and rooting your objects relative to the quad, your holograms will be located correctly with respect to the real world.</span></span> 

<!-- 
// TODO: Add sample link when released
For more detailed information please see our samples on quads which show specific implementations.
-->

### <a name="mesh"></a><span data-ttu-id="936c0-281">Mesh</span><span class="sxs-lookup"><span data-stu-id="936c0-281">Mesh</span></span>

<span data-ttu-id="936c0-282">Le mesh rappresentano rappresentazioni geometriche di oggetti o ambienti.</span><span class="sxs-lookup"><span data-stu-id="936c0-282">Meshes represent geometric representations of objects or environments.</span></span> <span data-ttu-id="936c0-283">In modo analogo al [mapping spaziale](../../design/spatial-mapping.md), i dati relativi a indici mesh e vertici forniti con ogni mesh di superficie spaziale utilizzano lo stesso layout familiare dei vertex buffer e degli indici utilizzati per il rendering di mesh triangolari in tutte le moderne API per il rendering.</span><span class="sxs-lookup"><span data-stu-id="936c0-283">Much like [spatial mapping](../../design/spatial-mapping.md), mesh index and vertex data provided with each spatial surface mesh uses the same familiar layout as the vertex and index buffers that are used for rendering triangle meshes in all modern rendering APIs.</span></span> <span data-ttu-id="936c0-284">Le posizioni dei vertici sono disponibili nel sistema di coordinate di `Scene` .</span><span class="sxs-lookup"><span data-stu-id="936c0-284">Vertex positions are provided in the coordinate system of the `Scene`.</span></span> <span data-ttu-id="936c0-285">Le API specifiche usate per fare riferimento a questi dati sono le seguenti:</span><span class="sxs-lookup"><span data-stu-id="936c0-285">The specific APIs used to reference this data are as follows:</span></span>

```cs
void GetTriangleIndices(int[] indices);
void GetVertices(System.Numerics.Vector3[] vertices);
```

<span data-ttu-id="936c0-286">Il codice seguente fornisce un esempio di generazione di un elenco di triangolo dalla struttura mesh:</span><span class="sxs-lookup"><span data-stu-id="936c0-286">The following code provides an example of generating a triangle list from the mesh structure:</span></span>

```cs
uint[] indices = new uint[mesh.TriangleIndexCount];
System.Numerics.Vector3[] positions = new System.Numerics.Vector3[mesh.VertexCount];

mesh.GetTriangleIndices(indices);
mesh.GetVertexPositions(positions);
```

<span data-ttu-id="936c0-287">I buffer di indice/vertice devono essere >= i conteggi di indice/vertice, ma in caso contrario possono essere dimensionati arbitrariamente, consentendo un utilizzo efficiente della memoria.</span><span class="sxs-lookup"><span data-stu-id="936c0-287">The index/vertex buffers must be >= the index/vertex counts, but otherwise can be arbitrarily sized allowing for efficient memory reuse.</span></span>

### <a name="collidermesh"></a><span data-ttu-id="936c0-288">ColliderMesh</span><span class="sxs-lookup"><span data-stu-id="936c0-288">ColliderMesh</span></span>

<span data-ttu-id="936c0-289">Gli oggetti scena consentono di accedere ai dati mesh mesh e Collider mesh tramite le proprietà mesh e ColliderMeshes.</span><span class="sxs-lookup"><span data-stu-id="936c0-289">Scene objects provide access to mesh and collider mesh data via the Meshes and ColliderMeshes properties.</span></span> <span data-ttu-id="936c0-290">Queste mesh corrisponderanno sempre, ovvero l'indice volto della della proprietà Meshes rappresenta la stessa geometria dell'indice volto della della proprietà ColliderMeshes.</span><span class="sxs-lookup"><span data-stu-id="936c0-290">These meshes will always match, meaning that the i'th index of the Meshes property represents the same geometry as the i'th index of the ColliderMeshes property.</span></span> <span data-ttu-id="936c0-291">Se il runtime/oggetto supporta le mesh di Collider, si ha la certezza di ottenere il poligono più basso, l'approssimazione dell'ordine più elevato ed è consigliabile usare ColliderMeshes laddove l'applicazione userà i Collider.</span><span class="sxs-lookup"><span data-stu-id="936c0-291">If the runtime/object supports collider meshes, you are guaranteed to get the lowest polygon, highest order approximation and it's good practice to use ColliderMeshes wherever your application would use colliders.</span></span> <span data-ttu-id="936c0-292">Se il sistema non supporta i Collider, l'oggetto mesh restituito in ColliderMeshes sarà lo stesso oggetto della mesh che riduce i vincoli di memoria.</span><span class="sxs-lookup"><span data-stu-id="936c0-292">If the system does not support colliders the Mesh object returned in ColliderMeshes will be the same object as the mesh reducing memory constraints.</span></span>

## <a name="developing-with-scene-understanding"></a><span data-ttu-id="936c0-293">Sviluppo con comprensione della scena</span><span class="sxs-lookup"><span data-stu-id="936c0-293">Developing with scene understanding</span></span>

<span data-ttu-id="936c0-294">A questo punto, è necessario comprendere i componenti di base della scena Understanding Runtime and SDK.</span><span class="sxs-lookup"><span data-stu-id="936c0-294">At this point, you should understand the core building blocks of the scene understanding runtime and SDK.</span></span> <span data-ttu-id="936c0-295">La maggior parte della potenza e della complessità si basa sui modelli di accesso, sull'interazione con i framework 3D e sugli strumenti che possono essere scritti su queste API per eseguire attività più avanzate, come la pianificazione spaziale, l'analisi delle stanze, la navigazione, la fisica e così via.</span><span class="sxs-lookup"><span data-stu-id="936c0-295">The bulk of the power and complexity lies in access patterns, interaction with 3D frameworks, and tools that can be written on top of these APIs to do more advanced tasks like spatial planning, room analysis, navigation, physics, and so on.</span></span> <span data-ttu-id="936c0-296">Ci auguriamo che questi esempi vengano acquisiti in esempi che dovrebbero guidare l'utente nella direzione corretta per rendere più brillanti gli scenari.</span><span class="sxs-lookup"><span data-stu-id="936c0-296">We hope to capture these in samples that should hopefully guide you in the proper direction to make your scenarios shine.</span></span> <span data-ttu-id="936c0-297">Se sono presenti esempi o scenari che non sono stati indirizzati, è possibile inviarli e provare a documentare/prototipare gli elementi necessari.</span><span class="sxs-lookup"><span data-stu-id="936c0-297">If there are samples or scenarios we aren't addressing, let us know and we'll try to document/prototype what you need.</span></span>

### <a name="where-can-i-get-sample-code"></a><span data-ttu-id="936c0-298">Dove è possibile ottenere il codice di esempio?</span><span class="sxs-lookup"><span data-stu-id="936c0-298">Where can I get sample code?</span></span>

<span data-ttu-id="936c0-299">Scenario per informazioni sul codice di esempio per Unity, vedere la pagina di [esempio Unity](https://github.com/sceneunderstanding-microsoft/unitysample) .</span><span class="sxs-lookup"><span data-stu-id="936c0-299">Scene Understanding sample code for Unity can be found on our [Unity Sample Page](https://github.com/sceneunderstanding-microsoft/unitysample) page.</span></span> <span data-ttu-id="936c0-300">Questa applicazione consente di comunicare con il dispositivo ed eseguire il rendering dei vari oggetti scena, oppure di caricare una scena serializzata nel PC e di sperimentare la comprensione della scena senza un dispositivo.</span><span class="sxs-lookup"><span data-stu-id="936c0-300">This application will allow you to communicate with your device and render the various scene objects, or, it will allow you to load a serialized scene on your PC and allow you to experience Scene Understanding without a device.</span></span>

### <a name="where-can-i-get-sample-scenes"></a><span data-ttu-id="936c0-301">Dove è possibile ottenere scene di esempio?</span><span class="sxs-lookup"><span data-stu-id="936c0-301">Where can I get sample scenes?</span></span>

<span data-ttu-id="936c0-302">Se si dispone di un HoloLens2, è possibile salvare qualsiasi scena acquisita salvando l'output di ComputeSerializedAsync in file e deserializzarlo in base alla propria convenienza.</span><span class="sxs-lookup"><span data-stu-id="936c0-302">If you have a HoloLens2, you can save any scene you've captured by saving the output of ComputeSerializedAsync to file and deserializing it at your own convenience.</span></span> 

<span data-ttu-id="936c0-303">Se non si ha un dispositivo HoloLens2 ma si vuole giocare con la comprensione della scena, è necessario scaricare una scena pre-acquisita.</span><span class="sxs-lookup"><span data-stu-id="936c0-303">If you don't have a HoloLens2 device but want to play with Scene Understanding, you'll need to download a pre-captured scene.</span></span> <span data-ttu-id="936c0-304">L'esempio di comprensione della scena è attualmente fornito con scene serializzate che possono essere scaricate e usate con facilità.</span><span class="sxs-lookup"><span data-stu-id="936c0-304">The Scene Understanding sample currently ships with serialized scenes that can be downloaded and used at your own convenience.</span></span> <span data-ttu-id="936c0-305">È possibile trovarli qui:</span><span class="sxs-lookup"><span data-stu-id="936c0-305">You can find them here:</span></span>

[<span data-ttu-id="936c0-306">Scene di esempio sulla comprensione della scena</span><span class="sxs-lookup"><span data-stu-id="936c0-306">Scene Understanding Sample Scenes</span></span>](https://github.com/microsoft/MixedReality-SceneUnderstanding-Samples/tree/master/Assets/Resources/SerializedScenesForPCPath)

## <a name="see-also"></a><span data-ttu-id="936c0-307">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="936c0-307">See also</span></span>

* [<span data-ttu-id="936c0-308">Mapping spaziale</span><span class="sxs-lookup"><span data-stu-id="936c0-308">Spatial mapping</span></span>](../../design/spatial-mapping.md)
* [<span data-ttu-id="936c0-309">Informazioni sulle scene</span><span class="sxs-lookup"><span data-stu-id="936c0-309">Scene understanding</span></span>](../../design/scene-understanding.md)
* [<span data-ttu-id="936c0-310">Esempio di Unity</span><span class="sxs-lookup"><span data-stu-id="936c0-310">Unity Sample</span></span>](https://github.com/microsoft/MixedReality-SceneUnderstanding-Samples)

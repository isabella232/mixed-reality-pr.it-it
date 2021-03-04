---
title: Feature_Contribution_Process
description: documentazione per l'aggiunta di funzionalità a MRTK.
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: da91e42abe39ced0939e328f340e6340b8b1d9d9
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/03/2021
ms.locfileid: "101782276"
---
# <a name="feature-contribution-process"></a><span data-ttu-id="91384-104">Processo di contributo delle funzionalità</span><span class="sxs-lookup"><span data-stu-id="91384-104">Feature contribution process</span></span>

> [!WARNING]
> <span data-ttu-id="91384-105">10/1/2019: Questa pagina è deprecata perché fornisce linee guida per contribuire ai sistemi di grandi dimensioni a MRTK prima della versione 2,0.</span><span class="sxs-lookup"><span data-stu-id="91384-105">10/1/2019: This page is deprecated because it provides guidelines for contributing very large systems to MRTK before the 2.0 release.</span></span> <span data-ttu-id="91384-106">Dopo la versione 2,0, le modifiche di grandi dimensioni devono essere eseguite con maggiore attenzione e il processo per questa operazione non è ancora stato deciso.</span><span class="sxs-lookup"><span data-stu-id="91384-106">After the 2.0 release, large changes need to be performed more carefully, and the process for this is not yet decided.</span></span> <span data-ttu-id="91384-107">Si prevede che la maggior parte dei contributi MRTK abbia modifiche molto più piccole rispetto a quanto illustrato qui.</span><span class="sxs-lookup"><span data-stu-id="91384-107">We expect most MRTK contributions to have much smaller changes than what is covered here.</span></span>

<span data-ttu-id="91384-108">L'aggiunta di funzionalità al Toolkit di realtà mista (MRTK) è suddivisa in alcuni passaggi di iterazione, quindi i gestori possono avere tempo per rivedere e garantire la corretta esecuzione del processo.</span><span class="sxs-lookup"><span data-stu-id="91384-108">Adding features to the Mixed Reality Toolkit (MRTK) is split up into a few iteration steps, so maintainers can have time to review and and ensure the process goes smoothly.</span></span> <span data-ttu-id="91384-109">Prima di iniziare, assicurarsi di esaminare l'elenco dei [requisiti delle funzionalità](#new-feature-requirements) .</span><span class="sxs-lookup"><span data-stu-id="91384-109">Please be sure to review the list of [feature requirements](#new-feature-requirements) before you get started.</span></span>

## <a name="process"></a><span data-ttu-id="91384-110">Processo</span><span class="sxs-lookup"><span data-stu-id="91384-110">Process</span></span>

<span data-ttu-id="91384-111">Il processo seguente è stato elaborato per garantire che tutti i nuovi lavori siano conformi agli standard e all'architettura aggiornati definiti per MRTK, che sono stati definiti come segue:</span><span class="sxs-lookup"><span data-stu-id="91384-111">The following process has been drafted to ensure all new work complies to the updated standards and architecture defined for the MRTK, this has been defined as:</span></span>

1. [<span data-ttu-id="91384-112">Aprire una nuova proposta e le attività correlate</span><span class="sxs-lookup"><span data-stu-id="91384-112">Open a new Proposal and related Tasks</span></span>](#new-proposal)
2. [<span data-ttu-id="91384-113">Inviare una bozza o una struttura dell'architettura</span><span class="sxs-lookup"><span data-stu-id="91384-113">Submit an Architecture Draft or Outline</span></span>](#architecture-draft)
3. [<span data-ttu-id="91384-114">Esaminare e finalizzare la documentazione dell'architettura</span><span class="sxs-lookup"><span data-stu-id="91384-114">Review and finalize the Architecture documentation</span></span>](#architecture-documentation)
4. [<span data-ttu-id="91384-115">Inviare una richiesta pull implementando le interfacce delle funzionalità di base e il riferimento all'evento (se applicabile)</span><span class="sxs-lookup"><span data-stu-id="91384-115">Submit a PR implementing the Core feature interfaces and event datum (if applicable)</span></span>](#core-implementation)
5. [<span data-ttu-id="91384-116">Inviare una richiesta pull per implementare gli eventuali componenti SDK necessari</span><span class="sxs-lookup"><span data-stu-id="91384-116">Submit a PR Implementing any required SDK components</span></span>](#sdk-implementation)
6. [<span data-ttu-id="91384-117">Inviare una richiesta pull che implementa demo di funzionalità o esempi di scalabilità completa</span><span class="sxs-lookup"><span data-stu-id="91384-117">Submit a PR Implementing feature demos or full scale Examples</span></span>](#example-implementation)

### <a name="new-proposal"></a><span data-ttu-id="91384-118">Nuova proposta</span><span class="sxs-lookup"><span data-stu-id="91384-118">New proposal</span></span>

<span data-ttu-id="91384-119">Per iniziare, aprire una nuova proposta o un'attività che descrive la funzionalità o il problema che si vuole risolvere.</span><span class="sxs-lookup"><span data-stu-id="91384-119">Start by opening a new Proposal or Task describing the feature or the problem you want to solve.</span></span> <span data-ttu-id="91384-120">Descrivere l'approccio e il modo in cui si inserisce nella versione del Toolkit di realtà mista di destinazione.</span><span class="sxs-lookup"><span data-stu-id="91384-120">Describe the approach and how it fits into the version of the Mixed Reality Toolkit you're targeting.</span></span> <span data-ttu-id="91384-121">Questo consentirà a tutti di discutere sulla proposta e, eventualmente, di identificare alcuni potenziali problemi prima dell'avvio di qualsiasi lavoro.</span><span class="sxs-lookup"><span data-stu-id="91384-121">This will enable everyone have a discussion about the proposal and, hopefully, identify some potential pitfalls before any work is started.</span></span>

<span data-ttu-id="91384-122">Le nuove proposte verranno esaminate e discusse durante le riunioni settimanali della spedizione e se viene accettata una proposta, verranno create e assegnate attività aggiuntive.</span><span class="sxs-lookup"><span data-stu-id="91384-122">New Proposals will be reviewed and discussed during our weekly ship room meetings and if a proposal is accepted, supplemental tasks will then be created and assigned.</span></span>

### <a name="architecture-draft"></a><span data-ttu-id="91384-123">Bozza di architettura</span><span class="sxs-lookup"><span data-stu-id="91384-123">Architecture draft</span></span>

<span data-ttu-id="91384-124">La prima attività dopo che la proposta iniziale è stata accettata, sarà la bozza del documento di architettura iniziale per la funzionalità o il lavoro da eseguire.</span><span class="sxs-lookup"><span data-stu-id="91384-124">The first task once the initial proposal has been accepted, will be to draft the initial architecture document for the feature or work to be done.</span></span> <span data-ttu-id="91384-125">Questo documento deve essere in genere costituito da una o due pagine e include una panoramica di alto livello della funzionalità e il modo in cui sarà correlato ad altre parti del Toolkit di realtà mista.</span><span class="sxs-lookup"><span data-stu-id="91384-125">This document should typically be one or two pages long and include a high level overview of the feature and how it will relate to other parts of the Mixed Reality Toolkit.</span></span>

* <span data-ttu-id="91384-126">Il progetto deve essere facile da utilizzare con le aree principali evidenziate.</span><span class="sxs-lookup"><span data-stu-id="91384-126">The draft must be easy to consume with key areas highlighted.</span></span>
* <span data-ttu-id="91384-127">La bozza deve includere un elenco di interfacce di base proposte, profili di configurazione e Datum di evento.</span><span class="sxs-lookup"><span data-stu-id="91384-127">The draft must include a list of the proposed core interfaces, configuration profiles, and event datum.</span></span>
* <span data-ttu-id="91384-128">Il progetto deve includere una semplice rappresentazione grafica dell'architettura proposta.</span><span class="sxs-lookup"><span data-stu-id="91384-128">The draft must include a simple graphic of the proposed architecture.</span></span>

<span data-ttu-id="91384-129">Assicurarsi che l'architettura della funzionalità sia conforme ai [nuovi requisiti di funzionalità](#new-feature-requirements) impostati dall'architettura MRTK di base.</span><span class="sxs-lookup"><span data-stu-id="91384-129">Ensure that the architecture of the feature complies with the [New Feature Requirements](#new-feature-requirements) set out by the Core MRTK architecture.</span></span>

><span data-ttu-id="91384-130">TODO: aggiungere un collegamento al modello bozza dell'architettura</span><span class="sxs-lookup"><span data-stu-id="91384-130">TODO: Add link to architecture draft template</span></span>

<span data-ttu-id="91384-131">Al termine della bozza, questo può essere aggiunto al problema della proposta/attività in GitHub per la revisione finale pubblica.</span><span class="sxs-lookup"><span data-stu-id="91384-131">Once the draft is completed, this can be appended to the Proposal / Task issue on GitHub for final public review.</span></span>

### <a name="architecture-documentation"></a><span data-ttu-id="91384-132">Documentazione sull'architettura</span><span class="sxs-lookup"><span data-stu-id="91384-132">Architecture documentation</span></span>

<span data-ttu-id="91384-133">Una volta accettata l'architettura bozza, è possibile effettuare richieste pull aggiuntive per inviare i documenti di architettura completa finale al repository.</span><span class="sxs-lookup"><span data-stu-id="91384-133">Once the draft architecture is accepted, additional pull requests can be made to submit the final full architecture documents to the repository.</span></span>

><span data-ttu-id="91384-134">TODO: aggiungere un collegamento al modello di architettura completo</span><span class="sxs-lookup"><span data-stu-id="91384-134">TODO: Add link to the full architecture template</span></span>

<span data-ttu-id="91384-135">Una volta approvato il documento di architettura, possono essere eseguiti solo i primi invii di codice.</span><span class="sxs-lookup"><span data-stu-id="91384-135">Once the architecture document is approved, only then can the first code submissions can be made.</span></span>

<span data-ttu-id="91384-136">Lo sviluppo può iniziare nel ramo privato e essere completato normalmente. Tuttavia, le richieste pull di riferimento al progetto MRTK di base devono essere inviate in fasi per garantire che la revisione e l'approvazione siano uniformi, e che le modifiche di base non influiscano sulle altre funzionalità.</span><span class="sxs-lookup"><span data-stu-id="91384-136">Development can begin in your own private branch and complete as normal, however, the PR's submitted back to the core MRTK project should be submitted in stages to ensure the review and approval is as smooth as it can be (and ensure core changes do not impact other features)</span></span>

### <a name="core-implementation"></a><span data-ttu-id="91384-137">Implementazione di base</span><span class="sxs-lookup"><span data-stu-id="91384-137">Core implementation</span></span>

<span data-ttu-id="91384-138">Il lavoro iniziale da inviare consiste nell'implementare:</span><span class="sxs-lookup"><span data-stu-id="91384-138">The initial work that should be submitted, is to implement:</span></span>

* <span data-ttu-id="91384-139">Definizioni</span><span class="sxs-lookup"><span data-stu-id="91384-139">Definitions</span></span>
* <span data-ttu-id="91384-140">Interfacce</span><span class="sxs-lookup"><span data-stu-id="91384-140">Interfaces</span></span>
* <span data-ttu-id="91384-141">Profili di configurazione</span><span class="sxs-lookup"><span data-stu-id="91384-141">Configuration profiles</span></span>
* <span data-ttu-id="91384-142">Dati dell'evento</span><span class="sxs-lookup"><span data-stu-id="91384-142">Event data</span></span>

<span data-ttu-id="91384-143">Se necessario, è possibile aggiornare il documento di architettura per allinearlo alle modifiche apportate all'implementazione.</span><span class="sxs-lookup"><span data-stu-id="91384-143">If needed, the architectural document can be updated to align with any changes to the implementation.</span></span>

<span data-ttu-id="91384-144">Assicurarsi che tutti gli unit test esistenti e tutti i nuovi test vengano superati prima dell'invio.</span><span class="sxs-lookup"><span data-stu-id="91384-144">Please ensure that all existing Unit Tests and any new tests are all passing prior to submission.</span></span>

### <a name="sdk-implementation"></a><span data-ttu-id="91384-145">Implementazione di SDK</span><span class="sxs-lookup"><span data-stu-id="91384-145">SDK implementation</span></span>

<span data-ttu-id="91384-146">Una volta che gli eventi e le interfacce principali vengono uniti allo sviluppo, è possibile inviare lavoro per i componenti SDK.</span><span class="sxs-lookup"><span data-stu-id="91384-146">Once the core interfaces and events are merged in to development, work can then be submitted for the SDK components.</span></span>  <span data-ttu-id="91384-147">Aggiunta dell'implementazione concreta della funzionalità e test sulle piattaforme e unit test supportati.</span><span class="sxs-lookup"><span data-stu-id="91384-147">Adding the concrete implementation of the feature and testing against the supported platforms and unit tests.</span></span>

### <a name="example-implementation"></a><span data-ttu-id="91384-148">Implementazione di esempio</span><span class="sxs-lookup"><span data-stu-id="91384-148">Example implementation</span></span>

<span data-ttu-id="91384-149">Una volta che i componenti SDK sono Stati Uniti, è possibile inviare qualsiasi scena demo o aggiornamento alle scene di esempio.</span><span class="sxs-lookup"><span data-stu-id="91384-149">Once the SDK components are merged, then any demo scenes or updates to the example scenes can be submitted.</span></span>

* <span data-ttu-id="91384-150">Demo per evidenziare funzionalità e dimostrazione specifiche</span><span class="sxs-lookup"><span data-stu-id="91384-150">Demos are for specific feature highlighting and demonstration</span></span>
* <span data-ttu-id="91384-151">Esempi sono esempi di apprendimento della scena di lavoro completo</span><span class="sxs-lookup"><span data-stu-id="91384-151">Examples are full working scene learning examples</span></span>

## <a name="new-feature-requirements"></a><span data-ttu-id="91384-152">Nuovi requisiti delle funzionalità</span><span class="sxs-lookup"><span data-stu-id="91384-152">New feature requirements</span></span>

<span data-ttu-id="91384-153">La maggior parte delle implementazioni delle funzionalità può essere suddivisa in tre parti principali:</span><span class="sxs-lookup"><span data-stu-id="91384-153">Most feature implementations can be broken down into 3 main parts:</span></span>

1. [<span data-ttu-id="91384-154">Gestione funzionalità</span><span class="sxs-lookup"><span data-stu-id="91384-154">The Feature Manager</span></span>](#manager-implementation-requirements)
2. <span data-ttu-id="91384-155">[Dati dell'evento](#event-data-implementation-requirements) (facoltativo)</span><span class="sxs-lookup"><span data-stu-id="91384-155">[The Event Data](#event-data-implementation-requirements) (Optional)</span></span>
3. <span data-ttu-id="91384-156">[Gestore di funzionalità](#handler-implementation-requirements) (facoltativo)</span><span class="sxs-lookup"><span data-stu-id="91384-156">[The Feature Handler](#handler-implementation-requirements) (Optional)</span></span>

### <a name="manager-implementation-requirements"></a><span data-ttu-id="91384-157">Requisiti di implementazione del responsabile</span><span class="sxs-lookup"><span data-stu-id="91384-157">Manager implementation requirements</span></span>

* <span data-ttu-id="91384-158">Definizioni di assembly per il codice esterno alla `MRTK/Core` cartella.</span><span class="sxs-lookup"><span data-stu-id="91384-158">Assembly Definitions for code outside of the `MRTK/Core` folder.</span></span>
  * <span data-ttu-id="91384-159">In questo modo le funzionalità sono indipendenti e non hanno dipendenze con altre funzionalità.</span><span class="sxs-lookup"><span data-stu-id="91384-159">This ensures features are self-contained and have no dependencies to other features.</span></span>
* <span data-ttu-id="91384-160">Essere definito utilizzando un'interfaccia presente in `MRTK/Core/Definitions/<FeatureName>System` .</span><span class="sxs-lookup"><span data-stu-id="91384-160">Be defined using an interface found in `MRTK/Core/Definitions/<FeatureName>System`.</span></span>
* <span data-ttu-id="91384-161">Un'implementazione di gestione concreta di una funzionalità deve ereditare direttamente da `BaseManager` o `MixedRealityEventManager` se genera eventi.</span><span class="sxs-lookup"><span data-stu-id="91384-161">A feature's concrete manager implementation should inherit directly from `BaseManager` or `MixedRealityEventManager` if they will raise events.</span></span>
* <span data-ttu-id="91384-162">Un'implementazione di gestione concreta di una funzionalità dovrebbe configurare e verificare che la scena sia pronta per il sistema in uso in `Initialize` .</span><span class="sxs-lookup"><span data-stu-id="91384-162">A feature's concrete manager implementation should setup and verify that the scene is ready for that system to use in `Initialize`.</span></span>
* <span data-ttu-id="91384-163">Un responsabile concreto di una funzionalità dovrebbe anche pulire dopo aver rimosso qualsiasi elemento creato nella scena in `Destroy` .</span><span class="sxs-lookup"><span data-stu-id="91384-163">A feature's concrete manager should also clean up after themselves removing anything created in the scene in `Destroy`.</span></span>
* <span data-ttu-id="91384-164">Essere registrato con il responsabile della realtà mista.</span><span class="sxs-lookup"><span data-stu-id="91384-164">Be registered with the Mixed Reality Manager.</span></span>
  * <span data-ttu-id="91384-165">Se la funzionalità è una funzionalità di base, deve essere codificata in `MixedRealityToolkit` e `CoreServices` e aggiunta a `MixedRealityConfigurationProfile` .</span><span class="sxs-lookup"><span data-stu-id="91384-165">If the feature is a core feature, this should be hard coded into the `MixedRealityToolkit` and `CoreServices` and added to the `MixedRealityConfigurationProfile`.</span></span>
    * <span data-ttu-id="91384-166">Ciò include la possibilità di specificare un'implementazione concreta tramite l'elenco a discesa usando `SystemType` .</span><span class="sxs-lookup"><span data-stu-id="91384-166">This includes being able to specify a concrete implementation via dropdown using `SystemType`.</span></span>
    * <span data-ttu-id="91384-167">Le funzionalità devono disporre di un profilo di configurazione che deriva da un oggetto con script.</span><span class="sxs-lookup"><span data-stu-id="91384-167">Features should have a configuration profile that derives from a scriptable object.</span></span>
    * <span data-ttu-id="91384-168">Un profilo di configurazione predefinito che si trova in `MRTK/SDK/Profiles` e deve essere assegnato nel profilo di configurazione predefinito per il gestore di realtà misto</span><span class="sxs-lookup"><span data-stu-id="91384-168">A default configuration profile located in `MRTK/SDK/Profiles` and be assigned in the default configuration profile for the Mixed Reality Manager</span></span>
  * <span data-ttu-id="91384-169">Se questa funzionalità **non** è una funzionalità di base, è necessario registrarla utilizzando il profilo di configurazione del servizio di estensione e implementare `IMixedRealityExtensionService` .</span><span class="sxs-lookup"><span data-stu-id="91384-169">If this feature is **not** a core feature, then it must be registered using the extension service configuration profile and implement `IMixedRealityExtensionService`.</span></span>
* <span data-ttu-id="91384-170">In è disponibile un'implementazione predefinita `MRTK/Services/<FeatureName>`</span><span class="sxs-lookup"><span data-stu-id="91384-170">Have a default implementation located in `MRTK/Services/<FeatureName>`</span></span>
* <span data-ttu-id="91384-171">Gli eventi che possono essere generati con il sistema devono essere definiti nell'interfaccia, con tutti i parametri obbligatori per inizializzare i dati dell'evento.</span><span class="sxs-lookup"><span data-stu-id="91384-171">Events that can be raised with the system should be defined in the interface, with all the required parameters for initializing the event data.</span></span>

### <a name="event-data-implementation-requirements"></a><span data-ttu-id="91384-172">Requisiti di implementazione dei dati degli eventi</span><span class="sxs-lookup"><span data-stu-id="91384-172">Event data implementation requirements</span></span>

<span data-ttu-id="91384-173">I dati dell'evento definiscono esattamente quali dati devono essere ricevuti dal gestore dall'evento.</span><span class="sxs-lookup"><span data-stu-id="91384-173">The Event Data defines exactly what data the handler is expected to receive from the event.</span></span>

* <span data-ttu-id="91384-174">Tutti i riferimenti all'evento per la funzionalità devono essere definiti in `MixedRealityToolkit/EventDatum/<FeatureName>` .</span><span class="sxs-lookup"><span data-stu-id="91384-174">All Event Datum for the feature should be defined in `MixedRealityToolkit/EventDatum/<FeatureName>`.</span></span>
* <span data-ttu-id="91384-175">Tutte le nuove classi di dati degli eventi devono ereditare da `GenericBaseEventData`</span><span class="sxs-lookup"><span data-stu-id="91384-175">All new Event Data classes should inherit from `GenericBaseEventData`</span></span>

### <a name="handler-implementation-requirements"></a><span data-ttu-id="91384-176">Requisiti di implementazione del gestore</span><span class="sxs-lookup"><span data-stu-id="91384-176">Handler implementation requirements</span></span>

<span data-ttu-id="91384-177">L'interfaccia del gestore definisce ogni evento di cui un componente deve essere in ascolto e i tipi di dati passati.</span><span class="sxs-lookup"><span data-stu-id="91384-177">The Handler Interface defines each event a component should be listening for and the types of data passed.</span></span> <span data-ttu-id="91384-178">Gli utenti finali implementeranno l'interfaccia per eseguire la logica in base ai dati degli eventi ricevuti.</span><span class="sxs-lookup"><span data-stu-id="91384-178">End users will implement the interface to execute logic based on the event data received.</span></span>

* <span data-ttu-id="91384-179">Le interfacce del gestore devono essere definite in `MixedRealityToolkit/Interfaces/<FeatureName>System/Handlers` .</span><span class="sxs-lookup"><span data-stu-id="91384-179">Handler interfaces should be defined in `MixedRealityToolkit/Interfaces/<FeatureName>System/Handlers`.</span></span>
* <span data-ttu-id="91384-180">Le interfacce del gestore devono ereditare da `UnityEngine.EventSystems.IEventSystemHandler`</span><span class="sxs-lookup"><span data-stu-id="91384-180">Handler interfaces should inherit from `UnityEngine.EventSystems.IEventSystemHandler`</span></span>
* <span data-ttu-id="91384-181">Per impostazione predefinita, acconsentire esplicitamente.</span><span class="sxs-lookup"><span data-stu-id="91384-181">Opt-in by default.</span></span> <span data-ttu-id="91384-182">Per ricevere gli eventi dal sistema, è necessario che il gestore si registri con il sistema per la ricezione degli eventi.</span><span class="sxs-lookup"><span data-stu-id="91384-182">To receive events from the system, the handler will need to register itself with the system to receive those events.</span></span>

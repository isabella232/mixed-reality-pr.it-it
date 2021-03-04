---
title: MRTK_Modularization
description: Descrive la componentizzazione in MRTK.
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: 26bb2d0d2eebb7c7450b3eb8ed29c05ab54e3e09
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/03/2021
ms.locfileid: "101783807"
---
# <a name="mixed-reality-toolkit-componentization"></a><span data-ttu-id="1f0ec-104">Componentizzazione del Toolkit di realtà mista</span><span class="sxs-lookup"><span data-stu-id="1f0ec-104">Mixed Reality Toolkit componentization</span></span>

<span data-ttu-id="1f0ec-105">Una delle nuove eccezionali funzionalità di Mixed Reality toolkit V2 è il miglioramento della componentizzazione.</span><span class="sxs-lookup"><span data-stu-id="1f0ec-105">One of the great new features of Mixed Reality Toolkit v2 is improved componentization.</span></span> <span data-ttu-id="1f0ec-106">Laddove possibile, i singoli componenti sono isolati da tutti i livelli di base della base.</span><span class="sxs-lookup"><span data-stu-id="1f0ec-106">Wherever possible, individual components are isolated from all but the core layer of the foundation.</span></span>

## <a name="minimized-dependencies"></a><span data-ttu-id="1f0ec-107">Dipendenze minime</span><span class="sxs-lookup"><span data-stu-id="1f0ec-107">Minimized dependencies</span></span>

<span data-ttu-id="1f0ec-108">MRTK V2 è stato intenzionalmente sviluppato per essere modulare e per ridurre al minimo le dipendenze tra i servizi di sistema (ad esempio, la consapevolezza spaziale).</span><span class="sxs-lookup"><span data-stu-id="1f0ec-108">MRTK v2 was intentionally developed to be modular and to minimize dependencies between system services (ex: spatial awareness).</span></span>

<span data-ttu-id="1f0ec-109">A causa della natura di alcuni servizi di sistema (ad esempio, input e Teleportation), esiste un numero ridotto di dipendenze.</span><span class="sxs-lookup"><span data-stu-id="1f0ec-109">Due to the nature of some system services (ex: input and teleportation), a small number of dependencies exist.</span></span>

<span data-ttu-id="1f0ec-110">Sebbene sia previsto che i servizi necessitino di uno o più componenti del provider di dati, non vi sono collegamenti diretti tra di essi.</span><span class="sxs-lookup"><span data-stu-id="1f0ec-110">While it is expected that services will need one or more data provider components, there are no direct links between them.</span></span> <span data-ttu-id="1f0ec-111">Lo stesso vale per le funzionalità SDK (ad esempio, i componenti dell'interfaccia utente).</span><span class="sxs-lookup"><span data-stu-id="1f0ec-111">The same is true for SDK features (ex: User Interface components).</span></span>

## <a name="component-communication"></a><span data-ttu-id="1f0ec-112">Comunicazione componenti</span><span class="sxs-lookup"><span data-stu-id="1f0ec-112">Component communication</span></span>

<span data-ttu-id="1f0ec-113">Per assicurarsi che non vi siano collegamenti diretti tra i componenti, MRTK V2 usa le interfacce per la comunicazione tra servizi, provider di dati e codice dell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="1f0ec-113">To ensure that there are no direct links between components, MRTK v2 utilizes interfaces to communicate between services, data providers and application code.</span></span> <span data-ttu-id="1f0ec-114">Queste interfacce sono definite in e tutte le comunicazioni vengono instradate tramite il componente principale del Toolkit di realtà mista.</span><span class="sxs-lookup"><span data-stu-id="1f0ec-114">These interfaces are defined in and all communication is routed through the Mixed Reality Toolkit core component.</span></span>

![Uso del sistema di riconoscimento spaziale tramite le interfacce](../features/images/packaging/AccessingViaInterfaces.png)

## <a name="minimizing-mrtk-import-footprint"></a><span data-ttu-id="1f0ec-116">Riduzione del footprint di importazione MRTK</span><span class="sxs-lookup"><span data-stu-id="1f0ec-116">Minimizing MRTK import footprint</span></span>

<span data-ttu-id="1f0ec-117">A questo punto, il MRTK viene importato come singolo pacchetto di base (ignorando per un momento l'esistenza del pacchetto di esempi, che è un pacchetto completamente facoltativo).</span><span class="sxs-lookup"><span data-stu-id="1f0ec-117">At this moment, the MRTK is imported as a single foundation package (ignoring for a moment the existence of the examples package, which is a completely optional package).</span></span> <span data-ttu-id="1f0ec-118">È possibile ridurre questo footprint riducendo manualmente i file importati, anche se si tratta di un processo estremamente manuale senza una guida ben definita.</span><span class="sxs-lookup"><span data-stu-id="1f0ec-118">It is possible to make this footprint smaller by manually cutting down on the files imported, though this is a highly manual process which doesn't have a well-defined guide.</span></span>

<span data-ttu-id="1f0ec-119">È possibile deselezionare gli elementi arbitrari durante l'importazione del pacchetto di base.</span><span class="sxs-lookup"><span data-stu-id="1f0ec-119">It is possible to uncheck arbitrary items during the import of the Foundation package.</span></span> <span data-ttu-id="1f0ec-120">Tuttavia, non è consigliabile eseguire questa operazione in una fase iniziale dello sviluppo perché potrebbe interrompere la funzionalità.</span><span class="sxs-lookup"><span data-stu-id="1f0ec-120">However, it's not recommended to do this at an early stage in development as it might break functionality.</span></span> <span data-ttu-id="1f0ec-121">Dopo aver individuato il set di funzionalità finali di un'app, è possibile eliminare i provider e i servizi non necessari nelle cartelle seguenti:</span><span class="sxs-lookup"><span data-stu-id="1f0ec-121">After having figured out the final feature set of an app, pruning unneeded providers and services can be done on the following folders:</span></span>

- <span data-ttu-id="1f0ec-122">MRTK/servizi</span><span class="sxs-lookup"><span data-stu-id="1f0ec-122">MRTK/Services</span></span>
- <span data-ttu-id="1f0ec-123">MRTK/provider</span><span class="sxs-lookup"><span data-stu-id="1f0ec-123">MRTK/Providers</span></span>
- <span data-ttu-id="1f0ec-124">MRTK/SDK/funzionalità</span><span class="sxs-lookup"><span data-stu-id="1f0ec-124">MRTK/SDK/Features</span></span>

> [!NOTE]
> <span data-ttu-id="1f0ec-125">MRTK V2. x **_richiede_** il contenuto della cartella assets/MRTK/core.</span><span class="sxs-lookup"><span data-stu-id="1f0ec-125">MRTK v2.x **_requires_** the contents of the Assets/MRTK/Core folder.</span></span>

## <a name="upcoming-features"></a><span data-ttu-id="1f0ec-126">Funzionalità future</span><span class="sxs-lookup"><span data-stu-id="1f0ec-126">Upcoming features</span></span>

### <a name="application-architecture"></a><span data-ttu-id="1f0ec-127">Architettura dell'applicazione</span><span class="sxs-lookup"><span data-stu-id="1f0ec-127">Application architecture</span></span>

<span data-ttu-id="1f0ec-128">MRTK avrà il supporto per consentire la compilazione di applicazioni con un'ampia gamma di architetture, tra cui:</span><span class="sxs-lookup"><span data-stu-id="1f0ec-128">The MRTK will have support to enable applications to be built with a variety of architectures, including:</span></span>

- [<span data-ttu-id="1f0ec-129">Localizzatore del servizio MixedRealityToolkit</span><span class="sxs-lookup"><span data-stu-id="1f0ec-129">MixedRealityToolkit service locator</span></span>](#mixedrealitytoolkit-service-locator)
- [<span data-ttu-id="1f0ec-130">Singoli servizi</span><span class="sxs-lookup"><span data-stu-id="1f0ec-130">Individual services</span></span>](#individual-service-components)
- [<span data-ttu-id="1f0ec-131">Localizzatore servizio personalizzato</span><span class="sxs-lookup"><span data-stu-id="1f0ec-131">Custom service locator</span></span>](#custom-service-locator)
- [<span data-ttu-id="1f0ec-132">Architettura ibrida</span><span class="sxs-lookup"><span data-stu-id="1f0ec-132">Hybrid architecture</span></span>](#hybrid-architecture)

<span data-ttu-id="1f0ec-133">Quando si seleziona un'architettura di applicazione, è importante considerare la flessibilità di progettazione e le prestazioni dell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="1f0ec-133">When selecting an application architecture, it is important to consider design flexibility and application performance.</span></span> <span data-ttu-id="1f0ec-134">Le architetture descritte di seguito non sono adatte per ogni applicazione.</span><span class="sxs-lookup"><span data-stu-id="1f0ec-134">The architectures described here are not expected to be suitable for every application.</span></span>

#### <a name="mixedrealitytoolkit-service-locator"></a><span data-ttu-id="1f0ec-135">Localizzatore del servizio MixedRealityToolkit</span><span class="sxs-lookup"><span data-stu-id="1f0ec-135">MixedRealityToolkit service locator</span></span>

<span data-ttu-id="1f0ec-136">Il MRTK Abilita (e configura automaticamente) le scene dell'applicazione per usare il [`MixedRealityToolkit`](xref:Microsoft.MixedReality.Toolkit.MixedRealityToolkit) componente di localizzazione del servizio predefinito.</span><span class="sxs-lookup"><span data-stu-id="1f0ec-136">The MRTK enables (and automatically configures) application scenes to use the default [`MixedRealityToolkit`](xref:Microsoft.MixedReality.Toolkit.MixedRealityToolkit) service locator component.</span></span> <span data-ttu-id="1f0ec-137">Questo componente include il supporto per la configurazione di sistemi e provider di dati MRTK tramite i controlli di configurazione e gestisce le durate dei componenti e i comportamenti principali (ad esempio, quando aggiornare).</span><span class="sxs-lookup"><span data-stu-id="1f0ec-137">This component includes support for configuring MRTK systems and data providers via configuration inspectors and manages component lifespans and core behaviors (ex: when to update).</span></span>

<span data-ttu-id="1f0ec-138">Tutti i sistemi sono rappresentati nel controllo configurazione principale, indipendentemente dal fatto che siano presenti o non siano abilitati nel progetto.</span><span class="sxs-lookup"><span data-stu-id="1f0ec-138">All systems are represented in the core configuration inspector, regardless of whether or not they are present or enabled in the project.</span></span> <span data-ttu-id="1f0ec-139">Per ulteriori informazioni, vedere la [Guida alla configurazione della realtà mista](../configuration/MixedRealityConfigurationGuide.md) .</span><span class="sxs-lookup"><span data-stu-id="1f0ec-139">Please see the [Mixed Reality Configuration Guide](../configuration/MixedRealityConfigurationGuide.md) for more information.</span></span>

#### <a name="individual-service-components"></a><span data-ttu-id="1f0ec-140">Singoli componenti del servizio</span><span class="sxs-lookup"><span data-stu-id="1f0ec-140">Individual service components</span></span>

<span data-ttu-id="1f0ec-141">Alcuni sviluppatori hanno espresso il desiderio di includere singoli componenti del servizio nella gerarchia della scena dell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="1f0ec-141">Some developers have expressed a desire to include individual service components into the application scene hierarchy.</span></span> <span data-ttu-id="1f0ec-142">Per abilitare questo utilizzo, i servizi dovranno essere incapsulati in un registrar personalizzato o essere autofirmati o autogestiti.</span><span class="sxs-lookup"><span data-stu-id="1f0ec-142">To enable this usage, services will either need to be encapsulated in a custom registrar or be self-registering / self-managing.</span></span>

<span data-ttu-id="1f0ec-143">Un servizio di registrazione automatica implementa [`IMixedRealityServiceRegistrar`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) e registra se stesso in modo che il codice dell'applicazione possa individuare l'istanza del servizio tramite un registro di sistema.</span><span class="sxs-lookup"><span data-stu-id="1f0ec-143">A self-registering service would implement the [`IMixedRealityServiceRegistrar`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) and register itself so that application code could discover the service instance via a registry.</span></span>

<span data-ttu-id="1f0ec-144">Un servizio di gestione automatica può essere implementato come un oggetto singleton nella gerarchia della scena.</span><span class="sxs-lookup"><span data-stu-id="1f0ec-144">A self-managing service could be implemented as a singleton object in the scene hierarchy.</span></span> <span data-ttu-id="1f0ec-145">Questo oggetto fornisce una proprietà di istanza che può essere utilizzata dal codice dell'applicazione per accedere direttamente alle funzionalità del servizio.</span><span class="sxs-lookup"><span data-stu-id="1f0ec-145">This object would provide and instance property which application code could use to directly access service functionality.</span></span>

#### <a name="custom-service-locator"></a><span data-ttu-id="1f0ec-146">Localizzatore servizio personalizzato</span><span class="sxs-lookup"><span data-stu-id="1f0ec-146">Custom service locator</span></span>

<span data-ttu-id="1f0ec-147">Alcuni sviluppatori hanno richiesto la possibilità di creare un componente del localizzatore di servizi personalizzato.</span><span class="sxs-lookup"><span data-stu-id="1f0ec-147">Some developers have requested the ability to create a custom service locator component.</span></span> <span data-ttu-id="1f0ec-148">I localizzatori di servizi personalizzati implementano l' [`IMixedRealityServiceRegistrar`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) interfaccia e gestiscono il ciclo di vita e i comportamenti principali dei servizi attivi.</span><span class="sxs-lookup"><span data-stu-id="1f0ec-148">Custom service locators would implement the [`IMixedRealityServiceRegistrar`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) interface and manage the life cycle and core behaviors of active services.</span></span>

#### <a name="hybrid-architecture"></a><span data-ttu-id="1f0ec-149">Architettura ibrida</span><span class="sxs-lookup"><span data-stu-id="1f0ec-149">Hybrid architecture</span></span>

<span data-ttu-id="1f0ec-150">MRTK supporterà un'architettura ibrida in cui gli sviluppatori possono combinare gli approcci precedenti in base alle esigenze o alle esigenze.</span><span class="sxs-lookup"><span data-stu-id="1f0ec-150">The MRTK will support a hybrid architecture in which developers can combine the previous approaches as needed or desired.</span></span> <span data-ttu-id="1f0ec-151">Ad esempio, uno sviluppatore può iniziare con il [`MixedRealityToolkit`](xref:Microsoft.MixedReality.Toolkit.MixedRealityToolkit) localizzatore del servizio e aggiungere un servizio di registrazione automatica.</span><span class="sxs-lookup"><span data-stu-id="1f0ec-151">For example, a developer could start with the [`MixedRealityToolkit`](xref:Microsoft.MixedReality.Toolkit.MixedRealityToolkit) service locator and add a self-registering service.</span></span>

> [!NOTE]
> <span data-ttu-id="1f0ec-152">Quando si opta per un'architettura ibrida, è importante tenere presente qualsiasi duplicazione del lavoro (ad esempio, l'acquisizione dei dati del controller da più componenti).</span><span class="sxs-lookup"><span data-stu-id="1f0ec-152">When opting for a hybrid architecture, it is important to be mindful of any duplication of work (ex: acquiring controller data from multiple components).</span></span>

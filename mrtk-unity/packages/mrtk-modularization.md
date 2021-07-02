---
title: Modularizzazione di MRTK
description: Descrive la componentizzazione in MRTK.
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: eac96e309afc21f9a2b6efe9c3aef5975e4f0dff
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177015"
---
# <a name="mrtk-modularization"></a><span data-ttu-id="d2e22-104">Modularizzazione di MRTK</span><span class="sxs-lookup"><span data-stu-id="d2e22-104">MRTK modularization</span></span>

<span data-ttu-id="d2e22-105">Una delle nuove funzionalità di Mixed Reality Toolkit v2 è stata migliorata la componentizzazione.</span><span class="sxs-lookup"><span data-stu-id="d2e22-105">One of the great new features of Mixed Reality Toolkit v2 is improved componentization.</span></span> <span data-ttu-id="d2e22-106">Laddove possibile, i singoli componenti sono isolati da tutti, ma dal livello principale della base.</span><span class="sxs-lookup"><span data-stu-id="d2e22-106">Wherever possible, individual components are isolated from all but the core layer of the foundation.</span></span>

## <a name="minimized-dependencies"></a><span data-ttu-id="d2e22-107">Dipendenze ridotte al minimo</span><span class="sxs-lookup"><span data-stu-id="d2e22-107">Minimized dependencies</span></span>

<span data-ttu-id="d2e22-108">MRTK v2 è stato sviluppato intenzionalmente per essere modulare e per ridurre al minimo le dipendenze tra i servizi di sistema (ad esempio, la consapevolezza spaziale).</span><span class="sxs-lookup"><span data-stu-id="d2e22-108">MRTK v2 was intentionally developed to be modular and to minimize dependencies between system services (ex: spatial awareness).</span></span>

<span data-ttu-id="d2e22-109">A causa della natura di alcuni servizi di sistema (ad esempio input e teletrasporto), esiste un numero ridotto di dipendenze.</span><span class="sxs-lookup"><span data-stu-id="d2e22-109">Due to the nature of some system services (ex: input and teleportation), a small number of dependencies exist.</span></span>

<span data-ttu-id="d2e22-110">Sebbene sia previsto che i servizi necessitino di uno o più componenti del provider di dati, tra di essi non sono presenti collegamenti diretti.</span><span class="sxs-lookup"><span data-stu-id="d2e22-110">While it is expected that services will need one or more data provider components, there are no direct links between them.</span></span> <span data-ttu-id="d2e22-111">Lo stesso vale per le funzionalità dell'SDK (ad esempio, Interfaccia utente componenti).</span><span class="sxs-lookup"><span data-stu-id="d2e22-111">The same is true for SDK features (ex: User Interface components).</span></span>

## <a name="component-communication"></a><span data-ttu-id="d2e22-112">Comunicazione dei componenti</span><span class="sxs-lookup"><span data-stu-id="d2e22-112">Component communication</span></span>

<span data-ttu-id="d2e22-113">Per garantire che non siano presenti collegamenti diretti tra i componenti, MRTK v2 usa le interfacce per comunicare tra servizi, provider di dati e codice dell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="d2e22-113">To ensure that there are no direct links between components, MRTK v2 utilizes interfaces to communicate between services, data providers and application code.</span></span> <span data-ttu-id="d2e22-114">Queste interfacce sono definite in e tutte le comunicazioni vengono indirizzate tramite il componente Toolkit core di Realtà mista.</span><span class="sxs-lookup"><span data-stu-id="d2e22-114">These interfaces are defined in and all communication is routed through the Mixed Reality Toolkit core component.</span></span>

![Uso del sistema di consapevolezza spaziale tramite interfacce](../features/images/packaging/AccessingViaInterfaces.png)

## <a name="minimizing-mrtk-import-footprint"></a><span data-ttu-id="d2e22-116">Riduzione al minimo del footprint di importazione MRTK</span><span class="sxs-lookup"><span data-stu-id="d2e22-116">Minimizing MRTK import footprint</span></span>

<span data-ttu-id="d2e22-117">In questo momento, MRTK viene importato come singolo pacchetto di base (ignorando per un momento l'esistenza del pacchetto examples, che è un pacchetto completamente facoltativo).</span><span class="sxs-lookup"><span data-stu-id="d2e22-117">At this moment, the MRTK is imported as a single foundation package (ignoring for a moment the existence of the examples package, which is a completely optional package).</span></span> <span data-ttu-id="d2e22-118">È possibile ridurre il footprint riducendo manualmente i file importati, anche se si tratta di un processo altamente manuale che non ha una guida ben definita.</span><span class="sxs-lookup"><span data-stu-id="d2e22-118">It is possible to make this footprint smaller by manually cutting down on the files imported, though this is a highly manual process which doesn't have a well-defined guide.</span></span>

<span data-ttu-id="d2e22-119">È possibile deselezionare gli elementi arbitrari durante l'importazione del pacchetto di Foundation.</span><span class="sxs-lookup"><span data-stu-id="d2e22-119">It is possible to uncheck arbitrary items during the import of the Foundation package.</span></span> <span data-ttu-id="d2e22-120">Tuttavia, non è consigliabile eseguire questa operazione in una fase iniziale dello sviluppo perché potrebbe interrompere la funzionalità.</span><span class="sxs-lookup"><span data-stu-id="d2e22-120">However, it's not recommended to do this at an early stage in development as it might break functionality.</span></span> <span data-ttu-id="d2e22-121">Dopo aver trovato il set di funzionalità finale di un'app, è possibile eliminare i provider e i servizi non necessari nelle cartelle seguenti:</span><span class="sxs-lookup"><span data-stu-id="d2e22-121">After having figured out the final feature set of an app, pruning unneeded providers and services can be done on the following folders:</span></span>

- <span data-ttu-id="d2e22-122">MRTK/Services</span><span class="sxs-lookup"><span data-stu-id="d2e22-122">MRTK/Services</span></span>
- <span data-ttu-id="d2e22-123">MRTK/Providers</span><span class="sxs-lookup"><span data-stu-id="d2e22-123">MRTK/Providers</span></span>
- <span data-ttu-id="d2e22-124">MRTK/SDK/Features</span><span class="sxs-lookup"><span data-stu-id="d2e22-124">MRTK/SDK/Features</span></span>

> [!NOTE]
> <span data-ttu-id="d2e22-125">MRTK v2.x **_richiede_** il contenuto della cartella Assets/MRTK/Core.</span><span class="sxs-lookup"><span data-stu-id="d2e22-125">MRTK v2.x **_requires_** the contents of the Assets/MRTK/Core folder.</span></span>

## <a name="upcoming-features"></a><span data-ttu-id="d2e22-126">Funzionalità future</span><span class="sxs-lookup"><span data-stu-id="d2e22-126">Upcoming features</span></span>

### <a name="application-architecture"></a><span data-ttu-id="d2e22-127">Architettura dell'applicazione</span><span class="sxs-lookup"><span data-stu-id="d2e22-127">Application architecture</span></span>

<span data-ttu-id="d2e22-128">MrTK avrà il supporto per consentire la costruzione di applicazioni con un'ampia gamma di architetture, tra cui:</span><span class="sxs-lookup"><span data-stu-id="d2e22-128">The MRTK will have support to enable applications to be built with a variety of architectures, including:</span></span>

- [<span data-ttu-id="d2e22-129">Localizzatore del servizio MixedRealityToolkit</span><span class="sxs-lookup"><span data-stu-id="d2e22-129">MixedRealityToolkit service locator</span></span>](#mixedrealitytoolkit-service-locator)
- [<span data-ttu-id="d2e22-130">Singoli servizi</span><span class="sxs-lookup"><span data-stu-id="d2e22-130">Individual services</span></span>](#individual-service-components)
- [<span data-ttu-id="d2e22-131">Localizzatore del servizio personalizzato</span><span class="sxs-lookup"><span data-stu-id="d2e22-131">Custom service locator</span></span>](#custom-service-locator)
- [<span data-ttu-id="d2e22-132">Architettura ibrida</span><span class="sxs-lookup"><span data-stu-id="d2e22-132">Hybrid architecture</span></span>](#hybrid-architecture)

<span data-ttu-id="d2e22-133">Quando si seleziona un'architettura dell'applicazione, è importante considerare la flessibilità di progettazione e le prestazioni dell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="d2e22-133">When selecting an application architecture, it is important to consider design flexibility and application performance.</span></span> <span data-ttu-id="d2e22-134">Le architetture descritte in questo articolo non sono idonee per ogni applicazione.</span><span class="sxs-lookup"><span data-stu-id="d2e22-134">The architectures described here are not expected to be suitable for every application.</span></span>

#### <a name="mixedrealitytoolkit-service-locator"></a><span data-ttu-id="d2e22-135">Localizzatore del servizio MixedRealityToolkit</span><span class="sxs-lookup"><span data-stu-id="d2e22-135">MixedRealityToolkit service locator</span></span>

<span data-ttu-id="d2e22-136">MRTK abilita (e configura automaticamente) le scene dell'applicazione per usare il componente [`MixedRealityToolkit`](xref:Microsoft.MixedReality.Toolkit.MixedRealityToolkit) del localizzatore di servizi predefinito.</span><span class="sxs-lookup"><span data-stu-id="d2e22-136">The MRTK enables (and automatically configures) application scenes to use the default [`MixedRealityToolkit`](xref:Microsoft.MixedReality.Toolkit.MixedRealityToolkit) service locator component.</span></span> <span data-ttu-id="d2e22-137">Questo componente include il supporto per la configurazione di sistemi MRTK e provider di dati tramite i controlli di configurazione e gestisce la durata dei componenti e i comportamenti principali (ad esempio, quando eseguire l'aggiornamento).</span><span class="sxs-lookup"><span data-stu-id="d2e22-137">This component includes support for configuring MRTK systems and data providers via configuration inspectors and manages component lifespans and core behaviors (ex: when to update).</span></span>

<span data-ttu-id="d2e22-138">Tutti i sistemi sono rappresentati nel controllo della configurazione principale, indipendentemente dal fatto che siano o meno presenti o abilitati nel progetto.</span><span class="sxs-lookup"><span data-stu-id="d2e22-138">All systems are represented in the core configuration inspector, regardless of whether or not they are present or enabled in the project.</span></span> <span data-ttu-id="d2e22-139">Per altre [informazioni, vedere la Guida](../configuration/mixed-reality-configuration-guide.md) alla configurazione della realtà mista.</span><span class="sxs-lookup"><span data-stu-id="d2e22-139">Please see the [Mixed Reality Configuration Guide](../configuration/mixed-reality-configuration-guide.md) for more information.</span></span>

#### <a name="individual-service-components"></a><span data-ttu-id="d2e22-140">Singoli componenti del servizio</span><span class="sxs-lookup"><span data-stu-id="d2e22-140">Individual service components</span></span>

<span data-ttu-id="d2e22-141">Alcuni sviluppatori hanno espresso il desiderio di includere singoli componenti del servizio nella gerarchia della scena dell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="d2e22-141">Some developers have expressed a desire to include individual service components into the application scene hierarchy.</span></span> <span data-ttu-id="d2e22-142">Per abilitare questo utilizzo, i servizi dovranno essere incapsulati in un registrar personalizzato o essere autoregistrati/autogestiti.</span><span class="sxs-lookup"><span data-stu-id="d2e22-142">To enable this usage, services will either need to be encapsulated in a custom registrar or be self-registering / self-managing.</span></span>

<span data-ttu-id="d2e22-143">Un servizio autoregistrato implementa e registra se stesso in modo che il codice dell'applicazione possa individuare l'istanza del servizio [`IMixedRealityServiceRegistrar`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) tramite un registro.</span><span class="sxs-lookup"><span data-stu-id="d2e22-143">A self-registering service would implement the [`IMixedRealityServiceRegistrar`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) and register itself so that application code could discover the service instance via a registry.</span></span>

<span data-ttu-id="d2e22-144">Un servizio self-managing può essere implementato come oggetto singleton nella gerarchia della scena.</span><span class="sxs-lookup"><span data-stu-id="d2e22-144">A self-managing service could be implemented as a singleton object in the scene hierarchy.</span></span> <span data-ttu-id="d2e22-145">Questo oggetto fornisce e la proprietà dell'istanza che il codice dell'applicazione può usare per accedere direttamente alle funzionalità del servizio.</span><span class="sxs-lookup"><span data-stu-id="d2e22-145">This object would provide and instance property which application code could use to directly access service functionality.</span></span>

#### <a name="custom-service-locator"></a><span data-ttu-id="d2e22-146">Localizzatore del servizio personalizzato</span><span class="sxs-lookup"><span data-stu-id="d2e22-146">Custom service locator</span></span>

<span data-ttu-id="d2e22-147">Alcuni sviluppatori hanno richiesto la possibilità di creare un componente del localizzatore di servizi personalizzato.</span><span class="sxs-lookup"><span data-stu-id="d2e22-147">Some developers have requested the ability to create a custom service locator component.</span></span> <span data-ttu-id="d2e22-148">I localizzatori di servizi personalizzati implementano l'interfaccia e gestiscono il ciclo di vita e [`IMixedRealityServiceRegistrar`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) i comportamenti principali dei servizi attivi.</span><span class="sxs-lookup"><span data-stu-id="d2e22-148">Custom service locators would implement the [`IMixedRealityServiceRegistrar`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) interface and manage the life cycle and core behaviors of active services.</span></span>

#### <a name="hybrid-architecture"></a><span data-ttu-id="d2e22-149">Architettura ibrida</span><span class="sxs-lookup"><span data-stu-id="d2e22-149">Hybrid architecture</span></span>

<span data-ttu-id="d2e22-150">MrTK supporterà un'architettura ibrida in cui gli sviluppatori possono combinare gli approcci precedenti in base alle esigenze o alle esigenze.</span><span class="sxs-lookup"><span data-stu-id="d2e22-150">The MRTK will support a hybrid architecture in which developers can combine the previous approaches as needed or desired.</span></span> <span data-ttu-id="d2e22-151">Ad esempio, uno sviluppatore può iniziare con [`MixedRealityToolkit`](xref:Microsoft.MixedReality.Toolkit.MixedRealityToolkit) il localizzatore del servizio e aggiungere un servizio di autoregistrazione.</span><span class="sxs-lookup"><span data-stu-id="d2e22-151">For example, a developer could start with the [`MixedRealityToolkit`](xref:Microsoft.MixedReality.Toolkit.MixedRealityToolkit) service locator and add a self-registering service.</span></span>

> [!NOTE]
> <span data-ttu-id="d2e22-152">Quando si sceglie un'architettura ibrida, è importante tenere presente qualsiasi duplicazione del lavoro ,ad esempio l'acquisizione dei dati del controller da più componenti.</span><span class="sxs-lookup"><span data-stu-id="d2e22-152">When opting for a hybrid architecture, it is important to be mindful of any duplication of work (ex: acquiring controller data from multiple components).</span></span>

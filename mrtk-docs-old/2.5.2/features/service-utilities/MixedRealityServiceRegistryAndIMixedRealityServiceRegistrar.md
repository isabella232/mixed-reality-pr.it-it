---
title: MixedRealityServiceRegistryAndIMixedRealityServiceRegistrar
description: Documentazione su MixedRealityServiceRegistry e IMixedRealityServiceRegistrar
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: 773e7b647db3498d88e1cf10c05429d518b3ed3f
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2021
ms.locfileid: "104690451"
---
# <a name="what-are-the-mixedrealityserviceregistry-and-imixedrealityserviceregistrar"></a><span data-ttu-id="eda28-104">Quali sono MixedRealityServiceRegistry e IMixedRealityServiceRegistrar?</span><span class="sxs-lookup"><span data-stu-id="eda28-104">What are the MixedRealityServiceRegistry and IMixedRealityServiceRegistrar?</span></span>

<span data-ttu-id="eda28-105">Il Toolkit di realtà mista ha due componenti denominati molto simili che eseguono attività correlate: MixedRealityServiceRegistry e IMixedRealityServiceRegistrar.</span><span class="sxs-lookup"><span data-stu-id="eda28-105">The Mixed Reality Toolkit has two very similarly named components that perform related tasks: MixedRealityServiceRegistry and IMixedRealityServiceRegistrar.</span></span>

## <a name="mixedrealityserviceregistry"></a><span data-ttu-id="eda28-106">MixedRealityServiceRegistry</span><span class="sxs-lookup"><span data-stu-id="eda28-106">MixedRealityServiceRegistry</span></span>

<span data-ttu-id="eda28-107">[MixedRealityServiceRegistry](xref:Microsoft.MixedReality.Toolkit.MixedRealityServiceRegistry) è il componente che contiene le istanze di ogni servizio registrato (sistemi core e servizi di estensione).</span><span class="sxs-lookup"><span data-stu-id="eda28-107">The [MixedRealityServiceRegistry](xref:Microsoft.MixedReality.Toolkit.MixedRealityServiceRegistry) is the component that contains instances of each registered service (core systems and extension services).</span></span>

> [!NOTE]
> <span data-ttu-id="eda28-108">MixedRealityServiceRegistry contiene istanze di oggetti che implementano l'interfaccia [IMixedRealityService](xref:Microsoft.MixedReality.Toolkit.IMixedRealityService) , incluso [IMixedRealityExtensionService](xref:Microsoft.MixedReality.Toolkit.IMixedRealityExtensionService).</span><span class="sxs-lookup"><span data-stu-id="eda28-108">The MixedRealityServiceRegistry contains instances of objects that implement [IMixedRealityService](xref:Microsoft.MixedReality.Toolkit.IMixedRealityService) interface, including [IMixedRealityExtensionService](xref:Microsoft.MixedReality.Toolkit.IMixedRealityExtensionService).</span></span>
>
><span data-ttu-id="eda28-109">Gli oggetti che implementano [IMixedRealityDataProvider](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) (una sottoclasse di IMixedRealityService) non sono registrati in modo esplicito nel MixedRealityServiceRegistry.</span><span class="sxs-lookup"><span data-stu-id="eda28-109">Objects implementing the [IMixedRealityDataProvider](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) (a subclass of IMixedRealityService) are explicitly not registered in the MixedRealityServiceRegistry.</span></span> <span data-ttu-id="eda28-110">Questi oggetti vengono gestiti dai singoli servizi (ad esempio, la consapevolezza spaziale).</span><span class="sxs-lookup"><span data-stu-id="eda28-110">These objects are managed by the individual services (ex: Spatial Awareness).</span></span>

<span data-ttu-id="eda28-111">MixedRealityServiceRegistry viene implementato come classe C# statica ed è il modello consigliato da usare per acquisire le istanze del servizio nel codice dell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="eda28-111">The MixedRealityServiceRegistry is implemented as a static C# class and is the recommended pattern to use to acquire service instances in application code.</span></span>

<span data-ttu-id="eda28-112">Il frammento di codice seguente illustra l'acquisizione di un'istanza di IMixedRealityInputSystem.</span><span class="sxs-lookup"><span data-stu-id="eda28-112">The following snippet demonstrates acquiring an IMixedRealityInputSystem instance.</span></span>

```c#
IMixedRealityInputSystem inputSystem = null;

if (!MixedRealityServiceRegistry.TryGetService<IMixedRealityInputSystem>(out inputSystem))
{
    // Failed to acquire the input system. It may not have been registered
}
```

## <a name="imixedrealityserviceregistrar"></a><span data-ttu-id="eda28-113">IMixedRealityServiceRegistrar</span><span class="sxs-lookup"><span data-stu-id="eda28-113">IMixedRealityServiceRegistrar</span></span>

<span data-ttu-id="eda28-114">[IMixedRealityServiceRegistrar](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) è l'interfaccia che definisce la funzionalità implementata dai componenti che gestiscono la registrazione di uno o più servizi.</span><span class="sxs-lookup"><span data-stu-id="eda28-114">The [IMixedRealityServiceRegistrar](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) is the interface that defines the functionality implemented by components that manage the registration of one or more services.</span></span> <span data-ttu-id="eda28-115">I componenti che implementano IMixedRealityServiceRegistrar sono responsabili dell'aggiunta e della rimozione dei dati all'interno di MixedRealityServiceRegistry.</span><span class="sxs-lookup"><span data-stu-id="eda28-115">Components that implement IMixedRealityServiceRegistrar are responsible for adding and removing the data within the MixedRealityServiceRegistry.</span></span> <span data-ttu-id="eda28-116">L'oggetto [MixedRealityToolkit](xref:Microsoft.MixedReality.Toolkit.MixedRealityToolkit) è un componente di questo tipo.</span><span class="sxs-lookup"><span data-stu-id="eda28-116">The [MixedRealityToolkit](xref:Microsoft.MixedReality.Toolkit.MixedRealityToolkit) object is one such component.</span></span>

<span data-ttu-id="eda28-117">Altri registrar si trovano nella cartella MRTK/SDK/Experimental/Features.</span><span class="sxs-lookup"><span data-stu-id="eda28-117">Other registrars can be found in the MRTK/SDK/Experimental/Features folder.</span></span> <span data-ttu-id="eda28-118">Questi componenti possono essere usati per aggiungere il supporto di un singolo servizio (ad esempio, la consapevolezza spaziale) a un'applicazione.</span><span class="sxs-lookup"><span data-stu-id="eda28-118">These components can be used to add single service (ex: Spatial Awareness) support to an application.</span></span> <span data-ttu-id="eda28-119">Questi singoli gestori di servizi sono elencati di seguito.</span><span class="sxs-lookup"><span data-stu-id="eda28-119">These single service managers are listed below.</span></span>

- [<span data-ttu-id="eda28-120">BoundarySystemManager</span><span class="sxs-lookup"><span data-stu-id="eda28-120">BoundarySystemManager</span></span>](xref:Microsoft.MixedReality.Toolkit.Experimental.Boundary.BoundarySystemManager)
- [<span data-ttu-id="eda28-121">CameraSystemManager</span><span class="sxs-lookup"><span data-stu-id="eda28-121">CameraSystemManager</span></span>](xref:Microsoft.MixedReality.Toolkit.Experimental.CameraSystem.CameraSystemManager)
- [<span data-ttu-id="eda28-122">DiagnosticsSystemManager</span><span class="sxs-lookup"><span data-stu-id="eda28-122">DiagnosticsSystemManager</span></span>](xref:Microsoft.MixedReality.Toolkit.Experimental.Diagnostics.DiagnosticsSystemManager)
- [<span data-ttu-id="eda28-123">InputSystemManager</span><span class="sxs-lookup"><span data-stu-id="eda28-123">InputSystemManager</span></span>](xref:Microsoft.MixedReality.Toolkit.Experimental.Input.InputSystemManager)
- [<span data-ttu-id="eda28-124">SpatialAwarenessSystemManager</span><span class="sxs-lookup"><span data-stu-id="eda28-124">SpatialAwarenessSystemManager</span></span>](xref:Microsoft.MixedReality.Toolkit.Experimental.SpatialAwareness.SpatialAwarenessSystemManager)
- [<span data-ttu-id="eda28-125">TeleportSystemManager</span><span class="sxs-lookup"><span data-stu-id="eda28-125">TeleportSystemManager</span></span>](xref:Microsoft.MixedReality.Toolkit.Experimental.Teleport.TeleportSystemManager)

<span data-ttu-id="eda28-126">Ogni componente precedente, ad eccezione di InputSystemManager, è responsabile della gestione della registrazione e dello stato di un singolo tipo di servizio.</span><span class="sxs-lookup"><span data-stu-id="eda28-126">Each of the above components, with the exception of the InputSystemManager, are responsible for managing the registration and status of a single service type.</span></span> <span data-ttu-id="eda28-127">InputSystem richiede servizi di supporto aggiuntivi (ad esempio, FocusProvider) che vengono gestiti anche da InputSystemManager.</span><span class="sxs-lookup"><span data-stu-id="eda28-127">The InputSystem requires some additional support services (ex: FocusProvider) that are also managed by the InputSystemManager.</span></span>

<span data-ttu-id="eda28-128">In generale, i metodi definiti da IMixedRealityServiceRegistrar vengono chiamati internamente dai componenti di gestione dei servizi o chiamati da servizi che richiedono che i componenti del servizio aggiuntivi funzionino correttamente.</span><span class="sxs-lookup"><span data-stu-id="eda28-128">In general, the methods defined by IMixedRealityServiceRegistrar are called internally by service management components or called by services that require additional service components to function correctly.</span></span> <span data-ttu-id="eda28-129">Il codice dell'applicazione, in genere, non chiama questi metodi perché questa operazione potrebbe causare un comportamento imprevedibile dell'applicazione (ad esempio, un'istanza del servizio memorizzata nella cache potrebbe diventare non valida).</span><span class="sxs-lookup"><span data-stu-id="eda28-129">Application code should, generally, not call these methods as doing so may cause the application to behave unpredictably (ex: a cached service instance may become invalid).</span></span>

## <a name="see-also"></a><span data-ttu-id="eda28-130">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="eda28-130">See also</span></span>

- [<span data-ttu-id="eda28-131">Documentazione dell'API IMixedRealityServiceRegistrar</span><span class="sxs-lookup"><span data-stu-id="eda28-131">IMixedRealityServiceRegistrar API documentation</span></span>](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar)
- [<span data-ttu-id="eda28-132">Documentazione dell'API MixedRealityServiceRegistry</span><span class="sxs-lookup"><span data-stu-id="eda28-132">MixedRealityServiceRegistry API documentation</span></span>](xref:Microsoft.MixedReality.Toolkit.MixedRealityServiceRegistry)

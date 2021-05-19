---
title: Provider di estensioni di sistema
description: Estensioni MRTK e provider di dati
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, estensioni di sistema,
ms.openlocfilehash: add1f443edb687edfc387a316d83443779e079f9
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143499"
---
# <a name="systems-extension-services-and-data-providers"></a><span data-ttu-id="d7eee-104">Sistemi, servizi di estensione e provider di dati</span><span class="sxs-lookup"><span data-stu-id="d7eee-104">Systems, extension services and data providers</span></span>

<span data-ttu-id="d7eee-105">In Mixed Reality Toolkit molte delle funzionalità sono disponibili sotto forma di servizi.</span><span class="sxs-lookup"><span data-stu-id="d7eee-105">In the Mixed Reality Toolkit, many of the features are delivered in the form of services.</span></span> <span data-ttu-id="d7eee-106">I servizi sono raggruppati in tre categorie principali: sistemi, servizi di estensione e provider di dati.</span><span class="sxs-lookup"><span data-stu-id="d7eee-106">Services are grouped into three primary categories: systems, extension services and data providers.</span></span>

## <a name="systems"></a><span data-ttu-id="d7eee-107">-</span><span class="sxs-lookup"><span data-stu-id="d7eee-107">Systems</span></span>

<span data-ttu-id="d7eee-108">I sistemi sono servizi che forniscono le funzionalità di base di Mixed Reality Toolkit.</span><span class="sxs-lookup"><span data-stu-id="d7eee-108">Systems are services that provide the core functionality of the Mixed Reality Toolkit.</span></span> <span data-ttu-id="d7eee-109">Tutti i sistemi sono implementazioni [`IMixedRealityService`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityService) dell'interfaccia .</span><span class="sxs-lookup"><span data-stu-id="d7eee-109">All systems are implementations of the [`IMixedRealityService`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityService) interface.</span></span>

- [<span data-ttu-id="d7eee-110">BoundarySystem</span><span class="sxs-lookup"><span data-stu-id="d7eee-110">BoundarySystem</span></span>](../features/boundary/boundary-system-getting-started.md)
- [<span data-ttu-id="d7eee-111">CameraSystem</span><span class="sxs-lookup"><span data-stu-id="d7eee-111">CameraSystem</span></span>](../features/camera-system/camera-system-overview.md)
- [<span data-ttu-id="d7eee-112">DiagnosticsSystem</span><span class="sxs-lookup"><span data-stu-id="d7eee-112">DiagnosticsSystem</span></span>](../features/diagnostics/diagnostics-system-getting-started.md)
- [<span data-ttu-id="d7eee-113">InputSystem</span><span class="sxs-lookup"><span data-stu-id="d7eee-113">InputSystem</span></span>](../features/input/overview.md)
- [<span data-ttu-id="d7eee-114">SceneSystem</span><span class="sxs-lookup"><span data-stu-id="d7eee-114">SceneSystem</span></span>](../features/scene-system/scene-system-getting-started.md)
- [<span data-ttu-id="d7eee-115">SpatialAwarenessSystem</span><span class="sxs-lookup"><span data-stu-id="d7eee-115">SpatialAwarenessSystem</span></span>](../features/spatial-awareness/spatial-awareness-getting-started.md)
- [<span data-ttu-id="d7eee-116">TeleportSystem</span><span class="sxs-lookup"><span data-stu-id="d7eee-116">TeleportSystem</span></span>](../features/teleport-system/teleport-system.md)

<span data-ttu-id="d7eee-117">Ognuno dei sistemi elencati viene visualizzato nel profilo di configurazione [](../features/profiles/profiles.md)del componente MixedRealityToolkit.</span><span class="sxs-lookup"><span data-stu-id="d7eee-117">Each of the listed systems are surfaced in the MixedRealityToolkit component's configuration [profile](../features/profiles/profiles.md).</span></span>

## <a name="extensions"></a><span data-ttu-id="d7eee-118">Estensioni</span><span class="sxs-lookup"><span data-stu-id="d7eee-118">Extensions</span></span>

<span data-ttu-id="d7eee-119">I servizi di estensione sono componenti che estendono le funzionalità di Mixed Reality Toolkit.</span><span class="sxs-lookup"><span data-stu-id="d7eee-119">Extension services are components that extend the functionality of the Mixed Reality Toolkit.</span></span> <span data-ttu-id="d7eee-120">Tutti i servizi di estensione devono specificare che implementano [`IMixedRealityExtensionService`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityExtensionService) l'interfaccia .</span><span class="sxs-lookup"><span data-stu-id="d7eee-120">All extension services must specify that they implement the [`IMixedRealityExtensionService`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityExtensionService) interface.</span></span>

<span data-ttu-id="d7eee-121">Per informazioni sulla creazione di servizi di estensione, vedere [l'articolo Servizi di](../features/extensions/extension-services.md) estensione.</span><span class="sxs-lookup"><span data-stu-id="d7eee-121">For information on creating extension services, please reference the [Extension services](../features/extensions/extension-services.md) article.</span></span>

<span data-ttu-id="d7eee-122">Per essere accessibili a MRTK, i servizi di estensione vengono registrati e configurati usando la sezione Extensions del profilo di configurazione del componente MixedRealityToolkit.</span><span class="sxs-lookup"><span data-stu-id="d7eee-122">To be accessible to the MRTK, extension services are registered and configured using the Extensions section of the MixedRealityToolkit component's configuration profile.</span></span>

![Configurazione di un servizio di estensione](../features/images/profiles/ConfiguredExtensionService.png)

## <a name="data-providers"></a><span data-ttu-id="d7eee-124">Provider di dati</span><span class="sxs-lookup"><span data-stu-id="d7eee-124">Data providers</span></span>

<span data-ttu-id="d7eee-125">I provider di dati sono componenti che, in base al nome, forniscono dati a un servizio Mixed Reality Toolkit.</span><span class="sxs-lookup"><span data-stu-id="d7eee-125">Data providers are components that, per their name, provide data to a Mixed Reality Toolkit service.</span></span> <span data-ttu-id="d7eee-126">Tutti i provider di dati devono specificare che implementano [`IMixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) l'interfaccia .</span><span class="sxs-lookup"><span data-stu-id="d7eee-126">All data providers must specify that they implement the [`IMixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) interface.</span></span>

> [!NOTE]
> <span data-ttu-id="d7eee-127">Non tutti i servizi richiedono provider di dati.</span><span class="sxs-lookup"><span data-stu-id="d7eee-127">Not all services will require data providers.</span></span> <span data-ttu-id="d7eee-128">Tra i sistemi di Mixed Reality Toolkit, i sistemi di input e consapevolezza spaziale sono gli unici servizi che possono usare i provider di dati.</span><span class="sxs-lookup"><span data-stu-id="d7eee-128">Of the Mixed Reality Toolkit's systems, the Input and Spatial Awareness systems are the only services to utilize data providers.</span></span>

<span data-ttu-id="d7eee-129">Per essere accessibili al servizio MRTK specifico, i provider di dati vengono registrati nel profilo di configurazione del servizio.</span><span class="sxs-lookup"><span data-stu-id="d7eee-129">To be accessible to the specific MRTK service, data providers are registered in the service's configuration profile.</span></span>

<span data-ttu-id="d7eee-130">Il codice dell'applicazione accede ai provider di dati tramite [`IMixedRealityDataProviderAccess`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProviderAccess) l'interfaccia .</span><span class="sxs-lookup"><span data-stu-id="d7eee-130">Application code accesses data providers via the [`IMixedRealityDataProviderAccess`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProviderAccess) interface.</span></span> <span data-ttu-id="d7eee-131">Per semplificare l'accesso, i provider di dati possono essere recuperati anche tramite la `CoreServices` classe helper .</span><span class="sxs-lookup"><span data-stu-id="d7eee-131">To simplify access, data providers can also be retrieved via the `CoreServices` helper class.</span></span>

```c#
var inputSimulationService = CoreServices.GetDataProvider<IInputSimulationService>(CoreServices.InputSystem);
```

> [!IMPORTANT]
> <span data-ttu-id="d7eee-132">Anche `IMixedRealityDataProvider` se eredita da , i provider di dati non sono registrati con `IMixedRealityService` `MixedRealityServiceRegistry` .</span><span class="sxs-lookup"><span data-stu-id="d7eee-132">Although `IMixedRealityDataProvider` inherits from `IMixedRealityService`, data providers are not registered with the `MixedRealityServiceRegistry`.</span></span> <span data-ttu-id="d7eee-133">Per accedere ai provider di dati, il codice dell'applicazione deve eseguire una query sull'istanza del servizio per cui sono stati registrati (ad esempio, il sistema di input).</span><span class="sxs-lookup"><span data-stu-id="d7eee-133">To access data providers, application code must query the service instance for which they were registered (ex: input system).</span></span>

### <a name="input"></a><span data-ttu-id="d7eee-134">Input</span><span class="sxs-lookup"><span data-stu-id="d7eee-134">Input</span></span>

<span data-ttu-id="d7eee-135">Il sistema di input MRTK usa solo provider di dati che implementano [`IMixedRealityInputDeviceManager`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputDeviceManager) .</span><span class="sxs-lookup"><span data-stu-id="d7eee-135">The MRTK input system utilizes only data providers that implement the [`IMixedRealityInputDeviceManager`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputDeviceManager).</span></span>

![Provider di dati di sistema di input](../features/images/input/RegisteredServiceProviders.PNG)

<span data-ttu-id="d7eee-137">L'esempio seguente illustra l'accesso al provider di simulazione di input e l'attivazione/disattivazione della proprietà SmoothEyeTracking.</span><span class="sxs-lookup"><span data-stu-id="d7eee-137">The following example demonstrates accessing the input simulation provider and toggle the SmoothEyeTracking property.</span></span>

```c#
IMixedRealityDataProviderAccess dataProviderAccess = CoreServices.InputSystem as IMixedRealityDataProviderAccess;

if (dataProviderAccess != null)
{
    IInputSimulationService inputSimulation =
        dataProviderAccess.GetDataProvider<IInputSimulationService>();

    if (inputSimulation != null)
    {
        inputSimulation.SmoothEyeTracking = !inputSimulation.SmoothEyeTracking;
    }
}
```

<span data-ttu-id="d7eee-138">L'accesso a un provider di dati per il sistema di input di base può anche essere semplificato tramite l'uso della `CoreServices` classe helper .</span><span class="sxs-lookup"><span data-stu-id="d7eee-138">Accessing a data provider for the core input system can also be simplified via use of the `CoreServices` helper class.</span></span>

```c#
var inputSimulationService = CoreServices.GetInputSystemDataProvider<IInputSimulationService>();
if (inputSimulationService != null)
{
    // do something here
}
```

> [!NOTE]
> <span data-ttu-id="d7eee-139">Il sistema di input restituisce solo i provider di dati supportati per la piattaforma in cui è in esecuzione l'applicazione.</span><span class="sxs-lookup"><span data-stu-id="d7eee-139">The input system returns only data providers that are supported for the platform on which the application is running.</span></span>

<span data-ttu-id="d7eee-140">Per informazioni sulla scrittura di un provider di dati per il sistema di input MRTK, vedere Creazione [di un provider di dati del sistema di input.](../features/input/create-data-provider.md)</span><span class="sxs-lookup"><span data-stu-id="d7eee-140">For information on writing a data provider for the MRTK input system, please see [creating an input system data provider](../features/input/create-data-provider.md).</span></span>

### <a name="spatial-awareness"></a><span data-ttu-id="d7eee-141">Consapevolezza spaziale</span><span class="sxs-lookup"><span data-stu-id="d7eee-141">Spatial awareness</span></span>

<span data-ttu-id="d7eee-142">Il sistema di consapevolezza spaziale di MRTK usa solo provider di dati che implementano [`IMixedRealitySpatialAwarenessObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver) l'interfaccia .</span><span class="sxs-lookup"><span data-stu-id="d7eee-142">The MRTK spatial awareness system utilizes only data providers that implement the [`IMixedRealitySpatialAwarenessObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver) interface.</span></span>

![Provider di dati del sistema di consapevolezza spaziale](../features/images/spatial-awareness/SpatialAwarenessProfile.png)

<span data-ttu-id="d7eee-144">L'esempio seguente illustra l'accesso ai provider di dati di mesh spaziali registrati e la modifica della visibilità delle mesh.</span><span class="sxs-lookup"><span data-stu-id="d7eee-144">The following example demonstrates accessing the registered spatial mesh data providers and changing the visibility of the meshes.</span></span>

```c#
IMixedRealityDataProviderAccess dataProviderAccess =
    CoreServices.SpatialAwarenessSystem as IMixedRealityDataProviderAccess;

if (dataProviderAccess != null)
{
    IReadOnlyList<IMixedRealitySpatialAwarenessMeshObserver> observers =
        dataProviderAccess.GetDataProviders<IMixedRealitySpatialAwarenessMeshObserver>();

    foreach (IMixedRealitySpatialAwarenessMeshObserver observer in observers)
    {
        // Set the mesh to use the occlusion material
        observer.DisplayOption = SpatialMeshDisplayOptions.Occlusion;
    }
}
```

<span data-ttu-id="d7eee-145">L'accesso a un provider di dati per il sistema di riconoscimento spaziale principale può essere semplificato anche tramite l'uso della `CoreServices` classe helper.</span><span class="sxs-lookup"><span data-stu-id="d7eee-145">Accessing a data provider for the core spatial awareness system can also be simplified via use of the `CoreServices` helper class.</span></span>

```c#
var dataProvider = CoreServices.GetSpatialAwarenessSystemDataProvider<IMixedRealitySpatialAwarenessMeshObserver>();
if (dataProvider != null)
{
    // do something here
}
```

> [!NOTE]
> <span data-ttu-id="d7eee-146">Il sistema di riconoscimento spaziale restituisce solo i provider di dati supportati per la piattaforma in cui è in esecuzione l'applicazione.</span><span class="sxs-lookup"><span data-stu-id="d7eee-146">The spatial awareness system returns only data providers that are supported for the platform on which the application is running.</span></span>

<span data-ttu-id="d7eee-147">Per informazioni sulla scrittura di un provider di dati per il sistema di riconoscimento spaziale MRTK, vedere Creazione di un provider di dati [del sistema di riconoscimento spaziale](../features/spatial-awareness/create-data-provider.md).</span><span class="sxs-lookup"><span data-stu-id="d7eee-147">For information on writing a data provider for the MRTK spatial awareness system, please see [creating a spatial awareness system data provider](../features/spatial-awareness/create-data-provider.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d7eee-148">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="d7eee-148">See also</span></span>

- [<span data-ttu-id="d7eee-149">Servizi di estensione</span><span class="sxs-lookup"><span data-stu-id="d7eee-149">Extension services</span></span>](../features/extensions/extension-services.md)
- [<span data-ttu-id="d7eee-150">Creazione di un provider di dati del sistema di input</span><span class="sxs-lookup"><span data-stu-id="d7eee-150">Creating an input system data provider</span></span>](../features/input/create-data-provider.md)
- [<span data-ttu-id="d7eee-151">Creazione di un provider di dati del sistema di riconoscimento spaziale</span><span class="sxs-lookup"><span data-stu-id="d7eee-151">Creating a spatial awareness system system data provider</span></span>](../features/spatial-awareness/create-data-provider.md)
- [<span data-ttu-id="d7eee-152">Interfaccia IMixedRealityService</span><span class="sxs-lookup"><span data-stu-id="d7eee-152">IMixedRealityService interface</span></span>](xref:Microsoft.MixedReality.Toolkit.IMixedRealityService)
- [<span data-ttu-id="d7eee-153">Interfaccia IMixedRealityDataProvider</span><span class="sxs-lookup"><span data-stu-id="d7eee-153">IMixedRealityDataProvider interface</span></span>](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider)
- [<span data-ttu-id="d7eee-154">Interfaccia IMixedRealityExtensionService</span><span class="sxs-lookup"><span data-stu-id="d7eee-154">IMixedRealityExtensionService interface</span></span>](xref:Microsoft.MixedReality.Toolkit.IMixedRealityExtensionService)

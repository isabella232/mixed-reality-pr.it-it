---
title: SystemExtensionsProvider
description: Estensioni MRTK e provider di dati
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, estensioni di sistema,
ms.openlocfilehash: e59a9ef2609ea0fcdc6ff2a18e427ea9fa7a4120
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/03/2021
ms.locfileid: "101782041"
---
# <a name="systems-extension-services-and-data-providers"></a><span data-ttu-id="b2510-104">Sistemi, servizi di estensione e provider di dati</span><span class="sxs-lookup"><span data-stu-id="b2510-104">Systems, extension services and data providers</span></span>

<span data-ttu-id="b2510-105">Nel Toolkit per la realtà mista, molte delle funzionalità vengono fornite sotto forma di servizi.</span><span class="sxs-lookup"><span data-stu-id="b2510-105">In the Mixed Reality Toolkit, many of the features are delivered in the form of services.</span></span> <span data-ttu-id="b2510-106">I servizi sono raggruppati in tre categorie principali: sistemi, servizi di estensione e provider di dati.</span><span class="sxs-lookup"><span data-stu-id="b2510-106">Services are grouped into three primary categories: systems, extension services and data providers.</span></span>

## <a name="systems"></a><span data-ttu-id="b2510-107">-</span><span class="sxs-lookup"><span data-stu-id="b2510-107">Systems</span></span>

<span data-ttu-id="b2510-108">I sistemi sono servizi che forniscono le funzionalità principali del Toolkit di realtà mista.</span><span class="sxs-lookup"><span data-stu-id="b2510-108">Systems are services that provide the core functionality of the Mixed Reality Toolkit.</span></span> <span data-ttu-id="b2510-109">Tutti i sistemi sono implementazioni dell' [`IMixedRealityService`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityService) interfaccia.</span><span class="sxs-lookup"><span data-stu-id="b2510-109">All systems are implementations of the [`IMixedRealityService`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityService) interface.</span></span>

- [<span data-ttu-id="b2510-110">BoundarySystem</span><span class="sxs-lookup"><span data-stu-id="b2510-110">BoundarySystem</span></span>](../features/Boundary/BoundarySystemGettingStarted.md)
- [<span data-ttu-id="b2510-111">CameraSystem</span><span class="sxs-lookup"><span data-stu-id="b2510-111">CameraSystem</span></span>](../features/CameraSystem/CameraSystemOverview.md)
- [<span data-ttu-id="b2510-112">DiagnosticsSystem</span><span class="sxs-lookup"><span data-stu-id="b2510-112">DiagnosticsSystem</span></span>](../features/Diagnostics/DiagnosticsSystemGettingStarted.md)
- [<span data-ttu-id="b2510-113">InputSystem</span><span class="sxs-lookup"><span data-stu-id="b2510-113">InputSystem</span></span>](../features/Input/Overview.md)
- [<span data-ttu-id="b2510-114">SceneSystem</span><span class="sxs-lookup"><span data-stu-id="b2510-114">SceneSystem</span></span>](../features/SceneSystem/SceneSystemGettingStarted.md)
- [<span data-ttu-id="b2510-115">SpatialAwarenessSystem</span><span class="sxs-lookup"><span data-stu-id="b2510-115">SpatialAwarenessSystem</span></span>](../features/SpatialAwareness/SpatialAwarenessGettingStarted.md)
- [<span data-ttu-id="b2510-116">TeleportSystem</span><span class="sxs-lookup"><span data-stu-id="b2510-116">TeleportSystem</span></span>](../features/TeleportSystem/Overview.md)

<span data-ttu-id="b2510-117">Ognuno dei sistemi elencati viene esposto nel [profilo](../features/Profiles/Profiles.md)di configurazione del componente MixedRealityToolkit.</span><span class="sxs-lookup"><span data-stu-id="b2510-117">Each of the listed systems are surfaced in the MixedRealityToolkit component's configuration [profile](../features/Profiles/Profiles.md).</span></span>

## <a name="extensions"></a><span data-ttu-id="b2510-118">Estensioni</span><span class="sxs-lookup"><span data-stu-id="b2510-118">Extensions</span></span>

<span data-ttu-id="b2510-119">I servizi di estensione sono componenti che estendono le funzionalità del Toolkit di realtà mista.</span><span class="sxs-lookup"><span data-stu-id="b2510-119">Extension services are components that extend the functionality of the Mixed Reality Toolkit.</span></span> <span data-ttu-id="b2510-120">Tutti i servizi di estensione devono specificare che implementano l' [`IMixedRealityExtensionService`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityExtensionService) interfaccia.</span><span class="sxs-lookup"><span data-stu-id="b2510-120">All extension services must specify that they implement the [`IMixedRealityExtensionService`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityExtensionService) interface.</span></span>

<span data-ttu-id="b2510-121">Per informazioni sulla creazione di servizi di estensione, fare riferimento all'articolo [servizi di estensione](../features/Extensions/ExtensionServices.md) .</span><span class="sxs-lookup"><span data-stu-id="b2510-121">For information on creating extension services, please reference the [Extension services](../features/Extensions/ExtensionServices.md) article.</span></span>

<span data-ttu-id="b2510-122">Per poter accedere a MRTK, i servizi di estensione sono registrati e configurati usando la sezione Extensions del profilo di configurazione del componente MixedRealityToolkit.</span><span class="sxs-lookup"><span data-stu-id="b2510-122">To be accessible to the MRTK, extension services are registered and configured using the Extensions section of the MixedRealityToolkit component's configuration profile.</span></span>

![Configurazione di un servizio di estensione](../features/Images/Profiles/ConfiguredExtensionService.png)

## <a name="data-providers"></a><span data-ttu-id="b2510-124">Provider di dati</span><span class="sxs-lookup"><span data-stu-id="b2510-124">Data providers</span></span>

<span data-ttu-id="b2510-125">I provider di dati sono componenti che, per nome, forniscono dati a un servizio Toolkit di realtà mista.</span><span class="sxs-lookup"><span data-stu-id="b2510-125">Data providers are components that, per their name, provide data to a Mixed Reality Toolkit service.</span></span> <span data-ttu-id="b2510-126">Tutti i provider di dati devono specificare che implementano l' [`IMixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) interfaccia.</span><span class="sxs-lookup"><span data-stu-id="b2510-126">All data providers must specify that they implement the [`IMixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) interface.</span></span>

> [!NOTE]
> <span data-ttu-id="b2510-127">Non tutti i servizi richiedono provider di dati.</span><span class="sxs-lookup"><span data-stu-id="b2510-127">Not all services will require data providers.</span></span> <span data-ttu-id="b2510-128">Dei sistemi del Toolkit di realtà mista, i sistemi di riconoscimento spaziale e di input sono gli unici servizi per usare i provider di dati.</span><span class="sxs-lookup"><span data-stu-id="b2510-128">Of the Mixed Reality Toolkit's systems, the Input and Spatial Awareness systems are the only services to utilize data providers.</span></span>

<span data-ttu-id="b2510-129">Per essere accessibile al servizio MRTK specifico, i provider di dati vengono registrati nel profilo di configurazione del servizio.</span><span class="sxs-lookup"><span data-stu-id="b2510-129">To be accessible to the specific MRTK service, data providers are registered in the service's configuration profile.</span></span>

<span data-ttu-id="b2510-130">Il codice dell'applicazione accede ai provider di dati tramite l' [`IMixedRealityDataProviderAccess`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProviderAccess) interfaccia.</span><span class="sxs-lookup"><span data-stu-id="b2510-130">Application code accesses data providers via the [`IMixedRealityDataProviderAccess`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProviderAccess) interface.</span></span> <span data-ttu-id="b2510-131">Per semplificare l'accesso, è inoltre possibile recuperare i provider di dati tramite la `CoreServices` classe helper.</span><span class="sxs-lookup"><span data-stu-id="b2510-131">To simplify access, data providers can also be retrieved via the `CoreServices` helper class.</span></span>

```c#
var inputSimulationService = CoreServices.GetDataProvider<IInputSimulationService>(CoreServices.InputSystem);
```

> [!IMPORTANT]
> <span data-ttu-id="b2510-132">Sebbene `IMixedRealityDataProvider` erediti da `IMixedRealityService` , i provider di dati non sono registrati con `MixedRealityServiceRegistry` .</span><span class="sxs-lookup"><span data-stu-id="b2510-132">Although `IMixedRealityDataProvider` inherits from `IMixedRealityService`, data providers are not registered with the `MixedRealityServiceRegistry`.</span></span> <span data-ttu-id="b2510-133">Per accedere ai provider di dati, il codice dell'applicazione deve eseguire una query sull'istanza del servizio per la quale sono stati registrati (ad esempio, il sistema di input).</span><span class="sxs-lookup"><span data-stu-id="b2510-133">To access data providers, application code must query the service instance for which they were registered (ex: input system).</span></span>

### <a name="input"></a><span data-ttu-id="b2510-134">Input</span><span class="sxs-lookup"><span data-stu-id="b2510-134">Input</span></span>

<span data-ttu-id="b2510-135">Il sistema di input MRTK utilizza solo i provider di dati che implementano [`IMixedRealityInputDeviceManager`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputDeviceManager) .</span><span class="sxs-lookup"><span data-stu-id="b2510-135">The MRTK input system utilizes only data providers that implement the [`IMixedRealityInputDeviceManager`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputDeviceManager).</span></span>

![Provider di dati di sistema di input](../features/Images/Input/RegisteredServiceProviders.PNG)

<span data-ttu-id="b2510-137">Nell'esempio seguente viene illustrato l'accesso al provider della simulazione di input e la proprietà SmoothEyeTracking.</span><span class="sxs-lookup"><span data-stu-id="b2510-137">The following example demonstrates accessing the input simulation provider and toggle the SmoothEyeTracking property.</span></span>

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

<span data-ttu-id="b2510-138">L'accesso a un provider di dati per il sistema di input di base può anche essere semplificato tramite l'uso della `CoreServices` classe helper.</span><span class="sxs-lookup"><span data-stu-id="b2510-138">Accessing a data provider for the core input system can also be simplified via use of the `CoreServices` helper class.</span></span>

```c#
var inputSimulationService = CoreServices.GetInputSystemDataProvider<IInputSimulationService>();
if (inputSimulationService != null)
{
    // do something here
}
```

> [!NOTE]
> <span data-ttu-id="b2510-139">Il sistema di input restituisce solo i provider di dati supportati per la piattaforma in cui è in esecuzione l'applicazione.</span><span class="sxs-lookup"><span data-stu-id="b2510-139">The input system returns only data providers that are supported for the platform on which the application is running.</span></span>

<span data-ttu-id="b2510-140">Per informazioni sulla scrittura di un provider di dati per il sistema di input MRTK, vedere [creazione di un provider di dati di sistema di input](../features/Input/CreateDataProvider.md).</span><span class="sxs-lookup"><span data-stu-id="b2510-140">For information on writing a data provider for the MRTK input system, please see [creating an input system data provider](../features/Input/CreateDataProvider.md).</span></span>

### <a name="spatial-awareness"></a><span data-ttu-id="b2510-141">Consapevolezza spaziale</span><span class="sxs-lookup"><span data-stu-id="b2510-141">Spatial awareness</span></span>

<span data-ttu-id="b2510-142">Il sistema di riconoscimento spaziale MRTK utilizza solo i provider di dati che implementano l' [`IMixedRealitySpatialAwarenessObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver) interfaccia.</span><span class="sxs-lookup"><span data-stu-id="b2510-142">The MRTK spatial awareness system utilizes only data providers that implement the [`IMixedRealitySpatialAwarenessObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver) interface.</span></span>

![Provider di dati del sistema di riconoscimento spaziale](../features/Images/SpatialAwareness/SpatialAwarenessProfile.png)

<span data-ttu-id="b2510-144">Nell'esempio seguente viene illustrato l'accesso ai provider di dati di mesh spaziali registrati e la modifica della visibilità dei mesh.</span><span class="sxs-lookup"><span data-stu-id="b2510-144">The following example demonstrates accessing the registered spatial mesh data providers and changing the visibility of the meshes.</span></span>

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

<span data-ttu-id="b2510-145">L'accesso a un provider di dati per il sistema di riconoscimento spaziale principale può anche essere semplificato tramite l'uso della `CoreServices` classe helper.</span><span class="sxs-lookup"><span data-stu-id="b2510-145">Accessing a data provider for the core spatial awareness system can also be simplified via use of the `CoreServices` helper class.</span></span>

```c#
var dataProvider = CoreServices.GetSpatialAwarenessSystemDataProvider<IMixedRealitySpatialAwarenessMeshObserver>();
if (dataProvider != null)
{
    // do something here
}
```

> [!NOTE]
> <span data-ttu-id="b2510-146">Il sistema di riconoscimento spaziale restituisce solo i provider di dati supportati per la piattaforma in cui è in esecuzione l'applicazione.</span><span class="sxs-lookup"><span data-stu-id="b2510-146">The spatial awareness system returns only data providers that are supported for the platform on which the application is running.</span></span>

<span data-ttu-id="b2510-147">Per informazioni sulla scrittura di un provider di dati per il sistema di riconoscimento spaziale MRTK, vedere [creazione di un provider di dati di sistema per la consapevolezza spaziale](../features/SpatialAwareness/CreateDataProvider.md).</span><span class="sxs-lookup"><span data-stu-id="b2510-147">For information on writing a data provider for the MRTK spatial awareness system, please see [creating a spatial awareness system data provider](../features/SpatialAwareness/CreateDataProvider.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="b2510-148">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="b2510-148">See also</span></span>

- [<span data-ttu-id="b2510-149">Cosa rende una funzionalità di realtà mista</span><span class="sxs-lookup"><span data-stu-id="b2510-149">What makes a mixed reality feature</span></span>](../out-of-scope/MixedRealityServices.md)
- [<span data-ttu-id="b2510-150">Servizi di estensione</span><span class="sxs-lookup"><span data-stu-id="b2510-150">Extension services</span></span>](../features/Extensions/ExtensionServices.md)
- [<span data-ttu-id="b2510-151">Creazione di un provider di dati di sistema di input</span><span class="sxs-lookup"><span data-stu-id="b2510-151">Creating an input system data provider</span></span>](../features/Input/CreateDataProvider.md)
- [<span data-ttu-id="b2510-152">Creazione di un provider di dati di sistema del sistema di riconoscimento spaziale</span><span class="sxs-lookup"><span data-stu-id="b2510-152">Creating a spatial awareness system system data provider</span></span>](../features/SpatialAwareness/CreateDataProvider.md)
- [<span data-ttu-id="b2510-153">Interfaccia IMixedRealityService</span><span class="sxs-lookup"><span data-stu-id="b2510-153">IMixedRealityService interface</span></span>](xref:Microsoft.MixedReality.Toolkit.IMixedRealityService)
- [<span data-ttu-id="b2510-154">Interfaccia IMixedRealityDataProvider</span><span class="sxs-lookup"><span data-stu-id="b2510-154">IMixedRealityDataProvider interface</span></span>](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider)
- [<span data-ttu-id="b2510-155">Interfaccia IMixedRealityExtensionService</span><span class="sxs-lookup"><span data-stu-id="b2510-155">IMixedRealityExtensionService interface</span></span>](xref:Microsoft.MixedReality.Toolkit.IMixedRealityExtensionService)

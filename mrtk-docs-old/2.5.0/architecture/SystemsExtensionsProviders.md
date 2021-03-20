---
title: SystemExtensionsProvider
description: Estensioni MRTK e provider di dati
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, estensioni di sistema,
ms.openlocfilehash: 3b48f8f6fa8612fdd3c54425454c13843a718042
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2021
ms.locfileid: "104692248"
---
# <a name="systems-extension-services-and-data-providers"></a>Sistemi, servizi di estensione e provider di dati

Nel Toolkit per la realtà mista, molte delle funzionalità vengono fornite sotto forma di servizi. I servizi sono raggruppati in tre categorie principali: sistemi, servizi di estensione e provider di dati.

## <a name="systems"></a>-

I sistemi sono servizi che forniscono le funzionalità principali del Toolkit di realtà mista. Tutti i sistemi sono implementazioni dell' [`IMixedRealityService`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityService) interfaccia.

- [BoundarySystem](../features/Boundary/BoundarySystemGettingStarted.md)
- [CameraSystem](../features/CameraSystem/CameraSystemOverview.md)
- [DiagnosticsSystem](../features/Diagnostics/DiagnosticsSystemGettingStarted.md)
- [InputSystem](../features/Input/Overview.md)
- [SceneSystem](../features/SceneSystem/SceneSystemGettingStarted.md)
- [SpatialAwarenessSystem](../features/SpatialAwareness/SpatialAwarenessGettingStarted.md)
- [TeleportSystem](../features/TeleportSystem/Overview.md)

Ognuno dei sistemi elencati viene esposto nel [profilo](../features/Profiles/Profiles.md)di configurazione del componente MixedRealityToolkit.

## <a name="extensions"></a>Estensioni

I servizi di estensione sono componenti che estendono le funzionalità del Toolkit di realtà mista. Tutti i servizi di estensione devono specificare che implementano l' [`IMixedRealityExtensionService`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityExtensionService) interfaccia.

Per informazioni sulla creazione di servizi di estensione, fare riferimento all'articolo [servizi di estensione](../features/Extensions/ExtensionServices.md) .

Per poter accedere a MRTK, i servizi di estensione sono registrati e configurati usando la sezione Extensions del profilo di configurazione del componente MixedRealityToolkit.

![Configurazione di un servizio di estensione](../features/Images/Profiles/ConfiguredExtensionService.png)

## <a name="data-providers"></a>Provider di dati

I provider di dati sono componenti che, per nome, forniscono dati a un servizio Toolkit di realtà mista. Tutti i provider di dati devono specificare che implementano l' [`IMixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) interfaccia.

> [!NOTE]
> Non tutti i servizi richiedono provider di dati. Dei sistemi del Toolkit di realtà mista, i sistemi di riconoscimento spaziale e di input sono gli unici servizi per usare i provider di dati.

Per essere accessibile al servizio MRTK specifico, i provider di dati vengono registrati nel profilo di configurazione del servizio.

Il codice dell'applicazione accede ai provider di dati tramite l' [`IMixedRealityDataProviderAccess`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProviderAccess) interfaccia. Per semplificare l'accesso, è inoltre possibile recuperare i provider di dati tramite la `CoreServices` classe helper.

```c#
var inputSimulationService = CoreServices.GetDataProvider<IInputSimulationService>(CoreServices.InputSystem);
```

> [!IMPORTANT]
> Sebbene `IMixedRealityDataProvider` erediti da `IMixedRealityService` , i provider di dati non sono registrati con `MixedRealityServiceRegistry` . Per accedere ai provider di dati, il codice dell'applicazione deve eseguire una query sull'istanza del servizio per la quale sono stati registrati (ad esempio, il sistema di input).

### <a name="input"></a>Input

Il sistema di input MRTK utilizza solo i provider di dati che implementano [`IMixedRealityInputDeviceManager`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputDeviceManager) .

![Provider di dati di sistema di input](../features/Images/Input/RegisteredServiceProviders.PNG)

Nell'esempio seguente viene illustrato l'accesso al provider della simulazione di input e la proprietà SmoothEyeTracking.

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

L'accesso a un provider di dati per il sistema di input di base può anche essere semplificato tramite l'uso della `CoreServices` classe helper.

```c#
var inputSimulationService = CoreServices.GetInputSystemDataProvider<IInputSimulationService>();
if (inputSimulationService != null)
{
    // do something here
}
```

> [!NOTE]
> Il sistema di input restituisce solo i provider di dati supportati per la piattaforma in cui è in esecuzione l'applicazione.

Per informazioni sulla scrittura di un provider di dati per il sistema di input MRTK, vedere [creazione di un provider di dati di sistema di input](../features/Input/CreateDataProvider.md).

### <a name="spatial-awareness"></a>Consapevolezza spaziale

Il sistema di riconoscimento spaziale MRTK utilizza solo i provider di dati che implementano l' [`IMixedRealitySpatialAwarenessObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver) interfaccia.

![Provider di dati del sistema di riconoscimento spaziale](../features/Images/SpatialAwareness/SpatialAwarenessProfile.png)

Nell'esempio seguente viene illustrato l'accesso ai provider di dati di mesh spaziali registrati e la modifica della visibilità dei mesh.

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

L'accesso a un provider di dati per il sistema di riconoscimento spaziale principale può anche essere semplificato tramite l'uso della `CoreServices` classe helper.

```c#
var dataProvider = CoreServices.GetSpatialAwarenessSystemDataProvider<IMixedRealitySpatialAwarenessMeshObserver>();
if (dataProvider != null)
{
    // do something here
}
```

> [!NOTE]
> Il sistema di riconoscimento spaziale restituisce solo i provider di dati supportati per la piattaforma in cui è in esecuzione l'applicazione.

Per informazioni sulla scrittura di un provider di dati per il sistema di riconoscimento spaziale MRTK, vedere [creazione di un provider di dati di sistema per la consapevolezza spaziale](../features/SpatialAwareness/CreateDataProvider.md).

## <a name="see-also"></a>Vedi anche

- [Cosa rende una funzionalità di realtà mista](../out-of-scope/MixedRealityServices.md)
- [Servizi di estensione](../features/Extensions/ExtensionServices.md)
- [Creazione di un provider di dati di sistema di input](../features/Input/CreateDataProvider.md)
- [Creazione di un provider di dati di sistema del sistema di riconoscimento spaziale](../features/SpatialAwareness/CreateDataProvider.md)
- [Interfaccia IMixedRealityService](xref:Microsoft.MixedReality.Toolkit.IMixedRealityService)
- [Interfaccia IMixedRealityDataProvider](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider)
- [Interfaccia IMixedRealityExtensionService](xref:Microsoft.MixedReality.Toolkit.IMixedRealityExtensionService)

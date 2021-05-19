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
# <a name="systems-extension-services-and-data-providers"></a>Sistemi, servizi di estensione e provider di dati

In Mixed Reality Toolkit molte delle funzionalità sono disponibili sotto forma di servizi. I servizi sono raggruppati in tre categorie principali: sistemi, servizi di estensione e provider di dati.

## <a name="systems"></a>-

I sistemi sono servizi che forniscono le funzionalità di base di Mixed Reality Toolkit. Tutti i sistemi sono implementazioni [`IMixedRealityService`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityService) dell'interfaccia .

- [BoundarySystem](../features/boundary/boundary-system-getting-started.md)
- [CameraSystem](../features/camera-system/camera-system-overview.md)
- [DiagnosticsSystem](../features/diagnostics/diagnostics-system-getting-started.md)
- [InputSystem](../features/input/overview.md)
- [SceneSystem](../features/scene-system/scene-system-getting-started.md)
- [SpatialAwarenessSystem](../features/spatial-awareness/spatial-awareness-getting-started.md)
- [TeleportSystem](../features/teleport-system/teleport-system.md)

Ognuno dei sistemi elencati viene visualizzato nel profilo di configurazione [](../features/profiles/profiles.md)del componente MixedRealityToolkit.

## <a name="extensions"></a>Estensioni

I servizi di estensione sono componenti che estendono le funzionalità di Mixed Reality Toolkit. Tutti i servizi di estensione devono specificare che implementano [`IMixedRealityExtensionService`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityExtensionService) l'interfaccia .

Per informazioni sulla creazione di servizi di estensione, vedere [l'articolo Servizi di](../features/extensions/extension-services.md) estensione.

Per essere accessibili a MRTK, i servizi di estensione vengono registrati e configurati usando la sezione Extensions del profilo di configurazione del componente MixedRealityToolkit.

![Configurazione di un servizio di estensione](../features/images/profiles/ConfiguredExtensionService.png)

## <a name="data-providers"></a>Provider di dati

I provider di dati sono componenti che, in base al nome, forniscono dati a un servizio Mixed Reality Toolkit. Tutti i provider di dati devono specificare che implementano [`IMixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) l'interfaccia .

> [!NOTE]
> Non tutti i servizi richiedono provider di dati. Tra i sistemi di Mixed Reality Toolkit, i sistemi di input e consapevolezza spaziale sono gli unici servizi che possono usare i provider di dati.

Per essere accessibili al servizio MRTK specifico, i provider di dati vengono registrati nel profilo di configurazione del servizio.

Il codice dell'applicazione accede ai provider di dati tramite [`IMixedRealityDataProviderAccess`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProviderAccess) l'interfaccia . Per semplificare l'accesso, i provider di dati possono essere recuperati anche tramite la `CoreServices` classe helper .

```c#
var inputSimulationService = CoreServices.GetDataProvider<IInputSimulationService>(CoreServices.InputSystem);
```

> [!IMPORTANT]
> Anche `IMixedRealityDataProvider` se eredita da , i provider di dati non sono registrati con `IMixedRealityService` `MixedRealityServiceRegistry` . Per accedere ai provider di dati, il codice dell'applicazione deve eseguire una query sull'istanza del servizio per cui sono stati registrati (ad esempio, il sistema di input).

### <a name="input"></a>Input

Il sistema di input MRTK usa solo provider di dati che implementano [`IMixedRealityInputDeviceManager`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputDeviceManager) .

![Provider di dati di sistema di input](../features/images/input/RegisteredServiceProviders.PNG)

L'esempio seguente illustra l'accesso al provider di simulazione di input e l'attivazione/disattivazione della proprietà SmoothEyeTracking.

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

L'accesso a un provider di dati per il sistema di input di base può anche essere semplificato tramite l'uso della `CoreServices` classe helper .

```c#
var inputSimulationService = CoreServices.GetInputSystemDataProvider<IInputSimulationService>();
if (inputSimulationService != null)
{
    // do something here
}
```

> [!NOTE]
> Il sistema di input restituisce solo i provider di dati supportati per la piattaforma in cui è in esecuzione l'applicazione.

Per informazioni sulla scrittura di un provider di dati per il sistema di input MRTK, vedere Creazione [di un provider di dati del sistema di input.](../features/input/create-data-provider.md)

### <a name="spatial-awareness"></a>Consapevolezza spaziale

Il sistema di consapevolezza spaziale di MRTK usa solo provider di dati che implementano [`IMixedRealitySpatialAwarenessObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver) l'interfaccia .

![Provider di dati del sistema di consapevolezza spaziale](../features/images/spatial-awareness/SpatialAwarenessProfile.png)

L'esempio seguente illustra l'accesso ai provider di dati di mesh spaziali registrati e la modifica della visibilità delle mesh.

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

L'accesso a un provider di dati per il sistema di riconoscimento spaziale principale può essere semplificato anche tramite l'uso della `CoreServices` classe helper.

```c#
var dataProvider = CoreServices.GetSpatialAwarenessSystemDataProvider<IMixedRealitySpatialAwarenessMeshObserver>();
if (dataProvider != null)
{
    // do something here
}
```

> [!NOTE]
> Il sistema di riconoscimento spaziale restituisce solo i provider di dati supportati per la piattaforma in cui è in esecuzione l'applicazione.

Per informazioni sulla scrittura di un provider di dati per il sistema di riconoscimento spaziale MRTK, vedere Creazione di un provider di dati [del sistema di riconoscimento spaziale](../features/spatial-awareness/create-data-provider.md).

## <a name="see-also"></a>Vedi anche

- [Servizi di estensione](../features/extensions/extension-services.md)
- [Creazione di un provider di dati del sistema di input](../features/input/create-data-provider.md)
- [Creazione di un provider di dati del sistema di riconoscimento spaziale](../features/spatial-awareness/create-data-provider.md)
- [Interfaccia IMixedRealityService](xref:Microsoft.MixedReality.Toolkit.IMixedRealityService)
- [Interfaccia IMixedRealityDataProvider](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider)
- [Interfaccia IMixedRealityExtensionService](xref:Microsoft.MixedReality.Toolkit.IMixedRealityExtensionService)

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
ms.locfileid: "104680594"
---
# <a name="what-are-the-mixedrealityserviceregistry-and-imixedrealityserviceregistrar"></a>Quali sono MixedRealityServiceRegistry e IMixedRealityServiceRegistrar?

Il Toolkit di realtà mista ha due componenti denominati molto simili che eseguono attività correlate: MixedRealityServiceRegistry e IMixedRealityServiceRegistrar.

## <a name="mixedrealityserviceregistry"></a>MixedRealityServiceRegistry

[MixedRealityServiceRegistry](xref:Microsoft.MixedReality.Toolkit.MixedRealityServiceRegistry) è il componente che contiene le istanze di ogni servizio registrato (sistemi core e servizi di estensione).

> [!NOTE]
> MixedRealityServiceRegistry contiene istanze di oggetti che implementano l'interfaccia [IMixedRealityService](xref:Microsoft.MixedReality.Toolkit.IMixedRealityService) , incluso [IMixedRealityExtensionService](xref:Microsoft.MixedReality.Toolkit.IMixedRealityExtensionService).
>
>Gli oggetti che implementano [IMixedRealityDataProvider](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) (una sottoclasse di IMixedRealityService) non sono registrati in modo esplicito nel MixedRealityServiceRegistry. Questi oggetti vengono gestiti dai singoli servizi (ad esempio, la consapevolezza spaziale).

MixedRealityServiceRegistry viene implementato come classe C# statica ed è il modello consigliato da usare per acquisire le istanze del servizio nel codice dell'applicazione.

Il frammento di codice seguente illustra l'acquisizione di un'istanza di IMixedRealityInputSystem.

```c#
IMixedRealityInputSystem inputSystem = null;

if (!MixedRealityServiceRegistry.TryGetService<IMixedRealityInputSystem>(out inputSystem))
{
    // Failed to acquire the input system. It may not have been registered
}
```

## <a name="imixedrealityserviceregistrar"></a>IMixedRealityServiceRegistrar

[IMixedRealityServiceRegistrar](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) è l'interfaccia che definisce la funzionalità implementata dai componenti che gestiscono la registrazione di uno o più servizi. I componenti che implementano IMixedRealityServiceRegistrar sono responsabili dell'aggiunta e della rimozione dei dati all'interno di MixedRealityServiceRegistry. L'oggetto [MixedRealityToolkit](xref:Microsoft.MixedReality.Toolkit.MixedRealityToolkit) è un componente di questo tipo.

Altri registrar si trovano nella cartella MRTK/SDK/Experimental/Features. Questi componenti possono essere usati per aggiungere il supporto di un singolo servizio (ad esempio, la consapevolezza spaziale) a un'applicazione. Questi singoli gestori di servizi sono elencati di seguito.

- [BoundarySystemManager](xref:Microsoft.MixedReality.Toolkit.Experimental.Boundary.BoundarySystemManager)
- [CameraSystemManager](xref:Microsoft.MixedReality.Toolkit.Experimental.CameraSystem.CameraSystemManager)
- [DiagnosticsSystemManager](xref:Microsoft.MixedReality.Toolkit.Experimental.Diagnostics.DiagnosticsSystemManager)
- [InputSystemManager](xref:Microsoft.MixedReality.Toolkit.Experimental.Input.InputSystemManager)
- [SpatialAwarenessSystemManager](xref:Microsoft.MixedReality.Toolkit.Experimental.SpatialAwareness.SpatialAwarenessSystemManager)
- [TeleportSystemManager](xref:Microsoft.MixedReality.Toolkit.Experimental.Teleport.TeleportSystemManager)

Ogni componente precedente, ad eccezione di InputSystemManager, è responsabile della gestione della registrazione e dello stato di un singolo tipo di servizio. InputSystem richiede servizi di supporto aggiuntivi (ad esempio, FocusProvider) che vengono gestiti anche da InputSystemManager.

In generale, i metodi definiti da IMixedRealityServiceRegistrar vengono chiamati internamente dai componenti di gestione dei servizi o chiamati da servizi che richiedono che i componenti del servizio aggiuntivi funzionino correttamente. Il codice dell'applicazione, in genere, non chiama questi metodi perché questa operazione potrebbe causare un comportamento imprevedibile dell'applicazione (ad esempio, un'istanza del servizio memorizzata nella cache potrebbe diventare non valida).

## <a name="see-also"></a>Vedi anche

- [Documentazione dell'API IMixedRealityServiceRegistrar](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar)
- [Documentazione dell'API MixedRealityServiceRegistry](xref:Microsoft.MixedReality.Toolkit.MixedRealityServiceRegistry)

---
title: Registro del servizio realtà mista
description: Documentazione su MixedRealityServiceRegistry e IMixedRealityServiceRegistrar
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: 16aea46890297dab209c13b6776a0a571b1e05bf5021a5795a33dc88366ee9b1
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115217433"
---
# <a name="mixed-reality-service-registry"></a>Registro del servizio realtà mista

L'Toolkit realtà mista include due componenti con nomi molto simili che eseguono attività correlate: MixedRealityServiceRegistry e IMixedRealityServiceRegistrar.

## <a name="mixedrealityserviceregistry"></a>MixedRealityServiceRegistry

[MixedRealityServiceRegistry è](xref:Microsoft.MixedReality.Toolkit.MixedRealityServiceRegistry) il componente che contiene le istanze di ogni servizio registrato (sistemi di base e servizi di estensione).

> [!NOTE]
> MixedRealityServiceRegistry contiene istanze di oggetti che implementano [l'interfaccia IMixedRealityService,](xref:Microsoft.MixedReality.Toolkit.IMixedRealityService) incluso [IMixedRealityExtensionService.](xref:Microsoft.MixedReality.Toolkit.IMixedRealityExtensionService)
>
>Gli oggetti che implementano [IMixedRealityDataProvider](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) (una sottoclasse di IMixedRealityService) non vengono registrati in modo esplicito in MixedRealityServiceRegistry. Questi oggetti sono gestiti dai singoli servizi (ad esempio: Consapevolezza spaziale).

MixedRealityServiceRegistry viene implementato come classe C# statica ed è il modello consigliato da usare per acquisire istanze del servizio nel codice dell'applicazione.

Il frammento di codice seguente illustra l'acquisizione di un'istanza di IMixedRealityInputSystem.

```c#
IMixedRealityInputSystem inputSystem = null;

if (!MixedRealityServiceRegistry.TryGetService<IMixedRealityInputSystem>(out inputSystem))
{
    // Failed to acquire the input system. It may not have been registered
}
```

## <a name="imixedrealityserviceregistrar"></a>IMixedRealityServiceRegistrar

[IMixedRealityServiceRegistrar](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar) è l'interfaccia che definisce la funzionalità implementata dai componenti che gestiscono la registrazione di uno o più servizi. I componenti che implementano IMixedRealityServiceRegistrar sono responsabili dell'aggiunta e della rimozione dei dati all'interno di MixedRealityServiceRegistry. [L'oggetto MixedRealityToolkit](xref:Microsoft.MixedReality.Toolkit.MixedRealityToolkit) è uno di questi componenti.

Altri registrar sono disponibili nella cartella MRTK/SDK/Experimental/Features. Questi componenti possono essere usati per aggiungere il supporto di un singolo servizio (ad esempio, la consapevolezza spaziale) a un'applicazione. Questi gestori di servizi singoli sono elencati di seguito.

- [BoundarySystemManager](xref:Microsoft.MixedReality.Toolkit.Experimental.Boundary.BoundarySystemManager)
- [CameraSystemManager](xref:Microsoft.MixedReality.Toolkit.Experimental.CameraSystem.CameraSystemManager)
- [DiagnosticsSystemManager](xref:Microsoft.MixedReality.Toolkit.Experimental.Diagnostics.DiagnosticsSystemManager)
- [InputSystemManager](xref:Microsoft.MixedReality.Toolkit.Experimental.Input.InputSystemManager)
- [SpatialAwarenessSystemManager](xref:Microsoft.MixedReality.Toolkit.Experimental.SpatialAwareness.SpatialAwarenessSystemManager)
- [TeleportSystemManager](xref:Microsoft.MixedReality.Toolkit.Experimental.Teleport.TeleportSystemManager)

Ognuno dei componenti precedenti, ad eccezione di InputSystemManager, è responsabile della gestione della registrazione e dello stato di un singolo tipo di servizio. InputSystem richiede alcuni servizi di supporto aggiuntivi ,ad esempio FocusProvider, che vengono gestiti anche da InputSystemManager.

In generale, i metodi definiti da IMixedRealityServiceRegistrar vengono chiamati internamente dai componenti di gestione dei servizi o dai servizi che richiedono componenti del servizio aggiuntivi per funzionare correttamente. Il codice dell'applicazione in genere non deve chiamare questi metodi, perché in questo modo l'applicazione potrebbe comportarsi in modo imprevedibile (ad esempio, un'istanza del servizio memorizzata nella cache potrebbe diventare non valida).

## <a name="see-also"></a>Vedi anche

- [Documentazione dell'API IMixedRealityServiceRegistrar](xref:Microsoft.MixedReality.Toolkit.IMixedRealityServiceRegistrar)
- [Documentazione dell'API MixedRealityServiceRegistry](xref:Microsoft.MixedReality.Toolkit.MixedRealityServiceRegistry)

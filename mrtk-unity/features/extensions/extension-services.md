---
title: Servizi di estensione
description: documentazione per le funzionalità estese in MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: 0f9f30bb7d2d44cef828b79bc916d933a6355dbb1068b09e73317d1c977ef45a
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115186997"
---
# <a name="extension-services"></a>Servizi di estensione

I servizi di estensione sono componenti che estendono le funzionalità di Realtà mista Toolkit. Questi servizi possono essere forniti da MRTK o da altre parti.

## <a name="creating-an-extension-service"></a>Creazione di un servizio di estensione

Il modo più efficiente per creare un servizio di estensione è usare la creazione [guidata del servizio di estensione](../tools/extension-service-creation-wizard.md).
Per avviare la creazione guidata del servizio di estensione, selezionare Mixed Reality Toolkit > Utilities > Create Extension Service (Crea **servizio di estensione).**

![Creazione guidata del servizio di estensione](../images/extension-wizard/ExtensionServiceCreationWizard.png)

La procedura guidata automatizza la creazione dei componenti del servizio e garantisce l'ereditarietà dell'interfaccia appropriata.

![Componenti creati dalla creazione guidata del servizio di estensione](../images/extension-wizard/ExtensionServiceComponents.png)

> [!Note]
> In MRTK versione 2.0.0 si verifica un problema nella procedura guidata del servizio di estensione a causa del quale è necessario generare il controllo del servizio e il profilo del servizio. Per altre informazioni, vedere il [problema 5654.](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/5654)

Al termine della procedura guidata, la funzionalità del servizio può essere implementata.

## <a name="registering-an-extension-service"></a>Registrazione di un servizio di estensione

Per essere accessibile da un'applicazione, il nuovo servizio di estensione deve essere registrato con mixed reality Toolkit.

La creazione guidata del servizio di estensione può essere usata per registrare il servizio.

![Registrazione guidata del servizio di estensione](../images/extension-wizard/ExtensionServiceWizardRegister.png)

Il servizio può anche essere registrato manualmente usando mixed reality Toolkit di configurazione.

![Registrazione manuale del servizio di estensione](../images/profiles/RegisterExtensionService.png)

Se il servizio di estensione usa un profilo, assicurarsi che sia specificato nel controllo.

![Servizio di estensione configurato](../images/profiles/ConfiguredExtensionService.png)

È anche possibile modificare il nome e la priorità del componente.

## <a name="accessing-an-extension-service"></a>Accesso a un servizio di estensione

È possibile accedere ai servizi di estensione nel codice usando [`MixedRealityServiceRegistry`](xref:Microsoft.MixedReality.Toolkit.MixedRealityServiceRegistry) , come illustrato nell'esempio seguente.

```c#
INewService service = null;
if (MixedRealityServiceRegistry.TryGetService<INewService>(out service))
{
    // Succeeded in getting the service,  perform any desired tasks.
}
```

## <a name="see-also"></a>Vedi anche

- [Sistemi, servizi di estensione e provider di dati](../../architecture/systems-extensions-providers.md)
- [Creazione guidata del servizio di estensione](../tools/extension-service-creation-wizard.md)
- [IMixedRealityExtensionService](xref:Microsoft.MixedReality.Toolkit.IMixedRealityExtensionService)
- [MixedRealityServiceRegistry](xref:Microsoft.MixedReality.Toolkit.MixedRealityServiceRegistry)

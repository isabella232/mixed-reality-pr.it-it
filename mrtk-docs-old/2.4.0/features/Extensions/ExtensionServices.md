---
title: ExtensionServices
description: documentazione per la funzionalità estesa in MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: 981c7cd164e99760ee93ff4db7af906dbe5ab9a9
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/03/2021
ms.locfileid: "101783657"
---
# <a name="extension-services"></a>Servizi di estensione

I servizi di estensione sono componenti che estendono le funzionalità del Toolkit di realtà mista. Questi servizi possono essere forniti da MRTK o da altre parti.

## <a name="creating-an-extension-service"></a>Creazione di un servizio di estensione

Il modo più efficiente per creare un servizio di estensione consiste nell'utilizzare la [procedura guidata di creazione del servizio di estensione](../Tools/ExtensionServiceCreationWizard.md).
Per avviare la creazione guidata del servizio di estensione, selezionare **mixed reality Toolkit > Utilities > creare un servizio di estensione**.

![Creazione guidata servizio di estensione](../Images/ExtensionWizard/ExtensionServiceCreationWizard.png)

La procedura guidata automatizza la creazione dei componenti del servizio e garantisce l'ereditarietà corretta dell'interfaccia.

![Componenti creati dalla creazione guidata servizio di estensione](../Images/ExtensionWizard/ExtensionServiceComponents.png)

> [!Note]
> In MRTK versione 2.0.0 si verifica un problema nella procedura guidata del servizio di estensione in cui è necessario generare il controllo del servizio e il profilo del servizio. Per ulteriori informazioni, vedere il problema [5654](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/5654) .

Al termine della procedura guidata, è possibile implementare la funzionalità del servizio.

## <a name="registering-an-extension-service"></a>Registrazione di un servizio di estensione

Per essere accessibile da parte di un'applicazione, il nuovo servizio di estensione deve essere registrato con il Toolkit di realtà mista.

Per registrare il servizio è possibile utilizzare la procedura guidata di creazione del servizio di estensione.

![Registrazione della creazione guidata servizio di estensione](../Images/ExtensionWizard/ExtensionServiceWizardRegister.png)

Il servizio può anche essere registrato manualmente usando il controllo di configurazione di Mixed Reality Toolkit.

![Registrazione del servizio di estensione manuale](../Images/Profiles/RegisterExtensionService.png)

Se il servizio di estensione usa un profilo, assicurarsi che sia specificato nel controllo.

![Servizio di estensione configurato](../Images/Profiles/ConfiguredExtensionService.png)

È inoltre possibile modificare il nome e la priorità di un componente.

## <a name="accessing-an-extension-service"></a>Accesso a un servizio di estensione

Per accedere ai servizi di estensione, usare il codice, [`MixedRealityServiceRegistry`](xref:Microsoft.MixedReality.Toolkit.MixedRealityServiceRegistry) come illustrato nell'esempio riportato di seguito.

```c#
INewService service = null;
if (MixedRealityServiceRegistry.TryGetService<INewService>(out service))
{
    // Succeeded in getting the service,  perform any desired tasks.
}
```

## <a name="see-also"></a>Vedi anche

- [Sistemi, servizi di estensione e provider di dati](../../architecture/SystemsExtensionsProviders.md)
- [Creazione guidata servizio di estensione](../Tools/ExtensionServiceCreationWizard.md)
- [IMixedRealityExtensionService](xref:Microsoft.MixedReality.Toolkit.IMixedRealityExtensionService)
- [MixedRealityServiceRegistry](xref:Microsoft.MixedReality.Toolkit.MixedRealityServiceRegistry)

---
title: Servizi di estensione
description: documentazione per le funzionalità estese in MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: f8f7b8dbac0355c226e4bbfae39246e5c1c58f69
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176273"
---
# <a name="extension-services"></a><span data-ttu-id="48d7a-104">Servizi di estensione</span><span class="sxs-lookup"><span data-stu-id="48d7a-104">Extension services</span></span>

<span data-ttu-id="48d7a-105">I servizi di estensione sono componenti che estendono le funzionalità dell'Toolkit.</span><span class="sxs-lookup"><span data-stu-id="48d7a-105">Extension services are components that extend the functionality of the Mixed Reality Toolkit.</span></span> <span data-ttu-id="48d7a-106">Questi servizi possono essere forniti da MRTK o da altre parti.</span><span class="sxs-lookup"><span data-stu-id="48d7a-106">These services may be provided by the MRTK or by other parties.</span></span>

## <a name="creating-an-extension-service"></a><span data-ttu-id="48d7a-107">Creazione di un servizio di estensione</span><span class="sxs-lookup"><span data-stu-id="48d7a-107">Creating an extension service</span></span>

<span data-ttu-id="48d7a-108">Il modo più efficiente per creare un servizio di estensione è usare la creazione [guidata del servizio di estensione](../tools/extension-service-creation-wizard.md).</span><span class="sxs-lookup"><span data-stu-id="48d7a-108">The most efficient way to create an extension service is to use the [extension service creation wizard](../tools/extension-service-creation-wizard.md).</span></span>
<span data-ttu-id="48d7a-109">Per avviare la creazione guidata del servizio di estensione, selezionare **Mixed Reality Toolkit > Utilities > Create Extension Service**.</span><span class="sxs-lookup"><span data-stu-id="48d7a-109">To start the extension service creation wizard, select **Mixed Reality Toolkit > Utilities > Create Extension Service**.</span></span>

![Creazione guidata servizio di estensione](../images/extension-wizard/ExtensionServiceCreationWizard.png)

<span data-ttu-id="48d7a-111">La procedura guidata automatizza la creazione dei componenti del servizio e garantisce l'ereditarietà dell'interfaccia appropriata.</span><span class="sxs-lookup"><span data-stu-id="48d7a-111">The wizard automates the creation of the service components and ensures the proper interface inheritance.</span></span>

![Componenti creati dalla creazione guidata del servizio di estensione](../images/extension-wizard/ExtensionServiceComponents.png)

> [!Note]
> <span data-ttu-id="48d7a-113">In MRTK versione 2.0.0 si verifica un problema nella procedura guidata del servizio di estensione in cui è necessario generare il controllo del servizio e il profilo del servizio.</span><span class="sxs-lookup"><span data-stu-id="48d7a-113">In MRTK version 2.0.0, there is an issue in the extension service wizard where the service inspector and service profile are required to be generated.</span></span> <span data-ttu-id="48d7a-114">Per altre informazioni, vedere il [problema 5654.](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/5654)</span><span class="sxs-lookup"><span data-stu-id="48d7a-114">Please see issue [5654](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/5654) for more information.</span></span>

<span data-ttu-id="48d7a-115">Al termine della procedura guidata, la funzionalità del servizio può essere implementata.</span><span class="sxs-lookup"><span data-stu-id="48d7a-115">When the wizard completes, the service functionality can be implemented.</span></span>

## <a name="registering-an-extension-service"></a><span data-ttu-id="48d7a-116">Registrazione di un servizio di estensione</span><span class="sxs-lookup"><span data-stu-id="48d7a-116">Registering an extension service</span></span>

<span data-ttu-id="48d7a-117">Per essere accessibile da un'applicazione, il nuovo servizio di estensione deve essere registrato con l'Toolkit.</span><span class="sxs-lookup"><span data-stu-id="48d7a-117">To be accessible by an application, the new extension service needs to be registered with the Mixed Reality Toolkit.</span></span>

<span data-ttu-id="48d7a-118">La creazione guidata del servizio di estensione può essere usata per registrare il servizio.</span><span class="sxs-lookup"><span data-stu-id="48d7a-118">The extension service creation wizard can be used to register the service.</span></span>

![Registrazione guidata del servizio di estensione](../images/extension-wizard/ExtensionServiceWizardRegister.png)

<span data-ttu-id="48d7a-120">Il servizio può anche essere registrato manualmente usando il controllo configurazione Toolkit realtà mista.</span><span class="sxs-lookup"><span data-stu-id="48d7a-120">The service can also be manually registered using the Mixed Reality Toolkit configuration inspector.</span></span>

![Registrazione manuale del servizio di estensione](../images/profiles/RegisterExtensionService.png)

<span data-ttu-id="48d7a-122">Se il servizio di estensione usa un profilo, assicurarsi che sia specificato nel controllo .</span><span class="sxs-lookup"><span data-stu-id="48d7a-122">If the extension service uses a profile, please ensure that it is specified in the inspector.</span></span>

![Servizio di estensione configurato](../images/profiles/ConfiguredExtensionService.png)

<span data-ttu-id="48d7a-124">È anche possibile modificare il nome e la priorità del componente.</span><span class="sxs-lookup"><span data-stu-id="48d7a-124">The component name and priority can also be adjusted.</span></span>

## <a name="accessing-an-extension-service"></a><span data-ttu-id="48d7a-125">Accesso a un servizio di estensione</span><span class="sxs-lookup"><span data-stu-id="48d7a-125">Accessing an extension service</span></span>

<span data-ttu-id="48d7a-126">È possibile accedere ai servizi di estensione nel codice usando [`MixedRealityServiceRegistry`](xref:Microsoft.MixedReality.Toolkit.MixedRealityServiceRegistry) come illustrato nell'esempio seguente.</span><span class="sxs-lookup"><span data-stu-id="48d7a-126">Extension services are accessed, in code, using the [`MixedRealityServiceRegistry`](xref:Microsoft.MixedReality.Toolkit.MixedRealityServiceRegistry) as shown in the example below.</span></span>

```c#
INewService service = null;
if (MixedRealityServiceRegistry.TryGetService<INewService>(out service))
{
    // Succeeded in getting the service,  perform any desired tasks.
}
```

## <a name="see-also"></a><span data-ttu-id="48d7a-127">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="48d7a-127">See also</span></span>

- [<span data-ttu-id="48d7a-128">Sistemi, servizi di estensione e provider di dati</span><span class="sxs-lookup"><span data-stu-id="48d7a-128">Systems, extension services and data providers</span></span>](../../architecture/systems-extensions-providers.md)
- [<span data-ttu-id="48d7a-129">Creazione guidata servizio di estensione</span><span class="sxs-lookup"><span data-stu-id="48d7a-129">Extension service creation wizard</span></span>](../tools/extension-service-creation-wizard.md)
- [<span data-ttu-id="48d7a-130">IMixedRealityExtensionService</span><span class="sxs-lookup"><span data-stu-id="48d7a-130">IMixedRealityExtensionService</span></span>](xref:Microsoft.MixedReality.Toolkit.IMixedRealityExtensionService)
- [<span data-ttu-id="48d7a-131">MixedRealityServiceRegistry</span><span class="sxs-lookup"><span data-stu-id="48d7a-131">MixedRealityServiceRegistry</span></span>](xref:Microsoft.MixedReality.Toolkit.MixedRealityServiceRegistry)

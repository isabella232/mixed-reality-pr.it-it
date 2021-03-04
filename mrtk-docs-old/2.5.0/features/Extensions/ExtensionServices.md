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
ms.locfileid: "101782676"
---
# <a name="extension-services"></a><span data-ttu-id="a555b-104">Servizi di estensione</span><span class="sxs-lookup"><span data-stu-id="a555b-104">Extension services</span></span>

<span data-ttu-id="a555b-105">I servizi di estensione sono componenti che estendono le funzionalità del Toolkit di realtà mista.</span><span class="sxs-lookup"><span data-stu-id="a555b-105">Extension services are components that extend the functionality of the Mixed Reality Toolkit.</span></span> <span data-ttu-id="a555b-106">Questi servizi possono essere forniti da MRTK o da altre parti.</span><span class="sxs-lookup"><span data-stu-id="a555b-106">These services may be provided by the MRTK or by other parties.</span></span>

## <a name="creating-an-extension-service"></a><span data-ttu-id="a555b-107">Creazione di un servizio di estensione</span><span class="sxs-lookup"><span data-stu-id="a555b-107">Creating an extension service</span></span>

<span data-ttu-id="a555b-108">Il modo più efficiente per creare un servizio di estensione consiste nell'utilizzare la [procedura guidata di creazione del servizio di estensione](../Tools/ExtensionServiceCreationWizard.md).</span><span class="sxs-lookup"><span data-stu-id="a555b-108">The most efficient way to create an extension service is to use the [extension service creation wizard](../Tools/ExtensionServiceCreationWizard.md).</span></span>
<span data-ttu-id="a555b-109">Per avviare la creazione guidata del servizio di estensione, selezionare **mixed reality Toolkit > Utilities > creare un servizio di estensione**.</span><span class="sxs-lookup"><span data-stu-id="a555b-109">To start the extension service creation wizard, select **Mixed Reality Toolkit > Utilities > Create Extension Service**.</span></span>

![Creazione guidata servizio di estensione](../Images/ExtensionWizard/ExtensionServiceCreationWizard.png)

<span data-ttu-id="a555b-111">La procedura guidata automatizza la creazione dei componenti del servizio e garantisce l'ereditarietà corretta dell'interfaccia.</span><span class="sxs-lookup"><span data-stu-id="a555b-111">The wizard automates the creation of the service components and ensures the proper interface inheritance.</span></span>

![Componenti creati dalla creazione guidata servizio di estensione](../Images/ExtensionWizard/ExtensionServiceComponents.png)

> [!Note]
> <span data-ttu-id="a555b-113">In MRTK versione 2.0.0 si verifica un problema nella procedura guidata del servizio di estensione in cui è necessario generare il controllo del servizio e il profilo del servizio.</span><span class="sxs-lookup"><span data-stu-id="a555b-113">In MRTK version 2.0.0, there is an issue in the extension service wizard where the service inspector and service profile are required to be generated.</span></span> <span data-ttu-id="a555b-114">Per ulteriori informazioni, vedere il problema [5654](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/5654) .</span><span class="sxs-lookup"><span data-stu-id="a555b-114">Please see issue [5654](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/5654) for more information.</span></span>

<span data-ttu-id="a555b-115">Al termine della procedura guidata, è possibile implementare la funzionalità del servizio.</span><span class="sxs-lookup"><span data-stu-id="a555b-115">When the wizard completes, the service functionality can be implemented.</span></span>

## <a name="registering-an-extension-service"></a><span data-ttu-id="a555b-116">Registrazione di un servizio di estensione</span><span class="sxs-lookup"><span data-stu-id="a555b-116">Registering an extension service</span></span>

<span data-ttu-id="a555b-117">Per essere accessibile da parte di un'applicazione, il nuovo servizio di estensione deve essere registrato con il Toolkit di realtà mista.</span><span class="sxs-lookup"><span data-stu-id="a555b-117">To be accessible by an application, the new extension service needs to be registered with the Mixed Reality Toolkit.</span></span>

<span data-ttu-id="a555b-118">Per registrare il servizio è possibile utilizzare la procedura guidata di creazione del servizio di estensione.</span><span class="sxs-lookup"><span data-stu-id="a555b-118">The extension service creation wizard can be used to register the service.</span></span>

![Registrazione della creazione guidata servizio di estensione](../Images/ExtensionWizard/ExtensionServiceWizardRegister.png)

<span data-ttu-id="a555b-120">Il servizio può anche essere registrato manualmente usando il controllo di configurazione di Mixed Reality Toolkit.</span><span class="sxs-lookup"><span data-stu-id="a555b-120">The service can also be manually registered using the Mixed Reality Toolkit configuration inspector.</span></span>

![Registrazione del servizio di estensione manuale](../Images/Profiles/RegisterExtensionService.png)

<span data-ttu-id="a555b-122">Se il servizio di estensione usa un profilo, assicurarsi che sia specificato nel controllo.</span><span class="sxs-lookup"><span data-stu-id="a555b-122">If the extension service uses a profile, please ensure that it is specified in the inspector.</span></span>

![Servizio di estensione configurato](../Images/Profiles/ConfiguredExtensionService.png)

<span data-ttu-id="a555b-124">È inoltre possibile modificare il nome e la priorità di un componente.</span><span class="sxs-lookup"><span data-stu-id="a555b-124">The component name and priority can also be adjusted.</span></span>

## <a name="accessing-an-extension-service"></a><span data-ttu-id="a555b-125">Accesso a un servizio di estensione</span><span class="sxs-lookup"><span data-stu-id="a555b-125">Accessing an extension service</span></span>

<span data-ttu-id="a555b-126">Per accedere ai servizi di estensione, usare il codice, [`MixedRealityServiceRegistry`](xref:Microsoft.MixedReality.Toolkit.MixedRealityServiceRegistry) come illustrato nell'esempio riportato di seguito.</span><span class="sxs-lookup"><span data-stu-id="a555b-126">Extension services are accessed, in code, using the [`MixedRealityServiceRegistry`](xref:Microsoft.MixedReality.Toolkit.MixedRealityServiceRegistry) as shown in the example below.</span></span>

```c#
INewService service = null;
if (MixedRealityServiceRegistry.TryGetService<INewService>(out service))
{
    // Succeeded in getting the service,  perform any desired tasks.
}
```

## <a name="see-also"></a><span data-ttu-id="a555b-127">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="a555b-127">See also</span></span>

- [<span data-ttu-id="a555b-128">Sistemi, servizi di estensione e provider di dati</span><span class="sxs-lookup"><span data-stu-id="a555b-128">Systems, extension services and data providers</span></span>](../../architecture/SystemsExtensionsProviders.md)
- [<span data-ttu-id="a555b-129">Creazione guidata servizio di estensione</span><span class="sxs-lookup"><span data-stu-id="a555b-129">Extension service creation wizard</span></span>](../Tools/ExtensionServiceCreationWizard.md)
- [<span data-ttu-id="a555b-130">IMixedRealityExtensionService</span><span class="sxs-lookup"><span data-stu-id="a555b-130">IMixedRealityExtensionService</span></span>](xref:Microsoft.MixedReality.Toolkit.IMixedRealityExtensionService)
- [<span data-ttu-id="a555b-131">MixedRealityServiceRegistry</span><span class="sxs-lookup"><span data-stu-id="a555b-131">MixedRealityServiceRegistry</span></span>](xref:Microsoft.MixedReality.Toolkit.MixedRealityServiceRegistry)

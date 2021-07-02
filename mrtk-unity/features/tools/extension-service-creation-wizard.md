---
title: Creazione guidata servizio di estensione
description: Documentazione sulla procedura guidata per eseguire la transizione dai singleton ai servizi MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: 4be9a58c7d63ab3bc93bcc326a90260cf6a3366b
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176617"
---
# <a name="extension-service-creation-wizard"></a><span data-ttu-id="6aa30-104">Creazione guidata servizio di estensione</span><span class="sxs-lookup"><span data-stu-id="6aa30-104">Extension service creation wizard</span></span>

<span data-ttu-id="6aa30-105">La transizione dai singleton ai servizi può essere difficile.</span><span class="sxs-lookup"><span data-stu-id="6aa30-105">Making the transition from singletons to services can be difficult.</span></span> <span data-ttu-id="6aa30-106">Questa procedura guidata può integrare la documentazione e il codice di esempio consentendo agli sviluppatori di creare nuovi servizi con (approssimativamente) la stessa facilità con cui si crea un nuovo script MonoBehaviour.</span><span class="sxs-lookup"><span data-stu-id="6aa30-106">This wizard can supplement our other documentation and sample code by enabling devs to create new services with (roughly) the same ease as creating a new MonoBehaviour script.</span></span> <span data-ttu-id="6aa30-107">Per informazioni sulla creazione di servizi da zero, vedere la Guida [alla creazione di](../../configuration/mixed-reality-configuration-guide.md) servizi registrati (Presto disponibili).</span><span class="sxs-lookup"><span data-stu-id="6aa30-107">To learn about creating services from scratch, see our [Guide to building Registered Services](../../configuration/mixed-reality-configuration-guide.md) (Coming soon).</span></span>

## <a name="launching-the-wizard"></a><span data-ttu-id="6aa30-108">Avvio della procedura guidata</span><span class="sxs-lookup"><span data-stu-id="6aa30-108">Launching the wizard</span></span>

<span data-ttu-id="6aa30-109">Avviare la procedura guidata dal menu principale: **MixedRealityToolkit/Utilities/Create Extension Service.** La procedura guidata consente quindi di generare lo script del servizio, l'interfaccia e la classe del profilo.</span><span class="sxs-lookup"><span data-stu-id="6aa30-109">Launch the wizard from the main menu: **MixedRealityToolkit/Utilities/Create Extension Service** - the wizard will then take you through the process of generating your service script, interface and profile class.</span></span>

## <a name="editing-your-service-script"></a><span data-ttu-id="6aa30-110">Modifica dello script del servizio</span><span class="sxs-lookup"><span data-stu-id="6aa30-110">Editing your service script</span></span>

<span data-ttu-id="6aa30-111">Per impostazione predefinita, i nuovi asset di script verranno generati nella `MixedRealityToolkit.Generated/Extensions` cartella .</span><span class="sxs-lookup"><span data-stu-id="6aa30-111">By default, your new script assets will be generated in the `MixedRealityToolkit.Generated/Extensions` folder.</span></span> <span data-ttu-id="6aa30-112">Dopo aver completato la procedura guidata, passare qui e aprire il nuovo script del servizio.</span><span class="sxs-lookup"><span data-stu-id="6aa30-112">Once you've completed the wizard, navigate here and open your new service script.</span></span>

<span data-ttu-id="6aa30-113">Gli script del servizio generati includono alcune richieste simili ai nuovi script MonoBehaviour.</span><span class="sxs-lookup"><span data-stu-id="6aa30-113">Generated service scripts include some prompts similar to new MonoBehaviour scripts.</span></span> <span data-ttu-id="6aa30-114">In questo modo sarà possibile sapere dove inizializzare e aggiornare il servizio.</span><span class="sxs-lookup"><span data-stu-id="6aa30-114">They will let you know where to initialize and update your service.</span></span>

```csharp
namespace Microsoft.MixedReality.Toolkit.Extensions
{
    [MixedRealityExtensionService(SupportedPlatforms.WindowsStandalone|SupportedPlatforms.MacStandalone|SupportedPlatforms.LinuxStandalone|SupportedPlatforms.WindowsUniversal)]
    public class NewService : BaseExtensionService, INewService, IMixedRealityExtensionService
    {
        private NewServiceProfile newServiceProfile;

        public NewService(IMixedRealityServiceRegistrar registrar,  string name,  uint priority,  BaseMixedRealityProfile profile) : base(registrar, name, priority, profile) 
        {
            newServiceProfile = (NewServiceProfile)profile;
        }

        public override void Initialize()
        {
            // Do service initialization here.
        }

        public override void Update()
        {
            // Do service updates here.
        }
    }
}
```

<span data-ttu-id="6aa30-115">Se si sceglie di registrare il servizio nella procedura guidata, è necessario solo modificare questo script e il servizio verrà aggiornato automaticamente.</span><span class="sxs-lookup"><span data-stu-id="6aa30-115">If you chose to register your service in the wizard, all you have to do is edit this script and your service will automatically be updated.</span></span> <span data-ttu-id="6aa30-116">In caso contrario, è possibile [leggere la registrazione del nuovo servizio qui.](../../configuration/mixed-reality-configuration-guide.md)</span><span class="sxs-lookup"><span data-stu-id="6aa30-116">Otherwise you can read about [registering your new service here](../../configuration/mixed-reality-configuration-guide.md).</span></span>

---
title: ExtensionServiceCreationWizard
description: Documentazione sulla procedura guidata per eseguire la transizione da Singleton ai servizi MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: 3d2bb7f5c2c3947cb2256062db2c2e5a16b50caf
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/03/2021
ms.locfileid: "101783352"
---
# <a name="extension-service-creation-wizard"></a><span data-ttu-id="8d049-104">Creazione guidata servizio di estensione</span><span class="sxs-lookup"><span data-stu-id="8d049-104">Extension service creation wizard</span></span>

<span data-ttu-id="8d049-105">L'esecuzione della transizione da Singleton ai servizi può essere difficile.</span><span class="sxs-lookup"><span data-stu-id="8d049-105">Making the transition from singletons to services can be difficult.</span></span> <span data-ttu-id="8d049-106">Questa procedura guidata può integrare l'altra documentazione e il codice di esempio consentendo agli sviluppatori di creare nuovi servizi con la stessa facilità della creazione di un nuovo script monobehavior.</span><span class="sxs-lookup"><span data-stu-id="8d049-106">This wizard can supplement our other documentation and sample code by enabling devs to create new services with (roughly) the same ease as creating a new MonoBehaviour script.</span></span> <span data-ttu-id="8d049-107">Per informazioni sulla creazione di servizi da zero, vedere la [Guida alla creazione di servizi registrati](../../out-of-scope/MixedRealityConfigurationGuide.md) (presto disponibile).</span><span class="sxs-lookup"><span data-stu-id="8d049-107">To learn about creating services from scratch, see our [Guide to building Registered Services](../../out-of-scope/MixedRealityConfigurationGuide.md) (Coming soon).</span></span>

## <a name="launching-the-wizard"></a><span data-ttu-id="8d049-108">Avvio della procedura guidata</span><span class="sxs-lookup"><span data-stu-id="8d049-108">Launching the wizard</span></span>

<span data-ttu-id="8d049-109">Avviare la procedura guidata dal menu principale: **MixedRealityToolkit/Utilities/Crea servizio di estensione** . la procedura guidata consente di eseguire il processo di generazione dello script del servizio, dell'interfaccia e della classe del profilo.</span><span class="sxs-lookup"><span data-stu-id="8d049-109">Launch the wizard from the main menu: **MixedRealityToolkit/Utilities/Create Extension Service** - the wizard will then take you through the process of generating your service script, interface and profile class.</span></span>

## <a name="editing-your-service-script"></a><span data-ttu-id="8d049-110">Modifica dello script del servizio</span><span class="sxs-lookup"><span data-stu-id="8d049-110">Editing your service script</span></span>

<span data-ttu-id="8d049-111">Per impostazione predefinita, i nuovi asset di script verranno generati nella `MixedRealityToolkit.Generated/Extensions` cartella.</span><span class="sxs-lookup"><span data-stu-id="8d049-111">By default, your new script assets will be generated in the `MixedRealityToolkit.Generated/Extensions` folder.</span></span> <span data-ttu-id="8d049-112">Dopo aver completato la procedura guidata, passare a questa pagina e aprire il nuovo script del servizio.</span><span class="sxs-lookup"><span data-stu-id="8d049-112">Once you've completed the wizard, navigate here and open your new service script.</span></span>

<span data-ttu-id="8d049-113">Gli script di servizio generati includono alcuni prompt simili a quelli dei nuovi script monobehavior.</span><span class="sxs-lookup"><span data-stu-id="8d049-113">Generated service scripts include some prompts similar to new MonoBehaviour scripts.</span></span> <span data-ttu-id="8d049-114">Che forniranno informazioni su dove inizializzare e aggiornare il servizio.</span><span class="sxs-lookup"><span data-stu-id="8d049-114">They will let you know where to initialize and update your service.</span></span>

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

<span data-ttu-id="8d049-115">Se si sceglie di registrare il servizio nella procedura guidata, è sufficiente modificare questo script e il servizio verrà aggiornato automaticamente.</span><span class="sxs-lookup"><span data-stu-id="8d049-115">If you chose to register your service in the wizard, all you have to do is edit this script and your service will automatically be updated.</span></span> <span data-ttu-id="8d049-116">In caso contrario, è possibile leggere la pagina relativa [alla registrazione del nuovo servizio qui](../../out-of-scope/MixedRealityConfigurationGuide.md).</span><span class="sxs-lookup"><span data-stu-id="8d049-116">Otherwise you can read about [registering your new service here](../../out-of-scope/MixedRealityConfigurationGuide.md).</span></span>

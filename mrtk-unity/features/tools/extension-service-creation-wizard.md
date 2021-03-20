---
title: ExtensionServiceCreationWizard
description: Documentazione sulla procedura guidata per eseguire la transizione da Singleton ai servizi MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: 5ba857096605508df1173daa29736a5d2279acf8
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2021
ms.locfileid: "104695958"
---
# <a name="extension-service-creation-wizard"></a>Creazione guidata servizio di estensione

L'esecuzione della transizione da Singleton ai servizi può essere difficile. Questa procedura guidata può integrare l'altra documentazione e il codice di esempio consentendo agli sviluppatori di creare nuovi servizi con la stessa facilità della creazione di un nuovo script monobehavior. Per informazioni sulla creazione di servizi da zero, vedere la [Guida alla creazione di servizi registrati](../../configuration/mixed-reality-configuration-guide.md) (presto disponibile).

## <a name="launching-the-wizard"></a>Avvio della procedura guidata

Avviare la procedura guidata dal menu principale: **MixedRealityToolkit/Utilities/Crea servizio di estensione** . la procedura guidata consente di eseguire il processo di generazione dello script del servizio, dell'interfaccia e della classe del profilo.

## <a name="editing-your-service-script"></a>Modifica dello script del servizio

Per impostazione predefinita, i nuovi asset di script verranno generati nella `MixedRealityToolkit.Generated/Extensions` cartella. Dopo aver completato la procedura guidata, passare a questa pagina e aprire il nuovo script del servizio.

Gli script di servizio generati includono alcuni prompt simili a quelli dei nuovi script monobehavior. Che forniranno informazioni su dove inizializzare e aggiornare il servizio.

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

Se si sceglie di registrare il servizio nella procedura guidata, è sufficiente modificare questo script e il servizio verrà aggiornato automaticamente. In caso contrario, è possibile leggere la pagina relativa [alla registrazione del nuovo servizio qui](../../configuration/mixed-reality-configuration-guide.md).

---
title: Creazione guidata servizio di estensione
description: Documentazione sulla procedura guidata per eseguire la transizione dai singleton ai servizi MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realtà mista, sviluppo, MRTK,
ms.openlocfilehash: 83797a9d6d465a150406b27162a5e84c157567f1
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143542"
---
# <a name="extension-service-creation-wizard"></a>Creazione guidata servizio di estensione

La transizione dai singleton ai servizi può essere difficile. Questa procedura guidata può integrare la documentazione e il codice di esempio consentendo agli sviluppatori di creare nuovi servizi con (approssimativamente) la stessa facilità con cui si crea un nuovo script MonoBehaviour. Per informazioni sulla creazione di servizi da zero, vedere la Guida [alla creazione di](../../configuration/mixed-reality-configuration-guide.md) servizi registrati (Presto disponibili).

## <a name="launching-the-wizard"></a>Avvio della procedura guidata

Avviare la procedura guidata dal menu principale: **MixedRealityToolkit/Utilities/Create Extension Service.** La procedura guidata consente quindi di generare lo script del servizio, l'interfaccia e la classe del profilo.

## <a name="editing-your-service-script"></a>Modifica dello script del servizio

Per impostazione predefinita, i nuovi asset di script verranno generati nella `MixedRealityToolkit.Generated/Extensions` cartella . Dopo aver completato la procedura guidata, passare qui e aprire il nuovo script del servizio.

Gli script del servizio generati includono alcune richieste simili ai nuovi script MonoBehaviour. In questo modo sarà possibile sapere dove inizializzare e aggiornare il servizio.

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

Se si è scelto di registrare il servizio nella procedura guidata, è necessario solo modificare questo script e il servizio verrà aggiornato automaticamente. In caso contrario, è possibile [leggere la registrazione del nuovo servizio qui.](../../configuration/mixed-reality-configuration-guide.md)

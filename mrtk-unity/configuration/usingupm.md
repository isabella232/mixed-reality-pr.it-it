---
title: Uso dell'Gestione pacchetti Unity
description: Uso di MRTK in Unity Gestione pacchetti
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, pacchetti MRTK,
ms.openlocfilehash: 524783c48b82722aec26648ea54477a6c7bcd4ae
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177323"
---
# <a name="using-the-unity-package-manager"></a>Uso dell'Gestione pacchetti Unity

A partire dalla versione 2.5.0, con lo strumento di funzionalità di realtà mista [,](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool)Microsoft Mixed Reality Toolkit si integra con Unity Gestione pacchetti (UPM) quando si usa Unity 2019.4 e versioni più nuove.

## <a name="using-the-mixed-reality-feature-tool"></a>Uso dello strumento di funzionalità di realtà mista

Come descritto in Welcome to the Mixed Reality Feature Tool (Introduzione [a Mixed Reality Feature Tool),](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool) è possibile scaricare lo strumento usando questo [collegamento.](https://aka.ms/MRFeatureTool)

> [!IMPORTANT]
> Se il manifesto del progetto include una voce nella sezione , è `Microsoft Mixed Reality` `scopedRegistries` consigliabile che venga rimosso.
>
> Per rimuovere un registro con ambito configurato, accedere a `Edit`  >  `Project Settings`  >  `Package Manager` .
>
> ![Rimozione del Registro di sistema con ambito](../features/images/packaging/RemoveScopedRegistry.png)

I pacchetti MRTK vengono visualizzati sotto `Mixed Reality Toolkit` l'intestazione quando si individuano le funzionalità.

![Individuare le funzionalità](../features/images/packaging/DiscoverFeatures.png)

Quando si selezionano le funzionalità, non è necessario preoccuparsi delle dipendenze necessarie. Lo strumento le scarica e le integra automaticamente nel progetto.

![Dipendenze necessarie](../features/images/packaging/RequiredDependencies.png)

## <a name="managing-mixed-reality-features-with-the-unity-package-manager"></a>Gestione delle funzionalità di realtà mista con Unity Gestione pacchetti

Dopo che un pacchetto Toolkit realtà mista è stato aggiunto al manifesto del pacchetto, può essere gestito usando l'interfaccia utente Gestione pacchetti unity.

![Pacchetto UPM di MRTK Foundation](../features/images/packaging/MRTK_FoundationUPM.png)

> [!NOTE]
> Se un pacchetto Toolkit realtà mista viene rimosso usando unity Gestione pacchetti, sarà necessario aggiungere di nuovo il pacchetto usando i [passaggi descritti in precedenza.](#using-the-mixed-reality-feature-tool)

### <a name="using-mixed-reality-toolkit-examples"></a>Uso di esempi Toolkit realtà mista

A differenza di quando si usano file di pacchetto asset (con estensione unitypackage) e non importare automaticamente le scene `com.microsoft.mixedreality.toolkit.examples` e gli asset di `com.microsoft.mixedreality.toolkit.handphysicsservice` esempio.

Per usare uno o più esempi, seguire questa procedura:

1. Nell'editor di Unity passare a `Window` > `Package Manager`
1. Nell'elenco dei pacchetti selezionare `Mixed Reality Toolkit Examples`
1. Individuare gli esempi desiderati `Samples` nell'elenco
1. Fare clic su`Import into Project`.

![Importazione di esempi](../features/images/packaging/MRTK_ExamplesUpm.png)

Quando viene aggiornato un pacchetto di esempio, Unity offre la possibilità di aggiornare gli esempi importati.

> [!NOTE]
> L'aggiornamento di un esempio importato sovrascriverà tutte le modifiche apportate all'esempio e agli asset associati.

## <a name="see-also"></a>Vedere anche

- [Pacchetti Toolkit realtà mista](../packages/mrtk-packages.md)

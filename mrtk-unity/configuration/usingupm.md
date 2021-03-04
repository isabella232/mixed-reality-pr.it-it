---
title: Uso di gestione pacchetti Unity
description: Uso di MRTK in Unity pakage Manager
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK pakages,
ms.openlocfilehash: 75b5a01baea2255a49713c6a8c75044a90d21132
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/03/2021
ms.locfileid: "101783659"
---
# <a name="mixed-reality-toolkit-and-unity-package-manager"></a>Toolkit per realtà mista e gestione pacchetti Unity

A partire dalla versione 2.5.0, usando lo strumento per la [funzionalità di realtà mista](https://aka.ms/MRFeatureToolDocs), Microsoft Mixed Reality Toolkit si integra con gestione pacchetti Unity (UPM) quando si usa unity 2019,4 e versioni successive.

## <a name="using-the-mixed-reality-feature-tool"></a>Uso dello strumento funzionalità per la realtà mista

Come descritto in [Introduzione allo strumento per la funzionalità di realtà mista](https://aka.ms/MRFeatureToolDocs) , è possibile scaricare lo strumento usando [questo collegamento](https://aka.ms/MRFeatureTool).

> [!IMPORTANT]
> Se nel manifesto del progetto è `Microsoft Mixed Reality` presente una voce nella `scopedRegistries` sezione, è consigliabile rimuoverla.
>
> Per rimuovere un registro con ambito configurato, rivolgersi a a `Edit`  >  `Project Settings`  >  `Package Manager` .
>
> ![Rimozione del registro di sistema con ambito](../features/images/packaging/RemoveScopedRegistry.png)

I pacchetti MRTK vengono visualizzati sotto l' `Mixed Reality Toolkit` intestazione durante l'individuazione delle funzionalità.

![Individua funzionalità](../features/images/packaging/DiscoverFeatures.png)

Quando si selezionano le funzionalità, non è necessario preoccuparsi delle dipendenze richieste, che verranno scaricate e integrate automaticamente nel progetto.

![Dipendenze obbligatorie](../features/images/packaging/RequiredDependencies.png)

## <a name="managing-mixed-reality-features-with-the-unity-package-manager"></a>Gestione delle funzionalità della realtà mista con gestione pacchetti Unity

Una volta aggiunto al manifesto del pacchetto, un pacchetto del Toolkit di realtà mista può essere gestito tramite l'interfaccia utente di gestione pacchetti Unity.

![Pacchetto UPM MRTK Foundation](../features/images/packaging/MRTK_FoundationUPM.png)

> [!NOTE]
> Se un pacchetto del Toolkit di realtà mista viene rimosso tramite Gestione pacchetti Unity, sarà necessario aggiungerlo di nuovo usando i [passaggi descritti in precedenza](#using-the-mixed-reality-feature-tool).

### <a name="using-mixed-reality-toolkit-examples"></a>Esempi di utilizzo del Toolkit di realtà mista

Diversamente da quando si usano i file di pacchetto asset (con estensione file unitypackage Tools), `com.microsoft.mixedreality.toolkit.examples` `com.microsoft.mixedreality.toolkit.handphysicsservice` non vengono importati automaticamente gli asset e le scene di esempio.

Per usare uno o più degli esempi, attenersi alla procedura seguente:

1. Nell'editor di Unity passare a `Window` > `Package Manager`
1. Nell'elenco dei pacchetti selezionare `Mixed Reality Toolkit Examples`
1. Individuare gli esempi desiderati nell' `Samples` elenco
1. Fare clic su`Import into Project`.

![Importazione di esempi](../features/images/packaging/MRTK_ExamplesUpm.png)

Quando viene aggiornato un pacchetto di esempio, Unity offre la possibilità di aggiornare gli esempi importati.

> [!NOTE]
> L'aggiornamento di un esempio importato sovrascriverà tutte le modifiche apportate all'esempio e alle risorse associate.

## <a name="see-also"></a>Vedere anche

- [Pacchetti Toolkit per realtà mista](../packages-releases/mrtk-packages.md)

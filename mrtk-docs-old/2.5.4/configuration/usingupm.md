---
title: usingupm
description: Uso di MRTK in Unity Pakage Manager
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK Pakages,
ms.openlocfilehash: 47966fd419e4dc5c546fb5325b1924e48c85022267f112f42d9669753e7ca174
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115209775"
---
# <a name="mixed-reality-toolkit-and-unity-package-manager"></a>Realtà mista Toolkit e Unity Gestione pacchetti

A partire dalla versione 2.5.0, usando mixed [reality feature tool,](https://aka.ms/MRFeatureToolDocs)Microsoft Mixed Reality Toolkit si integra con Unity Gestione pacchetti (UPM) quando si usa Unity 2019.4 e versioni più recente.

## <a name="using-the-mixed-reality-feature-tool"></a>Uso dello strumento di funzionalità di realtà mista

Come descritto in Welcome to the Mixed Reality Feature Tool (Introduzione [a Mixed Reality Feature Tool),](https://aka.ms/MRFeatureToolDocs) è possibile scaricare lo strumento usando questo [collegamento.](https://aka.ms/MRFeatureTool)

> [!IMPORTANT]
> Se il manifesto del progetto include una voce nella sezione , è `Microsoft Mixed Reality` `scopedRegistries` consigliabile rimuovere il manifesto.
>
> Per rimuovere un registro con ambito configurato, accedere a `Edit`  >  `Project Settings`  >  `Package Manager` .
>
> ![Rimozione del Registro di sistema con ambito](../features/images/packaging/RemoveScopedRegistry.png)

I pacchetti MRTK vengono visualizzati sotto `Mixed Reality Toolkit` l'intestazione durante l'individuazione delle funzionalità.

![Individuare le funzionalità](../features/images/packaging/DiscoverFeatures.png)

Quando si selezionano le funzionalità, non è necessario preoccuparsi delle dipendenze necessarie. Lo strumento le scarica e le integra automaticamente nel progetto.

![Dipendenze necessarie](../features/images/packaging/RequiredDependencies.png)

## <a name="managing-mixed-reality-features-with-the-unity-package-manager"></a>Gestione delle funzionalità di realtà mista con Unity Gestione pacchetti

Dopo che un pacchetto Toolkit realtà mista è stato aggiunto al manifesto del pacchetto, può essere gestito usando l'interfaccia utente Gestione pacchetti Unity.

![Pacchetto UPM MRTK Foundation](../features/images/packaging/MRTK_FoundationUPM.png)

> [!NOTE]
> Se un pacchetto Toolkit realtà mista viene rimosso usando il Gestione pacchetti Unity, sarà necessario aggiungere di nuovo il pacchetto usando i passaggi descritti [in precedenza.](#using-the-mixed-reality-feature-tool)

### <a name="using-mixed-reality-toolkit-examples"></a>Uso di esempi di Toolkit realtà mista

A differenza di quando si usano file di pacchetto di asset (con estensione unitypackage), e non importano automaticamente le scene `com.microsoft.mixedreality.toolkit.examples` e gli asset di `com.microsoft.mixedreality.toolkit.handphysicsservice` esempio.

Per usare uno o più esempi, seguire questa procedura:

1. Nell'editor di Unity passare a `Window` > `Package Manager`
1. Nell'elenco dei pacchetti selezionare `Mixed Reality Toolkit Examples`
1. Individuare gli esempi desiderati `Samples` nell'elenco
1. Fare clic su`Import into Project`.

![Importazione di esempi](../features/images/packaging/MRTK_ExamplesUpm.png)

Quando viene aggiornato un pacchetto di esempio, Unity offre la possibilità di aggiornare gli esempi importati.

> [!NOTE]
> L'aggiornamento di un esempio importato sovrascriverà tutte le modifiche apportate a tale esempio e agli asset associati.

## <a name="see-also"></a>Vedere anche

- [Pacchetti di Toolkit realtà mista](../packages-releases/mrtk-packages.md)

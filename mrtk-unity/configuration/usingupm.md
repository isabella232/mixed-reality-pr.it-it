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
# <a name="using-the-unity-package-manager"></a><span data-ttu-id="c530f-104">Uso dell'Gestione pacchetti Unity</span><span class="sxs-lookup"><span data-stu-id="c530f-104">Using the Unity Package Manager</span></span>

<span data-ttu-id="c530f-105">A partire dalla versione 2.5.0, con lo strumento di funzionalità di realtà mista [,](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool)Microsoft Mixed Reality Toolkit si integra con Unity Gestione pacchetti (UPM) quando si usa Unity 2019.4 e versioni più nuove.</span><span class="sxs-lookup"><span data-stu-id="c530f-105">Starting with version 2.5.0, using the [Mixed Reality Feature Tool](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool), the Microsoft Mixed Reality Toolkit integrates with the Unity Package Manager (UPM) when using Unity 2019.4 and newer.</span></span>

## <a name="using-the-mixed-reality-feature-tool"></a><span data-ttu-id="c530f-106">Uso dello strumento di funzionalità di realtà mista</span><span class="sxs-lookup"><span data-stu-id="c530f-106">Using the Mixed Reality Feature Tool</span></span>

<span data-ttu-id="c530f-107">Come descritto in Welcome to the Mixed Reality Feature Tool (Introduzione [a Mixed Reality Feature Tool),](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool) è possibile scaricare lo strumento usando questo [collegamento.](https://aka.ms/MRFeatureTool)</span><span class="sxs-lookup"><span data-stu-id="c530f-107">As described in [Welcome to the Mixed Reality Feature Tool](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool) you can download the tool using [this link](https://aka.ms/MRFeatureTool).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c530f-108">Se il manifesto del progetto include una voce nella sezione , è `Microsoft Mixed Reality` `scopedRegistries` consigliabile che venga rimosso.</span><span class="sxs-lookup"><span data-stu-id="c530f-108">If the project's manifest has a `Microsoft Mixed Reality` entry in the `scopedRegistries` section, it is recommended that it be removed.</span></span>
>
> <span data-ttu-id="c530f-109">Per rimuovere un registro con ambito configurato, accedere a `Edit`  >  `Project Settings`  >  `Package Manager` .</span><span class="sxs-lookup"><span data-stu-id="c530f-109">To remove a configured scoped registry, please to to `Edit` > `Project Settings` > `Package Manager`.</span></span>
>
> ![Rimozione del Registro di sistema con ambito](../features/images/packaging/RemoveScopedRegistry.png)

<span data-ttu-id="c530f-111">I pacchetti MRTK vengono visualizzati sotto `Mixed Reality Toolkit` l'intestazione quando si individuano le funzionalità.</span><span class="sxs-lookup"><span data-stu-id="c530f-111">MRTK packages appear under the `Mixed Reality Toolkit` heading when discovering features.</span></span>

![Individuare le funzionalità](../features/images/packaging/DiscoverFeatures.png)

<span data-ttu-id="c530f-113">Quando si selezionano le funzionalità, non è necessario preoccuparsi delle dipendenze necessarie. Lo strumento le scarica e le integra automaticamente nel progetto.</span><span class="sxs-lookup"><span data-stu-id="c530f-113">When selecting features, there is no need to be concerned with required dependencies, the tool will automatically download and integrate them into the project.</span></span>

![Dipendenze necessarie](../features/images/packaging/RequiredDependencies.png)

## <a name="managing-mixed-reality-features-with-the-unity-package-manager"></a><span data-ttu-id="c530f-115">Gestione delle funzionalità di realtà mista con Unity Gestione pacchetti</span><span class="sxs-lookup"><span data-stu-id="c530f-115">Managing Mixed Reality features with the Unity Package Manager</span></span>

<span data-ttu-id="c530f-116">Dopo che un pacchetto Toolkit realtà mista è stato aggiunto al manifesto del pacchetto, può essere gestito usando l'interfaccia utente Gestione pacchetti unity.</span><span class="sxs-lookup"><span data-stu-id="c530f-116">Once a Mixed Reality Toolkit package has been added to the package manifest, it can be managed using the Unity Package Manager user interface.</span></span>

![Pacchetto UPM di MRTK Foundation](../features/images/packaging/MRTK_FoundationUPM.png)

> [!NOTE]
> <span data-ttu-id="c530f-118">Se un pacchetto Toolkit realtà mista viene rimosso usando unity Gestione pacchetti, sarà necessario aggiungere di nuovo il pacchetto usando i [passaggi descritti in precedenza.](#using-the-mixed-reality-feature-tool)</span><span class="sxs-lookup"><span data-stu-id="c530f-118">If a Mixed Reality Toolkit package is removed using the Unity Package Manager, it will have to be re-added using the [previously described steps](#using-the-mixed-reality-feature-tool).</span></span>

### <a name="using-mixed-reality-toolkit-examples"></a><span data-ttu-id="c530f-119">Uso di esempi Toolkit realtà mista</span><span class="sxs-lookup"><span data-stu-id="c530f-119">Using Mixed Reality Toolkit examples</span></span>

<span data-ttu-id="c530f-120">A differenza di quando si usano file di pacchetto asset (con estensione unitypackage) e non importare automaticamente le scene `com.microsoft.mixedreality.toolkit.examples` e gli asset di `com.microsoft.mixedreality.toolkit.handphysicsservice` esempio.</span><span class="sxs-lookup"><span data-stu-id="c530f-120">Unlike when using asset package (.unitypackage) files, `com.microsoft.mixedreality.toolkit.examples` and `com.microsoft.mixedreality.toolkit.handphysicsservice` do not automatically import the example scenes and assets.</span></span>

<span data-ttu-id="c530f-121">Per usare uno o più esempi, seguire questa procedura:</span><span class="sxs-lookup"><span data-stu-id="c530f-121">To utilize one or more of the examples, please use the following steps:</span></span>

1. <span data-ttu-id="c530f-122">Nell'editor di Unity passare a `Window` > `Package Manager`</span><span class="sxs-lookup"><span data-stu-id="c530f-122">In the Unity Editor, navigate to `Window` > `Package Manager`</span></span>
1. <span data-ttu-id="c530f-123">Nell'elenco dei pacchetti selezionare `Mixed Reality Toolkit Examples`</span><span class="sxs-lookup"><span data-stu-id="c530f-123">In the list of packages, select `Mixed Reality Toolkit Examples`</span></span>
1. <span data-ttu-id="c530f-124">Individuare gli esempi desiderati `Samples` nell'elenco</span><span class="sxs-lookup"><span data-stu-id="c530f-124">Locate the desired sample(s) in the `Samples` list</span></span>
1. <span data-ttu-id="c530f-125">Fare clic su`Import into Project`.</span><span class="sxs-lookup"><span data-stu-id="c530f-125">Click `Import into Project`</span></span>

![Importazione di esempi](../features/images/packaging/MRTK_ExamplesUpm.png)

<span data-ttu-id="c530f-127">Quando viene aggiornato un pacchetto di esempio, Unity offre la possibilità di aggiornare gli esempi importati.</span><span class="sxs-lookup"><span data-stu-id="c530f-127">When an example package is updated, Unity provides the option to update imported samples.</span></span>

> [!NOTE]
> <span data-ttu-id="c530f-128">L'aggiornamento di un esempio importato sovrascriverà tutte le modifiche apportate all'esempio e agli asset associati.</span><span class="sxs-lookup"><span data-stu-id="c530f-128">Updating an imported sample will overwrite any changes that have been made to that sample and the associated assets.</span></span>

## <a name="see-also"></a><span data-ttu-id="c530f-129">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="c530f-129">See Also</span></span>

- [<span data-ttu-id="c530f-130">Pacchetti Toolkit realtà mista</span><span class="sxs-lookup"><span data-stu-id="c530f-130">Mixed Reality Toolkit packages</span></span>](../packages/mrtk-packages.md)

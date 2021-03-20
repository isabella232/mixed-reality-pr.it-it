---
title: Uso di gestione pacchetti Unity
description: Uso di MRTK in Unity pakage Manager
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK pakages,
ms.openlocfilehash: a231ae1d286541ae66ba4576b6eb11142a38170f
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2021
ms.locfileid: "104701817"
---
# <a name="mixed-reality-toolkit-and-unity-package-manager"></a><span data-ttu-id="fdc72-104">Toolkit per realtà mista e gestione pacchetti Unity</span><span class="sxs-lookup"><span data-stu-id="fdc72-104">Mixed Reality Toolkit and Unity Package Manager</span></span>

<span data-ttu-id="fdc72-105">A partire dalla versione 2.5.0, usando lo strumento per la [funzionalità di realtà mista](https://aka.ms/MRFeatureToolDocs), Microsoft Mixed Reality Toolkit si integra con gestione pacchetti Unity (UPM) quando si usa unity 2019,4 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="fdc72-105">Starting with version 2.5.0, using the [Mixed Reality Feature Tool](https://aka.ms/MRFeatureToolDocs), the Microsoft Mixed Reality Toolkit integrates with the Unity Package Manager (UPM) when using Unity 2019.4 and newer.</span></span>

## <a name="using-the-mixed-reality-feature-tool"></a><span data-ttu-id="fdc72-106">Uso dello strumento funzionalità per la realtà mista</span><span class="sxs-lookup"><span data-stu-id="fdc72-106">Using the Mixed Reality Feature Tool</span></span>

<span data-ttu-id="fdc72-107">Come descritto in [Introduzione allo strumento per la funzionalità di realtà mista](https://aka.ms/MRFeatureToolDocs) , è possibile scaricare lo strumento usando [questo collegamento](https://aka.ms/MRFeatureTool).</span><span class="sxs-lookup"><span data-stu-id="fdc72-107">As described in [Welcome to the Mixed Reality Feature Tool](https://aka.ms/MRFeatureToolDocs) you can download the tool using [this link](https://aka.ms/MRFeatureTool).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="fdc72-108">Se nel manifesto del progetto è `Microsoft Mixed Reality` presente una voce nella `scopedRegistries` sezione, è consigliabile rimuoverla.</span><span class="sxs-lookup"><span data-stu-id="fdc72-108">If the project's manifest has a `Microsoft Mixed Reality` entry in the `scopedRegistries` section, it is recommended that it be removed.</span></span>
>
> <span data-ttu-id="fdc72-109">Per rimuovere un registro con ambito configurato, rivolgersi a a `Edit`  >  `Project Settings`  >  `Package Manager` .</span><span class="sxs-lookup"><span data-stu-id="fdc72-109">To remove a configured scoped registry, please to to `Edit` > `Project Settings` > `Package Manager`.</span></span>
>
> ![Rimozione del registro di sistema con ambito](../features/images/packaging/RemoveScopedRegistry.png)

<span data-ttu-id="fdc72-111">I pacchetti MRTK vengono visualizzati sotto l' `Mixed Reality Toolkit` intestazione durante l'individuazione delle funzionalità.</span><span class="sxs-lookup"><span data-stu-id="fdc72-111">MRTK packages appear under the `Mixed Reality Toolkit` heading when discovering features.</span></span>

![Individua funzionalità](../features/images/packaging/DiscoverFeatures.png)

<span data-ttu-id="fdc72-113">Quando si selezionano le funzionalità, non è necessario preoccuparsi delle dipendenze richieste, che verranno scaricate e integrate automaticamente nel progetto.</span><span class="sxs-lookup"><span data-stu-id="fdc72-113">When selecting features, there is no need to be concerned with required dependencies, the tool will automatically download and integrate them into the project.</span></span>

![Dipendenze obbligatorie](../features/images/packaging/RequiredDependencies.png)

## <a name="managing-mixed-reality-features-with-the-unity-package-manager"></a><span data-ttu-id="fdc72-115">Gestione delle funzionalità della realtà mista con gestione pacchetti Unity</span><span class="sxs-lookup"><span data-stu-id="fdc72-115">Managing Mixed Reality features with the Unity Package Manager</span></span>

<span data-ttu-id="fdc72-116">Una volta aggiunto al manifesto del pacchetto, un pacchetto del Toolkit di realtà mista può essere gestito tramite l'interfaccia utente di gestione pacchetti Unity.</span><span class="sxs-lookup"><span data-stu-id="fdc72-116">Once a Mixed Reality Toolkit package has been added to the package manifest, it can be managed using the Unity Package Manager user interface.</span></span>

![Pacchetto UPM MRTK Foundation](../features/images/packaging/MRTK_FoundationUPM.png)

> [!NOTE]
> <span data-ttu-id="fdc72-118">Se un pacchetto del Toolkit di realtà mista viene rimosso tramite Gestione pacchetti Unity, sarà necessario aggiungerlo di nuovo usando i [passaggi descritti in precedenza](#using-the-mixed-reality-feature-tool).</span><span class="sxs-lookup"><span data-stu-id="fdc72-118">If a Mixed Reality Toolkit package is removed using the Unity Package Manager, it will have to be re-added using the [previously described steps](#using-the-mixed-reality-feature-tool).</span></span>

### <a name="using-mixed-reality-toolkit-examples"></a><span data-ttu-id="fdc72-119">Esempi di utilizzo del Toolkit di realtà mista</span><span class="sxs-lookup"><span data-stu-id="fdc72-119">Using Mixed Reality Toolkit examples</span></span>

<span data-ttu-id="fdc72-120">Diversamente da quando si usano i file di pacchetto asset (con estensione file unitypackage Tools), `com.microsoft.mixedreality.toolkit.examples` `com.microsoft.mixedreality.toolkit.handphysicsservice` non vengono importati automaticamente gli asset e le scene di esempio.</span><span class="sxs-lookup"><span data-stu-id="fdc72-120">Unlike when using asset package (.unitypackage) files, `com.microsoft.mixedreality.toolkit.examples` and `com.microsoft.mixedreality.toolkit.handphysicsservice` do not automatically import the example scenes and assets.</span></span>

<span data-ttu-id="fdc72-121">Per usare uno o più degli esempi, attenersi alla procedura seguente:</span><span class="sxs-lookup"><span data-stu-id="fdc72-121">To utilize one or more of the examples, please use the following steps:</span></span>

1. <span data-ttu-id="fdc72-122">Nell'editor di Unity passare a `Window` > `Package Manager`</span><span class="sxs-lookup"><span data-stu-id="fdc72-122">In the Unity Editor, navigate to `Window` > `Package Manager`</span></span>
1. <span data-ttu-id="fdc72-123">Nell'elenco dei pacchetti selezionare `Mixed Reality Toolkit Examples`</span><span class="sxs-lookup"><span data-stu-id="fdc72-123">In the list of packages, select `Mixed Reality Toolkit Examples`</span></span>
1. <span data-ttu-id="fdc72-124">Individuare gli esempi desiderati nell' `Samples` elenco</span><span class="sxs-lookup"><span data-stu-id="fdc72-124">Locate the desired sample(s) in the `Samples` list</span></span>
1. <span data-ttu-id="fdc72-125">Fare clic su`Import into Project`.</span><span class="sxs-lookup"><span data-stu-id="fdc72-125">Click `Import into Project`</span></span>

![Importazione di esempi](../features/images/packaging/MRTK_ExamplesUpm.png)

<span data-ttu-id="fdc72-127">Quando viene aggiornato un pacchetto di esempio, Unity offre la possibilità di aggiornare gli esempi importati.</span><span class="sxs-lookup"><span data-stu-id="fdc72-127">When an example package is updated, Unity provides the option to update imported samples.</span></span>

> [!NOTE]
> <span data-ttu-id="fdc72-128">L'aggiornamento di un esempio importato sovrascriverà tutte le modifiche apportate all'esempio e alle risorse associate.</span><span class="sxs-lookup"><span data-stu-id="fdc72-128">Updating an imported sample will overwrite any changes that have been made to that sample and the associated assets.</span></span>

## <a name="see-also"></a><span data-ttu-id="fdc72-129">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="fdc72-129">See Also</span></span>

- [<span data-ttu-id="fdc72-130">Pacchetti Toolkit per realtà mista</span><span class="sxs-lookup"><span data-stu-id="fdc72-130">Mixed Reality Toolkit packages</span></span>](../packages/mrtk-packages.md)

---
title: Ancoraggi spaziali in Unity
description: Informazioni su come creare, archiviare e recuperare gli ancoraggi spaziali nelle applicazioni di realtà mista di Unity.
author: hferrone
ms.author: v-hferrone
ms.date: 03/16/2021
ms.topic: article
keywords: Unity, ancoraggi spaziali, archivio di ancoraggio, HoloLens, cuffie per realtà mista, cuffia a realtà mista di Windows, auricolare della realtà virtuale
ms.openlocfilehash: 665cdae56f271a061972922af835ff64bdc35496
ms.sourcegitcommit: d5e4eb94c87b86a7774a639f11cd9e35a7050107
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/17/2021
ms.locfileid: "103623621"
---
# <a name="spatial-anchors-in-unity"></a><span data-ttu-id="41168-104">Ancoraggi spaziali in Unity</span><span class="sxs-lookup"><span data-stu-id="41168-104">Spatial Anchors in Unity</span></span>

<span data-ttu-id="41168-105">Gli ancoraggi spaziali salvano gli ologrammi nello spazio reale tra le sessioni dell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="41168-105">Spatial anchors save holograms in real-world space between application sessions.</span></span> <span data-ttu-id="41168-106">Una volta salvati nell'archivio di ancoraggio di HoloLens, è possibile trovarli e caricarli in sessioni diverse e costituiscono un fallback ideale in assenza di connettività Internet.</span><span class="sxs-lookup"><span data-stu-id="41168-106">Once saved in the HoloLens' anchor store, they can be found and loaded in different sessions and are an ideal fallback when there's no internet connectivity.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="41168-107">Gli ancoraggi locali vengono archiviati nel dispositivo, mentre i dati relativi ad Ancoraggi nello spazio di Azure vengono archiviati nel cloud.</span><span class="sxs-lookup"><span data-stu-id="41168-107">Local anchors are stored on device, while Azure Spatial Anchors are stored in the cloud.</span></span> <span data-ttu-id="41168-108">Se si vuole usare i servizi cloud di Azure per archiviare gli ancoraggi, è disponibile un documento che fornisce informazioni dettagliate sull'integrazione di [Ancoraggi nello spazio di Azure](../mixed-reality-cloud-services.md#azure-spatial-anchors).</span><span class="sxs-lookup"><span data-stu-id="41168-108">If you're looking to use Azure cloud services to store your anchors, we have a document that can walk you through integrating [Azure Spatial Anchors](../mixed-reality-cloud-services.md#azure-spatial-anchors).</span></span> <span data-ttu-id="41168-109">Si noti che è possibile includere ancoraggi locali e ancoraggi di Azure nello stesso progetto senza che si verifichino conflitti.</span><span class="sxs-lookup"><span data-stu-id="41168-109">Note that you can have local and Azure anchors in the same project without conflict.</span></span>

## <a name="understanding-anchors"></a><span data-ttu-id="41168-110">Informazioni sugli ancoraggi</span><span class="sxs-lookup"><span data-stu-id="41168-110">Understanding Anchors</span></span>

[!INCLUDE[](includes/unity-understanding-anchors.md)]

## <a name="using-the-anchorstore"></a><span data-ttu-id="41168-111">Uso di AnchorStore</span><span class="sxs-lookup"><span data-stu-id="41168-111">Using the AnchorStore</span></span>

[!INCLUDE[](includes/unity-spatial-anchorstore.md)]

## <a name="next-development-checkpoint"></a><span data-ttu-id="41168-112">Successivo checkpoint di sviluppo</span><span class="sxs-lookup"><span data-stu-id="41168-112">Next Development Checkpoint</span></span>

<span data-ttu-id="41168-113">Se si sta seguendo il percorso di checkpoint per lo sviluppo di Unity, è possibile esplorare i blocchi predefiniti di base della realtà mista.</span><span class="sxs-lookup"><span data-stu-id="41168-113">If you're following the Unity development checkpoint journey we've laid out, you're in the midst of exploring the Mixed Reality core building blocks.</span></span> <span data-ttu-id="41168-114">Da qui è possibile passare al blocco predefinito successivo:</span><span class="sxs-lookup"><span data-stu-id="41168-114">From here, you can continue to the next building block:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="41168-115">Mapping spaziale</span><span class="sxs-lookup"><span data-stu-id="41168-115">Spatial mapping</span></span>](spatial-mapping-in-unity.md)

<span data-ttu-id="41168-116">In alternativa, passare alle API e alle funzionalità della piattaforma di realtà mista:</span><span class="sxs-lookup"><span data-stu-id="41168-116">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="41168-117">Esperienze condivise</span><span class="sxs-lookup"><span data-stu-id="41168-117">Shared experiences</span></span>](shared-experiences-in-unity.md)

<span data-ttu-id="41168-118">È sempre possibile tornare ai [checkpoint per lo sviluppo con Unity](unity-development-overview.md#2-core-building-blocks) in qualsiasi momento.</span><span class="sxs-lookup"><span data-stu-id="41168-118">You can always go back to the [Unity development checkpoints](unity-development-overview.md#2-core-building-blocks) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="41168-119">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="41168-119">See Also</span></span>
* [<span data-ttu-id="41168-120">Persistenza di ancoraggio spaziale</span><span class="sxs-lookup"><span data-stu-id="41168-120">Spatial anchor persistence</span></span>](../../design/coordinate-systems.md#spatial-anchor-persistence)
* <span data-ttu-id="41168-121"><a href="/azure/spatial-anchors" target="_blank">Ancoraggi nello spazio di Azure</a></span><span class="sxs-lookup"><span data-stu-id="41168-121"><a href="/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a></span></span>
* <span data-ttu-id="41168-122"><a href="/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Azure Spatial Anchors SDK per Unity</a></span><span class="sxs-lookup"><span data-stu-id="41168-122"><a href="/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Azure Spatial Anchors SDK for Unity</a></span></span>
* [<span data-ttu-id="41168-123">Scale Experience</span><span class="sxs-lookup"><span data-stu-id="41168-123">Experience scales</span></span>](../../design/coordinate-systems.md#mixed-reality-experience-scales)
* [<span data-ttu-id="41168-124">Fase spaziale</span><span class="sxs-lookup"><span data-stu-id="41168-124">Spatial stage</span></span>](../../design/coordinate-systems.md#stage-frame-of-reference)
* [<span data-ttu-id="41168-125">Perdita del rilevamento in Unity</span><span class="sxs-lookup"><span data-stu-id="41168-125">Tracking loss in Unity</span></span>](tracking-loss-in-unity.md)
* [<span data-ttu-id="41168-126">Ancoraggi nello spazio</span><span class="sxs-lookup"><span data-stu-id="41168-126">Spatial anchors</span></span>](../../design/spatial-anchors.md)
* [<span data-ttu-id="41168-127">Esperienze condivise in Unity</span><span class="sxs-lookup"><span data-stu-id="41168-127">Shared experiences in Unity</span></span>](shared-experiences-in-unity.md)
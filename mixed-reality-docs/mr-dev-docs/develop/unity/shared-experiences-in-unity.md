---
title: Esperienze condivise in Unity
description: Informazioni su come condividere gli stessi ologrammi tra più utenti in un'applicazione Unity con gli ancoraggi spaziali di Azure.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: Condivisione, ancoraggio, WorldAnchor, MR sharing 250, WorldAnchorTransferBatch, SpatialPerception, Azure, ancoraggi spaziali di Azure, ASA, auricolare realtà mista, auricolare di realtà mista di Windows, auricolare della realtà virtuale
ms.openlocfilehash: a82439d5676bf4bcb7898a33aafc29b43e91a49f
ms.sourcegitcommit: b13c517df19179ca281362a1f006914289c58ad4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2021
ms.locfileid: "98031957"
---
# <a name="shared-experiences-in-unity"></a><span data-ttu-id="fd01c-104">Esperienze condivise in Unity</span><span class="sxs-lookup"><span data-stu-id="fd01c-104">Shared experiences in Unity</span></span>

<span data-ttu-id="fd01c-105">Un'esperienza condivisa consente a più utenti, ognuno con il proprio dispositivo HoloLens, iOS o Android, di visualizzare e interagire collettivamente con lo stesso ologramma.</span><span class="sxs-lookup"><span data-stu-id="fd01c-105">A shared experience lets multiple users, each with their own HoloLens, iOS or Android device, collectively view and interact with the same hologram.</span></span> <span data-ttu-id="fd01c-106">Gli ologrammi vengono posizionati in un punto fisso nello spazio attraverso la condivisione di ancoraggio spaziale.</span><span class="sxs-lookup"><span data-stu-id="fd01c-106">Holograms are positioned at a fixed point in space through spatial anchor sharing.</span></span>

## <a name="azure-spatial-anchors"></a><span data-ttu-id="fd01c-107">Ancoraggi nello spazio di Azure</span><span class="sxs-lookup"><span data-stu-id="fd01c-107">Azure Spatial Anchors</span></span>

<span data-ttu-id="fd01c-108">Gli <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">ancoraggi spaziali di Azure</a> creano ancoraggi spaziali durevoli basati sul cloud, che possono essere individuati dall'app su più dispositivi HoloLens, iOS e Android.</span><span class="sxs-lookup"><span data-stu-id="fd01c-108"><a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> create durable cloud-backed spatial anchors, which your app can then locate across multiple HoloLens, iOS and Android devices.</span></span>  <span data-ttu-id="fd01c-109">Condividendo un ancoraggio spaziale comune tra più dispositivi, ogni utente può visualizzare il contenuto di cui è stato eseguito il rendering relativo a tale ancoraggio nella stessa posizione fisica.</span><span class="sxs-lookup"><span data-stu-id="fd01c-109">By sharing a common spatial anchor across multiple devices, each user can see content rendered relative to that anchor in the same physical location.</span></span> 

<span data-ttu-id="fd01c-110">È anche possibile usare gli <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">ancoraggi spaziali di Azure</a> per la persistenza ologramma asincrona nei dispositivi HoloLens, iOS e Android.</span><span class="sxs-lookup"><span data-stu-id="fd01c-110">You can also use <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> for asynchronous hologram persistence across HoloLens, iOS, and Android devices.</span></span>  <span data-ttu-id="fd01c-111">Grazie alla condivisione di un ancoraggio spaziale cloud durevole, più dispositivi possono osservare lo stesso ologramma persistente nel tempo, anche se i dispositivi non sono presenti contemporaneamente.</span><span class="sxs-lookup"><span data-stu-id="fd01c-111">By sharing a durable cloud spatial anchor, multiple devices can observe the same persisted hologram over time, even if those devices aren't present together at the same time.</span></span>

<span data-ttu-id="fd01c-112">Per iniziare a creare esperienze condivise in Unity, provare le <a href="https://docs.microsoft.com/azure/spatial-anchors/unity-overview" target="_blank">guide introduttive Unity Anchors di Azure</a>di 5 minuti.</span><span class="sxs-lookup"><span data-stu-id="fd01c-112">To get started building shared experiences in Unity, try out the 5-minute <a href="https://docs.microsoft.com/azure/spatial-anchors/unity-overview" target="_blank">Azure Spatial Anchors Unity quickstarts</a>.</span></span>

<span data-ttu-id="fd01c-113">Una volta configurati gli ancoraggi spaziali di Azure, è possibile <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">creare e individuare ancoraggi in Unity</a>.</span><span class="sxs-lookup"><span data-stu-id="fd01c-113">Once Azure Spatial Anchors is set up, you can <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">create and locate anchors in Unity</a>.</span></span>

## <a name="local-anchor-transfers"></a><span data-ttu-id="fd01c-114">Trasferimenti di ancoraggio locali</span><span class="sxs-lookup"><span data-stu-id="fd01c-114">Local anchor transfers</span></span>

<span data-ttu-id="fd01c-115">Nei casi in cui non è possibile usare gli ancoraggi spaziali di Azure, i [trasferimenti di ancoraggio locali](../../out-of-scope/local-anchor-transfers-in-unity.md) consentono a un dispositivo HoloLens di esportare un ancoraggio in modo che un secondo HoloLens possa importarlo.</span><span class="sxs-lookup"><span data-stu-id="fd01c-115">In situations where you can't use Azure Spatial Anchors, [local anchor transfers](../../out-of-scope/local-anchor-transfers-in-unity.md) enable one HoloLens device to export an anchor so that a second HoloLens can import it.</span></span>  <span data-ttu-id="fd01c-116">Questo approccio non è supportato nei dispositivi iOS e Android e fornisce un richiamo di ancoraggio meno affidabile rispetto agli ancoraggi spaziali di Azure.</span><span class="sxs-lookup"><span data-stu-id="fd01c-116">This approach is not supported on iOS and Android devices, and provides less robust anchor recall than Azure Spatial Anchors.</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="fd01c-117">Successivo checkpoint di sviluppo</span><span class="sxs-lookup"><span data-stu-id="fd01c-117">Next Development Checkpoint</span></span>

<span data-ttu-id="fd01c-118">Se si sta seguendo il percorso di sviluppo di Unity, è possibile esplorare le funzionalità e le API della piattaforma per la realtà mista.</span><span class="sxs-lookup"><span data-stu-id="fd01c-118">If you're following the Unity development journey we've laid out, you're in the midst of exploring the Mixed Reality platform capabilities and APIs.</span></span> <span data-ttu-id="fd01c-119">Da qui è possibile passare alla sezione successiva:</span><span class="sxs-lookup"><span data-stu-id="fd01c-119">From here, you can continue to the next section:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="fd01c-120">Fotocamera individuabile</span><span class="sxs-lookup"><span data-stu-id="fd01c-120">Locatable camera</span></span>](locatable-camera-in-unity.md)

<span data-ttu-id="fd01c-121">In alternativa, passare direttamente alla distribuzione dell'app in un dispositivo o emulatore:</span><span class="sxs-lookup"><span data-stu-id="fd01c-121">Or jump directly to deploying your app on a device or emulator:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="fd01c-122">Eseguire la distribuzione in HoloLens o in modalità mista di Windows per la realtà mista</span><span class="sxs-lookup"><span data-stu-id="fd01c-122">Deploy to HoloLens or Windows Mixed Reality immersive headsets</span></span>](../platform-capabilities-and-apis/using-visual-studio.md)

<span data-ttu-id="fd01c-123">È sempre possibile tornare ai [checkpoint per lo sviluppo con Unity](unity-development-overview.md#3-platform-capabilities-and-apis) in qualsiasi momento.</span><span class="sxs-lookup"><span data-stu-id="fd01c-123">You can always go back to the [Unity development checkpoints](unity-development-overview.md#3-platform-capabilities-and-apis) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="fd01c-124">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="fd01c-124">See also</span></span>
* [<span data-ttu-id="fd01c-125">Esperienze condivise nella realtà mista</span><span class="sxs-lookup"><span data-stu-id="fd01c-125">Shared experiences in mixed reality</span></span>](../platform-capabilities-and-apis/shared-experiences-in-mixed-reality.md)
* <span data-ttu-id="fd01c-126"><a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Ancoraggi nello spazio di Azure</a></span><span class="sxs-lookup"><span data-stu-id="fd01c-126"><a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a></span></span>
* <span data-ttu-id="fd01c-127"><a href="https://docs.microsoft.com/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Azure Spatial Anchors SDK per Unity</a></span><span class="sxs-lookup"><span data-stu-id="fd01c-127"><a href="https://docs.microsoft.com/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Azure Spatial Anchors SDK for Unity</a></span></span>

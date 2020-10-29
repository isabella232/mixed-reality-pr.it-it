---
title: Esperienze condivise in Unity
description: Condividere gli stessi ologrammi tra più utenti in un'applicazione Unity.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: Condivisione, ancoraggio, WorldAnchor, MR sharing 250, WorldAnchorTransferBatch, SpatialPerception, Azure, ancoraggi spaziali di Azure, ASA
ms.openlocfilehash: 324aecdc89b4996625ce93514616c32d2d064ffa
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/03/2020
ms.locfileid: "91684805"
---
# <a name="shared-experiences-in-unity"></a><span data-ttu-id="2f521-104">Esperienze condivise in Unity</span><span class="sxs-lookup"><span data-stu-id="2f521-104">Shared experiences in Unity</span></span>

<span data-ttu-id="2f521-105">Un'esperienza condivisa è quella in cui più utenti, ognuno con il proprio dispositivo HoloLens, iOS o Android, visualizzano collettivamente e interagiscono con lo stesso ologramma posizionato in un punto fisso nello spazio.</span><span class="sxs-lookup"><span data-stu-id="2f521-105">A shared experience is one where multiple users, each with their own HoloLens, iOS or Android device, collectively view and interact with the same hologram which is positioned at a fixed point in space.</span></span> <span data-ttu-id="2f521-106">Questa operazione viene eseguita tramite la condivisione di ancoraggio spaziale.</span><span class="sxs-lookup"><span data-stu-id="2f521-106">This is accomplished through spatial anchor sharing.</span></span>

## <a name="azure-spatial-anchors"></a><span data-ttu-id="2f521-107">Ancoraggi nello spazio di Azure</span><span class="sxs-lookup"><span data-stu-id="2f521-107">Azure Spatial Anchors</span></span>

<span data-ttu-id="2f521-108">È possibile usare gli <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">ancoraggi spaziali di Azure</a> per creare ancoraggi spaziali durevoli basati sul cloud, che possono essere individuati dall'app su più dispositivi HoloLens, iOS e Android.</span><span class="sxs-lookup"><span data-stu-id="2f521-108">You can use <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> to create durable cloud-backed spatial anchors, which your app can then locate across multiple HoloLens, iOS and Android devices.</span></span>  <span data-ttu-id="2f521-109">Condividendo un ancoraggio spaziale comune tra più dispositivi, ogni utente può visualizzare il contenuto di cui è stato eseguito il rendering relativo a tale ancoraggio nella stessa posizione fisica.</span><span class="sxs-lookup"><span data-stu-id="2f521-109">By sharing a common spatial anchor across multiple devices, each user can see content rendered relative to that anchor in the same physical location.</span></span>  <span data-ttu-id="2f521-110">Ciò rende possibili esperienze condivise in tempo reale.</span><span class="sxs-lookup"><span data-stu-id="2f521-110">This allows for real-time shared experiences.</span></span>

<span data-ttu-id="2f521-111">Puoi usare <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Ancoraggi nello spazio di Azure</a> anche per la persistenza asincrona degli ologrammi su dispositivi HoloLens, iOS e Android.</span><span class="sxs-lookup"><span data-stu-id="2f521-111">You can also use <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> for asynchronous hologram persistence across HoloLens, iOS and Android devices.</span></span>  <span data-ttu-id="2f521-112">Condividendo un ancoraggio durevole nello spazio del cloud, più dispositivi possono osservare nel tempo lo stesso ologramma salvato in modo permanente, anche se tali dispositivi non sono presenti insieme contemporaneamente.</span><span class="sxs-lookup"><span data-stu-id="2f521-112">By sharing a durable cloud spatial anchor, multiple devices can observe the same persisted hologram over time, even if those devices are not present together at the same time.</span></span>

<span data-ttu-id="2f521-113">Per iniziare a creare esperienze condivise in Unity, provare le <a href="https://docs.microsoft.com/azure/spatial-anchors/unity-overview" target="_blank">guide introduttive Unity Anchors di Azure</a>di 5 minuti.</span><span class="sxs-lookup"><span data-stu-id="2f521-113">To get started building shared experiences in Unity, try out the 5-minute <a href="https://docs.microsoft.com/azure/spatial-anchors/unity-overview" target="_blank">Azure Spatial Anchors Unity quickstarts</a>.</span></span>

<span data-ttu-id="2f521-114">Quando si è operativi con i Anchor spaziali di Azure, è possibile <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">creare e individuare ancoraggi in Unity</a>.</span><span class="sxs-lookup"><span data-stu-id="2f521-114">Once you're up and running with Azure Spatial Anchors, you can then <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">create and locate anchors in Unity</a>.</span></span>

## <a name="local-anchor-transfers"></a><span data-ttu-id="2f521-115">Trasferimenti di ancoraggio locali</span><span class="sxs-lookup"><span data-stu-id="2f521-115">Local anchor transfers</span></span>

<span data-ttu-id="2f521-116">Nei casi in cui non è possibile usare gli ancoraggi spaziali di Azure, i [trasferimenti di ancoraggio locali](../../out-of-scope/local-anchor-transfers-in-unity.md) consentono a un dispositivo HoloLens di esportare un ancoraggio per l'importazione da parte di un secondo dispositivo HoloLens.</span><span class="sxs-lookup"><span data-stu-id="2f521-116">In situations where you cannot use Azure Spatial Anchors, [local anchor transfers](../../out-of-scope/local-anchor-transfers-in-unity.md) enable one HoloLens device to export an anchor to be imported by a second HoloLens device.</span></span>  <span data-ttu-id="2f521-117">Si noti che questo approccio offre un richiamo di ancoraggio meno affidabile rispetto agli ancoraggi spaziali di Azure e i dispositivi iOS e Android non sono supportati da questo approccio.</span><span class="sxs-lookup"><span data-stu-id="2f521-117">Note that this approach provides less robust anchor recall than Azure Spatial Anchors, and iOS and Android devices are not supported by this approach.</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="2f521-118">Checkpoint di sviluppo successivo</span><span class="sxs-lookup"><span data-stu-id="2f521-118">Next Development Checkpoint</span></span>

<span data-ttu-id="2f521-119">Se si segue il percorso di checkpoint per lo sviluppo di Unity, è possibile esplorare le funzionalità e le API della piattaforma per la realtà mista.</span><span class="sxs-lookup"><span data-stu-id="2f521-119">If you're following the Unity development checkpoint journey we've laid out, you're in the midst of exploring the Mixed Reality platform capabilities and APIs.</span></span> <span data-ttu-id="2f521-120">Da qui è possibile passare all'argomento successivo:</span><span class="sxs-lookup"><span data-stu-id="2f521-120">From here, you can proceed to the next topic:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="2f521-121">Fotocamera individuabile</span><span class="sxs-lookup"><span data-stu-id="2f521-121">Locatable camera</span></span>](locatable-camera-in-unity.md)

<span data-ttu-id="2f521-122">In alternativa, passare direttamente alla distribuzione dell'app in un dispositivo o in un emulatore:</span><span class="sxs-lookup"><span data-stu-id="2f521-122">Or jump directly to deploying your app on a device or emulator:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="2f521-123">Eseguire la distribuzione in HoloLens o in modalità mista di Windows per la realtà mista</span><span class="sxs-lookup"><span data-stu-id="2f521-123">Deploy to HoloLens or Windows Mixed Reality immersive headsets</span></span>](../platform-capabilities-and-apis/using-visual-studio.md)

<span data-ttu-id="2f521-124">È sempre possibile tornare ai checkpoint per [lo sviluppo di Unity](unity-development-overview.md#3-platform-capabilities-and-apis) in qualsiasi momento.</span><span class="sxs-lookup"><span data-stu-id="2f521-124">You can always go back to the [Unity development checkpoints](unity-development-overview.md#3-platform-capabilities-and-apis) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="2f521-125">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="2f521-125">See also</span></span>
* [<span data-ttu-id="2f521-126">Esperienze condivise nella realtà mista</span><span class="sxs-lookup"><span data-stu-id="2f521-126">Shared experiences in mixed reality</span></span>](../platform-capabilities-and-apis/shared-experiences-in-mixed-reality.md)
* <span data-ttu-id="2f521-127"><a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Ancoraggi nello spazio di Azure</a></span><span class="sxs-lookup"><span data-stu-id="2f521-127"><a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a></span></span>
* <span data-ttu-id="2f521-128"><a href="https://docs.microsoft.com/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Azure Spatial Anchors SDK per Unity</a></span><span class="sxs-lookup"><span data-stu-id="2f521-128"><a href="https://docs.microsoft.com/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Azure Spatial Anchors SDK for Unity</a></span></span>

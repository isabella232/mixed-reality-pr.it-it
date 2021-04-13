---
title: Sguardo fisso in Unity
description: Informazioni su come usare l'input di sguardi come un modo principale per consentire agli utenti di individuare gli ologrammi creati dall'app in realtà mista.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: occhi, sguardi, Unity, ologramma, realtà mista, cuffie per realtà mista, auricolare di realtà mista, auricolare di realtà virtuale, MRTK, Toolkit di realtà mista
ms.openlocfilehash: 98eb4445d04b236dea74917d9c51108b66d6df3b
ms.sourcegitcommit: 1c9035487270af76c6eaba11b11f6fc56c008135
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/13/2021
ms.locfileid: "107300366"
---
# <a name="head-gaze-in-unity"></a><span data-ttu-id="8df88-104">Sguardo da capo in Unity</span><span class="sxs-lookup"><span data-stu-id="8df88-104">Head-gaze in Unity</span></span>

<span data-ttu-id="8df88-105">Lo [sguardo](../../design/gaze-and-commit.md) è il modo principale per consentire agli utenti di individuare gli [ologrammi](../../discover/hologram.md) creati dall'app in [realtà mista](../../discover/mixed-reality.md).</span><span class="sxs-lookup"><span data-stu-id="8df88-105">[Gaze](../../design/gaze-and-commit.md) is the primary way for users to target [holograms](../../discover/hologram.md) your app creates in [Mixed Reality](../../discover/mixed-reality.md).</span></span>

## <a name="implementing-head-gaze"></a><span data-ttu-id="8df88-106">Implementazione dell'Head-sguardi</span><span class="sxs-lookup"><span data-stu-id="8df88-106">Implementing head-gaze</span></span>

<span data-ttu-id="8df88-107">A livello concettuale, è possibile determinare lo [sguardo a capo](../../design/gaze-and-commit.md) proiettando un raggio dall'auricolare dell'utente per verificarne il risultato.</span><span class="sxs-lookup"><span data-stu-id="8df88-107">Conceptually, you determine [head-gaze](../../design/gaze-and-commit.md) by projecting a ray forward from the user's headset to see what it hits.</span></span> <span data-ttu-id="8df88-108">In Unity, la posizione e la direzione della testa dell'utente vengono esposte tramite la [fotocamera](camera-in-unity.md), in particolare [UnityEngine. camera. Main](https://docs.unity3d.com/ScriptReference/Camera-main.html). [Transform. inoltr](https://docs.unity3d.com/ScriptReference/Transform-forward.html) e [UnityEngine. camera. Main](https://docs.unity3d.com/ScriptReference/Camera-main.html). [Transform. Position](https://docs.unity3d.com/ScriptReference/Transform-position.html).</span><span class="sxs-lookup"><span data-stu-id="8df88-108">In Unity, the user's head position and direction are exposed through the [Camera](camera-in-unity.md), specifically [UnityEngine.Camera.main](https://docs.unity3d.com/ScriptReference/Camera-main.html).[transform.forward](https://docs.unity3d.com/ScriptReference/Transform-forward.html) and [UnityEngine.Camera.main](https://docs.unity3d.com/ScriptReference/Camera-main.html).[transform.position](https://docs.unity3d.com/ScriptReference/Transform-position.html).</span></span>

<span data-ttu-id="8df88-109">La chiamata a [Physics. RayCast](https://docs.unity3d.com/ScriptReference/Physics.Raycast.html) fornisce un [RaycastHit](https://docs.unity3d.com/ScriptReference/RaycastHit.html) che contiene informazioni sulla collisione, tra cui il punto di collisione 3D e l'altro GameObject il raggio d'occhio.</span><span class="sxs-lookup"><span data-stu-id="8df88-109">Calling [Physics.RayCast](https://docs.unity3d.com/ScriptReference/Physics.Raycast.html) gives you a [RaycastHit](https://docs.unity3d.com/ScriptReference/RaycastHit.html) containing information about the collision, including the 3D collision point and the other GameObject the head-gaze ray hit.</span></span>

### <a name="example-implement-head-gaze"></a><span data-ttu-id="8df88-110">Esempio: implementare l'Head-sguardi</span><span class="sxs-lookup"><span data-stu-id="8df88-110">Example: Implement head-gaze</span></span>

```cs
void Update()
{
       RaycastHit hitInfo;
       if (Physics.Raycast(
               Camera.main.transform.position,
               Camera.main.transform.forward,
               out hitInfo,
               20.0f,
               Physics.DefaultRaycastLayers))
       {
           // If the Raycast has succeeded and hit a hologram
           // hitInfo's point represents the position being gazed at
           // hitInfo's collider GameObject represents the hologram being gazed at
       }
}
```

### <a name="best-practices"></a><span data-ttu-id="8df88-111">Procedure consigliate</span><span class="sxs-lookup"><span data-stu-id="8df88-111">Best practices</span></span>

<span data-ttu-id="8df88-112">Mentre l'esempio precedente genera una singola Raycast dal ciclo di aggiornamento per trovare la destinazione a cui punta l'utente, si consiglia di usare un singolo oggetto per gestire tutti i processi con lo sguardo a capo.</span><span class="sxs-lookup"><span data-stu-id="8df88-112">While the example above fires a single raycast from the update loop to find the target the user's head points at, we recommended using a single object to manage all head-gaze processes.</span></span> <span data-ttu-id="8df88-113">Combinando la logica di puntamento, la potenza di elaborazione dell'app viene salvata e il Raycasting viene limitato a uno per fotogramma.</span><span class="sxs-lookup"><span data-stu-id="8df88-113">Combining your head-gaze logic will save your app precious processing power and limit your raycasting to one per frame.</span></span>

## <a name="visualizing-head-gaze"></a><span data-ttu-id="8df88-114">Visualizzazione dell'Head-sguardi</span><span class="sxs-lookup"><span data-stu-id="8df88-114">Visualizing head-gaze</span></span>

<span data-ttu-id="8df88-115">Analogamente a quanto avviene con un puntatore del mouse su un computer, è necessario implementare un [cursore](../../design/cursors.md) che rappresenti l'Head-sguardi dell'utente.</span><span class="sxs-lookup"><span data-stu-id="8df88-115">Just like with a mouse pointer on a computer, you should implement a [cursor](../../design/cursors.md) that represents the user's head-gaze.</span></span> <span data-ttu-id="8df88-116">Conoscere il contenuto di destinazione di un utente aumenta la fiducia nell'interazione con.</span><span class="sxs-lookup"><span data-stu-id="8df88-116">Knowing what content a user is targeting increases confidence in what they're about to interact with.</span></span>

## <a name="head-gaze-in-the-mixed-reality-toolkit"></a><span data-ttu-id="8df88-117">Head-sguardi nel Toolkit per la realtà mista</span><span class="sxs-lookup"><span data-stu-id="8df88-117">Head-gaze in the Mixed Reality Toolkit</span></span>

<span data-ttu-id="8df88-118">È possibile accedere a Head-sguardi da [Gestione input](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/input/overview) in MRTK.</span><span class="sxs-lookup"><span data-stu-id="8df88-118">You can access head-gaze from the [Input Manager](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/input/overview) in MRTK.</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="8df88-119">Successivo checkpoint di sviluppo</span><span class="sxs-lookup"><span data-stu-id="8df88-119">Next Development Checkpoint</span></span>

<span data-ttu-id="8df88-120">Se si sta seguendo il percorso di sviluppo di Unity, si sta per esplorare i blocchi predefiniti di MRTK core.</span><span class="sxs-lookup"><span data-stu-id="8df88-120">If you're following the Unity development journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="8df88-121">Da qui è possibile passare al blocco predefinito successivo:</span><span class="sxs-lookup"><span data-stu-id="8df88-121">From here, you can continue to the next building block:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="8df88-122">Controller del movimento</span><span class="sxs-lookup"><span data-stu-id="8df88-122">Motion controllers</span></span>](motion-controllers-in-unity.md)

<span data-ttu-id="8df88-123">In alternativa, passare alle API e funzionalità della piattaforma di realtà mista:</span><span class="sxs-lookup"><span data-stu-id="8df88-123">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="8df88-124">Esperienze condivise</span><span class="sxs-lookup"><span data-stu-id="8df88-124">Shared experiences</span></span>](shared-experiences-in-unity.md)

<span data-ttu-id="8df88-125">È sempre possibile tornare ai [checkpoint per lo sviluppo con Unity](unity-development-overview.md#2-core-building-blocks) in qualsiasi momento.</span><span class="sxs-lookup"><span data-stu-id="8df88-125">You can always go back to the [Unity development checkpoints](unity-development-overview.md#2-core-building-blocks) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="8df88-126">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="8df88-126">See also</span></span>
* [<span data-ttu-id="8df88-127">Fotocamera</span><span class="sxs-lookup"><span data-stu-id="8df88-127">Camera</span></span>](camera-in-unity.md)
* [<span data-ttu-id="8df88-128">Cursori</span><span class="sxs-lookup"><span data-stu-id="8df88-128">Cursors</span></span>](../../design/cursors.md)
* [<span data-ttu-id="8df88-129">Puntamento con la testa e commit</span><span class="sxs-lookup"><span data-stu-id="8df88-129">Head-gaze and commit</span></span>](../../design/gaze-and-commit.md)

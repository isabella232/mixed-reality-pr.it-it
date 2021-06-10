---
title: Sguardo fisso in Unity
description: Informazioni su come usare l'input dello sguardo fisso come modo principale per gli utenti di usare come destinazione gli ologrammi creati dall'app nella realtà mista.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: sguardo fisso, sguardo fisso, unity, ologramma, realtà mista, visore VR di realtà mista, visore VR di realtà mista windows, visore VR di realtà virtuale, MRTK, Mixed Reality Toolkit
ms.openlocfilehash: f10079d36f737e5d8a2ee74a88ca0f8b2b3d791c
ms.sourcegitcommit: 9ae76b339968f035c703d9c1fe57ddecb33198e3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/27/2021
ms.locfileid: "110600150"
---
# <a name="head-gaze-in-unity"></a><span data-ttu-id="3db26-104">Sguardo fisso con la testa in Unity</span><span class="sxs-lookup"><span data-stu-id="3db26-104">Head-gaze in Unity</span></span>

<span data-ttu-id="3db26-105">[Lo](../../design/gaze-and-commit.md) sguardo fisso è il modo principale per gli utenti di impostare come destinazione [gli ologrammi](../../discover/hologram.md) creati dall'app in [Realtà mista.](../../discover/mixed-reality.md)</span><span class="sxs-lookup"><span data-stu-id="3db26-105">[Gaze](../../design/gaze-and-commit.md) is the primary way for users to target [holograms](../../discover/hologram.md) your app creates in [Mixed Reality](../../discover/mixed-reality.md).</span></span>

## <a name="implementing-head-gaze"></a><span data-ttu-id="3db26-106">Implementazione dello sguardo fisso con la testa</span><span class="sxs-lookup"><span data-stu-id="3db26-106">Implementing head-gaze</span></span>

<span data-ttu-id="3db26-107">Concettualmente, è possibile [determinare lo sguardo](../../design/gaze-and-commit.md) con la testa proiettando un raggio in avanti dal visore VR dell'utente per vedere cosa raggiunge.</span><span class="sxs-lookup"><span data-stu-id="3db26-107">Conceptually, you determine [head-gaze](../../design/gaze-and-commit.md) by projecting a ray forward from the user's headset to see what it hits.</span></span> <span data-ttu-id="3db26-108">In Unity la posizione e la direzione della testa dell'utente vengono esposte tramite [la fotocamera,](camera-in-unity.md)in particolare [UnityEngine.Camera.main.](https://docs.unity3d.com/ScriptReference/Camera-main.html) [transform.forward](https://docs.unity3d.com/ScriptReference/Transform-forward.html) e [UnityEngine.Camera.main](https://docs.unity3d.com/ScriptReference/Camera-main.html). [transform.position](https://docs.unity3d.com/ScriptReference/Transform-position.html).</span><span class="sxs-lookup"><span data-stu-id="3db26-108">In Unity, the user's head position and direction are exposed through the [Camera](camera-in-unity.md), specifically [UnityEngine.Camera.main](https://docs.unity3d.com/ScriptReference/Camera-main.html).[transform.forward](https://docs.unity3d.com/ScriptReference/Transform-forward.html) and [UnityEngine.Camera.main](https://docs.unity3d.com/ScriptReference/Camera-main.html).[transform.position](https://docs.unity3d.com/ScriptReference/Transform-position.html).</span></span>

<span data-ttu-id="3db26-109">La [chiamata a Physics.RayCast](https://docs.unity3d.com/ScriptReference/Physics.Raycast.html) offre un [RaycastHit](https://docs.unity3d.com/ScriptReference/RaycastHit.html) contenente informazioni sulla collisione, tra cui il punto di collisione 3D e l'altro GameObject in cui è stato raggiunto il raggio dello sguardo con la testa.</span><span class="sxs-lookup"><span data-stu-id="3db26-109">Calling [Physics.RayCast](https://docs.unity3d.com/ScriptReference/Physics.Raycast.html) gives you a [RaycastHit](https://docs.unity3d.com/ScriptReference/RaycastHit.html) containing information about the collision, including the 3D collision point and the other GameObject the head-gaze ray hit.</span></span>

### <a name="example-implement-head-gaze"></a><span data-ttu-id="3db26-110">Esempio: Implementare lo sguardo fisso con la testa</span><span class="sxs-lookup"><span data-stu-id="3db26-110">Example: Implement head-gaze</span></span>

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

### <a name="best-practices"></a><span data-ttu-id="3db26-111">Procedure consigliate</span><span class="sxs-lookup"><span data-stu-id="3db26-111">Best practices</span></span>

<span data-ttu-id="3db26-112">Anche se l'esempio precedente genera un singolo raycast dal ciclo di aggiornamento per trovare la destinazione in cui punta la testa dell'utente, è consigliabile usare un singolo oggetto per gestire tutti i processi di puntamenti con la testa.</span><span class="sxs-lookup"><span data-stu-id="3db26-112">While the example above fires a single raycast from the update loop to find the target the user's head points at, we recommended using a single object to manage all head-gaze processes.</span></span> <span data-ttu-id="3db26-113">La combinazione della logica del sguardo fisso con la testa consente di risparmiare potenza di elaborazione di valore per l'app e limitare il raycasting a uno per fotogramma.</span><span class="sxs-lookup"><span data-stu-id="3db26-113">Combining your head-gaze logic will save your app precious processing power and limit your raycasting to one per frame.</span></span>

## <a name="visualizing-head-gaze"></a><span data-ttu-id="3db26-114">Visualizzazione dello sguardo fisso con la testa</span><span class="sxs-lookup"><span data-stu-id="3db26-114">Visualizing head-gaze</span></span>

<span data-ttu-id="3db26-115">Proprio come con un puntatore del mouse in un computer, è necessario implementare un [cursore](../../design/cursors.md) che rappresenta lo sguardo con la testa dell'utente.</span><span class="sxs-lookup"><span data-stu-id="3db26-115">Just like with a mouse pointer on a computer, you should implement a [cursor](../../design/cursors.md) that represents the user's head-gaze.</span></span> <span data-ttu-id="3db26-116">Conoscere il contenuto di destinazione di un utente aumenta la fiducia nel contenuto con cui sta per interagire.</span><span class="sxs-lookup"><span data-stu-id="3db26-116">Knowing what content a user is targeting increases confidence in what they're about to interact with.</span></span>

## <a name="head-gaze-in-the-mixed-reality-toolkit"></a><span data-ttu-id="3db26-117">Sguardo fisso con la testa in Mixed Reality Toolkit</span><span class="sxs-lookup"><span data-stu-id="3db26-117">Head-gaze in the Mixed Reality Toolkit</span></span>

<span data-ttu-id="3db26-118">È possibile accedere al controllo con la testa da [Input Manager](/windows/mixed-reality/mrtk-unity/features/input/overview) in MRTK.</span><span class="sxs-lookup"><span data-stu-id="3db26-118">You can access head-gaze from the [Input Manager](/windows/mixed-reality/mrtk-unity/features/input/overview) in MRTK.</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="3db26-119">Successivo checkpoint di sviluppo</span><span class="sxs-lookup"><span data-stu-id="3db26-119">Next Development Checkpoint</span></span>

<span data-ttu-id="3db26-120">Se si sta seguendo il percorso di sviluppo di Unity che è stato strutturato, si stanno esplorando i blocchi predefiniti principali di MRTK.</span><span class="sxs-lookup"><span data-stu-id="3db26-120">If you're following the Unity development journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="3db26-121">Da qui è possibile passare al blocco predefinito successivo:</span><span class="sxs-lookup"><span data-stu-id="3db26-121">From here, you can continue to the next building block:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="3db26-122">Controller del movimento</span><span class="sxs-lookup"><span data-stu-id="3db26-122">Motion controllers</span></span>](motion-controllers-in-unity.md)

<span data-ttu-id="3db26-123">In alternativa, passare alle API e funzionalità della piattaforma di realtà mista:</span><span class="sxs-lookup"><span data-stu-id="3db26-123">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="3db26-124">Esperienze condivise</span><span class="sxs-lookup"><span data-stu-id="3db26-124">Shared experiences</span></span>](shared-experiences-in-unity.md)

<span data-ttu-id="3db26-125">È sempre possibile tornare ai [checkpoint per lo sviluppo con Unity](unity-development-overview.md#2-core-building-blocks) in qualsiasi momento.</span><span class="sxs-lookup"><span data-stu-id="3db26-125">You can always go back to the [Unity development checkpoints](unity-development-overview.md#2-core-building-blocks) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="3db26-126">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="3db26-126">See also</span></span>
* [<span data-ttu-id="3db26-127">Fotocamera</span><span class="sxs-lookup"><span data-stu-id="3db26-127">Camera</span></span>](camera-in-unity.md)
* [<span data-ttu-id="3db26-128">Cursori</span><span class="sxs-lookup"><span data-stu-id="3db26-128">Cursors</span></span>](../../design/cursors.md)
* [<span data-ttu-id="3db26-129">Puntamento con la testa e commit</span><span class="sxs-lookup"><span data-stu-id="3db26-129">Head-gaze and commit</span></span>](../../design/gaze-and-commit.md)
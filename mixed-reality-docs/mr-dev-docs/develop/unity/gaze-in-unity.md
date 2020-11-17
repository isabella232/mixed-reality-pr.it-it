---
title: Sguardo fisso in Unity
description: Lo sguardo è un modo principale per consentire agli utenti di individuare gli ologrammi creati dall'app in realtà mista.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: occhi, sguardi, Unity, ologramma, realtà mista, cuffie per realtà mista, auricolare di realtà mista, auricolare di realtà virtuale, MRTK, Toolkit di realtà mista
ms.openlocfilehash: 0c62de9cb1b7ea892831ea2cedbeb23be5ea7b37
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2020
ms.locfileid: "94677510"
---
# <a name="head-gaze-in-unity"></a><span data-ttu-id="57987-104">Sguardo da capo in Unity</span><span class="sxs-lookup"><span data-stu-id="57987-104">Head-gaze in Unity</span></span>

<span data-ttu-id="57987-105">Lo [sguardo](../../design/gaze-and-commit.md) è un modo principale per consentire agli utenti di individuare gli [ologrammi](../../discover/hologram.md) creati dall'app in [realtà mista](../../discover/mixed-reality.md).</span><span class="sxs-lookup"><span data-stu-id="57987-105">[Gaze](../../design/gaze-and-commit.md) is a primary way for users to target the [holograms](../../discover/hologram.md) your app creates in [Mixed Reality](../../discover/mixed-reality.md).</span></span>


## <a name="implementing-head-gaze"></a><span data-ttu-id="57987-106">Implementazione dell'Head-sguardi</span><span class="sxs-lookup"><span data-stu-id="57987-106">Implementing head-gaze</span></span>

<span data-ttu-id="57987-107">Dal punto di vista concettuale, l' [Head-sguardi](../../design/gaze-and-commit.md) viene implementato proiettando un raggio dalla parte iniziale dell'utente in cui si trova l'auricolare, nella direzione in avanti che si trovano e determinano la collisione del raggio.</span><span class="sxs-lookup"><span data-stu-id="57987-107">Conceptually, [head-gaze](../../design/gaze-and-commit.md) is implemented by projecting a ray from the user's head where the headset is, in the forward direction they are facing and determining what that ray collides with.</span></span>
<span data-ttu-id="57987-108">In Unity, la posizione e la direzione della testa dell'utente vengono esposte tramite la [fotocamera](camera-in-unity.md)principale di Unity, in particolare [UnityEngine. camera. Main](https://docs.unity3d.com/ScriptReference/Camera-main.html). [Transform. inoltr](https://docs.unity3d.com/ScriptReference/Transform-forward.html) e [UnityEngine. camera. Main](https://docs.unity3d.com/ScriptReference/Camera-main.html). [Transform. Position](https://docs.unity3d.com/ScriptReference/Transform-position.html).</span><span class="sxs-lookup"><span data-stu-id="57987-108">In Unity, the user's head position and direction are exposed through the Unity Main [Camera](camera-in-unity.md), specifically [UnityEngine.Camera.main](https://docs.unity3d.com/ScriptReference/Camera-main.html).[transform.forward](https://docs.unity3d.com/ScriptReference/Transform-forward.html) and [UnityEngine.Camera.main](https://docs.unity3d.com/ScriptReference/Camera-main.html).[transform.position](https://docs.unity3d.com/ScriptReference/Transform-position.html).</span></span>

<span data-ttu-id="57987-109">La chiamata a [Physics. RayCast](https://docs.unity3d.com/ScriptReference/Physics.Raycast.html) genera una struttura [RaycastHit](https://docs.unity3d.com/ScriptReference/RaycastHit.html) che contiene informazioni sulla collisione, tra cui il punto 3D in cui si è verificata la collisione e l'altro GameObject del raggio di puntamento.</span><span class="sxs-lookup"><span data-stu-id="57987-109">Calling [Physics.RayCast](https://docs.unity3d.com/ScriptReference/Physics.Raycast.html) results in a [RaycastHit](https://docs.unity3d.com/ScriptReference/RaycastHit.html) structure which contains information about the collision including the 3D point where collision occurred and the other GameObject the head-gaze ray collided with.</span></span>

### <a name="example-implement-head-gaze"></a><span data-ttu-id="57987-110">Esempio: implementare l'Head-sguardi</span><span class="sxs-lookup"><span data-stu-id="57987-110">Example: Implement head-gaze</span></span>

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

### <a name="best-practices"></a><span data-ttu-id="57987-111">Procedure consigliate</span><span class="sxs-lookup"><span data-stu-id="57987-111">Best practices</span></span>

<span data-ttu-id="57987-112">Mentre nell'esempio precedente viene illustrato come eseguire un singolo Raycast in un ciclo di aggiornamento per trovare la destinazione a cui puntano gli utenti, è consigliabile eseguire questa operazione in un singolo oggetto che gestisce il controllo, anziché eseguire questa operazione in un oggetto potenzialmente interessato all'oggetto che si sta osservando.</span><span class="sxs-lookup"><span data-stu-id="57987-112">While the example above demonstrates how to do a single raycast in an update loop to find the target the user's head points at, it is recommended to do this in a single object managing head-gaze instead of doing this in any object that is potentially interested in the object being gazed at.</span></span> <span data-ttu-id="57987-113">In questo modo, l'app consente di salvare l'elaborazione eseguendo solo uno sguardo a capo Raycast ogni frame.</span><span class="sxs-lookup"><span data-stu-id="57987-113">This lets your app save processing by doing just one head-gaze raycast each frame.</span></span>

## <a name="visualizing-head-gaze"></a><span data-ttu-id="57987-114">Visualizzazione dell'Head-sguardi</span><span class="sxs-lookup"><span data-stu-id="57987-114">Visualizing head-gaze</span></span>

<span data-ttu-id="57987-115">Proprio come nel desktop in cui si usa un puntatore del mouse per la destinazione e l'interazione con il contenuto, è necessario implementare un [cursore](../../design/cursors.md) che rappresenti il capo dell'utente.</span><span class="sxs-lookup"><span data-stu-id="57987-115">Just like on the desktop where you use a mouse pointer to target and interact with content, you should implement a [cursor](../../design/cursors.md) that represents the user's head-gaze.</span></span> <span data-ttu-id="57987-116">In questo modo l'utente è in confidenza con l'interazione con.</span><span class="sxs-lookup"><span data-stu-id="57987-116">This gives the user confidence in what they're about to interact with.</span></span>

## <a name="head-gaze-in-the-mixed-reality-toolkit-v2"></a><span data-ttu-id="57987-117">Head-sguardi nel Toolkit di realtà misto V2</span><span class="sxs-lookup"><span data-stu-id="57987-117">Head-gaze in the Mixed Reality Toolkit v2</span></span>
<span data-ttu-id="57987-118">È possibile accedere a Head-sguardi da [Gestione input](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html) in MRTK V2.</span><span class="sxs-lookup"><span data-stu-id="57987-118">You can access head-gaze from the [Input Manager](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html) in MRTK v2.</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="57987-119">Successivo checkpoint di sviluppo</span><span class="sxs-lookup"><span data-stu-id="57987-119">Next Development Checkpoint</span></span>

<span data-ttu-id="57987-120">Se si sta seguendo il percorso di checkpoint per lo sviluppo con Unity che abbiamo delineato, si stanno esplorando i blocchi predefiniti fondamentali in MRTK.</span><span class="sxs-lookup"><span data-stu-id="57987-120">If you're following the Unity development checkpoint journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="57987-121">Da qui è possibile passare al blocco predefinito successivo:</span><span class="sxs-lookup"><span data-stu-id="57987-121">From here, you can proceed to the next building block:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="57987-122">Movimenti e controller del movimento</span><span class="sxs-lookup"><span data-stu-id="57987-122">Gestures and motion controllers</span></span>](gestures-and-motion-controllers-in-unity.md)

<span data-ttu-id="57987-123">In alternativa, passare alle API e funzionalità della piattaforma di realtà mista:</span><span class="sxs-lookup"><span data-stu-id="57987-123">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="57987-124">Esperienze condivise</span><span class="sxs-lookup"><span data-stu-id="57987-124">Shared experiences</span></span>](shared-experiences-in-unity.md)

<span data-ttu-id="57987-125">È sempre possibile tornare ai [checkpoint per lo sviluppo con Unity](unity-development-overview.md#2-core-building-blocks) in qualsiasi momento.</span><span class="sxs-lookup"><span data-stu-id="57987-125">You can always go back to the [Unity development checkpoints](unity-development-overview.md#2-core-building-blocks) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="57987-126">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="57987-126">See also</span></span>
* [<span data-ttu-id="57987-127">Fotocamera</span><span class="sxs-lookup"><span data-stu-id="57987-127">Camera</span></span>](camera-in-unity.md)
* [<span data-ttu-id="57987-128">Cursori</span><span class="sxs-lookup"><span data-stu-id="57987-128">Cursors</span></span>](../../design/cursors.md)
* [<span data-ttu-id="57987-129">Puntamento con la testa e commit</span><span class="sxs-lookup"><span data-stu-id="57987-129">Head-gaze and commit</span></span>](../../design/gaze-and-commit.md)

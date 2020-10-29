---
title: Sguardo fisso in Unity
description: Lo sguardo è un modo principale per consentire agli utenti di individuare gli ologrammi creati dall'app in realtà mista.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: occhi, sguardi, Unity, ologramma, realtà mista
ms.openlocfilehash: 8c1a6cb0847cd0e6e776c6d4e1f7c1efdc126279
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/03/2020
ms.locfileid: "91684708"
---
# <a name="head-gaze-in-unity"></a>Sguardo da capo in Unity

Lo [sguardo](../../design/gaze-and-commit.md) è un modo principale per consentire agli utenti di individuare gli [ologrammi](../../discover/hologram.md) creati dall'app in [realtà mista](../../discover/mixed-reality.md).


## <a name="implementing-head-gaze"></a>Implementazione dell'Head-sguardi

Dal punto di vista concettuale, l' [Head-sguardi](../../design/gaze-and-commit.md) viene implementato proiettando un raggio dalla parte iniziale dell'utente in cui si trova l'auricolare, nella direzione in avanti che si trovano e determinano la collisione del raggio.
In Unity, la posizione e la direzione della testa dell'utente vengono esposte tramite la [fotocamera](camera-in-unity.md)principale di Unity, in particolare [UnityEngine. camera. Main](https://docs.unity3d.com/ScriptReference/Camera-main.html). [Transform. inoltr](https://docs.unity3d.com/ScriptReference/Transform-forward.html) e [UnityEngine. camera. Main](https://docs.unity3d.com/ScriptReference/Camera-main.html). [Transform. Position](https://docs.unity3d.com/ScriptReference/Transform-position.html).

La chiamata a [Physics. RayCast](https://docs.unity3d.com/ScriptReference/Physics.Raycast.html) genera una struttura [RaycastHit](https://docs.unity3d.com/ScriptReference/RaycastHit.html) che contiene informazioni sulla collisione, tra cui il punto 3D in cui si è verificata la collisione e l'altro GameObject del raggio di puntamento.

### <a name="example-implement-head-gaze"></a>Esempio: implementare l'Head-sguardi

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

### <a name="best-practices"></a>Procedure consigliate

Mentre nell'esempio precedente viene illustrato come eseguire un singolo Raycast in un ciclo di aggiornamento per trovare la destinazione a cui puntano gli utenti, è consigliabile eseguire questa operazione in un singolo oggetto che gestisce il controllo, anziché eseguire questa operazione in un oggetto potenzialmente interessato all'oggetto che si sta osservando. In questo modo, l'app consente di salvare l'elaborazione eseguendo solo uno sguardo a capo Raycast ogni frame.

## <a name="visualizing-head-gaze"></a>Visualizzazione dell'Head-sguardi

Proprio come nel desktop in cui si usa un puntatore del mouse per la destinazione e l'interazione con il contenuto, è necessario implementare un [cursore](../../design/cursors.md) che rappresenti il capo dell'utente. In questo modo l'utente è in confidenza con l'interazione con.

## <a name="head-gaze-in-the-mixed-reality-toolkit-v2"></a>Head-sguardi nel Toolkit di realtà misto V2
È possibile accedere a Head-sguardi da [Gestione input](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html) in MRTK V2.

## <a name="next-development-checkpoint"></a>Checkpoint di sviluppo successivo

Se si sta seguendo il percorso di checkpoint per lo sviluppo di Unity, è possibile esplorare i blocchi predefiniti di MRTK core. Da qui è possibile passare al blocco predefinito successivo:

> [!div class="nextstepaction"]
> [Movimenti e controller del movimento](gestures-and-motion-controllers-in-unity.md)

In alternativa, passare alle API e alle funzionalità della piattaforma di realtà mista:

> [!div class="nextstepaction"]
> [Esperienze condivise](shared-experiences-in-unity.md)

È sempre possibile tornare ai checkpoint per [lo sviluppo di Unity](unity-development-overview.md#2-core-building-blocks) in qualsiasi momento.

## <a name="see-also"></a>Vedere anche
* [Fotocamera](camera-in-unity.md)
* [Cursori](../../design/cursors.md)
* [Puntamento con la testa e commit](../../design/gaze-and-commit.md)

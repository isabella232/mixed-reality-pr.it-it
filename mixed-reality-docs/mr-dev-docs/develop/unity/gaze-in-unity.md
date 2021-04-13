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
# <a name="head-gaze-in-unity"></a>Sguardo da capo in Unity

Lo [sguardo](../../design/gaze-and-commit.md) è il modo principale per consentire agli utenti di individuare gli [ologrammi](../../discover/hologram.md) creati dall'app in [realtà mista](../../discover/mixed-reality.md).

## <a name="implementing-head-gaze"></a>Implementazione dell'Head-sguardi

A livello concettuale, è possibile determinare lo [sguardo a capo](../../design/gaze-and-commit.md) proiettando un raggio dall'auricolare dell'utente per verificarne il risultato. In Unity, la posizione e la direzione della testa dell'utente vengono esposte tramite la [fotocamera](camera-in-unity.md), in particolare [UnityEngine. camera. Main](https://docs.unity3d.com/ScriptReference/Camera-main.html). [Transform. inoltr](https://docs.unity3d.com/ScriptReference/Transform-forward.html) e [UnityEngine. camera. Main](https://docs.unity3d.com/ScriptReference/Camera-main.html). [Transform. Position](https://docs.unity3d.com/ScriptReference/Transform-position.html).

La chiamata a [Physics. RayCast](https://docs.unity3d.com/ScriptReference/Physics.Raycast.html) fornisce un [RaycastHit](https://docs.unity3d.com/ScriptReference/RaycastHit.html) che contiene informazioni sulla collisione, tra cui il punto di collisione 3D e l'altro GameObject il raggio d'occhio.

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

Mentre l'esempio precedente genera una singola Raycast dal ciclo di aggiornamento per trovare la destinazione a cui punta l'utente, si consiglia di usare un singolo oggetto per gestire tutti i processi con lo sguardo a capo. Combinando la logica di puntamento, la potenza di elaborazione dell'app viene salvata e il Raycasting viene limitato a uno per fotogramma.

## <a name="visualizing-head-gaze"></a>Visualizzazione dell'Head-sguardi

Analogamente a quanto avviene con un puntatore del mouse su un computer, è necessario implementare un [cursore](../../design/cursors.md) che rappresenti l'Head-sguardi dell'utente. Conoscere il contenuto di destinazione di un utente aumenta la fiducia nell'interazione con.

## <a name="head-gaze-in-the-mixed-reality-toolkit"></a>Head-sguardi nel Toolkit per la realtà mista

È possibile accedere a Head-sguardi da [Gestione input](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/input/overview) in MRTK.

## <a name="next-development-checkpoint"></a>Successivo checkpoint di sviluppo

Se si sta seguendo il percorso di sviluppo di Unity, si sta per esplorare i blocchi predefiniti di MRTK core. Da qui è possibile passare al blocco predefinito successivo:

> [!div class="nextstepaction"]
> [Controller del movimento](motion-controllers-in-unity.md)

In alternativa, passare alle API e funzionalità della piattaforma di realtà mista:

> [!div class="nextstepaction"]
> [Esperienze condivise](shared-experiences-in-unity.md)

È sempre possibile tornare ai [checkpoint per lo sviluppo con Unity](unity-development-overview.md#2-core-building-blocks) in qualsiasi momento.

## <a name="see-also"></a>Vedere anche
* [Fotocamera](camera-in-unity.md)
* [Cursori](../../design/cursors.md)
* [Puntamento con la testa e commit](../../design/gaze-and-commit.md)

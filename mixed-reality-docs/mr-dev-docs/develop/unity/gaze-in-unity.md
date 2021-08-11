---
title: Sguardo fisso in Unity
description: Informazioni su come usare l'input dello sguardo fisso come modo principale per consentire agli utenti di usare come destinazione gli ologrammi creati dall'app nella realtà mista.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: sguardo oculare, sguardo alla testa, unity, ologramma, realtà mista, visore per realtà mista, visore windows mixed reality, visore per realtà virtuale, MRTK, realtà mista Toolkit
ms.openlocfilehash: c6a435e958a92adeed6cd965bebd0b8829e00da735bd193ca72a68acb9e0d6aa
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115200114"
---
# <a name="head-gaze-in-unity"></a>Sguardo con la testa in Unity

[Lo](../../design/gaze-and-commit.md) sguardo fisso è il modo principale per consentire agli utenti di impostare come destinazione [gli ologrammi](../../discover/hologram.md) creati dall'app in [Realtà mista.](../../discover/mixed-reality.md)

## <a name="implementing-head-gaze"></a>Implementazione dello sguardo rivolto verso la testa

Concettualmente, è possibile [determinare lo](../../design/gaze-and-commit.md) sguardo rivolto verso la testa proiettando un raggio in avanti dal visore dell'utente per vedere cosa raggiunge. In Unity la posizione e la direzione della testa dell'utente vengono esposte tramite [la fotocamera](camera-in-unity.md), in particolare [UnityEngine.Camera.main](https://docs.unity3d.com/ScriptReference/Camera-main.html). [transform.forward e](https://docs.unity3d.com/ScriptReference/Transform-forward.html) [UnityEngine.Camera.main](https://docs.unity3d.com/ScriptReference/Camera-main.html). [transform.position](https://docs.unity3d.com/ScriptReference/Transform-position.html).

La [chiamata a Physics.RayCast](https://docs.unity3d.com/ScriptReference/Physics.Raycast.html) offre un [RaycastHit](https://docs.unity3d.com/ScriptReference/RaycastHit.html) contenente informazioni sulla collisione, tra cui il punto di collisione 3D e l'altro GameObject, il raggio dello sguardo alla testa.

### <a name="example-implement-head-gaze"></a>Esempio: Implementare lo sguardo rivolto verso la testa

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

Mentre l'esempio precedente genera un singolo raycast dal ciclo di aggiornamento per trovare la destinazione a cui punta la testa dell'utente, è consigliabile usare un singolo oggetto per gestire tutti i processi head-gaze. La combinazione della logica head-gaze consente di risparmiare potenza di elaborazione preziosi per l'app e limitare il raycasting a uno per fotogramma.

## <a name="visualizing-head-gaze"></a>Visualizzazione dello sguardo rivolto verso la testa

Proprio come con un puntatore del mouse su un computer, è necessario implementare un [cursore](../../design/cursors.md) che rappresenta lo sguardo alla testa dell'utente. Conoscere il contenuto di destinazione di un utente aumenta l'attendibilità di ciò con cui sta per interagire.

## <a name="head-gaze-in-the-mixed-reality-toolkit"></a>Sguardo rivolto verso la testa nell'Toolkit

È possibile accedere al head-gaze da [Input Manager](/windows/mixed-reality/mrtk-unity/features/input/overview) in MRTK.

## <a name="next-development-checkpoint"></a>Successivo checkpoint di sviluppo

Se si sta seguendo il percorso di sviluppo di Unity che è stato previsto, si stanno esplorando i blocchi predefiniti principali di MRTK. Da qui è possibile passare al blocco predefinito successivo:

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
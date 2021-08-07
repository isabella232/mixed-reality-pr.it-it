---
title: SceneSystemLightingScenes
description: Documentazione sull'illuminazione nella scena.
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: 5dfb8337d14c5d361e4a6ff21030a3b7c738908a4cfcd43b07aa006b91b9f8e1
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115213158"
---
# <a name="lighting-scene-operations"></a>Operazioni della scena di illuminazione

La scena di illuminazione predefinita definita nel profilo viene caricata all'avvio. Tale scena di illuminazione rimane caricata fino a quando `SetLightingScene` non viene chiamato .

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

sceneSystem.SetLightingScene("MorningLighting");
```

## <a name="lighting-setting-transitions"></a>Transizioni delle impostazioni di illuminazione

`transitionType` controlla lo stile della transizione alla nuova scena di illuminazione.

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

sceneSystem.SetLightingScene("MiddayLighting", LightingSceneTransitionType.CrossFade);
```

Gli stili disponibili sono:

Tipo | Descrizione | Durata
--- | --- | ---
Nessuno | La scena di illuminazione precedente viene scaricata e viene caricata una nuova scena di illuminazione. Nessuna transizione. | Ignorato
FadeToBlack | La scena di illuminazione precedente si dissolve in nero. Viene caricata una nuova scena di illuminazione, quindi sfumare dal nero. Utile per transizioni fluide tra le posizioni. | Usata
Dissolvenza incrociata | La scena di illuminazione precedente si dissolve quando la nuova scena di illuminazione si dissolve. Utile per transizioni fluide tra le impostazioni di illuminazione nella stessa posizione. | Usata

Si noti che alcune impostazioni di illuminazione non possono essere interpolate durante le transizioni. Se si vuole una transizione visiva uniforme, queste impostazioni devono rimanere coerenti tra le scene di illuminazione.

Impostazione | Transizione Smooth FadeToBlack | Transizione Smooth CrossFade
--- | --- | ---
Skybox | No | No
Reflection personalizzate | No | No
Ombreggiature in tempo reale luce solare | Sì | No

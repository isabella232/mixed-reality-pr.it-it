---
title: SceneSystemLightingScenes
description: Documentazione sull'illuminazione nella scena.
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: 4cd6b61172f03da99ba33a06d06e20f095572622
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2021
ms.locfileid: "104685094"
---
# <a name="lighting-scene-operations"></a>Operazioni di illuminazione della scena

La scena di illuminazione predefinita definita nel profilo viene caricata all'avvio. La scena di illuminazione rimane caricata fino a quando non `SetLightingScene` viene chiamato il metodo.

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

sceneSystem.SetLightingScene("MorningLighting");
```

## <a name="lighting-setting-transitions"></a>Transizioni di impostazioni di illuminazione

`transitionType` Controlla lo stile della transizione alla nuova scena di illuminazione.

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

sceneSystem.SetLightingScene("MiddayLighting", LightingSceneTransitionType.CrossFade);
```

Gli stili disponibili sono:

Tipo | Descrizione | Duration
--- | --- | ---
nessuno | La scena di illuminazione precedente è scaricata e viene caricata una nuova scena di illuminazione. Nessuna transizione. | Ignorato
FadeToBlack | La scena di illuminazione precedente si dissolve in nero. La nuova scena di illuminazione è stata caricata, quindi è svanita dal nero. Utile per transizioni uniformi tra i percorsi. | Usata
CrossFade | La scena di illuminazione precedente si dissolve quando la nuova scena di illuminazione si affievolisce. Utile per transizioni uniformi tra le impostazioni di illuminazione nella stessa posizione. | Usata

Si noti che alcune impostazioni di illuminazione non possono essere interpolate durante le transizioni. Se si vuole una transizione visiva uniforme, queste impostazioni dovranno rimanere coerenti tra le scene di illuminazione.

Impostazione | Transizione Smooth FadeToBlack | Transizione senza dissolvenza
--- | --- | ---
SKYBOX | No | No
Riflessioni personalizzate | No | No
Shadows in tempo reale luce solare | Sì | No

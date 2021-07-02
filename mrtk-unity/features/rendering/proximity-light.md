---
title: Luce di prossimità
description: Documentazione sulla luce di prossimità con esempi in MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: 6e57a76d54d0f3f63ce8dcb80582e178effa39d9
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176386"
---
# <a name="proximity-light"></a>Luce di prossimità

Un è un paradigma Fluent Design System che simula una "luce del punto inverso sfumatura" che si posiziona accanto [`ProximityLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) alla superficie di un oggetto. [](https://www.microsoft.com/design/fluent/) Spesso usata per le interazioni da vicino, l'applicazione può controllare le proprietà di una luce di prossimità tramite il [`ProximityLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) componente .

Perché un materiale sia influenzato da uno shader Toolkit/Standard di realtà mista, è necessario usare e la proprietà Luce di prossimità [`ProximityLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) deve essere  abilitata. 

> [!NOTE]
> Per impostazione [`ProximityLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) predefinita, sono supportate fino a due.

## <a name="examples"></a>Esempio

La maggior parte delle scene all'interno di MRTK usa un [`ProximityLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) oggetto . Il caso d'uso più comune è disponibile in MRTK/SDK/Features/UX/Prefabs/Cursors/FingerCursor.prefab

## <a name="advanced-usage"></a>Utilizzo avanzato

Per impostazione predefinita, [`ProximityLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) solo due possono illuminare [un](https://docs.unity3d.com/ScriptReference/Material.html) materiale alla volta. Se il progetto richiede più di due elementi [`ProximityLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) per influenzare un [materiale,](https://docs.unity3d.com/ScriptReference/Material.html) il codice di esempio seguente illustra come ottenere questo risultato.

> [!NOTE]
> La presenza [`ProximityLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) di molti elementi che [illuminano un](https://docs.unity3d.com/ScriptReference/Material.html) materiale aumenterà pixel shader istruzioni e inciderà sulle prestazioni. Profilare queste modifiche all'interno del progetto.

*Come aumentare il numero di disponibili [`ProximityLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) da due a quattro.*

```C#
// 1) Within MRTK/Core/StandardAssets/Shaders/MixedRealityStandard.shader change:

#define PROXIMITY_LIGHT_COUNT 2

// to:

#define PROXIMITY_LIGHT_COUNT 4

// 2) Within MRTK/Core/Utilities/StandardShader/ProximityLight.cs change:

private const int proximityLightCount = 2;

// to:

private const int proximityLightCount = 4;
```

> [!NOTE]
> Se Unity registra un avviso simile al seguente, è necessario riavviare Unity prima che le modifiche avranno effetto.
>
>`Property (_ProximityLightData) exceeds previous array size (24 vs 12). Cap to previous size.`

## <a name="see-also"></a>Vedere anche

* [MRTK Standard Shader](mrtk-standard-shader.md)

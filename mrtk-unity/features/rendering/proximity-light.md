---
title: Luce di prossimità
description: Documentazione sulla luce di prossimità con esempi in MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: 1be58cd22228258d51f63b2a4db0294bceaec1320640ecbbfa2795edde5e39bd
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115208321"
---
# <a name="proximity-light"></a>Luce di prossimità

Un [`ProximityLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) è un [paradigma Fluent Design System](https://www.microsoft.com/design/fluent/) che simula una "luce del punto inverso della sfumatura" che si sposta vicino alla superficie di un oggetto. Spesso usata per le interazioni near, l'applicazione può controllare le proprietà di una luce di prossimità tramite il [`ProximityLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) componente .

Perché un materiale sia influenzato da uno shader Toolkit/Standard di realtà mista, è necessario che sia abilitata [`ProximityLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) la proprietà *Luce* di prossimità. 

> [!NOTE]
> Per impostazione [`ProximityLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) predefinita, sono supportate fino a due.

## <a name="examples"></a>Esempio

La maggior parte delle scene all'interno di MRTK usa un [`ProximityLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) oggetto . Il caso d'uso più comune è disponibile in MRTK/SDK/Features/UX/Prefabs/Cursors/FingerCursor.prefab

## <a name="advanced-usage"></a>Utilizzo avanzato

Per impostazione predefinita, [`ProximityLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) solo due possono [illuminare un materiale](https://docs.unity3d.com/ScriptReference/Material.html) alla volta. Se il progetto richiede più di due elementi per influenzare un materiale, il codice di esempio seguente [`ProximityLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) illustra come ottenere questo risultato. [](https://docs.unity3d.com/ScriptReference/Material.html)

> [!NOTE]
> La presenza [`ProximityLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) di molti elementi che [illuminano un](https://docs.unity3d.com/ScriptReference/Material.html) materiale aumenta pixel shader istruzioni e influisce sulle prestazioni. Profilare queste modifiche all'interno del progetto.

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

## <a name="see-also"></a>Vedi anche

* [MRTK Standard Shader](mrtk-standard-shader.md)

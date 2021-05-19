---
title: Luce del passaggio del mouse
description: Documentazione su HoverLight con esempi in MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realtà mista, sviluppo, MRTK, Hover Light,
ms.openlocfilehash: b98dff0dd3ff0312f6ce607a5fb8a26f94959ff2
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/19/2021
ms.locfileid: "110145172"
---
# <a name="hover-light"></a>Luce del passaggio del mouse

Un [`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) è un [paradigma Fluent Design System](https://www.microsoft.com/design/fluent/) che [](https://docs.unity3d.com/Manual/Lighting.html) simula una luce del punto che si sposta vicino alla superficie di un oggetto. Spesso usata per interazioni di distanza, l'applicazione può controllare le proprietà di una luce al passaggio del mouse tramite il [`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) componente .

Perché un materiale sia influenzato da uno [`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) shader *Mixed Reality Toolkit/Standard,* è necessario che sia abilitata la proprietà *Hover Light.*

> [!Note]
> Lo shader MRTK/Standard supporta fino a due per impostazione predefinita, ma verrà ridimensionato in modo da supportare quattro e quindi dieci quando vengono aggiunte altre luci [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) alla scena.

## <a name="examples"></a>Esempio

La maggior parte delle scene all'interno di MRTK usa un [`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) oggetto . Il caso d'uso più comune è disponibile in MRTK/SDK/Features/UX/Prefabs/Cursors/DefaultCursor.prefab

La **scena HoverLightExamples** illustra anche l'uso dei comportamenti ed è disponibile [`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) in: MRTK/Examples/Demos/StandardShader/Scenes/

## <a name="advanced-usage"></a>Utilizzo avanzato

Solo dieci [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) possono illuminare [un materiale](https://docs.unity3d.com/ScriptReference/Material.html) alla volta. Se il progetto richiede più di dieci elementi per influenzare un materiale, il codice di esempio seguente [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) illustra come ottenere questo risultato. [](https://docs.unity3d.com/ScriptReference/Material.html)

> [!Note]
> La presenza [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) di molti elementi che [illuminano un](https://docs.unity3d.com/ScriptReference/Material.html) materiale aumenta pixel shader istruzioni e influisce sulle prestazioni. **Profilare queste modifiche all'interno del progetto.**

*Come aumentare il numero di disponibili [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) da dieci a dodici.*

```C#
// 1) Within MRTK/Core/StandardAssets/Shaders/MixedRealityStandard.shader change:

#if defined(_HOVER_LIGHT_HIGH)
#define HOVER_LIGHT_COUNT 10

// to:

#if defined(_HOVER_LIGHT_HIGH)
#define HOVER_LIGHT_COUNT 12

// 2) Within MRTK/Core/Utilities/StandardShader/HoverLight.cs change:

private const int hoverLightCountHigh = 10;

// to:

private const int hoverLightCountHigh = 12;
```

> [!NOTE]
> Se Unity registra un avviso simile al seguente, è necessario riavviare Unity prima che le modifiche avranno effetto.
>
> `Property (_HoverLightData) exceeds previous array size (24 vs 20). Cap to previous >size.`

## <a name="see-also"></a>Vedi anche

* [MRTK Standard Shader](mrtk-standard-shader.md)

---
title: HoverLight
description: Documentazione su HoverLight con esempi in MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, hover light,
ms.openlocfilehash: c528de3aabab6339bd8b9d63eb808756a5a249238fbe5a0deb15ba34c9d961cf
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115214403"
---
# <a name="hover-light"></a>Luce al passaggio del mouse

Un è un paradigma Fluent Design System che simula una luce punto che passa il [`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) puntatore del mouse vicino alla superficie di un oggetto. [](https://www.microsoft.com/design/fluent/) [](https://docs.unity3d.com/Manual/Lighting.html) Spesso usata per le interazioni da lontano, l'applicazione può controllare le proprietà di una luce al passaggio del mouse tramite il [`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) componente .

Perché un materiale sia influenzato da uno shader Toolkit/Standard di Realtà mista deve essere usato e la proprietà Luce al passaggio del mouse [`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) deve essere  abilitata. 

> [!Note]
> Lo shader MRTK/Standard supporta fino a due per impostazione predefinita, ma verrà ridimensionato per supportare quattro e dieci quando vengono aggiunte altre luci [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) alla scena.

## <a name="examples"></a>Esempio

La maggior parte delle scene all'interno di MRTK usa un [`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) oggetto . Il caso d'uso più comune è disponibile in MRTK/SDK/Features/UX/Prefabs/Cursors/DefaultCursor.prefab

La **scena HoverLightExamples** illustra anche l'uso dei comportamenti ed è disponibile [`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) in: MRTK/Examples/Demos/StandardShader/Scenes/

## <a name="advanced-usage"></a>Utilizzo avanzato

Solo dieci [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) possono illuminare [un materiale](https://docs.unity3d.com/ScriptReference/Material.html) alla volta. Se il progetto richiede più di dieci elementi per influenzare un materiale, il codice di esempio [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) seguente illustra come ottenere questo risultato. [](https://docs.unity3d.com/ScriptReference/Material.html)

> [!Note]
> La presenza di [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) molti elementi che [illuminano un](https://docs.unity3d.com/ScriptReference/Material.html) materiale aumenterà pixel shader istruzioni e inciderà sulle prestazioni. **Profilare queste modifiche all'interno del progetto.**

*Come aumentare il numero di disponibili da [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) dieci a dodici.*

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

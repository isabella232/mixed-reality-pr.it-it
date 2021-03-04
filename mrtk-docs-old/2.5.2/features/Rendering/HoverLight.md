---
title: HoverLight
description: Documentazione su HoverLight con esempi in MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, hover Light,
ms.openlocfilehash: af99c84684dd8b50e81ecd27b86e2be5f473e954
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/03/2021
ms.locfileid: "101782265"
---
# <a name="hover-light"></a>Luce al passaggio del mouse

Un [`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) è un paradigma del [sistema di progettazione Fluent](https://www.microsoft.com/design/fluent/) che simula una [luce puntiforme](https://docs.unity3d.com/Manual/Lighting.html) posizionata vicino alla superficie di un oggetto. Spesso usato per le interazioni lontane, l'applicazione può controllare le proprietà di una luce del passaggio del mouse tramite il [`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) componente.

Affinché un materiale venga influenzato da un [`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) Toolkit di *realtà mista o* da un shader standard, è necessario che sia abilitata la proprietà del *passaggio del mouse* .

> [!Note]
> Lo shader MRTK/standard supporta fino a due per [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) impostazione predefinita, ma viene scalato in modo da supportare quattro e poi dieci con l'aggiunta di più luci alla scena.

## <a name="examples"></a>Esempio

La maggior parte delle scene all'interno della MRTK utilizza un [`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) . Il caso d'uso più comune è reperibile in MRTK/SDK/features/UX/prefabrics/Cursors/DefaultCursor. prefabrical

La scena **HoverLightExamples** illustra anche l'uso dei [`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) comportamenti ed è disponibile all'indirizzo: MRTK/examples/Demos/StandardShader/scenes/

## <a name="advanced-usage"></a>Utilizzo avanzato

Solo dieci [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) può illuminare un [materiale](https://docs.unity3d.com/ScriptReference/Material.html) alla volta. Se il progetto richiede più di dieci [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) per influenzare un [materiale](https://docs.unity3d.com/ScriptReference/Material.html) , nel codice di esempio riportato di seguito viene illustrato come ottenere questo risultato.

> [!Note]
> La presenza [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) di molti [materiali](https://docs.unity3d.com/ScriptReference/Material.html) illuminati aumenterà pixel shader istruzioni e influirà sulle prestazioni. **Per profilare queste modifiche all'interno del progetto.**

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
> Se Unity registra un avviso simile a quello riportato di seguito, è necessario riavviare Unity prima che le modifiche siano effettive.
>
> `Property (_HoverLightData) exceeds previous array size (24 vs 20). Cap to previous >size.`

## <a name="see-also"></a>Vedi anche

* [Shader standard MRTK](MRTKStandardShader.md)

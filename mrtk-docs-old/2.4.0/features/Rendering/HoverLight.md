---
title: HoverLight
description: Documentazione su HoverLight con esempi in MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
ms.localizationpriority: medium
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, hover Light,
ms.openlocfilehash: 98090cbb9cc7a18806df710078f8ba19a5f31240
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2021
ms.locfileid: "104681234"
---
# <a name="hover-light"></a>Luce al passaggio del mouse

Un [`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) è un paradigma del [sistema di progettazione Fluent](https://www.microsoft.com/design/fluent/) che simula una [luce puntiforme](https://docs.unity3d.com/Manual/Lighting.html) posizionata vicino alla superficie di un oggetto. Spesso usato per le interazioni lontane, l'applicazione può controllare le proprietà di una luce del passaggio del mouse tramite il [`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) componente.

Affinché un materiale venga influenzato da un [`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) Toolkit di *realtà mista o* da un shader standard, è necessario che sia abilitata la proprietà del *passaggio del mouse* .

> [!Note]
> Per [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) impostazione predefinita, sono supportati fino a due.

## <a name="examples"></a>Esempio

La maggior parte delle scene all'interno della MRTK utilizza un [`HoverLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) . Il caso d'uso più comune è reperibile in MRTK/SDK/features/UX/prefabrics/Cursors/DefaultCursor. prefabrical

## <a name="advanced-usage"></a>Utilizzo avanzato

Per impostazione predefinita, solo due [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) possono illuminare un [materiale](https://docs.unity3d.com/ScriptReference/Material.html) alla volta. Se il progetto richiede più di due [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) per influenzare un [materiale](https://docs.unity3d.com/ScriptReference/Material.html) , nel codice di esempio riportato di seguito viene illustrato come ottenere questo risultato.

> [!Note]
> La presenza [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) di molti [materiali](https://docs.unity3d.com/ScriptReference/Material.html) illuminati aumenterà pixel shader istruzioni e influirà sulle prestazioni. Per profilare queste modifiche all'interno del progetto.

*Come aumentare il numero di disponibili [`HoverLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.HoverLight) da due a quattro.*

```C#
// 1) Within MRTK/Core/StandardAssets/Shaders/MixedRealityStandard.shader change:

#define HOVER_LIGHT_COUNT 2

// to:

#define HOVER_LIGHT_COUNT 4

// 2) Within MRTK/Core/Utilities/StandardShader/HoverLight.cs change:

private const int hoverLightCount = 2;

// to:

private const int hoverLightCount = 4;
```

> [!NOTE]
> Se Unity registra un avviso simile a quello riportato di seguito, è necessario riavviare Unity prima che le modifiche siano effettive.
>
> `Property (_HoverLightData) exceeds previous array size (8 vs 4). Cap to previous >size.`

## <a name="see-also"></a>Vedi anche

* [Shader standard MRTK](../README_MRTKStandardShader.md)

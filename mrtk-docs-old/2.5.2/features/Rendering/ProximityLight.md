---
title: ProximityLight
description: Documentazione su prossimità Light con esempi in MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: 9b29dc5f52180ae4251ab27455002cb18e3ea1f9
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2021
ms.locfileid: "104691288"
---
# <a name="proximity-light"></a>Luce vicina

Un [`ProximityLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) è un paradigma del [sistema di progettazione Fluent](https://www.microsoft.com/design/fluent/) che simula una "sfumatura del punto inverso della sfumatura" accanto alla superficie di un oggetto. Spesso usato per le interazioni near, l'applicazione può controllare le proprietà di una luce di prossimità tramite il [`ProximityLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) componente.

Affinché un materiale venga influenzato da un [`ProximityLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) Toolkit di *realtà mista o* da un shader standard, è necessario che sia abilitata la proprietà *prossimità luce* .

> [!NOTE]
> Per [`ProximityLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) impostazione predefinita, sono supportati fino a due.

## <a name="examples"></a>Esempio

La maggior parte delle scene all'interno della MRTK utilizza un [`ProximityLight`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) . Il caso d'uso più comune è reperibile in MRTK/SDK/features/UX/prefabrics/Cursors/FingerCursor. prefabrical

## <a name="advanced-usage"></a>Utilizzo avanzato

Per impostazione predefinita, solo due [`ProximityLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) possono illuminare un [materiale](https://docs.unity3d.com/ScriptReference/Material.html) alla volta. Se il progetto richiede più di due [`ProximityLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) per influenzare un [materiale](https://docs.unity3d.com/ScriptReference/Material.html) , nel codice di esempio riportato di seguito viene illustrato come ottenere questo risultato.

> [!NOTE]
> La presenza [`ProximityLights`](xref:Microsoft.MixedReality.Toolkit.Utilities.ProximityLight) di molti [materiali](https://docs.unity3d.com/ScriptReference/Material.html) illuminati aumenterà pixel shader istruzioni e influirà sulle prestazioni. Per profilare queste modifiche all'interno del progetto.

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
> Se Unity registra un avviso simile a quello riportato di seguito, è necessario riavviare Unity prima che le modifiche siano effettive.
>
>`Property (_ProximityLightData) exceeds previous array size (24 vs 12). Cap to previous size.`

## <a name="see-also"></a>Vedi anche

* [Shader standard MRTK](MRTKStandardShader.md)

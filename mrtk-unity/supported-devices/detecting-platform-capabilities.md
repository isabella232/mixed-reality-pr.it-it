---
title: Rilevamento delle funzionalità della piattaforma
description: Dettagli delle diverse funzionalità supportate da MRTK
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, funzionalità,
ms.openlocfilehash: 0a3ad248e418e10ad1a7105ca5f9ece3e02c62bd7679cfd22d9c4396016d09a7
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115207609"
---
# <a name="detecting-platform-capabilities"></a>Rilevamento delle funzionalità della piattaforma

Una domanda comune su MRTK consiste nel sapere quale dispositivo specifico (ad esempio, Microsoft HoloLens 2) viene usato per eseguire un'applicazione. L'identificazione dell'hardware esatto può risultare complessa in piattaforme diverse. MrTK consente invece di identificare funzionalità specifiche in fase di esecuzione, ad esempio se l'endpoint del dispositivo corrente supporta mani articolate.

## <a name="capabilities"></a>Funzionalità

L'Toolkit di realtà mista fornisce l'enumerazione , che definisce un set di funzionalità per cui un'applicazione [`MixedRealityCapability`](xref:Microsoft.MixedReality.Toolkit.MixedRealityCapability) può eseguire query in fase di esecuzione.

### <a name="input-system-capabilities"></a>Funzionalità del sistema di input

Il sistema di input MRTK predefinito supporta l'esecuzione di query sulle funzionalità seguenti:

| Funzionalità | Descrizione |
|---|---|
| ArticulatedHand | Input manuale articolato |
| EyeTracking | Targeting dello sguardo fisso |
| GGVHand | Input della mano Gaze-Gesture-Voice |
| MotionController | Input del controller di movimento |
| VoiceCommand | Comandi vocali con parole chiave definite dall'app |
| VoiceDictation | Dettatura da voce a testo |

Il codice di esempio seguente verifica se il sistema di input ha caricato un provider di dati con supporto per mani articolate.

```c#
bool supportsArticulatedHands = false;

IMixedRealityCapabilityCheck capabilityCheck = CoreServices.InputSystem as IMixedRealityCapabilityCheck;
if (capabilityCheck != null)
{
    supportsArticulatedHands = capabilityCheck.CheckCapability(MixedRealityCapability.ArticulatedHand);
}
```

### <a name="spatial-awareness-capabilities"></a>Funzionalità di consapevolezza spaziale

Il sistema di riconoscimento spaziale MRTK predefinito supporta l'esecuzione di query sulle funzionalità seguenti:

| Funzionalità | Descrizione |
|---|---|
| SpatialAwarenessMesh | Mesh spaziali |
| SpatialAwarenessPlane | Piani spaziali |
| SpatialAwarenessPoint | Punti spaziali |

Questo esempio verifica se il sistema di riconoscimento spaziale ha caricato un provider di dati con supporto per le mesh spaziali.

```c#
bool supportsSpatialMesh = false;

IMixedRealityCapabilityCheck capabilityCheck = CoreServices.SpatialAwarenessSystem as IMixedRealityCapabilityCheck;
if (capabilityCheck != null)
{
    supportsSpatialMesh = capabilityCheck.CheckCapability(MixedRealityCapability.SpatialAwarenessMesh);
}
```

## <a name="see-also"></a>Vedi anche

- [Documentazione dell'API IMixedRealityCapabilityCheck](xref:Microsoft.MixedReality.Toolkit.IMixedRealityCapabilityCheck)
- [Documentazione dell'enumerazione MixedRealityCapability](xref:Microsoft.MixedReality.Toolkit.MixedRealityCapability)

---
title: DetectingPlatformCapabilities
description: Informazioni dettagliate sulle diverse funzionalità supportate da MRTK
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, funzionalità,
ms.openlocfilehash: 62e03c6d47deb079d3460759b5c694dd258a7767
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2021
ms.locfileid: "104691988"
---
# <a name="detecting-platform-capabilities"></a>Rilevamento delle funzionalità della piattaforma

Una domanda comune di MRTK prevede la conoscenza del dispositivo specifico (ad esempio, Microsoft HoloLens 2) usato per eseguire un'applicazione. Identificare l'hardware esatto può risultare complesso su piattaforme diverse. Al contrario, MRTK fornisce un modo per identificare funzionalità specifiche in fase di esecuzione, ad esempio se l'endpoint del dispositivo corrente supporta le mani articolate.

## <a name="capabilities"></a>Funzionalità

Il Toolkit di realtà mista fornisce l' [`MixedRealityCapability`](xref:Microsoft.MixedReality.Toolkit.MixedRealityCapability) enumerazione, che definisce un set di funzionalità per le quali un'applicazione può eseguire query in fase di esecuzione.

### <a name="input-system-capabilities"></a>Funzionalità del sistema di input

Il sistema di input MRTK predefinito supporta l'esecuzione di query sulle funzionalità seguenti:

| Funzionalità | Descrizione |
|---|---|
| ArticulatedHand | Input della mano articolata |
| EyeTracking | Targeting degli occhi |
| GGVHand | Sguardo-movimento-input della mano vocale |
| MotionController | Input del controller di movimento |
| VoiceCommand | Comandi vocali che usano parole chiave definite dall'app |
| VoiceDictation | Dettatura da voce a testo |

Il codice di esempio seguente controlla se il sistema di input ha caricato un provider di dati con supporto per le mani articolate.

```c#
bool supportsArticulatedHands = false;

IMixedRealityCapabilityCheck capabilityCheck = CoreServices.InputSystem as IMixedRealityCapabilityCheck;
if (capabilityCheck != null)
{
    supportsArticulatedHands = capabilityCheck.CheckCapability(MixedRealityCapability.ArticulatedHand);
}
```

### <a name="spatial-awareness-capabilities"></a>Funzionalità di riconoscimento spaziale

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
- [Documentazione di enumerazione MixedRealityCapability](xref:Microsoft.MixedReality.Toolkit.MixedRealityCapability)

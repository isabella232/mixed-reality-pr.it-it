---
title: Abitare
description: Interazione dwell
author: cre8ivepark
ms.author: dongpark
ms.date: 05/20/2021
keywords: Dwell, Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK
monikerRange: '>= mrtkunity-2021-05'
ms.openlocfilehash: 8ac63ee723cdd524ee7abbad7fd2658b446156adbd5ddee06ae1795edb3b68d1
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115226910"
---
# <a name="dwell"></a>Abitare

![Dwell Hero](../images/dwell/MRTK_UX_Dwell.png)

Lo sguardo alla testa e l'insodamento sono ottimi negli scenari in cui le mani di una persona sono occupate con altre attività. La funzionalità è utile anche quando la voce non è affidabile al 100% o disponibile a causa di vincoli ambientali o sociali.
Gli esempi dwell di MRTK illustrano diversi tipi di componenti dell'interfaccia utente con tempo di risposta configurabile e feedback visivo.

Per le raccomandazioni di progettazione, vedere la pagina delle [linee guida head-gaze and dwell.](/windows/mixed-reality/design/gaze-and-dwell-head)

## <a name="dwell-scripts"></a>Script di dwell

- **DwellHandler:** aggiunge una modalità di inattività alla destinazione dell'interfaccia utente.
- **DwellStateType:** stati del gestore di dwell.
- **DwellUnityEvent:** evento Unity per un evento dwell. Contiene il riferimento al puntatore.
- **BaseDwellPressableButton.cs:** script che attiva l'evento OnClick() nei `Interactable` prefab PressableButtonHoloLens2.
- **ToggleDwellPressableButton.cs:** questo script modifica la proprietà dell'oggetto `_BorderWidth` `dwellVisualImage` che usa MRTK Standard Shader.

## <a name="dwell-profiles"></a>Profili di dwell
I profili di dwell vengono usati dal **gestore Dwell** per configurare le varie soglie.
- **ButtonDwellProfile.asset**
- **InstandDwellProfile.asset**
- **DwellProfileWithDecay.asset**

## <a name="prefabs"></a>Prefab

Questi prefab sono varianti dei prefab HoloLens 2 pulsanti stampabili in stile stile che hanno componenti aggiuntivi per supportare le interazioni di sospensione.

- **PressableButtonHoloLens2_Dwell.prefab**
- **PressableButtonHoloLens2_32x96_Dwell.prefab**
- **PressableButtonHoloLens2ToggleDwell.prefab**
- **PressableButtonHoloLens2Toggle_32x96_Dwell.prefab**

Questi prefab hanno un componente backplate aggiuntivo **QuadDwellVisual** per visualizzare lo stato di input della sospensione. È stato **assegnato il materiale HolographicBackPlateDwellVisual.mat.** **ToggleDwellPressableButton.cs** aggiorna la **proprietà _BorderWidth** dello shader STANDARD MRTK per visualizzare l'input di dwell.

<img src="../images/dwell/MRTK_UX_Dwell_Prefabs_Structure.png" alt="Dwell prefabs structure" width="550px">
<img src="../images/dwell/MRTK_UX_Dwell_Prefabs.png" alt="Dwell prefabs" width="350px">

## <a name="example-scene"></a>Scena di esempio

È possibile trovare esempi nella `DwellExample` scena. La scena di esempio mostra sia esempi di interfaccia utente volumetrici che esempi di interfaccia utente unity.

<img src="../images/dwell/MRTK_UX_Dwell_Examples.png" alt="Near Menu Example">

## <a name="see-also"></a>Vedi anche

- [**Pulsanti**](button.md)
- [**Interagibile**](interactable.md)

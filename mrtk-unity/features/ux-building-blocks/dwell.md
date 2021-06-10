---
title: Abitare
description: Interazione con l'ora
author: cre8ivepark
ms.author: dongpark
ms.date: 05/20/2021
keywords: Dwell, Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK
monikerRange: '>= mrtkunity-2021-05'
ms.openlocfilehash: 18e69f001c8989234d1b75fb713796f079cacbdf
ms.sourcegitcommit: a5afc24a4887880e394ef57216b8fd9de9760004
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/28/2021
ms.locfileid: "110647800"
---
# <a name="dwell"></a>Abitare

![Dwell hero](../images/dwell/MRTK_UX_Dwell.png)

Il sguardo fisso e l'sguardo fisso sono ottimi negli scenari in cui le mani di una persona sono occupate da altre attività. Questa funzionalità è utile anche quando la voce non è affidabile al 100% o disponibile a causa di vincoli ambientali o sociali.
Gli esempi di dwell di MRTK illustrano diversi tipi di componenti dell'interfaccia utente con tempi di risposta configurabili e feedback visivo.

Per le [raccomandazioni di progettazione,](/windows/mixed-reality/design/gaze-and-dwell-head) vedere la pagina delle linee guida per lo sguardo fisso e l'sguardo fisso.

## <a name="dwell-scripts"></a>Script di dwell

- **DwellHandler:** aggiunge una modalità di inattività alla destinazione dell'interfaccia utente.
- **DwellStateType:** stati del gestore di dwell.
- **DwellUnityEvent:** evento Unity per un evento di dwell. Contiene il riferimento al puntatore.
- **BaseDwellPressableButton.cs:** script che attiva l'evento OnClick() nei `Interactable` prefab PressableButtonHoloLens2.
- **ToggleDwellPressableButton.cs:** questo script modifica la proprietà di `_BorderWidth` che usa lo shader standard `dwellVisualImage` MRTK.

## <a name="dwell-profiles"></a>Profili di dwell
I profili di memoria vengono usati dal **gestore di memoria per** configurare le varie soglie.
- **ButtonDwellProfile.asset**
- **InstandDwellProfile.asset**
- **DwellProfileWithDecay.asset**

## <a name="prefabs"></a>Prefab

Questi prefab sono varianti dei prefab HoloLens 2 prefab di pulsanti pre-stampabili in stile stile che dispongono di componenti aggiuntivi per supportare le interazioni di sospensione.

- **PressableButtonHoloLens2_Dwell.prefab**
- **PressableButtonHoloLens2_32x96_Dwell.prefab**
- **PressableButtonHoloLens2ToggleDwell.prefab**
- **PressableButtonHoloLens2Toggle_32x96_Dwell.prefab**

Questi prefab hanno un componente backplate aggiuntivo **QuadDwellVisual** per visualizzare lo stato di input dell'intervallo di tempo. Ha un **materiale HolographicBackPlateDwellVisual.mat** assegnato. **ToggleDwellPressableButton.cs** aggiorna la **proprietà _BorderWidth** dello shader MRTK Standard per visualizzare l'input di dwell.

<img src="../images/dwell/MRTK_UX_Dwell_Prefabs_Structure.png" alt="Dwell prefabs structure" width="550px">
<img src="../images/dwell/MRTK_UX_Dwell_Prefabs.png" alt="Dwell prefabs" width="350px">

## <a name="example-scene"></a>Scena di esempio

È possibile trovare esempi nella `DwellExample` scena. La scena di esempio mostra sia esempi di interfaccia utente volumetrici che esempi di interfaccia utente unity.

<img src="../images/dwell/MRTK_UX_Dwell_Examples.png" alt="Near Menu Example">

## <a name="see-also"></a>Vedi anche

- [**Pulsanti**](button.md)
- [**Con interazione**](interactable.md)

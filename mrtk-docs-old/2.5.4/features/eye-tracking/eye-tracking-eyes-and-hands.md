---
title: EyeTracking_EyesAndHands
description: Come usare il targeting oculare come puntatore primario in combinazione con i movimenti della mano in MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, EyeTracking,
ms.openlocfilehash: d2bc65f3fb26c0df6985f83ee4cecdaa94bb5ff9bca62a7c3c863faf4a5c5d07
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115212723"
---
# <a name="eyes--hand-interaction"></a>Occhi e interazione con la mano

## <a name="how-to-support-_look--hand-motions_-eye-gaze--hand-gestures"></a>Come supportare _l'aspetto e i movimenti della mano_ (& movimenti della mano)

Questa pagina illustra come usare il targeting oculare come puntatore primario in combinazione con i movimenti della mano.
Nelle demo sul tracciamento oculare [MRTK](eye-tracking-examples-overview.md)vengono descritti diversi esempi per l'uso di occhi e mani, ad esempio:

- [Selezione:](eye-tracking-target-selection.md)osservando il pulsante olografico distante e semplicemente eseguendo un movimento di avvicinamento delle dita per selezionarlo rapidamente.
- [Posizionamento:](eye-tracking-positioning.md)spostare fluentemente un ologramma sulla scena semplicemente osservandolo, avvicinando le dita e il pollice dell'indice per afferrarlo e quindi spostarlo con la mano.
- [Navigazione:](eye-tracking-navigation.md)è sufficiente esaminare una posizione in cui si vuole  eseguire lo zoom avanti, avvicinare le dita e il pollice dell'indice e avvicinare la mano per ingrandire.

Si noti che MRTK è attualmente progettato in modo che i raggi della mano a distanza fungono da puntatori di messa a fuoco con priorità.
Ciò significa che i puntatori della testa e dello sguardo oculare vengono automaticamente eliminati quando viene rilevata una mano e diventano nuovamente visibili dopo aver detto "Seleziona".
Tuttavia, questo potrebbe non essere il modo in cui si vuole interagire a distanza e preferire una semplice interazione _di "sguardo_ e commit" indipendentemente dalla presenza di mani nella visualizzazione.

### <a name="how-to-disable-the-hand-ray"></a>Come disabilitare il raggio della mano

Per disabilitare il puntatore a raggi della mano, è sufficiente rimuovere _"DefaultControllerPointer"_ nell'impostazione di configurazione _Input -> Pointer_ MRTK.
Per usare gli occhi e le mani come descritto in precedenza nell'app, assicurarsi anche di soddisfare tutti i requisiti per [l'uso del tracciamento oculare.](eye-tracking-basic-setup.md)

![Come rimuovere il raggio della mano](../images/eye-tracking/mrtk_setup_removehandray.jpg)

È anche possibile verificare come il profilo di input _EyeTrackingDemoPointerProfile_ del pacchetto di esempio di tracciamento oculare sia configurato come riferimento.

### <a name="how-to-keep-gaze-pointer-always-on"></a>Come mantenere sempre l'indicatore di misura dello sguardo

Per evitare che i puntatori della testa o dello sguardo oculare siano automaticamente soppressi quando viene rilevata una mano, è possibile specificare lo sguardo per controllare se deve essere attivata [`PointerBehavior`](xref:Microsoft.MixedReality.Toolkit.Input.PointerBehavior) o disattivata.

```c#
// Turn on gaze pointer
PointerUtils.SetGazePointerBehavior(PointerBehavior.AlwaysOn);
```

Vedere [`Controllers Pointers and Focus`](../../architecture/controllers-pointers-and-focus.md)

---
[Tornare a "Tracciamento oculare in MixedRealityToolkit"](eye-tracking-main.md)

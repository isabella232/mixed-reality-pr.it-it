---
title: EyeTracking_EyesAndHands
description: Come usare la destinazione degli occhi come puntatore principale in combinazione con i movimenti della mano in MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, EyeTracking,
ms.openlocfilehash: dcd6f373fc10c7510ca2b18ccc41192f39c9ccba
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2021
ms.locfileid: "104687291"
---
# <a name="eyes--hand-interaction"></a>Interazione tra occhi e mano

## <a name="how-to-support-_look--hand-motions_-eye-gaze--hand-gestures"></a>Come supportare i _movimenti di aspetto e mano_ (sguardi a occhio & movimenti della mano)

Questa pagina illustra come usare la destinazione degli occhi come puntatore principale in combinazione con i movimenti della mano.
Nelle [demo di MRTK Eye Tracking](EyeTracking_ExamplesOverview.md)sono descritti diversi esempi per l'uso di Eyes + Hands, ad esempio:

- [Selezione](EyeTracking_TargetSelection.md): visualizzazione di un pulsante olografico distante e semplice esecuzione di un gesto di pizzico per selezionarlo rapidamente.
- [Posizionamento](EyeTracking_Positioning.md): spostare in modo scorrevole un ologramma nella scena semplicemente cercandolo, pizzicando il dito dell'indice e il pollice insieme per spostarlo e spostarlo in un secondo momento.
- [Navigazione](EyeTracking_Navigation.md): è sufficiente esaminare la posizione in cui si vuole eseguire lo zoom, pizzicare il dito dell'indice e il pollice insieme e _tirare_ la mano verso lo zoom avanti.

Si noti che MRTK è attualmente progettato in modo che i raggi a distanza agiscono da puntatori di interesse con priorità.
Ciò significa che i puntatori Head e Eye sguardi verranno eliminati automaticamente dopo che è stata rilevata una mano, che diventerà nuovamente visibile dopo aver detto "Select".
Tuttavia, questo potrebbe non essere il modo in cui si vuole interagire a distanza e prediligendo una semplice interazione _"sguardo e commit"_ indipendente dalla presenza di mani nella visualizzazione.

### <a name="how-to-disable-the-hand-ray"></a>Come disabilitare il raggio della mano

Per disabilitare il puntatore del raggio di mano, è sufficiente rimuovere _"DefaultControllerPointer"_ nell'impostazione di configurazione MRTK di _input-> Pointer_ .
Per usare gli occhi e le mani come descritto in precedenza nell'app, assicurarsi di soddisfare tutti i [requisiti per l'uso di Eye Tracking](EyeTracking_BasicSetup.md).

![Come rimuovere il raggio della mano](../images/eye-tracking/mrtk_setup_removehandray.jpg)

È anche possibile consultare la pagina relativa alla configurazione del profilo di input _EyeTrackingDemoPointerProfile_ dal pacchetto di esempio Eye Tracking come riferimento.

### <a name="how-to-keep-gaze-pointer-always-on"></a>Come osservare il puntatore sempre attivo

Per evitare che i puntatori della testa o degli occhi vengano eliminati automaticamente quando viene rilevata una mano, è [`PointerBehavior`](xref:Microsoft.MixedReality.Toolkit.Input.PointerBehavior) possibile specificare lo sguardo per controllare se deve essere acceso o disattivato.

```c#
// Turn on gaze pointer
PointerUtils.SetGazePointerBehavior(PointerBehavior.AlwaysOn);
```

Vedere [`Controllers Pointers and Focus`](../../architecture/ControllersPointersAndFocus.md)

---
[Torna a "Eye Tracking in the MixedRealityToolkit"](EyeTracking_Main.md)

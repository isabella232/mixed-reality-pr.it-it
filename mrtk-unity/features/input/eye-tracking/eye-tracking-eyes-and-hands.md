---
title: Occhi e mani
description: Come usare il targeting oculare come puntatore principale in combinazione con i movimenti della mano in MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, EyeTracking,
ms.openlocfilehash: ff464c6f2381a9df020a9ccf807672d4463d662c
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2021
ms.locfileid: "113175117"
---
# <a name="eyes-and-hands"></a>Occhi e mani

## <a name="how-to-support-_look--hand-motions_-eye-gaze--hand-gestures"></a>Come supportare _l'aspetto e i movimenti della mano_ (sguardo fisso & movimenti della mano)

Questa pagina illustra come usare il targeting oculare come puntatore principale in combinazione con i movimenti della mano.
Nelle demo [sul tracciamento oculare di MRTK](../../example-scenes/eye-tracking-examples-overview.md)vengono descritti diversi esempi per l'uso di occhi e mani, ad esempio:

- [Selezione:](eye-tracking-target-selection.md)è possibile guardare un pulsante olografico distante ed eseguire semplicemente un movimento di avvicinamento delle dita per selezionarlo rapidamente.
- **Posizionamento (questo articolo):** spostare fluently un ologramma sulla scena semplicemente osservandolo, avvicinando le dita e il pollice dell'indice per afferrarlo e quindi spostarlo con la mano.
- [Navigazione:](eye-tracking-navigation.md)è sufficiente esaminare una posizione in cui si vuole  eseguire lo zoom avanti, avvicinare le dita e il pollice dell'indice e avvicinare la mano per fare zoom avanti.

Si noti che MRTK è attualmente progettato in modo che i raggi della mano a distanza fungono da puntatori di messa a fuoco classificati in ordine di priorità.
Ciò significa che i puntatori della testa e dello sguardo fisso verranno automaticamente soppressi quando viene rilevata una mano e diventeranno nuovamente visibili dopo aver detto "Seleziona".
Tuttavia, questo potrebbe non essere il modo in cui si vuole interagire a una distanza e preferire una semplice interazione "sguardo fisso e _commit"_ indipendente dalla presenza di mani nella visualizzazione.

### <a name="how-to-disable-the-hand-ray"></a>Come disabilitare il raggio della mano

Per disabilitare l'indicatore di misura del raggio della mano, è sufficiente rimuovere _"DefaultControllerPointer"_ nell'impostazione di configurazione _Input -> pointer_ MRTK.
Per usare occhi e mani come descritto in precedenza nell'app, assicurarsi anche di soddisfare tutti i requisiti per [l'uso del tracciamento oculare.](eye-tracking-basic-setup.md)

![Come rimuovere il raggio della mano](../../images/eye-tracking/mrtk_setup_removehandray.jpg)

È anche possibile verificare come il profilo di input _EyeTrackingDemoPointerProfile_ del pacchetto di esempio di tracciamento oculare sia configurato come riferimento.

### <a name="how-to-keep-gaze-pointer-always-on"></a>Come mantenere sempre l'indicatore di misura dello sguardo fisso

Per evitare che i puntatori con la testa o lo sguardo fisso siano soppressi automaticamente una volta rilevata una mano, è possibile specificare lo sguardo fisso per controllare se deve essere [`PointerBehavior`](xref:Microsoft.MixedReality.Toolkit.Input.PointerBehavior) attivata o disattivata.

```c#
// Turn on gaze pointer
PointerUtils.SetGazePointerBehavior(PointerBehavior.AlwaysOn);
```

Vedere [`Controllers Pointers and Focus`](../../../architecture/controllers-pointers-and-focus.md)

---
[Torna a "Tracciamento oculare in MixedRealityToolkit"](eye-tracking-main.md)

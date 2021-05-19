---
title: Tracciamento oculare di occhi e mani
description: Come usare il targeting oculare come puntatore principale in combinazione con i movimenti della mano in MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, EyeTracking,
ms.openlocfilehash: c9d5f23610d821aa1e50a3217a4be736601dc14d
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143995"
---
# <a name="eyes--hand-interaction"></a><span data-ttu-id="3df71-104">Occhi e interazione con la mano</span><span class="sxs-lookup"><span data-stu-id="3df71-104">Eyes + hand interaction</span></span>

## <a name="how-to-support-_look--hand-motions_-eye-gaze--hand-gestures"></a><span data-ttu-id="3df71-105">Come supportare _l'aspetto e i movimenti della mano_ (sguardo fisso & movimenti della mano)</span><span class="sxs-lookup"><span data-stu-id="3df71-105">How to support _look + hand motions_ (eye gaze & hand gestures)</span></span>

<span data-ttu-id="3df71-106">Questa pagina illustra come usare il targeting oculare come puntatore principale in combinazione con i movimenti della mano.</span><span class="sxs-lookup"><span data-stu-id="3df71-106">This page explains how to use eye targeting as a primary pointer in combination with hand motions.</span></span>
<span data-ttu-id="3df71-107">Nelle demo [sul tracciamento oculare di MRTK](../../example-scenes/eye-tracking-examples-overview.md)vengono descritti diversi esempi per l'uso di occhi e mani, ad esempio:</span><span class="sxs-lookup"><span data-stu-id="3df71-107">In our [MRTK eye tracking demos](../../example-scenes/eye-tracking-examples-overview.md), we describe several examples for using eyes + hands, for example:</span></span>

- <span data-ttu-id="3df71-108">[Selezione:](eye-tracking-target-selection.md)è possibile guardare un pulsante olografico distante ed eseguire semplicemente un movimento di avvicinamento delle dita per selezionarlo rapidamente.</span><span class="sxs-lookup"><span data-stu-id="3df71-108">[Selection](eye-tracking-target-selection.md): Looking at distant holographic button and simply performing a pinch gesture to quickly select it.</span></span>
- <span data-ttu-id="3df71-109">**Posizionamento (questo articolo):** spostare fluently un ologramma sulla scena semplicemente osservandolo, avvicinando le dita e il pollice dell'indice per afferrarlo e quindi spostarlo con la mano.</span><span class="sxs-lookup"><span data-stu-id="3df71-109">**Positioning (this article)**: Fluently move a hologram across your scene by simply looking at it, pinching your index finger and thumb together to grab it and then move it around using your hand.</span></span>
- <span data-ttu-id="3df71-110">[Navigazione:](eye-tracking-navigation.md)è sufficiente esaminare una posizione in cui si vuole  eseguire lo zoom avanti, avvicinare le dita e il pollice dell'indice e avvicinare la mano per fare zoom avanti.</span><span class="sxs-lookup"><span data-stu-id="3df71-110">[Navigation](eye-tracking-navigation.md): Simply look at a location you want to zoom in, pinch your index finger and thumb together and _pull_ your hand toward you to zoom in.</span></span>

<span data-ttu-id="3df71-111">Si noti che MRTK è attualmente progettato in modo che i raggi della mano a distanza fungono da puntatori di messa a fuoco classificati in ordine di priorità.</span><span class="sxs-lookup"><span data-stu-id="3df71-111">Please note that MRTK is currently designed in a way that at a distance hand rays act as the prioritized focus pointers.</span></span>
<span data-ttu-id="3df71-112">Ciò significa che i puntatori della testa e dello sguardo fisso verranno automaticamente soppressi quando viene rilevata una mano e diventeranno nuovamente visibili dopo aver detto "Seleziona".</span><span class="sxs-lookup"><span data-stu-id="3df71-112">This means that the head and eye gaze pointers will automatically be suppressed once a hand is detected and will become visible again after saying "Select".</span></span>
<span data-ttu-id="3df71-113">Tuttavia, questo potrebbe non essere il modo in cui si vuole interagire a una distanza e preferire una semplice interazione "sguardo fisso e _commit"_ indipendente dalla presenza di mani nella visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="3df71-113">However, this may not be the way you would like to interact at a distance and rather favor a simple _'gaze and commit'_ interaction independent of the presence of hands in your view.</span></span>

### <a name="how-to-disable-the-hand-ray"></a><span data-ttu-id="3df71-114">Come disabilitare il raggio della mano</span><span class="sxs-lookup"><span data-stu-id="3df71-114">How to disable the hand ray</span></span>

<span data-ttu-id="3df71-115">Per disabilitare l'indicatore di misura del raggio della mano, è sufficiente rimuovere _"DefaultControllerPointer"_ nell'impostazione di configurazione _Input -> POINTER_ MRTK.</span><span class="sxs-lookup"><span data-stu-id="3df71-115">To disable the hand ray pointer, simply remove the _'DefaultControllerPointer'_ in your _Input -> Pointer_ MRTK configuration setting.</span></span>
<span data-ttu-id="3df71-116">Per usare occhi e mani come descritto in precedenza nell'app, assicurarsi anche di soddisfare tutti i requisiti per [l'uso del tracciamento oculare.](eye-tracking-basic-setup.md)</span><span class="sxs-lookup"><span data-stu-id="3df71-116">To use eyes and hands as described above in your app, please also make sure that you meet all of the [requirements for using eye tracking](eye-tracking-basic-setup.md).</span></span>

![Come rimuovere il raggio della mano](../../images/eye-tracking/mrtk_setup_removehandray.jpg)

<span data-ttu-id="3df71-118">È anche possibile verificare come il profilo di input _EyeTrackingDemoPointerProfile_ del pacchetto di esempio di tracciamento oculare sia configurato come riferimento.</span><span class="sxs-lookup"><span data-stu-id="3df71-118">You can also check out, how the input profile _EyeTrackingDemoPointerProfile_ from the eye tracking sample package is set up as a reference.</span></span>

### <a name="how-to-keep-gaze-pointer-always-on"></a><span data-ttu-id="3df71-119">Come mantenere sempre l'indicatore di misura dello sguardo fisso</span><span class="sxs-lookup"><span data-stu-id="3df71-119">How to keep gaze pointer always on</span></span>

<span data-ttu-id="3df71-120">Per evitare che i puntatori della testa o dello sguardo oculare siano automaticamente soppressi quando viene rilevata una mano, è possibile specificare lo sguardo per controllare se deve essere attivata [`PointerBehavior`](xref:Microsoft.MixedReality.Toolkit.Input.PointerBehavior) o disattivata.</span><span class="sxs-lookup"><span data-stu-id="3df71-120">To avoid having the head or eye gaze pointers automatically suppressed once a hand is detected, the gaze [`PointerBehavior`](xref:Microsoft.MixedReality.Toolkit.Input.PointerBehavior) can be specified to control whether it should be on or off.</span></span>

```c#
// Turn on gaze pointer
PointerUtils.SetGazePointerBehavior(PointerBehavior.AlwaysOn);
```

<span data-ttu-id="3df71-121">Vedere [`Controllers Pointers and Focus`](../../../architecture/controllers-pointers-and-focus.md)</span><span class="sxs-lookup"><span data-stu-id="3df71-121">See [`Controllers Pointers and Focus`](../../../architecture/controllers-pointers-and-focus.md)</span></span>

---
[<span data-ttu-id="3df71-122">Tornare a "Tracciamento oculare in MixedRealityToolkit"</span><span class="sxs-lookup"><span data-stu-id="3df71-122">Back to "Eye tracking in the MixedRealityToolkit"</span></span>](eye-tracking-main.md)

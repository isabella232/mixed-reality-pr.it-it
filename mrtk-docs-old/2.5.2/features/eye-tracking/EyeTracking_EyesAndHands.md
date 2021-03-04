---
title: EyeTracking_EyesAndHands
description: Come usare la destinazione degli occhi come puntatore principale in combinazione con i movimenti della mano in MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, EyeTracking,
ms.openlocfilehash: 75ca0289dcac86dc68043c4deceaea2b85e2a236
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/03/2021
ms.locfileid: "101783288"
---
# <a name="eyes--hand-interaction"></a><span data-ttu-id="027e9-104">Interazione tra occhi e mano</span><span class="sxs-lookup"><span data-stu-id="027e9-104">Eyes + hand interaction</span></span>

## <a name="how-to-support-_look--hand-motions_-eye-gaze--hand-gestures"></a><span data-ttu-id="027e9-105">Come supportare i _movimenti di aspetto e mano_ (sguardi a occhio & movimenti della mano)</span><span class="sxs-lookup"><span data-stu-id="027e9-105">How to support _look + hand motions_ (eye gaze & hand gestures)</span></span>

<span data-ttu-id="027e9-106">Questa pagina illustra come usare la destinazione degli occhi come puntatore principale in combinazione con i movimenti della mano.</span><span class="sxs-lookup"><span data-stu-id="027e9-106">This page explains how to use eye targeting as a primary pointer in combination with hand motions.</span></span>
<span data-ttu-id="027e9-107">Nelle [demo di MRTK Eye Tracking](EyeTracking_ExamplesOverview.md)sono descritti diversi esempi per l'uso di Eyes + Hands, ad esempio:</span><span class="sxs-lookup"><span data-stu-id="027e9-107">In our [MRTK eye tracking demos](EyeTracking_ExamplesOverview.md), we describe several examples for using eyes + hands, for example:</span></span>

- <span data-ttu-id="027e9-108">[Selezione](EyeTracking_TargetSelection.md): visualizzazione di un pulsante olografico distante e semplice esecuzione di un gesto di pizzico per selezionarlo rapidamente.</span><span class="sxs-lookup"><span data-stu-id="027e9-108">[Selection](EyeTracking_TargetSelection.md): Looking at distant holographic button and simply performing a pinch gesture to quickly select it.</span></span>
- <span data-ttu-id="027e9-109">[Posizionamento](EyeTracking_Positioning.md): spostare in modo scorrevole un ologramma nella scena semplicemente cercandolo, pizzicando il dito dell'indice e il pollice insieme per spostarlo e spostarlo in un secondo momento.</span><span class="sxs-lookup"><span data-stu-id="027e9-109">[Positioning](EyeTracking_Positioning.md): Fluently move a hologram across your scene by simply looking at it, pinching your index finger and thumb together to grab it and then move it around using your hand.</span></span>
- <span data-ttu-id="027e9-110">[Navigazione](EyeTracking_Navigation.md): è sufficiente esaminare la posizione in cui si vuole eseguire lo zoom, pizzicare il dito dell'indice e il pollice insieme e _tirare_ la mano verso lo zoom avanti.</span><span class="sxs-lookup"><span data-stu-id="027e9-110">[Navigation](EyeTracking_Navigation.md): Simply look at a location you want to zoom in, pinch your index finger and thumb together and _pull_ your hand toward you to zoom in.</span></span>

<span data-ttu-id="027e9-111">Si noti che MRTK è attualmente progettato in modo che i raggi a distanza agiscono da puntatori di interesse con priorità.</span><span class="sxs-lookup"><span data-stu-id="027e9-111">Please note that MRTK is currently designed in a way that at a distance hand rays act as the prioritized focus pointers.</span></span>
<span data-ttu-id="027e9-112">Ciò significa che i puntatori Head e Eye sguardi verranno eliminati automaticamente dopo che è stata rilevata una mano, che diventerà nuovamente visibile dopo aver detto "Select".</span><span class="sxs-lookup"><span data-stu-id="027e9-112">This means that the head and eye gaze pointers will automatically be suppressed once a hand is detected and will become visible again after saying "Select".</span></span>
<span data-ttu-id="027e9-113">Tuttavia, questo potrebbe non essere il modo in cui si vuole interagire a distanza e prediligendo una semplice interazione _"sguardo e commit"_ indipendente dalla presenza di mani nella visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="027e9-113">However, this may not be the way you would like to interact at a distance and rather favor a simple _'gaze and commit'_ interaction independent of the presence of hands in your view.</span></span>

### <a name="how-to-disable-the-hand-ray"></a><span data-ttu-id="027e9-114">Come disabilitare il raggio della mano</span><span class="sxs-lookup"><span data-stu-id="027e9-114">How to disable the hand ray</span></span>

<span data-ttu-id="027e9-115">Per disabilitare il puntatore del raggio di mano, è sufficiente rimuovere _"DefaultControllerPointer"_ nell'impostazione di configurazione MRTK di _input-> Pointer_ .</span><span class="sxs-lookup"><span data-stu-id="027e9-115">To disable the hand ray pointer, simply remove the _'DefaultControllerPointer'_ in your _Input -> Pointer_ MRTK configuration setting.</span></span>
<span data-ttu-id="027e9-116">Per usare gli occhi e le mani come descritto in precedenza nell'app, assicurarsi di soddisfare tutti i [requisiti per l'uso di Eye Tracking](EyeTracking_BasicSetup.md).</span><span class="sxs-lookup"><span data-stu-id="027e9-116">To use eyes and hands as described above in your app, please also make sure that you meet all of the [requirements for using eye tracking](EyeTracking_BasicSetup.md).</span></span>

![Come rimuovere il raggio della mano](../images/eye-tracking/mrtk_setup_removehandray.jpg)

<span data-ttu-id="027e9-118">È anche possibile consultare la pagina relativa alla configurazione del profilo di input _EyeTrackingDemoPointerProfile_ dal pacchetto di esempio Eye Tracking come riferimento.</span><span class="sxs-lookup"><span data-stu-id="027e9-118">You can also check out, how the input profile _EyeTrackingDemoPointerProfile_ from the eye tracking sample package is set up as a reference.</span></span>

### <a name="how-to-keep-gaze-pointer-always-on"></a><span data-ttu-id="027e9-119">Come osservare il puntatore sempre attivo</span><span class="sxs-lookup"><span data-stu-id="027e9-119">How to keep gaze pointer always on</span></span>

<span data-ttu-id="027e9-120">Per evitare che i puntatori della testa o degli occhi vengano eliminati automaticamente quando viene rilevata una mano, è [`PointerBehavior`](xref:Microsoft.MixedReality.Toolkit.Input.PointerBehavior) possibile specificare lo sguardo per controllare se deve essere acceso o disattivato.</span><span class="sxs-lookup"><span data-stu-id="027e9-120">To avoid having the head or eye gaze pointers automatically suppressed once a hand is detected, the gaze [`PointerBehavior`](xref:Microsoft.MixedReality.Toolkit.Input.PointerBehavior) can be specified to control whether it should be on or off.</span></span>

```c#
// Turn on gaze pointer
PointerUtils.SetGazePointerBehavior(PointerBehavior.AlwaysOn);
```

<span data-ttu-id="027e9-121">Vedere [`Controllers Pointers and Focus`](../../architecture/ControllersPointersAndFocus.md)</span><span class="sxs-lookup"><span data-stu-id="027e9-121">See [`Controllers Pointers and Focus`](../../architecture/ControllersPointersAndFocus.md)</span></span>

---
[<span data-ttu-id="027e9-122">Torna a "Eye Tracking in the MixedRealityToolkit"</span><span class="sxs-lookup"><span data-stu-id="027e9-122">Back to "Eye tracking in the MixedRealityToolkit"</span></span>](EyeTracking_Main.md)

---
title: Dispositivi di scorrimento
description: Panoramica dei dispositivi di scorrimento MRTK
author: RogPodge
ms.author: roliu
ms.date: 06/18/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, dispositivi di scorrimento,
ms.openlocfilehash: c8a2b6c377762918bfff79008ab34d3dfe4e20bb
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177502"
---
# <a name="sliders"></a><span data-ttu-id="1a8eb-104">Dispositivi di scorrimento</span><span class="sxs-lookup"><span data-stu-id="1a8eb-104">Sliders</span></span>

![Esempio di dispositivo di scorrimento](../images/slider/MRTK_UX_Slider_Main.jpg)

<span data-ttu-id="1a8eb-106">I dispositivi di scorrimento sono componenti dell'interfaccia utente che consentono di modificare continuamente un valore spostando un dispositivo di scorrimento su una traccia. Attualmente il dispositivo di scorrimento avvicinamento delle dita può essere spostato afferrando direttamente il dispositivo di scorrimento, direttamente o a distanza.</span><span class="sxs-lookup"><span data-stu-id="1a8eb-106">Sliders are UI components that allow you to continuously change a value by moving a slider on a track. Currently the Pinch Slider can be moved by directly grabbing the slider, either directly or at a distance.</span></span> <span data-ttu-id="1a8eb-107">I dispositivi di scorrimento funzionano in AR e VR, usando controller del movimento, mani o movimenti + voce.</span><span class="sxs-lookup"><span data-stu-id="1a8eb-107">Sliders work on AR and VR, using motion controllers, hands, or Gesture + Voice.</span></span>

## <a name="example-scene"></a><span data-ttu-id="1a8eb-108">Scena di esempio</span><span class="sxs-lookup"><span data-stu-id="1a8eb-108">Example scene</span></span>

<span data-ttu-id="1a8eb-109">È possibile trovare esempi nella scena **SliderExample** in `MRTK/Examples/Demos/UX/Slider/Scenes/` .</span><span class="sxs-lookup"><span data-stu-id="1a8eb-109">You can find examples in the **SliderExample** scene under `MRTK/Examples/Demos/UX/Slider/Scenes/`.</span></span>

## <a name="how-to-use-sliders"></a><span data-ttu-id="1a8eb-110">Come usare i dispositivi di scorrimento</span><span class="sxs-lookup"><span data-stu-id="1a8eb-110">How to use sliders</span></span>

<span data-ttu-id="1a8eb-111">Trascinare e rilasciare il prefab **PinchSlider** nella gerarchia della scena.</span><span class="sxs-lookup"><span data-stu-id="1a8eb-111">Drag and drop the **PinchSlider** prefab into the scene hierarchy.</span></span> <span data-ttu-id="1a8eb-112">Se si vuole modificare o creare un dispositivo di scorrimento personalizzato, ricordarsi di eseguire le operazioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="1a8eb-112">If you want to modify or create your own slider, remember to do the following:</span></span>

- <span data-ttu-id="1a8eb-113">Assicurarsi che l'oggetto thumb abbia un collisore.</span><span class="sxs-lookup"><span data-stu-id="1a8eb-113">Make sure your that your thumb object has a collider on it.</span></span> <span data-ttu-id="1a8eb-114">Nel prefab PinchSlider il collisore è in `SliderThumb/Button_AnimationContainer/Slider_Button`</span><span class="sxs-lookup"><span data-stu-id="1a8eb-114">In the PinchSlider prefab, the collider is on `SliderThumb/Button_AnimationContainer/Slider_Button`</span></span>
- <span data-ttu-id="1a8eb-115">Assicurati che l'oggetto contenente il collisore abbia anche un componente Near Interaction Grabbable (Afferrabile con interazione da vicino) se vuoi essere in grado di afferrare il dispositivo di scorrimento vicino.</span><span class="sxs-lookup"><span data-stu-id="1a8eb-115">Make sure that the object containing the collider also has a Near Interaction Grabbable component on it, if you want to be able to grab the slider near.</span></span>

<span data-ttu-id="1a8eb-116">È anche consigliabile usare la gerarchia seguente</span><span class="sxs-lookup"><span data-stu-id="1a8eb-116">We also recommend using the following hierarchy</span></span>

- <span data-ttu-id="1a8eb-117">PinchSlider: contiene sliderComponent</span><span class="sxs-lookup"><span data-stu-id="1a8eb-117">PinchSlider - Contains the sliderComponent</span></span>
  - <span data-ttu-id="1a8eb-118">TouchCollider: collisore contenente l'intera area selezionabile del dispositivo di scorrimento.</span><span class="sxs-lookup"><span data-stu-id="1a8eb-118">TouchCollider - Collider containing the entire selectable area of the slider.</span></span> <span data-ttu-id="1a8eb-119">Abilita il comportamento Blocca sulla posizione.</span><span class="sxs-lookup"><span data-stu-id="1a8eb-119">Enables the Snap To Position behavior.</span></span>
  - <span data-ttu-id="1a8eb-120">SliderThumb: contiene il cursore mobile</span><span class="sxs-lookup"><span data-stu-id="1a8eb-120">SliderThumb - Contains the movable thumb</span></span>
  - <span data-ttu-id="1a8eb-121">TrackVisuals : contiene la traccia e qualsiasi altro oggetto visivo</span><span class="sxs-lookup"><span data-stu-id="1a8eb-121">TrackVisuals - Containing the track and any other visuals</span></span>
  - <span data-ttu-id="1a8eb-122">OtherVisuals - Contenente qualsiasi altro oggetto visivo</span><span class="sxs-lookup"><span data-stu-id="1a8eb-122">OtherVisuals - Containing any other visuals</span></span>

## <a name="slider-events"></a><span data-ttu-id="1a8eb-123">Eventi dispositivo di scorrimento</span><span class="sxs-lookup"><span data-stu-id="1a8eb-123">Slider events</span></span>

<span data-ttu-id="1a8eb-124">I dispositivi di scorrimento espongono gli eventi seguenti:</span><span class="sxs-lookup"><span data-stu-id="1a8eb-124">Sliders expose the following events:</span></span>

- <span data-ttu-id="1a8eb-125">OnValueUpdated: viene chiamato ogni volta che cambia il valore del dispositivo di scorrimento</span><span class="sxs-lookup"><span data-stu-id="1a8eb-125">OnValueUpdated - Called whenever the slider value changes</span></span>
- <span data-ttu-id="1a8eb-126">OnInteractionStarted: chiamata quando l'utente afferra il dispositivo di scorrimento</span><span class="sxs-lookup"><span data-stu-id="1a8eb-126">OnInteractionStarted - Called when the user grabs the slider</span></span>
- <span data-ttu-id="1a8eb-127">OnInteractionEnded: chiamata quando l'utente rilascia il dispositivo di scorrimento</span><span class="sxs-lookup"><span data-stu-id="1a8eb-127">OnInteractionEnded - Called when the user releases the slider</span></span>
- <span data-ttu-id="1a8eb-128">OnHoverEntered: viene chiamato quando la mano o il controller dell'utente passa il puntatore del mouse sul dispositivo di scorrimento, usando l'interazione da vicino o da lontano.</span><span class="sxs-lookup"><span data-stu-id="1a8eb-128">OnHoverEntered - Called when the user's hand / controller hovers over the slider, using either near or far interaction.</span></span>
- <span data-ttu-id="1a8eb-129">OnHoverExited: viene chiamato quando la mano/controller dell'utente non si trova più vicino al dispositivo di scorrimento.</span><span class="sxs-lookup"><span data-stu-id="1a8eb-129">OnHoverExited - Called when the user's hand / controller is no longer near the slider.</span></span>

## <a name="configuring-slider-bound-and-axis"></a><span data-ttu-id="1a8eb-130">Configurazione del limite e dell'asse del dispositivo di scorrimento</span><span class="sxs-lookup"><span data-stu-id="1a8eb-130">Configuring slider bound and axis</span></span>

<span data-ttu-id="1a8eb-131">È possibile spostare direttamente i punti iniziale e finale del dispositivo di scorrimento spostando i quadratini di ridimensionamento nella scena:</span><span class="sxs-lookup"><span data-stu-id="1a8eb-131">You can directly move the starting and end points of the slider by moving the handles in the Scene:</span></span>

![Configurazione dei dispositivi di scorrimento](../images/sliders/MRTK_Sliders_Setup.png)

<span data-ttu-id="1a8eb-133">È anche possibile specificare l'asse (nello spazio locale) del dispositivo di scorrimento tramite il campo _Asse dispositivo di_ scorrimento</span><span class="sxs-lookup"><span data-stu-id="1a8eb-133">You can also specify the axis (in local space) of the slider via the _Slider Axis_ field</span></span>

<span data-ttu-id="1a8eb-134">Se non è possibile usare i quadratini di ridimensionamento, è invece possibile specificare i punti di inizio e di fine del dispositivo di scorrimento tramite i campi _Distanza_ iniziale dispositivo di scorrimento e _Distanza fine dispositivo di scorrimento._</span><span class="sxs-lookup"><span data-stu-id="1a8eb-134">If you cannot use the handles, you can instead specify the start and end points of the slider via the _Slider Start Distance_ and _Slider End Distance_ fields.</span></span> <span data-ttu-id="1a8eb-135">Specificano la posizione iniziale/finale del dispositivo di scorrimento come distanza dal centro del dispositivo di scorrimento, in coordinate locali.</span><span class="sxs-lookup"><span data-stu-id="1a8eb-135">These specify start / end position of slider as a distance from the slider's center, in local coordinates.</span></span> <span data-ttu-id="1a8eb-136">Ciò significa che, dopo aver impostato le distanze di inizio e di fine del dispositivo di scorrimento nel modo desiderato, è possibile ridimensionare il dispositivo di scorrimento in modo che sia più piccolo o più grande senza dover aggiornare le distanze di inizio e di fine.</span><span class="sxs-lookup"><span data-stu-id="1a8eb-136">This means that once you set the slider start and end distances as you want them, you can scale the slider to be smaller or larger without needing to update the start and end distances.</span></span>

## <a name="inspector-properties"></a><span data-ttu-id="1a8eb-137">Proprietà del controllo</span><span class="sxs-lookup"><span data-stu-id="1a8eb-137">Inspector properties</span></span>

<span data-ttu-id="1a8eb-138">**Radice thumb** Gameobject che contiene il cursore del dispositivo di scorrimento.</span><span class="sxs-lookup"><span data-stu-id="1a8eb-138">**Thumb Root** The gameobject that contains the slider thumb.</span></span>

<span data-ttu-id="1a8eb-139">**Blocca sulla posizione** Indica se il dispositivo di scorrimento si blocca sulla posizione designata sul dispositivo di scorrimento</span><span class="sxs-lookup"><span data-stu-id="1a8eb-139">**Snap To Position** Whether or not this slider snaps to the designated position on the slider</span></span>

<span data-ttu-id="1a8eb-140">**È toccabile** Indica se questo dispositivo di scorrimento può essere o meno controllabile tramite eventi di tocco</span><span class="sxs-lookup"><span data-stu-id="1a8eb-140">**Is Touchable** Whether or not this slider is controllable via touch events</span></span>

<span data-ttu-id="1a8eb-141">**Collisore del pollice** Collisore che controlla il cursore del dispositivo di scorrimento</span><span class="sxs-lookup"><span data-stu-id="1a8eb-141">**Thumb Collider** The collider that controls the slider thumb</span></span>

<span data-ttu-id="1a8eb-142">**Collisore toccabile** Area del dispositivo di scorrimento che può essere toccata o selezionata quando Blocca in posizione è true.</span><span class="sxs-lookup"><span data-stu-id="1a8eb-142">**Touchable Collider** The area of the slider that can be touched or selected when Snap To Position is true.</span></span>

<span data-ttu-id="1a8eb-143">**Valore dispositivo di scorrimento** Valore del dispositivo di scorrimento.</span><span class="sxs-lookup"><span data-stu-id="1a8eb-143">**Slider Value** The value of the slider.</span></span>

<span data-ttu-id="1a8eb-144">**Usare le divisioni dei passaggi del dispositivo di scorrimento** Controlla se il dispositivo di scorrimento viene incrementato in passaggi o continuamente.</span><span class="sxs-lookup"><span data-stu-id="1a8eb-144">**Use Slider Step Divisions** Controls whether this slider is increments in steps or continuously.</span></span>

<span data-ttu-id="1a8eb-145">**Divisioni passaggio dispositivo di scorrimento** Numero di suddivisioni in cui è suddiviso il dispositivo di scorrimento quando l'opzione Usa divisioni passaggio dispositivo di scorrimento è abilitata.</span><span class="sxs-lookup"><span data-stu-id="1a8eb-145">**Slider Step Divisions** Number of subdivisions the slider is split into when Use Slider Step Divisions is enabled.</span></span>

<span data-ttu-id="1a8eb-146">**Tenere traccia degli oggetti visivi** Gameobject che contiene gli oggetti visivi traccia desiderati che si spostano lungo il dispositivo di scorrimento.</span><span class="sxs-lookup"><span data-stu-id="1a8eb-146">**Track Visuals** The gameobject that contains the desired track visuals that goes along the slider.</span></span>

<span data-ttu-id="1a8eb-147">**Segni di graduazione** Gameobject che contiene i segni di graduazione desiderati lungo il dispositivo di scorrimento.</span><span class="sxs-lookup"><span data-stu-id="1a8eb-147">**Tick Marks** The gameobject that contains the desired tick marks that goes along the slider.</span></span>

<span data-ttu-id="1a8eb-148">**Oggetti visivi Thumb** Gameobject che contiene l'oggetto visivo thumb desiderato lungo il dispositivo di scorrimento.</span><span class="sxs-lookup"><span data-stu-id="1a8eb-148">**Thumb Visuals** The gameobject that contains the desired thumb visual that goes along the slider.</span></span>

<span data-ttu-id="1a8eb-149">**Asse dispositivo di scorrimento** Asse lungo il dispositivo di scorrimento.</span><span class="sxs-lookup"><span data-stu-id="1a8eb-149">**Slider Axis** The axis the slider moves along.</span></span>

<span data-ttu-id="1a8eb-150">**Distanza iniziale dispositivo di scorrimento** Punto di inizio della traccia del dispositivo di scorrimento, come distanza dal centro lungo l'asse del dispositivo di scorrimento, in unità di spazio locali.</span><span class="sxs-lookup"><span data-stu-id="1a8eb-150">**Slider Start Distance** Where the slider track starts, as distance from center along slider axis, in local space units.</span></span>

<span data-ttu-id="1a8eb-151">**Distanza di fine dispositivo di scorrimento** Punto in cui termina la traccia del dispositivo di scorrimento, come distanza dal centro lungo l'asse del dispositivo di scorrimento, in unità di spazio locali.</span><span class="sxs-lookup"><span data-stu-id="1a8eb-151">**Slider End Distance** Where the slider track ends, as distance from center along slider axis, in local space units.</span></span>

<span data-ttu-id="1a8eb-152">Quando l'utente aggiorna il valore dell'asse del dispositivo di scorrimento nell'editor, se si specifica Track Visuals (Rileva oggetti visivi) o Tick Visuals (Oggetti visivi tick), la trasformazione viene aggiornata.</span><span class="sxs-lookup"><span data-stu-id="1a8eb-152">When user updates the slider axis value in editor then if Track Visuals or Tick Visuals are specified then their transform is updated.</span></span>
<span data-ttu-id="1a8eb-153">In particolare, la posizione locale viene reimpostata e la rotazione locale viene impostata in modo da corrispondere all'orientamento dell'asse del dispositivo di scorrimento.</span><span class="sxs-lookup"><span data-stu-id="1a8eb-153">Specifically, their local position is reset and their local rotation is set to match the Slider Axis orientation.</span></span>
<span data-ttu-id="1a8eb-154">La scalabilità non viene modificata.</span><span class="sxs-lookup"><span data-stu-id="1a8eb-154">Their scale isn't modified.</span></span>
<span data-ttu-id="1a8eb-155">Se i segni di graduazione hanno un componente Grid Object Collection, Layout e CellWidth o CellHeight vengono aggiornati di conseguenza in modo che corrispondano all'asse del dispositivo di scorrimento.</span><span class="sxs-lookup"><span data-stu-id="1a8eb-155">If Tick Marks have a Grid Object Collection component then the Layout and CellWidth or CellHeight is updated accordingly to match the Slider Axis.</span></span>

## <a name="example-slider-configurations"></a><span data-ttu-id="1a8eb-156">Esempio di configurazioni del dispositivo di scorrimento</span><span class="sxs-lookup"><span data-stu-id="1a8eb-156">Example Slider Configurations</span></span>

<span data-ttu-id="1a8eb-157">Dispositivi di scorrimento continui con blocca sulla posizione ![ Dispositivi di scorrimento continui](https://user-images.githubusercontent.com/39840334/122488212-d410a400-cf91-11eb-8d31-fc7584ddc465.gif)</span><span class="sxs-lookup"><span data-stu-id="1a8eb-157">Continuous Sliders with Snap To Position ![Continuous Sliders](https://user-images.githubusercontent.com/39840334/122488212-d410a400-cf91-11eb-8d31-fc7584ddc465.gif)</span></span>

<span data-ttu-id="1a8eb-158">Dispositivi di scorrimento passo con blocca sulla posizione</span><span class="sxs-lookup"><span data-stu-id="1a8eb-158">Step Sliders with Snap To Position</span></span>

![Dispositivi di scorrimento dei passaggi](https://user-images.githubusercontent.com/39840334/122488226-dc68df00-cf91-11eb-9459-89655bbb054d.gif)

<span data-ttu-id="1a8eb-160">Dispositivi di scorrimento tocco</span><span class="sxs-lookup"><span data-stu-id="1a8eb-160">Touch Sliders</span></span>

![Dispositivi di scorrimento tocco](https://user-images.githubusercontent.com/39840334/122488221-d8d55800-cf91-11eb-91a1-bb12debe2797.gif)

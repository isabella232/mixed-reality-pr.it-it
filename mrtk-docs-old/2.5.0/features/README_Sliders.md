---
title: README_Slider
description: Panoramica dei dispositivi di scorrimento MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, dispositivi di scorrimento,
ms.openlocfilehash: af94da6e72a6dc87adef27d6f4a055b522f68155
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2021
ms.locfileid: "104694898"
---
# <a name="sliders"></a><span data-ttu-id="99c3f-104">Dispositivi di scorrimento</span><span class="sxs-lookup"><span data-stu-id="99c3f-104">Sliders</span></span>

![Esempio di dispositivo di scorrimento](Images/Slider/MRTK_UX_Slider_Main.jpg)

<span data-ttu-id="99c3f-106">I dispositivi di scorrimento sono componenti dell'interfaccia utente che consentono di modificare continuamente un valore spostando un dispositivo di scorrimento in una traccia. Attualmente, è possibile spostare il dispositivo di scorrimento a pizzico direttamente o a distanza.</span><span class="sxs-lookup"><span data-stu-id="99c3f-106">Sliders are UI components that allow you to continuously change a value by moving a slider on a track. Currently the Pinch Slider can be moved by directly grabbing the slider, either directly or at a distance.</span></span> <span data-ttu-id="99c3f-107">I dispositivi di scorrimento funzionano su AR e VR, usando i controller di movimento, le mani o il gesto e la voce.</span><span class="sxs-lookup"><span data-stu-id="99c3f-107">Sliders work on AR and VR, using motion controllers, hands, or Gesture + Voice.</span></span>

## <a name="example-scene"></a><span data-ttu-id="99c3f-108">Scena di esempio</span><span class="sxs-lookup"><span data-stu-id="99c3f-108">Example scene</span></span>

<span data-ttu-id="99c3f-109">È possibile trovare esempi nella scena **SliderExample** in `MRTK/Examples/Demos/UX/Slider/Scenes/` .</span><span class="sxs-lookup"><span data-stu-id="99c3f-109">You can find examples in the **SliderExample** scene under `MRTK/Examples/Demos/UX/Slider/Scenes/`.</span></span>

## <a name="how-to-use-sliders"></a><span data-ttu-id="99c3f-110">Come usare i dispositivi di scorrimento</span><span class="sxs-lookup"><span data-stu-id="99c3f-110">How to use sliders</span></span>

<span data-ttu-id="99c3f-111">Trascinare e rilasciare il prefabbricato **PinchSlider** nella gerarchia della scena.</span><span class="sxs-lookup"><span data-stu-id="99c3f-111">Drag and drop the **PinchSlider** prefab into the scene hierarchy.</span></span> <span data-ttu-id="99c3f-112">Se si desidera modificare o creare il proprio dispositivo di scorrimento, ricordarsi di eseguire le operazioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="99c3f-112">If you want to modify or create your own slider, remember to do the following:</span></span>

- <span data-ttu-id="99c3f-113">Verificare che l'oggetto Thumb disponga di un Collider.</span><span class="sxs-lookup"><span data-stu-id="99c3f-113">Make sure your that your thumb object has a collider on it.</span></span> <span data-ttu-id="99c3f-114">Nella prefabbricazione PinchSlider, il Collider è on `SliderThumb/Button_AnimationContainer/Slider_Button`</span><span class="sxs-lookup"><span data-stu-id="99c3f-114">In the PinchSlider prefab, the collider is on `SliderThumb/Button_AnimationContainer/Slider_Button`</span></span>
- <span data-ttu-id="99c3f-115">Verificare che anche l'oggetto che contiene l'oggetto Collider disponga di un componente che può essere rilevabile in prossimità dell'interazione, se si desidera essere in grado di estrarre il dispositivo di scorrimento vicino a.</span><span class="sxs-lookup"><span data-stu-id="99c3f-115">Make sure that the object containing the collider also has a Near Interaction Grabbable component on it, if you want to be able to grab the slider near.</span></span>

<span data-ttu-id="99c3f-116">Si consiglia inoltre di utilizzare la seguente gerarchia</span><span class="sxs-lookup"><span data-stu-id="99c3f-116">We also recommend using the following hierarchy</span></span>

- <span data-ttu-id="99c3f-117">PinchSlider-contiene sliderComponent</span><span class="sxs-lookup"><span data-stu-id="99c3f-117">PinchSlider - Contains the sliderComponent</span></span>
  - <span data-ttu-id="99c3f-118">SliderThumb-contiene il pollice mobile</span><span class="sxs-lookup"><span data-stu-id="99c3f-118">SliderThumb - Contains the movable thumb</span></span>
  - <span data-ttu-id="99c3f-119">TrackVisuals-contenente la traccia e altri oggetti visivi</span><span class="sxs-lookup"><span data-stu-id="99c3f-119">TrackVisuals - Containing the track and any other visuals</span></span>
  - <span data-ttu-id="99c3f-120">OtherVisuals-contenenti altri oggetti visivi</span><span class="sxs-lookup"><span data-stu-id="99c3f-120">OtherVisuals - Containing any other visuals</span></span>

## <a name="slider-events"></a><span data-ttu-id="99c3f-121">Eventi Slider</span><span class="sxs-lookup"><span data-stu-id="99c3f-121">Slider events</span></span>

<span data-ttu-id="99c3f-122">I dispositivi di scorrimento espongono gli eventi seguenti:</span><span class="sxs-lookup"><span data-stu-id="99c3f-122">Sliders expose the following events:</span></span>

- <span data-ttu-id="99c3f-123">OnValueUpdated-chiamato ogni volta che viene modificato il valore del dispositivo di scorrimento</span><span class="sxs-lookup"><span data-stu-id="99c3f-123">OnValueUpdated - Called whenever the slider value changes</span></span>
- <span data-ttu-id="99c3f-124">OnInteractionStarted: viene chiamato quando l'utente estrae il dispositivo di scorrimento</span><span class="sxs-lookup"><span data-stu-id="99c3f-124">OnInteractionStarted - Called when the user grabs the slider</span></span>
- <span data-ttu-id="99c3f-125">OnInteractionEnded: viene chiamato quando l'utente rilascia il dispositivo di scorrimento</span><span class="sxs-lookup"><span data-stu-id="99c3f-125">OnInteractionEnded - Called when the user releases the slider</span></span>
- <span data-ttu-id="99c3f-126">OnHoverEntered: viene chiamato quando l'utente o il controller passa il puntatore del mouse sul dispositivo di scorrimento, usando un'interazione vicina o di gran lunga.</span><span class="sxs-lookup"><span data-stu-id="99c3f-126">OnHoverEntered - Called when the user's hand / controller hovers over the slider, using either near or far interaction.</span></span>
- <span data-ttu-id="99c3f-127">OnHoverExited: viene chiamato quando la mano o il controller dell'utente non è più vicino al dispositivo di scorrimento.</span><span class="sxs-lookup"><span data-stu-id="99c3f-127">OnHoverExited - Called when the user's hand / controller is no longer near the slider.</span></span>

## <a name="configuring-slider-bound-and-axis"></a><span data-ttu-id="99c3f-128">Configurazione dell'asse e del limite del dispositivo di scorrimento</span><span class="sxs-lookup"><span data-stu-id="99c3f-128">Configuring slider bound and axis</span></span>

<span data-ttu-id="99c3f-129">È possibile spostare direttamente i punti iniziale e finale del dispositivo di scorrimento spostando gli handle nella scena:</span><span class="sxs-lookup"><span data-stu-id="99c3f-129">You can directly move the starting and end points of the slider by moving the handles in the Scene:</span></span>

![Configurazione Slider](Images/Sliders/MRTK_Sliders_Setup.png)

<span data-ttu-id="99c3f-131">È anche possibile specificare l'asse (nello spazio locale) del dispositivo di scorrimento tramite il campo dell' _asse del dispositivo di scorrimento_</span><span class="sxs-lookup"><span data-stu-id="99c3f-131">You can also specify the axis (in local space) of the slider via the _Slider Axis_ field</span></span>

<span data-ttu-id="99c3f-132">Se non è possibile usare gli handle, è invece possibile specificare i punti iniziale e finale del dispositivo di scorrimento tramite i campi distanza _iniziale_ del dispositivo di scorrimento e _distanza di scorrimento_ .</span><span class="sxs-lookup"><span data-stu-id="99c3f-132">If you cannot use the handles, you can instead specify the start and end points of the slider via the _Slider Start Distance_ and _Slider End Distance_ fields.</span></span> <span data-ttu-id="99c3f-133">Che specificano la posizione iniziale/finale del dispositivo di scorrimento come distanza dal centro del dispositivo di scorrimento, in coordinate locali.</span><span class="sxs-lookup"><span data-stu-id="99c3f-133">These specify start / end position of slider as a distance from the slider's center, in local coordinates.</span></span> <span data-ttu-id="99c3f-134">Ciò significa che, una volta impostate le distanze di inizio e fine del dispositivo di scorrimento, è possibile ridimensionare il dispositivo di scorrimento in modo che sia più piccolo o più grande senza dover aggiornare le distanze di inizio e fine.</span><span class="sxs-lookup"><span data-stu-id="99c3f-134">This means that once you set the slider start and end distances as you want them, you can scale the slider to be smaller or larger without needing to update the start and end distances.</span></span>

## <a name="inspector-properties"></a><span data-ttu-id="99c3f-135">Proprietà di Inspector</span><span class="sxs-lookup"><span data-stu-id="99c3f-135">Inspector properties</span></span>

<span data-ttu-id="99c3f-136">**Radice Thumb** GameObject che contiene il cursore del dispositivo di scorrimento.</span><span class="sxs-lookup"><span data-stu-id="99c3f-136">**Thumb Root** The gameobject that contains the slider thumb.</span></span>

<span data-ttu-id="99c3f-137">**Valore dispositivo di scorrimento** Valore del dispositivo di scorrimento.</span><span class="sxs-lookup"><span data-stu-id="99c3f-137">**Slider Value** The value of the slider.</span></span>

<span data-ttu-id="99c3f-138">**Tenere traccia degli oggetti visivi** GameObject che contiene gli oggetti visivi di rilevamento desiderati che passano lungo il dispositivo di scorrimento.</span><span class="sxs-lookup"><span data-stu-id="99c3f-138">**Track Visuals** The gameobject that contains the desired track visuals that goes along the slider.</span></span>

<span data-ttu-id="99c3f-139">**Segni di graduazione** GameObject che contiene i segni di graduazione desiderati che passano lungo il dispositivo di scorrimento.</span><span class="sxs-lookup"><span data-stu-id="99c3f-139">**Tick Marks** The gameobject that contains the desired tick marks that goes along the slider.</span></span>

<span data-ttu-id="99c3f-140">Oggetti **visivi Thumb** GameObject che contiene l'oggetto visivo Thumb desiderato che va lungo il dispositivo di scorrimento.</span><span class="sxs-lookup"><span data-stu-id="99c3f-140">**Thumb Visuals** The gameobject that contains the desired thumb visual that goes along the slider.</span></span>

<span data-ttu-id="99c3f-141">**Asse del dispositivo di scorrimento** Asse in cui viene spostato il dispositivo di scorrimento.</span><span class="sxs-lookup"><span data-stu-id="99c3f-141">**Slider Axis** The axis the slider moves along.</span></span>

<span data-ttu-id="99c3f-142">**Distanza avvio dispositivo di scorrimento** Dove inizia la traccia del dispositivo di scorrimento, come distanza dal centro lungo l'asse del dispositivo di scorrimento, in unità di spazio locale.</span><span class="sxs-lookup"><span data-stu-id="99c3f-142">**Slider Start Distance** Where the slider track starts, as distance from center along slider axis, in local space units.</span></span>

<span data-ttu-id="99c3f-143">**Distanza finale dispositivo di scorrimento** Dove la traccia del dispositivo di scorrimento termina, come distanza dal centro lungo l'asse del dispositivo di scorrimento, in unità di spazio locale.</span><span class="sxs-lookup"><span data-stu-id="99c3f-143">**Slider End Distance** Where the slider track ends, as distance from center along slider axis, in local space units.</span></span>

<span data-ttu-id="99c3f-144">Quando l'utente aggiorna il valore dell'asse del dispositivo di scorrimento nell'editor, se vengono specificati oggetti visivi di rilevamento o oggetti visivi di selezione, la relativa trasformazione viene aggiornata.</span><span class="sxs-lookup"><span data-stu-id="99c3f-144">When user updates the slider axis value in editor then if Track Visuals or Tick Visuals are specified then their transform is updated.</span></span>
<span data-ttu-id="99c3f-145">In particolare, la posizione locale viene reimpostata e la rotazione locale viene impostata in modo da corrispondere all'orientamento dell'asse del dispositivo di scorrimento.</span><span class="sxs-lookup"><span data-stu-id="99c3f-145">Specifically, their local position is reset and their local rotation is set to match the Slider Axis orientation.</span></span>
<span data-ttu-id="99c3f-146">La scalabilità non è stata modificata.</span><span class="sxs-lookup"><span data-stu-id="99c3f-146">Their scale isn't modified.</span></span>
<span data-ttu-id="99c3f-147">Se i segni di graduazione contengono un componente della raccolta di oggetti Grid, il layout e CellWidth o CellHeight vengono aggiornati di conseguenza in modo da corrispondere all'asse del dispositivo di scorrimento.</span><span class="sxs-lookup"><span data-stu-id="99c3f-147">If Tick Marks have a Grid Object Collection component then the Layout and CellWidth or CellHeight is updated accordingly to match the Slider Axis.</span></span>

---
title: Movimenti e controller del movimento in Unity
description: Informazioni su come intervenire sullo sguardo in Unity con i movimenti della mano e i controller di movimento.
author: hferrone
ms.author: alexturn
ms.date: 12/1/2020
ms.topic: article
keywords: movimenti, controller di movimento, Unity, sguardo, input, cuffie per realtà mista, cuffie di realtà mista di Windows, cuffie per realtà virtuale, MRTK, Toolkit di realtà mista
ms.openlocfilehash: 122642bb7fc561e505098bca00b8bf65bfd4552e
ms.sourcegitcommit: 9664bcc10ed7e60f7593f3a7ae58c66060802ab1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/01/2020
ms.locfileid: "96443583"
---
# <a name="gestures-and-motion-controllers-in-unity"></a><span data-ttu-id="bfd57-104">Movimenti e controller del movimento in Unity</span><span class="sxs-lookup"><span data-stu-id="bfd57-104">Gestures and motion controllers in Unity</span></span>

<span data-ttu-id="bfd57-105">Ci sono due modi principali per agire sullo [sguardo in Unity](gaze-in-unity.md), [movimenti della mano](../../design/gaze-and-commit.md#composite-gestures) e [controller di movimento](../../design/motion-controllers.md) in HoloLens e HMD immersivi.</span><span class="sxs-lookup"><span data-stu-id="bfd57-105">There are two key ways to take action on your [gaze in Unity](gaze-in-unity.md), [hand gestures](../../design/gaze-and-commit.md#composite-gestures) and [motion controllers](../../design/motion-controllers.md) in HoloLens and Immersive HMD.</span></span> <span data-ttu-id="bfd57-106">È possibile accedere ai dati per entrambe le origini dell'input spaziale tramite le stesse API in Unity.</span><span class="sxs-lookup"><span data-stu-id="bfd57-106">You access the data for both sources of spatial input through the same APIs in Unity.</span></span>

<span data-ttu-id="bfd57-107">Unity offre due modi principali per accedere ai dati di input spaziali per la realtà mista di Windows, le API *input. GetButton/input. getaxis* comuni che funzionano su più SDK di Unity XR e un'API *InteractionManager/GestureRecognizer* specifica della realtà mista di Windows che espone il set completo di dati di input spaziali disponibili.</span><span class="sxs-lookup"><span data-stu-id="bfd57-107">Unity provides two primary ways to access spatial input data for Windows Mixed Reality, the common *Input.GetButton/Input.GetAxis* APIs that work across multiple Unity XR SDKs, and an *InteractionManager/GestureRecognizer* API specific to Windows Mixed Reality that exposes the full set of spatial input data available.</span></span>

## <a name="unity-xr-input-apis"></a><span data-ttu-id="bfd57-108">API di input di Unity XR</span><span class="sxs-lookup"><span data-stu-id="bfd57-108">Unity XR input APIs</span></span>

<span data-ttu-id="bfd57-109">Per i nuovi progetti, è consigliabile usare le nuove API di input XR dall'inizio.</span><span class="sxs-lookup"><span data-stu-id="bfd57-109">For new projects, we recommend using the new XR input APIs from the beginning.</span></span> 

<span data-ttu-id="bfd57-110">Altre informazioni sulle [API XR](https://docs.unity3d.com/Manual/xr_input.html)sono disponibili qui.</span><span class="sxs-lookup"><span data-stu-id="bfd57-110">You can find more information about the [XR APIs here](https://docs.unity3d.com/Manual/xr_input.html).</span></span>

## <a name="unity-buttonaxis-mapping-table"></a><span data-ttu-id="bfd57-111">Pulsante Unity/tabella di mapping asse</span><span class="sxs-lookup"><span data-stu-id="bfd57-111">Unity button/axis mapping table</span></span>

<span data-ttu-id="bfd57-112">Gli ID dei pulsanti e degli assi nella tabella seguente sono supportati nel gestore di input di Unity per i controller di movimento della realtà mista di Windows tramite le API *input. GetButton/getaxis* , mentre la colonna "Windows specific" si riferisce alle proprietà disponibili nel tipo *InteractionSourceState* .</span><span class="sxs-lookup"><span data-stu-id="bfd57-112">The button and axis IDs in the table below are supported in Unity's Input Manager for Windows Mixed Reality motion controllers through the *Input.GetButton/GetAxis* APIs, while the "Windows MR-specific" column refers to properties available off of the *InteractionSourceState* type.</span></span> <span data-ttu-id="bfd57-113">Ognuna di queste API è descritta in dettaglio nelle sezioni riportate di seguito.</span><span class="sxs-lookup"><span data-stu-id="bfd57-113">Each of these APIs are described in detail in the sections below.</span></span>

<span data-ttu-id="bfd57-114">I mapping degli ID di pulsanti/assi per la realtà mista di Windows in genere corrispondono agli ID dell'asse o del pulsante Oculus.</span><span class="sxs-lookup"><span data-stu-id="bfd57-114">The button/axis ID mappings for Windows Mixed Reality generally match the Oculus button/axis IDs.</span></span>

<span data-ttu-id="bfd57-115">I mapping degli ID di pulsanti/assi per la realtà mista di Windows differiscono dai mapping di OpenVR in due modi:</span><span class="sxs-lookup"><span data-stu-id="bfd57-115">The button/axis ID mappings for Windows Mixed Reality differ from OpenVR's mappings in two ways:</span></span>
1. <span data-ttu-id="bfd57-116">Il mapping USA ID touchpad distinti da levetta per supportare i controller con ThumbSticks e touchpad.</span><span class="sxs-lookup"><span data-stu-id="bfd57-116">The mapping uses touchpad IDs that are distinct from thumbstick, to support controllers with both thumbsticks and touchpads.</span></span>
2. <span data-ttu-id="bfd57-117">Il mapping evita l'overload degli ID dei pulsanti A e X per i pulsanti di menu, in modo da lasciare quelli disponibili per i pulsanti ABXY fisici.</span><span class="sxs-lookup"><span data-stu-id="bfd57-117">The mapping avoids overloading the A and X button IDs for the Menu buttons, to leave those available for physical ABXY buttons.</span></span>

<table>
<tr>
<th rowspan="2"><span data-ttu-id="bfd57-118">Input</span><span class="sxs-lookup"><span data-stu-id="bfd57-118">Input</span></span> </th><th colspan="2"><span data-ttu-id="bfd57-119"><a href="gestures-and-motion-controllers-in-unity.md#common-unity-apis-inputgetbuttongetaxis">API Unity comuni</a></span><span class="sxs-lookup"><span data-stu-id="bfd57-119"><a href="gestures-and-motion-controllers-in-unity.md#common-unity-apis-inputgetbuttongetaxis">Common Unity APIs</a></span></span><br /><span data-ttu-id="bfd57-120">(Input. GetButton/getaxis)</span><span class="sxs-lookup"><span data-stu-id="bfd57-120">(Input.GetButton/GetAxis)</span></span> </th><th rowspan="2"><span data-ttu-id="bfd57-121"><a href="gestures-and-motion-controllers-in-unity.md#">API di input specifica di Windows</a></span><span class="sxs-lookup"><span data-stu-id="bfd57-121"><a href="gestures-and-motion-controllers-in-unity.md#">Windows MR-specific Input API</a></span></span><br /><span data-ttu-id="bfd57-122">XR. WSA. Input</span><span class="sxs-lookup"><span data-stu-id="bfd57-122">(XR.WSA.Input)</span></span></th>
</tr><tr>
<th> <span data-ttu-id="bfd57-123">Mano sinistra</span><span class="sxs-lookup"><span data-stu-id="bfd57-123">Left hand</span></span> </th><th> <span data-ttu-id="bfd57-124">A destra</span><span class="sxs-lookup"><span data-stu-id="bfd57-124">Right hand</span></span></th>
</tr><tr>
<td> <span data-ttu-id="bfd57-125">Seleziona trigger premuto</span><span class="sxs-lookup"><span data-stu-id="bfd57-125">Select trigger pressed</span></span> </td><td> <span data-ttu-id="bfd57-126">AXIS 9 = 1,0</span><span class="sxs-lookup"><span data-stu-id="bfd57-126">Axis 9 = 1.0</span></span> </td><td> <span data-ttu-id="bfd57-127">Asse 10 = 1,0</span><span class="sxs-lookup"><span data-stu-id="bfd57-127">Axis 10 = 1.0</span></span> </td><td> <span data-ttu-id="bfd57-128">selectPressed</span><span class="sxs-lookup"><span data-stu-id="bfd57-128">selectPressed</span></span></td>
</tr><tr>
<td> <span data-ttu-id="bfd57-129">Selezionare il trigger valore analogico</span><span class="sxs-lookup"><span data-stu-id="bfd57-129">Select trigger analog value</span></span> </td><td> <span data-ttu-id="bfd57-130">Asse 9</span><span class="sxs-lookup"><span data-stu-id="bfd57-130">Axis 9</span></span> </td><td> <span data-ttu-id="bfd57-131">Asse 10</span><span class="sxs-lookup"><span data-stu-id="bfd57-131">Axis 10</span></span> </td><td> <span data-ttu-id="bfd57-132">selectPressedAmount</span><span class="sxs-lookup"><span data-stu-id="bfd57-132">selectPressedAmount</span></span></td>
</tr><tr>
<td> <span data-ttu-id="bfd57-133">Selezione trigger parzialmente premuto</span><span class="sxs-lookup"><span data-stu-id="bfd57-133">Select trigger partially pressed</span></span> </td><td> <span data-ttu-id="bfd57-134">Pulsante 14 <i>(gamepad compat)</i> </span><span class="sxs-lookup"><span data-stu-id="bfd57-134">Button 14 <i>(gamepad compat)</i> </span></span></td><td> <span data-ttu-id="bfd57-135">Pulsante 15 <i>(gamepad compat)</i> </span><span class="sxs-lookup"><span data-stu-id="bfd57-135">Button 15 <i>(gamepad compat)</i> </span></span></td><td> <span data-ttu-id="bfd57-136">selectPressedAmount &gt; 0,0</span><span class="sxs-lookup"><span data-stu-id="bfd57-136">selectPressedAmount &gt; 0.0</span></span></td>
</tr><tr>
<td> <span data-ttu-id="bfd57-137">Pulsante di menu premuto</span><span class="sxs-lookup"><span data-stu-id="bfd57-137">Menu button pressed</span></span> </td><td> <span data-ttu-id="bfd57-138">Pulsante 6 \*</span><span class="sxs-lookup"><span data-stu-id="bfd57-138">Button 6\*</span></span> </td><td> <span data-ttu-id="bfd57-139">Pulsante 7 \*</span><span class="sxs-lookup"><span data-stu-id="bfd57-139">Button 7\*</span></span> </td><td> <span data-ttu-id="bfd57-140">menuPressed</span><span class="sxs-lookup"><span data-stu-id="bfd57-140">menuPressed</span></span></td>
</tr><tr>
<td> <span data-ttu-id="bfd57-141">Pulsante grip premuto</span><span class="sxs-lookup"><span data-stu-id="bfd57-141">Grip button pressed</span></span> </td><td> <span data-ttu-id="bfd57-142">Asse 11 = 1,0 (nessun valore analogo)</span><span class="sxs-lookup"><span data-stu-id="bfd57-142">Axis 11 = 1.0 (no analog values)</span></span><br /><span data-ttu-id="bfd57-143">Pulsante 4 <i>(gamepad compat)</i> </span><span class="sxs-lookup"><span data-stu-id="bfd57-143">Button 4 <i>(gamepad compat)</i> </span></span></td><td> <span data-ttu-id="bfd57-144">Asse 12 = 1,0 (nessun valore analogo)</span><span class="sxs-lookup"><span data-stu-id="bfd57-144">Axis 12 = 1.0 (no analog values)</span></span><br /><span data-ttu-id="bfd57-145">Pulsante 5 <i>(gamepad compat)</i> </span><span class="sxs-lookup"><span data-stu-id="bfd57-145">Button 5 <i>(gamepad compat)</i> </span></span></td><td> <span data-ttu-id="bfd57-146">afferrato</span><span class="sxs-lookup"><span data-stu-id="bfd57-146">grasped</span></span></td>
</tr><tr>
<td> <span data-ttu-id="bfd57-147">Levetta X <i>(Left:-1,0, right: 1,0)</i> </span><span class="sxs-lookup"><span data-stu-id="bfd57-147">Thumbstick X <i>(left: -1.0, right: 1.0)</i> </span></span></td><td> <span data-ttu-id="bfd57-148">Asse 1</span><span class="sxs-lookup"><span data-stu-id="bfd57-148">Axis 1</span></span> </td><td> <span data-ttu-id="bfd57-149">Asse 4</span><span class="sxs-lookup"><span data-stu-id="bfd57-149">Axis 4</span></span> </td><td> <span data-ttu-id="bfd57-150">thumbstickPosition. x</span><span class="sxs-lookup"><span data-stu-id="bfd57-150">thumbstickPosition.x</span></span></td>
</tr><tr>
<td> <span data-ttu-id="bfd57-151">Levetta Y <i>(Top:-1,0, bottom: 1,0)</i> </span><span class="sxs-lookup"><span data-stu-id="bfd57-151">Thumbstick Y <i>(top: -1.0, bottom: 1.0)</i> </span></span></td><td> <span data-ttu-id="bfd57-152">Asse 2</span><span class="sxs-lookup"><span data-stu-id="bfd57-152">Axis 2</span></span> </td><td> <span data-ttu-id="bfd57-153">Asse 5</span><span class="sxs-lookup"><span data-stu-id="bfd57-153">Axis 5</span></span> </td><td> <span data-ttu-id="bfd57-154">thumbstickPosition. y</span><span class="sxs-lookup"><span data-stu-id="bfd57-154">thumbstickPosition.y</span></span></td>
</tr><tr>
<td> <span data-ttu-id="bfd57-155">Levetta premuto</span><span class="sxs-lookup"><span data-stu-id="bfd57-155">Thumbstick pressed</span></span> </td><td> <span data-ttu-id="bfd57-156">Pulsante 8</span><span class="sxs-lookup"><span data-stu-id="bfd57-156">Button 8</span></span> </td><td> <span data-ttu-id="bfd57-157">Pulsante 9</span><span class="sxs-lookup"><span data-stu-id="bfd57-157">Button 9</span></span> </td><td> <span data-ttu-id="bfd57-158">thumbstickPressed</span><span class="sxs-lookup"><span data-stu-id="bfd57-158">thumbstickPressed</span></span></td>
</tr><tr>
<td> <span data-ttu-id="bfd57-159">Touchpad X <i>(Left:-1,0, right: 1,0)</i> </span><span class="sxs-lookup"><span data-stu-id="bfd57-159">Touchpad X <i>(left: -1.0, right: 1.0)</i> </span></span></td><td> <span data-ttu-id="bfd57-160">Asse 17 \*</span><span class="sxs-lookup"><span data-stu-id="bfd57-160">Axis 17\*</span></span> </td><td> <span data-ttu-id="bfd57-161">Asse 19 \*</span><span class="sxs-lookup"><span data-stu-id="bfd57-161">Axis 19\*</span></span> </td><td> <span data-ttu-id="bfd57-162">touchpadPosition. x</span><span class="sxs-lookup"><span data-stu-id="bfd57-162">touchpadPosition.x</span></span></td>
</tr><tr>
<td> <span data-ttu-id="bfd57-163">Touchpad Y <i>(Top:-1,0, bottom: 1,0)</i> </span><span class="sxs-lookup"><span data-stu-id="bfd57-163">Touchpad Y <i>(top: -1.0, bottom: 1.0)</i> </span></span></td><td> <span data-ttu-id="bfd57-164">Asse 18 \*</span><span class="sxs-lookup"><span data-stu-id="bfd57-164">Axis 18\*</span></span> </td><td> <span data-ttu-id="bfd57-165">Asse 20 \*</span><span class="sxs-lookup"><span data-stu-id="bfd57-165">Axis 20\*</span></span> </td><td> <span data-ttu-id="bfd57-166">touchpadPosition. y</span><span class="sxs-lookup"><span data-stu-id="bfd57-166">touchpadPosition.y</span></span></td>
</tr><tr>
<td> <span data-ttu-id="bfd57-167">Tocco touchpad</span><span class="sxs-lookup"><span data-stu-id="bfd57-167">Touchpad touched</span></span> </td><td> <span data-ttu-id="bfd57-168">Pulsante 18 \*</span><span class="sxs-lookup"><span data-stu-id="bfd57-168">Button 18\*</span></span> </td><td> <span data-ttu-id="bfd57-169">Pulsante 19 \*</span><span class="sxs-lookup"><span data-stu-id="bfd57-169">Button 19\*</span></span> </td><td> <span data-ttu-id="bfd57-170">touchpadTouched</span><span class="sxs-lookup"><span data-stu-id="bfd57-170">touchpadTouched</span></span></td>
</tr><tr>
<td> <span data-ttu-id="bfd57-171">Touchpad premuto</span><span class="sxs-lookup"><span data-stu-id="bfd57-171">Touchpad pressed</span></span> </td><td> <span data-ttu-id="bfd57-172">Pulsante 16 \*</span><span class="sxs-lookup"><span data-stu-id="bfd57-172">Button 16\*</span></span> </td><td> <span data-ttu-id="bfd57-173">Pulsante 17 \*</span><span class="sxs-lookup"><span data-stu-id="bfd57-173">Button 17\*</span></span> </td><td> <span data-ttu-id="bfd57-174">touchpadPressed</span><span class="sxs-lookup"><span data-stu-id="bfd57-174">touchpadPressed</span></span></td>
</tr><tr>
<td> <span data-ttu-id="bfd57-175">6DoF della posa o del puntatore del grip</span><span class="sxs-lookup"><span data-stu-id="bfd57-175">6DoF grip pose or pointer pose</span></span> </td><td colspan="2"> <span data-ttu-id="bfd57-176">Solo <i>grip</i> per la posa: <a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html">XR. InputTracking. GetLocalPosition</a></span><span class="sxs-lookup"><span data-stu-id="bfd57-176"><i>Grip</i> pose only: <a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html">XR.InputTracking.GetLocalPosition</a></span></span><br /><span data-ttu-id="bfd57-177"><a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalRotation.html">XR. InputTracking.GetLocalRotation</a></span><span class="sxs-lookup"><span data-stu-id="bfd57-177"><a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalRotation.html">XR.InputTracking.GetLocalRotation</a></span></span></td><td> <span data-ttu-id="bfd57-178">Passare il <i>grip</i> o il <i>puntatore</i> come argomento: SourceState. sourcePose. TryGetPosition</span><span class="sxs-lookup"><span data-stu-id="bfd57-178">Pass <i>Grip</i> or <i>Pointer</i> as an argument: sourceState.sourcePose.TryGetPosition</span></span><br /><span data-ttu-id="bfd57-179">sourceState.sourcePose.TryGetRotation</span><span class="sxs-lookup"><span data-stu-id="bfd57-179">sourceState.sourcePose.TryGetRotation</span></span><br /></td>
</tr><tr>
<td> <span data-ttu-id="bfd57-180">Stato di rilevamento</span><span class="sxs-lookup"><span data-stu-id="bfd57-180">Tracking state</span></span> </td><td colspan="2"> <span data-ttu-id="bfd57-181"><i>Accuratezza della posizione e rischi per la perdita di codice sorgente solo tramite API specifiche del sig.</i> </span><span class="sxs-lookup"><span data-stu-id="bfd57-181"><i>Position accuracy and source loss risk only available through MR-specific API</i> </span></span></td><td> <span data-ttu-id="bfd57-182"><a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourcePose-positionAccuracy.html">sourceState.sourcePose.positionAccuracy</a></span><span class="sxs-lookup"><span data-stu-id="bfd57-182"><a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourcePose-positionAccuracy.html">sourceState.sourcePose.positionAccuracy</a></span></span><br /><span data-ttu-id="bfd57-183"><a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourceProperties-sourceLossRisk.html">sourceState. Properties. sourceLossRisk</a></span><span class="sxs-lookup"><span data-stu-id="bfd57-183"><a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourceProperties-sourceLossRisk.html">sourceState.properties.sourceLossRisk</a></span></span></td>
</tr>
</table>

>[!NOTE]
><span data-ttu-id="bfd57-184">Questi ID di pulsanti/assi sono diversi dagli ID usati da Unity per OpenVR a causa di conflitti nei mapping usati dai gamepad, Oculus touch e OpenVR.</span><span class="sxs-lookup"><span data-stu-id="bfd57-184">These button/axis IDs differ from the IDs that Unity uses for OpenVR due to collisions in the mappings used by gamepads, Oculus Touch and OpenVR.</span></span>

<!-- ### Using HP Reverb G2 controllers

If you're using the HP Reverb G2 controllers, refer to the table below for button and axis IDs.

<table>
<tr>
<th rowspan="2"><a href="https://docs.unity3d.com/ScriptReference/XR.CommonUsages.html">Input </th><th colspan="2">Common Unity APIs</a><br />(Input.GetButton/GetAxis) </th><th rowspan="2">HP Reverb G2 Input API</a></th>
</tr><tr>
<th> Left hand </th><th> Right hand</th>
</tr><tr>
<td> Primary2DAxis </td><td> Axis 1 (X) / Axis 2 (Y) </td><td> Axis 4 (X) / Axis 5(Y) </td><td> Thumbstick</td>
</tr><tr>
<td> Trigger pressed </td><td> Axis 9 </td><td> Axis 10 </td><td> Index trigger</td>
</tr><tr>
<td> Grip </td><td> Axis 11d </td><td> Axis 12 </td><td> Grip trigger</td>
</tr><tr>
<td> PrimaryButton pressed </td><td> Button 2 </td><td> Button 0 </td><td> Menu button pressed</td>
</tr><tr>
<td> SecondaryButton pressed </td><td> Button 3 </td><td> Button 1 </td><td> A/X button</td>
</tr><tr>
<td> GripButton </td><td> Button 4 </td><td> Button 5 </td><td> Grip trigger</td>
</tr><tr>
<td> TriggerButton </td><td> Button 14 </td><td> Button 15 </td><td> Index trigger</td>
</tr><tr>
</tr>
</table> -->


## <a name="grip-pose-vs-pointing-pose"></a><span data-ttu-id="bfd57-185">Posa del grip e puntamento</span><span class="sxs-lookup"><span data-stu-id="bfd57-185">Grip pose vs. pointing pose</span></span>

<span data-ttu-id="bfd57-186">La realtà mista di Windows supporta i controller di movimento in diversi fattori di forma, con la progettazione di ogni controller diversa nella relazione tra la posizione della mano dell'utente e la direzione naturale "Avanti" che le app devono usare per puntare durante il rendering del controller.</span><span class="sxs-lookup"><span data-stu-id="bfd57-186">Windows Mixed Reality supports motion controllers in a variety of form factors, with each controller's design differing in its relationship between the user's hand position and the natural "forward" direction that apps should use for pointing when rendering the controller.</span></span>

<span data-ttu-id="bfd57-187">Per rappresentare meglio questi controller, esistono due tipi di pose che è possibile esaminare per ogni origine interazione, la **posizione del grip** e la **posizione del puntatore**.</span><span class="sxs-lookup"><span data-stu-id="bfd57-187">To better represent these controllers, there are two kinds of poses you can investigate for each interaction source, the **grip pose** and the **pointer pose**.</span></span> <span data-ttu-id="bfd57-188">Sia le coordinate della formula del grip che del puntatore sono espresse da tutte le API Unity nelle coordinate globali di Unity.</span><span class="sxs-lookup"><span data-stu-id="bfd57-188">Both the grip pose and pointer pose coordinates are expressed by all Unity APIs in global Unity world coordinates.</span></span>

### <a name="grip-pose"></a><span data-ttu-id="bfd57-189">Pose di grip</span><span class="sxs-lookup"><span data-stu-id="bfd57-189">Grip pose</span></span>

<span data-ttu-id="bfd57-190">La posizione del **grip** rappresenta la posizione della Palma di una mano rilevata da un HoloLens o della palma che contiene un controller di movimento.</span><span class="sxs-lookup"><span data-stu-id="bfd57-190">The **grip pose** represents the location of either the palm of a hand detected by a HoloLens, or the palm holding a motion controller.</span></span>

<span data-ttu-id="bfd57-191">Negli auricolari immersivi, la disposizione dei grip è la scelta migliore per eseguire **il rendering della mano dell'utente** o di **un oggetto contenuto nella mano**, ad esempio una spada o una pistola.</span><span class="sxs-lookup"><span data-stu-id="bfd57-191">On immersive headsets, the grip pose is best used to render **the user's hand** or **an object held in the user's hand**, such as a sword or gun.</span></span> <span data-ttu-id="bfd57-192">La posizione del grip viene usata anche durante la visualizzazione di un controller di movimento, perché il **modello di rendering** fornito da Windows per un controller di movimento usa la posizione del grip come origine e centro di rotazione.</span><span class="sxs-lookup"><span data-stu-id="bfd57-192">The grip pose is also used when visualizing a motion controller, as the **renderable model** provided by Windows for a motion controller uses the grip pose as its origin and center of rotation.</span></span>

<span data-ttu-id="bfd57-193">Il grip viene definito in modo specifico come segue:</span><span class="sxs-lookup"><span data-stu-id="bfd57-193">The grip pose is defined specifically as follows:</span></span>
* <span data-ttu-id="bfd57-194">**Posizione del grip**: il centro della palma quando si tiene il controller in modo naturale, regolato a sinistra o a destra per centrare la posizione all'interno del grip.</span><span class="sxs-lookup"><span data-stu-id="bfd57-194">The **grip position**: The palm centroid when holding the controller naturally, adjusted left or right to center the position within the grip.</span></span> <span data-ttu-id="bfd57-195">Sul controller di movimento per la realtà mista di Windows, questa posizione viene in genere allineata con il pulsante afferra.</span><span class="sxs-lookup"><span data-stu-id="bfd57-195">On the Windows Mixed Reality motion controller, this position generally aligns with the Grasp button.</span></span>
* <span data-ttu-id="bfd57-196">L' **asse destro dell'orientamento del grip**: quando si apre completamente la mano per formare una formula a 5 dita piatta, il raggio normale per la Palma (in avanti dal palmo sinistro e viceversa)</span><span class="sxs-lookup"><span data-stu-id="bfd57-196">The **grip orientation's Right axis**: When you completely open your hand to form a flat 5-finger pose, the ray that is normal to your palm (forward from left palm, backward from right palm)</span></span>
* <span data-ttu-id="bfd57-197">**Asse di avanzamento dell'orientamento del grip**: quando si chiude parzialmente la mano (come se si utilizzasse il controller), il raggio che punta "in poi" attraverso il tubo formato dalle dita non Thumb.</span><span class="sxs-lookup"><span data-stu-id="bfd57-197">The **grip orientation's Forward axis**: When you close your hand partially (as if holding the controller), the ray that points "forward" through the tube formed by your non-thumb fingers.</span></span>
* <span data-ttu-id="bfd57-198">**Asse verticale dell'orientamento del grip**: l'asse verso l'alto implicato dalle definizioni di destra e di avanzamento.</span><span class="sxs-lookup"><span data-stu-id="bfd57-198">The **grip orientation's Up axis**: The Up axis implied by the Right and Forward definitions.</span></span>

<span data-ttu-id="bfd57-199">È possibile accedere al grip con l'API di input tra fornitori di Unity (*[XR). InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html). GetLocalPosition/Rotation*) o tramite l'API specifica di Windows (*SourceState. SourcePose. TryGetPosition/Rotation*, che richiede i dati di post per il nodo **grip** ).</span><span class="sxs-lookup"><span data-stu-id="bfd57-199">You can access the grip pose through either Unity's cross-vendor input API (*[XR.InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html).GetLocalPosition/Rotation*) or through the Windows MR-specific API (*sourceState.sourcePose.TryGetPosition/Rotation*, requesting pose data for the **Grip** node).</span></span>

### <a name="pointer-pose"></a><span data-ttu-id="bfd57-200">Posa puntatore</span><span class="sxs-lookup"><span data-stu-id="bfd57-200">Pointer pose</span></span>

<span data-ttu-id="bfd57-201">Il **puntatore** posizionato rappresenta il suggerimento del controller che punta in futuro.</span><span class="sxs-lookup"><span data-stu-id="bfd57-201">The **pointer pose** represents the tip of the controller pointing forward.</span></span>

<span data-ttu-id="bfd57-202">La disposizione del puntatore fornita dal sistema è ideale per Raycast quando si esegue **il rendering del modello di controller**.</span><span class="sxs-lookup"><span data-stu-id="bfd57-202">The system-provided pointer pose is best used to raycast when you are **rendering the controller model itself**.</span></span> <span data-ttu-id="bfd57-203">Se si esegue il rendering di un altro oggetto virtuale al posto del controller, ad esempio una pistola virtuale, è necessario puntare con un raggio più naturale per tale oggetto virtuale, ad esempio un raggio che viaggia lungo il barilotto del modello Gun definito dall'app.</span><span class="sxs-lookup"><span data-stu-id="bfd57-203">If you are rendering some other virtual object in place of the controller, such as a virtual gun, you should point with a ray that is most natural for that virtual object, such as a ray that travels along the barrel of the app-defined gun model.</span></span> <span data-ttu-id="bfd57-204">Poiché gli utenti possono visualizzare l'oggetto virtuale e non il controller fisico, puntare con l'oggetto virtuale sarà probabilmente più naturale per quelli che usano l'app.</span><span class="sxs-lookup"><span data-stu-id="bfd57-204">Because users can see the virtual object and not the physical controller, pointing with the virtual object will likely be more natural for those using your app.</span></span>

<span data-ttu-id="bfd57-205">Attualmente, la posa del puntatore è disponibile in Unity solo tramite l'API specifica di Windows, *sourceState. sourcePose. TryGetPosition/Rotation*, passando *InteractionSourceNode. pointer* come argomento.</span><span class="sxs-lookup"><span data-stu-id="bfd57-205">Currently, the pointer pose is available in Unity only through the Windows MR-specific API, *sourceState.sourcePose.TryGetPosition/Rotation*, passing in *InteractionSourceNode.Pointer* as the argument.</span></span>

## <a name="controller-tracking-state"></a><span data-ttu-id="bfd57-206">Stato di rilevamento del controller</span><span class="sxs-lookup"><span data-stu-id="bfd57-206">Controller tracking state</span></span>

<span data-ttu-id="bfd57-207">Come gli auricolari, il controller di movimento di realtà mista di Windows non richiede l'installazione di sensori di rilevamento esterni.</span><span class="sxs-lookup"><span data-stu-id="bfd57-207">Like the headsets, the Windows Mixed Reality motion controller requires no setup of external tracking sensors.</span></span> <span data-ttu-id="bfd57-208">Il controller viene invece rilevato dai sensori nell'auricolare.</span><span class="sxs-lookup"><span data-stu-id="bfd57-208">Instead, the controllers are tracked by sensors in the headset itself.</span></span>

<span data-ttu-id="bfd57-209">Se l'utente sposta i controller fuori dal campo di visualizzazione dell'auricolare, nella maggior parte dei casi Windows continuerà a dedurre le posizioni del controller e le fornirà all'app.</span><span class="sxs-lookup"><span data-stu-id="bfd57-209">If the user moves the controllers out of the headset's field of view, in most cases Windows will continue to infer controller positions and provide them to the app.</span></span> <span data-ttu-id="bfd57-210">Quando il controller ha perso il rilevamento visivo per un periodo di tempo sufficiente, le posizioni del controller vengono rilasciate a posizioni di accuratezza approssimativa.</span><span class="sxs-lookup"><span data-stu-id="bfd57-210">When the controller has lost visual tracking for long enough, the controller's positions will drop to approximate-accuracy positions.</span></span>

<span data-ttu-id="bfd57-211">A questo punto, il sistema bloccherà il controller all'utente, tenendo traccia della posizione dell'utente mentre si spostano, esponendo comunque il vero orientamento del controller usando i sensori di orientamento interni.</span><span class="sxs-lookup"><span data-stu-id="bfd57-211">At this point, the system will body-lock the controller to the user, tracking the user's position as they move around, while still exposing the controller's true orientation using its internal orientation sensors.</span></span> <span data-ttu-id="bfd57-212">Molte app che usano i controller per puntare e attivare gli elementi dell'interfaccia utente possono funzionare normalmente con una precisione approssimativa senza che l'utente abbia notato.</span><span class="sxs-lookup"><span data-stu-id="bfd57-212">Many apps that use controllers to point at and activate UI elements can operate normally while in approximate accuracy without the user noticing.</span></span>

<span data-ttu-id="bfd57-213">Il modo migliore per ottenere questo aspetto è provare a eseguire l'operazione.</span><span class="sxs-lookup"><span data-stu-id="bfd57-213">The best way to get a feel for this is to try it yourself.</span></span> <span data-ttu-id="bfd57-214">Vedere questo video con esempi di contenuti immersivi che funzionano con i controller di movimento in diversi Stati di rilevamento:</span><span class="sxs-lookup"><span data-stu-id="bfd57-214">Check out this video with examples of immersive content that works with motion controllers across various tracking states:</span></span>

<br>

 >[!VIDEO https://www.youtube.com/embed/QK_fOFDHj0g]

### <a name="reasoning-about-tracking-state-explicitly"></a><span data-ttu-id="bfd57-215">Ragionamento sullo stato di rilevamento in modo esplicito</span><span class="sxs-lookup"><span data-stu-id="bfd57-215">Reasoning about tracking state explicitly</span></span>

<span data-ttu-id="bfd57-216">Le app che desiderano gestire le posizioni in modo diverso in base allo stato di rilevamento possono andare oltre e controllare le proprietà nello stato del controller, ad esempio *SourceLossRisk* e *PositionAccuracy*:</span><span class="sxs-lookup"><span data-stu-id="bfd57-216">Apps that wish to treat positions differently based on tracking state may go further and inspect properties on the controller's state, such as *SourceLossRisk* and *PositionAccuracy*:</span></span>

<table>
<tr>
<th> <span data-ttu-id="bfd57-217">Stato di rilevamento</span><span class="sxs-lookup"><span data-stu-id="bfd57-217">Tracking state</span></span> </th><th> <span data-ttu-id="bfd57-218">SourceLossRisk</span><span class="sxs-lookup"><span data-stu-id="bfd57-218">SourceLossRisk</span></span> </th><th> <span data-ttu-id="bfd57-219">PositionAccuracy</span><span class="sxs-lookup"><span data-stu-id="bfd57-219">PositionAccuracy</span></span> </th><th> <span data-ttu-id="bfd57-220">TryGetPosition</span><span class="sxs-lookup"><span data-stu-id="bfd57-220">TryGetPosition</span></span></th>
</tr><tr>
<td> <span data-ttu-id="bfd57-221"><b>Accuratezza elevata</b> </span><span class="sxs-lookup"><span data-stu-id="bfd57-221"><b>High accuracy</b> </span></span></td><td style="background-color: green; color: white"> <span data-ttu-id="bfd57-222">&lt; 1,0</span><span class="sxs-lookup"><span data-stu-id="bfd57-222">&lt; 1.0</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="bfd57-223">Alto</span><span class="sxs-lookup"><span data-stu-id="bfd57-223">High</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="bfd57-224">true</span><span class="sxs-lookup"><span data-stu-id="bfd57-224">true</span></span></td>
</tr><tr>
<td> <span data-ttu-id="bfd57-225"><b>Accuratezza elevata (a rischio di perdita)</b> </span><span class="sxs-lookup"><span data-stu-id="bfd57-225"><b>High accuracy (at risk of losing)</b> </span></span></td><td style="background-color: orange"> <span data-ttu-id="bfd57-226">= = 1,0</span><span class="sxs-lookup"><span data-stu-id="bfd57-226">== 1.0</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="bfd57-227">Alto</span><span class="sxs-lookup"><span data-stu-id="bfd57-227">High</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="bfd57-228">true</span><span class="sxs-lookup"><span data-stu-id="bfd57-228">true</span></span></td>
</tr><tr>
<td> <span data-ttu-id="bfd57-229"><b>Accuratezza approssimativa</b> </span><span class="sxs-lookup"><span data-stu-id="bfd57-229"><b>Approximate accuracy</b> </span></span></td><td style="background-color: orange"> <span data-ttu-id="bfd57-230">= = 1,0</span><span class="sxs-lookup"><span data-stu-id="bfd57-230">== 1.0</span></span> </td><td style="background-color: orange"> <span data-ttu-id="bfd57-231">Con approssimazione</span><span class="sxs-lookup"><span data-stu-id="bfd57-231">Approximate</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="bfd57-232">true</span><span class="sxs-lookup"><span data-stu-id="bfd57-232">true</span></span></td>
</tr><tr>
<td> <span data-ttu-id="bfd57-233"><b>Nessuna posizione</b> </span><span class="sxs-lookup"><span data-stu-id="bfd57-233"><b>No position</b> </span></span></td><td style="background-color: orange"> <span data-ttu-id="bfd57-234">= = 1,0</span><span class="sxs-lookup"><span data-stu-id="bfd57-234">== 1.0</span></span> </td><td style="background-color: orange"> <span data-ttu-id="bfd57-235">Con approssimazione</span><span class="sxs-lookup"><span data-stu-id="bfd57-235">Approximate</span></span> </td><td style="background-color: orange"> <span data-ttu-id="bfd57-236">false</span><span class="sxs-lookup"><span data-stu-id="bfd57-236">false</span></span></td>
</tr>
</table>

<span data-ttu-id="bfd57-237">Questi stati di rilevamento del controller di movimento sono definiti come segue:</span><span class="sxs-lookup"><span data-stu-id="bfd57-237">These motion controller tracking states are defined as follows:</span></span>
* <span data-ttu-id="bfd57-238">**Accuratezza elevata:** Mentre il controller di movimento si trova all'interno del campo di visualizzazione dell'auricolare, in genere fornisce posizioni con accuratezza elevata, in base al rilevamento visivo.</span><span class="sxs-lookup"><span data-stu-id="bfd57-238">**High accuracy:** While the motion controller is within the headset's field of view, it will generally provide high-accuracy positions, based on visual tracking.</span></span> <span data-ttu-id="bfd57-239">Si noti che un controller che sposta temporaneamente il campo di visualizzazione o è temporaneamente nascosto dai sensori dell'auricolare (ad esempio, da parte dell'utente) continuerà a restituire le pose con precisione elevata per un breve periodo di tempo, in base al rilevamento inerziale del controller stesso.</span><span class="sxs-lookup"><span data-stu-id="bfd57-239">Note that a moving controller that momentarily leaves the field of view or is momentarily obscured from the headset sensors (e.g. by the user's other hand) will continue to return high-accuracy poses for a short time, based on inertial tracking of the controller itself.</span></span>
* <span data-ttu-id="bfd57-240">**Accuratezza elevata (a rischio di perdita):** Quando l'utente sposta il controller di movimento oltre il bordo del campo di visualizzazione dell'auricolare, l'auricolare non sarà presto in grado di rilevare visivamente la posizione del controller.</span><span class="sxs-lookup"><span data-stu-id="bfd57-240">**High accuracy (at risk of losing):** When the user moves the motion controller past the edge of the headset's field of view, the headset will soon be unable to visually track the controller's position.</span></span> <span data-ttu-id="bfd57-241">L'app sa quando il controller ha raggiunto questo limite FOV visualizzando il **SourceLossRisk** REACH 1,0.</span><span class="sxs-lookup"><span data-stu-id="bfd57-241">The app knows when the controller has reached this FOV boundary by seeing the **SourceLossRisk** reach 1.0.</span></span> <span data-ttu-id="bfd57-242">A questo punto, l'app può scegliere di sospendere i movimenti del controller che richiedono un flusso costante di pose di qualità molto elevata.</span><span class="sxs-lookup"><span data-stu-id="bfd57-242">At that point, the app may choose to pause controller gestures that require a steady stream of very high-quality poses.</span></span>
* <span data-ttu-id="bfd57-243">**Accuratezza approssimativa:** Quando il controller ha perso il rilevamento visivo per un periodo di tempo sufficiente, le posizioni del controller vengono rilasciate a posizioni di accuratezza approssimativa.</span><span class="sxs-lookup"><span data-stu-id="bfd57-243">**Approximate accuracy:** When the controller has lost visual tracking for long enough, the controller's positions will drop to approximate-accuracy positions.</span></span> <span data-ttu-id="bfd57-244">A questo punto, il sistema bloccherà il controller all'utente, tenendo traccia della posizione dell'utente mentre si spostano, esponendo comunque il vero orientamento del controller usando i sensori di orientamento interni.</span><span class="sxs-lookup"><span data-stu-id="bfd57-244">At this point, the system will body-lock the controller to the user, tracking the user's position as they move around, while still exposing the controller's true orientation using its internal orientation sensors.</span></span> <span data-ttu-id="bfd57-245">Molte app che usano i controller per puntare e attivare gli elementi dell'interfaccia utente possono funzionare normalmente con una precisione approssimativa senza che l'utente ne abbia notato.</span><span class="sxs-lookup"><span data-stu-id="bfd57-245">Many apps that use controllers to point at and activate UI elements can operate as normal while in approximate accuracy without the user noticing.</span></span> <span data-ttu-id="bfd57-246">Le app con requisiti di input più pesanti possono scegliere di comprendere questo calo dall'accuratezza **elevata** all'accuratezza **approssimativa** controllando la proprietà **PositionAccuracy** , ad esempio per dare all'utente un hitbox più generoso sulle destinazioni fuori schermo durante questo periodo di tempo.</span><span class="sxs-lookup"><span data-stu-id="bfd57-246">Apps with heavier input requirements may choose to sense this drop from **High** accuracy to **Approximate** accuracy by inspecting the **PositionAccuracy** property, for example to give the user a more generous hitbox on off-screen targets during this time.</span></span>
* <span data-ttu-id="bfd57-247">**Nessuna posizione:** Mentre il controller può funzionare con una precisione approssimativa per molto tempo, a volte il sistema sa che anche una posizione bloccata dal corpo non è al momento significativa.</span><span class="sxs-lookup"><span data-stu-id="bfd57-247">**No position:** While the controller can operate at approximate accuracy for a long time, sometimes the system knows that even a body-locked position is not meaningful at the moment.</span></span> <span data-ttu-id="bfd57-248">Ad esempio, un controller appena attivato potrebbe non essere mai stato osservato visivamente oppure un utente può arrestare un controller che viene quindi prelevato da qualcun altro.</span><span class="sxs-lookup"><span data-stu-id="bfd57-248">For example, a controller that was just turned on may have never been observed visually, or a user may put down a controller that's then picked up by someone else.</span></span> <span data-ttu-id="bfd57-249">In questi casi, il sistema non fornirà alcuna posizione all'app e *TryGetPosition* restituirà false.</span><span class="sxs-lookup"><span data-stu-id="bfd57-249">At those times, the system will not provide any position to the app, and *TryGetPosition* will return false.</span></span>

## <a name="common-unity-apis-inputgetbuttongetaxis"></a><span data-ttu-id="bfd57-250">API Unity comuni (input. GetButton/getaxis)</span><span class="sxs-lookup"><span data-stu-id="bfd57-250">Common Unity APIs (Input.GetButton/GetAxis)</span></span>

<span data-ttu-id="bfd57-251">**Spazio dei nomi:** *UnityEngine*, *UnityEngine. XR*</span><span class="sxs-lookup"><span data-stu-id="bfd57-251">**Namespace:** *UnityEngine*, *UnityEngine.XR*</span></span><br>
<span data-ttu-id="bfd57-252">**Tipi**: *input*, *XR. InputTracking*</span><span class="sxs-lookup"><span data-stu-id="bfd57-252">**Types**: *Input*, *XR.InputTracking*</span></span>

<span data-ttu-id="bfd57-253">Unity usa attualmente le API *input. GetButton/input. getaxis* per esporre l'input per [Oculus SDK](https://docs.unity3d.com/Manual/OculusControllers.html), [l'SDK di OpenVR e la](https://docs.unity3d.com/Manual/OpenVRControllers.html) realtà mista di Windows, inclusi i controller hands e Motion.</span><span class="sxs-lookup"><span data-stu-id="bfd57-253">Unity currently uses its general *Input.GetButton/Input.GetAxis* APIs to expose input for [the Oculus SDK](https://docs.unity3d.com/Manual/OculusControllers.html), [the OpenVR SDK](https://docs.unity3d.com/Manual/OpenVRControllers.html) and Windows Mixed Reality, including hands and motion controllers.</span></span> <span data-ttu-id="bfd57-254">Se l'app usa queste API per l'input, può supportare facilmente i controller di movimento tra più SDK XR, inclusa la realtà mista di Windows.</span><span class="sxs-lookup"><span data-stu-id="bfd57-254">If your app uses these APIs for input, it can easily support motion controllers across multiple XR SDKs, including Windows Mixed Reality.</span></span>

### <a name="getting-a-logical-buttons-pressed-state"></a><span data-ttu-id="bfd57-255">Recupero dello stato premuto di un pulsante logico</span><span class="sxs-lookup"><span data-stu-id="bfd57-255">Getting a logical button's pressed state</span></span>

<span data-ttu-id="bfd57-256">Per usare le API di input di Unity generale, si inizia in genere collegando pulsanti e assi ai nomi logici in [Gestione input Unity](https://docs.unity3d.com/Manual/ConventionalGameInput.html), associando un pulsante o gli ID dell'asse a ogni nome.</span><span class="sxs-lookup"><span data-stu-id="bfd57-256">To use the general Unity input APIs, you'll typically start by wiring up buttons and axes to logical names in the [Unity Input Manager](https://docs.unity3d.com/Manual/ConventionalGameInput.html), binding a button or axis IDs to each name.</span></span> <span data-ttu-id="bfd57-257">È quindi possibile scrivere codice che fa riferimento a tale nome di pulsante/asse logico.</span><span class="sxs-lookup"><span data-stu-id="bfd57-257">You can then write code that refers to that logical button/axis name.</span></span>

<span data-ttu-id="bfd57-258">Ad esempio, per eseguire il mapping del pulsante trigger del controller di movimento sinistro all'azione Invia, passare a **modifica > impostazioni progetto > input** in Unity ed espandere le proprietà della sezione Submit in assi.</span><span class="sxs-lookup"><span data-stu-id="bfd57-258">For example, to map the left motion controller's trigger button to the Submit action, go to **Edit > Project Settings > Input** within Unity, and expand the properties of the Submit section under Axes.</span></span> <span data-ttu-id="bfd57-259">Modificare il pulsante **positivo** o la proprietà **pulsante Alt positivo** per leggere il **pulsante del joystick 14**, in questo modo:</span><span class="sxs-lookup"><span data-stu-id="bfd57-259">Change the **Positive Button** or **Alt Positive Button** property to read **joystick button 14**, like this:</span></span>

<span data-ttu-id="bfd57-260">![InputManager di Unity](images/unity-input-manager.png)</span><span class="sxs-lookup"><span data-stu-id="bfd57-260">![Unity's InputManager](images/unity-input-manager.png)</span></span><br>
<span data-ttu-id="bfd57-261">*Unity InputManager*</span><span class="sxs-lookup"><span data-stu-id="bfd57-261">*Unity InputManager*</span></span>

<span data-ttu-id="bfd57-262">Lo script può quindi verificare la presenza di un'azione di invio tramite *input. GetButton*:</span><span class="sxs-lookup"><span data-stu-id="bfd57-262">Your script can then check for the Submit action using *Input.GetButton*:</span></span>

```cs
if (Input.GetButton("Submit"))
{
  // ...
}
```
<span data-ttu-id="bfd57-263">È possibile aggiungere più pulsanti logici modificando la proprietà **size** in **assi**.</span><span class="sxs-lookup"><span data-stu-id="bfd57-263">You can add more logical buttons by changing the **Size** property under **Axes**.</span></span>

### <a name="getting-a-physical-buttons-pressed-state-directly"></a><span data-ttu-id="bfd57-264">Ottenere direttamente lo stato premuto di un pulsante fisico</span><span class="sxs-lookup"><span data-stu-id="bfd57-264">Getting a physical button's pressed state directly</span></span>

<span data-ttu-id="bfd57-265">È anche possibile accedere manualmente ai pulsanti con il nome completo, usando *input. GetKey*:</span><span class="sxs-lookup"><span data-stu-id="bfd57-265">You can also access buttons manually by their fully-qualified name, using *Input.GetKey*:</span></span>

```cs
if (Input.GetKey("joystick button 8"))
{
  // ...
}
```

### <a name="getting-a-hand-or-motion-controllers-pose"></a><span data-ttu-id="bfd57-266">Acquisizione di una mano o di un controller di movimento</span><span class="sxs-lookup"><span data-stu-id="bfd57-266">Getting a hand or motion controller's pose</span></span>

<span data-ttu-id="bfd57-267">È possibile accedere alla posizione e alla rotazione del controller usando *XR. InputTracking*:</span><span class="sxs-lookup"><span data-stu-id="bfd57-267">You can access the position and rotation of the controller, using *XR.InputTracking*:</span></span>

```cs
Vector3 leftPosition = InputTracking.GetLocalPosition(XRNode.LeftHand);
Quaternion leftRotation = InputTracking.GetLocalRotation(XRNode.LeftHand);
```

<span data-ttu-id="bfd57-268">Si noti che questo rappresenta la posizione del grip del controller (dove l'utente possiede il controller), che è utile per il rendering di una spada o di una pistola nella mano dell'utente o di un modello del controller stesso.</span><span class="sxs-lookup"><span data-stu-id="bfd57-268">Note that this represents the controller's grip pose (where the user holds the controller), which is useful for rendering a sword or gun in the user's hand, or a model of the controller itself.</span></span>

<span data-ttu-id="bfd57-269">Si noti che la relazione tra la posizione del grip e la posizione del puntatore (dove la punta del controller sta puntando) può variare tra i controller.</span><span class="sxs-lookup"><span data-stu-id="bfd57-269">Note that the relationship between this grip pose and the pointer pose (where the tip of the controller is pointing) may differ across controllers.</span></span> <span data-ttu-id="bfd57-270">Al momento, l'accesso alla posizione del puntatore del controller è possibile solo tramite l'API di input specifica del sig, descritta nelle sezioni riportate di seguito.</span><span class="sxs-lookup"><span data-stu-id="bfd57-270">At this moment, accessing the controller's pointer pose is only possible through the MR-specific input API, described in the sections below.</span></span>

## <a name="windows-specific-apis-xrwsainput"></a><span data-ttu-id="bfd57-271">API specifiche di Windows (XR. WSA. Input</span><span class="sxs-lookup"><span data-stu-id="bfd57-271">Windows-specific APIs (XR.WSA.Input)</span></span>

> [!CAUTION]
> <span data-ttu-id="bfd57-272">Se il progetto usa uno dei XR. Le API WSA vengono gradualmente eliminate a favore di XR SDK in future versioni di Unity.</span><span class="sxs-lookup"><span data-stu-id="bfd57-272">If your project is using any of the XR.WSA APIs, these are being phased out in favor of the XR SDK in future Unity releases.</span></span> <span data-ttu-id="bfd57-273">Per i nuovi progetti, è consigliabile usare XR SDK dall'inizio.</span><span class="sxs-lookup"><span data-stu-id="bfd57-273">For new projects, we recommend using the XR SDK from the beginning.</span></span> <span data-ttu-id="bfd57-274">Altre informazioni sul [sistema di input e sulle API di XR](https://docs.unity3d.com/Manual/xr_input.html)sono disponibili qui.</span><span class="sxs-lookup"><span data-stu-id="bfd57-274">You can find more information about the [XR Input system and APIs here](https://docs.unity3d.com/Manual/xr_input.html).</span></span>

<span data-ttu-id="bfd57-275">**Spazio dei nomi:** *UnityEngine. XR. WSA. input*</span><span class="sxs-lookup"><span data-stu-id="bfd57-275">**Namespace:** *UnityEngine.XR.WSA.Input*</span></span><br>
<span data-ttu-id="bfd57-276">**Tipi**: *InteractionManager*, *InteractionSourceState*, *InteractionSource*, *InteractionSourceProperties*, *InteractionSourceKind*, *InteractionSourceLocation*</span><span class="sxs-lookup"><span data-stu-id="bfd57-276">**Types**: *InteractionManager*, *InteractionSourceState*, *InteractionSource*, *InteractionSourceProperties*, *InteractionSourceKind*, *InteractionSourceLocation*</span></span>

<span data-ttu-id="bfd57-277">Per ottenere informazioni più dettagliate sull'input della realtà mista di Windows (per HoloLens) e sui controller di movimento, è possibile scegliere di usare le API di input spaziali specifiche di Windows nello spazio dei nomi *UnityEngine. XR. WSA. input* .</span><span class="sxs-lookup"><span data-stu-id="bfd57-277">To get at more detailed information about Windows Mixed Reality hand input (for HoloLens) and motion controllers, you can choose to use the Windows-specific spatial input APIs under the *UnityEngine.XR.WSA.Input* namespace.</span></span> <span data-ttu-id="bfd57-278">In questo modo è possibile accedere a informazioni aggiuntive, come l'accuratezza della posizione o il tipo di origine, che consentono di distinguere le mani e i controller.</span><span class="sxs-lookup"><span data-stu-id="bfd57-278">This lets you access additional information, such as position accuracy or the source kind, letting you tell hands and controllers apart.</span></span>

### <a name="polling-for-the-state-of-hands-and-motion-controllers"></a><span data-ttu-id="bfd57-279">Polling dello stato di hands and Motion Controllers</span><span class="sxs-lookup"><span data-stu-id="bfd57-279">Polling for the state of hands and motion controllers</span></span>

<span data-ttu-id="bfd57-280">È possibile eseguire il polling dello stato di questo frame per ogni origine interazione (controller di movimento o mano) usando il metodo *GetCurrentReading* .</span><span class="sxs-lookup"><span data-stu-id="bfd57-280">You can poll for this frame's state for each interaction source (hand or motion controller) using the *GetCurrentReading* method.</span></span>

```cs
var interactionSourceStates = InteractionManager.GetCurrentReading();
foreach (var interactionSourceState in interactionSourceStates) {
    // ...
}
```

<span data-ttu-id="bfd57-281">Ogni *InteractionSourceState* restituito rappresenta un'origine interazione nel momento corrente.</span><span class="sxs-lookup"><span data-stu-id="bfd57-281">Each *InteractionSourceState* you get back represents an interaction source at the current moment in time.</span></span> <span data-ttu-id="bfd57-282">*InteractionSourceState* espone informazioni come:</span><span class="sxs-lookup"><span data-stu-id="bfd57-282">The *InteractionSourceState* exposes info such as:</span></span>
* <span data-ttu-id="bfd57-283">Quali [tipi di presse](../../design/motion-controllers.md) si verificano (Select/menu/afferrare/touchpad/levetta)</span><span class="sxs-lookup"><span data-stu-id="bfd57-283">Which [kinds of presses](../../design/motion-controllers.md) are occurring (Select/Menu/Grasp/Touchpad/Thumbstick)</span></span>

   ```cs
   if (interactionSourceState.selectPressed) {
       // ...
   }
   ```
* <span data-ttu-id="bfd57-284">Altri dati specifici per i controller di movimento, come le coordinate XY di touchpad e/o levetta e lo stato toccato</span><span class="sxs-lookup"><span data-stu-id="bfd57-284">Other data specific to motion controllers, such the touchpad and/or thumbstick's XY coordinates and touched state</span></span>

   ```cs
   if (interactionSourceState.touchpadTouched && interactionSourceState.touchpadPosition.x > 0.5) {
       // ...
   }
   ```

* <span data-ttu-id="bfd57-285">InteractionSourceKind per verificare se l'origine è una mano o un controller di movimento</span><span class="sxs-lookup"><span data-stu-id="bfd57-285">The InteractionSourceKind to know if the source is a hand or a motion controller</span></span>

   ```cs
   if (interactionSourceState.source.kind == InteractionSourceKind.Hand) {
       // ...
   }
   ```

### <a name="polling-for-forward-predicted-rendering-poses"></a><span data-ttu-id="bfd57-286">Polling per le pose di rendering con stima avanzata</span><span class="sxs-lookup"><span data-stu-id="bfd57-286">Polling for forward-predicted rendering poses</span></span>

* <span data-ttu-id="bfd57-287">Quando si esegue il polling per i dati di origine dell'interazione da mani e controller, le pose ricevute sono le pose stimate in avanti per il momento in cui i fotoni del frame raggiungono gli occhi dell'utente.</span><span class="sxs-lookup"><span data-stu-id="bfd57-287">When polling for interaction source data from hands and controllers, the poses you get are forward-predicted poses for the moment in time when this frame's photons will reach the user's eyes.</span></span>  <span data-ttu-id="bfd57-288">Queste pose con stima avanzata vengono usate in modo ottimale per il **rendering** del controller o di un oggetto mantenuto per ogni frame.</span><span class="sxs-lookup"><span data-stu-id="bfd57-288">These forward-predicted poses are best used for **rendering** the controller or a held object each frame.</span></span>  <span data-ttu-id="bfd57-289">Se si fa riferimento a una determinata pressione o rilascio con il controller, questo sarà più accurato se si usano le API degli eventi cronologici descritte di seguito.</span><span class="sxs-lookup"><span data-stu-id="bfd57-289">If you are targeting a given press or release with the controller, that will be most accurate if you use the historical event APIs described below.</span></span>

   ```cs
   var sourcePose = interactionSourceState.sourcePose;
   Vector3 sourceGripPosition;
   Quaternion sourceGripRotation;
   if ((sourcePose.TryGetPosition(out sourceGripPosition, InteractionSourceNode.Grip)) &&
       (sourcePose.TryGetRotation(out sourceGripRotation, InteractionSourceNode.Grip))) {
       // ...
   }
   ```

* <span data-ttu-id="bfd57-290">È anche possibile ottenere la formula Head con stima avanzata per il frame corrente.</span><span class="sxs-lookup"><span data-stu-id="bfd57-290">You can also get the forward-predicted head pose for this current frame.</span></span>  <span data-ttu-id="bfd57-291">Come per la posa di origine, questa operazione è utile per il **rendering** di un cursore, anche se la scelta di una determinata pressione o rilascio sarà più accurata se si usano le API degli eventi cronologici descritte di seguito.</span><span class="sxs-lookup"><span data-stu-id="bfd57-291">As with the source pose, this is useful for **rendering** a cursor, although targeting a given press or release will be most accurate if you use the historical event APIs described below.</span></span>

   ```cs
   var headPose = interactionSourceState.headPose;
   var headRay = new Ray(headPose.position, headPose.forward);
   RaycastHit raycastHit;
   if (Physics.Raycast(headPose.position, headPose.forward, out raycastHit, 10)) {
       var cursorPos = raycastHit.point;
       // ...
   }
   ```

### <a name="handling-interaction-source-events"></a><span data-ttu-id="bfd57-292">Gestione degli eventi di origine interazione</span><span class="sxs-lookup"><span data-stu-id="bfd57-292">Handling interaction source events</span></span>

<span data-ttu-id="bfd57-293">Per gestire gli eventi di input Man mano che si verificano con i dati di posa cronologici accurati, è possibile gestire gli eventi di origine interazione anziché il polling.</span><span class="sxs-lookup"><span data-stu-id="bfd57-293">To handle input events as they happen with their accurate historical pose data, you can handle interaction source events instead of polling.</span></span>

<span data-ttu-id="bfd57-294">Per gestire gli eventi di origine interazione:</span><span class="sxs-lookup"><span data-stu-id="bfd57-294">To handle interaction source events:</span></span>
* <span data-ttu-id="bfd57-295">Eseguire la registrazione per un evento di input *InteractionManager* .</span><span class="sxs-lookup"><span data-stu-id="bfd57-295">Register for a *InteractionManager* input event.</span></span> <span data-ttu-id="bfd57-296">Per ogni tipo di evento di interazione a cui si è interessati, è necessario sottoscriverlo.</span><span class="sxs-lookup"><span data-stu-id="bfd57-296">For each type of interaction event that you are interested in, you need to subscribe to it.</span></span>

   ```cs
   InteractionManager.InteractionSourcePressed += InteractionManager_InteractionSourcePressed;
   ```

* <span data-ttu-id="bfd57-297">Gestire l'evento.</span><span class="sxs-lookup"><span data-stu-id="bfd57-297">Handle the event.</span></span> <span data-ttu-id="bfd57-298">Una volta effettuata la sottoscrizione a un evento di interazione, si otterrà il callback quando appropriato.</span><span class="sxs-lookup"><span data-stu-id="bfd57-298">Once you have subscribed to an interaction event, you will get the callback when appropriate.</span></span> <span data-ttu-id="bfd57-299">Nell'esempio *SourcePressed* , questo sarà dopo che l'origine è stata rilevata e prima che venga rilasciata o persa.</span><span class="sxs-lookup"><span data-stu-id="bfd57-299">In the *SourcePressed* example, this will be after the source was detected and before it is released or lost.</span></span>

   ```cs
   void InteractionManager_InteractionSourceDetected(InteractionSourceDetectedEventArgs args)
       var interactionSourceState = args.state;

       // args.state has information about:
          // targeting head ray at the time when the event was triggered
          // whether the source is pressed or not
          // properties like position, velocity, source loss risk
          // source id (which hand id for example) and source kind like hand, voice, controller or other
   }
   ```

### <a name="how-to-stop-handling-an-event"></a><span data-ttu-id="bfd57-300">Come interrompere la gestione di un evento</span><span class="sxs-lookup"><span data-stu-id="bfd57-300">How to stop handling an event</span></span>

<span data-ttu-id="bfd57-301">È necessario arrestare la gestione di un evento quando non si è più interessati all'evento o si sta eliminando l'oggetto che ha sottoscritto l'evento.</span><span class="sxs-lookup"><span data-stu-id="bfd57-301">You need to stop handling an event when you are no longer interested in the event or you are destroying the object that has subscribed to the event.</span></span> <span data-ttu-id="bfd57-302">Per arrestare la gestione dell'evento, annullare la sottoscrizione all'evento.</span><span class="sxs-lookup"><span data-stu-id="bfd57-302">To stop handling the event, you unsubscribe from the event.</span></span>

```cs
InteractionManager.InteractionSourcePressed -= InteractionManager_InteractionSourcePressed;
```

### <a name="list-of-interaction-source-events"></a><span data-ttu-id="bfd57-303">Elenco di eventi di origine interazione</span><span class="sxs-lookup"><span data-stu-id="bfd57-303">List of interaction source events</span></span>

<span data-ttu-id="bfd57-304">Gli eventi di origine interazione disponibili sono:</span><span class="sxs-lookup"><span data-stu-id="bfd57-304">The available interaction source events are:</span></span>
* <span data-ttu-id="bfd57-305">*InteractionSourceDetected* (l'origine diventa attiva)</span><span class="sxs-lookup"><span data-stu-id="bfd57-305">*InteractionSourceDetected* (source becomes active)</span></span>
* <span data-ttu-id="bfd57-306">*InteractionSourceLost* (diventa inattivo)</span><span class="sxs-lookup"><span data-stu-id="bfd57-306">*InteractionSourceLost* (becomes inactive)</span></span>
* <span data-ttu-id="bfd57-307">*InteractionSourcePressed* (toccare, premere il pulsante o "Select")</span><span class="sxs-lookup"><span data-stu-id="bfd57-307">*InteractionSourcePressed* (tap, button press, or "Select" uttered)</span></span>
* <span data-ttu-id="bfd57-308">*InteractionSourceReleased* (fine di un tocco, pulsante rilasciato o fine di "Select" pronunciata)</span><span class="sxs-lookup"><span data-stu-id="bfd57-308">*InteractionSourceReleased* (end of a tap, button released, or end of "Select" uttered)</span></span>
* <span data-ttu-id="bfd57-309">*InteractionSourceUpdated* (sposta o modifica in altro modo lo stato)</span><span class="sxs-lookup"><span data-stu-id="bfd57-309">*InteractionSourceUpdated* (moves or otherwise changes some state)</span></span>

### <a name="events-for-historical-targeting-poses-that-most-accurately-match-a-press-or-release"></a><span data-ttu-id="bfd57-310">Gli eventi per il targeting cronologico rappresentano la corrispondenza più accurata tra una stampa o una versione</span><span class="sxs-lookup"><span data-stu-id="bfd57-310">Events for historical targeting poses that most accurately match a press or release</span></span>

<span data-ttu-id="bfd57-311">Le API di polling descritte in precedenza forniscono le pose previste dall'app.</span><span class="sxs-lookup"><span data-stu-id="bfd57-311">The polling APIs described earlier give your app forward-predicted poses.</span></span>  <span data-ttu-id="bfd57-312">Anche se queste pose stimate sono ideali per il rendering del controller o di un oggetto palmare virtuale, le pose future non sono ottimali per la destinazione, per due motivi principali:</span><span class="sxs-lookup"><span data-stu-id="bfd57-312">While those predicted poses are best for rendering the controller or a virtual handheld object, future poses are not optimal for targeting, for two key reasons:</span></span>
* <span data-ttu-id="bfd57-313">Quando l'utente preme un pulsante su un controller, è possibile che si verifichino 20ms di latenza wireless su Bluetooth prima che il sistema riceva la pressione.</span><span class="sxs-lookup"><span data-stu-id="bfd57-313">When the user presses a button on a controller, there can be about 20ms of wireless latency over Bluetooth before the system receives the press.</span></span>
* <span data-ttu-id="bfd57-314">Quindi, se si usa una formula con stima di avanzamento, è possibile applicare un altro 20ms di stima in diretta per individuare l'ora in cui i fotoni del frame corrente raggiungono gli occhi dell'utente.</span><span class="sxs-lookup"><span data-stu-id="bfd57-314">Then, if you are using a forward-predicted pose, there would be another 10-20ms of forward prediction applied to target the time when the current frame's photons will reach the user's eyes.</span></span>

<span data-ttu-id="bfd57-315">Questo significa che il polling fornisce una posizione di origine o una posizione Head che è 30-40ms in uscita dal punto in cui si è verificata l'intestazione e le mani dell'utente.</span><span class="sxs-lookup"><span data-stu-id="bfd57-315">This means that polling gives you a source pose or head pose that is 30-40ms forward from where the user's head and hands actually were back when the press or release happened.</span></span>  <span data-ttu-id="bfd57-316">Per l'input della mano HoloLens, anche se non si verifica alcun ritardo di trasmissione wireless, si verifica un ritardo di elaborazione simile per rilevare la pressione.</span><span class="sxs-lookup"><span data-stu-id="bfd57-316">For HoloLens hand input, while there's no wireless transmission delay, there is a similar processing delay to detect the press.</span></span>

<span data-ttu-id="bfd57-317">Per definire la destinazione in modo accurato in base all'intento originale dell'utente per la pressione di un controller o una mano, è necessario usare la funzione di origine o di intestazione di origine cronologica da tale evento di input *InteractionSourcePressed* o *InteractionSourceReleased* .</span><span class="sxs-lookup"><span data-stu-id="bfd57-317">To accurately target based on the user's original intent for a hand or controller press, you should use the historical source pose or head pose from that *InteractionSourcePressed* or *InteractionSourceReleased* input event.</span></span>

<span data-ttu-id="bfd57-318">È possibile fare riferimento a una stampa o a una versione con dati di posa cronologici dall'Head dell'utente o dal controller:</span><span class="sxs-lookup"><span data-stu-id="bfd57-318">You can target a press or release with historical pose data from the user's head or their controller:</span></span>
* <span data-ttu-id="bfd57-319">Il primo posto nel momento in cui [si è verificato](../../design/gaze-and-commit.md) un movimento o un controller, che può essere **usato per definire** la scelta dell'utente:</span><span class="sxs-lookup"><span data-stu-id="bfd57-319">The head pose at the moment in time when a gesture or controller press occurred, which can be used for **targeting** to determine what the user was [gazing](../../design/gaze-and-commit.md) at:</span></span>

   ```cs
   void InteractionManager_InteractionSourcePressed(InteractionSourcePressedEventArgs args) {
       var interactionSourceState = args.state;
       var headPose = interactionSourceState.headPose;
       RaycastHit raycastHit;
       if (Physics.Raycast(headPose.position, headPose.forward, out raycastHit, 10)) {
           var targetObject = raycastHit.collider.gameObject;
           // ...
       }
   }
   ```

* <span data-ttu-id="bfd57-320">La posizione di origine nel momento in cui si è verificata la pressione di un controller di movimento, che può essere **usata per determinare** l'elemento che l'utente stava puntando al controller.</span><span class="sxs-lookup"><span data-stu-id="bfd57-320">The source pose at the moment in time when a motion controller press occurred, which can be used for **targeting** to determine what the user was pointing the controller at.</span></span>  <span data-ttu-id="bfd57-321">Si tratta dello stato del controller che ha riscontrato la pressione.</span><span class="sxs-lookup"><span data-stu-id="bfd57-321">This will be the state of the controller that experienced the press.</span></span>  <span data-ttu-id="bfd57-322">Se si esegue il rendering del controller stesso, è possibile richiedere la presenza del puntatore anziché il grip, per sparare al raggio di destinazione da quello che l'utente considererà il suggerimento naturale del controller sottoposto a rendering:</span><span class="sxs-lookup"><span data-stu-id="bfd57-322">If you are rendering the controller itself, you can request the pointer pose rather than the grip pose, to shoot the targeting ray from what the user will consider the natural tip of that rendered controller:</span></span>

   ```cs
   void InteractionManager_InteractionSourcePressed(InteractionSourcePressedEventArgs args)
   {
       var interactionSourceState = args.state;
       var sourcePose = interactionSourceState.sourcePose;
       Vector3 sourceGripPosition;
       Quaternion sourceGripRotation;
       if ((sourcePose.TryGetPosition(out sourceGripPosition, InteractionSourceNode.Pointer)) &&
           (sourcePose.TryGetRotation(out sourceGripRotation, InteractionSourceNode.Pointer))) {
           RaycastHit raycastHit;
           if (Physics.Raycast(sourceGripPosition, sourceGripRotation * Vector3.forward, out raycastHit, 10)) {
               var targetObject = raycastHit.collider.gameObject;
               // ...
           }
       }
   }
   ```

### <a name="event-handlers-example"></a><span data-ttu-id="bfd57-323">Esempio di gestori eventi</span><span class="sxs-lookup"><span data-stu-id="bfd57-323">Event handlers example</span></span>

```cs
using UnityEngine.XR.WSA.Input;

void Start()
{
    InteractionManager.InteractionSourceDetected += InteractionManager_InteractionSourceDetected;
    InteractionManager.InteractionSourceLost += InteractionManager_InteractionSourceLost;
    InteractionManager.InteractionSourcePressed += InteractionManager_InteractionSourcePressed;
    InteractionManager.InteractionSourceReleased += InteractionManager_InteractionSourceReleased;
    InteractionManager.InteractionSourceUpdated += InteractionManager_InteractionSourceUpdated;
}

void OnDestroy()
{
    InteractionManager.InteractionSourceDetected -= InteractionManager_InteractionSourceDetected;
    InteractionManager.InteractionSourceLost -= InteractionManager_InteractionSourceLost;
    InteractionManager.InteractionSourcePressed -= InteractionManager_InteractionSourcePressed;
    InteractionManager.InteractionSourceReleased -= InteractionManager_InteractionSourceReleased;
    InteractionManager.InteractionSourceUpdated -= InteractionManager_InteractionSourceUpdated;
}

void InteractionManager_InteractionSourceDetected(InteractionSourceDetectedEventArgs args)
{
    // Source was detected
    // args.state has the current state of the source including id, position, kind, etc.
}

void InteractionManager_InteractionSourceLost(InteractionSourceLostEventArgs state)
{
    // Source was lost. This will be after a SourceDetected event and no other events for this
    // source id will occur until it is Detected again
    // args.state has the current state of the source including id, position, kind, etc.
}

void InteractionManager_InteractionSourcePressed(InteractionSourcePressedEventArgs state)
{
    // Source was pressed. This will be after the source was detected and before it is
    // released or lost
    // args.state has the current state of the source including id, position, kind, etc.
}

void InteractionManager_InteractionSourceReleased(InteractionSourceReleasedEventArgs state)
{
    // Source was released. The source would have been detected and pressed before this point.
    // This event will not fire if the source is lost
    // args.state has the current state of the source including id, position, kind, etc.
}

void InteractionManager_InteractionSourceUpdated(InteractionSourceUpdatedEventArgs state)
{
    // Source was updated. The source would have been detected before this point
    // args.state has the current state of the source including id, position, kind, etc.
}
```

## <a name="high-level-composite-gesture-apis-gesturerecognizer"></a><span data-ttu-id="bfd57-324">API per movimenti compositi di alto livello (GestureRecognizer)</span><span class="sxs-lookup"><span data-stu-id="bfd57-324">High-level composite gesture APIs (GestureRecognizer)</span></span>

<span data-ttu-id="bfd57-325">**Spazio dei nomi:** *UnityEngine. XR. WSA. input*</span><span class="sxs-lookup"><span data-stu-id="bfd57-325">**Namespace:** *UnityEngine.XR.WSA.Input*</span></span><br>
<span data-ttu-id="bfd57-326">**Tipi**: *GestureRecognizer*, *GestureSettings*, *InteractionSourceKind*</span><span class="sxs-lookup"><span data-stu-id="bfd57-326">**Types**: *GestureRecognizer*, *GestureSettings*, *InteractionSourceKind*</span></span>

<span data-ttu-id="bfd57-327">L'app può anche riconoscere movimenti compositi di livello superiore per le origini di input spaziali, i movimenti di tocco, di manipolazione e di navigazione.</span><span class="sxs-lookup"><span data-stu-id="bfd57-327">Your app can also recognize higher-level composite gestures for spatial input sources, Tap, Hold, Manipulation and Navigation gestures.</span></span> <span data-ttu-id="bfd57-328">È possibile riconoscere questi movimenti compositi tra [le mani](../../design/gaze-and-commit.md#composite-gestures) e i [controller di movimento](../../design/motion-controllers.md) usando l'oggetto GestureRecognizer.</span><span class="sxs-lookup"><span data-stu-id="bfd57-328">You can recognize these composite gestures across both [hands](../../design/gaze-and-commit.md#composite-gestures) and [motion controllers](../../design/motion-controllers.md) using the GestureRecognizer.</span></span>

<span data-ttu-id="bfd57-329">Ogni evento di movimento nell'oggetto GestureRecognizer fornisce SourceKind per l'input, nonché il raggio Head di destinazione al momento dell'evento.</span><span class="sxs-lookup"><span data-stu-id="bfd57-329">Each Gesture event on the GestureRecognizer provides the SourceKind for the input as well as the targeting head ray at the time of the event.</span></span> <span data-ttu-id="bfd57-330">Alcuni eventi forniscono informazioni aggiuntive specifiche del contesto.</span><span class="sxs-lookup"><span data-stu-id="bfd57-330">Some events provide additional context specific information.</span></span>

<span data-ttu-id="bfd57-331">Sono necessari solo pochi passaggi per acquisire i movimenti usando un riconoscitore di movimento:</span><span class="sxs-lookup"><span data-stu-id="bfd57-331">There are only a few steps required to capture gestures using a Gesture Recognizer:</span></span>
1. <span data-ttu-id="bfd57-332">Creare un nuovo riconoscitore di movimento</span><span class="sxs-lookup"><span data-stu-id="bfd57-332">Create a new Gesture Recognizer</span></span>
2. <span data-ttu-id="bfd57-333">Specificare i movimenti da controllare</span><span class="sxs-lookup"><span data-stu-id="bfd57-333">Specify which gestures to watch for</span></span>
3. <span data-ttu-id="bfd57-334">Sottoscrivere gli eventi per questi movimenti</span><span class="sxs-lookup"><span data-stu-id="bfd57-334">Subscribe to events for those gestures</span></span>
4. <span data-ttu-id="bfd57-335">Avviare l'acquisizione di movimenti</span><span class="sxs-lookup"><span data-stu-id="bfd57-335">Start capturing gestures</span></span>

### <a name="create-a-new-gesture-recognizer"></a><span data-ttu-id="bfd57-336">Creare un nuovo riconoscitore di movimento</span><span class="sxs-lookup"><span data-stu-id="bfd57-336">Create a new Gesture Recognizer</span></span>

<span data-ttu-id="bfd57-337">Per utilizzare l'oggetto *GestureRecognizer*, è necessario avere creato un oggetto *GestureRecognizer*:</span><span class="sxs-lookup"><span data-stu-id="bfd57-337">To use the *GestureRecognizer*, you must have created a *GestureRecognizer*:</span></span>

```cs
GestureRecognizer recognizer = new GestureRecognizer();
```

### <a name="specify-which-gestures-to-watch-for"></a><span data-ttu-id="bfd57-338">Specificare i movimenti da controllare</span><span class="sxs-lookup"><span data-stu-id="bfd57-338">Specify which gestures to watch for</span></span>

<span data-ttu-id="bfd57-339">Specificare i movimenti a cui si è interessati tramite *SetRecognizableGestures ()*:</span><span class="sxs-lookup"><span data-stu-id="bfd57-339">Specify which gestures you are interested in via *SetRecognizableGestures()*:</span></span>

```cs
recognizer.SetRecognizableGestures(GestureSettings.Tap | GestureSettings.Hold);
```

### <a name="subscribe-to-events-for-those-gestures"></a><span data-ttu-id="bfd57-340">Sottoscrivere gli eventi per questi movimenti</span><span class="sxs-lookup"><span data-stu-id="bfd57-340">Subscribe to events for those gestures</span></span>

<span data-ttu-id="bfd57-341">Sottoscrivere gli eventi per i movimenti a cui si è interessati.</span><span class="sxs-lookup"><span data-stu-id="bfd57-341">Subscribe to events for the gestures you are interested in.</span></span>

```cs
void Start()
{
    recognizer.Tapped += GestureRecognizer_Tapped;
    recognizer.HoldStarted += GestureRecognizer_HoldStarted;
    recognizer.HoldCompleted += GestureRecognizer_HoldCompleted;
    recognizer.HoldCanceled += GestureRecognizer_HoldCanceled;
}
```

>[!NOTE]
><span data-ttu-id="bfd57-342">I movimenti di spostamento e manipolazione si escludono a vicenda in un'istanza di un oggetto *GestureRecognizer*.</span><span class="sxs-lookup"><span data-stu-id="bfd57-342">Navigation and Manipulation gestures are mutually exclusive on an instance of a *GestureRecognizer*.</span></span>

### <a name="start-capturing-gestures"></a><span data-ttu-id="bfd57-343">Avviare l'acquisizione di movimenti</span><span class="sxs-lookup"><span data-stu-id="bfd57-343">Start capturing gestures</span></span>

<span data-ttu-id="bfd57-344">Per impostazione predefinita, un oggetto *GestureRecognizer* non monitora l'input fino a quando non viene chiamato *StartCapturingGestures ()* .</span><span class="sxs-lookup"><span data-stu-id="bfd57-344">By default, a *GestureRecognizer* does not monitor input until *StartCapturingGestures()* is called.</span></span> <span data-ttu-id="bfd57-345">È possibile che venga generato un evento di movimento dopo che è stato chiamato *StopCapturingGestures ()* se l'input è stato eseguito prima del frame in cui è stato elaborato *StopCapturingGestures ()* .</span><span class="sxs-lookup"><span data-stu-id="bfd57-345">It is possible that a gesture event may be generated after *StopCapturingGestures()* is called if input was performed before the frame where *StopCapturingGestures()* was processed.</span></span> <span data-ttu-id="bfd57-346">L'oggetto *GestureRecognizer* ricorda se è stato acceso o disattivato durante il frame precedente in cui si è effettivamente verificato il movimento ed è quindi affidabile per avviare e arrestare il monitoraggio dei movimenti in base alla destinazione dello sguardo del frame.</span><span class="sxs-lookup"><span data-stu-id="bfd57-346">The *GestureRecognizer* will remember whether it was on or off during the previous frame in which the gesture actually occurred, and so it is reliable to start and stop gesture monitoring based on this frame's gaze targeting.</span></span>

```cs
recognizer.StartCapturingGestures();
```

### <a name="stop-capturing-gestures"></a><span data-ttu-id="bfd57-347">Interrompi acquisizione movimenti</span><span class="sxs-lookup"><span data-stu-id="bfd57-347">Stop capturing gestures</span></span>

<span data-ttu-id="bfd57-348">Per arrestare il riconoscimento del movimento:</span><span class="sxs-lookup"><span data-stu-id="bfd57-348">To stop gesture recognition:</span></span>

```cs
recognizer.StopCapturingGestures();
```

### <a name="removing-a-gesture-recognizer"></a><span data-ttu-id="bfd57-349">Rimozione di un riconoscimento di movimento</span><span class="sxs-lookup"><span data-stu-id="bfd57-349">Removing a gesture recognizer</span></span>

<span data-ttu-id="bfd57-350">Ricordarsi di annullare la sottoscrizione agli eventi sottoscritti prima di eliminare un oggetto *GestureRecognizer* .</span><span class="sxs-lookup"><span data-stu-id="bfd57-350">Remember to unsubscribe from subscribed events before destroying a *GestureRecognizer* object.</span></span>

```cs
void OnDestroy()
{
    recognizer.Tapped -= GestureRecognizer_Tapped;
    recognizer.HoldStarted -= GestureRecognizer_HoldStarted;
    recognizer.HoldCompleted -= GestureRecognizer_HoldCompleted;
    recognizer.HoldCanceled -= GestureRecognizer_HoldCanceled;
}
```

## <a name="rendering-the-motion-controller-model-in-unity"></a><span data-ttu-id="bfd57-351">Rendering del modello di controller di movimento in Unity</span><span class="sxs-lookup"><span data-stu-id="bfd57-351">Rendering the motion controller model in Unity</span></span>

<span data-ttu-id="bfd57-352">![Modello e teleporting del controller di movimento](images/motioncontrollertest-teleport-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="bfd57-352">![Motion Controller model and teleportation](images/motioncontrollertest-teleport-1000px.png)</span></span><br>
<span data-ttu-id="bfd57-353">*Modello e teleporting del controller di movimento*</span><span class="sxs-lookup"><span data-stu-id="bfd57-353">*Motion controller model and teleportation*</span></span>

<span data-ttu-id="bfd57-354">Per eseguire il rendering dei controller di movimento nell'app che corrispondono ai controller fisici che gli utenti mantengono e si articolano con la pressione di vari pulsanti, è possibile usare la **prefabbricazione MotionController** nel [Toolkit di realtà mista](https://github.com/Microsoft/MixedRealityToolkit-Unity/).</span><span class="sxs-lookup"><span data-stu-id="bfd57-354">To render motion controllers in your app that match the physical controllers your users are holding and articulate as various buttons are pressed, you can use the **MotionController prefab** in the [Mixed Reality Toolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity/).</span></span>  <span data-ttu-id="bfd57-355">Questa prefabbricata carica dinamicamente il modello glTF corretto in fase di esecuzione dal driver del controller di movimento installato dal sistema.</span><span class="sxs-lookup"><span data-stu-id="bfd57-355">This prefab dynamically loads the correct glTF model at runtime from the system's installed motion controller driver.</span></span>  <span data-ttu-id="bfd57-356">È importante caricare i modelli in modo dinamico, anziché importarli manualmente nell'editor, in modo che l'app visualizzi modelli 3D fisicamente accurati per i controller correnti e futuri che possono avere gli utenti.</span><span class="sxs-lookup"><span data-stu-id="bfd57-356">It's important to load these models dynamically rather than importing them manually in the editor, so that your app will show physically accurate 3D models for any current and future controllers your users may have.</span></span>

1. <span data-ttu-id="bfd57-357">Seguire le istruzioni [Introduzione](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/GettingStarted.md) per scaricare il Toolkit di realtà mista e aggiungerlo al progetto Unity.</span><span class="sxs-lookup"><span data-stu-id="bfd57-357">Follow the [Getting Started](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/GettingStarted.md) instructions to download the Mixed Reality Toolkit and add it to your Unity project.</span></span>
2. <span data-ttu-id="bfd57-358">Se la fotocamera è stata sostituita con la prefabbricata *MixedRealityCameraParent* come parte del Introduzione passaggi, è possibile iniziare.</span><span class="sxs-lookup"><span data-stu-id="bfd57-358">If you replaced your camera with the *MixedRealityCameraParent* prefab as part of the Getting Started steps, you're good to go!</span></span>  <span data-ttu-id="bfd57-359">Il prefabbricato include il rendering del controller di movimento.</span><span class="sxs-lookup"><span data-stu-id="bfd57-359">That prefab includes motion controller rendering.</span></span>  <span data-ttu-id="bfd57-360">In caso contrario, aggiungere *assets/HoloToolkit/input/precasers/MotionControllers. prefabbricate* nella scena dal riquadro progetto.</span><span class="sxs-lookup"><span data-stu-id="bfd57-360">Otherwise, add *Assets/HoloToolkit/Input/Prefabs/MotionControllers.prefab* into your scene from the Project pane.</span></span>  <span data-ttu-id="bfd57-361">È opportuno aggiungere tale prefabbricato come elemento figlio di qualsiasi oggetto padre utilizzato per spostare la fotocamera quando l'utente esegue il teleportamento all'interno della scena, in modo che i controller siano insieme all'utente.</span><span class="sxs-lookup"><span data-stu-id="bfd57-361">You'll want to add that prefab as a child of whatever parent object you use to move the camera around when the user teleports within your scene, so that the controllers come along with the user.</span></span>  <span data-ttu-id="bfd57-362">Se l'app non implica il Teleporting, è sufficiente aggiungere il prefabbricato alla radice della scena.</span><span class="sxs-lookup"><span data-stu-id="bfd57-362">If your app does not involve teleporting, just add the prefab at the root of your scene.</span></span>

## <a name="throwing-objects"></a><span data-ttu-id="bfd57-363">Generazione di oggetti</span><span class="sxs-lookup"><span data-stu-id="bfd57-363">Throwing objects</span></span>

<span data-ttu-id="bfd57-364">La generazione di oggetti in realtà virtuale è un problema più complesso che può sembrare.</span><span class="sxs-lookup"><span data-stu-id="bfd57-364">Throwing objects in virtual reality is a harder problem then it may at first seem.</span></span> <span data-ttu-id="bfd57-365">Come per la maggior parte delle interazioni basate fisicamente, quando la generazione di un gioco agisce in modo imprevisto, è immediatamente evidente e interrompe l'immersione.</span><span class="sxs-lookup"><span data-stu-id="bfd57-365">As with most physically based interactions, when throwing in game acts in an unexpected way, it is immediately obvious and breaks immersion.</span></span> <span data-ttu-id="bfd57-366">Abbiamo dedicato un po' di tempo a comprendere in modo approfondito come rappresentare un comportamento di generazione fisico corretto e avere a disposizione alcune linee guida, abilitate tramite aggiornamenti della piattaforma, che vogliamo condividere con te.</span><span class="sxs-lookup"><span data-stu-id="bfd57-366">We have spent some time thinking deeply about how to represent a physically correct throwing behavior, and have come up with a few guidelines, enabled through updates to our platform, that we would like to share with you.</span></span>

<span data-ttu-id="bfd57-367">È possibile trovare un esempio di come si consiglia di implementare il lancio [qui](https://github.com/keluecke/MixedRealityToolkit-Unity/blob/master/External/Unitypackages/ThrowingStarter.unitypackage).</span><span class="sxs-lookup"><span data-stu-id="bfd57-367">You can find an example of how we recommend to implement throwing [here](https://github.com/keluecke/MixedRealityToolkit-Unity/blob/master/External/Unitypackages/ThrowingStarter.unitypackage).</span></span> <span data-ttu-id="bfd57-368">Questo esempio segue le quattro linee guida seguenti:</span><span class="sxs-lookup"><span data-stu-id="bfd57-368">This sample follows these four guidelines:</span></span>
* <span data-ttu-id="bfd57-369">**Utilizzare la *velocità* del controller invece della posizione**.</span><span class="sxs-lookup"><span data-stu-id="bfd57-369">**Use the controller’s *velocity* instead of position**.</span></span> <span data-ttu-id="bfd57-370">Nell'aggiornamento di novembre di Windows è stata introdotta una modifica nel comportamento quando si [Verifica lo stato di rilevamento posizionale '' approssimativo](../../design/motion-controllers.md#controller-tracking-state).</span><span class="sxs-lookup"><span data-stu-id="bfd57-370">In the November update to Windows, we introduced a change in behavior when in the [''Approximate'' positional tracking state](../../design/motion-controllers.md#controller-tracking-state).</span></span> <span data-ttu-id="bfd57-371">In questo stato, le informazioni sulla velocità del controller continueranno a essere segnalate fino a quando riteniamo che la precisione è elevata, che è spesso più lunga della posizione rimane alta.</span><span class="sxs-lookup"><span data-stu-id="bfd57-371">When in this state, velocity information about the controller will continue to be reported for as long as we believe it is high accuracy, which is often longer than position remains high accuracy.</span></span>
* <span data-ttu-id="bfd57-372">**Incorporare la *velocità angolare* del controller**.</span><span class="sxs-lookup"><span data-stu-id="bfd57-372">**Incorporate the *angular velocity* of the controller**.</span></span> <span data-ttu-id="bfd57-373">Questa logica è interamente contenuta nel `throwing.cs` file nel `GetThrownObjectVelAngVel` metodo statico, all'interno del pacchetto collegato sopra:</span><span class="sxs-lookup"><span data-stu-id="bfd57-373">This logic is all contained in the `throwing.cs` file in the `GetThrownObjectVelAngVel` static method, within the package linked above:</span></span>
   1. <span data-ttu-id="bfd57-374">Poiché viene mantenuta la velocità angolare, l'oggetto generato deve mantenere la stessa velocità angolare del momento in cui si trovava al momento della generazione: `objectAngularVelocity = throwingControllerAngularVelocity;`</span><span class="sxs-lookup"><span data-stu-id="bfd57-374">As angular velocity is conserved, the thrown object must maintain the same angular velocity as it had at the moment of the throw: `objectAngularVelocity = throwingControllerAngularVelocity;`</span></span>
   2. <span data-ttu-id="bfd57-375">Poiché il centro della massa dell'oggetto generato è probabilmente diverso dall'origine della posizione del grip, probabilmente ha una velocità diversa rispetto a quella del controller nel frame di riferimento dell'utente.</span><span class="sxs-lookup"><span data-stu-id="bfd57-375">As the center of mass of the thrown object is likely not at the origin of the grip pose, it likely has a different velocity then that of the controller in the frame of reference of the user.</span></span> <span data-ttu-id="bfd57-376">La parte della velocità dell'oggetto contribuito in questo modo è la velocità tangenziale istantanea del centro della massa dell'oggetto generato intorno all'origine del controller.</span><span class="sxs-lookup"><span data-stu-id="bfd57-376">The portion of the object’s velocity contributed in this way is the instantaneous tangential velocity of the center of mass of the thrown object around the controller origin.</span></span> <span data-ttu-id="bfd57-377">Questa velocità tangenziale è il prodotto incrociato della velocità angolare del controller con il vettore che rappresenta la distanza tra l'origine del controller e il centro della massa dell'oggetto generato.</span><span class="sxs-lookup"><span data-stu-id="bfd57-377">This tangential velocity is the cross product of the angular velocity of the controller with the vector representing the distance between the controller origin and the center of mass of the thrown object.</span></span>

      ```cs
      Vector3 radialVec = thrownObjectCenterOfMass - throwingControllerPos;
      Vector3 tangentialVelocity = Vector3.Cross(throwingControllerAngularVelocity, radialVec);
      ```

   3. <span data-ttu-id="bfd57-378">La velocità totale dell'oggetto generata è quindi la somma della velocità del controller e della velocità tangenziale: `objectVelocity = throwingControllerVelocity + tangentialVelocity;`</span><span class="sxs-lookup"><span data-stu-id="bfd57-378">The total velocity of the thrown object is thus the sum of velocity of the controller and this tangential velocity: `objectVelocity = throwingControllerVelocity + tangentialVelocity;`</span></span>

* <span data-ttu-id="bfd57-379">**Prestare particolare attenzione all' *ora* in cui viene applicata la velocità**.</span><span class="sxs-lookup"><span data-stu-id="bfd57-379">**Pay close attention to the *time* at which we apply the velocity**.</span></span> <span data-ttu-id="bfd57-380">Quando si preme un pulsante, può essere necessario fino a 20ms per l'evento per propagarsi attraverso la tecnologia Bluetooth al sistema operativo.</span><span class="sxs-lookup"><span data-stu-id="bfd57-380">When a button is pressed, it can take up to 20ms for that event to bubble up through Bluetooth to the operating system.</span></span> <span data-ttu-id="bfd57-381">Ciò significa che se si esegue il polling di una modifica dello stato del controller da Pressed a not Pressed o viceversa, il controller pone le informazioni che verranno apportate in precedenza in questa modifica dello stato.</span><span class="sxs-lookup"><span data-stu-id="bfd57-381">This means that if you poll for a controller state change from pressed to not pressed or vice versa, the controller pose information you get with it will actually be ahead of this change in state.</span></span> <span data-ttu-id="bfd57-382">Inoltre, la presentazione del controller presentata dall'API di polling viene stimata in modo da riflettere una probabile situazione nel momento in cui verrà visualizzato il frame, che potrebbe essere più 20ms in futuro.</span><span class="sxs-lookup"><span data-stu-id="bfd57-382">Further, the controller pose presented by our polling API is forward predicted to reflect a likely pose at the time the frame will be displayed which could be more then 20ms in the future.</span></span> <span data-ttu-id="bfd57-383">Questo è ideale per il *rendering* degli oggetti conservati, ma costituisce un problema di tempo per la *destinazione* dell'oggetto durante il calcolo della traiettoria nel momento in cui l'utente ha rilasciato il proprio Throw.</span><span class="sxs-lookup"><span data-stu-id="bfd57-383">This is good for *rendering* held objects, but compounds our time problem for *targeting* the object as we calculate the trajectory for the moment the user released their throw.</span></span> <span data-ttu-id="bfd57-384">Fortunatamente, con l'aggiornamento di novembre, quando viene inviato un evento Unity, ad esempio *InteractionSourcePressed* o *InteractionSourceReleased* , lo stato include i dati cronologici di post di ritorno quando il pulsante è stato effettivamente premuto o rilasciato.</span><span class="sxs-lookup"><span data-stu-id="bfd57-384">Fortunately, with the November update, when a Unity event like *InteractionSourcePressed* or *InteractionSourceReleased* is sent, the state includes the historical pose data from back when the button was actually pressed or released.</span></span>  <span data-ttu-id="bfd57-385">Per ottenere il rendering del controller più accurato e la destinazione del controller durante i lanci, è necessario usare correttamente il polling e la gestione degli eventi, in base alle esigenze:</span><span class="sxs-lookup"><span data-stu-id="bfd57-385">To get the most accurate controller rendering and controller targeting during throws, you must correctly use polling and eventing, as appropriate:</span></span>
   * <span data-ttu-id="bfd57-386">Per il **rendering del controller** ogni frame, l'app deve posizionare il *GameObject* del controller in corrispondenza del controller con stima avanzata per l'ora del fotone del frame corrente.</span><span class="sxs-lookup"><span data-stu-id="bfd57-386">For **controller rendering** each frame, your app should position the controller's *GameObject* at the forward-predicted controller pose for the current frame’s photon time.</span></span>  <span data-ttu-id="bfd57-387">Si ottengono questi dati dalle API di polling Unity, ad esempio *[XR. InputTracking. GetLocalPosition](https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html)* o *[XR. WSA. Input. InteractionManager. GetCurrentReading](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.GetCurrentReading.html)*.</span><span class="sxs-lookup"><span data-stu-id="bfd57-387">You get this data from Unity polling APIs like *[XR.InputTracking.GetLocalPosition](https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html)* or *[XR.WSA.Input.InteractionManager.GetCurrentReading](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.GetCurrentReading.html)*.</span></span>
   * <span data-ttu-id="bfd57-388">Per il **controller che punta** alla stampa o al rilascio, l'app deve Raycast e calcolare le traiettorie in base alla definizione del controller cronologico per l'evento di stampa o di rilascio.</span><span class="sxs-lookup"><span data-stu-id="bfd57-388">For **controller targeting** upon a press or release, your app should raycast and calculate trajectories based on the historical controller pose for that press or release event.</span></span>  <span data-ttu-id="bfd57-389">Si ottengono questi dati dalle API di gestione degli eventi di Unity, ad esempio *[InteractionManager. InteractionSourcePressed](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.InteractionSourcePressed.html)*.</span><span class="sxs-lookup"><span data-stu-id="bfd57-389">You get this data from Unity eventing APIs, like *[InteractionManager.InteractionSourcePressed](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.InteractionSourcePressed.html)*.</span></span>
* <span data-ttu-id="bfd57-390">**Utilizzare la disposizione del grip**.</span><span class="sxs-lookup"><span data-stu-id="bfd57-390">**Use the grip pose**.</span></span> <span data-ttu-id="bfd57-391">La velocità e la velocità angolari vengono segnalate rispetto alla posizione del grip, non alla posizione del puntatore.</span><span class="sxs-lookup"><span data-stu-id="bfd57-391">Angular velocity and velocity are reported relative to the grip pose, not pointer pose.</span></span>

<span data-ttu-id="bfd57-392">La generazione continuerà a migliorare con gli aggiornamenti futuri di Windows e ci si aspetterà di trovare altre informazioni su di essa.</span><span class="sxs-lookup"><span data-stu-id="bfd57-392">Throwing will continue to improve with future Windows updates, and you can expect to find more information on it here.</span></span>

## <a name="gesture-and-motion-controllers-in-mrtk-v2"></a><span data-ttu-id="bfd57-393">Controller movimento e movimento in MRTK V2</span><span class="sxs-lookup"><span data-stu-id="bfd57-393">Gesture and Motion Controllers in MRTK v2</span></span>

<span data-ttu-id="bfd57-394">È possibile accedere a gesture e Motion controller dal gestore di input.</span><span class="sxs-lookup"><span data-stu-id="bfd57-394">You can access gesture and motion controller from the input Manager.</span></span>
* [<span data-ttu-id="bfd57-395">Movimento in MRTK V2</span><span class="sxs-lookup"><span data-stu-id="bfd57-395">Gesture in MRTK v2</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Gestures.html)
* [<span data-ttu-id="bfd57-396">Controller di movimento in MRTK V2</span><span class="sxs-lookup"><span data-stu-id="bfd57-396">Motion Controller in MRTK v2</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Controllers.html)


## <a name="follow-along-with-tutorials"></a><span data-ttu-id="bfd57-397">Seguire le esercitazioni</span><span class="sxs-lookup"><span data-stu-id="bfd57-397">Follow along with tutorials</span></span>

<span data-ttu-id="bfd57-398">Le esercitazioni dettagliate, con esempi di personalizzazione più dettagliati, sono disponibili in Mixed Reality Academy:</span><span class="sxs-lookup"><span data-stu-id="bfd57-398">Step-by-step tutorials, with more detailed customization examples, are available in the Mixed Reality Academy:</span></span>

- [<span data-ttu-id="bfd57-399">Input MR 211: Movimento</span><span class="sxs-lookup"><span data-stu-id="bfd57-399">MR Input 211: Gesture</span></span>](tutorials/holograms-211.md)
- [<span data-ttu-id="bfd57-400">Input MR 213: Controller del movimento</span><span class="sxs-lookup"><span data-stu-id="bfd57-400">MR Input 213: Motion controllers</span></span>](../../deprecated/mixed-reality-213.md)

<span data-ttu-id="bfd57-401">[![Input MR 213-controller di movimento](images/mr213-main-600px.jpg)](https://docs.microsoft.com/windows/mixed-reality/mixed-reality-213)</span><span class="sxs-lookup"><span data-stu-id="bfd57-401">[![MR Input 213 - Motion controller](images/mr213-main-600px.jpg)](https://docs.microsoft.com/windows/mixed-reality/mixed-reality-213)</span></span><br>
<span data-ttu-id="bfd57-402">*Input MR 213-controller di movimento*</span><span class="sxs-lookup"><span data-stu-id="bfd57-402">*MR Input 213 - Motion controller*</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="bfd57-403">Successivo checkpoint di sviluppo</span><span class="sxs-lookup"><span data-stu-id="bfd57-403">Next Development Checkpoint</span></span>

<span data-ttu-id="bfd57-404">Se si sta seguendo il percorso di checkpoint per lo sviluppo con Unity che abbiamo delineato, si stanno esplorando i blocchi predefiniti fondamentali in MRTK.</span><span class="sxs-lookup"><span data-stu-id="bfd57-404">If you're following the Unity development checkpoint journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="bfd57-405">Da qui è possibile passare al blocco predefinito successivo:</span><span class="sxs-lookup"><span data-stu-id="bfd57-405">From here, you can proceed to the next building block:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="bfd57-406">Tracciamento della mano e oculare</span><span class="sxs-lookup"><span data-stu-id="bfd57-406">Hand and eye tracking</span></span>](hand-eye-in-unit.md)

<span data-ttu-id="bfd57-407">In alternativa, passare alle API e funzionalità della piattaforma di realtà mista:</span><span class="sxs-lookup"><span data-stu-id="bfd57-407">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="bfd57-408">Esperienze condivise</span><span class="sxs-lookup"><span data-stu-id="bfd57-408">Shared experiences</span></span>](shared-experiences-in-unity.md)

<span data-ttu-id="bfd57-409">È sempre possibile tornare ai [checkpoint per lo sviluppo con Unity](unity-development-overview.md#2-core-building-blocks) in qualsiasi momento.</span><span class="sxs-lookup"><span data-stu-id="bfd57-409">You can always go back to the [Unity development checkpoints](unity-development-overview.md#2-core-building-blocks) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="bfd57-410">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="bfd57-410">See also</span></span>

* [<span data-ttu-id="bfd57-411">Puntamento con la testa e commit</span><span class="sxs-lookup"><span data-stu-id="bfd57-411">Head-gaze and commit</span></span>](../../design/gaze-and-commit.md)
* [<span data-ttu-id="bfd57-412">Controller del movimento</span><span class="sxs-lookup"><span data-stu-id="bfd57-412">Motion controllers</span></span>](../../design/motion-controllers.md)

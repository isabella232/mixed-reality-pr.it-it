---
title: Movimenti e controller del movimento in Unity
description: Informazioni su come intervenire sullo sguardo in Unity con i movimenti della mano e i controller di movimento.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: movimenti, controller di movimento, Unity, sguardo, input
ms.openlocfilehash: 6b132e56e5d60e59fda53b95328580ed861ce75c
ms.sourcegitcommit: 4bb5544a0c74ac4e9766bab3401c9b30ee170a71
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2020
ms.locfileid: "92638558"
---
# <a name="gestures-and-motion-controllers-in-unity"></a><span data-ttu-id="5a7b1-104">Movimenti e controller del movimento in Unity</span><span class="sxs-lookup"><span data-stu-id="5a7b1-104">Gestures and motion controllers in Unity</span></span>

<span data-ttu-id="5a7b1-105">Ci sono due modi principali per agire sullo [sguardo in Unity](gaze-in-unity.md), [movimenti della mano](../../design/gaze-and-commit.md#composite-gestures) e [controller di movimento](../../design/motion-controllers.md) in HoloLens e HMD immersivi.</span><span class="sxs-lookup"><span data-stu-id="5a7b1-105">There are two key ways to take action on your [gaze in Unity](gaze-in-unity.md), [hand gestures](../../design/gaze-and-commit.md#composite-gestures) and [motion controllers](../../design/motion-controllers.md) in HoloLens and Immersive HMD.</span></span> <span data-ttu-id="5a7b1-106">È possibile accedere ai dati per entrambe le origini dell'input spaziale tramite le stesse API in Unity.</span><span class="sxs-lookup"><span data-stu-id="5a7b1-106">You access the data for both sources of spatial input through the same APIs in Unity.</span></span>

<span data-ttu-id="5a7b1-107">Unity offre due modi principali per accedere ai dati di input spaziali per la realtà mista di Windows, le API *input. GetButton/input. getaxis* comuni che funzionano su più SDK di Unity XR e un'API *InteractionManager/GestureRecognizer* specifica della realtà mista di Windows che espone il set completo di dati di input spaziali disponibili.</span><span class="sxs-lookup"><span data-stu-id="5a7b1-107">Unity provides two primary ways to access spatial input data for Windows Mixed Reality, the common *Input.GetButton/Input.GetAxis* APIs that work across multiple Unity XR SDKs, and an *InteractionManager/GestureRecognizer* API specific to Windows Mixed Reality that exposes the full set of spatial input data available.</span></span>

## <a name="unity-buttonaxis-mapping-table"></a><span data-ttu-id="5a7b1-108">Pulsante Unity/tabella di mapping asse</span><span class="sxs-lookup"><span data-stu-id="5a7b1-108">Unity button/axis mapping table</span></span>

<span data-ttu-id="5a7b1-109">Gli ID dei pulsanti e degli assi nella tabella seguente sono supportati nel gestore di input di Unity per i controller di movimento della realtà mista di Windows tramite le API *input. GetButton/getaxis* , mentre la colonna "Windows specific" si riferisce alle proprietà disponibili nel tipo *InteractionSourceState* .</span><span class="sxs-lookup"><span data-stu-id="5a7b1-109">The button and axis IDs in the table below are supported in Unity's Input Manager for Windows Mixed Reality motion controllers through the *Input.GetButton/GetAxis* APIs, while the "Windows MR-specific" column refers to properties available off of the *InteractionSourceState* type.</span></span> <span data-ttu-id="5a7b1-110">Ognuna di queste API è descritta in dettaglio nelle sezioni riportate di seguito.</span><span class="sxs-lookup"><span data-stu-id="5a7b1-110">Each of these APIs are described in detail in the sections below.</span></span>

<span data-ttu-id="5a7b1-111">I mapping degli ID di pulsanti/assi per la realtà mista di Windows in genere corrispondono agli ID dell'asse o del pulsante Oculus.</span><span class="sxs-lookup"><span data-stu-id="5a7b1-111">The button/axis ID mappings for Windows Mixed Reality generally match the Oculus button/axis IDs.</span></span>

<span data-ttu-id="5a7b1-112">I mapping degli ID di pulsanti/assi per la realtà mista di Windows differiscono dai mapping di OpenVR in due modi:</span><span class="sxs-lookup"><span data-stu-id="5a7b1-112">The button/axis ID mappings for Windows Mixed Reality differ from OpenVR's mappings in two ways:</span></span>
1. <span data-ttu-id="5a7b1-113">Il mapping USA ID touchpad distinti da levetta per supportare i controller con ThumbSticks e touchpad.</span><span class="sxs-lookup"><span data-stu-id="5a7b1-113">The mapping uses touchpad IDs that are distinct from thumbstick, to support controllers with both thumbsticks and touchpads.</span></span>
2. <span data-ttu-id="5a7b1-114">Il mapping evita l'overload degli ID dei pulsanti A e X per i pulsanti di menu, in modo da lasciare quelli disponibili per i pulsanti ABXY fisici.</span><span class="sxs-lookup"><span data-stu-id="5a7b1-114">The mapping avoids overloading the A and X button IDs for the Menu buttons, to leave those available for physical ABXY buttons.</span></span>

<table>
<tr>
<th rowspan="2"><span data-ttu-id="5a7b1-115">Input</span><span class="sxs-lookup"><span data-stu-id="5a7b1-115">Input</span></span> </th><th colspan="2"><span data-ttu-id="5a7b1-116"><a href="gestures-and-motion-controllers-in-unity.md#common-unity-apis-inputgetbuttongetaxis">API Unity comuni</a></span><span class="sxs-lookup"><span data-stu-id="5a7b1-116"><a href="gestures-and-motion-controllers-in-unity.md#common-unity-apis-inputgetbuttongetaxis">Common Unity APIs</a></span></span><br /><span data-ttu-id="5a7b1-117">(Input. GetButton/getaxis)</span><span class="sxs-lookup"><span data-stu-id="5a7b1-117">(Input.GetButton/GetAxis)</span></span> </th><th rowspan="2"><span data-ttu-id="5a7b1-118"><a href="gestures-and-motion-controllers-in-unity.md#">API di input specifica di Windows</a></span><span class="sxs-lookup"><span data-stu-id="5a7b1-118"><a href="gestures-and-motion-controllers-in-unity.md#">Windows MR-specific Input API</a></span></span><br /><span data-ttu-id="5a7b1-119">XR. WSA. Input</span><span class="sxs-lookup"><span data-stu-id="5a7b1-119">(XR.WSA.Input)</span></span></th>
</tr><tr>
<th> <span data-ttu-id="5a7b1-120">Mano sinistra</span><span class="sxs-lookup"><span data-stu-id="5a7b1-120">Left hand</span></span> </th><th> <span data-ttu-id="5a7b1-121">A destra</span><span class="sxs-lookup"><span data-stu-id="5a7b1-121">Right hand</span></span></th>
</tr><tr>
<td> <span data-ttu-id="5a7b1-122">Seleziona trigger premuto</span><span class="sxs-lookup"><span data-stu-id="5a7b1-122">Select trigger pressed</span></span> </td><td> <span data-ttu-id="5a7b1-123">AXIS 9 = 1,0</span><span class="sxs-lookup"><span data-stu-id="5a7b1-123">Axis 9 = 1.0</span></span> </td><td> <span data-ttu-id="5a7b1-124">Asse 10 = 1,0</span><span class="sxs-lookup"><span data-stu-id="5a7b1-124">Axis 10 = 1.0</span></span> </td><td> <span data-ttu-id="5a7b1-125">selectPressed</span><span class="sxs-lookup"><span data-stu-id="5a7b1-125">selectPressed</span></span></td>
</tr><tr>
<td> <span data-ttu-id="5a7b1-126">Selezionare il trigger valore analogico</span><span class="sxs-lookup"><span data-stu-id="5a7b1-126">Select trigger analog value</span></span> </td><td> <span data-ttu-id="5a7b1-127">Asse 9</span><span class="sxs-lookup"><span data-stu-id="5a7b1-127">Axis 9</span></span> </td><td> <span data-ttu-id="5a7b1-128">Asse 10</span><span class="sxs-lookup"><span data-stu-id="5a7b1-128">Axis 10</span></span> </td><td> <span data-ttu-id="5a7b1-129">selectPressedAmount</span><span class="sxs-lookup"><span data-stu-id="5a7b1-129">selectPressedAmount</span></span></td>
</tr><tr>
<td> <span data-ttu-id="5a7b1-130">Selezione trigger parzialmente premuto</span><span class="sxs-lookup"><span data-stu-id="5a7b1-130">Select trigger partially pressed</span></span> </td><td> <span data-ttu-id="5a7b1-131">Pulsante 14 <i>(gamepad compat)</i> </span><span class="sxs-lookup"><span data-stu-id="5a7b1-131">Button 14 <i>(gamepad compat)</i> </span></span></td><td> <span data-ttu-id="5a7b1-132">Pulsante 15 <i>(gamepad compat)</i> </span><span class="sxs-lookup"><span data-stu-id="5a7b1-132">Button 15 <i>(gamepad compat)</i> </span></span></td><td> <span data-ttu-id="5a7b1-133">selectPressedAmount &gt; 0,0</span><span class="sxs-lookup"><span data-stu-id="5a7b1-133">selectPressedAmount &gt; 0.0</span></span></td>
</tr><tr>
<td> <span data-ttu-id="5a7b1-134">Pulsante di menu premuto</span><span class="sxs-lookup"><span data-stu-id="5a7b1-134">Menu button pressed</span></span> </td><td> <span data-ttu-id="5a7b1-135">Pulsante 6 \*</span><span class="sxs-lookup"><span data-stu-id="5a7b1-135">Button 6\*</span></span> </td><td> <span data-ttu-id="5a7b1-136">Pulsante 7 \*</span><span class="sxs-lookup"><span data-stu-id="5a7b1-136">Button 7\*</span></span> </td><td> <span data-ttu-id="5a7b1-137">menuPressed</span><span class="sxs-lookup"><span data-stu-id="5a7b1-137">menuPressed</span></span></td>
</tr><tr>
<td> <span data-ttu-id="5a7b1-138">Pulsante grip premuto</span><span class="sxs-lookup"><span data-stu-id="5a7b1-138">Grip button pressed</span></span> </td><td> <span data-ttu-id="5a7b1-139">Asse 11 = 1,0 (nessun valore analogo)</span><span class="sxs-lookup"><span data-stu-id="5a7b1-139">Axis 11 = 1.0 (no analog values)</span></span><br /><span data-ttu-id="5a7b1-140">Pulsante 4 <i>(gamepad compat)</i> </span><span class="sxs-lookup"><span data-stu-id="5a7b1-140">Button 4 <i>(gamepad compat)</i> </span></span></td><td> <span data-ttu-id="5a7b1-141">Asse 12 = 1,0 (nessun valore analogo)</span><span class="sxs-lookup"><span data-stu-id="5a7b1-141">Axis 12 = 1.0 (no analog values)</span></span><br /><span data-ttu-id="5a7b1-142">Pulsante 5 <i>(gamepad compat)</i> </span><span class="sxs-lookup"><span data-stu-id="5a7b1-142">Button 5 <i>(gamepad compat)</i> </span></span></td><td> <span data-ttu-id="5a7b1-143">afferrato</span><span class="sxs-lookup"><span data-stu-id="5a7b1-143">grasped</span></span></td>
</tr><tr>
<td> <span data-ttu-id="5a7b1-144">Levetta X <i>(Left:-1,0, right: 1,0)</i> </span><span class="sxs-lookup"><span data-stu-id="5a7b1-144">Thumbstick X <i>(left: -1.0, right: 1.0)</i> </span></span></td><td> <span data-ttu-id="5a7b1-145">Asse 1</span><span class="sxs-lookup"><span data-stu-id="5a7b1-145">Axis 1</span></span> </td><td> <span data-ttu-id="5a7b1-146">Asse 4</span><span class="sxs-lookup"><span data-stu-id="5a7b1-146">Axis 4</span></span> </td><td> <span data-ttu-id="5a7b1-147">thumbstickPosition. x</span><span class="sxs-lookup"><span data-stu-id="5a7b1-147">thumbstickPosition.x</span></span></td>
</tr><tr>
<td> <span data-ttu-id="5a7b1-148">Levetta Y <i>(Top:-1,0, bottom: 1,0)</i> </span><span class="sxs-lookup"><span data-stu-id="5a7b1-148">Thumbstick Y <i>(top: -1.0, bottom: 1.0)</i> </span></span></td><td> <span data-ttu-id="5a7b1-149">Asse 2</span><span class="sxs-lookup"><span data-stu-id="5a7b1-149">Axis 2</span></span> </td><td> <span data-ttu-id="5a7b1-150">Asse 5</span><span class="sxs-lookup"><span data-stu-id="5a7b1-150">Axis 5</span></span> </td><td> <span data-ttu-id="5a7b1-151">thumbstickPosition. y</span><span class="sxs-lookup"><span data-stu-id="5a7b1-151">thumbstickPosition.y</span></span></td>
</tr><tr>
<td> <span data-ttu-id="5a7b1-152">Levetta premuto</span><span class="sxs-lookup"><span data-stu-id="5a7b1-152">Thumbstick pressed</span></span> </td><td> <span data-ttu-id="5a7b1-153">Pulsante 8</span><span class="sxs-lookup"><span data-stu-id="5a7b1-153">Button 8</span></span> </td><td> <span data-ttu-id="5a7b1-154">Pulsante 9</span><span class="sxs-lookup"><span data-stu-id="5a7b1-154">Button 9</span></span> </td><td> <span data-ttu-id="5a7b1-155">thumbstickPressed</span><span class="sxs-lookup"><span data-stu-id="5a7b1-155">thumbstickPressed</span></span></td>
</tr><tr>
<td> <span data-ttu-id="5a7b1-156">Touchpad X <i>(Left:-1,0, right: 1,0)</i> </span><span class="sxs-lookup"><span data-stu-id="5a7b1-156">Touchpad X <i>(left: -1.0, right: 1.0)</i> </span></span></td><td> <span data-ttu-id="5a7b1-157">Asse 17 \*</span><span class="sxs-lookup"><span data-stu-id="5a7b1-157">Axis 17\*</span></span> </td><td> <span data-ttu-id="5a7b1-158">Asse 19 \*</span><span class="sxs-lookup"><span data-stu-id="5a7b1-158">Axis 19\*</span></span> </td><td> <span data-ttu-id="5a7b1-159">touchpadPosition. x</span><span class="sxs-lookup"><span data-stu-id="5a7b1-159">touchpadPosition.x</span></span></td>
</tr><tr>
<td> <span data-ttu-id="5a7b1-160">Touchpad Y <i>(Top:-1,0, bottom: 1,0)</i> </span><span class="sxs-lookup"><span data-stu-id="5a7b1-160">Touchpad Y <i>(top: -1.0, bottom: 1.0)</i> </span></span></td><td> <span data-ttu-id="5a7b1-161">Asse 18 \*</span><span class="sxs-lookup"><span data-stu-id="5a7b1-161">Axis 18\*</span></span> </td><td> <span data-ttu-id="5a7b1-162">Asse 20 \*</span><span class="sxs-lookup"><span data-stu-id="5a7b1-162">Axis 20\*</span></span> </td><td> <span data-ttu-id="5a7b1-163">touchpadPosition. y</span><span class="sxs-lookup"><span data-stu-id="5a7b1-163">touchpadPosition.y</span></span></td>
</tr><tr>
<td> <span data-ttu-id="5a7b1-164">Tocco touchpad</span><span class="sxs-lookup"><span data-stu-id="5a7b1-164">Touchpad touched</span></span> </td><td> <span data-ttu-id="5a7b1-165">Pulsante 18 \*</span><span class="sxs-lookup"><span data-stu-id="5a7b1-165">Button 18\*</span></span> </td><td> <span data-ttu-id="5a7b1-166">Pulsante 19 \*</span><span class="sxs-lookup"><span data-stu-id="5a7b1-166">Button 19\*</span></span> </td><td> <span data-ttu-id="5a7b1-167">touchpadTouched</span><span class="sxs-lookup"><span data-stu-id="5a7b1-167">touchpadTouched</span></span></td>
</tr><tr>
<td> <span data-ttu-id="5a7b1-168">Touchpad premuto</span><span class="sxs-lookup"><span data-stu-id="5a7b1-168">Touchpad pressed</span></span> </td><td> <span data-ttu-id="5a7b1-169">Pulsante 16 \*</span><span class="sxs-lookup"><span data-stu-id="5a7b1-169">Button 16\*</span></span> </td><td> <span data-ttu-id="5a7b1-170">Pulsante 17 \*</span><span class="sxs-lookup"><span data-stu-id="5a7b1-170">Button 17\*</span></span> </td><td> <span data-ttu-id="5a7b1-171">touchpadPressed</span><span class="sxs-lookup"><span data-stu-id="5a7b1-171">touchpadPressed</span></span></td>
</tr><tr>
<td> <span data-ttu-id="5a7b1-172">6DoF della posa o del puntatore del grip</span><span class="sxs-lookup"><span data-stu-id="5a7b1-172">6DoF grip pose or pointer pose</span></span> </td><td colspan="2"> <span data-ttu-id="5a7b1-173">Solo <i>grip</i> per la posa: <a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html">XR. InputTracking. GetLocalPosition</a></span><span class="sxs-lookup"><span data-stu-id="5a7b1-173"><i>Grip</i> pose only: <a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html">XR.InputTracking.GetLocalPosition</a></span></span><br /><span data-ttu-id="5a7b1-174"><a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalRotation.html">XR. InputTracking.GetLocalRotation</a></span><span class="sxs-lookup"><span data-stu-id="5a7b1-174"><a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalRotation.html">XR.InputTracking.GetLocalRotation</a></span></span></td><td> <span data-ttu-id="5a7b1-175">Passare il <i>grip</i> o il <i>puntatore</i> come argomento: SourceState. sourcePose. TryGetPosition</span><span class="sxs-lookup"><span data-stu-id="5a7b1-175">Pass <i>Grip</i> or <i>Pointer</i> as an argument: sourceState.sourcePose.TryGetPosition</span></span><br /><span data-ttu-id="5a7b1-176">sourceState.sourcePose.TryGetRotation</span><span class="sxs-lookup"><span data-stu-id="5a7b1-176">sourceState.sourcePose.TryGetRotation</span></span><br /></td>
</tr><tr>
<td> <span data-ttu-id="5a7b1-177">Stato di rilevamento</span><span class="sxs-lookup"><span data-stu-id="5a7b1-177">Tracking state</span></span> </td><td colspan="2"> <span data-ttu-id="5a7b1-178"><i>Accuratezza della posizione e rischi per la perdita di codice sorgente solo tramite API specifiche del sig.</i> </span><span class="sxs-lookup"><span data-stu-id="5a7b1-178"><i>Position accuracy and source loss risk only available through MR-specific API</i> </span></span></td><td> <span data-ttu-id="5a7b1-179"><a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourcePose-positionAccuracy.html">sourceState.sourcePose.positionAccuracy</a></span><span class="sxs-lookup"><span data-stu-id="5a7b1-179"><a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourcePose-positionAccuracy.html">sourceState.sourcePose.positionAccuracy</a></span></span><br /><span data-ttu-id="5a7b1-180"><a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourceProperties-sourceLossRisk.html">sourceState. Properties. sourceLossRisk</a></span><span class="sxs-lookup"><span data-stu-id="5a7b1-180"><a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourceProperties-sourceLossRisk.html">sourceState.properties.sourceLossRisk</a></span></span></td>
</tr>
</table>

>[!NOTE]
><span data-ttu-id="5a7b1-181">Questi ID di pulsanti/assi sono diversi dagli ID usati da Unity per OpenVR a causa di conflitti nei mapping usati dai gamepad, Oculus touch e OpenVR.</span><span class="sxs-lookup"><span data-stu-id="5a7b1-181">These button/axis IDs differ from the IDs that Unity uses for OpenVR due to collisions in the mappings used by gamepads, Oculus Touch and OpenVR.</span></span>

### <a name="using-hp-reverb-g2-controllers"></a><span data-ttu-id="5a7b1-182">Uso di controller di HP Reverb G2</span><span class="sxs-lookup"><span data-stu-id="5a7b1-182">Using HP Reverb G2 controllers</span></span>

<span data-ttu-id="5a7b1-183">Se si usano i controller di HP Reverb G2, fare riferimento alla tabella seguente per gli ID dei pulsanti e degli assi.</span><span class="sxs-lookup"><span data-stu-id="5a7b1-183">If you're using the HP Reverb G2 controllers, refer to the table below for button and axis IDs.</span></span>

<table>
<tr>
<th rowspan="2"><span data-ttu-id="5a7b1-184"><a href="https://docs.unity3d.com/ScriptReference/XR.CommonUsages.html">Input</span><span class="sxs-lookup"><span data-stu-id="5a7b1-184"><a href="https://docs.unity3d.com/ScriptReference/XR.CommonUsages.html">Input</span></span> </th><span data-ttu-id="5a7b1-185"><th colspan="2">API Unity comuni</span><span class="sxs-lookup"><span data-stu-id="5a7b1-185"><th colspan="2">Common Unity APIs</span></span></a><br /><span data-ttu-id="5a7b1-186">(Input. GetButton/getaxis)</span><span class="sxs-lookup"><span data-stu-id="5a7b1-186">(Input.GetButton/GetAxis)</span></span> </th><span data-ttu-id="5a7b1-187"><th rowspan="2">API di input di HP Reverb G2</span><span class="sxs-lookup"><span data-stu-id="5a7b1-187"><th rowspan="2">HP Reverb G2 Input API</span></span></a></th>
</tr><tr>
<th> <span data-ttu-id="5a7b1-188">Mano sinistra</span><span class="sxs-lookup"><span data-stu-id="5a7b1-188">Left hand</span></span> </th><th> <span data-ttu-id="5a7b1-189">A destra</span><span class="sxs-lookup"><span data-stu-id="5a7b1-189">Right hand</span></span></th>
</tr><tr>
<td> <span data-ttu-id="5a7b1-190">Primary2DAxis</span><span class="sxs-lookup"><span data-stu-id="5a7b1-190">Primary2DAxis</span></span> </td><td> <span data-ttu-id="5a7b1-191">Asse 1 (X)/asse 2 (Y)</span><span class="sxs-lookup"><span data-stu-id="5a7b1-191">Axis 1 (X) / Axis 2 (Y)</span></span> </td><td> <span data-ttu-id="5a7b1-192">Asse 4 (X)/asse 5 (Y)</span><span class="sxs-lookup"><span data-stu-id="5a7b1-192">Axis 4 (X) / Axis 5(Y)</span></span> </td><td> <span data-ttu-id="5a7b1-193">Levetta</span><span class="sxs-lookup"><span data-stu-id="5a7b1-193">Thumbstick</span></span></td>
</tr><tr>
<td> <span data-ttu-id="5a7b1-194">Trigger premuto</span><span class="sxs-lookup"><span data-stu-id="5a7b1-194">Trigger pressed</span></span> </td><td> <span data-ttu-id="5a7b1-195">Asse 9</span><span class="sxs-lookup"><span data-stu-id="5a7b1-195">Axis 9</span></span> </td><td> <span data-ttu-id="5a7b1-196">Asse 10</span><span class="sxs-lookup"><span data-stu-id="5a7b1-196">Axis 10</span></span> </td><td> <span data-ttu-id="5a7b1-197">Trigger index</span><span class="sxs-lookup"><span data-stu-id="5a7b1-197">Index trigger</span></span></td>
</tr><tr>
<td> <span data-ttu-id="5a7b1-198">Ridimensionamento</span><span class="sxs-lookup"><span data-stu-id="5a7b1-198">Grip</span></span> </td><td> <span data-ttu-id="5a7b1-199">11d asse</span><span class="sxs-lookup"><span data-stu-id="5a7b1-199">Axis 11d</span></span> </td><td> <span data-ttu-id="5a7b1-200">Asse 12</span><span class="sxs-lookup"><span data-stu-id="5a7b1-200">Axis 12</span></span> </td><td> <span data-ttu-id="5a7b1-201">Trigger di grip</span><span class="sxs-lookup"><span data-stu-id="5a7b1-201">Grip trigger</span></span></td>
</tr><tr>
<td> <span data-ttu-id="5a7b1-202">PrimaryButton premuto</span><span class="sxs-lookup"><span data-stu-id="5a7b1-202">PrimaryButton pressed</span></span> </td><td> <span data-ttu-id="5a7b1-203">Pulsante 2</span><span class="sxs-lookup"><span data-stu-id="5a7b1-203">Button 2</span></span> </td><td> <span data-ttu-id="5a7b1-204">Pulsante 0</span><span class="sxs-lookup"><span data-stu-id="5a7b1-204">Button 0</span></span> </td><td> <span data-ttu-id="5a7b1-205">Pulsante di menu premuto</span><span class="sxs-lookup"><span data-stu-id="5a7b1-205">Menu button pressed</span></span></td>
</tr><tr>
<td> <span data-ttu-id="5a7b1-206">SecondaryButton premuto</span><span class="sxs-lookup"><span data-stu-id="5a7b1-206">SecondaryButton pressed</span></span> </td><td> <span data-ttu-id="5a7b1-207">Pulsante 3</span><span class="sxs-lookup"><span data-stu-id="5a7b1-207">Button 3</span></span> </td><td> <span data-ttu-id="5a7b1-208">Pulsante 1</span><span class="sxs-lookup"><span data-stu-id="5a7b1-208">Button 1</span></span> </td><td> <span data-ttu-id="5a7b1-209">Pulsante A/X</span><span class="sxs-lookup"><span data-stu-id="5a7b1-209">A/X button</span></span></td>
</tr><tr>
<td> <span data-ttu-id="5a7b1-210">GripButton</span><span class="sxs-lookup"><span data-stu-id="5a7b1-210">GripButton</span></span> </td><td> <span data-ttu-id="5a7b1-211">Pulsante 4</span><span class="sxs-lookup"><span data-stu-id="5a7b1-211">Button 4</span></span> </td><td> <span data-ttu-id="5a7b1-212">Pulsante 5</span><span class="sxs-lookup"><span data-stu-id="5a7b1-212">Button 5</span></span> </td><td> <span data-ttu-id="5a7b1-213">Trigger di grip</span><span class="sxs-lookup"><span data-stu-id="5a7b1-213">Grip trigger</span></span></td>
</tr><tr>
<td> <span data-ttu-id="5a7b1-214">TriggerButton</span><span class="sxs-lookup"><span data-stu-id="5a7b1-214">TriggerButton</span></span> </td><td> <span data-ttu-id="5a7b1-215">Pulsante 14</span><span class="sxs-lookup"><span data-stu-id="5a7b1-215">Button 14</span></span> </td><td> <span data-ttu-id="5a7b1-216">Pulsante 15</span><span class="sxs-lookup"><span data-stu-id="5a7b1-216">Button 15</span></span> </td><td> <span data-ttu-id="5a7b1-217">Trigger index</span><span class="sxs-lookup"><span data-stu-id="5a7b1-217">Index trigger</span></span></td>
</tr><tr>
</tr>
</table>


## <a name="grip-pose-vs-pointing-pose"></a><span data-ttu-id="5a7b1-218">Posa del grip e puntamento</span><span class="sxs-lookup"><span data-stu-id="5a7b1-218">Grip pose vs. pointing pose</span></span>

<span data-ttu-id="5a7b1-219">La realtà mista di Windows supporta i controller di movimento in diversi fattori di forma, con la progettazione di ogni controller diversa nella relazione tra la posizione della mano dell'utente e la direzione naturale "Avanti" che le app devono usare per puntare durante il rendering del controller.</span><span class="sxs-lookup"><span data-stu-id="5a7b1-219">Windows Mixed Reality supports motion controllers in a variety of form factors, with each controller's design differing in its relationship between the user's hand position and the natural "forward" direction that apps should use for pointing when rendering the controller.</span></span>

<span data-ttu-id="5a7b1-220">Per rappresentare meglio questi controller, esistono due tipi di pose che è possibile esaminare per ogni origine interazione, la **posizione del grip** e la **posizione del puntatore** .</span><span class="sxs-lookup"><span data-stu-id="5a7b1-220">To better represent these controllers, there are two kinds of poses you can investigate for each interaction source, the **grip pose** and the **pointer pose** .</span></span> <span data-ttu-id="5a7b1-221">Sia le coordinate della formula del grip che del puntatore sono espresse da tutte le API Unity nelle coordinate globali di Unity.</span><span class="sxs-lookup"><span data-stu-id="5a7b1-221">Both the grip pose and pointer pose coordinates are expressed by all Unity APIs in global Unity world coordinates.</span></span>

### <a name="grip-pose"></a><span data-ttu-id="5a7b1-222">Pose di grip</span><span class="sxs-lookup"><span data-stu-id="5a7b1-222">Grip pose</span></span>

<span data-ttu-id="5a7b1-223">La posizione del **grip** rappresenta la posizione della Palma di una mano rilevata da un HoloLens o della palma che contiene un controller di movimento.</span><span class="sxs-lookup"><span data-stu-id="5a7b1-223">The **grip pose** represents the location of either the palm of a hand detected by a HoloLens, or the palm holding a motion controller.</span></span>

<span data-ttu-id="5a7b1-224">Negli auricolari immersivi, la disposizione dei grip è la scelta migliore per eseguire **il rendering della mano dell'utente** o di **un oggetto contenuto nella mano** , ad esempio una spada o una pistola.</span><span class="sxs-lookup"><span data-stu-id="5a7b1-224">On immersive headsets, the grip pose is best used to render **the user's hand** or **an object held in the user's hand** , such as a sword or gun.</span></span> <span data-ttu-id="5a7b1-225">La posizione del grip viene usata anche durante la visualizzazione di un controller di movimento, perché il **modello di rendering** fornito da Windows per un controller di movimento usa la posizione del grip come origine e centro di rotazione.</span><span class="sxs-lookup"><span data-stu-id="5a7b1-225">The grip pose is also used when visualizing a motion controller, as the **renderable model** provided by Windows for a motion controller uses the grip pose as its origin and center of rotation.</span></span>

<span data-ttu-id="5a7b1-226">Il grip viene definito in modo specifico come segue:</span><span class="sxs-lookup"><span data-stu-id="5a7b1-226">The grip pose is defined specifically as follows:</span></span>
* <span data-ttu-id="5a7b1-227">**Posizione del grip** : il centro della palma quando si tiene il controller in modo naturale, regolato a sinistra o a destra per centrare la posizione all'interno del grip.</span><span class="sxs-lookup"><span data-stu-id="5a7b1-227">The **grip position** : The palm centroid when holding the controller naturally, adjusted left or right to center the position within the grip.</span></span> <span data-ttu-id="5a7b1-228">Sul controller di movimento per la realtà mista di Windows, questa posizione viene in genere allineata con il pulsante afferra.</span><span class="sxs-lookup"><span data-stu-id="5a7b1-228">On the Windows Mixed Reality motion controller, this position generally aligns with the Grasp button.</span></span>
* <span data-ttu-id="5a7b1-229">L' **asse destro dell'orientamento del grip** : quando si apre completamente la mano per formare una formula a 5 dita piatta, il raggio normale per la Palma (in avanti dal palmo sinistro e viceversa)</span><span class="sxs-lookup"><span data-stu-id="5a7b1-229">The **grip orientation's Right axis** : When you completely open your hand to form a flat 5-finger pose, the ray that is normal to your palm (forward from left palm, backward from right palm)</span></span>
* <span data-ttu-id="5a7b1-230">**Asse di avanzamento dell'orientamento del grip** : quando si chiude parzialmente la mano (come se si utilizzasse il controller), il raggio che punta "in poi" attraverso il tubo formato dalle dita non Thumb.</span><span class="sxs-lookup"><span data-stu-id="5a7b1-230">The **grip orientation's Forward axis** : When you close your hand partially (as if holding the controller), the ray that points "forward" through the tube formed by your non-thumb fingers.</span></span>
* <span data-ttu-id="5a7b1-231">**Asse verticale dell'orientamento del grip** : l'asse verso l'alto implicato dalle definizioni di destra e di avanzamento.</span><span class="sxs-lookup"><span data-stu-id="5a7b1-231">The **grip orientation's Up axis** : The Up axis implied by the Right and Forward definitions.</span></span>

<span data-ttu-id="5a7b1-232">È possibile accedere al grip con l'API di input tra fornitori di Unity ( *[XR). InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html). GetLocalPosition/Rotation* ) o tramite l'API specifica di Windows ( *SourceState. SourcePose. TryGetPosition/Rotation* , che richiede i dati di post per il nodo **grip** ).</span><span class="sxs-lookup"><span data-stu-id="5a7b1-232">You can access the grip pose through either Unity's cross-vendor input API ( *[XR.InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html).GetLocalPosition/Rotation* ) or through the Windows MR-specific API ( *sourceState.sourcePose.TryGetPosition/Rotation* , requesting pose data for the **Grip** node).</span></span>

### <a name="pointer-pose"></a><span data-ttu-id="5a7b1-233">Posa puntatore</span><span class="sxs-lookup"><span data-stu-id="5a7b1-233">Pointer pose</span></span>

<span data-ttu-id="5a7b1-234">Il **puntatore** posizionato rappresenta il suggerimento del controller che punta in futuro.</span><span class="sxs-lookup"><span data-stu-id="5a7b1-234">The **pointer pose** represents the tip of the controller pointing forward.</span></span>

<span data-ttu-id="5a7b1-235">La disposizione del puntatore fornita dal sistema è ideale per Raycast quando si esegue **il rendering del modello di controller** .</span><span class="sxs-lookup"><span data-stu-id="5a7b1-235">The system-provided pointer pose is best used to raycast when you are **rendering the controller model itself** .</span></span> <span data-ttu-id="5a7b1-236">Se si esegue il rendering di un altro oggetto virtuale al posto del controller, ad esempio una pistola virtuale, è necessario puntare con un raggio più naturale per tale oggetto virtuale, ad esempio un raggio che viaggia lungo il barilotto del modello Gun definito dall'app.</span><span class="sxs-lookup"><span data-stu-id="5a7b1-236">If you are rendering some other virtual object in place of the controller, such as a virtual gun, you should point with a ray that is most natural for that virtual object, such as a ray that travels along the barrel of the app-defined gun model.</span></span> <span data-ttu-id="5a7b1-237">Poiché gli utenti possono visualizzare l'oggetto virtuale e non il controller fisico, puntare con l'oggetto virtuale sarà probabilmente più naturale per quelli che usano l'app.</span><span class="sxs-lookup"><span data-stu-id="5a7b1-237">Because users can see the virtual object and not the physical controller, pointing with the virtual object will likely be more natural for those using your app.</span></span>

<span data-ttu-id="5a7b1-238">Attualmente, la posa del puntatore è disponibile in Unity solo tramite l'API specifica di Windows, *sourceState. sourcePose. TryGetPosition/Rotation* , passando *InteractionSourceNode. pointer* come argomento.</span><span class="sxs-lookup"><span data-stu-id="5a7b1-238">Currently, the pointer pose is available in Unity only through the Windows MR-specific API, *sourceState.sourcePose.TryGetPosition/Rotation* , passing in *InteractionSourceNode.Pointer* as the argument.</span></span>

## <a name="controller-tracking-state"></a><span data-ttu-id="5a7b1-239">Stato di rilevamento del controller</span><span class="sxs-lookup"><span data-stu-id="5a7b1-239">Controller tracking state</span></span>

<span data-ttu-id="5a7b1-240">Come gli auricolari, il controller di movimento di realtà mista di Windows non richiede l'installazione di sensori di rilevamento esterni.</span><span class="sxs-lookup"><span data-stu-id="5a7b1-240">Like the headsets, the Windows Mixed Reality motion controller requires no setup of external tracking sensors.</span></span> <span data-ttu-id="5a7b1-241">Il controller viene invece rilevato dai sensori nell'auricolare.</span><span class="sxs-lookup"><span data-stu-id="5a7b1-241">Instead, the controllers are tracked by sensors in the headset itself.</span></span>

<span data-ttu-id="5a7b1-242">Se l'utente sposta i controller fuori dal campo di visualizzazione dell'auricolare, nella maggior parte dei casi Windows continuerà a dedurre le posizioni del controller e le fornirà all'app.</span><span class="sxs-lookup"><span data-stu-id="5a7b1-242">If the user moves the controllers out of the headset's field of view, in most cases Windows will continue to infer controller positions and provide them to the app.</span></span> <span data-ttu-id="5a7b1-243">Quando il controller ha perso il rilevamento visivo per un periodo di tempo sufficiente, le posizioni del controller vengono rilasciate a posizioni di accuratezza approssimativa.</span><span class="sxs-lookup"><span data-stu-id="5a7b1-243">When the controller has lost visual tracking for long enough, the controller's positions will drop to approximate-accuracy positions.</span></span>

<span data-ttu-id="5a7b1-244">A questo punto, il sistema bloccherà il controller all'utente, tenendo traccia della posizione dell'utente mentre si spostano, esponendo comunque il vero orientamento del controller usando i sensori di orientamento interni.</span><span class="sxs-lookup"><span data-stu-id="5a7b1-244">At this point, the system will body-lock the controller to the user, tracking the user's position as they move around, while still exposing the controller's true orientation using its internal orientation sensors.</span></span> <span data-ttu-id="5a7b1-245">Molte app che usano i controller per puntare e attivare gli elementi dell'interfaccia utente possono funzionare normalmente con una precisione approssimativa senza che l'utente abbia notato.</span><span class="sxs-lookup"><span data-stu-id="5a7b1-245">Many apps that use controllers to point at and activate UI elements can operate normally while in approximate accuracy without the user noticing.</span></span>

<span data-ttu-id="5a7b1-246">Il modo migliore per ottenere questo aspetto è provare a eseguire l'operazione.</span><span class="sxs-lookup"><span data-stu-id="5a7b1-246">The best way to get a feel for this is to try it yourself.</span></span> <span data-ttu-id="5a7b1-247">Vedere questo video con esempi di contenuti immersivi che funzionano con i controller di movimento in diversi Stati di rilevamento:</span><span class="sxs-lookup"><span data-stu-id="5a7b1-247">Check out this video with examples of immersive content that works with motion controllers across various tracking states:</span></span>

<br>

 >[!VIDEO https://www.youtube.com/embed/QK_fOFDHj0g]

### <a name="reasoning-about-tracking-state-explicitly"></a><span data-ttu-id="5a7b1-248">Ragionamento sullo stato di rilevamento in modo esplicito</span><span class="sxs-lookup"><span data-stu-id="5a7b1-248">Reasoning about tracking state explicitly</span></span>

<span data-ttu-id="5a7b1-249">Le app che desiderano gestire le posizioni in modo diverso in base allo stato di rilevamento possono andare oltre e controllare le proprietà nello stato del controller, ad esempio *SourceLossRisk* e *PositionAccuracy* :</span><span class="sxs-lookup"><span data-stu-id="5a7b1-249">Apps that wish to treat positions differently based on tracking state may go further and inspect properties on the controller's state, such as *SourceLossRisk* and *PositionAccuracy* :</span></span>

<table>
<tr>
<th> <span data-ttu-id="5a7b1-250">Stato di rilevamento</span><span class="sxs-lookup"><span data-stu-id="5a7b1-250">Tracking state</span></span> </th><th> <span data-ttu-id="5a7b1-251">SourceLossRisk</span><span class="sxs-lookup"><span data-stu-id="5a7b1-251">SourceLossRisk</span></span> </th><th> <span data-ttu-id="5a7b1-252">PositionAccuracy</span><span class="sxs-lookup"><span data-stu-id="5a7b1-252">PositionAccuracy</span></span> </th><th> <span data-ttu-id="5a7b1-253">TryGetPosition</span><span class="sxs-lookup"><span data-stu-id="5a7b1-253">TryGetPosition</span></span></th>
</tr><tr>
<td> <span data-ttu-id="5a7b1-254"><b>Accuratezza elevata</b> </span><span class="sxs-lookup"><span data-stu-id="5a7b1-254"><b>High accuracy</b> </span></span></td><td style="background-color: green; color: white"> <span data-ttu-id="5a7b1-255">&lt; 1,0</span><span class="sxs-lookup"><span data-stu-id="5a7b1-255">&lt; 1.0</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="5a7b1-256">Alto</span><span class="sxs-lookup"><span data-stu-id="5a7b1-256">High</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="5a7b1-257">True</span><span class="sxs-lookup"><span data-stu-id="5a7b1-257">true</span></span></td>
</tr><tr>
<td> <span data-ttu-id="5a7b1-258"><b>Accuratezza elevata (a rischio di perdita)</b> </span><span class="sxs-lookup"><span data-stu-id="5a7b1-258"><b>High accuracy (at risk of losing)</b> </span></span></td><td style="background-color: orange"> <span data-ttu-id="5a7b1-259">= = 1,0</span><span class="sxs-lookup"><span data-stu-id="5a7b1-259">== 1.0</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="5a7b1-260">Alto</span><span class="sxs-lookup"><span data-stu-id="5a7b1-260">High</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="5a7b1-261">True</span><span class="sxs-lookup"><span data-stu-id="5a7b1-261">true</span></span></td>
</tr><tr>
<td> <span data-ttu-id="5a7b1-262"><b>Accuratezza approssimativa</b> </span><span class="sxs-lookup"><span data-stu-id="5a7b1-262"><b>Approximate accuracy</b> </span></span></td><td style="background-color: orange"> <span data-ttu-id="5a7b1-263">= = 1,0</span><span class="sxs-lookup"><span data-stu-id="5a7b1-263">== 1.0</span></span> </td><td style="background-color: orange"> <span data-ttu-id="5a7b1-264">Con approssimazione</span><span class="sxs-lookup"><span data-stu-id="5a7b1-264">Approximate</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="5a7b1-265">True</span><span class="sxs-lookup"><span data-stu-id="5a7b1-265">true</span></span></td>
</tr><tr>
<td> <span data-ttu-id="5a7b1-266"><b>Nessuna posizione</b> </span><span class="sxs-lookup"><span data-stu-id="5a7b1-266"><b>No position</b> </span></span></td><td style="background-color: orange"> <span data-ttu-id="5a7b1-267">= = 1,0</span><span class="sxs-lookup"><span data-stu-id="5a7b1-267">== 1.0</span></span> </td><td style="background-color: orange"> <span data-ttu-id="5a7b1-268">Con approssimazione</span><span class="sxs-lookup"><span data-stu-id="5a7b1-268">Approximate</span></span> </td><td style="background-color: orange"> <span data-ttu-id="5a7b1-269">false</span><span class="sxs-lookup"><span data-stu-id="5a7b1-269">false</span></span></td>
</tr>
</table>

<span data-ttu-id="5a7b1-270">Questi stati di rilevamento del controller di movimento sono definiti come segue:</span><span class="sxs-lookup"><span data-stu-id="5a7b1-270">These motion controller tracking states are defined as follows:</span></span>
* <span data-ttu-id="5a7b1-271">**Accuratezza elevata:** Mentre il controller di movimento si trova all'interno del campo di visualizzazione dell'auricolare, in genere fornisce posizioni con accuratezza elevata, in base al rilevamento visivo.</span><span class="sxs-lookup"><span data-stu-id="5a7b1-271">**High accuracy:** While the motion controller is within the headset's field of view, it will generally provide high-accuracy positions, based on visual tracking.</span></span> <span data-ttu-id="5a7b1-272">Si noti che un controller che sposta temporaneamente il campo di visualizzazione o è temporaneamente nascosto dai sensori dell'auricolare (ad esempio, da parte dell'utente) continuerà a restituire le pose con precisione elevata per un breve periodo di tempo, in base al rilevamento inerziale del controller stesso.</span><span class="sxs-lookup"><span data-stu-id="5a7b1-272">Note that a moving controller that momentarily leaves the field of view or is momentarily obscured from the headset sensors (e.g. by the user's other hand) will continue to return high-accuracy poses for a short time, based on inertial tracking of the controller itself.</span></span>
* <span data-ttu-id="5a7b1-273">**Accuratezza elevata (a rischio di perdita):** Quando l'utente sposta il controller di movimento oltre il bordo del campo di visualizzazione dell'auricolare, l'auricolare non sarà presto in grado di rilevare visivamente la posizione del controller.</span><span class="sxs-lookup"><span data-stu-id="5a7b1-273">**High accuracy (at risk of losing):** When the user moves the motion controller past the edge of the headset's field of view, the headset will soon be unable to visually track the controller's position.</span></span> <span data-ttu-id="5a7b1-274">L'app sa quando il controller ha raggiunto questo limite FOV visualizzando il **SourceLossRisk** REACH 1,0.</span><span class="sxs-lookup"><span data-stu-id="5a7b1-274">The app knows when the controller has reached this FOV boundary by seeing the **SourceLossRisk** reach 1.0.</span></span> <span data-ttu-id="5a7b1-275">A questo punto, l'app può scegliere di sospendere i movimenti del controller che richiedono un flusso costante di pose di qualità molto elevata.</span><span class="sxs-lookup"><span data-stu-id="5a7b1-275">At that point, the app may choose to pause controller gestures that require a steady stream of very high-quality poses.</span></span>
* <span data-ttu-id="5a7b1-276">**Accuratezza approssimativa:** Quando il controller ha perso il rilevamento visivo per un periodo di tempo sufficiente, le posizioni del controller vengono rilasciate a posizioni di accuratezza approssimativa.</span><span class="sxs-lookup"><span data-stu-id="5a7b1-276">**Approximate accuracy:** When the controller has lost visual tracking for long enough, the controller's positions will drop to approximate-accuracy positions.</span></span> <span data-ttu-id="5a7b1-277">A questo punto, il sistema bloccherà il controller all'utente, tenendo traccia della posizione dell'utente mentre si spostano, esponendo comunque il vero orientamento del controller usando i sensori di orientamento interni.</span><span class="sxs-lookup"><span data-stu-id="5a7b1-277">At this point, the system will body-lock the controller to the user, tracking the user's position as they move around, while still exposing the controller's true orientation using its internal orientation sensors.</span></span> <span data-ttu-id="5a7b1-278">Molte app che usano i controller per puntare e attivare gli elementi dell'interfaccia utente possono funzionare normalmente con una precisione approssimativa senza che l'utente ne abbia notato.</span><span class="sxs-lookup"><span data-stu-id="5a7b1-278">Many apps that use controllers to point at and activate UI elements can operate as normal while in approximate accuracy without the user noticing.</span></span> <span data-ttu-id="5a7b1-279">Le app con requisiti di input più pesanti possono scegliere di comprendere questo calo dall'accuratezza **elevata** all'accuratezza **approssimativa** controllando la proprietà **PositionAccuracy** , ad esempio per dare all'utente un hitbox più generoso sulle destinazioni fuori schermo durante questo periodo di tempo.</span><span class="sxs-lookup"><span data-stu-id="5a7b1-279">Apps with heavier input requirements may choose to sense this drop from **High** accuracy to **Approximate** accuracy by inspecting the **PositionAccuracy** property, for example to give the user a more generous hitbox on off-screen targets during this time.</span></span>
* <span data-ttu-id="5a7b1-280">**Nessuna posizione:** Mentre il controller può funzionare con una precisione approssimativa per molto tempo, a volte il sistema sa che anche una posizione bloccata dal corpo non è al momento significativa.</span><span class="sxs-lookup"><span data-stu-id="5a7b1-280">**No position:** While the controller can operate at approximate accuracy for a long time, sometimes the system knows that even a body-locked position is not meaningful at the moment.</span></span> <span data-ttu-id="5a7b1-281">Ad esempio, un controller appena attivato potrebbe non essere mai stato osservato visivamente oppure un utente può arrestare un controller che viene quindi prelevato da qualcun altro.</span><span class="sxs-lookup"><span data-stu-id="5a7b1-281">For example, a controller that was just turned on may have never been observed visually, or a user may put down a controller that's then picked up by someone else.</span></span> <span data-ttu-id="5a7b1-282">In questi casi, il sistema non fornirà alcuna posizione all'app e *TryGetPosition* restituirà false.</span><span class="sxs-lookup"><span data-stu-id="5a7b1-282">At those times, the system will not provide any position to the app, and *TryGetPosition* will return false.</span></span>

## <a name="common-unity-apis-inputgetbuttongetaxis"></a><span data-ttu-id="5a7b1-283">API Unity comuni (input. GetButton/getaxis)</span><span class="sxs-lookup"><span data-stu-id="5a7b1-283">Common Unity APIs (Input.GetButton/GetAxis)</span></span>

<span data-ttu-id="5a7b1-284">**Spazio dei nomi:** *UnityEngine* , *UnityEngine. XR*</span><span class="sxs-lookup"><span data-stu-id="5a7b1-284">**Namespace:** *UnityEngine* , *UnityEngine.XR*</span></span><br>
<span data-ttu-id="5a7b1-285">**Tipi** : *input* , *XR. InputTracking*</span><span class="sxs-lookup"><span data-stu-id="5a7b1-285">**Types** : *Input* , *XR.InputTracking*</span></span>

<span data-ttu-id="5a7b1-286">Unity usa attualmente le API *input. GetButton/input. getaxis* per esporre l'input per [Oculus SDK](https://docs.unity3d.com/Manual/OculusControllers.html), [l'SDK di OpenVR e la](https://docs.unity3d.com/Manual/OpenVRControllers.html) realtà mista di Windows, inclusi i controller hands e Motion.</span><span class="sxs-lookup"><span data-stu-id="5a7b1-286">Unity currently uses its general *Input.GetButton/Input.GetAxis* APIs to expose input for [the Oculus SDK](https://docs.unity3d.com/Manual/OculusControllers.html), [the OpenVR SDK](https://docs.unity3d.com/Manual/OpenVRControllers.html) and Windows Mixed Reality, including hands and motion controllers.</span></span> <span data-ttu-id="5a7b1-287">Se l'app usa queste API per l'input, può supportare facilmente i controller di movimento tra più SDK XR, inclusa la realtà mista di Windows.</span><span class="sxs-lookup"><span data-stu-id="5a7b1-287">If your app uses these APIs for input, it can easily support motion controllers across multiple XR SDKs, including Windows Mixed Reality.</span></span>

### <a name="getting-a-logical-buttons-pressed-state"></a><span data-ttu-id="5a7b1-288">Recupero dello stato premuto di un pulsante logico</span><span class="sxs-lookup"><span data-stu-id="5a7b1-288">Getting a logical button's pressed state</span></span>

<span data-ttu-id="5a7b1-289">Per usare le API di input di Unity generale, si inizia in genere collegando pulsanti e assi ai nomi logici in [Gestione input Unity](https://docs.unity3d.com/Manual/ConventionalGameInput.html), associando un pulsante o gli ID dell'asse a ogni nome.</span><span class="sxs-lookup"><span data-stu-id="5a7b1-289">To use the general Unity input APIs, you'll typically start by wiring up buttons and axes to logical names in the [Unity Input Manager](https://docs.unity3d.com/Manual/ConventionalGameInput.html), binding a button or axis IDs to each name.</span></span> <span data-ttu-id="5a7b1-290">È quindi possibile scrivere codice che fa riferimento a tale nome di pulsante/asse logico.</span><span class="sxs-lookup"><span data-stu-id="5a7b1-290">You can then write code that refers to that logical button/axis name.</span></span>

<span data-ttu-id="5a7b1-291">Ad esempio, per eseguire il mapping del pulsante trigger del controller di movimento sinistro all'azione Invia, passare a **modifica > impostazioni progetto > input** in Unity ed espandere le proprietà della sezione Submit in assi.</span><span class="sxs-lookup"><span data-stu-id="5a7b1-291">For example, to map the left motion controller's trigger button to the Submit action, go to **Edit > Project Settings > Input** within Unity, and expand the properties of the Submit section under Axes.</span></span> <span data-ttu-id="5a7b1-292">Modificare il pulsante **positivo** o la proprietà **pulsante Alt positivo** per leggere il **pulsante del joystick 14** , in questo modo:</span><span class="sxs-lookup"><span data-stu-id="5a7b1-292">Change the **Positive Button** or **Alt Positive Button** property to read **joystick button 14** , like this:</span></span>

<span data-ttu-id="5a7b1-293">![InputManager di Unity](images/unity-input-manager.png)</span><span class="sxs-lookup"><span data-stu-id="5a7b1-293">![Unity's InputManager](images/unity-input-manager.png)</span></span><br>
<span data-ttu-id="5a7b1-294">*Unity InputManager*</span><span class="sxs-lookup"><span data-stu-id="5a7b1-294">*Unity InputManager*</span></span>

<span data-ttu-id="5a7b1-295">Lo script può quindi verificare la presenza di un'azione di invio tramite *input. GetButton* :</span><span class="sxs-lookup"><span data-stu-id="5a7b1-295">Your script can then check for the Submit action using *Input.GetButton* :</span></span>

```cs
if (Input.GetButton("Submit"))
{
  // ...
}
```
<span data-ttu-id="5a7b1-296">È possibile aggiungere più pulsanti logici modificando la proprietà **size** in **assi** .</span><span class="sxs-lookup"><span data-stu-id="5a7b1-296">You can add more logical buttons by changing the **Size** property under **Axes** .</span></span>

### <a name="getting-a-physical-buttons-pressed-state-directly"></a><span data-ttu-id="5a7b1-297">Ottenere direttamente lo stato premuto di un pulsante fisico</span><span class="sxs-lookup"><span data-stu-id="5a7b1-297">Getting a physical button's pressed state directly</span></span>

<span data-ttu-id="5a7b1-298">È anche possibile accedere manualmente ai pulsanti con il nome completo, usando *input. GetKey* :</span><span class="sxs-lookup"><span data-stu-id="5a7b1-298">You can also access buttons manually by their fully-qualified name, using *Input.GetKey* :</span></span>

```cs
if (Input.GetKey("joystick button 8"))
{
  // ...
}
```

### <a name="getting-a-hand-or-motion-controllers-pose"></a><span data-ttu-id="5a7b1-299">Acquisizione di una mano o di un controller di movimento</span><span class="sxs-lookup"><span data-stu-id="5a7b1-299">Getting a hand or motion controller's pose</span></span>

<span data-ttu-id="5a7b1-300">È possibile accedere alla posizione e alla rotazione del controller usando *XR. InputTracking* :</span><span class="sxs-lookup"><span data-stu-id="5a7b1-300">You can access the position and rotation of the controller, using *XR.InputTracking* :</span></span>

```cs
Vector3 leftPosition = InputTracking.GetLocalPosition(XRNode.LeftHand);
Quaternion leftRotation = InputTracking.GetLocalRotation(XRNode.LeftHand);
```

<span data-ttu-id="5a7b1-301">Si noti che questo rappresenta la posizione del grip del controller (dove l'utente possiede il controller), che è utile per il rendering di una spada o di una pistola nella mano dell'utente o di un modello del controller stesso.</span><span class="sxs-lookup"><span data-stu-id="5a7b1-301">Note that this represents the controller's grip pose (where the user holds the controller), which is useful for rendering a sword or gun in the user's hand, or a model of the controller itself.</span></span>

<span data-ttu-id="5a7b1-302">Si noti che la relazione tra la posizione del grip e la posizione del puntatore (dove la punta del controller sta puntando) può variare tra i controller.</span><span class="sxs-lookup"><span data-stu-id="5a7b1-302">Note that the relationship between this grip pose and the pointer pose (where the tip of the controller is pointing) may differ across controllers.</span></span> <span data-ttu-id="5a7b1-303">Al momento, l'accesso alla posizione del puntatore del controller è possibile solo tramite l'API di input specifica del sig, descritta nelle sezioni riportate di seguito.</span><span class="sxs-lookup"><span data-stu-id="5a7b1-303">At this moment, accessing the controller's pointer pose is only possible through the MR-specific input API, described in the sections below.</span></span>

## <a name="windows-specific-apis-xrwsainput"></a><span data-ttu-id="5a7b1-304">API specifiche di Windows (XR. WSA. Input</span><span class="sxs-lookup"><span data-stu-id="5a7b1-304">Windows-specific APIs (XR.WSA.Input)</span></span>

<span data-ttu-id="5a7b1-305">**Spazio dei nomi:** *UnityEngine. XR. WSA. input*</span><span class="sxs-lookup"><span data-stu-id="5a7b1-305">**Namespace:** *UnityEngine.XR.WSA.Input*</span></span><br>
<span data-ttu-id="5a7b1-306">**Tipi** : *InteractionManager* , *InteractionSourceState* , *InteractionSource* , *InteractionSourceProperties* , *InteractionSourceKind* , *InteractionSourceLocation*</span><span class="sxs-lookup"><span data-stu-id="5a7b1-306">**Types** : *InteractionManager* , *InteractionSourceState* , *InteractionSource* , *InteractionSourceProperties* , *InteractionSourceKind* , *InteractionSourceLocation*</span></span>

<span data-ttu-id="5a7b1-307">Per ottenere informazioni più dettagliate sull'input della realtà mista di Windows (per HoloLens) e sui controller di movimento, è possibile scegliere di usare le API di input spaziali specifiche di Windows nello spazio dei nomi *UnityEngine. XR. WSA. input* .</span><span class="sxs-lookup"><span data-stu-id="5a7b1-307">To get at more detailed information about Windows Mixed Reality hand input (for HoloLens) and motion controllers, you can choose to use the Windows-specific spatial input APIs under the *UnityEngine.XR.WSA.Input* namespace.</span></span> <span data-ttu-id="5a7b1-308">In questo modo è possibile accedere a informazioni aggiuntive, come l'accuratezza della posizione o il tipo di origine, che consentono di distinguere le mani e i controller.</span><span class="sxs-lookup"><span data-stu-id="5a7b1-308">This lets you access additional information, such as position accuracy or the source kind, letting you tell hands and controllers apart.</span></span>

### <a name="polling-for-the-state-of-hands-and-motion-controllers"></a><span data-ttu-id="5a7b1-309">Polling dello stato di hands and Motion Controllers</span><span class="sxs-lookup"><span data-stu-id="5a7b1-309">Polling for the state of hands and motion controllers</span></span>

<span data-ttu-id="5a7b1-310">È possibile eseguire il polling dello stato di questo frame per ogni origine interazione (controller di movimento o mano) usando il metodo *GetCurrentReading* .</span><span class="sxs-lookup"><span data-stu-id="5a7b1-310">You can poll for this frame's state for each interaction source (hand or motion controller) using the *GetCurrentReading* method.</span></span>

```cs
var interactionSourceStates = InteractionManager.GetCurrentReading();
foreach (var interactionSourceState in interactionSourceStates) {
    // ...
}
```

<span data-ttu-id="5a7b1-311">Ogni *InteractionSourceState* restituito rappresenta un'origine interazione nel momento corrente.</span><span class="sxs-lookup"><span data-stu-id="5a7b1-311">Each *InteractionSourceState* you get back represents an interaction source at the current moment in time.</span></span> <span data-ttu-id="5a7b1-312">*InteractionSourceState* espone informazioni come:</span><span class="sxs-lookup"><span data-stu-id="5a7b1-312">The *InteractionSourceState* exposes info such as:</span></span>
* <span data-ttu-id="5a7b1-313">Quali [tipi di presse](../../design/motion-controllers.md) si verificano (Select/menu/afferrare/touchpad/levetta)</span><span class="sxs-lookup"><span data-stu-id="5a7b1-313">Which [kinds of presses](../../design/motion-controllers.md) are occurring (Select/Menu/Grasp/Touchpad/Thumbstick)</span></span>

   ```cs
   if (interactionSourceState.selectPressed) {
       // ...
   }
   ```
* <span data-ttu-id="5a7b1-314">Altri dati specifici per i controller di movimento, come le coordinate XY di touchpad e/o levetta e lo stato toccato</span><span class="sxs-lookup"><span data-stu-id="5a7b1-314">Other data specific to motion controllers, such the touchpad and/or thumbstick's XY coordinates and touched state</span></span>

   ```cs
   if (interactionSourceState.touchpadTouched && interactionSourceState.touchpadPosition.x > 0.5) {
       // ...
   }
   ```

* <span data-ttu-id="5a7b1-315">InteractionSourceKind per verificare se l'origine è una mano o un controller di movimento</span><span class="sxs-lookup"><span data-stu-id="5a7b1-315">The InteractionSourceKind to know if the source is a hand or a motion controller</span></span>

   ```cs
   if (interactionSourceState.source.kind == InteractionSourceKind.Hand) {
       // ...
   }
   ```

### <a name="polling-for-forward-predicted-rendering-poses"></a><span data-ttu-id="5a7b1-316">Polling per le pose di rendering con stima avanzata</span><span class="sxs-lookup"><span data-stu-id="5a7b1-316">Polling for forward-predicted rendering poses</span></span>

* <span data-ttu-id="5a7b1-317">Quando si esegue il polling per i dati di origine dell'interazione da mani e controller, le pose ricevute sono le pose stimate in avanti per il momento in cui i fotoni del frame raggiungono gli occhi dell'utente.</span><span class="sxs-lookup"><span data-stu-id="5a7b1-317">When polling for interaction source data from hands and controllers, the poses you get are forward-predicted poses for the moment in time when this frame's photons will reach the user's eyes.</span></span>  <span data-ttu-id="5a7b1-318">Queste pose con stima avanzata vengono usate in modo ottimale per il **rendering** del controller o di un oggetto mantenuto per ogni frame.</span><span class="sxs-lookup"><span data-stu-id="5a7b1-318">These forward-predicted poses are best used for **rendering** the controller or a held object each frame.</span></span>  <span data-ttu-id="5a7b1-319">Se si fa riferimento a una determinata pressione o rilascio con il controller, questo sarà più accurato se si usano le API degli eventi cronologici descritte di seguito.</span><span class="sxs-lookup"><span data-stu-id="5a7b1-319">If you are targeting a given press or release with the controller, that will be most accurate if you use the historical event APIs described below.</span></span>

   ```cs
   var sourcePose = interactionSourceState.sourcePose;
   Vector3 sourceGripPosition;
   Quaternion sourceGripRotation;
   if ((sourcePose.TryGetPosition(out sourceGripPosition, InteractionSourceNode.Grip)) &&
       (sourcePose.TryGetRotation(out sourceGripRotation, InteractionSourceNode.Grip))) {
       // ...
   }
   ```

* <span data-ttu-id="5a7b1-320">È anche possibile ottenere la formula Head con stima avanzata per il frame corrente.</span><span class="sxs-lookup"><span data-stu-id="5a7b1-320">You can also get the forward-predicted head pose for this current frame.</span></span>  <span data-ttu-id="5a7b1-321">Come per la posa di origine, questa operazione è utile per il **rendering** di un cursore, anche se la scelta di una determinata pressione o rilascio sarà più accurata se si usano le API degli eventi cronologici descritte di seguito.</span><span class="sxs-lookup"><span data-stu-id="5a7b1-321">As with the source pose, this is useful for **rendering** a cursor, although targeting a given press or release will be most accurate if you use the historical event APIs described below.</span></span>

   ```cs
   var headPose = interactionSourceState.headPose;
   var headRay = new Ray(headPose.position, headPose.forward);
   RaycastHit raycastHit;
   if (Physics.Raycast(headPose.position, headPose.forward, out raycastHit, 10)) {
       var cursorPos = raycastHit.point;
       // ...
   }
   ```

### <a name="handling-interaction-source-events"></a><span data-ttu-id="5a7b1-322">Gestione degli eventi di origine interazione</span><span class="sxs-lookup"><span data-stu-id="5a7b1-322">Handling interaction source events</span></span>

<span data-ttu-id="5a7b1-323">Per gestire gli eventi di input Man mano che si verificano con i dati di posa cronologici accurati, è possibile gestire gli eventi di origine interazione anziché il polling.</span><span class="sxs-lookup"><span data-stu-id="5a7b1-323">To handle input events as they happen with their accurate historical pose data, you can handle interaction source events instead of polling.</span></span>

<span data-ttu-id="5a7b1-324">Per gestire gli eventi di origine interazione:</span><span class="sxs-lookup"><span data-stu-id="5a7b1-324">To handle interaction source events:</span></span>
* <span data-ttu-id="5a7b1-325">Eseguire la registrazione per un evento di input *InteractionManager* .</span><span class="sxs-lookup"><span data-stu-id="5a7b1-325">Register for a *InteractionManager* input event.</span></span> <span data-ttu-id="5a7b1-326">Per ogni tipo di evento di interazione a cui si è interessati, è necessario sottoscriverlo.</span><span class="sxs-lookup"><span data-stu-id="5a7b1-326">For each type of interaction event that you are interested in, you need to subscribe to it.</span></span>

   ```cs
   InteractionManager.InteractionSourcePressed += InteractionManager_InteractionSourcePressed;
   ```

* <span data-ttu-id="5a7b1-327">Gestire l'evento.</span><span class="sxs-lookup"><span data-stu-id="5a7b1-327">Handle the event.</span></span> <span data-ttu-id="5a7b1-328">Una volta effettuata la sottoscrizione a un evento di interazione, si otterrà il callback quando appropriato.</span><span class="sxs-lookup"><span data-stu-id="5a7b1-328">Once you have subscribed to an interaction event, you will get the callback when appropriate.</span></span> <span data-ttu-id="5a7b1-329">Nell'esempio *SourcePressed* , questo sarà dopo che l'origine è stata rilevata e prima che venga rilasciata o persa.</span><span class="sxs-lookup"><span data-stu-id="5a7b1-329">In the *SourcePressed* example, this will be after the source was detected and before it is released or lost.</span></span>

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

### <a name="how-to-stop-handling-an-event"></a><span data-ttu-id="5a7b1-330">Come interrompere la gestione di un evento</span><span class="sxs-lookup"><span data-stu-id="5a7b1-330">How to stop handling an event</span></span>

<span data-ttu-id="5a7b1-331">È necessario arrestare la gestione di un evento quando non si è più interessati all'evento o si sta eliminando l'oggetto che ha sottoscritto l'evento.</span><span class="sxs-lookup"><span data-stu-id="5a7b1-331">You need to stop handling an event when you are no longer interested in the event or you are destroying the object that has subscribed to the event.</span></span> <span data-ttu-id="5a7b1-332">Per arrestare la gestione dell'evento, annullare la sottoscrizione all'evento.</span><span class="sxs-lookup"><span data-stu-id="5a7b1-332">To stop handling the event, you unsubscribe from the event.</span></span>

```cs
InteractionManager.InteractionSourcePressed -= InteractionManager_InteractionSourcePressed;
```

### <a name="list-of-interaction-source-events"></a><span data-ttu-id="5a7b1-333">Elenco di eventi di origine interazione</span><span class="sxs-lookup"><span data-stu-id="5a7b1-333">List of interaction source events</span></span>

<span data-ttu-id="5a7b1-334">Gli eventi di origine interazione disponibili sono:</span><span class="sxs-lookup"><span data-stu-id="5a7b1-334">The available interaction source events are:</span></span>
* <span data-ttu-id="5a7b1-335">*InteractionSourceDetected* (l'origine diventa attiva)</span><span class="sxs-lookup"><span data-stu-id="5a7b1-335">*InteractionSourceDetected* (source becomes active)</span></span>
* <span data-ttu-id="5a7b1-336">*InteractionSourceLost* (diventa inattivo)</span><span class="sxs-lookup"><span data-stu-id="5a7b1-336">*InteractionSourceLost* (becomes inactive)</span></span>
* <span data-ttu-id="5a7b1-337">*InteractionSourcePressed* (toccare, premere il pulsante o "Select")</span><span class="sxs-lookup"><span data-stu-id="5a7b1-337">*InteractionSourcePressed* (tap, button press, or "Select" uttered)</span></span>
* <span data-ttu-id="5a7b1-338">*InteractionSourceReleased* (fine di un tocco, pulsante rilasciato o fine di "Select" pronunciata)</span><span class="sxs-lookup"><span data-stu-id="5a7b1-338">*InteractionSourceReleased* (end of a tap, button released, or end of "Select" uttered)</span></span>
* <span data-ttu-id="5a7b1-339">*InteractionSourceUpdated* (sposta o modifica in altro modo lo stato)</span><span class="sxs-lookup"><span data-stu-id="5a7b1-339">*InteractionSourceUpdated* (moves or otherwise changes some state)</span></span>

### <a name="events-for-historical-targeting-poses-that-most-accurately-match-a-press-or-release"></a><span data-ttu-id="5a7b1-340">Gli eventi per il targeting cronologico rappresentano la corrispondenza più accurata tra una stampa o una versione</span><span class="sxs-lookup"><span data-stu-id="5a7b1-340">Events for historical targeting poses that most accurately match a press or release</span></span>

<span data-ttu-id="5a7b1-341">Le API di polling descritte in precedenza forniscono le pose previste dall'app.</span><span class="sxs-lookup"><span data-stu-id="5a7b1-341">The polling APIs described earlier give your app forward-predicted poses.</span></span>  <span data-ttu-id="5a7b1-342">Anche se queste pose stimate sono ideali per il rendering del controller o di un oggetto palmare virtuale, le pose future non sono ottimali per la destinazione, per due motivi principali:</span><span class="sxs-lookup"><span data-stu-id="5a7b1-342">While those predicted poses are best for rendering the controller or a virtual handheld object, future poses are not optimal for targeting, for two key reasons:</span></span>
* <span data-ttu-id="5a7b1-343">Quando l'utente preme un pulsante su un controller, è possibile che si verifichino 20ms di latenza wireless su Bluetooth prima che il sistema riceva la pressione.</span><span class="sxs-lookup"><span data-stu-id="5a7b1-343">When the user presses a button on a controller, there can be about 20ms of wireless latency over Bluetooth before the system receives the press.</span></span>
* <span data-ttu-id="5a7b1-344">Quindi, se si usa una formula con stima di avanzamento, è possibile applicare un altro 20ms di stima in diretta per individuare l'ora in cui i fotoni del frame corrente raggiungono gli occhi dell'utente.</span><span class="sxs-lookup"><span data-stu-id="5a7b1-344">Then, if you are using a forward-predicted pose, there would be another 10-20ms of forward prediction applied to target the time when the current frame's photons will reach the user's eyes.</span></span>

<span data-ttu-id="5a7b1-345">Questo significa che il polling fornisce una posizione di origine o una posizione Head che è 30-40ms in uscita dal punto in cui si è verificata l'intestazione e le mani dell'utente.</span><span class="sxs-lookup"><span data-stu-id="5a7b1-345">This means that polling gives you a source pose or head pose that is 30-40ms forward from where the user's head and hands actually were back when the press or release happened.</span></span>  <span data-ttu-id="5a7b1-346">Per l'input della mano HoloLens, anche se non si verifica alcun ritardo di trasmissione wireless, si verifica un ritardo di elaborazione simile per rilevare la pressione.</span><span class="sxs-lookup"><span data-stu-id="5a7b1-346">For HoloLens hand input, while there's no wireless transmission delay, there is a similar processing delay to detect the press.</span></span>

<span data-ttu-id="5a7b1-347">Per definire la destinazione in modo accurato in base all'intento originale dell'utente per la pressione di un controller o una mano, è necessario usare la funzione di origine o di intestazione di origine cronologica da tale evento di input *InteractionSourcePressed* o *InteractionSourceReleased* .</span><span class="sxs-lookup"><span data-stu-id="5a7b1-347">To accurately target based on the user's original intent for a hand or controller press, you should use the historical source pose or head pose from that *InteractionSourcePressed* or *InteractionSourceReleased* input event.</span></span>

<span data-ttu-id="5a7b1-348">È possibile fare riferimento a una stampa o a una versione con dati di posa cronologici dall'Head dell'utente o dal controller:</span><span class="sxs-lookup"><span data-stu-id="5a7b1-348">You can target a press or release with historical pose data from the user's head or their controller:</span></span>
* <span data-ttu-id="5a7b1-349">Il primo posto nel momento in cui [si è verificato](../../design/gaze-and-commit.md) un movimento o un controller, che può essere **usato per definire** la scelta dell'utente:</span><span class="sxs-lookup"><span data-stu-id="5a7b1-349">The head pose at the moment in time when a gesture or controller press occurred, which can be used for **targeting** to determine what the user was [gazing](../../design/gaze-and-commit.md) at:</span></span>

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

* <span data-ttu-id="5a7b1-350">La posizione di origine nel momento in cui si è verificata la pressione di un controller di movimento, che può essere **usata per determinare** l'elemento che l'utente stava puntando al controller.</span><span class="sxs-lookup"><span data-stu-id="5a7b1-350">The source pose at the moment in time when a motion controller press occurred, which can be used for **targeting** to determine what the user was pointing the controller at.</span></span>  <span data-ttu-id="5a7b1-351">Si tratta dello stato del controller che ha riscontrato la pressione.</span><span class="sxs-lookup"><span data-stu-id="5a7b1-351">This will be the state of the controller that experienced the press.</span></span>  <span data-ttu-id="5a7b1-352">Se si esegue il rendering del controller stesso, è possibile richiedere la presenza del puntatore anziché il grip, per sparare al raggio di destinazione da quello che l'utente considererà il suggerimento naturale del controller sottoposto a rendering:</span><span class="sxs-lookup"><span data-stu-id="5a7b1-352">If you are rendering the controller itself, you can request the pointer pose rather than the grip pose, to shoot the targeting ray from what the user will consider the natural tip of that rendered controller:</span></span>

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

### <a name="event-handlers-example"></a><span data-ttu-id="5a7b1-353">Esempio di gestori eventi</span><span class="sxs-lookup"><span data-stu-id="5a7b1-353">Event handlers example</span></span>

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

## <a name="high-level-composite-gesture-apis-gesturerecognizer"></a><span data-ttu-id="5a7b1-354">API per movimenti compositi di alto livello (GestureRecognizer)</span><span class="sxs-lookup"><span data-stu-id="5a7b1-354">High-level composite gesture APIs (GestureRecognizer)</span></span>

<span data-ttu-id="5a7b1-355">**Spazio dei nomi:** *UnityEngine. XR. WSA. input*</span><span class="sxs-lookup"><span data-stu-id="5a7b1-355">**Namespace:** *UnityEngine.XR.WSA.Input*</span></span><br>
<span data-ttu-id="5a7b1-356">**Tipi** : *GestureRecognizer* , *GestureSettings* , *InteractionSourceKind*</span><span class="sxs-lookup"><span data-stu-id="5a7b1-356">**Types** : *GestureRecognizer* , *GestureSettings* , *InteractionSourceKind*</span></span>

<span data-ttu-id="5a7b1-357">L'app può anche riconoscere movimenti compositi di livello superiore per le origini di input spaziali, i movimenti di tocco, di manipolazione e di navigazione.</span><span class="sxs-lookup"><span data-stu-id="5a7b1-357">Your app can also recognize higher-level composite gestures for spatial input sources, Tap, Hold, Manipulation and Navigation gestures.</span></span> <span data-ttu-id="5a7b1-358">È possibile riconoscere questi movimenti compositi tra [le mani](../../design/gaze-and-commit.md#composite-gestures) e i [controller di movimento](../../design/motion-controllers.md) usando l'oggetto GestureRecognizer.</span><span class="sxs-lookup"><span data-stu-id="5a7b1-358">You can recognize these composite gestures across both [hands](../../design/gaze-and-commit.md#composite-gestures) and [motion controllers](../../design/motion-controllers.md) using the GestureRecognizer.</span></span>

<span data-ttu-id="5a7b1-359">Ogni evento di movimento nell'oggetto GestureRecognizer fornisce SourceKind per l'input, nonché il raggio Head di destinazione al momento dell'evento.</span><span class="sxs-lookup"><span data-stu-id="5a7b1-359">Each Gesture event on the GestureRecognizer provides the SourceKind for the input as well as the targeting head ray at the time of the event.</span></span> <span data-ttu-id="5a7b1-360">Alcuni eventi forniscono informazioni aggiuntive specifiche del contesto.</span><span class="sxs-lookup"><span data-stu-id="5a7b1-360">Some events provide additional context specific information.</span></span>

<span data-ttu-id="5a7b1-361">Sono necessari solo pochi passaggi per acquisire i movimenti usando un riconoscitore di movimento:</span><span class="sxs-lookup"><span data-stu-id="5a7b1-361">There are only a few steps required to capture gestures using a Gesture Recognizer:</span></span>
1. <span data-ttu-id="5a7b1-362">Creare un nuovo riconoscitore di movimento</span><span class="sxs-lookup"><span data-stu-id="5a7b1-362">Create a new Gesture Recognizer</span></span>
2. <span data-ttu-id="5a7b1-363">Specificare i movimenti da controllare</span><span class="sxs-lookup"><span data-stu-id="5a7b1-363">Specify which gestures to watch for</span></span>
3. <span data-ttu-id="5a7b1-364">Sottoscrivere gli eventi per questi movimenti</span><span class="sxs-lookup"><span data-stu-id="5a7b1-364">Subscribe to events for those gestures</span></span>
4. <span data-ttu-id="5a7b1-365">Avviare l'acquisizione di movimenti</span><span class="sxs-lookup"><span data-stu-id="5a7b1-365">Start capturing gestures</span></span>

### <a name="create-a-new-gesture-recognizer"></a><span data-ttu-id="5a7b1-366">Creare un nuovo riconoscitore di movimento</span><span class="sxs-lookup"><span data-stu-id="5a7b1-366">Create a new Gesture Recognizer</span></span>

<span data-ttu-id="5a7b1-367">Per utilizzare l'oggetto *GestureRecognizer* , è necessario avere creato un oggetto *GestureRecognizer* :</span><span class="sxs-lookup"><span data-stu-id="5a7b1-367">To use the *GestureRecognizer* , you must have created a *GestureRecognizer* :</span></span>

```cs
GestureRecognizer recognizer = new GestureRecognizer();
```

### <a name="specify-which-gestures-to-watch-for"></a><span data-ttu-id="5a7b1-368">Specificare i movimenti da controllare</span><span class="sxs-lookup"><span data-stu-id="5a7b1-368">Specify which gestures to watch for</span></span>

<span data-ttu-id="5a7b1-369">Specificare i movimenti a cui si è interessati tramite *SetRecognizableGestures ()* :</span><span class="sxs-lookup"><span data-stu-id="5a7b1-369">Specify which gestures you are interested in via *SetRecognizableGestures()* :</span></span>

```cs
recognizer.SetRecognizableGestures(GestureSettings.Tap | GestureSettings.Hold);
```

### <a name="subscribe-to-events-for-those-gestures"></a><span data-ttu-id="5a7b1-370">Sottoscrivere gli eventi per questi movimenti</span><span class="sxs-lookup"><span data-stu-id="5a7b1-370">Subscribe to events for those gestures</span></span>

<span data-ttu-id="5a7b1-371">Sottoscrivere gli eventi per i movimenti a cui si è interessati.</span><span class="sxs-lookup"><span data-stu-id="5a7b1-371">Subscribe to events for the gestures you are interested in.</span></span>

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
><span data-ttu-id="5a7b1-372">I movimenti di spostamento e manipolazione si escludono a vicenda in un'istanza di un oggetto *GestureRecognizer* .</span><span class="sxs-lookup"><span data-stu-id="5a7b1-372">Navigation and Manipulation gestures are mutually exclusive on an instance of a *GestureRecognizer* .</span></span>

### <a name="start-capturing-gestures"></a><span data-ttu-id="5a7b1-373">Avviare l'acquisizione di movimenti</span><span class="sxs-lookup"><span data-stu-id="5a7b1-373">Start capturing gestures</span></span>

<span data-ttu-id="5a7b1-374">Per impostazione predefinita, un oggetto *GestureRecognizer* non monitora l'input fino a quando non viene chiamato *StartCapturingGestures ()* .</span><span class="sxs-lookup"><span data-stu-id="5a7b1-374">By default, a *GestureRecognizer* does not monitor input until *StartCapturingGestures()* is called.</span></span> <span data-ttu-id="5a7b1-375">È possibile che venga generato un evento di movimento dopo che è stato chiamato *StopCapturingGestures ()* se l'input è stato eseguito prima del frame in cui è stato elaborato *StopCapturingGestures ()* .</span><span class="sxs-lookup"><span data-stu-id="5a7b1-375">It is possible that a gesture event may be generated after *StopCapturingGestures()* is called if input was performed before the frame where *StopCapturingGestures()* was processed.</span></span> <span data-ttu-id="5a7b1-376">L'oggetto *GestureRecognizer* ricorda se è stato acceso o disattivato durante il frame precedente in cui si è effettivamente verificato il movimento ed è quindi affidabile per avviare e arrestare il monitoraggio dei movimenti in base alla destinazione dello sguardo del frame.</span><span class="sxs-lookup"><span data-stu-id="5a7b1-376">The *GestureRecognizer* will remember whether it was on or off during the previous frame in which the gesture actually occurred, and so it is reliable to start and stop gesture monitoring based on this frame's gaze targeting.</span></span>

```cs
recognizer.StartCapturingGestures();
```

### <a name="stop-capturing-gestures"></a><span data-ttu-id="5a7b1-377">Interrompi acquisizione movimenti</span><span class="sxs-lookup"><span data-stu-id="5a7b1-377">Stop capturing gestures</span></span>

<span data-ttu-id="5a7b1-378">Per arrestare il riconoscimento del movimento:</span><span class="sxs-lookup"><span data-stu-id="5a7b1-378">To stop gesture recognition:</span></span>

```cs
recognizer.StopCapturingGestures();
```

### <a name="removing-a-gesture-recognizer"></a><span data-ttu-id="5a7b1-379">Rimozione di un riconoscimento di movimento</span><span class="sxs-lookup"><span data-stu-id="5a7b1-379">Removing a gesture recognizer</span></span>

<span data-ttu-id="5a7b1-380">Ricordarsi di annullare la sottoscrizione agli eventi sottoscritti prima di eliminare un oggetto *GestureRecognizer* .</span><span class="sxs-lookup"><span data-stu-id="5a7b1-380">Remember to unsubscribe from subscribed events before destroying a *GestureRecognizer* object.</span></span>

```cs
void OnDestroy()
{
    recognizer.Tapped -= GestureRecognizer_Tapped;
    recognizer.HoldStarted -= GestureRecognizer_HoldStarted;
    recognizer.HoldCompleted -= GestureRecognizer_HoldCompleted;
    recognizer.HoldCanceled -= GestureRecognizer_HoldCanceled;
}
```

## <a name="rendering-the-motion-controller-model-in-unity"></a><span data-ttu-id="5a7b1-381">Rendering del modello di controller di movimento in Unity</span><span class="sxs-lookup"><span data-stu-id="5a7b1-381">Rendering the motion controller model in Unity</span></span>

<span data-ttu-id="5a7b1-382">![Modello e teleporting del controller di movimento](images/motioncontrollertest-teleport-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="5a7b1-382">![Motion Controller model and teleportation](images/motioncontrollertest-teleport-1000px.png)</span></span><br>
<span data-ttu-id="5a7b1-383">*Modello e teleporting del controller di movimento*</span><span class="sxs-lookup"><span data-stu-id="5a7b1-383">*Motion controller model and teleportation*</span></span>

<span data-ttu-id="5a7b1-384">Per eseguire il rendering dei controller di movimento nell'app che corrispondono ai controller fisici che gli utenti mantengono e si articolano con la pressione di vari pulsanti, è possibile usare la **prefabbricazione MotionController** nel [Toolkit di realtà mista](https://github.com/Microsoft/MixedRealityToolkit-Unity/).</span><span class="sxs-lookup"><span data-stu-id="5a7b1-384">To render motion controllers in your app that match the physical controllers your users are holding and articulate as various buttons are pressed, you can use the **MotionController prefab** in the [Mixed Reality Toolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity/).</span></span>  <span data-ttu-id="5a7b1-385">Questa prefabbricata carica dinamicamente il modello glTF corretto in fase di esecuzione dal driver del controller di movimento installato dal sistema.</span><span class="sxs-lookup"><span data-stu-id="5a7b1-385">This prefab dynamically loads the correct glTF model at runtime from the system's installed motion controller driver.</span></span>  <span data-ttu-id="5a7b1-386">È importante caricare i modelli in modo dinamico, anziché importarli manualmente nell'editor, in modo che l'app visualizzi modelli 3D fisicamente accurati per i controller correnti e futuri che possono avere gli utenti.</span><span class="sxs-lookup"><span data-stu-id="5a7b1-386">It's important to load these models dynamically rather than importing them manually in the editor, so that your app will show physically accurate 3D models for any current and future controllers your users may have.</span></span>

1. <span data-ttu-id="5a7b1-387">Seguire le istruzioni [Introduzione](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/GettingStarted.md) per scaricare il Toolkit di realtà mista e aggiungerlo al progetto Unity.</span><span class="sxs-lookup"><span data-stu-id="5a7b1-387">Follow the [Getting Started](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/GettingStarted.md) instructions to download the Mixed Reality Toolkit and add it to your Unity project.</span></span>
2. <span data-ttu-id="5a7b1-388">Se la fotocamera è stata sostituita con la prefabbricata *MixedRealityCameraParent* come parte del Introduzione passaggi, è possibile iniziare.</span><span class="sxs-lookup"><span data-stu-id="5a7b1-388">If you replaced your camera with the *MixedRealityCameraParent* prefab as part of the Getting Started steps, you're good to go!</span></span>  <span data-ttu-id="5a7b1-389">Il prefabbricato include il rendering del controller di movimento.</span><span class="sxs-lookup"><span data-stu-id="5a7b1-389">That prefab includes motion controller rendering.</span></span>  <span data-ttu-id="5a7b1-390">In caso contrario, aggiungere *assets/HoloToolkit/input/precasers/MotionControllers. prefabbricate* nella scena dal riquadro progetto.</span><span class="sxs-lookup"><span data-stu-id="5a7b1-390">Otherwise, add *Assets/HoloToolkit/Input/Prefabs/MotionControllers.prefab* into your scene from the Project pane.</span></span>  <span data-ttu-id="5a7b1-391">È opportuno aggiungere tale prefabbricato come elemento figlio di qualsiasi oggetto padre utilizzato per spostare la fotocamera quando l'utente esegue il teleportamento all'interno della scena, in modo che i controller siano insieme all'utente.</span><span class="sxs-lookup"><span data-stu-id="5a7b1-391">You'll want to add that prefab as a child of whatever parent object you use to move the camera around when the user teleports within your scene, so that the controllers come along with the user.</span></span>  <span data-ttu-id="5a7b1-392">Se l'app non implica il Teleporting, è sufficiente aggiungere il prefabbricato alla radice della scena.</span><span class="sxs-lookup"><span data-stu-id="5a7b1-392">If your app does not involve teleporting, just add the prefab at the root of your scene.</span></span>

## <a name="throwing-objects"></a><span data-ttu-id="5a7b1-393">Generazione di oggetti</span><span class="sxs-lookup"><span data-stu-id="5a7b1-393">Throwing objects</span></span>

<span data-ttu-id="5a7b1-394">La generazione di oggetti in realtà virtuale è un problema più complesso che può sembrare.</span><span class="sxs-lookup"><span data-stu-id="5a7b1-394">Throwing objects in virtual reality is a harder problem then it may at first seem.</span></span> <span data-ttu-id="5a7b1-395">Come per la maggior parte delle interazioni basate fisicamente, quando la generazione di un gioco agisce in modo imprevisto, è immediatamente evidente e interrompe l'immersione.</span><span class="sxs-lookup"><span data-stu-id="5a7b1-395">As with most physically based interactions, when throwing in game acts in an unexpected way, it is immediately obvious and breaks immersion.</span></span> <span data-ttu-id="5a7b1-396">Abbiamo dedicato un po' di tempo a comprendere in modo approfondito come rappresentare un comportamento di generazione fisico corretto e avere a disposizione alcune linee guida, abilitate tramite aggiornamenti della piattaforma, che vogliamo condividere con te.</span><span class="sxs-lookup"><span data-stu-id="5a7b1-396">We have spent some time thinking deeply about how to represent a physically correct throwing behavior, and have come up with a few guidelines, enabled through updates to our platform, that we would like to share with you.</span></span>

<span data-ttu-id="5a7b1-397">È possibile trovare un esempio di come si consiglia di implementare il lancio [qui](https://github.com/keluecke/MixedRealityToolkit-Unity/blob/master/External/Unitypackages/ThrowingStarter.unitypackage).</span><span class="sxs-lookup"><span data-stu-id="5a7b1-397">You can find an example of how we recommend to implement throwing [here](https://github.com/keluecke/MixedRealityToolkit-Unity/blob/master/External/Unitypackages/ThrowingStarter.unitypackage).</span></span> <span data-ttu-id="5a7b1-398">Questo esempio segue le quattro linee guida seguenti:</span><span class="sxs-lookup"><span data-stu-id="5a7b1-398">This sample follows these four guidelines:</span></span>
* <span data-ttu-id="5a7b1-399">**Utilizzare la *velocità* del controller invece della posizione** .</span><span class="sxs-lookup"><span data-stu-id="5a7b1-399">**Use the controller’s *velocity* instead of position** .</span></span> <span data-ttu-id="5a7b1-400">Nell'aggiornamento di novembre di Windows è stata introdotta una modifica nel comportamento quando si [Verifica lo stato di rilevamento posizionale '' approssimativo](../../design/motion-controllers.md#controller-tracking-state).</span><span class="sxs-lookup"><span data-stu-id="5a7b1-400">In the November update to Windows, we introduced a change in behavior when in the [''Approximate'' positional tracking state](../../design/motion-controllers.md#controller-tracking-state).</span></span> <span data-ttu-id="5a7b1-401">In questo stato, le informazioni sulla velocità del controller continueranno a essere segnalate fino a quando riteniamo che la precisione è elevata, che è spesso più lunga della posizione rimane alta.</span><span class="sxs-lookup"><span data-stu-id="5a7b1-401">When in this state, velocity information about the controller will continue to be reported for as long as we believe it is high accuracy, which is often longer than position remains high accuracy.</span></span>
* <span data-ttu-id="5a7b1-402">**Incorporare la *velocità angolare* del controller** .</span><span class="sxs-lookup"><span data-stu-id="5a7b1-402">**Incorporate the *angular velocity* of the controller** .</span></span> <span data-ttu-id="5a7b1-403">Questa logica è interamente contenuta nel `throwing.cs` file nel `GetThrownObjectVelAngVel` metodo statico, all'interno del pacchetto collegato sopra:</span><span class="sxs-lookup"><span data-stu-id="5a7b1-403">This logic is all contained in the `throwing.cs` file in the `GetThrownObjectVelAngVel` static method, within the package linked above:</span></span>
   1. <span data-ttu-id="5a7b1-404">Poiché viene mantenuta la velocità angolare, l'oggetto generato deve mantenere la stessa velocità angolare del momento in cui si trovava al momento della generazione: `objectAngularVelocity = throwingControllerAngularVelocity;`</span><span class="sxs-lookup"><span data-stu-id="5a7b1-404">As angular velocity is conserved, the thrown object must maintain the same angular velocity as it had at the moment of the throw: `objectAngularVelocity = throwingControllerAngularVelocity;`</span></span>
   2. <span data-ttu-id="5a7b1-405">Poiché il centro della massa dell'oggetto generato è probabilmente diverso dall'origine della posizione del grip, probabilmente ha una velocità diversa rispetto a quella del controller nel frame di riferimento dell'utente.</span><span class="sxs-lookup"><span data-stu-id="5a7b1-405">As the center of mass of the thrown object is likely not at the origin of the grip pose, it likely has a different velocity then that of the controller in the frame of reference of the user.</span></span> <span data-ttu-id="5a7b1-406">La parte della velocità dell'oggetto contribuito in questo modo è la velocità tangenziale istantanea del centro della massa dell'oggetto generato intorno all'origine del controller.</span><span class="sxs-lookup"><span data-stu-id="5a7b1-406">The portion of the object’s velocity contributed in this way is the instantaneous tangential velocity of the center of mass of the thrown object around the controller origin.</span></span> <span data-ttu-id="5a7b1-407">Questa velocità tangenziale è il prodotto incrociato della velocità angolare del controller con il vettore che rappresenta la distanza tra l'origine del controller e il centro della massa dell'oggetto generato.</span><span class="sxs-lookup"><span data-stu-id="5a7b1-407">This tangential velocity is the cross product of the angular velocity of the controller with the vector representing the distance between the controller origin and the center of mass of the thrown object.</span></span>

      ```cs
      Vector3 radialVec = thrownObjectCenterOfMass - throwingControllerPos;
      Vector3 tangentialVelocity = Vector3.Cross(throwingControllerAngularVelocity, radialVec);
      ```

   3. <span data-ttu-id="5a7b1-408">La velocità totale dell'oggetto generata è quindi la somma della velocità del controller e della velocità tangenziale: `objectVelocity = throwingControllerVelocity + tangentialVelocity;`</span><span class="sxs-lookup"><span data-stu-id="5a7b1-408">The total velocity of the thrown object is thus the sum of velocity of the controller and this tangential velocity: `objectVelocity = throwingControllerVelocity + tangentialVelocity;`</span></span>

* <span data-ttu-id="5a7b1-409">**Prestare particolare attenzione all' *ora* in cui viene applicata la velocità** .</span><span class="sxs-lookup"><span data-stu-id="5a7b1-409">**Pay close attention to the *time* at which we apply the velocity** .</span></span> <span data-ttu-id="5a7b1-410">Quando si preme un pulsante, può essere necessario fino a 20ms per l'evento per propagarsi attraverso la tecnologia Bluetooth al sistema operativo.</span><span class="sxs-lookup"><span data-stu-id="5a7b1-410">When a button is pressed, it can take up to 20ms for that event to bubble up through Bluetooth to the operating system.</span></span> <span data-ttu-id="5a7b1-411">Ciò significa che se si esegue il polling di una modifica dello stato del controller da Pressed a not Pressed o viceversa, il controller pone le informazioni che verranno apportate in precedenza in questa modifica dello stato.</span><span class="sxs-lookup"><span data-stu-id="5a7b1-411">This means that if you poll for a controller state change from pressed to not pressed or vice versa, the controller pose information you get with it will actually be ahead of this change in state.</span></span> <span data-ttu-id="5a7b1-412">Inoltre, la presentazione del controller presentata dall'API di polling viene stimata in modo da riflettere una probabile situazione nel momento in cui verrà visualizzato il frame, che potrebbe essere più 20ms in futuro.</span><span class="sxs-lookup"><span data-stu-id="5a7b1-412">Further, the controller pose presented by our polling API is forward predicted to reflect a likely pose at the time the frame will be displayed which could be more then 20ms in the future.</span></span> <span data-ttu-id="5a7b1-413">Questo è ideale per il *rendering* degli oggetti conservati, ma costituisce un problema di tempo per la *destinazione* dell'oggetto durante il calcolo della traiettoria nel momento in cui l'utente ha rilasciato il proprio Throw.</span><span class="sxs-lookup"><span data-stu-id="5a7b1-413">This is good for *rendering* held objects, but compounds our time problem for *targeting* the object as we calculate the trajectory for the moment the user released their throw.</span></span> <span data-ttu-id="5a7b1-414">Fortunatamente, con l'aggiornamento di novembre, quando viene inviato un evento Unity, ad esempio *InteractionSourcePressed* o *InteractionSourceReleased* , lo stato include i dati cronologici di post di ritorno quando il pulsante è stato effettivamente premuto o rilasciato.</span><span class="sxs-lookup"><span data-stu-id="5a7b1-414">Fortunately, with the November update, when a Unity event like *InteractionSourcePressed* or *InteractionSourceReleased* is sent, the state includes the historical pose data from back when the button was actually pressed or released.</span></span>  <span data-ttu-id="5a7b1-415">Per ottenere il rendering del controller più accurato e la destinazione del controller durante i lanci, è necessario usare correttamente il polling e la gestione degli eventi, in base alle esigenze:</span><span class="sxs-lookup"><span data-stu-id="5a7b1-415">To get the most accurate controller rendering and controller targeting during throws, you must correctly use polling and eventing, as appropriate:</span></span>
   * <span data-ttu-id="5a7b1-416">Per il **rendering del controller** ogni frame, l'app deve posizionare il *GameObject* del controller in corrispondenza del controller con stima avanzata per l'ora del fotone del frame corrente.</span><span class="sxs-lookup"><span data-stu-id="5a7b1-416">For **controller rendering** each frame, your app should position the controller's *GameObject* at the forward-predicted controller pose for the current frame’s photon time.</span></span>  <span data-ttu-id="5a7b1-417">Si ottengono questi dati dalle API di polling Unity, ad esempio *[XR. InputTracking. GetLocalPosition](https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html)* o *[XR. WSA. Input. InteractionManager. GetCurrentReading](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.GetCurrentReading.html)* .</span><span class="sxs-lookup"><span data-stu-id="5a7b1-417">You get this data from Unity polling APIs like *[XR.InputTracking.GetLocalPosition](https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html)* or *[XR.WSA.Input.InteractionManager.GetCurrentReading](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.GetCurrentReading.html)* .</span></span>
   * <span data-ttu-id="5a7b1-418">Per il **controller che punta** alla stampa o al rilascio, l'app deve Raycast e calcolare le traiettorie in base alla definizione del controller cronologico per l'evento di stampa o di rilascio.</span><span class="sxs-lookup"><span data-stu-id="5a7b1-418">For **controller targeting** upon a press or release, your app should raycast and calculate trajectories based on the historical controller pose for that press or release event.</span></span>  <span data-ttu-id="5a7b1-419">Si ottengono questi dati dalle API di gestione degli eventi di Unity, ad esempio *[InteractionManager. InteractionSourcePressed](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.InteractionSourcePressed.html)* .</span><span class="sxs-lookup"><span data-stu-id="5a7b1-419">You get this data from Unity eventing APIs, like *[InteractionManager.InteractionSourcePressed](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.InteractionSourcePressed.html)* .</span></span>
* <span data-ttu-id="5a7b1-420">**Utilizzare la disposizione del grip** .</span><span class="sxs-lookup"><span data-stu-id="5a7b1-420">**Use the grip pose** .</span></span> <span data-ttu-id="5a7b1-421">La velocità e la velocità angolari vengono segnalate rispetto alla posizione del grip, non alla posizione del puntatore.</span><span class="sxs-lookup"><span data-stu-id="5a7b1-421">Angular velocity and velocity are reported relative to the grip pose, not pointer pose.</span></span>

<span data-ttu-id="5a7b1-422">La generazione continuerà a migliorare con gli aggiornamenti futuri di Windows e ci si aspetterà di trovare altre informazioni su di essa.</span><span class="sxs-lookup"><span data-stu-id="5a7b1-422">Throwing will continue to improve with future Windows updates, and you can expect to find more information on it here.</span></span>

## <a name="gesture-and-motion-controllers-in-mrtk-v2"></a><span data-ttu-id="5a7b1-423">Controller movimento e movimento in MRTK V2</span><span class="sxs-lookup"><span data-stu-id="5a7b1-423">Gesture and Motion Controllers in MRTK v2</span></span>

<span data-ttu-id="5a7b1-424">È possibile accedere a gesture e Motion controller dal gestore di input.</span><span class="sxs-lookup"><span data-stu-id="5a7b1-424">You can access gesture and motion controller from the input Manager.</span></span>
* [<span data-ttu-id="5a7b1-425">Movimento in MRTK V2</span><span class="sxs-lookup"><span data-stu-id="5a7b1-425">Gesture in MRTK v2</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Gestures.html)
* [<span data-ttu-id="5a7b1-426">Controller di movimento in MRTK V2</span><span class="sxs-lookup"><span data-stu-id="5a7b1-426">Motion Controller in MRTK v2</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Controllers.html)


## <a name="follow-along-with-tutorials"></a><span data-ttu-id="5a7b1-427">Seguire le esercitazioni</span><span class="sxs-lookup"><span data-stu-id="5a7b1-427">Follow along with tutorials</span></span>

<span data-ttu-id="5a7b1-428">Le esercitazioni dettagliate, con esempi di personalizzazione più dettagliati, sono disponibili in Mixed Reality Academy:</span><span class="sxs-lookup"><span data-stu-id="5a7b1-428">Step-by-step tutorials, with more detailed customization examples, are available in the Mixed Reality Academy:</span></span>

- [<span data-ttu-id="5a7b1-429">Input MR 211: Movimento</span><span class="sxs-lookup"><span data-stu-id="5a7b1-429">MR Input 211: Gesture</span></span>](tutorials/holograms-211.md)
- [<span data-ttu-id="5a7b1-430">Input MR 213: Controller del movimento</span><span class="sxs-lookup"><span data-stu-id="5a7b1-430">MR Input 213: Motion controllers</span></span>](../../deprecated/mixed-reality-213.md)

<span data-ttu-id="5a7b1-431">[![Input MR 213-controller di movimento](images/mr213-main-600px.jpg)](https://docs.microsoft.com/windows/mixed-reality/mixed-reality-213)</span><span class="sxs-lookup"><span data-stu-id="5a7b1-431">[![MR Input 213 - Motion controller](images/mr213-main-600px.jpg)](https://docs.microsoft.com/windows/mixed-reality/mixed-reality-213)</span></span><br>
<span data-ttu-id="5a7b1-432">*Input MR 213-controller di movimento*</span><span class="sxs-lookup"><span data-stu-id="5a7b1-432">*MR Input 213 - Motion controller*</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="5a7b1-433">Successivo checkpoint di sviluppo</span><span class="sxs-lookup"><span data-stu-id="5a7b1-433">Next Development Checkpoint</span></span>

<span data-ttu-id="5a7b1-434">Se si sta seguendo il percorso di checkpoint per lo sviluppo con Unity che abbiamo delineato, si stanno esplorando i blocchi predefiniti fondamentali in MRTK.</span><span class="sxs-lookup"><span data-stu-id="5a7b1-434">If you're following the Unity development checkpoint journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="5a7b1-435">Da qui è possibile passare al blocco predefinito successivo:</span><span class="sxs-lookup"><span data-stu-id="5a7b1-435">From here, you can proceed to the next building block:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="5a7b1-436">Tracciamento della mano e oculare</span><span class="sxs-lookup"><span data-stu-id="5a7b1-436">Hand and eye tracking</span></span>](hand-eye-in-unit.md)

<span data-ttu-id="5a7b1-437">In alternativa, passare alle API e funzionalità della piattaforma di realtà mista:</span><span class="sxs-lookup"><span data-stu-id="5a7b1-437">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="5a7b1-438">Esperienze condivise</span><span class="sxs-lookup"><span data-stu-id="5a7b1-438">Shared experiences</span></span>](shared-experiences-in-unity.md)

<span data-ttu-id="5a7b1-439">È sempre possibile tornare ai [checkpoint per lo sviluppo con Unity](unity-development-overview.md#2-core-building-blocks) in qualsiasi momento.</span><span class="sxs-lookup"><span data-stu-id="5a7b1-439">You can always go back to the [Unity development checkpoints](unity-development-overview.md#2-core-building-blocks) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="5a7b1-440">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="5a7b1-440">See also</span></span>

* [<span data-ttu-id="5a7b1-441">Puntamento con la testa e commit</span><span class="sxs-lookup"><span data-stu-id="5a7b1-441">Head-gaze and commit</span></span>](../../design/gaze-and-commit.md)
* [<span data-ttu-id="5a7b1-442">Controller del movimento</span><span class="sxs-lookup"><span data-stu-id="5a7b1-442">Motion controllers</span></span>](../../design/motion-controllers.md)

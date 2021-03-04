---
title: InputAnimationFileFormat
description: Documentazione sulla specifica del formato di file binario di animazione di input in MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: 5ec2b3f3ac83ee0ca1923cb62b36fe80edc22120
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/03/2021
ms.locfileid: "101781756"
---
# <a name="input-animation-binary-file-format-specification"></a><span data-ttu-id="2e2c6-104">Specifica del formato file binario animazione input</span><span class="sxs-lookup"><span data-stu-id="2e2c6-104">Input animation binary file format specification</span></span>

## <a name="overall-structure"></a><span data-ttu-id="2e2c6-105">Struttura complessiva</span><span class="sxs-lookup"><span data-stu-id="2e2c6-105">Overall structure</span></span>

<span data-ttu-id="2e2c6-106">Il file binario di animazione di input inizia con un numero intero a 64 bit.</span><span class="sxs-lookup"><span data-stu-id="2e2c6-106">The input animation binary file begins with a 64 bit integer magic number.</span></span> <span data-ttu-id="2e2c6-107">Il valore di questo numero in notazione esadecimale è `0x6a8faf6e0f9e42c6` e può essere usato per identificare i file di animazione di input validi.</span><span class="sxs-lookup"><span data-stu-id="2e2c6-107">The value of this number in hexadecimal notation is `0x6a8faf6e0f9e42c6` and can be used to identify valid input animation files.</span></span>

<span data-ttu-id="2e2c6-108">Gli otto byte successivi sono due valori Int32 che dichiarano il numero di versione principale e secondario del file.</span><span class="sxs-lookup"><span data-stu-id="2e2c6-108">The next eight bytes are two Int32 values declaring the major and minor version number of the file.</span></span>

<span data-ttu-id="2e2c6-109">Il resto del file viene occupato dai dati di animazione, che possono variare tra i numeri di versione.</span><span class="sxs-lookup"><span data-stu-id="2e2c6-109">The rest of the file is taken up by animation data, which may change between version numbers.</span></span>

| <span data-ttu-id="2e2c6-110">Sezione</span><span class="sxs-lookup"><span data-stu-id="2e2c6-110">Section</span></span> | <span data-ttu-id="2e2c6-111">Tipo</span><span class="sxs-lookup"><span data-stu-id="2e2c6-111">Type</span></span> |
|---------|------|
| <span data-ttu-id="2e2c6-112">Numero magico</span><span class="sxs-lookup"><span data-stu-id="2e2c6-112">Magic Number</span></span> | <span data-ttu-id="2e2c6-113">Int64</span><span class="sxs-lookup"><span data-stu-id="2e2c6-113">Int64</span></span> |
| <span data-ttu-id="2e2c6-114">Numero di versione principale</span><span class="sxs-lookup"><span data-stu-id="2e2c6-114">Major Version Number</span></span> | <span data-ttu-id="2e2c6-115">Int32</span><span class="sxs-lookup"><span data-stu-id="2e2c6-115">Int32</span></span> |
| <span data-ttu-id="2e2c6-116">Numero di versione secondario</span><span class="sxs-lookup"><span data-stu-id="2e2c6-116">Minor Version Number</span></span> | <span data-ttu-id="2e2c6-117">Int32</span><span class="sxs-lookup"><span data-stu-id="2e2c6-117">Int32</span></span> |
| <span data-ttu-id="2e2c6-118">Dati di animazione</span><span class="sxs-lookup"><span data-stu-id="2e2c6-118">Animation Data</span></span> | <span data-ttu-id="2e2c6-119">_vedere la sezione Version_</span><span class="sxs-lookup"><span data-stu-id="2e2c6-119">_see version section_</span></span> |

## <a name="version-10"></a><span data-ttu-id="2e2c6-120">Versione 1,0</span><span class="sxs-lookup"><span data-stu-id="2e2c6-120">Version 1.0</span></span>

<span data-ttu-id="2e2c6-121">I dati di animazione di input sono costituiti da una sequenza di curve di animazione.</span><span class="sxs-lookup"><span data-stu-id="2e2c6-121">The input animation data consists of a sequence of animation curves.</span></span> <span data-ttu-id="2e2c6-122">Il numero e il significato delle curve di animazione sono corretti, ma ogni curva può avere un numero diverso di fotogrammi chiave.</span><span class="sxs-lookup"><span data-stu-id="2e2c6-122">The number and meaning of animation curves is fixed, but each curve can have a different number of keyframes.</span></span>

| <span data-ttu-id="2e2c6-123">Sezione</span><span class="sxs-lookup"><span data-stu-id="2e2c6-123">Section</span></span> | <span data-ttu-id="2e2c6-124">Tipo</span><span class="sxs-lookup"><span data-stu-id="2e2c6-124">Type</span></span> |
|---------|------|
| <span data-ttu-id="2e2c6-125">Fotocamera</span><span class="sxs-lookup"><span data-stu-id="2e2c6-125">Camera</span></span> | [<span data-ttu-id="2e2c6-126">Pose curve</span><span class="sxs-lookup"><span data-stu-id="2e2c6-126">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="2e2c6-127">Mano rilevata a sinistra</span><span class="sxs-lookup"><span data-stu-id="2e2c6-127">Hand Tracked Left</span></span> | [<span data-ttu-id="2e2c6-128">Curva booleana</span><span class="sxs-lookup"><span data-stu-id="2e2c6-128">Boolean Curve</span></span>](#boolean-curve) |
| <span data-ttu-id="2e2c6-129">Rilevamento a destra della mano</span><span class="sxs-lookup"><span data-stu-id="2e2c6-129">Hand Tracked Right</span></span> | [<span data-ttu-id="2e2c6-130">Curva booleana</span><span class="sxs-lookup"><span data-stu-id="2e2c6-130">Boolean Curve</span></span>](#boolean-curve) |
| <span data-ttu-id="2e2c6-131">Mano pizzicata a sinistra</span><span class="sxs-lookup"><span data-stu-id="2e2c6-131">Hand Pinching Left</span></span> | [<span data-ttu-id="2e2c6-132">Curva booleana</span><span class="sxs-lookup"><span data-stu-id="2e2c6-132">Boolean Curve</span></span>](#boolean-curve) |
| <span data-ttu-id="2e2c6-133">Pizzica a destra</span><span class="sxs-lookup"><span data-stu-id="2e2c6-133">Hand Pinching Right</span></span> | [<span data-ttu-id="2e2c6-134">Curva booleana</span><span class="sxs-lookup"><span data-stu-id="2e2c6-134">Boolean Curve</span></span>](#boolean-curve) |
| <span data-ttu-id="2e2c6-135">Giunzioni a sinistra</span><span class="sxs-lookup"><span data-stu-id="2e2c6-135">Hand Joints Left</span></span> | [<span data-ttu-id="2e2c6-136">Curve di pose congiunte</span><span class="sxs-lookup"><span data-stu-id="2e2c6-136">Joint Pose Curves</span></span>](#joint-pose-curves) |
| <span data-ttu-id="2e2c6-137">Giunzioni a destra</span><span class="sxs-lookup"><span data-stu-id="2e2c6-137">Hand Joints Right</span></span> | [<span data-ttu-id="2e2c6-138">Curve di pose congiunte</span><span class="sxs-lookup"><span data-stu-id="2e2c6-138">Joint Pose Curves</span></span>](#joint-pose-curves) |

### <a name="joint-pose-curves"></a><span data-ttu-id="2e2c6-139">Curve di pose congiunte</span><span class="sxs-lookup"><span data-stu-id="2e2c6-139">Joint pose curves</span></span>

<span data-ttu-id="2e2c6-140">Per ogni mano, viene archiviata una sequenza di curve di animazione congiunta.</span><span class="sxs-lookup"><span data-stu-id="2e2c6-140">For each hand a sequence of joint animation curves is stored.</span></span> <span data-ttu-id="2e2c6-141">Il numero di giunzioni è fisso e viene archiviato un set di curve di pose per ogni giunzione.</span><span class="sxs-lookup"><span data-stu-id="2e2c6-141">The number of joints is fixed, and a set of pose curves is stored for each joint.</span></span>

| <span data-ttu-id="2e2c6-142">Sezione</span><span class="sxs-lookup"><span data-stu-id="2e2c6-142">Section</span></span> | <span data-ttu-id="2e2c6-143">Tipo</span><span class="sxs-lookup"><span data-stu-id="2e2c6-143">Type</span></span> |
|---------|------|
| <span data-ttu-id="2e2c6-144">nessuno</span><span class="sxs-lookup"><span data-stu-id="2e2c6-144">None</span></span> | [<span data-ttu-id="2e2c6-145">Pose curve</span><span class="sxs-lookup"><span data-stu-id="2e2c6-145">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="2e2c6-146">Del polso</span><span class="sxs-lookup"><span data-stu-id="2e2c6-146">Wrist</span></span> | [<span data-ttu-id="2e2c6-147">Pose curve</span><span class="sxs-lookup"><span data-stu-id="2e2c6-147">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="2e2c6-148">Palm</span><span class="sxs-lookup"><span data-stu-id="2e2c6-148">Palm</span></span> | [<span data-ttu-id="2e2c6-149">Pose curve</span><span class="sxs-lookup"><span data-stu-id="2e2c6-149">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="2e2c6-150">ThumbMetacarpalJoint</span><span class="sxs-lookup"><span data-stu-id="2e2c6-150">ThumbMetacarpalJoint</span></span> | [<span data-ttu-id="2e2c6-151">Pose curve</span><span class="sxs-lookup"><span data-stu-id="2e2c6-151">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="2e2c6-152">ThumbProximalJoint</span><span class="sxs-lookup"><span data-stu-id="2e2c6-152">ThumbProximalJoint</span></span> | [<span data-ttu-id="2e2c6-153">Pose curve</span><span class="sxs-lookup"><span data-stu-id="2e2c6-153">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="2e2c6-154">ThumbDistalJoint</span><span class="sxs-lookup"><span data-stu-id="2e2c6-154">ThumbDistalJoint</span></span> | [<span data-ttu-id="2e2c6-155">Pose curve</span><span class="sxs-lookup"><span data-stu-id="2e2c6-155">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="2e2c6-156">ThumbTip</span><span class="sxs-lookup"><span data-stu-id="2e2c6-156">ThumbTip</span></span> | [<span data-ttu-id="2e2c6-157">Pose curve</span><span class="sxs-lookup"><span data-stu-id="2e2c6-157">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="2e2c6-158">IndexMetacarpal</span><span class="sxs-lookup"><span data-stu-id="2e2c6-158">IndexMetacarpal</span></span> | [<span data-ttu-id="2e2c6-159">Pose curve</span><span class="sxs-lookup"><span data-stu-id="2e2c6-159">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="2e2c6-160">IndexKnuckle</span><span class="sxs-lookup"><span data-stu-id="2e2c6-160">IndexKnuckle</span></span> | [<span data-ttu-id="2e2c6-161">Pose curve</span><span class="sxs-lookup"><span data-stu-id="2e2c6-161">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="2e2c6-162">IndexMiddleJoint</span><span class="sxs-lookup"><span data-stu-id="2e2c6-162">IndexMiddleJoint</span></span> | [<span data-ttu-id="2e2c6-163">Pose curve</span><span class="sxs-lookup"><span data-stu-id="2e2c6-163">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="2e2c6-164">IndexDistalJoint</span><span class="sxs-lookup"><span data-stu-id="2e2c6-164">IndexDistalJoint</span></span> | [<span data-ttu-id="2e2c6-165">Pose curve</span><span class="sxs-lookup"><span data-stu-id="2e2c6-165">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="2e2c6-166">IndexTip</span><span class="sxs-lookup"><span data-stu-id="2e2c6-166">IndexTip</span></span> | [<span data-ttu-id="2e2c6-167">Pose curve</span><span class="sxs-lookup"><span data-stu-id="2e2c6-167">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="2e2c6-168">MiddleMetacarpal</span><span class="sxs-lookup"><span data-stu-id="2e2c6-168">MiddleMetacarpal</span></span> | [<span data-ttu-id="2e2c6-169">Pose curve</span><span class="sxs-lookup"><span data-stu-id="2e2c6-169">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="2e2c6-170">MiddleKnuckle</span><span class="sxs-lookup"><span data-stu-id="2e2c6-170">MiddleKnuckle</span></span> | [<span data-ttu-id="2e2c6-171">Pose curve</span><span class="sxs-lookup"><span data-stu-id="2e2c6-171">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="2e2c6-172">MiddleMiddleJoint</span><span class="sxs-lookup"><span data-stu-id="2e2c6-172">MiddleMiddleJoint</span></span> | [<span data-ttu-id="2e2c6-173">Pose curve</span><span class="sxs-lookup"><span data-stu-id="2e2c6-173">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="2e2c6-174">MiddleDistalJoint</span><span class="sxs-lookup"><span data-stu-id="2e2c6-174">MiddleDistalJoint</span></span> | [<span data-ttu-id="2e2c6-175">Pose curve</span><span class="sxs-lookup"><span data-stu-id="2e2c6-175">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="2e2c6-176">MiddleTip</span><span class="sxs-lookup"><span data-stu-id="2e2c6-176">MiddleTip</span></span> | [<span data-ttu-id="2e2c6-177">Pose curve</span><span class="sxs-lookup"><span data-stu-id="2e2c6-177">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="2e2c6-178">RingMetacarpal</span><span class="sxs-lookup"><span data-stu-id="2e2c6-178">RingMetacarpal</span></span> | [<span data-ttu-id="2e2c6-179">Pose curve</span><span class="sxs-lookup"><span data-stu-id="2e2c6-179">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="2e2c6-180">RingKnuckle</span><span class="sxs-lookup"><span data-stu-id="2e2c6-180">RingKnuckle</span></span> | [<span data-ttu-id="2e2c6-181">Pose curve</span><span class="sxs-lookup"><span data-stu-id="2e2c6-181">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="2e2c6-182">RingMiddleJoint</span><span class="sxs-lookup"><span data-stu-id="2e2c6-182">RingMiddleJoint</span></span> | [<span data-ttu-id="2e2c6-183">Pose curve</span><span class="sxs-lookup"><span data-stu-id="2e2c6-183">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="2e2c6-184">RingDistalJoint</span><span class="sxs-lookup"><span data-stu-id="2e2c6-184">RingDistalJoint</span></span> | [<span data-ttu-id="2e2c6-185">Pose curve</span><span class="sxs-lookup"><span data-stu-id="2e2c6-185">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="2e2c6-186">RingTip</span><span class="sxs-lookup"><span data-stu-id="2e2c6-186">RingTip</span></span> | [<span data-ttu-id="2e2c6-187">Pose curve</span><span class="sxs-lookup"><span data-stu-id="2e2c6-187">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="2e2c6-188">PinkyMetacarpal</span><span class="sxs-lookup"><span data-stu-id="2e2c6-188">PinkyMetacarpal</span></span> | [<span data-ttu-id="2e2c6-189">Pose curve</span><span class="sxs-lookup"><span data-stu-id="2e2c6-189">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="2e2c6-190">PinkyKnuckle</span><span class="sxs-lookup"><span data-stu-id="2e2c6-190">PinkyKnuckle</span></span> | [<span data-ttu-id="2e2c6-191">Pose curve</span><span class="sxs-lookup"><span data-stu-id="2e2c6-191">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="2e2c6-192">PinkyMiddleJoint</span><span class="sxs-lookup"><span data-stu-id="2e2c6-192">PinkyMiddleJoint</span></span> | [<span data-ttu-id="2e2c6-193">Pose curve</span><span class="sxs-lookup"><span data-stu-id="2e2c6-193">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="2e2c6-194">PinkyDistalJoint</span><span class="sxs-lookup"><span data-stu-id="2e2c6-194">PinkyDistalJoint</span></span> | [<span data-ttu-id="2e2c6-195">Pose curve</span><span class="sxs-lookup"><span data-stu-id="2e2c6-195">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="2e2c6-196">PinkyTip</span><span class="sxs-lookup"><span data-stu-id="2e2c6-196">PinkyTip</span></span> | [<span data-ttu-id="2e2c6-197">Pose curve</span><span class="sxs-lookup"><span data-stu-id="2e2c6-197">Pose Curves</span></span>](#pose-curves) |

### <a name="pose-curves"></a><span data-ttu-id="2e2c6-198">Pose curve</span><span class="sxs-lookup"><span data-stu-id="2e2c6-198">Pose curves</span></span>

<span data-ttu-id="2e2c6-199">Le curve pose sono una sequenza di 3 curve di animazione per il vettore di posizione, seguite da 4 curve di animazione per il quaternione di rotazione.</span><span class="sxs-lookup"><span data-stu-id="2e2c6-199">Pose curves are a sequence of 3 animation curves for the position vector, followed by 4 animation curves for the rotation quaternion.</span></span>

| <span data-ttu-id="2e2c6-200">Sezione</span><span class="sxs-lookup"><span data-stu-id="2e2c6-200">Section</span></span> | <span data-ttu-id="2e2c6-201">Tipo</span><span class="sxs-lookup"><span data-stu-id="2e2c6-201">Type</span></span> |
|---------|------|
| <span data-ttu-id="2e2c6-202">Posizione X</span><span class="sxs-lookup"><span data-stu-id="2e2c6-202">Position X</span></span> | [<span data-ttu-id="2e2c6-203">Curva float</span><span class="sxs-lookup"><span data-stu-id="2e2c6-203">Float Curve</span></span>](#float-curve) |
| <span data-ttu-id="2e2c6-204">Posizione Y</span><span class="sxs-lookup"><span data-stu-id="2e2c6-204">Position Y</span></span> | [<span data-ttu-id="2e2c6-205">Curva float</span><span class="sxs-lookup"><span data-stu-id="2e2c6-205">Float Curve</span></span>](#float-curve) |
| <span data-ttu-id="2e2c6-206">Posizione Z</span><span class="sxs-lookup"><span data-stu-id="2e2c6-206">Position Z</span></span> | [<span data-ttu-id="2e2c6-207">Curva float</span><span class="sxs-lookup"><span data-stu-id="2e2c6-207">Float Curve</span></span>](#float-curve) |
| <span data-ttu-id="2e2c6-208">Rotazione X</span><span class="sxs-lookup"><span data-stu-id="2e2c6-208">Rotation X</span></span> | [<span data-ttu-id="2e2c6-209">Curva float</span><span class="sxs-lookup"><span data-stu-id="2e2c6-209">Float Curve</span></span>](#float-curve) |
| <span data-ttu-id="2e2c6-210">Rotazione Y</span><span class="sxs-lookup"><span data-stu-id="2e2c6-210">Rotation Y</span></span> | [<span data-ttu-id="2e2c6-211">Curva float</span><span class="sxs-lookup"><span data-stu-id="2e2c6-211">Float Curve</span></span>](#float-curve) |
| <span data-ttu-id="2e2c6-212">Rotazione Z</span><span class="sxs-lookup"><span data-stu-id="2e2c6-212">Rotation Z</span></span> | [<span data-ttu-id="2e2c6-213">Curva float</span><span class="sxs-lookup"><span data-stu-id="2e2c6-213">Float Curve</span></span>](#float-curve) |
| <span data-ttu-id="2e2c6-214">Rotazione W</span><span class="sxs-lookup"><span data-stu-id="2e2c6-214">Rotation W</span></span> | [<span data-ttu-id="2e2c6-215">Curva float</span><span class="sxs-lookup"><span data-stu-id="2e2c6-215">Float Curve</span></span>](#float-curve) |

### <a name="float-curve"></a><span data-ttu-id="2e2c6-216">Curva float</span><span class="sxs-lookup"><span data-stu-id="2e2c6-216">Float curve</span></span>

<span data-ttu-id="2e2c6-217">Le curve a virgola mobile sono le curve di Bézier completamente vere con un numero variabile di fotogrammi chiave.</span><span class="sxs-lookup"><span data-stu-id="2e2c6-217">Floating point curves are fully fledged Bézier curves with a variable number of keyframes.</span></span> <span data-ttu-id="2e2c6-218">Ogni fotogramma chiave archivia un valore di ora e una curva, nonché tangenti e pesi sul lato sinistro e destro di ogni fotogramma chiave.</span><span class="sxs-lookup"><span data-stu-id="2e2c6-218">Each keyframe stores a time and a curve value, as well as tangents and weights on the left and right side of each keyframe.</span></span>

| <span data-ttu-id="2e2c6-219">Sezione</span><span class="sxs-lookup"><span data-stu-id="2e2c6-219">Section</span></span> | <span data-ttu-id="2e2c6-220">Tipo</span><span class="sxs-lookup"><span data-stu-id="2e2c6-220">Type</span></span> |
|---------|------|
| <span data-ttu-id="2e2c6-221">Modalità pre-wrapping</span><span class="sxs-lookup"><span data-stu-id="2e2c6-221">Pre-Wrap Mode</span></span> | <span data-ttu-id="2e2c6-222">Int32, [modalità a capo automatico](#wrap-mode)</span><span class="sxs-lookup"><span data-stu-id="2e2c6-222">Int32, [Wrap Mode](#wrap-mode)</span></span> |
| <span data-ttu-id="2e2c6-223">Modalità di post-wrapping</span><span class="sxs-lookup"><span data-stu-id="2e2c6-223">Post-Wrap Mode</span></span> | <span data-ttu-id="2e2c6-224">Int32, [modalità a capo automatico](#wrap-mode)</span><span class="sxs-lookup"><span data-stu-id="2e2c6-224">Int32, [Wrap Mode](#wrap-mode)</span></span> |
| <span data-ttu-id="2e2c6-225">Numero di fotogrammi chiave</span><span class="sxs-lookup"><span data-stu-id="2e2c6-225">Number of keyframes</span></span> | <span data-ttu-id="2e2c6-226">Int32</span><span class="sxs-lookup"><span data-stu-id="2e2c6-226">Int32</span></span> |
| <span data-ttu-id="2e2c6-227">KeyFrames</span><span class="sxs-lookup"><span data-stu-id="2e2c6-227">Keyframes</span></span> | [<span data-ttu-id="2e2c6-228">Fotogramma chiave float</span><span class="sxs-lookup"><span data-stu-id="2e2c6-228">Float Keyframe</span></span>](#float-keyframe) |

### <a name="float-keyframe"></a><span data-ttu-id="2e2c6-229">Fotogramma chiave float</span><span class="sxs-lookup"><span data-stu-id="2e2c6-229">Float keyframe</span></span>

<span data-ttu-id="2e2c6-230">Un fotogramma chiave float archivia i valori della tangente e del peso insieme al valore e all'ora di base.</span><span class="sxs-lookup"><span data-stu-id="2e2c6-230">A float keyframe stores tangent and weight values alongside the basic time and value.</span></span>

| <span data-ttu-id="2e2c6-231">Sezione</span><span class="sxs-lookup"><span data-stu-id="2e2c6-231">Section</span></span> | <span data-ttu-id="2e2c6-232">Tipo</span><span class="sxs-lookup"><span data-stu-id="2e2c6-232">Type</span></span> |
|---------|------|
| <span data-ttu-id="2e2c6-233">Tempo</span><span class="sxs-lookup"><span data-stu-id="2e2c6-233">Time</span></span> | <span data-ttu-id="2e2c6-234">Float32</span><span class="sxs-lookup"><span data-stu-id="2e2c6-234">Float32</span></span> |
| <span data-ttu-id="2e2c6-235">Valore</span><span class="sxs-lookup"><span data-stu-id="2e2c6-235">Value</span></span> | <span data-ttu-id="2e2c6-236">Float32</span><span class="sxs-lookup"><span data-stu-id="2e2c6-236">Float32</span></span> |
| <span data-ttu-id="2e2c6-237">Intangente</span><span class="sxs-lookup"><span data-stu-id="2e2c6-237">InTangent</span></span> | <span data-ttu-id="2e2c6-238">Float32</span><span class="sxs-lookup"><span data-stu-id="2e2c6-238">Float32</span></span> |
| <span data-ttu-id="2e2c6-239">Distangente</span><span class="sxs-lookup"><span data-stu-id="2e2c6-239">OutTangent</span></span> | <span data-ttu-id="2e2c6-240">Float32</span><span class="sxs-lookup"><span data-stu-id="2e2c6-240">Float32</span></span> |
| <span data-ttu-id="2e2c6-241">Peso</span><span class="sxs-lookup"><span data-stu-id="2e2c6-241">InWeight</span></span> | <span data-ttu-id="2e2c6-242">Float32</span><span class="sxs-lookup"><span data-stu-id="2e2c6-242">Float32</span></span> |
| <span data-ttu-id="2e2c6-243">OutWeight</span><span class="sxs-lookup"><span data-stu-id="2e2c6-243">OutWeight</span></span> | <span data-ttu-id="2e2c6-244">Float32</span><span class="sxs-lookup"><span data-stu-id="2e2c6-244">Float32</span></span> |
| <span data-ttu-id="2e2c6-245">WeightedMode</span><span class="sxs-lookup"><span data-stu-id="2e2c6-245">WeightedMode</span></span> | <span data-ttu-id="2e2c6-246">Int32, [modalità ponderata](#weighted-mode)</span><span class="sxs-lookup"><span data-stu-id="2e2c6-246">Int32, [Weighted Mode](#weighted-mode)</span></span> |

### <a name="boolean-curve"></a><span data-ttu-id="2e2c6-247">Curva booleana</span><span class="sxs-lookup"><span data-stu-id="2e2c6-247">Boolean curve</span></span>

<span data-ttu-id="2e2c6-248">Le curve booleane sono semplici sequenze di valori on/off.</span><span class="sxs-lookup"><span data-stu-id="2e2c6-248">Boolean curves are simple sequences of on/off values.</span></span> <span data-ttu-id="2e2c6-249">Su ogni fotogramma chiave, il valore della curva viene immediatamente invertito.</span><span class="sxs-lookup"><span data-stu-id="2e2c6-249">On every keyframe the value of the curve flips immediately.</span></span>

| <span data-ttu-id="2e2c6-250">Sezione</span><span class="sxs-lookup"><span data-stu-id="2e2c6-250">Section</span></span> | <span data-ttu-id="2e2c6-251">Tipo</span><span class="sxs-lookup"><span data-stu-id="2e2c6-251">Type</span></span> |
|---------|------|
| <span data-ttu-id="2e2c6-252">Modalità pre-wrapping</span><span class="sxs-lookup"><span data-stu-id="2e2c6-252">Pre-Wrap Mode</span></span> | <span data-ttu-id="2e2c6-253">Int32, [modalità a capo automatico](#wrap-mode)</span><span class="sxs-lookup"><span data-stu-id="2e2c6-253">Int32, [Wrap Mode](#wrap-mode)</span></span> |
| <span data-ttu-id="2e2c6-254">Modalità di post-wrapping</span><span class="sxs-lookup"><span data-stu-id="2e2c6-254">Post-Wrap Mode</span></span> | <span data-ttu-id="2e2c6-255">Int32, [modalità a capo automatico](#wrap-mode)</span><span class="sxs-lookup"><span data-stu-id="2e2c6-255">Int32, [Wrap Mode](#wrap-mode)</span></span> |
| <span data-ttu-id="2e2c6-256">Numero di fotogrammi chiave</span><span class="sxs-lookup"><span data-stu-id="2e2c6-256">Number of keyframes</span></span> | <span data-ttu-id="2e2c6-257">Int32</span><span class="sxs-lookup"><span data-stu-id="2e2c6-257">Int32</span></span> |
| <span data-ttu-id="2e2c6-258">KeyFrames</span><span class="sxs-lookup"><span data-stu-id="2e2c6-258">Keyframes</span></span> | [<span data-ttu-id="2e2c6-259">Fotogramma chiave booleana</span><span class="sxs-lookup"><span data-stu-id="2e2c6-259">Boolean Keyframe</span></span>](#boolean-keyframe) |

### <a name="boolean-keyframe"></a><span data-ttu-id="2e2c6-260">Fotogramma chiave booleana</span><span class="sxs-lookup"><span data-stu-id="2e2c6-260">Boolean keyframe</span></span>

<span data-ttu-id="2e2c6-261">Un fotogramma chiave booleano archivia solo un'ora e un valore.</span><span class="sxs-lookup"><span data-stu-id="2e2c6-261">A boolean keyframe only stores a time and value.</span></span>

| <span data-ttu-id="2e2c6-262">Sezione</span><span class="sxs-lookup"><span data-stu-id="2e2c6-262">Section</span></span> | <span data-ttu-id="2e2c6-263">Tipo</span><span class="sxs-lookup"><span data-stu-id="2e2c6-263">Type</span></span> |
|---------|------|
| <span data-ttu-id="2e2c6-264">Tempo</span><span class="sxs-lookup"><span data-stu-id="2e2c6-264">Time</span></span> | <span data-ttu-id="2e2c6-265">Float32</span><span class="sxs-lookup"><span data-stu-id="2e2c6-265">Float32</span></span> |
| <span data-ttu-id="2e2c6-266">Valore</span><span class="sxs-lookup"><span data-stu-id="2e2c6-266">Value</span></span> | <span data-ttu-id="2e2c6-267">Float32</span><span class="sxs-lookup"><span data-stu-id="2e2c6-267">Float32</span></span> |

### <a name="wrap-mode"></a><span data-ttu-id="2e2c6-268">Modalità a capo automatico</span><span class="sxs-lookup"><span data-stu-id="2e2c6-268">Wrap mode</span></span>

<span data-ttu-id="2e2c6-269">La semantica delle modalità pre-e post-wrap segue la definizione di [Unity WrapMode](https://docs.unity3d.com/ScriptReference/WrapMode.html) .</span><span class="sxs-lookup"><span data-stu-id="2e2c6-269">The semantics of Pre- and Post-Wrap modes follow the [Unity WrapMode](https://docs.unity3d.com/ScriptReference/WrapMode.html) definition.</span></span> <span data-ttu-id="2e2c6-270">Si tratta di una combinazione dei bit seguenti:</span><span class="sxs-lookup"><span data-stu-id="2e2c6-270">They are a combination of the following bits:</span></span>

| <span data-ttu-id="2e2c6-271">Valore</span><span class="sxs-lookup"><span data-stu-id="2e2c6-271">Value</span></span> | <span data-ttu-id="2e2c6-272">Significato</span><span class="sxs-lookup"><span data-stu-id="2e2c6-272">Meaning</span></span> |
|-------|---------|
| <span data-ttu-id="2e2c6-273">0</span><span class="sxs-lookup"><span data-stu-id="2e2c6-273">0</span></span> | <span data-ttu-id="2e2c6-274">Impostazione predefinita: legge la modalità di ripetizione predefinita impostata su un valore superiore.</span><span class="sxs-lookup"><span data-stu-id="2e2c6-274">Default: Reads the default repeat mode set higher up.</span></span> |
| <span data-ttu-id="2e2c6-275">1</span><span class="sxs-lookup"><span data-stu-id="2e2c6-275">1</span></span> | <span data-ttu-id="2e2c6-276">Una volta: quando il tempo raggiunge la fine del clip di animazione, il clip verrà interrotto automaticamente e l'ora verrà reimpostata all'inizio della clip.</span><span class="sxs-lookup"><span data-stu-id="2e2c6-276">Once: When time reaches the end of the animation clip, the clip will automatically stop playing and time will be reset to beginning of the clip.</span></span> |
| <span data-ttu-id="2e2c6-277">2</span><span class="sxs-lookup"><span data-stu-id="2e2c6-277">2</span></span> | <span data-ttu-id="2e2c6-278">Loop: quando il tempo raggiunge la fine del clip di animazione, l'ora continuerà all'inizio.</span><span class="sxs-lookup"><span data-stu-id="2e2c6-278">Loop: When time reaches the end of the animation clip, time will continue at the beginning.</span></span> |
| <span data-ttu-id="2e2c6-279">4</span><span class="sxs-lookup"><span data-stu-id="2e2c6-279">4</span></span> | <span data-ttu-id="2e2c6-280">PingPong: quando il tempo raggiunge la fine della clip di animazione, l'ora eseguirà il ping di un posto tra l'inizio e la fine.</span><span class="sxs-lookup"><span data-stu-id="2e2c6-280">PingPong: When time reaches the end of the animation clip, time will ping pong back between beginning and end.</span></span> |
| <span data-ttu-id="2e2c6-281">8</span><span class="sxs-lookup"><span data-stu-id="2e2c6-281">8</span></span> | <span data-ttu-id="2e2c6-282">ClampForever: riproduce l'animazione.</span><span class="sxs-lookup"><span data-stu-id="2e2c6-282">ClampForever: Plays back the animation.</span></span> <span data-ttu-id="2e2c6-283">Quando raggiunge la fine, continuerà a riprodurre l'ultimo frame senza interrompere la riproduzione.</span><span class="sxs-lookup"><span data-stu-id="2e2c6-283">When it reaches the end, it will keep playing the last frame and never stop playing.</span></span> |

### <a name="weighted-mode"></a><span data-ttu-id="2e2c6-284">Modalità ponderata</span><span class="sxs-lookup"><span data-stu-id="2e2c6-284">Weighted mode</span></span>

<span data-ttu-id="2e2c6-285">La semantica della modalità ponderata segue la definizione di [Unity WeightedMode](https://docs.unity3d.com/ScriptReference/WeightedMode.html) .</span><span class="sxs-lookup"><span data-stu-id="2e2c6-285">The semantics of the Weighted mode follow the [Unity WeightedMode](https://docs.unity3d.com/ScriptReference/WeightedMode.html) definition.</span></span>

| <span data-ttu-id="2e2c6-286">Valore</span><span class="sxs-lookup"><span data-stu-id="2e2c6-286">Value</span></span> | <span data-ttu-id="2e2c6-287">Significato</span><span class="sxs-lookup"><span data-stu-id="2e2c6-287">Meaning</span></span> |
|-------|---------|
| <span data-ttu-id="2e2c6-288">0</span><span class="sxs-lookup"><span data-stu-id="2e2c6-288">0</span></span> | <span data-ttu-id="2e2c6-289">None: escludere sia il peso che il peso quando si calcolano i segmenti della curva.</span><span class="sxs-lookup"><span data-stu-id="2e2c6-289">None: Exclude both inWeight or outWeight when calculating curve segments.</span></span> |
| <span data-ttu-id="2e2c6-290">1</span><span class="sxs-lookup"><span data-stu-id="2e2c6-290">1</span></span> | <span data-ttu-id="2e2c6-291">In: includere il peso durante il calcolo del segmento della curva precedente.</span><span class="sxs-lookup"><span data-stu-id="2e2c6-291">In: Include inWeight when calculating the previous curve segment.</span></span> |
| <span data-ttu-id="2e2c6-292">2</span><span class="sxs-lookup"><span data-stu-id="2e2c6-292">2</span></span> | <span data-ttu-id="2e2c6-293">Out: includere l'outgramma durante il calcolo del segmento di curva successivo.</span><span class="sxs-lookup"><span data-stu-id="2e2c6-293">Out: Include outWeight when calculating the next curve segment.</span></span> |
| <span data-ttu-id="2e2c6-294">3</span><span class="sxs-lookup"><span data-stu-id="2e2c6-294">3</span></span> | <span data-ttu-id="2e2c6-295">Entrambi: includono il peso e il peso quando si calcolano i segmenti della curva.</span><span class="sxs-lookup"><span data-stu-id="2e2c6-295">Both: Include inWeight and outWeight when calculating curve segments.</span></span> |

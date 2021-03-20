---
title: InputAnimationFileFormat
description: Documentazione sulla specifica del formato di file binario di animazione di input in MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
ms.localizationpriority: medium
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: dc9e474863421dae185c7b5566b8ba46a3597221
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2021
ms.locfileid: "104688881"
---
# <a name="input-animation-binary-file-format-specification"></a><span data-ttu-id="54e62-104">Specifica del formato file binario animazione input</span><span class="sxs-lookup"><span data-stu-id="54e62-104">Input animation binary file format specification</span></span>

## <a name="overall-structure"></a><span data-ttu-id="54e62-105">Struttura complessiva</span><span class="sxs-lookup"><span data-stu-id="54e62-105">Overall structure</span></span>

<span data-ttu-id="54e62-106">Il file binario di animazione di input inizia con un numero intero a 64 bit.</span><span class="sxs-lookup"><span data-stu-id="54e62-106">The input animation binary file begins with a 64 bit integer magic number.</span></span> <span data-ttu-id="54e62-107">Il valore di questo numero in notazione esadecimale è `0x6a8faf6e0f9e42c6` e può essere usato per identificare i file di animazione di input validi.</span><span class="sxs-lookup"><span data-stu-id="54e62-107">The value of this number in hexadecimal notation is `0x6a8faf6e0f9e42c6` and can be used to identify valid input animation files.</span></span>

<span data-ttu-id="54e62-108">Gli otto byte successivi sono due valori Int32 che dichiarano il numero di versione principale e secondario del file.</span><span class="sxs-lookup"><span data-stu-id="54e62-108">The next eight bytes are two Int32 values declaring the major and minor version number of the file.</span></span>

<span data-ttu-id="54e62-109">Il resto del file viene occupato dai dati di animazione, che possono variare tra i numeri di versione.</span><span class="sxs-lookup"><span data-stu-id="54e62-109">The rest of the file is taken up by animation data, which may change between version numbers.</span></span>

| <span data-ttu-id="54e62-110">Sezione</span><span class="sxs-lookup"><span data-stu-id="54e62-110">Section</span></span> | <span data-ttu-id="54e62-111">Tipo</span><span class="sxs-lookup"><span data-stu-id="54e62-111">Type</span></span> |
|---------|------|
| <span data-ttu-id="54e62-112">Numero magico</span><span class="sxs-lookup"><span data-stu-id="54e62-112">Magic Number</span></span> | <span data-ttu-id="54e62-113">Int64</span><span class="sxs-lookup"><span data-stu-id="54e62-113">Int64</span></span> |
| <span data-ttu-id="54e62-114">Numero di versione principale</span><span class="sxs-lookup"><span data-stu-id="54e62-114">Major Version Number</span></span> | <span data-ttu-id="54e62-115">Int32</span><span class="sxs-lookup"><span data-stu-id="54e62-115">Int32</span></span> |
| <span data-ttu-id="54e62-116">Numero di versione secondario</span><span class="sxs-lookup"><span data-stu-id="54e62-116">Minor Version Number</span></span> | <span data-ttu-id="54e62-117">Int32</span><span class="sxs-lookup"><span data-stu-id="54e62-117">Int32</span></span> |
| <span data-ttu-id="54e62-118">Dati di animazione</span><span class="sxs-lookup"><span data-stu-id="54e62-118">Animation Data</span></span> | <span data-ttu-id="54e62-119">_vedere la sezione Version_</span><span class="sxs-lookup"><span data-stu-id="54e62-119">_see version section_</span></span> |

## <a name="version-10"></a><span data-ttu-id="54e62-120">Versione 1,0</span><span class="sxs-lookup"><span data-stu-id="54e62-120">Version 1.0</span></span>

<span data-ttu-id="54e62-121">I dati di animazione di input sono costituiti da una sequenza di curve di animazione.</span><span class="sxs-lookup"><span data-stu-id="54e62-121">The input animation data consists of a sequence of animation curves.</span></span> <span data-ttu-id="54e62-122">Il numero e il significato delle curve di animazione sono corretti, ma ogni curva può avere un numero diverso di fotogrammi chiave.</span><span class="sxs-lookup"><span data-stu-id="54e62-122">The number and meaning of animation curves is fixed, but each curve can have a different number of keyframes.</span></span>

| <span data-ttu-id="54e62-123">Sezione</span><span class="sxs-lookup"><span data-stu-id="54e62-123">Section</span></span> | <span data-ttu-id="54e62-124">Tipo</span><span class="sxs-lookup"><span data-stu-id="54e62-124">Type</span></span> |
|---------|------|
| <span data-ttu-id="54e62-125">Fotocamera</span><span class="sxs-lookup"><span data-stu-id="54e62-125">Camera</span></span> | [<span data-ttu-id="54e62-126">Pose curve</span><span class="sxs-lookup"><span data-stu-id="54e62-126">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="54e62-127">Mano rilevata a sinistra</span><span class="sxs-lookup"><span data-stu-id="54e62-127">Hand Tracked Left</span></span> | [<span data-ttu-id="54e62-128">Curva booleana</span><span class="sxs-lookup"><span data-stu-id="54e62-128">Boolean Curve</span></span>](#boolean-curve) |
| <span data-ttu-id="54e62-129">Rilevamento a destra della mano</span><span class="sxs-lookup"><span data-stu-id="54e62-129">Hand Tracked Right</span></span> | [<span data-ttu-id="54e62-130">Curva booleana</span><span class="sxs-lookup"><span data-stu-id="54e62-130">Boolean Curve</span></span>](#boolean-curve) |
| <span data-ttu-id="54e62-131">Mano pizzicata a sinistra</span><span class="sxs-lookup"><span data-stu-id="54e62-131">Hand Pinching Left</span></span> | [<span data-ttu-id="54e62-132">Curva booleana</span><span class="sxs-lookup"><span data-stu-id="54e62-132">Boolean Curve</span></span>](#boolean-curve) |
| <span data-ttu-id="54e62-133">Pizzica a destra</span><span class="sxs-lookup"><span data-stu-id="54e62-133">Hand Pinching Right</span></span> | [<span data-ttu-id="54e62-134">Curva booleana</span><span class="sxs-lookup"><span data-stu-id="54e62-134">Boolean Curve</span></span>](#boolean-curve) |
| <span data-ttu-id="54e62-135">Giunzioni a sinistra</span><span class="sxs-lookup"><span data-stu-id="54e62-135">Hand Joints Left</span></span> | [<span data-ttu-id="54e62-136">Curve di pose congiunte</span><span class="sxs-lookup"><span data-stu-id="54e62-136">Joint Pose Curves</span></span>](#joint-pose-curves) |
| <span data-ttu-id="54e62-137">Giunzioni a destra</span><span class="sxs-lookup"><span data-stu-id="54e62-137">Hand Joints Right</span></span> | [<span data-ttu-id="54e62-138">Curve di pose congiunte</span><span class="sxs-lookup"><span data-stu-id="54e62-138">Joint Pose Curves</span></span>](#joint-pose-curves) |

### <a name="joint-pose-curves"></a><span data-ttu-id="54e62-139">Curve di pose congiunte</span><span class="sxs-lookup"><span data-stu-id="54e62-139">Joint pose curves</span></span>

<span data-ttu-id="54e62-140">Per ogni mano, viene archiviata una sequenza di curve di animazione congiunta.</span><span class="sxs-lookup"><span data-stu-id="54e62-140">For each hand a sequence of joint animation curves is stored.</span></span> <span data-ttu-id="54e62-141">Il numero di giunzioni è fisso e viene archiviato un set di curve di pose per ogni giunzione.</span><span class="sxs-lookup"><span data-stu-id="54e62-141">The number of joints is fixed, and a set of pose curves is stored for each joint.</span></span>

| <span data-ttu-id="54e62-142">Sezione</span><span class="sxs-lookup"><span data-stu-id="54e62-142">Section</span></span> | <span data-ttu-id="54e62-143">Tipo</span><span class="sxs-lookup"><span data-stu-id="54e62-143">Type</span></span> |
|---------|------|
| <span data-ttu-id="54e62-144">nessuno</span><span class="sxs-lookup"><span data-stu-id="54e62-144">None</span></span> | [<span data-ttu-id="54e62-145">Pose curve</span><span class="sxs-lookup"><span data-stu-id="54e62-145">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="54e62-146">Del polso</span><span class="sxs-lookup"><span data-stu-id="54e62-146">Wrist</span></span> | [<span data-ttu-id="54e62-147">Pose curve</span><span class="sxs-lookup"><span data-stu-id="54e62-147">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="54e62-148">Palm</span><span class="sxs-lookup"><span data-stu-id="54e62-148">Palm</span></span> | [<span data-ttu-id="54e62-149">Pose curve</span><span class="sxs-lookup"><span data-stu-id="54e62-149">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="54e62-150">ThumbMetacarpalJoint</span><span class="sxs-lookup"><span data-stu-id="54e62-150">ThumbMetacarpalJoint</span></span> | [<span data-ttu-id="54e62-151">Pose curve</span><span class="sxs-lookup"><span data-stu-id="54e62-151">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="54e62-152">ThumbProximalJoint</span><span class="sxs-lookup"><span data-stu-id="54e62-152">ThumbProximalJoint</span></span> | [<span data-ttu-id="54e62-153">Pose curve</span><span class="sxs-lookup"><span data-stu-id="54e62-153">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="54e62-154">ThumbDistalJoint</span><span class="sxs-lookup"><span data-stu-id="54e62-154">ThumbDistalJoint</span></span> | [<span data-ttu-id="54e62-155">Pose curve</span><span class="sxs-lookup"><span data-stu-id="54e62-155">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="54e62-156">ThumbTip</span><span class="sxs-lookup"><span data-stu-id="54e62-156">ThumbTip</span></span> | [<span data-ttu-id="54e62-157">Pose curve</span><span class="sxs-lookup"><span data-stu-id="54e62-157">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="54e62-158">IndexMetacarpal</span><span class="sxs-lookup"><span data-stu-id="54e62-158">IndexMetacarpal</span></span> | [<span data-ttu-id="54e62-159">Pose curve</span><span class="sxs-lookup"><span data-stu-id="54e62-159">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="54e62-160">IndexKnuckle</span><span class="sxs-lookup"><span data-stu-id="54e62-160">IndexKnuckle</span></span> | [<span data-ttu-id="54e62-161">Pose curve</span><span class="sxs-lookup"><span data-stu-id="54e62-161">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="54e62-162">IndexMiddleJoint</span><span class="sxs-lookup"><span data-stu-id="54e62-162">IndexMiddleJoint</span></span> | [<span data-ttu-id="54e62-163">Pose curve</span><span class="sxs-lookup"><span data-stu-id="54e62-163">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="54e62-164">IndexDistalJoint</span><span class="sxs-lookup"><span data-stu-id="54e62-164">IndexDistalJoint</span></span> | [<span data-ttu-id="54e62-165">Pose curve</span><span class="sxs-lookup"><span data-stu-id="54e62-165">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="54e62-166">IndexTip</span><span class="sxs-lookup"><span data-stu-id="54e62-166">IndexTip</span></span> | [<span data-ttu-id="54e62-167">Pose curve</span><span class="sxs-lookup"><span data-stu-id="54e62-167">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="54e62-168">MiddleMetacarpal</span><span class="sxs-lookup"><span data-stu-id="54e62-168">MiddleMetacarpal</span></span> | [<span data-ttu-id="54e62-169">Pose curve</span><span class="sxs-lookup"><span data-stu-id="54e62-169">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="54e62-170">MiddleKnuckle</span><span class="sxs-lookup"><span data-stu-id="54e62-170">MiddleKnuckle</span></span> | [<span data-ttu-id="54e62-171">Pose curve</span><span class="sxs-lookup"><span data-stu-id="54e62-171">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="54e62-172">MiddleMiddleJoint</span><span class="sxs-lookup"><span data-stu-id="54e62-172">MiddleMiddleJoint</span></span> | [<span data-ttu-id="54e62-173">Pose curve</span><span class="sxs-lookup"><span data-stu-id="54e62-173">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="54e62-174">MiddleDistalJoint</span><span class="sxs-lookup"><span data-stu-id="54e62-174">MiddleDistalJoint</span></span> | [<span data-ttu-id="54e62-175">Pose curve</span><span class="sxs-lookup"><span data-stu-id="54e62-175">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="54e62-176">MiddleTip</span><span class="sxs-lookup"><span data-stu-id="54e62-176">MiddleTip</span></span> | [<span data-ttu-id="54e62-177">Pose curve</span><span class="sxs-lookup"><span data-stu-id="54e62-177">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="54e62-178">RingMetacarpal</span><span class="sxs-lookup"><span data-stu-id="54e62-178">RingMetacarpal</span></span> | [<span data-ttu-id="54e62-179">Pose curve</span><span class="sxs-lookup"><span data-stu-id="54e62-179">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="54e62-180">RingKnuckle</span><span class="sxs-lookup"><span data-stu-id="54e62-180">RingKnuckle</span></span> | [<span data-ttu-id="54e62-181">Pose curve</span><span class="sxs-lookup"><span data-stu-id="54e62-181">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="54e62-182">RingMiddleJoint</span><span class="sxs-lookup"><span data-stu-id="54e62-182">RingMiddleJoint</span></span> | [<span data-ttu-id="54e62-183">Pose curve</span><span class="sxs-lookup"><span data-stu-id="54e62-183">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="54e62-184">RingDistalJoint</span><span class="sxs-lookup"><span data-stu-id="54e62-184">RingDistalJoint</span></span> | [<span data-ttu-id="54e62-185">Pose curve</span><span class="sxs-lookup"><span data-stu-id="54e62-185">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="54e62-186">RingTip</span><span class="sxs-lookup"><span data-stu-id="54e62-186">RingTip</span></span> | [<span data-ttu-id="54e62-187">Pose curve</span><span class="sxs-lookup"><span data-stu-id="54e62-187">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="54e62-188">PinkyMetacarpal</span><span class="sxs-lookup"><span data-stu-id="54e62-188">PinkyMetacarpal</span></span> | [<span data-ttu-id="54e62-189">Pose curve</span><span class="sxs-lookup"><span data-stu-id="54e62-189">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="54e62-190">PinkyKnuckle</span><span class="sxs-lookup"><span data-stu-id="54e62-190">PinkyKnuckle</span></span> | [<span data-ttu-id="54e62-191">Pose curve</span><span class="sxs-lookup"><span data-stu-id="54e62-191">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="54e62-192">PinkyMiddleJoint</span><span class="sxs-lookup"><span data-stu-id="54e62-192">PinkyMiddleJoint</span></span> | [<span data-ttu-id="54e62-193">Pose curve</span><span class="sxs-lookup"><span data-stu-id="54e62-193">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="54e62-194">PinkyDistalJoint</span><span class="sxs-lookup"><span data-stu-id="54e62-194">PinkyDistalJoint</span></span> | [<span data-ttu-id="54e62-195">Pose curve</span><span class="sxs-lookup"><span data-stu-id="54e62-195">Pose Curves</span></span>](#pose-curves) |
| <span data-ttu-id="54e62-196">PinkyTip</span><span class="sxs-lookup"><span data-stu-id="54e62-196">PinkyTip</span></span> | [<span data-ttu-id="54e62-197">Pose curve</span><span class="sxs-lookup"><span data-stu-id="54e62-197">Pose Curves</span></span>](#pose-curves) |

### <a name="pose-curves"></a><span data-ttu-id="54e62-198">Pose curve</span><span class="sxs-lookup"><span data-stu-id="54e62-198">Pose curves</span></span>

<span data-ttu-id="54e62-199">Le curve pose sono una sequenza di 3 curve di animazione per il vettore di posizione, seguite da 4 curve di animazione per il quaternione di rotazione.</span><span class="sxs-lookup"><span data-stu-id="54e62-199">Pose curves are a sequence of 3 animation curves for the position vector, followed by 4 animation curves for the rotation quaternion.</span></span>

| <span data-ttu-id="54e62-200">Sezione</span><span class="sxs-lookup"><span data-stu-id="54e62-200">Section</span></span> | <span data-ttu-id="54e62-201">Tipo</span><span class="sxs-lookup"><span data-stu-id="54e62-201">Type</span></span> |
|---------|------|
| <span data-ttu-id="54e62-202">Posizione X</span><span class="sxs-lookup"><span data-stu-id="54e62-202">Position X</span></span> | [<span data-ttu-id="54e62-203">Curva float</span><span class="sxs-lookup"><span data-stu-id="54e62-203">Float Curve</span></span>](#float-curve) |
| <span data-ttu-id="54e62-204">Posizione Y</span><span class="sxs-lookup"><span data-stu-id="54e62-204">Position Y</span></span> | [<span data-ttu-id="54e62-205">Curva float</span><span class="sxs-lookup"><span data-stu-id="54e62-205">Float Curve</span></span>](#float-curve) |
| <span data-ttu-id="54e62-206">Posizione Z</span><span class="sxs-lookup"><span data-stu-id="54e62-206">Position Z</span></span> | [<span data-ttu-id="54e62-207">Curva float</span><span class="sxs-lookup"><span data-stu-id="54e62-207">Float Curve</span></span>](#float-curve) |
| <span data-ttu-id="54e62-208">Rotazione X</span><span class="sxs-lookup"><span data-stu-id="54e62-208">Rotation X</span></span> | [<span data-ttu-id="54e62-209">Curva float</span><span class="sxs-lookup"><span data-stu-id="54e62-209">Float Curve</span></span>](#float-curve) |
| <span data-ttu-id="54e62-210">Rotazione Y</span><span class="sxs-lookup"><span data-stu-id="54e62-210">Rotation Y</span></span> | [<span data-ttu-id="54e62-211">Curva float</span><span class="sxs-lookup"><span data-stu-id="54e62-211">Float Curve</span></span>](#float-curve) |
| <span data-ttu-id="54e62-212">Rotazione Z</span><span class="sxs-lookup"><span data-stu-id="54e62-212">Rotation Z</span></span> | [<span data-ttu-id="54e62-213">Curva float</span><span class="sxs-lookup"><span data-stu-id="54e62-213">Float Curve</span></span>](#float-curve) |
| <span data-ttu-id="54e62-214">Rotazione W</span><span class="sxs-lookup"><span data-stu-id="54e62-214">Rotation W</span></span> | [<span data-ttu-id="54e62-215">Curva float</span><span class="sxs-lookup"><span data-stu-id="54e62-215">Float Curve</span></span>](#float-curve) |

### <a name="float-curve"></a><span data-ttu-id="54e62-216">Curva float</span><span class="sxs-lookup"><span data-stu-id="54e62-216">Float curve</span></span>

<span data-ttu-id="54e62-217">Le curve a virgola mobile sono le curve di Bézier completamente vere con un numero variabile di fotogrammi chiave.</span><span class="sxs-lookup"><span data-stu-id="54e62-217">Floating point curves are fully fledged Bézier curves with a variable number of keyframes.</span></span> <span data-ttu-id="54e62-218">Ogni fotogramma chiave archivia un valore di ora e una curva, nonché tangenti e pesi sul lato sinistro e destro di ogni fotogramma chiave.</span><span class="sxs-lookup"><span data-stu-id="54e62-218">Each keyframe stores a time and a curve value, as well as tangents and weights on the left and right side of each keyframe.</span></span>

| <span data-ttu-id="54e62-219">Sezione</span><span class="sxs-lookup"><span data-stu-id="54e62-219">Section</span></span> | <span data-ttu-id="54e62-220">Tipo</span><span class="sxs-lookup"><span data-stu-id="54e62-220">Type</span></span> |
|---------|------|
| <span data-ttu-id="54e62-221">Modalità pre-wrapping</span><span class="sxs-lookup"><span data-stu-id="54e62-221">Pre-Wrap Mode</span></span> | <span data-ttu-id="54e62-222">Int32, [modalità a capo automatico](#wrap-mode)</span><span class="sxs-lookup"><span data-stu-id="54e62-222">Int32, [Wrap Mode](#wrap-mode)</span></span> |
| <span data-ttu-id="54e62-223">Modalità di post-wrapping</span><span class="sxs-lookup"><span data-stu-id="54e62-223">Post-Wrap Mode</span></span> | <span data-ttu-id="54e62-224">Int32, [modalità a capo automatico](#wrap-mode)</span><span class="sxs-lookup"><span data-stu-id="54e62-224">Int32, [Wrap Mode](#wrap-mode)</span></span> |
| <span data-ttu-id="54e62-225">Numero di fotogrammi chiave</span><span class="sxs-lookup"><span data-stu-id="54e62-225">Number of keyframes</span></span> | <span data-ttu-id="54e62-226">Int32</span><span class="sxs-lookup"><span data-stu-id="54e62-226">Int32</span></span> |
| <span data-ttu-id="54e62-227">KeyFrames</span><span class="sxs-lookup"><span data-stu-id="54e62-227">Keyframes</span></span> | [<span data-ttu-id="54e62-228">Fotogramma chiave float</span><span class="sxs-lookup"><span data-stu-id="54e62-228">Float Keyframe</span></span>](#float-keyframe) |

### <a name="float-keyframe"></a><span data-ttu-id="54e62-229">Fotogramma chiave float</span><span class="sxs-lookup"><span data-stu-id="54e62-229">Float keyframe</span></span>

<span data-ttu-id="54e62-230">Un fotogramma chiave float archivia i valori della tangente e del peso insieme al valore e all'ora di base.</span><span class="sxs-lookup"><span data-stu-id="54e62-230">A float keyframe stores tangent and weight values alongside the basic time and value.</span></span>

| <span data-ttu-id="54e62-231">Sezione</span><span class="sxs-lookup"><span data-stu-id="54e62-231">Section</span></span> | <span data-ttu-id="54e62-232">Tipo</span><span class="sxs-lookup"><span data-stu-id="54e62-232">Type</span></span> |
|---------|------|
| <span data-ttu-id="54e62-233">Tempo</span><span class="sxs-lookup"><span data-stu-id="54e62-233">Time</span></span> | <span data-ttu-id="54e62-234">Float32</span><span class="sxs-lookup"><span data-stu-id="54e62-234">Float32</span></span> |
| <span data-ttu-id="54e62-235">Valore</span><span class="sxs-lookup"><span data-stu-id="54e62-235">Value</span></span> | <span data-ttu-id="54e62-236">Float32</span><span class="sxs-lookup"><span data-stu-id="54e62-236">Float32</span></span> |
| <span data-ttu-id="54e62-237">Intangente</span><span class="sxs-lookup"><span data-stu-id="54e62-237">InTangent</span></span> | <span data-ttu-id="54e62-238">Float32</span><span class="sxs-lookup"><span data-stu-id="54e62-238">Float32</span></span> |
| <span data-ttu-id="54e62-239">Distangente</span><span class="sxs-lookup"><span data-stu-id="54e62-239">OutTangent</span></span> | <span data-ttu-id="54e62-240">Float32</span><span class="sxs-lookup"><span data-stu-id="54e62-240">Float32</span></span> |
| <span data-ttu-id="54e62-241">Peso</span><span class="sxs-lookup"><span data-stu-id="54e62-241">InWeight</span></span> | <span data-ttu-id="54e62-242">Float32</span><span class="sxs-lookup"><span data-stu-id="54e62-242">Float32</span></span> |
| <span data-ttu-id="54e62-243">OutWeight</span><span class="sxs-lookup"><span data-stu-id="54e62-243">OutWeight</span></span> | <span data-ttu-id="54e62-244">Float32</span><span class="sxs-lookup"><span data-stu-id="54e62-244">Float32</span></span> |
| <span data-ttu-id="54e62-245">WeightedMode</span><span class="sxs-lookup"><span data-stu-id="54e62-245">WeightedMode</span></span> | <span data-ttu-id="54e62-246">Int32, [modalità ponderata](#weighted-mode)</span><span class="sxs-lookup"><span data-stu-id="54e62-246">Int32, [Weighted Mode](#weighted-mode)</span></span> |

### <a name="boolean-curve"></a><span data-ttu-id="54e62-247">Curva booleana</span><span class="sxs-lookup"><span data-stu-id="54e62-247">Boolean curve</span></span>

<span data-ttu-id="54e62-248">Le curve booleane sono semplici sequenze di valori on/off.</span><span class="sxs-lookup"><span data-stu-id="54e62-248">Boolean curves are simple sequences of on/off values.</span></span> <span data-ttu-id="54e62-249">Su ogni fotogramma chiave, il valore della curva viene immediatamente invertito.</span><span class="sxs-lookup"><span data-stu-id="54e62-249">On every keyframe the value of the curve flips immediately.</span></span>

| <span data-ttu-id="54e62-250">Sezione</span><span class="sxs-lookup"><span data-stu-id="54e62-250">Section</span></span> | <span data-ttu-id="54e62-251">Tipo</span><span class="sxs-lookup"><span data-stu-id="54e62-251">Type</span></span> |
|---------|------|
| <span data-ttu-id="54e62-252">Modalità pre-wrapping</span><span class="sxs-lookup"><span data-stu-id="54e62-252">Pre-Wrap Mode</span></span> | <span data-ttu-id="54e62-253">Int32, [modalità a capo automatico](#wrap-mode)</span><span class="sxs-lookup"><span data-stu-id="54e62-253">Int32, [Wrap Mode](#wrap-mode)</span></span> |
| <span data-ttu-id="54e62-254">Modalità di post-wrapping</span><span class="sxs-lookup"><span data-stu-id="54e62-254">Post-Wrap Mode</span></span> | <span data-ttu-id="54e62-255">Int32, [modalità a capo automatico](#wrap-mode)</span><span class="sxs-lookup"><span data-stu-id="54e62-255">Int32, [Wrap Mode](#wrap-mode)</span></span> |
| <span data-ttu-id="54e62-256">Numero di fotogrammi chiave</span><span class="sxs-lookup"><span data-stu-id="54e62-256">Number of keyframes</span></span> | <span data-ttu-id="54e62-257">Int32</span><span class="sxs-lookup"><span data-stu-id="54e62-257">Int32</span></span> |
| <span data-ttu-id="54e62-258">KeyFrames</span><span class="sxs-lookup"><span data-stu-id="54e62-258">Keyframes</span></span> | [<span data-ttu-id="54e62-259">Fotogramma chiave booleana</span><span class="sxs-lookup"><span data-stu-id="54e62-259">Boolean Keyframe</span></span>](#boolean-keyframe) |

### <a name="boolean-keyframe"></a><span data-ttu-id="54e62-260">Fotogramma chiave booleana</span><span class="sxs-lookup"><span data-stu-id="54e62-260">Boolean keyframe</span></span>

<span data-ttu-id="54e62-261">Un fotogramma chiave booleano archivia solo un'ora e un valore.</span><span class="sxs-lookup"><span data-stu-id="54e62-261">A boolean keyframe only stores a time and value.</span></span>

| <span data-ttu-id="54e62-262">Sezione</span><span class="sxs-lookup"><span data-stu-id="54e62-262">Section</span></span> | <span data-ttu-id="54e62-263">Tipo</span><span class="sxs-lookup"><span data-stu-id="54e62-263">Type</span></span> |
|---------|------|
| <span data-ttu-id="54e62-264">Tempo</span><span class="sxs-lookup"><span data-stu-id="54e62-264">Time</span></span> | <span data-ttu-id="54e62-265">Float32</span><span class="sxs-lookup"><span data-stu-id="54e62-265">Float32</span></span> |
| <span data-ttu-id="54e62-266">Valore</span><span class="sxs-lookup"><span data-stu-id="54e62-266">Value</span></span> | <span data-ttu-id="54e62-267">Float32</span><span class="sxs-lookup"><span data-stu-id="54e62-267">Float32</span></span> |

### <a name="wrap-mode"></a><span data-ttu-id="54e62-268">Modalità a capo automatico</span><span class="sxs-lookup"><span data-stu-id="54e62-268">Wrap mode</span></span>

<span data-ttu-id="54e62-269">La semantica delle modalità pre-e post-wrap segue la definizione di [Unity WrapMode](https://docs.unity3d.com/ScriptReference/WrapMode.html) .</span><span class="sxs-lookup"><span data-stu-id="54e62-269">The semantics of Pre- and Post-Wrap modes follow the [Unity WrapMode](https://docs.unity3d.com/ScriptReference/WrapMode.html) definition.</span></span> <span data-ttu-id="54e62-270">Si tratta di una combinazione dei bit seguenti:</span><span class="sxs-lookup"><span data-stu-id="54e62-270">They are a combination of the following bits:</span></span>

| <span data-ttu-id="54e62-271">Valore</span><span class="sxs-lookup"><span data-stu-id="54e62-271">Value</span></span> | <span data-ttu-id="54e62-272">Significato</span><span class="sxs-lookup"><span data-stu-id="54e62-272">Meaning</span></span> |
|-------|---------|
| <span data-ttu-id="54e62-273">0</span><span class="sxs-lookup"><span data-stu-id="54e62-273">0</span></span> | <span data-ttu-id="54e62-274">Impostazione predefinita: legge la modalità di ripetizione predefinita impostata su un valore superiore.</span><span class="sxs-lookup"><span data-stu-id="54e62-274">Default: Reads the default repeat mode set higher up.</span></span> |
| <span data-ttu-id="54e62-275">1</span><span class="sxs-lookup"><span data-stu-id="54e62-275">1</span></span> | <span data-ttu-id="54e62-276">Una volta: quando il tempo raggiunge la fine del clip di animazione, il clip verrà interrotto automaticamente e l'ora verrà reimpostata all'inizio della clip.</span><span class="sxs-lookup"><span data-stu-id="54e62-276">Once: When time reaches the end of the animation clip, the clip will automatically stop playing and time will be reset to beginning of the clip.</span></span> |
| <span data-ttu-id="54e62-277">2</span><span class="sxs-lookup"><span data-stu-id="54e62-277">2</span></span> | <span data-ttu-id="54e62-278">Loop: quando il tempo raggiunge la fine del clip di animazione, l'ora continuerà all'inizio.</span><span class="sxs-lookup"><span data-stu-id="54e62-278">Loop: When time reaches the end of the animation clip, time will continue at the beginning.</span></span> |
| <span data-ttu-id="54e62-279">4</span><span class="sxs-lookup"><span data-stu-id="54e62-279">4</span></span> | <span data-ttu-id="54e62-280">PingPong: quando il tempo raggiunge la fine della clip di animazione, l'ora eseguirà il ping di un posto tra l'inizio e la fine.</span><span class="sxs-lookup"><span data-stu-id="54e62-280">PingPong: When time reaches the end of the animation clip, time will ping pong back between beginning and end.</span></span> |
| <span data-ttu-id="54e62-281">8</span><span class="sxs-lookup"><span data-stu-id="54e62-281">8</span></span> | <span data-ttu-id="54e62-282">ClampForever: riproduce l'animazione.</span><span class="sxs-lookup"><span data-stu-id="54e62-282">ClampForever: Plays back the animation.</span></span> <span data-ttu-id="54e62-283">Quando raggiunge la fine, continuerà a riprodurre l'ultimo frame senza interrompere la riproduzione.</span><span class="sxs-lookup"><span data-stu-id="54e62-283">When it reaches the end, it will keep playing the last frame and never stop playing.</span></span> |

### <a name="weighted-mode"></a><span data-ttu-id="54e62-284">Modalità ponderata</span><span class="sxs-lookup"><span data-stu-id="54e62-284">Weighted mode</span></span>

<span data-ttu-id="54e62-285">La semantica della modalità ponderata segue la definizione di [Unity WeightedMode](https://docs.unity3d.com/ScriptReference/WeightedMode.html) .</span><span class="sxs-lookup"><span data-stu-id="54e62-285">The semantics of the Weighted mode follow the [Unity WeightedMode](https://docs.unity3d.com/ScriptReference/WeightedMode.html) definition.</span></span>

| <span data-ttu-id="54e62-286">Valore</span><span class="sxs-lookup"><span data-stu-id="54e62-286">Value</span></span> | <span data-ttu-id="54e62-287">Significato</span><span class="sxs-lookup"><span data-stu-id="54e62-287">Meaning</span></span> |
|-------|---------|
| <span data-ttu-id="54e62-288">0</span><span class="sxs-lookup"><span data-stu-id="54e62-288">0</span></span> | <span data-ttu-id="54e62-289">None: escludere sia il peso che il peso quando si calcolano i segmenti della curva.</span><span class="sxs-lookup"><span data-stu-id="54e62-289">None: Exclude both inWeight or outWeight when calculating curve segments.</span></span> |
| <span data-ttu-id="54e62-290">1</span><span class="sxs-lookup"><span data-stu-id="54e62-290">1</span></span> | <span data-ttu-id="54e62-291">In: includere il peso durante il calcolo del segmento della curva precedente.</span><span class="sxs-lookup"><span data-stu-id="54e62-291">In: Include inWeight when calculating the previous curve segment.</span></span> |
| <span data-ttu-id="54e62-292">2</span><span class="sxs-lookup"><span data-stu-id="54e62-292">2</span></span> | <span data-ttu-id="54e62-293">Out: includere l'outgramma durante il calcolo del segmento di curva successivo.</span><span class="sxs-lookup"><span data-stu-id="54e62-293">Out: Include outWeight when calculating the next curve segment.</span></span> |
| <span data-ttu-id="54e62-294">3</span><span class="sxs-lookup"><span data-stu-id="54e62-294">3</span></span> | <span data-ttu-id="54e62-295">Entrambi: includono il peso e il peso quando si calcolano i segmenti della curva.</span><span class="sxs-lookup"><span data-stu-id="54e62-295">Both: Include inWeight and outWeight when calculating curve segments.</span></span> |

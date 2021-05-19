---
title: Configurazione della visualizzazione dei limiti
description: Dettagli per configurare il sistema boundary in MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, sistema di limiti,
ms.openlocfilehash: 36717493107b129a7200dd3f912bcbdc3337b9a1
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144492"
---
# <a name="configuring-the-boundary-visualization"></a><span data-ttu-id="b6f4d-104">Configurazione della visualizzazione dei limiti</span><span class="sxs-lookup"><span data-stu-id="b6f4d-104">Configuring the boundary visualization</span></span>

<span data-ttu-id="b6f4d-105">Profilo *di visualizzazione dei limiti* offre opzioni per la configurazione dell'aspetto visivo e di altri parametri correlati per il sistema Boundary.</span><span class="sxs-lookup"><span data-stu-id="b6f4d-105">The *Boundary Visualization Profile* provides options for configuring the visual aesthetics and other related parameters for the Boundary system.</span></span> <span data-ttu-id="b6f4d-106">Le visualizzazioni dei limiti vengono collegate all'oggetto Playspace di realtà mista nella scena e teletrasportate con l'utente.</span><span class="sxs-lookup"><span data-stu-id="b6f4d-106">Boundary visualizations are attached to the Mixed Reality Playspace object in the scene and teleport with the user.</span></span>

## <a name="general-settings"></a><span data-ttu-id="b6f4d-107">Impostazioni generali</span><span class="sxs-lookup"><span data-stu-id="b6f4d-107">General settings</span></span>

![Impostazioni generali per la visualizzazione dei limiti](../images/boundary/BoundaryVisualizationGeneralSettings.png)

### <a name="boundary-height"></a><span data-ttu-id="b6f4d-109">Altezza limite</span><span class="sxs-lookup"><span data-stu-id="b6f4d-109">Boundary height</span></span>

<span data-ttu-id="b6f4d-110">L'altezza del limite indica la distanza sopra il piano terra in cui deve essere eseguito il rendering del controsoffitto limite.</span><span class="sxs-lookup"><span data-stu-id="b6f4d-110">The boundary height indicates the distance above the floor plane at which the boundary ceiling should be rendered.</span></span> <span data-ttu-id="b6f4d-111">Il valore predefinito è 3 metri.</span><span class="sxs-lookup"><span data-stu-id="b6f4d-111">The default value is 3 meters.</span></span>

## <a name="floor-settings"></a><span data-ttu-id="b6f4d-112">Impostazioni del piano</span><span class="sxs-lookup"><span data-stu-id="b6f4d-112">Floor settings</span></span>

![Impostazioni del piano di visualizzazione dei limiti](../images/boundary/BoundaryVisualizationFloorSettings.png)

<span data-ttu-id="b6f4d-114">**Mostra**</span><span class="sxs-lookup"><span data-stu-id="b6f4d-114">**Show**</span></span>

<span data-ttu-id="b6f4d-115">Indica se un piano piano deve essere creato e aggiunto alla scena.</span><span class="sxs-lookup"><span data-stu-id="b6f4d-115">Indicates whether or not a floor plane is to be created and added to the scene.</span></span> <span data-ttu-id="b6f4d-116">Il valore predefinito è true.</span><span class="sxs-lookup"><span data-stu-id="b6f4d-116">The default value is true.</span></span>

<span data-ttu-id="b6f4d-117">**Materiale**</span><span class="sxs-lookup"><span data-stu-id="b6f4d-117">**Material**</span></span>

<span data-ttu-id="b6f4d-118">Indica il materiale da usare durante la creazione del piano terra.</span><span class="sxs-lookup"><span data-stu-id="b6f4d-118">Indicates the material that should be used when creating the floor plane.</span></span>

<span data-ttu-id="b6f4d-119">**Scalabilità**</span><span class="sxs-lookup"><span data-stu-id="b6f4d-119">**Scale**</span></span>

<span data-ttu-id="b6f4d-120">Indica le dimensioni, in metri, del piano da creare.</span><span class="sxs-lookup"><span data-stu-id="b6f4d-120">Indicates the size, in meters, of the floor plane to be created.</span></span> <span data-ttu-id="b6f4d-121">La scala predefinita è un quadrato di 3 metri x 3 metri.</span><span class="sxs-lookup"><span data-stu-id="b6f4d-121">The default scale is a 3 meter x 3 meter square.</span></span>

<span data-ttu-id="b6f4d-122">**Livello fisico**</span><span class="sxs-lookup"><span data-stu-id="b6f4d-122">**Physics Layer**</span></span>

<span data-ttu-id="b6f4d-123">Livello su cui deve essere impostato il piano terra.</span><span class="sxs-lookup"><span data-stu-id="b6f4d-123">The layer on which the floor plane should be set.</span></span> <span data-ttu-id="b6f4d-124">Il valore predefinito è *Livello* predefinito.</span><span class="sxs-lookup"><span data-stu-id="b6f4d-124">The default value is the *Default* layer.</span></span>

## <a name="play-area-settings"></a><span data-ttu-id="b6f4d-125">Impostazioni dell'area di riproduzione</span><span class="sxs-lookup"><span data-stu-id="b6f4d-125">Play area settings</span></span>

![Impostazioni dell'area di riproduzione per la visualizzazione dei limiti](../images/boundary/BoundaryVisualizationPlayAreaSettings.png)

<span data-ttu-id="b6f4d-127">**Mostra**</span><span class="sxs-lookup"><span data-stu-id="b6f4d-127">**Show**</span></span>

<span data-ttu-id="b6f4d-128">Indica se un rettangolo dell'area di riproduzione viene creato e aggiunto alla scena.</span><span class="sxs-lookup"><span data-stu-id="b6f4d-128">Indicates whether or not a play area rectangle is be created and added to the scene.</span></span> <span data-ttu-id="b6f4d-129">Il valore predefinito è true.</span><span class="sxs-lookup"><span data-stu-id="b6f4d-129">The default value is true.</span></span>

<span data-ttu-id="b6f4d-130">**Materiale**</span><span class="sxs-lookup"><span data-stu-id="b6f4d-130">**Material**</span></span>

<span data-ttu-id="b6f4d-131">Indica il materiale da usare durante la creazione dell'oggetto area di riproduzione.</span><span class="sxs-lookup"><span data-stu-id="b6f4d-131">Indicates the material that should be used when creating the play area object.</span></span>

<span data-ttu-id="b6f4d-132">**Livello fisico**</span><span class="sxs-lookup"><span data-stu-id="b6f4d-132">**Physics Layer**</span></span>

<span data-ttu-id="b6f4d-133">Livello su cui deve essere impostata l'area di riproduzione.</span><span class="sxs-lookup"><span data-stu-id="b6f4d-133">The layer on which the play area should be set.</span></span> <span data-ttu-id="b6f4d-134">Il valore predefinito è *Ignora raycast.*</span><span class="sxs-lookup"><span data-stu-id="b6f4d-134">The default value is the *Ignore Raycast* layer.</span></span>

## <a name="tracked-area-settings"></a><span data-ttu-id="b6f4d-135">Impostazioni dell'area rilevata</span><span class="sxs-lookup"><span data-stu-id="b6f4d-135">Tracked area settings</span></span>

![Impostazioni dell'area rilevata per la visualizzazione dei limiti](../images/boundary/BoundaryVisualizationTrackedAreaSettings.png)

<span data-ttu-id="b6f4d-137">**Mostra**</span><span class="sxs-lookup"><span data-stu-id="b6f4d-137">**Show**</span></span>

<span data-ttu-id="b6f4d-138">Indica se il contorno dell'area tracciata deve essere creato e aggiunto alla scena.</span><span class="sxs-lookup"><span data-stu-id="b6f4d-138">Indicates whether or not the outline of the tracked area is be created and added to the scene.</span></span> <span data-ttu-id="b6f4d-139">Il valore predefinito è true.</span><span class="sxs-lookup"><span data-stu-id="b6f4d-139">The default value is true.</span></span>

<span data-ttu-id="b6f4d-140">**Materiale**</span><span class="sxs-lookup"><span data-stu-id="b6f4d-140">**Material**</span></span>

<span data-ttu-id="b6f4d-141">Indica il materiale da usare durante la creazione del contorno dell'area tracciata.</span><span class="sxs-lookup"><span data-stu-id="b6f4d-141">Indicates the material that should be used when creating the tracked area outline.</span></span>

<span data-ttu-id="b6f4d-142">**Livello fisico**</span><span class="sxs-lookup"><span data-stu-id="b6f4d-142">**Physics Layer**</span></span>

<span data-ttu-id="b6f4d-143">Livello su cui deve essere impostata l'area rilevata.</span><span class="sxs-lookup"><span data-stu-id="b6f4d-143">The layer on which the tracked area should be sets.</span></span> <span data-ttu-id="b6f4d-144">Il valore predefinito è *Ignora raycast.*</span><span class="sxs-lookup"><span data-stu-id="b6f4d-144">The default value is the *Ignore Raycast* layer.</span></span>

## <a name="boundary-wall-settings"></a><span data-ttu-id="b6f4d-145">Impostazioni della barriera limite</span><span class="sxs-lookup"><span data-stu-id="b6f4d-145">Boundary wall settings</span></span>

![Boundary Visualization Boundary Wall Settings](../images/boundary/BoundaryVisualizationWallSettings.png)

<span data-ttu-id="b6f4d-147">**Mostra**</span><span class="sxs-lookup"><span data-stu-id="b6f4d-147">**Show**</span></span>

<span data-ttu-id="b6f4d-148">Indica se i piani delle pareti limite devono essere creati e aggiunti alla scena.</span><span class="sxs-lookup"><span data-stu-id="b6f4d-148">Indicates whether or not boundary wall planes are to be created and added to the scene.</span></span> <span data-ttu-id="b6f4d-149">Il valore predefinito è false.</span><span class="sxs-lookup"><span data-stu-id="b6f4d-149">The default value is false.</span></span>

<span data-ttu-id="b6f4d-150">**Materiale**</span><span class="sxs-lookup"><span data-stu-id="b6f4d-150">**Material**</span></span>

<span data-ttu-id="b6f4d-151">Indica il materiale da usare durante la creazione dei piani delle pareti limite.</span><span class="sxs-lookup"><span data-stu-id="b6f4d-151">Indicates the material that should be used when creating the boundary wall planes.</span></span>

<span data-ttu-id="b6f4d-152">**Livello fisico**</span><span class="sxs-lookup"><span data-stu-id="b6f4d-152">**Physics Layer**</span></span>

<span data-ttu-id="b6f4d-153">Livello su cui devono essere impostate le pareti limite.</span><span class="sxs-lookup"><span data-stu-id="b6f4d-153">The layer on which the boundary walls should be set.</span></span> <span data-ttu-id="b6f4d-154">Il valore predefinito è *Ignora raycast.*</span><span class="sxs-lookup"><span data-stu-id="b6f4d-154">The default value is the *Ignore Raycast* layer.</span></span>

> [!NOTE]
> <span data-ttu-id="b6f4d-155">L'impostazione del componente della parete limite su un livello fisico diverso da *Ignora Raycast* può impedire agli utenti di interagire con gli oggetti all'interno della scena.</span><span class="sxs-lookup"><span data-stu-id="b6f4d-155">Setting the boundary wall component to a physics layer other than *Ignore Raycast* may prevent users from interacting with objects within the scene.</span></span>

## <a name="boundary-ceiling-settings"></a><span data-ttu-id="b6f4d-156">Impostazioni del limite massimo</span><span class="sxs-lookup"><span data-stu-id="b6f4d-156">Boundary ceiling settings</span></span>

![Impostazioni limite limite visualizzazione limiti](../images/boundary/BoundaryVisualizationCeilingSettings.png)

<span data-ttu-id="b6f4d-158">**Mostra**</span><span class="sxs-lookup"><span data-stu-id="b6f4d-158">**Show**</span></span>

<span data-ttu-id="b6f4d-159">Indica se un piano limite deve essere creato e aggiunto alla scena.</span><span class="sxs-lookup"><span data-stu-id="b6f4d-159">Indicates whether or not a boundary ceiling plane is to be created and added to the scene.</span></span> <span data-ttu-id="b6f4d-160">Il valore predefinito è false.</span><span class="sxs-lookup"><span data-stu-id="b6f4d-160">The default value is false.</span></span>

<span data-ttu-id="b6f4d-161">**Materiale**</span><span class="sxs-lookup"><span data-stu-id="b6f4d-161">**Material**</span></span>

<span data-ttu-id="b6f4d-162">Indica il materiale che deve essere usato durante la creazione del piano del controsoffitto limite.</span><span class="sxs-lookup"><span data-stu-id="b6f4d-162">Indicates the material that should be used when creating the boundary ceiling plane.</span></span>

<span data-ttu-id="b6f4d-163">**Livello fisico**</span><span class="sxs-lookup"><span data-stu-id="b6f4d-163">**Physics Layer**</span></span>

<span data-ttu-id="b6f4d-164">Livello su cui devono essere impostati i limiti.</span><span class="sxs-lookup"><span data-stu-id="b6f4d-164">The layer on which the boundary walls should be set.</span></span> <span data-ttu-id="b6f4d-165">Il valore predefinito è *Il livello Ignora Raycast.*</span><span class="sxs-lookup"><span data-stu-id="b6f4d-165">The default value is the *Ignore Raycast* layer.</span></span>

> [!NOTE]
> <span data-ttu-id="b6f4d-166">L'impostazione del componente limite massimo su un livello fisico diverso da *Ignora Raycast* può impedire agli utenti di interagire con gli oggetti all'interno della scena.</span><span class="sxs-lookup"><span data-stu-id="b6f4d-166">Setting the boundary ceiling component to a physics layer other than *Ignore Raycast* may prevent users from interacting with objects within the scene.</span></span>

## <a name="see-also"></a><span data-ttu-id="b6f4d-167">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="b6f4d-167">See also</span></span>

- [<span data-ttu-id="b6f4d-168">Documentazione dell'API Boundary</span><span class="sxs-lookup"><span data-stu-id="b6f4d-168">Boundary API documentation</span></span>](xref:Microsoft.MixedReality.Toolkit.Boundary)
- [<span data-ttu-id="b6f4d-169">Sistema di limiti</span><span class="sxs-lookup"><span data-stu-id="b6f4d-169">Boundary System</span></span>](boundary-system-getting-started.md)

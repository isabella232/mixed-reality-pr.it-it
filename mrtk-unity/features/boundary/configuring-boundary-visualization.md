---
title: Configurazione della visualizzazione dei limiti
description: Dettagli per configurare il sistema di limiti in MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, sistema di limiti,
ms.openlocfilehash: 0f1a9edd9f9a31e7ba20f630406b299909a4864c
ms.sourcegitcommit: 8b4c2b1aac83bc8adf46acfd92b564f899ef7735
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/30/2021
ms.locfileid: "113121249"
---
# <a name="configuring-the-boundary-visualization"></a><span data-ttu-id="61a8e-104">Configurazione della visualizzazione dei limiti</span><span class="sxs-lookup"><span data-stu-id="61a8e-104">Configuring the boundary visualization</span></span>

<span data-ttu-id="61a8e-105">Il *profilo di visualizzazione dei* limiti offre opzioni per la configurazione dell'aspetto visivo e di altri parametri correlati per il sistema di limiti.</span><span class="sxs-lookup"><span data-stu-id="61a8e-105">The *Boundary Visualization Profile* provides options for configuring the visual aesthetics and other related parameters for the Boundary system.</span></span> <span data-ttu-id="61a8e-106">Le visualizzazioni dei limiti vengono collegate all'oggetto Playspace di realtà mista nella scena e teletrasportate con l'utente.</span><span class="sxs-lookup"><span data-stu-id="61a8e-106">Boundary visualizations are attached to the Mixed Reality Playspace object in the scene and teleport with the user.</span></span>

## <a name="general-settings"></a><span data-ttu-id="61a8e-107">Impostazioni generali</span><span class="sxs-lookup"><span data-stu-id="61a8e-107">General settings</span></span>

![Impostazioni generali di visualizzazione dei limiti](../images/boundary/BoundaryVisualizationGeneralSettings.png)

### <a name="boundary-height"></a><span data-ttu-id="61a8e-109">Altezza limite</span><span class="sxs-lookup"><span data-stu-id="61a8e-109">Boundary height</span></span>

<span data-ttu-id="61a8e-110">L'altezza limite indica la distanza sopra il piano del piano in corrispondenza della quale deve essere eseguito il rendering del limite massimo.</span><span class="sxs-lookup"><span data-stu-id="61a8e-110">The boundary height indicates the distance above the floor plane at which the boundary ceiling should be rendered.</span></span> <span data-ttu-id="61a8e-111">Il valore predefinito è 3 metri.</span><span class="sxs-lookup"><span data-stu-id="61a8e-111">The default value is 3 meters.</span></span>

## <a name="floor-settings"></a><span data-ttu-id="61a8e-112">Impostazioni del piano</span><span class="sxs-lookup"><span data-stu-id="61a8e-112">Floor settings</span></span>

![Impostazioni del piano per la visualizzazione dei limiti](../images/boundary/BoundaryVisualizationFloorSettings.png)

<span data-ttu-id="61a8e-114">**Mostra**</span><span class="sxs-lookup"><span data-stu-id="61a8e-114">**Show**</span></span>

<span data-ttu-id="61a8e-115">Indica se un piano piano deve essere creato e aggiunto alla scena.</span><span class="sxs-lookup"><span data-stu-id="61a8e-115">Indicates whether or not a floor plane is to be created and added to the scene.</span></span> <span data-ttu-id="61a8e-116">Il valore predefinito è true.</span><span class="sxs-lookup"><span data-stu-id="61a8e-116">The default value is true.</span></span>

<span data-ttu-id="61a8e-117">**Materiale**</span><span class="sxs-lookup"><span data-stu-id="61a8e-117">**Material**</span></span>

<span data-ttu-id="61a8e-118">Indica il materiale da usare durante la creazione del piano piano.</span><span class="sxs-lookup"><span data-stu-id="61a8e-118">Indicates the material that should be used when creating the floor plane.</span></span>

<span data-ttu-id="61a8e-119">**Scalabilità**</span><span class="sxs-lookup"><span data-stu-id="61a8e-119">**Scale**</span></span>

<span data-ttu-id="61a8e-120">Indica le dimensioni, in metri, del piano piano da creare.</span><span class="sxs-lookup"><span data-stu-id="61a8e-120">Indicates the size, in meters, of the floor plane to be created.</span></span> <span data-ttu-id="61a8e-121">La scala predefinita è 3 metri x 3 metri quadrati.</span><span class="sxs-lookup"><span data-stu-id="61a8e-121">The default scale is a 3 meter x 3 meter square.</span></span>

<span data-ttu-id="61a8e-122">**Livello fisico**</span><span class="sxs-lookup"><span data-stu-id="61a8e-122">**Physics Layer**</span></span>

<span data-ttu-id="61a8e-123">Livello su cui deve essere impostato il piano piano.</span><span class="sxs-lookup"><span data-stu-id="61a8e-123">The layer on which the floor plane should be set.</span></span> <span data-ttu-id="61a8e-124">Il valore predefinito è *Il livello* predefinito.</span><span class="sxs-lookup"><span data-stu-id="61a8e-124">The default value is the *Default* layer.</span></span>

## <a name="play-area-settings"></a><span data-ttu-id="61a8e-125">Impostazioni dell'area di riproduzione</span><span class="sxs-lookup"><span data-stu-id="61a8e-125">Play area settings</span></span>

![Impostazioni dell'area di riproduzione per la visualizzazione dei limiti](../images/boundary/BoundaryVisualizationPlayAreaSettings.png)

<span data-ttu-id="61a8e-127">**Mostra**</span><span class="sxs-lookup"><span data-stu-id="61a8e-127">**Show**</span></span>

<span data-ttu-id="61a8e-128">Indica se un rettangolo dell'area di riproduzione viene creato e aggiunto alla scena.</span><span class="sxs-lookup"><span data-stu-id="61a8e-128">Indicates whether or not a play area rectangle is be created and added to the scene.</span></span> <span data-ttu-id="61a8e-129">Il valore predefinito è true.</span><span class="sxs-lookup"><span data-stu-id="61a8e-129">The default value is true.</span></span>

<span data-ttu-id="61a8e-130">**Materiale**</span><span class="sxs-lookup"><span data-stu-id="61a8e-130">**Material**</span></span>

<span data-ttu-id="61a8e-131">Indica il materiale da usare durante la creazione dell'oggetto area di riproduzione.</span><span class="sxs-lookup"><span data-stu-id="61a8e-131">Indicates the material that should be used when creating the play area object.</span></span>

<span data-ttu-id="61a8e-132">**Livello fisico**</span><span class="sxs-lookup"><span data-stu-id="61a8e-132">**Physics Layer**</span></span>

<span data-ttu-id="61a8e-133">Livello su cui deve essere impostata l'area di riproduzione.</span><span class="sxs-lookup"><span data-stu-id="61a8e-133">The layer on which the play area should be set.</span></span> <span data-ttu-id="61a8e-134">Il valore predefinito è *Ignora raycast.*</span><span class="sxs-lookup"><span data-stu-id="61a8e-134">The default value is the *Ignore Raycast* layer.</span></span>

## <a name="tracked-area-settings"></a><span data-ttu-id="61a8e-135">Impostazioni dell'area rilevata</span><span class="sxs-lookup"><span data-stu-id="61a8e-135">Tracked area settings</span></span>

![Impostazioni dell'area rilevata per la visualizzazione dei limiti](../images/boundary/BoundaryVisualizationTrackedAreaSettings.png)

<span data-ttu-id="61a8e-137">**Mostra**</span><span class="sxs-lookup"><span data-stu-id="61a8e-137">**Show**</span></span>

<span data-ttu-id="61a8e-138">Indica se la struttura dell'area tracciata deve essere creata e aggiunta alla scena.</span><span class="sxs-lookup"><span data-stu-id="61a8e-138">Indicates whether or not the outline of the tracked area is be created and added to the scene.</span></span> <span data-ttu-id="61a8e-139">Il valore predefinito è true.</span><span class="sxs-lookup"><span data-stu-id="61a8e-139">The default value is true.</span></span>

<span data-ttu-id="61a8e-140">**Materiale**</span><span class="sxs-lookup"><span data-stu-id="61a8e-140">**Material**</span></span>

<span data-ttu-id="61a8e-141">Indica il materiale da usare durante la creazione del contorno dell'area tracciata.</span><span class="sxs-lookup"><span data-stu-id="61a8e-141">Indicates the material that should be used when creating the tracked area outline.</span></span>

<span data-ttu-id="61a8e-142">**Livello fisico**</span><span class="sxs-lookup"><span data-stu-id="61a8e-142">**Physics Layer**</span></span>

<span data-ttu-id="61a8e-143">Livello su cui deve essere impostata l'area rilevata.</span><span class="sxs-lookup"><span data-stu-id="61a8e-143">The layer on which the tracked area should be sets.</span></span> <span data-ttu-id="61a8e-144">Il valore predefinito è *Ignora raycast.*</span><span class="sxs-lookup"><span data-stu-id="61a8e-144">The default value is the *Ignore Raycast* layer.</span></span>

## <a name="boundary-wall-settings"></a><span data-ttu-id="61a8e-145">Impostazioni della barriera limite</span><span class="sxs-lookup"><span data-stu-id="61a8e-145">Boundary wall settings</span></span>

![Boundary Visualization Boundary Wall Settings](../images/boundary/BoundaryVisualizationWallSettings.png)

<span data-ttu-id="61a8e-147">**Mostra**</span><span class="sxs-lookup"><span data-stu-id="61a8e-147">**Show**</span></span>

<span data-ttu-id="61a8e-148">Indica se i piani delle pareti limite devono essere creati e aggiunti alla scena.</span><span class="sxs-lookup"><span data-stu-id="61a8e-148">Indicates whether or not boundary wall planes are to be created and added to the scene.</span></span> <span data-ttu-id="61a8e-149">Il valore predefinito è false.</span><span class="sxs-lookup"><span data-stu-id="61a8e-149">The default value is false.</span></span>

<span data-ttu-id="61a8e-150">**Materiale**</span><span class="sxs-lookup"><span data-stu-id="61a8e-150">**Material**</span></span>

<span data-ttu-id="61a8e-151">Indica il materiale da usare durante la creazione dei piani delle pareti limite.</span><span class="sxs-lookup"><span data-stu-id="61a8e-151">Indicates the material that should be used when creating the boundary wall planes.</span></span>

<span data-ttu-id="61a8e-152">**Livello fisico**</span><span class="sxs-lookup"><span data-stu-id="61a8e-152">**Physics Layer**</span></span>

<span data-ttu-id="61a8e-153">Livello su cui devono essere impostate le pareti limite.</span><span class="sxs-lookup"><span data-stu-id="61a8e-153">The layer on which the boundary walls should be set.</span></span> <span data-ttu-id="61a8e-154">Il valore predefinito è *Ignora raycast.*</span><span class="sxs-lookup"><span data-stu-id="61a8e-154">The default value is the *Ignore Raycast* layer.</span></span>

> [!NOTE]
> <span data-ttu-id="61a8e-155">L'impostazione del componente della barriera limite su un livello fisico diverso da *Ignora Raycast* può impedire agli utenti di interagire con gli oggetti all'interno della scena.</span><span class="sxs-lookup"><span data-stu-id="61a8e-155">Setting the boundary wall component to a physics layer other than *Ignore Raycast* may prevent users from interacting with objects within the scene.</span></span>

## <a name="boundary-ceiling-settings"></a><span data-ttu-id="61a8e-156">Impostazioni limite massimo</span><span class="sxs-lookup"><span data-stu-id="61a8e-156">Boundary ceiling settings</span></span>

![Boundary Visualization Boundary Ceiling Settings](../images/boundary/BoundaryVisualizationCeilingSettings.png)

<span data-ttu-id="61a8e-158">**Mostra**</span><span class="sxs-lookup"><span data-stu-id="61a8e-158">**Show**</span></span>

<span data-ttu-id="61a8e-159">Indica se un piano limite del limite deve essere creato e aggiunto alla scena.</span><span class="sxs-lookup"><span data-stu-id="61a8e-159">Indicates whether or not a boundary ceiling plane is to be created and added to the scene.</span></span> <span data-ttu-id="61a8e-160">Il valore predefinito è false.</span><span class="sxs-lookup"><span data-stu-id="61a8e-160">The default value is false.</span></span>

<span data-ttu-id="61a8e-161">**Materiale**</span><span class="sxs-lookup"><span data-stu-id="61a8e-161">**Material**</span></span>

<span data-ttu-id="61a8e-162">Indica il materiale da usare durante la creazione del piano limite del limite.</span><span class="sxs-lookup"><span data-stu-id="61a8e-162">Indicates the material that should be used when creating the boundary ceiling plane.</span></span>

<span data-ttu-id="61a8e-163">**Livello fisico**</span><span class="sxs-lookup"><span data-stu-id="61a8e-163">**Physics Layer**</span></span>

<span data-ttu-id="61a8e-164">Livello su cui devono essere impostate le pareti limite.</span><span class="sxs-lookup"><span data-stu-id="61a8e-164">The layer on which the boundary walls should be set.</span></span> <span data-ttu-id="61a8e-165">Il valore predefinito è *Ignora raycast.*</span><span class="sxs-lookup"><span data-stu-id="61a8e-165">The default value is the *Ignore Raycast* layer.</span></span>

> [!NOTE]
> <span data-ttu-id="61a8e-166">L'impostazione del componente limite massimo su un livello fisico diverso da *Ignora Raycast* può impedire agli utenti di interagire con gli oggetti all'interno della scena.</span><span class="sxs-lookup"><span data-stu-id="61a8e-166">Setting the boundary ceiling component to a physics layer other than *Ignore Raycast* may prevent users from interacting with objects within the scene.</span></span>

## <a name="see-also"></a><span data-ttu-id="61a8e-167">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="61a8e-167">See also</span></span>

- [<span data-ttu-id="61a8e-168">Documentazione dell'API Limite</span><span class="sxs-lookup"><span data-stu-id="61a8e-168">Boundary API documentation</span></span>](xref:Microsoft.MixedReality.Toolkit.Boundary)
- [<span data-ttu-id="61a8e-169">Sistema di limiti</span><span class="sxs-lookup"><span data-stu-id="61a8e-169">Boundary System</span></span>](boundary-system-getting-started.md)

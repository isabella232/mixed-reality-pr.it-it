---
title: ConfiguringBoundaryVisualization
description: Dettagli per configurare il sistema di limiti in MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, sistema di limiti,
ms.openlocfilehash: e118359bf5faf4f198d1ed2a59329e585c547fad
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/03/2021
ms.locfileid: "101782149"
---
# <a name="configuring-the-boundary-visualization"></a><span data-ttu-id="67d8a-104">Configurazione della visualizzazione dei limiti</span><span class="sxs-lookup"><span data-stu-id="67d8a-104">Configuring the boundary visualization</span></span>

<span data-ttu-id="67d8a-105">Il *profilo di visualizzazione dei limiti* fornisce opzioni per la configurazione dell'estetica visiva e di altri parametri correlati per il sistema di limiti.</span><span class="sxs-lookup"><span data-stu-id="67d8a-105">The *Boundary Visualization Profile* provides options for configuring the visual aesthetics and other related parameters for the Boundary system.</span></span> <span data-ttu-id="67d8a-106">Le visualizzazioni dei limiti sono collegate all'oggetto playspace della realtà mista nella scena e si teletrasportano con l'utente.</span><span class="sxs-lookup"><span data-stu-id="67d8a-106">Boundary visualizations are attached to the Mixed Reality Playspace object in the scene and teleport with the user.</span></span>

## <a name="general-settings"></a><span data-ttu-id="67d8a-107">Impostazioni generali</span><span class="sxs-lookup"><span data-stu-id="67d8a-107">General settings</span></span>

![Impostazioni generali visualizzazione limite](../images/boundary/BoundaryVisualizationGeneralSettings.png)

### <a name="boundary-height"></a><span data-ttu-id="67d8a-109">Altezza limite</span><span class="sxs-lookup"><span data-stu-id="67d8a-109">Boundary height</span></span>

<span data-ttu-id="67d8a-110">L'altezza del limite indica la distanza al di sopra del piano di pavimento in corrispondenza della quale deve essere eseguito il rendering del limite massimo.</span><span class="sxs-lookup"><span data-stu-id="67d8a-110">The boundary height indicates the distance above the floor plane at which the boundary ceiling should be rendered.</span></span> <span data-ttu-id="67d8a-111">Il valore predefinito è 3 metri.</span><span class="sxs-lookup"><span data-stu-id="67d8a-111">The default value is 3 meters.</span></span>

## <a name="floor-settings"></a><span data-ttu-id="67d8a-112">Impostazioni del piano</span><span class="sxs-lookup"><span data-stu-id="67d8a-112">Floor settings</span></span>

![Impostazioni del piano visualizzazione limite](../images/boundary/BoundaryVisualizationFloorSettings.png)

<span data-ttu-id="67d8a-114">**Mostra**</span><span class="sxs-lookup"><span data-stu-id="67d8a-114">**Show**</span></span>

<span data-ttu-id="67d8a-115">Indica se un piano di piano deve essere creato e aggiunto alla scena.</span><span class="sxs-lookup"><span data-stu-id="67d8a-115">Indicates whether or not a floor plane is to be created and added to the scene.</span></span> <span data-ttu-id="67d8a-116">Il valore predefinito è true.</span><span class="sxs-lookup"><span data-stu-id="67d8a-116">The default value is true.</span></span>

<span data-ttu-id="67d8a-117">**Materiale**</span><span class="sxs-lookup"><span data-stu-id="67d8a-117">**Material**</span></span>

<span data-ttu-id="67d8a-118">Indica il materiale da utilizzare durante la creazione del piano di piano.</span><span class="sxs-lookup"><span data-stu-id="67d8a-118">Indicates the material that should be used when creating the floor plane.</span></span>

<span data-ttu-id="67d8a-119">**Ridimensiona**</span><span class="sxs-lookup"><span data-stu-id="67d8a-119">**Scale**</span></span>

<span data-ttu-id="67d8a-120">Indica la dimensione, in metri, del piano del piano da creare.</span><span class="sxs-lookup"><span data-stu-id="67d8a-120">Indicates the size, in meters, of the floor plane to be created.</span></span> <span data-ttu-id="67d8a-121">La scala predefinita è un quadrato da 3 metri x 3 metri.</span><span class="sxs-lookup"><span data-stu-id="67d8a-121">The default scale is a 3 meter x 3 meter square.</span></span>

<span data-ttu-id="67d8a-122">**Livello di fisica**</span><span class="sxs-lookup"><span data-stu-id="67d8a-122">**Physics Layer**</span></span>

<span data-ttu-id="67d8a-123">Livello sul quale deve essere impostato il piano del piano.</span><span class="sxs-lookup"><span data-stu-id="67d8a-123">The layer on which the floor plane should be set.</span></span> <span data-ttu-id="67d8a-124">Il valore predefinito è il livello *predefinito* .</span><span class="sxs-lookup"><span data-stu-id="67d8a-124">The default value is the *Default* layer.</span></span>

## <a name="play-area-settings"></a><span data-ttu-id="67d8a-125">Impostazioni area di riproduzione</span><span class="sxs-lookup"><span data-stu-id="67d8a-125">Play area settings</span></span>

![Impostazioni dell'area di riproduzione della visualizzazione limite](../images/boundary/BoundaryVisualizationPlayAreaSettings.png)

<span data-ttu-id="67d8a-127">**Mostra**</span><span class="sxs-lookup"><span data-stu-id="67d8a-127">**Show**</span></span>

<span data-ttu-id="67d8a-128">Indica se un rettangolo area di riproduzione viene creato e aggiunto alla scena.</span><span class="sxs-lookup"><span data-stu-id="67d8a-128">Indicates whether or not a play area rectangle is be created and added to the scene.</span></span> <span data-ttu-id="67d8a-129">Il valore predefinito è true.</span><span class="sxs-lookup"><span data-stu-id="67d8a-129">The default value is true.</span></span>

<span data-ttu-id="67d8a-130">**Materiale**</span><span class="sxs-lookup"><span data-stu-id="67d8a-130">**Material**</span></span>

<span data-ttu-id="67d8a-131">Indica il materiale da utilizzare quando si crea l'oggetto area di riproduzione.</span><span class="sxs-lookup"><span data-stu-id="67d8a-131">Indicates the material that should be used when creating the play area object.</span></span>

<span data-ttu-id="67d8a-132">**Livello di fisica**</span><span class="sxs-lookup"><span data-stu-id="67d8a-132">**Physics Layer**</span></span>

<span data-ttu-id="67d8a-133">Il livello in cui deve essere impostata l'area di riproduzione.</span><span class="sxs-lookup"><span data-stu-id="67d8a-133">The layer on which the play area should be set.</span></span> <span data-ttu-id="67d8a-134">Il valore predefinito è il livello *Ignora Raycast* .</span><span class="sxs-lookup"><span data-stu-id="67d8a-134">The default value is the *Ignore Raycast* layer.</span></span>

## <a name="tracked-area-settings"></a><span data-ttu-id="67d8a-135">Impostazioni area rilevata</span><span class="sxs-lookup"><span data-stu-id="67d8a-135">Tracked area settings</span></span>

![Impostazioni area rilevate visualizzazione limite](../images/boundary/BoundaryVisualizationTrackedAreaSettings.png)

<span data-ttu-id="67d8a-137">**Mostra**</span><span class="sxs-lookup"><span data-stu-id="67d8a-137">**Show**</span></span>

<span data-ttu-id="67d8a-138">Indica se il contorno dell'area rilevata viene creato e aggiunto alla scena.</span><span class="sxs-lookup"><span data-stu-id="67d8a-138">Indicates whether or not the outline of the tracked area is be created and added to the scene.</span></span> <span data-ttu-id="67d8a-139">Il valore predefinito è true.</span><span class="sxs-lookup"><span data-stu-id="67d8a-139">The default value is true.</span></span>

<span data-ttu-id="67d8a-140">**Materiale**</span><span class="sxs-lookup"><span data-stu-id="67d8a-140">**Material**</span></span>

<span data-ttu-id="67d8a-141">Indica il materiale da usare quando si crea il contorno dell'area rilevata.</span><span class="sxs-lookup"><span data-stu-id="67d8a-141">Indicates the material that should be used when creating the tracked area outline.</span></span>

<span data-ttu-id="67d8a-142">**Livello di fisica**</span><span class="sxs-lookup"><span data-stu-id="67d8a-142">**Physics Layer**</span></span>

<span data-ttu-id="67d8a-143">Il livello in cui deve essere impostata l'area rilevata.</span><span class="sxs-lookup"><span data-stu-id="67d8a-143">The layer on which the tracked area should be sets.</span></span> <span data-ttu-id="67d8a-144">Il valore predefinito è il livello *Ignora Raycast* .</span><span class="sxs-lookup"><span data-stu-id="67d8a-144">The default value is the *Ignore Raycast* layer.</span></span>

## <a name="boundary-wall-settings"></a><span data-ttu-id="67d8a-145">Impostazioni muro limite</span><span class="sxs-lookup"><span data-stu-id="67d8a-145">Boundary wall settings</span></span>

![Impostazioni parete limite visualizzazione limite](../images/boundary/BoundaryVisualizationWallSettings.png)

<span data-ttu-id="67d8a-147">**Mostra**</span><span class="sxs-lookup"><span data-stu-id="67d8a-147">**Show**</span></span>

<span data-ttu-id="67d8a-148">Indica se devono essere creati e aggiunti alla scena i piani della parete limite.</span><span class="sxs-lookup"><span data-stu-id="67d8a-148">Indicates whether or not boundary wall planes are to be created and added to the scene.</span></span> <span data-ttu-id="67d8a-149">Il valore predefinito è false.</span><span class="sxs-lookup"><span data-stu-id="67d8a-149">The default value is false.</span></span>

<span data-ttu-id="67d8a-150">**Materiale**</span><span class="sxs-lookup"><span data-stu-id="67d8a-150">**Material**</span></span>

<span data-ttu-id="67d8a-151">Indica il materiale da usare quando si creano i piani della barriera limite.</span><span class="sxs-lookup"><span data-stu-id="67d8a-151">Indicates the material that should be used when creating the boundary wall planes.</span></span>

<span data-ttu-id="67d8a-152">**Livello di fisica**</span><span class="sxs-lookup"><span data-stu-id="67d8a-152">**Physics Layer**</span></span>

<span data-ttu-id="67d8a-153">Livello su cui devono essere impostati i muri limite.</span><span class="sxs-lookup"><span data-stu-id="67d8a-153">The layer on which the boundary walls should be set.</span></span> <span data-ttu-id="67d8a-154">Il valore predefinito è il livello *Ignora Raycast* .</span><span class="sxs-lookup"><span data-stu-id="67d8a-154">The default value is the *Ignore Raycast* layer.</span></span>

> [!NOTE]
> <span data-ttu-id="67d8a-155">L'impostazione del componente della parete limite su un livello di fisica diverso da *Ignore Raycast* può impedire agli utenti di interagire con gli oggetti all'interno della scena.</span><span class="sxs-lookup"><span data-stu-id="67d8a-155">Setting the boundary wall component to a physics layer other than *Ignore Raycast* may prevent users from interacting with objects within the scene.</span></span>

## <a name="boundary-ceiling-settings"></a><span data-ttu-id="67d8a-156">Impostazioni Ceiling limite</span><span class="sxs-lookup"><span data-stu-id="67d8a-156">Boundary ceiling settings</span></span>

![Impostazioni limite massimo limite visualizzazione limite](../images/boundary/BoundaryVisualizationCeilingSettings.png)

<span data-ttu-id="67d8a-158">**Mostra**</span><span class="sxs-lookup"><span data-stu-id="67d8a-158">**Show**</span></span>

<span data-ttu-id="67d8a-159">Indica se è necessario creare un piano di limite massimo e aggiungerlo alla scena.</span><span class="sxs-lookup"><span data-stu-id="67d8a-159">Indicates whether or not a boundary ceiling plane is to be created and added to the scene.</span></span> <span data-ttu-id="67d8a-160">Il valore predefinito è false.</span><span class="sxs-lookup"><span data-stu-id="67d8a-160">The default value is false.</span></span>

<span data-ttu-id="67d8a-161">**Materiale**</span><span class="sxs-lookup"><span data-stu-id="67d8a-161">**Material**</span></span>

<span data-ttu-id="67d8a-162">Indica il materiale da usare quando si crea il piano limite massimo.</span><span class="sxs-lookup"><span data-stu-id="67d8a-162">Indicates the material that should be used when creating the boundary ceiling plane.</span></span>

<span data-ttu-id="67d8a-163">**Livello di fisica**</span><span class="sxs-lookup"><span data-stu-id="67d8a-163">**Physics Layer**</span></span>

<span data-ttu-id="67d8a-164">Livello su cui devono essere impostati i muri limite.</span><span class="sxs-lookup"><span data-stu-id="67d8a-164">The layer on which the boundary walls should be set.</span></span> <span data-ttu-id="67d8a-165">Il valore predefinito è il livello *Ignora Raycast* .</span><span class="sxs-lookup"><span data-stu-id="67d8a-165">The default value is the *Ignore Raycast* layer.</span></span>

> [!NOTE]
> <span data-ttu-id="67d8a-166">Impostando il componente Ceiling limite su un livello di fisica diverso da *Ignore Raycast* , è possibile impedire agli utenti di interagire con gli oggetti all'interno della scena.</span><span class="sxs-lookup"><span data-stu-id="67d8a-166">Setting the boundary ceiling component to a physics layer other than *Ignore Raycast* may prevent users from interacting with objects within the scene.</span></span>

## <a name="see-also"></a><span data-ttu-id="67d8a-167">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="67d8a-167">See also</span></span>

- [<span data-ttu-id="67d8a-168">Documentazione dell'API limite</span><span class="sxs-lookup"><span data-stu-id="67d8a-168">Boundary API documentation</span></span>](xref:Microsoft.MixedReality.Toolkit.Boundary)
- [<span data-ttu-id="67d8a-169">Sistema di limiti</span><span class="sxs-lookup"><span data-stu-id="67d8a-169">Boundary System</span></span>](boundary-system-getting-started.md)

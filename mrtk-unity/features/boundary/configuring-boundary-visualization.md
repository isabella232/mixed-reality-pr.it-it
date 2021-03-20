---
title: ConfiguringBoundaryVisualization
description: Dettagli per configurare il sistema di limiti in MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, sistema di limiti,
ms.openlocfilehash: 36e8ac69a76f3ec1483d8dd0404900972a8caee7
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2021
ms.locfileid: "104681934"
---
# <a name="configuring-the-boundary-visualization"></a><span data-ttu-id="98ec4-104">Configurazione della visualizzazione dei limiti</span><span class="sxs-lookup"><span data-stu-id="98ec4-104">Configuring the boundary visualization</span></span>

<span data-ttu-id="98ec4-105">Il *profilo di visualizzazione dei limiti* fornisce opzioni per la configurazione dell'estetica visiva e di altri parametri correlati per il sistema di limiti.</span><span class="sxs-lookup"><span data-stu-id="98ec4-105">The *Boundary Visualization Profile* provides options for configuring the visual aesthetics and other related parameters for the Boundary system.</span></span> <span data-ttu-id="98ec4-106">Le visualizzazioni dei limiti sono collegate all'oggetto playspace della realtà mista nella scena e si teletrasportano con l'utente.</span><span class="sxs-lookup"><span data-stu-id="98ec4-106">Boundary visualizations are attached to the Mixed Reality Playspace object in the scene and teleport with the user.</span></span>

## <a name="general-settings"></a><span data-ttu-id="98ec4-107">Impostazioni generali</span><span class="sxs-lookup"><span data-stu-id="98ec4-107">General settings</span></span>

![Impostazioni generali visualizzazione limite](../images/boundary/BoundaryVisualizationGeneralSettings.png)

### <a name="boundary-height"></a><span data-ttu-id="98ec4-109">Altezza limite</span><span class="sxs-lookup"><span data-stu-id="98ec4-109">Boundary height</span></span>

<span data-ttu-id="98ec4-110">L'altezza del limite indica la distanza al di sopra del piano di pavimento in corrispondenza della quale deve essere eseguito il rendering del limite massimo.</span><span class="sxs-lookup"><span data-stu-id="98ec4-110">The boundary height indicates the distance above the floor plane at which the boundary ceiling should be rendered.</span></span> <span data-ttu-id="98ec4-111">Il valore predefinito è 3 metri.</span><span class="sxs-lookup"><span data-stu-id="98ec4-111">The default value is 3 meters.</span></span>

## <a name="floor-settings"></a><span data-ttu-id="98ec4-112">Impostazioni del piano</span><span class="sxs-lookup"><span data-stu-id="98ec4-112">Floor settings</span></span>

![Impostazioni del piano visualizzazione limite](../images/boundary/BoundaryVisualizationFloorSettings.png)

<span data-ttu-id="98ec4-114">**Mostra**</span><span class="sxs-lookup"><span data-stu-id="98ec4-114">**Show**</span></span>

<span data-ttu-id="98ec4-115">Indica se un piano di piano deve essere creato e aggiunto alla scena.</span><span class="sxs-lookup"><span data-stu-id="98ec4-115">Indicates whether or not a floor plane is to be created and added to the scene.</span></span> <span data-ttu-id="98ec4-116">Il valore predefinito è true.</span><span class="sxs-lookup"><span data-stu-id="98ec4-116">The default value is true.</span></span>

<span data-ttu-id="98ec4-117">**Materiale**</span><span class="sxs-lookup"><span data-stu-id="98ec4-117">**Material**</span></span>

<span data-ttu-id="98ec4-118">Indica il materiale da utilizzare durante la creazione del piano di piano.</span><span class="sxs-lookup"><span data-stu-id="98ec4-118">Indicates the material that should be used when creating the floor plane.</span></span>

<span data-ttu-id="98ec4-119">**Ridimensiona**</span><span class="sxs-lookup"><span data-stu-id="98ec4-119">**Scale**</span></span>

<span data-ttu-id="98ec4-120">Indica la dimensione, in metri, del piano del piano da creare.</span><span class="sxs-lookup"><span data-stu-id="98ec4-120">Indicates the size, in meters, of the floor plane to be created.</span></span> <span data-ttu-id="98ec4-121">La scala predefinita è un quadrato da 3 metri x 3 metri.</span><span class="sxs-lookup"><span data-stu-id="98ec4-121">The default scale is a 3 meter x 3 meter square.</span></span>

<span data-ttu-id="98ec4-122">**Livello di fisica**</span><span class="sxs-lookup"><span data-stu-id="98ec4-122">**Physics Layer**</span></span>

<span data-ttu-id="98ec4-123">Livello sul quale deve essere impostato il piano del piano.</span><span class="sxs-lookup"><span data-stu-id="98ec4-123">The layer on which the floor plane should be set.</span></span> <span data-ttu-id="98ec4-124">Il valore predefinito è il livello *predefinito* .</span><span class="sxs-lookup"><span data-stu-id="98ec4-124">The default value is the *Default* layer.</span></span>

## <a name="play-area-settings"></a><span data-ttu-id="98ec4-125">Impostazioni area di riproduzione</span><span class="sxs-lookup"><span data-stu-id="98ec4-125">Play area settings</span></span>

![Impostazioni dell'area di riproduzione della visualizzazione limite](../images/boundary/BoundaryVisualizationPlayAreaSettings.png)

<span data-ttu-id="98ec4-127">**Mostra**</span><span class="sxs-lookup"><span data-stu-id="98ec4-127">**Show**</span></span>

<span data-ttu-id="98ec4-128">Indica se un rettangolo area di riproduzione viene creato e aggiunto alla scena.</span><span class="sxs-lookup"><span data-stu-id="98ec4-128">Indicates whether or not a play area rectangle is be created and added to the scene.</span></span> <span data-ttu-id="98ec4-129">Il valore predefinito è true.</span><span class="sxs-lookup"><span data-stu-id="98ec4-129">The default value is true.</span></span>

<span data-ttu-id="98ec4-130">**Materiale**</span><span class="sxs-lookup"><span data-stu-id="98ec4-130">**Material**</span></span>

<span data-ttu-id="98ec4-131">Indica il materiale da utilizzare quando si crea l'oggetto area di riproduzione.</span><span class="sxs-lookup"><span data-stu-id="98ec4-131">Indicates the material that should be used when creating the play area object.</span></span>

<span data-ttu-id="98ec4-132">**Livello di fisica**</span><span class="sxs-lookup"><span data-stu-id="98ec4-132">**Physics Layer**</span></span>

<span data-ttu-id="98ec4-133">Il livello in cui deve essere impostata l'area di riproduzione.</span><span class="sxs-lookup"><span data-stu-id="98ec4-133">The layer on which the play area should be set.</span></span> <span data-ttu-id="98ec4-134">Il valore predefinito è il livello *Ignora Raycast* .</span><span class="sxs-lookup"><span data-stu-id="98ec4-134">The default value is the *Ignore Raycast* layer.</span></span>

## <a name="tracked-area-settings"></a><span data-ttu-id="98ec4-135">Impostazioni area rilevata</span><span class="sxs-lookup"><span data-stu-id="98ec4-135">Tracked area settings</span></span>

![Impostazioni area rilevate visualizzazione limite](../images/boundary/BoundaryVisualizationTrackedAreaSettings.png)

<span data-ttu-id="98ec4-137">**Mostra**</span><span class="sxs-lookup"><span data-stu-id="98ec4-137">**Show**</span></span>

<span data-ttu-id="98ec4-138">Indica se il contorno dell'area rilevata viene creato e aggiunto alla scena.</span><span class="sxs-lookup"><span data-stu-id="98ec4-138">Indicates whether or not the outline of the tracked area is be created and added to the scene.</span></span> <span data-ttu-id="98ec4-139">Il valore predefinito è true.</span><span class="sxs-lookup"><span data-stu-id="98ec4-139">The default value is true.</span></span>

<span data-ttu-id="98ec4-140">**Materiale**</span><span class="sxs-lookup"><span data-stu-id="98ec4-140">**Material**</span></span>

<span data-ttu-id="98ec4-141">Indica il materiale da usare quando si crea il contorno dell'area rilevata.</span><span class="sxs-lookup"><span data-stu-id="98ec4-141">Indicates the material that should be used when creating the tracked area outline.</span></span>

<span data-ttu-id="98ec4-142">**Livello di fisica**</span><span class="sxs-lookup"><span data-stu-id="98ec4-142">**Physics Layer**</span></span>

<span data-ttu-id="98ec4-143">Il livello in cui deve essere impostata l'area rilevata.</span><span class="sxs-lookup"><span data-stu-id="98ec4-143">The layer on which the tracked area should be sets.</span></span> <span data-ttu-id="98ec4-144">Il valore predefinito è il livello *Ignora Raycast* .</span><span class="sxs-lookup"><span data-stu-id="98ec4-144">The default value is the *Ignore Raycast* layer.</span></span>

## <a name="boundary-wall-settings"></a><span data-ttu-id="98ec4-145">Impostazioni muro limite</span><span class="sxs-lookup"><span data-stu-id="98ec4-145">Boundary wall settings</span></span>

![Impostazioni parete limite visualizzazione limite](../images/boundary/BoundaryVisualizationWallSettings.png)

<span data-ttu-id="98ec4-147">**Mostra**</span><span class="sxs-lookup"><span data-stu-id="98ec4-147">**Show**</span></span>

<span data-ttu-id="98ec4-148">Indica se devono essere creati e aggiunti alla scena i piani della parete limite.</span><span class="sxs-lookup"><span data-stu-id="98ec4-148">Indicates whether or not boundary wall planes are to be created and added to the scene.</span></span> <span data-ttu-id="98ec4-149">Il valore predefinito è false.</span><span class="sxs-lookup"><span data-stu-id="98ec4-149">The default value is false.</span></span>

<span data-ttu-id="98ec4-150">**Materiale**</span><span class="sxs-lookup"><span data-stu-id="98ec4-150">**Material**</span></span>

<span data-ttu-id="98ec4-151">Indica il materiale da usare quando si creano i piani della barriera limite.</span><span class="sxs-lookup"><span data-stu-id="98ec4-151">Indicates the material that should be used when creating the boundary wall planes.</span></span>

<span data-ttu-id="98ec4-152">**Livello di fisica**</span><span class="sxs-lookup"><span data-stu-id="98ec4-152">**Physics Layer**</span></span>

<span data-ttu-id="98ec4-153">Livello su cui devono essere impostati i muri limite.</span><span class="sxs-lookup"><span data-stu-id="98ec4-153">The layer on which the boundary walls should be set.</span></span> <span data-ttu-id="98ec4-154">Il valore predefinito è il livello *Ignora Raycast* .</span><span class="sxs-lookup"><span data-stu-id="98ec4-154">The default value is the *Ignore Raycast* layer.</span></span>

> [!NOTE]
> <span data-ttu-id="98ec4-155">L'impostazione del componente della parete limite su un livello di fisica diverso da *Ignore Raycast* può impedire agli utenti di interagire con gli oggetti all'interno della scena.</span><span class="sxs-lookup"><span data-stu-id="98ec4-155">Setting the boundary wall component to a physics layer other than *Ignore Raycast* may prevent users from interacting with objects within the scene.</span></span>

## <a name="boundary-ceiling-settings"></a><span data-ttu-id="98ec4-156">Impostazioni Ceiling limite</span><span class="sxs-lookup"><span data-stu-id="98ec4-156">Boundary ceiling settings</span></span>

![Impostazioni limite massimo limite visualizzazione limite](../images/boundary/BoundaryVisualizationCeilingSettings.png)

<span data-ttu-id="98ec4-158">**Mostra**</span><span class="sxs-lookup"><span data-stu-id="98ec4-158">**Show**</span></span>

<span data-ttu-id="98ec4-159">Indica se è necessario creare un piano di limite massimo e aggiungerlo alla scena.</span><span class="sxs-lookup"><span data-stu-id="98ec4-159">Indicates whether or not a boundary ceiling plane is to be created and added to the scene.</span></span> <span data-ttu-id="98ec4-160">Il valore predefinito è false.</span><span class="sxs-lookup"><span data-stu-id="98ec4-160">The default value is false.</span></span>

<span data-ttu-id="98ec4-161">**Materiale**</span><span class="sxs-lookup"><span data-stu-id="98ec4-161">**Material**</span></span>

<span data-ttu-id="98ec4-162">Indica il materiale da usare quando si crea il piano limite massimo.</span><span class="sxs-lookup"><span data-stu-id="98ec4-162">Indicates the material that should be used when creating the boundary ceiling plane.</span></span>

<span data-ttu-id="98ec4-163">**Livello di fisica**</span><span class="sxs-lookup"><span data-stu-id="98ec4-163">**Physics Layer**</span></span>

<span data-ttu-id="98ec4-164">Livello su cui devono essere impostati i muri limite.</span><span class="sxs-lookup"><span data-stu-id="98ec4-164">The layer on which the boundary walls should be set.</span></span> <span data-ttu-id="98ec4-165">Il valore predefinito è il livello *Ignora Raycast* .</span><span class="sxs-lookup"><span data-stu-id="98ec4-165">The default value is the *Ignore Raycast* layer.</span></span>

> [!NOTE]
> <span data-ttu-id="98ec4-166">Impostando il componente Ceiling limite su un livello di fisica diverso da *Ignore Raycast* , è possibile impedire agli utenti di interagire con gli oggetti all'interno della scena.</span><span class="sxs-lookup"><span data-stu-id="98ec4-166">Setting the boundary ceiling component to a physics layer other than *Ignore Raycast* may prevent users from interacting with objects within the scene.</span></span>

## <a name="see-also"></a><span data-ttu-id="98ec4-167">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="98ec4-167">See also</span></span>

- [<span data-ttu-id="98ec4-168">Documentazione dell'API limite</span><span class="sxs-lookup"><span data-stu-id="98ec4-168">Boundary API documentation</span></span>](xref:Microsoft.MixedReality.Toolkit.Boundary)
- [<span data-ttu-id="98ec4-169">Sistema di limiti</span><span class="sxs-lookup"><span data-stu-id="98ec4-169">Boundary System</span></span>](boundary-system-getting-started.md)

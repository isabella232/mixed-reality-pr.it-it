---
title: NearMenu_README
description: Panoramica vicino ai tipi di menu in MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, menu near,
ms.openlocfilehash: 3a11020c9acf5a107ba35172a8ee536a1d78143c
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2021
ms.locfileid: "104695028"
---
# <a name="near-menu"></a><span data-ttu-id="5a51e-104">Menu adiacente</span><span class="sxs-lookup"><span data-stu-id="5a51e-104">Near menu</span></span>

![Menu vicino](Images/NearMenu/MRTK_UX_NearMenu.png)

<span data-ttu-id="5a51e-106">Near menu è un controllo UX che fornisce una raccolta di pulsanti o altri componenti dell'interfaccia utente.</span><span class="sxs-lookup"><span data-stu-id="5a51e-106">Near Menu is a UX control which provides a collection of buttons or other UI components.</span></span> <span data-ttu-id="5a51e-107">Il corpo dell'utente è fluttuante e facilmente accessibile in qualsiasi momento.</span><span class="sxs-lookup"><span data-stu-id="5a51e-107">It is floating around the user's body and easily accessible anytime.</span></span> <span data-ttu-id="5a51e-108">Poiché è a regime di controllo libero, l'interazione dell'utente con il contenuto di destinazione non viene disturbata.</span><span class="sxs-lookup"><span data-stu-id="5a51e-108">Since it is loosely coupled with the user, it does not disturb the user's interaction with the target content.</span></span> <span data-ttu-id="5a51e-109">L'utente può utilizzare il pulsante "Aggiungi" per bloccare/sbloccare il menu.</span><span class="sxs-lookup"><span data-stu-id="5a51e-109">The user can use the 'Pin' button to world-lock/unlock the menu.</span></span> <span data-ttu-id="5a51e-110">Il menu può essere afferrato e posizionato in una posizione specifica.</span><span class="sxs-lookup"><span data-stu-id="5a51e-110">The menu can be grabbed and placed at a specific position.</span></span>

## <a name="interaction-behavior"></a><span data-ttu-id="5a51e-111">Comportamento interazione</span><span class="sxs-lookup"><span data-stu-id="5a51e-111">Interaction behavior</span></span>

- <span data-ttu-id="5a51e-112">**Tag-along**: il menu segue e rimane entro 30-60cm dall'utente per le interazioni near.</span><span class="sxs-lookup"><span data-stu-id="5a51e-112">**Tag-along**: The menu follows you and stays within 30-60cm range from the user for the near interactions.</span></span>
- <span data-ttu-id="5a51e-113">**Pin**: usando il pulsante "pin", il menu può essere bloccato e rilasciato in tutto il mondo.</span><span class="sxs-lookup"><span data-stu-id="5a51e-113">**Pin**: Using the 'Pin' button, the menu can be world-locked and released.</span></span>
- <span data-ttu-id="5a51e-114">**Acquisisci e sposta**: il menu è sempre accessibile e mobile.</span><span class="sxs-lookup"><span data-stu-id="5a51e-114">**Grab and move**: The menu is always grabbable and movable.</span></span> <span data-ttu-id="5a51e-115">Indipendentemente dallo stato precedente, il menu verrà bloccato (con blocco internazionale) quando viene catturato e rilasciato.</span><span class="sxs-lookup"><span data-stu-id="5a51e-115">Regardless of the previous state, the menu will be pinned(world-locked) when grabbed and released.</span></span> <span data-ttu-id="5a51e-116">Sono disponibili segnali visivi per l'area di acquisizione.</span><span class="sxs-lookup"><span data-stu-id="5a51e-116">There are visual cues for the grabbable area.</span></span> <span data-ttu-id="5a51e-117">Vengono rivelate sulla prossimità.</span><span class="sxs-lookup"><span data-stu-id="5a51e-117">They are revealed on hand proximity.</span></span>

<img src="Images/NearMenu/MRTK_UX_NearMenu_Grab.png" alt="Near Menu Grab">

## <a name="prefabs"></a><span data-ttu-id="5a51e-118">Prefabbricati</span><span class="sxs-lookup"><span data-stu-id="5a51e-118">Prefabs</span></span>

<span data-ttu-id="5a51e-119">I prefissi dei menu near sono progettati per illustrare come usare i vari componenti di MRTK per compilare menu per le interazioni near.</span><span class="sxs-lookup"><span data-stu-id="5a51e-119">Near Menu prefabs are designed to demonstrate how to use MRTK's various components to build menus for near interactions.</span></span>

- <span data-ttu-id="5a51e-120">**NearMenu2x4. prefabbricate**</span><span class="sxs-lookup"><span data-stu-id="5a51e-120">**NearMenu2x4.prefab**</span></span>
- <span data-ttu-id="5a51e-121">**NearMenu3x1. prefabbricate**</span><span class="sxs-lookup"><span data-stu-id="5a51e-121">**NearMenu3x1.prefab**</span></span>
- <span data-ttu-id="5a51e-122">**NearMenu3x2. prefabbricate**</span><span class="sxs-lookup"><span data-stu-id="5a51e-122">**NearMenu3x2.prefab**</span></span>
- <span data-ttu-id="5a51e-123">**NearMenu3x3. prefabbricate**</span><span class="sxs-lookup"><span data-stu-id="5a51e-123">**NearMenu3x3.prefab**</span></span>
- <span data-ttu-id="5a51e-124">**NearMenu4x1. prefabbricate**</span><span class="sxs-lookup"><span data-stu-id="5a51e-124">**NearMenu4x1.prefab**</span></span>
- <span data-ttu-id="5a51e-125">**NearMenu4x2. prefabbricate**</span><span class="sxs-lookup"><span data-stu-id="5a51e-125">**NearMenu4x2.prefab**</span></span>

## <a name="example-scene"></a><span data-ttu-id="5a51e-126">Scena di esempio</span><span class="sxs-lookup"><span data-stu-id="5a51e-126">Example scene</span></span>

<span data-ttu-id="5a51e-127">È possibile trovare esempi di prefabbricati di menu near nella `NearMenuExamples` scena.</span><span class="sxs-lookup"><span data-stu-id="5a51e-127">You can find examples of Near Menu prefabs in the `NearMenuExamples` scene.</span></span>

<img src="Images/NearMenu/MRTK_UX_NearMenu_Examples.png" alt="Near menu Examples">

## <a name="structure"></a><span data-ttu-id="5a51e-128">Struttura</span><span class="sxs-lookup"><span data-stu-id="5a51e-128">Structure</span></span>

<span data-ttu-id="5a51e-129">I prefabbricati di menu near vengono creati con i componenti MRTK seguenti.</span><span class="sxs-lookup"><span data-stu-id="5a51e-129">Near Menu prefabs are made with following MRTK components.</span></span>

- <span data-ttu-id="5a51e-130">[**PressableButtonHoloLens2**](README_Button.md) prefabbricato</span><span class="sxs-lookup"><span data-stu-id="5a51e-130">[**PressableButtonHoloLens2**](README_Button.md) prefab</span></span>
- <span data-ttu-id="5a51e-131">[**Raccolta di oggetti Grid**](README_ObjectCollection.md): layout di più pulsanti nella griglia</span><span class="sxs-lookup"><span data-stu-id="5a51e-131">[**Grid Object Collection**](README_ObjectCollection.md): Multiple button layout in grid</span></span>
- <span data-ttu-id="5a51e-132">[**Gestore di manipolazione**](README_ManipulationHandler.md): selezionare e spostare il menu</span><span class="sxs-lookup"><span data-stu-id="5a51e-132">[**Manipulation Handler**](README_ManipulationHandler.md): Grab and move the menu</span></span>
- <span data-ttu-id="5a51e-133">[**RadialView Solver**](README_Solver.md): comportamento follow me (Tag-Along)</span><span class="sxs-lookup"><span data-stu-id="5a51e-133">[**RadialView Solver**](README_Solver.md): Follow Me(tag-along) behavior</span></span>

![Prefabbricato menu vicino](Images/NearMenu/MRTK_UX_NearMenu_Structure.png)

## <a name="how-to-customize"></a><span data-ttu-id="5a51e-135">Modalità di personalizzazione</span><span class="sxs-lookup"><span data-stu-id="5a51e-135">How to customize</span></span>

<span data-ttu-id="5a51e-136">**1. pulsanti Aggiungi/Rimuovi**</span><span class="sxs-lookup"><span data-stu-id="5a51e-136">**1. Add/Remove Buttons**</span></span>

<span data-ttu-id="5a51e-137">In `ButtonCollection` oggetto, Aggiungi o rimuovi pulsanti.</span><span class="sxs-lookup"><span data-stu-id="5a51e-137">Under `ButtonCollection` object, add or remove buttons.</span></span>  
<img src="Images/NearMenu/MRTK_UX_NearMenu_Custom0.png" width="450" alt="Near menu custom 0">

<span data-ttu-id="5a51e-138">**2. aggiornare la raccolta di oggetti Grid**</span><span class="sxs-lookup"><span data-stu-id="5a51e-138">**2. Update the Grid Object Collection**</span></span>

<span data-ttu-id="5a51e-139">Fare clic sul `Update Collection` pulsante nel controllo dell' `ButtonCollection` oggetto.</span><span class="sxs-lookup"><span data-stu-id="5a51e-139">Click `Update Collection` button in the Inspector of the `ButtonCollection` object.</span></span> <span data-ttu-id="5a51e-140">Il layout della griglia verrà aggiornato.</span><span class="sxs-lookup"><span data-stu-id="5a51e-140">It will update the grid layout.</span></span>  
<img src="Images/NearMenu/MRTK_UX_NearMenu_Custom1.png" alt="Near menu custom 1">

<span data-ttu-id="5a51e-141">È possibile configurare il numero di righe utilizzando `Rows` la proprietà della raccolta di oggetti Grid.</span><span class="sxs-lookup"><span data-stu-id="5a51e-141">You can configure the number of rows using `Rows` property of the Grid Object Collection.</span></span>  
<img src="Images/NearMenu/MRTK_UX_NearMenu_Custom2.png" alt="near menu custom 2">

<span data-ttu-id="5a51e-142">**3. regolare le dimensioni del backplate**</span><span class="sxs-lookup"><span data-stu-id="5a51e-142">**3. Adjust the backplate size**</span></span>

<span data-ttu-id="5a51e-143">Regolare le dimensioni dell' `Quad` oggetto sotto `Backplate` .</span><span class="sxs-lookup"><span data-stu-id="5a51e-143">Adjust the size of the `Quad` under `Backplate` object.</span></span> <span data-ttu-id="5a51e-144">La larghezza e l'altezza del backplate devono essere `0.032 * [Number of the buttons + 1]` .</span><span class="sxs-lookup"><span data-stu-id="5a51e-144">The width and height of the backplate should be `0.032 * [Number of the buttons + 1]`.</span></span> <span data-ttu-id="5a51e-145">Se, ad esempio, si dispone di 3 pulsanti x 2, la larghezza della contropiastra è `0.032 * 4` e l'altezza è `0.032 * 3` .</span><span class="sxs-lookup"><span data-stu-id="5a51e-145">For example, if you have 3 x 2 buttons, the width of the backplate is `0.032 * 4` and the height is `0.032 * 3`.</span></span> <span data-ttu-id="5a51e-146">È possibile inserire direttamente questa espressione nel campo di Unity.</span><span class="sxs-lookup"><span data-stu-id="5a51e-146">You can directly put this expression into the Unity's field.</span></span>  
<img src="Images/NearMenu/MRTK_UX_NearMenu_Custom3.png" width="450" alt="Near Menu Custom 3">

- <span data-ttu-id="5a51e-147">Le dimensioni predefinite del pulsante HoloLens 2 sono 3,2 x 3,2 cm (0.032 m)</span><span class="sxs-lookup"><span data-stu-id="5a51e-147">Default size of the HoloLens 2 button is 3.2x3.2 cm (0.032m)</span></span>

## <a name="see-also"></a><span data-ttu-id="5a51e-148">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="5a51e-148">See also</span></span>

- [<span data-ttu-id="5a51e-149">**Pulsanti**</span><span class="sxs-lookup"><span data-stu-id="5a51e-149">**Buttons**</span></span>](README_Button.md)
- [<span data-ttu-id="5a51e-150">**Controllo dei limiti**</span><span class="sxs-lookup"><span data-stu-id="5a51e-150">**Bounds Control**</span></span>](README_BoundsControl.md)
- [<span data-ttu-id="5a51e-151">**Slider**</span><span class="sxs-lookup"><span data-stu-id="5a51e-151">**Slider**</span></span>](README_Sliders.md)
- [<span data-ttu-id="5a51e-152">**Raccolta di oggetti Grid**</span><span class="sxs-lookup"><span data-stu-id="5a51e-152">**Grid Object Collection**</span></span>](README_ObjectCollection.md)
- [<span data-ttu-id="5a51e-153">**Gestore di manipolazione**</span><span class="sxs-lookup"><span data-stu-id="5a51e-153">**Manipulation Handler**</span></span>](README_ManipulationHandler.md)
- [<span data-ttu-id="5a51e-154">**Risolutore RadialView**</span><span class="sxs-lookup"><span data-stu-id="5a51e-154">**RadialView Solver**</span></span>](README_Solver.md)

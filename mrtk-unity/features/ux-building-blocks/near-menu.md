---
title: Menu adiacente
description: Panoramica dei tipi di menu near in MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, menu vicino,
ms.openlocfilehash: 15f53ad4e67a0b281750fd1df7f894c49f546531
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2021
ms.locfileid: "113175657"
---
# <a name="near-menu"></a><span data-ttu-id="b0bd6-104">Menu adiacente</span><span class="sxs-lookup"><span data-stu-id="b0bd6-104">Near menu</span></span>

![Menu vicino](../images/near-menu/MRTK_UX_NearMenu.png)

<span data-ttu-id="b0bd6-106">Near Menu è un controllo UX che fornisce una raccolta di pulsanti o altri componenti dell'interfaccia utente.</span><span class="sxs-lookup"><span data-stu-id="b0bd6-106">Near Menu is a UX control which provides a collection of buttons or other UI components.</span></span> <span data-ttu-id="b0bd6-107">È mobile intorno al corpo dell'utente e facilmente accessibile in qualsiasi momento.</span><span class="sxs-lookup"><span data-stu-id="b0bd6-107">It is floating around the user's body and easily accessible anytime.</span></span> <span data-ttu-id="b0bd6-108">Poiché è associato in modo libero all'utente, non influisce sull'interazione dell'utente con il contenuto di destinazione.</span><span class="sxs-lookup"><span data-stu-id="b0bd6-108">Since it is loosely coupled with the user, it does not disturb the user's interaction with the target content.</span></span> <span data-ttu-id="b0bd6-109">L'utente può usare il pulsante "Aggiungi" per bloccare o sbloccare il menu.</span><span class="sxs-lookup"><span data-stu-id="b0bd6-109">The user can use the 'Pin' button to world-lock/unlock the menu.</span></span> <span data-ttu-id="b0bd6-110">Il menu può essere afferrato e posizionato in una posizione specifica.</span><span class="sxs-lookup"><span data-stu-id="b0bd6-110">The menu can be grabbed and placed at a specific position.</span></span>

## <a name="interaction-behavior"></a><span data-ttu-id="b0bd6-111">Comportamento di interazione</span><span class="sxs-lookup"><span data-stu-id="b0bd6-111">Interaction behavior</span></span>

- <span data-ttu-id="b0bd6-112">**Tag lungo:** il menu segue l'utente e rimane entro un intervallo di 30-60 cm dall'utente per le interazioni da vicino.</span><span class="sxs-lookup"><span data-stu-id="b0bd6-112">**Tag-along**: The menu follows you and stays within 30-60cm range from the user for the near interactions.</span></span>
- <span data-ttu-id="b0bd6-113">**Aggiungi:** usando il pulsante "Aggiungi", il menu può essere bloccato a livello mondiale e rilasciato.</span><span class="sxs-lookup"><span data-stu-id="b0bd6-113">**Pin**: Using the 'Pin' button, the menu can be world-locked and released.</span></span>
- <span data-ttu-id="b0bd6-114">**Afferra e sposta:** il menu è sempre afferrabile e mobile.</span><span class="sxs-lookup"><span data-stu-id="b0bd6-114">**Grab and move**: The menu is always grabbable and movable.</span></span> <span data-ttu-id="b0bd6-115">Indipendentemente dallo stato precedente, il menu verrà aggiunto (bloccato al mondo) quando viene afferrato e rilasciato.</span><span class="sxs-lookup"><span data-stu-id="b0bd6-115">Regardless of the previous state, the menu will be pinned(world-locked) when grabbed and released.</span></span> <span data-ttu-id="b0bd6-116">Esistono segnali visivi per l'area afferrabile.</span><span class="sxs-lookup"><span data-stu-id="b0bd6-116">There are visual cues for the grabbable area.</span></span> <span data-ttu-id="b0bd6-117">Vengono rivelati sulla prossimità manuale.</span><span class="sxs-lookup"><span data-stu-id="b0bd6-117">They are revealed on hand proximity.</span></span>

<img src="../images/near-menu/MRTK_UX_NearMenu_Grab.png" alt="Near Menu grab">

## <a name="prefabs"></a><span data-ttu-id="b0bd6-118">Prefab</span><span class="sxs-lookup"><span data-stu-id="b0bd6-118">Prefabs</span></span>

<span data-ttu-id="b0bd6-119">I prefab near menu sono progettati per illustrare come usare i vari componenti di MRTK per creare menu per le interazioni da vicino.</span><span class="sxs-lookup"><span data-stu-id="b0bd6-119">Near Menu prefabs are designed to demonstrate how to use MRTK's various components to build menus for near interactions.</span></span>

- <span data-ttu-id="b0bd6-120">**NearMenu2x4.prefab**</span><span class="sxs-lookup"><span data-stu-id="b0bd6-120">**NearMenu2x4.prefab**</span></span>
- <span data-ttu-id="b0bd6-121">**NearMenu3x1.prefab**</span><span class="sxs-lookup"><span data-stu-id="b0bd6-121">**NearMenu3x1.prefab**</span></span>
- <span data-ttu-id="b0bd6-122">**NearMenu3x2.prefab**</span><span class="sxs-lookup"><span data-stu-id="b0bd6-122">**NearMenu3x2.prefab**</span></span>
- <span data-ttu-id="b0bd6-123">**NearMenu3x3.prefab**</span><span class="sxs-lookup"><span data-stu-id="b0bd6-123">**NearMenu3x3.prefab**</span></span>
- <span data-ttu-id="b0bd6-124">**NearMenu4x1.prefab**</span><span class="sxs-lookup"><span data-stu-id="b0bd6-124">**NearMenu4x1.prefab**</span></span>
- <span data-ttu-id="b0bd6-125">**NearMenu4x2.prefab**</span><span class="sxs-lookup"><span data-stu-id="b0bd6-125">**NearMenu4x2.prefab**</span></span>

## <a name="example-scene"></a><span data-ttu-id="b0bd6-126">Scena di esempio</span><span class="sxs-lookup"><span data-stu-id="b0bd6-126">Example scene</span></span>

<span data-ttu-id="b0bd6-127">È possibile trovare esempi di prefab near menu nella `NearMenuExamples` scena.</span><span class="sxs-lookup"><span data-stu-id="b0bd6-127">You can find examples of Near Menu prefabs in the `NearMenuExamples` scene.</span></span>

<img src="../images/near-menu/MRTK_UX_NearMenu_Examples.png" alt="Near Menu Example">

## <a name="structure"></a><span data-ttu-id="b0bd6-128">Struttura</span><span class="sxs-lookup"><span data-stu-id="b0bd6-128">Structure</span></span>

<span data-ttu-id="b0bd6-129">I prefab near menu sono realizzati con i componenti MRTK seguenti.</span><span class="sxs-lookup"><span data-stu-id="b0bd6-129">Near Menu prefabs are made with following MRTK components.</span></span>

- <span data-ttu-id="b0bd6-130">[**Prefab PressableButtonHoloLens2**](button.md)</span><span class="sxs-lookup"><span data-stu-id="b0bd6-130">[**PressableButtonHoloLens2**](button.md) prefab</span></span>
- <span data-ttu-id="b0bd6-131">[**Raccolta di oggetti Grid:**](object-collection.md)layout a più pulsanti nella griglia</span><span class="sxs-lookup"><span data-stu-id="b0bd6-131">[**Grid Object Collection**](object-collection.md): Multiple button layout in grid</span></span>
- <span data-ttu-id="b0bd6-132">[**Manipulation Handler (Gestore**](manipulation-handler.md)manipolazione): afferra e sposta il menu</span><span class="sxs-lookup"><span data-stu-id="b0bd6-132">[**Manipulation Handler**](manipulation-handler.md): Grab and move the menu</span></span>
- <span data-ttu-id="b0bd6-133">[**RadialView Solver**](solvers/solver.md): Follow Me(tag-along) behavior (Comportamento del risolutore RadialView: seguimi)(tag-along)</span><span class="sxs-lookup"><span data-stu-id="b0bd6-133">[**RadialView Solver**](solvers/solver.md): Follow Me(tag-along) behavior</span></span>

![Prefab menu vicino](../images/near-menu/MRTK_UX_NearMenu_Structure.png)

## <a name="how-to-customize"></a><span data-ttu-id="b0bd6-135">Modalità di personalizzazione</span><span class="sxs-lookup"><span data-stu-id="b0bd6-135">How to customize</span></span>

<span data-ttu-id="b0bd6-136">**1. Aggiungere/rimuovere pulsanti**</span><span class="sxs-lookup"><span data-stu-id="b0bd6-136">**1. Add/Remove Buttons**</span></span>

<span data-ttu-id="b0bd6-137">`ButtonCollection`Nell'oggetto aggiungere o rimuovere pulsanti.</span><span class="sxs-lookup"><span data-stu-id="b0bd6-137">Under `ButtonCollection` object, add or remove buttons.</span></span>  
<img src="../images/near-menu/MRTK_UX_NearMenu_Custom0.png" width="450" alt="Near Menu Custome 0">

<span data-ttu-id="b0bd6-138">**2. Aggiornare la raccolta di oggetti Grid**</span><span class="sxs-lookup"><span data-stu-id="b0bd6-138">**2. Update the Grid Object Collection**</span></span>

<span data-ttu-id="b0bd6-139">Fare `Update Collection` clic sul pulsante nel controllo dell'oggetto. `ButtonCollection`</span><span class="sxs-lookup"><span data-stu-id="b0bd6-139">Click `Update Collection` button in the Inspector of the `ButtonCollection` object.</span></span> <span data-ttu-id="b0bd6-140">Aggiornerà il layout della griglia.</span><span class="sxs-lookup"><span data-stu-id="b0bd6-140">It will update the grid layout.</span></span>  
<img src="../images/near-menu/MRTK_UX_NearMenu_Custom1.png" alt="Near Menu Custome 1">

<span data-ttu-id="b0bd6-141">È possibile configurare il numero di righe usando `Rows` la proprietà della raccolta di oggetti Grid.</span><span class="sxs-lookup"><span data-stu-id="b0bd6-141">You can configure the number of rows using `Rows` property of the Grid Object Collection.</span></span>  
<img src="../images/near-menu/MRTK_UX_NearMenu_Custom2.png" alt="Near Menu Custome 2">

<span data-ttu-id="b0bd6-142">**3. Regolare le dimensioni del backplate**</span><span class="sxs-lookup"><span data-stu-id="b0bd6-142">**3. Adjust the backplate size**</span></span>

<span data-ttu-id="b0bd6-143">Regolare le dimensioni dell'oggetto `Quad` `Backplate` nell'oggetto .</span><span class="sxs-lookup"><span data-stu-id="b0bd6-143">Adjust the size of the `Quad` under `Backplate` object.</span></span> <span data-ttu-id="b0bd6-144">La larghezza e l'altezza del backplate devono essere `0.032 * [Number of the buttons + 1]` .</span><span class="sxs-lookup"><span data-stu-id="b0bd6-144">The width and height of the backplate should be `0.032 * [Number of the buttons + 1]`.</span></span> <span data-ttu-id="b0bd6-145">Ad esempio, se si dispone di 3 x 2 pulsanti, la larghezza del backplate è `0.032 * 4` e l'altezza è `0.032 * 3` .</span><span class="sxs-lookup"><span data-stu-id="b0bd6-145">For example, if you have 3 x 2 buttons, the width of the backplate is `0.032 * 4` and the height is `0.032 * 3`.</span></span> <span data-ttu-id="b0bd6-146">È possibile inserire direttamente questa espressione nel campo di Unity.</span><span class="sxs-lookup"><span data-stu-id="b0bd6-146">You can directly put this expression into the Unity's field.</span></span>  
<img src="../images/near-menu/MRTK_UX_NearMenu_Custom3.png" width="450" alt="Near Menu Custome 3">

- <span data-ttu-id="b0bd6-147">La dimensione predefinita del HoloLens 2 è 3,2x3,2 cm (0,032 m)</span><span class="sxs-lookup"><span data-stu-id="b0bd6-147">Default size of the HoloLens 2 button is 3.2x3.2 cm (0.032m)</span></span>

## <a name="see-also"></a><span data-ttu-id="b0bd6-148">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="b0bd6-148">See also</span></span>

- [<span data-ttu-id="b0bd6-149">**Pulsanti**</span><span class="sxs-lookup"><span data-stu-id="b0bd6-149">**Buttons**</span></span>](button.md)
- [<span data-ttu-id="b0bd6-150">**Controllo Bounds**</span><span class="sxs-lookup"><span data-stu-id="b0bd6-150">**Bounds Control**</span></span>](bounds-control.md)
- [<span data-ttu-id="b0bd6-151">**Slider**</span><span class="sxs-lookup"><span data-stu-id="b0bd6-151">**Slider**</span></span>](sliders.md)
- [<span data-ttu-id="b0bd6-152">**Raccolta di oggetti Grid**</span><span class="sxs-lookup"><span data-stu-id="b0bd6-152">**Grid Object Collection**</span></span>](object-collection.md)
- [<span data-ttu-id="b0bd6-153">**Gestore di manipolazione**</span><span class="sxs-lookup"><span data-stu-id="b0bd6-153">**Manipulation Handler**</span></span>](manipulation-handler.md)
- [<span data-ttu-id="b0bd6-154">**Risolutore RadialView**</span><span class="sxs-lookup"><span data-stu-id="b0bd6-154">**RadialView Solver**</span></span>](solvers/solver.md)

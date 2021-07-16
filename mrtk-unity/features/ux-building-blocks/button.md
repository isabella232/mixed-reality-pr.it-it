---
title: Pulsanti
description: Panoramica sui pulsanti in MRTK
author: cre8ivepark
ms.author: dongpark
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, pulsanti MRTK
ms.openlocfilehash: 16baeede2c63437e933eb1367f01af7f372cd62f
ms.sourcegitcommit: 912fa204ef79e9b973eab9b862846ba5ed5cd69f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/16/2021
ms.locfileid: "114281850"
---
# <a name="buttons"></a><span data-ttu-id="05b49-104">Pulsanti</span><span class="sxs-lookup"><span data-stu-id="05b49-104">Buttons</span></span>

![Pulsante principale](../images/button/MRTK_Button_Main.png)

<span data-ttu-id="05b49-106">Un pulsante offre all'utente un modo per attivare un'azione immediata.</span><span class="sxs-lookup"><span data-stu-id="05b49-106">A button gives the user a way to trigger an immediate action.</span></span> <span data-ttu-id="05b49-107">È uno dei componenti di base della realtà mista.</span><span class="sxs-lookup"><span data-stu-id="05b49-107">It is one of the most foundational components in mixed reality.</span></span> <span data-ttu-id="05b49-108">MRTK offre vari tipi di prefab per i pulsanti.</span><span class="sxs-lookup"><span data-stu-id="05b49-108">MRTK provides various types of button prefabs.</span></span>

## <a name="button-prefabs-in-mrtk"></a><span data-ttu-id="05b49-109">Prefab dei pulsanti in MRTK</span><span class="sxs-lookup"><span data-stu-id="05b49-109">Button prefabs in MRTK</span></span>

<span data-ttu-id="05b49-110">Esempi dei prefab dei pulsanti nella ``MRTK/SDK/Features/UX/Interactable/Prefabs`` cartella</span><span class="sxs-lookup"><span data-stu-id="05b49-110">Examples of the button prefabs under ``MRTK/SDK/Features/UX/Interactable/Prefabs`` folder</span></span>

### <a name="unity-ui-imagegraphic-based-buttons"></a><span data-ttu-id="05b49-111">Pulsanti basati su immagine/grafica dell'interfaccia utente di Unity</span><span class="sxs-lookup"><span data-stu-id="05b49-111">Unity UI Image/Graphic based buttons</span></span>

* `UnityUIInteractableButton.prefab`
* `PressableButtonUnityUI.prefab`
* `PressableButtonUnityUICircular.prefab`
* `PressableButtonHoloLens2UnityUI.prefab`

### <a name="collider-based-buttons"></a><span data-ttu-id="05b49-112">Pulsanti basati su collisori</span><span class="sxs-lookup"><span data-stu-id="05b49-112">Collider based buttons</span></span>

:::row:::
    :::column:::
    ![PressableButtonHoloLens2](../images/button/MRTK_Button_Prefabs_HoloLens2.png) <span data-ttu-id="05b49-114">PressableButtonHoloLens2</span><span class="sxs-lookup"><span data-stu-id="05b49-114">PressableButtonHoloLens2</span></span> 
    :::column-end:::
    :::column:::
    ![PressableButtonHoloLens2Unplated](../images/button/MRTK_Button_Prefabs_HoloLens2Unplated.png) <span data-ttu-id="05b49-116">PressableButtonHoloLens2Unplated</span><span class="sxs-lookup"><span data-stu-id="05b49-116">PressableButtonHoloLens2Unplated</span></span> 
    :::column-end:::
    :::column:::
    ![PressableButtonHoloLens2Circular](../images/button/MRTK_Button_Prefabs_HoloLens2Circular.png) <span data-ttu-id="05b49-118">PressableButtonHoloLens2Circular</span><span class="sxs-lookup"><span data-stu-id="05b49-118">PressableButtonHoloLens2Circular</span></span> 
    :::column-end:::
:::row-end:::
:::row:::
    :::column::: 
    <span data-ttu-id="05b49-119">HoloLens 2 pulsante in stile shell di HoloLens 2 con backplate che supporta vari commenti visivi, ad esempio luce del bordo, luce di prossimità e pappe anteriore compresso</span><span class="sxs-lookup"><span data-stu-id="05b49-119">HoloLens 2's shell-style button with backplate which supports various visual feedback such as border light, proximity light, and compressed front plate</span></span>
    :::column-end:::
    :::column:::
    <span data-ttu-id="05b49-120">HoloLens 2 di stile della shell senza backplate</span><span class="sxs-lookup"><span data-stu-id="05b49-120">HoloLens 2's shell-style button without backplate</span></span>
    :::column-end:::
    :::column:::
    <span data-ttu-id="05b49-121">HoloLens 2 in stile shell di HoloLens 2 con forma circolare</span><span class="sxs-lookup"><span data-stu-id="05b49-121">HoloLens 2's shell-style button with circular shape</span></span>
    :::column-end:::
:::row-end:::
:::row:::
    :::column::: 
    <span data-ttu-id="05b49-122">![PressableButtonHoloLens2_32x96 ](../images/button/MRTK_Button_Prefabs_HoloLens2_32x96.png) **PressableButtonHoloLens2_32x96**</span><span class="sxs-lookup"><span data-stu-id="05b49-122">![PressableButtonHoloLens2_32x96](../images/button/MRTK_Button_Prefabs_HoloLens2_32x96.png) **PressableButtonHoloLens2_32x96**</span></span>
    :::column-end:::
    :::column:::
    <span data-ttu-id="05b49-123">![PressableButtonHoloLens2Bar3H ](../images/button/MRTK_Button_Prefabs_HoloLens2BarH.png) **PressableButtonHoloLens2Bar3H**</span><span class="sxs-lookup"><span data-stu-id="05b49-123">![PressableButtonHoloLens2Bar3H](../images/button/MRTK_Button_Prefabs_HoloLens2BarH.png) **PressableButtonHoloLens2Bar3H**</span></span>
    :::column-end:::
    :::column:::
    <span data-ttu-id="05b49-124">![PressableButtonHoloLens2Bar3V ](../images/button/MRTK_Button_Prefabs_HoloLens2BarV.png) **PressableButtonHoloLens2Bar3V**</span><span class="sxs-lookup"><span data-stu-id="05b49-124">![PressableButtonHoloLens2Bar3V](../images/button/MRTK_Button_Prefabs_HoloLens2BarV.png) **PressableButtonHoloLens2Bar3V**</span></span>
    :::column-end:::
:::row-end:::
:::row:::
    :::column::: 
    <span data-ttu-id="05b49-125">Pulsante HoloLens 2 stile shell di Wide HoloLens 2 32x96mm</span><span class="sxs-lookup"><span data-stu-id="05b49-125">Wide HoloLens 2's shell-style button 32x96mm</span></span>
    :::column-end:::
    :::column:::
    <span data-ttu-id="05b49-126">Barra dei HoloLens 2 orizzontale con backplate condiviso</span><span class="sxs-lookup"><span data-stu-id="05b49-126">Horizontal HoloLens 2 button bar with shared backplate</span></span>
    :::column-end:::
    :::column:::
    <span data-ttu-id="05b49-127">Barra HoloLens 2 pulsante con backplate condiviso</span><span class="sxs-lookup"><span data-stu-id="05b49-127">Vertical HoloLens 2 button bar with shared backplate</span></span>
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::     
    <span data-ttu-id="05b49-128">![PressableButtonHoloLens2ToggleCheckBox_32x32 ](../images/button/MRTK_Button_Prefabs_HoloLens2_Checkbox.png) **PressableButtonHoloLens2ToggleCheckBox_32x32**</span><span class="sxs-lookup"><span data-stu-id="05b49-128">![PressableButtonHoloLens2ToggleCheckBox_32x32](../images/button/MRTK_Button_Prefabs_HoloLens2_Checkbox.png) **PressableButtonHoloLens2ToggleCheckBox_32x32**</span></span> 
    :::column-end:::
    :::column:::
    <span data-ttu-id="05b49-129">![PressableButtonHoloLens2ToggleSwitch_32x32 ](../images/button/MRTK_Button_Prefabs_HoloLens2_Switch.png) **PressableButtonHoloLens2ToggleSwitch_32x32**</span><span class="sxs-lookup"><span data-stu-id="05b49-129">![PressableButtonHoloLens2ToggleSwitch_32x32](../images/button/MRTK_Button_Prefabs_HoloLens2_Switch.png) **PressableButtonHoloLens2ToggleSwitch_32x32**</span></span>
    :::column-end:::
    :::column:::
    <span data-ttu-id="05b49-130">![PressableButtonHoloLens2ToggleRadio_32x32 ](../images/button/MRTK_Button_Prefabs_HoloLens2_Radio.png) **PressableButtonHoloLens2ToggleRadio_32x32**</span><span class="sxs-lookup"><span data-stu-id="05b49-130">![PressableButtonHoloLens2ToggleRadio_32x32](../images/button/MRTK_Button_Prefabs_HoloLens2_Radio.png) **PressableButtonHoloLens2ToggleRadio_32x32**</span></span>
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::     
    <span data-ttu-id="05b49-131">HoloLens 2 della casella di controllo di tipo shell 32x32mm</span><span class="sxs-lookup"><span data-stu-id="05b49-131">HoloLens 2's shell-style checkbox 32x32mm</span></span>
    :::column-end:::
    :::column:::
    <span data-ttu-id="05b49-132">HoloLens 2 di tipo shell di HoloLens 2 32x32mm</span><span class="sxs-lookup"><span data-stu-id="05b49-132">HoloLens 2's shell-style switch 32x32mm</span></span> 
    :::column-end:::
    :::column:::
    <span data-ttu-id="05b49-133">HoloLens 2 radio in stile shell di HoloLens 2 32x32mm</span><span class="sxs-lookup"><span data-stu-id="05b49-133">HoloLens 2's shell-style radio 32x32mm</span></span>
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::     
    <span data-ttu-id="05b49-134">![PressableButtonHoloLens2ToggleCheckBox_32x96 ](../images/button/MRTK_Button_Prefabs_HoloLens2_Checkbox_32x96.png) **PressableButtonHoloLens2ToggleCheckBox_32x96**</span><span class="sxs-lookup"><span data-stu-id="05b49-134">![PressableButtonHoloLens2ToggleCheckBox_32x96](../images/button/MRTK_Button_Prefabs_HoloLens2_Checkbox_32x96.png) **PressableButtonHoloLens2ToggleCheckBox_32x96**</span></span>
    :::column-end:::
    :::column:::
    <span data-ttu-id="05b49-135">![PressableButtonHoloLens2ToggleSwitch_32x96 ](../images/button/MRTK_Button_Prefabs_HoloLens2_Switch_32x96.png) **PressableButtonHoloLens2ToggleSwitch_32x96**</span><span class="sxs-lookup"><span data-stu-id="05b49-135">![PressableButtonHoloLens2ToggleSwitch_32x96](../images/button/MRTK_Button_Prefabs_HoloLens2_Switch_32x96.png) **PressableButtonHoloLens2ToggleSwitch_32x96**</span></span> 
    :::column-end:::
    :::column:::
    <span data-ttu-id="05b49-136">![PressableButtonHoloLens2ToggleRadio_32x96 ](../images/button/MRTK_Button_Prefabs_HoloLens2_Radio_32x96.png) **PressableButtonHoloLens2ToggleRadio_32x96**</span><span class="sxs-lookup"><span data-stu-id="05b49-136">![PressableButtonHoloLens2ToggleRadio_32x96](../images/button/MRTK_Button_Prefabs_HoloLens2_Radio_32x96.png) **PressableButtonHoloLens2ToggleRadio_32x96**</span></span> 
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::  
    <span data-ttu-id="05b49-137">HoloLens 2 di controllo di tipo shell di HoloLens 2 32x96mm</span><span class="sxs-lookup"><span data-stu-id="05b49-137">HoloLens 2's shell-style checkbox 32x96mm</span></span>
    :::column-end:::
    :::column:::
    <span data-ttu-id="05b49-138">HoloLens 2 di shell di HoloLens 2 32x96mm</span><span class="sxs-lookup"><span data-stu-id="05b49-138">HoloLens 2's shell-style switch 32x96mm</span></span>
    :::column-end:::
    :::column:::
    <span data-ttu-id="05b49-139">HoloLens 2 radio in stile shell di HoloLens 2 32x96mm</span><span class="sxs-lookup"><span data-stu-id="05b49-139">HoloLens 2's shell-style radio 32x96mm</span></span>
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::  
    <span data-ttu-id="05b49-140">![Radiale ](../images/button/MRTK_Button_Radial.png) **radiale**</span><span class="sxs-lookup"><span data-stu-id="05b49-140">![Radial](../images/button/MRTK_Button_Radial.png) **Radial**</span></span>
    :::column-end:::
    :::column:::
    <span data-ttu-id="05b49-141">![Casella di controllo ](../images/button/MRTK_Button_Checkbox.png) **della casella di controllo**</span><span class="sxs-lookup"><span data-stu-id="05b49-141">![Checkbox](../images/button/MRTK_Button_Checkbox.png) **Checkbox**</span></span>
    :::column-end:::
    :::column:::
    <span data-ttu-id="05b49-142">![ToggleSwitch ](../images/button/MRTK_Button_ToggleSwitch.png) **ToggleSwitch**</span><span class="sxs-lookup"><span data-stu-id="05b49-142">![ToggleSwitch](../images/button/MRTK_Button_ToggleSwitch.png) **ToggleSwitch**</span></span>
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::  
    <span data-ttu-id="05b49-143">Pulsante radiale</span><span class="sxs-lookup"><span data-stu-id="05b49-143">Radial button</span></span> 
    :::column-end:::
    :::column:::
    <span data-ttu-id="05b49-144">Casella di controllo</span><span class="sxs-lookup"><span data-stu-id="05b49-144">Checkbox</span></span> 
    :::column-end:::
    :::column:::
    <span data-ttu-id="05b49-145">Interruttore Attiva/Disattiva</span><span class="sxs-lookup"><span data-stu-id="05b49-145">Toggle switch</span></span>
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::  
    <span data-ttu-id="05b49-146">![ButtonHoloLens1 ](../images/button/MRTK_Button_HoloLens1.png) **ButtonHoloLens1**</span><span class="sxs-lookup"><span data-stu-id="05b49-146">![ButtonHoloLens1](../images/button/MRTK_Button_HoloLens1.png) **ButtonHoloLens1**</span></span>
    :::column-end:::
    :::column:::
    <span data-ttu-id="05b49-147">![PressableRoundButton ](../images/button/MRTK_Button_Round.png) **PressableRoundButton**</span><span class="sxs-lookup"><span data-stu-id="05b49-147">![PressableRoundButton](../images/button/MRTK_Button_Round.png) **PressableRoundButton**</span></span> 
    :::column-end:::
    :::column:::
    <span data-ttu-id="05b49-148">![Pulsante di base ](../images/button/MRTK_Button_Base.png) **del pulsante**</span><span class="sxs-lookup"><span data-stu-id="05b49-148">![Button Base](../images/button/MRTK_Button_Base.png) **Button**</span></span>
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::  
    <span data-ttu-id="05b49-149">HoloLens pulsante di stile della shell di prima generazione</span><span class="sxs-lookup"><span data-stu-id="05b49-149">HoloLens 1st gen's shell style button</span></span>
    :::column-end:::
    :::column:::
    <span data-ttu-id="05b49-150">Pulsante di selezione forma rotonda</span><span class="sxs-lookup"><span data-stu-id="05b49-150">Round shape push button</span></span>
    :::column-end:::
    :::column:::
    <span data-ttu-id="05b49-151">Pulsante Di base</span><span class="sxs-lookup"><span data-stu-id="05b49-151">Basic button</span></span>
    :::column-end:::
:::row-end:::

<span data-ttu-id="05b49-152">`Button`(Assets/MRTK/SDK/Features/UX/Interactable/Prefabs/Button.prefab) si basa sul concetto [interactable](interactable.md) per fornire controlli dell'interfaccia utente semplici per i pulsanti o altri tipi di superfici interattive.</span><span class="sxs-lookup"><span data-stu-id="05b49-152">The `Button` (Assets/MRTK/SDK/Features/UX/Interactable/Prefabs/Button.prefab) is based on the [Interactable](interactable.md) concept to provide easy UI controls for buttons or other types of interactive surfaces.</span></span> <span data-ttu-id="05b49-153">Il pulsante baseline supporta tutti i metodi di input disponibili, incluso l'input della mano articolato per le interazioni da vicino, nonché lo sguardo fisso e il tocco nell'aria per le interazioni da lontano.</span><span class="sxs-lookup"><span data-stu-id="05b49-153">The baseline button supports all available input methods, including articulated hand input for the near interactions as well as gaze + air-tap for the far interactions.</span></span> <span data-ttu-id="05b49-154">È anche possibile usare il comando vocale per attivare il pulsante.</span><span class="sxs-lookup"><span data-stu-id="05b49-154">You can also use voice command to trigger the button.</span></span>

<span data-ttu-id="05b49-155">`PressableButtonHoloLens2`(Assets/MRTK/SDK/Features/UX/Interactable/Prefabs/PressableButtonHoloLens2.prefab) è un pulsante di stile della shell di HoloLens 2 che supporta il movimento preciso del pulsante per l'input di tracciamento diretto della mano.</span><span class="sxs-lookup"><span data-stu-id="05b49-155">`PressableButtonHoloLens2` (Assets/MRTK/SDK/Features/UX/Interactable/Prefabs/PressableButtonHoloLens2.prefab) is HoloLens 2's shell style button that supports the precise movement of the button for the direct hand tracking input.</span></span> <span data-ttu-id="05b49-156">Combina script `Interactable` con `PressableButton` script.</span><span class="sxs-lookup"><span data-stu-id="05b49-156">It combines `Interactable` script with `PressableButton` script.</span></span>

<span data-ttu-id="05b49-157">Per HoloLens 2, è consigliabile usare pulsanti con un backplate opaco.</span><span class="sxs-lookup"><span data-stu-id="05b49-157">For HoloLens 2, it is recommended to use buttons with an opaque backplate.</span></span> <span data-ttu-id="05b49-158">I pulsanti trasparenti non sono consigliati a causa di questi problemi di usabilità e stabilità:</span><span class="sxs-lookup"><span data-stu-id="05b49-158">Transparent buttons are not recommended because of these usability and stability issues:</span></span>

* <span data-ttu-id="05b49-159">L'icona e il testo sono difficili da leggere con l'ambiente fisico</span><span class="sxs-lookup"><span data-stu-id="05b49-159">Icon and text are difficult to read with the physical environment</span></span>
* <span data-ttu-id="05b49-160">È difficile comprendere quando viene attivato l'evento</span><span class="sxs-lookup"><span data-stu-id="05b49-160">It is hard to understand when the event triggers</span></span>
* <span data-ttu-id="05b49-161">Ologrammi visualizzati tramite un piano trasparente possono essere instabili con la HoloLens 2 LSR di profondità del sistema</span><span class="sxs-lookup"><span data-stu-id="05b49-161">Holograms that are displayed through a transparent plane can be unstable with HoloLens 2's Depth LSR stabilization</span></span>

![Pulsante con i toni](../images/button/MRTK_Button_UsePlated.png)

## <a name="how-to-use-pressable-buttons"></a><span data-ttu-id="05b49-163">Come usare i pulsanti a pressione</span><span class="sxs-lookup"><span data-stu-id="05b49-163">How to use pressable buttons</span></span>

### <a name="unity-ui-based-buttons"></a><span data-ttu-id="05b49-164">Pulsanti basati sull'interfaccia utente di Unity</span><span class="sxs-lookup"><span data-stu-id="05b49-164">Unity UI based buttons</span></span>

<span data-ttu-id="05b49-165">Creare un'area di disegno nella scena (GameObject -> UI -> Canvas).</span><span class="sxs-lookup"><span data-stu-id="05b49-165">Create a Canvas in your scene (GameObject -> UI -> Canvas).</span></span> <span data-ttu-id="05b49-166">Nel pannello Inspector (Controllo) per Canvas:</span><span class="sxs-lookup"><span data-stu-id="05b49-166">In the Inspector panel for your Canvas:</span></span>

* <span data-ttu-id="05b49-167">Fare clic su "Convert to MRTK Canvas" (Converti in canvas MRTK)</span><span class="sxs-lookup"><span data-stu-id="05b49-167">Click "Convert to MRTK Canvas"</span></span>
* <span data-ttu-id="05b49-168">Fare clic su "Add NearInteractionTouchableUnityUI" (Aggiungi NearInteractionTouchableUnityUI)</span><span class="sxs-lookup"><span data-stu-id="05b49-168">Click "Add NearInteractionTouchableUnityUI"</span></span>
* <span data-ttu-id="05b49-169">Impostare la scala X, Y e Z del componente Rect Transform su 0,001</span><span class="sxs-lookup"><span data-stu-id="05b49-169">Set the Rect Transform component's X, Y, and Z scale to 0.001</span></span>

<span data-ttu-id="05b49-170">Trascinare `PressableButtonUnityUI` quindi (Assets/MRTK/SDK/Features/UX/Interactable/Prefabs/PressableButtonUnityUI.prefab), `PressableButtonUnityUICircular` (Assets/MRTK/SDK/Features/UX/Interactable/Prefabs/PressableButtonUnityUICircular.prefab) o `PressableButtonHoloLens2UnityUI` (Assets/MRTK/SDK/Features/UX/Interactable/Prefabs/PressableButtonHoloLens2UnityUI.prefab) nell'area di disegno.</span><span class="sxs-lookup"><span data-stu-id="05b49-170">Then, drag `PressableButtonUnityUI` (Assets/MRTK/SDK/Features/UX/Interactable/Prefabs/PressableButtonUnityUI.prefab), `PressableButtonUnityUICircular` (Assets/MRTK/SDK/Features/UX/Interactable/Prefabs/PressableButtonUnityUICircular.prefab), or `PressableButtonHoloLens2UnityUI` (Assets/MRTK/SDK/Features/UX/Interactable/Prefabs/PressableButtonHoloLens2UnityUI.prefab) onto the Canvas.</span></span>

### <a name="collider-based-buttons"></a><span data-ttu-id="05b49-171">Pulsanti basati su collisori</span><span class="sxs-lookup"><span data-stu-id="05b49-171">Collider based buttons</span></span>

<span data-ttu-id="05b49-172">È sufficiente trascinare `PressableButtonHoloLens2` (Assets/MRTK/SDK/Features/UX/Interactable/Prefabs/PressableButtonHoloLens2.prefab) o `PressableButtonHoloLens2Unplated` (Assets/MRTK/SDK/Features/UX/Interactable/Prefabs/PressableButtonHoloLens2Unplated.prefab) nella scena.</span><span class="sxs-lookup"><span data-stu-id="05b49-172">Simply drag `PressableButtonHoloLens2` (Assets/MRTK/SDK/Features/UX/Interactable/Prefabs/PressableButtonHoloLens2.prefab) or `PressableButtonHoloLens2Unplated` (Assets/MRTK/SDK/Features/UX/Interactable/Prefabs/PressableButtonHoloLens2Unplated.prefab) into the scene.</span></span> <span data-ttu-id="05b49-173">Questi prefab dei pulsanti sono già configurati per fornire feedback audio-visivo per i vari tipi di input, tra cui input con mano articolata e sguardo fisso.</span><span class="sxs-lookup"><span data-stu-id="05b49-173">These button prefabs are already configured to have audio-visual feedback for the various types of inputs, including articulated hand input and gaze.</span></span>

<span data-ttu-id="05b49-174">Gli eventi esposti nel prefab stesso e nel componente [Interactable](interactable.md) possono essere usati per attivare azioni aggiuntive.</span><span class="sxs-lookup"><span data-stu-id="05b49-174">The events exposed in the prefab itself as well as the [Interactable](interactable.md) component can be used to trigger additional actions.</span></span> <span data-ttu-id="05b49-175">I pulsanti a pressione nella scena [HandInteractionExample](../example-scenes/hand-interaction-examples.md) usano l'evento *OnClick* di Interactable per attivare una modifica nel colore di un cubo.</span><span class="sxs-lookup"><span data-stu-id="05b49-175">The pressable buttons in the [HandInteractionExample scene](../example-scenes/hand-interaction-examples.md) use Interactable's *OnClick* event to trigger a change in the color of a cube.</span></span> <span data-ttu-id="05b49-176">Questo evento viene attivato per diversi tipi di metodi di input, ad esempio sguardo fisso, tocco d'aria, raggio della mano e pressione di pulsanti fisici tramite lo script del pulsante a pressione.</span><span class="sxs-lookup"><span data-stu-id="05b49-176">This event gets triggered for different types of input methods such as gaze, air-tap, hand-ray, as well as physical button presses through the pressable button script.</span></span>

<img src="../images/button/MRTK_Button_HowToUse_Interactable.png" width="450" alt="How to Use Interactable">

<span data-ttu-id="05b49-177">È possibile configurare quando il pulsante a pressione genera *l'evento OnClick* tramite `PhysicalPressEventRouter` sul pulsante.</span><span class="sxs-lookup"><span data-stu-id="05b49-177">You can configure when the pressable button fires the *OnClick* event via the `PhysicalPressEventRouter` on the button.</span></span> <span data-ttu-id="05b49-178">Ad esempio, è possibile impostare *OnClick* in modo che venga generato quando il pulsante viene premuto per la prima volta, anziché essere premuto e rilasciato, impostando *Interactable On Click* su *Event On Press*.</span><span class="sxs-lookup"><span data-stu-id="05b49-178">For example, you can set *OnClick* to fire when the button is first pressed, as opposed to being pressed and released, by setting *Interactable On Click* to *Event On Press*.</span></span>

<img src="../images/button/MRTK_Button_HowTo_Events.png" width="450" alt="How to use events">

<span data-ttu-id="05b49-179">Per sfruttare informazioni specifiche sullo stato di input della mano articolata, è possibile usare gli eventi dei pulsanti a pressione: *Inizio* tocco, *Fine* tocco, *Pulsante* premuto, *Pulsante rilasciato.*</span><span class="sxs-lookup"><span data-stu-id="05b49-179">To leverage specific articulated hand input state information, you can use pressable buttons events - *Touch Begin*, *Touch End*, *Button Pressed*, *Button Released*.</span></span> <span data-ttu-id="05b49-180">Questi eventi, tuttavia, non verranno generati in risposta al tocco, al raggio della mano o agli input oculare.</span><span class="sxs-lookup"><span data-stu-id="05b49-180">These events will not fire in response to air-tap, hand-ray, or eye inputs, however.</span></span> <span data-ttu-id="05b49-181">**Per supportare le interazioni da vicino e da lontano, è consigliabile usare l'evento *OnClick di Interactable.***</span><span class="sxs-lookup"><span data-stu-id="05b49-181">**To support both near and far interactions, it is recommended to use Interactable's *OnClick* event.**</span></span>

<img src="../images/button/MRTK_Button_HowTo_PressableButton.png" width="450"  alt="How to use Pressable Buttons">

## <a name="interaction-states"></a><span data-ttu-id="05b49-182">Stati di interazione</span><span class="sxs-lookup"><span data-stu-id="05b49-182">Interaction states</span></span>

<span data-ttu-id="05b49-183">Nello stato di inattività, il pannello anteriore del pulsante non è visibile.</span><span class="sxs-lookup"><span data-stu-id="05b49-183">In the idle state, the button's front plate is not visible.</span></span> <span data-ttu-id="05b49-184">Quando un dito si avvicina o un cursore dall'input dello sguardo fisso si rivolge alla superficie, il bordo incandescente della superficie diventa visibile.</span><span class="sxs-lookup"><span data-stu-id="05b49-184">As a finger approaches or a cursor from gaze input targets the surface, the front plate's glowing border becomes visible.</span></span> <span data-ttu-id="05b49-185">È disponibile un'evidenziazione aggiuntiva della posizione della punta del dito sulla superficie della piana anteriore.</span><span class="sxs-lookup"><span data-stu-id="05b49-185">There is additional highlighting of the fingertip position on the front plate surface.</span></span> <span data-ttu-id="05b49-186">Quando viene premuto con un dito, il piano anteriore si sposta con la punta del dito.</span><span class="sxs-lookup"><span data-stu-id="05b49-186">When pushed with a finger, the front plate moves with the fingertip.</span></span> <span data-ttu-id="05b49-187">Quando la punta del dito tocca la superficie della lastra anteriore, mostra un effetto di pulsazione sottile per fornire un feedback visivo del punto di tocco.</span><span class="sxs-lookup"><span data-stu-id="05b49-187">When the fingertip touches the surface of the front plate, it shows a subtle pulse effect to give visual feedback of the touch point.</span></span>

<span data-ttu-id="05b49-188">In HoloLens 2 di tipo shell, sono disponibili molti suggerimenti visivi e suggerimenti per aumentare la fiducia dell'utente nell'interazione.</span><span class="sxs-lookup"><span data-stu-id="05b49-188">In HoloLens 2 shell-style button, there are many visual cues and affordances to increase the user's confidence on interaction.</span></span>

|  ![Luce di prossimità](../images/button/ux_button_affordance_proximitylight.jpg) | ![Evidenziazione dello stato attivo](../images/button/ux_button_affordance_focushighlight.jpg)  | ![Compressione della compressa](../images/button/ux_button_affordance_compression.jpg) | ![Pulse on trigger](../images/button/ux_button_affordance_pulse.jpg) |
|:--- | :--- | :--- | :--- |
| <span data-ttu-id="05b49-193">Luce di prossimità</span><span class="sxs-lookup"><span data-stu-id="05b49-193">Proximity light</span></span> | <span data-ttu-id="05b49-194">Evidenziazione dello stato attivo</span><span class="sxs-lookup"><span data-stu-id="05b49-194">Focus highlight</span></span> | <span data-ttu-id="05b49-195">Compressione della compressa</span><span class="sxs-lookup"><span data-stu-id="05b49-195">Compressing cage</span></span> | <span data-ttu-id="05b49-196">Pulse on trigger</span><span class="sxs-lookup"><span data-stu-id="05b49-196">Pulse on trigger</span></span> |

<span data-ttu-id="05b49-197">L'effetto di pulsazione sottile viene attivato dal pulsante a pressione, che cerca *proximityLight(s)* che si trovano sul puntatore che interagisce attualmente.</span><span class="sxs-lookup"><span data-stu-id="05b49-197">The subtle pulse effect is triggered by the pressable button, which looks for *ProximityLight(s)* that live on the currently interacting pointer.</span></span> <span data-ttu-id="05b49-198">Se vengono trovate luci di prossimità, viene chiamato il metodo , che aggiunge automaticamente un'animazione ai parametri `ProximityLight.Pulse` dello shader per visualizzare un'animazione.</span><span class="sxs-lookup"><span data-stu-id="05b49-198">If any proximity lights are found, the `ProximityLight.Pulse` method is called, which automatically animates shader parameters to display a pulse.</span></span>

## <a name="inspector-properties"></a><span data-ttu-id="05b49-199">Proprietà del controllo</span><span class="sxs-lookup"><span data-stu-id="05b49-199">Inspector properties</span></span>

![Struttura dei pulsanti](../images/button/MRTK_Button_Structure.png)

<span data-ttu-id="05b49-201">**Box Collisore** 
 `Box Collider` per la barra anteriore del pulsante.</span><span class="sxs-lookup"><span data-stu-id="05b49-201">**Box Collider**
`Box Collider` for the button's front plate.</span></span>

<span data-ttu-id="05b49-202">**Pulsante a pressione** Logica per lo spostamento del pulsante con l'interazione con la pressione della mano.</span><span class="sxs-lookup"><span data-stu-id="05b49-202">**Pressable Button** The logic for the button movement with hand press interaction.</span></span>

<span data-ttu-id="05b49-203">**Router eventi di stampa fisica** Questo script invia eventi dall'interazione con la pressione manuale a [Interactable.](interactable.md)</span><span class="sxs-lookup"><span data-stu-id="05b49-203">**Physical Press Event Router** This script sends events from hand press interaction to [Interactable](interactable.md).</span></span>

<span data-ttu-id="05b49-204">**Interagibile** 
 [L'interazione](interactable.md) gestisce vari tipi di stati ed eventi di interazione.</span><span class="sxs-lookup"><span data-stu-id="05b49-204">**Interactable**
[Interactable](interactable.md) handles various types of interaction states and events.</span></span> <span data-ttu-id="05b49-205">HoloLens lo sguardo, il movimento e l'input vocale e l'input del controller di movimento vr immersivo vengono gestiti direttamente da questo script.</span><span class="sxs-lookup"><span data-stu-id="05b49-205">HoloLens gaze, gesture, and voice input and immersive headset motion controller input are directly handled by this script.</span></span>

<span data-ttu-id="05b49-206">**Origine audio** Origine audio Unity per le clip di feedback audio.</span><span class="sxs-lookup"><span data-stu-id="05b49-206">**Audio Source** Unity audio source for the audio feedback clips.</span></span>

<span data-ttu-id="05b49-207">*NearInteractionTouchable.cs* Obbligatorio per rendere toccabile qualsiasi oggetto con input manuale articolato.</span><span class="sxs-lookup"><span data-stu-id="05b49-207">*NearInteractionTouchable.cs* Required to make any object touchable with articulated hand input.</span></span>

## <a name="prefab-layout"></a><span data-ttu-id="05b49-208">Layout prefab</span><span class="sxs-lookup"><span data-stu-id="05b49-208">Prefab layout</span></span>

<span data-ttu-id="05b49-209">*L'oggetto ButtonContent* contiene la barra anteriore, l'etichetta di testo e l'icona.</span><span class="sxs-lookup"><span data-stu-id="05b49-209">The *ButtonContent* object contains front plate, text label and icon.</span></span> <span data-ttu-id="05b49-210">*FrontPlate* risponde alla prossimità della punta dell'indice usando Button_Box *shader.*</span><span class="sxs-lookup"><span data-stu-id="05b49-210">The *FrontPlate* responds to the proximity of the index fingertip using the *Button_Box* shader.</span></span> <span data-ttu-id="05b49-211">Mostra bordi incandescenti, luce di prossimità e un effetto di impulso sul tocco.</span><span class="sxs-lookup"><span data-stu-id="05b49-211">It shows glowing borders, proximity light, and a pulse effect on touch.</span></span> <span data-ttu-id="05b49-212">L'etichetta di testo viene fatta con TextMesh Pro.</span><span class="sxs-lookup"><span data-stu-id="05b49-212">The text label is made with TextMesh Pro.</span></span> <span data-ttu-id="05b49-213">*La visibilità di SeeItSayItLabel* è controllata dal tema di [Interactable.](interactable.md)</span><span class="sxs-lookup"><span data-stu-id="05b49-213">*SeeItSayItLabel*'s visibility is controlled by [Interactable](interactable.md)'s theme.</span></span>

![Layout dei pulsanti](../images/button/MRTK_Button_Layout.png)

## <a name="how-to-change-the-icon-and-text"></a><span data-ttu-id="05b49-215">Come modificare l'icona e il testo</span><span class="sxs-lookup"><span data-stu-id="05b49-215">How to change the icon and text</span></span>

<span data-ttu-id="05b49-216">I pulsanti MRTK usano un componente per facilitare la modifica dell'icona, del testo e `ButtonConfigHelper` dell'etichetta del pulsante.</span><span class="sxs-lookup"><span data-stu-id="05b49-216">MRTK buttons use a `ButtonConfigHelper` component to assist you in changing the button's icon, text and label.</span></span> <span data-ttu-id="05b49-217">Si noti che alcuni campi potrebbero essere assenti se gli elementi non sono presenti nel pulsante selezionato.</span><span class="sxs-lookup"><span data-stu-id="05b49-217">(Note that some fields may be absent if elements are not present on the selected button.)</span></span>

![Helper di configurazione dei pulsanti](../images/button/MRTK_Button_Config_Helper.png)

### <a name="creating-and-modifying-icon-sets"></a><span data-ttu-id="05b49-219">Creazione e modifica di set di icone</span><span class="sxs-lookup"><span data-stu-id="05b49-219">Creating and Modifying Icon Sets</span></span>

<span data-ttu-id="05b49-220">Un **set di** icone è un set condiviso di asset icona usati dal `ButtonConfigHelper` componente.</span><span class="sxs-lookup"><span data-stu-id="05b49-220">An **Icon Set** is a shared set of icon assets used by the `ButtonConfigHelper` component.</span></span> <span data-ttu-id="05b49-221">Sono supportati *tre stili* icona.</span><span class="sxs-lookup"><span data-stu-id="05b49-221">Three icon *styles* are supported.</span></span>

* <span data-ttu-id="05b49-222">**Il rendering** delle icone quadre viene eseguito su un quad usando `MeshRenderer` un oggetto .</span><span class="sxs-lookup"><span data-stu-id="05b49-222">**Quad** icons are rendered on a quad using a `MeshRenderer`.</span></span> <span data-ttu-id="05b49-223">Questo è lo stile predefinito dell'icona.</span><span class="sxs-lookup"><span data-stu-id="05b49-223">This is the default icon style.</span></span>
* <span data-ttu-id="05b49-224">**Il rendering delle icone sprite** viene eseguito usando `SpriteRenderer` un oggetto .</span><span class="sxs-lookup"><span data-stu-id="05b49-224">**Sprite** icons are rendered using a `SpriteRenderer`.</span></span> <span data-ttu-id="05b49-225">Ciò è utile se si preferisce importare le icone come foglio sprite o se si vuole che gli asset delle icone siano condivisi con i componenti dell'interfaccia utente di Unity.</span><span class="sxs-lookup"><span data-stu-id="05b49-225">This is useful if you prefer to import your icons as a sprite sheet, or if you want your icon assets to be shared with Unity UI components.</span></span> <span data-ttu-id="05b49-226">Per usare questo stile è necessario installare il pacchetto Sprite Editor **(Windows -> Gestione pacchetti -> 2D Sprite)**</span><span class="sxs-lookup"><span data-stu-id="05b49-226">To use this style you will need to install the Sprite Editor package **(Windows -> Package Manager -> 2D Sprite)**</span></span>
* <span data-ttu-id="05b49-227">**Il rendering** delle icone char viene eseguito usando un `TextMeshPro` componente .</span><span class="sxs-lookup"><span data-stu-id="05b49-227">**Char** icons are rendered using a `TextMeshPro` component.</span></span> <span data-ttu-id="05b49-228">Ciò è utile se si preferisce usare un tipo di carattere icona.</span><span class="sxs-lookup"><span data-stu-id="05b49-228">This is useful if you prefer to use an icon font.</span></span> <span data-ttu-id="05b49-229">Per usare il tipo HoloLens tipo di carattere dell'icona, è necessario creare un `TextMeshPro` asset del tipo di carattere.</span><span class="sxs-lookup"><span data-stu-id="05b49-229">To use the HoloLens icon font you will need to create a `TextMeshPro` font asset.</span></span>

<span data-ttu-id="05b49-230">Per modificare lo stile utilizzato  dal pulsante, espandere l'elenco a discesa Icone nell'elenco a discesa ButtonConfigHelper e selezionare dall'elenco a discesa *Stile* icona.</span><span class="sxs-lookup"><span data-stu-id="05b49-230">To change which style your button uses, expand the *Icons* dropdown in the ButtonConfigHelper and select from the *Icon Style* dropdown.</span></span>

<span data-ttu-id="05b49-231">È possibile creare un nuovo set di icone pulsante con il menu asset: Creare > **realtà mista Toolkit > set di icone.**</span><span class="sxs-lookup"><span data-stu-id="05b49-231">You can create a new button icon set with the asset menu: **Create > Mixed Reality Toolkit > Icon Set.**</span></span> <span data-ttu-id="05b49-232">Per aggiungere icone quad e sprite, è sufficiente trascinarle nelle rispettive matrici.</span><span class="sxs-lookup"><span data-stu-id="05b49-232">To add quad and sprite icons, simply drag them into their respective arrays.</span></span> <span data-ttu-id="05b49-233">Per aggiungere icone Char, è prima necessario creare e assegnare un asset del tipo di carattere.</span><span class="sxs-lookup"><span data-stu-id="05b49-233">To add Char icons, you must first create and assign a font asset.</span></span>

<span data-ttu-id="05b49-234">In MRTK 2.4 e oltre è consigliabile spostare trame di icone personalizzate in un oggetto IconSet.</span><span class="sxs-lookup"><span data-stu-id="05b49-234">In MRTK 2.4 and beyond, we recommend custom icon textures be moved into an IconSet.</span></span>
<span data-ttu-id="05b49-235">Per aggiornare gli asset in tutti i pulsanti di un progetto al nuovo formato consigliato, usare ButtonConfigHelperMigrationHandler.</span><span class="sxs-lookup"><span data-stu-id="05b49-235">To upgrade the assets on all buttons in a project to the new recommended format, use the ButtonConfigHelperMigrationHandler.</span></span>
<span data-ttu-id="05b49-236">(Mixed Reality Toolkit -> Utilities -> Migration Window -> Migration Handler Selection -> Microsoft.MixedReality. Toolkit. Utilities.ButtonConfigHelperMigrationHandler)</span><span class="sxs-lookup"><span data-stu-id="05b49-236">(Mixed Reality Toolkit -> Utilities -> Migration Window -> Migration Handler Selection -> Microsoft.MixedReality.Toolkit.Utilities.ButtonConfigHelperMigrationHandler)</span></span>

<span data-ttu-id="05b49-237">Importazione del pacchetto Microsoft.MixedRealityToolkit.Unity.Tools necessario per aggiornare i pulsanti.</span><span class="sxs-lookup"><span data-stu-id="05b49-237">Importing the Microsoft.MixedRealityToolkit.Unity.Tools package required to upgrade the buttons.</span></span>

![Finestra di dialogo Aggiorna](https://user-images.githubusercontent.com/39840334/82096923-bd28bf80-96b6-11ea-93a9-ceafcb822242.png)

<span data-ttu-id="05b49-239">Se non viene trovata un'icona nel set di icone predefinito durante la migrazione, verrà creato un set di icone personalizzato in MixedRealityToolkit.Generated/CustomIconSets.</span><span class="sxs-lookup"><span data-stu-id="05b49-239">If an icon is not found in the default icon set during migration, a custom icon set will be created in MixedRealityToolkit.Generated/CustomIconSets.</span></span> <span data-ttu-id="05b49-240">Una finestra di dialogo indicherà che l'operazione è stata eseguita.</span><span class="sxs-lookup"><span data-stu-id="05b49-240">A dialog will indicate that this has taken place.</span></span>

![Notifica dell'icona personalizzata](https://user-images.githubusercontent.com/9789716/82093856-c57dfc00-96b0-11ea-83ab-4df57446d661.PNG)

### <a name="creating-a-hololens-icon-font-asset"></a><span data-ttu-id="05b49-242">Creazione di un asset HoloLens carattere dell'icona</span><span class="sxs-lookup"><span data-stu-id="05b49-242">Creating a HoloLens Icon Font Asset</span></span>

<span data-ttu-id="05b49-243">Per prima cosa, importare il tipo di carattere dell'icona in Unity.</span><span class="sxs-lookup"><span data-stu-id="05b49-243">First, import the icon font into Unity.</span></span> <span data-ttu-id="05b49-244">Nei Windows è possibile trovare il tipo di carattere HoloLens predefinito in *Windows/Fonts/holomdl2.ttf.*</span><span class="sxs-lookup"><span data-stu-id="05b49-244">On Windows machines you can find the default HoloLens font in *Windows/Fonts/holomdl2.ttf.*</span></span> <span data-ttu-id="05b49-245">Copiare e incollare questo file nella cartella Assets.</span><span class="sxs-lookup"><span data-stu-id="05b49-245">Copy and paste this file into your Assets folder.</span></span>

<span data-ttu-id="05b49-246">Aprire quindi TextMeshPro Font Asset Creator tramite **Window > TextMeshPro > Font Asset Creator.Next,** open the TextMeshPro Font Asset Creator via Window > TextMeshPro > Font Asset Creator.</span><span class="sxs-lookup"><span data-stu-id="05b49-246">Next, open the TextMeshPro Font Asset Creator via **Window > TextMeshPro > Font Asset Creator.**</span></span> <span data-ttu-id="05b49-247">Ecco le impostazioni consigliate per la generazione di un at atlas HoloLens tipo di carattere.</span><span class="sxs-lookup"><span data-stu-id="05b49-247">Here are the recommended settings for generating a HoloLens font atlas.</span></span> <span data-ttu-id="05b49-248">Per includere tutte le icone, incollare l'intervallo Unicode seguente nel *campo Sequenza di* caratteri:</span><span class="sxs-lookup"><span data-stu-id="05b49-248">To include all icons, paste the following Unicode range into the *Character Sequence* field:</span></span>

```c#
E700-E702,E706,E70D-E70E,E710-E714,E718,E71A,E71D-E71E,E720,E722,E728,E72A-E72E,E736,E738,E73F,E74A-E74B,E74D,E74F-E752,E760-E761,E765,E767-E769,E76B-E76C,E770,E772,E774,E777,E779-E77B,E782-E783,E785-E786,E799,E7A9-E7AB,E7AF-E7B1,E7B4,E7C8,E7E8-E7E9,E7FC,E80F,E821,E83F,E850-E859,E872-E874,E894-E895,E8A7,E8B2,E8B7,E8B9,E8D5,E8EC,E8FB,E909,E91B,E92C,E942,E95B,E992-E995,E9E9-E9EA,EA37,EA40,EA4A,EA55,EA96,EB51-EB52,EB65,EB9D-EBB5,EBCB-EBCC,EBCF-EBD3,EC03,EC19,EC3F,EC7A,EC8E-EC98,ECA2,ECD8-ECDA,ECE0,ECE7-ECEB,ED17,EE93,EFA9,F114-F120,F132,F181,F183-F186
```

![Creazione del pulsante 1](../images/button/MRTK_Font_Asset_Creation_1.png)

<span data-ttu-id="05b49-250">Dopo aver generato l'asset del tipo di carattere, salvarlo nel progetto e assegnarlo al campo Carattere icona del set *di* icone.</span><span class="sxs-lookup"><span data-stu-id="05b49-250">Once the font asset is generated, save it to your project and assign it to your Icon Set's *Char Icon Font* field.</span></span> <span data-ttu-id="05b49-251">*L'elenco a discesa* Icone disponibili verrà ora popolato.</span><span class="sxs-lookup"><span data-stu-id="05b49-251">The *Available Icons* dropdown will now be populated.</span></span> <span data-ttu-id="05b49-252">Per rendere disponibile un'icona per l'uso da parte di un pulsante, fare clic su di essa.</span><span class="sxs-lookup"><span data-stu-id="05b49-252">To make an icon available for use by a button, click it.</span></span> <span data-ttu-id="05b49-253">Verrà aggiunto all'elenco a discesa *Icone* selezionate e verrà ora visualizzato in È possibile assegnare all'icona `ButtonConfigHelper.` un tag.</span><span class="sxs-lookup"><span data-stu-id="05b49-253">It will be added to the *Selected Icons* dropdown and will now show up in the `ButtonConfigHelper.` You can optionally give the icon a tag.</span></span> <span data-ttu-id="05b49-254">In questo modo è possibile impostare l'icona in fase di esecuzione.</span><span class="sxs-lookup"><span data-stu-id="05b49-254">This enables setting the icon at runtime.</span></span>

![Creazione del pulsante 3](../images/button/MRTK_Font_Asset_Creation_3.png)

![Creazione del pulsante 2](../images/button/MRTK_Font_Asset_Creation_2.png)

```c#
public void SetButtonToAdjust()
{
    ButtonConfigHelper buttonConfigHelper = gameObject.GetComponent<ButtonConfigHelper>();
    buttonConfigHelper.SetCharIconByName("AppBarAdjust");
}
```

<span data-ttu-id="05b49-257">Per usare il set di icone, selezionare un pulsante, espandere l'elenco a discesa Icone in `ButtonConfigHelper` e assegnarlo al *campo Set di* icone.</span><span class="sxs-lookup"><span data-stu-id="05b49-257">To use your Icon Set select a button, expand the Icons dropdown in the `ButtonConfigHelper` and assign it to the *Icon Set* field.</span></span>

![Set di icone dei pulsanti](../images/button/MRTK_Button_Icon_Set_Assign.png)

## <a name="how-to-change-the-size-of-a-button"></a><span data-ttu-id="05b49-259">Come modificare le dimensioni di un pulsante</span><span class="sxs-lookup"><span data-stu-id="05b49-259">How to change the size of a button</span></span>

<span data-ttu-id="05b49-260">HoloLens 2 dimensioni del pulsante in stile shell è di 32 x 32 mm.</span><span class="sxs-lookup"><span data-stu-id="05b49-260">HoloLens 2's shell-style button's size is 32x32mm.</span></span> <span data-ttu-id="05b49-261">Per personalizzare la dimensione, modificare le dimensioni di questi oggetti nel prefab del pulsante:</span><span class="sxs-lookup"><span data-stu-id="05b49-261">To customize the dimension, change the size of these objects in the button prefab:</span></span>

1. <span data-ttu-id="05b49-262">**FrontPlate**</span><span class="sxs-lookup"><span data-stu-id="05b49-262">**FrontPlate**</span></span>
2. <span data-ttu-id="05b49-263">**Quad** in BackPlate</span><span class="sxs-lookup"><span data-stu-id="05b49-263">**Quad** under BackPlate</span></span>
3. <span data-ttu-id="05b49-264">**Box Collisore** nella radice</span><span class="sxs-lookup"><span data-stu-id="05b49-264">**Box Collider** on the root</span></span>

<span data-ttu-id="05b49-265">Fare quindi **clic sul pulsante Correggi** limiti nello script NearInteractionTouchable che si trova nella radice del pulsante.</span><span class="sxs-lookup"><span data-stu-id="05b49-265">Then, click **Fix Bounds** button in the NearInteractionTouchable script which is in the root of the button.</span></span>

<span data-ttu-id="05b49-266">Aggiornare le dimensioni della personalizzazione di FrontPlate ![ Button Size 1](../images/button/MRTK_Button_SizeCustomization1.png)</span><span class="sxs-lookup"><span data-stu-id="05b49-266">Update the size of the FrontPlate ![Button Size customization 1](../images/button/MRTK_Button_SizeCustomization1.png)</span></span>

<span data-ttu-id="05b49-267">Aggiornare le dimensioni della personalizzazione di Quad ![ Button Size 2](../images/button/MRTK_Button_SizeCustomization2.png)</span><span class="sxs-lookup"><span data-stu-id="05b49-267">Update the size of the Quad ![Button Size customization 2](../images/button/MRTK_Button_SizeCustomization2.png)</span></span>

<span data-ttu-id="05b49-268">Aggiornare le dimensioni della personalizzazione di Box Collider ![ Button Size 3](../images/button/MRTK_Button_SizeCustomization3.png)</span><span class="sxs-lookup"><span data-stu-id="05b49-268">Update the size of the Box Collider ![Button Size customization 3](../images/button/MRTK_Button_SizeCustomization3.png)</span></span>

<span data-ttu-id="05b49-269">Fare clic su "Correggi limiti" ![ Personalizzazione dimensioni pulsante 4](../images/button/MRTK_Button_SizeCustomization4.png)</span><span class="sxs-lookup"><span data-stu-id="05b49-269">Click 'Fix Bounds' ![Button Size customization 4](../images/button/MRTK_Button_SizeCustomization4.png)</span></span>

## <a name="voice-command-see-it-say-it"></a><span data-ttu-id="05b49-270">Comando vocale ('see-it, say-it')</span><span class="sxs-lookup"><span data-stu-id="05b49-270">Voice command ('see-it, say-it')</span></span>

<span data-ttu-id="05b49-271">**Gestore input vocale** Lo script [Interactable](interactable.md) in Pressable Button implementa già `IMixedRealitySpeechHandler` .</span><span class="sxs-lookup"><span data-stu-id="05b49-271">**Speech Input Handler** The [Interactable](interactable.md) script in Pressable Button already implements `IMixedRealitySpeechHandler`.</span></span> <span data-ttu-id="05b49-272">Qui è possibile impostare una parola chiave di comando vocale.</span><span class="sxs-lookup"><span data-stu-id="05b49-272">A voice command keyword can be set here.</span></span>

<img src="../images/button/MRTK_Button_Speech1.png" width="450" alt="Buttons Speech">

<span data-ttu-id="05b49-273">**Profilo di input vocale** Inoltre, è necessario registrare la parola chiave del comando vocale nel profilo *comandi vocali globale.*</span><span class="sxs-lookup"><span data-stu-id="05b49-273">**Speech Input Profile** Additionally, you need to register the voice command keyword in the global *Speech Commands Profile*.</span></span>

<img src="../images/button/MRTK_Button_Speech2.png" width="450" alt="Button speech 2">

<span data-ttu-id="05b49-274">**Etichetta See-it, Say-it** Il prefab del pulsante selezionabile ha un segnaposto TextMesh Pro'etichetta sotto *l'oggetto SeeItSayItLabel.*</span><span class="sxs-lookup"><span data-stu-id="05b49-274">**See-it, Say-it label** The pressable button prefab has a placeholder TextMesh Pro label under the *SeeItSayItLabel* object.</span></span> <span data-ttu-id="05b49-275">È possibile usare questa etichetta per comunicare all'utente la parola chiave del comando vocale per il pulsante.</span><span class="sxs-lookup"><span data-stu-id="05b49-275">You can use this label to communicate the voice command keyword for the button to the user.</span></span>

<img src="../images/button/MRTK_Button_Speech3.png" width="450" alt="Button Speech 3">

## <a name="how-to-make-a-button-from-scratch"></a><span data-ttu-id="05b49-276">Come creare un pulsante da zero</span><span class="sxs-lookup"><span data-stu-id="05b49-276">How to make a button from scratch</span></span>

<span data-ttu-id="05b49-277">Gli esempi di questi pulsanti sono disponibili nella **scena PressableButtonExample.**</span><span class="sxs-lookup"><span data-stu-id="05b49-277">You can find the examples of these buttons in the **PressableButtonExample** scene.</span></span>

<img src="../images/button/MRTK_PressableButtonCube0.png" alt="Pressable button cube 0">

### <a name="1-creating-a-pressable-button-with-cube-near-interaction-only"></a><span data-ttu-id="05b49-278">1. Creazione di un pulsante pressabile con cubo (solo vicino all'interazione)</span><span class="sxs-lookup"><span data-stu-id="05b49-278">1. Creating a pressable button with cube (near interaction only)</span></span>

1. <span data-ttu-id="05b49-279">Creare un cubo Unity (GameObject > 3D Object > Cube)</span><span class="sxs-lookup"><span data-stu-id="05b49-279">Create a Unity Cube (GameObject > 3D Object > Cube)</span></span>
2. <span data-ttu-id="05b49-280">Aggiungere `PressableButton.cs` uno script</span><span class="sxs-lookup"><span data-stu-id="05b49-280">Add `PressableButton.cs` script</span></span>
3. <span data-ttu-id="05b49-281">Aggiungere `NearInteractionTouchable.cs` uno script</span><span class="sxs-lookup"><span data-stu-id="05b49-281">Add `NearInteractionTouchable.cs` script</span></span>

<span data-ttu-id="05b49-282">Nel pannello `PressableButton` Inspector (Controllo) assegnare l'oggetto cubo agli **oggetti visivi pulsante di spostamento**.</span><span class="sxs-lookup"><span data-stu-id="05b49-282">In the `PressableButton`'s Inspector panel, assign the cube object to the **Moving Button Visuals**.</span></span>

<img src="../images/button/MRTK_PressableButtonCube3.png" width="450" alt="pressable button cube 3">

<span data-ttu-id="05b49-283">Quando si seleziona il cubo, sull'oggetto verranno visualizzati più livelli colorati.</span><span class="sxs-lookup"><span data-stu-id="05b49-283">When you select the cube, you will see multiple colored layers on the object.</span></span> <span data-ttu-id="05b49-284">In questo modo vengono visualizzati i valori della distanza **in Press Impostazioni**.</span><span class="sxs-lookup"><span data-stu-id="05b49-284">This visualizes the distance values under **Press Settings**.</span></span> <span data-ttu-id="05b49-285">Usando gli handle, è possibile configurare quando iniziare a premere (spostare l'oggetto) e quando attivare l'evento.</span><span class="sxs-lookup"><span data-stu-id="05b49-285">Using the handles, you can configure when to start press (move the object) and when to trigger event.</span></span>

<img src="../images/button/MRTK_PressableButtonCube1.jpg" width="450" alt="Pressable Buton cube 1">

<img src="../images/button/MRTK_PressableButtonCube2.png" width="450" alt="Pressable button cube 2">

<span data-ttu-id="05b49-286">Quando si preme il pulsante, questo si sposterà e genererà gli eventi adeguati esposti nello script, ad esempio `PressableButton.cs` TouchBegin(), TouchEnd(), ButtonPressed(), ButtonReleased().</span><span class="sxs-lookup"><span data-stu-id="05b49-286">When you press the button, it will move and generate proper events exposed in the `PressableButton.cs` script such as TouchBegin(), TouchEnd(), ButtonPressed(), ButtonReleased().</span></span>

<img src="../images/button/MRTK_PressableButtonCubeRun1.jpg" alt="Pressable button cube run 1">

#### <a name="troubleshooting"></a><span data-ttu-id="05b49-287">Risoluzione dei problemi</span><span class="sxs-lookup"><span data-stu-id="05b49-287">Troubleshooting</span></span>

<span data-ttu-id="05b49-288">Se il pulsante esegue una doppia pressione, assicurarsi che la proprietà Imponi push frontale sia attiva e che il piano **Start Push Distance** sia posizionato davanti al piano Near Interaction **Touchable.** </span><span class="sxs-lookup"><span data-stu-id="05b49-288">If your button is executing a double press, make sure the **Enforce Front Push** property is active and the **Start Push Distance** plane is placed in front of the **Near Interaction Touchable** plane.</span></span> <span data-ttu-id="05b49-289">Il **piano Near Interaction Touchable** è indicato dal piano blu posizionato davanti all'origine della freccia bianca nella gif seguente:</span><span class="sxs-lookup"><span data-stu-id="05b49-289">The **Near Interaction Touchable** plane is indicated by the blue plane placed in front of the origin of the white arrow in the gif below:</span></span>

![Componente script pulsante a pressione con la proprietà Imponi front push evidenziata](../images/button/MRTK_Button_Enforce_Push.png)

![Esempio animato di spostamento della distanza di push iniziale davanti al piano toccabile vicino all'interazione](../images/button/MRTK_Button_Front_Touch.gif)

### <a name="2-adding-visual-feedback-to-the-basic-cube-button"></a><span data-ttu-id="05b49-292">2. Aggiunta di commenti e suggerimenti visivi al pulsante cubo di base</span><span class="sxs-lookup"><span data-stu-id="05b49-292">2. Adding visual feedback to the basic cube button</span></span>

<span data-ttu-id="05b49-293">MrTK Standard Shader offre varie funzionalità che semplificano l'aggiunta di commenti e suggerimenti visivi.</span><span class="sxs-lookup"><span data-stu-id="05b49-293">MRTK Standard Shader provides various features that makes it easy to add visual feedback.</span></span> <span data-ttu-id="05b49-294">Creare un materiale e selezionare shader `Mixed Reality Toolkit/Standard` .</span><span class="sxs-lookup"><span data-stu-id="05b49-294">Create a material and select shader `Mixed Reality Toolkit/Standard`.</span></span> <span data-ttu-id="05b49-295">Oppure è possibile usare o duplicare uno dei materiali esistenti in `/SDK/StandardAssets/Materials/` che usa MRTK Standard Shader.</span><span class="sxs-lookup"><span data-stu-id="05b49-295">Or you can use or duplicate one of the existing materials under `/SDK/StandardAssets/Materials/` that uses MRTK Standard Shader.</span></span>

<img src="../images/button/MRTK_PressableButtonCube4.png" width="450" alt="Pressable button cube 4">

<span data-ttu-id="05b49-296">Selezionare `Hover Light` e in Fluent `Proximity Light` **opzioni**.</span><span class="sxs-lookup"><span data-stu-id="05b49-296">Check `Hover Light` and `Proximity Light` under **Fluent Options**.</span></span> <span data-ttu-id="05b49-297">Ciò consente un feedback visivo sia per le interazioni vicino alla mano (luce di prossimità) che per le interazioni con puntatore lontano (Luce del passaggio del mouse).</span><span class="sxs-lookup"><span data-stu-id="05b49-297">This enables visual feedback for both near hand(Proximity Light) and far pointer(Hover Light) interactions.</span></span>

<img src="../images/button/MRTK_PressableButtonCube5.png" width="450" alt="pressable button cube 5">

<img src="../images/button/MRTK_PressableButtonCubeRun2.jpg" alt="pressable button cube run 2">

### <a name="3-adding-audio-feedback-to-the-basic-cube-button"></a><span data-ttu-id="05b49-298">3. Aggiunta di commenti audio al pulsante cubo di base</span><span class="sxs-lookup"><span data-stu-id="05b49-298">3. Adding audio feedback to the basic cube button</span></span>

<span data-ttu-id="05b49-299">Poiché lo script espone eventi come `PressableButton.cs` TouchBegin(), TouchEnd(), ButtonPressed(), ButtonReleased(), è possibile assegnare facilmente commenti audio.</span><span class="sxs-lookup"><span data-stu-id="05b49-299">Since `PressableButton.cs` script exposes events such as TouchBegin(), TouchEnd(), ButtonPressed(), ButtonReleased(), we can easily assign audio feedback.</span></span> <span data-ttu-id="05b49-300">È sufficiente aggiungere Unity `Audio Source` all'oggetto cubo e quindi assegnare clip audio selezionando AudioSource.PlayOneShot().</span><span class="sxs-lookup"><span data-stu-id="05b49-300">Simply add Unity's `Audio Source` to the cube object then assign audio clips by selecting AudioSource.PlayOneShot().</span></span> <span data-ttu-id="05b49-301">È possibile usare MRTK_Select_Main e MRTK_Select_Secondary clip audio nella `/SDK/StandardAssets/Audio/` cartella .</span><span class="sxs-lookup"><span data-stu-id="05b49-301">You can use MRTK_Select_Main and MRTK_Select_Secondary audio clips under `/SDK/StandardAssets/Audio/` folder.</span></span>

<img src="../images/button/MRTK_PressableButtonCube7.png" width="450" alt="pressable button cube 7">

<img src="../images/button/MRTK_PressableButtonCube6.png" width="450" alt="Pressable Button Cube 6">

### <a name="4-adding-visual-states-and-handle-far-interaction-events"></a><span data-ttu-id="05b49-302">4. Aggiunta di stati di visualizzazione e gestione di eventi di interazione lontano</span><span class="sxs-lookup"><span data-stu-id="05b49-302">4. Adding visual states and handle far interaction events</span></span>

<span data-ttu-id="05b49-303">[Interactable](interactable.md) è uno script che semplifica la creazione di uno stato di visualizzazione per i vari tipi di interazioni di input.</span><span class="sxs-lookup"><span data-stu-id="05b49-303">[Interactable](interactable.md) is a script that makes it easy to create a visual state for the various types of input interactions.</span></span> <span data-ttu-id="05b49-304">Gestisce anche eventi di interazione lontano.</span><span class="sxs-lookup"><span data-stu-id="05b49-304">It also handles far interaction events.</span></span> <span data-ttu-id="05b49-305">Aggiungere `Interactable.cs` e trascinare l'oggetto cubo nel **campo Destinazione** in **Profili**.</span><span class="sxs-lookup"><span data-stu-id="05b49-305">Add `Interactable.cs` and drag and drop the cube object onto the **Target** field under **Profiles**.</span></span> <span data-ttu-id="05b49-306">Creare quindi un nuovo tema con un tipo **ScaleOffsetColorTheme.**</span><span class="sxs-lookup"><span data-stu-id="05b49-306">Then, create a new Theme with a type **ScaleOffsetColorTheme**.</span></span> <span data-ttu-id="05b49-307">In questo tema è possibile specificare il colore dell'oggetto per gli stati di interazione specifici, ad esempio **Stato attivo** e **Premuto.**</span><span class="sxs-lookup"><span data-stu-id="05b49-307">Under this theme, you can specify the color of the object for the specific interaction states, such as **Focus** and **Pressed**.</span></span> <span data-ttu-id="05b49-308">È anche possibile controllare Scale e Offset.</span><span class="sxs-lookup"><span data-stu-id="05b49-308">You can also control Scale and Offset, as well.</span></span> <span data-ttu-id="05b49-309">Selezionare **Easing e** impostare la durata per rendere uniforme la transizione visiva.</span><span class="sxs-lookup"><span data-stu-id="05b49-309">Check **Easing** and set duration to make the visual transition smooth.</span></span>

![Selezionare il tema del profilo](../images/button/mrtk_button_profiles.gif)

<span data-ttu-id="05b49-311">L'oggetto risponde sia alle interazioni lontano (raggio della mano o sguardo fisso) che alle interazioni near(hand).</span><span class="sxs-lookup"><span data-stu-id="05b49-311">You will see the object respond to both far (hand ray or gaze cursor) and near(hand) interactions.</span></span>

<img src="../images/button/MRTK_PressableButtonCubeRun3.jpg" alt="Pressable Button Cube Run 3">
<img src="../images/button/MRTK_PressableButtonCubeRun4.jpg" alt="Pressable Button Cube Run 4">

## <a name="custom-button-examples"></a><span data-ttu-id="05b49-312">Esempi di pulsanti personalizzati</span><span class="sxs-lookup"><span data-stu-id="05b49-312">Custom button examples</span></span>

<span data-ttu-id="05b49-313">Nella scena [HandInteractionExample](../example-scenes/hand-interaction-examples.md)vedere gli esempi di pulsanti piano e tondo che usano entrambi `PressableButton` .</span><span class="sxs-lookup"><span data-stu-id="05b49-313">In the [HandInteractionExample scene](../example-scenes/hand-interaction-examples.md), see the piano and round button examples which are both using `PressableButton`.</span></span>

<img src="../images/button/MRTK_Button_Custom1.png" width="450" alt="Pressable Custom1">

<img src="../images/button/MRTK_Button_Custom2.png" width="450" alt="Pressable Custom2">

<span data-ttu-id="05b49-314">A ogni chiave del piano sono `PressableButton` assegnati un e uno `NearInteractionTouchable` script.</span><span class="sxs-lookup"><span data-stu-id="05b49-314">Each piano key has a `PressableButton` and a `NearInteractionTouchable` script assigned.</span></span> <span data-ttu-id="05b49-315">È importante verificare che la *direzione in* avanti locale di `NearInteractionTouchable` sia corretta.</span><span class="sxs-lookup"><span data-stu-id="05b49-315">It is important to verify that the *Local Forward* direction of `NearInteractionTouchable` is correct.</span></span> <span data-ttu-id="05b49-316">È rappresentato da una freccia bianca nell'editor.</span><span class="sxs-lookup"><span data-stu-id="05b49-316">It is represented by a white arrow in the editor.</span></span> <span data-ttu-id="05b49-317">Assicurarsi che la freccia punti lontano dal lato anteriore del pulsante:</span><span class="sxs-lookup"><span data-stu-id="05b49-317">Make sure the arrow points away from the button's front face:</span></span>

<img src="../images/button/MRTK_Button_Custom3.png" width="450" alt="Pressable Custom3">

## <a name="see-also"></a><span data-ttu-id="05b49-318">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="05b49-318">See also</span></span>

* [<span data-ttu-id="05b49-319">Interagibile</span><span class="sxs-lookup"><span data-stu-id="05b49-319">Interactable</span></span>](interactable.md)
* [<span data-ttu-id="05b49-320">Temi visivi</span><span class="sxs-lookup"><span data-stu-id="05b49-320">Visual Themes</span></span>](visual-themes.md)

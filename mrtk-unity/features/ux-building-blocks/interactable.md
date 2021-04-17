---
title: Interagibile
description: Panoramica sul componente script interactable in MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, interagiscibile, eventi,
ms.openlocfilehash: f141a394ec9395e0a27cc964caeb66654fb6fe08
ms.sourcegitcommit: 47c402dc8e588817ce60229bf019170fa36f3045
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2021
ms.locfileid: "107581563"
---
# <a name="interactable"></a><span data-ttu-id="be98b-104">Interagibile</span><span class="sxs-lookup"><span data-stu-id="be98b-104">Interactable</span></span>

![Interagibile](../images/interactable/InteractableExamples.png)

<span data-ttu-id="be98b-106">Il [`Interactable`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) componente è un contenitore all-in-one per rendere qualsiasi oggetto facilmente *intervienibile* e reattivo all'input.</span><span class="sxs-lookup"><span data-stu-id="be98b-106">The [`Interactable`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) component is an all-in-one container to make any object easily *interactable* and responsive to input.</span></span> <span data-ttu-id="be98b-107">Interactable funge da catch-all per tutti i tipi di input, tra cui tocco, raggi della mano, voce e così via, e incanalare queste interazioni in eventi e risposte [del](visual-themes.md) tema visivo. [](#events)</span><span class="sxs-lookup"><span data-stu-id="be98b-107">Interactable acts as a catch-all for all types of input including touch, hand rays, speech etc and funnel these interactions into [events](#events) and [visual theme](visual-themes.md) responses.</span></span> <span data-ttu-id="be98b-108">Questo componente offre un modo semplice per creare pulsanti, modificare il colore degli oggetti con lo stato attivo e altro ancora.</span><span class="sxs-lookup"><span data-stu-id="be98b-108">This component provides an easy way to make buttons, change color on objects with focus, and more.</span></span>

## <a name="how-to-configure-interactable"></a><span data-ttu-id="be98b-109">Come configurare Interactable</span><span class="sxs-lookup"><span data-stu-id="be98b-109">How to configure Interactable</span></span>

<span data-ttu-id="be98b-110">Il componente consente tre sezioni principali di configurazione:</span><span class="sxs-lookup"><span data-stu-id="be98b-110">The component allows for three primary sections of configuration:</span></span>

1) [<span data-ttu-id="be98b-111">Configurazione di input generale</span><span class="sxs-lookup"><span data-stu-id="be98b-111">General input configuration</span></span>](#general-input-settings)
1) <span data-ttu-id="be98b-112">[Temi visivi destinati](visual-themes.md) a più GameObject</span><span class="sxs-lookup"><span data-stu-id="be98b-112">[Visual Themes](visual-themes.md) targeted against multiple GameObjects</span></span>
1) [<span data-ttu-id="be98b-113">Gestori eventi</span><span class="sxs-lookup"><span data-stu-id="be98b-113">Event handlers</span></span>](#events)

### <a name="general-input-settings"></a><span data-ttu-id="be98b-114">Impostazioni di input generali</span><span class="sxs-lookup"><span data-stu-id="be98b-114">General input settings</span></span>

![Impostazioni generali interagiscibili](../images/interactable/InputFeatures_short.png)

<span data-ttu-id="be98b-116">**Stati**</span><span class="sxs-lookup"><span data-stu-id="be98b-116">**States**</span></span>

<span data-ttu-id="be98b-117">*States* è un [parametro ScriptableObject](https://docs.unity3d.com/Manual/class-ScriptableObject.html) che definisce le fasi di interazione, ad esempio press o observed, per i profili [interagiscibili](#interactable-profiles) e i [temi visivi.](visual-themes.md)</span><span class="sxs-lookup"><span data-stu-id="be98b-117">*States* is a [ScriptableObject](https://docs.unity3d.com/Manual/class-ScriptableObject.html) parameter that defines the interactions phases, like press or observed, for [Interactable Profiles](#interactable-profiles) and [Visual Themes](visual-themes.md).</span></span>

<span data-ttu-id="be98b-118">**DefaultInteractableStates** (Assets/MRTK/SDK/Features/UX/Interactable/States/DefaultInteractableStates.asset) viene fornito con MRTK predefinito ed è  il parametro predefinito per i componenti interagiscibili.</span><span class="sxs-lookup"><span data-stu-id="be98b-118">The **DefaultInteractableStates** (Assets/MRTK/SDK/Features/UX/Interactable/States/DefaultInteractableStates.asset) ships with MRTK out-of-box and is the default parameter for *Interactable* components.</span></span>

![Esempio di ScriptableObject di stati nel controllo](../images/interactable/DefaultInteractableStates.png)

<span data-ttu-id="be98b-120">*L'asset DefaultInteractableStates* contiene quattro stati e usa l'implementazione [`InteractableStates`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableStates) del modello di stato.</span><span class="sxs-lookup"><span data-stu-id="be98b-120">The *DefaultInteractableStates* asset contains four states and utilizes the [`InteractableStates`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableStates) state model implementation.</span></span>

* <span data-ttu-id="be98b-121">**Impostazione** predefinita: non accade nulla, si tratta dello stato di base più isolato.</span><span class="sxs-lookup"><span data-stu-id="be98b-121">**Default**: Nothing is happening, this is the most isolated base state.</span></span>

* <span data-ttu-id="be98b-122">**Stato attivo:** l'oggetto viene puntato a .</span><span class="sxs-lookup"><span data-stu-id="be98b-122">**Focus**: The object is being pointed at.</span></span> <span data-ttu-id="be98b-123">Si tratta di un singolo stato, non sono attualmente impostati altri stati, ma il valore predefinito sarà il più alto.</span><span class="sxs-lookup"><span data-stu-id="be98b-123">This is a single state, no other states are currently set, but it will out rank Default.</span></span>

* <span data-ttu-id="be98b-124">**Premere**: l'oggetto viene puntato e viene premuto un pulsante o una mano.</span><span class="sxs-lookup"><span data-stu-id="be98b-124">**Press**: The object is being pointed at and a button or hand is pressing.</span></span> <span data-ttu-id="be98b-125">Lo stato Press out (Stato di pressione) classifica Default (Predefinito) e Focus (Stato attivo).</span><span class="sxs-lookup"><span data-stu-id="be98b-125">The Press state out ranks Default and Focus.</span></span> <span data-ttu-id="be98b-126">Questo stato verrà impostato anche come fallback alla pressione fisica.</span><span class="sxs-lookup"><span data-stu-id="be98b-126">This state will also get set as a fallback to Physical Press.</span></span>

* <span data-ttu-id="be98b-127">**Disabilitato:** il pulsante non deve essere interattivo e il feedback visivo invierà all'utente se per qualche motivo questo pulsante non è utilizzabile al momento.</span><span class="sxs-lookup"><span data-stu-id="be98b-127">**Disabled**: The button should not be interactive and visual feedback will let the user know if for some reason this button is not usable at this time.</span></span> <span data-ttu-id="be98b-128">In teoria, lo stato disabilitato può contenere tutti gli altri stati, ma quando l'opzione Abilitato è disattivata, lo stato Disabilitato non è attivo per tutti gli altri stati.</span><span class="sxs-lookup"><span data-stu-id="be98b-128">In theory, the disabled state could contain all other states, but when Enabled is turned off, the Disabled state trumps all other states.</span></span>

<span data-ttu-id="be98b-129">Un valore di bit (#) viene assegnato allo stato a seconda dell'ordine nell'elenco.</span><span class="sxs-lookup"><span data-stu-id="be98b-129">A bit value (#) is assigned to the state depending on the order in the list.</span></span>

> [!NOTE]
> <span data-ttu-id="be98b-130">È in genere consigliabile usare **DefaultInteractableStates** (Assets/MRTK/SDK/Features/UX/Interactable/States/DefaultInteractableStates.asset) durante la creazione di componenti *interattivi.*</span><span class="sxs-lookup"><span data-stu-id="be98b-130">It is generally recommended to utilize the **DefaultInteractableStates** (Assets/MRTK/SDK/Features/UX/Interactable/States/DefaultInteractableStates.asset) when creating *Interactable* components.</span></span>
>
> <span data-ttu-id="be98b-131">Tuttavia, sono disponibili 17 stati con interazione che possono essere usati per la guida dei temi, anche se alcuni sono destinati a essere guidati da altri componenti.</span><span class="sxs-lookup"><span data-stu-id="be98b-131">However, there are 17 Interactable states available that can be used to drive themes, though some are meant to be driven by other components.</span></span> <span data-ttu-id="be98b-132">Di seguito è riportato un elenco di quelli con funzionalità incorporate.</span><span class="sxs-lookup"><span data-stu-id="be98b-132">Here is a list of those with built-in functionality.</span></span>
>
> * <span data-ttu-id="be98b-133">Visitato: è stato fatto clic su Interactable.</span><span class="sxs-lookup"><span data-stu-id="be98b-133">Visited: the Interactable has been clicked.</span></span>
> * <span data-ttu-id="be98b-134">Attiva/Disattiva: il pulsante si trova in uno stato attivato/disattivato o l'indice dimensione è un numero dispari.</span><span class="sxs-lookup"><span data-stu-id="be98b-134">Toggled: The button is in a toggled state or Dimension index is an odd number.</span></span>
> * <span data-ttu-id="be98b-135">Movimento: la mano o il controller è stato premuto ed è stato spostato dalla posizione originale.</span><span class="sxs-lookup"><span data-stu-id="be98b-135">Gesture: The hand or controller was pressed and has moved from the original position.</span></span>
> * <span data-ttu-id="be98b-136">VoiceCommand: è stato usato un comando vocale per attivare Interactable.</span><span class="sxs-lookup"><span data-stu-id="be98b-136">VoiceCommand: A speech command was used to trigger the Interactable.</span></span>
> * <span data-ttu-id="be98b-137">PhysicalTouch: è attualmente rilevato un input tocco, usare [`NearInteractionTouchable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) per abilitare.</span><span class="sxs-lookup"><span data-stu-id="be98b-137">PhysicalTouch: A touch input is currently detected, use [`NearInteractionTouchable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) to enable.</span></span>
> * <span data-ttu-id="be98b-138">Afferra: una mano sta attualmente afferrando i limiti dell'oggetto, usare [`NearInteractionGrabbable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionGrabbable) per abilitare</span><span class="sxs-lookup"><span data-stu-id="be98b-138">Grab: A hand is currently grabbing in the bounds of the object, use [`NearInteractionGrabbable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionGrabbable) to enable</span></span>

<span data-ttu-id="be98b-139">**Enabled**</span><span class="sxs-lookup"><span data-stu-id="be98b-139">**Enabled**</span></span>

<span data-ttu-id="be98b-140">Attiva o disattiva l'attivazione di un oggetto Interactable.</span><span class="sxs-lookup"><span data-stu-id="be98b-140">Toggles whether an Interactable will start enabled or not.</span></span> <span data-ttu-id="be98b-141">Corrisponde a [`Interactable.IsEnabled`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.IsEnabled) nel codice.</span><span class="sxs-lookup"><span data-stu-id="be98b-141">This corresponds to the [`Interactable.IsEnabled`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.IsEnabled) in code.</span></span>

<span data-ttu-id="be98b-142">La *proprietà abilitata di un oggetto Interactable* è diversa dalla proprietà abilitata configurata tramite GameObject/Component ,ad esempio</span><span class="sxs-lookup"><span data-stu-id="be98b-142">An *Interactable's* enabled property is different than the enabled property configured via GameObject/Component (i.e</span></span> <span data-ttu-id="be98b-143">SetActive e così via).</span><span class="sxs-lookup"><span data-stu-id="be98b-143">SetActive etc).</span></span> <span data-ttu-id="be98b-144">La disabilitazione di GameObject o *Interactable* MonoBehaviour disabilita l'esecuzione di tutti gli elementi della classe, inclusi input, temi visivi, eventi e così via. La disabilitazione tramite [`Interactable.IsEnabled`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.IsEnabled) disabilita la maggior parte della gestione dell'input, reimpostando gli stati di input correlati.</span><span class="sxs-lookup"><span data-stu-id="be98b-144">Disabling the GameObject or *Interactable* MonoBehaviour will disable everything in the class from running including input, visual themes, events, etc. Disabling via [`Interactable.IsEnabled`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.IsEnabled) will disable most input handling, resetting related input states.</span></span> <span data-ttu-id="be98b-145">Tuttavia, la classe eseguirà comunque ogni frame e riceverà eventi di input che verranno ignorati.</span><span class="sxs-lookup"><span data-stu-id="be98b-145">However, the class will still run every frame and receive input events which will be ignored.</span></span> <span data-ttu-id="be98b-146">Ciò è utile per visualizzare l'oggetto Interactable in uno stato disabilitato che può essere eseguito tramite temi visivi.</span><span class="sxs-lookup"><span data-stu-id="be98b-146">This is useful for displaying the Interactable in a disabled state which can be done via Visual Themes.</span></span> <span data-ttu-id="be98b-147">Un esempio tipico è un pulsante di invio in attesa del completamento di tutti i campi di input necessari.</span><span class="sxs-lookup"><span data-stu-id="be98b-147">A typical example of this would be a submit button waiting for all the required input fields to be completed.</span></span>

<span data-ttu-id="be98b-148">**Azioni di input**</span><span class="sxs-lookup"><span data-stu-id="be98b-148">**Input Actions**</span></span>

<span data-ttu-id="be98b-149">Selezionare [l'azione di input](../input/input-actions.md) dal profilo di mapping della configurazione di input o del controller a cui deve reagire il componente *Interactable.*</span><span class="sxs-lookup"><span data-stu-id="be98b-149">Select the [input action](../input/input-actions.md) from the input configuration or controller mapping profile that the *Interactable* component should react to.</span></span>

<span data-ttu-id="be98b-150">Questa proprietà può essere configurata in fase di esecuzione nel codice tramite [`Interactable.InputAction`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.InputAction) .</span><span class="sxs-lookup"><span data-stu-id="be98b-150">This property can be configured at runtime in code via [`Interactable.InputAction`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.InputAction).</span></span>

<span data-ttu-id="be98b-151">**IsGlobal**</span><span class="sxs-lookup"><span data-stu-id="be98b-151">**IsGlobal**</span></span>

<span data-ttu-id="be98b-152">Se true, il componente verrà contrassegnato come listener di input globale per l'azione [di input selezionata.](../input/input-actions.md)</span><span class="sxs-lookup"><span data-stu-id="be98b-152">If true, this will mark the component as a global input listener for the selected [input action](../input/input-actions.md).</span></span> <span data-ttu-id="be98b-153">Il comportamento predefinito è false,  che limita l'input solo a questo collisore interactable/GameObject.</span><span class="sxs-lookup"><span data-stu-id="be98b-153">Default behavior is false which will restrict input to only this *Interactable* collider/GameObject.</span></span>

<span data-ttu-id="be98b-154">Questa proprietà può essere configurata in fase di esecuzione nel codice tramite [`Interactable.IsGlobal`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.IsGlobal) .</span><span class="sxs-lookup"><span data-stu-id="be98b-154">This property can be configured at runtime in code via [`Interactable.IsGlobal`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.IsGlobal).</span></span>

<span data-ttu-id="be98b-155">**Comando Voce**</span><span class="sxs-lookup"><span data-stu-id="be98b-155">**Speech Command**</span></span>

<span data-ttu-id="be98b-156">[Comando voce](../input/speech.md), dal profilo comandi vocali MRTK, per attivare un evento OnClick per l'interazione vocale.</span><span class="sxs-lookup"><span data-stu-id="be98b-156">[Speech command](../input/speech.md), from the MRTK Speech Commands Profile, to trigger an OnClick event for voice interaction.</span></span>

<span data-ttu-id="be98b-157">Questa proprietà può essere configurata in fase di esecuzione nel codice tramite [`Interactable.VoiceCommand`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.VoiceCommand) .</span><span class="sxs-lookup"><span data-stu-id="be98b-157">This property can be configured at runtime in code via [`Interactable.VoiceCommand`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.VoiceCommand).</span></span>

<span data-ttu-id="be98b-158">**Richiede lo stato attivo**</span><span class="sxs-lookup"><span data-stu-id="be98b-158">**Requires Focus**</span></span>

<span data-ttu-id="be98b-159">Se true, il comando vocale attiverà *l'oggetto Interactable* solo se e solo se ha già lo stato attivo da un puntatore.</span><span class="sxs-lookup"><span data-stu-id="be98b-159">If true, the voice command will only activate the *Interactable* if and only if it already has focus from a pointer.</span></span> <span data-ttu-id="be98b-160">Se false, *interactable* fungerà da listener globale per il comando vocale selezionato.</span><span class="sxs-lookup"><span data-stu-id="be98b-160">If false, then the *Interactable* will act as a global listener for the selected voice command.</span></span> <span data-ttu-id="be98b-161">Il comportamento predefinito è true, perché più listener vocali globali possono essere difficili da organizzare in una scena.</span><span class="sxs-lookup"><span data-stu-id="be98b-161">The default behavior is true, as multiple global speech listeners can be difficult to organize in a scene.</span></span>

<span data-ttu-id="be98b-162">Questa proprietà può essere configurata in fase di esecuzione nel codice tramite [`Interactable.VoiceRequiresFocus`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.VoiceRequiresFocus) .</span><span class="sxs-lookup"><span data-stu-id="be98b-162">This property can be configured at runtime in code via [`Interactable.VoiceRequiresFocus`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.VoiceRequiresFocus).</span></span>

<span data-ttu-id="be98b-163">**Modalità di selezione**</span><span class="sxs-lookup"><span data-stu-id="be98b-163">**Selection Mode**</span></span>

<span data-ttu-id="be98b-164">Questa proprietà definisce la logica di selezione.</span><span class="sxs-lookup"><span data-stu-id="be98b-164">This property defines the selection logic.</span></span> <span data-ttu-id="be98b-165">Quando si *fa clic* su un oggetto Interactable, esegue l'iterazione in un livello *dimensione* successivo.</span><span class="sxs-lookup"><span data-stu-id="be98b-165">When an *Interactable* is clicked, it iterates into a next *Dimension* level.</span></span> <span data-ttu-id="be98b-166">*Le* dimensioni sono simili alla classificazione e definiscono uno stato all'esterno degli input ,ad esempio</span><span class="sxs-lookup"><span data-stu-id="be98b-166">*Dimensions* is similar to rank and defines a state outside of inputs (i.e</span></span> <span data-ttu-id="be98b-167">stato attivo, premere e così via).</span><span class="sxs-lookup"><span data-stu-id="be98b-167">focus, press etc).</span></span> <span data-ttu-id="be98b-168">Sono utili per definire gli stati toggle o altri stati a più classifica associati a un pulsante.</span><span class="sxs-lookup"><span data-stu-id="be98b-168">They are useful for defining Toggle states or other multi-rank states associated with a button.</span></span> <span data-ttu-id="be98b-169">Il livello dimensione corrente viene monitorato da `Interactable.DimensionIndex` .</span><span class="sxs-lookup"><span data-stu-id="be98b-169">The current Dimension level is tracked by `Interactable.DimensionIndex`.</span></span>

<span data-ttu-id="be98b-170">Le modalità di selezione disponibili sono:</span><span class="sxs-lookup"><span data-stu-id="be98b-170">The selection modes available are:</span></span>

* <span data-ttu-id="be98b-171">**Pulsante**  -  *Dimensions* = 1, simple clickable *Interactable*</span><span class="sxs-lookup"><span data-stu-id="be98b-171">**Button** - *Dimensions* = 1, simple clickable *Interactable*</span></span>
* <span data-ttu-id="be98b-172">**Attiva/Disattiva**  -  *Dimensioni* = 2, *alternabile con* interazione tra *lo stato on* / *off*</span><span class="sxs-lookup"><span data-stu-id="be98b-172">**Toggle** - *Dimensions* = 2, *Interactable* alternates between *on*/*off* state</span></span>
* <span data-ttu-id="be98b-173">**Più dimensioni**  -  *Dimensioni* >= 3, ogni clic aumenta il livello di dimensione corrente + 1.</span><span class="sxs-lookup"><span data-stu-id="be98b-173">**Multi-dimension** - *Dimensions* >= 3, every click increases the current dimension level + 1.</span></span> <span data-ttu-id="be98b-174">Utile per definire lo stato di un pulsante in un elenco e così via.</span><span class="sxs-lookup"><span data-stu-id="be98b-174">Useful for defining a button state to a list, etc.</span></span>

<span data-ttu-id="be98b-175">*L'interazione* consente anche di definire più temi per ogni *dimensione.*</span><span class="sxs-lookup"><span data-stu-id="be98b-175">*Interactable* also allows for multiple Themes to be defined per *Dimension*.</span></span> <span data-ttu-id="be98b-176">Ad esempio, quando *SelectionMode=Toggle* è possibile applicare  un tema quando *interactable* è deselezionato e un altro tema applicato quando il componente è *selezionato.*</span><span class="sxs-lookup"><span data-stu-id="be98b-176">For example when *SelectionMode=Toggle*, one theme may be applied when the *Interactable* is *deselected* and another theme applied when the component is *selected*.</span></span>

<span data-ttu-id="be98b-177">È possibile eseguire query sulla modalità di selezione corrente in fase di esecuzione tramite [`Interactable.ButtonMode`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.ButtonMode) .</span><span class="sxs-lookup"><span data-stu-id="be98b-177">The current Selection Mode can be queried at runtime via [`Interactable.ButtonMode`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.ButtonMode).</span></span> <span data-ttu-id="be98b-178">L'aggiornamento della modalità in fase di esecuzione può essere ottenuto impostando la  [`Interactable.Dimensions`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.Dimensions) proprietà in modo che corrisponda alla funzionalità desiderata.</span><span class="sxs-lookup"><span data-stu-id="be98b-178">Updating the mode at runtime can be achieved by setting the  [`Interactable.Dimensions`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.Dimensions) property to match the desired functionality.</span></span> <span data-ttu-id="be98b-179">Inoltre, è possibile accedere alla dimensione corrente, utile per le modalità *Toggle* e *Multi-Dimension,* tramite [`Interactable.CurrentDimension`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.CurrentDimension) .</span><span class="sxs-lookup"><span data-stu-id="be98b-179">Furthermore, the current dimension, useful for *Toggle* and *Multi-Dimension* modes, can be accessed via [`Interactable.CurrentDimension`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.CurrentDimension).</span></span>

### <a name="interactable-profiles"></a><span data-ttu-id="be98b-180">Profili con interazione</span><span class="sxs-lookup"><span data-stu-id="be98b-180">Interactable profiles</span></span>

<span data-ttu-id="be98b-181">*I* profili sono elementi che creano una relazione tra un GameObject e un [tema visivo.](visual-themes.md)</span><span class="sxs-lookup"><span data-stu-id="be98b-181">*Profiles* are items that create a relationship between a GameObject and a [Visual Theme](visual-themes.md).</span></span> <span data-ttu-id="be98b-182">Il profilo definisce il contenuto che verrà modificato da un tema quando si verifica [una modifica dello stato.](#general-input-settings)</span><span class="sxs-lookup"><span data-stu-id="be98b-182">The profile defines what content will be manipulated by a theme when a [state change occurs](#general-input-settings).</span></span>

<span data-ttu-id="be98b-183">I temi funzionano molto come i materiali.</span><span class="sxs-lookup"><span data-stu-id="be98b-183">Themes work a lot like materials.</span></span> <span data-ttu-id="be98b-184">Sono oggetti che possono essere creati da script che contengono un elenco di proprietà che verranno assegnate a un oggetto in base allo stato corrente.</span><span class="sxs-lookup"><span data-stu-id="be98b-184">They are scriptable objects that contain a list of properties that will be assigned to an object based on the current state.</span></span> <span data-ttu-id="be98b-185">I temi sono anche riutilizzabili e possono essere assegnati a più *oggetti dell'esperienza utente* interagibili.</span><span class="sxs-lookup"><span data-stu-id="be98b-185">Themes are also re-usable and can be assigned across multiple *Interactable* UX objects.</span></span>

<span data-ttu-id="be98b-186">**Reimposta in base all'eliminazione**</span><span class="sxs-lookup"><span data-stu-id="be98b-186">**Reset On Destroy**</span></span>

<span data-ttu-id="be98b-187">I temi visivi modificano varie proprietà in un GameObject di destinazione, a seconda della classe e del tipo di motore del tema selezionato.</span><span class="sxs-lookup"><span data-stu-id="be98b-187">Visual themes modify various properties on a targeted GameObject, dependent on the class and type of theme engine selected.</span></span> <span data-ttu-id="be98b-188">Se *Reset On Destroy è* true quando il componente Interactable viene eliminato, il componente reimposta tutte le proprietà modificate dai temi attivi ai valori originali.</span><span class="sxs-lookup"><span data-stu-id="be98b-188">If *Reset On Destroy* is true when the Interactable component is destroyed, the component will reset all modified properties from active themes to their original values.</span></span> <span data-ttu-id="be98b-189">In caso contrario, quando viene eliminato, il componente Interactable lascia tutte le proprietà modificate così come sono.</span><span class="sxs-lookup"><span data-stu-id="be98b-189">Otherwise, when destroyed, the Interactable component will leave any modified properties as-is.</span></span> <span data-ttu-id="be98b-190">In quest'ultimo caso, l'ultimo stato dei valori verrà mantenuto a meno che non venga modificato da un altro componente esterno.</span><span class="sxs-lookup"><span data-stu-id="be98b-190">In this latter case, the last state of values will persist unless altered by another external component.</span></span> <span data-ttu-id="be98b-191">Il valore predefinito è false.</span><span class="sxs-lookup"><span data-stu-id="be98b-191">The default is false.</span></span>

<img src="../images/interactable/Profiles_Themes.png" width="450" alt="Profile theams">

## <a name="events"></a><span data-ttu-id="be98b-192">Eventi</span><span class="sxs-lookup"><span data-stu-id="be98b-192">Events</span></span>

<span data-ttu-id="be98b-193">Ogni *componente interactable* ha un *evento OnClick* che viene generato quando il componente viene semplicemente selezionato.</span><span class="sxs-lookup"><span data-stu-id="be98b-193">Every *Interactable* component has an *OnClick* event that fires when the component is simply selected.</span></span> <span data-ttu-id="be98b-194">È tuttavia *possibile usare Interactable* per rilevare eventi di input diversi da *OnClick.*</span><span class="sxs-lookup"><span data-stu-id="be98b-194">However, *Interactable* can be used to detect input events other than just *OnClick*.</span></span>

<span data-ttu-id="be98b-195">Fare clic *sul pulsante Aggiungi* evento per aggiungere un nuovo tipo di definizione del ricevitore di eventi.</span><span class="sxs-lookup"><span data-stu-id="be98b-195">Click the *Add Event* button to add a new type of Event Receiver definition.</span></span> <span data-ttu-id="be98b-196">Dopo l'aggiunta, selezionare il tipo di evento desiderato.</span><span class="sxs-lookup"><span data-stu-id="be98b-196">Once added, select the type of Event desired.</span></span>

![Esempio di eventi](../images/interactable/Events.png)<span data-ttu-id="be98b-198">)</span><span class="sxs-lookup"><span data-stu-id="be98b-198">)</span></span>

<span data-ttu-id="be98b-199">Esistono diversi tipi di ricevitori di eventi per rispondere a diversi tipi di input.</span><span class="sxs-lookup"><span data-stu-id="be98b-199">There are different types of event receivers to respond to different types of input.</span></span> <span data-ttu-id="be98b-200">MRTK viene fornito con il set predefinito di ricevitori seguente.</span><span class="sxs-lookup"><span data-stu-id="be98b-200">MRTK ships with the following set of receivers out-of-box.</span></span>

* [`InteractableAudioReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableAudioReceiver)
* [`InteractableOnClickReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnClickReceiver)
* [`InteractableOnFocusReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnFocusReceiver)
* [`InteractableOnGrabReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnGrabReceiver)
* [`InteractableOnHoldReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnHoldReceiver)
* [`InteractableOnPressReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnPressReceiver)
* [`InteractableOnToggleReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnToggleReceiver)
* [`InteractableOnTouchReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnTouchReceiver)

<span data-ttu-id="be98b-201">È possibile creare un ricevitore personalizzato tramite una nuova classe che estende [`ReceiverBase`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBase) .</span><span class="sxs-lookup"><span data-stu-id="be98b-201">A custom receiver can be created by making a new class that extends [`ReceiverBase`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBase).</span></span>

![Esempio di ricevitore di attivazione/disattivazione eventi](../images/interactable/Event_toggle.png)

<span data-ttu-id="be98b-203">*Esempio di un ricevitore di eventi Toggle*</span><span class="sxs-lookup"><span data-stu-id="be98b-203">*Example of a Toggle Event Receiver*</span></span>

### <a name="interactable-receivers"></a><span data-ttu-id="be98b-204">Ricevitori interagibili</span><span class="sxs-lookup"><span data-stu-id="be98b-204">Interactable receivers</span></span>

 <span data-ttu-id="be98b-205">Il [`InteractableReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableReceiver) componente consente di definire eventi all'esterno del componente *interactable di* origine.</span><span class="sxs-lookup"><span data-stu-id="be98b-205">The [`InteractableReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableReceiver) component allows for events to be defined outside of the source *Interactable* component.</span></span> <span data-ttu-id="be98b-206">*InteractableReceiver rimane* in ascolto di un tipo di evento filtrato attivato da un *altro oggetto Interactable.*</span><span class="sxs-lookup"><span data-stu-id="be98b-206">The *InteractableReceiver* will listen for a filtered event type fired by another *Interactable*.</span></span> <span data-ttu-id="be98b-207">Se la proprietà *Interactable* non è  assegnata direttamente, la proprietà Ambito di ricerca definisce la direzione in cui *InteractableReceiver* è in ascolto di eventi che si verificano su se stesso, in un elemento padre o in un GameObject figlio.</span><span class="sxs-lookup"><span data-stu-id="be98b-207">If the *Interactable* property is not directly assigned, then the *Search Scope* property defines the direction the *InteractableReceiver* listens for events which is either on itself, in a parent, or in a child GameObject.</span></span>

<span data-ttu-id="be98b-208">[`InteractableReceiverList`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableReceiverList) funziona in modo simile, ma per un elenco di eventi corrispondenti.</span><span class="sxs-lookup"><span data-stu-id="be98b-208">[`InteractableReceiverList`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableReceiverList) acts in a similar fashion but for a list of matching events.</span></span>

<img src="../images/interactable/InteractableReceiver.png" width="450" alt="Interactable reciver">

### <a name="create-custom-events"></a><span data-ttu-id="be98b-209">Creare eventi personalizzati</span><span class="sxs-lookup"><span data-stu-id="be98b-209">Create custom events</span></span>

<span data-ttu-id="be98b-210">Come [i temi visivi,](visual-themes.md#custom-theme-engines)gli eventi possono essere estesi per rilevare qualsiasi modello di stato o esporre funzionalità.</span><span class="sxs-lookup"><span data-stu-id="be98b-210">Like [Visual Themes](visual-themes.md#custom-theme-engines), events can be extended to detect any state pattern or to expose functionality.</span></span>

<span data-ttu-id="be98b-211">Gli eventi personalizzati possono essere creati in due modi principali:</span><span class="sxs-lookup"><span data-stu-id="be98b-211">Custom events can be created in two main ways:</span></span>

1) <span data-ttu-id="be98b-212">Estendere la [`ReceiverBase`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBase) classe per creare un evento personalizzato che verrà visualizzato nell'elenco a discesa dei tipi di evento.</span><span class="sxs-lookup"><span data-stu-id="be98b-212">Extend the [`ReceiverBase`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBase) class to create a custom event that will show up in the dropdown list of event types.</span></span> <span data-ttu-id="be98b-213">Per impostazione predefinita, viene fornito un evento Unity, ma è possibile aggiungere altri eventi di Unity oppure impostare l'evento in modo da nascondere gli eventi di Unity.</span><span class="sxs-lookup"><span data-stu-id="be98b-213">A Unity event is provided by default, but additional Unity events can be added or the event can be set to hide Unity events.</span></span> <span data-ttu-id="be98b-214">Questa funzionalità consente a una finestra di progettazione di lavorare con un tecnico su un progetto per creare un evento personalizzato che la finestra di progettazione può configurare nell'editor.</span><span class="sxs-lookup"><span data-stu-id="be98b-214">This functionality allows a designer to work with an engineer on a project to create a custom event that the designer can setup in the editor.</span></span>

1) <span data-ttu-id="be98b-215">Estendere la [`ReceiverBaseMonoBehavior`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBaseMonoBehavior) classe per creare un componente dell'evento completamente personalizzato che può risiedere nell'oggetto *Interactable* o in un altro oggetto.</span><span class="sxs-lookup"><span data-stu-id="be98b-215">Extend the [`ReceiverBaseMonoBehavior`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBaseMonoBehavior) class to create a completely custom event component that can reside on the *Interactable* or another object.</span></span> <span data-ttu-id="be98b-216">[`ReceiverBaseMonoBehavior`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBaseMonoBehavior)L'oggetto farà riferimento a *Interactable* per rilevare le modifiche di stato.</span><span class="sxs-lookup"><span data-stu-id="be98b-216">The [`ReceiverBaseMonoBehavior`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBaseMonoBehavior) will reference the *Interactable* to detect state changes.</span></span>

#### <a name="example-of-extending-receiverbase"></a><span data-ttu-id="be98b-217">Esempio di estensione `ReceiverBase`</span><span class="sxs-lookup"><span data-stu-id="be98b-217">Example of extending `ReceiverBase`</span></span>

<span data-ttu-id="be98b-218">La classe visualizza informazioni sullo stato di un oggetto Interactable ed è un esempio di [`CustomInteractablesReceiver`](xref:Microsoft.MixedReality.Toolkit.UI) come creare un ricevitore di eventi  personalizzato.</span><span class="sxs-lookup"><span data-stu-id="be98b-218">The [`CustomInteractablesReceiver`](xref:Microsoft.MixedReality.Toolkit.UI) class displays status information about an *Interactable* and is an example of how to create a custom Event Receiver.</span></span>

```c#
public CustomInteractablesReceiver(UnityEvent ev) : base(ev, "CustomEvent")
{
    HideUnityEvents = true; // hides Unity events in the receiver - meant to be code only
}
```

<span data-ttu-id="be98b-219">I metodi seguenti sono utili per eseguire l'override o l'implementazione quando si crea un ricevitore di eventi personalizzato.</span><span class="sxs-lookup"><span data-stu-id="be98b-219">The following methods are useful to override/implement when creating a custom Event Receiver.</span></span> <span data-ttu-id="be98b-220">[`ReceiverBase.OnUpdate()`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBase) è un metodo astratto che può essere usato per rilevare i modelli/transizioni di stato.</span><span class="sxs-lookup"><span data-stu-id="be98b-220">[`ReceiverBase.OnUpdate()`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBase) is an abstract method that can be used to detect state patterns/transitions.</span></span> <span data-ttu-id="be98b-221">Inoltre, i [`ReceiverBase.OnVoiceCommand()`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBase) metodi e sono utili per la creazione di logica di eventi personalizzata quando si seleziona [`ReceiverBase.OnClick()`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBase) *Interactable.*</span><span class="sxs-lookup"><span data-stu-id="be98b-221">Furthermore, the [`ReceiverBase.OnVoiceCommand()`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBase) and [`ReceiverBase.OnClick()`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBase) methods are useful for creating custom event logic when the *Interactable* is selected.</span></span>

```c#
public override void OnUpdate(InteractableStates state, Interactable source)
{
    if (state.CurrentState() != lastState)
    {
        // the state has changed, do something new
        lastState = state.CurrentState();
        ...
    }
}

public virtual void OnVoiceCommand(InteractableStates state, Interactable source,
                                    string command, int index = 0, int length = 1)
{
    base.OnVoiceCommand(state, source, command, index, length);
    // voice command called, perform some action
}  

public virtual void OnClick(InteractableStates state,
                            Interactable source,
                            IMixedRealityPointer pointer = null)
{
    base.OnClick(state, source);
    // click called, perform some action
}
```

##### <a name="displaying-custom-event-receiver-fields-in-the-inspector"></a><span data-ttu-id="be98b-222">Visualizzazione dei campi del ricevitore di eventi personalizzati nel controllo</span><span class="sxs-lookup"><span data-stu-id="be98b-222">Displaying custom event receiver fields in the inspector</span></span>

<span data-ttu-id="be98b-223">*Gli script ReceiverBase* [`InspectorField`](xref:Microsoft.MixedReality.Toolkit.Utilities.Editor.InspectorField) usano gli attributi per esporre le proprietà personalizzate nel controllo.</span><span class="sxs-lookup"><span data-stu-id="be98b-223">*ReceiverBase* scripts use [`InspectorField`](xref:Microsoft.MixedReality.Toolkit.Utilities.Editor.InspectorField) attributes to expose custom properties in the inspector.</span></span> <span data-ttu-id="be98b-224">Ecco un esempio di Vector3, una proprietà personalizzata con informazioni su descrizione comando ed etichetta.</span><span class="sxs-lookup"><span data-stu-id="be98b-224">Here's an example of Vector3, a custom property with tooltip and label information.</span></span> <span data-ttu-id="be98b-225">Questa proprietà verrà mostrata come configurabile nel controllo quando viene selezionato un *oggetto GameObject* interagiscibile con il tipo *di* ricevitore di eventi associato aggiunto.</span><span class="sxs-lookup"><span data-stu-id="be98b-225">This property will show up as configurable in the inspector when an *Interactable* GameObject is selected and has the associated *Event Receiver* type added.</span></span>

```c#
[InspectorField(Label = "<Property label>",Tooltip = "<Insert tooltip info>",Type = InspectorField.FieldTypes.Vector3)]
public Vector3 EffectOffset = Vector3.zero;
```

## <a name="how-to-use-interactable"></a><span data-ttu-id="be98b-226">Come usare Interactable</span><span class="sxs-lookup"><span data-stu-id="be98b-226">How to use Interactable</span></span>

### <a name="building-a-simple-button"></a><span data-ttu-id="be98b-227">Compilazione di un pulsante semplice</span><span class="sxs-lookup"><span data-stu-id="be98b-227">Building a simple button</span></span>

<span data-ttu-id="be98b-228">È possibile creare un pulsante semplice aggiungendo il *componente Interactable* a un GameObject configurato per ricevere eventi di input.</span><span class="sxs-lookup"><span data-stu-id="be98b-228">One can create a simple button by adding the *Interactable* component to a GameObject that is configured to receive input events.</span></span> <span data-ttu-id="be98b-229">Può avere un collisore su di esso o su un figlio per ricevere l'input.</span><span class="sxs-lookup"><span data-stu-id="be98b-229">It can have a collider on it or on a child to receive input.</span></span> <span data-ttu-id="be98b-230">Se si *usa Interactable* con un GameObject basato sull'interfaccia utente di Unity, deve essere in Canvas GameObject.</span><span class="sxs-lookup"><span data-stu-id="be98b-230">If using *Interactable* with a Unity UI based GameObjects, it should be under the Canvas GameObject.</span></span>

<span data-ttu-id="be98b-231">Fare un ulteriore passo avanti con il pulsante, creando un nuovo profilo, assegnando lo stesso GameObject e creando un nuovo tema.</span><span class="sxs-lookup"><span data-stu-id="be98b-231">Take the button one step further, by creating a new profile, assigning the GameObject itself and creating a new theme.</span></span> <span data-ttu-id="be98b-232">Usare anche *l'evento OnClick* per eseguire un'altra verifica.</span><span class="sxs-lookup"><span data-stu-id="be98b-232">Furthermore, use the *OnClick* event to make something happen.</span></span>

> [!NOTE]
> <span data-ttu-id="be98b-233">La pressione [di un pulsante](button.md) richiede il componente [`PressableButton`](xref:Microsoft.MixedReality.Toolkit.UI.PressableButton) .</span><span class="sxs-lookup"><span data-stu-id="be98b-233">Making a [button pressable](button.md) requires the [`PressableButton`](xref:Microsoft.MixedReality.Toolkit.UI.PressableButton) component.</span></span> <span data-ttu-id="be98b-234">Inoltre, il componente è necessario per incanalare gli eventi [`PhysicalPressEventRouter`](xref:Microsoft.MixedReality.Toolkit.PhysicalPressEventRouter) di pressione nel componente *Interactable.*</span><span class="sxs-lookup"><span data-stu-id="be98b-234">Additionally, the [`PhysicalPressEventRouter`](xref:Microsoft.MixedReality.Toolkit.PhysicalPressEventRouter) component is needed to funnel press events to the *Interactable* component.</span></span>

### <a name="creating-toggle-and-multi-dimension-buttons"></a><span data-ttu-id="be98b-235">Creazione di pulsanti di attivazione/disattivazione e multi-dimensione</span><span class="sxs-lookup"><span data-stu-id="be98b-235">Creating toggle and multi-dimension buttons</span></span>

#### <a name="toggle-button"></a><span data-ttu-id="be98b-236">Interruttore</span><span class="sxs-lookup"><span data-stu-id="be98b-236">Toggle button</span></span>

<span data-ttu-id="be98b-237">Per rendere attiva/disattiva un pulsante, modificare il [`Selection Mode`](xref:Microsoft.MixedReality.Toolkit.UI.SelectionModes) campo in digitare `Toggle` .</span><span class="sxs-lookup"><span data-stu-id="be98b-237">To make a button Toggle-able, change the [`Selection Mode`](xref:Microsoft.MixedReality.Toolkit.UI.SelectionModes) field to type `Toggle`.</span></span> <span data-ttu-id="be98b-238">Nella sezione *Profili* viene aggiunto un nuovo tema attivato/disattivato per ogni profilo usato quando l'elemento *Interactable* è attivato.</span><span class="sxs-lookup"><span data-stu-id="be98b-238">In the *Profiles* section, a new toggled theme is added for each profile that is used when the *Interactable* is toggled on.</span></span>

<span data-ttu-id="be98b-239">Mentre è [`SelectionMode`](xref:Microsoft.MixedReality.Toolkit.UI.SelectionModes) impostata su Toggle, la casella di controllo *IsToggled* può essere usata per impostare il valore predefinito del controllo in fase di inizializzazione di runtime.</span><span class="sxs-lookup"><span data-stu-id="be98b-239">While the [`SelectionMode`](xref:Microsoft.MixedReality.Toolkit.UI.SelectionModes) is set to Toggle, the *IsToggled* check box can be used to set the default value of the control at runtime initialization.</span></span>

<span data-ttu-id="be98b-240">*CanSelect* indica che *l'oggetto Interactable* può andare da *un'opzione* all'altro *mentre* *CanDeselect* indica l'inverso.</span><span class="sxs-lookup"><span data-stu-id="be98b-240">*CanSelect* means the *Interactable* can go from *off* to *on* while the *CanDeselect* means the inverse.</span></span>

![Esempio di attivazione/disattivazione dei temi visivi del profilo](../images/interactable/Profile_toggle.png)

<span data-ttu-id="be98b-242">Gli sviluppatori possono usare le [`SetToggled`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) interfacce e per ottenere/impostare lo stato di [`IsToggled`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) attivazione/disattivazione di *un oggetto Interactable* tramite codice.</span><span class="sxs-lookup"><span data-stu-id="be98b-242">Developers can utilize the [`SetToggled`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) and [`IsToggled`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) interfaces to get/set the toggle state of an *Interactable* via code.</span></span>

```c#
// If using SelectionMode = Toggle (i.e Dimensions == 2)

// Make the Interactable selected and toggled on
myInteractable.IsToggled = true;

// Get whether the Interactable is selected or not
bool isSelected = myInteractable.IsToggled;
```

##### <a name="toggle-button-collection"></a><span data-ttu-id="be98b-243">Attivare/disattivare la raccolta di pulsanti</span><span class="sxs-lookup"><span data-stu-id="be98b-243">Toggle button collection</span></span>

<span data-ttu-id="be98b-244">È comune avere un elenco di pulsanti di attivazione/disattivazione in cui solo uno può essere attivo in un determinato momento, noto anche come set radiale o pulsanti di opzione e così via.</span><span class="sxs-lookup"><span data-stu-id="be98b-244">It is common to have a list of toggle buttons where only one can be active at any given time, also known as a radial set or radio buttons etc.</span></span>

<span data-ttu-id="be98b-245">Usare il [`InteractableToggleCollection`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableToggleCollection) componente per abilitare questa funzionalità.</span><span class="sxs-lookup"><span data-stu-id="be98b-245">Use the [`InteractableToggleCollection`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableToggleCollection) component to enable this functionality.</span></span> <span data-ttu-id="be98b-246">Questo controllo garantisce l'attivazione di un solo elemento *Interactable* in un determinato momento.</span><span class="sxs-lookup"><span data-stu-id="be98b-246">This control ensures only one *Interactable* is toggled on at any given time.</span></span> <span data-ttu-id="be98b-247">*RadialSet* (Assets/MRTK/SDK/Features/UX/Interactable/Prefabs/RadialSet.prefab) è anche un ottimo punto di partenza predefinito.</span><span class="sxs-lookup"><span data-stu-id="be98b-247">The *RadialSet* (Assets/MRTK/SDK/Features/UX/Interactable/Prefabs/RadialSet.prefab) is also a great starting point out-of-box.</span></span>

<span data-ttu-id="be98b-248">Per creare un gruppo di pulsanti radiali personalizzato:</span><span class="sxs-lookup"><span data-stu-id="be98b-248">To create a custom radial button group:</span></span>

1) <span data-ttu-id="be98b-249">Creare più *GameObject/pulsanti* con supporto per l'interazione</span><span class="sxs-lookup"><span data-stu-id="be98b-249">Create multiple *Interactable* GameObjects/buttons</span></span>
1) <span data-ttu-id="be98b-250">Impostare ogni *oggetto Interactable* *con SelectionMode* = Toggle, *CanSelect* = true e *CanDeselect* = false</span><span class="sxs-lookup"><span data-stu-id="be98b-250">Set each *Interactable* with *SelectionMode* = Toggle, *CanSelect* = true, and *CanDeselect* = false</span></span>
1) <span data-ttu-id="be98b-251">Creare un GameObject padre vuoto su tutti *gli oggetti Interactable e* aggiungere il componente *InteractableToggleCollection*</span><span class="sxs-lookup"><span data-stu-id="be98b-251">Create an empty parent GameObject over all the *Interactables* and add the *InteractableToggleCollection* component</span></span>
1) <span data-ttu-id="be98b-252">Aggiungere tutti *gli oggetti Interactable* a *ToggleList* in *InteractableToggleCollection*</span><span class="sxs-lookup"><span data-stu-id="be98b-252">Add all *Interactables* to the *ToggleList* on the *InteractableToggleCollection*</span></span>
1) <span data-ttu-id="be98b-253">Impostare la *proprietà InteractableToggleCollection.CurrentIndex* per determinare quale pulsante è selezionato per impostazione predefinita all'inizio</span><span class="sxs-lookup"><span data-stu-id="be98b-253">Set the *InteractableToggleCollection.CurrentIndex* property to determine which button is selected by default at start</span></span>

<img src="../images/interactable/InteractableToggleCollection.png" width="450" alt="Toggle collection">

#### <a name="multi-dimensional-button"></a><span data-ttu-id="be98b-254">Pulsante multidimensionale</span><span class="sxs-lookup"><span data-stu-id="be98b-254">Multi-dimensional button</span></span>

<span data-ttu-id="be98b-255">La modalità di selezione multi-dimensione viene usata per creare pulsanti sequenziali o un pulsante con più di due passaggi, ad esempio il controllo della velocità con tre valori, Veloce (1x), Più veloce (2x) o Più veloce (3x).</span><span class="sxs-lookup"><span data-stu-id="be98b-255">Multi-Dimension selection mode is used to create sequential buttons, or a button that has more than two steps, like controlling speed with three values, Fast (1x), Faster (2x) or Fastest (3x).</span></span>

<span data-ttu-id="be98b-256">Con le dimensioni come valore numerico, è possibile aggiungere fino a 9 temi per controllare l'etichetta di testo o la trama del pulsante per ogni impostazione di velocità, usando un tema diverso per ogni passaggio.</span><span class="sxs-lookup"><span data-stu-id="be98b-256">With dimensions being a numeric value, up to 9 themes can be added to control the text label or texture of the button for each speed setting, using a different theme for each of step.</span></span>

<span data-ttu-id="be98b-257">Ogni evento click avanza di `DimensionIndex` 1 in fase di esecuzione fino a quando non `Dimensions` viene raggiunto il valore .</span><span class="sxs-lookup"><span data-stu-id="be98b-257">Every click event will advance the `DimensionIndex` by 1 at runtime until the `Dimensions` value is reached.</span></span> <span data-ttu-id="be98b-258">Il ciclo verrà quindi reimpostato su 0.</span><span class="sxs-lookup"><span data-stu-id="be98b-258">Then the cycle will reset to 0.</span></span>

![Esempio di profilo multidimensionale](../images/interactable/Profile_multiDimensions.png)

<span data-ttu-id="be98b-260">Gli sviluppatori possono valutare [`DimensionIndex`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) per determinare quale dimensione è attualmente attiva.</span><span class="sxs-lookup"><span data-stu-id="be98b-260">Developers can assess the [`DimensionIndex`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) to determine which dimension is currently active.</span></span>

```c#
// If using SelectionMode = Multi-dimension (i.e Dimensions >= 3)

//Access the current DimensionIndex
int currentDimension = myInteractable.CurrentDimension;

//Set the current DimensionIndex to 2
myInteractable.CurrentDimension = 2;

// Promote Dimension to next level
myInteractable.IncreaseDimension();
```

### <a name="create-interactable-at-runtime"></a><span data-ttu-id="be98b-261">Creare oggetti interactable in fase di esecuzione</span><span class="sxs-lookup"><span data-stu-id="be98b-261">Create Interactable at runtime</span></span>

<span data-ttu-id="be98b-262">*È possibile aggiungere* facilmente oggetti Interactable a qualsiasi GameObject in fase di esecuzione.</span><span class="sxs-lookup"><span data-stu-id="be98b-262">*Interactable* can be easily added to any GameObject at runtime.</span></span> <span data-ttu-id="be98b-263">Nell'esempio seguente viene illustrato come assegnare un profilo con un [tema visivo](visual-themes.md).</span><span class="sxs-lookup"><span data-stu-id="be98b-263">The following example demonstrates how to assign a profile with a [visual theme](visual-themes.md).</span></span>

```c#
var interactableObject = GameObject.CreatePrimitive(PrimitiveType.Cylinder);
var interactable = interactableObject.AddComponent<Interactable>();

// Get the default configuration for the Theme engine InteractableColorTheme
var newThemeType = ThemeDefinition.GetDefaultThemeDefinition<InteractableColorTheme>().Value;

// Define a color for every state in our Default Interactable States
newThemeType.StateProperties[0].Values = new List<ThemePropertyValue>()
{
    new ThemePropertyValue() { Color = Color.black},  // Default
    new ThemePropertyValue() { Color = Color.black}, // Focus
    new ThemePropertyValue() { Color = Random.ColorHSV()},   // Pressed
    new ThemePropertyValue() { Color = Color.black},   // Disabled
};

interactable.Profiles = new List<InteractableProfileItem>()
{
    new InteractableProfileItem()
    {
        Themes = new List<Theme>()
        {
            Interactable.GetDefaultThemeAsset(new List<ThemeDefinition>() { newThemeType })
        },
        Target = interactableObject,
    },
};

// Force the Interactable to be clicked
interactable.TriggerOnClick()
```

### <a name="interactable-events-via-code"></a><span data-ttu-id="be98b-264">Eventi con interazione tramite codice</span><span class="sxs-lookup"><span data-stu-id="be98b-264">Interactable events via code</span></span>

<span data-ttu-id="be98b-265">È possibile aggiungere un'azione all'evento di base [`Interactable.OnClick`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.OnClick) tramite codice con l'esempio seguente.</span><span class="sxs-lookup"><span data-stu-id="be98b-265">One can add an action to the base [`Interactable.OnClick`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.OnClick) event via code with the following example.</span></span>

```c#
public static void AddOnClick(Interactable interactable)
{
    interactable.OnClick.AddListener(() => Debug.Log("Interactable clicked"));
}
```

<span data-ttu-id="be98b-266">Usare la [`Interactable.AddReceiver<T>()`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) funzione per aggiungere ricevitori di eventi in modo dinamico in fase di esecuzione.</span><span class="sxs-lookup"><span data-stu-id="be98b-266">Use the [`Interactable.AddReceiver<T>()`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) function to add event receivers dynamically at runtime.</span></span>

<span data-ttu-id="be98b-267">Il codice di esempio seguente illustra come aggiungere [un oggetto InteractableOnFocusReceiver](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnFocusReceiver), che rimane in ascolto dell'attivazione/uscita dello stato attivo e definisce inoltre il codice azione da eseguire quando vengono create le istanze dell'evento.</span><span class="sxs-lookup"><span data-stu-id="be98b-267">The example code below demonstrates how to add an [InteractableOnFocusReceiver](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnFocusReceiver), which listens for focus enter/exit, and furthermore define action code to perform when the event instances fire.</span></span>

```c#
public static void AddFocusEvents(Interactable interactable)
{
    var onFocusReceiver = interactable.AddReceiver<InteractableOnFocusReceiver>();

    onFocusReceiver.OnFocusOn.AddListener(() => Debug.Log("Focus on"));
    onFocusReceiver.OnFocusOff.AddListener(() => Debug.Log("Focus off"));
}
```

<span data-ttu-id="be98b-268">Il codice di esempio seguente illustra come aggiungere un [oggetto InteractableOnToggleReceiver](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnFocusReceiver), che rimane in ascolto delle transizioni di stato selezionate/deselezionate in *interactables* attivabili e definisce inoltre il codice azione da eseguire quando vengono attivate le istanze dell'evento.</span><span class="sxs-lookup"><span data-stu-id="be98b-268">The example code below demonstrates how to add an [InteractableOnToggleReceiver](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnFocusReceiver), which listens for selected/deselected state transitions on toggle-able *Interactables*, and furthermore defines action code to perform when the event instances fire.</span></span>

```c#
public static void AddToggleEvents(Interactable interactable)
{
    var toggleReceiver = interactable.AddReceiver<InteractableOnToggleReceiver>();

    // Make the interactable have toggle capability, from code.
    // In the gui editor it's much easier
    interactable.Dimensions = 2;
    interactable.CanSelect = true;
    interactable.CanDeselect  = true;

    toggleReceiver.OnSelect.AddListener(() => Debug.Log("Toggle selected"));
    toggleReceiver.OnDeselect.AddListener(() => Debug.Log("Toggle un-selected"));
}
```

## <a name="see-also"></a><span data-ttu-id="be98b-269">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="be98b-269">See also</span></span>

* [<span data-ttu-id="be98b-270">Temi visivi</span><span class="sxs-lookup"><span data-stu-id="be98b-270">Visual Themes</span></span>](visual-themes.md)
* [<span data-ttu-id="be98b-271">Azioni di input</span><span class="sxs-lookup"><span data-stu-id="be98b-271">Input Actions</span></span>](../input/input-actions.md)
* [<span data-ttu-id="be98b-272">Comandi vocali</span><span class="sxs-lookup"><span data-stu-id="be98b-272">Speech Commands</span></span>](../input/speech.md)
* [<span data-ttu-id="be98b-273">Pulsanti</span><span class="sxs-lookup"><span data-stu-id="be98b-273">Buttons</span></span>](button.md)
* [<span data-ttu-id="be98b-274">MRTK Standard Shader</span><span class="sxs-lookup"><span data-stu-id="be98b-274">MRTK Standard Shader</span></span>](../rendering/MRTK-standard-shader.md)

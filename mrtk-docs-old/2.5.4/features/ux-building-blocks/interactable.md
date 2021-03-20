---
title: Con cui
description: Panoramica sul componente script interactable in MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, interactable, eventi,
ms.openlocfilehash: 0a7c8567feae0c903dae83e020035c3e6de995e8
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2021
ms.locfileid: "104686364"
---
# <a name="interactable"></a><span data-ttu-id="0409c-104">Con cui</span><span class="sxs-lookup"><span data-stu-id="0409c-104">Interactable</span></span>

![Con cui](../images/interactable/InteractableExamples.png)

<span data-ttu-id="0409c-106">Il [`Interactable`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) componente è un contenitore All-in-One per rendere qualsiasi oggetto facilmente *interactabile* e reattivo all'input.</span><span class="sxs-lookup"><span data-stu-id="0409c-106">The [`Interactable`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) component is an all-in-one container to make any object easily *interactable* and responsive to input.</span></span> <span data-ttu-id="0409c-107">Interactable funge da catch-all per tutti i tipi di input, tra cui il tocco, i raggi di mano, il parlato e così via, e l'imbuto di queste interazioni negli [eventi](#events) e nelle risposte del [tema](../visual-themes.md)</span><span class="sxs-lookup"><span data-stu-id="0409c-107">Interactable acts as a catch-all for all types of input including touch, hand rays, speech etc and funnel these interactions into [events](#events) and [visual theme](../visual-themes.md) responses.</span></span> <span data-ttu-id="0409c-108">Questo componente fornisce un modo semplice per creare pulsanti, modificare il colore degli oggetti con lo stato attivo e altro ancora.</span><span class="sxs-lookup"><span data-stu-id="0409c-108">This component provides an easy way to make buttons, change color on objects with focus, and more.</span></span>

## <a name="how-to-configure-interactable"></a><span data-ttu-id="0409c-109">Come configurare interactable</span><span class="sxs-lookup"><span data-stu-id="0409c-109">How to configure Interactable</span></span>

<span data-ttu-id="0409c-110">Il componente consente tre sezioni principali della configurazione:</span><span class="sxs-lookup"><span data-stu-id="0409c-110">The component allows for three primary sections of configuration:</span></span>

1) [<span data-ttu-id="0409c-111">Configurazione di input generale</span><span class="sxs-lookup"><span data-stu-id="0409c-111">General input configuration</span></span>](#general-input-settings)
1) <span data-ttu-id="0409c-112">[Temi visivi](../visual-themes.md) destinati a più GameObject</span><span class="sxs-lookup"><span data-stu-id="0409c-112">[Visual Themes](../visual-themes.md) targeted against multiple GameObjects</span></span>
1) [<span data-ttu-id="0409c-113">Gestori eventi</span><span class="sxs-lookup"><span data-stu-id="0409c-113">Event handlers</span></span>](#events)

### <a name="general-input-settings"></a><span data-ttu-id="0409c-114">Impostazioni di input generali</span><span class="sxs-lookup"><span data-stu-id="0409c-114">General input settings</span></span>

![Impostazioni generali per l'interazione](../images/interactable/InputFeatures_short.png)

<span data-ttu-id="0409c-116">**Stati**</span><span class="sxs-lookup"><span data-stu-id="0409c-116">**States**</span></span>

<span data-ttu-id="0409c-117">*States* è un parametro [ScriptableObject](https://docs.unity3d.com/Manual/class-ScriptableObject.html) che definisce le fasi di interazione, ad esempio premere o osservato, per i profili e i [temi visivi](../visual-themes.md) [interagibili](#interactable-profiles) .</span><span class="sxs-lookup"><span data-stu-id="0409c-117">*States* is a [ScriptableObject](https://docs.unity3d.com/Manual/class-ScriptableObject.html) parameter that defines the interactions phases, like press or observed, for [Interactable Profiles](#interactable-profiles) and [Visual Themes](../visual-themes.md).</span></span>

<span data-ttu-id="0409c-118">**DefaultInteractableStates** (assets/MRTK/SDK/features/UX/interactable/States/DefaultInteractableStates. asset) viene fornito con MRTK predefinito ed è il parametro predefinito per i componenti *interagibili* .</span><span class="sxs-lookup"><span data-stu-id="0409c-118">The **DefaultInteractableStates** (Assets/MRTK/SDK/Features/UX/Interactable/States/DefaultInteractableStates.asset) ships with MRTK out-of-box and is the default parameter for *Interactable* components.</span></span>

![Esempio di ScriptableObject di stati in Inspector](../images/interactable/DefaultInteractableStates.png)

<span data-ttu-id="0409c-120">L'asset *DefaultInteractableStates* contiene quattro Stati e usa l' [`InteractableStates`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableStates) implementazione del modello di stato.</span><span class="sxs-lookup"><span data-stu-id="0409c-120">The *DefaultInteractableStates* asset contains four states and utilizes the [`InteractableStates`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableStates) state model implementation.</span></span>

* <span data-ttu-id="0409c-121">**Impostazione predefinita**: non viene eseguita alcuna operazione. si tratta dello stato di base più isolato.</span><span class="sxs-lookup"><span data-stu-id="0409c-121">**Default**: Nothing is happening, this is the most isolated base state.</span></span>

* <span data-ttu-id="0409c-122">**Focus**: l'oggetto a cui si fa riferimento.</span><span class="sxs-lookup"><span data-stu-id="0409c-122">**Focus**: The object is being pointed at.</span></span> <span data-ttu-id="0409c-123">Si tratta di uno stato singolo, nessun altro stato è attualmente impostato, ma il valore predefinito è rango.</span><span class="sxs-lookup"><span data-stu-id="0409c-123">This is a single state, no other states are currently set, but it will out rank Default.</span></span>

* <span data-ttu-id="0409c-124">**Premere**: viene fatto riferimento all'oggetto e viene premuto un pulsante o una mano.</span><span class="sxs-lookup"><span data-stu-id="0409c-124">**Press**: The object is being pointed at and a button or hand is pressing.</span></span> <span data-ttu-id="0409c-125">Per impostazione predefinita, lo stato viene impostato su Allinea e lo stato attivo.</span><span class="sxs-lookup"><span data-stu-id="0409c-125">The Press state out ranks Default and Focus.</span></span> <span data-ttu-id="0409c-126">Questo stato verrà inoltre impostato come fallback per la pressione fisica.</span><span class="sxs-lookup"><span data-stu-id="0409c-126">This state will also get set as a fallback to Physical Press.</span></span>

* <span data-ttu-id="0409c-127">**Disabilitato**: il pulsante non deve essere interattivo e il feedback visivo consente all'utente di verificare se per qualche motivo questo pulsante non è utilizzabile in questo momento.</span><span class="sxs-lookup"><span data-stu-id="0409c-127">**Disabled**: The button should not be interactive and visual feedback will let the user know if for some reason this button is not usable at this time.</span></span> <span data-ttu-id="0409c-128">In teoria, lo stato disabilitato potrebbe contenere tutti gli altri Stati, ma se abilitato è disattivato, lo stato disabilitato trionferà su tutti gli altri Stati.</span><span class="sxs-lookup"><span data-stu-id="0409c-128">In theory, the disabled state could contain all other states, but when Enabled is turned off, the Disabled state trumps all other states.</span></span>

<span data-ttu-id="0409c-129">A seconda dell'ordine nell'elenco, viene assegnato un valore di bit (#) allo stato.</span><span class="sxs-lookup"><span data-stu-id="0409c-129">A bit value (#) is assigned to the state depending on the order in the list.</span></span>

> [!NOTE]
> <span data-ttu-id="0409c-130">È in genere consigliabile usare **DefaultInteractableStates** (assets/MRTK/SDK/features/UX/interactable/States/DefaultInteractableStates. asset) quando si creano componenti *interagibili* .</span><span class="sxs-lookup"><span data-stu-id="0409c-130">It is generally recommended to utilize the **DefaultInteractableStates** (Assets/MRTK/SDK/Features/UX/Interactable/States/DefaultInteractableStates.asset) when creating *Interactable* components.</span></span>
>
> <span data-ttu-id="0409c-131">Tuttavia, sono disponibili 17 Stati interagibili che possono essere usati per guidare i temi, anche se alcuni sono pensati per essere gestiti da altri componenti.</span><span class="sxs-lookup"><span data-stu-id="0409c-131">However, there are 17 Interactable states available that can be used to drive themes, though some are meant to be driven by other components.</span></span> <span data-ttu-id="0409c-132">Di seguito è riportato un elenco di quelli con funzionalità predefinite.</span><span class="sxs-lookup"><span data-stu-id="0409c-132">Here is a list of those with built-in functionality.</span></span>
>
> * <span data-ttu-id="0409c-133">Visitata: è stato fatto clic su interactable.</span><span class="sxs-lookup"><span data-stu-id="0409c-133">Visited: the Interactable has been clicked.</span></span>
> * <span data-ttu-id="0409c-134">Attivato/disattivato: il pulsante è in uno stato o un indice della dimensione disattivato è un numero dispari.</span><span class="sxs-lookup"><span data-stu-id="0409c-134">Toggled: The button is in a toggled state or Dimension index is an odd number.</span></span>
> * <span data-ttu-id="0409c-135">Gesto: la mano o il controller è stato premuto ed è stato spostato dalla posizione originale.</span><span class="sxs-lookup"><span data-stu-id="0409c-135">Gesture: The hand or controller was pressed and has moved from the original position.</span></span>
> * <span data-ttu-id="0409c-136">VoiceCommand: è stato usato un comando per la sintesi vocale per attivare l'interazione.</span><span class="sxs-lookup"><span data-stu-id="0409c-136">VoiceCommand: A speech command was used to trigger the Interactable.</span></span>
> * <span data-ttu-id="0409c-137">PhysicalTouch: è attualmente rilevato un input tocco, [`NearInteractionTouchable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) da usare per abilitare.</span><span class="sxs-lookup"><span data-stu-id="0409c-137">PhysicalTouch: A touch input is currently detected, use [`NearInteractionTouchable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) to enable.</span></span>
> * <span data-ttu-id="0409c-138">Acquisisci: una mano è attualmente in fase di acquisizione nei limiti dell'oggetto, usare [`NearInteractionGrabbable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionGrabbable) per abilitare</span><span class="sxs-lookup"><span data-stu-id="0409c-138">Grab: A hand is currently grabbing in the bounds of the object, use [`NearInteractionGrabbable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionGrabbable) to enable</span></span>

<span data-ttu-id="0409c-139">**Enabled**</span><span class="sxs-lookup"><span data-stu-id="0409c-139">**Enabled**</span></span>

<span data-ttu-id="0409c-140">Consente di attivare o meno l'abilitazione di un oggetto che interagisce.</span><span class="sxs-lookup"><span data-stu-id="0409c-140">Toggles whether an Interactable will start enabled or not.</span></span> <span data-ttu-id="0409c-141">Corrisponde al [`Interactable.IsEnabled`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.IsEnabled) nel codice.</span><span class="sxs-lookup"><span data-stu-id="0409c-141">This corresponds to the [`Interactable.IsEnabled`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.IsEnabled) in code.</span></span>

<span data-ttu-id="0409c-142">Una proprietà abilitata per *Interact* è diversa dalla proprietà Enabled configurata tramite GameObject/Component (ovvero</span><span class="sxs-lookup"><span data-stu-id="0409c-142">An *Interactable's* enabled property is different than the enabled property configured via GameObject/Component (i.e</span></span> <span data-ttu-id="0409c-143">Seattivo e così via).</span><span class="sxs-lookup"><span data-stu-id="0409c-143">SetActive etc).</span></span> <span data-ttu-id="0409c-144">La disabilitazione di GameObject *o di* monobehavior interattivi comporta la disabilitazione di tutti gli elementi nella classe, inclusi input, temi visivi, eventi e così via. La disabilitazione [`Interactable.IsEnabled`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.IsEnabled) di via Disabilita la maggior parte della gestione degli input, reimpostando gli Stati di input correlati.</span><span class="sxs-lookup"><span data-stu-id="0409c-144">Disabling the GameObject or *Interactable* MonoBehaviour will disable everything in the class from running including input, visual themes, events, etc. Disabling via [`Interactable.IsEnabled`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.IsEnabled) will disable most input handling, resetting related input states.</span></span> <span data-ttu-id="0409c-145">Tuttavia, la classe continuerà a eseguire tutti i frame e a ricevere eventi di input che verranno ignorati.</span><span class="sxs-lookup"><span data-stu-id="0409c-145">However, the class will still run every frame and receive input events which will be ignored.</span></span> <span data-ttu-id="0409c-146">Questa operazione è utile per visualizzare lo stato interattivo in uno stato disabilitato, che può essere eseguito tramite temi visivi.</span><span class="sxs-lookup"><span data-stu-id="0409c-146">This is useful for displaying the Interactable in a disabled state which can be done via Visual Themes.</span></span> <span data-ttu-id="0409c-147">Un esempio tipico è costituito da un pulsante di invio in attesa del completamento di tutti i campi di input necessari.</span><span class="sxs-lookup"><span data-stu-id="0409c-147">A typical example of this would be a submit button waiting for all the required input fields to be completed.</span></span>

<span data-ttu-id="0409c-148">**Azioni di input**</span><span class="sxs-lookup"><span data-stu-id="0409c-148">**Input Actions**</span></span>

<span data-ttu-id="0409c-149">Consente di selezionare l' [azione di input](../input/input-actions.md) dal profilo di configurazione di input o di mapping del controller a cui il componente *interagibile* deve rispondere.</span><span class="sxs-lookup"><span data-stu-id="0409c-149">Select the [input action](../input/input-actions.md) from the input configuration or controller mapping profile that the *Interactable* component should react to.</span></span>

<span data-ttu-id="0409c-150">Questa proprietà può essere configurata in fase di esecuzione nel codice tramite [`Interactable.InputAction`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.InputAction) .</span><span class="sxs-lookup"><span data-stu-id="0409c-150">This property can be configured at runtime in code via [`Interactable.InputAction`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.InputAction).</span></span>

<span data-ttu-id="0409c-151">**IsGlobal**</span><span class="sxs-lookup"><span data-stu-id="0409c-151">**IsGlobal**</span></span>

<span data-ttu-id="0409c-152">Se true, il componente viene contrassegnato come listener di input globale per l'azione di [input](../input/input-actions.md)selezionata.</span><span class="sxs-lookup"><span data-stu-id="0409c-152">If true, this will mark the component as a global input listener for the selected [input action](../input/input-actions.md).</span></span> <span data-ttu-id="0409c-153">Il comportamento predefinito è false che consente di limitare l'input solo a questo Collider/GameObject di *interazione* .</span><span class="sxs-lookup"><span data-stu-id="0409c-153">Default behavior is false which will restrict input to only this *Interactable* collider/GameObject.</span></span>

<span data-ttu-id="0409c-154">Questa proprietà può essere configurata in fase di esecuzione nel codice tramite [`Interactable.IsGlobal`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.IsGlobal) .</span><span class="sxs-lookup"><span data-stu-id="0409c-154">This property can be configured at runtime in code via [`Interactable.IsGlobal`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.IsGlobal).</span></span>

<span data-ttu-id="0409c-155">**Comando sintesi vocale**</span><span class="sxs-lookup"><span data-stu-id="0409c-155">**Speech Command**</span></span>

<span data-ttu-id="0409c-156">[Comando di sintesi vocale](../input/speech.md), dal profilo dei comandi di sintesi vocale MRTK, per attivare un evento OnClick per l'interazione vocale.</span><span class="sxs-lookup"><span data-stu-id="0409c-156">[Speech command](../input/speech.md), from the MRTK Speech Commands Profile, to trigger an OnClick event for voice interaction.</span></span>

<span data-ttu-id="0409c-157">Questa proprietà può essere configurata in fase di esecuzione nel codice tramite [`Interactable.VoiceCommand`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.VoiceCommand) .</span><span class="sxs-lookup"><span data-stu-id="0409c-157">This property can be configured at runtime in code via [`Interactable.VoiceCommand`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.VoiceCommand).</span></span>

<span data-ttu-id="0409c-158">**Richiede lo stato attivo**</span><span class="sxs-lookup"><span data-stu-id="0409c-158">**Requires Focus**</span></span>

<span data-ttu-id="0409c-159">Se true, il comando Voice attiverà solo l'interoperabilità *solo se è* già stato attivato da un puntatore.</span><span class="sxs-lookup"><span data-stu-id="0409c-159">If true, the voice command will only activate the *Interactable* if and only if it already has focus from a pointer.</span></span> <span data-ttu-id="0409c-160">Se false, l' *interfaccia* interoperabile fungerà da listener globale per il comando Voice selezionato.</span><span class="sxs-lookup"><span data-stu-id="0409c-160">If false, then the *Interactable* will act as a global listener for the selected voice command.</span></span> <span data-ttu-id="0409c-161">Il comportamento predefinito è true, in quanto più listener di riconoscimento vocale globale possono essere difficili da organizzare in una scena.</span><span class="sxs-lookup"><span data-stu-id="0409c-161">The default behavior is true, as multiple global speech listeners can be difficult to organize in a scene.</span></span>

<span data-ttu-id="0409c-162">Questa proprietà può essere configurata in fase di esecuzione nel codice tramite [`Interactable.VoiceRequiresFocus`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.VoiceRequiresFocus) .</span><span class="sxs-lookup"><span data-stu-id="0409c-162">This property can be configured at runtime in code via [`Interactable.VoiceRequiresFocus`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.VoiceRequiresFocus).</span></span>

<span data-ttu-id="0409c-163">**Modalità di selezione**</span><span class="sxs-lookup"><span data-stu-id="0409c-163">**Selection Mode**</span></span>

<span data-ttu-id="0409c-164">Questa proprietà definisce la logica di selezione.</span><span class="sxs-lookup"><span data-stu-id="0409c-164">This property defines the selection logic.</span></span> <span data-ttu-id="0409c-165">Quando si fa clic su un oggetto *interactable* , viene iterato in un livello di *dimensione* successivo.</span><span class="sxs-lookup"><span data-stu-id="0409c-165">When an *Interactable* is clicked, it iterates into a next *Dimension* level.</span></span> <span data-ttu-id="0409c-166">*Dimensions* è simile a Rank e definisce uno stato al di fuori degli input (ad esempio</span><span class="sxs-lookup"><span data-stu-id="0409c-166">*Dimensions* is similar to rank and defines a state outside of inputs (i.e</span></span> <span data-ttu-id="0409c-167">concentrarsi, premere e così via.</span><span class="sxs-lookup"><span data-stu-id="0409c-167">focus, press etc).</span></span> <span data-ttu-id="0409c-168">Sono utili per definire gli Stati di attivazione/disattivazione o altri Stati con più livelli associati a un pulsante.</span><span class="sxs-lookup"><span data-stu-id="0409c-168">They are useful for defining Toggle states or other multi-rank states associated with a button.</span></span> <span data-ttu-id="0409c-169">Il livello della dimensione corrente viene rilevato da `Interactable.DimensionIndex` .</span><span class="sxs-lookup"><span data-stu-id="0409c-169">The current Dimension level is tracked by `Interactable.DimensionIndex`.</span></span>

<span data-ttu-id="0409c-170">Le modalità di selezione disponibili sono:</span><span class="sxs-lookup"><span data-stu-id="0409c-170">The selection modes available are:</span></span>

* <span data-ttu-id="0409c-171">**Pulsante**  -  *Dimensioni* = 1, semplice e *interattivo* selezionabile</span><span class="sxs-lookup"><span data-stu-id="0409c-171">**Button** - *Dimensions* = 1, simple clickable *Interactable*</span></span>
* <span data-ttu-id="0409c-172">**Imposta/Nascondi**  -  *Dimensioni* = *2,* alternanze  / *interattive* tra lo stato disattivato</span><span class="sxs-lookup"><span data-stu-id="0409c-172">**Toggle** - *Dimensions* = 2, *Interactable* alternates between *on*/*off* state</span></span>
* <span data-ttu-id="0409c-173">**MULTIDIMENSIONE**  -  *Dimensions* >= 3, ogni clic aumenta il livello della dimensione corrente + 1.</span><span class="sxs-lookup"><span data-stu-id="0409c-173">**Multi-dimension** - *Dimensions* >= 3, every click increases the current dimension level + 1.</span></span> <span data-ttu-id="0409c-174">Utile per definire lo stato di un pulsante in un elenco e così via.</span><span class="sxs-lookup"><span data-stu-id="0409c-174">Useful for defining a button state to a list, etc.</span></span>

<span data-ttu-id="0409c-175">*Interactable* consente inoltre di definire più temi per *dimensione*.</span><span class="sxs-lookup"><span data-stu-id="0409c-175">*Interactable* also allows for multiple Themes to be defined per *Dimension*.</span></span> <span data-ttu-id="0409c-176">Ad esempio, quando *SelectionMode = interruttore*, un tema può essere applicato quando l'elemento *Interagisci* viene *deselezionato* e un altro tema viene applicato quando il componente è *selezionato*.</span><span class="sxs-lookup"><span data-stu-id="0409c-176">For example when *SelectionMode=Toggle*, one theme may be applied when the *Interactable* is *deselected* and another theme applied when the component is *selected*.</span></span>

<span data-ttu-id="0409c-177">La modalità di selezione corrente può essere sottoposta a query in fase di esecuzione tramite [`Interactable.ButtonMode`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.ButtonMode) .</span><span class="sxs-lookup"><span data-stu-id="0409c-177">The current Selection Mode can be queried at runtime via [`Interactable.ButtonMode`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.ButtonMode).</span></span> <span data-ttu-id="0409c-178">L'aggiornamento della modalità in fase di esecuzione può essere eseguito impostando la  [`Interactable.Dimensions`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.Dimensions) Proprietà in modo che corrisponda alla funzionalità desiderata.</span><span class="sxs-lookup"><span data-stu-id="0409c-178">Updating the mode at runtime can be achieved by setting the  [`Interactable.Dimensions`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.Dimensions) property to match the desired functionality.</span></span> <span data-ttu-id="0409c-179">Inoltre, è possibile accedere alla dimensione corrente, utile per le modalità di *attivazione/disattivazione* e *MULTIDIMENSIONE* , tramite [`Interactable.CurrentDimension`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.CurrentDimension) .</span><span class="sxs-lookup"><span data-stu-id="0409c-179">Furthermore, the current dimension, useful for *Toggle* and *Multi-Dimension* modes, can be accessed via [`Interactable.CurrentDimension`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.CurrentDimension).</span></span>

### <a name="interactable-profiles"></a><span data-ttu-id="0409c-180">Profili interagibili</span><span class="sxs-lookup"><span data-stu-id="0409c-180">Interactable profiles</span></span>

<span data-ttu-id="0409c-181">I *profili* sono elementi che creano una relazione tra un GameObject e un [tema visivo](../visual-themes.md).</span><span class="sxs-lookup"><span data-stu-id="0409c-181">*Profiles* are items that create a relationship between a GameObject and a [Visual Theme](../visual-themes.md).</span></span> <span data-ttu-id="0409c-182">Il profilo definisce il contenuto che verrà modificato da un tema quando [si verifica una modifica dello stato](#general-input-settings).</span><span class="sxs-lookup"><span data-stu-id="0409c-182">The profile defines what content will be manipulated by a theme when a [state change occurs](#general-input-settings).</span></span>

<span data-ttu-id="0409c-183">I temi funzionano in modo molto simile ai materiali.</span><span class="sxs-lookup"><span data-stu-id="0409c-183">Themes work a lot like materials.</span></span> <span data-ttu-id="0409c-184">Sono oggetti configurabili tramite script che contengono un elenco di proprietà che verranno assegnate a un oggetto in base allo stato corrente.</span><span class="sxs-lookup"><span data-stu-id="0409c-184">They are scriptable objects that contain a list of properties that will be assigned to an object based on the current state.</span></span> <span data-ttu-id="0409c-185">Anche i temi sono riutilizzabili e possono essere assegnati tra più oggetti UX di *interazione* .</span><span class="sxs-lookup"><span data-stu-id="0409c-185">Themes are also re-usable and can be assigned across multiple *Interactable* UX objects.</span></span>

<span data-ttu-id="0409c-186">**Reimposta in eliminazione**</span><span class="sxs-lookup"><span data-stu-id="0409c-186">**Reset On Destroy**</span></span>

<span data-ttu-id="0409c-187">I temi visivi modificano varie proprietà in un GameObject di destinazione, a seconda della classe e del tipo di motore di tema selezionato.</span><span class="sxs-lookup"><span data-stu-id="0409c-187">Visual themes modify various properties on a targeted GameObject, dependent on the class and type of theme engine selected.</span></span> <span data-ttu-id="0409c-188">Se *Reset on Destroy* è true quando il componente interactable viene eliminato definitivamente, il componente Reimposta tutte le proprietà modificate dai temi attivi ai valori originali.</span><span class="sxs-lookup"><span data-stu-id="0409c-188">If *Reset On Destroy* is true when the Interactable component is destroyed, the component will reset all modified properties from active themes to their original values.</span></span> <span data-ttu-id="0409c-189">In caso contrario, quando viene distrutta, il componente interactable lascerà le proprietà modificate così come sono.</span><span class="sxs-lookup"><span data-stu-id="0409c-189">Otherwise, when destroyed, the Interactable component will leave any modified properties as-is.</span></span> <span data-ttu-id="0409c-190">In quest'ultimo caso, l'ultimo stato dei valori verrà mantenuto a meno che non venga modificato da un altro componente esterno.</span><span class="sxs-lookup"><span data-stu-id="0409c-190">In this latter case, the last state of values will persist unless altered by another external component.</span></span> <span data-ttu-id="0409c-191">Il valore predefinito è false.</span><span class="sxs-lookup"><span data-stu-id="0409c-191">The default is false.</span></span>

<img src="../images/interactable/Profiles_Themes.png" width="450" alt="Profile theams">

## <a name="events"></a><span data-ttu-id="0409c-192">Eventi</span><span class="sxs-lookup"><span data-stu-id="0409c-192">Events</span></span>

<span data-ttu-id="0409c-193">Ogni componente *interagibile* ha un evento *OnClick* che viene attivato quando il componente viene semplicemente selezionato.</span><span class="sxs-lookup"><span data-stu-id="0409c-193">Every *Interactable* component has an *OnClick* event that fires when the component is simply selected.</span></span> <span data-ttu-id="0409c-194">Tuttavia, *è* possibile utilizzare Interoperable per rilevare eventi di input diversi da solo *OnClick*.</span><span class="sxs-lookup"><span data-stu-id="0409c-194">However, *Interactable* can be used to detect input events other than just *OnClick*.</span></span>

<span data-ttu-id="0409c-195">Fare clic sul pulsante *Aggiungi evento* per aggiungere un nuovo tipo di definizione del ricevitore di eventi.</span><span class="sxs-lookup"><span data-stu-id="0409c-195">Click the *Add Event* button to add a new type of Event Receiver definition.</span></span> <span data-ttu-id="0409c-196">Una volta aggiunto, selezionare il tipo di evento desiderato.</span><span class="sxs-lookup"><span data-stu-id="0409c-196">Once added, select the type of Event desired.</span></span>

![Esempio di eventi](../images/interactable/Events.png)<span data-ttu-id="0409c-198">)</span><span class="sxs-lookup"><span data-stu-id="0409c-198">)</span></span>

<span data-ttu-id="0409c-199">Esistono diversi tipi di destinatari di eventi per rispondere a diversi tipi di input.</span><span class="sxs-lookup"><span data-stu-id="0409c-199">There are different types of event receivers to respond to different types of input.</span></span> <span data-ttu-id="0409c-200">MRTK viene fornito con il seguente set di ricevitori predefiniti.</span><span class="sxs-lookup"><span data-stu-id="0409c-200">MRTK ships with the following set of receivers out-of-box.</span></span>

* [`InteractableAudioReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableAudioReceiver)
* [`InteractableOnClickReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnClickReceiver)
* [`InteractableOnFocusReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnFocusReceiver)
* [`InteractableOnGrabReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnGrabReceiver)
* [`InteractableOnHoldReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnHoldReceiver)
* [`InteractableOnPressReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnPressReceiver)
* [`InteractableOnToggleReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnToggleReceiver)
* [`InteractableOnTouchReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnTouchReceiver)

<span data-ttu-id="0409c-201">Per creare un ricevitore personalizzato, è possibile creare una nuova classe che estenda [`ReceiverBase`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBase) .</span><span class="sxs-lookup"><span data-stu-id="0409c-201">A custom receiver can be created by making a new class that extends [`ReceiverBase`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBase).</span></span>

![Esempio di ricevitore interruttore evento](../images/interactable/Event_toggle.png)

<span data-ttu-id="0409c-203">*Esempio di ricevitore di eventi di attivazione/disattivione*</span><span class="sxs-lookup"><span data-stu-id="0409c-203">*Example of a Toggle Event Receiver*</span></span>

### <a name="interactable-receivers"></a><span data-ttu-id="0409c-204">Ricevitori interagiscono</span><span class="sxs-lookup"><span data-stu-id="0409c-204">Interactable receivers</span></span>

 <span data-ttu-id="0409c-205">Il [`InteractableReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableReceiver) componente consente di definire gli eventi all'esterno del componente *interactabile* di origine.</span><span class="sxs-lookup"><span data-stu-id="0409c-205">The [`InteractableReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableReceiver) component allows for events to be defined outside of the source *Interactable* component.</span></span> <span data-ttu-id="0409c-206">*InteractableReceiver* resterà in ascolto di un tipo di evento filtrato generato da un altro *interactable*.</span><span class="sxs-lookup"><span data-stu-id="0409c-206">The *InteractableReceiver* will listen for a filtered event type fired by another *Interactable*.</span></span> <span data-ttu-id="0409c-207">Se la proprietà *interagibile* non viene assegnata direttamente, la proprietà dell' *ambito di ricerca* definisce la direzione in cui *InteractableReceiver* è in ascolto per gli eventi che si trova su se stesso, in un elemento padre o in un GameObject figlio.</span><span class="sxs-lookup"><span data-stu-id="0409c-207">If the *Interactable* property is not directly assigned, then the *Search Scope* property defines the direction the *InteractableReceiver* listens for events which is either on itself, in a parent, or in a child GameObject.</span></span>

<span data-ttu-id="0409c-208">[`InteractableReceiverList`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableReceiverList) funziona in modo simile, ma per un elenco di eventi corrispondenti.</span><span class="sxs-lookup"><span data-stu-id="0409c-208">[`InteractableReceiverList`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableReceiverList) acts in a similar fashion but for a list of matching events.</span></span>

<img src="../images/interactable/InteractableReceiver.png" width="450" alt="Interactable reciver">

### <a name="create-custom-events"></a><span data-ttu-id="0409c-209">Creazione di eventi personalizzati</span><span class="sxs-lookup"><span data-stu-id="0409c-209">Create custom events</span></span>

<span data-ttu-id="0409c-210">Analogamente ai [temi visivi](../visual-themes.md#custom-theme-engines), gli eventi possono essere estesi per rilevare qualsiasi modello di stato o per esporre la funzionalità.</span><span class="sxs-lookup"><span data-stu-id="0409c-210">Like [Visual Themes](../visual-themes.md#custom-theme-engines), events can be extended to detect any state pattern or to expose functionality.</span></span>

<span data-ttu-id="0409c-211">Gli eventi personalizzati possono essere creati in due modi principali:</span><span class="sxs-lookup"><span data-stu-id="0409c-211">Custom events can be created in two main ways:</span></span>

1) <span data-ttu-id="0409c-212">Estendere la [`ReceiverBase`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBase) classe per creare un evento personalizzato che sarà visualizzato nell'elenco a discesa dei tipi di evento.</span><span class="sxs-lookup"><span data-stu-id="0409c-212">Extend the [`ReceiverBase`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBase) class to create a custom event that will show up in the dropdown list of event types.</span></span> <span data-ttu-id="0409c-213">Per impostazione predefinita viene fornito un evento Unity, ma è possibile aggiungere altri eventi Unity oppure è possibile impostare l'evento in modo da nascondere gli eventi Unity.</span><span class="sxs-lookup"><span data-stu-id="0409c-213">A Unity event is provided by default, but additional Unity events can be added or the event can be set to hide Unity events.</span></span> <span data-ttu-id="0409c-214">Questa funzionalità consente a una finestra di progettazione di collaborare con un tecnico di un progetto per creare un evento personalizzato che la finestra di progettazione può configurare nell'editor.</span><span class="sxs-lookup"><span data-stu-id="0409c-214">This functionality allows a designer to work with an engineer on a project to create a custom event that the designer can setup in the editor.</span></span>

1) <span data-ttu-id="0409c-215">Estendere la [`ReceiverBaseMonoBehavior`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBaseMonoBehavior) classe per creare un componente evento completamente personalizzato che può risiedere in  un altro oggetto.</span><span class="sxs-lookup"><span data-stu-id="0409c-215">Extend the [`ReceiverBaseMonoBehavior`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBaseMonoBehavior) class to create a completely custom event component that can reside on the *Interactable* or another object.</span></span> <span data-ttu-id="0409c-216">Il [`ReceiverBaseMonoBehavior`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBaseMonoBehavior) fa riferimento a *interactable* per rilevare le modifiche di stato.</span><span class="sxs-lookup"><span data-stu-id="0409c-216">The [`ReceiverBaseMonoBehavior`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBaseMonoBehavior) will reference the *Interactable* to detect state changes.</span></span>

#### <a name="example-of-extending-receiverbase"></a><span data-ttu-id="0409c-217">Esempio di estensione `ReceiverBase`</span><span class="sxs-lookup"><span data-stu-id="0409c-217">Example of extending `ReceiverBase`</span></span>

<span data-ttu-id="0409c-218">La [`CustomInteractablesReceiver`](xref:Microsoft.MixedReality.Toolkit.UI) classe Visualizza informazioni sullo stato di un' *interfaccia interactabile* ed è un esempio di creazione di un ricevitore di eventi personalizzato.</span><span class="sxs-lookup"><span data-stu-id="0409c-218">The [`CustomInteractablesReceiver`](xref:Microsoft.MixedReality.Toolkit.UI) class displays status information about an *Interactable* and is an example of how to create a custom Event Receiver.</span></span>

```c#
public CustomInteractablesReceiver(UnityEvent ev) : base(ev, "CustomEvent")
{
    HideUnityEvents = true; // hides Unity events in the receiver - meant to be code only
}
```

<span data-ttu-id="0409c-219">I metodi seguenti sono utili per eseguire l'override o l'implementazione durante la creazione di un ricevitore di eventi personalizzato.</span><span class="sxs-lookup"><span data-stu-id="0409c-219">The following methods are useful to override/implement when creating a custom Event Receiver.</span></span> <span data-ttu-id="0409c-220">[`ReceiverBase.OnUpdate()`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBase) è un metodo astratto che può essere utilizzato per rilevare le transizioni/modelli di stato.</span><span class="sxs-lookup"><span data-stu-id="0409c-220">[`ReceiverBase.OnUpdate()`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBase) is an abstract method that can be used to detect state patterns/transitions.</span></span> <span data-ttu-id="0409c-221">Inoltre, i [`ReceiverBase.OnVoiceCommand()`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBase) [`ReceiverBase.OnClick()`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBase) metodi e sono utili per la creazione di una logica di evento personalizzata quando si seleziona *interactabile* .</span><span class="sxs-lookup"><span data-stu-id="0409c-221">Furthermore, the [`ReceiverBase.OnVoiceCommand()`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBase) and [`ReceiverBase.OnClick()`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBase) methods are useful for creating custom event logic when the *Interactable* is selected.</span></span>

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

##### <a name="displaying-custom-event-receiver-fields-in-the-inspector"></a><span data-ttu-id="0409c-222">Visualizzazione dei campi del ricevitore di eventi personalizzati nel controllo</span><span class="sxs-lookup"><span data-stu-id="0409c-222">Displaying custom event receiver fields in the inspector</span></span>

<span data-ttu-id="0409c-223">Gli script *ReceiverBase* usano [`InspectorField`](xref:Microsoft.MixedReality.Toolkit.Utilities.Editor.InspectorField) gli attributi per esporre le proprietà personalizzate nel controllo.</span><span class="sxs-lookup"><span data-stu-id="0409c-223">*ReceiverBase* scripts use [`InspectorField`](xref:Microsoft.MixedReality.Toolkit.Utilities.Editor.InspectorField) attributes to expose custom properties in the inspector.</span></span> <span data-ttu-id="0409c-224">Di seguito è riportato un esempio di Vector3, una proprietà personalizzata con le informazioni sull'etichetta e la descrizione comando.</span><span class="sxs-lookup"><span data-stu-id="0409c-224">Here's an example of Vector3, a custom property with tooltip and label information.</span></span> <span data-ttu-id="0409c-225">Questa proprietà viene visualizzata come configurabile nel controllo quando è selezionato *un GameObject* interoperabile e il tipo di *ricevitore di eventi* associato è stato aggiunto.</span><span class="sxs-lookup"><span data-stu-id="0409c-225">This property will show up as configurable in the inspector when an *Interactable* GameObject is selected and has the associated *Event Receiver* type added.</span></span>

```c#
[InspectorField(Label = "<Property label>",Tooltip = "<Insert tooltip info>",Type = InspectorField.FieldTypes.Vector3)]
public Vector3 EffectOffset = Vector3.zero;
```

## <a name="how-to-use-interactable"></a><span data-ttu-id="0409c-226">Come usare interactable</span><span class="sxs-lookup"><span data-stu-id="0409c-226">How to use Interactable</span></span>

### <a name="building-a-simple-button"></a><span data-ttu-id="0409c-227">Creazione di un pulsante semplice</span><span class="sxs-lookup"><span data-stu-id="0409c-227">Building a simple button</span></span>

<span data-ttu-id="0409c-228">È possibile creare un pulsante semplice aggiungendo il componente *Interactabile* a un GameObject configurato per la ricezione di eventi di input.</span><span class="sxs-lookup"><span data-stu-id="0409c-228">One can create a simple button by adding the *Interactable* component to a GameObject that is configured to receive input events.</span></span> <span data-ttu-id="0409c-229">Può avere un Collider o un elemento figlio per ricevere input.</span><span class="sxs-lookup"><span data-stu-id="0409c-229">It can have a collider on it or on a child to receive input.</span></span> <span data-ttu-id="0409c-230">Se si usa l'interfaccia *interagibile* con un GameObject basato sull'interfaccia utente di Unity, deve trovarsi sotto il GameObject Canvas.</span><span class="sxs-lookup"><span data-stu-id="0409c-230">If using *Interactable* with a Unity UI based GameObjects, it should be under the Canvas GameObject.</span></span>

<span data-ttu-id="0409c-231">Prendere il pulsante più avanti creando un nuovo profilo, assegnando il GameObject stesso e creando un nuovo tema.</span><span class="sxs-lookup"><span data-stu-id="0409c-231">Take the button one step further, by creating a new profile, assigning the GameObject itself and creating a new theme.</span></span> <span data-ttu-id="0409c-232">Inoltre, utilizzare l'evento *OnClick* per eseguire un'operazione.</span><span class="sxs-lookup"><span data-stu-id="0409c-232">Furthermore, use the *OnClick* event to make something happen.</span></span>

> [!NOTE]
> <span data-ttu-id="0409c-233">Per rendere la pressione di un [pulsante](button.md) è necessario il [`PressableButton`](xref:Microsoft.MixedReality.Toolkit.UI.PressableButton) componente.</span><span class="sxs-lookup"><span data-stu-id="0409c-233">Making a [button pressable](button.md) requires the [`PressableButton`](xref:Microsoft.MixedReality.Toolkit.UI.PressableButton) component.</span></span> <span data-ttu-id="0409c-234">Inoltre, il [`PhysicalPressEventRouter`](xref:Microsoft.MixedReality.Toolkit.PhysicalPressEventRouter) componente è necessario per l'imbuto degli eventi di pressione nel componente *interactabile* .</span><span class="sxs-lookup"><span data-stu-id="0409c-234">Additionally, the [`PhysicalPressEventRouter`](xref:Microsoft.MixedReality.Toolkit.PhysicalPressEventRouter) component is needed to funnel press events to the *Interactable* component.</span></span>

### <a name="creating-toggle-and-multi-dimension-buttons"></a><span data-ttu-id="0409c-235">Creazione di pulsanti di attivazione/disattivazione e MULTIDIMENSIONE</span><span class="sxs-lookup"><span data-stu-id="0409c-235">Creating toggle and multi-dimension buttons</span></span>

#### <a name="toggle-button"></a><span data-ttu-id="0409c-236">Interruttore</span><span class="sxs-lookup"><span data-stu-id="0409c-236">Toggle button</span></span>

<span data-ttu-id="0409c-237">Per impostare un pulsante in modo da attivarlo, impostare il [`Selection Mode`](xref:Microsoft.MixedReality.Toolkit.UI.SelectionModes) campo su tipo `Toggle` .</span><span class="sxs-lookup"><span data-stu-id="0409c-237">To make a button Toggle-able, change the the [`Selection Mode`](xref:Microsoft.MixedReality.Toolkit.UI.SelectionModes) field to type `Toggle`.</span></span> <span data-ttu-id="0409c-238">Nella sezione *profili* viene aggiunto un nuovo tema attivato per ogni profilo che viene usato quando il controllo *interattivo* è attivato.</span><span class="sxs-lookup"><span data-stu-id="0409c-238">In the *Profiles* section, a new toggled theme is added for each profile that is used when the *Interactable* is toggled on.</span></span>

<span data-ttu-id="0409c-239">Mentre l'oggetto [`SelectionMode`](xref:Microsoft.MixedReality.Toolkit.UI.SelectionModes) è impostato su interruttore, è  possibile utilizzare la casella di controllo attivato per impostare il valore predefinito del controllo in fase di inizializzazione in fase di esecuzione.</span><span class="sxs-lookup"><span data-stu-id="0409c-239">While the [`SelectionMode`](xref:Microsoft.MixedReality.Toolkit.UI.SelectionModes) is set to Toggle, the *IsToggled* check box can be used to set the default value of the control at runtime initialization.</span></span>

<span data-ttu-id="0409c-240">*CanSelect* significa che *interagisce* può passare dall' *esterno* a *on* mentre il *CanDeselect* indica l'inverso.</span><span class="sxs-lookup"><span data-stu-id="0409c-240">*CanSelect* means the *Interactable* can go from *off* to *on* while the *CanDeselect* means the inverse.</span></span>

![Esempio di profilatura di elementi visivi](../images/interactable/Profile_toggle.png)

<span data-ttu-id="0409c-242">Gli sviluppatori possono utilizzare le [`SetToggled`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) [`IsToggled`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) interfacce e per ottenere/impostare lo stato di attivazione/disinstallazione di un codice *interattivo* tramite codice.</span><span class="sxs-lookup"><span data-stu-id="0409c-242">Developers can utilize the [`SetToggled`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) and [`IsToggled`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) interfaces to get/set the toggle state of an *Interactable* via code.</span></span>

```c#
// If using SelectionMode = Toggle (i.e Dimensions == 2)

// Make the Interactable selected and toggled on
myInteractable.IsToggled = true;

// Get whether the Interactable is selected or not
bool isSelected = myInteractable.IsToggled;
```

##### <a name="toggle-button-collection"></a><span data-ttu-id="0409c-243">Imposta/Rimuovi pulsante</span><span class="sxs-lookup"><span data-stu-id="0409c-243">Toggle button collection</span></span>

<span data-ttu-id="0409c-244">È comune avere un elenco di pulsanti di attivazione, in cui solo uno può essere attivo in qualsiasi momento, anche noto come un set radiale o pulsanti di opzione e così via.</span><span class="sxs-lookup"><span data-stu-id="0409c-244">It is common to have a list of toggle buttons where only one can be active at any given time, also known as a radial set or radio buttons etc.</span></span>

<span data-ttu-id="0409c-245">Utilizzare il [`InteractableToggleCollection`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableToggleCollection) componente per abilitare questa funzionalità.</span><span class="sxs-lookup"><span data-stu-id="0409c-245">Use the [`InteractableToggleCollection`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableToggleCollection) component to enable this functionality.</span></span> <span data-ttu-id="0409c-246">Questo controllo garantisce che venga attivato un solo *Interactabile* in un determinato momento.</span><span class="sxs-lookup"><span data-stu-id="0409c-246">This control ensures only one *Interactable* is toggled on at any given time.</span></span> <span data-ttu-id="0409c-247">Il *RadialSet* (assets/MRTK/SDK/features/UX/interactable/prefabrics/RadialSet. prefabbricate) è anche un ottimo punto di partenza.</span><span class="sxs-lookup"><span data-stu-id="0409c-247">The *RadialSet* (Assets/MRTK/SDK/Features/UX/Interactable/Prefabs/RadialSet.prefab) is also a great starting point out-of-box.</span></span>

<span data-ttu-id="0409c-248">Per creare un gruppo di pulsanti radiali personalizzati:</span><span class="sxs-lookup"><span data-stu-id="0409c-248">To create a custom radial button group:</span></span>

1) <span data-ttu-id="0409c-249">Crea più GameObject/pulsanti *Interagiscabili*</span><span class="sxs-lookup"><span data-stu-id="0409c-249">Create multiple *Interactable* GameObjects/buttons</span></span>
1) <span data-ttu-id="0409c-250">Impostare ogni *interagire* con *SelectionMode* = interruttore, *CanSelect* = true e *CanDeselect* = false</span><span class="sxs-lookup"><span data-stu-id="0409c-250">Set each *Interactable* with *SelectionMode* = Toggle, *CanSelect* = true, and *CanDeselect* = false</span></span>
1) <span data-ttu-id="0409c-251">Creare un GameObject padre vuoto su tutti i *Interactables* e aggiungere il componente *InteractableToggleCollection*</span><span class="sxs-lookup"><span data-stu-id="0409c-251">Create an empty parent GameObject over all the *Interactables* and add the *InteractableToggleCollection* component</span></span>
1) <span data-ttu-id="0409c-252">Aggiungere tutti *Interactables* a *ToggleList* in *InteractableToggleCollection*</span><span class="sxs-lookup"><span data-stu-id="0409c-252">Add all *Interactables* to the *ToggleList* on the *InteractableToggleCollection*</span></span>
1) <span data-ttu-id="0409c-253">Impostare la proprietà *InteractableToggleCollection. CurrentIndex* per determinare quale pulsante è selezionato per impostazione predefinita all'avvio</span><span class="sxs-lookup"><span data-stu-id="0409c-253">Set the *InteractableToggleCollection.CurrentIndex* property to determine which button is selected by default at start</span></span>

<img src="../images/interactable/InteractableToggleCollection.png" width="450" alt="Toggle collection">

#### <a name="multi-dimensional-button"></a><span data-ttu-id="0409c-254">Pulsante multidimensionale</span><span class="sxs-lookup"><span data-stu-id="0409c-254">Multi-dimensional button</span></span>

<span data-ttu-id="0409c-255">La modalità di selezione MULTIDIMENSIONE viene utilizzata per creare pulsanti sequenziali o un pulsante che include più di due passaggi, ad esempio il controllo della velocità con tre valori, veloce (1x), più veloce (2x) o più veloce (3x).</span><span class="sxs-lookup"><span data-stu-id="0409c-255">Multi-Dimension selection mode is used to create sequential buttons, or a button that has more than two steps, like controlling speed with three values, Fast (1x), Faster (2x) or Fastest (3x).</span></span>

<span data-ttu-id="0409c-256">Con le dimensioni che costituiscono un valore numerico, è possibile aggiungere fino a 9 temi per controllare l'etichetta di testo o la trama del pulsante per ogni impostazione di velocità, usando un tema diverso per ogni passaggio.</span><span class="sxs-lookup"><span data-stu-id="0409c-256">With dimensions being a numeric value, up to 9 themes can be added to control the text label or texture of the button for each speed setting, using a different theme for each of step.</span></span>

<span data-ttu-id="0409c-257">Ogni evento Click anticiperà la `DimensionIndex` di 1 in fase di esecuzione fino a quando non `Dimensions` viene raggiunto il valore.</span><span class="sxs-lookup"><span data-stu-id="0409c-257">Every click event will advance the `DimensionIndex` by 1 at runtime until the `Dimensions` value is reached.</span></span> <span data-ttu-id="0409c-258">Il ciclo verrà quindi reimpostato su 0.</span><span class="sxs-lookup"><span data-stu-id="0409c-258">Then the cycle will reset to 0.</span></span>

![Esempio di profilo multidimensionale](../images/interactable/Profile_multiDimensions.png)

<span data-ttu-id="0409c-260">Gli sviluppatori possono valutare [`DimensionIndex`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) per determinare la dimensione attualmente attiva.</span><span class="sxs-lookup"><span data-stu-id="0409c-260">Developers can assess the [`DimensionIndex`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) to determine which dimension is currently active.</span></span>

```c#
// If using SelectionMode = Multi-dimension (i.e Dimensions >= 3)

//Access the current DimensionIndex
int currentDimension = myInteractable.CurrentDimension;

//Set the current DimensionIndex to 2
myInteractable.CurrentDimension = 2;

// Promote Dimension to next level
myInteractable.IncreaseDimension();
```

### <a name="create-interactable-at-runtime"></a><span data-ttu-id="0409c-261">Crea interactabile in fase di esecuzione</span><span class="sxs-lookup"><span data-stu-id="0409c-261">Create Interactable at runtime</span></span>

<span data-ttu-id="0409c-262">È possibile aggiungere facilmente *interactable* a qualsiasi GameObject in fase di esecuzione.</span><span class="sxs-lookup"><span data-stu-id="0409c-262">*Interactable* can be easily added to any GameObject at runtime.</span></span> <span data-ttu-id="0409c-263">Nell'esempio seguente viene illustrato come assegnare un profilo con un [tema visivo](../visual-themes.md).</span><span class="sxs-lookup"><span data-stu-id="0409c-263">The following example demonstrates how to assign a profile with a [visual theme](../visual-themes.md).</span></span>

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

### <a name="interactable-events-via-code"></a><span data-ttu-id="0409c-264">Eventi interactabili tramite codice</span><span class="sxs-lookup"><span data-stu-id="0409c-264">Interactable events via code</span></span>

<span data-ttu-id="0409c-265">È possibile aggiungere un'azione all'evento di base [`Interactable.OnClick`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.OnClick) tramite codice con l'esempio seguente.</span><span class="sxs-lookup"><span data-stu-id="0409c-265">One can add an action to the base [`Interactable.OnClick`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.OnClick) event via code with the following example.</span></span>

```c#
public static void AddOnClick(Interactable interactable)
{
    interactable.OnClick.AddListener(() => Debug.Log("Interactable clicked"));
}
```

<span data-ttu-id="0409c-266">Usare la [`Interactable.AddReceiver<T>()`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) funzione per aggiungere i ricevitori di eventi in modo dinamico in fase di esecuzione.</span><span class="sxs-lookup"><span data-stu-id="0409c-266">Use the [`Interactable.AddReceiver<T>()`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) function to add event receivers dynamically at runtime.</span></span>

<span data-ttu-id="0409c-267">Il codice di esempio riportato di seguito illustra come aggiungere un [InteractableOnFocusReceiver](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnFocusReceiver), che rimane in attesa di invio/uscita dello stato attivo, nonché definire il codice dell'azione da eseguire quando vengono attivate le istanze dell'evento.</span><span class="sxs-lookup"><span data-stu-id="0409c-267">The example code below demonstrates how to add an [InteractableOnFocusReceiver](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnFocusReceiver), which listens for focus enter/exit, and furthermore define action code to perform when the event instances fire.</span></span>

```c#
public static void AddFocusEvents(Interactable interactable)
{
    var onFocusReceiver = interactable.AddReceiver<InteractableOnFocusReceiver>();

    onFocusReceiver.OnFocusOn.AddListener(() => Debug.Log("Focus on"));
    onFocusReceiver.OnFocusOff.AddListener(() => Debug.Log("Focus off"));
}
```

<span data-ttu-id="0409c-268">Il codice di esempio riportato di seguito illustra come aggiungere un [InteractableOnToggleReceiver](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnFocusReceiver), che rimane in attesa delle transizioni di stato selezionate/deselezionate in *Interactables* abilitati per l'attivazione/disattivazione e definisce inoltre il codice dell'azione da eseguire quando vengono attivate le istanze di evento.</span><span class="sxs-lookup"><span data-stu-id="0409c-268">The example code below demonstrates how to add an [InteractableOnToggleReceiver](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnFocusReceiver), which listens for selected/deselected state transitions on toggle-able *Interactables*, and furthermore defines action code to perform when the event instances fire.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="0409c-269">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="0409c-269">See also</span></span>

* [<span data-ttu-id="0409c-270">Temi visivi</span><span class="sxs-lookup"><span data-stu-id="0409c-270">Visual Themes</span></span>](../visual-themes.md)
* [<span data-ttu-id="0409c-271">Azioni di input</span><span class="sxs-lookup"><span data-stu-id="0409c-271">Input Actions</span></span>](../input/input-actions.md)
* [<span data-ttu-id="0409c-272">Comandi vocali</span><span class="sxs-lookup"><span data-stu-id="0409c-272">Speech Commands</span></span>](../input/speech.md)
* [<span data-ttu-id="0409c-273">Pulsanti</span><span class="sxs-lookup"><span data-stu-id="0409c-273">Buttons</span></span>](button.md)
* [<span data-ttu-id="0409c-274">Shader standard MRTK</span><span class="sxs-lookup"><span data-stu-id="0409c-274">MRTK Standard Shader</span></span>](../rendering/MRTK-standard-shader.md)

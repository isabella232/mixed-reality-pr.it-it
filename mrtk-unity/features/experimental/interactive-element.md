---
title: Interactiveelement
description: Documentazione di interactiveelement MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 02/22/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, elemento interattivo, interactable
ms.openlocfilehash: 0526dbe88fad14ba4f4dfe41abe889a74b21c796
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/03/2021
ms.locfileid: "101781599"
---
# <a name="interactive-element-experimental"></a><span data-ttu-id="ca8a6-104">Interactive (elemento) [sperimentale]</span><span class="sxs-lookup"><span data-stu-id="ca8a6-104">Interactive Element [Experimental]</span></span>

<span data-ttu-id="ca8a6-105">Un punto di ingresso centralizzato semplificato al sistema di input MRTK.</span><span class="sxs-lookup"><span data-stu-id="ca8a6-105">A simplified centralized entry point to the MRTK input system.</span></span> <span data-ttu-id="ca8a6-106">Contiene i metodi di gestione dello stato, la gestione degli eventi e la logica di impostazione dello stato per gli Stati di interazione principali.</span><span class="sxs-lookup"><span data-stu-id="ca8a6-106">Contains state management methods, event management and the state setting logic for Core Interaction States.</span></span>

<span data-ttu-id="ca8a6-107">L'elemento interattivo è una funzionalità sperimentale supportata in Unity 2019,3 e, in quanto usa una funzionalità nuova per Unity 2019,3: [Serialize Reference](https://docs.unity3d.com/ScriptReference/SerializeReference.html).</span><span class="sxs-lookup"><span data-stu-id="ca8a6-107">Interactive Element is an experimental feature supported in Unity 2019.3 and up as it utilizes a capability new to Unity 2019.3: [Serialize Reference](https://docs.unity3d.com/ScriptReference/SerializeReference.html).</span></span>

### <a name="interactive-element-inspector"></a><span data-ttu-id="ca8a6-108">Controllo elemento interattivo</span><span class="sxs-lookup"><span data-stu-id="ca8a6-108">Interactive Element Inspector</span></span>

<span data-ttu-id="ca8a6-109">In modalità di riproduzione, il controllo dell'elemento interattivo fornisce un feedback visivo che indica se lo stato corrente è attivo o meno.</span><span class="sxs-lookup"><span data-stu-id="ca8a6-109">During play mode, the Interactive Element inspector provides visual feedback that indicates whether or not the current state is active.</span></span> <span data-ttu-id="ca8a6-110">Se uno stato è attivo, verrà evidenziato con un colore ciano.</span><span class="sxs-lookup"><span data-stu-id="ca8a6-110">If a state is active, it will be highlighted with a cyan color.</span></span>  <span data-ttu-id="ca8a6-111">Se lo stato non è attivo, il colore non viene modificato.</span><span class="sxs-lookup"><span data-stu-id="ca8a6-111">If the state is not active, the color is not changed.</span></span> <span data-ttu-id="ca8a6-112">I numeri accanto agli Stati del controllo sono i valori di stato, se lo stato è attivo, il valore è 1, se lo stato non è attivo, il valore è 0.</span><span class="sxs-lookup"><span data-stu-id="ca8a6-112">The numbers next to the states in the inspector are the state values, if the state is active then the value is 1, if the state is not active the value is 0.</span></span>

![InteractiveElementAddCoreState](../images/interactive-element/InEditor/Gifs/InspectorHighlightEditor.gif)

## <a name="core-states"></a><span data-ttu-id="ca8a6-114">Stati principali</span><span class="sxs-lookup"><span data-stu-id="ca8a6-114">Core States</span></span>

<span data-ttu-id="ca8a6-115">L'elemento interattivo contiene gli Stati di base e supporta l'aggiunta di [stati personalizzati](#custom-states).</span><span class="sxs-lookup"><span data-stu-id="ca8a6-115">Interactive Element contains core states and supports the addition of [custom states](#custom-states).</span></span>  <span data-ttu-id="ca8a6-116">Uno stato principale è quello in cui è già presente la logica di impostazione dello stato definita in `BaseInteractiveElement` .</span><span class="sxs-lookup"><span data-stu-id="ca8a6-116">A core state is one that already has the state setting logic defined in `BaseInteractiveElement`.</span></span> <span data-ttu-id="ca8a6-117">Di seguito è riportato un elenco degli stati principali di core basati su input:</span><span class="sxs-lookup"><span data-stu-id="ca8a6-117">The following is a list of the current input-driven core states:</span></span> 

### <a name="current-core-states"></a><span data-ttu-id="ca8a6-118">Stati Core correnti</span><span class="sxs-lookup"><span data-stu-id="ca8a6-118">Current Core States</span></span>

- [<span data-ttu-id="ca8a6-119">Default</span><span class="sxs-lookup"><span data-stu-id="ca8a6-119">Default</span></span>](#default-state) 

<span data-ttu-id="ca8a6-120">Stati di core per l'interazione near and lontano:</span><span class="sxs-lookup"><span data-stu-id="ca8a6-120">Near and Far Interaction Core States:</span></span>
- [<span data-ttu-id="ca8a6-121">Lo stato attivo</span><span class="sxs-lookup"><span data-stu-id="ca8a6-121">Focus</span></span>](#focus-state) 

<span data-ttu-id="ca8a6-122">Stati principali di interazione near:</span><span class="sxs-lookup"><span data-stu-id="ca8a6-122">Near Interaction Core States:</span></span>

- [<span data-ttu-id="ca8a6-123">Stato attivo vicino</span><span class="sxs-lookup"><span data-stu-id="ca8a6-123">Focus Near</span></span>](#focus-near-state)
- [<span data-ttu-id="ca8a6-124">Tocco</span><span class="sxs-lookup"><span data-stu-id="ca8a6-124">Touch</span></span>](#touch-state)

<span data-ttu-id="ca8a6-125">Stati principali per l'interazione tra i componenti:</span><span class="sxs-lookup"><span data-stu-id="ca8a6-125">Far Interaction Core States:</span></span>
- [<span data-ttu-id="ca8a6-126">Stato attivo</span><span class="sxs-lookup"><span data-stu-id="ca8a6-126">Focus Far</span></span>](#focus-far-state)
- [<span data-ttu-id="ca8a6-127">Seleziona a lungo</span><span class="sxs-lookup"><span data-stu-id="ca8a6-127">Select Far</span></span>](#select-far-state)

<span data-ttu-id="ca8a6-128">Altri stati principali:</span><span class="sxs-lookup"><span data-stu-id="ca8a6-128">Other Core States:</span></span>
- [<span data-ttu-id="ca8a6-129">Clicked</span><span class="sxs-lookup"><span data-stu-id="ca8a6-129">Clicked</span></span>](#clicked-state)
- [<span data-ttu-id="ca8a6-130">Attivare e disattivare</span><span class="sxs-lookup"><span data-stu-id="ca8a6-130">Toggle On and Toggle Off</span></span>](#toggle-on-and-toggle-off-state)
- [<span data-ttu-id="ca8a6-131">Parola chiave Speech</span><span class="sxs-lookup"><span data-stu-id="ca8a6-131">Speech Keyword</span></span>](#speech-keyword-state)

### <a name="how-to-add-a-core-state-via-inspector"></a><span data-ttu-id="ca8a6-132">Come aggiungere uno stato principale tramite Inspector</span><span class="sxs-lookup"><span data-stu-id="ca8a6-132">How to Add a Core State via Inspector</span></span>

1. <span data-ttu-id="ca8a6-133">Passare a **Aggiungi stato principale** nell'elemento Inspector per Interactive.</span><span class="sxs-lookup"><span data-stu-id="ca8a6-133">Navigate to **Add Core State** in the inspector for Interactive Element.</span></span>

    ![InteractiveElementAddCoreState](../images/interactive-element/InEditor/InteractiveElementAddCoreState.png)


1. <span data-ttu-id="ca8a6-135">Selezionare il pulsante **Seleziona stato** per scegliere lo stato principale da aggiungere.</span><span class="sxs-lookup"><span data-stu-id="ca8a6-135">Select the **Select State** button to choose the core state to add.</span></span> <span data-ttu-id="ca8a6-136">Gli Stati nel menu sono ordinati in base al tipo di interazione.</span><span class="sxs-lookup"><span data-stu-id="ca8a6-136">The states in the menu are sorted by interaction type.</span></span>

    ![InteractiveElementAddCoreStateSelectState](../images/interactive-element/InEditor/InteractiveElementAddCoreStateSelectState.png)

1. <span data-ttu-id="ca8a6-138">Aprire la finestra di dialogo di configurazione dell'evento per visualizzare gli eventi e le proprietà associati allo stato.</span><span class="sxs-lookup"><span data-stu-id="ca8a6-138">Open the Event Configuration foldout to view the events and properties associated with the state.</span></span>

    ![InteractiveElementAddCoreStateSelectStateEventConfig](../images/interactive-element/InEditor/InteractiveElementAddCoreStateSelectStateEventConfig.png)


### <a name="how-to-add-a-core-state-via-script"></a><span data-ttu-id="ca8a6-140">Come aggiungere uno stato principale tramite script</span><span class="sxs-lookup"><span data-stu-id="ca8a6-140">How to Add a Core State via Script</span></span>

<span data-ttu-id="ca8a6-141">Usare il `AddNewState(stateName)` metodo per aggiungere uno stato principale.</span><span class="sxs-lookup"><span data-stu-id="ca8a6-141">Use the `AddNewState(stateName)` method to add a core state.</span></span> <span data-ttu-id="ca8a6-142">Per un elenco dei nomi di stato principali disponibili, usare l' `CoreInteractionState` enumerazione.</span><span class="sxs-lookup"><span data-stu-id="ca8a6-142">For a list of the available core state names, use the `CoreInteractionState` enum.</span></span>

```c#
// Add by name or add by CoreInteractionState enum to string

interactiveElement.AddNewState("SelectFar");

interactiveElement.AddNewState(CoreInteractionState.SelectFar.ToString());
```

### <a name="states-internal-structure"></a><span data-ttu-id="ca8a6-143">Struttura interna degli Stati</span><span class="sxs-lookup"><span data-stu-id="ca8a6-143">States Internal Structure</span></span> 

<span data-ttu-id="ca8a6-144">Gli Stati nell'elemento interattivo sono di tipo `InteractionState` .</span><span class="sxs-lookup"><span data-stu-id="ca8a6-144">The states in Interactive Element are of type `InteractionState`.</span></span>  <span data-ttu-id="ca8a6-145">Un oggetto `InteractionState` contiene le proprietà seguenti:</span><span class="sxs-lookup"><span data-stu-id="ca8a6-145">An `InteractionState` contains the following properties:</span></span>

- <span data-ttu-id="ca8a6-146">**Nome**: nome dello stato.</span><span class="sxs-lookup"><span data-stu-id="ca8a6-146">**Name**: The name of the state.</span></span>
- <span data-ttu-id="ca8a6-147">**Value**: valore di stato.</span><span class="sxs-lookup"><span data-stu-id="ca8a6-147">**Value**: The state value.</span></span>  <span data-ttu-id="ca8a6-148">Se lo stato è on, il valore dello stato è 1.</span><span class="sxs-lookup"><span data-stu-id="ca8a6-148">If the state is on, the state value is 1.</span></span> <span data-ttu-id="ca8a6-149">Se lo stato è disattivato, il valore di stato è 0.</span><span class="sxs-lookup"><span data-stu-id="ca8a6-149">If the state is off, the state value is 0.</span></span>
- <span data-ttu-id="ca8a6-150">**Attivo**: indica se lo stato è attualmente attivo o meno.</span><span class="sxs-lookup"><span data-stu-id="ca8a6-150">**Active**: Whether or not the state is currently active.</span></span> <span data-ttu-id="ca8a6-151">Il valore della proprietà attiva è true quando lo stato è on, false se lo stato è off.</span><span class="sxs-lookup"><span data-stu-id="ca8a6-151">The value for the Active property is true when the state is on, false if the state is off.</span></span> 
- <span data-ttu-id="ca8a6-152">**Tipo** di interazione: il tipo di interazione di uno stato è il tipo di interazione a cui è destinato uno stato.</span><span class="sxs-lookup"><span data-stu-id="ca8a6-152">**Interaction Type**: The Interaction Type of a state is the type of interaction a state is intended for.</span></span> 
  - <span data-ttu-id="ca8a6-153">`None`: Non supporta alcuna forma di interazione di input.</span><span class="sxs-lookup"><span data-stu-id="ca8a6-153">`None`: Does not support any form of input interaction.</span></span>
  - <span data-ttu-id="ca8a6-154">`Near`: Supporto per l'interazione near.</span><span class="sxs-lookup"><span data-stu-id="ca8a6-154">`Near`: Near interaction support.</span></span> <span data-ttu-id="ca8a6-155">L'input viene considerato vicino all'interazione quando una mano articolata ha un contatto diretto con un altro oggetto gioco, ovvero la posizione in cui la mano articolata è vicina alla posizione dell'oggetto gioco nello spazio globale.</span><span class="sxs-lookup"><span data-stu-id="ca8a6-155">Input is considered near interaction when an articulated hand has direct contact with another game object, i.e. the position the articulated hand is close to the position of the game object in world space.</span></span>
  - <span data-ttu-id="ca8a6-156">`Far`: Supporto per l'interazione.</span><span class="sxs-lookup"><span data-stu-id="ca8a6-156">`Far`: Far interaction support.</span></span> <span data-ttu-id="ca8a6-157">L'input è considerato un'interazione molto quando non è necessario un contatto diretto con l'oggetto gioco.</span><span class="sxs-lookup"><span data-stu-id="ca8a6-157">Input is considered far interaction when direct contact with the game object is not required.</span></span> <span data-ttu-id="ca8a6-158">Ad esempio, l'input tramite raggio controller o sguardo è considerato un input di interazione molto lungo.</span><span class="sxs-lookup"><span data-stu-id="ca8a6-158">For example, input via controller ray or gaze is considered far interaction input.</span></span>
  - <span data-ttu-id="ca8a6-159">`NearAndFar`: Include sia il supporto per l'interazione vicino che l'altro.</span><span class="sxs-lookup"><span data-stu-id="ca8a6-159">`NearAndFar`: Encompasses both near and far interaction support.</span></span> 
  - <span data-ttu-id="ca8a6-160">`Other`: Supporto dell'interazione indipendente del puntatore.</span><span class="sxs-lookup"><span data-stu-id="ca8a6-160">`Other`: Pointer independent interaction support.</span></span>
- <span data-ttu-id="ca8a6-161">**Configurazione evento**: la configurazione dell'evento per uno stato è il punto di ingresso del profilo degli eventi serializzati.</span><span class="sxs-lookup"><span data-stu-id="ca8a6-161">**Event Configuration**: The event configuration for a state is the serialized events profile entry point.</span></span> 

<span data-ttu-id="ca8a6-162">Tutte queste proprietà vengono impostate internamente nell' `State Manager` elemento contenuto in interattivo.</span><span class="sxs-lookup"><span data-stu-id="ca8a6-162">All of these properties are set internally in the `State Manager` contained in Interactive Element.</span></span> <span data-ttu-id="ca8a6-163">Per la modifica degli Stati, usare i metodi helper seguenti:</span><span class="sxs-lookup"><span data-stu-id="ca8a6-163">For modification of states use the following helper methods:</span></span>

<span data-ttu-id="ca8a6-164">**Metodi helper per l'impostazione dello stato**</span><span class="sxs-lookup"><span data-stu-id="ca8a6-164">**State Setting Helper Methods**</span></span>

```c# 
// Get the InteractionState
interactiveElement.GetState("StateName");

// Set a state value to 1/on
interactiveElement.SetStateOn("StateName");

// Set a state value to 0/off
interactiveElement.SetStateOff("StateName");

// Check if a state is present in the state list
interactiveElement.IsStatePresent("StateName");

// Check whether or not a state is active
interactiveElement.IsStateActive("StateName");

// Add a new state to the state list
interactiveElement.AddNewState("StateName");

// Remove a state from the state list
interactiveElement.RemoveState("StateName");
```

<span data-ttu-id="ca8a6-165">Il recupero della configurazione dell'evento di uno stato è specifico per lo stato stesso.</span><span class="sxs-lookup"><span data-stu-id="ca8a6-165">Getting the event configuration of a state is specific to the state itself.</span></span> <span data-ttu-id="ca8a6-166">Ogni stato principale ha un tipo di configurazione di evento specifico, illustrato di seguito sotto le sezioni che descrivono ogni stato principale.</span><span class="sxs-lookup"><span data-stu-id="ca8a6-166">Each core state has a specific event configuration type which is outlined below under the sections describing each core state.</span></span>

<span data-ttu-id="ca8a6-167">Di seguito è riportato un esempio generalizzato di recupero della configurazione di un evento di stato:</span><span class="sxs-lookup"><span data-stu-id="ca8a6-167">Here is a generalized example of getting a state's event configuration:</span></span>

```c#
// T varies depending on the core state - the specific T's are specified under each of the core state sections
T stateNameEvents = interactiveElement.GetStateEvents<T>("StateName");
```

### <a name="default-state"></a><span data-ttu-id="ca8a6-168">Stato predefinito</span><span class="sxs-lookup"><span data-stu-id="ca8a6-168">Default State</span></span>

<span data-ttu-id="ca8a6-169">Lo stato predefinito è sempre presente in un elemento interattivo.</span><span class="sxs-lookup"><span data-stu-id="ca8a6-169">The Default state is always present on an Interactive Element.</span></span>  <span data-ttu-id="ca8a6-170">Questo stato sarà attivo solo quando tutti gli altri Stati non sono attivi.</span><span class="sxs-lookup"><span data-stu-id="ca8a6-170">This state will be active only when all other states are not active.</span></span>  <span data-ttu-id="ca8a6-171">Se un altro stato diventa attivo, lo stato predefinito verrà impostato su off internamente.</span><span class="sxs-lookup"><span data-stu-id="ca8a6-171">If any other state becomes active, then the Default state will be set to off internally.</span></span> 

<span data-ttu-id="ca8a6-172">Un elemento interattivo viene inizializzato con gli Stati di attivazione e predefiniti presenti nell'elenco degli Stati.</span><span class="sxs-lookup"><span data-stu-id="ca8a6-172">An Interactive Element is initialized with the Default and Focus states present in the state list.</span></span> <span data-ttu-id="ca8a6-173">Lo stato predefinito deve sempre essere presente nell'elenco degli Stati.</span><span class="sxs-lookup"><span data-stu-id="ca8a6-173">The Default state always needs to be present in the state list.</span></span> 

#### <a name="getting-default-state-events"></a><span data-ttu-id="ca8a6-174">Recupero degli eventi di stato predefiniti</span><span class="sxs-lookup"><span data-stu-id="ca8a6-174">Getting Default State Events</span></span>

<span data-ttu-id="ca8a6-175">Tipo di configurazione dell'evento per lo stato predefinito: `StateEvents`</span><span class="sxs-lookup"><span data-stu-id="ca8a6-175">Event configuration type for the Default State: `StateEvents`</span></span>

```c#
StateEvents defaultEvents = interactiveElement.GetStateEvents<StateEvents>("Default");

defaultEvents.OnStateOn.AddListener(() =>
{
    Debug.Log($"{gameObject.name} Default State On");
});

defaultEvents.OnStateOff.AddListener(() =>
{
    Debug.Log($"{gameObject.name} Default State Off");
});
```

### <a name="focus-state"></a><span data-ttu-id="ca8a6-176">Stato attivo</span><span class="sxs-lookup"><span data-stu-id="ca8a6-176">Focus State</span></span>

<span data-ttu-id="ca8a6-177">Lo stato attivo è uno stato di interazione vicino e lontano che può essere considerato come la realtà mista equivalente al passaggio del mouse.</span><span class="sxs-lookup"><span data-stu-id="ca8a6-177">The Focus state is a near and far interaction state that can be thought of as the mixed reality equivalent to hover.</span></span> <span data-ttu-id="ca8a6-178">Il fattore di distinzione tra l'interazione quasi e la distanza per lo stato attivo è il tipo di puntatore attivo corrente.</span><span class="sxs-lookup"><span data-stu-id="ca8a6-178">The distinguishing factor between near and far interaction for the Focus state is the current active pointer type.</span></span>  <span data-ttu-id="ca8a6-179">Se il tipo di puntatore per lo stato attivo è il puntatore poke, l'interazione viene considerata quasi interazione.</span><span class="sxs-lookup"><span data-stu-id="ca8a6-179">If the pointer type for the Focus state is the Poke Pointer, then the interaction is considered near interaction.</span></span>  <span data-ttu-id="ca8a6-180">Se il puntatore primario non è il puntatore poke, l'interazione è considerata un'interazione di gran lunga.</span><span class="sxs-lookup"><span data-stu-id="ca8a6-180">If the primary pointer is not the Poke Pointer, then the interaction is considered far interaction.</span></span> <span data-ttu-id="ca8a6-181">Per impostazione predefinita, lo stato attivo è presente nell'elemento interattivo.</span><span class="sxs-lookup"><span data-stu-id="ca8a6-181">The Focus state is present in Interactive Element by default.</span></span>

<span data-ttu-id="ca8a6-182"> 
 Comportamento ![ dello stato attivo FocusStateEditor](../images/interactive-element/InEditor/Gifs/FocusStateEditor.gif)</span><span class="sxs-lookup"><span data-stu-id="ca8a6-182">**Focus State Behavior**
![FocusStateEditor](../images/interactive-element/InEditor/Gifs/FocusStateEditor.gif)</span></span> 

<span data-ttu-id="ca8a6-183">Controllo stato di **messa a fuoco** 
 ![ FocusStateInspector](../images/interactive-element/InEditor/FocusStateInspector.png)</span><span class="sxs-lookup"><span data-stu-id="ca8a6-183">**Focus State Inspector**
![FocusStateInspector](../images/interactive-element/InEditor/FocusStateInspector.png)</span></span>

#### <a name="getting-focus-state-events"></a><span data-ttu-id="ca8a6-184">Recupero degli eventi dello stato attivo</span><span class="sxs-lookup"><span data-stu-id="ca8a6-184">Getting Focus State Events</span></span>

<span data-ttu-id="ca8a6-185">Tipo di configurazione evento per lo stato attivo: `FocusEvents`</span><span class="sxs-lookup"><span data-stu-id="ca8a6-185">Event configuration type for the Focus State: `FocusEvents`</span></span>

```c#
FocusEvents focusEvents = interactiveElement.GetStateEvents<FocusEvents>("Focus");

focusEvents.OnFocusOn.AddListener((pointerEventData) =>
{
    Debug.Log($"{gameObject.name} Focus On");
});

focusEvents.OnFocusOff.AddListener((pointerEventData) =>
{
    Debug.Log($"{gameObject.name} Focus Off");
});
```

#### <a name="focus-near-vs-focus-far-behavior"></a><span data-ttu-id="ca8a6-186">Concentrati sul comportamento estremo rispetto a Visual Studio</span><span class="sxs-lookup"><span data-stu-id="ca8a6-186">Focus Near vs Focus Far Behavior</span></span> 

![FocusNearFocusFar](../images/interactive-element/InEditor/Gifs/FocusNearFocusFar.gif)

### <a name="focus-near-state"></a><span data-ttu-id="ca8a6-188">Stato attivo vicino allo stato</span><span class="sxs-lookup"><span data-stu-id="ca8a6-188">Focus Near State</span></span>

<span data-ttu-id="ca8a6-189">Lo stato attivo near viene impostato quando viene generato un evento di messa a fuoco e il puntatore principale è il puntatore poke, un'indicazione di near Interaction.</span><span class="sxs-lookup"><span data-stu-id="ca8a6-189">The Focus Near state is set when a focus event is raised and the primary pointer is the Poke pointer, an indication of near interaction.</span></span> 

<span data-ttu-id="ca8a6-190">**Stato attivo vicino al comportamento** 
 ![ dello stato FocusNearStateEditor](../images/interactive-element/InEditor/Gifs/FocusNearStateEditor.gif)</span><span class="sxs-lookup"><span data-stu-id="ca8a6-190">**Focus Near State Behavior**
![FocusNearStateEditor](../images/interactive-element/InEditor/Gifs/FocusNearStateEditor.gif)</span></span> 

<span data-ttu-id="ca8a6-191">**Stato attivo vicino a controllo stato** 
 ![ FocusNearStateInspector](../images/interactive-element/InEditor/FocusNearStateInspector.png)</span><span class="sxs-lookup"><span data-stu-id="ca8a6-191">**Focus Near State Inspector**
![FocusNearStateInspector](../images/interactive-element/InEditor/FocusNearStateInspector.png)</span></span>

#### <a name="getting-focusnear-state-events"></a><span data-ttu-id="ca8a6-192">Recupero degli eventi di stato FocusNear</span><span class="sxs-lookup"><span data-stu-id="ca8a6-192">Getting FocusNear State Events</span></span>

<span data-ttu-id="ca8a6-193">Tipo di configurazione dell'evento per lo stato FocusNear: `FocusEvents`</span><span class="sxs-lookup"><span data-stu-id="ca8a6-193">Event configuration type for the FocusNear State: `FocusEvents`</span></span>

```c#
FocusEvents focusNearEvents = interactiveElement.GetStateEvents<FocusEvents>("FocusNear");

focusNearEvents.OnFocusOn.AddListener((pointerEventData) =>
{
    Debug.Log($"{gameObject.name} Near Interaction Focus On");
});

focusNearEvents.OnFocusOff.AddListener((pointerEventData) =>
{
    Debug.Log($"{gameObject.name} Near Interaction Focus Off");
});
```

### <a name="focus-far-state"></a><span data-ttu-id="ca8a6-194">Stato di disattivazione</span><span class="sxs-lookup"><span data-stu-id="ca8a6-194">Focus Far State</span></span>

<span data-ttu-id="ca8a6-195">Lo stato di disattivazione dello stato attivo viene impostato quando il puntatore primario non è il puntatore poke.</span><span class="sxs-lookup"><span data-stu-id="ca8a6-195">The Focus Far state is set when the primary pointer is not the Poke pointer.</span></span>  <span data-ttu-id="ca8a6-196">Ad esempio, il puntatore del raggio del controller predefinito e il puntatore GGV (sguardo, movimento, voce) sono considerati puntatori di interazione.</span><span class="sxs-lookup"><span data-stu-id="ca8a6-196">For example, the default controller ray pointer and the GGV (Gaze, Gesture, Voice) pointer are considered far interaction pointers.</span></span>

<span data-ttu-id="ca8a6-197">Comportamento dello stato di **disattivazione** 
 ![ FocusFarStateEditor](../images/interactive-element/InEditor/Gifs/FocusFarStateEditor.gif)</span><span class="sxs-lookup"><span data-stu-id="ca8a6-197">**Focus Far State Behavior**
![FocusFarStateEditor](../images/interactive-element/InEditor/Gifs/FocusFarStateEditor.gif)</span></span>

<span data-ttu-id="ca8a6-198">Controllo dello stato **attivo per lo stato** 
 ![ FocusFarStateInspector](../images/interactive-element/InEditor/FocusFarStateInspector.png)</span><span class="sxs-lookup"><span data-stu-id="ca8a6-198">**Focus Far State Inspector**
![FocusFarStateInspector](../images/interactive-element/InEditor/FocusFarStateInspector.png)</span></span>

#### <a name="getting-focus-far-state-events"></a><span data-ttu-id="ca8a6-199">Recupero degli eventi di stato attivo</span><span class="sxs-lookup"><span data-stu-id="ca8a6-199">Getting Focus Far State Events</span></span>

<span data-ttu-id="ca8a6-200">Tipo di configurazione dell'evento per lo stato FocusFar: `FocusEvents`</span><span class="sxs-lookup"><span data-stu-id="ca8a6-200">Event configuration type for the FocusFar State: `FocusEvents`</span></span>

```c#
FocusEvents focusFarEvents = interactiveElement.GetStateEvents<FocusEvents>("FocusFar");

focusFarEvents.OnFocusOn.AddListener((pointerEventData) =>
{
    Debug.Log($"{gameObject.name} Far Interaction Focus On");
});

focusFarEvents.OnFocusOff.AddListener((pointerEventData) =>
{
    Debug.Log($"{gameObject.name} Far Interaction Focus Off");
});
```

### <a name="touch-state"></a><span data-ttu-id="ca8a6-201">Stato tocco</span><span class="sxs-lookup"><span data-stu-id="ca8a6-201">Touch State</span></span>

<span data-ttu-id="ca8a6-202">Lo stato del tocco è uno stato near Interaction impostato quando una mano articolata tocca direttamente l'oggetto.</span><span class="sxs-lookup"><span data-stu-id="ca8a6-202">The Touch state is a near interaction state that is set when an articulated hand touches the object directly.</span></span>  <span data-ttu-id="ca8a6-203">Un tocco diretto significa che il dito dell'indice della mano articolata è molto vicino alla posizione globale dell'oggetto.</span><span class="sxs-lookup"><span data-stu-id="ca8a6-203">A direct touch means that the articulated hand's index finger is very close to the world position of the object.</span></span> <span data-ttu-id="ca8a6-204">Per impostazione predefinita, un `NearInteractionTouchableVolume` componente viene associato all'oggetto se lo stato tocco viene aggiunto all'elenco degli Stati.</span><span class="sxs-lookup"><span data-stu-id="ca8a6-204">By default, a `NearInteractionTouchableVolume` component is attached to the object if the Touch state is added to the the state list.</span></span>  <span data-ttu-id="ca8a6-205">La presenza di un  `NearInteractionTouchableVolume` `NearInteractionTouchable` componente o è necessaria per rilevare gli eventi di tocco.</span><span class="sxs-lookup"><span data-stu-id="ca8a6-205">The presence of a  `NearInteractionTouchableVolume` or `NearInteractionTouchable` component is required for detecting Touch events.</span></span>  <span data-ttu-id="ca8a6-206">La differenza tra `NearInteractionTouchableVolume` e `NearInteractionTouchable` è che `NearInteractionTouchableVolume` rileva un tocco basato sul Collider dell'oggetto e `NearInteractionTouchable` rileva il tocco in un'area definita di un piano.</span><span class="sxs-lookup"><span data-stu-id="ca8a6-206">The difference between `NearInteractionTouchableVolume` and `NearInteractionTouchable` is that `NearInteractionTouchableVolume` detects a touch based on the collider of the object and `NearInteractionTouchable`detects touch within a defined area of a plane.</span></span>

<span data-ttu-id="ca8a6-207">Comportamento dello stato di **tocco** 
 ![ TouchStateEditor](../images/interactive-element/InEditor/Gifs/TouchStateEditor.gif)</span><span class="sxs-lookup"><span data-stu-id="ca8a6-207">**Touch State Behavior**
![TouchStateEditor](../images/interactive-element/InEditor/Gifs/TouchStateEditor.gif)</span></span>

<span data-ttu-id="ca8a6-208">Controllo dello stato di **tocco** 
 ![ TouchStateInspector](../images/interactive-element/InEditor/TouchStateInspector.png)</span><span class="sxs-lookup"><span data-stu-id="ca8a6-208">**Touch State Inspector**
![TouchStateInspector](../images/interactive-element/InEditor/TouchStateInspector.png)</span></span>

#### <a name="getting-touch-state-events"></a><span data-ttu-id="ca8a6-209">Recupero degli eventi di stato tocco</span><span class="sxs-lookup"><span data-stu-id="ca8a6-209">Getting Touch State Events</span></span>

<span data-ttu-id="ca8a6-210">Tipo di configurazione dell'evento per lo stato di tocco: `TouchEvents`</span><span class="sxs-lookup"><span data-stu-id="ca8a6-210">Event configuration type for the Touch State: `TouchEvents`</span></span>

```c#
TouchEvents touchEvents = interactiveElement.GetStateEvents<TouchEvents>("Touch");

touchEvents.OnTouchStarted.AddListener((touchData) =>
{
    Debug.Log($"{gameObject.name} Touch Started");
});

touchEvents.OnTouchCompleted.AddListener((touchData) =>
{
    Debug.Log($"{gameObject.name} Touch Completed");
});

touchEvents.OnTouchUpdated.AddListener((touchData) =>
{
    Debug.Log($"{gameObject.name} Touch Updated");
});
```

### <a name="select-far-state"></a><span data-ttu-id="ca8a6-211">Selezione stato lontano</span><span class="sxs-lookup"><span data-stu-id="ca8a6-211">Select Far State</span></span>

<span data-ttu-id="ca8a6-212">Lo stato di selezione della distanza è la `IMixedRealityPointerHandler` superficie.</span><span class="sxs-lookup"><span data-stu-id="ca8a6-212">The Select Far state is the `IMixedRealityPointerHandler` surfaced.</span></span>  <span data-ttu-id="ca8a6-213">Questo stato è uno stato di interazione molto lungo che rileva il clic di interazione di tipo esponente (TAP) ed è in grado di usare puntatori di interazione di gran lunga come il puntatore del raggio del controller predefinito o il puntatore GGV.</span><span class="sxs-lookup"><span data-stu-id="ca8a6-213">This state is a far interaction state that detects far interaction click (air-tap) and holds through the use of far interaction pointers such as the default controller ray pointer or the GGV pointer.</span></span>  <span data-ttu-id="ca8a6-214">Per lo stato Select-out è presente un'opzione nell'applicazione di chiusura della configurazione dell'evento denominata `Global` .</span><span class="sxs-lookup"><span data-stu-id="ca8a6-214">The Select Far state has an option under the event configuration foldout named `Global`.</span></span> <span data-ttu-id="ca8a6-215">Se `Global` è true, l'oggetto `IMixedRealityPointerHandler` viene registrato come gestore di input globale.</span><span class="sxs-lookup"><span data-stu-id="ca8a6-215">If `Global` is true, then the `IMixedRealityPointerHandler` is registered as a global input handler.</span></span>  <span data-ttu-id="ca8a6-216">Lo stato attivo su un oggetto non è necessario per attivare gli eventi di sistema di input se un gestore viene registrato come globale.</span><span class="sxs-lookup"><span data-stu-id="ca8a6-216">Focus on an object is not required to trigger input system events if a handler is registered as global.</span></span>  <span data-ttu-id="ca8a6-217">Se, ad esempio, un utente desidera conoscere ogni volta che viene eseguito il movimento di tocco/selezione dell'aria indipendentemente dall'oggetto nello stato attivo, impostare `Global` su true.</span><span class="sxs-lookup"><span data-stu-id="ca8a6-217">For example, if a user wants to know anytime the air-tap/select gesture is performed regardless of the object in focus, set `Global` to true.</span></span> 

<span data-ttu-id="ca8a6-218">**Selezionare il comportamento** 
 ![ dello stato di distanti SelectFarStateEditor](../images/interactive-element/InEditor/Gifs/SelectFarStateEditor.gif)</span><span class="sxs-lookup"><span data-stu-id="ca8a6-218">**Select Far State Behavior**
![SelectFarStateEditor](../images/interactive-element/InEditor/Gifs/SelectFarStateEditor.gif)</span></span>

<span data-ttu-id="ca8a6-219">**Selezionare il controllo** 
 ![ di stato lontano SelectFarStateInspector](../images/interactive-element/InEditor/SelectFarStateInspector.png)</span><span class="sxs-lookup"><span data-stu-id="ca8a6-219">**Select Far State Inspector**
![SelectFarStateInspector](../images/interactive-element/InEditor/SelectFarStateInspector.png)</span></span>

#### <a name="getting-select-far-state-events"></a><span data-ttu-id="ca8a6-220">Recupero degli eventi di selezione dello stato</span><span class="sxs-lookup"><span data-stu-id="ca8a6-220">Getting Select Far State Events</span></span>

<span data-ttu-id="ca8a6-221">Tipo di configurazione dell'evento per lo stato SelectFar: `SelectFarEvents`</span><span class="sxs-lookup"><span data-stu-id="ca8a6-221">Event configuration type for the SelectFar State: `SelectFarEvents`</span></span>

```c#
SelectFarEvents selectFarEvents = interactiveElement.GetStateEvents<SelectFarEvents>("SelectFar");

selectFarEvents.OnSelectUp.AddListener((pointerEventData) =>
{
    Debug.Log($"{gameObject.name} Far Interaction Pointer Up");
});

selectFarEvents.OnSelectDown.AddListener((pointerEventData) =>
{
    Debug.Log($"{gameObject.name} Far Interaction Pointer Down");
});

selectFarEvents.OnSelectHold.AddListener((pointerEventData) =>
{
    Debug.Log($"{gameObject.name} Far Interaction Pointer Hold");
});

selectFarEvents.OnSelectClicked.AddListener((pointerEventData) =>
{
    Debug.Log($"{gameObject.name} Far Interaction Pointer Clicked");
});
```

### <a name="clicked-state"></a><span data-ttu-id="ca8a6-222">Stato selezionato</span><span class="sxs-lookup"><span data-stu-id="ca8a6-222">Clicked State</span></span>

<span data-ttu-id="ca8a6-223">Per impostazione predefinita, lo stato selezionato viene attivato da un clic per l'interazione con la distanza (selezione dello stato).</span><span class="sxs-lookup"><span data-stu-id="ca8a6-223">The Clicked state is triggered by a far interaction click (Select Far state) by default.</span></span>  <span data-ttu-id="ca8a6-224">Questo stato viene attivato internamente, richiama l'evento OnClicked e quindi viene immediatamente disattivato.</span><span class="sxs-lookup"><span data-stu-id="ca8a6-224">This state is internally switched to on, invokes the OnClicked event and then is immediately switched to off.</span></span> 

> [!NOTE]
> <span data-ttu-id="ca8a6-225">Il feedback visivo nel controllo basato sull'attività di stato non è presente per lo stato selezionato perché è attivato e quindi disattivato immediatamente.</span><span class="sxs-lookup"><span data-stu-id="ca8a6-225">The visual feedback in the inspector based on state activity is not present for the Clicked state because it is switched on and then off immediately.</span></span> 

<span data-ttu-id="ca8a6-226"> 
 Comportamento ![ stato selezionato ClickedStateEditor](../images/interactive-element/InEditor/Gifs/ClickedStateEditor.gif)</span><span class="sxs-lookup"><span data-stu-id="ca8a6-226">**Clicked State Behavior**
![ClickedStateEditor](../images/interactive-element/InEditor/Gifs/ClickedStateEditor.gif)</span></span>

<span data-ttu-id="ca8a6-227"> 
 Controllo ![ stato selezionato ClickedStateInspector](../images/interactive-element/InEditor/ClickedStateInspector.png)</span><span class="sxs-lookup"><span data-stu-id="ca8a6-227">**Clicked State Inspector**
![ClickedStateInspector](../images/interactive-element/InEditor/ClickedStateInspector.png)</span></span>

<span data-ttu-id="ca8a6-228">**Esempio di stato vicino e molto selezionato**</span><span class="sxs-lookup"><span data-stu-id="ca8a6-228">**Near and Far Clicked State Example**</span></span>  
<span data-ttu-id="ca8a6-229">Lo stato selezionato può essere attivato tramite punti di ingresso aggiuntivi tramite il `interactiveElement.TriggerClickedState()` metodo.</span><span class="sxs-lookup"><span data-stu-id="ca8a6-229">The clicked state can be triggered through additional entry points using the `interactiveElement.TriggerClickedState()` method.</span></span>  <span data-ttu-id="ca8a6-230">Ad esempio, se un utente vuole un tocco near Interaction per attivare un clic su un oggetto, aggiunge il `TriggerClickedState()` metodo come listener nello stato touch.</span><span class="sxs-lookup"><span data-stu-id="ca8a6-230">For example, if a user wants a near interaction touch to trigger a click on an object as well, then they would add the `TriggerClickedState()` method as a listener in the touch state.</span></span>   

![NearFarClickedState](../images/interactive-element/InEditor/Gifs/NearFarClickedState.gif)

#### <a name="getting-clicked-state-events"></a><span data-ttu-id="ca8a6-232">Recupero degli eventi di stato selezionato</span><span class="sxs-lookup"><span data-stu-id="ca8a6-232">Getting Clicked State Events</span></span>

<span data-ttu-id="ca8a6-233">Tipo di configurazione evento per lo stato selezionato: `ClickedEvents`</span><span class="sxs-lookup"><span data-stu-id="ca8a6-233">Event configuration type for the Clicked State: `ClickedEvents`</span></span>

```c#
ClickedEvents clickedEvent = interactiveElement.GetStateEvents<ClickedEvents>("Clicked");

clickedEvent.OnClicked.AddListener(() =>
{
    Debug.Log($"{gameObject.name} Clicked");
});
```

### <a name="toggle-on-and-toggle-off-state"></a><span data-ttu-id="ca8a6-234">Attivare e disattivare lo stato</span><span class="sxs-lookup"><span data-stu-id="ca8a6-234">Toggle On and Toggle Off state</span></span>

<span data-ttu-id="ca8a6-235">Gli Stati di attivazione e disattivazione sono una coppia ed è necessario che entrambi siano presenti per il comportamento di attivazione/disattivazione.</span><span class="sxs-lookup"><span data-stu-id="ca8a6-235">The Toggle On and Toggle Off states are a pair and both need to be present for toggle behavior.</span></span>  <span data-ttu-id="ca8a6-236">Per impostazione predefinita, gli Stati di attivazione e disattivazione e disattivazione vengono attivati tramite un clic di interazione con la distanza (selezione dello stato lontano).</span><span class="sxs-lookup"><span data-stu-id="ca8a6-236">By default, the Toggle On and Toggle Off states are triggered through a far interaction click (Select Far state).</span></span>  <span data-ttu-id="ca8a6-237">Per impostazione predefinita, lo stato di attivazione/disattivazione è attivo all'inizio, ovvero l'interruttore verrà inizializzato su disattivato.</span><span class="sxs-lookup"><span data-stu-id="ca8a6-237">By default, the Toggle Off state is active on start, meaning that the toggle will be initialized to off.</span></span>  <span data-ttu-id="ca8a6-238">Se un utente desidera che lo stato di attivazione/disattivazione sia attivo all'avvio, quindi nello stato di attivazione/disattivazione impostato su `IsSelectedOnStart` true.</span><span class="sxs-lookup"><span data-stu-id="ca8a6-238">If a user wants the Toggle On state to be active on start, then in the Toggle On state set `IsSelectedOnStart` to true.</span></span>

<span data-ttu-id="ca8a6-239">**ToggleOn e disattivare il comportamento** 
 ![ dello stato ToggleOnToggleOffStateEditor](../images/interactive-element/InEditor/Gifs/ToggleOnToggleOffStateEditor.gif)</span><span class="sxs-lookup"><span data-stu-id="ca8a6-239">**ToggleOn and Toggle Off State Behavior**
![ToggleOnToggleOffStateEditor](../images/interactive-element/InEditor/Gifs/ToggleOnToggleOffStateEditor.gif)</span></span>

<span data-ttu-id="ca8a6-240">**ToggleOn e Disattiva controllo stato** 
 ![ ToggleOnToggleOffStateInspector](../images/interactive-element/InEditor/ToggleOnToggleOffStateInspector.png)</span><span class="sxs-lookup"><span data-stu-id="ca8a6-240">**ToggleOn and Toggle Off State Inspector**
![ToggleOnToggleOffStateInspector](../images/interactive-element/InEditor/ToggleOnToggleOffStateInspector.png)</span></span>

<span data-ttu-id="ca8a6-241">**Esempio per gli Stati di attivazione o distanti**</span><span class="sxs-lookup"><span data-stu-id="ca8a6-241">**Near and Far Toggle States Example**</span></span>  
<span data-ttu-id="ca8a6-242">Analogamente allo stato selezionato, l'impostazione dello stato di attivazione/disinstallazione può avere più punti di ingresso usando il `interactiveElement.SetToggleStates()` metodo.</span><span class="sxs-lookup"><span data-stu-id="ca8a6-242">Similar to the Clicked state, toggle state setting can have multiple entry points using the `interactiveElement.SetToggleStates()` method.</span></span> <span data-ttu-id="ca8a6-243">Se, ad esempio, un utente desidera toccare come punto di ingresso aggiuntivo per impostare gli Stati di attivazione, aggiunge il `SetToggleStates()` metodo a uno degli eventi nello stato di tocco.</span><span class="sxs-lookup"><span data-stu-id="ca8a6-243">For example, if a user wants touch as an additional entry point to set the toggle states, then they add the `SetToggleStates()` method to one of the events in the Touch state.</span></span> 

![NearFarToggleStates](../images/interactive-element/InEditor/Gifs/NearFarToggleStates.gif)

#### <a name="getting-toggle-on-and-toggle-off-state-events"></a><span data-ttu-id="ca8a6-245">Ottenere l'interruttore e disattivare gli eventi di stato</span><span class="sxs-lookup"><span data-stu-id="ca8a6-245">Getting Toggle On and Toggle Off State Events</span></span>

<span data-ttu-id="ca8a6-246">Tipo di configurazione dell'evento per lo stato ToggleOn: `ToggleOnEvents`</span><span class="sxs-lookup"><span data-stu-id="ca8a6-246">Event configuration type for the ToggleOn State: `ToggleOnEvents`</span></span>  
<span data-ttu-id="ca8a6-247">Tipo di configurazione dell'evento per lo stato ToggleOff: `ToggleOffEvents`</span><span class="sxs-lookup"><span data-stu-id="ca8a6-247">Event configuration type for the ToggleOff State: `ToggleOffEvents`</span></span>

```c#
// Toggle On Events
ToggleOnEvents toggleOnEvent = interactiveElement.GetStateEvents<ToggleOnEvents>("ToggleOn");

toggleOnEvent.OnToggleOn.AddListener(() =>
{
    Debug.Log($"{gameObject.name} Toggled On");
});

// Toggle Off Events
ToggleOffEvents toggleOffEvent = interactiveElement.GetStateEvents<ToggleOffEvents>("ToggleOff");

toggleOffEvent.OnToggleOff.AddListener(() =>
{
    Debug.Log($"{gameObject.name} Toggled Off");
});
```

### <a name="speech-keyword-state"></a><span data-ttu-id="ca8a6-248">Stato parola chiave vocale</span><span class="sxs-lookup"><span data-stu-id="ca8a6-248">Speech Keyword State</span></span>

<span data-ttu-id="ca8a6-249">Lo stato della parola chiave vocale è in ascolto per le parole chiave definite nel profilo di sintesi vocale della realtà mista.</span><span class="sxs-lookup"><span data-stu-id="ca8a6-249">The Speech Keyword state listens for the keywords defined in the Mixed Reality Speech Profile.</span></span> <span data-ttu-id="ca8a6-250">Qualsiasi nuova parola chiave deve essere registrata nel profilo del comando vocale prima del runtime (passaggi successivi).</span><span class="sxs-lookup"><span data-stu-id="ca8a6-250">Any new keyword MUST be registered in the speech command profile prior to runtime (steps below).</span></span> 

<span data-ttu-id="ca8a6-251">Comportamento stato parola **chiave vocale** 
 ![ SpeechKeywordStateEditor](../images/interactive-element/InEditor/Gifs/SpeechKeywordStateEditor.gif)</span><span class="sxs-lookup"><span data-stu-id="ca8a6-251">**Speech Keyword State Behavior**
![SpeechKeywordStateEditor](../images/interactive-element/InEditor/Gifs/SpeechKeywordStateEditor.gif)</span></span>

<span data-ttu-id="ca8a6-252">Controllo stato parola **chiave vocale** 
 ![ SpeechKeywordStateInspector](../images/interactive-element/InEditor/SpeechKeywordStateInspector.png)</span><span class="sxs-lookup"><span data-stu-id="ca8a6-252">**Speech Keyword State Inspector**
![SpeechKeywordStateInspector](../images/interactive-element/InEditor/SpeechKeywordStateInspector.png)</span></span>

> [!NOTE]
> <span data-ttu-id="ca8a6-253">Lo stato della parola chiave vocale è stato attivato nell'Editor premendo il tasto F5 nel gif precedente.</span><span class="sxs-lookup"><span data-stu-id="ca8a6-253">The Speech Keyword state was triggered in editor by pressing the F5 key in the gif above.</span></span> <span data-ttu-id="ca8a6-254">La configurazione nel test dell'editor per la sintesi vocale è illustrata nella procedura seguente.</span><span class="sxs-lookup"><span data-stu-id="ca8a6-254">Setting up in editor testing for speech is outlined the steps below.</span></span> 

#### <a name="how-to-register-a-speech-commandkeyword"></a><span data-ttu-id="ca8a6-255">Come registrare un comando/parola chiave vocale</span><span class="sxs-lookup"><span data-stu-id="ca8a6-255">How to Register a Speech Command/Keyword</span></span>

1. <span data-ttu-id="ca8a6-256">Selezionare l'oggetto gioco **MixedRealityToolkit**</span><span class="sxs-lookup"><span data-stu-id="ca8a6-256">Select the **MixedRealityToolkit** game object</span></span>

1. <span data-ttu-id="ca8a6-257">Selezionare **copia e Personalizza** il profilo corrente</span><span class="sxs-lookup"><span data-stu-id="ca8a6-257">Select **Copy and Customize** the current profile</span></span>

1. <span data-ttu-id="ca8a6-258">Passare alla sezione input e selezionare **clona** per abilitare la modifica del profilo di input.</span><span class="sxs-lookup"><span data-stu-id="ca8a6-258">Navigate to the Input section and select **Clone** to enable modification of the Input profile</span></span>

1. <span data-ttu-id="ca8a6-259">Scorrere verso il basso fino alla sezione voce del profilo di input e clonare il profilo vocale</span><span class="sxs-lookup"><span data-stu-id="ca8a6-259">Scroll down to the Speech section in the Input profile and clone the Speech Profile</span></span>

    ![SpeechKeywordProfileClone](../images/interactive-element/InEditor/SpeechKeywordProfileClone.png) 

1. <span data-ttu-id="ca8a6-261">Selezionare Aggiungi un nuovo comando vocale</span><span class="sxs-lookup"><span data-stu-id="ca8a6-261">Select Add a New Speech Command</span></span>

    ![SpeechKeywordStateEditor](../images/interactive-element/InEditor/SpeechKeywordProfileAddKeyword.png) 

1. <span data-ttu-id="ca8a6-263">Immettere la parola chiave New.</span><span class="sxs-lookup"><span data-stu-id="ca8a6-263">Enter the new keyword.</span></span> <span data-ttu-id="ca8a6-264">Facoltativo: modificare il codice in F5 (o un altro codice) per consentire il test nell'editor.</span><span class="sxs-lookup"><span data-stu-id="ca8a6-264">Optional: Change the KeyCode to F5 (or another KeyCode) to allow for testing in editor.</span></span> 

    ![SpeechKeywordProfileAddKeywordName](../images/interactive-element/InEditor/SpeechKeywordProfileAddKeywordName.png) 

1. <span data-ttu-id="ca8a6-266">Tornare alla finestra di dialogo di controllo dello stato delle parole chiave vocale degli elementi interattivi e selezionare **Aggiungi parola chiave**</span><span class="sxs-lookup"><span data-stu-id="ca8a6-266">Go back to the Interactive Element Speech Keyword state inspector and select **Add Keyword**</span></span> 

    ![SpeechKeywordAddKeyword](../images/interactive-element/InEditor/SpeechKeywordAddKeyword.png) 

    ![SpeechKeywordAddKeywordBlank](../images/interactive-element/InEditor/SpeechKeywordAddKeywordBlank.png) 

1. <span data-ttu-id="ca8a6-269">Immettere la nuova parola chiave appena registrata nel profilo vocale</span><span class="sxs-lookup"><span data-stu-id="ca8a6-269">Enter the new keyword that was just registered in the Speech Profile</span></span>

    ![SpeechKeywordAddKeyword](../images/interactive-element/InEditor/SpeechKeywordEnterKeyword.png) 


<span data-ttu-id="ca8a6-271">Per testare lo stato della parola chiave Speech nell'editor, premere il KeyCode definito nel passaggio 6 (F5) per simulare l'evento riconoscimento parola chiave vocale.</span><span class="sxs-lookup"><span data-stu-id="ca8a6-271">To test the Speech Keyword state in editor, press the KeyCode that was defined in step 6 (F5) to simulate the speech keyword recognized event.</span></span>

#### <a name="getting-speech-keyword-state-events"></a><span data-ttu-id="ca8a6-272">Recupero degli eventi di stato della parola chiave vocale</span><span class="sxs-lookup"><span data-stu-id="ca8a6-272">Getting Speech Keyword State Events</span></span>

<span data-ttu-id="ca8a6-273">Tipo di configurazione dell'evento per lo stato SpeechKeyword: `SpeechKeywordEvents`</span><span class="sxs-lookup"><span data-stu-id="ca8a6-273">Event configuration type for the SpeechKeyword State: `SpeechKeywordEvents`</span></span>

```c#
SpeechKeywordEvents speechKeywordEvents = interactiveElement.GetStateEvents<SpeechKeywordEvents>("SpeechKeyword");

speechKeywordEvents.OnAnySpeechKeywordRecognized.AddListener((speechEventData) =>
{
    Debug.Log($"{speechEventData.Command.Keyword} recognized");
});

// Get the "Change" Keyword event specifically
KeywordEvent keywordEvent = speechKeywordEvents.Keywords.Find((keyword) => keyword.Keyword == "Change");

keywordEvent.OnKeywordRecognized.AddListener(() =>
{ 
    Debug.Log("Change Keyword Recognized"); 
});
```

## <a name="custom-states"></a><span data-ttu-id="ca8a6-274">Stati personalizzati</span><span class="sxs-lookup"><span data-stu-id="ca8a6-274">Custom States</span></span>

### <a name="how-to-create-a-custom-state-via-inspector"></a><span data-ttu-id="ca8a6-275">Come creare uno stato personalizzato tramite Inspector</span><span class="sxs-lookup"><span data-stu-id="ca8a6-275">How to Create a Custom State via Inspector</span></span> 

<span data-ttu-id="ca8a6-276">Lo stato personalizzato creato tramite Inspector verrà inizializzato con la configurazione dell'evento di stato predefinito.</span><span class="sxs-lookup"><span data-stu-id="ca8a6-276">The custom state created via inspector will be initialized with the default state event configuration.</span></span> <span data-ttu-id="ca8a6-277">La configurazione dell'evento predefinito per uno stato personalizzato è di tipo `StateEvents` e contiene gli eventi OnStateOn e OnStateOff.</span><span class="sxs-lookup"><span data-stu-id="ca8a6-277">The default event configuration for a custom state is of type `StateEvents` and contains the OnStateOn and OnStateOff events.</span></span>

1. <span data-ttu-id="ca8a6-278">Passare a **Crea stato personalizzato** nell'elemento Inspector per l'elemento interattivo.</span><span class="sxs-lookup"><span data-stu-id="ca8a6-278">Navigate to **Create Custom State** in the inspector for Interactive Element.</span></span>
    
    ![InteractiveElementCreateCustomState](../images/interactive-element/InEditor/InteractiveElementCreateCustomState.png)

1. <span data-ttu-id="ca8a6-280">Immettere il nome del nuovo stato.</span><span class="sxs-lookup"><span data-stu-id="ca8a6-280">Enter the name of the new state.</span></span> <span data-ttu-id="ca8a6-281">Questo nome deve essere univoco e non può essere uguale a quello degli Stati core esistenti.</span><span class="sxs-lookup"><span data-stu-id="ca8a6-281">This name must be unique and cannot be the same as the existing core states.</span></span> 
    
    ![InteractiveElementCreateCustomStateName](../images/interactive-element/InEditor/InteractiveElementCreateCustomStateName.png)

1. <span data-ttu-id="ca8a6-283">Selezionare **Imposta nome stato** da aggiungere all'elenco degli Stati.</span><span class="sxs-lookup"><span data-stu-id="ca8a6-283">Select **Set State Name** to add to the state list.</span></span>
    
    ![InteractiveElementCreateCustomStateNameSet](../images/interactive-element/InEditor/InteractiveElementCreateCustomStateNameSet.png)

   <span data-ttu-id="ca8a6-285">Questo stato personalizzato viene inizializzato con la `StateEvents` configurazione dell'evento predefinita che contiene gli `OnStateOn` `OnStateOff` eventi e.</span><span class="sxs-lookup"><span data-stu-id="ca8a6-285">This custom state is initialized with the default `StateEvents` event configuration which contains the `OnStateOn` and `OnStateOff` events.</span></span> <span data-ttu-id="ca8a6-286">Per creare una configurazione di evento personalizzata per un nuovo stato, vedere [creazione di uno stato personalizzato con una configurazione di evento personalizzata](#creating-a-custom-state-with-a-custom-event-configuration).</span><span class="sxs-lookup"><span data-stu-id="ca8a6-286">To create a custom event configuration for a new state see: [Creating a Custom State with a Custom Event Configuration](#creating-a-custom-state-with-a-custom-event-configuration).</span></span>
    
    ![InteractiveElementCreateCustomStateNameSet](../images/interactive-element/InEditor/InteractiveElementCreateCustomStateEventConfig.png)


### <a name="how-to-create-a-custom-state-via-script"></a><span data-ttu-id="ca8a6-288">Come creare uno stato personalizzato tramite script</span><span class="sxs-lookup"><span data-stu-id="ca8a6-288">How to Create a Custom State via Script</span></span>

```c#
interactiveElement.AddNewState("MyNewState");

// A new state by default is initialized with a the default StateEvents configuration which contains the 
// OnStateOn and OnStateOff events

StateEvents myNewStateEvents = interactiveElement.GetStateEvents<StateEvents>("MyNewState");

myNewStateEvents.OnStateOn.AddListener(() =>
{
    Debug.Log($"MyNewState is On");
});

```

### <a name="creating-a-custom-state-with-a-custom-event-configuration"></a><span data-ttu-id="ca8a6-289">Creazione di uno stato personalizzato con una configurazione di evento personalizzata</span><span class="sxs-lookup"><span data-stu-id="ca8a6-289">Creating a Custom State with a Custom Event Configuration</span></span> 

<span data-ttu-id="ca8a6-290">I file di esempio per uno stato personalizzato denominato **Keyboard** sono disponibili qui: MRTK\SDK\Experimental\InteractiveElement\Examples\Scripts\CustomStateExample</span><span class="sxs-lookup"><span data-stu-id="ca8a6-290">Example files for a custom state named **Keyboard** are located here: MRTK\SDK\Experimental\InteractiveElement\Examples\Scripts\CustomStateExample</span></span>

<span data-ttu-id="ca8a6-291">I passaggi seguenti illustrano un esempio esistente di creazione di un file di configurazione e di un ricevitore di eventi di stato personalizzati.</span><span class="sxs-lookup"><span data-stu-id="ca8a6-291">The following steps walk through an existing example of creating a custom state event configuration and receiver files.</span></span>

1. <span data-ttu-id="ca8a6-292">Si pensi a un nome di stato.</span><span class="sxs-lookup"><span data-stu-id="ca8a6-292">Think of a state name.</span></span>  <span data-ttu-id="ca8a6-293">Questo nome deve essere univoco e non può essere uguale a quello degli Stati core esistenti.</span><span class="sxs-lookup"><span data-stu-id="ca8a6-293">This name must be unique and cannot be the same as the existing core states.</span></span> <span data-ttu-id="ca8a6-294">Ai fini di questo esempio, il nome dello stato sarà la **tastiera**.</span><span class="sxs-lookup"><span data-stu-id="ca8a6-294">For the purposes of this example, the state name is going to be **Keyboard**.</span></span>

1. <span data-ttu-id="ca8a6-295">Creare due file con estensione cs con nome stato + "Receiver" e nome stato + "Events".</span><span class="sxs-lookup"><span data-stu-id="ca8a6-295">Create two .cs files named state name + "Receiver" and state name + "Events".</span></span> <span data-ttu-id="ca8a6-296">La denominazione di questi file viene presa in considerazione internamente e deve essere conforme al nome dello stato e alla convenzione di evento/destinatario.</span><span class="sxs-lookup"><span data-stu-id="ca8a6-296">The naming of these files are taken into consideration internally and must follow the state name + Event/Receiver convention.</span></span> 

    ![KeyboardStateFiles](../images/interactive-element/InEditor/KeyboardStateFiles.png)

1. <span data-ttu-id="ca8a6-298">Per ulteriori informazioni sui contenuti dei file, vedere i file KeyboardEvents.cs e KeyboardReceiver.cs.</span><span class="sxs-lookup"><span data-stu-id="ca8a6-298">See the KeyboardEvents.cs and KeyboardReceiver.cs files for more details on file contents.</span></span> <span data-ttu-id="ca8a6-299">Le nuove classi di configurazione degli eventi devono ereditare da `BaseInteractionEventConfiguration` e le nuove classi del ricevitore di eventi devono ereditare da `BaseEventReceiver` .</span><span class="sxs-lookup"><span data-stu-id="ca8a6-299">New event configuration classes must inherit from `BaseInteractionEventConfiguration` and new event receiver classes must inherit from `BaseEventReceiver`.</span></span>  <span data-ttu-id="ca8a6-300">Gli esempi di impostazioni di stato per lo stato della tastiera si trovano nel `CustomStateSettingExample.cs` file.</span><span class="sxs-lookup"><span data-stu-id="ca8a6-300">Examples on state setting for the Keyboard state are located in the `CustomStateSettingExample.cs` file.</span></span> 

1. <span data-ttu-id="ca8a6-301">Aggiungere lo stato all'elemento interattivo utilizzando il nome dello stato, il nome dello stato verrà riconosciuto se sono presenti file di configurazione eventi e ricevitore di eventi.</span><span class="sxs-lookup"><span data-stu-id="ca8a6-301">Add the state to Interactive Element using the state name, the state name will be recognized if event configuration and event receiver files exist.</span></span>  <span data-ttu-id="ca8a6-302">Le proprietà nel file di configurazione dell'evento personalizzato devono essere visualizzate nel controllo.</span><span class="sxs-lookup"><span data-stu-id="ca8a6-302">The properties in the custom event configuration file should appear in the inspector.</span></span>

    <span data-ttu-id="ca8a6-303">![](../images/interactive-element/InEditor/AddKeyboardState.png) ![ KeyboardStateFiles KeyboardStateFiles](../images/interactive-element/InEditor/SetKeyboardStateName.png)</span><span class="sxs-lookup"><span data-stu-id="ca8a6-303">![KeyboardStateFiles](../images/interactive-element/InEditor/AddKeyboardState.png) ![KeyboardStateFiles](../images/interactive-element/InEditor/SetKeyboardStateName.png)</span></span>


1. <span data-ttu-id="ca8a6-304">Per ulteriori esempi di file di configurazione di eventi e di ricevitore di eventi, vedere i file nei percorsi seguenti:</span><span class="sxs-lookup"><span data-stu-id="ca8a6-304">For more examples of event configuration and event receiver files see the files at these paths:</span></span>    
- <span data-ttu-id="ca8a6-305">MRTK\SDK\Experimental\InteractiveElement\InteractiveElement\Events\EventConfigurations</span><span class="sxs-lookup"><span data-stu-id="ca8a6-305">MRTK\SDK\Experimental\InteractiveElement\InteractiveElement\Events\EventConfigurations</span></span>
- <span data-ttu-id="ca8a6-306">MRTK\SDK\Experimental\InteractiveElement\InteractiveElement\Events\EventReceivers</span><span class="sxs-lookup"><span data-stu-id="ca8a6-306">MRTK\SDK\Experimental\InteractiveElement\InteractiveElement\Events\EventReceivers</span></span>

## <a name="example-scene"></a><span data-ttu-id="ca8a6-307">Scena di esempio</span><span class="sxs-lookup"><span data-stu-id="ca8a6-307">Example Scene</span></span> 

<span data-ttu-id="ca8a6-308">La scena di esempio per l'elemento interattivo + Visualizzatore stato si trova qui: MRTK\SDK\Experimental\InteractiveElement\Examples\InteractiveElementExampleScene.unity</span><span class="sxs-lookup"><span data-stu-id="ca8a6-308">The example scene for Interactive Element + State Visualizer is located here: MRTK\SDK\Experimental\InteractiveElement\Examples\InteractiveElementExampleScene.unity</span></span>

![ExampleScene](../images/interactive-element/InEditor/ExampleScene.png)

### <a name="compressable-button"></a><span data-ttu-id="ca8a6-310">Pulsante compressive</span><span class="sxs-lookup"><span data-stu-id="ca8a6-310">Compressable Button</span></span>

<span data-ttu-id="ca8a6-311">La scena di esempio contiene prefabbricati denominati `CompressableButton` e `CompressableButtonToggle` , che rispecchiano il comportamento dei `PressableButtonHoloLens2` pulsanti, costruiti usando l'elemento interattivo e il Visualizzatore di stato.</span><span class="sxs-lookup"><span data-stu-id="ca8a6-311">The example scene contains prefabs named `CompressableButton` and `CompressableButtonToggle`, these prefabs mirror the behavior of the `PressableButtonHoloLens2` buttons, that are constructed using Interactive Element and the State Visualizer.</span></span> <span data-ttu-id="ca8a6-312">Il `CompressableButton` componente è attualmente una combinazione di `PressableButton`  +  `PressableButtonHoloLens2` con `BaseInteractiveElement` come classe di base.</span><span class="sxs-lookup"><span data-stu-id="ca8a6-312">The `CompressableButton` component is currently a combination of `PressableButton` + `PressableButtonHoloLens2` with `BaseInteractiveElement`as a base class.</span></span> 

# <a name="state-visualizer-experimental"></a><span data-ttu-id="ca8a6-313">Visualizzatore stato [sperimentale]</span><span class="sxs-lookup"><span data-stu-id="ca8a6-313">State Visualizer [Experimental]</span></span>

<span data-ttu-id="ca8a6-314">Il componente Visualizzatore stato aggiunge animazioni a un oggetto in base agli stati definiti in un componente elemento interattivo collegato.</span><span class="sxs-lookup"><span data-stu-id="ca8a6-314">The State Visualizer component adds animations to an object based on the states defined in a linked Interactive Element component.</span></span> <span data-ttu-id="ca8a6-315">Questo componente crea asset di animazione, li inserisce nella cartella MixedRealityToolkit. generated e Abilita l'impostazione del fotogramma chiave di animazione semplificato tramite l'aggiunta di proprietà animata a un oggetto Game di destinazione.</span><span class="sxs-lookup"><span data-stu-id="ca8a6-315">This component creates animation assets, places them in the MixedRealityToolkit.Generated folder and enables simplified animation keyframe setting through adding Animatable properties to a target game object.</span></span> <span data-ttu-id="ca8a6-316">Per abilitare le transizioni di animazioni tra gli Stati, viene creato un asset del controller di animazione e viene generata una macchina a stati predefinita con i parametri associati e le transizioni di stato.</span><span class="sxs-lookup"><span data-stu-id="ca8a6-316">To enable animation transitions between states, an Animator Controller asset is created and a default state machine is generated with associated parameters and any state transitions.</span></span>  <span data-ttu-id="ca8a6-317">La macchina a stati può essere visualizzata nella finestra Animator di Unity.</span><span class="sxs-lookup"><span data-stu-id="ca8a6-317">The state machine can be viewed in Unity's Animator window.</span></span>

## <a name="state-visualizer-and-unity-animation-system"></a><span data-ttu-id="ca8a6-318">Visualizzatore di stato e sistema di animazione Unity</span><span class="sxs-lookup"><span data-stu-id="ca8a6-318">State Visualizer and Unity Animation System</span></span>

<span data-ttu-id="ca8a6-319">Il Visualizzatore di stato utilizza attualmente il sistema di animazione Unity.</span><span class="sxs-lookup"><span data-stu-id="ca8a6-319">The State Visualizer currently leverages the Unity Animation System.</span></span> 

<span data-ttu-id="ca8a6-320">Quando si preme il pulsante **genera nuova animazione clip** nel Visualizzatore di stato, vengono generati nuovi asset di clip di animazione basati sui nomi degli Stati nell'elemento interattivo e inseriti nella cartella MixedRealityToolkit. generated.</span><span class="sxs-lookup"><span data-stu-id="ca8a6-320">When the **Generate New Animation Clips** button in the State Visualizer is pressed, new animation clip assets are generated based on the state names in Interactive Element and are placed in the MixedRealityToolkit.Generated folder.</span></span> <span data-ttu-id="ca8a6-321">La proprietà clip animazione in ogni contenitore di stato è impostata sul clip di animazione associato.</span><span class="sxs-lookup"><span data-stu-id="ca8a6-321">The Animation Clip property in each state container is set to the associated animation clip.</span></span>

![AnimationClips](../images/interactive-element/StateVisualizer/AnimationClips.png)

<span data-ttu-id="ca8a6-323">Viene inoltre generata una [macchina a stati di animazione](https://docs.unity3d.com/Manual/AnimationOverview.html) per gestire transizioni uniformi tra clip di animazione.</span><span class="sxs-lookup"><span data-stu-id="ca8a6-323">An [Animator State Machine](https://docs.unity3d.com/Manual/AnimationOverview.html) is also generated to manage smooth transitions between animation clips.</span></span>  <span data-ttu-id="ca8a6-324">Per impostazione predefinita, la macchina a stati USA lo [stato any](https://docs.unity3d.com/Manual/class-State.html) per consentire le transizioni tra qualsiasi stato nell'elemento interattivo.</span><span class="sxs-lookup"><span data-stu-id="ca8a6-324">By default, the state machine utilizes the [Any State](https://docs.unity3d.com/Manual/class-State.html) to allow transitions between any state in Interactive Element.</span></span> 

<span data-ttu-id="ca8a6-325">Per ogni stato vengono generati anche [parametri di animazione](https://docs.unity3d.com/Manual/AnimationParameters.html) , i parametri del trigger vengono usati nel Visualizzatore di stato per attivare un'animazione.</span><span class="sxs-lookup"><span data-stu-id="ca8a6-325">[Animation Parameters](https://docs.unity3d.com/Manual/AnimationParameters.html) are also generated for each state, the trigger parameters are used in the State Visualizer to trigger an animation.</span></span>

![UnityStateMachine](../images/interactive-element/StateVisualizer/UnityStateMachine.png)

### <a name="runtime-limitations"></a><span data-ttu-id="ca8a6-327">Limitazioni di runtime</span><span class="sxs-lookup"><span data-stu-id="ca8a6-327">Runtime Limitations</span></span> 

<span data-ttu-id="ca8a6-328">Il Visualizzatore di stato deve essere aggiunto a un oggetto tramite il controllo e non può essere aggiunto tramite script.</span><span class="sxs-lookup"><span data-stu-id="ca8a6-328">The State Visualizer must be added to an object via the Inspector and cannot be added via script.</span></span>  <span data-ttu-id="ca8a6-329">Le proprietà che modificano AnimatorStateMachine/AnimationController sono contenute in uno spazio dei nomi dell'editor ( `UnityEditor.Animations` ) che viene rimosso quando viene compilata l'app.</span><span class="sxs-lookup"><span data-stu-id="ca8a6-329">The properties that modify the AnimatorStateMachine/AnimationController are contained in an editor namespace (`UnityEditor.Animations`) which get removed when the app is built.</span></span>

## <a name="how-to-use-the-state-visualizer"></a><span data-ttu-id="ca8a6-330">Come usare il Visualizzatore di stato</span><span class="sxs-lookup"><span data-stu-id="ca8a6-330">How to use the State Visualizer</span></span>

1. <span data-ttu-id="ca8a6-331">Creazione di un cubo</span><span class="sxs-lookup"><span data-stu-id="ca8a6-331">Create a Cube</span></span>
1. <span data-ttu-id="ca8a6-332">Connetti elemento interattivo</span><span class="sxs-lookup"><span data-stu-id="ca8a6-332">Attach Interactive Element</span></span>
1. <span data-ttu-id="ca8a6-333">Visualizzatore stato di connessione</span><span class="sxs-lookup"><span data-stu-id="ca8a6-333">Attach State Visualizer</span></span>
1. <span data-ttu-id="ca8a6-334">Selezionare **genera nuove clip di animazione**</span><span class="sxs-lookup"><span data-stu-id="ca8a6-334">Select **Generate New Animation Clips**</span></span>

    ![GenerateAnimationClips](../images/interactive-element/StateVisualizer/GenerateAnimationClips.png)

    ![GenerateAnimationClips2](../images/interactive-element/StateVisualizer/GenerateAnimationClips2.png)

1. <span data-ttu-id="ca8a6-337">Nel contenitore stato attivo selezionare **Aggiungi destinazione**</span><span class="sxs-lookup"><span data-stu-id="ca8a6-337">In the Focus state container, select **Add Target**</span></span>

    ![AddTarget](../images/interactive-element/StateVisualizer/AddTarget.png)

1. <span data-ttu-id="ca8a6-339">Trascinare l'oggetto Game corrente nel campo di destinazione</span><span class="sxs-lookup"><span data-stu-id="ca8a6-339">Drag the current game object to the target field</span></span> 

    ![SetTarget](../images/interactive-element/StateVisualizer/SetTarget.png)

1. <span data-ttu-id="ca8a6-341">Apri l'aggiunta delle proprietà animabili del cubo</span><span class="sxs-lookup"><span data-stu-id="ca8a6-341">Open the Cube Animatable Properties foldout</span></span>
1. <span data-ttu-id="ca8a6-342">Selezionare il menu a discesa proprietà animata e selezionare **colore**</span><span class="sxs-lookup"><span data-stu-id="ca8a6-342">Select the Animatable property drop down menu and select **Color**</span></span>

    ![SetColor](../images/interactive-element/StateVisualizer/SetColor.png)

1. <span data-ttu-id="ca8a6-344">Selezionare **Aggiungi la proprietà con animazione colore**</span><span class="sxs-lookup"><span data-stu-id="ca8a6-344">Select **Add the Color Animatable Property**</span></span>

    ![SetColorProperty](../images/interactive-element/StateVisualizer/SetColorProperty.png)

1. <span data-ttu-id="ca8a6-346">Scegliere un colore</span><span class="sxs-lookup"><span data-stu-id="ca8a6-346">Choose a Color</span></span> 

    ![SetBlueColorProperty](../images/interactive-element/StateVisualizer/SetBlueColor.png)

1. <span data-ttu-id="ca8a6-348">Premere Riproduci e osservare la modifica del colore di transizione</span><span class="sxs-lookup"><span data-stu-id="ca8a6-348">Press play and observe the transitional color change</span></span>

    ![FocusColorChange](../images/interactive-element/InEditor/Gifs/FocusColorChange.gif)

## <a name="animatable-properties"></a><span data-ttu-id="ca8a6-350">Proprietà animata</span><span class="sxs-lookup"><span data-stu-id="ca8a6-350">Animatable Properties</span></span>

<span data-ttu-id="ca8a6-351">Lo scopo principale delle proprietà animata è semplificare l'impostazione del fotogramma chiave per la clip di animazione.</span><span class="sxs-lookup"><span data-stu-id="ca8a6-351">The primary purpose of the Animatable Properties is to simplify animation clip keyframe setting.</span></span>  <span data-ttu-id="ca8a6-352">Se un utente ha familiarità con il sistema di animazione Unity e preferisce impostare direttamente i fotogrammi chiave sui clip di animazione generati, non può semplicemente aggiungere proprietà animata a un oggetto di destinazione e aprire il clip nella finestra di animazione di Unity (animazione di Windows > > animazione).</span><span class="sxs-lookup"><span data-stu-id="ca8a6-352">If a user is familiar with the Unity Animation System and would prefer to directly set keyframes on the generated animation clips, then they can simply not add Animatable properties to a target object and open the clip in Unity's Animation window (Windows > Animation > Animation).</span></span> 

<span data-ttu-id="ca8a6-353">Se si usano le proprietà Animatable per Animation, il tipo di curva viene impostato su EaseInOut.</span><span class="sxs-lookup"><span data-stu-id="ca8a6-353">If using the Animatable properties for animation, the curve type is set to EaseInOut.</span></span>

<span data-ttu-id="ca8a6-354">**Proprietà animabili correnti:**</span><span class="sxs-lookup"><span data-stu-id="ca8a6-354">**Current Animatable Properties:**</span></span>
- [<span data-ttu-id="ca8a6-355">Offset scala</span><span class="sxs-lookup"><span data-stu-id="ca8a6-355">Scale Offset</span></span>](#scale-offset)
- [<span data-ttu-id="ca8a6-356">Offset posizione</span><span class="sxs-lookup"><span data-stu-id="ca8a6-356">Position Offset</span></span>](#position-offset)
- [<span data-ttu-id="ca8a6-357">Colore</span><span class="sxs-lookup"><span data-stu-id="ca8a6-357">Color</span></span>](#color)
- [<span data-ttu-id="ca8a6-358">Colore shader</span><span class="sxs-lookup"><span data-stu-id="ca8a6-358">Shader Color</span></span>](#shader-color)
- [<span data-ttu-id="ca8a6-359">Float shader</span><span class="sxs-lookup"><span data-stu-id="ca8a6-359">Shader Float</span></span>](#shader-float)
- [<span data-ttu-id="ca8a6-360">Vettore shader</span><span class="sxs-lookup"><span data-stu-id="ca8a6-360">Shader Vector</span></span>](#shader-vector)

### <a name="scale-offset"></a><span data-ttu-id="ca8a6-361">Offset scala</span><span class="sxs-lookup"><span data-stu-id="ca8a6-361">Scale Offset</span></span>

<span data-ttu-id="ca8a6-362">La proprietà animata offset di ridimensionamento accetta la scala corrente dell'oggetto e aggiunge l'offset definito.</span><span class="sxs-lookup"><span data-stu-id="ca8a6-362">The Scale Offset Animatable property takes the current scale of the object and adds the defined offset.</span></span>

![ScaleOffset](../images/interactive-element/InEditor/Gifs/ScaleOffset.gif)

### <a name="position-offset"></a><span data-ttu-id="ca8a6-364">Offset posizione</span><span class="sxs-lookup"><span data-stu-id="ca8a6-364">Position Offset</span></span>

<span data-ttu-id="ca8a6-365">La proprietà animata offset della posizione accetta la posizione corrente dell'oggetto e aggiunge l'offset definito.</span><span class="sxs-lookup"><span data-stu-id="ca8a6-365">The Position Offset Animatable property takes the current position of the object and adds the defined offset.</span></span>

![PositionOffset](../images/interactive-element/InEditor/Gifs/PositionOffset.gif)

### <a name="color"></a><span data-ttu-id="ca8a6-367">Colore</span><span class="sxs-lookup"><span data-stu-id="ca8a6-367">Color</span></span>

<span data-ttu-id="ca8a6-368">La proprietà Color Animable rappresenta il colore principale di un materiale se il materiale ha una proprietà del colore principale.</span><span class="sxs-lookup"><span data-stu-id="ca8a6-368">The Color Animatable property represents the main color of a material if the material has a main color property.</span></span> <span data-ttu-id="ca8a6-369">Questa proprietà aggiunge un'animazione alla `material._Color` Proprietà.</span><span class="sxs-lookup"><span data-stu-id="ca8a6-369">This property animates the `material._Color` property.</span></span>

![FocusColorChange](../images/interactive-element/InEditor/Gifs/FocusColorChange.gif)

### <a name="shader-color"></a><span data-ttu-id="ca8a6-371">Colore shader</span><span class="sxs-lookup"><span data-stu-id="ca8a6-371">Shader Color</span></span>

<span data-ttu-id="ca8a6-372">La proprietà di animazione del colore dello shader fa riferimento a una proprietà dello shader di tipo Color.</span><span class="sxs-lookup"><span data-stu-id="ca8a6-372">The Shader Color Animatable property refers to a shader property of type color.</span></span> <span data-ttu-id="ca8a6-373">È necessario specificare un nome di proprietà per tutte le proprietà dello shader.</span><span class="sxs-lookup"><span data-stu-id="ca8a6-373">A property name is required for all shader properties.</span></span> <span data-ttu-id="ca8a6-374">Il gif seguente illustra l'animazione di una proprietà di colore shader denominata Fill_Color che non è il colore principale del materiale.</span><span class="sxs-lookup"><span data-stu-id="ca8a6-374">The gif below demonstrates animating a shader color property named Fill_Color that is not the main material color.</span></span>  <span data-ttu-id="ca8a6-375">Osservare i valori modificabili nel controllo materiali.</span><span class="sxs-lookup"><span data-stu-id="ca8a6-375">Observe the changing values in the material inspector.</span></span>

![ShaderColor](../images/interactive-element/InEditor/Gifs/ShaderColor.gif)

### <a name="shader-float"></a><span data-ttu-id="ca8a6-377">Float shader</span><span class="sxs-lookup"><span data-stu-id="ca8a6-377">Shader Float</span></span>

<span data-ttu-id="ca8a6-378">La proprietà con animazione float shader fa riferimento a una proprietà shader di tipo float.</span><span class="sxs-lookup"><span data-stu-id="ca8a6-378">The Shader Float Animatable property refers to a shader property of type float.</span></span> <span data-ttu-id="ca8a6-379">È necessario specificare un nome di proprietà per tutte le proprietà dello shader.</span><span class="sxs-lookup"><span data-stu-id="ca8a6-379">A property name is required for all shader properties.</span></span> <span data-ttu-id="ca8a6-380">Nel formato gif riportato di seguito osservare i valori modificabili in Material Inspector per la proprietà metallic.</span><span class="sxs-lookup"><span data-stu-id="ca8a6-380">In the gif below, observe the changing values in the material inspector for the Metallic property.</span></span> 

![ShaderFloat](../images/interactive-element/InEditor/Gifs/ShaderFloat.gif)

### <a name="shader-vector"></a><span data-ttu-id="ca8a6-382">Vettore shader</span><span class="sxs-lookup"><span data-stu-id="ca8a6-382">Shader Vector</span></span>

<span data-ttu-id="ca8a6-383">La proprietà Animable Vector shader fa riferimento a una proprietà shader di tipo Vector4.</span><span class="sxs-lookup"><span data-stu-id="ca8a6-383">The Shader Vector Animatable property refers to a shader property of type Vector4.</span></span> <span data-ttu-id="ca8a6-384">È necessario specificare un nome di proprietà per tutte le proprietà dello shader.</span><span class="sxs-lookup"><span data-stu-id="ca8a6-384">A property name is required for all shader properties.</span></span> <span data-ttu-id="ca8a6-385">Nel gif seguente osservare i valori modificabili nel controllo materiale per la proprietà di affiancamento (Main Tex_ST).</span><span class="sxs-lookup"><span data-stu-id="ca8a6-385">In the gif below, observe the changing values in the material inspector for the Tiling (Main Tex_ST) property.</span></span> 

![ShaderVector](../images/interactive-element/InEditor/Gifs/ShaderVector.gif)


### <a name="how-to-find-animatable-shader-property-names"></a><span data-ttu-id="ca8a6-387">Come trovare i nomi delle proprietà shader di animazione</span><span class="sxs-lookup"><span data-stu-id="ca8a6-387">How to Find Animatable Shader Property Names</span></span>

1. <span data-ttu-id="ca8a6-388">Passa a finestra > animazione > animazione</span><span class="sxs-lookup"><span data-stu-id="ca8a6-388">Navigate to Window > Animation > Animation</span></span>
1. <span data-ttu-id="ca8a6-389">Verificare che l'oggetto con il Visualizzatore di stato sia selezionato nella gerarchia</span><span class="sxs-lookup"><span data-stu-id="ca8a6-389">Ensure that the object with the State Visualizer is selected in the hierarchy</span></span>
1. <span data-ttu-id="ca8a6-390">Selezionare qualsiasi clip di animazione nella finestra animazione</span><span class="sxs-lookup"><span data-stu-id="ca8a6-390">Select any animation clip in the Animation window</span></span>
1. <span data-ttu-id="ca8a6-391">Selezionare **Aggiungi proprietà**, aprire la sezione del renderer mesh</span><span class="sxs-lookup"><span data-stu-id="ca8a6-391">Select **Add Property**, open the Mesh Renderer foldout</span></span> 

    ![AnimationWindow](../images/interactive-element/StateVisualizer/AnimationWindow.png)

1. <span data-ttu-id="ca8a6-393">Questo elenco contiene i nomi di tutti i nomi di proprietà animabili</span><span class="sxs-lookup"><span data-stu-id="ca8a6-393">This list contains the names of all the Animatable property names</span></span> 

    ![MeshRendererProperties](../images/interactive-element/StateVisualizer/MeshRendererProperties.png)

## <a name="see-also"></a><span data-ttu-id="ca8a6-395">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="ca8a6-395">See also</span></span>

- [<span data-ttu-id="ca8a6-396">**Pulsanti**</span><span class="sxs-lookup"><span data-stu-id="ca8a6-396">**Buttons**</span></span>](button.md)
- [<span data-ttu-id="ca8a6-397">**Controllo dei limiti**</span><span class="sxs-lookup"><span data-stu-id="ca8a6-397">**Bounds Control**</span></span>](bounds-control.md)
- [<span data-ttu-id="ca8a6-398">**Raccolta di oggetti Grid**</span><span class="sxs-lookup"><span data-stu-id="ca8a6-398">**Grid Object Collection**</span></span>](object-collection.md)
- [<span data-ttu-id="ca8a6-399">**Risolutore RadialView**</span><span class="sxs-lookup"><span data-stu-id="ca8a6-399">**RadialView Solver**</span></span>](solvers/solver.md)

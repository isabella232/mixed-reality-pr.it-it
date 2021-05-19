---
title: Elemento Interactive
description: Documentazione di InteractiveElement MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 02/22/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, elemento interattivo, interactable
ms.openlocfilehash: 65f518c53414d68d3a9d2093cb427140cc65560b
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144768"
---
# <a name="interactive-element-experimental"></a><span data-ttu-id="f63ae-104">Elemento Interactive [Sperimentale]</span><span class="sxs-lookup"><span data-stu-id="f63ae-104">Interactive Element [Experimental]</span></span>

<span data-ttu-id="f63ae-105">Un punto di ingresso centralizzato semplificato al sistema di input MRTK.</span><span class="sxs-lookup"><span data-stu-id="f63ae-105">A simplified centralized entry point to the MRTK input system.</span></span> <span data-ttu-id="f63ae-106">Contiene i metodi di gestione dello stato, la gestione degli eventi e la logica di impostazione dello stato per gli stati di interazione principali.</span><span class="sxs-lookup"><span data-stu-id="f63ae-106">Contains state management methods, event management and the state setting logic for Core Interaction States.</span></span>

<span data-ttu-id="f63ae-107">Interactive Element è una funzionalità sperimentale supportata in Unity 2019.3 e versioni fino a quando usa una funzionalità nuova di Unity 2019.3: [Serialize Reference](https://docs.unity3d.com/ScriptReference/SerializeReference.html).</span><span class="sxs-lookup"><span data-stu-id="f63ae-107">Interactive Element is an experimental feature supported in Unity 2019.3 and up as it utilizes a capability new to Unity 2019.3: [Serialize Reference](https://docs.unity3d.com/ScriptReference/SerializeReference.html).</span></span>

### <a name="interactive-element-inspector"></a><span data-ttu-id="f63ae-108">Controllo elemento interattivo</span><span class="sxs-lookup"><span data-stu-id="f63ae-108">Interactive Element Inspector</span></span>

<span data-ttu-id="f63ae-109">Durante la modalità di riproduzione, il controllo elemento interattivo fornisce un feedback visivo che indica se lo stato corrente è attivo o meno.</span><span class="sxs-lookup"><span data-stu-id="f63ae-109">During play mode, the Interactive Element inspector provides visual feedback that indicates whether or not the current state is active.</span></span> <span data-ttu-id="f63ae-110">Se uno stato è attivo, verrà evidenziato con un colore ciano.</span><span class="sxs-lookup"><span data-stu-id="f63ae-110">If a state is active, it will be highlighted with a cyan color.</span></span>  <span data-ttu-id="f63ae-111">Se lo stato non è attivo, il colore non viene modificato.</span><span class="sxs-lookup"><span data-stu-id="f63ae-111">If the state is not active, the color is not changed.</span></span> <span data-ttu-id="f63ae-112">I numeri accanto agli stati nel controllo sono i valori dello stato. Se lo stato è attivo, il valore è 1, se lo stato non è attivo il valore è 0.</span><span class="sxs-lookup"><span data-stu-id="f63ae-112">The numbers next to the states in the inspector are the state values, if the state is active then the value is 1, if the state is not active the value is 0.</span></span>

![Elemento interattivo con interazione con la mano virtuale](../images/interactive-element/InEditor/Gifs/InspectorHighlightEditor.gif)

## <a name="core-states"></a><span data-ttu-id="f63ae-114">Stati principali</span><span class="sxs-lookup"><span data-stu-id="f63ae-114">Core States</span></span>

<span data-ttu-id="f63ae-115">L'elemento Interactive contiene gli stati principali e supporta l'aggiunta [di stati personalizzati.](#custom-states)</span><span class="sxs-lookup"><span data-stu-id="f63ae-115">Interactive Element contains core states and supports the addition of [custom states](#custom-states).</span></span>  <span data-ttu-id="f63ae-116">Uno stato principale è uno stato che ha già la logica di impostazione dello stato definita in `BaseInteractiveElement` .</span><span class="sxs-lookup"><span data-stu-id="f63ae-116">A core state is one that already has the state setting logic defined in `BaseInteractiveElement`.</span></span> <span data-ttu-id="f63ae-117">Di seguito è riportato un elenco degli stati principali correnti guidati dall'input:</span><span class="sxs-lookup"><span data-stu-id="f63ae-117">The following is a list of the current input-driven core states:</span></span> 

### <a name="current-core-states"></a><span data-ttu-id="f63ae-118">Stati principali correnti</span><span class="sxs-lookup"><span data-stu-id="f63ae-118">Current Core States</span></span>

- [<span data-ttu-id="f63ae-119">Default</span><span class="sxs-lookup"><span data-stu-id="f63ae-119">Default</span></span>](#default-state) 

<span data-ttu-id="f63ae-120">Stati principali di interazione da vicino e da lontano:</span><span class="sxs-lookup"><span data-stu-id="f63ae-120">Near and Far Interaction Core States:</span></span>
- [<span data-ttu-id="f63ae-121">Concentrarsi</span><span class="sxs-lookup"><span data-stu-id="f63ae-121">Focus</span></span>](#focus-state) 

<span data-ttu-id="f63ae-122">Vicino agli stati core di interazione:</span><span class="sxs-lookup"><span data-stu-id="f63ae-122">Near Interaction Core States:</span></span>

- [<span data-ttu-id="f63ae-123">Messa a fuoco nelle vicinanze</span><span class="sxs-lookup"><span data-stu-id="f63ae-123">Focus Near</span></span>](#focus-near-state)
- [<span data-ttu-id="f63ae-124">Tocco</span><span class="sxs-lookup"><span data-stu-id="f63ae-124">Touch</span></span>](#touch-state)

<span data-ttu-id="f63ae-125">Stati principali di interazione lontano:</span><span class="sxs-lookup"><span data-stu-id="f63ae-125">Far Interaction Core States:</span></span>
- [<span data-ttu-id="f63ae-126">Messa a fuoco lontano</span><span class="sxs-lookup"><span data-stu-id="f63ae-126">Focus Far</span></span>](#focus-far-state)
- [<span data-ttu-id="f63ae-127">Selezionare Lontano</span><span class="sxs-lookup"><span data-stu-id="f63ae-127">Select Far</span></span>](#select-far-state)

<span data-ttu-id="f63ae-128">Altri stati principali:</span><span class="sxs-lookup"><span data-stu-id="f63ae-128">Other Core States:</span></span>
- [<span data-ttu-id="f63ae-129">Clicked</span><span class="sxs-lookup"><span data-stu-id="f63ae-129">Clicked</span></span>](#clicked-state)
- [<span data-ttu-id="f63ae-130">Attivare e disattivare</span><span class="sxs-lookup"><span data-stu-id="f63ae-130">Toggle On and Toggle Off</span></span>](#toggle-on-and-toggle-off-state)
- [<span data-ttu-id="f63ae-131">Parola chiave Speech</span><span class="sxs-lookup"><span data-stu-id="f63ae-131">Speech Keyword</span></span>](#speech-keyword-state)

### <a name="how-to-add-a-core-state-via-inspector"></a><span data-ttu-id="f63ae-132">Come aggiungere uno stato core tramite Inspector</span><span class="sxs-lookup"><span data-stu-id="f63ae-132">How to Add a Core State via Inspector</span></span>

1. <span data-ttu-id="f63ae-133">Passare ad **Add Core State (Aggiungi** stato core) nel controllo per Interactive Element (Elemento interattivo).</span><span class="sxs-lookup"><span data-stu-id="f63ae-133">Navigate to **Add Core State** in the inspector for Interactive Element.</span></span>

    ![Aggiungere uno stato di base tramite Inspector](../images/interactive-element/InEditor/InteractiveElementAddCoreState.png)


1. <span data-ttu-id="f63ae-135">Selezionare il **pulsante Seleziona stato** per scegliere lo stato principale da aggiungere.</span><span class="sxs-lookup"><span data-stu-id="f63ae-135">Select the **Select State** button to choose the core state to add.</span></span> <span data-ttu-id="f63ae-136">Gli stati nel menu vengono ordinati in base al tipo di interazione.</span><span class="sxs-lookup"><span data-stu-id="f63ae-136">The states in the menu are sorted by interaction type.</span></span>

    ![Aggiungere uno stato core tramite Inspector con lo stato selezionato](../images/interactive-element/InEditor/InteractiveElementAddCoreStateSelectState.png)

1. <span data-ttu-id="f63ae-138">Aprire il foldout Configurazione eventi per visualizzare gli eventi e le proprietà associati allo stato.</span><span class="sxs-lookup"><span data-stu-id="f63ae-138">Open the Event Configuration foldout to view the events and properties associated with the state.</span></span>

    ![Aggiungere uno stato core tramite Inspector con la configurazione degli eventi](../images/interactive-element/InEditor/InteractiveElementAddCoreStateSelectStateEventConfig.png)


### <a name="how-to-add-a-core-state-via-script"></a><span data-ttu-id="f63ae-140">Come aggiungere uno stato core tramite script</span><span class="sxs-lookup"><span data-stu-id="f63ae-140">How to Add a Core State via Script</span></span>

<span data-ttu-id="f63ae-141">Usare il `AddNewState(stateName)` metodo per aggiungere uno stato principale.</span><span class="sxs-lookup"><span data-stu-id="f63ae-141">Use the `AddNewState(stateName)` method to add a core state.</span></span> <span data-ttu-id="f63ae-142">Per un elenco dei nomi di stato principali disponibili, usare `CoreInteractionState` l'enumerazione .</span><span class="sxs-lookup"><span data-stu-id="f63ae-142">For a list of the available core state names, use the `CoreInteractionState` enum.</span></span>

```c#
// Add by name or add by CoreInteractionState enum to string

interactiveElement.AddNewState("SelectFar");

interactiveElement.AddNewState(CoreInteractionState.SelectFar.ToString());
```

### <a name="states-internal-structure"></a><span data-ttu-id="f63ae-143">Struttura interna States</span><span class="sxs-lookup"><span data-stu-id="f63ae-143">States Internal Structure</span></span> 

<span data-ttu-id="f63ae-144">Gli stati nell'elemento interattivo sono di tipo `InteractionState` .</span><span class="sxs-lookup"><span data-stu-id="f63ae-144">The states in Interactive Element are of type `InteractionState`.</span></span>  <span data-ttu-id="f63ae-145">Un `InteractionState` oggetto contiene le proprietà seguenti:</span><span class="sxs-lookup"><span data-stu-id="f63ae-145">An `InteractionState` contains the following properties:</span></span>

- <span data-ttu-id="f63ae-146">**Nome**: nome dello stato.</span><span class="sxs-lookup"><span data-stu-id="f63ae-146">**Name**: The name of the state.</span></span>
- <span data-ttu-id="f63ae-147">**Valore**: valore dello stato.</span><span class="sxs-lookup"><span data-stu-id="f63ae-147">**Value**: The state value.</span></span>  <span data-ttu-id="f63ae-148">Se lo stato è attivo, il valore dello stato è 1.</span><span class="sxs-lookup"><span data-stu-id="f63ae-148">If the state is on, the state value is 1.</span></span> <span data-ttu-id="f63ae-149">Se lo stato è disattivato, il valore dello stato è 0.</span><span class="sxs-lookup"><span data-stu-id="f63ae-149">If the state is off, the state value is 0.</span></span>
- <span data-ttu-id="f63ae-150">**Attivo:** indica se lo stato è attualmente attivo.</span><span class="sxs-lookup"><span data-stu-id="f63ae-150">**Active**: Whether or not the state is currently active.</span></span> <span data-ttu-id="f63ae-151">Il valore della proprietà Active è true quando lo stato è attivo, false se lo stato è disattivato.</span><span class="sxs-lookup"><span data-stu-id="f63ae-151">The value for the Active property is true when the state is on, false if the state is off.</span></span> 
- <span data-ttu-id="f63ae-152">**Tipo di interazione:** il tipo di interazione di uno stato è il tipo di interazione a cui è destinato uno stato.</span><span class="sxs-lookup"><span data-stu-id="f63ae-152">**Interaction Type**: The Interaction Type of a state is the type of interaction a state is intended for.</span></span> 
  - <span data-ttu-id="f63ae-153">`None`: non supporta alcuna forma di interazione di input.</span><span class="sxs-lookup"><span data-stu-id="f63ae-153">`None`: Does not support any form of input interaction.</span></span>
  - <span data-ttu-id="f63ae-154">`Near`: supporto vicino all'interazione.</span><span class="sxs-lookup"><span data-stu-id="f63ae-154">`Near`: Near interaction support.</span></span> <span data-ttu-id="f63ae-155">L'input viene considerato vicino all'interazione quando una mano articolata ha un contatto diretto con un altro oggetto di gioco, ad esempio la posizione in cui la mano articolata è vicina alla posizione dell'oggetto di gioco nello spazio mondiale.</span><span class="sxs-lookup"><span data-stu-id="f63ae-155">Input is considered near interaction when an articulated hand has direct contact with another game object, i.e. the position the articulated hand is close to the position of the game object in world space.</span></span>
  - <span data-ttu-id="f63ae-156">`Far`: supporto dell'interazione da lontano.</span><span class="sxs-lookup"><span data-stu-id="f63ae-156">`Far`: Far interaction support.</span></span> <span data-ttu-id="f63ae-157">L'input viene considerato interazione da lontano quando non è necessario un contatto diretto con l'oggetto del gioco.</span><span class="sxs-lookup"><span data-stu-id="f63ae-157">Input is considered far interaction when direct contact with the game object is not required.</span></span> <span data-ttu-id="f63ae-158">Ad esempio, l'input tramite il raggio del controller o lo sguardo è considerato input di interazione lontano.</span><span class="sxs-lookup"><span data-stu-id="f63ae-158">For example, input via controller ray or gaze is considered far interaction input.</span></span>
  - <span data-ttu-id="f63ae-159">`NearAndFar`: include il supporto per le interazioni vicino e lontano.</span><span class="sxs-lookup"><span data-stu-id="f63ae-159">`NearAndFar`: Encompasses both near and far interaction support.</span></span> 
  - <span data-ttu-id="f63ae-160">`Other`: supporto dell'interazione indipendente dal puntatore.</span><span class="sxs-lookup"><span data-stu-id="f63ae-160">`Other`: Pointer independent interaction support.</span></span>
- <span data-ttu-id="f63ae-161">**Configurazione eventi:** la configurazione degli eventi per uno stato è il punto di ingresso del profilo eventi serializzati.</span><span class="sxs-lookup"><span data-stu-id="f63ae-161">**Event Configuration**: The event configuration for a state is the serialized events profile entry point.</span></span> 

<span data-ttu-id="f63ae-162">Tutte queste proprietà vengono impostate internamente nell'elemento `State Manager` contenuto in Interactive Element.</span><span class="sxs-lookup"><span data-stu-id="f63ae-162">All of these properties are set internally in the `State Manager` contained in Interactive Element.</span></span> <span data-ttu-id="f63ae-163">Per la modifica degli stati, usare i metodi helper seguenti:</span><span class="sxs-lookup"><span data-stu-id="f63ae-163">For modification of states use the following helper methods:</span></span>

<span data-ttu-id="f63ae-164">**Metodi helper per l'impostazione dello stato**</span><span class="sxs-lookup"><span data-stu-id="f63ae-164">**State Setting Helper Methods**</span></span>

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

<span data-ttu-id="f63ae-165">Il recupero della configurazione dell'evento di uno stato è specifico dello stato stesso.</span><span class="sxs-lookup"><span data-stu-id="f63ae-165">Getting the event configuration of a state is specific to the state itself.</span></span> <span data-ttu-id="f63ae-166">Ogni stato principale ha un tipo di configurazione di evento specifico, descritto di seguito nelle sezioni che descrivono ogni stato principale.</span><span class="sxs-lookup"><span data-stu-id="f63ae-166">Each core state has a specific event configuration type which is outlined below under the sections describing each core state.</span></span>

<span data-ttu-id="f63ae-167">Di seguito è riportato un esempio generalizzato di recupero della configurazione degli eventi di uno stato:</span><span class="sxs-lookup"><span data-stu-id="f63ae-167">Here is a generalized example of getting a state's event configuration:</span></span>

```c#
// T varies depending on the core state - the specific T's are specified under each of the core state sections
T stateNameEvents = interactiveElement.GetStateEvents<T>("StateName");
```

### <a name="default-state"></a><span data-ttu-id="f63ae-168">Stato predefinito</span><span class="sxs-lookup"><span data-stu-id="f63ae-168">Default State</span></span>

<span data-ttu-id="f63ae-169">Lo stato Predefinito è sempre presente in un elemento interattivo.</span><span class="sxs-lookup"><span data-stu-id="f63ae-169">The Default state is always present on an Interactive Element.</span></span>  <span data-ttu-id="f63ae-170">Questo stato sarà attivo solo quando tutti gli altri stati non sono attivi.</span><span class="sxs-lookup"><span data-stu-id="f63ae-170">This state will be active only when all other states are not active.</span></span>  <span data-ttu-id="f63ae-171">Se un altro stato diventa attivo, lo stato Predefinito verrà impostato su disattivato internamente.</span><span class="sxs-lookup"><span data-stu-id="f63ae-171">If any other state becomes active, then the Default state will be set to off internally.</span></span> 

<span data-ttu-id="f63ae-172">Un elemento interattivo viene inizializzato con gli stati Predefinito e Stato attivo presenti nell'elenco degli stati.</span><span class="sxs-lookup"><span data-stu-id="f63ae-172">An Interactive Element is initialized with the Default and Focus states present in the state list.</span></span> <span data-ttu-id="f63ae-173">Lo stato Predefinito deve essere sempre presente nell'elenco degli stati.</span><span class="sxs-lookup"><span data-stu-id="f63ae-173">The Default state always needs to be present in the state list.</span></span> 

#### <a name="getting-default-state-events"></a><span data-ttu-id="f63ae-174">Recupero degli eventi di stato predefiniti</span><span class="sxs-lookup"><span data-stu-id="f63ae-174">Getting Default State Events</span></span>

<span data-ttu-id="f63ae-175">Tipo di configurazione dell'evento per lo stato predefinito: `StateEvents`</span><span class="sxs-lookup"><span data-stu-id="f63ae-175">Event configuration type for the Default State: `StateEvents`</span></span>

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

### <a name="focus-state"></a><span data-ttu-id="f63ae-176">Stato attivo</span><span class="sxs-lookup"><span data-stu-id="f63ae-176">Focus State</span></span>

<span data-ttu-id="f63ae-177">Lo stato messa a fuoco è uno stato di interazione da vicino e da lontano che può essere ritenuto come la realtà mista equivalente al passaggio del mouse.</span><span class="sxs-lookup"><span data-stu-id="f63ae-177">The Focus state is a near and far interaction state that can be thought of as the mixed reality equivalent to hover.</span></span> <span data-ttu-id="f63ae-178">Il fattore di distinzione tra l'interazione da vicino e da lontano per lo stato di messa a fuoco è il tipo di puntatore attivo corrente.</span><span class="sxs-lookup"><span data-stu-id="f63ae-178">The distinguishing factor between near and far interaction for the Focus state is the current active pointer type.</span></span>  <span data-ttu-id="f63ae-179">Se il tipo di puntatore per lo stato di messa a fuoco è il puntatore Poke, l'interazione viene considerata quasi interazione.</span><span class="sxs-lookup"><span data-stu-id="f63ae-179">If the pointer type for the Focus state is the Poke Pointer, then the interaction is considered near interaction.</span></span>  <span data-ttu-id="f63ae-180">Se il puntatore principale non è il puntatore Poke, l'interazione viene considerata un'interazione da lontano.</span><span class="sxs-lookup"><span data-stu-id="f63ae-180">If the primary pointer is not the Poke Pointer, then the interaction is considered far interaction.</span></span> <span data-ttu-id="f63ae-181">Lo stato attivo è presente nell'elemento interattivo per impostazione predefinita.</span><span class="sxs-lookup"><span data-stu-id="f63ae-181">The Focus state is present in Interactive Element by default.</span></span>

<span data-ttu-id="f63ae-182">**Comportamento dello stato attivo** 
 ![ Stato di messa a fuoco con interazione con la mano virtuale](../images/interactive-element/InEditor/Gifs/FocusStateEditor.gif)</span><span class="sxs-lookup"><span data-stu-id="f63ae-182">**Focus State Behavior**
![Focus state with virtual hand interaction](../images/interactive-element/InEditor/Gifs/FocusStateEditor.gif)</span></span> 

<span data-ttu-id="f63ae-183">**Controllo stato attivo** 
 ![ Stato dello stato attivo nell'inpsector](../images/interactive-element/InEditor/FocusStateInspector.png)</span><span class="sxs-lookup"><span data-stu-id="f63ae-183">**Focus State Inspector**
![Focus state in the Inpsector](../images/interactive-element/InEditor/FocusStateInspector.png)</span></span>

#### <a name="getting-focus-state-events&quot;></a><span data-ttu-id=&quot;f63ae-184&quot;>Recupero di eventi di stato attivo</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;f63ae-184&quot;>Getting Focus State Events</span></span>

<span data-ttu-id=&quot;f63ae-185&quot;>Tipo di configurazione dell'evento per lo stato attivo: `FocusEvents`</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;f63ae-185&quot;>Event configuration type for the Focus State: `FocusEvents`</span></span>

```c#
FocusEvents focusEvents = interactiveElement.GetStateEvents<FocusEvents>(&quot;Focus");

focusEvents.OnFocusOn.AddListener((pointerEventData) =>
{
    Debug.Log($"{gameObject.name} Focus On");
});

focusEvents.OnFocusOff.AddListener((pointerEventData) =>
{
    Debug.Log($"{gameObject.name} Focus Off");
});
```

#### <a name="focus-near-vs-focus-far-behavior"></a><span data-ttu-id="f63ae-186">Comportamento di messa a fuoco vicino a messa a fuoco e stato attivo lontano</span><span class="sxs-lookup"><span data-stu-id="f63ae-186">Focus Near vs Focus Far Behavior</span></span> 

![Concentrarsi vicino e lontano con l'interazione con la mano virtuale](../images/interactive-element/InEditor/Gifs/FocusNearFocusFar.gif)

### <a name="focus-near-state"></a><span data-ttu-id="f63ae-188">Messa a fuoco vicino allo stato</span><span class="sxs-lookup"><span data-stu-id="f63ae-188">Focus Near State</span></span>

<span data-ttu-id="f63ae-189">Lo stato Stato attivo vicino viene impostato quando viene generato un evento di stato attivo e il puntatore primario è il puntatore Poke, un'indicazione dell'interazione vicina.</span><span class="sxs-lookup"><span data-stu-id="f63ae-189">The Focus Near state is set when a focus event is raised and the primary pointer is the Poke pointer, an indication of near interaction.</span></span> 

<span data-ttu-id="f63ae-190">**Messa a fuoco vicino allo stato Comportamento** 
 ![ Concentrarsi vicino allo stato con l'interazione con la mano virtuale](../images/interactive-element/InEditor/Gifs/FocusNearStateEditor.gif)</span><span class="sxs-lookup"><span data-stu-id="f63ae-190">**Focus Near State Behavior**
![Focus near state with virtual hand interaction](../images/interactive-element/InEditor/Gifs/FocusNearStateEditor.gif)</span></span> 

<span data-ttu-id="f63ae-191">**Focus Near State Inspector (Messa a fuoco vicino a controllo stato)** 
 ![ Messa a fuoco vicino al componente nel controllo](../images/interactive-element/InEditor/FocusNearStateInspector.png)</span><span class="sxs-lookup"><span data-stu-id="f63ae-191">**Focus Near State Inspector**
![Focus near component in the Inspector](../images/interactive-element/InEditor/FocusNearStateInspector.png)</span></span>

#### <a name="getting-focusnear-state-events&quot;></a><span data-ttu-id=&quot;f63ae-192&quot;>Recupero di eventi di stato FocusNear</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;f63ae-192&quot;>Getting FocusNear State Events</span></span>

<span data-ttu-id=&quot;f63ae-193&quot;>Tipo di configurazione dell'evento per stato FocusNear: `FocusEvents`</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;f63ae-193&quot;>Event configuration type for the FocusNear State: `FocusEvents`</span></span>

```c#
FocusEvents focusNearEvents = interactiveElement.GetStateEvents<FocusEvents>(&quot;FocusNear");

focusNearEvents.OnFocusOn.AddListener((pointerEventData) =>
{
    Debug.Log($"{gameObject.name} Near Interaction Focus On");
});

focusNearEvents.OnFocusOff.AddListener((pointerEventData) =>
{
    Debug.Log($"{gameObject.name} Near Interaction Focus Off");
});
```

### <a name="focus-far-state"></a><span data-ttu-id="f63ae-194">Stato attivo lontano</span><span class="sxs-lookup"><span data-stu-id="f63ae-194">Focus Far State</span></span>

<span data-ttu-id="f63ae-195">Lo stato Focus Far viene impostato quando il puntatore primario non è il puntatore Poke.</span><span class="sxs-lookup"><span data-stu-id="f63ae-195">The Focus Far state is set when the primary pointer is not the Poke pointer.</span></span>  <span data-ttu-id="f63ae-196">Ad esempio, il puntatore di raggio del controller predefinito e il puntatore GGV (Sguardo fisso, Movimento, Voce) sono considerati puntatori di interazione lontano.</span><span class="sxs-lookup"><span data-stu-id="f63ae-196">For example, the default controller ray pointer and the GGV (Gaze, Gesture, Voice) pointer are considered far interaction pointers.</span></span>

<span data-ttu-id="f63ae-197">**Comportamento dello stato attivo lontano** 
 ![ Stato di messa a fuoco lontano con l'interazione con la mano virtuale](../images/interactive-element/InEditor/Gifs/FocusFarStateEditor.gif)</span><span class="sxs-lookup"><span data-stu-id="f63ae-197">**Focus Far State Behavior**
![Focus state far with virtual hand interaction](../images/interactive-element/InEditor/Gifs/FocusFarStateEditor.gif)</span></span>

<span data-ttu-id="f63ae-198">**Focus Far State Inspector** 
 ![ Componente Distorsiva nello stato attivo nel controllo](../images/interactive-element/InEditor/FocusFarStateInspector.png)</span><span class="sxs-lookup"><span data-stu-id="f63ae-198">**Focus Far State Inspector**
![Focus far component in the Inspector](../images/interactive-element/InEditor/FocusFarStateInspector.png)</span></span>

#### <a name="getting-focus-far-state-events&quot;></a><span data-ttu-id=&quot;f63ae-199&quot;>Recupero di eventi di stato lontano dello stato attivo</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;f63ae-199&quot;>Getting Focus Far State Events</span></span>

<span data-ttu-id=&quot;f63ae-200&quot;>Tipo di configurazione dell'evento per stato FocusFar: `FocusEvents`</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;f63ae-200&quot;>Event configuration type for the FocusFar State: `FocusEvents`</span></span>

```c#
FocusEvents focusFarEvents = interactiveElement.GetStateEvents<FocusEvents>(&quot;FocusFar");

focusFarEvents.OnFocusOn.AddListener((pointerEventData) =>
{
    Debug.Log($"{gameObject.name} Far Interaction Focus On");
});

focusFarEvents.OnFocusOff.AddListener((pointerEventData) =>
{
    Debug.Log($"{gameObject.name} Far Interaction Focus Off");
});
```

### <a name="touch-state"></a><span data-ttu-id="f63ae-201">Stato tocco</span><span class="sxs-lookup"><span data-stu-id="f63ae-201">Touch State</span></span>

<span data-ttu-id="f63ae-202">Lo stato Tocco è uno stato di interazione vicino che viene impostato quando una mano articolata tocca direttamente l'oggetto.</span><span class="sxs-lookup"><span data-stu-id="f63ae-202">The Touch state is a near interaction state that is set when an articulated hand touches the object directly.</span></span>  <span data-ttu-id="f63ae-203">Un tocco diretto significa che il dito indice della mano articolata è molto vicino alla posizione mondiale dell'oggetto.</span><span class="sxs-lookup"><span data-stu-id="f63ae-203">A direct touch means that the articulated hand's index finger is very close to the world position of the object.</span></span> <span data-ttu-id="f63ae-204">Per impostazione predefinita, `NearInteractionTouchableVolume` un componente viene collegato all'oggetto se lo stato Tocco viene aggiunto all'elenco degli stati.</span><span class="sxs-lookup"><span data-stu-id="f63ae-204">By default, a `NearInteractionTouchableVolume` component is attached to the object if the Touch state is added to the the state list.</span></span>  <span data-ttu-id="f63ae-205">La presenza di un  `NearInteractionTouchableVolume` componente o è necessaria per `NearInteractionTouchable` rilevare gli eventi touch.</span><span class="sxs-lookup"><span data-stu-id="f63ae-205">The presence of a  `NearInteractionTouchableVolume` or `NearInteractionTouchable` component is required for detecting Touch events.</span></span>  <span data-ttu-id="f63ae-206">La differenza tra e è che rileva un tocco in base al collisore dell'oggetto e rileva il tocco all'interno di `NearInteractionTouchableVolume` un'area definita di un `NearInteractionTouchable` `NearInteractionTouchableVolume` `NearInteractionTouchable` piano.</span><span class="sxs-lookup"><span data-stu-id="f63ae-206">The difference between `NearInteractionTouchableVolume` and `NearInteractionTouchable` is that `NearInteractionTouchableVolume` detects a touch based on the collider of the object and `NearInteractionTouchable`detects touch within a defined area of a plane.</span></span>

<span data-ttu-id="f63ae-207">**Comportamento dello stato tocco** 
 ![ Stato tocco con interazione con la mano virtuale](../images/interactive-element/InEditor/Gifs/TouchStateEditor.gif)</span><span class="sxs-lookup"><span data-stu-id="f63ae-207">**Touch State Behavior**
![Touch state with virtual hand interaction](../images/interactive-element/InEditor/Gifs/TouchStateEditor.gif)</span></span>

<span data-ttu-id="f63ae-208">**Controllo stato tocco** 
 ![ Componente stato tocco nel controllo](../images/interactive-element/InEditor/TouchStateInspector.png)</span><span class="sxs-lookup"><span data-stu-id="f63ae-208">**Touch State Inspector**
![Touch state component in the Inspector](../images/interactive-element/InEditor/TouchStateInspector.png)</span></span>

#### <a name="getting-touch-state-events&quot;></a><span data-ttu-id=&quot;f63ae-209&quot;>Recupero di eventi di stato tocco</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;f63ae-209&quot;>Getting Touch State Events</span></span>

<span data-ttu-id=&quot;f63ae-210&quot;>Tipo di configurazione dell'evento per Lo stato tocco: `TouchEvents`</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;f63ae-210&quot;>Event configuration type for the Touch State: `TouchEvents`</span></span>

```c#
TouchEvents touchEvents = interactiveElement.GetStateEvents<TouchEvents>(&quot;Touch");

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

### <a name="select-far-state"></a><span data-ttu-id="f63ae-211">Selezionare Stato lontano</span><span class="sxs-lookup"><span data-stu-id="f63ae-211">Select Far State</span></span>

<span data-ttu-id="f63ae-212">Lo stato Select Far (Seleziona da lontano) `IMixedRealityPointerHandler` è quello indicato.</span><span class="sxs-lookup"><span data-stu-id="f63ae-212">The Select Far state is the `IMixedRealityPointerHandler` surfaced.</span></span>  <span data-ttu-id="f63ae-213">Questo stato è uno stato di interazione da lontano che rileva il clic di interazione da lontano (tocco) e mantiene l'uso di puntatori di interazione da lontano, ad esempio l'indicatore di misura del raggio del controller predefinito o il puntatore GGV.</span><span class="sxs-lookup"><span data-stu-id="f63ae-213">This state is a far interaction state that detects far interaction click (air-tap) and holds through the use of far interaction pointers such as the default controller ray pointer or the GGV pointer.</span></span>  <span data-ttu-id="f63ae-214">Lo stato Select Far (Seleziona da lontano) ha un'opzione nella sezione di configurazione dell'evento denominata `Global` .</span><span class="sxs-lookup"><span data-stu-id="f63ae-214">The Select Far state has an option under the event configuration foldout named `Global`.</span></span> <span data-ttu-id="f63ae-215">Se `Global` è true, viene `IMixedRealityPointerHandler` registrato come gestore di input globale.</span><span class="sxs-lookup"><span data-stu-id="f63ae-215">If `Global` is true, then the `IMixedRealityPointerHandler` is registered as a global input handler.</span></span>  <span data-ttu-id="f63ae-216">Lo stato attivo su un oggetto non è necessario per attivare eventi di sistema di input se un gestore è registrato come globale.</span><span class="sxs-lookup"><span data-stu-id="f63ae-216">Focus on an object is not required to trigger input system events if a handler is registered as global.</span></span>  <span data-ttu-id="f63ae-217">Ad esempio, se un utente vuole sapere ogni volta che viene eseguito il movimento di tocco/selezione indipendentemente dall'oggetto nello stato attivo, impostare `Global` su true.</span><span class="sxs-lookup"><span data-stu-id="f63ae-217">For example, if a user wants to know anytime the air-tap/select gesture is performed regardless of the object in focus, set `Global` to true.</span></span> 

<span data-ttu-id="f63ae-218">**Selezionare Far State Behavior (Comportamento stato lontano)** 
 ![ Selezionare da lontano con l'interazione con la mano virtuale](../images/interactive-element/InEditor/Gifs/SelectFarStateEditor.gif)</span><span class="sxs-lookup"><span data-stu-id="f63ae-218">**Select Far State Behavior**
![Select far with virtual hand interaction](../images/interactive-element/InEditor/Gifs/SelectFarStateEditor.gif)</span></span>

<span data-ttu-id="f63ae-219">**Selezionare Far State Inspector (Controllo stato lontano)** 
 ![ Selezionare il componente lontano nel controllo](../images/interactive-element/InEditor/SelectFarStateInspector.png)</span><span class="sxs-lookup"><span data-stu-id="f63ae-219">**Select Far State Inspector**
![Select far component in the Inspector](../images/interactive-element/InEditor/SelectFarStateInspector.png)</span></span>

#### <a name="getting-select-far-state-events&quot;></a><span data-ttu-id=&quot;f63ae-220&quot;>Recupero di eventi select far state</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;f63ae-220&quot;>Getting Select Far State Events</span></span>

<span data-ttu-id=&quot;f63ae-221&quot;>Tipo di configurazione dell'evento per SelectFar State: `SelectFarEvents`</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;f63ae-221&quot;>Event configuration type for the SelectFar State: `SelectFarEvents`</span></span>

```c#
SelectFarEvents selectFarEvents = interactiveElement.GetStateEvents<SelectFarEvents>(&quot;SelectFar");

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

### <a name="clicked-state"></a><span data-ttu-id="f63ae-222">Stato selezionato</span><span class="sxs-lookup"><span data-stu-id="f63ae-222">Clicked State</span></span>

<span data-ttu-id="f63ae-223">Lo stato Clicked (Selezionato) viene attivato da un clic di interazione da lontano (Select Far state) (Seleziona stato lontano) per impostazione predefinita.</span><span class="sxs-lookup"><span data-stu-id="f63ae-223">The Clicked state is triggered by a far interaction click (Select Far state) by default.</span></span>  <span data-ttu-id="f63ae-224">Questo stato viene commutato internamente su on, richiama l'evento OnClicked e quindi viene immediatamente disattivato.</span><span class="sxs-lookup"><span data-stu-id="f63ae-224">This state is internally switched to on, invokes the OnClicked event and then is immediately switched to off.</span></span> 

> [!NOTE]
> <span data-ttu-id="f63ae-225">Il feedback visivo nel controllo in base all'attività di stato non è presente per lo stato Clicked perché viene attivata e quindi disattivata immediatamente.</span><span class="sxs-lookup"><span data-stu-id="f63ae-225">The visual feedback in the inspector based on state activity is not present for the Clicked state because it is switched on and then off immediately.</span></span> 

<span data-ttu-id="f63ae-226">**Comportamento dello stato su cui è stato fatto clic** 
 ![ Stato selezionato con interazioni con la mano virtuale](../images/interactive-element/InEditor/Gifs/ClickedStateEditor.gif)</span><span class="sxs-lookup"><span data-stu-id="f63ae-226">**Clicked State Behavior**
![Clicked state with virtual hand interactions](../images/interactive-element/InEditor/Gifs/ClickedStateEditor.gif)</span></span>

<span data-ttu-id="f63ae-227">**Controllo di stato su cui è stato fatto clic** 
 ![ Fare clic sul componente di stato nel controllo](../images/interactive-element/InEditor/ClickedStateInspector.png)</span><span class="sxs-lookup"><span data-stu-id="f63ae-227">**Clicked State Inspector**
![Click state component in the Inspector](../images/interactive-element/InEditor/ClickedStateInspector.png)</span></span>

<span data-ttu-id="f63ae-228">**Esempio di stato near e far clicked**</span><span class="sxs-lookup"><span data-stu-id="f63ae-228">**Near and Far Clicked State Example**</span></span>  
<span data-ttu-id="f63ae-229">Lo stato selezionato può essere attivato tramite punti di ingresso aggiuntivi usando il `interactiveElement.TriggerClickedState()` metodo .</span><span class="sxs-lookup"><span data-stu-id="f63ae-229">The clicked state can be triggered through additional entry points using the `interactiveElement.TriggerClickedState()` method.</span></span>  <span data-ttu-id="f63ae-230">Ad esempio, se un utente vuole che un tocco vicino all'interazione attiverà un clic su un oggetto, aggiungerà il metodo come listener nello stato `TriggerClickedState()` tocco.</span><span class="sxs-lookup"><span data-stu-id="f63ae-230">For example, if a user wants a near interaction touch to trigger a click on an object as well, then they would add the `TriggerClickedState()` method as a listener in the touch state.</span></span>   

![Stato vicino e lontano con interazioni con la mano virtuale](../images/interactive-element/InEditor/Gifs/NearFarClickedState.gif)

#### <a name="getting-clicked-state-events&quot;></a><span data-ttu-id=&quot;f63ae-232&quot;>Recupero di eventi di stato su cui è stato fatto clic</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;f63ae-232&quot;>Getting Clicked State Events</span></span>

<span data-ttu-id=&quot;f63ae-233&quot;>Tipo di configurazione dell'evento per lo stato selezionato: `ClickedEvents`</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;f63ae-233&quot;>Event configuration type for the Clicked State: `ClickedEvents`</span></span>

```c#
ClickedEvents clickedEvent = interactiveElement.GetStateEvents<ClickedEvents>(&quot;Clicked");

clickedEvent.OnClicked.AddListener(() =>
{
    Debug.Log($"{gameObject.name} Clicked");
});
```

### <a name="toggle-on-and-toggle-off-state"></a><span data-ttu-id="f63ae-234">Attivare e disattivare lo stato</span><span class="sxs-lookup"><span data-stu-id="f63ae-234">Toggle On and Toggle Off state</span></span>

<span data-ttu-id="f63ae-235">Gli stati Attiva/Disattiva e Disattiva sono una coppia ed entrambi devono essere presenti per il comportamento di attivazione/disattivazione.</span><span class="sxs-lookup"><span data-stu-id="f63ae-235">The Toggle On and Toggle Off states are a pair and both need to be present for toggle behavior.</span></span>  <span data-ttu-id="f63ae-236">Per impostazione predefinita, gli stati Attiva/Disattiva e Disattiva vengono attivati tramite un clic di interazione lontano (Seleziona stato lontano).</span><span class="sxs-lookup"><span data-stu-id="f63ae-236">By default, the Toggle On and Toggle Off states are triggered through a far interaction click (Select Far state).</span></span>  <span data-ttu-id="f63ae-237">Per impostazione predefinita, lo stato Toggle Off è attivo all'avvio, vale a dire che l'interruttore verrà inizializzato su off.</span><span class="sxs-lookup"><span data-stu-id="f63ae-237">By default, the Toggle Off state is active on start, meaning that the toggle will be initialized to off.</span></span>  <span data-ttu-id="f63ae-238">Se un utente vuole che lo stato Attiva/Disattiva sia attivo all'avvio, nello stato Attiva/Disattiva impostare `IsSelectedOnStart` su true.</span><span class="sxs-lookup"><span data-stu-id="f63ae-238">If a user wants the Toggle On state to be active on start, then in the Toggle On state set `IsSelectedOnStart` to true.</span></span>

<span data-ttu-id="f63ae-239">**Comportamento dello stato ToggleOn e** 
 ![ Toggle Off Attivare e disattivare le interazioni con la mano virtuale](../images/interactive-element/InEditor/Gifs/ToggleOnToggleOffStateEditor.gif)</span><span class="sxs-lookup"><span data-stu-id="f63ae-239">**ToggleOn and Toggle Off State Behavior**
![Toggle on and off with virtual hand interactions](../images/interactive-element/InEditor/Gifs/ToggleOnToggleOffStateEditor.gif)</span></span>

<span data-ttu-id="f63ae-240">**ToggleOn e Toggle Off State Inspector** 
 ![ Attivare/disattivare il componente nel controllo](../images/interactive-element/InEditor/ToggleOnToggleOffStateInspector.png)</span><span class="sxs-lookup"><span data-stu-id="f63ae-240">**ToggleOn and Toggle Off State Inspector**
![Toggle component in the Inspector](../images/interactive-element/InEditor/ToggleOnToggleOffStateInspector.png)</span></span>

<span data-ttu-id="f63ae-241">**Esempio di stati near e far toggle**</span><span class="sxs-lookup"><span data-stu-id="f63ae-241">**Near and Far Toggle States Example**</span></span>  
<span data-ttu-id="f63ae-242">Analogamente allo stato Clicked, l'impostazione toggle state può avere più punti di ingresso usando il `interactiveElement.SetToggleStates()` metodo .</span><span class="sxs-lookup"><span data-stu-id="f63ae-242">Similar to the Clicked state, toggle state setting can have multiple entry points using the `interactiveElement.SetToggleStates()` method.</span></span> <span data-ttu-id="f63ae-243">Ad esempio, se un utente vuole che il tocco sia un punto di ingresso aggiuntivo per impostare gli stati di attivazione/disattivazione, aggiunge il metodo a uno degli eventi `SetToggleStates()` nello stato Tocco.</span><span class="sxs-lookup"><span data-stu-id="f63ae-243">For example, if a user wants touch as an additional entry point to set the toggle states, then they add the `SetToggleStates()` method to one of the events in the Touch state.</span></span> 

![Interruttore vicino e lontano con le interazioni con la mano virtuale](../images/interactive-element/InEditor/Gifs/NearFarToggleStates.gif)

#### <a name="getting-toggle-on-and-toggle-off-state-events&quot;></a><span data-ttu-id=&quot;f63ae-245&quot;>Attivazione e disattivazione degli eventi di stato</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;f63ae-245&quot;>Getting Toggle On and Toggle Off State Events</span></span>

<span data-ttu-id=&quot;f63ae-246&quot;>Tipo di configurazione dell'evento per lo stato ToggleOn: `ToggleOnEvents`</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;f63ae-246&quot;>Event configuration type for the ToggleOn State: `ToggleOnEvents`</span></span>  
<span data-ttu-id=&quot;f63ae-247&quot;>Tipo di configurazione dell'evento per lo stato ToggleOff: `ToggleOffEvents`</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;f63ae-247&quot;>Event configuration type for the ToggleOff State: `ToggleOffEvents`</span></span>

```c#
// Toggle On Events
ToggleOnEvents toggleOnEvent = interactiveElement.GetStateEvents<ToggleOnEvents>(&quot;ToggleOn");

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

### <a name="speech-keyword-state"></a><span data-ttu-id="f63ae-248">Stato parola chiave voce</span><span class="sxs-lookup"><span data-stu-id="f63ae-248">Speech Keyword State</span></span>

<span data-ttu-id="f63ae-249">Lo stato Parola chiave voce è in ascolto delle parole chiave definite nel profilo voce di realtà mista.</span><span class="sxs-lookup"><span data-stu-id="f63ae-249">The Speech Keyword state listens for the keywords defined in the Mixed Reality Speech Profile.</span></span> <span data-ttu-id="f63ae-250">Qualsiasi nuova parola chiave DEVE essere registrata nel profilo del comando vocale prima del runtime (procedura seguente).</span><span class="sxs-lookup"><span data-stu-id="f63ae-250">Any new keyword MUST be registered in the speech command profile prior to runtime (steps below).</span></span> 

<span data-ttu-id="f63ae-251">**Comportamento dello stato delle parole chiave vocali** 
 ![ Parola chiave voce con interazione virtuale](../images/interactive-element/InEditor/Gifs/SpeechKeywordStateEditor.gif)</span><span class="sxs-lookup"><span data-stu-id="f63ae-251">**Speech Keyword State Behavior**
![Speech keyword with virtual interaction](../images/interactive-element/InEditor/Gifs/SpeechKeywordStateEditor.gif)</span></span>

<span data-ttu-id="f63ae-252">**Controllo stato parola chiave voce** 
 ![ Componente parola chiave Voce in Inspector](../images/interactive-element/InEditor/SpeechKeywordStateInspector.png)</span><span class="sxs-lookup"><span data-stu-id="f63ae-252">**Speech Keyword State Inspector**
![Speech keyword component in the Inspector](../images/interactive-element/InEditor/SpeechKeywordStateInspector.png)</span></span>

> [!NOTE]
> <span data-ttu-id="f63ae-253">Lo stato della parola chiave voce è stato attivato nell'editor premendo F5 nella gif precedente.</span><span class="sxs-lookup"><span data-stu-id="f63ae-253">The Speech Keyword state was triggered in editor by pressing the F5 key in the gif above.</span></span> <span data-ttu-id="f63ae-254">La configurazione nel test dell'editor per il riconoscimento vocale è descritta nei passaggi seguenti.</span><span class="sxs-lookup"><span data-stu-id="f63ae-254">Setting up in editor testing for speech is outlined the steps below.</span></span> 

#### <a name="how-to-register-a-speech-commandkeyword"></a><span data-ttu-id="f63ae-255">Come registrare un comando vocale/parola chiave</span><span class="sxs-lookup"><span data-stu-id="f63ae-255">How to Register a Speech Command/Keyword</span></span>

1. <span data-ttu-id="f63ae-256">Selezionare **l'oggetto gioco MixedRealityToolkit**</span><span class="sxs-lookup"><span data-stu-id="f63ae-256">Select the **MixedRealityToolkit** game object</span></span>

1. <span data-ttu-id="f63ae-257">Selezionare **Copia e personalizza** il profilo corrente</span><span class="sxs-lookup"><span data-stu-id="f63ae-257">Select **Copy and Customize** the current profile</span></span>

1. <span data-ttu-id="f63ae-258">Passare alla sezione Input e selezionare **Clona** per abilitare la modifica del profilo di input</span><span class="sxs-lookup"><span data-stu-id="f63ae-258">Navigate to the Input section and select **Clone** to enable modification of the Input profile</span></span>

1. <span data-ttu-id="f63ae-259">Scorrere verso il basso fino alla sezione Voce nel profilo di input e clonare il profilo voce</span><span class="sxs-lookup"><span data-stu-id="f63ae-259">Scroll down to the Speech section in the Input profile and clone the Speech Profile</span></span>

    ![Profilo delle parole chiave vocali nell'oggetto gioco MRTK](../images/interactive-element/InEditor/SpeechKeywordProfileClone.png) 

1. <span data-ttu-id="f63ae-261">Selezionare Aggiungi un nuovo comando vocale</span><span class="sxs-lookup"><span data-stu-id="f63ae-261">Select Add a New Speech Command</span></span>

    ![Aggiunta di una nuova parola chiave vocale nel profilo MRTK](../images/interactive-element/InEditor/SpeechKeywordProfileAddKeyword.png) 

1. <span data-ttu-id="f63ae-263">Immettere la nuova parola chiave.</span><span class="sxs-lookup"><span data-stu-id="f63ae-263">Enter the new keyword.</span></span> <span data-ttu-id="f63ae-264">Facoltativo: modificare KeyCode in F5 (o un altro KeyCode) per consentire il test nell'editor.</span><span class="sxs-lookup"><span data-stu-id="f63ae-264">Optional: Change the KeyCode to F5 (or another KeyCode) to allow for testing in editor.</span></span> 

    ![Configurazione della parola chiave speech nel profilo MRTK](../images/interactive-element/InEditor/SpeechKeywordProfileAddKeywordName.png) 

1. <span data-ttu-id="f63ae-266">Tornare al controllo di stato Interactive Element Speech Keyword (Parola chiave voce elemento interattivo) e selezionare **Add Keyword (Aggiungi parola chiave)**</span><span class="sxs-lookup"><span data-stu-id="f63ae-266">Go back to the Interactive Element Speech Keyword state inspector and select **Add Keyword**</span></span> 

    ![Aggiunta di una parola chiave al componente dell'elemento interattivo](../images/interactive-element/InEditor/SpeechKeywordAddKeyword.png) 

    ![Convalida e registrazione delle parole chiave](../images/interactive-element/InEditor/SpeechKeywordAddKeywordBlank.png) 

1. <span data-ttu-id="f63ae-269">Immettere la nuova parola chiave appena registrata nel profilo voce</span><span class="sxs-lookup"><span data-stu-id="f63ae-269">Enter the new keyword that was just registered in the Speech Profile</span></span>

    ![Immissione di una nuova parola chiave vocale](../images/interactive-element/InEditor/SpeechKeywordEnterKeyword.png) 


<span data-ttu-id="f63ae-271">Per testare lo stato parola chiave voce nell'editor, premere keyCode definito nel passaggio 6 (F5) per simulare l'evento riconoscimento della parola chiave vocale.</span><span class="sxs-lookup"><span data-stu-id="f63ae-271">To test the Speech Keyword state in editor, press the KeyCode that was defined in step 6 (F5) to simulate the speech keyword recognized event.</span></span>

#### <a name="getting-speech-keyword-state-events"></a><span data-ttu-id="f63ae-272">Recupero di eventi relativi allo stato delle parole chiave vocali</span><span class="sxs-lookup"><span data-stu-id="f63ae-272">Getting Speech Keyword State Events</span></span>

<span data-ttu-id="f63ae-273">Tipo di configurazione dell'evento per SpeechKeyword State: `SpeechKeywordEvents`</span><span class="sxs-lookup"><span data-stu-id="f63ae-273">Event configuration type for the SpeechKeyword State: `SpeechKeywordEvents`</span></span>

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

## <a name="custom-states"></a><span data-ttu-id="f63ae-274">Stati personalizzati</span><span class="sxs-lookup"><span data-stu-id="f63ae-274">Custom States</span></span>

### <a name="how-to-create-a-custom-state-via-inspector"></a><span data-ttu-id="f63ae-275">Come creare uno stato personalizzato tramite Inspector</span><span class="sxs-lookup"><span data-stu-id="f63ae-275">How to Create a Custom State via Inspector</span></span> 

<span data-ttu-id="f63ae-276">Lo stato personalizzato creato tramite il controllo verrà inizializzato con la configurazione dell'evento di stato predefinita.</span><span class="sxs-lookup"><span data-stu-id="f63ae-276">The custom state created via inspector will be initialized with the default state event configuration.</span></span> <span data-ttu-id="f63ae-277">La configurazione dell'evento predefinita per uno stato personalizzato è di tipo `StateEvents` e contiene gli eventi OnStateOn e OnStateOff.</span><span class="sxs-lookup"><span data-stu-id="f63ae-277">The default event configuration for a custom state is of type `StateEvents` and contains the OnStateOn and OnStateOff events.</span></span>

1. <span data-ttu-id="f63ae-278">Passare a **Crea stato personalizzato nel** controllo per elemento interattivo.</span><span class="sxs-lookup"><span data-stu-id="f63ae-278">Navigate to **Create Custom State** in the inspector for Interactive Element.</span></span>
    
    ![Creazione di uno stato personalizzato](../images/interactive-element/InEditor/InteractiveElementCreateCustomState.png)

1. <span data-ttu-id="f63ae-280">Immettere il nome del nuovo stato.</span><span class="sxs-lookup"><span data-stu-id="f63ae-280">Enter the name of the new state.</span></span> <span data-ttu-id="f63ae-281">Questo nome deve essere univoco e non può essere uguale agli stati di base esistenti.</span><span class="sxs-lookup"><span data-stu-id="f63ae-281">This name must be unique and cannot be the same as the existing core states.</span></span> 
    
    ![Immissione del nome di un nuovo stato personalizzato](../images/interactive-element/InEditor/InteractiveElementCreateCustomStateName.png)

1. <span data-ttu-id="f63ae-283">Selezionare **Imposta nome stato da** aggiungere all'elenco degli stati.</span><span class="sxs-lookup"><span data-stu-id="f63ae-283">Select **Set State Name** to add to the state list.</span></span>
    
    ![Aggiungere uno stato personalizzato all'elenco di stati](../images/interactive-element/InEditor/InteractiveElementCreateCustomStateNameSet.png)

   <span data-ttu-id="f63ae-285">Questo stato personalizzato viene inizializzato con la configurazione `StateEvents` dell'evento predefinita che contiene gli `OnStateOn` eventi `OnStateOff` e .</span><span class="sxs-lookup"><span data-stu-id="f63ae-285">This custom state is initialized with the default `StateEvents` event configuration which contains the `OnStateOn` and `OnStateOff` events.</span></span> <span data-ttu-id="f63ae-286">Per creare una configurazione di evento personalizzata per un nuovo stato, vedere: [Creazione di uno stato personalizzato con una configurazione di eventi personalizzati.](#creating-a-custom-state-with-a-custom-event-configuration)</span><span class="sxs-lookup"><span data-stu-id="f63ae-286">To create a custom event configuration for a new state see: [Creating a Custom State with a Custom Event Configuration](#creating-a-custom-state-with-a-custom-event-configuration).</span></span>
    
    ![Nuovo stato visualizzato nel componente dell'elemento interattivo](../images/interactive-element/InEditor/InteractiveElementCreateCustomStateEventConfig.png)


### <a name="how-to-create-a-custom-state-via-script&quot;></a><span data-ttu-id=&quot;f63ae-288&quot;>Come creare uno stato personalizzato tramite script</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;f63ae-288&quot;>How to Create a Custom State via Script</span></span>

```c#
interactiveElement.AddNewState(&quot;MyNewState");

// A new state by default is initialized with a the default StateEvents configuration which contains the 
// OnStateOn and OnStateOff events

StateEvents myNewStateEvents = interactiveElement.GetStateEvents<StateEvents>("MyNewState");

myNewStateEvents.OnStateOn.AddListener(() =>
{
    Debug.Log($"MyNewState is On");
});

```

### <a name="creating-a-custom-state-with-a-custom-event-configuration"></a><span data-ttu-id="f63ae-289">Creazione di uno stato personalizzato con una configurazione di eventi personalizzati</span><span class="sxs-lookup"><span data-stu-id="f63ae-289">Creating a Custom State with a Custom Event Configuration</span></span> 

<span data-ttu-id="f63ae-290">I file di esempio per uno stato personalizzato denominato **Keyboard** sono disponibili qui: MRTK\SDK\Experimental\InteractiveElement\Examples\Scripts\CustomStateExample</span><span class="sxs-lookup"><span data-stu-id="f63ae-290">Example files for a custom state named **Keyboard** are located here: MRTK\SDK\Experimental\InteractiveElement\Examples\Scripts\CustomStateExample</span></span>

<span data-ttu-id="f63ae-291">La procedura seguente illustra un esempio esistente di creazione di file di configurazione e ricevitore di eventi di stato personalizzati.</span><span class="sxs-lookup"><span data-stu-id="f63ae-291">The following steps walk through an existing example of creating a custom state event configuration and receiver files.</span></span>

1. <span data-ttu-id="f63ae-292">Si pensi a un nome di stato.</span><span class="sxs-lookup"><span data-stu-id="f63ae-292">Think of a state name.</span></span>  <span data-ttu-id="f63ae-293">Questo nome deve essere univoco e non può corrispondere agli stati principali esistenti.</span><span class="sxs-lookup"><span data-stu-id="f63ae-293">This name must be unique and cannot be the same as the existing core states.</span></span> <span data-ttu-id="f63ae-294">Ai fini di questo esempio, il nome dello stato sarà **Tastiera**.</span><span class="sxs-lookup"><span data-stu-id="f63ae-294">For the purposes of this example, the state name is going to be **Keyboard**.</span></span>

1. <span data-ttu-id="f63ae-295">Creare due file con estensione cs denominati state name + "Receiver" e state name + "Events".</span><span class="sxs-lookup"><span data-stu-id="f63ae-295">Create two .cs files named state name + "Receiver" and state name + "Events".</span></span> <span data-ttu-id="f63ae-296">La denominazione di questi file viene presa in considerazione internamente e deve seguire la convenzione nome stato + evento/ricevitore.</span><span class="sxs-lookup"><span data-stu-id="f63ae-296">The naming of these files are taken into consideration internally and must follow the state name + Event/Receiver convention.</span></span> 

    ![Script di stato della tastiera](../images/interactive-element/InEditor/KeyboardStateFiles.png)

1. <span data-ttu-id="f63ae-298">Per altri dettagli sul contenuto dei file, vedere i file KeyboardEvents.cs e KeyboardReceiver.cs.</span><span class="sxs-lookup"><span data-stu-id="f63ae-298">See the KeyboardEvents.cs and KeyboardReceiver.cs files for more details on file contents.</span></span> <span data-ttu-id="f63ae-299">Le nuove classi di configurazione degli eventi devono ereditare da e le nuove classi del ricevitore `BaseInteractionEventConfiguration` di eventi devono ereditare da `BaseEventReceiver` .</span><span class="sxs-lookup"><span data-stu-id="f63ae-299">New event configuration classes must inherit from `BaseInteractionEventConfiguration` and new event receiver classes must inherit from `BaseEventReceiver`.</span></span>  <span data-ttu-id="f63ae-300">Esempi di impostazione dello stato per lo stato della tastiera si trovano nel `CustomStateSettingExample.cs` file .</span><span class="sxs-lookup"><span data-stu-id="f63ae-300">Examples on state setting for the Keyboard state are located in the `CustomStateSettingExample.cs` file.</span></span> 

1. <span data-ttu-id="f63ae-301">Aggiungere lo stato all'elemento interattivo usando il nome dello stato. Il nome dello stato verrà riconosciuto se sono presenti file di configurazione dell'evento e del ricevitore di eventi.</span><span class="sxs-lookup"><span data-stu-id="f63ae-301">Add the state to Interactive Element using the state name, the state name will be recognized if event configuration and event receiver files exist.</span></span>  <span data-ttu-id="f63ae-302">Le proprietà nel file di configurazione dell'evento personalizzato dovrebbero essere visualizzate nel controllo.</span><span class="sxs-lookup"><span data-stu-id="f63ae-302">The properties in the custom event configuration file should appear in the inspector.</span></span>

    <span data-ttu-id="f63ae-303">![Aggiunta di uno stato personalizzato all'elemento interattivo ](../images/interactive-element/InEditor/AddKeyboardState.png) ![ Stato personalizzato riconosciuto nell'elemento interattivo](../images/interactive-element/InEditor/SetKeyboardStateName.png)</span><span class="sxs-lookup"><span data-stu-id="f63ae-303">![Adding custom state to interactive element](../images/interactive-element/InEditor/AddKeyboardState.png) ![Custom state recognized in the interactive element](../images/interactive-element/InEditor/SetKeyboardStateName.png)</span></span>


1. <span data-ttu-id="f63ae-304">Per altri esempi di file di configurazione e ricevitore di eventi, vedere i file nei percorsi seguenti:</span><span class="sxs-lookup"><span data-stu-id="f63ae-304">For more examples of event configuration and event receiver files see the files at these paths:</span></span>    
- <span data-ttu-id="f63ae-305">MRTK\SDK\Experimental\InteractiveElement\InteractiveElement\Events\EventConfigurations</span><span class="sxs-lookup"><span data-stu-id="f63ae-305">MRTK\SDK\Experimental\InteractiveElement\InteractiveElement\Events\EventConfigurations</span></span>
- <span data-ttu-id="f63ae-306">MRTK\SDK\Experimental\InteractiveElement\InteractiveElement\Events\EventReceivers</span><span class="sxs-lookup"><span data-stu-id="f63ae-306">MRTK\SDK\Experimental\InteractiveElement\InteractiveElement\Events\EventReceivers</span></span>

## <a name="example-scene"></a><span data-ttu-id="f63ae-307">Scena di esempio</span><span class="sxs-lookup"><span data-stu-id="f63ae-307">Example Scene</span></span> 

<span data-ttu-id="f63ae-308">La scena di esempio per Interactive Element + State Visualizer si trova qui: MRTK\SDK\Experimental\InteractiveElement\Examples\InteractiveElementExampleScene.unity</span><span class="sxs-lookup"><span data-stu-id="f63ae-308">The example scene for Interactive Element + State Visualizer is located here: MRTK\SDK\Experimental\InteractiveElement\Examples\InteractiveElementExampleScene.unity</span></span>

![Scena di esempio con elemento interattivo e visualizzatore di stato](../images/interactive-element/InEditor/ExampleScene.png)

### <a name="compressable-button"></a><span data-ttu-id="f63ae-310">Pulsante comprimibile</span><span class="sxs-lookup"><span data-stu-id="f63ae-310">Compressable Button</span></span>

<span data-ttu-id="f63ae-311">La scena di esempio contiene prefab denominati e , che rispecchiano il comportamento dei pulsanti, costruiti usando l'elemento interattivo e `CompressableButton` `CompressableButtonToggle` il `PressableButtonHoloLens2` visualizzatore di stato.</span><span class="sxs-lookup"><span data-stu-id="f63ae-311">The example scene contains prefabs named `CompressableButton` and `CompressableButtonToggle`, these prefabs mirror the behavior of the `PressableButtonHoloLens2` buttons, that are constructed using Interactive Element and the State Visualizer.</span></span> <span data-ttu-id="f63ae-312">Il `CompressableButton` componente è attualmente una combinazione di con come classe di `PressableButton`  +  `PressableButtonHoloLens2` `BaseInteractiveElement` base.</span><span class="sxs-lookup"><span data-stu-id="f63ae-312">The `CompressableButton` component is currently a combination of `PressableButton` + `PressableButtonHoloLens2` with `BaseInteractiveElement`as a base class.</span></span> 

## <a name="state-visualizer-experimental"></a><span data-ttu-id="f63ae-313">Visualizzatore di stato [Sperimentale]</span><span class="sxs-lookup"><span data-stu-id="f63ae-313">State Visualizer [Experimental]</span></span>

<span data-ttu-id="f63ae-314">Il componente Visualizzatore stato aggiunge animazioni a un oggetto in base agli stati definiti in un componente elemento interattivo collegato.</span><span class="sxs-lookup"><span data-stu-id="f63ae-314">The State Visualizer component adds animations to an object based on the states defined in a linked Interactive Element component.</span></span> <span data-ttu-id="f63ae-315">Questo componente crea asset di animazione, li inserisce nella cartella MixedRealityToolkit.Generated e abilita l'impostazione semplificata dei fotogrammi chiave di animazione tramite l'aggiunta di proprietà animabili a un oggetto gioco di destinazione.</span><span class="sxs-lookup"><span data-stu-id="f63ae-315">This component creates animation assets, places them in the MixedRealityToolkit.Generated folder and enables simplified animation keyframe setting through adding Animatable properties to a target game object.</span></span> <span data-ttu-id="f63ae-316">Per abilitare le transizioni di animazione tra gli stati, viene creato un asset di Animator Controller e viene generata una macchina a stati predefinita con i parametri associati ed eventuali transizioni di stato.</span><span class="sxs-lookup"><span data-stu-id="f63ae-316">To enable animation transitions between states, an Animator Controller asset is created and a default state machine is generated with associated parameters and any state transitions.</span></span>  <span data-ttu-id="f63ae-317">La macchina a stati può essere visualizzata nella finestra animatore di Unity.</span><span class="sxs-lookup"><span data-stu-id="f63ae-317">The state machine can be viewed in Unity's Animator window.</span></span>

### <a name="state-visualizer-and-unity-animation-system"></a><span data-ttu-id="f63ae-318">Visualizzatore di stato e sistema di animazione Unity</span><span class="sxs-lookup"><span data-stu-id="f63ae-318">State Visualizer and Unity Animation System</span></span>

<span data-ttu-id="f63ae-319">Il visualizzatore di stato sfrutta attualmente il sistema di animazione Unity.</span><span class="sxs-lookup"><span data-stu-id="f63ae-319">The State Visualizer currently leverages the Unity Animation System.</span></span> 

<span data-ttu-id="f63ae-320">Quando  si preme il pulsante Genera nuove clip di animazione nel visualizzatore di stato, vengono generati nuovi asset di clip di animazione in base ai nomi di stato nell'elemento interattivo e inseriti nella cartella MixedRealityToolkit.Generated.</span><span class="sxs-lookup"><span data-stu-id="f63ae-320">When the **Generate New Animation Clips** button in the State Visualizer is pressed, new animation clip assets are generated based on the state names in Interactive Element and are placed in the MixedRealityToolkit.Generated folder.</span></span> <span data-ttu-id="f63ae-321">La proprietà Clip animazione in ogni contenitore di stato è impostata sul clip di animazione associato.</span><span class="sxs-lookup"><span data-stu-id="f63ae-321">The Animation Clip property in each state container is set to the associated animation clip.</span></span>

![Clip di animazione nel componente visualizzatore di stato](../images/interactive-element/StateVisualizer/AnimationClips.png)

<span data-ttu-id="f63ae-323">Viene generata anche una macchina a stati di [Animator](https://docs.unity3d.com/Manual/AnimationOverview.html) per gestire le transizioni uniformi tra le clip di animazione.</span><span class="sxs-lookup"><span data-stu-id="f63ae-323">An [Animator State Machine](https://docs.unity3d.com/Manual/AnimationOverview.html) is also generated to manage smooth transitions between animation clips.</span></span>  <span data-ttu-id="f63ae-324">Per impostazione predefinita, la macchina a stati usa [Qualsiasi stato](https://docs.unity3d.com/Manual/class-State.html) per consentire le transizioni tra qualsiasi stato nell'elemento interattivo.</span><span class="sxs-lookup"><span data-stu-id="f63ae-324">By default, the state machine utilizes the [Any State](https://docs.unity3d.com/Manual/class-State.html) to allow transitions between any state in Interactive Element.</span></span> 

<span data-ttu-id="f63ae-325">[I visualizzatori di stato attivati nell'animatore](https://docs.unity3d.com/Manual/AnimationParameters.html) vengono generati anche per ogni stato. I parametri del trigger vengono usati nel visualizzatore di stato per attivare un'animazione.</span><span class="sxs-lookup"><span data-stu-id="f63ae-325">[State visualizers triggered in the animator](https://docs.unity3d.com/Manual/AnimationParameters.html) are also generated for each state, the trigger parameters are used in the State Visualizer to trigger an animation.</span></span>

![Macchina a stati Unity](../images/interactive-element/StateVisualizer/UnityStateMachine.png)

### <a name="runtime-limitations"></a><span data-ttu-id="f63ae-327">Limitazioni di runtime</span><span class="sxs-lookup"><span data-stu-id="f63ae-327">Runtime Limitations</span></span> 

<span data-ttu-id="f63ae-328">Il visualizzatore di stato deve essere aggiunto a un oggetto tramite il controllo e non può essere aggiunto tramite script.</span><span class="sxs-lookup"><span data-stu-id="f63ae-328">The State Visualizer must be added to an object via the Inspector and cannot be added via script.</span></span>  <span data-ttu-id="f63ae-329">Le proprietà che modificano AnimatorStateMachine/AnimationController sono contenute in uno spazio dei nomi dell'editor ( ) che vengono rimosse `UnityEditor.Animations` quando viene compilata l'app.</span><span class="sxs-lookup"><span data-stu-id="f63ae-329">The properties that modify the AnimatorStateMachine/AnimationController are contained in an editor namespace (`UnityEditor.Animations`) which get removed when the app is built.</span></span>

## <a name="how-to-use-the-state-visualizer"></a><span data-ttu-id="f63ae-330">Come usare il visualizzatore di stato</span><span class="sxs-lookup"><span data-stu-id="f63ae-330">How to use the State Visualizer</span></span>

1. <span data-ttu-id="f63ae-331">Creare un cubo</span><span class="sxs-lookup"><span data-stu-id="f63ae-331">Create a Cube</span></span>
1. <span data-ttu-id="f63ae-332">Associare un elemento interattivo</span><span class="sxs-lookup"><span data-stu-id="f63ae-332">Attach Interactive Element</span></span>
1. <span data-ttu-id="f63ae-333">Attach State Visualizer</span><span class="sxs-lookup"><span data-stu-id="f63ae-333">Attach State Visualizer</span></span>
1. <span data-ttu-id="f63ae-334">Selezionare Generate **New Animation Clips (Genera nuove clip di animazione)**</span><span class="sxs-lookup"><span data-stu-id="f63ae-334">Select **Generate New Animation Clips**</span></span>

    ![Generazione di nuove clip di animazione](../images/interactive-element/StateVisualizer/GenerateAnimationClips.png)

    ![Visualizzazione delle clip di animazione generate nei componenti del visualizzatore e degli elementi interattivi](../images/interactive-element/StateVisualizer/GenerateAnimationClips2.png)

1. <span data-ttu-id="f63ae-337">Nel contenitore Stato attivo selezionare **Aggiungi destinazione**</span><span class="sxs-lookup"><span data-stu-id="f63ae-337">In the Focus state container, select **Add Target**</span></span>

    ![Aggiunta della destinazione del visualizzatore di stato](../images/interactive-element/StateVisualizer/AddTarget.png)

1. <span data-ttu-id="f63ae-339">Trascinare l'oggetto gioco corrente nel campo di destinazione</span><span class="sxs-lookup"><span data-stu-id="f63ae-339">Drag the current game object to the target field</span></span> 

    ![Impostazione della destinazione del visualizzatore di stato](../images/interactive-element/StateVisualizer/SetTarget.png)

1. <span data-ttu-id="f63ae-341">Aprire il riquadro proprietà animabili del cubo</span><span class="sxs-lookup"><span data-stu-id="f63ae-341">Open the Cube Animatable Properties foldout</span></span>
1. <span data-ttu-id="f63ae-342">Selezionare il menu a discesa delle proprietà Animabile e selezionare **Colore**</span><span class="sxs-lookup"><span data-stu-id="f63ae-342">Select the Animatable property drop down menu and select **Color**</span></span>

    ![Impostazione del colore del visualizzatore di stato](../images/interactive-element/StateVisualizer/SetColor.png)

1. <span data-ttu-id="f63ae-344">Selezionare **Add the Color Animatable Property (Aggiungi proprietà animabile color)**</span><span class="sxs-lookup"><span data-stu-id="f63ae-344">Select **Add the Color Animatable Property**</span></span>

    ![Selezione della proprietà animabile color color animatable del visualizzatore](../images/interactive-element/StateVisualizer/SetColorProperty.png)

1. <span data-ttu-id="f63ae-346">Scegliere un colore</span><span class="sxs-lookup"><span data-stu-id="f63ae-346">Choose a Color</span></span> 

    ![Scelta di un colore del visualizzatore dalla ruota dei colori](../images/interactive-element/StateVisualizer/SetBlueColor.png)

1. <span data-ttu-id="f63ae-348">Premere play e osservare il cambio di colore di transizione</span><span class="sxs-lookup"><span data-stu-id="f63ae-348">Press play and observe the transitional color change</span></span>

    ![Esempio di modifica del colore di transizione con l'interazione con la mano virtuale](../images/interactive-element/InEditor/Gifs/FocusColorChange.gif)

## <a name="animatable-properties"></a><span data-ttu-id="f63ae-350">Proprietà animabili</span><span class="sxs-lookup"><span data-stu-id="f63ae-350">Animatable Properties</span></span>

<span data-ttu-id="f63ae-351">Lo scopo principale di Proprietà animabili è semplificare l'impostazione del fotogramma chiave della clip di animazione.</span><span class="sxs-lookup"><span data-stu-id="f63ae-351">The primary purpose of the Animatable Properties is to simplify animation clip keyframe setting.</span></span>  <span data-ttu-id="f63ae-352">Se un utente ha familiarità con Unity Animation System e preferisce impostare direttamente i fotogrammi chiave nelle clip di animazione generate, non può semplicemente aggiungere proprietà animabili a un oggetto di destinazione e aprire il clip nella finestra Animazione di Unity (Animazione di Windows > > Animation).</span><span class="sxs-lookup"><span data-stu-id="f63ae-352">If a user is familiar with the Unity Animation System and would prefer to directly set keyframes on the generated animation clips, then they can simply not add Animatable properties to a target object and open the clip in Unity's Animation window (Windows > Animation > Animation).</span></span> 

<span data-ttu-id="f63ae-353">Se si usano le proprietà animabili per l'animazione, il tipo di curva viene impostato su EaseInOut.</span><span class="sxs-lookup"><span data-stu-id="f63ae-353">If using the Animatable properties for animation, the curve type is set to EaseInOut.</span></span>

<span data-ttu-id="f63ae-354">**Proprietà animabili correnti:**</span><span class="sxs-lookup"><span data-stu-id="f63ae-354">**Current Animatable Properties:**</span></span>
- [<span data-ttu-id="f63ae-355">Offset della scala</span><span class="sxs-lookup"><span data-stu-id="f63ae-355">Scale Offset</span></span>](#scale-offset)
- [<span data-ttu-id="f63ae-356">Offset della posizione</span><span class="sxs-lookup"><span data-stu-id="f63ae-356">Position Offset</span></span>](#position-offset)
- [<span data-ttu-id="f63ae-357">Colore</span><span class="sxs-lookup"><span data-stu-id="f63ae-357">Color</span></span>](#color)
- [<span data-ttu-id="f63ae-358">Colore shader</span><span class="sxs-lookup"><span data-stu-id="f63ae-358">Shader Color</span></span>](#shader-color)
- [<span data-ttu-id="f63ae-359">Shader Float</span><span class="sxs-lookup"><span data-stu-id="f63ae-359">Shader Float</span></span>](#shader-float)
- [<span data-ttu-id="f63ae-360">Vettore shader</span><span class="sxs-lookup"><span data-stu-id="f63ae-360">Shader Vector</span></span>](#shader-vector)

### <a name="scale-offset"></a><span data-ttu-id="f63ae-361">Offset della scala</span><span class="sxs-lookup"><span data-stu-id="f63ae-361">Scale Offset</span></span>

<span data-ttu-id="f63ae-362">La proprietà Scale Offset Animatable accetta la scala corrente dell'oggetto e aggiunge l'offset definito.</span><span class="sxs-lookup"><span data-stu-id="f63ae-362">The Scale Offset Animatable property takes the current scale of the object and adds the defined offset.</span></span>

![Offset della scala con l'interazione con la mano virtuale](../images/interactive-element/InEditor/Gifs/ScaleOffset.gif)

### <a name="position-offset"></a><span data-ttu-id="f63ae-364">Offset della posizione</span><span class="sxs-lookup"><span data-stu-id="f63ae-364">Position Offset</span></span>

<span data-ttu-id="f63ae-365">La proprietà Position Offset Animatable accetta la posizione corrente dell'oggetto e aggiunge l'offset definito.</span><span class="sxs-lookup"><span data-stu-id="f63ae-365">The Position Offset Animatable property takes the current position of the object and adds the defined offset.</span></span>

![Offset della posizione con l'interazione con la mano virtuale](../images/interactive-element/InEditor/Gifs/PositionOffset.gif)

### <a name="color"></a><span data-ttu-id="f63ae-367">Color</span><span class="sxs-lookup"><span data-stu-id="f63ae-367">Color</span></span>

<span data-ttu-id="f63ae-368">La proprietà Color Animatable rappresenta il colore principale di un materiale se il materiale ha una proprietà di colore principale.</span><span class="sxs-lookup"><span data-stu-id="f63ae-368">The Color Animatable property represents the main color of a material if the material has a main color property.</span></span> <span data-ttu-id="f63ae-369">Questa proprietà aggiunge un'animazione alla `material._Color` proprietà .</span><span class="sxs-lookup"><span data-stu-id="f63ae-369">This property animates the `material._Color` property.</span></span>

![Modifica del colore dello stato attivo con l'interazione con la mano virtuale](../images/interactive-element/InEditor/Gifs/FocusColorChange.gif)

### <a name="shader-color"></a><span data-ttu-id="f63ae-371">Colore shader</span><span class="sxs-lookup"><span data-stu-id="f63ae-371">Shader Color</span></span>

<span data-ttu-id="f63ae-372">La proprietà Shader Color Animatable fa riferimento a una proprietà shader di tipo color.</span><span class="sxs-lookup"><span data-stu-id="f63ae-372">The Shader Color Animatable property refers to a shader property of type color.</span></span> <span data-ttu-id="f63ae-373">Un nome di proprietà è obbligatorio per tutte le proprietà dello shader.</span><span class="sxs-lookup"><span data-stu-id="f63ae-373">A property name is required for all shader properties.</span></span> <span data-ttu-id="f63ae-374">La gif seguente illustra l'animazione di una proprietà di colore shader Fill_Color che non è il colore principale del materiale.</span><span class="sxs-lookup"><span data-stu-id="f63ae-374">The gif below demonstrates animating a shader color property named Fill_Color that is not the main material color.</span></span>  <span data-ttu-id="f63ae-375">Osservare i valori che cambiano nel controllo materiali.</span><span class="sxs-lookup"><span data-stu-id="f63ae-375">Observe the changing values in the material inspector.</span></span>

![Colore ombreggiatura con interazione con la mano virtuale](../images/interactive-element/InEditor/Gifs/ShaderColor.gif)

### <a name="shader-float"></a><span data-ttu-id="f63ae-377">Shader Float</span><span class="sxs-lookup"><span data-stu-id="f63ae-377">Shader Float</span></span>

<span data-ttu-id="f63ae-378">La proprietà Shader Float Animatable fa riferimento a una proprietà shader di tipo float.</span><span class="sxs-lookup"><span data-stu-id="f63ae-378">The Shader Float Animatable property refers to a shader property of type float.</span></span> <span data-ttu-id="f63ae-379">Un nome di proprietà è obbligatorio per tutte le proprietà dello shader.</span><span class="sxs-lookup"><span data-stu-id="f63ae-379">A property name is required for all shader properties.</span></span> <span data-ttu-id="f63ae-380">Nella gif seguente osservare i valori che cambiano nel controllo materiale per la proprietà Metallic.</span><span class="sxs-lookup"><span data-stu-id="f63ae-380">In the gif below, observe the changing values in the material inspector for the Metallic property.</span></span> 

![Float shader con interazione con la mano virtuale](../images/interactive-element/InEditor/Gifs/ShaderFloat.gif)

### <a name="shader-vector"></a><span data-ttu-id="f63ae-382">Vettore shader</span><span class="sxs-lookup"><span data-stu-id="f63ae-382">Shader Vector</span></span>

<span data-ttu-id="f63ae-383">La proprietà Animatable del vettore shader fa riferimento a una proprietà shader di tipo Vector4.</span><span class="sxs-lookup"><span data-stu-id="f63ae-383">The Shader Vector Animatable property refers to a shader property of type Vector4.</span></span> <span data-ttu-id="f63ae-384">Un nome di proprietà è obbligatorio per tutte le proprietà dello shader.</span><span class="sxs-lookup"><span data-stu-id="f63ae-384">A property name is required for all shader properties.</span></span> <span data-ttu-id="f63ae-385">Nella gif seguente osservare i valori che cambiano nel controllo materiale per la proprietà Tiling (Main Tex_ST).</span><span class="sxs-lookup"><span data-stu-id="f63ae-385">In the gif below, observe the changing values in the material inspector for the Tiling (Main Tex_ST) property.</span></span> 

![Vettore shader con interazione con la mano virtuale](../images/interactive-element/InEditor/Gifs/ShaderVector.gif)


### <a name="how-to-find-animatable-shader-property-names"></a><span data-ttu-id="f63ae-387">Come trovare i nomi delle proprietà shader animabili</span><span class="sxs-lookup"><span data-stu-id="f63ae-387">How to Find Animatable Shader Property Names</span></span>

1. <span data-ttu-id="f63ae-388">Passare all'animazione > finestra > animazione</span><span class="sxs-lookup"><span data-stu-id="f63ae-388">Navigate to Window > Animation > Animation</span></span>
1. <span data-ttu-id="f63ae-389">Assicurarsi che l'oggetto con il visualizzatore di stato sia selezionato nella gerarchia</span><span class="sxs-lookup"><span data-stu-id="f63ae-389">Ensure that the object with the State Visualizer is selected in the hierarchy</span></span>
1. <span data-ttu-id="f63ae-390">Selezionare un clip di animazione nella finestra Animazione</span><span class="sxs-lookup"><span data-stu-id="f63ae-390">Select any animation clip in the Animation window</span></span>
1. <span data-ttu-id="f63ae-391">Selezionare **Aggiungi proprietà,** aprire il foldout renderer mesh</span><span class="sxs-lookup"><span data-stu-id="f63ae-391">Select **Add Property**, open the Mesh Renderer foldout</span></span> 

    ![Aggiunta della proprietà di animazione nella finestra Animator](../images/interactive-element/StateVisualizer/AnimationWindow.png)

1. <span data-ttu-id="f63ae-393">Questo elenco contiene i nomi di tutti i nomi delle proprietà animabili</span><span class="sxs-lookup"><span data-stu-id="f63ae-393">This list contains the names of all the Animatable property names</span></span> 

    ![Proprietà di animazione del renderer mesh nella finestra animatore](../images/interactive-element/StateVisualizer/MeshRendererProperties.png)

## <a name="see-also"></a><span data-ttu-id="f63ae-395">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="f63ae-395">See also</span></span>

- [<span data-ttu-id="f63ae-396">**Pulsanti**</span><span class="sxs-lookup"><span data-stu-id="f63ae-396">**Buttons**</span></span>](../ux-building-blocks/button.md)
- [<span data-ttu-id="f63ae-397">**Controllo Bounds**</span><span class="sxs-lookup"><span data-stu-id="f63ae-397">**Bounds Control**</span></span>](../ux-building-blocks/bounds-control.md)
- [<span data-ttu-id="f63ae-398">**Raccolta di oggetti Grid**</span><span class="sxs-lookup"><span data-stu-id="f63ae-398">**Grid Object Collection**</span></span>](../ux-building-blocks/object-collection.md)
- [<span data-ttu-id="f63ae-399">**Risolutore RadialView**</span><span class="sxs-lookup"><span data-stu-id="f63ae-399">**RadialView Solver**</span></span>](../ux-building-blocks/solvers/solver.md)

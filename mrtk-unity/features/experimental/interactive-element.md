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
# <a name="interactive-element-experimental"></a>Elemento Interactive [Sperimentale]

Un punto di ingresso centralizzato semplificato al sistema di input MRTK. Contiene i metodi di gestione dello stato, la gestione degli eventi e la logica di impostazione dello stato per gli stati di interazione principali.

Interactive Element è una funzionalità sperimentale supportata in Unity 2019.3 e versioni fino a quando usa una funzionalità nuova di Unity 2019.3: [Serialize Reference](https://docs.unity3d.com/ScriptReference/SerializeReference.html).

### <a name="interactive-element-inspector"></a>Controllo elemento interattivo

Durante la modalità di riproduzione, il controllo elemento interattivo fornisce un feedback visivo che indica se lo stato corrente è attivo o meno. Se uno stato è attivo, verrà evidenziato con un colore ciano.  Se lo stato non è attivo, il colore non viene modificato. I numeri accanto agli stati nel controllo sono i valori dello stato. Se lo stato è attivo, il valore è 1, se lo stato non è attivo il valore è 0.

![Elemento interattivo con interazione con la mano virtuale](../images/interactive-element/InEditor/Gifs/InspectorHighlightEditor.gif)

## <a name="core-states"></a>Stati principali

L'elemento Interactive contiene gli stati principali e supporta l'aggiunta [di stati personalizzati.](#custom-states)  Uno stato principale è uno stato che ha già la logica di impostazione dello stato definita in `BaseInteractiveElement` . Di seguito è riportato un elenco degli stati principali correnti guidati dall'input: 

### <a name="current-core-states"></a>Stati principali correnti

- [Default](#default-state) 

Stati principali di interazione da vicino e da lontano:
- [Concentrarsi](#focus-state) 

Vicino agli stati core di interazione:

- [Messa a fuoco nelle vicinanze](#focus-near-state)
- [Tocco](#touch-state)

Stati principali di interazione lontano:
- [Messa a fuoco lontano](#focus-far-state)
- [Selezionare Lontano](#select-far-state)

Altri stati principali:
- [Clicked](#clicked-state)
- [Attivare e disattivare](#toggle-on-and-toggle-off-state)
- [Parola chiave Speech](#speech-keyword-state)

### <a name="how-to-add-a-core-state-via-inspector"></a>Come aggiungere uno stato core tramite Inspector

1. Passare ad **Add Core State (Aggiungi** stato core) nel controllo per Interactive Element (Elemento interattivo).

    ![Aggiungere uno stato di base tramite Inspector](../images/interactive-element/InEditor/InteractiveElementAddCoreState.png)


1. Selezionare il **pulsante Seleziona stato** per scegliere lo stato principale da aggiungere. Gli stati nel menu vengono ordinati in base al tipo di interazione.

    ![Aggiungere uno stato core tramite Inspector con lo stato selezionato](../images/interactive-element/InEditor/InteractiveElementAddCoreStateSelectState.png)

1. Aprire il foldout Configurazione eventi per visualizzare gli eventi e le proprietà associati allo stato.

    ![Aggiungere uno stato core tramite Inspector con la configurazione degli eventi](../images/interactive-element/InEditor/InteractiveElementAddCoreStateSelectStateEventConfig.png)


### <a name="how-to-add-a-core-state-via-script"></a>Come aggiungere uno stato core tramite script

Usare il `AddNewState(stateName)` metodo per aggiungere uno stato principale. Per un elenco dei nomi di stato principali disponibili, usare `CoreInteractionState` l'enumerazione .

```c#
// Add by name or add by CoreInteractionState enum to string

interactiveElement.AddNewState("SelectFar");

interactiveElement.AddNewState(CoreInteractionState.SelectFar.ToString());
```

### <a name="states-internal-structure"></a>Struttura interna States 

Gli stati nell'elemento interattivo sono di tipo `InteractionState` .  Un `InteractionState` oggetto contiene le proprietà seguenti:

- **Nome**: nome dello stato.
- **Valore**: valore dello stato.  Se lo stato è attivo, il valore dello stato è 1. Se lo stato è disattivato, il valore dello stato è 0.
- **Attivo:** indica se lo stato è attualmente attivo. Il valore della proprietà Active è true quando lo stato è attivo, false se lo stato è disattivato. 
- **Tipo di interazione:** il tipo di interazione di uno stato è il tipo di interazione a cui è destinato uno stato. 
  - `None`: non supporta alcuna forma di interazione di input.
  - `Near`: supporto vicino all'interazione. L'input viene considerato vicino all'interazione quando una mano articolata ha un contatto diretto con un altro oggetto di gioco, ad esempio la posizione in cui la mano articolata è vicina alla posizione dell'oggetto di gioco nello spazio mondiale.
  - `Far`: supporto dell'interazione da lontano. L'input viene considerato interazione da lontano quando non è necessario un contatto diretto con l'oggetto del gioco. Ad esempio, l'input tramite il raggio del controller o lo sguardo è considerato input di interazione lontano.
  - `NearAndFar`: include il supporto per le interazioni vicino e lontano. 
  - `Other`: supporto dell'interazione indipendente dal puntatore.
- **Configurazione eventi:** la configurazione degli eventi per uno stato è il punto di ingresso del profilo eventi serializzati. 

Tutte queste proprietà vengono impostate internamente nell'elemento `State Manager` contenuto in Interactive Element. Per la modifica degli stati, usare i metodi helper seguenti:

**Metodi helper per l'impostazione dello stato**

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

Il recupero della configurazione dell'evento di uno stato è specifico dello stato stesso. Ogni stato principale ha un tipo di configurazione di evento specifico, descritto di seguito nelle sezioni che descrivono ogni stato principale.

Di seguito è riportato un esempio generalizzato di recupero della configurazione degli eventi di uno stato:

```c#
// T varies depending on the core state - the specific T's are specified under each of the core state sections
T stateNameEvents = interactiveElement.GetStateEvents<T>("StateName");
```

### <a name="default-state"></a>Stato predefinito

Lo stato Predefinito è sempre presente in un elemento interattivo.  Questo stato sarà attivo solo quando tutti gli altri stati non sono attivi.  Se un altro stato diventa attivo, lo stato Predefinito verrà impostato su disattivato internamente. 

Un elemento interattivo viene inizializzato con gli stati Predefinito e Stato attivo presenti nell'elenco degli stati. Lo stato Predefinito deve essere sempre presente nell'elenco degli stati. 

#### <a name="getting-default-state-events"></a>Recupero degli eventi di stato predefiniti

Tipo di configurazione dell'evento per lo stato predefinito: `StateEvents`

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

### <a name="focus-state"></a>Stato attivo

Lo stato messa a fuoco è uno stato di interazione da vicino e da lontano che può essere ritenuto come la realtà mista equivalente al passaggio del mouse. Il fattore di distinzione tra l'interazione da vicino e da lontano per lo stato di messa a fuoco è il tipo di puntatore attivo corrente.  Se il tipo di puntatore per lo stato di messa a fuoco è il puntatore Poke, l'interazione viene considerata quasi interazione.  Se il puntatore principale non è il puntatore Poke, l'interazione viene considerata un'interazione da lontano. Lo stato attivo è presente nell'elemento interattivo per impostazione predefinita.

**Comportamento dello stato attivo** 
 ![ Stato di messa a fuoco con interazione con la mano virtuale](../images/interactive-element/InEditor/Gifs/FocusStateEditor.gif) 

**Controllo stato attivo** 
 ![ Stato dello stato attivo nell'inpsector](../images/interactive-element/InEditor/FocusStateInspector.png)

#### <a name="getting-focus-state-events&quot;></a>Recupero di eventi di stato attivo

Tipo di configurazione dell'evento per lo stato attivo: `FocusEvents`

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

#### <a name="focus-near-vs-focus-far-behavior"></a>Comportamento di messa a fuoco vicino a messa a fuoco e stato attivo lontano 

![Concentrarsi vicino e lontano con l'interazione con la mano virtuale](../images/interactive-element/InEditor/Gifs/FocusNearFocusFar.gif)

### <a name="focus-near-state"></a>Messa a fuoco vicino allo stato

Lo stato Stato attivo vicino viene impostato quando viene generato un evento di stato attivo e il puntatore primario è il puntatore Poke, un'indicazione dell'interazione vicina. 

**Messa a fuoco vicino allo stato Comportamento** 
 ![ Concentrarsi vicino allo stato con l'interazione con la mano virtuale](../images/interactive-element/InEditor/Gifs/FocusNearStateEditor.gif) 

**Focus Near State Inspector (Messa a fuoco vicino a controllo stato)** 
 ![ Messa a fuoco vicino al componente nel controllo](../images/interactive-element/InEditor/FocusNearStateInspector.png)

#### <a name="getting-focusnear-state-events&quot;></a>Recupero di eventi di stato FocusNear

Tipo di configurazione dell'evento per stato FocusNear: `FocusEvents`

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

### <a name="focus-far-state"></a>Stato attivo lontano

Lo stato Focus Far viene impostato quando il puntatore primario non è il puntatore Poke.  Ad esempio, il puntatore di raggio del controller predefinito e il puntatore GGV (Sguardo fisso, Movimento, Voce) sono considerati puntatori di interazione lontano.

**Comportamento dello stato attivo lontano** 
 ![ Stato di messa a fuoco lontano con l'interazione con la mano virtuale](../images/interactive-element/InEditor/Gifs/FocusFarStateEditor.gif)

**Focus Far State Inspector** 
 ![ Componente Distorsiva nello stato attivo nel controllo](../images/interactive-element/InEditor/FocusFarStateInspector.png)

#### <a name="getting-focus-far-state-events&quot;></a>Recupero di eventi di stato lontano dello stato attivo

Tipo di configurazione dell'evento per stato FocusFar: `FocusEvents`

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

### <a name="touch-state"></a>Stato tocco

Lo stato Tocco è uno stato di interazione vicino che viene impostato quando una mano articolata tocca direttamente l'oggetto.  Un tocco diretto significa che il dito indice della mano articolata è molto vicino alla posizione mondiale dell'oggetto. Per impostazione predefinita, `NearInteractionTouchableVolume` un componente viene collegato all'oggetto se lo stato Tocco viene aggiunto all'elenco degli stati.  La presenza di un  `NearInteractionTouchableVolume` componente o è necessaria per `NearInteractionTouchable` rilevare gli eventi touch.  La differenza tra e è che rileva un tocco in base al collisore dell'oggetto e rileva il tocco all'interno di `NearInteractionTouchableVolume` un'area definita di un `NearInteractionTouchable` `NearInteractionTouchableVolume` `NearInteractionTouchable` piano.

**Comportamento dello stato tocco** 
 ![ Stato tocco con interazione con la mano virtuale](../images/interactive-element/InEditor/Gifs/TouchStateEditor.gif)

**Controllo stato tocco** 
 ![ Componente stato tocco nel controllo](../images/interactive-element/InEditor/TouchStateInspector.png)

#### <a name="getting-touch-state-events&quot;></a>Recupero di eventi di stato tocco

Tipo di configurazione dell'evento per Lo stato tocco: `TouchEvents`

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

### <a name="select-far-state"></a>Selezionare Stato lontano

Lo stato Select Far (Seleziona da lontano) `IMixedRealityPointerHandler` è quello indicato.  Questo stato è uno stato di interazione da lontano che rileva il clic di interazione da lontano (tocco) e mantiene l'uso di puntatori di interazione da lontano, ad esempio l'indicatore di misura del raggio del controller predefinito o il puntatore GGV.  Lo stato Select Far (Seleziona da lontano) ha un'opzione nella sezione di configurazione dell'evento denominata `Global` . Se `Global` è true, viene `IMixedRealityPointerHandler` registrato come gestore di input globale.  Lo stato attivo su un oggetto non è necessario per attivare eventi di sistema di input se un gestore è registrato come globale.  Ad esempio, se un utente vuole sapere ogni volta che viene eseguito il movimento di tocco/selezione indipendentemente dall'oggetto nello stato attivo, impostare `Global` su true. 

**Selezionare Far State Behavior (Comportamento stato lontano)** 
 ![ Selezionare da lontano con l'interazione con la mano virtuale](../images/interactive-element/InEditor/Gifs/SelectFarStateEditor.gif)

**Selezionare Far State Inspector (Controllo stato lontano)** 
 ![ Selezionare il componente lontano nel controllo](../images/interactive-element/InEditor/SelectFarStateInspector.png)

#### <a name="getting-select-far-state-events&quot;></a>Recupero di eventi select far state

Tipo di configurazione dell'evento per SelectFar State: `SelectFarEvents`

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

### <a name="clicked-state"></a>Stato selezionato

Lo stato Clicked (Selezionato) viene attivato da un clic di interazione da lontano (Select Far state) (Seleziona stato lontano) per impostazione predefinita.  Questo stato viene commutato internamente su on, richiama l'evento OnClicked e quindi viene immediatamente disattivato. 

> [!NOTE]
> Il feedback visivo nel controllo in base all'attività di stato non è presente per lo stato Clicked perché viene attivata e quindi disattivata immediatamente. 

**Comportamento dello stato su cui è stato fatto clic** 
 ![ Stato selezionato con interazioni con la mano virtuale](../images/interactive-element/InEditor/Gifs/ClickedStateEditor.gif)

**Controllo di stato su cui è stato fatto clic** 
 ![ Fare clic sul componente di stato nel controllo](../images/interactive-element/InEditor/ClickedStateInspector.png)

**Esempio di stato near e far clicked**  
Lo stato selezionato può essere attivato tramite punti di ingresso aggiuntivi usando il `interactiveElement.TriggerClickedState()` metodo .  Ad esempio, se un utente vuole che un tocco vicino all'interazione attiverà un clic su un oggetto, aggiungerà il metodo come listener nello stato `TriggerClickedState()` tocco.   

![Stato vicino e lontano con interazioni con la mano virtuale](../images/interactive-element/InEditor/Gifs/NearFarClickedState.gif)

#### <a name="getting-clicked-state-events&quot;></a>Recupero di eventi di stato su cui è stato fatto clic

Tipo di configurazione dell'evento per lo stato selezionato: `ClickedEvents`

```c#
ClickedEvents clickedEvent = interactiveElement.GetStateEvents<ClickedEvents>(&quot;Clicked");

clickedEvent.OnClicked.AddListener(() =>
{
    Debug.Log($"{gameObject.name} Clicked");
});
```

### <a name="toggle-on-and-toggle-off-state"></a>Attivare e disattivare lo stato

Gli stati Attiva/Disattiva e Disattiva sono una coppia ed entrambi devono essere presenti per il comportamento di attivazione/disattivazione.  Per impostazione predefinita, gli stati Attiva/Disattiva e Disattiva vengono attivati tramite un clic di interazione lontano (Seleziona stato lontano).  Per impostazione predefinita, lo stato Toggle Off è attivo all'avvio, vale a dire che l'interruttore verrà inizializzato su off.  Se un utente vuole che lo stato Attiva/Disattiva sia attivo all'avvio, nello stato Attiva/Disattiva impostare `IsSelectedOnStart` su true.

**Comportamento dello stato ToggleOn e** 
 ![ Toggle Off Attivare e disattivare le interazioni con la mano virtuale](../images/interactive-element/InEditor/Gifs/ToggleOnToggleOffStateEditor.gif)

**ToggleOn e Toggle Off State Inspector** 
 ![ Attivare/disattivare il componente nel controllo](../images/interactive-element/InEditor/ToggleOnToggleOffStateInspector.png)

**Esempio di stati near e far toggle**  
Analogamente allo stato Clicked, l'impostazione toggle state può avere più punti di ingresso usando il `interactiveElement.SetToggleStates()` metodo . Ad esempio, se un utente vuole che il tocco sia un punto di ingresso aggiuntivo per impostare gli stati di attivazione/disattivazione, aggiunge il metodo a uno degli eventi `SetToggleStates()` nello stato Tocco. 

![Interruttore vicino e lontano con le interazioni con la mano virtuale](../images/interactive-element/InEditor/Gifs/NearFarToggleStates.gif)

#### <a name="getting-toggle-on-and-toggle-off-state-events&quot;></a>Attivazione e disattivazione degli eventi di stato

Tipo di configurazione dell'evento per lo stato ToggleOn: `ToggleOnEvents`  
Tipo di configurazione dell'evento per lo stato ToggleOff: `ToggleOffEvents`

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

### <a name="speech-keyword-state"></a>Stato parola chiave voce

Lo stato Parola chiave voce è in ascolto delle parole chiave definite nel profilo voce di realtà mista. Qualsiasi nuova parola chiave DEVE essere registrata nel profilo del comando vocale prima del runtime (procedura seguente). 

**Comportamento dello stato delle parole chiave vocali** 
 ![ Parola chiave voce con interazione virtuale](../images/interactive-element/InEditor/Gifs/SpeechKeywordStateEditor.gif)

**Controllo stato parola chiave voce** 
 ![ Componente parola chiave Voce in Inspector](../images/interactive-element/InEditor/SpeechKeywordStateInspector.png)

> [!NOTE]
> Lo stato della parola chiave voce è stato attivato nell'editor premendo F5 nella gif precedente. La configurazione nel test dell'editor per il riconoscimento vocale è descritta nei passaggi seguenti. 

#### <a name="how-to-register-a-speech-commandkeyword"></a>Come registrare un comando vocale/parola chiave

1. Selezionare **l'oggetto gioco MixedRealityToolkit**

1. Selezionare **Copia e personalizza** il profilo corrente

1. Passare alla sezione Input e selezionare **Clona** per abilitare la modifica del profilo di input

1. Scorrere verso il basso fino alla sezione Voce nel profilo di input e clonare il profilo voce

    ![Profilo delle parole chiave vocali nell'oggetto gioco MRTK](../images/interactive-element/InEditor/SpeechKeywordProfileClone.png) 

1. Selezionare Aggiungi un nuovo comando vocale

    ![Aggiunta di una nuova parola chiave vocale nel profilo MRTK](../images/interactive-element/InEditor/SpeechKeywordProfileAddKeyword.png) 

1. Immettere la nuova parola chiave. Facoltativo: modificare KeyCode in F5 (o un altro KeyCode) per consentire il test nell'editor. 

    ![Configurazione della parola chiave speech nel profilo MRTK](../images/interactive-element/InEditor/SpeechKeywordProfileAddKeywordName.png) 

1. Tornare al controllo di stato Interactive Element Speech Keyword (Parola chiave voce elemento interattivo) e selezionare **Add Keyword (Aggiungi parola chiave)** 

    ![Aggiunta di una parola chiave al componente dell'elemento interattivo](../images/interactive-element/InEditor/SpeechKeywordAddKeyword.png) 

    ![Convalida e registrazione delle parole chiave](../images/interactive-element/InEditor/SpeechKeywordAddKeywordBlank.png) 

1. Immettere la nuova parola chiave appena registrata nel profilo voce

    ![Immissione di una nuova parola chiave vocale](../images/interactive-element/InEditor/SpeechKeywordEnterKeyword.png) 


Per testare lo stato parola chiave voce nell'editor, premere keyCode definito nel passaggio 6 (F5) per simulare l'evento riconoscimento della parola chiave vocale.

#### <a name="getting-speech-keyword-state-events&quot;></a>Recupero di eventi relativi allo stato delle parole chiave vocali

Tipo di configurazione dell'evento per SpeechKeyword State: `SpeechKeywordEvents`

```c#
SpeechKeywordEvents speechKeywordEvents = interactiveElement.GetStateEvents<SpeechKeywordEvents>(&quot;SpeechKeyword");

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

## <a name="custom-states"></a>Stati personalizzati

### <a name="how-to-create-a-custom-state-via-inspector"></a>Come creare uno stato personalizzato tramite Inspector 

Lo stato personalizzato creato tramite il controllo verrà inizializzato con la configurazione dell'evento di stato predefinita. La configurazione dell'evento predefinita per uno stato personalizzato è di tipo `StateEvents` e contiene gli eventi OnStateOn e OnStateOff.

1. Passare a **Crea stato personalizzato nel** controllo per elemento interattivo.
    
    ![Creazione di uno stato personalizzato](../images/interactive-element/InEditor/InteractiveElementCreateCustomState.png)

1. Immettere il nome del nuovo stato. Questo nome deve essere univoco e non può essere uguale agli stati di base esistenti. 
    
    ![Immissione del nome di un nuovo stato personalizzato](../images/interactive-element/InEditor/InteractiveElementCreateCustomStateName.png)

1. Selezionare **Imposta nome stato da** aggiungere all'elenco degli stati.
    
    ![Aggiungere uno stato personalizzato all'elenco di stati](../images/interactive-element/InEditor/InteractiveElementCreateCustomStateNameSet.png)

   Questo stato personalizzato viene inizializzato con la configurazione `StateEvents` dell'evento predefinita che contiene gli `OnStateOn` eventi `OnStateOff` e . Per creare una configurazione di evento personalizzata per un nuovo stato, vedere: [Creazione di uno stato personalizzato con una configurazione di eventi personalizzati.](#creating-a-custom-state-with-a-custom-event-configuration)
    
    ![Nuovo stato visualizzato nel componente dell'elemento interattivo](../images/interactive-element/InEditor/InteractiveElementCreateCustomStateEventConfig.png)


### <a name="how-to-create-a-custom-state-via-script&quot;></a>Come creare uno stato personalizzato tramite script

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

### <a name="creating-a-custom-state-with-a-custom-event-configuration"></a>Creazione di uno stato personalizzato con una configurazione di eventi personalizzati 

I file di esempio per uno stato personalizzato denominato **Keyboard** sono disponibili qui: MRTK\SDK\Experimental\InteractiveElement\Examples\Scripts\CustomStateExample

La procedura seguente illustra un esempio esistente di creazione di file di configurazione e ricevitore di eventi di stato personalizzati.

1. Si pensi a un nome di stato.  Questo nome deve essere univoco e non può corrispondere agli stati principali esistenti. Ai fini di questo esempio, il nome dello stato sarà **Tastiera**.

1. Creare due file con estensione cs denominati state name + "Receiver" e state name + "Events". La denominazione di questi file viene presa in considerazione internamente e deve seguire la convenzione nome stato + evento/ricevitore. 

    ![Script di stato della tastiera](../images/interactive-element/InEditor/KeyboardStateFiles.png)

1. Per altri dettagli sul contenuto dei file, vedere i file KeyboardEvents.cs e KeyboardReceiver.cs. Le nuove classi di configurazione degli eventi devono ereditare da e le nuove classi del ricevitore `BaseInteractionEventConfiguration` di eventi devono ereditare da `BaseEventReceiver` .  Esempi di impostazione dello stato per lo stato della tastiera si trovano nel `CustomStateSettingExample.cs` file . 

1. Aggiungere lo stato all'elemento interattivo usando il nome dello stato. Il nome dello stato verrà riconosciuto se sono presenti file di configurazione dell'evento e del ricevitore di eventi.  Le proprietà nel file di configurazione dell'evento personalizzato dovrebbero essere visualizzate nel controllo.

    ![Aggiunta di uno stato personalizzato all'elemento interattivo ](../images/interactive-element/InEditor/AddKeyboardState.png) ![ Stato personalizzato riconosciuto nell'elemento interattivo](../images/interactive-element/InEditor/SetKeyboardStateName.png)


1. Per altri esempi di file di configurazione e ricevitore di eventi, vedere i file nei percorsi seguenti:    
- MRTK\SDK\Experimental\InteractiveElement\InteractiveElement\Events\EventConfigurations
- MRTK\SDK\Experimental\InteractiveElement\InteractiveElement\Events\EventReceivers

## <a name="example-scene"></a>Scena di esempio 

La scena di esempio per Interactive Element + State Visualizer si trova qui: MRTK\SDK\Experimental\InteractiveElement\Examples\InteractiveElementExampleScene.unity

![Scena di esempio con elemento interattivo e visualizzatore di stato](../images/interactive-element/InEditor/ExampleScene.png)

### <a name="compressable-button"></a>Pulsante comprimibile

La scena di esempio contiene prefab denominati e , che rispecchiano il comportamento dei pulsanti, costruiti usando l'elemento interattivo e `CompressableButton` `CompressableButtonToggle` il `PressableButtonHoloLens2` visualizzatore di stato. Il `CompressableButton` componente è attualmente una combinazione di con come classe di `PressableButton`  +  `PressableButtonHoloLens2` `BaseInteractiveElement` base. 

## <a name="state-visualizer-experimental"></a>Visualizzatore di stato [Sperimentale]

Il componente Visualizzatore stato aggiunge animazioni a un oggetto in base agli stati definiti in un componente elemento interattivo collegato. Questo componente crea asset di animazione, li inserisce nella cartella MixedRealityToolkit.Generated e abilita l'impostazione semplificata dei fotogrammi chiave di animazione tramite l'aggiunta di proprietà animabili a un oggetto gioco di destinazione. Per abilitare le transizioni di animazione tra gli stati, viene creato un asset di Animator Controller e viene generata una macchina a stati predefinita con i parametri associati ed eventuali transizioni di stato.  La macchina a stati può essere visualizzata nella finestra animatore di Unity.

### <a name="state-visualizer-and-unity-animation-system"></a>Visualizzatore di stato e sistema di animazione Unity

Il visualizzatore di stato sfrutta attualmente il sistema di animazione Unity. 

Quando  si preme il pulsante Genera nuove clip di animazione nel visualizzatore di stato, vengono generati nuovi asset di clip di animazione in base ai nomi di stato nell'elemento interattivo e inseriti nella cartella MixedRealityToolkit.Generated. La proprietà Clip animazione in ogni contenitore di stato è impostata sul clip di animazione associato.

![Clip di animazione nel componente visualizzatore di stato](../images/interactive-element/StateVisualizer/AnimationClips.png)

Viene generata anche una macchina a stati di [Animator](https://docs.unity3d.com/Manual/AnimationOverview.html) per gestire le transizioni uniformi tra le clip di animazione.  Per impostazione predefinita, la macchina a stati usa [Qualsiasi stato](https://docs.unity3d.com/Manual/class-State.html) per consentire le transizioni tra qualsiasi stato nell'elemento interattivo. 

[I visualizzatori di stato attivati nell'animatore](https://docs.unity3d.com/Manual/AnimationParameters.html) vengono generati anche per ogni stato. I parametri del trigger vengono usati nel visualizzatore di stato per attivare un'animazione.

![Macchina a stati Unity](../images/interactive-element/StateVisualizer/UnityStateMachine.png)

### <a name="runtime-limitations"></a>Limitazioni di runtime 

Il visualizzatore di stato deve essere aggiunto a un oggetto tramite il controllo e non può essere aggiunto tramite script.  Le proprietà che modificano AnimatorStateMachine/AnimationController sono contenute in uno spazio dei nomi dell'editor ( ) che vengono rimosse `UnityEditor.Animations` quando viene compilata l'app.

## <a name="how-to-use-the-state-visualizer"></a>Come usare il visualizzatore di stato

1. Creare un cubo
1. Associare un elemento interattivo
1. Attach State Visualizer
1. Selezionare Generate **New Animation Clips (Genera nuove clip di animazione)**

    ![Generazione di nuove clip di animazione](../images/interactive-element/StateVisualizer/GenerateAnimationClips.png)

    ![Visualizzazione delle clip di animazione generate nei componenti del visualizzatore e degli elementi interattivi](../images/interactive-element/StateVisualizer/GenerateAnimationClips2.png)

1. Nel contenitore Stato attivo selezionare **Aggiungi destinazione**

    ![Aggiunta della destinazione del visualizzatore di stato](../images/interactive-element/StateVisualizer/AddTarget.png)

1. Trascinare l'oggetto gioco corrente nel campo di destinazione 

    ![Impostazione della destinazione del visualizzatore di stato](../images/interactive-element/StateVisualizer/SetTarget.png)

1. Aprire il riquadro proprietà animabili del cubo
1. Selezionare il menu a discesa delle proprietà Animabile e selezionare **Colore**

    ![Impostazione del colore del visualizzatore di stato](../images/interactive-element/StateVisualizer/SetColor.png)

1. Selezionare **Add the Color Animatable Property (Aggiungi proprietà animabile color)**

    ![Selezione della proprietà animabile color color animatable del visualizzatore](../images/interactive-element/StateVisualizer/SetColorProperty.png)

1. Scegliere un colore 

    ![Scelta di un colore del visualizzatore dalla ruota dei colori](../images/interactive-element/StateVisualizer/SetBlueColor.png)

1. Premere play e osservare il cambio di colore di transizione

    ![Esempio di modifica del colore di transizione con l'interazione con la mano virtuale](../images/interactive-element/InEditor/Gifs/FocusColorChange.gif)

## <a name="animatable-properties"></a>Proprietà animabili

Lo scopo principale di Proprietà animabili è semplificare l'impostazione del fotogramma chiave della clip di animazione.  Se un utente ha familiarità con Unity Animation System e preferisce impostare direttamente i fotogrammi chiave nelle clip di animazione generate, non può semplicemente aggiungere proprietà animabili a un oggetto di destinazione e aprire il clip nella finestra Animazione di Unity (Animazione di Windows > > Animation). 

Se si usano le proprietà animabili per l'animazione, il tipo di curva viene impostato su EaseInOut.

**Proprietà animabili correnti:**
- [Offset della scala](#scale-offset)
- [Offset della posizione](#position-offset)
- [Colore](#color)
- [Colore shader](#shader-color)
- [Shader Float](#shader-float)
- [Vettore shader](#shader-vector)

### <a name="scale-offset"></a>Offset della scala

La proprietà Scale Offset Animatable accetta la scala corrente dell'oggetto e aggiunge l'offset definito.

![Offset della scala con l'interazione con la mano virtuale](../images/interactive-element/InEditor/Gifs/ScaleOffset.gif)

### <a name="position-offset"></a>Offset della posizione

La proprietà Position Offset Animatable accetta la posizione corrente dell'oggetto e aggiunge l'offset definito.

![Offset della posizione con l'interazione con la mano virtuale](../images/interactive-element/InEditor/Gifs/PositionOffset.gif)

### <a name="color"></a>Color

La proprietà Color Animatable rappresenta il colore principale di un materiale se il materiale ha una proprietà di colore principale. Questa proprietà aggiunge un'animazione alla `material._Color` proprietà .

![Modifica del colore dello stato attivo con l'interazione con la mano virtuale](../images/interactive-element/InEditor/Gifs/FocusColorChange.gif)

### <a name="shader-color"></a>Colore shader

La proprietà Shader Color Animatable fa riferimento a una proprietà shader di tipo color. Un nome di proprietà è obbligatorio per tutte le proprietà dello shader. La gif seguente illustra l'animazione di una proprietà di colore shader Fill_Color che non è il colore principale del materiale.  Osservare i valori che cambiano nel controllo materiali.

![Colore ombreggiatura con interazione con la mano virtuale](../images/interactive-element/InEditor/Gifs/ShaderColor.gif)

### <a name="shader-float"></a>Shader Float

La proprietà Shader Float Animatable fa riferimento a una proprietà shader di tipo float. Un nome di proprietà è obbligatorio per tutte le proprietà dello shader. Nella gif seguente osservare i valori che cambiano nel controllo materiale per la proprietà Metallic. 

![Float shader con interazione con la mano virtuale](../images/interactive-element/InEditor/Gifs/ShaderFloat.gif)

### <a name="shader-vector"></a>Vettore shader

La proprietà Animatable del vettore shader fa riferimento a una proprietà shader di tipo Vector4. Un nome di proprietà è obbligatorio per tutte le proprietà dello shader. Nella gif seguente osservare i valori che cambiano nel controllo materiale per la proprietà Tiling (Main Tex_ST). 

![Vettore shader con interazione con la mano virtuale](../images/interactive-element/InEditor/Gifs/ShaderVector.gif)


### <a name="how-to-find-animatable-shader-property-names"></a>Come trovare i nomi delle proprietà shader animabili

1. Passare all'animazione > finestra > animazione
1. Assicurarsi che l'oggetto con il visualizzatore di stato sia selezionato nella gerarchia
1. Selezionare un clip di animazione nella finestra Animazione
1. Selezionare **Aggiungi proprietà,** aprire il foldout renderer mesh 

    ![Aggiunta della proprietà di animazione nella finestra Animator](../images/interactive-element/StateVisualizer/AnimationWindow.png)

1. Questo elenco contiene i nomi di tutti i nomi delle proprietà animabili 

    ![Proprietà di animazione del renderer mesh nella finestra animatore](../images/interactive-element/StateVisualizer/MeshRendererProperties.png)

## <a name="see-also"></a>Vedi anche

- [**Pulsanti**](../ux-building-blocks/button.md)
- [**Controllo Bounds**](../ux-building-blocks/bounds-control.md)
- [**Raccolta di oggetti Grid**](../ux-building-blocks/object-collection.md)
- [**Risolutore RadialView**](../ux-building-blocks/solvers/solver.md)

---
title: Interactiveelement
description: Documentazione di interactiveelement MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 02/22/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, elemento interattivo, interactable
ms.openlocfilehash: 7c3bc6810a6ac5b556384b2ab97bb3ecda783760
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2021
ms.locfileid: "104694538"
---
# <a name="interactive-element-experimental"></a>Interactive (elemento) [sperimentale]

Un punto di ingresso centralizzato semplificato al sistema di input MRTK. Contiene i metodi di gestione dello stato, la gestione degli eventi e la logica di impostazione dello stato per gli Stati di interazione principali.

L'elemento interattivo è una funzionalità sperimentale supportata in Unity 2019,3 e, in quanto usa una funzionalità nuova per Unity 2019,3: [Serialize Reference](https://docs.unity3d.com/ScriptReference/SerializeReference.html).

### <a name="interactive-element-inspector"></a>Controllo elemento interattivo

In modalità di riproduzione, il controllo dell'elemento interattivo fornisce un feedback visivo che indica se lo stato corrente è attivo o meno. Se uno stato è attivo, verrà evidenziato con un colore ciano.  Se lo stato non è attivo, il colore non viene modificato. I numeri accanto agli Stati del controllo sono i valori di stato, se lo stato è attivo, il valore è 1, se lo stato non è attivo, il valore è 0.

![Elemento interattivo con interazione con la mano virtuale](../images/interactive-element/InEditor/Gifs/InspectorHighlightEditor.gif)

## <a name="core-states"></a>Stati principali

L'elemento interattivo contiene gli Stati di base e supporta l'aggiunta di [stati personalizzati](#custom-states).  Uno stato principale è quello in cui è già presente la logica di impostazione dello stato definita in `BaseInteractiveElement` . Di seguito è riportato un elenco degli stati principali di core basati su input: 

### <a name="current-core-states"></a>Stati Core correnti

- [Default](#default-state) 

Stati di core per l'interazione near and lontano:
- [Lo stato attivo](#focus-state) 

Stati principali di interazione near:

- [Stato attivo vicino](#focus-near-state)
- [Tocco](#touch-state)

Stati principali per l'interazione tra i componenti:
- [Stato attivo](#focus-far-state)
- [Seleziona a lungo](#select-far-state)

Altri stati principali:
- [Clicked](#clicked-state)
- [Attivare e disattivare](#toggle-on-and-toggle-off-state)
- [Parola chiave Speech](#speech-keyword-state)

### <a name="how-to-add-a-core-state-via-inspector"></a>Come aggiungere uno stato principale tramite Inspector

1. Passare a **Aggiungi stato principale** nell'elemento Inspector per Interactive.

    ![Aggiungere uno stato principale tramite Inspector](../images/interactive-element/InEditor/InteractiveElementAddCoreState.png)


1. Selezionare il pulsante **Seleziona stato** per scegliere lo stato principale da aggiungere. Gli Stati nel menu sono ordinati in base al tipo di interazione.

    ![Aggiungere uno stato principale tramite Inspector con stato selezionato](../images/interactive-element/InEditor/InteractiveElementAddCoreStateSelectState.png)

1. Aprire la finestra di dialogo di configurazione dell'evento per visualizzare gli eventi e le proprietà associati allo stato.

    ![Aggiungere uno stato principale tramite Inspector con la configurazione dell'evento](../images/interactive-element/InEditor/InteractiveElementAddCoreStateSelectStateEventConfig.png)


### <a name="how-to-add-a-core-state-via-script"></a>Come aggiungere uno stato principale tramite script

Usare il `AddNewState(stateName)` metodo per aggiungere uno stato principale. Per un elenco dei nomi di stato principali disponibili, usare l' `CoreInteractionState` enumerazione.

```c#
// Add by name or add by CoreInteractionState enum to string

interactiveElement.AddNewState("SelectFar");

interactiveElement.AddNewState(CoreInteractionState.SelectFar.ToString());
```

### <a name="states-internal-structure"></a>Struttura interna degli Stati 

Gli Stati nell'elemento interattivo sono di tipo `InteractionState` .  Un oggetto `InteractionState` contiene le proprietà seguenti:

- **Nome**: nome dello stato.
- **Value**: valore di stato.  Se lo stato è on, il valore dello stato è 1. Se lo stato è disattivato, il valore di stato è 0.
- **Attivo**: indica se lo stato è attualmente attivo o meno. Il valore della proprietà attiva è true quando lo stato è on, false se lo stato è off. 
- **Tipo** di interazione: il tipo di interazione di uno stato è il tipo di interazione a cui è destinato uno stato. 
  - `None`: Non supporta alcuna forma di interazione di input.
  - `Near`: Supporto per l'interazione near. L'input viene considerato vicino all'interazione quando una mano articolata ha un contatto diretto con un altro oggetto gioco, ovvero la posizione in cui la mano articolata è vicina alla posizione dell'oggetto gioco nello spazio globale.
  - `Far`: Supporto per l'interazione. L'input è considerato un'interazione molto quando non è necessario un contatto diretto con l'oggetto gioco. Ad esempio, l'input tramite raggio controller o sguardo è considerato un input di interazione molto lungo.
  - `NearAndFar`: Include sia il supporto per l'interazione vicino che l'altro. 
  - `Other`: Supporto dell'interazione indipendente del puntatore.
- **Configurazione evento**: la configurazione dell'evento per uno stato è il punto di ingresso del profilo degli eventi serializzati. 

Tutte queste proprietà vengono impostate internamente nell' `State Manager` elemento contenuto in interattivo. Per la modifica degli Stati, usare i metodi helper seguenti:

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

Il recupero della configurazione dell'evento di uno stato è specifico per lo stato stesso. Ogni stato principale ha un tipo di configurazione di evento specifico, illustrato di seguito sotto le sezioni che descrivono ogni stato principale.

Di seguito è riportato un esempio generalizzato di recupero della configurazione di un evento di stato:

```c#
// T varies depending on the core state - the specific T's are specified under each of the core state sections
T stateNameEvents = interactiveElement.GetStateEvents<T>("StateName");
```

### <a name="default-state"></a>Stato predefinito

Lo stato predefinito è sempre presente in un elemento interattivo.  Questo stato sarà attivo solo quando tutti gli altri Stati non sono attivi.  Se un altro stato diventa attivo, lo stato predefinito verrà impostato su off internamente. 

Un elemento interattivo viene inizializzato con gli Stati di attivazione e predefiniti presenti nell'elenco degli Stati. Lo stato predefinito deve sempre essere presente nell'elenco degli Stati. 

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

Lo stato attivo è uno stato di interazione vicino e lontano che può essere considerato come la realtà mista equivalente al passaggio del mouse. Il fattore di distinzione tra l'interazione quasi e la distanza per lo stato attivo è il tipo di puntatore attivo corrente.  Se il tipo di puntatore per lo stato attivo è il puntatore poke, l'interazione viene considerata quasi interazione.  Se il puntatore primario non è il puntatore poke, l'interazione è considerata un'interazione di gran lunga. Per impostazione predefinita, lo stato attivo è presente nell'elemento interattivo.

 
 Comportamento ![ dello stato attivo Stato attivo con interazione della mano virtuale](../images/interactive-element/InEditor/Gifs/FocusStateEditor.gif) 

Controllo stato di **messa a fuoco** 
 ![ Stato attivo in Inpsector](../images/interactive-element/InEditor/FocusStateInspector.png)

#### <a name="getting-focus-state-events"></a>Recupero degli eventi dello stato attivo

Tipo di configurazione evento per lo stato attivo: `FocusEvents`

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

#### <a name="focus-near-vs-focus-far-behavior"></a>Concentrati sul comportamento estremo rispetto a Visual Studio 

![Concentrati sull'interazione con la mano virtuale](../images/interactive-element/InEditor/Gifs/FocusNearFocusFar.gif)

### <a name="focus-near-state"></a>Stato attivo vicino allo stato

Lo stato attivo near viene impostato quando viene generato un evento di messa a fuoco e il puntatore principale è il puntatore poke, un'indicazione di near Interaction. 

**Stato attivo vicino al comportamento** 
 ![ dello stato Stato attivo vicino allo stato con interazione con la mano virtuale](../images/interactive-element/InEditor/Gifs/FocusNearStateEditor.gif) 

**Stato attivo vicino a controllo stato** 
 ![ Concentrare l'attenzione sul componente nel controllo](../images/interactive-element/InEditor/FocusNearStateInspector.png)

#### <a name="getting-focusnear-state-events"></a>Recupero degli eventi di stato FocusNear

Tipo di configurazione dell'evento per lo stato FocusNear: `FocusEvents`

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

### <a name="focus-far-state"></a>Stato di disattivazione

Lo stato di disattivazione dello stato attivo viene impostato quando il puntatore primario non è il puntatore poke.  Ad esempio, il puntatore del raggio del controller predefinito e il puntatore GGV (sguardo, movimento, voce) sono considerati puntatori di interazione.

Comportamento dello stato di **disattivazione** 
 ![ Stato di messa a fuoco per l'interazione con la mano virtuale](../images/interactive-element/InEditor/Gifs/FocusFarStateEditor.gif)

Controllo dello stato **attivo per lo stato** 
 ![ Concentrare l'attenzione sul componente nell'Ispettore](../images/interactive-element/InEditor/FocusFarStateInspector.png)

#### <a name="getting-focus-far-state-events"></a>Recupero degli eventi di stato attivo

Tipo di configurazione dell'evento per lo stato FocusFar: `FocusEvents`

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

### <a name="touch-state"></a>Stato tocco

Lo stato del tocco è uno stato near Interaction impostato quando una mano articolata tocca direttamente l'oggetto.  Un tocco diretto significa che il dito dell'indice della mano articolata è molto vicino alla posizione globale dell'oggetto. Per impostazione predefinita, un `NearInteractionTouchableVolume` componente viene associato all'oggetto se lo stato tocco viene aggiunto all'elenco degli Stati.  La presenza di un  `NearInteractionTouchableVolume` `NearInteractionTouchable` componente o è necessaria per rilevare gli eventi di tocco.  La differenza tra `NearInteractionTouchableVolume` e `NearInteractionTouchable` è che `NearInteractionTouchableVolume` rileva un tocco basato sul Collider dell'oggetto e `NearInteractionTouchable` rileva il tocco in un'area definita di un piano.

Comportamento dello stato di **tocco** 
 ![ Stato di tocco con interazione della mano virtuale](../images/interactive-element/InEditor/Gifs/TouchStateEditor.gif)

Controllo dello stato di **tocco** 
 ![ Componente stato tocco nel controllo](../images/interactive-element/InEditor/TouchStateInspector.png)

#### <a name="getting-touch-state-events"></a>Recupero degli eventi di stato tocco

Tipo di configurazione dell'evento per lo stato di tocco: `TouchEvents`

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

### <a name="select-far-state"></a>Selezione stato lontano

Lo stato di selezione della distanza è la `IMixedRealityPointerHandler` superficie.  Questo stato è uno stato di interazione molto lungo che rileva il clic di interazione di tipo esponente (TAP) ed è in grado di usare puntatori di interazione di gran lunga come il puntatore del raggio del controller predefinito o il puntatore GGV.  Per lo stato Select-out è presente un'opzione nell'applicazione di chiusura della configurazione dell'evento denominata `Global` . Se `Global` è true, l'oggetto `IMixedRealityPointerHandler` viene registrato come gestore di input globale.  Lo stato attivo su un oggetto non è necessario per attivare gli eventi di sistema di input se un gestore viene registrato come globale.  Se, ad esempio, un utente desidera conoscere ogni volta che viene eseguito il movimento di tocco/selezione dell'aria indipendentemente dall'oggetto nello stato attivo, impostare `Global` su true. 

**Selezionare il comportamento** 
 ![ dello stato di distanti Seleziona molto con interazione della mano virtuale](../images/interactive-element/InEditor/Gifs/SelectFarStateEditor.gif)

**Selezionare il controllo** 
 ![ di stato lontano Selezionare un componente lontano nel controllo](../images/interactive-element/InEditor/SelectFarStateInspector.png)

#### <a name="getting-select-far-state-events"></a>Recupero degli eventi di selezione dello stato

Tipo di configurazione dell'evento per lo stato SelectFar: `SelectFarEvents`

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

### <a name="clicked-state"></a>Stato selezionato

Per impostazione predefinita, lo stato selezionato viene attivato da un clic per l'interazione con la distanza (selezione dello stato).  Questo stato viene attivato internamente, richiama l'evento OnClicked e quindi viene immediatamente disattivato. 

> [!NOTE]
> Il feedback visivo nel controllo basato sull'attività di stato non è presente per lo stato selezionato perché è attivato e quindi disattivato immediatamente. 

 
 Comportamento ![ stato selezionato Stato selezionato con interazioni con la mano virtuale](../images/interactive-element/InEditor/Gifs/ClickedStateEditor.gif)

 
 Controllo ![ stato selezionato Fare clic su componente stato nel controllo](../images/interactive-element/InEditor/ClickedStateInspector.png)

**Esempio di stato vicino e molto selezionato**  
Lo stato selezionato può essere attivato tramite punti di ingresso aggiuntivi tramite il `interactiveElement.TriggerClickedState()` metodo.  Ad esempio, se un utente vuole un tocco near Interaction per attivare un clic su un oggetto, aggiunge il `TriggerClickedState()` metodo come listener nello stato touch.   

![Stato near and distanti con interazioni con la mano virtuale](../images/interactive-element/InEditor/Gifs/NearFarClickedState.gif)

#### <a name="getting-clicked-state-events"></a>Recupero degli eventi di stato selezionato

Tipo di configurazione evento per lo stato selezionato: `ClickedEvents`

```c#
ClickedEvents clickedEvent = interactiveElement.GetStateEvents<ClickedEvents>("Clicked");

clickedEvent.OnClicked.AddListener(() =>
{
    Debug.Log($"{gameObject.name} Clicked");
});
```

### <a name="toggle-on-and-toggle-off-state"></a>Attivare e disattivare lo stato

Gli Stati di attivazione e disattivazione sono una coppia ed è necessario che entrambi siano presenti per il comportamento di attivazione/disattivazione.  Per impostazione predefinita, gli Stati di attivazione e disattivazione e disattivazione vengono attivati tramite un clic di interazione con la distanza (selezione dello stato lontano).  Per impostazione predefinita, lo stato di attivazione/disattivazione è attivo all'inizio, ovvero l'interruttore verrà inizializzato su disattivato.  Se un utente desidera che lo stato di attivazione/disattivazione sia attivo all'avvio, quindi nello stato di attivazione/disattivazione impostato su `IsSelectedOnStart` true.

**ToggleOn e disattivare il comportamento** 
 ![ dello stato Attivare e disattivare le interazioni con la mano virtuale](../images/interactive-element/InEditor/Gifs/ToggleOnToggleOffStateEditor.gif)

**ToggleOn e Disattiva controllo stato** 
 ![ Imposta/Nascondi componente nel controllo](../images/interactive-element/InEditor/ToggleOnToggleOffStateInspector.png)

**Esempio per gli Stati di attivazione o distanti**  
Analogamente allo stato selezionato, l'impostazione dello stato di attivazione/disinstallazione può avere più punti di ingresso usando il `interactiveElement.SetToggleStates()` metodo. Se, ad esempio, un utente desidera toccare come punto di ingresso aggiuntivo per impostare gli Stati di attivazione, aggiunge il `SetToggleStates()` metodo a uno degli eventi nello stato di tocco. 

![Passare da un elemento a un altro e viceversa con interazioni con la mano virtuale](../images/interactive-element/InEditor/Gifs/NearFarToggleStates.gif)

#### <a name="getting-toggle-on-and-toggle-off-state-events"></a>Ottenere l'interruttore e disattivare gli eventi di stato

Tipo di configurazione dell'evento per lo stato ToggleOn: `ToggleOnEvents`  
Tipo di configurazione dell'evento per lo stato ToggleOff: `ToggleOffEvents`

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

### <a name="speech-keyword-state"></a>Stato parola chiave vocale

Lo stato della parola chiave vocale è in ascolto per le parole chiave definite nel profilo di sintesi vocale della realtà mista. Qualsiasi nuova parola chiave deve essere registrata nel profilo del comando vocale prima del runtime (passaggi successivi). 

Comportamento stato parola **chiave vocale** 
 ![ Parola chiave Speech con interazione virtuale](../images/interactive-element/InEditor/Gifs/SpeechKeywordStateEditor.gif)

Controllo stato parola **chiave vocale** 
 ![ Componente parola chiave vocale nel controllo](../images/interactive-element/InEditor/SpeechKeywordStateInspector.png)

> [!NOTE]
> Lo stato della parola chiave vocale è stato attivato nell'Editor premendo il tasto F5 nel gif precedente. La configurazione nel test dell'editor per la sintesi vocale è illustrata nella procedura seguente. 

#### <a name="how-to-register-a-speech-commandkeyword"></a>Come registrare un comando/parola chiave vocale

1. Selezionare l'oggetto gioco **MixedRealityToolkit**

1. Selezionare **copia e Personalizza** il profilo corrente

1. Passare alla sezione input e selezionare **clona** per abilitare la modifica del profilo di input.

1. Scorrere verso il basso fino alla sezione voce del profilo di input e clonare il profilo vocale

    ![Profilo parola chiave vocale nell'oggetto gioco MRTK](../images/interactive-element/InEditor/SpeechKeywordProfileClone.png) 

1. Selezionare Aggiungi un nuovo comando vocale

    ![Aggiunta di una nuova parola chiave vocale nel profilo MRTK](../images/interactive-element/InEditor/SpeechKeywordProfileAddKeyword.png) 

1. Immettere la parola chiave New. Facoltativo: modificare il codice in F5 (o un altro codice) per consentire il test nell'editor. 

    ![Configurazione della parola chiave Speech nel profilo MRTK](../images/interactive-element/InEditor/SpeechKeywordProfileAddKeywordName.png) 

1. Tornare alla finestra di dialogo di controllo dello stato delle parole chiave vocale degli elementi interattivi e selezionare **Aggiungi parola chiave** 

    ![Aggiunta della parola chiave al componente elemento interattivo](../images/interactive-element/InEditor/SpeechKeywordAddKeyword.png) 

    ![Convalida e registrazione delle parole chiave](../images/interactive-element/InEditor/SpeechKeywordAddKeywordBlank.png) 

1. Immettere la nuova parola chiave appena registrata nel profilo vocale

    ![Immissione di una nuova parola chiave vocale](../images/interactive-element/InEditor/SpeechKeywordEnterKeyword.png) 


Per testare lo stato della parola chiave Speech nell'editor, premere il KeyCode definito nel passaggio 6 (F5) per simulare l'evento riconoscimento parola chiave vocale.

#### <a name="getting-speech-keyword-state-events"></a>Recupero degli eventi di stato della parola chiave vocale

Tipo di configurazione dell'evento per lo stato SpeechKeyword: `SpeechKeywordEvents`

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

## <a name="custom-states"></a>Stati personalizzati

### <a name="how-to-create-a-custom-state-via-inspector"></a>Come creare uno stato personalizzato tramite Inspector 

Lo stato personalizzato creato tramite Inspector verrà inizializzato con la configurazione dell'evento di stato predefinito. La configurazione dell'evento predefinito per uno stato personalizzato è di tipo `StateEvents` e contiene gli eventi OnStateOn e OnStateOff.

1. Passare a **Crea stato personalizzato** nell'elemento Inspector per l'elemento interattivo.
    
    ![Creazione di uno stato personalizzato](../images/interactive-element/InEditor/InteractiveElementCreateCustomState.png)

1. Immettere il nome del nuovo stato. Questo nome deve essere univoco e non può essere uguale a quello degli Stati core esistenti. 
    
    ![Immissione del nome di un nuovo stato personalizzato](../images/interactive-element/InEditor/InteractiveElementCreateCustomStateName.png)

1. Selezionare **Imposta nome stato** da aggiungere all'elenco degli Stati.
    
    ![Aggiungi stato personalizzato a elenco stato](../images/interactive-element/InEditor/InteractiveElementCreateCustomStateNameSet.png)

   Questo stato personalizzato viene inizializzato con la `StateEvents` configurazione dell'evento predefinita che contiene gli `OnStateOn` `OnStateOff` eventi e. Per creare una configurazione di evento personalizzata per un nuovo stato, vedere [creazione di uno stato personalizzato con una configurazione di evento personalizzata](#creating-a-custom-state-with-a-custom-event-configuration).
    
    ![Nuovo stato visualizzato nel componente elemento interattivo](../images/interactive-element/InEditor/InteractiveElementCreateCustomStateEventConfig.png)


### <a name="how-to-create-a-custom-state-via-script"></a>Come creare uno stato personalizzato tramite script

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

### <a name="creating-a-custom-state-with-a-custom-event-configuration"></a>Creazione di uno stato personalizzato con una configurazione di evento personalizzata 

I file di esempio per uno stato personalizzato denominato **Keyboard** sono disponibili qui: MRTK\SDK\Experimental\InteractiveElement\Examples\Scripts\CustomStateExample

I passaggi seguenti illustrano un esempio esistente di creazione di un file di configurazione e di un ricevitore di eventi di stato personalizzati.

1. Si pensi a un nome di stato.  Questo nome deve essere univoco e non può essere uguale a quello degli Stati core esistenti. Ai fini di questo esempio, il nome dello stato sarà la **tastiera**.

1. Creare due file con estensione cs con nome stato + "Receiver" e nome stato + "Events". La denominazione di questi file viene presa in considerazione internamente e deve essere conforme al nome dello stato e alla convenzione di evento/destinatario. 

    ![Script di stato della tastiera](../images/interactive-element/InEditor/KeyboardStateFiles.png)

1. Per informazioni dettagliate sui contenuti dei file, vedere i file KeyboardEvents. cs e KeyboardReceiver. cs. Le nuove classi di configurazione degli eventi devono ereditare da `BaseInteractionEventConfiguration` e le nuove classi del ricevitore di eventi devono ereditare da `BaseEventReceiver` .  Gli esempi di impostazioni di stato per lo stato della tastiera si trovano nel `CustomStateSettingExample.cs` file. 

1. Aggiungere lo stato all'elemento interattivo utilizzando il nome dello stato, il nome dello stato verrà riconosciuto se sono presenti file di configurazione eventi e ricevitore di eventi.  Le proprietà nel file di configurazione dell'evento personalizzato devono essere visualizzate nel controllo.

    ![Aggiunta dello stato personalizzato allo ](../images/interactive-element/InEditor/AddKeyboardState.png) ![ stato personalizzato dell'elemento interattivo riconosciuto nell'elemento interattivo](../images/interactive-element/InEditor/SetKeyboardStateName.png)


1. Per ulteriori esempi di file di configurazione di eventi e di ricevitore di eventi, vedere i file nei percorsi seguenti:    
- MRTK\SDK\Experimental\InteractiveElement\InteractiveElement\Events\EventConfigurations
- MRTK\SDK\Experimental\InteractiveElement\InteractiveElement\Events\EventReceivers

## <a name="example-scene"></a>Scena di esempio 

La scena di esempio per l'elemento interattivo + Visualizzatore stato si trova qui: MRTK\SDK\Experimental\InteractiveElement\Examples\InteractiveElementExampleScene.unity

![Scena di esempio con elemento interattivo e Visualizzatore stato](../images/interactive-element/InEditor/ExampleScene.png)

### <a name="compressable-button"></a>Pulsante compressive

La scena di esempio contiene prefabbricati denominati `CompressableButton` e `CompressableButtonToggle` , che rispecchiano il comportamento dei `PressableButtonHoloLens2` pulsanti, costruiti usando l'elemento interattivo e il Visualizzatore di stato. Il `CompressableButton` componente è attualmente una combinazione di `PressableButton`  +  `PressableButtonHoloLens2` con `BaseInteractiveElement` come classe di base. 

## <a name="state-visualizer-experimental"></a>Visualizzatore stato [sperimentale]

Il componente Visualizzatore stato aggiunge animazioni a un oggetto in base agli stati definiti in un componente elemento interattivo collegato. Questo componente crea asset di animazione, li inserisce nella cartella MixedRealityToolkit. generated e Abilita l'impostazione del fotogramma chiave di animazione semplificato tramite l'aggiunta di proprietà animata a un oggetto Game di destinazione. Per abilitare le transizioni di animazioni tra gli Stati, viene creato un asset del controller di animazione e viene generata una macchina a stati predefinita con i parametri associati e le transizioni di stato.  La macchina a stati può essere visualizzata nella finestra Animator di Unity.

### <a name="state-visualizer-and-unity-animation-system"></a>Visualizzatore di stato e sistema di animazione Unity

Il Visualizzatore di stato utilizza attualmente il sistema di animazione Unity. 

Quando si preme il pulsante **genera nuova animazione clip** nel Visualizzatore di stato, vengono generati nuovi asset di clip di animazione basati sui nomi degli Stati nell'elemento interattivo e inseriti nella cartella MixedRealityToolkit. generated. La proprietà clip animazione in ogni contenitore di stato è impostata sul clip di animazione associato.

![Clip di animazione nel componente Visualizzatore stato](../images/interactive-element/StateVisualizer/AnimationClips.png)

Viene inoltre generata una [macchina a stati di animazione](https://docs.unity3d.com/Manual/AnimationOverview.html) per gestire transizioni uniformi tra clip di animazione.  Per impostazione predefinita, la macchina a stati USA lo [stato any](https://docs.unity3d.com/Manual/class-State.html) per consentire le transizioni tra qualsiasi stato nell'elemento interattivo. 

I [visualizzatori di stato attivati nell'animatore](https://docs.unity3d.com/Manual/AnimationParameters.html) vengono generati anche per ogni stato, i parametri del trigger vengono usati nel Visualizzatore di stato per attivare un'animazione.

![Macchina a stati Unity](../images/interactive-element/StateVisualizer/UnityStateMachine.png)

### <a name="runtime-limitations"></a>Limitazioni di runtime 

Il Visualizzatore di stato deve essere aggiunto a un oggetto tramite il controllo e non può essere aggiunto tramite script.  Le proprietà che modificano AnimatorStateMachine/AnimationController sono contenute in uno spazio dei nomi dell'editor ( `UnityEditor.Animations` ) che viene rimosso quando viene compilata l'app.

## <a name="how-to-use-the-state-visualizer"></a>Come usare il Visualizzatore di stato

1. Creazione di un cubo
1. Connetti elemento interattivo
1. Visualizzatore stato di connessione
1. Selezionare **genera nuove clip di animazione**

    ![Generazione di nuove clip di animazione](../images/interactive-element/StateVisualizer/GenerateAnimationClips.png)

    ![Visualizzazione delle clip di animazione generate nei componenti del visualizzatore e degli elementi interattivi](../images/interactive-element/StateVisualizer/GenerateAnimationClips2.png)

1. Nel contenitore stato attivo selezionare **Aggiungi destinazione**

    ![Aggiunta della destinazione del Visualizzatore di stato](../images/interactive-element/StateVisualizer/AddTarget.png)

1. Trascinare l'oggetto Game corrente nel campo di destinazione 

    ![Impostazione della destinazione del Visualizzatore di stato](../images/interactive-element/StateVisualizer/SetTarget.png)

1. Apri l'aggiunta delle proprietà animabili del cubo
1. Selezionare il menu a discesa proprietà animata e selezionare **colore**

    ![Impostazione del colore del Visualizzatore di stato](../images/interactive-element/StateVisualizer/SetColor.png)

1. Selezionare **Aggiungi la proprietà con animazione colore**

    ![Selezione della proprietà Animatable color del Visualizzatore](../images/interactive-element/StateVisualizer/SetColorProperty.png)

1. Scegliere un colore 

    ![Scelta di un colore del visualizzatore dalla rotellina colori](../images/interactive-element/StateVisualizer/SetBlueColor.png)

1. Premere Riproduci e osservare la modifica del colore di transizione

    ![Esempio di modifica del colore di transizione con interazione della mano virtuale](../images/interactive-element/InEditor/Gifs/FocusColorChange.gif)

## <a name="animatable-properties"></a>Proprietà animata

Lo scopo principale delle proprietà animata è semplificare l'impostazione del fotogramma chiave per la clip di animazione.  Se un utente ha familiarità con il sistema di animazione Unity e preferisce impostare direttamente i fotogrammi chiave sui clip di animazione generati, non può semplicemente aggiungere proprietà animata a un oggetto di destinazione e aprire il clip nella finestra di animazione di Unity (animazione di Windows > > animazione). 

Se si usano le proprietà Animatable per Animation, il tipo di curva viene impostato su EaseInOut.

**Proprietà animabili correnti:**
- [Offset scala](#scale-offset)
- [Offset posizione](#position-offset)
- [Colore](#color)
- [Colore shader](#shader-color)
- [Float shader](#shader-float)
- [Vettore shader](#shader-vector)

### <a name="scale-offset"></a>Offset scala

La proprietà animata offset di ridimensionamento accetta la scala corrente dell'oggetto e aggiunge l'offset definito.

![Offset di scalabilità con interazione con la mano virtuale](../images/interactive-element/InEditor/Gifs/ScaleOffset.gif)

### <a name="position-offset"></a>Offset posizione

La proprietà animata offset della posizione accetta la posizione corrente dell'oggetto e aggiunge l'offset definito.

![Offset della posizione con interazione con la mano virtuale](../images/interactive-element/InEditor/Gifs/PositionOffset.gif)

### <a name="color"></a>Colore

La proprietà Color Animable rappresenta il colore principale di un materiale se il materiale ha una proprietà del colore principale. Questa proprietà aggiunge un'animazione alla `material._Color` Proprietà.

![Modifica del colore di attivazione con interazione con la mano virtuale](../images/interactive-element/InEditor/Gifs/FocusColorChange.gif)

### <a name="shader-color"></a>Colore shader

La proprietà di animazione del colore dello shader fa riferimento a una proprietà dello shader di tipo Color. È necessario specificare un nome di proprietà per tutte le proprietà dello shader. Il gif seguente illustra l'animazione di una proprietà di colore shader denominata Fill_Color che non è il colore principale del materiale.  Osservare i valori modificabili nel controllo materiali.

![Colore ombreggiatura con interazione della mano virtuale](../images/interactive-element/InEditor/Gifs/ShaderColor.gif)

### <a name="shader-float"></a>Float shader

La proprietà con animazione float shader fa riferimento a una proprietà shader di tipo float. È necessario specificare un nome di proprietà per tutte le proprietà dello shader. Nel formato gif riportato di seguito osservare i valori modificabili in Material Inspector per la proprietà metallic. 

![Float shader con interazione della mano virtuale](../images/interactive-element/InEditor/Gifs/ShaderFloat.gif)

### <a name="shader-vector"></a>Vettore shader

La proprietà Animable Vector shader fa riferimento a una proprietà shader di tipo Vector4. È necessario specificare un nome di proprietà per tutte le proprietà dello shader. Nel gif seguente osservare i valori modificabili nel controllo materiale per la proprietà di affiancamento (Main Tex_ST). 

![Vettore shader con interazione della mano virtuale](../images/interactive-element/InEditor/Gifs/ShaderVector.gif)


### <a name="how-to-find-animatable-shader-property-names"></a>Come trovare i nomi delle proprietà shader di animazione

1. Passa a finestra > animazione > animazione
1. Verificare che l'oggetto con il Visualizzatore di stato sia selezionato nella gerarchia
1. Selezionare qualsiasi clip di animazione nella finestra animazione
1. Selezionare **Aggiungi proprietà**, aprire la sezione del renderer mesh 

    ![Aggiunta della proprietà Animation nella finestra Animator](../images/interactive-element/StateVisualizer/AnimationWindow.png)

1. Questo elenco contiene i nomi di tutti i nomi di proprietà animabili 

    ![Proprietà di animazione del renderer mesh nella finestra Animator](../images/interactive-element/StateVisualizer/MeshRendererProperties.png)

## <a name="see-also"></a>Vedi anche

- [**Pulsanti**](../ux-building-blocks/button.md)
- [**Controllo dei limiti**](../ux-building-blocks/bounds-control.md)
- [**Raccolta di oggetti Grid**](../ux-building-blocks/object-collection.md)
- [**Risolutore RadialView**](../ux-building-blocks/solvers/solver.md)

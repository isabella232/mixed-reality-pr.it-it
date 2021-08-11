---
title: Con interazione
description: Panoramica sul componente script con interazione in MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, con interazione, eventi,
ms.openlocfilehash: a0aee99d01ae59a8ebedc4d62a4b0aaf844a7afaa6961bbfd05238dd9d5b673d
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115206775"
---
# <a name="interactable"></a>Con interazione

![Con interazione](../images/interactable/InteractableExamples.png)

Il [`Interactable`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) componente è un contenitore all-in-one per rendere qualsiasi oggetto facilmente *intervienibile* e reattivo all'input. Interactable funge da catch-all per tutti i tipi di input, tra cui tocco, raggi della mano, parlato e così via, e incanalare queste interazioni in eventi e risposte [del](visual-themes.md) tema visivo. [](#events) Questo componente offre un modo semplice per creare pulsanti, modificare il colore degli oggetti con lo stato attivo e altro ancora.

## <a name="how-to-configure-interactable"></a>Come configurare Interactable

Il componente consente tre sezioni principali di configurazione:

1) [Configurazione di input generale](#general-input-settings)
1) [Temi visivi](visual-themes.md) destinati a più GameObject
1) [Gestori eventi](#events)

### <a name="general-input-settings"></a>Impostazioni di input generali

![General Interactable Impostazioni](../images/interactable/InputFeatures_short.png)

**Stati**

*States* è un [parametro ScriptableObject](https://docs.unity3d.com/Manual/class-ScriptableObject.html) che definisce le fasi di interazione, ad esempio press o observed, [per](#interactable-profiles) i profili con interazione e i temi [visivi.](visual-themes.md)

**DefaultInteractableStates** (Assets/MRTK/SDK/Features/UX/Interactable/States/DefaultInteractableStates.asset) viene fornito con MRTK predefinito ed è  il parametro predefinito per i componenti interactable.

![Esempio scriptableObject di stati nel controllo](../images/interactable/DefaultInteractableStates.png)

*L'asset DefaultInteractableStates* contiene quattro stati e usa l'implementazione [`InteractableStates`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableStates) del modello di stato.

* **Impostazione** predefinita: non accade nulla, si tratta dello stato di base più isolato.

* **Stato attivo:** l'oggetto viene puntato. Si tratta di uno stato singolo, non sono attualmente impostati altri stati, ma il valore predefinito sarà il valore predefinito.

* **Premere**: l'oggetto viene puntato e viene premuto un pulsante o una mano. Lo stato Press out (Stato di pressione) classifica Default (Predefinito) e Focus (Stato attivo). Questo stato verrà impostato anche come fallback alla pressione fisica.

* **Disabilitato:** il pulsante non deve essere interattivo e il feedback visivo invierà all'utente informazioni se per qualche motivo questo pulsante non è attualmente utilizzabile. In teoria, lo stato disabilitato potrebbe contenere tutti gli altri stati, ma quando l'opzione Abilitato è disattivata, lo stato Disabilitato è contrario a tutti gli altri stati.

Un valore di bit (#) viene assegnato allo stato a seconda dell'ordine nell'elenco.

> [!NOTE]
> È in genere consigliabile usare **DefaultInteractableStates** (Assets/MRTK/SDK/Features/UX/Interactable/States/DefaultInteractableStates.asset) durante la creazione di componenti *interattivi.*
>
> Tuttavia, sono disponibili 17 stati con interazione che possono essere usati per la guida dei temi, anche se alcuni sono destinati ad altri componenti. Di seguito è riportato un elenco di quelli con funzionalità incorporate.
>
> * Visitato: è stato fatto clic su Interactable.
> * Attiva/Disattiva: il pulsante si trova in uno stato attivato/disattivato o l'indice dimensione è un numero dispari.
> * Movimento: la mano o il controller è stato premuto ed è stato spostato dalla posizione originale.
> * VoiceCommand: è stato usato un comando vocale per attivare Interactable.
> * PhysicalTouch: è attualmente rilevato un input tocco, usare [`NearInteractionTouchable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) per abilitare.
> * Afferra: una mano sta attualmente afferrando i limiti dell'oggetto, usare [`NearInteractionGrabbable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionGrabbable) per abilitare

**Enabled**

Attiva o disattiva l'attivazione o meno di un oggetto Interactable. Corrisponde a [`Interactable.IsEnabled`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.IsEnabled) nel codice.

La *proprietà abilitata di un oggetto Interactable* è diversa dalla proprietà abilitata configurata tramite GameObject/Component ,ad esempio SetActive e così via). La disabilitazione di  GameObject o MonoBehaviour con interazione disabiliterà l'esecuzione di tutti gli elementi della classe, inclusi input, temi visivi, eventi e così via. La disabilitazione tramite [`Interactable.IsEnabled`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.IsEnabled) disabilita la maggior parte della gestione dell'input, reimpostando gli stati di input correlati. Tuttavia, la classe eseguirà comunque ogni frame e riceverà eventi di input che verranno ignorati. Ciò è utile per la visualizzazione di Interactable in uno stato disabilitato che può essere eseguito tramite temi visivi. Un esempio tipico è un pulsante di invio in attesa del completamento di tutti i campi di input necessari.

**Azioni di input**

Selezionare [l'azione di input](../input/input-actions.md) dal profilo di configurazione di input o di mapping del controller a cui deve rispondere il componente *Interactable.*

Questa proprietà può essere configurata in fase di esecuzione nel codice tramite [`Interactable.InputAction`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.InputAction) .

**IsGlobal**

Se true, il componente verrà contrassegnato come listener di input globale per l'azione [di input selezionata.](../input/input-actions.md) Il comportamento predefinito è false,  che limita l'input solo a questo collisore/GameObject con interazione.

Questa proprietà può essere configurata in fase di esecuzione nel codice tramite [`Interactable.IsGlobal`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.IsGlobal) .

**Comando vocale**

[Comando vocale,](../input/speech.md)dal profilo dei comandi vocali MRTK, per attivare un evento OnClick per l'interazione vocale.

Questa proprietà può essere configurata in fase di esecuzione nel codice tramite [`Interactable.VoiceCommand`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.VoiceCommand) .

**Richiede lo stato attivo**

Se true, il comando vocale attiverà *interactable* solo se e solo se ha già lo stato attivo da un puntatore. Se false, *interactable* fungerà da listener globale per il comando vocale selezionato. Il comportamento predefinito è true, perché più listener vocali globali possono essere difficili da organizzare in una scena.

Questa proprietà può essere configurata in fase di esecuzione nel codice tramite [`Interactable.VoiceRequiresFocus`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.VoiceRequiresFocus) .

**Modalità di selezione**

Questa proprietà definisce la logica di selezione. Quando si *fa clic* su un oggetto Interactable, esegue l'iterazione in un livello *dimensione* successivo. *Le* dimensioni sono simili alla classificazione e definiscono uno stato all'esterno degli input (ad esempio stato attivo, premere e così via). Sono utili per definire gli stati toggle o altri stati a più classifica associati a un pulsante. Il livello dimensione corrente viene monitorato da `Interactable.DimensionIndex` .

Le modalità di selezione disponibili sono:

* **Pulsante**  -  *Dimensioni* = 1, semplice con interazione *selezionabile*
* **Attiva/Disattiva**  -  *Dimensioni* = 2, *alternabile con* interazione tra *lo stato on* / *off*
* **Più dimensioni**  -  *Dimensioni* >= 3, ogni clic aumenta il livello di dimensione corrente + 1. Utile per definire lo stato di un pulsante in un elenco e così via.

*Interactable* consente anche di definire più temi per ogni *dimensione.* Ad esempio, quando *SelectionMode=Toggle* è possibile applicare  un tema quando *interactable* è deselezionato e un altro tema applicato quando il componente è *selezionato.*

È possibile eseguire query sulla modalità di selezione corrente in fase di esecuzione tramite [`Interactable.ButtonMode`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.ButtonMode) . L'aggiornamento della modalità in fase di esecuzione può essere ottenuto impostando la  [`Interactable.Dimensions`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.Dimensions) proprietà in modo che corrisponda alla funzionalità desiderata. Inoltre, è possibile accedere alla dimensione corrente, utile per le modalità *Toggle* e *Multi-Dimension,* tramite [`Interactable.CurrentDimension`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.CurrentDimension) .

### <a name="interactable-profiles"></a>Profili con interazione

*I* profili sono elementi che creano una relazione tra un GameObject e un [tema visivo.](visual-themes.md) Il profilo definisce il contenuto che verrà modificato da un tema quando si verifica [una modifica dello stato.](#general-input-settings)

I temi funzionano molto come i materiali. Sono oggetti gestibili da script che contengono un elenco di proprietà che verranno assegnate a un oggetto in base allo stato corrente. I temi sono anche riutilizzabili e possono essere assegnati a più *oggetti dell'esperienza* utente con interazione.

**Reimposta in base all'eliminazione**

I temi visivi modificano varie proprietà in un GameObject di destinazione, a seconda della classe e del tipo di motore del tema selezionato. Se *Reset On Destroy è* true quando il componente Interactable viene eliminato, il componente reimposta tutte le proprietà modificate dai temi attivi sui valori originali. In caso contrario, quando viene eliminato, il componente Interactable lascia tutte le proprietà modificate così come sono. In quest'ultimo caso, l'ultimo stato dei valori verrà mantenuto a meno che non venga modificato da un altro componente esterno. Il valore predefinito è false.

<img src="../images/interactable/Profiles_Themes.png" width="450" alt="Profile theams">

## <a name="events"></a>Eventi

Ogni *componente interactable* ha un *evento OnClick* che viene generato quando il componente viene semplicemente selezionato. È tuttavia *possibile usare Interactable* per rilevare eventi di input diversi da *OnClick.*

Fare clic *sul pulsante Aggiungi* evento per aggiungere un nuovo tipo di definizione del ricevitore di eventi. Dopo l'aggiunta, selezionare il tipo di evento desiderato.

![Esempio di eventi](../images/interactable/Events.png))

Esistono diversi tipi di ricevitori di eventi per rispondere a diversi tipi di input. MRTK viene fornito con il set di ricevitori predefinito seguente.

* [`InteractableAudioReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableAudioReceiver)
* [`InteractableOnClickReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnClickReceiver)
* [`InteractableOnFocusReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnFocusReceiver)
* [`InteractableOnGrabReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnGrabReceiver)
* [`InteractableOnHoldReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnHoldReceiver)
* [`InteractableOnPressReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnPressReceiver)
* [`InteractableOnToggleReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnToggleReceiver)
* [`InteractableOnTouchReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnTouchReceiver)

È possibile creare un ricevitore personalizzato effettuando una nuova classe che estende [`ReceiverBase`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBase) .

![Esempio di ricevitore di Attivazione/disattivazione eventi](../images/interactable/Event_toggle.png)

*Esempio di ricevitore di eventi Toggle*

### <a name="interactable-receivers"></a>Ricevitori con interazione

 Il [`InteractableReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableReceiver) componente consente di definire eventi all'esterno del componente *interactable di* origine. *InteractableReceiver rimane in* ascolto di un tipo di evento filtrato generato da un *altro oggetto interactable.* Se la proprietà *Interactable* non è  assegnata direttamente, la proprietà Ambito di ricerca definisce la direzione in cui *InteractableReceiver* è in ascolto di eventi che si verificano su se stesso, in un elemento padre o in un GameObject figlio.

[`InteractableReceiverList`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableReceiverList) funziona in modo simile, ma per un elenco di eventi corrispondenti.

<img src="../images/interactable/InteractableReceiver.png" width="450" alt="Interactable reciver">

### <a name="create-custom-events"></a>Creare eventi personalizzati

Come [i temi visivi,](visual-themes.md#custom-theme-engines)gli eventi possono essere estesi per rilevare qualsiasi modello di stato o esporre funzionalità.

Gli eventi personalizzati possono essere creati in due modi principali:

1) Estendere la [`ReceiverBase`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBase) classe per creare un evento personalizzato che verrà visualizzato nell'elenco a discesa dei tipi di evento. Per impostazione predefinita, viene fornito un evento Unity, ma è possibile aggiungere altri eventi di Unity oppure impostare l'evento in modo da nascondere gli eventi di Unity. Questa funzionalità consente a una finestra di progettazione di lavorare con un tecnico su un progetto per creare un evento personalizzato che la finestra di progettazione può configurare nell'editor.

1) Estendere la [`ReceiverBaseMonoBehavior`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBaseMonoBehavior) classe per creare un componente dell'evento completamente personalizzato che può risiedere nell'oggetto *Interactable* o in un altro oggetto. [`ReceiverBaseMonoBehavior`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBaseMonoBehavior)L'oggetto farà riferimento a *Interactable* per rilevare le modifiche di stato.

#### <a name="example-of-extending-receiverbase"></a>Esempio di estensione `ReceiverBase`

La classe visualizza informazioni sullo stato di un oggetto Interactable ed è un esempio di [`CustomInteractablesReceiver`](xref:Microsoft.MixedReality.Toolkit.UI) come creare un ricevitore di eventi  personalizzato.

```c#
public CustomInteractablesReceiver(UnityEvent ev) : base(ev, "CustomEvent")
{
    HideUnityEvents = true; // hides Unity events in the receiver - meant to be code only
}
```

I metodi seguenti sono utili per eseguire l'override o l'implementazione quando si crea un ricevitore di eventi personalizzato. [`ReceiverBase.OnUpdate()`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBase) è un metodo astratto che può essere usato per rilevare i modelli/transizioni di stato. Inoltre, i [`ReceiverBase.OnVoiceCommand()`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBase) metodi e sono utili per la creazione di logica di eventi personalizzata quando si seleziona [`ReceiverBase.OnClick()`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBase) *Interactable.*

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

##### <a name="displaying-custom-event-receiver-fields-in-the-inspector"></a>Visualizzazione dei campi del ricevitore di eventi personalizzati nel controllo

*Gli script ReceiverBase* [`InspectorField`](xref:Microsoft.MixedReality.Toolkit.Utilities.Editor.InspectorField) usano gli attributi per esporre le proprietà personalizzate nel controllo. Ecco un esempio di Vector3, una proprietà personalizzata con informazioni su descrizione comando ed etichetta. Questa proprietà verrà mostrata come configurabile nel controllo quando viene selezionato un *GameObject* con interazione a cui è stato aggiunto il *tipo di* ricevitore di eventi associato.

```c#
[InspectorField(Label = "<Property label>",Tooltip = "<Insert tooltip info>",Type = InspectorField.FieldTypes.Vector3)]
public Vector3 EffectOffset = Vector3.zero;
```

## <a name="how-to-use-interactable"></a>Come usare Interactable

### <a name="building-a-simple-button"></a>Creazione di un pulsante semplice

È possibile creare un pulsante semplice aggiungendo il *componente Interactable* a un GameObject configurato per ricevere eventi di input. Può avere un collisore su di esso o su un figlio per ricevere l'input. Se si *usa Interactable* con un GameObject basato sull'interfaccia utente di Unity, deve essere in Canvas GameObject.

Fare un ulteriore passo avanti con il pulsante creando un nuovo profilo, assegnando il GameObject stesso e creando un nuovo tema. Usare anche *l'evento OnClick* per eseguire un evento.

> [!NOTE]
> La pressione [di un pulsante](button.md) richiede il componente [`PressableButton`](xref:Microsoft.MixedReality.Toolkit.UI.PressableButton) . Inoltre, il componente [`PhysicalPressEventRouter`](xref:Microsoft.MixedReality.Toolkit.PhysicalPressEventRouter) è necessario per l'imbuto degli eventi di pressione al *componente Interactable.*

### <a name="creating-toggle-and-multi-dimension-buttons"></a>Creazione di pulsanti di attivazione/disattivazione e di più dimensioni

#### <a name="toggle-button"></a>Interruttore

Per rendere un pulsante toggle-able, modificare il [`Selection Mode`](xref:Microsoft.MixedReality.Toolkit.UI.SelectionModes) campo in digitare `Toggle` . Nella sezione *Profili* viene aggiunto un nuovo tema attivato/disattivato per ogni profilo usato quando l'elemento *Interactable* è attivato.

Mentre è impostato su Toggle, la casella di controllo IsToggled può essere usata per impostare il valore predefinito del controllo in fase di [`SelectionMode`](xref:Microsoft.MixedReality.Toolkit.UI.SelectionModes) inizializzazione in fase di esecuzione. 

*CanSelect indica* che *l'elemento Interactable* può andare da *un'opzione* all'altro, mentre *CanDeselect* indica l'inverso. 

![Esempio di temi visivi attiva/disattiva profilo](../images/interactable/Profile_toggle.png)

Gli sviluppatori possono usare le interfacce e per ottenere/impostare lo stato di [`SetToggled`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) [`IsToggled`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) attivazione/disattivazione di un elemento *Interactable* tramite codice.

```c#
// If using SelectionMode = Toggle (i.e Dimensions == 2)

// Make the Interactable selected and toggled on
myInteractable.IsToggled = true;

// Get whether the Interactable is selected or not
bool isSelected = myInteractable.IsToggled;
```

##### <a name="toggle-button-collection"></a>Raccolta di pulsanti di attivazione/disattivazione

È comune avere un elenco di interruttori in cui solo uno può essere attivo in un determinato momento, noto anche come set radiale o pulsanti di opzione e così via.

Usare il [`InteractableToggleCollection`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableToggleCollection) componente per abilitare questa funzionalità. Questo controllo garantisce l'attivazione di un solo *elemento Interactable* in un determinato momento. *RadialSet* (Assets/MRTK/SDK/Features/UX/Interactable/Prefabs/RadialSet.prefab) è anche un ottimo punto di partenza predefinito.

Per creare un gruppo di pulsanti radiali personalizzato:

1) Creare più *GameObject/pulsanti* con supporto per l'interazione
1) Impostare ogni *oggetto Interactable* *con SelectionMode* = Toggle, *CanSelect* = true e *CanDeselect* = false
1) Creare un GameObject padre vuoto su tutti *gli oggetti Interactable e* aggiungere il componente *InteractableToggleCollection*
1) Aggiungere tutti *gli oggetti Interactable* a *ToggleList* in *InteractableToggleCollection*
1) Impostare la *proprietà InteractableToggleCollection.CurrentIndex* per determinare quale pulsante è selezionato per impostazione predefinita all'inizio

<img src="../images/interactable/InteractableToggleCollection.png" width="450" alt="Toggle collection">

#### <a name="multi-dimensional-button"></a>Pulsante multidimensionale

La modalità di selezione multi-dimensione viene usata per creare pulsanti sequenziali o un pulsante con più di due passaggi, ad esempio il controllo della velocità con tre valori, Veloce (1x), Più veloce (2x) o Più veloce (3x).

Con le dimensioni come valore numerico, è possibile aggiungere fino a 9 temi per controllare l'etichetta di testo o la trama del pulsante per ogni impostazione di velocità, usando un tema diverso per ogni passaggio.

Ogni evento click avanza di `DimensionIndex` 1 in fase di esecuzione fino a quando non `Dimensions` viene raggiunto il valore . Il ciclo verrà quindi reimpostato su 0.

![Esempio di profilo multidimensionale](../images/interactable/Profile_multiDimensions.png)

Gli sviluppatori possono valutare [`DimensionIndex`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) per determinare quale dimensione è attualmente attiva.

```c#
// If using SelectionMode = Multi-dimension (i.e Dimensions >= 3)

//Access the current DimensionIndex
int currentDimension = myInteractable.CurrentDimension;

//Set the current DimensionIndex to 2
myInteractable.CurrentDimension = 2;

// Promote Dimension to next level
myInteractable.IncreaseDimension();
```

### <a name="create-interactable-at-runtime"></a>Creare oggetti interactable in fase di esecuzione

*È possibile aggiungere* facilmente oggetti Interactable a qualsiasi GameObject in fase di esecuzione. Nell'esempio seguente viene illustrato come assegnare un profilo con un [tema visivo](visual-themes.md).

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

### <a name="interactable-events-via-code"></a>Eventi con interazione tramite codice

È possibile aggiungere un'azione all'evento di base [`Interactable.OnClick`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.OnClick) tramite codice con l'esempio seguente.

```c#
public static void AddOnClick(Interactable interactable)
{
    interactable.OnClick.AddListener(() => Debug.Log("Interactable clicked"));
}
```

Usare la [`Interactable.AddReceiver<T>()`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) funzione per aggiungere i ricevitori di eventi in modo dinamico in fase di esecuzione.

Il codice di esempio seguente illustra come aggiungere un oggetto [InteractableOnFocusReceiver](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnFocusReceiver)che rimane in ascolto dell'attivazione/uscita dello stato attivo e definisce inoltre il codice azione da eseguire quando vengono eseguite le istanze dell'evento.

```c#
public static void AddFocusEvents(Interactable interactable)
{
    var onFocusReceiver = interactable.AddReceiver<InteractableOnFocusReceiver>();

    onFocusReceiver.OnFocusOn.AddListener(() => Debug.Log("Focus on"));
    onFocusReceiver.OnFocusOff.AddListener(() => Debug.Log("Focus off"));
}
```

Il codice di esempio seguente illustra come aggiungere un oggetto [InteractableOnToggleReceiver](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnFocusReceiver), che rimane in ascolto delle transizioni di stato selezionate/deselezionate sugli oggetti *Interactable* attivabili da toggle e definisce inoltre il codice azione da eseguire quando vengono attivate le istanze dell'evento.

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

## <a name="see-also"></a>Vedi anche

* [Temi degli oggetti visivi](visual-themes.md)
* [Azioni di input](../input/input-actions.md)
* [Comandi vocali](../input/speech.md)
* [Pulsanti](button.md)
* [MRTK Standard Shader](../rendering/MRTK-standard-shader.md)

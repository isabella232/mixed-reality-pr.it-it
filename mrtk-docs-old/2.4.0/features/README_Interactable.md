---
title: README_Interactable
description: Panoramica sul componente script interactable in MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
ms.localizationpriority: medium
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, interactable, eventi,
ms.openlocfilehash: 58aa646a69282da0cfb322031e85cd396def7be5
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2021
ms.locfileid: "104682674"
---
# <a name="interactable"></a>Con cui

![Con cui](Images/Interactable/InteractableExamples.png)

Il [`Interactable`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) componente è un contenitore All-in-One per rendere qualsiasi oggetto facilmente *interactabile* e reattivo all'input. Interactable funge da catch-all per tutti i tipi di input, tra cui il tocco, i raggi di mano, il parlato e così via, e l'imbuto di queste interazioni negli [eventi](#events) e nelle risposte del [tema](visualthemes.md) Questo componente fornisce un modo semplice per creare pulsanti, modificare il colore degli oggetti con lo stato attivo e altro ancora.

## <a name="how-to-configure-interactable"></a>Come configurare interactable

Il componente consente tre sezioni principali della configurazione:

1) [Configurazione di input generale](#general-input-settings)
1) [Temi visivi](VisualThemes.md) destinati a più GameObject
1) [Gestori eventi](#events)

### <a name="general-input-settings"></a>Impostazioni di input generali

![Impostazioni generali per l'interazione](Images/Interactable/InputFeatures_short.png)

**Stati**

*States* è un parametro [ScriptableObject](https://docs.unity3d.com/Manual/class-ScriptableObject.html) che definisce le fasi di interazione, ad esempio premere o osservato, per i profili e i [temi visivi](VisualThemes.md) [interagibili](#interactable-profiles) .

**DefaultInteractableStates** (assets/MRTK/SDK/features/UX/interactable/States/DefaultInteractableStates. asset) viene fornito con MRTK predefinito ed è il parametro predefinito per i componenti *interagibili* .

![Esempio di ScriptableObject di stati in Inspector](Images/Interactable/DefaultInteractableStates.png)

L'asset *DefaultInteractableStates* contiene quattro Stati e usa l' [`InteractableStates`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableStates) implementazione del modello di stato.

* **Impostazione predefinita**: non viene eseguita alcuna operazione. si tratta dello stato di base più isolato.

* **Focus**: l'oggetto a cui si fa riferimento. Si tratta di uno stato singolo, nessun altro stato è attualmente impostato, ma il valore predefinito è rango.

* **Premere**: viene fatto riferimento all'oggetto e viene premuto un pulsante o una mano. Per impostazione predefinita, lo stato viene impostato su Allinea e lo stato attivo. Questo stato verrà inoltre impostato come fallback per la pressione fisica.

* **Disabilitato**: il pulsante non deve essere interattivo e il feedback visivo consente all'utente di verificare se per qualche motivo questo pulsante non è utilizzabile in questo momento. In teoria, lo stato disabilitato potrebbe contenere tutti gli altri Stati, ma se abilitato è disattivato, lo stato disabilitato trionferà su tutti gli altri Stati.

A seconda dell'ordine nell'elenco, viene assegnato un valore di bit (#) allo stato.

> [!NOTE]
> È in genere consigliabile usare **DefaultInteractableStates** (assets/MRTK/SDK/features/UX/interactable/States/DefaultInteractableStates. asset) quando si creano componenti *interagibili* .
>
> Tuttavia, sono disponibili 17 Stati interagibili che possono essere usati per guidare i temi, anche se alcuni sono pensati per essere gestiti da altri componenti. Di seguito è riportato un elenco di quelli con funzionalità predefinite.
>
> * Visitata: è stato fatto clic su interactable.
> * Attivato/disattivato: il pulsante è in uno stato o un indice della dimensione disattivato è un numero dispari.
> * Gesto: la mano o il controller è stato premuto ed è stato spostato dalla posizione originale.
> * VoiceCommand: è stato usato un comando per la sintesi vocale per attivare l'interazione.
> * PhysicalTouch: è attualmente rilevato un input tocco, [`NearInteractionTouchable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) da usare per abilitare.
> * Acquisisci: una mano è attualmente in fase di acquisizione nei limiti dell'oggetto, usare [`NearInteractionGrabbable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionGrabbable) per abilitare

**Enabled**

Consente di attivare o meno l'abilitazione di un oggetto che interagisce. Corrisponde al [`Interactable.IsEnabled`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.IsEnabled) nel codice.

Una proprietà abilitata per *Interact* è diversa dalla proprietà Enabled configurata tramite GameObject/Component (ovvero Seattivo e così via). La disabilitazione di GameObject *o di* monobehavior interattivi comporta la disabilitazione di tutti gli elementi nella classe, inclusi input, temi visivi, eventi e così via. La disabilitazione [`Interactable.IsEnabled`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.IsEnabled) di via Disabilita la maggior parte della gestione degli input, reimpostando gli Stati di input correlati. Tuttavia, la classe continuerà a eseguire tutti i frame e a ricevere eventi di input che verranno ignorati. Questa operazione è utile per visualizzare lo stato interattivo in uno stato disabilitato, che può essere eseguito tramite temi visivi. Un esempio tipico è costituito da un pulsante di invio in attesa del completamento di tutti i campi di input necessari.

**Azioni di input**

Consente di selezionare l' [azione di input](./Input/InputActions.md) dal profilo di configurazione di input o di mapping del controller a cui il componente *interagibile* deve rispondere.

Questa proprietà può essere configurata in fase di esecuzione nel codice tramite [`Interactable.InputAction`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.InputAction) .

**IsGlobal**

Se true, il componente viene contrassegnato come listener di input globale per l'azione di [input](./Input/InputActions.md)selezionata. Il comportamento predefinito è false che consente di limitare l'input solo a questo Collider/GameObject di *interazione* .

Questa proprietà può essere configurata in fase di esecuzione nel codice tramite [`Interactable.IsGlobal`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.IsGlobal) .

**Comando sintesi vocale**

[Comando di sintesi vocale](./Input/Speech.md), dal profilo dei comandi di sintesi vocale MRTK, per attivare un evento OnClick per l'interazione vocale.

Questa proprietà può essere configurata in fase di esecuzione nel codice tramite [`Interactable.VoiceCommand`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.VoiceCommand) .

**Richiede lo stato attivo**

Se true, il comando Voice attiverà solo l'interoperabilità *solo se è* già stato attivato da un puntatore. Se false, l' *interfaccia* interoperabile fungerà da listener globale per il comando Voice selezionato. Il comportamento predefinito è true, in quanto più listener di riconoscimento vocale globale possono essere difficili da organizzare in una scena.

Questa proprietà può essere configurata in fase di esecuzione nel codice tramite [`Interactable.VoiceRequiresFocus`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.VoiceRequiresFocus) .

**Modalità di selezione**

Questa proprietà definisce la logica di selezione. Quando si fa clic su un oggetto *interactable* , viene iterato in un livello di *dimensione* successivo. *Dimensions* è simile a Rank e definisce uno stato al di fuori degli input (ad esempio concentrarsi, premere e così via. Sono utili per definire gli Stati di attivazione/disattivazione o altri Stati con più livelli associati a un pulsante. Il livello della dimensione corrente viene rilevato da `Interactable.DimensionIndex` .

Le modalità di selezione disponibili sono:

* **Pulsante**  -  *Dimensioni* = 1, semplice e *interattivo* selezionabile
* **Imposta/Nascondi**  -  *Dimensioni* = *2,* alternanze  / *interattive* tra lo stato disattivato
* **MULTIDIMENSIONE**  -  *Dimensions* >= 3, ogni clic aumenta il livello della dimensione corrente + 1. Utile per definire lo stato di un pulsante in un elenco e così via.

*Interactable* consente inoltre di definire più temi per *dimensione*. Ad esempio, quando *SelectionMode = interruttore*, un tema può essere applicato quando l'elemento *Interagisci* viene *deselezionato* e un altro tema viene applicato quando il componente è *selezionato*.

La modalità di selezione corrente può essere sottoposta a query in fase di esecuzione tramite [`Interactable.ButtonMode`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.ButtonMode) . L'aggiornamento della modalità in fase di esecuzione può essere eseguito impostando la  [`Interactable.Dimensions`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.Dimensions) Proprietà in modo che corrisponda alla funzionalità desiderata. Inoltre, è possibile accedere alla dimensione corrente, utile per le modalità di *attivazione/disattivazione* e *MULTIDIMENSIONE* , tramite [`Interactable.CurrentDimension`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.CurrentDimension) .

### <a name="interactable-profiles"></a>Profili interagibili

I *profili* sono elementi che creano una relazione tra un GameObject e un [tema visivo](VisualThemes.md). Il profilo definisce il contenuto che verrà modificato da un tema quando [si verifica una modifica dello stato](#general-input-settings).

I temi funzionano in modo molto simile ai materiali. Sono oggetti configurabili tramite script che contengono un elenco di proprietà che verranno assegnate a un oggetto in base allo stato corrente. Anche i temi sono riutilizzabili e possono essere assegnati tra più oggetti UX di *interazione* .

**Reimposta in eliminazione**

I temi visivi modificano varie proprietà in un GameObject di destinazione, a seconda della classe e del tipo di motore di tema selezionato. Se *Reset on Destroy* è true quando il componente interactable viene eliminato definitivamente, il componente Reimposta tutte le proprietà modificate dai temi attivi ai valori originali. In caso contrario, quando viene distrutta, il componente interactable lascerà le proprietà modificate così come sono. In quest'ultimo caso, l'ultimo stato dei valori verrà mantenuto a meno che non venga modificato da un altro componente esterno. Il valore predefinito è false.

<img src="Images/Interactable/Profiles_Themes.png" width="450" alt="Profile Themes">

## <a name="events"></a>Eventi

Ogni componente *interagibile* ha un evento *OnClick* che viene attivato quando il componente viene semplicemente selezionato. Tuttavia, *è* possibile utilizzare Interoperable per rilevare eventi di input diversi da solo *OnClick*.

Fare clic sul pulsante *Aggiungi evento* per aggiungere un nuovo tipo di definizione del ricevitore di eventi. Una volta aggiunto, selezionare il tipo di evento desiderato.

![Esempio di eventi](Images/Interactable/Events.png))

Esistono diversi tipi di destinatari di eventi per rispondere a diversi tipi di input. MRTK viene fornito con il seguente set di ricevitori predefiniti.

* [`InteractableAudioReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableAudioReceiver)
* [`InteractableOnClickReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnClickReceiver)
* [`InteractableOnFocusReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnFocusReceiver)
* [`InteractableOnGrabReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnGrabReceiver)
* [`InteractableOnHoldReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnHoldReceiver)
* [`InteractableOnPressReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnPressReceiver)
* [`InteractableOnToggleReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnToggleReceiver)
* [`InteractableOnTouchReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnTouchReceiver)

Per creare un ricevitore personalizzato, è possibile creare una nuova classe che estenda [`ReceiverBase`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBase) .

![Esempio di ricevitore interruttore evento](Images/Interactable/Event_toggle.png)

*Esempio di ricevitore di eventi di attivazione/disattivione*

### <a name="interactable-receivers"></a>Ricevitori interagiscono

 Il [`InteractableReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableReceiver) componente consente di definire gli eventi all'esterno del componente *interactabile* di origine. *InteractableReceiver* resterà in ascolto di un tipo di evento filtrato generato da un altro *interactable*. Se la proprietà *interagibile* non viene assegnata direttamente, la proprietà dell' *ambito di ricerca* definisce la direzione in cui *InteractableReceiver* è in ascolto per gli eventi che si trova su se stesso, in un elemento padre o in un GameObject figlio.

[`InteractableReceiverList`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableReceiverList) funziona in modo simile, ma per un elenco di eventi corrispondenti.

<img src="Images/Interactable/InteractableReceiver.png" width="450" alt="Interactable Reciver">

### <a name="create-custom-events"></a>Creazione di eventi personalizzati

Analogamente ai [temi visivi](VisualThemes.md#custom-theme-engines), gli eventi possono essere estesi per rilevare qualsiasi modello di stato o per esporre la funzionalità.

Gli eventi personalizzati possono essere creati in due modi principali:

1) Estendere la [`ReceiverBase`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBase) classe per creare un evento personalizzato che sarà visualizzato nell'elenco a discesa dei tipi di evento. Per impostazione predefinita viene fornito un evento Unity, ma è possibile aggiungere altri eventi Unity oppure è possibile impostare l'evento in modo da nascondere gli eventi Unity. Questa funzionalità consente a una finestra di progettazione di collaborare con un tecnico di un progetto per creare un evento personalizzato che la finestra di progettazione può configurare nell'editor.

1) Estendere la [`ReceiverBaseMonoBehavior`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBaseMonoBehavior) classe per creare un componente evento completamente personalizzato che può risiedere in  un altro oggetto. Il [`ReceiverBaseMonoBehavior`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBaseMonoBehavior) fa riferimento a *interactable* per rilevare le modifiche di stato.

#### <a name="example-of-extending-receiverbase"></a>Esempio di estensione `ReceiverBase`

La [`CustomInteractablesReceiver`](xref:Microsoft.MixedReality.Toolkit.UI) classe Visualizza informazioni sullo stato di un' *interfaccia interactabile* ed è un esempio di creazione di un ricevitore di eventi personalizzato.

```c#
public CustomInteractablesReceiver(UnityEvent ev) : base(ev, "CustomEvent")
{
    HideUnityEvents = true; // hides Unity events in the receiver - meant to be code only
}
```

I metodi seguenti sono utili per eseguire l'override o l'implementazione durante la creazione di un ricevitore di eventi personalizzato. [`ReceiverBase.OnUpdate()`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBase) è un metodo astratto che può essere utilizzato per rilevare le transizioni/modelli di stato. Inoltre, i [`ReceiverBase.OnVoiceCommand()`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBase) [`ReceiverBase.OnClick()`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBase) metodi e sono utili per la creazione di una logica di evento personalizzata quando si seleziona *interactabile* .

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

Gli script *ReceiverBase* usano [`InspectorField`](xref:Microsoft.MixedReality.Toolkit.Utilities.Editor.InspectorField) gli attributi per esporre le proprietà personalizzate nel controllo. Di seguito è riportato un esempio di Vector3, una proprietà personalizzata con le informazioni sull'etichetta e la descrizione comando. Questa proprietà viene visualizzata come configurabile nel controllo quando è selezionato *un GameObject* interoperabile e il tipo di *ricevitore di eventi* associato è stato aggiunto.

```c#
[InspectorField(Label = "<Property label>",Tooltip = "<Insert tooltip info>",Type = InspectorField.FieldTypes.Vector3)]
public Vector3 EffectOffset = Vector3.zero;
```

## <a name="how-to-use-interactable"></a>Come usare interactable

### <a name="building-a-simple-button"></a>Creazione di un pulsante semplice

È possibile creare un pulsante semplice aggiungendo il componente *Interactabile* a un GameObject configurato per la ricezione di eventi di input. Può avere un Collider o un elemento figlio per ricevere input. Se si usa l'interfaccia *interagibile* con un GameObject basato sull'interfaccia utente di Unity, deve trovarsi sotto il GameObject Canvas.

Prendere il pulsante più avanti creando un nuovo profilo, assegnando il GameObject stesso e creando un nuovo tema. Inoltre, utilizzare l'evento *OnClick* per eseguire un'operazione.

> [!NOTE]
> Per rendere la pressione di un [pulsante](README_Button.md) è necessario il [`PressableButton`](xref:Microsoft.MixedReality.Toolkit.UI.PressableButton) componente. Inoltre, il [`PhysicalPressEventRouter`](xref:Microsoft.MixedReality.Toolkit.PhysicalPressEventRouter) componente è necessario per l'imbuto degli eventi di pressione nel componente *interactabile* .

### <a name="creating-toggle-and-multi-dimension-buttons"></a>Creazione di pulsanti di attivazione/disattivazione e MULTIDIMENSIONE

#### <a name="toggle-button"></a>Interruttore

Per impostare un pulsante in modo da attivarlo, impostare il [`Selection Mode`](xref:Microsoft.MixedReality.Toolkit.UI.SelectionModes) campo su tipo `Toggle` . Nella sezione *profili* viene aggiunto un nuovo tema attivato per ogni profilo che viene usato quando il controllo *interattivo* è attivato.

Mentre l'oggetto [`SelectionMode`](xref:Microsoft.MixedReality.Toolkit.UI.SelectionModes) è impostato su interruttore, è  possibile utilizzare la casella di controllo attivato per impostare il valore predefinito del controllo in fase di inizializzazione in fase di esecuzione.

*CanSelect* significa che *interagisce* può passare dall' *esterno* a *on* mentre il *CanDeselect* indica l'inverso.

![Esempio di profilatura di elementi visivi](Images/Interactable/Profile_toggle.png)

Gli sviluppatori possono utilizzare le [`SetToggled`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) [`IsToggled`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) interfacce e per ottenere/impostare lo stato di attivazione/disinstallazione di un codice *interattivo* tramite codice.

```c#
// If using SelectionMode = Toggle (i.e Dimensions == 2)

// Make the Interactable selected and toggled on
myInteractable.IsToggled = true;

// Get whether the Interactable is selected or not
bool isSelected = myInteractable.IsToggled;
```

##### <a name="toggle-button-collection"></a>Imposta/Rimuovi pulsante

È comune avere un elenco di pulsanti di attivazione, in cui solo uno può essere attivo in qualsiasi momento, anche noto come un set radiale o pulsanti di opzione e così via.

Utilizzare il [`InteractableToggleCollection`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableToggleCollection) componente per abilitare questa funzionalità. Questo controllo garantisce che venga attivato un solo *Interactabile* in un determinato momento. Il *RadialSet* (assets/MRTK/SDK/features/UX/interactable/prefabrics/RadialSet. prefabbricate) è anche un ottimo punto di partenza.

Per creare un gruppo di pulsanti radiali personalizzati:

1) Crea più GameObject/pulsanti *Interagiscabili*
1) Impostare ogni *interagire* con *SelectionMode* = interruttore, *CanSelect* = true e *CanDeselect* = false
1) Creare un GameObject padre vuoto su tutti i *Interactables* e aggiungere il componente *InteractableToggleCollection*
1) Aggiungere tutti *Interactables* a *ToggleList* in *InteractableToggleCollection*
1) Impostare la proprietà *InteractableToggleCollection. CurrentIndex* per determinare quale pulsante è selezionato per impostazione predefinita all'avvio

<img src="Images/Interactable/InteractableToggleCollection.png" width="450" alt="Interactable ">

#### <a name="multi-dimensional-button"></a>Pulsante multidimensionale

La modalità di selezione MULTIDIMENSIONE viene utilizzata per creare pulsanti sequenziali o un pulsante che include più di due passaggi, ad esempio il controllo della velocità con tre valori, veloce (1x), più veloce (2x) o più veloce (3x).

Con le dimensioni che costituiscono un valore numerico, è possibile aggiungere fino a 9 temi per controllare l'etichetta di testo o la trama del pulsante per ogni impostazione di velocità, usando un tema diverso per ogni passaggio.

Ogni evento Click anticiperà la `DimensionIndex` di 1 in fase di esecuzione fino a quando non `Dimensions` viene raggiunto il valore. Il ciclo verrà quindi reimpostato su 0.

![Esempio di profilo multidimensionale](Images/Interactable/Profile_multiDimensions.png)

Gli sviluppatori possono valutare [`DimensionIndex`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) per determinare la dimensione attualmente attiva.

```c#
// If using SelectionMode = Multi-dimension (i.e Dimensions >= 3)

//Access the current DimensionIndex
int currentDimension = myInteractable.CurrentDimension;

//Set the current DimensionIndex to 2
myInteractable.CurrentDimension = 2;

// Promote Dimension to next level
myInteractable.IncreaseDimension();
```

### <a name="create-interactable-at-runtime"></a>Crea interactabile in fase di esecuzione

È possibile aggiungere facilmente *interactable* a qualsiasi GameObject in fase di esecuzione. Nell'esempio seguente viene illustrato come assegnare un profilo con un [tema visivo](visualthemes.md).

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

### <a name="interactable-events-via-code"></a>Eventi interactabili tramite codice

È possibile aggiungere un'azione all'evento di base [`Interactable.OnClick`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.OnClick) tramite codice con l'esempio seguente.

```c#
public static void AddOnClick(Interactable interactable)
{
    interactable.OnClick.AddListener(() => Debug.Log("Interactable clicked"));
}
```

Usare la [`Interactable.AddReceiver<T>()`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) funzione per aggiungere i ricevitori di eventi in modo dinamico in fase di esecuzione.

Il codice di esempio riportato di seguito illustra come aggiungere un [InteractableOnFocusReceiver](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnFocusReceiver), che rimane in attesa di invio/uscita dello stato attivo, nonché definire il codice dell'azione da eseguire quando vengono attivate le istanze dell'evento.

```c#
public static void AddFocusEvents(Interactable interactable)
{
    var onFocusReceiver = interactable.AddReceiver<InteractableOnFocusReceiver>();

    onFocusReceiver.OnFocusOn.AddListener(() => Debug.Log("Focus on"));
    onFocusReceiver.OnFocusOff.AddListener(() => Debug.Log("Focus off"));
}
```

Il codice di esempio riportato di seguito illustra come aggiungere un [InteractableOnToggleReceiver](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnFocusReceiver), che rimane in attesa delle transizioni di stato selezionate/deselezionate in *Interactables* abilitati per l'attivazione/disattivazione e definisce inoltre il codice dell'azione da eseguire quando vengono attivate le istanze di evento.

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

* [Temi visivi](VisualThemes.md)
* [Azioni di input](./Input/InputActions.md)
* [Comandi vocali](./Input/Speech.md)
* [Pulsanti](README_Button.md)
* [Shader standard MRTK](README_MRTKStandardShader.md)

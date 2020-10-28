---
title: Controller di HP Reverb G2 in Unity
description: Istruzioni sull'uso dei controller HP Reverb G2 in SteamVR e in realtà mista di Windows.
author: hferrone
ms.author: v-hferrone
ms.date: 10/14/2020
ms.topic: article
keywords: Unity, Reverb, Reverb G2, HP reverbi G2, realtà mista, sviluppo, controller di movimento, input utente, funzionalità, nuovo progetto, emulatore, documentazione, guide, funzionalità, ologrammi, sviluppo di giochi
ms.openlocfilehash: 17f373a3d94740bf103821b85ee5d6fe4dbaa11f
ms.sourcegitcommit: 8b16945d6a551f174a65fa3980ba392682ca45d4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/28/2020
ms.locfileid: "92886254"
---
# <a name="hp-reverb-g2-controllers-in-unity"></a>Controller di HP Reverb G2 in Unity

I controller di movimento HP sono un nuovo tipo di controller di realtà mista di Windows: tutte le stesse tecnologie di rilevamento con un set leggermente diverso di input disponibili: 

* Touchpad è stato sostituito da due pulsanti: A e B per il controller destro e X e Y per il controller sinistro. 
* La funzione di comprensione è ora un trigger che pubblica un flusso di valori compreso tra 0,0 e 1,0 anziché un pulsante con gli stati premuto e non premuto. 

Poiché i nuovi input non sono accessibili tramite le API Windows e Unity esistenti, è necessario il pacchetto di **Microsoft. MixedReality. input** . 

> [!IMPORTANT]
> **Le classi in questo pacchetto non sostituiscono le API Windows e Unity esistenti, ma le completano.** Le funzionalità disponibili in genere per i controller di realtà misto di Windows classico e i controller di movimento HP sono accessibili tramite lo stesso percorso di codice usando le API esistenti. Solo i nuovi input richiedono l'uso del pacchetto Microsoft. MixedReality. input aggiuntivo. 

## <a name="hp-motion-controller-overview"></a>Panoramica di HP Motion controller

*Microsoft. MixedReality. input. MotionController* rappresenta un controller di movimento. Ogni istanza di *MotionController* dispone di una *XR. WSA. Input. InteractionSource* peer, che può essere correlato tramite la manualità, l'ID del fornitore, l'ID prodotto e la versione. 

È possibile recuperare le istanze di MotionController creando un *MotionControllerWatcher* e sottoscrivendo gli eventi, in modo analogo all'uso di eventi *InteractionManager* per individuare nuove istanze di *InteractionSource* . I metodi e le proprietà di MotionController descrivono gli input supportati dal controller, inclusi i pulsanti, i trigger, l'asse 2D e levetta. La classe MotionController espone inoltre metodi per l'accesso agli Stati di input tramite la classe *MotionControllerReading* . La classe MotionControllerReading rappresenta uno snapshot dello stato del controller in un determinato momento. 

## <a name="installing-microsoftmixedrealityinput-using-the-unity-package-manager"></a>Installazione di Microsoft. MixedReality. input tramite Gestione pacchetti Unity 

Gestione pacchetti Unity usa un [file manifesto](https://docs.unity3d.com/Manual/upm-manifestPkg.html) (manifest.json) per determinare i pacchetti da installare e i registri (Server) da cui possono essere installati. Prima di poter usare il pacchetto Microsoft. MixedReality. input, è necessario registrare il server del componente per la realtà mista.

### <a name="registering-the-mixed-reality-component-server"></a>Registrazione del server del componente realtà mista 

Per ogni progetto che utilizzerà il pacchetto di input della realtà mista, la manifest.jssul file (nella cartella Pacchetti) richiede l'aggiunta del registro di sistema con ambito di realtà misto. Per modificare correttamente manifest.jssu per supportare la realtà mista: 
    1. Aprire <projectRoot> /Packages/manifest.jsin un editor di testo, ad esempio Visual Studio Code. 
    2. Nella parte superiore del file manifesto aggiungere il server di realtà misto alla sezione del registro di sistema con ambito e salvare il file. 
    
<pre>
{ 
  "scopedRegistries": [ 
    { 
      "name": "Microsoft Mixed Reality", 
      "url": "https://pkgs.dev.azure.com/aipmr/MixedReality-Unity-Packages/_packaging/Unity-packages/npm/registry/", 
      "scopes": [ 
        "com.microsoft.mixedreality" 
      ] 
    } 
  ], 
</pre>

### <a name="adding-the-microsoftmixedrealityinput-package"></a>Aggiunta del pacchetto Microsoft. MixedReality. input 

Modificare la sezione dipendenze del <projectRoot> manifest.js/Packages/su file nell'editor di testo per aggiungere il pacchetto com. Microsoft. mixedreality. input e salvare il file. 

<pre>
  "dependencies": { 
    "com.microsoft.mixedreality.input": "0.9.2006", 
  }
</pre>

## <a name="using-microsoftmixedrealityinput"></a>Uso di Microsoft. MixedReality. input 

### <a name="input-values"></a>Valori di input

Un MotionController può esporre due tipi di input: 

* I pulsanti e gli Stati dei trigger sono espressi da un valore float univoco compreso tra 0,0 e 1,0 che indica la quantità di pressione selezionata.
    * Un pulsante può restituire solo 0,0 (se non premuto) o 1,0 (quando premuto) mentre un trigger può restituire valori continui compresi tra 0,0 (completamente rilasciato) e 1,0 (completamente premuto). 
* Lo stato levetta è espresso da un valore Vector2 i cui componenti X e Y sono compresi tra-1,0 e 1,0. 

È possibile usare *MotionController. GetPressableInputs ()* per restituire un elenco di input che restituiscono un valore premuto (pulsanti e trigger) o il metodo *MotionController. GetXYInputs ()* per restituire un elenco di input che restituiscono un valore di 2 assi. 

Un'istanza di MotionControllerReading rappresenta lo stato del controller in un determinato momento: 

* *GetPressedValue ()* recupera lo stato di un pulsante o di un trigger. 
* *GetXYValue ()* recupera lo stato di un levetta. 

### <a name="creating-a-cache-to-maintain-a-collection-of-motioncontroller-instances-and-their-states"></a>Creazione di una cache per la gestione di una raccolta di istanze di MotionController e dei relativi stati 

Iniziare creando un'istanza di MotionControllerWatcher e registrando i gestori per i relativi eventi *MotionControllerAdded* e *MotionControllerRemoved* per memorizzare una cache di istanze MotionController disponibili. Questa cache deve essere un monocomportamento associato a un GameObject, come illustrato nel codice seguente:

```csharp
public class MotionControllerStateCache : MonoBehaviour 
{ 
    /// <summary> 
    /// Internal helper class which associates a Motion Controller 
    /// and its known state 
    /// </summary> 
    private class MotionControllerState 
    { 
        /// <summary> 
        /// Construction 
        /// </summary> 
        /// <param name="mc">motion controller</param>` 
        public MotionControllerState(MotionController mc) 
        { 
            this.MotionController = mc; 
        } 

        /// <summary> 
        /// Motion Controller that the state represents 
        /// </summary> 
        public MotionController MotionController { get; private set; } 
        … 
    } 

    private MotionControllerWatcher _watcher; 
    private Dictionary<Handedness, MotionControllerState> 
        _controllers = new Dictionary<Handedness, MotionControllerState>(); 

    /// <summary> 
    /// Starts monitoring controller's connections and disconnections 
    /// </summary> 
    public void Start() 
    { 
        _watcher = new MotionControllerWatcher(); 
        _watcher.MotionControllerAdded += _watcher_MotionControllerAdded; 
        _watcher.MotionControllerRemoved += _watcher_MotionControllerRemoved; 
        var nowait = _watcher.StartAsync(); 
    } 

    /// <summary> 
    /// Stops monitoring controller's connections and disconnections 
    /// </summary> 
    public void Stop() 
    { 
        if (_watcher != null) 
        { 
            _watcher.MotionControllerAdded -= _watcher_MotionControllerAdded; 
            _watcher.MotionControllerRemoved -= _watcher_MotionControllerRemoved; 
            _watcher.Stop(); 
        } 
    }

    /// <summary> 
    /// called when a motion controller has been removed from the system: 
    /// Remove a motion controller from the cache 
    /// </summary> 
    /// <param name="sender">motion controller watcher</param> 
    /// <param name="e">motion controller </param> 
    private void _watcher_MotionControllerRemoved(object sender, MotionController e) 
    { 
        lock (_controllers) 
        { 
            _controllers.Remove(e.Handedness); 
        } 
    }

    /// <summary> 
    /// called when a motion controller has been added to the system: 
    /// Remove a motion controller from the cache 
    /// </summary> 
    /// <param name="sender">motion controller watcher</param> 
    /// <param name="e">motion controller </param> 
    private void _watcher_MotionControllerAdded(object sender, MotionController e) 
    { 
        lock (_controllers) 
        { 
            _controllers[e.Handedness] = new MotionControllerState(e); 
        } 
    } 
} 
```

### <a name="reading-new-inputs-by-polling"></a>Lettura di nuovi input tramite polling 

È possibile leggere lo stato corrente di ogni controller noto tramite *MotionController. TryGetReadingAtTime* durante il metodo *Update* della classe monobehavior. Si desidera passare *DateTime. Now* come parametro timestamp per assicurarsi che venga letto lo stato più recente del controller. 

```csharp
public class MotionControllerStateCache : MonoBehaviour 
{ 
    … 

    private class MotionControllerState 
    {
        … 

        /// <summary> 
        /// Update the current state of the motion controller 
        /// </summary> 
        /// <param name="when">time of the reading</param> 
        public void Update(DateTime when) 
        { 
            this.CurrentReading = this.MotionController.TryGetReadingAtTime(when); 
        } 

        /// <summary> 
        /// Last reading from the controller 
        /// </summary> 
        public MotionControllerReading CurrentReading { get; private set; } 
    } 

    /// <summary> 
    /// Updates the input states of the known motion controllers 
    /// </summary> 
    public void Update() 
    { 
        var now = DateTime.Now; 

        lock (_controllers) 
        { 
            foreach (var controller in _controllers) 
            { 
                controller.Value.Update(now); 
            } 
        } 
    } 
} 
```

È possibile acquisire il valore di input corrente dei controller usando la manualità del controller: 

```csharp
public class MotionControllerStateCache : MonoBehaviour 
{ 
    … 
    /// <summary> 
    /// Returns the current value of a controller input such as button or trigger 
    /// </summary> 
    /// <param name="handedness">Handedness of the controller</param> 
    /// <param name="input">Button or Trigger to query</param> 
    /// <returns>float value between 0.0 (not pressed) and 1.0 
    /// (fully pressed)</returns> 
    public float GetValue(Handedness handedness, ControllerInput input) 
    { 
        MotionControllerReading currentReading = null; 

        lock (_controllers) 
        { 
            if (_controllers.TryGetValue(handedness, out MotionControllerState mc)) 
            { 
                currentReading = mc.CurrentReading; 
            } 
        } 

        return (currentReading == null) ? 0.0f : currentReading.GetPressedValue(input); 
    } 

    /// <summary> 
    /// Returns the current value of a controller input such as button or trigger 
    /// </summary> 
    /// <param name="handedness">Handedness of the controller</param> 
    /// <param name="input">Button or Trigger to query</param> 
    /// <returns>float value between 0.0 (not pressed) and 1.0 
    /// (fully pressed)</returns> 
    public float GetValue(UnityEngine.XR.WSA.Input.InteractionSourceHandedness handedness, ControllerInput input) 
    { 
        return GetValue(Convert(handedness), input); 
    } 

    /// <summary> 
    /// Returns a boolean indicating whether a controller input such as button or trigger is pressed 
    /// </summary> 
    /// <param name="handedness">Handedness of the controller</param> 
    /// <param name="input">Button or Trigger to query</param> 
    /// <returns>true if pressed, false if not pressed</returns> 
    public bool IsPressed(Handedness handedness, ControllerInput input) 
    { 
        return GetValue(handedness, input) >= PressedThreshold; 
    } 
} 
```

Ad esempio, per leggere il valore di stretta analogo di un InteractionSource: 

```csharp
/// Read the analog grasp value of all connected interaction sources 
void Update() 
{ 
    … 
    var stateCache = gameObject.GetComponent<MotionControllerStateCache>(); 
    foreach (var sourceState in InteractionManager.GetCurrentReading()) 
    { 
        float graspValue = stateCache.GetValue(sourceState.source.handedness, 
            Microsoft.MixedReality.Input.ControllerInput.Grasp);
        … 
    }
} 
```

### <a name="generating-events-from-the-new-inputs"></a>Generazione di eventi dai nuovi input 

Anziché eseguire il polling dello stato di un controller una volta per ogni fotogramma, è possibile scegliere di gestire tutte le modifiche di stato come eventi, consentendo di gestire anche le azioni più veloci che durano meno di un frame. Per il corretto funzionamento di questo approccio, è necessario che la cache dei controller di movimento elabori tutti gli stati pubblicati da un controller dall'ultimo frame. a tale scopo, è possibile archiviare il timestamp dell'ultimo MotionControllerReading recuperato da un MotionController e chiamare *MotionController. TryGetReadingAfterTime ()* : 

```csharp
private class MotionControllerState 
{ 
    … 
    /// <summary> 
    /// Returns an array representng buttons which are pressed 
    /// </summary> 
    /// <param name="reading">motion controller reading</param> 
    /// <returns>array of booleans</returns> 
    private bool[] GetPressed(MotionControllerReading reading) 
    { 
        if (reading == null) 
        { 
            return null; 
        } 
        else 
        { 
            bool[] ret = new bool[this.pressableInputs.Length]; 
            for (int i = 0; i < pressableInputs.Length; ++i) 
            { 
                ret[i] = reading.GetPressedValue(pressableInputs[i]) >= PressedThreshold; 
            } 

            return ret; 
        } 
    } 

    /// <summary> 
    /// Get the next available state of the motion controller 
    /// </summary> 
    /// <param name="lastReading">previous reading</param> 
    /// <param name="newReading">new reading</param> 
    /// <returns>true is a new reading was available</returns> 
    private bool GetNextReading(MotionControllerReading lastReading, out MotionControllerReading newReading) 
    { 
        if (lastReading == null) 
        { 
            // Get the first state published by the controller 
            newReading = this.MotionController.TryGetReadingAfterSystemRelativeTime(TimeSpan.FromSeconds(0.0)); 
        } 
        else 
        { 
            // Get the next state published by the controller 
            newReading = this.MotionController.TryGetReadingAfterTime(lastReading.InputTime); 
        } 

        return newReading != null; 
    } 

    /// <summary> 
    /// Processes all the new states published by the controller since the last call 
    /// </summary> 
    public IEnumerable<MotionControllerEventArgs> GetNextEvents() 
    {
        MotionControllerReading lastReading = this.CurrentReading; 
        bool[] lastPressed = GetPressed(lastReading); 
        MotionControllerReading newReading; 
        bool[] newPressed; 

        while (GetNextReading(lastReading, out newReading)) 
        { 
            newPressed = GetPressed(newReading); 

            // If we have two readings, compare and generate events 
            if (lastPressed != null) 
            { 
                for (int i = 0; i < pressableInputs.Length; ++i) 
                { 
                    if (newPressed[i] != lastPressed[i]) 
                    { 
                        yield return new MotionControllerEventArgs(this.MotionController.Handedness, newPressed[i], this.pressableInputs[i], newReading.InputTime); 
                    } 
                } 
            } 

            lastPressed = newPressed; 
            lastReading = newReading; 
        } 

        // No more reading 
        this.CurrentReading = lastReading; 
    } 
} 
```

A questo punto, dopo aver aggiornato le classi interne della cache, la classe monobehavior può esporre due eventi, premuti e rilasciati, e generarli dal metodo Update (): 

```csharp
/// <summary> 
/// Event argument class for InputPressed and InputReleased events 
/// </summary> 
public class MotionControllerEventArgs : EventArgs 
{ 
    public MotionControllerEventArgs(Handedness handedness, bool isPressed, rollerInput input, DateTime inputTime) 
    { 
        this.Handedness = handedness; 
        this.Input = input; 
        this.InputTime = inputTime; 
        this.IsPressed = isPressed; 
    } 

    /// <summary> 
    /// Handedness of the controller raising the event 
    /// </summary> 
    public Handedness Handedness { get; private set; } 

    /// <summary> 
    /// Button pressed or released 
    /// </summary> 
    public ControllerInput Input { get; private set; } 

    /// <summary> 
    /// Time of the event 
    /// </summary> 
    public DateTime InputTime { get; private set; } 

    /// <summary> 
    /// true if button is pressed, false otherwise 
    /// </summary> 
    public bool IsPressed { get; private set; } 
} 

/// <summary> 
/// Event raised when a button is pressed 
/// </summary> 
public event EventHandler<MotionControllerEventArgs> InputPressed; 

/// <summary> 
/// Event raised when a button is released 
/// </summary> 
public event EventHandler<MotionControllerEventArgs> InputReleased; 

/// <summary> 
/// Updates the input states of the known motion controllers 
/// </summary> 
public void Update() 
{ 
    // If some event handler has been registered, we need to process all states  
    // since the last update, to avoid missing a quick press / release 
    if ((InputPressed != null) || (InputReleased != null)) 
    { 
        List<MotionControllerEventArgs> events = new <MotionControllerEventArgs>(); 

        lock (_controllers) 
        { 
            foreach (var controller in _controllers) 
            { 
                events.AddRange(controller.Value.GetNextEvents()); 
            } 
        } 
 
        // Sort the events by time 
        events.Sort((e1, e2) => DateTime.Compare(e1.InputTime, e2.InputTime)); 

        foreach (MotionControllerEventArgs evt in events) 
        { 
            if (evt.IsPressed && (InputPressed != null)) 
            { 
                InputPressed(this, evt); 
            } 
            else if (!evt.IsPressed && (InputReleased != null)) 
            { 
                InputReleased(this, evt); 
            } 
        } 
    } 
    else 
    { 
        // As we do not predict button presses and the timestamp of the next e is in the future 
        // DateTime.Now is correct in this context as it will return the latest e of controllers 
        // which is the best we have at the moment for the frame. 
        var now = DateTime.Now; 
        lock (_controllers) 
        { 
            foreach (var controller in _controllers) 
            { 
                controller.Value.Update(now); 
            } 
        } 
    } 
} 
```

La struttura degli esempi di codice precedente rende la registrazione degli eventi molto più leggibile: 

```csharp
public InteractionSourceHandedness handedness; 
public Microsoft.MixedReality.Input.ControllerInput redButton;

// Start of the Mono Behavior: register handlers for events from cache 
void Start() 
{ 
    var stateCache = gameObject.GetComponent<MotionControllerStateCache>(); 
    stateCache.InputPressed += stateCache_InputPressed; 
    stateCache.InputReleased += stateCache_InputReleased; 
    … 
} 

// Called when a button is released 
private void stateCache_InputReleased(object sender, MotionControllerStateCache.MotionControllerEventArgs e) 
{ 
    if ((e.SourceHandedness == handedness) && (e.Input == redButton)) 
    { 
        … 
    } 
} 

// Called when a button is pressed 
private void stateCache_InputPressed(object sender, MotionControllerStateCache.MotionControllerEventArgs e) 
{ 
    if ((e.SourceHandedness == handedness) && (e.Input == redButton)) 
    { 
        … 
    } 
} 
```

## <a name="see-also"></a>Vedere anche

<!-- ## Getting started

There's no additional setup required to use the HP Reverb G2 controller if you're developing for SteamVR or using the Windows Mixed Reality Input API (XR.WSA.Input). However, the A, B, X, Y buttons and the squeeze trigger are not currently accessible through the Input Manager unless you're using SteamVR. Support for the extra Reverb G2 inputs will be available in the near future, so be sure to check back!

## Porting existing applications

If you already have an existing app that you're developing for Windows Mixed Reality immersive headsets, check out our [porting guide](../porting-apps/porting-guides.md) and [project settings](https://docs.microsoft.com/windows/mixed-reality/develop/porting-apps/porting-guides?tabs=project#unity-porting-guidance) sections for general suggestions.

## Mapping input

When you're ready to get your input mapping up and running for your new controllers, start at the [input mapping](https://docs.microsoft.com/windows/mixed-reality/develop/porting-apps/porting-guides?tabs=input#unity-porting-guidance) section of the immersive porting guide. Instructions on how to configure inputs in Unity is detailed in [Gestures and motion controllers](gestures-and-motion-controllers-in-unity.md), along with a full [button and axis mapping table](gestures-and-motion-controllers-in-unity.md#using-hp-reverb-g2-controllers) for reference.

## See also
* [Updating for SteamVR](../porting-apps/updating-your-steamvr-application-for-windows-mixed-reality.md) -->
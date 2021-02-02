---
title: Controller di HP Reverb G2 in Unity
description: Informazioni su come configurare e usare i nuovi controller di HP reverbi G2 in SteamVR e Windows Mixed Reality Unity.
author: hferrone
ms.author: v-hferrone
ms.date: 10/14/2020
ms.topic: article
keywords: Unity, Reverb, Reverb G2, HP reverbi G2, realtà mista, sviluppo, controller di movimento, input utente, funzionalità, nuovo progetto, emulatore, documentazione, guide, funzionalità, ologrammi, sviluppo di giochi
ms.openlocfilehash: 26435ef57c9baf59b1008fb4750aedd913a19814
ms.sourcegitcommit: 1304f8f0a838290c1ae3db34670b67c75ea9bdaa
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/02/2021
ms.locfileid: "99421395"
---
# <a name="hp-reverb-g2-controllers-in-unity"></a><span data-ttu-id="16f29-104">Controller di HP Reverb G2 in Unity</span><span class="sxs-lookup"><span data-stu-id="16f29-104">HP Reverb G2 Controllers in Unity</span></span>

<span data-ttu-id="16f29-105">I controller di movimento HP sono un nuovo tipo di controller di realtà mista di Windows: tutte le stesse tecnologie di rilevamento con un set leggermente diverso di input disponibili:</span><span class="sxs-lookup"><span data-stu-id="16f29-105">HP Motion controllers are a brand new type of Windows Mixed Reality controllers: all the same tracking technology with a slightly different set of available inputs:</span></span> 

* <span data-ttu-id="16f29-106">Touchpad è stato sostituito da due pulsanti: A e B per il controller destro e X e Y per il controller sinistro.</span><span class="sxs-lookup"><span data-stu-id="16f29-106">Touchpad has been replaced by two buttons: A and B for the right controller, and X and Y for the left controller.</span></span> 
* <span data-ttu-id="16f29-107">La funzione di comprensione è ora un trigger che pubblica un flusso di valori compreso tra 0,0 e 1,0 anziché un pulsante con gli stati premuto e non premuto.</span><span class="sxs-lookup"><span data-stu-id="16f29-107">Grasp is now a trigger that publishes a stream of values between 0.0 and 1.0 instead of a button with Pressed and Not Pressed states.</span></span> 

<span data-ttu-id="16f29-108">Poiché i nuovi input non sono accessibili tramite le API Windows e Unity esistenti, è necessario il pacchetto di **Microsoft. MixedReality. input** .</span><span class="sxs-lookup"><span data-stu-id="16f29-108">Since the new inputs aren't accessible through existing Windows and Unity APIs, you need the dedicated **Microsoft.MixedReality.Input** UPM Package.</span></span> 

> [!IMPORTANT]
> <span data-ttu-id="16f29-109">**Le classi in questo pacchetto non sostituiscono le API Windows e Unity esistenti, ma le completano.**</span><span class="sxs-lookup"><span data-stu-id="16f29-109">**Classes in this package do not replace existing Windows and Unity APIs but complement them.**</span></span> <span data-ttu-id="16f29-110">Le funzionalità disponibili in genere per i controller di realtà misto di Windows classico e i controller di movimento HP sono accessibili tramite lo stesso percorso di codice usando le API esistenti.</span><span class="sxs-lookup"><span data-stu-id="16f29-110">Features commonly available to both classic Windows Mixed Reality controllers and HP Motion Controllers are accessible through the same code path using existing APIs.</span></span> <span data-ttu-id="16f29-111">Solo i nuovi input richiedono l'uso del pacchetto Microsoft. MixedReality. input aggiuntivo.</span><span class="sxs-lookup"><span data-stu-id="16f29-111">Only the new inputs require the use of the additional Microsoft.MixedReality.Input package.</span></span> 

## <a name="hp-motion-controller-overview"></a><span data-ttu-id="16f29-112">Panoramica di HP Motion controller</span><span class="sxs-lookup"><span data-stu-id="16f29-112">HP Motion Controller overview</span></span>

<span data-ttu-id="16f29-113">*Microsoft. MixedReality. input. MotionController* rappresenta un controller di movimento.</span><span class="sxs-lookup"><span data-stu-id="16f29-113">*Microsoft.MixedReality.Input.MotionController* represents a motion controller.</span></span> <span data-ttu-id="16f29-114">Ogni istanza di *MotionController* dispone di una *XR. WSA. Input. InteractionSource* peer, che può essere correlato tramite la manualità, l'ID del fornitore, l'ID prodotto e la versione.</span><span class="sxs-lookup"><span data-stu-id="16f29-114">Each *MotionController* instance has an *XR.WSA.Input.InteractionSource* peer, which can be correlated using handedness, vendor ID, product ID, and version.</span></span> 

<span data-ttu-id="16f29-115">È possibile recuperare le istanze di MotionController creando un *MotionControllerWatcher* e sottoscrivendo gli eventi, in modo analogo all'uso di eventi *InteractionManager* per individuare nuove istanze di *InteractionSource* .</span><span class="sxs-lookup"><span data-stu-id="16f29-115">You can grab MotionController instances by creating a *MotionControllerWatcher* and subscribing to its events, similar to using *InteractionManager* events to discover new *InteractionSource* instances.</span></span> <span data-ttu-id="16f29-116">I metodi e le proprietà di MotionController descrivono gli input supportati dal controller, inclusi i pulsanti, i trigger, l'asse 2D e levetta.</span><span class="sxs-lookup"><span data-stu-id="16f29-116">The MotionController’s methods and properties describe the inputs supported by the controller, including its buttons, triggers, 2D axis, and thumbstick.</span></span> <span data-ttu-id="16f29-117">La classe MotionController espone inoltre metodi per l'accesso agli Stati di input tramite la classe *MotionControllerReading* .</span><span class="sxs-lookup"><span data-stu-id="16f29-117">The MotionController class also exposes methods for accessing input states through the *MotionControllerReading* class.</span></span> <span data-ttu-id="16f29-118">La classe MotionControllerReading rappresenta uno snapshot dello stato del controller in un determinato momento.</span><span class="sxs-lookup"><span data-stu-id="16f29-118">The MotionControllerReading class represents a snapshot of the controller’s state at a given time.</span></span> 

## <a name="installing-microsoftmixedrealityinput-with-the-mixed-reality-feature-tool"></a><span data-ttu-id="16f29-119">Installazione di Microsoft. MixedReality. input con lo strumento della funzionalità di realtà mista</span><span class="sxs-lookup"><span data-stu-id="16f29-119">Installing Microsoft.MixedReality.Input with the Mixed Reality Feature Tool</span></span>

<span data-ttu-id="16f29-120">Installare il plug-in Microsoft. MixedReality. input con la nuova applicazione dello strumento per la funzionalità di realtà mista.</span><span class="sxs-lookup"><span data-stu-id="16f29-120">Install the Microsoft.MixedReality.Input plugin with the new Mixed Reality Feature Tool application.</span></span> <span data-ttu-id="16f29-121">Seguire le [istruzioni di installazione e utilizzo](welcome-to-mr-feature-tool.md) e selezionare il pacchetto di input per la **realtà mista** nella categoria del Toolkit di realtà mista:</span><span class="sxs-lookup"><span data-stu-id="16f29-121">Follow the [installation and usage instructions](welcome-to-mr-feature-tool.md) and select the **Mixed Reality Input** package in the Mixed Reality Toolkit category:</span></span>

![Finestra pacchetti di strumenti per la realtà mista con input realtà misto evidenziato](images/feature-tool-mrinput.png)

## <a name="using-microsoftmixedrealityinput"></a><span data-ttu-id="16f29-123">Uso di Microsoft. MixedReality. input</span><span class="sxs-lookup"><span data-stu-id="16f29-123">Using Microsoft.MixedReality.Input</span></span> 

### <a name="input-values"></a><span data-ttu-id="16f29-124">Valori di input</span><span class="sxs-lookup"><span data-stu-id="16f29-124">Input values</span></span>

<span data-ttu-id="16f29-125">Un MotionController può esporre due tipi di input:</span><span class="sxs-lookup"><span data-stu-id="16f29-125">A MotionController can expose two kinds of inputs:</span></span> 

* <span data-ttu-id="16f29-126">I pulsanti e gli Stati dei trigger sono espressi da un valore float univoco compreso tra 0,0 e 1,0 che indica la quantità di pressione selezionata.</span><span class="sxs-lookup"><span data-stu-id="16f29-126">Buttons and trigger states are expressed by a unique float value between 0.0 and 1.0 that indicates how much they're pressed.</span></span>
    * <span data-ttu-id="16f29-127">Un pulsante può restituire solo 0,0 (se non premuto) o 1,0 (quando premuto) mentre un trigger può restituire valori continui compresi tra 0,0 (completamente rilasciato) e 1,0 (completamente premuto).</span><span class="sxs-lookup"><span data-stu-id="16f29-127">A button can only return 0.0 (when not pressed) or 1.0 (when pressed) while a trigger can return continuous values between 0.0 (fully released) to 1.0 (fully pressed).</span></span> 
* <span data-ttu-id="16f29-128">Lo stato levetta è espresso da un valore Vector2 i cui componenti X e Y sono compresi tra-1,0 e 1,0.</span><span class="sxs-lookup"><span data-stu-id="16f29-128">Thumbstick state is expressed by a Vector2 whose X and Y components are between -1.0 and 1.0.</span></span> 

<span data-ttu-id="16f29-129">È possibile usare *MotionController. GetPressableInputs ()* per restituire un elenco di input che restituiscono un valore premuto (pulsanti e trigger) o il metodo *MotionController. GetXYInputs ()* per restituire un elenco di input che restituiscono un valore di 2 assi.</span><span class="sxs-lookup"><span data-stu-id="16f29-129">You can use *MotionController.GetPressableInputs()* to return a list of inputs returning a pressed value (buttons and triggers) or the *MotionController.GetXYInputs()* method to return a list of inputs returning a 2-axis value.</span></span> 

<span data-ttu-id="16f29-130">Un'istanza di MotionControllerReading rappresenta lo stato del controller in un determinato momento:</span><span class="sxs-lookup"><span data-stu-id="16f29-130">A MotionControllerReading instance represents the state of the controller at a given time:</span></span> 

* <span data-ttu-id="16f29-131">*GetPressedValue ()* recupera lo stato di un pulsante o di un trigger.</span><span class="sxs-lookup"><span data-stu-id="16f29-131">*GetPressedValue()* retrieves the state of a button or a trigger.</span></span> 
* <span data-ttu-id="16f29-132">*GetXYValue ()* recupera lo stato di un levetta.</span><span class="sxs-lookup"><span data-stu-id="16f29-132">*GetXYValue()* retrieves the state of a thumbstick.</span></span> 

### <a name="creating-a-cache-to-maintain-a-collection-of-motioncontroller-instances-and-their-states"></a><span data-ttu-id="16f29-133">Creazione di una cache per la gestione di una raccolta di istanze di MotionController e dei relativi stati</span><span class="sxs-lookup"><span data-stu-id="16f29-133">Creating a cache to maintain a collection of MotionController instances and their states</span></span> 

<span data-ttu-id="16f29-134">Iniziare creando un'istanza di MotionControllerWatcher e registrando i gestori per i relativi eventi *MotionControllerAdded* e *MotionControllerRemoved* per memorizzare una cache di istanze MotionController disponibili.</span><span class="sxs-lookup"><span data-stu-id="16f29-134">Start by instantiating a MotionControllerWatcher and registering handlers for its *MotionControllerAdded* and *MotionControllerRemoved* events to keep a cache of available MotionController instances.</span></span> <span data-ttu-id="16f29-135">Questa cache deve essere un monocomportamento associato a un GameObject, come illustrato nel codice seguente:</span><span class="sxs-lookup"><span data-stu-id="16f29-135">This cache should be a MonoBehavior attached to a GameObject as demonstrated in the following code:</span></span>

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

### <a name="reading-new-inputs-by-polling"></a><span data-ttu-id="16f29-136">Lettura di nuovi input tramite polling</span><span class="sxs-lookup"><span data-stu-id="16f29-136">Reading new inputs by polling</span></span> 

<span data-ttu-id="16f29-137">È possibile leggere lo stato corrente di ogni controller noto tramite *MotionController. TryGetReadingAtTime* durante il metodo *Update* della classe monobehavior.</span><span class="sxs-lookup"><span data-stu-id="16f29-137">You can read the current state of each known controller through *MotionController.TryGetReadingAtTime* during the *Update* method of the MonoBehavior class.</span></span> <span data-ttu-id="16f29-138">Si desidera passare *DateTime. Now* come parametro timestamp per assicurarsi che venga letto lo stato più recente del controller.</span><span class="sxs-lookup"><span data-stu-id="16f29-138">You want to pass *DateTime.Now* as the timestamp parameter to ensure that the latest state of the controller is read.</span></span> 

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

<span data-ttu-id="16f29-139">È possibile acquisire il valore di input corrente dei controller usando la manualità del controller:</span><span class="sxs-lookup"><span data-stu-id="16f29-139">You can grab the controllers current input value using the Handedness of the controller:</span></span> 

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

<span data-ttu-id="16f29-140">Ad esempio, per leggere il valore di stretta analogo di un InteractionSource:</span><span class="sxs-lookup"><span data-stu-id="16f29-140">For example, to read the analog grasp value of an InteractionSource:</span></span> 

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

### <a name="generating-events-from-the-new-inputs"></a><span data-ttu-id="16f29-141">Generazione di eventi dai nuovi input</span><span class="sxs-lookup"><span data-stu-id="16f29-141">Generating events from the new inputs</span></span> 

<span data-ttu-id="16f29-142">Anziché eseguire il polling dello stato di un controller una volta per ogni fotogramma, è possibile scegliere di gestire tutte le modifiche di stato come eventi, consentendo di gestire anche le azioni più veloci che durano meno di un frame.</span><span class="sxs-lookup"><span data-stu-id="16f29-142">Instead of polling for a controller's state once per frame, you have the option of handling all state changes as events, which lets you handle even the quickest actions lasting less than a frame.</span></span> <span data-ttu-id="16f29-143">Per il corretto funzionamento di questo approccio, è necessario che la cache dei controller di movimento elabori tutti gli stati pubblicati da un controller dall'ultimo frame. a tale scopo, è possibile archiviare il timestamp dell'ultimo MotionControllerReading recuperato da un MotionController e chiamare *MotionController. TryGetReadingAfterTime ()*:</span><span class="sxs-lookup"><span data-stu-id="16f29-143">In order for this approach to work, the cache of motion controllers needs to process all states published by a controller since the last frame, which you can do by storing the timestamp of the last MotionControllerReading retrieved from a MotionController and calling *MotionController.TryGetReadingAfterTime()*:</span></span> 

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

<span data-ttu-id="16f29-144">A questo punto, dopo aver aggiornato le classi interne della cache, la classe monobehavior può esporre due eventi, premuti e rilasciati, e generarli dal metodo Update ():</span><span class="sxs-lookup"><span data-stu-id="16f29-144">Now that you've updated the cache internal classes, the MonoBehavior class can expose two events – Pressed and Released – and raise them from its Update() method:</span></span> 

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

<span data-ttu-id="16f29-145">La struttura degli esempi di codice precedente rende la registrazione degli eventi molto più leggibile:</span><span class="sxs-lookup"><span data-stu-id="16f29-145">The structure in the above code examples makes registering events much more readable:</span></span> 

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

## <a name="see-also"></a><span data-ttu-id="16f29-146">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="16f29-146">See also</span></span>

<!-- ## Getting started

There's no additional setup required to use the HP Reverb G2 controller if you're developing for SteamVR or using the Windows Mixed Reality Input API (XR.WSA.Input). However, the A, B, X, Y buttons and the squeeze trigger are not currently accessible through the Input Manager unless you're using SteamVR. Support for the extra Reverb G2 inputs will be available in the near future, so be sure to check back!

## Porting existing applications

If you already have an existing app that you're developing for Windows Mixed Reality immersive headsets, check out our [porting guide](../porting-apps/porting-guides.md) and [project settings](../porting-apps/porting-guides.md?tabs=project#unity-porting-guidance) sections for general suggestions.

## Mapping input

When you're ready to get your input mapping up and running for your new controllers, start at the [input mapping](../porting-apps/porting-guides.md?tabs=input#unity-porting-guidance) section of the immersive porting guide. Instructions on how to configure inputs in Unity is detailed in [Gestures and motion controllers](gestures-and-motion-controllers-in-unity.md), along with a full [button and axis mapping table](gestures-and-motion-controllers-in-unity.md#using-hp-reverb-g2-controllers) for reference.

## See also
* [Updating for SteamVR](../porting-apps/updating-your-steamvr-application-for-windows-mixed-reality.md) -->
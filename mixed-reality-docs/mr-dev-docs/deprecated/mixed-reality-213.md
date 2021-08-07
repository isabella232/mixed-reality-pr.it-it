---
title: Input MR 213
description: Seguire questa esercitazione sulla codifica con Unity, Visual Studio visori immersivi e visori immersivi per apprendere i dettagli dei controller di movimento.
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit-unity, immersive, motion controller, academy, tutorial
ms.openlocfilehash: 1cb53ed619a978e2aef17b5006b6254e5c7d3b9f53a39fbcb5932ebcc44ca98b
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115210226"
---
# <a name="mr-input-213-motion-controllers"></a>Input MR 213: Controller del movimento

>[!NOTE]
>Le esercitazioni di Mixed Reality Academy sono state progettate in base a HoloLens (prima generazione) e ai visori VR immersive di realtà mista.  Pertanto, riteniamo importante lasciarle a disposizione degli sviluppatori a cui serve ancora materiale sussidiario per lo sviluppo di questi dispositivi.  Queste esercitazioni **_non_** verranno aggiornate con i set di strumenti o le interazioni più recenti usati per HoloLens 2.  Rimarranno invariate per consentire di continuare a lavorare sui dispositivi supportati. Per HoloLens 2 è stata pubblicata [una nuova serie di esercitazioni](../develop/unity/tutorials/mr-learning-base-01.md).

I controller di movimento nel mondo della realtà mista aggiungono un altro livello di interattività. Con [i controller](../design/motion-controllers.md)di movimento è possibile interagire direttamente con gli oggetti in modo più naturale, in modo simile alle interazioni fisiche nella vita reale, aumentando l'esperienza dell'app.

In MR Input 213 verranno esaminati gli eventi di input del controller di movimento creando una semplice esperienza di disegno spaziale. Con questa app, gli utenti possono disegnare in uno spazio tridimensionale con vari tipi di pennelli e colori.

## <a name="topics-covered-in-this-tutorial"></a>Argomenti trattati in questa esercitazione

|![MixedReality213 Topic1](images/mr213-topic1.png)|![MixedReality213 Topic2](images/mr213-topic2.png)|![Argomento MixedReality2133](images/mr213-topic3.png)|
| :--- | :--- | :--- |
|**Visualizzazione del controller**|**Eventi di input del controller**|**Controller personalizzato e interfaccia utente**|
|Informazioni su come eseguire il rendering dei modelli di controller del movimento in modalità di gioco e runtime di Unity.|Informazioni sui diversi tipi di eventi pulsante e sulle relative applicazioni.|Informazioni su come sovrapporre gli elementi dell'interfaccia utente al controller o personalizzarlo completamente.|

## <a name="device-support"></a>Supporto di dispositivi

<table>
<tr>
<th>Corso</th><th style="width:150px"> <a href="/hololens/hololens1-hardware">HoloLens</a></th><th style="width:150px"> <a href="../discover/immersive-headset-hardware-details.md">Visori VR immersive</a></th>
</tr><tr>
<td>Input MR 213: Controller del movimento</td><td style="text-align: center;"> </td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="before-you-start"></a>Prima di iniziare

### <a name="prerequisites"></a>Prerequisiti

Vedere l'elenco di controllo per l'installazione di visori immersivi [in questa pagina.](../develop/install-the-tools.md)

* Questa esercitazione richiede [Unity 2017.2.1p2](https://beta.unity3d.com/download/1dc514532f08/UnityDownloadAssistant-2017.2.1p2.exe)

### <a name="project-files"></a>File di progetto

* [Scaricare i file](https://github.com/Microsoft/MixedReality213/archive/master.zip) richiesti dal progetto ed estrarre i file nel desktop.

>[!NOTE]
>Se si vuole esaminare il codice sorgente prima del download, è disponibile in GitHub [.](https://github.com/Microsoft/MixedReality213)

## <a name="unity-setup"></a>Installazione di Unity

>[!VIDEO https://www.youtube.com/embed/cBAOALaHys4]

### <a name="objectives"></a>Obiettivi

* Ottimizzare Unity per Windows Mixed Reality sviluppo
* Configurare Fotocamera realtà mista
* Configurare l'ambiente

### <a name="instructions"></a>Istruzioni

* Riavviare Unity.
* Selezionare **Open** (Apri).
* Passare al desktop e trovare la **cartella MixedReality213-master** precedentemente nonarchiviata.
* Fare clic su **Seleziona cartella**.
* Al termine del caricamento dei file di progetto, Unity sarà in grado di visualizzare l'editor di Unity.
* In Unity selezionare **File > build Impostazioni**.

    ![MR213_BuildSettings](images/mr213-buildsettings-450px.png)

* Selezionare **Universal Windows Platform** nell'elenco **Piattaforma** e fare clic sul pulsante **Cambia** piattaforma.
* Impostare Dispositivo di destinazione su **Qualsiasi dispositivo**
* Impostare Tipo di compilazione su **D3D**
* Impostare SDK su **Più recente installato**
* Controllare **i progetti C# di Unity**
    * In questo modo è possibile modificare i file di script nel Visual Studio progetto senza ricompilare il progetto Unity.
* Fare **clic su Player Impostazioni**.
* Nel pannello **Controllo** scorrere verso il basso fino alla fine
* In XR Impostazioni, selezionare **Virtual Reality Supported (Realtà virtuale supportata)**
* In SDK di realtà virtuale **selezionare** Windows Mixed Reality

    ![MR213_XRSettings](images/mr213-xrsettings-500px.png)

* Chiudere **la finestra Impostazioni** compilazione.

### <a name="project-structure"></a>Struttura del progetto

Questa esercitazione usa **[Mixed Reality Toolkit - Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity)**. Le versioni sono disponibili in [questa pagina.](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases)

![ProjectStructure](images/mr213-projectstructure-650px.png)

**Scene completate per il riferimento**

* Nella cartella Scenes sono  disponibili due scene unity completate.
    * **MixedReality213:** scena completata con un singolo pennello
    * **MixedReality213Advanced:** scena completata per la progettazione avanzata con più pennelli

**Nuova configurazione della scena per l'esercitazione**

* In Unity fare clic **su File > Nuova scena**
* Eliminare **la fotocamera principale** e la luce **direzionale**
* Dal pannello **Project ,** cercare e trascinare i prefab seguenti nel pannello **Gerarchia:**
    * Assets/HoloToolkit/Input/Prefabs/**MixedRealityCamera**
    * Asset/AppPrefabs/Ambiente

    ![Fotocamera e ambiente](images/mr213-cameraenvironment-300px.jpg)

* In Realtà mista sono disponibili due prefab Toolkit:
    * **MixedRealityCamera.prefab:** solo fotocamera
    * **MixedRealityCameraParent.prefab:** Fotocamera + Teletrasporto + Limite
    * In questa esercitazione si userà **MixedRealityCamera senza** funzionalità di teletrasporto. Per questo motivo, è stato aggiunto **un** semplice prefab ambiente che contiene un piano di base per far sentire l'utente a terra.
    * Per altre informazioni sul teletrasporto **con MixedRealityCameraParent,** vedere [Progettazione avanzata - Teletrasporto e locomozione](#advanced-design---teleportation-and-locomotion)

**Configurazione di Skybox**

* Fare **clic su Finestra > illuminazione > Impostazioni**
* Fare clic sul cerchio a destra del **campo Skybox Material**
* Digitare "gray" e selezionare **SkyboxGray** (Assets/AppPrefabs/Support/Materials/SkyboxGray.mat)

    ![Impostazione di skybox](images/mr123-skyboxsetting-400px.jpg)

* Selezionare **l'opzione Skybox** per visualizzare il skybox con sfumatura grigia assegnata

    ![Attivare/disattivare l'opzione skybox](images/mr213-skyboxcheck-400px.jpg)

* La scena con MixedRealityCamera, Environment e skybox grigio sarà simile alla seguente.

    ![Ambiente MixedReality213](images/mr213-environment-600px.jpg)

* Fare **clic su File > Salva scena con nome**
* **Salvare** la scena nella cartella Scenes con qualsiasi nome

## <a name="chapter-1---controller-visualization"></a>Capitolo 1 - Visualizzazione del controller

>[!VIDEO https://www.youtube.com/embed/Kw0bf5NqyRg]

### <a name="objectives"></a>Obiettivi

* Informazioni su come eseguire il rendering dei modelli di controller di movimento in modalità di gioco di Unity e in fase di esecuzione.

Windows Mixed Reality un modello di controller animato per la visualizzazione del controller. Esistono diversi approcci che è possibile adottare per la visualizzazione del controller nell'app:

* Impostazione predefinita: uso del controller predefinito senza modifiche
* Ibrido: uso del controller predefinito, ma personalizzazione di alcuni elementi o sovrapposizione dei componenti dell'interfaccia utente
* Sostituzione: uso del proprio modello 3D personalizzato per il controller

In questo capitolo verranno illustrati gli esempi di queste personalizzazioni del controller.

### <a name="instructions"></a>Istruzioni

* Nel pannello **Project,** digitare **MotionControllers** nella casella di ricerca . È anche possibile trovarlo in Assets/HoloToolkit/Input/Prefabs/.
* Trascinare il prefab **MotionControllers** nel **pannello Gerarchia.**
* Fare clic sul prefab **MotionControllers** nel **pannello Gerarchia.**

**Prefab MotionControllers**

Il prefab **MotionControllers** ha uno script **MotionControllerVisualizer** che fornisce gli slot per i modelli di controller alternativi. Se si assegnano modelli 3D personalizzati, ad esempio una mano o una freccia e si seleziona "Usa sempre un modello di sinistra/destra alternativo", verranno visualizzati al posto del modello predefinito. Questo slot verrà utilizzato nel capitolo 4 per sostituire il modello di controller con un pennello.

![MR213_ControllerVisualizer](images/mr213-controllervisualizer-600px.png)

**Istruzioni**

* Nel pannello **Controllo** fare doppio clic su **MotionControllerVisualizer** script per visualizzare il codice nel Visual Studio

**Script MotionControllerVisualizer**

Le **classi MotionControllerVisualizer** **e MotionControllerInfo** forniscono i mezzi per accedere & modificare i modelli di controller predefiniti. **MotionControllerVisualizer** sottoscrive l'evento **InteractionSourceDetected** di Unity e crea automaticamente un'istanza dei modelli controller quando vengono trovati.

```cs
protected override void Awake()
{
    ...
    InteractionManager.InteractionSourceDetected += InteractionManager_InteractionSourceDetected;
    InteractionManager.InteractionSourceLost += InteractionManager_InteractionSourceLost;
    ...
}
```

I modelli di controller vengono recapitati in base [alla specifica glTF](https://github.com/KhronosGroup/glTF). Questo formato è stato creato per fornire un formato comune, migliorando al tempo stesso il processo di trasmissione e decompressione degli asset 3D. In questo caso, è necessario recuperare e caricare i modelli di controller in fase di esecuzione, in quanto si vuole rendere più semplice possibile l'esperienza dell'utente e non è garantita la versione dei controller di movimento che l'utente potrebbe usare. Questo corso, tramite Toolkit realtà mista, usa una versione del progetto [UnityGLTF](https://github.com/KhronosGroup/UnityGLTF)del gruppo Khronos.

Dopo che il controller è stato recapitato, gli script possono usare **MotionControllerInfo** per trovare le trasformazioni per elementi controller specifici in modo che possano posizionarsi correttamente.

In un capitolo successivo si apprenderà come usare questi script per collegare gli elementi dell'interfaccia utente ai controller.

*In alcuni script sono presenti blocchi di codice **con #if ! UNITY_EDITOR** o **UNITY_WSA**. Questi blocchi di codice vengono eseguiti solo nel runtime UWP quando si esegue la distribuzione in Windows. Questo perché il set di API usate dall'editor di Unity e dal runtime dell'app UWP è diverso.*

* **Salvare** la scena e fare clic sul **pulsante di** riproduzione.

Sarà possibile visualizzare la scena con controller di movimento nel visore. È possibile visualizzare animazioni dettagliate per i clic sui pulsanti, lo spostamento della levetta e l'evidenziazione del tocco del touchpad.

![MR213_Controller visualizzazione predefinita](images/mr213-controllervisualizationdefault-500px.jpg)

## <a name="chapter-2---attaching-ui-elements-to-the-controller"></a>Capitolo 2 - Collegamento di elementi dell'interfaccia utente al controller

>[!VIDEO https://www.youtube.com/embed/e-mLlwmTzJo]

### <a name="objectives"></a>Obiettivi

* Informazioni sugli elementi dei controller di movimento
* Informazioni su come associare oggetti a parti specifiche dei controller

In questo capitolo si apprenderà come aggiungere elementi dell'interfaccia utente al controller a cui l'utente può accedere e modificare facilmente in qualsiasi momento. Si apprenderà anche come aggiungere un'interfaccia utente di selezione colori semplice usando l'input del touchpad.

### <a name="instructions"></a>Istruzioni

* Nel pannello **Project** ricerca dello script **MotionControllerInfo.**
* Nel risultato della ricerca fare doppio clic su **Script MotionControllerInfo** per visualizzare il codice in Visual Studio.

**Script MotionControllerInfo**

Il primo passaggio consiste nel scegliere l'elemento del controller a cui associare l'interfaccia utente. Questi elementi sono definiti in **ControllerElementEnum** in **MotionControllerInfo.cs**.

![MR213 MotionControllerElements](images/mr213-motioncontrollerelements-1000px.jpg)

* **Home**
* **Menu**
* **Afferrare**
* **Levetta personale**
* **Select**
* **Touchpad**
* **Posizione di puntamento:** questo elemento rappresenta la punta del controller che punta in avanti.

**Istruzioni**

* Nel pannello **Project** ricerca dello script **AttachToController.**
* Nel risultato della ricerca fare doppio clic su **Script AttachToController** per visualizzare il codice in Visual Studio.

**Script AttachToController**

Lo script **AttachToController** fornisce un modo semplice per associare qualsiasi oggetto a un elemento e a una mano del controller specificati.

In **AttachElementToController()**,

* Controllare la mano usando **MotionControllerInfo.Handedness**
* Ottenere un elemento specifico del controller **usando MotionControllerInfo.TryGetElement()**
* Dopo il recupero della trasformazione dell'elemento dal modello controller, padre dell'oggetto sotto di esso e impostare la posizione locale dell'oggetto & rotazione su zero.

```cs
public MotionControllerInfo.ControllerElementEnum Element { get { return element; } }

private void AttachElementToController(MotionControllerInfo newController)
{
     if (!IsAttached && newController.Handedness == handedness)
     {
          if (!newController.TryGetElement(element, out elementTransform))
          {
               Debug.LogError("Unable to find element of type &quot; + element + &quot; under controller &quot; + newController.ControllerParent.name + &quot;; not attaching.");
               return;
          }

          controller = newController;

          SetChildrenActive(true);

          // Parent ourselves under the element and set our offsets
          transform.parent = elementTransform;
          transform.localPosition = positionOffset;
          transform.localEulerAngles = rotationOffset;
          if (setScaleOnAttach)
          {
               transform.localScale = scale;
          }

          // Announce that we're attached
          OnAttachToController();
          IsAttached = true;
     }
}
```

Il modo più semplice per usare lo script **AttachToController** è ereditare da esso, come è stato fatto nel caso di **ColorPickerWheel.** È sufficiente eseguire **l'override delle funzioni OnAttachToController** e **OnDetachFromController** per eseguire la configurazione/scomposizione quando il controller viene rilevato/disconnesso.

**Istruzioni**

* Nel pannello **Project** digitare nella casella di ricerca **ColorPickerWheel**. È anche possibile trovarlo in Assets/AppPrefabs/.
* Trascinare il prefab **ColorPickerWheel** nel **pannello Gerarchia.**
* Fare clic sul prefab **ColorPickerWheel** nel **pannello Gerarchia.**
* Nel pannello **Controllo** fare doppio clic **su ColorPickerWheel** Script per visualizzare il codice in Visual Studio.

![Prefab ColorPickerWheel](images/mr213-colorpickerwheel-1000px.jpg)

**Script ColorPickerWheel**

Poiché **ColorPickerWheel** eredita **AttachToController,** mostra **Handedness** e **Element** nel **pannello Inspector.** L'interfaccia utente verrà collegata all'elemento Touchpad nel controller di sinistra.

![Script ColorPickerWheel](images/mr213-attachtocontroller-300px.jpg)

**ColorPickerWheel** esegue l'override di **OnAttachToController** e **OnDetachFromController** per sottoscrivere l'evento di input che verrà usato nel capitolo successivo per la selezione dei colori con l'input del touchpad.

```cs
public class ColorPickerWheel : AttachToController, IPointerTarget
{
    protected override void OnAttachToController()
    {
        // Subscribe to input now that we're parented under the controller
        InteractionManager.InteractionSourceUpdated += InteractionSourceUpdated;
    }

    protected override void OnDetachFromController()
    {
        Visible = false;

        // Unsubscribe from input now that we've detached from the controller
        InteractionManager.InteractionSourceUpdated -= InteractionSourceUpdated;
    }
    ...
}
```

* **Salvare** la scena e fare clic sul **pulsante di** riproduzione.

**Metodo alternativo per collegare oggetti ai controller**

È consigliabile che gli script ereditino **da AttachToController** ed eseere **l'override di OnAttachToController**. Tuttavia, questo potrebbe non essere sempre possibile. Un'alternativa consiste nell'usarlo come componente autonomo. Ciò può essere utile quando si vuole collegare un prefab esistente a un controller senza eseguire il refactoring degli script. È sufficiente che la classe attenda che IsAttached sia impostato su true prima di eseguire qualsiasi configurazione. Il modo più semplice per eseguire questa operazione è usare una coroutine per 'Start'.

```cs
private IEnumerator Start() {
    AttachToController attach = gameObject.GetComponent<AttachToController>();

    while (!attach.IsAttached) {
        yield return null;
    }

    // Perform setup here
}
```

## <a name="chapter-3---working-with-touchpad-input"></a>Capitolo 3 - Uso dell'input del touchpad

>[!VIDEO https://www.youtube.com/embed/SUyw0kxZPFw]

### <a name="objectives"></a>Obiettivi

* Informazioni su come ottenere eventi di dati di input touchpad
* Informazioni su come usare le informazioni sulla posizione dell'asse del touchpad per l'esperienza dell'app

### <a name="instructions"></a>Istruzioni

* Nel pannello **Gerarchia** fare clic **su ColorPickerWheel**
* Nel pannello **Inspector (Controllo)** in **Animator (Animatore)** fare doppio clic **su ColorPickerWheelController**
* Sarà possibile visualizzare la scheda **Animator** aperta

**Visualizzazione/nascondere l'interfaccia utente con il controller di animazione di Unity**

Per mostrare e nascondere **l'interfaccia utente colorPickerWheel** con l'animazione, viene utilizzato il sistema [di animazione di Unity.](https://docs.unity3d.com/Manual/AnimationOverview.html) L'impostazione della proprietà **Visible** di **ColorPickerWheel** su  true o false attiva i trigger di animazione **Mostra** e Nascondi. **I** parametri **Show e Hide** sono definiti nel controller di **animazione ColorPickerWheelController.**

![Controller di animazione Unity](images/mr123-animationcontroller-550px.jpg)

**Istruzioni**

* Nel pannello **Gerarchia** selezionare **ColorPickerWheel** prefab
* Nel pannello **Controllo** fare doppio clic **su ColorPickerWheel** script per visualizzare il codice nel Visual Studio

**Script ColorPickerWheel**

**ColorPickerWheel** sottoscrive l'evento **InteractionSourceUpdated** di Unity per restare in ascolto degli eventi del touchpad.

In **InteractionSourceUpdated()** lo script verifica innanzitutto che:

* è in realtà un evento touchpad (obj.state.**touchpadTouched**)
* ha origine dal controller di sinistra (obj.state.source.**handedness**)

Se entrambi sono true, la posizione del touchpad (obj.state.**touchpadPosition**) viene assegnato a **selectorPosition**.

```cs
private void InteractionSourceUpdated(InteractionSourceUpdatedEventArgs obj)
{
    if (obj.state.source.handedness == handedness && obj.state.touchpadTouched)
    {
        Visible = true;
        selectorPosition = obj.state.touchpadPosition;
    }
}
```

In **Update()**, in base alla **proprietà visible,** attiva i trigger di animazione Mostra e Nascondi nel componente animatore del selettore colori

```cs
if (visible != visibleLastFrame)
{
    if (visible)
    {
        animator.SetTrigger("Show");
    }
    else
    {
        animator.SetTrigger("Hide");
    }
}
```

In **Update()** **selectorPosition** viene usato per eseguire il cast di un raggio sul collisore mesh della ruota dei colori, che restituisce una posizione UV. Questa posizione può quindi essere usata per trovare la coordinata pixel e il valore del colore della trama della ruota dei colori. Questo valore è accessibile ad altri script tramite la **proprietà SelectedColor.**

![Selezione colori Wheel Raycasting](images/mr213-colorpickerwheel-raycast-700px.png)

```cs
...
    // Clamp selector position to a radius of 1
    Vector3 localPosition = new Vector3(selectorPosition.x * inputScale, 0.15f, selectorPosition.y * inputScale);
    if (localPosition.magnitude > 1)
    {
        localPosition = localPosition.normalized;
    }
    selectorTransform.localPosition = localPosition;

    // Raycast the wheel mesh and get its UV coordinates
    Vector3 raycastStart = selectorTransform.position + selectorTransform.up * 0.15f;
    RaycastHit hit;
    Debug.DrawLine(raycastStart, raycastStart - (selectorTransform.up * 0.25f));

    if (Physics.Raycast(raycastStart, -selectorTransform.up, out hit, 0.25f, 1 << colorWheelObject.layer, QueryTriggerInteraction.Ignore))
    {
        // Get pixel from the color wheel texture using UV coordinates
        Vector2 uv = hit.textureCoord;
        int pixelX = Mathf.FloorToInt(colorWheelTexture.width * uv.x);
        int pixelY = Mathf.FloorToInt(colorWheelTexture.height * uv.y);
        selectedColor = colorWheelTexture.GetPixel(pixelX, pixelY);
        selectedColor.a = 1f;
    }
    // Set the selector's color and blend it with white to make it visible on top of the wheel
    selectorRenderer.material.color = Color.Lerp (selectedColor, Color.white, 0.5f);
}
```

## <a name="chapter-4---overriding-controller-model"></a>Capitolo 4 - Override del modello di controller

>[!VIDEO https://www.youtube.com/embed/8gBFqA_DZ_U]

### <a name="objectives"></a>Obiettivi

* Informazioni su come eseguire l'override del modello di controller con un modello 3D personalizzato.

![MR213_BrushToolOverride](images/mr213-brushtooloverride-500px.jpg)

### <a name="instructions"></a>Istruzioni

* Fare **clic su MotionControllers** nel **pannello Hierarchy (Gerarchia).**
* Fare clic sul cerchio a destra del **campo Alternate Right Controller (Controller destro** alternativo).
* Digitare **'BrushController'** e selezionare il prefab dal risultato. È possibile trovarlo in Assets/AppPrefabs/**BrushController**.
* Selezionare **Usa sempre il modello a destra alternativo**

![MR213_BrushToolOverrideSlot](images/mr213-motioncontrollersoverride-700px.jpg)

Il prefab **BrushController** non deve essere incluso nel **pannello Gerarchia.** Tuttavia, per estrarre i componenti figlio:

* Nel pannello **Project,** digitare **BrushController** e trascinare il prefab **BrushController** nel **pannello Gerarchia.**

![MR213_BrushTool_Prefab2](images/mr213-brushtool-prefab-1000px.jpg)

Il componente Tip è **disponibile** in **BrushController.** La trasformazione verrà utilizzata per avviare/arrestare il disegno delle linee.

* Eliminare **BrushController** dal pannello **Gerarchia.**
* **Salvare** la scena e fare clic sul **pulsante di** riproduzione. Sarà possibile vedere che il modello di pennello ha sostituito il controller di movimento a destra.

## <a name="chapter-5---painting-with-select-input"></a>Capitolo 5 - Disegno con Selezione input

>[!VIDEO https://www.youtube.com/embed/QTrYaMHIs7w]

### <a name="objectives"></a>Obiettivi

* Informazioni su come usare l'evento Del pulsante Seleziona per avviare e arrestare un disegno linea

### <a name="instructions"></a>Istruzioni

* Cercare il prefab **BrushController** **nel pannello Project** precedente.
* Nel pannello **Controllo** fare doppio clic su **BrushController** Script per visualizzare il codice in Visual Studio

**Script BrushController**

**BrushController** sottoscrive gli eventi **InteractionSourcePressed** e **InteractionSourceReleased di InteractionManager.** Quando **viene attivato l'evento InteractionSourcePressed,** la proprietà **Draw** del pennello viene impostata su true; quando **viene attivato l'evento InteractionSourceReleased,** la proprietà **Draw** del pennello è impostata su false.

```cs
private void InteractionSourcePressed(InteractionSourcePressedEventArgs obj)
{
    if (obj.state.source.handedness == InteractionSourceHandedness.Right && obj.pressType == InteractionSourcePressType.Select)
    {
        Draw = true;
    }
}

private void InteractionSourceReleased(InteractionSourceReleasedEventArgs obj)
{
    if (obj.state.source.handedness == InteractionSourceHandedness.Right && obj.pressType == InteractionSourcePressType.Select)
    {
        Draw = false;
    }
}
```

Mentre **Draw** è impostato su true, il pennello genererà punti in un oggetto **LineRenderer** Unity di cui è stata creata un'istanza. Un riferimento a questo prefab viene mantenuto nel campo **Prefab tratto del** pennello.

```cs
private IEnumerator DrawOverTime()
{
    // Get the position of the tip
    Vector3 lastPointPosition = tip.position;

    ...

    // Create a new brush stroke
    GameObject newStroke = Instantiate(strokePrefab);
    LineRenderer line = newStroke.GetComponent<LineRenderer>();
    newStroke.transform.position = startPosition;
    line.SetPosition(0, tip.position);
    float initialWidth = line.widthMultiplier;

    // Generate points in an instantiated Unity LineRenderer
    while (draw)
    {
        // Move the last point to the draw point position
        line.SetPosition(line.positionCount - 1, tip.position);
        line.material.color = colorPicker.SelectedColor;
        brushRenderer.material.color = colorPicker.SelectedColor;
        lastPointAddedTime = Time.unscaledTime;
        // Adjust the width between 1x and 2x width based on strength of trigger pull
        line.widthMultiplier = Mathf.Lerp(initialWidth, initialWidth * 2, width);

        if (Vector3.Distance(lastPointPosition, tip.position) > minPositionDelta || Time.unscaledTime > lastPointAddedTime + maxTimeDelta)
        {
            // Spawn a new point
            lastPointAddedTime = Time.unscaledTime;
            lastPointPosition = tip.position;
            line.positionCount += 1;
            line.SetPosition(line.positionCount - 1, lastPointPosition);
        }
        yield return null;
    }
}
```

Per usare il colore attualmente selezionato dall'interfaccia utente della rotellina del selettore colori, **BrushController** deve avere un riferimento **all'oggetto ColorPickerWheel.** Poiché viene **creata un'istanza** del prefab BrushController in fase di esecuzione come controller sostitutivo, tutti i riferimenti agli oggetti nella scena devono essere impostati in fase di esecuzione. In questo caso si usa **GameObject.FindObjectOfType** per individuare **ColorPickerWheel:**

```cs
private void OnEnable()
{
    // Locate the ColorPickerWheel
    colorPicker = FindObjectOfType<ColorPickerWheel>();

    // Assign currently selected color to the brush’s material color
    brushRenderer.material.color = colorPicker.SelectedColor;
    ...
}
```

* **Salvare** la scena e fare clic sul **pulsante di** riproduzione. Sarà possibile disegnare le linee e disegnare usando il pulsante seleziona sul controller di destra.

## <a name="chapter-6---object-spawning-with-select-input"></a>Capitolo 6 - Generazione di oggetti con Selezione input

>[!VIDEO https://www.youtube.com/embed/z4IxyzFHP0U]

### <a name="objectives"></a>Obiettivi

* Informazioni su come usare gli eventi di input del pulsante Seleziona e afferra
* Informazioni su come creare un'istanza di oggetti

### <a name="instructions"></a>Istruzioni

* Nel pannello **Project** digitare **ObjectSpawner** nella casella di ricerca. È anche possibile trovarlo in Assets/AppPrefabs/
* Trascinare il prefab **ObjectSpawner** nel **pannello Gerarchia.**
* Fare **clic su ObjectSpawner** nel **pannello Gerarchia.**
* **ObjectSpawner** ha un campo denominato **Origine colore**.
* Dal pannello **Gerarchia** trascinare il **riferimento ColorPickerWheel** in questo campo.

    ![Controllo spawner di oggetti](images/mr213-objectspawnercolorpickerwheel-650px.jpg)

* Fare clic sul prefab **ObjectSpawner** nel **pannello Gerarchia.**
* Nel pannello **Inspector** (Controllo) fare doppio clic su ObjectSpawner Script (Script **ObjectSpawner)** per visualizzare il codice in Visual Studio.

**Script ObjectSpawner**

**ObjectSpawner crea** un'istanza di copie di una mesh primitiva (cubo, sfera, cilindro) nello spazio. Quando viene **rilevato un oggetto InteractionSourcePressed,** controlla la mano e se si tratta di un evento **InteractionSourcePressType.Grasp** o **InteractionSourcePressType.Select.**

Per un **evento Grasp,** incrementa l'indice del tipo di mesh corrente (sphere, cube, cylinder)

```cs
private void InteractionSourcePressed(InteractionSourcePressedEventArgs obj)
{
    // Check handedness, see if it is left controller
    if (obj.state.source.handedness == handedness)
    {
        switch (obj.pressType)
        {
            // If it is Select button event, spawn object
            case InteractionSourcePressType.Select:
                if (state == StateEnum.Idle)
                {
                    // We've pressed the grasp - enter spawning state
                    state = StateEnum.Spawning;
                    SpawnObject();
                }
                break;

            // If it is Grasp button event
            case InteractionSourcePressType.Grasp:

                // Increment the index of current mesh type (sphere, cube, cylinder)
                meshIndex++;
                if (meshIndex >= NumAvailableMeshes)
                {
                    meshIndex = 0;
                }
                break;

            default:
                break;
        }
    }
}
```

Per un **evento Select,** in **SpawnObject()** viene creata un'istanza di un nuovo oggetto, non padre e rilasciato nel mondo.

```cs
private void SpawnObject()
{
    // Instantiate the spawned object
    GameObject newObject = Instantiate(displayObject.gameObject, spawnParent);
    // Detach the newly spawned object
    newObject.transform.parent = null;
    // Reset the scale transform to 1
    scaleParent.localScale = Vector3.one;
    // Set its material color so its material gets instantiated
    newObject.GetComponent<Renderer>().material.color = colorSource.SelectedColor;
}
```

**ObjectSpawner** usa **ColorPickerWheel** per impostare il colore del materiale dell'oggetto di visualizzazione. Agli oggetti generati viene data un'istanza di questo materiale in modo che mantenino il colore.

* **Salvare** la scena e fare clic sul **pulsante di** riproduzione.

Sarà possibile modificare gli oggetti con il pulsante Afferra e generare oggetti con il pulsante Seleziona.

## <a name="build-and-deploy-app-to-mixed-reality-portal"></a>Compilare e distribuire un'app Portale realtà mista

* In Unity selezionare **File > build Impostazioni**.
* Fare **clic su Aggiungi scene aperte** per aggiungere la scena corrente a Scene in **compilazione**.
* Fare clic su **Compila**.
* Creare una **nuova cartella** denominata "App".
* Fare clic sulla **cartella App.**
* Fare clic su **Seleziona cartella**.
* Al termine di Unity, viene visualizzata Esplora file finestra di dialogo.
* Aprire la **cartella App.**
* Fare doppio **clic su YourSceneName.sln Visual Studio** file della soluzione.
* Usando la barra degli strumenti superiore Visual Studio, modificare la destinazione da Debug a **Versione** e da ARM a **X64.**
* Fare clic sulla freccia a discesa accanto al pulsante Dispositivo e selezionare **Computer locale**.
* Fare **clic su Debug -> Avvia** senza eseguire debug nel menu o premere **CTRL+F5.**

L'app viene ora compilata e installata in Portale realtà mista. È possibile avviarlo di nuovo tramite menu Start in Portale realtà mista.

## <a name="advanced-design---brush-tools-with-radial-layout"></a>Progettazione avanzata - Strumenti pennello con layout radiale

![MixedReality213 Main](images/mr213-main-600px.jpg)

In questo capitolo si apprenderà come sostituire il modello di controller di movimento predefinito con una raccolta di strumenti pennello personalizzata. Per riferimento, è possibile trovare la scena completata **MixedReality213Advanced nella** **cartella Scenes.**

### <a name="instructions"></a>Istruzioni

* Nel pannello **Project** digitare **BrushSelector** nella casella di ricerca . È anche possibile trovarlo in Assets/AppPrefabs/
* Trascinare il prefab **BrushSelector** nel **pannello Gerarchia.**
* Per l'organizzazione, creare un GameObject vuoto denominato **Brushes**
* Trascinare i prefab seguenti **dal pannello Project** in **Pennelli**
    * Assets/AppPrefabs/BrushFat
    * Asset/AppPrefabs/BrushThin
    * Asset/AppPrefabs/Gomma
    * Assets/AppPrefabs/MarkerFat
    * Assets/AppPrefabs/MarkerThin
    * Asset/AppPrefabs/Pencil

    ![Pennelli](images/mixedreality213-brushes-250px.png)

* Fare clic sul prefab **MotionControllers** nel **pannello Gerarchia.**
* Nel pannello **Inspector** (Controllo) deselezionare **Always Use Alternate Right Model** (Usa sempre modello a destra alternativo) nel **visualizzatore del controller di movimento**
* Nel pannello **Gerarchia** fare clic **su BrushSelector**
* **BrushSelector** ha un campo denominato **ColorPicker**
* Dal pannello Hierarchy (Gerarchia) trascina **ColorPickerWheel** **nel campo ColorPicker** nel pannello **Inspector (Controllo).** 

    ![Assegnare ColorPickerWheel al selettore pennello](images/mr213-brushselector-500px.jpg)

* Nel pannello **Hierarchy (Gerarchia)** in BrushSelector prefab (Prefab **BrushSelector)** selezionare **l'oggetto Menu.**
* Nel pannello **Inspector (Controllo),** sotto il **componente LineObjectCollection,** apri l'elenco a discesa Objects array **(Matrice** di oggetti). Verranno visualizzati 6 slot vuoti.
* Dal pannello **Hierarchy (Gerarchia)** trascina ognuno dei prefab padre sotto **Brushes** GameObject (GameObject pennelli) in questi slot in qualsiasi ordine. Assicurarsi di trascinare i prefab dalla scena, non i prefab nella cartella del progetto.

![Selettore pennello](images/mr213-brushselectorbrushes-700px.jpg)

**Prefab BrushSelector**

Poiché **BrushSelector** eredita **AttachToController,** nel pannello **Inspector** vengono visualizzate le opzioni **Handedness** ed **Element.** Sono stati selezionati **Right (Destra)** **e Pointing Pose (Posizione di puntamento)** per collegare gli strumenti del pennello al controller della mano destra con direzione avanti.

**BrushSelector usa** due utilità:

* **Ellisse**: usata per generare punti nello spazio lungo una forma ellisse.
* **LineObjectCollection:** distribuisce gli oggetti usando i punti generati da qualsiasi classe Line (ad esempio Ellipse). Questo è ciò che verrà utilizzato per posizionare i pennelli lungo la forma Ellipse.

Se combinate, queste utilità possono essere usate per creare un menu radiale.

**Script LineObjectCollection**

**LineObjectCollection include** controlli per le dimensioni, la posizione e la rotazione degli oggetti distribuiti lungo la linea. Ciò è utile per la creazione di menu radiali come il selettore del pennello. Per creare l'aspetto dei pennelli che si adattano da nessuna parte quando si avvicinano alla posizione al centro selezionata, la curva **ObjectScale** raggiunge il picco al centro e conica ai bordi.

**Script BrushSelector**

Nel caso di **BrushSelector**, si è scelto di usare l'animazione procedurale. In primo luogo, i modelli di pennello vengono distribuiti in un'ellisse dallo script **LineObjectCollection.** Ogni pennello è quindi responsabile del mantenimento della propria posizione nella mano dell'utente in base al valore **DisplayMode,** che cambia in base alla selezione. È stato scelto un approccio procedurale a causa dell'elevata probabilità che le transizioni di posizione del pennello vengano interrotte quando l'utente seleziona i pennelli. Le animazioni Mecanim possono gestire correttamente le interruzioni, ma tendono a essere più complesse rispetto a una semplice operazione Lerp.

**BrushSelector** usa una combinazione di entrambi. Quando viene rilevato l'input del touchpad, le opzioni del pennello diventano visibili e vengono ridimensionate lungo il menu radiale. Dopo un periodo di timeout (che indica che l'utente ha effettuato una selezione), le opzioni del pennello vengono nuovamente ridimensionate, lasciando solo il pennello selezionato.

**Visualizzazione dell'input del touchpad**

Anche nei casi in cui il modello controller è stato completamente sostituito, può essere utile visualizzare l'input sugli input del modello originale. Ciò consente di impostare le azioni dell'utente nella realtà. Per **BrushSelector** abbiamo scelto di rendere il touchpad brevemente visibile quando viene ricevuto l'input. Questa operazione è stata eseguita recuperando l'elemento Touchpad dal controller, sostituendone il materiale con un materiale personalizzato, quindi applicando una sfumatura al colore del materiale in base all'ultimo input del touchpad ricevuto.

```cs
protected override void OnAttachToController()
{
    // Turn off the default controller's renderers
    controller.SetRenderersVisible(false);

    // Get the touchpad and assign our custom material to it
    Transform touchpad;
    if (controller.TryGetElement(MotionControllerInfo.ControllerElementEnum.Touchpad, out touchpad))
    {
        touchpadRenderer = touchpad.GetComponentInChildren<MeshRenderer>();
        originalTouchpadMaterial = touchpadRenderer.material;
        touchpadRenderer.material = touchpadMaterial;
        touchpadRenderer.enabled = true;
    }

    // Subscribe to input now that we're parented under the controller
    InteractionManager.InteractionSourceUpdated += InteractionSourceUpdated;
}

private void Update()
{
    ...
    // Update our touchpad material
    Color glowColor = touchpadColor.Evaluate((Time.unscaledTime - touchpadTouchTime) / touchpadGlowLossTime);
    touchpadMaterial.SetColor("_EmissionColor", glowColor);
    touchpadMaterial.SetColor("_Color", glowColor);
    ...
}
```

**Selezione dello strumento pennello con input del touchpad**

Quando il selettore del pennello rileva l'input premuto del touchpad, controlla la posizione dell'input per determinare se era a sinistra o a destra.

**Spessore del tratto con selectPressedAmount**

Invece **dell'evento InteractionSourcePressType.Select** in **InteractionSourcePressed(),** puoi ottenere il valore analogo della quantità premuta tramite **selectPressedAmount.** Questo valore può essere recuperato in **InteractionSourceUpdated().**

```cs
private void InteractionSourceUpdated(InteractionSourceUpdatedEventArgs obj)
{
    if (obj.state.source.handedness == handedness)
    {
        if (obj.state.touchpadPressed)
        {
            // Check which side we clicked
            if (obj.state.touchpadPosition.x < 0)
            {
                currentAction = SwipeEnum.Left;
            }
            else
            {
                currentAction = SwipeEnum.Right;
            }

            // Ping the touchpad material so it gets bright
            touchpadTouchTime = Time.unscaledTime;
        }

        if (activeBrush != null)
        {
            // If the pressed amount is greater than our threshold, draw
            if (obj.state.selectPressedAmount >= selectPressedDrawThreshold)
            {
                activeBrush.Draw = true;
                activeBrush.Width = ProcessSelectPressedAmount(obj.state.selectPressedAmount);
            }
            else
            {
                // Otherwise, stop drawing
                activeBrush.Draw = false;
                selectPressedSmooth = 0f;
            }
        }
    }
}
```

**Script di cancellazione**

**Eraser è** un tipo speciale di pennello che esegue **l'override** della funzione **DrawOverTime()** del pennello di base. Mentre Draw è true, la gomma controlla se la punta si interseca con i tratti del pennello esistenti. In caso contrario, vengono aggiunti a una coda per essere ridotti ed eliminati.

## <a name="advanced-design---teleportation-and-locomotion"></a>Progettazione avanzata - Teletrasporto e locomozione

Se vuoi consentire all'utente di spostarsi nella scena con il teletrasporto usando la levetta, usa **MixedRealityCameraParent** invece di **MixedRealityCamera.** È anche necessario aggiungere **InputManager** e **DefaultCursor**. Poiché **MixedRealityCameraParent** include già **MotionControllers** e **Boundary** come componenti figlio, è necessario rimuovere i prefab **MotionController e** **Environment** esistenti.

### <a name="instructions"></a>Istruzioni

* Nel pannello **Hierarchy (Gerarchia)** eliminare **MixedRealityCamera**, **Environment** e **MotionControllers**
* Dal pannello **Project ,** cercare e trascinare i prefab seguenti nel pannello **Hierarchy (Gerarchia):**
    * Assets/AppPrefabs/Input/Prefabs/**MixedRealityCameraParent**
    * Assets/AppPrefabs/Input/Prefabs/**InputManager**
    * Assets/AppPrefabs/Input/Prefabs/Cursor/**DefaultCursor**

    ![Fotocamera realtà mista padre](images/mr213-cameraparent-300px.png)

* Nel pannello **Hierarchy (Gerarchia)** fare clic **su Input Manager (Gestione input).**
* Nel pannello **Inspector (Controllo)** scorrere verso il basso fino **alla sezione Simple Single Pointer Selector (Selettore di puntatore singolo** semplice)
* Dal pannello **Hierarchy (Gerarchia)** **trascinare DefaultCursor** nel **campo Cursore**

    ![Assegnazione di DefaultCursor](images/mr213-defaultcursor-500px.png)

* **Salvare** la scena e fare clic sul **pulsante di** riproduzione. Sarà possibile usare la levetta per ruotare verso sinistra/destra o il teletrasporto.

## <a name="the-end"></a>La fine

Questa è la fine di questa esercitazione. Sono stati appresi i concetti seguenti:

* Come usare i modelli di controller del movimento nella modalità di gioco e nel runtime di Unity.
* Come usare diversi tipi di eventi pulsante e le relative applicazioni.
* Come sovrapporre gli elementi dell'interfaccia utente al controller o personalizzarlo completamente.

A questo punto è possibile iniziare a creare un'esperienza immersiva personalizzata con i controller del movimento.

## <a name="completed-scenes"></a>Scene completate

* Nel pannello **di** Project di Unity fare clic sulla **cartella Scenes.**
* Sono disponibili due scene di Unity **MixedReality213** e **MixedReality213Avanzate.**
    * **MixedReality213:** scena completata con pennello singolo
    * **MixedReality213Avanzata:** scena completata con più pennelli con esempio di quantità di pressione del pulsante seleziona

## <a name="see-also"></a>Vedi anche

* [File di progetto input MR 213](https://github.com/Microsoft/MixedReality213)
* [Realtà mista Toolkit - Scena di test del controller del movimento](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/Input/Scenes)
* [Realtà mista Toolkit - Meccanismi di cattura](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/MotionControllers-GrabMechanics)
* [Linee guida per lo sviluppo di controller del movimento](../design/motion-controllers.md)
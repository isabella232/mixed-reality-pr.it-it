---
title: InputSimulationServices
description: Documentazione sul servizio di simulazione di input in MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: e77b5e6bf67e44abef024ad67dc3a82bc7eea0b1
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/03/2021
ms.locfileid: "101781951"
---
# <a name="input-simulation-service"></a><span data-ttu-id="06795-104">Servizio di simulazione di input</span><span class="sxs-lookup"><span data-stu-id="06795-104">Input simulation service</span></span>

<span data-ttu-id="06795-105">Il servizio simulazione input emula il comportamento di dispositivi e piattaforme che potrebbero non essere disponibili nell'editor di Unity.</span><span class="sxs-lookup"><span data-stu-id="06795-105">The Input Simulation Service emulates the behavior of devices and platforms that may not be available in the Unity editor.</span></span> <span data-ttu-id="06795-106">Alcuni esempi:</span><span class="sxs-lookup"><span data-stu-id="06795-106">Examples include:</span></span>

* <span data-ttu-id="06795-107">Rilevamento Head del dispositivo HoloLens o VR</span><span class="sxs-lookup"><span data-stu-id="06795-107">HoloLens or VR device head tracking</span></span>
* <span data-ttu-id="06795-108">Movimenti della mano HoloLens</span><span class="sxs-lookup"><span data-stu-id="06795-108">HoloLens hand gestures</span></span>
* <span data-ttu-id="06795-109">HoloLens 2-rilevamento a mano articolato</span><span class="sxs-lookup"><span data-stu-id="06795-109">HoloLens 2 articulated hand tracking</span></span>
* <span data-ttu-id="06795-110">HoloLens 2 Eye Tracking</span><span class="sxs-lookup"><span data-stu-id="06795-110">HoloLens 2 eye tracking</span></span>
* <span data-ttu-id="06795-111">Controller del dispositivo VR</span><span class="sxs-lookup"><span data-stu-id="06795-111">VR device controllers</span></span>

<span data-ttu-id="06795-112">Gli utenti possono usare una combinazione di tastiera e mouse convenzionale per controllare i dispositivi simulati in fase di esecuzione.</span><span class="sxs-lookup"><span data-stu-id="06795-112">Users can use a conventional keyboard and mouse combination to control simulated devices at runtime.</span></span> <span data-ttu-id="06795-113">Questo approccio consente di testare le interazioni nell'editor di Unity senza prima eseguire la distribuzione in un dispositivo.</span><span class="sxs-lookup"><span data-stu-id="06795-113">This approach allows testing of interactions in the Unity editor without first deploying to a device.</span></span>

> [!WARNING]
> <span data-ttu-id="06795-114">Questa operazione non funziona quando si usa l'emulazione olografica XR di Unity > modalità di emulazione = "simula nell'editor".</span><span class="sxs-lookup"><span data-stu-id="06795-114">This does not work when using Unity's XR Holographic Emulation > Emulation Mode = "Simulate in Editor".</span></span> <span data-ttu-id="06795-115">La simulazione nell'editor di Unity eliminerà il controllo dalla simulazione di input di MRTK.</span><span class="sxs-lookup"><span data-stu-id="06795-115">Unity's in-editor simulation will take control away from MRTK's input simulation.</span></span> <span data-ttu-id="06795-116">Per usare il servizio simulazione input MRTK, è necessario impostare XR olografica emulazione in modalità emulazione = *"None"*</span><span class="sxs-lookup"><span data-stu-id="06795-116">In order to use the MRTK input simulation service, you will need to set XR Holographic Emulation to Emulation Mode = *"None"*</span></span>

## <a name="enabling-the-input-simulation-service"></a><span data-ttu-id="06795-117">Abilitazione del servizio di simulazione di input</span><span class="sxs-lookup"><span data-stu-id="06795-117">Enabling the input simulation service</span></span>

<span data-ttu-id="06795-118">La simulazione di input è abilitata per impostazione predefinita nei profili forniti con MRTK.</span><span class="sxs-lookup"><span data-stu-id="06795-118">Input simulation is enabled by default in the profiles that ship with MRTK.</span></span>

<span data-ttu-id="06795-119">La simulazione di input è un [servizio di realtà mista](../../architecture/mixed-reality-services.md) facoltativo, ma può essere rimosso come provider di dati nel [profilo di sistema di input](../input/input-providers.md).</span><span class="sxs-lookup"><span data-stu-id="06795-119">Input simulation is an optional [Mixed Reality service](../../architecture/mixed-reality-services.md) though and can be removed as a data provider in the [Input System profile](../input/input-providers.md).</span></span>

<span data-ttu-id="06795-120">Con la configurazione del provider di dati di sistema di input, il servizio di simulazione di input può essere configurato con quanto segue.</span><span class="sxs-lookup"><span data-stu-id="06795-120">Under the Input System Data provider configuration, the Input Simulation service can be configured with the following.</span></span>

* <span data-ttu-id="06795-121">Il **tipo** deve essere *Microsoft. MixedReality. Toolkit. input > InputSimulationService*.</span><span class="sxs-lookup"><span data-stu-id="06795-121">**Type** must be *Microsoft.MixedReality.Toolkit.Input > InputSimulationService*.</span></span>
* <span data-ttu-id="06795-122">Per impostazione predefinita, le piattaforme **supportate** includono tutte le piattaforme dell' *Editor* , poiché il servizio usa l'input della tastiera e del mouse.</span><span class="sxs-lookup"><span data-stu-id="06795-122">**Supported Platform(s)** by default includes all *Editor* platforms, since the service uses keyboard and mouse input.</span></span>

> [!NOTE]
> <span data-ttu-id="06795-123">Il servizio di simulazione di input può essere usato in altri endpoint della piattaforma, ad esempio autonomo, modificando la proprietà **piattaforme supportate** per includere le destinazioni desiderate.</span><span class="sxs-lookup"><span data-stu-id="06795-123">The Input Simulation service can be used on other platform endpoints such as standalone by changing the **Supported Platform(s)** property to include the desired targets.</span></span>
> <span data-ttu-id="06795-124">![Piattaforme supportate per la simulazione di input](../images/input-simulation/InputSimulationSupportedPlatforms.gif)</span><span class="sxs-lookup"><span data-stu-id="06795-124">![Input Simulation Supported Platforms](../images/input-simulation/InputSimulationSupportedPlatforms.gif)</span></span>

## <a name="input-simulation-tools-window"></a><span data-ttu-id="06795-125">Finestra degli strumenti di simulazione di input</span><span class="sxs-lookup"><span data-stu-id="06795-125">Input simulation tools window</span></span>

<span data-ttu-id="06795-126">Abilitare la finestra degli strumenti di simulazione di input dal menu di simulazione di input di utilità di **reality Toolkit misto**  >    >   .</span><span class="sxs-lookup"><span data-stu-id="06795-126">Enable the input simulation tools window from the  **Mixed Reality Toolkit** > **Utilities** > **Input Simulation** menu.</span></span> <span data-ttu-id="06795-127">Questa finestra consente di accedere allo stato della simulazione di input durante la modalità di riproduzione.</span><span class="sxs-lookup"><span data-stu-id="06795-127">This window provides access to the state of input simulation during play mode.</span></span>

## <a name="viewport-buttons"></a><span data-ttu-id="06795-128">Pulsanti viewport</span><span class="sxs-lookup"><span data-stu-id="06795-128">Viewport buttons</span></span>

<span data-ttu-id="06795-129">Un prefabbricato per i pulsanti nell'editor per controllare la posizione di base della mano può essere specificato nel profilo di simulazione di input sotto gli **indicatori prefabbricati**.</span><span class="sxs-lookup"><span data-stu-id="06795-129">A prefab for in-editor buttons to control basic hand placement can be specified in the input simulation profile under **Indicators Prefab**.</span></span> <span data-ttu-id="06795-130">Si tratta di un'utilità facoltativa. è possibile accedere alle stesse funzionalità nella [finestra strumenti di simulazione input](#input-simulation-tools-window).</span><span class="sxs-lookup"><span data-stu-id="06795-130">This is an optional utility, the same features can be accessed in the [input simulation tools window](#input-simulation-tools-window).</span></span>

> [!NOTE]
> <span data-ttu-id="06795-131">Gli indicatori del viewport sono disabilitati per impostazione predefinita, in quanto attualmente possono interferire con le interazioni dell'interfaccia utente di Unity.</span><span class="sxs-lookup"><span data-stu-id="06795-131">The viewport indicators are disabled by default, as they currently can sometimes interfere with Unity UI interactions.</span></span> <span data-ttu-id="06795-132">Vedere [#6106](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/6106)di problema.</span><span class="sxs-lookup"><span data-stu-id="06795-132">See issue [#6106](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/6106).</span></span> <span data-ttu-id="06795-133">Per abilitare, aggiungere la prefabbricazione InputSimulationIndicators agli **indicatori prefabbricati**.</span><span class="sxs-lookup"><span data-stu-id="06795-133">To enable, add the InputSimulationIndicators prefab to **Indicators Prefab**.</span></span>

<span data-ttu-id="06795-134">Le icone a mano mostrano lo stato delle mani simulate:</span><span class="sxs-lookup"><span data-stu-id="06795-134">Hand icons show the state of the simulated hands:</span></span>

* ![Icona della mano non rilevata](../images/input-simulation/MRTK_InputSimulation_HandIndicator_Untracked.png) <span data-ttu-id="06795-136">La mano non viene verificata.</span><span class="sxs-lookup"><span data-stu-id="06795-136">The hand is not tracking.</span></span> <span data-ttu-id="06795-137">Fare clic per abilitare la mano.</span><span class="sxs-lookup"><span data-stu-id="06795-137">Click to enable the hand.</span></span>
* <span data-ttu-id="06795-138">![Icona della mano rilevata](../images/input-simulation/MRTK_InputSimulation_HandIndicator_Tracked.png "Icona della mano rilevata") La mano viene rilevata, ma non controllata dall'utente.</span><span class="sxs-lookup"><span data-stu-id="06795-138">![Tracked hand icon](../images/input-simulation/MRTK_InputSimulation_HandIndicator_Tracked.png "Tracked hand icon") The hand is tracked, but not controlled by the user.</span></span> <span data-ttu-id="06795-139">Fare clic per nascondere la mano.</span><span class="sxs-lookup"><span data-stu-id="06795-139">Click to hide the hand.</span></span>
* <span data-ttu-id="06795-140">![Icona a mano controllata](../images/input-simulation/MRTK_InputSimulation_HandIndicator_Controlled.png "Icona a mano controllata") La mano viene rilevata e controllata dall'utente.</span><span class="sxs-lookup"><span data-stu-id="06795-140">![Controlled hand icon](../images/input-simulation/MRTK_InputSimulation_HandIndicator_Controlled.png "Controlled hand icon") The hand is tracked and controlled by the user.</span></span> <span data-ttu-id="06795-141">Fare clic per nascondere la mano.</span><span class="sxs-lookup"><span data-stu-id="06795-141">Click to hide the hand.</span></span>
* <span data-ttu-id="06795-142">![Icona di reimpostazione della mano](../images/input-simulation/MRTK_InputSimulation_HandIndicator_Reset.png "Icona di reimpostazione della mano") Fare clic per reimpostare la mano nella posizione predefinita.</span><span class="sxs-lookup"><span data-stu-id="06795-142">![Reset hand icon](../images/input-simulation/MRTK_InputSimulation_HandIndicator_Reset.png "Reset hand icon") Click to reset the hand to default position.</span></span>

## <a name="in-editor-input-simulation-cheat-sheet"></a><span data-ttu-id="06795-143">Nel foglio informativo sulla simulazione di input dell'editor</span><span class="sxs-lookup"><span data-stu-id="06795-143">In editor input simulation cheat sheet</span></span>

<span data-ttu-id="06795-144">Premere CTRL + H nella scena HandInteractionExamples per visualizzare un foglio informativo con i controlli di simulazione di input.</span><span class="sxs-lookup"><span data-stu-id="06795-144">Press Left Ctrl + H in the HandInteractionExamples scene to bring up a cheat sheet with Input simulation controls.</span></span>

![Foglio informativo sulla simulazione di input](https://user-images.githubusercontent.com/39840334/86066480-13637f00-ba27-11ea-8814-d222d548f684.gif)

## <a name="camera-control"></a><span data-ttu-id="06795-146">Controllo fotocamera</span><span class="sxs-lookup"><span data-stu-id="06795-146">Camera control</span></span>

<span data-ttu-id="06795-147">Il movimento Head può essere emulato dal servizio di simulazione input.</span><span class="sxs-lookup"><span data-stu-id="06795-147">Head movement can be emulated by the Input Simulation Service.</span></span>

### <a name="rotating-the-camera"></a><span data-ttu-id="06795-148">Rotazione della fotocamera</span><span class="sxs-lookup"><span data-stu-id="06795-148">Rotating the camera</span></span>

1. <span data-ttu-id="06795-149">Passare il puntatore sulla finestra dell'editor del viewport.</span><span class="sxs-lookup"><span data-stu-id="06795-149">Hover over the viewport editor window.</span></span>
    <span data-ttu-id="06795-150">*Potrebbe essere necessario fare clic sulla finestra per assegnargli lo stato attivo per l'input se le pressioni dei pulsanti non funzionano.*</span><span class="sxs-lookup"><span data-stu-id="06795-150">*You may need to click the window to give it input focus if button presses don't work.*</span></span>
1. <span data-ttu-id="06795-151">Premere e tenere premuto il **pulsante di ricerca del mouse** (impostazione predefinita: pulsante destro del mouse).</span><span class="sxs-lookup"><span data-stu-id="06795-151">Press and hold the **Mouse Look Button** (default: Right mouse button).</span></span>
1. <span data-ttu-id="06795-152">Spostare il mouse nella finestra del viewport per ruotare la fotocamera.</span><span class="sxs-lookup"><span data-stu-id="06795-152">Move the mouse in the viewport window to rotate the camera.</span></span>
1. <span data-ttu-id="06795-153">Utilizzare la rotellina di scorrimento per ruotare la fotocamera attorno alla direzione di visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="06795-153">Use the scroll wheel to roll the camera around the view direction.</span></span>

<span data-ttu-id="06795-154">La velocità di rotazione della fotocamera può essere configurata modificando l'impostazione della **velocità di ricerca del mouse** nel profilo di simulazione di input.</span><span class="sxs-lookup"><span data-stu-id="06795-154">Camera rotation speed can be configured by changing the **Mouse Look Speed** setting in the input simulation profile.</span></span>

<span data-ttu-id="06795-155">In alternativa, usare gli assi verticali Cerca aspetto **orizzontale** /  per ruotare la fotocamera (impostazione predefinita: controller del gioco a destra levetta).</span><span class="sxs-lookup"><span data-stu-id="06795-155">Alternatively, use the **Look Horizontal**/**Look Vertical** axes to rotate the camera (default: game controller right thumbstick).</span></span>

### <a name="moving-the-camera"></a><span data-ttu-id="06795-156">Spostamento della videocamera</span><span class="sxs-lookup"><span data-stu-id="06795-156">Moving the camera</span></span>

<span data-ttu-id="06795-157">Usare gli assi verticali sposta **orizzontali** /  per spostare la fotocamera (impostazione predefinita: chiavi WASD o controller di gioco a sinistra levetta).</span><span class="sxs-lookup"><span data-stu-id="06795-157">Use the **Move Horizontal**/**Move Vertical** axes to move the camera (default: WASD keys or game controller left thumbstick).</span></span>

<span data-ttu-id="06795-158">Gli angoli di rotazione e posizione della fotocamera possono essere impostati in modo esplicito anche nella finestra degli strumenti.</span><span class="sxs-lookup"><span data-stu-id="06795-158">Camera position and rotation angles can be set explicitly in the tools window, as well.</span></span> <span data-ttu-id="06795-159">È possibile ripristinare il valore predefinito della fotocamera utilizzando il pulsante **Reimposta** .</span><span class="sxs-lookup"><span data-stu-id="06795-159">The camera can be reset to its default using the **Reset** button.</span></span>

<iframe width="560" height="315" src="https://www.youtube.com/embed/Z7L4I1ET7GU" class="center" frameborder="0" allow="accelerometer; encrypted-media; gyroscope; picture-in-picture" allowfullscreen />

## <a name="controller-simulation"></a><span data-ttu-id="06795-160">Simulazione del controller</span><span class="sxs-lookup"><span data-stu-id="06795-160">Controller simulation</span></span>

<span data-ttu-id="06795-161">La simulazione di input supporta i dispositivi controller emulati (ad esempio, i controller di movimento e le mani).</span><span class="sxs-lookup"><span data-stu-id="06795-161">The input simulation supports emulated controller devices (i.e. motion controllers and hands).</span></span> <span data-ttu-id="06795-162">Questi controller virtuali possono interagire con qualsiasi oggetto che supporti i controller normali, ad esempio pulsanti o oggetti afferrabili.</span><span class="sxs-lookup"><span data-stu-id="06795-162">These virtual controllers can interact with any object that supports regular controllers, such as buttons or grabbable objects.</span></span>

### <a name="controller-simulation-mode"></a><span data-ttu-id="06795-163">Modalità di simulazione del controller</span><span class="sxs-lookup"><span data-stu-id="06795-163">Controller simulation mode</span></span>

<span data-ttu-id="06795-164">Nella [finestra strumenti di simulazione input](#input-simulation-tools-window) l'impostazione della **modalità di simulazione del controller predefinita** cambia tra tre modelli di input distinti.</span><span class="sxs-lookup"><span data-stu-id="06795-164">In the [input simulation tools window](#input-simulation-tools-window) the **Default Controller Simulation Mode** setting switches between three distinct input models.</span></span> <span data-ttu-id="06795-165">Questa modalità predefinita può essere impostata anche nel profilo di simulazione di input.</span><span class="sxs-lookup"><span data-stu-id="06795-165">This default mode can also be set in the input simulation profile.</span></span>

* <span data-ttu-id="06795-166">*Mano articolata*: simula un dispositivo mano completamente articolato con dati di posizione congiunta.</span><span class="sxs-lookup"><span data-stu-id="06795-166">*Articulated Hands*: Simulates a fully articulated hand device with joint position data.</span></span>

   <span data-ttu-id="06795-167">Emula il modello di interazione HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="06795-167">Emulates HoloLens 2 interaction model.</span></span>

   <span data-ttu-id="06795-168">In questa modalità le interazioni basate sul posizionamento preciso della mano o sull'uso del contatto possono essere simulate.</span><span class="sxs-lookup"><span data-stu-id="06795-168">Interactions that are based on the precise positioning of the hand or use touching can be simulated in this mode.</span></span>

* <span data-ttu-id="06795-169">*Movimenti della mano*: simula un modello a mano semplificato con tocchi aria e movimenti di base.</span><span class="sxs-lookup"><span data-stu-id="06795-169">*Hand Gestures*: Simulates a simplified hand model with air tap and basic gestures.</span></span>

   <span data-ttu-id="06795-170">Emula il [modello di interazione HoloLens](https://docs.microsoft.com/windows/mixed-reality/gestures).</span><span class="sxs-lookup"><span data-stu-id="06795-170">Emulates [HoloLens interaction model](https://docs.microsoft.com/windows/mixed-reality/gestures).</span></span>

   <span data-ttu-id="06795-171">Lo stato attivo è controllato tramite il puntatore a sguardi.</span><span class="sxs-lookup"><span data-stu-id="06795-171">Focus is controlled using the Gaze pointer.</span></span> <span data-ttu-id="06795-172">Il gesto del *rubinetto d'aria* viene usato per interagire con i pulsanti.</span><span class="sxs-lookup"><span data-stu-id="06795-172">The *Air Tap* gesture is used to interact with buttons.</span></span>

* <span data-ttu-id="06795-173">*Motion controller*: simula un controller di movimento usato con auricolari VR che funziona in modo analogo a molte interazioni con le mani articolate.</span><span class="sxs-lookup"><span data-stu-id="06795-173">*Motion Controller*: Simulates a motion controller used with VR headsets that works similarly to far interactions with Articulated Hands.</span></span>

   <span data-ttu-id="06795-174">Emula la cuffia VR con il modello di interazione dei controller.</span><span class="sxs-lookup"><span data-stu-id="06795-174">Emulates VR headset with controllers interaction model.</span></span>

   <span data-ttu-id="06795-175">I tasti trigger, Acquisisci e menu vengono simulati tramite input da tastiera e mouse.</span><span class="sxs-lookup"><span data-stu-id="06795-175">The trigger, grab and menu keys are simulated via keyboard and mouse input.</span></span>

### <a name="simulating-controller-movement"></a><span data-ttu-id="06795-176">Simulazione dello spostamento del controller</span><span class="sxs-lookup"><span data-stu-id="06795-176">Simulating controller movement</span></span>

<span data-ttu-id="06795-177">Premere e tenere premuto il **tasto di manipolazione del controller di sinistra/destra** (impostazione predefinita: spostamento a *sinistra* per il controller sinistro e *lo spazio* per il controller destro) per ottenere il controllo di uno dei controller.</span><span class="sxs-lookup"><span data-stu-id="06795-177">Press and hold the **Left/Right Controller Manipulation Key** (default: *Left Shift* for left controller and *Space* for right controller) to gain control of either controller.</span></span> <span data-ttu-id="06795-178">Mentre viene premuto il tasto di manipolazione, il controller verrà visualizzato nel viewport.</span><span class="sxs-lookup"><span data-stu-id="06795-178">While the manipulation key is pressed, the controller will appear in the viewport.</span></span> <span data-ttu-id="06795-179">Una volta rilasciata la chiave di manipolazione, i controller scompariranno dopo un **timeout di Hide del controller** breve.</span><span class="sxs-lookup"><span data-stu-id="06795-179">Once the manipulation key is released, the controllers will disappear after a short **Controller Hide Timeout**.</span></span>

<span data-ttu-id="06795-180">I controller possono essere attivati e bloccati rispetto alla fotocamera nella [finestra degli strumenti di simulazione di input](#input-simulation-tools-window) o premendo la **chiave del controller di attivazione/disattivazione** (impostazione predefinita: *T* per left e *Y* per Right).</span><span class="sxs-lookup"><span data-stu-id="06795-180">Controllers can be toggled on and frozen relative to the camera in the [input simulation tools window](#input-simulation-tools-window) or by pressing the **Toggle Left/Right Controller Key** (default: *T* for left and *Y* for right).</span></span> <span data-ttu-id="06795-181">Premere di nuovo il tasto di attivazione per nascondere di nuovo i controller.</span><span class="sxs-lookup"><span data-stu-id="06795-181">Press the toggle key again to hide the controllers again.</span></span> <span data-ttu-id="06795-182">Per modificare i controller, è necessario che venga mantenuta la **chiave di manipolazione del controller di sinistra/destra** .</span><span class="sxs-lookup"><span data-stu-id="06795-182">To manipulate the controllers, the **Left/Right Controller Manipulation Key** needs to be held.</span></span> <span data-ttu-id="06795-183">Il doppio tocco della **chiave di manipolazione del controller di sinistra/destra** può anche attivare/disattivare i controller.</span><span class="sxs-lookup"><span data-stu-id="06795-183">Double tapping the **Left/Right Controller Manipulation Key** can also toggle the controllers on/off.</span></span>

<span data-ttu-id="06795-184">Il movimento del mouse sposterà il controller nel piano di visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="06795-184">Mouse movement will move the controller in the view plane.</span></span> <span data-ttu-id="06795-185">I controller possono essere spostati in modo più o più vicino alla fotocamera usando la **rotellina del mouse**.</span><span class="sxs-lookup"><span data-stu-id="06795-185">Controllers can be moved further or closer to the camera using the **mouse wheel**.</span></span>

<span data-ttu-id="06795-186">Per ruotare i controller con il mouse, tenere premuto il tasto di **manipolazione del controller di sinistra/destra** (spostamento *a* *sinistra* o *spazio*) e il **pulsante ruota del controller** (impostazione predefinita: pulsante *sinistro CTRL* ), quindi spostare il mouse per ruotare il controller.</span><span class="sxs-lookup"><span data-stu-id="06795-186">To rotate controllers using the mouse, hold both the **Left/Right Controller Manipulation Key** (*Left Shift* or *Space*) *and* the **Controller Rotate Button** (default: *Left Ctrl* button) and then move the mouse to rotate the controller.</span></span> <span data-ttu-id="06795-187">La velocità di rotazione del controller può essere configurata modificando l'impostazione della **velocità di rotazione del controller del mouse** nel profilo di simulazione di input.</span><span class="sxs-lookup"><span data-stu-id="06795-187">Controller rotation speed can be configured by changing the **Mouse Controller Rotation Speed** setting in the input simulation profile.</span></span>

<span data-ttu-id="06795-188">È anche possibile modificare la selezione host della mano nella [finestra strumenti di simulazione input](#input-simulation-tools-window), inclusa la reimpostazione delle lancette per impostazione predefinita.</span><span class="sxs-lookup"><span data-stu-id="06795-188">All hand placement can also changed in the [input simulation tools window](#input-simulation-tools-window), including resetting hands to default.</span></span>

### <a name="additional-profile-settings"></a><span data-ttu-id="06795-189">Impostazioni del profilo aggiuntive</span><span class="sxs-lookup"><span data-stu-id="06795-189">Additional profile settings</span></span>

* <span data-ttu-id="06795-190">Il **moltiplicatore di profondità del controller** controlla la sensibilità del movimento di profondità della rotellina del mouse.</span><span class="sxs-lookup"><span data-stu-id="06795-190">**Controller Depth Multiplier** controls the sensitivity of the mouse scroll wheel depth movement.</span></span> <span data-ttu-id="06795-191">Un numero maggiore accelererà lo zoom del controller.</span><span class="sxs-lookup"><span data-stu-id="06795-191">A larger number will speed up controller zoom.</span></span>
* <span data-ttu-id="06795-192">La **distanza del controller predefinita** è la distanza iniziale dei controller dalla fotocamera.</span><span class="sxs-lookup"><span data-stu-id="06795-192">**Default Controller Distance** is the initial distance of controllers from the camera.</span></span> <span data-ttu-id="06795-193">Se si fa clic sui controller dei pulsanti di **reimpostazione** , i controller vengono posizionati a distanza.</span><span class="sxs-lookup"><span data-stu-id="06795-193">Clicking the **Reset** button controllers will also place controllers at this distance.</span></span>
* <span data-ttu-id="06795-194">La **quantità di jitter del controller** aggiunge un movimento casuale ai controller.</span><span class="sxs-lookup"><span data-stu-id="06795-194">**Controller Jitter Amount** adds random motion to controllers.</span></span> <span data-ttu-id="06795-195">Questa funzionalità può essere usata per simulare un rilevamento del controller non accurato nel dispositivo e garantire che le interazioni funzionino correttamente con l'input rumoroso.</span><span class="sxs-lookup"><span data-stu-id="06795-195">This feature can be used to simulate inaccurate controller tracking on the device, and ensure that interactions work well with noisy input.</span></span>

<iframe width="560" height="315" src="https://www.youtube.com/embed/uRYfwuqsjBQ" class="center" frameborder="0" allow="accelerometer; encrypted-media; gyroscope; picture-in-picture" allowfullscreen />

### <a name="hand-gestures"></a><span data-ttu-id="06795-196">Movimenti della mano</span><span class="sxs-lookup"><span data-stu-id="06795-196">Hand gestures</span></span>

<span data-ttu-id="06795-197">È anche possibile simulare movimenti della mano, ad esempio pizzicare, afferrare, frugare e così via.</span><span class="sxs-lookup"><span data-stu-id="06795-197">Hand gestures such as pinching, grabbing, poking, etc. can also be simulated.</span></span>

1. <span data-ttu-id="06795-198">Abilitare il controllo della mano usando il **tasto di manipolazione del controller sinistro/destro** (*spostamento a sinistra* o *spazio*)</span><span class="sxs-lookup"><span data-stu-id="06795-198">Enable hand control using the **Left/Right Controller Manipulation Key** (*Left Shift* or *Space*)</span></span>

2. <span data-ttu-id="06795-199">Durante la manipolazione, premere e tenere premuto un pulsante del mouse per eseguire un movimento di mano.</span><span class="sxs-lookup"><span data-stu-id="06795-199">While manipulating, press and hold a mouse button to perform a hand gesture.</span></span>

<span data-ttu-id="06795-200">È possibile eseguire il mapping di ognuno dei pulsanti del mouse per trasformare la forma mano in un movimento diverso usando le impostazioni di *movimento della mano sinistra/centrale/destra del mouse* .</span><span class="sxs-lookup"><span data-stu-id="06795-200">Each of the mouse buttons can be mapped to transform the hand shape into a different gesture using the *Left/Middle/Right Mouse Hand Gesture* settings.</span></span> <span data-ttu-id="06795-201">Il *gesto della mano predefinito* è la forma della mano quando non viene premuto alcun pulsante.</span><span class="sxs-lookup"><span data-stu-id="06795-201">The *Default Hand Gesture* is the shape of the hand when no button is pressed.</span></span>

> [!NOTE]
> <span data-ttu-id="06795-202">Il gesto del *pizzico* è l'unico gesto che esegue l'azione "Select" a questo punto.</span><span class="sxs-lookup"><span data-stu-id="06795-202">The *Pinch* gesture is the only gesture that performs the "Select" action at this point.</span></span>

### <a name="one-hand-manipulation"></a><span data-ttu-id="06795-203">Manipolazione a mano singola</span><span class="sxs-lookup"><span data-stu-id="06795-203">One-hand manipulation</span></span>

1. <span data-ttu-id="06795-204">Premere e tenere premuto il **tasto di manipolazione del controller di sinistra/destra** (*spostamento a sinistra* o *spazio*)</span><span class="sxs-lookup"><span data-stu-id="06795-204">Press and hold **Left/Right Controller Manipulation Key** (*Left Shift* or *Space*)</span></span>
2. <span data-ttu-id="06795-205">Punto all'oggetto</span><span class="sxs-lookup"><span data-stu-id="06795-205">Point at object</span></span>
3. <span data-ttu-id="06795-206">Premere il pulsante del mouse per pizzicare</span><span class="sxs-lookup"><span data-stu-id="06795-206">Hold mouse button to pinch</span></span>
4. <span data-ttu-id="06795-207">Usare il mouse per spostare l'oggetto</span><span class="sxs-lookup"><span data-stu-id="06795-207">Use your mouse to move the object</span></span>
5. <span data-ttu-id="06795-208">Rilasciare il pulsante del mouse per arrestare l'interazione</span><span class="sxs-lookup"><span data-stu-id="06795-208">Release the mouse button to stop interaction</span></span>

<iframe width="560" height="315" src="https://www.youtube.com/embed/rM0xaHam6wM" class="center" frameborder="0" allow="accelerometer; encrypted-media; gyroscope; picture-in-picture" allowfullscreen />

### <a name="two-hand-manipulation"></a><span data-ttu-id="06795-209">Manipolazione a due mano</span><span class="sxs-lookup"><span data-stu-id="06795-209">Two-hand manipulation</span></span>

<span data-ttu-id="06795-210">Per la modifica di oggetti con due mani allo stesso tempo, è consigliabile usare la modalità mano permanente.</span><span class="sxs-lookup"><span data-stu-id="06795-210">For manipulating objects with two hands at the same time, the persistent hand mode is recommended.</span></span>

1. <span data-ttu-id="06795-211">Premere il tasto di attivazione/disattivazione (*T/Y*) per entrambe le mani.</span><span class="sxs-lookup"><span data-stu-id="06795-211">Toggle on both hands by pressing the toggle keys (*T/Y*).</span></span>
1. <span data-ttu-id="06795-212">Modificare una mano alla volta:</span><span class="sxs-lookup"><span data-stu-id="06795-212">Manipulate one hand at a time:</span></span>
    1. <span data-ttu-id="06795-213">Mantenere lo **spazio** per controllare la mano destra</span><span class="sxs-lookup"><span data-stu-id="06795-213">Hold **Space** to control the right hand</span></span>
    1. <span data-ttu-id="06795-214">Spostare la mano nella posizione in cui si desidera ottenere l'oggetto</span><span class="sxs-lookup"><span data-stu-id="06795-214">Move the hand to where you want to grab the object</span></span>
    1. <span data-ttu-id="06795-215">Premere il **pulsante sinistro del mouse** per attivare il gesto del *pizzico* .</span><span class="sxs-lookup"><span data-stu-id="06795-215">Press the **left mouse button** to activate the *Pinch* gesture.</span></span>
    1. <span data-ttu-id="06795-216">Liberare **spazio** per arrestare il controllo della mano destra.</span><span class="sxs-lookup"><span data-stu-id="06795-216">Release **Space** to stop controlling the right hand.</span></span> <span data-ttu-id="06795-217">La mano verrà bloccata sul posto e verrà bloccata nel movimento del *pizzico* perché non è più manipolata.</span><span class="sxs-lookup"><span data-stu-id="06795-217">The hand will be frozen in place and be locked into the *Pinch* gesture since it is no longer being manipulated.</span></span>
1. <span data-ttu-id="06795-218">Ripetere il processo con l'altra parte, afferrando lo stesso oggetto in una seconda posizione.</span><span class="sxs-lookup"><span data-stu-id="06795-218">Repeat the process with the other hand, grabbing the same object in a second spot.</span></span>
1. <span data-ttu-id="06795-219">Ora che entrambe le mani stanno afferrando lo stesso oggetto, è possibile spostarle per eseguire una manipolazione a due mani.</span><span class="sxs-lookup"><span data-stu-id="06795-219">Now that both hands are grabbing the same object, you can move either of them to perform two-handed manipulation.</span></span>

<iframe width="560" height="315" src="https://www.youtube.com/embed/Qol5OFNfN14" class="center" frameborder="0" allow="accelerometer; encrypted-media; gyroscope; picture-in-picture" allowfullscreen />

### <a name="ggv-gaze-gesture-and-voice-interaction"></a><span data-ttu-id="06795-220">Interazione tra GGV (sguardi, movimenti e voce)</span><span class="sxs-lookup"><span data-stu-id="06795-220">GGV (Gaze, Gesture, and Voice) interaction</span></span>

<span data-ttu-id="06795-221">Per impostazione predefinita, l'interazione GGV è abilitata nell'editor mentre non vi sono mani articolate presenti nella scena.</span><span class="sxs-lookup"><span data-stu-id="06795-221">By default, GGV interaction is enabled in-editor while there are no articulated hands present in the scene.</span></span>

1. <span data-ttu-id="06795-222">Ruota la fotocamera per puntare il cursore sullo sguardo all'oggetto interagibile (pulsante destro del mouse)</span><span class="sxs-lookup"><span data-stu-id="06795-222">Rotate the camera to point the gaze cursor at the interactable object (right mouse button)</span></span>
1. <span data-ttu-id="06795-223">Fare clic e tenendo premuto il **pulsante sinistro del mouse** per interagire</span><span class="sxs-lookup"><span data-stu-id="06795-223">Click and hold **left mouse button** to interact</span></span>
1. <span data-ttu-id="06795-224">Ruotare nuovamente la fotocamera per modificare l'oggetto</span><span class="sxs-lookup"><span data-stu-id="06795-224">Rotate the camera again to manipulate the object</span></span>

<span data-ttu-id="06795-225">Per disattivare questa opzione, è possibile attivare o disattivare l'opzione *è abilitata per l'input Hand Free* all'interno del profilo di simulazione di input.</span><span class="sxs-lookup"><span data-stu-id="06795-225">You can turn this off by toggling the *Is Hand Free Input Enabled* option inside the Input Simulation Profile.</span></span>

<span data-ttu-id="06795-226">Inoltre, è possibile usare le mani simulate per l'interazione GGV</span><span class="sxs-lookup"><span data-stu-id="06795-226">In addition, you can use simulated hands for GGV interaction</span></span>

1. <span data-ttu-id="06795-227">Abilitare la simulazione GGV cambiando la **modalità di simulazione Hand** in *movimenti* nel [profilo di simulazione di input](#enabling-the-input-simulation-service)</span><span class="sxs-lookup"><span data-stu-id="06795-227">Enable GGV simulation by switching **Hand Simulation Mode** to *Gestures* in the [Input Simulation Profile](#enabling-the-input-simulation-service)</span></span>
1. <span data-ttu-id="06795-228">Ruota la fotocamera per puntare il cursore sullo sguardo all'oggetto interagibile (pulsante destro del mouse)</span><span class="sxs-lookup"><span data-stu-id="06795-228">Rotate the camera to point the gaze cursor at the interactable object (right mouse button)</span></span>
1. <span data-ttu-id="06795-229">Mantenere lo **spazio** per controllare la mano destra</span><span class="sxs-lookup"><span data-stu-id="06795-229">Hold **Space** to control the right hand</span></span>
1. <span data-ttu-id="06795-230">Fare clic e tenendo premuto il **pulsante sinistro del mouse** per interagire</span><span class="sxs-lookup"><span data-stu-id="06795-230">Click and hold **left mouse button** to interact</span></span>
1. <span data-ttu-id="06795-231">Usare il mouse per spostare l'oggetto</span><span class="sxs-lookup"><span data-stu-id="06795-231">Use your mouse to move the object</span></span>
1. <span data-ttu-id="06795-232">Rilasciare il pulsante del mouse per arrestare l'interazione</span><span class="sxs-lookup"><span data-stu-id="06795-232">Release the mouse button to stop interaction</span></span>

<iframe width="560" height="315" src="https://www.youtube.com/embed/6841rRMdqWw" class="center" frameborder="0" allow="accelerometer; encrypted-media; gyroscope; picture-in-picture" allowfullscreen />

### <a name="motion-controller-interaction"></a><span data-ttu-id="06795-233">Interazione del controller di movimento</span><span class="sxs-lookup"><span data-stu-id="06795-233">Motion controller interaction</span></span>

<span data-ttu-id="06795-234">I controller di movimento simulati possono essere manipolati allo stesso modo delle mani articolate.</span><span class="sxs-lookup"><span data-stu-id="06795-234">The simulated motion controllers can be manipulated the same way articulated hands are.</span></span> <span data-ttu-id="06795-235">Il modello di interazione è analogo all'interazione tra la mano articolata, mentre il trigger, il tasto di scelta rapida e i tasti di menu vengono mappati rispettivamente al *pulsante sinistro del mouse*, alla chiave *G* e *M* .</span><span class="sxs-lookup"><span data-stu-id="06795-235">The interaction model is similar to far interaction of articulated hand while the trigger, grab and menu keys are mapped to *left mouse button*, *G* and *M* key respectively.</span></span>

### <a name="eye-tracking"></a><span data-ttu-id="06795-236">Tracciamento oculare</span><span class="sxs-lookup"><span data-stu-id="06795-236">Eye tracking</span></span>

<span data-ttu-id="06795-237">È possibile abilitare la [simulazione di rilevamento degli occhi](../eye-tracking/eye-tracking-basic-setup.md#simulating-eye-tracking-in-the-unity-editor) selezionando l'opzione **simula posizione occhio** nel [Profilo simulazione di input](#enabling-the-input-simulation-service).</span><span class="sxs-lookup"><span data-stu-id="06795-237">[Eye tracking simulation](../eye-tracking/eye-tracking-basic-setup.md#simulating-eye-tracking-in-the-unity-editor) can be enabled by checking the **Simulate Eye Position** option in the [Input Simulation Profile](#enabling-the-input-simulation-service).</span></span> <span data-ttu-id="06795-238">Questo non deve essere usato con le interazioni di stile GGV o Motion controller (assicurarsi che la **modalità di simulazione del controller predefinito** sia impostata su *mano articolata*).</span><span class="sxs-lookup"><span data-stu-id="06795-238">This should not be used with GGV or motion controller style interactions (so ensure that **Default Controller Simulation Mode** is set to *Articulated Hand*).</span></span>

## <a name="see-also"></a><span data-ttu-id="06795-239">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="06795-239">See also</span></span>

* <span data-ttu-id="06795-240">[Profilo di sistema di input](../input/input-providers.md).</span><span class="sxs-lookup"><span data-stu-id="06795-240">[Input System profile](../input/input-providers.md).</span></span>

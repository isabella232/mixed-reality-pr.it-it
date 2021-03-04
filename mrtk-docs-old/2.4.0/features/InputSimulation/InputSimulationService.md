---
title: InputSimulationServices
description: Documentazione sul servizio di simulazione di input in MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: b36af476c3b7e257ee132e0e70c9aecf721a95b1
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/03/2021
ms.locfileid: "101783146"
---
# <a name="input-simulation-service"></a><span data-ttu-id="ff39e-104">Servizio di simulazione di input</span><span class="sxs-lookup"><span data-stu-id="ff39e-104">Input simulation service</span></span>

<span data-ttu-id="ff39e-105">Il servizio simulazione input emula il comportamento di dispositivi e piattaforme che potrebbero non essere disponibili nell'editor di Unity.</span><span class="sxs-lookup"><span data-stu-id="ff39e-105">The Input Simulation Service emulates the behaviour of devices and platforms that may not be available in the Unity editor.</span></span> <span data-ttu-id="ff39e-106">Alcuni esempi:</span><span class="sxs-lookup"><span data-stu-id="ff39e-106">Examples include:</span></span>

* <span data-ttu-id="ff39e-107">Rilevamento Head del dispositivo HoloLens o VR</span><span class="sxs-lookup"><span data-stu-id="ff39e-107">HoloLens or VR device head tracking</span></span>
* <span data-ttu-id="ff39e-108">Movimenti della mano HoloLens</span><span class="sxs-lookup"><span data-stu-id="ff39e-108">HoloLens hand gestures</span></span>
* <span data-ttu-id="ff39e-109">HoloLens 2-rilevamento a mano articolato</span><span class="sxs-lookup"><span data-stu-id="ff39e-109">HoloLens 2 articulated hand tracking</span></span>
* <span data-ttu-id="ff39e-110">HoloLens 2 Eye Tracking</span><span class="sxs-lookup"><span data-stu-id="ff39e-110">HoloLens 2 eye tracking</span></span>

<span data-ttu-id="ff39e-111">Gli utenti possono usare una combinazione di tastiera e mouse convenzionale per controllare i dispositivi simulati in fase di esecuzione.</span><span class="sxs-lookup"><span data-stu-id="ff39e-111">Users can use a conventional keyboard and mouse combination to control simulated devices at runtime.</span></span> <span data-ttu-id="ff39e-112">Questo approccio consente di testare le interazioni nell'editor di Unity senza prima eseguire la distribuzione in un dispositivo.</span><span class="sxs-lookup"><span data-stu-id="ff39e-112">This approach allows testing of interactions in the Unity editor without first deploying to a device.</span></span>

> [!WARNING]
> <span data-ttu-id="ff39e-113">Questa operazione non funziona quando si usa l'emulazione olografica XR di Unity > modalità di emulazione = "simula nell'editor".</span><span class="sxs-lookup"><span data-stu-id="ff39e-113">This does not work when using Unity's XR Holographic Emulation > Emulation Mode = "Simulate in Editor".</span></span> <span data-ttu-id="ff39e-114">La simulazione nell'editor di Unity eliminerà il controllo dalla simulazione di input di MRTK.</span><span class="sxs-lookup"><span data-stu-id="ff39e-114">Unity's in-editor simulation will take control away from MRTK's input simulation.</span></span> <span data-ttu-id="ff39e-115">Per usare il servizio simulazione input MRTK, è necessario impostare XR olografica emulazione in modalità emulazione = *"None"*</span><span class="sxs-lookup"><span data-stu-id="ff39e-115">In order to use the MRTK input simulation service, you will need to set XR Holographic Emulation to Emulation Mode = *"None"*</span></span>

## <a name="enabling-the-input-simulation-service"></a><span data-ttu-id="ff39e-116">Abilitazione del servizio di simulazione di input</span><span class="sxs-lookup"><span data-stu-id="ff39e-116">Enabling the input simulation service</span></span>

<span data-ttu-id="ff39e-117">La simulazione di input è abilitata per impostazione predefinita nei profili forniti con MRTK.</span><span class="sxs-lookup"><span data-stu-id="ff39e-117">Input simulation is enabled by default in the profiles that ship with MRTK.</span></span>

<span data-ttu-id="ff39e-118">La simulazione di input è un [servizio di realtà mista](../../out-of-scope/MixedRealityServices.md) facoltativo, ma può essere rimosso come provider di dati nel [profilo di sistema di input](../Input/InputProviders.md).</span><span class="sxs-lookup"><span data-stu-id="ff39e-118">Input simulation is an optional [Mixed Reality service](../../out-of-scope/MixedRealityServices.md) though and can be removed as a data provider in the [Input System profile](../Input/InputProviders.md).</span></span>

<span data-ttu-id="ff39e-119">Con la configurazione del provider di dati di sistema di input, il servizio di simulazione di input può essere configurato con quanto segue.</span><span class="sxs-lookup"><span data-stu-id="ff39e-119">Under the Input System Data provider configuration, the Input Simulation service can be configured with the following.</span></span>

* <span data-ttu-id="ff39e-120">Il **tipo** deve essere *Microsoft. MixedReality. Toolkit. input > InputSimulationService*.</span><span class="sxs-lookup"><span data-stu-id="ff39e-120">**Type** must be *Microsoft.MixedReality.Toolkit.Input > InputSimulationService*.</span></span>
* <span data-ttu-id="ff39e-121">Per impostazione predefinita, le piattaforme **supportate** includono tutte le piattaforme dell' *Editor* , poiché il servizio usa l'input della tastiera e del mouse.</span><span class="sxs-lookup"><span data-stu-id="ff39e-121">**Supported Platform(s)** by default includes all *Editor* platforms, since the service uses keyboard and mouse input.</span></span>

> [!NOTE]
> <span data-ttu-id="ff39e-122">Il servizio di simulazione di input può essere usato in altri endpoint della piattaforma, ad esempio autonomo, modificando la proprietà **piattaforme supportate** per includere le destinazioni desiderate.</span><span class="sxs-lookup"><span data-stu-id="ff39e-122">The Input Simulation service can be used on other platform endpoints such as standalone by changing the **Supported Platform(s)** property to include the desired targets.</span></span>
> <span data-ttu-id="ff39e-123">![Piattaforme supportate per la simulazione di input](../Images/InputSimulation/InputSimulationSupportedPlatforms.gif)</span><span class="sxs-lookup"><span data-stu-id="ff39e-123">![Input Simulation Supported Platforms](../Images/InputSimulation/InputSimulationSupportedPlatforms.gif)</span></span>

## <a name="input-simulation-tools-window"></a><span data-ttu-id="ff39e-124">Finestra degli strumenti di simulazione di input</span><span class="sxs-lookup"><span data-stu-id="ff39e-124">Input simulation tools window</span></span>

<span data-ttu-id="ff39e-125">Abilitare la finestra degli strumenti di simulazione di input dal menu di simulazione di input di utilità di **reality Toolkit misto**  >    >   .</span><span class="sxs-lookup"><span data-stu-id="ff39e-125">Enable the input simulation tools window from the  **Mixed Reality Toolkit** > **Utilities** > **Input Simulation** menu.</span></span> <span data-ttu-id="ff39e-126">Questa finestra consente di accedere allo stato della simulazione di input durante la modalità di riproduzione.</span><span class="sxs-lookup"><span data-stu-id="ff39e-126">This window provides access to the state of input simulation during play mode.</span></span>

## <a name="viewport-buttons"></a><span data-ttu-id="ff39e-127">Pulsanti viewport</span><span class="sxs-lookup"><span data-stu-id="ff39e-127">Viewport buttons</span></span>

<span data-ttu-id="ff39e-128">Un prefabbricato per i pulsanti nell'editor per controllare la posizione di base della mano può essere specificato nel profilo di simulazione di input sotto gli **indicatori prefabbricati**.</span><span class="sxs-lookup"><span data-stu-id="ff39e-128">A prefab for in-editor buttons to control basic hand placement can be specified in the input simulation profile under **Indicators Prefab**.</span></span> <span data-ttu-id="ff39e-129">Si tratta di un'utilità facoltativa. è possibile accedere alle stesse funzionalità nella [finestra strumenti di simulazione input](#input-simulation-tools-window).</span><span class="sxs-lookup"><span data-stu-id="ff39e-129">This is an optional utility, the same features can be accessed in the [input simulation tools window](#input-simulation-tools-window).</span></span>

> [!NOTE]
> <span data-ttu-id="ff39e-130">Gli indicatori del viewport sono disabilitati per impostazione predefinita, in quanto attualmente possono interferire con le interazioni dell'interfaccia utente di Unity.</span><span class="sxs-lookup"><span data-stu-id="ff39e-130">The viewport indicators are disabled by default, as they currently can sometimes interfere with Unity UI interactions.</span></span> <span data-ttu-id="ff39e-131">Vedere [#6106](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/6106)di problema.</span><span class="sxs-lookup"><span data-stu-id="ff39e-131">See issue [#6106](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/6106).</span></span> <span data-ttu-id="ff39e-132">Per abilitare, aggiungere la prefabbricazione InputSimulationIndicators agli **indicatori prefabbricati**.</span><span class="sxs-lookup"><span data-stu-id="ff39e-132">To enable, add the InputSimulationIndicators prefab to **Indicators Prefab**.</span></span>

<span data-ttu-id="ff39e-133">Le icone a mano mostrano lo stato delle mani simulate:</span><span class="sxs-lookup"><span data-stu-id="ff39e-133">Hand icons show the state of the simulated hands:</span></span>

* ![Icona della mano non rilevata](../Images/InputSimulation/MRTK_InputSimulation_HandIndicator_Untracked.png) <span data-ttu-id="ff39e-135">La mano non viene verificata.</span><span class="sxs-lookup"><span data-stu-id="ff39e-135">The hand is not tracking.</span></span> <span data-ttu-id="ff39e-136">Fare clic per abilitare la mano.</span><span class="sxs-lookup"><span data-stu-id="ff39e-136">Click to enable the hand.</span></span>
* <span data-ttu-id="ff39e-137">![Icona della mano rilevata](../Images/InputSimulation/MRTK_InputSimulation_HandIndicator_Tracked.png "Icona della mano rilevata") La mano viene rilevata, ma non controllata dall'utente.</span><span class="sxs-lookup"><span data-stu-id="ff39e-137">![Tracked hand icon](../Images/InputSimulation/MRTK_InputSimulation_HandIndicator_Tracked.png "Tracked hand icon") The hand is tracked, but not controlled by the user.</span></span> <span data-ttu-id="ff39e-138">Fare clic per nascondere la mano.</span><span class="sxs-lookup"><span data-stu-id="ff39e-138">Click to hide the hand.</span></span>
* <span data-ttu-id="ff39e-139">![Icona a mano controllata](../Images/InputSimulation/MRTK_InputSimulation_HandIndicator_Controlled.png "Icona a mano controllata") La mano viene rilevata e controllata dall'utente.</span><span class="sxs-lookup"><span data-stu-id="ff39e-139">![Controlled hand icon](../Images/InputSimulation/MRTK_InputSimulation_HandIndicator_Controlled.png "Controlled hand icon") The hand is tracked and controlled by the user.</span></span> <span data-ttu-id="ff39e-140">Fare clic per nascondere la mano.</span><span class="sxs-lookup"><span data-stu-id="ff39e-140">Click to hide the hand.</span></span>
* <span data-ttu-id="ff39e-141">![Icona di reimpostazione della mano](../Images/InputSimulation/MRTK_InputSimulation_HandIndicator_Reset.png "Icona di reimpostazione della mano") Fare clic per reimpostare la mano nella posizione predefinita.</span><span class="sxs-lookup"><span data-stu-id="ff39e-141">![Reset hand icon](../Images/InputSimulation/MRTK_InputSimulation_HandIndicator_Reset.png "Reset hand icon") Click to reset the hand to default position.</span></span>

## <a name="camera-control"></a><span data-ttu-id="ff39e-142">Controllo fotocamera</span><span class="sxs-lookup"><span data-stu-id="ff39e-142">Camera control</span></span>

<span data-ttu-id="ff39e-143">Il movimento Head può essere emulato dal servizio di simulazione input.</span><span class="sxs-lookup"><span data-stu-id="ff39e-143">Head movement can be emulated by the Input Simulation Service.</span></span>

### <a name="rotating-the-camera"></a><span data-ttu-id="ff39e-144">Rotazione della fotocamera</span><span class="sxs-lookup"><span data-stu-id="ff39e-144">Rotating the camera</span></span>

1. <span data-ttu-id="ff39e-145">Passare il puntatore sulla finestra dell'editor del viewport.</span><span class="sxs-lookup"><span data-stu-id="ff39e-145">Hover over the viewport editor window.</span></span>
    <span data-ttu-id="ff39e-146">*Potrebbe essere necessario fare clic sulla finestra per assegnargli lo stato attivo per l'input se le pressioni dei pulsanti non funzionano.*</span><span class="sxs-lookup"><span data-stu-id="ff39e-146">*You may need to click the window to give it input focus if button presses don't work.*</span></span>
1. <span data-ttu-id="ff39e-147">Premere e tenere premuto il **pulsante di ricerca del mouse** (impostazione predefinita: pulsante destro del mouse).</span><span class="sxs-lookup"><span data-stu-id="ff39e-147">Press and hold the **Mouse Look Button** (default: Right mouse button).</span></span>
1. <span data-ttu-id="ff39e-148">Spostare il mouse nella finestra del viewport per ruotare la fotocamera.</span><span class="sxs-lookup"><span data-stu-id="ff39e-148">Move the mouse in the viewport window to rotate the camera.</span></span>
1. <span data-ttu-id="ff39e-149">Utilizzare la rotellina di scorrimento per ruotare la fotocamera attorno alla direzione di visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="ff39e-149">Use the scroll wheel to roll the camera around the view direction.</span></span>

<span data-ttu-id="ff39e-150">La velocità di rotazione della fotocamera può essere configurata modificando l'impostazione della **velocità di ricerca del mouse** nel profilo di simulazione di input.</span><span class="sxs-lookup"><span data-stu-id="ff39e-150">Camera rotation speed can be configured by changing the **Mouse Look Speed** setting in the input simulation profile.</span></span>

<span data-ttu-id="ff39e-151">In alternativa, usare gli assi verticali Cerca aspetto **orizzontale** /  per ruotare la fotocamera (impostazione predefinita: controller del gioco a destra levetta).</span><span class="sxs-lookup"><span data-stu-id="ff39e-151">Alternatively, use the **Look Horizontal**/**Look Vertical** axes to rotate the camera (default: game controller right thumbstick).</span></span>

### <a name="moving-the-camera"></a><span data-ttu-id="ff39e-152">Spostamento della videocamera</span><span class="sxs-lookup"><span data-stu-id="ff39e-152">Moving the camera</span></span>

<span data-ttu-id="ff39e-153">Usare gli assi verticali sposta **orizzontali** /  per spostare la fotocamera (impostazione predefinita: chiavi WASD o controller di gioco a sinistra levetta).</span><span class="sxs-lookup"><span data-stu-id="ff39e-153">Use the **Move Horizontal**/**Move Vertical** axes to move the camera (default: WASD keys or game controller left thumbstick).</span></span>

<span data-ttu-id="ff39e-154">Gli angoli di rotazione e posizione della fotocamera possono essere impostati in modo esplicito anche nella finestra degli strumenti.</span><span class="sxs-lookup"><span data-stu-id="ff39e-154">Camera position and rotation angles can be set explicitly in the tools window, as well.</span></span> <span data-ttu-id="ff39e-155">È possibile ripristinare il valore predefinito della fotocamera utilizzando il pulsante **Reimposta** .</span><span class="sxs-lookup"><span data-stu-id="ff39e-155">The camera can be reset to its default using the **Reset** button.</span></span>

<iframe width="560" height="315" src="https://www.youtube.com/embed/Z7L4I1ET7GU" class="center" frameborder="0" allow="accelerometer; encrypted-media; gyroscope; picture-in-picture" allowfullscreen />

## <a name="hand-simulation"></a><span data-ttu-id="ff39e-156">Simulazione manuale</span><span class="sxs-lookup"><span data-stu-id="ff39e-156">Hand simulation</span></span>

<span data-ttu-id="ff39e-157">La simulazione di input supporta i dispositivi a mano emulata.</span><span class="sxs-lookup"><span data-stu-id="ff39e-157">The input simulation supports emulated hand devices.</span></span> <span data-ttu-id="ff39e-158">Queste mani virtuali possono interagire con qualsiasi oggetto che supporti i normali dispositivi a mano, ad esempio pulsanti o oggetti afferrabili.</span><span class="sxs-lookup"><span data-stu-id="ff39e-158">These virtual hands can interact with any object that supports regular hand devices, such as buttons or grabbable objects.</span></span>

### <a name="hand-simulation-mode"></a><span data-ttu-id="ff39e-159">Modalità simulazione manuale</span><span class="sxs-lookup"><span data-stu-id="ff39e-159">Hand simulation mode</span></span>

<span data-ttu-id="ff39e-160">Nella [finestra strumenti di simulazione input](#input-simulation-tools-window) l'impostazione **modalità simulazione manuale** passa tra due modelli di input distinti.</span><span class="sxs-lookup"><span data-stu-id="ff39e-160">In the [input simulation tools window](#input-simulation-tools-window) the **Hand Simulation Mode** setting switches between two distinct input models.</span></span> <span data-ttu-id="ff39e-161">È anche possibile impostare la modalità predefinita nel profilo di simulazione di input.</span><span class="sxs-lookup"><span data-stu-id="ff39e-161">The default mode can also be set in the input simulation profile.</span></span>

* <span data-ttu-id="ff39e-162">*Mano articolata*: simula un dispositivo mano completamente articolato con dati di posizione congiunta.</span><span class="sxs-lookup"><span data-stu-id="ff39e-162">*Articulated Hands*: Simulates a fully articulated hand device with joint position data.</span></span>

   <span data-ttu-id="ff39e-163">Emula il modello di interazione HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="ff39e-163">Emulates HoloLens 2 interaction model.</span></span>

   <span data-ttu-id="ff39e-164">In questa modalità le interazioni basate sul posizionamento preciso della mano o sull'uso del contatto possono essere simulate.</span><span class="sxs-lookup"><span data-stu-id="ff39e-164">Interactions that are based on the precise positioning of the hand or use touching can be simulated in this mode.</span></span>

* <span data-ttu-id="ff39e-165">*Movimenti*: simula un modello a mano semplificato con il tocco aereo e i movimenti di base.</span><span class="sxs-lookup"><span data-stu-id="ff39e-165">*Gestures*: Simulates a simplified hand model with air tap and basic gestures.</span></span>

   <span data-ttu-id="ff39e-166">Emula il [modello di interazione HoloLens](https://docs.microsoft.com/windows/mixed-reality/gestures).</span><span class="sxs-lookup"><span data-stu-id="ff39e-166">Emulates [HoloLens interaction model](https://docs.microsoft.com/windows/mixed-reality/gestures).</span></span>

   <span data-ttu-id="ff39e-167">Lo stato attivo è controllato tramite il puntatore a sguardi.</span><span class="sxs-lookup"><span data-stu-id="ff39e-167">Focus is controlled using the Gaze pointer.</span></span> <span data-ttu-id="ff39e-168">Il gesto del *rubinetto d'aria* viene usato per interagire con i pulsanti.</span><span class="sxs-lookup"><span data-stu-id="ff39e-168">The *Air Tap* gesture is used to interact with buttons.</span></span>

### <a name="controlling-hand-movement"></a><span data-ttu-id="ff39e-169">Controllo del movimento della mano</span><span class="sxs-lookup"><span data-stu-id="ff39e-169">Controlling hand movement</span></span>

<span data-ttu-id="ff39e-170">Premere e tenere premuto il **tasto di controllo a sinistra/destra** (impostazione predefinita: *spostamento sinistro* per la mano sinistra e *spazio* per la mano destra) per ottenere il controllo di entrambe le parti.</span><span class="sxs-lookup"><span data-stu-id="ff39e-170">Press and hold the **Left/Right Hand Control Key** (default: *Left Shift* for left hand and *Space* for right hand) to gain control of either hand.</span></span> <span data-ttu-id="ff39e-171">Mentre viene premuto il tasto di manipolazione, la mano verrà visualizzata nel viewport.</span><span class="sxs-lookup"><span data-stu-id="ff39e-171">While the manipulation key is pressed, the hand will appear in the viewport.</span></span> <span data-ttu-id="ff39e-172">Una volta rilasciata la chiave di manipolazione, le mani scompariranno dopo un **timeout di Nascondi a mano** breve.</span><span class="sxs-lookup"><span data-stu-id="ff39e-172">Once the manipulation key is released, the hands will disappear after a short **Hand Hide Timeout**.</span></span>

<span data-ttu-id="ff39e-173">Le mani possono essere attivate in modo permanente nella [finestra degli strumenti di simulazione di input](#input-simulation-tools-window) o premendo il tasto di **attivazione/disattivazione** (impostazione predefinita: *T* per left e *Y* per Right).</span><span class="sxs-lookup"><span data-stu-id="ff39e-173">Hands can be toggled on permanently in the [input simulation tools window](#input-simulation-tools-window) or by pressing the **Toggle Left/Right Hand Key** (default: *T* for left and *Y* for right).</span></span> <span data-ttu-id="ff39e-174">Premere di nuovo il tasto di attivazione per nascondere di nuovo le lancette.</span><span class="sxs-lookup"><span data-stu-id="ff39e-174">Press the toggle key again to hide the hands again.</span></span>

<span data-ttu-id="ff39e-175">Il movimento del mouse sposterà la mano nel piano di visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="ff39e-175">Mouse movement will move the hand in the view plane.</span></span> <span data-ttu-id="ff39e-176">Le mani possono essere spostate in modo più o più vicino alla fotocamera usando la **rotellina del mouse**.</span><span class="sxs-lookup"><span data-stu-id="ff39e-176">Hands can be moved further or closer to the camera using the **mouse wheel**.</span></span>

<span data-ttu-id="ff39e-177">Per ruotare le mani usando il mouse, tenere premuto il tasto di **controllo sinistro/destro** (*spostamento a sinistra* o *spazio*) *e* il pulsante di **rotazione della mano** (impostazione predefinita: *CTRL* pulsante), quindi spostare il mouse per ruotare la mano.</span><span class="sxs-lookup"><span data-stu-id="ff39e-177">To rotate hands using the mouse, hold both the **Left/Right Hand Control Key** (*Left Shift* or *Space*) *and* the **Hand Rotate Button** (default: *ctrl* button) and then move the mouse to rotate the hand.</span></span> <span data-ttu-id="ff39e-178">La velocità di rotazione della mano può essere configurata modificando l'impostazione della **velocità di rotazione della mano del mouse** nel profilo di simulazione di input.</span><span class="sxs-lookup"><span data-stu-id="ff39e-178">Hand rotation speed can be configured by changing the **Mouse Hand Rotation Speed** setting in the input simulation profile.</span></span>

<span data-ttu-id="ff39e-179">È anche possibile modificare la selezione host della mano nella [finestra strumenti di simulazione input](#input-simulation-tools-window), inclusa la reimpostazione delle lancette per impostazione predefinita.</span><span class="sxs-lookup"><span data-stu-id="ff39e-179">All hand placement can also changed in the [input simulation tools window](#input-simulation-tools-window), including resetting hands to default.</span></span>

### <a name="additional-profile-settings"></a><span data-ttu-id="ff39e-180">Impostazioni del profilo aggiuntive</span><span class="sxs-lookup"><span data-stu-id="ff39e-180">Additional profile settings</span></span>

* <span data-ttu-id="ff39e-181">Il **moltiplicatore di profondità della mano** controlla la sensibilità del movimento di profondità della rotellina del mouse.</span><span class="sxs-lookup"><span data-stu-id="ff39e-181">**Hand Depth Multiplier** controls the sensitivity of the mouse scroll wheel depth movement.</span></span> <span data-ttu-id="ff39e-182">Un numero maggiore accelererà lo zoom mano.</span><span class="sxs-lookup"><span data-stu-id="ff39e-182">A larger number will speed up hand zoom.</span></span>
* <span data-ttu-id="ff39e-183">La **distanza della mano predefinita** è la distanza iniziale delle mani dalla fotocamera.</span><span class="sxs-lookup"><span data-stu-id="ff39e-183">**Default Hand Distance** is the initial distance of hands from the camera.</span></span> <span data-ttu-id="ff39e-184">Se si fa clic sul pulsante **Reimposta** , le mani vengono inserite anche a distanza.</span><span class="sxs-lookup"><span data-stu-id="ff39e-184">Clicking the **Reset** button hands will also place hands at this distance.</span></span>
* <span data-ttu-id="ff39e-185">L' **importo del tremolio della mano** aggiunge movimento casuale a mani.</span><span class="sxs-lookup"><span data-stu-id="ff39e-185">**Hand Jitter Amount** adds random motion to hands.</span></span> <span data-ttu-id="ff39e-186">Questa funzionalità può essere usata per simulare il rilevamento manuale non accurato nel dispositivo e garantire che le interazioni funzionino correttamente con l'input rumoroso.</span><span class="sxs-lookup"><span data-stu-id="ff39e-186">This feature can be used to simulate inaccurate hand tracking on the device, and ensure that interactions work well with noisy input.</span></span>

<iframe width="560" height="315" src="https://www.youtube.com/embed/uRYfwuqsjBQ" class="center" frameborder="0" allow="accelerometer; encrypted-media; gyroscope; picture-in-picture" allowfullscreen />

### <a name="hand-gestures"></a><span data-ttu-id="ff39e-187">Movimenti della mano</span><span class="sxs-lookup"><span data-stu-id="ff39e-187">Hand gestures</span></span>

<span data-ttu-id="ff39e-188">È anche possibile simulare movimenti della mano, ad esempio pizzicare, afferrare, frugare e così via.</span><span class="sxs-lookup"><span data-stu-id="ff39e-188">Hand gestures such as pinching, grabbing, poking, etc. can also be simulated.</span></span>

1. <span data-ttu-id="ff39e-189">Abilitare il controllo della mano usando il **tasto di controllo sinistro o destro** (*spostamento a sinistra* o *spazio*)</span><span class="sxs-lookup"><span data-stu-id="ff39e-189">Enable hand control using the **Left/Right Hand Control Key** (*Left Shift* or *Space*)</span></span>

   <span data-ttu-id="ff39e-190">In alternativa, attivare/disattivare le lancette usando i tasti di alternanza (*T* o *Y*).</span><span class="sxs-lookup"><span data-stu-id="ff39e-190">Alternatively, toggle the hands on/off using the toggle keys (*T* or *Y*).</span></span>

2. <span data-ttu-id="ff39e-191">Durante la manipolazione, premere e tenere premuto un pulsante del mouse per eseguire un movimento di mano.</span><span class="sxs-lookup"><span data-stu-id="ff39e-191">While manipulating, press and hold a mouse button to perform a hand gesture.</span></span>

<span data-ttu-id="ff39e-192">È possibile eseguire il mapping di ognuno dei pulsanti del mouse per trasformare la forma mano in un movimento diverso usando le impostazioni di *movimento della mano sinistra/centrale/destra del mouse* .</span><span class="sxs-lookup"><span data-stu-id="ff39e-192">Each of the mouse buttons can be mapped to transform the hand shape into a different gesture using the *Left/Middle/Right Mouse Hand Gesture* settings.</span></span> <span data-ttu-id="ff39e-193">Il *gesto della mano predefinito* è la forma della mano quando non viene premuto alcun pulsante.</span><span class="sxs-lookup"><span data-stu-id="ff39e-193">The *Default Hand Gesture* is the shape of the hand when no button is pressed.</span></span>

> [!NOTE]
> <span data-ttu-id="ff39e-194">Il gesto del *pizzico* è l'unico gesto che esegue l'azione "Select" a questo punto.</span><span class="sxs-lookup"><span data-stu-id="ff39e-194">The *Pinch* gesture is the only gesture that performs the "Select" action at this point.</span></span>

### <a name="one-hand-manipulation"></a><span data-ttu-id="ff39e-195">Manipolazione a mano singola</span><span class="sxs-lookup"><span data-stu-id="ff39e-195">One-hand manipulation</span></span>

1. <span data-ttu-id="ff39e-196">Premere e tenere premuto il **tasto di controllo a sinistra/destra** (*spostamento a sinistra* o *spazio*)</span><span class="sxs-lookup"><span data-stu-id="ff39e-196">Press and hold **Left/Right Hand Control Key** (*Left Shift* or *Space*)</span></span>
2. <span data-ttu-id="ff39e-197">Punto all'oggetto</span><span class="sxs-lookup"><span data-stu-id="ff39e-197">Point at object</span></span>
3. <span data-ttu-id="ff39e-198">Premere il pulsante del mouse per pizzicare</span><span class="sxs-lookup"><span data-stu-id="ff39e-198">Hold mouse button to pinch</span></span>
4. <span data-ttu-id="ff39e-199">Usare il mouse per spostare l'oggetto</span><span class="sxs-lookup"><span data-stu-id="ff39e-199">Use your mouse to move the object</span></span>
5. <span data-ttu-id="ff39e-200">Rilasciare il pulsante del mouse per arrestare l'interazione</span><span class="sxs-lookup"><span data-stu-id="ff39e-200">Release the mouse button to stop interaction</span></span>

<iframe width="560" height="315" src="https://www.youtube.com/embed/rM0xaHam6wM" class="center" frameborder="0" allow="accelerometer; encrypted-media; gyroscope; picture-in-picture" allowfullscreen />

### <a name="two-hand-manipulation"></a><span data-ttu-id="ff39e-201">Manipolazione a due mano</span><span class="sxs-lookup"><span data-stu-id="ff39e-201">Two-hand manipulation</span></span>

<span data-ttu-id="ff39e-202">Per la modifica di oggetti con due mani allo stesso tempo, è consigliabile usare la modalità mano permanente.</span><span class="sxs-lookup"><span data-stu-id="ff39e-202">For manipulating objects with two hands at the same time, the persistent hand mode is recommended.</span></span>

1. <span data-ttu-id="ff39e-203">Premere il tasto di attivazione/disattivazione (*T/Y*) per entrambe le mani.</span><span class="sxs-lookup"><span data-stu-id="ff39e-203">Toggle on both hands by pressing the toggle keys (*T/Y*).</span></span>
1. <span data-ttu-id="ff39e-204">Modificare una mano alla volta:</span><span class="sxs-lookup"><span data-stu-id="ff39e-204">Manipulate one hand at a time:</span></span>
    1. <span data-ttu-id="ff39e-205">Mantenere lo **spazio** per controllare la mano destra</span><span class="sxs-lookup"><span data-stu-id="ff39e-205">Hold **Space** to control the right hand</span></span>
    1. <span data-ttu-id="ff39e-206">Spostare la mano nella posizione in cui si desidera ottenere l'oggetto</span><span class="sxs-lookup"><span data-stu-id="ff39e-206">Move the hand to where you want to grab the object</span></span>
    1. <span data-ttu-id="ff39e-207">Premere il **pulsante sinistro del mouse** per attivare il gesto del *pizzico* .</span><span class="sxs-lookup"><span data-stu-id="ff39e-207">Press the **left mouse button** to activate the *Pinch* gesture.</span></span> <span data-ttu-id="ff39e-208">In modalità persistente il movimento rimarrà attivo quando si rilascia il pulsante del mouse.</span><span class="sxs-lookup"><span data-stu-id="ff39e-208">In persistent mode the gesture will remain active when you release the mouse button.</span></span>
1. <span data-ttu-id="ff39e-209">Ripetere il processo con l'altra parte, afferrando lo stesso oggetto in una seconda posizione.</span><span class="sxs-lookup"><span data-stu-id="ff39e-209">Repeat the process with the other hand, grabbing the same object in a second spot.</span></span>
1. <span data-ttu-id="ff39e-210">Ora che entrambe le mani stanno afferrando lo stesso oggetto, è possibile spostarle per eseguire una manipolazione a due mani.</span><span class="sxs-lookup"><span data-stu-id="ff39e-210">Now that both hands are grabbing the same object, you can move either of them to perform two-handed manipulation.</span></span>

<iframe width="560" height="315" src="https://www.youtube.com/embed/Qol5OFNfN14" class="center" frameborder="0" allow="accelerometer; encrypted-media; gyroscope; picture-in-picture" allowfullscreen />

### <a name="ggv-gaze-gesture-and-voice-interaction"></a><span data-ttu-id="ff39e-211">Interazione tra GGV (sguardi, movimenti e voce)</span><span class="sxs-lookup"><span data-stu-id="ff39e-211">GGV (Gaze, Gesture, and Voice) interaction</span></span>

<span data-ttu-id="ff39e-212">Per impostazione predefinita, l'interazione GGV è abilitata nell'editor mentre non vi sono mani articolate presenti nella scena.</span><span class="sxs-lookup"><span data-stu-id="ff39e-212">By default, GGV interaction is enabled in-editor while there are no articulated hands present in the scene.</span></span>

1. <span data-ttu-id="ff39e-213">Ruota la fotocamera per puntare il cursore sullo sguardo all'oggetto interagibile (pulsante destro del mouse)</span><span class="sxs-lookup"><span data-stu-id="ff39e-213">Rotate the camera to point the gaze cursor at the interactable object (right mouse button)</span></span>
1. <span data-ttu-id="ff39e-214">Fare clic e tenendo premuto il **pulsante sinistro del mouse** per interagire</span><span class="sxs-lookup"><span data-stu-id="ff39e-214">Click and hold **left mouse button** to interact</span></span>
1. <span data-ttu-id="ff39e-215">Ruotare nuovamente la fotocamera per modificare l'oggetto</span><span class="sxs-lookup"><span data-stu-id="ff39e-215">Rotate the camera again to manipulate the object</span></span>

<span data-ttu-id="ff39e-216">Per disattivare questa opzione, è possibile attivare o disattivare l'opzione *è abilitata per l'input Hand Free* all'interno del profilo di simulazione di input.</span><span class="sxs-lookup"><span data-stu-id="ff39e-216">You can turn this off by toggling the *Is Hand Free Input Enabled* option inside the Input Simulation Profile.</span></span>

<span data-ttu-id="ff39e-217">Inoltre, è possibile usare le mani simulate per l'interazione GGV</span><span class="sxs-lookup"><span data-stu-id="ff39e-217">In addition, you can use simulated hands for GGV interaction</span></span>

1. <span data-ttu-id="ff39e-218">Abilitare la simulazione GGV cambiando la **modalità di simulazione Hand** in *movimenti* nel [profilo di simulazione di input](#enabling-the-input-simulation-service)</span><span class="sxs-lookup"><span data-stu-id="ff39e-218">Enable GGV simulation by switching **Hand Simulation Mode** to *Gestures* in the [Input Simulation Profile](#enabling-the-input-simulation-service)</span></span>
1. <span data-ttu-id="ff39e-219">Ruota la fotocamera per puntare il cursore sullo sguardo all'oggetto interagibile (pulsante destro del mouse)</span><span class="sxs-lookup"><span data-stu-id="ff39e-219">Rotate the camera to point the gaze cursor at the interactable object (right mouse button)</span></span>
1. <span data-ttu-id="ff39e-220">Mantenere lo **spazio** per controllare la mano destra</span><span class="sxs-lookup"><span data-stu-id="ff39e-220">Hold **Space** to control the right hand</span></span>
1. <span data-ttu-id="ff39e-221">Fare clic e tenendo premuto il **pulsante sinistro del mouse** per interagire</span><span class="sxs-lookup"><span data-stu-id="ff39e-221">Click and hold **left mouse button** to interact</span></span>
1. <span data-ttu-id="ff39e-222">Usare il mouse per spostare l'oggetto</span><span class="sxs-lookup"><span data-stu-id="ff39e-222">Use your mouse to move the object</span></span>
1. <span data-ttu-id="ff39e-223">Rilasciare il pulsante del mouse per arrestare l'interazione</span><span class="sxs-lookup"><span data-stu-id="ff39e-223">Release the mouse button to stop interaction</span></span>

<iframe width="560" height="315" src="https://www.youtube.com/embed/6841rRMdqWw" class="center" frameborder="0" allow="accelerometer; encrypted-media; gyroscope; picture-in-picture" allowfullscreen />

### <a name="eye-tracking"></a><span data-ttu-id="ff39e-224">Tracciamento oculare</span><span class="sxs-lookup"><span data-stu-id="ff39e-224">Eye tracking</span></span>

<span data-ttu-id="ff39e-225">È possibile abilitare la [simulazione di rilevamento degli occhi](../EyeTracking/EyeTracking_BasicSetup.md#simulating-eye-tracking-in-the-unity-editor) selezionando l'opzione **simula posizione occhio** nel [Profilo simulazione di input](#enabling-the-input-simulation-service).</span><span class="sxs-lookup"><span data-stu-id="ff39e-225">[Eye tracking simulation](../EyeTracking/EyeTracking_BasicSetup.md#simulating-eye-tracking-in-the-unity-editor) can be enabled by checking the **Simulate Eye Position** option in the [Input Simulation Profile](#enabling-the-input-simulation-service).</span></span> <span data-ttu-id="ff39e-226">Questa operazione non deve essere utilizzata con le interazioni di stile GGV (pertanto, assicurarsi che la **modalità simulazione manuale** sia impostata su *articolato*).</span><span class="sxs-lookup"><span data-stu-id="ff39e-226">This should not be used with GGV style interactions (so ensure that **Hand Simulation Mode** is set to *Articulated*).</span></span>

## <a name="see-also"></a><span data-ttu-id="ff39e-227">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="ff39e-227">See also</span></span>

* <span data-ttu-id="ff39e-228">[Profilo di sistema di input](../Input/InputProviders.md).</span><span class="sxs-lookup"><span data-stu-id="ff39e-228">[Input System profile](../Input/InputProviders.md).</span></span>

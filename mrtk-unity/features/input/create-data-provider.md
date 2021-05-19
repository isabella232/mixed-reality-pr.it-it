---
title: Creazione di provider di dati di input
description: documentazione per creare il sistema di input e il provider di dati in MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: c164fa406ae6822f4d889aff3bf615cf7fa76337
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144069"
---
# <a name="creating-an-input-system-data-provider"></a><span data-ttu-id="8dbd8-104">Creazione di un provider di dati del sistema di input</span><span class="sxs-lookup"><span data-stu-id="8dbd8-104">Creating an input system data provider</span></span>

<span data-ttu-id="8dbd8-105">Il sistema di input mixed reality toolkit è un sistema estendibile per l'abilitazione del supporto dei dispositivi di input.</span><span class="sxs-lookup"><span data-stu-id="8dbd8-105">The Mixed Reality Toolkit input system is an extensible system for enabling input device support.</span></span> <span data-ttu-id="8dbd8-106">Per aggiungere il supporto per una nuova piattaforma hardware, potrebbe essere necessario un provider di dati di input personalizzato.</span><span class="sxs-lookup"><span data-stu-id="8dbd8-106">To add support for a new hardware platform, a custom input data provider may be required.</span></span>

<span data-ttu-id="8dbd8-107">Questo articolo descrive come creare provider di dati personalizzati, detti anche gestori di dispositivi, per il sistema di input.</span><span class="sxs-lookup"><span data-stu-id="8dbd8-107">This article describes how to create custom data providers, also called device managers, for the input system.</span></span> <span data-ttu-id="8dbd8-108">Il codice di esempio illustrato di seguito è da [`WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityDeviceManager) .</span><span class="sxs-lookup"><span data-stu-id="8dbd8-108">The example code shown here is from the [`WindowsMixedRealityDeviceManager`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityDeviceManager).</span></span>

> <span data-ttu-id="8dbd8-109">Il codice completo usato in questo esempio è disponibile nella cartella MRTK/Providers/WindowsMixedReality.</span><span class="sxs-lookup"><span data-stu-id="8dbd8-109">The complete code used in this example can be found in the MRTK/Providers/WindowsMixedReality folder.</span></span>

## <a name="namespace-and-folder-structure"></a><span data-ttu-id="8dbd8-110">Spazio dei nomi e struttura di cartelle</span><span class="sxs-lookup"><span data-stu-id="8dbd8-110">Namespace and folder structure</span></span>

<span data-ttu-id="8dbd8-111">I provider di dati possono essere distribuiti come componenti aggiuntivi di terze parti o come parte di Microsoft Mixed Reality Toolkit.</span><span class="sxs-lookup"><span data-stu-id="8dbd8-111">Data providers can be distributed as a third party add-on or as a part of the Microsoft Mixed Reality Toolkit.</span></span> <span data-ttu-id="8dbd8-112">Il processo di approvazione per l'invio di nuovi provider di dati a MRTK varia caso per caso e verrà comunicato al momento della proposta iniziale.</span><span class="sxs-lookup"><span data-stu-id="8dbd8-112">The approval process for submissions of new data providers to the MRTK will vary on a case-by-case basis and will be communicated at the time of the initial proposal.</span></span>

> [!Important]
> <span data-ttu-id="8dbd8-113">Se un provider di dati del sistema di input  viene inviato al [repository mixed reality toolkit,](https://github.com/Microsoft/MixedRealityToolkit-Unity)lo spazio dei nomi deve iniziare con Microsoft.MixedReality.Toolkit (ad esempio: Microsoft.MixedReality.Toolkit.WindowsMixedReality) e il codice deve trovarsi in una cartella sotto MRTK/Providers (ad esempio: MRTK/Providers/WindowsMixedReality).</span><span class="sxs-lookup"><span data-stu-id="8dbd8-113">If an input system data provider is being submitted to the [Mixed Reality Toolkit repository](https://github.com/Microsoft/MixedRealityToolkit-Unity), the namespace **must** begin with Microsoft.MixedReality.Toolkit (ex: Microsoft.MixedReality.Toolkit.WindowsMixedReality) and the code should be located in a folder beneath MRTK/Providers (ex: MRTK/Providers/WindowsMixedReality).</span></span>

### <a name="namespace"></a><span data-ttu-id="8dbd8-114">Spazio dei nomi</span><span class="sxs-lookup"><span data-stu-id="8dbd8-114">Namespace</span></span>

<span data-ttu-id="8dbd8-115">I provider di dati devono disporre di uno spazio dei nomi per ridurre i potenziali conflitti di nomi.</span><span class="sxs-lookup"><span data-stu-id="8dbd8-115">Data providers are required to have a namespace to mitigate potential name collisions.</span></span> <span data-ttu-id="8dbd8-116">È consigliabile che lo spazio dei nomi includa i componenti seguenti.</span><span class="sxs-lookup"><span data-stu-id="8dbd8-116">It is recommended that the namespace includes the following components.</span></span>

- <span data-ttu-id="8dbd8-117">Nome azienda</span><span class="sxs-lookup"><span data-stu-id="8dbd8-117">Company name</span></span>
- <span data-ttu-id="8dbd8-118">Area funzionale</span><span class="sxs-lookup"><span data-stu-id="8dbd8-118">Feature area</span></span>

<span data-ttu-id="8dbd8-119">Ad esempio, un provider di dati di input creato dall'azienda Contoso può essere "Contoso.MixedReality.Toolkit.Input".</span><span class="sxs-lookup"><span data-stu-id="8dbd8-119">For example, an input data provider created by the Contoso company may be "Contoso.MixedReality.Toolkit.Input".</span></span>

### <a name="recommended-folder-structure"></a><span data-ttu-id="8dbd8-120">Struttura di cartelle consigliata</span><span class="sxs-lookup"><span data-stu-id="8dbd8-120">Recommended folder structure</span></span>

<span data-ttu-id="8dbd8-121">È consigliabile che il codice sorgente per i provider di dati sia disponibile in una gerarchia di cartelle, come illustrato nell'immagine seguente.</span><span class="sxs-lookup"><span data-stu-id="8dbd8-121">It is recommended that the source code for data providers be layed out in a folder hierarchy as shown in the following image.</span></span>

![Esempio di struttura di cartelle](../images/input/ExampleProviderFolderStructure.png)

<span data-ttu-id="8dbd8-123">Dove ContosoInput contiene l'implementazione del provider di dati, la cartella Editor contiene il controllo (e qualsiasi altro codice specifico dell'editor unity), la cartella Textures contiene le immagini dei controller supportati e Profiles contiene uno o più profili predefiniti.</span><span class="sxs-lookup"><span data-stu-id="8dbd8-123">Where ContosoInput contains the implementation of the data provider, the Editor folder contains the inspector (and any other Unity editor specific code), the Textures folder contains images of the supported controllers, and Profiles contains one or more pre-made profiles.</span></span>

> [!Note]
> <span data-ttu-id="8dbd8-124">Alcune immagini comuni del controller sono disponibili nella cartella MixedRealityToolkit\StandardAssets\Textures.</span><span class="sxs-lookup"><span data-stu-id="8dbd8-124">Some common controller images can be found in the MixedRealityToolkit\StandardAssets\Textures folder.</span></span>

## <a name="implement-the-data-provider"></a><span data-ttu-id="8dbd8-125">Implementare il provider di dati</span><span class="sxs-lookup"><span data-stu-id="8dbd8-125">Implement the data provider</span></span>

### <a name="specify-interface-andor-base-class-inheritance"></a><span data-ttu-id="8dbd8-126">Specificare l'ereditarietà dell'interfaccia e/o della classe base</span><span class="sxs-lookup"><span data-stu-id="8dbd8-126">Specify interface and/or base class inheritance</span></span>

<span data-ttu-id="8dbd8-127">Tutti i provider di dati del sistema di input devono implementare l'interfaccia , che [`IMixedRealityInputDeviceManager`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputDeviceManager) specifica la funzionalità minima richiesta dal sistema di input.</span><span class="sxs-lookup"><span data-stu-id="8dbd8-127">All input system data providers must implement the [`IMixedRealityInputDeviceManager`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputDeviceManager) interface, which specifies the minimum functionality required by the input system.</span></span> <span data-ttu-id="8dbd8-128">La base di MRTK include [`BaseInputDeviceManager`](xref:Microsoft.MixedReality.Toolkit.Input.BaseInputDeviceManager) la classe che fornisce un'implementazione predefinita di questa funzionalità richiesta.</span><span class="sxs-lookup"><span data-stu-id="8dbd8-128">The MRTK foundation includes the [`BaseInputDeviceManager`](xref:Microsoft.MixedReality.Toolkit.Input.BaseInputDeviceManager) class which provides a default implementation of this required functionality.</span></span> <span data-ttu-id="8dbd8-129">Per i dispositivi che si basano sulla classe UInput di Unity, la [`UnityJoystickManager`](xref:Microsoft.MixedReality.Toolkit.Input.UnityInput.UnityJoystickManager) classe può essere usata come classe di base.</span><span class="sxs-lookup"><span data-stu-id="8dbd8-129">For devices that build upon Unity's UInput class, the [`UnityJoystickManager`](xref:Microsoft.MixedReality.Toolkit.Input.UnityInput.UnityJoystickManager) class can be used as a base class.</span></span>

> [!Note]
> <span data-ttu-id="8dbd8-130">Le `BaseInputDeviceManager` classi e forniscono `UnityJoystickManager` l'implementazione `IMixedRealityInputDeviceManager` richiesta.</span><span class="sxs-lookup"><span data-stu-id="8dbd8-130">The `BaseInputDeviceManager` and `UnityJoystickManager` classes provide the required `IMixedRealityInputDeviceManager` implementation.</span></span>

```c#
public class WindowsMixedRealityDeviceManager :
    BaseInputDeviceManager,
    IMixedRealityCapabilityCheck
{ }
```

> <span data-ttu-id="8dbd8-131">`IMixedRealityCapabilityCheck` viene usato da per indicare che fornisce supporto per un set di funzionalità di input, in particolare mani articolate, mani con movimento fisso e controller `WindowsMixedRealityDeviceManager` del movimento.</span><span class="sxs-lookup"><span data-stu-id="8dbd8-131">`IMixedRealityCapabilityCheck` is used by the `WindowsMixedRealityDeviceManager` to indicate that it provides support for a set of input capabilities, specifically; articulated hands, gaze-gesture-voice hands and motion controllers.</span></span>

#### <a name="apply-the-mixedrealitydataprovider-attribute"></a><span data-ttu-id="8dbd8-132">Applicare l'attributo MixedRealityDataProvider</span><span class="sxs-lookup"><span data-stu-id="8dbd8-132">Apply the MixedRealityDataProvider attribute</span></span>

<span data-ttu-id="8dbd8-133">Un passaggio chiave della creazione di un provider di dati di sistema di input consiste nell'applicare [`MixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.MixedRealityDataProviderAttribute) l'attributo alla classe .</span><span class="sxs-lookup"><span data-stu-id="8dbd8-133">A key step of creating an input system data provider is to apply the [`MixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.MixedRealityDataProviderAttribute) attribute to the class.</span></span> <span data-ttu-id="8dbd8-134">Questo passaggio abilita l'impostazione del profilo predefinito e delle piattaforme per il provider, se selezionato nel profilo di sistema di input.</span><span class="sxs-lookup"><span data-stu-id="8dbd8-134">This step enables setting the default profile and platform(s) for the provider, when selected in the input system profile.</span></span>

```c#
[MixedRealityDataProvider(
    typeof(IMixedRealityInputSystem),
    SupportedPlatforms.WindowsUniversal,
    "Windows Mixed Reality Device Manager")]
public class WindowsMixedRealityDeviceManager :
    BaseInputDeviceManager,
    IMixedRealityCapabilityCheck
{ }
```

### <a name="implement-the-imixedrealitydataprovider-methods"></a><span data-ttu-id="8dbd8-135">Implementare i metodi IMixedRealityDataProvider</span><span class="sxs-lookup"><span data-stu-id="8dbd8-135">Implement the IMixedRealityDataProvider methods</span></span>

<span data-ttu-id="8dbd8-136">Dopo aver definito la classe , il passaggio successivo consiste nel fornire l'implementazione [`IMixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) dell'interfaccia .</span><span class="sxs-lookup"><span data-stu-id="8dbd8-136">Once the class has been defined, the next step is to provide the implementation of the [`IMixedRealityDataProvider`](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider) interface.</span></span>

> [!Note]
> <span data-ttu-id="8dbd8-137">La `BaseInputDeviceManager` classe , tramite la classe , fornisce solo `BaseService` implementazioni vuote per i metodi `IMixedRealityDataProvider` .</span><span class="sxs-lookup"><span data-stu-id="8dbd8-137">The `BaseInputDeviceManager` class, via the `BaseService` class, provides only empty implementations for `IMixedRealityDataProvider` methods.</span></span> <span data-ttu-id="8dbd8-138">I dettagli di questi metodi sono in genere specifici del provider di dati.</span><span class="sxs-lookup"><span data-stu-id="8dbd8-138">The details of these methods are generally data provider specific.</span></span>

<span data-ttu-id="8dbd8-139">I metodi che devono essere implementati dal provider di dati sono:</span><span class="sxs-lookup"><span data-stu-id="8dbd8-139">The methods that should be implemented by the data provider are:</span></span>

- `Destroy()`
- `Disable()`
- `Enable()`
- `Initialize()`
- `Reset()`
- `Update()`

### <a name="implement-the-data-provider-logic"></a><span data-ttu-id="8dbd8-140">Implementare la logica del provider di dati</span><span class="sxs-lookup"><span data-stu-id="8dbd8-140">Implement the data provider logic</span></span>

<span data-ttu-id="8dbd8-141">Il passaggio successivo consiste nell'aggiungere la logica per la gestione dei dispositivi di input, inclusi eventuali controller da supporto.</span><span class="sxs-lookup"><span data-stu-id="8dbd8-141">The next step is to add the logic for managing the input devices, including any controllers to be supported.</span></span>

### <a name="implement-the-controller-classes"></a><span data-ttu-id="8dbd8-142">Implementare le classi controller</span><span class="sxs-lookup"><span data-stu-id="8dbd8-142">Implement the controller classes</span></span>

 <span data-ttu-id="8dbd8-143">L'esempio di `WindowsMixedRealityDeviceManager` definisce e implementa le classi controller seguenti.</span><span class="sxs-lookup"><span data-stu-id="8dbd8-143">The example of the `WindowsMixedRealityDeviceManager` defines and implements the following controller classes.</span></span>

> <span data-ttu-id="8dbd8-144">Il codice sorgente per ognuna di queste classi è disponibile nella cartella MRTK/Providers/WindowsMixedReality.</span><span class="sxs-lookup"><span data-stu-id="8dbd8-144">The source code for each of these classes can be found in the MRTK/Providers/WindowsMixedReality folder.</span></span>

- <span data-ttu-id="8dbd8-145">WindowsMixedRealityArticulatedHand.cs</span><span class="sxs-lookup"><span data-stu-id="8dbd8-145">WindowsMixedRealityArticulatedHand.cs</span></span>
- <span data-ttu-id="8dbd8-146">WindowsMixedRealityController.cs</span><span class="sxs-lookup"><span data-stu-id="8dbd8-146">WindowsMixedRealityController.cs</span></span>
- <span data-ttu-id="8dbd8-147">WindowsMixedRealityGGVHand.cs</span><span class="sxs-lookup"><span data-stu-id="8dbd8-147">WindowsMixedRealityGGVHand.cs</span></span>

> [!Note]
> <span data-ttu-id="8dbd8-148">Non tutti i gestori di dispositivi supporteranno più tipi di controller.</span><span class="sxs-lookup"><span data-stu-id="8dbd8-148">Not all device managers will support multiple controller types.</span></span>

#### <a name="apply-the-mixedrealitycontroller-attribute"></a><span data-ttu-id="8dbd8-149">Applicare l'attributo MixedRealityController</span><span class="sxs-lookup"><span data-stu-id="8dbd8-149">Apply the MixedRealityController attribute</span></span>

<span data-ttu-id="8dbd8-150">Applicare quindi [`MixedRealityController`](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityControllerAttribute) l'attributo alla classe .</span><span class="sxs-lookup"><span data-stu-id="8dbd8-150">Next, apply the [`MixedRealityController`](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityControllerAttribute) attribute to the class.</span></span> <span data-ttu-id="8dbd8-151">Questo attributo specifica il tipo di controller (ad esempio: mano articolata), la mano (ad esempio, sinistra o destra) e un'immagine del controller facoltativa.</span><span class="sxs-lookup"><span data-stu-id="8dbd8-151">This attribute specifies the type of controller (ex: articulated hand), the handedness (ex: left or right) and an optional controller image.</span></span>

```c#
[MixedRealityController(
    SupportedControllerType.WindowsMixedReality,
    new[] { Handedness.Left, Handedness.Right },
    "StandardAssets/Textures/MotionController")]
{ }
```

#### <a name="configure-the-interaction-mappings"></a><span data-ttu-id="8dbd8-152">Configurare i mapping di interazione</span><span class="sxs-lookup"><span data-stu-id="8dbd8-152">Configure the interaction mappings</span></span>

<span data-ttu-id="8dbd8-153">Il passaggio successivo consiste nel definire il set di mapping di interazione supportati dal controller.</span><span class="sxs-lookup"><span data-stu-id="8dbd8-153">The next step is to define the set of interaction mappings supported by the controller.</span></span> <span data-ttu-id="8dbd8-154">Per i dispositivi che ricevono i dati tramite la classe Input di Unity, lo strumento di mapping del [controller](../tools/controller-mapping-tool.md) è una risorsa utile per confermare i mapping degli assi e dei pulsanti corretti da assegnare alle interazioni.</span><span class="sxs-lookup"><span data-stu-id="8dbd8-154">For devices that receive their data via Unity's Input class, the [controller mapping tool](../tools/controller-mapping-tool.md) is a helpful resource to confirm the correct axis and button mappings to assign to interactions.</span></span>

<span data-ttu-id="8dbd8-155">L'esempio seguente è abbreviato dalla classe `GenericOpenVRController` , che si trova nella cartella MRTK/Providers/OpenVR.</span><span class="sxs-lookup"><span data-stu-id="8dbd8-155">The following example is abbreviated from the `GenericOpenVRController` class, located in the MRTK/Providers/OpenVR folder.</span></span>

```c#
public override MixedRealityInteractionMapping[] DefaultLeftHandedInteractions => new[]
{
    // Controller Pose
    new MixedRealityInteractionMapping(0, "Spatial Pointer", AxisType.SixDof, DeviceInputType.SpatialPointer, MixedRealityInputAction.None),
    // Left Trigger Squeeze
    new MixedRealityInteractionMapping(1, "Trigger Position", AxisType.SingleAxis, DeviceInputType.Trigger, ControllerMappingLibrary.AXIS_9),
    // Left Trigger Press (Select)
    new MixedRealityInteractionMapping(2, "Trigger Press (Select)", AxisType.Digital, DeviceInputType.TriggerPress, KeyCode.JoystickButton14),
};
```

>[!Note]
><span data-ttu-id="8dbd8-156">La [`ControllerMappingLibrary`](xref:Microsoft.MixedReality.Toolkit.Input.ControllerMappingLibrary) classe fornisce costanti simboliche per le definizioni di asse di input e pulsante di Unity.</span><span class="sxs-lookup"><span data-stu-id="8dbd8-156">The [`ControllerMappingLibrary`](xref:Microsoft.MixedReality.Toolkit.Input.ControllerMappingLibrary) class provides symbolic constants for the Unity input axis and button definitions.</span></span>

### <a name="raise-notification-events"></a><span data-ttu-id="8dbd8-157">Generare eventi di notifica</span><span class="sxs-lookup"><span data-stu-id="8dbd8-157">Raise notification events</span></span>

<span data-ttu-id="8dbd8-158">Per consentire alle applicazioni di rispondere all'input dell'utente, il provider di dati genera eventi di notifica corrispondenti alle modifiche dello stato del controller, come definito nelle [`IMixedRealityInputHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler) [`IMixedRealityInputHandler<T>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler`1) interfacce e .</span><span class="sxs-lookup"><span data-stu-id="8dbd8-158">To enable applications to respond to input from the user, the data provider raises notification events corresponding to controller state changes as defined in the [`IMixedRealityInputHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler) and [`IMixedRealityInputHandler<T>`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler`1) interfaces.</span></span>

<span data-ttu-id="8dbd8-159">Per i controlli di tipo digitale (pulsante), generare gli eventi OnInputDown e OnInputUp.</span><span class="sxs-lookup"><span data-stu-id="8dbd8-159">For digital (button) type controls, raise the OnInputDown and OnInputUp events.</span></span>

```c#
// inputAction is the input event that is to be raised.
if (interactionSourceState.touchpadPressed)
{
    InputSystem?.RaiseOnInputDown(InputSource, ControllerHandedness, inputAction);
}
else
{
    InputSystem?.RaiseOnInputUp(InputSource, ControllerHandedness, inputAction);
}
```

<span data-ttu-id="8dbd8-160">Per i controlli analoghi ,ad esempio la posizione del touchpad, deve essere generato l'evento InputChanged.</span><span class="sxs-lookup"><span data-stu-id="8dbd8-160">For analog controls (ex: touchpad position) the InputChanged event should be raised.</span></span>

```c#
InputSystem?.RaisePositionInputChanged(InputSource, ControllerHandedness, interactionMapping.MixedRealityInputAction, interactionSourceState.touchpadPosition);
```

### <a name="add-unity-profiler-instrumentation"></a><span data-ttu-id="8dbd8-161">Aggiungere la strumentazione del profiler Unity</span><span class="sxs-lookup"><span data-stu-id="8dbd8-161">Add Unity Profiler instrumentation</span></span>

<span data-ttu-id="8dbd8-162">Le prestazioni sono fondamentali nelle applicazioni di realtà mista.</span><span class="sxs-lookup"><span data-stu-id="8dbd8-162">Performance is critical in mixed reality applications.</span></span> <span data-ttu-id="8dbd8-163">Ogni componente aggiunge una certa quantità di overhead per cui le applicazioni devono essere gestite.</span><span class="sxs-lookup"><span data-stu-id="8dbd8-163">Every component adds some amount of overhead for which applications must account.</span></span> <span data-ttu-id="8dbd8-164">A questo scopo, è importante che tutti i provider di dati di input contengano la strumentazione del profiler Unity nel ciclo interno e i percorsi di codice usati di frequente.</span><span class="sxs-lookup"><span data-stu-id="8dbd8-164">To this end, it is important that all input data providers contain Unity Profiler instrumentation in inner loop and frequently utilized code paths.</span></span>

<span data-ttu-id="8dbd8-165">È consigliabile implementare il modello utilizzato da MRTK durante la strumentazione di provider personalizzati.</span><span class="sxs-lookup"><span data-stu-id="8dbd8-165">It is recommended to implement the pattern utilized by the MRTK when instrumenting custom providers.</span></span>

```c#
        private static readonly ProfilerMarker GetOrAddControllerPerfMarker = new ProfilerMarker("[MRTK] WindowsMixedRealityDeviceManager.GetOrAddController");

        private async void GetOrAddController(InteractionSourceState interactionSourceState)
        {
            using (GetOrAddControllerPerfMarker.Auto())
            {
                // Code to be measured.
            }
        }
```

> [!Note]
> <span data-ttu-id="8dbd8-166">Il nome usato per identificare il marcatore del profiler è arbitrario.</span><span class="sxs-lookup"><span data-stu-id="8dbd8-166">The name used to identify the profiler marker is arbitrary.</span></span> <span data-ttu-id="8dbd8-167">MrTK usa il modello seguente.</span><span class="sxs-lookup"><span data-stu-id="8dbd8-167">The MRTK uses the following pattern.</span></span>
>
> <span data-ttu-id="8dbd8-168">"[product] className.methodName - nota facoltativa"</span><span class="sxs-lookup"><span data-stu-id="8dbd8-168">"[product] className.methodName - optional note"</span></span>
>
> <span data-ttu-id="8dbd8-169">È consigliabile che i provider di dati personalizzati seguano un modello simile per semplificare l'identificazione di componenti e metodi specifici durante l'analisi delle tracce.</span><span class="sxs-lookup"><span data-stu-id="8dbd8-169">It is recommended that custom data providers follow a similar pattern to help simplify identification of specific components and methods when analyzing traces.</span></span>

## <a name="create-the-profile-and-inspector"></a><span data-ttu-id="8dbd8-170">Creare il profilo e il controllo</span><span class="sxs-lookup"><span data-stu-id="8dbd8-170">Create the profile and inspector</span></span>

<span data-ttu-id="8dbd8-171">In Mixed Reality Toolkit i provider di dati vengono configurati usando [i profili](../profiles/profiles.md).</span><span class="sxs-lookup"><span data-stu-id="8dbd8-171">In the Mixed Reality Toolkit, data providers are configured using [profiles](../profiles/profiles.md).</span></span>

<span data-ttu-id="8dbd8-172">I provider di dati con opzioni di configurazione aggiuntive (ad [esempio, InputSimulationService](../input-simulation/input-simulation-service.md)) devono creare un profilo e un controllo per consentire ai clienti di modificare il comportamento in base alle esigenze dell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="8dbd8-172">Data providers with additional configuration options (ex: [InputSimulationService](../input-simulation/input-simulation-service.md)) should create a profile and inspector to allow customers to modify the behavior to best suit the needs of the application.</span></span>

> <span data-ttu-id="8dbd8-173">Il codice completo per l'esempio in questa sezione è disponibile in MRTK. Cartella Services/InputSimulation.</span><span class="sxs-lookup"><span data-stu-id="8dbd8-173">The complete code for the example in this section can be found in the MRTK.Services/InputSimulation folder.</span></span>

### <a name="define-the-profile"></a><span data-ttu-id="8dbd8-174">Definire il profilo</span><span class="sxs-lookup"><span data-stu-id="8dbd8-174">Define the profile</span></span>

<span data-ttu-id="8dbd8-175">Il contenuto del profilo deve rispecchiare le proprietà accessibili dell'osservatore (ad esempio, l'intervallo di aggiornamento).</span><span class="sxs-lookup"><span data-stu-id="8dbd8-175">Profile contents should mirror the accessible properties of the observer (ex: update interval).</span></span> <span data-ttu-id="8dbd8-176">Tutte le proprietà configurabili dall'utente definite in ogni interfaccia devono essere contenute nel profilo.</span><span class="sxs-lookup"><span data-stu-id="8dbd8-176">All of the user configurable properties defined in each interface should be contained with the profile.</span></span>

```c#
[CreateAssetMenu(
    menuName = "Mixed Reality Toolkit/Profiles/Mixed Reality Simulated Input Profile",
    fileName = "MixedRealityInputSimulationProfile",
    order = (int)CreateProfileMenuItemIndices.InputSimulation)]
public class MixedRealityInputSimulationProfile : BaseMixedRealityProfile
{ }
```

<span data-ttu-id="8dbd8-177">L'attributo può essere applicato alla classe del profilo per consentire ai clienti di creare un'istanza del profilo usando il menu Create > Assets > Mixed Reality Toolkit > Profiles (Crea asset > `CreateAssetMenu` Mixed Reality Toolkit > **profili).**</span><span class="sxs-lookup"><span data-stu-id="8dbd8-177">The `CreateAssetMenu` attribute can be applied to the profile class to enable customers to create a profile instance using the **Create > Assets > Mixed Reality Toolkit > Profiles** menu.</span></span>

### <a name="implement-the-inspector"></a><span data-ttu-id="8dbd8-178">Implementare il controllo</span><span class="sxs-lookup"><span data-stu-id="8dbd8-178">Implement the inspector</span></span>

<span data-ttu-id="8dbd8-179">I controlli profilo sono l'interfaccia utente per la configurazione e la visualizzazione del contenuto del profilo.</span><span class="sxs-lookup"><span data-stu-id="8dbd8-179">Profile inspectors are the user interface for configuring and viewing profile contents.</span></span> <span data-ttu-id="8dbd8-180">Ogni controllo profilo deve estendere la [classe 'BaseMixedRealityToolkitConfigurationProfileInspector.](xref:Microsoft.MixedReality.Toolkit.Editor.BaseMixedRealityToolkitConfigurationProfileInspector)</span><span class="sxs-lookup"><span data-stu-id="8dbd8-180">Each profile inspector should extend the [\`BaseMixedRealityToolkitConfigurationProfileInspector](xref:Microsoft.MixedReality.Toolkit.Editor.BaseMixedRealityToolkitConfigurationProfileInspector) class.</span></span>

```c#
[CustomEditor(typeof(MixedRealityInputSimulationProfile))]
public class MixedRealityInputSimulationProfileInspector : BaseMixedRealityToolkitConfigurationProfileInspector
{ }
```

<span data-ttu-id="8dbd8-181">`CustomEditor`L'attributo indica a Unity il tipo di asset a cui si applica il controllo.</span><span class="sxs-lookup"><span data-stu-id="8dbd8-181">The `CustomEditor` attribute informs Unity the type of asset to which the inspector applies.</span></span>

## <a name="create-assembly-definitions"></a><span data-ttu-id="8dbd8-182">Creare definizioni di assembly</span><span class="sxs-lookup"><span data-stu-id="8dbd8-182">Create assembly definition(s)</span></span>

<span data-ttu-id="8dbd8-183">Mixed Reality Toolkit usa i file di definizione dell'assembly (con estensione[asmdef)](https://docs.unity3d.com/Manual/ScriptCompilationAssemblyDefinitionFiles.html)per specificare le dipendenze tra i componenti e per aiutare Unity a ridurre il tempo di compilazione.</span><span class="sxs-lookup"><span data-stu-id="8dbd8-183">The Mixed Reality Toolkit uses assembly definition ([.asmdef](https://docs.unity3d.com/Manual/ScriptCompilationAssemblyDefinitionFiles.html)) files to specify dependencies between components as well as to assist Unity in reducing compilation time.</span></span>

<span data-ttu-id="8dbd8-184">È consigliabile creare file di definizione dell'assembly per tutti i provider di dati e i relativi componenti dell'editor.</span><span class="sxs-lookup"><span data-stu-id="8dbd8-184">It is recommended that assembly definition files are created for all data providers and their editor components.</span></span>

<span data-ttu-id="8dbd8-185">Usando la [struttura di cartelle](#recommended-folder-structure) nell'esempio precedente, saranno presenti due file con estensione asmdef per il provider di dati ContosoInput.</span><span class="sxs-lookup"><span data-stu-id="8dbd8-185">Using the [folder structure](#recommended-folder-structure) in the earlier example, there would be two .asmdef files for the ContosoInput data provider.</span></span>

<span data-ttu-id="8dbd8-186">La prima definizione di assembly è per il provider di dati.</span><span class="sxs-lookup"><span data-stu-id="8dbd8-186">The first assembly definition is for the data provider.</span></span> <span data-ttu-id="8dbd8-187">Per questo esempio, verrà chiamato ContosoInput e si trova nella cartella ContosoInput dell'esempio.</span><span class="sxs-lookup"><span data-stu-id="8dbd8-187">For this example, it will be called ContosoInput and will be located in the example's ContosoInput folder.</span></span>
<span data-ttu-id="8dbd8-188">Questa definizione di assembly deve specificare una dipendenza da Microsoft.MixedReality.Toolkit e da qualsiasi altro assembly da cui dipende.</span><span class="sxs-lookup"><span data-stu-id="8dbd8-188">This assembly definition must specify a dependency on Microsoft.MixedReality.Toolkit and any other assemblies upon which it depends.</span></span>

<span data-ttu-id="8dbd8-189">La definizione dell'assembly ContosoInputEditor specificherà il controllo profilo e qualsiasi codice specifico dell'editor.</span><span class="sxs-lookup"><span data-stu-id="8dbd8-189">The ContosoInputEditor assembly definition will specify the profile inspector and any editor specific code.</span></span> <span data-ttu-id="8dbd8-190">Questo file deve trovarsi nella cartella radice del codice dell'editor.</span><span class="sxs-lookup"><span data-stu-id="8dbd8-190">This file must be located in the root folder of the editor code.</span></span> <span data-ttu-id="8dbd8-191">In questo esempio il file si trova nella cartella ContosoInput\Editor.</span><span class="sxs-lookup"><span data-stu-id="8dbd8-191">In this example, the file will be located in the ContosoInput\Editor folder.</span></span> <span data-ttu-id="8dbd8-192">Questa definizione di assembly conterrà un riferimento all'assembly ContosoInput, nonché:</span><span class="sxs-lookup"><span data-stu-id="8dbd8-192">This assembly definition will contain a reference to the ContosoInput assembly as well as:</span></span>

- <span data-ttu-id="8dbd8-193">Microsoft.MixedReality.Toolkit</span><span class="sxs-lookup"><span data-stu-id="8dbd8-193">Microsoft.MixedReality.Toolkit</span></span>
- <span data-ttu-id="8dbd8-194">Microsoft.MixedReality.Toolkit.Editor.Inspectors</span><span class="sxs-lookup"><span data-stu-id="8dbd8-194">Microsoft.MixedReality.Toolkit.Editor.Inspectors</span></span>
- <span data-ttu-id="8dbd8-195">Microsoft.MixedReality.Toolkit.Editor.Utilities</span><span class="sxs-lookup"><span data-stu-id="8dbd8-195">Microsoft.MixedReality.Toolkit.Editor.Utilities</span></span>

## <a name="register-the-data-provider"></a><span data-ttu-id="8dbd8-196">Registrare il provider di dati</span><span class="sxs-lookup"><span data-stu-id="8dbd8-196">Register the data provider</span></span>

<span data-ttu-id="8dbd8-197">Una volta creato, il provider di dati può essere registrato con il sistema di input e usato nell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="8dbd8-197">Once created, the data provider can be registered with the input system and be used in the application.</span></span>

![Provider di dati del sistema di input registrati](../images/input/RegisteredServiceProviders.PNG)

## <a name="packaging-and-distribution"></a><span data-ttu-id="8dbd8-199">Creazione di pacchetti e distribuzione</span><span class="sxs-lookup"><span data-stu-id="8dbd8-199">Packaging and distribution</span></span>

<span data-ttu-id="8dbd8-200">I provider di dati distribuiti come componenti di terze parti hanno i dettagli specifici della creazione dei pacchetti e della distribuzione lasciati alle preferenze dello sviluppatore.</span><span class="sxs-lookup"><span data-stu-id="8dbd8-200">Data providers that are distributed as third party components have the specific details of packaging and distribution left to the preference of the developer.</span></span> <span data-ttu-id="8dbd8-201">È probabile che la soluzione più comune sia generare un file con estensione unitypackage e distribuirsi tramite Unity Asset Store.</span><span class="sxs-lookup"><span data-stu-id="8dbd8-201">Likely, the most common solution will be to generate a .unitypackage and distribute via the Unity Asset Store.</span></span>

<span data-ttu-id="8dbd8-202">Se un provider di dati viene inviato e accettato come parte del pacchetto Microsoft Mixed Reality Toolkit, il team di Microsoft MRTK lo inserirà in un pacchetto e lo distribuirà come parte delle offerte di MRTK.</span><span class="sxs-lookup"><span data-stu-id="8dbd8-202">If a data provider is submitted and accepted as a part of the Microsoft Mixed Reality Toolkit package, the Microsoft MRTK team will package and distribute it as part of the MRTK offerings.</span></span>

## <a name="see-also"></a><span data-ttu-id="8dbd8-203">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="8dbd8-203">See also</span></span>

- [<span data-ttu-id="8dbd8-204">Sistema di input</span><span class="sxs-lookup"><span data-stu-id="8dbd8-204">Input system</span></span>](overview.md)
- [<span data-ttu-id="8dbd8-205">Classe `BaseInputDeviceManager`</span><span class="sxs-lookup"><span data-stu-id="8dbd8-205">`BaseInputDeviceManager` class</span></span>](xref:Microsoft.MixedReality.Toolkit.Input.BaseInputDeviceManager)
- [<span data-ttu-id="8dbd8-206">`IMixedRealityInputDeviceManager` Interfaccia</span><span class="sxs-lookup"><span data-stu-id="8dbd8-206">`IMixedRealityInputDeviceManager` interface</span></span>](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputDeviceManager)
- [<span data-ttu-id="8dbd8-207">`IMixedRealityInputHandler` Interfaccia</span><span class="sxs-lookup"><span data-stu-id="8dbd8-207">`IMixedRealityInputHandler` interface</span></span>](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler)
- [<span data-ttu-id="8dbd8-208">`IMixedRealityInputHandler<T>` Interfaccia</span><span class="sxs-lookup"><span data-stu-id="8dbd8-208">`IMixedRealityInputHandler<T>` interface</span></span>](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputHandler`1)
- [<span data-ttu-id="8dbd8-209">`IMixedRealityDataProvider` Interfaccia</span><span class="sxs-lookup"><span data-stu-id="8dbd8-209">`IMixedRealityDataProvider` interface</span></span>](xref:Microsoft.MixedReality.Toolkit.IMixedRealityDataProvider)
- [<span data-ttu-id="8dbd8-210">`IMixedRealityCapabilityCheck` Interfaccia</span><span class="sxs-lookup"><span data-stu-id="8dbd8-210">`IMixedRealityCapabilityCheck` interface</span></span>](xref:Microsoft.MixedReality.Toolkit.IMixedRealityCapabilityCheck)
- [<span data-ttu-id="8dbd8-211">Strumento di mapping del controller</span><span class="sxs-lookup"><span data-stu-id="8dbd8-211">Controller Mapping Tool</span></span>](../tools/controller-mapping-tool.md)

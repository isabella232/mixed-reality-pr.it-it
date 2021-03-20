---
title: HandTracking
description: Documentazione su come usare HandTracking in MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, rilevamento manuale,
ms.openlocfilehash: 3609abdda55f6ceb8a8a34dc2509331a8d11800d
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2021
ms.locfileid: "104693928"
---
# <a name="hand-tracking"></a><span data-ttu-id="90f39-104">Tracciamento mano</span><span class="sxs-lookup"><span data-stu-id="90f39-104">Hand tracking</span></span>

## <a name="hand-tracking-profile"></a><span data-ttu-id="90f39-105">Profilo di rilevamento mano</span><span class="sxs-lookup"><span data-stu-id="90f39-105">Hand tracking profile</span></span>

<span data-ttu-id="90f39-106">Il _profilo di rilevamento della mano_ è disponibile nel _profilo di sistema di input_.</span><span class="sxs-lookup"><span data-stu-id="90f39-106">The _Hand Tracking profile_ is found under the _Input System profile_.</span></span> <span data-ttu-id="90f39-107">Contiene le impostazioni per la personalizzazione della rappresentazione manuale.</span><span class="sxs-lookup"><span data-stu-id="90f39-107">It contains settings for customizing hand representation.</span></span>

<img src="../images/input/HandTrackingProfile.png" width="650px" style="display:block;" alt="Hand Tracking Profile view">

## <a name="joint-prefabs"></a><span data-ttu-id="90f39-108">Prefabbricati comuni</span><span class="sxs-lookup"><span data-stu-id="90f39-108">Joint prefabs</span></span>

<span data-ttu-id="90f39-109">I prefabbricati Uniti vengono visualizzati usando semplici prefabbricati.</span><span class="sxs-lookup"><span data-stu-id="90f39-109">Joint prefabs are visualized using simple prefabs.</span></span> <span data-ttu-id="90f39-110">Le giunzioni _Palm_ e _index finger_ sono di particolare importanza e hanno una propria precostruzione, mentre tutte le altre articolazioni condividono la stessa prefabbricata.</span><span class="sxs-lookup"><span data-stu-id="90f39-110">The _Palm_ and _Index Finger_ joints are of special importance and have their own prefab, while all other joints share the same prefab.</span></span>

<span data-ttu-id="90f39-111">Per impostazione predefinita, i prefabbricati di join sono semplici primitive geometriche.</span><span class="sxs-lookup"><span data-stu-id="90f39-111">By default the hand joint prefabs are simple geometric primitives.</span></span> <span data-ttu-id="90f39-112">Se lo si desidera, è possibile sostituirli.</span><span class="sxs-lookup"><span data-stu-id="90f39-112">These can be replaced if desired.</span></span> <span data-ttu-id="90f39-113">Se non viene specificata alcuna prefabbricata, vengono invece creati [GameObject](https://docs.unity3d.com/ScriptReference/GameObject.html) vuoti.</span><span class="sxs-lookup"><span data-stu-id="90f39-113">If no prefab is specified at all, empty [GameObjects](https://docs.unity3d.com/ScriptReference/GameObject.html) are created instead.</span></span>

> [!WARNING]
> <span data-ttu-id="90f39-114">Evitare l'uso di script complessi o il rendering costoso in prefabbricati comuni, poiché gli oggetti combinati vengono trasformati in ogni frame e possono avere un costo significativo per le prestazioni.</span><span class="sxs-lookup"><span data-stu-id="90f39-114">Avoid using complex scripts or expensive rendering in joint prefabs, since joint objects are transformed on every frame and can have significant performance cost!</span></span>

<span data-ttu-id="90f39-115">Rappresentazione congiunta della mano predefinita</span><span class="sxs-lookup"><span data-stu-id="90f39-115">Default Hand Joint Representation</span></span> |  <span data-ttu-id="90f39-116">Etichette congiunte</span><span class="sxs-lookup"><span data-stu-id="90f39-116">Joint Labels</span></span>
:-------------------------:|:-------------------------:
<img src="../images/input-simulation/ArticulatedHandJoints.png" height="300px"  style="display:inline;" alt="Articulated Hand Joints">  |  <img src="../images/input-simulation/MRTK_Core_Input_Hands_JointNames.png" height="300px"  style="display:inline;" alt="Hand Joints Names">

## <a name="hand-mesh-prefab"></a><span data-ttu-id="90f39-117">Prefabbricato mesh mano</span><span class="sxs-lookup"><span data-stu-id="90f39-117">Hand mesh prefab</span></span>

<span data-ttu-id="90f39-118">La mesh mano viene usata se i dati mesh completamente definiti vengono forniti dal dispositivo di rilevamento a mano.</span><span class="sxs-lookup"><span data-stu-id="90f39-118">The hand mesh is used if fully defined mesh data is provided by the hand tracking device.</span></span> <span data-ttu-id="90f39-119">Il rendering della mesh nella prefabbricata viene sostituito dai dati dal dispositivo, quindi è sufficiente una mesh fittizia, ad esempio un cubo.</span><span class="sxs-lookup"><span data-stu-id="90f39-119">The mesh renderable in the prefab is replaced by data from the device, so a dummy mesh such as a cube is sufficient.</span></span> <span data-ttu-id="90f39-120">Il materiale della prefabbricato viene usato per la rete a mano.</span><span class="sxs-lookup"><span data-stu-id="90f39-120">The material of the prefab is used for the hand mesh.</span></span>

<span data-ttu-id="90f39-121"><img src = ".. /images/input-Simulation/MRTK_Core_Input_Hands_ArticulatedHandMesh.png "width =" 350px "Style =" display: Block; " Alt = "visualizzazione Mesh a mano articolata" ></span><span class="sxs-lookup"><span data-stu-id="90f39-121"><img src="../images/input-simulation/MRTK_Core_Input_Hands_ArticulatedHandMesh.png" width="350px"  style="display:block;"alt="Articulated Hand Mesh View"></span></span>

<span data-ttu-id="90f39-122">La visualizzazione della mesh della mano può avere un impatto significativo sulle prestazioni, per questo motivo può essere disabilitata completamente deselezionando l'opzione **Abilita visualizzazione Mesh a mano** .</span><span class="sxs-lookup"><span data-stu-id="90f39-122">Hand mesh display can have a noticeable performance impact, for this reason it can be disabled entirely by unchecking **Enable Hand Mesh Visualization** option.</span></span>

## <a name="hand-visualization-settings"></a><span data-ttu-id="90f39-123">Impostazioni visualizzazione mano</span><span class="sxs-lookup"><span data-stu-id="90f39-123">Hand visualization settings</span></span>

<span data-ttu-id="90f39-124">La mesh mano e le visualizzazioni congiunte a mano possono essere disattivate o attivate tramite l'impostazione delle *modalità di visualizzazione della mesh mano* e le *modalità di visualizzazione congiunte a mano* rispettivamente.</span><span class="sxs-lookup"><span data-stu-id="90f39-124">The hand mesh and hand joint visualizations can be turned off or on via the *Hand Mesh Visualization Modes* setting and *Hand Joint Visualization Modes* respectively.</span></span> <span data-ttu-id="90f39-125">Queste impostazioni sono specifiche della modalità applicazione, vale a dire che è possibile attivare alcune funzionalità durante l'editor (per vedere, ad esempio, le giunzioni con la simulazione in-Editor), mentre le stesse funzionalità sono disattivate quando vengono distribuite nel dispositivo (nelle compilazioni del lettore).</span><span class="sxs-lookup"><span data-stu-id="90f39-125">These settings are application-mode specific, meaning it is possible to turn on some features while in editor (to see joints with in-editor simulation, for example) while having the same features turned off when deployed to device (in player builds).</span></span>

<span data-ttu-id="90f39-126">Si noti che in genere è consigliabile che la visualizzazione congiunta della mano sia attivata nell'editor (in modo che la simulazione in-Editor mostri la posizione dei giunti) e che la visualizzazione congiunta della mano e la visualizzazione della mesh a mano siano disattivate in Player (in quanto comportano un impatto sulle prestazioni).</span><span class="sxs-lookup"><span data-stu-id="90f39-126">Note that it's generally recommended to have hand joint visualization turned on in editor (so that in-editor simulation will show where the hand joints are), and to have both hand joint visualization and hand mesh visualization turned off in player (because they incur a performance hit).</span></span>

## <a name="scripting"></a><span data-ttu-id="90f39-127">Scripting</span><span class="sxs-lookup"><span data-stu-id="90f39-127">Scripting</span></span>

<span data-ttu-id="90f39-128">La posizione e la rotazione possono essere richieste dal sistema di input per ogni singolo giunto di mano come [`MixedRealityPose`](xref:Microsoft.MixedReality.Toolkit.Utilities.MixedRealityPose) .</span><span class="sxs-lookup"><span data-stu-id="90f39-128">Position and rotation can be requested from the input system for each individual hand joint as a [`MixedRealityPose`](xref:Microsoft.MixedReality.Toolkit.Utilities.MixedRealityPose).</span></span>

<span data-ttu-id="90f39-129">In alternativa, il sistema consente l'accesso a [GameObject](https://docs.unity3d.com/ScriptReference/GameObject.html) che seguono le giunzioni.</span><span class="sxs-lookup"><span data-stu-id="90f39-129">Alternatively the system allows access to [GameObjects](https://docs.unity3d.com/ScriptReference/GameObject.html) that follow the joints.</span></span> <span data-ttu-id="90f39-130">Questo può essere utile se un altro GameObject deve tenere traccia di un giunto in modo continuo.</span><span class="sxs-lookup"><span data-stu-id="90f39-130">This can be useful if another GameObject should track a joint continuously.</span></span>

<span data-ttu-id="90f39-131">Le giunzioni disponibili sono elencate nell' [`TrackedHandJoint`](xref:Microsoft.MixedReality.Toolkit.Utilities.TrackedHandJoint) enum.</span><span class="sxs-lookup"><span data-stu-id="90f39-131">Available joints are listed in the [`TrackedHandJoint`](xref:Microsoft.MixedReality.Toolkit.Utilities.TrackedHandJoint) enum.</span></span>

> [!NOTE]
> <span data-ttu-id="90f39-132">L'oggetto misto viene eliminato quando il rilevamento della mano viene perso.</span><span class="sxs-lookup"><span data-stu-id="90f39-132">Joint object are destroyed when hand tracking is lost!</span></span> <span data-ttu-id="90f39-133">Assicurarsi che gli script che usano l'oggetto combinato gestiscano `null` normalmente il caso per evitare errori.</span><span class="sxs-lookup"><span data-stu-id="90f39-133">Make sure that any scripts using the joint object handle the `null` case gracefully to avoid errors!</span></span>

### <a name="accessing-a-given-hand-controller"></a><span data-ttu-id="90f39-134">Accesso a un controller della mano specificato</span><span class="sxs-lookup"><span data-stu-id="90f39-134">Accessing a given hand controller</span></span>

<span data-ttu-id="90f39-135">Un controller della mano specifico è spesso disponibile, ad esempio quando si gestiscono gli eventi di input.</span><span class="sxs-lookup"><span data-stu-id="90f39-135">A specific hand controller is often available, e.g. when handling input events.</span></span> <span data-ttu-id="90f39-136">In questo caso i dati congiunti possono essere richiesti direttamente dal dispositivo, usando l' [`IMixedRealityHand`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHand) interfaccia.</span><span class="sxs-lookup"><span data-stu-id="90f39-136">In this case the joint data can be requested directly from the device, using the [`IMixedRealityHand`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHand) interface.</span></span>

#### <a name="polling-joint-pose-from-controller"></a><span data-ttu-id="90f39-137">Il polling della giunzione dal controller</span><span class="sxs-lookup"><span data-stu-id="90f39-137">Polling joint pose from controller</span></span>

<span data-ttu-id="90f39-138">La [`TryGetJoint`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHand.TryGetJoint*) funzione restituisce `false` se il giunto richiesto non è disponibile per qualche motivo.</span><span class="sxs-lookup"><span data-stu-id="90f39-138">The [`TryGetJoint`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHand.TryGetJoint*) function returns `false` if the requested joint is not available for some reason.</span></span> <span data-ttu-id="90f39-139">In tal caso la richiesta risultante sarà [`MixedRealityPose.ZeroIdentity`](xref:Microsoft.MixedReality.Toolkit.Utilities.MixedRealityPose.ZeroIdentity) .</span><span class="sxs-lookup"><span data-stu-id="90f39-139">In that case the resulting pose will be [`MixedRealityPose.ZeroIdentity`](xref:Microsoft.MixedReality.Toolkit.Utilities.MixedRealityPose.ZeroIdentity).</span></span>

```c#
public void OnSourceDetected(SourceStateEventData eventData)
{
  var hand = eventData.Controller as IMixedRealityHand;
  if (hand != null)
  {
    if (hand.TryGetJoint(TrackedHandJoint.IndexTip, out MixedRealityPose jointPose)
    {
      // ...
    }
  }
}
```

#### <a name="joint-transform-from-hand-visualizer"></a><span data-ttu-id="90f39-140">Trasformazione congiunta dal Visualizzatore della mano</span><span class="sxs-lookup"><span data-stu-id="90f39-140">Joint transform from hand visualizer</span></span>

<span data-ttu-id="90f39-141">È possibile richiedere oggetti Uniti dal [Visualizzatore del controller](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityController.Visualizer).</span><span class="sxs-lookup"><span data-stu-id="90f39-141">Joint objects can be requested from the [controller visualizer](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityController.Visualizer).</span></span>

```c#
public void OnSourceDetected(SourceStateEventData eventData)
{
  var handVisualizer = eventData.Controller.Visualizer as IMixedRealityHandVisualizer;
  if (handVisualizer != null)
  {
    if (handVisualizer.TryGetJointTransform(TrackedHandJoint.IndexTip, out Transform jointTransform)
    {
      // ...
    }
  }
}
```

### <a name="simplified-joint-data-access"></a><span data-ttu-id="90f39-142">Accesso combinato ai dati semplificato</span><span class="sxs-lookup"><span data-stu-id="90f39-142">Simplified joint data access</span></span>

<span data-ttu-id="90f39-143">Se non viene specificato alcun controller specifico, vengono fornite le classi di utilità per accedere facilmente ai dati congiunti a mano.</span><span class="sxs-lookup"><span data-stu-id="90f39-143">If no specific controller is given then utility classes are provided for convenient access to hand joint data.</span></span> <span data-ttu-id="90f39-144">Queste funzioni richiedono dati comuni dal primo dispositivo a disposizione attualmente rilevato.</span><span class="sxs-lookup"><span data-stu-id="90f39-144">These functions request joint data from the first available hand device currently tracked.</span></span>

#### <a name="polling-joint-pose-from-handjointutils"></a><span data-ttu-id="90f39-145">Polling di joint join da HandJointUtils</span><span class="sxs-lookup"><span data-stu-id="90f39-145">Polling joint pose from HandJointUtils</span></span>

<span data-ttu-id="90f39-146">[`HandJointUtils`](xref:Microsoft.MixedReality.Toolkit.Input.HandJointUtils) è una classe statica che esegue una query sul primo dispositivo a mano attiva.</span><span class="sxs-lookup"><span data-stu-id="90f39-146">[`HandJointUtils`](xref:Microsoft.MixedReality.Toolkit.Input.HandJointUtils) is a static class that queries the first active hand device.</span></span>

```c#
if (HandJointUtils.TryGetJointPose(TrackedHandJoint.IndexTip, Handedness.Right, out MixedRealityPose pose))
{
    // ...
}
```

#### <a name="joint-transform-from-hand-joint-service"></a><span data-ttu-id="90f39-147">Trasformazione congiunta dal servizio combinato di mano</span><span class="sxs-lookup"><span data-stu-id="90f39-147">Joint transform from hand joint service</span></span>

<span data-ttu-id="90f39-148">[`IMixedRealityHandJointService`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHandJointService) mantiene un set permanente di [GameObject](https://docs.unity3d.com/ScriptReference/GameObject.html) per il rilevamento delle giunzioni.</span><span class="sxs-lookup"><span data-stu-id="90f39-148">[`IMixedRealityHandJointService`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHandJointService) keeps a persistent set of [GameObjects](https://docs.unity3d.com/ScriptReference/GameObject.html) for tracking joints.</span></span>

```c#
var handJointService = CoreServices.GetInputSystemDataProvider<IMixedRealityHandJointService>();
if (handJointService != null)
{
    Transform jointTransform = handJointService.RequestJointTransform(TrackedHandJoint.IndexTip, Handedness.Right);
    // ...
}
```

### <a name="hand-tracking-events"></a><span data-ttu-id="90f39-149">Eventi di rilevamento della mano</span><span class="sxs-lookup"><span data-stu-id="90f39-149">Hand tracking events</span></span>

<span data-ttu-id="90f39-150">Il sistema di input fornisce anche gli eventi, se non è consigliabile eseguire il polling dei dati direttamente dai controller.</span><span class="sxs-lookup"><span data-stu-id="90f39-150">The input system provides events as well, if polling data from controllers directly is not desirable.</span></span>

#### <a name="joint-events"></a><span data-ttu-id="90f39-151">Eventi comuni</span><span class="sxs-lookup"><span data-stu-id="90f39-151">Joint events</span></span>

<span data-ttu-id="90f39-152">[`IMixedRealityHandJointHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHandJointHandler) gestisce gli aggiornamenti delle posizioni congiunte.</span><span class="sxs-lookup"><span data-stu-id="90f39-152">[`IMixedRealityHandJointHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHandJointHandler) handles updates of joint positions.</span></span>

```c#
public class MyHandJointEventHandler : IMixedRealityHandJointHandler
{
    public Handedness myHandedness;

    void IMixedRealityHandJointHandler.OnHandJointsUpdated(InputEventData<IDictionary<TrackedHandJoint, MixedRealityPose>> eventData)
    {
        if (eventData.Handedness == myHandedness)
        {
            if (eventData.InputData.TryGetValue(TrackedHandJoint.IndexTip, out MixedRealityPose pose))
            {
                // ...
            }
        }
    }
}
```

#### <a name="mesh-events"></a><span data-ttu-id="90f39-153">Eventi Mesh</span><span class="sxs-lookup"><span data-stu-id="90f39-153">Mesh events</span></span>

<span data-ttu-id="90f39-154">[`IMixedRealityHandMeshHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHandMeshHandler) gestisce le modifiche della mesh a mano articolata.</span><span class="sxs-lookup"><span data-stu-id="90f39-154">[`IMixedRealityHandMeshHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHandMeshHandler) handles changes of the articulated hand mesh.</span></span>

<span data-ttu-id="90f39-155">Si noti che le mesh della mano non sono abilitate per impostazione predefinita.</span><span class="sxs-lookup"><span data-stu-id="90f39-155">Note that hand meshes are not enabled by default.</span></span>

```c#
public class MyHandMeshEventHandler : IMixedRealityHandMeshHandler
{
    public Handedness myHandedness;
    public Mesh myMesh;

    public void OnHandMeshUpdated(InputEventData<HandMeshInfo> eventData)
    {
        if (eventData.Handedness == myHandedness)
        {
            myMesh.vertices = eventData.InputData.vertices;
            myMesh.normals = eventData.InputData.normals;
            myMesh.triangles = eventData.InputData.triangles;

            if (eventData.InputData.uvs != null && eventData.InputData.uvs.Length > 0)
            {
                myMesh.uv = eventData.InputData.uvs;
            }

            // ...
        }
    }
}
```

## <a name="known-issues"></a><span data-ttu-id="90f39-156">Problemi noti</span><span class="sxs-lookup"><span data-stu-id="90f39-156">Known issues</span></span>

### <a name="net-native"></a><span data-ttu-id="90f39-157">.NET Native</span><span class="sxs-lookup"><span data-stu-id="90f39-157">.NET Native</span></span>

<span data-ttu-id="90f39-158">Attualmente esiste un problema noto relativo alle compilazioni Master con il back-end .NET.</span><span class="sxs-lookup"><span data-stu-id="90f39-158">There is currently a known issue with Master builds using the .NET backend.</span></span> <span data-ttu-id="90f39-159">In .NET Native `IInspectable` non è possibile effettuare il marshalling dei puntatori dal codice nativo al codice gestito utilizzando `Marshal.GetObjectForIUnknown` .</span><span class="sxs-lookup"><span data-stu-id="90f39-159">In .NET Native, `IInspectable` pointers cannot be marshaled from native to managed code using `Marshal.GetObjectForIUnknown`.</span></span> <span data-ttu-id="90f39-160">Il MRTK lo usa per ottenere l'oggetto per `SpatialCoordinateSystem` ricevere dati sulla mano e sugli occhi dalla piattaforma.</span><span class="sxs-lookup"><span data-stu-id="90f39-160">The MRTK uses this to obtain the `SpatialCoordinateSystem` in order to receive hand and eye data from the platform.</span></span>

<span data-ttu-id="90f39-161">È stata fornita una soluzione alternativa per questo problema nel [repository native Mixed Reality Toolkit](https://github.com/microsoft/MixedRealityToolkit/tree/master/DotNetNativeWorkaround).</span><span class="sxs-lookup"><span data-stu-id="90f39-161">We've provided DLL source as a workaround for this issue, in [the native Mixed Reality Toolkit repo](https://github.com/microsoft/MixedRealityToolkit/tree/master/DotNetNativeWorkaround).</span></span> <span data-ttu-id="90f39-162">Seguire le istruzioni contenute nel file Leggimi e copiare i file binari risultanti in una cartella dei plug-in degli asset Unity.</span><span class="sxs-lookup"><span data-stu-id="90f39-162">Please follow the instructions in the README there and copy the resulting binaries into a Plugins folder in your Unity assets.</span></span> <span data-ttu-id="90f39-163">Successivamente, lo script WindowsMixedRealityUtilities fornito in MRTK risolverà la soluzione alternativa.</span><span class="sxs-lookup"><span data-stu-id="90f39-163">After that, the WindowsMixedRealityUtilities script provided in the MRTK will resolve the workaround for you.</span></span>

<span data-ttu-id="90f39-164">Se si vuole creare una DLL personalizzata o includere questa soluzione alternativa in una esistente, il nucleo della soluzione alternativa è:</span><span class="sxs-lookup"><span data-stu-id="90f39-164">If you want to create your own DLL or include this workaround in an existing one, the core of the workaround is:</span></span>

```c++
extern "C" __declspec(dllexport) void __stdcall MarshalIInspectable(IUnknown* nativePtr, IUnknown** inspectable)
{
    *inspectable = nativePtr;
}
```

<span data-ttu-id="90f39-165">E il suo uso nel codice C# Unity:</span><span class="sxs-lookup"><span data-stu-id="90f39-165">And its use in your C# Unity code:</span></span>

```c#
[DllImport("DotNetNativeWorkaround.dll", EntryPoint = "MarshalIInspectable")]
private static extern void GetSpatialCoordinateSystem(IntPtr nativePtr, out SpatialCoordinateSystem coordinateSystem);

private static SpatialCoordinateSystem GetSpatialCoordinateSystem(IntPtr nativePtr)
{
    try
    {
        GetSpatialCoordinateSystem(nativePtr, out SpatialCoordinateSystem coordinateSystem);
        return coordinateSystem;
    }
    catch
    {
        UnityEngine.Debug.LogError("Call to the DotNetNativeWorkaround plug-in failed. The plug-in is required for correct behavior when using .NET Native compilation");
        return Marshal.GetObjectForIUnknown(nativePtr) as SpatialCoordinateSystem;
    }
}
```

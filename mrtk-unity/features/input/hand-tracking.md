---
title: Tracciamento manuale
description: Documentazione su come usare HandTracking in MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, tracciamento manuale,
ms.openlocfilehash: 6cd55bc76d9fba42640954bcbf50e62f66454a94
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143358"
---
# <a name="hand-tracking"></a><span data-ttu-id="3bdd4-104">Tracciamento mano</span><span class="sxs-lookup"><span data-stu-id="3bdd4-104">Hand tracking</span></span>

## <a name="hand-tracking-profile"></a><span data-ttu-id="3bdd4-105">Profilo di tracciamento manuale</span><span class="sxs-lookup"><span data-stu-id="3bdd4-105">Hand tracking profile</span></span>

<span data-ttu-id="3bdd4-106">Il _profilo Di rilevamento manuale_ si trova nel profilo del sistema di _input_.</span><span class="sxs-lookup"><span data-stu-id="3bdd4-106">The _Hand Tracking profile_ is found under the _Input System profile_.</span></span> <span data-ttu-id="3bdd4-107">Contiene le impostazioni per la personalizzazione della rappresentazione manuale.</span><span class="sxs-lookup"><span data-stu-id="3bdd4-107">It contains settings for customizing hand representation.</span></span>

<img src="../images/input/HandTrackingProfile.png" width="650px" alt="Hand Tracking Profile" style="display:block;">

## <a name="joint-prefabs"></a><span data-ttu-id="3bdd4-108">Prefab congiunti</span><span class="sxs-lookup"><span data-stu-id="3bdd4-108">Joint prefabs</span></span>

<span data-ttu-id="3bdd4-109">I prefab congiunti vengono visualizzato usando prefab semplici.</span><span class="sxs-lookup"><span data-stu-id="3bdd4-109">Joint prefabs are visualized using simple prefabs.</span></span> <span data-ttu-id="3bdd4-110">Le _giunzioni_ Palm _e Index Finger_ sono di particolare importanza e hanno il proprio prefab, mentre tutte le altre giunzioni condividono lo stesso prefab.</span><span class="sxs-lookup"><span data-stu-id="3bdd4-110">The _Palm_ and _Index Finger_ joints are of special importance and have their own prefab, while all other joints share the same prefab.</span></span>

<span data-ttu-id="3bdd4-111">Per impostazione predefinita, i prefab delle giunzione della mano sono primitive geometriche semplici.</span><span class="sxs-lookup"><span data-stu-id="3bdd4-111">By default the hand joint prefabs are simple geometric primitives.</span></span> <span data-ttu-id="3bdd4-112">Possono essere sostituiti, se lo si desidera.</span><span class="sxs-lookup"><span data-stu-id="3bdd4-112">These can be replaced if desired.</span></span> <span data-ttu-id="3bdd4-113">Se non viene specificato alcun prefab, vengono creati [gameobject](https://docs.unity3d.com/ScriptReference/GameObject.html) vuoti.</span><span class="sxs-lookup"><span data-stu-id="3bdd4-113">If no prefab is specified at all, empty [GameObjects](https://docs.unity3d.com/ScriptReference/GameObject.html) are created instead.</span></span>

> [!WARNING]
> <span data-ttu-id="3bdd4-114">Evitare di usare script complessi o un rendering costoso nei prefab congiunti, poiché gli oggetti congiunti vengono trasformati in ogni frame e possono avere un costo significativo per le prestazioni.</span><span class="sxs-lookup"><span data-stu-id="3bdd4-114">Avoid using complex scripts or expensive rendering in joint prefabs, since joint objects are transformed on every frame and can have significant performance cost!</span></span>

<span data-ttu-id="3bdd4-115">Rappresentazione predefinita delle giunzione della mano</span><span class="sxs-lookup"><span data-stu-id="3bdd4-115">Default Hand Joint Representation</span></span> |  <span data-ttu-id="3bdd4-116">Etichette congiunte</span><span class="sxs-lookup"><span data-stu-id="3bdd4-116">Joint Labels</span></span>
:-------------------------:|:-------------------------:
<img src="../images/input-simulation/ArticulatedHandJoints.png" height="300px" alt="Articulated hand joints"  style="display:inline;">  |  <img src="../images/input-simulation/MRTK_Core_Input_Hands_JointNames.png" height="300px" alt="Input Hand joints"  style="display:inline;">

## <a name="hand-mesh-prefab"></a><span data-ttu-id="3bdd4-117">Prefab della mesh manuale</span><span class="sxs-lookup"><span data-stu-id="3bdd4-117">Hand mesh prefab</span></span>

<span data-ttu-id="3bdd4-118">La mesh manuale viene usata se i dati della mesh completamente definiti vengono forniti dal dispositivo di rilevamento manuale.</span><span class="sxs-lookup"><span data-stu-id="3bdd4-118">The hand mesh is used if fully defined mesh data is provided by the hand tracking device.</span></span> <span data-ttu-id="3bdd4-119">La mesh di cui è possibile eseguire il rendering nel prefab viene sostituita dai dati del dispositivo, quindi è sufficiente una mesh fittizia, ad esempio un cubo.</span><span class="sxs-lookup"><span data-stu-id="3bdd4-119">The mesh renderable in the prefab is replaced by data from the device, so a dummy mesh such as a cube is sufficient.</span></span> <span data-ttu-id="3bdd4-120">Il materiale del prefab viene usato per la mesh manuale.</span><span class="sxs-lookup"><span data-stu-id="3bdd4-120">The material of the prefab is used for the hand mesh.</span></span>

<img src="../images/input-simulation/MRTK_Core_Input_Hands_ArticulatedHandMesh.png" width="350px" alt="Input Hand Mesh"  style="display:block;">

<span data-ttu-id="3bdd4-121">La visualizzazione della mesh manuale può avere un impatto significativo sulle prestazioni, per questo motivo può essere disabilitata completamente deselezionando l'opzione **Abilita visualizzazione mesh** manuale.</span><span class="sxs-lookup"><span data-stu-id="3bdd4-121">Hand mesh display can have a noticeable performance impact, for this reason it can be disabled entirely by unchecking **Enable Hand Mesh Visualization** option.</span></span>

## <a name="hand-visualization-settings"></a><span data-ttu-id="3bdd4-122">Impostazioni di visualizzazione manuale</span><span class="sxs-lookup"><span data-stu-id="3bdd4-122">Hand visualization settings</span></span>

<span data-ttu-id="3bdd4-123">Le visualizzazioni della mesh mano e delle giunzioni delle mani possono essere disattivate o attivate rispettivamente tramite l'impostazione *Hand Mesh Visualization Modes* (Modalità di visualizzazione della mesh manuale) e Hand Joint Visualization Modes (Modalità di visualizzazione *mano* giunzione).</span><span class="sxs-lookup"><span data-stu-id="3bdd4-123">The hand mesh and hand joint visualizations can be turned off or on via the *Hand Mesh Visualization Modes* setting and *Hand Joint Visualization Modes* respectively.</span></span> <span data-ttu-id="3bdd4-124">Queste impostazioni sono specifiche della modalità applicazione, vale a dire che è possibile attivare alcune funzionalità nell'editor (per visualizzare i giunzioni con la simulazione nell'editor, ad esempio) e avere le stesse funzionalità disattivate quando vengono distribuite nel dispositivo (nelle build del lettore).</span><span class="sxs-lookup"><span data-stu-id="3bdd4-124">These settings are application-mode specific, meaning it is possible to turn on some features while in editor (to see joints with in-editor simulation, for example) while having the same features turned off when deployed to device (in player builds).</span></span>

<span data-ttu-id="3bdd4-125">Si noti che in genere è consigliabile che la visualizzazione con giunzione della mano sia attivata nell'editor (in modo che la simulazione nell'editor mostri dove si trova la giunzione della mano) e che la visualizzazione delle giunzioni delle mani e la visualizzazione della mesh della mano siano disattivate nel lettore (perché comportano un miglioramento delle prestazioni).</span><span class="sxs-lookup"><span data-stu-id="3bdd4-125">Note that it's generally recommended to have hand joint visualization turned on in editor (so that in-editor simulation will show where the hand joints are), and to have both hand joint visualization and hand mesh visualization turned off in player (because they incur a performance hit).</span></span>

## <a name="scripting"></a><span data-ttu-id="3bdd4-126">Scripting</span><span class="sxs-lookup"><span data-stu-id="3bdd4-126">Scripting</span></span>

<span data-ttu-id="3bdd4-127">La posizione e la rotazione possono essere richieste dal sistema di input per ogni singola giunzione della mano come [`MixedRealityPose`](xref:Microsoft.MixedReality.Toolkit.Utilities.MixedRealityPose) .</span><span class="sxs-lookup"><span data-stu-id="3bdd4-127">Position and rotation can be requested from the input system for each individual hand joint as a [`MixedRealityPose`](xref:Microsoft.MixedReality.Toolkit.Utilities.MixedRealityPose).</span></span>

<span data-ttu-id="3bdd4-128">In alternativa, il sistema consente [l'accesso ai GameObject](https://docs.unity3d.com/ScriptReference/GameObject.html) che seguono le giunzioni.</span><span class="sxs-lookup"><span data-stu-id="3bdd4-128">Alternatively the system allows access to [GameObjects](https://docs.unity3d.com/ScriptReference/GameObject.html) that follow the joints.</span></span> <span data-ttu-id="3bdd4-129">Ciò può essere utile se un altro GameObject deve tenere traccia continuamente di un congiunto.</span><span class="sxs-lookup"><span data-stu-id="3bdd4-129">This can be useful if another GameObject should track a joint continuously.</span></span>

<span data-ttu-id="3bdd4-130">Le giunzioni disponibili sono elencate [`TrackedHandJoint`](xref:Microsoft.MixedReality.Toolkit.Utilities.TrackedHandJoint) nell'enumerazione .</span><span class="sxs-lookup"><span data-stu-id="3bdd4-130">Available joints are listed in the [`TrackedHandJoint`](xref:Microsoft.MixedReality.Toolkit.Utilities.TrackedHandJoint) enum.</span></span>

> [!NOTE]
> <span data-ttu-id="3bdd4-131">L'oggetto congiunto viene eliminato quando si perde il tracciamento delle mani.</span><span class="sxs-lookup"><span data-stu-id="3bdd4-131">Joint object are destroyed when hand tracking is lost!</span></span> <span data-ttu-id="3bdd4-132">Assicurarsi che tutti gli script che usano l'oggetto congiunto gestino correttamente il `null` caso per evitare errori.</span><span class="sxs-lookup"><span data-stu-id="3bdd4-132">Make sure that any scripts using the joint object handle the `null` case gracefully to avoid errors!</span></span>

### <a name="accessing-a-given-hand-controller"></a><span data-ttu-id="3bdd4-133">Accesso a un determinato controller della mano</span><span class="sxs-lookup"><span data-stu-id="3bdd4-133">Accessing a given hand controller</span></span>

<span data-ttu-id="3bdd4-134">Spesso è disponibile un controller della mano specifico, ad esempio durante la gestione degli eventi di input.</span><span class="sxs-lookup"><span data-stu-id="3bdd4-134">A specific hand controller is often available, e.g. when handling input events.</span></span> <span data-ttu-id="3bdd4-135">In questo caso i dati congiunti possono essere richiesti direttamente dal dispositivo, usando [`IMixedRealityHand`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHand) l'interfaccia .</span><span class="sxs-lookup"><span data-stu-id="3bdd4-135">In this case the joint data can be requested directly from the device, using the [`IMixedRealityHand`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHand) interface.</span></span>

#### <a name="polling-joint-pose-from-controller"></a><span data-ttu-id="3bdd4-136">Posizione congiunta di polling dal controller</span><span class="sxs-lookup"><span data-stu-id="3bdd4-136">Polling joint pose from controller</span></span>

<span data-ttu-id="3bdd4-137">La [`TryGetJoint`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHand.TryGetJoint*) funzione restituisce se il `false` congiunto richiesto non è disponibile per qualche motivo.</span><span class="sxs-lookup"><span data-stu-id="3bdd4-137">The [`TryGetJoint`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHand.TryGetJoint*) function returns `false` if the requested joint is not available for some reason.</span></span> <span data-ttu-id="3bdd4-138">In tal caso, la posizione risultante sarà [`MixedRealityPose.ZeroIdentity`](xref:Microsoft.MixedReality.Toolkit.Utilities.MixedRealityPose.ZeroIdentity) .</span><span class="sxs-lookup"><span data-stu-id="3bdd4-138">In that case the resulting pose will be [`MixedRealityPose.ZeroIdentity`](xref:Microsoft.MixedReality.Toolkit.Utilities.MixedRealityPose.ZeroIdentity).</span></span>

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

#### <a name="joint-transform-from-hand-visualizer"></a><span data-ttu-id="3bdd4-139">Trasformazione congiunta dal visualizzatore mano</span><span class="sxs-lookup"><span data-stu-id="3bdd4-139">Joint transform from hand visualizer</span></span>

<span data-ttu-id="3bdd4-140">Gli oggetti congiunti possono essere richiesti dal [visualizzatore controller](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityController.Visualizer).</span><span class="sxs-lookup"><span data-stu-id="3bdd4-140">Joint objects can be requested from the [controller visualizer](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityController.Visualizer).</span></span>

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

### <a name="simplified-joint-data-access"></a><span data-ttu-id="3bdd4-141">Accesso semplificato ai dati congiunti</span><span class="sxs-lookup"><span data-stu-id="3bdd4-141">Simplified joint data access</span></span>

<span data-ttu-id="3bdd4-142">Se non viene specificato alcun controller specifico, le classi di utilità vengono fornite per l'accesso pratico ai dati congiunti mano.</span><span class="sxs-lookup"><span data-stu-id="3bdd4-142">If no specific controller is given then utility classes are provided for convenient access to hand joint data.</span></span> <span data-ttu-id="3bdd4-143">Queste funzioni richiedono dati congiunti dal primo dispositivo a mano disponibile attualmente monitorato.</span><span class="sxs-lookup"><span data-stu-id="3bdd4-143">These functions request joint data from the first available hand device currently tracked.</span></span>

#### <a name="polling-joint-pose-from-handjointutils"></a><span data-ttu-id="3bdd4-144">Posizione congiunta di polling da HandJointUtils</span><span class="sxs-lookup"><span data-stu-id="3bdd4-144">Polling joint pose from HandJointUtils</span></span>

<span data-ttu-id="3bdd4-145">[`HandJointUtils`](xref:Microsoft.MixedReality.Toolkit.Input.HandJointUtils) è una classe statica che esegue una query sul primo dispositivo a mano attivo.</span><span class="sxs-lookup"><span data-stu-id="3bdd4-145">[`HandJointUtils`](xref:Microsoft.MixedReality.Toolkit.Input.HandJointUtils) is a static class that queries the first active hand device.</span></span>

```c#
if (HandJointUtils.TryGetJointPose(TrackedHandJoint.IndexTip, Handedness.Right, out MixedRealityPose pose))
{
    // ...
}
```

#### <a name="joint-transform-from-hand-joint-service"></a><span data-ttu-id="3bdd4-146">Trasformazione congiunta dal servizio hand joint</span><span class="sxs-lookup"><span data-stu-id="3bdd4-146">Joint transform from hand joint service</span></span>

<span data-ttu-id="3bdd4-147">[`IMixedRealityHandJointService`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHandJointService) mantiene un set persistente [di GameObject per tenere](https://docs.unity3d.com/ScriptReference/GameObject.html) traccia delle giunzioni.</span><span class="sxs-lookup"><span data-stu-id="3bdd4-147">[`IMixedRealityHandJointService`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHandJointService) keeps a persistent set of [GameObjects](https://docs.unity3d.com/ScriptReference/GameObject.html) for tracking joints.</span></span>

```c#
var handJointService = CoreServices.GetInputSystemDataProvider<IMixedRealityHandJointService>();
if (handJointService != null)
{
    Transform jointTransform = handJointService.RequestJointTransform(TrackedHandJoint.IndexTip, Handedness.Right);
    // ...
}
```

### <a name="hand-tracking-events"></a><span data-ttu-id="3bdd4-148">Eventi di rilevamento manuale</span><span class="sxs-lookup"><span data-stu-id="3bdd4-148">Hand tracking events</span></span>

<span data-ttu-id="3bdd4-149">Anche il sistema di input fornisce eventi, se il polling diretto dei dati dai controller non è consigliabile.</span><span class="sxs-lookup"><span data-stu-id="3bdd4-149">The input system provides events as well, if polling data from controllers directly is not desirable.</span></span>

#### <a name="joint-events"></a><span data-ttu-id="3bdd4-150">Eventi congiunti</span><span class="sxs-lookup"><span data-stu-id="3bdd4-150">Joint events</span></span>

<span data-ttu-id="3bdd4-151">[`IMixedRealityHandJointHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHandJointHandler) gestisce gli aggiornamenti delle posizioni congiunte.</span><span class="sxs-lookup"><span data-stu-id="3bdd4-151">[`IMixedRealityHandJointHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHandJointHandler) handles updates of joint positions.</span></span>

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

#### <a name="mesh-events"></a><span data-ttu-id="3bdd4-152">Eventi mesh</span><span class="sxs-lookup"><span data-stu-id="3bdd4-152">Mesh events</span></span>

<span data-ttu-id="3bdd4-153">[`IMixedRealityHandMeshHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHandMeshHandler) gestisce le modifiche della mesh articolata della mano.</span><span class="sxs-lookup"><span data-stu-id="3bdd4-153">[`IMixedRealityHandMeshHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHandMeshHandler) handles changes of the articulated hand mesh.</span></span>

<span data-ttu-id="3bdd4-154">Si noti che le mesh a mano non sono abilitate per impostazione predefinita.</span><span class="sxs-lookup"><span data-stu-id="3bdd4-154">Note that hand meshes are not enabled by default.</span></span>

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

## <a name="known-issues"></a><span data-ttu-id="3bdd4-155">Problemi noti</span><span class="sxs-lookup"><span data-stu-id="3bdd4-155">Known issues</span></span>

### <a name="net-native"></a><span data-ttu-id="3bdd4-156">.NET Native</span><span class="sxs-lookup"><span data-stu-id="3bdd4-156">.NET Native</span></span>

<span data-ttu-id="3bdd4-157">Esiste attualmente un problema noto con le compilazioni master che usano il back-end .NET.</span><span class="sxs-lookup"><span data-stu-id="3bdd4-157">There is currently a known issue with Master builds using the .NET backend.</span></span> <span data-ttu-id="3bdd4-158">In .NET Native, non è possibile effettuare il marshalling dei puntatori da codice nativo `IInspectable` a codice gestito usando `Marshal.GetObjectForIUnknown` .</span><span class="sxs-lookup"><span data-stu-id="3bdd4-158">In .NET Native, `IInspectable` pointers cannot be marshaled from native to managed code using `Marshal.GetObjectForIUnknown`.</span></span> <span data-ttu-id="3bdd4-159">MrTK usa questo oggetto per ottenere per ricevere i dati relativi a mani `SpatialCoordinateSystem` e occhi dalla piattaforma.</span><span class="sxs-lookup"><span data-stu-id="3bdd4-159">The MRTK uses this to obtain the `SpatialCoordinateSystem` in order to receive hand and eye data from the platform.</span></span>

<span data-ttu-id="3bdd4-160">L'origine DLL è stata fornita come soluzione alternativa per questo problema, nel [repo nativo di Mixed Reality Toolkit.](https://github.com/microsoft/MixedRealityToolkit/tree/master/DotNetNativeWorkaround)</span><span class="sxs-lookup"><span data-stu-id="3bdd4-160">We've provided DLL source as a workaround for this issue, in [the native Mixed Reality Toolkit repo](https://github.com/microsoft/MixedRealityToolkit/tree/master/DotNetNativeWorkaround).</span></span> <span data-ttu-id="3bdd4-161">Seguire le istruzioni nel file LEGGIMI e copiare i file binari risultanti in una cartella Plugins negli asset di Unity.</span><span class="sxs-lookup"><span data-stu-id="3bdd4-161">Please follow the instructions in the README there and copy the resulting binaries into a Plugins folder in your Unity assets.</span></span> <span data-ttu-id="3bdd4-162">Successivamente, lo script WindowsMixedRealityUtilities fornito in MRTK risolverà automaticamente la soluzione alternativa.</span><span class="sxs-lookup"><span data-stu-id="3bdd4-162">After that, the WindowsMixedRealityUtilities script provided in the MRTK will resolve the workaround for you.</span></span>

<span data-ttu-id="3bdd4-163">Se si vuole creare una DLL personalizzata o includere questa soluzione alternativa in una esistente, il nucleo della soluzione alternativa è:</span><span class="sxs-lookup"><span data-stu-id="3bdd4-163">If you want to create your own DLL or include this workaround in an existing one, the core of the workaround is:</span></span>

```c++
extern "C" __declspec(dllexport) void __stdcall MarshalIInspectable(IUnknown* nativePtr, IUnknown** inspectable)
{
    *inspectable = nativePtr;
}
```

<span data-ttu-id="3bdd4-164">E il suo uso nel codice C# Unity:</span><span class="sxs-lookup"><span data-stu-id="3bdd4-164">And its use in your C# Unity code:</span></span>

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

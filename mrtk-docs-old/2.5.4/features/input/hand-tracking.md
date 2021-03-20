---
title: HandTracking
description: Documentazione su come usare HandTracking in MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, rilevamento manuale,
ms.openlocfilehash: 958c148e115624cf76a9ac1b5399864fb2269c9e
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2021
ms.locfileid: "104685354"
---
# <a name="hand-tracking"></a>Tracciamento mano

## <a name="hand-tracking-profile"></a>Profilo di rilevamento mano

Il _profilo di rilevamento della mano_ è disponibile nel _profilo di sistema di input_. Contiene le impostazioni per la personalizzazione della rappresentazione manuale.

<img src="../images/input/HandTrackingProfile.png" width="650px" alt="Hand Tracking Profile" style="display:block;">

## <a name="joint-prefabs"></a>Prefabbricati comuni

I prefabbricati Uniti vengono visualizzati usando semplici prefabbricati. Le giunzioni _Palm_ e _index finger_ sono di particolare importanza e hanno una propria precostruzione, mentre tutte le altre articolazioni condividono la stessa prefabbricata.

Per impostazione predefinita, i prefabbricati di join sono semplici primitive geometriche. Se lo si desidera, è possibile sostituirli. Se non viene specificata alcuna prefabbricata, vengono invece creati [GameObject](href:https://docs.unity3d.com/ScriptReference/GameObject.html) vuoti.

> [!WARNING]
> Evitare l'uso di script complessi o il rendering costoso in prefabbricati comuni, poiché gli oggetti combinati vengono trasformati in ogni frame e possono avere un costo significativo per le prestazioni.

Rappresentazione congiunta della mano predefinita |  Etichette congiunte
:-------------------------:|:-------------------------:
<img src="../images/input-simulation/ArticulatedHandJoints.png" height="300px" alt="Articulated hand joints"  style="display:inline;">  |  <img src="../images/input-simulation/MRTK_Core_Input_Hands_JointNames.png" height="300px" alt="Input Hand joints"  style="display:inline;">

## <a name="hand-mesh-prefab"></a>Prefabbricato mesh mano

La mesh mano viene usata se i dati mesh completamente definiti vengono forniti dal dispositivo di rilevamento a mano. Il rendering della mesh nella prefabbricata viene sostituito dai dati dal dispositivo, quindi è sufficiente una mesh fittizia, ad esempio un cubo. Il materiale della prefabbricato viene usato per la rete a mano.

<img src="../images/input-simulation/MRTK_Core_Input_Hands_ArticulatedHandMesh.png" width="350px" alt="Input Hand Mesh"  style="display:block;">

La visualizzazione della mesh della mano può avere un impatto significativo sulle prestazioni, per questo motivo può essere disabilitata completamente deselezionando l'opzione **Abilita visualizzazione Mesh a mano** .

## <a name="hand-visualization-settings"></a>Impostazioni visualizzazione mano

La mesh mano e le visualizzazioni congiunte a mano possono essere disattivate o attivate tramite l'impostazione delle *modalità di visualizzazione della mesh mano* e le *modalità di visualizzazione congiunte a mano* rispettivamente. Queste impostazioni sono specifiche della modalità applicazione, vale a dire che è possibile attivare alcune funzionalità durante l'editor (per vedere, ad esempio, le giunzioni con la simulazione in-Editor), mentre le stesse funzionalità sono disattivate quando vengono distribuite nel dispositivo (nelle compilazioni del lettore).

Si noti che in genere è consigliabile che la visualizzazione congiunta della mano sia attivata nell'editor (in modo che la simulazione in-Editor mostri la posizione dei giunti) e che la visualizzazione congiunta della mano e la visualizzazione della mesh a mano siano disattivate in Player (in quanto comportano un impatto sulle prestazioni).

## <a name="scripting"></a>Scripting

La posizione e la rotazione possono essere richieste dal sistema di input per ogni singolo giunto di mano come [`MixedRealityPose`](xref:Microsoft.MixedReality.Toolkit.Utilities.MixedRealityPose) .

In alternativa, il sistema consente l'accesso a [GameObject](https://docs.unity3d.com/ScriptReference/GameObject.html) che seguono le giunzioni. Questo può essere utile se un altro GameObject deve tenere traccia di un giunto in modo continuo.

Le giunzioni disponibili sono elencate nell' [`TrackedHandJoint`](xref:Microsoft.MixedReality.Toolkit.Utilities.TrackedHandJoint) enum.

> [!NOTE]
> L'oggetto misto viene eliminato quando il rilevamento della mano viene perso. Assicurarsi che gli script che usano l'oggetto combinato gestiscano `null` normalmente il caso per evitare errori.

### <a name="accessing-a-given-hand-controller"></a>Accesso a un controller della mano specificato

Un controller della mano specifico è spesso disponibile, ad esempio quando si gestiscono gli eventi di input. In questo caso i dati congiunti possono essere richiesti direttamente dal dispositivo, usando l' [`IMixedRealityHand`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHand) interfaccia.

#### <a name="polling-joint-pose-from-controller"></a>Il polling della giunzione dal controller

La [`TryGetJoint`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHand.TryGetJoint*) funzione restituisce `false` se il giunto richiesto non è disponibile per qualche motivo. In tal caso la richiesta risultante sarà [`MixedRealityPose.ZeroIdentity`](xref:Microsoft.MixedReality.Toolkit.Utilities.MixedRealityPose.ZeroIdentity) .

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

#### <a name="joint-transform-from-hand-visualizer"></a>Trasformazione congiunta dal Visualizzatore della mano

È possibile richiedere oggetti Uniti dal [Visualizzatore del controller](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityController.Visualizer).

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

### <a name="simplified-joint-data-access"></a>Accesso combinato ai dati semplificato

Se non viene specificato alcun controller specifico, vengono fornite le classi di utilità per accedere facilmente ai dati congiunti a mano. Queste funzioni richiedono dati comuni dal primo dispositivo a disposizione attualmente rilevato.

#### <a name="polling-joint-pose-from-handjointutils"></a>Polling di joint join da HandJointUtils

[`HandJointUtils`](xref:Microsoft.MixedReality.Toolkit.Input.HandJointUtils) è una classe statica che esegue una query sul primo dispositivo a mano attiva.

```c#
if (HandJointUtils.TryGetJointPose(TrackedHandJoint.IndexTip, Handedness.Right, out MixedRealityPose pose))
{
    // ...
}
```

#### <a name="joint-transform-from-hand-joint-service"></a>Trasformazione congiunta dal servizio combinato di mano

[`IMixedRealityHandJointService`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHandJointService) mantiene un set permanente di [GameObject](https://docs.unity3d.com/ScriptReference/GameObject.html) per il rilevamento delle giunzioni.

```c#
var handJointService = CoreServices.GetInputSystemDataProvider<IMixedRealityHandJointService>();
if (handJointService != null)
{
    Transform jointTransform = handJointService.RequestJointTransform(TrackedHandJoint.IndexTip, Handedness.Right);
    // ...
}
```

### <a name="hand-tracking-events"></a>Eventi di rilevamento della mano

Il sistema di input fornisce anche gli eventi, se non è consigliabile eseguire il polling dei dati direttamente dai controller.

#### <a name="joint-events"></a>Eventi comuni

[`IMixedRealityHandJointHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHandJointHandler) gestisce gli aggiornamenti delle posizioni congiunte.

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

#### <a name="mesh-events"></a>Eventi Mesh

[`IMixedRealityHandMeshHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHandMeshHandler) gestisce le modifiche della mesh a mano articolata.

Si noti che le mesh della mano non sono abilitate per impostazione predefinita.

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

## <a name="known-issues"></a>Problemi noti

### <a name="net-native"></a>.NET Native

Attualmente esiste un problema noto relativo alle compilazioni Master con il back-end .NET. In .NET Native `IInspectable` non è possibile effettuare il marshalling dei puntatori dal codice nativo al codice gestito utilizzando `Marshal.GetObjectForIUnknown` . Il MRTK lo usa per ottenere l'oggetto per `SpatialCoordinateSystem` ricevere dati sulla mano e sugli occhi dalla piattaforma.

È stata fornita una soluzione alternativa per questo problema nel [repository native Mixed Reality Toolkit](https://github.com/microsoft/MixedRealityToolkit/tree/master/DotNetNativeWorkaround). Seguire le istruzioni contenute nel file Leggimi e copiare i file binari risultanti in una cartella dei plug-in degli asset Unity. Successivamente, lo script WindowsMixedRealityUtilities fornito in MRTK risolverà la soluzione alternativa.

Se si vuole creare una DLL personalizzata o includere questa soluzione alternativa in una esistente, il nucleo della soluzione alternativa è:

```c++
extern "C" __declspec(dllexport) void __stdcall MarshalIInspectable(IUnknown* nativePtr, IUnknown** inspectable)
{
    *inspectable = nativePtr;
}
```

E il suo uso nel codice C# Unity:

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

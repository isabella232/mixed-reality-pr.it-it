---
title: Tracciamento mano
description: Documentazione su come usare HandTracking in MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, tracciamento manuale,
ms.openlocfilehash: f9d3b6b0f83a513b849aa27d464595ec8543bc30b64314c9a6e341cd6cb3a519
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115189497"
---
# <a name="hand-tracking"></a>Tracciamento mano

## <a name="hand-tracking-profile"></a>Profilo di tracciamento manuale

Il _profilo Di rilevamento manuale_ si trova nel profilo del sistema di _input_. Contiene le impostazioni per la personalizzazione della rappresentazione manuale.

<img src="../images/input/HandTrackingProfile.png" width="650px" alt="Hand Tracking Profile" style="display:block;">

## <a name="joint-prefabs"></a>Prefab congiunti

I prefab congiunti vengono visualizzato usando prefab semplici. Le _giunzioni_ Palm _e Index Finger_ sono di particolare importanza e hanno il proprio prefab, mentre tutte le altre giunzioni condividono lo stesso prefab.

Per impostazione predefinita, i prefab delle giunzione della mano sono primitive geometriche semplici. Possono essere sostituiti, se lo si desidera. Se non viene specificato alcun prefab, vengono creati [gameobject](https://docs.unity3d.com/ScriptReference/GameObject.html) vuoti.

> [!WARNING]
> Evitare di usare script complessi o un rendering costoso nei prefab congiunti, poiché gli oggetti congiunti vengono trasformati in ogni frame e possono avere un costo significativo per le prestazioni.

Rappresentazione predefinita delle giunzione della mano |  Etichette congiunte
:-------------------------:|:-------------------------:
<img src="../images/input-simulation/ArticulatedHandJoints.png" height="300px" alt="Articulated hand joints"  style="display:inline;">  |  <img src="../images/input-simulation/MRTK_Core_Input_Hands_JointNames.png" height="300px" alt="Input Hand joints"  style="display:inline;">

## <a name="hand-mesh-prefab"></a>Prefab della mesh manuale

La mesh manuale viene usata se i dati della mesh completamente definiti vengono forniti dal dispositivo di rilevamento manuale. La mesh di cui è possibile eseguire il rendering nel prefab viene sostituita dai dati del dispositivo, quindi è sufficiente una mesh fittizia, ad esempio un cubo. Il materiale del prefab viene usato per la mesh della mano.

<img src="../images/input-simulation/MRTK_Core_Input_Hands_ArticulatedHandMesh.png" width="350px" alt="Input Hand Mesh"  style="display:block;">

La visualizzazione della mesh manuale può avere un impatto significativo sulle prestazioni, per questo motivo può essere disabilitata completamente deselezionando l'opzione **Abilita visualizzazione mesh** manuale.

## <a name="hand-visualization-settings"></a>Impostazioni di visualizzazione manuale

Le visualizzazioni della mesh manuale e delle giunzioni della mano possono essere disattivate o attivate rispettivamente tramite l'impostazione *Modalità* di visualizzazione della mesh manuale e le modalità *di visualizzazione delle giunzioni* della mano. Queste impostazioni sono specifiche della modalità applicazione, vale a dire che è possibile attivare alcune funzionalità nell'editor (per visualizzare i giunzioni con la simulazione nell'editor, ad esempio) mentre le stesse funzionalità sono disattivate quando vengono distribuite nel dispositivo (nelle build del lettore).

Si noti che è in genere consigliabile che la visualizzazione delle giunzioni delle mani sia attivata nell'editor (in modo che la simulazione nell'editor mostri dove si trovano le giunzioni della mano) e che sia la visualizzazione delle giunzioni della mano che la visualizzazione della mesh manuale siano disattivate nel lettore (perché comportano un miglioramento delle prestazioni).

## <a name="scripting"></a>Scripting

La posizione e la rotazione possono essere richieste dal sistema di input per ogni singolo giunto della mano come [`MixedRealityPose`](xref:Microsoft.MixedReality.Toolkit.Utilities.MixedRealityPose) .

In alternativa, il sistema consente [l'accesso a GameObject che](https://docs.unity3d.com/ScriptReference/GameObject.html) seguono le giunzioni. Ciò può essere utile se un altro GameObject deve tenere traccia continuamente di un giunto.

Le giunzioni disponibili sono elencate [`TrackedHandJoint`](xref:Microsoft.MixedReality.Toolkit.Utilities.TrackedHandJoint) nell'enumerazione .

> [!NOTE]
> L'oggetto congiunto viene eliminato quando il tracciamento manuale viene perso. Assicurarsi che tutti gli script che usano l'oggetto congiunto gestino correttamente il `null` caso per evitare errori.

### <a name="accessing-a-given-hand-controller"></a>Accesso a un determinato controller manuale

Spesso è disponibile un controller della mano specifico, ad esempio quando si gestisce gli eventi di input. In questo caso i dati congiunti possono essere richiesti direttamente dal dispositivo, usando [`IMixedRealityHand`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHand) l'interfaccia .

#### <a name="polling-joint-pose-from-controller"></a>Polling della posizione congiunta dal controller

La [`TryGetJoint`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHand.TryGetJoint*) funzione restituisce se il giunto richiesto non è disponibile per qualche `false` motivo. In tal caso, la posizione risultante sarà [`MixedRealityPose.ZeroIdentity`](xref:Microsoft.MixedReality.Toolkit.Utilities.MixedRealityPose.ZeroIdentity) .

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

#### <a name="joint-transform-from-hand-visualizer"></a>Trasformazione congiunta dal visualizzatore mano

Gli oggetti congiunti possono essere richiesti dal [visualizzatore controller](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityController.Visualizer).

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

### <a name="simplified-joint-data-access"></a>Accesso semplificato ai dati congiunti

Se non viene specificato alcun controller specifico, vengono fornite classi di utilità per un comodo accesso ai dati delle giunzione manuale. Queste funzioni richiedono dati congiunti dal primo dispositivo a mano disponibile attualmente monitorato.

#### <a name="polling-joint-pose-from-handjointutils"></a>Posizione congiunta di polling da HandJointUtils

[`HandJointUtils`](xref:Microsoft.MixedReality.Toolkit.Input.HandJointUtils) è una classe statica che esegue una query sul primo dispositivo a mano attivo.

```c#
if (HandJointUtils.TryGetJointPose(TrackedHandJoint.IndexTip, Handedness.Right, out MixedRealityPose pose))
{
    // ...
}
```

#### <a name="joint-transform-from-hand-joint-service"></a>Trasformazione congiunta dal servizio hand joint

[`IMixedRealityHandJointService`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHandJointService) mantiene un set persistente [di GameObject per tenere](https://docs.unity3d.com/ScriptReference/GameObject.html) traccia delle giunzioni.

```c#
var handJointService = CoreServices.GetInputSystemDataProvider<IMixedRealityHandJointService>();
if (handJointService != null)
{
    Transform jointTransform = handJointService.RequestJointTransform(TrackedHandJoint.IndexTip, Handedness.Right);
    // ...
}
```

### <a name="hand-tracking-events"></a>Eventi di rilevamento manuale

Anche il sistema di input fornisce eventi, se il polling diretto dei dati dai controller non è consigliabile.

#### <a name="joint-events"></a>Eventi congiunti

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

#### <a name="mesh-events"></a>Eventi mesh

[`IMixedRealityHandMeshHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHandMeshHandler) gestisce le modifiche della mesh della mano articolata.

Si noti che le mesh a mano non sono abilitate per impostazione predefinita.

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

Esiste attualmente un problema noto con le compilazioni master che usano il back-end .NET. In .NET Native, non è possibile effettuare il marshalling dei puntatori da codice nativo `IInspectable` a codice gestito usando `Marshal.GetObjectForIUnknown` . MrTK usa questo oggetto per ottenere per ricevere i dati relativi a mani `SpatialCoordinateSystem` e occhi dalla piattaforma.

L'origine DLL è stata fornita come soluzione alternativa per questo problema, nel Toolkit di realtà [mista nativa.](https://github.com/microsoft/MixedRealityToolkit/tree/master/DotNetNativeWorkaround) Seguire le istruzioni nel file LEGGIMI e copiare i file binari risultanti in una cartella Plugins negli asset di Unity. Successivamente, lo script WindowsMixedRealityUtilities fornito in MRTK risolverà automaticamente la soluzione alternativa.

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

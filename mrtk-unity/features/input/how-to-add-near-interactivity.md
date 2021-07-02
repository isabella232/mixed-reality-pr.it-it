---
title: Come aggiungere l'interattività vicina
description: Documentazione sull'interazione near in MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realtà mista, sviluppo, MRTK, Near Interaction,
ms.openlocfilehash: 241425f0c158d684cad6dad8c88c8d692cbec42f
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176869"
---
# <a name="how-to-add-near-interactivity"></a>Come aggiungere l'interattività vicina

Le interazioni nelle vicinanze sono sotto forma di tocchi e afferramenti. Gli eventi di tocco e di afferrare vengono generati rispettivamente come eventi puntatore [da PokePointer](pointers.md#pokepointer) e [SpherePointer.](pointers.md#spherepointer)

Sono necessari tre passaggi chiave per restare in ascolto degli eventi di tocco e/o di input in un gameobject specifico.

1. Assicurarsi che il puntatore pertinente sia registrato nel profilo [di configurazione MRTK principale.](../../configuration/mixed-reality-configuration-guide.md)
1. Verificare che l'oggetto GameObject desiderato abbia il componente di [script](#add-touch-interactions) [di](#add-grab-interactions) tocco o di tocco appropriato e [`Unity Collider`](https://docs.unity3d.com/ScriptReference/Collider.html) .
1. Implementare un'interfaccia del gestore di input in uno script associato all'oggetto GameObject desiderato per restare in ascolto degli [eventi di tocco](#grab-code-example) o [di](#touch-code-example) cattura.

## <a name="add-grab-interactions"></a>Aggiungere interazioni di afferrare

1. Assicurarsi che [SpherePointer](pointers.md#spherepointer) sia registrato nel *profilo puntatore MRTK*.

    Il profilo MRTK predefinito e il profilo HoloLens 2 predefinito contengono già *spherePointer*. È possibile confermare che verrà creato un SpherePointer selezionando il profilo di configurazione MRTK e passando a **Opzioni** puntatore  >    >  **puntatore di input**. Il `GrabPointer` prefab predefinito (Assets/MRTK/SDK/Features/UX/Prefabs/Pointers) deve essere elencato con un tipo di *controller* di mano *articolata.* Un prefab personalizzato può essere utilizzato purché implementi la [`SpherePointer`](xref:Microsoft.MixedReality.Toolkit.Input.SpherePointer) classe .

    ![Esempio di profilo puntatore Grab](../images/input/Pointers/GrabPointer_MRTKProfile.png)

    Il puntatore grab predefinito esegue una query per gli oggetti vicini in un cono intorno al punto di afferrare in modo che corrisponda all'interfaccia predefinita di Hololens 2.

    ![Puntatore conical Grab](https://user-images.githubusercontent.com/39840334/82500569-72d58300-9aa8-11ea-8102-ec9a62832d4e.png)

1. Nell'oggetto GameObject che deve essere afferrabile aggiungere , [`NearInteractionGrabbable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionGrabbable) nonché un collisore.

    Assicurarsi che il livello di GameObject si trova in un livello afferrabile. Per impostazione predefinita, tutti i livelli, ad eccezione *di Consapevolezza spaziale* *e Ignora raycast,* sono selezionabili. Vedere quali livelli possono essere afferrati controllando le maschere di *livello* Grab nel prefab *GrabPointer.*

1. In GameObject o in uno dei relativi predecessori aggiungere un componente script che implementa [`IMixedRealityPointerHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityPointerHandler) l'interfaccia . Anche qualsiasi predecessore dell'oggetto [`NearInteractionGrabbable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionGrabbable) con sarà in grado di ricevere eventi puntatore.

### <a name="grab-code-example"></a>Esempio di codice Grab

Di seguito è riportato uno script che verrà stampato se un evento è un tocco o un afferrare. Nella funzione di *interfaccia IMixedRealityPointerHandler* pertinente è possibile esaminare il tipo di puntatore che attiva l'evento tramite [`MixedRealityPointerEventData`](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityPointerEventData) . Se il puntatore è *un SpherePointer,* l'interazione è un'interazione di tipo grab.

```c#
public class PrintPointerEvents : MonoBehaviour, IMixedRealityPointerHandler
{
    public void OnPointerDown(MixedRealityPointerEventData eventData)
    {
        if (eventData.Pointer is SpherePointer)
        {
            Debug.Log($"Grab start from {eventData.Pointer.PointerName}");
        }
        if (eventData.Pointer is PokePointer)
        {
            Debug.Log($"Touch start from {eventData.Pointer.PointerName}");
        }
    }

    public void OnPointerClicked(MixedRealityPointerEventData eventData) {}
    public void OnPointerDragged(MixedRealityPointerEventData eventData) {}
    public void OnPointerUp(MixedRealityPointerEventData eventData) {}
}
```

## <a name="add-touch-interactions"></a>Aggiungere interazioni tramite tocco

Il processo per l'aggiunta di interazioni tramite tocco sugli elementi UnityUI è diverso da quello di Vanilla 3D GameObjects. È possibile passare alla sezione seguente, Unity *UI*, per abilitare i componenti dell'interfaccia utente di Unity.

Per **entrambi** i tipi di elementi dell'esperienza utente, tuttavia, assicurarsi che [pokePointer](pointers.md#pokepointer) sia registrato nel *profilo puntatore MRTK*.

Il profilo MRTK predefinito e il profilo HoloLens 2 predefinito contengono già *un PokePointer*. È possibile confermare che verrà creato un oggetto PokePointer selezionando il profilo di configurazione MRTK e passare a **Opzioni** puntatore  >    >  **puntatore di input**. Il `PokePointer` prefab predefinito (Assets/MRTK/SDK/Features/UX/Prefabs/Pointers) deve essere elencato con un tipo di *controller* di mano *articolata.* Un prefab personalizzato può essere utilizzato purché implementi la [`PokePointer`](xref:Microsoft.MixedReality.Toolkit.Input.PokePointer) classe .

![Esempio di profilo del puntatore Poke](../images/input/Pointers/PokePointer_MRTKProfile.png)

### <a name="3d-gameobjects"></a>GameObject 3D

Esistono due modi diversi per aggiungere interazioni tramite tocco a GameObject 3D, a seconda che l'oggetto 3D debba avere un solo piano toccabile o se deve essere toccabile in base all'intero collisore.
Il primo modo è in genere sugli oggetti con BoxColliders, in cui si desidera che solo un singolo viso del collisore reagisca agli eventi di tocco. L'altro è per gli oggetti che devono essere toccabili da qualsiasi direzione in base al collisore.

### <a name="single-face-touch"></a>Tocco con un singolo viso

Ciò è utile per abilitare situazioni in cui un solo viso deve essere toccabile. Questa opzione presuppone che l'oggetto gioco abbia un oggetto BoxCollider. è possibile usarlo con oggetti non BoxCollider, nel qual caso le proprietà "Bounds" e "Local Center" possono essere impostate manualmente per configurare il piano toccabile( ad esempio, i limiti devono essere impostati su un valore diverso da zero).

1. In GameObject che deve essere toccabile aggiungere un oggetto BoxCollider e un oggetto [ `NearInteractionTouchable` ] (xref:Microsoft.MixedReality.Toolkit. Componente Input.NearInteractionTouchable).

    1. Impostare **Events su Receive** su *Touch* se si usa [ `IMixedRealityTouchHandler` ] (xref:Microsoft.MixedReality.Toolkit. Interfaccia Input.IMixedRealityTouchHandler) nello script del componente seguente.

    1. Fare clic **su Correggi limiti e** centro **correzioni**

    ![NearInteractionTouchable Setup](../images/input/Pointers/NearInteractionTouchableSetup.gif)

1. In tale oggetto o in uno dei relativi predecessori aggiungere un componente script che implementa l'oggetto [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler)
   . Qualsiasi predecessore dell'oggetto con [ `NearInteractionTouchable` ] (xref:Microsoft.MixedReality.Toolkit. Input.NearInteractionTouchable) sarà in grado di ricevere anche eventi puntatore.

> [!NOTE]
> Nella visualizzazione della scena dell'editor con *l'oggetto NearInteractionTouchable* GameObject selezionato, notare un quadrato con contorno bianco e una freccia. La freccia punta alla "parte anteriore" dell'oggetto toccabile. L'oggetto collidable sarà toccabile solo da tale direzione. Per rendere un collisore toccabile da tutte le direzioni, vedere la sezione sul tocco del [collisore arbitrario.](#arbitrary-collider-touch)
> ![NearInteractionTouchable Gizmos ](../images/input/Pointers/NearInteractionTouchableGizmos.png)

### <a name="arbitrary-collider-touch"></a>Tocco del collisore arbitrario

Ciò è utile per consentire situazioni in cui l'oggetto del gioco deve essere toccabile lungo l'intero viso del collisore. Ad esempio, può essere usato per abilitare le interazioni tramite tocco per un oggetto con sphereCollider, in cui l'intero collisore deve essere toccabile.

1. In GameObject che deve essere toccabile aggiungere un collisore e un [ `NearInteractionTouchableVolume` ] (xref:Microsoft.MixedReality.Toolkit. Componente Input.NearInteractionTouchableVolume).

    1. Impostare **Events su Receive** su *Touch* se si usa [ `IMixedRealityTouchHandler` ] (xref:Microsoft.MixedReality.Toolkit. Interfaccia Input.IMixedRealityTouchHandler) nello script del componente seguente.

1. In tale oggetto o in uno dei relativi predecessori aggiungere un componente script che implementa l'oggetto [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler)
   . Qualsiasi predecessore dell'oggetto con [ `NearInteractionTouchable` ] (xref:Microsoft.MixedReality.Toolkit. Input.NearInteractionTouchable) sarà in grado di ricevere anche eventi puntatore.

### <a name="unity-ui"></a>Interfaccia utente di Unity

1. Aggiungere/verificare che nella scena sia presente [un canvas UnityUI.](https://docs.unity3d.com/Manual/UICanvas.html)

1. In GameObject che deve essere toccabile aggiungere un [`NearInteractionTouchableUnityUI`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchableUnityUI) componente.  

    1. Impostare **Eventi su Ricevi su** Tocco *se* si usa [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler) l'interfaccia nello script del componente seguente.

1. In tale oggetto o in uno dei relativi predecessori aggiungere un componente script che implementa [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler) l'interfaccia . Anche qualsiasi predecessore dell'oggetto [`NearInteractionTouchableUnityUI`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchableUnityUI) con sarà in grado di ricevere eventi puntatore.

> [!IMPORTANT]
> Gli oggetti potrebbero non comportarsi come previsto se si trovano su oggetti canvas sovrapposti. Per garantire un comportamento coerente, non sovrapporre mai gli oggetti canvas nella scena.

> [!IMPORTANT]
> Nel componente `NearInteractionTouchable` script, per la proprietà *Eventi da ricevere* sono disponibili due opzioni: *Puntatore* e *Tocco*. Impostare *Events su Receive* su *Pointer* se si usa l'interfaccia e impostare su Touch se si usa l'interfaccia nello script del componente che [`IMixedRealityPointerHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityPointerHandler)  [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler) risponde/gestisce gli eventi di input.

#### <a name="touch-code-example"></a>Esempio di codice touch

Il codice seguente illustra un oggetto MonoBehaviour che può essere collegato a un GameObject con un componente variant e rispondere agli [`NearInteractionTouchable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) eventi di input tocco.

```c#
public class TouchEventsExample : MonoBehaviour, IMixedRealityTouchHandler
{
    public void OnTouchStarted(HandTrackingInputEventData eventData)
    {
        string ptrName = eventData.Pointer.PointerName;
        Debug.Log($"Touch started from {ptrName}");
    }
    public void OnTouchCompleted(HandTrackingInputEventData eventData) {}
    public void OnTouchUpdated(HandTrackingInputEventData eventData) { }
}
```

## <a name="near-interaction-script-examples"></a>Esempi di script di interazione nelle vicinanze

### <a name="touch-events"></a>Eventi di tocco

Questo esempio crea un cubo, lo rende toccabile e modifica il colore al tocco.

```c#
public static void MakeChangeColorOnTouch(GameObject target)
{
    // Add and configure the touchable
    var touchable = target.AddComponent<NearInteractionTouchableVolume>();
    touchable.EventsToReceive = TouchableEventType.Pointer;

    var material = target.GetComponent<Renderer>().material;
    // Change color on pointer down and up
    var pointerHandler = target.AddComponent<PointerHandler>();
    pointerHandler.OnPointerDown.AddListener((e) => material.color = Color.green);
    pointerHandler.OnPointerUp.AddListener((e) => material.color = Color.magenta);
}
```

### <a name="grab-events"></a>Eventi grab

L'esempio seguente mostra come rendere trascinabile un oggetto GameObject. Presuppone che l'oggetto gioco abbia un collisore.

```c#
public static void MakeNearDraggable(GameObject target)
{
    // Instantiate and add grabbable
    target.AddComponent<NearInteractionGrabbable>();

    // Add ability to drag by re-parenting to pointer object on pointer down
    var pointerHandler = target.AddComponent<PointerHandler>();
    pointerHandler.OnPointerDown.AddListener((e) =>
    {
        if (e.Pointer is SpherePointer)
        {
            target.transform.parent = ((SpherePointer)(e.Pointer)).transform;
        }
    });
    pointerHandler.OnPointerUp.AddListener((e) =>
    {
        if (e.Pointer is SpherePointer)
        {
            target.transform.parent = null;
        }
    });
}
```

## <a name="useful-apis"></a>API utili

* [`NearInteractionGrabbable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionGrabbable)
* [`NearInteractionTouchable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable)
* [`NearInteractionTouchableUnityUI`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchableUnityUI)
* [`NearInteractionTouchableVolume`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchableVolume)
* [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler)
* [`IMixedRealityPointerHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityPointerHandler)

## <a name="see-also"></a>Vedere anche

* [Cenni preliminari sull'input](overview.md)
* [Puntatori](pointers.md)
* [Eventi di input](input-events.md)

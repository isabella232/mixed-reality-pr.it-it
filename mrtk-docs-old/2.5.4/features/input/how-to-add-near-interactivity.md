---
title: HowToAddNearInteractivity
description: Documentazione su near Interaction in MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, near Interaction,
ms.openlocfilehash: b340341f34a1d9a2e2a91fb4215761c4e53ced86
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2021
ms.locfileid: "104685334"
---
# <a name="how-to-add-near-interaction-in-mrtk"></a>Come aggiungere near Interaction in MRTK

Quasi le interazioni sono disponibili sotto forma di tocchi e catture. Gli eventi di tocco e di cattura vengono generati come eventi puntatore rispettivamente da [PokePointer](pointers.md#pokepointer) e [SpherePointer](pointers.md#spherepointer).

Sono necessari tre passaggi chiave per restare in ascolto di eventi di input touch e/o di input in un determinato GameObject.

1. Verificare che il puntatore pertinente sia registrato nel [profilo di configurazione](../../configuration/mixed-reality-configuration-guide.md)principale di MRTK.
1. Verificare che il GameObject desiderato disponga del componente di script di [cattura](#add-grab-interactions) o [tocco](#add-touch-interactions) appropriato e [`Unity Collider`](https://docs.unity3d.com/ScriptReference/Collider.html) .
1. Implementare un'interfaccia del gestore di input su uno script collegato al GameObject desiderato per restare in ascolto degli eventi di [cattura](#grab-code-example) o [tocco](#touch-code-example) .

## <a name="add-grab-interactions"></a>Aggiungere interazioni di cattura

1. Verificare che [SpherePointer](pointers.md#spherepointer) sia registrato nel *profilo puntatore MRTK*.

    Il profilo MRTK predefinito e il profilo HoloLens 2 predefinito contengono già un *SpherePointer*. È possibile verificare che venga creato un SpherePointer selezionando il profilo di configurazione MRTK e passando alle   >  Opzioni del puntatore a **puntatori** di input  >  . Il `GrabPointer` prefabbricato predefinito (assets/MRTK/SDK/features/UX/Prefabbricates/puntatori) dovrebbe essere elencato con un *tipo di controller* a *mano articolata*. Una precostruzione personalizzata può essere usata purché implementi la [`SpherePointer`](xref:Microsoft.MixedReality.Toolkit.Input.SpherePointer) classe.

    ![Esempio di profilo del puntatore per la cattura](../images/input/Pointers/GrabPointer_MRTKProfile.png)

    Il puntatore di recupero predefinito esegue una query per gli oggetti vicini in un cono intorno al punto di recupero per trovare la corrispondenza con l'interfaccia predefinita Hololens 2.

    ![Puntatore a pinza conica](https://user-images.githubusercontent.com/39840334/82500569-72d58300-9aa8-11ea-8102-ec9a62832d4e.png)

1. Sul GameObject che deve essere afferrabile, aggiungere un [`NearInteractionGrabbable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionGrabbable) , nonché un Collider.

    Verificare che il livello di GameObject sia in un livello di acquisizione. Per impostazione predefinita, tutti i livelli ad eccezione di *consapevolezza spaziale* e *ignorano Raycasts* sono afferrabili. Vedere quali livelli sono afferrabili controllando le *maschere del livello* di acquisizione nella prefabbricazione *GrabPointer* .

1. In GameObject o in uno dei relativi predecessori aggiungere un componente script che implementi l' [`IMixedRealityPointerHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityPointerHandler) interfaccia. Qualsiasi predecessore dell'oggetto con l'oggetto [`NearInteractionGrabbable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionGrabbable) sarà in grado di ricevere anche gli eventi puntatore.

### <a name="grab-code-example"></a>Esempio di codice di recupero

Di seguito è riportato uno script che stampa se un evento è un tocco o una cattura. Nella funzione di interfaccia *IMixedRealityPointerHandler* pertinente, è possibile esaminare il tipo di puntatore che attiva l'evento tramite [`MixedRealityPointerEventData`](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityPointerEventData) . Se il puntatore è un *SpherePointer*, l'interazione è una cattura.

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

## <a name="add-touch-interactions"></a>Aggiungere interazioni tocco

Il processo per l'aggiunta di interazioni tocco sugli elementi UnityUI è diverso rispetto a quello per Vanilla 3D GameObject. È possibile passare alla sezione seguente, *interfaccia utente di Unity*, per abilitare i componenti dell'interfaccia utente di Unity.

Per **entrambi** i tipi di elementi UX, verificare tuttavia che [PokePointer](pointers.md#pokepointer) sia registrato nel *profilo puntatore MRTK*.

Il profilo MRTK predefinito e il profilo HoloLens 2 predefinito contengono già un *PokePointer*. È possibile verificare che venga creato un PokePointer selezionando il profilo di configurazione MRTK e passare a puntatore di **input**  >    >  **Opzioni puntatore**. La `PokePointer` prefabbricazione predefinita (assets/MRTK/SDK/features/UX/Prefabbricates/puntatori) deve essere elencata con un *tipo di controller* a *mano articolata*. Una precostruzione personalizzata può essere usata purché implementi la [`PokePointer`](xref:Microsoft.MixedReality.Toolkit.Input.PokePointer) classe.

![Esempio di profilo puntatore poke](../images/input/Pointers/PokePointer_MRTKProfile.png)

### <a name="3d-gameobjects"></a>GameObject 3D

Esistono due modi diversi per aggiungere interazioni di tocco a GameObject 3D, a seconda che l'oggetto 3D debba avere solo un singolo piano toccabile o se deve essere toccabile in base all'intero Collider.
Il primo consiste in genere negli oggetti con BoxColliders, in cui è preferibile avere una sola faccia del Collider React per gli eventi di tocco. L'altro è per gli oggetti che devono essere toccabili da qualsiasi direzione in base al relativo Collider.

### <a name="single-face-touch"></a>Tocco a faccia singola

Questa operazione è utile per abilitare situazioni in cui è necessario che solo un singolo Face sia toccabile. Questa opzione presuppone che l'oggetto gioco disponga di un BoxCollider. è possibile usarlo con oggetti non BoxCollider, nel qual caso le proprietà' Bounds ' è local Center ' devono essere impostate manualmente per configurare il piano toccabile (ovvero i limiti devono essere impostati su un valore diverso da zero).

1. In GameObject che devono essere toccabili, aggiungere un BoxCollider e un componente [ `NearInteractionTouchable` ] (xrif: Microsoft. MixedReality. Toolkit. input. NearInteractionTouchable).

    1. Impostare **gli eventi da ricevere** per il *tocco* se si usa l' `IMixedRealityTouchHandler` interfaccia [] (xrif: Microsoft. MixedReality. Toolkit. input. IMixedRealityTouchHandler) nello script componente seguente.

    1. Fare clic su **Correggi limiti** e **Correggi al centro**

    ![Installazione di NearInteractionTouchable](../images/input/Pointers/NearInteractionTouchableSetup.gif)

1. In tale oggetto o in uno dei relativi predecessori aggiungere un componente script che implementi il [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler)
   . Qualsiasi predecessore dell'oggetto con [ `NearInteractionTouchable` ] (xrif: Microsoft. MixedReality. Toolkit. input. NearInteractionTouchable) sarà in grado di ricevere anche gli eventi puntatore.

> [!NOTE]
> Nella visualizzazione della scena dell'editor con *NearInteractionTouchable* GameObject selezionato, si noti un contorno bianco e una freccia. La freccia punta alla "parte anteriore" del touchable. La collisione potrà essere toccabile solo da tale direzione. Per rendere un Collider toccabile da tutte le direzioni, vedere la sezione sul [tocco di Collider arbitrario](#arbitrary-collider-touch).
> ![Gizmo NearInteractionTouchable ](../images/input/Pointers/NearInteractionTouchableGizmos.png)

### <a name="arbitrary-collider-touch"></a>Tocco di Collider arbitrario

Questa operazione è utile per consentire situazioni in cui l'oggetto gioco deve essere toccabile lungo l'intero volto di Collider. Ad esempio, può essere usato per abilitare le interazioni di tocco per un oggetto con un SphereCollider, in cui l'intero Collider deve essere toccabile.

1. In GameObject che devono essere toccabili, aggiungere un componente Collider e un componente [ `NearInteractionTouchableVolume` ] (xrif: Microsoft. MixedReality. Toolkit. input. NearInteractionTouchableVolume).

    1. Impostare **gli eventi da ricevere** per il *tocco* se si usa l' `IMixedRealityTouchHandler` interfaccia [] (xrif: Microsoft. MixedReality. Toolkit. input. IMixedRealityTouchHandler) nello script componente seguente.

1. In tale oggetto o in uno dei relativi predecessori aggiungere un componente script che implementi il [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler)
   . Qualsiasi predecessore dell'oggetto con [ `NearInteractionTouchable` ] (xrif: Microsoft. MixedReality. Toolkit. input. NearInteractionTouchable) sarà in grado di ricevere anche gli eventi puntatore.

### <a name="unity-ui"></a>Interfaccia utente di Unity

1. Aggiungere/verificare che nella scena sia presente un' [area di disegno UnityUI](https://docs.unity3d.com/Manual/UICanvas.html) .

1. In GameObject che deve essere toccabile aggiungere un [`NearInteractionTouchableUnityUI`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchableUnityUI) componente.  

    1. Impostare **gli eventi da ricevere** per il *tocco* se si usa l' [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler) interfaccia nello script dei componenti riportato di seguito.

1. In tale oggetto o in uno dei relativi predecessori aggiungere un componente script che implementi l' [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler) interfaccia. Qualsiasi predecessore dell'oggetto con il [`NearInteractionTouchableUnityUI`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchableUnityUI) sarà in grado di ricevere anche eventi puntatore.

> [!IMPORTANT]
> Nel `NearInteractionTouchable` componente script, per gli *eventi di proprietà da ricevere* sono disponibili due opzioni: *pointer* e *touch*. Impostare *gli eventi da ricevere* al *puntatore* se si utilizza l' [`IMixedRealityPointerHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityPointerHandler) interfaccia e impostare su *touch* se si utilizza l' [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler) interfaccia nello script componente che risponde/gestisce gli eventi di input.

#### <a name="touch-code-example"></a>Esempio di codice tocco

Il codice riportato di seguito illustra un monocomportamento che può essere collegato a un GameObject con un [`NearInteractionTouchable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) componente Variant e rispondere agli eventi di input di tocco.

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

## <a name="near-interaction-script-examples"></a>Esempi di script near Interaction

### <a name="touch-events"></a>Eventi di tocco

Questo esempio crea un cubo, lo rende toccabile e cambia il colore del tocco.

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

### <a name="grab-events"></a>Acquisisci eventi

Nell'esempio seguente viene illustrato come creare un GameObject trascinabile. Presuppone che l'oggetto gioco disponga di un Collider.

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

## <a name="see-also"></a>Vedi anche

* [Cenni preliminari sull'input](overview.md)
* [Pointers](pointers.md)
* [Eventi di input](input-events.md)

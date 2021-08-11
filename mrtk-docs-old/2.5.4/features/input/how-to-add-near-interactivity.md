---
title: HowToAddNearInteractivity
description: Documentazione sull'interazione da vicino in MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, interazione da vicino,
ms.openlocfilehash: 32b1cd78328a76713c011b48f49aa4fb7fea90f325ffdf24da9c7321c92ccad0
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115197035"
---
# <a name="how-to-add-near-interaction-in-mrtk"></a>Come aggiungere l'interazione da vicino in MRTK

Le interazioni da vicino sono sotto forma di tocchi e afferrazioni. Gli eventi di tocco e cattura vengono generati come eventi puntatore rispettivamente da [PokePointer](pointers.md#pokepointer) [e SpherePointer.](pointers.md#spherepointer)

Sono necessari tre passaggi chiave per restare in ascolto di eventi di tocco e/o di input in un determinato GameObject.

1. Verificare che il puntatore pertinente sia registrato nel profilo [di configurazione principale di MRTK.](../../configuration/mixed-reality-configuration-guide.md)
1. Verificare che il GameObject desiderato abbia il componente dello script [di cattura](#add-grab-interactions) [o tocco](#add-touch-interactions) appropriato e [`Unity Collider`](https://docs.unity3d.com/ScriptReference/Collider.html) .
1. Implementare un'interfaccia del gestore di input in uno script associato al GameObject desiderato per restare in ascolto degli eventi [di cattura](#grab-code-example) [o tocco.](#touch-code-example)

## <a name="add-grab-interactions"></a>Aggiungere interazioni di cattura

1. Verificare che [spherePointer sia](pointers.md#spherepointer) registrato nel profilo del puntatore *MRTK.*

    Il profilo MRTK predefinito e il profilo HoloLens 2 predefinito contengono già *un oggetto SpherePointer.* È possibile confermare che verrà creato un SpherePointer selezionando il profilo di configurazione di MRTK e passando a **Input**  >  **Pointers** Pointer  >  Options (Opzioni **puntatore puntatore di input).** Il `GrabPointer` prefab predefinito (Assets/MRTK/SDK/Features/UX/Prefabs/Pointers) deve essere elencato con il tipo di *controller* Mano *articolata.* Un prefab personalizzato può essere utilizzato purché implementi la [`SpherePointer`](xref:Microsoft.MixedReality.Toolkit.Input.SpherePointer) classe .

    ![Esempio di profilo puntatore Grab](../images/input/Pointers/GrabPointer_MRTKProfile.png)

    Il puntatore di cattura predefinito esegue query per gli oggetti vicini in un cono intorno al punto di cattura in modo che corrispondano all'interfaccia predefinita di Hololens 2.

    ![Puntatore di cattura conico](https://user-images.githubusercontent.com/39840334/82500569-72d58300-9aa8-11ea-8102-ec9a62832d4e.png)

1. Nel GameObject che deve essere afferrabile, aggiungere un oggetto [`NearInteractionGrabbable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionGrabbable) , nonché un collisore.

    Assicurati che il livello del GameObject si trova su un livello afferrabile. Per impostazione predefinita, tutti i livelli, ad *eccezione di Consapevolezza spaziale* e Ignora *raycast,* sono afferrabili. Scopri quali livelli possono essere afferrati esaminando le maschere *di livello* grab nel prefab *GrabPointer.*

1. Nel GameObject o in uno dei relativi predecessori aggiungere un componente script che implementa [`IMixedRealityPointerHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityPointerHandler) l'interfaccia . Qualsiasi predecessore dell'oggetto con [`NearInteractionGrabbable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionGrabbable) sarà in grado di ricevere anche gli eventi del puntatore.

### <a name="grab-code-example"></a>Esempio di codice Grab

Di seguito è riportato uno script che verrà stampato se un evento è un tocco o una cattura. Nella funzione *di interfaccia IMixedRealityPointerHandler* pertinente è possibile esaminare il tipo di puntatore che attiva l'evento tramite [`MixedRealityPointerEventData`](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityPointerEventData) . Se il puntatore è *un SpherePointer,* l'interazione è una cattura.

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

Il processo per l'aggiunta di interazioni tramite tocco sugli elementi UnityUI è diverso rispetto ai GameObject 3D vanilla. È possibile passare alla sezione seguente, Interfaccia utente *di Unity,* per abilitare i componenti dell'interfaccia utente di Unity.

Per **entrambi** i tipi di elementi dell'esperienza utente, tuttavia, assicurarsi che [un PokePointer](pointers.md#pokepointer) sia registrato nel *profilo puntatore MRTK.*

Il profilo MRTK predefinito e il profilo HoloLens 2 predefinito contengono già *un oggetto PokePointer.* È possibile confermare che verrà creato un PokePointer selezionando il profilo di configurazione di MRTK e passare a **Input**  >  **Pointers** Pointer  >  Options (Opzioni **puntatore di input).** Il `PokePointer` prefab predefinito (Assets/MRTK/SDK/Features/UX/Prefabs/Pointers) deve essere elencato con il tipo di *controller* *Mano articolata.* Un prefab personalizzato può essere utilizzato purché implementi la [`PokePointer`](xref:Microsoft.MixedReality.Toolkit.Input.PokePointer) classe .

![Esempio di profilo puntatore Poke](../images/input/Pointers/PokePointer_MRTKProfile.png)

### <a name="3d-gameobjects"></a>GameObject 3D

Esistono due modi diversi per aggiungere interazioni tramite tocco ai GameObject 3D, a seconda che l'oggetto 3D debba avere un solo piano toccabile o se deve essere toccabile in base all'intero collisore.
Il primo modo è in genere sugli oggetti con BoxColliders, in cui si desidera che solo un singolo viso del collisore reagisca agli eventi di tocco. L'altro è per gli oggetti che devono essere toccabili da qualsiasi direzione in base al collisore.

### <a name="single-face-touch"></a>Tocco con viso singolo

Ciò è utile per abilitare situazioni in cui un solo viso deve essere toccabile. Questa opzione presuppone che l'oggetto gioco abbia boxcollider. è possibile usarlo con oggetti non BoxCollider, nel qual caso le proprietà "Bounds" e "Local Center" devono essere impostate manualmente per configurare il piano toccabile( i limiti devono essere impostati su un valore diverso da zero).

1. Nel GameObject che deve essere toccabile, aggiungere un BoxCollider e un [ `NearInteractionTouchable` ] (xref:Microsoft.MixedReality.Toolkit. Input.NearInteractionTouchable).

    1. Impostare **Eventi su Ricevi** su *Tocco* se si usa [ `IMixedRealityTouchHandler` ] (xref:Microsoft.MixedReality.Toolkit. Input.IMixedRealityTouchHandler) nello script del componente riportato di seguito.

    1. Fare clic **su Correggi limiti** e **Correggi centro**

    ![Configurazione NearInteractionTouchable](../images/input/Pointers/NearInteractionTouchableSetup.gif)

1. In tale oggetto o in uno dei relativi predecessori aggiungere un componente script che implementa l'interfaccia [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler)
   . Qualsiasi predecessore dell'oggetto con [ `NearInteractionTouchable` ] (xref:Microsoft.MixedReality.Toolkit. Input.NearInteractionTouchable) sarà in grado di ricevere anche gli eventi del puntatore.

> [!NOTE]
> Nella visualizzazione della scena dell'editor con *l'oggetto GameObject NearInteractionTouchable* selezionato, si noti un quadrato con contorno bianco e una freccia. La freccia punta alla "parte anteriore" del toccabile. L'oggetto collidabile sarà toccabile solo da tale direzione. Per rendere toccabile un collisore da tutte le direzioni, vedere la sezione sul [tocco del collisore arbitrario.](#arbitrary-collider-touch)
> ![NearInteractionTouchable Gizmos ](../images/input/Pointers/NearInteractionTouchableGizmos.png)

### <a name="arbitrary-collider-touch"></a>Tocco del collisore arbitrario

Ciò è utile per consentire situazioni in cui l'oggetto gioco deve essere toccabile lungo l'intero viso del collisore. Ad esempio, può essere usato per abilitare le interazioni tramite tocco per un oggetto con sphereCollider, in cui l'intero collisore deve essere toccabile.

1. Nel GameObject che deve essere toccabile aggiungere un collisore e [ `NearInteractionTouchableVolume` ] (xref:Microsoft.MixedReality.Toolkit. Input.NearInteractionTouchableVolume).

    1. Impostare **Eventi su Ricevi** su *Tocco* se si usa [ `IMixedRealityTouchHandler` ] (xref:Microsoft.MixedReality.Toolkit. Input.IMixedRealityTouchHandler) nello script del componente riportato di seguito.

1. In tale oggetto o in uno dei relativi predecessori aggiungere un componente script che implementa l'interfaccia [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler)
   . Qualsiasi predecessore dell'oggetto con [ `NearInteractionTouchable` ] (xref:Microsoft.MixedReality.Toolkit. Input.NearInteractionTouchable) sarà in grado di ricevere anche gli eventi del puntatore.

### <a name="unity-ui"></a>Interfaccia utente di Unity

1. Aggiungere/verificare che nella scena sia presente un'area di disegno [UnityUI.](https://docs.unity3d.com/Manual/UICanvas.html)

1. Nel GameObject che deve essere toccabile aggiungere un [`NearInteractionTouchableUnityUI`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchableUnityUI) componente .  

    1. Impostare **Eventi su Ricevi su** Tocco *se* si usa [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler) l'interfaccia nello script del componente seguente.

1. In tale oggetto o in uno dei relativi predecessori aggiungere un componente script che implementa [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler) l'interfaccia . Qualsiasi predecessore dell'oggetto con [`NearInteractionTouchableUnityUI`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchableUnityUI) sarà in grado di ricevere anche gli eventi del puntatore.

> [!IMPORTANT]
> Nel componente script per la proprietà Eventi da ricevere sono disponibili `NearInteractionTouchable` due opzioni: *Puntatore* e  *Tocco.* Impostare *Eventi su Ricevi su* *Puntatore* se si usa l'interfaccia e impostare su Tocco se si usa l'interfaccia nello script del componente che [`IMixedRealityPointerHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityPointerHandler)  [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler) risponde/gestisce gli eventi di input.

#### <a name="touch-code-example"></a>Esempio di codice touch

Il codice seguente illustra un oggetto MonoBehaviour che può essere associato a un GameObject con un componente variant e rispondere agli [`NearInteractionTouchable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) eventi di input tocco.

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

## <a name="near-interaction-script-examples"></a>Esempi di script di interazione da vicino

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

### <a name="grab-events"></a>Afferrare gli eventi

L'esempio seguente mostra come rendere trascinabile un GameObject. Presuppone che l'oggetto gioco abbia un collisore.

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
* [Puntatori](pointers.md)
* [Eventi di input](input-events.md)

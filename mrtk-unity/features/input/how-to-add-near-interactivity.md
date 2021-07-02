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
# <a name="how-to-add-near-interactivity"></a><span data-ttu-id="f5c78-104">Come aggiungere l'interattività vicina</span><span class="sxs-lookup"><span data-stu-id="f5c78-104">How to add near interactivity</span></span>

<span data-ttu-id="f5c78-105">Le interazioni nelle vicinanze sono sotto forma di tocchi e afferramenti.</span><span class="sxs-lookup"><span data-stu-id="f5c78-105">Near interactions come in the form of touches and grabs.</span></span> <span data-ttu-id="f5c78-106">Gli eventi di tocco e di afferrare vengono generati rispettivamente come eventi puntatore [da PokePointer](pointers.md#pokepointer) e [SpherePointer.](pointers.md#spherepointer)</span><span class="sxs-lookup"><span data-stu-id="f5c78-106">Touch and grab events are raised as pointer events by the [PokePointer](pointers.md#pokepointer) and [SpherePointer](pointers.md#spherepointer), respectively.</span></span>

<span data-ttu-id="f5c78-107">Sono necessari tre passaggi chiave per restare in ascolto degli eventi di tocco e/o di input in un gameobject specifico.</span><span class="sxs-lookup"><span data-stu-id="f5c78-107">Three key steps are required to listen for touch and/or grab input events on a particular GameObject.</span></span>

1. <span data-ttu-id="f5c78-108">Assicurarsi che il puntatore pertinente sia registrato nel profilo [di configurazione MRTK principale.](../../configuration/mixed-reality-configuration-guide.md)</span><span class="sxs-lookup"><span data-stu-id="f5c78-108">Ensure the relevant pointer is registered in the main [MRTK Configuration Profile](../../configuration/mixed-reality-configuration-guide.md).</span></span>
1. <span data-ttu-id="f5c78-109">Verificare che l'oggetto GameObject desiderato abbia il componente di [script](#add-touch-interactions) [di](#add-grab-interactions) tocco o di tocco appropriato e [`Unity Collider`](https://docs.unity3d.com/ScriptReference/Collider.html) .</span><span class="sxs-lookup"><span data-stu-id="f5c78-109">Ensure the desired GameObject has the appropriate [grab](#add-grab-interactions) or [touch](#add-touch-interactions) script component and [`Unity Collider`](https://docs.unity3d.com/ScriptReference/Collider.html).</span></span>
1. <span data-ttu-id="f5c78-110">Implementare un'interfaccia del gestore di input in uno script associato all'oggetto GameObject desiderato per restare in ascolto degli [eventi di tocco](#grab-code-example) o [di](#touch-code-example) cattura.</span><span class="sxs-lookup"><span data-stu-id="f5c78-110">Implement an input handler interface on an attached script to the desired GameObject to listen for the [grab](#grab-code-example) or [touch](#touch-code-example) events.</span></span>

## <a name="add-grab-interactions"></a><span data-ttu-id="f5c78-111">Aggiungere interazioni di afferrare</span><span class="sxs-lookup"><span data-stu-id="f5c78-111">Add grab interactions</span></span>

1. <span data-ttu-id="f5c78-112">Assicurarsi che [SpherePointer](pointers.md#spherepointer) sia registrato nel *profilo puntatore MRTK*.</span><span class="sxs-lookup"><span data-stu-id="f5c78-112">Ensure a [SpherePointer](pointers.md#spherepointer) is registered in the *MRTK Pointer profile*.</span></span>

    <span data-ttu-id="f5c78-113">Il profilo MRTK predefinito e il profilo HoloLens 2 predefinito contengono già *spherePointer*.</span><span class="sxs-lookup"><span data-stu-id="f5c78-113">The default MRTK profile and the default HoloLens 2 profile already contain a *SpherePointer*.</span></span> <span data-ttu-id="f5c78-114">È possibile confermare che verrà creato un SpherePointer selezionando il profilo di configurazione MRTK e passando a **Opzioni** puntatore  >    >  **puntatore di input**.</span><span class="sxs-lookup"><span data-stu-id="f5c78-114">One can confirm a SpherePointer will be created by selecting the MRTK Configuration Profile and navigating to **Input** > **Pointers** > **Pointer Options**.</span></span> <span data-ttu-id="f5c78-115">Il `GrabPointer` prefab predefinito (Assets/MRTK/SDK/Features/UX/Prefabs/Pointers) deve essere elencato con un tipo di *controller* di mano *articolata.*</span><span class="sxs-lookup"><span data-stu-id="f5c78-115">The default `GrabPointer` prefab (Assets/MRTK/SDK/Features/UX/Prefabs/Pointers) should be listed with a *Controller Type* of *Articulated Hand*.</span></span> <span data-ttu-id="f5c78-116">Un prefab personalizzato può essere utilizzato purché implementi la [`SpherePointer`](xref:Microsoft.MixedReality.Toolkit.Input.SpherePointer) classe .</span><span class="sxs-lookup"><span data-stu-id="f5c78-116">A custom prefab can be utilized as long as it implements the [`SpherePointer`](xref:Microsoft.MixedReality.Toolkit.Input.SpherePointer) class.</span></span>

    ![Esempio di profilo puntatore Grab](../images/input/Pointers/GrabPointer_MRTKProfile.png)

    <span data-ttu-id="f5c78-118">Il puntatore grab predefinito esegue una query per gli oggetti vicini in un cono intorno al punto di afferrare in modo che corrisponda all'interfaccia predefinita di Hololens 2.</span><span class="sxs-lookup"><span data-stu-id="f5c78-118">The default grab pointer queries for nearby objects in a cone around the grab point to match the default Hololens 2 interface.</span></span>

    ![Puntatore conical Grab](https://user-images.githubusercontent.com/39840334/82500569-72d58300-9aa8-11ea-8102-ec9a62832d4e.png)

1. <span data-ttu-id="f5c78-120">Nell'oggetto GameObject che deve essere afferrabile aggiungere , [`NearInteractionGrabbable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionGrabbable) nonché un collisore.</span><span class="sxs-lookup"><span data-stu-id="f5c78-120">On the GameObject that should be grabbable, add a [`NearInteractionGrabbable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionGrabbable), as well as a collider.</span></span>

    <span data-ttu-id="f5c78-121">Assicurarsi che il livello di GameObject si trova in un livello afferrabile.</span><span class="sxs-lookup"><span data-stu-id="f5c78-121">Make sure the layer of the GameObject is on a grabbable layer.</span></span> <span data-ttu-id="f5c78-122">Per impostazione predefinita, tutti i livelli, ad eccezione *di Consapevolezza spaziale* *e Ignora raycast,* sono selezionabili.</span><span class="sxs-lookup"><span data-stu-id="f5c78-122">By default, all layers except *Spatial Awareness* and *Ignore Raycasts* are grabbable.</span></span> <span data-ttu-id="f5c78-123">Vedere quali livelli possono essere afferrati controllando le maschere di *livello* Grab nel prefab *GrabPointer.*</span><span class="sxs-lookup"><span data-stu-id="f5c78-123">See which layers are grabbable by inspecting the *Grab Layer Masks* in your *GrabPointer* prefab.</span></span>

1. <span data-ttu-id="f5c78-124">In GameObject o in uno dei relativi predecessori aggiungere un componente script che implementa [`IMixedRealityPointerHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityPointerHandler) l'interfaccia .</span><span class="sxs-lookup"><span data-stu-id="f5c78-124">On the GameObject or one of its ancestors, add a script component that implements the [`IMixedRealityPointerHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityPointerHandler) interface.</span></span> <span data-ttu-id="f5c78-125">Anche qualsiasi predecessore dell'oggetto [`NearInteractionGrabbable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionGrabbable) con sarà in grado di ricevere eventi puntatore.</span><span class="sxs-lookup"><span data-stu-id="f5c78-125">Any ancestor of the object with the [`NearInteractionGrabbable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionGrabbable) will be able to receive pointer events, as well.</span></span>

### <a name="grab-code-example"></a><span data-ttu-id="f5c78-126">Esempio di codice Grab</span><span class="sxs-lookup"><span data-stu-id="f5c78-126">Grab code example</span></span>

<span data-ttu-id="f5c78-127">Di seguito è riportato uno script che verrà stampato se un evento è un tocco o un afferrare.</span><span class="sxs-lookup"><span data-stu-id="f5c78-127">Below is a script that will print if an event is a touch or grab.</span></span> <span data-ttu-id="f5c78-128">Nella funzione di *interfaccia IMixedRealityPointerHandler* pertinente è possibile esaminare il tipo di puntatore che attiva l'evento tramite [`MixedRealityPointerEventData`](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityPointerEventData) .</span><span class="sxs-lookup"><span data-stu-id="f5c78-128">In the relevant *IMixedRealityPointerHandler* interface function, one can look at the type of pointer that triggers that event via the [`MixedRealityPointerEventData`](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityPointerEventData).</span></span> <span data-ttu-id="f5c78-129">Se il puntatore è *un SpherePointer,* l'interazione è un'interazione di tipo grab.</span><span class="sxs-lookup"><span data-stu-id="f5c78-129">If the pointer is a *SpherePointer*, the interaction is a grab.</span></span>

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

## <a name="add-touch-interactions"></a><span data-ttu-id="f5c78-130">Aggiungere interazioni tramite tocco</span><span class="sxs-lookup"><span data-stu-id="f5c78-130">Add touch interactions</span></span>

<span data-ttu-id="f5c78-131">Il processo per l'aggiunta di interazioni tramite tocco sugli elementi UnityUI è diverso da quello di Vanilla 3D GameObjects.</span><span class="sxs-lookup"><span data-stu-id="f5c78-131">The process for adding touch interactions on UnityUI elements is different than for vanilla 3D GameObjects.</span></span> <span data-ttu-id="f5c78-132">È possibile passare alla sezione seguente, Unity *UI*, per abilitare i componenti dell'interfaccia utente di Unity.</span><span class="sxs-lookup"><span data-stu-id="f5c78-132">You can skip to the following section, *Unity UI*, for enabling Unity UI components.</span></span>

<span data-ttu-id="f5c78-133">Per **entrambi** i tipi di elementi dell'esperienza utente, tuttavia, assicurarsi che [pokePointer](pointers.md#pokepointer) sia registrato nel *profilo puntatore MRTK*.</span><span class="sxs-lookup"><span data-stu-id="f5c78-133">For **both** types of UX elements though, ensure a [PokePointer](pointers.md#pokepointer) is registered in the *MRTK Pointer profile*.</span></span>

<span data-ttu-id="f5c78-134">Il profilo MRTK predefinito e il profilo HoloLens 2 predefinito contengono già *un PokePointer*.</span><span class="sxs-lookup"><span data-stu-id="f5c78-134">The default MRTK profile and the default HoloLens 2 profile already contain a *PokePointer*.</span></span> <span data-ttu-id="f5c78-135">È possibile confermare che verrà creato un oggetto PokePointer selezionando il profilo di configurazione MRTK e passare a **Opzioni** puntatore  >    >  **puntatore di input**.</span><span class="sxs-lookup"><span data-stu-id="f5c78-135">One can confirm a PokePointer will be created by selecting the MRTK Configuration Profile and navigate to **Input** > **Pointers** > **Pointer Options**.</span></span> <span data-ttu-id="f5c78-136">Il `PokePointer` prefab predefinito (Assets/MRTK/SDK/Features/UX/Prefabs/Pointers) deve essere elencato con un tipo di *controller* di mano *articolata.*</span><span class="sxs-lookup"><span data-stu-id="f5c78-136">The default `PokePointer` (Assets/MRTK/SDK/Features/UX/Prefabs/Pointers) prefab should be listed with a *Controller Type* of *Articulated Hand*.</span></span> <span data-ttu-id="f5c78-137">Un prefab personalizzato può essere utilizzato purché implementi la [`PokePointer`](xref:Microsoft.MixedReality.Toolkit.Input.PokePointer) classe .</span><span class="sxs-lookup"><span data-stu-id="f5c78-137">A custom prefab can be utilized as long as it implements the [`PokePointer`](xref:Microsoft.MixedReality.Toolkit.Input.PokePointer) class.</span></span>

![Esempio di profilo del puntatore Poke](../images/input/Pointers/PokePointer_MRTKProfile.png)

### <a name="3d-gameobjects"></a><span data-ttu-id="f5c78-139">GameObject 3D</span><span class="sxs-lookup"><span data-stu-id="f5c78-139">3D GameObjects</span></span>

<span data-ttu-id="f5c78-140">Esistono due modi diversi per aggiungere interazioni tramite tocco a GameObject 3D, a seconda che l'oggetto 3D debba avere un solo piano toccabile o se deve essere toccabile in base all'intero collisore.</span><span class="sxs-lookup"><span data-stu-id="f5c78-140">There are two different ways of adding touch interactions to 3D GameObjects, depending on if your 3d object should only have a single touchable plane, or of if it should be touchable based on its entire collider.</span></span>
<span data-ttu-id="f5c78-141">Il primo modo è in genere sugli oggetti con BoxColliders, in cui si desidera che solo un singolo viso del collisore reagisca agli eventi di tocco.</span><span class="sxs-lookup"><span data-stu-id="f5c78-141">The first way is typically on objects with BoxColliders, where it is desired to only have a single face of the collider react to touch events.</span></span> <span data-ttu-id="f5c78-142">L'altro è per gli oggetti che devono essere toccabili da qualsiasi direzione in base al collisore.</span><span class="sxs-lookup"><span data-stu-id="f5c78-142">The other is for objects that need to be touchable from any direction based on their collider.</span></span>

### <a name="single-face-touch"></a><span data-ttu-id="f5c78-143">Tocco con un singolo viso</span><span class="sxs-lookup"><span data-stu-id="f5c78-143">Single face touch</span></span>

<span data-ttu-id="f5c78-144">Ciò è utile per abilitare situazioni in cui un solo viso deve essere toccabile.</span><span class="sxs-lookup"><span data-stu-id="f5c78-144">This is useful to enable situations where only a single face needs to be touchable.</span></span> <span data-ttu-id="f5c78-145">Questa opzione presuppone che l'oggetto gioco abbia un oggetto BoxCollider.</span><span class="sxs-lookup"><span data-stu-id="f5c78-145">This option assumes that the game object has a BoxCollider.</span></span> <span data-ttu-id="f5c78-146">è possibile usarlo con oggetti non BoxCollider, nel qual caso le proprietà "Bounds" e "Local Center" possono essere impostate manualmente per configurare il piano toccabile( ad esempio, i limiti devono essere impostati su un valore diverso da zero).</span><span class="sxs-lookup"><span data-stu-id="f5c78-146">it's possible to use this with non-BoxCollider objects, in which case the 'Bounds' and 'Local Center' properties much be manually set to configure the touchable plane (i.e. Bounds should be set to a non-zero-zero value).</span></span>

1. <span data-ttu-id="f5c78-147">In GameObject che deve essere toccabile aggiungere un oggetto BoxCollider e un oggetto [ `NearInteractionTouchable` ] (xref:Microsoft.MixedReality.Toolkit. Componente Input.NearInteractionTouchable).</span><span class="sxs-lookup"><span data-stu-id="f5c78-147">On the GameObject that should be touchable, add a BoxCollider and a [`NearInteractionTouchable`] (xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) component.</span></span>

    1. <span data-ttu-id="f5c78-148">Impostare **Events su Receive** su *Touch* se si usa [ `IMixedRealityTouchHandler` ] (xref:Microsoft.MixedReality.Toolkit. Interfaccia Input.IMixedRealityTouchHandler) nello script del componente seguente.</span><span class="sxs-lookup"><span data-stu-id="f5c78-148">Set **Events to Receive** to *Touch* if using the [`IMixedRealityTouchHandler`] (xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler) interface in your component script below.</span></span>

    1. <span data-ttu-id="f5c78-149">Fare clic **su Correggi limiti e** centro **correzioni**</span><span class="sxs-lookup"><span data-stu-id="f5c78-149">Click **Fix bounds** and **Fix center**</span></span>

    ![NearInteractionTouchable Setup](../images/input/Pointers/NearInteractionTouchableSetup.gif)

1. <span data-ttu-id="f5c78-151">In tale oggetto o in uno dei relativi predecessori aggiungere un componente script che implementa l'oggetto [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler)</span><span class="sxs-lookup"><span data-stu-id="f5c78-151">On that object or one of its ancestors, add a script component that implements the [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler)</span></span>
   <span data-ttu-id="f5c78-152">.</span><span class="sxs-lookup"><span data-stu-id="f5c78-152">interface.</span></span> <span data-ttu-id="f5c78-153">Qualsiasi predecessore dell'oggetto con [ `NearInteractionTouchable` ] (xref:Microsoft.MixedReality.Toolkit. Input.NearInteractionTouchable) sarà in grado di ricevere anche eventi puntatore.</span><span class="sxs-lookup"><span data-stu-id="f5c78-153">Any ancestor of the object with the [`NearInteractionTouchable`] (xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) will be able to receive pointer events, as well.</span></span>

> [!NOTE]
> <span data-ttu-id="f5c78-154">Nella visualizzazione della scena dell'editor con *l'oggetto NearInteractionTouchable* GameObject selezionato, notare un quadrato con contorno bianco e una freccia.</span><span class="sxs-lookup"><span data-stu-id="f5c78-154">In the editor scene view with the *NearInteractionTouchable* GameObject selected, notice a white outline square and arrow.</span></span> <span data-ttu-id="f5c78-155">La freccia punta alla "parte anteriore" dell'oggetto toccabile.</span><span class="sxs-lookup"><span data-stu-id="f5c78-155">The arrow points to the "front" of the touchable.</span></span> <span data-ttu-id="f5c78-156">L'oggetto collidable sarà toccabile solo da tale direzione.</span><span class="sxs-lookup"><span data-stu-id="f5c78-156">The collidable will only be touchable from that direction.</span></span> <span data-ttu-id="f5c78-157">Per rendere un collisore toccabile da tutte le direzioni, vedere la sezione sul tocco del [collisore arbitrario.](#arbitrary-collider-touch)</span><span class="sxs-lookup"><span data-stu-id="f5c78-157">To make a collider touchable from all directions, see the section on [arbitrary collider touch](#arbitrary-collider-touch).</span></span>
> <span data-ttu-id="f5c78-158">![NearInteractionTouchable Gizmos ](../images/input/Pointers/NearInteractionTouchableGizmos.png)</span><span class="sxs-lookup"><span data-stu-id="f5c78-158">![NearInteractionTouchable Gizmos ](../images/input/Pointers/NearInteractionTouchableGizmos.png)</span></span>

### <a name="arbitrary-collider-touch"></a><span data-ttu-id="f5c78-159">Tocco del collisore arbitrario</span><span class="sxs-lookup"><span data-stu-id="f5c78-159">Arbitrary collider touch</span></span>

<span data-ttu-id="f5c78-160">Ciò è utile per consentire situazioni in cui l'oggetto del gioco deve essere toccabile lungo l'intero viso del collisore.</span><span class="sxs-lookup"><span data-stu-id="f5c78-160">This is useful to enable situations where the game object needs to be touchable along its entire collider face.</span></span> <span data-ttu-id="f5c78-161">Ad esempio, può essere usato per abilitare le interazioni tramite tocco per un oggetto con sphereCollider, in cui l'intero collisore deve essere toccabile.</span><span class="sxs-lookup"><span data-stu-id="f5c78-161">For example, this can be used to enable touch interactions for an object with a SphereCollider, where the entire collider needs to be touchable.</span></span>

1. <span data-ttu-id="f5c78-162">In GameObject che deve essere toccabile aggiungere un collisore e un [ `NearInteractionTouchableVolume` ] (xref:Microsoft.MixedReality.Toolkit. Componente Input.NearInteractionTouchableVolume).</span><span class="sxs-lookup"><span data-stu-id="f5c78-162">On the GameObject that should be touchable, add a collider and a [`NearInteractionTouchableVolume`] (xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchableVolume) component.</span></span>

    1. <span data-ttu-id="f5c78-163">Impostare **Events su Receive** su *Touch* se si usa [ `IMixedRealityTouchHandler` ] (xref:Microsoft.MixedReality.Toolkit. Interfaccia Input.IMixedRealityTouchHandler) nello script del componente seguente.</span><span class="sxs-lookup"><span data-stu-id="f5c78-163">Set **Events to Receive** to *Touch* if using the [`IMixedRealityTouchHandler`] (xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler) interface in your component script below.</span></span>

1. <span data-ttu-id="f5c78-164">In tale oggetto o in uno dei relativi predecessori aggiungere un componente script che implementa l'oggetto [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler)</span><span class="sxs-lookup"><span data-stu-id="f5c78-164">On that object or one of its ancestors, add a script component that implements the [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler)</span></span>
   <span data-ttu-id="f5c78-165">.</span><span class="sxs-lookup"><span data-stu-id="f5c78-165">interface.</span></span> <span data-ttu-id="f5c78-166">Qualsiasi predecessore dell'oggetto con [ `NearInteractionTouchable` ] (xref:Microsoft.MixedReality.Toolkit. Input.NearInteractionTouchable) sarà in grado di ricevere anche eventi puntatore.</span><span class="sxs-lookup"><span data-stu-id="f5c78-166">Any ancestor of the object with the [`NearInteractionTouchable`] (xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) will be able to receive pointer events, as well.</span></span>

### <a name="unity-ui"></a><span data-ttu-id="f5c78-167">Interfaccia utente di Unity</span><span class="sxs-lookup"><span data-stu-id="f5c78-167">Unity UI</span></span>

1. <span data-ttu-id="f5c78-168">Aggiungere/verificare che nella scena sia presente [un canvas UnityUI.](https://docs.unity3d.com/Manual/UICanvas.html)</span><span class="sxs-lookup"><span data-stu-id="f5c78-168">Add/ensure there is a [UnityUI canvas](https://docs.unity3d.com/Manual/UICanvas.html) in the scene.</span></span>

1. <span data-ttu-id="f5c78-169">In GameObject che deve essere toccabile aggiungere un [`NearInteractionTouchableUnityUI`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchableUnityUI) componente.</span><span class="sxs-lookup"><span data-stu-id="f5c78-169">On the GameObject that should be touchable, add a [`NearInteractionTouchableUnityUI`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchableUnityUI) component.</span></span>  

    1. <span data-ttu-id="f5c78-170">Impostare **Eventi su Ricevi su** Tocco *se* si usa [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler) l'interfaccia nello script del componente seguente.</span><span class="sxs-lookup"><span data-stu-id="f5c78-170">Set **Events to Receive** to *Touch* if using the [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler) interface in your component script below.</span></span>

1. <span data-ttu-id="f5c78-171">In tale oggetto o in uno dei relativi predecessori aggiungere un componente script che implementa [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler) l'interfaccia .</span><span class="sxs-lookup"><span data-stu-id="f5c78-171">On that object or one of its ancestors, add a script component that implements the [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler) interface.</span></span> <span data-ttu-id="f5c78-172">Anche qualsiasi predecessore dell'oggetto [`NearInteractionTouchableUnityUI`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchableUnityUI) con sarà in grado di ricevere eventi puntatore.</span><span class="sxs-lookup"><span data-stu-id="f5c78-172">Any ancestor of the object with the [`NearInteractionTouchableUnityUI`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchableUnityUI) will be able to receive pointer events as well.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f5c78-173">Gli oggetti potrebbero non comportarsi come previsto se si trovano su oggetti canvas sovrapposti.</span><span class="sxs-lookup"><span data-stu-id="f5c78-173">Objects may not behave as expected if they are located on overlapping canvas objects.</span></span> <span data-ttu-id="f5c78-174">Per garantire un comportamento coerente, non sovrapporre mai gli oggetti canvas nella scena.</span><span class="sxs-lookup"><span data-stu-id="f5c78-174">To ensure consistent behavior, never overlap canvas objects in your scene.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f5c78-175">Nel componente `NearInteractionTouchable` script, per la proprietà *Eventi da ricevere* sono disponibili due opzioni: *Puntatore* e *Tocco*.</span><span class="sxs-lookup"><span data-stu-id="f5c78-175">On the `NearInteractionTouchable` script component, for the property *Events to Receive* there are two options: *Pointer* and *Touch*.</span></span> <span data-ttu-id="f5c78-176">Impostare *Events su Receive* su *Pointer* se si usa l'interfaccia e impostare su Touch se si usa l'interfaccia nello script del componente che [`IMixedRealityPointerHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityPointerHandler)  [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler) risponde/gestisce gli eventi di input.</span><span class="sxs-lookup"><span data-stu-id="f5c78-176">Set *Events to Receive* to *Pointer* if using the [`IMixedRealityPointerHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityPointerHandler) interface and set to *Touch* if using the [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler) interface in your component script that responds/handles the input events.</span></span>

#### <a name="touch-code-example"></a><span data-ttu-id="f5c78-177">Esempio di codice touch</span><span class="sxs-lookup"><span data-stu-id="f5c78-177">Touch code example</span></span>

<span data-ttu-id="f5c78-178">Il codice seguente illustra un oggetto MonoBehaviour che può essere collegato a un GameObject con un componente variant e rispondere agli [`NearInteractionTouchable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) eventi di input tocco.</span><span class="sxs-lookup"><span data-stu-id="f5c78-178">The code below demonstrates a MonoBehaviour that can be attached to a GameObject with a [`NearInteractionTouchable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) variant component and respond to touch input events.</span></span>

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

## <a name="near-interaction-script-examples"></a><span data-ttu-id="f5c78-179">Esempi di script di interazione nelle vicinanze</span><span class="sxs-lookup"><span data-stu-id="f5c78-179">Near interaction script examples</span></span>

### <a name="touch-events"></a><span data-ttu-id="f5c78-180">Eventi di tocco</span><span class="sxs-lookup"><span data-stu-id="f5c78-180">Touch events</span></span>

<span data-ttu-id="f5c78-181">Questo esempio crea un cubo, lo rende toccabile e modifica il colore al tocco.</span><span class="sxs-lookup"><span data-stu-id="f5c78-181">This example creates a cube, makes it touchable, and changes color on touch.</span></span>

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

### <a name="grab-events"></a><span data-ttu-id="f5c78-182">Eventi grab</span><span class="sxs-lookup"><span data-stu-id="f5c78-182">Grab events</span></span>

<span data-ttu-id="f5c78-183">L'esempio seguente mostra come rendere trascinabile un oggetto GameObject.</span><span class="sxs-lookup"><span data-stu-id="f5c78-183">The below example shows how to make a GameObject draggable.</span></span> <span data-ttu-id="f5c78-184">Presuppone che l'oggetto gioco abbia un collisore.</span><span class="sxs-lookup"><span data-stu-id="f5c78-184">Assumes that the game object has a collider on it.</span></span>

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

## <a name="useful-apis"></a><span data-ttu-id="f5c78-185">API utili</span><span class="sxs-lookup"><span data-stu-id="f5c78-185">Useful APIs</span></span>

* [`NearInteractionGrabbable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionGrabbable)
* [`NearInteractionTouchable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable)
* [`NearInteractionTouchableUnityUI`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchableUnityUI)
* [`NearInteractionTouchableVolume`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchableVolume)
* [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler)
* [`IMixedRealityPointerHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityPointerHandler)

## <a name="see-also"></a><span data-ttu-id="f5c78-186">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="f5c78-186">See also</span></span>

* [<span data-ttu-id="f5c78-187">Cenni preliminari sull'input</span><span class="sxs-lookup"><span data-stu-id="f5c78-187">Input Overview</span></span>](overview.md)
* [<span data-ttu-id="f5c78-188">Puntatori</span><span class="sxs-lookup"><span data-stu-id="f5c78-188">Pointers</span></span>](pointers.md)
* [<span data-ttu-id="f5c78-189">Eventi di input</span><span class="sxs-lookup"><span data-stu-id="f5c78-189">Input Events</span></span>](input-events.md)

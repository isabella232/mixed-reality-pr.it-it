---
title: HowToAddNearInteractivity
description: Documentazione sull'interazione da vicino in MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, near interaction,
ms.openlocfilehash: fc6fbb33e5a8e9aa6930f56f292f8ded51c53ff0
ms.sourcegitcommit: 0c717ed0043c7a65e2caf1452eb0f49059cdf154
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/06/2021
ms.locfileid: "108644847"
---
# <a name="how-to-add-near-interaction-in-mrtk"></a><span data-ttu-id="69880-104">Come aggiungere l'interazione da vicino in MRTK</span><span class="sxs-lookup"><span data-stu-id="69880-104">How to add near interaction in MRTK</span></span>

<span data-ttu-id="69880-105">Le interazioni da vicino sono sotto forma di tocchi e afferrazioni.</span><span class="sxs-lookup"><span data-stu-id="69880-105">Near interactions come in the form of touches and grabs.</span></span> <span data-ttu-id="69880-106">Gli eventi di tocco e cattura vengono generati come eventi puntatore rispettivamente da [PokePointer](pointers.md#pokepointer) [e SpherePointer.](pointers.md#spherepointer)</span><span class="sxs-lookup"><span data-stu-id="69880-106">Touch and grab events are raised as pointer events by the [PokePointer](pointers.md#pokepointer) and [SpherePointer](pointers.md#spherepointer), respectively.</span></span>

<span data-ttu-id="69880-107">Sono necessari tre passaggi chiave per restare in ascolto degli eventi di tocco e/o di input in un determinato GameObject.</span><span class="sxs-lookup"><span data-stu-id="69880-107">Three key steps are required to listen for touch and/or grab input events on a particular GameObject.</span></span>

1. <span data-ttu-id="69880-108">Verificare che il puntatore pertinente sia registrato nel profilo [di configurazione principale di MRTK.](../../configuration/mixed-reality-configuration-guide.md)</span><span class="sxs-lookup"><span data-stu-id="69880-108">Ensure the relevant pointer is registered in the main [MRTK Configuration Profile](../../configuration/mixed-reality-configuration-guide.md).</span></span>
1. <span data-ttu-id="69880-109">Verificare che il GameObject desiderato abbia il componente script [di cattura](#add-grab-interactions) [o tocco](#add-touch-interactions) appropriato e [`Unity Collider`](https://docs.unity3d.com/ScriptReference/Collider.html) .</span><span class="sxs-lookup"><span data-stu-id="69880-109">Ensure the desired GameObject has the appropriate [grab](#add-grab-interactions) or [touch](#add-touch-interactions) script component and [`Unity Collider`](https://docs.unity3d.com/ScriptReference/Collider.html).</span></span>
1. <span data-ttu-id="69880-110">Implementare un'interfaccia del gestore di input in uno script associato al GameObject desiderato per restare in ascolto degli eventi [di cattura](#grab-code-example) [o tocco.](#touch-code-example)</span><span class="sxs-lookup"><span data-stu-id="69880-110">Implement an input handler interface on an attached script to the desired GameObject to listen for the [grab](#grab-code-example) or [touch](#touch-code-example) events.</span></span>

## <a name="add-grab-interactions"></a><span data-ttu-id="69880-111">Aggiungere interazioni di cattura</span><span class="sxs-lookup"><span data-stu-id="69880-111">Add grab interactions</span></span>

1. <span data-ttu-id="69880-112">Verificare che [spherePointer sia](pointers.md#spherepointer) registrato nel profilo *del puntatore MRTK.*</span><span class="sxs-lookup"><span data-stu-id="69880-112">Ensure a [SpherePointer](pointers.md#spherepointer) is registered in the *MRTK Pointer profile*.</span></span>

    <span data-ttu-id="69880-113">Il profilo MRTK predefinito e il profilo di HoloLens 2 predefinito contengono *già un oggetto SpherePointer.*</span><span class="sxs-lookup"><span data-stu-id="69880-113">The default MRTK profile and the default HoloLens 2 profile already contain a *SpherePointer*.</span></span> <span data-ttu-id="69880-114">È possibile confermare che verrà creato un SpherePointer selezionando il profilo di configurazione di MRTK e passando a **Input**  >  **Pointers** Pointer  >  Options (Opzioni **puntatore puntatore di input).**</span><span class="sxs-lookup"><span data-stu-id="69880-114">One can confirm a SpherePointer will be created by selecting the MRTK Configuration Profile and navigating to **Input** > **Pointers** > **Pointer Options**.</span></span> <span data-ttu-id="69880-115">Il `GrabPointer` prefab predefinito (Assets/MRTK/SDK/Features/UX/Prefabs/Pointers) deve essere elencato con il tipo di *controller* Mano *articolata.*</span><span class="sxs-lookup"><span data-stu-id="69880-115">The default `GrabPointer` prefab (Assets/MRTK/SDK/Features/UX/Prefabs/Pointers) should be listed with a *Controller Type* of *Articulated Hand*.</span></span> <span data-ttu-id="69880-116">Un prefab personalizzato può essere utilizzato purché implementi la [`SpherePointer`](xref:Microsoft.MixedReality.Toolkit.Input.SpherePointer) classe .</span><span class="sxs-lookup"><span data-stu-id="69880-116">A custom prefab can be utilized as long as it implements the [`SpherePointer`](xref:Microsoft.MixedReality.Toolkit.Input.SpherePointer) class.</span></span>

    ![Esempio di profilo puntatore Grab](../images/input/Pointers/GrabPointer_MRTKProfile.png)

    <span data-ttu-id="69880-118">Il puntatore di cattura predefinito esegue query per gli oggetti vicini in un cono intorno al punto di cattura in modo che corrispondano all'interfaccia predefinita di Hololens 2.</span><span class="sxs-lookup"><span data-stu-id="69880-118">The default grab pointer queries for nearby objects in a cone around the grab point to match the default Hololens 2 interface.</span></span>

    ![Puntatore di cattura conico](https://user-images.githubusercontent.com/39840334/82500569-72d58300-9aa8-11ea-8102-ec9a62832d4e.png)

1. <span data-ttu-id="69880-120">Nel GameObject che deve essere afferrabile, aggiungere un oggetto [`NearInteractionGrabbable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionGrabbable) , nonché un collisore.</span><span class="sxs-lookup"><span data-stu-id="69880-120">On the GameObject that should be grabbable, add a [`NearInteractionGrabbable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionGrabbable), as well as a collider.</span></span>

    <span data-ttu-id="69880-121">Assicurarsi che il livello di GameObject si trova su un livello afferrabile.</span><span class="sxs-lookup"><span data-stu-id="69880-121">Make sure the layer of the GameObject is on a grabbable layer.</span></span> <span data-ttu-id="69880-122">Per impostazione predefinita, tutti i livelli, ad eccezione *di Consapevolezza spaziale* *e Ignora raycast,* sono selezionabili.</span><span class="sxs-lookup"><span data-stu-id="69880-122">By default, all layers except *Spatial Awareness* and *Ignore Raycasts* are grabbable.</span></span> <span data-ttu-id="69880-123">Vedere quali livelli possono essere afferrati controllando le maschere di *livello* Grab nel prefab *GrabPointer.*</span><span class="sxs-lookup"><span data-stu-id="69880-123">See which layers are grabbable by inspecting the *Grab Layer Masks* in your *GrabPointer* prefab.</span></span>

1. <span data-ttu-id="69880-124">In GameObject o in uno dei relativi predecessori aggiungere un componente script che implementa [`IMixedRealityPointerHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityPointerHandler) l'interfaccia .</span><span class="sxs-lookup"><span data-stu-id="69880-124">On the GameObject or one of its ancestors, add a script component that implements the [`IMixedRealityPointerHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityPointerHandler) interface.</span></span> <span data-ttu-id="69880-125">Anche qualsiasi predecessore dell'oggetto [`NearInteractionGrabbable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionGrabbable) con sarà in grado di ricevere eventi puntatore.</span><span class="sxs-lookup"><span data-stu-id="69880-125">Any ancestor of the object with the [`NearInteractionGrabbable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionGrabbable) will be able to receive pointer events, as well.</span></span>

### <a name="grab-code-example"></a><span data-ttu-id="69880-126">Esempio di codice Grab</span><span class="sxs-lookup"><span data-stu-id="69880-126">Grab code example</span></span>

<span data-ttu-id="69880-127">Di seguito è riportato uno script che verrà stampato se un evento è un tocco o un grab.</span><span class="sxs-lookup"><span data-stu-id="69880-127">Below is a script that will print if an event is a touch or grab.</span></span> <span data-ttu-id="69880-128">Nella funzione di *interfaccia IMixedRealityPointerHandler* pertinente è possibile esaminare il tipo di puntatore che attiva l'evento tramite [`MixedRealityPointerEventData`](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityPointerEventData) .</span><span class="sxs-lookup"><span data-stu-id="69880-128">In the relevant *IMixedRealityPointerHandler* interface function, one can look at the type of pointer that triggers that event via the [`MixedRealityPointerEventData`](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityPointerEventData).</span></span> <span data-ttu-id="69880-129">Se il puntatore è *un SpherePointer,* l'interazione è un'interazione di tipo grab.</span><span class="sxs-lookup"><span data-stu-id="69880-129">If the pointer is a *SpherePointer*, the interaction is a grab.</span></span>

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

## <a name="add-touch-interactions"></a><span data-ttu-id="69880-130">Aggiungere interazioni tramite tocco</span><span class="sxs-lookup"><span data-stu-id="69880-130">Add touch interactions</span></span>

<span data-ttu-id="69880-131">Il processo per l'aggiunta di interazioni tramite tocco sugli elementi UnityUI è diverso da per vanilla 3D GameObjects.</span><span class="sxs-lookup"><span data-stu-id="69880-131">The process for adding touch interactions on UnityUI elements is different than for vanilla 3D GameObjects.</span></span> <span data-ttu-id="69880-132">È possibile passare alla sezione seguente, Unity *UI*, per abilitare i componenti dell'interfaccia utente di Unity.</span><span class="sxs-lookup"><span data-stu-id="69880-132">You can skip to the following section, *Unity UI*, for enabling Unity UI components.</span></span>

<span data-ttu-id="69880-133">Per **entrambi** i tipi di elementi dell'esperienza utente, tuttavia, assicurarsi che [pokePointer](pointers.md#pokepointer) sia registrato nel *profilo puntatore MRTK*.</span><span class="sxs-lookup"><span data-stu-id="69880-133">For **both** types of UX elements though, ensure a [PokePointer](pointers.md#pokepointer) is registered in the *MRTK Pointer profile*.</span></span>

<span data-ttu-id="69880-134">Il profilo MRTK predefinito e il profilo HoloLens 2 predefinito contengono già *un PokePointer*.</span><span class="sxs-lookup"><span data-stu-id="69880-134">The default MRTK profile and the default HoloLens 2 profile already contain a *PokePointer*.</span></span> <span data-ttu-id="69880-135">È possibile confermare che verrà creato un oggetto PokePointer selezionando il profilo di configurazione MRTK e passare a **Opzioni** puntatore  >    >  **puntatore di input**.</span><span class="sxs-lookup"><span data-stu-id="69880-135">One can confirm a PokePointer will be created by selecting the MRTK Configuration Profile and navigate to **Input** > **Pointers** > **Pointer Options**.</span></span> <span data-ttu-id="69880-136">Il `PokePointer` prefab predefinito (Assets/MRTK/SDK/Features/UX/Prefabs/Pointers) deve essere elencato con un tipo di *controller* di mano *articolata.*</span><span class="sxs-lookup"><span data-stu-id="69880-136">The default `PokePointer` (Assets/MRTK/SDK/Features/UX/Prefabs/Pointers) prefab should be listed with a *Controller Type* of *Articulated Hand*.</span></span> <span data-ttu-id="69880-137">Un prefab personalizzato può essere utilizzato purché implementi la [`PokePointer`](xref:Microsoft.MixedReality.Toolkit.Input.PokePointer) classe .</span><span class="sxs-lookup"><span data-stu-id="69880-137">A custom prefab can be utilized as long as it implements the [`PokePointer`](xref:Microsoft.MixedReality.Toolkit.Input.PokePointer) class.</span></span>

![Esempio di profilo del puntatore Poke](../images/input/Pointers/PokePointer_MRTKProfile.png)

### <a name="3d-gameobjects"></a><span data-ttu-id="69880-139">GameObject 3D</span><span class="sxs-lookup"><span data-stu-id="69880-139">3D GameObjects</span></span>

<span data-ttu-id="69880-140">Esistono due modi diversi per aggiungere interazioni tramite tocco a GameObject 3D, a seconda che l'oggetto 3D debba avere un solo piano toccabile o se deve essere toccabile in base all'intero collisore.</span><span class="sxs-lookup"><span data-stu-id="69880-140">There are two different ways of adding touch interactions to 3D GameObjects, depending on if your 3d object should only have a single touchable plane, or of if it should be touchable based on its entire collider.</span></span>
<span data-ttu-id="69880-141">Il primo modo è in genere sugli oggetti con BoxColliders, in cui si desidera che solo un singolo viso del collisore reagisca agli eventi di tocco.</span><span class="sxs-lookup"><span data-stu-id="69880-141">The first way is typically on objects with BoxColliders, where it is desired to only have a single face of the collider react to touch events.</span></span> <span data-ttu-id="69880-142">L'altro è per gli oggetti che devono essere toccabili da qualsiasi direzione in base al collisore.</span><span class="sxs-lookup"><span data-stu-id="69880-142">The other is for objects that need to be touchable from any direction based on their collider.</span></span>

### <a name="single-face-touch"></a><span data-ttu-id="69880-143">Tocco con viso singolo</span><span class="sxs-lookup"><span data-stu-id="69880-143">Single face touch</span></span>

<span data-ttu-id="69880-144">Ciò è utile per abilitare situazioni in cui un solo viso deve essere toccabile.</span><span class="sxs-lookup"><span data-stu-id="69880-144">This is useful to enable situations where only a single face needs to be touchable.</span></span> <span data-ttu-id="69880-145">Questa opzione presuppone che l'oggetto gioco abbia boxcollider.</span><span class="sxs-lookup"><span data-stu-id="69880-145">This option assumes that the game object has a BoxCollider.</span></span> <span data-ttu-id="69880-146">è possibile usarlo con oggetti non BoxCollider, nel qual caso le proprietà "Bounds" e "Local Center" devono essere impostate manualmente per configurare il piano toccabile( i limiti devono essere impostati su un valore diverso da zero).</span><span class="sxs-lookup"><span data-stu-id="69880-146">it's possible to use this with non-BoxCollider objects, in which case the 'Bounds' and 'Local Center' properties much be manually set to configure the touchable plane (i.e. Bounds should be set to a non-zero-zero value).</span></span>

1. <span data-ttu-id="69880-147">Nel GameObject che deve essere toccabile aggiungere un componente BoxCollider e un componente [ `NearInteractionTouchable` ] (xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable).</span><span class="sxs-lookup"><span data-stu-id="69880-147">On the GameObject that should be touchable, add a BoxCollider and a [`NearInteractionTouchable`] (xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) component.</span></span>

    1. <span data-ttu-id="69880-148">Impostare Eventi su **Ricevi** su *Tocco* se si usa l'interfaccia [ `IMixedRealityTouchHandler` ] (xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler) nello script del componente seguente.</span><span class="sxs-lookup"><span data-stu-id="69880-148">Set **Events to Receive** to *Touch* if using the [`IMixedRealityTouchHandler`] (xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler) interface in your component script below.</span></span>

    1. <span data-ttu-id="69880-149">Fare clic **su Correggi limiti** e **Correggi centro**</span><span class="sxs-lookup"><span data-stu-id="69880-149">Click **Fix bounds** and **Fix center**</span></span>

    ![Configurazione NearInteractionTouchable](../images/input/Pointers/NearInteractionTouchableSetup.gif)

1. <span data-ttu-id="69880-151">In tale oggetto o in uno dei relativi predecessori aggiungere un componente script che implementa l'interfaccia [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler)</span><span class="sxs-lookup"><span data-stu-id="69880-151">On that object or one of its ancestors, add a script component that implements the [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler)</span></span>
   <span data-ttu-id="69880-152">.</span><span class="sxs-lookup"><span data-stu-id="69880-152">interface.</span></span> <span data-ttu-id="69880-153">Qualsiasi predecessore dell'oggetto con [ `NearInteractionTouchable` ] (xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) sarà in grado di ricevere anche gli eventi del puntatore.</span><span class="sxs-lookup"><span data-stu-id="69880-153">Any ancestor of the object with the [`NearInteractionTouchable`] (xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) will be able to receive pointer events, as well.</span></span>

> [!NOTE]
> <span data-ttu-id="69880-154">Nella visualizzazione della scena dell'editor con *l'oggetto GameObject NearInteractionTouchable* selezionato, si noti un quadrato con contorno bianco e una freccia.</span><span class="sxs-lookup"><span data-stu-id="69880-154">In the editor scene view with the *NearInteractionTouchable* GameObject selected, notice a white outline square and arrow.</span></span> <span data-ttu-id="69880-155">La freccia punta alla "parte anteriore" del toccabile.</span><span class="sxs-lookup"><span data-stu-id="69880-155">The arrow points to the "front" of the touchable.</span></span> <span data-ttu-id="69880-156">L'oggetto collidabile sarà toccabile solo da tale direzione.</span><span class="sxs-lookup"><span data-stu-id="69880-156">The collidable will only be touchable from that direction.</span></span> <span data-ttu-id="69880-157">Per rendere un collisore toccabile da tutte le direzioni, vedere la sezione sul [tocco del collisore arbitrario.](#arbitrary-collider-touch)</span><span class="sxs-lookup"><span data-stu-id="69880-157">To make a collider touchable from all directions, see the section on [arbitrary collider touch](#arbitrary-collider-touch).</span></span>
> <span data-ttu-id="69880-158">![NearInteractionTouchable Gizmos ](../images/input/Pointers/NearInteractionTouchableGizmos.png)</span><span class="sxs-lookup"><span data-stu-id="69880-158">![NearInteractionTouchable Gizmos ](../images/input/Pointers/NearInteractionTouchableGizmos.png)</span></span>

### <a name="arbitrary-collider-touch"></a><span data-ttu-id="69880-159">Tocco di collisore arbitrario</span><span class="sxs-lookup"><span data-stu-id="69880-159">Arbitrary collider touch</span></span>

<span data-ttu-id="69880-160">Ciò è utile per consentire situazioni in cui l'oggetto gioco deve essere toccabile lungo l'intero viso del collisore.</span><span class="sxs-lookup"><span data-stu-id="69880-160">This is useful to enable situations where the game object needs to be touchable along its entire collider face.</span></span> <span data-ttu-id="69880-161">Ad esempio, può essere usato per abilitare le interazioni tramite tocco per un oggetto con sphereCollider, in cui l'intero collisore deve essere toccabile.</span><span class="sxs-lookup"><span data-stu-id="69880-161">For example, this can be used to enable touch interactions for an object with a SphereCollider, where the entire collider needs to be touchable.</span></span>

1. <span data-ttu-id="69880-162">In GameObject che deve essere toccabile aggiungere un collisore e un componente [ `NearInteractionTouchableVolume` ] (xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchableVolume).</span><span class="sxs-lookup"><span data-stu-id="69880-162">On the GameObject that should be touchable, add a collider and a [`NearInteractionTouchableVolume`] (xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchableVolume) component.</span></span>

    1. <span data-ttu-id="69880-163">Impostare **Events su Receive** su *Touch* se si usa l'interfaccia [ ] `IMixedRealityTouchHandler` (xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler) nello script del componente seguente.</span><span class="sxs-lookup"><span data-stu-id="69880-163">Set **Events to Receive** to *Touch* if using the [`IMixedRealityTouchHandler`] (xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler) interface in your component script below.</span></span>

1. <span data-ttu-id="69880-164">In tale oggetto o in uno dei relativi predecessori aggiungere un componente script che implementa l'oggetto [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler)</span><span class="sxs-lookup"><span data-stu-id="69880-164">On that object or one of its ancestors, add a script component that implements the [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler)</span></span>
   <span data-ttu-id="69880-165">.</span><span class="sxs-lookup"><span data-stu-id="69880-165">interface.</span></span> <span data-ttu-id="69880-166">Anche qualsiasi predecessore dell'oggetto con [ `NearInteractionTouchable` ] (xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) sarà in grado di ricevere eventi puntatore.</span><span class="sxs-lookup"><span data-stu-id="69880-166">Any ancestor of the object with the [`NearInteractionTouchable`] (xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) will be able to receive pointer events, as well.</span></span>

### <a name="unity-ui"></a><span data-ttu-id="69880-167">Interfaccia utente di Unity</span><span class="sxs-lookup"><span data-stu-id="69880-167">Unity UI</span></span>

1. <span data-ttu-id="69880-168">Aggiungere/verificare che nella scena sia presente [un canvas UnityUI.](https://docs.unity3d.com/Manual/UICanvas.html)</span><span class="sxs-lookup"><span data-stu-id="69880-168">Add/ensure there is a [UnityUI canvas](https://docs.unity3d.com/Manual/UICanvas.html) in the scene.</span></span>

1. <span data-ttu-id="69880-169">In GameObject che deve essere toccabile aggiungere un [`NearInteractionTouchableUnityUI`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchableUnityUI) componente.</span><span class="sxs-lookup"><span data-stu-id="69880-169">On the GameObject that should be touchable, add a [`NearInteractionTouchableUnityUI`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchableUnityUI) component.</span></span>  

    1. <span data-ttu-id="69880-170">Impostare **Eventi su Ricevi su** Tocco *se* si usa [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler) l'interfaccia nello script del componente seguente.</span><span class="sxs-lookup"><span data-stu-id="69880-170">Set **Events to Receive** to *Touch* if using the [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler) interface in your component script below.</span></span>

1. <span data-ttu-id="69880-171">In tale oggetto o in uno dei relativi predecessori aggiungere un componente script che implementa [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler) l'interfaccia .</span><span class="sxs-lookup"><span data-stu-id="69880-171">On that object or one of its ancestors, add a script component that implements the [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler) interface.</span></span> <span data-ttu-id="69880-172">Anche qualsiasi predecessore dell'oggetto [`NearInteractionTouchableUnityUI`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchableUnityUI) con sarà in grado di ricevere eventi puntatore.</span><span class="sxs-lookup"><span data-stu-id="69880-172">Any ancestor of the object with the [`NearInteractionTouchableUnityUI`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchableUnityUI) will be able to receive pointer events as well.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="69880-173">Gli oggetti potrebbero non comportarsi come previsto se si trovano su oggetti canvas sovrapposti.</span><span class="sxs-lookup"><span data-stu-id="69880-173">Objects may not behave as expected if they are located on overlapping canvas objects.</span></span> <span data-ttu-id="69880-174">Per garantire un comportamento coerente, non sovrapporre mai gli oggetti canvas nella scena.</span><span class="sxs-lookup"><span data-stu-id="69880-174">To ensure consistent behavior, never overlap canvas objects in your scene.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="69880-175">Nel componente `NearInteractionTouchable` script, per la proprietà *Eventi da ricevere* sono disponibili due opzioni: *Puntatore* e *Tocco*.</span><span class="sxs-lookup"><span data-stu-id="69880-175">On the `NearInteractionTouchable` script component, for the property *Events to Receive* there are two options: *Pointer* and *Touch*.</span></span> <span data-ttu-id="69880-176">Impostare *Events su Receive* su *Pointer* se si usa l'interfaccia e impostare su Touch se si usa l'interfaccia nello script del componente che [`IMixedRealityPointerHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityPointerHandler)  [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler) risponde/gestisce gli eventi di input.</span><span class="sxs-lookup"><span data-stu-id="69880-176">Set *Events to Receive* to *Pointer* if using the [`IMixedRealityPointerHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityPointerHandler) interface and set to *Touch* if using the [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler) interface in your component script that responds/handles the input events.</span></span>

#### <a name="touch-code-example"></a><span data-ttu-id="69880-177">Esempio di codice touch</span><span class="sxs-lookup"><span data-stu-id="69880-177">Touch code example</span></span>

<span data-ttu-id="69880-178">Il codice seguente illustra un oggetto MonoBehaviour che può essere collegato a un GameObject con un componente variant e rispondere agli [`NearInteractionTouchable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) eventi di input tocco.</span><span class="sxs-lookup"><span data-stu-id="69880-178">The code below demonstrates a MonoBehaviour that can be attached to a GameObject with a [`NearInteractionTouchable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) variant component and respond to touch input events.</span></span>

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

## <a name="near-interaction-script-examples"></a><span data-ttu-id="69880-179">Esempi di script di interazione nelle vicinanze</span><span class="sxs-lookup"><span data-stu-id="69880-179">Near interaction script examples</span></span>

### <a name="touch-events"></a><span data-ttu-id="69880-180">Eventi di tocco</span><span class="sxs-lookup"><span data-stu-id="69880-180">Touch events</span></span>

<span data-ttu-id="69880-181">Questo esempio crea un cubo, lo rende toccabile e modifica il colore al tocco.</span><span class="sxs-lookup"><span data-stu-id="69880-181">This example creates a cube, makes it touchable, and changes color on touch.</span></span>

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

### <a name="grab-events"></a><span data-ttu-id="69880-182">Eventi grab</span><span class="sxs-lookup"><span data-stu-id="69880-182">Grab events</span></span>

<span data-ttu-id="69880-183">L'esempio seguente mostra come rendere trascinabile un oggetto GameObject.</span><span class="sxs-lookup"><span data-stu-id="69880-183">The below example shows how to make a GameObject draggable.</span></span> <span data-ttu-id="69880-184">Presuppone che l'oggetto gioco abbia un collisore.</span><span class="sxs-lookup"><span data-stu-id="69880-184">Assumes that the game object has a collider on it.</span></span>

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

## <a name="useful-apis"></a><span data-ttu-id="69880-185">API utili</span><span class="sxs-lookup"><span data-stu-id="69880-185">Useful APIs</span></span>

* [`NearInteractionGrabbable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionGrabbable)
* [`NearInteractionTouchable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable)
* [`NearInteractionTouchableUnityUI`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchableUnityUI)
* [`NearInteractionTouchableVolume`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchableVolume)
* [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler)
* [`IMixedRealityPointerHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityPointerHandler)

## <a name="see-also"></a><span data-ttu-id="69880-186">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="69880-186">See also</span></span>

* [<span data-ttu-id="69880-187">Cenni preliminari sull'input</span><span class="sxs-lookup"><span data-stu-id="69880-187">Input Overview</span></span>](overview.md)
* [<span data-ttu-id="69880-188">Pointers</span><span class="sxs-lookup"><span data-stu-id="69880-188">Pointers</span></span>](pointers.md)
* [<span data-ttu-id="69880-189">Eventi di input</span><span class="sxs-lookup"><span data-stu-id="69880-189">Input Events</span></span>](input-events.md)

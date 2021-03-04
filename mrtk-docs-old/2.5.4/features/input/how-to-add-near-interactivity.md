---
title: HowToAddNearInteractivity
description: Documentazione su near Interaction in MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, near Interaction,
ms.openlocfilehash: 0a936dae3500d94aaecbaf2f460f30169e4cb264
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/03/2021
ms.locfileid: "101781948"
---
# <a name="how-to-add-near-interaction-in-mrtk"></a><span data-ttu-id="e438e-104">Come aggiungere near Interaction in MRTK</span><span class="sxs-lookup"><span data-stu-id="e438e-104">How to add near interaction in MRTK</span></span>

<span data-ttu-id="e438e-105">Quasi le interazioni sono disponibili sotto forma di tocchi e catture.</span><span class="sxs-lookup"><span data-stu-id="e438e-105">Near interactions come in the form of touches and grabs.</span></span> <span data-ttu-id="e438e-106">Gli eventi di tocco e di cattura vengono generati come eventi puntatore rispettivamente da [PokePointer](pointers.md#pokepointer) e [SpherePointer](pointers.md#spherepointer).</span><span class="sxs-lookup"><span data-stu-id="e438e-106">Touch and grab events are raised as pointer events by the [PokePointer](pointers.md#pokepointer) and [SpherePointer](pointers.md#spherepointer), respectively.</span></span>

<span data-ttu-id="e438e-107">Sono necessari tre passaggi chiave per restare in ascolto di eventi di input touch e/o di input in un determinato GameObject.</span><span class="sxs-lookup"><span data-stu-id="e438e-107">Three key steps are required to listen for touch and/or grab input events on a particular GameObject.</span></span>

1. <span data-ttu-id="e438e-108">Verificare che il puntatore pertinente sia registrato nel [profilo di configurazione](../../configuration/mixed-reality-configuration-guide.md)principale di MRTK.</span><span class="sxs-lookup"><span data-stu-id="e438e-108">Ensure the relevant pointer is registered in the main [MRTK Configuration Profile](../../configuration/mixed-reality-configuration-guide.md).</span></span>
1. <span data-ttu-id="e438e-109">Verificare che il GameObject desiderato disponga del componente di script di [cattura](#add-grab-interactions) o [tocco](#add-touch-interactions) appropriato e [`Unity Collider`](https://docs.unity3d.com/ScriptReference/Collider.html) .</span><span class="sxs-lookup"><span data-stu-id="e438e-109">Ensure the desired GameObject has the appropriate [grab](#add-grab-interactions) or [touch](#add-touch-interactions) script component and [`Unity Collider`](https://docs.unity3d.com/ScriptReference/Collider.html).</span></span>
1. <span data-ttu-id="e438e-110">Implementare un'interfaccia del gestore di input su uno script collegato al GameObject desiderato per restare in ascolto degli eventi di [cattura](#grab-code-example) o [tocco](#touch-code-example) .</span><span class="sxs-lookup"><span data-stu-id="e438e-110">Implement an input handler interface on an attached script to the desired GameObject to listen for the [grab](#grab-code-example) or [touch](#touch-code-example) events.</span></span>

## <a name="add-grab-interactions"></a><span data-ttu-id="e438e-111">Aggiungere interazioni di cattura</span><span class="sxs-lookup"><span data-stu-id="e438e-111">Add grab interactions</span></span>

1. <span data-ttu-id="e438e-112">Verificare che [SpherePointer](pointers.md#spherepointer) sia registrato nel *profilo puntatore MRTK*.</span><span class="sxs-lookup"><span data-stu-id="e438e-112">Ensure a [SpherePointer](pointers.md#spherepointer) is registered in the *MRTK Pointer profile*.</span></span>

    <span data-ttu-id="e438e-113">Il profilo MRTK predefinito e il profilo HoloLens 2 predefinito contengono già un *SpherePointer*.</span><span class="sxs-lookup"><span data-stu-id="e438e-113">The default MRTK profile and the default HoloLens 2 profile already contain a *SpherePointer*.</span></span> <span data-ttu-id="e438e-114">È possibile verificare che venga creato un SpherePointer selezionando il profilo di configurazione MRTK e passando alle   >  Opzioni del puntatore a **puntatori** di input  >  .</span><span class="sxs-lookup"><span data-stu-id="e438e-114">One can confirm a SpherePointer will be created by selecting the MRTK Configuration Profile and navigating to **Input** > **Pointers** > **Pointer Options**.</span></span> <span data-ttu-id="e438e-115">Il `GrabPointer` prefabbricato predefinito (assets/MRTK/SDK/features/UX/Prefabbricates/puntatori) dovrebbe essere elencato con un *tipo di controller* a *mano articolata*.</span><span class="sxs-lookup"><span data-stu-id="e438e-115">The default `GrabPointer` prefab (Assets/MRTK/SDK/Features/UX/Prefabs/Pointers) should be listed with a *Controller Type* of *Articulated Hand*.</span></span> <span data-ttu-id="e438e-116">Una precostruzione personalizzata può essere usata purché implementi la [`SpherePointer`](xref:Microsoft.MixedReality.Toolkit.Input.SpherePointer) classe.</span><span class="sxs-lookup"><span data-stu-id="e438e-116">A custom prefab can be utilized as long as it implements the [`SpherePointer`](xref:Microsoft.MixedReality.Toolkit.Input.SpherePointer) class.</span></span>

    ![Esempio di profilo del puntatore per la cattura](../images/input/Pointers/GrabPointer_MRTKProfile.png)

    <span data-ttu-id="e438e-118">Il puntatore di recupero predefinito esegue una query per gli oggetti vicini in un cono intorno al punto di recupero per trovare la corrispondenza con l'interfaccia predefinita Hololens 2.</span><span class="sxs-lookup"><span data-stu-id="e438e-118">The default grab pointer queries for nearby objects in a cone around the grab point to match the default Hololens 2 interface.</span></span>

    ![Puntatore a pinza conica](https://user-images.githubusercontent.com/39840334/82500569-72d58300-9aa8-11ea-8102-ec9a62832d4e.png)

1. <span data-ttu-id="e438e-120">Sul GameObject che deve essere afferrabile, aggiungere un [`NearInteractionGrabbable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionGrabbable) , nonché un Collider.</span><span class="sxs-lookup"><span data-stu-id="e438e-120">On the GameObject that should be grabbable, add a [`NearInteractionGrabbable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionGrabbable), as well as a collider.</span></span>

    <span data-ttu-id="e438e-121">Verificare che il livello di GameObject sia in un livello di acquisizione.</span><span class="sxs-lookup"><span data-stu-id="e438e-121">Make sure the layer of the GameObject is on a grabbable layer.</span></span> <span data-ttu-id="e438e-122">Per impostazione predefinita, tutti i livelli ad eccezione di *consapevolezza spaziale* e *ignorano Raycasts* sono afferrabili.</span><span class="sxs-lookup"><span data-stu-id="e438e-122">By default, all layers except *Spatial Awareness* and *Ignore Raycasts* are grabbable.</span></span> <span data-ttu-id="e438e-123">Vedere quali livelli sono afferrabili controllando le *maschere del livello* di acquisizione nella prefabbricazione *GrabPointer* .</span><span class="sxs-lookup"><span data-stu-id="e438e-123">See which layers are grabbable by inspecting the *Grab Layer Masks* in your *GrabPointer* prefab.</span></span>

1. <span data-ttu-id="e438e-124">In GameObject o in uno dei relativi predecessori aggiungere un componente script che implementi l' [`IMixedRealityPointerHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityPointerHandler) interfaccia.</span><span class="sxs-lookup"><span data-stu-id="e438e-124">On the GameObject or one of its ancestors, add a script component that implements the [`IMixedRealityPointerHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityPointerHandler) interface.</span></span> <span data-ttu-id="e438e-125">Qualsiasi predecessore dell'oggetto con l'oggetto [`NearInteractionGrabbable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionGrabbable) sarà in grado di ricevere anche gli eventi puntatore.</span><span class="sxs-lookup"><span data-stu-id="e438e-125">Any ancestor of the object with the [`NearInteractionGrabbable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionGrabbable) will be able to receive pointer events, as well.</span></span>

### <a name="grab-code-example"></a><span data-ttu-id="e438e-126">Esempio di codice di recupero</span><span class="sxs-lookup"><span data-stu-id="e438e-126">Grab code example</span></span>

<span data-ttu-id="e438e-127">Di seguito è riportato uno script che stampa se un evento è un tocco o una cattura.</span><span class="sxs-lookup"><span data-stu-id="e438e-127">Below is a script that will print if an event is a touch or grab.</span></span> <span data-ttu-id="e438e-128">Nella funzione di interfaccia *IMixedRealityPointerHandler* pertinente, è possibile esaminare il tipo di puntatore che attiva l'evento tramite [`MixedRealityPointerEventData`](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityPointerEventData) .</span><span class="sxs-lookup"><span data-stu-id="e438e-128">In the relevant *IMixedRealityPointerHandler* interface function, one can look at the type of pointer that triggers that event via the [`MixedRealityPointerEventData`](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityPointerEventData).</span></span> <span data-ttu-id="e438e-129">Se il puntatore è un *SpherePointer*, l'interazione è una cattura.</span><span class="sxs-lookup"><span data-stu-id="e438e-129">If the pointer is a *SpherePointer*, the interaction is a grab.</span></span>

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

## <a name="add-touch-interactions"></a><span data-ttu-id="e438e-130">Aggiungere interazioni tocco</span><span class="sxs-lookup"><span data-stu-id="e438e-130">Add touch interactions</span></span>

<span data-ttu-id="e438e-131">Il processo per l'aggiunta di interazioni tocco sugli elementi UnityUI è diverso rispetto a quello per Vanilla 3D GameObject.</span><span class="sxs-lookup"><span data-stu-id="e438e-131">The process for adding touch interactions on UnityUI elements is different than for vanilla 3D GameObjects.</span></span> <span data-ttu-id="e438e-132">È possibile passare alla sezione seguente, *interfaccia utente di Unity*, per abilitare i componenti dell'interfaccia utente di Unity.</span><span class="sxs-lookup"><span data-stu-id="e438e-132">You can skip to the following section, *Unity UI*, for enabling Unity UI components.</span></span>

<span data-ttu-id="e438e-133">Per **entrambi** i tipi di elementi UX, verificare tuttavia che [PokePointer](pointers.md#pokepointer) sia registrato nel *profilo puntatore MRTK*.</span><span class="sxs-lookup"><span data-stu-id="e438e-133">For **both** types of UX elements though, ensure a [PokePointer](pointers.md#pokepointer) is registered in the *MRTK Pointer profile*.</span></span>

<span data-ttu-id="e438e-134">Il profilo MRTK predefinito e il profilo HoloLens 2 predefinito contengono già un *PokePointer*.</span><span class="sxs-lookup"><span data-stu-id="e438e-134">The default MRTK profile and the default HoloLens 2 profile already contain a *PokePointer*.</span></span> <span data-ttu-id="e438e-135">È possibile verificare che venga creato un PokePointer selezionando il profilo di configurazione MRTK e passare a puntatore di **input**  >    >  **Opzioni puntatore**.</span><span class="sxs-lookup"><span data-stu-id="e438e-135">One can confirm a PokePointer will be created by selecting the MRTK Configuration Profile and navigate to **Input** > **Pointers** > **Pointer Options**.</span></span> <span data-ttu-id="e438e-136">La `PokePointer` prefabbricazione predefinita (assets/MRTK/SDK/features/UX/Prefabbricates/puntatori) deve essere elencata con un *tipo di controller* a *mano articolata*.</span><span class="sxs-lookup"><span data-stu-id="e438e-136">The default `PokePointer` (Assets/MRTK/SDK/Features/UX/Prefabs/Pointers) prefab should be listed with a *Controller Type* of *Articulated Hand*.</span></span> <span data-ttu-id="e438e-137">Una precostruzione personalizzata può essere usata purché implementi la [`PokePointer`](xref:Microsoft.MixedReality.Toolkit.Input.PokePointer) classe.</span><span class="sxs-lookup"><span data-stu-id="e438e-137">A custom prefab can be utilized as long as it implements the [`PokePointer`](xref:Microsoft.MixedReality.Toolkit.Input.PokePointer) class.</span></span>

![Esempio di profilo puntatore poke](../images/input/Pointers/PokePointer_MRTKProfile.png)

### <a name="3d-gameobjects"></a><span data-ttu-id="e438e-139">GameObject 3D</span><span class="sxs-lookup"><span data-stu-id="e438e-139">3D GameObjects</span></span>

<span data-ttu-id="e438e-140">Esistono due modi diversi per aggiungere interazioni di tocco a GameObject 3D, a seconda che l'oggetto 3D debba avere solo un singolo piano toccabile o se deve essere toccabile in base all'intero Collider.</span><span class="sxs-lookup"><span data-stu-id="e438e-140">There are two different ways of adding touch interactions to 3D GameObjects, depending on if your 3d object should only have a single touchable plane, or of if it should be touchable based on its entire collider.</span></span>
<span data-ttu-id="e438e-141">Il primo consiste in genere negli oggetti con BoxColliders, in cui è preferibile avere una sola faccia del Collider React per gli eventi di tocco.</span><span class="sxs-lookup"><span data-stu-id="e438e-141">The first way is typically on objects with BoxColliders, where it is desired to only have a single face of the collider react to touch events.</span></span> <span data-ttu-id="e438e-142">L'altro è per gli oggetti che devono essere toccabili da qualsiasi direzione in base al relativo Collider.</span><span class="sxs-lookup"><span data-stu-id="e438e-142">The other is for objects that need to be touchable from any direction based on their collider.</span></span>

### <a name="single-face-touch"></a><span data-ttu-id="e438e-143">Tocco a faccia singola</span><span class="sxs-lookup"><span data-stu-id="e438e-143">Single face touch</span></span>

<span data-ttu-id="e438e-144">Questa operazione è utile per abilitare situazioni in cui è necessario che solo un singolo Face sia toccabile.</span><span class="sxs-lookup"><span data-stu-id="e438e-144">This is useful to enable situations where only a single face needs to be touchable.</span></span> <span data-ttu-id="e438e-145">Questa opzione presuppone che l'oggetto gioco disponga di un BoxCollider.</span><span class="sxs-lookup"><span data-stu-id="e438e-145">This option assumes that the game object has a BoxCollider.</span></span> <span data-ttu-id="e438e-146">è possibile usarlo con oggetti non BoxCollider, nel qual caso le proprietà' Bounds ' è local Center ' devono essere impostate manualmente per configurare il piano toccabile (ovvero i limiti devono essere impostati su un valore diverso da zero).</span><span class="sxs-lookup"><span data-stu-id="e438e-146">it's possible to use this with non-BoxCollider objects, in which case the 'Bounds' and 'Local Center' properties much be manually set to configure the touchable plane (i.e. Bounds should be set to a non-zero-zero value).</span></span>

1. <span data-ttu-id="e438e-147">In GameObject che devono essere toccabili, aggiungere un BoxCollider e un componente [ `NearInteractionTouchable` ] (xrif: Microsoft. MixedReality. Toolkit. input. NearInteractionTouchable).</span><span class="sxs-lookup"><span data-stu-id="e438e-147">On the GameObject that should be touchable, add a BoxCollider and a [`NearInteractionTouchable`] (xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) component.</span></span>

    1. <span data-ttu-id="e438e-148">Impostare **gli eventi da ricevere** per il *tocco* se si usa l' `IMixedRealityTouchHandler` interfaccia [] (xrif: Microsoft. MixedReality. Toolkit. input. IMixedRealityTouchHandler) nello script componente seguente.</span><span class="sxs-lookup"><span data-stu-id="e438e-148">Set **Events to Receive** to *Touch* if using the [`IMixedRealityTouchHandler`] (xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler) interface in your component script below.</span></span>

    1. <span data-ttu-id="e438e-149">Fare clic su **Correggi limiti** e **Correggi al centro**</span><span class="sxs-lookup"><span data-stu-id="e438e-149">Click **Fix bounds** and **Fix center**</span></span>

    ![Installazione di NearInteractionTouchable](../images/input/Pointers/NearInteractionTouchableSetup.gif)

1. <span data-ttu-id="e438e-151">In tale oggetto o in uno dei relativi predecessori aggiungere un componente script che implementi il [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler)</span><span class="sxs-lookup"><span data-stu-id="e438e-151">On that object or one of its ancestors, add a script component that implements the [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler)</span></span>
   <span data-ttu-id="e438e-152">.</span><span class="sxs-lookup"><span data-stu-id="e438e-152">interface.</span></span> <span data-ttu-id="e438e-153">Qualsiasi predecessore dell'oggetto con [ `NearInteractionTouchable` ] (xrif: Microsoft. MixedReality. Toolkit. input. NearInteractionTouchable) sarà in grado di ricevere anche gli eventi puntatore.</span><span class="sxs-lookup"><span data-stu-id="e438e-153">Any ancestor of the object with the [`NearInteractionTouchable`] (xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) will be able to receive pointer events, as well.</span></span>

> [!NOTE]
> <span data-ttu-id="e438e-154">Nella visualizzazione della scena dell'editor con *NearInteractionTouchable* GameObject selezionato, si noti un contorno bianco e una freccia.</span><span class="sxs-lookup"><span data-stu-id="e438e-154">In the editor scene view with the *NearInteractionTouchable* GameObject selected, notice a white outline square and arrow.</span></span> <span data-ttu-id="e438e-155">La freccia punta alla "parte anteriore" del touchable.</span><span class="sxs-lookup"><span data-stu-id="e438e-155">The arrow points to the "front" of the touchable.</span></span> <span data-ttu-id="e438e-156">La collisione potrà essere toccabile solo da tale direzione.</span><span class="sxs-lookup"><span data-stu-id="e438e-156">The collidable will only be touchable from that direction.</span></span> <span data-ttu-id="e438e-157">Per rendere un Collider toccabile da tutte le direzioni, vedere la sezione sul [tocco di Collider arbitrario](#arbitrary-collider-touch).</span><span class="sxs-lookup"><span data-stu-id="e438e-157">To make a collider touchable from all directions, see the section on [arbitrary collider touch](#arbitrary-collider-touch).</span></span>
> <span data-ttu-id="e438e-158">![Gizmo NearInteractionTouchable ](../images/input/Pointers/NearInteractionTouchableGizmos.png)</span><span class="sxs-lookup"><span data-stu-id="e438e-158">![NearInteractionTouchable Gizmos ](../images/input/Pointers/NearInteractionTouchableGizmos.png)</span></span>

### <a name="arbitrary-collider-touch"></a><span data-ttu-id="e438e-159">Tocco di Collider arbitrario</span><span class="sxs-lookup"><span data-stu-id="e438e-159">Arbitrary collider touch</span></span>

<span data-ttu-id="e438e-160">Questa operazione è utile per consentire situazioni in cui l'oggetto gioco deve essere toccabile lungo l'intero volto di Collider.</span><span class="sxs-lookup"><span data-stu-id="e438e-160">This is useful to enable situations where the game object needs to be touchable along its entire collider face.</span></span> <span data-ttu-id="e438e-161">Ad esempio, può essere usato per abilitare le interazioni di tocco per un oggetto con un SphereCollider, in cui l'intero Collider deve essere toccabile.</span><span class="sxs-lookup"><span data-stu-id="e438e-161">For example, this can be used to enable touch interactions for an object with a SphereCollider, where the entire collider needs to be touchable.</span></span>

1. <span data-ttu-id="e438e-162">In GameObject che devono essere toccabili, aggiungere un componente Collider e un componente [ `NearInteractionTouchableVolume` ] (xrif: Microsoft. MixedReality. Toolkit. input. NearInteractionTouchableVolume).</span><span class="sxs-lookup"><span data-stu-id="e438e-162">On the GameObject that should be touchable, add a collider and a [`NearInteractionTouchableVolume`] (xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchableVolume) component.</span></span>

    1. <span data-ttu-id="e438e-163">Impostare **gli eventi da ricevere** per il *tocco* se si usa l' `IMixedRealityTouchHandler` interfaccia [] (xrif: Microsoft. MixedReality. Toolkit. input. IMixedRealityTouchHandler) nello script componente seguente.</span><span class="sxs-lookup"><span data-stu-id="e438e-163">Set **Events to Receive** to *Touch* if using the [`IMixedRealityTouchHandler`] (xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler) interface in your component script below.</span></span>

1. <span data-ttu-id="e438e-164">In tale oggetto o in uno dei relativi predecessori aggiungere un componente script che implementi il [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler)</span><span class="sxs-lookup"><span data-stu-id="e438e-164">On that object or one of its ancestors, add a script component that implements the [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler)</span></span>
   <span data-ttu-id="e438e-165">.</span><span class="sxs-lookup"><span data-stu-id="e438e-165">interface.</span></span> <span data-ttu-id="e438e-166">Qualsiasi predecessore dell'oggetto con [ `NearInteractionTouchable` ] (xrif: Microsoft. MixedReality. Toolkit. input. NearInteractionTouchable) sarà in grado di ricevere anche gli eventi puntatore.</span><span class="sxs-lookup"><span data-stu-id="e438e-166">Any ancestor of the object with the [`NearInteractionTouchable`] (xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) will be able to receive pointer events, as well.</span></span>

### <a name="unity-ui"></a><span data-ttu-id="e438e-167">Interfaccia utente di Unity</span><span class="sxs-lookup"><span data-stu-id="e438e-167">Unity UI</span></span>

1. <span data-ttu-id="e438e-168">Aggiungere/verificare che nella scena sia presente un' [area di disegno UnityUI](https://docs.unity3d.com/Manual/UICanvas.html) .</span><span class="sxs-lookup"><span data-stu-id="e438e-168">Add/ensure there is a [UnityUI canvas](https://docs.unity3d.com/Manual/UICanvas.html) in the scene.</span></span>

1. <span data-ttu-id="e438e-169">In GameObject che deve essere toccabile aggiungere un [`NearInteractionTouchableUnityUI`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchableUnityUI) componente.</span><span class="sxs-lookup"><span data-stu-id="e438e-169">On the GameObject that should be touchable, add a [`NearInteractionTouchableUnityUI`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchableUnityUI) component.</span></span>  

    1. <span data-ttu-id="e438e-170">Impostare **gli eventi da ricevere** per il *tocco* se si usa l' [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler) interfaccia nello script dei componenti riportato di seguito.</span><span class="sxs-lookup"><span data-stu-id="e438e-170">Set **Events to Receive** to *Touch* if using the [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler) interface in your component script below.</span></span>

1. <span data-ttu-id="e438e-171">In tale oggetto o in uno dei relativi predecessori aggiungere un componente script che implementi l' [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler) interfaccia.</span><span class="sxs-lookup"><span data-stu-id="e438e-171">On that object or one of its ancestors, add a script component that implements the [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler) interface.</span></span> <span data-ttu-id="e438e-172">Qualsiasi predecessore dell'oggetto con il [`NearInteractionTouchableUnityUI`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchableUnityUI) sarà in grado di ricevere anche eventi puntatore.</span><span class="sxs-lookup"><span data-stu-id="e438e-172">Any ancestor of the object with the [`NearInteractionTouchableUnityUI`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchableUnityUI) will be able to receive pointer events as well.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e438e-173">Nel `NearInteractionTouchable` componente script, per gli *eventi di proprietà da ricevere* sono disponibili due opzioni: *pointer* e *touch*.</span><span class="sxs-lookup"><span data-stu-id="e438e-173">On the `NearInteractionTouchable` script component, for the property *Events to Receive* there are two options: *Pointer* and *Touch*.</span></span> <span data-ttu-id="e438e-174">Impostare *gli eventi da ricevere* al *puntatore* se si utilizza l' [`IMixedRealityPointerHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityPointerHandler) interfaccia e impostare su *touch* se si utilizza l' [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler) interfaccia nello script componente che risponde/gestisce gli eventi di input.</span><span class="sxs-lookup"><span data-stu-id="e438e-174">Set *Events to Receive* to *Pointer* if using the [`IMixedRealityPointerHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityPointerHandler) interface and set to *Touch* if using the [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler) interface in your component script that responds/handles the input events.</span></span>

#### <a name="touch-code-example"></a><span data-ttu-id="e438e-175">Esempio di codice tocco</span><span class="sxs-lookup"><span data-stu-id="e438e-175">Touch code example</span></span>

<span data-ttu-id="e438e-176">Il codice riportato di seguito illustra un monocomportamento che può essere collegato a un GameObject con un [`NearInteractionTouchable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) componente Variant e rispondere agli eventi di input di tocco.</span><span class="sxs-lookup"><span data-stu-id="e438e-176">The code below demonstrates a MonoBehaviour that can be attached to a GameObject with a [`NearInteractionTouchable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) variant component and respond to touch input events.</span></span>

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

## <a name="near-interaction-script-examples"></a><span data-ttu-id="e438e-177">Esempi di script near Interaction</span><span class="sxs-lookup"><span data-stu-id="e438e-177">Near interaction script examples</span></span>

### <a name="touch-events"></a><span data-ttu-id="e438e-178">Eventi di tocco</span><span class="sxs-lookup"><span data-stu-id="e438e-178">Touch events</span></span>

<span data-ttu-id="e438e-179">Questo esempio crea un cubo, lo rende toccabile e cambia il colore del tocco.</span><span class="sxs-lookup"><span data-stu-id="e438e-179">This example creates a cube, makes it touchable, and changes color on touch.</span></span>

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

### <a name="grab-events"></a><span data-ttu-id="e438e-180">Acquisisci eventi</span><span class="sxs-lookup"><span data-stu-id="e438e-180">Grab events</span></span>

<span data-ttu-id="e438e-181">Nell'esempio seguente viene illustrato come creare un GameObject trascinabile.</span><span class="sxs-lookup"><span data-stu-id="e438e-181">The below example shows how to make a GameObject draggable.</span></span> <span data-ttu-id="e438e-182">Presuppone che l'oggetto gioco disponga di un Collider.</span><span class="sxs-lookup"><span data-stu-id="e438e-182">Assumes that the game object has a collider on it.</span></span>

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

## <a name="useful-apis"></a><span data-ttu-id="e438e-183">API utili</span><span class="sxs-lookup"><span data-stu-id="e438e-183">Useful APIs</span></span>

* [`NearInteractionGrabbable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionGrabbable)
* [`NearInteractionTouchable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable)
* [`NearInteractionTouchableUnityUI`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchableUnityUI)
* [`NearInteractionTouchableVolume`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchableVolume)
* [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler)
* [`IMixedRealityPointerHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityPointerHandler)

## <a name="see-also"></a><span data-ttu-id="e438e-184">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="e438e-184">See also</span></span>

* [<span data-ttu-id="e438e-185">Cenni preliminari sull'input</span><span class="sxs-lookup"><span data-stu-id="e438e-185">Input Overview</span></span>](overview.md)
* [<span data-ttu-id="e438e-186">Pointers</span><span class="sxs-lookup"><span data-stu-id="e438e-186">Pointers</span></span>](pointers.md)
* [<span data-ttu-id="e438e-187">Eventi di input</span><span class="sxs-lookup"><span data-stu-id="e438e-187">Input Events</span></span>](input-events.md)

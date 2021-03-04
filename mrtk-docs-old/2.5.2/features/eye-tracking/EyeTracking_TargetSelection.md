---
title: EyeTracking_TargetSelection
description: Come accedere ai dati degli occhi e agli eventi specifici degli sguardi per selezionare le destinazioni in MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, EyeTracking,
ms.openlocfilehash: 4863f93a2b3015c3fc499532d500e4cf4d21d705
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/03/2021
ms.locfileid: "101783282"
---
# <a name="eye-supported-target-selection"></a><span data-ttu-id="84306-104">Selezione della destinazione supportata dagli occhi</span><span class="sxs-lookup"><span data-stu-id="84306-104">Eye-supported target selection</span></span>

![Selezione destinazione MRTK](../images/eye-tracking/mrtk_et_targetselect.png)

<span data-ttu-id="84306-106">In questa pagina vengono illustrate diverse opzioni per l'accesso ai dati degli occhi e agli eventi specifici degli sguardi per selezionare le destinazioni in MRTK.</span><span class="sxs-lookup"><span data-stu-id="84306-106">This page discusses different options for accessing eye gaze data and eye gaze specific events to select targets in MRTK.</span></span> <span data-ttu-id="84306-107">Il rilevamento degli occhi consente selezioni di destinazione rapide e veloci utilizzando una combinazione di informazioni sugli elementi che un utente sta esaminando con input aggiuntivi, ad esempio il _rilevamento manuale_ e i _comandi vocali_:</span><span class="sxs-lookup"><span data-stu-id="84306-107">Eye tracking allows for fast and effortless target selections using a combination of information about what a user is looking at with additional inputs such as _hand tracking_ and _voice commands_:</span></span>

- <span data-ttu-id="84306-108">Osservare & pronunciare _"Select"_ (comando Voice predefinito)</span><span class="sxs-lookup"><span data-stu-id="84306-108">Look & Say _"Select"_ (default voice command)</span></span>
- <span data-ttu-id="84306-109">Look & Say _"Explode"_ o _"pop"_ (Custom Voice Commands)</span><span class="sxs-lookup"><span data-stu-id="84306-109">Look & Say _"Explode"_ or _"Pop"_ (custom voice commands)</span></span>
- <span data-ttu-id="84306-110">Cerca & pulsante Bluetooth</span><span class="sxs-lookup"><span data-stu-id="84306-110">Look & Bluetooth button</span></span>
- <span data-ttu-id="84306-111">Si osservi & pizzico (ad esempio, tenete la mano davanti all'utente e si riuniscono il pollice e l'indice)</span><span class="sxs-lookup"><span data-stu-id="84306-111">Look & Pinch (i.e., hold up your hand in front of you and bring your thumb and index finger together)</span></span>
  - <span data-ttu-id="84306-112">Si noti che per il corretto funzionamento, [è necessario disabilitare i raggi della mano](EyeTracking_EyesAndHands.md#how-to-disable-the-hand-ray)</span><span class="sxs-lookup"><span data-stu-id="84306-112">Please note that for this to work, the [hand rays need to be disabled](EyeTracking_EyesAndHands.md#how-to-disable-the-hand-ray)</span></span>

<span data-ttu-id="84306-113">Per selezionare il contenuto olografico con Eye sguardi, sono disponibili diverse opzioni:</span><span class="sxs-lookup"><span data-stu-id="84306-113">To select holographic content using eye gaze, there are several options:</span></span>

[<span data-ttu-id="84306-114">**1. utilizzare il puntatore di stato attivo primario:**</span><span class="sxs-lookup"><span data-stu-id="84306-114">**1. Use the primary focus pointer:**</span></span>](#1-use-generic-focus-and-pointer-handlers)

<span data-ttu-id="84306-115">Questo può essere considerato come il cursore con priorità.</span><span class="sxs-lookup"><span data-stu-id="84306-115">This can be understood as your prioritized cursor.</span></span>
<span data-ttu-id="84306-116">Per impostazione predefinita, se le mani sono visualizzate, si tratta di raggi di mano.</span><span class="sxs-lookup"><span data-stu-id="84306-116">By default, if the hands are in view, then this would be hand rays.</span></span>
<span data-ttu-id="84306-117">Se non è presente alcuna mano, il puntatore con priorità è il punto di vista.</span><span class="sxs-lookup"><span data-stu-id="84306-117">If no hands are in view, then the prioritized pointer would be head or eye gaze.</span></span>
<span data-ttu-id="84306-118">Si noti, quindi, che in base alla testa di progettazione corrente o allo sguardo occhi viene eliminato come input del cursore se vengono usati i raggi mano.</span><span class="sxs-lookup"><span data-stu-id="84306-118">Thus, please note that based on the current design head or eye gaze is suppressed as a cursor input if hand rays are used.</span></span>

<span data-ttu-id="84306-119">Ad esempio:</span><span class="sxs-lookup"><span data-stu-id="84306-119">For example:</span></span>

<span data-ttu-id="84306-120">Un utente desidera selezionare un pulsante olografico remoto.</span><span class="sxs-lookup"><span data-stu-id="84306-120">A user wants to select a distant holographic button.</span></span>
<span data-ttu-id="84306-121">Gli sviluppatori desiderano fornire una soluzione flessibile che consenta all'utente di ottenere queste attività in diverse condizioni:</span><span class="sxs-lookup"><span data-stu-id="84306-121">As a developer, you want to provide a flexible solution that allows the user to achieve this tasks in various conditions:</span></span>

- <span data-ttu-id="84306-122">Passare al pulsante e incuriosirlo</span><span class="sxs-lookup"><span data-stu-id="84306-122">Walk up to the button and poke it</span></span>
- <span data-ttu-id="84306-123">Esaminarla da una distanza e pronunciare "Select"</span><span class="sxs-lookup"><span data-stu-id="84306-123">Look at it from a distance and say "select"</span></span>
- <span data-ttu-id="84306-124">Come destinazione del pulsante usando un raggio di mano ed eseguendo un pizzicotto in questo caso, la soluzione più flessibile consiste nell'usare il gestore dello stato attivo primario, in quanto invierà una notifica ogni volta che il puntatore di stato attivo primario con priorità corrente attiva un evento.</span><span class="sxs-lookup"><span data-stu-id="84306-124">Target the button using a hand ray and performing a pinch In this case, the most flexible solution is to use the primary focus handler as it will notify you whenever the currently prioritized primary focus pointer triggers an event.</span></span> <span data-ttu-id="84306-125">Si noti che se sono abilitati i raggi di mano, il puntatore a capo o a occhio è disabilitato non appena vengono visualizzate le lancette.</span><span class="sxs-lookup"><span data-stu-id="84306-125">Please note that if hand rays are enabled, the head or eye gaze focus pointer are disabled as soon as the hands come into view.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="84306-126">Si noti che se sono abilitati i raggi di mano, il puntatore a capo o a occhio è disabilitato non appena vengono visualizzate le lancette.</span><span class="sxs-lookup"><span data-stu-id="84306-126">Please note that if hand rays are enabled, the head or eye gaze focus pointer are disabled as soon as the hands come into view.</span></span> <span data-ttu-id="84306-127">Se si vuole supportare un'interazione [ _"look and Pinch"_ , è necessario disabilitare il raggio di mano](EyeTracking_EyesAndHands.md#how-to-disable-the-hand-ray).</span><span class="sxs-lookup"><span data-stu-id="84306-127">If you want to support a [_'look and pinch'_ interaction, you need to disable the hand ray](EyeTracking_EyesAndHands.md#how-to-disable-the-hand-ray).</span></span> <span data-ttu-id="84306-128">Nelle scene di esempio di analisi degli occhi è stato disabilitato il raggio della mano per consentire la presentazione di interazioni più ricche con gli occhi e i movimenti di mano. vedere ad esempio [posizionamento con supporto oculare](EyeTracking_Positioning.md).</span><span class="sxs-lookup"><span data-stu-id="84306-128">In our eye tracking sample scenes, we have disabled the hand ray to allow for showcasing richer interactions using eyes + hand motions - see for example [Eye-Supported Positioning](EyeTracking_Positioning.md).</span></span>

[<span data-ttu-id="84306-129">**2. utilizzare lo stato attivo per gli occhi e i raggi della mano contemporaneamente:**</span><span class="sxs-lookup"><span data-stu-id="84306-129">**2. Use both eye focus and hand rays at the same time:**</span></span>](#2-independent-eye-gaze-specific-eyetrackingtarget)

<span data-ttu-id="84306-130">Potrebbero essere presenti istanze in cui si desidera essere più specifici del tipo di puntatori di interesse che può attivare determinati eventi e consentire simultaneamente l'utilizzo di più tecniche di interazione a distanza.</span><span class="sxs-lookup"><span data-stu-id="84306-130">There might be instances where you want to be more specific which type of focus pointers can trigger certain events and allow for simultaneously using multiple far interaction techniques.</span></span>

<span data-ttu-id="84306-131">Nell'app, ad esempio, un utente può usare raggi lontani per modificare alcune configurazioni meccaniche olografiche. ad esempio, afferrare e mantenere alcune parti del motore olografico distanti e mantenerle sul posto.</span><span class="sxs-lookup"><span data-stu-id="84306-131">For example: In your app, a user can use far hand rays to manipulate some holographic mechanical setup - e.g., grab and hold some distant holographic engine parts and hold them in place.</span></span> <span data-ttu-id="84306-132">Quando si esegue questa operazione, l'utente deve eseguire una serie di istruzioni e registrarne lo stato di avanzamento contrassegnando alcune caselle di controllo.</span><span class="sxs-lookup"><span data-stu-id="84306-132">While doing so, the user has to go through a number of instructions and record her/his progress by marking off some check boxes.</span></span> <span data-ttu-id="84306-133">Se l'utente ha le proprie mani _non occupate_, sarà istintivo toccare semplicemente la casella di controllo o selezionarla usando un raggio di mano.</span><span class="sxs-lookup"><span data-stu-id="84306-133">If the user has her/his hands _not busy_, it would be instinctual to simply touch the check box or select it using a hand ray.</span></span> <span data-ttu-id="84306-134">Tuttavia, se l'utente ha le sue mani occupate, come nel caso di alcune parti del motore olografiche, si desidera consentire all'utente di scorrere facilmente le istruzioni usando il proprio sguardo ed esaminare semplicemente una casella di controllo e pronunciare "check!".</span><span class="sxs-lookup"><span data-stu-id="84306-134">However, if the user has her/his hands busy, as in our case holding some holographic engine parts in place, you want to enable the user to seamlessly scroll through the instructions using their eye gaze and to simply look at a check box and say "check it!".</span></span>

<span data-ttu-id="84306-135">Per abilitare questa operazione, è necessario usare uno script EyeTrackingTarget specifico per gli occhi, che è indipendente dal FocusHandlers Core MRTK e verrà illustrato più avanti.</span><span class="sxs-lookup"><span data-stu-id="84306-135">To enable this, you need to use eye-specific EyeTrackingTarget script that is independent from the core MRTK FocusHandlers and will be discussed further below.</span></span>

## <a name="1-use-generic-focus-and-pointer-handlers"></a><span data-ttu-id="84306-136">1. utilizzare i gestori di puntatore e messa a fuoco generici</span><span class="sxs-lookup"><span data-stu-id="84306-136">1. Use generic focus and pointer handlers</span></span>

<span data-ttu-id="84306-137">Se la verifica degli occhi è configurata correttamente (vedere il [programma di installazione di base di MRTK per l'uso degli](EyeTracking_BasicSetup.md)occhi), consentire agli utenti di selezionare gli ologrammi usando gli occhi è uguale a qualsiasi altro input dello stato attivo (ad esempio, lo sguardo a capo o il raggio della mano). Questo offre il grande vantaggio di un modo flessibile per interagire con gli ologrammi definendo il tipo di stato attivo principale nel profilo del puntatore di input di MRTK in base alle esigenze dell'utente, lasciando inalterato il codice.</span><span class="sxs-lookup"><span data-stu-id="84306-137">If eye tracking is set up correctly (see [Basic MRTK setup to use eye tracking](EyeTracking_BasicSetup.md)), enabling users to select holograms using their eyes is the same as for any other focus input (e.g., head gaze or hand ray).This provides the great advantage of a flexible way to interact with your holograms by defining the main focus type in your MRTK Input Pointer Profile depending on your user's needs, while leaving your code untouched.</span></span> <span data-ttu-id="84306-138">In questo modo è possibile passare da uno sguardo all'altro senza modificare una riga di codice o sostituire i raggi mano con la destinazione degli occhi per le interazioni.</span><span class="sxs-lookup"><span data-stu-id="84306-138">This allows for switching between head or eye gaze without changing a line of code or replace hand rays with eye targeting for far interactions.</span></span>

### <a name="focusing-on-a-hologram"></a><span data-ttu-id="84306-139">Concentrarsi su un ologramma</span><span class="sxs-lookup"><span data-stu-id="84306-139">Focusing on a hologram</span></span>

<span data-ttu-id="84306-140">Per rilevare quando un ologramma è concentrato, usare l'interfaccia _' IMixedRealityFocusHandler '_ che fornisce due membri di interfaccia: _OnFocusEnter_ e _OnFocusExit_.</span><span class="sxs-lookup"><span data-stu-id="84306-140">To detect when a hologram is focused, use the _'IMixedRealityFocusHandler'_ interface that provides you with two interface members: _OnFocusEnter_ and _OnFocusExit_.</span></span>

<span data-ttu-id="84306-141">Ecco un semplice esempio di [ColorTap.cs](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.ColorTap) per modificare il colore di un ologramma quando si esamina.</span><span class="sxs-lookup"><span data-stu-id="84306-141">Here is a simple example from [ColorTap.cs](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.ColorTap) to change a hologram's color when being looked at.</span></span>

```c#
public class ColorTap : MonoBehaviour, IMixedRealityFocusHandler
{
    void IMixedRealityFocusHandler.OnFocusEnter(FocusEventData eventData)
    {
        material.color = color_OnHover;
    }

    void IMixedRealityFocusHandler.OnFocusExit(FocusEventData eventData)
    {
        material.color = color_IdleState;
    }
    ...
}
```

### <a name="selecting-a-focused-hologram"></a><span data-ttu-id="84306-142">Selezione di un ologramma concentrato</span><span class="sxs-lookup"><span data-stu-id="84306-142">Selecting a focused hologram</span></span>

<span data-ttu-id="84306-143">Per selezionare un ologramma concentrato, usare _PointerHandler_ per restare in ascolto degli eventi di input per confermare una selezione.</span><span class="sxs-lookup"><span data-stu-id="84306-143">To select a focused hologram, use _PointerHandler_ to listen for input events to confirm a selection.</span></span>
<span data-ttu-id="84306-144">Ad esempio, se si aggiunge _IMixedRealityPointerHandler_ , i reagenti reagiranno a un semplice input del puntatore.</span><span class="sxs-lookup"><span data-stu-id="84306-144">For example, adding the _IMixedRealityPointerHandler_ will make them react to simple pointer input.</span></span>
<span data-ttu-id="84306-145">L'interfaccia _IMixedRealityPointerHandler_ richiede l'implementazione dei tre membri di interfaccia seguenti: _OnPointerUp_, _OnPointerDown_ e _OnPointerClicked_.</span><span class="sxs-lookup"><span data-stu-id="84306-145">The _IMixedRealityPointerHandler_ interface requires implementing the following three interface members: _OnPointerUp_, _OnPointerDown_, and _OnPointerClicked_.</span></span>

<span data-ttu-id="84306-146">Nell'esempio seguente viene modificato il colore di un ologramma guardandolo e pizzicando o dicendo "Select".</span><span class="sxs-lookup"><span data-stu-id="84306-146">In the example below, we change the color of a hologram by looking at it and pinching or saying "select".</span></span>
<span data-ttu-id="84306-147">L'azione necessaria per attivare l'evento è definita `eventData.MixedRealityInputAction == selectAction` in base alla quale è possibile impostare il tipo di `selectAction` nell'editor di Unity. per impostazione predefinita, si tratta dell'azione "Select".</span><span class="sxs-lookup"><span data-stu-id="84306-147">The required action to trigger the event is defined by `eventData.MixedRealityInputAction == selectAction` whereby we can set the type of `selectAction` in the Unity Editor - by default it's the "Select" action.</span></span> <span data-ttu-id="84306-148">I tipi di [MixedRealityInputActions](../Input/InputActions.md) disponibili possono essere configurati nel profilo MRTK tramite azioni di input di input del _profilo di configurazione di MRTK_  ->    ->  .</span><span class="sxs-lookup"><span data-stu-id="84306-148">The types of available [MixedRealityInputActions](../Input/InputActions.md) can be configured in the MRTK Profile via _MRTK Configuration Profile_ -> _Input_ -> _Input Actions_.</span></span>

```c#
public class ColorTap : MonoBehaviour, IMixedRealityFocusHandler, IMixedRealityPointerHandler
{
    // Allow for editing the type of select action in the Unity Editor.
    [SerializeField]
    private MixedRealityInputAction selectAction = MixedRealityInputAction.None;
    ...

    void IMixedRealityPointerHandler.OnPointerUp(MixedRealityPointerEventData eventData)
    {
        if (eventData.MixedRealityInputAction == selectAction)
        {
            material.color = color_OnHover;
        }
    }

    void IMixedRealityPointerHandler.OnPointerDown(MixedRealityPointerEventData eventData)
    {
        if (eventData.MixedRealityInputAction == selectAction)
        {
            material.color = color_OnSelect;
        }
    }

    void IMixedRealityPointerHandler.OnPointerClicked(MixedRealityPointerEventData eventData) { }
}
```

### <a name="eye-gaze-specific-baseeyefocushandler"></a><span data-ttu-id="84306-149">BaseEyeFocusHandler specifici degli sguardi</span><span class="sxs-lookup"><span data-stu-id="84306-149">Eye-gaze-specific BaseEyeFocusHandler</span></span>

<span data-ttu-id="84306-150">Considerato che gli occhi possono essere molto diversi da quelli degli altri input del puntatore, è opportuno assicurarsi di reagire all'input dello stato attivo solo se si tratta di un' _occhiata_ e si tratta attualmente del puntatore di input primario.</span><span class="sxs-lookup"><span data-stu-id="84306-150">Given that eye gaze can be very different to other pointer inputs, you may want to make sure to only react to the focus input if it is _eye gaze_ and it is currently the primary input pointer.</span></span>
<span data-ttu-id="84306-151">A questo scopo, è necessario usare l'oggetto [`BaseEyeFocusHandler`](xref:Microsoft.MixedReality.Toolkit.Input.BaseEyeFocusHandler) specifico del rilevamento degli occhi e che deriva da [`BaseFocusHandler`](xref:Microsoft.MixedReality.Toolkit.Input.BaseFocusHandler) .</span><span class="sxs-lookup"><span data-stu-id="84306-151">For this purpose, you would use the [`BaseEyeFocusHandler`](xref:Microsoft.MixedReality.Toolkit.Input.BaseEyeFocusHandler) which is specific to eye tracking and which derives from the [`BaseFocusHandler`](xref:Microsoft.MixedReality.Toolkit.Input.BaseFocusHandler).</span></span>
<span data-ttu-id="84306-152">Come indicato in precedenza, viene attivato solo se il targeting degli occhi è l'input del puntatore principale (ovvero, non è attivo alcun raggio di mano).</span><span class="sxs-lookup"><span data-stu-id="84306-152">As mentioned before, it will only trigger if eye gaze targeting is currently the primary pointer input (i.e., no hand ray is active).</span></span> <span data-ttu-id="84306-153">Per ulteriori informazioni, vedere [la pagina relativa alla modalità di supporto di sguardi a occhio e movimenti della mano](EyeTracking_EyesAndHands.md).</span><span class="sxs-lookup"><span data-stu-id="84306-153">For more information, see [How to support eye gaze + hand gestures](EyeTracking_EyesAndHands.md).</span></span>

<span data-ttu-id="84306-154">Di seguito è riportato un esempio di `EyeTrackingDemo-03-Navigation` (assets/MRTK/examples/Demos/eyetracking/scenes).</span><span class="sxs-lookup"><span data-stu-id="84306-154">Here is an example from `EyeTrackingDemo-03-Navigation` (Assets/MRTK/Examples/Demos/EyeTracking/Scenes).</span></span>
<span data-ttu-id="84306-155">In questa demo sono presenti due ologrammi 3D che diventeranno a seconda della parte dell'oggetto da esaminare: se l'utente osserva il lato sinistro dell'ologramma, la parte verrà spostata lentamente verso l'inizio dell'utente.</span><span class="sxs-lookup"><span data-stu-id="84306-155">In this demo, there are two 3D holograms that will turn depending on which part of the object is looked at: If the user looks at the left side of the hologram, then that part will slowly move towards the front facing the user.</span></span>
<span data-ttu-id="84306-156">Se si esamina il lato destro, la parte verrà spostata lentamente in primo piano.</span><span class="sxs-lookup"><span data-stu-id="84306-156">If the right side is looked at, then that part will slowly move to the front.</span></span>
<span data-ttu-id="84306-157">Si tratta di un comportamento che potrebbe non essere necessario attivare in qualsiasi momento e anche qualcosa che potrebbe non essere necessario attivare accidentalmente da un raggio di mano o da uno sguardo a capo.</span><span class="sxs-lookup"><span data-stu-id="84306-157">This is a behavior that you may not want to have active at all times and also something that you may not want to accidentally trigger by a hand ray or head gaze.</span></span>
<span data-ttu-id="84306-158">Con l'oggetto [`OnLookAtRotateByEyeGaze`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.OnLookAtRotateByEyeGaze) collegato, un GameObject verrà ruotato mentre viene esaminato.</span><span class="sxs-lookup"><span data-stu-id="84306-158">Having the [`OnLookAtRotateByEyeGaze`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.OnLookAtRotateByEyeGaze) attached, a GameObject will rotate while being looked at.</span></span>

```c#
public class OnLookAtRotateByEyeGaze : BaseEyeFocusHandler
{
    ...

    protected override void OnEyeFocusStay()
    {
        // Update target rotation
        RotateHitTarget();
    }

    ...

    ///
    /// This function computes the rotation of the target to move the currently
    /// looked at aspect slowly to the front.
    ///
    private void RotateHitTarget()
    {
        // Example for querying the hit position of the eye gaze ray using EyeGazeProvider
        Vector3 TargetToHit = (this.gameObject.transform.position - InputSystem.EyeGazeProvider.HitPosition).normalized;

        ...
    }
}
```

<span data-ttu-id="84306-159">Consultare la documentazione dell'API per un elenco completo degli eventi disponibili di [`BaseEyeFocusHandler`](xref:Microsoft.MixedReality.Toolkit.Input.BaseEyeFocusHandler) :</span><span class="sxs-lookup"><span data-stu-id="84306-159">Check the API documentation for a complete list of available events of the [`BaseEyeFocusHandler`](xref:Microsoft.MixedReality.Toolkit.Input.BaseEyeFocusHandler):</span></span>

- <span data-ttu-id="84306-160">**OnEyeFocusStart:** Attivato dopo che il raggio d'occhio *inizia* a intersecarsi con questo Collider della destinazione.</span><span class="sxs-lookup"><span data-stu-id="84306-160">**OnEyeFocusStart:** Triggered once the eye gaze ray *starts* intersecting with this target's collider.</span></span>
- <span data-ttu-id="84306-161">**OnEyeFocusStay:** Attivato *quando* il raggio di sguardi occhi si interseca con il Collider di questa destinazione.</span><span class="sxs-lookup"><span data-stu-id="84306-161">**OnEyeFocusStay:** Triggered *while* the eye gaze ray is intersecting with this target's collider.</span></span>
- <span data-ttu-id="84306-162">**OnEyeFocusStop:** Attivato quando il raggio di sguardi occhi *smette* di intersecarsi con questo Collider della destinazione.</span><span class="sxs-lookup"><span data-stu-id="84306-162">**OnEyeFocusStop:** Triggered once the eye gaze ray *stops* intersecting with this target's collider.</span></span>
- <span data-ttu-id="84306-163">**OnEyeFocusDwell:** Attivato dopo che il raggio d'occhio è stato intersecato con il Collider della destinazione per un periodo di tempo specificato.</span><span class="sxs-lookup"><span data-stu-id="84306-163">**OnEyeFocusDwell:** Triggered once the eye gaze ray has intersected with this target's collider for a specified amount of time.</span></span>

## <a name="2-independent-eye-gaze-specific-eyetrackingtarget"></a><span data-ttu-id="84306-164">2. EyeTrackingTarget specifici per gli occhi indipendenti</span><span class="sxs-lookup"><span data-stu-id="84306-164">2. Independent eye-gaze-specific EyeTrackingTarget</span></span>

<span data-ttu-id="84306-165">Infine, viene fornita una soluzione che consente di considerare l'input basato sugli occhi completamente indipendente dagli altri puntatori dello stato attivo tramite lo [`EyeTrackingTarget`](xref:Microsoft.MixedReality.Toolkit.Input.EyeTrackingTarget) script.</span><span class="sxs-lookup"><span data-stu-id="84306-165">Finally, we provide you with a solution that let's you treat eye-based input completely independent from other focus pointers via the [`EyeTrackingTarget`](xref:Microsoft.MixedReality.Toolkit.Input.EyeTrackingTarget) script.</span></span>

<span data-ttu-id="84306-166">Questa operazione presenta tre _vantaggi_:</span><span class="sxs-lookup"><span data-stu-id="84306-166">This has three _advantages_:</span></span>

- <span data-ttu-id="84306-167">È possibile assicurarsi che l'ologramma stia reagendo solo sugli sguardi dell'utente.</span><span class="sxs-lookup"><span data-stu-id="84306-167">You can make sure that the hologram is only reacting to the user's eye gaze.</span></span>
- <span data-ttu-id="84306-168">Questo è indipendente dall'input primario attualmente attivo.</span><span class="sxs-lookup"><span data-stu-id="84306-168">This is independent from the currently active primary input.</span></span> <span data-ttu-id="84306-169">Di conseguenza, è possibile elaborare più input contemporaneamente, ad esempio, combinando il targeting rapido con i movimenti della mano.</span><span class="sxs-lookup"><span data-stu-id="84306-169">Hence, you can process multiple inputs at once - for example, combining fast eye targeting with hand gestures.</span></span>
- <span data-ttu-id="84306-170">Molti eventi Unity sono già stati configurati in modo da velocizzare e semplificare la gestione e il riutilizzo dei comportamenti esistenti dall'editor di Unity o tramite codice.</span><span class="sxs-lookup"><span data-stu-id="84306-170">Several Unity events have already been set up to make it fast and convenient to handle and reuse existing behaviors from within the Unity Editor or via code.</span></span>

<span data-ttu-id="84306-171">Sono presenti anche alcuni _svantaggi:_</span><span class="sxs-lookup"><span data-stu-id="84306-171">There are also some _disadvantages:_</span></span>

- <span data-ttu-id="84306-172">Maggiore sforzo per gestire separatamente gli input separati.</span><span class="sxs-lookup"><span data-stu-id="84306-172">More effort to handle separate inputs individually.</span></span>
- <span data-ttu-id="84306-173">Nessun calo di eleganza: supporta solo l'individuazione degli occhi.</span><span class="sxs-lookup"><span data-stu-id="84306-173">No elegant degradation: It only supports eye targeting.</span></span> <span data-ttu-id="84306-174">Se la verifica degli occhi non funziona, è necessario un altro fallback.</span><span class="sxs-lookup"><span data-stu-id="84306-174">If eye tracking is not working, you require some additional fallback.</span></span>

<span data-ttu-id="84306-175">Analogamente a _BaseFocusHandler_, _EyeTrackingTarget_ è pronto con diversi eventi Unity specifici degli sguardi che è possibile ascoltare comodamente tramite l'editor di Unity (vedere l'esempio seguente) o usando _AddListener ()_ nel codice:</span><span class="sxs-lookup"><span data-stu-id="84306-175">Similar to the _BaseFocusHandler_, the _EyeTrackingTarget_ comes ready with several eye-gaze-specific Unity events that you can conveniently listen to either via the Unity Editor (see example below) or by using _AddListener()_ in code:</span></span>

- <span data-ttu-id="84306-176">OnLookAtStart()</span><span class="sxs-lookup"><span data-stu-id="84306-176">OnLookAtStart()</span></span>
- <span data-ttu-id="84306-177">WhileLookingAtTarget()</span><span class="sxs-lookup"><span data-stu-id="84306-177">WhileLookingAtTarget()</span></span>
- <span data-ttu-id="84306-178">OnLookAway()</span><span class="sxs-lookup"><span data-stu-id="84306-178">OnLookAway()</span></span>
- <span data-ttu-id="84306-179">Ondweller ()</span><span class="sxs-lookup"><span data-stu-id="84306-179">OnDwell()</span></span>
- <span data-ttu-id="84306-180">OnSelected ()</span><span class="sxs-lookup"><span data-stu-id="84306-180">OnSelected()</span></span>

<span data-ttu-id="84306-181">Di seguito vengono illustrati alcuni esempi di come usare _EyeTrackingTarget_.</span><span class="sxs-lookup"><span data-stu-id="84306-181">In the following, we walk you through a few examples for how to use _EyeTrackingTarget_.</span></span>

### <a name="example-1-eye-supported-smart-notifications"></a><span data-ttu-id="84306-182">Esempio di #1: notifiche intelligenti con supporto oculistico</span><span class="sxs-lookup"><span data-stu-id="84306-182">Example #1: Eye-supported smart notifications</span></span>

<span data-ttu-id="84306-183">In `EyeTrackingDemo-02-TargetSelection` (assets/MRTK/examples/Demos/eyetracking/scenes), è possibile trovare un esempio per _"notifiche attente intelligenti"_ che reagiscono a sguardi d'occhio.</span><span class="sxs-lookup"><span data-stu-id="84306-183">In `EyeTrackingDemo-02-TargetSelection` (Assets/MRTK/Examples/Demos/EyeTracking/Scenes), you can find an example for _'smart attentive notifications'_ that react to your eye gaze.</span></span>
<span data-ttu-id="84306-184">Si tratta di caselle di testo 3D che possono essere posizionate nella scena e che aumenteranno in modo uniforme e si rivolgono all'utente quando vengono esaminate per semplificare la leggibilità.</span><span class="sxs-lookup"><span data-stu-id="84306-184">These are 3D text boxes that can be placed in the scene and that will smoothly enlarge and turn toward the user when being looked at to ease legibility.</span></span> <span data-ttu-id="84306-185">Mentre l'utente sta leggendo la notifica, le informazioni continuano a essere visualizzate in modo nitido e chiaro.</span><span class="sxs-lookup"><span data-stu-id="84306-185">While the user is reading the notification, the information keeps getting displayed crisp and clear.</span></span> <span data-ttu-id="84306-186">Dopo la lettura e la visualizzazione della notifica, la notifica verrà eliminata automaticamente e verrà rilasciata. Per ottenere questo risultato, sono disponibili alcuni script di comportamento generici che non sono specifici del rilevamento degli occhi, ad esempio:</span><span class="sxs-lookup"><span data-stu-id="84306-186">After reading it and looking away from the notification, the notification will automatically be dismissed and fades out. To achieve all this, there are a few generic behavior scripts that are not specific to eye tracking at all, such as:</span></span>

- [`FaceUser`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.FaceUser)
- [`ChangeSize`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.ChangeSize)
- [`BlendOut`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.BlendOut)

<span data-ttu-id="84306-187">Il vantaggio di questo approccio è che gli stessi script possono essere riutilizzati da vari eventi.</span><span class="sxs-lookup"><span data-stu-id="84306-187">The advantage of this approach is that the same scripts can be reused by various events.</span></span> <span data-ttu-id="84306-188">Un ologramma, ad esempio, può iniziare ad affrontare l'utente in base a comandi vocali o dopo aver premuto un pulsante virtuale.</span><span class="sxs-lookup"><span data-stu-id="84306-188">For example, a hologram may start facing the user based on a voice commands or after pressing a virtual button.</span></span> <span data-ttu-id="84306-189">Per attivare questi eventi, è possibile fare riferimento semplicemente ai metodi che devono essere eseguiti nello [`EyeTrackingTarget`](xref:Microsoft.MixedReality.Toolkit.Input.EyeTrackingTarget) script associato al GameObject.</span><span class="sxs-lookup"><span data-stu-id="84306-189">To trigger these events, you can simply reference the methods that should be executed in the [`EyeTrackingTarget`](xref:Microsoft.MixedReality.Toolkit.Input.EyeTrackingTarget) script that is attached to your GameObject.</span></span>

<span data-ttu-id="84306-190">Per l'esempio relativo alle _notifiche attente intelligenti_, si verifica quanto segue:</span><span class="sxs-lookup"><span data-stu-id="84306-190">For the example of the _'smart attentive notifications'_, the following happens:</span></span>

- <span data-ttu-id="84306-191">**OnLookAtStart ()**: la notifica inizia con...</span><span class="sxs-lookup"><span data-stu-id="84306-191">**OnLookAtStart()**: The notification starts to...</span></span>
  - <span data-ttu-id="84306-192">*FaceUser. Engage:* ... rivolgersi all'utente.</span><span class="sxs-lookup"><span data-stu-id="84306-192">*FaceUser.Engage:* ... turn toward the user.</span></span>
  - <span data-ttu-id="84306-193">*ChangeSize. Engage:* ... aumento delle dimensioni _(fino a una scala massima specificata)_.</span><span class="sxs-lookup"><span data-stu-id="84306-193">*ChangeSize.Engage:* ... increase in size _(up to a specified maximum scale)_.</span></span>
  - <span data-ttu-id="84306-194">*Blend out. Engage:* ... inizia a combinare più _(dopo essere stato inattivo più sottile)_.</span><span class="sxs-lookup"><span data-stu-id="84306-194">*BlendOut.Engage:* ... starts to blend in more _(after being at a more subtle idle state)_.</span></span>  

- <span data-ttu-id="84306-195">**Ondweller ()**: informa lo script di _Blend_ che la notifica è stata esaminata in modo sufficientemente appropriato.</span><span class="sxs-lookup"><span data-stu-id="84306-195">**OnDwell()**: Informs the _BlendOut_ script that the notification has been looked at sufficiently.</span></span>

- <span data-ttu-id="84306-196">**OnLookAway ()**: la notifica inizia con...</span><span class="sxs-lookup"><span data-stu-id="84306-196">**OnLookAway()**: The notification starts to...</span></span>
  - <span data-ttu-id="84306-197">*FaceUser. Disengage:* ... tornare all'orientamento originale.</span><span class="sxs-lookup"><span data-stu-id="84306-197">*FaceUser.Disengage:* ... turn back to its original orientation.</span></span>
  - <span data-ttu-id="84306-198">*ChangeSize. Disengage:* ... Riduci le dimensioni originali.</span><span class="sxs-lookup"><span data-stu-id="84306-198">*ChangeSize.Disengage:* ... decrease back to its original size.</span></span>
  - <span data-ttu-id="84306-199">*Blend out. Disengage:* ... inizia a Blend out: se è stato attivato _ondweller ()_ , Blend out completamente e distruggi; in caso contrario, torna allo stato inattivo.</span><span class="sxs-lookup"><span data-stu-id="84306-199">*BlendOut.Disengage:* ... starts to blend out - If _OnDwell()_ was triggered, blend out completely and destroy, otherwise back to its idle state.</span></span>

<span data-ttu-id="84306-200">**Considerazioni sulla progettazione:** La chiave per una piacevole esperienza consiste nell'ottimizzare con attenzione la velocità di uno di questi comportamenti, in modo da evitare la causa del disagio rispondendo troppo rapidamente al punto di vista dell'utente.</span><span class="sxs-lookup"><span data-stu-id="84306-200">**Design consideration:** The key to an enjoyable experience here is to carefully tune the speed of any of these behaviors to avoid causing discomfort by reacting to the user’s eye gaze too quickly all the time.</span></span>
<span data-ttu-id="84306-201">In caso contrario, questa operazione può essere estremamente travolgente.</span><span class="sxs-lookup"><span data-stu-id="84306-201">Otherwise this can quickly feel extremely overwhelming.</span></span>

<img src="../images/eye-tracking/mrtk_et_EyeTrackingTarget_Notification.jpg" width="750" alt="MRTK Notification">

### <a name="example-2-holographic-gem-rotates-slowly-when-looking-at-it"></a><span data-ttu-id="84306-202">Esempio #2: la gemma olografica ruota lentamente durante la ricerca</span><span class="sxs-lookup"><span data-stu-id="84306-202">Example #2: Holographic gem rotates slowly when looking at it</span></span>

<span data-ttu-id="84306-203">Analogamente a #1 di esempio, è possibile creare facilmente un feedback del passaggio del mouse per le gemme olografiche in una `EyeTrackingDemo-02-TargetSelection` scena (assets/MRTK/examples/Demos/eyetracking/scenes) che verrà ruotata lentamente in una direzione costante e a una velocità costante (contrariamente all'esempio di rotazione precedente) quando viene esaminato.</span><span class="sxs-lookup"><span data-stu-id="84306-203">Similar to Example #1, we can easily create a hover feedback for our holographic gems in `EyeTrackingDemo-02-TargetSelection` (Assets/MRTK/Examples/Demos/EyeTracking/Scenes) scene that will slowly rotate in a constant direction and at a constant speed (in contrast to the rotation example from above) when being looked at.</span></span> <span data-ttu-id="84306-204">È sufficiente attivare la rotazione della gemma olografica dall'evento _WhileLookingAtTarget ()_ di _EyeTrackingTarget_.</span><span class="sxs-lookup"><span data-stu-id="84306-204">All you need is to trigger the rotation of the holographic gem from the _EyeTrackingTarget_'s _WhileLookingAtTarget()_ event.</span></span> <span data-ttu-id="84306-205">Ecco alcuni dettagli:</span><span class="sxs-lookup"><span data-stu-id="84306-205">Here are a few more details:</span></span>

1. <span data-ttu-id="84306-206">Creare uno script generico che includa una funzione pubblica per ruotare il GameObject a cui è collegato.</span><span class="sxs-lookup"><span data-stu-id="84306-206">Create a generic script that includes a public function to rotate the GameObject it is attached to.</span></span> <span data-ttu-id="84306-207">Di seguito è riportato un esempio di _RotateWithConstSpeedDir.cs_ in cui è possibile modificare la direzione e la velocità di rotazione dall'editor di Unity.</span><span class="sxs-lookup"><span data-stu-id="84306-207">Below is an example from _RotateWithConstSpeedDir.cs_ where we can tweak the rotation direction and speed from the Unity Editor.</span></span>

    ```c#
    using UnityEngine;

    namespace Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking
    {
        /// <summary>
        /// The associated GameObject will rotate when RotateTarget() is called based on a given direction and speed.
        /// </summary>
        public class RotateWithConstSpeedDir : MonoBehaviour
        {
            [Tooltip("Euler angles by which the object should be rotated by.")]
            [SerializeField]
            private Vector3 RotateByEulerAngles = Vector3.zero;

            [Tooltip("Rotation speed factor.")]
            [SerializeField]
            private float speed = 1f;

            /// <summary>
            /// Rotate game object based on specified rotation speed and Euler angles.
            /// </summary>
            public void RotateTarget()
            {
                transform.eulerAngles = transform.eulerAngles + RotateByEulerAngles * speed;
            }
        }
    }
    ```

1. <span data-ttu-id="84306-208">Aggiungere lo [`EyeTrackingTarget`](xref:Microsoft.MixedReality.Toolkit.Input.EyeTrackingTarget) script alla GameObject di destinazione e fare riferimento alla funzione _RotateTarget ()_ nel trigger UnityEvent, come illustrato nella schermata seguente:</span><span class="sxs-lookup"><span data-stu-id="84306-208">Add the [`EyeTrackingTarget`](xref:Microsoft.MixedReality.Toolkit.Input.EyeTrackingTarget) script to your target GameObject and reference the _RotateTarget()_ function in the UnityEvent trigger as shown the screenshot below:</span></span>

    ![Esempio EyeTrackingTarget](../images/eye-tracking/mrtk_et_EyeTrackingTargetSample.jpg)

### <a name="example-3-pop-those-gems-aka-_multi-modal-eye-gaze-supported-target-selection_"></a><span data-ttu-id="84306-210">Esempio di #3: pop The Gems aka _multimodale Eye-sguardi-supported target selection_</span><span class="sxs-lookup"><span data-stu-id="84306-210">Example #3: Pop those gems aka _multi-modal eye-gaze-supported target selection_</span></span>

<span data-ttu-id="84306-211">Nell'esempio precedente è stato illustrato quanto sia facile rilevare se una destinazione viene esaminata e come attivare una reazione.</span><span class="sxs-lookup"><span data-stu-id="84306-211">In the previous example, we have shown how easy it is to detect whether a target is looked at and how to trigger a reaction to that.</span></span> <span data-ttu-id="84306-212">A questo punto, fare in modo che le gemme esplodano usando l'evento _OnSelected ()_ da [`EyeTrackingTarget`](xref:Microsoft.MixedReality.Toolkit.Input.EyeTrackingTarget) .</span><span class="sxs-lookup"><span data-stu-id="84306-212">Next, let's make the gems explode using the _OnSelected()_ event from the [`EyeTrackingTarget`](xref:Microsoft.MixedReality.Toolkit.Input.EyeTrackingTarget).</span></span> <span data-ttu-id="84306-213">La parte interessante è la *modalità* di attivazione della selezione.</span><span class="sxs-lookup"><span data-stu-id="84306-213">The interesting part is *how* the selection is triggered.</span></span> <span data-ttu-id="84306-214">[`EyeTrackingTarget`](xref:Microsoft.MixedReality.Toolkit.Input.EyeTrackingTarget)Consente di assegnare rapidamente diversi modi per richiamare una selezione:</span><span class="sxs-lookup"><span data-stu-id="84306-214">The [`EyeTrackingTarget`](xref:Microsoft.MixedReality.Toolkit.Input.EyeTrackingTarget) allows for quickly assigning different ways to invoke a selection:</span></span>

- <span data-ttu-id="84306-215">_Gesto del pizzico_: l'impostazione dell'azione ' Select ' su' Select ' usa il gesto della mano predefinito per attivare la selezione.</span><span class="sxs-lookup"><span data-stu-id="84306-215">_Pinch gesture_: Setting the 'Select Action' to 'Select' uses the default hand gesture to trigger the selection.</span></span>
<span data-ttu-id="84306-216">Ciò significa che l'utente può semplicemente alzare la mano e pizzicare il pollice e l'indice insieme per confermare la selezione.</span><span class="sxs-lookup"><span data-stu-id="84306-216">This means that the user can simply raise their hand and pinch their thumb and index finger together to confirm the selection.</span></span>

- <span data-ttu-id="84306-217">Pronunciare _"Select"_: usare il comando Voice predefinito _"Select"_ per selezionare un ologramma.</span><span class="sxs-lookup"><span data-stu-id="84306-217">Say _"Select"_: Use the default voice command _"Select"_ for selecting a hologram.</span></span>

- <span data-ttu-id="84306-218">Pronunciare " _Esplodi"_ o _"pop"_: per usare i comandi vocali personalizzati, è necessario eseguire due passaggi:</span><span class="sxs-lookup"><span data-stu-id="84306-218">Say _"Explode"_ or _"Pop"_: To use custom voice commands, you need to follow two steps:</span></span>
    1. <span data-ttu-id="84306-219">Configurare un'azione personalizzata, ad esempio _"DestroyTarget"_</span><span class="sxs-lookup"><span data-stu-id="84306-219">Set up a custom action such as _"DestroyTarget"_</span></span>
        - <span data-ttu-id="84306-220">Passare a _MRTK-> input-> azioni di input_</span><span class="sxs-lookup"><span data-stu-id="84306-220">Navigate to _MRTK -> Input -> Input Actions_</span></span>
        - <span data-ttu-id="84306-221">Fare clic su "Aggiungi una nuova azione"</span><span class="sxs-lookup"><span data-stu-id="84306-221">Click "Add a new action"</span></span>

    2. <span data-ttu-id="84306-222">Configurare i comandi vocali che attivano questa azione, ad esempio _"Esplodi"_ o _"pop"_</span><span class="sxs-lookup"><span data-stu-id="84306-222">Set up the voice commands that trigger this action such as _"Explode"_ or _"Pop"_</span></span>
        - <span data-ttu-id="84306-223">Passare a _MRTK-> input-> Speech_</span><span class="sxs-lookup"><span data-stu-id="84306-223">Navigate to _MRTK -> Input -> Speech_</span></span>
        - <span data-ttu-id="84306-224">Fare clic su "Aggiungi un nuovo comando vocale"</span><span class="sxs-lookup"><span data-stu-id="84306-224">Click "Add a new speech command"</span></span>
            - <span data-ttu-id="84306-225">Associare l'azione appena creata</span><span class="sxs-lookup"><span data-stu-id="84306-225">Associate the action you just created</span></span>
            - <span data-ttu-id="84306-226">Assegnare un _KeyCode_ per consentire l'attivazione dell'azione tramite un pulsante premere</span><span class="sxs-lookup"><span data-stu-id="84306-226">Assign a _KeyCode_ to allow for triggering the action via a button press</span></span>

![Esempio di EyeTrackingTarget comandi vocali](../images/eye-tracking/mrtk_et_voicecmdsample.jpg)

<span data-ttu-id="84306-228">Quando si seleziona una gemma, l'operazione verrà esplosa, rendendo un suono e scomparirà.</span><span class="sxs-lookup"><span data-stu-id="84306-228">When a gem is selected it will explode, making a sound and disappear.</span></span> <span data-ttu-id="84306-229">Questa operazione viene gestita dallo [`HitBehaviorDestroyOnSelect`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.HitBehaviorDestroyOnSelect) script.</span><span class="sxs-lookup"><span data-stu-id="84306-229">This is handled by the [`HitBehaviorDestroyOnSelect`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.HitBehaviorDestroyOnSelect) script.</span></span> <span data-ttu-id="84306-230">Sono disponibili due opzioni:</span><span class="sxs-lookup"><span data-stu-id="84306-230">You have two options:</span></span>

- <span data-ttu-id="84306-231">**Nell'editor di Unity:** È sufficiente collegare lo script associato a ognuno dei modelli Gem all'evento OnSelected () Unity nell'editor di Unity.</span><span class="sxs-lookup"><span data-stu-id="84306-231">**In the Unity Editor:** You could simply link the script that is attached to each of our gem templates to the OnSelected() Unity event in the Unity Editor.</span></span>
- <span data-ttu-id="84306-232">**Nel codice:** Se non si desidera trascinare GameObject in questo modo, è anche possibile aggiungere semplicemente un listener di eventi direttamente allo script.</span><span class="sxs-lookup"><span data-stu-id="84306-232">**In code:** If you don't want to drag and drop GameObjects around, you can also simply add a event listener directly to your script.</span></span>  
<span data-ttu-id="84306-233">Di seguito è riportato un esempio di come è stato fatto nello [`HitBehaviorDestroyOnSelect`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.HitBehaviorDestroyOnSelect) script:</span><span class="sxs-lookup"><span data-stu-id="84306-233">Here's an example from how we did it in the [`HitBehaviorDestroyOnSelect`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.HitBehaviorDestroyOnSelect) script:</span></span>

```c#
/// <summary>
/// Destroys the game object when selected and optionally plays a sound or animation when destroyed.
/// </summary>
[RequireComponent(typeof(EyeTrackingTarget))] // This helps to ensure that the EyeTrackingTarget is attached
public class HitBehaviorDestroyOnSelect : MonoBehaviour
{
    ...
    private EyeTrackingTarget myEyeTrackingTarget = null;

    private void Start()
    {
        myEyeTrackingTarget = this.GetComponent<EyeTrackingTarget>();

        if (myEyeTrackingTarget != null)
        {
            myEyeTrackingTarget.OnSelected.AddListener(TargetSelected);
        }
    }

    ...

    ///
    /// This is called once the EyeTrackingTarget detected a selection.
    ///
    public void TargetSelected()
    {
        // Play some animation
        // Play some audio effect
        // Handle destroying the target appropriately
    }
}
```

### <a name="example-4-use-hand-rays-and-eye-gaze-input-together"></a><span data-ttu-id="84306-234">Esempio di #4: usare i raggi mano e l'input dello sguardo oculare insieme</span><span class="sxs-lookup"><span data-stu-id="84306-234">Example #4: Use hand rays and eye gaze input together</span></span>

<span data-ttu-id="84306-235">I raggi di mano hanno la priorità rispetto alla destinazione e agli sguardi oculari.</span><span class="sxs-lookup"><span data-stu-id="84306-235">Hand rays take priority over head and eye gaze targeting.</span></span> <span data-ttu-id="84306-236">Ciò significa che, se sono abilitati i raggi mano, il momento in cui vengono visualizzate le lancette, il raggio della mano fungerà da puntatore primario.</span><span class="sxs-lookup"><span data-stu-id="84306-236">This means, if hand rays are enabled, the moment the hands come into view, the hand ray will act as the primary pointer.</span></span>
<span data-ttu-id="84306-237">Tuttavia, potrebbero esserci situazioni in cui si desidera utilizzare i raggi mano, pur continuando a rilevare se un utente sta osservando un certo ologramma.</span><span class="sxs-lookup"><span data-stu-id="84306-237">However, there might be situations in which you want to use hand rays while still detecting whether a user is looking at a certain hologram.</span></span> <span data-ttu-id="84306-238">Facile!</span><span class="sxs-lookup"><span data-stu-id="84306-238">Easy!</span></span> <span data-ttu-id="84306-239">Essenzialmente sono necessari due passaggi:</span><span class="sxs-lookup"><span data-stu-id="84306-239">Essentially you require two steps:</span></span>

<span data-ttu-id="84306-240">**1. abilitare il raggio della mano:** per abilitare il raggio della mano, passare a _mixed reality Toolkit-> puntatori di input->_.</span><span class="sxs-lookup"><span data-stu-id="84306-240">**1. Enable the hand ray:** To enable the hand ray, go to _Mixed Reality Toolkit -> Input -> Pointers_.</span></span>
<span data-ttu-id="84306-241">In _EyeTrackingDemo-00-RootScene_ , in cui il Toolkit di realtà misto viene configurato una sola volta per tutte le scene demo di rilevamento degli occhi, viene visualizzato il _EyeTrackingDemoPointerProfile_.</span><span class="sxs-lookup"><span data-stu-id="84306-241">In the _EyeTrackingDemo-00-RootScene_ where the Mixed Reality Toolkit is configured once for all of the eye tracking demo scenes, you should see the _EyeTrackingDemoPointerProfile_.</span></span>
<span data-ttu-id="84306-242">È possibile creare un nuovo _profilo di input_ da zero o adattare il rilevamento degli occhi corrente:</span><span class="sxs-lookup"><span data-stu-id="84306-242">You can either create a new _Input Profile_ from scratch or adapt the current eye tracking one:</span></span>

- <span data-ttu-id="84306-243">**Da zero:** Nella scheda _puntatori_ selezionare _DefaultMixedRealityInputPointerProfile_ dal menu di scelta rapida.</span><span class="sxs-lookup"><span data-stu-id="84306-243">**From scratch:** In the _Pointers_ tab, select the _DefaultMixedRealityInputPointerProfile_ from the context menu.</span></span>
<span data-ttu-id="84306-244">Si tratta del profilo puntatore predefinito per il quale è già abilitato il raggio di mano.</span><span class="sxs-lookup"><span data-stu-id="84306-244">This is the default pointer profile that already has the hand ray enabled!</span></span>
<span data-ttu-id="84306-245">Per modificare il cursore predefinito (un punto bianco opaco), è sufficiente clonare il profilo e creare un profilo puntatore personalizzato.</span><span class="sxs-lookup"><span data-stu-id="84306-245">To change the default cursor (an opaque white dot), simply clone the profile and create your own custom pointer profile.</span></span>
<span data-ttu-id="84306-246">Sostituire quindi _DefaultCursor_ con _EyeGazeCursor_ sotto precostruzione del _cursore dello sguardo_.</span><span class="sxs-lookup"><span data-stu-id="84306-246">Then replace _DefaultCursor_ with _EyeGazeCursor_ under _Gaze Cursor Prefab_.</span></span>  
- <span data-ttu-id="84306-247">**In base alla _EyeTrackingDemoPointerProfile_ esistente:** fare doppio clic su _EyeTrackingDemoPointerProfile_ e aggiungere la voce seguente in _Opzioni puntatore_:</span><span class="sxs-lookup"><span data-stu-id="84306-247">**Based on the existing _EyeTrackingDemoPointerProfile_:** Double-click the _EyeTrackingDemoPointerProfile_ and add the following entry under _Pointer Options_:</span></span>
  - <span data-ttu-id="84306-248">**Tipo di controller:** ' Articolato a mano ',' realtà mista di Windows '</span><span class="sxs-lookup"><span data-stu-id="84306-248">**Controller Type:** 'Articulated Hand', 'Windows Mixed Reality'</span></span>
  - <span data-ttu-id="84306-249">**Manualità:** Qualsiasi</span><span class="sxs-lookup"><span data-stu-id="84306-249">**Handedness:** Any</span></span>
  - <span data-ttu-id="84306-250">**Prefabbricato puntatore:** DefaultControllerPointer</span><span class="sxs-lookup"><span data-stu-id="84306-250">**Pointer Prefab:** DefaultControllerPointer</span></span>

<span data-ttu-id="84306-251">**2. rilevare l'aspetto di un ologramma:** usare lo [`EyeTrackingTarget`](xref:Microsoft.MixedReality.Toolkit.Input.EyeTrackingTarget) script per abilitare il rilevamento di un ologramma come descritto in precedenza.</span><span class="sxs-lookup"><span data-stu-id="84306-251">**2. Detect that a hologram is looked at:** Use the [`EyeTrackingTarget`](xref:Microsoft.MixedReality.Toolkit.Input.EyeTrackingTarget) script to enable detecting that a hologram is looked at as described above.</span></span> <span data-ttu-id="84306-252">È anche possibile esaminare lo `FollowEyeGaze` script di esempio per l'ispirazione perché mostra un ologramma che segue il proprio sguardo (ad esempio, un cursore) se i raggi di mano sono abilitati o meno.</span><span class="sxs-lookup"><span data-stu-id="84306-252">You can also take a look at the `FollowEyeGaze` sample script for inspiration as this is showing a hologram following your eye gaze (e.g., a cursor) whether hand rays are enabled or not.</span></span>

<span data-ttu-id="84306-253">A questo punto, quando si avviano le scene demo per la registrazione degli occhi, dovrebbe venire visualizzato un raggio dalle mani.</span><span class="sxs-lookup"><span data-stu-id="84306-253">Now, when you start the eye tracking demo scenes, you should see a ray coming from your hands.</span></span>
<span data-ttu-id="84306-254">Ad esempio, nella demo di selezione della destinazione di rilevamento degli occhi, il cerchio semitrasparente continua a osservare il proprio sguardo e le gemme rispondono a se sono state esaminate o meno, mentre i pulsanti del menu della scena principale usano invece il puntatore di input primario (le mani).</span><span class="sxs-lookup"><span data-stu-id="84306-254">For example, in the eye tracking target selection demo, the semi-transparent circle is still following your eye gaze and the gems respond to whether they are looked at or not, while the top scene menu buttons use the primary input pointer (your hands) instead.</span></span>

---
[<span data-ttu-id="84306-255">Torna a "Eye Tracking in the MixedRealityToolkit"</span><span class="sxs-lookup"><span data-stu-id="84306-255">Back to "Eye tracking in the MixedRealityToolkit"</span></span>](EyeTracking_Main.md)

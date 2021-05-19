---
title: Selezione del target di tracciamento oculare
description: Come accedere ai dati dello sguardo fisso e agli eventi specifici dello sguardo fisso per selezionare le destinazioni in MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realtà mista, sviluppo, MRTK, EyeTracking,
ms.openlocfilehash: 229903e01c597aefbb3fc29de8a49d79cbbd42d0
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144197"
---
# <a name="eye-supported-target-selection"></a><span data-ttu-id="6b8d5-104">Selezione della destinazione supportata dagli occhi</span><span class="sxs-lookup"><span data-stu-id="6b8d5-104">Eye-supported target selection</span></span>

![MRTK](../../images/eye-tracking/mrtk_et_targetselect.png)

<span data-ttu-id="6b8d5-106">Questa pagina illustra diverse opzioni per l'accesso ai dati dello sguardo fisso e a eventi specifici dello sguardo fisso per selezionare le destinazioni in MRTK.</span><span class="sxs-lookup"><span data-stu-id="6b8d5-106">This page discusses different options for accessing eye gaze data and eye gaze specific events to select targets in MRTK.</span></span> <span data-ttu-id="6b8d5-107">Il tracciamento oculare consente selezioni di destinazione veloci e senza sforzo usando una combinazione di informazioni su ciò che un utente sta esaminando con input aggiuntivi come il rilevamento manuale e i _comandi vocali:_ </span><span class="sxs-lookup"><span data-stu-id="6b8d5-107">Eye tracking allows for fast and effortless target selections using a combination of information about what a user is looking at with additional inputs such as _hand tracking_ and _voice commands_:</span></span>

- <span data-ttu-id="6b8d5-108">Cercare & say _"Select"_ (comando vocale predefinito)</span><span class="sxs-lookup"><span data-stu-id="6b8d5-108">Look & Say _"Select"_ (default voice command)</span></span>
- <span data-ttu-id="6b8d5-109">Cercare & _"Explode"_ o _"Pop"_ (comandi vocali personalizzati)</span><span class="sxs-lookup"><span data-stu-id="6b8d5-109">Look & Say _"Explode"_ or _"Pop"_ (custom voice commands)</span></span>
- <span data-ttu-id="6b8d5-110">Cercare & Bluetooth</span><span class="sxs-lookup"><span data-stu-id="6b8d5-110">Look & Bluetooth button</span></span>
- <span data-ttu-id="6b8d5-111">Cercare & avvicinamento delle dita (ad esempio, tenere la mano davanti a te e avvicinare il pollice e l'indice)</span><span class="sxs-lookup"><span data-stu-id="6b8d5-111">Look & Pinch (i.e., hold up your hand in front of you and bring your thumb and index finger together)</span></span>
  - <span data-ttu-id="6b8d5-112">Si noti che per il funzionamento, i [raggi della mano devono essere disabilitati](eye-tracking-eyes-and-hands.md#how-to-disable-the-hand-ray)</span><span class="sxs-lookup"><span data-stu-id="6b8d5-112">Please note that for this to work, the [hand rays need to be disabled](eye-tracking-eyes-and-hands.md#how-to-disable-the-hand-ray)</span></span>

<span data-ttu-id="6b8d5-113">Per selezionare il contenuto olografico usando lo sguardo fisso, sono disponibili diverse opzioni:</span><span class="sxs-lookup"><span data-stu-id="6b8d5-113">To select holographic content using eye gaze, there are several options:</span></span>

[<span data-ttu-id="6b8d5-114">**1. Usare il puntatore dello stato attivo primario:**</span><span class="sxs-lookup"><span data-stu-id="6b8d5-114">**1. Use the primary focus pointer:**</span></span>](#1-use-generic-focus-and-pointer-handlers)

<span data-ttu-id="6b8d5-115">Questo può essere inteso come cursore con priorità.</span><span class="sxs-lookup"><span data-stu-id="6b8d5-115">This can be understood as your prioritized cursor.</span></span>
<span data-ttu-id="6b8d5-116">Per impostazione predefinita, se le mani sono visualizzate, si tratta di raggi della mano.</span><span class="sxs-lookup"><span data-stu-id="6b8d5-116">By default, if the hands are in view, then this would be hand rays.</span></span>
<span data-ttu-id="6b8d5-117">Se non sono presenti mani, il puntatore con priorità sarà la testa o lo sguardo fisso.</span><span class="sxs-lookup"><span data-stu-id="6b8d5-117">If no hands are in view, then the prioritized pointer would be head or eye gaze.</span></span>
<span data-ttu-id="6b8d5-118">Di conseguenza, si noti che in base alla testa o lo sguardo oculare corrente viene eliminato come input del cursore se vengono usati i raggi della mano.</span><span class="sxs-lookup"><span data-stu-id="6b8d5-118">Thus, please note that based on the current design head or eye gaze is suppressed as a cursor input if hand rays are used.</span></span>

<span data-ttu-id="6b8d5-119">Esempio:</span><span class="sxs-lookup"><span data-stu-id="6b8d5-119">For example:</span></span>

<span data-ttu-id="6b8d5-120">Un utente vuole selezionare un pulsante olografico distante.</span><span class="sxs-lookup"><span data-stu-id="6b8d5-120">A user wants to select a distant holographic button.</span></span>
<span data-ttu-id="6b8d5-121">Gli sviluppatori vogliono fornire una soluzione flessibile che consenta all'utente di eseguire queste attività in diverse condizioni:</span><span class="sxs-lookup"><span data-stu-id="6b8d5-121">As a developer, you want to provide a flexible solution that allows the user to achieve this tasks in various conditions:</span></span>

- <span data-ttu-id="6b8d5-122">Accedere al pulsante e fare clic su di esso</span><span class="sxs-lookup"><span data-stu-id="6b8d5-122">Walk up to the button and poke it</span></span>
- <span data-ttu-id="6b8d5-123">Guardarlo da una distanza e pronunciare "select"</span><span class="sxs-lookup"><span data-stu-id="6b8d5-123">Look at it from a distance and say "select"</span></span>
- <span data-ttu-id="6b8d5-124">Imposta come destinazione il pulsante usando un raggio della mano ed eseguendo un avvicinamento delle dita. In questo caso, la soluzione più flessibile consiste nell'usare il gestore dello stato attivo principale, in quanto invierà una notifica ogni volta che il puntatore dello stato attivo primario attualmente in ordine di priorità attiva un evento.</span><span class="sxs-lookup"><span data-stu-id="6b8d5-124">Target the button using a hand ray and performing a pinch In this case, the most flexible solution is to use the primary focus handler as it will notify you whenever the currently prioritized primary focus pointer triggers an event.</span></span> <span data-ttu-id="6b8d5-125">Si noti che se i raggi della mano sono abilitati, il puntatore di messa a fuoco con la testa o lo sguardo fisso viene disabilitato non appena le mani vengono visualizzate.</span><span class="sxs-lookup"><span data-stu-id="6b8d5-125">Please note that if hand rays are enabled, the head or eye gaze focus pointer are disabled as soon as the hands come into view.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="6b8d5-126">Si noti che se i raggi della mano sono abilitati, il puntatore di messa a fuoco della testa o dello sguardo fisso viene disabilitato non appena le mani vengono visualizzate.</span><span class="sxs-lookup"><span data-stu-id="6b8d5-126">Please note that if hand rays are enabled, the head or eye gaze focus pointer are disabled as soon as the hands come into view.</span></span> <span data-ttu-id="6b8d5-127">Se si vuole supportare [ _un'interazione "look and pinch",_ è necessario disabilitare il raggio della mano.](eye-tracking-eyes-and-hands.md#how-to-disable-the-hand-ray)</span><span class="sxs-lookup"><span data-stu-id="6b8d5-127">If you want to support a [_'look and pinch'_ interaction, you need to disable the hand ray](eye-tracking-eyes-and-hands.md#how-to-disable-the-hand-ray).</span></span> <span data-ttu-id="6b8d5-128">Nelle scene di esempio del tracciamento oculare il raggio della mano è stato disabilitato per consentire interazioni più complesse con occhi e movimenti della mano. Vedere ad esempio Posizionamento supportato dagli [occhi.](eye-tracking-eyes-and-hands.md)</span><span class="sxs-lookup"><span data-stu-id="6b8d5-128">In our eye tracking sample scenes, we have disabled the hand ray to allow for showcasing richer interactions using eyes + hand motions - see for example [Eye-Supported Positioning](eye-tracking-eyes-and-hands.md).</span></span>

[<span data-ttu-id="6b8d5-129">**2. Usare contemporaneamente sia la messa a fuoco oculare che i raggi della mano:**</span><span class="sxs-lookup"><span data-stu-id="6b8d5-129">**2. Use both eye focus and hand rays at the same time:**</span></span>](#2-independent-eye-gaze-specific-eyetrackingtarget)

<span data-ttu-id="6b8d5-130">In alcuni casi può essere necessario essere più specifici del tipo di puntatore allo stato attivo che può attivare determinati eventi e consentire l'uso simultaneo di più tecniche di interazione da lontano.</span><span class="sxs-lookup"><span data-stu-id="6b8d5-130">There might be instances where you want to be more specific which type of focus pointers can trigger certain events and allow for simultaneously using multiple far interaction techniques.</span></span>

<span data-ttu-id="6b8d5-131">Ad esempio: nell'app un utente può usare raggi della mano da lontano per manipolare alcune configurazioni meccaniche olografiche, ad esempio afferrare e tenere premute alcune parti del motore olografiche distanti e posizionarle sul posto.</span><span class="sxs-lookup"><span data-stu-id="6b8d5-131">For example: In your app, a user can use far hand rays to manipulate some holographic mechanical setup - e.g., grab and hold some distant holographic engine parts and hold them in place.</span></span> <span data-ttu-id="6b8d5-132">Durante questa operazione, l'utente deve eseguire una serie di istruzioni e registrare lo stato di avanzamento contrassegnando alcune caselle di controllo.</span><span class="sxs-lookup"><span data-stu-id="6b8d5-132">While doing so, the user has to go through a number of instructions and record her/his progress by marking off some check boxes.</span></span> <span data-ttu-id="6b8d5-133">Se l'utente ha le mani non occupate, sarebbe istintivo toccare semplicemente la casella di controllo o selezionarla usando un raggio della mano.</span><span class="sxs-lookup"><span data-stu-id="6b8d5-133">If the user has her/his hands _not busy_, it would be instinctual to simply touch the check box or select it using a hand ray.</span></span> <span data-ttu-id="6b8d5-134">Tuttavia, se l'utente ha le sue mani occupate, come nel nostro caso, tenendo presenti alcune parti del motore olografico, vuoi consentire all'utente di scorrere facilmente le istruzioni usando lo sguardo fisso e semplicemente guardare una casella di controllo e pronunciare "check it!".</span><span class="sxs-lookup"><span data-stu-id="6b8d5-134">However, if the user has her/his hands busy, as in our case holding some holographic engine parts in place, you want to enable the user to seamlessly scroll through the instructions using their eye gaze and to simply look at a check box and say "check it!".</span></span>

<span data-ttu-id="6b8d5-135">Per abilitare questa funzionalità, è necessario usare lo script EyeTrackingTarget specifico dell'occhio, indipendente dai FocusHandler di MRTK di base e che verrà illustrato più avanti.</span><span class="sxs-lookup"><span data-stu-id="6b8d5-135">To enable this, you need to use eye-specific EyeTrackingTarget script that is independent from the core MRTK FocusHandlers and will be discussed further below.</span></span>

## <a name="1-use-generic-focus-and-pointer-handlers"></a><span data-ttu-id="6b8d5-136">1. Usare gestori generici dello stato attivo e del puntatore</span><span class="sxs-lookup"><span data-stu-id="6b8d5-136">1. Use generic focus and pointer handlers</span></span>

<span data-ttu-id="6b8d5-137">Se il tracciamento oculare è configurato correttamente (vedere Configurazione [MRTK](eye-tracking-basic-setup.md)di base per l'uso del tracciamento oculare), consentire agli utenti di selezionare ologrammi usando gli occhi è lo stesso di qualsiasi altro input di messa a fuoco (ad esempio, sguardo alla testa o raggio della mano). Ciò offre il grande vantaggio di un modo flessibile per interagire con gli ologrammi definendo il tipo di stato attivo principale nel profilo puntatore di input MRTK a seconda delle esigenze dell'utente, lasciando invariato il codice.</span><span class="sxs-lookup"><span data-stu-id="6b8d5-137">If eye tracking is set up correctly (see [Basic MRTK setup to use eye tracking](eye-tracking-basic-setup.md)), enabling users to select holograms using their eyes is the same as for any other focus input (e.g., head gaze or hand ray).This provides the great advantage of a flexible way to interact with your holograms by defining the main focus type in your MRTK Input Pointer Profile depending on your user's needs, while leaving your code untouched.</span></span> <span data-ttu-id="6b8d5-138">Ciò consente di passare da uno sguardo alla testa o dall'altro senza modificare una riga di codice o sostituire i raggi della mano con il targeting oculare per le interazioni lontano.</span><span class="sxs-lookup"><span data-stu-id="6b8d5-138">This allows for switching between head or eye gaze without changing a line of code or replace hand rays with eye targeting for far interactions.</span></span>

### <a name="focusing-on-a-hologram"></a><span data-ttu-id="6b8d5-139">Concentrarsi su un ologramma</span><span class="sxs-lookup"><span data-stu-id="6b8d5-139">Focusing on a hologram</span></span>

<span data-ttu-id="6b8d5-140">Per rilevare quando un ologramma è attivo, usare _l'interfaccia 'IMixedRealityFocusHandler'_ che fornisce due membri di interfaccia: _OnFocusEnter_ e _OnFocusExit_.</span><span class="sxs-lookup"><span data-stu-id="6b8d5-140">To detect when a hologram is focused, use the _'IMixedRealityFocusHandler'_ interface that provides you with two interface members: _OnFocusEnter_ and _OnFocusExit_.</span></span>

<span data-ttu-id="6b8d5-141">Ecco un semplice esempio di [ColorTap.cs](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.ColorTap) per modificare il colore di un ologramma quando viene esaminato.</span><span class="sxs-lookup"><span data-stu-id="6b8d5-141">Here is a simple example from [ColorTap.cs](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.ColorTap) to change a hologram's color when being looked at.</span></span>

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

### <a name="selecting-a-focused-hologram"></a><span data-ttu-id="6b8d5-142">Selezione di un ologramma con stato attivo</span><span class="sxs-lookup"><span data-stu-id="6b8d5-142">Selecting a focused hologram</span></span>

<span data-ttu-id="6b8d5-143">Per selezionare un ologramma con stato attivo, usare _PointerHandler_ per restare in ascolto degli eventi di input per confermare una selezione.</span><span class="sxs-lookup"><span data-stu-id="6b8d5-143">To select a focused hologram, use _PointerHandler_ to listen for input events to confirm a selection.</span></span>
<span data-ttu-id="6b8d5-144">Ad esempio, l'aggiunta _di IMixedRealityPointerHandler_ li farà reagire all'input del puntatore semplice.</span><span class="sxs-lookup"><span data-stu-id="6b8d5-144">For example, adding the _IMixedRealityPointerHandler_ will make them react to simple pointer input.</span></span>
<span data-ttu-id="6b8d5-145">_L'interfaccia IMixedRealityPointerHandler_ richiede l'implementazione dei tre membri di interfaccia _seguenti: OnPointerUp_, _OnPointerDown_ e _OnPointerClicked_.</span><span class="sxs-lookup"><span data-stu-id="6b8d5-145">The _IMixedRealityPointerHandler_ interface requires implementing the following three interface members: _OnPointerUp_, _OnPointerDown_, and _OnPointerClicked_.</span></span>

<span data-ttu-id="6b8d5-146">Nell'esempio seguente viene modificato il colore di un ologramma osservandolo e avvicinando o pronunciando "select".</span><span class="sxs-lookup"><span data-stu-id="6b8d5-146">In the example below, we change the color of a hologram by looking at it and pinching or saying "select".</span></span>
<span data-ttu-id="6b8d5-147">L'azione necessaria per attivare l'evento è definita da in base alla quale è possibile impostare il tipo di nell'editor di Unity. Per impostazione predefinita, si tratta `eventData.MixedRealityInputAction == selectAction` `selectAction` dell'azione "Seleziona".</span><span class="sxs-lookup"><span data-stu-id="6b8d5-147">The required action to trigger the event is defined by `eventData.MixedRealityInputAction == selectAction` whereby we can set the type of `selectAction` in the Unity Editor - by default it's the "Select" action.</span></span> <span data-ttu-id="6b8d5-148">I tipi di [MixedRealityInputActions](../input-actions.md) disponibili possono essere configurati nel profilo MRTK tramite azioni di input del profilo di configurazione _MRTK._  ->    ->  </span><span class="sxs-lookup"><span data-stu-id="6b8d5-148">The types of available [MixedRealityInputActions](../input-actions.md) can be configured in the MRTK Profile via _MRTK Configuration Profile_ -> _Input_ -> _Input Actions_.</span></span>

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

### <a name="eye-gaze-specific-baseeyefocushandler"></a><span data-ttu-id="6b8d5-149">BaseEyeFocusHandler specifico dello sguardo fisso</span><span class="sxs-lookup"><span data-stu-id="6b8d5-149">Eye-gaze-specific BaseEyeFocusHandler</span></span>

<span data-ttu-id="6b8d5-150">Dato che lo sguardo oculare può essere molto diverso da altri input del puntatore,  è possibile assicurarsi di reagire all'input dello stato attivo solo se è lo sguardo fisso e attualmente è il puntatore di input primario.</span><span class="sxs-lookup"><span data-stu-id="6b8d5-150">Given that eye gaze can be very different to other pointer inputs, you may want to make sure to only react to the focus input if it is _eye gaze_ and it is currently the primary input pointer.</span></span>
<span data-ttu-id="6b8d5-151">A questo scopo, si userebbe l'oggetto specifico per il tracciamento [`BaseEyeFocusHandler`](xref:Microsoft.MixedReality.Toolkit.Input.BaseEyeFocusHandler) oculare e che deriva da [`BaseFocusHandler`](xref:Microsoft.MixedReality.Toolkit.Input.BaseFocusHandler) .</span><span class="sxs-lookup"><span data-stu-id="6b8d5-151">For this purpose, you would use the [`BaseEyeFocusHandler`](xref:Microsoft.MixedReality.Toolkit.Input.BaseEyeFocusHandler) which is specific to eye tracking and which derives from the [`BaseFocusHandler`](xref:Microsoft.MixedReality.Toolkit.Input.BaseFocusHandler).</span></span>
<span data-ttu-id="6b8d5-152">Come accennato in precedenza, verrà attivato solo se il targeting dello sguardo fisso è attualmente l'input del puntatore primario (ad esempio, non è attivo alcun raggio della mano).</span><span class="sxs-lookup"><span data-stu-id="6b8d5-152">As mentioned before, it will only trigger if eye gaze targeting is currently the primary pointer input (i.e., no hand ray is active).</span></span> <span data-ttu-id="6b8d5-153">Per altre informazioni, vedere Come supportare lo sguardo [fisso e i movimenti della mano.](eye-tracking-eyes-and-hands.md)</span><span class="sxs-lookup"><span data-stu-id="6b8d5-153">For more information, see [How to support eye gaze + hand gestures](eye-tracking-eyes-and-hands.md).</span></span>

<span data-ttu-id="6b8d5-154">Ecco un esempio da `EyeTrackingDemo-03-Navigation` (Assets/MRTK/Examples/Demos/EyeTracking/Scenes).</span><span class="sxs-lookup"><span data-stu-id="6b8d5-154">Here is an example from `EyeTrackingDemo-03-Navigation` (Assets/MRTK/Examples/Demos/EyeTracking/Scenes).</span></span>
<span data-ttu-id="6b8d5-155">In questa demo sono presenti due ologrammi 3D che si attivano a seconda della parte dell'oggetto da guardare: se l'utente osserva il lato sinistro dell'ologramma, tale parte si sposterà lentamente verso la parte anteriore rivolta verso l'utente.</span><span class="sxs-lookup"><span data-stu-id="6b8d5-155">In this demo, there are two 3D holograms that will turn depending on which part of the object is looked at: If the user looks at the left side of the hologram, then that part will slowly move towards the front facing the user.</span></span>
<span data-ttu-id="6b8d5-156">Se viene esaminato il lato destro, tale parte si sposterà lentamente verso la parte anteriore.</span><span class="sxs-lookup"><span data-stu-id="6b8d5-156">If the right side is looked at, then that part will slowly move to the front.</span></span>
<span data-ttu-id="6b8d5-157">Si tratta di un comportamento che potrebbe non essere attivo in qualsiasi momento e anche qualcosa che potrebbe non essere necessario attivare accidentalmente con un raggio della mano o uno sguardo alla testa.</span><span class="sxs-lookup"><span data-stu-id="6b8d5-157">This is a behavior that you may not want to have active at all times and also something that you may not want to accidentally trigger by a hand ray or head gaze.</span></span>
<span data-ttu-id="6b8d5-158">Dopo [`OnLookAtRotateByEyeGaze`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.OnLookAtRotateByEyeGaze) l'associazione, un GameObject verrà ruotato mentre viene esaminato.</span><span class="sxs-lookup"><span data-stu-id="6b8d5-158">Having the [`OnLookAtRotateByEyeGaze`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.OnLookAtRotateByEyeGaze) attached, a GameObject will rotate while being looked at.</span></span>

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

<span data-ttu-id="6b8d5-159">Consultare la documentazione dell'API per un elenco completo degli eventi disponibili di [`BaseEyeFocusHandler`](xref:Microsoft.MixedReality.Toolkit.Input.BaseEyeFocusHandler) :</span><span class="sxs-lookup"><span data-stu-id="6b8d5-159">Check the API documentation for a complete list of available events of the [`BaseEyeFocusHandler`](xref:Microsoft.MixedReality.Toolkit.Input.BaseEyeFocusHandler):</span></span>

- <span data-ttu-id="6b8d5-160">**OnEyeFocusStart:** Attivato quando il raggio dello sguardo visivo *inizia* a intersecarsi con il collisore di questo obiettivo.</span><span class="sxs-lookup"><span data-stu-id="6b8d5-160">**OnEyeFocusStart:** Triggered once the eye gaze ray *starts* intersecting with this target's collider.</span></span>
- <span data-ttu-id="6b8d5-161">**OnEyeFocusStay:** Attivato mentre *il* raggio dello sguardo oculare si interseca con il collisore di questo obiettivo.</span><span class="sxs-lookup"><span data-stu-id="6b8d5-161">**OnEyeFocusStay:** Triggered *while* the eye gaze ray is intersecting with this target's collider.</span></span>
- <span data-ttu-id="6b8d5-162">**OnEyeFocusStop:** Attivato quando il raggio dello sguardo *fisso smette* di intersecarsi con il collisore di questo obiettivo.</span><span class="sxs-lookup"><span data-stu-id="6b8d5-162">**OnEyeFocusStop:** Triggered once the eye gaze ray *stops* intersecting with this target's collider.</span></span>
- <span data-ttu-id="6b8d5-163">**OnEyeFocusDwell:** Attivato dopo che il raggio dello sguardo oculare si è intersecato con il collisore di questo obiettivo per un periodo di tempo specificato.</span><span class="sxs-lookup"><span data-stu-id="6b8d5-163">**OnEyeFocusDwell:** Triggered once the eye gaze ray has intersected with this target's collider for a specified amount of time.</span></span>

## <a name="2-independent-eye-gaze-specific-eyetrackingtarget"></a><span data-ttu-id="6b8d5-164">2. EyeTrackingTarget indipendente specifico dello sguardo visivo</span><span class="sxs-lookup"><span data-stu-id="6b8d5-164">2. Independent eye-gaze-specific EyeTrackingTarget</span></span>

<span data-ttu-id="6b8d5-165">Infine, è possibile offrire una soluzione che consente di trattare l'input basato sugli occhi completamente indipendente dagli altri puntatori dello stato attivo tramite lo [`EyeTrackingTarget`](xref:Microsoft.MixedReality.Toolkit.Input.EyeTrackingTarget) script.</span><span class="sxs-lookup"><span data-stu-id="6b8d5-165">Finally, we provide you with a solution that let's you treat eye-based input completely independent from other focus pointers via the [`EyeTrackingTarget`](xref:Microsoft.MixedReality.Toolkit.Input.EyeTrackingTarget) script.</span></span>

<span data-ttu-id="6b8d5-166">Ciò offre tre _vantaggi:_</span><span class="sxs-lookup"><span data-stu-id="6b8d5-166">This has three _advantages_:</span></span>

- <span data-ttu-id="6b8d5-167">È possibile assicurarsi che l'ologramma reagisca solo con lo sguardo dell'utente.</span><span class="sxs-lookup"><span data-stu-id="6b8d5-167">You can make sure that the hologram is only reacting to the user's eye gaze.</span></span>
- <span data-ttu-id="6b8d5-168">È indipendente dall'input primario attualmente attivo.</span><span class="sxs-lookup"><span data-stu-id="6b8d5-168">This is independent from the currently active primary input.</span></span> <span data-ttu-id="6b8d5-169">Di conseguenza, è possibile elaborare più input contemporaneamente, ad esempio combinando il targeting oculare veloce con i movimenti della mano.</span><span class="sxs-lookup"><span data-stu-id="6b8d5-169">Hence, you can process multiple inputs at once - for example, combining fast eye targeting with hand gestures.</span></span>
- <span data-ttu-id="6b8d5-170">Diversi eventi di Unity sono già stati impostati per rendere più veloce e pratico gestire e riutilizzare i comportamenti esistenti dall'interno dell'editor di Unity o tramite codice.</span><span class="sxs-lookup"><span data-stu-id="6b8d5-170">Several Unity events have already been set up to make it fast and convenient to handle and reuse existing behaviors from within the Unity Editor or via code.</span></span>

<span data-ttu-id="6b8d5-171">Esistono anche _alcuni svantaggi:_</span><span class="sxs-lookup"><span data-stu-id="6b8d5-171">There are also some _disadvantages:_</span></span>

- <span data-ttu-id="6b8d5-172">Maggiore impegno nella gestione di input separati singolarmente.</span><span class="sxs-lookup"><span data-stu-id="6b8d5-172">More effort to handle separate inputs individually.</span></span>
- <span data-ttu-id="6b8d5-173">Nessuna degradazione elegante: supporta solo il targeting oculare.</span><span class="sxs-lookup"><span data-stu-id="6b8d5-173">No elegant degradation: It only supports eye targeting.</span></span> <span data-ttu-id="6b8d5-174">Se il tracciamento oculare non funziona, è necessario un fallback aggiuntivo.</span><span class="sxs-lookup"><span data-stu-id="6b8d5-174">If eye tracking is not working, you require some additional fallback.</span></span>

<span data-ttu-id="6b8d5-175">Analogamente a _BaseFocusHandler,_ _EyeTrackingTarget_ è pronto con diversi eventi Unity specifici dello sguardo fisso che è possibile ascoltare facilmente tramite l'editor di Unity (vedere l'esempio seguente) o usando _AddListener()_ nel codice:</span><span class="sxs-lookup"><span data-stu-id="6b8d5-175">Similar to the _BaseFocusHandler_, the _EyeTrackingTarget_ comes ready with several eye-gaze-specific Unity events that you can conveniently listen to either via the Unity Editor (see example below) or by using _AddListener()_ in code:</span></span>

- <span data-ttu-id="6b8d5-176">OnLookAtStart()</span><span class="sxs-lookup"><span data-stu-id="6b8d5-176">OnLookAtStart()</span></span>
- <span data-ttu-id="6b8d5-177">WhileLookingAtTarget()</span><span class="sxs-lookup"><span data-stu-id="6b8d5-177">WhileLookingAtTarget()</span></span>
- <span data-ttu-id="6b8d5-178">OnLookAway()</span><span class="sxs-lookup"><span data-stu-id="6b8d5-178">OnLookAway()</span></span>
- <span data-ttu-id="6b8d5-179">OnDwell()</span><span class="sxs-lookup"><span data-stu-id="6b8d5-179">OnDwell()</span></span>
- <span data-ttu-id="6b8d5-180">OnSelected()</span><span class="sxs-lookup"><span data-stu-id="6b8d5-180">OnSelected()</span></span>

<span data-ttu-id="6b8d5-181">Di seguito vengono illustrati alcuni esempi di come usare _EyeTrackingTarget._</span><span class="sxs-lookup"><span data-stu-id="6b8d5-181">In the following, we walk you through a few examples for how to use _EyeTrackingTarget_.</span></span>

### <a name="example-1-eye-supported-smart-notifications"></a><span data-ttu-id="6b8d5-182">Esempio #1: Notifiche intelligenti supportate dagli occhi</span><span class="sxs-lookup"><span data-stu-id="6b8d5-182">Example #1: Eye-supported smart notifications</span></span>

<span data-ttu-id="6b8d5-183">In `EyeTrackingDemo-02-TargetSelection` (Assets/MRTK/Examples/Demos/EyeTracking/Scenes) è possibile trovare un esempio di _notifiche_ intelligenti che reagiscono al sguardo fisso.</span><span class="sxs-lookup"><span data-stu-id="6b8d5-183">In `EyeTrackingDemo-02-TargetSelection` (Assets/MRTK/Examples/Demos/EyeTracking/Scenes), you can find an example for _'smart attentive notifications'_ that react to your eye gaze.</span></span>
<span data-ttu-id="6b8d5-184">Si tratta di caselle di testo 3D che possono essere posizionate nella scena e che vengono ingrandite e ruotate in modo uniforme verso l'utente quando viene esaminato per semplificare la leggibilità.</span><span class="sxs-lookup"><span data-stu-id="6b8d5-184">These are 3D text boxes that can be placed in the scene and that will smoothly enlarge and turn toward the user when being looked at to ease legibility.</span></span> <span data-ttu-id="6b8d5-185">Mentre l'utente legge la notifica, le informazioni continuano a essere visualizzate chiare e chiare.</span><span class="sxs-lookup"><span data-stu-id="6b8d5-185">While the user is reading the notification, the information keeps getting displayed crisp and clear.</span></span> <span data-ttu-id="6b8d5-186">Dopo la lettura e l'allontanarsi dalla notifica, la notifica verrà automaticamente ignorata e si dissolverà. A tale scopo, esistono alcuni script di comportamento generici che non sono specifici del tracciamento oculare, ad esempio:</span><span class="sxs-lookup"><span data-stu-id="6b8d5-186">After reading it and looking away from the notification, the notification will automatically be dismissed and fades out. To achieve all this, there are a few generic behavior scripts that are not specific to eye tracking at all, such as:</span></span>

- [`FaceUser`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.FaceUser)
- [`ChangeSize`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.ChangeSize)
- [`BlendOut`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.BlendOut)

<span data-ttu-id="6b8d5-187">Il vantaggio di questo approccio è che gli stessi script possono essere riutilizzati da vari eventi.</span><span class="sxs-lookup"><span data-stu-id="6b8d5-187">The advantage of this approach is that the same scripts can be reused by various events.</span></span> <span data-ttu-id="6b8d5-188">Ad esempio, un ologramma può iniziare ad affrontare l'utente in base a comandi vocali o dopo aver premuto un pulsante virtuale.</span><span class="sxs-lookup"><span data-stu-id="6b8d5-188">For example, a hologram may start facing the user based on a voice commands or after pressing a virtual button.</span></span> <span data-ttu-id="6b8d5-189">Per attivare questi eventi, è sufficiente fare riferimento ai metodi che devono essere eseguiti nello script associato [`EyeTrackingTarget`](xref:Microsoft.MixedReality.Toolkit.Input.EyeTrackingTarget) a GameObject.</span><span class="sxs-lookup"><span data-stu-id="6b8d5-189">To trigger these events, you can simply reference the methods that should be executed in the [`EyeTrackingTarget`](xref:Microsoft.MixedReality.Toolkit.Input.EyeTrackingTarget) script that is attached to your GameObject.</span></span>

<span data-ttu-id="6b8d5-190">Per l'esempio delle _"notifiche intelligenti e attente",_ si verifica quanto segue:</span><span class="sxs-lookup"><span data-stu-id="6b8d5-190">For the example of the _'smart attentive notifications'_, the following happens:</span></span>

- <span data-ttu-id="6b8d5-191">**OnLookAtStart():** la notifica inizia a...</span><span class="sxs-lookup"><span data-stu-id="6b8d5-191">**OnLookAtStart()**: The notification starts to...</span></span>
  - <span data-ttu-id="6b8d5-192">*FaceUser.Engage:* ... rivolgersi all'utente.</span><span class="sxs-lookup"><span data-stu-id="6b8d5-192">*FaceUser.Engage:* ... turn toward the user.</span></span>
  - <span data-ttu-id="6b8d5-193">*ChangeSize.Engage:* ... aumento delle _dimensioni (fino a una scala massima specificata)_.</span><span class="sxs-lookup"><span data-stu-id="6b8d5-193">*ChangeSize.Engage:* ... increase in size _(up to a specified maximum scale)_.</span></span>
  - <span data-ttu-id="6b8d5-194">*BlendOut.Engage:* ... inizia a integrarsi in più _(dopo essere in uno stato di inattività più sottile)_.</span><span class="sxs-lookup"><span data-stu-id="6b8d5-194">*BlendOut.Engage:* ... starts to blend in more _(after being at a more subtle idle state)_.</span></span>  

- <span data-ttu-id="6b8d5-195">**OnDwell():** informa lo script _BlendOut_ che la notifica è stata osservata sufficientemente.</span><span class="sxs-lookup"><span data-stu-id="6b8d5-195">**OnDwell()**: Informs the _BlendOut_ script that the notification has been looked at sufficiently.</span></span>

- <span data-ttu-id="6b8d5-196">**OnLookAway():** la notifica inizia a...</span><span class="sxs-lookup"><span data-stu-id="6b8d5-196">**OnLookAway()**: The notification starts to...</span></span>
  - <span data-ttu-id="6b8d5-197">*FaceUser.Disengage:* ... tornare all'orientamento originale.</span><span class="sxs-lookup"><span data-stu-id="6b8d5-197">*FaceUser.Disengage:* ... turn back to its original orientation.</span></span>
  - <span data-ttu-id="6b8d5-198">*ChangeSize.Disengage:* ... tornare alle dimensioni originali.</span><span class="sxs-lookup"><span data-stu-id="6b8d5-198">*ChangeSize.Disengage:* ... decrease back to its original size.</span></span>
  - <span data-ttu-id="6b8d5-199">*BlendOut.Disengage:* ... inizia a confondersi: se _OnDwell()_ è stato attivato, si fondono completamente ed eliminano, in caso contrario torna allo stato inattivo.</span><span class="sxs-lookup"><span data-stu-id="6b8d5-199">*BlendOut.Disengage:* ... starts to blend out - If _OnDwell()_ was triggered, blend out completely and destroy, otherwise back to its idle state.</span></span>

<span data-ttu-id="6b8d5-200">**Considerazioni sulla progettazione:** La chiave per un'esperienza piacevole è ottimizzare con attenzione la velocità di uno di questi comportamenti per evitare di causare disagio reagendo troppo rapidamente all'occhio dell'utente.</span><span class="sxs-lookup"><span data-stu-id="6b8d5-200">**Design consideration:** The key to an enjoyable experience here is to carefully tune the speed of any of these behaviors to avoid causing discomfort by reacting to the user’s eye gaze too quickly all the time.</span></span>
<span data-ttu-id="6b8d5-201">In caso contrario, può essere estremamente difficile.</span><span class="sxs-lookup"><span data-stu-id="6b8d5-201">Otherwise this can quickly feel extremely overwhelming.</span></span>

<img src="../../images/eye-tracking/mrtk_et_EyeTrackingTarget_Notification.jpg" width="750" alt="Target Notification">

### <a name="example-2-holographic-gem-rotates-slowly-when-looking-at-it"></a><span data-ttu-id="6b8d5-202">Esempio #2: gemma olografica ruota lentamente quando la si guarda</span><span class="sxs-lookup"><span data-stu-id="6b8d5-202">Example #2: Holographic gem rotates slowly when looking at it</span></span>

<span data-ttu-id="6b8d5-203">Analogamente a Example #1, è possibile creare facilmente un feedback al passaggio del mouse per le gemme olografiche nella scena (Assets/MRTK/Examples/Demos/EyeTracking/Scenes) che ruota lentamente in una direzione costante e a una velocità costante (a differenza dell'esempio di rotazione dall'alto) quando viene `EyeTrackingDemo-02-TargetSelection` esaminato.</span><span class="sxs-lookup"><span data-stu-id="6b8d5-203">Similar to Example #1, we can easily create a hover feedback for our holographic gems in `EyeTrackingDemo-02-TargetSelection` (Assets/MRTK/Examples/Demos/EyeTracking/Scenes) scene that will slowly rotate in a constant direction and at a constant speed (in contrast to the rotation example from above) when being looked at.</span></span> <span data-ttu-id="6b8d5-204">È necessario attivare la rotazione della gemma olografica dall'evento _WhileLookingAtTarget()_ di _EyeTrackingTarget._</span><span class="sxs-lookup"><span data-stu-id="6b8d5-204">All you need is to trigger the rotation of the holographic gem from the _EyeTrackingTarget_'s _WhileLookingAtTarget()_ event.</span></span> <span data-ttu-id="6b8d5-205">Ecco alcuni altri dettagli:</span><span class="sxs-lookup"><span data-stu-id="6b8d5-205">Here are a few more details:</span></span>

1. <span data-ttu-id="6b8d5-206">Creare uno script generico che includa una funzione pubblica per ruotare l'oggetto GameObject a cui è collegata.</span><span class="sxs-lookup"><span data-stu-id="6b8d5-206">Create a generic script that includes a public function to rotate the GameObject it is attached to.</span></span> <span data-ttu-id="6b8d5-207">Di seguito è riportato un esempio _di RotateWithConstSpeedDir.cs_ in cui è possibile modificare la direzione di rotazione e la velocità dall'editor di Unity.</span><span class="sxs-lookup"><span data-stu-id="6b8d5-207">Below is an example from _RotateWithConstSpeedDir.cs_ where we can tweak the rotation direction and speed from the Unity Editor.</span></span>

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

1. <span data-ttu-id="6b8d5-208">Aggiungere lo script al GameObject di destinazione [`EyeTrackingTarget`](xref:Microsoft.MixedReality.Toolkit.Input.EyeTrackingTarget) e fare riferimento alla funzione _RotateTarget()_ nel trigger UnityEvent, come illustrato nello screenshot seguente:</span><span class="sxs-lookup"><span data-stu-id="6b8d5-208">Add the [`EyeTrackingTarget`](xref:Microsoft.MixedReality.Toolkit.Input.EyeTrackingTarget) script to your target GameObject and reference the _RotateTarget()_ function in the UnityEvent trigger as shown the screenshot below:</span></span>

    ![Esempio di EyeTrackingTarget](../../images/eye-tracking/mrtk_et_EyeTrackingTargetSample.jpg)

### <a name="example-3-pop-those-gems-aka-_multi-modal-eye-gaze-supported-target-selection_"></a><span data-ttu-id="6b8d5-210">Esempio #3: Selezionare le gemme come selezione di destinazione _multimodale supportata_ da sguardo fisso</span><span class="sxs-lookup"><span data-stu-id="6b8d5-210">Example #3: Pop those gems aka _multi-modal eye-gaze-supported target selection_</span></span>

<span data-ttu-id="6b8d5-211">Nell'esempio precedente è stato illustrato quanto sia facile rilevare se una destinazione viene osservata e come attivare una reazione a tale obiettivo.</span><span class="sxs-lookup"><span data-stu-id="6b8d5-211">In the previous example, we have shown how easy it is to detect whether a target is looked at and how to trigger a reaction to that.</span></span> <span data-ttu-id="6b8d5-212">Ora le gemme esplodono usando _l'evento OnSelected()_ di [`EyeTrackingTarget`](xref:Microsoft.MixedReality.Toolkit.Input.EyeTrackingTarget) .</span><span class="sxs-lookup"><span data-stu-id="6b8d5-212">Next, let's make the gems explode using the _OnSelected()_ event from the [`EyeTrackingTarget`](xref:Microsoft.MixedReality.Toolkit.Input.EyeTrackingTarget).</span></span> <span data-ttu-id="6b8d5-213">La parte interessante è *il modo* in cui viene attivata la selezione.</span><span class="sxs-lookup"><span data-stu-id="6b8d5-213">The interesting part is *how* the selection is triggered.</span></span> <span data-ttu-id="6b8d5-214">consente [`EyeTrackingTarget`](xref:Microsoft.MixedReality.Toolkit.Input.EyeTrackingTarget) di assegnare rapidamente diversi modi per richiamare una selezione:</span><span class="sxs-lookup"><span data-stu-id="6b8d5-214">The [`EyeTrackingTarget`](xref:Microsoft.MixedReality.Toolkit.Input.EyeTrackingTarget) allows for quickly assigning different ways to invoke a selection:</span></span>

- <span data-ttu-id="6b8d5-215">_Movimento di avvicinamento_ delle dita: l'impostazione di "Seleziona azione" su "Seleziona" usa il movimento della mano predefinito per attivare la selezione.</span><span class="sxs-lookup"><span data-stu-id="6b8d5-215">_Pinch gesture_: Setting the 'Select Action' to 'Select' uses the default hand gesture to trigger the selection.</span></span>
<span data-ttu-id="6b8d5-216">Ciò significa che l'utente può semplicemente alzare la mano e avvicinare il pollice e il dito indice per confermare la selezione.</span><span class="sxs-lookup"><span data-stu-id="6b8d5-216">This means that the user can simply raise their hand and pinch their thumb and index finger together to confirm the selection.</span></span>

- <span data-ttu-id="6b8d5-217">Pronunciare _"Seleziona":_ usare il comando vocale _predefinito "Seleziona"_ per selezionare un ologramma.</span><span class="sxs-lookup"><span data-stu-id="6b8d5-217">Say _"Select"_: Use the default voice command _"Select"_ for selecting a hologram.</span></span>

- <span data-ttu-id="6b8d5-218">Pronunciare _"Explode"_ _o "Pop":_ per usare comandi vocali personalizzati, è necessario seguire due passaggi:</span><span class="sxs-lookup"><span data-stu-id="6b8d5-218">Say _"Explode"_ or _"Pop"_: To use custom voice commands, you need to follow two steps:</span></span>
    1. <span data-ttu-id="6b8d5-219">Configurare un'azione personalizzata, ad esempio _"DestroyTarget"_</span><span class="sxs-lookup"><span data-stu-id="6b8d5-219">Set up a custom action such as _"DestroyTarget"_</span></span>
        - <span data-ttu-id="6b8d5-220">Passare a _MRTK -> Input -> Input Actions_</span><span class="sxs-lookup"><span data-stu-id="6b8d5-220">Navigate to _MRTK -> Input -> Input Actions_</span></span>
        - <span data-ttu-id="6b8d5-221">Fare clic su "Aggiungi una nuova azione"</span><span class="sxs-lookup"><span data-stu-id="6b8d5-221">Click "Add a new action"</span></span>

    2. <span data-ttu-id="6b8d5-222">Configurare i comandi vocali che attivano questa azione, ad esempio _"Explode"_ o _"Pop"_</span><span class="sxs-lookup"><span data-stu-id="6b8d5-222">Set up the voice commands that trigger this action such as _"Explode"_ or _"Pop"_</span></span>
        - <span data-ttu-id="6b8d5-223">Passare a _MRTK -> Input -> Voce_</span><span class="sxs-lookup"><span data-stu-id="6b8d5-223">Navigate to _MRTK -> Input -> Speech_</span></span>
        - <span data-ttu-id="6b8d5-224">Fare clic su "Aggiungi un nuovo comando vocale"</span><span class="sxs-lookup"><span data-stu-id="6b8d5-224">Click "Add a new speech command"</span></span>
            - <span data-ttu-id="6b8d5-225">Associare l'azione appena creata</span><span class="sxs-lookup"><span data-stu-id="6b8d5-225">Associate the action you just created</span></span>
            - <span data-ttu-id="6b8d5-226">Assegnare _un keycode_ per consentire l'attivazione dell'azione tramite la pressione di un pulsante</span><span class="sxs-lookup"><span data-stu-id="6b8d5-226">Assign a _KeyCode_ to allow for triggering the action via a button press</span></span>

![Esempio di EyeTrackingTarget per i comandi vocali](../../images/eye-tracking/mrtk_et_voicecmdsample.jpg)

<span data-ttu-id="6b8d5-228">Quando viene selezionata una gemma, esplode, facendo un suono e scomparendo.</span><span class="sxs-lookup"><span data-stu-id="6b8d5-228">When a gem is selected it will explode, making a sound and disappear.</span></span> <span data-ttu-id="6b8d5-229">Questa operazione viene gestita dallo [`HitBehaviorDestroyOnSelect`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.HitBehaviorDestroyOnSelect) script.</span><span class="sxs-lookup"><span data-stu-id="6b8d5-229">This is handled by the [`HitBehaviorDestroyOnSelect`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.HitBehaviorDestroyOnSelect) script.</span></span> <span data-ttu-id="6b8d5-230">Sono disponibili due opzioni:</span><span class="sxs-lookup"><span data-stu-id="6b8d5-230">You have two options:</span></span>

- <span data-ttu-id="6b8d5-231">**Nell'editor di Unity:** È possibile collegare semplicemente lo script collegato a ognuno dei modelli di gemme all'evento Unity OnSelected() nell'editor di Unity.</span><span class="sxs-lookup"><span data-stu-id="6b8d5-231">**In the Unity Editor:** You could simply link the script that is attached to each of our gem templates to the OnSelected() Unity event in the Unity Editor.</span></span>
- <span data-ttu-id="6b8d5-232">**Nel codice:** Se non si vuole trascinare e rilasciare GameObject, è anche possibile aggiungere semplicemente un listener di eventi direttamente allo script.</span><span class="sxs-lookup"><span data-stu-id="6b8d5-232">**In code:** If you don't want to drag and drop GameObjects around, you can also simply add a event listener directly to your script.</span></span>  
<span data-ttu-id="6b8d5-233">Di seguito è riportato un esempio di come è stato eseguito nello [`HitBehaviorDestroyOnSelect`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.HitBehaviorDestroyOnSelect) script:</span><span class="sxs-lookup"><span data-stu-id="6b8d5-233">Here's an example from how we did it in the [`HitBehaviorDestroyOnSelect`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.HitBehaviorDestroyOnSelect) script:</span></span>

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

### <a name="example-4-use-hand-rays-and-eye-gaze-input-together"></a><span data-ttu-id="6b8d5-234">Esempio #4: Usare i raggi della mano e l'input dello sguardo fisso insieme</span><span class="sxs-lookup"><span data-stu-id="6b8d5-234">Example #4: Use hand rays and eye gaze input together</span></span>

<span data-ttu-id="6b8d5-235">I raggi della mano hanno la priorità rispetto alla destinazione della testa e dello sguardo fisso.</span><span class="sxs-lookup"><span data-stu-id="6b8d5-235">Hand rays take priority over head and eye gaze targeting.</span></span> <span data-ttu-id="6b8d5-236">Ciò significa che, se i raggi della mano sono abilitati, nel momento in cui le mani vengono visualizzate, il raggio della mano fungerà da indicatore di misura principale.</span><span class="sxs-lookup"><span data-stu-id="6b8d5-236">This means, if hand rays are enabled, the moment the hands come into view, the hand ray will act as the primary pointer.</span></span>
<span data-ttu-id="6b8d5-237">Tuttavia, in alcune situazioni potrebbe essere necessario usare i raggi della mano pur continuando a rilevare se un utente sta esaminando un determinato ologramma.</span><span class="sxs-lookup"><span data-stu-id="6b8d5-237">However, there might be situations in which you want to use hand rays while still detecting whether a user is looking at a certain hologram.</span></span> <span data-ttu-id="6b8d5-238">Facile!</span><span class="sxs-lookup"><span data-stu-id="6b8d5-238">Easy!</span></span> <span data-ttu-id="6b8d5-239">In sostanza sono necessari due passaggi:</span><span class="sxs-lookup"><span data-stu-id="6b8d5-239">Essentially you require two steps:</span></span>

<span data-ttu-id="6b8d5-240">**1. Abilitare il raggio** della mano: per abilitare il raggio della mano, passare a Mixed Reality Toolkit _-> Input -> Pointers (Puntatori di input -> realtà mista)._</span><span class="sxs-lookup"><span data-stu-id="6b8d5-240">**1. Enable the hand ray:** To enable the hand ray, go to _Mixed Reality Toolkit -> Input -> Pointers_.</span></span>
<span data-ttu-id="6b8d5-241">In _EyeTrackingDemo-00-RootScene,_ in cui Mixed Reality Toolkit è configurato una sola volta per tutte le scene demo di tracciamento oculare, dovrebbe essere visualizzato _EyeTrackingDemoPointerProfile._</span><span class="sxs-lookup"><span data-stu-id="6b8d5-241">In the _EyeTrackingDemo-00-RootScene_ where the Mixed Reality Toolkit is configured once for all of the eye tracking demo scenes, you should see the _EyeTrackingDemoPointerProfile_.</span></span>
<span data-ttu-id="6b8d5-242">È possibile creare un nuovo profilo _di input_ da zero o adattare il tracciamento oculare corrente:</span><span class="sxs-lookup"><span data-stu-id="6b8d5-242">You can either create a new _Input Profile_ from scratch or adapt the current eye tracking one:</span></span>

- <span data-ttu-id="6b8d5-243">**Da zero:** Nella scheda _Puntatori_ selezionare _DefaultMixedRealityInputPointerProfile_ dal menu di scelta rapida.</span><span class="sxs-lookup"><span data-stu-id="6b8d5-243">**From scratch:** In the _Pointers_ tab, select the _DefaultMixedRealityInputPointerProfile_ from the context menu.</span></span>
<span data-ttu-id="6b8d5-244">Questo è il profilo puntatore predefinito in cui è già abilitato il raggio della mano.</span><span class="sxs-lookup"><span data-stu-id="6b8d5-244">This is the default pointer profile that already has the hand ray enabled!</span></span>
<span data-ttu-id="6b8d5-245">Per modificare il cursore predefinito (un punto bianco opaco), è sufficiente clonare il profilo e creare un profilo puntatore personalizzato.</span><span class="sxs-lookup"><span data-stu-id="6b8d5-245">To change the default cursor (an opaque white dot), simply clone the profile and create your own custom pointer profile.</span></span>
<span data-ttu-id="6b8d5-246">Sostituire quindi _DefaultCursor con_ _EyeGazeCursor_ in _Gaze Cursor Prefab (Prefab cursore sguardo fisso)._</span><span class="sxs-lookup"><span data-stu-id="6b8d5-246">Then replace _DefaultCursor_ with _EyeGazeCursor_ under _Gaze Cursor Prefab_.</span></span>  
- <span data-ttu-id="6b8d5-247">**In base all'elemento _EyeTrackingDemoPointerProfile_ esistente:** fare doppio clic su _EyeTrackingDemoPointerProfile_ e aggiungere la voce seguente in _Pointer Options (Opzioni puntatore):_</span><span class="sxs-lookup"><span data-stu-id="6b8d5-247">**Based on the existing _EyeTrackingDemoPointerProfile_:** Double-click the _EyeTrackingDemoPointerProfile_ and add the following entry under _Pointer Options_:</span></span>
  - <span data-ttu-id="6b8d5-248">**Tipo di controller:** 'Articulated Hand', 'Windows Mixed Reality'</span><span class="sxs-lookup"><span data-stu-id="6b8d5-248">**Controller Type:** 'Articulated Hand', 'Windows Mixed Reality'</span></span>
  - <span data-ttu-id="6b8d5-249">**Mania:** Qualsiasi</span><span class="sxs-lookup"><span data-stu-id="6b8d5-249">**Handedness:** Any</span></span>
  - <span data-ttu-id="6b8d5-250">**Prefab puntatore:** DefaultControllerPointer</span><span class="sxs-lookup"><span data-stu-id="6b8d5-250">**Pointer Prefab:** DefaultControllerPointer</span></span>

<span data-ttu-id="6b8d5-251">**2. Rilevare che un ologramma** viene esaminato: usare lo script per abilitare il rilevamento che un ologramma viene esaminato [`EyeTrackingTarget`](xref:Microsoft.MixedReality.Toolkit.Input.EyeTrackingTarget) come descritto in precedenza.</span><span class="sxs-lookup"><span data-stu-id="6b8d5-251">**2. Detect that a hologram is looked at:** Use the [`EyeTrackingTarget`](xref:Microsoft.MixedReality.Toolkit.Input.EyeTrackingTarget) script to enable detecting that a hologram is looked at as described above.</span></span> <span data-ttu-id="6b8d5-252">È anche possibile esaminare lo script di esempio per trovare ispirazione, in quanto mostra un ologramma che segue lo sguardo (ad esempio, un cursore) indipendentemente dal fatto che i raggi della mano siano abilitati o `FollowEyeGaze` meno.</span><span class="sxs-lookup"><span data-stu-id="6b8d5-252">You can also take a look at the `FollowEyeGaze` sample script for inspiration as this is showing a hologram following your eye gaze (e.g., a cursor) whether hand rays are enabled or not.</span></span>

<span data-ttu-id="6b8d5-253">Ora, quando si avviano le scene della demo di tracciamento oculare, si dovrebbe vedere un raggio proveniente dalle mani.</span><span class="sxs-lookup"><span data-stu-id="6b8d5-253">Now, when you start the eye tracking demo scenes, you should see a ray coming from your hands.</span></span>
<span data-ttu-id="6b8d5-254">Ad esempio, nella demo di selezione della destinazione del tracciamento oculare, il cerchio semitrasparente sta ancora seguendo lo sguardo e le gemme rispondono se vengono osservate o meno, mentre i pulsanti del menu della scena superiore usano invece il puntatore di input primario (le mani).</span><span class="sxs-lookup"><span data-stu-id="6b8d5-254">For example, in the eye tracking target selection demo, the semi-transparent circle is still following your eye gaze and the gems respond to whether they are looked at or not, while the top scene menu buttons use the primary input pointer (your hands) instead.</span></span>

---
[<span data-ttu-id="6b8d5-255">Tornare a "Tracciamento oculare in MixedRealityToolkit"</span><span class="sxs-lookup"><span data-stu-id="6b8d5-255">Back to "Eye tracking in the MixedRealityToolkit"</span></span>](eye-tracking-main.md)

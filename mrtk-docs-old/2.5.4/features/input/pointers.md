---
title: Pointers
description: Documentazione sui puntatori in MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, puntatori,
ms.openlocfilehash: 96d7e1c14361fdce94efcdef07b02a51f06ce599
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2021
ms.locfileid: "104685264"
---
# <a name="pointers"></a><span data-ttu-id="c26d5-104">Pointers</span><span class="sxs-lookup"><span data-stu-id="c26d5-104">Pointers</span></span>

![Puntatore](../images/pointers/MRTK_Pointer_Main.png)

<span data-ttu-id="c26d5-106">Questo articolo illustra come configurare e rispondere all'input del puntatore in pratica rispetto all' [architettura del puntatore](../../architecture/controllers-pointers-and-focus.md)</span><span class="sxs-lookup"><span data-stu-id="c26d5-106">This article explains how to configure and respond to Pointer input in practice, compared to [Pointer Architecture](../../architecture/controllers-pointers-and-focus.md)</span></span>

<span data-ttu-id="c26d5-107">I puntatori vengono automaticamente istanze in fase di esecuzione quando viene rilevato un nuovo controller.</span><span class="sxs-lookup"><span data-stu-id="c26d5-107">Pointers are instanced automatically at runtime when a new controller is detected.</span></span> <span data-ttu-id="c26d5-108">È possibile collegare più di un puntatore a un controller.</span><span class="sxs-lookup"><span data-stu-id="c26d5-108">More than one pointer can be attached to a controller.</span></span> <span data-ttu-id="c26d5-109">Con il profilo puntatore predefinito, ad esempio, i controller di realtà mista di Windows ottengono rispettivamente una linea e un puntatore parabolico per la selezione e la teleportazione normali.</span><span class="sxs-lookup"><span data-stu-id="c26d5-109">For example, with the default pointer profile, Windows Mixed Reality controllers get both a line and a parabolic pointer for normal selection and teleportation respectively.</span></span>

## <a name="pointer-configuration"></a><span data-ttu-id="c26d5-110">Configurazione puntatore</span><span class="sxs-lookup"><span data-stu-id="c26d5-110">Pointer configuration</span></span>

<span data-ttu-id="c26d5-111">I puntatori sono configurati come parte del sistema di input in MRTK tramite un [`MixedRealityPointerProfile`](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityPointerProfile) .</span><span class="sxs-lookup"><span data-stu-id="c26d5-111">Pointers are configured as part of the Input System in MRTK via a [`MixedRealityPointerProfile`](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityPointerProfile).</span></span> <span data-ttu-id="c26d5-112">Questo tipo di profilo viene assegnato a un oggetto [`MixedRealityInputSystemProfile`](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityInputSystemProfile) in controllo configurazione MRTK.</span><span class="sxs-lookup"><span data-stu-id="c26d5-112">This type of profile is assigned to a [`MixedRealityInputSystemProfile`](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityInputSystemProfile) in the MRTK Configuration inspector.</span></span> <span data-ttu-id="c26d5-113">Il profilo del puntatore determina il cursore, i tipi di puntatori disponibili in fase di esecuzione e il modo in cui tali puntatori comunicano tra loro per decidere quale sia attivo.</span><span class="sxs-lookup"><span data-stu-id="c26d5-113">The Pointer profile determines the cursor, types of Pointers available at runtime, and how those pointers communicate with each other to decide which one is active.</span></span>

- <span data-ttu-id="c26d5-114">*Extent di puntamento* : definisce la distanza massima per cui un puntatore può interagire con un GameObject.</span><span class="sxs-lookup"><span data-stu-id="c26d5-114">*Pointing Extent* - Defines the max distance for which a Pointer can interact with a GameObject.</span></span>

- <span data-ttu-id="c26d5-115">*Pointing Raycast layer masks* : si tratta di una matrice con priorità di LayerMasks per determinare quali possibili GameObject qualsiasi puntatore specificato possono interagire con e l'ordine di interazione da tentare.</span><span class="sxs-lookup"><span data-stu-id="c26d5-115">*Pointing Raycast Layer Masks* - This is a prioritized array of LayerMasks to determine which possible GameObjects any given Pointer can interact with and the order of interaction to attempt.</span></span> <span data-ttu-id="c26d5-116">Questo può essere utile per garantire che i puntatori interagiscano con gli elementi dell'interfaccia utente prima di altri oggetti della scena.</span><span class="sxs-lookup"><span data-stu-id="c26d5-116">This may be useful to ensure Pointers interact with UI elements first before other scene objects.</span></span>
<span data-ttu-id="c26d5-117">![Esempio di profilo puntatore](../images/input/pointers/PointerProfile.PNG)</span><span class="sxs-lookup"><span data-stu-id="c26d5-117">![Pointer Profile Example](../images/input/pointers/PointerProfile.PNG)</span></span>

### <a name="pointer-options-configuration"></a><span data-ttu-id="c26d5-118">Configurazione delle opzioni del puntatore</span><span class="sxs-lookup"><span data-stu-id="c26d5-118">Pointer options configuration</span></span>

<span data-ttu-id="c26d5-119">La configurazione predefinita del profilo puntatore MRTK include le classi di puntatore seguenti e i prefabbricati associati.</span><span class="sxs-lookup"><span data-stu-id="c26d5-119">The default MRTK Pointer Profile configuration includes the following pointer classes and associated prefabs out-of-box.</span></span> <span data-ttu-id="c26d5-120">L'elenco di puntatori disponibili per il sistema in fase di esecuzione è definito in *Opzioni puntatore* nel profilo puntatore.</span><span class="sxs-lookup"><span data-stu-id="c26d5-120">The list of pointers available to the system at runtime is defined under *Pointer Options* in the Pointer profile.</span></span> <span data-ttu-id="c26d5-121">Gli sviluppatori possono utilizzare questo elenco per riconfigurare i puntatori esistenti, aggiungere nuovi puntatori o eliminarne uno.</span><span class="sxs-lookup"><span data-stu-id="c26d5-121">Developers can utilize this list to reconfigure existing Pointers, add new Pointers, or delete one.</span></span>

![Esempio di profilo Opzioni puntatore](../images/input/pointers/PointerOptionsProfile.PNG)

<span data-ttu-id="c26d5-123">Ogni voce del puntatore viene definita dal set di dati seguente:</span><span class="sxs-lookup"><span data-stu-id="c26d5-123">Each Pointer entry is defined by the following set of data:</span></span>

- <span data-ttu-id="c26d5-124">*Tipo di controller* : il set di controller per cui è valido un puntatore.</span><span class="sxs-lookup"><span data-stu-id="c26d5-124">*Controller Type* - The set of controllers that a pointer is valid for.</span></span>
  - <span data-ttu-id="c26d5-125">Ad esempio, *PokePointer* è responsabile per gli oggetti "frugare" con un dito e è, per impostazione predefinita, contrassegnato come supporto solo per il tipo di controller a mano articolata.</span><span class="sxs-lookup"><span data-stu-id="c26d5-125">For example, the *PokePointer* is responsible for "poking" objects with a finger, and is, by default marked as only supporting the articulated hand controller type.</span></span> <span data-ttu-id="c26d5-126">Viene creata un'istanza dei puntatori solo quando un controller diventa disponibile e in particolare il *tipo di controller* definisce quali controller possono essere creati da questo puntatore.</span><span class="sxs-lookup"><span data-stu-id="c26d5-126">Pointers are only instantiated when a controller becomes available and in particular the *Controller Type* defines what controllers this pointer prefab can be created with.</span></span>

- <span data-ttu-id="c26d5-127">*Manualità* : consente di creare un'istanza di un puntatore solo per una mano specifica (a sinistra o a destra)</span><span class="sxs-lookup"><span data-stu-id="c26d5-127">*Handedness* - allows for a pointer to only being instantiated for a specific hand (left/right)</span></span>

> [!NOTE]
> <span data-ttu-id="c26d5-128">Se si imposta la proprietà della *manualità* di una voce del puntatore su *None* , questa verrà disabilitata dal sistema come alternativa alla rimozione del puntatore dall'elenco.</span><span class="sxs-lookup"><span data-stu-id="c26d5-128">Setting the *Handedness* property of a Pointer entry to *None* will effectively disable it from the system as an alternative to removing that Pointer from the list.</span></span>

- <span data-ttu-id="c26d5-129">*Prefabbricato del puntatore* : verrà creata un'istanza dell'asset prefabbricato quando un controller che corrisponde al tipo di controller e alla manualità specificati inizierà a essere rilevato.</span><span class="sxs-lookup"><span data-stu-id="c26d5-129">*Pointer Prefab* - This prefab asset will be instantiated when a controller matching the specified controller type and handedness starts being tracked.</span></span>

<span data-ttu-id="c26d5-130">È possibile avere più puntatori associati a un controller.</span><span class="sxs-lookup"><span data-stu-id="c26d5-130">It is possible to have multiple pointers associated with a controller.</span></span> <span data-ttu-id="c26d5-131">Ad esempio, in `DefaultHoloLens2InputSystemProfile` (assets/MRTK/SDK/Profiles/HoloLens2/) il controller a mano articolata è associato a *PokePointer*, *GrabPointer* e *DefaultControllerPointer* (ovvero</span><span class="sxs-lookup"><span data-stu-id="c26d5-131">For example, in `DefaultHoloLens2InputSystemProfile` (Assets/MRTK/SDK/Profiles/HoloLens2/) the articulated hand controller is associated with the *PokePointer*, *GrabPointer*, and the *DefaultControllerPointer* (i.e</span></span> <span data-ttu-id="c26d5-132">raggi mano).</span><span class="sxs-lookup"><span data-stu-id="c26d5-132">hand rays).</span></span>

> [!NOTE]
> <span data-ttu-id="c26d5-133">MRTK fornisce un set di prefabbricati puntatore in *assets/MRTK/SDK/features/UX/premises/puntatori*.</span><span class="sxs-lookup"><span data-stu-id="c26d5-133">MRTK provides a set of pointer prefabs in *Assets/MRTK/SDK/Features/UX/Prefabs/Pointers*.</span></span> <span data-ttu-id="c26d5-134">Una nuova precostruzione personalizzata può essere compilata purché contenga uno degli script di puntatore in *assets/MRTK/SDK/features/UX/scripts/puntatori* o qualsiasi altro script che implementa [`IMixedRealityPointer`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityPointer) .</span><span class="sxs-lookup"><span data-stu-id="c26d5-134">A new custom prefab can be built as long as it contains one of the pointer scripts in *Assets/MRTK/SDK/Features/UX/Scripts/Pointers* or any other script implementing [`IMixedRealityPointer`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityPointer).</span></span>

### <a name="default-pointer-classes"></a><span data-ttu-id="c26d5-135">Classi puntatore predefinite</span><span class="sxs-lookup"><span data-stu-id="c26d5-135">Default pointer classes</span></span>

<span data-ttu-id="c26d5-136">Le classi seguenti sono i puntatori MRTK predefiniti disponibili e definiti nel *profilo puntatore MRTK* predefinito descritto in precedenza.</span><span class="sxs-lookup"><span data-stu-id="c26d5-136">The following classes are the out-of-box MRTK pointers available and defined in the default *MRTK Pointer Profile* outlined above.</span></span> <span data-ttu-id="c26d5-137">Ogni prefabbricato del puntatore fornito in *assets/MRTK/SDK/features/UX/Prefabbricates/puntatori* contiene uno dei componenti del puntatore collegati.</span><span class="sxs-lookup"><span data-stu-id="c26d5-137">Each pointer prefab provided under *Assets/MRTK/SDK/Features/UX/Prefabs/Pointers* contains one of the pointer components attached.</span></span>

![Puntatori predefiniti MRTK](../images/input/pointers/MRTK_Pointers.png)

#### <a name="far-pointers"></a><span data-ttu-id="c26d5-139">Puntatori a distanza</span><span class="sxs-lookup"><span data-stu-id="c26d5-139">Far pointers</span></span>

##### [`LinePointer`](xref:Microsoft.MixedReality.Toolkit.Input.LinePointer)

 <span data-ttu-id="c26d5-140">*LinePointer*, una classe puntatore di base, disegna una linea dall'origine dell'input (ovvero il controller) nella direzione del puntatore e supporta un solo cast a raggio in questa direzione.</span><span class="sxs-lookup"><span data-stu-id="c26d5-140">*LinePointer*, a base pointer class, draws a line from the source of the input (i.e. the controller) in the pointer direction and supports a single ray cast in this direction.</span></span> <span data-ttu-id="c26d5-141">In genere, [`ShellHandRayPointer`](xref:Microsoft.MixedReality.Toolkit.Input.ShellHandRayPointer) viene creata un'istanza delle classi figlio come e i puntatori di Teleport, che consentono di indicare la posizione in cui si trova la teleporta, anziché questa classe, che fornisce principalmente funzionalità comuni.</span><span class="sxs-lookup"><span data-stu-id="c26d5-141">Generally, children classes such as the [`ShellHandRayPointer`](xref:Microsoft.MixedReality.Toolkit.Input.ShellHandRayPointer) and the teleport pointers are instantiated and utilized (which also draw lines to indicate where teleportation will end up at) instead of this class which primarily provides common functionality.</span></span>

<span data-ttu-id="c26d5-142">Per i controller di movimento come in Oculus, vive e la realtà mista di Windows, la rotazione corrisponderà alla rotazione del controller.</span><span class="sxs-lookup"><span data-stu-id="c26d5-142">For motion controllers like in Oculus, Vive, and Windows Mixed Reality, the rotation will match the rotation of the controller.</span></span> <span data-ttu-id="c26d5-143">Per gli altri controller, ad esempio HoloLens 2, la rotazione corrisponde alla punta della mano fornita dal sistema.</span><span class="sxs-lookup"><span data-stu-id="c26d5-143">For other controllers like HoloLens 2 articulated hands, the rotation matches the system-provided pointing pose of the hand.</span></span>

<img src="../images/pointers/MRTK_Pointers_Line.png" width="400" alt="MRTK Pointer Line">

##### [`CurvePointer`](xref:Microsoft.MixedReality.Toolkit.Input.CurvePointer)

<span data-ttu-id="c26d5-144">*CurvePointer* estende la classe *LinePointer* consentendo il cast dei raggi in più passaggi lungo una curva.</span><span class="sxs-lookup"><span data-stu-id="c26d5-144">*CurvePointer* extends the *LinePointer* class by allowing for multi-step ray casts along a curve.</span></span> <span data-ttu-id="c26d5-145">Questa classe di puntatore di base è utile per le istanze curve, ad esempio i puntatori di teleportazione in cui la linea si piega in modo coerente in una parabola.</span><span class="sxs-lookup"><span data-stu-id="c26d5-145">This base pointer class is useful for curved instances such as teleportation pointers where the line consistently bends into a parabola.</span></span>

##### [`ShellHandRayPointer`](xref:Microsoft.MixedReality.Toolkit.Input.ShellHandRayPointer)

<span data-ttu-id="c26d5-146">L'implementazione di *ShellHandRayPointer*, che si estende da [`LinePointer`](xref:Microsoft.MixedReality.Toolkit.Input.MousePointer) , viene usata come impostazione predefinita per il *profilo del puntatore MRTK*.</span><span class="sxs-lookup"><span data-stu-id="c26d5-146">The implementation of *ShellHandRayPointer*, which extends from [`LinePointer`](xref:Microsoft.MixedReality.Toolkit.Input.MousePointer), is used as the default for the *MRTK Pointer Profile*.</span></span> <span data-ttu-id="c26d5-147">Il prefabbricato *DefaultControllerPointer* implementa la [`ShellHandRayPointer`](xref:Microsoft.MixedReality.Toolkit.Input.ShellHandRayPointer) classe.</span><span class="sxs-lookup"><span data-stu-id="c26d5-147">The *DefaultControllerPointer* prefab implements the [`ShellHandRayPointer`](xref:Microsoft.MixedReality.Toolkit.Input.ShellHandRayPointer) class.</span></span>

##### [`GGVPointer`](xref:Microsoft.MixedReality.Toolkit.Input.GGVPointer)

<span data-ttu-id="c26d5-148">Noto anche come puntatore a *sguardi/movimenti/voce (GGV)* , GGVPointer alimenta le interazioni di tipo "1" e "tocco", principalmente tramite lo sguardo e il tocco aereo o l'interazione con selezione voce.</span><span class="sxs-lookup"><span data-stu-id="c26d5-148">Also known as the *Gaze/Gesture/Voice (GGV)* pointer, the GGVPointer powers HoloLens 1-style look and tap interactions, primarily via Gaze and Air Tap or Gaze and voice Select interaction.</span></span> <span data-ttu-id="c26d5-149">La posizione e la direzione del puntatore GGV sono determinate dalla posizione e dalla rotazione della testa.</span><span class="sxs-lookup"><span data-stu-id="c26d5-149">The GGV pointer's position and direction is driven by the head's position and rotation.</span></span>

##### [`TouchPointer`](xref:Microsoft.MixedReality.Toolkit.Input.TouchPointer)

<span data-ttu-id="c26d5-150">Il *TouchPointer* è responsabile dell'uso di Unity touch input (ad esempio touchscreen).</span><span class="sxs-lookup"><span data-stu-id="c26d5-150">The *TouchPointer* is responsible for working with Unity Touch input (i.e. touchscreen).</span></span> <span data-ttu-id="c26d5-151">Si tratta di "Interactions", perché l'azione di toccare lo schermo consente di eseguire il cast di un raggio dalla fotocamera a una posizione potenzialmente lontana nella scena.</span><span class="sxs-lookup"><span data-stu-id="c26d5-151">These are 'far interactions' because the act of touching the screen will cast a ray from the camera to a potentially far location in the scene.</span></span>

##### [`MousePointer`](xref:Microsoft.MixedReality.Toolkit.Input.MousePointer)

<span data-ttu-id="c26d5-152">Il *MousePointer* alimenta una schermata per la Raycast globale per le interazioni di gran lunga, ma per il mouse anziché il tocco.</span><span class="sxs-lookup"><span data-stu-id="c26d5-152">The *MousePointer* powers a screen to world raycast for far interactions, but for mouse instead of touch.</span></span>

![Puntatore del mouse](../images/pointers/MRTK_MousePointer.png)

> [!NOTE]
> <span data-ttu-id="c26d5-154">Il supporto del mouse non è disponibile per impostazione predefinita in MRTK, ma può essere abilitato aggiungendo un nuovo *provider di dati di input* di tipo [`MouseDeviceManager`](xref:Microsoft.MixedReality.Toolkit.Input.UnityInput.MouseDeviceManager) al profilo di input MRTK e assegnando al [`MixedRealityMouseInputProfile`](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityMouseInputProfile) provider di dati.</span><span class="sxs-lookup"><span data-stu-id="c26d5-154">Mouse support is not available by default in MRTK but can be enabled by adding a new *Input Data Provider* of type [`MouseDeviceManager`](xref:Microsoft.MixedReality.Toolkit.Input.UnityInput.MouseDeviceManager) to the MRTK input profile and assigning the [`MixedRealityMouseInputProfile`](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityMouseInputProfile) to the data provider.</span></span>

#### <a name="near-pointers"></a><span data-ttu-id="c26d5-155">Near puntatori</span><span class="sxs-lookup"><span data-stu-id="c26d5-155">Near pointers</span></span>

##### [`PokePointer`](xref:Microsoft.MixedReality.Toolkit.Input.PokePointer)

<span data-ttu-id="c26d5-156">*[PokePointer](xref:Microsoft.MixedReality.Toolkit.Input.PokePointer)* viene usato per interagire con gli oggetti del gioco che supportano "near Interaction touchable".</span><span class="sxs-lookup"><span data-stu-id="c26d5-156">The *[PokePointer](xref:Microsoft.MixedReality.Toolkit.Input.PokePointer)* is used to interact with game objects that support “near interaction touchable.”</span></span> <span data-ttu-id="c26d5-157">ovvero GameObject a cui è associato uno [`NearInteractionTouchable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) script.</span><span class="sxs-lookup"><span data-stu-id="c26d5-157">which are GameObjects that have an attached [`NearInteractionTouchable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) script.</span></span> <span data-ttu-id="c26d5-158">Nel caso di UnityUI, questo puntatore Cerca NearInteractionTouchableUnityUIs.</span><span class="sxs-lookup"><span data-stu-id="c26d5-158">In the case of UnityUI, this pointer looks for NearInteractionTouchableUnityUIs.</span></span>  <span data-ttu-id="c26d5-159">PokePointer usa un SphereCast per determinare l'elemento ritoccabile più vicino e viene usato per potenziare elementi come i pulsanti stampabili.</span><span class="sxs-lookup"><span data-stu-id="c26d5-159">The PokePointer uses a SphereCast to determine the closest touchable element and is used to power things like the pressable buttons.</span></span>

 <span data-ttu-id="c26d5-160">Quando si configura GameObject con il [`NearInteractionTouchable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) componente, assicurarsi di configurare il parametro *localForward* in modo che punti all'inizio del pulsante o di un altro oggetto che deve essere reso toccabile.</span><span class="sxs-lookup"><span data-stu-id="c26d5-160">When configuring the GameObject with the [`NearInteractionTouchable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) component, make sure to configure the *localForward* parameter to point out of the front of the button or other object that should be made touchable.</span></span> <span data-ttu-id="c26d5-161">Assicurarsi inoltre che i *limiti* di touchable corrispondano ai limiti dell'oggetto toccabile.</span><span class="sxs-lookup"><span data-stu-id="c26d5-161">Also make sure that the touchable's *bounds* matches the bounds of the touchable object.</span></span>

<span data-ttu-id="c26d5-162">Proprietà del puntatore poke utili:</span><span class="sxs-lookup"><span data-stu-id="c26d5-162">Useful Poke Pointer properties:</span></span>

- <span data-ttu-id="c26d5-163">*TouchableDistance*: distanza massima in cui è possibile interagire con una superficie toccabile</span><span class="sxs-lookup"><span data-stu-id="c26d5-163">*TouchableDistance*: Maximum distance in which a touchable surface can be interacted with</span></span>
- <span data-ttu-id="c26d5-164">Oggetti *visivi*: oggetto gioco usato per eseguire il rendering dell'oggetto visivo della descrizione comando (l'anello sul dito, per impostazione predefinita).</span><span class="sxs-lookup"><span data-stu-id="c26d5-164">*Visuals*: Game object used to render finger tip visual (the ring on finger, by default).</span></span>
- <span data-ttu-id="c26d5-165">*Line*: linea facoltativa da trascinare da un dito alla superficie di input attiva.</span><span class="sxs-lookup"><span data-stu-id="c26d5-165">*Line*: Optional line to draw from fingertip to the active input surface.</span></span>
- <span data-ttu-id="c26d5-166">*Maschere livello poke* : matrice con priorità di LayerMasks per determinare il GameObject possibile con cui può interagire il puntatore e l'ordine di interazione da tentare.</span><span class="sxs-lookup"><span data-stu-id="c26d5-166">*Poke Layer Masks* - A prioritized array of LayerMasks to determine which possible GameObjects the pointer can interact with and the order of interaction to attempt.</span></span> <span data-ttu-id="c26d5-167">Si noti che un GameObject deve avere anche un `NearInteractionTouchable` componente per interagire con un puntatore poke.</span><span class="sxs-lookup"><span data-stu-id="c26d5-167">Note that a GameObject must also have a `NearInteractionTouchable` component in order to interact with a poke pointer.</span></span>

<img src="../images/pointers/MRTK_PokePointer.png" width="400" alt="Poke Pointer">

##### [`SpherePointer`](xref:Microsoft.MixedReality.Toolkit.Input.SpherePointer)

<span data-ttu-id="c26d5-168">*[SpherePointer](xref:Microsoft.MixedReality.Toolkit.Input.SpherePointer)* utilizza [UnityEngine. Physics. OverlapSphere](https://docs.unity3d.com/ScriptReference/Physics.OverlapSphere.html) per identificare l'oggetto più vicino per l' [`NearInteractionGrabbable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionGrabbable) interazione, che risulta utile per l'input "afferrabile", ad esempio `ManipulationHandler` .</span><span class="sxs-lookup"><span data-stu-id="c26d5-168">The *[SpherePointer](xref:Microsoft.MixedReality.Toolkit.Input.SpherePointer)* uses [UnityEngine.Physics.OverlapSphere](https://docs.unity3d.com/ScriptReference/Physics.OverlapSphere.html) in order to identify the closest [`NearInteractionGrabbable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionGrabbable) object for interaction, which is useful for "grabbable" input like the `ManipulationHandler`.</span></span> <span data-ttu-id="c26d5-169">Analogamente alla [`PokePointer`](xref:Microsoft.MixedReality.Toolkit.Input.PokePointer) / [`NearInteractionTouchable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) coppia funzionale, per poter interagire con il puntatore a sfera, l'oggetto Game deve contenere un componente che rappresenta lo [`NearInteractionGrabbable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionGrabbable) script.</span><span class="sxs-lookup"><span data-stu-id="c26d5-169">Similar to the [`PokePointer`](xref:Microsoft.MixedReality.Toolkit.Input.PokePointer)/[`NearInteractionTouchable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) functional pair, in order to be interactable with the Sphere Pointer, the game object must contain a component that is the [`NearInteractionGrabbable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionGrabbable) script.</span></span>

<img src="../images/pointers/MRTK_GrabPointer.jpg" width="400" alt="Grab Pointer">

<span data-ttu-id="c26d5-170">Proprietà del puntatore della sfera utili:</span><span class="sxs-lookup"><span data-stu-id="c26d5-170">Useful Sphere Pointer properties:</span></span>

- <span data-ttu-id="c26d5-171">*Raggio del cast della sfera*: raggio per la sfera utilizzata per eseguire una query per gli oggetti afferrabili.</span><span class="sxs-lookup"><span data-stu-id="c26d5-171">*Sphere Cast Radius*: The radius for the sphere used to query for grabbable objects.</span></span>
- <span data-ttu-id="c26d5-172">*Near object Margin*: distanza sulla parte superiore del raggio del cast della sfera per eseguire una query per rilevare se un oggetto si trova vicino al puntatore.</span><span class="sxs-lookup"><span data-stu-id="c26d5-172">*Near Object Margin*: The distance on top of the Sphere Cast Radius to query for detecting if an object is near the pointer.</span></span> <span data-ttu-id="c26d5-173">Raggio totale vicino al rilevamento di oggetti</span><span class="sxs-lookup"><span data-stu-id="c26d5-173">Total Near Object detection radius is Sphere Cast Radius + Near Object Margin</span></span>
- <span data-ttu-id="c26d5-174">*Angolo vicino al settore oggetto*: angolo intorno all'asse di avanzamento del puntatore per l'esecuzione di query per gli oggetti vicini.</span><span class="sxs-lookup"><span data-stu-id="c26d5-174">*Near Object Sector Angle*: The angle around the forward axis of the pointer for querying for nearby objects.</span></span> <span data-ttu-id="c26d5-175">Fa `IsNearObject` in modo che la query funzioni come un cono.</span><span class="sxs-lookup"><span data-stu-id="c26d5-175">Makes the `IsNearObject` query function like a cone.</span></span> <span data-ttu-id="c26d5-176">Per impostazione predefinita, questo valore è impostato su 66 gradi per trovare la corrispondenza con il comportamento di Hololens 2</span><span class="sxs-lookup"><span data-stu-id="c26d5-176">This is set to 66 degrees by default to match Hololens 2 behavior</span></span>

![Puntatore a sfera modificato in modo da eseguire solo una query per gli oggetti nella direzione avanti](https://user-images.githubusercontent.com/39840334/82500569-72d58300-9aa8-11ea-8102-ec9a62832d4e.png)

- <span data-ttu-id="c26d5-178">*Near object Smoothing Factor*: fattore di smussatura per il rilevamento Near object.</span><span class="sxs-lookup"><span data-stu-id="c26d5-178">*Near Object Smoothing Factor*: Smoothing factor for Near Object detection.</span></span> <span data-ttu-id="c26d5-179">Se viene rilevato un oggetto nel raggio dell'oggetto near, il raggio su cui viene eseguita la query diventa Near object RADIUS \* (1 + Near object Smoothing Factor) per ridurre la sensibilità e rendere più difficile per un oggetto lasciare l'intervallo di rilevamento.</span><span class="sxs-lookup"><span data-stu-id="c26d5-179">If an object is detected in the Near Object Radius, the queried radius then becomes Near Object Radius \* (1 + Near Object Smoothing Factor) to reduce the sensitivity and make it harder for an object to leave the detection range.</span></span>
- <span data-ttu-id="c26d5-180">*Acquisisci maschere di livello* : una matrice con priorità di LayerMasks per determinare il GameObject possibile con cui può interagire il puntatore e l'ordine di interazione da tentare.</span><span class="sxs-lookup"><span data-stu-id="c26d5-180">*Grab Layer Masks* - A prioritized array of LayerMasks to determine which possible GameObjects the pointer can interact with and the order of interaction to attempt.</span></span> <span data-ttu-id="c26d5-181">Si noti che un GameObject deve avere anche un oggetto `NearInteractionGrabbable` per interagire con un SpherePointer.</span><span class="sxs-lookup"><span data-stu-id="c26d5-181">Note that a GameObject must also have a `NearInteractionGrabbable` to interact with a SpherePointer.</span></span>
    > [!NOTE]
    > <span data-ttu-id="c26d5-182">Il livello di riconoscimento spaziale è disabilitato nel prefabbricato GrabPointer predefinito fornito da MRTK.</span><span class="sxs-lookup"><span data-stu-id="c26d5-182">The Spatial Awareness layer is disabled in the default GrabPointer prefab provided by MRTK.</span></span> <span data-ttu-id="c26d5-183">Questa operazione viene eseguita per ridurre l'effetto sulle prestazioni dell'esecuzione di una query di sovrapposizione delle sfere con la mesh spaziale.</span><span class="sxs-lookup"><span data-stu-id="c26d5-183">This is done to reduce performance impact of doing a sphere overlap query with the spatial mesh.</span></span> <span data-ttu-id="c26d5-184">Questa operazione può essere abilitata modificando il prefabbricato GrabPointer.</span><span class="sxs-lookup"><span data-stu-id="c26d5-184">You can enable this by modifying the GrabPointer prefab.</span></span>
- <span data-ttu-id="c26d5-185">*Ignorare i conflitti non in FOV* -se ignorare i Collider che potrebbero essere vicini al puntatore, ma non effettivamente nell'oggetto visivo FOV.</span><span class="sxs-lookup"><span data-stu-id="c26d5-185">*Ignore Colliders Not in FOV* - Whether to ignore colliders that may be near the pointer, but not actually in the visual FOV.</span></span>
<span data-ttu-id="c26d5-186">Questa operazione può impedire le catture accidentali e consentirà di attivare i raggi mano quando si può trovarsi vicino a un oggetto afferrabile, ma non può essere visualizzato.</span><span class="sxs-lookup"><span data-stu-id="c26d5-186">This can prevent accidental grabs, and will allow hand rays to turn on when you may be near a grabbable but cannot see it.</span></span> <span data-ttu-id="c26d5-187">L'oggetto *visivo FOV* viene definito tramite un cono anziché il tronco tipico per motivi di prestazioni.</span><span class="sxs-lookup"><span data-stu-id="c26d5-187">The *Visual FOV* is defined via a cone instead of the the typical frustum for performance reasons.</span></span> <span data-ttu-id="c26d5-188">Questo cono è centrato e orientato allo stesso modo in cui si trova il tronco della fotocamera con un raggio uguale a metà di visualizzazione (o di FOV verticale).</span><span class="sxs-lookup"><span data-stu-id="c26d5-188">This cone is centered and oriented the same as the camera's frustum with a radius equal to half display height(or vertical FOV).</span></span>

<img src="../images/input/pointers/SpherePointer_VisualFOV.png" width="200" alt="Sphere Pointer">

#### <a name="teleport-pointers"></a><span data-ttu-id="c26d5-189">Puntatori Teleport</span><span class="sxs-lookup"><span data-stu-id="c26d5-189">Teleport pointers</span></span>

- <span data-ttu-id="c26d5-190">[`TeleportPointer`](xref:Microsoft.MixedReality.Toolkit.Teleport.TeleportPointer) genererà una richiesta di Teleport quando viene eseguita l'azione (ad esempio</span><span class="sxs-lookup"><span data-stu-id="c26d5-190">[`TeleportPointer`](xref:Microsoft.MixedReality.Toolkit.Teleport.TeleportPointer) will raise a teleport request when action is taken (i.e</span></span> <span data-ttu-id="c26d5-191">viene premuto il pulsante Teleport per spostare l'utente.</span><span class="sxs-lookup"><span data-stu-id="c26d5-191">the teleport button is pressed) in order to move the user.</span></span>
- <span data-ttu-id="c26d5-192">[`ParabolicTeleportPointer`](xref:Microsoft.MixedReality.Toolkit.Teleport.ParabolicTeleportPointer) genererà una richiesta di Teleport quando viene eseguita l'azione (ad esempio</span><span class="sxs-lookup"><span data-stu-id="c26d5-192">[`ParabolicTeleportPointer`](xref:Microsoft.MixedReality.Toolkit.Teleport.ParabolicTeleportPointer) will raise a teleport request when action is taken (i.e</span></span> <span data-ttu-id="c26d5-193">il pulsante teleport viene premuto con una linea parabolica Raycast per spostare l'utente.</span><span class="sxs-lookup"><span data-stu-id="c26d5-193">the teleport button is pressed) with a parabolic line raycast in order to move the user.</span></span>

<img src="../images/pointers/MRTK_Pointers_Parabolic.png" width="400" alt="Pointer Parabolic">

## <a name="pointer-support-for-mixed-reality-platforms"></a><span data-ttu-id="c26d5-194">Supporto del puntatore per le piattaforme di realtà miste</span><span class="sxs-lookup"><span data-stu-id="c26d5-194">Pointer support for mixed reality platforms</span></span>

<span data-ttu-id="c26d5-195">La tabella seguente illustra in dettaglio i tipi di puntatore che vengono in genere usati per le piattaforme comuni in MRTK.</span><span class="sxs-lookup"><span data-stu-id="c26d5-195">The following table details the pointer types that are typically used for the common platforms in MRTK.</span></span> <span data-ttu-id="c26d5-196">Nota: è possibile aggiungere diversi tipi di puntatore a queste piattaforme.</span><span class="sxs-lookup"><span data-stu-id="c26d5-196">NOTE: it's possible to add different pointer types to these platforms.</span></span> <span data-ttu-id="c26d5-197">Ad esempio, è possibile aggiungere un puntatore poke o un puntatore a sfera a VR.</span><span class="sxs-lookup"><span data-stu-id="c26d5-197">For example, you could add a Poke pointer or Sphere pointer to VR.</span></span> <span data-ttu-id="c26d5-198">Inoltre, i dispositivi VR con un gamepad possono usare il puntatore GGV.</span><span class="sxs-lookup"><span data-stu-id="c26d5-198">Additionally, VR devices with a gamepad could use the GGV pointer.</span></span>

|       <span data-ttu-id="c26d5-199">Puntatore</span><span class="sxs-lookup"><span data-stu-id="c26d5-199">Pointer</span></span>              | <span data-ttu-id="c26d5-200">OpenVR</span><span class="sxs-lookup"><span data-stu-id="c26d5-200">OpenVR</span></span>  | <span data-ttu-id="c26d5-201">Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="c26d5-201">Windows Mixed Reality</span></span> | <span data-ttu-id="c26d5-202">HoloLens 1</span><span class="sxs-lookup"><span data-stu-id="c26d5-202">HoloLens 1</span></span> | <span data-ttu-id="c26d5-203">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="c26d5-203">HoloLens 2</span></span> |
|---------------------|---------|-----------------------|------------|------------|
| <span data-ttu-id="c26d5-204">ShellHandRayPointer</span><span class="sxs-lookup"><span data-stu-id="c26d5-204">ShellHandRayPointer</span></span> | <span data-ttu-id="c26d5-205">Valido</span><span class="sxs-lookup"><span data-stu-id="c26d5-205">Valid</span></span>   | <span data-ttu-id="c26d5-206">Valido</span><span class="sxs-lookup"><span data-stu-id="c26d5-206">Valid</span></span>                 |            | <span data-ttu-id="c26d5-207">Valido</span><span class="sxs-lookup"><span data-stu-id="c26d5-207">Valid</span></span>      |
| <span data-ttu-id="c26d5-208">TeleportPointer</span><span class="sxs-lookup"><span data-stu-id="c26d5-208">TeleportPointer</span></span>     | <span data-ttu-id="c26d5-209">Valido</span><span class="sxs-lookup"><span data-stu-id="c26d5-209">Valid</span></span>   | <span data-ttu-id="c26d5-210">Valido</span><span class="sxs-lookup"><span data-stu-id="c26d5-210">Valid</span></span>                 |            |            |
| <span data-ttu-id="c26d5-211">GGVPointer</span><span class="sxs-lookup"><span data-stu-id="c26d5-211">GGVPointer</span></span>          |         |                       | <span data-ttu-id="c26d5-212">Valido</span><span class="sxs-lookup"><span data-stu-id="c26d5-212">Valid</span></span>      |            |
| <span data-ttu-id="c26d5-213">SpherePointer</span><span class="sxs-lookup"><span data-stu-id="c26d5-213">SpherePointer</span></span>       |         |                       |            | <span data-ttu-id="c26d5-214">Valido</span><span class="sxs-lookup"><span data-stu-id="c26d5-214">Valid</span></span>      |
| <span data-ttu-id="c26d5-215">PokePointer</span><span class="sxs-lookup"><span data-stu-id="c26d5-215">PokePointer</span></span>         |         |                       |            | <span data-ttu-id="c26d5-216">Valido</span><span class="sxs-lookup"><span data-stu-id="c26d5-216">Valid</span></span>      |

## <a name="pointer-interactions-via-code"></a><span data-ttu-id="c26d5-217">Interazioni tra puntatori tramite codice</span><span class="sxs-lookup"><span data-stu-id="c26d5-217">Pointer interactions via code</span></span>

### <a name="pointer-event-interfaces"></a><span data-ttu-id="c26d5-218">Interfacce eventi puntatore</span><span class="sxs-lookup"><span data-stu-id="c26d5-218">Pointer event interfaces</span></span>

<span data-ttu-id="c26d5-219">I monobehavior che implementano una o più delle interfacce seguenti e sono assegnati a un GameObject con un oggetto riceverà `Collider` gli eventi di interazione del puntatore come definito dall'interfaccia associata.</span><span class="sxs-lookup"><span data-stu-id="c26d5-219">MonoBehaviours that implement one or more of the following interfaces and are assigned to a GameObject with a `Collider` will receive Pointer interactions events as defined by the associated interface.</span></span>

| <span data-ttu-id="c26d5-220">Event</span><span class="sxs-lookup"><span data-stu-id="c26d5-220">Event</span></span> | <span data-ttu-id="c26d5-221">Descrizione</span><span class="sxs-lookup"><span data-stu-id="c26d5-221">Description</span></span> | <span data-ttu-id="c26d5-222">Gestore</span><span class="sxs-lookup"><span data-stu-id="c26d5-222">Handler</span></span> |
| --- | --- | --- |
| <span data-ttu-id="c26d5-223">Prima dello stato attivo modificato/stato attivo modificato</span><span class="sxs-lookup"><span data-stu-id="c26d5-223">Before Focus Changed / Focus Changed</span></span> | <span data-ttu-id="c26d5-224">Generato nell'oggetto Game che perde lo stato attivo e quello che lo ottiene ogni volta che un puntatore cambia lo stato attivo.</span><span class="sxs-lookup"><span data-stu-id="c26d5-224">Raised on both the game object losing focus and the one gaining it every time a pointer changes focus.</span></span> | [`IMixedRealityFocusChangedHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityFocusChangedHandler) |
<span data-ttu-id="c26d5-225">Invio/uscita dello stato attivo</span><span class="sxs-lookup"><span data-stu-id="c26d5-225">Focus Enter / Exit</span></span> | <span data-ttu-id="c26d5-226">Generato sull'oggetto gioco che ottiene lo stato attivo quando il primo puntatore lo immette e su quello che perde lo stato attivo quando l'ultimo puntatore lo lascia.</span><span class="sxs-lookup"><span data-stu-id="c26d5-226">Raised on the game object gaining focus when the first pointer enters it and on the one losing focus when the last pointer leaves it.</span></span> | [`IMixedRealityFocusHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityFocusHandler)
<span data-ttu-id="c26d5-227">Puntatore inattivo/trascinamento/clic</span><span class="sxs-lookup"><span data-stu-id="c26d5-227">Pointer Down / Dragged / Up / Clicked</span></span> | <span data-ttu-id="c26d5-228">Elevato per segnalare la pressione, il trascinamento e il rilascio del puntatore.</span><span class="sxs-lookup"><span data-stu-id="c26d5-228">Raised to report pointer press, drag and release.</span></span> | [`IMixedRealityPointerHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityPointerHandler)
<span data-ttu-id="c26d5-229">Tocco avviato/aggiornato/completato</span><span class="sxs-lookup"><span data-stu-id="c26d5-229">Touch Started / Updated / Completed</span></span> | <span data-ttu-id="c26d5-230">Generato da puntatori compatibili con il tocco come [`PokePointer`](xref:Microsoft.MixedReality.Toolkit.Input.PokePointer) per segnalare l'attività di tocco.</span><span class="sxs-lookup"><span data-stu-id="c26d5-230">Raised by touch-aware pointers like [`PokePointer`](xref:Microsoft.MixedReality.Toolkit.Input.PokePointer) to report touch activity.</span></span> | [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler)

> [!NOTE]
> <span data-ttu-id="c26d5-231">[`IMixedRealityFocusChangedHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityFocusChangedHandler) e [`IMixedRealityFocusHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityFocusHandler) devono essere gestiti negli oggetti in cui vengono generati.</span><span class="sxs-lookup"><span data-stu-id="c26d5-231">[`IMixedRealityFocusChangedHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityFocusChangedHandler) and [`IMixedRealityFocusHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityFocusHandler) should be handled in the objects they are raised on.</span></span> <span data-ttu-id="c26d5-232">È possibile ricevere eventi di attivazione a livello globale, ma, a differenza di altri eventi di input, il gestore eventi globale non blocca la ricezione degli eventi in base allo stato attivo (l'evento verrà ricevuto dal gestore globale e da un oggetto corrispondente nello stato attivo).</span><span class="sxs-lookup"><span data-stu-id="c26d5-232">It is possible to receive focus events globally but, unlike other input events, global event handler won't block receiving events based on focus (the event will be received by both global handler and a corresponding object in focus).</span></span>

#### <a name="pointer-input-events-in-action"></a><span data-ttu-id="c26d5-233">Eventi di input puntatore in azione</span><span class="sxs-lookup"><span data-stu-id="c26d5-233">Pointer input events in action</span></span>

<span data-ttu-id="c26d5-234">Gli eventi di input del puntatore vengono riconosciuti e gestiti dal sistema di input MRTK in modo analogo [agli eventi di input normali](input-events.md#input-events-in-action).</span><span class="sxs-lookup"><span data-stu-id="c26d5-234">Pointer input events are recognized and handled by the MRTK input system in a similar way as [regular input events](input-events.md#input-events-in-action).</span></span> <span data-ttu-id="c26d5-235">La differenza consiste nel fatto che gli eventi di input del puntatore vengono gestiti solo da GameObject nello stato attivo dal puntatore che ha attivato l'evento di input, nonché da eventuali gestori di input globali.</span><span class="sxs-lookup"><span data-stu-id="c26d5-235">The difference being that pointer input events are handled only by the GameObject in focus by the pointer that fired the input event, as well as any global input handlers.</span></span> <span data-ttu-id="c26d5-236">Gli eventi di input normali vengono gestiti da GameObject in stato attivo per tutti i puntatori attivi.</span><span class="sxs-lookup"><span data-stu-id="c26d5-236">Regular input events are handled by GameObjects in focus for all active pointers.</span></span>

1. <span data-ttu-id="c26d5-237">Il sistema di input MRTK riconosce che si è verificato un evento di input</span><span class="sxs-lookup"><span data-stu-id="c26d5-237">The MRTK input system recognizes an input event has occurred</span></span>
1. <span data-ttu-id="c26d5-238">Il sistema di input MRTK genera la funzione di interfaccia pertinente per l'evento di input in tutti i gestori di input globali registrati</span><span class="sxs-lookup"><span data-stu-id="c26d5-238">The MRTK input system fires the relevant interface function for the input event to all registered global input handlers</span></span>
1. <span data-ttu-id="c26d5-239">Il sistema di input determina quale GameObject è attivo per il puntatore che ha attivato l'evento</span><span class="sxs-lookup"><span data-stu-id="c26d5-239">The input system determines which GameObject is in focus for the pointer that fired the event</span></span>
    1. <span data-ttu-id="c26d5-240">Il sistema di input usa il [sistema di eventi di Unity](https://docs.unity3d.com/Manual/EventSystem.html) per attivare la funzione di interfaccia pertinente per tutti i componenti corrispondenti nel GameObject con stato attivo</span><span class="sxs-lookup"><span data-stu-id="c26d5-240">The input system utilizes the [Unity's Event System](https://docs.unity3d.com/Manual/EventSystem.html) to fire the relevant interface function for all matching components on the focused GameObject</span></span>
    1. <span data-ttu-id="c26d5-241">Se in qualsiasi momento un evento di input è stato [contrassegnato come usato](input-events.md#how-to-stop-input-events), il processo terminerà e nessun altro GameObject riceverà i callback.</span><span class="sxs-lookup"><span data-stu-id="c26d5-241">If at any point an input event has been [marked as used](input-events.md#how-to-stop-input-events), the process will end and no further GameObjects will receive callbacks.</span></span>
        - <span data-ttu-id="c26d5-242">Esempio: ai componenti che implementano l'interfaccia [`IMixedRealityFocusHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySpeechHandler) verrà eseguita la ricerca di un GameObject guadagni o perde lo stato attivo</span><span class="sxs-lookup"><span data-stu-id="c26d5-242">Example: Components implementing the interface [`IMixedRealityFocusHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySpeechHandler) will be searched for a GameObject gains or loses focus</span></span>
        - <span data-ttu-id="c26d5-243">Nota: il sistema di eventi Unity verrà propagato per eseguire una ricerca nel GameObject padre se non sono stati trovati componenti corrispondenti all'interfaccia desiderata nel GameObject corrente.</span><span class="sxs-lookup"><span data-stu-id="c26d5-243">Note: The Unity Event System will bubble up to search the parent GameObject if no components matching the desired interface are found on the current GameObject..</span></span>
1. <span data-ttu-id="c26d5-244">Se non viene registrato alcun gestore di input globale e non viene trovato alcun GameObject con un componente/interfaccia corrispondente, il sistema di input chiamerà ogni gestore di input registrato di fallback.</span><span class="sxs-lookup"><span data-stu-id="c26d5-244">If no global input handlers are registered and no GameObject is found with a matching component/interface, then the input system will call each fallback registered input handlers</span></span>

#### <a name="example"></a><span data-ttu-id="c26d5-245">Esempio</span><span class="sxs-lookup"><span data-stu-id="c26d5-245">Example</span></span>

<span data-ttu-id="c26d5-246">Di seguito è riportato uno script di esempio che modifica il colore del renderer collegato quando un puntatore accetta o lascia lo stato attivo o quando un puntatore seleziona l'oggetto.</span><span class="sxs-lookup"><span data-stu-id="c26d5-246">Below is an example script that changes the color of the attached renderer when a pointer takes or leaves focus or when a pointer selects the object.</span></span>

```c#
public class ColorTap : MonoBehaviour, IMixedRealityFocusHandler, IMixedRealityPointerHandler
{
    private Color color_IdleState = Color.cyan;
    private Color color_OnHover = Color.white;
    private Color color_OnSelect = Color.blue;
    private Material material;

    private void Awake()
    {
        material = GetComponent<Renderer>().material;
    }

    void IMixedRealityFocusHandler.OnFocusEnter(FocusEventData eventData)
    {
        material.color = color_OnHover;
    }

    void IMixedRealityFocusHandler.OnFocusExit(FocusEventData eventData)
    {
        material.color = color_IdleState;
    }

    void IMixedRealityPointerHandler.OnPointerDown(
         MixedRealityPointerEventData eventData) { }

    void IMixedRealityPointerHandler.OnPointerDragged(
         MixedRealityPointerEventData eventData) { }

    void IMixedRealityPointerHandler.OnPointerClicked(MixedRealityPointerEventData eventData)
    {
        material.color = color_OnSelect;
    }
}
```

### <a name="query-pointers"></a><span data-ttu-id="c26d5-247">Puntatori di query</span><span class="sxs-lookup"><span data-stu-id="c26d5-247">Query pointers</span></span>

<span data-ttu-id="c26d5-248">È possibile raccogliere tutti i puntatori attualmente attivi eseguendo un ciclo attraverso le origini di input disponibili, ad esempio</span><span class="sxs-lookup"><span data-stu-id="c26d5-248">It is possible to gather all pointers currently active by looping through the available input sources (i.e</span></span> <span data-ttu-id="c26d5-249">controller e input disponibili) per individuare i puntatori a essi collegati.</span><span class="sxs-lookup"><span data-stu-id="c26d5-249">controllers and inputs available) to discover which pointers are attached to them.</span></span>

```c#
var pointers = new HashSet<IMixedRealityPointer>();

// Find all valid pointers
foreach (var inputSource in CoreServices.InputSystem.DetectedInputSources)
{
    foreach (var pointer in inputSource.Pointers)
    {
        if (pointer.IsInteractionEnabled && !pointers.Contains(pointer))
        {
            pointers.Add(pointer);
        }
    }
}
```

#### <a name="primary-pointer"></a><span data-ttu-id="c26d5-250">Puntatore primario</span><span class="sxs-lookup"><span data-stu-id="c26d5-250">Primary pointer</span></span>

<span data-ttu-id="c26d5-251">Gli sviluppatori possono sottoscrivere l'evento PrimaryPointerChanged di FocusProviders per ricevere una notifica quando il puntatore primario è stato modificato.</span><span class="sxs-lookup"><span data-stu-id="c26d5-251">Developers can subscribe to the FocusProviders PrimaryPointerChanged event to be notified when the primary pointer in focus has changed.</span></span> <span data-ttu-id="c26d5-252">Questo può essere estremamente utile per identificare se l'utente sta attualmente interagendo con una scena tramite lo sguardo o un raggio di mano o un'altra origine di input.</span><span class="sxs-lookup"><span data-stu-id="c26d5-252">This can be extremely useful to identify if the user is currently interacting with a scene via gaze or a hand ray or another input source.</span></span>

```c#
private void OnEnable()
{
    var focusProvider = CoreServices.InputSystem?.FocusProvider;
    focusProvider?.SubscribeToPrimaryPointerChanged(OnPrimaryPointerChanged, true);
}

private void OnPrimaryPointerChanged(IMixedRealityPointer oldPointer, IMixedRealityPointer newPointer)
{
    ...
}

private void OnDisable()
{
    var focusProvider = CoreServices.InputSystem?.FocusProvider;
    focusProvider?.UnsubscribeFromPrimaryPointerChanged(OnPrimaryPointerChanged);

    // This flushes out the current primary pointer
    OnPrimaryPointerChanged(null, null);
}
```

<span data-ttu-id="c26d5-253">La `PrimaryPointerExample` scena (assets/MRTK/examples/Demos/input/Scenes/PrimaryPointer) Mostra come usare la [`PrimaryPointerChangedHandler`](xref:Microsoft.MixedReality.Toolkit.Input.PrimaryPointerChangedHandler) per gli eventi per rispondere a un nuovo puntatore primario.</span><span class="sxs-lookup"><span data-stu-id="c26d5-253">The `PrimaryPointerExample` (Assets/MRTK/Examples/Demos/Input/Scenes/PrimaryPointer) scene shows how to use the [`PrimaryPointerChangedHandler`](xref:Microsoft.MixedReality.Toolkit.Input.PrimaryPointerChangedHandler) for events to respond to a new primary pointer.</span></span>

<img src="../images/pointers/PrimaryPointerExample.png" style="max-width:100%;" alt="Primary Pointer Example">

### <a name="pointer-result"></a><span data-ttu-id="c26d5-254">Risultato indicatore di misura</span><span class="sxs-lookup"><span data-stu-id="c26d5-254">Pointer result</span></span>

<span data-ttu-id="c26d5-255">La [`Result`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityPointer.Result) Proprietà Pointer contiene il risultato corrente per la query della scena utilizzata per determinare l'oggetto con lo stato attivo.</span><span class="sxs-lookup"><span data-stu-id="c26d5-255">The pointer [`Result`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityPointer.Result) property contains the current result for the scene query used to determine the object with focus.</span></span> <span data-ttu-id="c26d5-256">Per un puntatore Raycast, come quello creato per impostazione predefinita per i controller di movimento, l'input dello sguardo e il raggio della mano, conterrà la posizione e la normale della hit raycast.</span><span class="sxs-lookup"><span data-stu-id="c26d5-256">For a raycast pointer, like the ones created by default for motion controllers, gaze input and hand rays, it will contain the location and normal of the raycast hit.</span></span>

```c#
private void IMixedRealityPointerHandler.OnPointerClicked(MixedRealityPointerEventData eventData)
{
    var result = eventData.Pointer.Result;
    var spawnPosition = result.Details.Point;
    var spawnRotation = Quaternion.LookRotation(result.Details.Normal);
    Instantiate(MyPrefab, spawnPosition, spawnRotation);
}
```

<span data-ttu-id="c26d5-257">La `PointerResultExample` scena (assets/MRTK/examples/Demos/input/Scenes/PointerResult/PointerResultExample. Unity) Mostra come usare il puntatore [`Result`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityPointer.Result) per generare un oggetto in corrispondenza della posizione di hit.</span><span class="sxs-lookup"><span data-stu-id="c26d5-257">The `PointerResultExample` scene (Assets/MRTK/Examples/Demos/Input/Scenes/PointerResult/PointerResultExample.unity) shows how to use the pointer [`Result`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityPointer.Result) to spawn an object at the hit location.</span></span>

<img src="../images/input/PointerResultExample.png" style="max-width:100%;" alt="Pointer Result">

### <a name="disable-pointers"></a><span data-ttu-id="c26d5-258">Disabilitare i puntatori</span><span class="sxs-lookup"><span data-stu-id="c26d5-258">Disable pointers</span></span>

<span data-ttu-id="c26d5-259">Per attivare e disattivare i puntatori, ad esempio per disabilitare il raggio della mano, impostare [`PointerBehavior`](xref:Microsoft.MixedReality.Toolkit.Input.PointerBehavior) per un tipo di puntatore specificato tramite [`PointerUtils`](xref:Microsoft.MixedReality.Toolkit.Input.PointerUtils) .</span><span class="sxs-lookup"><span data-stu-id="c26d5-259">To turn enable and disable pointers (for example, to disable the hand ray), set the [`PointerBehavior`](xref:Microsoft.MixedReality.Toolkit.Input.PointerBehavior) for a given pointer type via [`PointerUtils`](xref:Microsoft.MixedReality.Toolkit.Input.PointerUtils).</span></span>

```c#
// Disable the hand rays
PointerUtils.SetHandRayPointerBehavior(PointerBehavior.AlwaysOff);

// Disable hand rays for the right hand only
PointerUtils.SetHandRayPointerBehavior(PointerBehavior.AlwaysOff, Handedness.Right);

// Disable the gaze pointer
PointerUtils.SetGazePointerBehavior(PointerBehavior.AlwaysOff);

// Set the behavior to match HoloLens 1
// Note, if on HoloLens 2, you must configure your pointer profile to make the GGV pointer show up for articulated hands.
public void SetHoloLens1()
{
    PointerUtils.SetPokePointerBehavior(PointerBehavior.AlwaysOff, Handedness.Any);
    PointerUtils.SetGrabPointerBehavior(PointerBehavior.AlwaysOff, Handedness.Any);
    PointerUtils.SetRayPointerBehavior(PointerBehavior.AlwaysOff, Handedness.Any);
    PointerUtils.SetGGVBehavior(PointerBehavior.Default);
}
```

<span data-ttu-id="c26d5-260">[`PointerUtils`](xref:Microsoft.MixedReality.Toolkit.Input.PointerUtils) [`TurnPointersOnOff`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.DisablePointersExample) Per altri esempi, vedere e.</span><span class="sxs-lookup"><span data-stu-id="c26d5-260">See [`PointerUtils`](xref:Microsoft.MixedReality.Toolkit.Input.PointerUtils) and [`TurnPointersOnOff`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.DisablePointersExample) for more examples.</span></span>

## <a name="pointer-interactions-via-editor"></a><span data-ttu-id="c26d5-261">Interazioni tra puntatori tramite Editor</span><span class="sxs-lookup"><span data-stu-id="c26d5-261">Pointer interactions via editor</span></span>

<span data-ttu-id="c26d5-262">Per gli eventi del puntatore gestiti da [`IMixedRealityPointerHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityPointerHandler) , MRTK offre ulteriore praticità sotto forma di [`PointerHandler`](xref:Microsoft.MixedReality.Toolkit.Input.PointerHandler) componente, che consente di gestire gli eventi del puntatore direttamente tramite gli eventi di Unity.</span><span class="sxs-lookup"><span data-stu-id="c26d5-262">For pointer events handled by [`IMixedRealityPointerHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityPointerHandler), MRTK provides further convenience in the form of the [`PointerHandler`](xref:Microsoft.MixedReality.Toolkit.Input.PointerHandler) component, which allows pointer events to be handled directly via Unity Events.</span></span>

<img src="../images/pointers/PointerHandler.png" style="max-width:100%;" alt="Pointer Handler">

## <a name="pointer-extent"></a><span data-ttu-id="c26d5-263">Extent del puntatore</span><span class="sxs-lookup"><span data-stu-id="c26d5-263">Pointer extent</span></span>

<span data-ttu-id="c26d5-264">I puntatori a distanza presentano impostazioni che limitano il modo in cui verranno Raycast e interagiranno con altri oggetti nella scena.</span><span class="sxs-lookup"><span data-stu-id="c26d5-264">Far pointers have settings which limit how far they will raycast and interact with other objects in the scene.</span></span>
<span data-ttu-id="c26d5-265">Per impostazione predefinita, questo valore è impostato su 10 metri.</span><span class="sxs-lookup"><span data-stu-id="c26d5-265">By default, this value is set to 10 meters.</span></span> <span data-ttu-id="c26d5-266">Questo valore è stato scelto per restare coerente con il comportamento della shell HoloLens.</span><span class="sxs-lookup"><span data-stu-id="c26d5-266">This value was chosen to remain consistent with the behavior of the HoloLens shell.</span></span>

<span data-ttu-id="c26d5-267">Questo può essere modificato aggiornando i `DefaultControllerPointer` campi del componente del prefabbricato [`ShellHandRayPointer`](xref:Microsoft.MixedReality.Toolkit.Input.ShellHandRayPointer) :</span><span class="sxs-lookup"><span data-stu-id="c26d5-267">This can be changed by updating the `DefaultControllerPointer` prefab's [`ShellHandRayPointer`](xref:Microsoft.MixedReality.Toolkit.Input.ShellHandRayPointer) component's fields:</span></span>

<span data-ttu-id="c26d5-268">*Extent del puntatore* : consente di controllare la distanza massima con cui i puntatori interagiranno.</span><span class="sxs-lookup"><span data-stu-id="c26d5-268">*Pointer Extent* - This controls the maximum distance that pointers will interact with.</span></span>

<span data-ttu-id="c26d5-269">*Extent del puntatore predefinito* : controlla la lunghezza del raggio/linea del puntatore che verrà eseguito quando il puntatore non interagisce con alcun elemento.</span><span class="sxs-lookup"><span data-stu-id="c26d5-269">*Default Pointer Extent* - This controls the length of the pointer ray/line that will render when the pointer is not interacting with anything.</span></span>

## <a name="see-also"></a><span data-ttu-id="c26d5-270">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="c26d5-270">See also</span></span>

- [<span data-ttu-id="c26d5-271">Architettura del puntatore</span><span class="sxs-lookup"><span data-stu-id="c26d5-271">Pointer Architecture</span></span>](../../architecture/controllers-pointers-and-focus.md)
- [<span data-ttu-id="c26d5-272">Eventi di input</span><span class="sxs-lookup"><span data-stu-id="c26d5-272">Input Events</span></span>](input-events.md)

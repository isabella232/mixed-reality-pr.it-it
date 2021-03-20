---
title: ConstraintManager
description: Panoramica su Gestione vincoli in MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: 7df30654195f0f8ffe73bcdd8bf7189035ad6775
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2021
ms.locfileid: "104691468"
---
# <a name="constraint-manager"></a><span data-ttu-id="628c6-104">Gestione vincoli</span><span class="sxs-lookup"><span data-stu-id="628c6-104">Constraint manager</span></span>

<span data-ttu-id="628c6-105">Gestione vincoli consente di applicare un set di componenti dei vincoli a una trasformazione.</span><span class="sxs-lookup"><span data-stu-id="628c6-105">The constraint manager allows to apply a set of constraint components to a transform.</span></span> <span data-ttu-id="628c6-106">I componenti di tipo [`TransformConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.TransformConstraint) collegati all'oggetto gioco possono essere presi in considerazione.</span><span class="sxs-lookup"><span data-stu-id="628c6-106">Components of type [`TransformConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.TransformConstraint) that are attached to the game object can be taken into consideration.</span></span>
<span data-ttu-id="628c6-107">Per impostazione predefinita, gestione vincoli raccoglie automaticamente tutti i [componenti dei vincoli](#transform-constraints) collegati all'oggetto gioco e li applica alle trasformazioni elaborate.</span><span class="sxs-lookup"><span data-stu-id="628c6-107">Per default, constraint manager will automatically collect all [constraint components](#transform-constraints) attached to the game object and apply them to processed transforms.</span></span>
<span data-ttu-id="628c6-108">Tuttavia, gli utenti possono scegliere di configurare manualmente l'elenco dei vincoli applicati e consentire l'applicazione solo di un subset di vincoli collegati.</span><span class="sxs-lookup"><span data-stu-id="628c6-108">However users can opt for configuring the list of applied constraints manually and allowing only a subset of attached constraints to be applied.</span></span>

<span data-ttu-id="628c6-109">Attualmente gli elementi UX MRTK seguenti supportano Gestione vincoli:</span><span class="sxs-lookup"><span data-stu-id="628c6-109">Currently the following MRTK UX elements are supporting constraint manager:</span></span>

- [<span data-ttu-id="628c6-110">Controllo dei limiti</span><span class="sxs-lookup"><span data-stu-id="628c6-110">Bounds control</span></span>](BoundsControl.md)
- [<span data-ttu-id="628c6-111">Manipolatore di oggetti</span><span class="sxs-lookup"><span data-stu-id="628c6-111">Object manipulator</span></span>](ObjectManipulator.md)

## <a name="inspector-properties-and-fields"></a><span data-ttu-id="628c6-112">Proprietà e campi di Inspector</span><span class="sxs-lookup"><span data-stu-id="628c6-112">Inspector properties and fields</span></span>

<span data-ttu-id="628c6-113">Gestione vincoli può essere utilizzato in due modalità:</span><span class="sxs-lookup"><span data-stu-id="628c6-113">Constraint manager can be operated in two modes:</span></span>

- <span data-ttu-id="628c6-114">Selezione vincolo automatico</span><span class="sxs-lookup"><span data-stu-id="628c6-114">Auto constraint selection</span></span>
- <span data-ttu-id="628c6-115">Selezione vincolo manuale</span><span class="sxs-lookup"><span data-stu-id="628c6-115">Manual constraint selection</span></span>

### <a name="auto-constraint-selection"></a><span data-ttu-id="628c6-116">Selezione vincolo automatico</span><span class="sxs-lookup"><span data-stu-id="628c6-116">Auto constraint selection</span></span>

<img src="../images/constraint-manager/AutoSelection.png" width="600" alt="Auto Selection Properties">

<span data-ttu-id="628c6-117">La modalità predefinita di gestione vincoli, selezione vincolo automatica, fornirà un elenco di tutti i componenti dei vincoli collegati, nonché i [pulsanti Vai a](#go-to-component) e [Aggiungi vincolo](#add-constraint-to-game-object).</span><span class="sxs-lookup"><span data-stu-id="628c6-117">The default mode of constraint manager, auto constraint selection, will provide a list of all attached constraint components as well as [go to buttons](#go-to-component) and an [add constraint button](#add-constraint-to-game-object).</span></span>

#### <a name="add-constraint-to-game-object"></a><span data-ttu-id="628c6-118">Aggiungi vincolo all'oggetto gioco</span><span class="sxs-lookup"><span data-stu-id="628c6-118">Add constraint to game object</span></span>

<span data-ttu-id="628c6-119">Questo pulsante consente di aggiungere un componente vincolo direttamente dal controllo Gestione vincoli.</span><span class="sxs-lookup"><span data-stu-id="628c6-119">This button allows a constraint component to be added directly from the constraint manager inspector.</span></span> <span data-ttu-id="628c6-120">Tutti i tipi di vincolo in un progetto devono essere visibili qui.</span><span class="sxs-lookup"><span data-stu-id="628c6-120">All constraint types in a project should be visible here.</span></span> <span data-ttu-id="628c6-121">Per altre informazioni, vedere [vincoli Transform](#transform-constraints) .</span><span class="sxs-lookup"><span data-stu-id="628c6-121">See [transform constraints](#transform-constraints) for more info.</span></span>

#### <a name="go-to-component"></a><span data-ttu-id="628c6-122">Vai al componente</span><span class="sxs-lookup"><span data-stu-id="628c6-122">Go to component</span></span>

<span data-ttu-id="628c6-123">Tutti i vincoli trovati nell'oggetto verranno elencati qui con un pulsante *Vai al componente* .</span><span class="sxs-lookup"><span data-stu-id="628c6-123">All constraints found on the object wil be listed here with a *Go to component* button.</span></span> <span data-ttu-id="628c6-124">Questo pulsante farà sì che il controllo scorra fino al componente del vincolo selezionato, in modo che possa essere configurato.</span><span class="sxs-lookup"><span data-stu-id="628c6-124">This button will cause the inspector to scroll to the selected constraint component so that it can be configured.</span></span>

### <a name="manual-constraint-selection"></a><span data-ttu-id="628c6-125">Selezione vincolo manuale</span><span class="sxs-lookup"><span data-stu-id="628c6-125">Manual constraint selection</span></span>

<img src="../images/constraint-manager/ManualSelection.png" width="600" alt="Manual Constraint selection">

<span data-ttu-id="628c6-126">Se Gestione vincoli è impostato sulla modalità manuale, solo i vincoli collegati nell'elenco di vincoli vengono elaborati e applicati alla trasformazione.</span><span class="sxs-lookup"><span data-stu-id="628c6-126">If constraint manager is set to manual mode, only constraints that are linked in the constraint list are processed and applied to the transform.</span></span> <span data-ttu-id="628c6-127">L'elenco visualizzato mostrerà solo i vincoli selezionati dall'utente, nonché i [pulsanti](#go-to-component) o le opzioni per rimuovere o aggiungere voci.</span><span class="sxs-lookup"><span data-stu-id="628c6-127">The list displayed will only show the user selected constraints as well as [go to buttons](#go-to-component) or options to remove or add entries.</span></span>
<span data-ttu-id="628c6-128">Quando si Abilita la modalità manuale per la prima volta, gestione vincoli compilerà l'elenco tutti i componenti disponibili come punto di partenza per la selezione dei componenti dei vincoli collegati.</span><span class="sxs-lookup"><span data-stu-id="628c6-128">When enabling manual mode for the first time, constraint manager will populate the list will all available components as a starting point for selecting attached constraint components.</span></span>

### <a name="remove-entry"></a><span data-ttu-id="628c6-129">Rimuovi voce</span><span class="sxs-lookup"><span data-stu-id="628c6-129">Remove entry</span></span>

<span data-ttu-id="628c6-130">Questa operazione consente di rimuovere la voce dall'elenco selezionato manualmente.</span><span class="sxs-lookup"><span data-stu-id="628c6-130">This removes the entry from the manually selected list.</span></span> <span data-ttu-id="628c6-131">Si noti che questa opzione non rimuoverà il componente vincolo dall'oggetto Game.</span><span class="sxs-lookup"><span data-stu-id="628c6-131">Note that this option will not remove the constraint component from the game object.</span></span> <span data-ttu-id="628c6-132">I componenti dei vincoli devono sempre essere rimossi manualmente per evitare di inavvertire eventuali altri componenti che fanno riferimento a questo componente.</span><span class="sxs-lookup"><span data-stu-id="628c6-132">Constraint components always need to be removed manually to ensure not accidentally breaking any other component referring to this component.</span></span>

### <a name="add-entry"></a><span data-ttu-id="628c6-133">Aggiungi voce</span><span class="sxs-lookup"><span data-stu-id="628c6-133">Add entry</span></span>

<span data-ttu-id="628c6-134">Aggiungi voce verrà aperto un elenco a discesa che Mostra tutti i componenti dei vincoli disponibili che non sono ancora presenti nell'elenco manuale.</span><span class="sxs-lookup"><span data-stu-id="628c6-134">Add entry will open a dropdown showing all available constraint components that are not in the manual list yet.</span></span> <span data-ttu-id="628c6-135">Facendo clic su una delle voci, il componente verrà aggiunto alla selezione dei vincoli manuale.</span><span class="sxs-lookup"><span data-stu-id="628c6-135">By clicking on any of the entries that component will be added to the manual constraint selection.</span></span>

### <a name="add-new-constraint"></a><span data-ttu-id="628c6-136">Aggiungi nuovo vincolo</span><span class="sxs-lookup"><span data-stu-id="628c6-136">Add new constraint</span></span>

<span data-ttu-id="628c6-137">Questa opzione consente di aggiungere un componente del tipo selezionato all'oggetto gioco e aggiungere il componente vincolo appena creato all'elenco di vincoli manuale.</span><span class="sxs-lookup"><span data-stu-id="628c6-137">This option will add a component of the selected type to the game object and add the newly created constraint component to the manual constraint list.</span></span>

## <a name="transform-constraints"></a><span data-ttu-id="628c6-138">Vincoli di trasformazione</span><span class="sxs-lookup"><span data-stu-id="628c6-138">Transform constraints</span></span>

<span data-ttu-id="628c6-139">I vincoli possono essere usati per limitare la manipolazione in qualche modo.</span><span class="sxs-lookup"><span data-stu-id="628c6-139">Constraints can be used to limit manipulation in some way.</span></span> <span data-ttu-id="628c6-140">Ad esempio, alcune applicazioni possono richiedere la rotazione, ma richiedono anche che l'oggetto rimanga verticale.</span><span class="sxs-lookup"><span data-stu-id="628c6-140">For example, some applications may require rotation, but also require that the object remain upright.</span></span> <span data-ttu-id="628c6-141">In questo caso, `RotationAxisConstraint` è possibile aggiungere un oggetto all'oggetto e usarlo per limitare la rotazione alla rotazione dell'asse y.</span><span class="sxs-lookup"><span data-stu-id="628c6-141">In this case, a `RotationAxisConstraint` can be added to the object and used to limit rotation to y-axis rotation.</span></span> <span data-ttu-id="628c6-142">MRTK fornisce una serie di vincoli, tutti descritti di seguito.</span><span class="sxs-lookup"><span data-stu-id="628c6-142">MRTK provides a number of constraints, all of which are described below.</span></span>

<span data-ttu-id="628c6-143">È anche possibile definire nuovi vincoli e usarli per creare un comportamento di manipolazione univoco che potrebbe essere necessario per alcune applicazioni.</span><span class="sxs-lookup"><span data-stu-id="628c6-143">It is also possible to define new constraints and use them to create unique manipulation behaviour that may be needed for some applications.</span></span> <span data-ttu-id="628c6-144">A tale scopo, creare uno script che erediti da [`TransformConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.TransformConstraint) e implementi la `ConstraintType` proprietà abstract e il `ApplyConstraint` metodo abstract.</span><span class="sxs-lookup"><span data-stu-id="628c6-144">To do this, create a script that inherits from [`TransformConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.TransformConstraint) and implement the abstract `ConstraintType` property and the abstract `ApplyConstraint` method.</span></span> <span data-ttu-id="628c6-145">Quando si aggiunge un nuovo vincolo all'oggetto, è necessario vincolare la manipolazione nel modo in cui è stato definito.</span><span class="sxs-lookup"><span data-stu-id="628c6-145">Upon adding a new constraint to the object, it should constrain manipulation in the way that was defined.</span></span> <span data-ttu-id="628c6-146">Questo nuovo vincolo dovrebbe inoltre essere visualizzato nell'elenco a discesa [selezione automatica](#auto-constraint-selection) gestione vincoli o [Aggiungi voce](#add-entry) in modalità manuale.</span><span class="sxs-lookup"><span data-stu-id="628c6-146">This new constraint should also show in the constraint manager [auto selection](#auto-constraint-selection) or [add entry](#add-entry) dropdown in manual mode.</span></span>

<span data-ttu-id="628c6-147">Tutti i vincoli forniti da MRTK condividono le proprietà seguenti:</span><span class="sxs-lookup"><span data-stu-id="628c6-147">All of the constraints provided by MRTK share the following properties:</span></span>

#### <a name="hand-type"></a><span data-ttu-id="628c6-148">Tipo di mano</span><span class="sxs-lookup"><span data-stu-id="628c6-148">Hand Type</span></span>

<span data-ttu-id="628c6-149">Specifica se il vincolo viene utilizzato per una sola mano, due o entrambi i tipi di manipolazione.</span><span class="sxs-lookup"><span data-stu-id="628c6-149">Specifies whether the constraint is used for one handed, two handed or both kinds of manipulation.</span></span> <span data-ttu-id="628c6-150">Poiché questa proprietà è un flag, è possibile selezionare entrambe le opzioni.</span><span class="sxs-lookup"><span data-stu-id="628c6-150">Because this property is a flag, both options can be selected.</span></span>

- <span data-ttu-id="628c6-151">*Una sola mano*: il vincolo verrà usato durante una manipolazione gestita, se selezionato.</span><span class="sxs-lookup"><span data-stu-id="628c6-151">*One handed*: Constraint will be used during one handed manipulation if selected.</span></span>
- <span data-ttu-id="628c6-152">*Due passate*: il vincolo verrà usato durante due manipolazioni gestite, se selezionato.</span><span class="sxs-lookup"><span data-stu-id="628c6-152">*Two handed*: Constraint will be used during two handed manipulation if selected.</span></span>

#### <a name="proximity-type"></a><span data-ttu-id="628c6-153">Tipo di prossimità</span><span class="sxs-lookup"><span data-stu-id="628c6-153">Proximity Type</span></span>

<span data-ttu-id="628c6-154">Specifica se il vincolo viene utilizzato per i tipi di manipolazione near, di gran lunga o entrambi.</span><span class="sxs-lookup"><span data-stu-id="628c6-154">Specifies whether the constraint is used for near, far or both kinds of manipulation.</span></span> <span data-ttu-id="628c6-155">Poiché questa proprietà è un flag, è possibile selezionare entrambe le opzioni.</span><span class="sxs-lookup"><span data-stu-id="628c6-155">Because this property is a flag, both options can be selected.</span></span>

- <span data-ttu-id="628c6-156">*Near*: il vincolo verrà usato in prossimità della manipolazione, se selezionato.</span><span class="sxs-lookup"><span data-stu-id="628c6-156">*Near*: Constraint will be used during near manipulation if selected.</span></span>
- <span data-ttu-id="628c6-157">*Lontano*: il vincolo verrà usato durante la manipolazione di gran lunga se selezionato.</span><span class="sxs-lookup"><span data-stu-id="628c6-157">*Far*: Constraint will be used during far manipulation if selected.</span></span>

### <a name="faceuserconstraint"></a><span data-ttu-id="628c6-158">FaceUserConstraint</span><span class="sxs-lookup"><span data-stu-id="628c6-158">FaceUserConstraint</span></span>

<img src="../Images/object-manipulator/MRTK_Constraint_FaceUser.gif" width="400" alt="face user constraint">

<span data-ttu-id="628c6-159">Quando questo vincolo è associato a un oggetto, la rotazione sarà limitata in modo che l'oggetto faccia sempre fronte all'utente.</span><span class="sxs-lookup"><span data-stu-id="628c6-159">When this constraint is attached to an object, rotation will be limited so that object will always face the user.</span></span> <span data-ttu-id="628c6-160">Questa operazione è utile per gli slate o i pannelli.</span><span class="sxs-lookup"><span data-stu-id="628c6-160">This is useful for slates or panels.</span></span> <span data-ttu-id="628c6-161">Le proprietà per `FaceUserConstraint` sono le seguenti:</span><span class="sxs-lookup"><span data-stu-id="628c6-161">The properties for `FaceUserConstraint` are as follows:</span></span>

#### <a name="face-away"></a><span data-ttu-id="628c6-162">Faccia fuori</span><span class="sxs-lookup"><span data-stu-id="628c6-162">Face away</span></span>

<span data-ttu-id="628c6-163">L'oggetto viene rivolto dall'utente se true.</span><span class="sxs-lookup"><span data-stu-id="628c6-163">Object faces away from the user if true.</span></span>

### <a name="fixeddistanceconstraint"></a><span data-ttu-id="628c6-164">FixedDistanceConstraint</span><span class="sxs-lookup"><span data-stu-id="628c6-164">FixedDistanceConstraint</span></span>

<img src="../Images/object-manipulator/MRTK_Constraint_FixedDistance.gif" width="400" alt="Face away">

<span data-ttu-id="628c6-165">Questo vincolo corregge la distanza tra l'oggetto modificato e un'altra trasformazione dell'oggetto all'avvio della manipolazione.</span><span class="sxs-lookup"><span data-stu-id="628c6-165">This constraint fixes the distance between the manipulated object and another object transform on manipulation start.</span></span> <span data-ttu-id="628c6-166">Questa operazione è utile per comportamenti come la correzione della distanza dall'oggetto modificato alla trasformazione Head.</span><span class="sxs-lookup"><span data-stu-id="628c6-166">This is useful for behaviour such as fixing the distance from the manipulated object to the head transform.</span></span> <span data-ttu-id="628c6-167">Le proprietà per `FixedDistanceConstraint` sono le seguenti:</span><span class="sxs-lookup"><span data-stu-id="628c6-167">The properties for `FixedDistanceConstraint` are as follows:</span></span>

#### <a name="constraint-transform"></a><span data-ttu-id="628c6-168">Trasformazione vincolo</span><span class="sxs-lookup"><span data-stu-id="628c6-168">Constraint transform</span></span>

<span data-ttu-id="628c6-169">Si tratta dell'altra trasformazione a cui l'oggetto modificato avrà una distanza fissa.</span><span class="sxs-lookup"><span data-stu-id="628c6-169">This is the other transform that the manipulated object will have a fixed distance to.</span></span> <span data-ttu-id="628c6-170">Il valore predefinito è la trasformazione della fotocamera.</span><span class="sxs-lookup"><span data-stu-id="628c6-170">Defaults to the camera transform.</span></span>

### <a name="fixedrotationtouserconstraint"></a><span data-ttu-id="628c6-171">FixedRotationToUserConstraint</span><span class="sxs-lookup"><span data-stu-id="628c6-171">FixedRotationToUserConstraint</span></span>

<img src="../Images/object-manipulator/MRTK_Constraint_FixedRotationToUser.gif" width="400" alt="Fixed Distance Constraint">

<span data-ttu-id="628c6-172">Questo vincolo corregge la rotazione relativa tra l'utente e l'oggetto modificato durante la manipolazione.</span><span class="sxs-lookup"><span data-stu-id="628c6-172">This constraint fixes the relative rotation between the user and the manipulated object while it is being manipulated.</span></span> <span data-ttu-id="628c6-173">Questa operazione è utile per gli slate o i pannelli, in quanto assicura che l'oggetto modificato mostri sempre lo stesso aspetto all'utente, così come è stato fatto all'inizio della manipolazione.</span><span class="sxs-lookup"><span data-stu-id="628c6-173">This is useful for slates or panels as it ensures that the manipulated object always shows the same face to the user as it did at the start of manipulation.</span></span> <span data-ttu-id="628c6-174">Non `FixedRotationToUserConstraint` dispone di proprietà univoche.</span><span class="sxs-lookup"><span data-stu-id="628c6-174">The `FixedRotationToUserConstraint` does not have any unique properties.</span></span>

### <a name="fixedrotationtoworldconstraint"></a><span data-ttu-id="628c6-175">FixedRotationToWorldConstraint</span><span class="sxs-lookup"><span data-stu-id="628c6-175">FixedRotationToWorldConstraint</span></span>

<img src="../Images/object-manipulator/MRTK_Constraint_FixedRotationToWorld.gif" width="400" alt="Fixed Rotation to user">

<span data-ttu-id="628c6-176">Questo vincolo corregge la rotazione globale dell'oggetto modificato durante la manipolazione.</span><span class="sxs-lookup"><span data-stu-id="628c6-176">This constraint fixes the global rotation of the manipulated object while it is being manipulated.</span></span> <span data-ttu-id="628c6-177">Questa operazione può essere utile nei casi in cui non è necessario che la rotazione venga ripartita dalla manipolazione.</span><span class="sxs-lookup"><span data-stu-id="628c6-177">This can be useful in cases where no rotation should be imparted by manipulation.</span></span> <span data-ttu-id="628c6-178">Non `FixedRotationToWorldConstraint` dispone di proprietà univoche:</span><span class="sxs-lookup"><span data-stu-id="628c6-178">The `FixedRotationToWorldConstraint` does not have any unique properties:</span></span>

### <a name="maintainapparentsizeconstraint"></a><span data-ttu-id="628c6-179">MaintainApparentSizeConstraint</span><span class="sxs-lookup"><span data-stu-id="628c6-179">MaintainApparentSizeConstraint</span></span>

<img src="../Images/object-manipulator/MRTK_Constraint_MaintainApparentSize.gif" width="400" alt="Apparent size constraint">

<span data-ttu-id="628c6-180">Quando questo vincolo è associato a un oggetto, indipendentemente dalla distanza dell'oggetto dall'utente, manterrà le stesse dimensioni apparenti per l'utente (ad esempio, prenderà la stessa proporzione del campo di visualizzazione dell'utente).</span><span class="sxs-lookup"><span data-stu-id="628c6-180">When this constraint is attached to an object, no matter how far the object is from the user, it will maintain the same apparent size to the user (i.e. it will take up the same proportion of the user's field of view).</span></span> <span data-ttu-id="628c6-181">Questa operazione può essere utilizzata per garantire che uno Slate o un pannello di testo rimanga leggibile durante la manipolazione.</span><span class="sxs-lookup"><span data-stu-id="628c6-181">This can be used to ensure that a slate or text panel remains readable while manipulating.</span></span> <span data-ttu-id="628c6-182">Non `MaintainApparentSizeConstraint` dispone di proprietà univoche:</span><span class="sxs-lookup"><span data-stu-id="628c6-182">The `MaintainApparentSizeConstraint` does not have any unique properties:</span></span>

### <a name="moveaxisconstraint"></a><span data-ttu-id="628c6-183">MoveAxisConstraint</span><span class="sxs-lookup"><span data-stu-id="628c6-183">MoveAxisConstraint</span></span>

<img src="../Images/object-manipulator/MRTK_Constraint_MoveAxis.gif" width="400" alt="Move Axis Constraint">

<span data-ttu-id="628c6-184">Questo vincolo può essere usato per correggere gli assi che possono essere spostati in un oggetto modificato.</span><span class="sxs-lookup"><span data-stu-id="628c6-184">This constraint can be used to fix along which axes a manipulated object can be moved.</span></span> <span data-ttu-id="628c6-185">Questa operazione può essere utile per la modifica degli oggetti sulla superficie di un piano o lungo una linea.</span><span class="sxs-lookup"><span data-stu-id="628c6-185">This can be useful for manipulating objects over the surface of a plane, or along a line.</span></span> <span data-ttu-id="628c6-186">Le proprietà per `MoveAxisConstraint` sono le seguenti:</span><span class="sxs-lookup"><span data-stu-id="628c6-186">The properties for `MoveAxisConstraint` are as follows:</span></span>

#### <a name="constraint-on-movement"></a><span data-ttu-id="628c6-187">Vincolo durante lo spostamento</span><span class="sxs-lookup"><span data-stu-id="628c6-187">Constraint on movement</span></span>

<span data-ttu-id="628c6-188">Specifica gli assi su cui impedire lo spostamento.</span><span class="sxs-lookup"><span data-stu-id="628c6-188">Specifies which axes to prevent movement on.</span></span> <span data-ttu-id="628c6-189">Per impostazione predefinita, questi assi saranno globali anziché locali, ma è possibile modificarli sotto.</span><span class="sxs-lookup"><span data-stu-id="628c6-189">By default, these axes will be global rather than local, but this can be changed below.</span></span> <span data-ttu-id="628c6-190">Poiché questa proprietà è un flag, è possibile selezionare qualsiasi numero di opzioni.</span><span class="sxs-lookup"><span data-stu-id="628c6-190">Because this property is a flag, any number of options can be selected.</span></span>

- <span data-ttu-id="628c6-191">*Asse x*: se selezionato, lo spostamento lungo l'asse x è vincolato.</span><span class="sxs-lookup"><span data-stu-id="628c6-191">*X Axis*: Movement along the x-axis is constrained if selected.</span></span>
- <span data-ttu-id="628c6-192">*Asse y*: se selezionato, lo spostamento lungo l'asse y è vincolato.</span><span class="sxs-lookup"><span data-stu-id="628c6-192">*Y Axis*: Movement along the y-axis is constrained if selected.</span></span>
- <span data-ttu-id="628c6-193">*Asse z*: lo spostamento lungo l'asse z è vincolato se selezionato.</span><span class="sxs-lookup"><span data-stu-id="628c6-193">*Z Axis*: Movement along the z-axis is constrained if selected.</span></span>

#### <a name="use-local-space-for-constraint"></a><span data-ttu-id="628c6-194">Usa spazio locale per il vincolo</span><span class="sxs-lookup"><span data-stu-id="628c6-194">Use local space for constraint</span></span>

<span data-ttu-id="628c6-195">Vincola gli assi di trasformazione locali dell'oggetto modificato se true.</span><span class="sxs-lookup"><span data-stu-id="628c6-195">Will constrain relative the manipulated object's local transform axes if true.</span></span> <span data-ttu-id="628c6-196">False per impostazione predefinita.</span><span class="sxs-lookup"><span data-stu-id="628c6-196">False by default.</span></span>

### <a name="rotationaxisconstraint"></a><span data-ttu-id="628c6-197">RotationAxisConstraint</span><span class="sxs-lookup"><span data-stu-id="628c6-197">RotationAxisConstraint</span></span>

<img src="../Images/object-manipulator/MRTK_Constraint_RotationAxis.gif" width="400" alt="Rotation Axis Constraint">

<span data-ttu-id="628c6-198">Questo vincolo può essere usato per correggere gli assi che possono essere ruotati da un oggetto modificato.</span><span class="sxs-lookup"><span data-stu-id="628c6-198">This constraint can be used to fix about which axes a manipulated object can be rotated.</span></span> <span data-ttu-id="628c6-199">Questa operazione può essere utile per mantenere un oggetto manipolato verticalmente, ma che consente comunque di ruotare gli assi y, ad esempio.</span><span class="sxs-lookup"><span data-stu-id="628c6-199">This can be useful for keeping a manipulated object upright, but still allowing y-axis rotations, for example.</span></span> <span data-ttu-id="628c6-200">Le proprietà per `RotationAxisConstraint` sono le seguenti:</span><span class="sxs-lookup"><span data-stu-id="628c6-200">The properties for `RotationAxisConstraint` are as follows:</span></span>

#### <a name="constraint-on-rotation"></a><span data-ttu-id="628c6-201">Vincolo alla rotazione</span><span class="sxs-lookup"><span data-stu-id="628c6-201">Constraint on rotation</span></span>

<span data-ttu-id="628c6-202">Specifica gli assi per i quali impedire la rotazione.</span><span class="sxs-lookup"><span data-stu-id="628c6-202">Specifies which axes to prevent rotation about.</span></span> <span data-ttu-id="628c6-203">Per impostazione predefinita, questi assi saranno globali anziché locali, ma è possibile modificarli sotto.</span><span class="sxs-lookup"><span data-stu-id="628c6-203">By default, these axes will be global rather than local, but this can be changed below.</span></span> <span data-ttu-id="628c6-204">Poiché questa proprietà è un flag, è possibile selezionare qualsiasi numero di opzioni.</span><span class="sxs-lookup"><span data-stu-id="628c6-204">Because this property is a flag, any number of options can be selected.</span></span>

- <span data-ttu-id="628c6-205">*Asse y*: la rotazione sull'asse y è vincolata se selezionata.</span><span class="sxs-lookup"><span data-stu-id="628c6-205">*Y Axis*: Rotation about the y-axis is constrained if selected.</span></span>
- <span data-ttu-id="628c6-206">*Asse z*: la rotazione sull'asse z è vincolata se selezionata.</span><span class="sxs-lookup"><span data-stu-id="628c6-206">*Z Axis*: Rotation about the z-axis is constrained if selected.</span></span>
- <span data-ttu-id="628c6-207">*Asse x*: la rotazione sull'asse x è vincolata se selezionata.</span><span class="sxs-lookup"><span data-stu-id="628c6-207">*X Axis*: Rotation about the x-axis is constrained if selected.</span></span>

#### <a name="use-local-space-for-constraint"></a><span data-ttu-id="628c6-208">Usa spazio locale per il vincolo</span><span class="sxs-lookup"><span data-stu-id="628c6-208">Use local space for constraint</span></span>

<span data-ttu-id="628c6-209">Vincola gli assi di trasformazione locali dell'oggetto modificato se true.</span><span class="sxs-lookup"><span data-stu-id="628c6-209">Will constrain relative the manipulated object's local transform axes if true.</span></span> <span data-ttu-id="628c6-210">False per impostazione predefinita.</span><span class="sxs-lookup"><span data-stu-id="628c6-210">False by default.</span></span>

### <a name="minmaxscaleconstraint"></a><span data-ttu-id="628c6-211">MinMaxScaleConstraint</span><span class="sxs-lookup"><span data-stu-id="628c6-211">MinMaxScaleConstraint</span></span>

<img src="../Images/object-manipulator/MRTK_Constraint_MinMaxScale.gif" width="400" alt="MinMax Scale constraint">

<span data-ttu-id="628c6-212">Questo vincolo consente di impostare i valori minimo e massimo per la scala dell'oggetto modificato.</span><span class="sxs-lookup"><span data-stu-id="628c6-212">This constraint allows minimum and maximum values to be set for the scale of the manipulated object.</span></span> <span data-ttu-id="628c6-213">Questa operazione è utile per impedire agli utenti di ridimensionare un oggetto troppo piccolo o troppo grande.</span><span class="sxs-lookup"><span data-stu-id="628c6-213">This is useful for preventing users from scaling an object too small or too large.</span></span> <span data-ttu-id="628c6-214">Le proprietà per `MinMaxScaleConstraint` sono le seguenti:</span><span class="sxs-lookup"><span data-stu-id="628c6-214">The properties for `MinMaxScaleConstraint` are as follows:</span></span>

#### <a name="scale-minimum"></a><span data-ttu-id="628c6-215">Dimensioni minime</span><span class="sxs-lookup"><span data-stu-id="628c6-215">Scale minimum</span></span>

<span data-ttu-id="628c6-216">Valore di scala minimo durante la manipolazione.</span><span class="sxs-lookup"><span data-stu-id="628c6-216">The minimum scale value during manipulation.</span></span>

#### <a name="scale-maximum"></a><span data-ttu-id="628c6-217">Scalabilità massima</span><span class="sxs-lookup"><span data-stu-id="628c6-217">Scale maximum</span></span>

<span data-ttu-id="628c6-218">Valore di scala massimo durante la manipolazione.</span><span class="sxs-lookup"><span data-stu-id="628c6-218">The maximum scale value during manipulation.</span></span>

#### <a name="relative-to-initial-state"></a><span data-ttu-id="628c6-219">Relativo allo stato iniziale</span><span class="sxs-lookup"><span data-stu-id="628c6-219">Relative to initial state</span></span>

<span data-ttu-id="628c6-220">Se true, i valori precedenti verranno interpretati come relativi alla scala iniziale degli oggetti.</span><span class="sxs-lookup"><span data-stu-id="628c6-220">If true, the values above will be interpreted as relative to the objects initial scale.</span></span> <span data-ttu-id="628c6-221">In caso contrario, verranno interpretati come valori di scala assoluti.</span><span class="sxs-lookup"><span data-stu-id="628c6-221">Otherwise they will be interpreted as absolute scale values.</span></span>

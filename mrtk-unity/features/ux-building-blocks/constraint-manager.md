---
title: Gestione vincoli
description: Panoramica di Gestione vincoli in MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: 7036bb552952a0e45a8ba465d769a8952e48bc36
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177557"
---
# <a name="constraint-manager"></a><span data-ttu-id="6fc65-104">Gestione vincoli</span><span class="sxs-lookup"><span data-stu-id="6fc65-104">Constraint manager</span></span>

<span data-ttu-id="6fc65-105">Gestione vincoli consente di applicare un set di componenti di vincolo a una trasformazione.</span><span class="sxs-lookup"><span data-stu-id="6fc65-105">The constraint manager allows to apply a set of constraint components to a transform.</span></span> <span data-ttu-id="6fc65-106">È possibile prendere in considerazione i componenti di tipo associati [`TransformConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.TransformConstraint) all'oggetto di gioco.</span><span class="sxs-lookup"><span data-stu-id="6fc65-106">Components of type [`TransformConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.TransformConstraint) that are attached to the game object can be taken into consideration.</span></span>
<span data-ttu-id="6fc65-107">Per impostazione predefinita, Gestione vincoli raccoglierà automaticamente tutti [i componenti](#transform-constraints) dei vincoli collegati all'oggetto gioco e li applicherà alle trasformazioni elaborate.</span><span class="sxs-lookup"><span data-stu-id="6fc65-107">Per default, constraint manager will automatically collect all [constraint components](#transform-constraints) attached to the game object and apply them to processed transforms.</span></span>
<span data-ttu-id="6fc65-108">Tuttavia, gli utenti possono scegliere di configurare manualmente l'elenco di vincoli applicati e di applicare solo un subset di vincoli associati.</span><span class="sxs-lookup"><span data-stu-id="6fc65-108">However users can opt for configuring the list of applied constraints manually and allowing only a subset of attached constraints to be applied.</span></span>

<span data-ttu-id="6fc65-109">Attualmente gli elementi dell'esperienza utente MRTK seguenti supportano la gestione vincoli:</span><span class="sxs-lookup"><span data-stu-id="6fc65-109">Currently the following MRTK UX elements are supporting constraint manager:</span></span>

- [<span data-ttu-id="6fc65-110">Controllo Limiti</span><span class="sxs-lookup"><span data-stu-id="6fc65-110">Bounds control</span></span>](bounds-control.md)
- [<span data-ttu-id="6fc65-111">Manipolatore di oggetti</span><span class="sxs-lookup"><span data-stu-id="6fc65-111">Object manipulator</span></span>](object-manipulator.md)

## <a name="inspector-properties-and-fields"></a><span data-ttu-id="6fc65-112">Proprietà e campi del controllo</span><span class="sxs-lookup"><span data-stu-id="6fc65-112">Inspector properties and fields</span></span>

<span data-ttu-id="6fc65-113">Gestione vincoli può essere gestito in due modalità:</span><span class="sxs-lookup"><span data-stu-id="6fc65-113">Constraint manager can be operated in two modes:</span></span>

- <span data-ttu-id="6fc65-114">Selezione automatica dei vincoli</span><span class="sxs-lookup"><span data-stu-id="6fc65-114">Auto constraint selection</span></span>
- <span data-ttu-id="6fc65-115">Selezione manuale dei vincoli</span><span class="sxs-lookup"><span data-stu-id="6fc65-115">Manual constraint selection</span></span>

### <a name="auto-constraint-selection"></a><span data-ttu-id="6fc65-116">Selezione automatica dei vincoli</span><span class="sxs-lookup"><span data-stu-id="6fc65-116">Auto constraint selection</span></span>

<img src="../images/constraint-manager/AutoSelection.png" width="600" alt="Auto Selection">

<span data-ttu-id="6fc65-117">La modalità predefinita di gestione vincoli, la selezione automatica dei [vincoli,](#add-constraint-to-game-object) [](#go-to-component) fornirà un elenco di tutti i componenti del vincolo associato, oltre a passare ai pulsanti e un pulsante Aggiungi vincolo .</span><span class="sxs-lookup"><span data-stu-id="6fc65-117">The default mode of constraint manager, auto constraint selection, will provide a list of all attached constraint components as well as [go to buttons](#go-to-component) and an [add constraint button](#add-constraint-to-game-object).</span></span>

#### <a name="add-constraint-to-game-object"></a><span data-ttu-id="6fc65-118">Aggiungere un vincolo all'oggetto gioco</span><span class="sxs-lookup"><span data-stu-id="6fc65-118">Add constraint to game object</span></span>

<span data-ttu-id="6fc65-119">Questo pulsante consente di aggiungere un componente vincolo direttamente dal controllo di Gestione vincoli.</span><span class="sxs-lookup"><span data-stu-id="6fc65-119">This button allows a constraint component to be added directly from the constraint manager inspector.</span></span> <span data-ttu-id="6fc65-120">Tutti i tipi di vincolo in un progetto devono essere visibili qui.</span><span class="sxs-lookup"><span data-stu-id="6fc65-120">All constraint types in a project should be visible here.</span></span> <span data-ttu-id="6fc65-121">Per [altre informazioni, vedere](#transform-constraints) Vincoli di trasformazione.</span><span class="sxs-lookup"><span data-stu-id="6fc65-121">See [transform constraints](#transform-constraints) for more info.</span></span>

#### <a name="go-to-component"></a><span data-ttu-id="6fc65-122">Vai al componente</span><span class="sxs-lookup"><span data-stu-id="6fc65-122">Go to component</span></span>

<span data-ttu-id="6fc65-123">Tutti i vincoli trovati nell'oggetto verranno elencati qui con *un pulsante Vai al componente.*</span><span class="sxs-lookup"><span data-stu-id="6fc65-123">All constraints found on the object wil be listed here with a *Go to component* button.</span></span> <span data-ttu-id="6fc65-124">Questo pulsante farà scorrere il controllo fino al componente vincolo selezionato in modo che possa essere configurato.</span><span class="sxs-lookup"><span data-stu-id="6fc65-124">This button will cause the inspector to scroll to the selected constraint component so that it can be configured.</span></span>

### <a name="manual-constraint-selection"></a><span data-ttu-id="6fc65-125">Selezione manuale dei vincoli</span><span class="sxs-lookup"><span data-stu-id="6fc65-125">Manual constraint selection</span></span>

<img src="../images/constraint-manager/ManualSelection.png" width="600" alt="Manual Selection">

<span data-ttu-id="6fc65-126">Se Gestione vincoli è impostato sulla modalità manuale, solo i vincoli collegati nell'elenco di vincoli vengono elaborati e applicati alla trasformazione.</span><span class="sxs-lookup"><span data-stu-id="6fc65-126">If constraint manager is set to manual mode, only constraints that are linked in the constraint list are processed and applied to the transform.</span></span> <span data-ttu-id="6fc65-127">L'elenco visualizzato mostrerà solo i vincoli selezionati dall'utente, nonché [i](#go-to-component) pulsanti o le opzioni per rimuovere o aggiungere voci.</span><span class="sxs-lookup"><span data-stu-id="6fc65-127">The list displayed will only show the user selected constraints as well as [go to buttons](#go-to-component) or options to remove or add entries.</span></span>
<span data-ttu-id="6fc65-128">Quando si abilita la modalità manuale per la prima volta, Gestione vincoli popola l'elenco per tutti i componenti disponibili come punto di partenza per la selezione dei componenti dei vincoli associati.</span><span class="sxs-lookup"><span data-stu-id="6fc65-128">When enabling manual mode for the first time, constraint manager will populate the list will all available components as a starting point for selecting attached constraint components.</span></span>

### <a name="remove-entry"></a><span data-ttu-id="6fc65-129">Rimuovi voce</span><span class="sxs-lookup"><span data-stu-id="6fc65-129">Remove entry</span></span>

<span data-ttu-id="6fc65-130">Questa operazione rimuove la voce dall'elenco selezionato manualmente.</span><span class="sxs-lookup"><span data-stu-id="6fc65-130">This removes the entry from the manually selected list.</span></span> <span data-ttu-id="6fc65-131">Si noti che questa opzione non rimuove il componente vincolo dall'oggetto del gioco.</span><span class="sxs-lookup"><span data-stu-id="6fc65-131">Note that this option will not remove the constraint component from the game object.</span></span> <span data-ttu-id="6fc65-132">I componenti di vincolo devono sempre essere rimossi manualmente per garantire che non vengano accidentalmente infrante eventuali altri componenti che fanno riferimento a questo componente.</span><span class="sxs-lookup"><span data-stu-id="6fc65-132">Constraint components always need to be removed manually to ensure not accidentally breaking any other component referring to this component.</span></span>

### <a name="add-entry"></a><span data-ttu-id="6fc65-133">Aggiungere una voce</span><span class="sxs-lookup"><span data-stu-id="6fc65-133">Add entry</span></span>

<span data-ttu-id="6fc65-134">Aggiungi voce aprirà un elenco a discesa che mostra tutti i componenti dei vincoli disponibili che non sono ancora presenti nell'elenco manuale.</span><span class="sxs-lookup"><span data-stu-id="6fc65-134">Add entry will open a dropdown showing all available constraint components that are not in the manual list yet.</span></span> <span data-ttu-id="6fc65-135">Facendo clic su una delle voci che il componente verrà aggiunto alla selezione manuale del vincolo.</span><span class="sxs-lookup"><span data-stu-id="6fc65-135">By clicking on any of the entries that component will be added to the manual constraint selection.</span></span>

### <a name="add-new-constraint"></a><span data-ttu-id="6fc65-136">Aggiungere un nuovo vincolo</span><span class="sxs-lookup"><span data-stu-id="6fc65-136">Add new constraint</span></span>

<span data-ttu-id="6fc65-137">Questa opzione aggiungerà un componente del tipo selezionato all'oggetto gioco e aggiungerà il componente vincolo appena creato all'elenco di vincoli manuale.</span><span class="sxs-lookup"><span data-stu-id="6fc65-137">This option will add a component of the selected type to the game object and add the newly created constraint component to the manual constraint list.</span></span>

## <a name="transform-constraints"></a><span data-ttu-id="6fc65-138">Vincoli di trasformazione</span><span class="sxs-lookup"><span data-stu-id="6fc65-138">Transform constraints</span></span>

<span data-ttu-id="6fc65-139">I vincoli possono essere usati per limitare la manipolazione in qualche modo.</span><span class="sxs-lookup"><span data-stu-id="6fc65-139">Constraints can be used to limit manipulation in some way.</span></span> <span data-ttu-id="6fc65-140">Ad esempio, alcune applicazioni possono richiedere la rotazione, ma anche che l'oggetto rimanga in posizione verticale.</span><span class="sxs-lookup"><span data-stu-id="6fc65-140">For example, some applications may require rotation, but also require that the object remain upright.</span></span> <span data-ttu-id="6fc65-141">In questo caso, è possibile aggiungere un oggetto all'oggetto e usare per limitare la `RotationAxisConstraint` rotazione alla rotazione dell'asse y.</span><span class="sxs-lookup"><span data-stu-id="6fc65-141">In this case, a `RotationAxisConstraint` can be added to the object and used to limit rotation to y-axis rotation.</span></span> <span data-ttu-id="6fc65-142">MRTK fornisce una serie di vincoli, tutti descritti di seguito.</span><span class="sxs-lookup"><span data-stu-id="6fc65-142">MRTK provides a number of constraints, all of which are described below.</span></span>

<span data-ttu-id="6fc65-143">È anche possibile definire nuovi vincoli e usarli per creare un comportamento di manipolazione univoco che potrebbe essere necessario per alcune applicazioni.</span><span class="sxs-lookup"><span data-stu-id="6fc65-143">It is also possible to define new constraints and use them to create unique manipulation behaviour that may be needed for some applications.</span></span> <span data-ttu-id="6fc65-144">A tale scopo, creare uno script che eredita da e [`TransformConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.TransformConstraint) implementare la proprietà astratta `ConstraintType` e il metodo `ApplyConstraint` astratto.</span><span class="sxs-lookup"><span data-stu-id="6fc65-144">To do this, create a script that inherits from [`TransformConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.TransformConstraint) and implement the abstract `ConstraintType` property and the abstract `ApplyConstraint` method.</span></span> <span data-ttu-id="6fc65-145">Quando si aggiunge un nuovo vincolo all'oggetto, deve vincolare la manipolazione nel modo definito.</span><span class="sxs-lookup"><span data-stu-id="6fc65-145">Upon adding a new constraint to the object, it should constrain manipulation in the way that was defined.</span></span> <span data-ttu-id="6fc65-146">Questo nuovo vincolo deve essere visualizzato anche nella selezione automatica di [Gestione](#auto-constraint-selection) vincoli o nell'elenco [a](#add-entry) discesa Aggiungi voce in modalità manuale.</span><span class="sxs-lookup"><span data-stu-id="6fc65-146">This new constraint should also show in the constraint manager [auto selection](#auto-constraint-selection) or [add entry](#add-entry) dropdown in manual mode.</span></span>

<span data-ttu-id="6fc65-147">Tutti i vincoli forniti da MRTK condividono le proprietà seguenti:</span><span class="sxs-lookup"><span data-stu-id="6fc65-147">All of the constraints provided by MRTK share the following properties:</span></span>

#### <a name="hand-type"></a><span data-ttu-id="6fc65-148">Tipo di mano</span><span class="sxs-lookup"><span data-stu-id="6fc65-148">Hand Type</span></span>

<span data-ttu-id="6fc65-149">Specifica se il vincolo viene usato per una mano, due mani o per entrambi i tipi di manipolazione.</span><span class="sxs-lookup"><span data-stu-id="6fc65-149">Specifies whether the constraint is used for one handed, two handed or both kinds of manipulation.</span></span> <span data-ttu-id="6fc65-150">Poiché questa proprietà è un flag, è possibile selezionare entrambe le opzioni.</span><span class="sxs-lookup"><span data-stu-id="6fc65-150">Because this property is a flag, both options can be selected.</span></span>

- <span data-ttu-id="6fc65-151">*Una mano:* il vincolo verrà usato durante la manipolazione con una mano, se selezionato.</span><span class="sxs-lookup"><span data-stu-id="6fc65-151">*One handed*: Constraint will be used during one handed manipulation if selected.</span></span>
- <span data-ttu-id="6fc65-152">*A due mani:* il vincolo verrà usato durante la manipolazione a due mani, se selezionato.</span><span class="sxs-lookup"><span data-stu-id="6fc65-152">*Two handed*: Constraint will be used during two handed manipulation if selected.</span></span>

#### <a name="proximity-type"></a><span data-ttu-id="6fc65-153">Tipo di prossimità</span><span class="sxs-lookup"><span data-stu-id="6fc65-153">Proximity Type</span></span>

<span data-ttu-id="6fc65-154">Specifica se il vincolo viene usato per la manipolazione vicina, lontana o per entrambi i tipi.</span><span class="sxs-lookup"><span data-stu-id="6fc65-154">Specifies whether the constraint is used for near, far or both kinds of manipulation.</span></span> <span data-ttu-id="6fc65-155">Poiché questa proprietà è un flag, è possibile selezionare entrambe le opzioni.</span><span class="sxs-lookup"><span data-stu-id="6fc65-155">Because this property is a flag, both options can be selected.</span></span>

- <span data-ttu-id="6fc65-156">*Vicino:* il vincolo verrà usato durante la manipolazione vicina, se selezionato.</span><span class="sxs-lookup"><span data-stu-id="6fc65-156">*Near*: Constraint will be used during near manipulation if selected.</span></span>
- <span data-ttu-id="6fc65-157">*Far:* il vincolo verrà usato durante la manipolazione da lontano, se selezionato.</span><span class="sxs-lookup"><span data-stu-id="6fc65-157">*Far*: Constraint will be used during far manipulation if selected.</span></span>

### <a name="faceuserconstraint"></a><span data-ttu-id="6fc65-158">FaceUserConstraint</span><span class="sxs-lookup"><span data-stu-id="6fc65-158">FaceUserConstraint</span></span>

<img src="../images/object-manipulator/MRTK_Constraint_FaceUser.gif" width="400" alt="Constraint Face User">

<span data-ttu-id="6fc65-159">Quando questo vincolo è associato a un oggetto, la rotazione sarà limitata in modo che l'oggetto si faccia sempre fronte all'utente.</span><span class="sxs-lookup"><span data-stu-id="6fc65-159">When this constraint is attached to an object, rotation will be limited so that object will always face the user.</span></span> <span data-ttu-id="6fc65-160">Ciò è utile per gli ardesia o i pannelli.</span><span class="sxs-lookup"><span data-stu-id="6fc65-160">This is useful for slates or panels.</span></span> <span data-ttu-id="6fc65-161">Le proprietà per `FaceUserConstraint` sono le seguenti:</span><span class="sxs-lookup"><span data-stu-id="6fc65-161">The properties for `FaceUserConstraint` are as follows:</span></span>

#### <a name="face-away"></a><span data-ttu-id="6fc65-162">Viso lontano</span><span class="sxs-lookup"><span data-stu-id="6fc65-162">Face away</span></span>

<span data-ttu-id="6fc65-163">L'oggetto si allontana dall'utente se è true.</span><span class="sxs-lookup"><span data-stu-id="6fc65-163">Object faces away from the user if true.</span></span>

### <a name="fixeddistanceconstraint"></a><span data-ttu-id="6fc65-164">FixedDistanceConstraint</span><span class="sxs-lookup"><span data-stu-id="6fc65-164">FixedDistanceConstraint</span></span>

<img src="../images/object-manipulator/MRTK_Constraint_FixedDistance.gif" width="400" alt="Constraint Fixed distances">

<span data-ttu-id="6fc65-165">Questo vincolo corregge la distanza tra l'oggetto modificato e un'altra trasformazione di oggetto all'inizio della manipolazione.</span><span class="sxs-lookup"><span data-stu-id="6fc65-165">This constraint fixes the distance between the manipulated object and another object transform on manipulation start.</span></span> <span data-ttu-id="6fc65-166">Ciò è utile per comportamenti come la correzione della distanza tra l'oggetto modificato e la trasformazione della testa.</span><span class="sxs-lookup"><span data-stu-id="6fc65-166">This is useful for behaviour such as fixing the distance from the manipulated object to the head transform.</span></span> <span data-ttu-id="6fc65-167">Le proprietà per `FixedDistanceConstraint` sono le seguenti:</span><span class="sxs-lookup"><span data-stu-id="6fc65-167">The properties for `FixedDistanceConstraint` are as follows:</span></span>

#### <a name="constraint-transform"></a><span data-ttu-id="6fc65-168">Trasformazione dei vincoli</span><span class="sxs-lookup"><span data-stu-id="6fc65-168">Constraint transform</span></span>

<span data-ttu-id="6fc65-169">Questa è l'altra trasformazione a cui l'oggetto modificato avrà una distanza fissa.</span><span class="sxs-lookup"><span data-stu-id="6fc65-169">This is the other transform that the manipulated object will have a fixed distance to.</span></span> <span data-ttu-id="6fc65-170">Il valore predefinito è la trasformazione della fotocamera.</span><span class="sxs-lookup"><span data-stu-id="6fc65-170">Defaults to the camera transform.</span></span>

### <a name="fixedrotationtouserconstraint"></a><span data-ttu-id="6fc65-171">FixedRotationToUserConstraint</span><span class="sxs-lookup"><span data-stu-id="6fc65-171">FixedRotationToUserConstraint</span></span>

<img src="../images/object-manipulator/MRTK_Constraint_FixedRotationToUser.gif" width="400" alt="Fixed Rotation">

<span data-ttu-id="6fc65-172">Questo vincolo corregge la rotazione relativa tra l'utente e l'oggetto modificato durante la modifica.</span><span class="sxs-lookup"><span data-stu-id="6fc65-172">This constraint fixes the relative rotation between the user and the manipulated object while it is being manipulated.</span></span> <span data-ttu-id="6fc65-173">Ciò è utile per gli ardeggiamenti o i pannelli in quanto garantisce che l'oggetto modificato abbia sempre lo stesso viso dell'utente all'inizio della manipolazione.</span><span class="sxs-lookup"><span data-stu-id="6fc65-173">This is useful for slates or panels as it ensures that the manipulated object always shows the same face to the user as it did at the start of manipulation.</span></span> <span data-ttu-id="6fc65-174">`FixedRotationToUserConstraint`l'oggetto non ha proprietà univoche.</span><span class="sxs-lookup"><span data-stu-id="6fc65-174">The `FixedRotationToUserConstraint` does not have any unique properties.</span></span>

### <a name="fixedrotationtoworldconstraint"></a><span data-ttu-id="6fc65-175">FixedRotationToWorldConstraint</span><span class="sxs-lookup"><span data-stu-id="6fc65-175">FixedRotationToWorldConstraint</span></span>

<img src="../images/object-manipulator/MRTK_Constraint_FixedRotationToWorld.gif" width="400" alt="Fixed rotation to the world">

<span data-ttu-id="6fc65-176">Questo vincolo corregge la rotazione globale dell'oggetto modificato durante la modifica.</span><span class="sxs-lookup"><span data-stu-id="6fc65-176">This constraint fixes the global rotation of the manipulated object while it is being manipulated.</span></span> <span data-ttu-id="6fc65-177">Questa operazione può essere utile nei casi in cui nessuna rotazione deve essere disodepolata dalla manipolazione.</span><span class="sxs-lookup"><span data-stu-id="6fc65-177">This can be useful in cases where no rotation should be imparted by manipulation.</span></span> <span data-ttu-id="6fc65-178">`FixedRotationToWorldConstraint`l'oggetto non ha proprietà univoche:</span><span class="sxs-lookup"><span data-stu-id="6fc65-178">The `FixedRotationToWorldConstraint` does not have any unique properties:</span></span>

### <a name="maintainapparentsizeconstraint"></a><span data-ttu-id="6fc65-179">MaintainApparentSizeConstraint</span><span class="sxs-lookup"><span data-stu-id="6fc65-179">MaintainApparentSizeConstraint</span></span>

<img src="../images/object-manipulator/MRTK_Constraint_MaintainApparentSize.gif" width="400" alt="Maintain Apparent size">

<span data-ttu-id="6fc65-180">Quando questo vincolo è associato a un oggetto, indipendentemente dalla distanza dell'oggetto dall'utente, manterrà le stesse dimensioni apparenti per l'utente(ad esempio, l'oggetto avrà la stessa proporzione del campo di visualizzazione dell'utente).</span><span class="sxs-lookup"><span data-stu-id="6fc65-180">When this constraint is attached to an object, no matter how far the object is from the user, it will maintain the same apparent size to the user (i.e. it will take up the same proportion of the user's field of view).</span></span> <span data-ttu-id="6fc65-181">Può essere usato per garantire che uno slate o un pannello di testo rimanga leggibile durante la modifica.</span><span class="sxs-lookup"><span data-stu-id="6fc65-181">This can be used to ensure that a slate or text panel remains readable while manipulating.</span></span> <span data-ttu-id="6fc65-182">`MaintainApparentSizeConstraint`l'oggetto non ha proprietà univoche:</span><span class="sxs-lookup"><span data-stu-id="6fc65-182">The `MaintainApparentSizeConstraint` does not have any unique properties:</span></span>

### <a name="moveaxisconstraint"></a><span data-ttu-id="6fc65-183">MoveAxisConstraint</span><span class="sxs-lookup"><span data-stu-id="6fc65-183">MoveAxisConstraint</span></span>

<img src="../images/object-manipulator/MRTK_Constraint_MoveAxis.gif" width="400" alt="Constraint Move Axis">

<span data-ttu-id="6fc65-184">Questo vincolo può essere usato per correggere gli assi lungo i quali è possibile spostare un oggetto modificato.</span><span class="sxs-lookup"><span data-stu-id="6fc65-184">This constraint can be used to fix along which axes a manipulated object can be moved.</span></span> <span data-ttu-id="6fc65-185">Può essere utile per modificare gli oggetti sulla superficie di un piano o lungo una linea.</span><span class="sxs-lookup"><span data-stu-id="6fc65-185">This can be useful for manipulating objects over the surface of a plane, or along a line.</span></span> <span data-ttu-id="6fc65-186">Le proprietà per `MoveAxisConstraint` sono le seguenti:</span><span class="sxs-lookup"><span data-stu-id="6fc65-186">The properties for `MoveAxisConstraint` are as follows:</span></span>

#### <a name="constraint-on-movement"></a><span data-ttu-id="6fc65-187">Vincolo sullo spostamento</span><span class="sxs-lookup"><span data-stu-id="6fc65-187">Constraint on movement</span></span>

<span data-ttu-id="6fc65-188">Specifica gli assi su cui impedire lo spostamento.</span><span class="sxs-lookup"><span data-stu-id="6fc65-188">Specifies which axes to prevent movement on.</span></span> <span data-ttu-id="6fc65-189">Per impostazione predefinita, questi assi saranno globali anziché locali, ma possono essere modificati di seguito.</span><span class="sxs-lookup"><span data-stu-id="6fc65-189">By default, these axes will be global rather than local, but this can be changed below.</span></span> <span data-ttu-id="6fc65-190">Poiché questa proprietà è un flag, è possibile selezionare un numero qualsiasi di opzioni.</span><span class="sxs-lookup"><span data-stu-id="6fc65-190">Because this property is a flag, any number of options can be selected.</span></span>

- <span data-ttu-id="6fc65-191">*Asse X:* lo spostamento lungo l'asse x è vincolato se selezionato.</span><span class="sxs-lookup"><span data-stu-id="6fc65-191">*X Axis*: Movement along the x-axis is constrained if selected.</span></span>
- <span data-ttu-id="6fc65-192">*Asse Y:* lo spostamento lungo l'asse y è vincolato se selezionato.</span><span class="sxs-lookup"><span data-stu-id="6fc65-192">*Y Axis*: Movement along the y-axis is constrained if selected.</span></span>
- <span data-ttu-id="6fc65-193">*Asse Z:* lo spostamento lungo l'asse z è vincolato se selezionato.</span><span class="sxs-lookup"><span data-stu-id="6fc65-193">*Z Axis*: Movement along the z-axis is constrained if selected.</span></span>

#### <a name="use-local-space-for-constraint"></a><span data-ttu-id="6fc65-194">Usare lo spazio locale per il vincolo</span><span class="sxs-lookup"><span data-stu-id="6fc65-194">Use local space for constraint</span></span>

<span data-ttu-id="6fc65-195">Vincola gli assi di trasformazione locali dell'oggetto modificato se true.</span><span class="sxs-lookup"><span data-stu-id="6fc65-195">Will constrain relative the manipulated object's local transform axes if true.</span></span> <span data-ttu-id="6fc65-196">False per impostazione predefinita.</span><span class="sxs-lookup"><span data-stu-id="6fc65-196">False by default.</span></span>

### <a name="rotationaxisconstraint"></a><span data-ttu-id="6fc65-197">RotationAxisConstraint</span><span class="sxs-lookup"><span data-stu-id="6fc65-197">RotationAxisConstraint</span></span>

<img src="../images/object-manipulator/MRTK_Constraint_RotationAxis.gif" width="400" alt="Constraint Rotation Axis">

<span data-ttu-id="6fc65-198">Questo vincolo può essere usato per correggere gli assi su cui può essere ruotato un oggetto modificato.</span><span class="sxs-lookup"><span data-stu-id="6fc65-198">This constraint can be used to fix about which axes a manipulated object can be rotated.</span></span> <span data-ttu-id="6fc65-199">Ciò può essere utile per mantenere un oggetto modificato in posizione verticale, ma consentendo comunque le rotazioni dell'asse y, ad esempio.</span><span class="sxs-lookup"><span data-stu-id="6fc65-199">This can be useful for keeping a manipulated object upright, but still allowing y-axis rotations, for example.</span></span> <span data-ttu-id="6fc65-200">Le proprietà per `RotationAxisConstraint` sono le seguenti:</span><span class="sxs-lookup"><span data-stu-id="6fc65-200">The properties for `RotationAxisConstraint` are as follows:</span></span>

#### <a name="constraint-on-rotation"></a><span data-ttu-id="6fc65-201">Vincolo alla rotazione</span><span class="sxs-lookup"><span data-stu-id="6fc65-201">Constraint on rotation</span></span>

<span data-ttu-id="6fc65-202">Specifica gli assi su cui impedire la rotazione.</span><span class="sxs-lookup"><span data-stu-id="6fc65-202">Specifies which axes to prevent rotation about.</span></span> <span data-ttu-id="6fc65-203">Per impostazione predefinita, questi assi saranno globali anziché locali, ma possono essere modificati di seguito.</span><span class="sxs-lookup"><span data-stu-id="6fc65-203">By default, these axes will be global rather than local, but this can be changed below.</span></span> <span data-ttu-id="6fc65-204">Poiché questa proprietà è un flag, è possibile selezionare un numero qualsiasi di opzioni.</span><span class="sxs-lookup"><span data-stu-id="6fc65-204">Because this property is a flag, any number of options can be selected.</span></span>

- <span data-ttu-id="6fc65-205">*Asse Y:* la rotazione intorno all'asse y è vincolata se selezionata.</span><span class="sxs-lookup"><span data-stu-id="6fc65-205">*Y Axis*: Rotation about the y-axis is constrained if selected.</span></span>
- <span data-ttu-id="6fc65-206">*Asse Z:* la rotazione intorno all'asse z è vincolata se selezionata.</span><span class="sxs-lookup"><span data-stu-id="6fc65-206">*Z Axis*: Rotation about the z-axis is constrained if selected.</span></span>
- <span data-ttu-id="6fc65-207">*Asse X:* la rotazione intorno all'asse x è vincolata se selezionata.</span><span class="sxs-lookup"><span data-stu-id="6fc65-207">*X Axis*: Rotation about the x-axis is constrained if selected.</span></span>

#### <a name="use-local-space-for-constraint"></a><span data-ttu-id="6fc65-208">Usare lo spazio locale per il vincolo</span><span class="sxs-lookup"><span data-stu-id="6fc65-208">Use local space for constraint</span></span>

<span data-ttu-id="6fc65-209">Vincola gli assi di trasformazione locali dell'oggetto modificato se true.</span><span class="sxs-lookup"><span data-stu-id="6fc65-209">Will constrain relative the manipulated object's local transform axes if true.</span></span> <span data-ttu-id="6fc65-210">False per impostazione predefinita.</span><span class="sxs-lookup"><span data-stu-id="6fc65-210">False by default.</span></span>

### <a name="minmaxscaleconstraint"></a><span data-ttu-id="6fc65-211">MinMaxScaleConstraint</span><span class="sxs-lookup"><span data-stu-id="6fc65-211">MinMaxScaleConstraint</span></span>

<img src="../images/object-manipulator/MRTK_Constraint_MinMaxScale.gif" width="400" alt="Min Max Constatint">

<span data-ttu-id="6fc65-212">Questo vincolo consente di impostare i valori minimo e massimo per la scala dell'oggetto modificato.</span><span class="sxs-lookup"><span data-stu-id="6fc65-212">This constraint allows minimum and maximum values to be set for the scale of the manipulated object.</span></span> <span data-ttu-id="6fc65-213">Ciò è utile per impedire agli utenti di ridimensionare un oggetto troppo piccolo o troppo grande.</span><span class="sxs-lookup"><span data-stu-id="6fc65-213">This is useful for preventing users from scaling an object too small or too large.</span></span> <span data-ttu-id="6fc65-214">Le proprietà per `MinMaxScaleConstraint` sono le seguenti:</span><span class="sxs-lookup"><span data-stu-id="6fc65-214">The properties for `MinMaxScaleConstraint` are as follows:</span></span>

#### <a name="scale-minimum"></a><span data-ttu-id="6fc65-215">Scalabilità minima</span><span class="sxs-lookup"><span data-stu-id="6fc65-215">Scale minimum</span></span>

<span data-ttu-id="6fc65-216">Valore di scala minimo durante la manipolazione.</span><span class="sxs-lookup"><span data-stu-id="6fc65-216">The minimum scale value during manipulation.</span></span>

#### <a name="scale-maximum"></a><span data-ttu-id="6fc65-217">Scalabilità massima</span><span class="sxs-lookup"><span data-stu-id="6fc65-217">Scale maximum</span></span>

<span data-ttu-id="6fc65-218">Valore di scala massima durante la manipolazione.</span><span class="sxs-lookup"><span data-stu-id="6fc65-218">The maximum scale value during manipulation.</span></span>

#### <a name="relative-to-initial-state"></a><span data-ttu-id="6fc65-219">Rispetto allo stato iniziale</span><span class="sxs-lookup"><span data-stu-id="6fc65-219">Relative to initial state</span></span>

<span data-ttu-id="6fc65-220">Se true, i valori precedenti verranno interpretati come relativi alla scala iniziale degli oggetti.</span><span class="sxs-lookup"><span data-stu-id="6fc65-220">If true, the values above will be interpreted as relative to the objects initial scale.</span></span> <span data-ttu-id="6fc65-221">In caso contrario, verranno interpretati come valori di scala assoluti.</span><span class="sxs-lookup"><span data-stu-id="6fc65-221">Otherwise they will be interpreted as absolute scale values.</span></span>

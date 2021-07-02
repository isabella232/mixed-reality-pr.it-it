---
title: Servizio di fisica manuale
description: documentazione per usare il servizio di estensione fisica manuale in MRTK
author: RogPodge
ms.author: roliu
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: af7ea753d52b5e478c54ca19d6d8e391401eea6d
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176255"
---
# <a name="hand-physics-service"></a><span data-ttu-id="e8bff-104">Servizio di fisica manuale</span><span class="sxs-lookup"><span data-stu-id="e8bff-104">Hand physics service</span></span>

![Servizio di estensione fisica della mano](../images/hand-physics/MRTK_UX_HandPhysics_Main.jpg)

<span data-ttu-id="e8bff-106">Il servizio di fisica della mano consente eventi rigidi di collisione del corpo e interazioni con le mani articolate.</span><span class="sxs-lookup"><span data-stu-id="e8bff-106">The hand physics service enables rigid body collision events and interactions with articulated hands.</span></span>

## <a name="enabling-the-extension"></a><span data-ttu-id="e8bff-107">Abilitazione dell'estensione</span><span class="sxs-lookup"><span data-stu-id="e8bff-107">Enabling the extension</span></span>

<span data-ttu-id="e8bff-108">Per abilitare l'estensione, aprire il profilo RegisteredServiceProvider.</span><span class="sxs-lookup"><span data-stu-id="e8bff-108">To enable the extension, open your RegisteredServiceProvider profile.</span></span> <span data-ttu-id="e8bff-109">Fare `Register a new Service Provider` clic per aggiungere una nuova configurazione.</span><span class="sxs-lookup"><span data-stu-id="e8bff-109">Click `Register a new Service Provider` to add a new configuration.</span></span> <span data-ttu-id="e8bff-110">Nel campo tipo di componente selezionare HandPhysicsService.</span><span class="sxs-lookup"><span data-stu-id="e8bff-110">In the component type field, select HandPhysicsService.</span></span> <span data-ttu-id="e8bff-111">Nel campo Profilo di configurazione selezionare il profilo di fisica della mano predefinito incluso nell'estensione.</span><span class="sxs-lookup"><span data-stu-id="e8bff-111">In the configuration Profile field, select the default hand physics profile included with the extension.</span></span>

## <a name="profile-options"></a><span data-ttu-id="e8bff-112">Opzioni del profilo</span><span class="sxs-lookup"><span data-stu-id="e8bff-112">Profile options</span></span>

### <a name="hand-physics-layer"></a><span data-ttu-id="e8bff-113">Livello di fisica della mano</span><span class="sxs-lookup"><span data-stu-id="e8bff-113">Hand physics layer</span></span>

<span data-ttu-id="e8bff-114">Controlla il livello a cui verranno associati i giunzioni delle mani di cui è stata creata un'istanza.</span><span class="sxs-lookup"><span data-stu-id="e8bff-114">Controls the layer the instantiated hand joints will go to.</span></span>

<span data-ttu-id="e8bff-115">Anche se per impostazione predefinita il servizio è il livello "predefinito" (0), è consigliabile usare un livello separato per gli oggetti di fisica manuale.</span><span class="sxs-lookup"><span data-stu-id="e8bff-115">While the service defaults to the "default" layer (0), it is recommended to use a separate layer for hand physics objects.</span></span> <span data-ttu-id="e8bff-116">In caso contrario, potrebbero verificarsi collisioni indesiderate e/o raycast non accurati.</span><span class="sxs-lookup"><span data-stu-id="e8bff-116">Otherwise there may be unwanted collisions and/or inaccurate raycasts.</span></span>

### <a name="finger-tip-kinematic-body-prefab"></a><span data-ttu-id="e8bff-117">Prefab del corpo cinematico con punta del dito</span><span class="sxs-lookup"><span data-stu-id="e8bff-117">Finger tip kinematic body prefab</span></span>

<span data-ttu-id="e8bff-118">Controlla il prefab di cui viene creata un'istanza a punta del dito.</span><span class="sxs-lookup"><span data-stu-id="e8bff-118">Controls which prefab is instantiated on fingertips.</span></span> <span data-ttu-id="e8bff-119">Per il funzionamento previsto del servizio, il prefab richiede:</span><span class="sxs-lookup"><span data-stu-id="e8bff-119">In order for the service to work as expected, the prefab requires:</span></span>

- <span data-ttu-id="e8bff-120">Componente rigidbody con isKinematic abilitato</span><span class="sxs-lookup"><span data-stu-id="e8bff-120">A rigidbody component, with isKinematic enabled</span></span>
- <span data-ttu-id="e8bff-121">Un collisore</span><span class="sxs-lookup"><span data-stu-id="e8bff-121">A collider</span></span>
- <span data-ttu-id="e8bff-122">Componente `JointKinematicBody`</span><span class="sxs-lookup"><span data-stu-id="e8bff-122">`JointKinematicBody` component</span></span>

### <a name="use-palm-kinematic-body"></a><span data-ttu-id="e8bff-123">Usare il corpo kinematico del palmo</span><span class="sxs-lookup"><span data-stu-id="e8bff-123">Use palm kinematic body</span></span>

<span data-ttu-id="e8bff-124">Controlla se il servizio tenterà di creare un'istanza di un prefab sull'giunzione del palmo.</span><span class="sxs-lookup"><span data-stu-id="e8bff-124">Controls whether the service will attempt to instantiate a prefab on the palm joint.</span></span>

### <a name="palm-kinematic-body-prefab"></a><span data-ttu-id="e8bff-125">Prefab del corpo kinematico di mano</span><span class="sxs-lookup"><span data-stu-id="e8bff-125">Palm kinematic body prefab</span></span>

<span data-ttu-id="e8bff-126">Quando `UsePalmKinematicBody` è abilitato, questo è il prefab di cui verrà creata un'istanza.</span><span class="sxs-lookup"><span data-stu-id="e8bff-126">When `UsePalmKinematicBody` is enabled, this is the prefab it will instantiate.</span></span> <span data-ttu-id="e8bff-127">Proprio come `FingerTipKinematicBodyPrefab` , questo prefab richiede:</span><span class="sxs-lookup"><span data-stu-id="e8bff-127">Just like `FingerTipKinematicBodyPrefab`, this prefab requires:</span></span>

- <span data-ttu-id="e8bff-128">Componente rigidbody con isKinematic abilitato</span><span class="sxs-lookup"><span data-stu-id="e8bff-128">A rigidbody component, with isKinematic enabled</span></span>
- <span data-ttu-id="e8bff-129">Un collisore</span><span class="sxs-lookup"><span data-stu-id="e8bff-129">A collider</span></span>
- <span data-ttu-id="e8bff-130">Componente `JointKinematicBody`</span><span class="sxs-lookup"><span data-stu-id="e8bff-130">`JointKinematicBody` component</span></span>

## <a name="how-to-use-the-service"></a><span data-ttu-id="e8bff-131">Come usare il servizio</span><span class="sxs-lookup"><span data-stu-id="e8bff-131">How to use the service</span></span>

<span data-ttu-id="e8bff-132">Una volta abilitata, usare la proprietà di qualsiasi collisore per ricevere gli eventi di collisione da `IsTrigger` tutte le 10 cifre (e palmi se sono abilitati).</span><span class="sxs-lookup"><span data-stu-id="e8bff-132">Once enabled, use any collider's `IsTrigger` property to receive collision events from all 10 digits (and palms if they're enabled).</span></span>

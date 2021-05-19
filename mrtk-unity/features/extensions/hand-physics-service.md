---
title: Panoramica del servizio Fisica della mano
description: documentazione per usare il servizio di estensione fisica manuale in MRTK
author: RogPodge
ms.author: roliu
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: 751aec148d3a40da4728d2fdd60a60402b59a4de
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/19/2021
ms.locfileid: "110145081"
---
# <a name="hand-physics-extension-service"></a><span data-ttu-id="450a5-104">Servizio di estensione della fisica manuale</span><span class="sxs-lookup"><span data-stu-id="450a5-104">Hand physics extension service</span></span>

![Servizio di estensione fisica della mano](../images/hand-physics/MRTK_UX_HandPhysics_Main.jpg)

<span data-ttu-id="450a5-106">Il servizio di fisica della mano consente eventi rigidi di collisione del corpo e interazioni con le mani articolate.</span><span class="sxs-lookup"><span data-stu-id="450a5-106">The hand physics service enables rigid body collision events and interactions with articulated hands.</span></span>

## <a name="enabling-the-extension"></a><span data-ttu-id="450a5-107">Abilitazione dell'estensione</span><span class="sxs-lookup"><span data-stu-id="450a5-107">Enabling the extension</span></span>

<span data-ttu-id="450a5-108">Per abilitare l'estensione, aprire il profilo RegisteredServiceProvider.</span><span class="sxs-lookup"><span data-stu-id="450a5-108">To enable the extension, open your RegisteredServiceProvider profile.</span></span> <span data-ttu-id="450a5-109">Fare `Register a new Service Provider` clic per aggiungere una nuova configurazione.</span><span class="sxs-lookup"><span data-stu-id="450a5-109">Click `Register a new Service Provider` to add a new configuration.</span></span> <span data-ttu-id="450a5-110">Nel campo tipo di componente selezionare HandPhysicsService.</span><span class="sxs-lookup"><span data-stu-id="450a5-110">In the component type field, select HandPhysicsService.</span></span> <span data-ttu-id="450a5-111">Nel campo Profilo di configurazione selezionare il profilo di fisica della mano predefinito incluso nell'estensione.</span><span class="sxs-lookup"><span data-stu-id="450a5-111">In the configuration Profile field, select the default hand physics profile included with the extension.</span></span>

## <a name="profile-options"></a><span data-ttu-id="450a5-112">Opzioni del profilo</span><span class="sxs-lookup"><span data-stu-id="450a5-112">Profile options</span></span>

### <a name="hand-physics-layer"></a><span data-ttu-id="450a5-113">Livello di fisica della mano</span><span class="sxs-lookup"><span data-stu-id="450a5-113">Hand physics layer</span></span>

<span data-ttu-id="450a5-114">Controlla il livello a cui verranno associati i giunzioni delle mani di cui è stata creata un'istanza.</span><span class="sxs-lookup"><span data-stu-id="450a5-114">Controls the layer the instantiated hand joints will go to.</span></span>

<span data-ttu-id="450a5-115">Mentre per impostazione predefinita il servizio è il livello "predefinito" (0), è consigliabile usare un livello separato per gli oggetti di fisica manuale.</span><span class="sxs-lookup"><span data-stu-id="450a5-115">While the service defaults to the "default" layer (0), it is recommended to use a separate layer for hand physics objects.</span></span> <span data-ttu-id="450a5-116">In caso contrario, potrebbero verificarsi collisioni indesiderate e/o raycast non accurati.</span><span class="sxs-lookup"><span data-stu-id="450a5-116">Otherwise there may be unwanted collisions and/or inaccurate raycasts.</span></span>

### <a name="finger-tip-kinematic-body-prefab"></a><span data-ttu-id="450a5-117">Prefab del corpo cinematico con punta del dito</span><span class="sxs-lookup"><span data-stu-id="450a5-117">Finger tip kinematic body prefab</span></span>

<span data-ttu-id="450a5-118">Controlla il prefab di cui viene creata un'istanza a punta del dito.</span><span class="sxs-lookup"><span data-stu-id="450a5-118">Controls which prefab is instantiated on fingertips.</span></span> <span data-ttu-id="450a5-119">Perché il servizio funzioni come previsto, il prefab richiede:</span><span class="sxs-lookup"><span data-stu-id="450a5-119">In order for the service to work as expected, the prefab requires:</span></span>

- <span data-ttu-id="450a5-120">Componente rigidbody con isKinematic abilitato</span><span class="sxs-lookup"><span data-stu-id="450a5-120">A rigidbody component, with isKinematic enabled</span></span>
- <span data-ttu-id="450a5-121">Un collisore</span><span class="sxs-lookup"><span data-stu-id="450a5-121">A collider</span></span>
- <span data-ttu-id="450a5-122">Componente `JointKinematicBody`</span><span class="sxs-lookup"><span data-stu-id="450a5-122">`JointKinematicBody` component</span></span>

### <a name="use-palm-kinematic-body"></a><span data-ttu-id="450a5-123">Usare il corpo cinematico delle palme</span><span class="sxs-lookup"><span data-stu-id="450a5-123">Use palm kinematic body</span></span>

<span data-ttu-id="450a5-124">Controlla se il servizio tenterà di creare un'istanza di un prefab sul palmo.</span><span class="sxs-lookup"><span data-stu-id="450a5-124">Controls whether the service will attempt to instantiate a prefab on the palm joint.</span></span>

### <a name="palm-kinematic-body-prefab"></a><span data-ttu-id="450a5-125">Prefab del corpo cinematico delle palme</span><span class="sxs-lookup"><span data-stu-id="450a5-125">Palm kinematic body prefab</span></span>

<span data-ttu-id="450a5-126">Quando `UsePalmKinematicBody` è abilitato, questo è il prefab di cui verrà creata un'istanza.</span><span class="sxs-lookup"><span data-stu-id="450a5-126">When `UsePalmKinematicBody` is enabled, this is the prefab it will instantiate.</span></span> <span data-ttu-id="450a5-127">Proprio come `FingerTipKinematicBodyPrefab` , questo prefab richiede:</span><span class="sxs-lookup"><span data-stu-id="450a5-127">Just like `FingerTipKinematicBodyPrefab`, this prefab requires:</span></span>

- <span data-ttu-id="450a5-128">Componente rigidbody con isKinematic abilitato</span><span class="sxs-lookup"><span data-stu-id="450a5-128">A rigidbody component, with isKinematic enabled</span></span>
- <span data-ttu-id="450a5-129">Un collisore</span><span class="sxs-lookup"><span data-stu-id="450a5-129">A collider</span></span>
- <span data-ttu-id="450a5-130">Componente `JointKinematicBody`</span><span class="sxs-lookup"><span data-stu-id="450a5-130">`JointKinematicBody` component</span></span>

## <a name="how-to-use-the-service"></a><span data-ttu-id="450a5-131">Come usare il servizio</span><span class="sxs-lookup"><span data-stu-id="450a5-131">How to use the service</span></span>

<span data-ttu-id="450a5-132">Una volta abilitata, usare la proprietà di qualsiasi collisore per ricevere eventi di collisione da `IsTrigger` tutte le 10 cifre (e palmi se abilitati).</span><span class="sxs-lookup"><span data-stu-id="450a5-132">Once enabled, use any collider's `IsTrigger` property to receive collision events from all 10 digits (and palms if they're enabled).</span></span>

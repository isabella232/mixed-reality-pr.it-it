---
title: HandPhysicsServiceOverview
description: documentazione per usare il servizio di estensione della fisica della mano in MRTK
author: RogPodge
ms.author: roliu
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: d897c9ab3e85aa38edfbc6f3bd3bff6b6c1b2627
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2021
ms.locfileid: "104685524"
---
# <a name="hand-physics-extension-service"></a><span data-ttu-id="eec97-104">Servizio di estensione fisica della mano</span><span class="sxs-lookup"><span data-stu-id="eec97-104">Hand physics extension service</span></span>

![Servizio di estensione fisica della mano](../images/hand-physics/MRTK_UX_HandPhysics_Main.jpg)

<span data-ttu-id="eec97-106">Il servizio di fisica della mano Abilita gli eventi di collisione corpo rigidi e le interazioni con le mani articolate.</span><span class="sxs-lookup"><span data-stu-id="eec97-106">The hand physics service enables rigid body collision events and interactions with articulated hands.</span></span>

## <a name="enabling-the-extension"></a><span data-ttu-id="eec97-107">Abilitazione dell'estensione</span><span class="sxs-lookup"><span data-stu-id="eec97-107">Enabling the extension</span></span>

<span data-ttu-id="eec97-108">Per abilitare l'estensione, aprire il profilo RegisteredServiceProvider.</span><span class="sxs-lookup"><span data-stu-id="eec97-108">To enable the extension, open your RegisteredServiceProvider profile.</span></span> <span data-ttu-id="eec97-109">Fare clic `Register a new Service Provider` per aggiungere una nuova configurazione.</span><span class="sxs-lookup"><span data-stu-id="eec97-109">Click `Register a new Service Provider` to add a new configuration.</span></span> <span data-ttu-id="eec97-110">Nel campo tipo di componente selezionare HandPhysicsService.</span><span class="sxs-lookup"><span data-stu-id="eec97-110">In the component type field, select HandPhysicsService.</span></span> <span data-ttu-id="eec97-111">Nel campo profilo di configurazione selezionare il profilo fisico della mano predefinito incluso nell'estensione.</span><span class="sxs-lookup"><span data-stu-id="eec97-111">In the configuration Profile field, select the default hand physics profile included with the extension.</span></span>

## <a name="profile-options"></a><span data-ttu-id="eec97-112">Opzioni profilo</span><span class="sxs-lookup"><span data-stu-id="eec97-112">Profile options</span></span>

### <a name="hand-physics-layer"></a><span data-ttu-id="eec97-113">Livello di fisica della mano</span><span class="sxs-lookup"><span data-stu-id="eec97-113">Hand physics layer</span></span>

<span data-ttu-id="eec97-114">Controlla il livello a cui verranno indirizzati i giunti a cui è stata creata un'istanza.</span><span class="sxs-lookup"><span data-stu-id="eec97-114">Controls the layer the instantiated hand joints will go to.</span></span>

<span data-ttu-id="eec97-115">Mentre per il servizio viene usato per impostazione predefinita il livello "default" (0), è consigliabile usare un livello separato per gli oggetti fisici della mano.</span><span class="sxs-lookup"><span data-stu-id="eec97-115">While the service defaults to the "default" layer (0), it is recommended to use a separate layer for hand physics objects.</span></span> <span data-ttu-id="eec97-116">In caso contrario, potrebbero verificarsi collisioni indesiderate e/o raycasts non accurati.</span><span class="sxs-lookup"><span data-stu-id="eec97-116">Otherwise there may be unwanted collisions and/or inaccurate raycasts.</span></span>

### <a name="finger-tip-kinematic-body-prefab"></a><span data-ttu-id="eec97-117">Prefabbricato del corpo cinematica del finger tip</span><span class="sxs-lookup"><span data-stu-id="eec97-117">Finger tip kinematic body prefab</span></span>

<span data-ttu-id="eec97-118">Controlla la creazione di un'istanza del prefabbricato a portata di mano.</span><span class="sxs-lookup"><span data-stu-id="eec97-118">Controls which prefab is instantiated on fingertips.</span></span> <span data-ttu-id="eec97-119">Affinché il servizio funzioni come previsto, il prefabbricato richiede:</span><span class="sxs-lookup"><span data-stu-id="eec97-119">In order for the service to work as expected, the prefab requires:</span></span>

- <span data-ttu-id="eec97-120">Un componente rigidbody con l'abilitazione della funzionalità cinematica</span><span class="sxs-lookup"><span data-stu-id="eec97-120">A rigidbody component, with isKinematic enabled</span></span>
- <span data-ttu-id="eec97-121">Un Collider</span><span class="sxs-lookup"><span data-stu-id="eec97-121">A collider</span></span>
- <span data-ttu-id="eec97-122">Componente `JointKinematicBody`</span><span class="sxs-lookup"><span data-stu-id="eec97-122">`JointKinematicBody` component</span></span>

### <a name="use-palm-kinematic-body"></a><span data-ttu-id="eec97-123">USA corpo cinematica Palm</span><span class="sxs-lookup"><span data-stu-id="eec97-123">Use palm kinematic body</span></span>

<span data-ttu-id="eec97-124">Controlla se il servizio tenterà di creare un'istanza di una prefabbricata sul giunto di Palm.</span><span class="sxs-lookup"><span data-stu-id="eec97-124">Controls whether the service will attempt to instantiate a prefab on the palm joint.</span></span>

### <a name="palm-kinematic-body-prefab"></a><span data-ttu-id="eec97-125">Prefabbricato del corpo di Palm cinematico</span><span class="sxs-lookup"><span data-stu-id="eec97-125">Palm kinematic body prefab</span></span>

<span data-ttu-id="eec97-126">Quando `UsePalmKinematicBody` è abilitato, si tratta della prefabbricata di cui verrà creata un'istanza.</span><span class="sxs-lookup"><span data-stu-id="eec97-126">When `UsePalmKinematicBody` is enabled, this is the prefab it will instantiate.</span></span> <span data-ttu-id="eec97-127">Analogamente a `FingerTipKinematicBodyPrefab` questa prefabbricata è necessario:</span><span class="sxs-lookup"><span data-stu-id="eec97-127">Just like `FingerTipKinematicBodyPrefab`, this prefab requires:</span></span>

- <span data-ttu-id="eec97-128">Un componente rigidbody con l'abilitazione della funzionalità cinematica</span><span class="sxs-lookup"><span data-stu-id="eec97-128">A rigidbody component, with isKinematic enabled</span></span>
- <span data-ttu-id="eec97-129">Un Collider</span><span class="sxs-lookup"><span data-stu-id="eec97-129">A collider</span></span>
- <span data-ttu-id="eec97-130">Componente `JointKinematicBody`</span><span class="sxs-lookup"><span data-stu-id="eec97-130">`JointKinematicBody` component</span></span>

## <a name="how-to-use-the-service"></a><span data-ttu-id="eec97-131">Come usare il servizio</span><span class="sxs-lookup"><span data-stu-id="eec97-131">How to use the service</span></span>

<span data-ttu-id="eec97-132">Una volta abilitata, usare la proprietà di qualsiasi Collider `IsTrigger` per ricevere eventi di collisione da tutte le 10 cifre (e Palms se sono abilitate).</span><span class="sxs-lookup"><span data-stu-id="eec97-132">Once enabled, use any collider's `IsTrigger` property to receive collision events from all 10 digits (and palms if they're enabled).</span></span>

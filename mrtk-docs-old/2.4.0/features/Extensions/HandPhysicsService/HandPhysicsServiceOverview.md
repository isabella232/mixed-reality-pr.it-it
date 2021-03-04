---
title: HandPhysicsServiceOverview
description: documentazione per usare il servizio di estensione della fisica della mano in MRTK
author: RogPodge
ms.author: roliu
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: 3ad1770746e9b7c829aa26ab9e301a38b2baf1ce
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/03/2021
ms.locfileid: "101783656"
---
# <a name="hand-physics-extension-service"></a><span data-ttu-id="e1e55-104">Servizio di estensione fisica della mano</span><span class="sxs-lookup"><span data-stu-id="e1e55-104">Hand physics extension service</span></span>

<span data-ttu-id="e1e55-105">Il servizio di fisica della mano Abilita gli eventi di collisione corpo rigidi e le interazioni con le mani articolate.</span><span class="sxs-lookup"><span data-stu-id="e1e55-105">The hand physics service enables rigid body collision events and interactions with articulated hands.</span></span>

## <a name="enabling-the-extension"></a><span data-ttu-id="e1e55-106">Abilitazione dell'estensione</span><span class="sxs-lookup"><span data-stu-id="e1e55-106">Enabling the extension</span></span>

<span data-ttu-id="e1e55-107">Per abilitare l'estensione, aprire il profilo RegisteredServiceProvider.</span><span class="sxs-lookup"><span data-stu-id="e1e55-107">To enable the extension, open your RegisteredServiceProvider profile.</span></span> <span data-ttu-id="e1e55-108">Fare clic `Register a new Service Provider` per aggiungere una nuova configurazione.</span><span class="sxs-lookup"><span data-stu-id="e1e55-108">Click `Register a new Service Provider` to add a new configuration.</span></span> <span data-ttu-id="e1e55-109">Nel campo tipo di componente selezionare HandPhysicsService.</span><span class="sxs-lookup"><span data-stu-id="e1e55-109">In the component type field, select HandPhysicsService.</span></span> <span data-ttu-id="e1e55-110">Nel campo profilo di configurazione selezionare il profilo fisico della mano predefinito incluso nell'estensione.</span><span class="sxs-lookup"><span data-stu-id="e1e55-110">In the configuration Profile field, select the default hand physics profile included with the extension.</span></span>

## <a name="profile-options"></a><span data-ttu-id="e1e55-111">Opzioni profilo</span><span class="sxs-lookup"><span data-stu-id="e1e55-111">Profile options</span></span>

### <a name="hand-physics-layer"></a><span data-ttu-id="e1e55-112">Livello di fisica della mano</span><span class="sxs-lookup"><span data-stu-id="e1e55-112">Hand physics layer</span></span>

<span data-ttu-id="e1e55-113">Controlla il livello a cui verranno indirizzati i giunti a cui è stata creata un'istanza.</span><span class="sxs-lookup"><span data-stu-id="e1e55-113">Controls the layer the instantiated hand joints will go to.</span></span>

<span data-ttu-id="e1e55-114">Mentre per il servizio viene usato per impostazione predefinita il livello "default" (0), è consigliabile usare un livello separato per gli oggetti fisici della mano.</span><span class="sxs-lookup"><span data-stu-id="e1e55-114">While the service defaults to the "default" layer (0), it is recommended to use a separate layer for hand physics objects.</span></span> <span data-ttu-id="e1e55-115">In caso contrario, potrebbero verificarsi collisioni indesiderate e/o raycasts non accurati.</span><span class="sxs-lookup"><span data-stu-id="e1e55-115">Otherwise there may be unwanted collisions and/or inaccurate raycasts.</span></span>

### <a name="finger-tip-kinematic-body-prefab"></a><span data-ttu-id="e1e55-116">Prefabbricato del corpo cinematica del finger tip</span><span class="sxs-lookup"><span data-stu-id="e1e55-116">Finger tip kinematic body prefab</span></span>

<span data-ttu-id="e1e55-117">Controlla la creazione di un'istanza del prefabbricato a portata di mano.</span><span class="sxs-lookup"><span data-stu-id="e1e55-117">Controls which prefab is instantiated on fingertips.</span></span> <span data-ttu-id="e1e55-118">Affinché il servizio funzioni come previsto, il prefabbricato richiede:</span><span class="sxs-lookup"><span data-stu-id="e1e55-118">In order for the service to work as expected, the prefab requires:</span></span>

- <span data-ttu-id="e1e55-119">Un componente rigidbody con l'abilitazione della funzionalità cinematica</span><span class="sxs-lookup"><span data-stu-id="e1e55-119">A rigidbody component, with isKinematic enabled</span></span>
- <span data-ttu-id="e1e55-120">Un Collider</span><span class="sxs-lookup"><span data-stu-id="e1e55-120">A collider</span></span>
- <span data-ttu-id="e1e55-121">Componente `JointKinematicBody`</span><span class="sxs-lookup"><span data-stu-id="e1e55-121">`JointKinematicBody` component</span></span>

### <a name="use-palm-kinematic-body"></a><span data-ttu-id="e1e55-122">USA corpo cinematica Palm</span><span class="sxs-lookup"><span data-stu-id="e1e55-122">Use palm kinematic body</span></span>

<span data-ttu-id="e1e55-123">Controlla se il servizio tenterà di creare un'istanza di una prefabbricata sul giunto di Palm.</span><span class="sxs-lookup"><span data-stu-id="e1e55-123">Controls whether the service will attempt to instantiate a prefab on the palm joint.</span></span>

### <a name="palm-kinematic-body-prefab"></a><span data-ttu-id="e1e55-124">Prefabbricato del corpo di Palm cinematico</span><span class="sxs-lookup"><span data-stu-id="e1e55-124">Palm kinematic body prefab</span></span>

<span data-ttu-id="e1e55-125">Quando `UsePalmKinematicBody` è abilitato, si tratta della prefabbricata di cui verrà creata un'istanza.</span><span class="sxs-lookup"><span data-stu-id="e1e55-125">When `UsePalmKinematicBody` is enabled, this is the prefab it will instantiate.</span></span> <span data-ttu-id="e1e55-126">Analogamente a `FingerTipKinematicBodyPrefab` questa prefabbricata è necessario:</span><span class="sxs-lookup"><span data-stu-id="e1e55-126">Just like `FingerTipKinematicBodyPrefab`, this prefab requires:</span></span>

- <span data-ttu-id="e1e55-127">Un componente rigidbody con l'abilitazione della funzionalità cinematica</span><span class="sxs-lookup"><span data-stu-id="e1e55-127">A rigidbody component, with isKinematic enabled</span></span>
- <span data-ttu-id="e1e55-128">Un Collider</span><span class="sxs-lookup"><span data-stu-id="e1e55-128">A collider</span></span>
- <span data-ttu-id="e1e55-129">Componente `JointKinematicBody`</span><span class="sxs-lookup"><span data-stu-id="e1e55-129">`JointKinematicBody` component</span></span>

## <a name="how-to-use-the-service"></a><span data-ttu-id="e1e55-130">Come usare il servizio</span><span class="sxs-lookup"><span data-stu-id="e1e55-130">How to use the service</span></span>

<span data-ttu-id="e1e55-131">Una volta abilitata, usare la proprietà di qualsiasi Collider `IsTrigger` per ricevere eventi di collisione da tutte le 10 cifre (e Palms se sono abilitate).</span><span class="sxs-lookup"><span data-stu-id="e1e55-131">Once enabled, use any collider's `IsTrigger` property to receive collision events from all 10 digits (and palms if they're enabled).</span></span>

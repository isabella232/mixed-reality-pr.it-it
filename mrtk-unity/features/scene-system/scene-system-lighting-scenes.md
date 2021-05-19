---
title: Scene di illuminazione del sistema di scena
description: Documentazione sull'illuminazione nella scena.
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realtà mista, sviluppo, MRTK,
ms.openlocfilehash: fa7442bc968710a31ce3ca379c7fd73928e6e324
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144418"
---
# <a name="lighting-scene-operations"></a><span data-ttu-id="adadc-104">Operazioni della scena di illuminazione</span><span class="sxs-lookup"><span data-stu-id="adadc-104">Lighting scene operations</span></span>

<span data-ttu-id="adadc-105">La scena di illuminazione predefinita definita nel profilo viene caricata all'avvio.</span><span class="sxs-lookup"><span data-stu-id="adadc-105">The default lighting scene defined in your profile is loaded on startup.</span></span> <span data-ttu-id="adadc-106">Tale scena di illuminazione rimane caricata fino a quando `SetLightingScene` non viene chiamato .</span><span class="sxs-lookup"><span data-stu-id="adadc-106">That lighting scene remains loaded until `SetLightingScene` is called.</span></span>

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

sceneSystem.SetLightingScene("MorningLighting");
```

## <a name="lighting-setting-transitions"></a><span data-ttu-id="adadc-107">Transizioni delle impostazioni di illuminazione</span><span class="sxs-lookup"><span data-stu-id="adadc-107">Lighting setting transitions</span></span>

<span data-ttu-id="adadc-108">`transitionType` controlla lo stile della transizione alla nuova scena di illuminazione.</span><span class="sxs-lookup"><span data-stu-id="adadc-108">`transitionType` controls the style of the transition to new lighting scene.</span></span>

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

sceneSystem.SetLightingScene("MiddayLighting", LightingSceneTransitionType.CrossFade);
```

<span data-ttu-id="adadc-109">Gli stili disponibili sono:</span><span class="sxs-lookup"><span data-stu-id="adadc-109">The available styles are:</span></span>

<span data-ttu-id="adadc-110">Tipo</span><span class="sxs-lookup"><span data-stu-id="adadc-110">Type</span></span> | <span data-ttu-id="adadc-111">Descrizione</span><span class="sxs-lookup"><span data-stu-id="adadc-111">Description</span></span> | <span data-ttu-id="adadc-112">Durata</span><span class="sxs-lookup"><span data-stu-id="adadc-112">Duration</span></span>
--- | --- | ---
<span data-ttu-id="adadc-113">Nessuno</span><span class="sxs-lookup"><span data-stu-id="adadc-113">None</span></span> | <span data-ttu-id="adadc-114">La scena di illuminazione precedente viene scaricata e viene caricata una nuova scena di illuminazione.</span><span class="sxs-lookup"><span data-stu-id="adadc-114">Previous lighting scene is unloaded, new lighting scene is loaded.</span></span> <span data-ttu-id="adadc-115">Nessuna transizione.</span><span class="sxs-lookup"><span data-stu-id="adadc-115">No transition.</span></span> | <span data-ttu-id="adadc-116">Ignorato</span><span class="sxs-lookup"><span data-stu-id="adadc-116">Ignored</span></span>
<span data-ttu-id="adadc-117">FadeToBlack</span><span class="sxs-lookup"><span data-stu-id="adadc-117">FadeToBlack</span></span> | <span data-ttu-id="adadc-118">La scena di illuminazione precedente si dissolve in nero.</span><span class="sxs-lookup"><span data-stu-id="adadc-118">Previous lighting scene fades out to black.</span></span> <span data-ttu-id="adadc-119">Viene caricata una nuova scena di illuminazione, quindi sfumare dal nero.</span><span class="sxs-lookup"><span data-stu-id="adadc-119">New lighting scene is loaded, then faded up from black.</span></span> <span data-ttu-id="adadc-120">Utile per transizioni fluide tra le posizioni.</span><span class="sxs-lookup"><span data-stu-id="adadc-120">Useful for smooth transitions between locations.</span></span> | <span data-ttu-id="adadc-121">Usata</span><span class="sxs-lookup"><span data-stu-id="adadc-121">Used</span></span>
<span data-ttu-id="adadc-122">Dissolvenza incrociata</span><span class="sxs-lookup"><span data-stu-id="adadc-122">CrossFade</span></span> | <span data-ttu-id="adadc-123">La scena di illuminazione precedente si dissolve quando la nuova scena di illuminazione si dissolve.</span><span class="sxs-lookup"><span data-stu-id="adadc-123">Previous lighting scene fades out as new lighting scene fades in.</span></span> <span data-ttu-id="adadc-124">Utile per transizioni fluide tra le impostazioni di illuminazione nella stessa posizione.</span><span class="sxs-lookup"><span data-stu-id="adadc-124">Useful for smooth transitions between lighting setups in the same location.</span></span> | <span data-ttu-id="adadc-125">Usata</span><span class="sxs-lookup"><span data-stu-id="adadc-125">Used</span></span>

<span data-ttu-id="adadc-126">Si noti che alcune impostazioni di illuminazione non possono essere interpolate durante le transizioni.</span><span class="sxs-lookup"><span data-stu-id="adadc-126">Note that some lighting settings cannot be interpolated during transitions.</span></span> <span data-ttu-id="adadc-127">Se si vuole una transizione visiva uniforme, queste impostazioni devono rimanere coerenti tra le scene di illuminazione.</span><span class="sxs-lookup"><span data-stu-id="adadc-127">If you want a smooth visual transition these settings will have to remain consistent between lighting scenes.</span></span>

<span data-ttu-id="adadc-128">Impostazione</span><span class="sxs-lookup"><span data-stu-id="adadc-128">Setting</span></span> | <span data-ttu-id="adadc-129">Transizione Smooth FadeToBlack</span><span class="sxs-lookup"><span data-stu-id="adadc-129">Smooth FadeToBlack Transition</span></span> | <span data-ttu-id="adadc-130">Transizione crossFade uniforme</span><span class="sxs-lookup"><span data-stu-id="adadc-130">Smooth CrossFade Transition</span></span>
--- | --- | ---
<span data-ttu-id="adadc-131">Skybox</span><span class="sxs-lookup"><span data-stu-id="adadc-131">Skybox</span></span> | <span data-ttu-id="adadc-132">No</span><span class="sxs-lookup"><span data-stu-id="adadc-132">No</span></span> | <span data-ttu-id="adadc-133">No</span><span class="sxs-lookup"><span data-stu-id="adadc-133">No</span></span>
<span data-ttu-id="adadc-134">Reflection personalizzate</span><span class="sxs-lookup"><span data-stu-id="adadc-134">Custom Reflections</span></span> | <span data-ttu-id="adadc-135">No</span><span class="sxs-lookup"><span data-stu-id="adadc-135">No</span></span> | <span data-ttu-id="adadc-136">No</span><span class="sxs-lookup"><span data-stu-id="adadc-136">No</span></span>
<span data-ttu-id="adadc-137">Ombreggiature in tempo reale luce del sole</span><span class="sxs-lookup"><span data-stu-id="adadc-137">Sun light realtime shadows</span></span> | <span data-ttu-id="adadc-138">Sì</span><span class="sxs-lookup"><span data-stu-id="adadc-138">Yes</span></span> | <span data-ttu-id="adadc-139">No</span><span class="sxs-lookup"><span data-stu-id="adadc-139">No</span></span>

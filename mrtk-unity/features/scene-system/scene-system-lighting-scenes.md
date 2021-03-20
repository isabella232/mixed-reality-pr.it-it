---
title: SceneSystemLightingScenes
description: Documentazione sull'illuminazione nella scena.
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: 4cd6b61172f03da99ba33a06d06e20f095572622
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2021
ms.locfileid: "104688361"
---
# <a name="lighting-scene-operations"></a><span data-ttu-id="b708b-104">Operazioni di illuminazione della scena</span><span class="sxs-lookup"><span data-stu-id="b708b-104">Lighting scene operations</span></span>

<span data-ttu-id="b708b-105">La scena di illuminazione predefinita definita nel profilo viene caricata all'avvio.</span><span class="sxs-lookup"><span data-stu-id="b708b-105">The default lighting scene defined in your profile is loaded on startup.</span></span> <span data-ttu-id="b708b-106">La scena di illuminazione rimane caricata fino a quando non `SetLightingScene` viene chiamato il metodo.</span><span class="sxs-lookup"><span data-stu-id="b708b-106">That lighting scene remains loaded until `SetLightingScene` is called.</span></span>

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

sceneSystem.SetLightingScene("MorningLighting");
```

## <a name="lighting-setting-transitions"></a><span data-ttu-id="b708b-107">Transizioni di impostazioni di illuminazione</span><span class="sxs-lookup"><span data-stu-id="b708b-107">Lighting setting transitions</span></span>

<span data-ttu-id="b708b-108">`transitionType` Controlla lo stile della transizione alla nuova scena di illuminazione.</span><span class="sxs-lookup"><span data-stu-id="b708b-108">`transitionType` controls the style of the transition to new lighting scene.</span></span>

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

sceneSystem.SetLightingScene("MiddayLighting", LightingSceneTransitionType.CrossFade);
```

<span data-ttu-id="b708b-109">Gli stili disponibili sono:</span><span class="sxs-lookup"><span data-stu-id="b708b-109">The available styles are:</span></span>

<span data-ttu-id="b708b-110">Tipo</span><span class="sxs-lookup"><span data-stu-id="b708b-110">Type</span></span> | <span data-ttu-id="b708b-111">Descrizione</span><span class="sxs-lookup"><span data-stu-id="b708b-111">Description</span></span> | <span data-ttu-id="b708b-112">Duration</span><span class="sxs-lookup"><span data-stu-id="b708b-112">Duration</span></span>
--- | --- | ---
<span data-ttu-id="b708b-113">nessuno</span><span class="sxs-lookup"><span data-stu-id="b708b-113">None</span></span> | <span data-ttu-id="b708b-114">La scena di illuminazione precedente è scaricata e viene caricata una nuova scena di illuminazione.</span><span class="sxs-lookup"><span data-stu-id="b708b-114">Previous lighting scene is unloaded, new lighting scene is loaded.</span></span> <span data-ttu-id="b708b-115">Nessuna transizione.</span><span class="sxs-lookup"><span data-stu-id="b708b-115">No transition.</span></span> | <span data-ttu-id="b708b-116">Ignorato</span><span class="sxs-lookup"><span data-stu-id="b708b-116">Ignored</span></span>
<span data-ttu-id="b708b-117">FadeToBlack</span><span class="sxs-lookup"><span data-stu-id="b708b-117">FadeToBlack</span></span> | <span data-ttu-id="b708b-118">La scena di illuminazione precedente si dissolve in nero.</span><span class="sxs-lookup"><span data-stu-id="b708b-118">Previous lighting scene fades out to black.</span></span> <span data-ttu-id="b708b-119">La nuova scena di illuminazione è stata caricata, quindi è svanita dal nero.</span><span class="sxs-lookup"><span data-stu-id="b708b-119">New lighting scene is loaded, then faded up from black.</span></span> <span data-ttu-id="b708b-120">Utile per transizioni uniformi tra i percorsi.</span><span class="sxs-lookup"><span data-stu-id="b708b-120">Useful for smooth transitions between locations.</span></span> | <span data-ttu-id="b708b-121">Usata</span><span class="sxs-lookup"><span data-stu-id="b708b-121">Used</span></span>
<span data-ttu-id="b708b-122">CrossFade</span><span class="sxs-lookup"><span data-stu-id="b708b-122">CrossFade</span></span> | <span data-ttu-id="b708b-123">La scena di illuminazione precedente si dissolve quando la nuova scena di illuminazione si affievolisce.</span><span class="sxs-lookup"><span data-stu-id="b708b-123">Previous lighting scene fades out as new lighting scene fades in.</span></span> <span data-ttu-id="b708b-124">Utile per transizioni uniformi tra le impostazioni di illuminazione nella stessa posizione.</span><span class="sxs-lookup"><span data-stu-id="b708b-124">Useful for smooth transitions between lighting setups in the same location.</span></span> | <span data-ttu-id="b708b-125">Usata</span><span class="sxs-lookup"><span data-stu-id="b708b-125">Used</span></span>

<span data-ttu-id="b708b-126">Si noti che alcune impostazioni di illuminazione non possono essere interpolate durante le transizioni.</span><span class="sxs-lookup"><span data-stu-id="b708b-126">Note that some lighting settings cannot be interpolated during transitions.</span></span> <span data-ttu-id="b708b-127">Se si vuole una transizione visiva uniforme, queste impostazioni dovranno rimanere coerenti tra le scene di illuminazione.</span><span class="sxs-lookup"><span data-stu-id="b708b-127">If you want a smooth visual transition these settings will have to remain consistent between lighting scenes.</span></span>

<span data-ttu-id="b708b-128">Impostazione</span><span class="sxs-lookup"><span data-stu-id="b708b-128">Setting</span></span> | <span data-ttu-id="b708b-129">Transizione Smooth FadeToBlack</span><span class="sxs-lookup"><span data-stu-id="b708b-129">Smooth FadeToBlack Transition</span></span> | <span data-ttu-id="b708b-130">Transizione senza dissolvenza</span><span class="sxs-lookup"><span data-stu-id="b708b-130">Smooth CrossFade Transition</span></span>
--- | --- | ---
<span data-ttu-id="b708b-131">SKYBOX</span><span class="sxs-lookup"><span data-stu-id="b708b-131">Skybox</span></span> | <span data-ttu-id="b708b-132">No</span><span class="sxs-lookup"><span data-stu-id="b708b-132">No</span></span> | <span data-ttu-id="b708b-133">No</span><span class="sxs-lookup"><span data-stu-id="b708b-133">No</span></span>
<span data-ttu-id="b708b-134">Riflessioni personalizzate</span><span class="sxs-lookup"><span data-stu-id="b708b-134">Custom Reflections</span></span> | <span data-ttu-id="b708b-135">No</span><span class="sxs-lookup"><span data-stu-id="b708b-135">No</span></span> | <span data-ttu-id="b708b-136">No</span><span class="sxs-lookup"><span data-stu-id="b708b-136">No</span></span>
<span data-ttu-id="b708b-137">Shadows in tempo reale luce solare</span><span class="sxs-lookup"><span data-stu-id="b708b-137">Sun light realtime shadows</span></span> | <span data-ttu-id="b708b-138">Sì</span><span class="sxs-lookup"><span data-stu-id="b708b-138">Yes</span></span> | <span data-ttu-id="b708b-139">No</span><span class="sxs-lookup"><span data-stu-id="b708b-139">No</span></span>

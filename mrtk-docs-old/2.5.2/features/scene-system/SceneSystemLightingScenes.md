---
title: SceneSystemLightingScenes
description: Documentazione sull'illuminazione nella scena.
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: 753738d8ac1404bb4d959ede108bfd8f4ec4749b
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/03/2021
ms.locfileid: "101783176"
---
# <a name="lighting-scene-operations"></a><span data-ttu-id="0b772-104">Operazioni di illuminazione della scena</span><span class="sxs-lookup"><span data-stu-id="0b772-104">Lighting scene operations</span></span>

<span data-ttu-id="0b772-105">La scena di illuminazione predefinita definita nel profilo viene caricata all'avvio.</span><span class="sxs-lookup"><span data-stu-id="0b772-105">The default lighting scene defined in your profile is loaded on startup.</span></span> <span data-ttu-id="0b772-106">La scena di illuminazione rimane caricata fino a quando non `SetLightingScene` viene chiamato il metodo.</span><span class="sxs-lookup"><span data-stu-id="0b772-106">That lighting scene remains loaded until `SetLightingScene` is called.</span></span>

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

sceneSystem.SetLightingScene("MorningLighting");
```

## <a name="lighting-setting-transitions"></a><span data-ttu-id="0b772-107">Transizioni di impostazioni di illuminazione</span><span class="sxs-lookup"><span data-stu-id="0b772-107">Lighting setting transitions</span></span>

<span data-ttu-id="0b772-108">`transitionType` Controlla lo stile della transizione alla nuova scena di illuminazione.</span><span class="sxs-lookup"><span data-stu-id="0b772-108">`transitionType` controls the style of the transition to new lighting scene.</span></span>

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

sceneSystem.SetLightingScene("MiddayLighting", LightingSceneTransitionType.CrossFade);
```

<span data-ttu-id="0b772-109">Gli stili disponibili sono:</span><span class="sxs-lookup"><span data-stu-id="0b772-109">The available styles are:</span></span>

<span data-ttu-id="0b772-110">Tipo</span><span class="sxs-lookup"><span data-stu-id="0b772-110">Type</span></span> | <span data-ttu-id="0b772-111">Descrizione</span><span class="sxs-lookup"><span data-stu-id="0b772-111">Description</span></span> | <span data-ttu-id="0b772-112">Duration</span><span class="sxs-lookup"><span data-stu-id="0b772-112">Duration</span></span>
--- | --- | ---
<span data-ttu-id="0b772-113">nessuno</span><span class="sxs-lookup"><span data-stu-id="0b772-113">None</span></span> | <span data-ttu-id="0b772-114">La scena di illuminazione precedente è scaricata e viene caricata una nuova scena di illuminazione.</span><span class="sxs-lookup"><span data-stu-id="0b772-114">Previous lighting scene is unloaded, new lighting scene is loaded.</span></span> <span data-ttu-id="0b772-115">Nessuna transizione.</span><span class="sxs-lookup"><span data-stu-id="0b772-115">No transition.</span></span> | <span data-ttu-id="0b772-116">Ignorato</span><span class="sxs-lookup"><span data-stu-id="0b772-116">Ignored</span></span>
<span data-ttu-id="0b772-117">FadeToBlack</span><span class="sxs-lookup"><span data-stu-id="0b772-117">FadeToBlack</span></span> | <span data-ttu-id="0b772-118">La scena di illuminazione precedente si dissolve in nero.</span><span class="sxs-lookup"><span data-stu-id="0b772-118">Previous lighting scene fades out to black.</span></span> <span data-ttu-id="0b772-119">La nuova scena di illuminazione è stata caricata, quindi è svanita dal nero.</span><span class="sxs-lookup"><span data-stu-id="0b772-119">New lighting scene is loaded, then faded up from black.</span></span> <span data-ttu-id="0b772-120">Utile per transizioni uniformi tra i percorsi.</span><span class="sxs-lookup"><span data-stu-id="0b772-120">Useful for smooth transitions between locations.</span></span> | <span data-ttu-id="0b772-121">Usata</span><span class="sxs-lookup"><span data-stu-id="0b772-121">Used</span></span>
<span data-ttu-id="0b772-122">CrossFade</span><span class="sxs-lookup"><span data-stu-id="0b772-122">CrossFade</span></span> | <span data-ttu-id="0b772-123">La scena di illuminazione precedente si dissolve quando la nuova scena di illuminazione si affievolisce.</span><span class="sxs-lookup"><span data-stu-id="0b772-123">Previous lighting scene fades out as new lighting scene fades in.</span></span> <span data-ttu-id="0b772-124">Utile per transizioni uniformi tra le impostazioni di illuminazione nella stessa posizione.</span><span class="sxs-lookup"><span data-stu-id="0b772-124">Useful for smooth transitions between lighting setups in the same location.</span></span> | <span data-ttu-id="0b772-125">Usata</span><span class="sxs-lookup"><span data-stu-id="0b772-125">Used</span></span>

<span data-ttu-id="0b772-126">Si noti che alcune impostazioni di illuminazione non possono essere interpolate durante le transizioni.</span><span class="sxs-lookup"><span data-stu-id="0b772-126">Note that some lighting settings cannot be interpolated during transitions.</span></span> <span data-ttu-id="0b772-127">Se si vuole una transizione visiva uniforme, queste impostazioni dovranno rimanere coerenti tra le scene di illuminazione.</span><span class="sxs-lookup"><span data-stu-id="0b772-127">If you want a smooth visual transition these settings will have to remain consistent between lighting scenes.</span></span>

<span data-ttu-id="0b772-128">Impostazione</span><span class="sxs-lookup"><span data-stu-id="0b772-128">Setting</span></span> | <span data-ttu-id="0b772-129">Transizione Smooth FadeToBlack</span><span class="sxs-lookup"><span data-stu-id="0b772-129">Smooth FadeToBlack Transition</span></span> | <span data-ttu-id="0b772-130">Transizione senza dissolvenza</span><span class="sxs-lookup"><span data-stu-id="0b772-130">Smooth CrossFade Transition</span></span>
--- | --- | ---
<span data-ttu-id="0b772-131">SKYBOX</span><span class="sxs-lookup"><span data-stu-id="0b772-131">Skybox</span></span> | <span data-ttu-id="0b772-132">No</span><span class="sxs-lookup"><span data-stu-id="0b772-132">No</span></span> | <span data-ttu-id="0b772-133">No</span><span class="sxs-lookup"><span data-stu-id="0b772-133">No</span></span>
<span data-ttu-id="0b772-134">Riflessioni personalizzate</span><span class="sxs-lookup"><span data-stu-id="0b772-134">Custom Reflections</span></span> | <span data-ttu-id="0b772-135">No</span><span class="sxs-lookup"><span data-stu-id="0b772-135">No</span></span> | <span data-ttu-id="0b772-136">No</span><span class="sxs-lookup"><span data-stu-id="0b772-136">No</span></span>
<span data-ttu-id="0b772-137">Shadows in tempo reale luce solare</span><span class="sxs-lookup"><span data-stu-id="0b772-137">Sun light realtime shadows</span></span> | <span data-ttu-id="0b772-138">Sì</span><span class="sxs-lookup"><span data-stu-id="0b772-138">Yes</span></span> | <span data-ttu-id="0b772-139">No</span><span class="sxs-lookup"><span data-stu-id="0b772-139">No</span></span>

---
title: SceneSystemContentLoading
description: Sistema di scena per il caricamento di documentazione con MRTK
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: de5a7e155a4c993ad128e4b3ab3fb46ea0873c1c
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2021
ms.locfileid: "104690541"
---
# <a name="content-scene-loading"></a><span data-ttu-id="8c3f5-104">Caricamento della scena del contenuto</span><span class="sxs-lookup"><span data-stu-id="8c3f5-104">Content scene loading</span></span>

<span data-ttu-id="8c3f5-105">Tutte le operazioni di caricamento del contenuto sono asincrone e, per impostazione predefinita, tutto il caricamento del contenuto è additivo.</span><span class="sxs-lookup"><span data-stu-id="8c3f5-105">All content load operations are asynchronous, and by default all content loading is additive.</span></span> <span data-ttu-id="8c3f5-106">I Manager e le scene di illuminazione non sono mai interessati dalle operazioni di caricamento del contenuto.</span><span class="sxs-lookup"><span data-stu-id="8c3f5-106">Manager and lighting scenes are never affected by content loading operations.</span></span> <span data-ttu-id="8c3f5-107">Per informazioni sul monitoraggio dello stato di avanzamento del caricamento e dell'attivazione della scena, vedere [monitoraggio del caricamento del contenuto](SceneSystemLoadProgress.md).</span><span class="sxs-lookup"><span data-stu-id="8c3f5-107">For information about monitoring load progress and scene activation, see [Monitoring Content Loading](SceneSystemLoadProgress.md).</span></span>

## <a name="loading-content"></a><span data-ttu-id="8c3f5-108">Caricamento del contenuto</span><span class="sxs-lookup"><span data-stu-id="8c3f5-108">Loading content</span></span>

<span data-ttu-id="8c3f5-109">Per caricare le scene del contenuto `LoadContent` , usare il metodo:</span><span class="sxs-lookup"><span data-stu-id="8c3f5-109">To load content scenes use the `LoadContent` method:</span></span>

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

// Additively load a single content scene
await sceneSystem.LoadContent("MyContentScene");

// Additively load a set of content scenes
await sceneSystem.LoadContent(new string[] { "MyContentScene1", "MyContentScene2", "MyContentScene3" });
```

## <a name="single-scene-loading"></a><span data-ttu-id="8c3f5-110">Caricamento di una singola scena</span><span class="sxs-lookup"><span data-stu-id="8c3f5-110">Single scene loading</span></span>

<span data-ttu-id="8c3f5-111">L'equivalente di un singolo carico della scena può essere effettuato tramite l' `mode` argomento facoltativo.</span><span class="sxs-lookup"><span data-stu-id="8c3f5-111">The equivalent of a single scene load can be achieved via the optional `mode` argument.</span></span> <span data-ttu-id="8c3f5-112">`LoadSceneMode.Single` prima di procedere con il caricamento, Scarica innanzitutto tutte le scene di contenuto caricati.</span><span class="sxs-lookup"><span data-stu-id="8c3f5-112">`LoadSceneMode.Single` will first unload all loaded content scenes before proceeding with the load.</span></span>

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

// ContentScene1, ContentScene2 and ContentScene3 will be loaded additively
await sceneSystem.LoadContent("ContentScene1");
await sceneSystem.LoadContent("ContentScene2");
await sceneSystem.LoadContent("ContentScene3");

// ContentScene1, ContentScene2 and ContentScene3 will be unloaded
// SingleContentScene will be loaded additively
await sceneSystem.LoadContent("SingleContentScene", LoadSceneMode.Single);
```

## <a name="next--previous-scene-loading"></a><span data-ttu-id="8c3f5-113">Caricamento della scena successiva/precedente</span><span class="sxs-lookup"><span data-stu-id="8c3f5-113">Next / previous scene loading</span></span>

<span data-ttu-id="8c3f5-114">Il contenuto può essere caricato singolarmente in ordine di indice di compilazione.</span><span class="sxs-lookup"><span data-stu-id="8c3f5-114">Content can be singly loaded in order of build index.</span></span> <span data-ttu-id="8c3f5-115">Questa operazione è utile per le applicazioni di presentazione che consentono agli utenti di eseguire una serie di scene dimostrative una alla volta.</span><span class="sxs-lookup"><span data-stu-id="8c3f5-115">This is useful for showcase applications that take users through a set of demonstration scenes one-by-one.</span></span>

![Immagine di MRTK_SceneSystemBuildSettings](../images/scene-system/MRTK_SceneSystemBuildSettings.png)

<span data-ttu-id="8c3f5-117">Si noti che il caricamento del contenuto successivo/precedente USA LoadSceneMode. Single per impostazione predefinita per garantire che il contenuto precedente venga scaricato.</span><span class="sxs-lookup"><span data-stu-id="8c3f5-117">Note that next / prev content loading uses LoadSceneMode.Single by default to ensure that the previous content is unloaded.</span></span>

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

if (nextSceneRequested && sceneSystem.NextContentExists)
{
    await sceneSystem.LoadNextContent();
}

if (prevSceneRequested && sceneSystem.PrevContentExists)
{
    await sceneSystem.LoadPrevContent();
}
```

<span data-ttu-id="8c3f5-118">`PrevContentExists` Restituisce true se è presente almeno una scena di contenuto con un indice di compilazione inferiore rispetto all'indice di compilazione più basso attualmente caricato.</span><span class="sxs-lookup"><span data-stu-id="8c3f5-118">`PrevContentExists` will return true if there is at least one content scene that has a lower build index than the lowest build index currently loaded.</span></span> <span data-ttu-id="8c3f5-119">`NextContentExists` Restituisce true se è presente almeno una scena di contenuto con un indice di compilazione superiore rispetto all'indice di compilazione più alto attualmente caricato.</span><span class="sxs-lookup"><span data-stu-id="8c3f5-119">`NextContentExists` will return true if there is at least one content scene that has a higher build index than the highest build index currently loaded.</span></span>

<span data-ttu-id="8c3f5-120">Se l' `wrap` argomento è true, il contenuto eseguirà il loopback al primo/ultimo indice di compilazione.</span><span class="sxs-lookup"><span data-stu-id="8c3f5-120">If the `wrap` argument is true, content will loop back to the first / last build index.</span></span> <span data-ttu-id="8c3f5-121">In questo modo si elimina la necessità di verificare il contenuto successivo o precedente:</span><span class="sxs-lookup"><span data-stu-id="8c3f5-121">This removes the need to check for next / previous content:</span></span>

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

if (nextSceneRequested)
{
    await sceneSystem.LoadNextContent(true);
}

if (prevSceneRequested)
{
    await sceneSystem.LoadPrevContent(true);
}
```

## <a name="loading-by-tag"></a><span data-ttu-id="8c3f5-122">Caricamento per tag</span><span class="sxs-lookup"><span data-stu-id="8c3f5-122">Loading by tag</span></span>

![Immagine di MRTK_SceneSystemLoadingByTag](../images/scene-system/MRTK_SceneSystemLoadingByTag.png)

<span data-ttu-id="8c3f5-124">A volte è consigliabile caricare le scene di contenuto nei gruppi.</span><span class="sxs-lookup"><span data-stu-id="8c3f5-124">It's sometimes desirable to load content scenes in groups.</span></span> <span data-ttu-id="8c3f5-125">Ad esempio, una fase di un'esperienza può essere costituita da più scene, che devono essere caricate simultaneamente per funzionare.</span><span class="sxs-lookup"><span data-stu-id="8c3f5-125">Eg, a stage of an experience may be composed of multiple scenes, all of which must be loaded simultaneously to function.</span></span> <span data-ttu-id="8c3f5-126">Per semplificare questa operazione, è possibile contrassegnare le scene e quindi caricarle o scaricarle con tale tag.</span><span class="sxs-lookup"><span data-stu-id="8c3f5-126">To facilitate this, you can tag your scenes and then load them or unload them with that tag.</span></span>

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

await LoadContentByTag("Stage1");

// Wait until stage 1 is complete

await UnloadContentByTag("Stage1");
await LoadContentByTag("Stage2);
```

<span data-ttu-id="8c3f5-127">Il caricamento in base al tag può essere utile anche se gli artisti vogliono incorporare o rimuovere elementi da un'esperienza senza dover modificare gli script.</span><span class="sxs-lookup"><span data-stu-id="8c3f5-127">Loading by tag can also be useful if artists want to incorporate / remove elements from an experience without having to modify scripts.</span></span> <span data-ttu-id="8c3f5-128">Ad esempio, l'esecuzione di questo script con i due set di tag seguenti produce risultati diversi:</span><span class="sxs-lookup"><span data-stu-id="8c3f5-128">For instance, running this script with the following two sets of tags produces different results:</span></span>

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

await LoadContentByTag("Terrain");
await LoadContentByTag("Structures");
await LoadContentByTag("Vegetation");
```

### <a name="testing-content"></a><span data-ttu-id="8c3f5-129">Test del contenuto</span><span class="sxs-lookup"><span data-stu-id="8c3f5-129">Testing content</span></span>

<span data-ttu-id="8c3f5-130">Nome scena</span><span class="sxs-lookup"><span data-stu-id="8c3f5-130">Scene Name</span></span> | <span data-ttu-id="8c3f5-131">Tag di scena</span><span class="sxs-lookup"><span data-stu-id="8c3f5-131">Scene Tag</span></span> | <span data-ttu-id="8c3f5-132">Caricato dallo script</span><span class="sxs-lookup"><span data-stu-id="8c3f5-132">Loaded by script</span></span>
---|---|---
<span data-ttu-id="8c3f5-133">DebugTerrainPhysics</span><span class="sxs-lookup"><span data-stu-id="8c3f5-133">DebugTerrainPhysics</span></span> | <span data-ttu-id="8c3f5-134">Terreno</span><span class="sxs-lookup"><span data-stu-id="8c3f5-134">Terrain</span></span> | <span data-ttu-id="8c3f5-135">•</span><span class="sxs-lookup"><span data-stu-id="8c3f5-135">•</span></span>
<span data-ttu-id="8c3f5-136">StructureTesting</span><span class="sxs-lookup"><span data-stu-id="8c3f5-136">StructureTesting</span></span> | <span data-ttu-id="8c3f5-137">Strutture</span><span class="sxs-lookup"><span data-stu-id="8c3f5-137">Structures</span></span> | <span data-ttu-id="8c3f5-138">•</span><span class="sxs-lookup"><span data-stu-id="8c3f5-138">•</span></span>
<span data-ttu-id="8c3f5-139">VegetationTools</span><span class="sxs-lookup"><span data-stu-id="8c3f5-139">VegetationTools</span></span> | <span data-ttu-id="8c3f5-140">Vegetazione</span><span class="sxs-lookup"><span data-stu-id="8c3f5-140">Vegetation</span></span> | <span data-ttu-id="8c3f5-141">•</span><span class="sxs-lookup"><span data-stu-id="8c3f5-141">•</span></span>
<span data-ttu-id="8c3f5-142">Mountain</span><span class="sxs-lookup"><span data-stu-id="8c3f5-142">Mountain</span></span> | <span data-ttu-id="8c3f5-143">Terreno</span><span class="sxs-lookup"><span data-stu-id="8c3f5-143">Terrain</span></span> | <span data-ttu-id="8c3f5-144">•</span><span class="sxs-lookup"><span data-stu-id="8c3f5-144">•</span></span>
<span data-ttu-id="8c3f5-145">Abitacolo</span><span class="sxs-lookup"><span data-stu-id="8c3f5-145">Cabin</span></span> | <span data-ttu-id="8c3f5-146">Strutture</span><span class="sxs-lookup"><span data-stu-id="8c3f5-146">Structures</span></span> | <span data-ttu-id="8c3f5-147">•</span><span class="sxs-lookup"><span data-stu-id="8c3f5-147">•</span></span>
<span data-ttu-id="8c3f5-148">Trees</span><span class="sxs-lookup"><span data-stu-id="8c3f5-148">Trees</span></span> | <span data-ttu-id="8c3f5-149">Vegetazione</span><span class="sxs-lookup"><span data-stu-id="8c3f5-149">Vegetation</span></span> | <span data-ttu-id="8c3f5-150">•</span><span class="sxs-lookup"><span data-stu-id="8c3f5-150">•</span></span>

### <a name="final-content"></a><span data-ttu-id="8c3f5-151">Contenuto finale</span><span class="sxs-lookup"><span data-stu-id="8c3f5-151">Final content</span></span>

<span data-ttu-id="8c3f5-152">Nome scena</span><span class="sxs-lookup"><span data-stu-id="8c3f5-152">Scene Name</span></span> | <span data-ttu-id="8c3f5-153">Tag di scena</span><span class="sxs-lookup"><span data-stu-id="8c3f5-153">Scene Tag</span></span> | <span data-ttu-id="8c3f5-154">Caricato dallo script</span><span class="sxs-lookup"><span data-stu-id="8c3f5-154">Loaded by script</span></span>
---|---|---
<span data-ttu-id="8c3f5-155">DebugTerrainPhysics</span><span class="sxs-lookup"><span data-stu-id="8c3f5-155">DebugTerrainPhysics</span></span> | <span data-ttu-id="8c3f5-156">DoNotInclude</span><span class="sxs-lookup"><span data-stu-id="8c3f5-156">DoNotInclude</span></span> |
<span data-ttu-id="8c3f5-157">StructureTesting</span><span class="sxs-lookup"><span data-stu-id="8c3f5-157">StructureTesting</span></span> | <span data-ttu-id="8c3f5-158">DoNotInclude</span><span class="sxs-lookup"><span data-stu-id="8c3f5-158">DoNotInclude</span></span> |
<span data-ttu-id="8c3f5-159">VegetationTools</span><span class="sxs-lookup"><span data-stu-id="8c3f5-159">VegetationTools</span></span> | <span data-ttu-id="8c3f5-160">DoNotInclude</span><span class="sxs-lookup"><span data-stu-id="8c3f5-160">DoNotInclude</span></span> |
<span data-ttu-id="8c3f5-161">Mountain</span><span class="sxs-lookup"><span data-stu-id="8c3f5-161">Mountain</span></span> | <span data-ttu-id="8c3f5-162">Terreno</span><span class="sxs-lookup"><span data-stu-id="8c3f5-162">Terrain</span></span> | <span data-ttu-id="8c3f5-163">•</span><span class="sxs-lookup"><span data-stu-id="8c3f5-163">•</span></span>
<span data-ttu-id="8c3f5-164">Abitacolo</span><span class="sxs-lookup"><span data-stu-id="8c3f5-164">Cabin</span></span> | <span data-ttu-id="8c3f5-165">Strutture</span><span class="sxs-lookup"><span data-stu-id="8c3f5-165">Structures</span></span> | <span data-ttu-id="8c3f5-166">•</span><span class="sxs-lookup"><span data-stu-id="8c3f5-166">•</span></span>
<span data-ttu-id="8c3f5-167">Trees</span><span class="sxs-lookup"><span data-stu-id="8c3f5-167">Trees</span></span> | <span data-ttu-id="8c3f5-168">Vegetazione</span><span class="sxs-lookup"><span data-stu-id="8c3f5-168">Vegetation</span></span> | <span data-ttu-id="8c3f5-169">•</span><span class="sxs-lookup"><span data-stu-id="8c3f5-169">•</span></span>

---

## <a name="editor-behavior"></a><span data-ttu-id="8c3f5-170">Comportamento dell'editor</span><span class="sxs-lookup"><span data-stu-id="8c3f5-170">Editor behavior</span></span>

<span data-ttu-id="8c3f5-171">È possibile eseguire tutte queste operazioni in Editor e in modalità di riproduzione usando il [controllo del servizio](../../configuration/MixedRealityConfigurationGuide.md#editor-utilities) del sistema di scena.</span><span class="sxs-lookup"><span data-stu-id="8c3f5-171">You can perform all these operations in editor and in play mode by using the Scene System's [service inspector.](../../configuration/MixedRealityConfigurationGuide.md#editor-utilities)</span></span> <span data-ttu-id="8c3f5-172">In modalità di modifica i caricamenti della scena saranno istantanei, mentre in modalità di riproduzione è possibile osservare lo stato di avanzamento del caricamento e usare i [token di attivazione.](SceneSystemLoadProgress.md)</span><span class="sxs-lookup"><span data-stu-id="8c3f5-172">In edit mode scene loads will be instantaneous, while in play mode you can observe loading progress and use [activation tokens.](SceneSystemLoadProgress.md)</span></span>

![Immagine di MRTK_SceneSystemServiceInspector](../images/scene-system/MRTK_SceneSystemServiceInspector.PNG)

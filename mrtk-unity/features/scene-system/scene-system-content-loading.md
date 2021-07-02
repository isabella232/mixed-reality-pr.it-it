---
title: Caricamento del contenuto del sistema della scena
description: Documentazione sul caricamento del sistema scene con MRTK
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: c6bc6474afd50fe265853e53c0f29009d816cf51
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177581"
---
# <a name="scene-system-content-loading"></a><span data-ttu-id="7d43b-104">Caricamento del contenuto del sistema della scena</span><span class="sxs-lookup"><span data-stu-id="7d43b-104">Scene system content loading</span></span>

<span data-ttu-id="7d43b-105">Tutte le operazioni di caricamento del contenuto sono asincrone e per impostazione predefinita tutto il caricamento del contenuto è additivo.</span><span class="sxs-lookup"><span data-stu-id="7d43b-105">All content load operations are asynchronous, and by default all content loading is additive.</span></span> <span data-ttu-id="7d43b-106">Le operazioni di caricamento del contenuto non hanno mai effetto sulle scene di gestione e di illuminazione.</span><span class="sxs-lookup"><span data-stu-id="7d43b-106">Manager and lighting scenes are never affected by content loading operations.</span></span> <span data-ttu-id="7d43b-107">Per informazioni sul monitoraggio dello stato di avanzamento del carico e dell'attivazione della scena, vedere [Monitoraggio del caricamento del contenuto](scene-system-load-progress.md).</span><span class="sxs-lookup"><span data-stu-id="7d43b-107">For information about monitoring load progress and scene activation, see [Monitoring Content Loading](scene-system-load-progress.md).</span></span>

## <a name="loading-content"></a><span data-ttu-id="7d43b-108">Caricamento del contenuto</span><span class="sxs-lookup"><span data-stu-id="7d43b-108">Loading content</span></span>

<span data-ttu-id="7d43b-109">Per caricare scene di contenuto, usare il `LoadContent` metodo :</span><span class="sxs-lookup"><span data-stu-id="7d43b-109">To load content scenes use the `LoadContent` method:</span></span>

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

// Additively load a single content scene
await sceneSystem.LoadContent("MyContentScene");

// Additively load a set of content scenes
await sceneSystem.LoadContent(new string[] { "MyContentScene1", "MyContentScene2", "MyContentScene3" });
```

## <a name="single-scene-loading"></a><span data-ttu-id="7d43b-110">Caricamento di una singola scena</span><span class="sxs-lookup"><span data-stu-id="7d43b-110">Single scene loading</span></span>

<span data-ttu-id="7d43b-111">L'equivalente di un singolo carico di scena può essere ottenuto tramite l'argomento `mode` facoltativo .</span><span class="sxs-lookup"><span data-stu-id="7d43b-111">The equivalent of a single scene load can be achieved via the optional `mode` argument.</span></span> <span data-ttu-id="7d43b-112">`LoadSceneMode.Single` scarica prima tutte le scene di contenuto caricato prima di procedere con il caricamento.</span><span class="sxs-lookup"><span data-stu-id="7d43b-112">`LoadSceneMode.Single` will first unload all loaded content scenes before proceeding with the load.</span></span>

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

## <a name="next--previous-scene-loading"></a><span data-ttu-id="7d43b-113">Caricamento della scena successiva/precedente</span><span class="sxs-lookup"><span data-stu-id="7d43b-113">Next / previous scene loading</span></span>

<span data-ttu-id="7d43b-114">Il contenuto può essere caricato in ordine di indice di compilazione.</span><span class="sxs-lookup"><span data-stu-id="7d43b-114">Content can be singly loaded in order of build index.</span></span> <span data-ttu-id="7d43b-115">Ciò è utile per presentare le applicazioni che consentono agli utenti di eseguire una alla volta un set di scene dimostrativi.</span><span class="sxs-lookup"><span data-stu-id="7d43b-115">This is useful for showcase applications that take users through a set of demonstration scenes one-by-one.</span></span>

![Scene correnti nella compilazione nelle impostazioni del lettore](../images/scene-system/MRTK_SceneSystemBuildSettings.png)

<span data-ttu-id="7d43b-117">Si noti che il caricamento del contenuto successivo/preliminare usa LoadSceneMode.Single per impostazione predefinita per garantire che il contenuto precedente sia scaricato.</span><span class="sxs-lookup"><span data-stu-id="7d43b-117">Note that next / prev content loading uses LoadSceneMode.Single by default to ensure that the previous content is unloaded.</span></span>

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

<span data-ttu-id="7d43b-118">`PrevContentExists` restituirà true se è presente almeno una scena di contenuto con un indice di compilazione inferiore rispetto all'indice di compilazione più basso attualmente caricato.</span><span class="sxs-lookup"><span data-stu-id="7d43b-118">`PrevContentExists` will return true if there is at least one content scene that has a lower build index than the lowest build index currently loaded.</span></span> <span data-ttu-id="7d43b-119">`NextContentExists` restituirà true se è presente almeno una scena di contenuto con un indice di compilazione più alto rispetto all'indice di compilazione più alto attualmente caricato.</span><span class="sxs-lookup"><span data-stu-id="7d43b-119">`NextContentExists` will return true if there is at least one content scene that has a higher build index than the highest build index currently loaded.</span></span>

<span data-ttu-id="7d43b-120">Se `wrap` l'argomento è true, il contenuto torna all'indice di prima/ultima compilazione.</span><span class="sxs-lookup"><span data-stu-id="7d43b-120">If the `wrap` argument is true, content will loop back to the first / last build index.</span></span> <span data-ttu-id="7d43b-121">In questo modo viene rimossa la necessità di controllare il contenuto successivo/precedente:</span><span class="sxs-lookup"><span data-stu-id="7d43b-121">This removes the need to check for next / previous content:</span></span>

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

## <a name="loading-by-tag"></a><span data-ttu-id="7d43b-122">Caricamento in base al tag</span><span class="sxs-lookup"><span data-stu-id="7d43b-122">Loading by tag</span></span>

![Caricamento di scene di contenuto in base al tag](../images/scene-system/MRTK_SceneSystemLoadingByTag.png)

<span data-ttu-id="7d43b-124">A volte è preferibile caricare scene di contenuto in gruppi.</span><span class="sxs-lookup"><span data-stu-id="7d43b-124">It's sometimes desirable to load content scenes in groups.</span></span> <span data-ttu-id="7d43b-125">Ad esempio, una fase di un'esperienza può essere costituita da più scene, tutte da caricare contemporaneamente per funzionare.</span><span class="sxs-lookup"><span data-stu-id="7d43b-125">Eg, a stage of an experience may be composed of multiple scenes, all of which must be loaded simultaneously to function.</span></span> <span data-ttu-id="7d43b-126">Per semplificare questa operazione, è possibile contrassegnare le scene e quindi caricarle o scaricarle con tale tag.</span><span class="sxs-lookup"><span data-stu-id="7d43b-126">To facilitate this, you can tag your scenes and then load them or unload them with that tag.</span></span>

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

await LoadContentByTag("Stage1");

// Wait until stage 1 is complete

await UnloadContentByTag("Stage1");
await LoadContentByTag("Stage2);
```

<span data-ttu-id="7d43b-127">Il caricamento in base al tag può essere utile anche se gli autori vogliono incorporare/rimuovere elementi da un'esperienza senza dover modificare gli script.</span><span class="sxs-lookup"><span data-stu-id="7d43b-127">Loading by tag can also be useful if artists want to incorporate / remove elements from an experience without having to modify scripts.</span></span> <span data-ttu-id="7d43b-128">Ad esempio, l'esecuzione di questo script con i due set di tag seguenti produce risultati diversi:</span><span class="sxs-lookup"><span data-stu-id="7d43b-128">For instance, running this script with the following two sets of tags produces different results:</span></span>

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

await LoadContentByTag("Terrain");
await LoadContentByTag("Structures");
await LoadContentByTag("Vegetation");
```

### <a name="testing-content"></a><span data-ttu-id="7d43b-129">Test del contenuto</span><span class="sxs-lookup"><span data-stu-id="7d43b-129">Testing content</span></span>

<span data-ttu-id="7d43b-130">Nome scena</span><span class="sxs-lookup"><span data-stu-id="7d43b-130">Scene Name</span></span> | <span data-ttu-id="7d43b-131">Tag della scena</span><span class="sxs-lookup"><span data-stu-id="7d43b-131">Scene Tag</span></span> | <span data-ttu-id="7d43b-132">Caricato da script</span><span class="sxs-lookup"><span data-stu-id="7d43b-132">Loaded by script</span></span>
---|---|---
<span data-ttu-id="7d43b-133">DebugTerrainPhysics</span><span class="sxs-lookup"><span data-stu-id="7d43b-133">DebugTerrainPhysics</span></span> | <span data-ttu-id="7d43b-134">Terreno</span><span class="sxs-lookup"><span data-stu-id="7d43b-134">Terrain</span></span> | <span data-ttu-id="7d43b-135">•</span><span class="sxs-lookup"><span data-stu-id="7d43b-135">•</span></span>
<span data-ttu-id="7d43b-136">StructureTesting</span><span class="sxs-lookup"><span data-stu-id="7d43b-136">StructureTesting</span></span> | <span data-ttu-id="7d43b-137">Strutture</span><span class="sxs-lookup"><span data-stu-id="7d43b-137">Structures</span></span> | <span data-ttu-id="7d43b-138">•</span><span class="sxs-lookup"><span data-stu-id="7d43b-138">•</span></span>
<span data-ttu-id="7d43b-139">Estrumenti di verde</span><span class="sxs-lookup"><span data-stu-id="7d43b-139">VegetationTools</span></span> | <span data-ttu-id="7d43b-140">Vegetazione</span><span class="sxs-lookup"><span data-stu-id="7d43b-140">Vegetation</span></span> | <span data-ttu-id="7d43b-141">•</span><span class="sxs-lookup"><span data-stu-id="7d43b-141">•</span></span>
<span data-ttu-id="7d43b-142">Mountain</span><span class="sxs-lookup"><span data-stu-id="7d43b-142">Mountain</span></span> | <span data-ttu-id="7d43b-143">Terreno</span><span class="sxs-lookup"><span data-stu-id="7d43b-143">Terrain</span></span> | <span data-ttu-id="7d43b-144">•</span><span class="sxs-lookup"><span data-stu-id="7d43b-144">•</span></span>
<span data-ttu-id="7d43b-145">Cabina</span><span class="sxs-lookup"><span data-stu-id="7d43b-145">Cabin</span></span> | <span data-ttu-id="7d43b-146">Strutture</span><span class="sxs-lookup"><span data-stu-id="7d43b-146">Structures</span></span> | <span data-ttu-id="7d43b-147">•</span><span class="sxs-lookup"><span data-stu-id="7d43b-147">•</span></span>
<span data-ttu-id="7d43b-148">Trees</span><span class="sxs-lookup"><span data-stu-id="7d43b-148">Trees</span></span> | <span data-ttu-id="7d43b-149">Vegetazione</span><span class="sxs-lookup"><span data-stu-id="7d43b-149">Vegetation</span></span> | <span data-ttu-id="7d43b-150">•</span><span class="sxs-lookup"><span data-stu-id="7d43b-150">•</span></span>

### <a name="final-content"></a><span data-ttu-id="7d43b-151">Contenuto finale</span><span class="sxs-lookup"><span data-stu-id="7d43b-151">Final content</span></span>

<span data-ttu-id="7d43b-152">Nome scena</span><span class="sxs-lookup"><span data-stu-id="7d43b-152">Scene Name</span></span> | <span data-ttu-id="7d43b-153">Tag della scena</span><span class="sxs-lookup"><span data-stu-id="7d43b-153">Scene Tag</span></span> | <span data-ttu-id="7d43b-154">Caricato da script</span><span class="sxs-lookup"><span data-stu-id="7d43b-154">Loaded by script</span></span>
---|---|---
<span data-ttu-id="7d43b-155">DebugTerrainPhysics</span><span class="sxs-lookup"><span data-stu-id="7d43b-155">DebugTerrainPhysics</span></span> | <span data-ttu-id="7d43b-156">DoNotInclude</span><span class="sxs-lookup"><span data-stu-id="7d43b-156">DoNotInclude</span></span> |
<span data-ttu-id="7d43b-157">StructureTesting</span><span class="sxs-lookup"><span data-stu-id="7d43b-157">StructureTesting</span></span> | <span data-ttu-id="7d43b-158">DoNotInclude</span><span class="sxs-lookup"><span data-stu-id="7d43b-158">DoNotInclude</span></span> |
<span data-ttu-id="7d43b-159">Estrumenti di verde</span><span class="sxs-lookup"><span data-stu-id="7d43b-159">VegetationTools</span></span> | <span data-ttu-id="7d43b-160">DoNotInclude</span><span class="sxs-lookup"><span data-stu-id="7d43b-160">DoNotInclude</span></span> |
<span data-ttu-id="7d43b-161">Mountain</span><span class="sxs-lookup"><span data-stu-id="7d43b-161">Mountain</span></span> | <span data-ttu-id="7d43b-162">Terreno</span><span class="sxs-lookup"><span data-stu-id="7d43b-162">Terrain</span></span> | <span data-ttu-id="7d43b-163">•</span><span class="sxs-lookup"><span data-stu-id="7d43b-163">•</span></span>
<span data-ttu-id="7d43b-164">Cabina</span><span class="sxs-lookup"><span data-stu-id="7d43b-164">Cabin</span></span> | <span data-ttu-id="7d43b-165">Strutture</span><span class="sxs-lookup"><span data-stu-id="7d43b-165">Structures</span></span> | <span data-ttu-id="7d43b-166">•</span><span class="sxs-lookup"><span data-stu-id="7d43b-166">•</span></span>
<span data-ttu-id="7d43b-167">Trees</span><span class="sxs-lookup"><span data-stu-id="7d43b-167">Trees</span></span> | <span data-ttu-id="7d43b-168">Vegetazione</span><span class="sxs-lookup"><span data-stu-id="7d43b-168">Vegetation</span></span> | <span data-ttu-id="7d43b-169">•</span><span class="sxs-lookup"><span data-stu-id="7d43b-169">•</span></span>

---

## <a name="editor-behavior"></a><span data-ttu-id="7d43b-170">Comportamento dell'editor</span><span class="sxs-lookup"><span data-stu-id="7d43b-170">Editor behavior</span></span>

<span data-ttu-id="7d43b-171">È possibile eseguire tutte queste operazioni nell'editor e in modalità di riproduzione usando il controllo dei servizi [del sistema di scena.](../../configuration/mixed-reality-configuration-guide.md#editor-utilities)</span><span class="sxs-lookup"><span data-stu-id="7d43b-171">You can perform all these operations in editor and in play mode by using the Scene System's [service inspector.](../../configuration/mixed-reality-configuration-guide.md#editor-utilities)</span></span> <span data-ttu-id="7d43b-172">In modalità di modifica i caricamenti della scena saranno istantanei, mentre in modalità di riproduzione è possibile osservare lo stato di avanzamento del caricamento e usare [i token di attivazione.](scene-system-load-progress.md)</span><span class="sxs-lookup"><span data-stu-id="7d43b-172">In edit mode scene loads will be instantaneous, while in play mode you can observe loading progress and use [activation tokens.](scene-system-load-progress.md)</span></span>

![Sistema di scena nel controllo con il caricamento del contenuto evidenziato](../images/scene-system/MRTK_SceneSystemServiceInspector.PNG)

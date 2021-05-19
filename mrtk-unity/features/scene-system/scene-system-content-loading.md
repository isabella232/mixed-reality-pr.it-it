---
title: Caricamento del contenuto del sistema della scena
description: Documentazione sul caricamento del sistema della scena con MRTK
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: f310b3687a6773404c7a998a3764163daf159857
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/19/2021
ms.locfileid: "110145141"
---
# <a name="content-scene-loading"></a><span data-ttu-id="9c04d-104">Caricamento della scena di contenuto</span><span class="sxs-lookup"><span data-stu-id="9c04d-104">Content scene loading</span></span>

<span data-ttu-id="9c04d-105">Tutte le operazioni di caricamento del contenuto sono asincrone e, per impostazione predefinita, tutto il caricamento del contenuto è additivo.</span><span class="sxs-lookup"><span data-stu-id="9c04d-105">All content load operations are asynchronous, and by default all content loading is additive.</span></span> <span data-ttu-id="9c04d-106">Le operazioni di caricamento del contenuto non hanno mai effetto sulle scene di gestione e di illuminazione.</span><span class="sxs-lookup"><span data-stu-id="9c04d-106">Manager and lighting scenes are never affected by content loading operations.</span></span> <span data-ttu-id="9c04d-107">Per informazioni sul monitoraggio dello stato di avanzamento del caricamento e dell'attivazione della scena, vedere [Monitoraggio del caricamento del contenuto.](scene-system-load-progress.md)</span><span class="sxs-lookup"><span data-stu-id="9c04d-107">For information about monitoring load progress and scene activation, see [Monitoring Content Loading](scene-system-load-progress.md).</span></span>

## <a name="loading-content"></a><span data-ttu-id="9c04d-108">Caricamento del contenuto</span><span class="sxs-lookup"><span data-stu-id="9c04d-108">Loading content</span></span>

<span data-ttu-id="9c04d-109">Per caricare scene di contenuto, usare il `LoadContent` metodo :</span><span class="sxs-lookup"><span data-stu-id="9c04d-109">To load content scenes use the `LoadContent` method:</span></span>

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

// Additively load a single content scene
await sceneSystem.LoadContent("MyContentScene");

// Additively load a set of content scenes
await sceneSystem.LoadContent(new string[] { "MyContentScene1", "MyContentScene2", "MyContentScene3" });
```

## <a name="single-scene-loading"></a><span data-ttu-id="9c04d-110">Caricamento di una singola scena</span><span class="sxs-lookup"><span data-stu-id="9c04d-110">Single scene loading</span></span>

<span data-ttu-id="9c04d-111">L'equivalente di un singolo carico della scena può essere ottenuto tramite l'argomento `mode` facoltativo .</span><span class="sxs-lookup"><span data-stu-id="9c04d-111">The equivalent of a single scene load can be achieved via the optional `mode` argument.</span></span> <span data-ttu-id="9c04d-112">`LoadSceneMode.Single` scarica tutte le scene di contenuto caricate prima di procedere con il caricamento.</span><span class="sxs-lookup"><span data-stu-id="9c04d-112">`LoadSceneMode.Single` will first unload all loaded content scenes before proceeding with the load.</span></span>

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

## <a name="next--previous-scene-loading"></a><span data-ttu-id="9c04d-113">Caricamento della scena successiva/precedente</span><span class="sxs-lookup"><span data-stu-id="9c04d-113">Next / previous scene loading</span></span>

<span data-ttu-id="9c04d-114">Il contenuto può essere caricato in ordine di indice di compilazione.</span><span class="sxs-lookup"><span data-stu-id="9c04d-114">Content can be singly loaded in order of build index.</span></span> <span data-ttu-id="9c04d-115">Ciò è utile per presentare le applicazioni che consentono agli utenti di eseguire una serie di scene dimostrativi una alla volta.</span><span class="sxs-lookup"><span data-stu-id="9c04d-115">This is useful for showcase applications that take users through a set of demonstration scenes one-by-one.</span></span>

![Scene correnti nella compilazione nelle impostazioni del lettore](../images/scene-system/MRTK_SceneSystemBuildSettings.png)

<span data-ttu-id="9c04d-117">Si noti che il caricamento del contenuto successivo/precedente usa LoadSceneMode.Single per impostazione predefinita per garantire che il contenuto precedente sia scaricato.</span><span class="sxs-lookup"><span data-stu-id="9c04d-117">Note that next / prev content loading uses LoadSceneMode.Single by default to ensure that the previous content is unloaded.</span></span>

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

<span data-ttu-id="9c04d-118">`PrevContentExists` restituirà true se è presente almeno una scena di contenuto con un indice di compilazione inferiore rispetto all'indice di compilazione più basso attualmente caricato.</span><span class="sxs-lookup"><span data-stu-id="9c04d-118">`PrevContentExists` will return true if there is at least one content scene that has a lower build index than the lowest build index currently loaded.</span></span> <span data-ttu-id="9c04d-119">`NextContentExists` restituirà true se è presente almeno una scena di contenuto con un indice di compilazione più alto rispetto all'indice di compilazione più alto attualmente caricato.</span><span class="sxs-lookup"><span data-stu-id="9c04d-119">`NextContentExists` will return true if there is at least one content scene that has a higher build index than the highest build index currently loaded.</span></span>

<span data-ttu-id="9c04d-120">Se `wrap` l'argomento è true, il contenuto torna all'indice della prima o dell'ultima compilazione.</span><span class="sxs-lookup"><span data-stu-id="9c04d-120">If the `wrap` argument is true, content will loop back to the first / last build index.</span></span> <span data-ttu-id="9c04d-121">In questo modo non è più necessario verificare il contenuto successivo o precedente:</span><span class="sxs-lookup"><span data-stu-id="9c04d-121">This removes the need to check for next / previous content:</span></span>

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

## <a name="loading-by-tag"></a><span data-ttu-id="9c04d-122">Caricamento in base al tag</span><span class="sxs-lookup"><span data-stu-id="9c04d-122">Loading by tag</span></span>

![Caricamento di scene di contenuto per tag](../images/scene-system/MRTK_SceneSystemLoadingByTag.png)

<span data-ttu-id="9c04d-124">A volte è consigliabile caricare scene di contenuto in gruppi.</span><span class="sxs-lookup"><span data-stu-id="9c04d-124">It's sometimes desirable to load content scenes in groups.</span></span> <span data-ttu-id="9c04d-125">Ad esempio, una fase di un'esperienza può essere costituita da più scene, che devono essere caricate contemporaneamente per funzionare.</span><span class="sxs-lookup"><span data-stu-id="9c04d-125">Eg, a stage of an experience may be composed of multiple scenes, all of which must be loaded simultaneously to function.</span></span> <span data-ttu-id="9c04d-126">Per semplificare questa operazione, è possibile contrassegnare le scene e quindi caricarle o scaricarle con tale tag.</span><span class="sxs-lookup"><span data-stu-id="9c04d-126">To facilitate this, you can tag your scenes and then load them or unload them with that tag.</span></span>

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

await LoadContentByTag("Stage1");

// Wait until stage 1 is complete

await UnloadContentByTag("Stage1");
await LoadContentByTag("Stage2);
```

<span data-ttu-id="9c04d-127">Il caricamento in base al tag può essere utile anche se gli autori vogliono incorporare/rimuovere elementi da un'esperienza senza dover modificare gli script.</span><span class="sxs-lookup"><span data-stu-id="9c04d-127">Loading by tag can also be useful if artists want to incorporate / remove elements from an experience without having to modify scripts.</span></span> <span data-ttu-id="9c04d-128">Ad esempio, l'esecuzione di questo script con i due set di tag seguenti produce risultati diversi:</span><span class="sxs-lookup"><span data-stu-id="9c04d-128">For instance, running this script with the following two sets of tags produces different results:</span></span>

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

await LoadContentByTag("Terrain");
await LoadContentByTag("Structures");
await LoadContentByTag("Vegetation");
```

### <a name="testing-content"></a><span data-ttu-id="9c04d-129">Test del contenuto</span><span class="sxs-lookup"><span data-stu-id="9c04d-129">Testing content</span></span>

<span data-ttu-id="9c04d-130">Nome scena</span><span class="sxs-lookup"><span data-stu-id="9c04d-130">Scene Name</span></span> | <span data-ttu-id="9c04d-131">Tag scena</span><span class="sxs-lookup"><span data-stu-id="9c04d-131">Scene Tag</span></span> | <span data-ttu-id="9c04d-132">Caricato dallo script</span><span class="sxs-lookup"><span data-stu-id="9c04d-132">Loaded by script</span></span>
---|---|---
<span data-ttu-id="9c04d-133">DebugPhysics</span><span class="sxs-lookup"><span data-stu-id="9c04d-133">DebugTerrainPhysics</span></span> | <span data-ttu-id="9c04d-134">Terreno</span><span class="sxs-lookup"><span data-stu-id="9c04d-134">Terrain</span></span> | <span data-ttu-id="9c04d-135">•</span><span class="sxs-lookup"><span data-stu-id="9c04d-135">•</span></span>
<span data-ttu-id="9c04d-136">StructureTesting</span><span class="sxs-lookup"><span data-stu-id="9c04d-136">StructureTesting</span></span> | <span data-ttu-id="9c04d-137">Strutture</span><span class="sxs-lookup"><span data-stu-id="9c04d-137">Structures</span></span> | <span data-ttu-id="9c04d-138">•</span><span class="sxs-lookup"><span data-stu-id="9c04d-138">•</span></span>
<span data-ttu-id="9c04d-139">Strumenti Disastrumenti</span><span class="sxs-lookup"><span data-stu-id="9c04d-139">VegetationTools</span></span> | <span data-ttu-id="9c04d-140">Vegetazione</span><span class="sxs-lookup"><span data-stu-id="9c04d-140">Vegetation</span></span> | <span data-ttu-id="9c04d-141">•</span><span class="sxs-lookup"><span data-stu-id="9c04d-141">•</span></span>
<span data-ttu-id="9c04d-142">Mountain</span><span class="sxs-lookup"><span data-stu-id="9c04d-142">Mountain</span></span> | <span data-ttu-id="9c04d-143">Terreno</span><span class="sxs-lookup"><span data-stu-id="9c04d-143">Terrain</span></span> | <span data-ttu-id="9c04d-144">•</span><span class="sxs-lookup"><span data-stu-id="9c04d-144">•</span></span>
<span data-ttu-id="9c04d-145">Cabina</span><span class="sxs-lookup"><span data-stu-id="9c04d-145">Cabin</span></span> | <span data-ttu-id="9c04d-146">Strutture</span><span class="sxs-lookup"><span data-stu-id="9c04d-146">Structures</span></span> | <span data-ttu-id="9c04d-147">•</span><span class="sxs-lookup"><span data-stu-id="9c04d-147">•</span></span>
<span data-ttu-id="9c04d-148">Trees</span><span class="sxs-lookup"><span data-stu-id="9c04d-148">Trees</span></span> | <span data-ttu-id="9c04d-149">Vegetazione</span><span class="sxs-lookup"><span data-stu-id="9c04d-149">Vegetation</span></span> | <span data-ttu-id="9c04d-150">•</span><span class="sxs-lookup"><span data-stu-id="9c04d-150">•</span></span>

### <a name="final-content"></a><span data-ttu-id="9c04d-151">Contenuto finale</span><span class="sxs-lookup"><span data-stu-id="9c04d-151">Final content</span></span>

<span data-ttu-id="9c04d-152">Nome scena</span><span class="sxs-lookup"><span data-stu-id="9c04d-152">Scene Name</span></span> | <span data-ttu-id="9c04d-153">Tag della scena</span><span class="sxs-lookup"><span data-stu-id="9c04d-153">Scene Tag</span></span> | <span data-ttu-id="9c04d-154">Caricato da script</span><span class="sxs-lookup"><span data-stu-id="9c04d-154">Loaded by script</span></span>
---|---|---
<span data-ttu-id="9c04d-155">DebugTerrainPhysics</span><span class="sxs-lookup"><span data-stu-id="9c04d-155">DebugTerrainPhysics</span></span> | <span data-ttu-id="9c04d-156">DoNotInclude</span><span class="sxs-lookup"><span data-stu-id="9c04d-156">DoNotInclude</span></span> |
<span data-ttu-id="9c04d-157">StructureTesting</span><span class="sxs-lookup"><span data-stu-id="9c04d-157">StructureTesting</span></span> | <span data-ttu-id="9c04d-158">DoNotInclude</span><span class="sxs-lookup"><span data-stu-id="9c04d-158">DoNotInclude</span></span> |
<span data-ttu-id="9c04d-159">Estrumenti di verde</span><span class="sxs-lookup"><span data-stu-id="9c04d-159">VegetationTools</span></span> | <span data-ttu-id="9c04d-160">DoNotInclude</span><span class="sxs-lookup"><span data-stu-id="9c04d-160">DoNotInclude</span></span> |
<span data-ttu-id="9c04d-161">Mountain</span><span class="sxs-lookup"><span data-stu-id="9c04d-161">Mountain</span></span> | <span data-ttu-id="9c04d-162">Terreno</span><span class="sxs-lookup"><span data-stu-id="9c04d-162">Terrain</span></span> | <span data-ttu-id="9c04d-163">•</span><span class="sxs-lookup"><span data-stu-id="9c04d-163">•</span></span>
<span data-ttu-id="9c04d-164">Cabina</span><span class="sxs-lookup"><span data-stu-id="9c04d-164">Cabin</span></span> | <span data-ttu-id="9c04d-165">Strutture</span><span class="sxs-lookup"><span data-stu-id="9c04d-165">Structures</span></span> | <span data-ttu-id="9c04d-166">•</span><span class="sxs-lookup"><span data-stu-id="9c04d-166">•</span></span>
<span data-ttu-id="9c04d-167">Trees</span><span class="sxs-lookup"><span data-stu-id="9c04d-167">Trees</span></span> | <span data-ttu-id="9c04d-168">Vegetazione</span><span class="sxs-lookup"><span data-stu-id="9c04d-168">Vegetation</span></span> | <span data-ttu-id="9c04d-169">•</span><span class="sxs-lookup"><span data-stu-id="9c04d-169">•</span></span>

---

## <a name="editor-behavior"></a><span data-ttu-id="9c04d-170">Comportamento dell'editor</span><span class="sxs-lookup"><span data-stu-id="9c04d-170">Editor behavior</span></span>

<span data-ttu-id="9c04d-171">È possibile eseguire tutte queste operazioni nell'editor e in modalità di riproduzione usando il controllo dei servizi [del sistema di scena.](../../configuration/mixed-reality-configuration-guide.md#editor-utilities)</span><span class="sxs-lookup"><span data-stu-id="9c04d-171">You can perform all these operations in editor and in play mode by using the Scene System's [service inspector.](../../configuration/mixed-reality-configuration-guide.md#editor-utilities)</span></span> <span data-ttu-id="9c04d-172">In modalità di modifica i caricamenti della scena saranno istantanei, mentre in modalità di riproduzione è possibile osservare lo stato di avanzamento del caricamento e usare [i token di attivazione.](scene-system-load-progress.md)</span><span class="sxs-lookup"><span data-stu-id="9c04d-172">In edit mode scene loads will be instantaneous, while in play mode you can observe loading progress and use [activation tokens.](scene-system-load-progress.md)</span></span>

![Sistema di scena nel controllo con il caricamento del contenuto evidenziato](../images/scene-system/MRTK_SceneSystemServiceInspector.PNG)

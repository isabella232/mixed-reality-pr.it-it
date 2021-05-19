---
title: Stato di caricamento del sistema della scena
description: Documentazione sul caricamento del contenuto delle scene in MRTK
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: 51b5d4d00d65491a0476068bbdc256ffce67412b
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144406"
---
# <a name="monitoring-content-loading"></a><span data-ttu-id="f9d09-104">Monitoraggio del caricamento del contenuto</span><span class="sxs-lookup"><span data-stu-id="f9d09-104">Monitoring content loading</span></span>

## <a name="scene-operation-progress"></a><span data-ttu-id="f9d09-105">Stato dell'operazione della scena</span><span class="sxs-lookup"><span data-stu-id="f9d09-105">Scene operation progress</span></span>

<span data-ttu-id="f9d09-106">Quando il contenuto viene caricato o scaricato, la `SceneOperationInProgress` proprietà restituirà true.</span><span class="sxs-lookup"><span data-stu-id="f9d09-106">When content is being loaded or unloaded, the `SceneOperationInProgress` property will return true.</span></span> <span data-ttu-id="f9d09-107">È possibile monitorare lo stato di avanzamento di questa operazione tramite la `SceneOperationProgress` proprietà .</span><span class="sxs-lookup"><span data-stu-id="f9d09-107">You can monitor the progress of this operation via the `SceneOperationProgress` property.</span></span>

<span data-ttu-id="f9d09-108">Il `SceneOperationProgress` valore è la media di tutte le operazioni correnti della scena asincrona.</span><span class="sxs-lookup"><span data-stu-id="f9d09-108">The `SceneOperationProgress` value is the average of all current async scene operations.</span></span> <span data-ttu-id="f9d09-109">All'inizio di un caricamento del contenuto, `SceneOperationProgress` sarà zero.</span><span class="sxs-lookup"><span data-stu-id="f9d09-109">At the start of a content load, `SceneOperationProgress` will be zero.</span></span> <span data-ttu-id="f9d09-110">Al termine, `SceneOperationProgress` verrà impostato su 1 e rimarrà su 1 fino a quando non verrà eseguita l'operazione successiva.</span><span class="sxs-lookup"><span data-stu-id="f9d09-110">Once fully completed, `SceneOperationProgress` will be set to 1 and will remain at 1 until the next operation takes place.</span></span> <span data-ttu-id="f9d09-111">Si noti che solo le operazioni della scena di contenuto influiscono su queste proprietà.</span><span class="sxs-lookup"><span data-stu-id="f9d09-111">Note that only content scene operations affect these properties.</span></span>

<span data-ttu-id="f9d09-112">Queste proprietà riflettono lo stato di *un'intera operazione* dall'inizio alla fine, anche se tale operazione include più passaggi:</span><span class="sxs-lookup"><span data-stu-id="f9d09-112">These properties reflect the state of an *entire operation* from start to finish, even if that operation includes multiple steps:</span></span>

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

// First do an additive scene load
// SceneOperationInProgress will be true for the duration of this operation
// SceneOperationProgress will show 0-1 as it completes
await sceneSystem.LoadContent("ContentScene1");

// Now do a single scene load
// This will result in two actions back-to-back
// First "ContentScene1" will be unloaded
// Then "ContentScene2" will be loaded
// SceneOperationInProgress will be true for the duration of this operation
// SceneOperationProgress will show 0-1 as it completes
sceneSystem.LoadContent("ContentScene2", LoadSceneMode.Single)
```

### <a name="progress-examples"></a><span data-ttu-id="f9d09-113">Esempi di stato</span><span class="sxs-lookup"><span data-stu-id="f9d09-113">Progress examples</span></span>

<span data-ttu-id="f9d09-114">`SceneOperationInProgress` può essere utile se l'attività deve essere sospesa durante il caricamento del contenuto:</span><span class="sxs-lookup"><span data-stu-id="f9d09-114">`SceneOperationInProgress` can be useful if activity should be suspended while content is being loaded:</span></span>

```c#
public class FooManager : MonoBehaviour
{
    private void Update()
    {
        IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

        // Don't update foos while a scene operation is in progress
        if (sceneSystem.SceneOperationInProgress)
        {
            return;
        }

        // Update foos
        ...
    }
    ...
}
```

<span data-ttu-id="f9d09-115">`SceneOperationProgress` può essere usato per visualizzare le finestre di dialogo di stato:</span><span class="sxs-lookup"><span data-stu-id="f9d09-115">`SceneOperationProgress` can be used to display progress dialogs:</span></span>

```c#
public class ProgressDialog : MonoBehaviour
{
    private void Update()
    {
        IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

        if (sceneSystem.SceneOperationInProgress)
        {
            DisplayProgressIndicator(sceneSystem.SceneOperationProgress);
        }
        else
        {
            HideProgressIndicator();
        }
    }
    ...
}
```

---

## <a name="monitoring-with-actions"></a><span data-ttu-id="f9d09-116">Monitoraggio con azioni</span><span class="sxs-lookup"><span data-stu-id="f9d09-116">Monitoring with actions</span></span>

<span data-ttu-id="f9d09-117">Scene System (Sistema scena) fornisce diverse azioni per sapere quando le scene vengono caricate o scaricate.</span><span class="sxs-lookup"><span data-stu-id="f9d09-117">The Scene System provides several actions to let you know when scenes are being loaded or unloaded.</span></span> <span data-ttu-id="f9d09-118">Ogni azione inoltra il nome della scena interessata.</span><span class="sxs-lookup"><span data-stu-id="f9d09-118">Each action relays the name of the affected scene.</span></span>

<span data-ttu-id="f9d09-119">Se un'operazione di caricamento o scaricamento include più scene, le azioni pertinenti verranno richiamate una volta per ogni scena interessata.</span><span class="sxs-lookup"><span data-stu-id="f9d09-119">If a load or unload operation involves multiple scenes, the relevant actions will be invoked once per affected scene.</span></span> <span data-ttu-id="f9d09-120">Vengono inoltre richiamati tutti contemporaneamente quando l'operazione di caricamento o scaricamento è *stata completata completamente.*</span><span class="sxs-lookup"><span data-stu-id="f9d09-120">They are also invoked all at once when the load or unload operation is *fully completed.*</span></span> <span data-ttu-id="f9d09-121">Per questo motivo è consigliabile usare le azioni *OnWillUnload* per rilevare il contenuto che verrà eliminato in modo eliminato, anziché usare le azioni *OnUnloaded* per rilevare il contenuto eliminato dopo il fatto. </span><span class="sxs-lookup"><span data-stu-id="f9d09-121">For this reason it's recommended that you use *OnWillUnload* actions to detect content that *will* be destroyed, as opposed to using *OnUnloaded* actions to detect destroyed content after the fact.</span></span>

<span data-ttu-id="f9d09-122">Sul lato opposto, poiché le azioni *OnLoaded* vengono richiamate solo quando tutte le scene sono attivate e caricate completamente, l'uso delle azioni *OnLoaded* per rilevare e usare il nuovo contenuto è garantito come sicuro.</span><span class="sxs-lookup"><span data-stu-id="f9d09-122">On the flip side, because *OnLoaded* actions are only invoked when all scenes are activated and fully loaded, using *OnLoaded* actions to detect and use new content is guaranteed to be safe.</span></span>

<span data-ttu-id="f9d09-123">Azione</span><span class="sxs-lookup"><span data-stu-id="f9d09-123">Action</span></span> | <span data-ttu-id="f9d09-124">Quando viene richiamato</span><span class="sxs-lookup"><span data-stu-id="f9d09-124">When it's invoked</span></span> | <span data-ttu-id="f9d09-125">Scene di contenuto</span><span class="sxs-lookup"><span data-stu-id="f9d09-125">Content Scenes</span></span> | <span data-ttu-id="f9d09-126">Scene di illuminazione</span><span class="sxs-lookup"><span data-stu-id="f9d09-126">Lighting Scenes</span></span> | <span data-ttu-id="f9d09-127">Scene di gestione</span><span class="sxs-lookup"><span data-stu-id="f9d09-127">Manager Scenes</span></span>
--- | --- | --- | --- | --- | ---
`OnWillLoadContent` | <span data-ttu-id="f9d09-128">Poco prima del caricamento di una scena di contenuto</span><span class="sxs-lookup"><span data-stu-id="f9d09-128">Just prior to a content scene load</span></span> | <span data-ttu-id="f9d09-129">•</span><span class="sxs-lookup"><span data-stu-id="f9d09-129">•</span></span> | |  
`OnContentLoaded` | <span data-ttu-id="f9d09-130">Dopo che tutte le scene di contenuto in un'operazione di caricamento sono state completamente caricate e attivate</span><span class="sxs-lookup"><span data-stu-id="f9d09-130">After all content scenes in a load operation have been fully loaded and activated</span></span> | <span data-ttu-id="f9d09-131">•</span><span class="sxs-lookup"><span data-stu-id="f9d09-131">•</span></span> | |
`OnWillUnloadContent` | <span data-ttu-id="f9d09-132">Poco prima di un'operazione di scaricamento di una scena di contenuto</span><span class="sxs-lookup"><span data-stu-id="f9d09-132">Just prior to a content scene unload operation</span></span> | <span data-ttu-id="f9d09-133">•</span><span class="sxs-lookup"><span data-stu-id="f9d09-133">•</span></span> | |
`OnContentUnloaded` | <span data-ttu-id="f9d09-134">Dopo che tutte le scene di contenuto in un'operazione di scaricamento sono state scaricate completamente</span><span class="sxs-lookup"><span data-stu-id="f9d09-134">After all content scenes in an unload operation have been fully unloaded</span></span> | <span data-ttu-id="f9d09-135">•</span><span class="sxs-lookup"><span data-stu-id="f9d09-135">•</span></span> | |
`OnWillLoadLighting` | <span data-ttu-id="f9d09-136">Poco prima del caricamento di una scena di illuminazione</span><span class="sxs-lookup"><span data-stu-id="f9d09-136">Just prior to a lighting scene load</span></span> | | <span data-ttu-id="f9d09-137">•</span><span class="sxs-lookup"><span data-stu-id="f9d09-137">•</span></span> |
`OnLightingLoaded` | <span data-ttu-id="f9d09-138">Dopo che una scena di illuminazione è stata completamente caricata e attivata</span><span class="sxs-lookup"><span data-stu-id="f9d09-138">After a lighting scene has been fully loaded and activated</span></span>| | <span data-ttu-id="f9d09-139">•</span><span class="sxs-lookup"><span data-stu-id="f9d09-139">•</span></span> |
`OnWillUnloadLighting` | <span data-ttu-id="f9d09-140">Poco prima dello scaricamento di una scena di illuminazione</span><span class="sxs-lookup"><span data-stu-id="f9d09-140">Just prior to a lighting scene unload</span></span> | | <span data-ttu-id="f9d09-141">•</span><span class="sxs-lookup"><span data-stu-id="f9d09-141">•</span></span> |
`OnLightingUnloaded` | <span data-ttu-id="f9d09-142">Dopo che una scena di illuminazione è stata scaricata completamente</span><span class="sxs-lookup"><span data-stu-id="f9d09-142">After a lighting scene has been fully unloaded</span></span> | | <span data-ttu-id="f9d09-143">•</span><span class="sxs-lookup"><span data-stu-id="f9d09-143">•</span></span> |
`OnWillLoadScene` | <span data-ttu-id="f9d09-144">Poco prima del caricamento di una scena</span><span class="sxs-lookup"><span data-stu-id="f9d09-144">Just prior to a scene load</span></span> | <span data-ttu-id="f9d09-145">•</span><span class="sxs-lookup"><span data-stu-id="f9d09-145">•</span></span> | <span data-ttu-id="f9d09-146">•</span><span class="sxs-lookup"><span data-stu-id="f9d09-146">•</span></span> | <span data-ttu-id="f9d09-147">•</span><span class="sxs-lookup"><span data-stu-id="f9d09-147">•</span></span>
`OnSceneLoaded` | <span data-ttu-id="f9d09-148">Dopo che tutte le scene di un'operazione sono state caricate e attivate</span><span class="sxs-lookup"><span data-stu-id="f9d09-148">After all scenes in an operation are fully loaded and activated</span></span> | <span data-ttu-id="f9d09-149">•</span><span class="sxs-lookup"><span data-stu-id="f9d09-149">•</span></span> | <span data-ttu-id="f9d09-150">•</span><span class="sxs-lookup"><span data-stu-id="f9d09-150">•</span></span> | <span data-ttu-id="f9d09-151">•</span><span class="sxs-lookup"><span data-stu-id="f9d09-151">•</span></span>
`OnWillUnloadScene` | <span data-ttu-id="f9d09-152">Poco prima dello scaricamento di una scena</span><span class="sxs-lookup"><span data-stu-id="f9d09-152">Just prior to a scene unload</span></span> | <span data-ttu-id="f9d09-153">•</span><span class="sxs-lookup"><span data-stu-id="f9d09-153">•</span></span> | <span data-ttu-id="f9d09-154">•</span><span class="sxs-lookup"><span data-stu-id="f9d09-154">•</span></span> | <span data-ttu-id="f9d09-155">•</span><span class="sxs-lookup"><span data-stu-id="f9d09-155">•</span></span>
`OnSceneUnloaded` | <span data-ttu-id="f9d09-156">Dopo che una scena è stata scaricata completamente</span><span class="sxs-lookup"><span data-stu-id="f9d09-156">After a scene is fully unloaded</span></span> |  <span data-ttu-id="f9d09-157">•</span><span class="sxs-lookup"><span data-stu-id="f9d09-157">•</span></span> | <span data-ttu-id="f9d09-158">•</span><span class="sxs-lookup"><span data-stu-id="f9d09-158">•</span></span> | <span data-ttu-id="f9d09-159">•</span><span class="sxs-lookup"><span data-stu-id="f9d09-159">•</span></span>

### <a name="action-examples"></a><span data-ttu-id="f9d09-160">Esempi di azioni</span><span class="sxs-lookup"><span data-stu-id="f9d09-160">Action examples</span></span>

<span data-ttu-id="f9d09-161">Un altro esempio di finestra di dialogo di stato che usa azioni e una coroutine invece di Update:</span><span class="sxs-lookup"><span data-stu-id="f9d09-161">Another progress dialog example using actions and a coroutine instead of Update:</span></span>

```c#
public class ProgressDialog : MonoBehaviour
{
    private bool displayingProgress = false;

    private void Start()
    {
        IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();
        sceneSystem.OnWillLoadContent += HandleSceneOperation;
        sceneSystem.OnWillUnloadContent += HandleSceneOperation;
    }

    private void HandleSceneOperation (string sceneName)
    {
        // This may be invoked multiple times per frame - once per scene being loaded or unloaded.
        // So filter the events appropriately.
        if (displayingProgress)
        {
            return;
        }

        displayingProgress = true;
        StartCoroutine(DisplayProgress());
    }

    private IEnumerator DisplayProgress()
    {
        IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

        while (sceneSystem.SceneOperationInProgress)
        {
            DisplayProgressIndicator(sceneSystem.SceneOperationProgress);
            yield return null;
        }

        HideProgressIndicator();
        displayingProgress = false;
    }

    ...
}
```

---

## <a name="controlling-scene-activation"></a><span data-ttu-id="f9d09-162">Controllo dell'attivazione della scena</span><span class="sxs-lookup"><span data-stu-id="f9d09-162">Controlling scene activation</span></span>

<span data-ttu-id="f9d09-163">Per impostazione predefinita, le scene di contenuto sono impostate per l'attivazione quando vengono caricate.</span><span class="sxs-lookup"><span data-stu-id="f9d09-163">By default content scenes are set to activate when loaded.</span></span> <span data-ttu-id="f9d09-164">Se si vuole controllare manualmente l'attivazione della scena, è possibile passare a `SceneActivationToken` qualsiasi metodo di caricamento del contenuto.</span><span class="sxs-lookup"><span data-stu-id="f9d09-164">If you want to control scene activation manually, you can pass a `SceneActivationToken` to any content load method.</span></span> <span data-ttu-id="f9d09-165">Se più scene di contenuto vengono caricate da una singola operazione, questo token di attivazione verrà applicato a tutte le scene.</span><span class="sxs-lookup"><span data-stu-id="f9d09-165">If multiple content scenes are being loaded by a single operation, this activation token will apply to all scenes.</span></span>

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

SceneActivationToken activationToken = new SceneActivationToken();

// Load the content and pass the activation token
sceneSystem.LoadContent(new string[] { "ContentScene1", "ContentScene2", "ContentScene3" }, LoadSceneMode.Additive, activationToken);

// Wait until all users have joined the experience
while (!AllUsersHaveJoinedExperience())
{
    await Task.Yield();
}

// Let scene system know we're ready to activate all scenes
activationToken.AllowSceneActivation = true;

// Wait for all scenes to be fully loaded and activated
while (sceneSystem.SceneOperationInProgress)
{
    await Task.Yield();
}

// Proceed with experience
```

---

## <a name="checking-which-content-is-loaded"></a><span data-ttu-id="f9d09-166">Controllo del contenuto caricato</span><span class="sxs-lookup"><span data-stu-id="f9d09-166">Checking which content is loaded</span></span>

<span data-ttu-id="f9d09-167">La `ContentSceneNames` proprietà fornisce una matrice di scene di contenuto disponibili in ordine di indice di compilazione.</span><span class="sxs-lookup"><span data-stu-id="f9d09-167">The `ContentSceneNames` property provides an array of available content scenes in order of build index.</span></span> <span data-ttu-id="f9d09-168">È possibile controllare se queste scene vengono caricate tramite `IsContentLoaded(string contentName)` .</span><span class="sxs-lookup"><span data-stu-id="f9d09-168">You can check whether these scenes are loaded via `IsContentLoaded(string contentName)`.</span></span>

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

string[] contentSceneNames = sceneSystem.ContentSceneNames;
bool[] loadStatus = new bool[contentSceneNames.Length];

for (int i = 0; i < contentSceneNames.Length; i++>)
{
    loadStatus[i] = sceneSystem.IsContentLoaded(contentSceneNames[i]);
}
```

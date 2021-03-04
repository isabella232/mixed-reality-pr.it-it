---
title: SceneSystemLoadProgress
description: Documentazione sul caricamento del contenuto di scene in MRTK
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: ec0b82a0393b6129d5b4c6fe562845234c52eb44
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/03/2021
ms.locfileid: "101781525"
---
# <a name="monitoring-content-loading"></a><span data-ttu-id="9887b-104">Monitoraggio del caricamento del contenuto</span><span class="sxs-lookup"><span data-stu-id="9887b-104">Monitoring content loading</span></span>

## <a name="scene-operation-progress"></a><span data-ttu-id="9887b-105">Stato operazione scena</span><span class="sxs-lookup"><span data-stu-id="9887b-105">Scene operation progress</span></span>

<span data-ttu-id="9887b-106">Quando il contenuto viene caricato o scaricato, la `SceneOperationInProgress` proprietà restituirà true.</span><span class="sxs-lookup"><span data-stu-id="9887b-106">When content is being loaded or unloaded, the `SceneOperationInProgress` property will return true.</span></span> <span data-ttu-id="9887b-107">È possibile monitorare lo stato di avanzamento di questa operazione tramite la `SceneOperationProgress` Proprietà.</span><span class="sxs-lookup"><span data-stu-id="9887b-107">You can monitor the progress of this operation via the `SceneOperationProgress` property.</span></span>

<span data-ttu-id="9887b-108">Il `SceneOperationProgress` valore è la media di tutte le operazioni di scena asincrone correnti.</span><span class="sxs-lookup"><span data-stu-id="9887b-108">The `SceneOperationProgress` value is the average of all current async scene operations.</span></span> <span data-ttu-id="9887b-109">All'inizio di un carico di contenuto, `SceneOperationProgress` sarà zero.</span><span class="sxs-lookup"><span data-stu-id="9887b-109">At the start of a content load, `SceneOperationProgress` will be zero.</span></span> <span data-ttu-id="9887b-110">Una volta completata `SceneOperationProgress` l'operazione, verrà impostata su 1 e rimarrà su 1 fino a quando non verrà eseguita l'operazione successiva.</span><span class="sxs-lookup"><span data-stu-id="9887b-110">Once fully completed, `SceneOperationProgress` will be set to 1 and will remain at 1 until the next operation takes place.</span></span> <span data-ttu-id="9887b-111">Si noti che solo le operazioni della scena del contenuto influiscono su queste proprietà.</span><span class="sxs-lookup"><span data-stu-id="9887b-111">Note that only content scene operations affect these properties.</span></span>

<span data-ttu-id="9887b-112">Queste proprietà riflettono lo stato di un' *intera operazione* dall'inizio alla fine, anche se tale operazione include più passaggi:</span><span class="sxs-lookup"><span data-stu-id="9887b-112">These properties reflect the state of an *entire operation* from start to finish, even if that operation includes multiple steps:</span></span>

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

### <a name="progress-examples"></a><span data-ttu-id="9887b-113">Esempi di stato</span><span class="sxs-lookup"><span data-stu-id="9887b-113">Progress examples</span></span>

<span data-ttu-id="9887b-114">`SceneOperationInProgress` può essere utile se l'attività deve essere sospesa durante il caricamento del contenuto:</span><span class="sxs-lookup"><span data-stu-id="9887b-114">`SceneOperationInProgress` can be useful if activity should be suspended while content is being loaded:</span></span>

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

<span data-ttu-id="9887b-115">`SceneOperationProgress` consente di visualizzare le finestre di dialogo dello stato di avanzamento:</span><span class="sxs-lookup"><span data-stu-id="9887b-115">`SceneOperationProgress` can be used to display progress dialogs:</span></span>

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

## <a name="monitoring-with-actions"></a><span data-ttu-id="9887b-116">Monitoraggio con azioni</span><span class="sxs-lookup"><span data-stu-id="9887b-116">Monitoring with actions</span></span>

<span data-ttu-id="9887b-117">Il sistema di scena fornisce diverse azioni che consentono di stabilire quando vengono caricate o scaricate scene.</span><span class="sxs-lookup"><span data-stu-id="9887b-117">The Scene System provides several actions to let you know when scenes are being loaded or unloaded.</span></span> <span data-ttu-id="9887b-118">Ogni azione inoltra il nome della scena interessata.</span><span class="sxs-lookup"><span data-stu-id="9887b-118">Each action relays the name of the affected scene.</span></span>

<span data-ttu-id="9887b-119">Se un'operazione di caricamento o scaricamento prevede più scene, le azioni rilevanti verranno richiamate una volta per ogni scena interessata.</span><span class="sxs-lookup"><span data-stu-id="9887b-119">If a load or unload operation involves multiple scenes, the relevant actions will be invoked once per affected scene.</span></span> <span data-ttu-id="9887b-120">Vengono richiamati tutti contemporaneamente quando l'operazione di caricamento o scaricamento viene *completata completamente.*</span><span class="sxs-lookup"><span data-stu-id="9887b-120">They are also invoked all at once when the load or unload operation is *fully completed.*</span></span> <span data-ttu-id="9887b-121">Per questo motivo è consigliabile usare le azioni *OnWillUnload* per rilevare il contenuto che *verrà* eliminato definitivamente, invece di usare le azioni *OnUnloaded* per rilevare il contenuto distrutto dopo il fatto.</span><span class="sxs-lookup"><span data-stu-id="9887b-121">For this reason it's recommended that you use *OnWillUnload* actions to detect content that *will* be destroyed, as opposed to using *OnUnloaded* actions to detect destroyed content after the fact.</span></span>

<span data-ttu-id="9887b-122">Sul lato flip, poiché le azioni *OnLoaded* vengono richiamate solo quando tutte le scene sono attivate e completamente caricate, l'uso di azioni *OnLoaded* per rilevare e usare nuovi contenuti è sicuramente sicuro.</span><span class="sxs-lookup"><span data-stu-id="9887b-122">On the flip side, because *OnLoaded* actions are only invoked when all scenes are activated and fully loaded, using *OnLoaded* actions to detect and use new content is guaranteed to be safe.</span></span>

<span data-ttu-id="9887b-123">Azione</span><span class="sxs-lookup"><span data-stu-id="9887b-123">Action</span></span> | <span data-ttu-id="9887b-124">Quando viene richiamato</span><span class="sxs-lookup"><span data-stu-id="9887b-124">When it's invoked</span></span> | <span data-ttu-id="9887b-125">Scene di contenuto</span><span class="sxs-lookup"><span data-stu-id="9887b-125">Content Scenes</span></span> | <span data-ttu-id="9887b-126">Scene di illuminazione</span><span class="sxs-lookup"><span data-stu-id="9887b-126">Lighting Scenes</span></span> | <span data-ttu-id="9887b-127">Scene di gestione</span><span class="sxs-lookup"><span data-stu-id="9887b-127">Manager Scenes</span></span>
--- | --- | --- | --- | --- | ---
`OnWillLoadContent` | <span data-ttu-id="9887b-128">Appena prima del caricamento di una scena del contenuto</span><span class="sxs-lookup"><span data-stu-id="9887b-128">Just prior to a content scene load</span></span> | <span data-ttu-id="9887b-129">•</span><span class="sxs-lookup"><span data-stu-id="9887b-129">•</span></span> | |  
`OnContentLoaded` | <span data-ttu-id="9887b-130">Dopo che tutte le scene di contenuto in un'operazione di caricamento sono state completamente caricate e attivate</span><span class="sxs-lookup"><span data-stu-id="9887b-130">After all content scenes in a load operation have been fully loaded and activated</span></span> | <span data-ttu-id="9887b-131">•</span><span class="sxs-lookup"><span data-stu-id="9887b-131">•</span></span> | |
`OnWillUnloadContent` | <span data-ttu-id="9887b-132">Appena prima di un'operazione di scaricamento della scena del contenuto</span><span class="sxs-lookup"><span data-stu-id="9887b-132">Just prior to a content scene unload operation</span></span> | <span data-ttu-id="9887b-133">•</span><span class="sxs-lookup"><span data-stu-id="9887b-133">•</span></span> | |
`OnContentUnloaded` | <span data-ttu-id="9887b-134">Dopo che tutte le scene di contenuto in un'operazione di scaricamento sono state completamente scaricate</span><span class="sxs-lookup"><span data-stu-id="9887b-134">After all content scenes in an unload operation have been fully unloaded</span></span> | <span data-ttu-id="9887b-135">•</span><span class="sxs-lookup"><span data-stu-id="9887b-135">•</span></span> | |
`OnWillLoadLighting` | <span data-ttu-id="9887b-136">Appena prima del caricamento di una scena di illuminazione</span><span class="sxs-lookup"><span data-stu-id="9887b-136">Just prior to a lighting scene load</span></span> | | <span data-ttu-id="9887b-137">•</span><span class="sxs-lookup"><span data-stu-id="9887b-137">•</span></span> |
`OnLightingLoaded` | <span data-ttu-id="9887b-138">Dopo che una scena di illuminazione è stata completamente caricata e attivata</span><span class="sxs-lookup"><span data-stu-id="9887b-138">After a lighting scene has been fully loaded and activated</span></span>| | <span data-ttu-id="9887b-139">•</span><span class="sxs-lookup"><span data-stu-id="9887b-139">•</span></span> |
`OnWillUnloadLighting` | <span data-ttu-id="9887b-140">Immediatamente prima dello scaricamento di una scena di illuminazione</span><span class="sxs-lookup"><span data-stu-id="9887b-140">Just prior to a lighting scene unload</span></span> | | <span data-ttu-id="9887b-141">•</span><span class="sxs-lookup"><span data-stu-id="9887b-141">•</span></span> |
`OnLightingUnloaded` | <span data-ttu-id="9887b-142">Dopo che una scena di illuminazione è stata completamente scaricata</span><span class="sxs-lookup"><span data-stu-id="9887b-142">After a lighting scene has been fully unloaded</span></span> | | <span data-ttu-id="9887b-143">•</span><span class="sxs-lookup"><span data-stu-id="9887b-143">•</span></span> |
`OnWillLoadScene` | <span data-ttu-id="9887b-144">Appena prima del caricamento di una scena</span><span class="sxs-lookup"><span data-stu-id="9887b-144">Just prior to a scene load</span></span> | <span data-ttu-id="9887b-145">•</span><span class="sxs-lookup"><span data-stu-id="9887b-145">•</span></span> | <span data-ttu-id="9887b-146">•</span><span class="sxs-lookup"><span data-stu-id="9887b-146">•</span></span> | <span data-ttu-id="9887b-147">•</span><span class="sxs-lookup"><span data-stu-id="9887b-147">•</span></span>
`OnSceneLoaded` | <span data-ttu-id="9887b-148">Dopo che tutte le scene in un'operazione sono state completamente caricate e attivate</span><span class="sxs-lookup"><span data-stu-id="9887b-148">After all scenes in an operation are fully loaded and activated</span></span> | <span data-ttu-id="9887b-149">•</span><span class="sxs-lookup"><span data-stu-id="9887b-149">•</span></span> | <span data-ttu-id="9887b-150">•</span><span class="sxs-lookup"><span data-stu-id="9887b-150">•</span></span> | <span data-ttu-id="9887b-151">•</span><span class="sxs-lookup"><span data-stu-id="9887b-151">•</span></span>
`OnWillUnloadScene` | <span data-ttu-id="9887b-152">Immediatamente prima dello scaricamento di una scena</span><span class="sxs-lookup"><span data-stu-id="9887b-152">Just prior to a scene unload</span></span> | <span data-ttu-id="9887b-153">•</span><span class="sxs-lookup"><span data-stu-id="9887b-153">•</span></span> | <span data-ttu-id="9887b-154">•</span><span class="sxs-lookup"><span data-stu-id="9887b-154">•</span></span> | <span data-ttu-id="9887b-155">•</span><span class="sxs-lookup"><span data-stu-id="9887b-155">•</span></span>
`OnSceneUnloaded` | <span data-ttu-id="9887b-156">Quando una scena è completamente scaricata</span><span class="sxs-lookup"><span data-stu-id="9887b-156">After a scene is fully unloaded</span></span> |  <span data-ttu-id="9887b-157">•</span><span class="sxs-lookup"><span data-stu-id="9887b-157">•</span></span> | <span data-ttu-id="9887b-158">•</span><span class="sxs-lookup"><span data-stu-id="9887b-158">•</span></span> | <span data-ttu-id="9887b-159">•</span><span class="sxs-lookup"><span data-stu-id="9887b-159">•</span></span>

### <a name="action-examples"></a><span data-ttu-id="9887b-160">Esempi di azione</span><span class="sxs-lookup"><span data-stu-id="9887b-160">Action examples</span></span>

<span data-ttu-id="9887b-161">Un altro esempio di finestra di dialogo di stato usando le azioni e una coroutine anziché Update:</span><span class="sxs-lookup"><span data-stu-id="9887b-161">Another progress dialog example using actions and a coroutine instead of Update:</span></span>

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

## <a name="controlling-scene-activation"></a><span data-ttu-id="9887b-162">Controllo dell'attivazione della scena</span><span class="sxs-lookup"><span data-stu-id="9887b-162">Controlling scene activation</span></span>

<span data-ttu-id="9887b-163">Per impostazione predefinita, le scene di contenuto sono impostate per l'attivazione al caricamento.</span><span class="sxs-lookup"><span data-stu-id="9887b-163">By default content scenes are set to activate when loaded.</span></span> <span data-ttu-id="9887b-164">Se si desidera controllare manualmente l'attivazione della scena, è possibile passare un oggetto `SceneActivationToken` a qualsiasi metodo di caricamento del contenuto.</span><span class="sxs-lookup"><span data-stu-id="9887b-164">If you want to control scene activation manually, you can pass a `SceneActivationToken` to any content load method.</span></span> <span data-ttu-id="9887b-165">Se più scene di contenuto vengono caricate da una singola operazione, questo token di attivazione verrà applicato a tutte le scene.</span><span class="sxs-lookup"><span data-stu-id="9887b-165">If multiple content scenes are being loaded by a single operation, this activation token will apply to all scenes.</span></span>

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

## <a name="checking-which-content-is-loaded"></a><span data-ttu-id="9887b-166">Verifica del contenuto caricato</span><span class="sxs-lookup"><span data-stu-id="9887b-166">Checking which content is loaded</span></span>

<span data-ttu-id="9887b-167">La `ContentSceneNames` proprietà fornisce una matrice di scene di contenuto disponibili nell'ordine dell'indice di compilazione.</span><span class="sxs-lookup"><span data-stu-id="9887b-167">The `ContentSceneNames` property provides an array of available content scenes in order of build index.</span></span> <span data-ttu-id="9887b-168">È possibile verificare se queste scene sono state caricate tramite `IsContentLoaded(string contentName)` .</span><span class="sxs-lookup"><span data-stu-id="9887b-168">You can check whether these scenes are loaded via `IsContentLoaded(string contentName)`.</span></span>

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

string[] contentSceneNames = sceneSystem.ContentSceneNames;
bool[] loadStatus = new bool[contentSceneNames.Length];

for (int i = 0; i < contentSceneNames.Length; i++>)
{
    loadStatus[i] = sceneSystem.IsContentLoaded(contentSceneNames[i]);
}
```

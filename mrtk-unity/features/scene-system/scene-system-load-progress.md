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
# <a name="monitoring-content-loading"></a>Monitoraggio del caricamento del contenuto

## <a name="scene-operation-progress"></a>Stato dell'operazione della scena

Quando il contenuto viene caricato o scaricato, la `SceneOperationInProgress` proprietà restituirà true. È possibile monitorare lo stato di avanzamento di questa operazione tramite la `SceneOperationProgress` proprietà .

Il `SceneOperationProgress` valore è la media di tutte le operazioni correnti della scena asincrona. All'inizio di un caricamento del contenuto, `SceneOperationProgress` sarà zero. Al termine, `SceneOperationProgress` verrà impostato su 1 e rimarrà su 1 fino a quando non verrà eseguita l'operazione successiva. Si noti che solo le operazioni della scena di contenuto influiscono su queste proprietà.

Queste proprietà riflettono lo stato di *un'intera operazione* dall'inizio alla fine, anche se tale operazione include più passaggi:

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

### <a name="progress-examples"></a>Esempi di stato

`SceneOperationInProgress` può essere utile se l'attività deve essere sospesa durante il caricamento del contenuto:

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

`SceneOperationProgress` può essere usato per visualizzare le finestre di dialogo di stato:

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

## <a name="monitoring-with-actions"></a>Monitoraggio con azioni

Scene System (Sistema scena) fornisce diverse azioni per sapere quando le scene vengono caricate o scaricate. Ogni azione inoltra il nome della scena interessata.

Se un'operazione di caricamento o scaricamento include più scene, le azioni pertinenti verranno richiamate una volta per ogni scena interessata. Vengono inoltre richiamati tutti contemporaneamente quando l'operazione di caricamento o scaricamento è *stata completata completamente.* Per questo motivo è consigliabile usare le azioni *OnWillUnload* per rilevare il contenuto che verrà eliminato in modo eliminato, anziché usare le azioni *OnUnloaded* per rilevare il contenuto eliminato dopo il fatto. 

Sul lato opposto, poiché le azioni *OnLoaded* vengono richiamate solo quando tutte le scene sono attivate e caricate completamente, l'uso delle azioni *OnLoaded* per rilevare e usare il nuovo contenuto è garantito come sicuro.

Azione | Quando viene richiamato | Scene di contenuto | Scene di illuminazione | Scene di gestione
--- | --- | --- | --- | --- | ---
`OnWillLoadContent` | Poco prima del caricamento di una scena di contenuto | • | |  
`OnContentLoaded` | Dopo che tutte le scene di contenuto in un'operazione di caricamento sono state completamente caricate e attivate | • | |
`OnWillUnloadContent` | Poco prima di un'operazione di scaricamento di una scena di contenuto | • | |
`OnContentUnloaded` | Dopo che tutte le scene di contenuto in un'operazione di scaricamento sono state scaricate completamente | • | |
`OnWillLoadLighting` | Poco prima del caricamento di una scena di illuminazione | | • |
`OnLightingLoaded` | Dopo che una scena di illuminazione è stata completamente caricata e attivata| | • |
`OnWillUnloadLighting` | Poco prima dello scaricamento di una scena di illuminazione | | • |
`OnLightingUnloaded` | Dopo che una scena di illuminazione è stata scaricata completamente | | • |
`OnWillLoadScene` | Poco prima del caricamento di una scena | • | • | •
`OnSceneLoaded` | Dopo che tutte le scene di un'operazione sono state caricate e attivate | • | • | •
`OnWillUnloadScene` | Poco prima dello scaricamento di una scena | • | • | •
`OnSceneUnloaded` | Dopo che una scena è stata scaricata completamente |  • | • | •

### <a name="action-examples"></a>Esempi di azioni

Un altro esempio di finestra di dialogo di stato che usa azioni e una coroutine invece di Update:

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

## <a name="controlling-scene-activation"></a>Controllo dell'attivazione della scena

Per impostazione predefinita, le scene di contenuto sono impostate per l'attivazione quando vengono caricate. Se si vuole controllare manualmente l'attivazione della scena, è possibile passare a `SceneActivationToken` qualsiasi metodo di caricamento del contenuto. Se più scene di contenuto vengono caricate da una singola operazione, questo token di attivazione verrà applicato a tutte le scene.

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

## <a name="checking-which-content-is-loaded"></a>Controllo del contenuto caricato

La `ContentSceneNames` proprietà fornisce una matrice di scene di contenuto disponibili in ordine di indice di compilazione. È possibile controllare se queste scene vengono caricate tramite `IsContentLoaded(string contentName)` .

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

string[] contentSceneNames = sceneSystem.ContentSceneNames;
bool[] loadStatus = new bool[contentSceneNames.Length];

for (int i = 0; i < contentSceneNames.Length; i++>)
{
    loadStatus[i] = sceneSystem.IsContentLoaded(contentSceneNames[i]);
}
```

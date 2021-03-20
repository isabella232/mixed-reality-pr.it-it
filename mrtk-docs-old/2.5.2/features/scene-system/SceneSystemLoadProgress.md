---
title: SceneSystemLoadProgress
description: Documentazione sul caricamento del contenuto di scene in MRTK
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: d54349461583241d19f260964528786e58baf54d
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2021
ms.locfileid: "104686981"
---
# <a name="monitoring-content-loading"></a>Monitoraggio del caricamento del contenuto

## <a name="scene-operation-progress"></a>Stato operazione scena

Quando il contenuto viene caricato o scaricato, la `SceneOperationInProgress` proprietà restituirà true. È possibile monitorare lo stato di avanzamento di questa operazione tramite la `SceneOperationProgress` Proprietà.

Il `SceneOperationProgress` valore è la media di tutte le operazioni di scena asincrone correnti. All'inizio di un carico di contenuto, `SceneOperationProgress` sarà zero. Una volta completata `SceneOperationProgress` l'operazione, verrà impostata su 1 e rimarrà su 1 fino a quando non verrà eseguita l'operazione successiva. Si noti che solo le operazioni della scena del contenuto influiscono su queste proprietà.

Queste proprietà riflettono lo stato di un' *intera operazione* dall'inizio alla fine, anche se tale operazione include più passaggi:

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

`SceneOperationProgress` consente di visualizzare le finestre di dialogo dello stato di avanzamento:

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

Il sistema di scena fornisce diverse azioni che consentono di stabilire quando vengono caricate o scaricate scene. Ogni azione inoltra il nome della scena interessata.

Se un'operazione di caricamento o scaricamento prevede più scene, le azioni rilevanti verranno richiamate una volta per ogni scena interessata. Vengono richiamati tutti contemporaneamente quando l'operazione di caricamento o scaricamento viene *completata completamente.* Per questo motivo è consigliabile usare le azioni *OnWillUnload* per rilevare il contenuto che *verrà* eliminato definitivamente, invece di usare le azioni *OnUnloaded* per rilevare il contenuto distrutto dopo il fatto.

Sul lato flip, poiché le azioni *OnLoaded* vengono richiamate solo quando tutte le scene sono attivate e completamente caricate, l'uso di azioni *OnLoaded* per rilevare e usare nuovi contenuti è sicuramente sicuro.

Azione | Quando viene richiamato | Scene di contenuto | Scene di illuminazione | Scene di gestione
--- | --- | --- | --- | --- | ---
`OnWillLoadContent` | Appena prima del caricamento di una scena del contenuto | • | |  
`OnContentLoaded` | Dopo che tutte le scene di contenuto in un'operazione di caricamento sono state completamente caricate e attivate | • | |
`OnWillUnloadContent` | Appena prima di un'operazione di scaricamento della scena del contenuto | • | |
`OnContentUnloaded` | Dopo che tutte le scene di contenuto in un'operazione di scaricamento sono state completamente scaricate | • | |
`OnWillLoadLighting` | Appena prima del caricamento di una scena di illuminazione | | • |
`OnLightingLoaded` | Dopo che una scena di illuminazione è stata completamente caricata e attivata| | • |
`OnWillUnloadLighting` | Immediatamente prima dello scaricamento di una scena di illuminazione | | • |
`OnLightingUnloaded` | Dopo che una scena di illuminazione è stata completamente scaricata | | • |
`OnWillLoadScene` | Appena prima del caricamento di una scena | • | • | •
`OnSceneLoaded` | Dopo che tutte le scene in un'operazione sono state completamente caricate e attivate | • | • | •
`OnWillUnloadScene` | Immediatamente prima dello scaricamento di una scena | • | • | •
`OnSceneUnloaded` | Quando una scena è completamente scaricata |  • | • | •

### <a name="action-examples"></a>Esempi di azione

Un altro esempio di finestra di dialogo di stato usando le azioni e una coroutine anziché Update:

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

Per impostazione predefinita, le scene di contenuto sono impostate per l'attivazione al caricamento. Se si desidera controllare manualmente l'attivazione della scena, è possibile passare un oggetto `SceneActivationToken` a qualsiasi metodo di caricamento del contenuto. Se più scene di contenuto vengono caricate da una singola operazione, questo token di attivazione verrà applicato a tutte le scene.

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

## <a name="checking-which-content-is-loaded"></a>Verifica del contenuto caricato

La `ContentSceneNames` proprietà fornisce una matrice di scene di contenuto disponibili nell'ordine dell'indice di compilazione. È possibile verificare se queste scene sono state caricate tramite `IsContentLoaded(string contentName)` .

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

string[] contentSceneNames = sceneSystem.ContentSceneNames;
bool[] loadStatus = new bool[contentSceneNames.Length];

for (int i = 0; i < contentSceneNames.Length; i++>)
{
    loadStatus[i] = sceneSystem.IsContentLoaded(contentSceneNames[i]);
}
```

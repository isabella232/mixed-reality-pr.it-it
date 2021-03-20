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
# <a name="content-scene-loading"></a>Caricamento della scena del contenuto

Tutte le operazioni di caricamento del contenuto sono asincrone e, per impostazione predefinita, tutto il caricamento del contenuto è additivo. I Manager e le scene di illuminazione non sono mai interessati dalle operazioni di caricamento del contenuto. Per informazioni sul monitoraggio dello stato di avanzamento del caricamento e dell'attivazione della scena, vedere [monitoraggio del caricamento del contenuto](SceneSystemLoadProgress.md).

## <a name="loading-content"></a>Caricamento del contenuto

Per caricare le scene del contenuto `LoadContent` , usare il metodo:

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

// Additively load a single content scene
await sceneSystem.LoadContent("MyContentScene");

// Additively load a set of content scenes
await sceneSystem.LoadContent(new string[] { "MyContentScene1", "MyContentScene2", "MyContentScene3" });
```

## <a name="single-scene-loading"></a>Caricamento di una singola scena

L'equivalente di un singolo carico della scena può essere effettuato tramite l' `mode` argomento facoltativo. `LoadSceneMode.Single` prima di procedere con il caricamento, Scarica innanzitutto tutte le scene di contenuto caricati.

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

## <a name="next--previous-scene-loading"></a>Caricamento della scena successiva/precedente

Il contenuto può essere caricato singolarmente in ordine di indice di compilazione. Questa operazione è utile per le applicazioni di presentazione che consentono agli utenti di eseguire una serie di scene dimostrative una alla volta.

![Immagine di MRTK_SceneSystemBuildSettings](../images/scene-system/MRTK_SceneSystemBuildSettings.png)

Si noti che il caricamento del contenuto successivo/precedente USA LoadSceneMode. Single per impostazione predefinita per garantire che il contenuto precedente venga scaricato.

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

`PrevContentExists` Restituisce true se è presente almeno una scena di contenuto con un indice di compilazione inferiore rispetto all'indice di compilazione più basso attualmente caricato. `NextContentExists` Restituisce true se è presente almeno una scena di contenuto con un indice di compilazione superiore rispetto all'indice di compilazione più alto attualmente caricato.

Se l' `wrap` argomento è true, il contenuto eseguirà il loopback al primo/ultimo indice di compilazione. In questo modo si elimina la necessità di verificare il contenuto successivo o precedente:

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

## <a name="loading-by-tag"></a>Caricamento per tag

![Immagine di MRTK_SceneSystemLoadingByTag](../images/scene-system/MRTK_SceneSystemLoadingByTag.png)

A volte è consigliabile caricare le scene di contenuto nei gruppi. Ad esempio, una fase di un'esperienza può essere costituita da più scene, che devono essere caricate simultaneamente per funzionare. Per semplificare questa operazione, è possibile contrassegnare le scene e quindi caricarle o scaricarle con tale tag.

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

await LoadContentByTag("Stage1");

// Wait until stage 1 is complete

await UnloadContentByTag("Stage1");
await LoadContentByTag("Stage2);
```

Il caricamento in base al tag può essere utile anche se gli artisti vogliono incorporare o rimuovere elementi da un'esperienza senza dover modificare gli script. Ad esempio, l'esecuzione di questo script con i due set di tag seguenti produce risultati diversi:

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

await LoadContentByTag("Terrain");
await LoadContentByTag("Structures");
await LoadContentByTag("Vegetation");
```

### <a name="testing-content"></a>Test del contenuto

Nome scena | Tag di scena | Caricato dallo script
---|---|---
DebugTerrainPhysics | Terreno | •
StructureTesting | Strutture | •
VegetationTools | Vegetazione | •
Mountain | Terreno | •
Abitacolo | Strutture | •
Trees | Vegetazione | •

### <a name="final-content"></a>Contenuto finale

Nome scena | Tag di scena | Caricato dallo script
---|---|---
DebugTerrainPhysics | DoNotInclude |
StructureTesting | DoNotInclude |
VegetationTools | DoNotInclude |
Mountain | Terreno | •
Abitacolo | Strutture | •
Trees | Vegetazione | •

---

## <a name="editor-behavior"></a>Comportamento dell'editor

È possibile eseguire tutte queste operazioni in Editor e in modalità di riproduzione usando il [controllo del servizio](../../configuration/MixedRealityConfigurationGuide.md#editor-utilities) del sistema di scena. In modalità di modifica i caricamenti della scena saranno istantanei, mentre in modalità di riproduzione è possibile osservare lo stato di avanzamento del caricamento e usare i [token di attivazione.](SceneSystemLoadProgress.md)

![Immagine di MRTK_SceneSystemServiceInspector](../images/scene-system/MRTK_SceneSystemServiceInspector.PNG)

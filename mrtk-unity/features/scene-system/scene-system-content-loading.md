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
# <a name="content-scene-loading"></a>Caricamento della scena di contenuto

Tutte le operazioni di caricamento del contenuto sono asincrone e, per impostazione predefinita, tutto il caricamento del contenuto è additivo. Le operazioni di caricamento del contenuto non hanno mai effetto sulle scene di gestione e di illuminazione. Per informazioni sul monitoraggio dello stato di avanzamento del caricamento e dell'attivazione della scena, vedere [Monitoraggio del caricamento del contenuto.](scene-system-load-progress.md)

## <a name="loading-content"></a>Caricamento del contenuto

Per caricare scene di contenuto, usare il `LoadContent` metodo :

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

// Additively load a single content scene
await sceneSystem.LoadContent("MyContentScene");

// Additively load a set of content scenes
await sceneSystem.LoadContent(new string[] { "MyContentScene1", "MyContentScene2", "MyContentScene3" });
```

## <a name="single-scene-loading"></a>Caricamento di una singola scena

L'equivalente di un singolo carico della scena può essere ottenuto tramite l'argomento `mode` facoltativo . `LoadSceneMode.Single` scarica tutte le scene di contenuto caricate prima di procedere con il caricamento.

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

Il contenuto può essere caricato in ordine di indice di compilazione. Ciò è utile per presentare le applicazioni che consentono agli utenti di eseguire una serie di scene dimostrativi una alla volta.

![Scene correnti nella compilazione nelle impostazioni del lettore](../images/scene-system/MRTK_SceneSystemBuildSettings.png)

Si noti che il caricamento del contenuto successivo/precedente usa LoadSceneMode.Single per impostazione predefinita per garantire che il contenuto precedente sia scaricato.

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

`PrevContentExists` restituirà true se è presente almeno una scena di contenuto con un indice di compilazione inferiore rispetto all'indice di compilazione più basso attualmente caricato. `NextContentExists` restituirà true se è presente almeno una scena di contenuto con un indice di compilazione più alto rispetto all'indice di compilazione più alto attualmente caricato.

Se `wrap` l'argomento è true, il contenuto torna all'indice della prima o dell'ultima compilazione. In questo modo non è più necessario verificare il contenuto successivo o precedente:

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

## <a name="loading-by-tag"></a>Caricamento in base al tag

![Caricamento di scene di contenuto per tag](../images/scene-system/MRTK_SceneSystemLoadingByTag.png)

A volte è consigliabile caricare scene di contenuto in gruppi. Ad esempio, una fase di un'esperienza può essere costituita da più scene, che devono essere caricate contemporaneamente per funzionare. Per semplificare questa operazione, è possibile contrassegnare le scene e quindi caricarle o scaricarle con tale tag.

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

await LoadContentByTag("Stage1");

// Wait until stage 1 is complete

await UnloadContentByTag("Stage1");
await LoadContentByTag("Stage2);
```

Il caricamento in base al tag può essere utile anche se gli autori vogliono incorporare/rimuovere elementi da un'esperienza senza dover modificare gli script. Ad esempio, l'esecuzione di questo script con i due set di tag seguenti produce risultati diversi:

```c#
IMixedRealitySceneSystem sceneSystem = MixedRealityToolkit.Instance.GetService<IMixedRealitySceneSystem>();

await LoadContentByTag("Terrain");
await LoadContentByTag("Structures");
await LoadContentByTag("Vegetation");
```

### <a name="testing-content"></a>Test del contenuto

Nome scena | Tag scena | Caricato dallo script
---|---|---
DebugPhysics | Terreno | •
StructureTesting | Strutture | •
Strumenti Disastrumenti | Vegetazione | •
Mountain | Terreno | •
Cabina | Strutture | •
Trees | Vegetazione | •

### <a name="final-content"></a>Contenuto finale

Nome scena | Tag della scena | Caricato da script
---|---|---
DebugTerrainPhysics | DoNotInclude |
StructureTesting | DoNotInclude |
Estrumenti di verde | DoNotInclude |
Mountain | Terreno | •
Cabina | Strutture | •
Trees | Vegetazione | •

---

## <a name="editor-behavior"></a>Comportamento dell'editor

È possibile eseguire tutte queste operazioni nell'editor e in modalità di riproduzione usando il controllo dei servizi [del sistema di scena.](../../configuration/mixed-reality-configuration-guide.md#editor-utilities) In modalità di modifica i caricamenti della scena saranno istantanei, mentre in modalità di riproduzione è possibile osservare lo stato di avanzamento del caricamento e usare [i token di attivazione.](scene-system-load-progress.md)

![Sistema di scena nel controllo con il caricamento del contenuto evidenziato](../images/scene-system/MRTK_SceneSystemServiceInspector.PNG)

---
title: SceneSystemGettingStarted
description: Pagina di destinazione per il sistema di scena con MRTK
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: 930f37e844992b98a0e2ea965b695734bef495e3
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/03/2021
ms.locfileid: "101782319"
---
# <a name="scene-system-overview"></a>Panoramica del sistema di scena

## <a name="when-to-use-the-scene-system"></a>Quando usare il sistema di scena

Se il progetto è costituito da un'unica scena, probabilmente il sistema della scena non è necessario. È particolarmente utile quando si verificano una o più delle condizioni seguenti:

- Il progetto include più scene.
- Si viene usati per il caricamento di una singola scena, ma non è come il modo in cui viene distrutta l'istanza di MixedRealityToolkit.
- Si vuole un modo semplice per caricare additivamente più scene per costruire la propria esperienza.
- Si vuole un modo semplice per tenere traccia delle operazioni di caricamento in corso o un modo semplice per controllare l'attivazione della scena per più scene caricate contemporaneamente.
- Si vuole rendere l'illuminazione coerente e prevedibile in tutte le scene.

## <a name="how-to-use-the-scene-system"></a>Come usare il sistema di scena

- [Tipi di scena](SceneSystemSceneTypes.md)
- [Caricamento della scena del contenuto](SceneSystemContentLoading.md)
- [Monitoraggio del caricamento del contenuto](SceneSystemLoadProgress.md)
- [Caricamento della scena di illuminazione](SceneSystemLightingScenes.md)

## <a name="editor-settings"></a>Impostazioni editor

Per impostazione predefinita, il sistema di scena impone diversi comportamenti nell'editor di Unity. Se uno di questi comportamenti è elevato, è possibile disabilitarli nella sezione **Impostazioni editor** del profilo di sistema della scena.

- `Editor Manage Build Settings:` Se true, il servizio aggiornerà automaticamente le impostazioni di compilazione, assicurando l'aggiunta di tutte le scene di gestione, illuminazione e contenuto. Disabilitare questa impostazione se si desidera il controllo totale sulle impostazioni di compilazione.

- `Editor Enforce Scene Order:` Se true, il servizio assicurerà che la scena del Manager venga visualizzata per prima nella gerarchia della scena, seguita dall'illuminazione e quindi dal contenuto. Disabilitare questa proprietà se si desidera il controllo totale sulla gerarchia della scena.

- `Editor Manage Loaded Scenes:` Se true, il servizio assicurerà che il responsabile, il contenuto e le scene di illuminazione siano sempre caricati. Disabilitare se si desidera il controllo totale sulle scene caricate nell'editor.

- `Editor Enforce Lighting Scene Types:` Se true, il servizio garantirà che solo i componenti correlati all'illuminazione definiti in `PermittedLightingSceneComponentTypes` siano consentiti nelle scene di illuminazione. Disabilitare se si desidera il controllo totale sul contenuto delle scene di illuminazione.

![Impostazioni dell'editor di sistema della scena](../Images/SceneSystem/MRTK_SceneSystemProfileEditorSettings.PNG)

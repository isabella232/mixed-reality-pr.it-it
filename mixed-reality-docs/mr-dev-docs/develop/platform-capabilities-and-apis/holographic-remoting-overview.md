---
title: Panoramica della comunicazione remota olografica
description: Informazioni su Holographic Remoting e su come può trarre vantaggio dal processo di sviluppo.
author: hferrone
ms.author: v-vtieto
ms.date: 08/12/2021
ms.topic: article
keywords: openxr, unity, hololens, hololens 2, realtà mista, MRTK, mixed reality Toolkit, realtà aumentata, realtà virtuale, visori di realtà mista, apprendimento, esercitazione, introduzione, comunicazione remota olografica, desktop, anteprima
ms.openlocfilehash: 52b69f942797b1f0a6a9bcc5276a49d4d2cebba5
ms.sourcegitcommit: 820f2dfe98065298f6978a651f838de12620dd45
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/14/2021
ms.locfileid: "122184602"
---
# <a name="holographic-remoting-overview"></a>Panoramica della comunicazione remota olografica

È possibile usare Holographic Remoting per trasmettere contenuti olografici al HoloLens in tempo reale. A questo scopo sono disponibili due usi principali ed è importante comprendere la differenza:

1. (Unity o Unreal): si vuole visualizzare in anteprima ed eseguire il **debug dell'app** durante il processo di sviluppo: è possibile eseguire l'app in locale nell'editor di Unity nel PC in modalità play e trasmettere l'esperienza al HoloLens. In questo modo è possibile eseguire rapidamente il debug dell'app senza compilare e distribuire un progetto completo. Questo tipo di app viene chiamato app _holographic Remoting Play Mode Preview._

    - [Altre informazioni sull'anteprima e il debug dell'app in Unity](../unity/preview-and-debug-your-app.md)

    - [Altre informazioni sull'anteprima e il debug dell'app in Unreal](../unreal/unreal-streaming.md)

1. (Unity, Unreal o C++): si vuole che le risorse di un PC possano alimentare l'app invece di basarsi sulle risorse di **HoloLens on-board:** è possibile creare e compilare un'app con la funzionalità Holographic Remoting. L'utente sperimenta l'app nel HoloLens, ma l'app viene effettivamente eseguita in un PC, che consente di sfruttare le risorse più potenti del PC. Questo può essere particolarmente utile se l'app dispone di asset o modelli ad alta risoluzione e non si vuole che la frequenza dei fotogrammi ne risenti. Questo tipo di app viene chiamato app _remota Holographic Remoting._

    - [Altre informazioni sull'uso delle risorse PC in Unity](../unity/use-pc-resources.md)

    - [Altre informazioni sull'uso delle risorse PC in Unreal](../unreal/unreal-streaming.md)

    - [Scrivere un'app remota Holographic Remoting usando Windows Mixed Reality API (C++)](holographic-remoting-create-remote-wmr.md)

    - [Scrivere un'app remota Holographic Remoting usando le API OpenXR (C++)](holographic-remoting-create-remote-openxr.md)

In entrambi i casi, gli input del mapping HoloLens,sguardo, movimento, voce e spaziale vengono inviati al PC, il contenuto viene sottoposto a rendering in una visualizzazione virtuale immersiva e i fotogrammi sottoposti a rendering vengono quindi inviati al HoloLens. 

## <a name="see-also"></a>Vedere anche

* [Holographic Remoting Player](holographic-remoting-player.md)
* [Esercitazione: Introduzione a PC Holographic Remoting](../unity/tutorials/mr-learning-pc-holographic-remoting-01.md)
* [Esercitazione: Creazione di un'applicazione per PC Holographic Remoting](../unity/tutorials/mr-learning-pc-holographic-remoting-02.md)

---
title: Visualizzare in anteprima ed eseguire il debug dell'app con la modalità Holographic Remoting e Play
description: Usare la modalità Holographic Remoting e Play per visualizzare in anteprima ed eseguire il debug dell'app
author: vtieto
ms.author: v-vtieto
ms.date: 08/12/2021
ms.topic: article
keywords: openxr, unity, hololens, hololens 2, realtà mista, MRTK, mixed reality Toolkit, realtà aumentata, realtà virtuale, visori di realtà mista, apprendimento, esercitazione, introduzione, comunicazione remota olografica, desktop, anteprima, debug
ms.openlocfilehash: fe15d55037f09c47fe1e8a1dd996d0c69480f7b2
ms.sourcegitcommit: 820f2dfe98065298f6978a651f838de12620dd45
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/14/2021
ms.locfileid: "122203845"
---
# <a name="preview-and-debug-your-app-using-holographic-remoting-and-play-mode"></a>Visualizzare in anteprima ed eseguire il debug dell'app usando la modalità Holographic Remoting e Play

Questo articolo illustra il caso d'uso seguente per Holographic Remoting: 

- **Si vuole visualizzare** in anteprima ed eseguire il debug dell'app durante il processo di sviluppo: è possibile eseguire l'app in locale nell'editor di Unity nel PC in modalità play e trasmettere l'esperienza al HoloLens. In questo modo è possibile eseguire rapidamente il debug dell'app senza compilare e distribuire un progetto completo. Questo tipo di app viene chiamato app _holographic Remoting Play Mode Preview._ Gli input del HoloLens, ad esempio lo sguardo, il movimento, la voce e il mapping spaziale, vengono inviati al PC, in cui viene eseguito il rendering del contenuto in una visualizzazione virtuale immersiva. I fotogrammi sottoposti a rendering vengono quindi inviati al HoloLens. 

Per altre informazioni sulla comunicazione remota Holographic, vedere [Panoramica di Holographic Remoting](../platform-capabilities-and-apis/holographic-remoting-overview.md)

Si noti che è anche possibile usare Holographic Remoting se si vuole che le risorse di un PC abilitino [l'app](use-pc-resources.md) invece di basarsi HoloLens risorse di bordo.

## <a name="set-up-holographic-remoting"></a>Configurare Holographic Remoting

Per usare Holographic Remoting, è necessario installare l'app [Holographic Remoting Player](../platform-capabilities-and-apis/holographic-remoting-player.md) dal Microsoft Store nel HoloLens. Come illustrato di seguito, dopo aver scaricato ed eseguito l'app, verranno visualizzati il numero di versione e l'indirizzo IP a cui connettersi. **Per usare il plug-in OpenXR** è necessaria la versione 2.4 o successiva.

Holographic Remoting richiede un PC veloce e Wi-Fi connessione. Per altri dettagli, vedere l'articolo holographic Remoting Player collegato in precedenza.

![Screenshot di Holographic Remoting Player in esecuzione nel HoloLens](images/openxr-features-img-01.png)

[!INCLUDE[](includes/unity-play-mode.md)]

## <a name="see-also"></a>Vedere anche
* [Holographic Remoting Player](../platform-capabilities-and-apis/holographic-remoting-player.md)
* [Esercitazione: Introduzione a PC Holographic Remoting](tutorials/mr-learning-pc-holographic-remoting-01.md)
* [Esercitazione: Creazione di un'applicazione per PC Holographic Remoting](tutorials/mr-learning-pc-holographic-remoting-02.md)

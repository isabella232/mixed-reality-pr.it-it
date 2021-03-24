---
title: Panoramica sullo sviluppo per JavaScript
description: Panoramica dello sviluppo di realtà miste mediante JavaScript per auricolari Web, per dispositivi mobili e Windows immersivi.
author: yonet
ms.author: ayyonet
ms.date: 04/10/2020
ms.topic: article
keywords: JavaScript, WebXR, WinMR, WebAR, WebVR, WindowsMixedReality, HoloLens, realtà mista di Windows, Web VR, Web XR, Web Mr, Web AR, 360, 360 video, 360 video, 360 Photo, 360 photos, 360 contenuto, immersive Web, immersive-Web, IW, immersiveweb
ms.openlocfilehash: 051c6079da939224c88d6414978b2b4b0e67f87c
ms.sourcegitcommit: cbfd1c37612aa6904fa41642ede6281d491e478d
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/23/2021
ms.locfileid: "104909056"
---
# <a name="javascript-development-overview"></a>Panoramica dello sviluppo con JavaScript

JavaScript è uno dei linguaggi di programmazione più diffusi al mondo. È semplice, leggero e ampiamente usato sul Web. Sfrutta la potenza delle tue competenze JavaScript e Web per creare esperienze di realtà miste più coinvolgenti.

## <a name="mixed-reality-applications-on-the-web"></a>Applicazioni di realtà mista sul Web

Le funzionalità di realtà mista sono disponibili sul Web mediante l'uso di [WebXR](webxr-overview.md). È possibile vedere la realtà virtuale (VR) e il contenuto della realtà aumentata (AR) in un browser compatibile abilitato per WebXR senza installare software o plug-in aggiuntivi. È possibile usare lo stesso browser con un dispositivo fisico come HoloLens 2. Per altri dettagli, vedere la documentazione di [WebXR](webxr-overview.md) .

> [!NOTE]
> **WebVR** è deprecato e non è disponibile nei browser correnti, quindi non deve essere usato per nuove attività di sviluppo. Sarà necessario eseguire la migrazione di tutte le implementazioni di **WebVR** esistenti in **WebXR**.

## <a name="what-can-i-use-to-develop-immersive-web-experiences"></a>Cosa si può usare per sviluppare esperienze Web Immersive?

Nell'elenco seguente sono illustrati i Framework e le API JavaScript per la creazione di esperienze immersive che attualmente dominano il mercato e sono ampiamente accettate e adottate dagli sviluppatori JavaScript di realtà mista:

|  |  |
| --- | --- |
|[**Babylon.js**](https://doc.babylonjs.com/)<br/><br/> Babylon è un motore 3D JavaScript che rende più semplice lo sviluppo di contenuti 3D e applicazioni immersive. Prima di iniziare a usare le applicazioni immersive, si consiglia di apprendere le nozioni di base dello sviluppo Babylon.js.<br/><br/>-Informazioni su come creare applicazioni 3D con babylon.js [Introduzione](https://doc.babylonjs.com/start).<br/>-Giocare con esempi 3D e il relativo codice sorgente usando babylon.js [Playground](https://doc.babylonjs.com/examples/)<br/>-Approfondimenti su [WebXR](https://doc.babylonjs.com/divingDeeper/webXR)<br/>-Informazioni su come iniziare a usare le esercitazioni per [creare la prima app "Hello World!"](tutorials/babylonjs-webxr-helloworld/introduction-01.md)|![Logo di BabylonJS](images/babylon.js.example.png) |
|[**A-frame**](https://aframe.io/) <br/><br/>Un frame è un framework JavaScript dichiarativo per iniziare a usare la realtà virtuale sul Web. Per altre informazioni, vedere la [documentazione a-frame](https://aframe.io/docs/1.2.0/introduction/) . |![A-frame](images/a-frame.example.png)  |
|[**Three.js**](https://threejs.org) <br/><br/>Three.js è una libreria 3D molto diffusa per la creazione di esperienze immersive. Per ulteriori informazioni sulla [three.js](https://threejs.org/docs/index.html#manual/en/introduction/Creating-a-scene) nella pagina della documentazione e sull'esplorazione degli [esempi](https://threejs.org/examples/#webgl_animation_cloth). |![Three.js](images/three.js.example.png)  |
|[**WebGL**](https://developer.mozilla.org/en-US/docs/Web/API/WebGL_API)  <br/><br/>È possibile accedere direttamente alle API del dispositivo WebXR usando le API di WebGL. WebGL (Web Graphics Library) è un'API JavaScript che consente di eseguire il rendering di immagini 2D e 3D interattive a prestazioni elevate in qualsiasi Web browser compatibile senza l'uso di plug-in. |![WebGL](images/webgl.example.png)  |

## <a name="next-steps"></a>Passaggi successivi

Informazioni su come iniziare a usare le esercitazioni.

> [!div class="nextstepaction"]
> [Creare la prima app "Hello World!"](tutorials/babylonjs-webxr-helloworld/introduction-01.md)

## <a name="see-also"></a>Vedere anche

* [Panoramica di WebXR](webxr-overview.md)
* [Specifica API del dispositivo WebXR](https://immersive-web.github.io/webxr/)
* [Documentazione dell'API del dispositivo WebXR](https://developer.mozilla.org/en-US/docs/Web/API/WebXR_Device_API)
* [Immersiveweb.dev](https://immersiveweb.dev/)
* [Esempi di WebXR](https://immersive-web.github.io/webxr-samples/)
* [Uso di Babylon.js per creare esperienze WebXR](https://doc.babylonjs.com/how_to/introduction_to_webxr)
* [Realtà mista di Windows e la nuova Microsoft Edge](/windows/mixed-reality/new-microsoft-edge#introducing-the-new-microsoft-edge)
* [GitHub sul Web W3C immersivo](https://github.com/immersive-web)
* [API WebGL](/previous-versions/windows/internet-explorer/ie-developer/dev-guides/bg182648(v=vs.85))
* Estensioni dell' [API gamepad](https://msdn.microsoft.com/library/dn743630(v=vs.85).aspx) e del [Gamepad](https://w3c.github.io/gamepad/extensions.html)

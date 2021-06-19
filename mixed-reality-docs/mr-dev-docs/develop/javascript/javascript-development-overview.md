---
title: Panoramica dello sviluppo javascript
description: Panoramica dello sviluppo di realtà mista con JavaScript per visori VR immersive Web, per dispositivi mobili e Windows.
author: yonet
ms.author: ayyonet
ms.date: 04/10/2020
ms.topic: article
keywords: JavaScript, WebXR, WinMR, WebAR, WebVR, WindowsMixedReality, HoloLens, windows mixed reality, web vr, web xr, web mr, web ar, 360, 360 video, 360 video, 360 foto, 360 foto, 360 foto, 360 contenuti, web immersive, immersive-web, IW, immersiveweb
ms.openlocfilehash: 311241d9dec6f5d086a45766c040b1b2b9eb4128
ms.sourcegitcommit: 6ade7e8ebab7003fc24f9e0b5fa81d091369622c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2021
ms.locfileid: "112394345"
---
# <a name="javascript-development-overview"></a>Panoramica dello sviluppo con JavaScript

JavaScript è uno dei linguaggi di programmazione più diffusi al mondo. È semplice, leggero e ampiamente usato sul Web. Sfrutta la potenza delle tue competenze JavaScript e Web per creare esperienze di realtà mista più coinvolgenti.

## <a name="mixed-reality-applications-on-the-web"></a>Applicazioni di realtà mista sul Web

Le funzionalità di realtà mista sono disponibili sul Web tramite [WebXR.](webxr-overview.md) È possibile visualizzare il contenuto di realtà virtuale (VR) e realtà aumentata (AR) in un browser compatibile con WebXR senza installare software o plug-in aggiuntivi. È possibile usare lo stesso browser con un dispositivo fisico come il HoloLens 2. Per altri dettagli, vedere la documentazione di [WebXR.](webxr-overview.md)

> [!NOTE]
> **WebVR** è deprecato e non è disponibile nei browser correnti, pertanto non deve essere usato per i nuovi progetti di sviluppo. Sarà necessario eseguire la migrazione di eventuali **implementazioni WebVR** esistenti a **WebXR.**

## <a name="what-can-i-use-to-develop-immersive-web-experiences"></a>Cosa è possibile usare per sviluppare esperienze Web immersive?

L'elenco seguente mostra i framework e le API JavaScript per la creazione di esperienze immersive che attualmente dominano il mercato e sono ampiamente accettate e adottate dagli sviluppatori JavaScript di realtà mista:

|  |  |
| --- | --- |
|[**Babylon.js**](https://doc.babylonjs.com/)<br/><br/> Babylon è un motore 3D JavaScript che semplifica lo sviluppo di contenuti 3D e applicazioni immersive. Prima di iniziare a usare le applicazioni immersive, è consigliabile apprendere le nozioni di base Babylon.js sviluppo.<br/><br/>- Informazioni su come compilare applicazioni 3D con babylon.js [Introduzione](https://doc.babylonjs.com/start)a .<br/>- Riprodurre con esempi 3D e il relativo codice sorgente usando babylon.js [Playground](https://doc.babylonjs.com/examples/)<br/>- Approfondimenti su [WebXR](https://doc.babylonjs.com/divingDeeper/webXR)<br/>- Informazioni su come iniziare a usare le esercitazioni [Creare la prima app "Hello World!"](tutorials/babylonjs-webxr-helloworld/introduction-01.md)|![BabylonJS Logo](images/babylon.js.example.png) |
|[**Frame A**](https://aframe.io/) <br/><br/>Un frame è un framework JavaScript dichiarativo per iniziare a usare la realtà virtuale nel Web. Per altre informazioni, vedere la documentazione di [A-Frame.](https://aframe.io/docs/1.2.0/introduction/) |![Frame A](images/a-frame.example.png)  |
|[**Three.js**](https://threejs.org) <br/><br/>Three.js è una libreria 3D molto diffusa per la creazione di esperienze immersive. Altre informazioni sulle [three.js](https://threejs.org/docs/index.html#manual/en/introduction/Creating-a-scene) nella pagina della documentazione ed esplorando [gli esempi](https://threejs.org/examples/#webgl_animation_cloth). |![Three.js](images/three.js.example.png)  |
|[**WebGL**](https://developer.mozilla.org/en-US/docs/Web/API/WebGL_API)  <br/><br/>È possibile accedere alle API del dispositivo WebXR direttamente usando le API WebGL. WebGL (Web Graphics Library) è un'API JavaScript per il rendering di grafica 3D e 2D interattiva ad alte prestazioni all'interno di qualsiasi Web browser compatibile senza l'uso di plug-in. |![WebGL](images/webgl.example.png)  |

## <a name="next-steps"></a>Passaggi successivi

Informazioni su come iniziare a usare le esercitazioni.

> [!div class="nextstepaction"]
> [Creare la prima app "Hello World!"](tutorials/babylonjs-webxr-helloworld/introduction-01.md)

## <a name="see-also"></a>Vedere anche

* [Panoramica di WebXR](webxr-overview.md)
* [Specifica dell'API del dispositivo WebXR](https://immersive-web.github.io/webxr/)
* [Documentazione dell'API del dispositivo WebXR](https://developer.mozilla.org/en-US/docs/Web/API/WebXR_Device_API)
* [Immersiveweb.dev](https://immersiveweb.dev/)
* [Esempi di WebXR](https://immersive-web.github.io/webxr-samples/)
* [Uso Babylon.js per creare esperienze WebXR](https://doc.babylonjs.com/how_to/introduction_to_webxr)
* [Windows Mixed Reality e il nuovo Microsoft Edge](/windows/mixed-reality/new-microsoft-edge#introducing-the-new-microsoft-edge)
* [Immersive Web W3C Github](https://github.com/immersive-web)
* [WebGL API](/previous-versions/windows/internet-explorer/ie-developer/dev-guides/bg182648(v=vs.85))
* [API Gamepad](https://msdn.microsoft.com/library/dn743630(v=vs.85).aspx) ed [estensioni gamepad](https://w3c.github.io/gamepad/extensions.html)

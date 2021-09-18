---
title: Uso di WebXR con Windows Mixed Reality
description: Informazioni di base sull'uso e lo sviluppo per applicazioni WebXR in esecuzione Windows Mixed Reality visori VR immersive.
author: yonet
ms.author: v-vtieto
ms.date: 09/16/2021
ms.topic: article
keywords: WebXR, WinMR, WebAR, WebVR, WindowsMixedReality, HoloLens, windows mixed reality, web vr, web xr, web mr, web ar, 360, 360 video, 360 video, 360 foto, 360 foto, 360 foto, 360 contenuti, web immersive, immersiveweb, IW
ms.openlocfilehash: f99637c79d1147d940bb6a72d68969c99a2482ec
ms.sourcegitcommit: 645608f33d2d02625484c29586f42d21c442aaa9
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/18/2021
ms.locfileid: "127932527"
---
# <a name="javascript-development-with-webxr"></a>Sviluppo JavaScript con WebXR

JavaScript è uno dei linguaggi di programmazione più diffusi al mondo. È semplice, leggero e ampiamente usato sul Web. Sfrutta la potenza delle tue competenze JavaScript e Web per creare esperienze di realtà mista più coinvolgenti.

## <a name="mixed-reality-applications-on-the-web"></a>Applicazioni di realtà mista sul Web

Le funzionalità di realtà mista sono disponibili sul Web tramite [WebXR.](webxr-overview.md) È possibile visualizzare il contenuto di realtà virtuale (VR) e realtà aumentata (AR) in un browser compatibile con WebXR senza installare software o plug-in aggiuntivi. È possibile usare lo stesso browser con un dispositivo fisico come il HoloLens 2.

L'API del dispositivo  [**WebXR**](https://www.w3.org/TR/webxr/) è per l'accesso ai dispositivi di  realtà virtuale **(VR)** e realtà aumentata **(AR),** inclusi sensori e schermi montati con la testa **sul Web.** L'API del dispositivo WebXR è attualmente disponibile in Microsoft Edge e Chrome versione 79 e successive supporta WebXR come impostazione predefinita. È possibile controllare lo stato di supporto del browser più recente per WebXR [all'indirizzo caniuse.com](https://caniuse.com/#search=webxr).

> [!NOTE]
> **WebVR** è deprecato e non è disponibile nei browser correnti, pertanto non deve essere usato per i nuovi progetti di sviluppo. Sarà necessario eseguire la migrazione di eventuali **implementazioni WebVR** esistenti a **WebXR.**

### <a name="viewing-webxr"></a>Visualizzazione di WebXR

È possibile visualizzare gli experinces di WebXR in [Windows Mixed Reality e](../../whats-new/new-microsoft-edge.md) i nuovi Microsoft Edge [e Firefox Reality.](https://mixedreality.mozilla.org/firefox-reality/)
Per verificare se il browser supporta WebXR, è possibile passare a [WebXR Samples (Esempi di WebXR)](https://immersive-web.github.io/webxr-samples/) nel browser

## <a name="what-can-i-use-to-develop-immersive-web-experiences"></a>Cosa è possibile usare per sviluppare esperienze Web immersive?

L'elenco seguente mostra i framework e le API JavaScript per la creazione di esperienze immersive che attualmente dominano il mercato e sono ampiamente accettate e adottate dagli sviluppatori JavaScript di realtà mista:

|  |  |
| --- | --- |
|[**Babylon.js**](https://doc.babylonjs.com/)<br/><br/> Babylon è un motore 3D JavaScript che semplifica lo sviluppo di contenuti 3D e applicazioni immersive. Prima di iniziare a usare le applicazioni immersive, è consigliabile apprendere le nozioni di base Babylon.js sviluppo.<br/><br/>- Informazioni su come compilare applicazioni 3D con babylon.js [Introduzione](https://doc.babylonjs.com/start)a .<br/>- Riprodurre con esempi 3D e il relativo codice sorgente usando babylon.js [Playground](https://doc.babylonjs.com/examples/)<br/>- Approfondimenti su [WebXR](https://doc.babylonjs.com/divingDeeper/webXR)<br/>- Informazioni su come iniziare a usare le esercitazioni [Creare la prima app "Hello World!"](tutorials/babylonjs-webxr-helloworld/introduction-01.md)|![BabylonJS Logo](images/babylon.js.example.png) |
|[**Frame A**](https://aframe.io/) <br/><br/>Un frame è un framework JavaScript dichiarativo per iniziare a usare la realtà virtuale nel Web. Per altre informazioni, vedere la documentazione di [A-Frame.](https://aframe.io/docs/1.2.0/introduction/) |![Frame A](images/a-frame.example.png)  |
|[**Three.js**](https://threejs.org) <br/><br/>Three.js è una popolare libreria 3D per la creazione di esperienze immersive. Altre informazioni sui [three.js](https://threejs.org/docs/index.html#manual/en/introduction/Creating-a-scene) nella pagina della documentazione ed esplorando gli [esempi](https://threejs.org/examples/#webgl_animation_cloth). |![Three.js](images/three.js.example.png)  |
|[**WebGL**](https://developer.mozilla.org/en-US/docs/Web/API/WebGL_API)  <br/><br/>È possibile accedere alle API del dispositivo WebXR direttamente usando le API WebGL. WebGL (Web Graphics Library) è un'API JavaScript per il rendering di grafica 3D e 2D interattiva ad alte prestazioni all'interno di qualsiasi Web browser compatibile senza l'uso di plug-in. |![WebGL](images/webgl.example.png)  |

## <a name="see-also"></a>Vedere anche

* [Panoramica di WebXR](webxr-overview.md)
* [Specifica dell'API del dispositivo WebXR](https://immersive-web.github.io/webxr/)
* [Documentazione dell'API del dispositivo WebXR](https://developer.mozilla.org/en-US/docs/Web/API/WebXR_Device_API)
* [Esempi di WebXR](https://immersive-web.github.io/webxr-samples/)
* [Immersiveweb.dev](https://immersiveweb.dev/)
* [Uso Babylon.js per creare esperienze WebXR](https://doc.babylonjs.com/how_to/introduction_to_webxr)
* [WebGL API](/previous-versions/windows/internet-explorer/ie-developer/dev-guides/bg182648(v=vs.85))
* [API Gamepad](https://msdn.microsoft.com/library/dn743630(v=vs.85).aspx) ed [estensioni gamepad](https://w3c.github.io/gamepad/extensions.html)
* [Windows Mixed Reality e il nuovo Microsoft Edge](../../whats-new/new-microsoft-edge.md)
* [Gestione del contesto perso in WebGL](https://www.khronos.org/webgl/wiki/HandlingContextLost)
* [Pointerlock](https://www.w3.org/TR/pointerlock/)
* [glTF](https://www.khronos.org/gltf)
* [Gruppo della community Web immersiva](https://www.w3.org/community/immersive-web/)
* [Immersive Web W3C Github](https://github.com/immersive-web)

## <a name="next-steps--tutorials"></a>Passaggi successivi- Esercitazioni

> [!div class="nextstepaction"]
> [Creare la prima applicazione WebXR usando Babylon.js](tutorials/babylonjs-webxr-helloworld/introduction-01.md)
> [!div class="nextstepaction"]

> [Creare un piano in WebXR usando Babylon.js](tutorials/babylonjs-webxr-piano/introduction-01.md)

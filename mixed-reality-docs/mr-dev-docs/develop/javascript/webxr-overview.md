---
title: Uso di WebXR con Windows Mixed Reality
description: Informazioni di base sull'uso e lo sviluppo per applicazioni WebXR in esecuzione Windows Mixed Reality visori immersivi.
author: yonet
ms.author: ayyonet
ms.date: 04/10/2020
ms.topic: article
keywords: WebXR, WinMR, WebAR, WebVR, WindowsMixedReality, HoloLens, windows mixed reality, web vr, web xr, web mr, web ar, 360, 360 video, 360 video, 360 foto, 360 foto, 360 foto, 360 contenuti, web immersivo, immersiveweb, IW
ms.openlocfilehash: f29be9af3a2dd1d13b301988845d0cc322e9d4de
ms.sourcegitcommit: 6ade7e8ebab7003fc24f9e0b5fa81d091369622c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2021
ms.locfileid: "112394375"
---
# <a name="webxr-overview"></a>Panoramica di WebXR

## <a name="javascript-development"></a>Sviluppo di JavaScript

JavaScript è uno dei linguaggi di programmazione più diffusi al mondo. È semplice, leggero e ampiamente usato sul Web. Sfruttare la potenza delle competenze JavaScript e Web per creare esperienze di realtà mista più coinvolgenti.

## <a name="mixed-reality-applications-on-the-web"></a>Applicazioni di realtà mista sul Web

Le funzionalità di realtà mista sono disponibili sul Web tramite [WebXR.](webxr-overview.md) È possibile visualizzare il contenuto di realtà virtuale (VR) e realtà aumentata (AR) in un browser compatibile abilitato per WebXR senza installare software o plug-in aggiuntivi. È possibile usare lo stesso browser con un dispositivo fisico come HoloLens 2.

L'API del dispositivo  [**WebXR**](https://www.w3.org/TR/webxr/) è per l'accesso ai dispositivi di  realtà virtuale **(VR)** e realtà aumentata **(AR),** inclusi sensori e schermi montati sulla testa **sul Web.** L'API del dispositivo WebXR è attualmente disponibile Microsoft Edge e Chrome versione 79 e successive supporta WebXR come impostazione predefinita. È possibile controllare lo stato di supporto del browser più recente per WebXR [all'caniuse.com](https://caniuse.com/#search=webxr).

> [!NOTE]
> **WebVR** è deprecato e non è disponibile nei browser correnti, pertanto non deve essere usato per nuovi sviluppi. Sarà necessario eseguire la migrazione di tutte le **implementazioni WebVR** esistenti in avanti a **WebXR.**

### <a name="viewing-webxr"></a>Visualizzazione di WebXR

È possibile visualizzare gli espositivi WebXR Windows Mixed Reality e il [nuovo](../../whats-new/new-microsoft-edge.md) Microsoft Edge [e Firefox Reality.](https://mixedreality.mozilla.org/firefox-reality/)
Per verificare se il browser supporta WebXR, è possibile passare a [Esempi WebXR](https://immersive-web.github.io/webxr-samples/) nel browser

## <a name="what-can-i-use-to-develop-immersive-web-experiences"></a>Cosa è possibile usare per sviluppare esperienze Web immersive?

L'elenco seguente mostra i framework e le API JavaScript per la creazione di esperienze immersive che dominano attualmente il mercato e sono ampiamente accettate e adottate dagli sviluppatori JavaScript di realtà mista:

|  |  |
| --- | --- |
|[**Babylon.js**](https://doc.babylonjs.com/)<br/><br/> Babylon è un motore 3D JavaScript che semplifica lo sviluppo di contenuti 3D e applicazioni immersive. Prima di iniziare a usare le applicazioni immersive, è consigliabile apprendere le nozioni di base Babylon.js sviluppo.<br/><br/>- Informazioni su come compilare applicazioni 3D con babylon.js [Introduzione.](https://doc.babylonjs.com/start)<br/>- Usare esempi 3D e il relativo codice sorgente usando babylon.js [Playground](https://doc.babylonjs.com/examples/)<br/>- Approfondimento su [WebXR](https://doc.babylonjs.com/divingDeeper/webXR)<br/>- Informazioni su come iniziare a usare le esercitazioni [Creare la prima app "Hello World!"](tutorials/babylonjs-webxr-helloworld/introduction-01.md)|![BabylonJS Logo](images/babylon.js.example.png) |
|[**A-Frame**](https://aframe.io/) <br/><br/>A-frame è un framework JavaScript dichiarativo per iniziare a usare la realtà virtuale sul Web. Per altre informazioni, vedere la documentazione di [A-Frame.](https://aframe.io/docs/1.2.0/introduction/) |![A-Frame](images/a-frame.example.png)  |
|[**Three.js**](https://threejs.org) <br/><br/>Three.js è una libreria 3D molto diffusa per la creazione di esperienze immersive. Altre informazioni sulle [three.js](https://threejs.org/docs/index.html#manual/en/introduction/Creating-a-scene) nella pagina della documentazione ed esplorando gli [esempi](https://threejs.org/examples/#webgl_animation_cloth). |![Three.js](images/three.js.example.png)  |
|[**WebGL**](https://developer.mozilla.org/en-US/docs/Web/API/WebGL_API)  <br/><br/>È possibile accedere direttamente alle API del dispositivo WebXR usando le API WebGL. WebGL (Web Graphics Library) è un'API JavaScript per il rendering di grafica interattiva 3D e 2D ad alte prestazioni all'interno di qualsiasi Web browser compatibile senza l'uso di plug-in. |![WebGL](images/webgl.example.png)  |

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
* [Gruppo community Web immersiva](https://www.w3.org/community/immersive-web/)
* [Github Web immersivo W3C](https://github.com/immersive-web)
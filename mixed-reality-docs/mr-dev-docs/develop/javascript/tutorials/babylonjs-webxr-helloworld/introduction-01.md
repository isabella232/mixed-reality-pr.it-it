---
title: Introduzione alle esercitazioni babylon.js e WebXR
description: Completare questo corso per informazioni su come usare babylon.js e creare un'applicazione di realtà mista di base.
author: bogenera
ms.author: ayyonet
ms.date: 03/05/2021
ms.topic: article
keywords: realtà mista, javascript, esercitazione, BabylonJS, hololens, realtà mista, UWP, Windows 10, WebXR, web immersivo
ms.localizationpriority: high
ms.openlocfilehash: 2d3f59b2769f99a756c4f0c10df1d8a8604a595e
ms.sourcegitcommit: 9ae76b339968f035c703d9c1fe57ddecb33198e3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/27/2021
ms.locfileid: "110600120"
---
# <a name="tutorial-create-your-first-webxr-application-using-babylonjs"></a>Esercitazione: Creare la prima applicazione WebXR usando babylon.js

Questa esercitazione illustra come creare un'app di realtà mista di base usando babylon.js e Visual Studio Code. L'app che si sta per compilare eseguirà il rendering di un cubo, consente di ruotarlo per visualizzare gli altri visi e aggiungere interazioni. In questa esercitazione verranno illustrate le procedure per:

> [!div class="checklist"]
> * Configurare un ambiente di sviluppo
> * Api babylon.js per creare elementi 3D di base  
> * Creare una nuova pagina Web
> * Interagire con gli elementi 3D
> * Eseguire l'applicazione in un simulatore di Windows Mixed Reality

## <a name="prerequisites"></a>Prerequisiti

* Browser supportato da WebXR, ad [esempio](../../../../whats-new/new-microsoft-edge.md) Microsoft Edge
* [Babylon.js](https://doc.babylonjs.com/divingDeeper/developWithBjs/frameworkVers) 4.2 o versione successiva
* [NodeJS](https://nodejs.org/)
* Facoltativo: [Windows 10 Creator Update](https://www.microsoft.com/software-download/windows10) se si vuole usare un simulatore di Windows Mixed Reality
* Facoltativo: [Windows Mixed Reality simulatore](../../../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md)

## <a name="getting-started"></a>Guida introduttiva

Per creare questo progetto da zero, iniziare con un progetto Visual Studio Code (VSCode).

> [!NOTE]
> L'uso di VSCode non è obbligatorio, ma verrà utilizzato per praticità durante l'esercitazione. Gli sviluppatori JavaScript più esperti possono usare qualsiasi altro editor di propria scelta, anche il Blocco note più semplice.

1. Scaricare il [babylon.js](https://doc.babylonjs.com/divingDeeper/developWithBjs/frameworkVers) file singolo o usare una versione online disponibile nel sito [Web ufficiale babylon.js](https://doc.babylonjs.com/divingDeeper/developWithBjs/frameworkVers). È anche possibile clonare l'intero babylon.js progetto da [GitHub](https://github.com/BabylonJS/Babylon.js)
1. Creare un file vuoto e salvarlo come pagina HTML, ad esempio index.html
1. Creare un markup HTML di base e fare riferimento al babylon.js javascript. Il codice finale è come illustrato di seguito:

    ```html
    <html>
        <head>
            <title>Babylon.js sample code</title>
            <script src="https://cdn.babylonjs.com/babylon.js"></script>
        </head>
    <body>
    </body>
    </html>
    ```

1. Aggiungere un elemento HTML *canvas* all'interno del corpo per eseguire il rendering del contenuto babylon.js. Si noti che l'area di disegno ha un attributo id, che consente di accedere a questo elemento HTML da JavaScript in un secondo momento.

    ```html
    <html>
        <head>
            <title>Babylon.js sample code</title>
            <script src="https://cdn.babylonjs.com/babylon.js"></script>
            <style>
                body,#renderCanvas { width: 100%; height: 100%;}
            </style>
        </head>
    <body>
        <canvas id="renderCanvas"></canvas>
    </body>
    </html>
    ```

1. L'area di disegno occupa l'intera pagina Web. Questa operazione completa la pagina Web. A questo punto, la pagina Web è pronta. È possibile aprirlo in qualsiasi browser e assicurarsi che non siano visualizzati errori, anche se non è ancora presente alcuna esperienza immersiva.

## <a name="next-steps"></a>Passaggi successivi

> [!div class="nextstepaction"]
> [Esercitazione successiva: 2. Preparare una scena](prepare-scene-02.md)
---
title: Introduzione alle esercitazioni babylon.js e WebXR
description: Completare questo corso per apprendere come usare babylon.js e creare un'applicazione di base per realtà mista.
author: bogenera
ms.author: ayyonet
ms.date: 03/05/2021
ms.topic: article
keywords: realtà mista, JavaScript, esercitazione, BabylonJS, hololens, realtà mista, UWP, Windows 10, WebXR, Web immersiva
ms.localizationpriority: high
ms.openlocfilehash: 945d27d13ac731447bd20e93805900605bc86f43
ms.sourcegitcommit: cbfd1c37612aa6904fa41642ede6281d491e478d
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/23/2021
ms.locfileid: "104946434"
---
# <a name="tutorial-create-your-first-webxr-application-using-babylonjs"></a>Esercitazione: creare la prima applicazione WebXR usando babylon.js

Questa esercitazione illustra come creare un'app di base per la realtà mista usando babylon.js e Visual Studio Code. L'app che verrà compilata compilerà il rendering di un cubo, ne consentirà la rotazione per portare gli altri visi in visualizzazione e aggiungere interazioni. In questa esercitazione verranno illustrate le procedure per:

> [!div class="checklist"]
> * Configurare un ambiente di sviluppo
> * API babylon.js per creare elementi 3D di base  
> * Crea una nuova pagina Web
> * Interagire con gli elementi 3D
> * Eseguire l'applicazione in un simulatore di realtà mista di Windows

## <a name="prerequisites"></a>Prerequisiti

* Browser supportato da WebXR, ad esempio [Microsoft Edge](https://docs.microsoft.com/windows/mixed-reality/whats-new/new-microsoft-edge)
* [Babylon.js](https://doc.babylonjs.com/divingDeeper/developWithBjs/frameworkVers) 4,2 o versione successiva
* [NodeJS](https://nodejs.org/)
* Facoltativo: [Windows 10 Creator Update](https://www.microsoft.com/software-download/windows10) se si vuole usare un simulatore di realtà mista di Windows
* Facoltativo: [simulatore di realtà mista di Windows](https://docs.microsoft.com/windows/mixed-reality/develop/platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator)

## <a name="getting-started"></a>Introduzione

Per creare il progetto da zero, iniziare con un progetto Visual Studio Code (VSCode).

> [!NOTE]
> L'uso di VSCode non è obbligatorio, ma verrà usato per praticità nell'esercitazione. Gli sviluppatori JavaScript più esperti possono utilizzare qualsiasi altro editor di propria scelta, anche il blocco note più semplice.

1. Scaricare il [babylon.js](https://doc.babylonjs.com/divingDeeper/developWithBjs/frameworkVers) singolo file o utilizzare una versione online disponibile nel [sito web ufficiale babylon.js](https://doc.babylonjs.com/divingDeeper/developWithBjs/frameworkVers). È anche possibile clonare l'intero progetto di babylon.js da [GitHub](https://github.com/BabylonJS/Babylon.js)
1. Creare un file vuoto e salvarlo come pagina HTML, ad esempio index.html
1. Creare un markup HTML di base e fare riferimento al file babylon.js JavaScript. Il codice finale è illustrato di seguito:

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

1. Aggiungere un elemento HTML *Canvas* all'interno del corpo per eseguire il rendering del contenuto di babylon.js. Si noti che l'area di disegno ha un attributo ID, che consente di accedere a questo elemento HTML da JavaScript in un secondo momento.

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

1. L'area di disegno occupa l'intera pagina Web. La pagina Web è stata completata. A questo punto, la pagina Web è pronta. È possibile aprirlo in qualsiasi browser e assicurarsi che non vengano visualizzati errori, anche se non esiste ancora un'esperienza immersiva.

## <a name="next-steps"></a>Passaggi successivi

> [!div class="nextstepaction"]
> [Esercitazione successiva: 2. preparare una scena](prepare-scene-02.md)

---
title: Creazione di un piano in WebXR con BabylonJS
description: Completare questa serie di esercitazioni per imparare a creare una tastiera per piano funzionante a 88 tasti in WebXR usando BabylonJS
author: JING1201
ms.author: v-vtieto
ms.prod: mixed-reality
ms.topic: tutorial
ms.date: 09/10/2021
keywords: realtà mista, javascript, esercitazione, BabylonJS, hololens, realtà mista, UWP, Windows 10, WebXR, web immersivo
ms.localizationpriority: high
ms.openlocfilehash: 93a3896b081e736bb62bceb6c8ae609685d7c5b5
ms.sourcegitcommit: 645608f33d2d02625484c29586f42d21c442aaa9
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/18/2021
ms.locfileid: "127932493"
---
# <a name="tutorial-build-a-piano-in-webxr-using-babylonjs"></a>Esercitazione: Creare un piano in WebXR usando Babylon.js

La creazione di un piano nel mondo reale richiede molto tempo, competenze e materiali. Che ne dici di creare una per il mondo VR/AR?

In questa serie di esercitazioni si apprenderà come usare Babylon.js per creare un'app Web di realtà mista che contiene un piano di supporto funzionante a 88 chiavi nel mondo virtuale. Nell'app completata sarà possibile teletrasportare al piano e riprodurre i tasti usando i controller di realtà mista.

In questa serie di esercitazioni si apprenderà come:

> [!div class="checklist"]
> * Creare, posizionare e unire mesh per creare una tastiera per piano
> * Importare un Babylon.js di un piano di supporto
> * Aggiungere interazioni con il puntatore a ogni tasto del piano
> * Abilitare il supporto del teletrasporto e multipointer in WebXR

## <a name="prerequisites"></a>Prerequisiti

* Un computer connesso a Internet
* Conoscenza javascript di base
* [Esercitazione su Javascript Hello World WebXR](../babylonjs-webxr-helloworld/introduction-01.md)
* Browser supportato da WebXR, ad esempio [Microsoft Edge](../../../../whats-new/new-microsoft-edge.md)
* [Babylon.js](https://doc.babylonjs.com/divingDeeper/developWithBjs/frameworkVers) 4.2 o versione successiva
* Qualsiasi [visore VR](../../../../discover/immersive-headset-hardware-details.md) [o simulatore Windows Mixed Reality virtuale](../../../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md)
* Facoltativo: [Windows 10 Creator Update](https://www.microsoft.com/software-download/windows10) se si vuole usare un simulatore di Windows Mixed Reality

## <a name="getting-started"></a>Introduzione

Si inizierà configurando la pagina Web HTML che conterrà la Babylon.js scena.

1. Creare una cartella denominata *babylonjs-piano-tutorial* e aprire la cartella in Visual Studio Code.

    > [!NOTE]
    > Anche se è possibile usare qualsiasi editor di codice per seguire questa procedura, in questa esercitazione verrà Visual Studio Code per praticità.

1. All'interno della cartella creare un file denominato *index.html* e inserire il modello seguente nel file:

    ```html
    <html>
        <head>
            <title>Piano in BabylonJS</title>
            <script src="https://cdn.babylonjs.com/babylon.js"></script>
            <style>
                body,#renderCanvas { width: 100%; height: 100%;}
            </style>
        </head>
        <body>
            <canvas id="renderCanvas"></canvas>
            <script type="text/javascript">
                const canvas = document.getElementById("renderCanvas"); 
                const engine = new BABYLON.Engine(canvas, true); 

                createScene(engine).then(sceneToRender => {
                    engine.runRenderLoop(() => sceneToRender.render());
                });
        
                // Watch for browser/canvas resize events
                window.addEventListener("resize", function () {
                    engine.resize();
                });
            </script>
        </body>
    </html>
    ```

    Per altre spiegazioni sul contenuto di questo modello, vedere l'esercitazione Hello World [,](../babylonjs-webxr-helloworld/introduction-01.md)che è un prerequisito di questa esercitazione.

1. Se si tenta di aprire questo file in un browser, nella console viene visualizzato un errore che indica che la funzione `createScene()` non è stata trovata. Risolvere questo errore implementando la funzione `createScene()` nella sezione successiva.

## <a name="setup-the-scene"></a>Configurare la scena

1. Nella stessa cartella di *index.html* creare un altro file denominato *scene.js*. Tutto il codice JavaScript correlato alla configurazione della scena e alla creazione del piano in questo file verrà archiviata.

1. Aggiungere la funzione in `createScene()`scene.js: **

    ```javascript
    const createScene = async function(engine) {
        const scene = new BABYLON.Scene(engine);
        return scene;
    }
    ```

    Si noti che si sta `createScene()` effettuando una funzione asincrona. Rimanere ottimizzati per scoprire perché.

1. Saranno quindi necessari una luce e una fotocamera per rendere visibile la scena. Aggiornare la `createScene()` funzione:

    ```javascript
    const createScene = async function(engine) {
        const scene = new BABYLON.Scene(engine);

        const alpha =  3*Math.PI/2;
        const beta = Math.PI/50;
        const radius = 220;
        const target = new BABYLON.Vector3(0, 0, 0);
        
        const camera = new BABYLON.ArcRotateCamera("Camera", alpha, beta, radius, target, scene);
        camera.attachControl(canvas, true);
        
        const light = new BABYLON.HemisphericLight("light", new BABYLON.Vector3(0, 1, 0), scene);
        light.intensity = 0.6;

        return scene;
    }
    ```

    In questo caso è stato creato [un oggetto ArcRotateCamera,](https://doc.babylonjs.com/divingDeeper/cameras/camera_introduction#arc-rotate-camera)che punta quasi completamente verso il basso e punta al punto di origine dello spazio. La luce creata è un [oggetto HemisphericLight](https://doc.babylonjs.com/divingDeeper/lights/lights_introduction#the-hemispheric-light) che punta al cielo ed è utile per simulare uno spazio ambientale. Abbiamo anche abbassato leggermente la luce abbassando l'intensità.

    Se è necessario un aggiornamento su come creare una fotocamera e una luce, rivedere la sezione Preparare la scena della serie di esercitazioni [Hello World](../babylonjs-webxr-helloworld/prepare-scene-02.md#add-a-camera) prima di procedere al passaggio successivo.

1. Infine, poiché si sta sviluppando per una piattaforma WebXR, è necessario abilitare l'esperienza [XR](https://doc.babylonjs.com/divingDeeper/webXR/introToWebXR) nella scena inserendo la riga seguente prima di `return scene;` :

    ```javascript
    const xrHelper = await scene.createDefaultXRExperienceAsync();
    ```

    In javascript, per usare la tastiera in una funzione all'interno di una funzione, anche la funzione padre deve essere , motivo per cui in precedenza la funzione è stata definita `await` `async` come `async` `createScene` asincrona. Più avanti in questa serie di esercitazioni verrà utilizzato per abilitare e configurare diverse `xrHelper` funzionalità WebXR supportate da Babylon.js.

1. Il valore *scene.js* dovrebbe essere simile al seguente:

    ```javascript
    const createScene = async function(engine) {
        const scene = new BABYLON.Scene(engine);
        
        const alpha =  3*Math.PI/2;
        const beta = Math.PI/50;
        const radius = 220;
        const target = new BABYLON.Vector3(0, 0, 0);
        
        const camera = new BABYLON.ArcRotateCamera("Camera", alpha, beta, radius, target, scene);
        camera.attachControl(canvas, true);
        
        const light = new BABYLON.HemisphericLight("light", new BABYLON.Vector3(0, 1, 0), scene);
        light.intensity = 0.6;
    
        const xrHelper = await scene.createDefaultXRExperienceAsync();
    
        return scene;
    }
    ```

1. Ora che è disponibile una funzione funzionante,index.htmlcaricare il filescene.jscome script in modo che la funzione sia riconosciuta `createScene()` in   `createScene()` *index.html*. Aggiungere questa riga di codice `<header>` all'interno della sezione del file html:

    ```html
    <html>
        <head>
            <title>Piano in BabylonJS</title>
            <script src="https://cdn.babylonjs.com/babylon.js"></script>
            <script src="scene.js"></script>
            <style>
                body,#renderCanvas { width: 100%; height: 100%;}
            </style>
        </head>
        <body>
            <canvas id="renderCanvas"></canvas>
            <script type="text/javascript">
                const canvas = document.getElementById("renderCanvas");
                const engine = new BABYLON.Engine(canvas, true); 

                createScene(engine).then(sceneToRender => {
                    engine.runRenderLoop(() => sceneToRender.render());
                });
                
                // Watch for browser/canvas resize events
                window.addEventListener("resize", function () {
                    engine.resize();
                });
            </script>
        </body>
    </html>
    ```

1. Aprire *index.html* nel browser e si scoprirà che il messaggio di errore visualizzato in precedenza non è più presente e che nella pagina è presente una scena di Babylon.js vuota.

## <a name="next-steps"></a>Passaggi successivi

> [!div class="nextstepaction"]
> [Esercitazione successiva: Creare un modello di piano 3D](keyboard-model-02.md)

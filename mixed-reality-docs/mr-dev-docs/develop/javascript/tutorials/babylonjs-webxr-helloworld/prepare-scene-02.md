---
title: Babylon.js esercitazione per preparare una scena con oggetti 3D di base
description: Informazioni su come usare babylon.js e aggiungere oggetti 3D di base a una scena.
author: bogenera
ms.author: ayyonet
ms.date: 03/05/2021
ms.topic: article
keywords: realtà mista, JavaScript, esercitazione, BabylonJS, hololens, realtà mista, UWP, Windows 10, WebXR, Web immersiva
ms.localizationpriority: high
ms.openlocfilehash: 3f601089132593b63cfa3f04cc62cb0775cc6e5e
ms.sourcegitcommit: cbfd1c37612aa6904fa41642ede6281d491e478d
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/23/2021
ms.locfileid: "104946436"
---
# <a name="tutorial-prepare-a-scene"></a>Esercitazione: preparare una scena

Informazioni su come preparare una scena e aggiungere alcuni elementi 3D di base.

In questa esercitazione si apprenderà come:

> [!div class="checklist"]
> * Creare una scena
> * Aggiungere una fotocamera
> * Aggiungi luce
> * Aggiungi elementi 3D di base

## <a name="before-you-begin"></a>Prima di iniziare

Nel passaggio precedente dell'esercitazione è stata creata una pagina Web di base. Aprire la pagina Web per la modifica.

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

## <a name="create-a-scene"></a>Creare una scena

Una scena è la posizione in cui verrà visualizzato tutto il contenuto. Potrebbero essere presenti più scene ed è possibile passare da una scena all'altra. Scopri di più su [babylon.js scena](https://doc.babylonjs.com/divingDeeper/scene).

1. Aggiungere il tag script dopo l'elemento HTML Canvas e aggiungere il codice seguente per creare una scena riempita con il colore nero:

    ```html
    <script type="text/javascript">
        var canvas = document.getElementById("renderCanvas");
        var engine = new BABYLON.Engine(canvas, true);
        
        const createScene = function() {
            const scene = new BABYLON.Scene(engine);
            scene.clearColor = new BABYLON.Color3.Black;
            return scene;
        }

        var sceneToRender = createScene();
    </script>
    ```

    Nel codice precedente è necessario creare un'istanza di babylon.js motore di rendering Web che esegue il rendering di una scena e associa gli eventi nell'area di disegno. Per altre informazioni sul motore, vedere la pagina della documentazione [Babylon. Engine](https://doc.babylonjs.com/typedoc/classes/babylon.engine)

1. Per impostazione predefinita, non viene eseguito il rendering della scena. Tenere presente che potrebbero essere presenti più scene e si controlla quale scena viene visualizzata. Per eseguire ripetutamente il rendering della scena in ogni frame, eseguire il codice seguente dopo la chiamata alla funzione *createScene* :

    ```javascript
    engine.runRenderLoop(function () {
        sceneToRender.render();
    });
    ```

## <a name="add-basic-3d-element"></a>Aggiungi elemento 3D di base

1. Aggiungere la prima forma 3D. Nelle forme 3D Virtual World sono compilate da *mesh*, molti facet triangolari Uniti in join, ognuno dei quali è costituito da tre vertici. È possibile usare una mesh predefinita o creare una mesh personalizzata. Qui verrà usata una Mesh Box predefinita, ad esempio un cubo. Per creare la casella usare [Babylon. MeshBuilder. CreateBox](https://doc.babylonjs.com/divingDeeper/mesh/creation/set/box). I parametri sono Name e Options (le opzioni sono diverse in base al tipo di mesh). Aggiungere il codice seguente alla funzione *createScene*:

    ```javascript
    const box = BABYLON.MeshBuilder.CreateBox("box", {});
    box.position.x = 0.5;
    box.position.y = 1;
    ```

1. Aprire la pagina Web nel browser Microsoft Edge e controllare l'output. Nella finestra del browser viene visualizzata una pagina vuota. Aprire DevTools usando la tastiera e selezionare F12 o CTRL + MAIUSC + I (Windows, Linux) o comando + opzione + I (macOS). Dopo aver aperto la scheda della *console* , è possibile iniziare a cercare gli errori. Verrà visualizzato un errore:' errore non rilevato: Nessuna fotocamera definita. A questo punto è necessario aggiungere una fotocamera alla scena.

## <a name="add-a-camera"></a>Aggiungere una fotocamera

1. Per consentire l'input dell'utente, è necessario collegare una fotocamera all'area di disegno. Aggiungere la fotocamera di tipo [Babylon. ArcRotateCamera](https://doc.babylonjs.com/divingDeeper/cameras/camera_introduction#arc-rotate-camera) che ci permette di cercare, ovvero può essere ruotato intorno all'oggetto appena aggiunto alla scena. I parametri necessari per creare un'istanza della fotocamera sono nome, Alfa (rotazione lungo l'asse longitudinale), beta (rotazione lungo l'asse latitudinali), raggio (distanza dalla destinazione) e destinazione (la destinazione che la fotocamera dovrebbe esaminare). Aggiungere il codice seguente alla funzione *createScene* :

    ```javascript
    const alpha =  Math.PI;
    const beta = Math.PI;
    const radius = 5;
    
    const camera = new BABYLON.ArcRotateCamera("Camera", 0, 0, 0);
    camera.setPosition(new BABYLON.Vector3(alpha, beta, radius));
    camera.attachControl(canvas, true);
    ```

1. Se si seleziona l'output nel browser, viene visualizzata un'area di disegno nera. La luce è mancante.

## <a name="add-light"></a>Aggiungi luce

1. Sono disponibili quattro tipi di luci che è possibile usare con una gamma di proprietà di illuminazione: punto, direzionale, spot e emisfero chiaro. Aggiungere la luce di ambiente [HemisphericLight](https://doc.babylonjs.com/typedoc/classes/babylon.hemisphericlight), come indicato di seguito:

    ```javascript
    const light = new BABYLON.HemisphericLight("light", new BABYLON.Vector3(1, 1, 0));
    ```

1. Il codice finale della pagina Web sarà simile al seguente:

    ```html
    <html>
    <head>
        <script src="https://cdn.babylonjs.com/babylon.js"></script>
        <style>
            body,#renderCanvas { width: 100%; height: 100%;}
        </style>
    </head>
    <body>
        <canvas id="renderCanvas"></canvas>
        <script>
            var canvas = document.getElementById("renderCanvas");
            var engine = new BABYLON.Engine(canvas, true);
            
            var createScene = function() {
                const scene = new BABYLON.Scene(engine);
                scene.clearColor = new BABYLON.Color3.Black;
                
                const alpha =  Math.PI;
                const beta = Math.PI;
                const radius = 5;
                
                const camera = new BABYLON.ArcRotateCamera("Camera", 0, 0, 0);
                camera.setPosition(new BABYLON.Vector3(alpha, beta, radius));
                camera.attachControl(canvas, true);
                
                const light = new BABYLON.HemisphericLight("light", new BABYLON.Vector3(1, 1, 0));
                
                const box = BABYLON.MeshBuilder.CreateBox("box", {});
                box.position.x = 0.5;
                box.position.y = 1;
                
                return scene;
            };
            
            var sceneToRender = createScene();
            engine.runRenderLoop(function(){
                sceneToRender.render();
            });
        </script>
    </body>
    </html>
    ```

1. Controllare l'output nel browser. Il cubo verrà visualizzato e si potrà utilizzare il mouse per ruotare la fotocamera attorno al cubo e visualizzare i diversi visi del cubo:

![Scena di base con cubo](../images/hello-world-basic-scene.png)

## <a name="next-steps"></a>Passaggi successivi

> [!div class="nextstepaction"]
> [Esercitazione successiva: 3. interagire con l'oggetto 3D](interact-03.md)

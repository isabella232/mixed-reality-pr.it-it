---
title: Babylon.js per preparare una scena con oggetti 3D di base
description: Informazioni su come usare babylon.js aggiungere oggetti 3D di base a una scena.
author: bogenera
ms.author: ayyonet
ms.date: 03/05/2021
ms.topic: article
keywords: realtà mista, javascript, esercitazione, BabylonJS, hololens, realtà mista, UWP, Windows 10, WebXR, web immersive
ms.localizationpriority: high
ms.openlocfilehash: 8213c445da9c1bbf0eeb591b7995fb61bc6d5b5f
ms.sourcegitcommit: 29a43366d5969f1a895bd184ebe272168d9be1e2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/27/2021
ms.locfileid: "110584506"
---
# <a name="tutorial-prepare-a-scene"></a>Esercitazione: Preparare una scena

Informazioni su come preparare una scena e aggiungervi alcuni elementi 3D di base.

In questa esercitazione si apprenderà come:

> [!div class="checklist"]
> * Creare una scena
> * Aggiungere una fotocamera
> * Aggiungi luce
> * Aggiungere elementi 3D di base

## <a name="before-you-begin"></a>Prima di iniziare

Nel passaggio precedente dell'esercitazione è stata creata una pagina Web di base. Fare in modo che la pagina Web sia aperta per la modifica.

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

Una scena è la posizione in cui verrà visualizzato tutto il contenuto. Potrebbero essere presenti più scene ed è possibile passare da una scena all'altro. Altre informazioni su [babylon.js scene.](https://doc.babylonjs.com/divingDeeper/scene)

1. Aggiungere il tag di script dopo l'elemento HTML canvas e aggiungere il codice seguente per creare una scena color nero:

    ```html
    <script type="text/javascript">
        const canvas = document.getElementById("renderCanvas");
        const engine = new BABYLON.Engine(canvas, true);
        
        const createScene = function() {
            const scene = new BABYLON.Scene(engine);
            scene.clearColor = new BABYLON.Color3.Black;
            return scene;
        }

        const sceneToRender = createScene();
    </script>
    ```

    Nel codice precedente è necessario creare un'istanza di babylon.js di rendering Web che esegue il rendering di una scena e collega gli eventi nell'area di disegno. Per altre informazioni sul motore, vedere la pagina della documentazione [babylon.engine](https://doc.babylonjs.com/typedoc/classes/babylon.engine)

1. Il rendering della scena non viene eseguito per impostazione predefinita. Tenere presente che potrebbero essere presenti più scene e si controlla quale scena viene visualizzata. Per eseguire ripetutamente il rendering della scena in ogni fotogramma, eseguire il codice seguente dopo la chiamata alla *funzione createScene:*

    ```javascript
    engine.runRenderLoop(function () {
        sceneToRender.render();
    });
    ```

## <a name="add-basic-3d-element"></a>Aggiungere un elemento 3D di base

1. Aggiungere la prima forma 3D. Nel mondo virtuale 3D le forme sono create da *mesh*, molti facet triangolari uniti, ognuno dei quali costituito da tre vertici. È possibile usare una mesh predefinita o creare una mesh personalizzata. In questo caso verrà utilizzata una mesh predefinita, ad esempio un cubo. Per creare la casella, [usare BABYLON. MeshBuilder.CreateBox](https://doc.babylonjs.com/divingDeeper/mesh/creation/set/box). I parametri sono name e options (le opzioni sono diverse in base al tipo di mesh). Aggiungere il codice seguente alla funzione *createScene*:

    ```javascript
    const box = BABYLON.MeshBuilder.CreateBox("box", {});
    box.position.x = 0.5;
    box.position.y = 1;
    ```

1. Aprire la pagina Web nel browser Microsoft Edge e controllare l'output. La finestra del browser mostra una pagina vuota. Aprire DevTools usando la tastiera e selezionare F12 o CTRL+MAIUSC+I (Windows, Linux) o Comando+Opzione+I (macOS). Dopo aver aperto *la scheda Console,* è possibile iniziare a cercare gli errori. Verrà visualizzato un errore: "Errore non rilevato: Nessuna fotocamera definita". A questo punto è necessario aggiungere una fotocamera alla scena.

## <a name="add-a-camera"></a>Aggiungere una fotocamera

1. Per visualizzare il mondo virtuale e interagire con esso, è necessario collegare una fotocamera all'area di disegno. Aggiungere la fotocamera di tipo [BABYLON. ArcRotateCamera,](https://doc.babylonjs.com/divingDeeper/cameras/camera_introduction#arc-rotate-camera)che può essere ruotato intorno a una destinazione. I parametri necessari per creare un'istanza della fotocamera sono:
    1. **name:** nome della fotocamera
    1. **alpha:** posizione angolare lungo l'asse longitudinale (in radianti)
    1. **beta:** posizione angolare lungo l'asse latitudine (in radianti)
    1. **radius:** distanza dalla destinazione
    1. **target:** il punto verso cui la fotocamera deve sempre essere puntata verso (definito dalle coordinate x-y-z)
    1. **scene:** la scena in cui si trova la fotocamera

    Alfa, beta, raggio e destinazione definiscono insieme la posizione della fotocamera nello spazio, come illustrato nel diagramma seguente:

    ![Camera Alpha Beta Radius](../images/camera-alpha-beta-radius.jpg)

    Aggiungere il codice seguente alla *funzione createScene:*

    ```javascript
    const alpha =  Math.PI/4;
    const beta = Math.PI/3;
    const radius = 8;
    const target = new BABYLON.Vector3(0, 0, 0);
    
    const camera = new BABYLON.ArcRotateCamera("Camera", alpha, beta, radius, target, scene);
    camera.attachControl(canvas, true);
    ```

1. Se si controlla l'output nel browser, verrà visualizzata un'area di disegno nera. Manca la luce.

## <a name="add-light"></a>Aggiungi luce

1. Esistono quattro tipi di luci che possono essere usati con una gamma di proprietà di illuminazione: Punto, Direzionale, Spot e Luce emisferica. Aggiungere la luce ambientale [HemisphericLight,](https://doc.babylonjs.com/typedoc/classes/babylon.hemisphericlight)come indicato di seguito:

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
            const canvas = document.getElementById("renderCanvas");
            const engine = new BABYLON.Engine(canvas, true);
            
            const createScene = function() {
                const scene = new BABYLON.Scene(engine);
                scene.clearColor = new BABYLON.Color3.Black;
                
                const alpha =  Math.PI/4;
                const beta = Math.PI/3;
                const radius = 8;
                const target = new BABYLON.Vector3(0, 0, 0);
                
                const camera = new BABYLON.ArcRotateCamera("Camera", alpha, beta, radius, target, scene);
                camera.attachControl(canvas, true);
                
                const light = new BABYLON.HemisphericLight("light", new BABYLON.Vector3(1, 1, 0));
                
                const box = BABYLON.MeshBuilder.CreateBox("box", {});
                box.position.x = 0.5;
                box.position.y = 1;
                
                return scene;
            };
            
            const sceneToRender = createScene();
            engine.runRenderLoop(function(){
                sceneToRender.render();
            });
        </script>
    </body>
    </html>
    ```

1. Controllare l'output nel browser. Dovrebbe essere visualizzato il cubo e usando il mouse è possibile ruotare la fotocamera intorno al cubo e visualizzare i diversi visi del cubo:

![Scena di base con cubo](../images/hello-world-basic-scene.png)

## <a name="next-steps"></a>Passaggi successivi

> [!div class="nextstepaction"]
> [Esercitazione successiva: 3. Interagire con un oggetto 3D](interact-03.md)

---
title: Babylon.js per preparare una scena con oggetti 3D di base
description: Informazioni su come usare babylon.js e aggiungere oggetti 3D di base a una scena.
author: bogenera
ms.author: ayyonet
ms.date: 03/05/2021
ms.topic: article
keywords: realtà mista, javascript, esercitazione, BabylonJS, hololens, realtà mista, UWP, Windows 10, WebXR, web immersive
ms.localizationpriority: high
ms.openlocfilehash: 963589cb221b7dba1c197fff06ccb8926e12f89c
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143681"
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

In una scena verranno visualizzati tutti i contenuti. Potrebbero essere presenti più scene ed è possibile passare da una scena all'altro. Altre informazioni su [babylon.js scene.](https://doc.babylonjs.com/divingDeeper/scene)

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

1. Per consentire l'input dell'utente, è necessario collegare una fotocamera all'area di disegno. Aggiungere la fotocamera di tipo [BABYLON. ArcRotateCamera,](https://doc.babylonjs.com/divingDeeper/cameras/camera_introduction#arc-rotate-camera) che consente di guardarsi attorno, ad esempio può essere ruotato intorno all'oggetto appena aggiunto alla scena. I parametri necessari per creare un'istanza della fotocamera sono nome, alfa (rotazione lungo l'asse longitudinale), beta (rotazione lungo l'asse latitudine), raggio (distanza dalla destinazione) e destinazione (destinazione che deve essere osservata dalla fotocamera). Aggiungere il codice seguente alla *funzione createScene:*

    ```javascript
    const alpha =  Math.PI;
    const beta = Math.PI;
    const radius = 5;
    
    const camera = new BABYLON.ArcRotateCamera("Camera", 0, 0, 0);
    camera.setPosition(new BABYLON.Vector3(alpha, beta, radius));
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

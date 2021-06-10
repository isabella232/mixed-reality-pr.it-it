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
# <a name="tutorial-prepare-a-scene"></a><span data-ttu-id="78f33-104">Esercitazione: Preparare una scena</span><span class="sxs-lookup"><span data-stu-id="78f33-104">Tutorial: Prepare a scene</span></span>

<span data-ttu-id="78f33-105">Informazioni su come preparare una scena e aggiungervi alcuni elementi 3D di base.</span><span class="sxs-lookup"><span data-stu-id="78f33-105">Learn how to prepare a scene, and add some basic 3D elements to it.</span></span>

<span data-ttu-id="78f33-106">In questa esercitazione si apprenderà come:</span><span class="sxs-lookup"><span data-stu-id="78f33-106">In this tutorial, learn how to:</span></span>

> [!div class="checklist"]
> * <span data-ttu-id="78f33-107">Creare una scena</span><span class="sxs-lookup"><span data-stu-id="78f33-107">Create a scene</span></span>
> * <span data-ttu-id="78f33-108">Aggiungere una fotocamera</span><span class="sxs-lookup"><span data-stu-id="78f33-108">Add a camera</span></span>
> * <span data-ttu-id="78f33-109">Aggiungi luce</span><span class="sxs-lookup"><span data-stu-id="78f33-109">Add light</span></span>
> * <span data-ttu-id="78f33-110">Aggiungere elementi 3D di base</span><span class="sxs-lookup"><span data-stu-id="78f33-110">Add basic 3D elements</span></span>

## <a name="before-you-begin"></a><span data-ttu-id="78f33-111">Prima di iniziare</span><span class="sxs-lookup"><span data-stu-id="78f33-111">Before you begin</span></span>

<span data-ttu-id="78f33-112">Nel passaggio precedente dell'esercitazione è stata creata una pagina Web di base.</span><span class="sxs-lookup"><span data-stu-id="78f33-112">In previous tutorial step a basic web page was created.</span></span> <span data-ttu-id="78f33-113">Fare in modo che la pagina Web sia aperta per la modifica.</span><span class="sxs-lookup"><span data-stu-id="78f33-113">Have the web page open for editing.</span></span>

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

## <a name="create-a-scene"></a><span data-ttu-id="78f33-114">Creare una scena</span><span class="sxs-lookup"><span data-stu-id="78f33-114">Create a scene</span></span>

<span data-ttu-id="78f33-115">Una scena è la posizione in cui verrà visualizzato tutto il contenuto.</span><span class="sxs-lookup"><span data-stu-id="78f33-115">A scene is where all the contents will be displayed.</span></span> <span data-ttu-id="78f33-116">Potrebbero essere presenti più scene ed è possibile passare da una scena all'altro.</span><span class="sxs-lookup"><span data-stu-id="78f33-116">There might be multiple scenes and it is possible to switch between scenes.</span></span> <span data-ttu-id="78f33-117">Altre informazioni su [babylon.js scene.](https://doc.babylonjs.com/divingDeeper/scene)</span><span class="sxs-lookup"><span data-stu-id="78f33-117">Read more about [babylon.js Scene](https://doc.babylonjs.com/divingDeeper/scene).</span></span>

1. <span data-ttu-id="78f33-118">Aggiungere il tag di script dopo l'elemento HTML canvas e aggiungere il codice seguente per creare una scena color nero:</span><span class="sxs-lookup"><span data-stu-id="78f33-118">Add the script tag after the canvas html element and add the following code to create a scene filled in black color:</span></span>

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

    <span data-ttu-id="78f33-119">Nel codice precedente è necessario creare un'istanza di babylon.js di rendering Web che esegue il rendering di una scena e collega gli eventi nell'area di disegno.</span><span class="sxs-lookup"><span data-stu-id="78f33-119">In the code above we have to create an instance of babylon.js web rendering engine that renders a scene and hooks events on the canvas.</span></span> <span data-ttu-id="78f33-120">Per altre informazioni sul motore, vedere la pagina della documentazione [babylon.engine](https://doc.babylonjs.com/typedoc/classes/babylon.engine)</span><span class="sxs-lookup"><span data-stu-id="78f33-120">For more information about the engine, check the documentation page [babylon.engine](https://doc.babylonjs.com/typedoc/classes/babylon.engine)</span></span>

1. <span data-ttu-id="78f33-121">Il rendering della scena non viene eseguito per impostazione predefinita.</span><span class="sxs-lookup"><span data-stu-id="78f33-121">The scene is not rendered by default.</span></span> <span data-ttu-id="78f33-122">Tenere presente che potrebbero essere presenti più scene e si controlla quale scena viene visualizzata.</span><span class="sxs-lookup"><span data-stu-id="78f33-122">Remember, there might be multiple scenes and you control which scene is displayed.</span></span> <span data-ttu-id="78f33-123">Per eseguire ripetutamente il rendering della scena in ogni fotogramma, eseguire il codice seguente dopo la chiamata alla *funzione createScene:*</span><span class="sxs-lookup"><span data-stu-id="78f33-123">To render the scene repeatedly on every frame, execute the following code after the call to *createScene* function:</span></span>

    ```javascript
    engine.runRenderLoop(function () {
        sceneToRender.render();
    });
    ```

## <a name="add-basic-3d-element"></a><span data-ttu-id="78f33-124">Aggiungere un elemento 3D di base</span><span class="sxs-lookup"><span data-stu-id="78f33-124">Add basic 3D element</span></span>

1. <span data-ttu-id="78f33-125">Aggiungere la prima forma 3D.</span><span class="sxs-lookup"><span data-stu-id="78f33-125">Let's add our first 3D shape.</span></span> <span data-ttu-id="78f33-126">Nel mondo virtuale 3D le forme sono create da *mesh*, molti facet triangolari uniti, ognuno dei quali costituito da tre vertici.</span><span class="sxs-lookup"><span data-stu-id="78f33-126">In the 3D virtual world shapes are built from *meshes*, lots of triangular facets joined together, each facet made from three vertices.</span></span> <span data-ttu-id="78f33-127">È possibile usare una mesh predefinita o creare una mesh personalizzata.</span><span class="sxs-lookup"><span data-stu-id="78f33-127">You can either use a predefined mesh or create your own custom mesh.</span></span> <span data-ttu-id="78f33-128">In questo caso verrà utilizzata una mesh predefinita, ad esempio un cubo.</span><span class="sxs-lookup"><span data-stu-id="78f33-128">Here we will be using a predefined box mesh, i.e. a cube.</span></span> <span data-ttu-id="78f33-129">Per creare la casella, [usare BABYLON. MeshBuilder.CreateBox](https://doc.babylonjs.com/divingDeeper/mesh/creation/set/box).</span><span class="sxs-lookup"><span data-stu-id="78f33-129">To create the box use [BABYLON.MeshBuilder.CreateBox](https://doc.babylonjs.com/divingDeeper/mesh/creation/set/box).</span></span> <span data-ttu-id="78f33-130">I parametri sono name e options (le opzioni sono diverse in base al tipo di mesh).</span><span class="sxs-lookup"><span data-stu-id="78f33-130">The parameters are name, and options (options are different according to the type of mesh).</span></span> <span data-ttu-id="78f33-131">Aggiungere il codice seguente alla funzione *createScene*:</span><span class="sxs-lookup"><span data-stu-id="78f33-131">Append the following code to the function *createScene*:</span></span>

    ```javascript
    const box = BABYLON.MeshBuilder.CreateBox("box", {});
    box.position.x = 0.5;
    box.position.y = 1;
    ```

1. <span data-ttu-id="78f33-132">Aprire la pagina Web nel browser Microsoft Edge e controllare l'output.</span><span class="sxs-lookup"><span data-stu-id="78f33-132">Open the web page in the Microsoft Edge browser and check the output.</span></span> <span data-ttu-id="78f33-133">La finestra del browser mostra una pagina vuota.</span><span class="sxs-lookup"><span data-stu-id="78f33-133">The browser window shows a blank page.</span></span> <span data-ttu-id="78f33-134">Aprire DevTools usando la tastiera e selezionare F12 o CTRL+MAIUSC+I (Windows, Linux) o Comando+Opzione+I (macOS).</span><span class="sxs-lookup"><span data-stu-id="78f33-134">Open DevTools by using the keyboard and select F12 or Control+Shift+I (Windows, Linux) or Command+Option+I (macOS).</span></span> <span data-ttu-id="78f33-135">Dopo aver aperto *la scheda Console,* è possibile iniziare a cercare gli errori.</span><span class="sxs-lookup"><span data-stu-id="78f33-135">After opening the *Console* tab, you can start looking for errors.</span></span> <span data-ttu-id="78f33-136">Verrà visualizzato un errore: "Errore non rilevato: Nessuna fotocamera definita".</span><span class="sxs-lookup"><span data-stu-id="78f33-136">There will be an error displayed: 'Uncaught Error: No camera defined'.</span></span> <span data-ttu-id="78f33-137">A questo punto è necessario aggiungere una fotocamera alla scena.</span><span class="sxs-lookup"><span data-stu-id="78f33-137">Now we have to add a camera to the scene.</span></span>

## <a name="add-a-camera"></a><span data-ttu-id="78f33-138">Aggiungere una fotocamera</span><span class="sxs-lookup"><span data-stu-id="78f33-138">Add a camera</span></span>

1. <span data-ttu-id="78f33-139">Per visualizzare il mondo virtuale e interagire con esso, è necessario collegare una fotocamera all'area di disegno.</span><span class="sxs-lookup"><span data-stu-id="78f33-139">In order to view the virtual world and interact with it, a camera must be attached to the canvas.</span></span> <span data-ttu-id="78f33-140">Aggiungere la fotocamera di tipo [BABYLON. ArcRotateCamera,](https://doc.babylonjs.com/divingDeeper/cameras/camera_introduction#arc-rotate-camera)che può essere ruotato intorno a una destinazione.</span><span class="sxs-lookup"><span data-stu-id="78f33-140">Let's add the camera of type [BABYLON.ArcRotateCamera](https://doc.babylonjs.com/divingDeeper/cameras/camera_introduction#arc-rotate-camera), which can be rotated around a target.</span></span> <span data-ttu-id="78f33-141">I parametri necessari per creare un'istanza della fotocamera sono:</span><span class="sxs-lookup"><span data-stu-id="78f33-141">The parameters required to create an instance of the camera are:</span></span>
    1. <span data-ttu-id="78f33-142">**name:** nome della fotocamera</span><span class="sxs-lookup"><span data-stu-id="78f33-142">**name**: name of the camera</span></span>
    1. <span data-ttu-id="78f33-143">**alpha:** posizione angolare lungo l'asse longitudinale (in radianti)</span><span class="sxs-lookup"><span data-stu-id="78f33-143">**alpha**: angular position along the longitudinal axis (in radians)</span></span>
    1. <span data-ttu-id="78f33-144">**beta:** posizione angolare lungo l'asse latitudine (in radianti)</span><span class="sxs-lookup"><span data-stu-id="78f33-144">**beta**: angular position along the latitudinal axis (in radians)</span></span>
    1. <span data-ttu-id="78f33-145">**radius:** distanza dalla destinazione</span><span class="sxs-lookup"><span data-stu-id="78f33-145">**radius**: distance from the target</span></span>
    1. <span data-ttu-id="78f33-146">**target:** il punto verso cui la fotocamera deve sempre essere puntata verso (definito dalle coordinate x-y-z)</span><span class="sxs-lookup"><span data-stu-id="78f33-146">**target**: the point that the camera would always face towards (defined by x-y-z coordinates)</span></span>
    1. <span data-ttu-id="78f33-147">**scene:** la scena in cui si trova la fotocamera</span><span class="sxs-lookup"><span data-stu-id="78f33-147">**scene**: the scene that the camera is in</span></span>

    <span data-ttu-id="78f33-148">Alfa, beta, raggio e destinazione definiscono insieme la posizione della fotocamera nello spazio, come illustrato nel diagramma seguente:</span><span class="sxs-lookup"><span data-stu-id="78f33-148">Alpha, beta, radius, and target together define the camera's position in the space, as shown in the diagram below:</span></span>

    ![Camera Alpha Beta Radius](../images/camera-alpha-beta-radius.jpg)

    <span data-ttu-id="78f33-150">Aggiungere il codice seguente alla *funzione createScene:*</span><span class="sxs-lookup"><span data-stu-id="78f33-150">Add the following code to the *createScene* function:</span></span>

    ```javascript
    const alpha =  Math.PI/4;
    const beta = Math.PI/3;
    const radius = 8;
    const target = new BABYLON.Vector3(0, 0, 0);
    
    const camera = new BABYLON.ArcRotateCamera("Camera", alpha, beta, radius, target, scene);
    camera.attachControl(canvas, true);
    ```

1. <span data-ttu-id="78f33-151">Se si controlla l'output nel browser, verrà visualizzata un'area di disegno nera.</span><span class="sxs-lookup"><span data-stu-id="78f33-151">If you check the output in the browser, you will see a black canvas.</span></span> <span data-ttu-id="78f33-152">Manca la luce.</span><span class="sxs-lookup"><span data-stu-id="78f33-152">We are missing the light.</span></span>

## <a name="add-light"></a><span data-ttu-id="78f33-153">Aggiungi luce</span><span class="sxs-lookup"><span data-stu-id="78f33-153">Add light</span></span>

1. <span data-ttu-id="78f33-154">Esistono quattro tipi di luci che possono essere usati con una gamma di proprietà di illuminazione: Punto, Direzionale, Spot e Luce emisferica.</span><span class="sxs-lookup"><span data-stu-id="78f33-154">There are four types of lights that can be used with a range of lighting properties: Point, Directional, Spot and Hemispheric Light.</span></span> <span data-ttu-id="78f33-155">Aggiungere la luce ambientale [HemisphericLight,](https://doc.babylonjs.com/typedoc/classes/babylon.hemisphericlight)come indicato di seguito:</span><span class="sxs-lookup"><span data-stu-id="78f33-155">Let's add the ambient light [HemisphericLight](https://doc.babylonjs.com/typedoc/classes/babylon.hemisphericlight), as follows:</span></span>

    ```javascript
    const light = new BABYLON.HemisphericLight("light", new BABYLON.Vector3(1, 1, 0));
    ```

1. <span data-ttu-id="78f33-156">Il codice finale della pagina Web sarà simile al seguente:</span><span class="sxs-lookup"><span data-stu-id="78f33-156">The final code of the web page will look as follows:</span></span>

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

1. <span data-ttu-id="78f33-157">Controllare l'output nel browser.</span><span class="sxs-lookup"><span data-stu-id="78f33-157">Check the output in the browser.</span></span> <span data-ttu-id="78f33-158">Dovrebbe essere visualizzato il cubo e usando il mouse è possibile ruotare la fotocamera intorno al cubo e visualizzare i diversi visi del cubo:</span><span class="sxs-lookup"><span data-stu-id="78f33-158">You should see the cube and using the mouse you can rotate the camera around the cube and see the different faces of the cube:</span></span>

![Scena di base con cubo](../images/hello-world-basic-scene.png)

## <a name="next-steps"></a><span data-ttu-id="78f33-160">Passaggi successivi</span><span class="sxs-lookup"><span data-stu-id="78f33-160">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="78f33-161">Esercitazione successiva: 3. Interagire con un oggetto 3D</span><span class="sxs-lookup"><span data-stu-id="78f33-161">Next Tutorial: 3. Interact with 3D object</span></span>](interact-03.md)

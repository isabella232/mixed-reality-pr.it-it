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
# <a name="tutorial-prepare-a-scene"></a><span data-ttu-id="59818-104">Esercitazione: preparare una scena</span><span class="sxs-lookup"><span data-stu-id="59818-104">Tutorial: Prepare a scene</span></span>

<span data-ttu-id="59818-105">Informazioni su come preparare una scena e aggiungere alcuni elementi 3D di base.</span><span class="sxs-lookup"><span data-stu-id="59818-105">Learn how to prepare a scene, and add some basic 3D elements to it.</span></span>

<span data-ttu-id="59818-106">In questa esercitazione si apprenderà come:</span><span class="sxs-lookup"><span data-stu-id="59818-106">In this tutorial, learn how to:</span></span>

> [!div class="checklist"]
> * <span data-ttu-id="59818-107">Creare una scena</span><span class="sxs-lookup"><span data-stu-id="59818-107">Create a scene</span></span>
> * <span data-ttu-id="59818-108">Aggiungere una fotocamera</span><span class="sxs-lookup"><span data-stu-id="59818-108">Add a camera</span></span>
> * <span data-ttu-id="59818-109">Aggiungi luce</span><span class="sxs-lookup"><span data-stu-id="59818-109">Add light</span></span>
> * <span data-ttu-id="59818-110">Aggiungi elementi 3D di base</span><span class="sxs-lookup"><span data-stu-id="59818-110">Add basic 3D elements</span></span>

## <a name="before-you-begin"></a><span data-ttu-id="59818-111">Prima di iniziare</span><span class="sxs-lookup"><span data-stu-id="59818-111">Before you begin</span></span>

<span data-ttu-id="59818-112">Nel passaggio precedente dell'esercitazione è stata creata una pagina Web di base.</span><span class="sxs-lookup"><span data-stu-id="59818-112">In previous tutorial step a basic web page was created.</span></span> <span data-ttu-id="59818-113">Aprire la pagina Web per la modifica.</span><span class="sxs-lookup"><span data-stu-id="59818-113">Have the web page open for editing.</span></span>

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

## <a name="create-a-scene"></a><span data-ttu-id="59818-114">Creare una scena</span><span class="sxs-lookup"><span data-stu-id="59818-114">Create a scene</span></span>

<span data-ttu-id="59818-115">Una scena è la posizione in cui verrà visualizzato tutto il contenuto.</span><span class="sxs-lookup"><span data-stu-id="59818-115">A scene is where all the contents will be displayed.</span></span> <span data-ttu-id="59818-116">Potrebbero essere presenti più scene ed è possibile passare da una scena all'altra.</span><span class="sxs-lookup"><span data-stu-id="59818-116">There might be multiple scenes and it is possible to switch between scenes.</span></span> <span data-ttu-id="59818-117">Scopri di più su [babylon.js scena](https://doc.babylonjs.com/divingDeeper/scene).</span><span class="sxs-lookup"><span data-stu-id="59818-117">Read more about [babylon.js Scene](https://doc.babylonjs.com/divingDeeper/scene).</span></span>

1. <span data-ttu-id="59818-118">Aggiungere il tag script dopo l'elemento HTML Canvas e aggiungere il codice seguente per creare una scena riempita con il colore nero:</span><span class="sxs-lookup"><span data-stu-id="59818-118">Add the script tag after the canvas html element and add the following code to create a scene filled in black color:</span></span>

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

    <span data-ttu-id="59818-119">Nel codice precedente è necessario creare un'istanza di babylon.js motore di rendering Web che esegue il rendering di una scena e associa gli eventi nell'area di disegno.</span><span class="sxs-lookup"><span data-stu-id="59818-119">In the code above we have to create an instance of babylon.js web rendering engine that renders a scene and hooks events on the canvas.</span></span> <span data-ttu-id="59818-120">Per altre informazioni sul motore, vedere la pagina della documentazione [Babylon. Engine](https://doc.babylonjs.com/typedoc/classes/babylon.engine)</span><span class="sxs-lookup"><span data-stu-id="59818-120">For more information about the engine, check the documentation page [babylon.engine](https://doc.babylonjs.com/typedoc/classes/babylon.engine)</span></span>

1. <span data-ttu-id="59818-121">Per impostazione predefinita, non viene eseguito il rendering della scena.</span><span class="sxs-lookup"><span data-stu-id="59818-121">The scene is not rendered by default.</span></span> <span data-ttu-id="59818-122">Tenere presente che potrebbero essere presenti più scene e si controlla quale scena viene visualizzata.</span><span class="sxs-lookup"><span data-stu-id="59818-122">Remember, there might be multiple scenes and you control which scene is displayed.</span></span> <span data-ttu-id="59818-123">Per eseguire ripetutamente il rendering della scena in ogni frame, eseguire il codice seguente dopo la chiamata alla funzione *createScene* :</span><span class="sxs-lookup"><span data-stu-id="59818-123">To render the scene repeatedly on every frame, execute the following code after the call to *createScene* function:</span></span>

    ```javascript
    engine.runRenderLoop(function () {
        sceneToRender.render();
    });
    ```

## <a name="add-basic-3d-element"></a><span data-ttu-id="59818-124">Aggiungi elemento 3D di base</span><span class="sxs-lookup"><span data-stu-id="59818-124">Add basic 3D element</span></span>

1. <span data-ttu-id="59818-125">Aggiungere la prima forma 3D.</span><span class="sxs-lookup"><span data-stu-id="59818-125">Let's add our first 3D shape.</span></span> <span data-ttu-id="59818-126">Nelle forme 3D Virtual World sono compilate da *mesh*, molti facet triangolari Uniti in join, ognuno dei quali è costituito da tre vertici.</span><span class="sxs-lookup"><span data-stu-id="59818-126">In the 3D virtual world shapes are built from *meshes*, lots of triangular facets joined together, each facet made from three vertices.</span></span> <span data-ttu-id="59818-127">È possibile usare una mesh predefinita o creare una mesh personalizzata.</span><span class="sxs-lookup"><span data-stu-id="59818-127">You can either use a predefined mesh or create your own custom mesh.</span></span> <span data-ttu-id="59818-128">Qui verrà usata una Mesh Box predefinita, ad esempio un cubo.</span><span class="sxs-lookup"><span data-stu-id="59818-128">Here we will be using a predefined box mesh, i.e. a cube.</span></span> <span data-ttu-id="59818-129">Per creare la casella usare [Babylon. MeshBuilder. CreateBox](https://doc.babylonjs.com/divingDeeper/mesh/creation/set/box).</span><span class="sxs-lookup"><span data-stu-id="59818-129">To create the box use [BABYLON.MeshBuilder.CreateBox](https://doc.babylonjs.com/divingDeeper/mesh/creation/set/box).</span></span> <span data-ttu-id="59818-130">I parametri sono Name e Options (le opzioni sono diverse in base al tipo di mesh).</span><span class="sxs-lookup"><span data-stu-id="59818-130">The parameters are name, and options (options are different according to the type of mesh).</span></span> <span data-ttu-id="59818-131">Aggiungere il codice seguente alla funzione *createScene*:</span><span class="sxs-lookup"><span data-stu-id="59818-131">Append the following code to the function *createScene*:</span></span>

    ```javascript
    const box = BABYLON.MeshBuilder.CreateBox("box", {});
    box.position.x = 0.5;
    box.position.y = 1;
    ```

1. <span data-ttu-id="59818-132">Aprire la pagina Web nel browser Microsoft Edge e controllare l'output.</span><span class="sxs-lookup"><span data-stu-id="59818-132">Open the web page in the Microsoft Edge browser and check the output.</span></span> <span data-ttu-id="59818-133">Nella finestra del browser viene visualizzata una pagina vuota.</span><span class="sxs-lookup"><span data-stu-id="59818-133">The browser window shows a blank page.</span></span> <span data-ttu-id="59818-134">Aprire DevTools usando la tastiera e selezionare F12 o CTRL + MAIUSC + I (Windows, Linux) o comando + opzione + I (macOS).</span><span class="sxs-lookup"><span data-stu-id="59818-134">Open DevTools by using the keyboard and select F12 or Control+Shift+I (Windows, Linux) or Command+Option+I (macOS).</span></span> <span data-ttu-id="59818-135">Dopo aver aperto la scheda della *console* , è possibile iniziare a cercare gli errori.</span><span class="sxs-lookup"><span data-stu-id="59818-135">After opening the *Console* tab, you can start looking for errors.</span></span> <span data-ttu-id="59818-136">Verrà visualizzato un errore:' errore non rilevato: Nessuna fotocamera definita.</span><span class="sxs-lookup"><span data-stu-id="59818-136">There will be an error displayed: 'Uncaught Error: No camera defined'.</span></span> <span data-ttu-id="59818-137">A questo punto è necessario aggiungere una fotocamera alla scena.</span><span class="sxs-lookup"><span data-stu-id="59818-137">Now we have to add a camera to the scene.</span></span>

## <a name="add-a-camera"></a><span data-ttu-id="59818-138">Aggiungere una fotocamera</span><span class="sxs-lookup"><span data-stu-id="59818-138">Add a camera</span></span>

1. <span data-ttu-id="59818-139">Per consentire l'input dell'utente, è necessario collegare una fotocamera all'area di disegno.</span><span class="sxs-lookup"><span data-stu-id="59818-139">To allow user input, a camera must be attached to the canvas.</span></span> <span data-ttu-id="59818-140">Aggiungere la fotocamera di tipo [Babylon. ArcRotateCamera](https://doc.babylonjs.com/divingDeeper/cameras/camera_introduction#arc-rotate-camera) che ci permette di cercare, ovvero può essere ruotato intorno all'oggetto appena aggiunto alla scena.</span><span class="sxs-lookup"><span data-stu-id="59818-140">Let's add the camera of type [BABYLON.ArcRotateCamera](https://doc.babylonjs.com/divingDeeper/cameras/camera_introduction#arc-rotate-camera) that allows us to look around, i.e. can be rotated around object that we've just added to the scene.</span></span> <span data-ttu-id="59818-141">I parametri necessari per creare un'istanza della fotocamera sono nome, Alfa (rotazione lungo l'asse longitudinale), beta (rotazione lungo l'asse latitudinali), raggio (distanza dalla destinazione) e destinazione (la destinazione che la fotocamera dovrebbe esaminare).</span><span class="sxs-lookup"><span data-stu-id="59818-141">The parameters required to create an instance of the camera are name, alpha (rotation along the longitudinal axis), beta (rotation along the latitudinal axis), radius (distance from the target), and target (the target the camera should look at).</span></span> <span data-ttu-id="59818-142">Aggiungere il codice seguente alla funzione *createScene* :</span><span class="sxs-lookup"><span data-stu-id="59818-142">Add the following code to the *createScene* function:</span></span>

    ```javascript
    const alpha =  Math.PI;
    const beta = Math.PI;
    const radius = 5;
    
    const camera = new BABYLON.ArcRotateCamera("Camera", 0, 0, 0);
    camera.setPosition(new BABYLON.Vector3(alpha, beta, radius));
    camera.attachControl(canvas, true);
    ```

1. <span data-ttu-id="59818-143">Se si seleziona l'output nel browser, viene visualizzata un'area di disegno nera.</span><span class="sxs-lookup"><span data-stu-id="59818-143">If you check the output in the browser, you will see a black canvas.</span></span> <span data-ttu-id="59818-144">La luce è mancante.</span><span class="sxs-lookup"><span data-stu-id="59818-144">We are missing the light.</span></span>

## <a name="add-light"></a><span data-ttu-id="59818-145">Aggiungi luce</span><span class="sxs-lookup"><span data-stu-id="59818-145">Add light</span></span>

1. <span data-ttu-id="59818-146">Sono disponibili quattro tipi di luci che è possibile usare con una gamma di proprietà di illuminazione: punto, direzionale, spot e emisfero chiaro.</span><span class="sxs-lookup"><span data-stu-id="59818-146">There are four types of lights that can be used with a range of lighting properties: Point, Directional, Spot and Hemispheric Light.</span></span> <span data-ttu-id="59818-147">Aggiungere la luce di ambiente [HemisphericLight](https://doc.babylonjs.com/typedoc/classes/babylon.hemisphericlight), come indicato di seguito:</span><span class="sxs-lookup"><span data-stu-id="59818-147">Let's add the ambient light [HemisphericLight](https://doc.babylonjs.com/typedoc/classes/babylon.hemisphericlight), as follows:</span></span>

    ```javascript
    const light = new BABYLON.HemisphericLight("light", new BABYLON.Vector3(1, 1, 0));
    ```

1. <span data-ttu-id="59818-148">Il codice finale della pagina Web sarà simile al seguente:</span><span class="sxs-lookup"><span data-stu-id="59818-148">The final code of the web page will look as follows:</span></span>

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

1. <span data-ttu-id="59818-149">Controllare l'output nel browser.</span><span class="sxs-lookup"><span data-stu-id="59818-149">Check the output in the browser.</span></span> <span data-ttu-id="59818-150">Il cubo verrà visualizzato e si potrà utilizzare il mouse per ruotare la fotocamera attorno al cubo e visualizzare i diversi visi del cubo:</span><span class="sxs-lookup"><span data-stu-id="59818-150">You should see the cube and using the mouse you can rotate the camera around the cube and see the different faces of the cube:</span></span>

![Scena di base con cubo](../images/hello-world-basic-scene.png)

## <a name="next-steps"></a><span data-ttu-id="59818-152">Passaggi successivi</span><span class="sxs-lookup"><span data-stu-id="59818-152">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="59818-153">Esercitazione successiva: 3. interagire con l'oggetto 3D</span><span class="sxs-lookup"><span data-stu-id="59818-153">Next Tutorial: 3. Interact with 3D object</span></span>](interact-03.md)

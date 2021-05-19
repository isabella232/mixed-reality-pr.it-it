---
title: Babylon.js esercitazione per interagire con gli oggetti 3D
description: Informazioni su come usare babylon.js e interagire con gli oggetti 3D.
author: bogenera
ms.author: ayyonet
ms.date: 03/05/2021
ms.topic: article
keywords: realtà mista, javascript, esercitazione, BabylonJS, hololens, realtà mista, UWP, Windows 10, WebXR, web immersive
ms.localizationpriority: high
ms.openlocfilehash: 102f2f29141c7a48c07a1dc80f7b3b180bc5e436
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143693"
---
# <a name="tutorial-interact-with-3d-object"></a><span data-ttu-id="8f7b9-104">Esercitazione: Interagire con un oggetto 3D</span><span class="sxs-lookup"><span data-stu-id="8f7b9-104">Tutorial: Interact with 3D object</span></span>

<span data-ttu-id="8f7b9-105">Informazioni su come creare oggetti e interazioni 3D per un'esperienza di realtà mista usando babylon.js.</span><span class="sxs-lookup"><span data-stu-id="8f7b9-105">Learn how to create 3D objects and interactions for a Mixed Reality experience using babylon.js.</span></span> <span data-ttu-id="8f7b9-106">In questa sezione si inizierà con qualcosa di semplice, ad esempio disegnare i visi di un cubo quando si seleziona l'oggetto.</span><span class="sxs-lookup"><span data-stu-id="8f7b9-106">In this section, you'll start with something simple, like painting the faces of a cube when you select the object.</span></span>

<span data-ttu-id="8f7b9-107">Questa esercitazione illustra gli argomenti seguenti:</span><span class="sxs-lookup"><span data-stu-id="8f7b9-107">This tutorial covers the following topics:</span></span>

> [!div class="checklist"]
> * <span data-ttu-id="8f7b9-108">Come aggiungere interazioni</span><span class="sxs-lookup"><span data-stu-id="8f7b9-108">How to add interactions</span></span>
> * <span data-ttu-id="8f7b9-109">Abilitare la modalità immersiva WebXR</span><span class="sxs-lookup"><span data-stu-id="8f7b9-109">Enable WebXR immersive mode</span></span>
> * <span data-ttu-id="8f7b9-110">Eseguire l'app nel simulatore Windows Mixed Reality app</span><span class="sxs-lookup"><span data-stu-id="8f7b9-110">Run the app on Windows Mixed Reality Simulator</span></span>
> * <span data-ttu-id="8f7b9-111">Eseguire l'app ed eseguirne il debug in Android Chrome</span><span class="sxs-lookup"><span data-stu-id="8f7b9-111">Run and debug the app on Android Chrome</span></span>

## <a name="before-you-begin"></a><span data-ttu-id="8f7b9-112">Prima di iniziare</span><span class="sxs-lookup"><span data-stu-id="8f7b9-112">Before you begin</span></span>

<span data-ttu-id="8f7b9-113">Nel passaggio precedente dell'esercitazione è stata creata una pagina Web di base con una scena.</span><span class="sxs-lookup"><span data-stu-id="8f7b9-113">In previous tutorial step a basic web page with a scene was created.</span></span> <span data-ttu-id="8f7b9-114">Fare in modo che la pagina Web di hosting sia aperta per la modifica.</span><span class="sxs-lookup"><span data-stu-id="8f7b9-114">Have the hosting web page open for editing.</span></span>

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

## <a name="add-interaction"></a><span data-ttu-id="8f7b9-115">Aggiungere l'interazione</span><span class="sxs-lookup"><span data-stu-id="8f7b9-115">Add interaction</span></span>

1. <span data-ttu-id="8f7b9-116">Prima di tutto, aggiornare il codice che crea il cubo, in modo che il cubo sia di colore casuale.</span><span class="sxs-lookup"><span data-stu-id="8f7b9-116">First, let's update our code that creates the cube, so that the cube is painted with a random color.</span></span> <span data-ttu-id="8f7b9-117">A tale scopo, si [aggiungerà materiale](https://doc.babylonjs.com/divingDeeper/materials/using/materials_introduction) al cubo.</span><span class="sxs-lookup"><span data-stu-id="8f7b9-117">To do that, we will add [material](https://doc.babylonjs.com/divingDeeper/materials/using/materials_introduction) to our cube.</span></span> <span data-ttu-id="8f7b9-118">Material consente di specificare colore e trame e può essere usato per coprire altri oggetti.</span><span class="sxs-lookup"><span data-stu-id="8f7b9-118">Material allows us to specify color and textures and can be used to cover other objects.</span></span> <span data-ttu-id="8f7b9-119">Il modo in cui viene visualizzato un materiale dipende dalla luce o dalle luci usate nella scena e da come viene impostato per reagire.</span><span class="sxs-lookup"><span data-stu-id="8f7b9-119">How a material appears depends on the light or lights used in the scene and how it is set to react.</span></span> <span data-ttu-id="8f7b9-120">Ad esempio, diffuseColor estende il colore su tutta la mesh a cui è collegato.</span><span class="sxs-lookup"><span data-stu-id="8f7b9-120">For example, the diffuseColor spreads the color all over the mesh to which it is attached.</span></span> <span data-ttu-id="8f7b9-121">Aggiungere il codice seguente:</span><span class="sxs-lookup"><span data-stu-id="8f7b9-121">Add the following code:</span></span>

    ```javascript
    const boxMaterial = new BABYLON.StandardMaterial("material", scene);
    boxMaterial.diffuseColor = BABYLON.Color3.Random();
    box.material = boxMaterial;
    ```

1. <span data-ttu-id="8f7b9-122">Ora che il cubo è stato dipinto con un colore casuale, è possibile aggiungere un'interazione a:</span><span class="sxs-lookup"><span data-stu-id="8f7b9-122">Now that the cube is painted with a random color, let's add an interaction to:</span></span>

    * <span data-ttu-id="8f7b9-123">Modificare il colore quando si fa clic sul cubo</span><span class="sxs-lookup"><span data-stu-id="8f7b9-123">Change the color when the cube is clicked</span></span>
    * <span data-ttu-id="8f7b9-124">Spostare il cubo dopo la modifica del colore</span><span class="sxs-lookup"><span data-stu-id="8f7b9-124">Move the cube after the color is changed</span></span>

    <span data-ttu-id="8f7b9-125">Per aggiungere interazioni, è necessario usare [le azioni](https://doc.babylonjs.com/divingDeeper/events/actions).</span><span class="sxs-lookup"><span data-stu-id="8f7b9-125">To add interactions we should be using [actions](https://doc.babylonjs.com/divingDeeper/events/actions).</span></span> <span data-ttu-id="8f7b9-126">Viene avviata un'azione in risposta al trigger di evento.</span><span class="sxs-lookup"><span data-stu-id="8f7b9-126">An action is launched in response to the event trigger.</span></span> <span data-ttu-id="8f7b9-127">Ad esempio, quando l'utente fa clic sul cubo.</span><span class="sxs-lookup"><span data-stu-id="8f7b9-127">For example, when the user clicks on the cube.</span></span> <span data-ttu-id="8f7b9-128">È necessario solo creare un'istanza di BABYLON. ActionManager e registrare un'azione per un determinato trigger.</span><span class="sxs-lookup"><span data-stu-id="8f7b9-128">All we need to do is instantiate BABYLON.ActionManager and register an action for certain trigger.</span></span> <span data-ttu-id="8f7b9-129">[LBABYLON.ExealtacodeAction](https://doc.babylonjs.com/typedoc/classes/babylon.executecodeaction) eseguirà la funzione JavaScript quando un utente fa clic sul cubo:</span><span class="sxs-lookup"><span data-stu-id="8f7b9-129">The [BABYLON.ExecuteCodeAction](https://doc.babylonjs.com/typedoc/classes/babylon.executecodeaction) will run our JavaScript function when someone clicks on the cube:</span></span>

    ```javascript
    box.actionManager = new BABYLON.ActionManager(scene);
    box.actionManager.registerAction(new BABYLON.ExecuteCodeAction(
        BABYLON.ActionManager.OnPickTrigger, 
        function (evt) {
            const sourceBox = evt.meshUnderPointer;
            
            //move the box upright
            sourceBox.position.x += 0.1;
            sourceBox.position.y += 0.1;

            //update the color
            boxMaterial.diffuseColor = BABYLON.Color3.Random();
        }));
    ```

1. <span data-ttu-id="8f7b9-130">Il codice finale della pagina Web sarà simile al seguente:</span><span class="sxs-lookup"><span data-stu-id="8f7b9-130">The final code of the web page will look as follows:</span></span>

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

                const boxMaterial = new BABYLON.StandardMaterial("material", scene);
                boxMaterial.diffuseColor = BABYLON.Color3.Random();
                box.material = boxMaterial;
 
                box.actionManager = new BABYLON.ActionManager(scene);
                box.actionManager.registerAction(
                    new BABYLON.ExecuteCodeAction(BABYLON.ActionManager.OnPickTrigger, 
                    function (evt) {
                        const sourceBox = evt.meshUnderPointer;
                        sourceBox.position.x += 0.1;
                        sourceBox.position.y += 0.1;

                        boxMaterial.diffuseColor = BABYLON.Color3.Random();
                    }));

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

## <a name="enable-webxr-immersive-experience"></a><span data-ttu-id="8f7b9-131">Abilitare l'esperienza immersiva WebXR</span><span class="sxs-lookup"><span data-stu-id="8f7b9-131">Enable WebXR immersive experience</span></span>

<span data-ttu-id="8f7b9-132">Ora che i colori del cubo cambiano, è possibile provare l'esperienza immersiva.</span><span class="sxs-lookup"><span data-stu-id="8f7b9-132">Now that our cube is changing colors, we're ready to try the immersive experience.</span></span>

1. <span data-ttu-id="8f7b9-133">In questo passaggio si introdurrà una [base.](https://doc.babylonjs.com/divingDeeper/mesh/creation/set/ground)</span><span class="sxs-lookup"><span data-stu-id="8f7b9-133">In this step we're going to introduce a [ground](https://doc.babylonjs.com/divingDeeper/mesh/creation/set/ground).</span></span> <span data-ttu-id="8f7b9-134">Il cubo verrà sospeso nell'aria e nella parte inferiore verrà visualizzato un piano.</span><span class="sxs-lookup"><span data-stu-id="8f7b9-134">The cube will be hanging in the air and we will see a floor at the bottom.</span></span> <span data-ttu-id="8f7b9-135">Aggiungere il campo come segue:</span><span class="sxs-lookup"><span data-stu-id="8f7b9-135">Add the ground as follows:</span></span>

    ```javascript
    const ground = BABYLON.MeshBuilder.CreateGround("ground", {width: 4, height: 4});
    ```

    <span data-ttu-id="8f7b9-136">In questo modo viene creato un semplice piano da 4x4 metri.</span><span class="sxs-lookup"><span data-stu-id="8f7b9-136">This creates a simple 4x4-meter floor.</span></span>

1. <span data-ttu-id="8f7b9-137">Per aggiungere il supporto di WebXR, è necessario chiamare *createDefaultXRExperienceAsync*, che ha un *risultato Promise.*</span><span class="sxs-lookup"><span data-stu-id="8f7b9-137">In order to add WebXR support, we need to call *createDefaultXRExperienceAsync*, which has a *Promise* result.</span></span> <span data-ttu-id="8f7b9-138">Aggiungere questo codice alla fine della *funzione createScene* anziché restituire *la scena;*:</span><span class="sxs-lookup"><span data-stu-id="8f7b9-138">Add this code at the end of *createScene* function instead of *return scene;*:</span></span>

    ```javascript
    const xrPromise = scene.createDefaultXRExperienceAsync({
        floorMeshes: [ground]
    });
    return xrPromise.then((xrExperience) => {
        console.log("Done, WebXR is enabled.");
        return scene;
    });
    ```

1. <span data-ttu-id="8f7b9-139">Il codice finale della pagina Web sarà simile al seguente:</span><span class="sxs-lookup"><span data-stu-id="8f7b9-139">The final code of the web page will look as follows:</span></span>

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

                const boxMaterial = new BABYLON.StandardMaterial("material", scene);
                boxMaterial.diffuseColor = BABYLON.Color3.Random();
                box.material = boxMaterial;
 
                box.actionManager = new BABYLON.ActionManager(scene);
                box.actionManager.registerAction(
                    new BABYLON.ExecuteCodeAction(BABYLON.ActionManager.OnPickTrigger, 
                    function (evt) {
                        const sourceBox = evt.meshUnderPointer;
                        sourceBox.position.x += 0.1;
                        sourceBox.position.y += 0.1;

                        boxMaterial.diffuseColor = BABYLON.Color3.Random();
                    }));
                    
                const ground = BABYLON.MeshBuilder.CreateGround("ground", {width: 4, height: 4});
                
                const xrPromise = scene.createDefaultXRExperienceAsync({
                    floorMeshes: [ground]
                });
                
                return xrPromise.then((xrExperience) => {
                    console.log("Done, WebXR is enabled.");
                    return scene;
                });
            };
            
            createScene().then(sceneToRender => {
                engine.runRenderLoop(() => sceneToRender.render());
            });
        </script>
    </body>
    </html>
    ```

1. <span data-ttu-id="8f7b9-140">Il codice precedente genera l'output seguente nella finestra del browser: ![ scena WebXR](../images/hello-world-webxr-scene.png)</span><span class="sxs-lookup"><span data-stu-id="8f7b9-140">The above code generates the following output in the browser window: ![WebXR scene](../images/hello-world-webxr-scene.png)</span></span>

## <a name="run-on-a-windows-mixed-reality-simulator"></a><span data-ttu-id="8f7b9-141">Eseguire in un simulatore Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="8f7b9-141">Run on a Windows Mixed Reality Simulator</span></span>

1. <span data-ttu-id="8f7b9-142">Selezionare il pulsante Immersive-VR nell'angolo in basso a destra: ![ Immersive VR Button (Pulsante vr immersiva)](../images/immersive-vr-button.png)</span><span class="sxs-lookup"><span data-stu-id="8f7b9-142">Select the Immersive-VR button on the bottom right corner: ![Immersive VR Button](../images/immersive-vr-button.png)</span></span>

1. <span data-ttu-id="8f7b9-143">Questa azione avvierà la finestra Windows Mixed Reality simulatore come illustrato di seguito: ![ Portale realtà mista](../images/mixed-reality-portal.png)</span><span class="sxs-lookup"><span data-stu-id="8f7b9-143">This action will launch the Windows Mixed Reality Simulator window as shown below: ![Mixed Reality Portal](../images/mixed-reality-portal.png)</span></span>

1. <span data-ttu-id="8f7b9-144">Usare i tasti W, A, S e D sulla tastiera per procedere, tornare a sinistra e a destra di conseguenza.</span><span class="sxs-lookup"><span data-stu-id="8f7b9-144">Use the W,A,S, and D keys on your keyboard to walk forward, back left and right accordingly.</span></span> <span data-ttu-id="8f7b9-145">Usare la mano simulata per impostare come destinazione il cubo e premere INVIO sulla tastiera per eseguire l'azione di clic.</span><span class="sxs-lookup"><span data-stu-id="8f7b9-145">Use simulated hand to target the cube and press the Enter key on your keyboard to perform the click action.</span></span> <span data-ttu-id="8f7b9-146">Il cubo cambierà colore e si sposterà in una nuova posizione.</span><span class="sxs-lookup"><span data-stu-id="8f7b9-146">The cube will change its color and move to a new position.</span></span>

> [!NOTE]
> <span data-ttu-id="8f7b9-147">Quando si fa riferimento al cubo, assicurarsi che l'estremità del raggio della mano (cerchio bianco) si interseci con il cubo, come illustrato nell'immagine precedente.</span><span class="sxs-lookup"><span data-stu-id="8f7b9-147">When targeting the cube, make sure that the end of hand ray (white circle) intersects with the cube as shown on the picture above.</span></span> <span data-ttu-id="8f7b9-148">Altre informazioni su [Point e commit con le mani.](https://docs.microsoft.com/windows/mixed-reality/design/point-and-commit)</span><span class="sxs-lookup"><span data-stu-id="8f7b9-148">Learn more about [Point and commit with hands](https://docs.microsoft.com/windows/mixed-reality/design/point-and-commit).</span></span>

## <a name="run-and-debug-on-android-device"></a><span data-ttu-id="8f7b9-149">Eseguire ed eseguire il debug in un dispositivo Android</span><span class="sxs-lookup"><span data-stu-id="8f7b9-149">Run and debug on Android device</span></span>

<span data-ttu-id="8f7b9-150">Seguire questa procedura per abilitare il debug nel dispositivo Android:</span><span class="sxs-lookup"><span data-stu-id="8f7b9-150">Perform the following steps to enable debugging on your Android device:</span></span>

### <a name="prerequisites"></a><span data-ttu-id="8f7b9-151">Prerequisiti</span><span class="sxs-lookup"><span data-stu-id="8f7b9-151">Prerequisites</span></span>

* <span data-ttu-id="8f7b9-152">Un server Web che fornisce una pagina HTML statica in un contesto sicuro (https:// o tramite port forwarding in localhost) nel computer di sviluppo.</span><span class="sxs-lookup"><span data-stu-id="8f7b9-152">A web server that serves static html page in secure context (https:// or via Port forwarding on localhost) on development machine.</span></span> <span data-ttu-id="8f7b9-153">Ad esempio, *sfruttare il pacchetto* serve npm come semplice server Web leggero che serve file HTML statici, controllare più [npm serve](https://github.com/vercel/serve#readme)</span><span class="sxs-lookup"><span data-stu-id="8f7b9-153">For example leverage *serve* npm package as simple lightweight web server that serves static html files, check more [npm serve](https://github.com/vercel/serve#readme)</span></span>
* <span data-ttu-id="8f7b9-154">Il dispositivo originariamente fornito con il Google Play Store e deve eseguire Android 7.0 o versione più recente</span><span class="sxs-lookup"><span data-stu-id="8f7b9-154">The device originally shipped with the Google Play Store and must be running Android 7.0 or newer</span></span>
* <span data-ttu-id="8f7b9-155">La versione più recente [di Google Chrome](https://support.google.com/chrome/answer/95346) sia nella workstation di sviluppo che nel dispositivo</span><span class="sxs-lookup"><span data-stu-id="8f7b9-155">The latest version of [Google Chrome](https://support.google.com/chrome/answer/95346) on both the development workstation and on the device</span></span>
* <span data-ttu-id="8f7b9-156">Per verificare che il dispositivo sia configurato correttamente per l'esecuzione di WebXR, passare a una [pagina WebXR](https://immersive-web.github.io/webxr-samples/) di esempio nel dispositivo.</span><span class="sxs-lookup"><span data-stu-id="8f7b9-156">To verify that the device is correctly configured to run WebXR, browse to a [sample WebXR page](https://immersive-web.github.io/webxr-samples/) on the device.</span></span> <span data-ttu-id="8f7b9-157">Verrà visualizzato il messaggio, ad esempio:</span><span class="sxs-lookup"><span data-stu-id="8f7b9-157">You should see the message, such as:</span></span>

    > <span data-ttu-id="8f7b9-158">Il browser supporta WebXR e può eseguire esperienze di realtà virtuale e realtà aumentata se si dispone dell'hardware appropriato.</span><span class="sxs-lookup"><span data-stu-id="8f7b9-158">Your browser supports WebXR and can run Virtual Reality and Augmented Reality experiences if you have the appropriate hardware.</span></span>

1. <span data-ttu-id="8f7b9-159">Abilitare la modalità sviluppatore e il debug USB in un dispositivo Android.</span><span class="sxs-lookup"><span data-stu-id="8f7b9-159">Enable developer mode and USB debugging on an Android device.</span></span> <span data-ttu-id="8f7b9-160">Per informazioni su come eseguire questa operazione per la versione di Android in uso, vedere la pagina della documentazione ufficiale [Configurare le opzioni per sviluppatori sul dispositivo](https://developer.android.com/studio/debug/dev-options)</span><span class="sxs-lookup"><span data-stu-id="8f7b9-160">See how to do this for your version of Android at the official documentation page [Configure on-device developer options](https://developer.android.com/studio/debug/dev-options)</span></span>
1. <span data-ttu-id="8f7b9-161">Connettere quindi il dispositivo Android al computer di sviluppo o al portatile tramite cavo USB</span><span class="sxs-lookup"><span data-stu-id="8f7b9-161">Next, connect Android device to your development machine or laptop via USB cable</span></span>
1. <span data-ttu-id="8f7b9-162">Assicurarsi che il server Web nel computer di sviluppo sia in esecuzione.</span><span class="sxs-lookup"><span data-stu-id="8f7b9-162">Ensure that the web server on the development machine is running.</span></span> <span data-ttu-id="8f7b9-163">Ad esempio, passare alla cartella radice contenente la pagina di hosting Web (index.html) ed eseguire il codice seguente (supponendo di usare il pacchetto serve npm):</span><span class="sxs-lookup"><span data-stu-id="8f7b9-163">For example, navigate to the root folder containing your web hosting page (index.html) and execute the following code (assuming you use serve npm package):</span></span>

    ```bash
    serve
    ```

1. <span data-ttu-id="8f7b9-164">Aprire Google Chrome nel computer di sviluppo e immettere nella barra degli indirizzi il testo seguente:</span><span class="sxs-lookup"><span data-stu-id="8f7b9-164">Open Google Chrome on your development machine and enter in the address bar the following text:</span></span>
    > <span data-ttu-id="8f7b9-165">chrome://inspect#devices ![ Finestra di debug USB chrome](../images/chrome-usb-debug.png)</span><span class="sxs-lookup"><span data-stu-id="8f7b9-165">chrome://inspect#devices ![Chrome USB debugging window](../images/chrome-usb-debug.png)</span></span>
1. <span data-ttu-id="8f7b9-166">Assicurarsi che la casella *di controllo Individua dispositivi USB* sia abilitata</span><span class="sxs-lookup"><span data-stu-id="8f7b9-166">Ensure that the *Discover USB devices* checkbox is enabled</span></span>
1. <span data-ttu-id="8f7b9-167">Fare clic sul pulsante *Port forwarding* (Inoltro porta) e assicurarsi che *port forwarding* sia abilitato e contenga una voce *localhost:5000,* come illustrato di seguito: Chrome Port Forwarding window (Finestra di inoltro delle porte di  ![ Chrome)](../images/chrome-port-forwarding.png)</span><span class="sxs-lookup"><span data-stu-id="8f7b9-167">Click the button *Port forwarding* and ensure that *Port forwarding* is enabled and contains an entry *localhost:5000* as shown below:  ![Chrome Port Forwarding window](../images/chrome-port-forwarding.png)</span></span>
1. <span data-ttu-id="8f7b9-168">Nel dispositivo Android connesso aprire una finestra di Google Chrome e passare *http://localhost:5000* a per visualizzare il cubo</span><span class="sxs-lookup"><span data-stu-id="8f7b9-168">In your connected Android device open a Google Chrome window and browse to *http://localhost:5000* and you should see the cube</span></span>
1. <span data-ttu-id="8f7b9-169">Nel computer di sviluppo, in Chrome, verrà visualizzato il dispositivo e un elenco di pagine Web attualmente aperte in questa finestra:  ![ Chrome Inspect window (Ispezionare Chrome)](../images/chrome-inspect.png)</span><span class="sxs-lookup"><span data-stu-id="8f7b9-169">On your development machine, in Chrome, you will see your device and a list of web pages currently opened in there:  ![Chrome Inspect window](../images/chrome-inspect.png)</span></span>
1. <span data-ttu-id="8f7b9-170">Fare clic sul pulsante *Inspect (Ispeziona)* accanto a una voce *http://localhost:5000* : Chrome  ![ DevTools Debug window (Debug di Chrome DevTools)](../images/chrome-debug.png)</span><span class="sxs-lookup"><span data-stu-id="8f7b9-170">Click the button *Inspect* next to an entry *http://localhost:5000*:  ![Chrome DevTools Debug window](../images/chrome-debug.png)</span></span>
1. <span data-ttu-id="8f7b9-171">Usare [Chrome DevTools per](https://developers.google.com/web/tools/chrome-devtools) eseguire il debug della pagina</span><span class="sxs-lookup"><span data-stu-id="8f7b9-171">Use the [Chrome DevTools](https://developers.google.com/web/tools/chrome-devtools) to debug the page</span></span>

## <a name="takeaways"></a><span data-ttu-id="8f7b9-172">Risultati</span><span class="sxs-lookup"><span data-stu-id="8f7b9-172">Takeaways</span></span>

<span data-ttu-id="8f7b9-173">Di seguito sono riportati i passaggi più importanti di questa esercitazione:</span><span class="sxs-lookup"><span data-stu-id="8f7b9-173">The following are the most important takeaways from this tutorial:</span></span>
* <span data-ttu-id="8f7b9-174">Babylon.js semplifica la creazione di esperienze immersive con JavaScript</span><span class="sxs-lookup"><span data-stu-id="8f7b9-174">Babylon.js makes it easy to create immersive experiences using JavaScript</span></span>
* <span data-ttu-id="8f7b9-175">Per creare scene virtuali non è necessario scrivere codice di basso livello o apprendere una nuova tecnologia</span><span class="sxs-lookup"><span data-stu-id="8f7b9-175">To create virtual scenes you don't need to write low-level code or learn a new technology</span></span>
* <span data-ttu-id="8f7b9-176">È possibile creare applicazioni di realtà mista con un browser supportato da WebXR senza dover acquistare un visore VR</span><span class="sxs-lookup"><span data-stu-id="8f7b9-176">You can build Mixed Reality applications with WebXR-supported browser without need to buy a headset</span></span>

## <a name="next-steps"></a><span data-ttu-id="8f7b9-177">Passaggi successivi</span><span class="sxs-lookup"><span data-stu-id="8f7b9-177">Next steps</span></span>

<span data-ttu-id="8f7b9-178">Congratulazioni!</span><span class="sxs-lookup"><span data-stu-id="8f7b9-178">Congratulations!</span></span> <span data-ttu-id="8f7b9-179">È stata completata la serie di esercitazioni babylon.js e si è appreso come:</span><span class="sxs-lookup"><span data-stu-id="8f7b9-179">You've completed our series of babylon.js tutorials and learned how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="8f7b9-180">Configurare un ambiente di sviluppo</span><span class="sxs-lookup"><span data-stu-id="8f7b9-180">Set up a development environment</span></span>
> * <span data-ttu-id="8f7b9-181">Creare una nuova pagina Web per visualizzare i risultati</span><span class="sxs-lookup"><span data-stu-id="8f7b9-181">Create a new web page to display results</span></span>
> * <span data-ttu-id="8f7b9-182">Api babylon.js per creare e interagire con elementi 3D di base</span><span class="sxs-lookup"><span data-stu-id="8f7b9-182">The babylon.js API to create and interact with basic 3D elements</span></span>
> * <span data-ttu-id="8f7b9-183">Eseguire e testare l'applicazione in un simulatore Windows Mixed Reality dati</span><span class="sxs-lookup"><span data-stu-id="8f7b9-183">Run and test the application in a Windows Mixed Reality Simulator</span></span>

<span data-ttu-id="8f7b9-184">Per altre informazioni sullo sviluppo JavaScript per realtà mista, vedere [Panoramica dello sviluppo javascript.](/javascript-development-overview.md)</span><span class="sxs-lookup"><span data-stu-id="8f7b9-184">For more information on Mixed Reality JavaScript development see [JavaScript development overview](/javascript-development-overview.md).</span></span>

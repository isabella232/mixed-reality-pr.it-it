---
title: Babylon.js esercitazione per interagire con gli oggetti 3D
description: Informazioni su come usare babylon.js e interagire con gli oggetti 3D.
author: bogenera
ms.author: ayyonet
ms.date: 03/05/2021
ms.topic: article
keywords: realtà mista, JavaScript, esercitazione, BabylonJS, hololens, realtà mista, UWP, Windows 10, WebXR, Web immersiva
ms.localizationpriority: high
ms.openlocfilehash: 50c491a12b4c1c8e21a2c1fa1ae61e213370d276
ms.sourcegitcommit: cbfd1c37612aa6904fa41642ede6281d491e478d
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/23/2021
ms.locfileid: "104946437"
---
# <a name="tutorial-interact-with-3d-object"></a><span data-ttu-id="5ffc0-104">Esercitazione: interagire con un oggetto 3D</span><span class="sxs-lookup"><span data-stu-id="5ffc0-104">Tutorial: Interact with 3D object</span></span>

<span data-ttu-id="5ffc0-105">Informazioni su come creare oggetti e interazioni 3D per un'esperienza di realtà mista usando babylon.js.</span><span class="sxs-lookup"><span data-stu-id="5ffc0-105">Learn how to create 3D objects and interactions for a Mixed Reality experience using babylon.js.</span></span> <span data-ttu-id="5ffc0-106">In questa sezione si inizierà con qualcosa di semplice, ad esempio disegnare le facce di un cubo quando si seleziona l'oggetto.</span><span class="sxs-lookup"><span data-stu-id="5ffc0-106">In this section, you'll start with something simple, like painting the faces of a cube when you select the object.</span></span>

<span data-ttu-id="5ffc0-107">Questa esercitazione illustra gli argomenti seguenti:</span><span class="sxs-lookup"><span data-stu-id="5ffc0-107">This tutorial covers the following topics:</span></span>

> [!div class="checklist"]
> * <span data-ttu-id="5ffc0-108">Come aggiungere interazioni</span><span class="sxs-lookup"><span data-stu-id="5ffc0-108">How to add interactions</span></span>
> * <span data-ttu-id="5ffc0-109">Abilitare la modalità immersiva WebXR</span><span class="sxs-lookup"><span data-stu-id="5ffc0-109">Enable WebXR immersive mode</span></span>
> * <span data-ttu-id="5ffc0-110">Eseguire l'app nel simulatore di realtà mista di Windows</span><span class="sxs-lookup"><span data-stu-id="5ffc0-110">Run the app on Windows Mixed Reality Simulator</span></span>
> * <span data-ttu-id="5ffc0-111">Eseguire ed eseguire il debug dell'app in Android Chrome</span><span class="sxs-lookup"><span data-stu-id="5ffc0-111">Run and debug the app on Android Chrome</span></span>

## <a name="before-you-begin"></a><span data-ttu-id="5ffc0-112">Prima di iniziare</span><span class="sxs-lookup"><span data-stu-id="5ffc0-112">Before you begin</span></span>

<span data-ttu-id="5ffc0-113">Nel passaggio precedente dell'esercitazione è stata creata una pagina Web di base con una scena.</span><span class="sxs-lookup"><span data-stu-id="5ffc0-113">In previous tutorial step a basic web page with a scene was created.</span></span> <span data-ttu-id="5ffc0-114">Aprire la pagina Web di hosting per la modifica.</span><span class="sxs-lookup"><span data-stu-id="5ffc0-114">Have the hosting web page open for editing.</span></span>

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

## <a name="add-interaction"></a><span data-ttu-id="5ffc0-115">Aggiungi interazione</span><span class="sxs-lookup"><span data-stu-id="5ffc0-115">Add interaction</span></span>

1. <span data-ttu-id="5ffc0-116">Per prima cosa, è necessario aggiornare il codice che crea il cubo, in modo che il cubo venga disegnato con un colore casuale.</span><span class="sxs-lookup"><span data-stu-id="5ffc0-116">First, let's update our code that creates the cube, so that the cube is painted with a random color.</span></span> <span data-ttu-id="5ffc0-117">A tale scopo, il [materiale](https://doc.babylonjs.com/divingDeeper/materials/using/materials_introduction) viene aggiunto al cubo.</span><span class="sxs-lookup"><span data-stu-id="5ffc0-117">To do that, we will add [material](https://doc.babylonjs.com/divingDeeper/materials/using/materials_introduction) to our cube.</span></span> <span data-ttu-id="5ffc0-118">Material consente di specificare il colore e le trame e può essere utilizzato per coprire altri oggetti.</span><span class="sxs-lookup"><span data-stu-id="5ffc0-118">Material allows us to specify color and textures and can be used to cover other objects.</span></span> <span data-ttu-id="5ffc0-119">Il modo in cui viene visualizzato un materiale dipende dalla luce o dalle luci usate nella scena e dal modo in cui viene impostato per rispondere.</span><span class="sxs-lookup"><span data-stu-id="5ffc0-119">How a material appears depends on the light or lights used in the scene and how it is set to react.</span></span> <span data-ttu-id="5ffc0-120">Ad esempio, diffuseColor distribuisce il colore tutto sulla mesh a cui è collegato.</span><span class="sxs-lookup"><span data-stu-id="5ffc0-120">For example, the diffuseColor spreads the color all over the mesh to which it is attached.</span></span> <span data-ttu-id="5ffc0-121">Aggiungere il codice seguente:</span><span class="sxs-lookup"><span data-stu-id="5ffc0-121">Add the following code:</span></span>

    ```javascript
    var boxMaterial = new BABYLON.StandardMaterial("material", scene);
    boxMaterial.diffuseColor = BABYLON.Color3.Random();
    box.material = boxMaterial;
    ```

1. <span data-ttu-id="5ffc0-122">Ora che il cubo viene disegnato con un colore casuale, è possibile aggiungere un'interazione a:</span><span class="sxs-lookup"><span data-stu-id="5ffc0-122">Now that the cube is painted with a random color, let's add an interaction to:</span></span>

    * <span data-ttu-id="5ffc0-123">Modificare il colore quando si fa clic sul cubo</span><span class="sxs-lookup"><span data-stu-id="5ffc0-123">Change the color when the cube is clicked</span></span>
    * <span data-ttu-id="5ffc0-124">Spostare il cubo dopo la modifica del colore</span><span class="sxs-lookup"><span data-stu-id="5ffc0-124">Move the cube after the color is changed</span></span>

    <span data-ttu-id="5ffc0-125">Per aggiungere interazioni è necessario usare le [azioni](https://doc.babylonjs.com/divingDeeper/events/actions).</span><span class="sxs-lookup"><span data-stu-id="5ffc0-125">To add interactions we should be using [actions](https://doc.babylonjs.com/divingDeeper/events/actions).</span></span> <span data-ttu-id="5ffc0-126">Viene avviata un'azione in risposta al trigger di evento.</span><span class="sxs-lookup"><span data-stu-id="5ffc0-126">An action is launched in response to the event trigger.</span></span> <span data-ttu-id="5ffc0-127">Ad esempio, quando l'utente fa clic sul cubo.</span><span class="sxs-lookup"><span data-stu-id="5ffc0-127">For example, when the user clicks on the cube.</span></span> <span data-ttu-id="5ffc0-128">È sufficiente creare un'istanza di BABYLON. ActionManager e registrare un'azione per un determinato trigger.</span><span class="sxs-lookup"><span data-stu-id="5ffc0-128">All we need to do is instantiate BABYLON.ActionManager and register an action for certain trigger.</span></span> <span data-ttu-id="5ffc0-129">Il [BABYLON.ExecuteCodeAction](https://doc.babylonjs.com/typedoc/classes/babylon.executecodeaction) eseguirà la funzione JavaScript quando un utente fa clic sul cubo:</span><span class="sxs-lookup"><span data-stu-id="5ffc0-129">The [BABYLON.ExecuteCodeAction](https://doc.babylonjs.com/typedoc/classes/babylon.executecodeaction) will run our JavaScript function when someone clicks on the cube:</span></span>

    ```javascript
    box.actionManager = new BABYLON.ActionManager(scene);
    box.actionManager.registerAction(new BABYLON.ExecuteCodeAction(
        BABYLON.ActionManager.OnPickTrigger, 
        function (evt) {
            var sourceBox = evt.meshUnderPointer;
            
            //move the box upright
            sourceBox.position.x += 0.1;
            sourceBox.position.y += 0.1;

            //update the color
            boxMaterial.diffuseColor = BABYLON.Color3.Random();
        }));
    ```

1. <span data-ttu-id="5ffc0-130">Il codice finale della pagina Web sarà simile al seguente:</span><span class="sxs-lookup"><span data-stu-id="5ffc0-130">The final code of the web page will look as follows:</span></span>

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

                var boxMaterial = new BABYLON.StandardMaterial("material", scene);
                boxMaterial.diffuseColor = BABYLON.Color3.Random();
                box.material = boxMaterial;
 
                box.actionManager = new BABYLON.ActionManager(scene);
                box.actionManager.registerAction(
                    new BABYLON.ExecuteCodeAction(BABYLON.ActionManager.OnPickTrigger, 
                    function (evt) {
                        var sourceBox = evt.meshUnderPointer;
                        sourceBox.position.x += 0.1;
                        sourceBox.position.y += 0.1;

                        boxMaterial.diffuseColor = BABYLON.Color3.Random();
                    }));

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

## <a name="enable-webxr-immersive-experience"></a><span data-ttu-id="5ffc0-131">Abilitare l'esperienza immersiva WebXR</span><span class="sxs-lookup"><span data-stu-id="5ffc0-131">Enable WebXR immersive experience</span></span>

<span data-ttu-id="5ffc0-132">Ora che il cubo sta cambiando i colori, è possibile provare l'esperienza immersiva.</span><span class="sxs-lookup"><span data-stu-id="5ffc0-132">Now that our cube is changing colors, we're ready to try the immersive experience.</span></span>

1. <span data-ttu-id="5ffc0-133">In questo passaggio verrà introdotto un [terreno](https://doc.babylonjs.com/divingDeeper/mesh/creation/set/ground).</span><span class="sxs-lookup"><span data-stu-id="5ffc0-133">In this step we're going to introduce a [ground](https://doc.babylonjs.com/divingDeeper/mesh/creation/set/ground).</span></span> <span data-ttu-id="5ffc0-134">Il cubo verrà sospeso in aria e verrà visualizzato un piano in basso.</span><span class="sxs-lookup"><span data-stu-id="5ffc0-134">The cube will be hanging in the air and we will see a floor at the bottom.</span></span> <span data-ttu-id="5ffc0-135">Aggiungere il campo come segue:</span><span class="sxs-lookup"><span data-stu-id="5ffc0-135">Add the ground as follows:</span></span>

    ```javascript
    var ground = BABYLON.MeshBuilder.CreateGround("ground", {width: 4, height: 4});
    ```

    <span data-ttu-id="5ffc0-136">Viene così creato un semplice piano 4x4.</span><span class="sxs-lookup"><span data-stu-id="5ffc0-136">This creates a simple 4x4-meter floor.</span></span>

1. <span data-ttu-id="5ffc0-137">Per aggiungere il supporto WebXR, è necessario chiamare *createDefaultXRExperienceAsync*, che presenta un risultato di *promessa* .</span><span class="sxs-lookup"><span data-stu-id="5ffc0-137">In order to add WebXR support, we need to call *createDefaultXRExperienceAsync*, which has a *Promise* result.</span></span> <span data-ttu-id="5ffc0-138">Aggiungere questo codice alla fine della funzione *createScene* anziché della *scena Return;*:</span><span class="sxs-lookup"><span data-stu-id="5ffc0-138">Add this code at the end of *createScene* function instead of *return scene;*:</span></span>

    ```javascript
    var xrPromise = scene.createDefaultXRExperienceAsync({
        floorMeshes: [ground]
    });
    return xrPromise.then((xrExperience) => {
        console.log("Done, WebXR is enabled.");
        return scene;
    });
    ```

1. <span data-ttu-id="5ffc0-139">Il codice finale della pagina Web sarà simile al seguente:</span><span class="sxs-lookup"><span data-stu-id="5ffc0-139">The final code of the web page will look as follows:</span></span>

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

                var boxMaterial = new BABYLON.StandardMaterial("material", scene);
                boxMaterial.diffuseColor = BABYLON.Color3.Random();
                box.material = boxMaterial;
 
                box.actionManager = new BABYLON.ActionManager(scene);
                box.actionManager.registerAction(
                    new BABYLON.ExecuteCodeAction(BABYLON.ActionManager.OnPickTrigger, 
                    function (evt) {
                        var sourceBox = evt.meshUnderPointer;
                        sourceBox.position.x += 0.1;
                        sourceBox.position.y += 0.1;

                        boxMaterial.diffuseColor = BABYLON.Color3.Random();
                    }));
                    
                var ground = BABYLON.MeshBuilder.CreateGround("ground", {width: 4, height: 4});
                
                var xrPromise = scene.createDefaultXRExperienceAsync({
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

1. <span data-ttu-id="5ffc0-140">Il codice precedente genera l'output seguente nella finestra del browser: ![ WebXR scena](../images/hello-world-webxr-scene.png)</span><span class="sxs-lookup"><span data-stu-id="5ffc0-140">The above code generates the following output in the browser window: ![WebXR scene](../images/hello-world-webxr-scene.png)</span></span>

## <a name="run-on-a-windows-mixed-reality-simulator"></a><span data-ttu-id="5ffc0-141">Esegui in un simulatore di realtà mista di Windows</span><span class="sxs-lookup"><span data-stu-id="5ffc0-141">Run on a Windows Mixed Reality Simulator</span></span>

1. <span data-ttu-id="5ffc0-142">Selezionare il pulsante immersive-VR nell'angolo in basso a destra: ![ pulsante VR immersivo](../images/immersive-vr-button.png)</span><span class="sxs-lookup"><span data-stu-id="5ffc0-142">Select the Immersive-VR button on the bottom right corner: ![Immersive VR Button](../images/immersive-vr-button.png)</span></span>

1. <span data-ttu-id="5ffc0-143">Questa azione avvierà la finestra del simulatore di realtà mista di Windows come illustrato di seguito: ![ portale di realtà mista](../images/mixed-reality-portal.png)</span><span class="sxs-lookup"><span data-stu-id="5ffc0-143">This action will launch the Windows Mixed Reality Simulator window as shown below: ![Mixed Reality Portal](../images/mixed-reality-portal.png)</span></span>

1. <span data-ttu-id="5ffc0-144">Usare i tasti W, A, S e D sulla tastiera per andare avanti, a sinistra e a destra di conseguenza.</span><span class="sxs-lookup"><span data-stu-id="5ffc0-144">Use the W,A,S, and D keys on your keyboard to walk forward, back left and right accordingly.</span></span> <span data-ttu-id="5ffc0-145">Utilizzare la mano simulata per impostare il cubo come destinazione e premere il tasto INVIO sulla tastiera per eseguire l'azione di clic.</span><span class="sxs-lookup"><span data-stu-id="5ffc0-145">Use simulated hand to target the cube and press the Enter key on your keyboard to perform the click action.</span></span> <span data-ttu-id="5ffc0-146">Il colore del cubo cambierà e lo spostamento in una nuova posizione.</span><span class="sxs-lookup"><span data-stu-id="5ffc0-146">The cube will change its color and move to a new position.</span></span>

> [!NOTE]
> <span data-ttu-id="5ffc0-147">Quando la destinazione è il cubo, verificare che il raggio di chiusura (cerchio bianco) si interseca con il cubo, come illustrato nell'immagine precedente.</span><span class="sxs-lookup"><span data-stu-id="5ffc0-147">When targeting the cube, make sure that the end of hand ray (white circle) intersects with the cube as shown on the picture above.</span></span> <span data-ttu-id="5ffc0-148">Scopri di più su [Point and commit with hands](https://docs.microsoft.com/windows/mixed-reality/design/point-and-commit).</span><span class="sxs-lookup"><span data-stu-id="5ffc0-148">Learn more about [Point and commit with hands](https://docs.microsoft.com/windows/mixed-reality/design/point-and-commit).</span></span>

## <a name="run-and-debug-on-android-device"></a><span data-ttu-id="5ffc0-149">Eseguire ed eseguire il debug su un dispositivo Android</span><span class="sxs-lookup"><span data-stu-id="5ffc0-149">Run and debug on Android device</span></span>

<span data-ttu-id="5ffc0-150">Per abilitare il debug nel dispositivo Android, seguire questa procedura:</span><span class="sxs-lookup"><span data-stu-id="5ffc0-150">Perform the following steps to enable debugging on your Android device:</span></span>

### <a name="prerequisites"></a><span data-ttu-id="5ffc0-151">Prerequisiti</span><span class="sxs-lookup"><span data-stu-id="5ffc0-151">Prerequisites</span></span>

* <span data-ttu-id="5ffc0-152">Un server Web che funge da pagina HTML statica in un contesto sicuro (https://o tramite Port inoltring su localhost) nel computer di sviluppo.</span><span class="sxs-lookup"><span data-stu-id="5ffc0-152">A web server that serves static html page in secure context (https:// or via Port forwarding on localhost) on development machine.</span></span> <span data-ttu-id="5ffc0-153">Ad esempio, usare il *pacchetto NPM come* semplice server Web leggero che funge da file HTML statici, verificare la presenza di un altro [servizio NPM](https://github.com/vercel/serve#readme)</span><span class="sxs-lookup"><span data-stu-id="5ffc0-153">For example leverage *serve* npm package as simple lightweight web server that serves static html files, check more [npm serve](https://github.com/vercel/serve#readme)</span></span>
* <span data-ttu-id="5ffc0-154">Il dispositivo è stato originariamente fornito con la Google Play Store ed è necessario che sia in esecuzione Android 7,0 o versione successiva</span><span class="sxs-lookup"><span data-stu-id="5ffc0-154">The device originally shipped with the Google Play Store and must be running Android 7.0 or newer</span></span>
* <span data-ttu-id="5ffc0-155">La versione più recente di [Google Chrome](https://support.google.com/chrome/answer/95346) sia nella workstation di sviluppo che nel dispositivo</span><span class="sxs-lookup"><span data-stu-id="5ffc0-155">The latest version of [Google Chrome](https://support.google.com/chrome/answer/95346) on both the development workstation and on the device</span></span>
* <span data-ttu-id="5ffc0-156">Per verificare che il dispositivo sia configurato correttamente per l'esecuzione di WebXR, passare a una [pagina WebXR di esempio](https://immersive-web.github.io/webxr-samples/) nel dispositivo.</span><span class="sxs-lookup"><span data-stu-id="5ffc0-156">To verify that the device is correctly configured to run WebXR, browse to a [sample WebXR page](https://immersive-web.github.io/webxr-samples/) on the device.</span></span> <span data-ttu-id="5ffc0-157">Verrà visualizzato il messaggio, ad esempio:</span><span class="sxs-lookup"><span data-stu-id="5ffc0-157">You should see the message, such as:</span></span>

    > <span data-ttu-id="5ffc0-158">Il browser supporta WebXR ed è in grado di eseguire la realtà virtuale e le esperienze di realtà ampliate se si dispone dell'hardware appropriato.</span><span class="sxs-lookup"><span data-stu-id="5ffc0-158">Your browser supports WebXR and can run Virtual Reality and Augmented Reality experiences if you have the appropriate hardware.</span></span>

1. <span data-ttu-id="5ffc0-159">Abilitare la modalità sviluppatore e il debug USB in un dispositivo Android.</span><span class="sxs-lookup"><span data-stu-id="5ffc0-159">Enable developer mode and USB debugging on an Android device.</span></span> <span data-ttu-id="5ffc0-160">Vedere come eseguire questa operazione per la versione di Android nella pagina della documentazione ufficiale [configurare le opzioni per gli sviluppatori su dispositivo](https://developer.android.com/studio/debug/dev-options)</span><span class="sxs-lookup"><span data-stu-id="5ffc0-160">See how to do this for your version of Android at the official documentation page [Configure on-device developer options](https://developer.android.com/studio/debug/dev-options)</span></span>
1. <span data-ttu-id="5ffc0-161">Connettere quindi il dispositivo Android al computer di sviluppo o al portatile tramite un cavo USB</span><span class="sxs-lookup"><span data-stu-id="5ffc0-161">Next, connect Android device to your development machine or laptop via USB cable</span></span>
1. <span data-ttu-id="5ffc0-162">Verificare che il server Web nel computer di sviluppo sia in esecuzione.</span><span class="sxs-lookup"><span data-stu-id="5ffc0-162">Ensure that the web server on the development machine is running.</span></span> <span data-ttu-id="5ffc0-163">Ad esempio, passare alla cartella radice contenente la pagina di hosting Web (index.html) ed eseguire il codice seguente (presupponendo che si usi il pacchetto NPM):</span><span class="sxs-lookup"><span data-stu-id="5ffc0-163">For example, navigate to the root folder containing your web hosting page (index.html) and execute the following code (assuming you use serve npm package):</span></span>

    ```bash
    serve
    ```

1. <span data-ttu-id="5ffc0-164">Aprire Google Chrome nel computer di sviluppo e immettere nella barra degli indirizzi il testo seguente:</span><span class="sxs-lookup"><span data-stu-id="5ffc0-164">Open Google Chrome on your development machine and enter in the address bar the following text:</span></span>
    > <span data-ttu-id="5ffc0-165">Chrome://Inspect # Devices ![ Chrome USB debug window](../images/chrome-usb-debug.png)</span><span class="sxs-lookup"><span data-stu-id="5ffc0-165">chrome://inspect#devices ![Chrome USB debugging window](../images/chrome-usb-debug.png)</span></span>
1. <span data-ttu-id="5ffc0-166">Verificare che la casella di controllo *individua dispositivi USB* sia abilitata</span><span class="sxs-lookup"><span data-stu-id="5ffc0-166">Ensure that the *Discover USB devices* checkbox is enabled</span></span>
1. <span data-ttu-id="5ffc0-167">Fare clic sul pulsante *porta avanti* e verificare che l' *invio della porta* sia abilitato e che contenga una voce *localhost: 5000* come illustrato di seguito:  ![ finestra di inoltri porta Chrome](../images/chrome-port-forwarding.png)</span><span class="sxs-lookup"><span data-stu-id="5ffc0-167">Click the button *Port forwarding* and ensure that *Port forwarding* is enabled and contains an entry *localhost:5000* as shown below:  ![Chrome Port Forwarding window](../images/chrome-port-forwarding.png)</span></span>
1. <span data-ttu-id="5ffc0-168">Nel dispositivo Android connesso aprire una finestra di Google Chrome e passare a per *http://localhost:5000* visualizzare il cubo</span><span class="sxs-lookup"><span data-stu-id="5ffc0-168">In your connected Android device open a Google Chrome window and browse to *http://localhost:5000* and you should see the cube</span></span>
1. <span data-ttu-id="5ffc0-169">Nel computer di sviluppo, in Chrome, viene visualizzato il dispositivo e un elenco di pagine Web attualmente aperte:  ![ finestra ispezione di Chrome](../images/chrome-inspect.png)</span><span class="sxs-lookup"><span data-stu-id="5ffc0-169">On your development machine, in Chrome, you will see your device and a list of web pages currently opened in there:  ![Chrome Inspect window](../images/chrome-inspect.png)</span></span>
1. <span data-ttu-id="5ffc0-170">Fare clic sul pulsante *Controlla* accanto a una voce *http://localhost:5000* : finestra di debug di  ![ Chrome devtools](../images/chrome-debug.png)</span><span class="sxs-lookup"><span data-stu-id="5ffc0-170">Click the button *Inspect* next to an entry *http://localhost:5000*:  ![Chrome DevTools Debug window](../images/chrome-debug.png)</span></span>
1. <span data-ttu-id="5ffc0-171">Usare il [devtools Chrome](https://developers.google.com/web/tools/chrome-devtools) per eseguire il debug della pagina</span><span class="sxs-lookup"><span data-stu-id="5ffc0-171">Use the [Chrome DevTools](https://developers.google.com/web/tools/chrome-devtools) to debug the page</span></span>

## <a name="takeaways"></a><span data-ttu-id="5ffc0-172">Risultati</span><span class="sxs-lookup"><span data-stu-id="5ffc0-172">Takeaways</span></span>

<span data-ttu-id="5ffc0-173">Di seguito sono riportate le considerazioni più importanti di questa esercitazione:</span><span class="sxs-lookup"><span data-stu-id="5ffc0-173">The following are the most important takeaways from this tutorial:</span></span>
* <span data-ttu-id="5ffc0-174">Babylon.js semplifica la creazione di esperienze immersive mediante JavaScript</span><span class="sxs-lookup"><span data-stu-id="5ffc0-174">Babylon.js makes it easy to create immersive experiences using JavaScript</span></span>
* <span data-ttu-id="5ffc0-175">Per creare scene virtuali non è necessario scrivere codice di basso livello o apprendere una nuova tecnologia</span><span class="sxs-lookup"><span data-stu-id="5ffc0-175">To create virtual scenes you don't need to write low-level code or learn a new technology</span></span>
* <span data-ttu-id="5ffc0-176">È possibile creare applicazioni di realtà miste con browser supportato da WebXR senza dover acquistare una cuffia</span><span class="sxs-lookup"><span data-stu-id="5ffc0-176">You can build Mixed Reality applications with WebXR-supported browser without need to buy a headset</span></span>

## <a name="next-steps"></a><span data-ttu-id="5ffc0-177">Passaggi successivi</span><span class="sxs-lookup"><span data-stu-id="5ffc0-177">Next steps</span></span>

<span data-ttu-id="5ffc0-178">Congratulazioni!</span><span class="sxs-lookup"><span data-stu-id="5ffc0-178">Congratulations!</span></span> <span data-ttu-id="5ffc0-179">È stata completata la serie di esercitazioni di babylon.js e si è appreso come:</span><span class="sxs-lookup"><span data-stu-id="5ffc0-179">You've completed our series of babylon.js tutorials and learned how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="5ffc0-180">Configurare un ambiente di sviluppo</span><span class="sxs-lookup"><span data-stu-id="5ffc0-180">Set up a development environment</span></span>
> * <span data-ttu-id="5ffc0-181">Crea una nuova pagina Web per visualizzare i risultati</span><span class="sxs-lookup"><span data-stu-id="5ffc0-181">Create a new web page to display results</span></span>
> * <span data-ttu-id="5ffc0-182">API babylon.js per creare e interagire con gli elementi 3D di base</span><span class="sxs-lookup"><span data-stu-id="5ffc0-182">The babylon.js API to create and interact with basic 3D elements</span></span>
> * <span data-ttu-id="5ffc0-183">Eseguire e testare l'applicazione in un simulatore di realtà mista di Windows</span><span class="sxs-lookup"><span data-stu-id="5ffc0-183">Run and test the application in a Windows Mixed Reality Simulator</span></span>

<span data-ttu-id="5ffc0-184">Per altre informazioni sullo sviluppo di JavaScript con realtà mista, vedere [Cenni preliminari sullo sviluppo JavaScript](/javascript-development-overview.md).</span><span class="sxs-lookup"><span data-stu-id="5ffc0-184">For more information on Mixed Reality JavaScript development see [JavaScript development overview](/javascript-development-overview.md).</span></span>

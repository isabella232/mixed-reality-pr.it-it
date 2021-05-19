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
# <a name="tutorial-interact-with-3d-object"></a>Esercitazione: Interagire con un oggetto 3D

Informazioni su come creare oggetti e interazioni 3D per un'esperienza di realtà mista usando babylon.js. In questa sezione si inizierà con qualcosa di semplice, ad esempio disegnare i visi di un cubo quando si seleziona l'oggetto.

Questa esercitazione illustra gli argomenti seguenti:

> [!div class="checklist"]
> * Come aggiungere interazioni
> * Abilitare la modalità immersiva WebXR
> * Eseguire l'app nel simulatore Windows Mixed Reality app
> * Eseguire l'app ed eseguirne il debug in Android Chrome

## <a name="before-you-begin"></a>Prima di iniziare

Nel passaggio precedente dell'esercitazione è stata creata una pagina Web di base con una scena. Fare in modo che la pagina Web di hosting sia aperta per la modifica.

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

## <a name="add-interaction"></a>Aggiungere l'interazione

1. Prima di tutto, aggiornare il codice che crea il cubo, in modo che il cubo sia di colore casuale. A tale scopo, si [aggiungerà materiale](https://doc.babylonjs.com/divingDeeper/materials/using/materials_introduction) al cubo. Material consente di specificare colore e trame e può essere usato per coprire altri oggetti. Il modo in cui viene visualizzato un materiale dipende dalla luce o dalle luci usate nella scena e da come viene impostato per reagire. Ad esempio, diffuseColor estende il colore su tutta la mesh a cui è collegato. Aggiungere il codice seguente:

    ```javascript
    const boxMaterial = new BABYLON.StandardMaterial("material", scene);
    boxMaterial.diffuseColor = BABYLON.Color3.Random();
    box.material = boxMaterial;
    ```

1. Ora che il cubo è stato dipinto con un colore casuale, è possibile aggiungere un'interazione a:

    * Modificare il colore quando si fa clic sul cubo
    * Spostare il cubo dopo la modifica del colore

    Per aggiungere interazioni, è necessario usare [le azioni](https://doc.babylonjs.com/divingDeeper/events/actions). Viene avviata un'azione in risposta al trigger di evento. Ad esempio, quando l'utente fa clic sul cubo. È necessario solo creare un'istanza di BABYLON. ActionManager e registrare un'azione per un determinato trigger. [LBABYLON.ExealtacodeAction](https://doc.babylonjs.com/typedoc/classes/babylon.executecodeaction) eseguirà la funzione JavaScript quando un utente fa clic sul cubo:

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

## <a name="enable-webxr-immersive-experience"></a>Abilitare l'esperienza immersiva WebXR

Ora che i colori del cubo cambiano, è possibile provare l'esperienza immersiva.

1. In questo passaggio si introdurrà una [base.](https://doc.babylonjs.com/divingDeeper/mesh/creation/set/ground) Il cubo verrà sospeso nell'aria e nella parte inferiore verrà visualizzato un piano. Aggiungere il campo come segue:

    ```javascript
    const ground = BABYLON.MeshBuilder.CreateGround("ground", {width: 4, height: 4});
    ```

    In questo modo viene creato un semplice piano da 4x4 metri.

1. Per aggiungere il supporto di WebXR, è necessario chiamare *createDefaultXRExperienceAsync*, che ha un *risultato Promise.* Aggiungere questo codice alla fine della *funzione createScene* anziché restituire *la scena;*:

    ```javascript
    const xrPromise = scene.createDefaultXRExperienceAsync({
        floorMeshes: [ground]
    });
    return xrPromise.then((xrExperience) => {
        console.log("Done, WebXR is enabled.");
        return scene;
    });
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

1. Il codice precedente genera l'output seguente nella finestra del browser: ![ scena WebXR](../images/hello-world-webxr-scene.png)

## <a name="run-on-a-windows-mixed-reality-simulator"></a>Eseguire in un simulatore Windows Mixed Reality

1. Selezionare il pulsante Immersive-VR nell'angolo in basso a destra: ![ Immersive VR Button (Pulsante vr immersiva)](../images/immersive-vr-button.png)

1. Questa azione avvierà la finestra Windows Mixed Reality simulatore come illustrato di seguito: ![ Portale realtà mista](../images/mixed-reality-portal.png)

1. Usare i tasti W, A, S e D sulla tastiera per procedere, tornare a sinistra e a destra di conseguenza. Usare la mano simulata per impostare come destinazione il cubo e premere INVIO sulla tastiera per eseguire l'azione di clic. Il cubo cambierà colore e si sposterà in una nuova posizione.

> [!NOTE]
> Quando si fa riferimento al cubo, assicurarsi che l'estremità del raggio della mano (cerchio bianco) si interseci con il cubo, come illustrato nell'immagine precedente. Altre informazioni su [Point e commit con le mani.](https://docs.microsoft.com/windows/mixed-reality/design/point-and-commit)

## <a name="run-and-debug-on-android-device"></a>Eseguire ed eseguire il debug in un dispositivo Android

Seguire questa procedura per abilitare il debug nel dispositivo Android:

### <a name="prerequisites"></a>Prerequisiti

* Un server Web che fornisce una pagina HTML statica in un contesto sicuro (https:// o tramite port forwarding in localhost) nel computer di sviluppo. Ad esempio, *sfruttare il pacchetto* serve npm come semplice server Web leggero che serve file HTML statici, controllare più [npm serve](https://github.com/vercel/serve#readme)
* Il dispositivo originariamente fornito con il Google Play Store e deve eseguire Android 7.0 o versione più recente
* La versione più recente [di Google Chrome](https://support.google.com/chrome/answer/95346) sia nella workstation di sviluppo che nel dispositivo
* Per verificare che il dispositivo sia configurato correttamente per l'esecuzione di WebXR, passare a una [pagina WebXR](https://immersive-web.github.io/webxr-samples/) di esempio nel dispositivo. Verrà visualizzato il messaggio, ad esempio:

    > Il browser supporta WebXR e può eseguire esperienze di realtà virtuale e realtà aumentata se si dispone dell'hardware appropriato.

1. Abilitare la modalità sviluppatore e il debug USB in un dispositivo Android. Per informazioni su come eseguire questa operazione per la versione di Android in uso, vedere la pagina della documentazione ufficiale [Configurare le opzioni per sviluppatori sul dispositivo](https://developer.android.com/studio/debug/dev-options)
1. Connettere quindi il dispositivo Android al computer di sviluppo o al portatile tramite cavo USB
1. Assicurarsi che il server Web nel computer di sviluppo sia in esecuzione. Ad esempio, passare alla cartella radice contenente la pagina di hosting Web (index.html) ed eseguire il codice seguente (supponendo di usare il pacchetto serve npm):

    ```bash
    serve
    ```

1. Aprire Google Chrome nel computer di sviluppo e immettere nella barra degli indirizzi il testo seguente:
    > chrome://inspect#devices ![ Finestra di debug USB chrome](../images/chrome-usb-debug.png)
1. Assicurarsi che la casella *di controllo Individua dispositivi USB* sia abilitata
1. Fare clic sul pulsante *Port forwarding* (Inoltro porta) e assicurarsi che *port forwarding* sia abilitato e contenga una voce *localhost:5000,* come illustrato di seguito: Chrome Port Forwarding window (Finestra di inoltro delle porte di  ![ Chrome)](../images/chrome-port-forwarding.png)
1. Nel dispositivo Android connesso aprire una finestra di Google Chrome e passare *http://localhost:5000* a per visualizzare il cubo
1. Nel computer di sviluppo, in Chrome, verrà visualizzato il dispositivo e un elenco di pagine Web attualmente aperte in questa finestra:  ![ Chrome Inspect window (Ispezionare Chrome)](../images/chrome-inspect.png)
1. Fare clic sul pulsante *Inspect (Ispeziona)* accanto a una voce *http://localhost:5000* : Chrome  ![ DevTools Debug window (Debug di Chrome DevTools)](../images/chrome-debug.png)
1. Usare [Chrome DevTools per](https://developers.google.com/web/tools/chrome-devtools) eseguire il debug della pagina

## <a name="takeaways"></a>Risultati

Di seguito sono riportati i passaggi più importanti di questa esercitazione:
* Babylon.js semplifica la creazione di esperienze immersive con JavaScript
* Per creare scene virtuali non è necessario scrivere codice di basso livello o apprendere una nuova tecnologia
* È possibile creare applicazioni di realtà mista con un browser supportato da WebXR senza dover acquistare un visore VR

## <a name="next-steps"></a>Passaggi successivi

Congratulazioni! È stata completata la serie di esercitazioni babylon.js e si è appreso come:
> [!div class="checklist"]
> * Configurare un ambiente di sviluppo
> * Creare una nuova pagina Web per visualizzare i risultati
> * Api babylon.js per creare e interagire con elementi 3D di base
> * Eseguire e testare l'applicazione in un simulatore Windows Mixed Reality dati

Per altre informazioni sullo sviluppo JavaScript per realtà mista, vedere [Panoramica dello sviluppo javascript.](/javascript-development-overview.md)

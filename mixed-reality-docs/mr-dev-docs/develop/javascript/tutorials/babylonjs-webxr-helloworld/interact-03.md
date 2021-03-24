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
# <a name="tutorial-interact-with-3d-object"></a>Esercitazione: interagire con un oggetto 3D

Informazioni su come creare oggetti e interazioni 3D per un'esperienza di realtà mista usando babylon.js. In questa sezione si inizierà con qualcosa di semplice, ad esempio disegnare le facce di un cubo quando si seleziona l'oggetto.

Questa esercitazione illustra gli argomenti seguenti:

> [!div class="checklist"]
> * Come aggiungere interazioni
> * Abilitare la modalità immersiva WebXR
> * Eseguire l'app nel simulatore di realtà mista di Windows
> * Eseguire ed eseguire il debug dell'app in Android Chrome

## <a name="before-you-begin"></a>Prima di iniziare

Nel passaggio precedente dell'esercitazione è stata creata una pagina Web di base con una scena. Aprire la pagina Web di hosting per la modifica.

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

## <a name="add-interaction"></a>Aggiungi interazione

1. Per prima cosa, è necessario aggiornare il codice che crea il cubo, in modo che il cubo venga disegnato con un colore casuale. A tale scopo, il [materiale](https://doc.babylonjs.com/divingDeeper/materials/using/materials_introduction) viene aggiunto al cubo. Material consente di specificare il colore e le trame e può essere utilizzato per coprire altri oggetti. Il modo in cui viene visualizzato un materiale dipende dalla luce o dalle luci usate nella scena e dal modo in cui viene impostato per rispondere. Ad esempio, diffuseColor distribuisce il colore tutto sulla mesh a cui è collegato. Aggiungere il codice seguente:

    ```javascript
    var boxMaterial = new BABYLON.StandardMaterial("material", scene);
    boxMaterial.diffuseColor = BABYLON.Color3.Random();
    box.material = boxMaterial;
    ```

1. Ora che il cubo viene disegnato con un colore casuale, è possibile aggiungere un'interazione a:

    * Modificare il colore quando si fa clic sul cubo
    * Spostare il cubo dopo la modifica del colore

    Per aggiungere interazioni è necessario usare le [azioni](https://doc.babylonjs.com/divingDeeper/events/actions). Viene avviata un'azione in risposta al trigger di evento. Ad esempio, quando l'utente fa clic sul cubo. È sufficiente creare un'istanza di BABYLON. ActionManager e registrare un'azione per un determinato trigger. Il [BABYLON.ExecuteCodeAction](https://doc.babylonjs.com/typedoc/classes/babylon.executecodeaction) eseguirà la funzione JavaScript quando un utente fa clic sul cubo:

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

## <a name="enable-webxr-immersive-experience"></a>Abilitare l'esperienza immersiva WebXR

Ora che il cubo sta cambiando i colori, è possibile provare l'esperienza immersiva.

1. In questo passaggio verrà introdotto un [terreno](https://doc.babylonjs.com/divingDeeper/mesh/creation/set/ground). Il cubo verrà sospeso in aria e verrà visualizzato un piano in basso. Aggiungere il campo come segue:

    ```javascript
    var ground = BABYLON.MeshBuilder.CreateGround("ground", {width: 4, height: 4});
    ```

    Viene così creato un semplice piano 4x4.

1. Per aggiungere il supporto WebXR, è necessario chiamare *createDefaultXRExperienceAsync*, che presenta un risultato di *promessa* . Aggiungere questo codice alla fine della funzione *createScene* anziché della *scena Return;*:

    ```javascript
    var xrPromise = scene.createDefaultXRExperienceAsync({
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

1. Il codice precedente genera l'output seguente nella finestra del browser: ![ WebXR scena](../images/hello-world-webxr-scene.png)

## <a name="run-on-a-windows-mixed-reality-simulator"></a>Esegui in un simulatore di realtà mista di Windows

1. Selezionare il pulsante immersive-VR nell'angolo in basso a destra: ![ pulsante VR immersivo](../images/immersive-vr-button.png)

1. Questa azione avvierà la finestra del simulatore di realtà mista di Windows come illustrato di seguito: ![ portale di realtà mista](../images/mixed-reality-portal.png)

1. Usare i tasti W, A, S e D sulla tastiera per andare avanti, a sinistra e a destra di conseguenza. Utilizzare la mano simulata per impostare il cubo come destinazione e premere il tasto INVIO sulla tastiera per eseguire l'azione di clic. Il colore del cubo cambierà e lo spostamento in una nuova posizione.

> [!NOTE]
> Quando la destinazione è il cubo, verificare che il raggio di chiusura (cerchio bianco) si interseca con il cubo, come illustrato nell'immagine precedente. Scopri di più su [Point and commit with hands](https://docs.microsoft.com/windows/mixed-reality/design/point-and-commit).

## <a name="run-and-debug-on-android-device"></a>Eseguire ed eseguire il debug su un dispositivo Android

Per abilitare il debug nel dispositivo Android, seguire questa procedura:

### <a name="prerequisites"></a>Prerequisiti

* Un server Web che funge da pagina HTML statica in un contesto sicuro (https://o tramite Port inoltring su localhost) nel computer di sviluppo. Ad esempio, usare il *pacchetto NPM come* semplice server Web leggero che funge da file HTML statici, verificare la presenza di un altro [servizio NPM](https://github.com/vercel/serve#readme)
* Il dispositivo è stato originariamente fornito con la Google Play Store ed è necessario che sia in esecuzione Android 7,0 o versione successiva
* La versione più recente di [Google Chrome](https://support.google.com/chrome/answer/95346) sia nella workstation di sviluppo che nel dispositivo
* Per verificare che il dispositivo sia configurato correttamente per l'esecuzione di WebXR, passare a una [pagina WebXR di esempio](https://immersive-web.github.io/webxr-samples/) nel dispositivo. Verrà visualizzato il messaggio, ad esempio:

    > Il browser supporta WebXR ed è in grado di eseguire la realtà virtuale e le esperienze di realtà ampliate se si dispone dell'hardware appropriato.

1. Abilitare la modalità sviluppatore e il debug USB in un dispositivo Android. Vedere come eseguire questa operazione per la versione di Android nella pagina della documentazione ufficiale [configurare le opzioni per gli sviluppatori su dispositivo](https://developer.android.com/studio/debug/dev-options)
1. Connettere quindi il dispositivo Android al computer di sviluppo o al portatile tramite un cavo USB
1. Verificare che il server Web nel computer di sviluppo sia in esecuzione. Ad esempio, passare alla cartella radice contenente la pagina di hosting Web (index.html) ed eseguire il codice seguente (presupponendo che si usi il pacchetto NPM):

    ```bash
    serve
    ```

1. Aprire Google Chrome nel computer di sviluppo e immettere nella barra degli indirizzi il testo seguente:
    > Chrome://Inspect # Devices ![ Chrome USB debug window](../images/chrome-usb-debug.png)
1. Verificare che la casella di controllo *individua dispositivi USB* sia abilitata
1. Fare clic sul pulsante *porta avanti* e verificare che l' *invio della porta* sia abilitato e che contenga una voce *localhost: 5000* come illustrato di seguito:  ![ finestra di inoltri porta Chrome](../images/chrome-port-forwarding.png)
1. Nel dispositivo Android connesso aprire una finestra di Google Chrome e passare a per *http://localhost:5000* visualizzare il cubo
1. Nel computer di sviluppo, in Chrome, viene visualizzato il dispositivo e un elenco di pagine Web attualmente aperte:  ![ finestra ispezione di Chrome](../images/chrome-inspect.png)
1. Fare clic sul pulsante *Controlla* accanto a una voce *http://localhost:5000* : finestra di debug di  ![ Chrome devtools](../images/chrome-debug.png)
1. Usare il [devtools Chrome](https://developers.google.com/web/tools/chrome-devtools) per eseguire il debug della pagina

## <a name="takeaways"></a>Risultati

Di seguito sono riportate le considerazioni più importanti di questa esercitazione:
* Babylon.js semplifica la creazione di esperienze immersive mediante JavaScript
* Per creare scene virtuali non è necessario scrivere codice di basso livello o apprendere una nuova tecnologia
* È possibile creare applicazioni di realtà miste con browser supportato da WebXR senza dover acquistare una cuffia

## <a name="next-steps"></a>Passaggi successivi

Congratulazioni! È stata completata la serie di esercitazioni di babylon.js e si è appreso come:
> [!div class="checklist"]
> * Configurare un ambiente di sviluppo
> * Crea una nuova pagina Web per visualizzare i risultati
> * API babylon.js per creare e interagire con gli elementi 3D di base
> * Eseguire e testare l'applicazione in un simulatore di realtà mista di Windows

Per altre informazioni sullo sviluppo di JavaScript con realtà mista, vedere [Cenni preliminari sullo sviluppo JavaScript](/javascript-development-overview.md).

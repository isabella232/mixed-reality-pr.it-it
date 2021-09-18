---
title: Riprodurre il piano 3D
description: Informazioni su come aggiungere interazioni a un piano virtuale usando Babylon.js
author: JING1201
ms.author: v-vtieto
ms.prod: mixed-reality
ms.topic: tutorial
ms.date: 09/10/2021
keywords: realtà mista, javascript, esercitazione, BabylonJS, hololens, realtà mista, UWP, Windows 10, WebXR, web immersivo
ms.localizationpriority: high
ms.openlocfilehash: 8f995d618398fef56ce42d6c3e9863256627bf75
ms.sourcegitcommit: 645608f33d2d02625484c29586f42d21c442aaa9
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/18/2021
ms.locfileid: "127932425"
---
# <a name="tutorial-play-the-3d-piano"></a>Esercitazione: Riprodurre il piano 3D

Nell'esercitazione precedente è stato creato un modello di tastiera completa di piano a 88 tasti. A questo punto è possibile renderlo riproducibile nello spazio XR.

In questa esercitazione verranno illustrate le procedure per:

> [!div class="checklist"]
> * Aggiungere funzionalità interattive del piano usando gli eventi puntatore
> * Ridimensionare le mesh a dimensioni diverse
> * Abilitare il teletrasporto e il supporto a più puntatori in XR

## <a name="before-you-begin"></a>Prima di iniziare

Assicurarsi di aver seguito [l'esercitazione precedente](keyboard-model-02.md) della serie per continuare ad aggiungere il codice.

*index.html*

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

*scene.js*

```javascript
const buildKey = function (scene, parent, props) {
    if (props.type === "white") {
        /*
        Props for building a white key should contain: 
        note, topWidth, bottomWidth, topPositionX, wholePositionX, register, referencePositionX

        As an example, the props for building the middle C white key would be
        {type: "white", note: "C", topWidth: 1.4, bottomWidth: 2.3, topPositionX: -0.45, wholePositionX: -14.4, register: 4, referencePositionX: 0}
        */

        // Create bottom part
        const bottom = BABYLON.MeshBuilder.CreateBox("whiteKeyBottom", {width: props.bottomWidth, height: 1.5, depth: 4.5}, scene);

        // Create top part
        const top = BABYLON.MeshBuilder.CreateBox("whiteKeyTop", {width: props.topWidth, height: 1.5, depth: 5}, scene);
        top.position.z =  4.75;
        top.position.x += props.topPositionX;

        // Merge bottom and top parts
        // Parameters of BABYLON.Mesh.MergeMeshes: (arrayOfMeshes, disposeSource, allow32BitsIndices, meshSubclass, subdivideWithSubMeshes, multiMultiMaterials)
        const key = BABYLON.Mesh.MergeMeshes([bottom, top], true, false, null, false, false);
        key.position.x = props.referencePositionX + props.wholePositionX;
        key.name = props.note + props.register;
        key.parent = parent;

        return key;
    }
    else if (props.type === "black") {
        /*
        Props for building a black key should contain: 
        note, wholePositionX, register, referencePositionX

        As an example, the props for building the C#4 black key would be
        {type: "black", note: "C#", wholePositionX: -13.45, register: 4, referencePositionX: 0}
        */

        // Create black color material
        const blackMat = new BABYLON.StandardMaterial("black");
        blackMat.diffuseColor = new BABYLON.Color3(0, 0, 0);

        // Create black key
        const key = BABYLON.MeshBuilder.CreateBox(props.note + props.register, {width: 1.4, height: 2, depth: 5}, scene);
        key.position.z += 4.75;
        key.position.y += 0.25;
        key.position.x = props.referencePositionX + props.wholePositionX;
        key.material = blackMat;
        key.parent = parent;

        return key;
    }
}

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

    const keyParams = [
        {type: "white", note: "C", topWidth: 1.4, bottomWidth: 2.3, topPositionX: -0.45, wholePositionX: -14.4},
        {type: "black", note: "C#", wholePositionX: -13.45},
        {type: "white", note: "D", topWidth: 1.4, bottomWidth: 2.4, topPositionX: 0, wholePositionX: -12},
        {type: "black", note: "D#", wholePositionX: -10.6},
        {type: "white", note: "E", topWidth: 1.4, bottomWidth: 2.3, topPositionX: 0.45, wholePositionX: -9.6},
        {type: "white", note: "F", topWidth: 1.3, bottomWidth: 2.4, topPositionX: -0.55, wholePositionX: -7.2},
        {type: "black", note: "F#", wholePositionX: -6.35},
        {type: "white", note: "G", topWidth: 1.3, bottomWidth: 2.3, topPositionX: -0.2, wholePositionX: -4.8},
        {type: "black", note: "G#", wholePositionX: -3.6},
        {type: "white", note: "A", topWidth: 1.3, bottomWidth: 2.3, topPositionX: 0.2, wholePositionX: -2.4},
        {type: "black", note: "A#", wholePositionX: -0.85},
        {type: "white", note: "B", topWidth: 1.3, bottomWidth: 2.4, topPositionX: 0.55, wholePositionX: 0},
    ]

    // Transform Node that acts as the parent of all piano keys
    const keyboard = new BABYLON.TransformNode("keyboard");

    // Register 1 through 7
    var referencePositionX = -2.4*14;
    for (let register = 1; register <= 7; register++) {
        keyParams.forEach(key => {
            buildKey(scene, keyboard, Object.assign({register: register, referencePositionX: referencePositionX}, key));
        })
        referencePositionX += 2.4*7;
    }

    // Register 0
    buildKey(scene, keyboard, {type: "white", note: "A", topWidth: 1.9, bottomWidth: 2.3, topPositionX: -0.20, wholePositionX: -2.4, register: 0, referencePositionX: -2.4*21});
    keyParams.slice(10, 12).forEach(key => {
        buildKey(scene, keyboard, Object.assign({register: 0, referencePositionX: -2.4*21}, key));
    })

    // Register 8
    buildKey(scene, keyboard, {type: "white", note: "C", topWidth: 2.3, bottomWidth: 2.3, topPositionX: 0, wholePositionX: -2.4*6, register: 8, referencePositionX: 84});

    // Transform node that acts as the parent of all piano components
    const piano = new BABYLON.TransformNode("piano");
    keyboard.parent = piano;

    // Import and scale piano frame
    BABYLON.SceneLoader.ImportMesh("frame", "https://docs.microsoft.com/windows/mixed-reality/develop/javascript/tutorials/babylonjs-webxr-piano/files", "pianoFrame.babylon", scene, function(meshes) {
        const frame = meshes[0];
        frame.parent = piano;
    });

    // Lift the piano keyboard
    keyboard.position.y += 80;

    const xrHelper = await scene.createDefaultXRExperienceAsync();

    return scene;
}
```

## <a name="making-the-piano-keyboard-playable"></a>Rendere la tastiera del piano riproducibile

Al momento, la tastiera del piano creata è un modello statico che non risponde alle interazioni dell'utente. In questa sezione verranno programmati i tasti per spostarsi verso il basso e riprodurre un suono quando qualcuno li preme.

1. Babylon.js tipi diversi di eventi, [o oggetti osservabili,](https://doc.babylonjs.com/divingDeeper/events/observables)con cui è possibile interagire. In questo caso, si avrà a che fare con poiché si vogliono programmare i tasti per eseguire azioni quando qualcuno li preme tramite un puntatore, che può essere un clic del mouse, un tocco, un clic del pulsante del controller XR e così `onPointerObservable` via.

    Ecco la struttura di base di come è possibile aggiungere qualsiasi comportamento a `onPointerObservable` un oggetto :

    ```javascript
    scene.onPointerObservable.add((pointerInfo) => {
        // do something
    });
    ```

1. Mentre Babylon.js fornisce molti [tipi](https://doc.babylonjs.com/typedoc/classes/babylon.pointereventtypes)diversi di eventi puntatore, verranno utilizzati solo gli eventi e per programmare il comportamento dei tasti del piano, usando `POINTERDOWN` la struttura `POINTERUP` seguente:

    ```javascript
    scene.onPointerObservable.add((pointerInfo) => {
        switch (pointerInfo.type) {
            case BABYLON.PointerEventTypes.POINTERDOWN:
                // When the pointer is down on a piano key,
                // move the piano key downward (to show that it is pressed)
                // and play the sound of the note
                break;
            case BABYLON.PointerEventTypes.POINTERUP:
                // When the pointer is released,
                // move the piano key upward to its original position
                // and stop the sound of the note of the key that is released
                break;
        }
    });
    ```

1. Prima di tutto, si sposta il tasto piano verso il basso e verso l'alto quando si preme e si rilascia il tasto.

    All'evento puntatore verso il basso, è necessario rilevare la mesh su cui si fa clic, assicurarsi che si tratta di una chiave di piano e modificare negativamente la coordinata y della mesh di una piccola quantità per renderla simile alla pressione del tasto.

    Per l'evento pointer up, è un po' più complicato perché il puntatore che ha premuto il tasto potrebbe non essere rilasciato sul tasto. Ad esempio, un utente potrebbe fare clic sul tasto C4, trascinare il mouse su E4 e quindi rilasciare il clic. In questo caso, è comunque necessario rilasciare il tasto premuto (C4) anziché il punto in cui si verifica `pointerUp` l'evento (E4).

    Di seguito viene illustrato come il codice seguente ottiene ciò che si vuole:

    ```javascript
    const pointerToKey = new Map();
    scene.onPointerObservable.add((pointerInfo) => {
        switch (pointerInfo.type) {
            case BABYLON.PointerEventTypes.POINTERDOWN:
                if(pointerInfo.pickInfo.hit) {
                    const pickedMesh = pointerInfo.pickInfo.pickedMesh;
                    const pointerId = pointerInfo.event.pointerId;
                    if (pickedMesh.parent === keyboard) {
                        pickedMesh.position.y -= 0.5;
                        // play the sound of the note
                        pointerToKey.set(pointerId, {
                            mesh: pickedMesh
                        });
                    }
                }
                break;
            case BABYLON.PointerEventTypes.POINTERUP:
                const pointerId = pointerInfo.event.pointerId;
                if (pointerToKey.has(pointerId)) {
                    pointerToKey.get(pointerId).mesh.position.y += 0.5;
                    // stop the sound of the note of the key that is released
                    pointerToKey.delete(pointerId);
                }
                break;
        }
    });
    ```

    è univoco per ogni puntatore e può essere utile per identificare un puntatore quando sono presenti più controller o se si `pointerId` usa un touch screen. In questo caso è stato inizializzato un oggetto denominato per archiviare la relazione di quale puntatore ha premuto il tasto, in modo da sapere quale tasto rilasciare quando il puntatore viene rilasciato, indipendentemente da dove avviene il `Map` `pointerToKey` rilascio.

1. Ecco l'aspetto dell'interazione con il codice precedente:

    ![Tasti piano interattivi](./images/interactive-piano-keys.gif)

1. Ora si lavora per riprodurre e arrestare un suono quando un tasto viene premuto e rilasciato. A tale scopo, verrà utilizzata una libreria Javascript denominata **soundfont-player,** che consente di riprodurre facilmente i suoni MIDI di uno strumento scelto.

    [Scaricare il codice minificato](./files/soundfont-player.min.js)della libreria, salvarlo nella stessa cartellaindex.html *e* includerlo nel `<header>` tag in *index.html*:

    ```html
    <head>
        <title>Babylon Template</title>
        <script src="https://cdn.babylonjs.com/babylon.js"></script>
        <script src="scene.js"></script>
        <script src="soundfont-player.min.js"></script>
        <style>
                body,#renderCanvas { width: 100%; height: 100%;}
        </style>
    </head>
    ```

    Dopo aver importato la libreria, ecco come inizializzare uno strumento e riprodurre/arrestare i suoni MIDI usando la libreria:

    ```javascript
    const pianoSound = await Soundfont.instrument(new AudioContext(), 'acoustic_grand_piano');
    const C4 = piano.play("C4"); // Play note C4
    C4.stop(); // Stop note C4
    ```

1. Ora si incorpora questo negli eventi del puntatore e si finalizza il codice per questa sezione:

    ```javascript
    const pointerToKey = new Map()
    const piano = await Soundfont.instrument(new AudioContext(), 'acoustic_grand_piano');

    scene.onPointerObservable.add((pointerInfo) => {
        switch (pointerInfo.type) {
            case BABYLON.PointerEventTypes.POINTERDOWN:
                if(pointerInfo.pickInfo.hit) {
                    let pickedMesh = pointerInfo.pickInfo.pickedMesh;
                    let pointerId = pointerInfo.event.pointerId;
                    if (keys.has(pickedMesh)) {
                        pickedMesh.position.y -= 0.5; // Move the key downward
                        pointerToKey.set(pointerId, {
                            mesh: pickedMesh,
                            note: pianoSound.play(pointerInfo.pickInfo.pickedMesh.name) // Play the sound of the note
                        });
                    }
                }
                break;
            case BABYLON.PointerEventTypes.POINTERUP:
                let pointerId = pointerInfo.event.pointerId;
                if (pointerToKey.has(pointerId)) {
                    pointerToKey.get(pointerId).mesh.position.y += 0.5; // Move the key upward
                    pointerToKey.get(pointerId).note.stop(); // Stop the sound of the note
                    pointerToKey.delete(pointerId);
                }
                break;
        }
    });
    ```

    Dato che la mesh di ogni chiave è stata denominata dalla nota che rappresenta, è possibile indicare facilmente quale nota riprodurre passando il nome della mesh alla `pianoSound.play()` funzione. Si noti anche che il suono viene archiviato nella mappa in modo da sapere quale suono arrestare quando `pointerToKey` viene rilasciato un tasto.

## <a name="scaling-the-piano-for-immersive-vr-mode"></a>Ridimensionamento del piano per la modalità VR immersiva

A questo punto probabilmente si è già suonato con il piano con il mouse (o anche con un touch screen) mentre sono state aggiunte le funzionalità interattive. In questa sezione si verrà spostati nello spazio VR immersivo.

1. Per aprire la pagina nel visore VR immersivo, è necessario prima connettere il visore al computer per sviluppatori e assicurarsi che sia configurato per l'uso [nell'app Windows Mixed Reality](/enthusiast-guide/set-up-windows-mixed-reality). Se si usa il simulatore Windows Mixed Reality, assicurarsi [che sia abilitato.](../../../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md)

1. Verrà ora visualizzato un pulsante Vr immersivo in basso a destra nella pagina Web. Fare clic su di esso per visualizzare il piano nel dispositivo XR a cui si è connessi.

    ![Pulsante VR immersivo](../images/immersive-vr-button.png)

1. Quando ci si trova nello spazio virtuale, è possibile notare che il piano creato è estremamente grande. Nel mondo vr, possiamo solo in piedi nella parte inferiore e riprodurla puntando il puntatore alle chiavi in lontananza.

    ![Piano enorme](./images/huge-piano.jpg)

1. Il piano verrà ridimensionato in modo che le sue dimensioni sono più simili a un normale piano di supporto nella vita reale. A tale scopo, è necessario usare una funzione di utilità che consente di ridimensionare una [mesh rispetto a un punto nello spazio](https://doc.babylonjs.com/toolsAndResources/utilities/Pivot#enlargement). Aggiungere questa funzione *a* scene.js(all'esterno di `createScene()` ):

    ```javascript
    const scaleFromPivot = function(transformNode, pivotPoint, scale) {
        const _sx = scale / transformNode.scaling.x;
        const _sy = scale / transformNode.scaling.y;
        const _sz = scale / transformNode.scaling.z;
        transformNode.scaling = new BABYLON.Vector3(_sx, _sy, _sz); 
        transformNode.position = new BABYLON.Vector3(pivotPoint.x + _sx * (transformNode.position.x - pivotPoint.x), pivotPoint.y + _sy * (transformNode.position.y - pivotPoint.y), pivotPoint.z + _sz * (transformNode.position.z - pivotPoint.z));
    }
    ```

    Questa funzione accetta 3 parametri:
    * **transformNode:** oggetto `TransformNode` da ridimensionare
    * **pivotPoint:** oggetto che indica il punto a cui è relativo `Vector3` il ridimensionamento
    * **scale:** fattore di scala

1. Questa funzione verrà utilizzata per ridimensionare la cornice del piano e i tasti di un fattore di 0,015, con un punto pivot all'origine. Aggiungere la chiamata di funzione alla `createScene()` funzione inserendola dopo `keyboard.position.y += 80;` :

    ```javascript
    // Put this line at the beginning of createScene()
    const scale = 0.015;
    ```

    ```javascript
    // Put this function call after keyboard.position.y += 80;

    // Scale the entire piano
    scaleFromPivot(piano, new BABYLON.Vector3(0, 0, 0), scale);
    ```

1. Non dimentichiamo di ridimensionare anche la posizione della fotocamera:

    ```javascript
    const alpha =  3*Math.PI/2;
    const beta = Math.PI/50;
    const radius = 220*scale; // scale the radius
    const target = new BABYLON.Vector3(0, 0, 0);
    
    const camera = new BABYLON.ArcRotateCamera("Camera", alpha, beta, radius, target, scene);
    camera.attachControl(canvas, true);
    ```

1. Ora, quando si entra di nuovo nello spazio VR, il piano sarà delle dimensioni di un piano di supporto normale.

    ![Piano di supporto normale in VR](./images/normal-standup-piano.jpg)

## <a name="enabling-webxr-features"></a>Abilitazione delle funzionalità WebXR

Ora che il piano è stato ridimensionato alle dimensioni giuste nello spazio VR, è possibile abilitare alcune funzionalità WebXR interessanti per migliorare l'esperienza di esecuzione del piano nello spazio.

1. Se si è riprodotto il piano usando i controller VR immersivi, è possibile notare che è possibile usare un solo controller alla volta. Si abiliterà ora il [supporto a](https://doc.babylonjs.com/typedoc/interfaces/babylon.iwebxrcontrollerpointerselectionoptions) più puntatori nello spazio XR usando il Babylon.js [funzionalità WebXR di Babylon.js](https://doc.babylonjs.com/divingDeeper/webXR/webXRFeaturesManager).

    Aggiungere il codice seguente alla funzione `createScene()` dopo la riga di `xrHelper` inizializzazione:

    ```javascript
    const featuresManager = xrHelper.baseExperience.featuresManager;

    const pointerSelection = featuresManager.enableFeature(BABYLON.WebXRFeatureName.POINTER_SELECTION, "stable", {
        xrInput: xrHelper.input,
        enablePointerSelectionOnAllControllers: true        
    });
    ```

1. Inoltre, a seconda di dove si trova il punto di partenza, potrebbe risultare un po' difficile posizionarsi davanti al piano. Se si ha familiarità con l'ambiente VR immersivo, è possibile che si conosca già il **teletrasporto,** una funzionalità che consente di passare immediatamente a un altro punto dello spazio puntando su di esso.

1. Per usare la Babylon.js [di teletrasporto,](https://doc.babylonjs.com/divingDeeper/webXR/WebXRSelectedFeatures#teleportation-module)è prima di tutto necessario avere una mesh di terra che sia possibile "restare" nello spazio VR. Aggiungere il codice seguente alla `createScene()` funzione per creare una base:

    ```javascript
    const ground = BABYLON.MeshBuilder.CreateGround("ground", {width: 400, height: 400});
    ```

1. Il supporto per il teletrasporto include anche una funzionalità molto utile denominata [posizioni snap-to.](https://doc.babylonjs.com/divingDeeper/webXR/WebXRSelectedFeatures#snap-to-hotspots) In breve, le posizioni snap-to sono posizioni specifiche a cui si vuole che gli utenti atterrino.

    Ad esempio, è possibile impostare una posizione snap-to davanti al piano in modo che gli utenti possano teletrasportarsi facilmente a tale posizione quando puntano i puntatori vicino al piano.

    Aggiungere il codice seguente per abilitare la funzionalità di teletrasporto e specificare uno snap-to-point:

    ```javascript
    const teleportation = featuresManager.enableFeature(BABYLON.WebXRFeatureName.TELEPORTATION, "stable", {
        xrInput: xrHelper.input,
        floorMeshes: [ground],
        snapPositions: [new BABYLON.Vector3(2.4*3.5*scale, 0, -10*scale)],
    });
    ```

1. A questo punto, si dovrebbe essere in grado di posizionarsi facilmente davanti al piano teletrasportando verso lo snap-to-point davanti al piano e si dovrebbe essere in grado di riprodurre due tasti alla volta usando entrambi i controller.

    ![Teletrasporto al piano](./images/teleportation-demo.gif)

    ![Riproduzione di un piano con controller](./images/play-piano-controller.gif)

## <a name="summary"></a>Riepilogo

Congratulazioni! È stata completata la serie dell'esercitazione sulla creazione Babylon.js piano e si è appreso come:

> [!div class="checklist"]
> * Creare, posizionare e unire mesh per creare un modello di tastiera per piano
> * Importare un Babylon.js di un piano di supporto
> * Aggiungere interazioni con il puntatore a ogni tasto del piano
> * Ridimensionare le dimensioni delle mesh in base a un punto pivot
> * Abilitare le principali funzionalità WebXR, ad esempio il teletrasporto e il supporto multipointer

Ecco il codice finale per *scene.js* e *index.html*:

*scene.js*

```javascript
const buildKey = function (scene, parent, props) {
    if (props.type === "white") {
        /*
        Props for building a white key should contain: 
        note, topWidth, bottomWidth, topPositionX, wholePositionX, register, referencePositionX

        As an example, the props for building the middle C white key would be
        {type: "white", note: "C", topWidth: 1.4, bottomWidth: 2.3, topPositionX: -0.45, wholePositionX: -14.4, register: 4, referencePositionX: 0}
        */

        // Create bottom part
        const bottom = BABYLON.MeshBuilder.CreateBox("whiteKeyBottom", {width: props.bottomWidth, height: 1.5, depth: 4.5}, scene);

        // Create top part
        const top = BABYLON.MeshBuilder.CreateBox("whiteKeyTop", {width: props.topWidth, height: 1.5, depth: 5}, scene);
        top.position.z =  4.75;
        top.position.x += props.topPositionX;

        // Merge bottom and top parts
        // Parameters of BABYLON.Mesh.MergeMeshes: (arrayOfMeshes, disposeSource, allow32BitsIndices, meshSubclass, subdivideWithSubMeshes, multiMultiMaterials)
        const key = BABYLON.Mesh.MergeMeshes([bottom, top], true, false, null, false, false);
        key.position.x = props.referencePositionX + props.wholePositionX;
        key.name = props.note + props.register;
        key.parent = parent;

        return key;
    }
    else if (props.type === "black") {
        /*
        Props for building a black key should contain: 
        note, wholePositionX, register, referencePositionX

        As an example, the props for building the C#4 black key would be
        {type: "black", note: "C#", wholePositionX: -13.45, register: 4, referencePositionX: 0}
        */

        // Create black color material
        const blackMat = new BABYLON.StandardMaterial("black");
        blackMat.diffuseColor = new BABYLON.Color3(0, 0, 0);

        // Create black key
        const key = BABYLON.MeshBuilder.CreateBox(props.note + props.register, {width: 1.4, height: 2, depth: 5}, scene);
        key.position.z += 4.75;
        key.position.y += 0.25;
        key.position.x = props.referencePositionX + props.wholePositionX;
        key.material = blackMat;
        key.parent = parent;

        return key;
    }
}

const scaleFromPivot = function(transformNode, pivotPoint, scale) {
    const _sx = scale / transformNode.scaling.x;
    const _sy = scale / transformNode.scaling.y;
    const _sz = scale / transformNode.scaling.z;
    transformNode.scaling = new BABYLON.Vector3(_sx, _sy, _sz); 
    transformNode.position = new BABYLON.Vector3(pivotPoint.x + _sx * (transformNode.position.x - pivotPoint.x), pivotPoint.y + _sy * (transformNode.position.y - pivotPoint.y), pivotPoint.z + _sz * (transformNode.position.z - pivotPoint.z));
}

const createScene = async function(engine) {
    const scale = 0.015;
    const scene = new BABYLON.Scene(engine);

    const alpha =  3*Math.PI/2;
    const beta = Math.PI/50;
    const radius = 220*scale;
    const target = new BABYLON.Vector3(0, 0, 0);

    const camera = new BABYLON.ArcRotateCamera("Camera", alpha, beta, radius, target, scene);
    camera.attachControl(canvas, true);

    const light = new BABYLON.HemisphericLight("light", new BABYLON.Vector3(0, 1, 0), scene);
    light.intensity = 0.6;

    const keyParams = [
        {type: "white", note: "C", topWidth: 1.4, bottomWidth: 2.3, topPositionX: -0.45, wholePositionX: -14.4},
        {type: "black", note: "C#", wholePositionX: -13.45},
        {type: "white", note: "D", topWidth: 1.4, bottomWidth: 2.4, topPositionX: 0, wholePositionX: -12},
        {type: "black", note: "D#", wholePositionX: -10.6},
        {type: "white", note: "E", topWidth: 1.4, bottomWidth: 2.3, topPositionX: 0.45, wholePositionX: -9.6},
        {type: "white", note: "F", topWidth: 1.3, bottomWidth: 2.4, topPositionX: -0.55, wholePositionX: -7.2},
        {type: "black", note: "F#", wholePositionX: -6.35},
        {type: "white", note: "G", topWidth: 1.3, bottomWidth: 2.3, topPositionX: -0.2, wholePositionX: -4.8},
        {type: "black", note: "G#", wholePositionX: -3.6},
        {type: "white", note: "A", topWidth: 1.3, bottomWidth: 2.3, topPositionX: 0.2, wholePositionX: -2.4},
        {type: "black", note: "A#", wholePositionX: -0.85},
        {type: "white", note: "B", topWidth: 1.3, bottomWidth: 2.4, topPositionX: 0.55, wholePositionX: 0},
    ]

    // Transform Node that acts as the parent of all piano keys
    const keyboard = new BABYLON.TransformNode("keyboard");

    // Register 1 through 7
    var referencePositionX = -2.4*14;
    for (let register = 1; register <= 7; register++) {
        keyParams.forEach(key => {
            buildKey(scene, keyboard, Object.assign({register: register, referencePositionX: referencePositionX}, key));
        })
        referencePositionX += 2.4*7;
    }

    // Register 0
    buildKey(scene, keyboard, {type: "white", note: "A", topWidth: 1.9, bottomWidth: 2.3, topPositionX: -0.20, wholePositionX: -2.4, register: 0, referencePositionX: -2.4*21});
    keyParams.slice(10, 12).forEach(key => {
        buildKey(scene, keyboard, Object.assign({register: 0, referencePositionX: -2.4*21}, key));
    })

    // Register 8
    buildKey(scene, keyboard, {type: "white", note: "C", topWidth: 2.3, bottomWidth: 2.3, topPositionX: 0, wholePositionX: -2.4*6, register: 8, referencePositionX: 84});

    // Transform node that acts as the parent of all piano components
    const piano = new BABYLON.TransformNode("piano");
    keyboard.parent = piano;

    // Import and scale piano frame
    BABYLON.SceneLoader.ImportMesh("frame", "https://docs.microsoft.com/windows/mixed-reality/develop/javascript/tutorials/babylonjs-webxr-piano/files", "pianoFrame.babylon", scene, function(meshes) {
        const frame = meshes[0];
        frame.parent = piano;
    });

    // Lift the piano keyboard
    keyboard.position.y += 80;

    // Scale the entire piano
    scaleFromPivot(piano, new BABYLON.Vector3(0, 0, 0), scale);

    const pointerToKey = new Map()
    const pianoSound = await Soundfont.instrument(new AudioContext(), 'acoustic_grand_piano');

    scene.onPointerObservable.add((pointerInfo) => {
        switch (pointerInfo.type) {
            case BABYLON.PointerEventTypes.POINTERDOWN:
                // Only take action if the pointer is down on a mesh
                if(pointerInfo.pickInfo.hit) {
                    let pickedMesh = pointerInfo.pickInfo.pickedMesh;
                    let pointerId = pointerInfo.event.pointerId;
                    if (pickedMesh.parent === keyboard) {
                        pickedMesh.position.y -= 0.5; // Move the key downward
                        pointerToKey.set(pointerId, {
                            mesh: pickedMesh,
                            note: pianoSound.play(pointerInfo.pickInfo.pickedMesh.name) // Play the sound of the note
                        });
                    }
                }
                break;
            case BABYLON.PointerEventTypes.POINTERUP:
                let pointerId = pointerInfo.event.pointerId;
                // Only take action if the released pointer was recorded in pointerToKey
                if (pointerToKey.has(pointerId)) {
                    pointerToKey.get(pointerId).mesh.position.y += 0.5; // Move the key upward
                    pointerToKey.get(pointerId).note.stop(); // Stop the sound of the note
                    pointerToKey.delete(pointerId);
                }
                break;
        }
    });

    const xrHelper = await scene.createDefaultXRExperienceAsync();

    const featuresManager = xrHelper.baseExperience.featuresManager;

    featuresManager.enableFeature(BABYLON.WebXRFeatureName.POINTER_SELECTION, "stable", {
        xrInput: xrHelper.input,
        enablePointerSelectionOnAllControllers: true        
    });

    const ground = BABYLON.MeshBuilder.CreateGround("ground", {width: 400, height: 400});

    featuresManager.enableFeature(BABYLON.WebXRFeatureName.TELEPORTATION, "stable", {
        xrInput: xrHelper.input,
        floorMeshes: [ground],
        snapPositions: [new BABYLON.Vector3(2.4*3.5*scale, 0, -10*scale)],
    });

    return scene;
}
```

*index.html*

```html
<html>
    <head>
        <title>Babylon Template</title>
        <script src="https://cdn.babylonjs.com/babylon.js"></script>
        <script src="scene.js"></script>
        <script src="soundfont-player.min.js"></script>
        <style>
            body,#renderCanvas { width: 100%; height: 100%;}
        </style>
    </head>
   <body>
    <canvas id="renderCanvas"></canvas>
    <script>
        const canvas = document.getElementById("renderCanvas"); // Get the canvas element
        const engine = new BABYLON.Engine(canvas, true); // Generate the BABYLON 3D engine

        // Register a render loop to repeatedly render the scene
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

## <a name="next-steps"></a>Passaggi successivi

Per altre informazioni sullo sviluppo JavaScript di realtà mista, vedere [Panoramica dello sviluppo JavaScript.](/javascript-development-overview.md)

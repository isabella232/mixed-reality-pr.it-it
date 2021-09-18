---
title: Creare un modello di piano 3D
description: Informazioni su come creare un modello di piano 3D codificando con Babylon.js
author: JING1201
ms.author: v-vtieto
ms.prod: mixed-reality
ms.topic: tutorial
ms.date: 09/10/2021
keywords: realtà mista, javascript, esercitazione, BabylonJS, hololens, realtà mista, UWP, Windows 10, WebXR, web immersive
ms.localizationpriority: high
ms.openlocfilehash: e5c3dd6206566f781ceb52e5d13a49a0c9ab1018
ms.sourcegitcommit: 645608f33d2d02625484c29586f42d21c442aaa9
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/18/2021
ms.locfileid: "127932510"
---
# <a name="tutorial-build-a-3d-piano-model"></a>Esercitazione: Creare un modello di piano 3D

Nell'esercitazione precedente della serie è stata impostata una pagina Web contenente una scena Babylon.js con una fotocamera e una luce. In questa esercitazione verrà compilata e aggiunta un modello di piano nella scena.

![Standup Piano Mesh](./images/standup-piano-mesh.png)

In questa esercitazione verranno illustrate le procedure per:

> [!div class="checklist"]
> * Creare, posizionare e unire mesh
> * Creare una tastiera per piano da mesh a scatola
> * Importare un modello 3D di una cornice del piano

## <a name="before-you-begin"></a>Prima di iniziare

Assicurarsi di aver seguito [l'esercitazione](introduction-01.md) precedente della serie e di essere pronti per continuare ad aggiungere al codice.

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

    const xrHelper = await scene.createDefaultXRExperienceAsync();

    return scene;
}
```

## <a name="getting-started"></a>Introduzione

Per iniziare, creare una semplice tastiera per piano con questa struttura:

![Descrizione registro piano](./images/piano-register.jpg)

In questa immagine sono presenti 7 tasti bianchi e 5 chiavi nere, ognuna etichettata con il nome della nota. Una tastiera completa con piano a 88 tasti contiene 7 ripetizioni complete di questa selezione di tasti (detta anche registro) e 4 tasti aggiuntivi. Ogni registro ha il doppio della frequenza del registro precedente. Ad esempio, la frequenza di tono di C5 (che significa la nota C nel quinto registro) è il doppio di C4, la frequenza del passo di D5 è il doppio di D4 e così via.

Visivamente, ogni registro ha esattamente lo stesso aspetto di un altro, quindi è possibile iniziare con l'analisi di come creare una semplice tastiera per piano con questa selezione di tasti. Successivamente, è possibile trovare un modo per espandere l'ambito a una tastiera con piano completo a 88 tasti.

## <a name="build-a-simple-piano-keyboard"></a>Creare una semplice tastiera per il piano

> [!NOTE]
> Anche se è possibile trovare modelli 3D predefiniti di tastiere per piano da origini online e importarli nella pagina Web, in questa esercitazione la tastiera verrà compilata da zero per consentire la massima personalizzazione e illustrare come creare modelli 3D tramite Babylon.js.

1. Prima di iniziare a creare mesh per la creazione della tastiera, si noti che ogni tasto nero non è perfettamente allineato al centro dei due tasti bianchi intorno e non tutti i tasti hanno la stessa larghezza. Ciò significa che è necessario creare e posizionare la mesh per ogni chiave singolarmente.

    ![Allineamento del tasto nero](./images/black-key-position.png)

1. Per i tasti bianchi, è possibile osservare che ogni tasto bianco è composto da due parti: (1) la parte inferiore sotto la chiave o le chiavi nere e (2) la parte superiore accanto alla chiave o alle chiavi nere. Le due parti hanno dimensioni diverse, ma sono impilate insieme per creare una chiave bianca completa.

    ![Forma Chiave bianca](./images/white-key-shape-label.png)

1. Di seguito è riportato il codice per la creazione di un singolo tasto bianco per la nota C (non preoccuparsi di aggiungerlo *scene.js* ancora):

    ```javascript
    const whiteKeyBottom = BABYLON.MeshBuilder.CreateBox("whiteKeyBottom", {width: 2.3, height: 1.5, depth: 4.5}, scene);
    const whiteKeyTop = BABYLON.MeshBuilder.CreateBox("whiteKeyTop", {width: 1.4, height: 1.5, depth: 5}, scene);
    whiteKeyTop.position.z += 4.75;
    whiteKeyTop.position.x -= 0.45;

    // Parameters of BABYLON.Mesh.MergeMeshes:
    // (arrayOfMeshes, disposeSource, allow32BitsIndices, meshSubclass, subdivideWithSubMeshes, multiMultiMaterials)
    const whiteKeyV1 = BABYLON.Mesh.MergeMeshes([whiteKeyBottom, whiteKeyTop], true, false, null, false, false);
    whiteKeyV1.material = whiteMat;
    whiteKeyV1.name = "C4";
    ```

    Qui sono state create due mesh [Box,](https://doc.babylonjs.com/divingDeeper/mesh/creation/set/box#box-mesh) una per la parte inferiore e una per la parte superiore della chiave bianca. Si modifica quindi la posizione della parte superiore per impilarla sopra la parte inferiore e spostarla verso sinistra per lasciare spazio per la chiave nera adiacente (C#).

    Infine, queste due parti sono state unite usando la [funzione MergeMeshes](https://doc.babylonjs.com/divingDeeper/mesh/mergeMeshes) per diventare un unico tasto bianco completo. Questa è la mesh risultante che questo codice produrrebbe:

    ![White Key C](./images/white-key-c.png)

1. La creazione di una chiave nera è più semplice. Poiché tutti i tasti neri hanno la forma di una scatola, è possibile creare una chiave nera semplicemente creando una mesh a forma di scatola con standardMaterial di colore [nero.](https://doc.babylonjs.com/divingDeeper/materials/using/materials_introduction#color)

    > [!NOTE]
    > Poiché il colore di mesh predefinito è grigio chiaro simile al bianco, questa esercitazione non include i passaggi per aggiungere un materiale di colore bianco ai tasti bianchi. Tuttavia, è possibile aggiungere il materiale manualmente se si desidera un vero colore bianco chiaro sui tasti bianchi.

    Ecco il codice per creare la chiave nera C# (non preoccuparsi di aggiungerlo *scene.js:*

    ```javascript
    const blackMat = new BABYLON.StandardMaterial("black");
    blackMat.diffuseColor = new BABYLON.Color3(0, 0, 0);

    const blackKey = BABYLON.MeshBuilder.CreateBox("C#4", {width: 1.4, height: 2, depth: 5}, scene);
    blackKey.position.z += 4.75;
    blackKey.position.y += 0.25;
    blackKey.position.x += 0.95;
    blackKey.material = blackMat;
    ```

    La chiave nera prodotta da questo codice (insieme al tasto bianco precedente) sarà simile alla seguente:

    ![Black Key C #](./images/black-key-csharp.png)

1. Come si può vedere, la creazione di ogni chiave può comportare una grande quantità di codice simile perché è necessario specificare ogni dimensione e posizione. Nella sezione successiva si proverà a rendere più efficiente il processo di creazione.

## <a name="build-a-simple-piano-keyboard-efficiently"></a>Creare una semplice tastiera per piano in modo efficiente

1. Anche se ogni tasto bianco ha una forma leggermente diversa l'una dall'altra, è possibile crearli tutti combinando una parte superiore e una parte inferiore. Implementare una funzione generica per creare e posizionare qualsiasi tasto bianco.

    Aggiungere la funzione seguente *per* scene.js, all'esterno della `createScene()` funzione :

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
    }
    ```

    In questo blocco di codice è stata creata una funzione denominata , che compila `buildKey()` e restituisce un tasto bianco se è `props.type` `"white"` . Identificando il tipo di chiave nel parametro , è possibile creare chiavi nere e chiavi di colore bianco nella stessa funzione diramando usando `props` un'istruzione if.

    I parametri di `buildKey()` sono:
    * **scene:** scena in cui si trova la chiave
    * **parent:** elemento padre della mesh (in questo modo è possibile raggruppare tutte le chiavi in un singolo elemento padre)
    * **props:** proprietà della chiave che verrà compilata

    `props`L'elemento per un tasto bianco conterrà gli elementi seguenti:
    * **tipo**: "white"
    * **name**: nome della nota che rappresenta la chiave
    * **topWidth:** larghezza della parte superiore
    * **bottomWidth:** larghezza della parte inferiore
    * **topPositionX:** posizione x della parte superiore rispetto alla parte inferiore
    * **wholePositionX:** posizione x dell'intera chiave rispetto al punto finale del registro (il bordo destro della chiave B).
    * **register:** registro a cui appartiene la chiave (un numero compreso tra 0 e 8)
    * **referencePositionX:** coordinata x del punto finale del registro (usato come punto di riferimento).

    Separando e , è possibile inizializzare i parametri necessari per creare un tipo specifico di chiave (ad esempio C) all'interno di qualsiasi registro e quindi aggiungere a e a durante la creazione di tale chiave in un registro specifico (ad esempio `wholePositionX` `referencePositionX` `props` `register` `referencePositionX` `props` C4, C5).

1. Analogamente, è anche possibile scrivere una funzione generica per creare una chiave nera. Espandere la funzione per `buildKey()` includere tale logica:

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
    ```

    `props`L'oggetto per un tasto nero contiene gli elementi seguenti:

    * **tipo**: "black"
    * **name**: nome della nota che rappresenta la chiave
    * **wholePositionX:** posizione x dell'intera chiave rispetto al punto finale del registro (bordo destro della chiave B)
    * **register:** registro a cui appartiene la chiave (un numero compreso tra 0 e 8)
    * **referencePositionX:** coordinata x del punto finale del registro (usato come punto di riferimento).

    L'oggetto per la creazione di una chiave nera è molto più semplice perché la creazione di una chiave nera implica solo la creazione di una casella e la larghezza e la posizione z di ogni chiave nera `props` sono uguali.

1. Ora che è disponibile un modo più efficiente per creare le chiavi, inizializzare una matrice che archivia per ogni tasto che corrisponde a una nota in un registro e quindi chiamare la funzione con ognuno di essi per creare una semplice tastiera nel `props` `buildKey()` 4° registro.

    Verrà anche creato un elemento [TransformNode](https://doc.babylonjs.com/divingDeeper/mesh/transforms/parent_pivot/transform_node#a-transformnode) denominato `keyboard` per fungere da [padre di tutte](https://doc.babylonjs.com/divingDeeper/mesh/transforms/parent_pivot/parent#overview-of-a-parent) le chiavi del piano. Poiché qualsiasi modifica di posizione o ridimensionamento applicata all'elemento padre verrebbe applicata anche agli elementi figlio, il raggruppamento delle chiavi in questo modo consentirà di ridimensionarle o spostarle nel loro complesso.

    Aggiungere le righe di codice seguenti nella `createScene()` funzione :

    ```javascript
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

    keyParams.forEach(key => {
        buildKey(scene, keyboard, Object.assign({register: 4, referencePositionX: 0}, key));
    })
    ```

    Come probabilmente si è notato, in questo blocco di codice vengono inserite tutte le chiavi relative all'origine dello spazio.

1. Di seguito è riportato il *codicescene.js* contenuto finora:

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
    
        // Transform Node that acts as the parent of all piano keys
        const keyboard = new BABYLON.TransformNode("keyboard");
    
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
    
        keyParams.forEach(key => {
            buildKey(scene, keyboard, Object.assign({register: 4, referencePositionX: 0}, key));
        })

        const xrHelper = await scene.createDefaultXRExperienceAsync();

        return scene;
    }
    ```

1. La tastiera risultante sarà simile alla seguente:

    ![Piano Keyboard with One Register](./images/piano-one-register.png)

## <a name="expanding-to-an-88-key-piano"></a>Espansione a un piano a 88 tasti

In questa sezione verrà espanso l'utilizzo delle funzioni di creazione dei tasti per generare una tastiera completa con piano a 88 tasti.

1. Come accennato in precedenza, una tastiera completa con piano a 88 tasti contiene 7 registri ripetuti e altre 4 note. 3 di queste note aggiuntive si trova nel registro 0 (estremità sinistra della tastiera) e 1 nel registro 8 (estremità destra della tastiera).

    ![Layout piano a 88 tasti](./images/88-key-piano-keyboard-layout.jpg)

1. Prima di tutto si lavora alla creazione delle 7 ripetizioni complete aggiungendo un ciclo aggiuntivo intorno al ciclo scritto in precedenza. Sostituire il ciclo precedente per la `buildKey()` funzione con il codice seguente:

    ```javascript
    // Register 1 through 7
    var referencePositionX = -2.4*14;
    for (let register = 1; register <= 7; register++) {
        keyParams.forEach(key => {
            buildKey(scene, keyboard, Object.assign({register: register, referencePositionX: referencePositionX}, key));
        })
        referencePositionX += 2.4*7;
    }
    ```

    In questo ciclo si compilano le chiavi per il registro da 1 a 7 e si incrementa la posizione di riferimento ogni volta che si passa al registro successivo.

1. Successivamente, si creerà il resto delle chiavi. Aggiungere il frammento di codice seguente alla `createScene()` funzione :

    ```javascript
    // Register 0
    buildKey(scene, keyboard, {type: "white", note: "A", topWidth: 1.9, bottomWidth: 2.3, topPositionX: -0.20, wholePositionX: -2.4, register: 0, referencePositionX: -2.4*21});
    keyParams.slice(10, 12).forEach(key => {
        buildKey(scene, keyboard, Object.assign({register: 0, referencePositionX: -2.4*21}, key));
    })

    // Register 8
    buildKey(scene, keyboard, {type: "white", note: "C", topWidth: 2.3, bottomWidth: 2.3, topPositionX: 0, wholePositionX: -2.4*6, register: 8, referencePositionX: 84});
    ```

    Si noti che il tasto più a sinistra e il tasto più a destra della tastiera del piano non rientrano nelle dimensioni delle proprietà definite in (perché non sono accanto a un tasto nero sul bordo), quindi è necessario definire un nuovo oggetto per ognuna di esse per specificare la forma `keyParams` `props` speciale.

1. Dopo aver apportato le modifiche, la tastiera prodotta dovrebbe essere simile alla seguente:

    ![Mesh tastiera piano completo](./images/full-keyboard-mesh.png)

## <a name="adding-a-piano-frame"></a>Aggiunta di una cornice per il piano

1. La scena ha un aspetto leggermente strano con una tastiera mobile nello spazio. Aggiungere un fotogramma del piano intorno alla tastiera per creare l'aspetto di un piano di supporto.

1. Analogamente a come sono state create le chiavi, è anche possibile creare il frame posizionando e combinando un gruppo di mesh di box.

    Tuttavia, questa sfida verrà data all'utente per provare da sola e usare [BABYLON. SceneLoader.ImportMesh](https://doc.babylonjs.com/divingDeeper/importers/loadingFileTypes#sceneloaderimportmesh) per importare una mesh pre-creata di una cornice di piano di supporto. Aggiungere questa parte di codice a `createScene()` :

    ```javascript
    // Transform node that acts as the parent of all piano components
    const piano = new BABYLON.TransformNode("piano");
    keyboard.parent = piano;

    // Import and scale piano frame
    BABYLON.SceneLoader.ImportMesh("frame", "https://docs.microsoft.com/windows/mixed-reality/develop/javascript/tutorials/babylonjs-webxr-piano/files", "pianoFrame.babylon", scene, function(meshes) {
        const frame = meshes[0];
        frame.parent = piano;
    });
    ```

    Si noti che, anche in questo caso, viene creato un elemento padre denominato per raggruppare la tastiera e `TransformNode` il frame nel suo `piano` complesso. In questo modo sarà molto più semplice spostare o ridimensionare l'intero piano, se necessario.

1. Dopo l'importazione del frame, si noti che la tastiera si trova nella parte inferiore del fotogramma (poiché le coordinate y dei tasti sono su 0 per impostazione predefinita). È possibile alzare la tastiera in modo che si adatti alla cornice del piano di supporto:

    ```javascript
    // Lift piano keys
    keyboard.position.y += 80;
    ```

    Poiché è l'elemento padre di tutti i tasti del piano, è possibile elevare tutti i tasti del piano modificando semplicemente `keyboard` la posizione y di `keyboard` .

1. Il codice finale della *scene.js* dovrebbe essere simile al seguente:

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

1. Ora si dovrebbe avere un piano di supporto simile al seguente: ![ Standup Piano Mesh](./images/standup-piano-mesh.png)

## <a name="next-steps"></a>Passaggi successivi

> [!div class="nextstepaction"]
> [Esercitazione successiva: Riprodurre il piano 3D](keyboard-interaction-03.md)

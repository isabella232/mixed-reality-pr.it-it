---
title: Introduzione alle esercitazioni babylon.js e WebXR
description: Completare questo corso per apprendere come usare babylon.js e creare un'applicazione di base per realtà mista.
author: bogenera
ms.author: ayyonet
ms.date: 03/05/2021
ms.topic: article
keywords: realtà mista, JavaScript, esercitazione, BabylonJS, hololens, realtà mista, UWP, Windows 10, WebXR, Web immersiva
ms.localizationpriority: high
ms.openlocfilehash: 945d27d13ac731447bd20e93805900605bc86f43
ms.sourcegitcommit: cbfd1c37612aa6904fa41642ede6281d491e478d
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/23/2021
ms.locfileid: "104946434"
---
# <a name="tutorial-create-your-first-webxr-application-using-babylonjs"></a><span data-ttu-id="e1093-104">Esercitazione: creare la prima applicazione WebXR usando babylon.js</span><span class="sxs-lookup"><span data-stu-id="e1093-104">Tutorial: Create your first WebXR application using babylon.js</span></span>

<span data-ttu-id="e1093-105">Questa esercitazione illustra come creare un'app di base per la realtà mista usando babylon.js e Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="e1093-105">This tutorial will show you how to create a basic Mixed Reality app using babylon.js and Visual Studio Code.</span></span> <span data-ttu-id="e1093-106">L'app che verrà compilata compilerà il rendering di un cubo, ne consentirà la rotazione per portare gli altri visi in visualizzazione e aggiungere interazioni.</span><span class="sxs-lookup"><span data-stu-id="e1093-106">The app you're going to build will render a cube, let you rotate it to bring the other faces into view, and add interactions.</span></span> <span data-ttu-id="e1093-107">In questa esercitazione verranno illustrate le procedure per:</span><span class="sxs-lookup"><span data-stu-id="e1093-107">In this tutorial, you learn how to:</span></span>

> [!div class="checklist"]
> * <span data-ttu-id="e1093-108">Configurare un ambiente di sviluppo</span><span class="sxs-lookup"><span data-stu-id="e1093-108">Set up a development environment</span></span>
> * <span data-ttu-id="e1093-109">API babylon.js per creare elementi 3D di base</span><span class="sxs-lookup"><span data-stu-id="e1093-109">The babylon.js API to create basic 3D elements</span></span>  
> * <span data-ttu-id="e1093-110">Crea una nuova pagina Web</span><span class="sxs-lookup"><span data-stu-id="e1093-110">Create a new web page</span></span>
> * <span data-ttu-id="e1093-111">Interagire con gli elementi 3D</span><span class="sxs-lookup"><span data-stu-id="e1093-111">Interact with 3D elements</span></span>
> * <span data-ttu-id="e1093-112">Eseguire l'applicazione in un simulatore di realtà mista di Windows</span><span class="sxs-lookup"><span data-stu-id="e1093-112">Run the application in a Windows Mixed Reality Simulator</span></span>

## <a name="prerequisites"></a><span data-ttu-id="e1093-113">Prerequisiti</span><span class="sxs-lookup"><span data-stu-id="e1093-113">Prerequisites</span></span>

* <span data-ttu-id="e1093-114">Browser supportato da WebXR, ad esempio [Microsoft Edge](https://docs.microsoft.com/windows/mixed-reality/whats-new/new-microsoft-edge)</span><span class="sxs-lookup"><span data-stu-id="e1093-114">WebXR-supported browser, for example [Microsoft Edge](https://docs.microsoft.com/windows/mixed-reality/whats-new/new-microsoft-edge)</span></span>
* <span data-ttu-id="e1093-115">[Babylon.js](https://doc.babylonjs.com/divingDeeper/developWithBjs/frameworkVers) 4,2 o versione successiva</span><span class="sxs-lookup"><span data-stu-id="e1093-115">[Babylon.js](https://doc.babylonjs.com/divingDeeper/developWithBjs/frameworkVers) 4.2 or higher</span></span>
* [<span data-ttu-id="e1093-116">NodeJS</span><span class="sxs-lookup"><span data-stu-id="e1093-116">NodeJS</span></span>](https://nodejs.org/)
* <span data-ttu-id="e1093-117">Facoltativo: [Windows 10 Creator Update](https://www.microsoft.com/software-download/windows10) se si vuole usare un simulatore di realtà mista di Windows</span><span class="sxs-lookup"><span data-stu-id="e1093-117">Optional: [Windows 10 Creator Update](https://www.microsoft.com/software-download/windows10) if you want to use a Windows Mixed Reality Simulator</span></span>
* <span data-ttu-id="e1093-118">Facoltativo: [simulatore di realtà mista di Windows](https://docs.microsoft.com/windows/mixed-reality/develop/platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator)</span><span class="sxs-lookup"><span data-stu-id="e1093-118">Optional: [Windows Mixed Reality simulator](https://docs.microsoft.com/windows/mixed-reality/develop/platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator)</span></span>

## <a name="getting-started"></a><span data-ttu-id="e1093-119">Introduzione</span><span class="sxs-lookup"><span data-stu-id="e1093-119">Getting started</span></span>

<span data-ttu-id="e1093-120">Per creare il progetto da zero, iniziare con un progetto Visual Studio Code (VSCode).</span><span class="sxs-lookup"><span data-stu-id="e1093-120">To create this project from scratch, start with a Visual Studio Code (VSCode) project.</span></span>

> [!NOTE]
> <span data-ttu-id="e1093-121">L'uso di VSCode non è obbligatorio, ma verrà usato per praticità nell'esercitazione.</span><span class="sxs-lookup"><span data-stu-id="e1093-121">Using VSCode isn't mandatory, but we'll be using it for convenience throughout the tutorial.</span></span> <span data-ttu-id="e1093-122">Gli sviluppatori JavaScript più esperti possono utilizzare qualsiasi altro editor di propria scelta, anche il blocco note più semplice.</span><span class="sxs-lookup"><span data-stu-id="e1093-122">More experienced JavaScript developers can use any other editor of their choice, even the simplest Notepad.</span></span>

1. <span data-ttu-id="e1093-123">Scaricare il [babylon.js](https://doc.babylonjs.com/divingDeeper/developWithBjs/frameworkVers) singolo file o utilizzare una versione online disponibile nel [sito web ufficiale babylon.js](https://doc.babylonjs.com/divingDeeper/developWithBjs/frameworkVers).</span><span class="sxs-lookup"><span data-stu-id="e1093-123">Either download the [babylon.js](https://doc.babylonjs.com/divingDeeper/developWithBjs/frameworkVers) single file or use an online version that can be found on the [official babylon.js web site](https://doc.babylonjs.com/divingDeeper/developWithBjs/frameworkVers).</span></span> <span data-ttu-id="e1093-124">È anche possibile clonare l'intero progetto di babylon.js da [GitHub](https://github.com/BabylonJS/Babylon.js)</span><span class="sxs-lookup"><span data-stu-id="e1093-124">You can also clone the entire babylon.js project from [GitHub](https://github.com/BabylonJS/Babylon.js)</span></span>
1. <span data-ttu-id="e1093-125">Creare un file vuoto e salvarlo come pagina HTML, ad esempio index.html</span><span class="sxs-lookup"><span data-stu-id="e1093-125">Create an empty file and save it as html page, for example index.html</span></span>
1. <span data-ttu-id="e1093-126">Creare un markup HTML di base e fare riferimento al file babylon.js JavaScript.</span><span class="sxs-lookup"><span data-stu-id="e1093-126">Create a basic html markup and reference the babylon.js javascript file.</span></span> <span data-ttu-id="e1093-127">Il codice finale è illustrato di seguito:</span><span class="sxs-lookup"><span data-stu-id="e1093-127">The final code is as shown below:</span></span>

    ```html
    <html>
        <head>
            <title>Babylon.js sample code</title>
            <script src="https://cdn.babylonjs.com/babylon.js"></script>
        </head>
    <body>
    </body>
    </html>
    ```

1. <span data-ttu-id="e1093-128">Aggiungere un elemento HTML *Canvas* all'interno del corpo per eseguire il rendering del contenuto di babylon.js.</span><span class="sxs-lookup"><span data-stu-id="e1093-128">Add a *canvas* HTML element inside the body to render the contents of babylon.js.</span></span> <span data-ttu-id="e1093-129">Si noti che l'area di disegno ha un attributo ID, che consente di accedere a questo elemento HTML da JavaScript in un secondo momento.</span><span class="sxs-lookup"><span data-stu-id="e1093-129">Note that the canvas has an id attribute, which lets you access this HTML element from JavaScript later on.</span></span>

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

1. <span data-ttu-id="e1093-130">L'area di disegno occupa l'intera pagina Web.</span><span class="sxs-lookup"><span data-stu-id="e1093-130">The canvas occupies the entire web page.</span></span> <span data-ttu-id="e1093-131">La pagina Web è stata completata.</span><span class="sxs-lookup"><span data-stu-id="e1093-131">That completes our web page.</span></span> <span data-ttu-id="e1093-132">A questo punto, la pagina Web è pronta.</span><span class="sxs-lookup"><span data-stu-id="e1093-132">At this point, the web page is ready.</span></span> <span data-ttu-id="e1093-133">È possibile aprirlo in qualsiasi browser e assicurarsi che non vengano visualizzati errori, anche se non esiste ancora un'esperienza immersiva.</span><span class="sxs-lookup"><span data-stu-id="e1093-133">You can open it in any browser and ensure there are no errors shown, though there is no immersive experience yet.</span></span>

## <a name="next-steps"></a><span data-ttu-id="e1093-134">Passaggi successivi</span><span class="sxs-lookup"><span data-stu-id="e1093-134">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="e1093-135">Esercitazione successiva: 2. preparare una scena</span><span class="sxs-lookup"><span data-stu-id="e1093-135">Next Tutorial: 2. Prepare a scene</span></span>](prepare-scene-02.md)

---
title: Introduzione alle esercitazioni babylon.js e WebXR
description: Completare questo corso per informazioni su come usare babylon.js e creare un'applicazione di realtà mista di base.
author: bogenera
ms.author: ayyonet
ms.date: 03/05/2021
ms.topic: article
keywords: realtà mista, javascript, esercitazione, BabylonJS, hololens, realtà mista, UWP, Windows 10, WebXR, web immersivo
ms.localizationpriority: high
ms.openlocfilehash: 2d3f59b2769f99a756c4f0c10df1d8a8604a595e
ms.sourcegitcommit: 9ae76b339968f035c703d9c1fe57ddecb33198e3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/27/2021
ms.locfileid: "110600120"
---
# <a name="tutorial-create-your-first-webxr-application-using-babylonjs"></a><span data-ttu-id="79895-104">Esercitazione: Creare la prima applicazione WebXR usando babylon.js</span><span class="sxs-lookup"><span data-stu-id="79895-104">Tutorial: Create your first WebXR application using babylon.js</span></span>

<span data-ttu-id="79895-105">Questa esercitazione illustra come creare un'app di realtà mista di base usando babylon.js e Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="79895-105">This tutorial will show you how to create a basic Mixed Reality app using babylon.js and Visual Studio Code.</span></span> <span data-ttu-id="79895-106">L'app che si sta per compilare eseguirà il rendering di un cubo, consente di ruotarlo per visualizzare gli altri visi e aggiungere interazioni.</span><span class="sxs-lookup"><span data-stu-id="79895-106">The app you're going to build will render a cube, let you rotate it to bring the other faces into view, and add interactions.</span></span> <span data-ttu-id="79895-107">In questa esercitazione verranno illustrate le procedure per:</span><span class="sxs-lookup"><span data-stu-id="79895-107">In this tutorial, you learn how to:</span></span>

> [!div class="checklist"]
> * <span data-ttu-id="79895-108">Configurare un ambiente di sviluppo</span><span class="sxs-lookup"><span data-stu-id="79895-108">Set up a development environment</span></span>
> * <span data-ttu-id="79895-109">Api babylon.js per creare elementi 3D di base</span><span class="sxs-lookup"><span data-stu-id="79895-109">The babylon.js API to create basic 3D elements</span></span>  
> * <span data-ttu-id="79895-110">Creare una nuova pagina Web</span><span class="sxs-lookup"><span data-stu-id="79895-110">Create a new web page</span></span>
> * <span data-ttu-id="79895-111">Interagire con gli elementi 3D</span><span class="sxs-lookup"><span data-stu-id="79895-111">Interact with 3D elements</span></span>
> * <span data-ttu-id="79895-112">Eseguire l'applicazione in un simulatore di Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="79895-112">Run the application in a Windows Mixed Reality Simulator</span></span>

## <a name="prerequisites"></a><span data-ttu-id="79895-113">Prerequisiti</span><span class="sxs-lookup"><span data-stu-id="79895-113">Prerequisites</span></span>

* <span data-ttu-id="79895-114">Browser supportato da WebXR, ad [esempio](../../../../whats-new/new-microsoft-edge.md) Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="79895-114">WebXR-supported browser, for example [Microsoft Edge](../../../../whats-new/new-microsoft-edge.md)</span></span>
* <span data-ttu-id="79895-115">[Babylon.js](https://doc.babylonjs.com/divingDeeper/developWithBjs/frameworkVers) 4.2 o versione successiva</span><span class="sxs-lookup"><span data-stu-id="79895-115">[Babylon.js](https://doc.babylonjs.com/divingDeeper/developWithBjs/frameworkVers) 4.2 or higher</span></span>
* [<span data-ttu-id="79895-116">NodeJS</span><span class="sxs-lookup"><span data-stu-id="79895-116">NodeJS</span></span>](https://nodejs.org/)
* <span data-ttu-id="79895-117">Facoltativo: [Windows 10 Creator Update](https://www.microsoft.com/software-download/windows10) se si vuole usare un simulatore di Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="79895-117">Optional: [Windows 10 Creator Update](https://www.microsoft.com/software-download/windows10) if you want to use a Windows Mixed Reality Simulator</span></span>
* <span data-ttu-id="79895-118">Facoltativo: [Windows Mixed Reality simulatore](../../../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md)</span><span class="sxs-lookup"><span data-stu-id="79895-118">Optional: [Windows Mixed Reality simulator](../../../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md)</span></span>

## <a name="getting-started"></a><span data-ttu-id="79895-119">Guida introduttiva</span><span class="sxs-lookup"><span data-stu-id="79895-119">Getting started</span></span>

<span data-ttu-id="79895-120">Per creare questo progetto da zero, iniziare con un progetto Visual Studio Code (VSCode).</span><span class="sxs-lookup"><span data-stu-id="79895-120">To create this project from scratch, start with a Visual Studio Code (VSCode) project.</span></span>

> [!NOTE]
> <span data-ttu-id="79895-121">L'uso di VSCode non è obbligatorio, ma verrà utilizzato per praticità durante l'esercitazione.</span><span class="sxs-lookup"><span data-stu-id="79895-121">Using VSCode isn't mandatory, but we'll be using it for convenience throughout the tutorial.</span></span> <span data-ttu-id="79895-122">Gli sviluppatori JavaScript più esperti possono usare qualsiasi altro editor di propria scelta, anche il Blocco note più semplice.</span><span class="sxs-lookup"><span data-stu-id="79895-122">More experienced JavaScript developers can use any other editor of their choice, even the simplest Notepad.</span></span>

1. <span data-ttu-id="79895-123">Scaricare il [babylon.js](https://doc.babylonjs.com/divingDeeper/developWithBjs/frameworkVers) file singolo o usare una versione online disponibile nel sito [Web ufficiale babylon.js](https://doc.babylonjs.com/divingDeeper/developWithBjs/frameworkVers).</span><span class="sxs-lookup"><span data-stu-id="79895-123">Either download the [babylon.js](https://doc.babylonjs.com/divingDeeper/developWithBjs/frameworkVers) single file or use an online version that can be found on the [official babylon.js web site](https://doc.babylonjs.com/divingDeeper/developWithBjs/frameworkVers).</span></span> <span data-ttu-id="79895-124">È anche possibile clonare l'intero babylon.js progetto da [GitHub](https://github.com/BabylonJS/Babylon.js)</span><span class="sxs-lookup"><span data-stu-id="79895-124">You can also clone the entire babylon.js project from [GitHub](https://github.com/BabylonJS/Babylon.js)</span></span>
1. <span data-ttu-id="79895-125">Creare un file vuoto e salvarlo come pagina HTML, ad esempio index.html</span><span class="sxs-lookup"><span data-stu-id="79895-125">Create an empty file and save it as html page, for example index.html</span></span>
1. <span data-ttu-id="79895-126">Creare un markup HTML di base e fare riferimento al babylon.js javascript.</span><span class="sxs-lookup"><span data-stu-id="79895-126">Create a basic html markup and reference the babylon.js javascript file.</span></span> <span data-ttu-id="79895-127">Il codice finale è come illustrato di seguito:</span><span class="sxs-lookup"><span data-stu-id="79895-127">The final code is as shown below:</span></span>

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

1. <span data-ttu-id="79895-128">Aggiungere un elemento HTML *canvas* all'interno del corpo per eseguire il rendering del contenuto babylon.js.</span><span class="sxs-lookup"><span data-stu-id="79895-128">Add a *canvas* HTML element inside the body to render the contents of babylon.js.</span></span> <span data-ttu-id="79895-129">Si noti che l'area di disegno ha un attributo id, che consente di accedere a questo elemento HTML da JavaScript in un secondo momento.</span><span class="sxs-lookup"><span data-stu-id="79895-129">Note that the canvas has an id attribute, which lets you access this HTML element from JavaScript later on.</span></span>

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

1. <span data-ttu-id="79895-130">L'area di disegno occupa l'intera pagina Web.</span><span class="sxs-lookup"><span data-stu-id="79895-130">The canvas occupies the entire web page.</span></span> <span data-ttu-id="79895-131">Questa operazione completa la pagina Web.</span><span class="sxs-lookup"><span data-stu-id="79895-131">That completes our web page.</span></span> <span data-ttu-id="79895-132">A questo punto, la pagina Web è pronta.</span><span class="sxs-lookup"><span data-stu-id="79895-132">At this point, the web page is ready.</span></span> <span data-ttu-id="79895-133">È possibile aprirlo in qualsiasi browser e assicurarsi che non siano visualizzati errori, anche se non è ancora presente alcuna esperienza immersiva.</span><span class="sxs-lookup"><span data-stu-id="79895-133">You can open it in any browser and ensure there are no errors shown, though there is no immersive experience yet.</span></span>

## <a name="next-steps"></a><span data-ttu-id="79895-134">Passaggi successivi</span><span class="sxs-lookup"><span data-stu-id="79895-134">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="79895-135">Esercitazione successiva: 2. Preparare una scena</span><span class="sxs-lookup"><span data-stu-id="79895-135">Next Tutorial: 2. Prepare a scene</span></span>](prepare-scene-02.md)
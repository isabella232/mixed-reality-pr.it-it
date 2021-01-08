---
title: Prestazioni di OpenXR
description: Informazioni su come eseguire il debug delle prestazioni GPU delle applicazioni di realtà mista OpenXR.
author: thetuvix
ms.author: alexturn
ms.date: 2/28/2020
ms.topic: article
keywords: OpenXR, Khronos, BasicXRApp, DirectX, nativo, app nativa, motore personalizzato, middleware, prestazioni, ottimizzazione, debug GPU, RenderDoc, PIX
ms.openlocfilehash: 158bd2eef8f38f16a1fb5299d64335aca33a3b7f
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2021
ms.locfileid: "98006761"
---
# <a name="openxr-performance"></a><span data-ttu-id="22dc1-104">Prestazioni di OpenXR</span><span class="sxs-lookup"><span data-stu-id="22dc1-104">OpenXR performance</span></span>

<span data-ttu-id="22dc1-105">In HoloLens 2 sono disponibili diversi modi per inviare i dati di composizione tramite, il che può comportare un `xrEndFrame` conseguente calo delle prestazioni in fase di post-elaborazione.</span><span class="sxs-lookup"><span data-stu-id="22dc1-105">On HoloLens 2, there are a number of ways to submit composition data through `xrEndFrame`, which can result in post-processing and noticeable performance penalties.</span></span>

<span data-ttu-id="22dc1-106">Per evitare una riduzione delle prestazioni, [inviare `XrCompositionProjectionLayer` un singolo](openxr-best-practices.md#use-a-single-projection-layer) con le caratteristiche seguenti:</span><span class="sxs-lookup"><span data-stu-id="22dc1-106">To avoid poor performance, [submit a single `XrCompositionProjectionLayer`](openxr-best-practices.md#use-a-single-projection-layer) with the following characteristics:</span></span>

* [<span data-ttu-id="22dc1-107">Usare una matrice di trama presentazione catena</span><span class="sxs-lookup"><span data-stu-id="22dc1-107">Use a texture array swapchain</span></span>](openxr-best-practices.md#render-with-texture-array-and-vprt)
* [<span data-ttu-id="22dc1-108">Usa il formato presentazione catena del colore primario</span><span class="sxs-lookup"><span data-stu-id="22dc1-108">Use the primary color swapchain format</span></span>](openxr-best-practices.md#select-a-swapchain-format)
* [<span data-ttu-id="22dc1-109">Usare le dimensioni di visualizzazione consigliate</span><span class="sxs-lookup"><span data-stu-id="22dc1-109">Use the recommended view dimensions</span></span>](openxr-best-practices.md#render-with-recommended-rendering-parameters-and-frame-timing)
* <span data-ttu-id="22dc1-110">Non impostare il `XR_COMPOSITION_LAYER_UNPREMULTIPLIED_ALPHA_BIT` flag</span><span class="sxs-lookup"><span data-stu-id="22dc1-110">Don't set the `XR_COMPOSITION_LAYER_UNPREMULTIPLIED_ALPHA_BIT` flag</span></span>
* <span data-ttu-id="22dc1-111">Impostare `XrCompositionLayerDepthInfoKHR` `minDepth` su 0,0 f e `maxDepth` su 1,0 f</span><span class="sxs-lookup"><span data-stu-id="22dc1-111">Set the `XrCompositionLayerDepthInfoKHR` `minDepth` to 0.0f and `maxDepth` to 1.0f</span></span>

<span data-ttu-id="22dc1-112">Per ottenere prestazioni ottimali, prendere in considerazione quanto segue:</span><span class="sxs-lookup"><span data-stu-id="22dc1-112">For better performance, consider:</span></span>

* [<span data-ttu-id="22dc1-113">Uso del formato Depth a 16 bit</span><span class="sxs-lookup"><span data-stu-id="22dc1-113">Using the 16-bit depth format</span></span>](openxr-best-practices.md#choose-a-reasonable-depth-range)
* [<span data-ttu-id="22dc1-114">Esecuzione di chiamate di disegni ad istanza</span><span class="sxs-lookup"><span data-stu-id="22dc1-114">Making instanced draw calls</span></span>](openxr-best-practices.md#render-with-texture-array-and-vprt)

---
title: Prestazioni di OpenXR
description: Eseguire il debug delle prestazioni GPU delle applicazioni OpenXR.
author: thetuvix
ms.author: alexturn
ms.date: 2/28/2020
ms.topic: article
keywords: OpenXR, Khronos, BasicXRApp, DirectX, nativo, app nativa, motore personalizzato, middleware, prestazioni, ottimizzazione, debug GPU, RenderDoc, PIX
ms.openlocfilehash: 7199b29067094d402348f00a9d26b93cf7e5393e
ms.sourcegitcommit: 2bf79eef6a9b845494484f458443ef4f89d7efc0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/17/2020
ms.locfileid: "97613175"
---
# <a name="openxr-performance"></a>Prestazioni di OpenXR

In HoloLens 2 sono disponibili diversi modi per inviare i dati di composizione tramite, il che può comportare un `xrEndFrame` conseguente calo delle prestazioni in fase di post-elaborazione.
Per evitare una riduzione delle prestazioni, [inviare `XrCompositionProjectionLayer` un singolo](openxr-best-practices.md#use-a-single-projection-layer) con le caratteristiche seguenti:
* [Usare una matrice di trama presentazione catena](openxr-best-practices.md#render-with-texture-array-and-vprt)
* [Usa il formato presentazione catena del colore primario](openxr-best-practices.md#select-a-swapchain-format)
* [Usare le dimensioni di visualizzazione consigliate](openxr-best-practices.md#render-with-recommended-rendering-parameters-and-frame-timing)
* Non impostare il `XR_COMPOSITION_LAYER_UNPREMULTIPLIED_ALPHA_BIT` flag
* Impostare `XrCompositionLayerDepthInfoKHR` `minDepth` su 0,0 f e `maxDepth` su 1,0 f

Per ottenere prestazioni ottimali, prendere in considerazione quanto segue:
* [Uso del formato Depth a 16 bit](openxr-best-practices.md#choose-a-reasonable-depth-range)
* [Esecuzione di chiamate di disegni ad istanza](openxr-best-practices.md#render-with-texture-array-and-vprt)

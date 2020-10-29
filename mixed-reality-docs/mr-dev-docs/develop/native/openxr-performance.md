---
title: Prestazioni di OpenXR
description: Eseguire il debug delle prestazioni GPU delle applicazioni OpenXR.
author: thetuvix
ms.author: alexturn
ms.date: 2/28/2020
ms.topic: article
keywords: OpenXR, Khronos, BasicXRApp, DirectX, nativo, app nativa, motore personalizzato, middleware, prestazioni, ottimizzazione, debug GPU, RenderDoc, PIX
ms.openlocfilehash: 717dc2d534773bd28f5ad2d5c3720bf4177a1480
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/03/2020
ms.locfileid: "91683829"
---
# <a name="openxr-performance"></a>Prestazioni di OpenXR

In HoloLens 2 sono disponibili diversi modi per inviare i dati di composizione tramite che comporteranno `xrEndFrame` una successiva elaborazione che avrà una notevole riduzione delle prestazioni.
Per evitare la penalizzazione delle prestazioni, [inviare `XrCompositionProjectionLayer` un singolo](openxr-best-practices.md#use-a-single-projection-layer) con le seguenti caratteristiche:
* [Usare una matrice di trama presentazione catena](openxr-best-practices.md#render-with-texture-array-and-vprt)
* [Usa il formato presentazione catena del colore primario](openxr-best-practices.md#select-a-swapchain-format)
* [Usare le dimensioni di visualizzazione consigliate](openxr-best-practices.md#render-with-recommended-rendering-parameters-and-frame-timing)
* Non impostare il `XR_COMPOSITION_LAYER_UNPREMULTIPLIED_ALPHA_BIT` flag
* Impostare `XrCompositionLayerDepthInfoKHR` `minDepth` su 0,0 f e `maxDepth` su 1,0 f

Ulteriori considerazioni comporteranno prestazioni migliori:
* [Usare il formato di profondità a 16 bit](openxr-best-practices.md#choose-a-reasonable-depth-range)
* [Eseguire chiamate di disegni ad istanza](openxr-best-practices.md#render-with-texture-array-and-vprt)

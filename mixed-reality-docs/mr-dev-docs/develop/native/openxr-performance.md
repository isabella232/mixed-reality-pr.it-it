---
title: Prestazioni di OpenXR
description: Informazioni su come eseguire il debug delle prestazioni GPU delle applicazioni openXR di realtà mista.
author: thetuvix
ms.author: alexturn
ms.date: 2/28/2020
ms.topic: article
keywords: OpenXR, Khronos, BasicXRApp, DirectX, native, native app, motore personalizzato, middleware, prestazioni, ottimizzazione, debug GPU, RenderDoc, PIX
ms.openlocfilehash: f4462da954a3b6093e47f03e75b460671e7638f406b761ad6e05689ab97b3ddc
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115213175"
---
# <a name="openxr-performance"></a>Prestazioni di OpenXR

In HoloLens 2, esistono diversi modi per inviare i dati di composizione tramite , che possono comportare una post-elaborazione e una notevole riduzione `xrEndFrame` delle prestazioni.

Per evitare prestazioni scarse, [inviare un singolo con `XrCompositionProjectionLayer` ](openxr-best-practices.md#use-a-single-projection-layer) le caratteristiche seguenti:

* [Usare uno swapchain della matrice di trame](openxr-best-practices.md#render-with-texture-array-and-vprt)
* [Usare il formato swapchain di colore primario](openxr-best-practices.md#select-a-swapchain-format)
* [Usare le dimensioni di visualizzazione consigliate](openxr-best-practices.md#render-with-recommended-rendering-parameters-and-frame-timing)
* Non impostare il `XR_COMPOSITION_LAYER_UNPREMULTIPLIED_ALPHA_BIT` flag
* Impostare su `XrCompositionLayerDepthInfoKHR` `minDepth` 0.0f e `maxDepth` su 1.0f

Per prestazioni migliori, prendere in considerazione:

* [Uso del formato di profondità a 16 bit](openxr-best-practices.md#choose-a-reasonable-depth-range)
* [Esecuzione di chiamate di disegno con istanze](openxr-best-practices.md#render-with-texture-array-and-vprt)

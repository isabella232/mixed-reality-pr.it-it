---
title: PulseShader
description: descrizione degli shader Pulse in MRTK.
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: 6a8979b42af9ce8e12875c8bd24ecc4fdc20df46650192fceb8b7a25707571ac
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115197033"
---
# <a name="pulse-shader"></a>Pulse shader

![MRTK_SpatialMesh_Pulse](https://user-images.githubusercontent.com/13754172/68261851-3489e200-fff6-11e9-9f6c-5574a7dd8db7.gif)

![MRTK_HandMesh_Pulse2 usare lo shader pulse per animare un effetto di impulso visivo sulla ricostruzione della superficie, sulla mesh della mano articolata ](https://user-images.githubusercontent.com/13754172/68262035-e4f7e600-fff6-11e9-9858-796afd1cabc5.gif) o su qualsiasi altra mesh.

## <a name="shader-and-material"></a>Shader e materiale

**MRTK_SurfaceReconstruction.mat** **e MRTK_ArticulatedHandMeshPulse.mat** **usa** SR_Triangles shader. È possibile configurare varie opzioni, ad esempio il colore di riempimento, il colore della linea e il colore dell'impulso.

## <a name="example-scene"></a>Scena di esempio

Aprire la scena **PulseShaderExamples.unity** e osservare l'effetto pulsante sulle sfera, la ricostruzione della superficie e la mesh articolata della mano.

Usare lo script SurfacePulse.cs per animare l'effetto di impulso sul materiale assegnato o attivare "Pulsazione automatica" nel materiale stesso.

## <a name="prerequisites"></a>Prerequisiti

Per la ricostruzione della superficie, assicurarsi che MRTK_SurfaceReconstruction.mat sia assegnato in MRTK Impostazioni -> Spatial Awareness -> Display Impostazioni -> Visible Material.

Per la mano articolata, assicurarsi che MRTK_ArticulatedHandMeshPulse.mat sia assegnato in ArticulatedHandMesh.prefab, che deve essere assegnato in MRTK Impostazioni -> Input -> Hand Tracking -> Hand Mesh Prefab.

## <a name="how-it-works"></a>Funzionamento

Lo shader hand mesh usa gli UV per mappare l'impulso lungo la mesh della mano e per sfumare il polso. Lo shader di ricostruzione della superficie usa le posizioni dei vertici per eseguire il mapping dell'impulso.

---
title: README_PulseShader
description: Descrizione su Pulse shader in MRTK.
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: 582c51c8ff57d5c8a9d835f508a8c277a480c527
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2021
ms.locfileid: "104689491"
---
# <a name="pulse-shader"></a>Pulse shader

![MRTK_SpatialMesh_Pulse](https://user-images.githubusercontent.com/13754172/68261851-3489e200-fff6-11e9-9f6c-5574a7dd8db7.gif)

![MRTK_HandMesh_Pulse2 ](https://user-images.githubusercontent.com/13754172/68262035-e4f7e600-fff6-11e9-9858-796afd1cabc5.gif) usare Pulse shader per animare un effetto di impulso visivo sulla ricostruzione della superficie, sulla mesh a mano articolata o su qualsiasi altra mesh.

## <a name="shader-and-material"></a>Shader e materiale

**MRTK_SurfaceReconstruction. Mat** e **MRTK_ArticulatedHandMeshPulse. Mat** utilizzano **SR_Triangles** shader. È possibile configurare diverse opzioni, ad esempio colore riempimento, colore linea e colore Pulse.

## <a name="example-scene"></a>Scena di esempio

Aprire la scena **PulseShaderExamples. Unity** e osservare l'effetto pulsato sulle sfere, sulla ricostruzione della superficie e sulla mesh a mano articolata.

Usare lo script SurfacePulse. cs per animare l'effetto di impulso sul materiale assegnato oppure attivare "Pulse automatico" nel materiale stesso.

## <a name="prerequisites"></a>Prerequisiti

Per la ricostruzione della superficie, assicurarsi che MRTK_SurfaceReconstruction. Mat sia assegnato in impostazioni di MRTK-> riconoscimento spaziale-> impostazioni di visualizzazione-> materiale visibile.

Per la mano articolata, assicurarsi che MRTK_ArticulatedHandMeshPulse. Mat venga assegnato in ArticulatedHandMesh. prefabbricate, che a sua volta deve essere assegnato in MRTK Settings-> input-> Hand Tracking-> prefabbricato mesh Hand.

## <a name="how-it-works"></a>Funzionamento

Lo shader della mano mesh usa le UV per eseguire il mapping dell'impulso lungo la mesh mano e per dissolvere il polso. Per eseguire il mapping dell'impulso, lo shader per la ricostruzione della superficie usa le posizioni dei vertici.

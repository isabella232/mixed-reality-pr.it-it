---
title: Pulse shader
description: descrizione degli shader Pulse in MRTK.
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: add3aaa2a98ca2ddc1f60b0307a3defed3236d9a2c09aa70ea2d12b2d9638eba
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115228386"
---
# <a name="pulse-shader"></a>Pulse shader

![MRTK_SpatialMesh_Pulse](https://user-images.githubusercontent.com/13754172/68261851-3489e200-fff6-11e9-9f6c-5574a7dd8db7.gif)

Usare lo shader pulse per animare un effetto di impulso visivo sulla ricostruzione della superficie, sulla mesh della mano articolata o su qualsiasi altra mesh.

## <a name="shader-and-material"></a>Shader e materiale

I materiali seguenti usano **SR_Triangles** shader. È possibile configurare varie opzioni, ad esempio il colore di riempimento, il colore della linea e il colore dell'impulso.

- **MRTK_Pulse_SpatialMeshBlue.mat** 
- **MRTK_Pulse_SpatialMeshPurple.mat** 
- **MRTK_Pulse_ArticulatedHandMeshBlue.mat** 
- **MRTK_Pulse_ArticulatedHandMeshPurple.mat** 

## <a name="prerequisites"></a>Prerequisiti

Per l'esempio di mesh spaziale, assicurarsi che MRTK_Pulse_SpatialMeshBlue.mat o MRTK_Pulse_SpatialMeshPurple.mat sia assegnato nell'oggetto MixedRealityToolkit -> Spatial Awareness Profile -> Display Impostazioni -> Visible Material.

Per l'esempio di mesh manuale, assicurarsi che MRTK_Pulse_ArticulatedHandMeshBlue.mat o MRTK_Pulse_ArticulatedHandMeshPurple.mat sia assegnato in ArticulatedHandMesh.prefab, che deve essere assegnato in MRTK Impostazioni -> Input -> Hand Tracking -> Hand Mesh Prefab.

## <a name="how-it-works"></a>Funzionamento

Lo shader hand mesh usa gli UV per mappare l'impulso lungo la mesh della mano e per sfumare il polso. Lo shader di ricostruzione della superficie usa le posizioni dei vertici per eseguire il mapping dell'impulso.

## <a name="spatial-mesh-example---pulseshaderspatialmeshexampleunity"></a>Esempio di mesh spaziale - PulseShaderSpatialMeshExample.unity

Analogamente all'esperienza della shell di HoloLens 2, è possibile puntare e toccare l'aria con il raggio della mano per generare un effetto pulsante sulla mesh spaziale. La scena di esempio contiene l'oggetto ExampleSpatialMesh, che è un test dei dati della mesh spaziale per la modalità di gioco di Unity. Questo oggetto verrà disabilitato e nascosto nel dispositivo.

Lo script **PulseShaderSpatialMeshHandler.cs** genera l'effetto pulse sulla mesh spaziale nella posizione del punto di hit se `PulseOnSelect` è true. La  `Auto Pulse` proprietà può anche essere impostata su true nel materiale stesso per un'animazione ripetuta.  Nella scena di esempio questo script è collegato al prefab PulseShaderSpatialMeshParent.  A questo prefab viene fatto riferimento nella proprietà Spatial Awareness Profile through Runtime Spatial Mesh Prefab . Durante il runtime, viene creata un'istanza del prefab PulseShaderSpatialMeshParent e viene aggiunta alla gerarchia della mesh spaziale (solo nel dispositivo questo comportamento non può essere osservato nell'editor).

## <a name="hand-mesh-example---pulseshaderhandmeshexampleunity"></a>Esempio di mesh manuale - PulseShaderHandMeshExample.unity

Questa scena di esempio illustra la visualizzazione della mesh della mano usando pulse shader. Quando una mano viene rilevata dal dispositivo HoloLens, l'animazione dell'impulso viene attivata una sola volta. Questo feedback visivo può aumentare l'attendibilità dell'interazione dell'utente. 

Lo script **PulseShaderHandMeshHandler.cs** genera l'effetto pulse sul materiale assegnato. Per impostazione predefinita, l'opzione "Pulse On Hand Detected" è selezionata.

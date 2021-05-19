---
title: Pulse Shader
description: descrizione degli shader Pulse in MRTK.
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: e03c021689b6701b86ae25ba9fa253ece1368428
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144946"
---
# <a name="pulse-shader"></a>Pulse shader

![MRTK_SpatialMesh_Pulse](https://user-images.githubusercontent.com/13754172/68261851-3489e200-fff6-11e9-9f6c-5574a7dd8db7.gif)

Usare l'pulse shader per animare un effetto di pulsazione visiva sulla superficie, sulla mesh della mano articolata o su qualsiasi altra mesh.

## <a name="shader-and-material"></a>Shader e materiale

I materiali seguenti usano **SR_Triangles** shader. È possibile configurare varie opzioni, ad esempio il colore di riempimento, il colore della linea e il colore di pulsazione.

- **MRTK_Pulse_SpatialMeshBlue.mat** 
- **MRTK_Pulse_SpatialMeshPurple.mat** 
- **MRTK_Pulse_ArticulatedHandMeshBlue.mat** 
- **MRTK_Pulse_ArticulatedHandMeshPurple.mat** 

## <a name="prerequisites"></a>Prerequisiti

Per l'esempio di mesh spaziale, assicurarsi che MRTK_Pulse_ArticulatedHandMeshBlue.mat o MRTK_Pulse_ArticulatedHandMeshPurple.mat sia assegnato in MrTK Settings -> Spatial Awareness -> Display Settings -> Visible Material (Impostazioni MRTK -> Spatial Awareness -> Display Settings -> Visible Material).

Per l'esempio della mesh manuale, assicurarsi che MRTK_Pulse_SpatialMeshBlue.mat o MRTK_Pulse_SpatialMeshPurple.mat sia assegnato in ArticulatedHandMesh.prefab, che a sua stesso deve essere assegnato in MRTK Settings -> Input -> Hand Tracking -> Hand Mesh Prefab (Impostazioni MRTK - Input -> Hand Tracking - > Hand Mesh Prefab).

## <a name="how-it-works"></a>Funzionamento

Lo shader con mesh manuale usa le UV per eseguire il mapping dell'pulse lungo la mesh della mano e per sfumare il corpo. Lo shader di ricorsiva della superficie usa le posizioni dei vertici per eseguire il mapping dell'pulse.

## <a name="spatial-mesh-example---pulseshaderspatialmeshexampleunity"></a>Esempio di mesh spaziale - PulseShaderSpatialMeshExample.unity

Analogamente all'HoloLens 2 della shell, è possibile puntare e toccare con il raggio della mano per generare un effetto pulsante sulla mesh spaziale. La scena di esempio contiene l'oggetto ExampleSpatialMesh, che è un test dei dati della mesh spaziale per la modalità di gioco di Unity. Questo oggetto verrà disabilitato e nascosto nel dispositivo.

Lo script **PulseShaderSpatialMeshHandler.cs** genera l'effetto pulse sulla mesh spaziale nella posizione del punto di hit se `PulseOnSelect` è true. La  `Auto Pulse` proprietà può anche essere impostata su true nel materiale stesso per un'animazione ripetuta.  Nella scena di esempio questo script è collegato al prefab PulseShaderSpatialMeshParent.  A questo prefab viene fatto riferimento nella proprietà Spatial Awareness Profile through Runtime Spatial Mesh Prefab . Durante il runtime, viene creata un'istanza del prefab PulseShaderSpatialMeshParent e viene aggiunta alla gerarchia della mesh spaziale (solo nel dispositivo questo comportamento non può essere osservato nell'editor).

## <a name="hand-mesh-example---pulseshaderhandmeshexampleunity"></a>Esempio di mesh manuale - PulseShaderHandMeshExample.unity

Questa scena di esempio illustra la visualizzazione della mesh della mano usando pulse shader. Quando viene rilevata una mano dal dispositivo HoloLens, l'animazione dell'impulso viene attivata una sola volta. Questo feedback visivo può aumentare l'attendibilità dell'interazione dell'utente. 

Lo script **PulseShaderHandMeshHandler.cs** genera l'effetto pulse sul materiale assegnato. Per impostazione predefinita, l'opzione "Pulse On Hand Detected" è selezionata.

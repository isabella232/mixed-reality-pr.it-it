---
title: Pulse shader
description: descrizione degli shader Pulse in MRTK.
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: 087806d48c7304d43f8383285cbaa2a12d8bf99a
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176309"
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

Per l'esempio della mesh spaziale, assicurarsi che MRTK_Pulse_ArticulatedHandMeshBlue.mat o MRTK_Pulse_ArticulatedHandMeshPurple.mat sia assegnato in MRTK Impostazioni -> Spatial Awareness -> Display Impostazioni -> Visible Material (MrTK Impostazioni -> Spatial Awareness -> Display Impostazioni -> Visible Material).

Per l'esempio della mesh manuale, assicurarsi che MRTK_Pulse_SpatialMeshBlue.mat o MRTK_Pulse_SpatialMeshPurple.mat sia assegnato in ArticulatedHandMesh.prefab, che a sua stessa deve essere assegnato nel prefab MRTK Impostazioni -> Input -> Hand Tracking -> Hand Mesh.

## <a name="how-it-works"></a>Funzionamento

Lo shader a mesh manuale usa le UV per eseguire il mapping dell'onda lungo la mesh mano e per dissolvere il corpo. Lo shader di ricorsiva della superficie usa le posizioni dei vertici per eseguire il mapping dell'pulse.

## <a name="spatial-mesh-example---pulseshaderspatialmeshexampleunity"></a>Esempio di mesh spaziale - PulseShaderSpatialMeshExample.unity

Analogamente all'HoloLens 2 della shell, è possibile puntare e toccare con il raggio della mano per generare un effetto pulsante sulla mesh spaziale. La scena di esempio contiene l'oggetto ExampleSpatialMesh, che è un test dei dati della mesh spaziale per la modalità di gioco di Unity. Questo oggetto verrà disabilitato e nascosto nel dispositivo.

Lo script **PulseShaderSpatialMeshHandler.cs** genera l'effetto di pulsazione sulla mesh spaziale in corrispondenza della posizione del punto di hit, `PulseOnSelect` se è true. La  `Auto Pulse` proprietà può anche essere impostata su true nel materiale stesso per un'animazione ripetuta.  Nella scena di esempio questo script è collegato al prefab PulseShaderSpatialMeshParent.  A questo prefab viene fatto riferimento nella proprietà Spatial Awareness Profile through Runtime Spatial Mesh Prefab (Profilo di consapevolezza spaziale tramite la proprietà Runtime Spatial Mesh Prefab). Durante il runtime, viene creata un'istanza del prefab PulseShaderSpatialMeshParent e viene aggiunta alla gerarchia della mesh spaziale (solo nel dispositivo questo comportamento non può essere osservato nell'editor).

## <a name="hand-mesh-example---pulseshaderhandmeshexampleunity"></a>Esempio di mesh mano - PulseShaderHandMeshExample.unity

Questa scena di esempio illustra la visualizzazione della mesh mano usando pulse shader. Quando viene rilevata una mano dal dispositivo HoloLens, l'animazione a pulsazione viene attivata una sola volta. Questo feedback visivo può aumentare l'attendibilità dell'interazione dell'utente. 

Lo script **PulseShaderHandMeshHandler.cs** genera l'effetto di pulsazione sul materiale assegnato. Per impostazione predefinita, è selezionato "Pulse On Hand Detected".

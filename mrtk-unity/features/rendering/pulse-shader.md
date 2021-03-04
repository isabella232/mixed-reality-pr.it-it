---
title: PulseShader
description: Descrizione su Pulse shader in MRTK.
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: 2861b86eddb6268ce348be753b795e9c294910cd
ms.sourcegitcommit: 7a8fa3257a13635ddad77d963e49440f62c19774
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/04/2021
ms.locfileid: "101884069"
---
# <a name="pulse-shader"></a>Pulse shader

![MRTK_SpatialMesh_Pulse](https://user-images.githubusercontent.com/13754172/68261851-3489e200-fff6-11e9-9f6c-5574a7dd8db7.gif)

Usare Pulse shader per animare un effetto di impulso visivo sulla ricostruzione della superficie, sulla mesh a mano articolata o su qualsiasi altra mesh.

## <a name="shader-and-material"></a>Shader e materiale

I materiali seguenti usano **SR_Triangles** shader. È possibile configurare diverse opzioni, ad esempio colore riempimento, colore linea e colore Pulse.

- **MRTK_Pulse_SpatialMeshBlue. Mat** 
- **MRTK_Pulse_SpatialMeshPurple. Mat** 
- **MRTK_Pulse_ArticulatedHandMeshBlue. Mat** 
- **MRTK_Pulse_ArticulatedHandMeshPurple. Mat** 

## <a name="prerequisites"></a>Prerequisiti

Per l'esempio di mesh spaziale, assicurarsi che MRTK_Pulse_ArticulatedHandMeshBlue. mat o MRTK_Pulse_ArticulatedHandMeshPurple. Mat sia assegnato in impostazioni di MRTK-> riconoscimento spaziale-impostazioni di visualizzazione >-> materiale visibile.

Per l'esempio di mesh della mano, assicurarsi che MRTK_Pulse_SpatialMeshBlue. mat o MRTK_Pulse_SpatialMeshPurple. Mat venga assegnato in ArticulatedHandMesh. prefabbricate, che a sua volta deve essere assegnato in MRTK Settings-> input-> Hand Tracking-> prefabbricato mesh Hand.

## <a name="how-it-works"></a>Funzionamento

Lo shader della mano mesh usa le UV per eseguire il mapping dell'impulso lungo la mesh mano e per dissolvere il polso. Per eseguire il mapping dell'impulso, lo shader per la ricostruzione della superficie usa le posizioni dei vertici.

## <a name="spatial-mesh-example---pulseshaderspatialmeshexampleunity"></a>Esempio di mesh spaziale-PulseShaderSpatialMeshExample. Unity

Analogamente all'esperienza della shell di HoloLens 2, è possibile puntare e toccare con il raggio di mano per generare un effetto pulsante sulla mesh spaziale. La scena di esempio contiene un oggetto ExampleSpatialMesh che rappresenta i dati della mesh spaziale di test per la modalità di gioco di Unity. Questo oggetto verrà disabilitato e nascosto nel dispositivo.

Lo script **PulseShaderSpatialMeshHandler.cs** genera l'effetto pulse sulla mesh spaziale nella posizione del punto di riscontro se `PulseOnSelect` è true. La  `Auto Pulse` proprietà può anche essere impostata su true nel materiale stesso per un'animazione ripetuta.  Nella scena di esempio, questo script è associato alla prefabbricata PulseShaderSpatialMeshParent.  Si fa riferimento a questa prefabbricata nel profilo di riconoscimento spaziale tramite la proprietà prefabbricata mesh spaziale di Runtime. Durante il runtime, viene creata un'istanza del prefabbricato PulseShaderSpatialMeshParent e ne viene creata un'istanza e viene aggiunto alla gerarchia mesh spaziale (solo sul dispositivo, questo comportamento non può essere osservato nell'editor).

## <a name="hand-mesh-example---pulseshaderhandmeshexampleunity"></a>Esempio di mesh a mano-PulseShaderHandMeshExample. Unity

In questa scena di esempio viene illustrata la visualizzazione Mesh mano con Pulse shader. Quando viene rilevata una mano dal dispositivo HoloLens, l'animazione a impulsi viene attivata una sola volta. Questo feedback visivo può aumentare la confidenza dell'interazione dell'utente. 

Lo script **PulseShaderHandMeshHandler.cs** genera un effetto impulsi sul materiale assegnato. Per impostazione predefinita, viene selezionato "Pulse on hand detected".

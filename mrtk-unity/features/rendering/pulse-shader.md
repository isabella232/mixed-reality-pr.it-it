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
# <a name="pulse-shader"></a><span data-ttu-id="a1b3c-104">Pulse shader</span><span class="sxs-lookup"><span data-stu-id="a1b3c-104">Pulse shader</span></span>

![MRTK_SpatialMesh_Pulse](https://user-images.githubusercontent.com/13754172/68261851-3489e200-fff6-11e9-9f6c-5574a7dd8db7.gif)

<span data-ttu-id="a1b3c-106">Usare l'pulse shader per animare un effetto di pulsazione visiva sulla superficie, sulla mesh della mano articolata o su qualsiasi altra mesh.</span><span class="sxs-lookup"><span data-stu-id="a1b3c-106">Use the pulse shader to animate a visual pulse effect over surface reconstruction, articulated hand mesh, or any other meshes.</span></span>

## <a name="shader-and-material"></a><span data-ttu-id="a1b3c-107">Shader e materiale</span><span class="sxs-lookup"><span data-stu-id="a1b3c-107">Shader and material</span></span>

<span data-ttu-id="a1b3c-108">I materiali seguenti usano **SR_Triangles** shader.</span><span class="sxs-lookup"><span data-stu-id="a1b3c-108">Following materials use **SR_Triangles** shader.</span></span> <span data-ttu-id="a1b3c-109">È possibile configurare varie opzioni, ad esempio il colore di riempimento, il colore della linea e il colore di pulsazione.</span><span class="sxs-lookup"><span data-stu-id="a1b3c-109">You can configure various options such as fill color, line color, and pulse color.</span></span>

- <span data-ttu-id="a1b3c-110">**MRTK_Pulse_SpatialMeshBlue.mat**</span><span class="sxs-lookup"><span data-stu-id="a1b3c-110">**MRTK_Pulse_SpatialMeshBlue.mat**</span></span> 
- <span data-ttu-id="a1b3c-111">**MRTK_Pulse_SpatialMeshPurple.mat**</span><span class="sxs-lookup"><span data-stu-id="a1b3c-111">**MRTK_Pulse_SpatialMeshPurple.mat**</span></span> 
- <span data-ttu-id="a1b3c-112">**MRTK_Pulse_ArticulatedHandMeshBlue.mat**</span><span class="sxs-lookup"><span data-stu-id="a1b3c-112">**MRTK_Pulse_ArticulatedHandMeshBlue.mat**</span></span> 
- <span data-ttu-id="a1b3c-113">**MRTK_Pulse_ArticulatedHandMeshPurple.mat**</span><span class="sxs-lookup"><span data-stu-id="a1b3c-113">**MRTK_Pulse_ArticulatedHandMeshPurple.mat**</span></span> 

## <a name="prerequisites"></a><span data-ttu-id="a1b3c-114">Prerequisiti</span><span class="sxs-lookup"><span data-stu-id="a1b3c-114">Prerequisites</span></span>

<span data-ttu-id="a1b3c-115">Per l'esempio di mesh spaziale, assicurarsi che MRTK_Pulse_ArticulatedHandMeshBlue.mat o MRTK_Pulse_ArticulatedHandMeshPurple.mat sia assegnato in MrTK Settings -> Spatial Awareness -> Display Settings -> Visible Material (Impostazioni MRTK -> Spatial Awareness -> Display Settings -> Visible Material).</span><span class="sxs-lookup"><span data-stu-id="a1b3c-115">For the spatial mesh example, ensure that MRTK_Pulse_ArticulatedHandMeshBlue.mat or MRTK_Pulse_ArticulatedHandMeshPurple.mat is assigned under MRTK Settings -> Spatial Awareness -> Display Settings -> Visible Material.</span></span>

<span data-ttu-id="a1b3c-116">Per l'esempio della mesh manuale, assicurarsi che MRTK_Pulse_SpatialMeshBlue.mat o MRTK_Pulse_SpatialMeshPurple.mat sia assegnato in ArticulatedHandMesh.prefab, che a sua stesso deve essere assegnato in MRTK Settings -> Input -> Hand Tracking -> Hand Mesh Prefab (Impostazioni MRTK - Input -> Hand Tracking - > Hand Mesh Prefab).</span><span class="sxs-lookup"><span data-stu-id="a1b3c-116">For the hand mesh example, ensure that MRTK_Pulse_SpatialMeshBlue.mat or MRTK_Pulse_SpatialMeshPurple.mat is assigned in ArticulatedHandMesh.prefab, which itself should be assigned in MRTK Settings -> Input -> Hand Tracking -> Hand Mesh Prefab.</span></span>

## <a name="how-it-works"></a><span data-ttu-id="a1b3c-117">Funzionamento</span><span class="sxs-lookup"><span data-stu-id="a1b3c-117">How it works</span></span>

<span data-ttu-id="a1b3c-118">Lo shader con mesh manuale usa le UV per eseguire il mapping dell'pulse lungo la mesh della mano e per sfumare il corpo.</span><span class="sxs-lookup"><span data-stu-id="a1b3c-118">The hand mesh shader uses UVs to map the pulse along the hand mesh, and to fade out the wrist.</span></span> <span data-ttu-id="a1b3c-119">Lo shader di ricorsiva della superficie usa le posizioni dei vertici per eseguire il mapping dell'pulse.</span><span class="sxs-lookup"><span data-stu-id="a1b3c-119">The surface reconstruction shader uses the vertex positions to map the pulse.</span></span>

## <a name="spatial-mesh-example---pulseshaderspatialmeshexampleunity"></a><span data-ttu-id="a1b3c-120">Esempio di mesh spaziale - PulseShaderSpatialMeshExample.unity</span><span class="sxs-lookup"><span data-stu-id="a1b3c-120">Spatial Mesh Example - PulseShaderSpatialMeshExample.unity</span></span>

<span data-ttu-id="a1b3c-121">Analogamente all'HoloLens 2 della shell, è possibile puntare e toccare con il raggio della mano per generare un effetto pulsante sulla mesh spaziale.</span><span class="sxs-lookup"><span data-stu-id="a1b3c-121">Similar to HoloLens 2's shell experience, you can point and air-tap with the hand ray to generate a pulsing effect on the spatial mesh.</span></span> <span data-ttu-id="a1b3c-122">La scena di esempio contiene l'oggetto ExampleSpatialMesh, che è un test dei dati della mesh spaziale per la modalità di gioco di Unity.</span><span class="sxs-lookup"><span data-stu-id="a1b3c-122">The example scene contains ExampleSpatialMesh object which is a test spatial mesh data for Unity's game mode.</span></span> <span data-ttu-id="a1b3c-123">Questo oggetto verrà disabilitato e nascosto nel dispositivo.</span><span class="sxs-lookup"><span data-stu-id="a1b3c-123">This object will be disabled and hidden on the device.</span></span>

<span data-ttu-id="a1b3c-124">Lo script **PulseShaderSpatialMeshHandler.cs** genera l'effetto pulse sulla mesh spaziale nella posizione del punto di hit se `PulseOnSelect` è true.</span><span class="sxs-lookup"><span data-stu-id="a1b3c-124">**PulseShaderSpatialMeshHandler.cs** script generates the pulse effect on the spatial mesh at the hit point position if `PulseOnSelect` is true.</span></span> <span data-ttu-id="a1b3c-125">La  `Auto Pulse` proprietà può anche essere impostata su true nel materiale stesso per un'animazione ripetuta.</span><span class="sxs-lookup"><span data-stu-id="a1b3c-125">The  `Auto Pulse` property can also be set to true in the material itself for a repeating animation.</span></span>  <span data-ttu-id="a1b3c-126">Nella scena di esempio questo script è collegato al prefab PulseShaderSpatialMeshParent.</span><span class="sxs-lookup"><span data-stu-id="a1b3c-126">In the example scene, this script is attached to the PulseShaderSpatialMeshParent prefab.</span></span>  <span data-ttu-id="a1b3c-127">A questo prefab viene fatto riferimento nella proprietà Spatial Awareness Profile through Runtime Spatial Mesh Prefab .</span><span class="sxs-lookup"><span data-stu-id="a1b3c-127">This prefab is referenced under the Spatial Awareness Profile through Runtime Spatial Mesh Prefab property.</span></span> <span data-ttu-id="a1b3c-128">Durante il runtime, viene creata un'istanza del prefab PulseShaderSpatialMeshParent e viene aggiunta alla gerarchia della mesh spaziale (solo nel dispositivo questo comportamento non può essere osservato nell'editor).</span><span class="sxs-lookup"><span data-stu-id="a1b3c-128">During runtime, the PulseShaderSpatialMeshParent prefab and is instantiated and added to the spatial mesh hierarchy (only on device, this behavior cannot be observed in the editor).</span></span>

## <a name="hand-mesh-example---pulseshaderhandmeshexampleunity"></a><span data-ttu-id="a1b3c-129">Esempio di mesh manuale - PulseShaderHandMeshExample.unity</span><span class="sxs-lookup"><span data-stu-id="a1b3c-129">Hand Mesh Example - PulseShaderHandMeshExample.unity</span></span>

<span data-ttu-id="a1b3c-130">Questa scena di esempio illustra la visualizzazione della mesh della mano usando pulse shader.</span><span class="sxs-lookup"><span data-stu-id="a1b3c-130">This example scene demonstrates the hand mesh visualization using pulse shader.</span></span> <span data-ttu-id="a1b3c-131">Quando viene rilevata una mano dal dispositivo HoloLens, l'animazione dell'impulso viene attivata una sola volta.</span><span class="sxs-lookup"><span data-stu-id="a1b3c-131">When a hand is detected by the HoloLens device, pulse animation will be triggered once.</span></span> <span data-ttu-id="a1b3c-132">Questo feedback visivo può aumentare l'attendibilità dell'interazione dell'utente.</span><span class="sxs-lookup"><span data-stu-id="a1b3c-132">This visual feedback can increase the user's interaction confidence.</span></span> 

<span data-ttu-id="a1b3c-133">Lo script **PulseShaderHandMeshHandler.cs** genera l'effetto pulse sul materiale assegnato.</span><span class="sxs-lookup"><span data-stu-id="a1b3c-133">**PulseShaderHandMeshHandler.cs** script generates pulse effect on the assigned material.</span></span> <span data-ttu-id="a1b3c-134">Per impostazione predefinita, l'opzione "Pulse On Hand Detected" è selezionata.</span><span class="sxs-lookup"><span data-stu-id="a1b3c-134">By default, 'Pulse On Hand Detected' is checked.</span></span>

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
# <a name="pulse-shader"></a><span data-ttu-id="e3391-104">Pulse shader</span><span class="sxs-lookup"><span data-stu-id="e3391-104">Pulse shader</span></span>

![MRTK_SpatialMesh_Pulse](https://user-images.githubusercontent.com/13754172/68261851-3489e200-fff6-11e9-9f6c-5574a7dd8db7.gif)

<span data-ttu-id="e3391-106">Usare l'pulse shader per animare un effetto di pulsazione visiva sulla superficie, sulla mesh della mano articolata o su qualsiasi altra mesh.</span><span class="sxs-lookup"><span data-stu-id="e3391-106">Use the pulse shader to animate a visual pulse effect over surface reconstruction, articulated hand mesh, or any other meshes.</span></span>

## <a name="shader-and-material"></a><span data-ttu-id="e3391-107">Shader e materiale</span><span class="sxs-lookup"><span data-stu-id="e3391-107">Shader and material</span></span>

<span data-ttu-id="e3391-108">I materiali seguenti usano **SR_Triangles** shader.</span><span class="sxs-lookup"><span data-stu-id="e3391-108">Following materials use **SR_Triangles** shader.</span></span> <span data-ttu-id="e3391-109">È possibile configurare varie opzioni, ad esempio il colore di riempimento, il colore della linea e il colore di pulsazione.</span><span class="sxs-lookup"><span data-stu-id="e3391-109">You can configure various options such as fill color, line color, and pulse color.</span></span>

- <span data-ttu-id="e3391-110">**MRTK_Pulse_SpatialMeshBlue.mat**</span><span class="sxs-lookup"><span data-stu-id="e3391-110">**MRTK_Pulse_SpatialMeshBlue.mat**</span></span> 
- <span data-ttu-id="e3391-111">**MRTK_Pulse_SpatialMeshPurple.mat**</span><span class="sxs-lookup"><span data-stu-id="e3391-111">**MRTK_Pulse_SpatialMeshPurple.mat**</span></span> 
- <span data-ttu-id="e3391-112">**MRTK_Pulse_ArticulatedHandMeshBlue.mat**</span><span class="sxs-lookup"><span data-stu-id="e3391-112">**MRTK_Pulse_ArticulatedHandMeshBlue.mat**</span></span> 
- <span data-ttu-id="e3391-113">**MRTK_Pulse_ArticulatedHandMeshPurple.mat**</span><span class="sxs-lookup"><span data-stu-id="e3391-113">**MRTK_Pulse_ArticulatedHandMeshPurple.mat**</span></span> 

## <a name="prerequisites"></a><span data-ttu-id="e3391-114">Prerequisiti</span><span class="sxs-lookup"><span data-stu-id="e3391-114">Prerequisites</span></span>

<span data-ttu-id="e3391-115">Per l'esempio della mesh spaziale, assicurarsi che MRTK_Pulse_ArticulatedHandMeshBlue.mat o MRTK_Pulse_ArticulatedHandMeshPurple.mat sia assegnato in MRTK Impostazioni -> Spatial Awareness -> Display Impostazioni -> Visible Material (MrTK Impostazioni -> Spatial Awareness -> Display Impostazioni -> Visible Material).</span><span class="sxs-lookup"><span data-stu-id="e3391-115">For the spatial mesh example, ensure that MRTK_Pulse_ArticulatedHandMeshBlue.mat or MRTK_Pulse_ArticulatedHandMeshPurple.mat is assigned under MRTK Settings -> Spatial Awareness -> Display Settings -> Visible Material.</span></span>

<span data-ttu-id="e3391-116">Per l'esempio della mesh manuale, assicurarsi che MRTK_Pulse_SpatialMeshBlue.mat o MRTK_Pulse_SpatialMeshPurple.mat sia assegnato in ArticulatedHandMesh.prefab, che a sua stessa deve essere assegnato nel prefab MRTK Impostazioni -> Input -> Hand Tracking -> Hand Mesh.</span><span class="sxs-lookup"><span data-stu-id="e3391-116">For the hand mesh example, ensure that MRTK_Pulse_SpatialMeshBlue.mat or MRTK_Pulse_SpatialMeshPurple.mat is assigned in ArticulatedHandMesh.prefab, which itself should be assigned in MRTK Settings -> Input -> Hand Tracking -> Hand Mesh Prefab.</span></span>

## <a name="how-it-works"></a><span data-ttu-id="e3391-117">Funzionamento</span><span class="sxs-lookup"><span data-stu-id="e3391-117">How it works</span></span>

<span data-ttu-id="e3391-118">Lo shader a mesh manuale usa le UV per eseguire il mapping dell'onda lungo la mesh mano e per dissolvere il corpo.</span><span class="sxs-lookup"><span data-stu-id="e3391-118">The hand mesh shader uses UVs to map the pulse along the hand mesh, and to fade out the wrist.</span></span> <span data-ttu-id="e3391-119">Lo shader di ricorsiva della superficie usa le posizioni dei vertici per eseguire il mapping dell'pulse.</span><span class="sxs-lookup"><span data-stu-id="e3391-119">The surface reconstruction shader uses the vertex positions to map the pulse.</span></span>

## <a name="spatial-mesh-example---pulseshaderspatialmeshexampleunity"></a><span data-ttu-id="e3391-120">Esempio di mesh spaziale - PulseShaderSpatialMeshExample.unity</span><span class="sxs-lookup"><span data-stu-id="e3391-120">Spatial Mesh Example - PulseShaderSpatialMeshExample.unity</span></span>

<span data-ttu-id="e3391-121">Analogamente all'HoloLens 2 della shell, è possibile puntare e toccare con il raggio della mano per generare un effetto pulsante sulla mesh spaziale.</span><span class="sxs-lookup"><span data-stu-id="e3391-121">Similar to HoloLens 2's shell experience, you can point and air-tap with the hand ray to generate a pulsing effect on the spatial mesh.</span></span> <span data-ttu-id="e3391-122">La scena di esempio contiene l'oggetto ExampleSpatialMesh, che è un test dei dati della mesh spaziale per la modalità di gioco di Unity.</span><span class="sxs-lookup"><span data-stu-id="e3391-122">The example scene contains ExampleSpatialMesh object which is a test spatial mesh data for Unity's game mode.</span></span> <span data-ttu-id="e3391-123">Questo oggetto verrà disabilitato e nascosto nel dispositivo.</span><span class="sxs-lookup"><span data-stu-id="e3391-123">This object will be disabled and hidden on the device.</span></span>

<span data-ttu-id="e3391-124">Lo script **PulseShaderSpatialMeshHandler.cs** genera l'effetto di pulsazione sulla mesh spaziale in corrispondenza della posizione del punto di hit, `PulseOnSelect` se è true.</span><span class="sxs-lookup"><span data-stu-id="e3391-124">**PulseShaderSpatialMeshHandler.cs** script generates the pulse effect on the spatial mesh at the hit point position if `PulseOnSelect` is true.</span></span> <span data-ttu-id="e3391-125">La  `Auto Pulse` proprietà può anche essere impostata su true nel materiale stesso per un'animazione ripetuta.</span><span class="sxs-lookup"><span data-stu-id="e3391-125">The  `Auto Pulse` property can also be set to true in the material itself for a repeating animation.</span></span>  <span data-ttu-id="e3391-126">Nella scena di esempio questo script è collegato al prefab PulseShaderSpatialMeshParent.</span><span class="sxs-lookup"><span data-stu-id="e3391-126">In the example scene, this script is attached to the PulseShaderSpatialMeshParent prefab.</span></span>  <span data-ttu-id="e3391-127">A questo prefab viene fatto riferimento nella proprietà Spatial Awareness Profile through Runtime Spatial Mesh Prefab (Profilo di consapevolezza spaziale tramite la proprietà Runtime Spatial Mesh Prefab).</span><span class="sxs-lookup"><span data-stu-id="e3391-127">This prefab is referenced under the Spatial Awareness Profile through Runtime Spatial Mesh Prefab property.</span></span> <span data-ttu-id="e3391-128">Durante il runtime, viene creata un'istanza del prefab PulseShaderSpatialMeshParent e viene aggiunta alla gerarchia della mesh spaziale (solo nel dispositivo questo comportamento non può essere osservato nell'editor).</span><span class="sxs-lookup"><span data-stu-id="e3391-128">During runtime, the PulseShaderSpatialMeshParent prefab and is instantiated and added to the spatial mesh hierarchy (only on device, this behavior cannot be observed in the editor).</span></span>

## <a name="hand-mesh-example---pulseshaderhandmeshexampleunity"></a><span data-ttu-id="e3391-129">Esempio di mesh mano - PulseShaderHandMeshExample.unity</span><span class="sxs-lookup"><span data-stu-id="e3391-129">Hand Mesh Example - PulseShaderHandMeshExample.unity</span></span>

<span data-ttu-id="e3391-130">Questa scena di esempio illustra la visualizzazione della mesh mano usando pulse shader.</span><span class="sxs-lookup"><span data-stu-id="e3391-130">This example scene demonstrates the hand mesh visualization using pulse shader.</span></span> <span data-ttu-id="e3391-131">Quando viene rilevata una mano dal dispositivo HoloLens, l'animazione a pulsazione viene attivata una sola volta.</span><span class="sxs-lookup"><span data-stu-id="e3391-131">When a hand is detected by the HoloLens device, pulse animation will be triggered once.</span></span> <span data-ttu-id="e3391-132">Questo feedback visivo può aumentare l'attendibilità dell'interazione dell'utente.</span><span class="sxs-lookup"><span data-stu-id="e3391-132">This visual feedback can increase the user's interaction confidence.</span></span> 

<span data-ttu-id="e3391-133">Lo script **PulseShaderHandMeshHandler.cs** genera l'effetto di pulsazione sul materiale assegnato.</span><span class="sxs-lookup"><span data-stu-id="e3391-133">**PulseShaderHandMeshHandler.cs** script generates pulse effect on the assigned material.</span></span> <span data-ttu-id="e3391-134">Per impostazione predefinita, è selezionato "Pulse On Hand Detected".</span><span class="sxs-lookup"><span data-stu-id="e3391-134">By default, 'Pulse On Hand Detected' is checked.</span></span>

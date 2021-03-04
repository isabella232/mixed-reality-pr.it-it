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
# <a name="pulse-shader"></a><span data-ttu-id="0c297-104">Pulse shader</span><span class="sxs-lookup"><span data-stu-id="0c297-104">Pulse shader</span></span>

![MRTK_SpatialMesh_Pulse](https://user-images.githubusercontent.com/13754172/68261851-3489e200-fff6-11e9-9f6c-5574a7dd8db7.gif)

<span data-ttu-id="0c297-106">Usare Pulse shader per animare un effetto di impulso visivo sulla ricostruzione della superficie, sulla mesh a mano articolata o su qualsiasi altra mesh.</span><span class="sxs-lookup"><span data-stu-id="0c297-106">Use the pulse shader to animate a visual pulse effect over surface reconstruction, articulated hand mesh, or any other meshes.</span></span>

## <a name="shader-and-material"></a><span data-ttu-id="0c297-107">Shader e materiale</span><span class="sxs-lookup"><span data-stu-id="0c297-107">Shader and material</span></span>

<span data-ttu-id="0c297-108">I materiali seguenti usano **SR_Triangles** shader.</span><span class="sxs-lookup"><span data-stu-id="0c297-108">Following materials use **SR_Triangles** shader.</span></span> <span data-ttu-id="0c297-109">È possibile configurare diverse opzioni, ad esempio colore riempimento, colore linea e colore Pulse.</span><span class="sxs-lookup"><span data-stu-id="0c297-109">You can configure various options such as fill color, line color, and pulse color.</span></span>

- <span data-ttu-id="0c297-110">**MRTK_Pulse_SpatialMeshBlue. Mat**</span><span class="sxs-lookup"><span data-stu-id="0c297-110">**MRTK_Pulse_SpatialMeshBlue.mat**</span></span> 
- <span data-ttu-id="0c297-111">**MRTK_Pulse_SpatialMeshPurple. Mat**</span><span class="sxs-lookup"><span data-stu-id="0c297-111">**MRTK_Pulse_SpatialMeshPurple.mat**</span></span> 
- <span data-ttu-id="0c297-112">**MRTK_Pulse_ArticulatedHandMeshBlue. Mat**</span><span class="sxs-lookup"><span data-stu-id="0c297-112">**MRTK_Pulse_ArticulatedHandMeshBlue.mat**</span></span> 
- <span data-ttu-id="0c297-113">**MRTK_Pulse_ArticulatedHandMeshPurple. Mat**</span><span class="sxs-lookup"><span data-stu-id="0c297-113">**MRTK_Pulse_ArticulatedHandMeshPurple.mat**</span></span> 

## <a name="prerequisites"></a><span data-ttu-id="0c297-114">Prerequisiti</span><span class="sxs-lookup"><span data-stu-id="0c297-114">Prerequisites</span></span>

<span data-ttu-id="0c297-115">Per l'esempio di mesh spaziale, assicurarsi che MRTK_Pulse_ArticulatedHandMeshBlue. mat o MRTK_Pulse_ArticulatedHandMeshPurple. Mat sia assegnato in impostazioni di MRTK-> riconoscimento spaziale-impostazioni di visualizzazione >-> materiale visibile.</span><span class="sxs-lookup"><span data-stu-id="0c297-115">For the spatial mesh example, ensure that MRTK_Pulse_ArticulatedHandMeshBlue.mat or MRTK_Pulse_ArticulatedHandMeshPurple.mat is assigned under MRTK Settings -> Spatial Awareness -> Display Settings -> Visible Material.</span></span>

<span data-ttu-id="0c297-116">Per l'esempio di mesh della mano, assicurarsi che MRTK_Pulse_SpatialMeshBlue. mat o MRTK_Pulse_SpatialMeshPurple. Mat venga assegnato in ArticulatedHandMesh. prefabbricate, che a sua volta deve essere assegnato in MRTK Settings-> input-> Hand Tracking-> prefabbricato mesh Hand.</span><span class="sxs-lookup"><span data-stu-id="0c297-116">For the hand mesh example, ensure that MRTK_Pulse_SpatialMeshBlue.mat or MRTK_Pulse_SpatialMeshPurple.mat is assigned in ArticulatedHandMesh.prefab, which itself should be assigned in MRTK Settings -> Input -> Hand Tracking -> Hand Mesh Prefab.</span></span>

## <a name="how-it-works"></a><span data-ttu-id="0c297-117">Funzionamento</span><span class="sxs-lookup"><span data-stu-id="0c297-117">How it works</span></span>

<span data-ttu-id="0c297-118">Lo shader della mano mesh usa le UV per eseguire il mapping dell'impulso lungo la mesh mano e per dissolvere il polso.</span><span class="sxs-lookup"><span data-stu-id="0c297-118">The hand mesh shader uses UVs to map the pulse along the hand mesh, and to fade out the wrist.</span></span> <span data-ttu-id="0c297-119">Per eseguire il mapping dell'impulso, lo shader per la ricostruzione della superficie usa le posizioni dei vertici.</span><span class="sxs-lookup"><span data-stu-id="0c297-119">The surface reconstruction shader uses the vertex positions to map the pulse.</span></span>

## <a name="spatial-mesh-example---pulseshaderspatialmeshexampleunity"></a><span data-ttu-id="0c297-120">Esempio di mesh spaziale-PulseShaderSpatialMeshExample. Unity</span><span class="sxs-lookup"><span data-stu-id="0c297-120">Spatial Mesh Example - PulseShaderSpatialMeshExample.unity</span></span>

<span data-ttu-id="0c297-121">Analogamente all'esperienza della shell di HoloLens 2, è possibile puntare e toccare con il raggio di mano per generare un effetto pulsante sulla mesh spaziale.</span><span class="sxs-lookup"><span data-stu-id="0c297-121">Similar to HoloLens 2's shell experience, you can point and air-tap with the hand ray to generate a pulsing effect on the spatial mesh.</span></span> <span data-ttu-id="0c297-122">La scena di esempio contiene un oggetto ExampleSpatialMesh che rappresenta i dati della mesh spaziale di test per la modalità di gioco di Unity.</span><span class="sxs-lookup"><span data-stu-id="0c297-122">The example scene contains ExampleSpatialMesh object which is a test spatial mesh data for Unity's game mode.</span></span> <span data-ttu-id="0c297-123">Questo oggetto verrà disabilitato e nascosto nel dispositivo.</span><span class="sxs-lookup"><span data-stu-id="0c297-123">This object will be disabled and hidden on the device.</span></span>

<span data-ttu-id="0c297-124">Lo script **PulseShaderSpatialMeshHandler.cs** genera l'effetto pulse sulla mesh spaziale nella posizione del punto di riscontro se `PulseOnSelect` è true.</span><span class="sxs-lookup"><span data-stu-id="0c297-124">**PulseShaderSpatialMeshHandler.cs** script generates the pulse effect on the spatial mesh at the hit point position if `PulseOnSelect` is true.</span></span> <span data-ttu-id="0c297-125">La  `Auto Pulse` proprietà può anche essere impostata su true nel materiale stesso per un'animazione ripetuta.</span><span class="sxs-lookup"><span data-stu-id="0c297-125">The  `Auto Pulse` property can also be set to true in the material itself for a repeating animation.</span></span>  <span data-ttu-id="0c297-126">Nella scena di esempio, questo script è associato alla prefabbricata PulseShaderSpatialMeshParent.</span><span class="sxs-lookup"><span data-stu-id="0c297-126">In the example scene, this script is attached to the PulseShaderSpatialMeshParent prefab.</span></span>  <span data-ttu-id="0c297-127">Si fa riferimento a questa prefabbricata nel profilo di riconoscimento spaziale tramite la proprietà prefabbricata mesh spaziale di Runtime.</span><span class="sxs-lookup"><span data-stu-id="0c297-127">This prefab is referenced under the Spatial Awareness Profile through Runtime Spatial Mesh Prefab property.</span></span> <span data-ttu-id="0c297-128">Durante il runtime, viene creata un'istanza del prefabbricato PulseShaderSpatialMeshParent e ne viene creata un'istanza e viene aggiunto alla gerarchia mesh spaziale (solo sul dispositivo, questo comportamento non può essere osservato nell'editor).</span><span class="sxs-lookup"><span data-stu-id="0c297-128">During runtime, the PulseShaderSpatialMeshParent prefab and is instantiated and added to the spatial mesh hierarchy (only on device, this behavior cannot be observed in the editor).</span></span>

## <a name="hand-mesh-example---pulseshaderhandmeshexampleunity"></a><span data-ttu-id="0c297-129">Esempio di mesh a mano-PulseShaderHandMeshExample. Unity</span><span class="sxs-lookup"><span data-stu-id="0c297-129">Hand Mesh Example - PulseShaderHandMeshExample.unity</span></span>

<span data-ttu-id="0c297-130">In questa scena di esempio viene illustrata la visualizzazione Mesh mano con Pulse shader.</span><span class="sxs-lookup"><span data-stu-id="0c297-130">This example scene demonstrates the hand mesh visualization using pulse shader.</span></span> <span data-ttu-id="0c297-131">Quando viene rilevata una mano dal dispositivo HoloLens, l'animazione a impulsi viene attivata una sola volta.</span><span class="sxs-lookup"><span data-stu-id="0c297-131">When a hand is detected by the HoloLens device, pulse animation will be triggered once.</span></span> <span data-ttu-id="0c297-132">Questo feedback visivo può aumentare la confidenza dell'interazione dell'utente.</span><span class="sxs-lookup"><span data-stu-id="0c297-132">This visual feedback can increase the user's interaction confidence.</span></span> 

<span data-ttu-id="0c297-133">Lo script **PulseShaderHandMeshHandler.cs** genera un effetto impulsi sul materiale assegnato.</span><span class="sxs-lookup"><span data-stu-id="0c297-133">**PulseShaderHandMeshHandler.cs** script generates pulse effect on the assigned material.</span></span> <span data-ttu-id="0c297-134">Per impostazione predefinita, viene selezionato "Pulse on hand detected".</span><span class="sxs-lookup"><span data-stu-id="0c297-134">By default, 'Pulse On Hand Detected' is checked.</span></span>

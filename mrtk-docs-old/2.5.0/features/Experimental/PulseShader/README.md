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
ms.locfileid: "104691768"
---
# <a name="pulse-shader"></a><span data-ttu-id="a1b94-104">Pulse shader</span><span class="sxs-lookup"><span data-stu-id="a1b94-104">Pulse shader</span></span>

![MRTK_SpatialMesh_Pulse](https://user-images.githubusercontent.com/13754172/68261851-3489e200-fff6-11e9-9f6c-5574a7dd8db7.gif)

<span data-ttu-id="a1b94-106">![MRTK_HandMesh_Pulse2 ](https://user-images.githubusercontent.com/13754172/68262035-e4f7e600-fff6-11e9-9858-796afd1cabc5.gif) usare Pulse shader per animare un effetto di impulso visivo sulla ricostruzione della superficie, sulla mesh a mano articolata o su qualsiasi altra mesh.</span><span class="sxs-lookup"><span data-stu-id="a1b94-106">![MRTK_HandMesh_Pulse2](https://user-images.githubusercontent.com/13754172/68262035-e4f7e600-fff6-11e9-9858-796afd1cabc5.gif) Use the pulse shader to animate a visual pulse effect over surface reconstruction, articulated hand mesh, or any other meshes.</span></span>

## <a name="shader-and-material"></a><span data-ttu-id="a1b94-107">Shader e materiale</span><span class="sxs-lookup"><span data-stu-id="a1b94-107">Shader and material</span></span>

<span data-ttu-id="a1b94-108">**MRTK_SurfaceReconstruction. Mat** e **MRTK_ArticulatedHandMeshPulse. Mat** utilizzano **SR_Triangles** shader.</span><span class="sxs-lookup"><span data-stu-id="a1b94-108">**MRTK_SurfaceReconstruction.mat** and **MRTK_ArticulatedHandMeshPulse.mat** uses **SR_Triangles** shader.</span></span> <span data-ttu-id="a1b94-109">È possibile configurare diverse opzioni, ad esempio colore riempimento, colore linea e colore Pulse.</span><span class="sxs-lookup"><span data-stu-id="a1b94-109">You can configure various options such as fill color, line color, and pulse color.</span></span>

## <a name="example-scene"></a><span data-ttu-id="a1b94-110">Scena di esempio</span><span class="sxs-lookup"><span data-stu-id="a1b94-110">Example scene</span></span>

<span data-ttu-id="a1b94-111">Aprire la scena **PulseShaderExamples. Unity** e osservare l'effetto pulsato sulle sfere, sulla ricostruzione della superficie e sulla mesh a mano articolata.</span><span class="sxs-lookup"><span data-stu-id="a1b94-111">Open **PulseShaderExamples.unity** scene, and observe the pulsing effect on the spheres, surface reconstruction, and the articulated hand mesh.</span></span>

<span data-ttu-id="a1b94-112">Usare lo script SurfacePulse. cs per animare l'effetto di impulso sul materiale assegnato oppure attivare "Pulse automatico" nel materiale stesso.</span><span class="sxs-lookup"><span data-stu-id="a1b94-112">Use the SurfacePulse.cs script to animate the pulse effect on the assigned material, or turn on "Auto Pulse" in the material itself.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="a1b94-113">Prerequisiti</span><span class="sxs-lookup"><span data-stu-id="a1b94-113">Prerequisites</span></span>

<span data-ttu-id="a1b94-114">Per la ricostruzione della superficie, assicurarsi che MRTK_SurfaceReconstruction. Mat sia assegnato in impostazioni di MRTK-> riconoscimento spaziale-> impostazioni di visualizzazione-> materiale visibile.</span><span class="sxs-lookup"><span data-stu-id="a1b94-114">For surface reconstruction, ensure that MRTK_SurfaceReconstruction.mat is assigned under MRTK Settings -> Spatial Awareness -> Display Settings -> Visible Material.</span></span>

<span data-ttu-id="a1b94-115">Per la mano articolata, assicurarsi che MRTK_ArticulatedHandMeshPulse. Mat venga assegnato in ArticulatedHandMesh. prefabbricate, che a sua volta deve essere assegnato in MRTK Settings-> input-> Hand Tracking-> prefabbricato mesh Hand.</span><span class="sxs-lookup"><span data-stu-id="a1b94-115">For articulated hand, ensure that MRTK_ArticulatedHandMeshPulse.mat is assigned in ArticulatedHandMesh.prefab, which itself should be assigned in MRTK Settings -> Input -> Hand Tracking -> Hand Mesh Prefab.</span></span>

## <a name="how-it-works"></a><span data-ttu-id="a1b94-116">Funzionamento</span><span class="sxs-lookup"><span data-stu-id="a1b94-116">How it works</span></span>

<span data-ttu-id="a1b94-117">Lo shader della mano mesh usa le UV per eseguire il mapping dell'impulso lungo la mesh mano e per dissolvere il polso.</span><span class="sxs-lookup"><span data-stu-id="a1b94-117">The hand mesh shader uses UVs to map the pulse along the hand mesh, and to fade out the wrist.</span></span> <span data-ttu-id="a1b94-118">Per eseguire il mapping dell'impulso, lo shader per la ricostruzione della superficie usa le posizioni dei vertici.</span><span class="sxs-lookup"><span data-stu-id="a1b94-118">The surface reconstruction shader uses the vertex positions to map the pulse.</span></span>

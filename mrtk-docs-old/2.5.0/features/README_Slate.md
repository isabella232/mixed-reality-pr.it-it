---
title: README_Slate
description: Documentazione su Slate in MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, Slate,
ms.openlocfilehash: a2228457d62f768c55da63425a9706559761ff3f
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/03/2021
ms.locfileid: "101783112"
---
# <a name="slate"></a><span data-ttu-id="d5031-104">Slate</span><span class="sxs-lookup"><span data-stu-id="d5031-104">Slate</span></span>

![Slate](Images/Slate/MRTK_Slate_Main.png)

<span data-ttu-id="d5031-106">La prefabbricata dello Slate offre un controllo dello stile della finestra sottile per la visualizzazione di contenuto 2D, ad esempio testo normale o articoli che includono supporti.</span><span class="sxs-lookup"><span data-stu-id="d5031-106">The Slate prefab offers a thin window style control for displaying 2D content, for example plain text or articles including media.</span></span> <span data-ttu-id="d5031-107">Offre una barra del titolo afferrabile, oltre a *seguire* e *chiudere* la funzionalità.</span><span class="sxs-lookup"><span data-stu-id="d5031-107">It offers a grabbable title bar as well as *Follow Me* and *Close* functionality.</span></span> <span data-ttu-id="d5031-108">È possibile scorrere la finestra del contenuto tramite input della mano articolata.</span><span class="sxs-lookup"><span data-stu-id="d5031-108">The content window can be scrolled via articulated hand input.</span></span>

## <a name="how-to-use-a-slate-control"></a><span data-ttu-id="d5031-109">Come usare un controllo Slate</span><span class="sxs-lookup"><span data-stu-id="d5031-109">How to use a slate control</span></span>

<span data-ttu-id="d5031-110">Un controllo Slate è costituito dagli elementi seguenti:</span><span class="sxs-lookup"><span data-stu-id="d5031-110">A slate control is composed of the following elements:</span></span>

* <span data-ttu-id="d5031-111">**Barra** del titolo: l'intera barra del titolo nella parte superiore dello Slate.</span><span class="sxs-lookup"><span data-stu-id="d5031-111">**TitleBar**: The entire title bar on top of the slate.</span></span>
* <span data-ttu-id="d5031-112">**Title**: area del titolo sul lato sinistro della barra del titolo.</span><span class="sxs-lookup"><span data-stu-id="d5031-112">**Title**: The title area on the left side of the title bar.</span></span>
* <span data-ttu-id="d5031-113">**Buttons**: area del pulsante sul lato destro della barra del titolo.</span><span class="sxs-lookup"><span data-stu-id="d5031-113">**Buttons**: The button area on the right side of the title bar.</span></span>
* <span data-ttu-id="d5031-114">**Backplate**: il lato posteriore dello Slate.</span><span class="sxs-lookup"><span data-stu-id="d5031-114">**BackPlate**: The back side of the slate.</span></span>
* <span data-ttu-id="d5031-115">**ContentQuad**: il contenuto viene assegnato come materiale.</span><span class="sxs-lookup"><span data-stu-id="d5031-115">**ContentQuad**: Content is assigned as material.</span></span> <span data-ttu-id="d5031-116">Nell'esempio viene utilizzato un materiale di esempio ' PanContent '.</span><span class="sxs-lookup"><span data-stu-id="d5031-116">The example uses a sample material 'PanContent'.</span></span>

<img src="Images/Slate/MRTK_SlateStructure.jpg" width="650" alt="Slate Structure">

## <a name="bounds-control"></a><span data-ttu-id="d5031-117">Controllo dei limiti</span><span class="sxs-lookup"><span data-stu-id="d5031-117">Bounds control</span></span>

<span data-ttu-id="d5031-118">Un controllo Slate contiene uno script di controllo dei limiti per la scala e la rotazione.</span><span class="sxs-lookup"><span data-stu-id="d5031-118">A slate control contains a bounds control script for scaling and rotating.</span></span> <span data-ttu-id="d5031-119">Per ulteriori informazioni sul controllo dei limiti, vedere la pagina relativa al [controllo dei limiti](README_BoundsControl.md) .</span><span class="sxs-lookup"><span data-stu-id="d5031-119">For more information on bounds control, please see the [bounds control](README_BoundsControl.md) page.</span></span>

<img src="Images/Slate/MRTK_Slate_BB.jpg" width="650" alt="Slate BB">

## <a name="buttons"></a><span data-ttu-id="d5031-120">Pulsanti</span><span class="sxs-lookup"><span data-stu-id="d5031-120">Buttons</span></span>

<span data-ttu-id="d5031-121">Uno slate standard offre due pulsanti come predefiniti nella parte superiore destra della barra del titolo:</span><span class="sxs-lookup"><span data-stu-id="d5031-121">A standard slate offers two buttons as default on the top right of the title bar:</span></span>

* <span data-ttu-id="d5031-122">**Follow me**: Abilita o imposta i componenti del Risolutore orbitali per fare in modo che l'oggetto Slate segua l'utente.</span><span class="sxs-lookup"><span data-stu-id="d5031-122">**Follow Me**: Toggles an orbital solver components to make the slate object follow the user.</span></span>
* <span data-ttu-id="d5031-123">**Close**: Disabilita l'oggetto Slate.</span><span class="sxs-lookup"><span data-stu-id="d5031-123">**Close**: Disables the slate object.</span></span>

<img src="Images/Slate/MRTK_Slate_Buttons.jpg" width="650" alt="Slate Buttons">

## <a name="scripts"></a><span data-ttu-id="d5031-124">Script</span><span class="sxs-lookup"><span data-stu-id="d5031-124">Scripts</span></span>

<span data-ttu-id="d5031-125">In generale, lo `NearInteractionTouchable.cs` script deve essere collegato a qualsiasi oggetto destinato a ricevere eventi di tocco da `IMixedRealityTouchHandler` .</span><span class="sxs-lookup"><span data-stu-id="d5031-125">In general, the `NearInteractionTouchable.cs` script must be attached to any object that is intended to receive touch events from the `IMixedRealityTouchHandler`.</span></span>

<img src="Images/Slate/MRTK_Slate_Scripts.png" alt="Slate Scripts">

* <span data-ttu-id="d5031-126">`HandInteractionPan.cs` Questo script gestisce l'input della mano articolata per toccare e muovere il contenuto nel *ContentQuad* dello Slate.</span><span class="sxs-lookup"><span data-stu-id="d5031-126">`HandInteractionPan.cs` This script handles articulated hand input for touching and moving the content on the slate's *ContentQuad*.</span></span>

* <span data-ttu-id="d5031-127">`HandInteractionPanZoom.cs`: Oltre all'interazione di panoramica, questo script supporta lo zoom a due bit.</span><span class="sxs-lookup"><span data-stu-id="d5031-127">`HandInteractionPanZoom.cs`: In addition to the panning interaction, this script supports two-handed zooming.</span></span>

<img src="Images/Slate/MRTK_Slate_PanZoom.png" width="500" alt="Slate Panzoom">

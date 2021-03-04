---
title: Descrizione comando
description: Panoramica della descrizione comando in MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK, descrizione comando,
ms.openlocfilehash: 3fbd7dac612cb669e8c4c6a4e3045e0117c97703
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/03/2021
ms.locfileid: "101781554"
---
# <a name="tooltip"></a><span data-ttu-id="96e06-104">Descrizione comando</span><span class="sxs-lookup"><span data-stu-id="96e06-104">Tooltip</span></span>

![Descrizione comando principale](../images/tooltip/MRTK_Tooltip_Main.png)

<span data-ttu-id="96e06-106">Le descrizioni comandi vengono in genere utilizzate per fornire un suggerimento o informazioni aggiuntive su un controllo più approfondito di un oggetto.</span><span class="sxs-lookup"><span data-stu-id="96e06-106">Tooltips are usually used to convey a hint or extra information upon closer inspection of an object.</span></span> <span data-ttu-id="96e06-107">È possibile utilizzare le descrizioni comandi per aggiungere annotazioni agli oggetti nell'ambiente fisico.</span><span class="sxs-lookup"><span data-stu-id="96e06-107">Tooltips can be used to annotate objects in the physical environment.</span></span>

## <a name="how-to-use-a-tooltip"></a><span data-ttu-id="96e06-108">Come usare una descrizione comando</span><span class="sxs-lookup"><span data-stu-id="96e06-108">How to use a tooltip</span></span>

<span data-ttu-id="96e06-109">Una descrizione comando può essere aggiunta direttamente alla gerarchia e destinata a un oggetto.</span><span class="sxs-lookup"><span data-stu-id="96e06-109">A tooltip can be added directly to the hierarchy and targeted to an object.</span></span>

<span data-ttu-id="96e06-110">Per usare questo metodo, è sufficiente aggiungere un oggetto Game e una delle precompilate ToolTip (assets/MRTK/SDK/features/UX/prefabrics/Tooltips) alla gerarchia di scene.</span><span class="sxs-lookup"><span data-stu-id="96e06-110">To use this method simply add a game object and one of the tooltip prefabs (Assets/MRTK/SDK/Features/UX/Prefabs/Tooltips) to the scene hierarchy.</span></span> <span data-ttu-id="96e06-111">Nel pannello di controllo del prefabbricato espandere lo [`ToolTip`](xref:Microsoft.MixedReality.Toolkit.UI.ToolTip) script.</span><span class="sxs-lookup"><span data-stu-id="96e06-111">In the prefab's inspector panel, expand the [`ToolTip`](xref:Microsoft.MixedReality.Toolkit.UI.ToolTip) script.</span></span> <span data-ttu-id="96e06-112">Selezionare uno stato tip e configurare la descrizione comando.</span><span class="sxs-lookup"><span data-stu-id="96e06-112">Select a tip state and configure the tooltip.</span></span>  <span data-ttu-id="96e06-113">Immettere il testo corrispondente per la descrizione comando nel campo di testo.</span><span class="sxs-lookup"><span data-stu-id="96e06-113">Enter the respective text for the tool tip in the text field.</span></span> <span data-ttu-id="96e06-114">Espandere lo [`ToolTipConnector`](xref:Microsoft.MixedReality.Toolkit.UI.ToolTipConnector) script e trascinare l'oggetto che deve avere la descrizione comando dalla gerarchia nel campo *destinazione* con etichetta.</span><span class="sxs-lookup"><span data-stu-id="96e06-114">Expand the [`ToolTipConnector`](xref:Microsoft.MixedReality.Toolkit.UI.ToolTipConnector) script and drag the object that is to have the tooltip from the hierarchy into the field labelled *Target*.</span></span> <span data-ttu-id="96e06-115">In questo modo la descrizione comando viene associata all'oggetto.</span><span class="sxs-lookup"><span data-stu-id="96e06-115">This attaches the tooltip to the object.</span></span>
<span data-ttu-id="96e06-116">![Connettore descrizione comando](../images/tooltip/MRTK_Tooltip_Connector.png)</span><span class="sxs-lookup"><span data-stu-id="96e06-116">![Tooltip Connector](../images/tooltip/MRTK_Tooltip_Connector.png)</span></span>

<span data-ttu-id="96e06-117">Questo utilizzo presuppone una descrizione comando che viene sempre visualizzata o mostrata/nascosta tramite script modificando la proprietà dello stato della descrizione comando del componente ToolTip.</span><span class="sxs-lookup"><span data-stu-id="96e06-117">This use assumes a tooltip that is always showing or that is shown / hidden via script by changing the tooltip state property of the tooltip component.</span></span>

## <a name="dynamically-spawning-tooltips"></a><span data-ttu-id="96e06-118">Generazione dinamica di descrizioni comandi</span><span class="sxs-lookup"><span data-stu-id="96e06-118">Dynamically spawning tooltips</span></span>

<span data-ttu-id="96e06-119">Una descrizione comando può essere aggiunta dinamicamente a un oggetto in fase di esecuzione, nonché preimpostata per visualizzare e nascondere un tocco o uno stato attivo.</span><span class="sxs-lookup"><span data-stu-id="96e06-119">A tooltip can be dynamically added to an object at runtime as well as pre-set to show and hide on a tap or focus.</span></span> <span data-ttu-id="96e06-120">È sufficiente aggiungere lo [`ToolTipSpawner`](xref:Microsoft.MixedReality.Toolkit.UI.ToolTipSpawner) script a un oggetto Game.</span><span class="sxs-lookup"><span data-stu-id="96e06-120">Simply add the [`ToolTipSpawner`](xref:Microsoft.MixedReality.Toolkit.UI.ToolTipSpawner) script to any game object.</span></span> <span data-ttu-id="96e06-121">I ritardi per la visualizzazione e la scomparsa possono essere impostati nel controllo degli script, oltre che in una durata, in modo che la descrizione comando scomparirà dopo una durata impostata.</span><span class="sxs-lookup"><span data-stu-id="96e06-121">Delays for appearing and disappearing can be set in the scripts inspector as well as a lifetime so that the tooltip will disappear after a set duration.</span></span> <span data-ttu-id="96e06-122">Le descrizioni comandi includono anche le proprietà di stile, ad esempio gli oggetti visivi in background nello script del generatore.</span><span class="sxs-lookup"><span data-stu-id="96e06-122">Tooltips also feature style properties such as background visuals in the spawner script.</span></span> <span data-ttu-id="96e06-123">Per impostazione predefinita, la descrizione comando verrà ancorata all'oggetto con lo script di generazione.</span><span class="sxs-lookup"><span data-stu-id="96e06-123">By default the tooltip will be anchored to the object with the spawner script.</span></span> <span data-ttu-id="96e06-124">Questa operazione può essere modificata assegnando un GameObject al campo di ancoraggio.</span><span class="sxs-lookup"><span data-stu-id="96e06-124">This can be changed by assigning a GameObject to the anchor field.</span></span>

## <a name="example-scene"></a><span data-ttu-id="96e06-125">Scena di esempio</span><span class="sxs-lookup"><span data-stu-id="96e06-125">Example scene</span></span>

<span data-ttu-id="96e06-126">Nelle scene di esempio (assets/MRTK/examples/Demos/UX/Tooltips/scenes), sarà possibile trovare diversi esempi di descrizioni comandi.</span><span class="sxs-lookup"><span data-stu-id="96e06-126">In the example scenes (Assets/MRTK/Examples/Demos/UX/Tooltips/Scenes), you will be able to find various examples of tooltips.</span></span>

![Esempi di descrizione comando](../images/tooltip/MRTK_Tooltip_Examples.png)

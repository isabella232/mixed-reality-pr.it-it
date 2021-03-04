---
title: README_Dock
description: Descrizione per i controlli di ancoraggio.
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: 35adf9c4aac62c468e70081a088eb83867428b4f
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/03/2021
ms.locfileid: "101782767"
---
# <a name="dock"></a><span data-ttu-id="78ffc-104">Ancora</span><span class="sxs-lookup"><span data-stu-id="78ffc-104">Dock</span></span>

![Ancora](../../Images/Dock/MRTK_UX_Dock_Main.png)

<span data-ttu-id="78ffc-106">Questo controllo consente lo spostamento di oggetti all'interno e all'esterno di posizioni predeterminate, per la creazione di tavolozze, scaffali e barre di spostamento.</span><span class="sxs-lookup"><span data-stu-id="78ffc-106">This control enables moving objects in and out of predetermined positions, to create palettes, shelves and navigation bars.</span></span>

## <a name="features"></a><span data-ttu-id="78ffc-107">Funzionalità</span><span class="sxs-lookup"><span data-stu-id="78ffc-107">Features</span></span>

- <span data-ttu-id="78ffc-108">Supporta un numero qualsiasi di posizioni e layout di ancoraggio (funziona perfettamente con [`GridObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.GridObjectCollection) )</span><span class="sxs-lookup"><span data-stu-id="78ffc-108">Supports any number of dock positions and layouts (works great with [`GridObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.GridObjectCollection))</span></span>
- <span data-ttu-id="78ffc-109">Gli oggetti ancorati si spostano automaticamente per creare spazio per i nuovi oggetti</span><span class="sxs-lookup"><span data-stu-id="78ffc-109">Docked objects automatically move away to make space for new objects</span></span>
- <span data-ttu-id="78ffc-110">Gli oggetti vengono ridimensionati per adattarsi allo spazio ancorato, quindi vengono ridimensionati in base alla posizione originale quando vengono trascinati.</span><span class="sxs-lookup"><span data-stu-id="78ffc-110">Objects scale to fit the docked space, then resize to their original position when dragged out.</span></span>

## <a name="getting-started-with-dock"></a><span data-ttu-id="78ffc-111">Introduzione a Dock</span><span class="sxs-lookup"><span data-stu-id="78ffc-111">Getting started with Dock</span></span>

- <span data-ttu-id="78ffc-112">Creare una GameObject con il componente Dock e aggiungere alcuni elementi figlio GameObject.</span><span class="sxs-lookup"><span data-stu-id="78ffc-112">Create a GameObject with the Dock component and add some children GameObjects to it.</span></span>
- <span data-ttu-id="78ffc-113">Aggiungere il componente impostata su DockPosition a ognuno degli elementi figlio.</span><span class="sxs-lookup"><span data-stu-id="78ffc-113">Add the DockPosition component to each of the children.</span></span>
- <span data-ttu-id="78ffc-114">Aggiungere il componente ancorabile a un numero qualsiasi di oggetti nella scena per consentirne l'ancoraggio.</span><span class="sxs-lookup"><span data-stu-id="78ffc-114">Add the Dockable component to any number of objects in the scene to allow them to be docked.</span></span> <span data-ttu-id="78ffc-115">Devono avere anche il [`ObjectManipulator`](xref:Microsoft.MixedReality.Toolkit.UI.ObjectManipulator) componente e un Collider.</span><span class="sxs-lookup"><span data-stu-id="78ffc-115">They must have the [`ObjectManipulator`](xref:Microsoft.MixedReality.Toolkit.UI.ObjectManipulator) component and a Collider as well.</span></span>
- <span data-ttu-id="78ffc-116">*Facoltativo:* usare un [`GridObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.GridObjectCollection) al dock per il layout automatico del DockPositions.</span><span class="sxs-lookup"><span data-stu-id="78ffc-116">*Optional:* use a [`GridObjectCollection`](xref:Microsoft.MixedReality.Toolkit.Utilities.GridObjectCollection) to the Dock to automatically lay out the DockPositions.</span></span>

### <a name="prerequisites"></a><span data-ttu-id="78ffc-117">Prerequisiti</span><span class="sxs-lookup"><span data-stu-id="78ffc-117">Prerequisites</span></span>

- <span data-ttu-id="78ffc-118">Ogni oggetto ancorabile deve avere un Collider con [`ObjectManipulator`](xref:Microsoft.MixedReality.Toolkit.UI.ObjectManipulator) o [`ManipulationHandler`](xref:Microsoft.MixedReality.Toolkit.UI.ManipulationHandler) .</span><span class="sxs-lookup"><span data-stu-id="78ffc-118">Every dockable object must have a collider with an [`ObjectManipulator`](xref:Microsoft.MixedReality.Toolkit.UI.ObjectManipulator) or [`ManipulationHandler`](xref:Microsoft.MixedReality.Toolkit.UI.ManipulationHandler).</span></span>
- <span data-ttu-id="78ffc-119">Se si vuole che un oggetto venga avviato ancorato quando viene caricata la scena, assegnarlo alla proprietà dell'oggetto ancorato di impostata su DockPosition.</span><span class="sxs-lookup"><span data-stu-id="78ffc-119">If you want an object to start Docked when the scene loads, assign it to any DockPosition's docked object property.</span></span>

## <a name="how-it-works"></a><span data-ttu-id="78ffc-120">Funzionamento</span><span class="sxs-lookup"><span data-stu-id="78ffc-120">How it works</span></span>

<span data-ttu-id="78ffc-121">Il componente ancorabile si basa su eventi di manipolazione per consentire l'ancoraggio e la disattivazione di oggetti trascinati in posizioni specifiche.</span><span class="sxs-lookup"><span data-stu-id="78ffc-121">The Dockable component builds upon manipulation events to allow dragged objects to be docked and undocked in specific positions.</span></span> <span data-ttu-id="78ffc-122">Il posizionamento è determinato dal impostata su DockPosition attivato sovrapposto più vicino all'oggetto trascinato, quindi entrambi gli oggetti devono avere Colliders affinché il trigger venga attivato.</span><span class="sxs-lookup"><span data-stu-id="78ffc-122">The placement is determined by the closest overlapping triggered DockPosition to the dragged object, so both objects need to have Colliders for the trigger to activate.</span></span>

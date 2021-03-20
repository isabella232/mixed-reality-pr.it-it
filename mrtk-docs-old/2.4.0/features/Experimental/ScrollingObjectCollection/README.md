---
title: README_ScrollingObject
description: Descrizione che scorre la raccolta di oggetti in MRTK.
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
ms.localizationpriority: medium
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK,
ms.openlocfilehash: a8c81be94d155a125366a390e0032a099e2d80b9
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2021
ms.locfileid: "104692688"
---
# <a name="scrolling-object-collection"></a><span data-ttu-id="df58d-104">Scorrimento della raccolta di oggetti</span><span class="sxs-lookup"><span data-stu-id="df58d-104">Scrolling object collection</span></span>

![Scorrimento della raccolta](../../features/Images/ScrollingCollection/MRTK_UX_ScrollingCollection_Main.jpg)

<span data-ttu-id="df58d-106">ScrollingObjectCollection è una raccolta di oggetti che scorre in modo nativo gli oggetti 3D.</span><span class="sxs-lookup"><span data-stu-id="df58d-106">The ScrollingObjectCollection is an Object Collection that natively scrolls 3D objects.</span></span> <span data-ttu-id="df58d-107">Supporta lo scorrimento di pulsanti stampabili e Interactables, nonché oggetti non interattivi.</span><span class="sxs-lookup"><span data-stu-id="df58d-107">It supports scrolling pressable buttons and Interactables as well as non-interactive objects.</span></span> <span data-ttu-id="df58d-108">Questa raccolta supporta l'input sia vicino che lontano.</span><span class="sxs-lookup"><span data-stu-id="df58d-108">This collection supports both near and far input.</span></span> <span data-ttu-id="df58d-109">Per usare ScrollingObjectCollection, gli oggetti devono usare lo shader standard MRTK per garantire il corretto funzionamento dell'effetto di ritaglio.</span><span class="sxs-lookup"><span data-stu-id="df58d-109">In order to use ScrollingObjectCollection, objects must use the MRTK Standard Shader in order for the clipping effect to work properly.</span></span>

## <a name="getting-started-with-scrolling-object-collection"></a><span data-ttu-id="df58d-110">Introduzione alla raccolta di oggetti di scorrimento</span><span class="sxs-lookup"><span data-stu-id="df58d-110">Getting started with scrolling object collection</span></span>

<span data-ttu-id="df58d-111">Per praticità, sono disponibili due prefabbricati ScrollingObjectCollection da usare.</span><span class="sxs-lookup"><span data-stu-id="df58d-111">For convenience, there are two ScrollingObjectCollection Prefabs available to use.</span></span> <span data-ttu-id="df58d-112">Una viene configurata per funzionare con 32x92mm PressableButton prefabbricates e l'altra per qualsiasi oggetto in un contenitore 32x32x32mm.</span><span class="sxs-lookup"><span data-stu-id="df58d-112">One is configured to work with 32x92mm PressableButton prefabs, and the other is for any object in a 32x32x32mm container.</span></span>

<span data-ttu-id="df58d-113">È sufficiente rilasciarle in una scena, aggiungere gli oggetti desiderati e premere "Updatecollection" per completare la configurazione e il layout della raccolta.</span><span class="sxs-lookup"><span data-stu-id="df58d-113">Simply drop these prefabs into a scene, add the desired objects, and press "UpdateCollection" to finalize the set up and layout of the Collection.</span></span>

### <a name="prerequisites"></a><span data-ttu-id="df58d-114">Prerequisiti</span><span class="sxs-lookup"><span data-stu-id="df58d-114">Prerequisites</span></span>

- <span data-ttu-id="df58d-115">Tutti gli oggetti nella raccolta devono usare lo shader standard MRTK</span><span class="sxs-lookup"><span data-stu-id="df58d-115">All objects in collection must use the MRTK standard shader</span></span>
- <span data-ttu-id="df58d-116">Ogni oggetto nella raccolta deve avere un Collider con un [`NearInteractionTouchable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) .</span><span class="sxs-lookup"><span data-stu-id="df58d-116">Every object in the collection must have a collider with a [`NearInteractionTouchable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable).</span></span> <span data-ttu-id="df58d-117">Tutti i test di collisione sono attualmente eseguiti usando questi Collider; ScrollingObjectCollection non supporta ancora un Collider di backup statico/non in stato di trasferimento.</span><span class="sxs-lookup"><span data-stu-id="df58d-117">All collision testing is currently done using these colliders; ScrollingObjectCollection does not yet support a static/nonmoving backing collider.</span></span>
- <span data-ttu-id="df58d-118">Per tutti gli oggetti della raccolta devono essere presenti le stesse dimensioni. è inoltre possibile ottenere risultati imprevisti se gli oggetti non sono centrati in un gameObject.</span><span class="sxs-lookup"><span data-stu-id="df58d-118">All objects in collection need to be the same size currently, additionally you may get unexpected results if your objects aren't centered in a gameObject.</span></span>
- <span data-ttu-id="df58d-119">Per una superficie facilmente toccabile, le "dimensioni della cella" nella raccolta di scorrimento devono corrispondere alle dimensioni di ogni oggetto nella raccolta.</span><span class="sxs-lookup"><span data-stu-id="df58d-119">For a seamless touchable surface, the 'cell size' in the scrolling collection should match the size of every object in the collection.</span></span>

<span data-ttu-id="df58d-120">Sono previsti requisiti aggiuntivi quando si usano i pulsanti:</span><span class="sxs-lookup"><span data-stu-id="df58d-120">There are additional requirements when using buttons:</span></span>

- <span data-ttu-id="df58d-121">PressableButton. ReleaseOnTouch deve essere disabilitato.</span><span class="sxs-lookup"><span data-stu-id="df58d-121">PressableButton.ReleaseOnTouch must be disabled.</span></span>
- <span data-ttu-id="df58d-122">PhysicalPressEventRouter. InteractableOnClick sono più impostati su EventOnClickCompletion o EventOnPress.</span><span class="sxs-lookup"><span data-stu-id="df58d-122">PhysicalPressEventRouter.InteractableOnClick most be set to EventOnClickCompletion or EventOnPress.</span></span>
- <span data-ttu-id="df58d-123">In fase di modifica, ScrollingObjectCollection è in grado di correggere automaticamente questi componenti.</span><span class="sxs-lookup"><span data-stu-id="df58d-123">At edit time, ScrollingObjectCollection can automatically fix these components.</span></span> <span data-ttu-id="df58d-124">Tuttavia, quando si crea un'istanza dinamica dei prefissi o dei componenti, assicurarsi che queste proprietà siano impostate correttamente.</span><span class="sxs-lookup"><span data-stu-id="df58d-124">But when dynamically instantiating Prefabs or components, make sure these properties are set properly.</span></span>

## <a name="how-it-works"></a><span data-ttu-id="df58d-125">Funzionamento</span><span class="sxs-lookup"><span data-stu-id="df58d-125">How it works</span></span>

<span data-ttu-id="df58d-126">ScrollingObjectCollection sottoscrive se stesso come listener globale per gli eventi di tocco e di puntatore, filtrando gli eventi che corrispondono agli elementi dell'elenco.</span><span class="sxs-lookup"><span data-stu-id="df58d-126">ScrollingObjectCollection subscribes itself as a global listener for Touch and Pointer events, filtering for events that correspond to the items in the list.</span></span> <span data-ttu-id="df58d-127">Inizialmente, la raccolta non esegue alcuna operazione e consente agli eventi di passare agli oggetti figlio, in modo che gli oggetti figlio vengano inseriti e selezionati come previsto.</span><span class="sxs-lookup"><span data-stu-id="df58d-127">Initially, the Collection doesn't do anything and lets events pass through to the child objects, this allows child objects to be poked and selected as expected.</span></span> <span data-ttu-id="df58d-128">Una volta che ScrollingObjectCollection ha riconsiderato un'interazione come "trascinamento", la raccolta inizia a contrassegnare tutti i eventData successivi come utilizzati e inizia a scorrere l'elenco sull'asse del set.</span><span class="sxs-lookup"><span data-stu-id="df58d-128">Once the ScrollingObjectCollection has deemed an interaction as a "drag", the collection begins marking all subsequent eventData as used and begins scrolling the list on the set axis.</span></span>

<span data-ttu-id="df58d-129">Quando si usa il tocco, l'elenco continuerà a scorrere fino a quando il PokePointer non ha superato il piano di tocco davanti all'elenco.</span><span class="sxs-lookup"><span data-stu-id="df58d-129">When using touch, the list will continue to scroll, until the PokePointer has crossed the touch plane in front of the list.</span></span>

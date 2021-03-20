---
title: Ancoraggi nello spazio locali in Unreal
description: Informazioni su come usare, salvare e gestire gli ancoraggi nello spazio presenti nelle applicazioni di realtà mista Unreal.
author: hferrone
ms.author: v-hferrone
ms.date: 12/9/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, realtà mista, sviluppo, funzionalità, documentazione, guide, ologrammi, ancoraggi nello spazio, visore VR realtà mista, visore VR di windows mixed reality, visore per realtà virtuale
ms.openlocfilehash: d44610ea0632dbc93941096007e60e4ae7be53e1
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2021
ms.locfileid: "98009981"
---
# <a name="local-spatial-anchors-in-unreal"></a><span data-ttu-id="1d79c-104">Ancoraggi nello spazio locali in Unreal</span><span class="sxs-lookup"><span data-stu-id="1d79c-104">Local Spatial Anchors in Unreal</span></span>

<span data-ttu-id="1d79c-105">Gli ancoraggi nello spazio salvano gli ologrammi nel mondo reale in più sessioni dell'applicazione come **ARPin**.</span><span class="sxs-lookup"><span data-stu-id="1d79c-105">Spatial anchors save holograms in real-world space between application sessions as **ARPin** s.</span></span> <span data-ttu-id="1d79c-106">Una volta salvati nell'archivio di ancoraggio di HoloLens, è possibile caricare ARPin in sessioni future e scegliere un'opzione di fallback ideale in assenza di connettività Internet.</span><span class="sxs-lookup"><span data-stu-id="1d79c-106">Once saved in the HoloLens' anchor store, ARPin's can be loaded in future sessions and are an ideal fallback option when there's no internet connectivity.</span></span>

> [!NOTE]
> <span data-ttu-id="1d79c-107">Le funzioni di ancoraggio di UE 4.25 sono obsolete nella versione 4.26 e devono essere sostituite con funzioni più recenti.</span><span class="sxs-lookup"><span data-stu-id="1d79c-107">Anchor functions from UE 4.25 are obsolete in 4.26 and should be replaced with newer ones.</span></span> 

> [!IMPORTANT]
> <span data-ttu-id="1d79c-108">Gli ancoraggi locali vengono archiviati nel dispositivo, mentre i dati relativi ad Ancoraggi nello spazio di Azure vengono archiviati nel cloud.</span><span class="sxs-lookup"><span data-stu-id="1d79c-108">Local anchors are stored on device, while Azure Spatial Anchors are stored in the cloud.</span></span> <span data-ttu-id="1d79c-109">Se si vuole usare i servizi cloud di Azure per archiviare gli ancoraggi, è disponibile un documento che fornisce informazioni dettagliate sull'integrazione di [Ancoraggi nello spazio di Azure](unreal-azure-spatial-anchors.md).</span><span class="sxs-lookup"><span data-stu-id="1d79c-109">If you're looking to use Azure cloud services to store your anchors, we have a document that can walk you through integrating [Azure Spatial Anchors](unreal-azure-spatial-anchors.md).</span></span> <span data-ttu-id="1d79c-110">Si noti che è possibile includere ancoraggi locali e ancoraggi di Azure nello stesso progetto senza che si verifichino conflitti.</span><span class="sxs-lookup"><span data-stu-id="1d79c-110">Note that you can have local and Azure anchors in the same project without conflict.</span></span>

## <a name="checking-the-anchor-store"></a><span data-ttu-id="1d79c-111">Verifica dell'archivio degli ancoraggi</span><span class="sxs-lookup"><span data-stu-id="1d79c-111">Checking the anchor store</span></span>

<span data-ttu-id="1d79c-112">Prima di salvare o caricare gli ancoraggi, verifica che l'archivio degli ancoraggi sia pronto.</span><span class="sxs-lookup"><span data-stu-id="1d79c-112">Before saving or loading anchors, you need to check if the anchor store is ready.</span></span>  <span data-ttu-id="1d79c-113">Chiamando una delle funzioni di ancoraggio di HoloLens prima che l'archivio degli ancoraggi sia pronto, la chiamata avrà esito negativo.</span><span class="sxs-lookup"><span data-stu-id="1d79c-113">Calling any of the HoloLens anchor functions before the anchor store is ready won't succeed.</span></span>  

[!INCLUDE[](includes/tabs-sa-1.md)]

## <a name="saving-anchors"></a><span data-ttu-id="1d79c-114">Salvataggio degli ancoraggi</span><span class="sxs-lookup"><span data-stu-id="1d79c-114">Saving anchors</span></span>

<span data-ttu-id="1d79c-115">Quando l'applicazione dispone di un componente che si vuole aggiungere al mondo reale, è possibile salvarlo nell'archivio di ancoraggio con la sequenza illustrata di seguito:</span><span class="sxs-lookup"><span data-stu-id="1d79c-115">Once the application has a component you need to pin to the world, it can be saved to the anchor store with the following sequence:</span></span> 

[!INCLUDE[](includes/tabs-sa-2.md)]

<span data-ttu-id="1d79c-116">Operazioni da eseguire:</span><span class="sxs-lookup"><span data-stu-id="1d79c-116">Breaking this down:</span></span>
1. <span data-ttu-id="1d79c-117">Genera un attore in una posizione nota.</span><span class="sxs-lookup"><span data-stu-id="1d79c-117">Spawn an actor at a known location.</span></span>
2. <span data-ttu-id="1d79c-118">Crea un oggetto **ARPin** con quella posizione e un nome basato sulla classe dell'attore.</span><span class="sxs-lookup"><span data-stu-id="1d79c-118">Create an **ARPin** with that location and a name based on the actor’s class.</span></span> 
3. <span data-ttu-id="1d79c-119">Aggiungi l'attore all'oggetto **ARPin** e salva il segnaposto nell'archivio degli ancoraggi di HoloLens.</span><span class="sxs-lookup"><span data-stu-id="1d79c-119">Add the actor to the **ARPin** and save the pin to the HoloLens anchor store.</span></span>  
    * <span data-ttu-id="1d79c-120">Il nome dell'ancoraggio scelto deve essere univoco. In questo esempio è usato il timestamp corrente.</span><span class="sxs-lookup"><span data-stu-id="1d79c-120">The anchor name you choose must be unique, which in this example is the current timestamp.</span></span> 

4. <span data-ttu-id="1d79c-121">Se l'ancoraggio viene salvato correttamente nell'archivio degli ancoraggi, è possibile ispezionarlo nel portale del dispositivo HoloLens in **System > Map manager > Anchor Files Saved On Device** (Sistema > Gestore mappe > File di ancoraggio salvati sul dispositivo).</span><span class="sxs-lookup"><span data-stu-id="1d79c-121">If the anchor is successfully saved to the anchor store, you can see it in the HoloLens device portal under **System > Map manager > Anchor Files Saved On Device**.</span></span> 

## <a name="loading-anchors"></a><span data-ttu-id="1d79c-122">Caricamento degli ancoraggi</span><span class="sxs-lookup"><span data-stu-id="1d79c-122">Loading anchors</span></span>

<span data-ttu-id="1d79c-123">Quando un'applicazione viene avviata, puoi usare il progetto seguente per ripristinare i componenti nelle rispettive posizioni di ancoraggio:</span><span class="sxs-lookup"><span data-stu-id="1d79c-123">When an application starts, you can use the following blueprint to restore components to their anchor locations:</span></span>

[!INCLUDE[](includes/tabs-sa-3.md)]

<span data-ttu-id="1d79c-124">Operazioni da eseguire:</span><span class="sxs-lookup"><span data-stu-id="1d79c-124">Breaking this down:</span></span>
1. <span data-ttu-id="1d79c-125">Esegui l'iterazione di tutti gli ancoraggi nell'archivio degli ancoraggi.</span><span class="sxs-lookup"><span data-stu-id="1d79c-125">Iterate over all of the anchors in the anchor store.</span></span> 
2. <span data-ttu-id="1d79c-126">Genera un attore in corrispondenza dell'identità.</span><span class="sxs-lookup"><span data-stu-id="1d79c-126">Spawn an actor at identity.</span></span>
3. <span data-ttu-id="1d79c-127">Blocca quell'attore sull'oggetto **ARPin** dall'archivio degli ancoraggi.</span><span class="sxs-lookup"><span data-stu-id="1d79c-127">Pin that actor to the **ARPin** from the anchor store.</span></span>  

    * <span data-ttu-id="1d79c-128">È importante generare l'attore in corrispondenza dell'identità perché l'ancoraggio è responsabile del riposizionamento dell'ologramma nel mondo reale, in base alla posizione in cui è stato salvato.</span><span class="sxs-lookup"><span data-stu-id="1d79c-128">It's important to spawn the actor at identity since the anchor is responsible for repositioning the hologram in the world based on where it was saved.</span></span> <span data-ttu-id="1d79c-129">Qualsiasi trasformazione aggiunta qui aggiungerà un offset all'ancoraggio.</span><span class="sxs-lookup"><span data-stu-id="1d79c-129">Any transform added here will add an offset to the anchor.</span></span> 

<span data-ttu-id="1d79c-130">Eseguiamo anche una query sull'ID di ancoraggio, in modo che sia possibile generare attori diversi in base al nome salvato dell'ancoraggio.</span><span class="sxs-lookup"><span data-stu-id="1d79c-130">The anchor ID is also queried so that different actors can be spawned depending on the anchor’s saved name.</span></span> 

## <a name="removing-anchors"></a><span data-ttu-id="1d79c-131">Rimozione degli ancoraggi</span><span class="sxs-lookup"><span data-stu-id="1d79c-131">Removing anchors</span></span> 

<span data-ttu-id="1d79c-132">Terminate le operazioni su un ancoraggio, è possibile eliminare singoli ancoraggi o l'intero archivio degli ancoraggi con i componenti **Remove ARPin from WMRAnchor Store** (Rimuovi ARPin dall'archivio WMRAnchor) e **Remove All ARPins from WMRAnchor Store** (Rimuovi tutti gli ARPin dall'archivio WMRAnchor).</span><span class="sxs-lookup"><span data-stu-id="1d79c-132">When you're done with an anchor, you can clear individual anchors or the entire anchor store with the **Remove ARPin from WMRAnchor Store** and **Remove All ARPins from WMRAnchor Store** components.</span></span>

[!INCLUDE[](includes/tabs-sa-4.md)]

> [!NOTE]
> <span data-ttu-id="1d79c-133">Tieni presente che gli ancoraggi spaziali sono ancora in versione beta, quindi visualizza di nuovo questa pagina in futuro per verificare se sono presenti informazioni e funzionalità aggiornate.</span><span class="sxs-lookup"><span data-stu-id="1d79c-133">Bear in mind that Spatial Anchors are still in Beta, so be sure to check back for updated information and features.</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="1d79c-134">Successivo checkpoint di sviluppo</span><span class="sxs-lookup"><span data-stu-id="1d79c-134">Next Development Checkpoint</span></span>

<span data-ttu-id="1d79c-135">Se si segue il percorso delineato per lo sviluppo con Unreal, tenere presente che si stanno esplorando i blocchi predefiniti fondamentali di MRTK.</span><span class="sxs-lookup"><span data-stu-id="1d79c-135">If you're following the Unreal development journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="1d79c-136">Da qui, è possibile passare al blocco predefinito successivo:</span><span class="sxs-lookup"><span data-stu-id="1d79c-136">From here, you can continue to the next building block:</span></span> 

> [!div class="nextstepaction"]
> [<span data-ttu-id="1d79c-137">Ancoraggi nello spazio di Azure</span><span class="sxs-lookup"><span data-stu-id="1d79c-137">Azure Spatial Anchors</span></span>](unreal-azure-spatial-anchors.md)

<span data-ttu-id="1d79c-138">In alternativa, passare alle API e alle funzionalità della piattaforma di realtà mista:</span><span class="sxs-lookup"><span data-stu-id="1d79c-138">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="1d79c-139">Fotocamera HoloLens</span><span class="sxs-lookup"><span data-stu-id="1d79c-139">HoloLens camera</span></span>](unreal-hololens-camera.md)

<span data-ttu-id="1d79c-140">È sempre possibile tornare ai [checkpoint per lo sviluppo con Unreal](unreal-development-overview.md#2-core-building-blocks) in qualsiasi momento.</span><span class="sxs-lookup"><span data-stu-id="1d79c-140">You can always go back to the [Unreal development checkpoints](unreal-development-overview.md#2-core-building-blocks) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="1d79c-141">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="1d79c-141">See also</span></span>

* [<span data-ttu-id="1d79c-142">Ancoraggi nello spazio di Azure</span><span class="sxs-lookup"><span data-stu-id="1d79c-142">Azure Spatial Anchors</span></span>](unreal-azure-spatial-anchors.md)
* [<span data-ttu-id="1d79c-143">Ancoraggi nello spazio</span><span class="sxs-lookup"><span data-stu-id="1d79c-143">Spatial anchors</span></span>](../../design/spatial-anchors.md)
* [<span data-ttu-id="1d79c-144">Sistemi di coordinate</span><span class="sxs-lookup"><span data-stu-id="1d79c-144">Coordinate systems</span></span>](../../design/coordinate-systems.md)

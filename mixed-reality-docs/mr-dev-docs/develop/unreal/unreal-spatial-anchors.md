---
title: Ancoraggi nello spazio locali in Unreal
description: Guida all'uso degli ancoraggi nello spazio in Unreal
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, realtà mista, sviluppo, funzionalità, documentazione, guide, ologrammi, ancoraggi nello spazio, visore VR realtà mista, visore VR di windows mixed reality, visore per realtà virtuale
ms.openlocfilehash: 8be1521d44a9dda521c1570d3ac55955e475bc30
ms.sourcegitcommit: 09522ab15a9008ca4d022f9e37fcc98f6eaf6093
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/30/2020
ms.locfileid: "96354502"
---
# <a name="local-spatial-anchors-in-unreal"></a><span data-ttu-id="2e5ab-104">Ancoraggi nello spazio locali in Unreal</span><span class="sxs-lookup"><span data-stu-id="2e5ab-104">Local Spatial Anchors in Unreal</span></span>

## <a name="overview"></a><span data-ttu-id="2e5ab-105">Panoramica</span><span class="sxs-lookup"><span data-stu-id="2e5ab-105">Overview</span></span>

<span data-ttu-id="2e5ab-106">Gli ancoraggi nello spazio consentono di salvare gli ologrammi nel mondo reale in più sessioni dell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="2e5ab-106">Spatial anchors are used to save holograms in real-world space between application sessions.</span></span> <span data-ttu-id="2e5ab-107">Questi vengono esposti tramite Unreal come oggetti **ARPin** e salvati nell'archivio degli ancoraggi di HoloLens che viene caricato nelle sessioni future.</span><span class="sxs-lookup"><span data-stu-id="2e5ab-107">These get surfaced through Unreal as **ARPin** s and saved in the HoloLens’ anchor store, which is loaded in future sessions.</span></span> <span data-ttu-id="2e5ab-108">Gli ancoraggi locali sono ideali come fallback in assenza di connettività Internet.</span><span class="sxs-lookup"><span data-stu-id="2e5ab-108">Local anchors are ideal as a fallback when there is no internet connectivity.</span></span>

> [!NOTE]
> <span data-ttu-id="2e5ab-109">Le funzioni di ancoraggio di UE 4.25 sono obsolete nella versione 4.26 e devono essere sostituite con funzioni più recenti.</span><span class="sxs-lookup"><span data-stu-id="2e5ab-109">Anchor functions from UE 4.25 are obsolete in 4.26 and should be replaced with newer ones.</span></span> 

> [!IMPORTANT]
> <span data-ttu-id="2e5ab-110">Gli ancoraggi locali vengono archiviati nel dispositivo, mentre i dati relativi ad Ancoraggi nello spazio di Azure vengono archiviati nel cloud.</span><span class="sxs-lookup"><span data-stu-id="2e5ab-110">Local anchors are stored on device, while Azure Spatial Anchors are stored in the cloud.</span></span> <span data-ttu-id="2e5ab-111">Se si vuole usare i servizi cloud di Azure per archiviare gli ancoraggi, è disponibile un documento che fornisce informazioni dettagliate sull'integrazione di [Ancoraggi nello spazio di Azure](unreal-azure-spatial-anchors.md).</span><span class="sxs-lookup"><span data-stu-id="2e5ab-111">If you're looking to use Azure cloud services to store your anchors, we have a document that can walk you through integrating [Azure Spatial Anchors](unreal-azure-spatial-anchors.md).</span></span> <span data-ttu-id="2e5ab-112">Si noti che è possibile includere ancoraggi locali e ancoraggi di Azure nello stesso progetto senza che si verifichino conflitti.</span><span class="sxs-lookup"><span data-stu-id="2e5ab-112">Note that you can have local and Azure anchors in the same project without conflict.</span></span>

## <a name="checking-the-anchor-store"></a><span data-ttu-id="2e5ab-113">Verifica dell'archivio degli ancoraggi</span><span class="sxs-lookup"><span data-stu-id="2e5ab-113">Checking the anchor store</span></span>

<span data-ttu-id="2e5ab-114">Prima di salvare o caricare gli ancoraggi, verifica che l'archivio degli ancoraggi sia pronto.</span><span class="sxs-lookup"><span data-stu-id="2e5ab-114">Before saving or loading anchors, you need to check if the anchor store is ready.</span></span>  <span data-ttu-id="2e5ab-115">Se chiami una delle funzioni di ancoraggio di HoloLens prima che l'archivio degli ancoraggi sia pronto, la chiamata avrà esito negativo.</span><span class="sxs-lookup"><span data-stu-id="2e5ab-115">Calling any of the HoloLens anchor functions before the anchor store is ready will not succeed.</span></span>  

[!INCLUDE[](includes/tabs-sa-1.md)]

## <a name="saving-anchors"></a><span data-ttu-id="2e5ab-116">Salvataggio degli ancoraggi</span><span class="sxs-lookup"><span data-stu-id="2e5ab-116">Saving anchors</span></span>

<span data-ttu-id="2e5ab-117">Quando l'applicazione dispone di un componente che deve essere aggiunto al mondo reale, può salvarlo nell'archivio di ancoraggio con la sequenza illustrata di seguito:</span><span class="sxs-lookup"><span data-stu-id="2e5ab-117">Once the application has a component that needs to be pinned to the world, it can be saved to the anchor store with the following sequence:</span></span> 

[!INCLUDE[](includes/tabs-sa-2.md)]

<span data-ttu-id="2e5ab-118">Operazioni da eseguire:</span><span class="sxs-lookup"><span data-stu-id="2e5ab-118">Breaking this down:</span></span>
1. <span data-ttu-id="2e5ab-119">Genera un attore in una posizione nota.</span><span class="sxs-lookup"><span data-stu-id="2e5ab-119">Spawn an actor at a known location.</span></span>
2. <span data-ttu-id="2e5ab-120">Crea un oggetto **ARPin** con quella posizione e un nome basato sulla classe dell'attore.</span><span class="sxs-lookup"><span data-stu-id="2e5ab-120">Create an **ARPin** with that location and a name based on the actor’s class.</span></span> 
3. <span data-ttu-id="2e5ab-121">Aggiungi l'attore all'oggetto **ARPin** e salva il segnaposto nell'archivio degli ancoraggi di HoloLens.</span><span class="sxs-lookup"><span data-stu-id="2e5ab-121">Add the actor to the **ARPin** and save the pin to the HoloLens anchor store.</span></span>  
    * <span data-ttu-id="2e5ab-122">Il nome dell'ancoraggio scelto deve essere univoco. In questo esempio è usato il timestamp corrente.</span><span class="sxs-lookup"><span data-stu-id="2e5ab-122">The anchor name you choose must be unique, which in this example is the current timestamp.</span></span> 

4. <span data-ttu-id="2e5ab-123">Se l'ancoraggio viene salvato correttamente nell'archivio degli ancoraggi, puoi ispezionarlo nel portale del dispositivo HoloLens in **System > Map manager > Anchor Files Saved On Device** (Sistema > Gestore mappe > File di ancoraggio salvati sul dispositivo).</span><span class="sxs-lookup"><span data-stu-id="2e5ab-123">If the anchor is successfully saved to the anchor store, you can be inspect it in the HoloLens device portal under **System > Map manager > Anchor Files Saved On Device**.</span></span> 

## <a name="loading-anchors"></a><span data-ttu-id="2e5ab-124">Caricamento degli ancoraggi</span><span class="sxs-lookup"><span data-stu-id="2e5ab-124">Loading anchors</span></span>

<span data-ttu-id="2e5ab-125">Quando un'applicazione viene avviata, puoi usare il progetto seguente per ripristinare i componenti nelle rispettive posizioni di ancoraggio:</span><span class="sxs-lookup"><span data-stu-id="2e5ab-125">When an application starts, you can use the following blueprint to restore components to their anchor locations:</span></span>

[!INCLUDE[](includes/tabs-sa-3.md)]

<span data-ttu-id="2e5ab-126">Operazioni da eseguire:</span><span class="sxs-lookup"><span data-stu-id="2e5ab-126">Breaking this down:</span></span>
1. <span data-ttu-id="2e5ab-127">Esegui l'iterazione di tutti gli ancoraggi nell'archivio degli ancoraggi.</span><span class="sxs-lookup"><span data-stu-id="2e5ab-127">Iterate over all of the anchors in the anchor store.</span></span> 
2. <span data-ttu-id="2e5ab-128">Genera un attore in corrispondenza dell'identità.</span><span class="sxs-lookup"><span data-stu-id="2e5ab-128">Spawn an actor at identity.</span></span>
3. <span data-ttu-id="2e5ab-129">Blocca quell'attore sull'oggetto **ARPin** dall'archivio degli ancoraggi.</span><span class="sxs-lookup"><span data-stu-id="2e5ab-129">Pin that actor to the **ARPin** from the anchor store.</span></span>  

    * <span data-ttu-id="2e5ab-130">È importante generare l'attore in corrispondenza dell'identità perché l'ancoraggio è responsabile del riposizionamento dell'ologramma nel mondo reale, in base alla posizione in cui è stato salvato.</span><span class="sxs-lookup"><span data-stu-id="2e5ab-130">It's important to spawn the actor at identity since the anchor is responsible for repositioning the hologram in the world based on where it was saved.</span></span> <span data-ttu-id="2e5ab-131">Qualsiasi trasformazione aggiunta qui aggiungerà un offset all'ancoraggio.</span><span class="sxs-lookup"><span data-stu-id="2e5ab-131">Any transform added here will add an offset to the anchor.</span></span> 

<span data-ttu-id="2e5ab-132">Eseguiamo anche una query sull'ID di ancoraggio, in modo che sia possibile generare attori diversi in base al nome salvato dell'ancoraggio.</span><span class="sxs-lookup"><span data-stu-id="2e5ab-132">The anchor ID is also queried so that different actors can be spawned depending on the anchor’s saved name.</span></span> 

## <a name="removing-anchors"></a><span data-ttu-id="2e5ab-133">Rimozione degli ancoraggi</span><span class="sxs-lookup"><span data-stu-id="2e5ab-133">Removing anchors</span></span> 

<span data-ttu-id="2e5ab-134">Terminate le operazioni su un ancoraggio, puoi eliminare singoli ancoraggi o l'intero archivio degli ancoraggi con i componenti **Remove ARPin from WMRAnchor Store** (Rimuovi ARPin dall'archivio WMRAnchor) e **Remove All ARPins from WMRAnchor Store** (Rimuovi tutti gli ARPin dall'archivio WMRAnchor).</span><span class="sxs-lookup"><span data-stu-id="2e5ab-134">When you're done with an anchor you can clear individual anchors or the entire anchor store with the **Remove ARPin from WMRAnchor Store** and **Remove All ARPins from WMRAnchor Store** components.</span></span>

[!INCLUDE[](includes/tabs-sa-4.md)]

> [!NOTE]
> <span data-ttu-id="2e5ab-135">Tieni presente che gli ancoraggi spaziali sono ancora in versione beta, quindi visualizza di nuovo questa pagina in futuro per verificare se sono presenti informazioni e funzionalità aggiornate.</span><span class="sxs-lookup"><span data-stu-id="2e5ab-135">Bear in mind that Spatial Anchors are still in Beta, so be sure to check back for updated information and features.</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="2e5ab-136">Successivo checkpoint di sviluppo</span><span class="sxs-lookup"><span data-stu-id="2e5ab-136">Next Development Checkpoint</span></span>

<span data-ttu-id="2e5ab-137">Se si segue il percorso di checkpoint per lo sviluppo con Unreal che è stato delineato, si stanno esplorando i blocchi predefiniti fondamentali di MRTK.</span><span class="sxs-lookup"><span data-stu-id="2e5ab-137">If you're following the Unreal development checkpoint journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="2e5ab-138">Da qui è possibile passare al blocco predefinito successivo:</span><span class="sxs-lookup"><span data-stu-id="2e5ab-138">From here, you can proceed to the next building block:</span></span> 

> [!div class="nextstepaction"]
> [<span data-ttu-id="2e5ab-139">Ancoraggi nello spazio di Azure</span><span class="sxs-lookup"><span data-stu-id="2e5ab-139">Azure Spatial Anchors</span></span>](unreal-azure-spatial-anchors.md)

<span data-ttu-id="2e5ab-140">In alternativa, passare alle API e alle funzionalità della piattaforma di realtà mista:</span><span class="sxs-lookup"><span data-stu-id="2e5ab-140">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="2e5ab-141">Fotocamera HoloLens</span><span class="sxs-lookup"><span data-stu-id="2e5ab-141">HoloLens camera</span></span>](unreal-hololens-camera.md)

<span data-ttu-id="2e5ab-142">È sempre possibile tornare ai [checkpoint per lo sviluppo con Unreal](unreal-development-overview.md#2-core-building-blocks) in qualsiasi momento.</span><span class="sxs-lookup"><span data-stu-id="2e5ab-142">You can always go back to the [Unreal development checkpoints](unreal-development-overview.md#2-core-building-blocks) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="2e5ab-143">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="2e5ab-143">See also</span></span>
* [<span data-ttu-id="2e5ab-144">Ancoraggi nello spazio di Azure</span><span class="sxs-lookup"><span data-stu-id="2e5ab-144">Azure Spatial Anchors</span></span>](unreal-azure-spatial-anchors.md)
* [<span data-ttu-id="2e5ab-145">Ancoraggi nello spazio</span><span class="sxs-lookup"><span data-stu-id="2e5ab-145">Spatial anchors</span></span>](../../design/spatial-anchors.md)
* [<span data-ttu-id="2e5ab-146">Sistemi di coordinate</span><span class="sxs-lookup"><span data-stu-id="2e5ab-146">Coordinate systems</span></span>](../../design/coordinate-systems.md)

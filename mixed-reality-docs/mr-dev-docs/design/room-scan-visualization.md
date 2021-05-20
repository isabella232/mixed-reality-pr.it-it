---
title: Visualizzazione della scansione dello spazio
description: Le applicazioni che richiedono il mapping spaziale usano il dispositivo per raccogliere dati nel tempo e tra le sessioni.
author: mattzmsft
ms.author: alexpf
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, Modelli di app, progettazione, HoloLens, scansione della stanza, mapping spaziale, mesh, visore VR di realtà mista, visore VR di realtà mista windows, visore VR di realtà virtuale, HoloLens
ms.openlocfilehash: 87312a5d5361ac0e8c24a622cf69fe3e9b147ff5
ms.sourcegitcommit: 8f141a843bcfc57e1b18cc606292186b8ac72641
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/19/2021
ms.locfileid: "110196406"
---
# <a name="room-scan-visualization"></a><span data-ttu-id="7d0f3-104">Visualizzazione della scansione dello spazio</span><span class="sxs-lookup"><span data-stu-id="7d0f3-104">Room scan visualization</span></span>

<span data-ttu-id="7d0f3-105">Le applicazioni che richiedono il mapping spaziale si basano sul dispositivo per raccogliere dati nel tempo e tra sessioni.</span><span class="sxs-lookup"><span data-stu-id="7d0f3-105">Applications that require spatial mapping rely on the device to collect data over time and across sessions.</span></span> <span data-ttu-id="7d0f3-106">La completezza e la qualità dei dati di mapping dipendono da molti fattori, tra cui la quantità di esplorazione eseguita dall'utente, il tempo passato dall'esplorazione e se oggetti come mobili e porte sono stati spostati dopo la scansione dell'area da parte del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="7d0f3-106">The completeness and quality of the mapping data depends on many factors, including the amount of exploration the user has done, how much time has passed since the exploration, and whether objects such as furniture and doors have moved since the device scanned the area.</span></span>

<span data-ttu-id="7d0f3-107">Per garantire dati di mapping spaziale utili, gli sviluppatori di applicazioni hanno diverse opzioni:</span><span class="sxs-lookup"><span data-stu-id="7d0f3-107">To ensure useful spatial mapping data, applications developers have several options:</span></span>
* <span data-ttu-id="7d0f3-108">Fare affidamento su ciò che potrebbe essere già stato raccolto.</span><span class="sxs-lookup"><span data-stu-id="7d0f3-108">Rely on what may have already been collected.</span></span> <span data-ttu-id="7d0f3-109">Questi dati potrebbero essere inizialmente incompleti.</span><span class="sxs-lookup"><span data-stu-id="7d0f3-109">This data may be incomplete initially.</span></span>
* <span data-ttu-id="7d0f3-110">Chiedere all'utente di usare il movimento di fiore per raggiungere la Windows Mixed Reality home e quindi esplorare l'area da usare per l'esperienza.</span><span class="sxs-lookup"><span data-stu-id="7d0f3-110">Ask the user to use the bloom gesture to get to the Windows Mixed Reality home and then explore the area they wish to use for the experience.</span></span> <span data-ttu-id="7d0f3-111">Possono usare il tocco per verificare che tutta l'area necessaria sia nota al dispositivo.</span><span class="sxs-lookup"><span data-stu-id="7d0f3-111">They can use air-tap to confirm that all the necessary area is known to the device.</span></span>
* <span data-ttu-id="7d0f3-112">Creare un'esperienza di esplorazione personalizzata nella propria applicazione.</span><span class="sxs-lookup"><span data-stu-id="7d0f3-112">Build a custom exploration experience in their own application.</span></span>

<span data-ttu-id="7d0f3-113">In tutti questi casi, i dati effettivi raccolti durante l'esplorazione vengono archiviati dal sistema e l'applicazione non deve eseguire questa operazione.</span><span class="sxs-lookup"><span data-stu-id="7d0f3-113">In all these cases, the actual data gathered during the exploration is stored by the system and the application doesn't need to do this.</span></span> <span data-ttu-id="7d0f3-114">Se si desidera vedere la visualizzazione della scansione della stanza in azione, vedere la demo video Progettazione di **ologrammi - Consapevolezza** spaziale di seguito:</span><span class="sxs-lookup"><span data-stu-id="7d0f3-114">If you'd like to see room scan visualization in action, check out our **Designing Holograms - Spatial Awareness** video demo below:</span></span>

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Microsofts-Designing-Holograms-Spatial-Awareness-Chapter/player]

<span data-ttu-id="7d0f3-115">*Questo video è stato tratto dall'app "Progettazione di ologrammi" HoloLens 2 app. Scaricare e usufruire dell'esperienza completa [qui.](https://aka.ms/dhapp)*</span><span class="sxs-lookup"><span data-stu-id="7d0f3-115">*This video was taken from the "Designing Holograms" HoloLens 2 app. Download and enjoy the full experience [here](https://aka.ms/dhapp).*</span></span>

## <a name="device-support"></a><span data-ttu-id="7d0f3-116">Supporto di dispositivi</span><span class="sxs-lookup"><span data-stu-id="7d0f3-116">Device support</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="7d0f3-117"><strong>Funzionalità</strong></span><span class="sxs-lookup"><span data-stu-id="7d0f3-117"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="7d0f3-118"><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="7d0f3-118"><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="7d0f3-119"><a href="../discover/immersive-headset-hardware-details.md"><strong>Visori VR immersive</strong></a></span><span class="sxs-lookup"><span data-stu-id="7d0f3-119"><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="7d0f3-120">Visualizzazione della scansione dello spazio</span><span class="sxs-lookup"><span data-stu-id="7d0f3-120">Room scan visualization</span></span></td>
        <td><span data-ttu-id="7d0f3-121">✔️</span><span class="sxs-lookup"><span data-stu-id="7d0f3-121">✔️</span></span></td>
        <td>❌</td>
    </tr>
</table>

## <a name="building-a-custom-scanning-experience"></a><span data-ttu-id="7d0f3-122">Creazione di un'esperienza di analisi personalizzata</span><span class="sxs-lookup"><span data-stu-id="7d0f3-122">Building a custom scanning experience</span></span>

<span data-ttu-id="7d0f3-123">Le applicazioni possono analizzare i dati di mapping spaziale all'inizio dell'esperienza per valutare se vogliono che l'utente eserciti passaggi aggiuntivi per migliorarne la completezza e la qualità.</span><span class="sxs-lookup"><span data-stu-id="7d0f3-123">Applications may analyze the spatial mapping data at the start of the experience to judge whether they want the user to do extra steps to improve its completeness and quality.</span></span> <span data-ttu-id="7d0f3-124">Se l'analisi indica che la qualità deve essere migliorata, gli sviluppatori devono fornire una visualizzazione da sovrapporre al mondo per indicare:</span><span class="sxs-lookup"><span data-stu-id="7d0f3-124">If analysis indicates quality should be improved, developers should provide a visualization to overlay on the world to indicate:</span></span>
* <span data-ttu-id="7d0f3-125">La quantità del volume totale nelle vicinanze degli utenti deve far parte dell'esperienza</span><span class="sxs-lookup"><span data-stu-id="7d0f3-125">How much of the total volume in the users vicinity needs to be part of the experience</span></span>
* <span data-ttu-id="7d0f3-126">Dove l'utente deve andare per migliorare i dati</span><span class="sxs-lookup"><span data-stu-id="7d0f3-126">Where the user should go to improve data</span></span>

<span data-ttu-id="7d0f3-127">Gli utenti non sanno cosa rende un'analisi "buona".</span><span class="sxs-lookup"><span data-stu-id="7d0f3-127">Users don't know what makes a "good" scan.</span></span> <span data-ttu-id="7d0f3-128">Devono essere visualizzati o indicati gli elementi da cercare se viene richiesto di valutare un'analisi: flatness, distanza dalle pareti effettive e così via.</span><span class="sxs-lookup"><span data-stu-id="7d0f3-128">They need to be shown or told what to look for if they’re asked to evaluate a scan – flatness, distance from actual walls, and so on.</span></span> <span data-ttu-id="7d0f3-129">Lo sviluppatore deve implementare un ciclo di feedback che includa l'aggiornamento dei dati di mapping spaziale durante la fase di analisi o esplorazione.</span><span class="sxs-lookup"><span data-stu-id="7d0f3-129">The developer should implement a feedback loop that includes refreshing the spatial mapping data during the scanning or exploration phase.</span></span>

<span data-ttu-id="7d0f3-130">In molti casi, è meglio indicare all'utente cosa deve fare per ottenere la qualità di analisi necessaria.</span><span class="sxs-lookup"><span data-stu-id="7d0f3-130">In many cases, it's best to tell the user what they need to do to get the necessary scan quality.</span></span> <span data-ttu-id="7d0f3-131">Ad esempio, osservare il controsoffitto, guardare dietro i mobili e così via.</span><span class="sxs-lookup"><span data-stu-id="7d0f3-131">For example, look at the ceiling, look behind furniture, and so on.</span></span>

## <a name="cached-versus-continuous-spatial-mapping"></a><span data-ttu-id="7d0f3-132">Mapping spaziale continuo e memorizzato nella cache</span><span class="sxs-lookup"><span data-stu-id="7d0f3-132">Cached versus continuous spatial mapping</span></span>

<span data-ttu-id="7d0f3-133">I dati di mapping spaziale sono le applicazioni di origine dati più pesanti che possono utilizzare.</span><span class="sxs-lookup"><span data-stu-id="7d0f3-133">The spatial mapping data is the most heavy weight data source applications can consume.</span></span> <span data-ttu-id="7d0f3-134">Per evitare problemi di prestazioni, ad esempio frame eliminati o stuttering, l'utilizzo di questi dati deve essere eseguito con attenzione.</span><span class="sxs-lookup"><span data-stu-id="7d0f3-134">To avoid performance issues such as dropped frames or stuttering, consumption of this data should be done carefully.</span></span>

<span data-ttu-id="7d0f3-135">La scansione attiva durante un'esperienza può essere utile e dannosa, quindi è necessario decidere quale metodo usare in base all'esperienza.</span><span class="sxs-lookup"><span data-stu-id="7d0f3-135">Active scanning during an experience can be both beneficial and detrimental, so you'll need to decide which method to use based on the experience.</span></span>

### <a name="cached-spatial-mapping"></a><span data-ttu-id="7d0f3-136">Mapping spaziale memorizzato nella cache</span><span class="sxs-lookup"><span data-stu-id="7d0f3-136">Cached spatial mapping</span></span>

<span data-ttu-id="7d0f3-137">Se sono presenti dati di mapping spaziale memorizzati nella cache, l'applicazione in genere prende uno snapshot dei dati di mapping spaziale e lo usa durante l'esperienza.</span><span class="sxs-lookup"><span data-stu-id="7d0f3-137">If there's cached spatial mapping data, the application typically takes a snapshot of the spatial mapping data and uses this snapshot during the experience.</span></span>

<span data-ttu-id="7d0f3-138">**Vantaggi**</span><span class="sxs-lookup"><span data-stu-id="7d0f3-138">**Benefits**</span></span>
* <span data-ttu-id="7d0f3-139">Riduzione del sovraccarico del sistema durante l'esecuzione dell'esperienza, con un notevole miglioramento delle prestazioni di potenza, termica e cpu.</span><span class="sxs-lookup"><span data-stu-id="7d0f3-139">Reduced overhead on the system while the experience is running leading to dramatic power, thermal, and cpu performance gains.</span></span>
* <span data-ttu-id="7d0f3-140">Implementazione più semplice dell'esperienza principale poiché non viene interrotta dalle modifiche nei dati spaziali.</span><span class="sxs-lookup"><span data-stu-id="7d0f3-140">A simpler implementation of the main experience since it is not interrupted by changes in the spatial data.</span></span>
* <span data-ttu-id="7d0f3-141">Un costo una sola volta per qualsiasi post-elaborazione dei dati spaziali per la fisica, la grafica e altri scopi.</span><span class="sxs-lookup"><span data-stu-id="7d0f3-141">A single one time cost on any post processing of the spatial data for physics, graphics, and other purposes.</span></span>

<span data-ttu-id="7d0f3-142">**Svantaggi**</span><span class="sxs-lookup"><span data-stu-id="7d0f3-142">**Drawbacks**</span></span>
* <span data-ttu-id="7d0f3-143">Lo spostamento di oggetti reali o persone non viene riflessa dai dati memorizzati nella cache.</span><span class="sxs-lookup"><span data-stu-id="7d0f3-143">The movement of real world objects or people is not reflected by the cached data.</span></span> <span data-ttu-id="7d0f3-144">Ad esempio, l'applicazione potrebbe considerare una porta aperta quando è chiusa.</span><span class="sxs-lookup"><span data-stu-id="7d0f3-144">for example, the application might consider a door open when it's closed now.</span></span>
* <span data-ttu-id="7d0f3-145">Potenzialmente più memoria dell'applicazione per mantenere la versione memorizzata nella cache dei dati.</span><span class="sxs-lookup"><span data-stu-id="7d0f3-145">Potentially more application memory to maintain the cached version of the data.</span></span>

<span data-ttu-id="7d0f3-146">Un buon caso per questo metodo è un ambiente controllato o un gioco da tavolo principale.</span><span class="sxs-lookup"><span data-stu-id="7d0f3-146">A good case for this method is a controlled environment or a table top game.</span></span>

### <a name="continuous-spatial-mapping"></a><span data-ttu-id="7d0f3-147">Mapping spaziale continuo</span><span class="sxs-lookup"><span data-stu-id="7d0f3-147">Continuous spatial mapping</span></span>

<span data-ttu-id="7d0f3-148">Alcune applicazioni possono basarsi sull'analisi continua per aggiornare i dati di mapping spaziale.</span><span class="sxs-lookup"><span data-stu-id="7d0f3-148">Certain applications may rely on continues scanning to refresh spatial mapping data.</span></span>

<span data-ttu-id="7d0f3-149">**Vantaggi**</span><span class="sxs-lookup"><span data-stu-id="7d0f3-149">**Benefits**</span></span>
* <span data-ttu-id="7d0f3-150">Non è necessario creare in anticipo un'esperienza di analisi o esplorazione separata nell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="7d0f3-150">You don't need to build in a separate scanning or exploration experience upfront in your application.</span></span>
* <span data-ttu-id="7d0f3-151">Lo spostamento di oggetti reali può essere riflessa dal gioco, anche se con un certo ritardo.</span><span class="sxs-lookup"><span data-stu-id="7d0f3-151">The movement of real world objects can be reflected by the game, although with some delay.</span></span>

<span data-ttu-id="7d0f3-152">**Svantaggi**</span><span class="sxs-lookup"><span data-stu-id="7d0f3-152">**Drawbacks**</span></span>
* <span data-ttu-id="7d0f3-153">Maggiore complessità nell'implementazione dell'esperienza principale.</span><span class="sxs-lookup"><span data-stu-id="7d0f3-153">Higher complexity in the implementation of the main experience.</span></span>
* <span data-ttu-id="7d0f3-154">Potenziale sovraccarico dovuto all'elaborazione grafica e fisica aggiuntiva, in quanto le modifiche devono essere inserite in modo incrementale da questi sistemi.</span><span class="sxs-lookup"><span data-stu-id="7d0f3-154">Potential overhead from the extra graphic and physics processing, as changes need to be incrementally ingested by these systems.</span></span>
* <span data-ttu-id="7d0f3-155">Maggiore impatto su potenza, termica e CPU.</span><span class="sxs-lookup"><span data-stu-id="7d0f3-155">Higher power, thermal, and CPU impact.</span></span>

<span data-ttu-id="7d0f3-156">Un buon caso per questo metodo è quello in cui si prevede che gli ologrammi interagiscano con gli oggetti in movimento, ad esempio un'auto olografica che guida sul piano può voler entrare in una porta a seconda che sia aperta o chiusa.</span><span class="sxs-lookup"><span data-stu-id="7d0f3-156">A good case for this method is one where holograms are expected to interact with moving objects, for example, a holographic car that drives on the floor may want to bump into a door depending on whether it's open or closed.</span></span>

## <a name="see-also"></a><span data-ttu-id="7d0f3-157">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="7d0f3-157">See also</span></span>

* [<span data-ttu-id="7d0f3-158">Mapping spaziale</span><span class="sxs-lookup"><span data-stu-id="7d0f3-158">Spatial mapping</span></span>](spatial-mapping.md)
* [<span data-ttu-id="7d0f3-159">Sistemi di coordinate</span><span class="sxs-lookup"><span data-stu-id="7d0f3-159">Coordinate systems</span></span>](coordinate-systems.md)
* [<span data-ttu-id="7d0f3-160">Progettazione dell'audio spaziale</span><span class="sxs-lookup"><span data-stu-id="7d0f3-160">Spatial sound design</span></span>](spatial-sound-design.md)
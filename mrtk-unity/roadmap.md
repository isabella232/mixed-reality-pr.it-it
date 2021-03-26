---
title: Roadmap
description: documentazione per la struttura della roadmap di MRTK.
author: polar-kev
ms.author: kesemple
ms.date: 03/03/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK
ms.openlocfilehash: 767fd41287c68812d51826d32a99296b9cd33018
ms.sourcegitcommit: ac315c1d35f2b9c431e79bc3f1212215301bb867
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105550901"
---
# <a name="roadmap"></a><span data-ttu-id="ef45e-104">Roadmap</span><span class="sxs-lookup"><span data-stu-id="ef45e-104">Roadmap</span></span>

<span data-ttu-id="ef45e-105">Questo documento descrive la roadmap del Toolkit di realtà mista.</span><span class="sxs-lookup"><span data-stu-id="ef45e-105">This document outlines the roadmap of the Mixed Reality Toolkit.</span></span> <span data-ttu-id="ef45e-106">Si noti che di seguito sono riportate le stime dei lavori nelle date di sviluppo e di destinazione.</span><span class="sxs-lookup"><span data-stu-id="ef45e-106">Please note that the following reflects work that is in development and target dates reflect estimates.</span></span>

## <a name="current-release"></a><span data-ttu-id="ef45e-107">Versione corrente</span><span class="sxs-lookup"><span data-stu-id="ef45e-107">Current release</span></span>

<span data-ttu-id="ef45e-108">Microsoft Mixed Reality Toolkit v 2.6</span><span class="sxs-lookup"><span data-stu-id="ef45e-108">Microsoft Mixed Reality Toolkit v2.6</span></span>

## <a name="upcoming-releases"></a><span data-ttu-id="ef45e-109">Prossime versioni</span><span class="sxs-lookup"><span data-stu-id="ef45e-109">Upcoming releases</span></span>

| <span data-ttu-id="ef45e-110">Prodotto</span><span class="sxs-lookup"><span data-stu-id="ef45e-110">Product</span></span> | <span data-ttu-id="ef45e-111">Descrizione</span><span class="sxs-lookup"><span data-stu-id="ef45e-111">Description</span></span> | <span data-ttu-id="ef45e-112">Sequenza temporale</span><span class="sxs-lookup"><span data-stu-id="ef45e-112">Timeline</span></span> | <span data-ttu-id="ef45e-113">Lavagna del progetto</span><span class="sxs-lookup"><span data-stu-id="ef45e-113">Project board</span></span> |
| --- | --- | --- | --- |
| [<span data-ttu-id="ef45e-114">MRTK V 2.7</span><span class="sxs-lookup"><span data-stu-id="ef45e-114">MRTK V2.7</span></span>](#270) | <span data-ttu-id="ef45e-115">Iterazione successiva di MRTK</span><span class="sxs-lookup"><span data-stu-id="ef45e-115">Next iteration of MRTK</span></span> | <span data-ttu-id="ef45e-116">Maggio 2021</span><span class="sxs-lookup"><span data-stu-id="ef45e-116">May 2021</span></span> | https://github.com/microsoft/MixedRealityToolkit-Unity/milestone/14 |

<span data-ttu-id="ef45e-117">Le versioni sono incentrate sui temi (ad esempio, aree funzionali di grandi dimensioni) e sono pianificati per essere eseguiti approssimativamente ogni 8-12 settimane.</span><span class="sxs-lookup"><span data-stu-id="ef45e-117">Releases are centered around themes (ex: large feature areas) and are scheduled to occur approximately every 8-12 weeks.</span></span>

<span data-ttu-id="ef45e-118">I dettagli della versione, inclusi gli elementi di backlog, sono reperibili nelle [pagine dell'attività cardine di GitHub](https://github.com/Microsoft/MixedRealityToolkit-Unity/milestones).</span><span class="sxs-lookup"><span data-stu-id="ef45e-118">Release details, including backlog items, can be found on the [GitHub milestone pages](https://github.com/Microsoft/MixedRealityToolkit-Unity/milestones).</span></span> <span data-ttu-id="ef45e-119">Il set completo di problemi aperti è disponibile anche in [GitHub](https://github.com/microsoft/MixedRealityToolkit-Unity/issues).</span><span class="sxs-lookup"><span data-stu-id="ef45e-119">The complete set of open issues can also be found on [GitHub](https://github.com/microsoft/MixedRealityToolkit-Unity/issues).</span></span>

## <a name="mixed-reality-toolkit-mrtk-roadmap"></a><span data-ttu-id="ef45e-120">Guida di orientamento a Mixed Reality Toolkit (MRTK)</span><span class="sxs-lookup"><span data-stu-id="ef45e-120">Mixed Reality Toolkit (MRTK) roadmap</span></span>

<span data-ttu-id="ef45e-121">Il Toolkit per la realtà mista è progettato per essere cross MR/AR/VR/XR Platform by Design.</span><span class="sxs-lookup"><span data-stu-id="ef45e-121">The Mixed Reality Toolkit is built to be cross MR/AR/VR/XR platform by design.</span></span> <span data-ttu-id="ef45e-122">Il Toolkit supporta attualmente Unity 2019.4. x e Unity 2018.4. x.</span><span class="sxs-lookup"><span data-stu-id="ef45e-122">The toolkit currently supports Unity 2019.4.x and Unity 2018.4.x.</span></span>

> <span data-ttu-id="ef45e-123">Quando Unity rilascia un prodotto LTS (supporto a lungo termine), il Toolkit di realtà mista viene aggiornato alla versione LTS.</span><span class="sxs-lookup"><span data-stu-id="ef45e-123">When Unity releases an LTS (Long Term Support) product, the Mixed Reality Toolkit will update to the LTS release.</span></span> <span data-ttu-id="ef45e-124">Sebbene il Toolkit di realtà mista venga eseguito nella versione più recente del ramo Tech non beta (ad esempio, 2020,1), non è ufficialmente supportato.</span><span class="sxs-lookup"><span data-stu-id="ef45e-124">Although the Mixed Reality Toolkit runs on the latest non-beta (ex: 2020.1) tech branch version of Unity, it is not officially supported.</span></span>

### <a name="270"></a><span data-ttu-id="ef45e-125">2.7.0</span><span class="sxs-lookup"><span data-stu-id="ef45e-125">2.7.0</span></span>

<span data-ttu-id="ef45e-126">Attualmente stiamo pianificando la versione 2.7.0 e avrai a disposizione più aggiornamenti.</span><span class="sxs-lookup"><span data-stu-id="ef45e-126">We are currently planning the 2.7.0 release and will have more updates for you soon!</span></span>
<span data-ttu-id="ef45e-127">Per lo stato più recente della versione, visitare la pagina relativa all' [attività cardine](https://github.com/microsoft/MixedRealityToolkit-Unity/milestone/14).</span><span class="sxs-lookup"><span data-stu-id="ef45e-127">For the latest status of the release, please visit the [milestone page](https://github.com/microsoft/MixedRealityToolkit-Unity/milestone/14).</span></span>

<span data-ttu-id="ef45e-128">Stato: pianificazione</span><span class="sxs-lookup"><span data-stu-id="ef45e-128">Status: Planning</span></span>

<span data-ttu-id="ef45e-129">Sequenza temporale di destinazione: 2021 maggio</span><span class="sxs-lookup"><span data-stu-id="ef45e-129">Target Timeline: May 2021</span></span>

<span data-ttu-id="ef45e-130">Temi:</span><span class="sxs-lookup"><span data-stu-id="ef45e-130">Themes:</span></span>

- <span data-ttu-id="ef45e-131">Stability</span><span class="sxs-lookup"><span data-stu-id="ef45e-131">Stability</span></span> 
- <span data-ttu-id="ef45e-132">Espansione della piattaforma: OpenXR</span><span class="sxs-lookup"><span data-stu-id="ef45e-132">Platform Expansion: OpenXR</span></span>
- <span data-ttu-id="ef45e-133">Esperienza dell'utente</span><span class="sxs-lookup"><span data-stu-id="ef45e-133">User Experience</span></span>
- <span data-ttu-id="ef45e-134">Formazione per sviluppatori</span><span class="sxs-lookup"><span data-stu-id="ef45e-134">Developer Education</span></span>
- <span data-ttu-id="ef45e-135">Packaging</span><span class="sxs-lookup"><span data-stu-id="ef45e-135">Packaging</span></span>

<span data-ttu-id="ef45e-136">**Stabilità**</span><span class="sxs-lookup"><span data-stu-id="ef45e-136">**Stability**</span></span>

<span data-ttu-id="ef45e-137">La qualità e la stabilità sono la massima priorità per questo e tutte le versioni di Microsoft Mixed Reality Toolkit.</span><span class="sxs-lookup"><span data-stu-id="ef45e-137">Quality and stability are the top priority for this and all Microsoft Mixed Reality Toolkit releases.</span></span> <span data-ttu-id="ef45e-138">Si continuerà ad assegnare una priorità ai problemi dei clienti e dei partner che influiscano sulla stabilità dei componenti di MRTK.</span><span class="sxs-lookup"><span data-stu-id="ef45e-138">We will continue to prioritize customer and partner issues that impact the stability of MRTK components.</span></span>

<span data-ttu-id="ef45e-139">**Espansione della piattaforma: OpenXR**</span><span class="sxs-lookup"><span data-stu-id="ef45e-139">**Platform Expansion: OpenXR**</span></span>

<span data-ttu-id="ef45e-140">Il team di MRTK supporta il futuro aperto della realtà mista tramite [OpenXR](https://techcommunity.microsoft.com/t5/mixed-reality-blog/moving-forward-to-openxr/ba-p/1825672).</span><span class="sxs-lookup"><span data-stu-id="ef45e-140">The MRTK team supports the open future of mixed reality through [OpenXR](https://techcommunity.microsoft.com/t5/mixed-reality-blog/moving-forward-to-openxr/ba-p/1825672).</span></span> <span data-ttu-id="ef45e-141">Il supporto per OpenXR è attualmente in fase di sviluppo, con supporto di anteprima iniziale rilasciato in MRTK 2.5.2.</span><span class="sxs-lookup"><span data-stu-id="ef45e-141">Support for OpenXR is currently under development, with initial preview support released in MRTK 2.5.2.</span></span>

<span data-ttu-id="ef45e-142">**Esperienza utente**</span><span class="sxs-lookup"><span data-stu-id="ef45e-142">**User Experience**</span></span>

<span data-ttu-id="ef45e-143">Stiamo ascoltando i tuoi commenti e suggerimenti su MRTK e abbiamo continuato a pianificare:</span><span class="sxs-lookup"><span data-stu-id="ef45e-143">We're listening to your feedback about MRTK and have continued plans for:</span></span>

- <span data-ttu-id="ef45e-144">Correzioni di bug</span><span class="sxs-lookup"><span data-stu-id="ef45e-144">Bug fixes</span></span>
- <span data-ttu-id="ef45e-145">Semplificazione della comprensione per i controlli UX MRTK</span><span class="sxs-lookup"><span data-stu-id="ef45e-145">Making MRTK UX controls easier to understand</span></span>
- <span data-ttu-id="ef45e-146">Parità della shell HoloLens</span><span class="sxs-lookup"><span data-stu-id="ef45e-146">HoloLens Shell parity</span></span>
- <span data-ttu-id="ef45e-147">Test per garantire che le funzionalità non regressione</span><span class="sxs-lookup"><span data-stu-id="ef45e-147">Tests to ensure features do not regress</span></span>

<span data-ttu-id="ef45e-148">**Formazione per sviluppatori**</span><span class="sxs-lookup"><span data-stu-id="ef45e-148">**Developer Education**</span></span>

<span data-ttu-id="ef45e-149">È stata eseguita la migrazione della documentazione per gli sviluppatori da GitHub a una nuova piattaforma docs.</span><span class="sxs-lookup"><span data-stu-id="ef45e-149">We've migrated our developer documentation from Github to a new docs platform!</span></span> <span data-ttu-id="ef45e-150">Microsoft vuole ricevere commenti e suggerimenti per poter continuare a migliorare l'esperienza di documentazione per gli sviluppatori.</span><span class="sxs-lookup"><span data-stu-id="ef45e-150">We want to hear your feedback so we can continue to improve our developer documentation experience.</span></span>
<span data-ttu-id="ef45e-151">Attualmente sono disponibili [esercitazioni di MRTK](/windows/mixed-reality/develop/unity/tutorials) che si trovano in una sezione diversa di docs realtà mista. Queste esercitazioni verranno migrate per vivere con il resto della documentazione di MRTK.</span><span class="sxs-lookup"><span data-stu-id="ef45e-151">We currently have [MRTK tutorials](/windows/mixed-reality/develop/unity/tutorials) that live in a different section of Mixed Reality docs. We will be migrating these tutorials to live with the rest of the MRTK documentation.</span></span> 

<span data-ttu-id="ef45e-152">**Packaging**</span><span class="sxs-lookup"><span data-stu-id="ef45e-152">**Packaging**</span></span>

<span data-ttu-id="ef45e-153">Lo [strumento per la funzionalità di realtà mista](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool) è un nuovo modo per gli sviluppatori di individuare, aggiornare e aggiungere pacchetti di funzionalità di realtà mista in progetti Unity.</span><span class="sxs-lookup"><span data-stu-id="ef45e-153">The [Mixed Reality Feature Tool](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool) is a new way for developers to discover, update, and add Mixed Reality feature packages into Unity projects.</span></span> <span data-ttu-id="ef45e-154">È possibile cercare i pacchetti in base al nome o alla categoria, visualizzarne le dipendenze e persino visualizzare le modifiche proposte al file manifesto del progetto prima dell'importazione.</span><span class="sxs-lookup"><span data-stu-id="ef45e-154">You can search packages by name or category, see their dependencies, and even view proposed changes to your projects manifest file before importing.</span></span> <span data-ttu-id="ef45e-155">Si prevede di apportare aggiornamenti allo strumento per le funzionalità di realtà mista quando si rispondono alle richieste di funzionalità e ai bug.</span><span class="sxs-lookup"><span data-stu-id="ef45e-155">We intend to make updates to the Mixed Reality Feature Tool as we respond to feature requests and bugs.</span></span>

## <a name="backlog"></a><span data-ttu-id="ef45e-156">Backlog</span><span class="sxs-lookup"><span data-stu-id="ef45e-156">Backlog</span></span>

<span data-ttu-id="ef45e-157">Nell'elenco seguente sono illustrati alcuni degli investimenti principali che il team di MRTK intende adottare.</span><span class="sxs-lookup"><span data-stu-id="ef45e-157">The following list highlights some of the key investments the MRTK team intends to pursue.</span></span>

- <span data-ttu-id="ef45e-158">Espansione della piattaforma</span><span class="sxs-lookup"><span data-stu-id="ef45e-158">Platform expansion</span></span>
- <span data-ttu-id="ef45e-159">Estendibilità</span><span class="sxs-lookup"><span data-stu-id="ef45e-159">Extensibility</span></span>
- <span data-ttu-id="ef45e-160">Modularità</span><span class="sxs-lookup"><span data-stu-id="ef45e-160">Modularity</span></span>
- <span data-ttu-id="ef45e-161">Funzionalità di accesso facilitato</span><span class="sxs-lookup"><span data-stu-id="ef45e-161">Accessibility features</span></span>
- <span data-ttu-id="ef45e-162">Miglioramenti della globalizzazione</span><span class="sxs-lookup"><span data-stu-id="ef45e-162">Globalization enhancements</span></span>
- <span data-ttu-id="ef45e-163">Supporto del servizio cloud</span><span class="sxs-lookup"><span data-stu-id="ef45e-163">Cloud service support</span></span>
- <span data-ttu-id="ef45e-164">Strumenti</span><span class="sxs-lookup"><span data-stu-id="ef45e-164">Tools</span></span>
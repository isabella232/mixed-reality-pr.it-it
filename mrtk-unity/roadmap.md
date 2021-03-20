---
title: Roadmap
description: documentazione per la struttura della roadmap di MRTK.
author: polar-kev
ms.author: kesemple
ms.date: 03/03/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK
ms.openlocfilehash: 0a3089d272542e4021bc77b324255830c7cb9c6a
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2021
ms.locfileid: "104690141"
---
# <a name="roadmap"></a><span data-ttu-id="0b957-104">Roadmap</span><span class="sxs-lookup"><span data-stu-id="0b957-104">Roadmap</span></span>

<span data-ttu-id="0b957-105">Questo documento descrive la roadmap del Toolkit di realtà mista.</span><span class="sxs-lookup"><span data-stu-id="0b957-105">This document outlines the roadmap of the Mixed Reality Toolkit.</span></span> <span data-ttu-id="0b957-106">Si noti che di seguito sono riportate le stime dei lavori nelle date di sviluppo e di destinazione.</span><span class="sxs-lookup"><span data-stu-id="0b957-106">Please note that the following reflects work that is in development and target dates reflect estimates.</span></span>

## <a name="current-release"></a><span data-ttu-id="0b957-107">Versione corrente</span><span class="sxs-lookup"><span data-stu-id="0b957-107">Current release</span></span>

<span data-ttu-id="0b957-108">Microsoft Mixed Reality Toolkit v 2.6</span><span class="sxs-lookup"><span data-stu-id="0b957-108">Microsoft Mixed Reality Toolkit v2.6</span></span>

## <a name="upcoming-releases"></a><span data-ttu-id="0b957-109">Prossime versioni</span><span class="sxs-lookup"><span data-stu-id="0b957-109">Upcoming releases</span></span>

| <span data-ttu-id="0b957-110">Prodotto</span><span class="sxs-lookup"><span data-stu-id="0b957-110">Product</span></span> | <span data-ttu-id="0b957-111">Descrizione</span><span class="sxs-lookup"><span data-stu-id="0b957-111">Description</span></span> | <span data-ttu-id="0b957-112">Sequenza temporale</span><span class="sxs-lookup"><span data-stu-id="0b957-112">Timeline</span></span> | <span data-ttu-id="0b957-113">Lavagna del progetto</span><span class="sxs-lookup"><span data-stu-id="0b957-113">Project board</span></span> |
| --- | --- | --- | --- |
| [<span data-ttu-id="0b957-114">MRTK V 2.7</span><span class="sxs-lookup"><span data-stu-id="0b957-114">MRTK V2.7</span></span>](#270) | <span data-ttu-id="0b957-115">Iterazione successiva di MRTK</span><span class="sxs-lookup"><span data-stu-id="0b957-115">Next iteration of MRTK</span></span> | <span data-ttu-id="0b957-116">Maggio 2021</span><span class="sxs-lookup"><span data-stu-id="0b957-116">May 2021</span></span> | https://github.com/microsoft/MixedRealityToolkit-Unity/milestone/14 |

<span data-ttu-id="0b957-117">Le versioni sono incentrate sui temi (ad esempio, aree funzionali di grandi dimensioni) e sono pianificati per essere eseguiti approssimativamente ogni 8-12 settimane.</span><span class="sxs-lookup"><span data-stu-id="0b957-117">Releases are centered around themes (ex: large feature areas) and are scheduled to occur approximately every 8-12 weeks.</span></span>

<span data-ttu-id="0b957-118">I dettagli della versione, inclusi gli elementi di backlog, sono reperibili nelle [pagine dell'attività cardine di GitHub](https://github.com/Microsoft/MixedRealityToolkit-Unity/milestones).</span><span class="sxs-lookup"><span data-stu-id="0b957-118">Release details, including backlog items, can be found on the [GitHub milestone pages](https://github.com/Microsoft/MixedRealityToolkit-Unity/milestones).</span></span> <span data-ttu-id="0b957-119">Il set completo di problemi aperti è disponibile anche in [GitHub](https://github.com/microsoft/MixedRealityToolkit-Unity/issues).</span><span class="sxs-lookup"><span data-stu-id="0b957-119">The complete set of open issues can also be found on [GitHub](https://github.com/microsoft/MixedRealityToolkit-Unity/issues).</span></span>

## <a name="mixed-reality-toolkit-mrtk-roadmap"></a><span data-ttu-id="0b957-120">Guida di orientamento a Mixed Reality Toolkit (MRTK)</span><span class="sxs-lookup"><span data-stu-id="0b957-120">Mixed Reality Toolkit (MRTK) roadmap</span></span>

<span data-ttu-id="0b957-121">Il Toolkit per la realtà mista è progettato per essere cross MR/AR/VR/XR Platform by Design.</span><span class="sxs-lookup"><span data-stu-id="0b957-121">The Mixed Reality Toolkit is built to be cross MR/AR/VR/XR platform by design.</span></span> <span data-ttu-id="0b957-122">Il Toolkit supporta attualmente Unity 2019.4. x e Unity 2018.4. x.</span><span class="sxs-lookup"><span data-stu-id="0b957-122">The toolkit currently supports Unity 2019.4.x and Unity 2018.4.x.</span></span>

> <span data-ttu-id="0b957-123">Quando Unity rilascia un prodotto LTS (supporto a lungo termine), il Toolkit di realtà mista viene aggiornato alla versione LTS.</span><span class="sxs-lookup"><span data-stu-id="0b957-123">When Unity releases an LTS (Long Term Support) product, the Mixed Reality Toolkit will update to the LTS release.</span></span> <span data-ttu-id="0b957-124">Sebbene il Toolkit di realtà mista venga eseguito nella versione più recente del ramo Tech non beta (ad esempio, 2020,1), non è ufficialmente supportato.</span><span class="sxs-lookup"><span data-stu-id="0b957-124">Although the Mixed Reality Toolkit runs on the latest non-beta (ex: 2020.1) tech branch version of Unity, it is not officially supported.</span></span>

### <a name="270"></a><span data-ttu-id="0b957-125">2.7.0</span><span class="sxs-lookup"><span data-stu-id="0b957-125">2.7.0</span></span>

<span data-ttu-id="0b957-126">Attualmente stiamo pianificando la versione 2.7.0 e avrai a disposizione più aggiornamenti.</span><span class="sxs-lookup"><span data-stu-id="0b957-126">We are currently planning the 2.7.0 release and will have more updates for you soon!</span></span>
<span data-ttu-id="0b957-127">Per lo stato più recente della versione, visitare la pagina relativa all' [attività cardine](https://github.com/microsoft/MixedRealityToolkit-Unity/milestone/14).</span><span class="sxs-lookup"><span data-stu-id="0b957-127">For the latest status of the release, please visit the [milestone page](https://github.com/microsoft/MixedRealityToolkit-Unity/milestone/14).</span></span>

<span data-ttu-id="0b957-128">Stato: pianificazione</span><span class="sxs-lookup"><span data-stu-id="0b957-128">Status: Planning</span></span>

<span data-ttu-id="0b957-129">Sequenza temporale di destinazione: 2021 maggio</span><span class="sxs-lookup"><span data-stu-id="0b957-129">Target Timeline: May 2021</span></span>

<span data-ttu-id="0b957-130">Temi:</span><span class="sxs-lookup"><span data-stu-id="0b957-130">Themes:</span></span>

- <span data-ttu-id="0b957-131">Stability</span><span class="sxs-lookup"><span data-stu-id="0b957-131">Stability</span></span> 
- <span data-ttu-id="0b957-132">Espansione della piattaforma: OpenXR</span><span class="sxs-lookup"><span data-stu-id="0b957-132">Platform Expansion: OpenXR</span></span>
- <span data-ttu-id="0b957-133">Esperienza dell'utente</span><span class="sxs-lookup"><span data-stu-id="0b957-133">User Experience</span></span>
- <span data-ttu-id="0b957-134">Formazione per sviluppatori</span><span class="sxs-lookup"><span data-stu-id="0b957-134">Developer Education</span></span>
- <span data-ttu-id="0b957-135">Packaging</span><span class="sxs-lookup"><span data-stu-id="0b957-135">Packaging</span></span>

<span data-ttu-id="0b957-136">**Stabilità**</span><span class="sxs-lookup"><span data-stu-id="0b957-136">**Stability**</span></span>

<span data-ttu-id="0b957-137">La qualità e la stabilità sono la massima priorità per questo e tutte le versioni di Microsoft Mixed Reality Toolkit.</span><span class="sxs-lookup"><span data-stu-id="0b957-137">Quality and stability are the top priority for this and all Microsoft Mixed Reality Toolkit releases.</span></span> <span data-ttu-id="0b957-138">Si continuerà ad assegnare una priorità ai problemi dei clienti e dei partner che influiscano sulla stabilità dei componenti di MRTK.</span><span class="sxs-lookup"><span data-stu-id="0b957-138">We will continue to prioritize customer and partner issues that impact the stability of MRTK components.</span></span>

<span data-ttu-id="0b957-139">**Espansione della piattaforma: OpenXR**</span><span class="sxs-lookup"><span data-stu-id="0b957-139">**Platform Expansion: OpenXR**</span></span>

<span data-ttu-id="0b957-140">Il team di MRTK supporta il futuro aperto della realtà mista tramite [OpenXR](https://techcommunity.microsoft.com/t5/mixed-reality-blog/moving-forward-to-openxr/ba-p/1825672).</span><span class="sxs-lookup"><span data-stu-id="0b957-140">The MRTK team supports the open future of mixed reality through [OpenXR](https://techcommunity.microsoft.com/t5/mixed-reality-blog/moving-forward-to-openxr/ba-p/1825672).</span></span> <span data-ttu-id="0b957-141">Il supporto per OpenXR è attualmente in fase di sviluppo, con supporto di anteprima iniziale rilasciato in MRTK 2.5.2.</span><span class="sxs-lookup"><span data-stu-id="0b957-141">Support for OpenXR is currently under development, with initial preview support released in MRTK 2.5.2.</span></span>

<span data-ttu-id="0b957-142">**Esperienza utente**</span><span class="sxs-lookup"><span data-stu-id="0b957-142">**User Experience**</span></span>

<span data-ttu-id="0b957-143">Stiamo ascoltando i tuoi commenti e suggerimenti su MRTK e abbiamo continuato a pianificare:</span><span class="sxs-lookup"><span data-stu-id="0b957-143">We're listening to your feedback about MRTK and have continued plans for:</span></span>

- <span data-ttu-id="0b957-144">Correzioni di bug</span><span class="sxs-lookup"><span data-stu-id="0b957-144">Bug fixes</span></span>
- <span data-ttu-id="0b957-145">Semplificazione della comprensione per i controlli UX MRTK</span><span class="sxs-lookup"><span data-stu-id="0b957-145">Making MRTK UX controls easier to understand</span></span>
- <span data-ttu-id="0b957-146">Parità della shell HoloLens</span><span class="sxs-lookup"><span data-stu-id="0b957-146">HoloLens Shell parity</span></span>
- <span data-ttu-id="0b957-147">Test per garantire che le funzionalità non regressione</span><span class="sxs-lookup"><span data-stu-id="0b957-147">Tests to ensure features do not regress</span></span>

<span data-ttu-id="0b957-148">**Formazione per sviluppatori**</span><span class="sxs-lookup"><span data-stu-id="0b957-148">**Developer Education**</span></span>

<span data-ttu-id="0b957-149">È stata eseguita la migrazione della documentazione per gli sviluppatori da GitHub a una nuova piattaforma docs.</span><span class="sxs-lookup"><span data-stu-id="0b957-149">We've migrated our developer documentation from Github to a new docs platform!</span></span> <span data-ttu-id="0b957-150">Microsoft vuole ricevere commenti e suggerimenti per poter continuare a migliorare l'esperienza di documentazione per gli sviluppatori.</span><span class="sxs-lookup"><span data-stu-id="0b957-150">We want to hear your feedback so we can continue to improve our developer documentation experience.</span></span>
<span data-ttu-id="0b957-151">Attualmente sono disponibili [esercitazioni di MRTK](https://docs.microsoft.com/windows/mixed-reality/develop/unity/tutorials) che si trovano in una sezione diversa di docs realtà mista. Queste esercitazioni verranno migrate per vivere con il resto della documentazione di MRTK.</span><span class="sxs-lookup"><span data-stu-id="0b957-151">We currently have [MRTK tutorials](https://docs.microsoft.com/windows/mixed-reality/develop/unity/tutorials) that live in a different section of Mixed Reality docs. We will be migrating these tutorials to live with the rest of the MRTK documentation.</span></span> 

<span data-ttu-id="0b957-152">**Packaging**</span><span class="sxs-lookup"><span data-stu-id="0b957-152">**Packaging**</span></span>

<span data-ttu-id="0b957-153">Lo [strumento per la funzionalità di realtà mista](https://docs.microsoft.com/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool) è un nuovo modo per gli sviluppatori di individuare, aggiornare e aggiungere pacchetti di funzionalità di realtà mista in progetti Unity.</span><span class="sxs-lookup"><span data-stu-id="0b957-153">The [Mixed Reality Feature Tool](https://docs.microsoft.com/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool) is a new way for developers to discover, update, and add Mixed Reality feature packages into Unity projects.</span></span> <span data-ttu-id="0b957-154">È possibile cercare i pacchetti in base al nome o alla categoria, visualizzarne le dipendenze e persino visualizzare le modifiche proposte al file manifesto del progetto prima dell'importazione.</span><span class="sxs-lookup"><span data-stu-id="0b957-154">You can search packages by name or category, see their dependencies, and even view proposed changes to your projects manifest file before importing.</span></span> <span data-ttu-id="0b957-155">Si prevede di apportare aggiornamenti allo strumento per le funzionalità di realtà mista quando si rispondono alle richieste di funzionalità e ai bug.</span><span class="sxs-lookup"><span data-stu-id="0b957-155">We intend to make updates to the Mixed Reality Feature Tool as we respond to feature requests and bugs.</span></span>

## <a name="backlog"></a><span data-ttu-id="0b957-156">Backlog</span><span class="sxs-lookup"><span data-stu-id="0b957-156">Backlog</span></span>

<span data-ttu-id="0b957-157">Nell'elenco seguente sono illustrati alcuni degli investimenti principali che il team di MRTK intende adottare.</span><span class="sxs-lookup"><span data-stu-id="0b957-157">The following list highlights some of the key investments the MRTK team intends to pursue.</span></span>

- <span data-ttu-id="0b957-158">Espansione della piattaforma</span><span class="sxs-lookup"><span data-stu-id="0b957-158">Platform expansion</span></span>
- <span data-ttu-id="0b957-159">Estendibilità</span><span class="sxs-lookup"><span data-stu-id="0b957-159">Extensibility</span></span>
- <span data-ttu-id="0b957-160">Modularità</span><span class="sxs-lookup"><span data-stu-id="0b957-160">Modularity</span></span>
- <span data-ttu-id="0b957-161">Funzionalità di accesso facilitato</span><span class="sxs-lookup"><span data-stu-id="0b957-161">Accessibility features</span></span>
- <span data-ttu-id="0b957-162">Miglioramenti della globalizzazione</span><span class="sxs-lookup"><span data-stu-id="0b957-162">Globalization enhancements</span></span>
- <span data-ttu-id="0b957-163">Supporto del servizio cloud</span><span class="sxs-lookup"><span data-stu-id="0b957-163">Cloud service support</span></span>
- <span data-ttu-id="0b957-164">Strumenti</span><span class="sxs-lookup"><span data-stu-id="0b957-164">Tools</span></span>

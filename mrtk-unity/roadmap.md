---
title: Roadmap
description: documentazione per la struttura della roadmap di MRTK.
author: polar-kev
ms.author: kesemple
ms.date: 03/03/2021
keywords: Unity, HoloLens, HoloLens 2, realtà mista, sviluppo, MRTK
ms.openlocfilehash: 7385d516e986c1602ad59e2825aa6d1262504727
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2021
ms.locfileid: "113175580"
---
# <a name="roadmap"></a><span data-ttu-id="bdbd6-104">Roadmap</span><span class="sxs-lookup"><span data-stu-id="bdbd6-104">Roadmap</span></span>

<span data-ttu-id="bdbd6-105">Questo documento illustra la roadmap del modello di realtà mista Toolkit.</span><span class="sxs-lookup"><span data-stu-id="bdbd6-105">This document outlines the roadmap of the Mixed Reality Toolkit.</span></span> <span data-ttu-id="bdbd6-106">Si noti che quanto segue riflette il lavoro in fase di sviluppo e le date di destinazione riflettono le stime.</span><span class="sxs-lookup"><span data-stu-id="bdbd6-106">Please note that the following reflects work that is in development and target dates reflect estimates.</span></span>

## <a name="current-release"></a><span data-ttu-id="bdbd6-107">Versione corrente</span><span class="sxs-lookup"><span data-stu-id="bdbd6-107">Current release</span></span>

<span data-ttu-id="bdbd6-108">Microsoft Mixed Reality Toolkit v2.6</span><span class="sxs-lookup"><span data-stu-id="bdbd6-108">Microsoft Mixed Reality Toolkit v2.6</span></span>

## <a name="upcoming-releases"></a><span data-ttu-id="bdbd6-109">Versioni future</span><span class="sxs-lookup"><span data-stu-id="bdbd6-109">Upcoming releases</span></span>

| <span data-ttu-id="bdbd6-110">Prodotto</span><span class="sxs-lookup"><span data-stu-id="bdbd6-110">Product</span></span> | <span data-ttu-id="bdbd6-111">Descrizione</span><span class="sxs-lookup"><span data-stu-id="bdbd6-111">Description</span></span> | <span data-ttu-id="bdbd6-112">Sequenza temporale</span><span class="sxs-lookup"><span data-stu-id="bdbd6-112">Timeline</span></span> | <span data-ttu-id="bdbd6-113">Project scheda</span><span class="sxs-lookup"><span data-stu-id="bdbd6-113">Project board</span></span> |
| --- | --- | --- | --- |
| [<span data-ttu-id="bdbd6-114">MRTK V2.7</span><span class="sxs-lookup"><span data-stu-id="bdbd6-114">MRTK V2.7</span></span>](#270) | <span data-ttu-id="bdbd6-115">Iterazione successiva di MRTK</span><span class="sxs-lookup"><span data-stu-id="bdbd6-115">Next iteration of MRTK</span></span> | <span data-ttu-id="bdbd6-116">Maggio 2021</span><span class="sxs-lookup"><span data-stu-id="bdbd6-116">May 2021</span></span> | https://github.com/microsoft/MixedRealityToolkit-Unity/milestone/14 |

<span data-ttu-id="bdbd6-117">Le versioni sono centrate sui temi (ad esempio aree di funzionalità di grandi dimensioni) e sono pianificate per essere eseguite circa ogni 8-12 settimane.</span><span class="sxs-lookup"><span data-stu-id="bdbd6-117">Releases are centered around themes (ex: large feature areas) and are scheduled to occur approximately every 8-12 weeks.</span></span>

<span data-ttu-id="bdbd6-118">I dettagli sulla versione, inclusi gli elementi di backlog, sono disponibili nelle pagine delle attività [cardine GitHub attività cardine.](https://github.com/Microsoft/MixedRealityToolkit-Unity/milestones)</span><span class="sxs-lookup"><span data-stu-id="bdbd6-118">Release details, including backlog items, can be found on the [GitHub milestone pages](https://github.com/Microsoft/MixedRealityToolkit-Unity/milestones).</span></span> <span data-ttu-id="bdbd6-119">Il set completo di problemi aperti è disponibile anche in [GitHub](https://github.com/microsoft/MixedRealityToolkit-Unity/issues).</span><span class="sxs-lookup"><span data-stu-id="bdbd6-119">The complete set of open issues can also be found on [GitHub](https://github.com/microsoft/MixedRealityToolkit-Unity/issues).</span></span>

## <a name="mixed-reality-toolkit-mrtk-roadmap"></a><span data-ttu-id="bdbd6-120">Guida di orientamento Toolkit realtà mista (MRTK)</span><span class="sxs-lookup"><span data-stu-id="bdbd6-120">Mixed Reality Toolkit (MRTK) roadmap</span></span>

<span data-ttu-id="bdbd6-121">L'Toolkit di realtà mista è progettato per essere multipiattaforma MR/AR/VR/XR.</span><span class="sxs-lookup"><span data-stu-id="bdbd6-121">The Mixed Reality Toolkit is built to be cross MR/AR/VR/XR platform by design.</span></span> <span data-ttu-id="bdbd6-122">Il toolkit attualmente supporta Unity 2019.4.x e Unity 2018.4.x.</span><span class="sxs-lookup"><span data-stu-id="bdbd6-122">The toolkit currently supports Unity 2019.4.x and Unity 2018.4.x.</span></span>

> <span data-ttu-id="bdbd6-123">Quando Unity rilascia un prodotto LTS (Supporto a lungo termine), l'Toolkit realtà mista verrà aggiornato alla versione LTS.</span><span class="sxs-lookup"><span data-stu-id="bdbd6-123">When Unity releases an LTS (Long Term Support) product, the Mixed Reality Toolkit will update to the LTS release.</span></span> <span data-ttu-id="bdbd6-124">Anche se l'Toolkit mixed reality viene eseguito nella versione tech branch più recente non beta (ad esempio, 2020.1) di Unity, non è ufficialmente supportata.</span><span class="sxs-lookup"><span data-stu-id="bdbd6-124">Although the Mixed Reality Toolkit runs on the latest non-beta (ex: 2020.1) tech branch version of Unity, it is not officially supported.</span></span>

### <a name="270"></a><span data-ttu-id="bdbd6-125">2.7.0</span><span class="sxs-lookup"><span data-stu-id="bdbd6-125">2.7.0</span></span>

<span data-ttu-id="bdbd6-126">È in corso la pianificazione della versione 2.7.0 e presto saranno disponibili altri aggiornamenti.</span><span class="sxs-lookup"><span data-stu-id="bdbd6-126">We are currently planning the 2.7.0 release and will have more updates for you soon!</span></span>
<span data-ttu-id="bdbd6-127">Per lo stato più recente della versione, visitare la pagina [attività cardine](https://github.com/microsoft/MixedRealityToolkit-Unity/milestone/14).</span><span class="sxs-lookup"><span data-stu-id="bdbd6-127">For the latest status of the release, please visit the [milestone page](https://github.com/microsoft/MixedRealityToolkit-Unity/milestone/14).</span></span>

<span data-ttu-id="bdbd6-128">Stato: Pianificazione</span><span class="sxs-lookup"><span data-stu-id="bdbd6-128">Status: Planning</span></span>

<span data-ttu-id="bdbd6-129">Sequenza temporale di destinazione: maggio 2021</span><span class="sxs-lookup"><span data-stu-id="bdbd6-129">Target Timeline: May 2021</span></span>

<span data-ttu-id="bdbd6-130">Temi:</span><span class="sxs-lookup"><span data-stu-id="bdbd6-130">Themes:</span></span>

- <span data-ttu-id="bdbd6-131">Stability</span><span class="sxs-lookup"><span data-stu-id="bdbd6-131">Stability</span></span> 
- <span data-ttu-id="bdbd6-132">Espansione della piattaforma: OpenXR</span><span class="sxs-lookup"><span data-stu-id="bdbd6-132">Platform Expansion: OpenXR</span></span>
- <span data-ttu-id="bdbd6-133">Esperienza dell'utente</span><span class="sxs-lookup"><span data-stu-id="bdbd6-133">User Experience</span></span>
- <span data-ttu-id="bdbd6-134">Formazione per sviluppatori</span><span class="sxs-lookup"><span data-stu-id="bdbd6-134">Developer Education</span></span>
- <span data-ttu-id="bdbd6-135">Packaging</span><span class="sxs-lookup"><span data-stu-id="bdbd6-135">Packaging</span></span>

<span data-ttu-id="bdbd6-136">**Stabilità**</span><span class="sxs-lookup"><span data-stu-id="bdbd6-136">**Stability**</span></span>

<span data-ttu-id="bdbd6-137">La qualità e la stabilità sono la priorità principale per questa e tutte le versioni di Microsoft Mixed Reality Toolkit versioni.</span><span class="sxs-lookup"><span data-stu-id="bdbd6-137">Quality and stability are the top priority for this and all Microsoft Mixed Reality Toolkit releases.</span></span> <span data-ttu-id="bdbd6-138">Microsoft continuerà a classificare in ordine di priorità i problemi relativi a clienti e partner che influiscono sulla stabilità dei componenti MRTK.</span><span class="sxs-lookup"><span data-stu-id="bdbd6-138">We will continue to prioritize customer and partner issues that impact the stability of MRTK components.</span></span>

<span data-ttu-id="bdbd6-139">**Espansione della piattaforma: OpenXR**</span><span class="sxs-lookup"><span data-stu-id="bdbd6-139">**Platform Expansion: OpenXR**</span></span>

<span data-ttu-id="bdbd6-140">Il team MRTK supporta il futuro aperto della realtà mista tramite [OpenXR.](https://techcommunity.microsoft.com/t5/mixed-reality-blog/moving-forward-to-openxr/ba-p/1825672)</span><span class="sxs-lookup"><span data-stu-id="bdbd6-140">The MRTK team supports the open future of mixed reality through [OpenXR](https://techcommunity.microsoft.com/t5/mixed-reality-blog/moving-forward-to-openxr/ba-p/1825672).</span></span> <span data-ttu-id="bdbd6-141">Il supporto per OpenXR è attualmente in fase di sviluppo, con il supporto dell'anteprima iniziale rilasciato in MRTK 2.5.2.</span><span class="sxs-lookup"><span data-stu-id="bdbd6-141">Support for OpenXR is currently under development, with initial preview support released in MRTK 2.5.2.</span></span>

<span data-ttu-id="bdbd6-142">**Esperienza utente**</span><span class="sxs-lookup"><span data-stu-id="bdbd6-142">**User Experience**</span></span>

<span data-ttu-id="bdbd6-143">Stiamo ascoltando i commenti e suggerimenti su MRTK e sono stati continuati i piani per:</span><span class="sxs-lookup"><span data-stu-id="bdbd6-143">We're listening to your feedback about MRTK and have continued plans for:</span></span>

- <span data-ttu-id="bdbd6-144">Correzioni di bug</span><span class="sxs-lookup"><span data-stu-id="bdbd6-144">Bug fixes</span></span>
- <span data-ttu-id="bdbd6-145">Semplificare la comprensione dei controlli dell'esperienza utente MRTK</span><span class="sxs-lookup"><span data-stu-id="bdbd6-145">Making MRTK UX controls easier to understand</span></span>
- <span data-ttu-id="bdbd6-146">HoloLens Parità della shell</span><span class="sxs-lookup"><span data-stu-id="bdbd6-146">HoloLens Shell parity</span></span>
- <span data-ttu-id="bdbd6-147">Test per garantire che le funzionalità non regredino</span><span class="sxs-lookup"><span data-stu-id="bdbd6-147">Tests to ensure features do not regress</span></span>

<span data-ttu-id="bdbd6-148">**Formazione per sviluppatori**</span><span class="sxs-lookup"><span data-stu-id="bdbd6-148">**Developer Education**</span></span>

<span data-ttu-id="bdbd6-149">È stata eseguita la migrazione della documentazione per sviluppatori da GitHub a una nuova piattaforma di documentazione.</span><span class="sxs-lookup"><span data-stu-id="bdbd6-149">We've migrated our developer documentation from Github to a new docs platform!</span></span> <span data-ttu-id="bdbd6-150">Microsoft vuole ricevere commenti e suggerimenti in modo da poter continuare a migliorare l'esperienza della documentazione per gli sviluppatori.</span><span class="sxs-lookup"><span data-stu-id="bdbd6-150">We want to hear your feedback so we can continue to improve our developer documentation experience.</span></span>
<span data-ttu-id="bdbd6-151">Attualmente sono disponibili [esercitazioni su MRTK](/windows/mixed-reality/develop/unity/tutorials) disponibili in un'altra sezione della documentazione sulla realtà mista. Verrà eseguita la migrazione di queste esercitazioni per l'esecuzione del resto della documentazione di MRTK.</span><span class="sxs-lookup"><span data-stu-id="bdbd6-151">We currently have [MRTK tutorials](/windows/mixed-reality/develop/unity/tutorials) that live in a different section of Mixed Reality docs. We will be migrating these tutorials to live with the rest of the MRTK documentation.</span></span> 

<span data-ttu-id="bdbd6-152">**Packaging**</span><span class="sxs-lookup"><span data-stu-id="bdbd6-152">**Packaging**</span></span>

<span data-ttu-id="bdbd6-153">[Lo strumento funzionalità realtà mista](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool) è un nuovo modo per consentire agli sviluppatori di individuare, aggiornare e aggiungere pacchetti di funzionalità di realtà mista nei progetti Unity.</span><span class="sxs-lookup"><span data-stu-id="bdbd6-153">The [Mixed Reality Feature Tool](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool) is a new way for developers to discover, update, and add Mixed Reality feature packages into Unity projects.</span></span> <span data-ttu-id="bdbd6-154">È possibile cercare i pacchetti in base al nome o alla categoria, visualizzarne le dipendenze e persino visualizzare le modifiche proposte al file manifesto del progetto prima dell'importazione.</span><span class="sxs-lookup"><span data-stu-id="bdbd6-154">You can search packages by name or category, see their dependencies, and even view proposed changes to your projects manifest file before importing.</span></span> <span data-ttu-id="bdbd6-155">Microsoft intende apportare aggiornamenti a Mixed Reality Feature Tool in risposta alle richieste di funzionalità e ai bug.</span><span class="sxs-lookup"><span data-stu-id="bdbd6-155">We intend to make updates to the Mixed Reality Feature Tool as we respond to feature requests and bugs.</span></span>

## <a name="backlog"></a><span data-ttu-id="bdbd6-156">Backlog</span><span class="sxs-lookup"><span data-stu-id="bdbd6-156">Backlog</span></span>

<span data-ttu-id="bdbd6-157">L'elenco seguente evidenzia alcuni degli investimenti chiave che il team di MRTK intende intraprendere.</span><span class="sxs-lookup"><span data-stu-id="bdbd6-157">The following list highlights some of the key investments the MRTK team intends to pursue.</span></span>

- <span data-ttu-id="bdbd6-158">Espansione della piattaforma</span><span class="sxs-lookup"><span data-stu-id="bdbd6-158">Platform expansion</span></span>
- <span data-ttu-id="bdbd6-159">Estendibilità</span><span class="sxs-lookup"><span data-stu-id="bdbd6-159">Extensibility</span></span>
- <span data-ttu-id="bdbd6-160">Modularità</span><span class="sxs-lookup"><span data-stu-id="bdbd6-160">Modularity</span></span>
- <span data-ttu-id="bdbd6-161">Funzionalità di accessibilità</span><span class="sxs-lookup"><span data-stu-id="bdbd6-161">Accessibility features</span></span>
- <span data-ttu-id="bdbd6-162">Miglioramenti della globalizzazione</span><span class="sxs-lookup"><span data-stu-id="bdbd6-162">Globalization enhancements</span></span>
- <span data-ttu-id="bdbd6-163">Supporto del servizio cloud</span><span class="sxs-lookup"><span data-stu-id="bdbd6-163">Cloud service support</span></span>
- <span data-ttu-id="bdbd6-164">Strumenti</span><span class="sxs-lookup"><span data-stu-id="bdbd6-164">Tools</span></span>

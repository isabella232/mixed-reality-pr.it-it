---
title: Spectator View
description: Visualizzare ologrammi da un dispositivo esterno per mostrare o registrare un'esperienza di realtà mista in uno schermo esterno.
author: chrisfromwork
ms.author: chriba
ms.date: 02/11/2019
ms.topic: article
ms.localizationpriority: high
keywords: Spectator View, iPhone, iOS, iPad, OpenCV, Camera, ARKit, HoloLens, Realtà mista, MixedRealityToolkit, demo, record
ms.openlocfilehash: c344edea9b499bdff15d1d93e400b8be626a63b6
ms.sourcegitcommit: c41372e0c6ca265f599bff309390982642d628b8
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/15/2020
ms.locfileid: "97530105"
---
# <a name="spectator-view-for-hololens-and-hololens-2"></a><span data-ttu-id="fc100-104">Spectator View per HoloLens e HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="fc100-104">Spectator View for HoloLens and HoloLens 2</span></span>

![Marcatore](images/SpecViewPhoneHero.jpg)

## <a name="overview"></a><span data-ttu-id="fc100-106">Panoramica</span><span class="sxs-lookup"><span data-stu-id="fc100-106">Overview</span></span>

<span data-ttu-id="fc100-107">Quando si indossa un dispositivo HoloLens, è facile dimenticare che una persona non dotata di tale dispositivo non può sperimentare le stesse meraviglie visive.</span><span class="sxs-lookup"><span data-stu-id="fc100-107">When you're wearing a HoloLens, it's easy to forget a person without one can't experience the same wonders you're seeing.</span></span> <span data-ttu-id="fc100-108">Spectator View consente ad altri utenti di visualizzare gli stessi elementi che un utente HoloLens vede in uno schermo 2D.</span><span class="sxs-lookup"><span data-stu-id="fc100-108">Spectator View lets others see what a HoloLens user sees on a 2D screen.</span></span> <span data-ttu-id="fc100-109">Si tratta inoltre di un approccio rapido e conveniente per registrare ologrammi in HD con dispositivi mobili e ottenere registrazioni di ologrammi di ottima qualità con l'uso di videocamere.</span><span class="sxs-lookup"><span data-stu-id="fc100-109">It's also a fast and affordable approach to recording holograms in HD with mobile devices and getting great quality recordings of holograms with video cameras.</span></span>

## <a name="key-resources"></a><span data-ttu-id="fc100-110">Risorse principali</span><span class="sxs-lookup"><span data-stu-id="fc100-110">Key Resources</span></span>

* [<span data-ttu-id="fc100-111">**Spectator View su GitHub**</span><span class="sxs-lookup"><span data-stu-id="fc100-111">**Spectator View on GitHub**</span></span>](https://github.com/microsoft/MixedReality-SpectatorView)
* [<span data-ttu-id="fc100-112">**Documentazione di Spectator View**</span><span class="sxs-lookup"><span data-stu-id="fc100-112">**Spectator View Documentation**</span></span>](https://microsoft.github.io/MixedReality-SpectatorView/README.html)
* [<span data-ttu-id="fc100-113">**Esempi di Spectator View**</span><span class="sxs-lookup"><span data-stu-id="fc100-113">**Spectator View Samples**</span></span>](https://github.com/microsoft/MixedReality-SpectatorView/tree/master/samples)

## <a name="use-cases"></a><span data-ttu-id="fc100-114">Casi d'uso</span><span class="sxs-lookup"><span data-stu-id="fc100-114">Use Cases</span></span>

* <span data-ttu-id="fc100-115">Puoi registrare un'esperienza di realtà mista usando un iPhone o un dispositivo Android.</span><span class="sxs-lookup"><span data-stu-id="fc100-115">You can record a mixed reality experience using an iPhone or Android device.</span></span> <span data-ttu-id="fc100-116">Per acquisire video di ologrammi in modo rapido e conveniente, registrare in Full HD e applicare l'anti-aliasing agli ologrammi e all'ombreggiatura.</span><span class="sxs-lookup"><span data-stu-id="fc100-116">Record in full HD and apply anti-aliasing to holograms and shadow for a cost-effective and quick way to capture video of holograms.</span></span>
* <span data-ttu-id="fc100-117">Trasmetti in streaming le esperienze di realtà mista a un dispositivo Apple TV direttamente dal tuo iPhone o iPad, in tempo reale.</span><span class="sxs-lookup"><span data-stu-id="fc100-117">Stream live mixed reality experiences to an Apple TV directly from your iPhone or iPad, lag-free!</span></span>
* <span data-ttu-id="fc100-118">Condividi l'esperienza con i tuoi ospiti: consenti alle persone che non hanno HoloLens di visualizzare gli ologrammi direttamente dai loro telefoni o tablet.</span><span class="sxs-lookup"><span data-stu-id="fc100-118">Share the experience with guests: Let non-HoloLens users experience holograms directly from their phones or tablets.</span></span>

## <a name="current-features"></a><span data-ttu-id="fc100-119">Funzionalità attualmente disponibili</span><span class="sxs-lookup"><span data-stu-id="fc100-119">Current Features</span></span>

* <span data-ttu-id="fc100-120">Sincronizzazione spaziale degli ologrammi, in modo che tutti possano visualizzare gli ologrammi esattamente nella stessa posizione.</span><span class="sxs-lookup"><span data-stu-id="fc100-120">Spatial synchronization of Holograms, so everyone sees holograms in the exact same place.</span></span>
* <span data-ttu-id="fc100-121">Supporto per iOS (dispositivi abilitati per ARKit) e Android (dispositivi abilitati per ARCore).</span><span class="sxs-lookup"><span data-stu-id="fc100-121">iOS (ARKit-enabled devices) and Android (ARCore-enabled devices) support.</span></span>
<span data-ttu-id="fc100-122">Più utenti guest iOS.</span><span class="sxs-lookup"><span data-stu-id="fc100-122">Multiple iOS guests.</span></span>
<span data-ttu-id="fc100-123">Registrazione di video + ologrammi + audio dell'ambiente + audio dell'ologramma.</span><span class="sxs-lookup"><span data-stu-id="fc100-123">Recording of video + holograms + ambient sound + hologram sound.</span></span>
<span data-ttu-id="fc100-124">Strumento di condivisione per poter salvare video, inviare un messaggio e-mail o condividere l'esperienza con altre app supportate.</span><span class="sxs-lookup"><span data-stu-id="fc100-124">Share sheet so you can save video, email it, or share with other supporting apps.</span></span>

<span data-ttu-id="fc100-125">![Marcatore](images/SpecViewPhoneDemo.jpg)
![Marcatore](images/hololensspectatorview-500px.jpg) ![Marcatore](images/spectatorview-300px.png)</span><span class="sxs-lookup"><span data-stu-id="fc100-125">![Marker](images/SpecViewPhoneDemo.jpg)
![Marker](images/hololensspectatorview-500px.jpg) ![Marker](images/spectatorview-300px.png)</span></span>

<span data-ttu-id="fc100-126">La tabella seguente illustra le diverse funzionalità di Spectator View e le opzioni supportate.</span><span class="sxs-lookup"><span data-stu-id="fc100-126">The following table shows different Spectator View functionality and their capabilities.</span></span> <span data-ttu-id="fc100-127">Scegli l'opzione più adatta alle tue esigenze di registrazione video:</span><span class="sxs-lookup"><span data-stu-id="fc100-127">Choose the option that best fits your video recording needs:</span></span>

|      <span data-ttu-id="fc100-128">Funzionalità</span><span class="sxs-lookup"><span data-stu-id="fc100-128">Functionality</span></span>                                | <span data-ttu-id="fc100-129">Mobile</span><span class="sxs-lookup"><span data-stu-id="fc100-129">Mobile</span></span>                  |                    <span data-ttu-id="fc100-130">Videocamera</span><span class="sxs-lookup"><span data-stu-id="fc100-130">Video Camera</span></span>              |
|--------------------------------------|:-----------------------:|:-------------------------------------------:|
| <span data-ttu-id="fc100-131">Qualità HD</span><span class="sxs-lookup"><span data-stu-id="fc100-131">HD quality</span></span>                           |         <span data-ttu-id="fc100-132">Full HD</span><span class="sxs-lookup"><span data-stu-id="fc100-132">Full HD</span></span>         |        <span data-ttu-id="fc100-133">Registrazioni di qualità professionale (in base alla videocamera)</span><span class="sxs-lookup"><span data-stu-id="fc100-133">Professional quality filming (as determined by video camera)</span></span>      |
| <span data-ttu-id="fc100-134">Facilità di spostamento della videocamera</span><span class="sxs-lookup"><span data-stu-id="fc100-134">Easy camera movement</span></span>                 |            <span data-ttu-id="fc100-135">✔</span><span class="sxs-lookup"><span data-stu-id="fc100-135">✔</span></span>            |                      <span data-ttu-id="fc100-136">✔</span><span class="sxs-lookup"><span data-stu-id="fc100-136">✔</span></span>                      |
| <span data-ttu-id="fc100-137">Visualizzazione di altre persone</span><span class="sxs-lookup"><span data-stu-id="fc100-137">Third-person view</span></span>                    |            <span data-ttu-id="fc100-138">✔</span><span class="sxs-lookup"><span data-stu-id="fc100-138">✔</span></span>            |                      <span data-ttu-id="fc100-139">✔</span><span class="sxs-lookup"><span data-stu-id="fc100-139">✔</span></span>                      |
| <span data-ttu-id="fc100-140">Trasmissione in streaming su uno schermo</span><span class="sxs-lookup"><span data-stu-id="fc100-140">Can be streamed to screens</span></span>           |            <span data-ttu-id="fc100-141">✔</span><span class="sxs-lookup"><span data-stu-id="fc100-141">✔</span></span>            |                      <span data-ttu-id="fc100-142">✔</span><span class="sxs-lookup"><span data-stu-id="fc100-142">✔</span></span>                      |
| <span data-ttu-id="fc100-143">Portabile</span><span class="sxs-lookup"><span data-stu-id="fc100-143">Portable</span></span>                             |            <span data-ttu-id="fc100-144">✔</span><span class="sxs-lookup"><span data-stu-id="fc100-144">✔</span></span>            |                                             |
| <span data-ttu-id="fc100-145">Wireless</span><span class="sxs-lookup"><span data-stu-id="fc100-145">Wireless</span></span>                             |            <span data-ttu-id="fc100-146">✔</span><span class="sxs-lookup"><span data-stu-id="fc100-146">✔</span></span>            |                                             |
| <span data-ttu-id="fc100-147">Altri requisiti hardware</span><span class="sxs-lookup"><span data-stu-id="fc100-147">Additional required hardware</span></span>         |     <span data-ttu-id="fc100-148">Telefono Android, iPhone</span><span class="sxs-lookup"><span data-stu-id="fc100-148">Android phone, iPhone</span></span>    | <span data-ttu-id="fc100-149">HoloLens + attrezzatura + treppiede + videocamera + PC + Unity</span><span class="sxs-lookup"><span data-stu-id="fc100-149">HoloLens + Rig + Tripod + Video Camera + PC + Unity</span></span> |
| <span data-ttu-id="fc100-150">Investimento hardware</span><span class="sxs-lookup"><span data-stu-id="fc100-150">Hardware investment</span></span>                  |           <span data-ttu-id="fc100-151">Basso</span><span class="sxs-lookup"><span data-stu-id="fc100-151">Low</span></span>            |                     <span data-ttu-id="fc100-152">Alto</span><span class="sxs-lookup"><span data-stu-id="fc100-152">High</span></span>                    |
| <span data-ttu-id="fc100-153">Multipiattaforma</span><span class="sxs-lookup"><span data-stu-id="fc100-153">Cross-platform</span></span>                       |           <span data-ttu-id="fc100-154">Android, iOS</span><span class="sxs-lookup"><span data-stu-id="fc100-154">Android, iOS</span></span>   |                                             |
| <span data-ttu-id="fc100-155">Contenuto sincronizzato</span><span class="sxs-lookup"><span data-stu-id="fc100-155">Synchronized content</span></span>                 |            <span data-ttu-id="fc100-156">✔</span><span class="sxs-lookup"><span data-stu-id="fc100-156">✔</span></span>            |                      <span data-ttu-id="fc100-157">✔</span><span class="sxs-lookup"><span data-stu-id="fc100-157">✔</span></span>                      |
| <span data-ttu-id="fc100-158">Durata di configurazione del runtime</span><span class="sxs-lookup"><span data-stu-id="fc100-158">Runtime setup duration</span></span>               |         <span data-ttu-id="fc100-159">Adesso</span><span class="sxs-lookup"><span data-stu-id="fc100-159">Instant</span></span>          |                     <span data-ttu-id="fc100-160">Lente</span><span class="sxs-lookup"><span data-stu-id="fc100-160">Slow</span></span>                    |
## <a name="see-also"></a><span data-ttu-id="fc100-161">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="fc100-161">See also</span></span>

* [<span data-ttu-id="fc100-162">Acquisizione in realtà mista (MRC, Mixed Reality Capture)</span><span class="sxs-lookup"><span data-stu-id="fc100-162">Mixed reality capture</span></span>](../../mixed-reality-capture.md) 
* [<span data-ttu-id="fc100-163">Acquisizione realtà mista per sviluppatori</span><span class="sxs-lookup"><span data-stu-id="fc100-163">Mixed reality capture for developers</span></span>](mixed-reality-capture-for-developers.md)
* [<span data-ttu-id="fc100-164">Esperienze condivise nella realtà mista</span><span class="sxs-lookup"><span data-stu-id="fc100-164">Shared experiences in mixed reality</span></span>](shared-experiences-in-mixed-reality.md)

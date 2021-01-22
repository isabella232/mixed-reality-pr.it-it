---
title: Introduzione a MRKT per Unity
description: Introduzione a tutte le funzionalità che Mixed Reality Toolkit con supporto multipiattaforma può offrire ai nuovi sviluppatori di realtà mista.
author: cre8ivepark
ms.author: dongpark
ms.date: 05/15/2019
ms.topic: article
ms.localizationpriority: high
keywords: Windows Mixed Reality, test, Mixed Reality Toolkit, MRTK versione 2, MRTK, strumenti, SDK, HoloLens, HoloLens 2, visore VR realtà mista, visore VR di windows mixed reality, visore per realtà virtuale, multipiattaforma
ms.openlocfilehash: 4c013f1fa50518404f899b4181e7c07b9e4e0e56
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/20/2021
ms.locfileid: "98581699"
---
# <a name="introducing-mrtk-for-unity"></a><span data-ttu-id="c6dd5-104">Introduzione a MRKT per Unity</span><span class="sxs-lookup"><span data-stu-id="c6dd5-104">Introducing MRTK for Unity</span></span>

![MRTK](../../design/images/MRTK_UX_Hero.png)

## <a name="what-is-mixed-reality-toolkit-mrtk"></a><span data-ttu-id="c6dd5-106">Che cos'è Mixed Reality Toolkit (MRTK)?</span><span class="sxs-lookup"><span data-stu-id="c6dd5-106">What is Mixed Reality Toolkit (MRTK)?</span></span>

<span data-ttu-id="c6dd5-107">MRTK è uno straordinario toolkit open source disponibile sin dalla prima versione di HoloLens.</span><span class="sxs-lookup"><span data-stu-id="c6dd5-107">MRTK is an amazing open-source toolkit that has been around since the HoloLens was first released.</span></span> <span data-ttu-id="c6dd5-108">Il toolkit non avrebbe raggiunto i livelli attuali senza il contributo e l'impegno costante della community di sviluppatori Microsoft.</span><span class="sxs-lookup"><span data-stu-id="c6dd5-108">The toolkit wouldn't be where it is today without the hard work of our contributing developer community.</span></span> <span data-ttu-id="c6dd5-109">Negli ultimi tre anni abbiamo acquisito feedback dalla community di sviluppatori e abbiamo creato MRTK v2 tenendo conto delle principali esigenze e segnalazioni.</span><span class="sxs-lookup"><span data-stu-id="c6dd5-109">Over the past three years, we've listened to the feedback of our developer community, and built MRTK v2 to take the biggest concerns into account.</span></span>  

<span data-ttu-id="c6dd5-110">MRTK per Unity è un kit di sviluppo multipiattaforma open source per applicazioni di realtà mista.</span><span class="sxs-lookup"><span data-stu-id="c6dd5-110">MRTK for Unity is an open-source, cross-platform development kit for mixed reality applications.</span></span> <span data-ttu-id="c6dd5-111">Il toolkit offre un sistema di input multipiattaforma, componenti di base e blocchi predefiniti comuni per le interazioni spaziali.</span><span class="sxs-lookup"><span data-stu-id="c6dd5-111">The toolkit provides a cross-platform input system, foundational components, and common building blocks for spatial interactions.</span></span> <span data-ttu-id="c6dd5-112">MRTK versione 2 intende accelerare lo sviluppo di applicazioni per Microsoft HoloLens, i visori VR immersive di Windows Mixed Reality e la piattaforma OpenVR.</span><span class="sxs-lookup"><span data-stu-id="c6dd5-112">MRTK version 2 intends to speed up application development for Microsoft HoloLens, Windows Mixed Reality immersive (VR) headsets, and OpenVR platform.</span></span> <span data-ttu-id="c6dd5-113">Il progetto mira a ridurre le barriere di accesso, creare applicazioni di realtà mista e restituire contributi alla community per continuare a crescere insieme.</span><span class="sxs-lookup"><span data-stu-id="c6dd5-113">The project is aimed at reducing barriers to entry, creating mixed reality applications, and contributing back to the community as we all grow.</span></span>

<br>

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4IkCG]

<span data-ttu-id="c6dd5-114">Vedere la [documentazione di MRTK su GitHub](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html) e iniziare a usare la Guida all' [installazione](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html).</span><span class="sxs-lookup"><span data-stu-id="c6dd5-114">Take a look at [MRTK's documentation on GitHub](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html) and get started with the [installation guide](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html).</span></span>

## <a name="new-with-mrtk-v2"></a><span data-ttu-id="c6dd5-115">Novità di MRTK v2</span><span class="sxs-lookup"><span data-stu-id="c6dd5-115">New with MRTK v2</span></span>

<span data-ttu-id="c6dd5-116">È importante sottolineare l'impegno che abbiamo dedicato a questi strumenti della piattaforma.</span><span class="sxs-lookup"><span data-stu-id="c6dd5-116">We want to stress our commitment to these platform tools.</span></span>  <span data-ttu-id="c6dd5-117">Infatti, abbiamo usato MRTK versione 2 per sviluppare le esperienze integrate, come l'esperienza di installazione predefinita (OOBE) e l'applicazione Mixed Reality Tips.</span><span class="sxs-lookup"><span data-stu-id="c6dd5-117">In fact, we used MRTK version 2 to develop our inbox experiences, such as the out-of-box setup experience (OOBE) and our Mixed Reality Tips application.</span></span> <span data-ttu-id="c6dd5-118">Probabilmente avrai l'occasione anche di vedere nuove funzionalità di HoloLens 2 esposte tramite MRTK prima del rilascio, perché crediamo che questo sia il modo migliore per sviluppare sulla nostra piattaforma.</span><span class="sxs-lookup"><span data-stu-id="c6dd5-118">You can also expect to see new HoloLens 2 capabilities first exposed through MRTK because we believe it’s the best way to develop on our platform.</span></span> 

### <a name="modular"></a><span data-ttu-id="c6dd5-119">Modularità</span><span class="sxs-lookup"><span data-stu-id="c6dd5-119">Modular</span></span>

<span data-ttu-id="c6dd5-120">Il toolkit è stato creato in modo modulare, quindi non è necessario includerlo per intero nel progetto.</span><span class="sxs-lookup"><span data-stu-id="c6dd5-120">We have built it in a modular way, so you don't need to take every bit of the toolkit into your project.</span></span>  <span data-ttu-id="c6dd5-121">Questa caratteristica presenta alcuni vantaggi.</span><span class="sxs-lookup"><span data-stu-id="c6dd5-121">There are actually a few benefits to this.</span></span>  <span data-ttu-id="c6dd5-122">Consente di limitare le dimensioni del progetto e ne semplifica la gestione.</span><span class="sxs-lookup"><span data-stu-id="c6dd5-122">It keeps your project size smaller, and makes it easier to manage.</span></span>  <span data-ttu-id="c6dd5-123">Inoltre, poiché il toolkit è stato creato con oggetti gestibili tramite script ed è dotato di interfaccia, puoi anche sostituire i componenti inclusi nel toolkit con componenti personalizzati, per supportare altri servizi, sistemi e piattaforme.</span><span class="sxs-lookup"><span data-stu-id="c6dd5-123">Additionally, because it’s built with scriptable objects and is interface-driven, it’s also possible for you to replace the components that are included with your own, to support other services, systems, and platforms.</span></span>

### <a name="cross-platform"></a><span data-ttu-id="c6dd5-124">Multipiattaforma</span><span class="sxs-lookup"><span data-stu-id="c6dd5-124">Cross-platform</span></span>

<span data-ttu-id="c6dd5-125">Il toolkit include il supporto per più piattaforme.</span><span class="sxs-lookup"><span data-stu-id="c6dd5-125">Speaking of other platforms, it has cross-platform support.</span></span>  <span data-ttu-id="c6dd5-126">Anche se questo non significa che ogni singola piattaforma sia supportata, Microsoft ha fatto in modo che nessuna parte di codice del toolkit smetta di funzionare quando si scelgono altre piattaforme di destinazione per la build.</span><span class="sxs-lookup"><span data-stu-id="c6dd5-126">And while this doesn’t mean every single platform is supported, we have made sure none of the toolkit code will break when you switch your build target to other platforms.</span></span>  <span data-ttu-id="c6dd5-127">L'affidabilità e l'estendibilità della progettazione modulare permettono alle app di supportare più piattaforme, ad esempio ARCore, ARKit e OpenVR.</span><span class="sxs-lookup"><span data-stu-id="c6dd5-127">The robustness and extensibility of the modular design sets your apps up to support multiple platforms, such as ARCore, ARKit, and OpenVR.</span></span>

### <a name="performant"></a><span data-ttu-id="c6dd5-128">Ottime prestazioni</span><span class="sxs-lookup"><span data-stu-id="c6dd5-128">Performant</span></span>

<span data-ttu-id="c6dd5-129">Dovendo lavorare con piattaforme mobili, abbiamo realizzato il toolkit tenendo sempre ben presenti le prestazioni.</span><span class="sxs-lookup"><span data-stu-id="c6dd5-129">Working with mobile platforms, we constructed it with performance in mind.</span></span>  <span data-ttu-id="c6dd5-130">Questo aspetto è molto importante e Microsoft ha voluto assicurarsi che gli strumenti non creino difficoltà agli utenti.</span><span class="sxs-lookup"><span data-stu-id="c6dd5-130">This is super important, and we wanted to ensure that the tools aren't going to work against you.</span></span>

## <a name="see-also"></a><span data-ttu-id="c6dd5-131">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="c6dd5-131">See also</span></span>

* [<span data-ttu-id="c6dd5-132">Installare gli strumenti</span><span class="sxs-lookup"><span data-stu-id="c6dd5-132">Install the tools</span></span>](../install-the-tools.md)
* [<span data-ttu-id="c6dd5-133">Sviluppo con MRTK per Unity</span><span class="sxs-lookup"><span data-stu-id="c6dd5-133">Developing with MRTK for Unity</span></span>](unity-development-overview.md)
* [<span data-ttu-id="c6dd5-134">MRTK - Guida all'installazione (GitHub)</span><span class="sxs-lookup"><span data-stu-id="c6dd5-134">MRTK - Installation guide (GitHub)</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html)
* [<span data-ttu-id="c6dd5-135">MRTK - Home page della documentazione (GitHub)</span><span class="sxs-lookup"><span data-stu-id="c6dd5-135">MRTK - Documentation home (GitHub)</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)
* [<span data-ttu-id="c6dd5-136">Porting da HoloToolkit/MRTK a MRTK versione 2 (GitHub)</span><span class="sxs-lookup"><span data-stu-id="c6dd5-136">Porting from HoloToolkit/MRTK to MRTK version 2 (GitHub)</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/HTKToMRTKPortingGuide.html)

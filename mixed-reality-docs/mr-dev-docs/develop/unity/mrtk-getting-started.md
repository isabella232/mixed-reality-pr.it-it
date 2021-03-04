---
title: Introduzione a MRKT per Unity
description: Introduzione a tutte le funzionalità che Mixed Reality Toolkit con supporto multipiattaforma può offrire ai nuovi sviluppatori di realtà mista.
author: cre8ivepark
ms.author: dongpark
ms.date: 05/15/2019
ms.topic: article
ms.localizationpriority: high
keywords: Windows Mixed Reality, test, Mixed Reality Toolkit, MRTK versione 2, MRTK, strumenti, SDK, HoloLens, HoloLens 2, visore VR realtà mista, visore VR di windows mixed reality, visore per realtà virtuale, multipiattaforma
ms.openlocfilehash: b2fdf1114e30afc3d34582ebb71dd24bb8bf324d
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/03/2021
ms.locfileid: "101759707"
---
# <a name="introducing-mrtk-for-unity"></a><span data-ttu-id="2705a-104">Introduzione a MRKT per Unity</span><span class="sxs-lookup"><span data-stu-id="2705a-104">Introducing MRTK for Unity</span></span>

![MRTK](../../design/images/MRTK_UX_Hero.png)

## <a name="what-is-mixed-reality-toolkit-mrtk"></a><span data-ttu-id="2705a-106">Che cos'è Mixed Reality Toolkit (MRTK)?</span><span class="sxs-lookup"><span data-stu-id="2705a-106">What is Mixed Reality Toolkit (MRTK)?</span></span>

<span data-ttu-id="2705a-107">MRTK è uno straordinario toolkit open source disponibile sin dalla prima versione di HoloLens.</span><span class="sxs-lookup"><span data-stu-id="2705a-107">MRTK is an amazing open-source toolkit that has been around since the HoloLens was first released.</span></span> <span data-ttu-id="2705a-108">Il toolkit non avrebbe raggiunto i livelli attuali senza il contributo e l'impegno costante della community di sviluppatori Microsoft.</span><span class="sxs-lookup"><span data-stu-id="2705a-108">The toolkit wouldn't be where it is today without the hard work of our contributing developer community.</span></span> <span data-ttu-id="2705a-109">Negli ultimi tre anni abbiamo acquisito feedback dalla community di sviluppatori e abbiamo creato MRTK v2 tenendo conto delle principali esigenze e segnalazioni.</span><span class="sxs-lookup"><span data-stu-id="2705a-109">Over the past three years, we've listened to the feedback of our developer community, and built MRTK v2 to take the biggest concerns into account.</span></span>  

<span data-ttu-id="2705a-110">MRTK per Unity è un kit di sviluppo multipiattaforma open source per applicazioni di realtà mista.</span><span class="sxs-lookup"><span data-stu-id="2705a-110">MRTK for Unity is an open-source, cross-platform development kit for mixed reality applications.</span></span> <span data-ttu-id="2705a-111">Il modo più semplice per installare il Toolkit è con la nuova applicazione di strumenti per la funzionalità di realtà mista.</span><span class="sxs-lookup"><span data-stu-id="2705a-111">The easiest way to install the toolkit is with our new Mixed Reality Feature Tool application.</span></span> <span data-ttu-id="2705a-112">Seguire le [istruzioni per l'installazione e l'utilizzo](welcome-to-mr-feature-tool.md) e selezionare il pacchetto **mixed reality Toolkit Foundation** nella categoria Mixed Reality Toolkit.</span><span class="sxs-lookup"><span data-stu-id="2705a-112">Follow our [installation and usage instructions](welcome-to-mr-feature-tool.md) and select the **Mixed Reality Toolkit Foundation** package in the Mixed Reality Toolkit category.</span></span> 

<span data-ttu-id="2705a-113">MRTK per Unity offre un sistema di input multipiattaforma, componenti fondamentali e blocchi predefiniti comuni per le interazioni spaziali.</span><span class="sxs-lookup"><span data-stu-id="2705a-113">MRTK for Unity provides a cross-platform input system, foundational components, and common building blocks for spatial interactions.</span></span> <span data-ttu-id="2705a-114">MRTK versione 2 intende accelerare lo sviluppo di applicazioni per Microsoft HoloLens, i visori VR immersive di Windows Mixed Reality e la piattaforma OpenVR.</span><span class="sxs-lookup"><span data-stu-id="2705a-114">MRTK version 2 intends to speed up application development for Microsoft HoloLens, Windows Mixed Reality immersive (VR) headsets, and OpenVR platform.</span></span> <span data-ttu-id="2705a-115">Il progetto mira a ridurre le barriere di accesso, creare applicazioni di realtà mista e restituire contributi alla community per continuare a crescere insieme.</span><span class="sxs-lookup"><span data-stu-id="2705a-115">The project is aimed at reducing barriers to entry, creating mixed reality applications, and contributing back to the community as we all grow.</span></span>

<br>

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4IkCG]

<span data-ttu-id="2705a-116">Per altri dettagli sulle funzionalità, vedere la [documentazione di MRTK](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/) .</span><span class="sxs-lookup"><span data-stu-id="2705a-116">Take a look at [MRTK's documentation](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/) for more feature details.</span></span>

## <a name="new-with-mrtk-v2"></a><span data-ttu-id="2705a-117">Novità di MRTK v2</span><span class="sxs-lookup"><span data-stu-id="2705a-117">New with MRTK v2</span></span>

<span data-ttu-id="2705a-118">È importante sottolineare l'impegno che abbiamo dedicato a questi strumenti della piattaforma.</span><span class="sxs-lookup"><span data-stu-id="2705a-118">We want to stress our commitment to these platform tools.</span></span>  <span data-ttu-id="2705a-119">Infatti, abbiamo usato MRTK versione 2 per sviluppare le esperienze integrate, come l'esperienza di installazione predefinita (OOBE) e l'applicazione Mixed Reality Tips.</span><span class="sxs-lookup"><span data-stu-id="2705a-119">In fact, we used MRTK version 2 to develop our inbox experiences, such as the out-of-box setup experience (OOBE) and our Mixed Reality Tips application.</span></span> <span data-ttu-id="2705a-120">Probabilmente avrai l'occasione anche di vedere nuove funzionalità di HoloLens 2 esposte tramite MRTK prima del rilascio, perché crediamo che questo sia il modo migliore per sviluppare sulla nostra piattaforma.</span><span class="sxs-lookup"><span data-stu-id="2705a-120">You can also expect to see new HoloLens 2 capabilities first exposed through MRTK because we believe it’s the best way to develop on our platform.</span></span> 

### <a name="modular"></a><span data-ttu-id="2705a-121">Modularità</span><span class="sxs-lookup"><span data-stu-id="2705a-121">Modular</span></span>

<span data-ttu-id="2705a-122">Il toolkit è stato creato in modo modulare, quindi non è necessario includerlo per intero nel progetto.</span><span class="sxs-lookup"><span data-stu-id="2705a-122">We have built it in a modular way, so you don't need to take every bit of the toolkit into your project.</span></span>  <span data-ttu-id="2705a-123">Questa caratteristica presenta alcuni vantaggi.</span><span class="sxs-lookup"><span data-stu-id="2705a-123">There are actually a few benefits to this.</span></span>  <span data-ttu-id="2705a-124">Consente di limitare le dimensioni del progetto e ne semplifica la gestione.</span><span class="sxs-lookup"><span data-stu-id="2705a-124">It keeps your project size smaller, and makes it easier to manage.</span></span>  <span data-ttu-id="2705a-125">Inoltre, poiché il toolkit è stato creato con oggetti gestibili tramite script ed è dotato di interfaccia, puoi anche sostituire i componenti inclusi nel toolkit con componenti personalizzati, per supportare altri servizi, sistemi e piattaforme.</span><span class="sxs-lookup"><span data-stu-id="2705a-125">Additionally, because it’s built with scriptable objects and is interface-driven, it’s also possible for you to replace the components that are included with your own, to support other services, systems, and platforms.</span></span>

### <a name="cross-platform"></a><span data-ttu-id="2705a-126">Multipiattaforma</span><span class="sxs-lookup"><span data-stu-id="2705a-126">Cross-platform</span></span>

<span data-ttu-id="2705a-127">Il toolkit include il supporto per più piattaforme.</span><span class="sxs-lookup"><span data-stu-id="2705a-127">Speaking of other platforms, it has cross-platform support.</span></span>  <span data-ttu-id="2705a-128">Anche se questo non significa che ogni singola piattaforma sia supportata, Microsoft ha fatto in modo che nessuna parte di codice del toolkit smetta di funzionare quando si scelgono altre piattaforme di destinazione per la build.</span><span class="sxs-lookup"><span data-stu-id="2705a-128">And while this doesn’t mean every single platform is supported, we have made sure none of the toolkit code will break when you switch your build target to other platforms.</span></span>  <span data-ttu-id="2705a-129">L'affidabilità e l'estendibilità della progettazione modulare permettono alle app di supportare più piattaforme, ad esempio ARCore, ARKit e OpenVR.</span><span class="sxs-lookup"><span data-stu-id="2705a-129">The robustness and extensibility of the modular design sets your apps up to support multiple platforms, such as ARCore, ARKit, and OpenVR.</span></span>

### <a name="performant"></a><span data-ttu-id="2705a-130">Ottime prestazioni</span><span class="sxs-lookup"><span data-stu-id="2705a-130">Performant</span></span>

<span data-ttu-id="2705a-131">Dovendo lavorare con piattaforme mobili, abbiamo realizzato il toolkit tenendo sempre ben presenti le prestazioni.</span><span class="sxs-lookup"><span data-stu-id="2705a-131">Working with mobile platforms, we constructed it with performance in mind.</span></span>  <span data-ttu-id="2705a-132">Questo aspetto è molto importante e Microsoft ha voluto assicurarsi che gli strumenti non creino difficoltà agli utenti.</span><span class="sxs-lookup"><span data-stu-id="2705a-132">This is super important, and we wanted to ensure that the tools aren't going to work against you.</span></span>

## <a name="see-also"></a><span data-ttu-id="2705a-133">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="2705a-133">See also</span></span>

* [<span data-ttu-id="2705a-134">Installare gli strumenti</span><span class="sxs-lookup"><span data-stu-id="2705a-134">Install the tools</span></span>](../install-the-tools.md)
* [<span data-ttu-id="2705a-135">Strumento per la funzionalità di realtà mista</span><span class="sxs-lookup"><span data-stu-id="2705a-135">Mixed Reality Feature Tool</span></span>](welcome-to-mr-feature-tool.md)
* [<span data-ttu-id="2705a-136">Sviluppo con MRTK per Unity</span><span class="sxs-lookup"><span data-stu-id="2705a-136">Developing with MRTK for Unity</span></span>](unity-development-overview.md)
* [<span data-ttu-id="2705a-137">MRTK-Home page della documentazione</span><span class="sxs-lookup"><span data-stu-id="2705a-137">MRTK - Documentation home</span></span>](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/)
* [<span data-ttu-id="2705a-138">Porting da HoloToolkit/MRTK a MRTK versione 2 (GitHub)</span><span class="sxs-lookup"><span data-stu-id="2705a-138">Porting from HoloToolkit/MRTK to MRTK version 2 (GitHub)</span></span>](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/updates-deployment/hrtk-to-mrtk-porting-guide.md)

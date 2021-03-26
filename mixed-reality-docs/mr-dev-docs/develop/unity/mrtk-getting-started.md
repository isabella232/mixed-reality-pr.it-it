---
title: Introduzione a MRKT per Unity
description: Introduzione a tutte le funzionalità che Mixed Reality Toolkit con supporto multipiattaforma può offrire ai nuovi sviluppatori di realtà mista.
author: cre8ivepark
ms.author: dongpark
ms.date: 05/15/2019
ms.topic: article
ms.localizationpriority: high
keywords: Windows Mixed Reality, test, Mixed Reality Toolkit, MRTK versione 2, MRTK, strumenti, SDK, HoloLens, HoloLens 2, visore VR realtà mista, visore VR di windows mixed reality, visore per realtà virtuale, multipiattaforma
ms.openlocfilehash: 9e816f0e10416fb5b5103d4fd98b47738ed156d6
ms.sourcegitcommit: ac315c1d35f2b9c431e79bc3f1212215301bb867
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105549931"
---
# <a name="introducing-mrtk-for-unity"></a><span data-ttu-id="8eade-104">Introduzione a MRKT per Unity</span><span class="sxs-lookup"><span data-stu-id="8eade-104">Introducing MRTK for Unity</span></span>

![MRTK](../../design/images/MRTK_UX_Hero.png)

## <a name="what-is-mixed-reality-toolkit-mrtk"></a><span data-ttu-id="8eade-106">Che cos'è Mixed Reality Toolkit (MRTK)?</span><span class="sxs-lookup"><span data-stu-id="8eade-106">What is Mixed Reality Toolkit (MRTK)?</span></span>

<span data-ttu-id="8eade-107">MRTK è uno straordinario toolkit open source disponibile sin dalla prima versione di HoloLens.</span><span class="sxs-lookup"><span data-stu-id="8eade-107">MRTK is an amazing open-source toolkit that has been around since the HoloLens was first released.</span></span> <span data-ttu-id="8eade-108">Il toolkit non avrebbe raggiunto i livelli attuali senza il contributo e l'impegno costante della community di sviluppatori Microsoft.</span><span class="sxs-lookup"><span data-stu-id="8eade-108">The toolkit wouldn't be where it is today without the hard work of our contributing developer community.</span></span> <span data-ttu-id="8eade-109">Negli ultimi tre anni abbiamo acquisito feedback dalla community di sviluppatori e abbiamo creato MRTK v2 tenendo conto delle principali esigenze e segnalazioni.</span><span class="sxs-lookup"><span data-stu-id="8eade-109">Over the past three years, we've listened to the feedback of our developer community, and built MRTK v2 to take the biggest concerns into account.</span></span>  

<span data-ttu-id="8eade-110">MRTK per Unity è un kit di sviluppo multipiattaforma open source per applicazioni di realtà mista.</span><span class="sxs-lookup"><span data-stu-id="8eade-110">MRTK for Unity is an open-source, cross-platform development kit for mixed reality applications.</span></span> <span data-ttu-id="8eade-111">Il modo più semplice per installare il Toolkit è con la nuova applicazione di strumenti per la funzionalità di realtà mista.</span><span class="sxs-lookup"><span data-stu-id="8eade-111">The easiest way to install the toolkit is with our new Mixed Reality Feature Tool application.</span></span> <span data-ttu-id="8eade-112">Seguire le [istruzioni per l'installazione e l'utilizzo](welcome-to-mr-feature-tool.md) e selezionare il pacchetto **mixed reality Toolkit Foundation** nella categoria Mixed Reality Toolkit.</span><span class="sxs-lookup"><span data-stu-id="8eade-112">Follow our [installation and usage instructions](welcome-to-mr-feature-tool.md) and select the **Mixed Reality Toolkit Foundation** package in the Mixed Reality Toolkit category.</span></span>

<span data-ttu-id="8eade-113">MRTK per Unity offre un sistema di input multipiattaforma, componenti fondamentali e blocchi predefiniti comuni per le interazioni spaziali.</span><span class="sxs-lookup"><span data-stu-id="8eade-113">MRTK for Unity provides a cross-platform input system, foundational components, and common building blocks for spatial interactions.</span></span> <span data-ttu-id="8eade-114">MRTK versione 2 intende accelerare lo sviluppo di applicazioni per Microsoft HoloLens, i visori VR immersive di Windows Mixed Reality e la piattaforma OpenVR.</span><span class="sxs-lookup"><span data-stu-id="8eade-114">MRTK version 2 intends to speed up application development for Microsoft HoloLens, Windows Mixed Reality immersive (VR) headsets, and OpenVR platform.</span></span> <span data-ttu-id="8eade-115">Il progetto mira a ridurre le barriere di accesso, creare applicazioni di realtà mista e restituire contributi alla community per continuare a crescere insieme.</span><span class="sxs-lookup"><span data-stu-id="8eade-115">The project is aimed at reducing barriers to entry, creating mixed reality applications, and contributing back to the community as we all grow.</span></span>

<br>

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4IkCG]

> [!div class="nextstepaction"]
> [<span data-ttu-id="8eade-116">Prova le nostre esercitazioni su MRTK</span><span class="sxs-lookup"><span data-stu-id="8eade-116">Try out our MRTK tutorials</span></span>](tutorials/mr-learning-base-01.md)

<span data-ttu-id="8eade-117">Per altri dettagli sulle funzionalità, vedere la [documentazione di MRTK](/windows/mixed-reality/mrtk-unity) .</span><span class="sxs-lookup"><span data-stu-id="8eade-117">Take a look at [MRTK's documentation](/windows/mixed-reality/mrtk-unity) for more feature details.</span></span>

## <a name="new-with-mrtk-v2"></a><span data-ttu-id="8eade-118">Novità di MRTK v2</span><span class="sxs-lookup"><span data-stu-id="8eade-118">New with MRTK v2</span></span>

<span data-ttu-id="8eade-119">È importante sottolineare l'impegno che abbiamo dedicato a questi strumenti della piattaforma.</span><span class="sxs-lookup"><span data-stu-id="8eade-119">We want to stress our commitment to these platform tools.</span></span>  <span data-ttu-id="8eade-120">Infatti, abbiamo usato MRTK versione 2 per sviluppare le esperienze integrate, come l'esperienza di installazione predefinita (OOBE) e l'applicazione Mixed Reality Tips.</span><span class="sxs-lookup"><span data-stu-id="8eade-120">In fact, we used MRTK version 2 to develop our inbox experiences, such as the out-of-box setup experience (OOBE) and our Mixed Reality Tips application.</span></span> <span data-ttu-id="8eade-121">Probabilmente avrai l'occasione anche di vedere nuove funzionalità di HoloLens 2 esposte tramite MRTK prima del rilascio, perché crediamo che questo sia il modo migliore per sviluppare sulla nostra piattaforma.</span><span class="sxs-lookup"><span data-stu-id="8eade-121">You can also expect to see new HoloLens 2 capabilities first exposed through MRTK because we believe it’s the best way to develop on our platform.</span></span>

### <a name="modular"></a><span data-ttu-id="8eade-122">Modularità</span><span class="sxs-lookup"><span data-stu-id="8eade-122">Modular</span></span>

<span data-ttu-id="8eade-123">Il toolkit è stato creato in modo modulare, quindi non è necessario includerlo per intero nel progetto.</span><span class="sxs-lookup"><span data-stu-id="8eade-123">We have built it in a modular way, so you don't need to take every bit of the toolkit into your project.</span></span>  <span data-ttu-id="8eade-124">Questa caratteristica presenta alcuni vantaggi.</span><span class="sxs-lookup"><span data-stu-id="8eade-124">There are actually a few benefits to this.</span></span>  <span data-ttu-id="8eade-125">Consente di limitare le dimensioni del progetto e ne semplifica la gestione.</span><span class="sxs-lookup"><span data-stu-id="8eade-125">It keeps your project size smaller, and makes it easier to manage.</span></span>  <span data-ttu-id="8eade-126">Inoltre, poiché il toolkit è stato creato con oggetti gestibili tramite script ed è dotato di interfaccia, puoi anche sostituire i componenti inclusi nel toolkit con componenti personalizzati, per supportare altri servizi, sistemi e piattaforme.</span><span class="sxs-lookup"><span data-stu-id="8eade-126">Additionally, because it’s built with scriptable objects and is interface-driven, it’s also possible for you to replace the components that are included with your own, to support other services, systems, and platforms.</span></span>

### <a name="cross-platform"></a><span data-ttu-id="8eade-127">Multipiattaforma</span><span class="sxs-lookup"><span data-stu-id="8eade-127">Cross-platform</span></span>

<span data-ttu-id="8eade-128">Il toolkit include il supporto per più piattaforme.</span><span class="sxs-lookup"><span data-stu-id="8eade-128">Speaking of other platforms, it has cross-platform support.</span></span>  <span data-ttu-id="8eade-129">Anche se questo non significa che ogni singola piattaforma sia supportata, Microsoft ha fatto in modo che nessuna parte di codice del toolkit smetta di funzionare quando si scelgono altre piattaforme di destinazione per la build.</span><span class="sxs-lookup"><span data-stu-id="8eade-129">And while this doesn’t mean every single platform is supported, we have made sure none of the toolkit code will break when you switch your build target to other platforms.</span></span>  <span data-ttu-id="8eade-130">L'affidabilità e l'estendibilità della progettazione modulare permettono alle app di supportare più piattaforme, ad esempio ARCore, ARKit e OpenVR.</span><span class="sxs-lookup"><span data-stu-id="8eade-130">The robustness and extensibility of the modular design sets your apps up to support multiple platforms, such as ARCore, ARKit, and OpenVR.</span></span>

### <a name="performant"></a><span data-ttu-id="8eade-131">Ottime prestazioni</span><span class="sxs-lookup"><span data-stu-id="8eade-131">Performant</span></span>

<span data-ttu-id="8eade-132">Dovendo lavorare con piattaforme mobili, abbiamo realizzato il toolkit tenendo sempre ben presenti le prestazioni.</span><span class="sxs-lookup"><span data-stu-id="8eade-132">Working with mobile platforms, we constructed it with performance in mind.</span></span>  <span data-ttu-id="8eade-133">Questo aspetto è molto importante e Microsoft ha voluto assicurarsi che gli strumenti non creino difficoltà agli utenti.</span><span class="sxs-lookup"><span data-stu-id="8eade-133">This is super important, and we wanted to ensure that the tools aren't going to work against you.</span></span>

## <a name="see-also"></a><span data-ttu-id="8eade-134">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="8eade-134">See also</span></span>

* [<span data-ttu-id="8eade-135">Installare gli strumenti</span><span class="sxs-lookup"><span data-stu-id="8eade-135">Install the tools</span></span>](../install-the-tools.md)
* [<span data-ttu-id="8eade-136">Strumento per la funzionalità di realtà mista</span><span class="sxs-lookup"><span data-stu-id="8eade-136">Mixed Reality Feature Tool</span></span>](welcome-to-mr-feature-tool.md)
* [<span data-ttu-id="8eade-137">Sviluppo con MRTK per Unity</span><span class="sxs-lookup"><span data-stu-id="8eade-137">Developing with MRTK for Unity</span></span>](unity-development-overview.md)
* [<span data-ttu-id="8eade-138">MRTK-Home page della documentazione</span><span class="sxs-lookup"><span data-stu-id="8eade-138">MRTK - Documentation home</span></span>](/windows/mixed-reality/mrtk-unity/)
* [<span data-ttu-id="8eade-139">Porting da HoloToolkit/MRTK a MRTK versione 2</span><span class="sxs-lookup"><span data-stu-id="8eade-139">Porting from HoloToolkit/MRTK to MRTK version 2</span></span>](/windows/mixed-reality/mrtk-unity/updates-deployment/htk-to-mrtk-porting-guide)
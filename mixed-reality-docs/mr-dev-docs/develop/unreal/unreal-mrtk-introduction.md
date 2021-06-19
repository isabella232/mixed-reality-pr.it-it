---
title: Introduzione a MRTK per Unreal
description: Introduzione a tutto ciò che Mixed Reality Toolkit per Unreal offre nuovi sviluppatori di realtà mista.
author: hferrone
ms.author: v-hferrone
ms.date: 01/08/2021
ms.topic: article
ms.localizationpriority: high
keywords: Windows Mixed Reality, test, Mixed Reality Toolkit, MRTK versione 2, MRTK, strumenti, SDK, HoloLens, HoloLens 2, visore VR realtà mista, visore VR di windows mixed reality, visore per realtà virtuale, multipiattaforma
ms.openlocfilehash: 3d46b92dbf3182ca5a50a8e106d2b947e4f7120f
ms.sourcegitcommit: 6ade7e8ebab7003fc24f9e0b5fa81d091369622c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2021
ms.locfileid: "112394285"
---
# <a name="introducing-mrtk-for-unreal"></a><span data-ttu-id="3735e-104">Introduzione a MRTK per Unreal</span><span class="sxs-lookup"><span data-stu-id="3735e-104">Introducing MRTK for Unreal</span></span>

![Immagine del banner MRTK](../../design/images/MRTK_UX_Hero.png)

## <a name="what-is-mixed-reality-toolkit-mrtk"></a><span data-ttu-id="3735e-106">Che cos'è Mixed Reality Toolkit (MRTK)?</span><span class="sxs-lookup"><span data-stu-id="3735e-106">What is Mixed Reality Toolkit (MRTK)?</span></span>

<span data-ttu-id="3735e-107">MRTK è uno straordinario toolkit open source disponibile sin dalla prima versione di HoloLens.</span><span class="sxs-lookup"><span data-stu-id="3735e-107">MRTK is an amazing open-source toolkit that has been around since the HoloLens was first released.</span></span> <span data-ttu-id="3735e-108">Il toolkit non avrebbe raggiunto i livelli attuali senza il contributo e l'impegno costante della community di sviluppatori Microsoft.</span><span class="sxs-lookup"><span data-stu-id="3735e-108">The toolkit wouldn't be where it is today without the hard work of our contributing developer community.</span></span> 

<span data-ttu-id="3735e-109">Mixed Reality Toolkit for Unreal (MRTK-Unreal) è un set di componenti, sotto forma di plug-in, esempi e documentazione, progettati per facilitare lo sviluppo di applicazioni di realtà mista usando il motore Unreal.</span><span class="sxs-lookup"><span data-stu-id="3735e-109">The Mixed Reality Toolkit for Unreal (MRTK-Unreal) is a set of components, in the form of plugins, samples and documentation, designed to help development of Mixed Reality applications using the Unreal Engine.</span></span> <span data-ttu-id="3735e-110">Attualmente, il toolkit è costituito da:</span><span class="sxs-lookup"><span data-stu-id="3735e-110">Currently, the toolkit consists of:</span></span>
* <span data-ttu-id="3735e-111">[UX Tools for Unreal,](https://github.com/microsoft/MixedReality-UXTools-Unreal)che fornisce codice, progetti ed esempi per implementare le funzionalità dell'esperienza utente per le applicazioni Hololens 2.</span><span class="sxs-lookup"><span data-stu-id="3735e-111">[UX Tools for Unreal](https://github.com/microsoft/MixedReality-UXTools-Unreal), which provides code, blueprints, and examples to implement UX features for Hololens 2 applications.</span></span>
* <span data-ttu-id="3735e-112">[Strumenti di grafica per Unreal](https://github.com/microsoft/MixedReality-GraphicsTools-Unreal), che consente di migliorare la fedeltà visiva delle applicazioni di realtà mista mantenendo i budget per le prestazioni.</span><span class="sxs-lookup"><span data-stu-id="3735e-112">[Graphics Tools for Unreal](https://github.com/microsoft/MixedReality-GraphicsTools-Unreal), which helps improve the visual fidelity of Mixed Reality applications while staying within performance budgets.</span></span>

<span data-ttu-id="3735e-113">Esaminare la documentazione [di MRTK](https://microsoft.github.io/MixedReality-UXTools-Unreal/README.html) in GitHub e iniziare a usare le guide all'installazione degli strumenti [UX](https://microsoft.github.io/MixedReality-UXTools-Unreal/Docs/Installation.html) o [degli strumenti](https://github.com/microsoft/MixedReality-GraphicsTools-Unreal/blob/main/Docs/Installation.md) di grafica.</span><span class="sxs-lookup"><span data-stu-id="3735e-113">Take a look at [MRTK's documentation on GitHub](https://microsoft.github.io/MixedReality-UXTools-Unreal/README.html) and get started with [UX Tools](https://microsoft.github.io/MixedReality-UXTools-Unreal/Docs/Installation.html) or [Graphics Tools](https://github.com/microsoft/MixedReality-GraphicsTools-Unreal/blob/main/Docs/Installation.md) installation guides.</span></span>

### <a name="modular"></a><span data-ttu-id="3735e-114">Modularità</span><span class="sxs-lookup"><span data-stu-id="3735e-114">Modular</span></span>

<span data-ttu-id="3735e-115">È stato creato MRTK Unreal in modo modulare, quindi non è necessario importare tutti i componenti del toolkit nel progetto.</span><span class="sxs-lookup"><span data-stu-id="3735e-115">We've built MRTK Unreal in a modular way, so you don't need to take every bit of the toolkit into your project.</span></span> <span data-ttu-id="3735e-116">È possibile selezionare e scegliere i plug-in necessari e aggiungerli o rimuoverli ogni volta che lo si desidera.</span><span class="sxs-lookup"><span data-stu-id="3735e-116">You can pick and choose the plugins you need, and add or remove them whenever you see fit.</span></span> <span data-ttu-id="3735e-117">Questo approccio mantiene le dimensioni del progetto più piccole e semplifica la gestione.</span><span class="sxs-lookup"><span data-stu-id="3735e-117">This approach keeps your project size smaller and makes it easier to manage.</span></span>  

### <a name="performant"></a><span data-ttu-id="3735e-118">Ottime prestazioni</span><span class="sxs-lookup"><span data-stu-id="3735e-118">Performant</span></span>

<span data-ttu-id="3735e-119">Lavorando con le piattaforme mobili, è stato creato MRTK Unreal con le prestazioni in considerazione.</span><span class="sxs-lookup"><span data-stu-id="3735e-119">Working with mobile platforms, we constructed MRTK Unreal with performance in mind.</span></span> <span data-ttu-id="3735e-120">Si tratta di un aspetto estremamente importante e si è voluto garantire che gli strumenti non funzionino con l'utente.</span><span class="sxs-lookup"><span data-stu-id="3735e-120">This is super important and we wanted to ensure that the tools aren't going to work against you.</span></span>

## <a name="project-setup"></a><span data-ttu-id="3735e-121">Configurazione del progetto</span><span class="sxs-lookup"><span data-stu-id="3735e-121">Project setup</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="3735e-122">Scaricare un motore Unreal e MRTK</span><span class="sxs-lookup"><span data-stu-id="3735e-122">Download Unreal Engine and MRTK</span></span>](unreal-project-setup.md)

## <a name="see-also"></a><span data-ttu-id="3735e-123">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="3735e-123">See also</span></span>

* [<span data-ttu-id="3735e-124">Installare gli strumenti</span><span class="sxs-lookup"><span data-stu-id="3735e-124">Install the tools</span></span>](../install-the-tools.md)
* [<span data-ttu-id="3735e-125">Sviluppo con MRTK per Unreal</span><span class="sxs-lookup"><span data-stu-id="3735e-125">Developing with MRTK for Unreal</span></span>](unreal-development-overview.md)
* [<span data-ttu-id="3735e-126">Strumenti dell'esperienza utente - Guida all'installazione (GitHub)</span><span class="sxs-lookup"><span data-stu-id="3735e-126">UX Tools - Installation guide (GitHub)</span></span>](https://microsoft.github.io/MixedReality-UXTools-Unreal/Docs/Installation.html)
* [<span data-ttu-id="3735e-127">Strumenti dell'esperienza utente- Home page della documentazione (GitHub)</span><span class="sxs-lookup"><span data-stu-id="3735e-127">UX Tools- Documentation home (GitHub)</span></span>](https://microsoft.github.io/MixedReality-UXTools-Unreal/README.html)
* [<span data-ttu-id="3735e-128">Strumenti di grafica - Guida all'installazione (GitHub)</span><span class="sxs-lookup"><span data-stu-id="3735e-128">Graphics Tools - Installation guide (GitHub)</span></span>](https://github.com/microsoft/MixedReality-GraphicsTools-Unreal/blob/main/Docs/Installation.md)
* [<span data-ttu-id="3735e-129">Strumenti di grafica - Home page della documentazione (GitHub)</span><span class="sxs-lookup"><span data-stu-id="3735e-129">Graphics Tools - Documentation home (GitHub)</span></span>](https://github.com/microsoft/MixedReality-GraphicsTools-Unreal/)
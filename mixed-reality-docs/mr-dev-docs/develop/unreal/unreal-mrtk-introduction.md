---
title: Introduzione a MRTK per Unreal
description: Per iniziare a usare tutto il Toolkit di realtà mista per Unreal è necessario offrire nuovi sviluppatori di realtà mista.
author: hferrone
ms.author: v-hferrone
ms.date: 01/08/2021
ms.topic: article
ms.localizationpriority: high
keywords: Windows Mixed Reality, test, Mixed Reality Toolkit, MRTK versione 2, MRTK, strumenti, SDK, HoloLens, HoloLens 2, visore VR realtà mista, visore VR di windows mixed reality, visore per realtà virtuale, multipiattaforma
ms.openlocfilehash: 4aa21cbee75c4c362abfd609add922ad9c922682
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/20/2021
ms.locfileid: "98584830"
---
# <a name="introducing-mrtk-for-unreal"></a><span data-ttu-id="acf0e-104">Introduzione a MRTK per Unreal</span><span class="sxs-lookup"><span data-stu-id="acf0e-104">Introducing MRTK for Unreal</span></span>

![MRTK](../../design/images/MRTK_UX_Hero.png)

## <a name="what-is-mixed-reality-toolkit-mrtk"></a><span data-ttu-id="acf0e-106">Che cos'è Mixed Reality Toolkit (MRTK)?</span><span class="sxs-lookup"><span data-stu-id="acf0e-106">What is Mixed Reality Toolkit (MRTK)?</span></span>

<span data-ttu-id="acf0e-107">MRTK è uno straordinario toolkit open source disponibile sin dalla prima versione di HoloLens.</span><span class="sxs-lookup"><span data-stu-id="acf0e-107">MRTK is an amazing open-source toolkit that has been around since the HoloLens was first released.</span></span> <span data-ttu-id="acf0e-108">Il toolkit non avrebbe raggiunto i livelli attuali senza il contributo e l'impegno costante della community di sviluppatori Microsoft.</span><span class="sxs-lookup"><span data-stu-id="acf0e-108">The toolkit wouldn't be where it is today without the hard work of our contributing developer community.</span></span> 

<span data-ttu-id="acf0e-109">Il Toolkit di realtà mista per Unreal (MRTK-Unreal) è un set di componenti, sotto forma di plug-in, esempi e documentazione, progettati per favorire lo sviluppo di applicazioni con realtà mista usando il motore Unreal.</span><span class="sxs-lookup"><span data-stu-id="acf0e-109">The Mixed Reality Toolkit for Unreal (MRTK-Unreal) is a set of components, in the form of plugins, samples and documentation, designed to help development of Mixed Reality applications using the Unreal Engine.</span></span> <span data-ttu-id="acf0e-110">Attualmente, il Toolkit è costituito da:</span><span class="sxs-lookup"><span data-stu-id="acf0e-110">Currently, the toolkit consists of:</span></span>
* <span data-ttu-id="acf0e-111">[Strumenti UX per Unreal](https://github.com/microsoft/MixedReality-UXTools-Unreal), che fornisce codice, progetti ed esempi per implementare le funzionalità UX per le applicazioni Hololens 2.</span><span class="sxs-lookup"><span data-stu-id="acf0e-111">[UX Tools for Unreal](https://github.com/microsoft/MixedReality-UXTools-Unreal), which provides code, blueprints, and examples to implement UX features for Hololens 2 applications.</span></span>
* <span data-ttu-id="acf0e-112">[Strumenti di grafica per Unreal](https://github.com/microsoft/MixedReality-GraphicsTools-Unreal), che consente di migliorare la fedeltà visiva delle applicazioni per realtà miste rimanendo nel budget delle prestazioni.</span><span class="sxs-lookup"><span data-stu-id="acf0e-112">[Graphics Tools for Unreal](https://github.com/microsoft/MixedReality-GraphicsTools-Unreal), which helps improve the visual fidelity of Mixed Reality applications while staying within performance budgets.</span></span>

<br>

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4IkCG]

<span data-ttu-id="acf0e-113">Vedere la [documentazione di MRTK su GitHub](https://microsoft.github.io/MixedReality-UXTools-Unreal/README.html) e iniziare a usare gli [strumenti UX](https://microsoft.github.io/MixedReality-UXTools-Unreal/Docs/Installation.html) o le guide all'installazione di [strumenti di grafica](https://github.com/microsoft/MixedReality-GraphicsTools-Unreal/blob/main/Docs/Installation.md) .</span><span class="sxs-lookup"><span data-stu-id="acf0e-113">Take a look at [MRTK's documentation on GitHub](https://microsoft.github.io/MixedReality-UXTools-Unreal/README.html) and get started with [UX Tools](https://microsoft.github.io/MixedReality-UXTools-Unreal/Docs/Installation.html) or [Graphics Tools](https://github.com/microsoft/MixedReality-GraphicsTools-Unreal/blob/main/Docs/Installation.md) installation guides.</span></span>

### <a name="modular"></a><span data-ttu-id="acf0e-114">Modularità</span><span class="sxs-lookup"><span data-stu-id="acf0e-114">Modular</span></span>

<span data-ttu-id="acf0e-115">Abbiamo creato MRTK Unreal in modo modulare, quindi non è necessario eseguire ogni bit del Toolkit nel progetto.</span><span class="sxs-lookup"><span data-stu-id="acf0e-115">We've built MRTK Unreal in a modular way, so you don't need to take every bit of the toolkit into your project.</span></span> <span data-ttu-id="acf0e-116">È possibile selezionare e selezionare i plug-in necessari e aggiungerli o rimuoverli ogni volta che si ritengono idonei.</span><span class="sxs-lookup"><span data-stu-id="acf0e-116">You can pick and choose the plugins you need, and add or remove them whenever you see fit.</span></span> <span data-ttu-id="acf0e-117">Questo approccio mantiene le dimensioni del progetto più ridotte e ne semplifica la gestione.</span><span class="sxs-lookup"><span data-stu-id="acf0e-117">This approach keeps your project size smaller and makes it easier to manage.</span></span>  

### <a name="performant"></a><span data-ttu-id="acf0e-118">Ottime prestazioni</span><span class="sxs-lookup"><span data-stu-id="acf0e-118">Performant</span></span>

<span data-ttu-id="acf0e-119">Lavorando con le piattaforme mobili, abbiamo costruito MRTK con le prestazioni in mente.</span><span class="sxs-lookup"><span data-stu-id="acf0e-119">Working with mobile platforms, we constructed MRTK Unreal with performance in mind.</span></span> <span data-ttu-id="acf0e-120">Si tratta di un aspetto molto importante e abbiamo voluto assicurarci che gli strumenti non collaborino con te.</span><span class="sxs-lookup"><span data-stu-id="acf0e-120">This is super important and we wanted to ensure that the tools aren't going to work against you.</span></span>

## <a name="see-also"></a><span data-ttu-id="acf0e-121">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="acf0e-121">See also</span></span>

* [<span data-ttu-id="acf0e-122">Installare gli strumenti</span><span class="sxs-lookup"><span data-stu-id="acf0e-122">Install the tools</span></span>](../install-the-tools.md)
* [<span data-ttu-id="acf0e-123">Sviluppo con MRTK per Unreal</span><span class="sxs-lookup"><span data-stu-id="acf0e-123">Developing with MRTK for Unreal</span></span>](unreal-development-overview.md)
* [<span data-ttu-id="acf0e-124">Strumenti UX-Guida all'installazione (GitHub)</span><span class="sxs-lookup"><span data-stu-id="acf0e-124">UX Tools - Installation guide (GitHub)</span></span>](https://microsoft.github.io/MixedReality-UXTools-Unreal/Docs/Installation.html)
* [<span data-ttu-id="acf0e-125">Strumenti UX-Home page della documentazione (GitHub)</span><span class="sxs-lookup"><span data-stu-id="acf0e-125">UX Tools- Documentation home (GitHub)</span></span>](https://microsoft.github.io/MixedReality-UXTools-Unreal/README.html)
* [<span data-ttu-id="acf0e-126">Strumenti di grafica-Guida all'installazione (GitHub)</span><span class="sxs-lookup"><span data-stu-id="acf0e-126">Graphics Tools - Installation guide (GitHub)</span></span>](https://github.com/microsoft/MixedReality-GraphicsTools-Unreal/blob/main/Docs/Installation.md)
* [<span data-ttu-id="acf0e-127">Strumenti di grafica-Home page della documentazione (GitHub)</span><span class="sxs-lookup"><span data-stu-id="acf0e-127">Graphics Tools - Documentation home (GitHub)</span></span>](https://github.com/microsoft/MixedReality-GraphicsTools-Unreal/)
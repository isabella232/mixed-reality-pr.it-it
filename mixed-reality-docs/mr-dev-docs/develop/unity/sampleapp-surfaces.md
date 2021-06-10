---
title: Superfici
description: Informazioni su come creare delle perfomanti tattili con oggetti visivi, audio e tracciamento manuale articolato nell'app di esempio Surfaces.
author: cre8ivepark
ms.author: dongpark
ms.date: 06/18/2020
ms.topic: article
keywords: Windows Mixed Reality, progettazione, app di esempio, controlli, MRTK, Mixed Reality Toolkit, Unity, app di esempio, app di esempio, open source, Microsoft Store, HoloLens, visore per realtà mista, visore per realtà mista windows, visore per realtà virtuale
ms.openlocfilehash: 28f8bc1e1f30573936067a83b1ad26133c23c5b8
ms.sourcegitcommit: 719682f70a75f732b573442fae8987be1acaaf19
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/02/2021
ms.locfileid: "110743394"
---
# <a name="surfaces"></a><span data-ttu-id="ae95e-104">Superfici</span><span class="sxs-lookup"><span data-stu-id="ae95e-104">Surfaces</span></span>

>[!NOTE]
><span data-ttu-id="ae95e-105">Questo articolo illustra un esempio esplorativo creato in [Mixed Reality Design Labs,](https://github.com/Microsoft/MRDesignLabs_Unity)un luogo in cui vengono illustrate le informazioni e i suggerimenti per lo sviluppo di app di realtà mista.</span><span class="sxs-lookup"><span data-stu-id="ae95e-105">This article discusses an exploratory sample we’ve created in the [Mixed Reality Design Labs](https://github.com/Microsoft/MRDesignLabs_Unity), a place where we share our learnings about and suggestions for mixed reality app development.</span></span> <span data-ttu-id="ae95e-106">Gli articoli e il codice relativi alla progettazione si evolvono man appena si effettuano nuove individuazioni.</span><span class="sxs-lookup"><span data-stu-id="ae95e-106">Our design-related articles and code will evolve as we make new discoveries.</span></span>

<span data-ttu-id="ae95e-107">[Surfaces](https://github.com/microsoft/MRDL_Unity_Surfaces)  è un'app di esempio open source di Microsoft Mixed Reality Design Labs.</span><span class="sxs-lookup"><span data-stu-id="ae95e-107">[Surfaces](https://github.com/microsoft/MRDL_Unity_Surfaces)  is an open-source sample app from Microsoft's Mixed Reality Design Labs.</span></span> <span data-ttu-id="ae95e-108">Esplora come creare una emozione tattile con oggetti visivi, audio e tracciamento manuale completamente articolato.</span><span class="sxs-lookup"><span data-stu-id="ae95e-108">It explores how we can create a tactile sensation with visual, audio, and fully articulated hand-tracking.</span></span>

![Superfici](images/MRDL_Surfaces_1.jpg)

## <a name="demo-video"></a><span data-ttu-id="ae95e-110">Video demo</span><span class="sxs-lookup"><span data-stu-id="ae95e-110">Demo video</span></span> 

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4IhWQ]

<span data-ttu-id="ae95e-111">Registrato con HoloLens 2 usando Acquisizione realtà mista</span><span class="sxs-lookup"><span data-stu-id="ae95e-111">Recorded with HoloLens 2 using Mixed Reality Capture</span></span>

## <a name="about-the-app"></a><span data-ttu-id="ae95e-112">Informazioni sull'app</span><span class="sxs-lookup"><span data-stu-id="ae95e-112">About the app</span></span>

<span data-ttu-id="ae95e-113">Surfaces illustra come usare il sistema di input e i blocchi predefiniti di Mixed Reality Toolkit (MRTK) per creare un'esperienza di app per HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="ae95e-113">Surfaces demonstrates how to use Mixed Reality Toolkit(MRTK)'s input system and building blocks to create an app experience for HoloLens 2.</span></span> <span data-ttu-id="ae95e-114">In questo progetto sono disponibili gli esempi di:</span><span class="sxs-lookup"><span data-stu-id="ae95e-114">In this project, you can find the examples of:</span></span>

- <span data-ttu-id="ae95e-115">Usare il sistema di [input](/windows/mixed-reality/mrtk-unity/features/input/overview)MRTK, in particolare il rilevamento mano/giunzione.</span><span class="sxs-lookup"><span data-stu-id="ae95e-115">Use MRTK's [Input System](/windows/mixed-reality/mrtk-unity/features/input/overview), specifically hand / joint tracking.</span></span>
- <span data-ttu-id="ae95e-116">Usare lo shader [Standard](/windows/mixed-reality/mrtk-unity/features/rendering/mrtk-standard-shader) di MRTK per la grafica performante.</span><span class="sxs-lookup"><span data-stu-id="ae95e-116">Use MRTK's [Standard Shader](/windows/mixed-reality/mrtk-unity/features/rendering/mrtk-standard-shader) for performant graphics.</span></span>

<span data-ttu-id="ae95e-117">È possibile usare i componenti di questo progetto per creare esperienze di app di realtà mista personalizzate.</span><span class="sxs-lookup"><span data-stu-id="ae95e-117">You can use this project's components to create your own mixed reality app experiences.</span></span>

## <a name="mr-dev-days-2020---learnings-from-the-mr-surfaces-app"></a><span data-ttu-id="ae95e-118">MR Dev Days 2020 - App di Mr Surfaces</span><span class="sxs-lookup"><span data-stu-id="ae95e-118">MR Dev Days 2020 - Learnings from the MR Surfaces App</span></span>

[<span data-ttu-id="ae95e-119">Apprendimenti dall'app Mr Surfaces</span><span class="sxs-lookup"><span data-stu-id="ae95e-119">Learnings from the MR Surfaces App</span></span>](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Learnings-from-the-MR-Surfaces-App)

<span data-ttu-id="ae95e-120">Lars Simkins, senior designer dell'app MRDL Surfaces, illustra la storia della progettazione dell'app e i punti di riferimento tecnici dell'app.</span><span class="sxs-lookup"><span data-stu-id="ae95e-120">Lars Simkins, Senior designer behind the MRDL Surfaces app talks about the app's design story and technical highlights.</span></span>

## <a name="project-repository-on-github"></a><span data-ttu-id="ae95e-121">Repository di progetti in GitHub</span><span class="sxs-lookup"><span data-stu-id="ae95e-121">Project repository on GitHub</span></span>

[https://github.com/microsoft/MRDL_Unity_Surfaces](https://github.com/microsoft/MRDL_Unity_Surfaces)

## <a name="download-app-from-microsoft-store-in-hololens-2"></a><span data-ttu-id="ae95e-122">Scaricare l'app Microsoft Store in HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="ae95e-122">Download app from Microsoft Store in HoloLens 2</span></span>

https://www.microsoft.com/en-us/p/surfaces/9nvkpv3sk3x0#activetab=pivot:overviewtab

<span data-ttu-id="ae95e-123">L'app è disponibile solo in HoloLens 2)</span><span class="sxs-lookup"><span data-stu-id="ae95e-123">(The app is only available on HoloLens 2)</span></span>

## <a name="about-the-author"></a><span data-ttu-id="ae95e-124">Informazioni sull'autore</span><span class="sxs-lookup"><span data-stu-id="ae95e-124">About the author</span></span>

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><span data-ttu-id="ae95e-125"><b>Dong Yoon Park</b></span><span class="sxs-lookup"><span data-stu-id="ae95e-125"><b>Dong Yoon Park</b></span></span><br><span data-ttu-id="ae95e-126">Designer di esperienza utente @Microsoft</span><span class="sxs-lookup"><span data-stu-id="ae95e-126">UX Designer @Microsoft</span></span></td>
</tr>
</table>

## <a name="see-also"></a><span data-ttu-id="ae95e-127">Vedi anche</span><span class="sxs-lookup"><span data-stu-id="ae95e-127">See also</span></span>

* <span data-ttu-id="ae95e-128">[Hub di esempi MRTK](/windows/mixed-reality/mrtk-unity/features/example-scenes/example-hub) - [(eseguire il download da Microsoft Store in HoloLens 2)](https://www.microsoft.com/en-us/p/mrtk-examples-hub/9mv8c39l2sj4)</span><span class="sxs-lookup"><span data-stu-id="ae95e-128">[MRTK Examples Hub](/windows/mixed-reality/mrtk-unity/features/example-scenes/example-hub) - [(Download from Microsoft Store in HoloLens 2)](https://www.microsoft.com/en-us/p/mrtk-examples-hub/9mv8c39l2sj4)</span></span>
* <span data-ttu-id="ae95e-129">[Superfici](sampleapp-surfaces.md) - [(eseguire il download da Microsoft Store in HoloLens 2)](https://www.microsoft.com/en-us/p/surfaces/9nvkpv3sk3x0)</span><span class="sxs-lookup"><span data-stu-id="ae95e-129">[Surfaces](sampleapp-surfaces.md) - [(Download from Microsoft Store in HoloLens 2)](https://www.microsoft.com/en-us/p/surfaces/9nvkpv3sk3x0)</span></span>
* [<span data-ttu-id="ae95e-130">Tavola periodica degli elementi 2.0</span><span class="sxs-lookup"><span data-stu-id="ae95e-130">Periodic Table of the Elements 2.0</span></span>](https://medium.com/@dongyoonpark/bringing-the-periodic-table-of-the-elements-app-to-hololens-2-with-mrtk-v2-a6e3d8362158)
* [<span data-ttu-id="ae95e-131">Galaxy Explorer 2.0</span><span class="sxs-lookup"><span data-stu-id="ae95e-131">Galaxy Explorer 2.0</span></span>](galaxy-explorer-update.md)
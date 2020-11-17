---
title: Superfici
description: Surfaces è un'app di esempio Open Source di Microsoft Mixed Reality Design Labs. Esplora il modo in cui è possibile creare una sensazione tattile con la traccia a mano visiva, audio e completamente articolata.
author: cre8ivepark
ms.author: dongpark
ms.date: 06/18/2020
ms.topic: article
keywords: Realtà mista di Windows, progettazione, app di esempio, controlli, MRTK, Toolkit per realtà mista, Unity, app di esempio, app di esempio, open source, Microsoft Store, HoloLens, auricolare per realtà mista, auricolare di realtà mista di Windows, auricolare della realtà virtuale
ms.openlocfilehash: c20ea17b20c867d9bf1da0d5f6244e36f2abbf27
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2020
ms.locfileid: "94678520"
---
# <a name="surfaces"></a><span data-ttu-id="297c2-105">Superfici</span><span class="sxs-lookup"><span data-stu-id="297c2-105">Surfaces</span></span>

>[!NOTE]
><span data-ttu-id="297c2-106">Questo articolo illustra un esempio esplorativo creato nei [laboratori di progettazione della realtà mista](https://github.com/Microsoft/MRDesignLabs_Unity), un posto in cui si condividono le informazioni e suggerimenti per lo sviluppo di app di realtà miste.</span><span class="sxs-lookup"><span data-stu-id="297c2-106">This article discusses an exploratory sample we’ve created in the [Mixed Reality Design Labs](https://github.com/Microsoft/MRDesignLabs_Unity), a place where we share our learnings about and suggestions for mixed reality app development.</span></span> <span data-ttu-id="297c2-107">Gli articoli e il codice correlati alla progettazione si evolveranno Man mano che si effettuano nuove individuazioni.</span><span class="sxs-lookup"><span data-stu-id="297c2-107">Our design-related articles and code will evolve as we make new discoveries.</span></span>

<span data-ttu-id="297c2-108">[Surfaces](https://github.com/microsoft/MRDL_Unity_Surfaces)  è un'app di esempio Open Source di Microsoft Mixed Reality Design Labs.</span><span class="sxs-lookup"><span data-stu-id="297c2-108">[Surfaces](https://github.com/microsoft/MRDL_Unity_Surfaces)  is an open-source sample app from Microsoft's Mixed Reality Design Labs.</span></span> <span data-ttu-id="297c2-109">Esplora il modo in cui è possibile creare una sensazione tattile con la traccia a mano visiva, audio e completamente articolata.</span><span class="sxs-lookup"><span data-stu-id="297c2-109">It explores how we can create a tactile sensation with visual, audio, and fully articulated hand-tracking.</span></span>

![Superfici](images/MRDL_Surfaces_1.jpg)

## <a name="demo-video"></a><span data-ttu-id="297c2-111">Video dimostrativo</span><span class="sxs-lookup"><span data-stu-id="297c2-111">Demo video</span></span> 
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4IhWQ]

<span data-ttu-id="297c2-112">Registrato con HoloLens 2 con l'acquisizione di realtà mista</span><span class="sxs-lookup"><span data-stu-id="297c2-112">Recorded with HoloLens 2 using Mixed Reality Capture</span></span>

## <a name="about-the-app"></a><span data-ttu-id="297c2-113">Informazioni sull'app</span><span class="sxs-lookup"><span data-stu-id="297c2-113">About the app</span></span>
<span data-ttu-id="297c2-114">Surfaces illustra come usare il sistema di input MRTK (Mixed Reality Toolkit) e i blocchi predefiniti per creare un'esperienza di app per HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="297c2-114">Surfaces demonstrates how to use Mixed Reality Toolkit(MRTK)'s input system and building blocks to create an app experience for HoloLens 2.</span></span> <span data-ttu-id="297c2-115">In questo progetto, è possibile trovare gli esempi seguenti:</span><span class="sxs-lookup"><span data-stu-id="297c2-115">In this project, you can find the examples of:</span></span>
- <span data-ttu-id="297c2-116">Usare il [sistema di input](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html)di MRTK, in particolare il rilevamento a mano/insieme.</span><span class="sxs-lookup"><span data-stu-id="297c2-116">Use MRTK's [Input System](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html), specifically hand / joint tracking.</span></span>
- <span data-ttu-id="297c2-117">Usare lo [shader standard](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_MRTKStandardShader.html) di MRTK per la grafica ad alte prestazioni.</span><span class="sxs-lookup"><span data-stu-id="297c2-117">Use MRTK's [Standard Shader](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_MRTKStandardShader.html) for performant graphics.</span></span>

<span data-ttu-id="297c2-118">È possibile usare i componenti di questo progetto per creare esperienze di app per la realtà mista.</span><span class="sxs-lookup"><span data-stu-id="297c2-118">You can use this project's components to create your own mixed reality app experiences.</span></span>

## <a name="mr-dev-days-2020---learnings-from-the-mr-surfaces-app"></a><span data-ttu-id="297c2-119">MR dev Days 2020-apprendere dall'app MR Surfaces</span><span class="sxs-lookup"><span data-stu-id="297c2-119">MR Dev Days 2020 - Learnings from the MR Surfaces App</span></span>
[<span data-ttu-id="297c2-120">Informazioni sull'app Surfaces</span><span class="sxs-lookup"><span data-stu-id="297c2-120">Learnings from the MR Surfaces App</span></span>](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Learnings-from-the-MR-Surfaces-App)

<span data-ttu-id="297c2-121">Lars Simkins, Senior designer dietro l'app MRDL Surfaces, illustra la storia di progettazione dell'app e gli Highlight tecnici.</span><span class="sxs-lookup"><span data-stu-id="297c2-121">Lars Simkins, Senior designer behind the MRDL Surfaces app talks about the app's design story and technical highlights.</span></span>

## <a name="project-repository-on-github"></a><span data-ttu-id="297c2-122">Repository del progetto in GitHub</span><span class="sxs-lookup"><span data-stu-id="297c2-122">Project repository on GitHub</span></span>
[https://github.com/microsoft/MRDL_Unity_Surfaces](https://github.com/microsoft/MRDL_Unity_Surfaces)

## <a name="download-app-from-microsoft-store-in-hololens-2"></a><span data-ttu-id="297c2-123">Scaricare un'app da Microsoft Store in HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="297c2-123">Download app from Microsoft Store in HoloLens 2</span></span>
https://www.microsoft.com/en-us/p/surfaces/9nvkpv3sk3x0#activetab=pivot:overviewtab

<span data-ttu-id="297c2-124">(L'app è disponibile solo in HoloLens 2)</span><span class="sxs-lookup"><span data-stu-id="297c2-124">(The app is only available on HoloLens 2)</span></span>

## <a name="about-the-author"></a><span data-ttu-id="297c2-125">Informazioni sull'autore</span><span class="sxs-lookup"><span data-stu-id="297c2-125">About the author</span></span>

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><span data-ttu-id="297c2-126"><b>Dong Yoon Park</b></span><span class="sxs-lookup"><span data-stu-id="297c2-126"><b>Dong Yoon Park</b></span></span><br><span data-ttu-id="297c2-127">Designer di esperienza utente @Microsoft</span><span class="sxs-lookup"><span data-stu-id="297c2-127">UX Designer @Microsoft</span></span></td>
</tr>
</table>

## <a name="see-also"></a><span data-ttu-id="297c2-128">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="297c2-128">See also</span></span>

* <span data-ttu-id="297c2-129">[Hub di esempi MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ExampleHub.html) - [(eseguire il download da Microsoft Store in HoloLens 2)](https://www.microsoft.com/en-us/p/mrtk-examples-hub/9mv8c39l2sj4)</span><span class="sxs-lookup"><span data-stu-id="297c2-129">[MRTK Examples Hub](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ExampleHub.html) - [(Download from Microsoft Store in HoloLens 2)](https://www.microsoft.com/en-us/p/mrtk-examples-hub/9mv8c39l2sj4)</span></span>
* <span data-ttu-id="297c2-130">[Superfici](sampleapp-surfaces.md) - [(eseguire il download da Microsoft Store in HoloLens 2)](https://www.microsoft.com/en-us/p/surfaces/9nvkpv3sk3x0)</span><span class="sxs-lookup"><span data-stu-id="297c2-130">[Surfaces](sampleapp-surfaces.md) - [(Download from Microsoft Store in HoloLens 2)](https://www.microsoft.com/en-us/p/surfaces/9nvkpv3sk3x0)</span></span>
* [<span data-ttu-id="297c2-131">Tavola periodica degli elementi 2.0</span><span class="sxs-lookup"><span data-stu-id="297c2-131">Periodic Table of the Elements 2.0</span></span>](https://medium.com/@dongyoonpark/bringing-the-periodic-table-of-the-elements-app-to-hololens-2-with-mrtk-v2-a6e3d8362158)
* [<span data-ttu-id="297c2-132">Galaxy Explorer 2.0</span><span class="sxs-lookup"><span data-stu-id="297c2-132">Galaxy Explorer 2.0</span></span>](galaxy-explorer-update.md)

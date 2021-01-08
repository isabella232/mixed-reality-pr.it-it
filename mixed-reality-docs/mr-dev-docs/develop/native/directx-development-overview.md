---
title: Panoramica dello sviluppo nativo
description: Informazioni su come creare un motore di realtà mista basato su DirectX usando direttamente le API di realtà mista di Windows.
author: thetuvix
ms.author: alexturn
ms.date: 08/04/2020
ms.topic: article
keywords: DirectX, rendering olografico, nativo, app nativa, WinRT, app WinRT, API della piattaforma, motore personalizzato, middleware, auricolare realtà mista, cuffia di realtà mista di Windows, auricolare della realtà virtuale
ms.openlocfilehash: 764cbe0a37501cc176e9bb05a9a7771b03666f0c
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2021
ms.locfileid: "98006851"
---
# <a name="native-development-overview"></a><span data-ttu-id="89bf3-104">Panoramica dello sviluppo nativo</span><span class="sxs-lookup"><span data-stu-id="89bf3-104">Native development overview</span></span>

![Logo banner nativo](../images/native_logo_banner.png)

<span data-ttu-id="89bf3-106">i motori 3D come [Unity](../unity/unity-development-overview.md) o [Unreal](../unreal/unreal-development-overview.md) non sono gli unici percorsi di sviluppo di realtà mista aperti.</span><span class="sxs-lookup"><span data-stu-id="89bf3-106">3D engines like [Unity](../unity/unity-development-overview.md) or [Unreal](../unreal/unreal-development-overview.md) aren't the only Mixed Reality development paths open to you.</span></span> <span data-ttu-id="89bf3-107">È anche possibile creare app per realtà mista usando le API di realtà mista di Windows con DirectX 11 o DirectX 12.</span><span class="sxs-lookup"><span data-stu-id="89bf3-107">You can also create Mixed Reality apps using the Windows Mixed Reality APIs with DirectX 11 or DirectX 12.</span></span> <span data-ttu-id="89bf3-108">Passando all'origine della piattaforma, si crea essenzialmente un middleware o un Framework personalizzato.</span><span class="sxs-lookup"><span data-stu-id="89bf3-108">By going to the platform source, you're essentially building your own middleware or framework.</span></span> 

> [!IMPORTANT]
> <span data-ttu-id="89bf3-109">Se si vuole mantenere un progetto WinRT esistente, passare alla documentazione principale di [WinRT](creating-a-holographic-directx-project.md).</span><span class="sxs-lookup"><span data-stu-id="89bf3-109">If you have an existing WinRT project that you'd like to maintain, head over to our main [WinRT documentation](creating-a-holographic-directx-project.md).</span></span> 

## <a name="development-checkpoints"></a><span data-ttu-id="89bf3-110">Checkpoint di sviluppo</span><span class="sxs-lookup"><span data-stu-id="89bf3-110">Development checkpoints</span></span>

<span data-ttu-id="89bf3-111">Usare i checkpoint seguenti per trasferire i giochi e le applicazioni di Unity nel mondo della realtà mista.</span><span class="sxs-lookup"><span data-stu-id="89bf3-111">Use the following checkpoints to bring your Unity games and applications into the world of mixed reality.</span></span>

### <a name="1-getting-started"></a><span data-ttu-id="89bf3-112">1. Guida introduttiva</span><span class="sxs-lookup"><span data-stu-id="89bf3-112">1. Getting started</span></span>

<span data-ttu-id="89bf3-113">La realtà mista [di Windows supporta due tipi di app](../../design/app-views.md):</span><span class="sxs-lookup"><span data-stu-id="89bf3-113">Windows Mixed Reality supports [two kinds of apps](../../design/app-views.md):</span></span>
* <span data-ttu-id="89bf3-114">UWP o **applicazioni di realtà mista** Win32 che usano l'API [HOLOGRAPHICSPACE](getting-a-holographicspace.md) o l' [API OpenXR](openxr.md) per eseguire il rendering di una [visualizzazione immersiva](../../design/app-views.md) che riempie la visualizzazione dell'auricolare</span><span class="sxs-lookup"><span data-stu-id="89bf3-114">UWP or Win32 **Mixed Reality applications** that use the [HolographicSpace API](getting-a-holographicspace.md) or [OpenXR API](openxr.md) to render an [immersive view](../../design/app-views.md) that fills the headset display</span></span>
* <span data-ttu-id="89bf3-115">**app 2D** (UWP) che usano DirectX, XAML o un altro Framework per eseguire il rendering di [visualizzazioni 2D](../../design/app-views.md#2d-views) in slate nella Home realtà mista di Windows</span><span class="sxs-lookup"><span data-stu-id="89bf3-115">**2D apps** (UWP) that use DirectX, XAML, or another framework to render [2D views](../../design/app-views.md#2d-views) on slates in the Windows Mixed Reality home</span></span>

<span data-ttu-id="89bf3-116">Le differenze tra lo sviluppo di DirectX per le [visualizzazioni 2D e le visualizzazioni immersive](../../design/app-views.md) riguardano principalmente il rendering olografico e l'input spaziale.</span><span class="sxs-lookup"><span data-stu-id="89bf3-116">The differences between DirectX development for [2D views and immersive views](../../design/app-views.md) primarily concern holographic rendering and spatial input.</span></span> <span data-ttu-id="89bf3-117">Il [IFrameworkView](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.core.iframeworkview.aspx) dell'applicazione UWP o l'HWND dell'applicazione Win32 sono obbligatori e rimangono in gran parte uguali.</span><span class="sxs-lookup"><span data-stu-id="89bf3-117">Your UWP application's [IFrameworkView](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.core.iframeworkview.aspx) or your Win32 application's HWND are required and remain largely the same.</span></span> <span data-ttu-id="89bf3-118">Lo stesso vale per le API WinRT disponibili per l'app.</span><span class="sxs-lookup"><span data-stu-id="89bf3-118">The same is true for the WinRT APIs that are available to your app.</span></span> <span data-ttu-id="89bf3-119">È tuttavia necessario usare un subset diverso di queste API per sfruttare le funzionalità olografiche.</span><span class="sxs-lookup"><span data-stu-id="89bf3-119">But you must use a different subset of these APIs to take advantage of holographic features.</span></span> <span data-ttu-id="89bf3-120">Ad esempio, il sistema per le applicazioni olografiche gestisce presentazione catena e frame presenti per abilitare un ciclo di frame stimato per la posa.</span><span class="sxs-lookup"><span data-stu-id="89bf3-120">For example, the system for holographic applications manages the swapchain and frame present to enable a pose-predicted frame loop.</span></span>

[!INCLUDE[](../includes/native-getting-started.md)]

### <a name="2-core-building-blocks"></a><span data-ttu-id="89bf3-121">2. Componenti fondamentali</span><span class="sxs-lookup"><span data-stu-id="89bf3-121">2. Core building blocks</span></span>

<span data-ttu-id="89bf3-122">Le applicazioni di realtà mista di Windows usano le API seguenti per creare esperienze di [realtà mista](../../discover/mixed-reality.md) per HoloLens e altri auricolari immersivi:</span><span class="sxs-lookup"><span data-stu-id="89bf3-122">Windows Mixed Reality applications use the following APIs to build [mixed-reality](../../discover/mixed-reality.md) experiences for HoloLens and other immersive headsets:</span></span>

|  <span data-ttu-id="89bf3-123">Caratteristica</span><span class="sxs-lookup"><span data-stu-id="89bf3-123">Feature</span></span>  |  <span data-ttu-id="89bf3-124">Funzionalità</span><span class="sxs-lookup"><span data-stu-id="89bf3-124">Capability</span></span>  |
| --- | --- |
| [<span data-ttu-id="89bf3-125">Sguardo fisso</span><span class="sxs-lookup"><span data-stu-id="89bf3-125">Gaze</span></span>](../../design/gaze-and-commit.md) | <span data-ttu-id="89bf3-126">Consentire agli utenti di puntare agli ologrammi fissandoli con lo sguardo</span><span class="sxs-lookup"><span data-stu-id="89bf3-126">Let users target holograms with by looking at them</span></span> |
| [<span data-ttu-id="89bf3-127">Movimento</span><span class="sxs-lookup"><span data-stu-id="89bf3-127">Gesture</span></span>](../../design/gaze-and-commit.md#composite-gestures) | <span data-ttu-id="89bf3-128">Aggiungere azioni spaziali alle app</span><span class="sxs-lookup"><span data-stu-id="89bf3-128">Add spatial actions to your apps</span></span> |
| [<span data-ttu-id="89bf3-129">Rendering olografico</span><span class="sxs-lookup"><span data-stu-id="89bf3-129">Holographic rendering</span></span>](../platform-capabilities-and-apis/rendering.md) | <span data-ttu-id="89bf3-130">Creare un ologramma in una posizione precisa in tutto il mondo intorno agli utenti</span><span class="sxs-lookup"><span data-stu-id="89bf3-130">Draw a hologram at a precise location in the world around your users</span></span> |
| [<span data-ttu-id="89bf3-131">Controller di movimento</span><span class="sxs-lookup"><span data-stu-id="89bf3-131">Motion controller</span></span>](../../design/motion-controllers.md) | <span data-ttu-id="89bf3-132">Consentire agli utenti di intervenire sugli ambienti di realtà mista</span><span class="sxs-lookup"><span data-stu-id="89bf3-132">Let your users take action in your Mixed Reality environments</span></span> |
| [<span data-ttu-id="89bf3-133">Mapping spaziale</span><span class="sxs-lookup"><span data-stu-id="89bf3-133">Spatial mapping</span></span>](../../design/spatial-mapping.md) | <span data-ttu-id="89bf3-134">Mappare lo spazio fisico con una mesh virtuale sovrapposta per contrassegnare i limiti dell'ambiente</span><span class="sxs-lookup"><span data-stu-id="89bf3-134">Map your physical space with a virtual mesh overlay to mark the boundaries of your environment</span></span> |
| [<span data-ttu-id="89bf3-135">Chiamata vocale</span><span class="sxs-lookup"><span data-stu-id="89bf3-135">Voice</span></span>](../../design/voice-input.md) | <span data-ttu-id="89bf3-136">Acquisire parole chiave, frasi e dettature pronunciate degli utenti</span><span class="sxs-lookup"><span data-stu-id="89bf3-136">Capture spoken keywords, phrases, and dictation from your users</span></span> |
 
> [!NOTE]
> <span data-ttu-id="89bf3-137">È possibile trovare le funzionalità principali imminenti e in fase di sviluppo nella documentazione di [Roadmap](openxr.md#roadmap) per OpenXR.</span><span class="sxs-lookup"><span data-stu-id="89bf3-137">You can find upcoming and in-development core features in the OpenXR [roadmap](openxr.md#roadmap) documentation.</span></span>

### <a name="3-deploying-and-testing"></a><span data-ttu-id="89bf3-138">3. distribuzione e test</span><span class="sxs-lookup"><span data-stu-id="89bf3-138">3. Deploying and testing</span></span>

<span data-ttu-id="89bf3-139">È possibile sviluppare su un desktop usando OpenXR in un auricolare HoloLens 2 o Windows misto realtà mista.</span><span class="sxs-lookup"><span data-stu-id="89bf3-139">You can develop on a desktop using OpenXR on a HoloLens 2 or Windows Mixed Reality immersive headset.</span></span>  <span data-ttu-id="89bf3-140">Se non si ha accesso a una cuffia, è invece possibile usare l' [emulatore HoloLens 2](../platform-capabilities-and-apis/using-the-hololens-emulator.md) o il [simulatore di realtà mista di Windows](../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md) .</span><span class="sxs-lookup"><span data-stu-id="89bf3-140">If you don't have access to a headset, you can use the [HoloLens 2 Emulator](../platform-capabilities-and-apis/using-the-hololens-emulator.md) or the [Windows Mixed Reality Simulator](../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md) instead.</span></span>

## <a name="whats-next"></a><span data-ttu-id="89bf3-141">Passaggi successivi</span><span class="sxs-lookup"><span data-stu-id="89bf3-141">What's next?</span></span>

<span data-ttu-id="89bf3-142">Il lavoro di uno sviluppatore non finisce mai, soprattutto per quanto riguarda l'apprendimento di nuovi strumenti o SDK.</span><span class="sxs-lookup"><span data-stu-id="89bf3-142">A developer's job is never done, especially when learning a new tool or SDK.</span></span> <span data-ttu-id="89bf3-143">Le sezioni seguenti consentono di accedere alle aree oltre il materiale di livello principiante già completato.</span><span class="sxs-lookup"><span data-stu-id="89bf3-143">The following sections can take you into areas beyond the beginner level material you've already completed.</span></span> <span data-ttu-id="89bf3-144">Questi argomenti e risorse non sono in ordine sequenziale, quindi è possibile esplorare</span><span class="sxs-lookup"><span data-stu-id="89bf3-144">These topics and resources aren't in any sequential order, so feel free to jump around and explore!</span></span>

### <a name="additional-resources"></a><span data-ttu-id="89bf3-145">Risorse aggiuntive</span><span class="sxs-lookup"><span data-stu-id="89bf3-145">Additional resources</span></span>

<span data-ttu-id="89bf3-146">Se si sta cercando di livellare il gioco OpenXR, vedere i collegamenti seguenti:</span><span class="sxs-lookup"><span data-stu-id="89bf3-146">If you're looking to level up your OpenXR game, check out the links below:</span></span>

* [<span data-ttu-id="89bf3-147">Procedure consigliate per OpenXR</span><span class="sxs-lookup"><span data-stu-id="89bf3-147">OpenXR best practices</span></span>](openxr-best-practices.md)
* [<span data-ttu-id="89bf3-148">Prestazioni di OpenXR</span><span class="sxs-lookup"><span data-stu-id="89bf3-148">OpenXR performance</span></span>](openxr-performance.md)
* [<span data-ttu-id="89bf3-149">Risoluzione dei problemi di OpenXR</span><span class="sxs-lookup"><span data-stu-id="89bf3-149">OpenXR troubleshooting</span></span>](openxr-troubleshooting.md)

## <a name="see-also"></a><span data-ttu-id="89bf3-150">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="89bf3-150">See also</span></span>
* [<span data-ttu-id="89bf3-151">Modello di app</span><span class="sxs-lookup"><span data-stu-id="89bf3-151">App model</span></span>](../../design/app-model.md)
* [<span data-ttu-id="89bf3-152">Visualizzazioni delle app</span><span class="sxs-lookup"><span data-stu-id="89bf3-152">App views</span></span>](../../design/app-views.md)

---
title: Uso di WebXR con la realtà mista di Windows
description: Scopri le nozioni di base sull'uso e lo sviluppo di applicazioni WebXR in esecuzione su cuffie immersive a realtà mista di Windows.
author: yonet
ms.author: ayyonet
ms.date: 04/10/2020
ms.topic: article
keywords: WebXR, WinMR, WebAR, WebVR, WindowsMixedReality, HoloLens, realtà mista di Windows, Web VR, Web XR, Web Mr, Web AR, 360, 360 video, 360 video, 360 foto, 360 foto, 360 contenuto, immersive Web, immersiveweb, IW
ms.openlocfilehash: e49f5f2422c9802f94b63943f8a38949a2969f83
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2021
ms.locfileid: "98006941"
---
# <a name="webxr-overview"></a><span data-ttu-id="1137a-104">Panoramica di WebXR</span><span class="sxs-lookup"><span data-stu-id="1137a-104">WebXR Overview</span></span>

## <a name="what-is-webxr"></a><span data-ttu-id="1137a-105">Informazioni su WebXR</span><span class="sxs-lookup"><span data-stu-id="1137a-105">What is WebXR</span></span>

<span data-ttu-id="1137a-106">L' **API del dispositivo WebXR** consente di accedere ai dispositivi di **realtà virtuale (VR)** e **realtà aumentata (AR)** , inclusi i **sensori** e le **visualizzazioni montate** sul **Web**.</span><span class="sxs-lookup"><span data-stu-id="1137a-106">The **WebXR device API** is for accessing **virtual reality (VR)** and **augmented reality (AR)** devices, including **sensors** and **head-mounted displays** on the **Web**.</span></span> <span data-ttu-id="1137a-107">L'API del dispositivo WebXR è attualmente disponibile in Microsoft Edge e Chrome versione 79 e versioni successive supporta WebXR come valore predefinito.</span><span class="sxs-lookup"><span data-stu-id="1137a-107">WebXR device API is currently available on Microsoft Edge and Chrome version 79 and later versions supports WebXR as a default.</span></span> <span data-ttu-id="1137a-108">È possibile controllare lo stato del supporto del browser più recente per WebXR in [caniuse.com](https://caniuse.com/#search=webxr).</span><span class="sxs-lookup"><span data-stu-id="1137a-108">You can check the latest browser support status for WebXR at [caniuse.com](https://caniuse.com/#search=webxr).</span></span>

<span data-ttu-id="1137a-109">Scopri di più sulla [realtà mista di Windows e sul nuovo Microsoft Edge](https://docs.microsoft.com/windows/mixed-reality/new-microsoft-edge#introducing-the-new-microsoft-edge) [nella sezione novità.](https://docs.microsoft.com/windows/mixed-reality/mrtk-porting-guide)</span><span class="sxs-lookup"><span data-stu-id="1137a-109">Learn more about the [Windows Mixed Reality and the new Microsoft Edge](https://docs.microsoft.com/windows/mixed-reality/new-microsoft-edge#introducing-the-new-microsoft-edge)in [What's new](https://docs.microsoft.com/windows/mixed-reality/mrtk-porting-guide) section.</span></span>

## <a name="viewing-webxr"></a><span data-ttu-id="1137a-110">Visualizzazione di WebXR</span><span class="sxs-lookup"><span data-stu-id="1137a-110">Viewing WebXR</span></span>

> [!IMPORTANT]
> <span data-ttu-id="1137a-111">Microsoft Edge (legacy) supporta solo WebVR, un'API deprecata che non è disponibile nei browser correnti.</span><span class="sxs-lookup"><span data-stu-id="1137a-111">Microsoft Edge (Legacy) only supports WebVR, a deprecated API that is not available in current browsers.</span></span> <span data-ttu-id="1137a-112">Tuttavia, il nuovo **[browser Edge basato su cromo](../../whats-new/new-microsoft-edge.md)** supporta WebXR ed è disponibile per la creazione di prototipi VR in realtà mista di Windows.</span><span class="sxs-lookup"><span data-stu-id="1137a-112">However, the new **[Chromium-based Edge browser](../../whats-new/new-microsoft-edge.md)** supports WebXR and is available for VR prototyping in Windows Mixed Reality.</span></span> <span data-ttu-id="1137a-113">WebVR non sarà disponibile nel nuovo browser Edge basato su cromo.</span><span class="sxs-lookup"><span data-stu-id="1137a-113">WebVR will not be available in the new Chromium-based Edge browser.</span></span>
> 
> <span data-ttu-id="1137a-114">Se si sta cercando un modo per eseguire il prototipo di WebXR in HoloLens 2 oggi, vedere la [realtà di Firefox](https://mixedreality.mozilla.org/firefox-reality/).</span><span class="sxs-lookup"><span data-stu-id="1137a-114">If you're looking for a way to prototype WebXR on HoloLens 2 today, check out [Firefox Reality](https://mixedreality.mozilla.org/firefox-reality/).</span></span>

<span data-ttu-id="1137a-115">Per verificare se il browser supporta WebXR, è possibile passare agli [esempi di WebXR](https://immersive-web.github.io/webxr-samples/) nel browser.</span><span class="sxs-lookup"><span data-stu-id="1137a-115">To test if your browser supports WebXR, you can navigate to [WebXR Samples](https://immersive-web.github.io/webxr-samples/) in your browser.</span></span>

## <a name="see-also"></a><span data-ttu-id="1137a-116">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="1137a-116">See Also</span></span>

* [<span data-ttu-id="1137a-117">Specifica API del dispositivo WebXR</span><span class="sxs-lookup"><span data-stu-id="1137a-117">WebXR Device API specification</span></span>](https://immersive-web.github.io/webxr/)
* [<span data-ttu-id="1137a-118">Documentazione dell'API del dispositivo WebXR</span><span class="sxs-lookup"><span data-stu-id="1137a-118">WebXR Device API documentation</span></span>](https://developer.mozilla.org/en-US/docs/Web/API/WebXR_Device_API)
* [<span data-ttu-id="1137a-119">Immersiveweb. dev</span><span class="sxs-lookup"><span data-stu-id="1137a-119">Immersiveweb.dev</span></span>](https://immersiveweb.dev/)
* [<span data-ttu-id="1137a-120">Esempi di WebXR</span><span class="sxs-lookup"><span data-stu-id="1137a-120">WebXR Samples</span></span>](https://immersive-web.github.io/webxr-samples/)
* [<span data-ttu-id="1137a-121">Realtà mista di Windows e la nuova Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="1137a-121">Windows Mixed Reality and the new Microsoft Edge</span></span>](https://docs.microsoft.com/windows/mixed-reality/new-microsoft-edge#introducing-the-new-microsoft-edge)
* [<span data-ttu-id="1137a-122">GitHub sul Web W3C immersivo</span><span class="sxs-lookup"><span data-stu-id="1137a-122">Immersive Web W3C Github</span></span>](https://github.com/immersive-web)
* <span data-ttu-id="1137a-123">[API WebGL](https://msdn.microsoft.com/library/bg182648(v=vs.85).aspx)</span><span class="sxs-lookup"><span data-stu-id="1137a-123">[WebGL API](https://msdn.microsoft.com/library/bg182648(v=vs.85).aspx)</span></span>
* <span data-ttu-id="1137a-124">Estensioni dell' [API gamepad](https://msdn.microsoft.com/library/dn743630(v=vs.85).aspx) e del [Gamepad](https://w3c.github.io/gamepad/extensions.html)</span><span class="sxs-lookup"><span data-stu-id="1137a-124">[Gamepad API](https://msdn.microsoft.com/library/dn743630(v=vs.85).aspx) and [Gamepad Extensions](https://w3c.github.io/gamepad/extensions.html)</span></span>
* [<span data-ttu-id="1137a-125">Gestione del contesto perduto in WebGL</span><span class="sxs-lookup"><span data-stu-id="1137a-125">Handling Lost Context in WebGL</span></span>](https://www.khronos.org/webgl/wiki/HandlingContextLost)
* [<span data-ttu-id="1137a-126">Pointerlock</span><span class="sxs-lookup"><span data-stu-id="1137a-126">Pointerlock</span></span>](https://www.w3.org/TR/pointerlock/)
* [<span data-ttu-id="1137a-127">glTF</span><span class="sxs-lookup"><span data-stu-id="1137a-127">glTF</span></span>](https://www.khronos.org/gltf)
* [<span data-ttu-id="1137a-128">Uso di Babylon.js per creare esperienze WebXR</span><span class="sxs-lookup"><span data-stu-id="1137a-128">Using Babylon.js to create WebXR experiences</span></span>](https://doc.babylonjs.com/how_to/introduction_to_webxr)
* [<span data-ttu-id="1137a-129">Gruppo di community Web Immersive</span><span class="sxs-lookup"><span data-stu-id="1137a-129">Immersive web community group</span></span>](https://www.w3.org/community/immersive-web/)

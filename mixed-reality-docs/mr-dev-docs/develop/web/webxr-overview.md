---
title: Uso di WebXR con la realtà mista di Windows
description: Scopri le nozioni di base sull'uso e lo sviluppo di applicazioni WebXR in esecuzione su cuffie immersive a realtà mista di Windows.
author: yonet
ms.author: ayyonet
ms.date: 04/10/2020
ms.topic: article
keywords: WebXR, WinMR, WebAR, WebVR, WindowsMixedReality, HoloLens, realtà mista di Windows, Web VR, Web XR, Web Mr, Web AR, 360, 360 video, 360 video, 360 foto, 360 foto, 360 contenuto, immersive Web, immersiveweb, IW
ms.openlocfilehash: 99cf5cf151c41252e43c6051c0d6281d33fe695a
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/20/2021
ms.locfileid: "98582908"
---
# <a name="webxr-overview"></a><span data-ttu-id="31883-104">Panoramica di WebXR</span><span class="sxs-lookup"><span data-stu-id="31883-104">WebXR Overview</span></span>

## <a name="what-is-webxr"></a><span data-ttu-id="31883-105">Informazioni su WebXR</span><span class="sxs-lookup"><span data-stu-id="31883-105">What is WebXR</span></span>

<span data-ttu-id="31883-106">L' **API del dispositivo WebXR** consente di accedere ai dispositivi di **realtà virtuale (VR)** e **realtà aumentata (AR)** , inclusi i **sensori** e le **visualizzazioni montate** sul **Web**.</span><span class="sxs-lookup"><span data-stu-id="31883-106">The **WebXR device API** is for accessing **virtual reality (VR)** and **augmented reality (AR)** devices, including **sensors** and **head-mounted displays** on the **Web**.</span></span> <span data-ttu-id="31883-107">L'API del dispositivo WebXR è attualmente disponibile in Microsoft Edge e Chrome versione 79 e versioni successive supporta WebXR come valore predefinito.</span><span class="sxs-lookup"><span data-stu-id="31883-107">WebXR device API is currently available on Microsoft Edge and Chrome version 79 and later versions supports WebXR as a default.</span></span> <span data-ttu-id="31883-108">È possibile controllare lo stato del supporto del browser più recente per WebXR in [caniuse.com](https://caniuse.com/#search=webxr).</span><span class="sxs-lookup"><span data-stu-id="31883-108">You can check the latest browser support status for WebXR at [caniuse.com](https://caniuse.com/#search=webxr).</span></span>

<span data-ttu-id="31883-109">Scopri di più sulla [realtà mista di Windows e sul nuovo Microsoft Edge](/windows/mixed-reality/new-microsoft-edge#introducing-the-new-microsoft-edge) [nella sezione novità.](/windows/mixed-reality/mrtk-porting-guide)</span><span class="sxs-lookup"><span data-stu-id="31883-109">Learn more about the [Windows Mixed Reality and the new Microsoft Edge](/windows/mixed-reality/new-microsoft-edge#introducing-the-new-microsoft-edge)in [What's new](/windows/mixed-reality/mrtk-porting-guide) section.</span></span>

## <a name="viewing-webxr"></a><span data-ttu-id="31883-110">Visualizzazione di WebXR</span><span class="sxs-lookup"><span data-stu-id="31883-110">Viewing WebXR</span></span>

> [!IMPORTANT]
> <span data-ttu-id="31883-111">Microsoft Edge (legacy) supporta solo WebVR, un'API deprecata che non è disponibile nei browser correnti.</span><span class="sxs-lookup"><span data-stu-id="31883-111">Microsoft Edge (Legacy) only supports WebVR, a deprecated API that is not available in current browsers.</span></span> <span data-ttu-id="31883-112">Tuttavia, il nuovo **[browser Edge basato su cromo](../../whats-new/new-microsoft-edge.md)** supporta WebXR ed è disponibile per la creazione di prototipi VR in realtà mista di Windows.</span><span class="sxs-lookup"><span data-stu-id="31883-112">However, the new **[Chromium-based Edge browser](../../whats-new/new-microsoft-edge.md)** supports WebXR and is available for VR prototyping in Windows Mixed Reality.</span></span> <span data-ttu-id="31883-113">WebVR non sarà disponibile nel nuovo browser Edge basato su cromo.</span><span class="sxs-lookup"><span data-stu-id="31883-113">WebVR will not be available in the new Chromium-based Edge browser.</span></span>
> 
> <span data-ttu-id="31883-114">Se si sta cercando un modo per eseguire il prototipo di WebXR in HoloLens 2 oggi, vedere la [realtà di Firefox](https://mixedreality.mozilla.org/firefox-reality/).</span><span class="sxs-lookup"><span data-stu-id="31883-114">If you're looking for a way to prototype WebXR on HoloLens 2 today, check out [Firefox Reality](https://mixedreality.mozilla.org/firefox-reality/).</span></span>

<span data-ttu-id="31883-115">Per verificare se il browser supporta WebXR, è possibile passare agli [esempi di WebXR](https://immersive-web.github.io/webxr-samples/) nel browser.</span><span class="sxs-lookup"><span data-stu-id="31883-115">To test if your browser supports WebXR, you can navigate to [WebXR Samples](https://immersive-web.github.io/webxr-samples/) in your browser.</span></span>

## <a name="see-also"></a><span data-ttu-id="31883-116">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="31883-116">See Also</span></span>

* [<span data-ttu-id="31883-117">Specifica API del dispositivo WebXR</span><span class="sxs-lookup"><span data-stu-id="31883-117">WebXR Device API specification</span></span>](https://immersive-web.github.io/webxr/)
* [<span data-ttu-id="31883-118">Documentazione dell'API del dispositivo WebXR</span><span class="sxs-lookup"><span data-stu-id="31883-118">WebXR Device API documentation</span></span>](https://developer.mozilla.org/en-US/docs/Web/API/WebXR_Device_API)
* [<span data-ttu-id="31883-119">Immersiveweb. dev</span><span class="sxs-lookup"><span data-stu-id="31883-119">Immersiveweb.dev</span></span>](https://immersiveweb.dev/)
* [<span data-ttu-id="31883-120">Esempi di WebXR</span><span class="sxs-lookup"><span data-stu-id="31883-120">WebXR Samples</span></span>](https://immersive-web.github.io/webxr-samples/)
* [<span data-ttu-id="31883-121">Realtà mista di Windows e la nuova Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="31883-121">Windows Mixed Reality and the new Microsoft Edge</span></span>](/windows/mixed-reality/new-microsoft-edge#introducing-the-new-microsoft-edge)
* [<span data-ttu-id="31883-122">GitHub sul Web W3C immersivo</span><span class="sxs-lookup"><span data-stu-id="31883-122">Immersive Web W3C Github</span></span>](https://github.com/immersive-web)
* <span data-ttu-id="31883-123">[API WebGL](/previous-versions/windows/internet-explorer/ie-developer/dev-guides/bg182648(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="31883-123">[WebGL API](/previous-versions/windows/internet-explorer/ie-developer/dev-guides/bg182648(v=vs.85))</span></span>
* <span data-ttu-id="31883-124">Estensioni dell' [API gamepad](https://msdn.microsoft.com/library/dn743630(v=vs.85).aspx) e del [Gamepad](https://w3c.github.io/gamepad/extensions.html)</span><span class="sxs-lookup"><span data-stu-id="31883-124">[Gamepad API](https://msdn.microsoft.com/library/dn743630(v=vs.85).aspx) and [Gamepad Extensions](https://w3c.github.io/gamepad/extensions.html)</span></span>
* [<span data-ttu-id="31883-125">Gestione del contesto perduto in WebGL</span><span class="sxs-lookup"><span data-stu-id="31883-125">Handling Lost Context in WebGL</span></span>](https://www.khronos.org/webgl/wiki/HandlingContextLost)
* [<span data-ttu-id="31883-126">Pointerlock</span><span class="sxs-lookup"><span data-stu-id="31883-126">Pointerlock</span></span>](https://www.w3.org/TR/pointerlock/)
* [<span data-ttu-id="31883-127">glTF</span><span class="sxs-lookup"><span data-stu-id="31883-127">glTF</span></span>](https://www.khronos.org/gltf)
* [<span data-ttu-id="31883-128">Uso di Babylon.js per creare esperienze WebXR</span><span class="sxs-lookup"><span data-stu-id="31883-128">Using Babylon.js to create WebXR experiences</span></span>](https://doc.babylonjs.com/how_to/introduction_to_webxr)
* [<span data-ttu-id="31883-129">Gruppo di community Web Immersive</span><span class="sxs-lookup"><span data-stu-id="31883-129">Immersive web community group</span></span>](https://www.w3.org/community/immersive-web/)
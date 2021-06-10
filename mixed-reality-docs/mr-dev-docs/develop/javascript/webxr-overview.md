---
title: Uso di WebXR con Windows Mixed Reality
description: Informazioni di base sull'uso e lo sviluppo per applicazioni WebXR in esecuzione Windows Mixed Reality visori immersivi.
author: yonet
ms.author: ayyonet
ms.date: 04/10/2020
ms.topic: article
keywords: WebXR, WinMR, WebAR, WebVR, WindowsMixedReality, HoloLens, windows mixed reality, web vr, web xr, web mr, web ar, 360, 360 video, 360 video, 360 foto, 360 foto, 360 foto, 360 contenuti, web immersivo, immersiveweb, IW
ms.openlocfilehash: fa4d11fac59e25f43d9d55de16d3b0c35e8166b7
ms.sourcegitcommit: 9ae76b339968f035c703d9c1fe57ddecb33198e3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/27/2021
ms.locfileid: "110600110"
---
# <a name="webxr-overview"></a><span data-ttu-id="d7051-104">Panoramica di WebXR</span><span class="sxs-lookup"><span data-stu-id="d7051-104">WebXR Overview</span></span>

## <a name="what-is-webxr"></a><span data-ttu-id="d7051-105">Che cos'è WebXR</span><span class="sxs-lookup"><span data-stu-id="d7051-105">What is WebXR</span></span>

<span data-ttu-id="d7051-106">L'API del dispositivo  [**WebXR**](https://www.w3.org/TR/webxr/) è per l'accesso ai dispositivi di  realtà virtuale **(VR)** e realtà aumentata **(AR),** inclusi sensori e schermi montati sulla testa **sul Web.**</span><span class="sxs-lookup"><span data-stu-id="d7051-106">The [**WebXR Device API**](https://www.w3.org/TR/webxr/) is for accessing **virtual reality (VR)** and **augmented reality (AR)** devices, including **sensors** and **head-mounted displays** on the **Web**.</span></span> <span data-ttu-id="d7051-107">L'API del dispositivo WebXR è attualmente disponibile Microsoft Edge e Chrome versione 79 e successive supporta WebXR come impostazione predefinita.</span><span class="sxs-lookup"><span data-stu-id="d7051-107">WebXR device API is currently available on Microsoft Edge and Chrome version 79 and later versions supports WebXR as a default.</span></span> <span data-ttu-id="d7051-108">È possibile controllare lo stato di supporto del browser più recente per WebXR [all'caniuse.com](https://caniuse.com/#search=webxr).</span><span class="sxs-lookup"><span data-stu-id="d7051-108">You can check the latest browser support status for WebXR at [caniuse.com](https://caniuse.com/#search=webxr).</span></span>

## <a name="viewing-webxr"></a><span data-ttu-id="d7051-109">Visualizzazione di WebXR</span><span class="sxs-lookup"><span data-stu-id="d7051-109">Viewing WebXR</span></span>

<span data-ttu-id="d7051-110">È possibile visualizzare gli espositivi WebXR Windows Mixed Reality e il [nuovo](../../whats-new/new-microsoft-edge.md) Microsoft Edge [e Firefox Reality.](https://mixedreality.mozilla.org/firefox-reality/)</span><span class="sxs-lookup"><span data-stu-id="d7051-110">You can view WebXR experinces on [Windows Mixed Reality and the new Microsoft Edge](../../whats-new/new-microsoft-edge.md) and [Firefox Reality](https://mixedreality.mozilla.org/firefox-reality/).</span></span>
<span data-ttu-id="d7051-111">Per verificare se il browser supporta WebXR, è possibile passare a [Esempi WebXR](https://immersive-web.github.io/webxr-samples/) nel browser.</span><span class="sxs-lookup"><span data-stu-id="d7051-111">To test if your browser supports WebXR, you can navigate to [WebXR Samples](https://immersive-web.github.io/webxr-samples/) in your browser.</span></span>

## <a name="see-also"></a><span data-ttu-id="d7051-112">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="d7051-112">See Also</span></span>

* [<span data-ttu-id="d7051-113">Uso Babylon.js per creare esperienze WebXR</span><span class="sxs-lookup"><span data-stu-id="d7051-113">Using Babylon.js to create WebXR experiences</span></span>](./tutorials/babylonjs-webxr-helloworld/introduction-01.md)
* [<span data-ttu-id="d7051-114">Specifica dell'API del dispositivo WebXR</span><span class="sxs-lookup"><span data-stu-id="d7051-114">WebXR Device API specification</span></span>](https://immersive-web.github.io/webxr/)
* [<span data-ttu-id="d7051-115">Documentazione dell'API del dispositivo WebXR</span><span class="sxs-lookup"><span data-stu-id="d7051-115">WebXR Device API documentation</span></span>](https://developer.mozilla.org/en-US/docs/Web/API/WebXR_Device_API)
* [<span data-ttu-id="d7051-116">Immersiveweb.dev</span><span class="sxs-lookup"><span data-stu-id="d7051-116">Immersiveweb.dev</span></span>](https://immersiveweb.dev/)
* [<span data-ttu-id="d7051-117">Esempi di WebXR</span><span class="sxs-lookup"><span data-stu-id="d7051-117">WebXR Samples</span></span>](https://immersive-web.github.io/webxr-samples/)
* [<span data-ttu-id="d7051-118">Windows Mixed Reality e il nuovo Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="d7051-118">Windows Mixed Reality and the new Microsoft Edge</span></span>](../../whats-new/new-microsoft-edge.md)
* [<span data-ttu-id="d7051-119">Github Web immersivo W3C</span><span class="sxs-lookup"><span data-stu-id="d7051-119">Immersive Web W3C Github</span></span>](https://github.com/immersive-web)
* <span data-ttu-id="d7051-120">[WebGL API](/previous-versions/windows/internet-explorer/ie-developer/dev-guides/bg182648(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="d7051-120">[WebGL API](/previous-versions/windows/internet-explorer/ie-developer/dev-guides/bg182648(v=vs.85))</span></span>
* <span data-ttu-id="d7051-121">[API Gamepad](https://msdn.microsoft.com/library/dn743630(v=vs.85).aspx) ed [estensioni gamepad](https://w3c.github.io/gamepad/extensions.html)</span><span class="sxs-lookup"><span data-stu-id="d7051-121">[Gamepad API](https://msdn.microsoft.com/library/dn743630(v=vs.85).aspx) and [Gamepad Extensions](https://w3c.github.io/gamepad/extensions.html)</span></span>
* [<span data-ttu-id="d7051-122">Gestione del contesto perso in WebGL</span><span class="sxs-lookup"><span data-stu-id="d7051-122">Handling Lost Context in WebGL</span></span>](https://www.khronos.org/webgl/wiki/HandlingContextLost)
* [<span data-ttu-id="d7051-123">Pointerlock</span><span class="sxs-lookup"><span data-stu-id="d7051-123">Pointerlock</span></span>](https://www.w3.org/TR/pointerlock/)
* [<span data-ttu-id="d7051-124">glTF</span><span class="sxs-lookup"><span data-stu-id="d7051-124">glTF</span></span>](https://www.khronos.org/gltf)
* [<span data-ttu-id="d7051-125">Gruppo community Web immersiva</span><span class="sxs-lookup"><span data-stu-id="d7051-125">Immersive web community group</span></span>](https://www.w3.org/community/immersive-web/)
---
title: Esempi e app di funzionalità
description: Aggiornamenti costanti su tutti gli esempi Microsoft disponibili e le app di funzionalità di realtà mista per HoloLens.
author: hferrone
ms.author: jemccull
ms.date: 12/3/2020
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens, learn, esempi, MRTK, research mode, HoloLens 2, codici a matrice, WebRTC, acquisizione realtà mista, holographic remoting, UX Tools
ms.localizationpriority: high
ms.openlocfilehash: 78cfc726bdffdb461a83bd1e9805d8f0e64b0f01
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/20/2021
ms.locfileid: "98583189"
---
# <a name="samples-and-feature-apps"></a><span data-ttu-id="1ee55-104">Esempi e app di funzionalità</span><span class="sxs-lookup"><span data-stu-id="1ee55-104">Samples and feature apps</span></span>

![Immagine di un utente che indossa un dispositivo HoloLens e manipola un ologramma con il movimento delle mani](unreal/images/unreal-developer.jpg)

<span data-ttu-id="1ee55-106">Ogni percorso di sviluppo ha inizio con un'indagine retrospettiva su ciò che è già stato realizzato da altri sviluppatori. Questo è vero anche per la realtà mista.</span><span class="sxs-lookup"><span data-stu-id="1ee55-106">Every development journey starts with a look back at what other developers have successfully built - mixed reality is no different.</span></span> <span data-ttu-id="1ee55-107">Attualmente, tutte le esercitazioni e le app di esempio vengono create in Unity o Unreal.</span><span class="sxs-lookup"><span data-stu-id="1ee55-107">Currently, all of our tutorials and sample apps are built in Unity or Unreal.</span></span> <span data-ttu-id="1ee55-108">Il contenuto che viene sviluppato per altri motori e piattaforme sarà disponibile sotto l'intestazione pertinente nel Sommario.</span><span class="sxs-lookup"><span data-stu-id="1ee55-108">As we develop content for other engines and platforms, you'll find them under the relevant heading in the Table of Contents.</span></span>

## <a name="sample-apps"></a><span data-ttu-id="1ee55-109">App di esempio</span><span class="sxs-lookup"><span data-stu-id="1ee55-109">Sample apps</span></span>

[!INCLUDE[](includes/tabs-samples.md)]

## <a name="feature-samples"></a><span data-ttu-id="1ee55-110">Esempi di funzionalità</span><span class="sxs-lookup"><span data-stu-id="1ee55-110">Feature samples</span></span>

<span data-ttu-id="1ee55-111">Gli esempi di funzionalità elencati di seguito corrispondono a implementazioni specifiche illustrate nella documentazione Microsoft e riguardano una vasta gamma di piattaforme di sviluppo e dispositivi hardware.</span><span class="sxs-lookup"><span data-stu-id="1ee55-111">The feature samples listed below correspond to specific implementations that are covered in our documentation and covers a range of development platforms and hardware devices.</span></span>

### <a name="research-mode"></a><span data-ttu-id="1ee55-112">Research Mode</span><span class="sxs-lookup"><span data-stu-id="1ee55-112">Research Mode</span></span>

<span data-ttu-id="1ee55-113">La funzionalità Research Mode è stata introdotta nel dispositivo HoloLens di prima generazione per consentire l'accesso ai sensori chiave sul dispositivo, in particolare per le applicazioni di ricerca che non sono destinate alla distribuzione.</span><span class="sxs-lookup"><span data-stu-id="1ee55-113">Research Mode was introduced in the 1st Generation HoloLens to give access to key sensors on the device, specifically for research applications that are not intended for deployment.</span></span> <span data-ttu-id="1ee55-114">Le applicazioni seguenti sono esempi relativi all'accesso e alla registrazione dei flussi di Search Mode e all'uso di funzioni [intrinseche ed estrinseche](/windows/mixed-reality/locatable-camera#locating-the-device-camera-in-the-world).</span><span class="sxs-lookup"><span data-stu-id="1ee55-114">The sample applications below are examples for accessing and recording Research Mode streams and using the [intrinsics and extrinsics](/windows/mixed-reality/locatable-camera#locating-the-device-camera-in-the-world).</span></span>

<br>

| <span data-ttu-id="1ee55-115">Articolo di riferimento</span><span class="sxs-lookup"><span data-stu-id="1ee55-115">Reference article</span></span> | <span data-ttu-id="1ee55-116">Applicazione di esempio</span><span class="sxs-lookup"><span data-stu-id="1ee55-116">Sample application</span></span> |
| --- | --- |
| [<span data-ttu-id="1ee55-117">Research Mode</span><span class="sxs-lookup"><span data-stu-id="1ee55-117">Research Mode</span></span>](platform-capabilities-and-apis/research-mode.md) | [<span data-ttu-id="1ee55-118">HoloLens (prima generazione)</span><span class="sxs-lookup"><span data-stu-id="1ee55-118">HoloLens (1st gen)</span></span>](https://github.com/microsoft/HoloLensForCV/tree/master/Samples) |
| [<span data-ttu-id="1ee55-119">Research Mode</span><span class="sxs-lookup"><span data-stu-id="1ee55-119">Research Mode</span></span>](platform-capabilities-and-apis/research-mode.md) | [<span data-ttu-id="1ee55-120">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="1ee55-120">HoloLens 2</span></span>](https://github.com/microsoft/HoloLens2ForCV/tree/main/Samples) |

### <a name="qr-codes"></a><span data-ttu-id="1ee55-121">Codici QR</span><span class="sxs-lookup"><span data-stu-id="1ee55-121">QR codes</span></span>

<span data-ttu-id="1ee55-122">HoloLens 2 è in grado di rilevare i codici a matrice nell'ambiente attorno al visore VR, stabilendo un sistema di coordinate nella posizione reale di ciascun codice.</span><span class="sxs-lookup"><span data-stu-id="1ee55-122">HoloLens 2 can detect QR codes in the environment around the headset, establishing a coordinate system at each code's real-world location.</span></span>

<br>

| <span data-ttu-id="1ee55-123">Articolo di riferimento</span><span class="sxs-lookup"><span data-stu-id="1ee55-123">Reference article</span></span> | <span data-ttu-id="1ee55-124">Esempio</span><span class="sxs-lookup"><span data-stu-id="1ee55-124">Sample</span></span> |
| --- | --- |
| [<span data-ttu-id="1ee55-125">Codici QR</span><span class="sxs-lookup"><span data-stu-id="1ee55-125">QR codes</span></span>](platform-capabilities-and-apis/qr-code-tracking.md) | [<span data-ttu-id="1ee55-126">Rilevamento di codici a matrice in Unity</span><span class="sxs-lookup"><span data-stu-id="1ee55-126">QR code tracking in Unity</span></span>](https://github.com/chgatla-microsoft/QRTracking/tree/master/SampleQRCodes) |

### <a name="webrtc"></a><span data-ttu-id="1ee55-127">WebRTC</span><span class="sxs-lookup"><span data-stu-id="1ee55-127">WebRTC</span></span>

<span data-ttu-id="1ee55-128">Il progetto MixedReality-WebRTC è una raccolta di componenti che consentono agli sviluppatori di app per la realtà mista di integrare comunicazioni audio, video e dati peer-to-peer in tempo reale nelle proprie applicazioni. I componenti WebRTC sono basati sul protocollo WebRTC per la comunicazioni RTC (Real-Time Communication), supportato dalla maggior parte dei moderni Web browser.</span><span class="sxs-lookup"><span data-stu-id="1ee55-128">The MixedReality-WebRTC project is a collection of components to help mixed reality app developers to integrate peer-to-peer audio, video, and data real-time communication into their applications WebRTC components are based on the WebRTC protocol for Real-Time Communication (RTC), which is supported by most modern web browsers.</span></span>

<br>

| <span data-ttu-id="1ee55-129">Articolo di riferimento</span><span class="sxs-lookup"><span data-stu-id="1ee55-129">Reference article</span></span> | <span data-ttu-id="1ee55-130">Esempio</span><span class="sxs-lookup"><span data-stu-id="1ee55-130">Sample</span></span> |
| --- | --- |
| [<span data-ttu-id="1ee55-131">WebRTC</span><span class="sxs-lookup"><span data-stu-id="1ee55-131">WebRTC</span></span>](https://microsoft.github.io/MixedReality-WebRTC) | [<span data-ttu-id="1ee55-132">App di esempio WebRTC</span><span class="sxs-lookup"><span data-stu-id="1ee55-132">WebRTC sample apps</span></span>](https://github.com/microsoft/MixedReality-WebRTC/tree/master/examples) |

### <a name="holographic-mixed-reality-capture"></a><span data-ttu-id="1ee55-133">Acquisizione realtà mista in modalità olografica</span><span class="sxs-lookup"><span data-stu-id="1ee55-133">Holographic Mixed Reality Capture</span></span>

<span data-ttu-id="1ee55-134">Acquisizione realtà mista (MRC, Mixed reality capture) acquisisce, in formato foto o video, l'esperienza in prima persona di mondi reali e digitali misti, consentendo di condividere ciò che si vede con altre persone in tempo reale.</span><span class="sxs-lookup"><span data-stu-id="1ee55-134">Mixed reality capture (MRC) captures the first-person experience of mixing real and digital worlds as a photo or video, sharing what you see with others in real-time.</span></span>

<br>

| <span data-ttu-id="1ee55-135">Articolo di riferimento</span><span class="sxs-lookup"><span data-stu-id="1ee55-135">Reference article</span></span> | <span data-ttu-id="1ee55-136">Esempio</span><span class="sxs-lookup"><span data-stu-id="1ee55-136">Sample</span></span> |
| --- | --- |
| [<span data-ttu-id="1ee55-137">Acquisizione realtà mista</span><span class="sxs-lookup"><span data-stu-id="1ee55-137">Mixed Reality Capture</span></span>](platform-capabilities-and-apis/mixed-reality-capture-for-developers.md) | [<span data-ttu-id="1ee55-138">Esempi di acquisizione realtà mista</span><span class="sxs-lookup"><span data-stu-id="1ee55-138">Mixed Reality Capture samples</span></span>](/samples/microsoft/windows-universal-samples/holographicmixedrealitycapture/) |

### <a name="holographic-remoting"></a><span data-ttu-id="1ee55-139">Holographic Remoting</span><span class="sxs-lookup"><span data-stu-id="1ee55-139">Holographic Remoting</span></span>

<span data-ttu-id="1ee55-140">Holographic Remoting Player è un'app complementare che si connette ad app e giochi per PC che supportano la tecnologia Holographic Remoting.</span><span class="sxs-lookup"><span data-stu-id="1ee55-140">The Holographic Remoting Player is a companion app that connects to PC apps and games that support Holographic Remoting.</span></span> <span data-ttu-id="1ee55-141">Questa tecnologia trasmette in streaming i contenuti olografici da un PC a Microsoft HoloLens in tempo reale, tramite una connessione Wi-Fi, ed è supportata in HoloLens (1a generazione) e HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="1ee55-141">Holographic Remoting streams holographic content from a PC to your Microsoft HoloLens in real-time, using a Wi-Fi connection, and is supported on HoloLens (1st gen) and HoloLens 2.</span></span>

<br>

| <span data-ttu-id="1ee55-142">Articolo di riferimento</span><span class="sxs-lookup"><span data-stu-id="1ee55-142">Reference article</span></span> | <span data-ttu-id="1ee55-143">Esempio</span><span class="sxs-lookup"><span data-stu-id="1ee55-143">Sample</span></span> |
| --- | --- |
| [<span data-ttu-id="1ee55-144">Holographic Remoting</span><span class="sxs-lookup"><span data-stu-id="1ee55-144">Holographic Remoting</span></span>](platform-capabilities-and-apis/holographic-remoting-player.md) | [<span data-ttu-id="1ee55-145">Esempi di Holographic Remoting</span><span class="sxs-lookup"><span data-stu-id="1ee55-145">Holographic Remoting samples</span></span>](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples) |
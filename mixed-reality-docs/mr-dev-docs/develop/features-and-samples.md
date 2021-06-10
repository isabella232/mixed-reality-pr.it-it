---
title: Esempi e app di funzionalità
description: Aggiornamenti costanti su tutti gli esempi Microsoft disponibili e le app di funzionalità di realtà mista per HoloLens.
author: hferrone
ms.author: jemccull
ms.date: 6/7/2021
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens, learn, esempi, MRTK, research mode, HoloLens 2, codici a matrice, WebRTC, acquisizione realtà mista, holographic remoting, UX Tools
ms.localizationpriority: high
ms.openlocfilehash: 5738c26366b3c1aafd86b20dc70a4d078fbffb1f
ms.sourcegitcommit: 62e5909b837c9c7ecedd040164f2308868db4723
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/08/2021
ms.locfileid: "111741943"
---
# <a name="samples-and-feature-apps"></a><span data-ttu-id="7c80d-104">Esempi e app di funzionalità</span><span class="sxs-lookup"><span data-stu-id="7c80d-104">Samples and feature apps</span></span>

![Immagine di un utente che indossa un dispositivo HoloLens e manipola un ologramma con il movimento delle mani](unreal/images/unreal-developer.jpg)

<span data-ttu-id="7c80d-106">Ogni percorso di sviluppo ha inizio con un'indagine retrospettiva su ciò che è già stato realizzato da altri sviluppatori. Questo è vero anche per la realtà mista.</span><span class="sxs-lookup"><span data-stu-id="7c80d-106">Every development journey starts with a look back at what other developers have successfully built - mixed reality is no different.</span></span> <span data-ttu-id="7c80d-107">Attualmente, tutte le esercitazioni e le app di esempio vengono create in Unity o Unreal.</span><span class="sxs-lookup"><span data-stu-id="7c80d-107">Currently, all of our tutorials and sample apps are built in Unity or Unreal.</span></span> <span data-ttu-id="7c80d-108">Il contenuto che viene sviluppato per altri motori e piattaforme sarà disponibile sotto l'intestazione pertinente nel Sommario.</span><span class="sxs-lookup"><span data-stu-id="7c80d-108">As we develop content for other engines and platforms, you'll find them under the relevant heading in the Table of Contents.</span></span>

## <a name="sample-apps"></a><span data-ttu-id="7c80d-109">App di esempio</span><span class="sxs-lookup"><span data-stu-id="7c80d-109">Sample apps</span></span>

[!INCLUDE[](includes/tabs-samples.md)]

## <a name="feature-samples"></a><span data-ttu-id="7c80d-110">Esempi di funzionalità</span><span class="sxs-lookup"><span data-stu-id="7c80d-110">Feature samples</span></span>

<span data-ttu-id="7c80d-111">Gli esempi di funzionalità elencati di seguito corrispondono a implementazioni specifiche illustrate nella documentazione Microsoft e riguardano una vasta gamma di piattaforme di sviluppo e dispositivi hardware.</span><span class="sxs-lookup"><span data-stu-id="7c80d-111">The feature samples listed below correspond to specific implementations that are covered in our documentation and covers a range of development platforms and hardware devices.</span></span>

### <a name="openxr"></a><span data-ttu-id="7c80d-112">OpenXR</span><span class="sxs-lookup"><span data-stu-id="7c80d-112">OpenXR</span></span>

<span data-ttu-id="7c80d-113">Per gli sviluppatori che hanno come destinazione Unity 2020 la creazione di applicazioni HoloLens 2 o realtà mista, è possibile usare il plug-in OpenXR invece del plug-in WindowsXR per una migliore compatibilità multipiattaforma.</span><span class="sxs-lookup"><span data-stu-id="7c80d-113">For developers targeting Unity 2020 to build HoloLens 2 or Mixed Reality applications, OpenXR plugin can be used instead of WindowsXR plugin for better cross platform compatibilities.</span></span> <span data-ttu-id="7c80d-114">Il plug-in OpenXR di realtà mista funziona bene anche con la versione più recente di Mixed Reality Toolkit 2.7.</span><span class="sxs-lookup"><span data-stu-id="7c80d-114">The Mixed Reality OpenXR Plugin also works well with latest Mixed Reality Toolkit 2.7.</span></span>

<br>

| <span data-ttu-id="7c80d-115">Articolo di riferimento</span><span class="sxs-lookup"><span data-stu-id="7c80d-115">Reference article</span></span> | <span data-ttu-id="7c80d-116">Esempio</span><span class="sxs-lookup"><span data-stu-id="7c80d-116">Sample</span></span> |
| --- | --- |
| [<span data-ttu-id="7c80d-117">Uso del plug-in OpenXR</span><span class="sxs-lookup"><span data-stu-id="7c80d-117">Using the OpenXR plugin</span></span>](unity/openxr-getting-started.md) | [<span data-ttu-id="7c80d-118">Esempi di Mixed Reality OpenXR con Unity</span><span class="sxs-lookup"><span data-stu-id="7c80d-118">Mixed Reality OpenXR with Unity samples</span></span>](https://github.com/microsoft/OpenXR-Unity-MixedReality-Samples) |
| <span data-ttu-id="7c80d-119">N/D</span><span class="sxs-lookup"><span data-stu-id="7c80d-119">N/A</span></span> | [<span data-ttu-id="7c80d-120">Progetto Unity di base di OpenXR MRTK</span><span class="sxs-lookup"><span data-stu-id="7c80d-120">OpenXR MRTK Base Unity project</span></span>](https://github.com/microsoft/UnityOpenXRMRTKBase) |

### <a name="research-mode"></a><span data-ttu-id="7c80d-121">Research Mode</span><span class="sxs-lookup"><span data-stu-id="7c80d-121">Research Mode</span></span>

<span data-ttu-id="7c80d-122">La funzionalità Research Mode è stata introdotta nel dispositivo HoloLens di prima generazione per consentire l'accesso ai sensori chiave sul dispositivo, in particolare per le applicazioni di ricerca che non sono destinate alla distribuzione.</span><span class="sxs-lookup"><span data-stu-id="7c80d-122">Research Mode was introduced in the 1st Generation HoloLens to give access to key sensors on the device, specifically for research applications that are not intended for deployment.</span></span> <span data-ttu-id="7c80d-123">Le applicazioni seguenti sono esempi relativi all'accesso e alla registrazione dei flussi di Search Mode e all'uso di funzioni [intrinseche ed estrinseche](/windows/mixed-reality/locatable-camera#locating-the-device-camera-in-the-world).</span><span class="sxs-lookup"><span data-stu-id="7c80d-123">The sample applications below are examples for accessing and recording Research Mode streams and using the [intrinsics and extrinsics](/windows/mixed-reality/locatable-camera#locating-the-device-camera-in-the-world).</span></span>

<br>

| <span data-ttu-id="7c80d-124">Articolo di riferimento</span><span class="sxs-lookup"><span data-stu-id="7c80d-124">Reference article</span></span> | <span data-ttu-id="7c80d-125">Applicazione di esempio</span><span class="sxs-lookup"><span data-stu-id="7c80d-125">Sample application</span></span> |
| --- | --- |
| [<span data-ttu-id="7c80d-126">Research Mode</span><span class="sxs-lookup"><span data-stu-id="7c80d-126">Research Mode</span></span>](platform-capabilities-and-apis/research-mode.md) | [<span data-ttu-id="7c80d-127">HoloLens (prima generazione)</span><span class="sxs-lookup"><span data-stu-id="7c80d-127">HoloLens (1st gen)</span></span>](https://github.com/microsoft/HoloLensForCV/tree/master/Samples) |
| [<span data-ttu-id="7c80d-128">Research Mode</span><span class="sxs-lookup"><span data-stu-id="7c80d-128">Research Mode</span></span>](platform-capabilities-and-apis/research-mode.md) | [<span data-ttu-id="7c80d-129">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="7c80d-129">HoloLens 2</span></span>](https://github.com/microsoft/HoloLens2ForCV/tree/main/Samples) |

### <a name="qr-codes"></a><span data-ttu-id="7c80d-130">Codici QR</span><span class="sxs-lookup"><span data-stu-id="7c80d-130">QR codes</span></span>

<span data-ttu-id="7c80d-131">HoloLens 2 è in grado di rilevare i codici a matrice nell'ambiente attorno al visore VR, stabilendo un sistema di coordinate nella posizione reale di ciascun codice.</span><span class="sxs-lookup"><span data-stu-id="7c80d-131">HoloLens 2 can detect QR codes in the environment around the headset, establishing a coordinate system at each code's real-world location.</span></span>

<br>

| <span data-ttu-id="7c80d-132">Articolo di riferimento</span><span class="sxs-lookup"><span data-stu-id="7c80d-132">Reference article</span></span> | <span data-ttu-id="7c80d-133">Esempio</span><span class="sxs-lookup"><span data-stu-id="7c80d-133">Sample</span></span> |
| --- | --- |
| [<span data-ttu-id="7c80d-134">Codici QR</span><span class="sxs-lookup"><span data-stu-id="7c80d-134">QR codes</span></span>](platform-capabilities-and-apis/qr-code-tracking.md) | [<span data-ttu-id="7c80d-135">Rilevamento di codici a matrice in Unity</span><span class="sxs-lookup"><span data-stu-id="7c80d-135">QR code tracking in Unity</span></span>](https://github.com/microsoft/MixedReality-QRCode-Sample) |

### <a name="scene-understanding"></a><span data-ttu-id="7c80d-136">Informazioni sulle scene</span><span class="sxs-lookup"><span data-stu-id="7c80d-136">Scene understanding</span></span>

<span data-ttu-id="7c80d-137">La comprensione della scena offre agli sviluppatori di realtà mista una rappresentazione strutturata di alto livello dell'ambiente progettata per rendere intuitivo lo sviluppo per applicazioni con consapevolezza ambientale.</span><span class="sxs-lookup"><span data-stu-id="7c80d-137">Scene understanding provides Mixed Reality developers with a structured, high-level environment representation designed to make developing for environmentally aware applications intuitive.</span></span> <span data-ttu-id="7c80d-138">La comprensione della scena combina la potenza dei runtime di realtà mista esistenti, ad esempio il mapping spaziale estremamente accurato ma meno strutturato e i nuovi runtime di intelligenza artificiale.</span><span class="sxs-lookup"><span data-stu-id="7c80d-138">Scene understanding does this by combining the power of existing mixed reality runtimes, like the highly accurate but less structured spatial mapping and new AI driven runtimes.</span></span>

<br>

| <span data-ttu-id="7c80d-139">Articolo di riferimento</span><span class="sxs-lookup"><span data-stu-id="7c80d-139">Reference article</span></span> | <span data-ttu-id="7c80d-140">Esempio</span><span class="sxs-lookup"><span data-stu-id="7c80d-140">Sample</span></span> |
| --- | --- |
| [<span data-ttu-id="7c80d-141">Informazioni sulle scene</span><span class="sxs-lookup"><span data-stu-id="7c80d-141">Scene understanding</span></span>](../design/scene-understanding.md) | [<span data-ttu-id="7c80d-142">Esempi di comprensione della scena di realtà mista</span><span class="sxs-lookup"><span data-stu-id="7c80d-142">Mixed Reality Scene Understanding samples</span></span>](https://github.com/microsoft/MixedReality-SceneUnderstanding-Samples) |

### <a name="webrtc"></a><span data-ttu-id="7c80d-143">WebRTC</span><span class="sxs-lookup"><span data-stu-id="7c80d-143">WebRTC</span></span>

<span data-ttu-id="7c80d-144">Il progetto MixedReality-WebRTC è una raccolta di componenti che consentono agli sviluppatori di app per la realtà mista di integrare comunicazioni audio, video e dati peer-to-peer in tempo reale nelle proprie applicazioni. I componenti WebRTC sono basati sul protocollo WebRTC per la comunicazioni RTC (Real-Time Communication), supportato dalla maggior parte dei moderni Web browser.</span><span class="sxs-lookup"><span data-stu-id="7c80d-144">The MixedReality-WebRTC project is a collection of components to help mixed reality app developers to integrate peer-to-peer audio, video, and data real-time communication into their applications WebRTC components are based on the WebRTC protocol for Real-Time Communication (RTC), which is supported by most modern web browsers.</span></span>

<br>

| <span data-ttu-id="7c80d-145">Articolo di riferimento</span><span class="sxs-lookup"><span data-stu-id="7c80d-145">Reference article</span></span> | <span data-ttu-id="7c80d-146">Esempio</span><span class="sxs-lookup"><span data-stu-id="7c80d-146">Sample</span></span> |
| --- | --- |
| [<span data-ttu-id="7c80d-147">WebRTC</span><span class="sxs-lookup"><span data-stu-id="7c80d-147">WebRTC</span></span>](https://microsoft.github.io/MixedReality-WebRTC) | [<span data-ttu-id="7c80d-148">App di esempio WebRTC</span><span class="sxs-lookup"><span data-stu-id="7c80d-148">WebRTC sample apps</span></span>](https://github.com/microsoft/MixedReality-WebRTC/tree/master/examples) |

### <a name="holographic-mixed-reality-capture"></a><span data-ttu-id="7c80d-149">Acquisizione realtà mista in modalità olografica</span><span class="sxs-lookup"><span data-stu-id="7c80d-149">Holographic Mixed Reality Capture</span></span>

<span data-ttu-id="7c80d-150">Acquisizione realtà mista (MRC, Mixed reality capture) acquisisce, in formato foto o video, l'esperienza in prima persona di mondi reali e digitali misti, consentendo di condividere ciò che si vede con altre persone in tempo reale.</span><span class="sxs-lookup"><span data-stu-id="7c80d-150">Mixed reality capture (MRC) captures the first-person experience of mixing real and digital worlds as a photo or video, sharing what you see with others in real-time.</span></span>

<br>

| <span data-ttu-id="7c80d-151">Articolo di riferimento</span><span class="sxs-lookup"><span data-stu-id="7c80d-151">Reference article</span></span> | <span data-ttu-id="7c80d-152">Esempio</span><span class="sxs-lookup"><span data-stu-id="7c80d-152">Sample</span></span> |
| --- | --- |
| [<span data-ttu-id="7c80d-153">Acquisizione realtà mista</span><span class="sxs-lookup"><span data-stu-id="7c80d-153">Mixed Reality Capture</span></span>](platform-capabilities-and-apis/mixed-reality-capture-for-developers.md) | [<span data-ttu-id="7c80d-154">Esempi di acquisizione realtà mista</span><span class="sxs-lookup"><span data-stu-id="7c80d-154">Mixed Reality Capture samples</span></span>](/samples/microsoft/windows-universal-samples/holographicmixedrealitycapture/) |

### <a name="holographic-remoting"></a><span data-ttu-id="7c80d-155">Holographic Remoting</span><span class="sxs-lookup"><span data-stu-id="7c80d-155">Holographic Remoting</span></span>

<span data-ttu-id="7c80d-156">Holographic Remoting Player è un'app complementare che si connette ad app e giochi per PC che supportano la tecnologia Holographic Remoting.</span><span class="sxs-lookup"><span data-stu-id="7c80d-156">The Holographic Remoting Player is a companion app that connects to PC apps and games that support Holographic Remoting.</span></span> <span data-ttu-id="7c80d-157">Questa tecnologia trasmette in streaming i contenuti olografici da un PC a Microsoft HoloLens in tempo reale, tramite una connessione Wi-Fi, ed è supportata in HoloLens (1a generazione) e HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="7c80d-157">Holographic Remoting streams holographic content from a PC to your Microsoft HoloLens in real-time, using a Wi-Fi connection, and is supported on HoloLens (1st gen) and HoloLens 2.</span></span>

<br>

| <span data-ttu-id="7c80d-158">Articolo di riferimento</span><span class="sxs-lookup"><span data-stu-id="7c80d-158">Reference article</span></span> | <span data-ttu-id="7c80d-159">Esempio</span><span class="sxs-lookup"><span data-stu-id="7c80d-159">Sample</span></span> |
| --- | --- |
| [<span data-ttu-id="7c80d-160">Holographic Remoting</span><span class="sxs-lookup"><span data-stu-id="7c80d-160">Holographic Remoting</span></span>](platform-capabilities-and-apis/holographic-remoting-player.md) | [<span data-ttu-id="7c80d-161">Esempi di Holographic Remoting</span><span class="sxs-lookup"><span data-stu-id="7c80d-161">Holographic Remoting samples</span></span>](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples) |
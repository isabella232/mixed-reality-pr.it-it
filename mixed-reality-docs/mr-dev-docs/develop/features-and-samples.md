---
title: Esempi e app di funzionalità
description: Aggiornamenti costanti su tutti gli esempi Microsoft disponibili e le app di funzionalità di realtà mista per HoloLens.
author: hferrone
ms.author: jemccull
ms.date: 6/7/2021
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens, learn, esempi, MRTK, research mode, HoloLens 2, codici a matrice, WebRTC, acquisizione realtà mista, holographic remoting, UX Tools
ms.localizationpriority: high
ms.openlocfilehash: 1c713604f3a73620c4b7314afe7b70e0b2a59bef1c4e0ae0482c7f0143c38e71
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115227673"
---
# <a name="samples-and-feature-apps"></a>Esempi e app di funzionalità

![Immagine di un utente che indossa un dispositivo HoloLens e manipola un ologramma con il movimento delle mani](unreal/images/unreal-developer.jpg)

Ogni percorso di sviluppo ha inizio con un'indagine retrospettiva su ciò che è già stato realizzato da altri sviluppatori. Questo è vero anche per la realtà mista. Attualmente, tutte le esercitazioni e le app di esempio vengono create in Unity o Unreal. Il contenuto che viene sviluppato per altri motori e piattaforme sarà disponibile sotto l'intestazione pertinente nel Sommario.

## <a name="sample-apps"></a>App di esempio

[!INCLUDE[](includes/tabs-samples.md)]

## <a name="feature-samples"></a>Esempi di funzionalità

Gli esempi di funzionalità elencati di seguito corrispondono a implementazioni specifiche illustrate nella documentazione Microsoft e riguardano una vasta gamma di piattaforme di sviluppo e dispositivi hardware.

### <a name="openxr"></a>OpenXR

Per gli sviluppatori che hanno come destinazione Unity 2020 la compilazione di applicazioni HoloLens 2 o realtà mista, è possibile usare il plug-in OpenXR invece del plug-in WindowsXR per migliorare la compatibilità multipiattaforma. Il plug-in OpenXR di realtà mista funziona bene anche con la versione più recente di Mixed Reality Toolkit 2.7.

<br>

| Articolo di riferimento | Esempio |
| --- | --- |
| [Uso del plug-in OpenXR](./unity/xr-project-setup.md) | [Esempi di Mixed Reality OpenXR con Unity](https://github.com/microsoft/OpenXR-Unity-MixedReality-Samples) |
| N/D | [Progetto Unity di base di OpenXR MRTK](https://github.com/microsoft/UnityOpenXRMRTKBase) |

### <a name="research-mode"></a>Research Mode

La funzionalità Research Mode è stata introdotta nel dispositivo HoloLens di prima generazione per consentire l'accesso ai sensori chiave sul dispositivo, in particolare per le applicazioni di ricerca che non sono destinate alla distribuzione. Le applicazioni seguenti sono esempi relativi all'accesso e alla registrazione dei flussi di Search Mode e all'uso di funzioni [intrinseche ed estrinseche](/windows/mixed-reality/locatable-camera#locating-the-device-camera-in-the-world).

<br>

| Articolo di riferimento | Applicazione di esempio |
| --- | --- |
| [Research Mode](platform-capabilities-and-apis/research-mode.md) | [HoloLens (prima generazione)](https://github.com/microsoft/HoloLensForCV/tree/master/Samples) |
| [Research Mode](platform-capabilities-and-apis/research-mode.md) | [HoloLens 2](https://github.com/microsoft/HoloLens2ForCV/tree/main/Samples) |

### <a name="qr-codes"></a>Codici QR

HoloLens 2 è in grado di rilevare i codici a matrice nell'ambiente attorno al visore VR, stabilendo un sistema di coordinate nella posizione reale di ciascun codice.

<br>

| Articolo di riferimento | Esempio |
| --- | --- |
| [Codici QR](platform-capabilities-and-apis/qr-code-tracking.md) | [Rilevamento di codici a matrice in Unity](https://github.com/microsoft/MixedReality-QRCode-Sample) |

### <a name="scene-understanding"></a>Informazioni sulle scene

La comprensione della scena offre agli sviluppatori di realtà mista una rappresentazione strutturata di alto livello dell'ambiente progettata per rendere intuitivo lo sviluppo per applicazioni con consapevolezza ambientale. La comprensione della scena combina la potenza dei runtime di realtà mista esistenti, ad esempio il mapping spaziale estremamente accurato ma meno strutturato e i nuovi runtime di intelligenza artificiale.

<br>

| Articolo di riferimento | Esempio |
| --- | --- |
| [Informazioni sulle scene](../design/scene-understanding.md) | [Esempi di comprensione della scena di realtà mista](https://github.com/microsoft/MixedReality-SceneUnderstanding-Samples) |

### <a name="webrtc"></a>WebRTC

Il progetto MixedReality-WebRTC è una raccolta di componenti che consentono agli sviluppatori di app per la realtà mista di integrare comunicazioni audio, video e dati peer-to-peer in tempo reale nelle proprie applicazioni. I componenti WebRTC sono basati sul protocollo WebRTC per la comunicazioni RTC (Real-Time Communication), supportato dalla maggior parte dei moderni Web browser.

<br>

| Articolo di riferimento | Esempio |
| --- | --- |
| [WebRTC](https://microsoft.github.io/MixedReality-WebRTC) | [App di esempio WebRTC](https://github.com/microsoft/MixedReality-WebRTC/tree/master/examples) |

### <a name="holographic-mixed-reality-capture"></a>Acquisizione realtà mista in modalità olografica

Acquisizione realtà mista (MRC, Mixed reality capture) acquisisce, in formato foto o video, l'esperienza in prima persona di mondi reali e digitali misti, consentendo di condividere ciò che si vede con altre persone in tempo reale.

<br>

| Articolo di riferimento | Esempio |
| --- | --- |
| [Acquisizione realtà mista](platform-capabilities-and-apis/mixed-reality-capture-for-developers.md) | [Esempi di acquisizione realtà mista](/samples/microsoft/windows-universal-samples/holographicmixedrealitycapture/) |

### <a name="holographic-remoting"></a>Holographic Remoting

Holographic Remoting Player è un'app complementare che si connette ad app e giochi per PC che supportano la tecnologia Holographic Remoting. Questa tecnologia trasmette in streaming i contenuti olografici da un PC a Microsoft HoloLens in tempo reale, tramite una connessione Wi-Fi, ed è supportata in HoloLens (1a generazione) e HoloLens 2.

<br>

| Articolo di riferimento | Esempio |
| --- | --- |
| [Holographic Remoting](platform-capabilities-and-apis/holographic-remoting-player.md) | [Esempi di Holographic Remoting](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples) |
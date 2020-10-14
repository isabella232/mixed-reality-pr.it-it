---
title: Panoramica dello sviluppo con Unreal
description: Panoramica dello sviluppo della realtà mista con Unreal Engine 4
author: hferrone
ms.author: v-hferrone
ms.date: 08/04/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, beta, streaming, comunicazione remota, realtà mista, sviluppo, guida introduttiva, funzionalità, nuovo progetto, emulatore, documentazione, guide, caratteristiche, ologrammi, sviluppo di giochi
ms.openlocfilehash: 3b5dc5d0ce1510405960c6effd653acc9c2588b2
ms.sourcegitcommit: 9ab467e36d7d9fad51b0e93a56038a6421a7b09d
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/13/2020
ms.locfileid: "91980342"
---
# <a name="unreal-development-overview"></a>Panoramica dello sviluppo con Unreal

![Logo banner Unreal](../images/unreal_logo_banner.png)

Muovere i primi passi nelle <a href="https://docs.microsoft.com/windows/mixed-reality" target="_blank" title="Documentazione sulla realtà mista">applicazioni in realtà mista</a> è un'attività complessa. Nuovi concetti, nuove piattaforme e hardware all'avanguardia possono sembrare ostacoli difficili da superare. Gli sviluppatori che usano Unreal, però, hanno un asso nella manica. Nella <a href="https://docs.unrealengine.com/Support/Builds/ReleaseNotes/4_25/index.html" target="_blank" title="Note sulla versione di Unreal Engine 4.25">versione</a> più recente di Unreal Engine è incluso il supporto per <a href="https://www.microsoft.com/windows/windows-mixed-reality" target="_blank" title="Documentazione su Windows Mixed Reality">Windows Mixed Reality</a> (VR) e <a href="https://www.microsoft.com/hololens/hardware" target="_blank" title="Documentazione su HoloLens 2">HoloLens 2</a> (AR). Questo aggiornamento include:
* Supporto del plug-in UX Tools di Mixed Reality Toolkit
* Supporto di OpenXR
* Comunicazione remota da un'app desktop
* Prestazioni migliori
* Acquisizione in realtà mista (MRC, Mixed Reality Capture)
* Supporto iniziale per Ancoraggi nello spazio di Azure

Se non hai esperienza di sviluppo con Unreal, non iniziare alla cieca. Esplora la <a href="https://docs.unrealengine.com/GettingStarted/index.html" target="_blank">serie di esercitazioni</a> su Unreal per acquisire familiarità e cerca risorse e supporto nel <a href="https://www.unrealengine.com/marketplace/store" target="_blank">marketplace</a> di Unreal e nei <a href="https://forums.unrealengine.com/development-discussion/vr-ar-development" target="_blank">forum</a> dedicati alla realtà mista. Queste risorse ti consentono di entrare in contatto con la community di sviluppatori e risolutori di problemi che operano oggi sul mercato della realtà mista.

## <a name="development-checkpoints"></a>Checkpoint di sviluppo

Usare i checkpoint seguenti per portare i giochi e le applicazioni Unreal nel mondo della realtà mista. Se non è stata ancora esplorata l'[applicazione di esempio Designing Holograms](https://www.microsoft.com/p/designing-holograms/9nxwnjklrzwd), è consigliabile scaricarla e usarla per acquisire familiarità con i concetti di base dell'esperienza utente in realtà mista.

### <a name="1-getting-started"></a>1. Guida introduttiva

[Mixed Reality Toolkit per Unreal](https://github.com/microsoft/MixedRealityToolkit-Unreal) è un set di componenti progettati per accelerare lo sviluppo in Unreal. Ogni componente include plug-in, esempi e documentazione per la creazione di esperienze immersive.

* [UX Tools per Unreal](https://github.com/microsoft/MixedReality-UXTools-Unreal) è il primo componente rilasciato ed è attualmente supportato solo su HoloLens 2. Il plug-in del componente include codice, progetti e asset di esempio delle funzionalità UX comuni per simulazione di input, attori di interazione manuale, componenti pulsante a pressione, componenti manipolatore e componenti comportamento.

Alla fine di questa sezione, si avrà una conoscenza di base su Mixed Reality Toolkit, un ambiente di sviluppo configurato correttamente per le app di realtà mista e un progetto MRTK funzionante in Unreal.

|  Checkpoint  |  Risultato  |
| --- | --- |
| [Installare gli ultimi aggiornamenti](../install-the-tools.md) | Scaricare e installare il pacchetto Unity più recente e configurare il progetto per la realtà mista |
| [Serie di esercitazioni su HoloLens 2](tutorials/unreal-uxt-ch1.md) | Seguire le esercitazioni su MRTK di livello principiante per l'hardware HoloLens 2 |

### <a name="2-core-building-blocks"></a>2. Componenti fondamentali

Ci sono diverse funzionalità chiave dello sviluppo per la realtà mista che non vengono trattate nella nostra serie di esercitazioni. Questi blocchi predefiniti sono disponibili come funzionalità autonome e tramite il Mixed Reality Toolkit. Potrebbero non essere tutti necessari nell'immediato, ma è bene esaminarli nella fase iniziale. Dopo avere esaminato i blocchi predefiniti fondamentali indicati di seguito, si avrà a disposizione un insieme completo di funzionalità da integrare nei progetti di realtà mista.

[!INCLUDE[](../includes/unreal-building-blocks.md)]

> [!NOTE]
> Per informazioni dettagliate, esaminare il **[repository di GitHub su UX Tools per Unreal](https://github.com/microsoft/MixedReality-UXTools-Unreal)** .

### <a name="3-platform-capabilities-and-apis"></a>3. API e funzionalità della piattaforma

Altre funzionalità chiave per le applicazioni di realtà mista sono disponibili senza ulteriori pacchetti o configurazioni. Queste funzionalità possono essere aggiunte ai progetti Unreal anche senza avere installato MRTK. Dopo avere esaminato queste funzionalità più avanzate, sarà possibile creare app di realtà mista più complesse.

|  Funzionalità  |  Capabilities  |
| --- | --- |
| [Fotocamera HoloLens](unreal-hololens-camera.md) | Acquisire contenuti visivi di realtà mista e del mondo reale dall'app in esecuzione su un dispositivo HoloLens |
| [Codici QR](unreal-qr-codes.md) | Eseguire il rendering di codici a matrice come ologrammi usando un sistema di coordinate nella posizione reale di ogni codice |
| [WinRT](unreal-winrt.md) | Creare un file binario separato con codice WinRT che può essere utilizzato dal sistema di compilazione di Unreal |

### <a name="4-deploying-to-a-device"></a>4. Distribuzione nel dispositivo

Se è la prima volta che crei o distribuisci un'app Unreal per HoloLens, dovrai [scaricare i file di supporto](tutorials/unreal-uxt-ch6.md#packaging-and-deploying-the-app-via-device-portal) dal launcher Epic. Una volta installati i file, è possibile eseguire la distribuzione dall'[editor Unreal](unreal-deploying.md) o dal [portale di dispositivi](tutorials/unreal-uxt-ch6.md#packaging-and-deploying-the-app-via-device-portal).

### <a name="5-adding-services"></a>5. Aggiunta di servizi

A questo punto del percorso di sviluppo, potrebbe essere necessario aggiungere servizi o ricevere supporto per una distribuzione commerciale. L'integrazione di [Servizi cloud di Azure](../mixed-reality-cloud-services.md) e funzionalità di Dynamics 365 può migliorare notevolmente i progetti. Abbiamo stilato alcuni punti di partenza per acquisire maggiori competenze sulla realtà mista.

[!INCLUDE[](../includes/unreal-cloud-services-d365.md)]

## <a name="whats-next"></a>Passaggi successivi

Il lavoro degli sviluppatori non finisce mai, soprattutto per quanto riguarda la conoscenza di nuovi strumenti o SDK. Le sezioni seguenti consentono di affrontare aspetti più avanzati rispetto al materiale di livello principiante già completato e di accedere a risorse utili se si rimane bloccati. Questi argomenti e queste risorse non sono presentati in ordine sequenziale, quindi possono essere esplorati liberamente.

### <a name="streaming--debugging"></a>Streaming e debug

Se si vuole testare l'applicazione in un dispositivo HoloLens mentre è ancora in fase di sviluppo, è possibile [trasmetterla in streaming direttamente dal PC](unreal-streaming.md) usando l'editor Unreal o un eseguibile Windows in pacchetto.

Se si vuole eseguire il debug dell'applicazione con Visual Studio, seguire queste [istruzioni](https://docs.microsoft.com/visualstudio/debugger/debug-installed-app-package#remote).

### <a name="performance"></a>Prestazioni

Lo sviluppo per la realtà mista prevede punti di controllo delle prestazioni che dipendono dalla piattaforma. Un'app HoloLens 2 deve essere eseguita a 60 fotogrammi al secondo perché gli ologrammi risultino stabili e reattivi. I [consigli sulle prestazioni](performance-recommendations-for-unreal.md) consentono di soddisfare questo requisito nelle applicazioni Unreal.

## <a name="supported-features"></a>Funzionalità supportate

| Funzionalità di HoloLens 2 | Prima versione di Unreal Engine supportata |
| ----------- | ----------- |
| Supporto per ARM64 | 4.23 |
| Streaming da un PC | 4.23 |
| Mapping spaziale | 4.23 |
| Tracciamento mano e articolazioni | 4.23 |
| Tracciamento oculare | 4.23 |
| Input vocale | 4.23 |
| Ancoraggi nello spazio | 4.23 |
| Accesso alla fotocamera | 4.23 |
| Codici QR | 4.23 |
| Audio spaziale | 4.23 |
| Supporto Spectator Screen per lo streaming | 4.24 |
| LSR planare sullo streaming | 4.24 |
| App di esempio ([HoloLens2Example](https://github.com/microsoft/MixedReality-Unreal-Samples) e [Mission AR](https://docs.unrealengine.com/Resources/Showcases/MissionAR/index.html)) | 4.24 |
| Mobile Multi-View: prestazioni fino a 60 fps | 4.25 |
| Rendering della terza fotocamera | 4.25 |
| Streaming da un'app desktop in pacchetto | 4.25.1 |
| Ancoraggi nello spazio di Azure per HoloLens 2 (beta) | 4.25 |
| Supporto per OpenXR (beta) | 4.25 |
| Supporto per UX Tools (0.8) | 4.25 |
| Documentazione ed esercitazioni per sviluppatori | 4.25 |

> [!div class="nextstepaction"]
> [Installare gli strumenti](../install-the-tools.md)

## <a name="see-also"></a>Vedere anche
* <a href="https://docs.unrealengine.com/Platforms/AR/HoloLens2/index.html" target="_blank">Unreal docs for streaming, deploying to emulator and device</a> (Documentazione su Unreal per lo streaming e la distribuzione in un emulatore e un dispositivo)
* <a href="https://docs.unrealengine.com/Platforms/Mobile/Performance/index.html" target="_blank">Unreal performance guidelines for mobile devices</a> (Linee guida sulle prestazioni di Unreal per i dispositivi mobili)

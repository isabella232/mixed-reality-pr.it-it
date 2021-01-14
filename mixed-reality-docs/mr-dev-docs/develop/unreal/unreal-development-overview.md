---
title: Panoramica dello sviluppo con Unreal
description: Introduzione allo sviluppo di realtà mista per HoloLens e VR con Unreal Engine 4 tramite il percorso di checkpoint dedicato.
author: hferrone
ms.author: v-hferrone
ms.date: 12/9/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, streaming, comunicazione remota, realtà mista, sviluppo, guida introduttiva, funzionalità, nuovo progetto, emulatore, documentazione, guide, caratteristiche, ologrammi, sviluppo di giochi, visore VR realtà mista, visore VR di windows mixed reality, visore per realtà virtuale, OpenXR
ms.openlocfilehash: 3d9a33ca98734d40a37e24805f28f7f70b6a4ba9
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2021
ms.locfileid: "98009761"
---
# <a name="unreal-development-overview"></a>Panoramica dello sviluppo con Unreal

![Logo banner Unreal](../images/unreal_logo_banner.png)

Muovere i primi passi nelle <a href="https://docs.microsoft.com/windows/mixed-reality" target="_blank" title="Documentazione sulla realtà mista">applicazioni in realtà mista</a> è un'attività complessa. Nuovi concetti, nuove piattaforme e hardware all'avanguardia possono sembrare ostacoli difficili da superare. Gli sviluppatori che usano Unreal, però, hanno un asso nella manica. In Unreal Engine 4 è incluso il supporto per <a href="https://www.microsoft.com/windows/windows-mixed-reality" target="_blank" title="Documentazione su Windows Mixed Reality">Windows Mixed Reality</a> (VR) e <a href="https://www.microsoft.com/hololens/hardware" target="_blank" title="Documentazione sui dispositivi HoloLens 2">HoloLens 2</a> (AR).

[!INCLUDE[](includes/tabs-unreal-features.md)]

Se non si ha esperienza di sviluppo con Unreal, non iniziare alla cieca. Esplorare la <a href="https://docs.unrealengine.com/GettingStarted/index.html" target="_blank">serie di esercitazioni</a> su Unreal e cercare le risorse nel <a href="https://www.unrealengine.com/marketplace/store" target="_blank">marketplace</a> di Unreal. È anche possibile trovare supporto nei forum sulla <a href="https://forums.unrealengine.com/development-discussion/vr-ar-development" target="_blank">realtà mista</a>. Queste risorse consentono di entrare in contatto con la community di sviluppatori e risolutori di problemi che operano oggi sul mercato della realtà mista.

> [!IMPORTANT]
> Se si ha a disposizione un progetto Unreal da trasferire in un visore VR immersive come Reverb G2, consultare la **[guida per il porting](unreal-reverb-g2-controllers.md)** .

## <a name="development-checkpoints"></a>Checkpoint di sviluppo

Usare i checkpoint seguenti per portare i giochi e le applicazioni Unreal nel mondo della realtà mista. Se non si è ancora esaminata l'[applicazione di esempio Designing Holograms](https://www.microsoft.com/p/designing-holograms/9nxwnjklrzwd), è consigliabile scaricarla per acquisire familiarità con i concetti di base dell'esperienza utente in realtà mista.

### <a name="1-getting-started"></a>1. Guida introduttiva

Prima di tutto, è necessario installare gli strumenti per lo sviluppo di app per HoloLens 2. Completare quindi la serie di esercitazioni per acquisire una conoscenza di base di Mixed Reality Toolkit, un ambiente di sviluppo appositamente configurato per le app di realtà mista e un progetto MRTK funzionante in Unreal. A partire da Unreal 4.26, è anche possibile sviluppare un'app OpenXR per HoloLens 2.

|  Checkpoint  |  Risultato  |
| --- | --- |
| [Installare gli ultimi aggiornamenti](../install-the-tools.md) | Scaricare e installare la versione più recente di Unreal Engine e configurare il progetto per la realtà mista |
| [Serie di esercitazioni su HoloLens 2](tutorials/unreal-uxt-ch1.md) | Acquisire le informazioni necessarie per sviluppare app di realtà mista in Unreal, compilare la prima app con MRTK e distribuire l'app in HoloLens 2 |
| (Facoltativo) Iniziare a usare [OpenXR](../native/openxr.md) in Unreal | Se si ha l'intenzione di creare un'app OpenXR in Unreal, è necessario disabilitare il plug-in del motore seguente:<ul><li>Windows Mixed Reality</li></ul><br>Scaricare e abilitare il plug-in seguente nel progetto da GitHub:<ul><li> [Microsoft OpenXR](https://github.com/microsoft/Microsoft-OpenXR-Unreal)</li></ul><br>L'elenco completo delle funzionalità attualmente supportate in OpenXR è [riportato di seguito](#supported-features).|

### <a name="2-core-building-blocks"></a>2. Componenti fondamentali

Ci sono diverse funzionalità chiave per la realtà mista che non vengono trattate in questa serie di esercitazioni. Questi blocchi predefiniti sono disponibili come funzionalità autonome e tramite il Mixed Reality Toolkit. Potrebbero non essere tutti necessari nell'immediato, ma è bene esaminarli nella fase iniziale. Dopo avere esaminato i blocchi predefiniti fondamentali indicati di seguito, si avrà a disposizione un insieme completo di funzionalità da integrare nei progetti di realtà mista.

[Mixed Reality Toolkit per Unreal](https://github.com/microsoft/MixedRealityToolkit-Unreal) è un set di plug-in progettati per accelerare lo sviluppo in Unreal. Ogni plug-in include componenti, esempi e documentazione per la creazione di esperienze immersive.

* [UX Tools for Unreal](https://www.unrealengine.com/marketplace/en-US/product/mixed-reality-ux-tools) è il primo plug-in rilasciato ed è attualmente supportato solo su HoloLens 2. Il plug-in include codice C++, progetti e asset di esempio di funzionalità di UX comuni per la simulazione di input, le interazioni con le mani, il magnetismo della superficie e altro ancora.

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

### <a name="4-streaming-and-deploying-to-a-device"></a>4. Trasmissione in streaming e distribuzione in un dispositivo

Se si vuole testare l'applicazione in un dispositivo HoloLens mentre è ancora in fase di sviluppo, è possibile [trasmetterla in streaming direttamente dal PC](unreal-streaming.md) usando l'editor Unreal o un eseguibile Windows in pacchetto.

Se è la prima volta che si distribuisce un'app Unreal in HoloLens 2, sarà necessario [scaricare i file di supporto](tutorials/unreal-uxt-ch6.md#packaging-and-deploying-the-app-via-device-portal) dal launcher Epic. Una volta installati i file, è possibile eseguire la distribuzione dall'[editor Unreal](unreal-deploying.md) o dal [portale di dispositivi](tutorials/unreal-uxt-ch6.md#packaging-and-deploying-the-app-via-device-portal).

### <a name="5-adding-services"></a>5. Aggiunta di servizi

A questo punto del percorso di sviluppo, potrebbe essere necessario aggiungere servizi o ricevere supporto per una distribuzione commerciale. L'integrazione di [Servizi cloud di Azure](../mixed-reality-cloud-services.md) e funzionalità di Dynamics 365 può migliorare notevolmente i progetti. Abbiamo stilato alcuni punti di partenza per acquisire maggiori competenze sulla realtà mista.

[!INCLUDE[](../includes/unreal-cloud-services-d365.md)]

## <a name="whats-next"></a>Passaggi successivi

Il lavoro di uno sviluppatore non finisce mai, soprattutto per quanto riguarda l'apprendimento di nuovi strumenti o SDK. Le sezioni seguenti consentono di affrontare aspetti più avanzati rispetto al materiale di livello principiante già completato e di accedere a risorse utili se si rimane bloccati. Questi argomenti e queste risorse non sono presentati in ordine sequenziale, quindi possono essere esplorati liberamente.

### <a name="debugging"></a>Debug

Se si vuole eseguire il debug dell'applicazione in esecuzione sul dispositivo con Visual Studio, seguire queste [istruzioni](https://docs.microsoft.com/visualstudio/debugger/debug-installed-app-package#remote).

### <a name="performance"></a>Prestazioni

Lo sviluppo per la realtà mista prevede punti di controllo delle prestazioni che dipendono dalla piattaforma. Un'app HoloLens 2 deve essere eseguita a 60 fotogrammi al secondo perché gli ologrammi risultino stabili e reattivi. Nei [consigli sulle prestazioni](performance-recommendations-for-unreal.md) è possibile trovare informazioni su come migliorare le prestazioni nelle applicazioni Unreal.

## <a name="supported-features"></a>Funzionalità supportate

| Funzionalità di HoloLens 2 | Prima versione di Unreal Engine supportata | Supportata in OpenXR (4.26) |
| ----------- | ----------- | ----------- |
| Supporto per ARM64 | 4.23 | ✔️ |
| Streaming da un PC | 4.23 | ✔️ |
| Mapping spaziale | 4.23 | ✔️ |
| Tracciamento mano e articolazioni | 4.23 | ✔️ |
| Tracciamento oculare | 4.23 | ✔️ |
| Input vocale | 4.23 | ✔️ |
| Ancoraggi nello spazio | 4.23 | ✔️ |
| Accesso alla fotocamera | 4.23 |
| Codici QR | 4.23 | ✔️ |
| Audio spaziale | 4.23 | ✔️ |
| Supporto Spectator Screen per lo streaming | 4.24 |
| LSR planare sullo streaming | 4.24 |
| [App di esempio](unreal-samples.md) | 4.24 | ✔️ |
| Mobile Multi-View: prestazioni fino a 60 fps | 4.25 | ✔️ |
| Rendering della terza fotocamera | 4.25 |
| Streaming da un'app desktop in pacchetto | 4.25.1 | ✔️ |
| Ancoraggi nello spazio di Azure per HoloLens 2 (beta) | 4.25 |
| Supporto del plug-in UX Tools di Mixed Reality Toolkit | 4.25 | ✔️ |
| Documentazione ed esercitazioni per sviluppatori | 4.25 | ✔️ |
| Tastiera di sistema | 4.26 | ✔️ |
| Plug-in HoloLens Media Player | 4.26 | ✔️ |
| Ancoraggi nello spazio di Azure per Android e iOS (beta) | 4.26 |
| Plug-in Microsoft OpenXR con estensioni OpenXR specifiche del fornitore Microsoft | 4.26 | ✔️ |
| Streaming da Azure a HoloLens 2 | 4.26 | ✔️ |
| Conformità del kit di certificazione app Windows per le app in pacchetto | 4.26 | ✔️ |
| Supporto del controller HP Reverb G2 | 4.26 | ✔️ |

> [!div class="nextstepaction"]
> [Installare gli strumenti](../install-the-tools.md)

## <a name="see-also"></a>Vedere anche
* <a href="https://docs.unrealengine.com/Platforms/AR/HoloLens2/index.html" target="_blank">Unreal docs for streaming, deploying to emulator and device</a> (Documentazione su Unreal per lo streaming e la distribuzione in un emulatore e un dispositivo)
* <a href="https://docs.unrealengine.com/Platforms/Mobile/Performance/index.html" target="_blank">Unreal performance guidelines for mobile devices</a> (Linee guida sulle prestazioni di Unreal per i dispositivi mobili)

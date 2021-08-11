---
title: Panoramica di Holographic Remoting
description: Informazioni su Holographic Remoting e su come può trarre vantaggio dal processo di sviluppo.
author: hferrone
ms.author: v-vtieto
ms.date: 07/26/2021
ms.topic: article
keywords: openxr, unity, hololens, hololens 2, realtà mista, MRTK, realtà mista Toolkit, realtà aumentata, realtà virtuale, visori VR di realtà mista, apprendimento, esercitazione, introduzione, comunicazione remota olografica, desktop, anteprima
ms.openlocfilehash: 1b20590429b7df209e805ed8e94de5a6010bdbb609edc10fc5854cd4df86f64c
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115217117"
---
# <a name="holographic-remoting-overview"></a>Panoramica di Holographic Remoting

Quando aggiungi il supporto per Holographic Rendering all'app o al gioco per PC, consente all'app di trasmettere contenuto olografico al HoloLens 2 in tempo reale. Questo è un ottimo modo per eseguire rapidamente il debug dell'app senza compilare e distribuire un progetto completo. Lo sguardo fisso, il movimento, la voce e l'input di mapping spaziale vengono inviati dal HoloLens 2 al PC, il rendering del contenuto viene eseguito in una visualizzazione immersiva virtuale usando le maggiori risorse di sistema del PC e i fotogrammi sottoposti a rendering vengono quindi inviati al HoloLens 2. Holographic Remoting è disponibile anche per l'Windows Mixed Reality visori VR immersive.

Aggiungi Holographic Remoting all'app desktop o UWP tramite un pacchetto NuGet e la connessione viene stabilita usando il Wi-Fi standard. È necessario codice aggiuntivo che gestisce la connessione ed esegue il rendering in una visualizzazione immersiva. Una tipica connessione remota avrà fino a 50 ms di latenza. Il dispositivo visualizza il contenuto trasmesso tramite un'app "lettore" in grado di segnalare la latenza in tempo reale.

Gli sviluppatori Unity possono anche usare Holographic Remoting eseguendo l'app nell'editor di Unity in modalità play.

## <a name="see-also"></a>Vedere anche
* [Holographic Remoting Player](holographic-remoting-player.md)
* [Scrittura di un'app remota Holographic Remoting Windows Mixed Reality API](holographic-remoting-create-remote-wmr.md)
* [Scrittura di un'app remota Holographic Remoting con le API OpenXR](holographic-remoting-create-remote-openxr.md)
* [Esercitazione: Introduzione a Holographic Remoting per PC](../unity/tutorials/mr-learning-pc-holographic-remoting-01.md)
* [Esercitazione: Creazione di un'applicazione per PC Holographic Remoting](../unity/tutorials/mr-learning-pc-holographic-remoting-02.md)

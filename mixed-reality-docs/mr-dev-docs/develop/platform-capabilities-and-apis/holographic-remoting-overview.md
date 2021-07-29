---
title: Panoramica della comunicazione remota olografica
description: Informazioni su Holographic Remoting e su come può trarre vantaggio dal processo di sviluppo.
author: hferrone
ms.author: v-vtieto
ms.date: 07/26/2021
ms.topic: article
keywords: openxr, unity, hololens, hololens 2, realtà mista, MRTK, mixed reality Toolkit, realtà aumentata, realtà virtuale, visori di realtà mista, apprendimento, esercitazione, introduzione, comunicazione remota olografica, desktop, anteprima
ms.openlocfilehash: 6eb3b9e9fe8811ab4666ef1beda0e48668bedbe6
ms.sourcegitcommit: 9831b89a1641ba1b5df14419ee2a4f29d3fa2d64
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/29/2021
ms.locfileid: "114757408"
---
# <a name="holographic-remoting-overview"></a>Panoramica della comunicazione remota olografica

Quando si aggiunge il supporto per il rendering holografico all'app o al gioco per PC, consente all'app di trasmettere contenuto olografico HoloLens 2 in tempo reale. Questo è un ottimo modo per eseguire rapidamente il debug dell'app senza compilare e distribuire un progetto completo. Lo sguardo, il movimento, la voce e l'input di mapping spaziale vengono inviati dal HoloLens 2 al PC, il rendering del contenuto viene eseguito in una visualizzazione virtuale immersiva usando le maggiori risorse di sistema del PC e i fotogrammi sottoposti a rendering vengono quindi inviati nuovamente al HoloLens 2. Holographic Remoting è disponibile anche per Windows Mixed Reality visori immersive.

Si aggiunge Holographic Remoting all'app desktop o UWP tramite un pacchetto NuGet e la connessione viene stabilita usando il Wi-Fi standard. È necessario codice aggiuntivo che gestisce la connessione ed esegue il rendering in una visualizzazione immersiva. Una connessione remota tipica avrà fino a 50 ms di latenza. Il dispositivo visualizza il contenuto trasmesso in streaming usando un'app "lettore" in grado di segnalare la latenza in tempo reale.

Gli sviluppatori di Unity possono anche usare Holographic Remoting eseguendo l'app nell'editor unity in modalità play.

## <a name="see-also"></a>Vedere anche
* [Holographic Remoting Player](holographic-remoting-player.md)
* [Scrittura di un'app remota Holographic Remoting Windows Mixed Reality API](holographic-remoting-create-remote-wmr.md)
* [Scrittura di un'app remota Holographic Remoting con API OpenXR](holographic-remoting-create-remote-openxr.md)
* [Esercitazione: Introduzione a PC Holographic Remoting](../unity/tutorials/mr-learning-pc-holographic-remoting-01.md)
* [Esercitazione: Creazione di un'applicazione per PC Holographic Remoting](../unity/tutorials/mr-learning-pc-holographic-remoting-02.md)

---
title: Ancoraggi nello spazio condivisi in DirectX
description: Informazioni su come sincronizzare due HoloLens condividendo ancoraggi nello stato locale e di Azure nelle applicazioni DirectX.
author: thetuvix
ms.author: alexturn
ms.date: 08/04/2020
ms.topic: article
keywords: HoloLens, sincronizzazione, ancoraggio nello spaziale, trasferimento, multiplayer, visualizzazione, scenario, procedura dettagliata, codice di esempio, Azure, Ancoraggi nello stato di Azure, ASA
ms.openlocfilehash: df78d9e2477fe377d61d2f2c13fc35e0a25b0b2cc37eeb883a69d2041fe42f9b
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115193545"
---
# <a name="shared-experiences-in-directx"></a>Esperienze condivise in DirectX

> [!NOTE]
> Questo articolo è correlato alle API native WinRT legacy.  Per i nuovi progetti di app native, è consigliabile usare **[l'API OpenXR](../native/openxr-getting-started.md)**.

Un'esperienza condivisa è quella in cui più utenti con il proprio dispositivo HoloLens, iOS o Android, visualizzano e interagiscono collettivamente con lo stesso ologramma. L'ologramma viene posizionato in un punto fisso nello spazio usando la condivisione degli ancoraggi nello spazio.

## <a name="azure-spatial-anchors"></a>Ancoraggi nello spazio di Azure

È possibile usare <a href="/azure/spatial-anchors/overview" target="_blank">Ancoraggi nello</a> stato di Azure per creare ancoraggi nello stato durevoli supportati dal cloud, che l'app può quindi individuare in più dispositivi HoloLens, iOS e Android.  Condividendo un ancoraggio nello spazio comune tra più dispositivi, ogni utente può visualizzare il rendering del contenuto relativo a tale ancoraggio nella stessa posizione fisica.  Ciò rende possibili esperienze condivise in tempo reale.

È anche possibile usare <a href="/azure/spatial-anchors/overview" target="_blank">Ancoraggi nello stato di Azure</a> per la persistenza asincrona degli ologrammi nei dispositivi HoloLens, iOS e Android.  Condividendo un ancoraggio nello spaziale cloud durevole, più dispositivi possono osservare lo stesso ologramma persistente nel tempo, anche se tali dispositivi non sono presenti contemporaneamente.

Per iniziare a creare esperienze condivise nell'app HoloLens, provare la guida introduttiva di Ancoraggi nello <a href="/azure/spatial-anchors/quickstarts/get-started-hololens" target="_blank">spazio di Azure HoloLens di 5 minuti.</a>

Quando si è in esecuzione con Ancoraggi nello spazio di Azure, è possibile creare e individuare <a href="/azure/spatial-anchors/concepts/create-locate-anchors-cpp-winrt" target="_blank">ancoraggi in HoloLens</a>.  Sono disponibili procedure dettagliate anche per Android e <a href="/azure/spatial-anchors/create-locate-anchors-overview" target="_blank">iOS,</a> che consentono di condividere gli stessi ancoraggi in tutti i dispositivi.

## <a name="local-anchor-transfers"></a>Trasferimenti di ancoraggi locali

Nei casi in cui non è possibile usare Ancoraggi nello stato di [Azure,](../../out-of-scope/local-anchor-transfers-in-directx.md) i trasferimenti di ancoraggi locali consentono a un dispositivo HoloLens di esportare un ancoraggio da importare da un secondo HoloLens dispositivo.  Questo approccio offre un richiamo degli ancoraggi meno affidabile rispetto ad Ancoraggi nello spazio di Azure e i dispositivi iOS e Android non sono supportati da questo approccio.

## <a name="see-also"></a>Vedi anche

* [Esperienze condivise nella realtà mista](shared-experiences-in-mixed-reality.md)
* <a href="/azure/spatial-anchors" target="_blank">Ancoraggi nello spazio di Azure</a>
* <a href="/cpp/api/spatial-anchors/winrt/" target="_blank">Azure Spatial Anchors SDK per HoloLens</a>
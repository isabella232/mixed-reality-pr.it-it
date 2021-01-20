---
title: Ancoraggi nello spazio condivisi in DirectX
description: Informazioni su come sincronizzare due dispositivi HoloLens condividendo gli ancoraggi locali e spaziali di Azure nelle applicazioni DirectX.
author: thetuvix
ms.author: alexturn
ms.date: 08/04/2020
ms.topic: article
keywords: HoloLens, Synchronize, ancoraggio spaziale, trasferimento, multiplayer, visualizzazione, scenario, procedura dettagliata, codice di esempio, Azure, ancoraggi spaziali di Azure, ASA
ms.openlocfilehash: cf823809d1f6b9bf4bc44a6aa1e8f0e16fd76a16
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/20/2021
ms.locfileid: "98583107"
---
# <a name="shared-experiences-in-directx"></a>Esperienze condivise in DirectX

> [!NOTE]
> Questo articolo si riferisce alle API native di WinRT legacy.  Per i nuovi progetti di app native, è consigliabile usare l' **[API OpenXR](../native/openxr-getting-started.md)**.

Un'esperienza condivisa è quella in cui più utenti con il proprio dispositivo HoloLens, iOS o Android, collettivamente visualizzano e interagiscono con lo stesso ologramma. L'ologramma è posizionato in un punto fisso nello spazio usando la condivisione di ancoraggio spaziale.

## <a name="azure-spatial-anchors"></a>Ancoraggi nello spazio di Azure

È possibile usare gli <a href="/azure/spatial-anchors/overview" target="_blank">ancoraggi spaziali di Azure</a> per creare ancoraggi spaziali durevoli basati sul cloud, che possono essere individuati dall'app su più dispositivi HoloLens, iOS e Android.  Condividendo un ancoraggio spaziale comune tra più dispositivi, ogni utente può visualizzare il contenuto di cui è stato eseguito il rendering relativo a tale ancoraggio nella stessa posizione fisica.  Ciò rende possibili esperienze condivise in tempo reale.

È anche possibile usare gli <a href="/azure/spatial-anchors/overview" target="_blank">ancoraggi spaziali di Azure</a> per la persistenza ologramma asincrona nei dispositivi HoloLens, iOS e Android.  Grazie alla condivisione di un ancoraggio spaziale cloud durevole, più dispositivi possono osservare lo stesso ologramma persistente nel tempo, anche se i dispositivi non sono presenti contemporaneamente.

Per iniziare a creare esperienze condivise nell'app HoloLens, provare la <a href="/azure/spatial-anchors/quickstarts/get-started-hololens" target="_blank">Guida introduttiva di Azure Spatial Anchors HoloLens</a>di 5 minuti.

Una volta che si è in esecuzione con gli ancoraggi spaziali di Azure, è possibile <a href="/azure/spatial-anchors/concepts/create-locate-anchors-cpp-winrt" target="_blank">creare e individuare ancoraggi in HoloLens</a>.  Le procedure dettagliate sono disponibili anche per <a href="/azure/spatial-anchors/create-locate-anchors-overview" target="_blank">Android e iOS</a> , consentendo di condividere gli stessi ancoraggi in tutti i dispositivi.

## <a name="local-anchor-transfers"></a>Trasferimenti di ancoraggio locali

Nei casi in cui non è possibile usare gli ancoraggi spaziali di Azure, i [trasferimenti di ancoraggio locali](../../out-of-scope/local-anchor-transfers-in-directx.md) consentono a un dispositivo HoloLens di esportare un ancoraggio per l'importazione da parte di un secondo dispositivo HoloLens.  Questo approccio offre un richiamo di ancoraggio meno affidabile rispetto agli ancoraggi spaziali di Azure e i dispositivi iOS e Android non sono supportati da questo approccio.

## <a name="see-also"></a>Vedere anche

* [Esperienze condivise nella realtà mista](shared-experiences-in-mixed-reality.md)
* <a href="/azure/spatial-anchors" target="_blank">Ancoraggi nello spazio di Azure</a>
* <a href="/cpp/api/spatial-anchors/winrt/" target="_blank">Azure Spatial Anchors SDK per HoloLens</a>
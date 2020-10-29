---
title: Ancoraggi nello spazio condivisi in DirectX
description: Viene illustrato come sincronizzare due dispositivi HoloLens condividendo ancoraggi spaziali.
author: thetuvix
ms.author: alexturn
ms.date: 08/04/2020
ms.topic: article
keywords: HoloLens, Synchronize, ancoraggio spaziale, trasferimento, multiplayer, visualizzazione, scenario, procedura dettagliata, codice di esempio, Azure, ancoraggi spaziali di Azure, ASA
ms.openlocfilehash: 2d6485e46a9802e1ee7e5adc12d6e0d026c79ae9
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/03/2020
ms.locfileid: "91684909"
---
# <a name="shared-experiences-in-directx"></a>Esperienze condivise in DirectX

> [!NOTE]
> Questo articolo si riferisce alle API native di WinRT legacy.  Per i nuovi progetti di app native, è consigliabile usare l' **[API OpenXR](../native/openxr-getting-started.md)** .

Un'esperienza condivisa è quella in cui più utenti, ognuno con il proprio dispositivo HoloLens, iOS o Android, visualizzano collettivamente e interagiscono con lo stesso ologramma posizionato in un punto fisso nello spazio. Questa operazione viene eseguita tramite la condivisione di ancoraggio spaziale.

## <a name="azure-spatial-anchors"></a>Ancoraggi nello spazio di Azure

È possibile usare gli <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">ancoraggi spaziali di Azure</a> per creare ancoraggi spaziali durevoli basati sul cloud, che possono essere individuati dall'app su più dispositivi HoloLens, iOS e Android.  Condividendo un ancoraggio spaziale comune tra più dispositivi, ogni utente può visualizzare il contenuto di cui è stato eseguito il rendering relativo a tale ancoraggio nella stessa posizione fisica.  Ciò rende possibili esperienze condivise in tempo reale.

Puoi usare <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Ancoraggi nello spazio di Azure</a> anche per la persistenza asincrona degli ologrammi su dispositivi HoloLens, iOS e Android.  Condividendo un ancoraggio durevole nello spazio del cloud, più dispositivi possono osservare nel tempo lo stesso ologramma salvato in modo permanente, anche se tali dispositivi non sono presenti insieme contemporaneamente.

Per iniziare a creare esperienze condivise nell'app HoloLens, provare la <a href="https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-hololens" target="_blank">Guida introduttiva di Azure Spatial Anchors HoloLens</a>di 5 minuti.

Una volta che si è in esecuzione con gli ancoraggi spaziali di Azure, è possibile <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-cpp-winrt" target="_blank">creare e individuare ancoraggi in HoloLens</a>.  Le procedure dettagliate sono disponibili anche per <a href="https://docs.microsoft.com/azure/spatial-anchors/create-locate-anchors-overview" target="_blank">Android e iOS</a> , consentendo di condividere gli stessi ancoraggi in tutti i dispositivi.

## <a name="local-anchor-transfers"></a>Trasferimenti di ancoraggio locali

Nei casi in cui non è possibile usare gli ancoraggi spaziali di Azure, i [trasferimenti di ancoraggio locali](../../out-of-scope/local-anchor-transfers-in-directx.md) consentono a un dispositivo HoloLens di esportare un ancoraggio per l'importazione da parte di un secondo dispositivo HoloLens.  Si noti che questo approccio offre un richiamo di ancoraggio meno affidabile rispetto agli ancoraggi spaziali di Azure e i dispositivi iOS e Android non sono supportati da questo approccio.

## <a name="see-also"></a>Vedere anche
* [Esperienze condivise nella realtà mista](shared-experiences-in-mixed-reality.md)
* <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Ancoraggi nello spazio di Azure</a>
* <a href="https://docs.microsoft.com/cpp/api/spatial-anchors/winrt/" target="_blank">Azure Spatial Anchors SDK per HoloLens</a>
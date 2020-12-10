---
title: Esperienze condivise in Unity
description: Condividere gli stessi ologrammi tra più utenti in un'applicazione Unity.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: Condivisione, ancoraggio, WorldAnchor, MR sharing 250, WorldAnchorTransferBatch, SpatialPerception, Azure, ancoraggi spaziali di Azure, ASA, auricolare realtà mista, auricolare di realtà mista di Windows, auricolare della realtà virtuale
ms.openlocfilehash: 46588f84c39a48e22147d0fc246ceb8d5ee7c47d
ms.sourcegitcommit: 87b54c75044f433cfadda68ca71c1165608e2f4b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/10/2020
ms.locfileid: "97010091"
---
# <a name="shared-experiences-in-unity"></a>Esperienze condivise in Unity

Un'esperienza condivisa consente a più utenti, ognuno con il proprio dispositivo HoloLens, iOS o Android, di visualizzare e interagire collettivamente con lo stesso ologramma. Gli ologrammi vengono posizionati in un punto fisso nello spazio attraverso la condivisione di ancoraggio spaziale.

## <a name="azure-spatial-anchors"></a>Ancoraggi nello spazio di Azure

Gli <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">ancoraggi spaziali di Azure</a>creano ancoraggi spaziali durevoli basati sul cloud, che possono essere individuati dall'app su più dispositivi HoloLens, iOS e Android.  Condividendo un ancoraggio spaziale comune tra più dispositivi, ogni utente può visualizzare il contenuto di cui è stato eseguito il rendering relativo a tale ancoraggio nella stessa posizione fisica. 

È anche possibile usare gli <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">ancoraggi spaziali di Azure</a> per la persistenza ologramma asincrona nei dispositivi HoloLens, iOS e Android.  Grazie alla condivisione di un ancoraggio spaziale cloud durevole, più dispositivi possono osservare lo stesso ologramma persistente nel tempo, anche se i dispositivi non sono presenti contemporaneamente.

Per iniziare a creare esperienze condivise in Unity, provare le <a href="https://docs.microsoft.com/azure/spatial-anchors/unity-overview" target="_blank">guide introduttive Unity Anchors di Azure</a>di 5 minuti.

Una volta configurati gli ancoraggi spaziali di Azure, è possibile <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">creare e individuare ancoraggi in Unity</a>.

## <a name="local-anchor-transfers"></a>Trasferimenti di ancoraggio locali

Nei casi in cui non è possibile usare gli ancoraggi spaziali di Azure, i [trasferimenti di ancoraggio locali](../../out-of-scope/local-anchor-transfers-in-unity.md) consentono a un dispositivo HoloLens di esportare un ancoraggio in modo che un secondo HoloLens possa importarlo.  Questo approccio non è supportato nei dispositivi iOS e Android e fornisce un richiamo di ancoraggio meno affidabile rispetto agli ancoraggi spaziali di Azure.

## <a name="next-development-checkpoint"></a>Successivo checkpoint di sviluppo

Se si sta seguendo il percorso di sviluppo di Unity, è possibile esplorare le funzionalità e le API della piattaforma per la realtà mista. Da qui è possibile passare alla sezione successiva:

> [!div class="nextstepaction"]
> [Fotocamera individuabile](locatable-camera-in-unity.md)

In alternativa, passare direttamente alla distribuzione dell'app in un dispositivo o emulatore:

> [!div class="nextstepaction"]
> [Eseguire la distribuzione in HoloLens o in modalità mista di Windows per la realtà mista](../platform-capabilities-and-apis/using-visual-studio.md)

È sempre possibile tornare ai [checkpoint per lo sviluppo con Unity](unity-development-overview.md#3-platform-capabilities-and-apis) in qualsiasi momento.

## <a name="see-also"></a>Vedere anche
* [Esperienze condivise nella realtà mista](../platform-capabilities-and-apis/shared-experiences-in-mixed-reality.md)
* <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Ancoraggi nello spazio di Azure</a>
* <a href="https://docs.microsoft.com/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Azure Spatial Anchors SDK per Unity</a>

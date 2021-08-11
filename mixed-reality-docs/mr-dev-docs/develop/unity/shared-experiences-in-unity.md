---
title: Esperienze condivise in Unity
description: Informazioni su come condividere gli stessi ologrammi tra più utenti in un'applicazione Unity con Ancoraggi nello spazio di Azure.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: Sharing, Anchor, WorldAnchor, MR Sharing 250, WorldAnchorTransferBatch, SpatialPerception, Azure, Ancoraggi nello spazio di Azure, ASA, visore per realtà mista, visore windows mixed reality, visore per realtà virtuale
ms.openlocfilehash: b9fdd09740dc6197c46a2d017f61e97898f213cd44bb504cbbf306f6a7ae21ec
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115195923"
---
# <a name="shared-experiences-in-unity"></a>Esperienze condivise in Unity

Un'esperienza condivisa consente a più utenti, ognuno con il proprio dispositivo HoloLens, iOS o Android, di visualizzare e interagire collettivamente con lo stesso ologramma. Ologrammi sono posizionati in un punto fisso nello spazio tramite la condivisione dell'ancoraggio spaziale.

## <a name="azure-spatial-anchors"></a>Ancoraggi nello spazio di Azure

<a href="/azure/spatial-anchors/overview" target="_blank">Ancoraggi nello stato di Azure</a> creano ancoraggi spaziali durevoli supportati dal cloud, che l'app può quindi individuare in più dispositivi HoloLens, iOS e Android.  Condividendo un ancoraggio spaziale comune tra più dispositivi, ogni utente può visualizzare il contenuto sottoposto a rendering rispetto a tale ancoraggio nella stessa posizione fisica. 

È anche possibile usare <a href="/azure/spatial-anchors/overview" target="_blank">Ancoraggi nello stato di Azure</a> per la persistenza ologramma asincrona HoloLens dispositivi iOS e Android.  Condividendo un ancoraggio spaziale cloud durevole, più dispositivi possono osservare lo stesso ologramma persistente nel tempo, anche se tali dispositivi non sono presenti contemporaneamente.

Per iniziare a creare esperienze condivise in Unity, provare le guide introduttive di <a href="/azure/spatial-anchors/unity-overview" target="_blank">Azure Spatial Anchors Unity di</a>5 minuti.

Dopo aver configurato Ancoraggi nello spazio di Azure, è possibile <a href="/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">creare e individuare ancoraggi in Unity.</a>

## <a name="local-anchor-transfers"></a>Trasferimenti di ancoraggio locali

Nei casi in cui non è possibile usare Ancoraggi nello stato di [Azure,](../../out-of-scope/local-anchor-transfers-in-unity.md) i trasferimenti di ancoraggio locali consentono a un dispositivo HoloLens di esportare un ancoraggio in modo che un secondo HoloLens possa importarlo.  Questo approccio non è supportato nei dispositivi iOS e Android e offre un richiamo dell'ancoraggio meno affidabile rispetto ad Ancoraggi nello spazio di Azure.

## <a name="next-development-checkpoint"></a>Successivo checkpoint di sviluppo

Se si sta seguendo il percorso di sviluppo di Unity che è stato strutturato, si stanno esplorando le API e le funzionalità della piattaforma di realtà mista. Da qui è possibile passare alla sezione successiva:

> [!div class="nextstepaction"]
> [Fotocamera individuabile](locatable-camera-in-unity.md)

In alternativa, passare direttamente alla distribuzione dell'app in un dispositivo o emulatore:

> [!div class="nextstepaction"]
> [Distribuire in HoloLens o Windows Mixed Reality visori immersive](../platform-capabilities-and-apis/using-visual-studio.md)

È sempre possibile tornare ai [checkpoint per lo sviluppo con Unity](unity-development-overview.md#3-advanced-features) in qualsiasi momento.

## <a name="see-also"></a>Vedere anche
* [Esperienze condivise nella realtà mista](../platform-capabilities-and-apis/shared-experiences-in-mixed-reality.md)
* <a href="/azure/spatial-anchors" target="_blank">Ancoraggi nello spazio di Azure</a>
* <a href="/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Azure Spatial Anchors SDK per Unity</a>
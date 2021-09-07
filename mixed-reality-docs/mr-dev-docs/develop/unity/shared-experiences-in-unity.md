---
title: Esperienze condivise in Unity
description: Informazioni su come condividere gli stessi ologrammi tra più utenti in un'applicazione Unity con Ancoraggi nello spazio di Azure.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: Sharing, Anchor, WorldAnchor, MR Sharing 250, WorldAnchorTransferBatch, SpatialPerception, Azure, Ancoraggi nello spazio di Azure, ASA, visore VR di realtà mista, visore VR windows mixed reality, visore VR di realtà virtuale
ms.openlocfilehash: f7725c8282d1b5a93d555ac0f55ee936b910ff6c
ms.sourcegitcommit: 6f3b3aa31cc3acefba5fa3ac3ba579d9868a4fe4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/31/2021
ms.locfileid: "123244181"
---
# <a name="shared-experiences-in-unity"></a>Esperienze condivise in Unity

Un'esperienza condivisa consente a più utenti, ognuno con il proprio dispositivo HoloLens, iOS o Android, di visualizzare e interagire collettivamente con lo stesso ologramma. Ologrammi vengono posizionati in un punto fisso nello spazio tramite la condivisione degli ancoraggi nello spazio.

## <a name="azure-spatial-anchors"></a>Ancoraggi nello spazio di Azure

### <a name="automated-with-world-locking-tools"></a>Automazione con gli strumenti di blocco del mondo

Come per gli ancoraggi locali, gli strumenti di blocco del mondo possono usare un gruppo di Ancoraggi nello spazio di Azure per bloccare interi spazi delle coordinate rispetto al mondo fisico, anziché usare singoli ancoraggi per bloccare singoli oggetti. Il blocco a livello mondiale dell'intero spazio non solo offre un ambiente più conducente a un layout preciso, ma è anche più efficiente sia in fase di sviluppo che in risorse di runtime.

Per altre informazioni ed esempi sull'uso di Ancoraggi nello spazio di Azure per condividere sistemi di coordinate tra dispositivi HoloLens, Android e iOS, nonché per rendere persistenti gli spazi tra le sessioni, vedere la documentazione degli strumenti di blocco del mondo [.](https://microsoft.github.io/MixedReality-WorldLockingTools-Unity/DocGen/Documentation/HowTos/WLT_ASA.html)

### <a name="manual-configuration-of-azure-spatial-anchors"></a>Configurazione manuale di Ancoraggi nello stato di Azure

<a href="/azure/spatial-anchors/overview" target="_blank">Ancoraggi nello stato di Azure</a> crea ancoraggi nello stato durevoli supportati dal cloud che l'app può individuare in più dispositivi HoloLens, iOS e Android.  Condividendo un ancoraggio nello spazio comune tra più dispositivi, ogni utente può visualizzare il rendering del contenuto relativo a tale ancoraggio nella stessa posizione fisica.

È anche possibile usare <a href="/azure/spatial-anchors/overview" target="_blank">Ancoraggi nello stato di Azure</a> per la persistenza asincrona degli ologrammi nei dispositivi HoloLens, iOS e Android.  Condividendo un ancoraggio nello spaziale cloud durevole, più dispositivi possono osservare lo stesso ologramma persistente nel tempo, anche se tali dispositivi non sono presenti contemporaneamente.

Per iniziare a creare esperienze condivise in Unity, provare le guide introduttive di Unity per Ancoraggi nello spazio di Azure di 5 <a href="/azure/spatial-anchors/unity-overview" target="_blank">minuti.</a>

Dopo aver configurato Ancoraggi nello spazio di Azure, è possibile <a href="/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">creare e individuare gli ancoraggi in Unity.</a>

## <a name="local-anchor-transfers"></a>Trasferimenti di ancoraggi locali

Nelle situazioni in cui non è possibile usare Ancoraggi nello HoloLens di [Azure,](../../out-of-scope/local-anchor-transfers-in-unity.md) i trasferimenti di ancoraggi locali consentono a un dispositivo HoloLens di esportare un ancoraggio in modo che un secondo HoloLens possa importarlo.  Questo approccio non è supportato nei dispositivi iOS e Android e offre un richiamo degli ancoraggi meno affidabile rispetto ad Ancoraggi nello spazio di Azure.

## <a name="next-development-checkpoint"></a>Successivo checkpoint di sviluppo

Se stai seguendo il percorso di sviluppo di Unity che abbiamo stabilito, stai esplorando le API e le funzionalità della piattaforma realtà mista. Da qui è possibile passare alla sezione successiva:

> [!div class="nextstepaction"]
> [Fotocamera individuabile](locatable-camera-in-unity.md)

In alternativa, passare direttamente alla distribuzione dell'app in un dispositivo o emulatore:

> [!div class="nextstepaction"]
> [Eseguire la distribuzione HoloLens o Windows Mixed Reality visori VR immersive](../platform-capabilities-and-apis/using-visual-studio.md)

È sempre possibile tornare ai [checkpoint per lo sviluppo con Unity](unity-development-overview.md#3-advanced-features) in qualsiasi momento.

## <a name="see-also"></a>Vedere anche
* [Esperienze condivise nella realtà mista](../platform-capabilities-and-apis/shared-experiences-in-mixed-reality.md)
* <a href="/azure/spatial-anchors" target="_blank">Ancoraggi nello spazio di Azure</a>
* <a href="/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Azure Spatial Anchors SDK per Unity</a>
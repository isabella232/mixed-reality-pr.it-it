---
title: Introduzione alle esercitazioni sulle funzionalità multiutente
description: In questo corso viene illustrato come implementare esperienze multiutente condivise in un'applicazione HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens, funzionalità multiutente, Photon, MRTK, mixed reality toolkit, UWP, ancoraggi nello spazio di Azure
ms.localizationpriority: high
ms.openlocfilehash: 97778dfb002a7313e08a65a20abd7c3bd6d046a4
ms.sourcegitcommit: 7a8fa3257a13635ddad77d963e49440f62c19774
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/04/2021
ms.locfileid: "101883316"
---
# <a name="1-introduction-to-the-multi-user-capabilities-tutorials"></a>1. Introduzione alle esercitazioni sulle funzionalità multiutente

Esercitazioni sulle funzionalità multiutente Con questa serie di esercitazioni si apprenderanno le nozioni di base per la creazione di un'esperienza multiutente usando <a href="https://www.photonengine.com/PUN" target="_blank">Photon Unity Networking</a> (PUN). PUN è una delle diverse opzioni di rete disponibili per gli sviluppatori di realtà mista per creare esperienze condivise.

Esercitazioni di questa serie:

* [Configurazione di Photon Unity Networking](mr-learning-sharing-02.md)
* [Connessione di più utenti](mr-learning-sharing-03.md)
* [Condivisione dei movimenti di oggetti con più utenti](mr-learning-sharing-04.md)
* [Integrazione di Ancoraggi nello spazio di Azure in un'esperienza condivisa](mr-learning-sharing-05.md)

## <a name="objectives"></a>Obiettivi

* Imparare a creare un'app PUN e a connettere il progetto Unity all'app
* Imparare a connettere più utenti in un'esperienza condivisa
* Imparare a condividere i movimenti degli oggetti con altri utenti
* Imparare a ottenere l'allineamento spaziale tra più dispositivi

## <a name="prerequisites"></a>Prerequisiti

* Un computer Windows 10 configurato in cui siano [installati gli strumenti](../../install-the-tools.md) corretti
* Windows 10 SDK 10.0.18362.0 o versioni successive
* Un dispositivo HoloLens 2 [configurato per lo sviluppo](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)
* <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> con Unity 2019 LTS installato e il modulo di supporto per la compilazione UWP (Universal Windows Platform) aggiunto
* Completamento della sezione [Creare una risorsa di Ancoraggi nello spazio](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource) dell'esercitazione [Avvio rapido: Creare un'app HoloLens in Unity che usa Ancoraggi nello spazio di Azure](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens)
* Completamento della serie di [esercitazioni introduttive](mr-learning-base-01.md) o di esperienze di base precedenti con Unity e MRTK
* Completamento della serie di [esercitazioni sugli Ancoraggi nello spazio di Azure](mr-learning-asa-01.md) o di esperienze precedenti sulla creazione di un account di Ancoraggi nello spazio di Azure
* Se è prevista la distribuzione in Android e HoloLens
  * Un dispositivo Android <a href="https://developer.android.com/studio/debug/dev-options" target="_blank">con le opzioni di sviluppo abilitate</a> e <a href="https://developers.google.com/ar/discover/supported-devices" target="_blank">supportato da ARCore</a> con connessione USB a un computer con Windows o macOS
  * <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Hub Unity</a> con unity 2019 LTS installato e aggiunta del modulo di supporto Build Android
* Se è prevista la distribuzione in iOS e HoloLens
  * Un computer macOS con la versione più recente di <a href="https://geo.itunes.apple.com/us/app/xcode/id497799835?mt=12" target="_blank">Xcode</a> e <a href="https://cocoapods.org" target="_blank">CocoaPods</a> installata
  * Un dispositivo iOS <a href="https://developer.apple.com/documentation/arkit/verifying_device_support_and_user_permission" target="_blank">compatibile con ARKit</a> con connessione USB al computer macOS
  * <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Hub Unity</a> con unity 2019 LTS installato e il modulo di supporto Build iOS aggiunto

> [!CAUTION]
> La versione consigliata del Toolkit per la realtà mista per questa serie di esercitazioni è MRTK 2,6.

> [!CAUTION]
> La versione consigliata di Unity per questa serie di esercitazioni è Unity 2019 LTS, che sostituisce tutti i requisiti di versione di Unity indicati nei prerequisiti collegati in precedenza.

> [!div class="nextstepaction"]
> [Esercitazione successiva: 2. Configurazione di Photon Unity Networking](mr-learning-sharing-02.md)

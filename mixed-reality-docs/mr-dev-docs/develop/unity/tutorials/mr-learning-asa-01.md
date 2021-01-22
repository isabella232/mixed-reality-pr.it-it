---
title: Introduzione alle esercitazioni su Ancoraggi nello spazio di Azure
description: In questo corso viene illustrato come implementare Ancoraggi nello spazio di Azure in un'applicazione di realtà mista.
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens, MRTK, mixed reality toolkit, UWP, ancoraggi nello spazio di Azure, ios, android, Windows 10, ARCore, macOS, Android Build Support, ARKit
ms.localizationpriority: high
ms.openlocfilehash: 9529b12968c5cbc985f4af8eb0053d277eb00c03
ms.sourcegitcommit: 3dad2adfdb5bdb8100d8d864f7845e34a3ef912d
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/22/2021
ms.locfileid: "98699030"
---
# <a name="1-introduction-to-the-azure-spatial-anchors-tutorials"></a>1. Introduzione alle esercitazioni su Ancoraggi nello spazio di Azure

Esercitazioni su Ancoraggi nello spazio di Azure Con questa serie di esercitazioni si apprenderanno le nozioni di base di <a href="https://azure.microsoft.com/services/spatial-anchors" target="_blank">Ancoraggi nello spazio di Azure</a> (ASA) e le procedure per ancorare un'esperienza di realtà mista completa al mondo reale. Si apprenderà anche come distribuire il progetto in Android e iOS.

Esercitazioni di questa serie:

1. [Introduzione](mr-learning-asa-01.md) (l'esercitazione corrente)
2. [Introduzione ad Ancoraggi nello spazio di Azure](mr-learning-asa-02.md)
3. [Salvataggio, recupero e condivisione di Ancoraggi nello spazio di Azure](mr-learning-asa-03.md)
4. [Visualizzazione del feedback su Ancoraggi nello spazio di Azure](mr-learning-asa-04.md)
5. [Ancoraggi nello spazio di Azure per Android e iOS](mr-learning-asa-05.md)

## <a name="objectives"></a>Obiettivi

* Imparare a creare ancoraggi nello spazio e recuperarli da Azure
* Imparare a ottenere l'allineamento spaziale tra le sessioni dell'app
* Imparare a ottenere l'allineamento spaziale tra più dispositivi
* Imparare a preparare, creare e distribuire il progetto in Android e iOS

## <a name="prerequisites"></a>Prerequisiti

* Un computer Windows 10 configurato in cui siano [installati gli strumenti](../../install-the-tools.md) corretti
* Windows 10 SDK 10.0.18362.0 o versioni successive
* Un dispositivo HoloLens 2 [configurato per lo sviluppo](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)
* <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> con Unity 2019 LTS installato e il modulo di supporto per la compilazione UWP (Universal Windows Platform) aggiunto
* Completamento della sezione [Creare una risorsa di Ancoraggi nello spazio](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource) dell'esercitazione [Avvio rapido: Creare un'app HoloLens in Unity che usa Ancoraggi nello spazio di Azure](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens)
* Completamento della serie di [esercitazioni introduttive](mr-learning-base-01.md) o di esperienze di base precedenti con Unity e MRTK
* Se è prevista la distribuzione in Android e HoloLens
  * Un dispositivo Android <a href="https://developer.android.com/studio/debug/dev-options" target="_blank">con le opzioni di sviluppo abilitate</a> e <a href="https://developers.google.com/ar/discover/supported-devices" target="_blank">supportato da ARCore</a> con connessione USB a un computer con Windows o macOS
  * <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Hub Unity</a> con unity 2019 LTS installato e aggiunta del modulo di supporto Build Android
* Se è prevista la distribuzione in iOS e HoloLens
  * Un computer macOS con la versione più recente di <a href="https://geo.itunes.apple.com/us/app/xcode/id497799835?mt=12" target="_blank">Xcode</a> e <a href="https://cocoapods.org" target="_blank">CocoaPods</a> installata
  * Un dispositivo iOS <a href="https://developer.apple.com/documentation/arkit/verifying_device_support_and_user_permission" target="_blank">compatibile con ARKit</a> con connessione USB al computer macOS
  * <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Hub Unity</a> con unity 2019 LTS installato e il modulo di supporto Build iOS aggiunto

> [!CAUTION]
> La versione consigliata del Toolkit per la realtà mista per questa serie di esercitazioni è MRTK 2.5.1.

> [!CAUTION]
> La versione consigliata di Unity per questa serie di esercitazioni è Unity 2019 LTS, che sostituisce tutti i requisiti di versione di Unity indicati nei prerequisiti collegati in precedenza.

> [!div class="nextstepaction"]
> [Esercitazione successiva: 2. Introduzione ad Ancoraggi nello spazio di Azure](mr-learning-asa-02.md)

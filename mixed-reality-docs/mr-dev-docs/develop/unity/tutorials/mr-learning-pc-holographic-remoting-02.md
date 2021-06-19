---
title: Creare un'applicazione Holographic Remoting per PC
description: In questo corso viene illustrato come creare un'applicazione per PC per usare in remoto un'esperienza di realtà mista da PC a HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: realtà mista, unity, esercitazione, hololens, holographic remoting per PC, Visual Studio
ms.localizationpriority: high
ms.openlocfilehash: ca0efe13acac4408a05ab89eb98b508e9993c5a4
ms.sourcegitcommit: bdf4babd13e021f41fb04cdb3611bb759bd77537
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2021
ms.locfileid: "112392540"
---
# <a name="2-creating-a-holographic-remoting-pc-application"></a>2. Creazione di un'applicazione Holographic Remoting per PC

In questa esercitazione si apprenderà come creare un'app Holographic Remoting per PC e connettere HoloLens 2 in qualsiasi momento, offrendo un modo per visualizzare il contenuto 3D in realtà mista.

## <a name="objectives"></a>Obiettivi

* Configurare Unity per Holographic Remoting
* Imparare a compilare e distribuire l'applicazione con Visual Studio
* Sviluppare un'applicazione Holographic Remoting e connetterla a HoloLens

## <a name="configuring-the-capabilities"></a>Configurazione delle funzionalità

Nella finestra **Impostazioni progetto** espandere Impostazioni di pubblicazione **,** scorrere verso il basso fino alla sezione Funzionalità e selezionare la casella di controllo funzionalità visualizzata di seguito oltre alle funzionalità esistenti.

* Client e server Internet
* Client e server di rete privata

![abilitazione delle funzionalità](images/mrlearning-pc-holographic-remoting/tutorial2-section0-step1-1.png)

[!INCLUDE[](includes/configuring-scene-for-holographic-remoting.md)]

## <a name="build-your-application-to-pc"></a>Compilare l'applicazione nel PC

L'app Holographic Remoting è ora pronta per la compilazione nel PC. Attenersi ai passaggi seguenti e apportare queste modifiche per compilare l'applicazione nel PC.

[!INCLUDE[](includes/build-your-application-to-pc.md)]

## <a name="testing-holographic-remoting-remote-application"></a>Test di un'applicazione remota Holographic Remoting

Per connettere l'applicazione PC a HoloLens 2, seguire questa procedura:

### <a name="1-install-the-remoting-player-application-on-hololens-2-device"></a>1. Installare l'applicazione Remoting Player nel dispositivo HoloLens 2

* In HoloLens 2 visitare l'app dello Store e cercare "**Remoting Player**".
* Selezionare l'app **Remoting Player**.
* Toccare **Install** (Installa) per scaricare e installare l'app.

### <a name="2-connect-the-holographic-remoting-pc-app-to-the-remoting-player"></a>2. Connettere l'app del PC Holographic Remoting a Remoting Player

* Avviare **Remoting Player** in HoloLens.
* Prendere nota dell'**indirizzo IP** di HoloLens. Verrà visualizzato come ologramma da **Remoting Player** non appena viene avviato.
* Aprire l'applicazione Holographic Remoting per PC nel PC in uso.
* Una volta avviata l'applicazione, immettere l'**indirizzo IP** e fare clic sul pulsante **Connect** (Connetti) per connettersi.

## <a name="congratulations"></a>Lezione completata

In questa esercitazione si è appreso come creare un'app remota Holographic Remoting e connetterla a HoloLens 2 in qualsiasi momento, offrendo un modo per visualizzare il contenuto 3D in realtà mista. Dopo aver connesso HoloLens all'applicazione PC Holographic Remoting, si noterà che l'esperienza di realtà mista è in streaming nel dispositivo HoloLens 2.

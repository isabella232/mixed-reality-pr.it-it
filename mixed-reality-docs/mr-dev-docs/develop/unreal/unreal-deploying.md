---
title: Distribuire nel dispositivo in Unreal
description: Guida alla distribuzione di un dispositivo in Unreal a HoloLens 2
author: sw5813
ms.author: suwu
ms.date: 7/10/2020
ms.topic: article
keywords: Unreal Engine 4, UE4, HoloLens, HoloLens 2, realtà mista, distribuzione nel dispositivo, PC, documentazione
appliesto:
- HoloLens 2
ms.openlocfilehash: abd5e5c28ec5e66c4f73df8edf5e0ac0212d170a
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/03/2020
ms.locfileid: "91684789"
---
# <a name="deploy-to-device-in-unreal"></a>Distribuire nel dispositivo in Unreal

## <a name="overview"></a>Panoramica
Esistono due modi per distribuire un'applicazione Unreal in HoloLens 2:
* Direttamente dall'editor non reale
* Come pacchetto caricato tramite il portale del dispositivo

Per entrambe le opzioni è necessario configurare il HoloLens per l'uso del portale per lo sviluppo del [dispositivo](../platform-capabilities-and-apis/using-the-windows-device-portal.md) .

## <a name="deploying-to-device-from-the-unreal-editor"></a>Distribuzione nel dispositivo da un editor non reale

1. Fare clic sulla freccia a discesa accanto al pulsante **Avvia** . Inizialmente, l'opzione del dispositivo HoloLens sarà disabilitata.

![Opzioni menu a discesa Avvia](images/unreal/launch-dropdown.png)

2. Aprire il **Device Manager** . Si noti che il HoloLens non verrà visualizzato automaticamente nell'elenco dei dispositivi.

3. Espandere la sezione **aggiungere un dispositivo** non in elenco.

4. Selezionare **HoloLens** come **piattaforma** .

5. Immettere le informazioni sull'indirizzo IP e sulla porta dei dispositivi separati da due punti come identificatore del dispositivo. Ad esempio, "127.0.0.1:10080" (quando si è connessi tramite USB). Usare le credenziali del nome utente e della password del portale del dispositivo.

6. Premere **Aggiungi** e chiudere Gestione dispositivi.
    * In caso di errore, ad esempio un indirizzo errato, un nome utente o una password, verrà visualizzato un messaggio nel log di output.

![Aggiunta di un dispositivo non in elenco](images/unreal/add-unlisted-device.png)

7. Fare clic sulla freccia a discesa accanto al pulsante **Launch (avvia** ). questa volta dovrebbe essere visualizzato il dispositivo HoloLens appena aggiunto. Selezionare il dispositivo HoloLens da compilare e distribuire in HoloLens.

>[!NOTE]
>La compilazione per il dispositivo può comportare la ricompilazione degli shader (soprattutto alla prima esecuzione). questa operazione può richiedere alcuni minuti. Non lasciare che il dispositivo vada a dormire fino a quando l'app non è in esecuzione (potrebbe essere necessario investirla). In caso contrario, la compilazione dello shader non riuscirà.

## <a name="deploying-to-device-via-device-portal"></a>Distribuzione nel dispositivo tramite il portale del dispositivo

Per istruzioni dettagliate sulla creazione di [pacchetti e sulla distribuzione di un'app,](tutorials/unreal-uxt-ch6.md#packaging-and-deploying-the-app-via-device-portal) vedere l'ultima sezione del introduzione con la serie di esercitazioni Unreal.

## <a name="next-development-checkpoint"></a>Checkpoint di sviluppo successivo

Se si sta seguendo il percorso di checkpoint per lo sviluppo non reale, si è in fase di distribuzione. Da qui è possibile procedere con l'aggiunta di servizi avanzati:

> [!div class="nextstepaction"]
> [Servizi avanzati](unreal-development-overview.md#5-adding-services)

È sempre possibile tornare ai checkpoint di [sviluppo non reali](unreal-development-overview.md#4-deploying-to-a-device) in qualsiasi momento.

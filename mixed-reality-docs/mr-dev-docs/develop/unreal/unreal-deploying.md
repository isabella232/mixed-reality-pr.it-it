---
title: Distribuire nel dispositivo in Unreal
description: Informazioni su tutto ciò che è necessario sapere sulla distribuzione di app di realtà mista Unreal in HoloLens 2 usando l'editor o il portale del dispositivo.
author: sw5813
ms.author: suwu
ms.date: 12/9/2020
ms.topic: article
keywords: Unreal Engine 4, UE4, HoloLens, HoloLens 2, realtà mista, distribuzione su dispositivo, PC, documentazione, auricolare realtà mista, headset di realtà mista di Windows, auricolare della realtà virtuale
appliesto:
- HoloLens 2
ms.openlocfilehash: 24b2c013e1c9f25f54be9a6fefec8a86846c1746
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2021
ms.locfileid: "98009751"
---
# <a name="deploy-to-device-in-unreal"></a>Distribuire nel dispositivo in Unreal

Esistono due modi per distribuire un'applicazione Unreal in HoloLens 2:
* Direttamente dall'editor non reale
* Come pacchetto caricato tramite il portale del dispositivo

Per entrambe le opzioni è necessario configurare il HoloLens per l'uso del portale per lo sviluppo del [dispositivo](../platform-capabilities-and-apis/using-the-windows-device-portal.md) .

## <a name="deploying-to-device-from-the-unreal-editor"></a>Distribuzione nel dispositivo da un editor non reale

1. Selezionare la freccia a discesa accanto al pulsante **Avvia** . Inizialmente, l'opzione del dispositivo HoloLens sarà disabilitata.

![Opzioni menu a discesa Avvia](images/unreal/launch-dropdown.png)

2. Aprire il **Device Manager** e notare che il HoloLens non verrà visualizzato automaticamente nell'elenco dei dispositivi.

3. Espandere la sezione **aggiungere un dispositivo** non in elenco.

4. Selezionare **HoloLens** come **piattaforma**.

5. Immettere le informazioni sull'indirizzo IP e sulla porta dei dispositivi separati da due punti come identificatore del dispositivo. Ad esempio, "127.0.0.1:10080" (quando si è connessi tramite USB). Usare le credenziali del nome utente e della password del portale del dispositivo.

6. Premere **Aggiungi** e chiudere Gestione dispositivi.
    * Se si verifica un errore, ad esempio un indirizzo errato o le credenziali dell'utente, verrà stampato un messaggio nel log di output.

![Aggiunta di un dispositivo non in elenco](images/unreal/add-unlisted-device.png)

7. Selezionare di nuovo la freccia a discesa accanto al pulsante **Launch (avvia** ). questa volta dovrebbe essere visualizzato il dispositivo HoloLens appena aggiunto. Selezionare il dispositivo HoloLens da compilare e distribuire in HoloLens.

>[!NOTE]
>La compilazione per il dispositivo può comportare la ricompilazione degli shader (soprattutto alla prima esecuzione). questa operazione può richiedere alcuni minuti. Non lasciare che il dispositivo vada a dormire fino a quando l'app non è in esecuzione (potrebbe essere necessario investirla). In caso contrario, la compilazione dello shader non riuscirà.

## <a name="deploying-to-device-via-device-portal"></a>Distribuzione nel dispositivo tramite il portale del dispositivo

Per istruzioni dettagliate sulla creazione di pacchetti e sulla distribuzione di un'app, vedere la [serie di esercitazioni su Unreal](tutorials/unreal-uxt-ch6.md#packaging-and-deploying-the-app-via-device-portal).

## <a name="next-development-checkpoint"></a>Successivo checkpoint di sviluppo

Se si sta seguendo il percorso di sviluppo non reale, si è in fase di distribuzione. Da qui è possibile continuare ad aggiungere servizi avanzati:

> [!div class="nextstepaction"]
> [Servizi avanzati](unreal-development-overview.md#5-adding-services)

È sempre possibile tornare ai [checkpoint per lo sviluppo con Unreal](unreal-development-overview.md#4-streaming-and-deploying-to-a-device) in qualsiasi momento.

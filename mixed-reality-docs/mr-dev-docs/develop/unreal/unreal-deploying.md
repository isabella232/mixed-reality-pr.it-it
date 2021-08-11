---
title: Distribuire nel dispositivo in Unreal
description: Scopri tutto quello che c'è da sapere sulla distribuzione di app Unreal di realtà mista HoloLens 2 usando l'editor o il portale per dispositivi.
author: sw5813
ms.author: suwu
ms.date: 12/9/2020
ms.topic: article
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, realtà mista, distribuzione nel dispositivo, PC, documentazione, visore VR di realtà mista, visore VR windows mixed reality, visore VR di realtà virtuale
appliesto:
- HoloLens 2
ms.openlocfilehash: d6df3f9af21a0759c98306c28696d21eac7687b92d3cb74a9cd9948122cbcbcc
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115226643"
---
# <a name="deploy-to-device-in-unreal"></a>Distribuire nel dispositivo in Unreal

Esistono due modi per distribuire un'applicazione Unreal in HoloLens 2:
* Direttamente dall'editor Unreal
* Come pacchetto caricato tramite il portale di dispositivi

Per entrambe le opzioni è necessario configurare il HoloLens usare il portale [per dispositivi per](../platform-capabilities-and-apis/using-the-windows-device-portal.md) lo sviluppo.

## <a name="deploying-to-device-from-the-unreal-editor"></a>Distribuzione nel dispositivo dall'editor Unreal

1. Selezionare la freccia a discesa accanto al **pulsante** Avvia. Inizialmente, l'HoloLens del dispositivo verrà disattivata.

![Opzioni dell'elenco a discesa di avvio](images/unreal/launch-dropdown.png)

2. Aprire **Gestione dispositivi e** notare che il HoloLens non verrà visualizzato automaticamente nell'elenco dei dispositivi.

3. Espandere la **sezione Aggiungi un dispositivo non in** elenco.

4. Selezionare **HoloLens** come **Piattaforma.**

5. Immettere l'indirizzo IP e le informazioni sulla porta dei dispositivi separati da due punti come identificatore del dispositivo. Ad esempio, "127.0.0.1:10080" (se connesso tramite USB). Usare le credenziali Portale di dispositivi nome utente e password.

6. Fare **clic su** Aggiungi e chiudere Gestione dispositivi.
    * Se si verifica un errore, ad esempio un indirizzo errato o credenziali utente, verrà stampato un messaggio nel log di output.

![Aggiunta di un dispositivo non in elenco](images/unreal/add-unlisted-device.png)

7. Selezionare di nuovo la  freccia a discesa accanto al pulsante Avvia. Questa volta verrà visualizzato HoloLens dispositivo appena aggiunto. Selezionare il HoloLens da compilare e distribuire nel HoloLens.

>[!NOTE]
>La compilazione per il dispositivo può comportare la ricompilazione degli shader (in particolare alla prima esecuzione): questa operazione può richiedere del tempo. Non lasciare che il dispositivo venga in sospensione fino a quando l'app non è in esecuzione (potrebbe essere necessario indossarlo). In caso contrario, la compilazione dello shader avrà esito negativo.

## <a name="deploying-to-device-via-device-portal"></a>Distribuzione nel dispositivo tramite il portale di dispositivi

Per istruzioni dettagliate sulla creazione del pacchetto e sulla distribuzione di un'app, vedere la serie [di esercitazioni su Unreal.](tutorials/unreal-uxt-ch6.md#packaging-and-deploying-the-app-via-device-portal)

## <a name="next-development-checkpoint"></a>Successivo checkpoint di sviluppo

Se si sta seguendo il percorso di sviluppo di Unreal che è stato strutturato, ci si trova nella fase di distribuzione. Da qui è possibile continuare ad aggiungere servizi avanzati:

> [!div class="nextstepaction"]
> [Servizi avanzati](unreal-development-overview.md#5-adding-services)

È sempre possibile tornare ai [checkpoint per lo sviluppo con Unreal](unreal-development-overview.md#4-streaming-and-deploying-to-a-device) in qualsiasi momento.

---
title: Streaming in Unreal
description: Guida allo streaming in Unreal per HoloLens 2
author: sw5813
ms.author: suwu
ms.date: 7/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, realtà mista, streaming, PC, app holographic remoting, holographic remoting player, documentazione, visore VR realtà mista, visore VR di windows mixed reality, visore per realtà virtuale
appliesto:
- HoloLens
- HoloLens 2
ms.openlocfilehash: 9cbde33ce7238d704d4b24b4afbed9d8306d4e4d
ms.sourcegitcommit: 32cb81eee976e73cd661c2b347691c37865a60bc
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/04/2020
ms.locfileid: "96609332"
---
# <a name="streaming-in-unreal"></a>Streaming in Unreal

Lo streaming da un PC a HoloLens offre due vantaggi fondamentali: 
* Consente all'app di realtà mista di sfruttare la potenza di calcolo del PC. 
* Consente di accelerare l'iterazione dello sviluppo. 

Prima di tutto, devi scaricare [Holographic Remoting Player](../platform-capabilities-and-apis/holographic-remoting-player.md) nel dispositivo HoloLens. Holographic Remoting Player consente all'app di trasmettere in streaming direttamente al lettore remoto di HoloLens dalle origini seguenti:

* Editor Unreal Engine
* Un eseguibile Windows in pacchetto 

Durante lo streaming, hai accesso a quasi tutte le funzionalità di HoloLens che avresti a disposizione durante l'esecuzione di un'applicazione in un dispositivo. Questo include [tracciamento mano e articolazioni](unreal-hand-tracking.md) se si usa HoloLens 2, [mapping spaziale](unreal-spatial-mapping.md) e [ancoraggi nello spazio](unreal-spatial-anchors.md), ma esclude le funzionalità riportate in questo [elenco](../platform-capabilities-and-apis/holographic-remoting-troubleshooting.md). 

> [!NOTE]
> * La qualità dello streaming dipende in larga misura dalla potenza del segnale Wi-Fi.
> * Tutte le funzionalità vengono abilitate automaticamente per il lettore Holographic Remoting. Se si trova una funzionalità che richiede l'autorizzazione dell'utente (ad esempio, il tracciamento oculare) per il funzionamento sul flusso ma non durante l'esecuzione nel dispositivo, verificare di aver abilitato le funzionalità appropriate nelle impostazioni del progetto.

## <a name="device-support"></a>Supporto di dispositivi

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><strong>Origine</strong></td>
        <td><a href="https://docs.microsoft.com/hololens/hololens1-hardware"><strong>HoloLens 1a generazione</strong></a></td>
        <td><a href="https://www.microsoft.com/hololens/hardware"><strong>HoloLens 2</strong></a></td>
        <td><strong>Visori VR immersive</strong></td>
    </tr>
     <tr>
        <td>Editor Unreal</td>
        <td>✔️</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
    <tr>
        <td>Pacchetto Windows</td>
        <td>❌</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>

</table>

## <a name="streaming-from-the-unreal-editor"></a>Streaming dall'editor Unreal

In qualità di sviluppatore, si noterà che lo streaming dall'editor Unreal al dispositivo HoloLens offre vantaggi significativi in fase di test, soprattutto perché non è più necessario attendere che l'app venga compilata e distribuita prima di provare gli aggiornamenti.

È possibile trovare istruzioni dettagliate per lo [streaming dall'editor Unreal](tutorials/unreal-uxt-ch6.md#device-only-streaming) nella serie di esercitazioni.

## <a name="streaming-from-a-packaged-windows-executable"></a>Streaming da un eseguibile Windows in pacchetto

In Unreal 4.25.1 e versioni successive, è possibile trasmettere l'app in streaming a un dispositivo HoloLens 2 da un eseguibile Windows in pacchetto: 

1. Passa a **File > Package Project > Windows** (File > Crea pacchetto progetto > Windows) nel menu dell'editor. 
    * Scegliere una posizione in cui salvare il pacchetto e selezionare **Select Folder** (Seleziona cartella).

2. Terminata la creazione del pacchetto, apri **Holographic Remoting Player** in HoloLens 2 e prendi nota dell'indirizzo IP. 
3. Lascia aperto **Holographic Remoting Player** e usa il prompt della riga di comando per: 
    * accedere con cd alla directory locale in cui hai salvato il pacchetto.
    * Immettere il comando seguente: ```<App Name>.exe -vr -HoloLensRemoting=<IP Address>```

> [!NOTE]
> Dovrebbe essere usato automaticamente il nome dell'applicazione nelle impostazioni del progetto per creare il pacchetto di Windows. Se per qualche motivo sono diversi, usa il nome dell'eseguibile di Windows al prompt dei comandi.

Premi INVIO e inizierà lo streaming dell'applicazione.

## <a name="see-also"></a>Vedere anche

* [Cronologia delle versioni di Holographic Remoting](../platform-capabilities-and-apis/holographic-remoting-version-history.md)
* [Scrivere un'app lettore Holographic Remoting personalizzata](../platform-capabilities-and-apis/holographic-remoting-create-player.md)
* [Stabilire una connessione sicura con Holographic Remoting](../platform-capabilities-and-apis/holographic-remoting-secure-connection.md)

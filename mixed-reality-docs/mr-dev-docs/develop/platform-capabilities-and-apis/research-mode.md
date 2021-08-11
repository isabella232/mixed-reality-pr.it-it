---
title: Modalità ricerca di HoloLens
description: Usando la modalità di ricerca HoloLens, un'applicazione può accedere ai flussi chiave del sensore del dispositivo (profondità, rilevamento dell'ambiente e riflettività IR).
author: hferrone
ms.author: v-hferrone
ms.date: 07/31/2020
ms.topic: article
keywords: Modalità di ricerca, cv, rs4, visione computer, ricerca, HoloLens, HoloLens 2
ms.openlocfilehash: 57306307e4fd23870ae4cbcdb88773cfc858515f4d7ff0e27e26930bace54d65
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115193687"
---
# <a name="hololens-research-mode"></a>Modalità ricerca di HoloLens

La modalità di ricerca è stata introdotta nei dispositivi HoloLens (prima generazione) per concedere l'accesso ai sensori chiave, in particolare per le applicazioni di ricerca che non sono destinate alla distribuzione.  La modalità di HoloLens 2 mantiene le funzionalità di HoloLens 1, ma aggiunge l'accesso ai flussi seguenti:

* **Visible Light Environment Tracking Cameras** : fotocamere in scala grigia usate dal sistema per il rilevamento della testa e la creazione di mappe.
* **Camera di profondità:** funziona in due modalità:  
    + Rilevamento quasi approfondito ad alta frequenza (45 FPS) usato per il tracciamento manuale. Diversamente dalla modalità di lancio breve della prima versione, AHAT offre una pseudo profondità con ritorno a capo della fase oltre 1 metro. 
    + Rilevamento a lungo termine a bassa frequenza (1-5 FPS) usato da [Mapping spaziale](../../design/spatial-mapping.md)

* **Due versioni del flusso di riflettività IR:** usate dal HoloLens per calcolare la profondità. Queste immagini sono illuminate da raggi infrarossi e non sono interessate dalla luce visibile dell'ambiente.

Se si usa un HoloLens 2, è anche possibile accedere agli input aggiuntivi seguenti:

* **Accelerometro:** usato dal sistema per determinare l'accelerazione lineare lungo gli assi X, Y e Z e la gravità.
* **Gyro:** usato dal sistema per determinare le rotazioni.
* **Magnetometro:** usato dal sistema per stimare l'orientamento assoluto.

> [!IMPORTANT]
> La modalità di ricerca è attualmente in anteprima pubblica. 

![Screenshot dell'app Modalità di ricerca](images/sensor-stream-viewer.jpg)<br>
*Acquisizione di realtà mista di un'applicazione di test che visualizza gli otto flussi del sensore disponibili in modalità di ricerca*

## <a name="usage"></a>Utilizzo

La modalità di ricerca è progettata per ricercatori accademici e industriali che esplorano nuove idee nei Visione artificiale e robotica.  Non è destinato alle applicazioni distribuite in ambienti aziendali o disponibili tramite Microsoft Store o altri canali di distribuzione.

Inoltre, Microsoft non fornisce garanzie che la modalità di ricerca o funzionalità equivalenti sarà supportata nei futuri aggiornamenti hardware o del sistema operativo. Tuttavia, non lasciare che questo impedisci di usarlo per sviluppare e testare nuove idee.

## <a name="security-and-performance"></a>Sicurezza e prestazioni

L'abilitazione della modalità ricerca usa più potenza della batteria rispetto all'uso HoloLens 2 in condizioni normali, anche se l'applicazione che usa le funzionalità della modalità ricerca non è in esecuzione.  L'abilitazione di questa modalità può anche ridurre la sicurezza complessiva del dispositivo, perché le applicazioni potrebbero usare in modo improprio i dati dei sensori.  Altre informazioni sulla sicurezza dei dispositivi sono disponibili nelle domande HoloLens [sulla sicurezza.](/hololens/hololens-faq-security)  

## <a name="device-support"></a>Supporto di dispositivi
<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" /> </colgroup>
    <tr>
        <td><strong>Funzionalità</strong></td>
        <td><a href="/hololens/hololens1-hardware"><strong>HoloLens 1a generazione</strong></a></td>
        <td><a href="/hololens/hololens2-hardware"><strong>HoloLens 2</strong></a></td>
    </tr>
     <tr>
        <td>Telecamere di rilevamento della testa</td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td>Profondità & fotocamera IR</td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td>Accelerometro</td>
        <td>❌</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td>Giroscopio</td>
        <td>❌</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td>Magnetometro</td>
        <td>❌</td>
        <td>✔️</td>
    </tr>
</table>

## <a name="enabling-research-mode-hololens-first-gen-and-hololens-2"></a>Abilitazione della modalità di ricerca (HoloLens prima generazione e HoloLens 2)

Modalità di ricerca è un'estensione della modalità sviluppatore. Prima di iniziare, è necessario che le funzionalità di sviluppo del dispositivo siano abilitate per accedere alle impostazioni della modalità di ricerca: 

* Aprire **il menu Start > Impostazioni** e selezionare **Aggiornamenti**.
* Selezionare **For Developers (Per** sviluppatori) e **abilitare Developer Mode (Modalità sviluppatore).**
* Scorri verso il basso e abilita **Portale dispositivi**.

Dopo aver abilitato le funzionalità per gli sviluppatori, [connettersi al portale dei dispositivi](/windows/uwp/debug-test-perf/device-portal-hololens) per abilitare le funzionalità della modalità ricerca:

* Passare a **Modalità ricerca > sistema** nel **Portale di dispositivi**.
* Selezionare **Consenti l'accesso al flusso del sensore.**
* Riavviare il dispositivo dalla **voce** di menu Alimentazione nella parte superiore della pagina.

Dopo aver riavviato il dispositivo, le applicazioni caricate tramite il Portale di dispositivi **possono** accedere ai flussi della modalità di ricerca.

![Scheda Modalità di ricerca HoloLens Portale di dispositivi](images/ResearchModeDevPortal.png)<br>
*Finestra Modalità di ricerca nel HoloLens Portale di dispositivi*

> [!IMPORTANT]
> La modalità di ricerca HoloLens 2 disponibile a partire dalla build 19041.1364 . Se è necessario accedere a una build precedente, iscriversi al programma [Insider Preview.](/hololens/hololens-insider) Per altri dettagli, vedere il [repository research mode GitHub](https://github.com/microsoft/HoloLens2ForCV).

### <a name="using-sensor-data-in-your-apps"></a>Uso dei dati dei sensori nelle app

Le applicazioni possono accedere ai dati del flusso del sensore nello stesso modo in cui Media Foundation [flussi](/windows/win32/medfound/microsoft-media-foundation-sdk) di foto e videocamere. 

Tutte le API che funzionano per HoloLens sviluppo sono disponibili anche in modalità di ricerca. In particolare, l'applicazione sa esattamente dove HoloLens si trova nello spazio 6DoF in ogni momento di acquisizione dei fotogrammi del sensore.

Sono state installate applicazioni di esempio che illustrano l'accesso al flusso in modalità di ricerca, usando gli intrinseci e gli [estensivi](/windows/mixed-reality/locatable-camera#locating-the-device-camera-in-the-world)e registrando i flussi:
* [HoloLens (prima generazione)](https://github.com/Microsoft/HoloLensForCV)
* [HoloLens 2](https://github.com/microsoft/HoloLens2ForCV)

## <a name="support"></a>Supporto

Per HoloLens (prima generazione), usare [](https://github.com/Microsoft/HololensForCV/issues) il rilevamento dei problemi nel repository HoloLensForCV per inviare commenti e suggerimenti e tenere traccia dei problemi noti.

Per HoloLens 2, usare il [rilevamento dei problemi](https://github.com/microsoft/HoloLens2ForCV/issues) nel repository HoloLens2ForCV per inviare commenti e suggerimenti e tenere traccia dei problemi noti.

## <a name="see-also"></a>Vedi anche

* [Microsoft Media Foundation](/windows/win32/medfound/microsoft-media-foundation-sdk)
* [Repo GitHub HoloLensForCV](https://github.com/Microsoft/HoloLensForCV)
* [Repo GitHub HoloLens2ForCV](https://github.com/microsoft/HoloLens2ForCV)
* [Avviare il Portale di dispositivi di Windows](using-the-windows-device-portal.md)
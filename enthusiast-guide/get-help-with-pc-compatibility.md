---
title: Ottieni assistenza per la compatibilità dei PC in realtà mista di Windows
description: Risorse della Guida per i problemi di compatibilità dei PC quando si lavora con la realtà mista di Windows.
author: hferrone
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Realtà mista di Windows, realtà mista, realtà virtuale, VR, MR, feedback, Hub feedback, bug
appliesto:
- Windows 10
ms.openlocfilehash: 42e855d97538b910c087e241420d871cc6935656
ms.sourcegitcommit: b90697776b7027ed7eb8dd49a72d52740a16d12d
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/08/2020
ms.locfileid: "96843119"
---
# <a name="get-help-with-pc-compatibility-in-windows-mixed-reality"></a>Ottieni assistenza per la compatibilità dei PC in realtà mista di Windows

Quando si configura la realtà mista di Windows o si esegue il [controllo del PC Windows Mixed Reality](https://www.microsoft.com/p/windows-mixed-reality-pc-check/9nzvl19n7cnc?rtc=1#activetab=pivot:overviewtab), viene segnalato se il PC è attivo per l'attività. Sono stati suddivisi dettagli specifici sugli elementi che potrebbero essere visualizzati nelle sezioni riportate di seguito.

Prima di procedere, verificare che il computer soddisfi i [requisiti minimi per la compatibilità hardware del PC](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md) per eseguire la realtà mista.

## <a name="youre-good-to-go"></a>Si è pronti per iniziare

Ottime notizie, il PC può eseguire la realtà mista di Windows. Esiste ancora una variazione tra l'hardware e la configurazione del computer, quindi l'esperienza di realtà mista potrebbe non essere la stessa in tutti i PC.

## <a name="supports-some-features"></a>Supporta alcune funzionalità

Il PC può eseguire alcune esperienze di realtà miste di Windows, ma potrebbe non offrire la migliore esperienza possibile. I possibili svantaggi includono la grafica in ritardo, i riscontri delle prestazioni e alcune applicazioni e giochi che non possono essere eseguiti. Sono stati elencati i messaggi che potrebbero essere visualizzati e le operazioni da eseguire:

### <a name="this-pc-has-an-integrated-graphics-card-with-single-channel-ram"></a>Questo PC ha una scheda grafica integrata con RAM a canale singolo

Le schede grafiche integrate forniranno la migliore esperienza di realtà mista di Windows nei PC con RAM Dual Channel. Se si verificano problemi di prestazioni:

* Installare una [scheda grafica discreta compatibile](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines).
* Installare un'altra chiavetta RAM per creare la RAM Dual Channel.
* Passa a un [PC compatibile](https://www.microsoft.com/mixed-reality/windows-mixed-reality?rtc=1).

### <a name="this-pc-has-a-hybrid-graphics-configuration-with-an-incompatible-pcie-link"></a>Questo PC ha una configurazione grafica ibrida con un collegamento PCIe non compatibile

PCIe è il *componente periferica Interconnect Express*, ovvero la connessione utilizzata da un PC per comunicare con una scheda grafica. La configurazione potrebbe funzionare, ma se si verificano problemi, è necessario passare a un [PC compatibile](https://www.microsoft.com/mixed-reality/windows-mixed-reality?rtc=1).

### <a name="this-pcs-graphics-driver-might-not-work-well-with-windows-mixed-reality"></a>Il driver grafico di questo PC potrebbe non funzionare correttamente con la realtà mista di Windows

Provare a scaricare un nuovo driver grafico usando Windows Update selezionando **avvia > impostazioni > aggiorna & sicurezza > verificare la disponibilità di aggiornamenti** oppure passare al sito Web del produttore del PC o della scheda grafica.

> [!div class="nextstepaction"]
> [Verificare gli aggiornamenti](ms-settings:windowsupdate?activationSource=SMC-Article-4045777)

Se il tentativo non funziona, è necessario aggiungere una [scheda grafica compatibile](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines) o passare a un [PC compatibile](https://www.microsoft.com/mixed-reality/windows-mixed-reality?rtc=1).

### <a name="this-pcs-processor-might-not-work-well-with-windows-mixed-reality"></a>Il processore di questo PC potrebbe non funzionare correttamente con la realtà mista di Windows

Il processore del PC potrebbe non funzionare correttamente con la realtà mista di Windows, perché non ha un numero sufficiente di core. Se la realtà mista di Windows non viene eseguita correttamente, sostituire il processore con uno [compatibile](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md) o passare a un [PC compatibile](https://www.microsoft.com/mixed-reality/windows-mixed-reality?rtc=1).

### <a name="this-pc-might-not-have-a-compatible-usb-configuration"></a>Il PC potrebbe non avere una configurazione USB compatibile

Se si verificano problemi con la realtà mista di Windows:

* Collegare la cuffia a una porta USB diversa, se disponibile.
* Se il sistema non funziona, disinstallare il driver USB corrente del PC e reinstallare un driver Microsoft:

1. Selezionare **Start**, quindi digitare "gestione dispositivi" nella casella di **ricerca** .
2. Selezionare **Device Manager** dai risultati.
3. Espandere la categoria per i controller del bus seriale universale, esaminare i dispositivi elencati e disinstallare tutti i driver incompatibili.
    * Se l'elenco include un elemento "controller host estendibile" che non ha "Microsoft" alla fine del nome del dispositivo, il driver non è compatibile con la realtà mista di Windows. È necessario disinstallarlo. Per disinstallare un driver, fare clic con il pulsante destro del mouse sul dispositivo nell'elenco e scegliere **Disinstalla dispositivo**. Selezionare la casella **di controllo Elimina il software driver per questo dispositivo** , quindi selezionare **Disinstalla**.
    * Se l'elenco include un elemento "controller host estendibile" che include "Etron" nel nome, il controller USB non è compatibile con la realtà mista di Windows. È necessario usare una porta USB diversa nel PC o acquistare un controller host USB 3,0 diverso.
4. Riavvia il PC.
5. Tornare a Device Manager e individuare nuovamente l'elemento del controller host estendibile. Se viene visualizzato "Microsoft" alla fine del nome del dispositivo, è possibile iniziare. In caso contrario, ripetere i passaggi di disinstallazione per rimuovere eventuali versioni non Microsoft aggiuntive del driver.

* Se il problema persiste, aggiungere una scheda USB PCIe al PC.

### <a name="this-pc-doesnt-have-bluetooth-40-for-controllers"></a>Il PC non ha Bluetooth 4,0 per i controller

2018 e i nuovi auricolari di realtà mista di Windows hanno già il Bluetooth integrato, ma se si dispone di un auricolare obsoleto, è necessario Bluetooth 4,0 per i controller di movimento della realtà mista. È comunque possibile usare la realtà mista di Windows con un controller Xbox, un mouse e una tastiera o un adattatore Bluetooth USB per connettere i controller di movimento al PC. [Vedere gli adapter consigliati](recommended-adapters-for-windows-mixed-reality-capable-pcs.md)

### <a name="depending-on-your-headset-you-may-need-a-bluetooth-adapter-to-use-motion-controllers"></a>A seconda dell'auricolare, potrebbe essere necessario un adattatore Bluetooth per usare i controller di movimento

Alcuni auricolari dispongono di Bluetooth integrato, quindi i controller possono associarsi direttamente agli auricolari. Per usare i controller di movimento, altri richiedono una radio Bluetooth nel PC o un dongle separato. Per ulteriori informazioni, vedere la pagina relativa agli [Adapter consigliati](recommended-adapters-for-windows-mixed-reality-capable-pcs.md) .

### <a name="this-pc-doesnt-have-a-self-powered-usb-port"></a>Il PC non dispone di una porta USB autonoma

Una porta USB 3,0 auto-alimentata è necessaria per connettere un headset di realtà mista di Windows. Connettere un hub USB 3,0 alimentato al PC e usarlo per connettere l'auricolare.

### <a name="this-pcs-graphics-card-wont-work-with-windows-mixed-reality"></a>La scheda grafica del PC non funzionerà con la realtà mista di Windows

La scheda grafica del PC non è compatibile con la realtà mista di Windows. È necessario aggiungere una [scheda grafica compatibile](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines) o passare a un [PC compatibile](https://www.microsoft.com/mixed-reality/windows-mixed-reality?rtc=1).

### <a name="this-pcs-graphics-driver-wont-work-with-windows-mixed-reality"></a>Il driver di grafica del PC non funzionerà con la realtà mista di Windows

Il driver di grafica del PC non funzionerà con la realtà mista di Windows. Provare a scaricare un nuovo driver grafico usando Windows Update selezionando **avvia > impostazioni > aggiorna & sicurezza > verificare la disponibilità di aggiornamenti** o andare al sito Web del produttore del PC o della scheda grafica.

> [!div class="nextstepaction"]
> [Verificare gli aggiornamenti](ms-settings:windowsupdate?activationSource=SMC-Article-4045777)

Se il tentativo non funziona, è necessario aggiungere una [scheda grafica compatibile](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines) o passare a un [PC compatibile](https://www.microsoft.com/mixed-reality/windows-mixed-reality?rtc=1).

### <a name="this-pcs-processor-wont-work-with-windows-mixed-reality"></a>Il processore del PC non funzionerà con la realtà mista di Windows

Il processore del PC non supporta le istruzioni AVX/POPCNT. Per eseguire la realtà mista di Windows, è necessario sostituirla con una [scheda grafica compatibile](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines) o passare a un PC compatibile.

### <a name="this-pc-doesnt-have-enough-free-disk-space-to-run-windows-mixed-reality"></a>Il PC non dispone di spazio su disco sufficiente per eseguire la realtà mista di Windows

Per la realtà mista di Windows sono necessari 10 GB di spazio libero su disco per l'installazione e prestazioni ottimali. Deselezionare uno spazio nell'unità e riprovare a eseguire la configurazione dall'inizio.

### <a name="this-pc-is-running-an-edition-of-windows-that-doesnt-support-windows-mixed-reality"></a>Questo PC esegue un'edizione di Windows che non supporta la realtà mista di Windows

La realtà mista di Windows funziona in Windows 10 Home e Windows 10 Pro. È necessario installare una di queste edizioni per usare la realtà mista di Windows.

### <a name="this-pc-isnt-running-the-latest-version-of-windows-10"></a>Il PC non esegue la versione più recente di Windows 10

La realtà mista di Windows richiede Windows 10 Fall Creators Update. [Aggiornare il PC](https://support.microsoft.com/help/4028685) e riprovare.

### <a name="this-pc-has-no-usb-30-port"></a>Il PC non ha una porta USB 3,0

È necessaria una porta USB 3,0 per connettere un auricolare di realtà mista di Windows. Se si usa un PC desktop, aggiungere una scheda USB PCIe. Se si usa un computer portatile, è necessario passare a un [PC compatibile](https://www.microsoft.com/mixed-reality/windows-mixed-reality?rtc=1).

### <a name="you-cant-run-this-app-via-remote-desktop"></a>Non è possibile eseguire questa app tramite Desktop remoto

Per usare la realtà mista di Windows, è necessario un PC con un monitor connesso. Se si usa una macchina virtuale o non si dispone di un monitoraggio, provare a usare una scheda di visualizzazione virtuale. Si tratta di un dispositivo che si connette al DisplayPort del PC e emula lo schermo di un computer.

## <a name="getting-the-best-performance"></a>Ottenere prestazioni ottimali

Alcune configurazioni hardware possono causare problemi di prestazioni con la realtà mista di Windows. Per problemi quali il caricamento lento, gli oggetti visivi increspati o qualità visiva scadente, provare queste correzioni comuni:

* Chiudere tutte le app aperte in esecuzione sul desktop del PC.
* Se si usa un adattatore USB-C o DisplayPort per HDMI, provare con un altro. Vedere gli adapter consigliati
* Se sono presenti monitoraggi aggiuntivi connessi alla scheda grafica del PC, disconnetterli.
* Provare a scaricare alcune app di realtà miste diverse da Windows Store: alcune possono funzionare meglio con la configurazione del computer.

> [!NOTE]
> Se viene visualizzato il messaggio "questa configurazione hardware potrebbe funzionare con la realtà mista di Windows, ma non è ancora stata testata", potrebbe verificarsi alcuni problemi di prestazioni quando si esegue la realtà mista di Windows per sessioni lunghe.

## <a name="see-also"></a>Vedi anche

* [Contattare la community](https://answers.microsoft.com)
* [Contattaci per assistenza](https://support.microsoft.com/contactus/)
* [Risoluzione dei problemi](troubleshooting-windows-mixed-reality.md)
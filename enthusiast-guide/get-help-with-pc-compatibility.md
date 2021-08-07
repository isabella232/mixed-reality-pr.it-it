---
title: Assistenza per la compatibilità dei PC
description: Tenersi aggiornati sulle risorse per la risoluzione dei problemi di compatibilità del PC quando si Windows Mixed Reality applicazioni e dispositivi.
author: hferrone
ms.author: v-hferrone
ms.date: 01/07/2021
ms.topic: article
keywords: Windows Mixed Reality, Realtà mista, Realtà virtuale, REALTÀ VIRTUALE, MR, Feedback, Hub di Feedback, bug
appliesto:
- Windows 10
ms.openlocfilehash: cd5598147823670d1aa00eddda844bea21d7da262339624613f3724cbc5157fa
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115189213"
---
# <a name="get-help-with-pc-compatibility-in-windows-mixed-reality"></a>Ottenere assistenza per la compatibilità del PC in Windows Mixed Reality

Quando si configura un Windows Mixed Reality o si usa il Portale realtà mista [,](install-windows-mixed-reality.md)si otterrà un report che indica se il PC è in grado di eseguire l'attività. Sono stati suddivisi dettagli specifici su ciò che potrebbe essere visualizzato nelle sezioni seguenti.

Prima di procedere, provare le correzioni più comuni seguenti: 

> [!div class="checklist"]
> * Assicurarsi che il computer soddisfi i requisiti [minimi di compatibilità hardware del PC](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md)
> * Verificare che la [scheda grafica e il processore](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines) siano compatibili
> * Controllare [l'elenco degli adapter consigliati](recommended-adapters-for-windows-mixed-reality-capable-pcs.md)
> * Aggiornare il driver di grafica selezionando Start > Impostazioni > Update & security > Check for updates (Verifica **disponibilità aggiornamenti)** 

Se si vuole entrare in contatto, è possibile chiedere alla [community,](https://answers.microsoft.com) [contattare](https://support.microsoft.com/contactus/)il supporto tecnico o passare alle informazioni sulla [risoluzione dei](troubleshooting-windows-mixed-reality.md) problemi.

## <a name="youre-good-to-go"></a>È tutto a posto

Buona notizia: se viene visualizzato il messaggio **You're good to go** (Sei a posto), il PC può essere Windows Mixed Reality! C'è ancora una variazione tra l'hardware e la configurazione del computer, quindi l'esperienza di realtà mista potrebbe non essere la stessa in ogni PC.

## <a name="supports-some-features"></a>Supporta alcune funzionalità

Se viene visualizzato il messaggio **Supports some features** (Supporta alcune funzionalità), il PC può eseguire alcune esperienze Windows Mixed Reality, ma potrebbe non offrire la migliore esperienza possibile. I possibili svantaggi includono grafica in ritardo, riscontri di prestazioni e alcune applicazioni e giochi che non è possibile eseguire. Di seguito sono elencati i messaggi che è possibile visualizzare e le relative opzioni:

* [Questo PC ha una scheda grafica integrata con RAM a canale singolo](#this-pc-has-an-integrated-graphics-card-with-single-channel-ram)
* [Questo PC ha una configurazione grafica ibrida con un collegamento PCIe incompatibile](#this-pc-has-a-hybrid-graphics-configuration-with-an-incompatible-pcie-link)
* [Il driver di grafica di questo PC potrebbe non funzionare correttamente con Windows Mixed Reality](#this-pcs-graphics-driver-might-not-work-well-with-windows-mixed-reality)
* [Il processore di questo PC potrebbe non funzionare correttamente con Windows Mixed Reality](#this-pcs-processor-might-not-work-well-with-windows-mixed-reality)
* [Questo PC potrebbe non avere una configurazione USB compatibile](#this-pc-might-not-have-a-compatible-usb-configuration)
* [Questo PC non dispone di Bluetooth 4.0 per i controller](#this-pc-doesnt-have-bluetooth-40-for-controllers)
* [A seconda del visore VR, potrebbe essere necessario un adattatore Bluetooth per usare i controller del movimento](#depending-on-your-headset-you-may-need-a-bluetooth-adapter-to-use-motion-controllers)
* [Questo PC non dispone di una porta USB autoesostima](#this-pc-doesnt-have-a-self-powered-usb-port)
* [La scheda grafica di questo PC non funzionerà con Windows Mixed Reality](#this-pcs-graphics-card-wont-work-with-windows-mixed-reality)
* [Il driver di grafica di questo PC non funzionerà con Windows Mixed Reality](#this-pcs-graphics-driver-wont-work-with-windows-mixed-reality)
* [Il processore di questo PC non funzionerà con Windows Mixed Reality](#this-pcs-processor-wont-work-with-windows-mixed-reality)
* [Questo PC non dispone di spazio libero su disco sufficiente per eseguire Windows Mixed Reality](#this-pc-doesnt-have-enough-free-disk-space-to-run-windows-mixed-reality)
* [Questo PC esegue un'edizione di Windows che non supporta Windows Mixed Reality](#this-pc-is-running-an-edition-of-windows-that-doesnt-support-windows-mixed-reality)
* [Questo PC non esegue la versione più recente di Windows 10](#this-pc-isnt-running-the-latest-version-of-windows-10)
* [Questo PC non ha una porta USB 3.0](#this-pc-has-no-usb-30-port)
* [Non è possibile eseguire questa app tramite Desktop remoto](#you-cant-run-this-app-via-remote-desktop)

### <a name="this-pc-has-an-integrated-graphics-card-with-single-channel-ram"></a>Questo PC ha una scheda grafica integrata con RAM a canale singolo

Le schede grafiche integrate offrono la migliore Windows Mixed Reality'esperienza nei PC con RAM a doppio canale. Se si verificano problemi di prestazioni:

> [!div class="checklist"]
> * Installare una [scheda grafica discreta compatibile](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines)
> * Installare un'unità RAM aggiuntiva per creare RAM a doppio canale
> * Passare a [un PC compatibile](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines)

### <a name="this-pc-has-a-hybrid-graphics-configuration-with-an-incompatible-pcie-link"></a>Questo PC ha una configurazione grafica ibrida con un collegamento PCIe incompatibile

PCIe è l'acronimo di *Peripheral Component Interconnect Express,* ovvero la connessione che un PC usa per comunicare con una scheda grafica. La configurazione potrebbe funzionare, ma se si verificano problemi è necessario passare a un [PC compatibile.](https://www.microsoft.com/mixed-reality/windows-mixed-reality?rtc=1)

### <a name="this-pcs-graphics-driver-might-not-work-well-with-windows-mixed-reality"></a>Il driver di grafica di questo PC potrebbe non funzionare correttamente con Windows Mixed Reality

Provare a scaricare un nuovo driver di grafica usando Windows Update by:

> [!div class="checklist"]
> * Selezionando **Start > Impostazioni > Update & security > Check for updates** (Controlla aggiornamenti) o visitando il sito Web del produttore del PC o della scheda grafica
> * [Verificare gli aggiornamenti](ms-settings:windowsupdate?activationSource=SMC-Article-4045777)

Se non funziona, è necessario:

> [!div class="checklist"]
> * Aggiungere una [scheda grafica compatibile](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines) 
> * Passare a [un PC compatibile](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines)

### <a name="this-pcs-processor-might-not-work-well-with-windows-mixed-reality"></a>Il processore di questo PC potrebbe non funzionare correttamente con Windows Mixed Reality

Il processore del PC potrebbe non funzionare correttamente Windows Mixed Reality perché non ha un numero sufficiente di core. Se Windows Mixed Reality non funziona bene:

> [!div class="checklist"]
> * Sostituire il processore con [uno compatibile](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md) 
> * Passare a [un PC compatibile](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines)

### <a name="this-pc-might-not-have-a-compatible-usb-configuration"></a>Questo PC potrebbe non avere una configurazione USB compatibile

Per problemi di esecuzione Windows Mixed Reality:

> [!div class="checklist"]
> * Consultare la documentazione [degli adapter consigliati per](recommended-adapters-for-windows-mixed-reality-capable-pcs.md) le soluzioni ai problemi di compatibilità comuni
> * Prendere in considerazione [l'uso di un hub USB esterno](recommended-adapters-for-windows-mixed-reality-capable-pcs.md#using-external-usb-30-hubs-with-windows-mixed-reality-headsets)

Se i problemi persistono:

> [!div class="checklist"]
> * Collegare il visore VR a una porta USB diversa, se disponibile.
> * Se non funziona, disinstallare il driver USB corrente del PC e quindi reinstallare un driver Microsoft:

1. Selezionare **Start** e quindi digitare "gestione dispositivi" nella **casella Cerca.**
2. Selezionare **Gestione dispositivi** nei risultati.
3. Espandere la categoria controller del bus seriale universale, esaminare i dispositivi elencati e disinstallare eventuali driver incompatibili.
    * Se l'elenco include un elemento "eXtensible Host Controller" che non contiene "Microsoft" alla fine del nome del dispositivo, il driver non è compatibile con Windows Mixed Reality. È necessario disinstallarlo. Per disinstallare un driver, fare clic con il pulsante destro del mouse sul dispositivo nell'elenco e **scegliere Disinstalla dispositivo.** Selezionare la **casella di controllo Delete the driver software for this device (Elimina il software** driver per questo dispositivo) e quindi selezionare **Disinstalla**.
    * Se l'elenco include un elemento "eXtensible Host Controller" che include "Etron" nel nome, il controller USB non è compatibile con Windows Mixed Reality. È necessario usare una porta USB diversa nel PC o acquistare un controller host USB 3.0 diverso.
4. Riavvia il PC.
5. Tornare a Gestione dispositivi e individuare di nuovo l'elemento Controller host eXtensible. Se ora viene visualizzato "Microsoft" alla fine del nome del dispositivo, è possibile andare. In caso contrario, ripetere i passaggi di disinstallazione per rimuovere eventuali versioni aggiuntive non Microsoft del driver.

> [!div class="checklist"]
> * Se il problema persiste, aggiungere una scheda USB PCIe al PC.

### <a name="this-pc-doesnt-have-bluetooth-40-for-controllers"></a>Questo PC non dispone di Bluetooth 4.0 per i controller

I visori VR Windows Mixed Reality 2018 e versioni più recenti hanno già il Bluetooth incorporato, ma se si dispone di visori VR meno recenti, è necessario bluetooth 4.0 per i controller del movimento di realtà mista. È comunque possibile usare Windows Mixed Reality con un [controller Xbox,](motion-controller-problems.md#can-i-pair-my-xbox-controller-to-my-pc-so-i-can-use-it-in-headset)un [mouse](/windows/mixed-reality/discover/navigating-the-windows-mixed-reality-home#keyboard-and-mouse)e una tastiera o un [adattatore usb Bluetooth](motion-controller-problems.md#how-can-i-tell-if-im-using-bluetooth-technology) per connettere i controller del movimento al PC. [Vedere schede consigliate](recommended-adapters-for-windows-mixed-reality-capable-pcs.md)

### <a name="depending-on-your-headset-you-may-need-a-bluetooth-adapter-to-use-motion-controllers"></a>A seconda del visore VR, potrebbe essere necessario un adattatore Bluetooth per usare i controller del movimento

Alcuni visori VR Bluetooth incorporati in modo che i controller possano essere associati direttamente ai visori VR. Altri richiedono una Bluetooth radio nel PC (o un dongle separato) per usare i controller del movimento. Per altre informazioni, vedere la [pagina adapter consigliati.](recommended-adapters-for-windows-mixed-reality-capable-pcs.md#windows-mixed-reality-compatible-usb-bluetooth-adapters)

### <a name="this-pc-doesnt-have-a-self-powered-usb-port"></a>Questo PC non dispone di una porta USB autoesostima

Per connettere un visore VR, è necessaria una porta USB 3.0 auto-Windows Mixed Reality. Connessione un [hub USB 3.0](recommended-adapters-for-windows-mixed-reality-capable-pcs.md#using-external-usb-30-hubs-with-windows-mixed-reality-headsets) alimentato al PC e usarlo per connettere il visore VR.

### <a name="this-pcs-graphics-card-wont-work-with-windows-mixed-reality"></a>La scheda grafica di questo PC non funzionerà con Windows Mixed Reality

La scheda grafica di questo PC non è compatibile con Windows Mixed Reality. È necessario:

> [!div class="checklist"]
> * Aggiungere una [scheda grafica compatibile](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines) 
> * Passare a [un PC compatibile](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines)

### <a name="this-pcs-graphics-driver-wont-work-with-windows-mixed-reality"></a>Il driver di grafica di questo PC non funzionerà con Windows Mixed Reality

Il driver di grafica di questo PC non funzionerà con Windows Mixed Reality. Provare a scaricare un nuovo driver di grafica usando Windows Update by:

> [!div class="checklist"]
> * Selezionando **Start > Impostazioni > Update & security > Check for updates** (Controlla aggiornamenti) o visitando il sito Web del produttore del PC o della scheda grafica
> * [Verificare gli aggiornamenti](ms-settings:windowsupdate?activationSource=SMC-Article-4045777)

Se non funziona, è necessario:

> [!div class="checklist"]
> * Aggiungere una [scheda grafica compatibile](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines) 
> * Passare a un [PC compatibile](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines)

### <a name="this-pcs-processor-wont-work-with-windows-mixed-reality"></a>Il processore di questo PC non funzionerà con Windows Mixed Reality

Il processore di questo PC non supporta le istruzioni AVX/Popcnt. Per eseguire Windows Mixed Reality, è necessario:

> [!div class="checklist"]
> * Sostituirlo con una [scheda grafica compatibile](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines) 
> * Passare a un [PC compatibile](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines)

### <a name="this-pc-doesnt-have-enough-free-disk-space-to-run-windows-mixed-reality"></a>Questo PC non dispone di spazio libero su disco sufficiente per eseguire Windows Mixed Reality

Windows Mixed Reality richiede 10 GB di spazio libero su disco per la configurazione e prestazioni ottimali. Cancellare spazio nell'unità e quindi provare a eseguire di nuovo la configurazione dall'inizio.

### <a name="this-pc-is-running-an-edition-of-windows-that-doesnt-support-windows-mixed-reality"></a>Questo PC esegue un'edizione di Windows che non supporta Windows Mixed Reality

Windows Mixed Reality funziona [su](https://www.microsoft.com/p/windows-10-home/d76qx4bznwk4?activetab=pivot:overviewtab) Windows 10 Home e [Windows 10 Pro](https://www.microsoft.com/p/windows-10-pro/DF77X4D43RKT?icid=W10Pro_upsell_071817&activetab=pivot:overviewtab). È necessario installare una di queste edizioni per usare Windows Mixed Reality.

### <a name="this-pc-isnt-running-the-latest-version-of-windows-10"></a>Questo PC non esegue la versione più recente di Windows 10

Windows Mixed Reality richiede l'Windows 10 Fall Creators Update. [Aggiornare il PC](https://support.microsoft.com/help/4028685) e riprovare.

### <a name="this-pc-has-no-usb-30-port"></a>Questo PC non ha una porta USB 3.0

Sarà necessaria una porta USB 3.0 per connettere un dispositivo Windows Mixed Reality visore. Se si usa un PC desktop, aggiungere una scheda USB PCIe. Per i portatili, è necessario passare a un [PC compatibile.](https://www.microsoft.com/mixed-reality/windows-mixed-reality?rtc=1)

### <a name="you-cant-run-this-app-via-remote-desktop"></a>Non è possibile eseguire questa app tramite Desktop remoto

Per usare Windows Mixed Reality, è necessario un PC con un monitor connesso. Se si usa una macchina virtuale o non si ha un monitoraggio, provare a usare una scheda video virtuale. Si tratta di un dispositivo che collega displayPort del PC ed emula uno schermo del computer.

## <a name="getting-the-best-performance"></a>Ottenere le prestazioni migliori

Alcune configurazioni hardware potrebbero causare problemi di prestazioni con Windows Mixed Reality. Per problemi come il caricamento lento, gli oggetti visivi sminuzzanti o una qualità visiva scadente, provare queste correzioni comuni:

* Chiudere tutte le app aperte in esecuzione sul desktop del PC
* Se si usa un adattatore USB-C o DisplayPort to HDMI, provarne uno diverso. Vedere gli adapter consigliati
* Se sono presenti monitor aggiuntivi connessi alla scheda grafica del PC, disconnetterli
* Provare a scaricare alcune diverse app di realtà mista da Windows Store. Alcune potrebbero funzionare meglio con la configurazione del computer
* Consultare la documentazione [sulle domande sulle prestazioni](performance-questions.md)

Se si verificano ancora problemi di prestazioni, aggiornare le [impostazioni](set-up-windows-mixed-reality.md) Windows Mixed Reality per un'esperienza utente ottimale:

* Esperienza
* Risoluzione
* Frequenza fotogrammi
* Calibrazione

> [!NOTE]
> Se viene visualizzato il messaggio "Questa configurazione hardware potrebbe funzionare con Windows Mixed Reality, ma non è ancora stata testata", si potrebbero verificare alcuni problemi di prestazioni durante l'esecuzione di Windows Mixed Reality per sessioni lunghe.

## <a name="working-with-steamvr"></a>Uso di SteamVR

L'esperienza dei giochi di SteamVR è un ottimo modo per sperimentare tutto ciò che la realtà virtuale ha da offrire. Tuttavia, è necessario assicurarsi di ottenere [](performance-questions.md) prestazioni ottimali dal dispositivo immersivo. Dopo aver installato [Steam:](https://store.steampowered.com/about)

* Seguire le istruzioni per [l'uso di SteamVR con Windows Mixed Reality](using-steamvr-with-windows-mixed-reality.md)
* Installare le app [di test delle prestazioni di SteamVR](https://store.steampowered.com/app/323910/SteamVR_Performance_Test)

## <a name="next-vr-checkpoint"></a>Checkpoint VR successivo

Se si sta seguendo il percorso vr che è stato stabilito, si è quasi pronti per acquistare un dispositivo. Da qui è possibile continuare fino all'ultimo checkpoint prima di acquistare il checkpoint:

> [!div class="nextstepaction"]
> [Domande frequenti per l'acquisto](before-you-buy-faqs.md)

Oppure passare direttamente alla sezione Introduttiva:

> [!div class="nextstepaction"]
> [Configurazione di Windows Mixed Reality](set-up-windows-mixed-reality.md)

È sempre possibile tornare al percorso [VR](vr-journey.md) in qualsiasi momento.
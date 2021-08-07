---
title: Domande frequenti sul visore VR
description: Visualizzare Windows Mixed Reality risoluzione dei problemi di visualizzazione dei visori VR che vanno oltre la documentazione di supporto per gli utenti standard.
author: hferrone
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Windows Mixed Reality, Realtà mista, Realtà virtuale, REALTÀ VIRTUALE, MR, Risoluzione dei problemi, Errori, Guida, Supporto
appliesto:
- Windows 10
ms.openlocfilehash: 811b5160c739c8b19fde737e7a61bcef84e0cf60a87927adbe21241e229f3f22
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115189390"
---
# <a name="headset-display-faqs"></a>Domande frequenti sul visore VR

## <a name="my-headset-displays-are-black"></a>I visori VR sono di colore nero

* Controllare le prestazioni e la stabilità del PC:
    * Usare il Gestione attività per verificare se alcuni processi stanno esendo il limite massimo di CPU, GPU o unità disco del PC.
    * Controllare i log "Applicazione" e "Sistema" nei log di **Visualizzatore eventi > Windows** per verificare se un'app si arresta in modo anomalo e genera report Segnalazione errori Windows (WER).
    * Controllare Windows Update per assicurarsi che la versione di Windows sia aggiornata. Potrebbe essere necessario selezionare "Controlla aggiornamenti" più volte.
* Verificare la stabilità di app e giochi:
    * Assicurarsi che il PC soddisfi i requisiti minimi di sistema di qualsiasi app o gioco che non viene eseguito correttamente.
    * Verificare che la versione del driver GPU sia recente e verificare la presenza di eventuali nuovi problemi di prestazioni e compatibilità e regressioni nei nuovi driver.
    * Se si usano app e giochi di SteamVR, assicurarsi che i componenti di SteamVR e Windows Mixed Reality per SteamVR siano aggiornati.
* Controllare la compatibilità dell'adattatore HDMI:
    * Assicurarsi che il cavo HDMI sia collegato in tutti i modi.
    * Se si usa un adattatore HDMI, ad esempio un mini displayport per l'adattatore HDMI, assicurarsi che sia compatibile con Windows Mixed Reality. L'adattatore deve supportare HDMI 2.0 e molte schede meno recenti supportano solo 1080p. Vedere [Schede consigliate per Windows Mixed Reality](recommended-adapters-for-windows-mixed-reality-capable-pcs.md).
    * L'ordine dei plug può essere importante. Connessione l'adattatore HDMI al PC prima di collegare il visore VR all'adattatore, soprattutto se si usa un adattatore USB-C a HDMI.
    * Provare a rimuovere i cavi di estensione, se in uso.
* Controllare la compatibilità delle schede grafiche e dei driver:
    * Provare la porta HDMI del PC con un monitor PC. Alcuni PC possono avere più di una porta HDMI e non tutti possono essere attivi.
    * Se il PC ha un'unità di elaborazione grafica integrata (iGPU) e un'unità di elaborazione grafica discreta (dGPU), assicurarsi di essere collegati alla porta HDMI della dGPU.
    * Controllare la versione del driver GPU. Assicurarsi che sia recente, ma prestare attenzione anche a eventuali nuovi problemi di prestazioni e compatibilità e regressioni sui driver nuovi.
    * Se si usa realtà mista in un portatile ed è stato installato un driver di grafica più recente dal sito Web del produttore della scheda grafica, provare a eseguire il downgrade al driver della scheda grafica più recente disponibile nel sito Web del produttore del PC o in Windows Update.
    * Se si dispone di più monitor PC connessi al PC, provare a disconnettere temporaneamente tutti i monitor, ad esempio uno.
    * Se è stata impostata una frequenza di aggiornamento personalizzata per il monitor del PC, provare a ripristinare temporaneamente una frequenza di aggiornamento standard, ad esempio 60 Hz.
    * Se la scheda grafica è stata modificata di recente senza reinstallare Windows, verificare che nel monitor del visore VR sia ancora installato il driver corretto. Con il visore VR collegato, verificare che "Visore VR realtà mista" sia elencato nel nodo Monitor in Gestione dispositivi.
    * Se il PC ha una scheda grafica Nvidia, assicurarsi che il software Visione 3D di Nvidia sia disabilitato.
    * In alcune schede grafiche (in particolare le schede meno recenti), la porta HDMI potrebbe non supportare HDMI 2.0 o non essere completamente compatibile con Windows Mixed Reality. Provare a usare displayPort della scheda grafica con una [scheda DisplayPort da 1.2 a HDMI 2.0.](recommended-adapters-for-windows-mixed-reality-capable-pcs.md)
    * I PC HP Omen con numero di prodotto HP 1RJ99EA#USB hanno porte HDMI incompatibili con Windows Mixed Reality (aprire "HP Support Assistant" e il numero verrà elencato nella parte inferiore dell'app).
    * Se il PC ha una scheda grafica serie AMD R9 e si usa un visore VR Samsung Mixed Reality, aggiornare il firmware del visore VR alla versione 1.0.8 o successiva per usare la porta HDMI della scheda grafica con il visore VR.
    * Se si usa un dispositivo Surface Book 2, assicurarsi di usare l'adattatore [Surface USB-C per HDMI.](recommended-adapters-for-windows-mixed-reality-capable-pcs.md)
* Verificare la presenza di un problema di hardware per visori VR di realtà mista:
    * Per confermare o escludere i problemi hardware con il visore VR, connettere il visore VR realtà mista a un altro PC.
    * Verificare prima di tutto la compatibilità del PC e i problemi di configurazione, perché i sintomi sono simili.
* Assicurarsi che il cavo USB sia collegato a una porta USB 3.0 o superiore. Accanto alle porte USB 3.0 sono presenti SS (Super Speed) e spesso sono di colore blu.

## <a name="my-headset-display-occasionally-turns-black-after-some-use"></a>Il visore VR diventa occasionalmente nero dopo un uso

* Provare a disabilitare le funzionalità di sospensione o risparmio energia USB nel PC. Ad esempio, in Impostazioni > System > Power & Sospendi sospensione **> [USB](/windows-hardware/drivers/usbcon/usb-selective-suspend)** selettiva sospende , l'impostazione "Consenti al computer di spegnere il dispositivo per risparmiare energia" in Gestione dispositivi ed eventuali impostazioni di risparmio energia USB nel firmware del PC.
* Disconnettere temporaneamente eventuali altri dispositivi USB e periferiche connessi al PC.
* Verificare che la versione del driver GPU sia recente e verificare la presenza di eventuali nuovi problemi di prestazioni e compatibilità e regressioni nei nuovi driver.

## <a name="one-of-the-displays-on-my-headset-is-black"></a>Uno dei display sul visore VR è nero

* Se si usa un adattatore HDMI, assicurarsi che supporti HDMI 2.0.
* Rimuovere eventuali cavi di estensione USB e HDMI in uso.
* Assicurarsi che il driver di grafica sia aggiornato.
* Provare il visore VR di realtà mista in un altro PC.

## <a name="my-headset-displays-turn-blue-and-then-mixed-reality-portal-reinitializes"></a>Il visore VR viene visualizzato in blu e quindi Portale realtà mista reinizializza

Ciò indica in genere un problema occasionale di affidabilità del controller USB nel PC:

* Provare un'altra porta USB. Il PC può avere più controller USB 3.0.
* Rimuovere eventuali cavi di estensione (se applicabile).
* Scollegare tutti gli altri dispositivi USB dal PC.
* Connessione un hub USB 3.0 alimentato esternamente al PC e collegare il visore VR all'hub.
* Se si usa un PC desktop, è consigliabile acquistare una scheda PCIe USB 3.0 per aggiungere un altro controller USB al PC.

## <a name="my-headset-causes-my-pc-to-hang-or-show-a-black-screen-while-starting-up"></a>Il visore VR causa il blocco del PC o la visualizzazione di uno schermo nero all'avvio

In alcuni PC, lasciare il visore VR collegato prima di accendere o riavviare il PC può interferire con il processo di avvio. Il PC può selezionare il visore VR come "monitor principale" per visualizzare lo stato di avvio del PC, non avviarsi correttamente o "bloccarsi" o produrre un codice di errore di segnalazione. Il comportamento dipende dalla make e dal modello del PC o dalla make e dal modello della scheda grafica. Per risolvere il problema:

* Connessione il visore VR su una porta diversa nella scheda grafica (potrebbe essere necessario usare un adattatore per usare le altre porte).
* Assicurarsi che il FIRMWARE BIOS/UEFI del PC sia aggiornato, ma aggiornare il FIRMWARE BIOS/UEFI del PC solo se si ha familiarità con questa operazione.

## <a name="my-pc-or-headset-displays-flicker-flash-or-remain-black-when-using-a-surface-pc"></a>Il PC o il visore VR visualizza sfarfallio, lampeggia o rimane nero quando si usa un Pc Surface

* Assicurarsi di usare un adattatore HDMI che supporta HDMI 2.0. Molte schede HDMI meno recenti supportano solo la risoluzione 1080p, che non è sufficiente per i visori VR di realtà mista.
* Assicurarsi che il driver di grafica sia aggiornato. Controllare Windows e il sito Web del produttore del PC per un driver di grafica aggiornato.
* Alcuni dispositivi Surface non sono compatibili con Windows Mixed Reality. Altre informazioni sulla [compatibilità e i requisiti di Surface.](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#windows-mixed-reality-and-surface)

## <a name="my-headset-display-doesnt-work-after-i-shut-down-and-do-a-fast-startup"></a>Il display del visore VR non funziona dopo l'arresto e l'avvio rapido

Scollegare il cavo HDMI e il cavo USB dal visore VR e quindi collegarli nuovamente.

## <a name="my-headset-displays-are-choppy-but-mixed-reality-portals-preview-window-appears-fine"></a>I visori VR sono molto visualizzati, Portale realtà mista la finestra di anteprima del dispositivo viene visualizzata correttamente

* Assicurati che le risorse di sistema del PC (CPU, memoria e disco rigido) siano disponibili e non utilizzate da un'altra app o processo.
* Aggiornare il driver di grafica.

## <a name="im-getting-a-the-install-class-is-not-present-or-is-invalid-error-in-device-manager"></a>Viene visualizzato l'errore "La classe di installazione non è presente o non è valida" in Gestione dispositivi

Se viene visualizzato "HoloLens" con un punto esclamativo giallo in Gestione dispositivi, selezionare il dispositivo per altri dettagli. Se viene visualizzato il messaggio "I driver per questo dispositivo non sono installati. (Codice 28): la classe di installazione non è presente o non è valida" perché il PC esegue [Windows 10 N.](https://support.microsoft.com/en-us/help/4039813/media-feature-pack-for-windows-10-n-october-2017) N edizioni Windows 10 non supportano Windows Mixed Reality e sarà necessario installare una versione diversa da N di Windows 10.

## <a name="my-wmr-environment-is-jittery-or-stutters-when-i-move-my-head-and-displays-double-vision"></a>L'ambiente WMR è instabilità o instabilità quando si sposta la testa e viene visualizzata una doppia visione

In un portatile con grafica integrata e GPU Nvidia, si verifica un errore dopo un periodo di tempo che sembra causare la visualizzazione di un frame precedente dopo il fotogramma successivo, con conseguente doppia visione, più velocemente si sposta la testa in un movimento di sbarrmento, passo o lancio. Il problema sembra essere presente nei driver dopo Nvidia Graphics Driver 436.48.  L'installazione di questo driver consente di risolvere il problema fino a quando Nvidia non risolve il problema nei driver aggiornati. Per un'installazione diretta di Nvidia Graphics Driver 436.48, visitare [NVIDIA.](https://www.nvidia.com/Download/driverResults.aspx/152007/en-us)

## <a name="im-uncomfortable-in-my-headset"></a>Sono contento nel visore VR

Per informazioni generali sul comfort in Windows Mixed Reality, vedi [Windows Mixed Reality, sicurezza e comfort](wmr-health-safety-comfort.md)dei visori VR immersive. Per informazioni dettagliate sul visore VR specifico, rivolgersi al produttore del visore VR.

## <a name="how-can-i-get-a-clearer-view-in-my-headset"></a>Come è possibile ottenere una visualizzazione più chiara nel visore VR?

Provare a regolare l'adattamento del visore VR. Spostarlo verso l'alto e verso il basso, a sinistra e a destra, sul viso e regolare i tasche in modo che sia aderente.

Se il visore VR ha una manopola per regolare la calibrazione, modificarne le impostazioni di calibrazione. In caso contrario, passare a Impostazioni > realtà mista > **qualità** visiva e regolare la calibrazione. Per altre informazioni sulla calibrazione per il dispositivo specifico, rivolgersi al produttore del visore VR.

## <a name="i-frequently-see-a-black-border-around-the-view-in-the-headset-sometimes-its-like-im-looking-down-a-tunnel"></a>Spesso viene visualizzato un bordo nero intorno alla visualizzazione nel visore VR. A volte è come guardare un tunnel

Ciò significa che l'applicazione non è in grado di ottenere la frequenza dei fotogrammi nel PC e il sistema usa fotogrammi vecchi per eseguire il rendering della visualizzazione nel visore. Poiché le applicazioni eseguono il rendering solo della parte del mondo che si sta osservando, se non hanno raggiunto in modo coerente la frequenza dei fotogrammi, il sistema tenterà di eseguire il rendering del mondo da un punto di vista precedente e riempirà i dettagli mancanti con il nero. Se ciò si verifica di frequente:

1. Chiudere o arrestare tutti i programmi non necessario per liberare memoria e CPU.
2. Ridurre le impostazioni dei dettagli nell'applicazione.
3. Passare a **Impostazioni > realtà > visore** visore per ridurre la quantità di dettagli visualizzati nella Windows Mixed Reality home.

## <a name="the-view-in-the-headset-is-jittering-and-stuttering-a-lot"></a>La visualizzazione nel visore è molto instabilità e stuttering

Il sistema potrebbe non essere in grado di eseguire il rendering del contenuto sul visore o il sistema di rilevamento potrebbe riscontrare problemi:

1. Aprire Gestione attività per assicurarsi che il PC abbia risorse di calcolo sufficienti. L'80% della CPU è gratuita, 400 MB di RAM e l'I/O del disco deve essere inferiore all'80%.
2. Assicurarsi di avere i driver di grafica più recenti per l'hardware. Vedere la [sezione relativa al driver di grafica](before-you-start.md#make-sure-you-have-a-compatible-graphics-driver).
3. Assicurarsi che la stanza abbia una luce sufficiente.
4. Scollegare il dispositivo, Windows Mixed Reality e collegarlo di nuovo.
5. Riavvia il PC.
6. Se il problema persiste, contattare il [supporto tecnico.](https://support.microsoft.com/)
---
title: Domande frequenti sul display visore
description: Visualizzare Windows Mixed Reality risoluzione dei problemi di visualizzazione delle cuffia che vanno oltre la documentazione del supporto clienti standard.
author: qianw211
ms.author: v-qianwen
ms.date: 09/30/2020
ms.topic: article
keywords: Windows Mixed Reality, Realtà mista, Realtà virtuale, VR, MR, Risoluzione dei problemi, Errori, Guida, Supporto
appliesto:
- Windows 10 and Windows 11
ms.openlocfilehash: 5a7c7979c9d93d917633cbfed23dc82597368a43
ms.sourcegitcommit: c159bdcf2ada1f45606b10d41ea3adf95109c979
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/04/2021
ms.locfileid: "129436682"
---
# <a name="headset-display-faqs"></a>Domande frequenti sul display visore

## <a name="my-headset-displays-are-black"></a>I display del visore sono di colore nero

* Controllare le prestazioni e la stabilità del PC:
    * Usare il Gestione attività per verificare se i processi esegueno il massimo delle unità CPU, GPU o disco del PC.
    * Controllare i log "Applicazione" e  "Sistema" nei log Visualizzatore eventi > Windows per verificare se un'app si arresta in modo anomalo e genera report Segnalazione errori Windows (WER).
    * Controllare Windows update per assicurarsi che la versione di Windows sia aggiornata. Potrebbe essere necessario selezionare "Controlla aggiornamenti" più volte.
* Controllare la stabilità di app e giochi:
    * Assicurarsi che il PC soddisfi i requisiti minimi di sistema di qualsiasi app o gioco non in esecuzione correttamente.
    * Assicurarsi che la versione del driver GPU sia recente e verificare la presenza di nuovi problemi di prestazioni e compatibilità e regressioni sui nuovi driver.
    * Se si usano app e giochi di SteamVR, assicurarsi che i componenti di SteamVR e Windows Mixed Reality per i componenti di SteamVR siano aggiornati.
* Verificare la compatibilità dell'adattatore HDMI:
    * Assicurarsi che il cavo HDMI sia collegato in tutto il modo.
    * Se si usa un adattatore HDMI,ad esempio un adattatore Mini DisplayPort per HDMI, assicurarsi che sia compatibile con Windows Mixed Reality. L'adattatore deve supportare HDMI 2.0 e sono presenti molte schede meno recenti che supportano solo 1080p. Vedere [Schede consigliate per Windows Mixed Reality](recommended-adapters-for-windows-mixed-reality-capable-pcs.md).
    * L'ordine dei plug può essere importante. Connessione l'adattatore HDMI al PC prima di connettere il visore all'adattatore, soprattutto se si usa un adattatore DA USB-C a HDMI.
    * Provare a rimuovere i cavi di estensione se vengono in uso.
* Verificare la compatibilità della scheda grafica e del driver:
    * Provare la porta HDMI del PC con un monitor PC. Alcuni PC possono avere più di una porta HDMI e non tutti possono essere attivi.
    * Se il PC ha un'unità di elaborazione grafica integrata (iGPU) e un'unità di elaborazione grafica discreta (dGPU), assicurarsi di essere collegati alla porta HDMI della dGPU.
    * Controllare la versione del driver GPU. Assicurarsi che sia recente, ma anche prestare attenzione a eventuali nuovi problemi di prestazioni e compatibilità e regressioni sui nuovi driver.
    * Se si usa Mixed Reality in un computer portatile ed è stato installato un driver di grafica più recente dal sito Web del produttore della scheda grafica, provare a eseguire il downgrade al driver della scheda grafica più recente disponibile nel sito Web del produttore del PC o in Windows Update.
    * Se si dispone di più monitor PC connessi al PC, provare a disconnettere temporaneamente tutti i monitor, ma uno solo.
    * Se è stata impostata una frequenza di aggiornamento personalizzata per il monitor PC, provare a ripristinare temporaneamente una frequenza di aggiornamento standard, ad esempio 60 Hz.
    * Se la scheda grafica è stata modificata di recente senza reinstallare Windows, verificare che nel monitor visore sia ancora installato il driver corretto. Con il visore collegato, verificare che "Visore realtà mista" sia elencato nel nodo Monitoraggi in Gestione dispositivi.
    * Se il PC ha una scheda grafica Nvidia, assicurarsi che il software 3D Vision di Nvidia sia disabilitato.
    * In alcune schede grafiche (in particolare le schede meno recenti), la porta HDMI potrebbe non supportare HDMI 2.0 o non essere completamente compatibile con Windows Mixed Reality. Provare a usare DisplayPort della scheda grafica con un [adattatore DisplayPort da 1.2 a HDMI 2.0.](recommended-adapters-for-windows-mixed-reality-capable-pcs.md)
    * I PC HP Omen con numero di prodotto HP 1RJ99EA#HASHTAG hanno porte HDMI incompatibili con Windows Mixed Reality (aprire "HP Support Assistant" e il numero verrà elencato nella parte inferiore dell'app).
    * Se il PC ha una scheda grafica amD R9 e si usa un visore Samsung Mixed Reality, aggiornare il firmware del visore alla versione 1.0.8 o successiva per usare la porta HDMI della scheda grafica con il visore.
    * Se si usa un Surface Book 2, assicurarsi di usare l'adattatore [Da USB-C a HDMI di Surface.](recommended-adapters-for-windows-mixed-reality-capable-pcs.md)
* Verificare la presenza di un problema hardware del visore vr in realtà mista:
    * Per verificare o escludere i problemi hardware con il visore, connettere il visore di realtà mista a un altro PC.
    * Verificare prima la compatibilità del PC e i problemi di configurazione, in quanto i sintomi sono simili.
* Assicurarsi che il cavo USB sia collegato a una porta USB 3.0 o superiore. Accanto alle porte USB 3.0 sono presenti SS (Super Speed) e spesso sono colorate di blu.

## <a name="my-headset-display-occasionally-turns-black-after-some-use"></a>Il mio visore diventa occasionalmente nero dopo un uso

* Provare a disabilitare le funzionalità di sospensione o risparmio energia USB nel PC. Ad esempio, in Impostazioni > Sistema > Power & Sospensione **> [USB](/windows-hardware/drivers/usbcon/usb-selective-suspend)** sospensione selettiva , l'impostazione "Consenti al computer di spegnere questo dispositivo per risparmiare energia" in Gestione dispositivi e qualsiasi impostazione di risparmio energia USB nel firmware del PC.
* Disconnettere temporaneamente tutti gli altri dispositivi USB e le periferiche connesse al PC.
* Verificare che la versione del driver GPU sia recente e verificare la presenza di nuovi problemi di prestazioni e compatibilità e regressioni sui nuovi driver.

## <a name="one-of-the-displays-on-my-headset-is-black"></a>Uno dei display sul visore è nero

* Se si usa un adattatore HDMI, assicurarsi che supporti HDMI 2.0.
* Rimuovere eventuali cavi di estensione USB e HDMI in uso.
* Assicurarsi che il driver di grafica sia aggiornato.
* Provare il visore di realtà mista in un altro PC.

## <a name="my-headset-displays-turn-blue-and-then-mixed-reality-portal-reinitializes"></a>Il visore visualizza il blu e quindi Portale realtà mista reinizializza

Ciò indica in genere un problema occasionale di affidabilità del controller USB nel PC:

* Provare un'altra porta USB. Il PC può avere più controller USB 3.0.
* Rimuovere eventuali cavi di estensione (se applicabile).
* Scollegare tutti gli altri dispositivi USB dal PC.
* Connessione un hub USB 3.0 alimentato esternamente al PC e connettere il visore all'hub.
* Se si usa un PC desktop, è consigliabile acquistare una scheda PCIe USB 3.0 per aggiungere un altro controller USB al PC.

## <a name="my-headset-causes-my-pc-to-hang-or-show-a-black-screen-while-starting-up"></a>L'headset causa il blocco del PC o la visualizzazione di uno schermo nero durante l'avvio

In alcuni PC, lasciare il visore collegato prima di accendere o durante il riavvio del PC può interferire con il processo di avvio. Il PC può selezionare gli schermi del visore come "monitoraggio primario" per visualizzare lo stato di avvio del PC, non avviarsi correttamente o "bloccarsi" o generare un codice di errore di segnalazione. Il comportamento dipende dalla progettazione e dal modello del PC o dal modello della scheda grafica. Per risolvere il problema:

* Connessione il visore a una porta diversa nella scheda grafica (potrebbe essere necessario usare un adattatore per usare le altre porte).
* Assicurarsi che il firmware BIOS/UEFI del PC sia aggiornato (ma aggiornare il firmware BIOS/UEFI del PC solo se si ha familiarità con questa operazione).

## <a name="my-pc-or-headset-displays-flicker-flash-or-remain-black-when-using-a-surface-pc"></a>Il PC o l'headset visualizza uno sfarfallio, un flash o rimane nero quando si usa un PC Surface

* Assicurarsi di usare un adattatore HDMI che supporta HDMI 2.0. Molti adattatori HDMI meno recenti supportano solo la risoluzione 1080p, che non è sufficiente per i visori di realtà mista.
* Assicurarsi che il driver di grafica sia aggiornato. Controllare Windows Update e il sito Web del produttore del PC per un driver di grafica aggiornato.
* Alcuni dispositivi Surface non sono compatibili con Windows Mixed Reality. Altre informazioni sulla [compatibilità e i requisiti di Surface.](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#windows-mixed-reality-and-surface)

## <a name="my-headset-display-doesnt-work-after-i-shut-down-and-do-a-fast-startup"></a>Lo schermo del visore non funziona dopo l'arresto e l'avvio rapido

Scollegare il cavo HDMI e il cavo USB dal visore e quindi collegarli nuovamente.

## <a name="my-headset-displays-are-choppy-but-mixed-reality-portals-preview-window-appears-fine"></a>I display del visore sono snodato, Portale realtà mista la finestra di anteprima del visore viene visualizzata correttamente

* Assicurarsi che le risorse di sistema del PC (CPU, memoria e disco rigido) siano disponibili e non utilizzate da un'altra app o processo.
* Aggiornare il driver di grafica.

## <a name="im-getting-a-the-install-class-is-not-present-or-is-invalid-error-in-device-manager"></a>Viene visualizzato un errore "La classe di installazione non è presente o non è valida" in Gestione dispositivi

Se viene visualizzato "HoloLens sensori" con un punto esclamativo giallo in Gestione dispositivi, selezionare il dispositivo per altri dettagli. Se viene visualizzato il messaggio "I driver per questo dispositivo non sono installati. (Codice 28): la classe di installazione non è presente o non è valida" perché il PC esegue Windows 10 [N](https://support.microsoft.com/en-us/help/4039813/media-feature-pack-for-windows-10-n-october-2017). Le edizioni N di Windows 10 e Windows 11 non supportano Windows Mixed Reality ed è necessario installare una versione non N di Windows 10 o Windows 11.

## <a name="my-wmr-environment-is-jittery-or-stutters-when-i-move-my-head-and-displays-double-vision"></a>L'ambiente WMR è instabilità o instabilità quando si sposta la testa e viene visualizzata una doppia visione

In un computer portatile con grafica integrata e una GPU Nvidia, si verifica un errore dopo un periodo di tempo che sembra causare la visualizzazione di un frame precedente dopo il frame successivo, con conseguente doppia visione più veloce si sposta la testa in un movimento di sbadiglio, passo o rullo. Il problema sembra essere nei driver dopo Nvidia Graphics Driver 436.48.  L'installazione di questo driver risolverà il problema fino a quando Nvidia non risolverà il problema nei driver aggiornati. Per un'installazione diretta di Nvidia Graphics Driver 436.48, visitare [NVIDIA](https://www.nvidia.com/Download/driverResults.aspx/152007/en-us).

## <a name="im-uncomfortable-in-my-headset"></a>I'm disagi nel visore

Per informazioni generali sul comfort in Windows Mixed Reality, vedere Windows Mixed Reality vr immersive per la [salute, la sicurezza e il comfort.](wmr-health-safety-comfort.md) Per informazioni dettagliate sul visore specifico, contattare il produttore del visore.

## <a name="how-can-i-get-a-clearer-view-in-my-headset"></a>Come è possibile ottenere una visualizzazione più chiara nel visore

Provare a regolare la misura del visore. Spostarlo verso l'alto e verso il basso, a sinistra e a destra, sul viso e regolare le cinghie in modo che si senta aderente.

Se il visore ha una manopola per regolare la calibrazione, regolarne le impostazioni di calibrazione. In caso contrario, passare a Impostazioni > realtà mista > **qualità** visiva e regolare la calibrazione. Per altre informazioni sulla calibrazione per il dispositivo specifico, contattare il produttore del visore.

## <a name="i-frequently-see-a-black-border-around-the-view-in-the-headset-sometimes-its-like-im-looking-down-a-tunnel"></a>Spesso viene visualizzato un bordo nero intorno alla visualizzazione nel visore. A volte è come guardare un tunnel

Ciò significa che l'applicazione non è in grado di ottenere la frequenza dei fotogrammi nel PC e il sistema usa fotogrammi vecchi per eseguire il rendering della visualizzazione nel visore. Poiché le applicazioni eseguono il rendering solo della parte del mondo che si sta osservando, se non hanno raggiunto in modo coerente la frequenza dei fotogrammi, il sistema tenterà di eseguire il rendering del mondo da un punto di vista precedente e riempirà i dettagli mancanti con il nero. Se ciò si verifica di frequente:

1. Chiudere o arrestare tutti i programmi non necessario per liberare memoria e CPU.
2. Ridurre le impostazioni dei dettagli nell'applicazione.
3. Passare a **Impostazioni > realtà > visore** visore per ridurre la quantità di dettagli visualizzati nella Windows Mixed Reality home.

## <a name="the-view-in-the-headset-is-jittering-and-stuttering-a-lot"></a>La visualizzazione nel visore è molto instabilità e stuttering

Il sistema potrebbe non essere in grado di eseguire il rendering del contenuto sul visore o il sistema di rilevamento potrebbe riscontrare problemi:

1. Aprire Gestione attività per assicurarsi che il PC abbia risorse di calcolo sufficienti. L'80% della CPU è gratuita, 400 MB di RAM e l'I/O del disco deve essere inferiore all'80%.
2. Assicurarsi di avere i driver di grafica più recenti per l'hardware. Vedere la [sezione relativa al driver di grafica](before-you-start.md#make-sure-you-have-a-compatible-graphics-driver).
3. Assicurarsi che la stanza abbia una luce sufficiente.
4. Scollegare il dispositivo, chiudere Windows Mixed Reality e collegarlo di nuovo.
5. Riavvia il PC.
6. Se il problema persiste, contattare il [supporto tecnico.](https://support.microsoft.com/)
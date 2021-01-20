---
title: Domande frequenti sulla visualizzazione dell'auricolare
description: Visualizza la risoluzione dei problemi di Windows Mixed Reality per i problemi di visualizzazione dell'auricolare che va oltre la documentazione standard del supporto clienti.
author: hferrone
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Realtà mista di Windows, realtà mista, realtà virtuale, VR, MR, risoluzione dei problemi, errori, guida, supporto
appliesto:
- Windows 10
ms.openlocfilehash: f448cafe3d0952ada63d545e44b58001779a1470
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/20/2021
ms.locfileid: "98580512"
---
# <a name="headset-display-faqs"></a>Domande frequenti sulla visualizzazione dell'auricolare

## <a name="my-headset-displays-are-black"></a>I display dell'auricolare sono neri

* Verificare le prestazioni e la stabilità del PC:
    * Utilizzare Gestione attività per verificare se sono presenti processi che trafugata la CPU, la GPU o le unità disco del computer.
    * Controllare i log "applicazione" e "sistema" in **Visualizzatore eventi > registri di Windows** per verificare se un'app è in arresto anomalo e genera segnalazione errori Windows (WER) report.
    * Controllare Windows Update per assicurarsi che la versione di Windows sia aggiornata. Potrebbe essere necessario selezionare più volte "Verifica disponibilità di aggiornamenti".
* Controllare la stabilità di app e giochi:
    * Verificare che il PC soddisfi i requisiti minimi di sistema di qualsiasi app o gioco non eseguito correttamente.
    * Verificare che la versione del driver GPU sia recente e verificare la presenza di nuovi problemi di prestazioni e compatibilità e regressioni sui nuovi driver.
    * Se usi app e giochi SteamVR, assicurati che SteamVR e la realtà mista di Windows per i componenti SteamVR siano aggiornati.
* Verifica compatibilità scheda HDMI:
    * Verificare che il cavo HDMI sia collegato in tutti i modi.
    * Se si usa una scheda HDMI (ad esempio, una mini-DisplayPort alla scheda HDMI), assicurarsi che sia compatibile con la realtà mista di Windows. L'adapter deve supportare HDMI 2,0 e sono disponibili molti schede meno recenti che supportano solo 1080p. Vedere [Adapter consigliati per la realtà mista di Windows](recommended-adapters-for-windows-mixed-reality-capable-pcs.md).
    * L'ordine del plug può essere importante. Connettere la scheda HDMI al PC prima di connettere l'auricolare alla scheda, soprattutto se si usa un adattatore da USB a HDMI.
    * Se vengono usati, provare a rimuovere i cavi di estensione.
* Controllare la compatibilità della scheda grafica e del driver:
    * Provare la porta HDMI del PC con un monitor di PC. Alcuni PC possono avere più di una porta HDMI e non tutti possono essere attivi.
    * Se il PC ha un'unità di elaborazione grafica integrata (iGPU) e un'unità di elaborazione grafica discreta (dGPU), assicurarsi di essere connessi alla porta HDMI di dGPU.
    * Controllare la versione del driver della GPU. Assicurarsi che sia recente, ma anche prestare attenzione a eventuali nuovi problemi di prestazioni e compatibilità e regressioni per i nuovi driver.
    * Se si usa la realtà mista in un portatile ed è stato installato un driver grafico più recente dal sito Web del produttore della scheda grafica, provare a effettuare il downgrade al driver della scheda grafica più recente disponibile sul sito Web del produttore del computer o su Windows Update.
    * Se sono presenti più monitor PC connessi al PC, provare a disconnettere temporaneamente tutti i monitor tranne un PC.
    * Se è stata impostata una frequenza di aggiornamento personalizzata per il monitor del PC, provare a ripristinare temporaneamente una frequenza di aggiornamento standard, ad esempio 60 Hz.
    * Se la scheda grafica è stata modificata di recente senza reinstallare Windows, verificare che nel monitor cuffia sia ancora installato il driver corretto. Con la cuffia collegata, verificare che "Mixed Reality headset" sia elencato nel nodo monitoraggi in Device Manager.
    * Se il PC ha una scheda grafica NVIDIA, verificare che il software per la visione 3D di NVIDIA sia disabilitato.
    * In alcune schede grafiche (soprattutto le schede meno recenti), è possibile che la porta HDMI non supporti HDMI 2,0 o non sia completamente compatibile con la realtà mista di Windows. Provare a usare DisplayPort della scheda grafica con una [scheda displayport 1,2 per HDMI 2,0](recommended-adapters-for-windows-mixed-reality-capable-pcs.md).
    * I PC HP Omen con numero di prodotto HP 1RJ99EA # ABU hanno porte HDMI non compatibili con la realtà mista di Windows (aprire "supporto tecnico HP" e il numero verrà elencato nella parte inferiore dell'app).
    * Se il PC ha una scheda grafica della serie AMD R9 e si usa una cuffia da Samsung Mixed Reality, aggiornare il firmware dell'auricolare alla versione 1.0.8 o successiva per usare la porta HDMI della scheda grafica con l'auricolare.
    * Se si usa una superficie del libro 2, assicurarsi di usare la [superficie USB-C alla scheda HDMI](recommended-adapters-for-windows-mixed-reality-capable-pcs.md).
* Verificare la presenza di un problema hardware della cuffia reale mista:
    * Per confermare o escludere problemi hardware con l'auricolare, connettere l'auricolare della realtà mista a un altro computer.
    * Verificare prima di tutto la compatibilità dei PC e i problemi di installazione, in quanto i sintomi sono simili.
* Verificare che il cavo USB sia collegato a una porta USB 3,0 o superiore. Le porte USB 3,0 dispongono di SS (Super Speed) accanto a esse e spesso sono colorate blu.

## <a name="my-headset-display-occasionally-turns-black-after-some-use"></a>Il display dell'auricolare viene occasionalmente trasformato in nero dopo un certo utilizzo

* Provare a disabilitare eventuali funzionalità di sospensione o risparmio di energia USB nel PC. Ad esempio, in **impostazioni > sistema > Power & sospensione > [sospensione selettiva USB](/windows-hardware/drivers/usbcon/usb-selective-suspend)**, l'impostazione "Consenti al computer di disattivare questo dispositivo per risparmiare energia" in Device Manager e tutte le impostazioni di risparmio energia USB nel firmware del PC.
* Disconnettere temporaneamente eventuali altri dispositivi USB e periferiche connesse al PC.
* Verificare che la versione del driver GPU sia recente e verificare la presenza di nuovi problemi di prestazioni e compatibilità e regressioni sui nuovi driver.

## <a name="one-of-the-displays-on-my-headset-is-black"></a>Uno degli schermi dell'auricolare è nero

* Se si usa una scheda HDMI, assicurarsi che supporti HDMI 2,0.
* Rimuovere tutti i cavi di estensione USB e HDMI che potrebbero essere in uso.
* Verificare che il driver di grafica sia aggiornato.
* Provare l'auricolare della realtà mista in un altro computer.

## <a name="my-headset-displays-turn-blue-and-then-mixed-reality-portal-reinitializes"></a>L'auricolare diventa blu, quindi il portale per la realtà mista viene reinizializzato

Questo indica in genere un problema di affidabilità del controller USB occasionale nel PC:

* Provare con un'altra porta USB. Il PC potrebbe avere più controller USB 3,0.
* Rimuovere eventuali cavi di estensione (se applicabile).
* Scollegare tutti gli altri dispositivi USB dal PC.
* Connettere un hub USB 3,0 alimentato esternamente al PC e connettere la cuffia all'hub.
* Se si usa un PC desktop, prendere in considerazione l'acquisto di una scheda PCI USB 3,0 per aggiungere un altro controller USB al PC.

## <a name="my-headset-causes-my-pc-to-hang-or-show-a-black-screen-while-starting-up"></a>L'auricolare causa il blocco del PC o la visualizzazione di una schermata nera durante l'avvio

In alcuni PC, l'auricolare collegato prima di accendere o durante il riavvio del PC potrebbe interferire con il processo di avvio. Il PC potrebbe selezionare la cuffia da visualizzare come "monitoraggio principale" per mostrare lo stato di avanzamento dell'avvio del PC, non avviarsi correttamente oppure "bloccarsi" o produrre un codice di errore acustico. Il comportamento dipende dalla marca e dal modello del PC o dalla marca e dal modello della scheda grafica. Per risolvere il problema:

* Connettere la cuffia a una porta diversa nella scheda grafica. potrebbe essere necessario usare un adapter per usare le altre porte.
* Verificare che il firmware BIOS/UEFI del PC sia aggiornato (ma aggiornare solo il firmware BIOS/UEFI del PC se si è abituati).

## <a name="my-pc-or-headset-displays-flicker-flash-or-remain-black-when-using-a-surface-pc"></a>Il PC o l'auricolare Visualizza sfarfallio, Flash o rimane nero quando si usa un PC Surface

* Assicurarsi di usare una scheda HDMI che supporti HDMI 2,0. Molti adapter HDMI precedenti supportano solo la risoluzione 1080p, che non è sufficiente per le cuffie con realtà mista.
* Verificare che il driver grafico sia aggiornato. Controllare Windows Update e il sito Web del produttore del PC per un driver di grafica aggiornato.
* Alcuni dispositivi della superficie non sono compatibili con la realtà mista di Windows. Altre informazioni sulla [compatibilità e sui requisiti di Surface](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#windows-mixed-reality-and-surface).

## <a name="my-headset-display-doesnt-work-after-i-shut-down-and-do-a-fast-startup"></a>La visualizzazione dell'auricolare non funziona dopo l'arresto e l'avvio rapido

Scollegare il cavo HDMI e il cavo USB dall'auricolare, quindi ricollegarlo.

## <a name="my-headset-displays-are-choppy-but-mixed-reality-portals-preview-window-appears-fine"></a>I display dell'auricolare sono invariati, ma la finestra di anteprima del portale di realtà mista sembra corretta

* Assicurarsi che le risorse di sistema del computer (CPU, memoria e disco rigido) siano disponibili e non utilizzate da un'altra app o da un altro processo.
* Aggiornare il driver della grafica.

## <a name="im-getting-a-the-install-class-is-not-present-or-is-invalid-error-in-device-manager"></a>Viene visualizzato l'errore "la classe di installazione non è presente o non è valida" in Device Manager

Se si visualizzano "sensori HoloLens" con un punto esclamativo giallo in Device Manager, selezionare il dispositivo per ulteriori dettagli. Se viene visualizzato un messaggio che informa che i driver per il dispositivo non sono installati. (Codice 28): la classe install non è presente o non è valida ", questo è in genere dovuto al fatto che il PC esegue [Windows 10 N](https://support.microsoft.com/en-us/help/4039813/media-feature-pack-for-windows-10-n-october-2017). Le edizioni di Windows 10 non supportano la realtà mista di Windows ed è necessario installare una versione non N di Windows 10.

## <a name="my-wmr-environment-is-jittery-or-stutters-when-i-move-my-head-and-displays-double-vision"></a>L'ambiente WMR è nervoso o balbetta quando sposto la mia testa e visualizza una doppia visione

In un computer portatile con una grafica integrata e una GPU NVIDIA, si verifica un errore dopo un periodo di tempo che sembra causare la visualizzazione di un frame precedente dopo il frame successivo, con una doppia visione più veloce, in modo da spostare la testa in un movimento di imbardata, pitch o Roll. Il problema sembra essere sui driver dopo il driver di grafica NVIDIA 436,48.  L'installazione di questo driver risolverà il problema fino a quando NVIDIA non risolve il problema nei driver aggiornati. Per un'installazione diretta di NVIDIA graphics driver 436,48, visitare [NVIDIA](https://www.nvidia.com/Download/driverResults.aspx/152007/en-us).

## <a name="im-uncomfortable-in-my-headset"></a>Sono scomodo nell'auricolare

Per informazioni generali sulla comodità nella realtà mista di Windows, vedere la pagina relativa all' [integrità, alla sicurezza e alla comodità dell'auricolare misto](wmr-health-safety-comfort.md)di Windows. Per informazioni dettagliate sull'auricolare specifico, rivolgersi al produttore dell'auricolare.

## <a name="how-can-i-get-a-clearer-view-in-my-headset"></a>Come è possibile ottenere una visualizzazione più chiara nell'auricolare

Provare a modificare l'adattamento dell'auricolare. Spostarla verso l'alto e verso il basso, a sinistra e a destra, e regolare le cinghie in modo che risultino accoglienti.

Se la cuffia ha una manopola per regolare la calibrazione, modificare le impostazioni di calibrazione. In caso contrario, passare a **impostazioni > realtà mista > qualità visiva** e regolare la calibrazione in tale posizione. Per ulteriori informazioni sulla calibrazione per un dispositivo specifico, rivolgersi al produttore dell'auricolare.

## <a name="i-frequently-see-a-black-border-around-the-view-in-the-headset-sometimes-its-like-im-looking-down-a-tunnel"></a>Spesso viene visualizzato un bordo nero attorno alla visualizzazione dell'auricolare. A volte è come si sta cercando un tunnel

Ciò significa che l'applicazione non è in grado di raggiungere la frequenza dei fotogrammi nel PC e il sistema usa i vecchi frame per eseguire il rendering della visualizzazione nell'auricolare. Poiché le applicazioni eseguono solo il rendering della parte del mondo che si sta osservando, se non soddisfano costantemente la frequenza dei fotogrammi, il sistema tenterà di eseguire il rendering del mondo da un punto di vista precedente e fornirà i dettagli mancanti con il nero. Se il problema si verifica di frequente:

1. Chiudere o arrestare tutti i programmi non necessari per liberare memoria e CPU.
2. Ridurre le impostazioni dei dettagli nell'applicazione.
3. Passare a **impostazioni > la realtà mista > visualizzazione della cuffia** per ridurre la quantità di dettaglio visualizzata nella Home realtà mista di Windows.

## <a name="the-view-in-the-headset-is-jittering-and-stuttering-a-lot"></a>La visualizzazione nell'auricolare sta per essere nervosa e balbettare molto

Il sistema potrebbe non essere in grado di eseguire il rendering del contenuto nell'auricolare oppure è possibile che si verifichino problemi nel sistema di rilevamento:

1. Aprire Gestione attività per assicurarsi che il PC disponga di risorse di calcolo sufficienti. È necessario disporre del 80% di CPU disponibile, 400 MB di RAM e i/o del disco devono essere inferiori al 80%.
2. Assicurarsi di disporre dei driver grafici più recenti per l'hardware. Vedere la [sezione driver grafica](before-you-start.md#make-sure-you-have-a-compatible-graphics-driver).
3. Assicurarsi che la stanza abbia una luce sufficiente.
4. Scollegare il dispositivo, chiudere la realtà mista di Windows e ricollegarlo.
5. Riavvia il PC.
6. Se il problema persiste, contattare il [supporto](https://support.microsoft.com/)tecnico.
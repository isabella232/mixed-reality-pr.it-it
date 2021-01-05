---
title: App di controllo del PC con la realtà mista di Windows
description: Come trovare e usare l'app di controllo PC di realtà mista di Windows per testare la compatibilità del PC prima di acquistare un auricolare con la realtà mista di Windows.
author: hferrone
ms.author: v-hferrone
ms.date: 09/16/2020
ms.topic: article
keywords: Realtà mista di Windows, realtà mista, realtà virtuale, VR, MR, compatibile, compatibilità, PC, requisiti di sistema
appliesto:
- Windows 10
ms.openlocfilehash: 6dc187b14950f1446fd5e60c3e6db10fd2c3ce25
ms.sourcegitcommit: 1b90f27af091dffd4fba63d69a89873aa0f75079
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2020
ms.locfileid: "97725432"
---
# <a name="windows-mixed-reality-pc-check-app"></a>App di controllo del PC con la realtà mista di Windows

L'app di **[controllo PC Windows Mixed Reality](https://www.microsoft.com/store/p/windows-mixed-reality-pc-check/9nzvl19n7cnc)** è il modo migliore per verificare che il PC sia pronto per l'esecuzione di realtà mista di Windows. L'app di controllo PC Windows Mixed Reality funziona solo nei PC con almeno Windows 10 versione 1607 installata. Per controllare la versione di Windows, digitare "winver" nella barra di ricerca ed eseguire il comando. Per le versioni di Windows 10 precedenti alla 1607, l'app viene comunque visualizzata nello Store, ma viene visualizzato un errore quando si tenta di installare.

<a href="https://www.microsoft.com/store/productid/9NZVL19N7CNC"><img alt="Download Windows Mixed Reality PC Check app" src="images/WMR-PC-Check-app.png"/></a>

Dopo aver eseguito l'app, si otterrà uno dei messaggi seguenti:

* **Si è pronti per iniziare.** Il PC ha il necessario per eseguire la realtà mista di Windows.
* **Ci siamo quasi.** Questo computer può eseguire la realtà mista di Windows, ma alcune funzionalità potrebbero essere limitate.
* **Non è possibile eseguire la realtà mista.** Questo PC non soddisfa i requisiti minimi necessari per eseguire la realtà mista di Windows.

Si otterrà quindi un'analisi del PC con l'hardware, i driver e il sistema operativo necessari.
![Screenshot del controllo del PC con la realtà mista di Windows](images/screenshot-mr-pc-check.jpg) 

<table>
<tr>
<th>Icona</th><th>Significato</th>
</tr><tr>
<td> <img alt="Succeeded" width="30" height="30" src="images/glyph-succeeded.png" /></td><td style="vertical-align: middle">Il PC passa l'elemento richiesto.</td>
</tr><tr>
<td> <img alt="Warning" width="30" height="30" src="images/glyph-warning.png" /></td><td style="vertical-align: middle">Potrebbero verificarsi problemi con il PC per il requisito specificato. Se si verificano problemi, potrebbe essere necessario risolvere i problemi o aggiornare il computer.</td>
</tr><tr>
<td> <img alt="Error" width="30" height="30" src="images/glyph-error.png" /></td><td style="vertical-align: middle">Il PC non soddisfa i requisiti per l'elemento specificato.</td>
</tr>
</table>

## <a name="get-help-with-windows-mixed-reality-pc-check-results"></a>Ottenere assistenza con i risultati del controllo del PC con la realtà mista di Windows

Si otterrà un report di compatibilità quando si configura la realtà mista di Windows o si esegue l'app di controllo del PC Windows Mixed Reality nel computer. Di seguito sono riportati alcuni dettagli su ciò che è possibile vedere.

### <a name="youre-good-to-go"></a>![Si è pronti per iniziare](images/glyph-succeeded.png)

Ottime notizie: il PC può eseguire la realtà mista di Windows. Tenere presente che è ancora presente una variazione tra l'hardware e la configurazione del computer. L'esperienza di realtà mista potrebbe non essere la stessa in tutti i PC.

>[!NOTE]
>Se viene visualizzato il messaggio "questa configurazione hardware potrebbe funzionare con la realtà mista di Windows, ma non è ancora stata testata", potrebbe verificarsi alcuni problemi di prestazioni quando si esegue la realtà mista di Windows per sessioni lunghe.

### <a name="youre-nearly-there"></a>![Ci siamo quasi](images/glyph-warning.png)

Il PC dovrebbe essere in grado di eseguire la realtà mista di Windows, ma potrebbe non offrire la migliore esperienza possibile. La grafica può essere ritardata, alcune app e giochi potrebbero non funzionare correttamente e altri potrebbero non essere eseguiti.

Ecco i messaggi che possono essere visualizzati e le operazioni da eseguire:

#### <a name="this-pc-has-an-integrated-graphics-card-with-single-channel-ram"></a>Questo PC ha una scheda grafica integrata con RAM a canale singolo

Le schede grafiche integrate forniranno la migliore esperienza di realtà mista di Windows nei PC con RAM Dual Channel. Se si verificano problemi di prestazioni:

* Installare una [scheda grafica discreta compatibile](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md).
* Installare un'altra chiavetta RAM per creare la RAM Dual Channel.
* Passa a un [PC compatibile](https://www.microsoft.com/windows/windows-mixed-reality-devices).

#### <a name="this-pc-has-a-hybrid-graphics-configuration-with-an-incompatible-pcie-link"></a>Questo PC ha una configurazione grafica ibrida con un collegamento PCIe non compatibile

PCIe sta per il *componente periferico Interconnect Express*. Si tratta della connessione utilizzata da un PC per comunicare con una scheda grafica. La configurazione potrebbe funzionare, ma se si verificano problemi, è necessario passare a un [PC compatibile](https://www.microsoft.com/windows/windows-mixed-reality-devices).

#### <a name="this-pcs-graphics-driver-might-not-work-well-with-windows-mixed-reality"></a>Il driver grafico di questo PC potrebbe non funzionare correttamente con la realtà mista di Windows

Se si verificano problemi, provare a scaricare un nuovo driver grafico usando Windows Update (**avvia > impostazioni > aggiorna & sicurezza > verificare la disponibilità di aggiornamenti**) o andare al sito Web del produttore del PC o del produttore della scheda grafica.

Se il tentativo non funziona, è necessario aggiungere una [scheda grafica compatibile](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md) o passare a un [PC compatibile](https://www.microsoft.com/windows/windows-mixed-reality-devices).

#### <a name="this-pcs-processor-might-not-work-well-with-windows-mixed-reality"></a>Il processore di questo PC potrebbe non funzionare correttamente con la realtà mista di Windows

Il processore di questo PC potrebbe non funzionare correttamente con la realtà mista di Windows, perché non ha un numero sufficiente di core. Se la realtà mista di Windows non viene eseguita correttamente, eseguire l'aggiornamento a un computer [compatibile o passare](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md) a un [PC compatibile](https://www.microsoft.com/windows/windows-mixed-reality-devices).

#### <a name="this-pc-might-not-have-a-compatible-usb-configuration"></a>Il PC potrebbe non avere una configurazione USB compatibile

Se si verificano problemi con la realtà mista di Windows:

* Collegare la cuffia a una porta USB diversa, se disponibile.
* Se il sistema non funziona, disinstallare il driver USB corrente del PC e reinstallare un driver Microsoft:

1. Selezionare **Start**, quindi digitare **"gestione dispositivi"** nella casella di ricerca.
1. Selezionare **Device Manager** dai risultati.
1. Espandere la categoria per i controller del bus seriale universale, esaminare i dispositivi elencati e disinstallare tutti i driver incompatibili. 
 * Se l'elenco include un elemento "controller host estendibile" senza "Microsoft" alla fine del nome del dispositivo, il driver non è compatibile con la realtà mista di Windows. È necessario disinstallarlo. Per disinstallare un driver, fare clic con il pulsante destro del mouse sul dispositivo nell'elenco e scegliere **Disinstalla dispositivo**. Selezionare la casella **di controllo Elimina il software driver per questo dispositivo** , quindi selezionare **Disinstalla**.
 * Se l'elenco include un elemento "controller host estendibile" che include "Etron" nel nome, il controller USB non è compatibile con la realtà mista di Windows. È necessario usare una porta USB diversa nel PC o acquistare un controller host USB 3,0 diverso.
1. Riavvia il PC. 
1. Tornare a Device Manager e individuare nuovamente l'elemento del controller host estendibile. Se viene visualizzato "Microsoft" alla fine del nome del dispositivo, è possibile iniziare. In caso contrario, ripetere i passaggi di disinstallazione per rimuovere eventuali versioni non Microsoft aggiuntive del driver.
* Se il problema persiste, aggiungere una scheda USB PCIe al PC.

#### <a name="this-pc-doesnt-have-bluetooth-40-for-controllers"></a>Il PC non ha Bluetooth 4,0 per i controller.

#### <a name="this-pc-doesnt-have-a-self-powered-usb-port"></a>Il PC non dispone di una porta USB autoalimentata.

#### <a name="this-pc-should-work-but-youll-have-the-best-experience-with-a-high-performance-intel-processor"></a>Il PC dovrebbe funzionare, ma si avrà la migliore esperienza con un processore Intel® a prestazioni elevate.

### <a name="cant-run-mixed-reality"></a>![Non è possibile eseguire la realtà mista](images/glyph-error.png)

 [Ottenere assistenza con i risultati del controllo del PC con la realtà mista di Windows](https://support.microsoft.com/en-us/help/4045777/windows-10-get-help-with-pc-compatibility-in-windows-mixed-reality)

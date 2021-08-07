---
title: Windows Mixed Reality App PC Check
description: Come trovare e usare l'app Windows Mixed Reality PC Check per testare la compatibilità del PC prima di acquistare un visore Windows Mixed Reality visore.
author: hferrone
ms.author: v-hferrone
ms.date: 09/16/2020
ms.topic: article
keywords: Windows Mixed Reality, realtà mista, realtà virtuale, VR, MR, compatibile, compatibilità, PC, requisiti di sistema
appliesto:
- Windows 10
ms.openlocfilehash: 463e7dfc2c95ed9efc70a87ebbb0dac08b134251401a1114f3b9a364aa197073
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115188046"
---
# <a name="windows-mixed-reality-pc-check-app"></a>Windows Mixed Reality App PC Check

**[L Windows Mixed Reality app PC Check](https://www.microsoft.com/store/p/windows-mixed-reality-pc-check/9nzvl19n7cnc)** è il modo migliore per assicurarsi che il PC sia pronto per l'Windows Mixed Reality. L Windows Mixed Reality'app PC Check funziona solo nei PC con almeno Windows 10 versione 1607 installata. Per controllare la versione di Windows, digitare "winver" nella barra di ricerca ed eseguire il comando . Per Windows 10 precedenti alla 1607, l'app verrà comunque mostrata nello Store, ma verrà visualizzato un errore quando si tenta di eseguire l'installazione.

<a href="https://www.microsoft.com/store/productid/9NZVL19N7CNC"><img alt="Download Windows Mixed Reality PC Check app" src="images/WMR-PC-Check-app.png"/></a>

Dopo aver eseguito l'app, si otterrà uno dei messaggi seguenti:

* **È possibile.** Il PC ha ciò che serve per eseguire Windows Mixed Reality.
* **Ci sei quasi.** Questo PC può essere Windows Mixed Reality, ma alcune funzionalità potrebbero essere limitate.
* **Non è possibile eseguire la realtà mista.** Questo PC non soddisfa i requisiti minimi necessari per eseguire Windows Mixed Reality.

Si otterrà quindi un'analisi del PC rispetto all'hardware, ai driver e al sistema operativo necessari.
![Screenshot di Windows Mixed Reality PC Check](images/screenshot-mr-pc-check.jpg) 

<table>
<tr>
<th>Icona</th><th>Significato</th>
</tr><tr>
<td> <img alt="Succeeded" width="30" height="30" src="images/glyph-succeeded.png" /></td><td style="vertical-align: middle">Il PC passa l'elemento richiesto.</td>
</tr><tr>
<td> <img alt="Warning" width="30" height="30" src="images/glyph-warning.png" /></td><td style="vertical-align: middle">Potrebbero verificarsi problemi con il PC per il requisito specificato. Se si verificano problemi, potrebbe essere necessario risolvere i problemi o aggiornare il PC.</td>
</tr><tr>
<td> <img alt="Error" width="30" height="30" src="images/glyph-error.png" /></td><td style="vertical-align: middle">Il PC non soddisfa i requisiti per l'elemento specificato.</td>
</tr>
</table>

## <a name="get-help-with-windows-mixed-reality-pc-check-results"></a>Ottenere informazioni sui risultati Windows Mixed Reality pc Check

Si otterrà un report di compatibilità quando si configura Windows Mixed Reality o si esegue l'app Windows Mixed Reality PC Check nel computer. Ecco alcuni dettagli su ciò che si potrebbe vedere.

### <a name="youre-good-to-go"></a>![Sei a posto](images/glyph-succeeded.png)

Buone notizie: il PC può essere eseguito Windows Mixed Reality. Tenere presente che esistono ancora differenze tra l'hardware e la configurazione del computer. L'esperienza di realtà mista potrebbe non essere la stessa in ogni PC.

>[!NOTE]
>Se viene visualizzato il messaggio "Questa configurazione hardware potrebbe funzionare con Windows Mixed Reality, ma non è ancora stata testata", si potrebbero verificare alcuni problemi di prestazioni durante l'esecuzione di Windows Mixed Reality per sessioni lunghe.

### <a name="youre-nearly-there"></a>![Ci si è quasi](images/glyph-warning.png)

Il PC dovrebbe essere in grado di eseguire Windows Mixed Reality, ma potrebbe non offrire la migliore esperienza possibile. La grafica può avere un ritardo, alcune app e giochi potrebbero non funzionare bene e alcune potrebbero non funzionare affatto.

Ecco i messaggi che potrebbero essere visualizzati e le relative informazioni:

#### <a name="this-pc-has-an-integrated-graphics-card-with-single-channel-ram"></a>Questo PC ha una scheda grafica integrata con RAM a canale singolo

Le schede grafiche integrate offrono la migliore esperienza Windows Mixed Reality nei PC con RAM a doppio canale. Se si verificano problemi di prestazioni:

* Installare una [scheda grafica discreta compatibile.](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md)
* Installare una stick ram aggiuntiva per creare ram a doppio canale.
* Passare a [un PC compatibile.](https://www.microsoft.com/windows/windows-mixed-reality-devices)

#### <a name="this-pc-has-a-hybrid-graphics-configuration-with-an-incompatible-pcie-link"></a>Questo PC ha una configurazione grafica ibrida con un collegamento PCIe incompatibile

PCIe è *l'acronimo di Peripheral Component Interconnect Express.* Si tratta della connessione utilizzata da un PC per comunicare con una scheda grafica. La configurazione potrebbe funzionare, ma se si verificano problemi, è necessario passare a un [PC compatibile.](https://www.microsoft.com/windows/windows-mixed-reality-devices)

#### <a name="this-pcs-graphics-driver-might-not-work-well-with-windows-mixed-reality"></a>Il driver di grafica di questo PC potrebbe non funzionare correttamente con Windows Mixed Reality

In caso di problemi, provare a scaricare un nuovo driver di grafica usando Windows Update (**Start > Impostazioni > Update & security & security > Check for updates**) oppure visitare il sito Web del produttore del PC o della scheda grafica.

Se non funziona, è necessario aggiungere una [](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md) scheda grafica compatibile o passare a un [PC compatibile.](https://www.microsoft.com/windows/windows-mixed-reality-devices)

#### <a name="this-pcs-processor-might-not-work-well-with-windows-mixed-reality"></a>Il processore di questo PC potrebbe non funzionare correttamente con Windows Mixed Reality

Il processore di questo PC potrebbe non funzionare Windows Mixed Reality, perché non ha un numero sufficiente di core. Se Windows Mixed Reality non funziona bene, eseguire l'aggiornamento [a](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md) uno compatibile o passare a un [PC compatibile.](https://www.microsoft.com/windows/windows-mixed-reality-devices)

#### <a name="this-pc-might-not-have-a-compatible-usb-configuration"></a>Questo PC potrebbe non avere una configurazione USB compatibile

Se si verificano problemi durante l'Windows Mixed Reality:

* Collegare il visore a una porta USB diversa, se disponibile.
* Se non funziona, disinstallare il driver USB corrente del PC e quindi reinstallare un driver Microsoft:

1. Selezionare **Start** e quindi digitare **"gestione dispositivi"** nella casella di ricerca.
1. Selezionare **Gestione dispositivi** nei risultati.
1. Espandere la categoria per controller del bus seriale universale, esaminare i dispositivi elencati e disinstallare eventuali driver incompatibili. 
 * Se l'elenco include un elemento "eXtensible Host Controller" senza "Microsoft" alla fine del nome del dispositivo, il driver non è compatibile con Windows Mixed Reality. È necessario disinstallarlo. Per disinstallare un driver, fare clic con il pulsante destro del mouse sul dispositivo nell'elenco e scegliere **Disinstalla dispositivo**. Selezionare la **casella di controllo Elimina il software driver** per questo dispositivo e quindi selezionare **Disinstalla**.
 * Se l'elenco include un elemento "eXtensible Host Controller" che include "Etron" nel nome, il controller USB non è compatibile con Windows Mixed Reality. È necessario usare una porta USB diversa nel PC o acquistare un controller host USB 3.0 diverso.
1. Riavvia il PC. 
1. Tornare a Gestione dispositivi e individuare di nuovo l'elemento controller host eXtensible. Se ora viene visualizzato "Microsoft" alla fine del nome del dispositivo, è possibile andare. In caso contrario, ripetere i passaggi di disinstallazione per rimuovere eventuali versioni aggiuntive non Microsoft del driver.
* Se il problema persiste, aggiungere una scheda USB PCIe al PC.

#### <a name="this-pc-doesnt-have-bluetooth-40-for-controllers"></a>Questo PC non dispone di Bluetooth 4.0 per i controller.

#### <a name="this-pc-doesnt-have-a-self-powered-usb-port"></a>Questo PC non ha una porta USB autoalimentato.

#### <a name="this-pc-should-work-but-youll-have-the-best-experience-with-a-high-performance-intel-processor"></a>Questo PC dovrebbe funzionare, ma si ha la migliore esperienza con un processore Intel® ad alte prestazioni.

### <a name="cant-run-mixed-reality"></a>![Non è possibile eseguire la realtà mista](images/glyph-error.png)

 [Ottenere informazioni sui risultati Windows Mixed Reality pc Check](https://support.microsoft.com/en-us/help/4045777/windows-10-get-help-with-pc-compatibility-in-windows-mixed-reality)

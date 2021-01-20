---
title: Domande frequenti sulla configurazione di Windows Mixed Reality
description: Risposte alle domande di configurazione comuni quando si utilizzano dispositivi e applicazioni di realtà mista di Windows.
author: hferrone
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Realtà mista di Windows, realtà mista, realtà virtuale, VR, MR, feedback, Hub feedback, bug
appliesto:
- Windows 10
ms.openlocfilehash: 87eb22e600ca2426bdd3fec1fd428c11d9c45313
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/20/2021
ms.locfileid: "98581817"
---
# <a name="windows-mixed-reality-setup-faq"></a>Domande frequenti sulla configurazione di Windows Mixed Reality

Di seguito sono riportate alcune informazioni che consentono di risolvere i problemi che possono verificarsi quando si configura la cuffia mista di Windows per la realtà mista.

## <a name="i-get-a-message-that-says-we-couldnt-download-the-window-mixed-reality-software-or-setup-is-stuck-on-the-hang-tight-while-we-do-some-downloading-page"></a>Viene visualizzato un messaggio che indica che non è stato possibile scaricare il software della realtà mista della finestra, oppure il programma di installazione è bloccato nella pagina "bloccarsi mentre è in corso il download"

Attenersi alla procedura seguente:

* Passare a **impostazioni > aggiorna & sicurezza > Windows Update** e assicurarsi che Windows Update sia attivato. Quindi, scaricare e installare gli aggiornamenti in attesa di installazione.
* Verificare che il PC sia connesso a Internet e che disponga di almeno 2 GB di spazio di archiviazione disponibile.
* Riavviare il computer e riprovare. Potrebbe essere necessario ripetere più volte o eseguire lo strumento di risoluzione dei problemi di Windows Update per cancellare gli aggiornamenti in sospeso.

> [!NOTE]
> * Se si è in una rete gestita dall'organizzazione, rivolgersi all'amministratore. Potrebbe essere necessario abilitare la realtà mista di Windows. Cerchi le istruzioni per professionisti IT? Vedere **[questo articolo](/windows/application-management/manage-windows-mixed-reality)**.
> * Se la connessione di rete Wi-Fi è impostata su a consumo, impostarla su non a consumo. **[Scopri di più](https://support.microsoft.com/help/4028458)**

## <a name="i-get-a-message-that-says-something-went-wrong-and-we-couldnt-start-windows-mixed-reality"></a>Viene visualizzato un messaggio che indica che si è verificato un errore e non è stato possibile avviare la realtà mista di Windows.

Attenersi alla procedura seguente:

1. Scollegare l'auricolare dal computer (entrambi i cavi).
2. Riavviare il computer.
3. Passare a **impostazioni > aggiorna & sicurezza > Windows Update** e assicurarsi che Windows Update sia attivato. Quindi, scaricare e installare gli aggiornamenti in attesa di installazione.
4. Riconnettere l'auricolare al computer, quindi riprovare a eseguire l'installazione.

Se i passaggi precedenti non funzionano, provare a disinstallare e reinstallare la realtà mista di Windows. Passare a **impostazioni > realtà mista > disinstallare** e selezionare **Disinstalla**. Riavviare quindi il computer. Per avviare nuovamente il processo di installazione, è sufficiente collegare la cuffia al PC.

## <a name="the-mixed-reality-portal-doesnt-open-when-i-plug-in-my-headset"></a>Il portale per la realtà mista non si apre quando si collega l'auricolare

Il portale per la realtà mista, l'app che consente di configurare la realtà mista di Windows, è progettata per l'apertura automatica quando si collega un auricolare compatibile. Se non si apre, passare a Start e digitare "Mixed Reality Portal" nella casella di ricerca per aprire l'app. Potrebbe essere necessario eseguire l' [aggiornamento alla versione più recente di Windows](https://support.microsoft.com/en-us/help/12373/windows-update-faq) , se non si riesce a trovare il portale di realtà mista.

## <a name="i-get-a-message-that-says-my-pc-cant-run-windows-mixed-reality"></a>Viene visualizzato un messaggio che indica che il PC non può eseguire la realtà mista di Windows

Se si riceve questo messaggio, il PC non soddisfa i [requisiti minimi](https://support.microsoft.com/help/4039260) necessari per eseguire la realtà mista di Windows. La configurazione hardware del computer potrebbe non essere compatibile con la realtà mista di Windows o potrebbe essere necessario eseguire [l'aggiornamento alla versione più recente di Windows](https://support.microsoft.com/help/12373).

Note sulle schede grafiche:

* Se la configurazione della realtà mista di Windows indica che la scheda grafica non soddisfa i requisiti e si ritiene che sia presente, assicurarsi che l'auricolare sia collegato alla scheda corretta.
* Rivolgersi al produttore della scheda grafica per l'aggiornamento del driver più recente. Per la realtà mista di Windows è necessario un driver di scheda grafica che supporta almeno WDDM 2,2.

## <a name="i-get-a-message-that-says-youre-nearly-therethis-pc-doesnt-meet-the-minimum-requirements-needed-to-run-windows-mixed-reality"></a>Viene visualizzato un messaggio che indica che il PC non soddisfa i requisiti minimi necessari per l'esecuzione della realtà mista di Windows.

Se si riceve questo messaggio, il PC non soddisfa i requisiti minimi necessari per la migliore esperienza nella realtà mista di Windows. Il PC può eseguire un auricolare immersivo, ma potrebbe non essere in grado di eseguire determinate app o potrebbe avere problemi con le prestazioni.

## <a name="my-xbox-controller-isnt-working"></a>Il controller Xbox non funziona

Attenersi alla procedura seguente:

* Verificare che il controller sia acceso, completamente addebitato e connesso al PC.
* Sostituire le batterie del controller.
* Se si usa un controller Bluetooth, passare a **impostazioni > dispositivi > Bluetooth & altri dispositivi** nel PC e assicurarsi che sia associato (dovrebbe essere visualizzato nella pagina).

[Altre informazioni sui controller Xbox](https://support.xbox.com/xbox-on-windows/accessories/connect-xbox-one-controller-to-pc)

## <a name="my-motion-controllers-arent-working"></a>I controller di movimento non funzionano

Attenersi alla procedura seguente:

* Assicurarsi che i controller siano accesi e addebitati completamente.
* Sostituire le batterie del controller.
* Spegnere e riaccendere i controller tenendoli davanti all'utente. Premere e tenere premuto il pulsante Windows per 4 secondi per spegnere un controller, quindi tenere premuto di nuovo per 2 secondi per attivarlo.
* Passare a **impostazioni > dispositivi > Bluetooth & altri dispositivi** nel PC e assicurarsi che siano abbinati (dovrebbero essere visualizzati nella pagina).

[Altre informazioni sui controller di movimento](controllers-in-wmr.md)

## <a name="i-get-a-message-that-says-connect-your-headset-even-though-ive-plugged-in-my-headset"></a>Viene visualizzato un messaggio con la dicitura "Connetti l'auricolare" anche se ho collegato l'auricolare

Attenersi alla procedura seguente:

- Verificare che l'auricolare sia connesso alle porte corrette del computer. Deve essere collegato alla scheda grafica discreta del PC e a una porta USB 3,0. Ecco come identificare le porte corrette:
    - Le porte USB 3,0 hanno un logo speciale con un contrassegno "SS" (che indica "SuperSpeed"). Il pezzo interno della porta è generalmente blu, ma le porte USB 2,0 precedenti sono in genere nere o bianche all'interno.
    - Se il computer dispone di due porte HDMI, utilizzare quella che si connette alla scheda grafica, non la scheda madre del computer. Questa operazione non è sempre ovvia, anche se le porte discrete si trovano spesso in uno slot di espansione nel computer. Se si prova a usare una porta e non funziona, provare l'altra.
- Accedere al sito Web del produttore dell'auricolare e aggiornare i driver e il firmware per l'auricolare.

## <a name="during-mixed-reality-start-up-im-stuck-at-turn-your-head-side-to-side-and-then-at-the-floor"></a>Durante l'avvio della realtà mista, mi sono bloccato a "capovolgere il lato destro e quindi al pavimento".

Questo passaggio consente all'auricolare di riconoscere lo spazio e di ripristinare i limiti e le pavimentazioni virtuali esistenti. Quando si usa l'auricolare, questo processo di analisi può richiedere fino a 10 secondi. Una volta completata l'operazione, si sarà in casa la realtà mista di Windows o verrà richiesto di configurare di nuovo il limite.

Se il processo di analisi richiede più di 10 secondi, potrebbe essersi verificato un problema con il sensore di prossimità nell'auricolare:

1. Verificare che l'adesivo sia stato rimosso dal sensore di prossimità. Il sensore di prossimità si trova all'interno dell'auricolare approssimativamente dove si trova il centro della fronte.
2. Verificare che il sensore di prossimità accenda l'input dell'auricolare: con il dito, coprire e scoprire il sensore di prossimità alcune volte per verificare che l'input passi all'auricolare. Nella parte superiore del PC verrà visualizzato il banner **tasto Windows + Y** . È possibile passare manualmente l'input all'auricolare in qualsiasi momento digitando il **tasto Windows + Y** sulla tastiera.

## <a name="the-floor-of-my-windows-mixed-reality-home-doesnt-appear-to-be-at-the-correct-height"></a>Il piano di casa della realtà mista di Windows non sembra essere all'altezza corretta

Selezionare **inizia > regolazione del piano**, che verrà avviata dopo aver inserito l'app nel mondo, per apportare modifiche durante l'uso dell'auricolare. In questa app si verrà indirizzati all'uso di touch pad (Motion controller) o direction pad (gamepad) per regolare l'altezza del piano. Quando il piano è corretto, usare il pulsante Windows per tornare alla Home page.

## <a name="i-cant-show-a-preview-of-what-im-seeing-in-my-headset-on-my-desktop"></a>Non è possibile visualizzare un'anteprima di ciò che viene visualizzato nell'auricolare sul desktop

Il portale per la realtà mista di Windows include un pulsante **Riproduci** nella parte inferiore della schermata che consente di visualizzare in anteprima gli elementi visualizzati nell'auricolare sullo schermo del desktop. Per motivi di prestazioni, questa funzionalità è disponibile solo nei PC che eseguono Windows Mixed Reality Ultra (90 Hz).

## <a name="how-can-i-get-a-clearer-view-in-my-headset"></a>Come è possibile ottenere una visualizzazione più chiara nell'auricolare

Provare a modificare l'adattamento dell'auricolare. Regolarne la posizione sulla faccia spostando l'icona verso l'alto e verso il basso o verso sinistra e destra, quindi modificare le cinghie in modo che risultino accoglienti.

Se l'auricolare lo supporta, è anche possibile modificare le impostazioni di calibrazione. Se la cuffia ha una manopola per regolare la calibrazione, usare questa. In caso contrario, passare a **impostazioni > realtà mista > qualità visiva** e regolare la calibrazione in tale posizione. Per ulteriori informazioni sulla calibrazione per un dispositivo specifico, rivolgersi al produttore dell'auricolare.

## <a name="when-i-plug-in-my-headset-nothing-happensmixed-reality-portal-doesnt-open"></a>Quando si collega l'auricolare, non accade nulla: il portale per la realtà mista non si apre

Il portale per la realtà mista, l'app che consente di configurare la realtà mista di Windows, è progettata per l'apertura automatica quando si collega un auricolare compatibile. Se non si apre, passare a **Start** e digitare il **portale Mixed Reality** nella casella di **ricerca**  per aprire l'app da questa posizione. Se non si riesce a trovare il portale Mixed Reality, questo potrebbe significare che è necessario eseguire [l'aggiornamento alla versione più recente di Windows](https://support.microsoft.com/help/12373) o che la cuffia non è connessa correttamente al PC.

## <a name="my-head-mount-display-doesnt-work-after-i-shut-down-and-do-a-fast-startup"></a>La visualizzazione del montaggio Head non funziona dopo l'arresto e l'avvio rapido

Provare a eseguire quanto segue:

* Scollegare il cavo di visualizzazione e il cavo USB dalla visualizzazione del montaggio a capo, quindi ricollegarlo.

## <a name="my-wi-fi-slows-down-when-i-use-windows-mixed-reality"></a>Il Wi-Fi rallenta quando si usa la realtà mista di Windows

Se si usa una connessione Wi-Fi a 2,4 GHz, i controller di movimento potrebbero rallentare la connessione Wi-Fi. Provare a eseguire una delle operazioni seguenti:

* Passare a una connessione Wi-Fi a 5 GHz, se disponibile. Altre informazioni
* Usare una scheda Bluetooth separata per connettere i controller di movimento al PC. [Vedere gli adapter consigliati](recommended-adapters-for-windows-mixed-reality-capable-pcs.md)

> [!NOTE]
> Le nuove cuffie vengono associate direttamente ai controller tramite un chip Bluetooth integrato e non dovrebbero riscontrare questo problema.

## <a name="i-got-a-something-went-wrong-error-message-or-im-having-problems-in-the-mixed-reality-portal"></a>Si è verificato un messaggio di errore "si è verificato un problema" oppure si sono verificati problemi nel portale di realtà mista

Per ottenere altre informazioni su un codice di errore specifico, vedere [qui](error-codes.md). È anche possibile provare a:

Riavviare la realtà mista di Windows:

1. Scollegare entrambi i cavi auricolare dal PC.
2. Riavvia il PC.
3. Riconnettere l'auricolare.

Verificare che il PC riconosca la cuffia:

1. Selezionare Avvia.
2. Digitare "Device Manager" nella casella di ricerca e selezionarlo nell'elenco.
3. Espandere "dispositivi in realtà mista" e verificare se l'auricolare è elencato.

Se non è elencato:

1. Collegare la cuffia a porte diverse sul PC, se disponibile.
2. Verificare la disponibilità degli aggiornamenti software più recenti da Windows Update.
3. Disinstallare e reinstallare la realtà mista di Windows:
    1. Scollegare entrambi i cavi auricolare dal PC.
    2. Selezionare **impostazioni > realtà mista > disinstallare**.
    3. Se i controller di movimento sono abbinati al PC, selezionare **impostazioni > dispositivi > Bluetooth & altri dispositivi** per disaccoppiarli. Selezionare ogni controller e "Rimuovi dispositivo". Se i controller sono abbinati all'auricolare, è possibile ignorare questo passaggio.
    4. Collegare la cuffia al PC per reinstallare la realtà mista di Windows.

## <a name="see-also"></a>Vedere anche

* [Contattare la community](https://answers.microsoft.com)
* [Contattaci per assistenza](https://support.microsoft.com/contactus/)
* [Risoluzione dei problemi](troubleshooting-windows-mixed-reality.md)
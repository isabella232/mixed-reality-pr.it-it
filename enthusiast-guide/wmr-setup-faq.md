---
title: Domande frequenti sull'installazione di realtà mista di Windows
description: Risposte alle domande di configurazione comuni quando si lavora con la realtà mista di Windows.
author: hferrone
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Realtà mista di Windows, realtà mista, realtà virtuale, VR, MR, feedback, Hub feedback, bug
appliesto:
- Windows 10
ms.openlocfilehash: 2e7276e7d734770e29ce41db9a19ef40555fea30
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/03/2020
ms.locfileid: "91685565"
---
# <a name="windows-mixed-reality-setup-faq"></a>Domande frequenti sull'installazione di realtà mista di Windows

Di seguito sono riportate alcune informazioni che consentono di risolvere i problemi che possono verificarsi quando si configura la cuffia mista di Windows per la realtà mista.

## <a name="i-get-a-message-that-says-we-couldnt-download-the-window-mixed-reality-software-or-setup-is-stuck-on-the-hang-tight-while-we-do-some-downloading-page"></a>Viene visualizzato un messaggio che indica che non è stato possibile scaricare il software della realtà mista della finestra, oppure il programma di installazione è bloccato nella pagina "bloccarsi mentre è in corso il download".

Attenersi alla procedura seguente:
* Passare a **impostazioni > aggiorna & sicurezza > Windows Update** e assicurarsi che Windows Update sia attivato. Quindi, scaricare e installare gli aggiornamenti in attesa di installazione.
* Verificare che il PC sia connesso a Internet e che disponga di almeno 2 GB di spazio di archiviazione disponibile.
* Riavviare il computer e riprovare. Potrebbe essere necessario ripetere più volte o eseguire lo strumento di risoluzione dei problemi di Windows Update per cancellare gli aggiornamenti in sospeso. 

> [!NOTE]
> * Se si è in una rete gestita dall'organizzazione, rivolgersi all'amministratore. Potrebbe essere necessario abilitare la realtà mista di Windows. Cerchi le istruzioni per professionisti IT? Vedere **[questo articolo](https://docs.microsoft.com/windows/application-management/manage-windows-mixed-reality)** .
> * Se la connessione di rete Wi-Fi è impostata su a consumo, impostarla su non a consumo. **[Scopri di più](https://support.microsoft.com/help/4028458)**

## <a name="i-get-a-message-that-says-something-went-wrong-and-we-couldnt-start-windows-mixed-reality"></a>Viene visualizzato un messaggio che indica che si è verificato un errore e non è stato possibile avviare la realtà mista di Windows.

Attenersi alla procedura seguente:
1. Scollegare l'auricolare dal computer (entrambi i cavi).
2. Riavviare il computer.
3. Passare a **impostazioni > aggiorna & sicurezza > Windows Update** e assicurarsi che Windows Update sia attivato. Quindi, scaricare e installare gli aggiornamenti in attesa di installazione.
4. Riconnettere l'auricolare al computer, quindi riprovare a eseguire l'installazione.

Se i passaggi precedenti non funzionano, provare a disinstallare e reinstallare la realtà mista di Windows. Passare a **impostazioni > realtà mista > disinstallare** e selezionare **Disinstalla** . Riavviare quindi il computer. Per avviare nuovamente il processo di installazione, è sufficiente collegare la cuffia al PC.

## <a name="i-get-a-message-that-says-my-pc-cant-run-windows-mixed-reality"></a>Viene visualizzato un messaggio che indica che il PC non è in grado di eseguire la realtà mista di Windows.

Se si riceve questo messaggio, il PC non soddisfa i [requisiti minimi](https://support.microsoft.com/help/4039260) necessari per eseguire la realtà mista di Windows. Il problema potrebbe essere dovuto al fatto che la configurazione hardware del computer non è compatibile con la realtà mista di Windows o perché è necessario eseguire l' [aggiornamento alla versione più recente di Windows](https://support.microsoft.com/help/12373).

Note sulle schede grafiche:

* Se la configurazione della realtà mista di Windows indica che la scheda grafica non soddisfa i requisiti e si ritiene che sia presente, assicurarsi che l'auricolare sia collegato alla scheda corretta.
* Rivolgersi al produttore della scheda grafica per l'aggiornamento del driver più recente. Per la realtà mista di Windows è necessario un driver di scheda grafica che supporta almeno WDDM 2,2.

## <a name="i-get-a-message-that-says-youre-nearly-therethis-pc-doesnt-meet-the-minimum-requirements-needed-to-run-windows-mixed-reality"></a>Viene visualizzato un messaggio che indica che il PC non soddisfa i requisiti minimi necessari per l'esecuzione della realtà mista di Windows.

Se si riceve questo messaggio, il PC non soddisfa i requisiti minimi necessari per la migliore esperienza nella realtà mista di Windows. Il PC potrebbe essere in grado di eseguire un auricolare immersivo, ma potrebbe non essere in grado di eseguire determinate app o potrebbe riscontrare problemi di prestazioni.

## <a name="my-xbox-controller-isnt-working"></a>Il controller Xbox non funziona.

Attenersi alla procedura seguente:

* Verificare che il controller sia acceso, completamente addebitato e connesso al PC.
* Sostituire le batterie del controller.
* Se si usa un controller Bluetooth, passare a **impostazioni > dispositivi > Bluetooth & altri dispositivi** nel PC e assicurarsi che sia associato (dovrebbe essere visualizzato nella pagina).

[Altre informazioni sui controller Xbox](https://support.xbox.com/xbox-on-windows/accessories/connect-xbox-one-controller-to-pc)

## <a name="my-motion-controllers-arent-working"></a>I controller di movimento non funzionano.
 
Attenersi alla procedura seguente:

* Assicurarsi che i controller siano accesi e addebitati completamente.
* Sostituire le batterie del controller.
* Spegnere e riaccendere i controller tenendoli davanti all'utente. Premere e tenere premuto il pulsante Windows per 4 secondi per spegnere un controller, quindi premerlo e tenerlo premuto di nuovo per 2 secondi per attivarlo. 
* Passare a **impostazioni > dispositivi > Bluetooth & altri dispositivi** nel PC e assicurarsi che siano abbinati (dovrebbero essere visualizzati nella pagina).

[Altre informazioni sui controller di movimento](controllers-in-wmr.md)

## <a name="i-get-a-message-that-says-connect-your-headset-even-though-ive-plugged-in-my-headset"></a>Viene visualizzato un messaggio con la dicitura "Connetti l'auricolare" anche se ho collegato l'auricolare

Attenersi alla procedura seguente:

* Verificare che l'auricolare sia connesso alle porte corrette del computer. Deve essere collegato alla scheda grafica discreta del PC e a una porta USB 3,0. Ecco come identificare le porte corrette:
    * Le porte USB 3,0 hanno un logo speciale con un contrassegno "SS" (che indica "SuperSpeed"). Il pezzo interno della porta è generalmente blu, mentre le porte USB 2,0 precedenti sono in genere nere o bianche all'interno.
    * Se il computer dispone di due porte HDMI, utilizzare quella che si connette alla scheda grafica, non la scheda madre del computer. Non è sempre ovvio, ma le porte discrete si trovano spesso in uno slot di espansione nel computer. Se si prova a usare una porta e non funziona, provare l'altra.
* Accedere al sito Web del produttore dell'auricolare e aggiornare i driver e il firmware per l'auricolare.

## <a name="i-get-an-error-message-when-i-try-to-create-a-boundary"></a>Viene ricevuto un messaggio di errore quando si tenta di creare un limite.

Di seguito sono riportate alcune linee guida per la creazione di un limite:

* Non avvicinarsi troppo a una parete o ad altre ostruzioni.
* Assicurarsi di mantenere l'auricolare all'altezza della vita e di affrontare il computer mentre si tracciano i limiti.
* Verificare che il sensore non sia bloccato e che la luce sia sufficiente.
* Lo spazio che si sta tracciando deve essere maggiore di 3 metri quadrati.
* Lo spazio non deve essere troppo grande o troppo complesso, ma è possibile attenersi a una forma geometrica semplice senza molte torsioni e giri.
* Non attraversare il proprio percorso mentre si esegue la traccia.
* Se ci si blocca in un angolo, ricominciare.

**Se scelgo "seduto e in piedi", quale tipo di esperienza dovrò?**

"Seduto e in piedi" significa che si userà l'auricolare senza un limite. Dovrai rimanere in un'unica posizione, perché non avrai alcun limite per aiutarti a evitare ostacoli fisici. Inoltre, alcune app e giochi possono essere progettati per essere usati con un limite, quindi potrebbero non funzionare come previsto.

## <a name="how-can-i-get-a-clearer-view-in-my-headset"></a>Come è possibile ottenere una visualizzazione più chiara nell'auricolare?

Provare a modificare l'adattamento dell'auricolare. Regolarne la posizione sulla faccia spostando l'icona verso l'alto e verso il basso o verso sinistra e destra, quindi modificare le cinghie in modo che risultino accoglienti.

Se l'auricolare lo supporta, è anche possibile modificare le impostazioni di calibrazione. Se la cuffia ha una manopola per regolare la calibrazione, usare questa. In caso contrario, passare a **impostazioni > realtà mista > qualità visiva** e regolare la calibrazione in tale posizione. Per ulteriori informazioni sulla calibrazione per un dispositivo specifico, rivolgersi al produttore dell'auricolare.

## <a name="what-languages-are-supported-in-windows-mixed-reality"></a>Quali lingue sono supportate in realtà mista di Windows?

La realtà mista di Windows è disponibile nelle lingue seguenti. Se il PC è impostato su una lingua diversa, è comunque possibile usare la realtà mista di Windows, ma l'interfaccia verrà visualizzata in inglese (Stati Uniti) e i comandi vocali e la dettatura non saranno disponibili.

* Cinese semplificato (Cina)
* Inglese (Australia)
* Inglese (Canada)
* Inglese (Gran Bretagna)
* Inglese (Stati Uniti)
* Francese (Canada)
* Francese (Francia)
* Tedesco (Germania)
* Italiano (Italia)
* Giapponese (Giappone)
* Spagnolo (Messico)
* Spagnolo (Spagna)

È anche possibile usare la dettatura in uno dei linguaggi di realtà mista supportati di Windows elencati in precedenza. è sufficiente selezionare **microfono**  sulla tastiera sullo schermo.

La realtà mista di Windows è disponibile anche nelle seguenti lingue senza comandi vocali o funzionalità di dettatura:

* Cinese tradizionale (Taiwan e Hong Kong)
* Olandese (Paesi Bassi)
* Coreano (Corea)
* Russo (Russia)

## <a name="when-i-plug-in-my-headset-nothing-happensmixed-reality-portal-doesnt-open"></a>Quando si collega l'auricolare, non accade nulla: il portale per la realtà mista non si apre.

Il portale per la realtà mista, l'app che consente di configurare la realtà mista di Windows, è progettata per l'apertura automatica quando si collega un auricolare compatibile. Se non si apre, passare a **Start** e digitare il **portale Mixed Reality** nella casella di **ricerca**  per aprire l'app da questa posizione. Se non si riesce a trovare il portale Mixed Reality, questo potrebbe significare che è necessario eseguire [l'aggiornamento alla versione più recente di Windows](https://support.microsoft.com/help/12373) o che la cuffia non è connessa correttamente al PC.

## <a name="i-cant-hear-any-sound-in-my-headset-or-sound-is-playing-through-my-computer"></a>Non è possibile udire alcun suono nell'auricolare o riprodurre un suono nel computer.

Se la cuffia a immersione non include cuffie predefinite, è necessario connettere le cuffie al jack audio dell'auricolare. Il Jack è spesso posizionato dietro la visiera o le lenti dell'auricolare; se si riscontrano problemi, rivolgersi al produttore dell'auricolare. 

Alcune cuffie audio dispongono di pulsanti fisici per controllare il volume. Se l'audio non funziona, controllare per verificare se il volume è disattivato o disattivato.

La realtà mista di Windows è progettata per riprodurre un suono attraverso l'auricolare immersiva quando lo si indossa e ci si connette alle cuffie. Quando si toglie la cuffia o si capovolge la visiera, l'audio passa al dispositivo Windows playback predefinito. È possibile modificare questa impostazione in **impostazioni > realtà mista > audio e sintesi vocale** .

> [!NOTE]
> * L'audio spaziale della realtà mista di Windows funziona meglio con le cuffie incorporate o connesse direttamente all'auricolare immersivo. Gli altoparlanti PC o le cuffie connesse al PC potrebbero non funzionare correttamente per l'audio spaziale.
> * La realtà mista di Windows non supporta le cuffie audio Bluetooth.

## <a name="speech-commands-arent-working"></a>I comandi di sintesi vocale non funzionano.

Per usare i comandi vocali, le impostazioni relative alla lingua e al linguaggio del PC devono essere impostate su una delle [lingue](#what-languages-are-supported-in-windows-mixed-reality) supportate nella realtà mista di Windows. Per verificarlo, passare a **impostazioni > ora & lingua > area & lingua** e **Impostazioni > ora & lingua > voce** .

Se la cuffia non ha un microfono incorporato, sarà necessario allungare le cuffie con un microfono alla cuffia o al PC. Per fare in modo che l'input Mic venga attivato automaticamente nell'auricolare quando lo si utilizza, passare a **impostazioni > realtà mista > audio e vocale** e verificare che **, quando si indossa la cuffia, passare alla** cuffia auricolare è attivato.

Alcune cuffie audio hanno un pulsante fisico per disattivare e disattivare il microfono. Se i comandi di sintesi vocale non funzionano, verificare se il MIC è disattivato.

## <a name="my-head-mount-display-doesnt-work-after-i-shut-down-and-do-a-fast-startup"></a>La visualizzazione del montaggio Head non funziona dopo l'arresto e l'avvio rapido.

Provare a eseguire quanto segue:

* Scollegare il cavo di visualizzazione e il cavo USB dalla visualizzazione del montaggio a capo, quindi ricollegarlo.

## <a name="my-wi-fi-slows-down-when-i-use-windows-mixed-reality"></a>Il Wi-Fi rallenta quando si usa la realtà mista di Windows

Se si usa una connessione Wi-Fi 2,4 GHz, i controller di movimento potrebbero rallentare la connessione Wi-Fi. Provare una delle operazioni seguenti:

* Passare a una connessione Wi-Fi a 5 GHz, se disponibile. Altre informazioni
* Usare una scheda Bluetooth separata per connettere i controller di movimento al PC. [Vedere gli adapter consigliati](recommended-adapters-for-windows-mixed-reality-capable-pcs.md)

> [!NOTE]
> Le nuove cuffie vengono associate direttamente ai controller tramite un chip Bluetooth integrato e non dovrebbero riscontrare questo problema. 

## <a name="see-also"></a>Vedere anche
* [Contattare la community](https://answers.microsoft.com)
* [Contattaci per assistenza](https://support.microsoft.com/contactus/)
* [Risoluzione dei problemi](troubleshooting-windows-mixed-reality.md)


---
title: Domande frequenti sul controller del movimento
description: I controller Windows Mixed Reality risoluzione dei problemi che vanno oltre la documentazione di supporto consumer standard.
author: hferrone
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Windows Mixed Reality, Realtà mista, Realtà virtuale, REALTÀ VIRTUALE, MR, Risoluzione dei problemi, Errori, Guida, Supporto, Controller del movimento
appliesto:
- Windows 10
ms.openlocfilehash: e477ed07e20fb06e270c9a6e13e20defecfc6328896983ed12c4b79ea2197e44
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115219748"
---
# <a name="motion-controller-faqs"></a>Domande frequenti sul controller del movimento

## <a name="what-do-the-vibrations-and-lights-mean"></a>Cosa significano le vibrazioni e le luci

L'anello di costellazione del LED e gli aptici indicano lo stato del controller del movimento.

| State    | Comportamento associato allo stato | Come ottenere/uscire dallo stato |
|----------------------------|-----------------------------|----------------------------------------------------------------------|
| **Accendere**               | I LED si attivano e il controller vibra una sola volta. | Tenere premuto il pulsante Windows sul controller per due secondi per accendere il controller.  |
| **Spegnimento**              |  I LED si spegnino e il controller vibra due volte. | Tenere premuto il pulsante Windows sul controller per quattro secondi per disattivare il controller.   |
| **Sospeso**               |  I LED si spegnino e lampeggiano ogni tre secondi mentre sono in stato di sospensione. | Il controller entra automaticamente nello stato di sospensione quando è senza movimento per 30 secondi. Il controller si riattiva quando rileva il movimento, tranne se il dispositivo non è associato al PC host. Premere il pulsante per riattivarlo in questo caso. |
| **Abbinamento**                |  I LED si pulsa lentamente in modalità di associazione e si distondono quando esci dalla modalità di associazione. Il controller vibra una volta se l'associazione ha avuto esito positivo o tre volte se l'associazione ha esito negativo e quindi si verifica il timeout. | Tenere premuto il pulsante di associazione all'interno della batteria per tre secondi.     |
| **Il controller si connette/si disconnette dal PC** |  Il controller vibra una volta alla connessione o alla disconnessione del PC. | Si verifica quando il controller si connette correttamente al PC dopo l'attivazione o se il controller si disconnette dal PC durante l'uso.|
| **Livello di batteria in esaurimento**      | Gli aptici sono disabilitati quando la batteria è in esaurimento (non è presente alcuna indicazione del LED). L'icona dell'indicatore della batteria sul punto di controllo del controller nel visore VR mostrerà 1/4 pieno quando la batteria è in esaurimento. | Sostituire le batterie. | 
| **Livello di batteria critico** |  Il controller vibra tre volte quando lo si attiva e quindi si spegne automaticamente. L'icona dell'indicatore della batteria sarà rossa. | Sostituire le batterie. Se il problema persiste, [ripristinare le impostazioni di fabbrica del dispositivo](motion-controller-problems.md#how-can-i-restore-the-controllers-to-factory-settings)|

## <a name="my-motion-controllers-arent-working-properly"></a>I controller del movimento non funzionano correttamente

Se i [controller del movimento](controllers-in-wmr.md) non funzionano, si connettono o visualizzano un'immagine dei controller quando si è in contatto con il visore VR:

1. Assicurarsi che i controller siano attivati. Per attivarli, tenere premuto il pulsante Windows per due secondi.
2. Assicurarsi che i controller siano completamente caricati e sostituire le batterie, se non lo sono.
3. Spegnere e riattivare i controller tenendoli davanti all'utente. Tenere premuto il pulsante Windows per quattro secondi per disattivare un controller. Premere e tenere premuto di nuovo per due secondi per attivarlo.
4. Controllare se i controller del movimento sono [associati correttamente.](controllers-in-wmr.md#pair-motion-controllers)
5. Controllare i LED dei controller del movimento: i controller accesi sono associati e connessi, i controller poco accesi non sono connessi.
6. Passare a **Start > Portale realtà mista** sul PC e selezionare "Menu". Dovrebbero essere elencati i controller del movimento, insieme a un messaggio di stato:
    * Pronto: i controller sono tutti impostati.
    * Rilevamento perso: Portale realtà mista non è in grado di trovare i controller. Tenere i dispositivi davanti al visore VR e riavviarli premendo il pulsante Windows per quattro secondi, quindi di nuovo per due secondi.
    * Batteria in esaurimento: sostituire le batterie del controller.
7. Se si usa un adattatore usb Bluetooth esterno, assicurarsi che sia collegato a una porta USB 2.0 (spesso ma non sempre nera). Deve anche essere collegato il più possibile da qualsiasi altro trasmettitore wireless o unità flash USB, incluso il connettore USB per il visore VR. 
8. Passare a **Gestione dispositivi > Bluetooth** e cercare una scheda per verificare che nel PC sia presente Bluetooth radio. Se si usa la configurazione del PC desktop con radio incorporata, verificare se è connessa un'antenna esterna. Se non è presente alcuna antenna esterna connessa, può causare problemi di rilevamento. In caso contrario, usare Bluetooth dongle (USB), disabilitare la funzionalità di Bluetooth interna e ripetere l'associazione e la connessione.
9. Se la Bluetooth delle impostazioni è aperta in background, vengono effettuate molte chiamate aggiuntive al protocollo Bluetooth. Chiuderlo.
10. Controllare il livello della batteria virtuale nel controller del movimento ruotando i controller nella realtà mista per visualizzare l'icona della batteria. Attendere circa 15 secondi prima di leggere il livello, poiché il livello segnalato è superiore al livello effettivo immediatamente dopo la connessione di un controller. Sostituire le batterie se l'icona è rossa.
11. Rimuovere Bluetooth e altoparlanti in Impostazioni > **dispositivi > Bluetooth & altri** dispositivi e disattivare i dispositivi. Usare il jack per le cuffi o gli altoparlanti integrati nel visore VR di realtà mista per un'esperienza audio ottimale.
12. Rimuovere altri Bluetooth dispositivi che possono essere associati al PC, ad esempio le cuffi o i game pad. Passare a **Impostazioni > dispositivi > Bluetooth & altri dispositivi,** selezionare i dispositivi e quindi "Rimuovi dispositivo".
13. Scollegare il cavo USB sul visore VR e collegarlo di nuovo al PC per riavviare Windows Mixed Reality.
14. Le luci del controller lampeggiano quando sono in fase di aggiornamento del firmware. Attendere il completamento dell'aggiornamento e i controller dovrebbero essere visualizzati in Realtà mista.
15. Assicurarsi che il PC sia connesso a una rete Wi-Fi 5 GHz. Se il portatile è connesso a una rete Wi-Fi a 2,4 GHz, in genere condivide la Bluetooth virtuale. Ciò può influire negativamente sulle prestazioni Wi-Fi o Bluetooth, a seconda della progettazione del prodotto. Impostare la banda preferita su 5 GHz nelle impostazioni della scheda di rete. Se la rete non supporta 5 GHz, è possibile usare un dongle Bluetooth invece della funzionalità di Bluetooth interna.
16. Se le impostazioni Bluetooth hanno controller del movimento già associati, Windows i nuovi dispositivi non verranno individuati fino a quando non vengono rimossi. Se sono stati aggiunti usando un dongle specifico, possono essere rimossi solo con tale dongle.
17. Se il PC ha una scheda Bluetooth e si verificano problemi di connessione, provare a usare un adattatore USB Bluetooth usb. A tale scopo, disattivare la radio Bluetooth predefinita in Gestione dispositivi e quindi associare gli altri dispositivi Bluetooth alla nuova scheda.

## <a name="my-controllers-jitter-get-stuck-or-flicker-and-disappear-in-mixed-reality"></a>I controller si instabilità, si bloccano o sfarfallio e scompaiono nella realtà mista

* Se il PC è in esecuzione in una rete Wi-Fi a 2,4 GHz, passare al Wi-Fi a 5 GHz. 
* Se si usa un adattatore Bluetooth esterno, assicurarsi che sia collegato a una porta USB 2.0 (spesso, ma non sempre nera), lontano da altri trasmettitori wireless o unità flash USB.
* Eseguire lo strumento Bluetooth risoluzione dei problemi in **Impostazioni > Aggiornamento & sicurezza > risoluzione dei > Bluetooth**.

## <a name="my-controller-is-stuck-in-an-infinite-reboot"></a>Il controller è bloccato in un riavvio infinito

Si tratta di un indicatore critico della batteria. Inserire batterie nuove nel dispositivo e, se il problema persiste, ripristinare le [impostazioni di fabbrica del controller.](motion-controller-problems.md#how-can-i-restore-the-controllers-to-factory-settings)

## <a name="the-mixed-reality-portal-is-working-but-my-controllers-are-tracking-poorly-flying-away-shaking-etc"></a>Il Portale realtà mista funziona, ma i controller sono insodamente (allontanarsi, afferrare e così via)

1. Le condizioni di illuminazione possono influire sul rilevamento. Assicurarsi di non essere esposti agli inforni diretti e di avere sorgenti di luce punto minime visibili all'HMD(ad esempio stringhe di luci come un albero di albero).
2. Questi sintomi sono causati da errori di comunicazione tra il controller e il PC host e indicano una qualità Bluetooth del collegamento. Vedere [le domande su Bluetooth](motion-controller-problems.md#how-can-i-tell-if-im-using-bluetooth-technology).

## <a name="motion-controller-leds-are-not-lit-but-the-buttons-and-thumbstick-still-work-in-mixed-reality-portal"></a>I LED del controller del movimento non sono accesi, ma i pulsanti e la levetta funzionano ancora Portale realtà mista

La cache di calibrazione del controller del movimento potrebbe essere danneggiata. Per eliminare la cache, eseguire il comando seguente in un prompt dei comandi dell'amministratore:

`rmdir /S /Q C:\Windows\ServiceProfiles\LocalService\AppData\Local\Microsoft\Windows\MotionController\Calibration`

Questa cartella non è accessibile in Windows Explorer e può essere modificata solo da un prompt dei comandi dell'amministratore. Dopo aver eliminato la cartella, riavviare il PC e riconnettere i controller del movimento per ripristinare i file di calibrazione.

## <a name="my-controller-looks-like-a-viveoculus-has-strange-orientation-or-the-buttons-are-incorrectly-mapped"></a>Il controller ha l'aspetto di Vive/Oculus, ha un orientamento strano o i pulsanti sono mappati in modo errato

È probabile che il sito Web non abbia il supporto completo per il controller del movimento.

## <a name="my-motion-controllers-do-not-appear-in-steamvr-apps-and-games"></a>I controller del movimento non vengono visualizzati nelle app e nei giochi di SteamVR

Prima di tutto, assicurarsi che le batterie del controller siano caricate. I controller non funzionano se le batterie sono in stato di insodre o di morte

Se è possibile visualizzare i controller nel Casa sulla scogliera ma non nelle app e nei giochi di SteamVR, il driver del modello di controller di movimento potrebbe non essere installato correttamente. Per verificare che il driver del modello di controller di movimento sia installato correttamente:

1. Attivare entrambi i controller di movimento. Controllare se i controller di movimento [sono associati correttamente.](controllers-in-wmr.md#pair-motion-controllers)
2. Passare a **Gestione dispositivi > dispositivi dell'interfaccia umana** e cercare "Controller di movimento".
3. Fare doppio clic su ogni dispositivo "Controller di movimento" e passare alla scheda "Driver". Verificare che la versione del driver elencata corrisponda a una [di queste versioni.](mixed-reality-software.md#mixed-reality-motion-controller-model-driver-release-history)
4. Se la versione del driver non corrisponde o non è possibile trovare un dispositivo denominato "Controller di movimento", eseguire Windows Update.  Il driver verrà scaricato e installato automaticamente. Se si è in un PC con criteri aziendali o se Windows Update è altrimenti limitato, potrebbe essere necessario installare manualmente il driver del modello di controller di movimento. A tale scopo, visitare [questa pagina e](mixed-reality-software.md#mixed-reality-motion-controller-model-driver-release-history) cercare la versione del driver corrispondente all'hardware del controller. Le istruzioni di installazione sono disponibili nella pagina di download.

## <a name="the-controller-firmware-update-takes-longer-than-two-minutes"></a>L'aggiornamento del firmware del controller richiede più di due minuti

Vedere la [Bluetooth domande.](motion-controller-problems.md#how-can-i-tell-if-im-using-bluetooth-technology) Questi Bluetooth di collegamento non sono in genere la causa di questi problemi.

## <a name="i-inserted-fresh-batteries-but-the-controller-virtual-battery-level-does-not-indicate-full-level"></a>Ho inserito batterie nuove, ma il livello della batteria virtuale del controller non indica il livello completo

Il livello della batteria del controller di movimento è ottimizzato per le batterie AA. Alcune batterie ricaricabili a bassa tensione potrebbero non essere segnalate come complete anche se sono completamente caricate.

## <a name="my-samsung-motion-controllers-touchpad-is-off-center-or-has-a-dead-spot"></a>Il touchpad del controller di movimento Samsung è spento al centro o ha un punto di inattivi

Si tratta probabilmente di un difetto hardware e si dovrebbe tornare al rivenditore o al produttore di apparecchiature per una sostituzione o uno scambio.

## <a name="how-can-i-restore-the-controllers-to-factory-settings"></a>Come ripristinare le impostazioni predefinite dei controller

Ripristinarlo in condizioni di fabbrica (saranno necessarie batterie nuove):

1. Scollegare e spegnere i controller.
2. Aprire il coperchio della batteria.
3. Inserire le nuove batterie.
4. Tenere premuto il pulsante di associazione (la scheda nella parte inferiore sotto le batterie).
5. Tenendo premuto il pulsante di associazione, alimentare il controller premendo e tenendo premuto il pulsante Windows per cinque secondi (mantenere entrambi i pulsanti premuto).
6. Rilasciare i pulsanti e attendere l'accensione del controller. Questa operazione richiede fino a 15 secondi e non sono presenti indicatori quando è in corso il ripristino del dispositivo. Se il dispositivo si alimenta immediatamente al rilascio del pulsante, la sequenza del pulsante di ripristino non è stata registrata ed è necessario riprovare.
7. Se i controller sono stati associati al **PC,** passare Impostazioni > Bluetooth > altri dispositivi e selezionare "Controller di movimento" e "Rimuovi dispositivo" per rimuovere le associazioni dei controller Bluetooth impostazioni.
8. [Associare nuovamente i controller](controllers-in-wmr.md#pair-motion-controllers) al visore o al PC.
9. Dopo la connessione con l'host e il visore, il dispositivo verrà aggiornato al firmware più recente disponibile.

## <a name="can-i-pair-my-xbox-controller-to-my-pc-so-i-can-use-it-in-headset"></a>È possibile associare il controller Xbox al PC in modo da poterlo usare nel visore

È possibile associare un controller Bluetooth Xbox per usarlo con il visore seguendo [queste istruzioni.](https://support.xbox.com/help/hardware-network/accessories/connect-and-troubleshoot-xbox-one-bluetooth-issues)

Se si dispone di un controller Xbox cablato, collegarlo al PC.

Alcuni giochi e app usano il controller Xbox in modo diverso rispetto a quello usato nella realtà mista. Per usare il controller per un gioco o un'app, selezionare "Usa come game pad" sulla barra dell'app o pronunciare "Usa come game pad". Per tornare alla realtà mista, selezionare di nuovo "Usa come game pad" o pronunciare "Usa con sguardo fisso". 

## <a name="how-do-i-pair-new-controllers-if-windows-mixed-reality-is-already-set-up-on-my-pc"></a>Ricerca per categorie i nuovi controller se Windows Mixed Reality è già configurato nel PC

Se si associano i controller al visore, usare l'app complementare [(il Portale realtà mista](install-windows-mixed-reality.md#launch-mixed-reality-portal) può aiutare a trovare un'app complementare da avviare o fornire un elenco di app complementari tra cui è possibile selezionare).

## <a name="how-can-i-return-my-controllers-to-their-factory-pairing"></a>Come è possibile restituire i controller all'associazione di factory

Per restituire i controller di movimento all'associazione di fabbrica o per associarli a un visore Windows Mixed Reality con una radio Bluetooth predefinita, eseguire l'app complementare del dispositivo del visore e seguire le istruzioni per l'associazione del controller di movimento. Ad esempio, l'app "Acer OJO 500" o l'app "Samsung HMD Odyssey+ Setup" viene installata automaticamente la prima volta che il visore è collegato.

## <a name="my-motion-controllers-are-not-pairing-to-my-pc"></a>I controller di movimento non sono associati al PC

* Se i controller non si attivano, inserire batterie nuove. Se il problema non viene risolto, ripristinare le impostazioni predefinite del dispositivo tramite l'accensione del dispositivo tenendo premuto i pulsanti di associazione. Per altre informazioni, vedere la procedura [di ripristino del dispositivo](motion-controller-problems.md#how-can-i-restore-the-controllers-to-factory-settings).
* Se i controller si attivano mentre si usa un adattatore Bluetooth esterno, assicurarsi che l'adattatore sia collegato a una porta USB 2.0 (spesso, ma non sempre, nera), lontano da altri trasmettitori wireless o unità flash USB. Se non funziona ancora, eseguire lo strumento di risoluzione dei Bluetooth in Impostazioni > aggiornamento & sicurezza > risoluzione dei > Bluetooth.
* Se si usa un adattatore Qualcomm e il PC si è appena in arresto anomalo, riavviare il PC.
* Provare a riavviare i controller di movimento che non sono associati, uno alla volta, quindi riavviare il PC.
* La cache del controller di movimento potrebbe essere danneggiata. Per risolvere questo problema, vedere questi [passaggi.](motion-controller-problems.md#motion-controller-leds-are-not-lit-but-the-buttons-and-thumbstick-still-work-in-mixed-reality-portal)
* Se la procedura consente di risolvere il problema, contattare il produttore.

## <a name="my-paired-controllers-dont-show-up-in-the-mixed-reality-portal"></a>I controller associati non vengono visualizzati nel Portale realtà mista

* Tenere i controller davanti al visore e riavviarli premendo il pulsante Windows per quattro secondi, quindi di nuovo per due secondi.
* Se i controller vengono visualizzati come connessi, annullare l'associazione e ripartire il [processo di associazione.](controllers-in-wmr.md#pair-motion-controllers)
* Se i LED del controller sono in bicicletta con un quadrante di luci accese e spente alla volta, vengono sottoposti a un aggiornamento del firmware. Attendere il completamento dell'aggiornamento e i controller dovrebbero essere visualizzati in Realtà mista.
* Se viene usato un adattatore Bluetooth esterno, assicurarsi che l'adattatore sia collegato a una porta USB 2.0 (nera), lontano da altri trasmettitori wireless o dispositivi USB 3.0.
* Se il PC si arresta in modo anomalo e viene usato un adattatore Qualcomm, la reimpostazione potrebbe non funzionare. Per risolvere il problema, scollegare l'alimentazione dal retro del computer (oppure, se su un computer portatile, tenere premuto il pulsante di alimentazione per 10 secondi) e riavviare il PC.
* Eseguire lo strumento Bluetooth risoluzione dei problemi in **Impostazioni > aggiornamento & sicurezza > risoluzione dei > Bluetooth**.  

## <a name="im-trying-to-pair-my-controllers-but-they-never-show-up-in-the-add-a-new-device-menu-in-bluetooth-settings"></a>Si sta tentando di associare i controller, ma non vengono mai visualizzati nel menu "Aggiungi un nuovo dispositivo" nelle impostazioni Bluetooth

Verificare che i controller non siano già associati. In caso contrario, rimuoverli e riprovare. Riavviare il PC se il problema persiste. In caso di errore, vedere altre [informazioni su Bluetooth](motion-controller-problems.md#how-can-i-tell-if-im-using-bluetooth-technology).

Nota: se un altro set di controller di movimento è associato al PC, sarà necessario annullare l'associazione di tali controller prima di associare quelli nuovi. Se un set di controller di movimento è stato associato al PC corrente e quindi li è stato associato a un secondo PC, sarà necessario annullare l'associazione e rias associarli al PC corrente prima di usarli di nuovo.

## <a name="how-can-i-tell-if-im-using-bluetooth-technology"></a>Come è possibile determinare se si usa la tecnologia Bluetooth

I controller di movimento usano la stessa Bluetooth disponibile in molti dispositivi consumer e sono progettati per funzionare con la funzionalità Bluetooth inclusa in qualsiasi PC recente. Il PC deve avere una Bluetooth radio se ha superato il controllo di compatibilità della realtà mista. Da verificare:

* Aprire "Gestione dispositivi".
* Espandere la Bluetooth e cercare un adapter.

![Screenshot di Gestione dispositivi di esempio. L'adapter è la Bluetooth radio.](images/devicemanagerbtadapterpic.png)

Se il PC non dispone di Bluetooth, usare pluggable USB Bluetooth micro adapter a basso consumo 4.0.

## <a name="wi-fi-slows-down-on-my-notebook-when-motion-controllers-are-turned-on"></a>Wi-Fi rallenta nel notebook quando i controller di movimento sono accesi

Il notebook può condividere l'antenna Wi-Fi con Bluetooth quando è connesso a un punto di accesso a 2,4 GHz. Verificare in Gestione dispositivi se è possibile impostare la preferenza banda su 5 GHz. Se una rete a 5 GHz non è disponibile e le prestazioni sono erre, è consigliabile usare un dongle Bluetooth rete.

![Le impostazioni di selezione della banda Wi-Fi sono disponibili tramite Gestione dispositivi](images/wifi5ghz.png)

## <a name="my-pc-has-bluetooth-technology-but-im-having-problems-with-my-controllers&quot;></a>Il PC ha Bluetooth tecnologia, ma si verificano problemi con i controller

I controller di movimento devono funzionare con Bluetooth tastiere, mouse e controller di gioco. L'esperienza varia a seconda del modello di tastiera, mouse o controller di gioco in uso. Ecco alcune operazioni che è possibile eseguire per migliorare le prestazioni:

* Se il computer ha Bluetooth ma si verificano ancora problemi con i controller di movimento, provare a sostituire la radio Bluetooth con un adattatore Bluetooth esterno collegabile collegato all'USB. È possibile avere una sola scheda Bluetooth radio attiva alla volta. Se si collega una radio esterna insieme a una radio esistente, è necessario disabilitare la radio Bluetooth esistente in Gestione dispositivi. Fare clic con il pulsante destro del mouse sull'adattatore e selezionare &quot;Disabilita dispositivo&quot; e annullare l'associazione/riassalvare tutti i dispositivi Bluetooth precedenti.
* Se si usa un adattatore Bluetooth USB, collegarlo a una porta USB 2.0 (le porte 2.0 sono spesso nere e non sono etichettate come &quot;SS"), se disponibili. La porta deve essere fisicamente separata da:
    - connettore USB HMD
    - unità flash
    - dischi rigidi
    - Ricevitori USB wireless come quelli per tastiere/mouse Idealmente, collegare l'adattatore Bluetooth USB sul lato opposto del computer il più possibile da questi altri connettori.
* Chiudere la Bluetooth delle impostazioni, se aperta. Lasciarlo aperto in background significa che vengono effettuate molte chiamate aggiuntive al Bluetooth protocollo.
* Se il visore è associato al PC, usare lo stack di driver Windows Bluetooth e non installare stack di driver Bluetooth di terze parti. Il software di terze parti potrebbe non funzionare correttamente.
* Disabilitare l'impostazione "Mostra notifica per la connessione tramite Swift Pair" in "Bluetooth & altri dispositivi" per ridurre l'attività di scansione radio dell'host.
* Se si usa una scheda Bluetooth interna, assicurarsi di usare un'antenna Bluetooth esterna o che si verifichino problemi di rilevamento. Se non funziona, usare un Bluetooth dongle (USB) esterno dopo aver disabilitato il Bluetooth.
* Il dispositivo dovrebbe essere visualizzato nella categoria "Mouse, tastiera & Penna" nelle Bluetooth impostazioni. Se si trova in "Altri dispositivi", annullare l'associazione e associare il dispositivo.
* Rimuovere, annullare l'associazione e spegnere le Bluetooth e gli altoparlanti. Questi non sono supportati con Windows Mixed Reality. Usare il jack per le cuffia o gli altoparlanti incorporati nel visore di Realtà mista per ottenere la migliore esperienza audio.

## <a name="my-second-controller-takes-a-long-time-to-reconnect"></a>La riconnessione del secondo controller richiede molto tempo

Questo problema si verifica in alcune radio Intel meno recenti se i controller di movimento sono acceso contemporaneamente. Evitare l'accensione dei controller contemporaneamente.

## <a name="my-qualcomm-bluetooth-radio-cannot-pair-controllers-after-a-pc-crash"></a>La radio Bluetooth Qualcomm non può associare i controller dopo un arresto anomalo del PC

Qualcomm (QCA) Bluetooth driver radio prima della 10.0.0.448 può finire in uno stato non valido dopo un Windows arresto anomalo. Spegnere completamente il PC per risolvere questo problema.

## <a name="im-experiencing-poor-controller-tracking-with-marvell-radio"></a>Si verifica un monitoraggio del controller scadente con la radio Marvell

Passare **> Bluetooth >** Gestione dispositivi > Bluetooth > Bluetooth Adapter > Radio Adapter > Properties > Driver e assicurarsi di usare il driver 15.68.9210.47 o versione successiva.

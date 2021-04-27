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
ms.openlocfilehash: cf45794d5c5c6c790578e76be4b222d851b5a73c
ms.sourcegitcommit: 229c33afab7c70341982f48962028aad13956356
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/27/2021
ms.locfileid: "108069195"
---
# <a name="motion-controller-faqs"></a>Domande frequenti sul controller del movimento

## <a name="what-do-the-vibrations-and-lights-mean"></a>Cosa significano le vibrazioni e le luci

L'anello di costellazione del LED e gli aptici indicano lo stato del controller del movimento.

| State    | Comportamento associato allo stato | Come ottenere/uscire dallo stato |
|----------------------------|-----------------------------|----------------------------------------------------------------------|
| **Accendere**               | I LED si attivano e il controller vibra una sola volta. | Tenere premuto il pulsante Windows sul controller per due secondi per accendere il controller.  |
| **Spegnimento**              |  I LED si spegnino e il controller vibra due volte. | Tenere premuto il pulsante Windows sul controller per quattro secondi per disattivare il controller.   |
| **Sospeso**               |  I LED si spegnino e lampeggiano ogni tre secondi mentre sono in stato di sospensione. | Il controller entra automaticamente nello stato di sospensione quando è senza movimento per 30 secondi. Il controller si riattiva quando rileva il movimento, tranne se il dispositivo non è associato al PC host. Premere il pulsante per riattivarlo in questo caso. |
| **Abbinamento**                |  I LED si pulsa lentamente mentre sono in modalità di associazione ed esci dalla modalità di associazione. Il controller vibra una volta se l'associazione ha avuto esito positivo o tre volte se l'associazione ha esito negativo e quindi si verifica il timeout. | Tenere premuto il pulsante di associazione all'interno della batteria per tre secondi.     |
| **Il controller si connette/disconnette dal PC** |  Il controller vibra una volta alla connessione o alla disconnessione del PC. | Si verifica quando il controller si connette correttamente al PC dopo l'attivazione o se il controller si disconnette dal PC durante l'uso.|
| **Livello di batteria in esaurimento**      | Gli aptici sono disabilitati quando la batteria è in esaurimento (non sono presenti indicazioni led). L'icona dell'indicatore della batteria sul handle del controller nel visore visualizza 1/4 pieno quando la batteria è scarica. | Sostituire le batterie. | 
| **Livello critico della batteria** |  Il controller vibra tre volte quando lo si accende e quindi si spegne automaticamente. L'icona dell'indicatore della batteria sarà rossa. | Sostituire le batterie. Se il problema persiste, [ripristinare le impostazioni predefinite del dispositivo](motion-controller-problems.md#how-can-i-restore-the-controllers-to-factory-settings)|

## <a name="my-motion-controllers-arent-working-properly"></a>I controller di movimento non funzionano correttamente

Se i [controller di movimento](controllers-in-wmr.md) non funzionano, si connettono o mostrano un'immagine dei controller quando si indossa il visore:

1. Assicurarsi che i controller siano accesi. Per attivarli, tenere premuto il pulsante Windows per due secondi.
2. Assicurarsi che i controller siano completamente caricati e sostituire le batterie in caso di insodd di carica.
3. Spegnere e riattivare i controller tenendoli davanti all'utente. Tenere premuto il pulsante di Windows per quattro secondi per disattivare un controller. Premere e tenere premuto di nuovo per due secondi per attivarlo.
4. Controllare se i controller del movimento sono [associati correttamente.](controllers-in-wmr.md#pair-motion-controllers)
5. Controllare i LED dei controller del movimento: i controller accesi sono associati e connessi, i controller poco accesi non sono connessi.
6. Passare a **Start > Portale realtà mista** sul PC e selezionare "Menu". Dovrebbero essere elencati i controller del movimento, insieme a un messaggio di stato:
    * Pronto: i controller sono tutti impostati.
    * Rilevamento perso: Portale realtà mista non è in grado di trovare i controller. Tenere i dispositivi davanti al visore VR e riavviarli premendo il pulsante Windows per quattro secondi, quindi di nuovo per due secondi.
    * Batteria in esaurimento: sostituire le batterie del controller.
7. Se si usa un adattatore Bluetooth USB esterno, assicurarsi che sia collegato a una porta USB 2.0 (spesso ma non sempre nera). Deve anche essere collegato il più possibile da qualsiasi altro trasmettitore wireless o unità flash USB, incluso il connettore USB per il visore VR. 
8. Passare a **Gestione dispositivi > Bluetooth** e cercare un adattatore per verificare che nel PC sia presente una sola radio Bluetooth. Se si usa la configurazione del PC desktop con radio incorporata, verificare se un'antenna esterna è connessa. Se non è presente un'antenna esterna connessa, può causare problemi di tracciamento. In caso contrario, usare un dongle Bluetooth esterno (USB), disabilitare la funzionalità Bluetooth interna e ripetere l'associazione e la connessione.
9. Se la finestra impostazioni Bluetooth è aperta in background, vengono effettuate molte chiamate aggiuntive al protocollo Bluetooth. Chiuderlo.
10. Controllare il livello della batteria virtuale nel controller del movimento ruotando i controller nella realtà mista per visualizzare l'icona della batteria. Attendere circa 15 secondi prima di leggere il livello, poiché il livello segnalato è superiore al livello effettivo immediatamente dopo la connessione di un controller. Sostituire le batterie se l'icona è rossa.
11. Rimuovere le cuffi e gli altoparlanti Bluetooth in Impostazioni **> dispositivi > Bluetooth &** altri dispositivi e disattivare i dispositivi. Usare il jack per le cuffi o gli altoparlanti integrati nel visore VR di realtà mista per un'esperienza audio ottimale.
12. Rimuovere altri dispositivi Bluetooth che possono essere associati al PC, ad esempio le cuffia o i gamepad. Passare a **Impostazioni > dispositivi > Bluetooth & altri** dispositivi, selezionare i dispositivi e quindi "Rimuovi dispositivo".
13. Scollegare il cavo USB sul visore e collegarlo di nuovo al PC per riavviare il Windows Mixed Reality.
14. Le luci del controller lampeggiano quando vengono sottoposte a un aggiornamento del firmware. Attendere il completamento dell'aggiornamento e i controller dovrebbero essere visualizzati in Realtà mista.
15. Assicurarsi che il PC sia connesso a una rete Wi-Fi 5 GHz. Se il portatile è connesso a una rete Wi-Fi 2,4 GHz, in genere condivide la connessione Bluetooth. Ciò può influire negativamente sulle prestazioni Wi-Fi o Bluetooth, a seconda della progettazione del prodotto. Impostare la banda preferita su 5 GHz nelle impostazioni della scheda di rete. Se la rete non supporta 5 GHz, è possibile usare un dongle Bluetooth invece della funzionalità Bluetooth interna.
16. Se alle impostazioni Bluetooth sono già associati controller di movimento, Windows non individua i nuovi dispositivi finché non vengono rimossi. Se sono stati aggiunti usando un dongle specifico, possono essere rimossi solo con tale dongle.
17. Se il PC ha bluetooth integrato e si verificano problemi di connessione, provare a usare un adattatore Bluetooth USB. A tale scopo, disattivare la radio Bluetooth predefinita in Gestione dispositivi e quindi associare gli altri dispositivi Bluetooth alla nuova scheda.

## <a name="my-controllers-jitter-get-stuck-or-flicker-and-disappear-in-mixed-reality"></a>I controller si instabilità, si bloccano o sfarfallio e scompaiono nella realtà mista

* Se il PC è in esecuzione su wifi a 2,4 GHz, passare al wifi a 5 GHz. 
* Se si usa un adattatore Bluetooth esterno, assicurarsi che sia collegato a una porta USB 2.0 (spesso, ma non sempre nera), lontano da altri trasmettitori wireless o unità flash USB.
* Eseguire lo strumento di risoluzione dei problemi Bluetooth in **Impostazioni > aggiornamento & sicurezza > risolvere > Bluetooth**.

## <a name="my-controller-is-stuck-in-an-infinite-reboot"></a>Il controller è bloccato in un riavvio infinito

Si tratta di un indicatore critico della batteria. Inserire batterie nuove nel dispositivo e, se il problema persiste, ripristinare le [impostazioni di fabbrica del controller.](motion-controller-problems.md#how-can-i-restore-the-controllers-to-factory-settings)

## <a name="the-mixed-reality-portal-is-working-but-my-controllers-are-tracking-poorly-flying-away-shaking-etc"></a>Il Portale realtà mista funziona, ma i controller sono insodamente (allontanarsi, afferrare e così via)

1. Le condizioni di illuminazione possono influire sul rilevamento. Assicurarsi di non essere esposti a luce diretta e avere sorgenti di luce punto minime visibili per l'HMD(ad esempio, stringhe di luci come un albero di albero).
2. Questi sintomi sono causati da errori di comunicazione tra il controller e il PC host e indicano una qualità del collegamento Bluetooth scadente. Vedere [le domande su Bluetooth.](motion-controller-problems.md#how-can-i-tell-if-im-using-bluetooth-technology)

## <a name="motion-controller-leds-are-not-lit-but-the-buttons-and-thumbstick-still-work-in-mixed-reality-portal"></a>I LED del controller del movimento non sono accesi, ma i pulsanti e la levetta funzionano ancora Portale realtà mista

La cache di calibrazione del controller del movimento potrebbe essere danneggiata. Per eliminare la cache, eseguire il comando seguente in un prompt dei comandi dell'amministratore:

`rmdir /S /Q C:\Windows\ServiceProfiles\LocalService\AppData\Local\Microsoft\Windows\MotionController\Calibration`

Questa cartella non è accessibile in Esplora risorse e può essere modificata solo da un prompt dei comandi dell'amministratore. Dopo aver eliminato la cartella, riavviare il PC e riconnettere i controller del movimento per ripristinare i file di calibrazione.

## <a name="my-controller-looks-like-a-viveoculus-has-strange-orientation-or-the-buttons-are-incorrectly-mapped"></a>Il controller ha l'aspetto di Vive/Oculus, ha un orientamento strano o i pulsanti sono mappati in modo errato

È probabile che il sito Web non abbia il supporto completo per il controller del movimento.

## <a name="my-motion-controllers-do-not-appear-in-steamvr-apps-and-games"></a>I controller del movimento non vengono visualizzati nelle app e nei giochi di SteamVR

Prima di tutto, assicurarsi che le batterie del controller siano caricate. I controller non funzionano se le batterie sono in stato di dead o dead

Se è possibile visualizzare i controller nel Casa sulla scogliera ma non nelle app e nei giochi Dirvr, il driver del modello di controller del movimento potrebbe non essere installato correttamente. Per verificare che il driver del modello di controller del movimento sia installato correttamente:

1. Attivare entrambi i controller del movimento. Controllare se i controller del movimento sono [associati correttamente.](controllers-in-wmr.md#pair-motion-controllers)
2. Passare a **Gestione dispositivi > dispositivi dell'interfaccia umana** e cercare "Controller di movimento".
3. Fare doppio clic su ogni dispositivo "Controller di movimento" e passare alla scheda "Driver". Verificare che la versione del driver elencata corrisponda a una [di queste versioni.](mixed-reality-software.md#mixed-reality-motion-controller-model-driver-release-history)
4. Se la versione del driver non corrisponde o non è possibile trovare un dispositivo denominato "Controller di movimento", eseguire Windows Update.  Il driver verrà scaricato e installato automaticamente. Se si è in un PC con criteri aziendali o se Windows Update è altrimenti limitato, potrebbe essere necessario installare manualmente il driver del modello di controller di movimento. A tale scopo, visitare [questa pagina e](mixed-reality-software.md#mixed-reality-motion-controller-model-driver-release-history) cercare la versione del driver corrispondente all'hardware del controller. Le istruzioni di installazione sono disponibili nella pagina di download.

## <a name="the-controller-firmware-update-takes-longer-than-two-minutes"></a>L'aggiornamento del firmware del controller richiede più di due minuti

Controllare la [sezione Domande Bluetooth](motion-controller-problems.md#how-can-i-tell-if-im-using-bluetooth-technology). La scarsa qualità del collegamento Bluetooth causa in genere questi problemi.

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
5. Tenendo premuto il pulsante di associazione, azionare il controller premendo e tenendo premuto il pulsante di Windows per cinque secondi (mantenere entrambi i pulsanti premuto).
6. Rilasciare i pulsanti e attendere l'accensione del controller. Questa operazione richiede fino a 15 secondi e non sono presenti indicatori quando è in corso il ripristino del dispositivo. Se il dispositivo si alimenta immediatamente al rilascio del pulsante, la sequenza del pulsante di ripristino non è stata registrata ed è necessario riprovare.
7. Se i controller sono stati associati al PC, passare a Impostazioni **> Bluetooth >** altri dispositivi e selezionare "Controller del movimento" e "Rimuovi dispositivo" per rimuovere le associazioni del controller dalle impostazioni Bluetooth.
8. [Associare nuovamente i controller](controllers-in-wmr.md#pair-motion-controllers) al visore VR o al PC.
9. Dopo la connessione con l'host e il visore VR, il dispositivo verrà aggiornato all'ultimo firmware disponibile.

## <a name="can-i-pair-my-xbox-controller-to-my-pc-so-i-can-use-it-in-headset"></a>È possibile associare il controller Xbox al PC in modo da poterlo usare nel visore VR?

È possibile associare un controller Xbox Bluetooth per usarlo con il visore VR seguendo [queste istruzioni.](https://support.xbox.com/help/hardware-network/accessories/connect-and-troubleshoot-xbox-one-bluetooth-issues)

Se si dispone di un controller Xbox cablato, collegarlo al PC.

Alcuni giochi e app usano il controller Xbox in modo diverso rispetto a quello usato nella realtà mista. Per usare il controller per un gioco o un'app, selezionare "Usa come game pad" sulla barra dell'app o pronunciare "Usa come game pad". Per tornare alla realtà mista del controller, selezionare di nuovo "Usa come game pad" o pronunciare "Usa con sguardo fisso". 

## <a name="how-do-i-pair-new-controllers-if-windows-mixed-reality-is-already-set-up-on-my-pc"></a>Ricerca per categorie associare nuovi controller se Windows Mixed Reality è già configurato nel PC

Se si associano i controller al visore VR, usare l'app complementare (il [Portale realtà mista](install-windows-mixed-reality.md#launch-mixed-reality-portal) consente di trovare un'app complementare da avviare o fornire un elenco di app complementari tra cui è possibile selezionare).

## <a name="how-can-i-return-my-controllers-to-their-factory-pairing"></a>Come è possibile restituire i controller all'associazione di factory

Per restituire i controller del movimento all'associazione di fabbrica o per associarli a un visore VR Windows Mixed Reality con la radio Bluetooth incorporata, eseguire l'app complementare del dispositivo del visore VR e seguire le istruzioni per l'associazione del controller del movimento. Ad esempio, l'app "Acer OJO 500" o l'app "Samsung HMD Odyssey+ Setup" viene installata automaticamente la prima volta che il visore è collegato.

## <a name="my-motion-controllers-are-not-pairing-to-my-pc"></a>I controller di movimento non sono associati al PC

* Se i controller non si attivano, inserire batterie nuove. Se il problema non viene risolto, ripristinare le impostazioni predefinite del dispositivo tramite l'accensione del dispositivo tenendo premuto i pulsanti di associazione. Per altre informazioni, vedere la procedura [di ripristino del dispositivo](motion-controller-problems.md#how-can-i-restore-the-controllers-to-factory-settings).
* Se i controller si attivano mentre si usa un adattatore Bluetooth esterno, assicurarsi che l'adattatore sia collegato a una porta USB 2.0 (spesso, ma non sempre, nera), lontano da altri trasmettitori wireless o unità flash USB. Se non funziona ancora, eseguire lo strumento di risoluzione dei problemi Bluetooth in Impostazioni > Aggiornamento & sicurezza > risoluzione dei problemi > Bluetooth.
* Se si usa un adattatore Qualcomm e il PC si è appena in arresto anomalo, riavviare il PC.
* Provare a riavviare i controller di movimento che non sono associati, uno alla volta, quindi riavviare il PC.
* La cache del controller di movimento potrebbe essere danneggiata. Per risolvere questo problema, vedere questi [passaggi.](motion-controller-problems.md#motion-controller-leds-are-not-lit-but-the-buttons-and-thumbstick-still-work-in-mixed-reality-portal)
* Se la procedura consente di risolvere il problema, contattare il produttore.

## <a name="my-paired-controllers-dont-show-up-in-the-mixed-reality-portal"></a>I controller associati non vengono visualizzati nel Portale realtà mista

* Tenere i controller davanti al visore e riavviarli premendo il pulsante Windows per quattro secondi, quindi di nuovo per due secondi.
* Se i controller vengono visualizzati come connessi, annullare l'associazione e ripartire il [processo di associazione.](controllers-in-wmr.md#pair-motion-controllers)
* Se i LED del controller sono in bicicletta con un quadrante di luci accese e spente alla volta, vengono sottoposti a un aggiornamento del firmware. Attendere il completamento dell'aggiornamento e i controller dovrebbero essere visualizzati in Realtà mista.
* Se si usa un adattatore Bluetooth esterno, assicurarsi che l'adattatore sia collegato a una porta USB 2.0 (nera), lontano da altri trasmettitori wireless o dispositivi USB 3.0.
* Se il PC si arresta in modo anomalo e viene usato un adattatore Qualcomm, la reimpostazione potrebbe non funzionare. Per risolvere questo problema, scollegare l'alimentazione dalla parte posteriore del computer (o, se su un portatile, tenere premuto il pulsante di alimentazione per 10 secondi) e riavviare il PC.
* Eseguire lo strumento di risoluzione dei problemi Bluetooth in **Impostazioni > Aggiornamento & sicurezza > risoluzione dei > Bluetooth**.  

## <a name="im-trying-to-pair-my-controllers-but-they-never-show-up-in-the-add-a-new-device-menu-in-bluetooth-settings"></a>Sto provando ad associare i controller, ma non vengono mai visualizzati nel menu "Aggiungi un nuovo dispositivo" nelle impostazioni Bluetooth

Verificare che i controller non siano già associati. In caso contrario, rimuoverli e riprovare. Riavviare il PC se il problema persiste. Se l'operazione non riesce, vedere [altre informazioni su Bluetooth.](motion-controller-problems.md#how-can-i-tell-if-im-using-bluetooth-technology)

Nota: se un altro set di controller del movimento è associato al PC, dovrai annullare l'associazione di tali controller prima di associarli a quelli nuovi. Se hai associato un set di controller del movimento al PC corrente e quindi li hai associati a un secondo PC, dovrai annullare l'associazione e rias associarli al PC corrente prima di usarli di nuovo.

## <a name="how-can-i-tell-if-im-using-bluetooth-technology"></a>Come è possibile determinare se si usa la tecnologia Bluetooth?

I controller del movimento usano la stessa tecnologia Bluetooth presente in molti dispositivi consumer e sono progettati per funzionare con la funzionalità Bluetooth inclusa in qualsiasi PC recente. Il PC deve avere la radio Bluetooth se ha superato il controllo di compatibilità della realtà mista. Da verificare:

* Aprire "Gestione dispositivi".
* Espandere la sezione Bluetooth e cercare un adattatore.

![Screenshot di un esempio di Gestione dispositivi. Adapter è la radio Bluetooth.](images/devicemanagerbtadapterpic.png)

Se il PC non dispone di Bluetooth, usare pluggable USB Bluetooth 4.0 Low Energy Micro Adapter(Micro adapter Bluetooth 4.0 a basso consumo).

## <a name="wi-fi-slows-down-on-my-notebook-when-motion-controllers-are-turned-on"></a>Wi-Fi rallenta nel notebook quando i controller del movimento sono attivati

Il notebook può condividere la propria antenna Wi-Fi bluetooth quando è connesso a un punto di accesso a 2,4 GHz. Controllare in Gestione dispositivi se è possibile impostare la preferenza di banda su 5 GHz. Se una rete a 5 GHz non è disponibile e le prestazioni sono gravemente interessate, è consigliabile usare un dongle Bluetooth.

![Le impostazioni di selezione della banda Wi-Fi sono disponibili tramite Gestione dispositivi](images/wifi5ghz.png)

## <a name="my-pc-has-bluetooth-technology-but-im-having-problems-with-my-controllers&quot;></a>Il PC ha la tecnologia Bluetooth, ma si verificano problemi con i controller

I controller di movimento devono funzionare con altre tastiere Bluetooth, mouse e controller di gioco. L'esperienza varia a seconda del modello di tastiera, mouse o controller di gioco in uso. Ecco alcune operazioni che è possibile eseguire per migliorare le prestazioni:

* Se il computer dispone di Bluetooth ma si verificano ancora problemi con i controller di movimento, valutare la possibilità di sostituire la radio Bluetooth con un adattatore Bluetooth esterno collegabile collegato a USB. È possibile avere un solo adattatore radio Bluetooth attivo alla volta. Se si collega una radio esterna insieme a una radio esistente, è necessario disabilitare la radio Bluetooth esistente in Gestione dispositivi. Fare clic con il pulsante destro del mouse sulla scheda e scegliere &quot;Disabilita dispositivo&quot; e annullare l'associazione/riasscoma tutti i dispositivi Bluetooth precedenti.
* Se si usa un adattatore Bluetooth USB, collegarlo a una porta USB 2.0 (le porte 2.0 sono spesso nere e non sono etichettate come &quot;SS"), se disponibili. La porta deve essere fisicamente separata da:
    - connettore USB HMD
    - unità flash
    - dischi rigidi
    - Ricevitori USB wireless come quelli per tastiere/mouse Idealmente, collegare l'adattatore Bluetooth USB sul lato opposto del computer il più possibile da questi altri connettori.
* Chiudere la finestra Impostazioni Bluetooth, se aperta. Lasciarlo aperto in background significa che vengono effettuate molte chiamate aggiuntive al protocollo Bluetooth.
* Se il visore è associato al PC, usare lo stack di driver Bluetooth di Windows e non installare stack di driver Bluetooth di terze parti. Il software di terze parti potrebbe non funzionare correttamente.
* Disabilitare l'impostazione "Show notification to connect using Swift Pair" (Mostra notifica per la connessione tramite coppia Swift) in "Bluetooth & altri dispositivi" per ridurre l'attività di scansione radio dell'host.
* Se si usa una scheda Bluetooth interna, assicurarsi di usare un'antenna Bluetooth esterna o che si verifichino problemi di rilevamento. Se non funziona, usare un dongle Bluetooth esterno (USB) dopo aver disabilitato il Bluetooth interno.
* Il dispositivo dovrebbe essere visualizzato nella categoria "Mouse, & penna" nelle impostazioni Bluetooth. Se si trova in "Altri dispositivi", annullare l'associazione e associare il dispositivo.
* Rimuovere, disassociare e spegnere le cuffi e gli altoparlanti Bluetooth. Questi non sono supportati con Windows Mixed Reality. Usare il jack per le cuffi o gli altoparlanti integrati nel visore VR di realtà mista per ottenere un'esperienza audio ottimale.

## <a name="my-second-controller-takes-a-long-time-to-reconnect"></a>La riconnessione del secondo controller richiede molto tempo

Questo problema si verifica in alcune radio Intel meno recenti se i controller del movimento sono acceso contemporaneamente. Evitare l'accensione dei controller contemporaneamente.

## <a name="my-qualcomm-bluetooth-radio-cannot-pair-controllers-after-a-pc-crash"></a>La radio Bluetooth Qualcomm non può associare controller dopo un arresto anomalo del PC

I driver radio Bluetooth Qualcomm (QCA) precedenti alla versione 10.0.0.448 potrebbero non essere corretti dopo un arresto anomalo di Windows. Spegnere completamente il PC per risolvere questo problema.

## <a name="im-experiencing-poor-controller-tracking-with-marvell-radio"></a>Si è verificato un monitoraggio del controller insod toto con la radio DiLlol

Passare **a Device Manager > Bluetooth > Bluetooth > Bluetooth Radio Adapter > Properties > Driver** (Proprietà > Driver) e assicurarsi di usare il driver 15.68.9210.47 o versione successiva.

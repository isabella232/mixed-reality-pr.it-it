---
title: Domande frequenti sul controller di movimento
description: Controller per la risoluzione dei problemi della realtà mista di Windows che va oltre la documentazione standard del supporto clienti.
author: hferrone
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Realtà mista di Windows, realtà mista, realtà virtuale, VR, MR, risoluzione dei problemi, errori, guida, supporto tecnico, controller di movimento
appliesto:
- Windows 10
ms.openlocfilehash: 7d3cdae2e098504a755369e3c829c1d4a6142b9d
ms.sourcegitcommit: 2da7e181e4e23eed31b59f0332c3ba8b3f594cd0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2020
ms.locfileid: "93132025"
---
# <a name="motion-controller-faqs"></a>Domande frequenti sul controller di movimento

## <a name="what-do-the-vibrations-and-lights-mean"></a>Cosa significano le vibrazioni e le luci

L'anello della costellazione LED e haptics indicano lo stato del controller di movimento.

| Stato    | Comportamento associato allo stato | Come ottenere/uscire dallo stato |
|----------------------------|-----------------------------|----------------------------------------------------------------------|
| **Accendere**               | I LED accendono e il controller vibra una volta. | Premere e tenere premuto il pulsante Windows sul controller per due secondi per accendere il controller.  |
| **Spegnimento**              |  I LED si spengono e il controller viene vibrato due volte. | Premere e tenere premuto il pulsante Windows sul controller per quattro secondi per disattivare il controller.   |
| **Sospeso**               |  I LED si spengono e lampeggiano ogni tre secondi in stato di sospensione. | Il controller passa automaticamente allo stato di sospensione quando non è in movimento per 30 secondi. Il controller viene riattivato quando rileva il movimento, tranne nel caso in cui il dispositivo non sia associato al PC host. Premere il pulsante per riattivarlo. |
| **Abbinamento**                |  I LED passano lentamente in modalità di associazione e diventano solidi quando si esce dalla modalità di associazione. Il controller vibra una volta se l'associazione ha avuto esito positivo o tre volte se l'associazione ha esito negativo e si verifica il timeout. | Premere e tenere premuto il pulsante di associazione nel caso della batteria per tre secondi.     |
| **Connessione/disconnessione del controller dal PC** |  Il controller vibra una volta sulla connessione del PC o sulla disconnessione. | Questo errore si verifica quando il controller si connette correttamente al PC dopo averlo acceso o se il controller si disconnette dal PC durante l'uso.|
| **Livello batteria basso**      | Haptics sono disabilitati quando la batteria è bassa (non è presente alcuna indicazione LED). L'icona indicatore batteria sulla maniglia del controller in cuffia Visualizza 1/4 quando la batteria è insufficiente. | Sostituire le batterie. | 
| **Livello di batteria critico** |  Il controller vibra tre volte quando lo si accende e quindi si disattiva automaticamente. L'icona dell'indicatore della batteria diventa rossa. | Sostituire le batterie. Se il problema persiste, [ripristinare le impostazioni di fabbrica del dispositivo](motion-controller-problems.md#how-can-i-restore-the-controllers-to-factory-settings)|

## <a name="my-motion-controllers-arent-working-properly"></a>I controller di movimento non funzionano correttamente

Se i [controller di movimento](controllers-in-wmr.md) non funzionano, non si connettono o se non viene visualizzata un'immagine dei controller quando si indossa la cuffia, provare a eseguire le operazioni seguenti:

1. Verificare che i controller siano accesi. Per attivarli, tenere premuto il pulsante Windows per due secondi.
2. Verificare che i controller siano completamente addebitati e sostituire le batterie in caso contrario.
3. Spegnere e riaccendere i controller tenendoli davanti all'utente. Premere e tenere premuto il pulsante Windows per quattro secondi per spegnere un controller, quindi premerlo e tenerlo premuto per due secondi per attivarlo.
4. Controllare se i controller di movimento sono [abbinati correttamente](controllers-in-wmr.md#pair-motion-controllers).
5. Controllare i LED dei controller di movimento: i controller con illuminazione luminosa sono abbinati e connessi, i controller debolmente illuminati non sono connessi.
6. Passare a **Start > portale per la realtà mista** nel PC e selezionare "menu". Verranno visualizzati i controller di movimento, insieme a un messaggio di stato:
    * Pronto: tutti i controller sono impostati.
    * Rilevamento perso: il portale per la realtà mista non riesce a trovare i controller. Tenerli davanti all'auricolare e riavviarli premendo il pulsante Windows per quattro secondi, quindi di nuovo per due secondi.
    * Batteria insufficiente: sostituire le batterie del controller.
7. Se si usa un adattatore Bluetooth USB esterno, assicurarsi che sia collegato a una porta USB 2,0 (spesso ma non sempre nero). Deve anche essere collegato per quanto possibile da qualsiasi altro trasmettitore wireless o unità flash USB, incluso il connettore USB per la cuffia. 
8. Per verificare la presenza di una sola radio Bluetooth nel computer, passare a **Device Manager > Bluetooth** e cercare una scheda. Se si usa la configurazione di desktop PC con la radio predefinita, controllare se è connessa un'antenna esterna. Se non è presente alcuna antenna esterna connessa, può causare problemi di rilevamento. In alternativa, usare un dongle Bluetooth esterno (USB), disabilitare la funzionalità Bluetooth interna e ritentare l'associazione e la connessione.
9. Se la finestra Impostazioni Bluetooth è aperta in background, vengono effettuate molte chiamate aggiuntive al protocollo Bluetooth. Chiuderlo.
10. Controllare il livello di batteria virtuale sul controller di movimento trasformando i controller in realtà mista per visualizzare l'icona della batteria. Attendere circa 15 secondi prima di leggere il livello, perché il livello segnalato è superiore al livello effettivo immediatamente dopo la connessione di un controller. Sostituire le batterie se l'icona è rossa.
11. Rimuovere cuffie e altoparlanti Bluetooth in **impostazioni > dispositivi > Bluetooth & altri dispositivi** e spegnere i dispositivi. Usare i jack per la cuffia o i relatori incorporati in un auricolare a realtà mista per ottenere la migliore esperienza audio.
12. Rimuovere gli altri dispositivi Bluetooth che possono essere associati al PC, ad esempio cuffie o gamepad. Passare a **impostazioni > dispositivi > Bluetooth & altri dispositivi** , selezionare i dispositivi e quindi "Rimuovi dispositivo".
13. Scollegare il cavo USB sulla cuffia e collegarlo di nuovo al PC per riavviare la realtà mista di Windows.
14. Il controller lampeggia quando è in fase di aggiornamento del firmware. Attendere il completamento dell'aggiornamento e i controller dovrebbero essere visualizzati in realtà mista.
15. Verificare che il PC sia connesso a una rete Wi-Fi 5GHz. Se il computer portatile è connesso a una rete Wi-Fi a 2,4 GHz, in genere condivide la connessione Bluetooth. Questo potrebbe influire negativamente sulle prestazioni Wi-Fi o Bluetooth, a seconda della progettazione del prodotto. Modificare la banda preferita in 5 GHz nelle impostazioni della scheda di rete. Se la rete non supporta 5GHz, è possibile usare un dongle Bluetooth al posto della funzionalità Bluetooth interna.
16. Se le impostazioni Bluetooth hanno controller di movimento già abbinati, Windows non individuerà i nuovi dispositivi fino a quando non vengono rimossi (se sono stati aggiunti usando un dongle specifico, possono essere rimossi solo con tale dongle).
17. Se il PC dispone di Bluetooth integrato e si verificano problemi di connessione, provare a usare una scheda Bluetooth USB. A tale scopo, disattivare la radio Bluetooth incorporata in Device Manager, quindi abbinare gli altri dispositivi Bluetooth con la nuova scheda.

## <a name="my-controllers-jitter-get-stuck-or-flicker-and-disappear-in-mixed-reality"></a>I miei controller si nervosano, si bloccano o sfarfallano e scompaiono in realtà mista

* Se il PC è in esecuzione su un Wi-Fi 2,4 GHz, passare a un Wi-Fi a 5 GHz. 
* Se si usa una scheda Bluetooth esterna, verificare che sia collegata a una porta USB 2,0 (spesso, ma non sempre, nero), da altri trasduttori wireless o unità flash USB.
* Eseguire lo strumento di risoluzione dei problemi Bluetooth in **impostazioni > aggiornamento & sicurezza > risolvere i problemi > Bluetooth** .

## <a name="my-controller-is-stuck-in-an-infinite-reboot"></a>Il controller è bloccato in un riavvio infinito

Si tratta di un indicatore di batteria essenziale. Inserire batterie aggiornate nel dispositivo. se il problema persiste, [ripristinare le impostazioni predefinite del controller](motion-controller-problems.md#how-can-i-restore-the-controllers-to-factory-settings).

## <a name="the-mixed-reality-portal-is-working-but-my-controllers-are-tracking-poorly-flying-away-shaking-etc"></a>Il portale per la realtà mista funziona, ma i miei controller si rilevano male (in volo, tremando e così via).

1. Le condizioni di illuminazione possono influire sul rilevamento. Assicurarsi di non essere esposti alla luce solare diretta e che non si disponga di una grande quantità di punti luce visibili ai HMD (ad esempio, stringhe di luci come un albero di Natale).
2. Questi sintomi sono in genere causati da errori di comunicazione tra il controller e il PC host e indicano una scarsa qualità del collegamento Bluetooth. Vedere le [domande su Bluetooth](motion-controller-problems.md#how-can-i-tell-if-im-using-bluetooth-technology).

## <a name="motion-controller-leds-are-not-lit-but-the-buttons-and-thumbstick-still-work-in-mixed-reality-portal"></a>I LED del controller di movimento non sono accesi, ma i pulsanti e levetta funzionano ancora nel portale di realtà mista

La cache di calibrazione del controller di movimento potrebbe essere danneggiata. Per eliminare la cache, eseguire il comando seguente in un prompt dei comandi dell'amministratore:

`rmdir /S /Q C:\Windows\ServiceProfiles\LocalService\AppData\Local\Microsoft\Windows\MotionController\Calibration`

Questa cartella non è accessibile in Esplora risorse e può essere modificata solo da un prompt dei comandi dell'amministratore. Dopo aver eliminato la cartella, riavviare il PC e riconnettere i controller di movimento per ripristinare i file di calibrazione.

## <a name="my-controller-looks-like-a-viveoculus-has-strange-orientation-or-the-buttons-are-incorrectly-mapped"></a>Il mio controller ha un aspetto di vive/Oculus, presenta un orientamento strano oppure i pulsanti sono mappati in modo errato

Il sito Web probabilmente non dispone del supporto per il controller di movimento completo.

## <a name="my-motion-controllers-do-not-appear-in-steamvr-apps-and-games"></a>I controller di movimento non vengono visualizzati nelle app e nei giochi di SteamVR

Prima di tutto, assicurarsi che vengano addebitate le batterie del controller. I controller non funzioneranno se le batterie non sono presenti o sono in stato di morte

Se è possibile visualizzare i controller nella casa scogliera ma non nelle app e nei giochi SteamVR, il driver del modello di motion controller potrebbe non essere installato correttamente. Per verificare che il driver del modello del controller di movimento sia installato correttamente:

1. Attivare entrambi i controller di movimento. Controllare se i controller di movimento sono [abbinati correttamente](controllers-in-wmr.md#pair-motion-controllers).
2. Passare a **Device Manager > Bluetooth** e cercare "motion controller".
3. Selezionare il dispositivo e quindi fare clic su **visualizza > dispositivi per connessione** .
4. Passare a **impostazioni di sistema > dispositivi > Bluetooth & altri dispositivi > altri dispositivi** per verificare se sono visibili. Ci saranno due dispositivi "dispositivo HID Bluetooth" e in ogni dispositivo HID Bluetooth dovrebbero essere i dispositivi denominati "motion controller" (con icone grigio) nello stesso nodo del controller di movimento.
5. Fare doppio clic su ogni dispositivo "motion controller" e passare alla scheda "driver". Verificare che la versione del driver elencata corrisponda a una di [queste versioni](mixed-reality-software.md#mixed-reality-motion-controller-model-driver-release-history).
6. In caso contrario, eseguire Windows Update, che consente di scaricare e installare automaticamente il driver. Se si usa un PC con criteri aziendali o se Windows Update è diversamente limitato, potrebbe essere necessario installare manualmente il driver del modello di motion controller. A tale scopo, visitare [Questa pagina](mixed-reality-software.md#mixed-reality-motion-controller-model-driver-release-history) e cercare la versione del driver corrispondente alla versione di Windows 10. Le istruzioni di installazione sono disponibili nella pagina di download.

## <a name="the-controller-firmware-update-takes-significantly-longer-than-two-minutes"></a>L'aggiornamento del firmware del controller richiede molto più di due minuti

Vedere la [sezione domande sul Bluetooth](motion-controller-problems.md#how-can-i-tell-if-im-using-bluetooth-technology). Una scarsa qualità dei collegamenti Bluetooth causa in genere questi problemi.

## <a name="i-just-inserted-fresh-batteries-but-the-controller-virtual-battery-level-does-not-indicate-full-level"></a>Ho appena inserito batterie nuove, ma il livello di batteria virtuale del controller non indica il livello completo

Il livello di batteria del controller di movimento viene ottimizzato per le batterie AA. Alcune batterie ricaricabili a bassa tensione potrebbero non essere segnalate come complete anche se sono completamente addebitate.

## <a name="my-samsung-motion-controllers-touchpad-is-off-center-or-has-a-dead-spot"></a>Il touchpad di Samsung Motion controller è esterno al centro o ha un punto morto

Si tratta probabilmente di un difetto hardware ed è necessario tornare al rivenditore o al produttore dell'apparecchiatura per un sostituto o uno scambio.

## <a name="how-can-i-restore-the-controllers-to-factory-settings"></a>Come è possibile ripristinare le impostazioni predefinite dei controller

Ripristinare le condizioni di fabbrica (sono necessarie batterie aggiornate):

1. Scollegare e spegnere i controller.
2. Aprire il coperchio della batteria.
3. Inserire le nuove batterie.
4. Premere e tenere premuto il pulsante di associazione (la scheda nella parte inferiore sotto le batterie).
5. Tenendo premuto il pulsante di associazione, accendere il controller premendo e tenendo premuto il pulsante Windows per cinque secondi (tenere premuto entrambi i pulsanti).
6. Rilasciare i pulsanti e attendere l'accensione del controller. Questa operazione richiede fino a 15 secondi e non ci sono indicatori quando si verifica il ripristino del dispositivo. Se il dispositivo attiva immediatamente il rilascio del pulsante, la sequenza dei pulsanti di ripristino non viene registrata ed è necessario riprovare.
7. Se i controller sono stati abbinati al PC, passare a **impostazioni > Bluetooth > altri dispositivi** e selezionare "motion controller" e "Rimuovi dispositivo" per rimuovere le associazioni del controller da impostazioni Bluetooth.
8. [Associare nuovamente i controller](controllers-in-wmr.md#pair-motion-controllers) alla cuffia o al PC.
9. Dopo la connessione con l'host e l'auricolare, il dispositivo viene aggiornato al firmware più recente disponibile.

## <a name="can-i-pair-my-xbox-controller-to-my-pc-so-i-can-use-it-in-headset"></a>È possibile associare il controller Xbox al PC per poterlo usare in cuffia

È possibile associare un controller Xbox Bluetooth per usarlo con l'auricolare seguendo [queste istruzioni](https://support.xbox.com/help/hardware-network/accessories/connect-and-troubleshoot-xbox-one-bluetooth-issues).

Se si dispone di un controller Xbox cablato, collegarlo al PC.

Alcuni giochi e app usano il controller Xbox in modo diverso rispetto a quello usato in realtà mista. Per usare il controller per un gioco o un'app, selezionare "USA come gamepad" sulla barra dell'app o "USA come gamepad". Per riportare il controller alla realtà mista, selezionare di nuovo "USA come gamepad" oppure "USA con lo sguardo". 

## <a name="how-do-i-pair-new-controllers-if-windows-mixed-reality-is-already-set-up-on-my-pc"></a>Ricerca per categorie associare nuovi controller se la realtà mista di Windows è già configurata nel PC

Se si abbinano i controller alla cuffia, usare l'app complementare (il [portale per la realtà mista](install-windows-mixed-reality.md#launch-mixed-reality-portal) può aiutare a trovare un'app complementare per avviare o fornire un elenco di app complementari che è possibile selezionare).

## <a name="how-can-i-return-my-controllers-to-their-factory-pairing"></a>Come è possibile ripristinare i controller nell'associazione di Factory

Per riportare i controller di movimento alla propria associazione di fabbrica, in alternativa, per associarli a un auricolare di realtà mista di Windows con la radio Bluetooth incorporata, eseguire l'app complementare del dispositivo dell'auricolare (ad esempio, l'app "Acer ' 500" o "Samsung HMD Odyssey + Setup", installata automaticamente la prima volta che l'auricolare è collegata) e seguire le istruzioni per l'associazione del controller di movimento.

## <a name="my-motion-controllers-are-not-pairing-to-my-pc"></a>I controller di movimento non sono associati al PC

* Se i controller non vengono attivati, inserire batterie aggiornate. Se il problema persiste, ripristinare le impostazioni di fabbrica del dispositivo accendendo il dispositivo tenendo premuto i pulsanti di associazione. Per ulteriori informazioni, vedere la [procedura di ripristino del dispositivo](motion-controller-problems.md#how-can-i-restore-the-controllers-to-factory-settings) .
* Se i controller si attivano e si utilizza una scheda Bluetooth esterna, verificare che la scheda sia collegata a una porta USB 2,0, che è spesso, ma non sempre, nera, lontano da altri trasduttori wireless o unità flash USB. Se il problema persiste, eseguire lo strumento di risoluzione dei problemi Bluetooth in impostazioni > aggiornamento & sicurezza > risolvere i problemi > Bluetooth.
* Se si usa una scheda Qualcomm e il PC si è arrestato in modo anomalo, riavviare il computer.
* Provare a riavviare i controller di movimento che non sono associati, uno alla volta, quindi riavviare il computer.
* La cache del controller di movimento potrebbe essere danneggiata. Per risolvere il problema, vedere questi [passaggi](motion-controller-problems.md#motion-controller-leds-are-not-lit-but-the-buttons-and-thumbstick-still-work-in-mixed-reality-portal).
* Se nessuna di queste procedure corregge il problema, contattare il produttore.

## <a name="my-paired-controllers-dont-show-up-in-the-mixed-reality-portal"></a>I controller associati non vengono visualizzati nel portale per la realtà mista

* Mantenere i controller davanti alla cuffia e riavviarli premendo il pulsante Windows per quattro secondi, quindi di nuovo per due secondi.
* Se i controller vengono visualizzati come connessi, non è possibile associarli ed eseguire di nuovo il [processo di associazione](controllers-in-wmr.md#pair-motion-controllers) .
* Se i LED del controller sono in bicicletta, l'accensione di un quadrante di luci alla volta e la loro disattivazione sono in fase di aggiornamento del firmware. Attendere il completamento dell'aggiornamento e i controller dovrebbero essere visualizzati in realtà mista.
* Se viene usata una scheda Bluetooth esterna, verificare che la scheda sia collegata a una porta USB 2,0 (che in genere è nera), a partire da altri trasduttori wireless o dispositivi USB 3,0.
* Se il PC si è arrestato in modo anomalo e viene usata una scheda Qualcomm, una reimpostazione potrebbe non funzionare. Per risolvere questo problema, scollegare l'alimentazione dal retro del computer (o, se si è in un computer portatile, tenendo premuto il pulsante di alimentazione per 10 secondi) e riavviare il computer.
* Eseguire lo strumento di risoluzione dei problemi Bluetooth in **impostazioni > aggiornamento & sicurezza > risolvere i problemi > Bluetooth** .  

## <a name="im-trying-to-pair-my-controllers-but-they-never-show-up-in-the-add-a-new-device-menu-in-bluetooth-settings"></a>Sto tentando di associare i controller, ma non vengono mai visualizzati nel menu "Aggiungi un nuovo dispositivo" nelle impostazioni Bluetooth

Verificare che non siano già stati associati controller. In caso contrario, rimuoverli e riprovare. Riavviare il computer se il problema persiste. Se il tentativo non riesce, vedere altre [informazioni su Bluetooth](motion-controller-problems.md#how-can-i-tell-if-im-using-bluetooth-technology).

Nota: se un altro set di controller di movimento è associato al PC, sarà necessario disaccoppiare tali controller prima di associarne di nuovi. Se un set di controller di movimento è stato associato al PC corrente e quindi abbinato a un secondo PC, sarà necessario disaccoppiarli e riassociarli al PC corrente prima di riutilizzarli.

## <a name="how-can-i-tell-if-im-using-bluetooth-technology"></a>Come è possibile stabilire se si usa la tecnologia Bluetooth

I controller di movimento usano la stessa tecnologia Bluetooth disponibile in molti dispositivi consumer e sono progettati per funzionare con la funzionalità Bluetooth inclusa in tutti i PC recenti. Il PC deve avere la radio Bluetooth se ha superato il controllo di compatibilità della realtà mista. Da verificare:

* Aprire "Device Manager".
* Espandere la sezione Bluetooth e cercare un adapter.

![Screenshot di un esempio Device Manager. L'adapter è la radio Bluetooth.](images/devicemanagerbtadapterpic.png)

Se il PC non ha Bluetooth, usare la scheda micro USB Bluetooth 4,0 a basso consumo.

## <a name="wi-fi-slows-down-on-my-notebook-when-motion-controllers-are-turned-on"></a>Wi-Fi rallenta il notebook quando i controller di movimento sono accesi

Il notebook può condividere l'antenna Wi-Fi con Bluetooth quando si è connessi a un punto di accesso a 2,4 GHz. Archiviare Device Manager se è possibile passare alla preferenza della banda a 5GHz. Se una rete 5GHz non è disponibile e le prestazioni hanno un notevole effetto, provare a usare un dongle Bluetooth.

![È possibile trovare le impostazioni di selezione banda Wi-Fi tramite Gestione dispositivi](images/wifi5ghz.png)

## <a name="my-pc-has-bluetooth-technology-but-im-having-problems-with-my-controllers"></a>Il PC ha la tecnologia Bluetooth ma si verificano problemi con i controller

I controller di movimento dovrebbero funzionare con altre tastiere, topi e controller di gioco Bluetooth, ma l'esperienza varia a seconda del modello di tastiera, mouse o controller di gioco che usi. Ecco alcune operazioni che è possibile eseguire per migliorare le prestazioni:

* Se il computer dispone di Bluetooth ma si verificano ancora problemi con i controller di movimento, sostituire la radio Bluetooth con una scheda Bluetooth esterna collegabile collegata al dispositivo USB. È possibile disporre di un solo adattatore radio Bluetooth attivo alla volta. Se si collega un'altra radio, oltre a una radio esistente, è necessario disabilitare la radio Bluetooth esistente in Device Manager (fare clic con il pulsante destro del mouse sulla scheda e selezionare "Disabilita dispositivo") e annullare la coppia/riassociare tutti i dispositivi Bluetooth precedenti.
* Se si usa una scheda Bluetooth USB, connetterla a una porta USB 2,0 (2,0 porte sono spesso nere e non sono etichettate "SS"), se disponibile. La porta deve essere fisicamente separata da:
    - connettore USB HMD
    - unità flash
    - unità disco rigido
    - i ricevitori USB wireless come quelli per tastiere/topi sono idealmente collegati al più possibile da questi altri connettori per collegare la scheda Bluetooth USB al lato opposto del computer.
* Chiudere la finestra Impostazioni Bluetooth se è aperta. Lasciarla aperta in background significa che vengono effettuate numerose chiamate aggiuntive al protocollo Bluetooth.
* Se l'auricolare è associato al PC, usare lo stack di driver Bluetooth di Windows e non installare gli stack di driver Bluetooth di terze parti. Il software di terze parti potrebbe non funzionare correttamente.
* Disabilitare l'impostazione "Mostra notifica per la connessione tramite una coppia Swift" in "Bluetooth & altri dispositivi" per ridurre l'attività di analisi radio host.
* Se si usa una scheda Bluetooth interna, assicurarsi che si stia usando un'antenna Bluetooth esterna o che si verifichino problemi di rilevamento. Se questa operazione non funziona, usare un dongle Bluetooth esterno (USB) dopo aver disattivato il Bluetooth interno.
* Il dispositivo dovrebbe essere visualizzato sotto la categoria "mouse, tastiera & Pen" nelle impostazioni Bluetooth. Se si trova in "altri dispositivi", disaccoppiare e associare il dispositivo.
* Rimuovere, rimuovere le coppie e spegnere cuffie e altoparlanti Bluetooth. Questi non sono supportati con la realtà mista di Windows. Usare i jack per la cuffia o i relatori incorporati in un auricolare a realtà mista per ottenere la migliore esperienza audio.

## <a name="my-second-controller-takes-a-long-time-to-reconnect"></a>Il secondo controller impiega molto tempo per la riconnessione

Alcune versioni precedenti di Intel radio hanno riscontrato questo problema se i controller di movimento sono accesi nello stesso momento. Evitare di accendere i controller allo stesso tempo.

## <a name="my-qualcomm-bluetooth-radio-cannot-pair-controllers-after-a-pc-crash"></a>Non è possibile associare i controller a un arresto anomalo del PC

I driver radio del dispositivo Qualcomm (QCA) prima di 10.0.0.448 potrebbero finire in uno stato non valido dopo un arresto anomalo di Windows. Spegnere completamente il PC per aggirare questo problema.

## <a name="im-experiencing-poor-controller-tracking-with-marvell-radio"></a>Si verificano problemi di rilevamento del controller con la radio Marvell

Passare a **Device Manager > bluetooth > Marvell avastr bluetooth > proprietà > driver** e assicurarsi di utilizzare driver 15.68.9210.47 o versione successiva.

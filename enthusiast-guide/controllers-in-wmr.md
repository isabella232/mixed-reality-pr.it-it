---
title: Controller in Windows Mixed Reality
description: Informazioni su come configurare e usare i controller in realtà mista di Windows.
author: hferrone
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Realtà mista di Windows, realtà mista, realtà virtuale, VR, MR, feedback, Hub feedback, bug
appliesto:
- Windows 10
ms.openlocfilehash: 56238f302074bb4de21acbc0575f4ab913cb84b1
ms.sourcegitcommit: 5eb27475f8616c9d4f95b4b386a5bd0d22f41125
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2020
ms.locfileid: "92174420"
---
# <a name="motion-controllers-in-windows-mixed-reality"></a>Controller di movimento in realtà mista di Windows

I controller di movimento sono accessori hardware che consentono agli utenti di intervenire in realtà mista. Un vantaggio dei controller di movimento rispetto ai movimenti è che i controller hanno una posizione precisa nello spazio, consentendo un'interazione con granularità fine con gli oggetti digitali. Per gli auricolari a realtà mista di Windows, i controller di movimento sono il modo principale in cui gli utenti interverranno in tutto il mondo.
I controller di movimento per la realtà mista di Windows offrono un tracking preciso e reattivo del movimento nel campo della visualizzazione usando i sensori nell'auricolare immersiva, ovvero non è necessario installare hardware nei muri dello spazio. Questi controller di movimento offriranno la stessa facilità di installazione e portabilità come gli auricolari immersivi a realtà mista di Windows.

La realtà mista di Windows è progettata per funzionare meglio con i controller di movimento della realtà mista, che forniscono interazioni naturali e precise senza necessità di installare hardware sulle pareti.

È anche possibile usare un controller Xbox, un mouse e una tastiera o aggirare [usando solo la voce](using-speech-in-wmr.md).

**Funzionalità**

* Rilevamento ottico
* Trigger
* Pulsante di cattura
* Levetta
* Touchpad

## <a name="motion-controller-setup"></a>Impostazione del controller di movimento

La maggior parte degli auricolari viene abbinata direttamente alla cuffia, ma alcune cuffie iniziali richiedono che i controller di movimento siano abbinati al PC con Bluetooth 4,0. Quando si connette la cuffia per la prima volta, si passa all'attivazione dei controller di movimento durante l'installazione. Tuttavia, se è necessario riassociarli in un secondo momento, ecco come:

1. Avviare il **portale di realtà mista** con la cuffia connessa.  
2. Nell'angolo in basso a sinistra selezionare **... > configurare i controller**.
3. Inserire 2 batterie AA in ogni controller e attivare la modalità di associazione del controller (vedere le istruzioni nella sezione controller di movimento pair)
4. Seguire le istruzioni fornite sullo schermo.

> [!NOTE]

> * Per i controller che si abbinano direttamente al PC, è necessario inserirli in modalità di associazione attivando e quindi premendo il pulsante di associazione all'interno del compartmento della batteria fino a quando le luci iniziano a lampeggiare.  
> * I controller di movimento supportano solo l'accoppiamento a un computer o a un PC alla volta. Se è necessario usarli con un'altra cuffia, è necessario eseguire il processo di associazione. Vedere [configurare la realtà mista di Windows](set-up-windows-mixed-reality.md)

[Ottenere assistenza per la connessione](wmr-setup-faq.md#my-motion-controllers-arent-working)

> [!IMPORTANT]
> **Hai un controller Xbox?**
> 
> Se si dispone di un controller Xbox Bluetooth, associarlo al PC per usarlo con l'auricolare.
> 
> Se si dispone di un controller Xbox cablato, collegarlo al PC.
> 
> Alcuni giochi e app usano il controller Xbox in modo diverso rispetto a come viene usato in realtà mista. Per usare il controller per un gioco o un'app, selezionare **Usa come gamepad** sulla barra dell'app o "USA come gamepad". Per riportare il controller alla realtà mista, selezionare **Usa come gamepad**, nuovamente oppure "USA con lo sguardo".  

## <a name="pair-motion-controllers"></a>Controller di movimento delle coppie

Accendere i controller premendo il pulsante Windows per 2 secondi fino alla luce dei LED.

Rimuovere il coperchio della batteria dai controller e trovare il piccolo pulsante di associazione al bordo del controller. Premere questo pulsante per associarlo al PC.

Se si usa l'auricolare HP Reverb G2, i controller devono essere già abbinati. Tuttavia, è possibile associare i controller usando l'app di configurazione HP reverbi G2 VR (dovrebbe essere già installata durante la configurazione. È anche possibile ottenerlo da Microsoft Store. È anche possibile associare il controller a un PV aggiungendo un altro dispositivo Bluetooth:

* Passa a impostazioni computer
* Dispositivo/Aggiungi Bluetooth o altro dispositivo.

![Associazione del controller di movimento](images/connect_controller.png)

È possibile che venga visualizzato un messaggio nell'angolo in basso a destra dello schermo quando il firmware sui controller viene aggiornato. Quando si verifica questa situazione, è possibile passare al passaggio successivo dell'esercitazione, ma non disattivare i controller.

Al termine dell'aggiornamento del firmware del controller, verrà riavviato e riconnesso al PC host. I LED saranno solidi e luminosi.

### <a name="common-issues"></a>Problemi comuni

* Verificare che nel PC sia attiva una sola radio Bluetooth. Se si dispone di più di una radio Bluetooth, sarà necessario disabilitare le altre radio in Device Manager.
* Posizionare il dongle Bluetooth in una porta con una linea di visibilità chiara per i controller e molto altro ancora collegato ai dispositivi USB 3,0. USB 3,0 è noto come interferenza RF con Bluetooth (leggere [questo documento](https://www.intel.com/content/dam/www/public/us/en/documents/white-papers/usb3-frequency-interference-paper.pdf) da Intel per altri dettagli). Le porte USB 2,0 possono funzionare meglio per il dongle Bluetooth.
* Assicurarsi che la chiavetta Bluetooth non sia collegata a una porta USB accanto al cavo USB di HMD. Il cavo Headset è stato noto per causare interferenze con i dongle Bluetooth. Per ottenere risultati ottimali, collegare il dongle alla porta USB anteriore del computer.
* Per i notebook, verificare che il Wi-Fi sia collegato alla banda 5GHz per la migliore esperienza (selezionare l'icona della rete wireless in basso a destra e selezionare le proprietà per la rete in uso). I notebook progettati per condividere un'antenna a 2,4 GHz per la connettività Bluetooth e Wi-Fi hanno più probabilità di congestione dei dati sotto forma di velocità di rete rallentate o prestazioni di rilevamento insufficienti per i controller di movimento.
* I controller di movimento riceveranno periodicamente nuovi aggiornamenti software da Microsoft. I controller visualizzeranno un modello alternato di spie lampeggianti quando ricevono questi nuovi aggiornamenti software. Si tratta di una situazione normale. Attendere il completamento dell'aggiornamento del software prima di usare i controller (i controller vibrano e una luce costante sostituirà il modello Flash alternato al termine).
* Prima che i controller completino il processo di aggiornamento, è possibile che venga richiesto di inserire la cuffia e usare levetta per teletrasportarsi ". I controller non saranno visibili o utilizzabili fino al completamento dell'aggiornamento. La maggior parte degli aggiornamenti si verifica entro due minuti, ma gli aggiornamenti possono richiedere fino a 10 minuti. Attendere il completamento dell'aggiornamento prima di procedere al passaggio successivo.

## <a name="using-controllers"></a>Uso di controller

Ecco come aggirare la realtà mista con i controller di movimento, un gamepad Xbox o un mouse e tastiera.

> [!TIP]
> Per cambiare l'input tra la realtà mista e il desktop, premere il **tasto logo Windows + Y** sulla tastiera del PC.

![Mapping del pulsante del controller di movimento](images/get_to_know_controllers.png)

|  Operazione da eseguire  |  Controller del movimento  | Game pad | Mouse + tastiera |
| --- | --- | --- | --- |
| Teletrasporto | Premere il levetta in poi, quindi puntare il controller in cui si desidera passare. Rilasciare il levetta. | Premere il levetta di sinistra in poi, quindi cercare la posizione desiderata. Rilasciare il levetta. | Fare clic e tenendo premuto il pulsante destro, quindi puntare il puntatore del mouse sul punto in cui si desidera passare. Rilasciare il pulsante. |
| Select | Puntare il controller, quindi tirare il trigger o fare clic sul touchpad. | Osservare la destinazione, quindi premere. | Puntare il mouse, quindi fare clic con il pulsante sinistro del mouse. |
| Aprire il menu Start | Premere il pulsante **Windows** . | Premere il pulsante **Xbox** . | Premere il **tasto logo Windows**. |
| Uscire da un'app immersiva | Premere il pulsante **Windows** . Quindi selezionare **Home realtà mista** dal menu azioni rapide. | Premere il pulsante **Xbox** . Quindi selezionare il pulsante **Home realtà mista** nel menu azioni rapide. | Premere il **tasto logo Windows**. Quindi selezionare il pulsante **Home realtà mista** nel menu azioni rapide visualizzato. |
| Ruota | Spostare il levetta a sinistra o a destra. | Spostare il lato destro verso sinistra o verso destra. | Non disponibile. |
| Eseguire il backup | Spostare il levetta indietro. | Spostare il Left stick indietro. | Non disponibile. |
| Camminata | Eseguire il push del levetta verso il basso e quindi premerlo nella direzione desiderata. | Premere il pulsante sinistro del mouse verso il basso e quindi premerlo nella direzione desiderata. | Non disponibile. |
| Spostare una finestra dell'app | Puntare sulla barra dell'app. Tirare e mantenere il trigger per ottenere la finestra, quindi usare il controller per spostarlo in qualsiasi direzione. Rilasciare il trigger. | Osservare la barra dell'app, quindi tenere premuto un per selezionare la finestra. Utilizzare il Left Stick per spostare la finestra affiancata o verso l'alto e verso il basso. Usare i trigger per spostarlo più vicino e più lontano. Quindi rilasciare un. | Posizionare il puntatore del mouse sulla barra dell'app. Fare clic con il pulsante destro del mouse e tenendo premuto il pulsante del mouse per spostarlo lateralmente o verso l'alto e verso il basso. Utilizzare la rotellina di scorrimento per spostare la finestra più vicina o più lontana. Rilasciare il pulsante del mouse. |
| Spostare un oggetto 3D | Puntare all'oggetto, quindi eseguire il pull e il trigger per afferrarlo. Spostarlo in qualsiasi direzione con il controller, quindi rilasciare il trigger. | Osservare l'oggetto, quindi tenere premuto un per estrarlo. Utilizzare il Left Stick per spostare la finestra affiancata o verso l'alto e verso il basso. Usare i trigger per spostarlo più vicino e più lontano. Quindi rilasciare un. | Posizionare il puntatore del mouse sull'oggetto. Fare clic con il pulsante destro del mouse e tenerlo premuto, quindi utilizzare il mouse per spostarlo side-to-side o verso l'alto e verso il basso.  Per spostarlo più vicino o più lontano, utilizzare la rotellina di scorrimento. Rilasciare il pulsante del mouse. |
| Ruotare o ridimensionare una finestra dell'app | Puntare un controller sulla barra dell'app e sull'altro controller in un punto qualsiasi della finestra. Mantenere entrambi i trigger, quindi spostare i controller insieme o separatamente per ridimensionare.  Per ruotare, spostare un controller verso l'utente e l'altro da parte dell'utente. Rilasciare i trigger. | Selezionare **Adjust** sulla barra dell'app. Osservare un angolo del frame di regolazione, quindi premere un oggetto per selezionarlo. Usare il Left Stick per ridimensionare la finestra.  | Selezionare **Adjust** sulla barra dell'app. Selezionare e mantenere un angolo del frame di regolazione, quindi utilizzare il mouse per ridimensionare la finestra. |
| Ruotare o ridimensionare un oggetto 3D | Puntare entrambi i controller all'oggetto. Mantenere entrambi i trigger, quindi spostare i controller insieme o separatamente per ridimensionare.  Per ruotare, spostare un controller verso l'utente e l'altro da parte dell'utente. | Selezionare **Adjust** sulla barra dell'app, quindi spostare l'oggetto usando il bastone a sinistra. | Selezionare **Adjust** sulla barra dell'app e quindi selezionare e tenere premuto l'oggetto e usare il mouse per spostarlo. |
| Scorrere in una finestra dell'app | Eseguire il pull e il mantenimento del trigger, quindi spostare il controller verso l'alto o verso il basso.  | Usare il D-Pad. | Utilizzare la rotellina di scorrimento del mouse. |
| Eseguire lo zoom avanti o indietro nella finestra dell'app | Eseguire il pull di entrambi i trigger, quindi spostare i controller più vicini o più lontani. | Eseguire il pull del trigger destro per eseguire lo zoom avanti e il trigger sinistro per eseguire lo zoom indietro. | Utilizzare la rotellina del mouse tenendo premuto il tasto CTRL sulla tastiera. |
| Aprire un menu | Premere il pulsante di **menu** . | Premere il pulsante di **menu** . | Fare clic con il pulsante destro del mouse. |

## <a name="what-do-the-vibrations-and-lights-mean"></a>Cosa significano le vibrazioni e le luci

Il controller comunica a chi sta facendo vibrando e lampeggiando le luci del LED.

|  Quando il controller esegue questa operazione  |  Ciò significa che |
| --- | --- |
| I LED accendono e il controller vibra una volta | **Attivazione** |  
| I LED si spengono e il controller vibra due volte | **Disattivazione** |
| LED lampeggia ogni 3 secondi | **Sospeso** |
| LED a impulsi lenti e il controller vibra una volta | **Immissione della modalità di associazione** |
| Il controller vibra una volta | **Connessione o disconnessione dal PC** |
| LED luminosi accesi | **Controller monitorati da auricolare** |
| I LED sono debolmente illuminati | **Controller non rilevati dall'auricolare** |
| Il controller vibra tre volte e quindi si disattiva | **Livello di batteria critico** |
| Gli anelli esterni e interni dei LED lampeggiano in un modello alternato | **Aggiornamento** |

## <a name="updating-motion-controllers-firmware"></a>Aggiornamento del firmware per i controller di movimento

* Se un headset immersivo è connesso al PC ed è disponibile un nuovo firmware del controller, il firmware verrà inserito automaticamente nei controller di movimento alla successiva accensione.
* Gli aggiornamenti del firmware del controller sono indicati da un modello di illuminazione del quadrante dei LED in movimento circolare e da richiedere 1-2 minuti. Gli aggiornamenti del firmware possono richiedere talvolta più tempo, fino a 10 minuti, che potrebbero indicare una scarsa connettività Bluetooth o interferenze radio.
* Nel caso in cui l'aggiornamento del firmware venga interrotto (spegnimento del controller o esaurimento della batteria) verrà effettuato un nuovo tentativo al successivo accensione.
* Al termine dell'aggiornamento del firmware, i controller vengono riavviati e riconnessi. 
* Entrambi i controller devono essere connessi adesso. (Controllare Bluetooth e altri dispositivi per gli elementi seguenti): ![Controller connessi](images/cyk-connected.jpg)
* Verificare che i controller funzionino correttamente:
  * Avviare il **portale di realtà mista** e immettere la Home realtà mista.
  * Spostare i controller e verificare il rilevamento, i pulsanti di test e verificare il funzionamento della teleportazione. In caso contrario, vedere [la sezione risoluzione dei problemi del controller di movimento](motion-controller-problems.md)

## <a name="faq"></a>Domande frequenti

### <a name="how-can-i-check-battery-level"></a>Come è possibile controllare il livello della batteria?

*R: il livello della batteria è sul lato inverso del modello virtuale, non è presente alcun indicatore di livello di batteria fisico. Al termine dell'accensione del controller, attendere alcuni secondi per stabilizzare la lettura.*

### <a name="can-you-use-these-controllers-without-a-headset-just-for-the-joysticktriggeretc-input"></a>È possibile usare questi controller senza cuffie? Solo per l'input joystick/trigger/etc?

*R: non per le applicazioni di Windows universale*

## <a name="filing-motion-controller-feedbackbugs"></a>Suggerimenti/bug del controller di movimento di archiviazione

Inviare commenti e suggerimenti nell'hub feedback, usando la categoria "Mixed Reality-> input".

## <a name="see-also"></a>Vedere anche

* [Contattare la community](https://answers.microsoft.com)
* [Contattaci per assistenza](https://support.microsoft.com/contactus/)
* [Risoluzione dei problemi](troubleshooting-windows-mixed-reality.md)

Problemi con i controller di movimento? [Ottieni aiuto](using-wmr-faq.md#im-having-trouble-with-my-motion-controllers)

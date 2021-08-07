---
title: Controller in Windows Mixed Reality
description: Informazioni su come configurare, associare, usare e risolvere i problemi comuni con i controller Windows Mixed Reality.
author: hferrone
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Windows Mixed Reality, Realtà mista, Realtà virtuale, VR, MR, Feedback, Hub di Feedback, bug
appliesto:
- Windows 10
ms.openlocfilehash: bc5983706d75d6c66bb8de375b38f2ebe0d3f0aba0d90be5ef1e39d5a6949743
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115187991"
---
# <a name="motion-controllers-in-windows-mixed-reality"></a>Controller del movimento in Windows Mixed Reality

I controller di movimento sono accessori hardware che consentono agli utenti di interagire in realtà mista. Un vantaggio dei controller di movimento rispetto ai movimenti è che i controller hanno una posizione precisa nello spazio, consentendo un'interazione granulare con gli oggetti digitali. Per Windows Mixed Reality visori immersivi, i controller di movimento sono il modo principale in cui gli utenti possono intervenire nel proprio mondo.

Windows Mixed Reality controller di movimento offrono un rilevamento preciso e reattivo del movimento nel campo di visualizzazione tramite i sensori vr immersivi. Non è necessario installare l'hardware sulle pareti nel proprio spazio. Questi controller di movimento offriranno la stessa facilità di configurazione e portabilità Windows Mixed Reality visori immersivi.

È anche possibile usare un controller Xbox, un mouse e una tastiera o spostarsi [usando solo la voce](using-speech-in-wmr.md).

## <a name="motion-controller-setup"></a>Configurazione del controller di movimento

La maggior parte dei visori è pre-associata direttamente al visore, ma alcuni visori iniziali richiedono l'associazione dei controller di movimento al PC con Bluetooth 4.0. Quando si connette il visore vr immersivo per la prima volta, si passa attraverso l'attivazione dei controller di movimento durante la configurazione. Tuttavia, se è necessario riass abbinarli in un secondo momento, ecco come:

1. Avviare **Portale realtà mista** con il visore connesso.  
2. Nell'angolo inferiore sinistro selezionare **... > Configura controller**.
3. Inserire due batterie AA in ogni controller e mettere il controller in modalità di associazione (vedere le istruzioni nella [sezione associazione dei controller di movimento](controllers-in-wmr.md#pair-motion-controllers)
4. Seguire le istruzioni fornite sullo schermo.

> [!NOTE]
> * Per i controller che si associano direttamente al PC, è necessario attivarli e quindi premere il pulsante di associazione all'interno del vano della batteria fino a quando le luci non iniziano a lampeggiare.
> * I controller di movimento supportano solo l'associazione a un PC alla volta. Se è necessario usarli con un visore diverso, è necessario eseguire il processo di associazione. Vedere [Configurare Windows Mixed Reality](set-up-windows-mixed-reality.md)

[Ottenere assistenza per la connessione](wmr-setup-faq.yml#my-motion-controllers-aren-t-working)

> [!IMPORTANT]
> **Hai un controller Xbox?**
> 
> Se si ha un controller Bluetooth Xbox, associarlo al PC per usarlo con il visore.
> 
> Se si dispone di un controller Xbox cablato, collegarlo al PC.
> 
> Alcuni giochi e app usano il controller Xbox in modo diverso da come viene usato nella realtà mista. Per usare il controller per un gioco o un'app, selezionare Usa come game pad **sulla** barra dell'app o pronunciare "Usa come game pad". Per tornare alla realtà mista, selezionare **Usa come game pad**, o pronunciare "Usa con sguardo fisso".  

## <a name="pair-motion-controllers"></a>Associare controller di movimento

Se si usa un visore che include un controller Bluetooth integrato, ad esempio Samsung Odyssey+ o HP Reverb, i controller dovrebbero essere già associati. È comunque possibile associare i controller usando l'app di installazione (dovrebbe essere già installato durante la configurazione del HMD). È anche possibile ottenerlo da Microsoft Store.

### <a name="pair-motion-controllers-to-hmd"></a>Associare controller di movimento a HMD

Accendere i controller premendo il pulsante Windows per 2 secondi fino a quando i LED non si accrendono.

Rimuovere il coperchio della batteria dai controller e trovare il piccolo pulsante di associazione sul bordo del controller. Tenere premuto questo pulsante per associare il PC.
    ![Associazione di controller di movimento](images/connect_controller.png)

Avviare **Portale realtà mista** con il visore connesso.  
Nell'angolo inferiore sinistro selezionare **... > Configura controller**.
Seguire le istruzioni sullo schermo.

### <a name="pair-motion-controllers-to-pc"></a>Associare i controller di movimento al PC

È possibile associare il controller a un PC aggiungendo un altro dispositivo Bluetooth.

Alimentare i controller e posizionarli in modalità di associazione, come descritto in precedenza.

* Passare a Impostazioni computer
* Dispositivo/ Aggiungi Bluetooth o altro dispositivo.

Al termine dell'associazione, i LED saranno solidi e luminosi.

### <a name="common-issues"></a>Problemi comuni

* Verificare di avere un solo Bluetooth radio attiva nel PC. Se sono presenti più radio Bluetooth, è necessario disabilitare le altre radio in Gestione dispositivi.
* Posizionare il Bluetooth dongle in una porta con una linea di vista chiara per i controller e non collegata ai dispositivi USB 3.0. USB 3.0 è noto per l'interferenza RF con Bluetooth (leggere questo [documento](https://www.intel.com/content/dam/www/public/us/en/documents/white-papers/usb3-frequency-interference-paper.pdf) da Intel per altri dettagli). Le porte USB 2.0 possono funzionare meglio per l'Bluetooth dongle.
* Assicurarsi che il Bluetooth dongle non sia collegato a una porta USB accanto al cavo USB del dispositivo HMD. È noto che il cavo visore causa interferenze con Bluetooth dongle. Collegare il dongle alla porta USB anteriore del PC per ottenere risultati ottimali.
* Per i notebook, assicurarsi che il Wi-Fi sia connesso a una banda a 5 GHz per un'esperienza ottimale. Selezionare l'icona della rete wireless in basso a destra e selezionare le proprietà per la rete in uso. I notebook progettati per condividere un'antenna a 2,4 GHz per Bluetooth e la connettività Wi-Fi rilevino la congestione dei dati a seguito di velocità di rete lente o prestazioni di monitoraggio del controller di movimento scarse.
* I controller di movimento riceveranno regolarmente nuovi aggiornamenti software da Microsoft. I controller mostreranno un modello alternato di luci lampeggianti quando ricevono questi nuovi aggiornamenti software. Si tratta di una situazione normale. Attendere il completamento dell'aggiornamento software prima di usare i controller. I controller vibrano e una luce costante sostituisce il modello flash alternato al termine.
* È possibile che venga detto di "Mettere il visore e usare la levetta per teletrasportare" prima che i controller completano il processo di aggiornamento. I controller non saranno visibili o utilizzabili fino al completamento dell'aggiornamento. La maggior parte degli aggiornamenti viene eseguita entro due minuti, ma gli aggiornamenti possono richiedere circa 10 minuti. Attendere il completamento dell'aggiornamento prima di procedere al passaggio successivo.

## <a name="using-controllers"></a>Uso dei controller

Ecco come spostarsi in realtà mista con controller di movimento, un gamepad Xbox o un mouse e una tastiera.

> [!TIP]
> Per passare dall'input alla realtà mista al desktop, **premere Windows logo + Y** sulla tastiera del PC.

![Mapping dei pulsanti del controller di movimento](images/get_to_know_controllers.png)

|  Per  |  Controller del movimento  | Game pad | Mouse e tastiera |
| --- | --- | --- | --- |
| Teletrasporto | Premere la levetta in avanti, quindi puntare il controller nel punto in cui si vuole andare. Rilasciare la levetta. | Premere la levetta sinistra in avanti, quindi cercare dove si vuole andare. Rilasciare la levetta. | Selezionare e tenere premuto il pulsante destro del mouse, quindi posizionare il puntatore del mouse nel punto desiderato. Rilasciare il pulsante. |
| Select | Puntare il controller, quindi premere il trigger o usare il touchpad. | Osservare la destinazione e quindi premere A. | Posizionare il puntatore del mouse e quindi fare clic con il pulsante sinistro del mouse. |
| Aprire il menu Start | Premere il **Windows** comando. | Premere il **pulsante Xbox.** | Premere il **Windows logo .** |
| Lasciare un'app immersiva | Premere il **Windows** comando. Selezionare quindi **Home di realtà mista** nel menu azioni rapide. | Premere il **pulsante Xbox.** Selezionare quindi **il pulsante Home della realtà mista** nel menu azioni rapide. | Premere il tasto **Windows logo. Selezionare quindi il **pulsante Home realtà mista** nel menu Azioni rapide visualizzato. |
| Ruota | Spostare la levetta a sinistra o a destra. | Spostare la levetta destra verso sinistra o verso destra. | Non disponibile. |
| Eseguire il backup | Spostare la levetta indietro. | Spostare la levetta sinistra all'indietro. | Non disponibile. |
| Camminata | Premere la levetta verso il basso e quindi premere nella direzione desiderata. | Premere il levetto sinistro verso il basso, quindi premere nella direzione desiderata. | Non disponibile. |
| Spostare una finestra dell'app | Posizionare il punto sulla barra dell'app. Premuta e tieni premuto il trigger per afferrare la finestra, quindi usa il controller per spostarlo in qualsiasi direzione. Rilasciare il trigger. | Sguardo fisso sulla barra dell'app, quindi tenere premuto A per afferrare la finestra. Usare la levetta sinistra per spostare la finestra da un lato all'altro o verso l'alto o verso il basso. Usare i trigger per avvicinarlo e allontanarlo. Rilasciare quindi A. | Posizionare il puntatore del mouse sulla barra dell'app. Fare clic con il pulsante sinistro del mouse e tenere premuto per afferrare la finestra, quindi usare il mouse per spostarlo da un lato all'altro o verso l'alto o verso il basso. Usare la rotellina di scorrimento per avvicinare o allontanare la finestra. Rilasciare il pulsante del mouse. |
| Spostare un oggetto 3D | Posizionare il punto sull'oggetto, quindi trascinare e tenere premuto il trigger per afferrarlo. Spostarlo in qualsiasi direzione con il controller, quindi rilasciare il trigger. | Fissa l'oggetto, quindi tieni premuto A per afferrarlo. Usare la levetta sinistra per spostare la finestra da un lato all'altro o verso l'alto o verso il basso. Usare i trigger per avvicinarlo e allontanarlo. Rilasciare quindi A. | Posizionare il puntatore del mouse sull'oggetto . Fare clic con il pulsante sinistro del mouse e tenere premuto per afferrarlo, quindi usare il mouse per spostarlo da un lato all'altro o verso l'alto o verso il basso.  Per spostarlo più vicino o lontano, usare la rotellina di scorrimento. Rilasciare il pulsante del mouse. |
| Ruotare o ridimensionare una finestra dell'app | Puntare un controller alla barra dell'app e l'altro controller in qualsiasi punto della finestra. Tenere premuti entrambi i trigger, quindi spostare i controller insieme o distanti per ridimensionarli.  Per ruotare, spostare un controller verso l'utente e l'altro lontano dall'utente. Rilasciare i trigger. | Selezionare **Regola sulla** barra dell'app. Osservare un angolo del frame di regolazione, quindi premere A per selezionarlo. Usare la levetta sinistra per ridimensionare la finestra.  | Selezionare **Regola sulla** barra dell'app. Selezionare e tenere premuto un angolo del frame di regolazione, quindi usare il mouse per ridimensionare la finestra. |
| Ruotare o ridimensionare un oggetto 3D | Puntare entrambi i controller all'oggetto . Tenere premuti entrambi i trigger, quindi spostare i controller insieme o distanti per ridimensionarli.  Per ruotare, spostare un controller verso l'utente e l'altro lontano dall'utente. | Selezionare **Regola** sulla barra dell'app e quindi spostare l'oggetto usando la levetta sinistra. | Selezionare **Regola** sulla barra dell'app, quindi selezionare e tenere premuto l'oggetto e usare il mouse per spostarlo. |
| Scorrere in una finestra dell'app | Premuta e tenere premuto il trigger, quindi spostare il controller verso l'alto o verso il basso.  | Usare il D-pad. | Usare la rotellina del mouse. |
| Fare zoom avanti o indietro nella finestra dell'app | Eseguire il pull di entrambi i trigger, quindi spostare i controller più vicini o più distanti. | Eseguire il pull del trigger destro per fare zoom avanti e del trigger sinistro per eseguire lo zoom indietro. | Usare la rotellina del mouse tenendo premuto CTRL sulla tastiera. |
| Aprire un menu | Premere il **pulsante Menu.** | Premere il **pulsante Menu.** | Fare clic su. |

## <a name="what-do-the-vibrations-and-lights-mean"></a>Cosa significano le vibrazioni e le luci

Il controller comunica all'utente cosa fa vibrando e lampeggiando le luci LED.

|  Quando il controller esegue questa operazione  |  Ciò significa che |
| --- | --- |
| I LED si attivano e il controller vibra una volta | **Attivazione** |  
| I LED si spegnino e il controller vibra due volte | **Spegnere** |
| LED lampeggiano ogni 3 secondi | **Sospeso** |
| I LED pulsa lentamente e il controller vibra una sola volta | **Immissione della modalità di associazione** |
| Il controller vibra una sola volta | **Connessione o disconnessione dal PC** |
| I LED sono accesi | **Controller monitorati dal visore VR** |
| I LED sono poco accesi | **Controller non monitorati dal visore VR** |
| Il controller vibra tre volte e quindi si spegne | **Livello critico della batteria** |
| Gli anelli interni e esterni dei LED lampeggiano in un modello alternato | **Aggiornamento** |

## <a name="updating-motion-controllers-firmware"></a>Aggiornamento del firmware dei controller del movimento

* Se un visore VR immersive è connesso al PC ed è disponibile un nuovo firmware del controller, il firmware verrà inserito automaticamente nei controller del movimento alla successiva azione.
* Gli aggiornamenti del firmware del controller vengono visualizzati con un modello di quadranti LED illuminanti in un movimento circolare e sono necessari 1-2 minuti. Gli aggiornamenti del firmware possono richiedere occasionalmente più tempo, fino a 10 minuti, il che può indicare problemi di Bluetooth o interferenze radio.
* In caso di interruzione dell'aggiornamento del firmware (spento il controller o esaurimento della batteria), verrà eseguito un nuovo tentativo all'accensione successiva.
* Al termine dell'aggiornamento del firmware, i controller verranno riavviati e riconnessi.
* Entrambi i controller devono essere connessi ora. Passare a Portale realtà mista per controllare lo stato dei controller.
* Verificare che i controller funzionino correttamente:
  * Avvia **Portale realtà mista** e immetti la home page di Realtà mista.
  * Spostare i controller e verificare il rilevamento, testare i pulsanti e verificare il funzionamento del teletrasporto. In caso contrario, vedere la sezione sulla risoluzione dei [problemi del controller del movimento](motion-controller-problems.md)

## <a name="faq"></a>Domande frequenti

### <a name="how-can-i-check-battery-level"></a>Come è possibile controllare il livello della batteria?

*A: Il livello della batteria si trova sul lato inverso del modello virtuale, non è presente alcun indicatore del livello della batteria fisica. Dopo l'accensione del controller, attendere alcuni secondi per far stabilizzare la lettura.*

### <a name="can-you-use-these-controllers-without-a-headset-just-for-the-joysticktriggeretc-input"></a>È possibile usare questi controller senza visore VR? Solo per l'input di joystick/trigger/etc?

*A: Not for Universal Windows Applications*

## <a name="filing-motion-controller-feedbackbugs"></a>Inviare commenti e suggerimenti/bug del controller di movimento

Inviare commenti e suggerimenti Hub di Feedback la categoria "Mixed Reality -> Input".

## <a name="see-also"></a>Vedi anche

- [Controller HP in Unity](/windows/mixed-reality/develop/unity/unity-reverb-g2-controllers)
- [Controller HP in Unreal](/windows/mixed-reality/develop/unreal/unreal-reverb-g2-controllers)
- [Contattare la community](https://answers.microsoft.com)
- [Per assistenza, contattare Microsoft](https://support.microsoft.com/contactus/)
- [Risoluzione dei problemi](troubleshooting-windows-mixed-reality.md)

Problemi con i controller di movimento? [Ottieni aiuto](motion-controller-problems.md)
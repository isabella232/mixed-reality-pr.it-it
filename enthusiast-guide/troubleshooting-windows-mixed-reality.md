---
title: Risoluzione dei problemi relativi a realtà mista di Windows
description: Risoluzione avanzata dei problemi di Windows Mixed Reality che va oltre la documentazione standard del supporto clienti.
ms.topic: article
keywords: Realtà mista di Windows, realtà mista, realtà virtuale, VR, MR, risoluzione dei problemi, errori, guida, supporto
ms.openlocfilehash: bf972c70f46ad9045005b953e28831df3ee9906e
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/03/2020
ms.locfileid: "91685709"
---
# <a name="troubleshooting-windows-mixed-reality-faqs"></a>Risoluzione dei problemi relativi alla realtà mista di Windows (domande frequenti)

## <a name="understanding-common-installation-error-messages"></a>Informazioni sui messaggi di errore di installazione comuni

### <a name="your-pc-cant-run-windows-mixed-reality"></a>"Il PC non può eseguire la realtà mista di Windows"

Il PC non soddisfa i [requisiti minimi](https://support.microsoft.com/en-us/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) necessari per eseguire la realtà mista di Windows. Il problema potrebbe essere dovuto al fatto che la configurazione hardware del computer non è compatibile con la realtà mista di Windows o perché è necessario eseguire l' [aggiornamento alla versione più recente di Windows](https://support.microsoft.com/en-us/help/12373/windows-update-faq). 

Si noti che la realtà mista di Windows richiede un driver di schede di grafica che supporta almeno WDDM 2,2, quindi assicurarsi di disporre dell'aggiornamento più recente del driver dal produttore. Se la configurazione della realtà mista di Windows indica che la scheda grafica non soddisfa i requisiti e si ritiene che sia presente, assicurarsi che l'auricolare sia collegato alla scheda corretta.

### <a name="youre-nearly-therethis-pc-doesnt-meet-the-minimum-requirements-needed-to-run-windows-mixed-reality"></a>"Ci siamo quasi lì: questo PC non soddisfa i requisiti minimi necessari per eseguire la realtà mista di Windows"

Il PC non soddisfa i [requisiti minimi](https://support.microsoft.com/en-us/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) necessari per ottenere la migliore esperienza nella realtà mista di Windows. Il PC potrebbe essere in grado di eseguire un auricolare immersivo, ma potrebbe non essere in grado di eseguire determinate applicazioni o potrebbe avere problemi con le prestazioni.

Si noti che la realtà mista di Windows richiede un driver di schede di grafica che supporta almeno WDDM 2,2, quindi assicurarsi di disporre dell'aggiornamento più recente del driver dal produttore. Se la configurazione della realtà mista di Windows indica che la scheda grafica non soddisfa i requisiti e si ritiene che sia presente, assicurarsi che l'auricolare sia collegato alla scheda corretta.

### <a name="before-we-can-set-up-windows-mixed-reality-your-administrator-will-need-to-enable-it-for-your-organization-learn-more"></a>"Prima di poter configurare la realtà mista di Windows, l'amministratore dovrà abilitarlo per l'organizzazione. Altre informazioni "

Probabilmente si è in una rete gestita dall'organizzazione e l'organizzazione usa Windows Server Update Services (WSUS) o altri criteri che potrebbero bloccare il download. Contattare il reparto IT dell'organizzazione o l'amministratore di sistema per [abilitare la realtà mista di Windows](https://docs.microsoft.com/windows/application-management/manage-windows-mixed-reality#enable).

### <a name="we-couldnt-download-the-mixed-reality-software-or-hang-tight-while-we-do-some-downloading"></a>"Non è stato possibile scaricare il software per realtà mista" o "blocco durante il download"

* A volte un aggiornamento in sospeso può bloccare il download del software per realtà mista. Passare a **impostazioni > aggiorna & sicurezza > Windows Update** e assicurarsi che Windows Update sia attivato. Scaricare e installare gli aggiornamenti in attesa di installazione. Se si verifica un errore con Windows Update durante il tentativo di eseguire questi passaggi, fare clic [qui](https://support.microsoft.com/en-us/help/10164/fix-windows-update-errors).
* Verificare che il PC sia connesso a Internet e che disponga di almeno 2 GB di spazio di archiviazione disponibile. Verificare lo stato della rete in: **impostazioni > rete & Internet > stato** . Se non si riesce a connettersi a Internet, fare clic [qui](https://support.microsoft.com/en-us/help/10741/windows-10-fix-network-connection-issues) per assistenza.  
* Riavviare il computer e riprovare. 

Se le soluzioni precedenti non funzionano, provare a:
* Se la connessione di rete Wi-Fi è impostata su a [consumo](https://support.microsoft.com/en-us/help/17452/windows-metered-internet-connections-faq), impostarla su non a consumo. Per disattivare una connessione a consumo, passare a: **impostazioni > rete & Internet > stato > modificare le proprietà di connessione > imposta come connessione a consumo** e selezionare "disattivato".  
* Se di recente è stato installato un aggiornamento, è possibile che si verifichino problemi. Non è consigliabile rimuovere gli aggiornamenti installati, in particolare gli aggiornamenti della sicurezza che mantengono il PC sicuro, ma a volte la rimozione dell'aggiornamento più recente può aiutare a determinare l'origine del problema. Per eseguire questa operazione: 
    * Passare a **impostazioni > aggiorna & sicurezza > Visualizza cronologia aggiornamenti installati > Disinstalla aggiornamenti**
    * Selezionare l'ultimo aggiornamento installato e "Disinstalla".
    * Quando viene richiesto di disinstallare l'aggiornamento? rispondere "Sì". Se si verifica un errore durante il tentativo di eseguire questi passaggi, fare clic [qui](https://support.microsoft.com/en-us/help/10164/fix-windows-update-errors). 
    * Riavviare il computer e riprovare. 
    * Se la realtà mista di Windows viene installata correttamente, reinstallare gli aggiornamenti più recenti in **impostazioni > Windows Update > verificare la disponibilità di aggiornamenti** e verificare se la realtà mista di Windows continua a funzionare. Se l'installazione non viene eseguita correttamente, reinstallare gli aggiornamenti più recenti e contattare il supporto tecnico di Windows. 

### <a name="something-went-wrong-and-we-couldnt-start-windows-mixed-reality"></a>"Si è verificato un errore e non è stato possibile avviare la realtà mista di Windows"
* Scollegare entrambi i cavi dell'auricolare dal PC.
* Riavvia il PC.
* Passare a **impostazioni > aggiorna & sicurezza > Windows Update** e assicurarsi che Windows Update sia attivato. Scaricare e installare tutti gli aggiornamenti in attesa.
* Riconnettere l'auricolare al PC, quindi riprovare a eseguire l'installazione.

Se i passaggi precedenti non funzionano, provare a disinstallare e reinstallare la realtà mista di Windows:
* Passare a **impostazioni > realtà mista > disinstallare** e selezionare "Disinstalla". 
* Riavvia il PC. 
* Per avviare nuovamente il processo di installazione, è sufficiente collegare la cuffia al PC.
    

## <a name="troubleshooting-setup-questions"></a>Risoluzione dei problemi relativi alle domande di installazione 

### <a name="my-xbox-controller-isnt-working-with-windows-mixed-reality"></a>Il controller Xbox non funziona con la realtà mista di Windows.

* Verificare che il controller sia acceso, completamente addebitato e connesso al PC.
* Sostituire le batterie del controller.
* Se si usa un controller Bluetooth, passare a **impostazioni > dispositivi > Bluetooth & altri dispositivi** nel PC e assicurarsi che sia associato (dovrebbe essere elencato nella pagina).

### <a name="i-cant-direct-input-controllers-gamepad-mousekeyboard-into-windows-mixed-reality"></a>Non è possibile indirizzare input (controller, gamepad, mouse/tastiera) in realtà mista di Windows.

Quando si usa l'auricolare, l'input dovrebbe passare automaticamente all'esperienza di realtà mista tramite il sensore di presenza dell'auricolare. Sul desktop verrà visualizzata una barra blu:

![Desktop di Windows con input indirizzato alla cuffia](images/1050px-windowsy.png)

Se l'input non viene attivato automaticamente, sarà necessario impostare manualmente l'input sull'auricolare. È possibile eseguire questa operazione digitando il **tasto Windows + Y** sulla tastiera (e lo stesso per impostare di nuovo l'input sul desktop).

### <a name="when-i-plug-in-my-headset-nothing-happens-the-mixed-reality-portal-doesnt-open"></a>Quando si collega l'auricolare, non viene eseguita alcuna operazione. Il portale per la realtà mista non si apre.
Il portale per la realtà mista, l'app che consente di configurare la realtà mista di Windows, è progettata per l'apertura automatica quando si collega un auricolare compatibile. Se non si apre, passare a Start e digitare "Mixed Reality Portal" nella casella di ricerca per aprire l'app da questa posizione. Se non si riesce a trovare il portale di realtà mista, questo potrebbe significare che è necessario eseguire [l'aggiornamento alla versione più recente di Windows](https://support.microsoft.com/en-us/help/12373/windows-update-faq).

### <a name="how-do-i-choose-between-seated-and-standing-and-all-experiences"></a>Ricerca per categorie scegliere tra "seduti e in piedi" e "tutte le esperienze"?

Se si sceglie "seduto e in piedi", durante l'installazione dell'auricolare o in un secondo momento, si userà l'auricolare senza un limite. È possibile rimanere in attesa o in primo luogo, ma in caso contrario sarà necessario rimanere in un'unica posizione, perché non ci saranno limiti per evitare ostacoli fisici. Alcune app possono essere progettate per funzionare con un limite, quindi è possibile che non sia possibile usarle o che non si abbia la stessa esperienza se vengono usate senza un limite. Vedere "Qual è il limite e perché è necessario crearne uno?" di seguito per altre informazioni.

Se si sceglie "tutte le esperienze", si configurerà un limite ed è possibile usare app ed esperienze che funzionano con un limite, oltre a quelli che non ne richiedono uno. 

### <a name="learn-mixed-reality-didnt-run-on-first-launch-and-i-went-right-into-the-windows-mixed-reality-home"></a>Imparare a usare la realtà mista non è stata eseguita al primo avvio e mi sono occupata della Home realtà mista di Windows.

È possibile eseguire di nuovo l'esperienza di apprendimento attenendosi alla [procedura di ripetizione dell'esecuzione](learn-mixed-reality.md#how-do-i-re-run-the-learning-experience). 


## <a name="boundary-setup-and-other-questions"></a>Impostazione del limite e altre domande

### <a name="whats-a-boundary-and-why-should-i-create-one"></a>Che cos'è un limite e perché è necessario crearne uno?

Un limite definisce l'area in cui è possibile spostarsi mentre si sta indossando la cuffia mista a realtà mista di Windows. Poiché non è possibile visualizzare l'area di lavoro mentre si usa l'auricolare, è importante creare un limite per evitare ostacoli. Il limite sembra essere un contorno bianco all'interno di realtà mista e viene visualizzato quando ci si avvicina. Quando viene visualizzato, rallentare i movimenti ed evitare di oltrepassare il limite o di estendere gli arti al di là.

L'area all'interno del limite deve essere libera di mobili, impianti di illuminazione a bassa pendenza, ventilatori a soffitto e così via. Informazioni [sull'integrità e sulla sicurezza in realtà mista di Windows](https://support.microsoft.com/en-us/help/4039969/windows-10-mixed-reality-immersive-headset-health-safety-comfort).

### <a name="how-do-i-create-a-boundary"></a>Ricerca per categorie creare un limite?

Quando si configura per la prima volta l'auricolare, l'app di installazione (portale per la realtà mista) illustra i passaggi necessari per creare un limite. Ma è possibile crearne uno in qualsiasi momento. Per eseguire questa operazione:
1. Selezionare **avvia > portale per la realtà mista** sul desktop. 
2. Aprire "menu".
3. Selezionare "Esegui installazione" per creare un nuovo limite.

Se un altro utente usa la cuffia, assicurarsi che sia in grado di comprendere il limite e come usarlo. Se si sposta l'auricolare in una nuova posizione, è necessario configurare un nuovo limite che funzioni per tale spazio.

### <a name="i-get-an-error-message-when-i-try-to-create-a-boundary"></a>Viene ricevuto un messaggio di errore quando si tenta di creare un limite.

* Non avvicinarsi troppo alla parete o ad altre ostruzioni durante la creazione di un limite.
* Assicurarsi di mantenere l'auricolare all'altezza della vita ed esaminare il computer mentre si tracciano i limiti.
* Verificare che il sensore non sia bloccato e che la luce sia sufficiente.
* Lo spazio che si sta tracciando deve essere maggiore di tre metri quadrati.
* Lo spazio non deve essere troppo grande o troppo complicato. Attenersi a una forma geometrica semplice senza numerose torsioni e giri.
* Non attraversare il proprio percorso mentre si esegue la traccia.
* Se ci si blocca in un angolo, ricominciare.

### <a name="during-start-up-of-mixed-reality-im-stuck-at-the-step-turn-your-head-side-to-side-and-then-at-the-floor"></a>Durante l'avvio della realtà mista, sono bloccato nel passaggio "capovolgere il lato destro e quindi al piano".

Questo passaggio consente all'auricolare di riconoscere lo spazio e di ripristinare i limiti e le pavimentazioni virtuali esistenti. Quando si usa l'auricolare, questo processo di analisi può richiedere fino a 10 secondi. Al termine dell'operazione, l'utente si troverà nella Home realtà mista o verrà richiesto di configurare di nuovo il limite.

Se il processo di analisi richiede più di 10 secondi, potrebbe essersi verificato un problema con il sensore di prossimità nell'auricolare:
1. Verificare che l'adesivo sia stato rimosso dal sensore di prossimità. Il sensore di prossimità si trova all'interno dell'auricolare approssimativamente dove si trova il centro della fronte.
2. Verificare che il sensore di prossimità accenda l'input dell'auricolare: con il dito, coprire e scoprire il sensore di prossimità alcune volte per verificare che l'input passi all'auricolare. Nella parte superiore del PC verrà visualizzato il banner **tasto Windows + Y** . È possibile passare manualmente l'input all'auricolare in qualsiasi momento digitando il **tasto Windows + Y** sulla tastiera.

### <a name="i-see-a-message-that-says-my-boundary-cant-be-found-what-should-i-do"></a>Viene visualizzato un messaggio che indica che il limite non è stato trovato. Cosa devo fare?

La realtà mista di Windows potrebbe avere problemi nell'identificare il limite esistente. È possibile creare un nuovo limite oppure è possibile usare il dispositivo in modalità "seduti e in piedi". 

### <a name="i-see-a-message-that-says-lost-tracking-or-we-dont-have-a-boundary-for-this-space"></a>Viene visualizzato un messaggio che indica "perdita del rilevamento" o "non è disponibile un limite per questo spazio".

È necessario creare un nuovo limite. Per eseguire questa operazione:
* Selezionare **avvia > portale per la realtà mista** .
* Selezionare "Esegui installazione".

### <a name="the-boundary-is-always-visible-how-can-i-make-it-go-away"></a>Il limite è sempre visibile. Come è possibile fare in modo che vada via?

Il limite viene visualizzato quando ci si avvicina. Se il limite include le sezioni con una forma stretta o irregolare, è possibile che ci si avvicini e che la causa appaia, più spesso di quanto si desideri. Per risolvere il problema, provare a creare di nuovo il limite usando una forma più grande e più regolare. Per eseguire questa operazione:
* Selezionare **avvia > portale per la realtà mista** .
* Selezionare "Esegui installazione".

### <a name="how-can-i-turn-off-the-boundary-temporarily"></a>Come è possibile disattivare temporaneamente il limite?

* Selezionare **avvia > portale per la realtà mista** .
* Aprire "menu". 
* Attivare "Boundary" su "off". Assicurarsi di rimanere in un'unica posizione mentre il limite è disattivato.


## <a name="problems-in-windows-mixed-reality-home"></a>Problemi nella Home realtà mista di Windows

### <a name="my-controllers-arent-showing-in-my-windows-mixed-reality-home"></a>I miei controller non vengono visualizzati nella mia Home realtà mista di Windows.

Assicurarsi che i controller dispongano di batterie complete e che siano abbinati correttamente usando Bluetooth. Provare a spegnere e accendere i controller usando il pulsante Windows. Se i controller non sono ancora visibili, provare a abbinare e riassociare ogni controller nel menu impostazioni in **dispositivi > Bluetooth** .

### <a name="the-floor-of-my-windows-mixed-reality-home-doesnt-appear-to-be-at-the-correct-height-or-it-is-slanted"></a>Il piano di casa della realtà mista di Windows non sembra essere all'altezza corretta o è inclinato.

Selezionare **inizia > regolazione della stanza** che viene avviata quando si inserisce l'app nel mondo, per apportare modifiche durante l'uso dell'auricolare. In questa app si verrà indirizzati all'uso del touch pad (Motion controller) o del riquadro direzione (gamepad) per regolare l'altezza del piano. Quando il piano è corretto, usare il pulsante Windows per tornare alla Home page.

### <a name="my-headset-has-stopped-tracking"></a>Il rilevamento dell'auricolare è stato interrotto.

Assicurarsi che le spie siano accese e che non sia presente alcun ostacolo alle fotocamere di rilevamento interne all'interno dell'auricolare. Se il rilevamento viene perso, la ripresa potrebbe richiedere alcuni secondi. Se il rilevamento non riprende, provare a riavviare il portale di realtà mista di Windows. Per ulteriori informazioni, vedere [rilevamento della risoluzione dei problemi](tracking.md) .

### <a name="i-cant-show-a-preview-of-what-im-seeing-in-my-headset-on-my-desktop-screen"></a>Non è possibile visualizzare un'anteprima di ciò che viene visualizzato nell'auricolare sullo schermo del desktop.

Il portale per la realtà mista include un pulsante **Riproduci** nella parte inferiore della schermata che consente di visualizzare un'anteprima di ciò che viene visualizzato nell'auricolare sullo schermo del desktop. Tuttavia, per motivi di prestazioni, questa funzionalità è disponibile solo nei PC che eseguono Windows Mixed Reality Ultra (90Hz).

## <a name="headset-connectivity-issues"></a>Problemi di connettività dell'auricolare

### <a name="my-computer-does-not-have-an-hdmi-port"></a>Il computer non dispone di una porta HDMI.
Se il computer non dispone di una porta HDMI ma ha una porta DisplayPort (DP), Mini DisplayPort (miniDP) o USB Type-C (USB-C) per l'output del video, potrebbe essere necessario utilizzare un [Adapter supportato](recommended-adapters-for-windows-mixed-reality-capable-pcs.md).

### <a name="can-i-use-usb-or-hdmi-extension-cables-with-windows-mixed-reality-headsets"></a>È possibile usare cavi di estensione USB o HDMI con auricolari per la realtà mista di Windows?
Gli auricolari per la realtà mista di Windows non supportano ufficialmente l'uso di cavi di estensione USB o HDMI. L'uso di questi cavi può influire in modo significativo sull'esperienza di realtà mista a causa delle variazioni nell'integrità del segnale risultante e dell'alimentazione del bus tra il controller USB del PC e l'auricolare della realtà mista. Se la visualizzazione dell'auricolare Mostra brevemente una schermata blu, quindi si riavviano o si riavviano i riavvii del portale di realtà misto o nero o se l'audio della cuffia viene ritagliato o si è verificato un problema oppure se l'auricolare si sposta tra il nero e la visualizzazione corretta, provare a usare l'auricolare senza cavi di estensione.

### <a name="i-am-getting-a-check-your-display-cable-error"></a>Viene visualizzato l'errore "controllare il cavo visualizzato".

* Se si usano schede per connettere l'auricolare al PC, assicurarsi che supportino la realtà mista di Windows. Provare anche a connettere l'adattatore al PC prima di connettere la HMD alla scheda.
* Se il PC dispone di grafica sia integrata che discreta, assicurarsi di usare la porta HDMI sulla scheda grafica attiva. In alcuni casi, questo potrebbe significare che è necessario connettere la visualizzazione del PC a una porta non HDMI.
* Se il PC dispone di grafica sia integrata che discreta e la grafica integrata è precedente e non supporta la realtà mista di Windows, provare a disabilitare la GPU integrata.
* Connettere un monitor PC alla porta HDMI del computer. Assicurarsi che i driver grafici siano aggiornati. Scaricare e installare le interfacce da AMD, NVIDIA o Intel direttamente, perché saranno probabilmente più recenti rispetto a quelle pubblicate per Windows Update.
* Assicurarsi di aver collegato il cavo HDMI dell'auricolare a una porta di **uscita HDMI** nel PC, non a una porta HDMI.
* Windows potrebbe non essere in grado di rilevare la connessione del cavo di visualizzazione. Aprire il Device Manager e verificare se la cuffia è elencata in "monitoraggi". In caso contrario, selezionare **azione > analizza modifiche hardware** . 

### <a name="i-see-a-message-that-says-put-on-your-headset-even-though-i-have-my-headset-on"></a>Viene visualizzato un messaggio che indica "put on the headset" anche se si dispone dell'auricolare.

Quando si usa l'auricolare, la realtà mista di Windows potrebbe richiedere alcuni secondi per ricaricare lo spazio. Se il messaggio non viene rimosso, assicurarsi che l'adesivo protettivo sia stato rimosso dal sensore di prossimità, che si trova all'interno dell'auricolare tra le lenti. Se il problema persiste, contattare il produttore dell'auricolare.

### <a name="a-message-says-connect-your-headset-even-though-ive-plugged-in-my-headset"></a>Un messaggio indica che "Connetti l'auricolare", anche se è stato collegato all'auricolare.

1. Assicurarsi che i cavi USB e HDMI dell'auricolare siano connessi alle porte corrette nel PC. Ecco come identificare le porte corrette:
    * Le porte USB 3,0 hanno un logo speciale con un contrassegno "SS" (che indica "SuperSpeed"). Il pezzo interno della porta è generalmente blu, mentre le porte USB 2,0 precedenti sono in genere nere o bianche all'interno.
    * Se il computer dispone di due porte HDMI, utilizzare quella che si connette alla scheda grafica, non la scheda madre del computer. Non è sempre ovvio, ma le porte discrete si trovano spesso in uno slot di espansione nel computer. Se si prova a usare una porta e non funziona, provare l'altra.
2. Scollegare i cavi USB e HDMI dall'auricolare per assicurarsi che siano connessi in modo sicuro. Quando si collega il cavo USB, provare a non sospendere l'inserimento del cavo USB.
3. Aprire Device Manager e verificare che la cuffia sia elencata in "dispositivi realtà misti". Fare doppio clic sulla cuffia in "Mixed Reality Devices" e verificare che lo stato del dispositivo indichi che il dispositivo funziona correttamente. Punti esclamativi gialli nei dispositivi elencati in Device Manager indicano gli errori segnalati dai dispositivi connessi al PC.
    * Se "Hololens sensors" è elencato con un punto esclamativo giallo in Device Manager, fare doppio clic sul dispositivo. Se viene visualizzato **il codice 10: i driver per il dispositivo non sono installati. Non sono disponibili driver compatibili per questo dispositivo** . seguire le [istruzioni](headset-connectivity.md#the-headset-driver-did-not-install-automatically-when-i-plugged-in-the-headset) per installare manualmente il driver Headset.
    * Se si usano più auricolari con realtà mista nel PC ed è stato installato manualmente il driver Headset per la realtà mista prima, in alcune circostanze l'aggiornamento manuale dei driver può essere applicato solo alla cuffia connessa al momento e non agli altri auricolari. In questo caso, verrà visualizzato **"codice 31: questo dispositivo non funziona correttamente perché Windows non è in grado di caricare i driver necessari per questo dispositivo. (Codice 31). Il messaggio ALPC richiesto non è più disponibile** in Device Manager. In Device Manager fare clic con il pulsante destro del mouse sulla cuffia in "Mixed Reality Devices" e selezionare "Disinstalla dispositivo". Selezionare "OK" per confermare e quindi scollegare e ricollegare l'auricolare.
4. Se viene visualizzato l'enumerazione parziale dell'auricolare (una serie di dispositivi USB viene enumerata, ma non è presente in "cuffie a realtà mista" in Device Manager), provare con un hub USB 3,0 alimentato esternamente.
5. Accedere al sito Web del produttore dell'auricolare e aggiornare i driver e il firmware per l'auricolare.
6. Connettere la cuffia a un altro PC e aprire Device Manager. Anche se il PC non è completamente compatibile con la realtà mista di Windows, è possibile verificare se l'auricolare viene enumerato. Se la cuffia non viene enumerata in più PC, potrebbe verificarsi un problema hardware.

**Nota per gli utenti della superficie:** Le versioni precedenti del software per l'aggiornamento del firmware dell'hub USB Surface Dock e Surface sono incompatibili con le cuffie a realtà mista. Se viene visualizzato il messaggio "Connetti la cuffia" in un PC Surface, verificare se i dispositivi segnalano un **errore "codice 10: Impossibile avviare il dispositivo"** in Device Manager. In tal caso, [rimuovere il driver in conflitto](https://support.microsoft.com/en-us/help/4032123/kinect-sensor-is-not-recognized-on-a-surface-book). Questa operazione deve essere eseguita solo una volta.

**Nota per gli utenti di Windows 10 N:** Se il PC esegue Windows 10 N, verrà visualizzato **l'errore "codice 28: la classe di installazione non è presente o non è valida"** in Device Manager dopo l'inserimento dell'auricolare in realtà mista. Le edizioni N di Windows 10 non sono supportate dalla realtà mista di Windows. Per ulteriori informazioni, seguire queste [istruzioni](troubleshooting-windows-mixed-reality.md#im-getting-a-the-install-class-is-not-present-or-is-invalid-error-in-device-manager) .

### <a name="a-message-says-check-your-usb-cable-or-insufficient-usb-speed"></a>Un messaggio indica che "controllare il cavo USB" o "velocità USB insufficiente".

* Assicurarsi di usare una porta USB 3,0 supportata nel PC:
    * Verificare che il cavo USB dell'auricolare sia collegato a tutti i modi.
    * Eseguire l'app [Windows Mixed Reality PC Check](https://aka.ms/pccheckapp) per verificare che il controller USB 3,0 del PC sia supportato.
    * Provare tutte le altre porte USB 3,0 nel PC. Alcuni PC hanno più di un controller USB 3,0.
    * Scollegare temporaneamente tutti i dispositivi USB collegati al PC e connettere solo l'auricolare.
    * Nei PC personalizzati, anche se una porta può essere contrassegnata come porta USB 3,0, potrebbe essere connessa a un controller USB 2,0. Con la cuffia connessa, aprire Device Manager, individuare e fare clic su uno dei dispositivi enumerati dall'auricolare, quindi passare a **visualizza > dispositivi per connessione** .
* Provare la cuffia in un altro computer. Se l'altro PC non è completamente compatibile con la realtà mista di Windows, archiviare Device Manager per verificare se viene visualizzato il messaggio "velocità USB insufficiente". Se la cuffia non viene enumerata correttamente su più PC, l'auricolare potrebbe essere difettoso.

### <a name="the-mixed-reality-portal-did-not-launch-automatically-after-i-plugged-in-my-headset"></a>Il portale per la realtà mista non viene avviato automaticamente dopo aver collegato l'auricolare.

È possibile che la cuffia non sia stata rilevata correttamente a causa di un problema sottostante. Provare ad avviare manualmente il portale di realtà mista e cercare eventuali messaggi di errore visualizzati. 

### <a name="my-headset-stopped-working-after-putting-my-pc-to-sleep-in-hibernation-mode-or-when-restarting-my-pc-with-my-headset-attached"></a>L'auricolare smette di funzionare dopo la sospensione del PC, in modalità di ibernazione o durante il riavvio del PC con la cuffia collegata.

1. Aprire Device Manager e verificare che la cuffia sia elencata in "dispositivi realtà misti".
2. Fare doppio clic sulla cuffia in "Mixed Reality Devices" e verificare che lo stato del dispositivo indichi che il dispositivo funziona correttamente.
3. Se viene visualizzato un errore "codice 43" che indica che il dispositivo ha smesso di funzionare o se l'auricolare non è elencato in "dispositivi con realtà mista", scollegare e ricollegare il cavo USB dell'auricolare. Microsoft sta esaminando un potenziale problema di interoperabilità di software/driver che può causare questo errore. Questo problema interessa un numero ridotto di PC e dovrebbe essere risolto in un aggiornamento futuro al driver della cuffia per la realtà mista.

### <a name="my-headset-causes-my-pc-to-generate-a-bug-check-blue-screen-when-i-put-my-pc-to-sleep-or-when-it-is-in-hibernation-mode"></a>Il mio auricolare causa la generazione di un controllo del bug (schermata blu) quando si posiziona il PC in modalità sospensione o in modalità di ibernazione.

Microsoft sta esaminando un potenziale problema di interoperabilità di software/driver che può comportare un numero ridotto di PC che potenzialmente generano un controllo bug "9F" (schermata blu) quando il PC viene messo in modalità di sospensione o di ibernazione con la cuffia collegata. Questo problema dovrebbe essere risolto in un aggiornamento futuro al driver della cuffia di realtà mista.

### <a name="the-headset-driver-did-not-install-automatically-when-i-plugged-in-the-headset"></a>Non è stato possibile installare automaticamente il driver headset quando è stato collegato l'auricolare.

Nei nuovi PC o nei PC con una copia di Windows 10 appena installata, il driver della cuffia potrebbe essere accodato dietro altri aggiornamenti di Windows e potrebbe non essere installato immediatamente. Se si dispone di una "N"-edizione di Windows, sarà necessario passare a un'edizione regolare di Windows 10 per utilizzare la realtà mista di Windows. Per installarlo manualmente:

1. Passare a **Start > Device Manager** e cercare "altri dispositivi" per un dispositivo "sensori HoloLens" con un punto esclamativo giallo: ![ visualizzazione dei sensori Device Manager HoloLens](images/hololenssensors.png)
2. Fare clic con il pulsante destro del mouse sul dispositivo e scegliere Proprietà. Se le proprietà del dispositivo leggono **i driver per questo dispositivo non sono installati (codice 28)** , chiudere la finestra e continuare. Se è presente un altro messaggio, seguire la procedura di risoluzione dei problemi nel resto della pagina.
![Codice 28 dei sensori HoloLens in Device Manager](images/code28.png)
3. Fare di nuovo clic con il pulsante destro del mouse sul dispositivo e scegliere "Aggiorna driver...". quindi, "Cerca automaticamente il software driver aggiornato" dopo l'aggiornamento del dispositivo, l'auricolare dovrebbe essere visualizzato in "dispositivi realtà mista" in Device Manager: il ![ dispositivo in realtà mista viene visualizzato in Device Manager](images/mixedrealitydevices.png)

Se l'installazione manuale non funziona o non si trova il driver in altri dispositivi, probabilmente è necessario disinstallare il driver esistente e reinstallarlo. A tale scopo, eseguire queste operazioni:
1. Passare a **Start > Device Manager** e cercare "Mixed Reality Devices" per la cuffia. Lo stato del dispositivo indicherà che il dispositivo funziona correttamente.
2. Fare clic con il pulsante destro del mouse sul dispositivo e scegliere "Disinstalla dispositivo".
3. Nella nuova finestra popup visualizzata selezionare la casella di controllo "Elimina il software driver per il dispositivo" e quindi selezionare "Disinstalla".
4. Al termine, scollegare l'auricolare dal PC e collegarlo di nuovo. Windows Update ora scaricherà e installerà un nuovo driver.

### <a name="troubleshooting-flowchart"></a>Diagramma di flusso per la risoluzione dei problemi

![Connetti la cuffia/controlla il cavo USB](images/hmd-connectivity2.jpg)


## <a name="mixed-reality-headset-display-problems"></a>Problemi di visualizzazione dell'auricolare di realtà mista ##

### <a name="my-headset-displays-are-black"></a>I display dell'auricolare sono neri.

* Verificare le prestazioni e la stabilità del PC:
    * Utilizzare Gestione attività per verificare se sono presenti processi che trafugata le unità CPU, GPU e/o disco del computer.
    * Esaminare le applicazioni e i registri eventi di sistema in Windows (usando Visualizzatore eventi) per verificare se si dispone di un'app che si sta bloccando frequentemente e generando report Segnalazione errori Windows (WER).
    * Controllare Windows Update per assicurarsi che la versione di Windows sia aggiornata. Potrebbe essere necessario selezionare più volte "Verifica disponibilità di aggiornamenti".
* Controllare la stabilità di app e giochi:
    * Verificare che il PC soddisfi i requisiti minimi di sistema per l'esecuzione di qualsiasi app o gioco che non venga eseguito correttamente.    
    * Verificare che la versione del driver GPU sia recente e verificare la presenza di nuovi problemi di prestazioni e compatibilità e regressioni sui nuovi driver.
    * Se si usano app e giochi SteamVR, verificare che SteamVR e la realtà mista di Windows per i componenti SteamVR siano aggiornati.
* Verifica compatibilità scheda HDMI:
    * Verificare che il cavo HDMI sia collegato in tutti i modi.
    * Se si usa una scheda HDMI (ad esempio, una mini-DisplayPort alla scheda HDMI), assicurarsi che sia compatibile con la realtà mista di Windows. L'adapter deve supportare HDMI 2,0 e sono disponibili molti schede meno recenti che supportano solo 1080p. Vedere [Adapter consigliati per la realtà mista di Windows](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs).
    * L'ordine del plug può essere importante. Connettere la scheda HDMI al PC prima di connettere l'auricolare alla scheda, soprattutto se si usa un adattatore da USB a HDMI. 
    * Se si usano, provare a rimuovere i cavi di estensione.
* Controllare la compatibilità della scheda grafica e del driver:
    * Provare la porta HDMI del PC con un monitor di PC. Alcuni PC possono avere più di una porta HDMI e non tutti possono essere attivi.
    * Se il PC dispone di un'unità di elaborazione grafica integrata (iGPU) e di un'unità di elaborazione grafica discreta (dGPU), assicurarsi di essere connessi alla porta HDMI di dGPU.<br> ![Porte HDMI](images/HP_HDMI_Ports_s.png)
    * Controllare la versione del driver della GPU. Assicurarsi che sia recente, ma anche prestare attenzione a eventuali nuovi problemi di prestazioni e compatibilità e regressioni per i nuovi driver.
    * Se si usa la realtà mista in un portatile ed è stato installato un driver grafico più recente dal sito Web del produttore della scheda grafica, provare a effettuare il downgrade al driver della scheda grafica più recente disponibile sul sito Web del produttore del computer o su Windows Update.
    * Se sono presenti più monitor PC connessi al PC, provare a disconnettere temporaneamente tutti i monitor tranne un PC.
    * Se è stata impostata una frequenza di aggiornamento personalizzata per il monitor del PC, provare a ripristinare temporaneamente una frequenza di aggiornamento standard, ad esempio 60Hz.
    * Se la scheda grafica è stata modificata di recente senza reinstallare Windows, verificare che nel monitor cuffia sia ancora installato il driver corretto. Con la cuffia collegata, verificare che "Mixed Reality headset" sia elencato nel nodo monitoraggi in Device Manager.
    * Se il PC ha una scheda grafica NVIDIA, verificare che il software per la visione 3D di NVIDIA sia disabilitato.
    * In alcune schede grafiche (soprattutto le schede grafiche precedenti), la porta HDMI potrebbe non supportare HDMI 2,0 o non essere completamente compatibile con la realtà mista di Windows. Provare la porta DisplayPort della scheda grafica usando un [adattatore displayport 1,2 per HDMI 2,0](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs)
    * I PC HP Omen con numero di prodotto HP 1RJ99EA # ABU hanno porte HDMI incompatibili con la realtà mista di Windows. Per eseguire questa operazione, aprire il "supporto tecnico HP" e il numero di prodotto verrà elencato nella parte inferiore dell'app.
    * Se il PC ha una scheda grafica della serie AMD R9 e si usa una cuffia a realtà mista Samsung, è necessario aggiornare il firmware dell'auricolare alla versione 1.0.8 o successiva per usare la porta HDMI della scheda grafica con l'auricolare.
    * Se si usa una superficie del libro 2, assicurarsi di usare la [superficie USB-C alla scheda HDMI](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs).
* Verificare la presenza di un problema hardware della cuffia reale mista:
    * Per confermare o escludere problemi hardware con l'auricolare della realtà mista, provare a connettere il dispositivo auricolare a realtà mista a un altro computer. 
    * Verificare prima di tutto la compatibilità dei PC e i problemi di installazione, in quanto i sintomi sono molto simili.
* Verificare che il cavo USB sia collegato a una porta USB 3,0 o superiore. Le porte USB 3,0 contengono SS (Super Speed) scritte accanto ad esse. Spesso (ma non sempre) blu colorato.        

Se utile, consultare il diagramma di flusso per la risoluzione dei problemi della cuffia nera.

![Schermata nera/non può visualizzare nulla](images/hmd-connectivity.jpg)

### <a name="my-headset-display-occasionally-turns-black-after-some-use"></a>Il display dell'auricolare viene talvolta trasformato in nero dopo un certo utilizzo.

* Provare a disabilitare le funzionalità di sospensione USB o di risparmio energia che il PC potrebbe avere. Ad esempio, la [sospensione selettiva USB](https://docs.microsoft.com/windows-hardware/drivers/usbcon/usb-selective-suspend) nelle opzioni di risparmio energia di Windows, l'impostazione "Consenti al computer di disattivare questo dispositivo per risparmiare energia" in Device Manager e tutte le impostazioni di risparmio energia USB nel firmware del PC.
* Disconnettere temporaneamente eventuali altri dispositivi USB e periferiche connesse al PC.
* Controllare la versione del driver della GPU. Assicurarsi che sia recente, ma anche prestare attenzione a eventuali nuovi problemi di prestazioni e compatibilità e regressioni per i nuovi driver.

### <a name="one-of-the-displays-on-my-headset-is-black"></a>Uno degli schermi dell'auricolare è nero.

* Se si usa una scheda HDMI, assicurarsi che supporti HDMI 2,0.
* Rimuovere tutti i cavi di estensione USB e HDMI che potrebbero essere in uso.
* Verificare che il driver grafico sia aggiornato.
* Provare l'auricolare della realtà mista in un altro computer.

### <a name="my-headset-displays-turn-blue-for-a-moment-and-then-mixed-reality-portal-reinitializes"></a>L'auricolare diventa blu per un istante, quindi il portale di realtà mista reinizializza.

Questo indica in genere un problema di affidabilità del controller USB occasionale nel PC:
* Provare con un'altra porta USB. Il PC potrebbe avere più controller USB 3,0.
* Rimuovere eventuali cavi di estensione (se applicabile).
* Provare a scollegare tutti gli altri dispositivi USB dal PC.
* Provare a connettere un hub USB 3,0 alimentato esternamente al PC e a connettere l'auricolare all'hub.
* Se si usa un PC desktop, prendere in considerazione l'acquisto di una scheda PCI USB 3,0 per aggiungere un altro controller USB al PC.

### <a name="my-headset-causes-my-pc-to-hang-or-show-a-black-screen-while-starting-up"></a>L'auricolare causa il blocco del PC o la visualizzazione di una schermata nera durante l'avvio.

In alcuni PC, l'auricolare collegato prima di accendere o durante il riavvio del PC potrebbe interferire con il processo di avvio. Il PC potrebbe selezionare la cuffia da visualizzare come "monitoraggio principale" per mostrare lo stato di avanzamento dell'avvio del PC oppure potrebbe essere impedito di avviarsi correttamente e potrebbe "bloccarsi" e/o produrre un codice di errore acustico. Il comportamento dipende in gran parte dal fatto che la marca e il modello del computer e/o la marca e il modello della scheda grafica. Per risolvere il problema:
* Connettere la cuffia a una porta diversa nella scheda grafica. potrebbe essere necessario usare un adapter per usare le altre porte.
* Verificare che il firmware BIOS/UEFI del PC sia aggiornato (ma è sufficiente aggiornare il firmware BIOS/UEFI del PC solo se si è a proprio agio).

### <a name="my-pc-or-headset-displays-flicker-flash-or-remain-black-when-using-a-surface-pc"></a>Il PC o l'auricolare Visualizza sfarfallio, Flash o rimane nero quando si utilizza un PC Surface.

* Assicurarsi di usare una scheda HDMI che supporti HDMI 2,0. Molti adapter HDMI precedenti supportano solo la risoluzione 1080p, che non è sufficiente per le cuffie con realtà mista.
* Verificare che il driver grafico sia aggiornato. Oltre a controllare Windows Update, è possibile controllare il sito Web del produttore del PC per un driver di grafica aggiornato.
* Alcuni dispositivi della superficie non sono compatibili con la realtà mista di Windows. Altre informazioni su [compatibilità e requisiti di Surface](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#windows-mixed-reality-and-surface).

### <a name="my-headset-display-doesnt-work-after-i-shut-down-and-do-a-fast-startup"></a>La visualizzazione dell'auricolare non funziona dopo l'arresto e l'avvio rapido.

Scollegare il cavo HDMI e il cavo USB dall'auricolare, quindi ricollegarlo.

### <a name="my-headset-displays-are-very-choppy-but-mixed-reality-portals-preview-window-appears-fine"></a>I display dell'auricolare sono molto frammentati, ma la finestra di anteprima del portale di realtà mista risulta corretta.

* Assicurarsi che le risorse di sistema del PC (CPU, memoria e disco rigido) siano disponibili e non siano ancorate o riuscite da un'altra app o da un altro processo.
* Aggiornare il driver della grafica.

### <a name="im-getting-a-the-install-class-is-not-present-or-is-invalid-error-in-device-manager"></a>Viene visualizzato l'errore "la classe di installazione non è presente o non è valida" in Device Manager.

Se si visualizzano "sensori HoloLens" con un punto esclamativo giallo in Device Manager, fare doppio clic sul dispositivo per altri dettagli. Se viene visualizzato un messaggio che informa che i driver per il dispositivo non sono installati. (Codice 28): la classe install non è presente o non è valida ", questo è in genere dovuto al fatto che il PC esegue [Windows 10 N](https://support.microsoft.com/en-us/help/4039813/media-feature-pack-for-windows-10-n-october-2017). Si noti che le edizioni N di Windows 10 non supportano la realtà mista di Windows ed è necessario installare una versione non N di Windows 10.

### <a name="my-wmr-environment-is-jittery-or-stutters-when-i-move-my-head-and-displays-double-vision"></a>L'ambiente WMR è nervoso o balbetta quando sposto la mia testa e visualizza una doppia visione.

In un computer portatile con una grafica integrata e una GPU NVIDIA, si verifica un errore dopo un periodo di tempo che sembra causare la visualizzazione di un frame precedente dopo il frame successivo, con una doppia visione più veloce, in modo da spostare la testa in un movimento di imbardata, pitch o Roll. Il problema sembra essere sui driver dopo il driver di grafica NVIDIA 436,48.  L'installazione di questo driver risolverà il problema fino a quando NVIDIA non risolve il problema nei driver aggiornati. Per un'installazione diretta di NVIDIA graphics driver 436,48, visitare [NVIDIA](https://www.nvidia.com/Download/driverResults.aspx/152007/en-us).

### <a name="im-experiencing-discomfort-when-i-use-my-headset"></a>Si è verificato un fastidio quando si usa l'auricolare.
Per informazioni generali sulla comodità nella realtà mista di Windows, vedere la pagina relativa all' [integrità, alla sicurezza e alla comodità dell'auricolare misto](https://support.microsoft.com/en-us/help/4039969/windows-10-mixed-reality-immersive-headset-health-safety-comfort)di Windows. Per informazioni dettagliate sull'auricolare specifico, rivolgersi al produttore dell'auricolare.

### <a name="how-can-i-get-a-clearer-view-in-my-headset"></a>Come è possibile ottenere una visualizzazione più chiara nell'auricolare?
Provare a modificare l'adattamento dell'auricolare. Regolarne la posizione sulla faccia spostando l'icona verso l'alto e verso il basso o verso sinistra e destra, quindi modificare le cinghie in modo che risultino accoglienti.

Se l'auricolare lo supporta, è anche possibile modificare le impostazioni di calibrazione. Se la cuffia ha una manopola per regolare la calibrazione, usare questa. In caso contrario, passare a **impostazioni > realtà mista > qualità visiva** e regolare la calibrazione in tale posizione. Per ulteriori informazioni sulla calibrazione per un dispositivo specifico, rivolgersi al produttore dell'auricolare.

## <a name="mixed-reality-portal-error-messages-and-problems"></a>Messaggi di errore e problemi del portale per realtà mista

### <a name="i-got-a-something-went-wrong-error-message-or-im-having-problems-in-the-mixed-reality-portal"></a>Si è verificato un messaggio di errore "si è verificato un problema" oppure si sono verificati problemi nel portale di realtà mista.

Riavviare la realtà mista di Windows:
1. Scollegare entrambi i cavi auricolare dal PC.
2. Riavvia il PC.
3. Riconnettere l'auricolare.

Se questa operazione non funziona, assicurarsi che il PC riconosca la cuffia:
1. Selezionare Avvia.
2. Digitare "gestione dispositivi" nella casella di ricerca e selezionarlo nell'elenco. 
3. Espandere "dispositivi in realtà mista" e verificare se l'auricolare è elencato. 

Se non è elencato, provare a eseguire le operazioni seguenti:
1. Collegare la cuffia a porte diverse sul PC, se disponibile.
2. Verificare la disponibilità degli aggiornamenti software più recenti da Windows Update.
3. Disinstallare e reinstallare la realtà mista di Windows:
    1. Scollegare entrambi i cavi auricolare dal PC.
    2. Selezionare **impostazioni > realtà mista > disinstallare** .
    3. Selezionare **impostazioni > dispositivi > Bluetooth & altri dispositivi** per disaccoppiare i controller di movimento. Selezionare ogni controller, quindi selezionare "Rimuovi dispositivo".
    4. Collegare la cuffia al PC per reinstallare la realtà mista di Windows.
    
### <a name="im-getting-a-check-your-usb-cable-error-message"></a>Viene ricevuto un messaggio di errore "controllare il cavo USB".

Connettere la cuffia a una porta USB diversa (e assicurarsi che si tratta di una supervelocità USB 3,0). Provare anche a rimuovere le estensioni o gli hub tra la cuffia e il computer.

### <a name="im-getting-a-check-your-display-cable-error-message"></a>Viene visualizzato il messaggio di errore "check your display Cable".

Attenersi alla procedura seguente:
* Connettere la cuffia a DisplayPort 1,2 o versione successiva o HDMI 1,4 o versione successiva. Assicurarsi che la porta corrisponda alla scheda grafica più avanzata nel PC.
* Se si sta usando un adapter, assicurarsi che sia in grado di supportare 4K.
* Provare a usare una porta HDMI diversa.
* Se un monitor esterno è collegato a una porta HDMI, provare a connetterlo a una DisplayPort e usare la porta HDMI per l'auricolare.


## <a name="something-went-wrong-error-codes-and-how-to-resolve-them"></a>Codici di errore "si è verificato un problema" e come risolverli

| **Codici di errore di Windows 10** (versione 1809/versioni 1709, 1803) | **Messaggio di errore e suggerimenti per la risoluzione dei problemi**                    |
|-------------------------------------------------------------|--------------------------------------------------------------------|
|   1-4 / 2197815297-4  | **Controllare il cavo di visualizzazione: assicurarsi che il cavo di visualizzazione dell'auricolare sia collegato correttamente.** <br/><br/><ol start="1"><li>Scollegare i cavi USB e HDMI dell'auricolare, quindi collegarli nuovamente.</li><li>Controllare Device Manager e verificare che in "monitoraggi" sia presente il monitoraggio "auricolare realtà mista".</li><li>Assicurarsi che i driver grafici siano aggiornati (dal sito Web del produttore della scheda grafica).</li><li>Se si usa un adapter per connettere l'auricolare, assicurarsi che supporti la [realtà mista di Windows](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs).</li><li>Se la scheda grafica dispone di porte DisplayPort e HDMI, provare a usare la porta DisplayPort sulla scheda grafica e usare un adattatore da DisplayPort a HDMI della realtà mista supportato.</li><li>Provare una porta USB 3,0 diversa nel PC</li></ol> |
|   1-5 / 2197815297-5  | **Controllare il cavo di visualizzazione: non è stato possibile inizializzare correttamente le cuffie visualizzate. Provare a riavviare il PC e a riconnettere l'auricolare.**<br/><br/>Windows Visualizza il monitor della cuffia, ma la realtà mista di Windows presenta problemi di comunicazione con le visualizzazioni sull'auricolare della realtà mista. Per risolvere il problema:<br/><ol start="1"><li>Assicurarsi che i driver grafici siano aggiornati (dal sito Web del produttore della scheda grafica).</li><li>Se si usa un adapter per connettere l'auricolare, assicurarsi che supporti la [realtà mista di Windows](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs).</li><li>Se la scheda grafica dispone di porte DisplayPort e HDMI, provare a usare la porta DisplayPort sulla scheda grafica e usare un adattatore da DisplayPort a HDMI della realtà mista supportato.</li><li>Provare a riavviare il PC.</li></ol> |
|   7-1, 7-2, 7-3/2181038087-1, 2181038087-2, 2181038087-3  | **La realtà mista di Windows presenta problemi di connessione all'auricolare. Provare a scollegare l'auricolare e a collegarlo di nuovo.**<br/><br/>Non è stato possibile inizializzare completamente l'auricolare della realtà mista. Probabilmente si tratta di un errore temporaneo. Scollegare la cuffia e collegarla di nuovo per risolvere il problema.
|   7-4 / 2181038087-4  | **La realtà mista di Windows presenta problemi di connessione all'auricolare. Provare a scollegare l'auricolare e a collegarlo di nuovo.**<br/><br/>Il driver dell'auricolare in realtà mista non è riuscito a inizializzare le telecamere di rilevamento nell'auricolare. Probabilmente si tratta di un errore temporaneo. Scollegare l'auricolare e ricollegarlo per risolvere il problema.
|   7-5 / 2181038087-5  | **La realtà mista di Windows presenta problemi di connessione all'auricolare. Provare a collegare la cuffia a una porta USB diversa e a scollegare temporaneamente qualsiasi altro dispositivo USB connesso al PC.**<br/><br/>La realtà mista di Windows ha perso la sincronizzazione tra i timestamp dei frame della macchina reale mista e i timestamp del PC. Potrebbe trattarsi di un errore temporaneo o di un'indicazione di problemi di integrità dei segnali USB. Per risolvere il problema:</li><li>Scollegare temporaneamente tutti i dispositivi e le periferiche USB, rimuovere tutti i cavi di estensione e collegare solo l'auricolare.</li><li>Disabilitare le funzionalità di sospensione/risparmio energia USB nel PC, ad esempio la sospensione selettiva nelle opzioni di risparmio energia di Windows, l'impostazione "Consenti al computer di disattivare questo dispositivo per risparmiare energia" in Device Manager e tutte le impostazioni di risparmio energia USB nel firmware del PC.</li></ul>
|   7-6 / 2181038087-6  | **Si è verificato un problema con il firmware dell'auricolare. Provare a scollegare l'auricolare e a collegarlo di nuovo.** <br/><br/>Può trattarsi di un errore temporaneo. Provare a scollegare e a ricollegare l'auricolare. Se il funzionamento non funziona:</li><li>Controllare gli aggiornamenti di Windows per verificare che sia in esecuzione il driver Headset più recente disponibile.</li><li>Provare la cuffia in un altro computer. Se viene visualizzato lo stesso messaggio di errore, sarà necessario servire l'auricolare.</li></ul>
|   7-7 / 2181038087-7  | **La realtà mista di Windows presenta problemi di connessione all'auricolare. Provare a collegare la cuffia a una porta USB diversa e a scollegare temporaneamente qualsiasi altro dispositivo USB connesso al PC.**<br/><br/>Il driver dell'auricolare in realtà mista non è riuscito a inizializzare il firmware nell'auricolare. Può trattarsi di un errore temporaneo. Provare a scollegare e a ricollegare l'auricolare. Se il funzionamento non funziona:<li>Scollegare temporaneamente i dispositivi USB e le periferiche non necessarie per eseguire la realtà mista di Windows.</li><li>Controllare gli aggiornamenti di Windows per verificare che sia in esecuzione l'ultimo driver della cuffia disponibile.</li></ul>
|   7-11 / 2181038087-11 | **La CPU è troppo vecchia per essere compatibile con la realtà mista di Windows.**<br/><br/>Il PC non riesce a verificare la compatibilità perché nella CPU manca il set di istruzioni AVX richiesto dai controller di movimento della realtà mista. È necessario un [PC compatibile con la realtà mista di Windows](https://www.microsoft.com/en-us/windows/view-all-devices?col=wmr-pcs#icons).
|   7-12 / 2181038087-12 | **La cuffia è connessa a un controller USB incompatibile. Provare a collegare la cuffia a una porta USB diversa, se disponibile. In alternativa, provare a installare un driver USB Microsoft al posto di eventuali driver non compatibili.**<br/><br/>La cuffia potrebbe essere collegata a una porta USB connessa a un driver del controller USB non Microsoft compatibile. Questi driver del controller USB 3,0 spesso non sono in grado di leggere e gestire il [descrittore ContainerId](https://docs.microsoft.com/windows-hardware/drivers/usbcon/usb-containerids-in-windows), che aggrega le parti diverse del headset della realtà mista in un'unità coesiva (per riprodurre l'audio dalle cuffie corrette, visualizzare il video e estrarre i dati di rilevamento dai sensori corretti). Per modificare il driver del controller USB: <ol start="1"><li>Avviare Device Manager.</li><li>Espandere la categoria per i controller del bus seriale universale e fare clic con il pulsante destro del mouse per disinstallare il driver per ogni elemento che include il testo "eXtensible Host Controller" **e** non ha "Microsoft" nel nome.</li><li>Selezionare "Elimina il software driver per questo dispositivo" per assicurarsi che i driver precedenti vengano rimossi.</li><li>Verificare che ogni elemento che include il testo "eXtensible Host Controller" disponga di "Microsoft" alla fine.</li><li>Inserire il HMD.</li></ol>In alternativa, se il problema è intermittente, è possibile che HMD non risponda correttamente ai comandi dal driver HMD. Per risolvere il problema, scollegare il HMD per 30 o più secondi, quindi ricollegarlo. | 
|   7-13 / 2181038087-13 | **La cuffia è connessa a un controller USB incompatibile. Provare a collegare la cuffia a una porta USB diversa, se disponibile. In caso contrario, è necessario installare un nuovo controller USB 3,0.**<br/><br/>La realtà mista di Windows non è in grado di sincronizzare i timestamp dei frame della fotocamera per realtà mista ai timestamp del PC. Questa situazione è probabilmente causata da un controller host USB 3,0 non compatibile che non supporta ITP (pacchetti timestamp isocroni). Contattare il produttore del PC per verificare se è possibile abilitare la funzionalità ITP oppure passare a un altro controller host USB con supporto ITP. |
|   7-14 / 2181038087-14 | **La realtà mista di Windows presenta problemi di connessione all'auricolare. Provare a scollegare l'auricolare e a collegarlo di nuovo.**<br/><br/>La realtà mista di Windows non ha problemi nell'inizializzazione del sensore di presenza sull'auricolare in realtà mista. In Device Manager, l'auricolare visualizzerà il messaggio di errore "PoseThread non è riuscito a inizializzare il sensore di presenza". Per risolvere il problema:<br/><ol start="1"><li>Scollegare l'auricolare, quindi ricollegarlo. Verificare che il cavo USB sia collegato in tutti i modi.</li><li>Provare con un'altra porta USB nel PC.</li><li>Provare la cuffia in un altro PC per verificare se la cuffia è completamente enumerata in Device Manager su tale computer.</li><li>Verificare che nel PC siano installati altri driver HID in conflitto, ad esempio dalla tastiera o dal mouse. (Cercare tutti i dispositivi HID in Device Manager con il logo di un punto interrogativo).</li><li>Se si usa una cuffia a realtà mista Samsung che esegue Windows 10 versione 1709 o versione 1803, seguire le istruzioni per il codice di errore 2181038087-12 per verificare se il controller USB 3,0 esegue un driver del controller USB non Microsoft.</li></ol> |
|   7-15 / 2181038087-15 | **La realtà mista di Windows ha rilevato un driver WinUSB incompatibile installato.**<br/><br/><ol start="1"><li>Verificare che il driver WinUSB nel PC sia quello incluso in Windows e che qualsiasi driver USB di terze parti non abbia sovrascritto la copia di WinUSB nel PC.</li><li>Se il problema persiste, potrebbe essere necessario ripristinare o reinstallare l'installazione di Windows.</li></ol> |
|   13-11/-            | Il portale per la realtà mista ha rilevato un problema di registrazione delle app con Windows. Controllare il registro eventi dell'applicazione (utilizzando Visualizzatore eventi) per verificare se sono disponibili ulteriori dettagli. |
|   14-1/-            | Il portale per la realtà mista sta riscontrando problemi nell'inizializzazione dello stack di composizione e grafica. Per risolvere il problema:<ul><li>Gestione finestre desktop (DWM, un componente chiave dello stack di grafica Windows) potrebbe verificarsi un arresto anomalo. Controllare il registro eventi dell'applicazione (utilizzando Visualizzatore eventi) per verificare se è in corso.</li><li>Provare una disinstallazione pulita del driver grafico, quindi installare il driver di grafica più recente dal sito Web del produttore della scheda grafica.</li></ul> |
|   14-2/C0001160-101  | **Si è riscontrato un problema di connessione all'auricolare. Provare a rimuovere tutti i cavi di estensione che potrebbero essere in uso e assicurarsi di aver connesso la cuffia alla porta corretta per la scheda grafica. Se si usano schede, assicurarsi che siano compatibili con la realtà mista. Se si verificano ancora problemi, provare ad aggiornare il driver della grafica.**<br/><br/>Impossibile inizializzare lo stack di composizione e visualizzazione della realtà mista. La scheda grafica o il driver della scheda grafica del PC potrebbe non essere compatibile con la realtà mista di Windows. Per verificare quanto segue: <ul><li>Verificare che il PC soddisfi i requisiti minimi di sistema per la realtà mista di Windows.</li><li>Se si usano i PC Dell Inspiron 5577 in Windows 10, versione 1809 o successive, è possibile che questo errore venga visualizzato a causa di un conflitto con la funzionalità di post-elaborazione grafica di Dell TrueColor. Per risolvere questo problema, usare l'app TrueColor di Dell per disattivare la funzionalità TrueColor, quindi provare a eseguire di nuovo il portale di realtà mista.</li><li>In un PC desktop installare il driver di grafica più recente dal sito Web del produttore della scheda grafica. In un portatile installare il driver grafico più recente per la marca e il modello dal sito Web del produttore del portatile.</li><li>Se si dispone di grafica di terze parti o si visualizzano software/accessori, disinstallare temporaneamente le app e i driver.</li><li>Selezionare "Riprova" per verificare se si tratta di un problema temporaneo.</li></ul> |
|   14-3/-             | **Si è riscontrato un problema di connessione all'auricolare. Provare a rimuovere tutti i cavi di estensione che potrebbero essere in uso e assicurarsi di aver connesso la cuffia alla porta corretta per la scheda grafica. Se si usano schede, assicurarsi che siano compatibili con la realtà mista. Se si verificano ancora problemi, provare ad aggiornare il driver della grafica.** <br/><br/><ul><li>Se si usano modalità personalizzate o frequenze di aggiornamento nel monitor del PC, provare a impostare la frequenza di aggiornamento su 60Hz.</li><li>Verificare che tutte le schede utilizzate supportino la realtà mista di Windows.</li><li>Provare a installare il driver di grafica più recente dal sito Web del produttore della scheda grafica.</li><li>Fare clic su "Riprova" per verificare se si tratta di un problema temporaneo.</li></ul> |
| 14-4/-             | **Si è riscontrato un problema di connessione all'auricolare. Provare a rimuovere tutti i cavi di estensione che potrebbero essere in uso e assicurarsi di aver connesso la cuffia alla porta corretta per la scheda grafica. Se si usano schede, assicurarsi che siano compatibili con la realtà mista. Se si verificano ancora problemi, provare ad aggiornare il driver della grafica.** <br/><br/><ul><li>Il PC potrebbe avere più monitor di PC connessi rispetto a quelli che possono essere supportati dalla scheda grafica. Disconnettere tutto tranne il monitor del PC primario.</li><li>Verificare che tutte le schede utilizzate supportino la realtà mista di Windows.</li><li>Installare il driver di grafica più recente dal sito Web del produttore della scheda grafica.</li><li>Fare clic su "Riprova" per verificare se si tratta di un problema temporaneo.</li></ul> |
|   15-5/-             | **Il portale per la realtà mista ha perso la sincronizzazione con la realtà mista di base e i componenti di Windows da cui dipende.**<br/><br/><ul><li>Il problema potrebbe essere causato da un problema di prestazioni del computer. Verificare che CPU, GPU e HDD non siano ancorati in Gestione attività.</li><li>Scollegare temporaneamente tutti gli altri dispositivi USB dal PC.</li><li>Riavvia il PC.</li></ul> |
|   -/H0002000-0    | **Il sistema operativo del PC si trova in uno stato non corrispondente per la realtà mista di Windows**<br/><br/>Controllare gli aggiornamenti di Windows per gli aggiornamenti. |
|   -/S0002261-101, S0002361-101 | **Un problema con un componente della shell della realtà mista impedisce l'avvio corretto del portale per la realtà mista**<br/><br/><ul><li>Aprire il registro applicazioni usando Visualizzatore eventi sul PC per verificare la presenza di arresti anomali dell'applicazione in un momento in cui si è tentato di avviare la realtà mista di Windows.</li><li>Verificare che il driver grafico sia aggiornato.</li><li>La scheda HDMI utilizzata non è compatibile con la realtà mista di Windows. Vedere il dongle supportato e consigliato da HDMI a mini Display Port (DP) [.](recommended-adapters-for-windows-mixed-reality-capable-pcs.md)</li></ul> |


## <a name="motion-controller-problems"></a>Problemi del controller di movimento

### <a name="my-motion-controllers-arent-working-properly"></a>I controller di movimento non funzionano correttamente.

Se i [controller di movimento](https://support.microsoft.com/en-us/help/4040517/windows-10-controllers-windows-mixed-reality) non funzionano, non si connettono o se non viene visualizzata un'immagine dei controller quando si indossa la cuffia, provare a eseguire le operazioni seguenti:
1. Verificare che i controller siano accesi. Per attivarli, tenere premuto il pulsante Windows per due secondi.
2. Verificare che i controller siano completamente addebitati e sostituire le batterie in caso contrario.
3. Spegnere e riaccendere i controller tenendoli davanti all'utente. Premere e tenere premuto il pulsante Windows per quattro secondi per spegnere un controller, quindi premerlo e tenerlo premuto per due secondi per attivarlo. 
4. Selezionare **impostazioni > dispositivi > Bluetooth & altri dispositivi** nel PC e assicurarsi che i controller siano elencati come abbinati. In caso contrario, è necessario [associarli](https://support.microsoft.com/en-us/help/4040517/windows-10-controllers-windows-mixed-reality). 
5. Verificare che i controller di movimento siano visualizzati come "connessi". "Abbinato" non significa necessariamente che i controller siano connessi al PC. I controller devono essere visualizzati sotto la categoria "mouse, tastiera & penna". I controller di movimento in "altri dispositivi" non hanno superato il processo di associazione e non funzionano. Controllare i LED dei controller di movimento: i controller con illuminazione luminosa sono abbinati e connessi, i controller debolmente illuminati non sono connessi.
6. Passare a **Start > portale per la realtà mista** nel PC e selezionare "menu". Verranno visualizzati i controller di movimento, insieme a un messaggio di stato:
    * Pronto: tutti i controller sono impostati.
    * Rilevamento perso: il portale per la realtà mista non riesce a trovare i controller. Tenerli davanti all'auricolare e riavviarli premendo il pulsante Windows per 4 secondi, quindi di nuovo per 2 secondi.
    * Batteria insufficiente: sostituire le batterie del controller.
7. Se si usa una scheda Bluetooth USB esterna, verificare che sia collegata a una porta USB 2,0 nera. Deve anche essere collegato al più lontano possibile da qualsiasi altro trasmettitore wireless o unità flash USB, incluso il connettore USB per la cuffia. 
8. Verificare che nel PC sia presente una sola radio Bluetooth facendo clic con il pulsante destro del mouse sul menu Start di Windows e selezionare Device Manager. Espandere la sezione Bluetooth e cercare una scheda. Se si usa la configurazione di desktop PC con la radio predefinita, controllare se è connessa un'antenna esterna. Se non è presente alcuna antenna esterna connessa, può causare problemi di rilevamento. In alternativa, usare un dongle Bluetooth esterno (USB), disabilitare la funzionalità Bluetooth interna e ritentare l'associazione e la connessione.
9. Chiudere la finestra Impostazioni Bluetooth se è aperta. Se è aperto in background, vengono effettuate numerose chiamate aggiuntive al protocollo Bluetooth.
10. Verificare il livello di batteria virtuale sul controller di movimento. In realtà mista, accendere i controller e sarà possibile visualizzare un'icona a forma di batteria. Se è rosso, sostituire le batterie. La segnalazione della batteria in genere segnala un livello superiore rispetto al livello effettivo immediatamente dopo la connessione di un controller. Attendere circa 15 secondi per consentire la stabilità del livello della batteria e quindi leggere il livello.
11. Rimuovere cuffie e altoparlanti Bluetooth in **impostazioni > dispositivi > Bluetooth & altri dispositivi** e spegnere i dispositivi. Usare i jack per la cuffia o i relatori incorporati in un auricolare a realtà mista per ottenere la migliore esperienza audio.
12. Se si dispone di altri dispositivi Bluetooth associati al PC, ad esempio cuffie o gamepad, rimuoverne alcuni. Selezionare **impostazioni > dispositivi > Bluetooth & altri dispositivi nel PC** , selezionare i dispositivi e quindi selezionare "Rimuovi dispositivo".
13. Scollegare il cavo USB sulla cuffia e collegarlo di nuovo al PC per riavviare la funzionalità del controller nel computer.
14. Il controller lampeggia quando è in fase di aggiornamento del firmware. Attendere il completamento dell'aggiornamento del firmware e visualizzare i controller in realtà mista.
15. Verificare che il PC sia connesso a una rete Wi-Fi 5GHz. Se il computer portatile è connesso a una rete Wi-Fi a 2,4 GHz, in genere condivide la connessione Bluetooth. Questo potrebbe influire negativamente sulle prestazioni Wi-Fi o Bluetooth, a seconda della progettazione del prodotto. Modificare la banda preferita in 5 GHz nelle impostazioni della scheda di rete. Se la rete non supporta 5GHz, è possibile usare un dongle Bluetooth al posto della funzionalità Bluetooth interna.
16. Se le impostazioni Bluetooth hanno controller di movimento già abbinati, Windows non individuerà i nuovi dispositivi fino a quando non vengono rimossi (se sono stati aggiunti usando un dongle specifico, possono essere rimossi solo con tale dongle).
17. Se il PC dispone di Bluetooth integrato e si verificano problemi di connessione, provare a usare una scheda Bluetooth USB. A tale scopo, è necessario disattivare la radio Bluetooth incorporata in Device Manager, quindi abbinare gli altri dispositivi Bluetooth con la nuova scheda.

### <a name="motion-controller-troubleshooting-flowchart"></a>Diagramma di flusso risoluzione dei problemi del controller di movimento

![Risoluzione dei problemi del diagramma di flusso per i controller di movimento](images/motion-controllers.jpg)

### <a name="my-controller-is-stuck-in-an-infinite-reboot-buzzing-after-leds-cycle"></a>Il controller è bloccato in un riavvio infinito (il ronzio dopo il ciclo LED).

Si tratta di un indicatore di batteria critico, quindi assicurarsi di avere batterie aggiornate nel dispositivo. Se il problema persiste, eseguire il [ripristino del dispositivo](motion-controller-problems.md#how-can-i-restore-the-controllers-to-factory-settings) per ripristinare le impostazioni predefinite del controller.

### <a name="im-trying-to-pair-my-controllers-but-they-never-show-up-in-the-add-a-new-device-menu-in-bluetooth-settings"></a>Sto tentando di associare i controller, ma non vengono mai visualizzati nel menu "Aggiungi un nuovo dispositivo" nelle impostazioni Bluetooth.

Verificare che non siano già stati associati controller, rimuoverli e riprovare. Se il problema persiste, riavviare il computer e riprovare. Se il tentativo non riesce, consultare le [domande frequenti su Bluetooth](motion-controller-problems.md#how-can-i-tell-if-im-using-bluetooth-technology).

### <a name="wi-fi-speeds-becomes-slow-on-my-notebook-when-motion-controllers-are-turned-on"></a>Le velocità Wi-Fi diventano lente nel notebook quando i controller di movimento sono accesi.

Il notebook può condividere l'antenna Wi-Fi con Bluetooth quando si è connessi a un punto di accesso a 2,4 GHz. Controllare da Gestione dispositivi se è possibile cambiare la preferenza della banda su 5GHz. Se la rete 5GHz non è disponibile e le prestazioni sono gravemente influenzate, è consigliabile usare un dongle Bluetooth.

![È possibile trovare le impostazioni di selezione banda Wi-Fi tramite Gestione dispositivi](images/wifi5ghz.png)

### <a name="my-second-controller-takes-a-long-time-to-reconnect"></a>Il secondo controller impiega molto tempo per la riconnessione.

Alcune versioni precedenti di Intel radio hanno riscontrato questo problema se i controller di movimento sono accesi nello stesso momento. Evitare di accendere i controller allo stesso tempo.

### <a name="my-qualcomm-bluetooth-radio-cannot-pair-controllers-after-a-pc-crash"></a>Non è possibile associare i controller a un arresto anomalo del computer.

I driver radio del dispositivo Qualcomm (QCA) prima di 10.0.0.448 potrebbero finire in uno stato non valido dopo un arresto anomalo di Windows. Spegnere completamente il PC per aggirare questo problema. 

### <a name="im-experiencing-poor-controller-tracking-with-marvell-radio"></a>Si verificano problemi di rilevamento del controller con la radio Marvell.

Passare a **Device Manager > bluetooth > Marvell avastr bluetooth > proprietà > driver** e assicurarsi di utilizzare driver 15.68.9210.47 o versione successiva.

### <a name="the-mixed-reality-portal-is-working-but-my-motion-controllers-are-tracking-poorly-controllers-keep-flying-away-shaking-etc"></a>Il portale per la realtà mista funziona, ma i controller di movimento eseguono un rilevamento scarso (i controller continuano a volare, tremando e così via).

1. Alcune condizioni di illuminazione possono influire sul rilevamento. Assicurarsi di non essere esposti alla luce solare diretta e che non si disponga di una grande quantità di punti luce visibili ai HMD (ad esempio, stringhe di luci come un albero di Natale). 
2. Controllare le [domande frequenti su Bluetooth](motion-controller-problems.md#how-can-i-tell-if-im-using-bluetooth-technology). Questi sintomi sono in genere causati da errori di comunicazione tra il controller e il PC host e indicano una scarsa qualità del collegamento Bluetooth.

### <a name="motion-controller-leds-are-not-lit-but-the-buttons-and-thumbstick-still-work-in-mixed-reality-portal"></a>I LED del controller di movimento non sono accesi, ma i pulsanti e levetta funzionano ancora nel portale di realtà mista.

La cache di calibrazione del controller di movimento potrebbe essere danneggiata. Per eliminare la cache, eseguire il comando seguente in un prompt dei comandi dell'amministratore:

`rmdir /S /Q C:\Windows\ServiceProfiles\LocalService\AppData\Local\Microsoft\Windows\MotionController\Calibration`

Questa cartella non è accessibile in Esplora risorse e può essere modificata solo da un prompt dei comandi dell'amministratore. Dopo aver eliminato la cartella, riavviare il PC e riconnettere i controller di movimento per ripristinare i file di calibrazione.

### <a name="motion-controllers-do-not-appear-in-steamvr-apps-and-games"></a>I controller di movimento non vengono visualizzati nelle app e nei giochi di SteamVR.

Se si è in grado di visualizzare i controller di movimento nella casa di Cliff, ma non nelle app e nei giochi SteamVR, il driver del modello di motion controller potrebbe non essere installato correttamente. Questo driver viene scaricato e installato automaticamente tramite Windows Update, ma se si usa un PC con criteri aziendali o se Windows Update è altrimenti limitato, potrebbe essere necessario installarlo manualmente. Per verificare che il driver del modello del controller di movimento sia installato correttamente:
1. Accendere entrambi i controller di movimento e assicurarsi che vengano visualizzati come "connessi" nell'app impostazioni in **dispositivi > Bluetooth & altri dispositivi** . Se non vengono visualizzati o visualizzati come "associati", [abbinarli](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/set-up-windows-mixed-reality).
2. Aprire Device Manager e cercare "motion controller-left" e "motion controller-Right" in "Bluetooth".
3. Selezionare uno dei due dispositivi, quindi passare a **visualizza > dispositivi per connessione** .
4. Verrà ora visualizzata una visualizzazione dei dispositivi Bluetooth del controller di movimento che eseguono il rollup nella radio Bluetooth. Nello stesso nodo dei due controller di movimento devono essere presenti due dispositivi "dispositivo HID Bluetooth" e, in ogni dispositivo HID Bluetooth, devono essere dispositivi denominati "motion controller" (con icone in grigio).
5. Fare doppio clic su ogni dispositivo "motion controller" e passare alla scheda **driver** . Verificare che la versione del driver elencata corrisponda a una di [queste versioni del driver del modello di motion controller](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/mixed-reality-software#mixed-reality-motion-controller-model-driver-release-history).

Per scaricare e installare manualmente il driver del modello di motion controller, visitare [Questa pagina](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/mixed-reality-software#mixed-reality-motion-controller-model-driver-release-history) e cercare la versione del driver corrispondente alla versione di Windows 10. Le istruzioni di installazione sono disponibili nella pagina di download.

### <a name="the-motion-controllers-firmware-update-takes-significantly-longer-than-two-minutes"></a>L'aggiornamento del firmware dei controller di movimento richiede molto più di due minuti.

Controllare le [domande frequenti su Bluetooth](motion-controller-problems.md#how-can-i-tell-if-im-using-bluetooth-technology). Una scarsa qualità dei collegamenti Bluetooth è in genere la fonte di questi problemi.

### <a name="i-just-inserted-fresh-batteries-but-the-controller-virtual-battery-level-does-not-indicate-full-level"></a>Ho appena inserito batterie nuove, ma il livello di batteria virtuale del controller non indica il livello completo.

Il livello di batteria del controller di movimento viene ottimizzato per le batterie AA. Alcune batterie ricaricabili a bassa tensione potrebbero non essere segnalate come complete anche se completamente addebitate.

### <a name="my-controller-does-not-vibrate-when-battery-is-low"></a>Il controller non vibra quando la batteria è insufficiente.

Haptics è disabilitato quando il livello della batteria diventa basso. Sostituire le batterie.

### <a name="my-device-vibrated-three-times-and-then-shutdown"></a>Il dispositivo è stato vibrato tre volte e quindi arrestato.

Le batterie vengono eseguite in basso e si raggiunge la soglia di riduzione. Sostituire le batterie.

### <a name="my-samsung-motion-controllers-touchpad-is-off-center-or-has-a-dead-spot"></a>Il touchpad di Samsung Motion controller è esterno al centro o ha un posto non attivo.

Si tratta probabilmente di un difetto hardware ed è necessario tornare al rivenditore o al produttore dell'apparecchiatura per un sostituto o uno scambio.

### <a name="the-controller-isnt-working-correctly-and-i-cant-update-the-device"></a>Il controller non funziona correttamente e non è possibile aggiornare il dispositivo.

Ripristinare le condizioni di fabbrica (sono necessarie batterie aggiornate):
1. Scollegare e spegnere i controller.
2. Aprire il coperchio della batteria.
3. Inserire le nuove batterie.
4. Premere e tenere premuto il pulsante di associazione (la scheda nella parte inferiore sotto le batterie).
5. Tenendo premuto il pulsante di associazione, accendere il controller premendo e tenendo premuto il pulsante Windows per cinque secondi (tenere premuto entrambi i pulsanti).
6. Rilasciare i pulsanti e attendere l'accensione del controller. Questa operazione richiede fino a 15 secondi e non ci sono indicatori quando si verifica il ripristino del dispositivo. Se il dispositivo attiva immediatamente il rilascio del pulsante, la sequenza dei pulsanti di ripristino non viene registrata ed è necessario riprovare.
7. Passare a **impostazioni > Bluetooth > altri dispositivi** e selezionare "motion controller-left" o "motion controller-Right" (Rimuovi dispositivo) per rimuovere le associazioni controller obsolete dalle impostazioni Bluetooth. 
8. Associare nuovamente il controller al PC.
9. Dopo la connessione con l'host e HMD, il dispositivo viene aggiornato al firmware più recente disponibile.

### <a name="lights-and-indicators"></a>Indicatori luminosi e indicatori

L'anello della costellazione LED e haptics indicano lo stato del controller di movimento.

| State    | Causa dello stato | Comportamento leggero e vibrazionale associato allo stato |
|----------------------------|-----------------------------|----------------------------------------------------------------------|
| **Accendere**               | Premere e tenere premuto il pulsante Windows sul controller per due secondi per accendere il controller.       | I LED accendono e il controller vibra una volta. |
| **Spegnimento**              | Premere e tenere premuto il pulsante Windows sul controller per quattro secondi per disattivare il controller.      | I LED si spengono e il controller viene vibrato due volte. |
| **Sospeso**               | Il controller entra automaticamente nello stato di sospensione quando non è in movimento per 30 secondi. Il controller viene riattivato automaticamente quando rileva il movimento tranne quando il dispositivo non è associato al PC host. In tal caso, sarà necessario premere un pulsante per riattivarlo. | I LED si spengono e lampeggiano ogni tre secondi in stato di sospensione. |
| **Abbinamento**                | Premere e tenere premuto il pulsante di associazione nel caso della batteria per tre secondi.     | I LED passano lentamente in modalità di associazione e diventano solidi quando si esce dalla modalità di associazione. Il controller vibra una volta se l'associazione ha avuto esito positivo o viene Vibrata tre volte se l'associazione ha esito negativo e si verifica il timeout. |
| **Connessione/disconnessione del controller dal PC** | Il controller si connette al PC dopo che è stato acceso oppure il controller si disconnette dal PC durante l'utilizzo per qualche motivo.| Il controller vibra una volta sulla connessione del PC o sulla disconnessione. |
| **Livello batteria basso**      | Il livello della batteria è basso.| Quando la batteria è insufficiente, non è presente alcun LED o indicazione di vibrazione. Icona dell'indicatore della batteria nell'handle della rappresentazione del controller in cuffia. Quando la batteria è insufficiente, l'icona dell'indicatore visualizzerà 1/4 Full. |
| **Livello di batteria critico** | Durante l'accensione quando il livello della batteria è "critico". Il livello di batteria "critico" indica che la potenza è insufficiente e che il controller si spegne automaticamente.| Il controller vibra tre volte quando lo si accende e quindi si disattiva automaticamente. Quando si avvicina questo stato, l'icona dell'indicatore della batteria viene visualizzata in rosso. |


### <a name="how-can-i-tell-if-im-using-bluetooth-technology"></a>Come è possibile stabilire se si usa la tecnologia Bluetooth?

I controller di movimento usano la stessa tecnologia Bluetooth disponibile in molti dispositivi consumer e sono progettati per funzionare con la funzionalità Bluetooth inclusa in tutti i PC recenti. Per verificare che il PC disponga di una radio Bluetooth (se il dispositivo ha superato il controllo di compatibilità della realtà mista): 
* Fare clic con il pulsante destro del mouse sul menu Start di Windows e selezionare "Device Manager". 
* Espandere la sezione Bluetooth e cercare un adapter. 
* Se il PC non ha Bluetooth, un dongle consigliato è il plug-in [USB bluetooth 4,0 Low Energy Micro Adapter](https://www.amazon.com/Plugable-Bluetooth-Adapter-Raspberry-Compatible/dp/B009ZIILLI/ref=sr-1-1?ie=UTF8&qid=1490148230&sr=8-1&keywords=plugable+broadcom). \
![Screenshot di un esempio Device Manager. L'adapter è la radio Bluetooth.](images/devicemanagerbtadapterpic.png) 


### <a name="my-pc-has-bluetooth-technology-but-im-having-problems-with-my-motion-controllers"></a>Il PC ha la tecnologia Bluetooth ma si verificano problemi con i controller di movimento.

I controller di movimento dovrebbero funzionare con altre tastiere, topi e controller di gioco Bluetooth, ma l'esperienza varia a seconda del modello di tastiera, mouse o controller di gioco che usi. Ecco alcune operazioni che è possibile eseguire per migliorare le prestazioni:
* Se il computer dispone di Bluetooth ma si verificano ancora problemi con i controller di movimento, sostituire la radio Bluetooth con la scheda Bluetooth esterna collegabile collegata a USB. Si noti che è possibile disporre di un solo adattatore radio Bluetooth attivo alla volta. Se si collega un'altra radio, oltre a una radio esistente, è necessario disabilitare la radio Bluetooth esistente in Device Manager (fare clic con il pulsante destro del mouse sulla scheda e selezionare "Disabilita dispositivo") e annullare la coppia/riassociare tutti i dispositivi Bluetooth precedenti.
* Se si usa una scheda Bluetooth USB, connetterla a una porta USB 2,0 (2,0 le porte sono nere e non sono etichettate "SS"), se disponibili. La porta deve essere fisicamente separata da:
    - connettore USB HMD
    - unità flash
    - unità disco rigido
    - i ricevitori USB wireless come quelli per tastiere/topi sono idealmente collegati al più possibile da questi altri connettori per collegare la scheda Bluetooth USB al lato opposto del computer.
* Non installare software di terze parti.
* Chiudere la finestra Impostazioni Bluetooth se è aperta. Lasciarla aperta in background significa che vengono effettuate numerose chiamate aggiuntive al protocollo Bluetooth.
* Disabilitare l'impostazione "Mostra notifica per la connessione tramite una coppia Swift" in Bluetooth & altri dispositivi per ridurre l'attività di analisi radio host.
* Se si usa una scheda Bluetooth interna, assicurarsi di usare un'antenna Bluetooth esterna. 
  * La mancanza di antenna Bluetooth esterna in questo caso è nota per causare problemi di rilevamento. 
  * Se questa operazione non funziona, usare un dongle Bluetooth esterno (USB) dopo aver disattivato il Bluetooth interno.
* È importante che il dispositivo venga visualizzato sotto la categoria "mouse, tastiera & Pen" nelle impostazioni Bluetooth. Se in "altri dispositivi", disaccoppiare e associare il dispositivo.
* Rimuovere, annullare la coppia e spegnere cuffie e altoparlanti Bluetooth. Questi non sono supportati con la realtà mista di Windows. Per la migliore esperienza audio, è possibile usare il connettore cuffia o gli altoparlanti predefiniti per l'auricolare della realtà mista.

### <a name="how-can-i-pair-my-motion-controllers-to-a-windows-mixed-reality-headset-with-built-in-bluetooth-radio-or-return-them-to-their-factory-pairing"></a>Come è possibile associare i controller di movimento a un auricolare di realtà mista di Windows con la radio Bluetooth incorporata o per restituirli alle associazioni di fabbrica?

Alcuni auricolari per la realtà mista di Windows, tra cui Acer 500 e Samsung Odyssey +, dispongono di radio Bluetooth predefinite da usare con i controller di movimento. I controller di movimento dotati di questi auricolari sono pre-abbinati all'auricolare dalla factory e non richiedono che il PC disponga di una radio Bluetooth separata. Questi controller di movimento _possono_ essere abbinati manualmente alla radio Bluetooth del PC, ad esempio per l'uso con auricolari a realtà mista di Windows che non dispongono di radio Bluetooth predefinite. Per riportare i controller di movimento alla propria associazione di fabbrica, in alternativa, per associarli a un auricolare di realtà mista di Windows con la radio Bluetooth incorporata, eseguire l'app complementare del dispositivo dell'auricolare (ad esempio, l'app "Acer ' 500" o "Samsung HMD Odyssey + Setup", installata automaticamente la prima volta che l'auricolare è collegata) e seguire le istruzioni per l'associazione del controller di movimento.


## <a name="performance-questions"></a>Domande sulle prestazioni

### <a name="how-can-i-tell-if-the-windows-mixed-reality-headset-is-rendering-at-60hz-or-90hz-framerate"></a>Come è possibile stabilire se l'auricolare della realtà mista di Windows sta eseguendo il rendering a 60Hz o 90Hz framerate?

Controllare il **portale del dispositivo > scheda prestazioni** . 

**Nota** : se si dispone di una GPU discreta con porte HDMI 2,0 e una CPU con quattro o più core fisici, si dovrebbe ottenere 90 Hz. Se la GPU dispone solo di un output HDMI 1,4, è possibile usare un adattatore DisplayPort per [hdmi 2,0](https://holodocswiki.com/wiki/Recommended_adapters_for_Windows_Mixed_Reality_Capable_PCs) come soluzione alternativa. 

**Nota** : la **visualizzazione dell'auricolare > le impostazioni della qualità visiva** influiscono solo sul rendering dell'esperienza della Home realtà mista di Windows.

### <a name="what-do-i-do-if-my-pc-appears-to-be-running-slowly"></a>Cosa fare se il PC sembra essere in esecuzione lentamente?

Il sistema può essere lento per diversi motivi e, nella maggior parte dei casi, questo sarà sottolato dopo alcuni secondi. Se si verifica questo problema in lunghi periodi di tempo:
1. Chiudere l'applicazione inutilizzata sul desktop.
2. Verificare che il computer portatile sia collegato a una fonte di alimentazione.
3. Verificare che il PC non stia scaldando.
4. Abbassare la qualità visiva nella Home realtà mista di Windows.
5. Assicurarsi di disporre dei driver grafici più recenti per il PC (vedere la sezione driver grafici).

### <a name="my-pc-is-warming-up-as-i-run-the-mixed-reality-experiences-how-do-i-keep-it-cool"></a>Il mio PC si sta scaldando durante l'esecuzione delle esperienze di realtà miste. Ricerca per categorie mantenerlo interessante?

1. Assicurarsi che la batteria venga addebitata e che l'alimentazione sia collegata.
2. Assicurarsi che le ventole che soffiano all'interno o all'esterno del PC non siano bloccate.
3. Usare il PC in un ambiente relativamente sporadico.
4. Verificare che non siano presenti fonti di calore, ad esempio il sole o i sfiati di calore, a cui punta il PC.

### <a name="my-visuals-are-choppy-load-slowly-or-dont-look-good"></a>Gli oggetti visivi sono irregolari, vengono caricati lentamente o non sembrano corretti.
* Assicurarsi che l'auricolare sia collegato alla scheda grafica corretta nel PC. Alcuni PC hanno schede grafiche sia integrate che discrete. La scheda discreta offre in genere le prestazioni migliori. [Altre informazioni sull'hardware del PC](https://support.microsoft.com/en-us/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines).
* Chiudere le applicazioni inutilizzate sul desktop.
* Assicurarsi che le cuffie si trovino comodamente (spostarle in basso e in alto o a sinistra e a destra per adattarle).
* Modificare le impostazioni visive dell'auricolare in **impostazioni > realtà mista > visualizzazione dell'auricolare** . Quando la "qualità visiva" è impostata su "automatico", si sceglierà la migliore esperienza di realtà mista per il PC. Per un'esperienza con un maggior numero di dettagli visivi, impostare "qualità visiva" su "alta". Se gli oggetti visivi sono increspati, potrebbe essere necessario selezionare un'impostazione inferiore.
* Provare a regolare la calibrazione dell'auricolare. Le lenti devono essere modificate in modo che corrispondano alla distanza interpupillare (dpi), alla distanza tra gli alunni. Se non si conosce il valore di dpi, un optometrista dovrebbe essere in grado di misurarlo. Sono inoltre disponibili siti Web progettati per misurare i dpi. Quando si conosce il dpi, usare la manopola di calibrazione dell'auricolare per apportare modifiche. Se la cuffia non ha una manopola di calibrazione, selezionare **impostazioni > realtà mista > visualizzare l'auricolare** e modificare il "controllo di calibrazione".


## <a name="tracking-system-problems"></a>Rilevamento dei problemi del sistema

### <a name="the-system-cannot-find-the-boundary-and-im-being-presented-with-setup-ui"></a>Il sistema non riesce a trovare il limite e viene visualizzata l'interfaccia utente del programma di installazione.

Ciò significa che il sistema di rilevamento non è stato in grado di riconoscere l'ambiente. Se ci si trova in un nuovo ambiente, è necessario configurare il [limite](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/set-up-windows-mixed-reality#set-up-your-room-boundary). Se in precedenza è stato usato il dispositivo in questo ambiente e si è configurato un limite:
* Assicurarsi che la stanza abbia una luce sufficiente.
* Assicurarsi di aver indossato il dispositivo e di aver esaminato la stanza. Il dispositivo deve osservare l'ambiente per conoscerne la posizione. Non troverà i limiti se si trova su una scrivania o una tabella.
* Scollegare il dispositivo, chiudere la realtà mista di Windows e ricollegare il dispositivo.
* Potrebbe essersi verificato un cambiamento nell'ambiente in uso e il dispositivo non lo riconosce più. Provare a configurare un nuovo limite.

Se questi passaggi non risolvono il problema, eliminare i dati dell'ambiente e configurare di nuovo il limite.

### <a name="the-system-is-presenting-me-with-ui-that-asks-me-to-choose-setup-for-all-experiences-or-seatedstanding-and-i-see-my-bounds"></a>Il sistema sta presentando l'interfaccia utente che mi chiede di scegliere la configurazione per tutte le esperienze o la posizione e I limiti.

Il dispositivo impiega troppo tempo per trovare i limiti. È possibile ignorare questo messaggio scegliendo l'opzione per l'utilizzo di un limite e verrà visualizzata la Home realtà mista di Windows con i limiti presenti.

### <a name="i-frequently-see-a-message-saying-ive-lost-my-bounds"></a>Spesso viene visualizzato un messaggio che informa che ho perso i limiti.

Il sistema di rilevamento è in fase di rilevamento e identifica l'ambiente. In questo stato, il dispositivo non può più visualizzare i limiti e la cuffia passa a 3DOF per evitare di inserirsi nel mondo reale fino a quando non individua di nuovo i limiti. Per risolvere il problema:
1. Assicurarsi che la stanza disponga di una luce sufficiente.
2. Eseguire di nuovo l'installazione se è stata recentemente ridecorata o rimodellata la chat room.
3. Scollegare il dispositivo, chiudere la realtà mista di Windows e ricollegarlo.
4. Cancellare i dati dell'ambiente e configurare di nuovo il dispositivo.
5. Se il messaggio viene mantenuto, contattare il supporto tecnico.

### <a name="i-can-look-around-but-i-cant-translate-im-stuck-in-3dof"></a>Posso esaminare ma non riesco a tradurre (sono bloccato in 3DOF).

Ciò significa che il sistema di rilevamento non è in grado di generare la richiesta o che l'applicazione ha interrotto l'uso dei nuovi dati di post per il rendering. Verificare quanto segue:
* Assicurarsi che la stanza abbia una luce sufficiente.
* Assicurarsi che la chat room disponga di informazioni sufficienti per la traccia.
* Scollegare il dispositivo, chiudere la realtà mista di Windows e ricollegare il dispositivo.
* Se il messaggio viene mantenuto, contattare il supporto tecnico

### <a name="the-view-in-the-hmd-is-completely-frozen"></a>La visualizzazione in HMD è completamente bloccata.

Ciò significa in genere che l'applicazione o un componente a livello di sistema non è riuscito. Provare a:
1. Per uscire dall'applicazione, fare clic sul pulsante "Home".
2. Scollegare il dispositivo, chiudere MRP e collegare di nuovo il dispositivo.
3. Riavviare il computer.

### <a name="i-frequently-see-a-black-border-around-the-edges-of-the-view-in-the-hmd-sometimes-it-looks-like-im-looking-down-a-tunnel"></a>Spesso viene visualizzato un bordo nero attorno ai bordi della visualizzazione in HMD. In alcuni casi sembra che si stia cercando un tunnel.

Ciò significa che l'applicazione non è in grado di raggiungere la frequenza dei fotogrammi nel PC e il sistema usa i vecchi frame per eseguire il rendering della visualizzazione in HMD. Poiché le applicazioni eseguono solo il rendering della parte del mondo che si sta osservando, se non hanno raggiunto costantemente la frequenza dei fotogrammi, il sistema tenterà di continuare a eseguire il rendering del mondo da un punto di vista precedente e fornirà i dettagli mancanti con il nero. Se il problema si verifica di frequente:
1. Chiudere o terminare tutti i programmi non necessari per liberare memoria e CPU.
2. Ridurre le impostazioni dei dettagli nell'applicazione.
3. Ridurre le impostazioni di dettaglio nelle impostazioni della realtà mista di Windows.

### <a name="the-view-in-the-hmd-is-jittering-and-stuttering-a-lot"></a>La visualizzazione in HMD è innervosa e balbetta molto.

Questo problema può verificarsi per diversi motivi. Le cause principali sono il fatto che il sistema non è in grado di eseguire il rendering del contenuto nell'auricolare o che si sono verificati problemi nel sistema di rilevamento. Verificare quanto segue:
1. Verificare che il PC non sia in conflitto di risorse. Aprire Task Manager e assicurarsi che le risorse di calcolo siano gratuite (ad esempio, 80% di CPU gratuito, 400MB di RAM e i/o disco è inferiore al 80%).
2. Assicurarsi di disporre dei driver grafici più recenti per l'hardware. Per altre informazioni, vedere la sezione driver grafica.
3. Assicurarsi che la stanza abbia una luce sufficiente.
4. Scollegare il dispositivo, chiudere la realtà mista di Windows e ricollegare il dispositivo.
5. Riavviare il PC.
6. Se il problema persiste, contattare il supporto tecnico.

### <a name="the-world-briefly-froze-and-perhaps-tilted-or-flipped-upside-before-returning-to-normal"></a>Il mondo si è bloccato brevemente e probabilmente inclinato o capovolto prima di tornare al normale.

Il problema potrebbe essere causato da un'app o da un componente a livello di sistema che raggiunge un errore irreversibile o da una mancanza temporanea di memoria o risorse della CPU. Verificare quanto segue:
1. Aprire "Task Manager" e verificare di disporre di almeno il 20% di memoria disponibile per la CPU e di 400MB (ad esempio, 80% di CPU disponibile, 400MB di RAM e i/o su disco sono inferiori al 80%).
2. Aprire "Visualizzatore eventi" e passare a **registri di Windows >** le voci degli eventi di errore e dell'applicazione per tutto il tempo del blocco. Controllare se si sono verificati arresti anomali dei processi.
3. Se il problema persiste, provare a riavviare il computer.

### <a name="the-world-flipped-upside-down-momentarily-and-returned-to-normal"></a>Il mondo è stato capovolto momentaneamente e restituito alla normalità.

Questa situazione è in genere causata da errori durante il recupero dei dati dei sensori dall'auricolare per informare gli algoritmi di rilevamento. Se il problema si verifica di frequente:
1. Collegare la cuffia a una porta USB 3,0 diversa.
2. Collegare la cuffia direttamente al PC invece che a un hub USB 3,0.
3. Se il problema persiste, contattare il supporto tecnico.

### <a name="the-world-is-tilted-but-i-can-navigate-and-walk-around-fine-in-windows-mixed-reality"></a>Il mondo è inclinato, ma è possibile spostarsi all'interno di una realtà mista di Windows.

Questa situazione è in genere causata da errori di dati del sensore registrati nei dati dell'ambiente archiviati nel PC. Ciò può comportare l'inclinazione della realtà mista di Windows, a volte in modo permanente. Attenersi alla procedura seguente:
1. Scollegare il HMD, chiudere la realtà mista di Windows e collegare di nuovo l'auricolare.
2. Riavviare il computer.
3. Cancellare i dati dell'ambiente.

## <a name="webvr-questions"></a>Domande su WebVR

### <a name="why-cant-i-see-my-controllers-when-viewing-vr-content-from-edge"></a>Perché non è possibile visualizzare i controller quando si visualizzano i contenuti VR da Edge?

Non tutto il contenuto di WebVR viene creato per supportare i controller di movimento. WebVR consente agli sviluppatori di contenuti di supportare diversi tipi di input, ad esempio controller di gioco o controller di movimento. Se non si visualizzano i controller in un sito, è probabile che non disponga del supporto del controller di movimento.

### <a name="why-cant-i-use-the-mouse-in-an-immersive-webvr-view"></a>Perché non è possibile usare il mouse in una visualizzazione WebVR immersiva?

Si tratta di una funzionalità facoltativa della specifica WebVR. Non tutti i browser supportano questa funzionalità e non tutto il contenuto di WebVR viene creato per supportare l'input del mouse. WebVR consente agli sviluppatori di contenuti di supportare diversi tipi di input, ad esempio mouse, tastiera, controller di gioco o controller di movimento. Il comportamento di input del mouse varia a seconda del browser. In Microsoft Edge gli autori di siti Web devono assicurarsi di usare "pointerlock" per la presentazione all'auricolare per il funzionamento dell'input del mouse.

### <a name="why-does-my-controller-look-like-a-viveoculus-has-strange-orientation-or-the-buttons-are-incorrectly-mapped"></a>Perché il mio controller è un aspetto di vive/Oculus, presenta un orientamento strano o i pulsanti sono mappati in modo errato?

Il sito Web probabilmente non dispone del supporto per il controller di movimento completo.

### <a name="why-cant-i-view-360-degree-videos-from-youtubefacebookvimeothe-guardiannew-york-times-etc-from-edge-in-vr"></a>Perché non è possibile visualizzare video di 360 Degree da YouTube/Facebook/Vimeo/The Guardian/New York Times e così via da Edge in VR?

Analogamente a qualsiasi altra specifica Web o standard, l'autore ha la possibilità di implementarlo o meno. È disponibile una specifica WebVR che consente ai siti Web di avviare esperienze VR direttamente dal browser e gli autori di questi siti Web non hanno implementato questa specifica in questo momento. In alcune piattaforme possono essere disponibili app scaricabili che consentono la visualizzazione di contenuto VR da tali fornitori.

### <a name="why-cant-i-enter-vr-from-firefox-or-chrome"></a>Perché non è possibile immettere VR da Firefox o Chrome?

WebVR è attualmente supportato solo da dispositivi di realtà mista Windows in Microsoft Edge.

### <a name="when-i-enter-vr-from-a-website-why-do-i-see-a-blank-screen-in-my-headset"></a>Quando si immette VR da un sito Web, perché viene visualizzata una schermata vuota nell'auricolare?

Il sito Web potrebbe non aver implementato il supporto per i computer con più GPU (inclusi i portatili GPU ibridi). Provare a:
* Ricaricare la pagina.
* Nei computer desktop collegare l'auricolare alla stessa scheda grafica del monitor che visualizza Microsoft Edge. Inserire entrambi i valori nella scheda grafica più elevata, non nella scheda grafica integrata.

### <a name="when-i-exit-vr-when-watching-a-video-from-edge-the-sound-continues-playing-but-the-edge-window-is-grayed-out"></a>Quando si esce da VR quando si guarda un video da Edge, il suono continua a riprodurre, ma la finestra perimetrale è disabilitata.

Si tratta di un problema noto quando si esegue WebVR da Edge nell'Cliffhouse realtà mista. Per risolverlo, premere ESC sulla tastiera anziché premere il pulsante Windows per uscire dall'esperienza WebVR oppure attivare la finestra bordo grigio selezionando il pulsante e quindi arrestare il video.

### <a name="can-i-use-webvr-on-the-hololens"></a>È possibile usare WebVR in HoloLens?

A questo punto, Microsoft non ha annunciato alcuna cosa su WebVR in HoloLens.

### <a name="why-is-my-view-at-floor-level-when-viewing-webvr-content-from-edge"></a>Perché la visualizzazione è a livello di piano quando si Visualizza il contenuto di WebVR da Edge?

Il sito Web non supporta correttamente le cuffie per la realtà mista di Windows. Per risolvere il problema:
1. Posizionare l'auricolare sul pavimento dello spazio.
2. Passare alla pagina WebVR usando Microsoft Edge sul desktop (non all'interno di realtà mista).
3. Fare clic sul pulsante nella pagina Web per immettere VR.
4. Attendere 5-10 secondi perché l'esperienza entri completamente in modalità immersiva.
5. Prelevare la cuffia e posizionarla in testa.

### <a name="the-display-is-very-low-resolution-in-some-webvr-experiences"></a>La visualizzazione è una soluzione molto bassa in alcune esperienze di WebVR.

I siti Web non supportano correttamente le cuffie ad alta risoluzione. Per aggirare questo problema:
* Se si avvia WebVR dal desktop (invece che dall'interno della Cliffhouse realtà mista), assicurarsi che la finestra sia ingrandita prima di immettere VR.
* Evitare di ridimensionare la finestra Microsoft Edge dopo aver immesso VR.

### <a name="why-does-the-webvr-immersive-view-exit-when-i-change-browser-tabs"></a>Perché la visualizzazione immersiva WebVR viene chiusa quando si modificano le schede del browser?

Si tratta di un comportamento previsto. Per motivi di sicurezza, solo la scheda Active browser può accedere alle cuffie connesse.

### <a name="why-cant-i-hear-audio-on-a-particular-webvr-experience"></a>Perché non è possibile ascoltare l'audio in una particolare esperienza WebVR?

Il sito Web può usare il formato di file audio OGG, che attualmente non è supportato da Microsoft Edge.

È possibile segnalare i siti interrotti direttamente al team del browser Microsoft Edge in [Issue Tracker](https://developer.microsoft.com/en-us/microsoft-edge/platform/issues/)o tramite twitter usando [#EdgeBug hashtag](https://blogs.windows.com/msedgedev/2016/08/11/edgebug-twitter/).

### <a name="why-does-haptic-feedback-not-work-in-webvr-with-motion-controllers"></a>Perché i feedback tattili non funzionano in WebVR con i controller di movimento?

Microsoft Edge attualmente non supporta haptics nelle estensioni dell'API di WebVR Gamepad.


## <a name="steamvr-questions"></a>Domande su SteamVR

### <a name="how-can-i-play-steamvr-games-in-my-windows-mixed-reality-immersive-headset"></a>In che modo è possibile riprodurre I giochi di SteamVR in una serie di funzionalità di Windows mista a realtà mista

È necessario installare la realtà mista di Windows per SteamVR nel PC e configurare SteamVR:
* [Scaricare e installare SteamVR](https://steamcdn-a.akamaihd.net/client/installer/SteamWindowsMRInstaller.exe).
* Avviare SteamVR. L'esercitazione su SteamVR dovrebbe avviarsi automaticamente.
* Connettere l'auricolare al PC e accendere i controller di movimento.
* Una volta che la Home realtà mista di Windows è stata caricata e i controller sono visibili, aprire l'app Steam sul desktop.
* Usare l'app Steam per avviare un gioco SteamVR dalla libreria di Steam. Per avviare giochi SteamVR senza togliere la cuffia, è possibile trovarli e avviarli con l'inizio della realtà mista di Windows **> tutte le app** . 

### <a name="i-get-a-message-that-says-to-use-steamvr-with-windows-mixed-reality-you-need-to-install-the-latest-windows-update-or-windows-developer-mode-required"></a>Viene visualizzato un messaggio che indica "per usare SteamVR con la realtà mista di Windows, è necessario installare la versione più recente di Windows Update" o "Windows Developer Mode required".

1. Verificare che il PC esegua la versione più recente di Windows 10. Per verificarlo, passare a **impostazioni > sistema > informazioni su** . In "specifiche di Windows" verificare che "compilazione sistema operativo" sia 16299,64 o superiore.
2. Assicurarsi che non siano presenti aggiornamenti in attesa di download o di installazione. Passare a **impostazioni > aggiorna & sicurezza > Windows Update** e selezionare "Verifica disponibilità aggiornamenti". Potrebbe essere necessario controllare gli aggiornamenti più volte, quindi continuare a controllare la disponibilità di aggiornamenti fino a quando non sono disponibili altri aggiornamenti e quindi riavviare il PC.

### <a name="steamvr-is-crashing-after-updating-windows"></a>SteamVR si arresta in modo anomalo dopo l'aggiornamento di Windows.

Alcune versioni precedenti della realtà mista di Windows per SteamVR non sono più compatibili con Windows. È possibile che si disponga di una versione precedente della realtà mista di Windows per SteamVR. Per assicurarsi di essere aggiornati:
1. Nella libreria di Steam passare a **Software > realtà mista di Windows per SteamVR** .
2. Fare clic con il pulsante destro del mouse e passare a "Properties".
3. Selezionare la scheda "Aggiorna" e selezionare "Mantieni sempre l'applicazione aggiornata".
4. Forzare l'aggiornamento passando alla scheda "file locali" e selezionando "Verifica integrità dei file dell'applicazione".
5. Riavviare Steam e SteamVR.

Se è ancora in corso l'arresto anomalo di SteamVR dopo l'aggiornamento, è possibile che nel computer siano presenti due installazioni della realtà mista di Windows per SteamVR. Per verificare se questo è il caso:
1. Individuare%LocalAppData%\openvr\openvrpaths.VrPath e aprirlo nel blocco note.
2. Nella sezione "driver esterni" cercare più voci per "MixedRealityVRDriver" 
   ```json
   "external_drivers" : [
      "D:\\Steam\\steamapps\\common\\MixedRealityVRDriver",
      "E:\\Steam\\steamapps\\common\\MixedRealityVRDriver"
   ],
   ```
3. Se vengono visualizzate più voci, rimuovere le precedenti delle due voci. Si noti che, una volta che è presente una sola voce, non dovrebbe essere più una virgola alla fine della riga, ad esempio:
   ```json
   "external_drivers" : [
      "D:\\Steam\\steamapps\\common\\MixedRealityVRDriver"
   ],
   ```
4. Salvare il file e chiuderlo.
5. Riavviare Steam e SteamVR.

### <a name="my-controllers-arent-working-as-expected-in-steamvr"></a>I controller non funzionano come previsto in SteamVR.

1. Chiudere SteamVR.
2. Tornare alla Home realtà mista e verificare che i controller funzionino come previsto.
3. Avviare di nuovo l'esperienza SteamVR e riportare i controller alla normalità.
4. Se i problemi permangono, inviare commenti e suggerimenti tramite l' [Hub feedback Windows](https://support.microsoft.com/en-us/help/4021566/windows-10-send-feedback-to-microsoft-with-feedback-hub-app) nella categoria realtà mista e includere SteamVR nel riepilogo.

Si noti che i controller di movimento verranno usati in modo diverso in giochi diversi. Di seguito sono riportate alcune informazioni di base per iniziare:
* Per aprire il dashboard di Steam, premere il pulsante destro del mouse sul levetta di sinistra.
* Per uscire da un gioco SteamVR e tornare alla Home page della realtà mista di Windows, premere il pulsante Windows. Quindi selezionare il pulsante Home realtà mista visualizzato sullo schermo.

### <a name="my-left-and-right-controllers-are-reversed-in-steamvr"></a>I controller sinistro e destro sono invertiti in SteamVR.

Avviare il gioco con i controller disattivati e quindi attivare il pulsante sinistro, seguito da quello destro.

### <a name="my-games-are-running-slowly"></a>I miei giochi vengono eseguiti lentamente.

1. Verificare che il PC soddisfi le specifiche per SteamVR in realtà mista di Windows
2. Verificare che il PC soddisfi le specifiche per il gioco SteamVR che si sta riproducendo.
2. Nel portale per la realtà mista sul desktop selezionare "Sospendi" per arrestare l'anteprima del desktop.
3. Seguire le istruzioni riportate sopra per assicurarsi che sia in esecuzione Windows 10 Build 16299,64 o versione successiva.
4. Verificare che il PC disponga dei driver grafici più recenti.
5. Controllare Gestione attività per vedere quali altri processi potrebbero essere in esecuzione nel PC e che utilizzano risorse.
6. Verificare se il download di un gioco è in background. In questo modo è possibile utilizzare le risorse e far funzionare i giochi.
7. Si verifica un problema di prestazioni noto che interessa una piccola classe di app che non dispongono di una finestra visibile, ad esempio SteamVR Home. La maggior parte delle app non rientra in questa categoria e una correzione sarà disponibile in un aggiornamento futuro.

Se si verificano ancora problemi di prestazioni imprevisti, inviare commenti e suggerimenti tramite l'hub feedback di Windows. Assicurarsi di seguire le istruzioni per [includere una traccia delle prestazioni di SteamVR](using-steamvr-with-windows-mixed-reality.md#sharing-feedback-on-steamvr). 

### <a name="steamvr-is-showing-a-compositor-error-for-example-shared-ipc-compositor-connect-failed-400"></a>SteamVR Mostra un errore del Compositor (ad esempio, "Shared IPC compositor Connect failed (400)").

Esiste un problema noto che può verificarsi se l'auricolare e il monitor primario si trovano su due schede video diverse. Alleghi il monitor alla stessa scheda della cuffia e configuri il monitoraggio in modo che sia il monitor primario in **impostazioni app > sistema > visualizzare** .

### <a name="steamvr-content-appears-in-the-wrong-place-like-beneath-the-floor-or-above-my-head"></a>Il contenuto di SteamVR viene visualizzato nella posizione sbagliata, ad esempio sotto il piano o sopra la mia testa.

Reimposta la posizione: 
1. Fare clic su levetta del controller di sinistra per visualizzare il "dashboard di SteamVR".
2. Selezionare il pulsante "Settings" (impostazioni).
3. Selezionare "Reimposta posizione posizionata".

### <a name="my-steam-app-closed-unexpectedly"></a>L'app Steam è stata chiusa in modo imprevisto.

L'app Steam verrà chiusa se si blocca lo schermo del PC, si rimuove l'auricolare, si comportano gli utenti o se il PC passa alla modalità sospensione.


## <a name="speech-and-audio-problems"></a>Problemi di sintesi vocale e audio

### <a name="i-cant-hear-any-sound-in-my-headset-or-sound-is-playing-through-my-computer-instead-of-my-headset"></a>Non è possibile udire alcun suono nell'auricolare o suonare il computer al posto dell'auricolare.

* Se la cuffia a immersione non include cuffie predefinite, è necessario connettere le cuffie al jack audio dell'auricolare. Il Jack è spesso posizionato dietro o sotto la visiera o le lenti dell'auricolare. Se non è possibile trovarlo, rivolgersi al produttore dell'auricolare.
* Alcune cuffie audio dispongono di pulsanti fisici per controllare il volume. Se l'audio non funziona, controllare per verificare se il volume è disattivato o disattivato.
* La realtà mista di Windows è progettata per riprodurre suoni attraverso l'auricolare immersiva quando il portale per la realtà mista è in esecuzione e si dispone di cuffie connesse. Quando si disattiva l'auricolare o si capovolge la visiera, si chiude l'applicazione del portale per la realtà mista o quando tale app non è stata usata per 15 minuti, l'audio passa al dispositivo di riproduzione Windows predefinito. È possibile modificare questa impostazione in **impostazioni > realtà mista > audio e sintesi vocale.**
* Assicurarsi che la cuffia audio sia collegata completamente al jack audio. In particolare, è possibile che la cuffia Acer richieda una maggiore attenzione per garantire che la cuffia audio sia collegata a tutti i modi.
* Verificare che la cuffia audio/microfono sia collegata all'auricolare e non al PC.
* Il pannello di controllo audio di Windows Mostra solo gli endpoint audio abilitati, non gli endpoint disabilitati. Il dispositivo audio Headset verrà disabilitato quando non si indossa la cuffia, quindi è necessario fare clic con il pulsante destro del mouse nel pannello di controllo audio e scegliere "Mostra dispositivi disabilitati" per visualizzarlo; il nome del dispositivo è "Realtek USB 2.0 audio". Una volta eseguita questa operazione, è possibile modificare il nome nella pagina "Properties" con un elemento che verrà riconosciuto più facilmente. Questa operazione può essere eseguita sia per le schede di riproduzione che di registrazione.
* Se l'audio non funziona in app a realtà mista (ad esempio, Netflix), questo potrebbe essere causato da un problema noto in cui la realtà mista di Windows non viene aggiornata automaticamente in modo da corrispondere alla versione del sistema operativo. Per risolvere questo problema e ottenere la migliore esperienza di realtà mista, passare a **impostazioni > aggiorna & sicurezza > Windows Update > verificare la disponibilità di aggiornamenti** .

**Nota:** L'audio spaziale della realtà mista di Windows funziona meglio con le cuffie incorporate o connesse direttamente all'auricolare immersivo. Gli altoparlanti PC o le cuffie connesse al PC potrebbero non funzionare correttamente per l'audio spaziale.

**Nota:** La realtà mista di Windows non supporta le cuffie audio Bluetooth.

### <a name="im-experiencing-sudden-volume-changes-lost-audio-or-buzzing"></a>Si verificano modifiche improvvise del volume, audio perso o ronzio.

* Alcune applicazioni, incluse molte di quelle avviate tramite SteamVR, possono perdere audio o bloccarsi quando il dispositivo audio cambia quando si avvia o si arresta il portale di realtà mista. Riavviare l'app dopo aver aperto l'app del portale per la realtà mista per correggere questo problema.
* Se un altro dispositivo USB multimediale, ad esempio una web cam, condivide lo stesso hub USB interno o esterno con l'auricolare della realtà mista di Windows, le cuffie o i jack audio della cuffia potrebbero occasionalmente avere un segnale acustico o nessun audio. Collegare la cuffia a una porta USB che usa un hub diverso oppure disconnettere/disabilitare l'altro dispositivo multimediale USB.
* Se si nota un forte aumento del rumore dalle cuffie connesse alla cuffia, è possibile che l'hub USB del PC non sia in grado di fornire una potenza sufficiente per l'auricolare della realtà mista di Windows. Se si verifica questa situazione, archiviare immediatamente un bug dell' [Hub di feedback](https://docs.microsoft.com/hololens/hololens-feedback) . Soluzioni alternative che possono essere utili per includere la mancata utilizzo di cavi di estensione, l'utilizzo di un HUB USB 3,0 Basato su esterno, o l'utilizzo di una porta USB diversa nel PC.

### <a name="my-bluetooth-audio-headset-isnt-working-as-expected"></a>La cuffia audio Bluetooth non funziona come previsto.

Microsoft non consiglia l'uso di auricolari audio Bluetooth con la realtà mista di Windows. Le periferiche audio Bluetooth non funzionano bene con le esperienze audio e spaziali di Windows Mixed Reality e le cuffie audio Bluetooth non possono supportare l'input del microfono e l'output stereo allo stesso tempo, quindi non si riceveranno suoni stereo o spaziali quando si usa per gamechat o altro input vocale. Le cuffie audio Bluetooth possono anche influire negativamente sull'esperienza del controller di movimento. 

### <a name="sound-isnt-coming-from-expected-directions"></a>Il suono non è proveniente dalle direzioni previste.

La Home realtà mista di Windows include il suono spaziale (audio simile a quello che deriva dalle app situate nella Home Page). Man mano che ci si sposta e si passa da un'app all'altra, la direzione e il livello audio cambieranno ulteriormente in modo più realistico. Di seguito sono riportati alcuni motivi per le direzioni del suono impreviste: 
* Quando si apre e si riproduce musica da un'app musicale in grado di supportare in background (ad esempio Groove Music) nella Home page e si apre un'esperienza di VR immersiva (come un gioco), il suono dall'app Music passerà a dissolvenza da un suono spaziale a uno stereo. Potrebbe sembrare più forte di prima perché non vi è più alcuna distanza tra l'utente e il suono.
* Se Cortana è stato abilitato nel computer host prima di usare l'auricolare della realtà mista di Windows, è possibile perdere il suono spaziale applicato alle app nella Home realtà mista di Windows. Per risolvere il problema, disattivare l'opzione "Consenti a Cortana di rispondere a Hey Cortana" in **Settings > Cortana** sul desktop prima di avviare la realtà mista di Windows o abilitare "Windows Sonic per le cuffie" dall'interno della finestra dell'app desktop della Home realtà mista di Windows:
    1. Fare clic sull'icona dell'altoparlante sulla barra delle applicazioni del desktop e selezionarla nell'elenco dei dispositivi audio.
    2. Fare clic con il pulsante destro del mouse sull'icona dell'altoparlante sulla barra delle applicazioni del desktop e selezionare "Windows Sonic per le cuffie" nel menu "impostazione del relatore".
    3. Ripetere questi passaggi per tutti i dispositivi audio (endpoint).

### <a name="speech-commands-are-not-working-as-expected"></a>I comandi di sintesi vocale non funzionano come previsto.

* Per usare i comandi vocali, le impostazioni vocali e della lingua del PC devono essere impostate su una [lingua supportata in realtà mista di Windows](https://support.microsoft.com/en-us/help/4039262/windows-10-mixed-reality-setup-faq#Languages). Per verificare le impostazioni relative alla lingua e al linguaggio Windows, selezionare **impostazioni > ora & lingua > area & lingua** e **Impostazioni > lingua & lingua > voce** .
* Se la cuffia non ha un microfono incorporato, sarà necessario associare le cuffie con un microfono alla cuffia o al PC. Per fare in modo che l'input del microfono passa automaticamente all'auricolare quando lo si indossa, passare a **impostazioni > realtà mista > audio e vocale** e attivare "quando si indossa la cuffia, passare alla cuffia auricolare".
* Alcune cuffie audio hanno un pulsante fisico per disattivare e disattivare il microfono. Se i comandi di sintesi vocale non funzionano, verificare se il microfono è disattivato.
* Le cuffie audio con un microfono che penzola dal cavo dell'auricolare non vengono eseguite correttamente per i comandi vocali negli ambienti con rumore di ambiente.
* Cortana può essere lento la prima volta che viene richiamato in una sessione del portale per realtà mista. Passare a **impostazioni > Cortana > comunicare con Cortana** e assicurarsi che "Let Cortana Rispondi a Hey Cortana" sia abilitato.
* In alcuni PC, il guadagno predefinito di acquisizione voce per il microfono collegato all'auricolare può essere impostato su un valore troppo basso. Se si riscontrano comandi vocali o dettature non affidabili, è possibile provare a eseguire la risoluzione dei problemi di installazione del microfono. È possibile raggiungere questo strumento di risoluzione dei problemi tramite le **impostazioni > ora & lingua > voce** , quindi selezionare "inizia" nella sezione "microfono". Eseguire questa operazione tramite l'app desktop nella Home realtà mista di Windows, mantenendo la cuffia per influire sul microfono usato per la realtà mista di Windows. Selezionare l'endpoint appropriato nella procedura guidata per la risoluzione dei problemi.

### <a name="i-only-have-one-audio-headset-and-i-want-to-use-it-for-both-desktop-and-my-headset"></a>Ho una sola cuffia audio e voglio usarla sia per il desktop che per la cuffia.

Se è presente una sola cuffia audio e non è presente una cuffia con cuffie predefinite, connettere la cuffia audio al PC host anziché all'auricolare. Disattivare quindi "passa a audio cuffia" nelle impostazioni MRP.

### <a name="i-want-to-switch-to-dolby-atmos-for-headphones"></a>Desidero passare a Dolby Atmos per le cuffie.

Gli ambienti di realtà mista di Windows e le relative applicazioni utilizzano la tecnologia audio spaziale Windows Sonic per le cuffie, che è personalizzata per esperienze di realtà miste. È possibile applicare altre tecnologie audio spaziali, ad esempio Dolby Atmos per le cuffie, per applicazioni a schermo intero come SteamVR, ma non per le applicazioni e gli ambienti shell della realtà mista di Windows, ad esempio l'inserimento di un Web browser sul muro di Cliff House o Sky Loft, che sono stati progettati usando Windows Sonic per le cuffie audio e acustica spaziali.


## <a name="questions-about-desktop-in-mixed-reality"></a>Domande sul desktop in realtà mista

### <a name="how-do-i-access-my-pc-desktop-in-mixed-reality"></a>Ricerca per categorie accedere al desktop del PC in realtà mista?
È possibile accedere al desktop del PC in realtà mista usando l'app desktop. Per avviarlo, fare clic sul pulsante cuffia da **Windows > tutte le app > desktop** . 

### <a name="how-can-i-see-multiple-monitors-in-mixed-reality"></a>Come è possibile visualizzare più monitor in realtà mista?
Per impostazione predefinita, l'app desktop passa automaticamente a visualizzare il monitoraggio con lo stato attivo. Se si desidera visualizzare tutti i monitoraggi in realtà mista: 
* Fare clic sull'icona di monitoraggio nell'angolo superiore sinistro dell'app
* Disabilitare "cambia automaticamente il monitoraggio"
* Selezionare il monitoraggio che si desidera visualizzare
* Avviare un'altra istanza dell'app desktop
* Selezionare il monitoraggio che si desidera visualizzare in tale istanza 
* Ripeti per tutti i monitoraggi fisici si noti che sarà necessario riselezionare il monitoraggio da visualizzare in ogni app desktop ogni volta che si riavvia la realtà mista. 

### <a name="my-desktop-app-only-shows-a-black-screen"></a>My Desktop App Mostra solo una schermata nera.
Se il PC ha una GPU NVIDIA ibrida, il problema potrebbe essere causato dal dispositivo Nvidia che esegue il runtimebroker.exe sulla GPU discreta invece che su quello integrato. Per risolvere il problema, seguire queste istruzioni in "[ricerca per categorie creare le impostazioni Optimus per un nuovo programma?](http://nvidia.custhelp.com/app/answers/detail/a_id/2615/~/how-do-i-customize-optimus-profiles-and-settings%3F)" per aggiungere C:\windows\system32\runtimebroker.exe e forzarlo per l'esecuzione nel processore "Integrated graphics". 


## <a name="other-questions"></a>Altre domande

### <a name="my-samsung-odyssey-or-odyssey-headset-firmware-update-is-getting-stuck"></a>L'aggiornamento del firmware di Samsung Odyssey o Odyssey + headset si blocca.

Samsung è proprietario e pubblica gli aggiornamenti del firmware dell'auricolare forniti tramite le app complementari per dispositivi "Samsung HMD Odyssey Setup" e "Samsung HMD Odyssey + Setup". Per altri dettagli e per informazioni sui problemi di aggiornamento del firmware Samsung, contattare il servizio clienti Samsung.

Se il processo di aggiornamento del firmware si blocca e non è stato trovato alcun progresso per più di cinque minuti:
* Scollegare temporaneamente tutti gli altri dispositivi USB e riprovare a eseguire l'aggiornamento del firmware.
* Connettere la cuffia Samsung a una porta USB 3,0 diversa nel PC.
* Disabilitazione e/o disinstallazione di software installati che potrebbero interferire con gli aggiornamenti del firmware, ad esempio AORUS App Center di gigabyte.
* Usare un PC diverso per eseguire l'aggiornamento del firmware per la cuffia Samsung.

### <a name="my-wi-fi-slows-down-when-im-using-windows-mixed-reality"></a>Il Wi-Fi rallenta quando si usa la realtà mista di Windows.

Se si usa una connessione Wi-Fi a 2,4 GHz, i controller di movimento potrebbero rallentare la connessione Wi-Fi. Provare una delle operazioni seguenti:
* Passare a una connessione Wi-Fi 5GHz, se disponibile. [Altre informazioni](https://support.microsoft.com/en-us/help/4000461)
* Usare una scheda Bluetooth separata per connettere i controller di movimento al PC. Vedere [Adapter consigliati](https://support.microsoft.com/en-us/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines).

### <a name="i-got-a-message-that-said-to-plug-in-and-charge-my-pc-why"></a>Ho ricevuto un messaggio che dice di inserire e addebitare il mio PC. Perché?

Se si usa un computer portatile, la realtà mista di Windows funziona meglio quando il PC è completamente addebitato e collegato. 

### <a name="what-is-the-experience-options-setting"></a>Che cos'è l'impostazione opzioni esperienza?

L'impostazione opzioni esperienza ( **impostazioni > realtà mista > visualizzazione > opzioni esperienza** ) consente di modificare le impostazioni delle prestazioni della realtà mista di Windows. Questo consente di scegliere la migliore esperienza possibile per la configurazione hardware in un intervallo di contenuti. L'esperienza 90Hz è disponibile per tutti i sistemi, ma potrebbe essere necessario provare automaticamente a individuare l'impostazione preferita. Ecco le opzioni seguenti:
* Automatico: la realtà mista di Windows determina la migliore esperienza per la configurazione hardware. Per la maggior parte delle persone, questa è la scelta migliore per iniziare.
* 60Hz: imposta la frequenza di aggiornamento su 60Hz e disattiva determinate funzionalità, ad esempio acquisizione video e anteprima nel portale di realtà mista.
* 90Hz: imposta la frequenza di aggiornamento su 90Hz.

### <a name="what-languages-are-supported-in-windows-mixed-reality"></a>Quali lingue sono supportate in realtà mista di Windows?

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

La tastiera di Windows per la realtà mista è solo l'inglese (Stati Uniti). Per immettere testo in un'altra lingua, usare una tastiera fisica connessa al PC. È anche possibile usare la dettatura in uno dei linguaggi di realtà mista supportati di Windows elencati in precedenza. è sufficiente selezionare microfono sulla tastiera sullo schermo.

La realtà mista di Windows è disponibile anche nelle seguenti lingue senza comandi vocali o funzionalità di dettatura:

* Cinese tradizionale (Taiwan e Hong Kong)
* Olandese (Paesi Bassi)
* Coreano (Corea)
* Russo (Russia)

### <a name="i-have-questions-about-my-headset-hardware"></a>Ho domande sull'hardware dell'auricolare.

Per informazioni dettagliate sull'auricolare, rivolgersi al produttore. È possibile che sia presente una guida del prodotto nella casella oppure provare il sito Web del produttore.


## <a name="how-to-uninstall-windows-mixed-reality"></a>Come disinstallare la realtà mista di Windows

### <a name="how-do-i-uninstall-windows-mixed-reality"></a>Ricerca per categorie disinstallare la realtà mista di Windows?

1. Disconnettere l'auricolare dal PC.
2. Chiudere il portale di realtà mista.
2. Passare a  **avvia > impostazioni > realtà mista** e selezionare "Disinstalla".

Quando si è pronti per iniziare a usare nuovamente l'auricolare, collegarlo e il portale per la realtà mista consente di eseguire l'installazione.

### <a name="i-got-a-we-couldnt-finish-uninstalling-windows-mixed-reality-message"></a>Ho un messaggio "non è stato possibile completare la disinstallazione della realtà mista di Windows".

Questo significa che alcuni file, incluse le informazioni sull'ambiente, potrebbero essere ancora presenti nel computer. Questo può causare problemi se si decide di reinstallare la realtà mista di Windows in un secondo momento. È possibile rimuovere manualmente le altre informazioni sulla realtà mista di Windows dal PC modificando il registro di sistema e usando Windows PowerShell per eseguire i comandi. _Se si modifica il registro di sistema in modo non corretto, potrebbero verificarsi gravi problemi. Assicurarsi di seguire attentamente questi passaggi. Per una maggiore protezione, eseguire il backup del registro di sistema prima di modificarlo in modo che sia possibile ripristinarlo se si verifica un problema._ Per altre informazioni, vedere [How to backup and restory the Registry in Windows](https://support.microsoft.com/en-us/help/322756/how-to-back-up-and-restore-the-registry-in-windows). 

Per disinstallare la realtà mista di Windows usando i comandi seguenti:
1. Riavvia il PC.
2. Nella casella di **ricerca** Digitare "regedit" e quindi selezionare **Sì** .
3. Rimuovere i valori del registro di sistema seguenti:
   <ul>
    <li><b>HKEY_CURRENT_USER \software\microsoft\windows\currentversion\holographic</b>, quindi eliminare <b>FirstRunSucceeded</b>.</li> 
    <li><b>HKEY_CURRENT_USER \software\microsoft\windows\currentversion\holographic\speechandaudio</b>, quindi eliminare <b>PreferDesktopSpeaker</b> e <b>PreferDesktopMic</b>.</li> 
    <li><b>HKEY_CURRENT_USER \software\microsoft\ Speech_OneCore &gt; Settings\Holographic</b>, quindi eliminare <b>DisableSpeechInput</b>. Nota: gli elementi del registro di sistema in HHKEY_CURRENT_USER devono essere eliminati per ogni account utente nel computer che ha utilizzato la realtà mista di Windows.</li> 
    <li><b>HKEY_LOCAL_MACHINE \software\microsoft\windows\currentversion\perceptionsimulationextensions</b>, quindi eliminare <b>DeviceID</b> e <b>modalità</b>.</li> 
    <li><b>HKEY_CURRENT_USER \software\microsoft\windows\currentversion\holographic</b>, quindi eliminare <b>OnDeviceLearningCompleted</b>.</li> 
   </ul>
4. Rimuovere le chiavi del registro di sistema seguenti: <ul>
   <li> <b>HKEY_CURRENT_USER \Software\Microsoft\Windows\CurrentVersion\HoloSI</b></li> 
   <li> <b>HKEY_LOCAL_MACHINE \Software\Microsoft\Windows\CurrentVersion\HoloSI</b></li> 
   <li> <b>HKEY_CURRENT_USER \Software\Microsoft\ Speech_OneCore \Settings\HolographicPreferences</b></li><br/></ul>
5. Chiudere l'editor del registro di sistema.
6. Passare a **C:\Utenti\nome name\appdata\local\packages\ Microsoft.Windows.HolographicFirstRun_cw5n1h2txyewy \localstate** , quindi eliminare **RoomBounds.jssu** . Ripetere questa operazione per ogni utente che ha utilizzato la realtà mista di Windows.
7. Aprire prompt dei comandi di amministrazione e passare a **C:\ProgramData\WindowsHolographicDevices\SpatialStore\HoloLensSensors** . Eliminare quindi il contenuto della cartella di **dati HeadTracking** , ma non la cartella stessa.
8. Digitare "PowerShell" nella **casella di ricerca** , fare clic con il pulsante destro del mouse su **Windows PowerShell** e scegliere **Esegui come amministratore** .
9. In Windows PowerShell eseguire le operazioni seguenti: <ul>
   <li>Copiare e incollare quanto segue al prompt dei comandi, quindi premere INVIO: <b>DISM/online/Get-capabilities</b></li> 
   <li>Copiare l'identità della funzionalità che inizia con Analog. Olografic. desktop (se non è&#39;t, significa che l'elemento non è&#39;installato. In tal caso, andare al passaggio 10.</li> 
   <li>Copiare e incollare il prompt dei comandi seguente, quindi premere INVIO: <b>DISM/online/Remove-Capability/CapabilityName: identità funzionalità copiata nell'ultimo passaggio</b></li>
   </ul>
10. Riavviare il PC.





---
title: Note sulla versione - ottobre 2017
description: Rimanere aggiornati sulle note sulla versione Windows Mixed Reality per il Windows 10 Fall Creators Update (ottobre 2017).
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: note sulla versione, versione, Windows 10, build, rs3, os
ms.openlocfilehash: 09a33e1bc4a13c75e4c8a0ee250c7b67eb8e68e21220840037085e727acfb1f3
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115190595"
---
# <a name="release-notes---october-2017"></a>Note sulla versione - ottobre 2017

Benvenuti a Windows Mixed Reality! La **[Windows 10 Fall Creators Update](https://blogs.windows.com/windowsexperience/2017/10/17/whats-new-windows-10-fall-creators-update/)** introduce il supporto per i nuovi visori Windows Mixed Reality [immersive e](/windows/mixed-reality/discover/immersive-headset-hardware-details) i controller di [movimento.](/windows/mixed-reality/design/motion-controllers) È ora possibile esplorare nuovi mondi, riprodurre giochi VR e sperimentare l'intrattenimento immersivo quando si è connessi a un PC Windows Mixed Reality [con funzionalità .](./windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md)

La Windows Mixed Reality di visori e controller di movimento è il punto culminante di un impegno di gruppo enorme e di un importante passo avanti per la piattaforma [Windows Mixed Reality](/windows/mixed-reality/discover/mixed-reality), tra cui Microsoft HoloLens [.](/windows/mixed-reality/hololens-hardware-details) Anche HoloLens non riceve un aggiornamento con il Windows 10 Fall Creators Update, il lavoro HoloLens non è stato arrestato. Saranno molte le informazioni e le informazioni dettagliate da applicare dal lavoro recente nell'Windows Mixed Reality nel suo complesso. In realtà, Windows Mixed Reality visori immersivi e controller di movimento rappresentano un ottimo punto di ingresso per lo sviluppo anche per HoloLens, perché le stesse API, strumenti e concetti si applicano a entrambi.

Per eseguire l'aggiornamento alla versione più recente per ogni dispositivo, aprire l'app **Impostazioni,** passare **& Security** e quindi selezionare il pulsante Controlla **aggiornamenti.** In un PC Windows 10, è anche possibile installare manualmente il Windows 10 Fall Creators Update usando lo Windows [di creazione di supporti.](https://www.microsoft.com/software-download/windows10)

 **Versione più recente per Desktop:** Windows 10 Desktop di ottobre 2017 (**10.0.16299.15**, Windows 10 Fall Creators Update)<br>
 **Versione più recente per HoloLens:** [Windows 10 Holographic agosto 2016](release-notes-august-2016.md) (**10.0.14393.0**, Windows 10 Aggiornamento dell'anniversario)

>[!VIDEO https://www.youtube.com/embed/YBcLy1lkegg]

## <a name="introducing-windows-mixed-reality"></a>Introduzione a Windows Mixed Reality

Il Windows 10 Fall Creators Update introduce ufficialmente il supporto per Windows Mixed Reality visori e controller di movimento e Windows 10 il primo sistema operativo spaziale al mondo. Ecco le novità:
* **[Varietà di visori:](https://blogs.windows.com/windowsexperience/2017/10/03/how-to-pre-order-your-windows-mixed-reality-headset/)** Windows Mixed Reality i partner possono offrire diversi tipi di visori a partire da $ 399 USD in bundle con controller di movimento.
* **[Controller di](/windows/mixed-reality/design/motion-controllers)** movimento: Windows Mixed Reality controller di movimento in modalità wireless si associano al PC tramite Bluetooth e offrono sei gradi di libertà di rilevamento, molti metodi di input e IME.
* **[Facile configurazione e portabilità:](./recommended-adapters-for-windows-mixed-reality-capable-pcs.md)** configurare e iniziare in meno di 10 minuti. I visori immersivi usano il rilevamento interno per tenere traccia del movimento e dei controller di movimento, con sei gradi di libertà. Non sono necessari marcatori esterni per fotocamere o fari.
* **[](./windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md)** Supporto per una gamma più ampia di PC: Windows Mixed Reality consentirà a più persone di sperimentare la realtà virtuale desktop che mai, con il supporto per schede grafiche e PC integrati selezionati a partire da $ 499 USD.
* **[Windows Mixed Reality casa:](/windows/mixed-reality/discover/navigating-the-windows-mixed-reality-home)** il primo sistema operativo spaziale al mondo offre un ambiente familiare per l'esecuzione di più attività con app 2D, l'avvio di giochi e app VR e l'inserimento di ologrammi decorativi.
* App e giochi VR straordinari nel **[Microsoft Store:](https://www.microsoft.com/store/collections/MR-All-ImmersiveContent/)** dall'intrattenimento immersivo come Hulu VR e video a 360 a giochi epici come SUPERHOT VR e Arizona Sunshine, il Microsoft Store ha una gamma di contenuti da sperimentare in Windows Mixed Reality.
* Accesso anticipato di **[SteamVR:](./using-steamvr-with-windows-mixed-reality.md)** Windows 10 Fall Creators Update consente di riprodurre i titoli di SteamVR con visori e controller Windows Mixed Reality, rendendo disponibile il catalogo più grande di titoli VR Windows Mixed Reality utenti.

## <a name="known-issues"></a>Problemi noti

Abbiamo lavorato sodo per offrire un'esperienza Windows Mixed Reality, ma stiamo ancora verificando alcuni problemi noti. Se si trovano altri utenti, [inviare commenti e suggerimenti.](/windows/mixed-reality/give-us-feedback)

### <a name="desktop-app-in-the-windows-mixed-reality-home"></a>App desktop nella Windows Mixed Reality principale
* Strumento di cattura non funziona nell'app desktop.
* L'app desktop non mantiene l'impostazione al riavvio.
* Se si usa l'anteprima Portale realtà mista desktop, quando si apre l'app Desktop nella home Windows Mixed Reality, è possibile notare l'effetto mirror infinito. 
* L'esecuzione dell'app Desktop può causare problemi di prestazioni nei PC Windows Mixed Reality Ultra. non è consigliabile.  
* L'app desktop può essere avviata automaticamente perché una finestra invisibile sul desktop ha lo stato attivo. 
* La richiesta di controllo dell'account utente desktop farà visualizzare il visore nero fino al completamento della richiesta.

### <a name="windows-mixed-reality-setup"></a>Windows Mixed Reality configurazione
* Quando si configura un Windows con un visore connesso, il monitor del PC potrebbe essere vuoto. Scollegare il visore per abilitare l'output nel monitor del PC per completare Windows configurazione.
* Quando si crea un limite, la traccia potrebbe non riuscire. In tal caso, riprovare, perché il sistema apprenderà di più sullo spazio nel tempo.
* Se si attiva o Cortana durante la configurazione Windows Mixed Reality, questa modifica verrà applicata alle impostazioni Cortana desktop.
* Se le cuffia non sono connesse, è possibile che i suggerimenti per la prima volta non siano Windows Mixed Reality home.
* Bluetooth le cuffia possono causare interferenze con i controller di movimento. È consigliabile annullare o disattivare i controller Bluetooth durante Windows Mixed Reality sessioni.

### <a name="games-and-apps-from-windows-store"></a>Giochi e app da Windows Store
* Alcuni giochi a elevato utilizzo grafico, ad esempio Forza Motorsports 6, possono causare problemi di prestazioni nei PC meno idonei quando vengono riprodotti all'interno Windows Mixed Reality.

### <a name="audio"></a>Audio
* Come indicato in precedenza, Bluetooth periferiche audio non funzionano correttamente con le Windows Mixed Reality voce e con le esperienze sonore spaziali. Possono anche influire negativamente sull'esperienza del controller di movimento. Non è consigliabile usare Bluetooth visori audio con Windows Mixed Reality.
* Non è possibile usare il dispositivo audio connesso (o parte di) al visore per la riproduzione audio quando il dispositivo non viene indossato. Se si ha un solo visore audio, è possibile connettere il visore audio al PC host anziché al visore. In tal caso, è necessario disattivare "Passa all'audio del visore" **in** Impostazioni  >    >  **audio e voce di realtà mista.**
* Alcune applicazioni, incluse molte di quelle avviate tramite SteamVR, possono perdere l'audio o bloccarsi quando il dispositivo audio cambia all'avvio o all'arresto del Portale realtà mista. Riavviare l'app dopo aver aperto l'app Portale realtà mista per risolvere il problema.
* Se Cortana è abilitato nel PC host prima di usare il visore Windows Mixed Reality, è possibile che la simulazione del suono spaziale applicata alle app posizionate intorno alla Windows Mixed Reality home. Il problema è abilitare "Windows Sonic per cuffie" in tutti i dispositivi audio collegati al PC, anche nel dispositivo audio connesso con visore:
   1. Fare clic con il pulsante sinistro del mouse sull'icona del parlante sulla barra delle applicazioni del desktop e selezionare dall'elenco dei dispositivi audio.
   2. Fare clic con il pulsante destro del mouse sull'icona del parlante sulla barra delle applicazioni del desktop e scegliere "Windows Sonic per cuffie" nel menu "Configurazione del parlante".
   3. Ripetere questi passaggi per tutti i dispositivi audio (endpoint).
>[!NOTE]
> - Poiché le cuffia/altoparlanti connessi al visore non vengono visualizzate a meno che non vengano indossate, è necessario eseguire questa operazione dalla finestra dell'app Desktop nella home page di Windows Mixed Reality per applicare questa impostazione al dispositivo audio connesso al visore o integrato nel visore.
> - Un'altra opzione è disattivare "Consenti Cortana rispondere a Hey Cortana" **in** Impostazioni Cortana sul desktop prima di avviare  >   Windows Mixed Reality.

* Quando un altro dispositivo USB multimediale (ad esempio una web cam) condivide lo stesso hub USB (esterno o all'interno del PC) con il visore Windows Mixed Reality, in rari casi il jack/cuffia audio del visore può avere un suono ronzante o nessun audio. È possibile risolvere il problema con il visore in una porta USB che non condivide lo stesso hub dell'altro dispositivo o disconnettere/disabilitare l'altro dispositivo multimediale USB.
* In rari casi, l'hub USB del PC host non è in grado di fornire potenza sufficiente al visore Windows Mixed Reality e si potrebbe notare un rumore delle cuffia connesse al visore.

### <a name="speech"></a>Voce
* Cortana possibile che non riesca a riprodurre i segnali audio per l'ascolto/il modo di pensare e le risposte audio ai comandi.
* Cortana nei mercati Cina e Giappone non viene visualizzato correttamente il testo sotto il cerchio Cortana durante l'uso.
* Cortana può essere lenta la prima volta che viene richiamata in una Portale realtà mista sessione. È possibile risolvere questo problema assicurando che "Consenti Cortana di rispondere a Hey Cortana" in Impostazioni  >  **Cortana**  >  **Talk to Cortana** sia abilitato.
* Cortana l'esecuzione potrebbe risultare più lenta nei PC che non sono Windows Mixed Reality Ultra PC.
* Quando la tastiera di sistema è impostata su una lingua diversa dalla lingua dell'interfaccia utente in Windows Mixed Reality, l'uso della dettatura della tastiera in Windows Mixed Reality comporta la visualizzazione di una finestra di dialogo di errore per il fatto che la dettatura non funziona a causa della Wi-Fi connessione. Per risolvere il problema, assicurarsi che la lingua della tastiera di sistema corrisponda alla lingua dell'Windows Mixed Reality dell'interfaccia utente.
* La Spagna non viene riconosciuta correttamente come un mercato in cui la voce è abilitata per Windows Mixed Reality.

### <a name="holograms"></a>Holograms (Ologrammi)
* Se è stato inserito un numero elevato di ologrammi nella casa Windows Mixed Reality, alcuni potrebbero scomparire e riapparire mentre ci si guarda intorno. Per evitare questo problema, rimuovere alcuni ologrammi nell'area del Windows Mixed Reality home.

### <a name="motion-controllers"></a>Controller del movimento
* In alcuni casi, se si seleziona una pagina Web in Edge, il contenuto verrà ingrandito anziché fare clic.
* A volte, quando si seleziona un collegamento in Edge, la selezione non funzionerà.

## <a name="prior-release-notes"></a>Note sulla versione precedente
* [Note sulla versione - agosto 2016](release-notes-august-2016.md)
* [Note sulla versione - maggio 2016](release-notes-may-2016.md)
* [Note sulla versione - marzo 2016](release-notes-march-2016.md)

## <a name="see-also"></a>Vedi anche
* [Supporto visore immersivo (collegamento esterno)](./troubleshooting-windows-mixed-reality.md)
* [Problemi noti di HoloLens](/windows/mixed-reality/hololens-known-issues)
* [Installare gli strumenti](/windows/mixed-reality/develop/install-the-tools)
* [Commenti e suggerimenti](/windows/mixed-reality/give-us-feedback)
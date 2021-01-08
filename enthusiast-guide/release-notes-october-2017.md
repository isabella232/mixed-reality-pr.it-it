---
title: Note sulla versione - ottobre 2017
description: È possibile rimanere sempre aggiornati sulle note sulla versione della realtà mista di Windows per Windows 10 Fall Creators Update (ottobre 2017).
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: Note sulla versione, versione, Windows 10, Build, RS3, sistema operativo
ms.openlocfilehash: 83c16a40388960547cfcf7444e1ae630c2f5b7f2
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2021
ms.locfileid: "98009491"
---
# <a name="release-notes---october-2017"></a>Note sulla versione - ottobre 2017

Benvenuti in Windows Mixed Reality La versione di **[Windows 10 Fall Creators Update](https://blogs.windows.com/windowsexperience/2017/10/17/whats-new-windows-10-fall-creators-update/)** introduce il supporto per i nuovi auricolari e i controller di [movimento](https://docs.microsoft.com/windows/mixed-reality/design/motion-controllers)con la [realtà mista di Windows](https://docs.microsoft.com/windows/mixed-reality/discover/immersive-headset-hardware-details) . È ora possibile esplorare i nuovi mondi, riprodurre giochi VR e sperimentare animazioni immersive quando si è connessi a un PC con supporto per la [realtà mista di Windows](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines).

Il rilascio di auricolari per la realtà mista di Windows e dei controller di movimento è il punto culminale di un enorme impegno del team e un importante passo avanti per la [piattaforma di realtà mista di Windows](https://docs.microsoft.com/windows/mixed-reality/discover/mixed-reality), tra cui [Microsoft HoloLens](https://docs.microsoft.com/windows/mixed-reality/hololens-hardware-details). Mentre HoloLens non riceve un aggiornamento con Windows 10 Fall Creators Update, il lavoro in HoloLens non è stato interrotto. Verranno fornite numerose informazioni e informazioni dettagliate da applicare al nostro lavoro recente nell'ambito della realtà mista di Windows. Infatti, gli auricolari e i controller di movimento di realtà mista di Windows rappresentano un ottimo punto di ingresso allo sviluppo anche per HoloLens, in quanto le stesse API, gli strumenti e i concetti si applicano a entrambi.

Per eseguire l'aggiornamento alla versione più recente per ogni dispositivo, aprire l'app **Impostazioni** , passare a **Aggiorna & sicurezza**, quindi selezionare il pulsante **Controlla aggiornamenti** . In un PC Windows 10, è anche possibile installare manualmente Windows 10 Fall Creators Update usando lo strumento di [creazione di Windows Media](https://www.microsoft.com/software-download/windows10).

 **Versione più recente per desktop:** Windows 10 desktop ottobre 2017 (**10.0.16299.15**, Windows 10 Fall Creators Update)<br>
 **Versione più recente per HoloLens:** [Windows 10 olografico agosto 2016](release-notes-august-2016.md) (**10.0.14393.0**, aggiornamento dell'anniversario di Windows 10)

>[!VIDEO https://www.youtube.com/embed/YBcLy1lkegg]

## <a name="introducing-windows-mixed-reality"></a>Introduzione alla realtà mista di Windows

Windows 10 Fall Creators Update introduce ufficialmente il supporto per gli auricolari per la realtà mista di Windows e i controller di movimento e rende Windows 10 il primo sistema operativo spaziale del mondo. Ecco le novità:
* **[Varietà di auricolari](https://blogs.windows.com/windowsexperience/2017/10/03/how-to-pre-order-your-windows-mixed-reality-headset/)** : la realtà mista di Windows consente ai partner di offrire diversi tipi di auricolari a partire da $399 USD in bundle con i controller di movimento.
* **[Controller di movimento](https://docs.microsoft.com/windows/mixed-reality/design/motion-controllers)** : i controller di movimento per la realtà mista di Windows sono abbinati in modalità wireless al PC tramite Bluetooth e sono caratterizzati da sei gradi di rilevamento della libertà, molti metodi di input e IMUs.
* **[Facile installazione e portabilità](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs)** : configurazione e introduzione in meno di 10 minuti. Gli auricolari immersivi usano il rilevamento interno per tenere traccia del movimento e dei controller di movimento, con sei gradi di libertà. Non sono richieste fotocamere esterne o marcatori Faro.
* **[Supporto per una gamma più ampia di PC: la](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)** realtà mista di Windows consentirà a un maggior numero di utenti di sperimentare Desktop VR, con il supporto per schede grafiche e PC integrati a partire da $499 USD.
* **[Home realtà mista di Windows](https://docs.microsoft.com/windows/mixed-reality/discover/navigating-the-windows-mixed-reality-home)** : il primo sistema operativo spaziale del mondo offre un ambiente domestico familiare per il multitasking con app 2D, l'avvio di giochi e app VR e l'inserimento di ologrammi decorativi.
* **[Giochi e app VR straordinarie nell'Microsoft Store](https://www.microsoft.com/store/collections/MR-All-ImmersiveContent/)** , da intrattenimento immersivo come Hulu vr e 360 video a Epic Games come SUPERHOT VR e Arizona Sunshine, il Microsoft Store offre una gamma di contenuti da sperimentare nella realtà mista di Windows.
* **[Accesso anticipato a SteamVR](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/using-steamvr-with-windows-mixed-reality)** : Windows 10 Fall Creators Update consente il supporto dei titoli SteamVR con le cuffie e i controller di realtà mista di Windows, rendendo disponibile il catalogo più grande di titoli VR per gli utenti di realtà mista di Windows.

## <a name="known-issues"></a>Problemi noti

Abbiamo lavorato duramente per offrire un'eccezionale esperienza di realtà mista di Windows, ma stiamo ancora verificando alcuni problemi noti. Se ne trovate altre, [inviaci commenti](https://docs.microsoft.com/windows/mixed-reality/give-us-feedback).

### <a name="desktop-app-in-the-windows-mixed-reality-home"></a>App desktop nella Home realtà mista di Windows
* Lo strumento di cattura non funziona nell'app desktop.
* L'app desktop non mantiene l'impostazione al rilancio.
* Se si usa l'anteprima del portale di realtà mista sul desktop, quando si apre l'app desktop nella Home realtà mista di Windows, è possibile notare l'effetto di mirror infinito. 
* L'esecuzione dell'applicazione desktop può causare problemi di prestazioni in PC con una realtà mista Windows non ultra-ultra; non è consigliabile.  
* L'app desktop può essere avviata automaticamente perché una finestra invisibile sul desktop ha lo stato attivo. 
* La richiesta di controllo dell'account utente desktop renderà la visualizzazione della cuffia nera fino al completamento della richiesta.

### <a name="windows-mixed-reality-setup"></a>Configurazione della realtà mista di Windows
* Quando si configura Windows con una cuffia connessa, il monitor del PC potrebbe essere vuoto. Scollegare la cuffia per abilitare l'output del monitor PC per completare l'installazione di Windows.
* Quando si crea un limite, la traccia potrebbe non riuscire. In tal caso, riprovare, perché il sistema apprenderà altre informazioni sullo spazio nel tempo.
* Se si attiva o disattiva Cortana durante la configurazione della realtà mista di Windows, questa modifica verrà applicata alle impostazioni del Cortana desktop.
* Se non si dispone di cuffie connesse, è possibile che si verifichino suggerimenti quando si visita la prima volta la Home realtà mista di Windows.
* Le cuffie Bluetooth possono causare interferenze con i controller di movimento. Si consiglia di disaccoppiare o spegnere i controller Bluetooth durante le sessioni di realtà mista di Windows.

### <a name="games-and-apps-from-windows-store"></a>Giochi e app di Windows Store
* Alcuni giochi a elevato utilizzo di grafica, ad esempio forza Motorsports 6, possono causare problemi di prestazioni nei PC meno idonei quando vengono riprodotti in realtà mista di Windows.

### <a name="audio"></a>Audio
* Come indicato in precedenza, le periferiche audio Bluetooth non funzionano correttamente con la voce di realtà mista di Windows e le esperienze audio spaziali. Possono anche influire negativamente sull'esperienza del controller di movimento. Non è consigliabile usare cuffie audio Bluetooth con la realtà mista di Windows.
* Non è possibile usare il dispositivo audio connesso o parte della cuffia per la riproduzione audio quando il dispositivo non viene usato. Se è presente una sola cuffia audio, potrebbe essere necessario connettere la cuffia audio al PC host anziché all'auricolare. In tal caso, è necessario disattivare l'opzione "passa a audio cuffia" in **Impostazioni**  >    >  **audio e sintesi vocale** della realtà mista.
* Alcune applicazioni, incluse molte di quelle avviate tramite SteamVR, possono perdere audio o bloccarsi quando il dispositivo audio cambia quando si avvia o si arresta il portale di realtà mista. Riavviare l'app dopo aver aperto l'app del portale per la realtà mista per correggere questo problema.
* Se la Cortana è abilitata nel computer host prima di usare l'auricolare della realtà mista di Windows, è possibile perdere la simulazione del suono spaziale applicata alle app posizionate intorno alla Home realtà mista di Windows. Per risolvere il sistema, è necessario abilitare "Windows Sonic per le cuffie" in tutti i dispositivi audio collegati al PC, anche il dispositivo audio connesso all'auricolare:
   1. Fare clic sull'icona dell'altoparlante sulla barra delle applicazioni del desktop e selezionare da un elenco di dispositivi audio.
   2. Fare clic con il pulsante destro del mouse sull'icona dell'altoparlante sulla barra delle applicazioni del desktop e selezionare "Windows Sonic per le cuffie" nel menu "impostazione del relatore".
   3. Ripetere questi passaggi per tutti i dispositivi audio (endpoint).
>[!NOTE]
> - Poiché le cuffie/altoparlanti connessi all'auricolare non vengono visualizzati a meno che non lo si usi, è necessario eseguire questa operazione dall'interno della finestra dell'app desktop nella Home realtà mista di Windows per applicare questa impostazione al dispositivo audio connesso all'auricolare (o integrato nell'auricolare).
> - Un'altra opzione consiste nel disattivare "Let Cortana rispondere a Hey Cortana" in **Settings**  >  **Cortana** on the desktop prima di avviare la realtà mista di Windows.

* Quando un altro dispositivo USB multimediale (ad esempio una Web Cam) condivide lo stesso hub USB (esterno o all'interno del PC) con l'auricolare della realtà mista di Windows, in rari casi è possibile che lo spinotto/le cuffie audio dell'auricolare abbia un segnale acustico o nessun audio. È possibile risolvere il problema tramite la cuffia in una porta USB che non condivide lo stesso hub dell'altro dispositivo o disconnettere/disabilitare l'altro dispositivo multimediale USB.
* In rari casi, l'hub USB del PC host non è in grado di fornire una potenza sufficiente per l'auricolare della realtà mista di Windows e potrebbe verificarsi un aumento del rumore dalle cuffie connesse all'auricolare.

### <a name="speech"></a>Voce
* Cortana potrebbe non riuscire a riprodurre i propri suggerimenti audio per le risposte in ascolto/pensiero e audio ai comandi.
* Cortana nei mercati Cina e Giappone non Mostra correttamente il testo sotto il cerchio Cortana durante l'uso.
* Cortana può essere lento la prima volta che viene richiamato in una sessione del portale per realtà mista. È possibile ovviare a questo problema assicurandosi che "Let Cortana rispondere a Hey Cortana" in **Settings**  >  **Cortana**  >  **Talk to Cortana** is enabled.
* Cortana può essere eseguito più lentamente nei PC che non sono Windows Mixed Reality Ultra PC.
* Quando la tastiera di sistema è impostata su una lingua diversa dalla lingua dell'interfaccia utente in ambiente misto Windows, l'utilizzo della dettatura dalla tastiera in realtà mista di Windows provocherà una finestra di dialogo di errore sulla dettatura non funzionante a causa della mancata connessione Wi-Fi. Per risolvere il problema, assicurarsi che la lingua della tastiera di sistema corrisponda al linguaggio di interfaccia utente della realtà mista di Windows.
* La Spagna non viene riconosciuta correttamente come mercato in cui è abilitato il riconoscimento vocale per la realtà mista di Windows.

### <a name="holograms"></a>Holograms (Ologrammi)
* Se è stato inserito un numero elevato di ologrammi nella Home page della realtà mista di Windows, alcuni possono scomparire e riapparire durante l'aspetto. Per evitare questo problema, rimuovere alcuni degli ologrammi in quell'area della Home realtà mista di Windows.

### <a name="motion-controllers"></a>Controller del movimento
* In alcuni casi, se si seleziona una pagina Web in Edge, il contenuto viene ingrandito anziché fare clic su.
* In alcuni casi, quando si seleziona un collegamento in Edge, la selezione non funzionerà.

## <a name="prior-release-notes"></a>Note sulla versione precedente
* [Note sulla versione - agosto 2016](release-notes-august-2016.md)
* [Note sulla versione - maggio 2016](release-notes-may-2016.md)
* [Note sulla versione - marzo 2016](release-notes-march-2016.md)

## <a name="see-also"></a>Vedere anche
* [Supporto per cuffie immersive (collegamento esterno)](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality)
* [Problemi noti di HoloLens](https://docs.microsoft.com/windows/mixed-reality/hololens-known-issues)
* [Installare gli strumenti](https://docs.microsoft.com/windows/mixed-reality/develop/install-the-tools)
* [Commenti e suggerimenti](https://docs.microsoft.com/windows/mixed-reality/give-us-feedback)

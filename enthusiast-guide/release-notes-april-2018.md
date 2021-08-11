---
title: Note sulla versione - Aprile 2018
description: Aggiornamento di aprile 2018/RS4 per HoloLens Windows 10 e Windows Mixed Reality sulla versione di aggiornamento di aprile 2018/RS4.
author: mattzmsft
ms.author: mazeller
ms.date: 05/21/2018
ms.topic: article
keywords: note sulla versione, versione, Windows 10, build, rs4, os
ms.openlocfilehash: 27f80d659c63362191a80eeae973111ca342090901c243772868d1a7c11e24d3
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115202433"
---
# <a name="release-notes---april-2018"></a>Note sulla versione - Aprile 2018

L Windows 10 update di **[aprile 2018](https://blogs.windows.com/windowsexperience/2018/04/30/whats-new-in-the-windows-10-april-2018-update)** (noto anche come RS4) include nuove funzionalità per HoloLens e Windows Mixed Reality visori immersivi connessi ai PC. 

Per eseguire l'aggiornamento alla versione più recente per entrambi i tipi di dispositivo, aprire l'app **Impostazioni,** passare **& Security** e quindi selezionare il pulsante Controlla **aggiornamenti.** In un PC Windows 10, è anche possibile installare manualmente l'aggiornamento Windows 10 aprile 2018 usando lo Windows [di creazione di supporti.](https://www.microsoft.com/software-download/windows10)

**Versione più recente per Desktop: Windows 10** aggiornamento di aprile 2018 (**10.0.17134.1**)<br>
**Versione più recente per HoloLens:** Windows 10 aggiornamento di aprile 2018 (**10.0.17134.80**)<br>
<br>

>[!VIDEO https://www.youtube.com/embed/O-84oWjSbr0]

*Messaggio di Alex Kipman e panoramica delle nuove funzionalità di realtà mista nell'aggiornamento Windows 10 aprile 2018*

## <a name="new-features-for-windows-mixed-reality-immersive-headsets"></a>Nuove funzionalità per i visori Windows Mixed Reality immersive

L Windows 10'aggiornamento di aprile 2018 include molti miglioramenti per l'uso di visori vr Windows Mixed Reality immersive con il PC desktop, ad esempio: 

* **Nuovi ambienti per il ambiente iniziale:** scegliere tra il Casa sulla scogliera e il nuovo  ambiente Skyloft selezionando Luoghi nel menu Start. È stata aggiunta anche [una funzionalità sperimentale](/windows/mixed-reality/design/add-custom-home-environments) che consente di usare ambienti personalizzati creati.
* **Accesso rapido l'acquisizione** di realtà mista: scattare foto di realtà mista usando un controller di movimento in ambienti e app, ma non acquisisce contenuto protetto con DRM. Tenere premuto Windows pulsante e quindi toccare il trigger. .
* **Nuove opzioni per l'avvio** e il ridimensionamento del contenuto: le app vengono ora posizionate automaticamente davanti all'utente quando vengono avviate dal menu Start. È anche possibile ridimensionare le app 2D trascinando i bordi e gli angoli della finestra.
* **Passare** facilmente al contenuto con il comando vocale "teletrasporto": si teletrasporta rapidamente davanti al contenuto nella home Windows Mixed Reality guardando il contenuto e pronunciando "teletrasporto".
* **[Utilità di avvio di app 3D animate](/windows/mixed-reality/distribute/creating-3d-models-for-use-in-the-windows-mixed-reality-home#animation-guidelines) e [oggetti decorativi 3D](/windows/mixed-reality/distribute/enable-placement-of-3d-models-in-the-home) per ambiente iniziale**. È ora possibile aggiungere animazione alle utilità di avvio delle app 3D e consentire agli utenti di posizionare modelli 3D decorativi da una pagina Web o un'app 2D nella home page Windows Mixed Reality 2D.
* Miglioramenti al **[Windows Mixed Reality per SteamVR:](/windows/mixed-reality/develop/porting-apps/updating-your-steamvr-application-for-windows-mixed-reality)** Windows Mixed Reality per SteamVR non è "accesso anticipato" con nuovi aggiornamenti, tra cui: feedback aptico quando si usano controller di movimento, prestazioni e affidabilità migliorate e miglioramenti all'aspetto dei controller di movimento in SteamVR.
* **Altri miglioramenti:** le impostazioni delle prestazioni automatiche aggiornate offrono un'esperienza più ottimizzata (è possibile eseguire manualmente [l'override](#visual-quality) di questa impostazione). Il programma di installazione fornisce ora informazioni più dettagliate sui problemi di compatibilità comuni con i controller USB 3.0 e le schede grafiche.

## <a name="new-features-for-hololens"></a>Nuove funzionalità per HoloLens

È Windows 10'aggiornamento di aprile 2018 per tutti HoloLens clienti. Questo aggiornamento è ricco di miglioramenti introdotti dopo l'ultima versione principale HoloLens software nell'agosto [2016.](release-notes-august-2016.md)

### <a name="for-everyone"></a>Per tutti

<table>
  <tr>
    <th>Funzionalità</th><th>Dettagli</th><th>Istruzioni</th>
  </tr>
  <tr>
    <td>Posizionamento automatico del contenuto 2D e 3D all'avvio</td><td>Un'icona di avvio di app 2D o un'app UWP 2D posiziona automaticamente nel mondo dimensioni e distanza ottimali quando viene avviata anziché richiedere all'utente di posizionarla. Se <a href="/windows/mixed-reality/design/app-views">un'app</a> immersiva usa un'icona di avvio di app 2D anziché un'icona di avvio di app <a href="/windows/mixed-reality/distribute/3d-app-launcher-design-guidance">3D,</a>l'app immersiva verrà avviata automaticamente dall'icona di avvio delle app 2D come in RS1.<br><br>Un'icona di avvio di app 3D menu Start anche le posizioni automaticamente nel mondo. Invece di avviare automaticamente l'app, gli utenti possono quindi fare clic sull'utilità di avvio per avviare l'app immersiva. Anche il contenuto 3D aperto dall'app Ologrammi e da Edge si inserisce automaticamente nel mondo.</td><td>Quando si apre un'app dal menu Start, non verrà chiesto di posizionarla nel mondo.<br><br>Se il posizionamento dell'icona di avvio di app<a href="/windows/mixed-reality/distribute/3d-app-launcher-design-guidance">2D/3D</a> non è ottimale, è possibile spostarli facilmente usando nuove modifiche fluide delle app descritte di seguito. È anche possibile riposizionare il contenuto 2D app launcher/3D pronunciando "Sposta" e quindi usando lo sguardo fisso per riposizionare il contenuto.</td>
  </tr>
  <tr>
    <td>Manipolazione fluida delle app</td><td>Spostare, ridimensionare e ruotare il contenuto 2D e 3D senza dover passare alla modalità "Regola".</td><td>Per spostare un'app UWP 2D o un'icona di avvio di app 2D, è sufficiente osservare la barra dell'app e quindi usare il tocco + tenere premuto e trascinare il movimento. È possibile spostare il contenuto 3D guardando in qualsiasi punto dell'oggetto e quindi toccando + tieni premuto e trascina.<br><br>Per ridimensionare il contenuto 2D, osservare l'angolo. Il cursore dello sguardo fisso si trasforma in un cursore di ridimensionamento e quindi è possibile toccare + tenere premuto e trascinare per ridimensionare. È anche possibile rendere il contenuto 2D più alto o più ampio osservandone i bordi e trascinandolo.<br><br>Per ridimensionare il contenuto 3D, alzare entrambe le mani nella cornice del movimento, alzando le dita nella posizione pronta. Il cursore si trasforma in uno stato con 2 piccole mani. Toccare e tenere premuto con entrambe le mani. Spostando le mani più vicine o più distanti, le dimensioni dell'oggetto cambiano. Spostando le mani avanti e indietro in relazione tra loro, l'oggetto verrà ruotato. È anche possibile ridimensionare/ruotare il contenuto 2D in questo modo.</td>
  </tr>
  <tr>
    <td>Ridimensionamento orizzontale dell'app 2D con ridisposizione</td><td>Rendere un'app UWP 2D più ampia in proporzioni per visualizzare più contenuto dell'app. Ad esempio, la larghezza dell'app Mail è sufficiente per visualizzare il riquadro di anteprima.</td><td>È sufficiente osservare il bordo sinistro o destro dell'app UWP 2D per visualizzare il cursore di ridimensionamento, quindi usare il tocco + tenere premuto e trascinare il movimento per ridimensionare.</td>
  </tr>
  <tr>
    <td>Supporto dei comandi vocali espansi</td><td>È possibile fare di più semplicemente usando la voce.</td><td>Provare questi comandi vocali:<ul><li>"Vai a Start" - Apre il menu Start o esce da <a href="/windows/mixed-reality/design/app-views">un'app immersiva.</a></li><li>"Sposta" - Consente di spostare un oggetto.</li></ul></td>
  </tr>
  <tr>
    <td>Aggiornamento Ologrammi e Foto app</td><td>Aggiornamento Ologrammi'app con nuovi ologrammi. Aggiornamento dell Foto app.</td><td>Si noterà un aspetto aggiornato delle app Ologrammi e Foto app. L Ologrammi app include diverse nuove Ologrammi e un'etichettatrice per semplificare la creazione del testo.</td>
  </tr>
  <tr>
    <td>Acquisizione di realtà mista migliorata</td><td>Video MRC iniziale e finale del collegamento hardware.</td><td>Tenere premuto Volume Su e Giù per 3 secondi per avviare la registrazione del video MRC. Toccare di nuovo entrambi o usare il movimento bloom per terminare.</td>
  </tr>
  <tr>
    <td>Spazi consolidati</td><td>Semplificare la gestione dello spazio per gli ologrammi in un unico spazio.</td><td>HoloLens trova automaticamente lo spazio e non richiede più la gestione o la selezione degli spazi. Se si verificano problemi con gli ologrammi, è possibile passare a Impostazioni > <b>sistema > Ologrammi > rimuovere gli ologrammi vicini.</b> Se necessario, è anche possibile selezionare <b>Rimuovi tutti gli ologrammi.</b></td>
  </tr>
  <tr>
    <td>Esperienza audio migliorata</td><td>È ora possibile ascoltare HoloLens in ambienti rumorosi e sperimentare un suono più realistico dalle applicazioni perché il suono è nascosto dalle pareti reali rilevate dal dispositivo.</td><td>Non è necessario eseguire qualsiasi operazione per ottenere il suono spaziale migliorato.</td>
  </tr>
  <tr>
    <td>Esplora file</td><td>Spostare ed eliminare file dall'HoloLens.</td><td>È possibile usare l'app <b>Esplora file</b> per spostare ed eliminare file dall'interno HoloLens.<br><br><b>Suggerimento:</b> Se non viene visualizzato alcun file, il filtro "Recenti" potrebbe essere attivo (l'icona dell'orologio è evidenziata nel riquadro sinistro). Per risolvere il problema, selezionare l'icona del documento This Device (Questo dispositivo) nel riquadro sinistro (sotto l'icona dell'orologio) oppure aprire il </b> menu e selezionare This Device <b>(Questo dispositivo).</b>
</td>
  </tr>
  <tr>
    <td>Supporto MTP (Media Transfer Protocol)</td><td>Consente al PC desktop di accedere alle librerie (foto, video, documenti) HoloLens per un facile trasferimento.</td><td>Analogamente ad altri dispositivi mobili, connettere il HoloLens <b></b> al PC per visualizzare Esplora file per accedere alle librerie HoloLens (foto, video, documenti) per un facile trasferimento.<br><br><b>Suggerimenti:</b><ul><li>Se non viene visualizzato alcun file, assicurarsi di accedere al HoloLens per abilitare l'accesso ai dati.</li><li>Dal <b>Esplora file</b> nel PC, è possibile <b></b> selezionare Proprietà del dispositivo per visualizzare Windows versione del sistema operativo Holographic (versione del firmware) e il numero di serie del dispositivo.</li></ul><b>Problema noto:</b> La ridenominazione HoloLens tramite <b>Esplora file</b> nel PC non è abilitata.</td>
  </tr>
  <tr>
    <td>Supporto di rete di Captive Portal durante l'installazione</td><td>È ora possibile configurare il HoloLens in una rete guest in hotel, centri conferenze, negozi al dettaglio o aziende che usano captive portal.</td><td>Durante l'installazione, selezionare la rete, selezionare Connetti automaticamente e immettere le informazioni di rete come richiesto.</td>
  </tr>
  <tr>
    <td>Sincronizzazione di foto e video tramite OneDrive app</td><td>Le foto e i video HoloLens verranno ora sincronizzati tramite l'app OneDrive dal Microsoft Store anziché dall'app Foto.</td><td>Per configurarlo, scaricare e avviare l'app OneDrive dallo Store. Alla prima esecuzione verrà richiesto di caricare automaticamente le foto in OneDrive. Se questa richiesta non viene visualizzata, è possibile trovare l'opzione nelle impostazioni dell'app.</td>
  </tr>
</table>

### <a name="for-developers"></a>Per sviluppatori

<table>
  <tr>
    <th>Funzionalità</th><th>Dettagli</th><th>Istruzioni</th>
  </tr>
  <tr>
    <td>Miglioramenti del mapping spaziale</td><td>Miglioramenti di qualità, semplificazione e prestazioni.</td><td>La mesh di mapping spaziale sarà più pulita. Sono necessari meno triangoli per rappresentare lo stesso livello di dettaglio. È possibile notare modifiche nella densità dei triangoli nella scena.</td>
  </tr>
  <tr>
    <td>Selezione automatica del punto di messa a fuoco in base al buffer di profondità</td><td>L'invio di un buffer di profondità Windows consente HoloLens selezionare automaticamente un punto di messa a fuoco per ottimizzare la stabilità dell'ologramma.</td><td>In Unity passare a Edit > Project Impostazioni > Player > Universal Windows Platform (Modifica > Project Impostazioni > <b>Player > Universal Windows Platform) > XR Impostazioni</b>, espandere l'elemento Windows Mixed Reality <b>SDK</b> e selezionare Enable Depth Buffer Sharing (Abilita condivisione <b>buffer</b>di profondità). Verrà verificata automaticamente la ricerca di nuovi progetti.<br><br>Per le app DirectX, assicurarsi di chiamare il metodo <a href="/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer">CommitDirect3D11DepthBuffer</a> in <b>HolographicRenderingParameters</b> per ogni frame per fornire il buffer di profondità Windows.
</td>
  </tr>
  <tr>
    <td>Modalità di riproiezione olografica</td><td>È ora possibile disabilitare la riproiezione posizionale HoloLens per migliorare la stabilità dell'ologramma di contenuto rigidamente bloccato dal corpo, ad esempio video a 360 gradi.</td><td>In Unity impostare <a href="https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.ReprojectionMode.html">HolographicSettings.ReprojectionMode</a> su <a href="https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.HolographicReprojectionMode.html">HolographicReprojectionMode.OrientationOnly</a> quando tutto il contenuto nella visualizzazione è rigidamente bloccato dal corpo.<br><br>Per le app DirectX, impostare <a href="/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.reprojectionmode"> HolographicCameraRenderingParameters.ReprojectionMode</a> su <a href="/uwp/api/windows.graphics.holographic.holographicreprojectionmode">HolographicReprojectionMode.OrientationOnly</a> quando tutto il contenuto nella visualizzazione è rigidamente bloccato dal corpo.</td>
  </tr>
  <tr>
    <td>API di personalizzazione delle app</td><td>Windows Le API sanno di più su dove è in esecuzione l'app, ad esempio se lo schermo del dispositivo è trasparente (HoloLens) o opaco (visore vr immersivo) e se la visualizzazione 2D di un'app UWP viene visualizzata nella shell olografica.</td><td>Unity in precedenza aveva esposto <a href="https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.IsDisplayOpaque.html">manualmente HolographicSettings.IsDisplayOpaque</a> in modo che funzionasse anche prima di questa compilazione.<br><br>Per le app DirectX è ora possibile accedere ad API esistenti come <a href="/uwp/api/windows.graphics.holographic.holographicdisplay.isopaque">HolographicDisplay.GetDefault(). Anche IsOpaque</a> e <a href="/uwp/api/windows.applicationmodel.preview.holographic.holographicapplicationpreview.iscurrentviewpresentedonholographicdisplay">HolographicApplicationPreview.IsCurrentViewPresentedOnHolographicDisplay</a> HoloLens.
</td>
  </tr>
  <tr>
      <td>Modalità di ricerca</td><td>Consente agli sviluppatori di accedere HoloLens sensori chiave durante la creazione di applicazioni accademiche e industriali per testare nuove idee nei campi della visione artificiale e della robotica, tra cui:<ul><li>Le quattro fotocamere di rilevamento dell'ambiente</li><li>Due versioni dei dati della fotocamera di mapping della profondità</li><li>Due versioni di un flusso di riflettività IR</li></ul></td><td><a href="/windows/mixed-reality/develop/platform-capabilities-and-apis/research-mode">Documentazione della modalità di ricerca</a><br><a href="https://github.com/Microsoft/HoloLensForCV">App di esempio in modalità ricerca</a></td>
  </tr>
</table>

### <a name="for-commercial-customers"></a>Per i clienti commerciali

<table>
  <tr>
    <th>Funzionalità</th><th>Dettagli</th><th>Istruzioni</th>
  </tr>
  <tr>
    <td>Usare più Azure Active Directory account utente in un singolo dispositivo</td><td>Condividere un HoloLens con più Azure AD utenti, ognuno con le proprie impostazioni utente e i dati utente nel dispositivo.</td><td><a href="/hololens/hololens-multiple-users">Centro Pro IT: Condividere HoloLens con più persone</a></td>
  </tr>
  <tr>
    <td>Modificare Wi-Fi rete all'accesso</td><td>Modificare Wi-Fi rete prima dell'accesso per consentire a un altro utente di accedere con il proprio account utente Azure AD per la prima volta, consentendo agli utenti di condividere i dispositivi in diverse posizioni e siti di lavoro.</td><td>Nella schermata di accesso è possibile usare l'icona di rete sotto il campo della password per connettersi a una rete. Ciò è utile quando si tratta della prima volta che si accede a un dispositivo.</td>
  </tr>
  <tr>
    <td>Registrazione unificata</td><td>È ora facile per un utente HoloLens che ha configurato il dispositivo con un account Microsoft personale per aggiungere un account aziendale (Azure AD) e aggiungere il dispositivo al server MDM.</td><td>Accedere con un account Azure AD e la registrazione viene eseguita automaticamente.</td>
  </tr>
  <tr>
    <td>Sincronizzazione della posta senza registrazione MDM</td><td>Supporto per la Exchange di posta elettronica di Active Sync (EAS) senza richiedere la registrazione MDM.</td><td>È ora possibile sincronizzare la posta elettronica senza registrarsi in MDM. È possibile configurare il dispositivo con un account Microsoft, scaricare e installare l'app Mail e aggiungere direttamente un account di posta elettronica aziendale.</td>
  </tr>
</table>

### <a name="for-it-pros"></a>Per i professionisti IT

<table>
  <tr>
    <th>Funzionalità</th><th>Dettagli</th><th>Istruzioni</th>
  </tr>
  <tr>
    <td>Nuovo nome del Windows Holographic for Business sistema operativo "Windows Holographic for Business"</td><td>Cancellare la denominazione delle edizioni per ridurre la confusione nell'applicazione delle licenze di aggiornamento dell'edizione quando le funzionalità di Commercial Suite sono abilitate HoloLens.</td><td>È possibile vedere quale edizione di Windows Holographic si trova nel dispositivo in Impostazioni > <b>System > About</b>. "Windows Holographic for Business" verrà visualizzato se è stato applicato un aggiornamento dell'edizione per abilitare le funzionalità di Commercial Suite. Informazioni su come <a href="/hololens/hololens-upgrade-enterprise">sbloccare Windows Holographic for Business funzionalità .</a></td>
  </tr>
  <tr>
  <td>Windows Progettazione configurazione (WCD)</td><td>Creare e modificare pacchetti di provisioning per configurare HoloLens tramite l'app WCD aggiornata. Procedura guidata HoloLens semplice per l'aggiornamento dell'edizione, configurazione guidata, fuso orario/area geografica, token di Azure AD, rete e provider di servizi di configurazione per sviluppatori. Editor avanzato filtrato per HoloLens opzioni supportate, inclusi i CSP di Accesso assegnato e Gestione account.</td><td><a href="/hololens/hololens-provisioning">Centro Pro IT: Configurare HoloLens usando un pacchetto di provisioning</a></td>
  </tr>
  <tr>
    <td>Configurazione configurabile (Configurazione guidata)</td><td>Nascondere calibrazione, training movimenti/sguardo e Wi-Fi di configurazione durante l'installazione.</td><td><a href="/hololens/hololens-provisioning#create-a-provisioning-package-for-hololens-using-the-hololens-wizard">Centro Pro IT: Configurare HoloLens usando un pacchetto di provisioning</a></td>
  </tr>
  <tr>
    <td>Supporto Azure AD token di blocco</td><td>Pre-registrare il dispositivo Azure AD tenant della directory per un flusso di configurazione utente più rapido.</td><td><a href="/hololens/hololens-provisioning">Centro Pro IT: Configurare HoloLens usando un pacchetto di provisioning</a></td>
  </tr>
  <tr>
  <td>Provider di servizi di sviluppo DeveloperSetup</td><td>Distribuire il profilo per configurare HoloLens in modalità sviluppatore. Utile sia per i dispositivi di sviluppo che per i dispositivi demo.</td><td><a href="/hololens/hololens-provisioning">Centro Pro IT: Configurare HoloLens usando un pacchetto di provisioning</a></td>
  </tr>
  <tr>
  <td>Provider di servizi di gestione account</td><td>Condividere un dispositivo HoloLens e rimuovere i dati utente dopo la disconnessione o le soglie di inattività/archiviazione per l'utilizzo temporaneo. Supporta gli Azure AD account.</td><td><a href="/hololens/hololens-provisioning">Centro Pro IT: Configurare HoloLens usando un pacchetto di provisioning</a></td>
  </tr>
  <tr>
  <td>Accesso assegnato</td><td>Windows accesso assegnato per i ruoli di lavoro o le demo di prima riga. Blocco singolo o multi-app. Non è necessario sbloccare lo sviluppatore.</td><td><a href="/hololens/hololens-kiosk">Centro Pro IT: configurare la HoloLens in modalità tutto schermo</a></td>
  </tr>
  <tr>
  <td>Accesso guest per i dispositivi in modalità tutto schermo</td><td>Windows accesso assegnato con account guest senza password per le demo. Blocco singolo o multi-app. Non è necessario sbloccare lo sviluppatore.</td><td><a href="/hololens/hololens-kiosk#guest">Centro Pro IT: configurare la HoloLens in modalità tutto schermo</a></td>
  </tr>
  <tr>
    <td>Configurare la diagnostica (Configurazione guidata)</td><td>Ottenere i log di diagnostica da HoloLens in modo da poter risolvere Azure AD errori di accesso (prima che Hub di Feedback sia disponibile per l'utente il cui accesso non è riuscito).</td><td>Quando l'installazione o l'accesso non riesce, scegliere la nuova <b>opzione Raccogli informazioni</b> per ottenere i log di diagnostica per la risoluzione dei problemi.</td>
  </tr>
  <tr>
    <td>Scadenza della password indefinita dell'account locale</td><td>Rimuovere l'interruzione della reimpostazione del dispositivo alla scadenza della password dell'account locale.</td><td>Quando si esegue il provisioning di un account locale, non è più necessario modificare la password ogni 42 giorni in <b>Impostazioni</b>, poiché la password dell'account non scade più.</td>
  </tr>
  <tr>
    <td>Dettagli e stato della sincronizzazione MDM</td><td>Funzionalità Windows standard per comprendere lo stato e i dettagli della sincronizzazione MDM dall'interno HoloLens.</td><td>È possibile controllare lo stato di sincronizzazione MDM per un dispositivo in Account Impostazioni > > accesso aziendale o dell'istituto <b>di istruzione > info</b>. Nella sezione Stato sincronizzazione dispositivo è possibile avviare una sincronizzazione, visualizzare le aree gestite da MDM e creare <b> <b> ed esportare un report di diagnostica avanzato.</td>
  </tr>
</table>

## <a name="known-issues"></a>Problemi noti

Abbiamo lavorato sodo per offrire un'esperienza Windows Mixed Reality, ma stiamo ancora verificando alcuni problemi noti. Se si trovano altri utenti, [inviare commenti e suggerimenti.](/windows/mixed-reality/give-us-feedback)

### <a name="hololens"></a>HoloLens

#### <a name="after-update"></a>Dopo l'aggiornamento

È possibile notare i problemi seguenti dopo l'aggiornamento da RS1 a RS4 nel HoloLens:
* **Reimpostazione dei pin:** le app 3x3 aggiunte al menu Start verranno reimpostate ai valori predefiniti dopo l'aggiornamento. 
* **Reimpostazione delle app e degli ologrammi** posizionati: le app inserite nel mondo verranno rimosse dopo l'aggiornamento e dovranno essere riposte nello spazio. 
* **Hub di Feedback** avvio immediato: subito dopo l'aggiornamento, saranno disponibili alcuni minuti prima di poter avviare alcune app della posta in arrivo, ad esempio Hub di Feedback, mentre si aggiornano automaticamente. 
* I **certificati Wi-Fi** aziendali devono essere sincronizzati di nuovo: è in corso l'analisi di un problema che richiede che il HoloLens sia connesso a una rete diversa per poter sincronizzare nuovamente i certificati aziendali con il dispositivo prima di potersi riconnettere alle reti aziendali usando i certificati. 
* **La riproduzione video H.265 HEVC** non funziona: le applicazioni che tentano di riprodurre video H.265 riceveranno un messaggio di errore. La soluzione alternativa consiste [nell'accedere Windows Portale di dispositivi,](/windows/mixed-reality/develop/platform-capabilities-and-apis/using-the-windows-device-portal)selezionare **App** sulla barra di spostamento a sinistra e **rimuovere l'applicazione** HEVC. Installare quindi la versione più [estensione video HEVC](https://www.microsoft.com/p/hevc-video-extensions/9nmzlz57r3t7) dal Microsoft Store. Il problema è in corso di analisi. 

#### <a name="for-developers-updating-hololens-apps-for-devices-running-windows-10-april-2018-update"></a>Per gli sviluppatori: aggiornamento delle HoloLens per i dispositivi che eseguono Windows 10 aggiornamento di aprile 2018

Oltre a un ottimo elenco di nuove [funzionalità,](#new-features-for-hololens)l'aggiornamento di Windows 10 aprile 2018 (RS4) per HoloLens applica alcuni comportamenti del codice che non sono stati applicati nelle versioni precedenti:
* Richieste di autorizzazione per l'uso di risorse sensibili **(fotocamera,** microfono e così via): RS4 in HoloLens imporrà le richieste di autorizzazione per le app che intendono accedere a risorse sensibili, ad esempio la fotocamera o il microfono. RS1 in HoloLens non ha forzato queste richieste, quindi, se l'app presuppone l'accesso immediato a queste risorse, potrebbe verificarsi un arresto anomalo in RS4 (anche se l'utente concede l'autorizzazione alla risorsa richiesta). Per altre informazioni, leggere l'articolo relativo alle dichiarazioni [di funzionalità delle app UWP.](/windows/uwp/packaging/app-capability-declarations)
* **Le chiamate alle app all'esterno** dell'utente: RS4 HoloLens applica l'uso corretto [ *Windows.System. Classe Launcher* per](/uwp/api/Windows.System.Launcher) avviare un'altra app dalla propria. Ad esempio, sono stati osservati problemi con le app che *chiamanoWindows.System. Launcher.LaunchUriForResultsAsync* da un thread non ASTA (interfaccia utente). Questa operazione avrà esito positivo in RS1 HoloLens, ma RS4 richiede l'esecuzione della chiamata sul thread dell'interfaccia utente.

### <a name="windows-mixed-reality-on-desktop"></a>Windows Mixed Reality desktop

#### <a name="visual-quality"></a>Qualità visiva

* Se dopo l'aggiornamento di Windows 10 aprile 2018 si nota che la grafica è più sfocata rispetto a prima o che il campo di visualizzazione è più piccolo sul visore VR, è possibile che l'impostazione delle prestazioni automatica sia stata modificata per mantenere una frequenza dei fotogrammi sufficiente su una scheda grafica meno potente (ad esempio Nvidia 1050). È possibile eseguire manualmente l'override di questa impostazione (se si sceglie) passando a Impostazioni > **Mixed reality > Headset display > Experience options (Opzioni** esperienza) > Change (Modifica) e impostando "Automatic" (Automatico) su "90 Hz". È anche possibile provare a modificare **Qualità visiva** (nella stessa Impostazioni pagina) in "Alta".

#### <a name="windows-mixed-reality-setup"></a>Windows Mixed Reality configurazione

* Quando si configurano Windows con un visore VR connesso, il monitor del PC potrebbe essere vuoto. Scollegare il visore VR per abilitare l'output sul monitor del PC per completare Windows configurazione.
* Se le cuffi non sono connesse, è possibile che non siano stati forniti suggerimenti quando si visita per la prima volta Windows Mixed Reality home.
* Altri Bluetooth possono causare interferenze con i controller del movimento. Se i controller del movimento hanno problemi di connessione/associazione/rilevamento, assicurarsi che la radio Bluetooth (se un dongle esterno) sia collegata a una posizione non strutturata e non immediatamente accanto a un altro dongle Bluetooth. Provare anche ad alimentare altre periferiche Bluetooth durante Windows Mixed Reality per verificare se è utile.

#### <a name="games-and-apps-from-the-microsoft-store"></a>Giochi e app dal Microsoft Store

* Alcuni giochi con uso intensivo della grafica, ad esempio ForzaElettrico 7, possono causare problemi di prestazioni nei PC meno idonei quando vengono riprodotti all'interno Windows Mixed Reality.

#### <a name="audio"></a>Audio

* Se Cortana è abilitata nel PC host prima di usare il visore VR di Windows Mixed Reality, è possibile che si perda la simulazione del suono spaziale applicata alle app posizionate nella Windows Mixed Reality home. 
   * Per risolvere il problema, abilitare "Windows Sonic per cuffie" in tutti i dispositivi audio collegati al PC, anche nel dispositivo audio connesso al visore VR:
      1. Fare clic con il pulsante sinistro del mouse sull'icona dell'altoparlante sulla barra delle applicazioni del desktop e selezionare dall'elenco dei dispositivi audio.
      2. Fare clic con il pulsante destro del mouse sull'icona dell'altoparlante sulla barra delle applicazioni del desktop e scegliere "Windows Sonic per cuffie" nel menu "Configurazione voce".
      3. Ripetere questi passaggi per tutti i dispositivi audio (endpoint).
   * Un'altra opzione è disattivare "Let Cortana respond to Hey Cortana" (Consenti Cortana rispondere a Hey Cortana) **in** Impostazioni Cortana desktop prima di avviare  >   Windows Mixed Reality.
* Quando un altro dispositivo USB multimediale (ad esempio una web cam) condivide lo stesso hub USB (esterno o interno al PC) con il visore VR di Windows Mixed Reality, in rari casi il jack/le cuffia audio del visore VR può avere un suono acustico o nessun audio. È possibile risolvere il problema tramite il visore VR in una porta USB che non condivide lo stesso hub dell'altro dispositivo oppure disconnettere o disabilitare l'altro dispositivo multimediale USB.
* In rari casi, l'hub USB del PC host non è in grado di fornire potenza sufficiente al visore VR Windows Mixed Reality e si potrebbe notare un rumore eccessivo dalle cuffie connesse al visore VR.

#### <a name="holograms"></a>Holograms (Ologrammi)

* Se è stato inserito un numero elevato di ologrammi nella propria casa Windows Mixed Reality, alcuni potrebbero scomparire e ricomparire mentre ci si guarda attorno. Per evitare questo problema, rimuovere alcuni degli ologrammi nell'area della Windows Mixed Reality home.

#### <a name="motion-controllers"></a>Controller del movimento

* Se l'input non viene indirizzato al visore VR, il controller del movimento scomparirà brevemente quando viene mantenuto accanto al limite della stanza. Premere Win+Y per assicurarsi che sia presente un banner blu nel monitor desktop per risolvere il problema. 
* In alcuni casi, quando si fa clic su una pagina Web in Microsoft Edge, il contenuto viene ingrandito anziché fare clic.

#### <a name="desktop-app-in-the-windows-mixed-reality-home"></a>App desktop nella home Windows Mixed Reality home

* Strumento di cattura non funziona nell'app desktop.
* L'app desktop non mantiene l'impostazione al riavvio.
* Se si usa un'anteprima Portale realtà mista desktop, quando si apre l'app desktop nella home page di Windows Mixed Reality, è possibile notare l'effetto mirror infinito. 
* L'esecuzione dell'app desktop può causare problemi di prestazioni nei PC Windows Mixed Reality Ultra; Non è consigliabile.  
* L'app desktop può essere avviata automaticamente perché una finestra invisibile sul desktop ha lo stato attivo. 
* La richiesta di controllo dell'account utente desktop rende nero il visore VR fino al completamento della richiesta.

#### <a name="windows-mixed-reality-for-steamvr"></a>Windows Mixed Reality for SteamVR

* Potrebbe essere necessario avviare Portale realtà mista dopo l'aggiornamento per assicurarsi che gli aggiornamenti software necessari per l'aggiornamento Windows 10 aprile 2018 siano stati completati prima dell'avvio di FirmwareVR. 
* Per mantenere la compatibilità con l'aggiornamento di Windows 10 aprile 2018, è necessario disporre di una versione recente di Windows Mixed Reality per SteamVR. Assicurarsi che gli aggiornamenti automatici siano attivati per Windows Mixed Reality per SteamVR, che si trova nella sezione "Software" della libreria in Steam.  

#### <a name="other-issues"></a>Altri problemi

>[!IMPORTANT]
>In una versione precedente dell'aggiornamento di Windows 10 aprile 2018 di cui è stato eseguito il push ai insider (versione 17134.5) mancava un componente software necessario per l'esecuzione Windows Mixed Reality. È consigliabile evitare questa versione se si usa Windows Mixed Reality. 

È stata identificata una regressione delle prestazioni quando si usa Surface Book 2 nella versione iniziale di questo aggiornamento (10.0.17134.1) che verrà risolto in una patch di aggiornamento futura. È consigliabile attendere che questo problema venga risolto prima di eseguire l'aggiornamento manualmente o attendere che l'aggiornamento venga eseguito normalmente.

## <a name="provide-feedback-and-report-issues"></a>Inviare commenti e suggerimenti e segnalare i problemi

Usare [l'app Hub di Feedback nel computer HoloLens o Windows 10 per](/windows/mixed-reality/give-us-feedback) inviare commenti e suggerimenti e segnalare problemi. L Hub di Feedback garantisce che tutte le informazioni di diagnostica necessarie siano incluse per consentire ai tecnici di eseguire rapidamente il debug e risolvere il problema.

>[!NOTE]
>Assicurarsi di accettare il prompt che chiede se si desidera Hub di Feedback accedere alla cartella Documenti (selezionare **Sì** quando richiesto).

## <a name="prior-release-notes"></a>Note sulla versione precedente

* [Note sulla versione - ottobre 2017](release-notes-october-2017.md)
* [Note sulla versione - agosto 2016](release-notes-august-2016.md)
* [Note sulla versione - maggio 2016](release-notes-may-2016.md)
* [Note sulla versione - marzo 2016](release-notes-march-2016.md)

## <a name="see-also"></a>Vedi anche
* [Supporto per visori VR immersive (collegamento esterno)](./troubleshooting-windows-mixed-reality.md)
* [HoloLens (collegamento esterno)](https://support.microsoft.com/products/hololens)
* [Installare gli strumenti](/windows/mixed-reality/develop/install-the-tools)
* [Commenti e suggerimenti](/windows/mixed-reality/give-us-feedback)
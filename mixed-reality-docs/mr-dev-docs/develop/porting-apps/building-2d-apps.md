---
title: Aggiornamento di app UWP 2D per Windows Mixed Reality
description: Questo articolo illustra l'aggiornamento dell'app 2D Universal Windows Platform esistente per l'esecuzione HoloLens e Windows Mixed Reality visori immersive.
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: App 2D, UWP, app flat, HoloLens, visore immersivo, modello di app, pulsante Indietro, barra dell'app, dpi, risoluzione, scalabilità, porting, HoloLens prima generazione, HoloLens 2, visore per realtà mista, visore windows mixed reality, migrazione, Windows 10
ms.openlocfilehash: 2b0fa403394432f2cec80e44d27804b07934260e60281f5c70b68c7377d3e55e
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115195990"
---
# <a name="updating-2d-uwp-apps-for-windows-mixed-reality"></a>Aggiornamento di app UWP 2D per Windows Mixed Reality

Windows Mixed Reality gli utenti possono vedere gli ologrammi come se fossero proprio intorno a loro nel mondo fisico e digitale. Nella sua base, sia HoloLens pc desktop a cui si collegano gli accessori vr immersivi sono Windows 10 dispositivi. È possibile eseguire quasi tutte le app UWP (Universal Windows Platform) nello Store come app 2D.

## <a name="creating-a-2d-uwp-app-for-mixed-reality"></a>Creazione di un'app UWP 2D per la realtà mista

Il primo passaggio per portare un'app 2D in visori di realtà mista consiste nell'eseguire l'app come app 2D standard sul monitor desktop.

### <a name="building-a-new-2d-uwp-app"></a>Creazione di una nuova app UWP 2D

Per creare una nuova app 2D per la realtà mista, è necessario creare un'app UWP (Universal Windows Platform) 2D standard. Non sono necessarie altre modifiche all'app per l'esecuzione come ardesia in realtà mista.

Per iniziare a creare un'app UWP 2D, vedere l'articolo [Creare la prima app.](/windows/uwp/get-started/your-first-app)

### <a name="bringing-an-existing-2d-store-app-to-uwp"></a>Portare un'app 2D Store esistente nella UWP

Se si ha già un'app Windows 2D nello Store, assicurarsi che sia mirata alla piattaforma UWP (Universal Windows Platform) Windows 10. Ecco tutti i potenziali punti di partenza che è possibile avere con l'app Dello Store:
<br>

|  Punto di partenza  |  Destinazione piattaforma manifesto AppX  |  Come rendere universale questo oggetto? | 
|----------|----------|----------|
|  Windows Phone (Silverlight)  |  Manifesto dell'app Silverlight |  [Eseguire la migrazione a WinRT](/previous-versions/windows/apps/dn642486(v=vs.105)) | 
|  Windows Phone 8.1 Universale  |  8.1 Manifesto AppX che non include la destinazione della piattaforma  |  [Eseguire la migrazione dell'app alla piattaforma Windows universali](/previous-versions/visualstudio/visual-studio-2015/misc/migrate-apps-to-the-universal-windows-platform-uwp) | 
|  Windows Store 8  |  8 Manifesto AppX che non include la destinazione della piattaforma  |  [Eseguire la migrazione dell'app alla piattaforma Windows universali](/previous-versions/visualstudio/visual-studio-2015/misc/migrate-apps-to-the-universal-windows-platform-uwp) | 
|  Windows Store 8.1 Universal  |  8.1 Manifesto AppX che non include la destinazione della piattaforma  |  [Eseguire la migrazione dell'app alla piattaforma Windows universali](/previous-versions/visualstudio/visual-studio-2015/misc/migrate-apps-to-the-universal-windows-platform-uwp) | 

Se oggi si ha un'app Unity 2D compilata come app Win32 nel **PC,** la destinazione di compilazione autonoma mac & Linux passa alla destinazione di compilazione della piattaforma **Universal Windows** per la realtà mista.

Si parlerà dei modi in cui è possibile limitare l'app in modo specifico HoloLens usando il Windows. Famiglia di dispositivi olografici [sotto](#publish-and-maintain-your-universal-app).

### <a name="run-your-2d-app-in-a-windows-mixed-reality-immersive-headset"></a>Eseguire l'app 2D in un visore Windows Mixed Reality visore immersivo

Se l'app 2D è stata distribuita in un computer desktop e l'hai provata sul monitor, sei pronto per provarla con un visore desktop immersivo.

È sufficiente passare al menu Start all'interno del visore di realtà mista e avviare l'app da qui. La shell desktop e la shell olografica condividono entrambi lo stesso set di app UWP e quindi l'app dovrebbe essere già presente dopo la distribuzione da Visual Studio.

## <a name="targeting-both-immersive-headsets-and-hololens"></a>Targeting both immersive headsets and HoloLens

Congratulazioni! L'app usa ora la piattaforma Windows 10 UWP (Universal Windows Platform).

L'app è ora in grado di essere eseguita nei dispositivi Windows attuali, ad esempio Desktop, Mobile, Xbox, Windows Mixed Reality visori immersivi, HoloLens e dispositivi Windows futuri. Tuttavia, per scegliere come destinazione tutti questi dispositivi, è necessario assicurarsi che l'app sia mirata al Windows. Famiglia di dispositivi universali.

### <a name="change-your-device-family-to-windowsuniversal"></a>Modificare la famiglia di dispositivi in Windows. Universale

Ora si passerà al manifesto di AppX per assicurarsi che l'app UWP Windows 10 possa essere eseguita in HoloLens:
* Aprire il file di soluzione dell'app **con** Visual Studio e passare al manifesto del pacchetto dell'app
* Fare clic con il pulsante destro del mouse sul file **Package.appxmanifest** nella soluzione e passare **a Visualizza codice**<br>
  ![package.appxmanifest in Esplora soluzioni](images/openappxmanifest-500px.png)<br>
* Assicurarsi che la piattaforma di destinazione sia Windows. Universale nella sezione dipendenze
  ```
  <Dependencies>
    <TargetDeviceFamily Name="Windows.Universal" MinVersion="10.0.10240.0" MaxVersionTested="10.0.10586.0" />
  </Dependencies>
  ```
* Salvare!

Se non si usa Visual Studio per l'ambiente di sviluppo, è possibile aprire **AppXManifest.xml** nell'editor di testo scelto per assicurarsi di scegliere come destinazione **l'Windows. Universal** *TargetDeviceFamily*.

### <a name="run-in-the-hololens-emulator"></a>Eseguire nel HoloLens Emulator

Ora che l'app UWP è destinata a "Windows. Universale", creare l'app ed eseguirla nel [HoloLens Emulator](../platform-capabilities-and-apis/using-the-hololens-emulator.md).
* Assicurarsi di aver installato [il HoloLens Emulator](../install-the-tools.md).
* In Visual Studio selezionare la configurazione della build **x86** per l'app

  ![Configurazione di build x86 in Visual Studio](../platform-capabilities-and-apis/images/x86setting.png)<br>
* Seleziona **Emulatore HoloLens** nel menu a discesa delle destinazioni di distribuzione

  ![HoloLens Emulator nell'elenco di destinazione della distribuzione](images/deployemulator-500px.png)<br>
* Selezionare **Debug > Avvia debug** per distribuire l'app e avviare il debug.
* L'emulatore avvia ed esegue l'app.
* Con una tastiera, un mouse e un controller Xbox, posizionare l'app nel mondo per avviarla.

  ![HoloLens Emulator caricato con un esempio UWP](images/hololensemulatorwithuwpsample-800px.png)<br>

### <a name="next-steps"></a>Passaggi successivi

A questo punto, può verificarsi una delle due operazioni seguenti:
1. L'app mostrerà la schermata iniziale e inizierà a essere eseguita dopo che è stata inserita nel Emulator! Fantastico!
2. In caso contrario, dopo aver visualizzato un'animazione di caricamento per un ologramma 2D, il caricamento verrà interrotta e l'app verrà semplicemente visualizzata nella schermata iniziale. Ciò significa che si è verificato un errore e sarà necessario un'analisi più approfondita per comprendere come dare vita all'app nella realtà mista.

È necessario eseguire il debug per accedere alla radice dei possibili problemi che bloccano l'avvio dell'app UWP HoloLens.

### <a name="running-your-uwp-app-in-the-debugger"></a>Esecuzione dell'app UWP nel debugger

Questa procedura illustra il debug dell'app UWP usando Visual Studio debugger.
* Se non è già stato fatto, aprire la soluzione in Visual Studio. Modificare la destinazione in **HoloLens Emulator** e la configurazione di compilazione in **x86**.
* Selezionare **Debug > Avvia debug** per distribuire l'app e avviare il debug.
* Posizionare l'app nel mondo con il mouse, la tastiera o il controller Xbox.
* Visual Studio'interruzione dovrebbe interrompersi in un punto qualsiasi del codice dell'app.
  - Se l'app non si arresta immediatamente in modo anomalo o si interrompe nel debugger a causa di un errore non gestito, eseguire un test delle funzionalità principali dell'app per assicurarsi che tutto sia in esecuzione e funzionante. È possibile che vengano visualizzati errori come nella figura seguente (eccezioni interne gestite). Per evitare errori interni che influiscono sull'esperienza dell'app, eseguire i test automatizzati e gli unit test per assicurarsi che tutto si comporti come previsto.

![HoloLens Emulator caricato con un esempio UWP che mostra un'eccezione di sistema](images/hololensemulatorwithuwpsampleexception-800px.png)

## <a name="update-your-ui"></a>Aggiornare l'interfaccia utente

Ora che l'app UWP è in esecuzione su visori immersivi e HoloLens come ologramma 2D, ora ci si assicurerà che sia molto bello. Di seguito sono illustrati alcuni aspetti da considerare:
* Windows Mixed Reality tutte le app 2D a una risoluzione fissa e DPI che equivale a 853 x 480 pixel effettivi. Valutare se la progettazione deve essere perfezionata su questa scala ed esaminare le linee guida di progettazione riportate di seguito per migliorare l'esperienza HoloLens visori immersivi.
* Windows Mixed Reality [non supporta riquadri](../../design/app-model.md) animati 2D. Se la funzionalità principale mostra informazioni in un riquadro animato, provare a spostare nuovamente le informazioni nell'app o esplorare le utilità di avvio delle [app 3D.](../../distribute/3d-app-launcher-design-guidance.md)

### <a name="2d-app-view-resolution-and-scale-factor"></a>Risoluzione della visualizzazione dell'app 2D e fattore di scala

![Dalla progettazione reattiva](images/scale-500px.png)

Windows 10 sposta tutta la progettazione visiva dai pixel dello schermo reale ai **pixel effettivi.** Ciò significa che gli sviluppatori progettano l'interfaccia utente seguendo le linee guida dell'interfaccia utente di Windows 10 per i pixel effettivi e il ridimensionamento Windows garantisce che tali pixel effettivi siano le dimensioni giuste per l'usabilità tra dispositivi, risoluzioni, DPI e così via. Per altre [informazioni, vedere](/windows/uwp/design/layout/screen-sizes-and-breakpoints-for-responsive-design) questo articolo su MSDN e questa [presentazione BUILD.](https://video.ch9.ms/sessions/build/2015/2-63_Build_2015_Windows_Scaling.pptx)

Anche con la possibilità unica di posizionare le app nel mondo a una gamma di distanze, è consigliabile visualizzare distanze simili a tv per produrre la migliore leggibilità e interazione con lo sguardo o il movimento. Per questo, un elenco virtuale nella home page di realtà mista visualizza la visualizzazione UWP flat in:

**1280x720, 150% DPI** (853 x 480 pixel effettivi)

Questa risoluzione presenta diversi vantaggi:
* Questo layout di pixel efficace avrà circa la stessa densità di informazioni di un tablet o di un desktop di piccole dimensioni.
* Corrisponde al valore DPI fisso e ai pixel effettivi per le app UWP in esecuzione Xbox One, consentendo esperienze semplici tra i dispositivi.
* Queste dimensioni hanno un aspetto positivo quando vengono ridimensionate attraverso la gamma di distanze operative per le app nel mondo.

### <a name="2d-app-view-interface-design-best-practices"></a>Procedure consigliate per la progettazione dell'interfaccia di visualizzazione delle app 2D

**fare:**
* Seguire la Windows 10 [human interface guidelines (HIG)](https://dev.windows.com/design) per gli stili, le dimensioni dei caratteri e le dimensioni dei pulsanti. HoloLens il lavoro necessario per garantire che l'app abbia modelli di app compatibili, dimensioni del testo leggibili e dimensioni appropriate della destinazione dei risultati.
* Assicurarsi che l'interfaccia [](/windows/uwp/design/layout/screen-sizes-and-breakpoints-for-responsive-design) utente segua le procedure consigliate per la progettazione reattiva HoloLens risoluzione e DPI univoche.
* Usare le raccomandazioni del tema a colori "chiaro" Windows.

**Non:**
* Modificare l'interfaccia utente in modo troppo drastico quando si è in realtà mista, per garantire agli utenti un'esperienza familiare in e fuori dal visore.

### <a name="understand-the-app-model"></a>Informazioni sul modello di app

Il [modello di app](../../design/app-model.md) per la realtà mista è progettato per usare La home page di realtà mista, in cui molte app convivino. Si pensi a questo come l'equivalente di realtà mista del desktop, in cui si eseguono molte app 2D contemporaneamente. Ciò ha implicazioni sul ciclo di vita dell'app, sui riquadri e su altre funzionalità chiave dell'app.

### <a name="app-bar-and-back-button"></a>Barra dell'app e pulsante Indietro

Le visualizzazioni 2D sono decorate con una barra dell'app sopra il contenuto. La barra dell'app include due punti di personalizzazione specifici dell'app:

**Titolo:** visualizza il *nome visualizzato del* riquadro associato all'istanza dell'app

**Pulsante Indietro:** genera *[l'evento BackRequested](/uwp/api/Windows.UI.Core.SystemNavigationManager)* quando viene premuto. La visibilità del pulsante Indietro è controllata *[da SystemNavigationManager.AppViewBackButtonVisibility](/uwp/api/Windows.UI.Core.SystemNavigationManager)*.

![Interfaccia utente della barra dell'app nella visualizzazione app 2D](images/12697297-10104100857470613-1470416918759008487-o-500px.jpg)<br>
*Interfaccia utente della barra dell'app nella visualizzazione app 2D*

### <a name="test-your-2d-apps-design"></a>Testare la progettazione dell'app 2D

È importante testare l'app per assicurarsi che il testo sia leggibile, che i pulsanti siano selezionabili come destinazione e che l'app complessiva sia corretta. È possibile [eseguire test](../platform-capabilities-and-apis/testing-your-app-on-hololens.md) su un visore visore desktop, un HoloLens, un emulatore o un dispositivo touch con risoluzione impostata su 1280x720 @150 %.

## <a name="new-input-possibilities"></a>Nuove possibilità di input

HoloLens sensori di profondità avanzati per vedere il mondo e vedere gli utenti. In questo modo è possibile eseguire movimenti avanzati della mano, [ad esempio bloom](../../design/system-gesture.md#bloom) e [air-tap.](../../design/gaze-and-commit.md#composite-gestures) I microfoni potenti abilitano anche [le esperienze vocali.](../../design/voice-input.md)

Con i visori visori desktop, gli utenti possono usare i controller di movimento per puntare alle app e intervenire. Possono anche usare un gamepad, mirando agli oggetti con lo sguardo.

Windows si occupa di tutta questa complessità per le app UWP, traducendo lo [sguardo,](../../design/gaze-and-commit.md) [](/windows/uwp/design/input/handle-pointer-input#pointer_events) i movimenti, la voce e l'input del controller di movimento in eventi puntatore che astrarre il meccanismo di input. Ad esempio, un utente potrebbe aver eseguito un tocco d'aria con la mano o aver premuto il trigger Seleziona in un controller di movimento, ma le applicazioni 2D non devono sapere da dove provenivano l'input, ma vedono semplicemente una pressione 2D tramite tocco, come su un touchscreen.

Ecco i concetti/scenari generali che è necessario comprendere per l'input quando si porta l'app UWP in HoloLens:
* [Lo](../../design/gaze-and-commit.md) sguardo si trasforma in eventi al passaggio del mouse, che possono attivare in modo imprevisto menu, riquadri a comparsa o altri elementi dell'interfaccia utente per visualizzare solo guardando l'app.
* Lo sguardo non è preciso come l'input del mouse. Usare destinazioni di hit di dimensioni appropriate per HoloLens, in modo simile alle applicazioni per dispositivi mobili con tocco. I piccoli elementi vicino ai bordi dell'app sono particolarmente difficili da interagire.
* Gli utenti devono cambiare modalità di input per passare dallo scorrimento al trascinamento fino alla panoramica con due dita. Se l'app è stata progettata per l'input tocco, è consigliabile assicurarsi che nessuna funzionalità principale sia bloccata dietro la panoramica con due dita. In tal caso, è consigliabile avere meccanismi di input alternativi come i pulsanti che possono avviare la panoramica con due dita. Ad esempio, l'app Mappe può eseguire lo zoom con la panoramica con due dita, ma ha un pulsante più, meno e ruota per simulare le stesse interazioni di zoom con singoli clic.

[L'input](../../design/voice-input.md) vocale è una parte essenziale dell'esperienza di realtà mista. Sono state abilitate tutte le API voce che si Windows 10 l'Cortana quando si usa un visore.

## <a name="publish-and-maintain-your-universal-app"></a>Pubblicare e gestire l'app universale

Una volta che l'app è in esecuzione, creare un pacchetto dell'app per [inviarla all'Microsoft Store](../../distribute/submitting-an-app-to-the-microsoft-store.md).

## <a name="see-also"></a>Vedi anche
* [Modello di app](../../design/app-model.md)
* [Puntamento con la testa e commit](../../design/gaze-and-commit.md)
* [Controller del movimento](../../design/motion-controllers.md)
* [Input vocale](../../design/voice-input.md)
* [Invio di un'app a Microsoft Store](../../distribute/submitting-an-app-to-the-microsoft-store.md)
* [Uso dell'emulatore HoloLens](../platform-capabilities-and-apis/using-the-hololens-emulator.md)
---
title: Note sulla versione - ottobre 2018
description: Rimanere aggiornati sulle note sulla versione HoloLens e Windows Mixed Reality per l'aggiornamento Windows 10 ottobre 2018/RS5.
author: mattzmsft
ms.author: mazeller
ms.date: 10/02/2018
ms.topic: article
keywords: note sulla versione, versione, Windows 10, build, rs5, sistema operativo
ms.openlocfilehash: e046025ff4952a6e8779545374ec59d9f49c907ad3174b188474ae040cb28ac7
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115219973"
---
# <a name="release-notes---october-2018"></a>Note sulla versione - ottobre 2018

Il **[Aggiornamento di Windows 10 (ottobre 2018)](https://blogs.windows.com/windowsexperience/2018/10/02/find-out-whats-new-in-windows-and-office-in-october/)** (noto anche come RS5) include nuove funzionalità per HoloLens e Windows Mixed Reality visori VR immersive connessi ai PC. 

Per eseguire l'aggiornamento alla versione più recente in HoloLens o PC (per i visori VR immersive di Windows Mixed Reality), aprire l'app  **Impostazioni,** passare a Update & Security (Aggiorna **sicurezza di &)** e quindi selezionare il pulsante Controlla aggiornamenti. In un PC Windows 10, è anche possibile installare manualmente il Aggiornamento di Windows 10 (ottobre 2018) usando lo Windows [di creazione di supporti.](https://www.microsoft.com/software-download/windows10)

**Versione più recente per Desktop:** Aggiornamento di Windows 10 (ottobre 2018) (**10.0.17763.107**)<br>
**Ultima versione per HoloLens:** Aggiornamento di Windows 10 (ottobre 2018) (**10.0.17763.134**)<br>

## <a name="new-features-for-windows-mixed-reality-immersive-headsets"></a>Nuove funzionalità per l'Windows Mixed Reality visori VR immersive

Il Aggiornamento di Windows 10 (ottobre 2018) include numerosi miglioramenti per l'uso Windows Mixed Reality visori VR immersive con il PC desktop.

### <a name="for-everyone"></a>Per tutti

* **Mixed Reality Flashlight:** apri un portale nel mondo reale per trovare la tastiera, vedere qualcuno nelle vicinanze o osservare l'ambiente circostante senza rimuovere il visore VR. Puoi attivare Mixed Reality Flashlight dal menu Start, premendo Windows + Grab sul controller del movimento o pronunciando "Flashlight on/off". Puntare il controller nella direzione di ciò che si vuole vedere, ad esempio usando una torcia nel scuro.

    ![Torcia di realtà mista](images/mr-flashlight.png)

* **Nuove app e modi per avviare il contenuto nel ambiente iniziale**
    * Se si usa [Windows Mixed Reality per SteamVR,](./using-steamvr-with-windows-mixed-reality.md)i titoli di SteamVR vengono ora visualizzati nel menu Start e le utilità di avvio delle app per ognuna possono essere inserite nel ambiente iniziale.
    
        ![Utilità di avvio delle app Disattese Disattese](images/steamvr-launchers.png)
        
    * Nuova app *360 Video* per l'individuazione di una selezione curata regolarmente di video a 360 gradi.
    * Nuova app *WebVR Showcase* per l'individuazione di una selezione curata regolarmente di esperienze WebVR.
    * La prima volta Windows Mixed Reality i clienti potranno accedere al Casa sulla scogliera e trovarlo precompilato con utilità di avvio di app 3D per alcune delle app immersive e dei giochi preferiti dell'Microsoft Store.
    * Microsoft Edge ora includono un *pulsante* Condividi.
* Menu Azioni rapide: da un'app di realtà mista immersiva, è possibile premere il pulsante Windows per accedere a un nuovo menu di azioni rapide, con accesso semplice al *menu Di Avvio* rapido, all'acquisizione di *foto/video,* alla torcia e alla *home page.* 
* **Supporto per PC di successo:** Windows Mixed Reality visori VR immersive vengono eseguiti su PC con visori VR senza richiedere un emulatore di visualizzazione al termine della configurazione.
* Nuove funzionalità **audio:** è ora possibile eseguire il mirroring dell'audio da un'esperienza Windows Mixed Reality  sia al jack audio (o alle cuffi) nel visore VR che a un dispositivo audio connesso al PC (ad esempio altoparlanti esterni). È stato anche aggiunto un indicatore visivo per il livello del volume nello schermo del visore VR.
* **Altri miglioramenti**
    * Portale realtà mista aggiornamenti vengono ora recapitati tramite il Microsoft Store, consentendo aggiornamenti più rapidi tra le versioni Windows principali. Si noti che questo vale solo per l'app desktop e l'esperienza Windows Mixed Reality visore VR continua a essere aggiornata con il sistema operativo. 
    * Quando i visori VR passano alla sospensione, Windows Mixed Reality le app vengono sospese anziché terminate (fino a Portale realtà mista vengono chiuse).
    
### <a name="for-developers"></a>Per sviluppatori

* **[](/windows/mixed-reality/develop/platform-capabilities-and-apis/qr-code-tracking)** Rilevamento del codice a codici Windows Mixed Reality: abilita il rilevamento del codice a qr nell'app di realtà mista, consentendo ai visori VR immersive di analizzare i codici a barre e segnalarli alle app interessate.
* **Supporto DRM** hardware per le app immersive: gli sviluppatori possono ora richiedere trame backbuffer protette da hardware, se supportate dall'hardware di visualizzazione, consentendo alle applicazioni di usare contenuto protetto da hardware da origini come PlayReady.
* **[Integrare l'interfaccia](/windows/mixed-reality/develop/platform-capabilities-and-apis/mixed-reality-capture-for-developers#integrating-mrc-functionality-from-within-your-app)** utente di acquisizione di realtà mista [nelle](/windows/uwp/audio-video-camera/capture-photos-and-video-with-cameracaptureui) app immersive: gli sviluppatori possono integrare l'acquisizione di realtà mista nelle app usando l'interfaccia utente di acquisizione della fotocamera Windows predefinita con poche righe di codice.

## <a name="new-features-for-hololens"></a>Nuove funzionalità per HoloLens

Il Aggiornamento di Windows 10 (ottobre 2018) è disponibile pubblicamente per tutti HoloLens clienti e include una serie di miglioramenti, ad esempio:

### <a name="for-everyone"></a>Per tutti

* Menu Azioni rapide: da un'app di realtà mista immersiva è possibile premere il pulsante Windows per accedere a un nuovo menu di azioni rapide, con accesso semplice a Avvia la registrazione *di video,* *Foto,* Home di Realtà mista, *Cambia volume* *e Connessione*. 
* **Avviare/arrestare** l'acquisizione video dal menu Avvia o azioni rapide: se si avvia l'acquisizione video dal menu menu Start o dalle azioni rapide, sarà possibile arrestare la registrazione dalla stessa posizione. Non dimenticare che è sempre possibile eseguire questa operazione anche con i comandi vocali.
* Project a un dispositivo abilitato per **Miracast:** Project il contenuto del HoloLens a un dispositivo Surface o a un tv/monitor nelle vicinanze se si usa uno schermo o un adattatore abilitato per Miracast.
* **Nuove notifiche:** consente di visualizzare e rispondere alle notifiche HoloLens, esattamente come in un PC.  
* **Sovrimpressione** utili nelle app immersive di realtà mista: sono ora disponibili sovrimpressione, ad esempio tastiera, finestre di dialogo, selezione file e così via, quando si usano app di realtà mista immersive.
* **Indicatore visivo per** la modifica del volume: quando si usano i pulsanti volume su/giù nel HoloLens verrà visualizzato un indicatore visivo del livello del volume nel visore VR.
* **Nuovi oggetti visivi per l'avvio del** dispositivo: durante il processo di avvio è stato aggiunto un indicatore di caricamento per fornire un feedback visivo sul caricamento del sistema.
* **Condivisione nelle vicinanze:** Windows condivisione nelle vicinanze consente di condividere un'acquisizione con un dispositivo Windows nelle vicinanze.  
* **Condividi da Microsoft Edge:** Microsoft Edge ora include un *pulsante Condividi.* 

### <a name="for-developers"></a>Per sviluppatori

* **[Integrare l'interfaccia](/windows/mixed-reality/develop/platform-capabilities-and-apis/mixed-reality-capture-for-developers#integrating-mrc-functionality-from-within-your-app)** utente di acquisizione di realtà mista [nelle](/windows/uwp/audio-video-camera/capture-photos-and-video-with-cameracaptureui) app immersive: gli sviluppatori possono integrare l'acquisizione di realtà mista nelle app usando l'interfaccia utente di acquisizione della fotocamera Windows predefinita con poche righe di codice.

### <a name="for-commercial-customers"></a>Per i clienti commerciali

* **Abilitare il provisioning post-installazione:** è ora possibile applicare un pacchetto di provisioning di runtime in qualsiasi momento usando Impostazioni.
* **Accesso assegnato con gruppi Azure AD:** è ora possibile usare i gruppi di Azure AD per la configurazione dell'accesso Windows assegnato per configurare una o più app in modalità tutto schermo.
* **Cambio di** pin di accesso al profilo dalla schermata di accesso: l'accesso tramite PIN è ora disponibile per "Altro utente" nella schermata di accesso. 
* **Leggere le informazioni sull'hardware del dispositivo** tramite MDM: gli amministratori IT possono visualizzare e tenere traccia HoloLens numero di serie del dispositivo nella console MDM.
* **Impostare HoloLens nome del dispositivo tramite MDM (ridenominazione):** gli amministratori IT possono visualizzare e rinominare HoloLens dispositivi nella console MDM.

### <a name="for-international-customers"></a>Per i clienti internazionali

È ora possibile usare HoloLens con l'interfaccia utente localizzata per il cinese semplificato o il giapponese, inclusi la tastiera, la dettatura, la sintesi vocale e i comandi vocali localizzati.

## <a name="known-issues"></a>Problemi noti

Abbiamo lavorato sodo per offrire un'esperienza Windows Mixed Reality, ma stiamo ancora verificando alcuni problemi noti. Se si trovano altri utenti, [inviare commenti e suggerimenti.](/windows/mixed-reality/give-us-feedback)

### <a name="hololens"></a>HoloLens
 
#### <a name="after-update"></a>Dopo l'aggiornamento
Quando si usa il Aggiornamento di Windows 10 (ottobre 2018) nell'HoloLens potrebbero verificarsi i problemi HoloLens:
* **Le app possono** terminare in un ciclo di accesso quando vengono avviate da una notifica: alcune app che richiedono l'accesso possono finire in un ciclo di accesso infinito quando vengono avviate da una notifica. Ad esempio, ciò può verificarsi dopo l'installazione dell'app Microsoft Portale aziendale dal Microsoft Store e l'avvio dalla notifica di completamento dell'installazione.
* **La** pagina di accesso dell'app può essere completata con una pagina vuota: in alcuni casi quando viene visualizzata una richiesta di accesso sull'applicazione, al termine la pagina di accesso non viene chiusa e viene invece visualizzata una pagina vuota (nera). È possibile chiudere la pagina vuota o spostarla per individuare l'applicazione sottostante. Ad esempio, questa operazione può verificarsi durante l'accesso durante la registrazione MDM dall'app Impostazioni app. 

## <a name="provide-feedback-and-report-issues"></a>Inviare commenti e suggerimenti e segnalare i problemi

Usare [l'app Hub di Feedback nel pc HoloLens](/windows/mixed-reality/give-us-feedback) o Windows 10 per inviare commenti e suggerimenti e segnalare problemi. L Hub di Feedback garantisce che tutte le informazioni di diagnostica necessarie siano incluse per consentire ai tecnici di eseguire rapidamente il debug e risolvere il problema.

>[!NOTE]
>Assicurarsi di accettare il prompt che chiede se si desidera Hub di Feedback accedere alla cartella Documenti (selezionare **Sì** quando richiesto).

## <a name="prior-release-notes"></a>Note sulla versione precedente

* [Note sulla versione - Aprile 2018](release-notes-april-2018.md)
* [Note sulla versione - ottobre 2017](release-notes-october-2017.md)
* [Note sulla versione - agosto 2016](release-notes-august-2016.md)
* [Note sulla versione - maggio 2016](release-notes-may-2016.md)
* [Note sulla versione - marzo 2016](release-notes-march-2016.md)

## <a name="see-also"></a>Vedi anche
* [Supporto per visori VR immersive (collegamento esterno)](./troubleshooting-windows-mixed-reality.md)
* [HoloLens (collegamento esterno)](https://support.microsoft.com/products/hololens)
* [Installare gli strumenti](/windows/mixed-reality/develop/install-the-tools)
* [Commenti e suggerimenti](/windows/mixed-reality/give-us-feedback)
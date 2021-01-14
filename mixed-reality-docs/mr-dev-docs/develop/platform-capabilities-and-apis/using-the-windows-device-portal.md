---
title: Uso del Portale di dispositivi di Windows
description: Informazioni su come configurare e gestire un dispositivo in remoto tramite Wi-Fi o USB usando il Portale di dispositivi di Windows.
author: hamalawi
ms.author: moelhama
ms.date: 08/03/2020
ms.topic: article
keywords: Portale di dispositivi di Windows, HoloLens
ms.localizationpriority: high
ms.openlocfilehash: 75eda2775486b1ace82b574816db34a2f895c80b
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2021
ms.locfileid: "98007791"
---
# <a name="using-the-windows-device-portal"></a>Uso del Portale di dispositivi di Windows

<table>
<tr>
<th>Funzionalità</th><th style="width:150px"><a href="../../hololens-hardware-details.md">HoloLens (prima generazione)</a></th><th style="width:150px">HoloLens 2</th><th style="width:150px">
</tr><tr>
<td> Portale di dispositivi di Windows</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"></td>
</tr>
</table>

Il Portale di dispositivi di Windows per HoloLens consente di configurare e gestire un dispositivo in remoto tramite Wi-Fi o USB. Device Portal è un server Web in HoloLens a cui è possibile connettersi da un browser Web nel PC. Il Portale di dispositivi include molti strumenti che ti consentono di gestire HoloLens, nonché di eseguire il debug delle app e ottimizzarle.

Questa documentazione è specifica del Portale di dispositivi di Windows per HoloLens. Per usare il Portale di dispositivi di Windows per desktop (tra cui Windows Mixed Reality), vedi [Panoramica del Portale di dispositivi di Windows](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal).

## <a name="setting-up-hololens-to-use-windows-device-portal"></a>Configurazione di HoloLens per l'uso del Portale di dispositivi di Windows

1. Accendi HoloLens e il dispositivo.
2. Usare il [gesto Start](https://docs.microsoft.com/hololens/hololens2-basic-usage#start-gesture) per HoloLens 2 o [aprire la mano a fiore](https://docs.microsoft.com/hololens/hololens1-basic-usage#open-the-start-menu-with-bloom) in HoloLens (prima generazione) per avviare il menu principale. 
3. Fissare il riquadro **Settings** (Impostazioni) ed eseguire una [simulazione del tocco](https://docs.microsoft.com/hololens/hololens1-basic-usage#select-holograms-with-gaze-and-air-tap) in HoloLens (prima generazione). È anche possibile selezionarlo in HoloLens 2 [toccandolo o usando un raggio della mano](https://docs.microsoft.com/hololens/hololens2-basic-usage). 
4. Scegli la voce di menu **Aggiorna**.
5. Scegli la voce di menu **Per gli sviluppatori**.
6. Abilita **Modalità sviluppatore**.

> [!IMPORTANT]
> Se non si è un amministratore ma in modalità multiutente, l'opzione per abilitare la modalità sviluppatore potrebbe non essere disponibile. Verificare di essere un **[amministratore sul dispositivo](https://docs.microsoft.com/hololens/security-adminless-os)** .

7. [Scorri verso il basso](../../design/gaze-and-commit.md#composite-gestures) e abilita **Portale dispositivi**.
8. Se si configura il Portale di dispositivi di Windows in modo da poter distribuire le app in questo dispositivo HoloLens tramite USB o Wi-Fi, selezionare **Associa** per [generare un PIN di associazione](using-visual-studio.md). Lascia l'app Impostazioni con la finestra popup del PIN aperta finché non immetti il PIN in Visual Studio nel corso della prima distribuzione.

![Abilitazione della modalità sviluppatore nell'app Impostazioni per Windows Holographic](images/using-windows-portal-img-01.jpg)

## <a name="connecting-over-wi-fi"></a>Connessione tramite Wi-Fi

1. [Connetti HoloLens alla rete Wi-Fi](../../connecting-to-wi-fi-on-hololens.md).
2. Cerca l'indirizzo IP del dispositivo in uno di questi modi:
   * Passa a **Impostazioni > Rete e Internet > Wi-Fi > Opzioni avanzate**.
   * Passa a **Impostazioni > Rete e Internet** e seleziona **Proprietà hardware**.

![Impostazioni HoloLens 2](images/using-windows-portal-img-02.jpg)

3. Da un Web browser sul PC vai a https://<INDIRIZZO_IP_HOLOLENS>
   * Il browser visualizzerà il messaggio seguente: "Si è verificato un problema con il certificato di sicurezza del sito Web" perché il certificato, rilasciato al Portale di dispositivi, è un certificato di prova. Per ora è possibile ignorare questo errore relativo al certificato e continuare.

## <a name="connecting-over-usb"></a>Connessione tramite USB

1. [Installare gli strumenti](../install-the-tools.md) necessari in modo da avere Visual Studio con gli strumenti di sviluppo per Windows 10 installati nel PC per abilitare la connettività USB.

> [!IMPORTANT]
> In caso di problemi relativi alla connettività USB, verificare che il componente facoltativo Connettività dispositivi USB sia installato come parte del **[pacchetto di strumenti di Visual Studio](../install-the-tools.md#installation-checklist)** .

2. Connetti HoloLens al PC con un cavo micro USB per HoloLens (prima generazione) o USB-C per HoloLens 2.
3. Da un Web browser nel PC vai a [https://127.0.0.1:10080](https://127.0.0.1:10080).

### <a name="moving-files-over-usb"></a>Spostamento di file tramite USB

È possibile spostare file dal PC a HoloLens senza alcuna configurazione aggiuntiva.
1. Collegare il PC a HoloLens tramite un cavo USB
2. Trascinare i file in **PC\\[Nome_dispositivo_HoloLens]\Internal Storage** sul desktop
3. Aprire il menu **Start** e selezionare **Tutte le app > Esplora file** su HoloLens

> [!NOTE]
> Per individuare i file potrebbe essere necessario selezionare **Questo dispositivo** sul lato sinistro del pannello per uscire da "Usati di recente". 

## <a name="connecting-to-an-emulator"></a>Connessione a un emulatore

Puoi usare Device Portal anche con un emulatore. Per connetterti al Portale di dispositivi, usa la [barra degli strumenti](using-the-hololens-emulator.md). Selezionare questa icona: ![Icona di apertura del Portale di dispositivi](images/emulator-deviceportal.png) **Open Device Portal** (Apri Portale di dispositivi): apre il Portale di dispositivi di Windows per il sistema operativo di HoloLens nell'emulatore.

## <a name="creating-a-username-and-password"></a>Creazione di un nome utente e di una password

![Configurare l'accesso al Portale di dispositivi di Windows](images/windows-device-portal-credentials-reset-page-1000px.png)<br>
*Configurare l'accesso al Portale di dispositivi di Windows*

La prima volta che ci si connette al Portale di dispositivi in HoloLens è necessario creare un nome utente e una password.
1. In un Web browser nel PC immetti l'indirizzo IP di HoloLens. Viene visualizzata la pagina di configurazione dell'accesso.
2. Selezionare o toccare **Request pin** (Richiedi PIN) e guardare lo schermo HoloLens per ottenere il PIN generato.
3. Immetti il PIN nella casella di testo **PIN displayed on your device** (PIN visualizzato sul dispositivo).
4. Immettere il nome utente che verrà usato per la connessione al Portale di dispositivi. Non deve necessariamente essere il nome di un account Microsoft o un nome di dominio.
5. Immetti una password e confermala. La password deve contenere almeno sette caratteri. Non deve necessariamente essere la password di un account Microsoft o una password di dominio.
6. Fai clic su **Pair** (Associa) per connetterti al Portale di dispositivi di Windows in HoloLens.

Per modificare il nome utente o la password in qualsiasi momento, puoi ripetere questo processo dalla pagina della sicurezza del dispositivo passando a https://<INDIRIZZO_IP_HOLOLENS>/devicepair.htm.

## <a name="security-certificate"></a>Certificato di sicurezza

Se visualizzi un messaggio di errore di certificato nel browser, puoi correggerlo creando una relazione di trust con il dispositivo.

Ogni dispositivo HoloLens genera un certificato autofirmato per la connessione SSL. Per impostazione predefinita, questo certificato non è ritenuto attendibile dal Web browser del PC e potresti ricevere un messaggio di errore. È possibile connettersi al dispositivo in modo sicuro scaricando il certificato da HoloLens (tramite USB o una rete Wi-Fi considerata attendibile) e impostandolo come attendibile nel PC.
1. **Assicurati di essere connesso a una rete protetta (USB o una rete Wi-Fi considerata attendibile).**
2. Scarica il certificato del dispositivo dalla pagina relativa alla sicurezza nel Portale di dispositivi.
   * Vai a https://<INDIRIZZO_IP_HOLOLENS>/devicepair.htm
   * Apri il nodo da System (Sistema) > Preferences (Preferenze). 
   * Scorrere verso il basso fino a Device Security (Sicurezza dispositivo) e selezionare il pulsante "Download this device's certificate" (Scarica certificato dispositivo).
3. Installa il certificato nell'archivio "Autorità di certificazione radice disponibile nell'elenco locale" nel PC.
   * Dal menu Windows digita: Gestisci certificati computer e avvia l'applet.
   * Espandi la cartella **Autorità di certificazione radice attendibili**.
   * Selezionare la cartella **Certificati**.
   * Scegli Tutte le attività > Importa... dal menu Azione.
   * Completa l'Importazione guidata certificati usando il file di certificato che hai scaricato da Device Portal.
4. Riavvia il browser.

>[!NOTE]
> Questo certificato sarà considerato attendibile solo per il dispositivo e l'utente dovrà eseguire di nuovo il processo se viene eseguito il flashing del dispositivo.

## <a name="sideloading-applications"></a>Trasferimento delle applicazioni in locale

### <a name="installing-a-certificate"></a>Installazione di un certificato

1. Nel Portale di dispositivi di Windows passare alla pagina di gestione **Apps** (App)
2. Nella sezione Deploy apps (Distribuzione delle app) selezionare **Install Certificate** (Installa certificato)
3. In Select certificate file (.cer) used to sign an app package (Selezionare il file di certificato (.cer) usato per firmare un pacchetto dell'app) selezionare Choose File (Scegli file) e passare al certificato associato al pacchetto dell'app da trasferire localmente
4. Fare clic su **Install** (Installa) per avviare l'installazione

![Screenshot della pagina di gestione Apps aperta nel Portale di dispositivi di Windows](images/sideloading-1.png)

### <a name="installing-an-app"></a>Installazione di un'app

> [!NOTE]
> Affinché un'app venga installata correttamente tramite il Portale di dispositivi, deve essere firmata da un certificato. Prima di tentare di installare l'app, è necessario che il certificato sia installato nel dispositivo. Per istruzioni, vedere la [sezione precedente](#installing-a-certificate).

1. Dopo aver [creato un pacchetto dell'app in Visual Studio](using-visual-studio.md), è possibile installarlo in remoto nel dispositivo a partire dai file generati:

![Screenshot del contenuto dei file del pacchetto dell'app](images/sideloading-2.png)

2. Nel Portale di dispositivi di Windows passare alla pagina di gestione **Apps** (App)
3. Nella sezione **Deploy apps** (Distribuzione delle app) selezionare **Local Storage** (Archiviazione locale)
4. In Select the application package (Selezionare il pacchetto dell'applicazione) selezionare Choose File (Scegli file) e passare al pacchetto dell'app da trasferire localmente
5. Selezionare le rispettive caselle se si vuole installare pacchetti facoltativi o framework insieme all'installazione dell'app e fare clic su **Next** (Avanti):

![Screenshot della pagina di gestione Apps aperta nel Portale di dispositivi di Windows con la scheda Local Storage evidenziata](images/sideloading-3.png)

6. Fare clic su **Install** (Installa) per avviare l'installazione
 
![Screenshot della pagina di gestione Apps aperta nel Portale di dispositivi di Windows con l'indicazione dell'installazione completata](images/sideloading-4.png) 

Al termine dell'installazione, tornare alla pagina **Tutte le app** in HoloLens e avviare la nuova applicazione installata.

## <a name="device-portal-pages"></a>Pagine di Device Portal

### <a name="home"></a>Home

![Home page del Portale di dispositivi di Windows in Microsoft HoloLens](images/using-windows-portal-img-04.png)<br>
*Home page del Portale di dispositivi di Windows in Microsoft HoloLens*

La pagina iniziale di una sessione di Device Portal è la home page. Puoi accedere alle altre pagine dalla barra di spostamento sul lato sinistro della home page.

La barra degli strumenti nella parte superiore della pagina permette di accedere allo stato e alle funzionalità che usi di frequente.
* **Online**: indica se il dispositivo è connesso alla rete Wi-Fi.
* **Shutdown** (Arresta): spegne il dispositivo.
* **Restart** (Riavvia): spegne e quindi riaccende il dispositivo.
* **Security** (Sicurezza): apre la pagina Device Security (Sicurezza dispositivo).
* **Cool** (Temperatura): indica la temperatura del dispositivo.
* **A/C** (Alimentazione): indica se il dispositivo è collegato e in carica.
* **Help** (Guida): apre la pagina della documentazione dell'interfaccia REST.

La home page mostra le informazioni seguenti:
* **Device Status** (Stato dispositivo): monitora lo stato del dispositivo e segnala eventuali errori critici.
* **Windows information** (Informazioni su Windows): mostra il nome del dispositivo HoloLens e la versione attualmente installata di Windows.
* La sezione **Preferences** contiene le impostazioni seguenti:
   * **IPD** (Distanza interpupillare): imposta la distanza interpupillare, ovvero la distanza in millimetri tra il centro delle pupille dell'utente quando guarda dritto davanti a sé. L'impostazione ha effetto immediatamente. Il valore predefinito è stato calcolato automaticamente quando hai configurato il dispositivo.
   * **Device name** (Nome dispositivo): consente di assegnare un nome a HoloLens. Riavviare il dispositivo dopo aver modificato questo valore per renderlo effettivo. Dopo aver fatto clic su **Save** (Salva), viene visualizzata una finestra di dialogo che chiede se vuoi riavviare il dispositivo subito o in seguito.
   * **Sleep settings** (Impostazioni sospensione): imposta l'intervallo di tempo di attesa prima che il dispositivo passi allo stato di sospensione quando è collegato e quando funziona a batteria.

### <a name="3d-view"></a>3D View

![Pagina 3D View (Visualizzazione 3D) del Portale di dispositivi di Windows in Microsoft HoloLens](images/using-windows-portal-img-05.png)<br>
*Pagina 3D View (Visualizzazione 3D) del Portale di dispositivi di Windows in Microsoft HoloLens*

Usa la pagina 3D View per osservare in che modo HoloLens interpreta l'ambiente circostante. Puoi spostarti nella visualizzazione usando il mouse:
* Rotazione: clic con il pulsante sinistro del mouse.
* Panoramica: clic con il pulsante destro del mouse.
* Zoom: scorrimento della rotellina del mouse.
* **Tracking options** (Opzioni di tracciatura)
   * Abilita la tracciatura visiva selezionando **Force visual tracking** (Forza tracciatura visiva). 
   * **Pause** (Sospendi) arresta la tracciatura visiva.
* **View options** (Opzioni di visualizzazione): consente di impostare le opzioni nella visualizzazione 3D:
  * **Tracking** (Tracciatura): indica se è attiva la tracciatura visiva.
  * **Show floor** (Mostra pavimento): visualizza un pavimento a scacchi.
  * **Show frustum** (Mostra tronco): mostra il tronco di visualizzazione.
  * **Show stabilization plane** (Mostra piano di stabilizzazione): visualizza il piano usato da HoloLens per stabilizzare il movimento.
  * **Show mesh** (Mostra mesh): visualizza la mesh di mapping spaziale che rappresenta l'ambiente circostante.
  * **Show spatial anchors** (Mostra ancoraggi nello spazio): visualizza gli ancoraggi nello spazio per l'app attiva. Selezionare il pulsante Update (Aggiorna) per ottenere e aggiornare gli ancoraggi.
  * **Show details** (Mostra dettagli): visualizza la posizione delle mani, i quaternioni di rotazione della testa e il vettore di origine del dispositivo man mano che cambiano in tempo reale.
  * **Full screen button** (Pulsante schermo intero): mostra la visualizzazione 3D in modalità schermo intero. Premi ESC per chiudere la visualizzazione a schermo intero.
* **Surface reconstruction** (Ricostruzione superficie): selezionare o toccare **Update** (Aggiorna) per visualizzare la mesh di mapping spaziale più recente dal dispositivo. Un passaggio completo può richiedere tempo, fino ad alcuni secondi. La mesh non viene aggiornata automaticamente nella visualizzazione 3D. Per ottenere la mesh più recente dal dispositivo, è necessario selezionare **Update** (Aggiorna) manualmente. Selezionare **Save** (Salva) per salvare la mesh di mapping spaziale corrente come file obj nel PC.
* **Spatial anchors** (Ancoraggi nello spazio): selezionare Update (Aggiorna) per visualizzare o aggiornare gli ancoraggi nello spazio per l'app attiva.

### <a name="map-manager"></a>Map Manager (Gestore mappe)

Map Manager (Gestore mappe) consente di condividere le mappe tra più dispositivi, che possono essere usati per configurare esperienze condivise per i clienti di servizi di intrattenimento basato sulla posizione. Lo strumento consente di importare ed esportare mappe di sistema e ancoraggi.  

Per accedere a Map Manager (Gestore mappe), eseguire l'accesso al Portale di dispositivi e selezionare **Mixed Reality -> Map Manager** (Realtà mista -> Gestore mappe): 

![Pagina Map Manager (Gestore mappe) nel Portale di dispositivi di Windows](images/using-windows-portal-img-06.png)
*Pagina Map Manager (Gestore mappe) nel Portale di dispositivi di Windows*

#### <a name="exporting-and-importing-maps"></a>Esportazione e importazione di mappe

Per esportare le mappe, selezionare **Export System Map & Anchors** (Esporta mappa di sistema e ancoraggi). L'esportazione della mappa potrebbe richiedere 30-60 secondi. Al termine, il file verrà scaricato nel browser.  

Per importare le mappe e gli ancoraggi, selezionare rispettivamente **Upload a map file** (Carica un file di mappe) e **Upload an anchor file** (Carica un file di ancoraggi) e scegliere un file di mappe o ancoraggi precedentemente esportato. Il file di mappe o ancoraggi caricato può provenire da qualsiasi altro dispositivo HoloLens. 

> [!NOTE]
> In HoloLens è anche possibile importare ed esportare il database di mapping spaziale. Questo non è invece possibile nei dispositivi non HoloLens.  


### <a name="mixed-reality-capture"></a>Mixed Reality Capture

![Pagina Mixed Reality Capture (Acquisizione realtà mista) del Portale di dispositivi di Windows in Microsoft HoloLens](images/using-windows-portal-img-07.png)<br>
*Pagina Mixed Reality Capture (Acquisizione realtà mista) del Portale di dispositivi di Windows in Microsoft HoloLens*

Usa la pagina Mixed Reality Capture per salvare flussi multimediali da HoloLens.
* **Impostazioni di acquisizione**: controlla i flussi multimediali acquisiti selezionando le impostazioni seguenti:
  * **Holograms** (Ologrammi): acquisisce il contenuto olografico nel flusso video. Il rendering degli ologrammi avviene in modalità mono, non in stereo.
  * **PV camera** (Fotocamera/videocamera): acquisisce il flusso video dalla fotocamera/videocamera.
  * **Mic Audio** (Audio microfoni): acquisisce l'audio dal gruppo di microfoni.
  * **App Audio** (Audio app): acquisisce l'audio dall'app attualmente in esecuzione.
  * **Render from Camera** (Rendering dalla fotocamera): allinea l'acquisizione dal punto di vista della fotocamera/videocamera, se [supportato dall'app in esecuzione](mixed-reality-capture-for-developers.md#render-from-the-pv-camera-opt-in) (solo HoloLens 2).
  * **Live preview quality** (Qualità anteprima dinamica): consente di selezionare la risoluzione dello schermo, la frequenza dei fotogrammi e la frequenza di streaming per l'anteprima dinamica.
* **Impostazioni audio** (solo HoloLens 2):
  * **Audio Media Category** (Categoria supporto audio): consente di selezionare la categoria usata durante l'elaborazione del microfono. **Default** (Predefinita) include una parte dell'ambiente, mentre **Communications** (Comunicazioni) applica la cancellazione del rumore di fondo.
  * **App Audio Gain** (Guadagno audio app): guadagno applicato al volume dell'audio dell'app.
  * **Mic Audio Gain** (Guadagno audio microfoni): guadagno applicato al volume dell'audio dei microfoni.
* **Impostazioni foto e video** (HoloLens 2, versione 2004 o successive):
  * **Capture Profile** (Profilo acquisizione): consente di selezionare il profilo usato per l'acquisizione di foto e video. Il profilo determina quali risoluzioni e frequenze fotogrammi sono disponibili.
  * **Photo Resolution** (Risoluzione foto): risoluzione con cui verrà scattata la foto.
  * **Video Resolution and Frame-rate** (Risoluzione video e frequenza fotogrammi): risoluzione e frequenza fotogrammi con cui verrà acquisito il video.
  * **Video Stabilization Buffer** (Buffer di stabilizzazione video): dimensioni del buffer usate durante l'acquisizione di un video. Maggiore è il valore, più è in grado di compensare i movimenti rapidi.
* Selezionare o toccare il pulsante **Live preview** (Anteprima dinamica) per visualizzare il flusso di acquisizione. **Stop live preview** (Arresta anteprimna dinamica) arresta il flusso di acquisizione.
* Selezionare o toccare **Record** (Registra) per avviare la registrazione del flusso di realtà mista, usando le impostazioni specificate. **Stop recording** (Arresta registrazione) termina la registrazione e la salva.
* Selezionare o toccare **Take photo** (Scatta foto) per acquisire un fermo immagine dal flusso di acquisizione.
* Selezionare o toccare **Restore Default Settings** (Ripristina impostazioni predefinite) per ripristinare le impostazioni predefinite per audio, foto e video.
* **Videos and photos** (Video e foto): mostra un elenco di acquisizioni di foto e video create nel dispositivo.

Tutte le impostazioni di questa pagina si applicano alle acquisizioni effettuate con il Portale di dispositivi di Windows. Alcune si applicano anche a MRC di sistema, inclusi il menu Start, i pulsanti hardware, i comandi vocali globali, Miracast e ai registratori MRC personalizzati.

|  Impostazione  |  Si applica al sistema MRC  |  Si applica ai registratori MRC personalizzati |
|----------|----------|----------|
|  Holograms (Ologrammi)  |  No  |  No |
|  PV camera (Fotocamera/videocamera)  |  No  |  No |
|  Mic Audio (Audio microfoni)  |  No  |  No |
|  App Audio (Audio app)  |  No  |  No |
|  Render from Camera (Rendering dalla fotocamera)  |  Sì    |  Yes (Sì) (è possibile eseguirne l'override) |
|  Live preview quality (Qualità anteprima dinamica)  |  No  |  No |
|  Audio Media Category (Categoria supporto audio)  |  Sì  |  No |
|  App Audio Gain (Guadagno audio app)  |  Sì  |  Yes (Sì) (è possibile eseguirne l'override) |
|  Mic Audio Gain (Guadagno audio microfoni)  |  Sì  |  Yes (Sì) (è possibile eseguirne l'override) |
|  Capture Profile (Profilo acquisizione)  |  Sì  |  No |
|  Photo Resolution (Risoluzione foto)  |  Sì  |  No |
|  Video Resolution and Frame-rate (Risoluzione video e frequenza fotogrammi)  |  Sì  |  No |
|  Video Stabilization Buffer (Buffer di stabilizzazione video)  |  Sì  |  Yes (Sì) (è possibile eseguirne l'override) |

> [!NOTE]
> Esistono [limitazioni per le acquisizioni simultanee in realtà mista](mixed-reality-capture-for-developers.md#simultaneous-mrc-limitations):
> * Se un'app tenta di accedere alla videocamera/fotocamera mentre il Portale di dispositivi sta registrando un video, la registrazione video si arresterà.
>   * HoloLens 2 non arresterà la registrazione video se l'app accede alla fotocamera/videocamera con la modalità SharedReadOnly.
> * Se un'app usa attivamente la fotocamera/videcamera, il Portale di dispositivi di Windows può scattare una foto o registrare un video.
> * Streaming live:
>   * HoloLens (prima generazione) impedisce a un'app di accedere alla fotocamera/videocamera durante lo streaming live dal Portale di dispositivi di Windows.
>   * Se un'app usa attivamente la fotocamera/videocamera, HoloLens (prima generazione) non riuscirà a eseguire lo streaming live.
>   * HoloLens 2 arresta automaticamente lo streaming live quando un'app tenta di accedere alla fotocamera/videocamera in modalità ExclusiveControl.
>   * HoloLens 2 è in grado di avviare uno streaming live mentre un'app usa attivamente la fotocamera/videocamera.

### <a name="performance-tracing"></a>Performance Tracing (Traccia prestazioni)

![Pagina Performance Tracing (Traccia prestazioni) del Portale di dispositivi di Windows in Microsoft HoloLens](images/using-windows-portal-img-08.png)<br>
*Pagina Performance Tracing (Traccia prestazioni) del Portale di dispositivi di Windows in Microsoft HoloLens*

Questa pagina acquisisce le tracce [Windows Performance Recorder](https://msdn.microsoft.com/library/windows/hardware/hh448205.aspx) (WPR) da HoloLens.
* **Available profiles** (Profili disponibili): selezionare il profilo WPR dall'elenco a discesa e selezionare o toccare **Start** per avviare il processo di traccia.
* **Custom profiles** (Profili personalizzati): selezionare o toccare **Browse** (Sfoglia) per scegliere un profilo WPR dal PC. Selezionare o toccare **Upload and start** (Carica e avvia) per avviare il processo di traccia.

Per arrestare la traccia, selezionare il collegamento di arresto. Rimani in questa pagina fino a quando non viene completato il download del file di traccia.

I file ETL acquisiti possono essere aperti per l'analisi in [Windows Performance Analyzer](https://msdn.microsoft.com/library/windows/hardware/hh448170.aspx).

### <a name="processes"></a>Processi

![Pagina Processes (Processi) del Portale di dispositivi di Windows in Microsoft HoloLens](images/using-windows-portal-img-09.png)<br>
*Pagina Processes (Processi) del Portale di dispositivi di Windows in Microsoft HoloLens*

La pagina dei processi mostra i dettagli sui processi attualmente in esecuzione. Sono inclusi sia processi di sistema sia app.

### <a name="system-performance"></a>System Performance

![Pagina System Performance (Prestazioni sistema) del Portale di dispositivi di Windows in Microsoft HoloLens](images/using-windows-portal-img-10.png)<br>
*Pagina System Performance (Prestazioni sistema) del Portale di dispositivi di Windows in Microsoft HoloLens*

La pagina delle prestazioni mostra grafici in tempo reale con informazioni di diagnostica di sistema, come consumo energetico, frequenza dei fotogrammi e carico della CPU.

Ecco le metriche disponibili:
* **SoC power** (Alimentazione SoC): utilizzo istantaneo dell'alimentazione SoC (System-on-Chip), misurato in media per un minuto
* **System power** (Alimentazione sistema): utilizzo istantaneo dell'alimentazione di sistema, misurato in media per un minuto
* **Frame rate** (Frequenza fotogrammi): fotogrammi al secondo, VBlank persi al secondo e VBlank persi consecutivi
* **GPU**: utilizzo del motore GPU, percentuale del totale disponibile
* **CPU**: percentuale del totale disponibile
* **I/O**: letture e scritture
* **Rete**: dati ricevuti e inviati
* **Memory** (Memoria): memoria totale, in uso, riservata disponibile, di paging e non di paging

### <a name="apps"></a>App

![Pagina Apps (App) del Portale di dispositivi di Windows in Microsoft HoloLens](images/using-windows-portal-img-11.png)<br>
*Pagina Apps (App) del Portale di dispositivi di Windows in Microsoft HoloLens*

Gestisce le app installate in HoloLens.
* **Installed apps** (App installate): consente di rimuovere e avviare le app.
* **Running apps** (App in esecuzione): elenca le app attualmente in esecuzione.
* **Install app** (App di installazione): consente di selezionare pacchetti di app da installare da una cartella nel computer o in rete.
* **Dependency** (Dipendenza): consente di aggiungere dipendenze per l'app che si intende installare.
* **Deploy** (Distribuzione): consente di distribuire l'app selezionata e le dipendenze in HoloLens.

### <a name="app-crash-dumps"></a>App Crash Dumps (Dump di arresto anomalo app)

![Pagina App Crash Dumps (Dump di arresto anomalo app) del Portale di dispositivi di Windows in Microsoft HoloLens](images/using-windows-portal-img-12.png)<br>
*Pagina App Crash Dumps (Dump di arresto anomalo app) del Portale di dispositivi di Windows in Microsoft HoloLens*

In questa pagina puoi raccogliere i dump di arresto anomalo del sistema per le tue app trasferite localmente. Seleziona la casella di controllo **Crash Dumps Enabled** (Dump di arresto anomalo abilitati) per ogni app per cui vuoi raccogliere i dump di arresto anomalo. Torna in questa pagina per raccogliere i dump di arresto anomalo del sistema. I file dump possono essere [aperti in Visual Studio per il debug](https://msdn.microsoft.com/library/d5zhxt22.aspx).

### <a name="file-explorer"></a>Esplora file

![Pagina File Explorer (Esplora file) del Portale di dispositivi di Windows in Microsoft HoloLens](images/using-windows-portal-img-13.png)<br>
*Pagina File Explorer (Esplora file) del Portale di dispositivi di Windows in Microsoft HoloLens*

Usa la pagina di esplorazione file per esplorare, caricare e scaricare i file. Puoi usare i file nella cartella Documenti, nella cartella Immagini e nelle cartelle di archiviazione locale per le app distribuite da Visual Studio o dal Portale di dispositivi.

### <a name="kiosk-mode"></a>Modalità tutto schermo

>[!NOTE]
>La modalità tutto schermo è disponibile solo con [Microsoft HoloLens Commercial Suite](../../commercial-features.md).

![Pagina della modalità tutto schermo nel Portale di dispositivi di Windows su Microsoft HoloLens](images/using-windows-portal-img-14.png)

Per istruzioni aggiornate sull'abilitazione della modalità tutto schermo tramite il Portale di dispositivi di Windows, vedi l'articolo [Configurare HoloLens in modalità tutto schermo](https://docs.microsoft.com/hololens/hololens-kiosk#set-up-kiosk-mode-using-the-windows-device-portal-windows-10-version-1607-and-version-1803) in Windows IT Pro Center.

### <a name="logging"></a>Registrazione

![Pagina Logging (Registrazione) del Portale di dispositivi di Windows in Microsoft HoloLens](images/using-windows-portal-img-15.png)<br>
*Pagina Logging (Registrazione) del Portale di dispositivi di Windows in Microsoft HoloLens*

Questa pagina consente di gestire in tempo reale Event Tracing for Windows (ETW) in HoloLens.

Seleziona **Hide providers** (Nascondi provider) per visualizzare solo l'elenco **Events** (Eventi).
* **Registered providers** (Provider registrati): consente di selezionare il provider ETW e il livello di traccia. Il valore del livello di traccia può indicare una delle situazioni seguenti:
   1. Chiusura o terminazione anomala
   2. Errori gravi
   3. Avvisi
   4. Avvisi non di errore

Selezionare o toccare **Enable** (Abilita) per avviare il processo di traccia. Il provider viene aggiunto all'elenco a discesa **Enabled Providers**.
* **Custom providers** (Provider personalizzati): consente di selezionare un provider ETW personalizzato e il livello di traccia. Identifica il provider tramite il relativo GUID. Non includere parentesi nel GUID.
* **Enabled providers** (Provider abilitati): elenca i provider abilitati. Seleziona un provider nell'elenco a discesa e tocca o fai clic su **Disable** per arrestare la traccia. Tocca o fai clic su **Stop** per sospendere tutte le operazioni di traccia.
* **Providers history** (Cronologia di provider): mostra i provider ETW che sono stati abilitati durante la sessione corrente. Tocca o fai clic su **Enable** per attivare un provider disabilitato. Tocca o fai clic su **Clear** per cancellare la cronologia.
* **Events** (Eventi): elenca in formato tabella gli eventi ETW dei provider selezionati. La tabella viene aggiornata in tempo reale. Sotto la tabella fai clic sul pulsante **Clear** per eliminare tutti gli eventi ETW dalla tabella. In questo modo, non viene disabilitato alcun provider. Puoi fare clic su **Save to file** per esportare gli eventi ETW attualmente raccolti in un file CSV locale.
* **Filters** (Filtri): consente di filtrare gli eventi ETW raccolti in base all'ID, alla parola chiave, al livello, al nome del provider, al nome dell'attività o al testo. È possibile combinare diversi criteri:
   1. Per i criteri che si applicano alla stessa proprietà, vengono visualizzati gli eventi che possono soddisfare uno qualsiasi dei criteri.
   2. Per i criteri che si applicano a una proprietà diversa, gli eventi devono soddisfare tutti i criteri.

È ad esempio possibile specificare i criteri *(Nome attività contiene 'Foo' o 'Bar') AND (Testo contiene 'errore' o 'avviso')*

### <a name="simulation"></a>Di simulazione

![Pagina Simulation (Simulazione) del Portale di dispositivi di Windows in Microsoft HoloLens](images/using-windows-portal-img-16.png)<br>
*Pagina Simulation (Simulazione) del Portale di dispositivi di Windows in Microsoft HoloLens*

Ti permette di registrare e riprodurre dati di input per il testing.
* **Capture room** (Ambiente acquisizione): opzione usata per scaricare il file di un ambiente simulato che contiene la mesh di mapping spaziale per l'ambiente circostante dell'utente. Assegnare un nome alla stanza e quindi fare clic su **Capture** (Acquisisci) per salvare i data come file con estensione xef nel PC. Questo file può essere caricato nell'emulatore di HoloLens.
* **Recording** (Registrazione): consente di controllare i flussi da registrare e di assegnare un nome alla registrazione. Tocca o fai clic su **Record** (Registra) per avviare la registrazione. Eseguire le azioni con HoloLens e quindi fare clic su **Stop** (Arresta) per salvare i dati come file con estensione xef nel PC. Questo file può essere caricato nell'emulatore di HoloLens o nel dispositivo stesso.
* **Playback** (Riproduzione): tocca o fai clic su **Upload recording** (Carica registrazione) per selezionare un file XEF nel PC e inviare i dati a HoloLens.
* **Control mode** (Modalità di controllo): seleziona **Default** (Predefinita) o **Simulation** (Simulazione) dall'elenco a discesa e quindi tocca o fai clic sul pulsante **Set** (Imposta) per selezionare la modalità in HoloLens. Scegliendo "Simulation" vengono disabilitati i sensori reali in HoloLens e al loro posto vengono usati i dati di simulazione caricati. Se si passa alla modalità "Simulation" (Simulazione), HoloLens non risponderà all'utente reale fino a quando non verrà ripristinata la modalità "Default" (Predefinita).

### <a name="networking"></a>Funzionalità di rete

![Pagina Networking (Funzionalità di rete) del Portale di dispositivi di Windows in Microsoft HoloLens](images/using-windows-portal-img-17.png)<br>
*Pagina Networking (Funzionalità di rete) del Portale di dispositivi di Windows in Microsoft HoloLens*

Gestisce le connessioni Wi-Fi in HoloLens.
* **WiFi adapters** (Schede Wi-Fi): consente di selezionare una scheda e un profilo Wi-Fi usando i controlli a discesa. Tocca o fai clic su **Connect** (Connetti) per usare la scheda selezionata.
* **Available networks** (Reti disponibili): elenca le reti Wi-Fi a cui può connettersi HoloLens. Tocca o fai clic su **Refresh** (Aggiorna) per aggiornare l'elenco.
* **IP configuration** (Configurazione IP): mostra l'indirizzo IP e altri dettagli della connessione di rete.

### <a name="virtual-input"></a>Virtual Input

![Pagina Virtual Input (Input virtuale) del Portale di dispositivi di Windows in Microsoft HoloLens](images/using-windows-portal-img-18.png)<br>
*Pagina Virtual Input (Input virtuale) del Portale di dispositivi di Windows in Microsoft HoloLens*

Invia l'input da tastiera dal computer remoto a HoloLens.

Tocca o fai clic sull'area al di sotto di **Virtual keyboard** (Tastiera virtuale) per abilitare l'invio delle pressioni di tasti a HoloLens. Digita nella casella di testo **Input text** (Testo di input) e tocca o fai clic su **Send** (Invia) per inviare le pressioni di tasti all'app attiva.

## <a name="device-portal-rest-apis"></a>API REST del Portale di dispositivi

Tutti gli elementi del Portale di dispositivi sono basati su [API REST](device-portal-api-reference.md) che è possibile usare facoltativamente per accedere ai dati e controllare il dispositivo a livello di codice.

## <a name="troubleshooting"></a>Risoluzione dei problemi

### <a name="how-to-fix-the-its-lonely-here-message"></a>Come correggere il messaggio "Nessun contenuto"

> [!NOTE]
> Se si passa da HoloLens 2 a HoloLens (prima generazione), è possibile che le pagine vengano visualizzate prive di contenuto se usate prima in HoloLens 2 e successivamente in HoloLens (prima generazione).

![Messaggio Nessun contenuto nella pagina del Portale di dispositivi](images/using-windows-portal-img-19.png)

1. Selezionare **Reimposta layout** dal menu in alto a sinistra:

![Selezione di Reimposta layout nel menu del Portale di dispositivi](images/using-windows-portal-img-20.png)

2. Fare clic su **Reimposta layout** sotto l'intestazione **Reset workspace** (Reimposta area di lavoro). La pagina del portale verrà aggiornata automaticamente e verrà visualizzato il contenuto.

![Selezione di Reimposta layout nella pagina Reimposta area di lavoro](images/using-windows-portal-img-21.png)

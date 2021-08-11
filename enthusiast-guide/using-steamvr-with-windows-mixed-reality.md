---
title: Uso di SteamVR con Windows Mixed Reality
description: Informazioni su come configurare e riprodurre giochi a SteamVR Windows Mixed Reality visori VR e controller con PC compatibili.
ms.topic: article
keywords: Windows Mixed Reality, Realtà mista, Realtà virtuale, VR, MR, giochi, SteamVR, Tutto, requisiti di sistema
ms.openlocfilehash: 42459f9b8d661bd01ce489460c5293333034612bc59becccf3d35e0ce506fddb
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115221383"
---
# <a name="using-steamvr-with-windows-mixed-reality"></a>Uso di SteamVR con Windows Mixed Reality

Windows Mixed Reality for SteamVR consente agli utenti di eseguire esperienze Dirvr su Windows Mixed Reality visori VR immersive. Dopo aver installato l'Windows Mixed Reality per SteamVR, gli utenti possono avviare le applicazioni Preferiti di SteamVR dal proprio desktop o dalla libreria di Steam e riprodurle direttamente sul visore WINDOWS visore VR.

## <a name="get-your-pc-ready"></a>Prepara il PC

* Assicurarsi che non siano presenti aggiornamenti in sospeso: selezionare Avvia > Impostazioni > **aggiorna & sicurezza > Windows Aggiorna**. Se sono disponibili aggiornamenti, selezionare **Installa ora.** Se non sono disponibili aggiornamenti, selezionare **Controlla la disponibilità di aggiornamenti** e quindi installarne di nuovi.
* I requisiti del PC variano per le app e il contenuto in Steam. Vedere i requisiti minimi per ogni titolo. Un PC con una scheda grafica GTX 1070 (o equivalente) e un processore Intel® Core™ i7 dovrebbe offrire un'esperienza ottimale per un'ampia gamma di titoli.
* Configurare le [Windows Mixed Reality,](set-up-windows-mixed-reality.md) se non è già stato fatto. 

## <a name="set-up-windows-mixed-reality-for-steamvr"></a>Configurare la Windows Mixed Reality per SteamVR

1. [Scaricare e installare SteamVR.](https://steamcdn-a.akamaihd.net/client/installer/SteamWindowsMRInstaller.exe)
2. Quando si è pronti, avviare SteamVR. L'esercitazione di SteamVR dovrebbe essere avviata automaticamente.

> **Nota:** Per la risoluzione dei problemi avanzata dell'installazione di SteamVR, assicurarsi che siano installati i componenti software seguenti:
> 1. Installare [Steam](http://store.steampowered.com/about/) e **accedere** o creare un **nuovo account.**
> 2. Installare [SteamVR.](https://store.steampowered.com/app/250820/SteamVR/) Dopo aver collegato il visore VR, avviare Steam. Verrà visualizzata una finestra di dialogo in cui viene richiesto di installare SteamVR. Seguire le istruzioni nella finestra di dialogo per installarlo.
    * Se il popup non viene visualizzato, installare SteamVR passando alla *sezione Strumenti* della *libreria*. Individuare SteamVR nell'elenco, quindi fare clic con il pulsante destro del mouse e *scegliere Install Game (Installa gioco).*
> 3. Installare [Windows Mixed Reality per SteamVR.](https://store.steampowered.com/app/719950/Windows_Mixed_Reality_for_SteamVR/)

## <a name="set-up-windows-mixed-reality-for-steamvr-in-an-environment-without-internet-access"></a>Configurare l Windows Mixed Reality per SteamVR in un ambiente senza accesso a Internet

**Archiviare i supporti necessari in un dispositivo di archiviazione portatile**
1. Installare [SteamVR](https://store.steampowered.com/app/250820/SteamVR/) e [Windows Mixed Reality per SteamVR](https://store.steampowered.com/app/719950/Windows_Mixed_Reality_for_SteamVR/) come indicato in precedenza usando [Steam](http://store.steampowered.com/about/) in un PC con accesso a Internet completo.
2. In Steam aprire la sezione Library (Libreria) e trovare la parte con etichetta "Tools".
3. Dopo aver installato SteamVR, fare clic con il pulsante destro del mouse sulla voce "SteamVR" e nel menu popup risultante fare clic sulla voce "Proprietà".
4. Verrà aperta una nuova finestra con più schede. Selezionare la scheda "FILE LOCALI" e fare clic sul pulsante "ESPLORA FILE LOCALI".
5. Verrà aperta la directory che contiene il runtime di SteamVR. Copiare l'intera directory (denominata SteamVR) in un supporto portatile di propria scelta, ad esempio una chiavetta USB.
6. Eseguire la stessa operazione con Windows Mixed Reality per SteamVR e con qualsiasi app compatibile con SteamVR che si vuole installare nel PC di destinazione.

**Eseguire SteamVR nel PC di destinazione**
1. Dopo aver collegato il dispositivo di archiviazione portatile al PC di destinazione, spostare Le cartelle SteamVR, MixedRealityVRDriver e altre cartelle in una posizione comoda nel PC di destinazione.
![SteamVR e Windows Mixed Reality per SteamVR installati nel PC di destinazione](images/steamvr-install-files.png)

2. Per assicurarsi che i driver Disistemvr e MixedRealityVRDriver siano nella stessa cartella, aprire un prompt dei comandi. Ai fini di questo esempio, si presuppone che la cartella contenitore si trova in *C:\SteamVRInstall*. In tal caso, nel prompt dei comandi è necessario eseguire:
```powershell
chdir "C:\SteamVRInstall"
.\SteamVR\bin\win64\vrpathreg.exe adddriver "C:\SteamVRInstall\MixedRealityVRDriver"
```
Si noti che se si esegue una versione a 32 bit di Windows, la parte del percorso precedente dovrebbe invece `win64` `win32` essere .

In questo modo il runtime sarà in grado di trovare il Windows Mixed Reality per il driver SteamVR nell'installazione personalizzata.

4. Per eseguire SteamVR, è necessario fare doppio clic sul file "vrstartup.exe" disponibile in *SteamVR\bin\win64\vrstartup.exe* o *SteamVR\bin\win32\vrstartup.exe* se il PC di destinazione esegue una versione a 32 bit di Windows.

Per altre informazioni e per la risoluzione dei problemi, vedere la pagina della documentazione [di Steamworks.](https://partner.steamgames.com/doc/features/steamvr/enterprise#2)

## <a name="play-steamvr-games"></a>Riprodurre giochi di SteamVR

1. Connessione il visore VR sul PC e accendere i controller del movimento.
2. Dopo che Windows Mixed Reality home page è stata caricata e i controller sono visibili, aprire l'app Steam sul desktop.
3. Usare l'app Steam per avviare un gioco Disatteso dalla libreria Di File system.

**Suggerimento:** per avviare giochi Dirvr senza spegnere il visore VR, usare l'app Desktop (**Start > Desktop**) per visualizzare e interagire con il desktop del PC all'interno di Windows Mixed Reality.

## <a name="using-motion-controllers-with-steamvr"></a>Uso dei controller del movimento con MotionVR

I controller del movimento verranno utilizzati in modo diverso in giochi diversi. Ecco alcune nozioni di base per iniziare:

* Per aprire il dashboard di Steam, premere direttamente verso il basso sulla levetta sinistra o destra.
* Per uscire da un gioco Disatteso e tornare Windows Mixed Reality home page, premere il Windows pulsante.

## <a name="changing-the-resolution"></a>Modifica della risoluzione

È possibile modificare il dispositivo di scorrimento risoluzione dell'applicazione nella finestra di Applicazioni -> Impostazioni -> di SteamVR in qualsiasi momento se si desidera riprodurre giochi a una risoluzione più elevata. **Quando si usa un moltiplicatore di risoluzione superiore, è possibile aspettarsi che il gioco metto più pressione sul PC. Se si aumenta il moltiplicatore e si verificano prestazioni ridotte, modificare il dispositivo di scorrimento al livello predefinito e riavviare il gioco per assicurarsi che la modifica venga effettiva.![Modificare la risoluzione dell'applicazione](images/SteamVR_Settings_Applications.png)

## <a name="using-multiple-headsets"></a>Uso di più visori VR

Gli appassionati di realtà virtuale possono usare regolarmente più visori VR nello stesso PC. Se questo è il caso, si noti che quando un visore VR Windows Mixed Reality è collegato, i giochi Per la prima volta vengono sempre avviati nel visore VR Windows Mixed Reality. Se si desidera avviare giochi Per la prima volta su un altro visore VR, assicurarsi di scollegare il visore WINDOWS MIXED REALITY visore VR prima di continuare.

## <a name="preview-programs"></a>Programmi di anteprima

Vengono rilasciati aggiornamenti regolari per migliorare le prestazioni, l'affidabilità e l'esperienza complessiva dell'uso di FirmwareVR Windows Mixed Reality visori VR immersive. Anche se nessuno di questi programmi di anteprima è obbligatorio, si consiglia di partecipare se si desidera ottenere gli aggiornamenti prima e più frequentemente (e inviare commenti e suggerimenti su tali aggiornamenti).)

### <a name="windows-mixed-reality-for-steamvr-beta"></a>Windows Mixed Reality per SteamVR Beta

Windows Mixed Reality per SteamVR è il componente che si installa da Store di Tutto il tempo che consente a SteamVR di usare il visore VR Windows Mixed Reality dispositivo.  Gli aggiornamenti a questo "bridge" vengono pubblicati regolarmente e Vengono installati automaticamente da Firmware.

Se si vogliono ottenere aggiornamenti più frequentemente, è possibile partecipare alla versione beta pubblica.  Gli aggiornamenti vengono prima di tutto ricevuti dai destinatari della versione beta e i commenti e suggerimenti degli utenti vengono utilizzati per assicurarsi che gli aggiornamenti siano di alta qualità prima di pubblicarli per tutti gli utenti.  Se non si è nel programma Beta, si otterrà alla fine tutte le stesse correzioni e funzionalità, ma dopo che sono state testate dagli utenti beta.

Per partecipare:

  1. In Steam usare l'elenco a discesa nel menu **Libreria** per filtrare in base a **Software.**
  2. Nell'elenco fare clic con il pulsante destro **del mouse Windows Mixed Reality per SteamVR** e scegliere **Proprietà.**
  3. Selezionare la **scheda Beta.**
  4. Acconsentire **esplicitamente a "beta - beta pubblica"** e selezionare **Chiudi per** confermare. Il campo del codice di accesso beta deve essere lasciato vuoto.
  
### <a name="steamvr-beta"></a>SteamVR Beta

L'estensione a tutto il mondo è compilata e rilasciata da Valve ed è comune in tutti i visori VR di SteamVR.  Segue un modello simile di rilascio degli aggiornamenti ai membri beta prima della pubblicazione per tutti gli utenti.

Per partecipare:

  1. In Steam usare l'elenco a discesa nel menu **Libreria** per filtrare in base a **Strumenti**.
  2. Nell'elenco fare clic con il pulsante destro **del mouse su SteamVR** e **scegliere Proprietà**.
  3. Selezionare la **scheda Beta.**
  4. Acconsentire **esplicitamente a "beta - beta pubblica"** e selezionare **Chiudi per** confermare.  Il campo del codice di accesso beta deve essere lasciato vuoto. ![ Passare alla versione beta di SteamVR nella finestra di dialogo delle proprietà per SteamVR](images/steamvr-beta.png)

### <a name="windows-insider-program"></a>Programma Windows Insider

Windows Mixed Reality fa parte di Windows 10.  Molte correzioni e funzionalità che interessano gli utenti di SteamVR vengono Windows sistema operativo.  Se si vogliono provare le build di anteprima Windows 10 più recenti, è possibile partecipare al [Windows Programma Insider](https://insider.windows.com).

## <a name="enabling-motion-reprojection-for-steamvr-apps"></a>Abilitazione della reproiezione del movimento per le app Disattesevr

Windows Mixed Reality per SteamVR include una funzionalità sperimentale di riproiezione del movimento per rendere più fluida la riproiezione di 90 FPS.

Quando la riproiezione del movimento è abilitata, il rendering nominale di tutti i giochi di vr a tutto tondo verrà eseguito a una frequenza di 1/2 fotogrammi (45 fps anziché 90 FPS), mentre Windows Mixed Reality per SteamVR usa vettori di movimento generati dalla GPU per estrapolare il fotogramma successivo. Per i giochi Dirvr che hanno raggiunto in modo affidabile 60 FPS+ in un determinato PC, questo dovrebbe comportare una solida esperienza di 90 FPS con artefatti occasionali, mantenendo al tempo stesso un'esperienza comoda.

Le modalità di riproiezione del movimento disponibili sono le seguenti:

* **Impostazione per app di MotionVR:** consente di controllare la riestrazione del movimento tramite l'interfaccia utente di Impostazioni di Controllo del movimento. È quindi possibile aprire l'Impostazioni Di flusso di > Per-Application Video, passare a Video Impostazioni e selezionare un'opzione per "Motion Smoothing" (Smussamento del movimento).
* **Auto:** consente di attivare automaticamente la riproiezione del movimento quando il rendering di un gioco è troppo lento per mantenere 90 FPS. Quando un gioco inizia a mantenere 90 FPS o inizia il rendering a meno di 45 FPS, la riproiezione del movimento viene disattivata. La riproiezione rotazione asincrona è sempre abilitata.
* **Vettore di** movimento: forza l'esecuzione dell'applicazione sempre a metà fotogramma con la riproiezione del vettore di movimento.
* **Nessuno:** disabilita la riproiezione del movimento.

**Previsto Artifacts** 

1. Quando si usa una risoluzione dell'applicazione superiore al 150%, è possibile che si verifichi una sfocatura. Quando si usa la riproiezione del movimento, è consigliabile usare un valore inferiore al 150%.
2. I bordi o il testo a contrasto acuto, in particolare negli HUD o nei menu all'interno del gioco, possono apparire temporaneamente distorti o distorti a causa della disocclusione.
3. La home page di SteamVR e molti altri giochi che non hanno raggiunto in modo affidabile 50-60 FPS nel PC continueranno a avere un'esperienza scadente con questa modalità.
4. Alcuni giochi sono stati segnalati per l'esecuzione a una velocità del 50% o con maggiore latenza (lag). Segnalare questi giochi tramite le istruzioni [Hub di Windows Feedback](filing-feedback.md) di seguito.

Inizialmente è stato supporto sperimentale per GPU NVidia di ultima generazione. Microsoft continua a eseguire l'iterazione e a migliorare il supporto per la riproiezione del movimento su più GPU e non vediamo l'ora di ricevere commenti e suggerimenti.

**GPU supportate:** Nvidia GeForce GTX1060, AMD RX470 o versione successiva, con Windows Mixed Reality driver di grafica compatibili.

Per abilitare la riproiezione del movimento:

1. Assicurarsi di aver acconsentito esplicitamente all'Windows Mixed Reality per La versione **beta di SteamVR** usando le istruzioni precedenti.
2. Aprire il dashboard di SteamVR.
3. Selezionare il pulsante a sinistra con il logo Windows Mixed Reality per aprire Windows Mixed Reality **per l'Impostazioni di SteamVR.**
4. Nell'interfaccia utente visualizzata selezionare la scheda Grafica.
5. Selezionare "Auto" per "Default SteamVR app motion reprojection mode" per abilitare la riproiezione automatica del movimento.

![Abilitare l'indicatore LSR & LSR con SettingsUX](images/settingsux-enable-lsr.gif)

**Indicatore di riproiezione del movimento**

L'indicatore di riproiezione del movimento consente di diagnosticare i problemi relativi alla funzionalità sperimentale di riproiezione automatica del movimento. Se impostato su true, durante la riproiezione automatica del movimento verrà visualizzato un indicatore in alto a sinistra dello schermo dell'visore. Il colore e la posizione di questo indicatore corrispondono alla modalità di riproiezione del movimento corrente. Per esempi, vedere il diagramma seguente.

![Indicatore mvLSR](images/mvLSRIndicator.png)

Verde = la riproiezione del movimento è disattivata perché l'applicazione può eseguire il rendering a piena frequenza dei fotogrammi.

Cyan = la riproiezione del movimento è impostata su perché l'applicazione è associata alla CPU.

Blu = la riproiezione del movimento è impostata su perché l'applicazione è associata a gpu.

Rosso = la riproiezione del movimento è disattivata perché l'applicazione è in esecuzione a meno di metà fotogramma. provare a ridurre il campionamento con super, se abilitato.

Green + Cyan + Blue = motion reprojection is in half-framerate mode or the application requested motion reprojection.

## <a name="sharing-feedback-on-steamvr"></a>Condivisione dei commenti e suggerimenti su SteamVR

Il feedback è prezioso quando si tratta di migliorare l'esperienza Windows Mixed Reality di SteamVR. Inviare tutti i commenti e i bug [tramite Hub di Windows Feedback](filing-feedback.md). Seguire questi suggerimenti per ottenere il massimo dai commenti e suggerimenti:

1. In Hub di Feedback indicare che si sta segnalando un nuovo problema nella sezione "Che tipo di feedback si tratta?" nella parte superiore.
2. Selezionare la **categoria Realtà mista** e la **sottocategoria** App.
3. Inserire la parola "SteamVR" nel riepilogo del problema. Ciò consente di trovare i commenti e suggerimenti.
4. Descrivere il gioco o l'applicazione di SteamVR in uso quando si è verificato il problema.
5. Valutare la possibilità di allegare un report di sistema di SteamVR ai commenti e suggerimenti. In questo modo vengono forniti altri log che consentono di diagnosticare il problema.
    1. Nella finestra di SteamVR (le piccole finestre che mostrano lo stato del controller) selezionare il titolo per aprire il menu.
    2. Selezionare "Crea report di sistema".
    3. Salva in file.
    4. Allegare direttamente il file generato Hub di Feedback voce.
6. Se il feedback riguarda le prestazioni di SteamVR, raccogliere una traccia delle prestazioni della realtà mista: 
    1. Selezionare il **pulsante Ricrea problema.**
    2. Nell'elenco a discesa accanto a "Includi dati su" selezionare **Prestazioni realtà mista**.
    3. Assicurarsi che il gioco sia in esecuzione e selezionare **Avvia acquisizione**.
    4. Dedicare alcuni secondi alla riproduzione del gioco per acquisire la traccia. Non acquisire la traccia per più di 10-15 secondi oppure sarà troppo grande per l'invio.
    5. Selezionare **Arresta acquisizione**.
7. Selezionare **Invia** dopo aver completato il resto dei campi.

In caso di domande o commenti da condividere, è anche possibile contattarci nel [forum di Steam.](http://steamcommunity.com/app/719950/discussions/)

## <a name="see-also"></a>Vedi anche

* [Risoluzione dei problemi di SteamVR con Windows Mixed Reality](steamvr-questions.md)
* [Uso di giochi e app in Windows Mixed Reality](using-games-and-apps-in-windows-mixed-reality.md)
* [Uso dei controller HP in Unity](/windows/mixed-reality/develop/unity/unity-reverb-g2-controllers)
* [Uso dei controller HP in Unreal](/windows/mixed-reality/develop/unreal/unreal-reverb-g2-controllers)
* [Registrazione di bug e feedback](filing-feedback.md)

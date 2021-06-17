---
title: Uso di SteamVR con Windows Mixed Reality
description: Informazioni su come configurare e riprodurre giochi di SteamVR Windows Mixed Reality visori e controller con PC compatibili.
ms.topic: article
keywords: Windows Mixed Reality, Realtà mista, Realtà virtuale, VR, MR, giochi, SteamVR, Vapore, requisiti di sistema
ms.openlocfilehash: 0d79b0c2079875b32387d616e77c5f497ab4aa59
ms.sourcegitcommit: c65759b8d6465b6b13925cacab5af74443f7e6bd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/15/2021
ms.locfileid: "112110142"
---
# <a name="using-steamvr-with-windows-mixed-reality"></a>Uso di SteamVR con Windows Mixed Reality

Windows Mixed Reality per SteamVR consente agli utenti di eseguire esperienze di SteamVR Windows Mixed Reality visori immersive. Dopo aver installato il Windows Mixed Reality per SteamVR, gli utenti possono avviare le applicazioni Preferiti di SteamVR dal desktop o dalla libreria di Steam e riprodurle direttamente sul visore Windows.

## <a name="get-your-pc-ready"></a>Prepara il PC

* Assicurarsi di non avere aggiornamenti in sospeso: selezionare Start **> Settings > Update & Security > Windows Update**. Se sono disponibili aggiornamenti, selezionare **Installa ora**. Se non sono disponibili aggiornamenti, selezionare **Controlla aggiornamenti** e quindi installarne uno nuovo.
* I requisiti del PC variano per le app e il contenuto in Steam. Vedere i requisiti minimi per ogni titolo. Un PC con una scheda grafica GTX 1070 (o equivalente) e un processore Intel® Core™ i7 dovrebbe offrire un'esperienza ottimale per un'ampia gamma di titoli.
* Configurare il [Windows Mixed Reality](set-up-windows-mixed-reality.md) se non è già stato fatto. 

## <a name="set-up-windows-mixed-reality-for-steamvr"></a>Configurare Windows Mixed Reality per SteamVR

1. [Scaricare e installare SteamVR.](https://steamcdn-a.akamaihd.net/client/installer/SteamWindowsMRInstaller.exe)
2. Quando è pronto, avviare SteamVR. L'esercitazione su SteamVR dovrebbe essere avviata automaticamente.

> **Nota:** Per la risoluzione avanzata dei problemi di configurazione di SteamVR, assicurarsi che siano installati i componenti software seguenti:
> 1. Installare [Steam](http://store.steampowered.com/about/) e **accedere o** creare un nuovo **account.**
> 2. Installare [SteamVR](https://store.steampowered.com/app/250820/SteamVR/). Con il visore collegato, avviare Steam e verrà visualizzata una finestra di dialogo che richiede di installare SteamVR. Seguire le istruzioni visualizzate nella finestra di dialogo per installarla.
    * Se il popup non viene visualizzato, installare SteamVR passando alla *sezione Strumenti* della *libreria*. Individuare SteamVR nell'elenco, quindi fare clic con il pulsante destro del mouse e *scegliere Installa gioco*.
> 3. Installare [Windows Mixed Reality per SteamVR](https://store.steampowered.com/app/719950/Windows_Mixed_Reality_for_SteamVR/).

## <a name="set-up-windows-mixed-reality-for-steamvr-in-an-environment-without-internet-access"></a>Configurare la Windows Mixed Reality per SteamVR in un ambiente senza accesso a Internet

**Archiviare i supporti necessari in un dispositivo di archiviazione portatile**
1. Installare [SteamVR](https://store.steampowered.com/app/250820/SteamVR/) e [Windows Mixed Reality per SteamVR](https://store.steampowered.com/app/719950/Windows_Mixed_Reality_for_SteamVR/) come indicato in precedenza usando [Steam](http://store.steampowered.com/about/) in un PC con accesso a Internet completo.
2. In Steam aprire la sezione Libreria e trovare la parte con l'etichetta "Strumenti".
3. Dopo aver installato SteamVR, fare clic con il pulsante destro del mouse sulla voce "SteamVR" e nel menu popup risultante fare clic sulla voce "Proprietà".
4. Verrà aperta una nuova finestra con più schede. Selezionare la scheda "FILE LOCALI" e fare clic sul pulsante "SFOGLIA FILE LOCALI".
5. Verrà aperta la directory contenente il runtime di SteamVR. Copiare l'intera directory (denominata SteamVR) in un supporto portatile di propria scelta,ad esempio un'unità USB.
6. Eseguire la stessa operazione con Windows Mixed Reality per SteamVR e con qualsiasi app compatibile con SteamVR che si vuole installare nel PC di destinazione.

**Eseguire SteamVR nel PC di destinazione**
1. Dopo aver collegato il dispositivo di archiviazione portatile al PC di destinazione, spostare le cartelle Disaffezionate, MixedRealityVRDriver e altre cartelle in una posizione comoda nel PC di destinazione.
![SteamVR e Windows Mixed Reality per SteamVR installati nel PC di destinazione](images/steamvr-install-files.png)

2. Verificare che i file Disaffezione e MixedRealityVRDriver siano nella stessa cartella, aprire un prompt dei comandi. Ai fini di questo esempio, si presuppone che la cartella contenitore si trova in *C:\SteamVRInstall*. In tal caso, nel prompt dei comandi è necessario eseguire:
```powershell
chdir "C:\SteamVRInstall"
.\SteamVR\bin\win64\vrpathreg.exe adddriver "C:\SteamVRInstall\MixedRealityVRDriver"
```
Si noti che se si esegue una versione a 32 bit di Windows, dovrebbe essere invece la parte del `win64` percorso `win32` precedente.

In questo modo il runtime troverà il driver Windows Mixed Reality per SteamVR nell'installazione personalizzata.

4. Per eseguire SteamVR, è necessario fare doppio clic sul file "vrstartup.exe" disponibile in *SteamVR\bin\win64\vrstartup.exe* o *SteamVR\bin\win32\vrstartup.exe* se il PC di destinazione esegue una versione a 32 bit di Windows.

Per altre informazioni e risoluzione dei problemi, vedere la pagina della documentazione [di Steamworks.](https://partner.steamgames.com/doc/features/steamvr/enterprise#2)

## <a name="play-steamvr-games"></a>Riprodurre giochi di SteamVR

1. Connettere il visore al PC e accendere i controller di movimento.
2. Dopo aver caricato Windows Mixed Reality home page e aver visualizzato i controller, aprire l'app Steam sul desktop.
3. Usare l'app Steam per avviare un gioco di SteamVR dalla libreria di Steam.

**Suggerimento:** per avviare giochi di SteamVR senza spegnere il visore, usare l'app Desktop (**Avvia > Desktop**) per visualizzare e interagire con il desktop del PC all'interno Windows Mixed Reality.

## <a name="using-motion-controllers-with-steamvr"></a>Uso di controller di movimento con SteamVR

I controller di movimento verranno utilizzati in modo diverso in giochi diversi. Ecco alcune nozioni di base per iniziare:

* Per aprire il dashboard di Steam, premere direttamente verso il basso sulla levetta sinistra o destra.
* Per uscire da un gioco di SteamVR e tornare Windows Mixed Reality home, premere il pulsante Windows.

## <a name="changing-the-resolution"></a>Modifica della risoluzione

È possibile modificare il dispositivo di scorrimento risoluzione dell'applicazione nella finestra Impostazioni di SteamVR -> -> Applications in qualsiasi momento se si desidera riprodurre giochi a una risoluzione superiore. **Quando si usa un moltiplicatore di risoluzione più elevato, è possibile aspettarsi che il gioco metto più a dura prova il PC. Se si aumenta il moltiplicatore e si verificano prestazioni ridotte, modificare il dispositivo di scorrimento al livello predefinito e riavviare il gioco per assicurarsi che la modifica venga apportata.![Modificare la risoluzione dell'applicazione](images/SteamVR_Settings_Applications.png)

## <a name="using-multiple-headsets"></a>Uso di più visori

Se si è un appassionato di VR, è possibile usare regolarmente più di un visore VR nello stesso PC. Se questo è il caso, si noti che quando un visore Windows Mixed Reality è collegato, i giochi di SteamVR verranno sempre avviati al visore Windows Mixed Reality visore. Se si desidera avviare giochi di SteamVR su un altro visore, assicurarsi di scollegare il visore Windows Mixed Reality prima di continuare.

## <a name="preview-programs"></a>Programmi di anteprima

Vengono rilasciati aggiornamenti regolari per migliorare le prestazioni, l'affidabilità e l'esperienza complessiva dell'uso di SteamVR Windows Mixed Reality visori immersivi. Anche se nessuno di questi programmi di anteprima è obbligatorio, è necessario unirsi a essi se si vuole ottenere gli aggiornamenti prima e più frequentemente (e inviare commenti e suggerimenti su tali aggiornamenti).)

### <a name="windows-mixed-reality-for-steamvr-beta"></a>Windows Mixed Reality per La versione beta di SteamVR

Windows Mixed Reality per SteamVR è il componente installato da Steam Store che consente a SteamVR di lavorare con il visore Windows Mixed Reality visore.  Gli aggiornamenti a questo "bridge" vengono pubblicati regolarmente e Vengono installati automaticamente da Steam.

Se si vogliono ottenere aggiornamenti più frequentemente, è necessario partecipare alla versione beta pubblica.  Gli aggiornamenti passano prima al pubblico beta e i commenti e suggerimenti vengono utilizzati per assicurarsi che gli aggiornamenti siano di alta qualità prima di pubblicarli a tutti gli utenti.  Se non si è nel programma Beta, alla fine si otterrà tutte le stesse correzioni e funzionalità, ma dopo che sono state testate dagli utenti beta.

Per partecipare:

  1. In Steam usare l'elenco a discesa nel menu **Libreria** per filtrare in **Software**.
  2. Nell'elenco fare clic con il pulsante destro **Windows Mixed Reality per SteamVR** e scegliere **Proprietà**.
  3. Selezionare la **scheda Beta.**
  4. Acconsentire esplicitamente **a "beta - beta pubblica"** e selezionare **Chiudi per** confermare. Il campo del codice di accesso beta deve essere lasciato vuoto.
  
### <a name="steamvr-beta"></a>SteamVR Beta

La versione di SteamVR è stata creata e rilasciata da Valve ed è comune in tutti i visori per visori di SteamVR.  Segue un modello simile di rilascio degli aggiornamenti ai membri Beta prima della pubblicazione per tutti gli utenti.

Per partecipare:

  1. In Steam usare l'elenco a discesa nel menu **Libreria** per filtrare in **Strumenti**.
  2. Nell'elenco fare clic con il pulsante destro **del mouse su SteamVR** e scegliere **Proprietà**.
  3. Selezionare la **scheda Beta.**
  4. Acconsentire esplicitamente **a "beta - beta pubblica"** e selezionare **Chiudi per** confermare.  Il campo del codice di accesso beta deve essere lasciato vuoto. ![ Passare alla versione beta di SteamVR nella finestra di dialogo delle proprietà per SteamVR](images/steamvr-beta.png)

### <a name="windows-insider-program"></a>Programma Windows Insider

Windows Mixed Reality fa parte di Windows 10.  Molte correzioni e funzionalità che interessano gli utenti di SteamVR sono disponibili con il sistema operativo Windows.  Se si vogliono provare le build di anteprima Windows 10 più recenti, è necessario partecipare al [Programma Windows Insider](https://insider.windows.com).

## <a name="enabling-motion-reprojection-for-steamvr-apps"></a>Abilitazione della riproiezione del movimento per le app SteamVR

Windows Mixed Reality per SteamVR ha una funzionalità sperimentale di riproiezione del movimento per rendere più fluida la riproiezione di 90 FPS.

Quando la riproiezione del movimento è abilitata, il rendering nominale di tutti i giochi vr di Steam verrà eseguito a una frequenza di fotogrammi di 1/2 (45 fps anziché 90 FPS), mentre Windows Mixed Reality per SteamVR usa vettori di movimento generati dalla GPU per estrapolare il fotogramma successivo. Per i giochi di SteamVR che hanno raggiunto in modo affidabile 60 FPS+ in un determinato PC, ciò dovrebbe comportare una solida esperienza di 90 FPS con artefatti occasionali mantenendo un'esperienza comoda.

Le modalità di riproiezione del movimento disponibili sono le seguenti:

* **Impostazione di SteamVR per app:** consente di controllare la riproiezione del movimento tramite l'interfaccia utente delle impostazioni di SteamVR. È quindi possibile aprire Impostazioni di SteamVR, passare a Impostazioni video > Per-Application video e selezionare un'opzione per "Smoothing movimento".
* **Auto:** consente di attivare automaticamente la riproiezione del movimento quando il rendering di un gioco è troppo lento per mantenere 90 FPS. Quando un gioco inizia a mantenere 90 FPS o inizia il rendering a meno di 45 FPS, la riproiezione del movimento viene disattivata. La riproiezione rotazione asincrona è sempre abilitata.
* **Vettore di** movimento: forza l'esecuzione dell'applicazione sempre a metà fotogramma con la riproiezione del vettore di movimento.
* **Nessuno:** disabilita la riproiezione del movimento.

**Elementi visivi previsti** 

1. Quando si usa una risoluzione dell'applicazione superiore al 150%, è possibile che si verifichi una sfocatura. Quando si usa la riproiezione del movimento, è consigliabile usare un valore inferiore al 150%.
2. I bordi o il testo a contrasto acuto, in particolare negli HUD o nei menu all'interno del gioco, possono apparire temporaneamente distorti o distorti a causa della disocclusione.
3. La home page di SteamVR e molti altri giochi che non hanno raggiunto in modo affidabile 50-60 FPS nel PC continueranno a avere un'esperienza scadente con questa modalità.
4. Alcuni giochi sono stati segnalati per l'esecuzione a una velocità del 50% o con maggiore latenza (lag). Segnalare questi giochi tramite le istruzioni [Hub di Windows Feedback](filing-feedback.md) di seguito.

Inizialmente è stato supporto sperimentale per GPU NVidia di ultima generazione. Microsoft continua a eseguire l'iterazione e a migliorare il supporto per la riproiezione del movimento su più GPU e non vediamo l'ora di ricevere commenti e suggerimenti.

**GPU supportate:** Nvidia GeForce GTX1060, AMD RX470 o versione successiva, con Windows Mixed Reality driver di grafica compatibili.

Per abilitare la riproiezione del movimento:

1. Assicurarsi di aver acconsentito esplicitamente all'Windows Mixed Reality per La versione **beta di SteamVR** usando le istruzioni precedenti.
2. Aprire il dashboard di SteamVR.
3. Selezionare il pulsante a sinistra con il logo Windows Mixed Reality per aprire Windows Mixed Reality **impostazioni di SteamVR.**
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

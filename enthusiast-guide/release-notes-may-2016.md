---
title: Note sulla versione - maggio 2016
description: È possibile rimanere sempre aggiornati sulle note sulla versione di HoloLens per l'aggiornamento olografico di Windows 2016.
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens, note sulla versione, sistema operativo, funzionalità, compilazione, piattaforma
ms.openlocfilehash: db5e3b87eaf619a0f25e07d0698499a89a1b4b12
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2021
ms.locfileid: "98009501"
---
# <a name="release-notes---may-2016"></a>Note sulla versione - maggio 2016

Il team di HoloLens si impegna a fornire gli aggiornamenti più recenti delle funzionalità e le correzioni principali tramite il programma Windows Insider. Grazie a tutti i tuoi suggerimenti, abbiamo inviato i tuoi commenti a Heart. Continua a [inviare commenti e suggerimenti](https://docs.microsoft.com/windows/mixed-reality/give-us-feedback) tramite l'hub di feedback, i [forum per sviluppatori](https://forums.hololens.com) e il [ @HoloLens Twitter tramite ](https://twitter.com/hololens).

**Versione di rilascio:** Aggiornamento di Windows olografico 2016 (**10.0.14342.1016**)

>[!VIDEO https://www.youtube.com/embed/XM5OHHrOGqQ]

Per eseguire l'aggiornamento alla versione corrente, aprire l'app *Impostazioni* , passare a *Aggiorna & sicurezza*, quindi selezionare il pulsante *Controlla aggiornamenti* .

## <a name="new-features"></a>Nuove funzionalità

* È ora possibile **eseguire fino a tre app nella visualizzazione 2D simultaneamente**, che consente casi d'uso infiniti per il multitasking in HoloLens. È possibile usare il nuovo hub di feedback con l'elenco delle missioni aperte, esplorando le nuove funzionalità di questo volo.

  ![HoloLens può eseguire tre app nello stesso momento](images/img-3625-400px.jpg)<br>
  Esegui fino a tre app in visualizzazione 2D simultaneamente

* Sono stati aggiunti nuovi **comandi vocali**:
   * Provare a esaminare un ologramma e ruotarlo dicendo "Face me"
   * Modificare le dimensioni definendo "Bigger" o "minor"
   * Spostare un'app dicendo "Hey Cortana, Move *app name* here".
* Lo **sviluppo in HoloLens è stato semplificato**. È ora possibile esplorare, caricare e scaricare i file tramite il [portale del dispositivo Windows](https://docs.microsoft.com/windows/mixed-reality/develop/platform-capabilities-and-apis/using-the-windows-device-portal). È possibile accedere alla cartella documenti, alla cartella immagini e all'archiviazione locale per qualsiasi app caricata o distribuita in Visual Studio.
* L' **emulatore supporta ora l'accesso con un account Microsoft** , proprio come in un HoloLens reale, che è possibile abilitare dal menu strumenti aggiuntivi ">>".
* **le app 2D ora nascondono la barra e il cursore dell'app quando si guarda il video a schermo intero** per evitare la distrazione. L'esperienza di visione video sarà ancora più gradevole in HoloLens.
* È anche possibile **aggiungere foto senza la barra dell'app** nel mondo.

  ![La barra dell'app può essere nascosta per le app 2D come le foto](images/img-3626-400px.jpg)<br>
  La barra dell'app può essere nascosta per le app con una visualizzazione 2D, ad esempio Photos

* Il **selettore file** funziona come previsto in HoloLens.
* Aggiornamento del **browser Edge** per il mapping dell'esperienza utente unificata con desktop e telefono. Sono state abilitate più istanze del browser, una nuova scheda HoloLens personalizzata, una nuova scheda e un'apertura in nuove finestre, oltre ai miglioramenti delle prestazioni di Power &.
* L'app **Groove Music** è ora disponibile in HoloLens. Visita lo Store per scaricarlo e provare a giocare in background.
* Puoi personalizzare facilmente il modo in cui le app vengono organizzate in tutto il mondo. Provare a **ruotare gli ologrammi** in modalità di regolazione semplicemente facendo clic e trascinando il cerchio nei wireframe centrali verticali. È possibile notare che gli ologrammi dispongono di **caselle di delimitazione più strette** per garantire l'interazione ingrandita. È anche possibile ridimensionare tutte le app Flat verticalmente (eccetto le foto e le app olografiche).

  ![Gli ologrammi possono essere ruotati dopo averli posizionati in tutto il mondo](images/img-3627-400px.jpg)<br>
  Ruotare gli ologrammi dopo averli posizionati nel mondo

* In questo volo sono stati apportati diversi **miglioramenti all'input** . È possibile connettere un normale mouse Bluetooth a HoloLens. Il Clicker è stato ottimizzato in modo da consentire il ridimensionamento & lo stesso passaggio con un clic. Anche la tastiera viene eseguita meglio.
* A questo punto è possibile eseguire le **Immagini della realtà mista** premendo contemporaneamente il volume verso l'alto e il volume verso il basso. È anche possibile condividere foto acquisite in realtà mista & video a Facebook, Twitter e YouTube.
* La lunghezza massima di registrazione dei **video in realtà mista** è stata aumentata a cinque minuti.
* **App Photos** ora trasmette video da OneDrive anziché scaricare l'intero video prima della riproduzione.
* È stato migliorato il modo in **cui gli ologrammi** saranno nel punto in cui sono stati lasciati. Verrà inoltre visualizzata l'opzione per riconnettersi a Wi-Fi e riprovare se HoloLens non è in grado di rilevare la posizione.
* La tastiera ha un **layout migliorato per l'immissione dell'indirizzo di posta elettronica** con chiavi che consentono di immettere i domini di posta elettronica più diffusi con un solo clic.
* **Registrazione dell'app** più veloce e **rilevamento automatico del fuso orario** durante la configurazione guidata, per offrire la migliore esperienza utente.
* Il **concetto di archiviazione** consente di visualizzare lo spazio su disco rimanente e utilizzato dal sistema e dalle app nell'app Impostazioni.
* Abbiamo convergeto l'app feedback e l'hub all'interno di un singolo **Hub di feedback** delle app, che è lo strumento ideale per inviare **commenti e suggerimenti** sulle funzionalità che preferisci, che necessitano di miglioramenti e con quelle che puoi fare senza. Quando si partecipa al programma Insider, è possibile continuare a **ricevere le ultime notizie Insider**, **valutare le compilazioni** e passare alle **ricerche di feedback** dall'hub di feedback.
* È stata anche [pubblicata una build aggiornata dell'emulatore di HoloLens](https://docs.microsoft.com/windows/mixed-reality/develop/install-the-tools) .
* I video della realtà mista ora sembrano migliori a causa della **stabilizzazione automatica dei video**.

## <a name="major-fixes"></a>Correzioni principali

Sono stati corretti i problemi con gli spazi ologrammi in cui gli spazi venivano rilevati in modo lento o errato. È stato risolto un problema di arresto che poteva continuare a provare ad avviare la shell durante l'arresto.

È stato risolto un problema
* in questo modo si impedisce la possibilità di riprendere un'applicazione XAML.
* dove un arresto anomalo lascia una schermata nera e alcune linee irregolari.
* a volte, lo scorrimento si posiziona nella direzione sbagliata quando si usano alcune app.
* il LED di alimentazione potrebbe indicare uno stato spento quando il dispositivo era ancora acceso.
* Il Wi-Fi potrebbe essere disattivato dopo la ripresa dalla modalità standby.
* il provider di identità Xbox offre la configurazione del gamertag e quindi rimane bloccata in un ciclo.
* la shell occasionalmente si arresta in modo anomalo quando si seleziona un file scaricato nel selettore file di OneDrive.
* Quando si preme e si mantiene un collegamento a volte, viene aperta una nuova scheda interruppe e viene aperto un menu di scelta rapida.
* dove il portale per dispositivi Windows non consente le rettifiche DPI da 50 a 80

Sono stati risolti i problemi relativi alle foto in cui
* occasionalmente, un'immagine viene visualizzata ruotata perché la proprietà dell'orientamento EXIF ignorata è stata ignorata.
* potrebbe arrestarsi in modo anomalo durante l'avvio delle foto aggiunte.
* i video verranno riavviati dopo la sospensione anziché continuare dall'ultima sospensione.
* la riproduzione di un video condiviso potrebbe essere impedita se è stata condivisa durante la riproduzione.
* Le registrazioni di acquisizione di realtà miste iniziano con 0,5-1 secondo di feed solo audio.
* il pulsante di sincronizzazione scompare durante la sincronizzazione iniziale di OneDrive.

Sono stati risolti i problemi relativi alle impostazioni in cui
* è necessario un aggiornamento in caso di modifica dell'ambiente.
* ' Enter ' sulla tastiera non si comporta come fare clic su Next in alcune finestre di dialogo.
* era difficile capire quando l'associazione del clic non è riuscita.
* potrebbe non rispondere con connessione Wi-Fi e connessione.

Sono stati risolti i problemi relativi a Cortana, dove
* potrebbe essere bloccata la visualizzazione dell'interfaccia utente in ascolto.
* Chiedere "Hey Cortana, cosa posso dire" da un'app in modalità esclusiva potrebbe rimanere bloccata se si rispondeva a una risposta forse piuttosto Sì/No alla richiesta di uscire dall'app.
* l'interfaccia utente di ascolto di Cortana non riprende correttamente se si chiede a Cortana di andare in sospensione e quindi riprendere.
* le query "a quale rete sono connesso?" e "sono connesso?" potrebbe non riuscire quando il primo profilo di rete torna senza connettività.
* l'interfaccia utente si è bloccata in "ascolto" ma quando si esce da un'app verrà immediatamente riavviato il riconoscimento vocale.
* Quando la disconnessione dall'app Cortana non consente di accedere al computer finché non viene eseguito il riavvio.
* non verrà avviato quando era attiva l'interfaccia utente di acquisizione di realtà mista.

Sono stati risolti i problemi con Visual Studio in cui
* il debug dell'attività in background non funziona.
* l'analisi dei frame nel debugger della grafica non funziona.
* l'emulatore di HoloLens non è stato visualizzato nell'elenco a discesa per Visual Studio, a meno che la TargetPlatformVersion del progetto non sia stata impostata su 10240.

## <a name="changes-from-previous-release"></a>Modifiche rispetto alla versione precedente
* Il comando Cortana **Hey Cortana, il riavvio del dispositivo** non funziona. L'utente può dire **Hey Cortana, riavviare** o **Hey Cortana riavviare il dispositivo**.
* La modalità tutto schermo è stata rimossa dal prodotto.

## <a name="prior-release-notes"></a>Note sulla versione precedente
* [Note sulla versione - marzo 2016](release-notes-march-2016.md)

## <a name="see-also"></a>Vedere anche
* [Problemi noti di HoloLens](https://docs.microsoft.com/windows/mixed-reality/hololens-known-issues)
* [Installare gli strumenti](https://docs.microsoft.com/windows/mixed-reality/develop/install-the-tools)
* [Shell](https://docs.microsoft.com/windows/mixed-reality/discover/navigating-the-windows-mixed-reality-home)
* [Aggiornamento di app UWP 2D per la realtà mista](https://docs.microsoft.com/windows/mixed-reality/develop/porting-apps/building-2d-apps)
* [Accessori hardware](https://docs.microsoft.com/windows/mixed-reality/discover/hardware-accessories)
* [Acquisizione in realtà mista (MRC, Mixed Reality Capture)](https://docs.microsoft.com/windows/mixed-reality/mixed-reality-capture)
* [Input vocale](https://docs.microsoft.com/windows/mixed-reality/design/voice-input)
* [Invio di un'app a Windows Store](https://docs.microsoft.com/windows/mixed-reality/distribute/submitting-an-app-to-the-microsoft-store)
* [Uso dell'emulatore HoloLens](https://docs.microsoft.com/windows/mixed-reality/develop/platform-capabilities-and-apis/using-the-hololens-emulator)

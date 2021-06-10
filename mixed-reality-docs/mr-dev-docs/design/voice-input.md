---
title: Input vocale
description: L'input vocale è un input principale per HoloLens e Windows Mixed Reality visori immersive. La voce può essere usata per comandi, dettatura, Cortana e altro ancora.
author: hak0n
ms.author: hakons
ms.date: 10/03/2019
ms.topic: article
keywords: ggv, voce, cortana, voce, input, visore di realtà mista, visore per realtà mista windows, visore per realtà virtuale, HoloLens, MRTK, Mixed Reality Toolkit, sguardo
ms.openlocfilehash: 6773bb71da7d98b1dd00d2246084d469e5e7c6ba
ms.sourcegitcommit: 9ae76b339968f035c703d9c1fe57ddecb33198e3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/27/2021
ms.locfileid: "110600580"
---
# <a name="voice-input"></a>Input vocale

![Input vocale](images/UX_Hero_VoiceCommand.jpg)

La voce è una delle forme di input chiave per HoloLens. Consente di eseguire direttamente un comando di un ologramma senza dover usare [i movimenti della mano.](gaze-and-commit.md#composite-gestures) L'input vocale può essere un modo naturale di comunicare le intenzioni. La voce è particolarmente utile per attraversare interfacce complesse, perché consente agli utenti di tagliare i menu annidati con un solo comando.

L'input vocale è basato sullo [stesso motore che](/windows/uwp/design/input/speech-recognition) supporta la voce in tutte le app di Windows _universali._ In HoloLens il riconoscimento vocale funzionerà sempre nella lingua di visualizzazione di Windows configurata nelle impostazioni del dispositivo. 

<br>

## <a name="voice-and-gaze&quot;></a>Voce e sguardo

Quando si usano comandi vocali, la testa o lo sguardo fisso è il meccanismo di destinazione tipico, sia con un cursore da &quot;selezionare&quot; che per incanalare il comando a un'applicazione che si sta esaminando. Potrebbe non essere nemmeno necessario visualizzare un cursore dello sguardo _(&quot;vedilo, pronuncialo")_. Alcuni comandi vocali non richiedono una destinazione, ad esempio "vai a start" o "Hey Cortana".

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/eHMkOpNUtR8" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>


## <a name="device-support"></a>Supporto di dispositivi

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><strong>Funzionalità</strong></td>
        <td><a href="/hololens/hololens1-hardware"><strong>HoloLens (prima generazione)</strong></a></td>
        <td><a href="/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
        <td><a href="../discover/immersive-headset-hardware-details.md"><strong>Visori VR immersive</strong></a></td>
    </tr>
     <tr>
        <td>Input vocale</td>
        <td>✔️</td>
        <td>✔️</td>
        <td>✔️ (con microfono)</td>
    </tr>
</table>

## <a name="the-select-command"></a>Comando "select"

**HoloLens (prima generazione)**

Anche senza aggiungere in modo specifico il supporto vocale all'app, gli utenti possono attivare gli ologrammi semplicemente pronunciando il comando vocale di sistema "select". Si comporta come un [](gaze-and-commit.md#composite-gestures) tocco in aria su HoloLens, premendo il pulsante di selezione sul [clicker HoloLens](/hololens/hololens1-clicker)o premendo il trigger in un controller di movimento [Windows Mixed Reality.](motion-controllers.md) Si sentirà un suono e verrà visualizzata una descrizione comando con "seleziona" come conferma. "Select" è abilitato da un algoritmo di rilevamento delle parole chiave a basso consumo, che significa che è possibile pronunciarlo in qualsiasi momento con un impatto minimo sulla durata della batteria. È anche possibile pronunciare "select" con le mani al proprio fianco.

<br>

---

:::row:::
    :::column:::
        **HoloLens 2**<br><br>
        Per usare il comando vocale "select" in HoloLens 2, è prima di tutto necessario visualizzare il cursore dello sguardo fisso da usare come puntatore. Il comando per la sua comparsa è facile da ricordare, ad esempio "select".<br><br>
        Per uscire dalla modalità, usare di nuovo le mani toccando l'aria, avvicinando un pulsante con le dita o usando il movimento del sistema.<br>
        <br> 
        *Immagine: pronunciare "select" per usare il comando vocale per la selezione*
    :::column-end:::
        :::column:::
       ![Un utente può pronunciare "select" per usare il comando vocale per una selezione.](images/kma-voice-select-00170.jpg)<br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="hey-cortana"></a>Hey Cortana

È possibile pronunciare "Hey Cortana" per visualizzare Cortana in qualsiasi momento. Non è necessario attendere che continui a porre la domanda o a fornire un'istruzione. Ad esempio, provare a dire "Hey Cortana, qual è il meteo?" come singola frase. Per altre informazioni su Cortana e sulle attività che è possibile eseguire, chiedere a Cortana. Dire "Hey Cortana, cosa posso dire?" e verrà visualizzato un elenco di comandi funzionanti e consigliati. Se si è già nell'app Cortana, selezionare **?** sulla barra laterale per visualizzare lo stesso menu.

**Comandi specifici di HoloLens**
* "Cosa posso dire?"
* "Vai a Start": invece di [fiorire](system-gesture.md#bloom) per accedere al [menu Start](../discover/navigating-the-windows-mixed-reality-home.md#start-menu)
* <app>"Avvia"
* "Sposta <app> qui"
* "Scatta una foto"
* "Avvia registrazione"
* "Arresta registrazione"
* "Mostra raggio mano"
* "Nascondi raggio mano"
* "Aumentare la luminosità"
* "Diminuisci la luminosità"
* "Aumentare il volume"
* "Ridurre il volume"
* "Disattiva audio" o "Riattiva"
* "Arresta il dispositivo"
* "Riavvia il dispositivo"
* "Vai a sospensione"
* "Che ora è?"
* "Quanta batteria è rimasto?"

<br>

---

:::row:::
    :::column:::
        ## <a name="see-it-say-itbr"></a>"See It, Say It"<br>
        HoloLens ha un modello "see it, say it" per l'input vocale, in cui le etichette sui pulsanti consentono agli utenti di indicare anche i comandi vocali che possono pronunciare. Ad esempio, quando si esamina una finestra dell'app in HoloLens (prima generazione), un utente può pronunciare il comando "Regola" per regolare la posizione dell'app nel mondo.<br>
        <br>
        *Immagine: un utente può pronunciare il comando "Regola", visualizzato nella barra dell'app per regolare la posizione dell'app*
    :::column-end:::
        :::column:::
        ![space](images/spacer-20x582.png)<br>
        ![Quando si esamina una finestra dell'app o un ologramma, un utente può pronunciare il comando "Regola" visualizzato nella barra dell'app per regolare la posizione dell'app nel mondo](images/microphone-600px.png)<br>
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        Quando le app seguono questa regola, gli utenti possono comprendere facilmente cosa dire per controllare il sistema. Mentre si guarda un pulsante in HoloLens (prima generazione), viene visualizzata una descrizione comando "sospensione vocale" che viene visualizzata dopo un secondo se il pulsante è abilitato per la voce e visualizza il comando per pronunciarlo "premere". Per visualizzare le descrizioni comando vocali HoloLens 2, visualizzare il cursore vocale pronunciando "select" o "What can I say" (Vedere l'immagine). <br>
        <br>
        *Immagine: i comandi "See it, say it" vengono visualizzati sotto i pulsanti*
    :::column-end:::
        :::column:::
       ![Vedere, dire che i comandi vengono visualizzati sotto i pulsanti](images/voice-seeitsayit-600px.png)<br><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="voice-commands-for-fast-hologram-manipulation"></a>Comandi vocali per la manipolazione rapida degli ologrammi

Sono disponibili molti comandi vocali che è possibile pronunciare mentre si guarda un ologramma per eseguire rapidamente attività di manipolazione. Questi comandi vocali funzionano sulle finestre dell'app e sugli oggetti 3D inseriti nel mondo.

**Comandi di manipolazione dell'ologramma**
* Guardami
* Dimensioni | intensificare
* Piccoli

In HoloLens 2 è anche possibile creare interazioni più naturali in combinazione con lo sguardo oculare, che fornisce in modo implicito informazioni contestuali su ciò a cui si fa riferimento. Ad esempio, è possibile esaminare un ologramma e pronunciare "put _this"_ e quindi esaminare dove si vuole posizionarlo e dire _"qui"._
Oppure è possibile esaminare una parte olografica in una macchina complessa e dire: "dammi altre informazioni su _questo"._

## <a name="discovering-voice-commands"></a>Individuazione dei comandi vocali

Alcuni comandi, ad esempio i comandi per la manipolazione rapida precedente, possono essere nascosti. Per informazioni sui comandi che è possibile usare, osservare un oggetto e pronunciare "cosa posso dire?". Viene visualizzato un elenco di possibili comandi. È anche possibile usare il cursore dello sguardo della testa per guardarsi intorno e visualizzare le descrizioni comando vocali per ogni pulsante davanti. 

Se si vuole un elenco completo, pronunciare semplicemente "Mostra tutti i comandi" in qualsiasi momento. 

## <a name="dictation"></a>Dettatura

Invece di digitare con [i tocchi d'aria,](gaze-and-commit.md#composite-gestures)la dettatura vocale può essere più efficiente per immettere testo in un'app. Questo può accelerare notevolmente l'input con meno sforzo per l'utente.

![La dettatura vocale inizia selezionando il pulsante del microfono](images/micbuttonfordictation.png)<br>
*La dettatura vocale inizia selezionando il pulsante del microfono sulla tastiera*

Ogni volta che la tastiera olografica è attiva, è possibile passare alla modalità dettatura anziché digitare. Selezionare il microfono sul lato della casella di input di testo per iniziare.

## <a name="adding-voice-commands-to-your-app"></a>Aggiunta di comandi vocali all'app

Valuta l'opportunità di aggiungere comandi vocali a un'esperienza che stai creando. La voce è un modo efficace per controllare il sistema e le app. Poiché gli utenti parlano con diversi tipi di dialetti e accenti, la scelta appropriata delle parole chiave vocali assicura che i comandi degli utenti siano interpretati senza ambiguità.

### <a name="best-practices"></a>Procedure consigliate

Di seguito vengono illustrate alcune procedure che semplificheranno il riconoscimento vocale.
* **Usa comandi concisi**. Quando possibile, scegli parole chiave di due o più sillabe. Le parole di una sillaba tendono a usare suoni di vocali differenti se pronunciate da persone con accenti diversi. Esempio: "Riproduci video" è migliore di "Riproduci il video attualmente selezionato"
* **Usare un vocabolario semplice:** ad esempio: "Mostra nota" è migliore di "Show placard"
* **Assicurarsi che i** comandi non siano distruttivi: assicurarsi che le azioni dei comandi vocali non siano distruttive e possano essere annullate facilmente nel caso in cui un'altra persona che parla vicino all'utente attiva accidentalmente un comando.
* **Evitare comandi acustici simili:** evitare di registrare più comandi vocali con un suono simile. Esempio: "Mostra altro" e "Mostra archivio" possono avere un suono simile.
* Annullare la registrazione **dell'app** quando non viene utilizzata: quando l'app non si trova in uno stato in cui un determinato comando vocale è valido, è consigliabile annullarne la registrazione in modo che altri comandi non siano confusi per questo.
* **Esegui test con accenti diversi**. Testa l'app con utenti con accenti diversi.
* **Mantieni la coerenza dei comandi vocali**. Se "Indietro" porta alla pagina precedente, mantieni questo comportamento nelle applicazioni.
* **Evitare di usare i comandi di** sistema: i comandi vocali seguenti sono riservati al sistema, quindi evitare di usarli nelle applicazioni:
   * "Ehi Cortana"
   * "Seleziona"
   * "Vai a start"

### <a name="advantages-of-voice-input"></a>Vantaggi dell'input vocale

L'input vocale è un modo naturale di comunicare le intenzioni. La voce è particolarmente utile per gli **attraversamenti di interfaccia** perché può aiutare gli utenti a eseguire più passaggi di un'interfaccia. Un utente potrebbe dire "torna indietro" mentre guarda una pagina Web, invece di dover passare verso l'alto e premere il pulsante Indietro nell'app. Questo piccolo risparmio di tempo ha un **potente** effetto emotivo sulla percezione dell'esperienza dell'utente e offre loro una piccola quantità di superpotenze. I comandi vocali rappresentano anche un pratico metodo di input quando hai le mani occupate oppure quando sei in modalità **multitasking**. Nei dispositivi in cui la digitazione su una tastiera è difficile, la **dettatura vocale** può essere un modo alternativo efficiente per immettere testo. Infine, in alcuni casi, quando l'accuratezza dello sguardo fisso e del movimento è limitata, la voce può contribuire a risolvere l'ambiguità della finalità dell'utente.  

**In che modo i comandi vocali possono rivelarsi utili per l'utente**
* Riducono i tempi: devono rendere l'obiettivo finale più efficiente.
* Riducono al minimo lo sforzo: devono rendere le attività più fluide e semplici.
* Riducono il carico cognitivo: sono intuitivi e facili da imparare e ricordare.
* È socialmente accettabile e deve adattarsi alle norme di comportamento sociale.
* Rappresentano la routine: i comandi vocali possono facilmente diventare un comportamento abituale.

### <a name="challenges-for-voice-input"></a>Problemi di input vocale

Anche se l'input vocale è ideale per molte applicazioni diverse, deve affrontare diverse sfide. La comprensione dei vantaggi e delle sfide per l'input vocale consente agli sviluppatori di app di effettuare scelte più intelligenti su come e quando usare l'input vocale e di creare un'esperienza ottimale per gli utenti.

**Input vocale per il controllo di input continuo** Il controllo con granularità fine è uno di questi. Ad esempio, un utente potrebbe voler modificare il volume nell'app per la musica. Può dire "più alto", ma non è chiaro quanto il sistema dovrebbe rendere il volume più alto. L'utente potrebbe dire: "Make it a little louder", but "a little" is difficult to quantify. Lo spostamento o il ridimensionamento degli ologrammi con la voce è molto difficile. 

**Affidabilità del rilevamento dell'input vocale** Anche se i sistemi di input vocale diventano sempre migliori, a volte possono ascoltare e interpretare erroneamente un comando vocale.
La chiave consiste nell'affrontare la sfida nell'applicazione. Inviare commenti e suggerimenti agli utenti quando il sistema è in ascolto e ciò che il sistema ha compreso chiarisce i potenziali problemi di comprensione del parlato degli utenti.  

**Input vocale negli spazi condivisi** La voce potrebbe non essere socialmente accettabile negli spazi condivisi con altri utenti.
Ecco alcuni esempi:
* L'utente potrebbe non voler intasare altri utenti (ad esempio, in una libreria non interattiva o in un ufficio condiviso)
* Gli utenti possono essere difficili da vedere parlare con se stessi in pubblico,
* Un utente può sembrare disagi nella dettatura di un messaggio personale o riservato (incluse le password) mentre altri sono in ascolto

**Input vocale di parole univoche o sconosciute** Le difficoltà per l'input vocale si verificano anche quando gli utenti dettano parole che potrebbero essere sconosciute al sistema, ad esempio nomi alternativi, alcune parole gergali o abbreviazioni. 

**Comandi vocali per l'apprendimento** Anche se l'obiettivo finale è quello di conversare naturalmente con il sistema, spesso le app si basano ancora su comandi vocali predefiniti specifici.
Una sfida associata a un set significativo di comandi vocali è come insegnare loro senza sovraccaricare l'utente e come aiutare l'utente a mantenerli. 

<br>

---

### <a name="voice-feedback-states"></a>Stati di feedback dei comandi vocali

Quando i comandi vocali vengono applicati in modo corretto, l'utente capisce **cosa può dire e ottiene un feedback chiaro** a indicare che il sistema ha **recepito correttamente i comandi**. Questi due segnali fanno sì che l'utente si senta sicuro di usare i comandi vocali come input principale. Di seguito è riportato un diagramma che illustra che cosa accade al cursore quando l'input vocale viene riconosciuto e come tale risultato viene comunicato all'utente.


:::row:::
    :::column:::
       ![1. Normale stato del cursore](images/voicefeedbackstates-regular.jpg)<br>
       **1. Normale stato del cursore**<br>
    :::column-end:::
    :::column:::
       ![2. Comunica il feedback vocale e quindi scompare](images/voicefeedbackstates-voice.jpg)<br>
        **2. Comunica il feedback vocale e quindi scompare**<br>
    :::column-end:::
    :::column:::
       ![*3. Stato normale del cursore](images/voicefeedbackstates-regular.jpg)<br>
       **3. Torna allo stato normale del cursore**<br>
    :::column-end:::
:::row-end:::

<br>

---

<br>

## <a name="top-things-users-should-know-about-speech-in-mixed-reality"></a>Nozioni di base sui comandi vocali che gli utenti devono conoscere per la realtà mista

* Pronunciare **"Seleziona"** quando si seleziona un pulsante come destinazione (è possibile usarlo in qualsiasi punto per selezionare un pulsante).
* Puoi pronunciare il **nome dell'etichetta di un pulsante della barra dell'app** in alcune app per eseguire un'azione. Ad esempio, quando si esamina un'app, un utente può pronunciare il comando "Remove" (Rimuovi) per rimuovere l'app dal mondo( in questo modo si risparmia tempo dalla necessità di selezionarla con la mano).
* È possibile avviare L'ascolto di Cortana **pronunciando "Hey Cortana".** Puoi porre domande ("Ehi Cortana, quanto è alta la Torre Eiffel?"), chiedere di aprire un'app ("Ehi Cortana, apri Netflix") o chiedere di visualizzare il menu di avvio ("Ehi Cortana, portami all'inizio") e altro ancora.

## <a name="common-questions-and-concerns-users-have-about-voice"></a>Domande e dubbi comuni degli utenti sui comandi vocali

* What can I say?
* Come posso sapere se il sistema mi ha capito correttamente?
   * Il sistema continua a interpretare i miei comandi vocali in modo errato.
   * Non reagisce quando pronuncio un comando vocale.
* Reagisce in modo non corretto quando pronuncio un comando vocale.
* Come posso indirizzare un comando vocale a una specifica app o un comando di app?
* Posso usare i comandi vocali per operazioni all'esterno del fotogramma olografico di HoloLens?

## <a name="communication"></a>Comunicazione

Per le applicazioni che vogliono sfruttare le opzioni di elaborazione dell'input audio personalizzate fornite da HoloLens, è importante comprendere le diverse categorie di flussi [audio](/windows/win32/api/audiosessiontypes/ne-audiosessiontypes-audio_stream_category) che l'app può usare. Windows 10 supporta diverse categorie di flussi e HoloLens ne usa tre per consentire l'elaborazione personalizzata per ottimizzare la qualità audio del microfono su misura per la voce, la comunicazione e altre, che possono essere usate per scenari di acquisizione audio dell'ambiente ambientale (cio' "camcorder").
* La categoria AudioCategory_Communications flusso è personalizzata per scenari di qualità delle chiamate e narrazione e fornisce al client un flusso audio mono a 16 kHz a 24 bit della voce dell'utente
* La categoria AudioCategory_Speech flusso è personalizzata per il motore vocale HoloLens (Windows) e fornisce un flusso mono a 16 kHz a 24 bit della voce dell'utente. Se necessario, questa categoria può essere usata dai motori di riconoscimento vocale di terze parti.
* La AudioCategory_Other è personalizzata per la registrazione audio dell'ambiente ambientale e fornisce al client un flusso audio stereo a 48 kHz a 24 bit.

Tutta questa elaborazione audio è accelerata dall'hardware, il che significa che le funzionalità svuotano molto meno potenza rispetto a quando la stessa elaborazione è stata eseguita sulla CPU HoloLens. Evitare di eseguire altre elaborazioni di input audio nella CPU per ottimizzare la durata della batteria del sistema e sfruttare l'elaborazione di input audio offloaded incorporata.

## <a name="languages"></a>Linguaggi

HoloLens 2 supporta [più lingue.](/hololens/hololens2-language-support) Tenere presente che i comandi vocali verranno sempre eseguiti nella lingua di visualizzazione del sistema anche se sono installate più tastiere o se le app tentano di creare un sistema di riconoscimento vocale in una lingua diversa.

## <a name="troubleshooting"></a>Risoluzione dei problemi

Se si verificano problemi durante l'uso di "select" e "Hey Cortana", provare a passare a uno spazio più silenzioso, allontanandosi dalla sorgente di rumore o pronunciando più altamente. Al momento, tutto il riconoscimento vocale in HoloLens è ottimizzato in modo specifico per i parlanti nativi Stati Uniti inglese.

Per Windows Mixed Reality Developer Edition versione 2017, la logica di gestione degli endpoint audio funzionerà correttamente (per sempre) dopo la disconnessione e il nuovo accesso al desktop del PC dopo la connessione HMD iniziale. Prima del primo evento di disconnessione/accesso dopo aver passato la Configurazione fuori rete WMR, l'utente poteva sperimentare vari problemi di funzionalità audio che vanno dall'assenza di audio a nessuna commutazione audio a seconda di come è stato configurato il sistema prima di connettere l'HMD per la prima volta.

<br>

---

## <a name="voice-input-in-mrtk-mixed-reality-toolkit-for-unity"></a>Input vocale in MRTK (Mixed Reality Toolkit) per Unity
Con **[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** è possibile assegnare facilmente un comando vocale su qualsiasi oggetto. Usare il profilo di input vocale **di** MRTK per definire le parole chiave. Assegnando lo script **SpeechInputHandler,** è possibile fare in modo che qualsiasi oggetto risponda alle parole chiave definite nel profilo di input vocale. SpeechInputHandler fornisce anche un'etichetta di conferma vocale per migliorare l'attendibilità dell'utente.

* [MRTK - Comando vocale](/windows/mixed-reality/mrtk-unity/features/input/speech)

---

## <a name="see-also"></a>Vedi anche

* [Sguardo e commit](gaze-and-commit.md)
* [Interazioni istintive](interaction-fundamentals.md)
* [Input vocale in DirectX](../develop/native/voice-input-in-directx.md)
* [Input vocale in Unity](../develop/unity/voice-input-in-unity.md)
---
title: Input vocale
description: L'input vocale è un input di base per HoloLens e per le cuffie immersive in realtà mista di Windows. La voce può essere usata per i comandi, la dettatura, il Cortana e altro ancora.
author: hak0n
ms.author: hakons
ms.date: 10/03/2019
ms.topic: article
keywords: GGV, voce, Cortana, sintesi vocale, input, auricolare realtà mista, cuffia di realtà mista di Windows, auricolare realtà virtuale, HoloLens, MRTK, Toolkit realtà mista, sguardo
ms.openlocfilehash: cc1ecd7d236748c3c4de77678e6f67c69a2c1af1
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/03/2021
ms.locfileid: "101759142"
---
# <a name="voice-input"></a>Input vocale

![Input vocale](images/UX_Hero_VoiceCommand.jpg)

La voce è una delle forme di input chiave per HoloLens. Consente di eseguire direttamente il comando di un ologramma senza dover usare i [movimenti di mano](gaze-and-commit.md#composite-gestures). L'input vocale può essere un modo naturale di comunicare le intenzioni. La voce è particolarmente utile per attraversare interfacce complesse, perché consente agli utenti di tagliare i menu nidificati con un unico comando.

L'input vocale è alimentato dallo [stesso motore](/windows/uwp/design/input/speech-recognition) che supporta la sintesi vocale in tutte le _app di Windows universale_. In HoloLens il riconoscimento vocale funzionerà sempre nella lingua di visualizzazione di Windows configurata nelle impostazioni del dispositivo. 

<br>

## <a name="voice-and-gaze"></a>Voice and sguardi

Quando si usano i comandi vocali, è il tipico meccanismo di destinazione, con un cursore a "Select" o per il canale del comando a un'applicazione che si sta esaminando. Potrebbe non essere necessario visualizzare alcun cursore _("vedere il cursore")_. Alcuni comandi vocali non richiedono una destinazione, ad esempio "go to Start" o "Hey Cortana".

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
        <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
        <td><a href="../discover/immersive-headset-hardware-details.md"><strong>Visori VR immersive</strong></a></td>
    </tr>
     <tr>
        <td>Input vocale</td>
        <td>✔️</td>
        <td>✔️</td>
        <td>✔️ (con microfono)</td>
    </tr>
</table>

## <a name="the-select-command"></a>Comando "Select"

**HoloLens (prima generazione)**

Anche senza aggiungere in modo specifico il supporto vocale all'app, gli utenti possono attivare gli ologrammi semplicemente pronunciando il comando "Select" del comando "System Voice". Questo comportamento è identico a quello di un [rubinetto d'aria](gaze-and-commit.md#composite-gestures) su HoloLens, facendo clic sul pulsante Seleziona nel [HoloLens clic](/hololens/hololens1-clicker)oppure premendo il trigger in un [controller di movimento della realtà mista di Windows](motion-controllers.md). Verrà visualizzato un suono e verrà visualizzata una descrizione comando con "Select" come conferma. "Select" è abilitato da un algoritmo di rilevamento parole chiave a basso consumo, che significa che è possibile pronunciarlo in qualsiasi momento con un minimo di durata della batteria. È anche possibile pronunciare "Select" con le proprie mani.

<br>

---

:::row:::
    :::column:::
        **HoloLens 2**<br><br>
        Per usare il comando voce "Select" in HoloLens 2, è necessario innanzitutto visualizzare il cursore di sguardi da usare come puntatore. Il comando per riportarlo è facile da ricordare, ovvero "Select".<br><br>
        Per uscire dalla modalità, usare di nuovo le mani toccando aria, avvicinando un pulsante con le dita o usando il gesto del sistema.<br>
        <br> 
        *Image: pronunciare "Select" per utilizzare il comando Voice per la selezione*
    :::column-end:::
        :::column:::
       ![Un utente può pronunciare "Select" per usare il comando Voice per una selezione.](images/kma-voice-select-00170.jpg)<br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="hey-cortana"></a>Salve Cortana

È possibile pronunciare "Hey Cortana" per visualizzare Cortana in qualsiasi momento. Non è necessario attendere che venga visualizzata per continuare a porre una domanda o fornire un'istruzione. Ad esempio, provare a pronunciare "Hey Cortana, qual è il meteo?" come singola frase. Per ulteriori informazioni su Cortana e sulle operazioni che è possibile eseguire, rivolgersi all'utente. Pronunciare "Hey Cortana, cosa posso dire?" verrà quindi eseguito il pull di un elenco di comandi funzionanti e consigliati. Se si è già nell'app Cortana, selezionare **?** icona sulla barra laterale per estrarre lo stesso menu.

**Comandi specifici di HoloLens**
* "Cosa posso dire?"
* "Vai a avvio"-anziché [Bloom](system-gesture.md#bloom) per visualizzare il [menu Start](../discover/navigating-the-windows-mixed-reality-home.md#start-menu)
* "Avvia <app> "
* "Sposta <app> qui"
* "Scattare un'immagine"
* "Avvia registrazione"
* "Arresta registrazione"
* "Mostra raggio della mano"
* "Nascondi raggio di mano"
* "Aumentare la luminosità"
* "Riduzione della luminosità"
* "Aumento del volume"
* "Diminuisci volume"
* "Mute" o "unmute"
* "Arresta il dispositivo"
* "Riavvia il dispositivo"
* "Vai a sospensione"
* "Qual è il tempo?"
* "Quanta batteria è rimasta?"

<br>

---

:::row:::
    :::column:::
        ## <a name="see-it-say-itbr"></a>"Vedere la voce"<br>
        HoloLens dispone di un modello "See it, Say it" per l'input vocale, in cui le etichette sui pulsanti indicano agli utenti i comandi vocali che possono dire. Ad esempio, quando si esamina una finestra dell'app in HoloLens (1st Gen), un utente può pronunciare il comando "Adjust" per modificare la posizione dell'app nel mondo.<br>
        <br>
        *Image: un utente può pronunciare il comando "Adjust", che viene visualizzato nella barra dell'app per modificare la posizione dell'app*
    :::column-end:::
        :::column:::
        ![space](images/spacer-20x582.png)<br>
        ![Quando si esamina una finestra o un ologramma dell'app, un utente può pronunciare il comando "Adjust" visualizzato nella barra dell'app per modificare la posizione dell'app nel mondo](images/microphone-600px.png)<br>
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        Quando le app seguono questa regola, gli utenti possono comprendere facilmente cosa dire per controllare il sistema. Quando si guarda un pulsante in HoloLens (1st Gen), viene visualizzata una descrizione comando "Voice Rest" che viene visualizzata dopo un secondo se il pulsante è abilitato per la voce e visualizza il comando per comunicare con "premere". Per rivelare le descrizioni comandi vocali in HoloLens 2, visualizzare il cursore vocale digitando "Select" o "What Can Say" (vedere l'immagine). <br>
        <br>
        *Image: i comandi "See it, Say it" vengono visualizzati sotto i pulsanti*
    :::column-end:::
        :::column:::
       ![Vedere i comandi visualizzati sotto i pulsanti](images/voice-seeitsayit-600px.png)<br><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="voice-commands-for-fast-hologram-manipulation"></a>Comandi vocali per la manipolazione rapida degli ologrammi

Ci sono molti comandi vocali che è possibile usare quando si guarda un ologramma per eseguire rapidamente attività di manipolazione. Questi comandi vocali funzionano con gli oggetti Windows e 3D dell'app che sono stati inseriti nel mondo.

**Comandi di manipolazione ologramma**
* Mi faccia
* Più grande | Migliorare
* Più piccoli

In HoloLens 2 è inoltre possibile creare interazioni più naturali in combinazione con l'occhio, che fornisce implicitamente informazioni contestuali sugli elementi a cui si fa riferimento. Ad esempio, è possibile esaminare un ologramma e pronunciare _il_ punto in cui si vuole posizionarlo e pronunciare " _qui_".
In alternativa, è possibile esaminare una parte olografica in un computer complesso e pronunciare: "fornire ulteriori informazioni su _questo_".

## <a name="discovering-voice-commands"></a>Individuazione di comandi vocali

Alcuni comandi, ad esempio i comandi per una manipolazione rapida precedente, possono essere nascosti. Per informazioni sui comandi che è possibile usare, osservare un oggetto e pronunciare "cosa si può dire?". Viene visualizzato un elenco di comandi possibili. È anche possibile usare il cursore Head sguardi per individuare e visualizzare le descrizioni comandi vocali per ogni pulsante davanti all'utente. 

Se si desidera un elenco completo, è sufficiente indicare "Mostra tutti i comandi" in qualsiasi momento. 

## <a name="dictation"></a>Dettatura

Invece di digitare con le scelte [aeree](gaze-and-commit.md#composite-gestures), la dettatura vocale può essere più efficiente per inserire il testo in un'app. Questo può accelerare significativamente l'input con minore impegno per l'utente.

![La dettatura vocale inizia selezionando il pulsante del microfono](images/micbuttonfordictation.png)<br>
*La dettatura vocale inizia selezionando il pulsante del microfono sulla tastiera*

Quando la tastiera olografica è attiva, è possibile passare alla modalità di dettatura anziché alla digitazione. Per iniziare, selezionare il microfono sul lato della casella input di testo.

## <a name="adding-voice-commands-to-your-app"></a>Aggiunta di comandi vocali all'app

Valuta l'opportunità di aggiungere comandi vocali a un'esperienza che stai creando. Voice è un potente strumento per controllare il sistema e le app. Poiché gli utenti parlano con tipi diversi di dialetti e accenti, la scelta corretta di parole chiave per il riconoscimento vocale garantisce che i comandi degli utenti vengano interpretati in modo non ambiguo.

### <a name="best-practices"></a>Procedure consigliate

Di seguito vengono illustrate alcune procedure che semplificheranno il riconoscimento vocale.
* **Usa comandi concisi**. Quando possibile, scegli parole chiave di due o più sillabe. Le parole di una sillaba tendono a usare suoni di vocali differenti se pronunciate da persone con accenti diversi. Esempio: "riprodurre video" è migliore di "riprodurre il video attualmente selezionato"
* **Usare un vocabolario semplice** , ad esempio: "show note" è migliore di "Show manifest"
* Assicurarsi che i **comandi non siano distruttivi** . Assicurarsi che le azioni del comando vocale non siano distruttive e che sia possibile annullarla in caso di un'altra persona che parla vicino all'utente accidentalmente un comando.
* **Evitare comandi audio simili** . evitare di registrare più comandi vocali che sembrano simili. Esempio: "Mostra più" e "Mostra archivio" può essere un suono simile.
* **Annulla la registrazione dell'app quando non usa** -quando l'app non è in uno stato in cui un particolare comando vocale è valido, è consigliabile annullarne la registrazione in modo che gli altri comandi non siano confusi.
* **Esegui test con accenti diversi**. Testa l'app con utenti con accenti diversi.
* **Mantieni la coerenza dei comandi vocali**. Se "Indietro" porta alla pagina precedente, mantieni questo comportamento nelle applicazioni.
* **Evitare di usare i comandi di sistema** : i comandi vocali seguenti sono riservati per il sistema, quindi evitare di usarli nelle applicazioni:
   * "Ehi Cortana"
   * "Seleziona"
   * "Vai all'avvio"

### <a name="advantages-of-voice-input"></a>Vantaggi dell'input vocale

L'input vocale è un modo naturale di comunicare le intenzioni. La voce è particolarmente utile negli **attraversamenti** dell'interfaccia perché può aiutare gli utenti a tagliare più passaggi di un'interfaccia. Un utente potrebbe dire "tornare indietro" guardando una pagina Web, anziché dover passare al pulsante indietro nell'app. Questo piccolo risparmio di tempo ha un forte **effetto emotivo** sulla percezione dell'esperienza dell'utente e offre una piccola superpotenza. I comandi vocali rappresentano anche un pratico metodo di input quando hai le mani occupate oppure quando sei in modalità **multitasking**. Nei dispositivi in cui la digitazione su una tastiera è difficile, la **Dettatura vocale** può essere un metodo alternativo efficace per inserire il testo. Infine, in alcuni casi, quando l' **intervallo di accuratezza** per lo sguardo e il movimento sono limitati, Voice può contribuire a evitare ambiguità tra le finalità dell'utente. 

**In che modo i comandi vocali possono rivelarsi utili per l'utente**
* Riducono i tempi: devono rendere l'obiettivo finale più efficiente.
* Riducono al minimo lo sforzo: devono rendere le attività più fluide e semplici.
* Riducono il carico cognitivo: sono intuitivi e facili da imparare e ricordare.
* È socialmente accettabile. dovrebbe adattarsi alle normative di comportamento della società.
* Rappresentano la routine: i comandi vocali possono facilmente diventare un comportamento abituale.

### <a name="challenges-for-voice-input"></a>Problemi per l'input vocale

Anche se l'input vocale è ideale per molte applicazioni diverse, presenta anche diverse problemi. Comprendere i vantaggi e le esigenze per l'input vocale consente agli sviluppatori di app di prendere scelte più intelligenti per sapere come e quando usare l'input vocale e per creare un'esperienza ottimale per gli utenti.

**Input vocale per il controllo di input continuo** Il controllo con granularità fine è uno di essi. Ad esempio, un utente potrebbe voler modificare il volume nella propria app musicale. Può dire "più forte", ma non è chiaro quanto sia forte il sistema che deve creare il volume. L'utente può affermare: "renderlo un po' più forte", ma è difficile quantificare "un po'". Lo stato di scalabilità o di ridimensionamento degli ologrammi con la voce è simile. 

**Affidabilità del rilevamento dell'input vocale** Sebbene i sistemi di input vocali siano migliori e migliori, a volte potrebbero non essere in grado di ascoltare e interpretare un comando vocale.
La chiave consiste nel risolvere il problema nell'applicazione. Fornire commenti e suggerimenti agli utenti quando il sistema è in ascolto e ciò che il sistema ha compreso chiarisce i potenziali problemi relativi alla sintesi vocale degli utenti.  

**Input vocale negli spazi condivisi** La voce potrebbe non essere socialmente accettabile negli spazi condivisi con altri utenti.
Ecco alcuni esempi:
* L'utente potrebbe non voler disturbare altri, ad esempio in una libreria non interattiva o in un ufficio condiviso
* Gli utenti potrebbero sembrare imbarazzanti,
* Un utente potrebbe non essere scomodo a indicare un messaggio personale o riservato (incluse le password) mentre altri sono in ascolto

**Input vocale di parole univoche o sconosciute** Le difficoltà per l'input vocale si verificano anche quando gli utenti impongono parole che potrebbero essere sconosciute al sistema, ad esempio nomi alternativi, parole slang specifiche o abbreviazioni. 

**Apprendimento di comandi vocali** Anche se l'obiettivo finale è quello di comunicare naturalmente con il sistema, spesso le app si basano su comandi vocali predefiniti specifici.
Un problema associato a un set significativo di comandi vocali è come insegnarli senza sovraccaricare l'utente e come aiutarli a mantenerli. 

<br>

---

### <a name="voice-feedback-states"></a>Stati di feedback dei comandi vocali

Quando i comandi vocali vengono applicati in modo corretto, l'utente capisce **cosa può dire e ottiene un feedback chiaro** a indicare che il sistema ha **recepito correttamente i comandi**. Questi due segnali fanno sì che l'utente si senta sicuro di usare i comandi vocali come input principale. Di seguito è riportato un diagramma che illustra che cosa accade al cursore quando l'input vocale viene riconosciuto e come tale risultato viene comunicato all'utente.


:::row:::
    :::column:::
       ![1. stato del cursore normale](images/voicefeedbackstates-regular.jpg)<br>
       **1. stato del cursore normale**<br>
    :::column-end:::
    :::column:::
       ![2. comunica il feedback vocale e scompare](images/voicefeedbackstates-voice.jpg)<br>
        **2. comunica il feedback vocale e scompare**<br>
    :::column-end:::
    :::column:::
       ![3. Stato normale del cursore](images/voicefeedbackstates-regular.jpg)<br>
       **3. torna allo stato normale del cursore**<br>
    :::column-end:::
:::row-end:::

<br>

---

<br>

## <a name="top-things-users-should-know-about-speech-in-mixed-reality"></a>Nozioni di base sui comandi vocali che gli utenti devono conoscere per la realtà mista

* Pronunciare **"Select"** mentre si sceglie come destinazione un pulsante (è possibile usarlo in qualsiasi punto per selezionare un pulsante).
* Puoi pronunciare il **nome dell'etichetta di un pulsante della barra dell'app** in alcune app per eseguire un'azione. Ad esempio, quando si esamina un'app, un utente può pronunciare il comando "Remove" per rimuovere l'app dal mondo. in questo modo si evita di dover selezionare la propria mano.
* È possibile avviare Cortana in attesa dicendo **"Hey Cortana".** Puoi porre domande ("Ehi Cortana, quanto è alta la Torre Eiffel?"), chiedere di aprire un'app ("Ehi Cortana, apri Netflix") o chiedere di visualizzare il menu di avvio ("Ehi Cortana, portami all'inizio") e altro ancora.

## <a name="common-questions-and-concerns-users-have-about-voice"></a>Domande e dubbi comuni degli utenti sui comandi vocali

* What can I say?
* Come posso sapere se il sistema mi ha capito correttamente?
   * Il sistema continua a interpretare i miei comandi vocali in modo errato.
   * Non reagisce quando pronuncio un comando vocale.
* Reagisce in modo non corretto quando pronuncio un comando vocale.
* Come posso indirizzare un comando vocale a una specifica app o un comando di app?
* Posso usare i comandi vocali per operazioni all'esterno del fotogramma olografico di HoloLens?

## <a name="communication"></a>Comunicazione

Per le applicazioni che vogliono sfruttare le opzioni di elaborazione dell'input audio personalizzato fornite da HoloLens, è importante comprendere le diverse categorie di [flussi audio](/windows/win32/api/audiosessiontypes/ne-audiosessiontypes-audio_stream_category) che l'app può utilizzare. Windows 10 supporta diverse categorie di flusso e HoloLens ne usa tre per consentire l'elaborazione personalizzata per ottimizzare la qualità audio del microfono personalizzata per la comunicazione vocale, la comunicazione e altro, che può essere usata per gli scenari di acquisizione audio dell'ambiente di ambiente (ovvero "videocamera").
* La categoria AudioCategory_Communications Stream è personalizzata per gli scenari di qualità della chiamata e di narrazione e fornisce al client un flusso audio mono a 16 kHz a 24 bit della voce dell'utente
* La categoria del flusso di AudioCategory_Speech è personalizzata per il motore di riconoscimento vocale HoloLens (Windows) e fornisce un flusso mono a 24 bit a 16 kHz della voce dell'utente. Questa categoria può essere usata dai motori di sintesi vocale di terze parti, se necessario.
* La categoria AudioCategory_Other Stream è personalizzata per la registrazione audio dell'ambiente di ambiente e fornisce al client un flusso audio stereo a 48 kHz a 24 bit.

Questa elaborazione audio è accelerata dall'hardware, il che significa che le funzionalità svuotano molto meno energia rispetto a quando la stessa elaborazione è stata eseguita sulla CPU HoloLens. Evitare di eseguire altre elaborazioni di input audio sulla CPU per ottimizzare la durata della batteria del sistema e sfruttare i vantaggi dell'elaborazione incorporata di input audio con offload.

## <a name="languages"></a>Linguaggi

HoloLens 2 [supporta più lingue](/hololens/hololens2-language-support). Tenere presente che i comandi vocali verranno sempre eseguiti nella lingua di visualizzazione del sistema anche se sono installate più tastiere o se le app tentano di creare un riconoscimento vocale in una lingua diversa.

## <a name="troubleshooting"></a>Risoluzione dei problemi

Se si verificano problemi con "Select" e "Hey Cortana", provare a passare a uno spazio più silenzioso, a disattivarsi dall'origine del rumore o a una voce più forte. A questo punto, tutto il riconoscimento vocale in HoloLens viene ottimizzato e ottimizzato in modo specifico per gli altoparlanti nativi di Stati Uniti inglese.

Per la versione 2017 di Windows Mixed Reality Developer Edition, la logica di gestione degli endpoint audio funzionerà correttamente (per sempre) dopo la disconnessione e l'accesso al desktop del PC dopo la connessione iniziale di HMD. Prima della prima disconnessione/evento dopo aver attraversato la configurazione guidata di WMR, l'utente può riscontrare diversi problemi di funzionalità audio che variano da nessuna audio a nessuna modifica audio a seconda di come è stato configurato il sistema prima di connettere HMD per la prima volta.

<br>

---

## <a name="voice-input-in-mrtk-mixed-reality-toolkit-for-unity"></a>Input vocale in MRTK (Mixed Reality Toolkit) per Unity
Con **[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)**, è possibile assegnare facilmente il comando Voice a tutti gli oggetti. Usare **il profilo di input vocale** di MRTK per definire le parole chiave. Assegnando lo script **SpeechInputHandler** , è possibile fare in modo che qualsiasi oggetto risponda alle parole chiave definite nel profilo di input vocale. SpeechInputHandler fornisce anche un'etichetta di conferma vocale per migliorare la confidenza dell'utente.

* [Comando MRTK-Voice](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/input/speech.md)

---

## <a name="see-also"></a>Vedi anche

* [Sguardo e commit](gaze-and-commit.md)
* [Interazioni istintive](interaction-fundamentals.md)
* [Input vocale in DirectX](../develop/native/voice-input-in-directx.md)
* [Input vocale in Unity](../develop/unity/voice-input-in-unity.md)
---
title: Sguardo fisso e commit
description: Informazioni sul modello di input dello sguardo e del commit, tra cui due tipi di sguardo (sguardo alla testa e sguardo oculare) e vari tipi di commit.
author: sostel
ms.author: sostel
ms.date: 10/31/2019
ms.topic: article
keywords: Realtà mista, sguardo, targeting dello sguardo, interazione, progettazione, tracciamento oculare, tracciamento della testa, visore di realtà mista, visore windows mixed reality, visore di realtà virtuale, HoloLens, MRTK, realtà mista Toolkit
ms.openlocfilehash: 98f2ac9d26fc02c969520fff9083152b77bf66a2f864d5fdb15b1ee781d5d7cb
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115201896"
---
# <a name="gaze-and-commit"></a>Sguardo fisso e commit

_Lo sguardo e il commit_ sono un modello di input fondamentale strettamente correlato al modo in cui si interagisce con i computer usando il mouse: punto & _clic._ In questa pagina vengono presentati due tipi di input dello sguardo (head e eye-gaze) e diversi tipi di azioni di commit. _Lo sguardo e il commit_ sono considerati un modello di input lontano con manipolazione indiretta. È ideale per interagire con contenuti olografici non raggiungibili.

I visori di realtà mista possono usare la posizione e l'orientamento della testa dell'utente per determinare il vettore di direzione della testa. Si pensi a uno sguardo come a un laser che punta direttamente tra gli occhi dell'utente. Questa è una grossolana approssimazione del punto guardato dall'utente. L'applicazione può intersecare questo raggio con oggetti virtuali o reali e disegnare un cursore in tale posizione per instradare l'utente al targeting.

Oltre allo sguardo della testa, alcuni visori di realtà mista, ad esempio HoloLens 2, includono sistemi di tracciamento oculare che producono un vettore di sguardo oculare. In questo modo si ottiene una misurazione precisa di dove sta guardando l'utente. In entrambi i casi, lo sguardo fisso rappresenta un segnale importante per la finalità dell'utente. Maggiore è la capacità del sistema di interpretare e stimare le azioni previste dall'utente, maggiore sarà la soddisfazione e le prestazioni dell'utente.

Di seguito sono riportati alcuni esempi di come uno sviluppatore di realtà mista può trarre vantaggio dalla testa o dallo sguardo oculare:
* L'app può intersecare lo sguardo con gli ologrammi nella scena per determinare dove si trova l'attenzione dell'utente (più precisa con lo sguardo oculare).
* L'app può incanala i movimenti e le pressione del controller in base alla visualizzazione dell'utente, che consente all'utente di selezionare, attivare, afferrare, scorrere o interagire in altro modo con gli ologrammi.
* L'app può consentire all'utente di posizionare ologrammi su superfici reali intersecando il raggio dello sguardo con la mesh di mapping spaziale.
* L'app può sapere quando l'utente non sta cercando nella direzione di un oggetto importante, il che può portare l'app a fornire segnali visivi e audio per rivolgersi a tale oggetto.

<br>

## <a name="device-support"></a>Supporto di dispositivi

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><strong>Modello di input</strong></td>
        <td><a href="/hololens/hololens1-hardware"><strong>HoloLens (prima generazione)</strong></a></td>
        <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
        <td><a href="../discover/immersive-headset-hardware-details.md"><strong>Visori VR immersive</strong></a></td>
    </tr>
     <tr>
        <td>Puntamento con la testa e commit</td>
        <td>✔️ Consigliato</td>
        <td>✔️ Consigliato (terza scelta - <a href="interaction-fundamentals.md">Vedi le altre opzioni</a>)</td>
        <td>➕ Opzione alternativa</td>
    </tr>
         <tr>
        <td>Sguardo fisso e commit</td>
        <td>❌ Non disponibile</td>
        <td>✔️ Consigliato (terza scelta - <a href="interaction-fundamentals.md">Vedi le altre opzioni</a>)</td>
        <td>❌ Non disponibile</td>
    </tr>
</table>

## <a name="head-and-eye-tracking-design-concepts-demo"></a>Demo dei concetti di progettazione del rilevamento oculare e della testa

Se si desidera vedere i concetti di progettazione di Head e Eye Tracking in azione, vedere la demo video Progettazione **di Ologrammi - Tracciamento** testina e tracciamento oculare di seguito. Al termine, continuare per un'analisi più dettagliata di argomenti specifici.

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Microsofts-Designing-Holograms-Head-Tracking-and-Eye-Tracking-Chapter/player]

*Questo video è stato tratto dall'app "Progettazione Ologrammi" HoloLens 2 app. Scaricare e usufruire dell'esperienza completa [qui.](https://aka.ms/dhapp)*

## <a name="gaze"></a>Sguardo fisso

### <a name="eye--or-head-gaze"></a>Sguardo oculare o sguardo con la testa?
Di fronte alla domanda se è consigliabile usare il modello di input "eye-gaze and commit" o "head-gaze and commit", è necessario tenere presente alcune considerazioni. Se si sviluppa per un visore immersivo o per HoloLens (prima generazione), la scelta è semplice: head-gaze e commit. Se si sta sviluppando per HoloLens 2, la scelta diventa un po' più difficile. È importante comprendere i vantaggi e le sfide che si presentano con ognuno di essi.
Nella tabella seguente sono stati compilati alcuni pro e contro generali per contrapporre il targeting della testa e dello sguardo oculare. Questa operazione non è completa e si consiglia di apprendere di più sul targeting dello sguardo visivo nella realtà mista qui:
* [Tracciamento oculare HoloLens 2:](eye-tracking.md)introduzione generale della nuova funzionalità di tracciamento oculare HoloLens 2 incluse alcune indicazioni per gli sviluppatori. 
* [Interazione con lo sguardo oculare:](eye-gaze-interaction.md)considerazioni e raccomandazioni di progettazione quando si prevede di usare il tracciamento oculare come input.

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
   <tr>
        <td><strong>Targeting con sguardo fisso</strong></td>
        <td><strong>Selezione della destinazione mediante puntamento con la testa</strong></td>
    </tr>
    <tr>
        <td>veloce!</td>
        <td>più lento</td>
    </tr>
    <tr>
        <td>Basso sforzo (quasi tutti i movimenti del corpo necessari)</td>
        <td>Può essere fatiguing - Possibile disturbo (ad esempio, ceppo del collo)</td>
    </tr>
    <tr>
        <td>Non richiede un cursore, ma è consigliabile un feedback sottile</td>
        <td>Richiede la visualizzazione di un cursore</td>
    </tr>
    <tr>
        <td>Nessun movimento smussato degli occhi, ad esempio non è un bene per il disegno</td>
        <td>Più controllato ed esplicito</td>
    </tr>
    <tr>
        <td>Difficile per le destinazioni di piccole dimensioni (ad esempio, pulsanti piccoli o weblink)</td>
        <td>Affidabile! Ottimo fallback.</td>
    </tr>
    <tr>
        <td>...</td>
        <td>...</td>
    </tr>
</table>

Sia che si usi lo sguardo con la testa o lo sguardo oculare per il modello di input gaze-and-commit, ogni modello include set diversi di vincoli di progettazione. Questi articoli sono trattati separatamente negli articoli [relativi al commit](gaze-and-commit-eyes.md) e alla testa e al [commit.](gaze-and-commit-head.md)

<br>

---

### <a name="cursor"></a>Cursore

:::row:::
    :::column:::
        Per lo sguardo con la testa, la maggior parte delle app deve usare un [cursore](cursors.md) o un'altra indicazione udibile/visiva per offrire all'utente l'attendibilità di ciò con cui sta per interagire. Questo cursore viene in genere posizionato nel mondo in cui il raggio dello sguardo interseca per la prima volta un oggetto, che può essere un ologramma o una superficie reale.<br>
        <br>
        Per lo sguardo fisso, in genere è *consigliabile* non visualizzare un cursore, perché può diventare rapidamente distratto e fastidioso per l'utente. È invece possibile evidenziare in modo subdotto le destinazioni visive o usare un cursore oculare debole per fornire sicurezza su ciò con cui l'utente sta per interagire. Per altre informazioni, vedere le linee guida [per la progettazione per l'input basato sugli](eye-tracking.md) HoloLens 2.
    :::column-end:::
        :::column:::
       ![Un cursore visivo di esempio per visualizzare lo sguardo](images/cursor.jpg)<br>
       *Immagine: un cursore visivo di esempio per visualizzare lo sguardo*
    :::column-end:::
:::row-end:::

<br>

---

## <a name="commit"></a>Commit
Dopo aver parlato  di diversi modi per osservare una destinazione, si parlerà un po' di più della parte _di commit_ nello sguardo e _del commit._
Dopo aver selezionato come destinazione un oggetto o un elemento dell'interfaccia utente, l'utente può interagire o fare clic su di esso usando un input secondario. Questo processo è noto come passaggio di commit del modello di input. 

Sono supportati i metodi di commit seguenti:
- Movimento della mano del tocco dell'aria(ovvero, alzare la mano davanti all'utente e riunire l'indice e il pollice)
- Pronunciare _"select"_ o uno dei comandi vocali di destinazione
- Premere un singolo pulsante in un HoloLens [clic](/hololens/hololens1-clicker)
- Premere il pulsante "A" in un gamepad Xbox
- Premere il pulsante "A" su un controller adattivo Xbox

### <a name="gaze-and-air-tap-gesture"></a>Movimento di tocco dello sguardo e dell'aria
Per simulazione del tocco si intende un gesto tocco fatto con la mano mantenuta in verticale. Per usare un tocco d'aria, alzare il dito dell'indice fino alla posizione pronta, quindi avvicinare il pollice e alzare il dito dell'indice per rilasciare. Nella HoloLens (prima generazione), il tocco dell'aria è l'input secondario più comune.


:::row:::
    :::column:::
       ![Dito nella posizione pronta](images/readyandpress-ready.jpg)<br>
       **Dito nella posizione pronta**<br>
    :::column-end:::
    :::column:::
       ![Premere il dito verso il basso per toccare o fare clic](images/readyandpress-press.jpg)<br>
        **Premere il dito verso il basso per toccare o fare clic**<br>
    :::column-end:::
:::row-end:::


Il tocco dell'aria è disponibile anche HoloLens 2. È stato rimosso dalla versione originale. Quasi tutti i tipi di pizzicamento sono ora supportati purché la mano sia in posizione verticale e in attesa. Questo rende molto più semplice per gli utenti imparare e usare il movimento. Questo nuovo tocco di aria sostituisce quello precedente tramite la stessa API, in modo che le applicazioni esistenti avranno il nuovo comportamento automaticamente dopo la ricompilazione per HoloLens 2.

<br>

---

### <a name="gaze-and-select-voice-command&quot;></a>Sguardo fisso e comando vocale &quot;Seleziona&quot;
Il comando vocale è uno dei metodi di interazione principali nella realtà mista. Fornisce un potente meccanismo hands-free per controllare il sistema. Esistono diversi tipi di modelli di interazione vocale:

- Comando generico &quot;Select&quot; che usa un'actuation click o un commit come input secondario.
- I comandi dell'oggetto (ad esempio, &quot;Chiudi&quot; o &quot;Aumenta dimensioni") eseguono ed eseguono il commit in un'azione come input secondario.
- I comandi globali , ad esempio "Vai a start", non richiedono una destinazione.
- Le interfacce utente di conversazione o le entità come Cortana hanno una funzionalità del linguaggio naturale di intelligenza artificiale.
- Comandi vocali personalizzati

Per altre informazioni sui dettagli e un elenco completo dei comandi vocali disponibili e su come usarli, vedere le linee guida per l'esecuzione [di comandi](../out-of-scope/voice-design.md) vocali.

<br>

---


### <a name="gaze-and-hololens-clicker"></a>Sguardo fisso e HoloLens clicker

:::row:::
    :::column:::
        Il HoloLens Clicker è il primo dispositivo periferico creato appositamente per HoloLens. È incluso in HoloLens (prima generazione) Development Edition. Il HoloLens Clicker consente a un utente di fare clic con un movimento minimo della mano ed eseguire il commit come input secondario. Il HoloLens Clicker si connette a HoloLens (prima generazione) o HoloLens 2 usando Bluetooth Low Energy (BTLE).<br>
        <br>
        [Altre informazioni e istruzioni per associare il dispositivo](../discover/hardware-accessories.md#pairing-bluetooth-accessories)<br>
        <br>
        *Immagine: HoloLens Clicker*
    :::column-end:::
        :::column:::
       ![Dispositivo Clicker HoloLens](images/hololens-clicker-500px.jpg)<br>
    :::column-end:::
:::row-end:::

<br>

---


### <a name="gaze-and-xbox-wireless-controller"></a>Sguardo fisso e controller wireless Xbox

:::row:::
    :::column:::
        Il controller wireless Xbox esegue un clic come input secondario usando il pulsante "A". Il dispositivo viene mappato a un set predefinito di azioni che consentono di esplorare e controllare il sistema. Se si vuole personalizzare il controller, usare l'Accessori Xbox per configurare il controller wireless Xbox.<br>
        <br>
        [Come associare un controller Xbox al PC](../discover/hardware-accessories.md#pairing-bluetooth-accessories)<br>
        <br>
        *Immagine: Controller wireless Xbox*
    :::column-end:::
        :::column:::
       ![Controller wireless Xbox](images/xboxcontroller.jpg)<br>
    :::column-end:::
:::row-end:::



<br>

---


### <a name="gaze-and-xbox-adaptive-controller"></a>Sguardo fisso e controller adattivo Xbox
Progettato principalmente per soddisfare le esigenze dei giocatori con mobilità limitata, il controller adattivo Xbox è un hub unificato per i dispositivi che consente di rendere la realtà mista più accessibile.

Il controller adattivo Xbox esegue un clic come input secondario usando il pulsante "A". Il dispositivo viene mappato a un set predefinito di azioni che consentono di esplorare e controllare il sistema. Se si vuole personalizzare il controller, usare l'applicazione Accessori Xbox per configurare il controller adattivo Xbox.

![Controller adattivo Xbox](images/xbox-adaptive-controller-devices.jpg)<br>
*Controller adattivo Xbox*

Connessione dispositivi esterni, ad esempio interruttori, pulsanti, montanti e levette, per creare un'esperienza controller personalizzata che sia esclusiva dell'utente. Gli input di pulsanti, levette e trigger sono controllati con dispositivi di assistive connessi tramite jack da 3,5 mm e porte USB.

![Porte del controller adattivo Xbox](images/xbox-adaptive-controller-ports.jpg)<br>
*Porte del controller adattivo Xbox*

[Istruzioni per associare il dispositivo](../discover/hardware-accessories.md#pairing-bluetooth-accessories)

<a href=https://www.xbox.com/xbox-one/accessories/controllers/xbox-adaptive-controller>Altre informazioni disponibili sul sito Xbox</a>

<br>

---

## <a name="composite-gestures"></a>Movimenti compositi

### <a name="air-tap"></a>Simulazione del tocco
Il movimento di tocco dell'aria (e gli altri movimenti seguenti) reagisce solo a un tocco specifico. Per rilevare altri tocchi, ad esempio Menu o Afferra, l'applicazione deve usare direttamente le interazioni di livello inferiore descritte nella sezione precedente relativa ai due movimenti dei componenti chiave.

### <a name="tap-and-hold"></a>Tocco e pressione prolungata
La pressione prolungata consiste nel mantenere la posizione del dito abbassato della simulazione del tocco. La combinazione di tocco e sospensione dell'aria consente diverse interazioni più complesse di "clic e trascinamento" se combinate con il movimento del arm, ad esempio la selezione di un oggetto invece di attivarlo o le interazioni secondarie con il mouse, ad esempio la visualizzazione di un menu di scelta rapida.
È tuttavia necessario prestare attenzione durante la progettazione per questo movimento, in quanto gli utenti possono essere increditi a distondersi dalle posture della mano durante qualsiasi movimento esteso.

### <a name="manipulation"></a>modifica
I movimenti di manipolazione possono essere usati per spostare, ridimensionare o ruotare un ologramma quando si vuole che l'ologramma reagisca 1:1 ai movimenti della mano dell'utente. Uno degli usi possibili di tali movimenti 1:1 è quello di consentire all'utente di disegnare o dipingere nel mondo.
La selezione iniziale della destinazione per un movimento di manipolazione dovrebbe avvenire mediante sguardo fisso o puntamento. Una volta avviato il tocco e il controllo, qualsiasi manipolazione degli oggetti viene gestita dai movimenti della mano, che consentono all'utente di guardarsi attorno mentre manipola.

### <a name="navigation"></a>Spostamento
I movimenti di navigazione funzionano come un joystick virtuale e possono essere usati per spostarsi nei widget dell'interfaccia utente, ad esempio nei menu radiali. Tocca e tieni premuto per avviare il movimento, quindi sposta la mano all'interno di un cubo 3D normalizzato, centrato attorno al punto di pressione iniziale. È possibile spostare la mano lungo l'asse X, Y o Z da un valore compreso tra -1 e 1, dove 0 è il punto iniziale.
La navigazione può essere usata per creare movimenti continui di scorrimento o zoom basati sulla velocità, analoghi allo scorrimento di un'interfaccia utente 2D mediante il clic sul pulsante centrale del mouse e il successivo spostamento del mouse verso l'alto o il basso.

La navigazione con le guide si riferisce alla capacità di riconoscere i movimenti in un determinato asse fino a quando non viene raggiunta una determinata soglia su tale asse. Ciò è utile solo quando lo sviluppatore attiva lo spostamento in più di un asse in un'applicazione, ad esempio se un'applicazione è configurata per riconoscere i movimenti di navigazione sull'asse X, Y ma anche l'asse X specificato con guide. In questo caso, il sistema riconoscerà i movimenti delle mani sull'asse X purché rimangano all'interno di guide immaginarie sull'asse X, se il movimento della mano si verifica anche sull'asse Y.

Nelle app 2D gli utenti possono usare movimenti di navigazione verticali per scorrere, eseguire lo zoom o trascinare all'interno dell'app. In questo modo vengono inseriti nell'app tocchi delle dita virtuali per simulare tocchi dello stesso tipo. Gli utenti possono selezionare quali di queste azioni vengono eseguite selezionando gli strumenti nella barra sopra l'applicazione, selezionando il pulsante o pronunciando "Strumento di scorrimento<scorrimento/trascinamento/zoom>".

[Altre informazioni sui movimenti compositi](gaze-and-commit.md#composite-gestures)

## <a name="gesture-recognizers"></a>Strumenti di riconoscimento dei movimenti

Uno dei vantaggi dell'uso del riconoscimento dei movimenti è che è possibile configurare un sistema di riconoscimento movimenti solo per i movimenti che l'ologramma di destinazione può accettare. La piattaforma non distingue solo le ambiguità necessarie per distinguere i movimenti supportati specifici. In questo modo, un ologramma che supporta solo il tocco può accettare qualsiasi periodo di tempo tra la pressione e il rilascio, mentre un ologramma che supporta sia il tocco che il tocco può alzare di livello il tocco a un blocco dopo la soglia di tempo di attesa.

## <a name="hand-recognition"></a>Riconoscimento della mano
HoloLens riconosce i movimenti della mano tenendo traccia della posizione di una o di entrambe le mani visibili al dispositivo. HoloLens vede le mani quando sono in stato pronto (dorso della mano rivolto verso di te con il dito indice alzato) o in stato premuto (dorso della mano rivolto verso di te con il dito indice abbassato). Quando le mani sono in altre posizioni, HoloLens le ignora.
Per ogni mano rilevata HoloLens, è possibile accedere alla relativa posizione senza orientamento e stato premuto. Non appena la mano si avvicina al bordo della cornice di movimento, viene fornito anche un vettore direzionale che puoi decidere di mostrare all'utente in modo che sappia come muovere la mano per riportarla dove può essere vista da HoloLens.

## <a name="gesture-frame"></a>Cornice di movimento
Per i movimenti in HoloLens, la mano deve essere all'interno di un fotogramma del movimento, in un intervallo che le fotocamere di rilevamento dei movimenti possono vedere in modo appropriato, dal rosso al collo e tra le camere. Gli utenti devono essere formati su quest'area di riconoscimento sia per il successo dell'azione che per il proprio comfort. Molti utenti presupporranno inizialmente che il fotogramma del movimento sia all'interno della propria visualizzazione tramite HoloLens e tenere le mani impresciamente a interagire. Quando si usa HoloLens clicker, non è necessario che le mani siano all'interno della cornice del movimento.

Per i movimenti continui, in particolare, c'è il rischio che gli utenti slocino le mani all'esterno del fotogramma del movimento mentre sono durante il movimento durante lo spostamento di un oggetto olografico, ad esempio, e la perdita del risultato previsto.

Sono tre gli aspetti da considerare:

- Formazione dell'utente sull'esistenza del fotogramma del movimento e sui limiti approssimativi. Questo viene insegnato durante la HoloLens configurazione.

- Notificare agli utenti quando i movimenti si avvicinano o violano i limiti dei fotogrammi del movimento all'interno di un'applicazione al punto che un movimento perso genera risultati indesiderati. La ricerca ha mostrato le qualità chiave di un sistema di notifica di questo tipo. La HoloLens shell fornisce un buon esempio di questo tipo di notifica, ovvero l'oggetto visivo, sul cursore centrale, che indica la direzione in cui è in corso l'attraversamento dei limiti.

- Necessità di ridurre al minimo le conseguenze del superamento dei limiti della cornice di movimento. In generale, ciò significa che il risultato di un movimento deve essere arrestato al limite e non invertito. Ad esempio, se un utente sposta un oggetto olografico in una stanza, il movimento deve interrompersi quando il fotogramma del movimento viene violato e non viene restituito al punto iniziale. L'utente potrebbe provare frustrazione, ma potrebbe comprendere più rapidamente i limiti e non dover riavviare ogni volta le azioni necessarie complete.



## <a name="see-also"></a>Vedi anche
* [Interazione basata sullo sguardo](eye-gaze-interaction.md)
* [Tracciamento oculare in HoloLens 2](eye-tracking.md)
* [Sguardo fisso e attesa](gaze-and-dwell.md)
* [Mani - Manipolazione diretta](direct-manipulation.md)
* [Mani - Movimenti](gaze-and-commit.md#composite-gestures)
* [Mani - Puntamento e commit](point-and-commit.md)
* [Interazioni istintive](interaction-fundamentals.md)
* [Input vocale](voice-input.md)
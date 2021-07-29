---
title: Modulo lunare
description: Scopri come estendere i movimenti HoloLens base con il rilevamento a due mani e l'input del controller Xbox, creare oggetti reattivi e implementare sistemi di menu.
author: radicalad
ms.author: adlinv
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, App di esempio, Progettazione, MRTK, Mixed Reality Toolkit, Unity, app di esempio, app di esempio, open source, Microsoft Store, HoloLens, visore VR di realtà mista, visore VR di realtà mista windows, visore VR di realtà virtuale
ms.openlocfilehash: 4a736990a94d7f5c97a1bfc2edf998e327071bcb
ms.sourcegitcommit: 9831b89a1641ba1b5df14419ee2a4f29d3fa2d64
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/29/2021
ms.locfileid: "114757223"
---
# <a name="lunar-module"></a>Modulo lunare

>[!NOTE]
>Questo articolo illustra un esempio esplorativo creato in [Mixed Reality Design Labs,](https://github.com/Microsoft/MRDesignLabs_Unity)un luogo in cui condividiamo le informazioni e i suggerimenti per lo sviluppo di app di realtà mista. Gli articoli e il codice relativi alla progettazione si evolveranno man appena si effettuano nuove individuazioni.

[Lunar Module](https://github.com/Microsoft/MRDesignLabs_Unity_LunarModule) è un'app di esempio open source di Mixed Reality Design Labs di Microsoft. Scopri come estendere i movimenti di base HoloLens con tracciamento a due mani e l'input del controller Xbox, creare oggetti reattivi al mapping della superficie e alla ricerca del piano e implementare semplici sistemi di menu. Tutti i componenti del progetto sono disponibili per l'uso nelle proprie esperienze di app di realtà mista.

## <a name="demo-video"></a>Video demo 
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4IcIP]

Registrato con HoloLens 2 usando Acquisizione realtà mista

## <a name="rethinking-classic-experiences-for-windows-mixed-reality"></a>Ridefinire le esperienze classiche per Windows Mixed Reality

In alto nell'aria, una piccola spedizione del modulo Apollo rileva metodicamente i terreno frastagliati sotto. Il nostro pilota impa urlato è in un'area di destinazione appropriata. La discesa è complicata, ma fortunatamente questo percorso è stato fatto molte volte prima...

![Interfaccia originale dal lander lunare di Atari del 1979](images/640px-atari-lunar-lander.png)<br>
*Interfaccia originale dal lander lunare di Atari del 1979*

[Lunar Lander è](https://en.wikipedia.org/wiki/Lunar_Lander_(1979_video_game)) un classico classico in cui i giocatori tentano di pilotare una lander lunare su una superficie piana di terreno lunare. Chiunque sia nato negli anni '70 ha probabilmente trascorso ore in un'insoddisfatta con gli occhi incollati a questa nave di vettori che si scema dal cielo. Mentre un giocatore si sposta verso un'area di destinazione, il terreno si ridimensiona per rivelare progressivamente più dettagli. Il successo significa attesi entro la soglia sicura di velocità orizzontale e verticale. I punti vengono assegnati per il tempo impiegato per l'destinazione e il carburante rimanente, con un moltiplicatore basato sulle dimensioni dell'area di destinazione.

A parte il gioco, l'era dei giochi ha portato all'innovazione costante degli schemi di controllo. Dalle configurazioni più semplici a 4 modi (come nel [pac-man)](https://en.wikipedia.org/wiki/Pac-Man)agli schemi estremamente specifici e complessi visti alla fine degli anni '90 e '00 (come quelli nei simulatori di simulatori di simulatori e nelle guide). Lo schema di input usato nella macchina lander lunare è interessante per due motivi: limitare l'ergasto e l'affollamento.

![Console console della console per la lander lunare di Atari](images/atariconsole.png)<br>
*Console della console della console per la lander lunare di Atari*

Perché Atari e così tante altre società di giochi hanno deciso di ritroso l'input?

Un bambini che attraversa un'affondo sarà naturalmente incuriosito dalla macchina più recente e più flash. Lander lunare, tuttavia, presenta un nuovo meccanismo di input che esce dalla massa.

Lander lunare usa due pulsanti per ruotare la spedizione a sinistra e a destra e una **leve** insoddibile per controllare la quantità di spazio prodotto dalla spedizione. Questa leve offre agli utenti un certo livello di finezza che una normale levetta non può fornire. Si tratta anche di un componente comune ai moderni pozze di controllo. Atari voleva che lander lunare fosse in grado di coinvolgere l'utente nella sensazione di pilotare un modulo lunare. Questo concetto è noto come **tattili.**

Il tattilità è l'esperienza del feedback sensoriale derivante dall'eseguire azioni ripetitive. In questo caso, l'azione ripetitiva di regolazione della leve e della rotazione della velocità, che i nostri occhi vedono e i nostri occhi udino, aiuta a connettere il giocatore all'atto di attecchire una nave sulla superficie lunare. Questo concetto può essere associato al concetto di "flusso". Dove un utente è pienamente soddisfatto di un'attività che ha la giusta combinazione di sfida e ricompensa o, in parole più semplici, si trova "nella zona".

Probabilmente, il tipo più importante di eterogeneo nella realtà mista è l'eterogeneo spaziale. L'intero punto della realtà mista è quello di insod dire che questi oggetti digitali esistono nel mondo reale. Si stanno sintetizzando ologrammi nell'ambiente circostante, immersi a livello spaziale in interi ambienti ed esperienze. Ciò non significa che non è ancora possibile usare altri tipi di avarizia nelle esperienze, proprio come Atari ha fatto con il tattile della lander lunare.

## <a name="designing-with-immersion"></a>Progettazione con l'ata

In che modo è possibile applicare l'aceto tattile a un elemento volumetrico aggiornato al classico Atari? Prima di affrontare lo schema di input, è necessario risolvere il costrutto di gioco per lo spazio tridimensionale.

![Visualizzazione del mapping della superficie in HoloLens](images/surfacemapping.png)<br>
*Visualizzazione del mapping spaziale in HoloLens*

Sfruttando l'ambiente circostante di un utente, sono disponibili opzioni di terreno infinite per atteggiare il modulo lunare. Per rendere il gioco più simile al titolo originale, un utente potrebbe potenzialmente manipolare e posizionare i pad di destinazione con varie difficoltà nel proprio ambiente.

![Svolse il modulo lunare](images/640px-lm-hero.jpg)<br>
*Svolse il modulo lunare*

Richiedere all'utente di apprendere lo schema di input, controllare la spedizione e avere un piccolo obiettivo su cui attesi è molto da chiedere. Un'esperienza di gioco di successo offre la giusta combinazione di sfida e ricompensa. L'utente può scegliere un livello di difficoltà, con la modalità più semplice che richiede semplicemente all'utente di accedere correttamente a un'area definita dall'utente su una superficie analizzata dal HoloLens. Quando un utente riceve il blocco del gioco, può quindi creare le difficoltà in base alle esigenze.

### <a name="adding-input-for-hand-gestures"></a>Aggiunta di input per i movimenti della mano

HoloLens'input di base ha solo due movimenti: [Air Tap e Bloom.](../../design/gaze-and-commit.md#composite-gestures) Gli utenti non devono ricordare sfumature contestuali o un elenco di movimenti specifici che rendono l'interfaccia della piattaforma versatile e facile da apprendere. Anche se il sistema può esporre solo questi due movimenti, HoloLens quando un dispositivo è in grado di tenere traccia di due mani contemporaneamente. L'ode al lander lunare è un'[app immersiva, il che significa che è possibile estendere il set di base di movimenti per sfruttare due mani e aggiungere le proprie mezzi taattili per la navigazione dei moduli lunari.

Esaminando lo schema di controllo originale, **era necessario risolvere per la rotazione e la rotazione.** L'avvertenza è che la rotazione nel nuovo contesto aggiunge un asse aggiuntivo (tecnicamente due, ma l'asse Y è meno importante per la destinazione). I due movimenti distinti delle spedizioni si prestano naturalmente a essere mappati a ogni mano:

![Toccare e trascinare il movimento per ruotare la lander su tutti e tre gli assi](images/module-handdrag.gif)<br>
*Toccare e trascinare il movimento per ruotare la lander su tutti e tre gli assi*

**Spinta**

La leve sulla macchina originale della versione di gioco mappata a una scala di valori, più elevata è la leve spostata, maggiore è la potenza applicata alla spedizione. Una sfumatura importante da notare è il modo in cui l'utente può prendere la mano dal controllo e mantenere un valore desiderato. È possibile usare in modo efficace il comportamento di tocco e trascinamento per ottenere lo stesso risultato. Il valore iniziale inizia da zero. L'utente tocca e trascina per aumentare il valore. A questo punto possono lasciar andare per gestirlo. Qualsiasi modifica del valore del movimento di tocco e trascinamento sarà il delta rispetto al valore originale.

**Rotazione**

Questo è un po' più complicato. La presenza di pulsanti olografici per "ruotare" il tocco garantisce un'esperienza straordinaria. Non esiste un controllo fisico da sfruttare, quindi il comportamento deve derivare dalla manipolazione di un oggetto che rappresenta il lander o con il lander stesso. È stato illustrato un metodo che usa il tocco e il trascinamento, che consente a un utente di "eseguire in modo efficace il push e il pull" nella direzione desiderata. Ogni volta che un utente tocca e tiene il mouse, il punto nello spazio in cui è stato avviato il movimento diventa l'origine per la rotazione. Il trascinamento dall'origine converte il delta della traslazione della mano (X,Y,Z) e lo applica al delta dei valori di rotazione del lander. O più semplicemente, trascinando < sinistra > destra, verso l'alto < > verso il *basso, <->* indietro negli spazi ruota la spedizione di conseguenza.

Poiché il HoloLens può tenere traccia di due mani, la rotazione può essere assegnata alla mano destra mentre la rotazione è controllata da sinistra. La finezza è il fattore determinante per il successo in questo gioco. *L'aspetto* di queste interazioni è la priorità più alta assoluta. Soprattutto nel contesto dell'accisa tattile. Una spedizione che reagisce troppo rapidamente sarebbe difficile da guidare, mentre un'operazione troppo lenta richiederebbe all'utente di "eseguire il push e il pull" sulla spedizione per un periodo di tempo estremamente lungo.

### <a name="adding-input-for-game-controllers"></a>Aggiunta di input per i controller di gioco

Anche se i movimenti della mano HoloLens forniscono un nuovo metodo di controllo con granularità fine, esiste ancora una certa mancanza di feedback tattile "vero" che si ottiene dai controlli analoghi. La connessione di un controller di gioco Xbox consente di riportare questo senso di fisicità sfruttando al tempo stesso i tasti di controllo per mantenere un controllo granulare.

Esistono diversi modi per applicare lo schema di controllo relativamente semplice al controller Xbox. Poiché si sta cercando di rimanere il più vicino possibile alla configurazione originale, **la** mappa Distoglie il più possibile al pulsante di attivazione. Questi pulsanti sono controlli analoghi, vale a dire che hanno più di semplici stati di on *e off,* rispondono effettivamente al grado di pressione su di essi. In questo modo si ha un costrutto simile **a quello della leve .** A differenza del gioco originale e del movimento della mano, questo controllo taglia la potenza della spedizione quando un utente smette di mettere pressione sul trigger. Offre comunque all'utente lo stesso livello di finezza del gioco originale.

![La levetta sinistra è mappata a Yaw and Roll, la levetta destra è mappata a Pitch and Roll](images/thumbsticksidebyside.gif)<br>
*La levetta sinistra è mappata a yaw e roll; la levetta destra è mappata a pitch and roll*

Le due levette si prestano naturalmente al controllo della rotazione delle spedizioni. Sfortunatamente, esistono tre assi su cui la spedizione può ruotare e due levette che supportano entrambi due assi. Questa mancata corrispondenza indica che una levetta controlla un asse. o c'è sovrapposizione di assi per le levette. La soluzione precedente ha finito per essere "interrotta" perché le levette combinano intrinsecamente i valori X e Y locali. Quest'ultima soluzione ha richiesto alcuni test per individuare gli assi ridondanti più naturali. L'esempio finale usa *yaw* and *roll* (assi Y e X) per la levetta sinistra e *pitch* and *roll* (assi Z e X) per la levetta destra. Questo ha ritenuto il più naturale perché *il lancio sembra* essere abbinato in modo indipendente a *yaw* e *pitch.* Come si può notare, l'uso di entrambe le levette *per il lancio* raddoppia anche il valore di rotazione; È piuttosto divertente avere i cicli Do del lander.

Questa app di esempio illustra in che modo il riconoscimento spaziale e il tattile possono modificare significativamente un'esperienza grazie alle modalità di input estendibili Windows Mixed Reality di Windows Mixed Reality di input estendibile. Mentre il lander lunare potrebbe essere prossimo a 40 anni di età, i concetti esposti con quel poco ottagonale con gli ottagoni vivranno per sempre. Quando si immaginare il futuro, perché non guardare al passato?

## <a name="technical-details"></a>Dettagli tecnici

È possibile trovare script e prefab per l'app di esempio Lunar Module in [Mixed Reality Design Labs GitHub](https://github.com/Microsoft/MRDesignLabs_Unity_LunarModule).

## <a name="about-the-author"></a>Informazioni sull'autore

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Addison Linville" width="60" height="60" src="images/addisonlinville-tile-60px.jpg"></td>
<td style="border-style: none"><b>Addison Linville</b><br>Designer di esperienza utente @Microsoft</td>
</tr>
</table>

## <a name="see-also"></a>Vedere anche

* [Hub di esempi MRTK](/windows/mixed-reality/mrtk-unity/features/example-scenes/example-hub) - [(eseguire il download da Microsoft Store in HoloLens 2)](https://www.microsoft.com/en-us/p/mrtk-examples-hub/9mv8c39l2sj4)
* [Superfici](sampleapp-surfaces.md) - [(eseguire il download da Microsoft Store in HoloLens 2)](https://www.microsoft.com/en-us/p/surfaces/9nvkpv3sk3x0)
* [Tavola periodica degli elementi 2.0](periodic-table-of-the-elements-2.md)
* [Galaxy Explorer 2.0](galaxy-explorer-update.md)
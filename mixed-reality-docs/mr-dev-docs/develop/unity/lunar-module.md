---
title: Modulo lunare
description: Informazioni su come estendere i movimenti di base di HoloLens con il rilevamento a due mani e l'input del controller Xbox, creare oggetti reattivi e implementare sistemi di menu.
author: radicalad
ms.author: adlinv
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, App di esempio, Progettazione, MRTK, Mixed Reality Toolkit, Unity, app di esempio, app di esempio, open source, Microsoft Store, HoloLens, visore per realtà mista, visore di realtà mista windows, visore per realtà virtuale
ms.openlocfilehash: ebac2c5680524b408d6dde8635d2585236fa0b08
ms.sourcegitcommit: 719682f70a75f732b573442fae8987be1acaaf19
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/02/2021
ms.locfileid: "110743509"
---
# <a name="lunar-module"></a>Modulo lunare

>[!NOTE]
>Questo articolo illustra un esempio esplorativo creato in [Mixed Reality Design Labs,](https://github.com/Microsoft/MRDesignLabs_Unity)un luogo in cui vengono illustrate le informazioni e i suggerimenti per lo sviluppo di app di realtà mista. Gli articoli e il codice relativi alla progettazione si evolvono man appena si effettuano nuove individuazioni.

[Lunar Module](https://github.com/Microsoft/MRDesignLabs_Unity_LunarModule) è un'app di esempio open source di Microsoft Mixed Reality Design Labs. Informazioni su come estendere i movimenti di base di HoloLens con il rilevamento a due mani e l'input del controller Xbox, creare oggetti reattivi alla mappatura della superficie e alla ricerca del piano e implementare sistemi di menu semplici. Tutti i componenti del progetto sono disponibili per l'uso nelle proprie esperienze di app di realtà mista.

## <a name="demo-video"></a>Video demo 
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4IcIP]

Registrato con HoloLens 2 usando Acquisizione realtà mista

## <a name="rethinking-classic-experiences-for-windows-mixed-reality"></a>Ridefinire le esperienze classiche per Windows Mixed Reality

In alto nell'atmosfera, una piccola navicella che ricorda il modulo Apollo rileva metodicamente il terreno frastagliato sottostante. Il nostro pilota senza paura ha un'area di destinazione adatta. La discesa è difficile, ma fortunatamente questo viaggio è stato fatto molte volte prima...

![Interfaccia originale del lander lunare di Atari del 1979](images/640px-atari-lunar-lander.png)<br>
*Interfaccia originale del lander lunare di Atari del 1979*

[Lunar Lander](https://en.wikipedia.org/wiki/Lunar_Lander_(1979_video_game)) è un classico della sala giochi in cui i giocatori provano a pilotare un lander lunare in un punto pianeggiante del terreno lunare. Chiunque sia nato negli anni '70 ha probabilmente trascorso ore in una sala giochi con gli occhi incollati a questa naVe vettoriale che precipitava dal cielo. Mentre un giocatore naviga verso un'area di destinazione, il terreno si ridimensiona per rivelare progressivamente più dettagli. Per successo si intende l'atterramento entro la soglia di sicurezza della velocità orizzontale e verticale. I punti vengono assegnati per il tempo dedicato all'destinazione e al carburante rimanente, con un moltiplicatore in base alle dimensioni dell'area di destinazione.

Oltre al gioco di gioco, l'era dei giochi della sala giochi ha portato costante innovazione degli schemi di controllo. Dalle configurazioni più semplici a quattro modi di joystick e pulsante (viste nell'icona [Pac-Man)](https://en.wikipedia.org/wiki/Pac-Man)agli schemi altamente specifici e complessi visti alla fine degli anni '90 e '00 (come quelli nei simulatori di simulatori di palla da campo e nei simulatori di rail). Lo schema di input usato nella macchina Lunar Lander è interessante per due motivi: ridurre l'appeal e l'immersione.

![Console della sala giochi lunari di Atari](images/atariconsole.png)<br>
*Console della sala giochi Lunar Lander di Atari*

Perché Atari e così tante altre società di giochi hanno deciso di ritroso l'input?

Un bimbo che attraversa una sala giochi sarà naturalmente incuriosito dalla macchina più recente e più appariscente. Ma Lunar Lander offre un nuovo meccanismo di input che si è disperso dalla massa.

Lunar Lander usa due pulsanti per ruotare la navicella a sinistra e a destra e una **leve** di affondo per controllare la quantità di spinta che la navicella produce. Questa leve offre agli utenti un certo livello di finezza che un normale rossetto non può fornire. Si tratta anche di un componente comune ai moderni pozzetto per aerei di trasporto aereo. Atari vuole che Lunar Lander indossi l'utente nella sensazione di pilotare un modulo lunare. Questo concetto è noto come **tattile.**

L'immersione tattile è l'esperienza del feedback sensoriale derivante dall'azione ripetitiva. In questo caso, l'azione ripetitiva di regolazione della leve e della rotazione dell'acceleratore, che i nostri occhi vedono e le nostre orecchini udino, aiuta a connettere il giocatore all'atto di atterrare una navicella sulla superficie lunare. Questo concetto può essere associato al concetto psichica di "flusso". Quando un utente è completamente immerso in un'attività che ha la giusta combinazione di sfida e ricompensa, o in parole più semplici, è "nella zona".

Probabilmente, il tipo più importante di immersione nella realtà mista è l'immersione spaziale. L'intero punto della realtà mista è quello di ingannare se stessi nel fatto che questi oggetti digitali esistono nel mondo reale. Stiamo sintetizzando ologrammi nell'ambiente circostante, immersi nello spazio in interi ambienti ed esperienze. Questo non significa che non è ancora possibile usare altri tipi di immersione nelle esperienze, proprio come ha fatto Atari con l'immersione tattile nel Lunar Lander.

## <a name="designing-with-immersion"></a>Progettazione con immersione

Come si può applicare l'immersione tattile a un seguito volumetrico aggiornato al classico Atari? Prima di affrontare lo schema di input, è necessario risolvere il costrutto di gioco per lo spazio tridimensionale.

![Visualizzazione del mapping della superficie in HoloLens](images/surfacemapping.png)<br>
*Visualizzazione del mapping spaziale in HoloLens*

Sfruttando l'ambiente circostante di un utente, sono effettivamente disponibili infinite opzioni di terreno per l'atterramento del modulo lunare. Per rendere il gioco più simile al titolo originale, un utente potrebbe potenzialmente manipolare e posizionare pad di destinazione di varie difficoltà nel proprio ambiente.

![Pilotare il modulo lunare](images/640px-lm-hero.jpg)<br>
*Pilotare il modulo lunare*

Chiedere all'utente di apprendere lo schema di input, controllare la navicella e avere un piccolo obiettivo su cui atterrare è molto da chiedere. Un'esperienza di gioco di successo offre il giusto mix di sfida e ricompensa. L'utente può scegliere un livello di difficoltà, con la modalità più semplice che richiede semplicemente all'utente di atterrare correttamente in un'area definita dall'utente su una superficie analizzata da HoloLens. Una volta che un utente ottiene il blocco del gioco, può quindi alzare la difficoltà in base alle esigenze.

### <a name="adding-input-for-hand-gestures"></a>Aggiunta di input per i movimenti della mano

L'input di base di HoloLens ha solo due movimenti: [Air Tap e Bloom.](../../design/gaze-and-commit.md#composite-gestures) Gli utenti non devono ricordare sfumature contestuali o un elenco di movimenti specifici che rendono l'interfaccia della piattaforma sia versatile che facile da imparare. Anche se il sistema può esporre solo questi due movimenti, HoloLens come dispositivo può tenere traccia di due mani contemporaneamente. L'ode a Lunar Lander è un'[app immersiva, il che significa che è possibile estendere il set di base di movimenti per sfruttare due mani e aggiungere i propri mezzi rettili per la navigazione dei moduli lunari.

Esaminando lo schema di controllo originale, era necessario risolvere il problema **di spinte e rotazione.** L'avvertenza è che la rotazione nel nuovo contesto aggiunge un asse aggiuntivo (tecnicamente due, ma l'asse Y è meno importante per la destinazione). I due movimenti distinti delle navi si prestano naturalmente a essere mappati a ogni mano:

![Toccare e trascinare il movimento per ruotare il lander su tutti e tre gli assi](images/module-handdrag.gif)<br>
*Toccare e trascinare il movimento per ruotare il lander su tutti e tre gli assi*

**Spinta**

La leve sulla macchina della sala giochi originale mappata a una scala di valori, più alta è stata spostata la leve, maggiore è la potenza applicata alla navicella. Una sfumatura importante da notare qui è il modo in cui l'utente può prendere la mano dal controllo e mantenere un valore desiderato. È possibile usare in modo efficace il comportamento di tocco e trascinamento per ottenere lo stesso risultato. Il valore di pulsamento inizia da zero. L'utente tocca e trascina per aumentare il valore. A quel punto potrebbero lasciarlo andare per mantenerlo. Qualsiasi modifica del valore del movimento di tocco e trascinamento sarà il delta rispetto al valore originale.

**Rotazione**

Questo è un po' più difficile. La presenza di pulsanti "ruota" olografici da toccare rende un'esperienza tremenda. Non esiste un controllo fisico da sfruttare, quindi il comportamento deve derivare dalla manipolazione di un oggetto che rappresenta il lander o con il lander stesso. È stato fornito un metodo che usa il tocco e il trascinamento, che consente a un utente di eseguire in modo efficace il push e il pull nella direzione desiderata. Ogni volta che un utente tocca e tiene, il punto nello spazio in cui è stato avviato il movimento diventa l'origine della rotazione. Il trascinamento dall'origine converte il delta della traslazione della mano (X,Y,Z) e lo applica al delta dei valori di rotazione del lander. O più semplicemente, trascinando < sinistra > destra, verso l'alto <-> verso il *basso, <->* indietro negli spazi ruota la naVe di conseguenza.

Poiché HoloLens può tenere traccia di due mani, la rotazione può essere assegnata alla mano destra mentre la spinta è controllata da sinistra. Finesse è il fattore trainante per il successo in questo gioco. *L'aspetto* di queste interazioni è la priorità più alta assoluta. Soprattutto nel contesto dell'immersione tattile. Una navicella che reagisce troppo rapidamente sarebbe difficile da guidare, mentre una di troppo lenta richiederebbe all'utente di "eseguire il push e il pull" sulla navicella per un periodo di tempo estremamente lungo.

### <a name="adding-input-for-game-controllers"></a>Aggiunta di input per i controller di gioco

Mentre i movimenti della mano in HoloLens forniscono un nuovo metodo di controllo granulare, esiste ancora una certa mancanza di feedback tattile "vero" che si ottiene dai controlli analoghi. La connessione di un controller di gioco Xbox consente di riportare questo senso di fisicità sfruttando i bastoni di controllo per mantenere un controllo accurato.

Esistono diversi modi per applicare lo schema di controllo relativamente diretto al controller Xbox. Dal momento che si sta cercando di rimanere il più vicino possibile alla configurazione originale della sala giochi, **La** spinta esegue il mapping migliore al pulsante di attivazione. Questi pulsanti sono controlli analoghi, vale a dire che hanno più di semplici stati di on *e off,* rispondono effettivamente al grado di pressione esercitato su di essi. In questo modo si otturà un costrutto simile a **quello della leve di spinta.** A differenza del gioco originale e del movimento della mano, questo controllo taglia la pressione della naVe quando un utente smette di mettere pressione sul trigger. Offre comunque all'utente lo stesso livello di finezza del gioco originale della sala giochi.

![La levetta sinistra è mappata a Yaw and Roll, la levetta destra viene mappata a Pitch and Roll](images/thumbsticksidebyside.gif)<br>
*La levetta sinistra è mappata a yaw and roll; la levetta destra è mappata a pitch and roll*

Le due leve si prestano naturalmente al controllo della rotazione della navicella. Sfortunatamente, ci sono tre assi su cui la navicella può ruotare e due leve che supportano entrambi due assi. Questa mancata corrispondenza indica che una levetta controlla un asse. o c'è sovrapposizione di assi per le levette. La soluzione precedente ha finito per essere "interrotta" perché le levette combinano intrinsecamente i valori X e Y locali. Quest'ultima soluzione ha richiesto alcuni test per individuare gli assi ridondanti più naturali. L'esempio finale usa *yaw* and *roll* (assi Y e X) per la levetta sinistra e *pitch* and *roll* (assi Z e X) per la levetta destra. Questo ha ritenuto il più naturale perché *il lancio sembra* essere abbinato in modo indipendente a *yaw* e *pitch.* Come si può notare, l'uso di entrambe le levette *per il lancio* raddoppia anche il valore di rotazione; È piuttosto divertente avere i cicli Do del lander.

Questa app di esempio illustra in che modo il riconoscimento spaziale e il tattile possono modificare significativamente un'esperienza grazie alle modalità di input estendibili Windows Mixed Reality di Windows Mixed Reality di input estendibili. Anche se Lander lunare potrebbe essere prossimo a 40 anni di età, i concetti esposti con quel poco ottagonale con gli ottagoni vivranno per sempre. Quando si immaginare il futuro, perché non guardare al passato?

## <a name="technical-details"></a>Dettagli tecnici

È possibile trovare script e prefab per l'app di esempio Lunar Module in [Mixed Reality Design Labs in GitHub.](https://github.com/Microsoft/MRDesignLabs_Unity_LunarModule)

## <a name="about-the-author"></a>Informazioni sull'autore

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Addison Linville" width="60" height="60" src="images/addisonlinville-tile-60px.jpg"></td>
<td style="border-style: none"><b>Addison Linville</b><br>Designer di esperienza utente @Microsoft</td>
</tr>
</table>

## <a name="see-also"></a>Vedi anche

* [Hub di esempi MRTK](/windows/mixed-reality/mrtk-unity/features/example-scenes/example-hub) - [(eseguire il download da Microsoft Store in HoloLens 2)](https://www.microsoft.com/en-us/p/mrtk-examples-hub/9mv8c39l2sj4)
* [Superfici](sampleapp-surfaces.md) - [(eseguire il download da Microsoft Store in HoloLens 2)](https://www.microsoft.com/en-us/p/surfaces/9nvkpv3sk3x0)
* [Tavola periodica degli elementi 2.0](https://medium.com/@dongyoonpark/bringing-the-periodic-table-of-the-elements-app-to-hololens-2-with-mrtk-v2-a6e3d8362158)
* [Galaxy Explorer 2.0](galaxy-explorer-update.md)
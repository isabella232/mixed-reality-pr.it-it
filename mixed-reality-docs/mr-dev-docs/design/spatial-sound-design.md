---
title: Usare l'audio spaziale nelle applicazioni di realtà mista
description: L'audio spaziale è uno strumento potente per la progettazione di accessibilità, accessibilità e esperienza utente nelle applicazioni di realtà mista.
author: kegodin
ms.author: v-hferrone
ms.date: 11/02/2019
ms.topic: article
keywords: Windows Mixed Reality, audio spaziale, progettazione, stile, visore VR di realtà mista, visore VR di realtà mista windows, visore VR di realtà virtuale, HoloLens, MRTK, Toolkit realtà mista, movimenti, interazioni, attenuazione
ms.openlocfilehash: 687811f23e11cadf6e75129098c9feb0393009f819eb961cf2f55a3208cc5f96
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115208961"
---
# <a name="how-to-use-sound-in-mixed-reality-applications"></a>Come usare i suoni nelle applicazioni di realtà mista

È possibile usare il suono per informare e rafforzare il modello psichiico dell'utente dello stato dell'applicazione. Usare la spazializzazione, quando appropriato, per inserire suoni nel mondo della realtà mista. Quando si connette il revisore e l'oggetto visivo in questo modo, si approfondirà la natura intuitiva delle interazioni e si aumenterà la fiducia degli utenti.
<br><br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/aB3TDjYklmo" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

## <a name="when-to-add-sounds"></a>Quando aggiungere suoni

Le applicazioni di realtà mista hanno spesso una maggiore necessità di audio rispetto alle app 2D, a causa della mancanza di un'interfaccia tattile. Aggiungere suoni quando informano l'utente o per rinforzare le interazioni.

### <a name="inform-and-reinforce"></a>Informare e rafforzare

* Per gli eventi che non vengono avviati dall'utente, ad esempio le notifiche, usare il suono per informare l'utente che si è verificata una modifica.
* Le interazioni possono avere diverse fasi. Usare il suono per rafforzare le transizioni di fase.

Vedere gli esempi seguenti di interazioni, eventi e caratteristiche sonore suggerite.

### <a name="exercise-restraint"></a>Esercizio di base

Gli utenti non hanno una capacità illimitata per le informazioni audio.
* Ogni suono deve comunicare informazioni specifiche e preziose.
* Quando l'app riproduce un suono per informare l'utente, ridurre temporaneamente il volume di altri suoni.
* Per i suoni al passaggio del mouse sui pulsanti (vedere le informazioni seguenti), aggiungere un ritardo di tempo per impedire l'attivazione di un suono eccessivo.

### <a name="dont-rely-solely-on-sounds"></a>Non fare affidamento esclusivamente sui suoni

I suoni usati bene sono utili per gli utenti. Assicurarsi tuttavia che l'applicazione sia utilizzabile anche con il suono disattivato.
* Gli utenti possono avere problemi di udito.
* L'applicazione può essere usata in un ambiente ad alta voce.
* Gli utenti possono avere problemi di privacy o altri motivi per disabilitare l'audio del dispositivo.

## <a name="how-to-sonify-interactions"></a>Come figlioificare le interazioni

I tipi di interazione nella realtà mista includono movimento, manipolazione diretta e voce. Usare le caratteristiche suggerite seguenti per selezionare o progettare suoni per queste interazioni.

### <a name="gesture-interactions"></a>Interazioni con movimenti

Nella realtà mista gli utenti possono interagire con i pulsanti usando il mouse. Le azioni del pulsante si verificano in genere quando l'utente rilascia anziché premere il pulsante per offrire all'utente la possibilità di annullare l'interazione. Usare i suoni per rafforzare queste fasi. Per assistere gli utenti nella scelta di pulsanti distanti, è consigliabile usare anche un suono al passaggio del puntatore.
* La pressione di un pulsante deve essere un breve "clic" tattile.<br/>Esempio: [MRTK_ButtonPress.wav](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/main/Assets/MRTK/SDK/StandardAssets/Audio/MRTK_ButtonPress.wav)
* I suoni button-"unpress" devono avere un aspetto tattile simile. Un tono più alto rispetto al suono della pressione consolida il senso di completamento.<br/>Esempio: [MRTK_ButtonUnpress.wav](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/main/Assets/MRTK/SDK/StandardAssets/Audio/MRTK_ButtonUnpress.wav)
* Per i suoni al passaggio del mouse, prendere in considerazione l'uso di un suono sottile e non strano, ad esempio un thud o un urto a bassa frequenza.

### <a name="direct-manipulation"></a>Manipolazione diretta

In HoloLens 2, il tracciamento delle mani articolato supporta la manipolazione diretta degli elementi dell'interfaccia utente. I suoni sono importanti quando non sono presenti altri commenti e suggerimenti fisici.

Un *suono di pressione* del pulsante è importante perché l'utente non ottiene altre indicazioni quando raggiunge la parte inferiore del tratto del tasto. Gli indicatori sonori del viaggio chiave possono essere piccoli, piccoli e occluded. Come per le interazioni con movimenti, le pressione dei pulsanti dovrebbero ottenere un suono breve e tattile come un clic. Le depressione devono avere un suono di clic simile, ma con tono in rilievo.
* Esempio: [MRTK_ButtonPress.wav](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/main/Assets/MRTK/SDK/StandardAssets/Audio/MRTK_ButtonPress.wav)
* Esempio: [MRTK_ButtonUnpress.wav](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/main/Assets/MRTK/SDK/StandardAssets/Audio/MRTK_ButtonUnpress.wav)

È difficile confermare visivamente un'azione di cattura o rilascio. La mano dell'utente sarà spesso in linea con qualsiasi effetto visivo e gli oggetti con corpo rigido non hanno un'analogia visiva reale di "afferramento". I suoni possono comunicare in modo efficace interazioni di cattura e rilascio.
* Le azioni di cattura devono avere un suono tattile breve e leggermente muffled che chiede l'idea di chiudere le dita intorno a un oggetto. A volte è presente anche un suono "whoosh" che porta al suono di afferramento per comunicare il movimento della mano.<br/>Esempio: [MRTK_Move_Start.wav](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/main/Assets/MRTK/SDK/StandardAssets/Audio/MRTK_Move_Start.wav)
* Le azioni di rilascio dovrebbero ottenere un suono simile breve e tattile. È in genere più bassa del suono di afferramento e in ordine inverso, con un impatto e quindi un "whoosh" per comunicare che l'oggetto si sta sistemando sul posto.<br/>Esempio: [MRTK_Move_End.wav](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/main/Assets/MRTK/SDK/StandardAssets/Audio/MRTK_Move_End.wav)

*Un'interazione* di disegno dovrebbe ottenere un suono persistente a ciclo continuo con il volume determinato dal movimento della mano dell'utente. Dovrebbe essere invisibile quando la mano dell'utente è ancora e più alta quando la mano si sposta rapidamente.

### <a name="voice-interactions"></a>Interazioni vocali

Le interazioni vocali spesso hanno piccoli elementi visivi. Usare i suoni per rafforzare le fasi di interazione. È possibile usare suoni più tonali per distinguerli dai movimenti e dai suoni di manipolazione diretta.

* Usare un tono positivo per le conferme dei *comandi vocali*. I toni della crescita e i principali intervalli di tempo sono efficaci.
* Usare un tono più breve e meno positivo per gli errori dei *comandi vocali.* Evitare suoni negativi. Usare invece un suono più percussivo e neutro per comunicare che l'applicazione sta passando dall'interazione.
* Se l'applicazione ha una parola di attivazione, usare un tono breve e a tono quando il dispositivo inizia ad *ascoltare*. Usare un suono a ciclo sottile mentre l'applicazione *è in* ascolto.

### <a name="notifications"></a>Notifiche

Le notifiche segnalano le modifiche dello stato dell'applicazione e altri eventi che l'utente non ha avviato. Le modifiche dello stato possono includere completamenti dei processi, messaggi e chiamate telefoniche.

Nella realtà mista, gli oggetti a volte si spostano fuori dal campo di visualizzazione dell'utente. Associa oggetti *animati in movimento* a un suono spazializzato che dipende dal tipo di oggetto e dalla velocità del movimento.
* Consente di riprodurre un suono spazializzato alla fine di un'animazione per informare l'utente della nuova posizione dell'oggetto.
* Per i movimenti graduali, un suono "whoosh" durante il movimento consente all'utente di tenere traccia dell'oggetto.

*I suoni delle* notifiche dei messaggi possono essere uditi ripetutamente, talvolta in rapida successione. È importante che non si distinguono o non siano solidi. I suoni tonali positivi di media gamma sono efficaci.

* I suoni delle chiamate in ingresso devono avere qualità simili a quelle di una ringtone del telefono cellulare. Questi suoni riproduceno a ciclo continuo frasi che vengono riprodotte fino a quando l'utente non risponde alla chiamata.
* La connessione e la disconnessione della comunicazione vocale devono avere un suono tonale breve. Il suono della connessione deve essere un tono positivo per indicare una connessione riuscita. Il suono di disconnessione deve essere un suono neutro per indicare il completamento della chiamata.

## <a name="handle-spatialization"></a>Gestire la spazializzazione

La spazializzazione usa altoparlanti o cuffi stereo per inserire suoni nel mondo della realtà mista.

### <a name="which-sounds-to-spatialize"></a>Quali suoni spazializzare

Un suono deve essere spazializzato quando è associato a un evento con una posizione spaziale. Sono inclusi l'interfaccia utente, le voci di intelligenza artificiale e gli indicatori visivi.

Spazializzare *gli elementi dell'interfaccia* utente per ingombrare lo "spazio" acustico dell'utente limitando il numero di suoni stereo che ascoltano. Le interazioni di manipolazione, ad esempio il tocco, l'afferramento e il rilascio, sono più naturali quando il feedback audio è spazializzato. Si considerino le informazioni seguenti sull'attenuazione della distanza per questi elementi.

Spazializzare *gli indicatori visivi* e le voci di *intelligenza* artificiale incorporate per informare in modo intuitivo gli utenti quando questi elementi sono esterni al campo visivo.
    
Al contrario, evitare la spazializzazione *per voci di intelligenza* artificiale senza viso e altri elementi che non dispongono di una posizione spaziale ben definita. La spazializzazione senza un elemento visivo correlato può distrarre gli utenti a pensare che c'è un elemento visivo che non possono trovare.

La spazializzazione ha un costo della CPU. Molte applicazioni hanno al massimo due suoni riprodotti contemporaneamente. Il costo della spazializzazione in questo caso è probabilmente trascurabile. È possibile usare il monitoraggio della frequenza fotogrammi MRTK per valutare l'impatto dell'aggiunta della spazializzazione.

### <a name="when-and-how-to-apply-distance-based-attenuation"></a>Quando e come applicare l'attenuazione basata sulla distanza

Nel mondo fisico, i suoni più lontani sono più silenziosi. Il motore audio può modellare questa attenuazione in base alla distanza di origine. Usare l'attenuazione basata sulla distanza quando comunica informazioni pertinenti.

Le distanze degli *indicatori visivi,* *degli ologrammi* animati e di altri suoni informativi sono rilevanti per l'utente. Usare l'attenuazione basata sulla distanza per fornire suggerimenti in modo intuitivo.

Regolare la curva di attenuazione per ogni origine in base alle dimensioni degli spazi del mondo di realtà mista. La curva predefinita del motore audio è spesso destinata a spazi di grandi dimensioni (fino a mezzo chilometro).

I suoni che *rinforzano le fasi progressive delle azioni dei pulsanti* e di altre interazioni non devono essere applicati all'attenuazione. Gli effetti di rinforzo di questi suoni sono più importanti della comunicazione della distanza dal pulsante. Le variazioni possono distrarre, in particolare con le tastiere, quando molti clic sui pulsanti possono essere uditi in successione.

### <a name="which-spatialization-technology-to-use"></a>Tecnologia di spazializzazione da usare

Con le cuffia o gli altoparlanti HoloLens, usare tecnologie di spazializzazione basate sulla funzione di trasferimento della testa (HRTF). Queste tecnologie modellano la propagazione del suono intorno alla testa nel mondo fisico. Anche quando una sorgente sonora si trova sul lato più lontano della testa, il suono si propaga all'orecchino lontano con qualche attenuazione e ritardo. La panoramica del parlante si basa solo sull'attenuazione e applica l'attenuazione totale nell'orecchio sinistro quando i suoni sono sul lato destro e al contrario. Questa tecnica può essere scomoda per i listener "ascolto normale" e inaccessibile per gli ascoltatori che hanno problemi udibili in un solo udito.

## <a name="next-steps"></a>Passaggi successivi

* [Usare il suono spaziale in Unity](../develop/unity/spatial-sound-in-unity.md)
* [Case study di Roboraid](case-study-using-spatial-sound-in-roboraid.md)
* [Case study di HoloTour](case-study-spatial-sound-design-for-holotour.md)

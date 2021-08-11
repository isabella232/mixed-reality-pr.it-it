---
title: Comfort
description: Nella visione naturale, il sistema visivo umano si basa su più fonti di informazioni, o "indizi", per interpretare le forme 3D e la posizione relativa degli oggetti.
author: erickjpaul
ms.author: erpau
ms.date: 06/25/2020
ms.topic: article
ms.localizationpriority: high
keywords: Realtà mista, progettazione, comodità, HoloLens 2, HoloLens (1a generazione), visore VR realtà mista, visore VR di windows mixed reality, visore per realtà virtuale, HoloLens, MRTK, Mixed Reality Toolkit, locomozione
ms.openlocfilehash: 87cf45628a530da65d9feb29556afb7c4a8ee1d3f13385cbf521d2621ac0c2ae
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115226433"
---
# <a name="comfort"></a>Comfort

Nella visione naturale, il sistema visivo umano si basa su più fonti di informazioni, o "indizi", per interpretare le forme 3D e le posizioni relative degli oggetti. Alcuni indizi si basano solo su un solo occhio (indizio monoculare), tra cui:

* [Prospettiva lineare](https://en.wikipedia.org/wiki/Perspective_(graphical))
* [Dimensioni note](https://en.wikipedia.org/wiki/Size#Perception_of_size)
* Occlusione
* [Sfocatura della profondità di campo](https://en.wikipedia.org/wiki/Depth_of_field)
* [Accomodazione](https://en.wikipedia.org/wiki/Accommodation_(eye)) 

Altri indizi si basano su entrambi gli occhi (indizi binoculari) e includono:

* [Convergenza](https://en.wikipedia.org/wiki/Vergence): in pratica le rotazioni relative degli occhi necessarie per guardare un oggetto
* [Disparità binoculare](https://en.wikipedia.org/wiki/Stereopsis): il modello delle differenze tra le proiezioni della scena sul retro dei due occhi 

Per garantire il massimo comfort per i caschi con visore, è importante creare e presentare contenuti in modo da simulare il funzionamento di questi indizi nel mondo naturale. Dal punto di vista fisico, è anche importante progettare contenuto che non richieda movimenti faticosi del collo o delle braccia. In questo articolo esamineremo gli aspetti principali da tenere in considerazione per raggiungere questi obiettivi.

## <a name="vergence-accommodation-conflict"></a>Conflitto tra convergenza e accomodazione

Per visualizzare chiaramente un oggetto, gli utenti devono [accomodare](https://en.wikipedia.org/wiki/Accommodation_%28eye%29), ovvero regolare, la messa a fuoco oculare in base alla distanza dell'oggetto. Allo stesso tempo, la rotazione di entrambi gli occhi deve [convergere](https://en.wikipedia.org/wiki/Convergence_(eye)) in base alla distanza dell'oggetto per evitare la visione di immagini doppie. Nella visione naturale, convergenza e accomodazione sono collegate. Quando si guarda qualcosa da vicino, ad esempio una mosca vicino al naso, gli occhi si incrociano e si accomodano in base a un punto vicino. Viceversa, se si guarda qualcosa all'infinito ottico (che corrisponde circa ad almeno sei metri di distanza nella visione naturale), le linee visive degli occhi diventano parallele e il cristallino negli occhi si accomoda all'infinito. 

Nella maggior parte dei caschi con visore gli occhi degli utenti si accomodano sempre alla distanza focale del visore per ottenere un'immagine nitida, ma convergono in base alla distanza dell'oggetto di interesse per ottenere una singola immagine. Quando l'accomodazione e la convergenza avvengono a distanze diverse, il collegamento naturale tra i due indizi viene interrotto causando fastidio o affaticamento visivo.

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/-606oZKLa_s" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

### <a name="guidance-for-holographic-devices"></a>Indicazioni per i dispositivi olografici

I display HoloLens sono fissati a una distanza ottica di circa 2 m dall'utente. Gli utenti devono sempre accomodare la visione a circa 2 m per mantenere un'immagine chiara nel dispositivo. Gli sviluppatori di app possono guidare la convergenza degli occhi degli utenti posizionando contenuto e ologrammi a varie profondità. Il disagio provocato dal conflitto tra convergenza e accomodazione può essere evitato o ridotto al minimo mantenendo il contenuto su cui gli utenti convergono lo sguardo il più vicino possibile a 2 m. Ad esempio, in una scena con molta profondità, è opportuno posizionare le aree di interesse a una distanza di circa 2 m dall'utente, quando possibile. Se non è possibile mantenere il contenuto a questa distanza, il disagio provocato dal conflitto tra convergenza e accomodazione è significativo quando lo sguardo dell'utente passa da una distanza all'altra. In altre parole, è molto più confortevole guardare un ologramma che rimane fisso a 50 cm di distanza rispetto a un ologramma distante 50 cm che si avvicina e si allontana gradualmente.

![Distanza ottimale per il posizionamento degli ologrammi rispetto allo sguardo dell'utente.](images/distanceguiderendering-950px.png)<br>
*Distanza ottimale per il posizionamento degli ologrammi rispetto allo sguardo dell'utente*

### <a name="best-practices-for-hololens-1st-gen-and-hololens-2"></a>Procedure consigliate per HoloLens (prima generazione) e HoloLens 2

Per il massimo comfort, **la zona ottimale per il posizionamento degli ologrammi è compresa tra 1,25 e 5 m**. In ogni caso, i progettisti devono cercare di strutturare le scene di contenuto per incoraggiare gli utenti a interagire ad almeno 1 m di distanza dal contenuto, ad esempio regolando i [parametri relativi alle dimensioni del contenuto e al posizionamento predefinito](gaze-and-commit.md). 

Anche se talvolta il contenuto deve essere visualizzato a una distanza inferiore a 1 m, è consigliabile evitare di presentare ologrammi a meno di 40 cm di distanza. È opportuno quindi **applicare un effetto di dissolvenza del contenuto a 40 cm e posizionare un piano di taglio del rendering a 30 cm** per evitare gli oggetti più vicini.

È più probabile che causino disagio oggetti che si muovono in profondità rispetto a oggetti fissi a causa del conflitto tra convergenza e accomodazione. Analogamente, costringere gli utenti ad alternare rapidamente la messa a fuoco da vicino e quella da lontano, ad esempio a causa di un ologramma popup che richiede l'interazione diretta, può causare disagio e affaticamento visivi. **È quindi necessario prestare particolare attenzione e ridurre la frequenza con cui gli utenti devono visualizzare contenuto che si muove in profondità o cambiare rapidamente la messa a fuoco tra ologrammi vicini e lontani**. 

### <a name="other-considerations-for-hololens-2-and-near-interaction-distances"></a>Considerazioni aggiuntive per HoloLens 2 e le distanze di interazione da vicino

Quando si progetta contenuto per l'interazione diretta (da vicino) in HoloLens 2 o **in qualsiasi applicazione in cui il contenuto debba essere posizionato a una distanza inferiore a 1 m, è necessario prestare particolare attenzione ad assicurare il comfort dell'utente**. La probabilità di disagio a causa del conflitto tra convergenza e accomodazione aumenta in modo esponenziale man mano che si riduce la distanza di visualizzazione. Inoltre, gli utenti possono riscontrare maggiori effetti di sfocatura quando visualizzano contenuto a distanze di interazione da vicino. È consigliabile quindi testare il contenuto sottoposto a rendering sia entro la zona di posizionamento ottimale dell'ologramma sia più vicino (meno di 1 m di distanza fino al piano di taglio) per garantirne la nitidezza e la facilità di visualizzazione. 

**È consigliabile quindi definire un "budget di profondità" per le app in base al periodo di tempo in cui si prevede che un utente visualizzi contenuto che si trova vicino (a meno di 1 m) e che si muove in profondità**. Un esempio consiste nell'evitare di costringere l'utente a rimanere in situazioni di questo tipo per oltre un quarto del tempo. Se questo budget viene superato, è opportuno eseguire con attenzione una serie di test utente per assicurare un'esperienza confortevole costante. 

In generale, è consigliabile anche eseguire un attento test per garantire che i requisiti di interazione (ad esempio la velocità di spostamento, la raggiungibilità e così via) a distanze da vicino risultino confortevoli per gli utenti. 

### <a name="guidance-for-immersive-devices"></a>Indicazioni per i dispositivi di tipo immersive

Per i dispositivi di tipo immersive sono comunque valide le linee guida e le procedure consigliate per HoloLens, ma i valori specifici per la zona di comfort variano a seconda della distanza focale rispetto al display. In generale, le distanze focali rispetto a questi display sono comprese tra 1,25 e 2,5 m. In caso di dubbio, è opportuno evitare di eseguire il rendering di oggetti di interesse troppo vicino agli utenti e provare invece a mantenere la maggior parte del contenuto ad almeno 1 m di distanza.

## <a name="interpupillary-distance-and-vertical-offset"></a>Distanza interpupillare e offset verticale

Quando viene visualizzato contenuto digitale sui caschi con visore, la posizione degli occhi dell'utente rispetto alla posizione di visualizzazione del contenuto digitale ha un'importanza critica. In particolare, sia la distanza interpupillare ([IPD](https://en.wikipedia.org/wiki/Pupillary_distance)) sia l'offset verticale (VO) sono importanti per una visualizzazione confortevole di contenuto digitale su caschi di questo tipo. 

Il valore di IPD si riferisce alla distanza tra le pupille, ovvero i punti centrali degli occhi di un individuo. Il valore di VO si riferisce invece al possibile offset verticale del contenuto digitale visualizzato da ogni occhio rispetto all'asse orizzontale degli occhi dell'utente (che NON corrisponde all'offset orizzontale, o disparità binoculare). La corrispondenza errata di almeno uno di questi fattori può peggiorare gli effetti del disagio provato dall'utente a causa del conflitto tra convergenza e accomodazione, ma può causare disturbo anche quando questo conflitto è ridotto al minimo (ad esempio nel caso di contenuto visualizzato alla distanza focale di 2 m di HoloLens). 

### <a name="guidance-for-holographic-devices"></a>Indicazioni per i dispositivi olografici

#### <a name="hololens-1st-gen"></a>HoloLens (prima generazione)

Per HoloLens (prima generazione), il valore di IPD viene stimato e impostato durante la [calibrazione](/hololens/hololens-calibration) del dispositivo. Per i nuovi utenti di un dispositivo già configurato, è necessario eseguire la calibrazione o impostare il valore di IPD manualmente. Il valore di VO dipende completamente dal modo in cui viene indossato il dispositivo. In particolare, per ridurre al minimo il valore di VO, il dispositivo deve essere posizionato sulla testa dell'utente in modo tale che i display si trovino allo stesso livello dell'asse degli occhi. 

#### <a name="hololens-2"></a>HoloLens 2

Per HoloLens 2, il valore di IPD viene stimato e impostato durante la [calibrazione](/hololens/hololens-calibration) del dispositivo rispetto agli occhi. Per i nuovi utenti di un dispositivo già configurato, è necessario eseguire la calibrazione per assicurarsi che il valore di IPD sia impostato correttamente. In HoloLens 2 il valore di VO viene calcolato automaticamente. 

### <a name="guidance-for-immersive-devices"></a>Indicazioni per i dispositivi di tipo immersive

I caschi con visore di tipo immersive di Windows Mixed Reality non prevedono la calibrazione automatica per i valori di IPD o VO. Il valore della distanza interpupillare può essere impostato manualmente nel software (nelle impostazioni del Portale realtà mista vedere la sezione relativa alla [calibrazione](/hololens/hololens-calibration)). In alternativa, alcuni caschi con visore sono dotati di un dispositivo di scorrimento meccanico che consente all'utente di adattare la spaziatura delle lenti a una posizione appropriata, che corrisponda approssimativamente alla distanza interpupillare. 

## <a name="rendering-rates"></a>Velocità di rendering

Le app di realtà mista sono veramente straordinarie perché gli utenti possono muoversi liberamente nel mondo e interagire con contenuto virtuale come se fossero oggetti reali. Per mantenere questa impressione, è fondamentale eseguire il rendering degli ologrammi in modo che risultino stabili nel mondo e si muovano senza interruzione di continuità. Il rendering ad [almeno 60 fotogrammi al secondo (FPS)](../develop/platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md) consente di raggiungere questo obiettivo. Esistono alcuni dispositivi per la realtà mista che supportano il rendering a una frequenza dei fotogrammi superiore a 60 fps e per questi dispositivi è fortemente consigliabile eseguire il rendering a una frequenza più elevata per offrire agli utenti un'esperienza ottimale.

**Approfondimenti**

Per disegnare gli ologrammi in modo che appaiano [stabili nel mondo reale o virtuale](../develop/platform-capabilities-and-apis/hologram-stability.md), le app devono eseguire il rendering delle immagini dalla posizione dell'utente. Poiché il rendering delle immagini richiede tempo, HoloLens e altri dispositivi di Windows Mixed Reality eseguono una stima della posizione in cui si troverà la testa di un utente quando le immagini verranno visualizzate nei display. Questo algoritmo di stima è un'approssimazione. Gli algoritmi e l'hardware di Windows Mixed Reality consentono di regolare l'immagine sottoposta a rendering in modo da tenere conto della discrepanza tra la posizione stimata della testa e quella effettiva. Questo processo ha l'effetto di mostrare l'immagine visualizzata dall'utente come se sottoposta a rendering dalla posizione corretta e gli ologrammi appaiono stabili. Gli aggiornamenti funzionano meglio per le piccole variazioni della posizione della testa e non possono tenere completamente conto di alcune differenze delle immagini sottoposte a rendering, come quelle causate dalla parallasse di movimento.

**Con il rendering a una frequenza dei fotogrammi minima di 60 FPS, due aspetti consentono di rendere stabili gli ologrammi:**
1. Riduzione dell'effetto di tremolio, caratterizzato da immagini doppie o con movimento non uniforme. Un movimento dell'ologramma più veloce e velocità di rendering inferiori determinano un effetto di tremolio più pronunciato. Pertanto, una frequenza dei fotogrammi di 60 FPS (o la massima velocità di rendering del dispositivo) consentirà di evitare questo effetto di tremolio.
2. Riduzione della latenza complessiva. In un motore con un thread di gioco e un thread di rendering eseguiti contemporaneamente, l'esecuzione a 30 fps può causare un aumento della latenza di 33,3 ms. La riduzione della latenza consente di ridurre l'errore di stima e aumentare la stabilità degli ologrammi.

**Analisi delle prestazioni**

Sono disponibili diversi strumenti per sottoporre a benchmark la frequenza dei fotogrammi dell'applicazione, ad esempio:
* GPUView
* Debugger grafica di Visual Studio
* Profiler integrati nei motori 3D come Frame Debugger in Unity

## <a name="self-motion-and-user-locomotion"></a>Movimento autonomo e locomozione dell'utente

L'unica limitazione è rappresentata dalle dimensioni dello spazio fisico. Se vuoi consentire agli utenti di spostarsi più lontano nell'ambiente virtuale rispetto a quanto è possibile nella stanza reale, devi implementare una forma di movimento puramente virtuale. Tuttavia, un movimento virtuale sostenuto che non corrisponde al movimento fisico reale dell'utente può spesso provocare una sensazione di mal d'auto. Questo effetto è dovuto agli *indizi visivi* per il movimento autonomo provenienti dal *mondo virtuale* che sono in conflitto con gli [indizi dell'apparato vestibolare](https://en.wikipedia.org/wiki/Vestibular_system) per il movimento autonomo provenienti dal *mondo reale*.

Per fortuna, puoi evitare questo problema seguendo alcuni suggerimenti per l'implementazione della locomozione dell'utente:
* Fare sempre in modo che l'utente abbia il controllo dei movimenti: un movimento autonomo imprevisto può risultare particolarmente problematico.
* Gli uomini sono molto sensibili alla direzione della forza di gravità. Pertanto, evita di usare in particolare movimenti verticali non avviati dall'utente.

### <a name="guidance-for-holographic-devices"></a>Indicazioni per i dispositivi olografici

Un metodo per consentire all'utente di spostarsi in un'altra posizione in un ambiente virtuale di grandi dimensioni consiste nel dare l'impressione di stare spostando un piccolo oggetto nella scena. Questo effetto può essere ottenuto nel modo seguente:
   1. Fornisci un'interfaccia in cui l'utente può selezionare un punto nell'ambiente virtuale in cui vuole spostarsi.
   2. Al momento della selezione, compatta il rendering della scena su un'area circolare intorno al punto desiderato.
   3. Mantenendo il punto selezionato, consenti all'utente di spostare l'area circolare come se fosse un oggetto di piccole dimensioni. L'utente potrà quindi spostare la selezione vicino ai piedi.
   4. Al momento della deselezione, riprendi il rendering dell'intera scena.

### <a name="guidance-for-immersive-devices"></a>Indicazioni per i dispositivi di tipo immersive

L'approccio precedente indicato per un dispositivo olografico non funziona altrettanto bene in un dispositivo di tipo immersive perché richiede che l'app esegua il rendering di una grande area nera vuota o di un altro ambiente predefinito mentre viene spostata l'area circolare. Questa modalità di rendering ha l'effetto di disturbare il senso di immersione del dispositivo. Una soluzione per la locomozione dell'utente in un visore VR immersive consiste nell'adottare un approccio di tipo "blink". Questa implementazione consente all'utente di controllare il proprio movimento e offre una breve impressione di spostamento, ma così breve che l'utente si sentirà meno disorientato dal movimento autonomo puramente virtuale:
   1. Fornisci un'interfaccia in cui l'utente può selezionare un punto nell'ambiente virtuale in cui vuole spostarsi.
   2. Al momento della selezione, inizia un movimento simulato molto rapido (100 m/s) verso tale posizione, mentre si dissolve rapidamente il rendering.
   3. Inverti la dissolvenza del rendering dopo aver terminato la traslazione.

## <a name="heads-up-displays"></a>Visori a sovrimpressione

Nei videogiochi in cui si spara in prima persona i visori a sovrimpressione (HUD, Head-Up Display) presentano costantemente informazioni quali lo stato dei giocatori, piccole mappe e le scorte disponibili, direttamente sullo schermo. Questi visori sono utili per consentire al giocatore di rimanere informato senza alcuna intrusione nell'esperienza di gioco. Nelle esperienze di realtà mista, i visori a sovrimpressione possono causare notevole fastidio e devono essere adattati al contesto più immersivo. In particolare, i visori a sovrimpressione bloccati rigidamente all'orientamento della testa dell'utente possono causare disagio. Se un'app richiede un visore di questo tipo, è preferibile bloccarlo al *corpo* anziché alla testa. Questo approccio può essere implementato come un set di visualizzazioni che si spostano immediatamente con l'utente, ma non vengono ruotate insieme alla testa finché non viene raggiunta una soglia di rotazione. Una volta eseguita la rotazione, il visore può essere riorientato in modo da presentare le informazioni nel campo di visione dell'utente. Evitare l'implementazione di una rotazione e di uno spostamento 1:1 per un visore a sovrimpressione rispetto ai movimenti della testa dell'utente.

## <a name="text-legibility"></a>Leggibilità del testo

La leggibilità ottimale del testo può aiutare a ridurre l'affaticamento oculare e a mantenere una posizione confortevole, soprattutto in applicazioni o scenari che richiedono la lettura quando si usa un casco con visore. La leggibilità del testo dipende da diversi fattori, tra cui:
* Proprietà del display, come la densità in pixel, la luminosità e il contrasto. 
* Proprietà dell'obiettivo, come l'aberrazione cromatica
* Proprietà del testo e del carattere, ad esempio lo spessore, la spaziatura, la presenza di grazie e il colore dello sfondo e del carattere.  

In generale, consigliamo di testare le applicazioni specifiche per determinare la leggibilità del testo e aumentare il più possibile le dimensioni dei caratteri per assicurare un'esperienza confortevole. Informazioni più dettagliate per i dispositivi olografici e immersivi sono disponibili nelle pagine dedicate a [tipografia](typography.md) e [testo in Unity](../develop/unity/text-in-unity.md).

## <a name="holographic-frame-considerations"></a>Considerazioni sul frame olografico

Per le esperienze in realtà mista con oggetti di grandi dimensioni o con molti oggetti, è fondamentale valutare quanti movimenti della testa e del collo sono necessari per interagire con il contenuto. Le esperienze possono essere suddivise in tre categorie in termini di movimento della testa: 
* **Orizzontale** (laterale)
* **Verticale** (su o giù)
* **Immersiva** (sia orizzontale sia verticale)
 
Quando possibile, limitare la maggior parte delle interazioni alle categorie orizzontale o verticale, preferibilmente concentrando la maggior parte delle esperienze al centro del frame olografico mentre la testa dell'utente si trova in posizione neutra. Evitare le interazioni che costringono l'utente a spostare costantemente la vista con la testa in una posizione innaturale, ad esempio guardando sempre in alto per accedere all'interazione con il menu principale.

![L'area ottimale per il contenuto è da 0 a 35 gradi sotto l'orizzonte](images/optimal-field-of-view-2.png)<br>
*L'area ottimale per il contenuto è compresa tra 0 e 35 gradi sotto l'orizzonte*

Lo spostamento della testa in orizzontale è più adatto alle interazioni frequenti, mentre i movimenti verticali devono essere riservati agli eventi non comuni. Ad esempio, un'esperienza che coinvolge una lunga sequenza temporale orizzontale deve limitare lo spostamento verticale della testa per le interazioni, ad esempio guardare un menu in basso.

È preferibile incoraggiare lo spostamento completo del corpo, anziché semplicemente il movimento della testa, posizionando gli oggetti attorno allo spazio dell'utente. Per le esperienze con oggetti in movimento o di grandi dimensioni è bene prestare particolare attenzione al movimento della testa, soprattutto se richiedono un movimento frequente lungo gli assi orizzontale e verticale.

## <a name="gaze-direction"></a>Direzione dello sguardo

Per evitare l'affaticamento oculare e la tensione a livello cervicale, il contenuto dovrebbe essere progettato in modo da evitare movimenti eccessivi di occhi e collo.
* **Evita** angolature dello sguardo di oltre 10 gradi al di sopra dell'orizzonte (spostamento verticale)
* **Evita** angolature dello sguardo di oltre 60 gradi al di sotto dell'orizzonte (spostamento verticale)
* **Evitare** rotazioni del collo di oltre 45 gradi rispetto al centro (spostamento orizzontale)

L'angolo di sguardo fisso ottimale viene considerato tra i 10 e i 20 gradi sotto l'orizzonte, perché la testa tende a inclinarsi leggermente verso il basso, soprattutto durante le attività.

## <a name="arm-positions"></a>Posizioni delle braccia

L'affaticamento muscolare può aumentare quando gli utenti devono tenere una mano alzata per tutta la durata di un'esperienza. Può anche essere faticoso per l'utente dover effettuare ripetutamente movimenti di simulazione del tocco con un dito per periodi prolungati. È pertanto consigliabile evitare di richiedere movimenti ripetuti e costanti. Questo obiettivo può essere raggiunto incorporando brevi interruzioni oppure offrendo la possibilità di interagire con l'app con una combinazione di gesti e input vocale.

## <a name="see-also"></a>Vedere anche
* [Sguardo fisso](gaze-and-commit.md)
* [Stabilità degli ologrammi](../develop/platform-capabilities-and-apis/hologram-stability.md)
* [Interazioni istintive](interaction-fundamentals.md)
* [Frame olografico](holographic-frame.md)
* [Calibrazione](/hololens/hololens-calibration)

---
title: Sistemi di coordinate
description: I sistemi di coordinate spaziali usati per la creazione di esperienze di realtà miste, in piedi, in scala e in scala mondiale.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: sistema di coordinate, sistema di coordinate spaziali, solo orientamento, scalabilità verticale, scalabilità, scalabilità, scalabilità globale, 360 gradi, seduto, in piedi, stanza, mondo, scala, posizione, orientamento, fermo, allegato, fase, ancoraggio, ancoraggio spaziale, blocco globale, blocco globale, blocco del corpo, blocco del corpo, limiti, persistenza, condivisione, perdita di rilevamento, ancoraggio spaziale cloud, headset di realtà mista, headset di realtà mista, auricolare di realtà virtuale, HoloLens, MRTK, Toolkit reality
ms.openlocfilehash: 6d4bddc17027ad32f82fbc8c37860e64b2bc57eb
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/20/2021
ms.locfileid: "98582414"
---
# <a name="coordinate-systems"></a>Sistemi di coordinate

Alle loro core, le app per la realtà mista inseriscono [ologrammi](../discover/hologram.md) nel mondo che sembrano e suonino oggetti reali. Questo implica il posizionamento e l'orientamento precisi degli ologrammi in posizioni significative nel mondo, indipendentemente dal fatto che il mondo sia la stanza fisica o un'area di autenticazione virtuale creata. Windows fornisce vari sistemi di coordinate reali per esprimere la geometria, nota come **sistemi di coordinate spaziali**. È possibile utilizzare i sistemi di coordinate spaziali per motivare la posizione dell'ologramma, l'orientamento, il raggio di [sguardi](gaze-and-commit.md) o le [posizioni della mano](hands-and-tools.md).

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/TneGSeqVAXQ" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

## <a name="device-support"></a>Supporto di dispositivi

<table>
    <colgroup>
    <col width="40%" />
    <col width="20%" />
    <col width="20%" />
    <col width="20%" />
    </colgroup>
    <tr>
        <td><strong>Funzionalità</strong></td>
        <td><a href="/hololens/hololens1-hardware"><strong>HoloLens (prima generazione)</strong></a></td>
        <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
        <td><a href="/windows/mixed-reality/immersive-headset-hardware-details"><strong>Visori VR immersive</strong></a></td>
    </tr>
     <tr>
        <td><a href="coordinate-systems.md#stationary-frame-of-reference">Cornice fissa di riferimento</a></td>
        <td>✔️</td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="coordinate-systems.md#attached-frame-of-reference">Frame di riferimento allegato</a></td>
        <td>✔️</td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="coordinate-systems.md#stage-frame-of-reference">Cornice della fase di riferimento</a></td>
        <td>Non ancora supportata</td>
        <td>Non ancora supportata</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="coordinate-systems.md#spatial-anchors">Ancoraggi nello spazio</a></td>
        <td>✔️</td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="spatial-mapping.md">Mapping spaziale</a></td>
        <td>✔️</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
    <tr>
        <td><a href="scene-understanding.md">Informazioni sulle scene</a></td>
        <td>❌</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
</table>

## <a name="mixed-reality-experience-scales"></a>Scalabilità dell'esperienza di realtà mista

È possibile progettare app a realtà mista per un'ampia gamma di esperienze utente, da visualizzatori video di 360 gradi usando l'orientamento della cuffia per app e giochi su scala globale con mapping spaziale e ancoraggi spaziali:

<br>

| Scalabilità dell'esperienza | Requisiti | Esperienza di esempio | 
|----------|----------|----------|
|  **Solo orientamento** |  **Orientamento auricolare** (gravità-allineato) |  360 ° Visualizzatore video | 
|  **Con scalabilità verticale** |  Sopra più la **posizione dell'auricolare** in base alla posizione zero |  Gioco da corsa o simulatore di spazio | 
|  **Scalabilità permanente** |  Sopra oltre la **fase di origine del piano** |  Gioco di azione in cui si Duck and Dodge sul posto  | 
|  **Scalabilità locale** |  **Poligono** superiore e limite di fasi |  Gioco rompicapo in cui è possibile aggirare il puzzle | 
|  **Scalabilità globale** |  **Ancoraggi spaziali** (e in genere [mapping spaziale](spatial-mapping.md)) |  Gioco con nemici provenienti da muri reali, ad esempio [RoboRaid](https://www.microsoft.com/p/roboraid/9nblggh5fv3j) | 

La scalabilità dell'esperienza segue un modello di "nidificazione di bambole". Il principio di progettazione principale per la realtà mista di Windows è un dato auricolare che supporta le app create per una scalabilità dell'esperienza di destinazione e tutte le scale inferiori:

<br>

| rilevamento 6DOF | Definito dal piano | rilevamento 360 ° | Limiti definiti | Ancoraggi nello spazio | Esperienza max | 
|----------|----------|----------|----------|----------|----------|
|  No |  - |  - |  - |  - |  **Solo orientamento** | 
|  **Sì** |  No |  - |  - |  - |  **Seduti** | 
|  **Sì** |  **Sì** |  No |  - |  - |  **In attesa** | 
|  **Sì** |  **Sì** |  **Sì** |  No |  - |  **In piedi-360 °** | 
|  **Sì** |  **Sì** |  **Sì** |  **Sì** |  No |  **Room** | 
|  **Sì** |  **Sì** |  **Sì** |  **Sì** |  **Sì** |  **World** | 

Il frame di fase del riferimento non è ancora supportato in HoloLens. Un'app scalabile in HoloLens attualmente deve usare il [mapping spaziale](spatial-mapping.md) o la [comprensione della scena](scene-understanding.md) per individuare il piano e le pareti dell'utente.

## <a name="spatial-coordinate-systems"></a>Sistemi di coordinate spaziali

Tutte le applicazioni grafiche 3D utilizzano [sistemi di coordinate cartesiane](/windows/uwp/graphics-concepts/coordinate-systems) per motivare le posizioni e gli orientamenti degli oggetti virtuali. Questi sistemi di coordinate stabiliscono 3 assi perpendicolari lungo i quali posizionare gli oggetti: un asse X, Y e Z.

In [realtà mista](../discover/mixed-reality.md), le app ragionano sui sistemi di coordinate virtuali e fisici. Windows chiama un sistema di coordinate che ha un significato reale nel mondo fisico di un **sistema di coordinate spaziali**.

I sistemi di coordinate spaziali esprimono i valori delle coordinate in metri. Ciò significa che gli oggetti posizionati a distanza di due unità nell'asse X, Y o Z verranno visualizzati 2 metri l'uno dall'altro quando ne viene eseguito il rendering in realtà mista. A questo scopo, è possibile eseguire facilmente il rendering di oggetti e ambienti su scala reale.

In generale, i sistemi di coordinate cartesiane possono essere gestiti a destra o a sinistra. I sistemi di coordinate spaziali su Windows sono sempre a destra, il che significa che l'asse X positivo punta a destra, l'asse Y positivo punta verso l'alto (allineato alla gravità) e l'asse Z positivo punta verso l'utente.

In entrambi i tipi di sistemi di coordinate, l'asse X positivo punta a destra e l'asse Y positivo punta verso l'alto. La differenza consiste nel fatto che l'asse Z positivo punti verso o fuori dall'utente. Tenere presente quale direzione indica l'asse Z positivo puntando le dita della parte sinistra o destra nella direzione X positiva e inserendole nella direzione Y positiva. La direzione dei punti di controllo, verso o lontano da te, è la direzione che l'asse Z positivo punta per il sistema di coordinate.

## <a name="building-an-orientation-only-or-seated-scale-experience"></a>Creazione di un'esperienza di solo orientamento o con scalabilità verticale

La chiave per il [rendering](../develop/platform-capabilities-and-apis/rendering.md) olografico è la modifica della visualizzazione dell'app degli ologrammi per ogni fotogramma mentre l'utente si sposta, in modo che corrisponda al movimento della testa stimato. È possibile creare **esperienze con scalabilità verticale** che rispettano le modifiche alla posizione iniziale e all'orientamento della testa dell'utente usando un **frame di riferimento fisso**.

Il contenuto deve ignorare gli aggiornamenti della posizione Head, rimanendo fisso a un'intestazione scelta e a distanza dall'utente sempre. L'esempio principale è il video di 360 gradi: poiché il video viene acquisito da un'unica prospettiva fissa, potrebbe rovinare l'illusione per la posizione di visualizzazione in base al contenuto, anche se l'orientamento della visualizzazione cambia quando l'utente cerca. È possibile compilare tali **esperienze solo di orientamento** utilizzando un **frame di riferimento allegato**.

### <a name="stationary-frame-of-reference"></a>Cornice fissa di riferimento

Il sistema di coordinate fornito da un frame di riferimento stazionario opera per rendere le posizioni degli oggetti più stabili possibile in base al mondo, rispettando al contempo le modifiche nella posizione Head dell'utente.

Per esperienze con scalabilità verticale in un motore di gioco quale [Unity](https://unity3d.com/), un frame di riferimento fisso è quello che definisce la "origine mondiale" del motore. Gli oggetti posizionati in una coordinata specifica del mondo usano il frame di riferimento fisso per definire la propria posizione nel mondo reale usando le stesse coordinate. Il contenuto che rimane in tutto il mondo, anche quando l'utente si aggira, è noto come contenuto con **blocco globale** .

Un'app crea in genere un frame di riferimento fisso all'avvio e usa il sistema di coordinate per tutta la durata dell'app. Gli sviluppatori di app in Unity possono semplicemente iniziare a collocare il contenuto in base all'origine, che sarà alla posizione iniziale e all'orientamento iniziali dell'utente. Se l'utente passa a una nuova posizione e vuole continuare a eseguire la propria esperienza di scalabilità, è possibile ricentrare l'origine del mondo in tale posizione.

Nel corso del tempo, poiché il sistema apprende di più sull'ambiente dell'utente, potrebbe determinare che le distanze tra i diversi punti nel mondo reale sono più brevi o più lunghe del sistema creduto in precedenza. Se si eseguono il rendering degli ologrammi in un frame di riferimento fisso per un'app in HoloLens, in cui gli utenti vagano oltre un'area di circa 5 metri di larghezza, l'app può osservare la tendenza nella posizione osservata di tali ologrammi. Se l'esperienza degli utenti si aggira oltre 5 metri, si sta creando un' [esperienza globale](#building-a-world-scale-experience), che richiede altre tecniche per la stabilità degli ologrammi, come descritto di seguito.

### <a name="attached-frame-of-reference"></a>Frame di riferimento allegato

Un frame allegato di riferimento si sposta con l'utente mentre viene aggirato, con un'intestazione fissa definita quando l'app crea prima il frame. In questo modo l'utente è in grado di esaminare il contenuto inserito all'interno di tale frame di riferimento. Il contenuto di cui viene eseguito il rendering in questa modalità relativa all'utente è denominato contenuto con **blocco del corpo** .

Quando la cuffia non riesce a capire dove si trova nel mondo, un frame di riferimento collegato fornisce l'unico sistema di coordinate, che può essere usato per il rendering degli ologrammi. In questo modo è ideale per la visualizzazione dell'interfaccia utente di fallback per indicare all'utente che il dispositivo non riesce a trovarle nel mondo. Le app con scalabilità verticale o superiore devono includere un fallback di solo orientamento per aiutare l'utente a tornare a un nuovo utente, con un'interfaccia utente simile a quella mostrata nella [Home realtà mista](../discover/navigating-the-windows-mixed-reality-home.md).

## <a name="building-a-standing-scale-or-room-scale-experience"></a>Creazione di un'esperienza di scalabilità o scalabilità in base all'ambiente

Per andare oltre la scalabilità verticale su un headset immersivo e creare un' **esperienza di scalabilità permanente**, è possibile usare il **frame della fase di riferimento**.

Per offrire un' **esperienza di scalabilità** in una stanza, consentire agli utenti di aggirare i limiti di 5 metri predefiniti, è possibile controllare anche i **limiti di fase** .

### <a name="stage-frame-of-reference"></a>Cornice della fase di riferimento

Quando si configura per la prima volta un auricolare immersivo, l'utente definisce una **fase** che rappresenta lo spazio in cui si verificheranno realtà miste. La fase definisce almeno un' **origine della fase**, un sistema di coordinate spaziali centrato sulla posizione del piano scelto dall'utente e sull'orientamento in base a cui si intende usare il dispositivo. Inserendo il contenuto in questo sistema di coordinate della fase sul piano Y = 0, è possibile assicurarsi che gli ologrammi vengano visualizzati comodamente al piano quando l'utente è in piedi, offrendo agli utenti un' **esperienza di scalabilità permanente**.

### <a name="stage-bounds"></a>Limiti di fase

L'utente può anche definire facoltativamente i **limiti della fase**, un'area all'interno della stanza che è stata cancellata per spostarsi in realtà mista. In tal caso, l'app può creare un' **esperienza su scala**, usando questi limiti per assicurarsi che gli ologrammi siano sempre posizionati laddove l'utente possa raggiungerli.

Poiché il frame della fase di riferimento fornisce un singolo sistema di coordinate fisso entro il quale collocare il contenuto relativo al piano, si tratta del percorso più semplice per il porting di applicazioni in scala e in scala sviluppate per le cuffie di realtà virtuale. Tuttavia, come con le piattaforme VR, un singolo sistema di coordinate può stabilizzare solo il contenuto in circa un diametro di 5 metri (16 piedi), prima che gli effetti della leva-ARM causino il contenuto lontano dal centro per spostarsi in modo evidente quando il sistema si adatta. Per superare i 5 metri, sono necessari ancoraggi spaziali.

## <a name="building-a-world-scale-experience"></a>Creazione di un'esperienza su scala globale

HoloLens consente di ottenere **esperienze** reali che consentono agli utenti di aggirare oltre 5 contatori. Per creare un'app su scala globale, sono necessarie nuove tecniche oltre a quelle usate per le esperienze su scala.

### <a name="why-a-single-rigid-coordinate-system-cannot-be-used-beyond-5-meters"></a>Perché non è possibile usare un singolo sistema di coordinate rigido oltre 5 contatori

Attualmente, quando si scrivono giochi, app per la visualizzazione dei dati o app per la realtà virtuale, l'approccio tipico consiste nello stabilire un sistema di coordinate globale assoluto a cui tutte le altre coordinate possano eseguire un mapping affidabile. In tale ambiente, è sempre possibile trovare una trasformazione stabile che definisce una relazione tra due oggetti qualsiasi nel mondo. Se gli oggetti non sono stati spostati, le trasformazioni relative rimarranno sempre le stesse. Questo tipo di sistema di coordinate globale funziona bene quando si esegue il rendering di un mondo puramente virtuale in cui si conoscono in anticipo tutte le geometrie. Le app VR con scalabilità orizzontale oggi stabiliscono in genere questo tipo di sistema di coordinate scalabile assoluto con la relativa origine al pavimento.

Al contrario, un dispositivo di realtà mista non tethered, ad esempio HoloLens, ha una conoscenza dinamica basata sui sensori del mondo, adattando continuamente le proprie conoscenze nel tempo dell'ambiente dell'utente, in quanto attraversano molti contatori in un intero piano di un edificio. In un'esperienza su scala globale, se tutti gli ologrammi sono stati inseriti in un unico sistema di coordinate rigide, tali ologrammi dovrebbero necessariamente andare alla deriva nel tempo, in base al mondo o tra loro.

Ad esempio, l'auricolare può attualmente ritenere che due posizioni del mondo siano a 4 metri di distanza e, successivamente, ridefinire la comprensione, apprendendo che i percorsi sono in effetti di 3,9 metri. Se inizialmente questi ologrammi venivano posizionati a distanza di 4 metri in un unico sistema di coordinate rigide, una di esse verrebbe sempre visualizzata 0,1 metri dal mondo reale.

### <a name="spatial-anchors"></a>Ancoraggi nello spazio

La realtà mista di Windows risolve il problema descritto nella sezione precedente consentendo di creare [ancoraggi spaziali](spatial-anchors.md) per contrassegnare punti importanti nel mondo in cui l'utente ha inserito gli ologrammi. Un ancoraggio nello spazio rappresenta un punto importante nel mondo di cui il sistema deve tenere traccia nel tempo.

Quando il dispositivo apprende il mondo, questi ancoraggi spaziali possono regolare la loro posizione in base a un altro, in base alle esigenze, per garantire che ogni ancoraggio rimanga esattamente nel punto in cui è stato posizionato in base al mondo reale. Inserendo un ancoraggio spaziale nella posizione in cui l'utente inserisce un ologramma e quindi posizionando tale ologramma in base al relativo ancoraggio spaziale, è possibile garantire che l'ologramma mantenga una stabilità ottimale, anche quando l'utente esegue il roaming in decine di contatori.

Questa regolazione continua degli ancoraggi spaziali basati l'uno sull'altro è la differenza principale tra sistemi di coordinate da ancoraggi spaziali e frame di riferimento stazionari:

* Gli ologrammi posizionati nel fotogramma fisso di riferimento mantengono una relazione rigida tra loro. Tuttavia, quando l'utente percorre le distanze lunghe, il sistema di coordinate del frame potrebbe derivare dal mondo per assicurarsi che gli ologrammi accanto all'utente siano stabili.

* Gli ologrammi posizionati nel frame della fase di riferimento mantengono anche una relazione rigida tra loro. A differenza del frame stazionari, il frame della fase rimane sempre fisso sulla base dell'origine fisica definita. Tuttavia, il contenuto di cui viene eseguito il rendering nel sistema di coordinate della fase oltre il limite di 5 contatori verrà visualizzato stabile solo quando l'utente è in tale limite.

* Gli ologrammi posizionati usando un ancoraggio spaziale possono essere derivati in base a ologrammi posizionati usando un altro ancoraggio spaziale. Ciò consente a Windows di migliorare la comprensione della posizione di ogni ancoraggio spaziale, anche se, ad esempio, un ancoraggio deve adattarsi a sinistra e un altro ancoraggio deve adattarsi a destra.

A differenza di un frame di riferimento stazionario, che ottimizza sempre la stabilità in prossimità dell'utente, il frame della fase dei riferimenti e degli ancoraggi spaziali garantisce stabilità vicino alle origini. Questo aiuta gli ologrammi a rimanere esattamente nel tempo, ma significa anche che gli ologrammi sottoposti a rendering troppo lontani dall'origine del sistema di coordinate potranno riscontrare un aumento degli effetti della leva-ARM. Questo è dovuto al fatto che piccole regolazioni della posizione e dell'orientamento della fase o dell'ancoraggio vengono ingrandite in modo proporzionale alla distanza da tale ancoraggio. 

Una regola empirica consiste nel garantire che tutto ciò che viene eseguito il rendering in base a un sistema di coordinate dell'ancoraggio spaziale distanti si trovi entro circa 3 metri dalla relativa origine. Per un'origine della fase vicina, il rendering di contenuto distante è accettabile, poiché qualsiasi errore di posizione maggiore influirà solo sui piccoli ologrammi che non si sposteranno molto nella visualizzazione dell'utente.

### <a name="spatial-anchor-persistence"></a>Persistenza di ancoraggio spaziale

Gli ancoraggi spaziali possono anche consentire all'app di ricordare un percorso importante anche dopo la sospensione dell'app o l'arresto del dispositivo.

È possibile salvare su disco gli ancoraggi spaziali creati dall'app e quindi caricarli di nuovo in un secondo momento, rendendoli in modo permanente nell' **Archivio di ancoraggio spaziale** dell'app. Quando si salva o si carica un ancoraggio, si fornisce una chiave di stringa significativa per l'app, per identificare l'ancoraggio in un secondo momento. Si pensi a questa chiave come nome file per l'ancoraggio. Se si vuole associare altri dati a tale ancoraggio, ad esempio un modello 3D che l'utente ha inserito in quel percorso, salvarlo nella risorsa di archiviazione locale dell'app e associarlo alla chiave scelta.

Grazie alla permanenza degli ancoraggi nello Store, gli utenti possono inserire singoli ologrammi o collocare un'area di lavoro attorno alla quale un'app inserirà i vari ologrammi e quindi troverà gli ologrammi in un secondo momento, su molti usi dell'app.

È anche possibile usare gli <a href="/azure/spatial-anchors/overview" target="_blank">ancoraggi spaziali di Azure</a> per la persistenza ologramma asincrona nei dispositivi HoloLens, iOS e Android.  Grazie alla condivisione di un ancoraggio spaziale cloud durevole, più dispositivi possono osservare lo stesso ologramma persistente nel tempo, anche se i dispositivi non sono presenti contemporaneamente.

### <a name="spatial-anchor-sharing"></a>Condivisione di ancoraggio spaziale

L'app può anche condividere un ancoraggio spaziale in tempo reale con altri dispositivi, consentendo esperienze condivise in tempo reale.

Usando gli <a href="/azure/spatial-anchors/overview" target="_blank">ancoraggi spaziali di Azure</a>, l'app può condividere un ancoraggio spaziale tra più dispositivi HoloLens, iOS e Android. Facendo in modo che ciascun dispositivo esegua il rendering di un ologramma usando lo stesso ancoraggio nello spazio, tutti gli utenti vedranno l'ologramma nello stesso punto nel mondo reale.

## <a name="avoid-head-locked-content"></a>Evitare contenuto con blocco Head

Si sconsiglia vivamente il rendering del contenuto con blocco Head, che rimane in un punto fisso dello schermo, ad esempio un HUD. In generale, il contenuto con blocco Head è scomodo per gli utenti e non sembra una parte naturale del loro mondo.

Il contenuto con blocco Head deve essere in genere sostituito con gli ologrammi collegati all'utente o inseriti nel mondo stesso. I [cursori](cursors.md) , ad esempio, devono essere in genere inseriti nel mondo, scalabilità naturale per riflettere la posizione e la distanza dell'oggetto sotto lo sguardo dell'utente.

## <a name="handling-tracking-errors"></a>Gestione degli errori di rilevamento

In alcuni ambienti, ad esempio i corridoi scuri, potrebbe non essere possibile che una cuffia che usa il rilevamento interno per individuarsi correttamente nel mondo. In questo modo gli ologrammi possono non essere visualizzati o visualizzati in posizioni errate se gestiti in modo errato. Verranno ora illustrate le condizioni in cui questo può verificarsi, il suo effetto sull'esperienza utente e suggerimenti per gestire al meglio questa situazione.

### <a name="headset-cant-track-due-to-insufficient-sensor-data"></a>Non è possibile rilevare le cuffie a causa di dati del sensore insufficienti

In alcuni casi, i sensori dell'auricolare non sono in grado di individuare il punto in cui si trova l'auricolare. Ciò avviene se:

* La stanza è scura
* Se i sensori sono coperti da capelli o mani
* Se le aree circostanti non hanno una trama sufficiente.

In questo caso, l'auricolare non sarà in grado di tenere traccia della propria posizione con una precisione sufficiente per eseguire il rendering degli ologrammi con blocco globale. Non è possibile determinare se un ancoraggio spaziale, un frame stazionario o un frame della fase è basato sul dispositivo. Tuttavia, è comunque possibile eseguire il rendering del contenuto con blocco del corpo nel frame di riferimento allegato.

L'app deve indicare all'utente come ottenere il rilevamento posizionale, eseguendo il rendering di alcuni contenuti con blocco del corpo di fallback che descrivono alcuni suggerimenti, ad esempio l'individuazione dei sensori e l'attivazione di più luci.

### <a name="headset-tracks-incorrectly-due-to-dynamic-changes-in-the-environment"></a>Le tracce dell'auricolare non sono corrette a causa di modifiche dinamiche nell'ambiente

Il dispositivo non è in grado di rilevare correttamente se sono presenti molte modifiche dinamiche nell'ambiente, ad esempio molti utenti che camminano nella stanza. In questo caso, gli ologrammi possono sembrare un salto o una deviazione quando il dispositivo tenta di tenerne traccia in questo ambiente dinamico. Se si raggiunge questo scenario, si consiglia di usare il dispositivo in un ambiente meno dinamico.

### <a name="headset-tracks-incorrectly-because-the-environment-has-changed-significantly-over-time"></a>Il rilevamento dell'auricolare non è corretto perché l'ambiente è stato modificato in modo significativo nel tempo

Quando si inizia a usare una cuffia in un ambiente in cui la mobilia, i blocchi da parete e così via sono stati spostati, è possibile che alcuni ologrammi siano spostati dalle posizioni originali. Gli ologrammi precedenti possono anche spostarsi quando l'utente si sposta nel nuovo spazio perché la comprensione dello spazio del sistema non è più vera. Il sistema tenta quindi di modificare il mapping dell'ambiente provando anche a riconciliare le funzionalità della chat room. In questo scenario, è consigliabile incoraggiare gli utenti a sostituire gli ologrammi aggiunti al mondo se non vengono visualizzati quando previsto.

### <a name="headset-tracks-incorrectly-due-to-identical-spaces-in-an-environment"></a>Le tracce dell'auricolare non sono corrette a causa di spazi identici in un ambiente

In alcuni casi, una casa o un altro spazio può avere due aree identiche. Ad esempio, due sale riunioni identiche, due aree d'angolo identiche, due manifesti identici di grandi dimensioni che coprono il campo di visualizzazione del dispositivo. In questi scenari, il dispositivo può, a volte, essere confuso tra le parti identiche e contrassegnarle come la stessa rappresentazione interna. Ciò può causare la visualizzazione degli ologrammi da alcune aree in altre posizioni. Il dispositivo può iniziare a perdere il rilevamento spesso perché la relativa rappresentazione interna dell'ambiente è danneggiata. In questo caso, è consigliabile reimpostare la comprensione ambientale del sistema. La reimpostazione della mappa comporta la perdita di tutte le posizionamenti di ancoraggio spaziali. In questo modo l'auricolare si rileverà correttamente nelle aree univoche dell'ambiente. Tuttavia, il problema può verificarsi se il dispositivo viene confuso nuovamente tra le aree identiche.

## <a name="see-also"></a>Vedere anche
* [Presentazione GDC 2017 su sistemi di coordinate spaziali e rendering olografico](https://channel9.msdn.com/events/GDC/GDC-2017/GDC2017-008)
* [Sistemi di coordinate in Unity](../develop/unity/coordinate-systems-in-unity.md)
* [Sistemi di coordinate in DirectX](../develop/native/coordinate-systems-in-directx.md)
* [Ancoraggi nello spazio](spatial-anchors.md)
* [Esperienze condivise nella realtà mista](../develop/platform-capabilities-and-apis/shared-experiences-in-mixed-reality.md)
* <a href="/azure/spatial-anchors" target="_blank">Ancoraggi nello spazio di Azure</a>
* [Case study - Guardare attraverso fori nella realtà](../out-of-scope/case-study-looking-through-holes-in-your-reality.md)
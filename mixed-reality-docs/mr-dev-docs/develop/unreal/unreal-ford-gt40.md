---
title: Esperienza di Ford GT40
description: Seguire questa procedura per esplorare la creazione dell'applicazione di realtà mista di Ford GT40 con MRTK per HoloLens 2 in Unreal.
author: hferrone
ms.author: v-hferrone
ms.date: 3/23/2021
ms.topic: article
keywords: Unreal Engine 4, UE4, HoloLens, HoloLens 2, realtà mista, distribuzione su dispositivo, PC, documentazione, auricolare realtà mista, headset di realtà mista di Windows, auricolare della realtà virtuale
appliesto:
- HoloLens 2
ms.openlocfilehash: ca577bdc5bc30aebf80c9888345eb0e2d5c3ce6d
ms.sourcegitcommit: cc9d90b046a9fce792058fea25ae13a9186e43e7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/24/2021
ms.locfileid: "105008926"
---
# <a name="the-making-of-the-ford-gt40-experience"></a>Creazione dell'esperienza di Ford GT40

*"Pre-MRTK, lo sviluppo per HoloLens 2 con Unreal era un po' noioso perché tutte le interazioni spaziali dovevano essere codificate manualmente in C++. Il MRTK per Unreal ha fatto molto di più le stesse attività. Vorrei stimare che il tempo necessario per il prototipo iniziale venisse ridotto a metà. "* -Jose Rodriguez, sviluppatore di software

*"L'esperienza di Ford GT40 è la prova che un'app HoloLens 2 a fedeltà elevata può essere completata in pochi mesi, con un budget modesto, ma offre comunque risultati estremamente effettivi".*  -Daniel Cheetham, Chief Innovation Officer, Happy Finish

Usando il Toolkit di realtà mista (MRTK) per una società di produzione creativa, la buona fortuna ha offerto un'esperienza HoloLens 2 che offre una nuova prospettiva in Ford GT40, la leggendaria razza che ha battuto Ferrari alle 24 ore di Le Mans!

Grazie a un'ampia gamma di interazioni spaziali naturali e intuitive, gli utenti possono esplorare i GT40's di bellezza, prestazioni e progettazione, tutti distribuiti in modo da sfruttare la massima fedeltà visiva fornita da Unreal Engine. Lo sviluppo software per l'intero progetto è stato completato da un singolo sviluppatore in meno di tre mesi, reso possibile da MRTK per l'ambiente di progettazione e creazione di script visivi non reali.

> [!div class="nextstepaction"]
> [Scaricare l'app Ford GT40](https://www.microsoft.com/p/ford-gt40/9p4vllktfvfp)

![Immagine di Ford GT40 Hero](images/ford-gt40-hero.jpg)

## <a name="the-ask"></a>Richiedi

Il buon fine è una delle società di produzione creative leader del mondo, con una base client che include, Ford, Microsoft, Nike, Netflix, Vodafone e altri nomi di famiglia. La società è stata avviata come agenzia foto-ritocco di fascia alta, diramazione in film e CGI prima di estenderne la dedizione all'eccellenza nella narrazione immersiva con progettazione e interazione spaziali 3D.

A metà 2020, Microsoft ha affrontato la soluzione completa per produrre un'app demo che può aiutare a mostrare le possibilità abilitate dal nuovo Toolkit di realtà mista (MRTK) per Unreal, che si basa sul supporto per HoloLens 2 in Unreal Engine. A questo punto, la società ha già realizzato due progetti HoloLens 2 con esito positivo. Entrambi erano destinati a una marca di consumer riconosciuta a livello globale, che ha scelto Unreal in HoloLens 2 per uno strumento di vendita R&D/B2B interno per la massima fedeltà visiva, come richiesto per presentare al meglio i prodotti di fascia alta del cliente.

Sebbene la soluzione stessa sarebbe stata lasciata invariata, doveva soddisfare alcune linee guida fondamentali. In primo luogo, doveva concentrarsi su uno scenario aziendale per illustrare l'utilità di Unreal in HoloLens 2 all'esterno del settore dei giochi. In secondo luogo, doveva essere solo dispositivo, ovvero può fungere da demo autonoma, senza la necessità di una connessione di rete e di una potenza di elaborazione esterna, per ottenere la frequenza dei fotogrammi di destinazione e la qualità visiva. In terzo luogo, è opportuno combinare la gamma di interazioni intuitive supportate da MRTK in un'esperienza naturale e semplice. Infine, la soluzione proposta dovrebbe presentare la fedeltà visiva intrinseca e altri vantaggi del motore Unreal, ad esempio l'efficienza dello shader. 

In base a queste linee guida, il buon fine ha iniziato a riflettere le possibilità, arrivando con l'idea di un'esperienza di realtà mista che usava l'interazione spaziale per comunicare il valore di un prodotto di nome e valore elevato. Dopo aver preso in considerazione una gamma di oggetti che includono orologi, fotocamere, automobili e jet privati, il lieto fine ha deciso di Ford GT40, una legenda automobilistica che ha ottenuto una notorietà nel 1966 quando Ford ha vinto la Ferrari alle 24 ore di Le Mans, come illustrato 2019 nel video di successo di Blockbuster Ford vs. Ferrari. 

Quando si ottiene l'acquisto da Ford, un client con una buona soddisfazione esistente, l'azienda ha deciso di fornire una nuova prospettiva sull'icona automobilistica classica.

## <a name="the-solution"></a>Soluzione

Il lavoro è iniziato il 7 maggio 2020. Una volta ottenuti i file del modello GT40, un artista 3D ha impiegato tre settimane per ottimizzare i modelli poligonali, il mapping UV, il ridisegno delle mappe delle trame e la riduzione delle mappe nel minor numero possibile di trame. Un artista tecnico ha lavorato in parallelo per eseguire il benchmarking dell'output dell'artista 3D, determinare dimensioni di trama ottimali in base alle frequenze dei fotogrammi di destinazione e scoprire il modo migliore per applicare shader personalizzati in irreale. Tutte queste operazioni di pre-produzione sono state eseguite per ottimizzare l'esperienza sul dispositivo.

Creative Director Alex Lambert ha immesso l'immagine al termine del lavoro di pre-produzione. Ha iniziato guardando Ford vs. Ferrari, pensando a come tessere una descrizione dettagliata degli scenari e delle interazioni. Ha inoltre raccolto i riferimenti visivi per l'autore dell'interfaccia utente, ad esempio le immagini del dashboard GT40 e gli oggetti visivi della pista di Le Mans, e le registrazioni audio raccolte di GT40 in azione per la finestra di progettazione del suono.

Con le risorse di preproduzione definite e ottimizzate a disposizione, lo sviluppatore di software freelance Jose Rodriguez è stato integrato per integrarlo. Rodriguez era stato lo sviluppatore dei due progetti precedenti HoloLens 2 che hanno completato il buon fine, prima del rilascio di MRTK per Unreal.

Il valore fornito da MRTK per Unreal è diventato presto evidente, contribuendo a Rodriguez a offrire un prototipo iniziale in una settimana. Ha implementato tre scenari univoci, uno per ognuno degli aspetti chiave del GT40 identificato da Lambert: la sua bellezza, le sue prestazioni e la sua progettazione. Per ogni scenario, Rodriguez ha usato MRTK per integrare le risorse 3D ottimizzate dalla fase di pre-produzione in una gamma di interazioni spaziali. 

Con MRTK per Unreal, Rodriguez ha creato ogni scenario usando la finestra di progettazione dell'interfaccia utente di Visual Unreal Motion Graphics (UMG) invece di implementare tutti gli elementi in C++. Gli [strumenti UX per Unreal](https://www.unrealengine.com/marketplace/product/mixed-reality-ux-tools), il plug-in che contiene i componenti e i blocchi di compilazione dell'esperienza utente all'interno di MRTK, ha fornito [schemi](https://docs.unrealengine.com/ProgrammingAndScripting/Blueprints/index.html) insoliti per la simulazione di input, interazioni con gli script visivi, pulsanti stampabili, manipolazione di immagini 3D, magnetismo della superficie e altro ancora, tutto all'interno di un ambiente di progettazione senza codice e trascinamento.

"MRTK, lo sviluppo per HoloLens 2 con Unreal era un po' noioso perché tutte le interazioni spaziali dovevano essere codificate manualmente, in C++", afferma Rodriguez. "MRTK per Unreal ha fatto molto di più le stesse attività. Vorrei stimare che il tempo necessario per il prototipo iniziale venisse ridotto a metà. "

Con un prototipo a disposizione, il team ha iniziato le iterazioni settimanali per ridefinire l'esperienza. "Questo è il momento in cui la funzionalità di acquisizione della realtà mista e il portale del dispositivo Windows sono diventati molto utili", richiama Lambert. "Li ho usati per acquisire le revisioni della progettazione, trasmettere commenti e suggerimenti ad altri utenti e collaborare alle modifiche. Lavorare in isolamento, ad esempio, non sarebbe stato possibile senza tali strumenti ".

![App di Ford GT40 dell'editor Unreal in esecuzione con componenti della rotella disposti in sequenza](images/ford-gt40-img-04.JPG)

Quando Lambert ha richiesto modifiche, come il riposizionamento degli elementi dell'interfaccia utente o la modifica del comportamento di un pulsante, Rodriguez le ha implementate. Mentre alcune delle modifiche richiedevano modifiche minime al codice, la maggior parte di esse venivano gestite nella finestra di progettazione visiva non reale. "Mi sono stupito della velocità con cui ho potuto iterare", afferma Rodriguez. "Non è stato sprecato tempo; Apportare una modifica nella finestra di progettazione e quindi premere Play per visualizzarla immediatamente sul dispositivo. Il MRTK ha davvero semplificato il lavoro. "

Rodriguez richiama anche che è stato impressionato dal modo in cui l'ambiente di produzione era pronto per tutti gli strumenti di sviluppo. "Abbiamo progredito in modo uniforme dal prototipo iniziale fino alla produzione finale, senza dover tornare indietro e implementare nuovamente o ottimizzare gli elementi nel codice", afferma.  

## <a name="the-final-build"></a>Compilazione finale

Buona conclusione della produzione di Ford GT40 Experience per HoloLens 2 il 28 luglio 2020, per dare una nuova prospettiva alla leggendaria corsa. L'esperienza inizia con una schermata iniziale, quindi guida l'utente per configurare un ancoraggio afferrando il logo Ford e inserendolo in una superficie piana come una tabella o un desktop. 

### <a name="beauty"></a>Bellezza

Il segmento **Beauty** riporta l'utente a uno strumento di configurazione di GT40, che Visualizza il GT40 su un piedistallo rotante, in modo analogo alla visualizzazione di un'automobile fisica in una presentazione automobilistica. L'utente può applicare diverse opzioni della rotellina, scegliere tra combinazioni di colori diverse e aprire e chiudere le porte e il trunk (o avviare, in modo che lo chiamano nel Regno Unito). Durante l'esperienza di bellezza, l'utente può prendere l'auto e manipolarla liberamente per un aspetto più vicino.

![GIF animata di GT40 Configurator in esecuzione su un dispositivo](images/ford-gt40-img-05.gif)

### <a name="performance"></a>Prestazioni

Il segmento **performance** Mostra la velocità e la durabilità GT40's. Il VoiceOver inizia con la descrizione del modo in cui l'auto è stata sviluppata e ha superato i ritmi di Ford Kingman, Arizona dimostrando i motivi, con gli oggetti visivi 3D che mostrano il GT40 in movimento sulla traccia dei test. Con l'introduzione del segmento di prestazioni, il VoiceOver chiede all'utente di "premere il pulsante le Mans per raggiungere il circuito".

![GIF animata dell'app GT40 Speed and durabilità in esecuzione su un dispositivo](images/ford-gt40-img-06.gif)

La seconda parte del segmento Performance presenta il GT40 in base all'intervallo di condizioni che i driver potrebbero riscontrare alle 24 ore delle Mans, che viene tenuta annualmente presso il circuito de la Sarthe vicino a Le Mans, Francia. Una visualizzazione 3D mostra l'auto in movimento sulla traccia le Mans, con i pulsanti forniti per velocizzare o rallentare l'auto. Immagini del tachimetro analogico GT40's e contagiri fluttuano sopra la visualizzazione Racetrack, con più dati di telemetria delle corse visualizzati in background. L'utente può passare tra le visualizzazioni giorno e notte e tra le condizioni di guida asciutte e umide, offrendo una prospettiva realistica e realistica delle informazioni su Ken Miles e sugli altri driver GT40 nella corsa effettiva.

### <a name="engineering"></a>Engineering

Il segmento **Engineering** dell'esperienza Ford GT40 presenta una delle innovazioni ingegneristiche che hanno aiutato Ford a vincere la gara: la possibilità di modificare i rotori e i rilievi dei freni in meno di un minuto rispetto ai 20-30 minuti necessari per tutti gli altri team. Usando i movimenti intuitivi, l'utente può modificare un modello 3D dettagliato della rotella GT40 e dell'assembly del freno. Per espandere l'assembly, l'utente sceglie una chiave lug, lo allinea al blocco centrale sulla rotellina, lo ruota in senso antiorario e quindi lo estrae dalla rotellina. Altri movimenti vengono usati per rimuovere i rotori e i riquadri del freno usati, sostituirli con quelli nuovi, comprimere l'assembly e riproteggere il blocco centrale. In background, un timer Visualizza il tempo trascorso, consentendo all'utente di verificare se è in grado di completare il processo con la stessa rapidità della squadra Pit a Le Mans.

![GIF animata dell'esperienza di progettazione di GT40 in esecuzione su un dispositivo](images/ford-gt40-img-07.gif)

L'esperienza di Ford GT40 può essere [scaricata da Microsoft Store](https://www.microsoft.com/p/ford-gt40/9p4vllktfvfp?activetab=pivot:overviewtab), consentendo a chiunque abbia un HoloLens 2 di esplorare il modo in cui il buon fine ha portato una nuova prospettiva alla leggendaria corsa.

### <a name="getting-impressive-visual-fidelity"></a>Ottenere fedeltà visiva impressionante

Sebbene la gamma di interazioni spaziali supportate dall'esperienza GT40 di Ford sia impressionante in modo autonomo, la creatività e la fedeltà visiva ottenuta dall'esperienza sono molto importanti. Grazie alla relativa ottimizzazione dei modelli 3D e all'uso di shader personalizzati non reali, il completamento del ciclo di prova ha raggiunto la destinazione di 60 fotogrammi al secondo, anche con il segmento delle prestazioni dell'app che si avvicina a 315.000 poligoni. 

"Sono molto soddisfatto del modo in cui siamo riusciti a unire un set di interazioni fluide e intuitive in un testo narrativo coerente e accattivante", afferma Lambert. "Ovviamente, la potenza di Unreal Engine in HoloLens 2 apre un nuovo mondo di opportunità per esperienze di realtà miste più sorprendenti e straordinarie. La fedeltà visiva senza compromessi non è sempre l'obiettivo finale per le applicazioni aziendali in HoloLens 2, ma, in questo caso, il supporto per Unreal in HoloLens 2 diventa inestimabile ".

### <a name="rapid-solution-delivery"></a>Distribuzione rapida delle soluzioni

Quanto è impressionante che l'esperienza dell'utente finale di Ford GT40 è il modo in cui la consegna è stata completata in modo rapido, con l'intero progetto, dal momento della pre-produzione alla distribuzione finale, fino a 12 settimane. In breve, il progetto ha utilizzato 1088 ore di lavoro, suddiviso come segue: Creative Director (80 hours), UX Designer (56 ore), UI Designer (40 hours), Sound Designer (40 hours), 3D/Technical Artist (328 ore), Software Developer (408 ore), Technical Director (40 ore), Producer (56 ore) e garanzia di qualità (40 ore).

"In generale, ci siamo avvicinati alle stime dei progetti originali", afferma Daniel Cheetham, Chief Innovation Officer, che ha partecipato alla divisione interattiva della società. "L'esperienza di Ford GT40 è la prova che un'app HoloLens 2 a fedeltà elevata può essere completata in pochi mesi, con un budget modesto, ma offre comunque risultati estremamente effettivi". 

Dal punto di vista dello sviluppo, in base alla sua esperienza precedente con Unreal in HoloLens 2, Rodriguez stima che la MRTK per inreale ha ridotto il tempo totale e lo sforzo richiesto per metà. Si nota anche come MRTK può aiutare gli sviluppatori che non hanno mai lavorato con HoloLens 2 per iniziare. "Quando altri sviluppatori affermano di essere interessati a una realtà mista, mi incoraggiano ad accedere, installare lo stack di sviluppo HoloLens 2 e MRTK. Il MRTK rende semplice e veloce la creazione di un'app e l'editor di oggetti visivi non reali funziona in modo da non dover neanche usare un dispositivo HoloLens 2 per iniziare. Non è affatto complicato, tutto funziona solo ".

### <a name="potential-azure-service-enhancements"></a>Miglioramenti potenziali per i servizi di Azure

Lambert rileva diversi modi in cui i servizi di realtà mista di Azure possono essere usati per migliorare l'esperienza di Ford GT40, ad esempio l'uso di ancoraggi spaziali di Azure per offrire un'esperienza multiutente ancorata nel mondo reale. "Dal punto di vista creativo, gli ancoraggi spaziali di Azure aprono una gamma completamente nuova di possibilità attraverso la possibilità di fornire per eseguire il mapping, rendere permanente e ripristinare il contenuto 3D o i punti di interesse all'interno del mondo fisico", afferma.

Lambert consente anche di eseguire il rendering remoto di Azure o di trasmettere l'app da Azure per ottenere le frequenze dei fotogrammi desiderate mentre si lavora con modelli 3D più dettagliati e complessi. "Abbiamo dovuto implementare shader personalizzati altamente ottimizzati in Unreal per raggiungere la destinazione sul dispositivo di 60 fotogrammi al secondo", spiega. "Con il rendering remoto di Azure, avremmo potuto eseguire molte altre operazioni, in modo molto più semplice, senza la necessità di ottimizzare i modelli poligoni, le mappe di trama e così via."

### <a name="endless-new-possibilities"></a>Nuove possibilità infinite

Quindi, qual è il prossimo passo per il lieto fine? Il feedback di Ford sull'esperienza di Ford GT40 è stato estremamente positivo, ottenendo ulteriori discussioni tra il lieto completamento e Ford nei progetti HoloLens 2 futuri. Al di fuori della sua relazione con Ford, il buon fine sta già iniziando un nuovo progetto in HoloLens 2, in cui il MRTK per Unreal sarà un blocco predefinito di base per la maggior parte dell'esperienza utente. 

"Abbiamo sempre mantenuto un approccio indipendente dalla tecnologia per ogni nuovo progetto, proponendo qualsiasi set di strumenti più adatto per aiutare il client a raggiungere i risultati desiderati", afferma Cheetham. "Detto questo, HoloLens 2 è emerso come lo standard Gold de facto per la realtà mista, specialmente nell'azienda, che precede tutte le altre opzioni in termini di funzionalità del dispositivo e della pervasività dell'ecosistema di supporto".

Secondo Cheetham, la pandemia globale ha alimentato un grande interesse per la realtà mista coinvolgente tra i potenziali clienti. "Siamo sempre più occupati, con circa il 50% dei potenziali client aperti per discutere di un'opzione di realtà mista", afferma. "La chiave consiste nel chiedere agli utenti di provarla. È possibile informarli sulla realtà mista per tutto il giorno, ma quando si passa un HoloLens 2 all'esperienza autonoma, si ottiene immediatamente il modo in cui può essere un cambio di gioco. Il supporto per Unreal Engine in HoloLens 2 aumenta solo il valore che è possibile offrire, consentendo di offrire esperienze visivamente accattivanti che assicurano la soddisfazione anche dei client più esigenti ".

## <a name="try-it-out"></a>Verifica

> [!div class="nextstepaction"]
> [Scaricare l'app Ford GT40](https://www.microsoft.com/p/ford-gt40/9p4vllktfvfp)

Vedere l' [Introduzione allo sviluppo di realtà mista in HoloLens 2](../development.md) o [MRTK per Unreal](https://github.com/microsoft/MixedRealityToolkit-Unreal) su GitHub.

<!-- ## About the team

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Jack Caron" width="60" height="60" src="images/kippys-escape/jack-caron.jpg"></td>
<td style="border-style: none"><b>Jack Caron</b><br><i>Lead Game Designer</i><br>Jack currently works on Mixed Reality experiences for Microsoft, including HoloLens 2 projects and AltspaceVR, and was previously a designer on the HoloLens platform team.</td>
</tr>
</table>

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Summer Wu" width="60" height="60" src="images/kippys-escape/summer-wu.jpg"></td>
<td style="border-style: none"><b>Summer Wu</b><br><i>Producer</i><br>Summer works on the mixed reality developer platform and heads the team’s Unreal Engine related efforts.</td>
</tr>
</table> -->
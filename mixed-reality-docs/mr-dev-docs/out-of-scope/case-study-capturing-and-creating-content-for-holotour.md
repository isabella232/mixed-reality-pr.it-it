---
title: Case study - HoloTour
description: Esplorare l'applicazione HoloTour case study e illustrare il processo di acquisizione e creazione del contenuto.
author: dannyaskew
ms.author: daaske
ms.date: 03/21/2018
ms.topic: article
keywords: HoloTour, HoloLens, Windows Mixed Reality
ms.openlocfilehash: 7e9bc2078e90b0f0cd98cf0612b583c06b2d51b400d682d3aff71e59eed620a4
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115202244"
---
# <a name="case-study---holotour"></a>Case study - HoloTour

HoloTour per Microsoft HoloLens offre tour personali in 3D immersivi di luoghi famosi in tutto il mondo. Come hanno scoperto i progettisti, gli artisti, i produttori, gli audio designer e gli sviluppatori che lavorano a questo progetto, la creazione di un rendering 3D davvero reale di una località nota richiede una combinazione unica di procedure guida creative e tecnologiche. Questa case study il processo di acquisizione e creazione del contenuto usato per HoloTour.

## <a name="the-tech"></a>La tecnologia

Con HoloTour, abbiamo voluto rendere possibile per le persone visitare alcune delle destinazioni più straordinarie del mondo, come le macerie di [Machu Picchu](https://en.wikipedia.org/wiki/Machu_Picchu) in Perù o la [moderna Via Navona](https://en.wikipedia.org/wiki/Piazza_Navona) in Italia, direttamente dai propri living. Il nostro team ha raggiunto l'obiettivo di HoloTour di "far sentire di essere realmente presenti". L'esperienza doveva essere superiore alle immagini o ai video. Sfruttando la tecnologia di visualizzazione, rilevamento e audio univoca HoloLens abbiamo ritenuto di poterti virtualmente traslitterare in un altro luogo. Sarebbe necessario acquisire le viste, i suoni e la geometria tridimensionale di ogni posizione visitata e quindi ricrearla all'interno dell'app.

A tale scopo, era necessario un rig fotocamera a 360° con acquisizione audio direzionale. Era necessario acquisire a una risoluzione estremamente elevata, in modo che il metraggio fosse nitido quando riprodotto su un HoloLens e le fotocamere dovevano essere posizionate insieme per ridurre al minimo gli artefatti di unione. Si vuole una copertura sferica completa, non solo lungo l'orizzonte, ma anche sopra e sotto di te. Il rig doveva anche essere portabile per poterlo portare in tutto il mondo. Abbiamo valutato le opzioni disponibili e ci siamo resi conto che non erano sufficienti per realizzare la nostra visione, sia a causa della risoluzione, del costo o delle dimensioni. Se non fosse possibile trovare un rig di telecamere che soddisfasse le esigenze, sarebbe necessario crearne uno da soli.

### <a name="building-the-rig"></a>Compilazione del rig

La prima versione, fatta di cardboard, Velcro, nastro dotto e 14 fotocamere GoPro, era qualcosa di cui MacGyver sarebbe stato molto fiero. Dopo aver esaminato tutto, dalle soluzioni di fascia bassa ai rig prodotti personalizzati, le fotocamere GoPro sono state l'opzione migliore per noi perché erano piccole, convenienti e avevano un'archiviazione di memoria facile da usare. Il fattore di forma di piccole dimensioni era particolarmente importante perché permetteva di posizionare le fotocamere piuttosto vicine: più piccola è la distanza tra le fotocamere, più piccoli saranno gli artefatti di unione. La disposizione esclusiva della fotocamera ci  ha consentito di ottenere la copertura completa della sfera più una sovrapposizione sufficiente per allineare in modo intelligente le fotocamere e smussare alcuni artefatti durante il processo di unione.

Sfruttare le funzionalità [del](../design/spatial-sound.md) suono spaziale HoloLens fondamentale per creare un'esperienza coinvolgente davvero reale. È stato usato un array a quattro microfoni situato sotto le telecamere sul treppiede, che acquisisce il suono dalla posizione della fotocamera in quattro direzioni, fornendo informazioni sufficienti per creare suoni spaziali nelle scene.

![Il rig di fotocamera a 360° configurato per le riprese all'esterno del Pantheon.](images/camera-pantheon-200px.png)

Il rig di fotocamera a 360° configurato per le riprese all'esterno del Pantheon. 


Abbiamo testato il nostro rig fatto in casa portandolo fino a Rattlesnake Ridge vicino Seattle, acquisendo il panorama nella parte superiore dell'escursione. Il risultato, anche se significativamente meno lucido rispetto alle località che si vedono oggi in HoloTour, ci ha dato la certezza che la progettazione del rig è stata abbastanza buona da far si che ci si senta realmente presenti.

Il rig è stato aggiornato da Velcro e cardboard a un alloggiamento con fotocamera stampato in 3D e sono stati acquistati pacchetti di batteria esterni per le fotocamere GoPro per semplificare la gestione della batteria. È stato quindi fatto un test più approfondito, in viaggio fino a San Francisco per creare un tour in miniatura della costa della città e dell'icona golden gate bridge. Questo rig di fotocamere è quello usato per la maggior parte delle acquisizioni delle località visitate in HoloTour.

![Il rig di fotocamera a 360° che filma in Machu Picchu.](images/camera-machu-pichu-500px.png)

Il rig di fotocamera a 360° che filma in Machu Picchu. 

## <a name="behind-the-scenes"></a>Dietro le quinte

Prima delle riprese, era necessario determinare le località da includere nel tour virtuale. Rome è stata la prima località che si intendeva spedire e abbiamo voluto farlo nel modo giusto, quindi abbiamo deciso di fare un viaggio di esplorazione in anticipo. È stato inviato un team di sei persone, tra cui artisti, designer e produttori, per una visita di persona ai siti che si prendevano in considerazione. Il viaggio ha richiesto circa 9 giorni, 2,5 per il viaggio, il resto per le riprese. (Per Machu Picchu abbiamo scelto di non fare una gita scout, cercando in anticipo e prenotando alcuni giorni di buffer per le riprese).

Mentre si trova a Roma, il team ha scattato foto di ogni area e ha preso in considerazione fatti interessanti e considerazioni pratiche, ad esempio quanto sia difficile recarsi in ogni luogo e quanto sarebbe difficile filmare a causa di crowds o restrizioni. Può sembrare una vacanza, ma è molto lavoro. I giorni sono iniziati nelle prime ore del mattino e non si fermano fino a sera. Ogni notte, i filmati sono stati caricati per il team a Seattle per la revisione. 

![La nostra squadra di acquisizione a Roma.](images/holotour-filming-crew-rome-500px.jpg) 

La nostra squadra di acquisizione a Roma. 


Al termine del viaggio scout, è stato creato un piano finale per le riprese effettive. Questo richiedeva un elenco dettagliato del punto in cui si sarebbe filmato, in quale giorno e a quale ora. Ogni giorno oltreoceano è costoso, quindi questi viaggi dovevano essere efficienti. Abbiamo prenotato guide e gestori a Roma per aiutarci e usare completamente ogni giorno da prima dell'inizio del sole a dopo il tramonto. È necessario ottenere il miglior filmato possibile per avere l'aspetto di essere effettivamente presenti.

### <a name="capturing-the-video"></a>Acquisizione del video

L'esecuzione di alcune operazioni semplici durante l'acquisizione può rendere molto più semplice la post-elaborazione. Ad esempio, ogni volta che si uniscono immagini di più fotocamere, si finisce con artefatti visivi perché ogni fotocamera ha una visualizzazione leggermente diversa. Gli oggetti più vicini sono alla fotocamera, maggiore è la differenza tra le visualizzazioni e più grandi saranno gli artefatti di unione. Ecco un modo semplice per visualizzare il problema: tenere il pollice in alto davanti al viso e guardarlo con un solo occhio. A questo punto, passare gli occhi. Si noti che il cursore viene spostato rispetto allo sfondo. Se si tiene il pollice più lontano dal viso e si ripete l'esperimento, il pollice sembra spostarsi meno. Questo movimento apparente è simile al problema di unione che abbiamo dovuto affrontare: gli occhi, come le fotocamere, non vedono esattamente la stessa immagine perché sono separati da una piccola distanza.

Poiché è molto più facile evitare gli artefatti peggiori durante le riprese rispetto a correggerli durante la post-elaborazione, abbiamo provato a mantenere persone e cose molto distoglie dalla fotocamera nella speranza di poter eliminare la necessità di unire oggetti da vicino. La gestione di un'ampia disaffezione intorno alla fotocamera è stata probabilmente una delle maggiori difficoltà che si verificavano durante le riprese e dovevano essere creativi per renderla più chiara. Lavorare con le guide locali è stato un grande aiuto per la gestione delle persone, ma abbiamo anche scoperto che l'uso di segni, e talvolta piccoli coni o sacchetti di fagiolo, per contrassegnare il nostro spazio di ripresa era ragionevolmente efficace, soprattutto perché era necessario ottenere solo una breve quantità di filmati in ogni posizione. Spesso il modo migliore per ottenere una buona acquisizione era semplicemente arrivare molto presto la mattina, prima che la maggior parte delle persone si presentava.

Alcune altre tecniche di acquisizione utili provengono direttamente dalle tradizionali procedure cinematografiche. Ad esempio, è stata usata una scheda di correzione del colore su tutte le fotocamere e sono state acquisite foto di riferimento di trame e oggetti che potrebbero essere necessarie in un secondo momento. 

![Taglio approssimativo di Machu Picchu che mostra la scheda di correzione del colore.](images/rough-cut-machu-picchu-500px.png)

Un taglio approssimativo del metraggio pantheon prima dell'unione.

### <a name="processing-the-video"></a>Elaborazione del video

L'acquisizione di contenuto a 360° è solo il primo passaggio: è necessaria una grande quantità di elaborazione per convertire il metraggio della fotocamera non elaborato acquisito negli asset finali visualizzati in HoloTour. Una volta tornati a casa, era necessario prendere il video da 14 feed di fotocamera diversi e trasformarlo in un singolo video continuo con artefatti minimi. Il team dell'arte ha usato diversi strumenti per combinare e lucidare il metraggio acquisito ed è stata sviluppata una pipeline per ottimizzare il più possibile l'elaborazione. Il metraggio doveva essere unito, corretto a colori e quindi composito per rimuovere elementi e artefatti distrattivi o aggiungere sacche supplementari di vita e movimento, il tutto con l'obiettivo di migliorare la sensazione di essere effettivamente presenti.

![Un taglio approssimativo del metraggio pantheon prima dell'unione.](images/rough-cut-pantheon-500px.png)

Un taglio approssimativo del metraggio pantheon prima dell'unione. 


Per unire i video, è stato usato uno strumento denominato [PTGui](https://www.ptgui.com/) e integrato nella pipeline di elaborazione. Durante la post-elaborazione sono stati estratti fotogrammi dai video e è stato trovato un modello di unione che era valido per uno di questi fotogrammi. Questo modello è stato quindi applicato a un plug-in personalizzato che ha consentito agli autori di video di ottimizzare e modificare direttamente il modello di unione durante la composizione in After Effects. 

![Screenshot di PTGui che mostra il metraggio Pantheon impunto.](images/stitching-tool-pantheon-500px.png)

Screenshot di PTGui che mostra il metraggio Pantheon impunto. 


### <a name="video-playback"></a>Riproduzione di video

Al termine dell'elaborazione del metraggio, è disponibile un video facile, ma molto grande, con una risoluzione di circa 8.000. La decodifica video è costosa e sono pochi i computer in grado di gestire un video da 8.000. La sfida successiva consisteva nel trovare un modo per riprodurre il video HoloLens. Sono state sviluppate diverse strategie per evitare il costo della decodifica, rendendo l'utente ancora in grado di visualizzare l'intero video.

L'ottimizzazione più semplice è evitare di decodificare parti del video che non cambiano molto. È stato scritto uno strumento per identificare le aree in ogni scena con poco o nessun movimento. Per queste aree viene visualizzata un'immagine statica anziché decodificare un video per ogni fotogramma. Per rendere possibile questo, il video di grandi dimensioni è stato suddiviso in blocchi molto più piccoli.

È stato anche verificato che ogni pixel decodificato fosse usato in modo più efficace. Sono stati sperimentati tecniche di compressione per ridurre le dimensioni del video. le aree video vengono suddivise in base ai poligoni della geometria su cui verrebbe proiettata; Sono stati modificati gli UV e i video sono stati ricompressi in base alla quantità di dettagli inclusi nei diversi poligoni. Il risultato di questo lavoro è che ciò che è iniziato come un singolo video da 8.000 si è trasformato in molti blocchi che sembrano quasi incomprensibili fino a quando non vengono proiettati correttamente nella scena. Per uno sviluppatore di giochi che comprende il mapping delle trame e la creazione di imballamenti UV, questa operazione avrà probabilmente un aspetto familiare. 

![Visualizzazione completa del Pantheon prima delle ottimizzazioni.](images/pantheon-before-optimization-500px.png) 

Visualizzazione completa del Pantheon prima delle ottimizzazioni. 


![Metà destra del Pantheon, elaborata per la riproduzione video.](images/pantheon-process-video-playback-500px.png) 

Metà destra del Pantheon, elaborata per la riproduzione video. 


![Esempio di una singola area video dopo l'ottimizzazione e la creazione di un pacchetto.](images/single-video-region-after-optimization-500px.png) 

Esempio di una singola area video dopo l'ottimizzazione e la creazione di un pacchetto. 


Un altro trucco usato era evitare di decodificare video che non si sta visualizzando attivamente. In HoloTour è possibile visualizzare solo parte della scena completa in un determinato momento. I video vengono decodificati solo all'interno o a breve all'esterno del campo di visualizzazione. Quando si ruota la testa, si iniziano a riprodurre le aree del video che ora si trova nella fov e si arresta la riproduzione di quelle che non sono più al suo interno. La maggior parte delle persone non noterà nemmeno che ciò accade, ma se ci si volta rapidamente, si noterà che il video impiega un secondo per iniziare. Nel frattempo verrà visualizzata un'immagine statica che si dissolve di nuovo in video quando è pronto.

Per far funzionare questa strategia, è stato sviluppato un ampio sistema di riproduzione video. È stato ottimizzato il codice di riproduzione di basso livello per rendere estremamente efficiente il cambio video. Inoltre, è stato necessario codificare i video in modo speciale per rendere possibile il passaggio rapido a qualsiasi video in qualsiasi momento. Questa pipeline di riproduzione ha richiesto una notevole quantità di tempo di sviluppo, quindi è stata implementata in fasi. Abbiamo iniziato con un sistema più semplice che era meno efficiente, ma consentiva a progettisti e autori di lavorare sull'esperienza e lo migliorava lentamente fino a ottenere un sistema di riproduzione più affidabile che consentiva di riusare al livello di qualità finale. Questo sistema finale aveva strumenti personalizzati creati all'interno di Unity per configurare il video all'interno della scena e monitorare il motore di riproduzione.

### <a name="recreating-near-space-objects-in-3d"></a>Ricreazione di oggetti near space in 3D

I video costituiscono la maggior parte di ciò che si vede in HoloTour, ma ci sono diversi oggetti 3D che appaiono vicino all'utente, ad esempio il disegno in Navona, il cane fuori dal Pantheon o il fumetto ad aria calda che si trova per le scene aeree. Questi oggetti 3D sono importanti perché la percezione della profondità umana è molto buona da vicino, ma non molto buona da lontano. È possibile uscire con i video in distanza, ma per consentire agli utenti di spostarsi nello spazio e avere l'aspetto di essere effettivamente presenti, gli oggetti vicini necessitano di profondità. Questa tecnica è simile al tipo di cosa che si può vedere in una storia naturale, ovvero si immagini un diorama con piante e animali fisici in primo piano, ma che si ricade in un disegno opaco mascherato in background.

Alcuni oggetti sono semplicemente asset 3D creati e aggiunti alla scena per migliorare l'esperienza. Il disegno e il fumetto dell'aria calda rientrano in questa categoria perché non erano presenti quando abbiamo filmato. Analogamente agli asset di gioco, sono stati creati da un artista 3D del nostro team e strutturati in modo appropriato. Questi elementi vengono posizionati nelle scene vicino alla posizione in cui ci si trova e il motore di gioco può eseguirne il rendering nei due schermi HoloLens in modo che vengano visualizzati come oggetto 3D.

Altri asset, ad esempio l'oggetto esterno a Pantheon, sono oggetti reali che esistono nelle posizioni in cui vengono ripresi i video, ma per portare questi oggetti fuori dal video e in 3D, è necessario eseguire una serie di operazioni.

Prima di tutto, sono necessarie informazioni aggiuntive su ogni oggetto. Mentre si è sul posto per le registrazioni, il team ha acquisito molti film di riferimento di questi oggetti in modo da avere immagini sufficientemente dettagliate da ricreare accuratamente le trame. Il team ha anche eseguito una [scansione](https://en.wikipedia.org/wiki/Photogrammetry) fotogrammetria, che costruisce un modello 3D da decine di immagini 2D, offrendo un modello approssimativo dell'oggetto in scala perfetta.

Durante l'elaborazione del filmato, gli oggetti che verranno successivamente sostituiti con una rappresentazione 3D vengono rimossi dal video. L'asset 3D è basato sul modello di fotogrammetria, ma è stato pulito e semplificato dagli autori. Per alcuni oggetti, è possibile usare parti del video, ad esempio la trama dell'acqua, ma la maggior parte del tempo è ora un oggetto 3D, che consente agli utenti di percepire la profondità e di aggirarlo in uno spazio limitato dell'esperienza. La presenza di oggetti vicini allo spazio come questo aumenta notevolmente il senso di autofino e aiuta a conferire le basi agli utenti nella posizione virtuale. 

![Pantheon metraggio con l'emisezione rimossa. Verrà sostituito con un asset 3D.](images/object-removal-pantheon-500px.png)

Pantheon metraggio con l'emisezione rimossa. Verrà sostituito con un asset 3D.


## <a name="final-thoughts"></a>Considerazioni finali

Ovviamente, la creazione di questo contenuto è stata molto più importante di quanto illustrato qui. Ci sono alcune scene, che sono state chiamate "prospettive impossibili", tra cui la corsa in mongolfiera e il viaggio in taxi nel Periodoeum, che ha avuto un approccio più creative. Queste informazioni verranno trattate in un case study.

Ci auguriamo che la condivisione di soluzioni ad alcune delle principali sfide che si sono verificate durante la produzione sia utile per altri sviluppatori e che si sia istinti a usare alcune di queste tecniche per creare esperienze immersive personalizzate per HoloLens. In caso contrario, assicurarsi di condividerlo con Microsoft nel forum sullo HoloLens di sviluppo [di app.](https://forums.hololens.com/)

## <a name="about-the-authors"></a>Informazioni sugli autori

<table style="border:0">
<tr>
<td style="border:0" width="60px"> <img alt="David Haley" width="60" height="60" src="images/haley.png" /></td>
<td style="border:0" width="408"> <b>David Haley è</b> uno sviluppatore senior che ha appreso di più sui dispositivi di videocamera e sulla riproduzione di video rispetto a quanto ritenuto possibile dall'uso di HoloTour.</td>
<td style="border:0" width="60px"> <img alt="Danny Askew" width="60" height="60" src="images/askew.png" /></td>
<td style="border:0" width="408"> <b>Massimo Askew</b> è un video artista che si è assicurata che il viaggio attraverso Rome sia stato il più possibile perfetto.</td>
</tr>
<tr>
<td style="border:0" width="60px"> <img alt="Jason Syltebo" width="60" height="60" src="images/syltebo.png" /></td>
<td style="border:0" width="408"> <b>Jason Syltebo</b> è un audio designer che ha verificato di poter sperimentare il soundscape di ogni destinazione visitata, anche quando si torna indietro nel tempo.</td>
<td style="border:0" width="60px"> <img alt="Travis Steiner" width="60" height="60" src="images/steiner.png" /></td>
<td style="border:0" width="408"> <b>Travis Scherer è</b> un design director che ha ricercato e esplorato posizioni, creato piani di viaggio e diretto film sul sito.</td>
</tr>
</table>



## <a name="see-also"></a>Vedi anche
* [Video: Microsoft HoloLens: HoloTour](https://www.youtube.com/watch?v=pLd9WPlaMpY)

---
title: Creazione di Galaxy Explorer per HoloLens 2
description: Informazioni su come il team sta aggiornando il progetto open source di Galaxy Explorer per HoloLens 2 in GitHub.
author: l-garrett
ms.author: grbury
ms.date: 06/30/2019
ms.topic: article
keywords: galaxy explorer, case study, project, sample, MRTK, Mixed Reality Toolkit, Unity, app di esempio, app di esempio, open source, Microsoft Store, HoloLens, visore per realtà mista, visore windows mixed reality, visore per realtà virtuale
ms.openlocfilehash: c3d9c6da13446816f3fd75f83e5a9088661c9604ef4d86ea805202f538d395b5
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115200505"
---
# <a name="the-making-of-galaxy-explorer-for-hololens-2"></a>Creazione di Galaxy Explorer per HoloLens 2

![Nuovo logo di Galaxy Explorer](../images/GalaxyExplorer2.jpg)


Benvenuti nell'applicazione Galaxy Explorer aggiornata per HoloLens 2! [Galaxy Explorer](/windows/mixed-reality/galaxy-explorer "Galaxy Explorer") è stato originariamente sviluppato come applicazione open source per HoloLens (prima generazione) tramite il programma Condividi la tua idea ed è una delle prime esperienze di realtà mista che molte persone hanno avuto. A questo punto lo stiamo aggiornando per le [nuove e interessanti funzionalità di HoloLens 2](https://www.microsoft.com/hololens/hardware).

In qualità di microsoft [Mixed Reality Studios,](galaxy-explorer-update.md#mixed-reality-studios)in genere sviluppiamo soluzioni di livello commerciale e stiamo sviluppando test & sulle piattaforme di destinazione durante il processo di creazione e sviluppo. Il progetto verrà avviato usando i framework e gli strumenti (ad esempio [MRTK)](mrtk-getting-started.md)quando saranno disponibili per noi e per la community.

Proprio come l'originale Galaxy Explorer, il [team](galaxy-explorer-update.md#meet-the-team) sarà aperto per approvvigionamento del progetto GitHub garantire che la community abbia accesso completo. [](https://github.com/Microsoft/GalaxyExplorer) Il nostro percorso verrà documentato anche in modo trasparente su come è stato possibile eseguire il porting da MRTK v1 a MRTK v2, migliorare l'esperienza con le nuove funzionalità disponibili in HoloLens 2 e garantire che Galaxy Explorer sia rimasto un'esperienza multipiattaforma. Indipendentemente dal fatto che si visualizzi Galaxy Explorer in HoloLens (prima generazione), HoloLens 2, visore Windows Mixed Reality o sul desktop Windows 10, microsoft vuole assicurarsi che il percorso sia così come lo siamo.

Questa pagina verrà espansa durante l'avanzamento del progetto con collegamenti ad articoli più dettagliati, codice, artefatti di progettazione e documentazione aggiuntiva di MRTK per offrire un'analisi del progetto da parte degli addetti ai lavori.

## <a name="download-app-from-microsoft-store-in-hololens-2"></a>Scaricare l'app Microsoft Store in HoloLens 2
Se si dispone di HoloLens 2, è possibile scaricare e installare direttamente l'app nel dispositivo.

<a href='//www.microsoft.com/store/apps/9nblggh4q4jg?cid=storebadge&ocid=badge'><img src='https://developer.microsoft.com/store/badges/images/English_get-it-from-MS.png' alt='English badge' width="284px" height="104px" style='width: 284px; height: 104px;'/></a>

## <a name="thinking-about-interactions"></a>Pensare alle interazioni

In quanto creative studio, il privilegio di convertire Galaxy Explorer in HoloLens 2. Si è già detto che l'esperienza era una ricorrenza per il nuovo dispositivo e per dimostrare che l'empowerment della realtà mista è limitato solo dall'immaginazione.

HoloLens 2 consente agli utenti di toccare, afferrare e spostare gli ologrammi in modo naturale: rispondono molto come gli oggetti reali. I modelli a mano completamente articolati sono straordinari, perché consentono agli utenti di fare ciò che sembra naturale. Ad esempio, ognuno prende una tazza in modo leggermente diverso e invece di usare un modo specifico per farlo, HoloLens 2 consente di farlo a modo suo.

>[!VIDEO https://www.youtube.com/embed/wogJv5v9x-s]

Si tratta di una modifica significativa rispetto alle interfacce basate su Air Tap nei dispositivi HoloLens di prima generazione. Invece di interagire con gli ologrammi da lontano, gli utenti possono ora ottenere "da vicino e personali". Quando si esegue il porting di esperienze esistenti HoloLens 2 o si pianificano nuove esperienze, è importante acquisire familiarità con la manipolazione diretta degli ologrammi.

### <a name="direct-manipulation-vs-the-vast-distances-in-space"></a>Manipolazione diretta rispetto alle ampie distanze nello spazio

È un'esperienza magica per raggiungere, afferrare un pianeta e tenerlo in mano. La sfida di questo approccio è la dimensione del sistema solare, che è enorme. L'utente avrebbe bisogno di aggirare la propria stanza per avvicinarsi a ogni pianeta per interagire con esso.

Per consentire agli utenti di interagire con oggetti più remoti, MRTK offre raggi della mano che si estrarranno dal centro del palmo dell'utente, fungendo da estensione della mano. Un cursore a forma di ciambella viene collegato alla fine del raggio per indicare dove il raggio si interseca con un oggetto di destinazione. L'oggetto su cui si posa il cursore può quindi ricevere i comandi gestuali dalla mano. 

>[!VIDEO https://www.youtube.com/embed/Qol5OFNfN14]

Nella versione originale di Galaxy Explorer, l'utente avrebbe mirato a un pianeta con il cursore dello sguardo e quindi al tocco dell'aria per chiamarlo più vicino. Il modo più semplice per convertire l'esperienza HoloLens 2 è adottare questo comportamento e usare i raggi della mano per selezionare i pianeti. Anche se questo era funzionale, ci ha lasciato desiderare di più.

### <a name="back-to-the-drawing-board"></a>Ripartiamo da zero

Ci siamo riuniti per ideare cosa si potrebbe creare in base alle interazioni esistenti. Il modo di pensare era: sebbene HoloLens 2 gli utenti di interagire con gli ologrammi in modo naturale e realistico, gli ologrammi non sono per definizione reali. Quindi, purché un'interazione sia plausibile per l'utente, non importa se l'interazione sarebbe possibile con un oggetto reale o meno, ma è possibile renderla possibile.

Un concetto che è stato esplorato era basato sulla telekinesi, il potere di manipolare gli oggetti con la mente. Spesso visto nei film con supereroi, una persona raggiungeva con la mente e chiamava un oggetto nella mano aperta. L'idea è stata illustrata in modo più semplice ed è stato fornito un rapido sketch del funzionamento del concetto.

![Concetto per l'interazione di afferrare la forza](images/ge-update-interactions-concept-force-grab.png)

L'utente punta il raggio della mano su un pianeta, che fornisce un feedback di destinazione. Man mano che l'utente estende la mano aperta, il pianeta viene trascinato verso l'utente da una forza magica fino a quando non è abbastanza vicino da afferrarlo. Di conseguenza, il nome dell'interazione è force grab. Man mano che l'utente allontanava il pianeta con la mano aperta, tornava di nuovo in orbita.

### <a name="force-grab-prototyping"></a>Prototipazione di afferramento forzato

Sono stati quindi creati più prototipi per testare il concetto: Come si verifica l'interazione nel complesso? L'oggetto chiamato deve arrestarsi davanti all'utente o restare in mano fino a quando non viene posizionato? L'oggetto chiamato deve modificare le dimensioni o la scala durante la chiamata?

<!--
Here is Amit Rojtblat (Technical Artist) presenting one of the prototypes to Yasushi Zonno (Creative Lead).

------------------------------------------------------------------

__*--- VIDEO OF AMIT PLAYING AND EXPLAINING THE PROTOTYPE ---*__

__*--- NEEDS TO BE UPLOADED (TO YOUTUBE?) AND LINKED ---*__

------------------------------------------------------------------
-->

### <a name="implementing-force-grab-into-the-application"></a>Implementazione dell'agguato forzato nell'applicazione

Quando abbiamo provato a afferrare la forza sui pianeti, ci siamo resi conto che era necessario modificare la scala del sistema solare. Si è scoperto che una rappresentazione accurata e di medie dimensioni del sistema solare è difficile da comprendere e navigare per gli utenti. Non sanno dove cercare. Tuttavia, una rappresentazione di piccole dimensioni ha reso alcuni pianeti troppo piccoli per essere facilmente selezionati. Di conseguenza, le dimensioni dei pianeti e la spaziatura tra oggetti solari sono state progettate per essere a proprio agio all'interno di una stanza di medie dimensioni mantenendo la relativa accuratezza.

Durante le fasi successive dello sprint di sviluppo, abbiamo avuto la fortuna di avere altri esperti di MSFT Mixed Reality all'interno, quindi abbiamo dovuto lavorare per ottenere il loro input come tester esperti ed eseguire iterazioni rapide sull'interazione di afferrare la forza.

![Test di Una build di anteprima di Galaxy Explorer](images/ge-update-user-testing.png)

Nell'immagine: Jenny Kam, Senior Design Lead, che testa un work-in-progress di Galaxy Explorer.

### <a name="adding-affordances-for-targeting"></a>Aggiunta di affordance per la destinazione

Come abbiamo fatto HoloLens 2, abbiamo scoperto che, anche se le nuove interazioni sono naturali e intuitive, gli ologrammi rimangono invariati: senza alcun peso o esperienze tattili. Poiché gli ologrammi non forniscono feedback naturali che gli esseri umani ricevono quando interagiscono con gli oggetti, è necessario crearli.

Abbiamo pensato al feedback visivo e audio che gli utenti sarebbero stati forniti per le varie fasi delle interazioni e poiché il meccanismo di afferramento della forza è fondamentale per interagire con Galaxy Explorer, sono stati eseguate molte iterazioni. L'obiettivo era trovare il giusto equilibrio tra feedback audio e visivo per ogni fase dell'interazione: concentrarsi sull'oggetto desiderato, chiamarlo all'utente e quindi rilasciarlo. Si è appreso che per rafforzare l'interazione era necessario un maggior feedback audio e visivo rispetto a quello usato per la HoloLens (prima generazione).

![Convenienze visive sui pianeti](images/ge-update-planet-affordances.png)

### <a name="adding-affordances-for-force-grab"></a>Aggiunta di affordance per il force grab
 
Dopo aver avuto il meccanismo di afferramento della forza di base con l'audio e gli affordance visivi, abbiamo esaminato come rendere più semplice la selezione dei pianeti. C'erano due aspetti principali da affrontare: poiché il sistema solare è un'interfaccia mobile 3D, gli utenti possono imparare a scegliere gli oggetti in modo coerente. Ciò è stato complicato dal fatto che il raggio della mano è veloce nella selezione di un oggetto, rendendo i pianeti che si spostano verso l'utente in modo estremamente rapido.

L'approccio è stato fatto con una soluzione a tre livelli. Il primo è stato abbastanza intuitivo: rallentare il processo di selezione in modo che i pianeti si avvicinino all'utente a un ritmo più naturale. Dopo aver regolato la velocità, è stato necessario rivedere gli affordance audio e visivi, aggiungendo feedback audio quando il pianeta è stato tracciato verso l'utente.

La seconda parte della soluzione consisteva nel rendere tangibile la visualizzazione dell'intera interazione di afferrare la forza. È stata visualizzata una linea di spessore che si sposta verso l'oggetto di destinazione quando il raggio della mano si connette a esso e quindi riporta l'oggetto all'utente, come un lazo. 

![Affordance "lasso" visivi per l'agguato forzato](images/ge-update-lasso-affordances.png)

Infine, è stata ottimizzata la scala del sistema solare in modo che i pianeti fossero sufficientemente grandi da poter essere mirati dal raggio della mano e dello sguardo dell'utente. 

Questi tre miglioramenti hanno consentito agli utenti di effettuare selezioni accurate, chiamandoli in modo intuitivo. In generale, l'effetto dell'afferrare la forza finale è un'esperienza più coinvolgente e interattiva nel sistema solare.

## <a name="spotlight-on-jupiter"></a>Spotlight su Giove

La creazione dei corpi solari della Via Lattea è stata un'esperienza molto semplice. In particolare, le caratteristiche univoche di Giove lo rendono un punto di vista da vedere. È il più grande e colorato dei gassosi e contiene più massa di tutti gli altri pianeti combinati. Le sue dimensioni e le sue bande ipnotizzanti di turbolenze e dinamiche cloud sono prefetto per un'attenzione particolare all'arte.

### <a name="geometry-and-meshes"></a>Geometria e mesh

Come un gassoso, i gusci esterni di Giove sono costituiti da livelli gassosi. La combinazione della velocità di rotazione rapida, dello scambio di calore interno e delle forze Coriolis crea livelli colorati e flussi che si formano in vortici e nastri nuvolosi. La creazione del sistema solare è stata fondamentale per l'acquisizione di questa straordinaria natura.

È stato subito chiaro che l'uso di tecniche di visualizzazione come simulazioni fluide e trame animate con flussi pre-ricalcolati non era in discussione. La potenza di calcolo necessaria per simulare questa situazione in combinazione con tutto il resto che accade contemporaneamente avrebbe avuto un impatto negativo significativo sulle prestazioni. 

![Panoramica dell'oggetto Jupiter](images/ge-update-jupiter-shells-complete.jpg)

L'approccio successivo era una soluzione "smoke-and-mirror", costituita dalla sovrapposizione di livelli di trama trasparenti, ognuno dei quali affrontava un aspetto specifico del movimento atmosferico, compilato su una composizione di mesh rotanti.

Nell'immagine seguente è possibile visualizzare la shell interna a sinistra. Questo livello mat ha fornito uno sfondo alla composizione per proteggersi da eventuali piccoli gap tra i più livelli che hanno costituito le nuvole. A causa della rotazione lenta del livello, è stato anche utilizzato come buffer visivo tra le bande in movimento più veloci per contribuire a creare l'unità visiva in tutti i livelli.

Dopo aver impostato questo ancoraggio sul modello, i livelli cloud in movimento sono stati proiettati sulle mesh centrale e destra visualizzate di seguito.

![Panoramica dell'oggetto Jupiter con shell separate](images/ge-update-jupiter-shells-separated.jpg)

### <a name="texturing"></a>Texturing

La trama esistente è stata separata in un atero di trame in tre parti: il terzo superiore ospita un livello di cloud senza movimento con lacune per fornire un effetto parallassa, la sezione centrale contiene i flussi esterni in rapido movimento e il terzo inferiore contiene un livello di base interno a rotazione lenta.

La caratteristica Great Red Spot è stata anche separata nelle varie parti in movimento e quindi inserita in un'area altrimenti invisibile della trama. Questi componenti possono essere visti come speckle con tono rosso nella sezione centrale dell'immagine seguente.

Poiché ogni banda ha una direzione e una velocità specifiche, la trama è stata applicata a ogni mesh singolarmente. Le mesh hanno quindi un centro e un punto pivot comuni, che hanno reso possibile animare concentricamente l'intera superficie.

![Panoramica delle trame di Giove](images/ge-update-jupiter-planet-cloud-texture.png)

### <a name="rotation-and-texture-behavior"></a>Comportamento di rotazione e trama

Dopo aver impostato la composizione visiva di Giove, è necessario assicurarsi che le velocità di rotazione e orbita siano state calcolate e applicate di conseguenza. Per completare una rotazione completa, Giove impiega circa 9 ore. Si tratta di una questione di definizione dovuta alla rotazione differenziale. Il flusso equatoriale è stato quindi impostato come "flusso master", prendendo 3600 fotogrammi per una rotazione completa. Ogni altro livello deve avere una velocità di rotazione come fattore 3600 per corrispondere alla posizione iniziale, consentendo, ad esempio, 600, 900, 1200, 1800 e così via.

![Trame della shell di Jupiter](images/ge-update-shell-texture.jpg)


### <a name="the-great-red-spot"></a>Il grande punto rosso

I flussi che ruotano singolarmente hanno fornito un'ottima impressione visiva, ma mancavano nei dettagli quando osservati a distanza ravvicinata.

La parte più accattivante è stata great red spot di Jupiter, quindi è stato creato un set di mesh e trame appositamente per presentarlo.
 
È stato usato un meccanismo simile a quello delle bande di Giove: un set di parti rotanti è stato composto uno sopra l'altro, ma anche raggruppato sotto il "livello master" per assicurarsi che rimangano in posizione indipendentemente dalla velocità di spostamento del resto.

Quando le mesh sono state impostate e posizionate, sono stati applicati diversi livelli del vortice tempestoso e ogni disco è stato animato singolarmente, i pezzi al centro si spostano più velocemente, mentre il resto rallenta progressivamente mentre si sposta verso l'esterno.

![Jupiter Great Red Spot Mesh](images/ge-update-great-red-spot-mesh.jpg)

La composizione ha anche lo stesso pivot di tutte le altre mesh, mantenendo anche l'inclinazione rispetto all'asse y originale (!) per consentire la libertà di animare la rotazione. 3600 fotogrammi è la frequenza di base, con ogni livello che ha un fattore di questo tipo come periodo di rotazione.

![Trama di Jupiter Great Red Spot](images/ge-update-red-spot-mesh-texture.jpg)

### <a name="getting-it-right-in-unity"></a>Come farlo in Unity

Quando si implementa questa funzionalità in Unity, è necessario tenere presenti alcuni aspetti chiave.

Unity è facilmente confuso quando si gestiscono grandi set di livelli trasparenti. La soluzione consisteva nel duplicare il materiale della trama per ogni mesh e applicare progressivamente i valori della coda di rendering crescente dall'interno all'esterno di 5 a ogni materiale.

Il risultato è che la shell interna ha un valore della coda di rendering pari a 3000 (impostazione predefinita), l'esterno statico con tono rosso in un secondo momento ha un valore pari a 3005, i cloud esterni bianchi veloci hanno 3010. Great Red Spot (che avanza dal livello interno a quello esterno), ha terminato con un valore di 3025 in questo modello.

![Oggetto finale di Giove](images/ge-update-jupiter-final.jpg)

### <a name="final-touches"></a>Passaggi finali

I livelli di Giove con trama sono stati impostati all'inizio, che si sono rivelati insufficienti per l'implementazione.

Lo shader Planet Standard originale e tutte le relative variazioni ricevono le informazioni di illuminazione tramite uno script, SunLightReceiver, che non è supportato dallo shader MRTK Standard.

Il semplice scambio degli shader non era una soluzione perché lo shader Planet Standard non supporta le mappe trame con trasparenze. Questo shader è stato modificato per fare in modo che la compilazione di Jupiter funzioni come previsto.

Infine, è necessario configurare Alpha Blend impostando Source Blend su 10 e Destination Blend su 5.

![Proprietà di Jupiter Unity](images/ge-update-jupiter-unity-render-queue.jpg)

È possibile visualizzare il rendering finale di Giove in Galaxy Explorer.

## <a name="meet-the-team"></a>Presentazione del team 

Il team di Mixed Reality Studio è costituito da designer, artisti 3D, specialisti dell'esperienza utente, sviluppatori, program manager e un responsabile di studio. Siamo provenienti da tutto il mondo: Belgio, Canada, Germania, Israele, Giappone, Regno Unito e Stati Uniti. Siamo un team multidisciplinare che proviene da un background diversificato: giochi tradizionali e indipendenti, marketing digitale, sanità e scienza.

Siamo entusiasti di creare Galaxy Explorer per HoloLens 2 e di aggiornare le versioni HoloLens (prima generazione), VR e desktop. 

![Il team di Galaxy Explorer](images/ge-update-team-image.png)

In alto da sinistra a destra: Artemis Tsouflidou (Developer), Angie Teickner (Visual Designer), David Janer (UX Designer), Laura Garrett (Delivery & Production Lead), Yasushi Zonno (Creative Lead), Eline Ledent (Developer) e Ben Turner (Sr. Developer).
In basso da sinistra a destra: Amit Rojtblat (Technical Artist), Martin Wettig (3D Artist) e Dirk Songuer (Studio Head).
Non in primo piano: Tim Gerken (Tech Lead) e Oscar Salandin (Visual Designer).

## <a name="additional-information"></a>Informazioni aggiuntive

### <a name="mixed-reality-studios"></a>Mixed Reality Studios

I team di Microsoft Mixed Reality Studio, che si trovano nelle Americhe, in Europa e Asia-Pacific, sono esperti di progettazione dell'esperienza utente, calcolo olografico, tecnologie AR/VR e sviluppo 3D; tra cui la creazione di asset 3D, DirectX, Unity e Unreal. Microsoft consente di immaginare i futuri desiderati, progettare, creare e distribuire soluzioni, consentendo al contempo ai clienti di creare un impatto misurabile nell'intera organizzazione. Gli studi collaborano strettamente con oltre 22.000 professionisti dei servizi Microsoft per l'integrazione, l'adozione, le operazioni e il supporto delle applicazioni aziendali.
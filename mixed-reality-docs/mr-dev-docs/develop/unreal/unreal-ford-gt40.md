---
title: Esperienza Ford GT40
description: Segui la procedura per esplorare la creazione dell'applicazione di realtà mista Ford GT40 con MRTK per HoloLens 2 in Unreal.
author: hferrone
ms.author: v-hferrone
ms.date: 3/23/2021
ms.topic: article
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, realtà mista, distribuzione nel dispositivo, PC, documentazione, visore VR di realtà mista, visore VR windows mixed reality, visore VR di realtà virtuale
appliesto:
- HoloLens 2
ms.openlocfilehash: 17314cca69148e73ee11fcd4cdc5359a5dbae4cf84b609bafb6cc75d477ec26f
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/05/2021
ms.locfileid: "115200617"
---
# <a name="the-making-of-the-ford-gt40-experience"></a>Creazione dell'esperienza Ford GT40
![Immagine del hero Ford GT40](images/ford-gt40-hero_1920.jpg)

*"Pre-MRTK, lo sviluppo per HoloLens 2 con Unreal è stato un po' noioso perché tutte le interazioni spaziali dovevano essere codificate manualmente, in C++. MrTK per Unreal ha reso semplici molte di queste stesse attività. La stima ha dimeato il tempo necessario per il prototipo iniziale."* - Jose Rodriguez, Software Developer

*"L'esperienza Ford GT40 è la prova che un'app HoloLens 2 ad alta fedeltà può essere completata in pochi mesi, con un budget limitato, ma continua a offrire risultati di grande impatto".*  - Daniel Cheetham, Chief Innovation Officer, Happy Finish

Usando Mixed Reality Toolkit (MRTK) per Unreal, l'azienda di produzione creative Happy Finish ha fornito un'esperienza di HoloLens 2 che offre una prospettiva nuova su Ford GT40, l'auto da corsa che ha insediato Il Mio alle 24 ore di Le Mans.

Usando un'ampia gamma di interazioni spaziali naturali e intuitive, gli utenti possono esplorare la straordinaria, le prestazioni e l'ingegneria della GT40, il tutto offerto in modo da sfruttare l'elevata fedeltà visiva fornita da Unreal Engine. Lo sviluppo di software per l'intero progetto è stato completato da un singolo sviluppatore in meno di tre mesi, reso possibile da MRTK per l'ambiente di progettazione e scripting visivo di Unreal.

## <a name="download-app-from-microsoft-store-in-hololens-2"></a>Scaricare l'app Microsoft Store in HoloLens 2
Se si dispone HoloLens 2 dispositivo, è possibile scaricare e installare direttamente l'app nel dispositivo.

<a href='//www.microsoft.com/store/apps/9p4vllktfvfp?cid=storebadge&ocid=badge'><img src='https://developer.microsoft.com/store/badges/images/English_get-it-from-MS.png' alt='English badge' width="284px" height="104px" style='width: 284px; height: 104px;'/></a>


## <a name="the-ask"></a>La richiesta

Happy Finish è una delle principali società di produzione creative del mondo, con una base di clienti che include, ford, Microsoft,Fone, Netflix, Vodafone e altri nomi di famiglie. L'azienda ha avviato l'azienda come agenzia di alto livello per il recupero di foto e si è diramata in film e CGI prima di estendersi all'eccellenza nella narrazione immersiva con la progettazione spaziale 3D e l'interazione.

A metà del 2020, Microsoft si avvicina a Happy Finish per produrre un'app demo che può illustrare le possibilità abilitate dal nuovo Mixed Reality Toolkit (MRTK) per Unreal, che si basa sul supporto per HoloLens 2 nel motore Unreal. A questo punto, l'azienda aveva già due progetti Unreal-on-HoloLens 2 riusciti. Entrambi erano per un marchio di consumo riconosciuto a livello globale, che ha scelto Unreal su HoloLens 2 per uno strumento di vendita R&D/B2B interno per la sua elevata fedeltà visiva, come richiesto per presentare al meglio i prodotti di fascia alta del cliente.

Anche se la soluzione stessa sarebbe stata lasciata a Happy Finish, doveva soddisfare alcune linee guida chiave. In primo luogo, è stato necessario concentrarsi su uno scenario aziendale per illustrare l'utilità di Unreal HoloLens 2 al di fuori del settore dei giochi. In secondo momento, doveva essere solo dispositivo, vale a dire che poteva essere utilizzato come demo autonoma, senza richiedere una connessione di rete e una potenza di elaborazione esterna per ottenere la frequenza dei fotogrammi di destinazione e la qualità visiva. In terzo piano, deve unire la gamma di interazioni intuitive supportate da MRTK in un'esperienza naturale e senza problemi. Infine, la soluzione proposta deve presentare la fedeltà visiva intrinseca e altri vantaggi del motore Unreal stesso, ad esempio l'efficienza degli shader. 

In base a queste linee guida, Happy Finish ha iniziato a creare un'idea per un'esperienza di realtà mista che usava l'interazione spaziale per comunicare il valore di un prodotto di alto valore. Dopo aver considerato una gamma di oggetti che includeva orologi, fotocamere, automobili e jet privati, Happy Finish alla fine ha deciso sulla Ford GT40, una legenda del settore che ha raggiunto la notorietà nel 1966 quando Ford ha gonfiato Le Mans alle 24 ore, come illustrato nel film blockbuster forbuster del 2019 Ford vs . 

Dopo aver ottenuto il buy-in da Ford, un cliente Happy Finish esistente, l'azienda si è imposta per offrire una nuova prospettiva sull'icona classica del settore automobilistico.

## <a name="the-solution"></a>Soluzione

Il lavoro è iniziato il 7 maggio 2020. Dopo aver ottenuto i file di modello GT40, un artista 3D ha dedicato tre settimane all'ottimizzazione dei modelli poligoni, al mapping UV, al ridisegno delle mappe delle trame e alla condensazione di tali mappe in un numero ridotto di trame. Un artista tecnico ha lavorato in parallelo per eseguire il benchmark dell'output dell'artista 3D, determinare le dimensioni ottimali della trama in base alle frequenze dei fotogrammi di destinazione e individuare il modo migliore per applicare shader personalizzati in Unreal. Tutte queste operazioni di pre-produzione sono stati eseguite per ottimizzare l'esperienza sul dispositivo.

Il direttore creative Alex Lambert è stato inserito nell'immagine al termine del lavoro di pre-produzione. Ha iniziato guardando Ford vs. In questo caso, ha pensato a come riunire una narrazione sugli scenari e sulle interazioni. Ha raccolto anche riferimenti visivi per l'artista dell'interfaccia utente, ad esempio immagini del dashboard GT40 e oggetti visivi del racetrack di Le Mans, e ha raccolto le registrazioni audio della GT40 in azione per sound designer.

Con le risorse di preproduzione definite e ottimizzate per la narrazione, lo sviluppatore di software indipendente Jose Rodriguez è stato insediato per riunire tutto. Rodriguez era stato lo sviluppatore dei due progetti Unreal-on-HoloLens 2 precedenti e completati da Happy Finish, prima del rilascio di MRTK per Unreal.

Il valore fornito da MRTK per Unreal è diventato evidente fin dall'inizio, consentendo a Rodriguez di distribuire un prototipo iniziale in una settimana. Ha implementato tre scenari univoci, uno per ognuno degli aspetti chiave della GT40 identificata da Lambert: la sua testa, le sue prestazioni e la sua progettazione. Per ogni scenario, Rodriguez ha usato MRTK per integrare gli asset 3D ottimizzati dalla fase di preproduzione in una gamma di interazioni spaziali. 

Con MRTK per Unreal, Rodriguez ha creato ogni scenario usando l'oggetto visivo Unreal Motion Graphics (UMG) UI Designer invece di dover implementare tutto in C++. [UX Tools per Unreal,](https://www.unrealengine.com/marketplace/product/mixed-reality-ux-tools)il plug-in che contiene componenti e blocchi predefiniti dell'esperienza utente all'interno di MRTK, gli ha fornito [Unreal Blueprints](https://docs.unrealengine.com/ProgrammingAndScripting/Blueprints/index.html) per la simulazione dell'input, la creazione di script visivi per le interazioni con la mano, i pulsanti a pressione, la manipolazione delle immagini 3D, il magnetismo della superficie e altro ancora, il tutto all'interno di un ambiente di progettazione senza codice e trascinamento della selezione.

"Pre-MRTK, lo sviluppo per HoloLens 2 con Unreal è stato un po' noioso perché tutte le interazioni spaziali dovevano essere codificate manualmente, in C++", afferma Rodriguez. "MrTK per Unreal ha reso semplici molte di queste stesse attività. La stima ha dimeato il tempo necessario per il prototipo iniziale."

Con un prototipo a disposizione, il team ha iniziato a eseguire iterazioni settimanali per perfezionare l'esperienza. "Questo è il momento in cui la Acquisizione realtà mista e la Windows Portale di dispositivi sono diventate molto utili", ricorda Lambert. "Li ho usati per acquisire le revisioni di progettazione, trasmettere il mio feedback ad altri utenti e collaborare alle modifiche. Lavorare in isolamento in questo modo sarebbe stato impossibile senza tali strumenti."

![App Ford GT40 dell'editor Unreal in esecuzione con componenti wheel disposti in sequenza](images/ford-gt40-img-04.JPG)

Quando Lambert ha richiesto modifiche, ad esempio il riposizionamento degli elementi dell'interfaccia utente o la modifica del comportamento di un pulsante, Rodriguez li ha implementati. Mentre alcune delle modifiche richiedevano piccole modifiche al codice, la maggior parte di esse era gestita nella finestra di progettazione visiva Unreal. "Sono rimasto sorvolato dalla velocità con cui ho potuto eseguire l'iterazione", afferma Rodriguez. "Nessun tempo è stato sprecato; Apportare una modifica nella finestra di progettazione e quindi premere riproduci per visualizzarla immediatamente sul dispositivo. MrTK ha semplificato il lavoro".

Rodriguez ricorda anche di essere com'era pronto per la produzione tutti gli strumenti di sviluppo. "Abbiamo procedeto senza problemi dal prototipo iniziale alla produzione finale, senza dover tornare indietro e reimplementare o ottimizzare gli elementi nel codice", afferma.  

## <a name="the-final-build"></a>Compilazione finale

Happy Finish ha completato la produzione dell'esperienza Ford GT40 per HoloLens 2 il 28 luglio 2020, offrendo una nuova prospettiva sull'auto da corsa. L'esperienza inizia con una schermata iniziale, quindi guida l'utente a configurare un ancoraggio afferrando il logo Ford e posizionarlo su una superficie piana, ad esempio un tavolo o un desktop. 

### <a name="beauty"></a>Bellezza

Il segmento dell'evasore porta l'utente a uno configuratore GT40, che visualizza la GT40 su un piedistallo rotante, in modo simile a come un'auto fisica potrebbe essere visualizzata in un'autovettura automobilistica.  L'utente può applicare diverse opzioni per le rotelle, scegliere tra diverse combinazioni di colori e aprire e chiudere porte e trunk (o avvio, come lo chiamano nel Regno Unito). Nel corso dell'esperienza, l'utente può prelevare l'auto e manipolarla liberamente per un'analisi più da vicino.

![GIF animata dello configuratore GT40 in esecuzione in un dispositivo](images/ford-gt40-img-05.gif)

### <a name="performance"></a>Prestazioni

Il **segmento** delle prestazioni illustra la velocità e la durabilità della GT40. Il voiceover inizia descrivendo il modo in cui l'auto è stata sviluppata e ha seguito i propri passi a Ford's Kingman, Arizona, dimostrando la sua discrizione, con oggetti visivi 3D che mostrano la GT40 in movimento sulla traccia di test. Al termine dell'introduzione al segmento delle prestazioni, il voiceover chiede all'utente di premere il pulsante Le Mans per premere il racetrack.

![GIF animata dell'app gt40 per velocità e durabilità in esecuzione in un dispositivo](images/ford-gt40-img-06.gif)

La seconda parte del segmento delle prestazioni presenta la GT40 sotto la gamma di condizioni che i driver potrebbero sperimentare alla 24 Ore di Le Mans, che si tiene ogni anno presso il Circuit de la Sarthe vicino a Le Mans, Francia. Una visualizzazione 3D mostra l'auto in movimento sulla traccia di Le Mans, con i pulsanti disponibili per rendere l'auto più veloce o più lenta. Le immagini del tachimetro e del tachimetro analogico della GT40 si spostano sopra la visualizzazione racetrack, con più dati di telemetria sulle corse visualizzati in background. L'utente può alternare le visualizzazioni giornaliere e notturne e le condizioni di guida secche e umide, offrendo una prospettiva realistica e realistica di ciò che Ken Miles e gli altri guidatori GT40 hanno provato nella corsa effettiva.

### <a name="engineering"></a>Engineering

Il  segmento engineering di Ford GT40 Experience presenta una delle innovazioni di progettazione che hanno consentito a Ford di ottenere la meglio: la possibilità di modificare i rotori e i pad dei freni in meno di un minuto, rispetto ai 20-30 minuti necessari a tutti gli altri team. Usando movimenti intuitivi, l'utente può modificare un modello 3D dettagliato del gruppo di rotelle e freni GT40. Per espandere l'assembly, l'utente preleva una chiave inglese, la allinea al lucchetto centrale sulla ruota, la ruota in senso antiorario e quindi la estrae dalla ruota. Altri movimenti vengono usati per rimuovere i rottori e i pad dei freni, sostituirli con quelli nuovi, comprimere l'assembly e ritieni sicuro il blocco centrale. In background, un timer visualizza il tempo trascorso, consentendo all'utente di verificare se è possibile completare il processo con la rapidità con cui l'antartide dei box di Le Mans.

![GIF animata dell'esperienza di progettazione GT40 in esecuzione in un dispositivo](images/ford-gt40-img-07.gif)

L'esperienza Ford GT40 può essere scaricata da [Microsoft Store,](https://www.microsoft.com/p/ford-gt40/9p4vllktfvfp?activetab=pivot:overviewtab)consentendo a chiunque abbia un HoloLens 2 di esplorare il modo in cui Happy Finish ha dato una nuova prospettiva a un'auto da corsa.

### <a name="getting-impressive-visual-fidelity"></a>Ottenere una grande fedeltà visiva

Anche se la gamma di interazioni spaziali supportate dall'esperienza Ford GT40 è straordinaria da sola, la creatività e la fedeltà visiva che l'esperienza offre è ciò che la rende davvero straordinaria. Grazie all'ottimizzazione dei modelli 3D e all'uso di shader personalizzati Unreal, Happy Finish ha raggiunto la destinazione di 60 fotogrammi al secondo, anche con il segmento delle prestazioni dell'app che si avvicina a 315.000 poligoni. 

"Sono davvero soddisfatto del modo in cui abbiamo potuto riunire un set di interazioni fluide e intuitive in una narrazione coerente e coinvolgente", afferma Lambert. "Ovviamente, la potenza di Unreal Engine in HoloLens 2 apre un nuovo mondo di opportunità per esperienze di realtà mista più interessanti ed interessanti. La fedeltà visiva senza compromessi non è sempre l'obiettivo finale per le applicazioni aziendali in HoloLens 2, ma quando lo è, il supporto per Unreal in HoloLens 2 diventa inestimabile".

### <a name="rapid-solution-delivery"></a>Distribuzione rapida di soluzioni

L'esperienza Ford GT40 dell'utente finale è la velocità con cui Happy Finish lo ha recapitato, con l'intero progetto, dalla preproduzione alla consegna finale, completata in poco meno di 12 settimane. In sintesi, il progetto ha utilizzato 1088 ore di lavoro, suddiviso come segue: direttore creative (80 ore), UX Designer (56 ore), ui designer (40 ore), sound designer (40 ore), 3D/artista tecnico (328 ore), sviluppatore software (408 ore), responsabile tecnico (40 ore), producer (56 ore) e controllo di qualità (40 ore).

"Nel complesso, le stime del progetto originale sono molto vicine", afferma Daniel Cheetham, Chief Innovation Officer di Happy Finish, responsabile della divisione interattiva dell'azienda. "L'esperienza Ford GT40 è la prova che un'app HoloLens 2 ad alta fedeltà può essere completata in pochi mesi, con un budget limitato, ma offre comunque risultati di grande impatto". 

Dal punto di vista dello sviluppo, in base alla sua esperienza precedente con Unreal in HoloLens 2, Rodriguez stima che MRTK per Unreal dimezza il tempo totale e il lavoro richiesto da Parte sua. Osserva anche come MRTK possa aiutare gli sviluppatori che non hanno mai lavorato con HoloLens 2 iniziare. "Quando altri sviluppatori affermano di essere interessati alla realtà mista, li incoraggio a passare, installare lo stack di sviluppo HoloLens 2 e MRTK e andare avanti. MRTK rende la creazione di un'app semplice e rapida e l'editor visivo Unreal funziona così bene che non è nemmeno necessario un dispositivo HoloLens 2 per iniziare. Non è affatto complicato, tutto funziona".

### <a name="potential-azure-service-enhancements"></a>Potenziali miglioramenti dei servizi di Azure

Lambert vede diversi modi in cui è possibile usare i servizi di realtà mista di Azure per migliorare l'esperienza Ford GT40, ad esempio usando Ancoraggi nello stato di Azure per offrire un'esperienza multi-utente ancorata nel mondo reale. "Dal punto di vista della creatività, Ancoraggi nello spazio di Azure aprono una gamma completamente nuova di possibilità attraverso la possibilità di mappare, rendere persistenti e ripristinare contenuti 3D o punti di interesse nel mondo fisico", afferma.

Lambert immagina anche come usare Rendering remoto di Azure o trasmettere l'app da Azure per ottenere la frequenza dei fotogrammi desiderata, lavorando con modelli 3D più dettagliati e complessi. "È stato necessario implementare alcuni shader personalizzati altamente ottimizzati in Unreal per ottenere una destinazione sul dispositivo di 60 fotogrammi al secondo", spiega. "Con Rendering remoto di Azure, si potrebbe fare molto di più e farlo molto più facilmente, senza il lavoro necessario per ottimizzare i modelli poligono, ridisegnare le mappe trame e così via."

### <a name="endless-new-possibilities"></a>Infinite nuove possibilità

Quali sono le prossime novità per Happy Finish? Il feedback di Ford sull'esperienza Ford GT40 è stato estremamente positivo, con la conseguenza di ulteriori discussioni tra Happy Finish e Ford sui progetti HoloLens 2 futuri. Al di fuori della relazione con Ford, Happy Finish sta già avviando un nuovo progetto in HoloLens 2, in cui MRTK per Unreal sarà un elemento di base per la maggior parte dell'esperienza utente. 

"Abbiamo sempre mantenuto un approccio indipendente dalla tecnologia a ogni nuovo progetto, proponendo qualsiasi set di strumenti più adatto per aiutare il client a ottenere i risultati desiderati", afferma Cheetham. "Detto questo, HoloLens 2 è emersa come standard gold de facto per la realtà mista, in particolare nell'azienda, in posizione di testa e di fronte a tutte le altre opzioni in termini di funzionalità dei dispositivi e di pervasivezza dell'ecosistema di supporto."

Secondo Cheetham, la pandemia globale ha alimentato un nuovo interesse per la realtà mista immersiva tra i potenziali clienti. "Siamo più attivi che mai, con circa il 50% dei potenziali clienti aperti a discutere di un'opzione di realtà mista", afferma. "La chiave è fare in modo che le persone lo provino. È possibile raccontare la realtà mista tutto il giorno, ma quando si consegnano loro un HoloLens 2 per sperimentare da soli, ottengono immediatamente come può essere un cambiamento di gioco. Il supporto per Unreal Engine in HoloLens 2 aumenta solo il valore che è possibile offrire, consentendo di offrire esperienze visivamente straordinarie che soddisfano anche i clienti più impegnativi."

## <a name="try-it-out"></a>Verifica

> [!div class="nextstepaction"]
> [Scaricare l'app Ford GT40](https://www.microsoft.com/p/ford-gt40/9p4vllktfvfp)

Vedere l'introduzione allo sviluppo di realtà [mista HoloLens 2](../development.md) [o MRTK per Unreal](https://github.com/microsoft/MixedRealityToolkit-Unreal) GitHub.

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